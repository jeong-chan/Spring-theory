# MyBatis

### 개요와 특징

- MyBatis는 Java Object와 SQL문 사이의 자동 Mapping 기능을 지원하는 ORM Framework
    - http://blog.mybatis.org
    - MyBatis는 SQL을 별도의 파일로 분리해서 관리
    - Object - SQL 사이의 parameter mapping 작업을 자동으로 함
    - MyBatis는 Hibernate나 JPA(Java Persistence API)처럼 새로운 DB프로그래밍 패러다임을 익혀야 하는 부담이 없음
    - 개발자가 익숙한 SQL을 그대로 이용하면서 JDBC코드 작성의 불편함을 제거함
    - 도메인 객체나 VO객체를 중심으로 개발 가능
- 특징
    - 쉬운 접근성과 코드의 간결함
        - 가장 간단한 persistence framework
        - XML형태로 서술된 JDBC 코드라 생각해도 될 만큼 JDBC의 모든 기능을 MyBatis가 대부분 제공
        - 복잡한 JDBC 코드를 걷어내며 깔끔한 소스코드를 유지
        - 수동적인 parameter 설정과 Query 결과에 대한 mapping 구문을 제거
    - SQL문과 프로그래밍 코드의 분리
        - SQL에 변경이 있을 때마다 자바 코드를 수정하거나 컴파일 하지 않아도 됨
        - SQL 작성과 관리 또는 검토를 DBA와 같은 개발자가 아닌 다른 사람에게 맡길 수 있음
    - 다양한 프로그래밍 언어로 구현 가능
