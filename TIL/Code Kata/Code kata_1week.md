# <p align="center">๐ Code Kata

<p align="center"> ๐ 2022.Oct.30 | 55min<br>

## Week 1 | test #1

`twoSum`ํจ์์ ์ซ์๋ฐฐ์ด๊ณผ `'ํน์  ์'`๋ฅผ ์ธ์๋ก ๋๊ธฐ๋ฉด, ๋ํด์ `'ํน์  ์'`๊ฐ ๋์ค๋ `index`๋ฅผ ๋ฐฐ์ด์ ๋ด์ returnํด ์ฃผ์ธ์.

> `nums: ์ซ์ ๋ฐฐ์ด` <br>`target: ๋ ์๋ฅผ ๋ํด์ ๋์ฌ ์ ์๋ ํฉ๊ณ`<br> `return: ๋ ์์ index๋ฅผ ๊ฐ์ง ์ซ์ ๋ฐฐ์ด`<br>
> ์๋ฅผ ๋ค์ด,<br>
> nums์ [4, 9, 11, 14] target์ 13<br>
> nums[0] + nums[1] = 4 + 9 = 13 ์๋๋ค.<br>
> ๊ทธ๋ฌํ์ฌ `[0, 1]`์ด return ๋์ด์ผ ํฉ๋๋ค.<br>
> ๐ก ๊ฐ์  : target์ผ๋ก ๋ณด๋ด๋ ํฉ๊ณ์ ์กฐํฉ์ ๋ฐฐ์ด ์ ์ฒด ์ค์ `2๊ฐ ๋ฐ์ ์๋ค๊ณ  ๊ฐ์ `ํ๊ฒ ์ต๋๋ค.

<br>

## ๐ฌ pseudocode

1. return ๊ฐ์ ๋ด์ array ์์ฑ
1. for๋ฌธ์ ์ฌ์ฉํ์ฌ array๋ฅผ ์ํ
1. ๋ ๊ฐ์ ๋น๊ตํด์ผํ๋ฏ๋ก ๋๊ฐ์ for ๋ฌธ ์์ฑ
1. ๐ ์ค๋ณต๋๋ ๊ฐ์ ๋นผ๊ธฐ
1. e.g. [4, 9, 11, 14] `target`์ `13`

   | i   | j   | note     |
   | --- | --- | -------- |
   | 4   | 4   | X : ์ค๋ณต |
   | 4   | 9   | `O`      |

1. e.g. [4, 9, 11, 14] `target`์ `20`

   | i   | j   | note     |
   | --- | --- | -------- |
   | 9   | 4   | X        |
   | 9   | 9   | X : ์ค๋ณต |
   | 9   | 11  | `O`      |
   | 9   | 14  | X        |

- ์์ ํ๋ฅผ ์ฐธ๊ณ ํ๋ฉด ์ค๋ณต๋๋ ๊ฐ๋ค์ `i=j`๋ฅผ ๋นผ์ฃผ์ด ๋ถํ์ํ ๊ฐ์ ์ญ์ 
  - A : ` for (let j = i + 1; j < nums.length; j++) { if (nums[i] + nums[j] === target)`
  - B : ` if (i < j) { if (nums[i] + nums[j] === target)`

```javascript
// 2์ฐจ ํ์ด โ
const twoSum = (nums, target) => {
  let result = [];
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
};
console.log(twoSum([11, 14, 4, 9], 13));
```

```javascript
//1์ฐจ ํ์ด โ
const twoSum = (nums, target) => {
  let result = [];
  for (let i = 0; i < nums.length; i++) {
    for (let j = 0; j < nums.length; j++) {
      if (i < j) {
        if (nums[i] + nums[j] === target) {
          console.log(i);
          console.log(j);
          result.push(i);
          result.push(j);
        }
      }
    }
  }
  return result;
};
console.log(twoSum([11, 14, 4, 9], 13));
```

## ๐ณ ์ฑ์ฅ ํฌ์ธํธ

- ์ค์ฒฉ for๋ฌธ์ ์ฌ์ฉ
  - ์ฌ์  ์คํฐ๋ ๋ ๋ฐฐ์ด ์ ๋ฐฐ์ด ๊ฐ์ ์ ๊ฑฐํ๋ ์ฝ๋๋ฅผ ๋ณต๊ธฐ
- `1์ฐจ์ฝ๋` result๊ฐ ์ด๋ฏธ array์ด๊ธฐ ๋๋ฌธ์ push ๋ฉ์๋ ์ฌ์ฉ์ด ๋ถํ์ํ๋ค
- ๋ ๊ฐ์ ๋น๊ตํ  ๋ `if (nums[i] + nums[j] === target)` ๋ฐฉ๋ฒ๊ณผ `(let j = i + 1; j < nums.length; j++)` ๋ฑ ์ฌ๋ฌ ํํ๋ฒ์ ํ์ต
- ํจ์๊ฐ ์๋ ์ ์ธ๋ฌธ์ด์ด๋ `console.log(func(arg,arg));` ์ฌ์ฉ๊ฐ๋ฅ.

<br>
<hr>
<p align="center"> ๐ 2022.Oct.31 | 1h<br>

## Week 1 | test #2

> ### Q.1
>
> reverse ํจ์์ ์ ์์ธ ์ซ์๋ฅผ ์ธ์๋ก ๋ฐ์ต๋๋ค.<br> ๊ทธ ์ซ์๋ฅผ ๋ค์ง์ด์ returnํด์ฃผ์ธ์.<br>
> x: ์ซ์ return: ๋ค์ง์ด์ง ์ซ์๋ฅผ ๋ฐํ!<br>์๋ค ๋ค์ด, x: 1234 return: 4321<br>
> x: -1234 return: -4321<br>
> x: 1230 return: 321

