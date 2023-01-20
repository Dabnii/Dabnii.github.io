# <p align="center"> 💻 Git & GitHub

![Git cheat sheet](https://raw.githubusercontent.com/hbons/git-cheat-sheet/master/preview.png)

> https://github.com/hbons/git-cheat-sheet

## 📌 자주 사용하는 명령어

- 터미널 명령어

| 명령어        | 뜻                      | 설명                        | 활용                  |
| ------------- | ----------------------- | --------------------------- | --------------------- |
| cd            | change directory        | 폴더이동                    | cd (경로) → . .. /usr |
| ls            | list segments           | 현재 경로 내 파일 목록 출력 | ls -al                |
| pwd           | print working directory | 현재 경로 출력              |                       |
| mkdir / rmdir | make directory          | 디렉토리 생성 / 제거        |                       |
| rm            | remove                  | 파일 / 디렉토리 제거        | rm -rf                |
| cp            | copy                    | 파일 / 디렉토리 복사        |                       |
| mv            | move                    | 파일 / 디렉토리 이동        |                       |
| cat           | concatenate             | 터미널에 파일 내용 출력     |                       |
| touch         | touch                   | 파일 생성 및 날짜정보 변경  | touch readme.md       |
| chmod         | change mode             | 파일 / 디렉토리 권한 설정   | chmod u+x readme.md   |

<br>

## 📌 Git의 목적과 필요성

1.  버전 컨트롤 시스템
2.  어떤 프로그램을 수정, 개선하여 완성한 것
3.  이전과 약간씩 다른 변화들을 구분하는 표시
    1. 수정할 때 마다 파일을 새로 만들면 관리가 불편
    2. ✨ 언제든 이전 버전의 코드로 돌아갈 수 있음
    3. ✨ 어떤 개발자가 어떤 코드를 작성했는지 확인할 수 있다
    4. 하나의 프로젝트를 두고 여러명이 개발자들이 협업할 수 있다

## 📌 Github 와 Git의 차이점

1.  `Git` git을 사용한 프로젝트들의 저장소
2.  개발자들의 `Social Network`
3.  `Git` 프로젝트의 버전관리를 도와주는 시스템
4.  `GitHub → Git`을 이용해 버전관리를 한 프로젝트들을 관리하게 해주는 `호스트 서비스`

# 📌 Git cheat sheet

| 명령어                              | 뜻                                        | 설명                                                                                                                                               | 활용                                |
| ----------------------------------- | ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| git clone                           | 깃 복제                                   | 신규 repository를 내 로컬로 가져오기                                                                                                               | git clone [%ropo link%]             |
| git branch                          | 독립된 개발 공간 생성                     | 개발자, 파드 별로 브랜치를 사용해야함 <br> - e.g. main 파트 개발자는 main 브랜치를 사용 <br> - e.g. log-in 파트 개발자는 log-in 브랜치를 사용 <br> | git branch [branch name]            |
| git checkout                        | 브랜치를 이동                             | 현재 → 이동할 브랜치                                                                                                                               | git checkout [branch name]          |
| git checkout -b                     | 브랜치 생성과 함께 해당 브랜치로 checkout | 생성 및 브랜치 이동                                                                                                                                | git checkout -b [branch]            |
| git pull                            | (이미 존재하는 repo) 코드 가져오기        | GitHub의 특정 브랜치의 코드를 가져올 때 사용                                                                                                       | git pull origin [branch name]       |
| git merge                           | 코드 합치기                               | 로컬에서 현재 브랜치의 코드와 특정 브랜치의 코드를 합칠 때 사용                                                                                    | git merge [branch name]             |
| git pull                            | GitHub에서 가져올 브랜치 이름             | GibHub Master → Local Master                                                                                                                       | git pull [branch]                   |
| git stash                           | git 임시저장                              | 브랜치 이동을 위한 임시저장                                                                                                                        | git stash                           |
| git stash show -p <br> git apply -R | stash 되돌리기                            | stash를 되돌린다                                                                                                                                   | git stash show -p,<br> git apply -R |
| git remote -v                       | git remote Ref 조회                       | 연결 되어있는 원격 레파지토리 확인                                                                                                                 | git remote -v                       |
| git remote remove origin            | 연결 되어있는 원격 레파지토리 삭제        | 연결 되어있는 원격 레파지토리 삭제                                                                                                                 | git remote remove origin            |

## 📌 Git의 init, add, status, commit, log, push 명령어의 역할

1.  `git init` → g it 저장소 생성 / 버전 관리를 위한 정보 생성
    - 버전관리를 하고싶은 디렉토리에서 해당 명령어 입력
    - 해당 `git` 에 접근하여 중요한 정보를 푸시 하지 않도록 주의
2.  `git add` → 파일 수정 이력 기록 준비 e.g. 장바구니
    - 수정한 파일의 이력을 남길 준비를 하는 명령어
    - `git add [파일이름]` 특정 파일 이력을 남기고 싶을 때
    - `git add .` 변경된 파일의 전체 이력을 남기고 싶을 때
3.  `git status` → 상태를 확인할 수 있는 명령어
    - 디렉토리에서 일어나고 있는 상태를 확인할 수 있는 명령어
4.  `commit` → 파일 수정 이력 기록 e.g. 주문하는 것 `add → commit`
    - `git commit -m “msg”` 한줄로 커밋 메세지를 남길 때
    - `git commit` 여러줄의 커밋을 남길 때
5.  `log` → e.g.영수증
    - 기록 열람용
6.  `push`
    - 작성한 코드를 원격 저장소에 업로드
    - 이력을 남긴 코드를 깃허브에 올리고 싶을 때 사용하는 명령어
    - `git push origin [branch-name]`

## 🔢 터미널을 사용한 깃 허브 업로드 순서

1.  GitHub 로컬 repository 생성
    - `+` 버튼을 눌러 새로운 repository를 생성합니다.
      - README.MD 없이 생성 합니다.
      - README.MD가 없는 경우
      - …or create a new repository on the command line 섹션에서 `6` `git remote add origin https://github.com/%UserName%/%New repo%`를 복사하여 터미널에 입력합니다.
1.  `git init`
1.  `git add .`
1.  `git commit` (공식적으로 기록 남김/업로드 합니다)
1.  `git push origin (branch name)`

<hr>

```javascript

pwd
//현재 경로 출력

cd git
//폴더이동

mkdir git
//디렉토리 생성

ls
//현재 경로 내 파일 목록 출력

💡 ls -al
//현재 경로 내 파일 목록 출력
//중요한 보안이나 정보가 입력여부를 필히 확인해야함

touch.md %file Name%.md
//md 생성

i
//md 파일에 insert 상태로 전환 후 입력
:wq
//md파일을 저장하고 나가기

git status

gid add .

git remote add origin https://github.com/%username%/%repo%
git remote
git remote --v

git push origin main

//branch 확인
origin	https://github.com/%username%/%repo% (fetch)
origin	https://github.com/%username%/%repo% (push)
git branch * main
```

## 🔍 Vscode 에서 터미널을 열어보자!

- `Cmd + J`

## 📌 Git Repo를 터미널을 이용하여 clone

```jsx
cd desktop
//폴더이동 루트에서 데스크탑으로
pwd
//어느 위치인지 확인 하기
git clone https://github.com/%repolink%reponame.git
//깃허브의 repository 링크를 넣습니다
Cloning into '%Repo%'...
... [다운로드]
//다운로드가 됩니다
```

## 📌 git clone

- 코드 복제 (신규 | 내 로컬에 없다는 전제)
- 기존 repository를 내 로컬로 가져오는 명령어
- `git clone [%ropo link%]`

## 📌 git branch

- 독립된 공간 만들기
- 독립적으로 개발을 할 수 있는 공간을 만드는 명령어
- `git branch [branch name]`
- 모두 main/master 브랜치를 사용한다면 코드가 꼬이게 됨
- 위의 이유로, 개발자 마다 개별의 브랜치에서 작업해야함
  - e.g. main 파트 개발자는 main 브랜치를 사용
  - e.g. log-in 파트 개발자는 log-in 브랜치를 사용

## 📌 git checkout

- 브랜치를 이동할 때 사용
- 현재 있는 브랜치에서 다른 브랜치로 이동할 때 사용하는 명령어
- `git checkout [branch name]`
- git branch와 다른 개념 → 필히 checkout 해주어야 함!
  - 🍯 `git checkout -b [branch]` 생성과 동시에 체크아웃 가능

## 📌 git pull

- 코드 가져오기 (이미 존재하는 repository)
- github에 있는 특정 브랜치의 코드를 로컬로 가져올 때 사용하는 명령어
  - git clone : 새로운/로컬에 존재하지 않는 전체 코드를 가져오는 것
- `git pull origin [branch name]`

## 📌 git merge

- 코드 합치기
- 로컬에서 현재 브랜치의 코드와 특정 브랜치의 코드를 합칠 때 사용
- 나의 현재 위치 브랜치에서 다른 브랜치를 합칠 때
- `git merge [branch name]`
- 내 브랜치와 깃허브의 코드 병합
- PR 하단에 컨펌 이후 merge버튼이 활성화 됨
  - 제약이 있음
  - github에서는 `merge` 머지담당자가 따로 있음

## 📌 git pull

- 깃허브에서 따오고 싶은 브랜치 이름
- `git pull [branch]`
- 마스터로 이동하여 최신화 되어 있는 코드를 가져옴
- 깃허브 마스터를 → 로컬 마스터로 가져오기
- 🍯 `git pull [branch]` 풀 브랜치명 생략은 지양... 예기치 못한 오류를 야기!

## 📌 git stash

- 🗂️ 작업물 임시 저장할 수 있는 명령어
- 완료하지 않은 작업을 commit하지 않고 다시 꺼내와 마무리 할 수 있음
- ⚠️ stash 이후 진행하는 작업에 따라 작업물이 연동되거나, 삭제될 수 있으니 주의 필요.

## 🙅‍♀️ Master(Main) 작업은 지양!

- Master(Main)가 기둥
- Master(Main)를 기준으로 branch가 확장 되어야 함
- Vscode 좌측 하단에 확인 가능
- branch 수시로 확인!
- 배포할 때 마스터 코드로 진행되기 때문에 작업 🙅‍♀️

```jsx
git branch BranchName/foloderName
git branch BranchName/foloderName
* master //현재 내가 있는 브랜치

git checkout BranchName/foloderName
//브랜치로 이동
//생성했다고 해서 바로 그 디렉토리/브랜치로 이동하지 않기 때문
//어떤 작업을 할것인지에 따라 'feature' 를 fix로 바꾸어서 변동
//feature/ 작업할 기능
git checkout BranchName/foloderName
//Switched to branch 'BranchName/foloderName'
git add .

git commit -m "ADD:md 파일생성 "
//ADD:md 파일생성

git push origin BranchName/foloderName

git push origin BranchName/foloderName

git checkout master
//Switched to branch 'master'
//Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
git pull origin master
git checkout BranchName/foloderName

Switched to branch 'feature/testfile'
//내 마스터를 가져와서 로컬에 머지 할 것

```

> Origin 로컬에선 사용 X | Origin은 깃허브의 링크를 대신하는 것이기 때문

출처:

- [하던 작업을 임시로 저장 해두고 싶을 때 사용하는 명령어 git stash](https://gmlwjd9405.github.io/2018/05/18/git-stash.html)
