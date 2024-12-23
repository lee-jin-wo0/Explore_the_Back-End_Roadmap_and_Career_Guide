# 5.2 API의 유형

API의 유형에는 대표적으로 REST API와 GraphQL이 있음.

<br />

## 5.2.1 REST API

**REST API**란 REpresentational State Transfer API의 약자로 API 작성 규칙을 표준화를 한 것임.

REST는 웹의 장점을 활용해 만든 API 설계 스타일로, 미국의 컴퓨터 과학자인 로이 필딩이 2000년 박사 학위 논문에서 처음 소개.

<br />

### REST API의 구성 요소

REST API는 크게 **자원(resource)**, **행위(verb)**, **표현(Representation Of Resource)**로 구성.

<br />

:black_circle: **자원**

REST API는 클라이언트와 서버가 주고받는 자원(텍스트, 이미지, 음악, 영상 등)을 URI로 명시.

URI는 URL보다 상위 개념으로, 특정 자원 자체를 의미.

URL은 웹상에서 자원이 있는 곳의 위치를 뜻함.

<br />

:spiral_notepad: URI의 구조

```html
schema:[//[user[:password]@]host[:port]][/path][?query][#fragment]
```

:one: schema : 사용할 프로토콜의 종류(http, https 등)를 나타냄.

:two: user, password : 서버에 저장된 데이터에 접근하는 데 필요한 사용자의 이름과 비밀 번호로, 없는 경우 생략.

:three: host, port : 접근할 서버의 호스트명(도메인, IP 주소 등)과 포트 번호.

:four: path : 접근할 서버의 경로에 대한 상세 정보.

:five: query :  접근할 대상에 전달하는 추가 정보.

:six: fragment : 메인 자원 내에 있는 서브 자원에 접근할 때 이를 식별하기 위한 정보.

<br />

:black_circle: **행위**

행위란 HTTP 메서드를 통해 해당 자원에 CRUD 연산을 적용하는 것을 의미.

<br />

:spiral_notepad: HTTP 메서드

:one: Create(데이터 생성) : POST

:two: Read(데이터 조회) : GET

:three: Update(데이터 수정) : PUT 또는 PATCH

:four: Delete(데이터 삭제) : DELETE

<br />

:black_circle: **표현**

클라이언트가 서버에 자원을 요청하면 서버는 요청받은 시점의 자원 상태를 반환.

자원 상태는 CRUD 연산에 의해 매번 바뀜.

REST API는 변하는 자원 상태를 반영해 요청받은 시점의 자원 상태를 반환.

주고받는 자원, 즉 데이터의 형식은 JSON 또는 XML.

<br />

<br />

> **정리하면 REST API는 네트워크상에서 클라이언트와 서버가 주고받는 자원에 이름을 붙여, HTTP 메서드로 특정 자원에 대한 CRUD 연산을 요청하고, 그에 대한 응답으로 JSON 또는 XML 데이터를 응답받는 방식으로 동작**

<br />

### REST API의 특징

REST API의 가장 큰 특징은 HTTP 요청 메시지만 보고 어떤 동작이나 정보를 요청하는 쉽게 이해.

``` http
POST /users HTTP/1.1	---- 시작 행
(중략)				--- 헤더
					---- 빈 행
{
	"name" : "Charles" ---- 본문
}

- 메시지의 시작 행에 있는 POST는 데이터를 생성하라는 HTTP 메서드
- /users는 데이터 생성 요청을 보내는 URI.
- 본문에서 "name" 속성 값으로 "Charles"를 보냄.
- 개발자는 이를 통해 Charles라는 이름을 가진 사용자를 생성하라는 요청을 보냈다는 추론 가능.
```

REST의 원칙과 제약을 준수해 설계한 API를 `RESTful한 API` 라고 함

<br />

### REST API 설계 규칙

RESTful한 API를 구현할려면 REST API를 설계할 때의 핵심인 세가지 구성 요소, 즉 자원, 행위, 표현을 역할에 맞게 잘 활용해야함.

<br />

:black_circle: **URI에 명사를 사용.** (가장 중요한 규칙.)

URI에 명사가 아닌 동사, 가령 /getUserById(사용자의 id를 조회하라)와 같은 행위가 포함되면 API의 의미를 쉽게 추론 불가능.

```http
# URI를 바르게 작성한 예
GET /users/:id		---- id번 사용자를 조회하라.
POST /users			---- 새로운 사용자를 생성하라.
PATCH /users/:id	---- id번 사용자를 수정하라.
DELETE /users/:id	---- id번 사용자를 삭제하라.
# URI를 잘못 작성한 예 
GET /getUserById/:id   ---- id번 사용자 id를 조회하는 것을 조회하라?
POST /createNewUser    ---- 새로운 사용자를 생성하는 것을 생성하라?
PATCH /updateUser/:id  ---- id번 사용자를 수정하는 것을 수정하라?
DELETE /deleteUser/:id ---- id번 사용자를 삭제하는 것을 삭제하라?
```

<br />

:black_circle: **자원의 계층 관계를 /로 나타냄.**

REST API는 /(슬래시) 구분자를 사용해 자원간의 계층 관계를 나타냄.

일반적으로 이러한 관계를 `has-a` 관계라고 함.

URI의 끝으로 갈수록 더 세부적인 자원임.

<br />

:black_circle: **마지막에 /를 넣지 않음.**

URI의 마지막에는 /를 넣지 않음.

/는 계층 관계를 나타내는 구분자이므로 /를 중심으로 계층 관계를 작성하되, 더 이상 계층 관계가 없으면 /를 넣지 않음.

<br />

:black_circle: **명사와 명사를 구분할 때 -을 사용.**

URI에서 명사와 명사를 구분할 때는 _(밑줄)이 아닌 -(하이픈)을 사용.

<br />

:black_circle: **소문자만 사용.**

URI에는 대문자를 사용하지 않고 소문자만 사용.

<br />

:black_circle: **파일 확장자를 포함하지 않음.**

REST API는 클라이언트와 서버가 주고받는 메시지 본문의 데이터 형식을 나타내기 위해 URI에 파일 확장자를 포함하지 않음.

메시지 본문의 데이터 형식은 Accept 헤더를 이용해 명시.

<br />

:black_circle: **적절한 HTTP 상태 코드를 응답함.**

RESTful API는 요청에 대한 응답까지 적절하게 보내야함.

클라이언트의 요청을 받아 완료했는지, 아니면 실패했는지 등의 정보를 담은 HTTP 상태 코드를 전송해야함.

<br />

## 5.2.2 GraphQL

**GraphQL**이란 Graph Query Language의 약자로 페이스북에서 만든 쿼리 언어로, 클라이언트가 서버로 부터 데이터를 효율적으로 가져오기 위해 개발.

REST API는 백엔드 개발자가 미리 만들어놓은 API만 요청할 수 있지만, GraphQL은 원하는 데이털르 직접 요청할 수 있음.

이름에 QL(쿼리 언어)이라는 말이 붙은 것도 필요한 데이터를 직접 질의할 수 있기 때문.

GraphQL은 클라이언트가 서버로부터 데이터를 효율적으로 가져오는 것에 초점을 맞추고 있음.

'URI + HTTP 메서드' 조합으로 다양한 엔드포인트가 존재하는 REST API와 달리 .graphql이라는 URI 하나로 필요한 데이터를 조합한 쿼리를 요청.

