시작하기
========

실행 환경 준비
--------------

TrainDB를 실행하려면 다음과 같은 환경이 필요하다.
설치 권한이 없다면 시스템 관리자에게 요청하기 바란다.
TrainDB에는 서브모듈로 TrainDB ML 모델 라이브러리가 함께 포함되어 있으며, 작동을 위해서는 아래의 요구사항을 만족해야 한다.

TrainDB
~~~~~~~

* Java 11+
* Maven 3.x
* SQLite3 (또는 datanucleus에서 지원하는 다른 DBMS - 카탈로그 저장소 용도)

TrainDB ML 모델 라이브러리
~~~~~~~~~~~~~~~~~~~~~~~~~~

* Python 3.8 또는 3.9
* pyenv 등 파이썬 가상환경 관리자 (선택)
* pytorch 등 ML 모델에서 사용하는 패키지들 - requirements.txt 설치

  * Using ``pip``: pip install -r traindb-model/requirements.txt

설치
----

다운로드
~~~~~~~~

TrainDB의 공개 저장소는 `https://github.com/traindb-project/traindb <https://github.com/traindb-project/traindb>`_ 이다. 해당 주소로부터 릴리스된 압축 파일을 다운로드하거나 아래와 같이 git을 사용해 내려받는다.

.. code-block:: console

  $ git clone --recurse-submodules https://github.com/traindb-project/traindb.git

빌드
~~~~

다음과 같이 Maven을 사용해 빌드할 수 있다.

.. code-block:: console

  $ cd traindb
  $ mvn package

빌드하고 나면 ``traindb-x.y.tar.gz`` 파일이 ``traindb-assembly/target`` 디렉토리에 생성된다. 다음과 같이 압축을 해제해 사용하면 된다.

.. code-block:: console

  $ tar xvfz traindb-assembly/target/traindb-*.tar.gz

