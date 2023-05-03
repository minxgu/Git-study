# Git 시작하기
- Git 다운로드 : https://git-scm.com/
- 작업할 로컬 저장소 생성
- 생성한 폴더에 마우스를 올리고 우측 클릭 후 `Git Bash Here` 열기


## Git 기본설정
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

