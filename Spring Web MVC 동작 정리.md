# Spring Web MVC 동작 정리

### Spring Web Application의 동작 원리

![13](https://user-images.githubusercontent.com/77624879/166157990-3027efea-3b80-4da6-b1ca-34ebd8e9dbf1.png)

- 실행 순서
    1. 웹 어플리케이션이 실행되면 Tomcat(WAS)에 의해 web.xml이 loading
    2. web.xml에 등록되어 있는 ContextLoaderListener (Java Class)가 생성됨.
        - ContextLoaderListener class는 ServletContextListener interface를 구성하고 있으며, ApplicationContext를 생성하는 역할을 수행
    3. 생성된 ContextLoaderListener는 root-context.xml을 loading
    4. root-context.xml에 등록되어 있는 Spring Container가 구동
        - 이 때 개발자가 작성한 Business Logic(Service)에 대한 부분과 Database Logic(DAO), VO 객체들이 생성됨
    5. Client로 부터 요청(request)가 들어옴
    6. DispatcherServlet(Servlet)이 생성. DipatcherServlet은 FrontController의 역할을 수행
        - Client로부터 요청 온 메시지를 분석하여 알맞은 PageController에게 전달하고 응답을 받아 요청에 따른 응답을 어떻게 할지 결정
        - 실질적인 작업은 PageController에서 이루어진다.
        - 이러한 클래스들을 HandlerMapping, ViewResolver Class라고 함
    7. DispathcerServlet은 servlet-context.xml을 loading
    8. 두번째 Spring Container가 구동되며 응답에 맞는 PageController들이 동작.
        - 이 때, 첫번 째 Spring Container가 구동되면서 생성된 DAO, VO, Service 클래스들과 협업하여 알맞은 작업을 처리
