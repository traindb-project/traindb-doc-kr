CREATE SYNOPSIS
===============

목적
----

``CREATE SYNOPSIS`` 문은 학습되어 있는 데이터 시놉시스 생성형 모델을 이용해 시놉시스 테이블을 생성하는 데 사용한다. 시놉시스란 원본 데이터와 유사한 형태를 갖는 합성 데이터로, 원본 데이터로부터 샘플링한 데이터와는 다르다는 점에 유의한다.

시놉시스 테이블의 구조는 모델을 학습시킬 때 지정한 컬럼 리스트를 따르며, 원본 테이블과 동일한 스키마에 저장된다.

구문
----

다이어그램
~~~~~~~~~~

**createSynopsis**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/createSynopsis1.rrd.svg"/>
    <embed type="image/svg+xml" src="../_static/rrd/createSynopsis2.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/createSynopsis1.rrd.*
  .. image:: ../_static/rrd/createSynopsis2.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**synopsisName**

생성할 시놉시스명을 나타내는 식별자다.

**modelName**

시놉시스 생성에 사용할 모델명을 나타내는 식별자다. 데이터 시놉시스 생성형 모델만 지정 가능하다.

**LIMIT**

생성할 시놉시스 테이블의 크기를 지정한다. 로우 개수 또는 원본 테이블 대비 백분율로 지정할 수 있다.


예시
----

시놉시스 생성
~~~~~~~~~~~~~

다음은 학습되어 있는 데이터 시놉시스 생성형 모델 ``tgan`` 을 이용해 10,000개 로우를 갖는 시놉시스 테이블 ``order_products_syn`` 을 생성하는 문장이다.

.. code-block:: console

  CREATE SYNOPSIS order_products_syn FROM MODEL tgan LIMIT 10000 ROWS;