`๐ก ํต์ฌ ํค์๋ : ์์์ธ ๊ฒฝ์ฐ๋ ๊ฒฐ๊ณผ๊ฐ์ด ๋ค์ ์์๊ฐ ๋์ด์ผ ํ๋ค.`

```javascript
//4์ฐจ ํ์ด
const reverse = (x) => {
  let resultNums = parseInt(x.toString().split("").reverse().join(""));
  โจ return x >= 0 ? resultNums : -resultNums;
};

console.log(reverse(-1234)); // -4321
console.log(reverse(9876)); //6789
```

- ์ผํญ์ฐ์ฐ์
- `parseInt` ๋ฌธ์์ด์ ์ ์๋ก ๋ฐํ
- `Math.abs()`

```javascript
//3์ฐจ ํ์ด
const reverse = (x) => {
  let makePositive = x * -1;
  if (x < 0) {
    result = makePositive.toString().split("").reverse().join("");
    return Number(result * -1);
  } else {
    result = x.toString().split("").reverse().join("");
    return Number(result);
  }
};

reverse(5678); //5678
reverse(-1234); //-4321
```

```javascript
//2์ฐจ ํ์ด
const reverse = (x) => {
  let makePositive = x * -1;
  if (x < 0) {
    result = makePositive.toString().split("").reverse().join("");
    return Number(result * -1);
  }
  if (x >= 0) {
    result = x.toString().split("").reverse().join("");
    return Number(result);
  }
};

reverse(0); //0
reverse(2345); //2345
reverse(-9876); //-6789
```

```javascript
//1์ฐจ ํ์ด ๋ฐ์ชฝ์ง๋ฆฌ ์ฝ๋
// for๋ฌธ์ ์ญ๋ฐฉํฅ์ผ๋ก ์ํํ ์๋๋ ์ข์์ผ๋ ์์๋ฅผ ์๋ ฅ์ NaN ์ค๋ฅ ๋ฐ์ ๐ค
const reverse = (x) => {
  let numToString = x.toString(); //'1234'
  let strToArr = numToString.split(""); //arr
  let newArr = [];

  for (let i = strToArr.length - 1; i >= 0; i--) {
    newArr.push(strToArr[i]);
  }
  let result = newArr.join("");
  console.log(result);
  return Number(result);
};
reverse(5678);
```

## ๐ณ ์ฑ์ฅ ํฌ์ธํธ

- `์๋๋งํผ ๊ฐ๊ฒฐํด์ง๋ ์ฝ๋`
- ์ธ๋ผ์ธ์ผ๋ก ๋ฉ์๋๋ค์ ์ฐ๊ฒฐํ๋ ๋ฐฉ๋ฒ์ ํ์ต
  - `result = makePositive.toString().split("").reverse().join("")`
- ์ซ์ โ ๋ฌธ์์ด :
  - `toString()`
  - `String()`
  - `toFixed()`
  - `${number1}`
- ์ญ๋ฐฉํฅ:
  - `For loop`
    - `(let i = strToArr.length - 1; i >= 0; i--)`
  - `reverse()`
- ๋ฌธ์์ด โ ์ซ์ :
  - `Number()`
  - `parseInt()`
  - `typeof`
  - `parseFloat()`
- ๋๊ธฐ ์๊ฒ, ์คํจํด๋ console.log๋ฅผ ์ฐ์ด๋ณด๋ฉฐ ํ ์ค ํ ์ค ์ต์ ์ ๋คํ์ฌ ์์ฑํ๋ค. ๊ธฐํน + 1

<hr>

<p align="center"> ๐ 2022.Nov.3 | 10min<br>

## Week 1 | test #4

> ์ซ์์ธ num์ ์ธ์๋ก ๋๊ฒจ์ฃผ๋ฉด, ๋ค์ง์ ๋ชจ์์ด num๊ณผ ๋๊ฐ์์ง ์ฌ๋ถ๋ฅผ ๋ฐํํด์ฃผ์ธ์.<br>
> num: ์ซ์ return: true or false (๋ค์ง์ ๋ชจ์์ด num์ ๋๊ฐ์์ง ์ฌ๋ถ)<br>
> ์๋ฅผ ๋ค์ด, num = 123 return false => ๋ค์ง์ ๋ชจ์์ด 321 ์ด๊ธฐ ๋๋ฌธ<br>
> num = 1221 return true => ๋ค์ง์ ๋ชจ์์ด `1221` ์ด๊ธฐ ๋๋ฌธ<br>
> num = -121 return false => ๋ค์ง์ ๋ชจ์์ด 121- ์ด๊ธฐ ๋๋ฌธ<br>
> num = 10 return false => ๋ค์ง์ ๋ชจ์์ด 01 ์ด๊ธฐ ๋๋ฌธ<br>

`๐ก ํต์ฌ ํค์๋ : 123321๊ฒฝ์ฐ๋ ๋ค์ง์ด๋, ๋ค์ง์ง ์์๋ ๊ฐ์ ๋ชจ์์ด๋ค!`

```javascript
const sameReverse = (num) => {
  let reverse = num.toString().split("").reverse().join("");
  return num == reverse ? true : false;
};
```

## ๐ณ ์ฑ์ฅ ํฌ์ธํธ

- ์ธ์ง์ ๊ธฐ์ต์ ๋ค๋ฅด๋ค! ๋ณต๊ธฐ์ ์ค์์ฑ
- 2๋ฒ ๋ฌธ์ ์ ์ฐ๊ด๋๋ ์ฝ๋ํ์คํธ
