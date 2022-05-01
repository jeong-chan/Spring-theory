# View

### View지정

- Controller에서는 처리 결과를 보여줄 View 이름이나 객체를 리턴하고, DispatcherServlet은 View이름이나 View 객체를 이용하여 view를 생성함
    - 명시적 지정
    - 자동 지정
- ViewResolver
    - 논리적 view와 실제 JSP파일 mapping
    - servlet-context.xml
    - prefix + 논리뷰 + suffix로 설정
- View 이름 명시적 지정
    - Controller에서 ModelAndView와 String 타입으로 리턴
- View 이름 자동 지정
    - RequestToViewNameTranslator를 이용하여 URL로 부터 view 이름을 지정
    - Model이나 Map 타입으로 리턴
    - void로 리턴하면서 ServletResponse나 HttpservletResponse 타입의 parameter가 없는 경우
- redirect view
    - View이름에 “redirect:” 접두어를 붙이면, 지정한 페이지로 redirect 됨
