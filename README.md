# Git 시작하기
- Git 다운로드 : https://git-scm.com/
- 작업할 로컬 저장소 생성
- 생성한 폴더에 마우스를 올리고 우측 클릭 후 `Git Bash Here` 열기

&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;

### :pushpin: **기본설정**
> Visual Studio Code 에서 터미널 여는 단축키 `Ctrl + Shift + ~`

### $ git config
- 처음 시작하는 것이라면 git의 config 과정을 진행해야합니다.
- `git config` 명령어를 이용하여 계정에 대한 정보를 설정합니다.
```bash
$ git config --global user.name "minxgu"
$ git config --global user.email "minxgu@mail.com"
```

### $ git init
- 깃은 초기에 `git init` 작업을 진행하여 git 사용을 선언합니다.
- 혹여나 GitHub에서 클론을 받은경우 이 작업은 필요하지 않습니다.
```bash
$ git init
```

#### $ git remote
- `git remote`란 git을 원격저장소에 저장하는 앤드포인트를 의미합니다.
```bash
$ git remote add origin https://github.com/minxgu/Git-study.git
```

#### $ git clone
- git 리모트 URL을 이용하여 원격저장소에 저장된 파일을 컴퓨터로 복사해올 수 있습니다.
- 이때 `git clone` 명령어를 사용하여 복사를 시작합니다.
- `git clone`을 통해 원격파일을 복사해오면, `origin` 에는 기본적으로 클론해온 리모트 URL이 저장되있습니다.
```bash
$ git clone https://github.com/minxgu/Git-study.git
```

&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;

### :pushpin: **소스기록**
### $ git add
- 소스를 스테이징 하기 위해서는 `git add` 명령어를 이용합니다.
 ```bash
# 모든 파일 스테이징할 때
$ git add .

# 특정 파일 스테이징할 때
$ git add test.html

# 2개 이상 파일 스테이징할 때
$ git add test.html test2.html
```

### $ git commit
- 파일의 기록을 위해서는 `commit` 작업이 필요합니다.
- `git commit` 명령을 통해 Staged 상태의 파일을 커밋할 수 있습니다.
- `-m` 옵션을 이용하여 `commit mesaage`를 작성하는 것을 권장합니다.
- 실수로 커밋을 하여, 다시 커밋을 할 경우 커밋을 덮어씌울 수 있습니다. 이때 `--amend` 옵션을 이용합니다.
```bash
$ git commit -m "test 작업"

# 수정사항 발생
$ git commit -m "test 작업 수정 후 abc 추가" --amend
```

### $ git push
- 소스를 원격저장소로 업로드 하기 위해서는 `git push` 명령어를 이용합니다.
- 기본문법은 `git push [원격저장소] [작업중인 브랜치명]`입니다.
```bash
$ git push origin master
```

&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;

### :pushpin: **소스업데이트**
- 상대방이 커밋한 파일은 명령어를 통해서 직접 업데이트를 하셔야 동기화가 됩니다.  
- 이때 사용하는 명령어는 `git pull`과 `git fetch`가 있습니다.

### $ git pull
- `pull` 과 `fetch` 의 차이점은 `merge` 작업을 하느냐 안하느냐로 나뉘어지며.
- `pull` 은 `fetch` + `merge` 작업이라고 생각하시면 됩니다.
- master 브랜치를 pull하여 업데이트
```bash
$ git pull origin master
```
### $ git fetch
```bash
$ git fetch origin master
```

&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;

### :pushpin: 소스 복원
- 여러분이 git을 쓰는 이유중에 중요한 부분을 차지하는 영역입니다.
- 정상적으로 커밋된 히스토리는, 리비전으로 git에 관리됩니다.
- 실수로 잘못 작업하였거나, 예전 버전으로 롤백하여 적용할 경우 여러분은 예전 버전으로 리셋하실 수 있습니다.
- 리셋은 `git reset` 명령을 사용합니다.

```bash
$ git reset HEAD^ --soft
```

&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;

### :pushpin: **브랜치**
> 브랜치는 한국말로 가지(branch)입니다.  
> git에서는 마치 가지를 펼치듯 하나의 근본에서 여러 갈래로 쪼개어 관리할 수 있습니다.

### $ git branch
- 기본은 master 브랜치라고 불리며, 필수로 제공되는 브랜치이다.
- 브랜치를 새로 만드신다면 `git branch [브랜치명]`으로 생성합니다.
- 브랜치의 삭제는 `git branch` 명령에서 `-d` 옵션을 사용합니다.
```bash
# 브랜치 생성
$ git branch new

# 브랜치에 병합되지 않은 변경이 남아있는 경우를 제외하고 삭제 (merge O)
$ git branch -d new

# 브랜치에 병합되지 않은 변경이 남아 있었다고 해도 강제로 삭제 (merge X)
$ git branch -D new

# 현재 브랜치의 이름 변경
$ git branch -m new2
```
- 삭제된 브랜치 또한 원격 저장소에 반영을 해야합니다.
- 이때 브랜치 명 앞에 콜론(:)을 붙여주어야 하니 이 점 주의해주세요.
```bash
$ git branch -d new
$ git push origin :new
```

### $ git checkout
- master 기준으로 new를 브랜치하면 master와 똑같은 소스코드가 new에도 적용됩니다.
- 하지만 이 이후로 new에서 코드를 수정하면, master와 new는 서로 다른 코드가 되기 때문에 갈라집니다.
- 생성된 new 브랜치로 접속하기 위해서는 `git checkout [브랜치명]`을 이용합니다.
```bash
$ git checkout new

# 브랜치 생성과 동시에 체크아웃 하고자 하면 "-b" 옵션 이용
$ git checkout -b new
```

### $ git merge
- 서로 다른 브랜치를 병합
- 문법은 `git merge [브랜치명]` 입니다.
```bash
$ git merge new

< merge 사용 예 >
# Start a new feature
$ git checkout -b new-feature master

# 파일 수정
$ git add test.html
$ git commit -m "Start a feature"
$ git add test.html
$ git commit -m "Finish a feature"

# Merge in the new-feature branch
git checkout master
git merge new-feature
git branch -d new-feature
```

### $ git fatch
- 원격 저장소의 변경사항을 로컬 저장소로 가져온다. 이때 git pull과 다르게 병합은 하지 않는다.
```bash
$ git fetch

```

&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;

### :pushpin: **소스검토**
### $ git status
- 작업 디렉토리의 상태와 스테이지 된 스냅 샷의 상태를 표시하는 명령이다.
- 스테이지 된 변경 내용, 스테이지가 되지 않은 변경 내용, Git에 의한 추적 대상에서 제외 된 파일이 표시된다.
```bash
$ git status

# Changes to be committed: ~
# Changes not staged for commit: ~
# Untracked files: ~
```

### $ git log
- commit 내역 조회
```bash
$ git log
$ git log --all --online
```

### $ git diff
- 마지막 git commit과 현재 작업 트리에서 git add하지 않은 파일 간의 차이를 표시한다.
```bash
$ git diff

$ git diff --cached
$ git diff HEAD
```

&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;

