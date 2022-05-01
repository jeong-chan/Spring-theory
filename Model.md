# Model

### Model 생성

- View에 전달하는 데이터
    - @RequestMapping annotation이 적용된 method의 Map, Mode, ModelMap
    - @RequestMapping method가 return하는 ModelAndView
    - @ModelAttribute annotation이 적용된 method가 return한 객체
- Map, Model, ModelMap을 통한 설정
    - method의 argument로 받는 방식
- Model Interface의 주요 메소드
    - Model addAttribute(String name, Object value)
    - Model addAttribute(Object value)
    - Model addAllAttributes(Collection<?> values)
    - Model addAllAttributes(Map<String, ?> attributes)
    - Model mergeAttributes(Map<String, ?> attributes)
    - boolean containsAttribute(String name)
- ModleAndView를 통한 Model설정
    - Controller에서 처리결과를 보여줄 view와 view에 전달할 값(model)을 저장하는 용도로 사용
    - setViewName(String viewname)
    - addObject(String name, Object value)
- @ModelAttribute annotation을 이용한 model data 처리
    - @RequestMapping annotation이 적용되지 않은 별도 method로 모델이 추가될 객체를 생성

### 요청 URL 매칭

- 전체 경로와 Servlet기반 경로 매칭
    - DispathcerServlet은 DefaultAnnotationHandlerMapping Class를 기본으로 HandlerMapping 구현체로 사용
    - Default로 Context 내의 경로가 아닌 Servlet 경로를 제외한 나머지 경로에 대해 mapping
- Servlet 기반 경로 매칭
    - Serlvet 경로를 포함한 전체 경로를 이용해서 매칭하려는 경우
    - @RequestMapping(”/product/list”)
- @PathVariable annotation을 이용한 URI 템플릿
    - RESTful 방식
        - http://localhost/users/..
    - @RequestMapping Annotation 값으로 {템플릿 변수}를 사용
    - @PathVariable Annotation을 이용해서 {템플릿 변수}와 동일한 이름을 갖는 parameter를 추가
    
    ![12](https://user-images.githubusercontent.com/77624879/166157989-b254d7cb-a892-454d-9e43-5145fe783af3.png)
    
- RequestMapping Annotation의 추가 설정 방법
    - @RequestMappping Annotation을 class와 method에 함께 적용
    - Ant 스타일의 URI패턴 사용
        - ? : 하나의 문자열과 대치
        - * : 하나 이상의 문자열과 대치
        - ** : 하나 이상의 디렉토리와 대치
