# DI

### 빈 생성범위

- 싱글톤 빈(Singleton Bean)
    - 스프링 빈은 기본적으로 싱글톤으로 만들어짐
    - 그러므로, 컨테이너가 제공하는 모든 빈의 인스턴스는 항상 동일함.
    - 컨테이너가 항상 새로운 인스턴스를 반환하게 만들고 싶을 경우 scope를 prototype으로 설정해야 함

```java
//annotation
@Scope("singleton")
```

```xml
<!-- xml configuration file -->
<bean id="memberService" class"com.saffy.hw.MemberServiceImpl" scope="prototype"/>
```

- 빈의 생성범위 지정
    - singleton
        - 스프링 컨테이너당 하나의 인스턴스 빈만 생성(default)
    - prototype
        - 컨테이너 빈을 요청할 때마다 새로운 인스턴스 생성
    - request
        - HTTP Request별로 새로운 인스턴스 생성
    - session
        - HTTP Session별로 새로운 인스턴스 생성

### 스프링 빈 설정

- 스프링 빈 설정 메타정보

![Untitled](https://user-images.githubusercontent.com/77624879/166152333-f7de8931-546b-4d86-a754-acfdddeb3870.png)

### 스프링 빈 설정 : XML

- XML문서
    - XML문서 형태로 빈의 설정 메타 정보를 기술
    - 단순하며 사용하기 쉬움, 가장 많이 사용하는 방식
    - <bean> 태그를 통해 세밀한 제어 가능

### 스프링 빈 설정 : Annotation

- Annotation
    - 어플리케이션의 규모가 커지고 빈의 개수가 많아질 경우 XML 파일을 관리하는 것이 번거로움.
    - 빈으로 사용될 클래스에 특별한 annotation을 부여해 주면 자동으로 빈 등록 가능.
    - “오브젝트 빈 스캐너”로 “빈 스캐닝”을 통해 자동 등록
        - 빈 스캐너는 기본적으로 클래스 이름의 빈의 아이디로 사용
        - 정확히는 클래스 이름의 첫 글자만 소문자로 바꾼 것을 사용
    - Annotation으로 빈을 설정할 경우 반드시 component-scan을 설정해야 한다.
    
    ```xml
    <context:component-scan base-package="com.test.hello.*"/>
    ```
    
    - Stereotype annotation 종류
        - 빈 자동등록에 사용할 수 있는 annotation
        - 빈 자동인식을 위한 annotation이 여러가지인 이유
            - 계층별로 빈의 특성이나 종류를 구분
            - AOP Pointcut 표현식을 사용하면 특정 annotation이 달린 클래스만 설정 가능
            - 특정 계층의 빈에 부가기능을 부여
        - @Repository
            - Data Access Layer의 DAO 또는 Repository 클래스에 사용
            - DataAccessException 자동변환과 같은 AOP의 적용 대상을 선정하기 위해 사용
        - @Service
            - Service Layer의 클래스에 사용
        - @Controller
            - Presentation Layer의 MVC Controller에 사용
            - 스프링 웹 서블릿에 의해 웹 요청을 처리하는 컨트롤러 빈으로 선정
        - Component
            - 위의 Layer 구분을 적용하기 어려운 일반적인 경우에 설정
            
        
        ### Dependency Injection
        
        - 객체 간의 의존관게를 자신이 아닌 외부의 조립기가 수행
        - 제어의 역행(inversion of Control, IoC)이라는 의미로 사용
        - DI를 통해 시스템에 있는 각 객체를 조정하는 외부 객체가 객체들에게 생성시에 의존관계를 주어짐
        - 느슨한 결합(loose coupling)의 주요 강점
            - 객체는 인터페이스에 의한 의존 관계만을 알고 있으며, 이 의존 관계는 구현 클래스에 대한 차이를 모르는채 서로 다른 구현으로 대체가 가능
        
        ### 스프링의 DI 지원
        
        - Spring Container가 DI 조립기를 제공
            - 스프링 설정 파일을 통하여 객체 간의 의존관계를 설정
            - Spring Container가 제공하는 API를 이용해 객체를 사용
