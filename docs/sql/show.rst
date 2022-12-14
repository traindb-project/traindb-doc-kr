SHOW
====

목적
----

``SHOW`` 문은 모델 타입, 모델, 시놉시스 등 존재하는 객체들의 정보를 조회하는 데 사용하는 구문이다.

구문
----

다이어그램
~~~~~~~~~~

**show**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/show.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/show.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**MODELTYPES**

정의되어 있는 모델 타입의 목록을 보여준다.

**MODELS**

학습되어 있는 모델의 목록을 보여준다.

**SYNOPSES**

생성되어 있는 시놉시스 테이블의 목록을 보여준다.

**SCHEMAS**

접속 중인 데이터 소스의 스키마 목록을 보여준다.

**TABLES**

사용 중인 현재 스키마에 속한 테이블 목록을 보여준다.

**QUERYLOGS**

수행했던 질의 목록을 보여준다. 환경 설정에서 수행 질의를 기록하도록 설정되어 있어야 한다.

**TASKS**

수행 질의의 태스크 목록을 보여준다. 환경 설정에서 태스크 정보를 기록하도록 설정되어 있어야 한다.


예시
----

모델 타입 조회
~~~~~~~~~~~~~~

다음은 정의되어 있는 모델 타입의 목록을 조회하는 문장이다.

.. code-block:: console

  SHOW MODELTYPES;

모델 조회
~~~~~~~~~

다음은 학습되어 있는 모델의 목록을 조회하는 문장이다.

.. code-block:: console

  SHOW MODELS;

시놉시스 조회
~~~~~~~~~~~~~

다음은 생성되어 있는 시놉시스 테이블의 목록을 조회하는 문장이다.

.. code-block:: console

  SHOW SYNOPSES;
