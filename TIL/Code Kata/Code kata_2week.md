# <p align="center">📖 Code Kata

<p align="center"> 📆 2022.Nov.7 | 50min<br>

## Week 2 | test #1

> ### Q.1 로마자에서 숫자로 바꾸기
>
> 1~3999 사이의 로마자 s를 인자로 주면 그에 해당하는 숫자를 반환해주세요. 로마 숫자를 숫자로 표기하면 다음과 같습니다.<br>
>
> ### 💡 Symbol Value<br>
>
> I 1<br>
> V 5<br>
> X 10<br>
> L 50<br>
> C 100<br>
> D 500<br>
> M 1000<br>
> 로마자를 숫자로 읽는 방법은 로마자를 왼쪽부터 차례대로 더하면 됩니다. III = 3 XII = 12 XXVII = 27 입니다.<br>
> 그런데 4를 표현할 때는 IIII가 아니라 IV 입니다. 뒤의 숫자에서 앞의 숫자를 빼주면 됩니다. 9는 IX입니다.
> I는 V와 X앞에 와서 4, 9 X는 L, C앞에 와서 40, 90 C는 D, M앞에 와서 400, 900

### 💡 핵심 키워드 :

- 데이터를 담는 객체를 활용.
- `[]` Bracket Notation 활용.
- IV 4, IX 9 경우는 앞 자리가 뒷 자리보다 작다.
- ✨ 복잡해 보이지만, 간단한 2가지의 조건만 충족 하면 된다.

| s    | i [0]   | i + 1 [1]        | 숫자 |
| ---- | ------- | ---------------- | ---- |
| I    | I (1)   | null             | 1    |
| II   | I (1)   | I (1)            | 2    |
| III  | I (1)   | I (1) ... + I(i) | 3    |
| `IV` | `I (1)` | `V (5)`          | `4`  |
| `IX` | `I (1)` | `X (10)`         | `9`  |

- 1️⃣ : 앞 자리가 뒷 자리 보다 작은 경우 `뒤에서 앞 자리를 뺀다`
- 2️⃣ : 앞 자리가 뒷 자리 보다 큰 경우 더 한다

```javascript
function romanToNum(s) {
  const romeNum = {
    I: 1,
    V: 5,
    X: 10,
    L: 50,
    C: 100,
    D: 500,
    M: 1000,
  };

  let result = 0;

  for (let i = 0; i < s.length; i++) {
    if (romeNum[s[i]] < romeNum[s[i + 1]]) {
      result -= romeNum[s[i]];
      //result  = result - romeNum[s[i]]
    } else {
      result += romeNum[s[i]];
    }
  }
  return result;
}
```

## 🌳 성장 포인트

- `+=` & `-=`

  - `result = result - romeNum[s[i]]`
  - `result = result + romeNum[s[i]]`
  - `0 = 0 - 1 ← i`

- 복잡해 보이는 문제 조건을 간단하게 생각하는 방법
  - 함정에 빠지지 말자 🕳
- 동기들에게 한 수 배우는 날 🙇‍♀️

<br>

---

<p align="center"> 📆 2022.Nov.8 | 1h30mins<br>

## Week 2 | test #2

> ### Q.2 majority, more than a half 찾기
>
> 숫자로 이루어진 배열인 nums를 인자로 전달합니다. <br>
> 숫자중에서 과반수(majority, more than a half)가 넘은 숫자를 반환해주세요. <br> `nums` 배열의 길이는 무조건 `2`개 이상

```js
//예
nums = [3, 2, 3];
return 3;

nums = [2, 2, 1, 1, 1, 2, 2];
return 2;
```

### 💡 핵심 키워드 : `forEach`

```javascript
function moreThanHalf(nums) {
  let numsLength = nums.length;

  const result = {};
  nums.forEach((element) => {
    if (result[element]) {
      result[element] = result[element] + 1;
    } else {
      result[element] = 0 + 1;
    }
  });

  let ans = 0;
  for (let i in result) {
    if (result[i] > numsLength / 2) {
      return i - 0;
    }
  }
}
```

```javascript
//줍줍코드
function moreThanHalf(numbers) {
  const counts = {};

  for (number of numbers) {
    counts[number] = counts[number] + 1 || 1;
  }

  for (number in counts) {
    if (counts[number] > numbers.length / 2) {
      return number - 0;
    }
  }
}
```

1. `for...of`와 `forEach`는 기능은 같다, 가독성의 차이
2. `counts[number] = counts[number] + 1 || 1`
3. lets you skip an if statement too
4. If counts[number] is truthy i.e. if it exists + 1
5. If it doesn't, set the value to 1

<br>

## 🌳 성장 포인트

- `res = 0, count= 0`
- ` return i - 0;` → 문자를 숫자로 `-`
- 코드 수집이 정말 재밌네요.. 같은 문제에 다양한 해석 ✨

<p align="center"> 📆 2022.Nov.9 | 45min<br>

## Week 2 | test #3

> ### Q.3 [string 유효판단] true/false
>
> `s`는 여러 괄호들로 이루어진 String 인자입니다. s가 유효한 표현인지 아닌지 `true/false`로 반환해주세요. <br>
> 종류는 `(', ')`, `[', ']`, `{', '}` 으로 총 `6`개 있습니다. 아래의 경우 유효합니다.
>
> 1. 한 번 괄호를 시작했으면, 같은 괄호로 끝내야 한다.
> 1. 괄호 순서가 맞아야 한다.<br>

```javascript
//예

s = "()";
return true;

s = "()[]{}";
return true;

s = "(]";
return false;

s = "([)]";
return false;

s = "{[]}";
return true;
s = "[]{}";
```

### 💡 핵심 키워드 :

- `includes()` <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/includes">MDN : includes()</a>

  - includes() 메서드는 배열이 특정 요소를 포함하고 있는지 판별합니다.
  - 반환값: `Boolean`

- `replace()` <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replace">MDN : reaplce()</a>

  - replace() 메서드는 어떤 패턴에 일치하는 일부 또는 모든 부분이 교체된 새로운 문자열을 반환

  ```javascript
  var newStr = str.replace(regexp|substr, newSubstr|function)

  ```

```javascript
function isValid(s) {
  while (s.includes("()") || s.includes("[]") || s.includes("{}")) {
    s = s.replace("()", "");
    s = s.replace("[]", "");
    s = s.replace("{}", "");
  }
  return s === "" ? true : false;
}
```

## 🌳 성장 포인트

- `return s === "" ? true : false;`

<p align="center"> 📆 2022.Nov.15 | 5mins<br>

## Q.2

> 문자로 구성된 배열을 input으로 전달하면, 문자를 뒤집어서 return 해주세요.<br>
> 새로운 배열을 선언하면 안 됩니다.<br>
> 인자로 받은 배열을 수정해서 만들어주세요.<br>
> Input: `["h","e","l","l","o"]`<br>
> Output: `["o","l","l","e","h"]`<br>
> Input: `["H","a","n","n","a","h"]`<br>
> Output: `["h","a","n","n","a","H"]`<br>

## A.2

```javascript
const reverseString = (s) => {
  return (reverseOut = s.reverse());
};
```

🫡
