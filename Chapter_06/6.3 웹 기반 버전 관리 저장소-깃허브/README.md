# 6.3 웹 기반 버전 관리 저장소 : 깃허브

협업 : 2명 이상의 개발자가 함께 프로젝트를 수행하는 것을 말함.

**깃허브(GitHub)** : 대표적인 외부 저장소. 깃으로 관리하는 프로젝트를 업로드할 수 있도록 웹 기반 저장소를 생성하고 관리하는 서비스.

<br />

## 6.3.1 깃허브의 동작 방식

:one: 프로젝트 매니저가 폴더를 생성한 후 소스 코드를 저장. 해당 폴더에 [.git] 저장소를 만들고 최초의 스냅숏을 저장.

:two: 자신의 컴퓨터에 있는 스냅숏을 외부 저장소인 깃허브에 업로드.

:three: 팀원들은 깃허브를 이용해 폴더에 저장된 소스 코드 파일과 [.git] 저장소에서 관리하는 모든 스냅숏을 내려받아 작업. 그리고 작업한 것을 깃허브에 업로드 하는 과정을 반복함으로써 팀원 간의 최신 파일 상태를 유지.

<br />

:one: 내부 저장소 만들고 스냅숏 저장하기

프로젝트 매니저 :arrow_right: git init, git add, git commit :arrow_right: A프로젝트 + [.git] 저장소

:two: 깃허브에 업로드하기

A프로젝트 + [.git] 저장소 :arrow_right: git remote add, git push :arrow_right: GitHub

:three:깃허브에서 파일 가져와 작업하기

팀원 :arrow_right: git push :arrow_right: GitHub

GitHub :arrow_right: git clone 또는 git pull :arrow_right: 팀원

<br />

###  내부 저장소 만들고 스냅숏 저장하기

git init 명령어 : 자신의 컴퓨터에서 특정 폴더를 대상으로 새로운 git 저장소를 생성할 때 사용.

```shell
git init
```

명령이 정상적으로 실행되면 폴더 안에 [.git] 폴더가 생성됨. 이때 [.git]은 숨긴 폴더임.

보통은 폴더 이름에 닷(.)이 붙으면 사용자에게 보이지 않음.

따라서 [.git] 폴더를 확인하려면 해당 폴더의 옵션에서 [숨김 파일, 폴더 및 드라이브 표시]에 체크해야함.

<br />

git add 명령어 : 현재 작업 공간의 모든 파일을 스테이징 영역으로 이동할 때 사용.

```shell
# 전체 파일을 스테이징 영역으로 이동
git add .

# 특정 파일만 스테이징 영역으로 이동
git add 특정파일이름.
```

<br />

git status 명령어 : 모든 파일이 스테이징 영역으로 이동 했다는 로그 확인 할 때 사용.

```shell
git status
```

<br />

git commit 명령어 : 스테이징 영역에 있는 파일의 변경 내용을 스냅숏으로 저장할 때 사용. `-m '커밋 메시지'` 는 필수 옵션으로, 사용자가 해당 커밋에 대해 남기고 싶은 메시지를 기입.

``` shell
git commit -m '커밋 메시지'
```

<br />

git reflog 명령어 : 해당 저장소의 커밋과 관련된 모든 작업 이력을 볼 수 있음.

```shell
git reflog
```

<br />

### 깃허브에 업로드하기

자신의 컴퓨터에서 만든 스냅숏을 깃허브에 업로드하려면 깃허브의 외부 저장소를 만들어야 함.

:notebook: 외부 저장소 주소의 형식

``` html
https://github.com/사용자_아이디/저장소_이름
```

<br />

git remote add 명령어 : 내 컴푸터의 프로젝트 폴더와 깃허브 간 연결 통로를 만드는 명령어

```shell
git remote add 외부_저장소_별칭(보통 origin) 외부_저장소_주소
```

<br />

git remote -v 명령어 : 자신의 프로젝트 폴더와 연결된 외부 저장소 내역을 볼 수 있음.

``` shell
git remote -v
```

<br />

git push 명령어 : git add를 이용해 만들어진 통로를 통해 자신의 프로젝트를 업로드할 때 사용.

```shell
git push 외부_저장소_별칭(보통 origin) 브랜치_이름(일반적으로 main 또는 master)
```

<br />

### 깃허브에서 파일 가져와 작업하기

git clone 명령어 : 팀원이 깃허브에 업로드된 프로젝트를 내려받아 작업할 때 사용.

```shell
git clone 외부_저장소_주소
```

<br />

git pull 명령어 : 깃허브에 공유된 프로젝트를 내려받을 때 사용.

```shell
git pull 외부_저장소_주소
```

<br />

:spiral_notepad:  git clone과 git pull의 차이

git clone : 깃이 내 컴퓨터의 특정 폴더를 관리하도록 선언하는 것과 동시에 깃허브에서 프로젝트를 내려받아 동기화하는 작업을 수행.

git pull : 이미 내 컴퓨터의 특정 폴더를 깃으로 관리하고 있는 상태에서 깃허브의 프로젝트와 동기화만 수행.

<br />

## 6.3.2 브랜치

**브랜치(Branch)**는 동일한 프로젝트에 대해 각 개발자가 독립적으로 작업을 수행하기 위해 사용하는 개념.

프로젝트 매니저가 맨 처음 프로젝트 폴더를 생성해 깃허브에 업로드하면 master 브랜치가 생성. 이후 프로젝트를 비롯한 모든 팀원은 master 브랜치에서 git clone 또는 git pull 명령을 사용해 프로젝트를 내려 받음. 그리고 새 브랜치를 생성해 해당 브랜치 위에서 작업을 진행. 만약 3명이 작업을 완료하고 나면 각 브랜치에서 작업한 기능 X, Y, Z를 순서대로 master 브랜치로 병합. 이때 각 feature 브랜치에서 작성한 코드를 검증하기 위해 **PR(Pull Request)**이라는 과정을 거침. 이는 각 feature 브랜치에서 작업한 내용이 어떤 코드인지 리뷰를 하는 것으로, 이 코드 리뷰를 통과해야만 병합될 수 있음.

:small_blue_diamond: master 브랜치 : 제품으로 출시될 수 있는 브랜치

:small_blue_diamond: feature 브랜치 : 새로운 기능을 개발하는 브랜치

:small_blue_diamond: develop 브랜치 : 다음 버전을 출시하기 위해 개발 중인 브랜치

<br />

## 6.3.3 충돌

깃은 다수의 개발자가 동시에 작업할 수 있는 분산 버전 관리 시스템임. 따라서 동일한 파일을 여러 개발자가 수정하거나 다른 브랜치에서 작업한 변경 사항을 병합할 때 충돌(conflict)이 발생.

:small_blue_diamond: 여러 브랜치에서 같은 파일을 수정한 경우 : 여러 브랜치에서 수정한 내용을 병합하려고 할 때 각 브랜치에서 같은 파일을 수정했다면 충돌이 발생할 수 있음.

:small_blue_diamond: 파일 이름이나 경로가 충돌하는 경우 : 두 개발자가 각자의 파일에 동일한 이름을 사용하거나, 같은 파일을 다른 경로에 저장하면 충돌이 발생.