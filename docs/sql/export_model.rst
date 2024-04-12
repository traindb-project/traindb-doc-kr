EXPORT MODEL
============

목적
----

``EXPORT MODEL`` 문은 학습되어 있는 모델을 내보내는 데 사용한다.
이 구문은 학습된 모델 파일들과 카탈로그 스토어의 관련 메타데이터 파일을 zip 형식으로 함께 압축하여 바이너리 형식으로 리턴한다.
애플리케이션에서 결과 데이터를 zip 파일로 저장한 다음, ``IMPORT MODEL`` 문을 이용해 다른 TrainDB 인스턴스에서 활용할 수 있다.

구문
----

다이어그램
~~~~~~~~~~

**exportModel**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/exportModel.rrd.svg" width="90%"/>

.. only:: latex

  .. image:: ../_static/rrd/exportModel.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**modelName**

내보낼 모델명을 나타내는 식별자다.

**TO FILE**

TrainDB가 동일한 머신에서 동작하고 있는 경우, TO FILE 절을 사용하여 모델을 내보낼 파일 경로를 지정하면 해당 경로로 모델을 내보낸다.
내보낼 파일 경로는 문자열 리터럴로 지정하며, 지정하지 않으면 내보낼 파일이 바이너리 형식으로 리턴된다.


예시
----

모델 내보내기
~~~~~~~~~~~~~

다음은 기존에 학습되어 있는 ``tgan`` 이라는 모델을 내보내는 문장이다.

.. code-block:: console

  EXPORT MODEL tgan;
