# GIT STUDY 03

- `open .` : 터미널에서 바로 파인더 열기

### 지난시간 fetch(.git까지), pull(workspace까지)
남이 작업한 것을 받아온다고 생각하면된다. 협업의 기초
(슬라이드 120페이지 보면된다.)

- 다른사람의 git clone을 받은 후
`$git remote -v` 하면 fetch, push경로가 나온다.

- master수정된 뒤(push후) 받을 때 pull을 받자.
`$git pull origin master`
 - 파일이 수정되어 있다.
 - fetch + merge된다고 생각하면된다.

- 이번엔 fetch를 받아보자.
`$git fetch origin master`
 - 파일 수정이 되어있지 않다.
 - .git폴더내의 log 정보는 받아온다.

#### 만약에 pull받고나서 편집창이 뜬다?
- 내가 local에서 commit을 했다. merge commit을 만들려고 편집창이 뜬 것이다.
- 파일 수정 후 git add. git commit -m 'msg' 이렇게 커밋까지 하고
  git pull origin master 를 해보면 편집창(**merge commit**)이 뜬다.
  저장하고 나간다. `:wq`
  - 해당 파일을 보자. 그럼 master에서 수정된 것, 내가 수정된 것 모두 적용되어 있다.
- merge commit을 없애고 싶다면 reset시키면 된다.
- 이런 상황이 좋지는 않다. pull을 먼저 받고 하면된다.

## Branch (브랜치)
git을 제대로 쓰는 가장 시작점이다.
원본을 기준으로 테스트, 세부작업 공간 등을 나뭇가지처럼 브랜치로 작업한다.
만약에 위처럼 merge commit이 남발이 되면 log보기 어렵다.
이럴 때 브랜치를 따서 작업하면 merge commit이 나오지 않겠지!
원본 파일을 기준으로 한 별도의 브랜치!

### 브랜치 사용 목적
- 분기(나누다)
- 단일화 된 그래프는 유연성을 잃는다.
- 깃은 모든 것을 브랜치로 관리한다. (무조건 하나의 활성화된 브랜치가 존재한다.)
- 원본에 영향을 주지 않으면서 나만의 테스트를 해보고 싶을 때
- 각 브랜치의 내용은 같지 않다. 같게 만들려면 merge를 해야한다.
- 깃의 브랜치는 아주 가볍다. 가볍게 브랜치를 추가해서 작업하다가 merge만 하면된다. 어렵게 생각하지 말자.
- master 브랜치 이름을 바꿀 수 있다.

### 브랜치 만들기
- 기준점(생성기준 브랜치)을 기준으로 그 파일들을 복사하여 생성된다.

#### `git branch 브랜치이름`
- 만들기만 한다.

#### `git checkout -b 브랜치이름`
- 브랜치를 생성하면서 바로 이동한다.  
- checkout : 브랜치 이동

#### 상태확인
- `git branch` : 로컬저장소에 있는 브랜치 보여주기
- `git branch -r`: 원격저장소의 브랜치 보여주기
 - origin/master : remove/원격저장소 브랜치이름
 - 내 로컬 브랜치와 원격 브랜치가 같을 필요는 없다.
- `git branch -a` : 로컬, 원격에 있는 브랜치 모두 보기

#### 브랜치 이동
`git checkout master` : 마스터 브랜치로 이동
- 디렉토리가 깨끗할 때 이동하도록 한다.

#### 브랜치 이름 바꾸기
`git branch -m 새로운브랜치이름` : master도 바꿀 수 있다.

- 새로운 브랜치에서 파일을 여러개 추가하고 커밋까지 해보자.
 - 다시 마스터로 브랜치 옮기면 추가된 파일이 없다.

#### 모든 브랜치 모두 push
`git push origin --all`

- github 해당 레포지토리에서 insights > network 에서 확인!

#### 브랜치 삭제
- 활성화 되어있는 브랜치를 삭제할 수 없다.
- 1) 로컬에서 merge가 안된 브랜치 지울 때
 - `git branch -D 브랜치이름`
- 2) merge가 된 브랜치 지울 때
 - `git branch -d 브랜치이름`
- 3) 원격저장소에 있는 브랜치 지울 때
 - `git push origin :브랜치이름`
- 브랜치를 삭제했다고 해서 커밋까지 삭제되는 건 아니다.  
