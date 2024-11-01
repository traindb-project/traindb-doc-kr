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
    <embed type="image/svg+xml" src="../_static/rrd/show2.rrd.svg" width="100%" height="100%"/>

.. only:: latex

  .. image:: ../_static/rrd/show.rrd.*
  .. image:: ../_static/rrd/show2.rrd.*

**showFilterCondition**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/showFilterCondition.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/showFilterCondition.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**MODELTYPES**

정의되어 있는 모델 타입의 목록을 보여준다.

**MODELS**

학습되어 있는 모델의 목록을 보여준다.

**HYPERPARAMETERS**

모델 타입의 하이퍼파라미터 목록을 보여준다.

**SYNOPSES**

생성되어 있는 시놉시스 테이블의 목록을 보여준다.

**SCHEMAS**

접속 중인 데이터 소스의 스키마 목록을 보여준다.

**TABLES**

사용 중인 현재 스키마에 속한 테이블 목록을 보여준다.

**TABLES**

현재 스키마에 속한 테이블의 컬럼 목록을 보여준다.

**QUERYLOGS**

수행했던 질의 목록을 보여준다. 환경 설정에서 수행 질의를 기록하도록 설정되어 있어야 한다.

**TASKS**

수행 질의의 태스크 목록을 보여준다. 환경 설정에서 태스크 정보를 기록하도록 설정되어 있어야 한다.

**TRAININGS**

훈련시킨 모델의 훈련 수행 상태를 보여준다.

**showFilterCondition**

목록 조회 시 지정한 조건을 충족하는 결과만 조회되도록 제한하는 데 사용한다.


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

하이퍼파라미터 조회
~~~~~~~~~~~~~~~~~~~

다음은 ``ctgan`` 이라는 모델 타입의 하이퍼파라미터 목록을 조회하는 문장이다.

.. code-block:: console

  SHOW HYPERPARAMETERS WHERE modeltype_name = 'ctgan';

다음은 ``gan`` 이 포함된 모델 타입의 하이퍼파라미터 목록을 조회하는 문장이다.

.. code-block:: console

  SHOW HYPERPARAMETERS WHERE modeltype_name LIKE '%gan%';

시놉시스 조회
~~~~~~~~~~~~~

다음은 생성되어 있는 시놉시스 테이블의 목록을 조회하는 문장이다.

.. code-block:: console

  SHOW SYNOPSES;
