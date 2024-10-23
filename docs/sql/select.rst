SELECT
======

목적
----

``SELECT`` 문은 테이블로부터 데이터를 조회하는 데 사용한다.

TrainDB는 Apache Calcite 기반으로 구현되어 있기 때문에 정확 질의를 표현하는 SELECT 문은 `Apache Calcite의 SQL 문법 <https://calcite.apache.org/docs/reference.html>`_ 을 따르므로 이에 대해서는 연결된 문서를 참고하기 바란다.

본 문서에서는 TrainDB에서 지원하는 근사 질의 기능인 ``SELECT APPROXIMATE`` 문에 초점을 맞추어 설명한다.

구문
----

다이어그램
~~~~~~~~~~

**select**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/select1.rrd.svg"/>
    <embed type="image/svg+xml" src="../_static/rrd/select2.rrd.svg"/>
    <embed type="image/svg+xml" src="../_static/rrd/select3.rrd.svg"/>
    <embed type="image/svg+xml" src="../_static/rrd/select4.rrd.svg"/>
    <embed type="image/svg+xml" src="../_static/rrd/select5.rrd.svg"/>
    <embed type="image/svg+xml" src="../_static/rrd/select6.rrd.svg"/>
    <embed type="image/svg+xml" src="../_static/rrd/select7.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/select1.rrd.*
  .. image:: ../_static/rrd/select2.rrd.*
  .. image:: ../_static/rrd/select3.rrd.*
  .. image:: ../_static/rrd/select4.rrd.*
  .. image:: ../_static/rrd/select5.rrd.*
  .. image:: ../_static/rrd/select6.rrd.*
  .. image:: ../_static/rrd/select7.rrd.*

**selectItemList**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/selectItemList.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/selectItemList.rrd.*

**selectItem**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/selectItem.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/selectItem.rrd.*

**tableExpression**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/tableExpression.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/tableExpression.rrd.*

**tableReference**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/tableReference.rrd.svg" width="100%" height="100%"/>

.. only:: latex

  .. image:: ../_static/rrd/tableReference.rrd.*

**tablePrimary**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/tablePrimary.rrd.svg" width="100%" height="100%"/>

.. only:: latex

  .. image:: ../_static/rrd/tablePrimary.rrd.*

**groupItemList**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/groupItemList.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/groupItemList.rrd.*

**groupItem**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/groupItem.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/groupItem.rrd.*

**orderItemList**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/orderItemList.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/orderItemList.rrd.*

**orderItem**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/orderItem.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/orderItem.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**APPROXIMATE**

근사 질의임을 나타내는 키워드다. 다음의 조건을 만족하는 경우에 근사 질의로 처리되며, 근사 질의로 처리할 수 없는 경우에는 키워드를 무시한 채 정확 질의로 처리된다.
* ``selectItemList`` 에 근사 질의를 지원하는 집계 함수가 포함되어 있다.
* ``selectItemList`` 의 컬럼들을 학습한 모델이나 시놉시스가 존재한다.

현재 근사 질의가 지원되는 집계 함수로는 ``avg``, ``sum``, ``count``, ``stddev``, ``variance``,  ``covar(covar_pop, covar_samp)``, ``corr``, ``min``, ``max``, ``mode``, ``percentile_disc`` 등이 있다.
근사 질의 시 ``GROUP BY``, ``HAVING``, ``ORDER BY`` 절을 함께 사용할 수 있다.

**selectItemList**

조회하고자 하는 컬럼 또는 표현식 목록을 지정한다.

**FROM tableExpression**

조회할 대상 테이블을 나타내는 절이다. ``tableExpression`` 에는 테이블명을 지정할 수 있으며, 추가적으로 별칭(alias)이나 컬럼명 리스트 등을 명시할 수 있다.

**WHERE booleanExpression**

``WHERE`` 조건절은 지정한 조건을 충족하는 로우(row)들만 조회되도록 제한하는 데 사용한다.
``WHERE`` 조건절을 생략하면 ``FROM`` 절의 모든 로우가 조회된다.

**GROUP BY groupItemList**

``groupItemList`` 에 포함된 표현식을 기준으로 조회된 로우들을 그룹화하는 데 사용하는 절이다. ``GROUP BY`` 절에 명시된 컬럼은 ``selectItemList`` 에 포함되어야 한다.

**HAVING booleanExpression**

``HAVING`` 절은 그룹화된 결과 중 지정된 조건이 TRUE인 로우만 조회되도록 제한하는 데 사용한다. ``HAVING`` 절을 생략하면 모든 그룹에 대한 로우가 조회된다.

**ORDER BY orderItemList**

``ORDER BY`` 절은 지정한 ``orderItemList`` 의 순서대로 결과를 정렬하는 데 사용한다. ``ORDER BY`` 절을 생략하면 결과 로우들의 조회 순서는 임의의 순서를 따른다.

**WITHIN numeric_literal SECONDS**

``WITHIN ~ SECONDS`` 절은 근사 질의 처리 시간을 가능하면 지정한 시간(초) 이내에 처리하도록 지정하는 절이다. 처리 시간이 반드시 보장되지는 않으나, 지정한 시간에 따라 내부에서 사용할 시놉시스나 모델을 선택하는 데 참고 기준이 된다. 현재는 초당 처리 가능한 로우의 수에 따라 시놉시스를 선택하는 정책이 구현되어 있으며, 해당 로우의 수는 설정 파라미터로 조절 가능하다.

**WITHIN numeric_literal PERCENT ERROR**

``WITHIN ~ PERCENT ERROR`` 절은 근사 질의 처리 정확도를 가능하면 지정한 에러 이내로 처리하도록 지정하는 절이다. 정확도가 반드시 보장되지는 않으나, 지정한 시간에 따라 내부에서 사용할 시놉시스나 모델을 선택하는 데 참고 기준이 된다.
단, ``ANALYZE SYNOPSIS`` 문을 통해 시놉시스의 데이터 분포가 분석되어 있어야만 질의 처리 시에 시놉시스의 정확도를 고려할 수 있다.

**SYNOPSIS 힌트**

``SELECT /*+ SYNOPSIS(synopsis_name) */ APPROXIMATE`` 와 같이 근사 질의에 사용할 시놉시스를 힌트로 지정할 수 있다. 해당 시놉시스가 존재하고 입력 질의를 처리하는 데 사용할 수 있다면 지정한 시놉시스를 사용하여 질의가 처리된다.


예시
----

근사 질의
~~~~~~~~~

다음은 ``instacart`` 스키마에 속한 ``order_products`` 테이블로부터 ``reordered`` 컬럼의 합계를 근사적으로 조회하는 질의문이다.

.. code-block:: console

  SELECT APPROXIMATE sum(reordered) FROM instacart.order_products;

다음과 같이 ``WHERE``, ``GROUP BY``, ``ORDER BY`` 절 등을 질의의 의도에 맞게 추가할 수 있다.

.. code-block:: console

  SELECT APPROXIMATE sum(reordered) FROM instacart.order_products
  WHERE add_to_cart_order < 5;

.. code-block:: console

  SELECT APPROXIMATE sum(reordered) FROM instacart.order_products
  GROUP BY add_to_cart_order
  ORDER BY add_to_cart_order ASC;
