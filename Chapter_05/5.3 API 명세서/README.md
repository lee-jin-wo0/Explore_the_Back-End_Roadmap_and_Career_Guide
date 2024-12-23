# 5.3 API 명세서

**API 명세서(API specificaton)**란 클라이언트와 서버가 API를 이용해 통신할 때 어떤 요청을 보내고 무엇을 응답 데이터로 받을지 약속을 정리한 문건.

<br />

## 5.3.1 API 명세서 작성 방법 (엑셀을 기준으로 설명)

API 명세서는 API 목차 시트를 만든 후 API별로 세부 명세를 기술하는 순서로 작성.

API 명세서는 마이크로소프트 워드, 엑셀, 노션 등으로 만들 수 있음.

<br />

### API 목차 시트 만들기

API 목차 시트는 수많은 API를 표 형태로 만들어 하눈에 볼수 있도록 정리한 것. 

목차 시트가 있어야 필요한 API를 빠르게 찾아 세부 명세 시트로 이동할 수 있음.

목차 시트는 크게 URL 부분과 API 목차 부분으로 나눠 작성.

<br />

:one: URL

클라이언트가 요청을 보낼 서버 주소를 말함.

서버에 도메인을 연결하기 전이라면 숫자로 된 IP 주소를 작성.

:two: API 목차

모든 API의 목록을 표 형태로 정리한 것.

각 API의 메서드(Method), 하위 URI, API에 대한 설명(Description), 명세서 작성 여부, 서버 반영 여부 등의 정보가 담겨 있음.

<br />

### API별 세부 명세 작성하기

세부 명세에는 해당 API 요청과 응답을 정확히 주고받는 데 필요한 내용이 들어감.

<br />

:one: Method

Method(메서드)에는 클라이언트가 서버에 요청을 보낼 때 사용하는 HTTP 메서드를 작성.

데이터를 생성할 때는 POST, 조회할 때는 GET, 수정할 때는 PUT 또는 PATCH, 삭제할 때는 DELETE를 작성.

:two: Header

Header(헤더)에는 HTTP Header에 담길 데이터를 작성.

:three: Body

Body(본문)에는 API 요청 시 클라이언트가 서버로 전송하는 본문 데이터를 작성.

Body는 데이터를 조회하거나 삭제할 때는 보내지 않아도 되고, 데이터를 생성하거나 수정할 때만 작성하므로 POST와 PUT/PATCH 메서드에서만 사용.

Body에 실어 주고받는 데이터의 형식은 주로 JSON 또는 XML임.

:four: Query String

Query String(쿼리 문자열)은 API 요청 시 URL 뒤에 오는 매개변수를 말함.

매개변수의 이름과 값은 key=value 형식으로 나타내고, 각 매개변수는 &로 구분.

Query String은 서버에 특정 조건을 전달하거나 검색 쿼리를 수행하는 데 사용하기 때문에 주로 GET 메서드에서 많이 쓰임.

:five: Path Variable

Path Variable(경로 변수)은 API 요청 시 URL 경로 내에 동적으로 변경되는 값을 나타내는 변수.

자원의 식별자나 특정 동작을 수행하기 위한 인자로 사용하며, 변수명을 URL 경로 내에 중괄호({})로 감싸 표현.

:six: Response Parameters

Response Parameters(응답 매개변수)는 API 요청에 대한 응답으로 반환되는 데이터의 필드와 속성을 나타냄. 이 항목을 보면 클라이언트가 서버로부터 받는 응답 데이터의 구조와 내용을 알 수 있음.

:seven: Response Sample

Response Sample(응답 예시)은 API 요청에 대한 응답 예시.

일반적으로 JSON 형식을 사용하며, 실제 서버 응답의 예시 데이터가 포함.

:eight: Result Code

Result Code(결과 코드)는 클라이언트가 보낸 API 요청에 대한 서버의 처리 결과를 나타내는 코드.

숫자 또는 문자열로 나타내며 크게 성공, 실패, 오류로 구분.

<br />

## 5.3.2 오픈 API:스웨거

**오픈 API(OAS, OpenAPI Specification)**는 REST API를 문서화하기 위한 공개 표준(open standard)으로, REST API 명세서를 작성하는 포맷을 제공.

API 개발자(백엔드 개발자)와 프론트엔드 개발자가 원활하게 소통할 수 있또록 API를 개발, 관리, 문서화하는 데 도움을 줌.

<br />

대표적인 오픈API 도구로 스웨거(Swagger)가 있음.

:spiral_notepad: 스웨거의 특징

:small_blue_diamond: 자동으로 API 명세서를 생성하고 스웨거 UI를 통해 API 명세서를 시각적으로 구조화해 보여줌.

:small_blue_diamond: 프론트엔드 개발자가 실시간으로 업데이트된 API 문서를 확인하고 각 API의 기능, API 요청 시 전달되는 매개변수, 응답 데이터의 형식 등을 쉽게 이해.

:small_blue_diamond: API 명세서를 토대로 API 테스트(API 요청을 보내리고 응답을 확인)를 할 수 있음. 클라이언트 개발자가 API를 직접 테스트하고 디버깅할 수 있어 개발 시간이 단축됨.

<br />

스웨거는 여러 개발자가 일관된 방식으로 표준화된 API 명세서를 생성할 수 있도록 도와줌.

하지만 초기 설정이 까다롭고 API 작성 규칙을 숙지해야 하는 어려움이 있음.

<br />