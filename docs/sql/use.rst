USE
===

목적
----

``USE`` 문은 기본 스키마를 변경하는 구문이다. 테이블을 지정할 때 앞에 스키마를 지정하지 않으면 기본 스키마로 간주하여 처리된다.

구문
----

다이어그램
~~~~~~~~~~

**use**

.. only:: html

  .. raw:: html

    <embed src="../_static/rrd/use.rrd.svg" type="image/svg+xml"/>

.. only:: latex

  .. image:: ../_static/rrd/use.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**schemaName**

기본 스키마로 사용할 스키마명을 나타내는 식별자다.


예시
----

기본 스키마 변경
~~~~~~~~~~~~~~~~

다음은 기본 스키마를 ``instacart``라는 스키마로 변경하는 문장이다.

.. code-block:: console

  USE instacart;
