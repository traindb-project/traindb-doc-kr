DROP SYNOPSIS
=============

목적
----

``DROP SYNOPSIS`` 문은 생성되어 있는 시놉시스 테이블을 삭제하는 데 사용한다.

구문
----

다이어그램
~~~~~~~~~~

**dropSynopsis**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/dropSynopsis.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/dropSynopsis.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**synopsisName**

삭제할 시놉시스명을 나타내는 식별자다.


예시
----

시놉시스 삭제
~~~~~~~~~~~~~

다음은 생성되어 있는 시놉시스 테이블 ``order_products_syn`` 을 삭제하는 문장이다.

.. code-block:: console

  DROP SYNOPSIS order_products_syn;
