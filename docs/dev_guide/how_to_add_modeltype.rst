ML 모델타입 추가 방법
=====================

모델타입 분류
-------------

TrainDB에서 근사 질의 처리에 사용하는 모델타입으로는 시놉시스 생성형 모델타입과 결과 추론형 모델타입의 두 가지가 있다.
시놉시스 생성형 모델타입은 원본 데이터와 유사한 합성 데이터를 생성하는 모델타입이며, 결과추론형 모델타입은 집계 연산의 근사 결과를 예측하여 제공하는 모델타입이다.
추가하려는 모델타입의 종류에 따라 다음 절을 참고하여 자신의 모델타입을 추가할 수 있다.


모델타입 구현
-------------

자신의 모델타입을 추가하려면 추상 베이스 클래스를 상속받아 구현하면 된다.
추가하려는 모델타입에 따라 다음의 클래스를 구현하면 된다.

* 시놉시스 생성형 모델타입: ``TrainDBSynopsisModel``(https://github.com/traindb-project/traindb-model/blob/02bf2f1fd3d81df22a53c5f32ae04c87098bc887/models/TrainDBBaseModel.py#L58-L62)

.. code-block:: python

  class TrainDBSynopsisModel(TrainDBModel, abc.ABC):
    """Base class for all the ``TrainDB`` synopsis generation models."""

    def synopsis(self, row_count):
      pass


* 결과추론형 모델타입: ``TrainDBInferenceModel``(https://github.com/traindb-project/traindb-model/blob/02bf2f1fd3d81df22a53c5f32ae04c87098bc887/models/TrainDBBaseModel.py#L64-L68)

.. code-block:: python

  class TrainDBInferenceModel(TrainDBModel, abc.ABC):

    """Base class for all the ``TrainDB`` inference models."""

    def infer(self, agg_expr, group_by_column, where_condition):
      pass


위의 두 모델타입은 공통의 베이스 클래스를 상속하고 있으므로 여기에 포함된 함수들도 함께 구현해야 한다.

* 공통 베이스 클래스: ``TrainDBModel``(https://github.com/traindb-project/traindb-model/blob/02bf2f1fd3d81df22a53c5f32ae04c87098bc887/models/TrainDBBaseModel.py#L46-L56)

.. code-block:: python

  class TrainDBModel(abc.ABC):
    """Base class for all the ``TrainDB`` models."""

    ...

    def train(self, real_data, table_metadata):
      pass
   
   
    def save(self, output_path):
      pass
   
   
    def load(self, input_path):
      pass
   
   
    def list_hyperparameters():
      return []
