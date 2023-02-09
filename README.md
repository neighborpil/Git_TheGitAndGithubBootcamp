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
    + -a: 모든 파일을 add한다
```
> git commit -m "commit message"
> git commit -a -m "commit message"
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


### HEAd
 - current location of cheking out(현재 리파지토리가 위치하는 곳)
 - branch와 커밋을 표시
 

### git branch
 - 현재 브렌치의 목록을 보여준다
```
> git branch
```
 - 새로운 브랜치 만들기(만들고 바로 바뀌지는 않는다
```
? git branch <branch-name>
```
#### 삭제
 - -d 또는 --delete 옵션으로 삭제(fully  머지 되어 있을 경우에만 가능)
 - -D 옵션으로 강제삭제가 가능하다
 - 삭제하고자 하는 브랜치에 체크아웃 되어 있으면 삭제가 불가능하다
```
$ git switch master
$ git branch -D deleteMe
```

#### 이동 또는 rename
 - -m 으로 변경
 - 변경하고자 하는 브랜치로 체크아웃 되어야 한다
```
$ git switch recentish-music
$ git -m 2000s
```

### git switch
 - 브랜치를 바꾼다
 - options
    + -c: 생성하고 바로 바꾼다
```
> git switch <branch-name>  # just create a new branch
> git switch -c <branch-name>  # create a new branch and switch to new branch

```
 - 만약 기존의 파일을 수정한 뒤 브랜치를 스위치 하려고 하면 커밋 또는 스태시를 하라는 메세지가 뜨면서 전환이 되지 않는다.
   하지만 새로운 파일을 만든 뒤에 git switch를 하면 변경된 파일이 바꾸고자 하는 브랜치에 같이 들고 가버린다

### git checkout
 - 브랜치를 바꾼다
 - 옛날 방식
```
> git checkout <branch-name>
```

### git merge
1. fast forward mrege
   - master branch가 앞서있는 bugfix 브랜치로 이동
   - master의 head가 이동한다
   - 그냥 앞서 있는 커밋을 따라가는 것과 동일하다
![image](https://user-images.githubusercontent.com/22423285/217854709-e6e190d4-1fe3-443f-ae6f-4988719a435a.png)
   - 먼저 master 브랜치로 이동한 뒤 merge 한다
```
$ git switch master
$ git merge bugfix
```

2. Generating merge commit
   - 만약 master 브랜치과 work branch를 머지하려고 할 때에 양쪽 다 커밋이 있을 경우
![image](https://user-images.githubusercontent.com/22423285/217853769-543f6c85-5223-4602-ad8f-7233b0632244.png)
![image](https://user-images.githubusercontent.com/22423285/217860254-4e4c6b10-6131-42fe-a76c-dd0cf22d3a24.png)
   - 이 때는 머지한 뉴 커밋이 한개 더 생긴다
![image](https://user-images.githubusercontent.com/22423285/217855088-36beedfa-518b-4ba3-b5ee-9c0470829d6a.png)
![image](https://user-images.githubusercontent.com/22423285/217861503-58e6a522-0099-4e28-b5e8-c574137f4e85.png)

   - 모든 커밋은 부모를 가지고 있고 이 머지에서 발생한 커밋은 양쪽 부모를 다 가진다
   - 머지를 시도하면 머짓 커밋 메시지를 입력하라는 창이 뜬다
   - merge conflict
      + 동일 파일 위치를 수정하려고 할 때에 발생
      + 컨플리트난 파일을 열어서 아래와 같은 부분을 다 찾아 어느쪽을 사용할지 설정하면 됨
```
<<<<HEAD
ㅁㄴㅇㄹ
===========
asdf
>>>>> mybranch
```
      + 정하고 나면 마커를 삭제하고 저장하면 된다
      + 그 이후에 하나의 








