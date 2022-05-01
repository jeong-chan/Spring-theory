# MyBatis-Spring

### MyBatis와 MyBatis-Spring의 주요 Component

- MyBatis와 MyBatis-Spring을 사용한 DB Access Architecture

![14](https://user-images.githubusercontent.com/77624879/166157992-7950538c-a528-4d98-ad8d-15bd7d97fbd7.png)

- MyBatis를 사용하는 Data Access Layer

![15](https://user-images.githubusercontent.com/77624879/166157993-c67f7b9f-6cad-438d-8355-3348f9aa1172.png)

- MyBatis 3의 주요 Component

![16](https://user-images.githubusercontent.com/77624879/166157994-72109c01-90d1-42ee-a609-4b8284460fb1.png)

- MyBtis 3의 주요 Component의 역할
    - MyBatis 설정 파일( sqlMapConfig.xml )
        - 데이터베이스의 접속 주소 정보나 객체의 alias, Mapping 파일의 경로 등의 고정된 환경 정보를 설정
    - SqlSessionFactoryBuilder
        - MyBatis 설정 파일을 바탕으로 SqlSessionFactory를 생성
    - SqlSessionFactroy
        - SqlSession을 생성
    - SqlSession
        - 핵심적인 역할을 하는 Class로 SQL 실행이나 Transaction 관리를 실행
        - SqlSession 오브젝트는 Tread-Safe하지 않으므로 therad마다 필요에 따라 생성
    - mapping 파일 (ex. member.xml)
        - SQL문과 ORMapping을 설정
- MyBatis-Spring의 주요 Component

![17](https://user-images.githubusercontent.com/77624879/166157996-9fcd59bc-0112-4bc1-bc76-b0de04975944.png)

- MyBatis-Spring의 주요 Component의 역할
    - MyBatis 설정파일 ( sqlMapConfig.xml )
        - Dto 객체의 정보를 설정함 ( Alias )
    - SqlSessionFactoryBean
        - MyBatis 설정 파일을 바탕으로 SqlSessionFatory를 생성
        - Spring Bean으로 등록해야 함
    - SqlSessionTemplate
        - 핵심적인 역할을 하는 클래스로서 SQL실행이나 Transaction 관리를 실행
        - SqlSession interface를 구현하며, Thread-safe 함.
        - Spring Bean으로 등록해야 함
    - mapping 파일 (ex. member.xml)
        - SQL문과 ORMapping을 설정
    - SpringBean 설정파일 ( beans.xml )
        - SqlSessionFactoryBean을 Bean에 등록할 때 DataSource 정보와 MyBatis Config 파일 정보, Mapping 파일의 정보를 함께 설정함
        - SqlSessionTemplate를 Bean으로 등록
