# Swagger

### Swagger를 이용한 REST API 문서화

- 프로젝트 개발 시 일반적으로 FrontEnd 개발자와 BackEnd 개발자가 분리
- FrontEnd 개발자의 경우 화면과 로직에 집중을 하고 BackEnd 개발자가 만든 문서 API를 보며 데이터 처리를 하게 된다.
- 이때 개발 상황의 변화에 따른 API의 추가 또는 변경할 때 마다 문서에 적용하는 불편함 발생
- 이 문제를 해결하기 위해 Swagger를 사용

### Swagger

- 간단한 설정으로 프로젝트 API 목록을 웹에서 확인 및 테스트 할 수 있게 해주는 Library
- Swagger를 사용하면 Controller에 정의되어 있는 모든 URL을 바로 확인할 수 있다.
- API 목록 뿐 아니라 API의 명세 및 설명도 볼 수 있으며, 또한 API를 직접 테스트해볼 수도 있다.

### Swagger의 적용

- pom.xml에 swagger2 dependency 추가

![26](https://user-images.githubusercontent.com/77624879/166157973-ffdaee3b-5a1c-451d-8065-a51162bba200.png)

- [SwaggerConfiguration.java](http://SwaggerConfiguration.java) 생성
    - 클래스 영역에 @EnableSwagger2 어노테이션 적용
- Swagger 적용 될 Controller
    - 클래스 영역에 @Api(value=” “) 어노테이션 적용
    - 메서드 영역에 @ApiOperation(value=” “, response= “List.class(임의의 클래스)”) 적용
- Swagger 적용 될 Model(Dto)
    - 클래스 영역에 @ApiModel(value = “ “ , description =” “) 적용
    - 프로퍼티 영역에 @ApiModelProperty(value=” “) 적용
