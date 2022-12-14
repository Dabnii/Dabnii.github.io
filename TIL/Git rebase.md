# <p align="center"> ๐ป Git Rebase

## ๐ Git rebase

0. `git push`๋ฅผ ๋๋ธ๋ค.

1. ```
   git rebase -i master || (main)
   ```

2. `i` insert

   ```
   pick AAAA BBBB
   s CCCC DDDD
   ```

   1. `i` insert
   1. ์ฒซ ๋ฒ์งธ ์ปค๋ฐ๋ง ๋จ๊ธฐ๊ธฐ ์ํ์ฌ ์ฒซ ๊ธ์๋ฅผ `s`๋ก ์์ 
      1. `s`๋ `squash` = use commit, but meld into previous commit
   1. `ESC`
   1. `:wq` ์ข๋ฃ
   1. `git push origin [branch name]`
   1. ๐ ์ด๋ฏธ ๋ค์์ ์ปค๋ฐ์ด ์กด์ฌ ํ  ๋
      - `git push origin [branch name] -f`
      - `-f` :force ๋ช๋ น์ด๋ฅผ ๋ฃ์ด ํ๋๋ก ์ ๋ฆฌ

- ์ต์ 3๊ฐ ์ ๋์ ์ปค๋ฐ์ด ์๊ฒผ์ ๋ rebase ์ถ์ฒ

## ๐ Git rebase `noop?!`

- ๋ง์์ง git commit์ ๋ฆฌ๋ฒ ์ด์ค ํ๋ ค ํ๋๋ฐ, ์๋์ ๊ฐ์ ์ค๋ฅ๋ฅผ ๋ง๋ฌ๋ค.
- 9๊ฐ์ commit์ด ์์ง๋ง ์์ ์ผ์ด์ค์ ๋ค๋ฅด๊ฒ `noop`์ด ๋์๋ค.

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

## ๐ก Git rebase `noop` Solution

```
//git rebase -i HEAD~Number
git rebase -i HEAD~7
```

1. `~Number` number ์๋ฆฌ์ ์ปค๋ฐ ๋ฒ์๋ฅผ ์๋ ฅ
   > `rebase -i` without a commit range will not display any commits. to rebase the last, say, 7 commits use the following:
1. Happy rebase ๐ฅณ

---

E.O.D

์ถ์ฒ:

- [Git interactive rebase no commits to pick](https://stackoverflow.com/questions/6485508/git-interactive-rebase-no-commits-to-pick)
