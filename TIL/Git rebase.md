# <p align="center"> 💻 Git Rebase

## 📌 Git rebase

0. `git push`를 끝낸다.

1. ```
   git rebase -i master || (main)
   ```

2. `i` insert

   ```
   pick AAAA BBBB
   s CCCC DDDD
   ```

   1. `i` insert
   1. 첫 번째 커밋만 남기기 위하여 첫 글자를 `s`로 수정
      1. `s`는 `squash` = use commit, but meld into previous commit
   1. `ESC`
   1. `:wq` 종료
   1. `git push origin [branch name]`
   1. 📌 이미 다수의 커밋이 존재 할 때
      - `git push origin [branch name] -f`
      - `-f` :force 명령어를 넣어 하나로 정리

- 최소 3개 정도의 커밋이 생겼을 때 rebase 추천

## 📌 Git rebase `noop?!`

- 많아진 git commit을 리베이스 하려 했는데, 아래와 같은 오류를 만났다.
- 9개의 commit이 있지만 위의 케이스와 다르게 `noop`이 나왔다.

```
noop

# Rebase c947bec..7e259d3 onto c947bec
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x <cmd>, exec <cmd> = Run a shell command <cmd>, and stop if it fails
#
# If you remove a line here THAT COMMIT WILL BE LOST.
# However, if you remove everything, the rebase will be aborted.
#
```

## 💡 Git rebase `noop` Solution

```
//git rebase -i HEAD~Number
git rebase -i HEAD~7
```

1. `~Number` number 자리에 커밋 범위를 입력
   > `rebase -i` without a commit range will not display any commits. to rebase the last, say, 7 commits use the following:
1. Happy rebase 🥳

---

E.O.D

출처:

- [Git interactive rebase no commits to pick](https://stackoverflow.com/questions/6485508/git-interactive-rebase-no-commits-to-pick)

---

## 🦄 git rebase `Reword`

#### 이미 작성된 커밋메세지를 리베이스 하며 바꿔보자!

1. `git rebase -i HEAD~number`
   1. 변경하려는 각 커밋 메시지 앞에서 `pick`를 🪄`reword`로 변경
2. `reword 0c39034 Better Commit message`
3. `git push origin main -f`
4. ✨ 끗-!

Ref:

- [이전 또는 여러 커밋 메시지 수정](https://docs.github.com/ko/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/changing-a-commit-message#amending-older-or-multiple-commit-messages)

---
