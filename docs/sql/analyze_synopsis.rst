ANALYZE SYNOPSIS
================

목적
----

``ANALYZE SYNOPSIS`` 문은 원본 데이터와 시놉시스 데이터의 분포를 비교하여 시놉시스의 품질을 분석하는 데 사용한다. 
사용자가 ``WITHIN ~ PERCENT ERROR`` 절을 사용하여 정확도 제약조건을 지정하는 근사 질의문을 요청했을 때, 분석해 둔 시놉시스의 품질 정보를 참고하여 시놉시스를 선정해 근사 결과를 제공하게 된다.

구문
----

다이어그램
~~~~~~~~~~

**analyzeSynopsis**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/analyzeSynopsis.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/analyzeSynopsis.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**synopsisName**

데이터 분포를 분석할 시놉시스의 이름을 지정하는 식별자다.


예시
----

시놉시스 분석하기
~~~~~~~~~~~~~~~~~

다음은 ``order_products_syn`` 라는 시놉시스의 데이터 분포를 분석하는 문장이다.

.. code-block:: console

  ANALYZE SYNOPSIS order_products_syn;
