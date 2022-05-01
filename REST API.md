# REST API

### REST(Representational State Transfer)

- 2000년도 로이 필딩(Roy Fielding)의 박사학위 논문에 최초로 소개
- REST는 ‘Representational State Transfer’의 약어로 하나의 URI는 하나의 고유한 리소스(Resource)를 대표하도록 설계된다는 개념에 전송방식을 결합해서 원하는 작업을 지정한다.

![24](https://user-images.githubusercontent.com/77624879/166158008-06b402ad-da8c-4431-922e-702f05111cc6.png)

- 웹의 장점을 최대한 활용할 수 있는 아키텍처로써 REST를 발표
- HTTP URI를 통해 제어할 자원(Resource)를 명시하고, HTTP Method( GET, POST, PUT, DELETE)을 통해 해당 자원을 제어하는 명령을 내리는 방식의 아키텍처

### REST구성

- 자원 (Resource) - URI
- 행위 (Verb) - HTTP Method
- 표현 (Representations)

### 기존 Service와 REST Service

- 기존 Service
    - 요청에 대한 처리를 한 후 가공된 data를 이용하여 특정 플랫폼에 적합한 형태의 View로 만들어서 반환
- REST Service
    - data 처리만 한다 거나, 처리 후 반환될 data가 있다면 JSON이나 XML형식으로 전달.
    - View에 대해서는 신경쓸 필요가 없음
    - 이러한 이유로 OPEN API에서 많이 사용됨

![25](https://user-images.githubusercontent.com/77624879/166158010-489eb698-f9ee-4cf9-8ada-a469dc1d3b13.png)

### REST

- 기존의 전송방식과는 달리 서버는 요청으로 받은 리소스에 대해 순수한 데이터를 전송한다.
- 기존의 GET/POST 외에 PUT, DELETE 방식을 사용하여 리소스에 대한 CRUD 처리를 할 수 있다.
- HTTP URI을 통해 제어할 자원(Resource)를 명시하고, HTTP Method ( GET/ POST/ PUT/ DELETE )를 통해 해당 자원(Resource)를 제어하는 명령을 내리는 방식의 아키텍처이다.
- 가장 큰 단점은 딱 정해진 표준이 없고 암묵적인 표준만 정해져 있음
    - 하이픈(-)은 사용가능하지만 언더바(_)는 사용하지 않는다.
    - 특별한 경우를 제외하고 대문자 사용은 하지 않는다. (대소문자를 구분하기 때문)
    - URI 마지막에 슬래시(/)를 사용하지 않는다.
    - 슬래시(/)로 계층 관계를 나타낸다.
    - 확장자가 포함된 파일 이름을 직접 포함시키지 않는다.
    - URI는 명사를 사용한다.
- 기존의 웹 접근 방식과 REST API 방식의 차이점
    - CREATE(Insert)
        - 기존
            - POST
            - /write.do?id= ?
        - REST
            - POST
            - /blog/?
    - Read(Select)
        - 기존
            - GET
            - /view.do?id=?&articleno=?
        - REST
            - GET
            - /blog/’id’/’articleno’
    - Update(Update)
        - 기존
            - POST
            - /modify.do?id=?
        - REST
            - PUT
            - /blog/?
    - Delete(Delete)
        - 기존
            - GET
            - /delete.do?id=?&articleno=?
        - REST
            - DELETE
            - /blog/’id’/’articleno’
    - 기존에는 GET과 POST방식만으로 자원에 대한 CRUD를 처리, URI는 액션을 나타냄
    - REST는 4가지 method를 모두 사용하여 CRUD를 처리, URI는 제어하려는 자원을 나타냄

### REST API 설정

- Jackson library
    - jackson-databind 라이브러리는 객체를 JSON포맷의 문자열로 변환시켜서 브라우저로 전송한다.
    - jackson-dataformat-xml 라이브러리는 객체를 xml로 브라우저로 전송한다.
    - pom.xml에 library를 추가해야 한다.

### REST관련 Annotation

- @RestController
    - Controller가 REST 방식을 처리하기 위한 것임을 명시
- @ResponsBody
    - JSP 같은 뷰로 전달되는 것이 아니라 데이터 자체를 전달
- @PathVariable
    - URL 경로에 있는 값을 파라미터로 추출
- @CrossOrigin
    - Ajax의 크로스 도메인 문제를 해결
- @RequestBody
    - JSON 데이터를 원하는 타입으로 바인딩
