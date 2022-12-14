DESCRIBE
========

목적
----

``DESCRIBE`` 문은 테이블의 구조를 조회하는 데 사용하는 구문이다.

구문
----

다이어그램
~~~~~~~~~~

**describe**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/describe.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/describe.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**schemaName**

구조를 조회할 테이블이 포함된 스키마명을 나타내는 식별자다. 지정하지 않으면 현재 사용 중인 스키마로 지정된다.

**tableName**

구조를 조회할 테이블명을 나타내는 식별자다.


예시
----

테이블 구조 조회
~~~~~~~~~~~~~~~~

다음은 ``instacart`` 스키마에 속한 ``order_products`` 테이블의 구조를 조회하는 문장이다.

.. code-block:: console

  DESCRIBE instacart.order_products;
