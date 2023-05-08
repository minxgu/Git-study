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

### $ git remote
- `git remote`란 git을 원격저장소에 저장하는 앤드포인트를 의미합니다.
```bash
$ git remote add origin https://github.com/minxgu/Git-study.git
```

### $ git clone
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
- 기본문법은 `git push [원격저장소] [작업중인 브랜치명]` 입니다.
```bash
$ git push origin master
```

&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;

### :pushpin: **소스업데이트**
> 상대방이 커밋한 파일은 명령어를 통해서 직접 업데이트를 하셔야 동기화가 됩니다.  
> 이때 사용하는 명령어는 `git pull`과 `git fetch`가 있습니다.

### $ git pull
- 원격 저장소의 정보를 가져오면서 자동으로 로컬 브랜치에 병합(Merge)까지 수행해주는 명령어이다.
- 기본문법은 `git pull [원격저장소이름] [브랜치명]` 입니다.
```bash
$ git pull origin master
```

### $ git fetch
- 원격 저장소의 커밋들을 로컬 저장소로 가져온다.
- 그리고 자동으로 병합(Merge)를 해주지 않기 때문에 본인이 직접 확인을 한 후에 병합(Merge)하는 과정을 거쳐야한다.
- 기본문법은 `git fetch [원격저장소이름]` 입니다.
```bash
$ git fetch
```

&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;

### :pushpin: 소스 복원
> 커밋을 아예 취소하거나 `git reset`, 커밋 내용을 되돌리거나 `git revert`,  
> 기존 커밋을 덮어써야하는 `--amend` 상황에 쓰이는 명령어입니다.

### $ git reset
- 커밋을 취소하는 명령어로 혼자만 사용하는 브랜치인 경우에만 사용을 권장합니다.
- 기본문법 `git reset --option [돌아갈커밋]`
```bash
< reset 사용 예 >
$ git commit -m "1"
$ git commit -m "2"
$ git commit -m "3"

# 가장 최근의 commit이 취소된다.(기본 옵션 mixed)
$ git reset HEAD^

# --hard = 돌아간 커밋 이후의 변경 이력 모두 삭제
$ git reset --hard abcdefg

# --mixed = 변경 이력은 모두 삭제하지만 변경 내용은 유지
$ git reset --mixed abcdefg

# --soft = 변경 이력은 모두 삭제하지만 변경 내용은 유지 / 리셋 후 코드반영시 add 하지 않아도 바로 커밋 가능 (stage)
$ fit reset --soft abcdefg
```

### $ git revert
- revert는 reset과 다르게 커밋을 삭제하는 것이 아닌 커밋을 추가합니다.
```bash
# 특정 커밋의 내용만을 되돌리기에 코드충돌을 최소화 한다.
$ git revert 2664ce8(돌아갈 COMMIT ID)

# 여러개의 커밋 내역도 취소가 가능하다.
$ git revert 2664ce8(돌아갈 COMMIT ID) 2234ce9(돌아갈 COMMIT ID)

# 최근 커밋을 취소 한다.
$ git revert HEAD
```

### $ git restore
- restore은 복구를 위한 명령이며, git add 명령으로 Staging Area에 올라간 파일들을 다시 Working Directory로 되돌릴 수도 있습니다.
```bash
# 최근 커밋의 파일로 복구된다.
git restore test.html(복구할 파일 명)

# 특정 커밋의 시점으로 특정 파일을 복구한다.
git restore --source 2664ce8(복구할 COMMIT ID) test.html(복구할 파일 명)

# 특정 파일 staging 취소 가능
git restore --staged test.html
```

### 원격 저장소와 로컬 저장소의 소스코드를 일치시키는 방법
```bash
# remote tracking branch (origin/main)를 깃의 원격 저장소와 일치 시킨다.
$ git fetch --prune origin 

# 방금 전 동기화된 remote tracking branch (origin/main)에 로컬 브랜치를 일치 시킨다.
$ git reset --hard origin/main 

# 만약 작성 중인 코드가 있었고, 필요 없다고 생각하면 git clean을 통하여 삭제한다. (필요에 따라 사용)
$ git clean
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

### :pushpin: **기타 명령어**
### $ sudo
- 관리자 권한으로 실행
```bash
$ sudo
```

### $ cd
```bash
# 홈 디렉토리로 이동
$ cd ~

# 디렉토리로 이동
$ cd [디렉토리명]

# 상위(부모) 디렉토리로 이동
$ cd ..
```

### $ mkdir
- 디렉토리 생성
```bash
$ mkdir [디렉토리명]
```

### $ touch
- 파일 생성
```bash
$ touch [파일명]
```

### $ rm
- 파일 생성
```bash
# 파일 삭제
$ touch [파일명]

# 렉토리 삭제
$ rm -r [디렉토리명]
```


&nbsp;
---------------------------------------------------------------------------------------------------------------------------------------------------
&nbsp;
