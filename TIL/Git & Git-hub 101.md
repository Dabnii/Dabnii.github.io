# <p align="center"> π» Git & GitHub

## π μμ£Ό μ¬μ©νλ λͺλ Ήμ΄

- ν°λ―Έλ λͺλ Ήμ΄

| λͺλ Ήμ΄        | λ»                      | μ€λͺ                        | νμ©                  |
| ------------- | ----------------------- | --------------------------- | --------------------- |
| cd            | change directory        | ν΄λμ΄λ                    | cd (κ²½λ‘) βΒ .Β ..Β /usr |
| ls            | list segments           | νμ¬ κ²½λ‘ λ΄ νμΌ λͺ©λ‘ μΆλ ₯ | ls -al                |
| pwd           | print working directory | νμ¬ κ²½λ‘ μΆλ ₯              |                       |
| mkdir / rmdir | make directory          | λλ ν λ¦¬ μμ± / μ κ±°        |                       |
| rm            | remove                  | νμΌ / λλ ν λ¦¬ μ κ±°        | rm -rf                |
| cp            | copy                    | νμΌ / λλ ν λ¦¬ λ³΅μ¬        |                       |
| mv            | move                    | νμΌ / λλ ν λ¦¬ μ΄λ        |                       |
| cat           | concatenate             | ν°λ―Έλμ νμΌ λ΄μ© μΆλ ₯     |                       |
| touch         | touch                   | νμΌ μμ± λ° λ μ§μ λ³΄ λ³κ²½  | touch readme.md       |
| chmod         | change mode             | νμΌ / λλ ν λ¦¬ κΆν μ€μ    | chmod u+x readme.md   |

<br>

## π Gitμ λͺ©μ κ³Ό νμμ±

1.  λ²μ  μ»¨νΈλ‘€ μμ€ν
2.  μ΄λ€ νλ‘κ·Έλ¨μ μμ , κ°μ νμ¬ μμ±ν κ²
3.  μ΄μ κ³Ό μ½κ°μ© λ€λ₯Έ λ³νλ€μ κ΅¬λΆνλ νμ
    1. μμ ν  λ λ§λ€ νμΌμ μλ‘ λ§λ€λ©΄ κ΄λ¦¬κ° λΆνΈ
    2. β¨Β μΈμ λ  μ΄μ  λ²μ μ μ½λλ‘ λμκ° μ μμ
    3. β¨Β μ΄λ  κ°λ°μκ° μ΄λ€ μ½λλ₯Ό μμ±νλμ§ νμΈν  μ μλ€
    4. νλμ νλ‘μ νΈλ₯Ό λκ³  μ¬λ¬λͺμ΄ κ°λ°μλ€μ΄ νμν  μ μλ€.

## π Github μ Gitμ μ°¨μ΄μ 

1.  `Git` gitμ μ¬μ©ν νλ‘μ νΈλ€μ μ μ₯μ
2.  κ°λ°μλ€μ Social Network
3.  `git` : νλ‘μ νΈμ λ²μ κ΄λ¦¬λ₯Ό λμμ£Όλ μμ€ν
4.  `GitHubβ Git`μ μ΄μ©ν΄ λ²μ κ΄λ¦¬λ₯Ό ν νλ‘μ νΈλ€μ κ΄λ¦¬νκ² ν΄μ£Όλ `νΈμ€νΈ μλΉμ€`

## π Gitμ init, add, status, commit, log, push λͺλ Ήμ΄μ μ­ν 

1.  `git init` β g it μ μ₯μ μμ± / λ²μ  κ΄λ¦¬λ₯Ό μν μ λ³΄ μμ±
    - λ²μ κ΄λ¦¬λ₯Ό νκ³ μΆμ λλ ν λ¦¬μμ ν΄λΉ λͺλ Ήμ΄ μλ ₯
    - ν΄λΉ `git` μ μ κ·Όνμ¬ μ€μν μ λ³΄λ₯Ό νΈμ νμ§ μλλ‘ μ£Όμ
2.  `git add` β νμΌ μμ  μ΄λ ₯ κΈ°λ‘ μ€λΉ e.g. μ₯λ°κ΅¬λ
    - μμ ν νμΌμ μ΄λ ₯μ λ¨κΈΈ μ€λΉλ₯Ό νλ λͺλ Ήμ΄
    - `git add [νμΌμ΄λ¦]` νΉμ  νμΌ μ΄λ ₯μ λ¨κΈ°κ³  μΆμ λ
    - `git add .` λ³κ²½λ νμΌμ μ μ²΄ μ΄λ ₯μ λ¨κΈ°κ³  μΆμ λ
