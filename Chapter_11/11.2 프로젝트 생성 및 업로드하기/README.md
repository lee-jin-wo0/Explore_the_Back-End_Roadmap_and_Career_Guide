# 11.2 프로젝트 생성 및 업로드하기

## 11.2.1 프로젝트 생성하기

스프링 부트 프로젝트는 spring initializr 사이트에서 만들 수 있음.

프로젝트의 각종 설정을 지정하고 필요한 도구를 추가한 후 [GENERATE] 버튼을 클릭하면 프로젝트 압축 파일이 자동으로 다운로드됨.

<br />

## 11.2.2 디렉터리 구조 잡기

:small_blue_diamond: config : 웹 애플리케이션의 설정 파일 또는 설정 관련 클래스를 저장.

:small_blue_diamond: domain : 웹 애플리케이션의 주요 도메인 모델을 구성하는 클래스를 저장.

<br />

:small_blue_diamond: controller : 클라이언트의 요청을 받아 처리하고 응답을 반환. 실질적인 비즈니스로직은 service가 구현하기 때문에 controller는 단순히 클라이언트의 요청을 받아 해당 요청을 처리할 srvice 객체의 메서드를 호출하고 그 결과를 반환하는 역할만 함.

:small_blue_diamond: service : 실질적인 비즈니스 로직, 즉 API의 핵심 기능을 처리. controller가 서비스를 호출하면 데이터 검증, 변환, 연산 등의 작업을 수행한 후 그 결과를 controller에 전달.

:small_blue_diamond: dao : 데이터베이스와의 통신을 담당하는 영역으로, 데이터베이스에 접근해 데이터를 조작하는 역할을 수행. service 계층으로부터 받은 요청에 따라 데이터베이스에 접근해 데이터를 생성, 조회, 수정, 삭제한 후 결과 데이터를 service에 반환.

<br />

## 11.2.3 데이터베이스와 연동하기

스프링 부트 프로젝트와 MySQL을 연동하려면 데이터베이스에 대한 정보를 application.yml 파일에 작성해야 함.

스프링 부트 웹 애플리케이션의 설정 파일인 application.yml은 웹 애플리케이션의 동작 방식, 외부 자원과의 연결 등을 정의하는 데 사용.

<br />

:small_blue_diamond: url : 데이터베이스의 주소를 지정. 

:small_blue_diamond: username : 데이터베이스의 사용자 이름을 작성.

:small_blue_diamond: password : 데이터베이스의 접근 비밀번호를 작성.

:small_blue_diamond: driver-class-name : 사용할 JDBC 드라이버의 클래스 이름을 지정.

<br />

## 11.2.4 API 구현하고 깃허브에 업로드하기

스프링 부트 프레임워크를 이용해 API를 구현.

API를 성공적으로 개발했다면 API 테스트 도구인 포스트맨을 통해 API 요청과 응답을 테스트해볼 수 있음.