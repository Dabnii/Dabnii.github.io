# <p align="center"> 💻 Git Rebase

## 📌 Git rebase

0. `git push`를 끝낸다.

1. 
    ```
    git rebase -i master || (main)
    ```

2. `i` insert
    ```
    pick AAAA BBBB
    s CCCC DDDD
    ```
    1. `i` insert
    1. 첫 번째 커밋만 남기기 위하여 첫 글자를 `s`로 수정
    1. `ESC`
    1. `:wq` 종료
    1. `git push origin [branch name]`
    1. 📌 이미 다수의 커밋이 존재 할 때
        - `git push origin [branch name] -f`
        -  `-f` :force 명령어를 넣어 하나로 정리 


- 최소 3개 정도의 커밋이 생겼을 때 rebase 추천

---