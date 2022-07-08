# Git_TheGitAndGithubBootcamp

## Documentation
 - https://git-scm.com/docs

## Config

### 이름 확인
```
> git config user.name
```

### 이름설정
```
> git config --global user.name Neighborpil
```

### 이메일 확인
```
> git config user.email
```

### 이메일설정
```
> git config --global user.email neighborpil@naver.com
```

### GitKraken 다운로드
 - https://www.gitkraken.com/
 
#### Linux Tips
 - bash에서 홈 디렉토리는 ~로 표시된다
 - mkdir에서 스페이스 있는 폴더를 만들려면 ""로 감싸줘야 한다
 
 
#### MacOS Tips
 - open . 커맨드를 하면 해당 디렉토리를 finder에서 보여준다
 - open 대상 폴더를 하면 대상 폴더를 finder에서 열어준다
```
> open .
> open Music 
```

#### Windows Tips
 - start . 커맨드를 하면 해당 디렉토리에서 익스플로어에서 보여준다(확인필요, git bash에서만 가능할 수 있음)
```
> start .
```

### 깃 상태 확인
```
> git status
```


### 깃 리포 생성시 기본 브렌치가 master일때 main으로 바꾸는 방법
```
git config --global init.defaultBranch main
```


### 깃 리포 생성
```
> git init
```

###  깃 스테이징
```
> git add filename
> git add .
```

### 깃 커밋
 - Options
    + -m: message
```
> git commit -m "commit message"

```

### 깃 메시지 에디터 재설정 방법(vs코드로)
```
> git config --global core.editor "code --wait"
```

### 깃 로그
 - Options
    + --abbrev-commit: 해시코드를 짧게 보여준다
    + --oneline: 한줄로 보여준다 
```
> git log
> git log --oneline
```

### 깃 어맨드(git amend)
 - 마지막 커밋만 수정 할 수 있다.
 - 마지막 커밋에 파일이 빠졌거나 아니면 오타가 있을 경우 수정 하는 것을 말한다
```
> git commit -m 'some commit'
> git add forgotten_file
> git commit --amend

```
 
### Git Ignore
 - .DS_Store : .DS_Store란 파일을 무시한다
 - folderName/ : 폴더 전체를 무시한다
 - *.log : 모든 log파일을 무시한다
 - git ignore 추천 사이트: https://www.toptal.com/developers/gitignore/
























