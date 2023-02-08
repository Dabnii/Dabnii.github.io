# <p align="center">🔍 Regular expression </p>

<img align="center" src="https://user-images.githubusercontent.com/110847597/217582662-b1f0ffab-4c4f-43b9-9b5a-34d3554949ea.png" alt="reg.Png" width="400px"/>

~~그렇습니다, 제가 제작한 이미지 입니다. 🤓~~

## 💡 Regular expression 101

- `/` 슬래시안에 패턴을 작성합니다

| Flag | Description                                                      |
| ---- | ---------------------------------------------------------------- |
| `g`  | 전역탐색 `global`                                                |
| `d`  | 부분 문자열 일치에 대해 인덱스 생성.                             |
| `i`  | 대소문자를 구분하지 않음. case `i`nsensitive                     |
| `m`  | 여러 줄에 걸쳐 탐색. `multiline`                                 |
| `s`  | 개행 문자가 `.`과 일치함.                                        |
| `u`  | "`u`nicode", 패턴을 유니코드 코드 포인트의 시퀀스로 간주함.      |
| `y`  | "접착 stick`y`" 탐색, 대상 문자열의 현재 위치에서 탐색을 시작함. |

## <p align="center"> 1️⃣ Group and ranges</p>

- `/Hi|Hello/`
  - `|` or 연산자를 사용하여 매칭되는 문자를 찾을 수 있음
- `(/Hi|Hello/)`
  - `()` 소괄호를 사용하여 그룹화 가능
- `(Hi|Hello)|(And)`
  - 그룹 1, 그룹2 를 찾아냄
- `gr(e|a)y`
  - gr로 시작하고 e 또는 a가 있고 y로 끝나는 것
  - 그룹을 기억함
- `gr(?:e|a)y`
  - 위와 같으나, 그룹이나 데이터를 기억하지 않음
- `gr[aed]`
  - 대괄호
  - 해당하는 집합체를 설정 가능
    - 즉, 하나라도 만족할 때!
    - expected answer = grey, gray. grdy
  - `gr[a-f]y`
    - a-f를 포함하는 것들을 찾아라
- `[a-ZA-Z0-9]`
  - 다양한 집합체들을 사용할 수 있다
- `[^a-ZA-Z0-9]`
  - 해당 집합체들이 아닌
  - `NOT` 을 찾을 때 `^`

## <p align="center"> 2️⃣ Quantifies</p>

- `/gra?y/`
  - 있거나, 없거나 (zero || one)
- `/gra*y/`
  - 없거나 있거나 많거나 (zero || more)
- `/gra+y/`
  - 하나 또는 많이 (one || more)
- `gra{2}y`
  - `{min}` n반복
  - a가 최소 두개 나오는 조건
- `gra{2,3}y`
  - `{min,}` 최소
  - `{min,max}` 최소, 그리고 최대

## <p align="center"> 3️⃣ Boundary-type</p>

> 대문자는 아님을 뜻함

- `\b` 단어 경계
- `\B` 단어 경게가 `아님`
- `^` 문장의 시작
- `$` 문장의 끝

## <p align="center"> 4️⃣ Character classes</p>

> 대문자는 아님을 뜻함

- `\` 특수문자가 `아닌` 문자
- `.` 어떤 글자 (줄바꿈 문자 제외)
- `\d` digit 숫자
- `\D` digit 숫자 `아님`
- `w` word 문자
- `W` word 문자가 `아님`
- `\s` space 공백
- `\S` space 공백 `아님`

### 🤓 코테에 사용한 정규식 되짚어보기

<details> 
    <summary>1️⃣ 숨어있는 숫자의 덧셈(1)</summary>

```javascript
문자열 `my_string`이 매개변수로 주어집니다.
`my_string`안의 모든 자연수들의 합을 return하도록 solution 함수를 완성해주세요.
```

| my_string       | result |
| --------------- | ------ |
| "aAb1B2cC34oOp" | 10     |
| "1a2b3c4d123"   | 16     |

```javascript
const solution = my_string => {
  let reg = /[a-zA-Z ]/gim;
  return my_string
    .replace(reg, "")
    .split("")
    .reduce((a, b) => a + Number(b), 0);
};
```

📌 `let reg = /[a-zA-Z ]/gim`

1. `[a-zA-Z]` 대소문자를 모두 찾는다
1. `g` : global search, 전체를 찾습니다 (하나의 값만을 찾는것이 아님)
1. `i` : Case-insensitive 대소문자 구분 없는 모두 검색
1. `m` : multilines 여러 줄에 걸쳐 탐색
</details>

<details>
<summary>2️⃣ 최댓값과 최솟값</summary>

```jsx
문자열 s에는 공백으로 구분된 숫자들이 저장되어 있습니다.
str에 나타나는 숫자 중 최소값과 최대값을 찾아 이를
"(최소값) (최대값)"형태의 문자열을 반환하는 함수, solution을 완성하세요.
예를들어 s가 "1 2 3 4"라면 "1 4"를 리턴하고,
"-1 -2 -3 -4"라면 "-4 -1"을 리턴하면 됩니다.

- 제한 조건
s에는 둘 이상의 정수가 공백으로 구분되어 있습니다.
```

- 입출력 예

  | s             | return  |
  | ------------- | ------- |
  | "1 2 3 4"     | "1 4"   |
  | "-1 -2 -3 -4" | "-4 -1" |
  | "-1 -1"       | "-1 -1" |

## 🧩 My Answer

```javascript
//두번째 풀이
const solution = s => {
  let num = s.split(/\s/g);
  return Math.min(...num) + " " + Math.max(...num);
};
```

📌 `let num = s.split(/\s/g)`

- `\s` space공백을 `g`전체에서 찾아 삭제

</details>

---

Reference

- [정규 표현식](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Regular_Expressions)
- [정규표현식 , 더이상 미루지 말자 🤩](https://youtu.be/t3M6toIflyQ)
