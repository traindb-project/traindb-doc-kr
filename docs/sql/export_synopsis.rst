EXPORT SYNOPSIS
===============

목적
----

``EXPORT SYNOPSIS`` 문은 생성되어 있는 시놉시스를 내보내는 데 사용한다.
이 구문은 생성된 시놉시스 데이터 파일과 카탈로그 스토어의 관련 메타데이터 파일을 zip 형식으로 함께 압축하여 바이너리 형식으로 리턴한다.
애플리케이션에서 결과 데이터를 zip 파일로 저장한 다음, ``IMPORT SYNOPSIS`` 문을 이용해 다른 TrainDB 인스턴스에서 활용할 수 있다.

구문
----

다이어그램
~~~~~~~~~~

**exportSynopsis**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/exportSynopsis.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/exportSynopsis.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**synopsisName**

내보낼 시놉시스명을 나타내는 식별자다.


예시
----

시놉시스 내보내기
~~~~~~~~~~~~~~~~~

다음은 기존에 생성되어 있는 ``order_products_syn`` 이라는 시놉시스를 내보내는 문장이다.

.. code-block:: console

  EXPORT SYNOPSIS order_products_syn;
