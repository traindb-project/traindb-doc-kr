ALTER MODEL
===========

목적
----

``ALTER MODEL`` 문은 기존 모델의 정보를 변경하는 데 사용한다.

구문
----

다이어그램
~~~~~~~~~~

**alterModel**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/alterModel.rrd.svg" width="100%" height="100%"/>

.. only:: latex

  .. image:: ../_static/rrd/alterModel.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**modelName**

변경할 모델의 이름을 나타내는 식별자다.

**RENAME TO**

기존 모델명을 새로운 모델명으로 변경할 때 사용한다.

**newModelName**

새로운 모델명을 나타내는 식별자다.

**ENABLE**

지정한 모델을 시놉시스 생성 또는 근사 질의 처리에 사용할 수 있도록 ``ENABLED`` 상태로 변경한다.

**DISABLE**

지정한 모델을 시놉시스 생성 또는 근사 질의 처리에 사용하지 않도록 ``DISABLED`` 상태로 변경한다.
다시 사용 가능하도록 변경하려면 ``ALTER MODEL`` 구문을 ``ENABLE`` 옵션을 지정하여 실행한다.


예시
----

모델 변경
~~~~~~~~~

다음은 존재하는 ``tgan`` 이라는 모델의 이름을 ``tgan_old`` 으로 변경하는 문장이다.

.. code-block:: console

  ALTER MODEL tgan RENAME TO tgan_old;


다음은 ``tgan_old`` 라는 이름의 모델을 사용하지 못하도록 상태를 변경하는 문장이다.

.. code-block:: console

  ALTER MODEL tgan_old DISABLE;


