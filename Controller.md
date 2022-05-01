# Controller

### @Controller

- @Controller와 RequestMapping의 선언
    - method 단위의 mapping이 가능
    - DefaultAnnotationHandlerMapping과 AnnotationHandlerAdapter를 사용함
        - Spring3.0 부터는 기본 설정이므로 별도의 추가 없이 사용 가능

![9](https://user-images.githubusercontent.com/77624879/166157986-735be2e8-51f9-42fb-babb-d7efc74968bb.png)

- Controller Class는 Client의 요청을 처리
- @Controller 선언
    - Class 타입에 적용
    - Spring 3.0 부터는 @Controller사용을 권장함
    - AbstractController class, AbstractCommonController class, Controller interface등을 확장하여 Controller 작성을 지양
- Controller Class를 <bean>에 등록
- Controller Class 자동 스캔
    - context:component-scan 선언
    - base-package에 설정된 package내의 class중 @Controller annotation이 적용된 클래스는 자동 스캔대상이 됨
    
    ```xml
    <context:component-scan base-package="com.test.controller"/>
    ```
    
- @RequestMapping 선언
    - 요청 URL mapping 정보를 설정
    - 클래스타입과 메소드에 설정 가능
    
    ![10](https://user-images.githubusercontent.com/77624879/166157987-d127a66e-4ca3-4044-af72-c0e6eb54b8a1.png)
    
- Controller method의 HTTP method에 한정
    - 같은 URL 요청에 대하여 HTTP method(GET, POST ..)에 따라 서로 다른 메소드를 mapping할 수 있음
    
    ![11](https://user-images.githubusercontent.com/77624879/166157988-cf25f20f-6b27-48bd-97fd-f219f561406a.png)
    
- Controller에서 @RequestMapping annotation을 설정하지 않으면 404 error 발생
- Controller method의 parameter로 다양한 Object를 받을 수 있음
- View에서 Command 객체에 접근 시
    - Command 객체는 자동으로 반환되는 Model에 추가됨
    - Controller의 @RequestMapping annotation method에서 전달받은 Command 객체에 접근
    - @ModelAttribute를 사용하여 View에서 사용할 Command 객체의 이름을 변경가능
- @RequestBody parmaeter type
    - HTTP  요청 Body가 그대로 객체에 전달됨
    - AnnotationMethodHandlerAdapter에는 HttpMessageConverter 타입의 메시지 변환기가 기본으로 여러 개 등록되어 있음
    - @RequestBody가 붙은 parameter가 있으면 해당 미디어 타입을 확인 후 처리 가능한 변환기(Converter)가 자동으로 객체로 변환시켜줌
    - 주로 @ResponseBody와 함께 사용됨 ( 비동기 처리 )
- Servlet API 사용
    - HttpSession의 생성을 직접 제어해야 하는 경우
    - Controller가 Cookie를 생성해야 하는 경우
    - Servlet API를 선호하는 경우
- Return 타입의 종류
    - Controller Class에서 method의 return type 종류
        - ModelAndView
        - Model
        - Map
        - String
        - View
        - void
        - (@ResponseBody Annotation 적용시) HTTP응답
