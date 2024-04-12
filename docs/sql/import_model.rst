IMPORT MODEL
============

목적
----

``IMPORT MODEL`` 문은 내보냈던 모델을 가져오는 데 사용한다.
TrainDB에서는 ``EXPORT MODEL`` 문을 사용해 모델 파일들과 카탈로그 스토어의 관련 메타데이터 파일을 zip 형식으로 내보내는 기능을 제공한다.
이 구문은 내보낸 모델을 다시 가져오기 위한 구문으로, zip 모델 파일을 바이너리 문자열로 다시 전달한다.
PreparedStatement의 setBytes 메소드 등을 이용해 모델을 바이너리 문자열로 바인딩하여 실행할 수 있다.

구문
----

다이어그램
~~~~~~~~~~

**importModel**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/importModel.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/importModel.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**modelName**

가져올 모델의 이름을 지정하는 식별자다.

**FROM**

가져올 모델 파일을 전달한다.
FROM 뒤에 모델 파일을 바이너리 형식으로 명시하여 전달할 수 있다.
TrainDB가 동일한 머신에서 동작하고 있는 경우, FILE 절을 사용하여 가져올 모델 파일 경로를 지정하면 해당 모델을 가져올 수 있으며, 가져올 파일 경로는 문자열 리터럴로 지정한다.


예시
----

모델 가져오기
~~~~~~~~~~~~~

다음은 내보냈던 모델을 ``tgan`` 이라는 이름으로 가져오는 문장이다.

.. code-block:: console

  IMPORT MODEL tgan FROM x'...';

모델의 바이너리 문자열을 ``?`` 로 두고 바인딩하여 실행할 수 있다.
