# <p align="center"> 💻 Git & GitHub

## 📌 자주 사용하는 명령어

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

<hr>

## 📌 Git의 목적과 필요성

1.  버전 컨트롤 시스템
2.  어떤 프로그램을 수정, 개선하여 완성한 것
3.  이전과 약간씩 다른 변화들을 구분하는 표시
    1. 수정할 때 마다 파일을 새로 만들면 관리가 불편
    2. ✨ 언제든 이전 버전의 코드로 돌아갈 수 있음
    3. ✨ 어떠 개발자가 어떤 코드를 작성했는지 확인할 수 있다
    4. 하나의 프로젝트를 두고 여러명이 개발자들이 협업할 수 있다.

## 📌 Github 와 Git의 차이점

1.  `Git` git을 사용한 프로젝트들의 저장소
2.  개발자들의 Social Network
3.  git : 프로젝트의 버전관리를 도와주는 시스템
4.  GitHub→ Git을 이용해 버전관리를 한 프로젝트들을 관리하게 해주는 호스트 서비스

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
    - 기록을 열람용
6.  `push` →
    - 작성한 코드를 원격 저장소에 업로드
    - 이력을 남긴 코드들을 깃허브에 올리고 싶을 때 사용하는 명령어
    - `git push origin [branch-name]`

## 🔢 터미널을 사용한 깃 허브 업로드 순서

1.  GitHub 로컬 레포토지 생성
    - `+` 버튼을 눌러 새로운 레포토지를 생성합니다.
      - README.MD 없이 생성 합니다.
      - README.MD가 없는 경우
      - …or create a new repository on the command line 섹션에서 `6` `git remote add origin https://github.com/%UserName%/%New repo%`를 복사하여 터미널에 입력합니다.
1.  `git innit`
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

li
// 현재 경로 내 파일 목록 출력

💡 li -al
//현재 경로 내 파일 목록 출력
// 중요한 보안이나 정보가 입력여부를 필히 확인해야함

touch.md %file Name%.md
//md 생성

i
// md 파일에 insert 상태로 전환 후 입력
:qw
//md파일을 저장하고 나가기

git status
// git
gid add .

git remote add origin https://github.com/%username%/%repo%
git remote
git remote --v

//it push origin main

//branch 확인
origin	https://github.com/%username%/%repo% (fetch)
origin	https://github.com/%username%/%repo% (push)
git branch * main


```
