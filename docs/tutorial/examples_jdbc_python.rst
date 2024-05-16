JDBC 사용 예 (Python)
=====================

Python에서도 JayDeBeApi와 같은 JDBC 연결 지원 패키지를 활용해 TrainDB를 활용할 수 있다.
Google Colab에서 실행 가능한 `튜토리얼 <https://colab.research.google.com/github/traindb-project/traindb/blob/main/examples/traindb_tutorial.ipynb>`_ 이 준비되어 있으니 참고하기 바란다.

데이터 소스 접속
----------------

SQL 문을 실행하려면 먼저 데이터 소스에 접속해야 한다.
다음은 파이썬 코드에서 JDBC를 사용하여 localhost의 MySQL 데이터 소스에 접속하는 예이다.
디렉토리 경로나 DBMS 사용자명, 패스워드 등은 알맞게 변경하기 바란다.

.. code-block:: python

  import os
  import glob
  import jaydebeapi
  import sys

  ###################
  # required setting
  ###################
  os.environ['TRAINDB_PREFIX'] = "/content/traindb/traindb-root"
  db_url = "jdbc:traindb:mysql://localhost:3306"
  db_user = "root"
  db_password = "root"

  jars = glob.glob(os.environ['TRAINDB_PREFIX'] + "/share/**/*.jar", recursive=True)
  conn = jaydebeapi.connect("traindb.jdbc.Driver", db_url, [db_user, db_password], jars=jars)

TrainDB SQL 실행
----------------

성공적으로 접속이 이루어지고 나면, 다음과 같이 TrainDB에서 지원하는 다양한 SQL 문을 실행할 수 있다.
실행 예에서는 instacart 데이터셋의 일부로 본 프로젝트에서 회귀 테스트 시 사용하는 `instacart_small <https://github.com/traindb-project/traindb/tree/main/traindb-core/src/test/resources/datasets/instacart_small>`_ 데이터셋을 사용한다.

모델 타입 등록
~~~~~~~~~~~~~~

다음은 모델 타입을 등록하는 예이다.

.. code-block:: python

  ...
  stmt = conn.jconn.createStatement()
  stmt.execute("CREATE MODELTYPE tablegan FOR SYNOPSIS AS CLASS 'TableGAN' IN 'models/TableGAN.py'")

모델 학습
~~~~~~~~~

다음은 등록한 모델 타입을 데이터에 학습해 모델을 구축하는 예이다.

.. code-block:: python

  ...
  stmt = conn.jconn.createStatement()
  stmt.execute("TRAIN MODEL tgan MODELTYPE tablegan ON instacart_small.order_products(reordered, add_to_cart_order)")


시놉시스 생성
~~~~~~~~~~~~~

다음은 학습한 모델로부터 시놉시스를 생성하는 예이다.

.. code-block:: python

  ...
  stmt = conn.jconn.createStatement()
  stmt.execute("CREATE SYNOPSIS order_products_syn FROM MODEL tgan LIMIT 1000")

근사 질의 실행
~~~~~~~~~~~~~~

다음은 근사 질의를 실행하는 예이다.
집계 질의에 대해 SELECT 뒤에 ``APPROXIMATE`` 키워드를 붙여 근사 질의를 수행할 수 있다.
그러면 원본 테이블이 아닌 시놉시스를 이용해 질의 결과를 근사하게 되며, 근사 결과는 생성된 시놉시스에 따라 다를 것이다.

.. code-block:: python

  ...
  curs = conn.cursor()
  curs.execute("SELECT APPROXIMATE sum(reordered) FROM instacart_small.order_products")
  rs = curs.fetchall()
  ...

아래의 정확 질의와 결과를 비교해 보기 바란다.

.. code-block:: python

  ...
  curs = conn.cursor()
  curs.execute("SELECT sum(add_to_cart_order) FROM instacart_small.order_products")
  rs = curs.fetchall()
  ...
