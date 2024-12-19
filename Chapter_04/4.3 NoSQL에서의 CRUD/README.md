# 4.3 NoSQL에서의 CRUD

NoSQL 중 가장 유명한 MongoDB를 기준으로 NoSQL의 특징과 CRUD 처리 방식을 알아봄.

<br />

## 4.3.1 MongoDB의 특징

MongoDB는 **컬렉션(collection)**과 **도큐먼트(document)**를 사용해 데이터를 저장.

컬렉션은 RDBMS의 테이블에 해당.

도큐먼트는 튜플에 해당. 도큐먼트는 필드(Field)와 값(Value)의 쌍으로 구성. 여기서 필드는 RDBMS의 속성에 해당.

<br />

## 4.3.2 컬렉션 만들기

컬렉션을 만들 때 사용하는 명령어.

```shell
db.createCollection("컬렉션명")
```

<br />

해당 데이터베이스 내의 컬렉션 목록을 확인하는 명령어.

```shell
show collections
```

<br />

## 4.3.3 데이터 CRUD

### 데이터 생성하기

MongoDB에서는 도큐먼트별로 필드가 각기 다를 수 있음.

도큐먼트에서 데이터를 생성하는 명령어.

```shell
db.컬렉션명.insert({field : value, field: value, ...})
```

<br />

결과에서 acknowledged는 데이터 생성 작업의 성공 여부를 나타냄.

결과에서 true는 생성이 성공적으로 완료됐음을 의미.

insertedIds는 생성된 도큐먼트의 아이디를 나타냄.

<br />

### 데이터 조회하기

데이터를 조회할 때 사용하는 명령어.

```shell
db.컬렉션명.find() // 모든 도큐먼트 조회
db.컬렉션명.find({조건}) // 조건에 부합하는 도큐먼트 조회
```

데이터를 조회할 때 컬렉션의 모든 도큐먼트를 조회할 수도 있고, 특정 조건에 부합하는 도큐먼트만 조회할 수 있음.

<br />

### 데이터 수정하기

도큐먼트를 수정하는 명령어.

:one: updateOne : 조건에 부합하는 도큐먼트 중 맨 처음 도큐먼트만 수정.

:two: updateMany : 조건에 부합하는 모든 도큐먼트를 수정.

```shell
db.컬렉션명.updateOne({filter}, {update})
db.컬렉션명.updateMany({filter}, {update})
```

<br />

$set은 필드 수정 연산자로, 해당 필드 값을 교체.

```shell
db.컬렉션명.updateMany({$set : {filter}, {update}})
```

<br />

### 데이터 삭제하기

도큐먼트를 삭제하는 명령어.

:one: deleteOne : 조건에 부합하는 도큐먼트 중 맨 처음 도큐먼트만 삭제.

:two: deleteMany : 조건에 부합하는 모든 도큐먼트를 삭제. 도큐먼트 전체를 삭제할 때도 사용.

```shell
db.컬렉션명.deleteOne({조건})
db.컬렉션명.deleteMany({조건})
db.컬렉션명.deleteMany({})
```

<br />

모든 도큐먼트를 조회하는 명령어.

```shell
db.board.find()
```

