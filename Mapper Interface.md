# Mapper Interface

### Mapper Interface

- Mapper Interface는 mapping 파일에 기재된 SQL을 호출하기 위한 Interface
    - Mapper Interface는 SQL을 호출하는 프로그램을 Type Safe하게 기술하기 위해 MyBatis 3.x부터 등장
    - Mapping 파일에 있는 SQL을 java interface를 통해 호출할 수 있도록 해줌
- Mapper Interface를 사용하지 않았을 경우
    - SQl을 호출하는 프로그램은 SqlSession의 method의 argument에 문자열로 namespace + “.” + SQL ID로 지정
    - 문자열로 지정하기 때문에 오타에 의한 버그가 생기거나, IDE에서 제공하는 code assist를 사용할 수 없음
- Mapper Interface를 사용했을 경우
    - UserMapper Interface는 개발자가 작성
    - packagename + “.” + InterfaceName + “.” + methodName이 namespace + “.” + SQL ID가 되도록 Namespace와 SQL ID를 설정해야 함
    - Namespace 속성에는 package를 포함한 Mapper Interface의 이름을 작성
    - SQL ID에는 mapping하는 method의 이름을 지정
