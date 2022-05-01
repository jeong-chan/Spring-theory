# DI - Annotation

### 스프링 빈 의존 관계설정 - Annotation

- Annotation : 멤버변수에 직접 정의 하는 경우 setter method를 만들지 않아도 됨
- 특정 Bean의 기능 수행을 위해 다른 Bean을 참조해야하 하는 경우 사용한다.
- @Resource
    - Spring 2.5부터 지원
    - 멤버변수, setter method에 사용 가능
    - 타입에 맞춰서 연결
    - JSR-250표준 Annotatino으로 Spring Framework 2.5.* 부터 지원하는 Annotation이다.
    - JNDI 리소스와 연관지어 생각할 수 있으며, 특정 Bean이 JNDI 리소스에 대한 Injection을 필요로 하는 경우 사용할 것을 권장한다.
    
    ![21](https://user-images.githubusercontent.com/77624879/166152274-3ac1976c-2b8f-46e8-8287-65700a705dcf.png)
    
    ![22](https://user-images.githubusercontent.com/77624879/166152235-85e34a3c-186f-4b22-b6dd-91f232181a10.png)
    
- @Autowired
    - Spring 2.5부터 지원
    - Spring에서만 사용 가능
    - Required 속성을 통해 DI여부 조정
    - 멤버변수, setter, constructor, 일반 method 사용 가능
    - 타입에 맞춰서 연결
    - Spring Framework에서 지원하는 Dependency 정의 용도의 Annotation으로, Spring Framework에 종속적이긴 하지만 정밀한 Dependency Injection이 필요한 경우에 유용하다.
        
        ![23](https://user-images.githubusercontent.com/77624879/166152240-db9aae0f-30df-4b7c-b3e5-9206990ed04f.png)
        
        ![24](https://user-images.githubusercontent.com/77624879/166152241-83b4485d-ca1c-430a-b900-b138e04028f7.png)
        
        ![25](https://user-images.githubusercontent.com/77624879/166152242-129a8a4e-a505-465a-bd84-363cd4852d09.png)
        
- @Inject
    - Spring 3.0부터 지원
    - Framework에 종속적이지 않음
    - Javax.inject-x.x.x.jar 필요
    - 멤버변수, setter, constructor, 일반 method 사용 가능
    - 이름으로 연결
    - JSR-330 표준 Annotation으로 Spring 3부터 지원하는 Annotation이다.
    - 특정 Framework에 종속되지 않은 어플리케이션을 구성하기 위해서 사용할 것을 권장한다.
    - 사용하기 위해서는 클래스 패스 내에 JSR-330 라이브러리(javax.inject-x.x.x.jar) 파일이 추가되어야 함에 유의해야 한다.
- 기타 설정
    - 빈 객체의 생성단위
        - BeanFactory를 통해 Bean을 요청 시 객체생성의 범위(단위)를 설정
        - <bean>의 scope 속성을 이용해 설정
    - Scope의 값
        - singleton
            - 스프링 컨테이너당 하나의 인스턴스 빈만 생성
        - prototype
            - 컨테이너에 빈을 요청할 때마다 새로운 인스턴스 생성
        - request
            - HTTP Request 별로 새로운 인스턴스 생성
        - session
            - HTTP Session 별로 새로운 인스턴스 생성
    - Factorymethod로 부터 빈(bean) 생성
        - getBean()으로 호출 시 private 생성자도 호출 하여 객체를 생성한다.
        - 그러므로 위의 상황에서 factory method만 호출해야 객체를 얻을 수 있는 것은 아니다.
        
        ![26](https://user-images.githubusercontent.com/77624879/166152245-460db882-f6f4-4df8-9bd0-ab17b482e985.png)
        
    

### 스프링 빈의 생명 주기(Life Cycle)
  
  ![27](https://user-images.githubusercontent.com/77624879/166152246-ab3194a9-3787-4bbe-9951-206e6d9b2e88.png)
  
  ![28](https://user-images.githubusercontent.com/77624879/166152248-4860f9c1-c174-4886-8ba1-0b8180463391.png)
