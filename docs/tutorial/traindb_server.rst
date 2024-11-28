TrainDB 서버 사용하기
=====================

앞서 설명한 방식으로 TrainDB를 서버 프로세스 없이 사용할 수 있지만, 서버 프로세스를 실행한 다음 원격에서 접속하는 형태로 사용할 수도 있다.
TrainDB 서버에 연결해서 사용할 때에는 별도의 `JDBC 드라이버 <https://github.com/traindb-project/traindb-jdbc>`_ 를 이용해야 한다.

TrainDB 서버 실행
-----------------

TrainDB 서버를 실행하려면 ``bin`` 디렉토리의 ``start-traindb.sh``  파일을 실행하면 된다.
기본 주소는 ``localhost``, 기본 포트는 ``58000`` 이며, ``traindb.properties`` 설정 파일에서 변경할 수 있다.

.. code-block:: console

  $ cd $TRAINDB_HOME/bin
  $ ./start-traindb.sh

TrainDB 서버 접속
-----------------

TrainDB 서버에 접속할 때는 다음과 같이 JDBC 접속 문자열을 변경하면 된다.

* 원시 DBMS를 연결하는 경우: 다음과 같이 접속 문자열 뒤에 ``server.host`` 와 ``server.port`` 파라미터로 TrainDB 서버 정보를 지정한다.

  jdbc:traindb:<dbms>://<dbms 주소>?server.host=<TrainDB 서버 주소>:<TrainDB 서버 포트>

* TrainDB 단독으로 연결하는 경우: jdbc:traindb://<TrainDB 서버 주소>:<TrainDB 서버 포트> 형태로 지정한다.

TrainDB 서버 연결 예 (Python)
-----------------------------

다음은 파이썬 코드에서 localhost에 실행 중인 TrainDB 서버를 통해 localhost의 MySQL 데이터 소스에 연결하는 예이다.
예시 코드에서는 현재 디렉토리에 TrainDB 서버용 JDBC 드라이버 파일이 있다고 가정한다.
디렉토리 경로나 DBMS 사용자명, 패스워드 등은 알맞게 변경하기 바란다.

.. code-block:: python

  import jaydebeapi

  db_url = "jdbc:traindb:mysql://localhost:3306?server.host=localhost&server.port=58000"
  db_user = "root"
  db_password = "root"
  jars = "traindb-jdbc-x.y.jar"
  conn = jaydebeapi.connect("traindb.jdbc.Driver", db_url, [db_user, db_password], jars=jars)

접속한 이후의 SQL 문 실행 과정은 JDBC 사용 예에서 설명한 것과 동일하다.

TrainDB 서버에 단독으로 연결하는 경우에는 다음과 같이 연결할 수 있다.

.. code-block:: python

  import jaydebeapi

  db_url = "jdbc:traindb://localhost:58000"
  db_user = ""
  db_password = ""
  jars = "traindb-jdbc-x.y.jar"
  conn = jaydebeapi.connect("traindb.jdbc.Driver", db_url, [db_user, db_password], jars=jars)

TrainDB 서버 종료
-----------------

TrainDB 서버를 종료하려면 다음과 같이 ``bin`` 디렉토리의 ``stop-traindb.sh``  파일을 실행한다.

.. code-block:: console

  $ cd $TRAINDB_HOME/bin
  $ ./stop-traindb.sh

TrainDB 서버용 JDBC 드라이버 준비
---------------------------------

다운로드
~~~~~~~~

TrainDB 서버용 JDBC 드라이버의 공개 저장소는 `https://github.com/traindb-project/traindb-jdbc <https://github.com/traindb-project/traindb-jdbc>`_ 이다. 해당 주소로부터 릴리스된 압축 파일을 다운로드하거나 아래와 같이 git을 사용해 내려받는다.

.. code-block:: console

  $ git clone https://github.com/traindb-project/traindb-jdbc.git

빌드
~~~~

다음과 같이 Maven을 사용해 빌드할 수 있다.

.. code-block:: console

  $ cd traindb-jdbc
  $ mvn package

빌드하고 나면 ``traindb-jdbc-x.y.jar`` 드라이버 파일이 ``target`` 디렉토리에 생성된다.

