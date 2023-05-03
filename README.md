# Git 시작하기
- Git 다운로드 : https://git-scm.com/
- 작업할 로컬 저장소 생성
- 생성한 폴더에 마우스를 올리고 우측 클릭 후 `Git Bash Here` 열기


## :pushpin: 기본설정
- Visual Studio Code 에서 터미널 여는 단축키 `Ctrl + Shift + ~`
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


## :pushpin: 소스기록
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
$ git add .
$ git commit -m "test 작업"

# 수정사항 발생
$ git add .
$ git commit -m "test 작업 수정 후 abc 추가" --amend
```

### $ git push
- 소스를 원격저장소로 업로드 하기 위해서는 `git push` 명령어를 이용합니다.
- 기본문법은 `git push [원격저장소] [작업중인 브랜치명]`입니다.
```bash
$ git push origin master
```


## :pushpin: 소스업데이트
### $ git pull
- 상대방이 커밋한 파일은 명령어를 통해서 직접 업데이트를 하셔야 동기화가 됩니다.
- 이때 사용하는 명령어는 `git pull`과 `git fetch`가 있습니다.
```bash
# master 브랜치를 pull하여 업데이트
$ git pull origin master
  
# master 브랜치를 fetch하여 업데이트
$ git fetch origin master
```
- `pull` 과 `fetch` 의 차이점은 `merge` 작업을 하느냐 안하느냐로 나뉘어지며.
- `pull` 은 `fetch` + `merge` 작업이라고 생각하시면 됩니다.


