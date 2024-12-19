# 4.2 RDBMS에서의 CRUD

CRUD란 RDBMS에서 SQL로 데이터를 어떻게 생성(Create), 조회(Read), 수정(Update), 삭제(Delete) 하는 작업.

<br />

## 4.2.1 테이블 만들기

:spiral_notepad: **CREATE문**

```sql
CREATE TABLE 테이블명 (
	속성명1 데이터_타입,
    속성명2 데이터_타입,
    ...
    속성명n 데이터_타입,
    PRIMARY KEY (속성명) /* 기본키 선언 */
);
```

<br />

만약 특정 속성의 데이터 타입으로 NULL(알 수 없는 상태를 나타내는 값)을 허용하지 않는 경우에는 데이터_타입 다음에 NOT NULL을 붙임. 아무것도 붙이지 않으면 해당 속성은 NULL 값을 허용하게 됨. 또한 속성 값이 정수(BIGINT, INT)일 때 자동으로 1씩 증가시키려면 AUTO_INCREMENT를 붙임.

CREATE문을 실행하면 데이터가 저장되지 않은 빈 user 테이블이 생성.

orderDate 속성의 TIMESTAMP는 날짜와 시간 정보를 저장하는 데 사용하는 데이터 타입.

<br />

## 4.2.2 데이터 CRUD

데이터 CRUD는 SQL의 DML(데이터 조작어)을 이용해 수행.

DML에는 INSERT 문, SELECT 문, UPDATE 문, DELETE 문이 있음.

<br />

### 데이터 생성하기

INSERT 문은 테이블에 데이터를 생성(삽입)할 때 사용.

:spiral_notepad: **INSERT 문**

```sql
INSERT INTO 테이블명(속성명1, 속성명2, 속성명3, ...)
VALUES(속성값1, 속성값2, 속성값3, ...);
```

<br />

### 데이터 조회하기

SELECT 문은 데이터를 조회할 때 사용.

:spiral_notepad: **SELECT 문**

```<br
SELECT 속성명1, 속성명2, ..., 속성명N
FROM 테이블명
WHERE 조건;
```

<br />

FROM 절에는 데이터를 조회할 테이블명을 작성함.

SELECT 절에는 해당 테이블에서 조회하고 싶은 속성명을 작성함. 이때 *(별표) 기호를 사용하면 해당 테이블의 모든 속성을 조회 가능.

WHERE 절에는 특정 조건을 만족하는 데이터만 조회함.

<br />

### 데이터 수정하기

UPDATE문은 테이블의 데이터를 수정할 때 사용.

:spiral_notepad: **UPDATE 문**

``` sql
UPDATE 테이블명
SET 속성명 = 변경할_값
WHERE 조건;
```

<br />

### 데이터 삭제하기

DELETE 문은 테이블의 데이터를 삭제할 때 사용.

관계형 데이터베이스에서 삭제는 튜플 단위로 수행.

:spiral_notepad: **DELETE 문**

```sql
DELETE FROM 테이블명
WHERE 조건;
```

<br />

## 4.2.3 조인

조인(join)은 2개 이상의 테이블을 연결해 관련 데이터를 함께 검색하는 데 사용되는 문법.

테이블들의 공통 속성 값을 기준을 테이블끼리 연결함.

<br />

### INNER JOIN

INNER JOIN은 두 테이블에서 공통된 속성 값을 가지고 있는 튜플을 반환.

:spiral_notepad: **INNER JOIN**

```sql
SELECT 속성명1, 속성명2, ..., 속성명N
FROM 테이블1 INNER JOIN 테이블2 ON 조건;
```

<br />

### FULL OUTER JOIN

FULL OUTER JOIN은 왼쪽 테이블과 오른쪽 테이블의 모든 행을 반환함.

공통 속성의 값이 일치하지 않은 경우 나머지 속성 값을 NULL로 채워 테이블을 연결.

:spiral_notepad: **FULL OUTER JOIN**

```sql
SELECT 속성명1, 속성명2, ... 속성명n
FROM 테이블1 FULL OUTER JOIN 테이블2 ON 조건;
```

<br />

### LEFT JOIN

LEFT JOIN은 기준 테이블인 왼쪽 테이블의 모든 튜플을 결과에 포함하고, 오른쪽 테이블에서는 왼쪽 테이블과 일치하는 값을 가진 튜프라만 결과에 포함.

오른쪽 테이블에 값이 없는 경우 나머지 속성을 NULL로 채움.

:spiral_notepad: **LEFT JOIN**

```sql
SELECT 속성명1, 속성명2, ... 속성명n
FROM 테이블1 LEFT JOIN 테이블2 ON 조건;
```

<br />

### RIGHT JOIN

RIGHT JOIN은 기준 테이블인 오른쪽 테이블의 모든 튜플을 결과에 포함하고, 왼쪽 테이블에서는 오른쪽 테이블과 일치하는 값을 가진 튜플만 결과에 포함.

왼쪽 테이블에 값이 없는 경우 나머지 속성을 NULL로 채움.

:spiral_notepad: **RIGHT JOIN**

```sql
SELECT 속성명1, 속성명2, ... 속성명n
FROM 테이블1 RIGHT JOIN 테이블2 ON 조건;
```