3.  `git status` β μνλ₯Ό νμΈν  μ μλ λͺλ Ήμ΄
    - λλ ν λ¦¬μμ μΌμ΄λκ³  μλ μνλ₯Ό νμΈν  μ μλ λͺλ Ήμ΄
4.  `commit` β νμΌ μμ  μ΄λ ₯ κΈ°λ‘ e.g. μ£Όλ¬Ένλ κ² `add β commit`
    - `git commit -m βmsgβ` νμ€λ‘ μ»€λ° λ©μΈμ§λ₯Ό λ¨κΈΈ λ
    - `git commit` μ¬λ¬μ€μ μ»€λ°μ λ¨κΈΈ λ
5.  `log` β e.g.μμμ¦
    - κΈ°λ‘μ μ΄λμ©
6.  `push` β
    - μμ±ν μ½λλ₯Ό μκ²© μ μ₯μμ μλ‘λ
    - μ΄λ ₯μ λ¨κΈ΄ μ½λλ€μ κΉνλΈμ μ¬λ¦¬κ³  μΆμ λ μ¬μ©νλ λͺλ Ήμ΄
    - `git push origin [branch-name]`

## π’ ν°λ―Έλμ μ¬μ©ν κΉ νλΈ μλ‘λ μμ

1.  GitHub λ‘μ»¬ repository μμ±
    - `+` λ²νΌμ λλ¬ μλ‘μ΄ repositoryλ₯Ό μμ±ν©λλ€.
      - README.MD μμ΄ μμ± ν©λλ€.
      - README.MDκ° μλ κ²½μ°
      - β¦or create a new repository on the command line μΉμμμ `6` `git remote add origin https://github.com/%UserName%/%New repo%`λ₯Ό λ³΅μ¬νμ¬ ν°λ―Έλμ μλ ₯ν©λλ€.
1.  `git init`
1.  `git add .`
1.  `git commit` (κ³΅μμ μΌλ‘ κΈ°λ‘ λ¨κΉ/μλ‘λ ν©λλ€)
1.  `git push origin (branch name)`

<hr>

```javascript

pwd
//νμ¬ κ²½λ‘ μΆλ ₯

cd git
//ν΄λμ΄λ

mkdir git
//λλ ν λ¦¬ μμ±

li
// νμ¬ κ²½λ‘ λ΄ νμΌ λͺ©λ‘ μΆλ ₯

π‘ li -al
//νμ¬ κ²½λ‘ λ΄ νμΌ λͺ©λ‘ μΆλ ₯
// μ€μν λ³΄μμ΄λ μ λ³΄κ° μλ ₯μ¬λΆλ₯Ό νν νμΈν΄μΌν¨

touch.md %file Name%.md
//md μμ±

i
// md νμΌμ insert μνλ‘ μ ν ν μλ ₯
:qw
//mdνμΌμ μ μ₯νκ³  λκ°κΈ°

git status
// git
gid add .

git remote add origin https://github.com/%username%/%repo%
git remote
git remote --v

//it push origin main

//branch νμΈ
origin	https://github.com/%username%/%repo% (fetch)
origin	https://github.com/%username%/%repo% (push)
git branch * main

```

