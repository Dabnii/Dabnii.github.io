# <p align="center">π Code Kata

<p align="center"> π 2022.Nov.7 | 50min<br>

## Week 2 | test #1

> ### Q.1 λ‘λ§μμμ μ«μλ‘ λ°κΎΈκΈ°
>
> 1~3999 μ¬μ΄μ λ‘λ§μ sλ₯Ό μΈμλ‘ μ£Όλ©΄ κ·Έμ ν΄λΉνλ μ«μλ₯Ό λ°νν΄μ£ΌμΈμ. λ‘λ§ μ«μλ₯Ό μ«μλ‘ νκΈ°νλ©΄ λ€μκ³Ό κ°μ΅λλ€.<br>
>
> ### π‘ Symbol Value<br>
>
> I 1<br>
> V 5<br>
> X 10<br>
> L 50<br>
> C 100<br>
> D 500<br>
> M 1000<br>
> λ‘λ§μλ₯Ό μ«μλ‘ μ½λ λ°©λ²μ λ‘λ§μλ₯Ό μΌμͺ½λΆν° μ°¨λ‘λλ‘ λνλ©΄ λ©λλ€. III = 3 XII = 12 XXVII = 27 μλλ€.<br>
> κ·Έλ°λ° 4λ₯Ό ννν  λλ IIIIκ° μλλΌ IV μλλ€. λ€μ μ«μμμ μμ μ«μλ₯Ό λΉΌμ£Όλ©΄ λ©λλ€. 9λ IXμλλ€.
> Iλ Vμ Xμμ μμ 4, 9 Xλ L, Cμμ μμ 40, 90 Cλ D, Mμμ μμ 400, 900

### π‘ ν΅μ¬ ν€μλ :

- λ°μ΄ν°λ₯Ό λ΄λ κ°μ²΄λ₯Ό νμ©.
- `[]` Bracket Notation νμ©.
- IV 4, IX 9 κ²½μ°λ μ μλ¦¬κ° λ· μλ¦¬λ³΄λ€ μλ€.
- β¨ λ³΅μ‘ν΄ λ³΄μ΄μ§λ§, κ°λ¨ν 2κ°μ§μ μ‘°κ±΄λ§ μΆ©μ‘± νλ©΄ λλ€.

| s    | i [0]   | i + 1 [1]        | μ«μ |
| ---- | ------- | ---------------- | ---- |
| I    | I (1)   | null             | 1    |
| II   | I (1)   | I (1)            | 2    |
| III  | I (1)   | I (1) ... + I(i) | 3    |
| `IV` | `I (1)` | `V (5)`          | `4`  |
| `IX` | `I (1)` | `X (10)`         | `9`  |

- 1οΈβ£ : μ μλ¦¬κ° λ· μλ¦¬ λ³΄λ€ μμ κ²½μ° `λ€μμ μ μλ¦¬λ₯Ό λΊλ€`
- 2οΈβ£ : μ μλ¦¬κ° λ· μλ¦¬ λ³΄λ€ ν° κ²½μ° λ νλ€

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

## π³ μ±μ₯ ν¬μΈνΈ

- `+=` & `-=`

  - `result = result - romeNum[s[i]]`
  - `result = result + romeNum[s[i]]`
  - `0 = 0 - 1 β i`

- λ³΅μ‘ν΄ λ³΄μ΄λ λ¬Έμ  μ‘°κ±΄μ κ°λ¨νκ² μκ°νλ λ°©λ²
  - ν¨μ μ λΉ μ§μ§ λ§μ π³
- λκΈ°λ€μκ² ν μ λ°°μ°λ λ  πββοΈ

<br>

---

<p align="center"> π 2022.Nov.8 | 1h30mins<br>

## Week 2 | test #2

> ### Q.2 majority, more than a half μ°ΎκΈ°
>
> μ«μλ‘ μ΄λ£¨μ΄μ§ λ°°μ΄μΈ numsλ₯Ό μΈμλ‘ μ λ¬ν©λλ€. <br>
> μ«μμ€μμ κ³Όλ°μ(majority, more than a half)κ° λμ μ«μλ₯Ό λ°νν΄μ£ΌμΈμ. <br> `nums` λ°°μ΄μ κΈΈμ΄λ λ¬΄μ‘°κ±΄ `2`κ° μ΄μ

```js
//μ
nums = [3, 2, 3];
return 3;

nums = [2, 2, 1, 1, 1, 2, 2];
return 2;
```

### π‘ ν΅μ¬ ν€μλ : `forEach`

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
//μ€μ€μ½λ
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

1. `for...of`μ `forEach`λ κΈ°λ₯μ κ°λ€, κ°λμ±μ μ°¨μ΄
2. `counts[number] = counts[number] + 1 || 1`
3. lets you skip an if statement too
4. If counts[number] is truthy i.e. if it exists + 1
5. If it doesn't, set the value to 1

<br>

## π³ μ±μ₯ ν¬μΈνΈ

- `res = 0, count= 0`
- ` return i - 0;` β λ¬Έμλ₯Ό μ«μλ‘ `-`
- μ½λ μμ§μ΄ μ λ§ μ¬λ°λ€μ.. κ°μ λ¬Έμ μ λ€μν ν΄μ β¨

<p align="center"> π 2022.Nov.9 | 45min<br>

## Week 2 | test #3

> ### Q.3 [string μ ν¨νλ¨] true/false
>
> `s`λ μ¬λ¬ κ΄νΈλ€λ‘ μ΄λ£¨μ΄μ§ String μΈμμλλ€. sκ° μ ν¨ν ννμΈμ§ μλμ§ `true/false`λ‘ λ°νν΄μ£ΌμΈμ. <br>
> μ’λ₯λ `(', ')`, `[', ']`, `{', '}` μΌλ‘ μ΄ `6`κ° μμ΅λλ€. μλμ κ²½μ° μ ν¨ν©λλ€.
>
> 1. ν λ² κ΄νΈλ₯Ό μμνμΌλ©΄, κ°μ κ΄νΈλ‘ λλ΄μΌ νλ€.
> 1. κ΄νΈ μμκ° λ§μμΌ νλ€.<br>

```javascript
//μ

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

### π‘ ν΅μ¬ ν€μλ :

- `includes()` <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/includes">MDN : includes()</a>

  - includes() λ©μλλ λ°°μ΄μ΄ νΉμ  μμλ₯Ό ν¬ν¨νκ³  μλμ§ νλ³ν©λλ€.
  - λ°νκ°: `Boolean`

- `replace()` <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replace">MDN : reaplce()</a>

  - replace() λ©μλλ μ΄λ€ ν¨ν΄μ μΌμΉνλ μΌλΆ λλ λͺ¨λ  λΆλΆμ΄ κ΅μ²΄λ μλ‘μ΄ λ¬Έμμ΄μ λ°ν

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

## π³ μ±μ₯ ν¬μΈνΈ

- `return s === "" ? true : false;`

<p align="center"> π 2022.Nov.15 | 5mins<br>

## Q.2

> λ¬Έμλ‘ κ΅¬μ±λ λ°°μ΄μ inputμΌλ‘ μ λ¬νλ©΄, λ¬Έμλ₯Ό λ€μ§μ΄μ return ν΄μ£ΌμΈμ.<br>
> μλ‘μ΄ λ°°μ΄μ μ μΈνλ©΄ μ λ©λλ€.<br>
> μΈμλ‘ λ°μ λ°°μ΄μ μμ ν΄μ λ§λ€μ΄μ£ΌμΈμ.<br>
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

π«‘
