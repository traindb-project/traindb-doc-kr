ALTER SYNOPSIS
==============

목적
----

``ALTER SYNOPSIS`` 문은 기존 시놉시스의 정보를 변경하는 데 사용한다.

구문
----

다이어그램
~~~~~~~~~~

**alterSynopsis**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/alterSynopsis.rrd.svg" width="100%" height="100%"/>

.. only:: latex

  .. image:: ../_static/rrd/alterSynopsis.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**synopsisName**

변경할 시놉시스의 이름을 나타내는 식별자다.

**RENAME TO**

기존 시놉시스명을 새로운 시놉시스명으로 변경할 때 사용한다.

**newSynopsisName**

새로운 시놉시스명을 나타내는 식별자다.

**ENABLE**

지정한 시놉시스를 근사 질의 처리에 사용할 수 있도록 ``ENABLED`` 상태로 변경한다.

**DISABLE**

지정한 시놉시스를 근사 질의 처리에 사용하지 않도록 ``DISABLED`` 상태로 변경한다.
다시 사용 가능하도록 변경하려면 ``ALTER SYNOPSIS`` 구문을 ``ENABLE`` 옵션을 지정하여 실행한다.


예시
----

시놉시스 변경
~~~~~~~~~~~~~

다음은 기존의 ``order_products_syn`` 이라는 시놉시스의 이름을 ``order_products_syn_old`` 으로 변경하는 문장이다.

.. code-block:: console

  ALTER SYNOPSIS order_products_syn RENAME TO order_products_syn_old;


다음은 ``order_products_syn_old`` 라는 이름의 시놉시스를 근사 질의 처리에 사용하지 못하도록 상태를 변경하는 문장이다.

.. code-block:: console

  ALTER SYNOPSIS order_products_syn_old DISABLE;