| λͺλ Ήμ΄                              | λ»                                        | μ€λͺ                                                                                                                                               | νμ©                             |
| ----------------------------------- | ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| git clone                           | κΉ λ³΅μ                                    | μ κ· repositoryλ₯Ό λ΄ λ‘μ»¬λ‘ κ°μ Έμ€κΈ°                                                                                                               | git clone [%ropo link%]          |
| git branch                          | λλ¦½λ κ°λ° κ³΅κ° μμ±                     | κ°λ°μ, νλ λ³λ‘ λΈλμΉλ₯Ό μ¬μ©ν΄μΌν¨ <br> - e.g. main ννΈ κ°λ°μλ main λΈλμΉλ₯Ό μ¬μ© <br> - e.g. log-in ννΈ κ°λ°μλ log-in λΈλμΉλ₯Ό μ¬μ© <br> | git branch [branch name]         |
| git checkout                        | λΈλμΉλ₯Ό μ΄λ                             | νμ¬ β μ΄λν  λΈλμΉ                                                                                                                               | git checkout [branch name]       |
| git checkout -b                     | λΈλμΉ μμ±κ³Ό ν¨κ» ν΄λΉ λΈλμΉλ‘ checkout | μμ± λ° λΈλμΉ μ΄λ                                                                                                                                | git checkout -b [branch]         |
| git pull                            | (μ΄λ―Έ μ‘΄μ¬νλ repo) μ½λ κ°μ Έμ€κΈ°        | GitHubμ νΉμ  λΈλμΉμ μ½λλ₯Ό κ°μ Έμ¬ λ μ¬μ©                                                                                                       | git pull origin [branch name]    |
| git merge                           | μ½λ ν©μΉκΈ°                               | λ‘μ»¬μμ νμ¬ λΈλμΉμ μ½λμ νΉμ  λΈλμΉμ μ½λλ₯Ό ν¨μΉ  λ μ¬μ©                                                                                    | git merge [branch name]          |
| git pull                            | GitHubμμ κ°μ Έμ¬ λΈλμΉ μ΄λ¦             | GibHub Master β Local Master                                                                                                                       | git pull [branch]                |
| git stash                           | git μμμ μ₯                              | λΈλμΉ μ΄λμ μν μμμ μ₯                                                                                                                        | git stash                        |
| git stash show -p <br> git apply -R | stash λλλ¦¬κΈ°                            | stashλ₯Ό λλλ¦°λ€                                                                                                                                   | git stash show -p , git apply -R |
| git remote -v                       | git remote Ref μ‘°ν                       | μ°κ²° λμ΄μλ μκ²© λ νμ§ν λ¦¬ νμΈ                                                                                                                 | git remote -v                    |
| git remote remove origin            | μ°κ²° λμ΄μλ μκ²© λ νμ§ν λ¦¬ μ­μ         | μ°κ²° λμ΄μλ μκ²© λ νμ§ν λ¦¬ μ­μ                                                                                                                  | git remote remove origin         |

## π Vscode μμ ν°λ―Έλμ μ΄μ΄λ³΄μ!

- `Cmd + J`

## πΒ Git Repoλ₯Ό ν°λ―Έλμ μ΄μ©νμ¬ clone

```jsx

cd desktop
//ν΄λμ΄λ λ£¨νΈμμ λ°μ€ν¬νμΌλ‘
pwd
//μ΄λ μμΉμΈμ§ νμΈ νκΈ°
git clone https://github.com/%repolink%reponame.git
// κΉνλΈμ repository λ§ν¬λ₯Ό λ£μ΅λλ€
Cloning into '%Repo%'...
... [λ€μ΄λ‘λ]
// λ€μ΄λ‘λκ° λ©λλ€
```

## πΒ git clone

- μ½λ λ³΅μ  (μ κ· | λ΄ λ‘μ»¬μ μλ€λ μ μ )
- κΈ°μ‘΄ repositoryλ₯Ό λ΄ λ‘μ»¬λ‘ κ°μ Έμ€λ λͺλ Ήμ΄
- `git clone [%ropo link%]`

## πΒ git branch

- λλ¦½λ κ³΅κ° λ§λ€κΈ°
- λλ¦½μ μΌλ‘ κ°λ°μ ν  μ μλ κ³΅κ°μ λ§λλ λͺλ Ήμ΄
- `git branch [branch name]`
- λͺ¨λ main/master λΈλμΉλ₯Ό μ¬μ©νλ€λ©΄ μ½λκ° κΌ¬μ΄κ² λ¨
- μμ μ΄μ λ‘, κ°λ°μ λ§λ€ κ°λ³μ λΈλμΉμμ μμν΄μΌν¨
  - e.g. main ννΈ κ°λ°μλ main λΈλμΉλ₯Ό μ¬μ©
  - e.g. log-in ννΈ κ°λ°μλ log-in λΈλμΉλ₯Ό μ¬μ©

## πΒ git checkout

- λΈλμΉλ₯Ό μ΄λν  λ μ¬μ©
- νμ¬ μλ λΈλμΉμμ λ€λ₯Έ λΈλμΉλ‘ μ΄λν  λ μ¬μ©νλ λͺλ Ήμ΄
- `git checkout [branch name]`
- git branchμ λ€λ₯Έ κ°λ β νν checkout ν΄μ£Όμ΄μΌ ν¨!
  - π― `git checkout -b [branch]` μμ±κ³Ό λμμ μ²΄ν¬μμ κ°λ₯

## πΒ git pull

- μ½λ κ°μ Έμ€κΈ° (μ΄λ―Έ μ‘΄μ¬νλ repository)
- githubμ μλ νΉμ  λΈλμΉμ μ½λλ₯Ό λ‘μ»¬λ‘ κ°μ Έμ¬ λ μ¬μ©νλ λͺλ Ήμ΄
  - git clone : μλ‘μ΄/λ‘μ»¬μ μ‘΄μ¬νμ§ μλ μ μ²΄ μ½λλ₯Ό κ°μ Έμ€λ κ²
