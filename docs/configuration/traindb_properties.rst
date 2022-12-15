traindb.properties
==================

TrainDB 서버 파라미터
---------------------
.. list-table:: traindb.server.*
   :widths: 25 25 50
   :header-rows: 1

   * - 파라미터명
     - 설정 값
     - 설명
   * - traindb.server.querylog
     - true, **false**
     - 수행 질의 로그의 기록 여부를 지정한다.
   * - traindb.server.tasktrace
     - true, **false**
     - 수행한 질의 태스크 정보의 기록 여부를 지정한다.
   * - traindb.server.modelrunner
     - **file**, py4j
     - 로컬 모델타입을 실행할 때 어떤 실행기를 사용할 것인지를 지정한다.


카탈로그 스토어 관련 파라미터
-----------------------------
.. list-table:: catalog.store.*
   :widths: 25 25 50
   :header-rows: 1

   * - 파라미터명
     - 설정 값
     - 설명
   * - catalog.store.driver
     - **org.sqlite.JDBC**
     - 카탈로그 스토어로 사용할 DBMS의 JDBC 드라이버 클래스
   * - catalog.store.uri
     - **jdbc:sqlite://${TRAINDB_PREFIX}/traindb_catalog_store.db**
     - 카탈로그 스토어의 URI 정보
   * - catalog.store.username
     - 
     - 카탈로그 스토어 DBMS에 접속할 계정의 사용자명
   * - catalog.store.passowrd
     - 
     - 카탈로그 스토어 DBMS에 접속할 계정의 패스워드


근사 질의 처리 관련 파라미터
----------------------------
.. list-table:: traindb.aqp.*
   :widths: 25 25 50
   :header-rows: 1

   * - 파라미터명
     - 설정 값
     - 설명
   * - traindb.aqp.exec.time.policy
     - **row**
     - 수행 시간 한정 구문을 처리할 때 사용할 정책
   * - traindb.aqp.exec.time.unit-amount
     - **10000000**
     - 수행 시간 한정 구문 처리 정책에 따른 단위 시간(초)당 설정 수치

