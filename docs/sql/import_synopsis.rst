IMPORT SYNOPSIS
===============

목적
----

``IMPORT SYNOPSIS`` 문은 내보냈던 시놉시스를 가져오는 데 사용한다.
TrainDB에서는 ``EXPORT SYNOPSIS`` 문을 사용해 시놉시스 데이터 파일과 카탈로그 스토어의 관련 메타데이터 파일을 zip 형식으로 내보내는 기능을 제공한다.
이 구문은 내보낸 시놉시스를 다시 가져오기 위한 구문으로, zip 모델 파일을 바이너리 문자열로 다시 전달한다.
PreparedStatement의 setBytes 메소드 등을 이용해 시놉시스를 바이너리 문자열로 바인딩하여 실행할 수 있다.

구문
----

다이어그램
~~~~~~~~~~

**importSynopsis**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/importSynopsis.rrd.svg" width="100%"/>
    <embed type="image/svg+xml" src="../_static/rrd/importSynopsis2.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/importSynopsis.rrd.*
  .. image:: ../_static/rrd/importSynopsis2.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**synopsisName**

가져올 시놉시스의 이름을 지정하는 식별자다.

**FROM**

가져올 시놉시스 파일을 전달한다.
FROM 뒤에 시놉시스 파일을 바이너리 형식으로 명시하여 전달할 수 있다.
TrainDB가 동일한 머신에서 동작하고 있는 경우, FILE 절을 사용하여 가져올 시놉시스 파일 경로를 지정하면 해당 시놉시스를 가져올 수 있으며, 가져올 파일 경로는 문자열 리터럴로 지정한다.


예시
----

시놉시스 가져오기
~~~~~~~~~~~~~~~~~

다음은 내보냈던 시놉시스를 ``order_products_syn`` 이라는 이름으로 가져오는 문장이다.

.. code-block:: console

  IMPORT SYNOPSIS order_products_syn FROM x'...';

시놉시스의 바이너리 문자열을 ``?`` 로 두고 바인딩하여 실행할 수 있다.