- `git pull origin [branch name]`

## πΒ git merge

- μ½λ ν©μΉκΈ°
- λ‘μ»¬μμ νμ¬ λΈλμΉμ μ½λμ νΉμ  λΈλμΉμ μ½λλ₯Ό ν©μΉ  λ μ¬μ©
- λμ νμ¬ μμΉ λΈλμΉμμ λ€λ₯Έ λΈλμΉλ₯Ό ν©μΉ  λ
- `git merge [branch name]`
- λ΄ λΈλμΉμ κΉνλΈμ μ½λ λ³ν©
- PR νλ¨μ μ»¨ν μ΄ν mergeλ²νΌμ΄ νμ±ν λ¨
  - μ μ½μ΄ μμ
  - λ¨Έμ§λ΄λΉμκ° λ°λ‘ μμ githubμμλ

## πΒ git pull

- κΉνλΈμμ λ°μ€κ³  μΆμ λΈλμΉ μ΄λ¦
- `git pull [branch]`
- λ§μ€ν°λ‘ μ΄λνμ¬ μ΅μ ν λμ΄ μλ μ½λλ₯Ό κ°μ Έμ΄
- κΉνλΈ λ§μ€ν°λ₯Ό β λ‘μ»¬ λ§μ€ν°λ‘ κ°μ Έμ€κΈ°
- π― `git pull [branch]` ν λΈλμΉλͺ μλ΅μ μ§μ... μκΈ°μΉ λͺ»ν μ€λ₯λ₯Ό μΌκΈ°!

## πΒ git stash

- ποΈ μμλ¬Ό μμ μ μ₯ν  μ μλ λͺλ Ήμ΄
- μλ£νμ§ μμ μμμ commitνμ§ μκ³  λ€μ κΊΌλ΄μ λ§λ¬΄λ¦¬ ν  μ μμ
- β οΈ stash μ΄ν μ§ννλ μμμ λ°λΌ μμλ¬Όμ΄ μ°λλκ±°λ, μ­μ λ  μ μμΌλ μ£Όμ νμ.

## πββοΈΒ Master(Main) μμμ μ§μ!

- Master(Main)κ° κΈ°λ₯
- master(Main)λ₯Ό κΈ°μ€μΌλ‘ branchκ° νμ₯ λμ΄μΌ ν¨
- Vscode μ’μΈ‘ νλ¨μ νμΈ κ°λ₯
- branch μμλ‘ νμΈ!
- λ°°ν¬ν  λ λ§μ€ν° μ½λλ‘ μ§νλκΈ° λλ¬Έμ μμ πββοΈ

```jsx
git branch BranchName/foloderName
git branch BranchName/foloderName
* master //νμ¬ λ΄κ° μλ λΈλμΉ

git checkout BranchName/foloderName
//λΈλμΉλ‘ μ΄λ
//μμ±νλ€κ³  ν΄μ λ°λ‘ κ·Έ λλ ν λ¦¬/λΈλμΉλ‘ μ΄λνμ§ μκΈ° λλ¬Έ
// μ΄λ€ μμμ ν κ²μΈμ§μ λ°λΌ 'feature' λ₯Ό fixλ‘ λ°κΎΈμ΄μ λ³λ
// feature/ μμν  κΈ°λ₯
git checkout BranchName/foloderName
//Switched to branch 'BranchName/foloderName'
git add .
//
git commit -m "ADD:md νμΌμμ± "
// ADD:md νμΌμμ±

git push origin BranchName/foloderName

git push origin BranchName/foloderName

git checkout master
//Switched to branch 'master'
//Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
git pull origin master
git checkout BranchName/foloderName

Switched to branch 'feature/testfile'
//λ΄ λ§μ€ν°λ₯Ό κ°μ Έμμ λ‘μ»¬μ λ¨Έμ§ ν  κ²

```

> Origin λ‘μ»¬μμ  μ¬μ© X | Originμ κΉνλΈμ λ§ν¬λ₯Ό λμ νλ κ²μ΄κΈ° λλ¬Έ

μΆμ²:

- [νλ μμμ μμλ‘ μ μ₯ ν΄λκ³  μΆμ λ μ¬μ©νλ λͺλ Ήμ΄ git stash](https://gmlwjd9405.github.io/2018/05/18/git-stash.html)
