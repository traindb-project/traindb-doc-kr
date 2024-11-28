traindb.properties
==================

서버 관련 파라미터
------------------
.. list-table:: traindb.server.*
   :widths: 25 25 50
   :header-rows: 1

   * - 파라미터명
     - 설정 값
     - 설명
   * - traindb.server.address
     - **localhost:58000**
     - TrainDB 서버 프로세스의 주소
   * - traindb.server.session.max
     - **100**
     - TrainDB 서버에 연결하는 최대 세션 개수
   * - traindb.server.querylog
     - true, **false**
     - 수행 질의 로그의 기록 여부
   * - traindb.server.tasktrace
     - true, **false**
     - 수행한 질의 태스크 정보의 기록 여부
   * - traindb.server.modelrunner
     - **file**, py4j
     - 로컬 모델타입의 실행 방식
   * - traindb.server.default.charset
     - **UTF-8**
     - 기본 문자 집합
   * - traindb.server.default.nationalcharset
     - **UTF-8**
     - 기본 다국어 문자 집합


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

