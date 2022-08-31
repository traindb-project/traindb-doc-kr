DROP MODEL
==========

목적
----

``DROP MODEL`` 문은 학습되어 있는 모델을 삭제하는 데 사용한다.
이 구문은 카탈로그 스토어에 있는 모델의 메타데이터만 삭제하며, 실제 모델 파일은 삭제하지 않는다.

구문
----

다이어그램
~~~~~~~~~~

**dropModel**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/dropModel.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/dropModel.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**modelName**

삭제할 모델명을 나타내는 식별자다.


예시
----

모델 삭제
~~~~~~~~~

다음은 기존에 학습되어 있는 ``tgan`` 이라는 모델을 삭제하는 문장이다.

.. code-block:: console

  DROP MODEL tgan;
