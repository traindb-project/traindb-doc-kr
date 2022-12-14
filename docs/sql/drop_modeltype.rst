DROP MODELTYPE
==============

목적
----

``DROP MODELTYPE`` 문은 정의되어 있는 모델 타입을 삭제하는 데 사용한다. 이 문장은 카탈로그 스토어에 있는 모델타입의 메타데이터만 삭제하며, 실제 모델타입 파일들은 그대로 남겨둔다.

구문
----

다이어그램
~~~~~~~~~~

**dropModeltype**

.. only:: html

  .. raw:: html

    <embed type="image/svg+xml" src="../_static/rrd/dropModeltype.rrd.svg"/>

.. only:: latex

  .. image:: ../_static/rrd/dropModeltype.rrd.*


키워드 및 파라미터
~~~~~~~~~~~~~~~~~~

**modeltypeName**

삭제할 모델 타입명을 나타내는 식별자다.


예시
----

모델 타입 삭제
~~~~~~~~~~~~~~

다음은 기존에 정의되어 있는 ``tablegan`` 이라는 모델 타입을 삭제하는 문장이다.

.. code-block:: console

 DROP MODELTYPE tablegan;
