# SpringBoot

### 특징

- Spring의 경우 Application을 개발하려면 사전에 많은 작업 (library추가, dependency 설정, SpringFramework가 처리해야 하는 여러 가지 구성 및 설정파일 등)을 해야 했다.
- SpringBoot의 장점
    - project에 따라 자주 사용되는 library들이 미리 조합되어 있다.
    - 복잡한 설정을 자동으로 처리
    - 내장 서버를 포함해서 tomcat과 같은 WAS를 추가로 설치하지 않아도 개발 가능
    - WAS에 배포하지 않고도 실행할 수 있는 JAR파일로 Web Application을 개발할 수 있다.
    

### SpringBoot Project

- projcet 생성 구조 및 주요 구성 폴더/파일
    - src/main/java
        - java source directory
    - HelloSpringBootApplication.java
        - application을 시작할 수 있는 main method가 존재하는 스프링 구성 메인 클래스
    - static
        - css, js, img등의 정적 resource directroy
    - templates
        - SpringBoot에서 사용 가능한 여러가지 View Template (Thymeleaf, Velocity, FreeMarker 등) 위치
    - [application.properties](http://application.properties)
        - application 및 스프링의 설정 등에서 사용할 여러가지 property를 정의한 file
    - src/main
        - jsp등의 리소스 directory
- src/main에 webapp 폴더 생성 후 index.html 작성
