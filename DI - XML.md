# DI - XML

### Spring설정 : XML

- XML 문서이용
    - Application에서 사용할 Spring 자원들을 설정하는 파일
    - Spring Container는 설정파일에 설정된 내용을 읽어 Application에서 필요한 기능들을 제공
    - Root tag는 <beans>
    - 파일명은 상관없음
  
![3](https://user-images.githubusercontent.com/77624879/166152256-86750489-d389-4bb6-ac9f-e555c799c3f7.png)

- 기본설정 - 빈 객체 생성 및 주입
    - 주입 할 객체를 설정파일에 설정
        - <bean>: 스프링 컨테이너가 관리할 Bean객체를 설정
    - 기본 속성
        - name : 주입 받을 곳에서 호출 할 이름 설정
        - id : 주입 받을 곳에서 호출 할 이름 설정(유일 값)
        - class : 주입 할 객체의 클래스
        - factory-method : Singleton 패턴으로 작성된 객체의 factory 메소드 호출

![4](https://user-images.githubusercontent.com/77624879/166152249-22f77699-96cb-4e4e-bad9-82beca09561c.png)

- 기본설정 - 빈 객체 얻기
    - 설정 파일에 설정한 bean을 Container가 제공하는 주입기 역할의 api를 통해 주입 받는다.

![5](https://user-images.githubusercontent.com/77624879/166152252-758f59f1-eb34-46b5-aa10-a3befaa4b3d4.png)

### 스프링 빈 의존관계설정 - xml

- Constructor 이용
    - 객체 또는 값을 생성자를 통해 주입 받는다.
    - <constructor-arg> : <bean>의 하위태그로 설정한 bean 객체 또는 값을 생성자를 통해 주입하도록 설정.
        - 설정 방법: <ref>, <value>와 같은 하위태그를 이용하여 설정 하거나 또는 속성을 이용하여 설정
            1. 하위태그 이용
                1. 객체 주입 시 : <ref bean=”bean name”’/>
                2. 문자열(String), primitive data 주입 시: <value>값</value>
                
                *type 속성: 값은 기본적으로 String으로 처리, 값의 타입을 명시해야 하는 경우에 사용 ex) <value type=”int”>10</value>
                
            2. 속성 이용
                1. 객체 주입 시 : <constructor-arg ref=”bean name”/>
                2. 문자열(String), primitive data 주입 시: <constructor-arg value=”값”/>

![6](https://user-images.githubusercontent.com/77624879/166152257-fe18faa9-a482-4f5e-9e99-f52533337c51.png)

![7](https://user-images.githubusercontent.com/77624879/166152254-57b80149-0cec-40ce-aea8-fafd58467f4a.png)

![8](https://user-images.githubusercontent.com/77624879/166152262-a9714859-0bf1-4714-a75f-05f652d19eda.png)

![9](https://user-images.githubusercontent.com/77624879/166152263-504551ca-48d7-4d0e-a3c9-b8ff9493216e.png)

![10](https://user-images.githubusercontent.com/77624879/166152265-4f0dcd35-3142-4fb4-82f7-7ff0c9635068.png)
  
![11](https://user-images.githubusercontent.com/77624879/166152264-523d012f-8a5e-4937-9c3b-d2eb807a46ed.png)

![12](https://user-images.githubusercontent.com/77624879/166152258-508d9670-cba9-48d0-b75b-eecd53a5eb38.png)

- Property 이용
    - property를 통해 객체 또는 값을 주입 받는다.
        - setter method
        - 주의: setter를 통해서는 하나의 값만 받을 수 있다.
    - <property> : <bean>의 하위 태그로 설정한 bean객체 또는 값을 property를 통해 주입하도록 설정
        - 설정 방법: <ref>, <value>와 같은 하위태그를 이용하여 설정 하거나 또는 속성을 이용하여 설정.
            - 하위태그 이용
                - 객체 주입 시:<ref bean=”bean name”/>
                - 문자열(String), primitive data 주입 시: <value>값</value>
            - 속성 이용: name - 값을 주입할 property 이름(setter의 이름)
                - 객체 주입 시: <property name=”propertyname” ref=”bean name/>
                - 문자열(String), primitive data 주입 시: <property name=”propertyname” value=”값”/>
            - xml namespace를 이용하여 설정
    
    ---
    
    - Property-하위 태그 이용
    
    ```xml
    <ref bean="bean name"/> -> 객체 주입시
    <value>값</value> -> 문자열(String), primitive data 주입 시
    ```
    
    - Property-속성 이용
    
    ```xml
    <property name="property name" ref="bean name"/>
    <property name="property name" value="값"/>
    ```
    
    - XML Namespace를 이용
        - <bean> 태그의 스키마 설정에 namespace등록
        
        ```xml
        xmlns:p="http://www.springframework.org/schema.p"
        ```
        
        - Bean 설정 시 <bean>태그의 속성으로 설정
        
        ```xml
        기본데이터 주입
        p:propertyname = "value"
        
        bean 주입
        p:propertyname-ref = "bean_id"
        
        <bean id="adminService" class="com.ssafy.service.AdminServiceImpl"
        p:name = "안효인"
        p:memberDao-ref = "memberDao" />
        ```
        
    
    ---
    
    ![13](https://user-images.githubusercontent.com/77624879/166152260-4cc321a6-7ef5-44d5-965f-dcf4882f3c28.png)
    
    ![14](https://user-images.githubusercontent.com/77624879/166152267-04fca073-ee75-4b01-8dee-d3b0f16007a8.png)
    
    ![15](https://user-images.githubusercontent.com/77624879/166152268-933b7b03-6070-4ad1-bab1-5296a3c65d39.png)
    
    ![16](https://user-images.githubusercontent.com/77624879/166152269-1643280c-1621-4fff-8edb-4484fa37b47d.png)
    
- Collection 계열 주입
    - <constructor-arg>또는 <property>의 하위 태그로 Collection값을 설정하는 태그를 이용하여 값 주입 설정
    - 설정 태그
    - <list>
        - java.util.List
        - List 계열 컬렉션 값 목록 전달
    - <set>
        - java.util.Set
        - Set계열 컬렉션 값 목록 전달
    - <map>
        - java.util.Map
        - Mpa계열 컬렉션에 key-value의 값 목록 전달
    - <props>
        - java.util.Properties
        - Properties에 key(String) - value(String)의 값 목록 전달
  
  ![17](https://user-images.githubusercontent.com/77624879/166152270-89302c0f-e661-41b0-b802-a4ffc63ec3a8.png)
  
  ![18](https://user-images.githubusercontent.com/77624879/166152271-19b6f2f1-185b-41f1-9f1a-7740a6b7caab.png)
  
  ![19](https://user-images.githubusercontent.com/77624879/166152266-c813fa0a-c4ef-4864-b069-105909ba41ca.png)
  
  ![20](https://user-images.githubusercontent.com/77624879/166152273-1d0888a8-8576-48d5-8fb2-00e11b68d904.png)
