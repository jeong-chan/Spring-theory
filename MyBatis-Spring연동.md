# MyBatis-Spring연동

### 개요

- MyBatis를 Standalone 형태로 사용하는 경우, SqlSessionFactory 객체를 직접 사용
- 스프링을 사용하는 경우, 스프링 컨테이너에 MyBatis 관련 빈을 등록하여 MyBatis를 사용
- 또한 스프링에서 제공하는 트랜잭션 기능을 사용하면 손쉽게 트랜잭션 처리 가능
- MyBatis를 스프링과 연동하기 위해서 MyBatis에서 제공하는 Spring 연동 라이브러리 필요

![18](https://user-images.githubusercontent.com/77624879/166158000-b3a18121-1953-4e2c-b7ab-b5652d79ae57.png)

### DataSource 설정

- 스프링을 사용하는 경우, 스프링에서 데이터 소스를 관리하므로 MyBatis 설정 파일에서는 일부 설정을 생략
- 스프링 환경 설정 파일(application-context.xml)에 데이터소스를 설정
- 데이터소스는 dataSource 아이디를 가진 빈으로 데이터베이스 연결정보를 가진 객체
- MyBatis와 스프링을 연동하면 데이터베이스 설정과 트랜잭션 처리는 스프링에서 관리

![19](https://user-images.githubusercontent.com/77624879/166158001-de548e19-276f-4920-bb74-1d41ffce0efc.png)

### 트랜잭션 관리자 설정

- transactionManager 아이디를 가진 빈은 트랜잭션을 관리하는 객체
- MyBatis는 JDBC를 그대로 사용하기 때문에 DataSourceTransactionManager 타입의 빈을 사용
- tx:annotation-driven 요소는 트랜잭션 관리방법을 어노테이션으로 선언하도록 설정
- 스프링은 메소드나 클래스에 @Transactional이 선언되어 있으면, AOP를 통해 트랜잭션을 처리

![20](https://user-images.githubusercontent.com/77624879/166158002-5cfd0726-f4db-4b51-941f-49bae955cdac.png)

### SqlSessionFactoryBean 설정

- MyBatis 어플리케이션은 SqlSessionFactory를 중심으로 수행
- 스프링에서 SqlSessionFactory 객체를 생성하기 위해서는 SqlSessionFactoryBean 을 빈으로 등록해야 함
- SqlSessionFactoryBean을 빈으로 등록할 때, 사용할 데이터 소스와 mybatis 설정파일 정보가 필요

![21](https://user-images.githubusercontent.com/77624879/166158003-1098d9a4-9c05-475d-a8e4-3ab2b87a994d.png)

### Mapper 빈 등록

- mapper 인터페이스를 사용하기 위해서 스캔를 사용하여 자동으로 등록하거나, 직접 빈으로 등록
- mapperScannerConfigurer을 설정하면, Mapper 인터페이스를 자동으로 검색하여 빈으로 등록
    - basePackage로 패키지를 설정하면, 해당 패키지 하위의 모든 매퍼 인터페이스가 자동으로 등록
- MapperFactoryBean 클래스는 매퍼 인터페이스를 직접 등록할 때 사용

![22](https://user-images.githubusercontent.com/77624879/166158004-e39a5c2c-808e-4db6-b0d2-9e5a72e5f9fc.png)

### MyBatis Configuration 파일 예시

- 스프링을 사용하면 DB 접속정보 및 Mapper 관련 설정은 스프링 빈으로 등록하여 관리
- 따라서, MyBatis 환경설정 파일에는 스프링에서 관리하지 않는 일부 정보만 설정
    - typeAlias, typeHandler 등

![23](https://user-images.githubusercontent.com/77624879/166158007-a8491aff-e06e-4c45-a2fd-8545a4361b84.png)

### 데이터 접근 객체 구현

- 데이터 접근객체는 특정한 기술을 사용하여 데이터 저장소에 접근하는 방식을 구현한 객체
- @Repository은 데이터 접근 객체를 빈으로 등록하기 위해 사용하는 스프링에서 제공하는 어노테이션
- @Autowired 어노테이션을 통해, 사용하려는 Mapper 인터페이스를 데이터접근 객체와 의존관계를 설정
