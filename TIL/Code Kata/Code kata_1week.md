# <p align="center">📖 Code Kata

<p align="center"> 📆 2022.Oct.30 | 55min<br>

## Week 1 | test #1

`twoSum`함수에 숫자배열과 `'특정 수'`를 인자로 넘기면, 더해서 `'특정 수'`가 나오는 `index`를 배열에 담아 return해 주세요.

> `nums: 숫자 배열` <br>`target: 두 수를 더해서 나올 수 있는 합계`<br> `return: 두 수의 index를 가진 숫자 배열`<br>
> 예를 들어,<br>
> nums은 [4, 9, 11, 14] target은 13<br>
> nums[0] + nums[1] = 4 + 9 = 13 입니다.<br>
> 그러하여 `[0, 1]`이 return 되어야 합니다.<br>
> 💡 가정 : target으로 보내는 합계의 조합은 배열 전체 중에 `2개 밖에 없다고 가정`하겠습니다.

<br>

## 💬 pseudocode

1. return 값을 담을 array 생성
1. for문을 사용하여 array를 순회
1. 두 값을 비교해야하므로 두개의 for 문 작성
1. 📌 중복되는 값을 빼기
1. e.g. [4, 9, 11, 14] `target`은 `13`

   | i   | j   | note     |
   | --- | --- | -------- |
   | 4   | 4   | X : 중복 |
   | 4   | 9   | `O`      |

1. e.g. [4, 9, 11, 14] `target`은 `20`

   | i   | j   | note     |
   | --- | --- | -------- |
   | 9   | 4   | X        |
   | 9   | 9   | X : 중복 |
   | 9   | 11  | `O`      |
   | 9   | 14  | X        |

- 위의 표를 참고하면 중복되는 값들은 `i=j`를 빼주어 불필요한 값을 삭제
  - A : ` for (let j = i + 1; j < nums.length; j++) { if (nums[i] + nums[j] === target)`
  - B : ` if (i < j) { if (nums[i] + nums[j] === target)`

```javascript
// 2차 풀이 ✅
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
//1차 풀이 ✅
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

## 🌳 성장 포인트

- 중첩 for문을 사용
  - 사전 스터디 때 배열 속 배열 값을 제거하는 코드를 복기
- `1차코드` result가 이미 array이기 때문에 push 메소드 사용이 불필요하다
- 두 값을 비교할 때 `if (nums[i] + nums[j] === target)` 방법과 `(let j = i + 1; j < nums.length; j++)` 등 여러 표현법을 학습
- 함수가 아닌 선언문이어도 `console.log(func(arg,arg));` 사용가능.

<br>
<hr>
<p align="center"> 📆 2022.Oct.31 | 1h<br>

## Week 1 | test #2

> ### Q.1
>
> reverse 함수에 정수인 숫자를 인자로 받습니다.<br> 그 숫자를 뒤집어서 return해주세요.<br>
> x: 숫자 return: 뒤집어진 숫자를 반환!<br>예들 들어, x: 1234 return: 4321<br>
> x: -1234 return: -4321<br>
> x: 1230 return: 321

`💡 핵심 키워드 : 음수인 경우는 결과값이 다시 음수가 되어야 한다.`

```javascript
//3차 풀이
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
//2차 풀이
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
//1차 풀이 반쪽짜리 코드
// for문을 역방향으로 순회한 시도는 좋았으나 음수를 입력시 NaN 오류 발생 🤔
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

## 🌳 성장 포인트

- `아는만큼 간결해지는 코드`
- 인라인으로 메소드들을 연결하는 방법을 학습
  - 숫자 → 문자열
    - `toString()`
    - `String()`
    - `toFixed()`
    - `${number1}`
  - 역방향:
    - `For loop`
      - `result = makePositive.toString().split("").reverse().join("")`
    - `reverse()`
  - 문자열 → 숫자
    - `Number()`
    - `parseInt()`
    - `typeof`
    - `parseFloat()`
- 코드는 아는 만큼 쓸 수 있다.
- 끈기 있게, 실팰해도 console.log를 찍어보며 한 줄 한 줄 최선을 다하여 작성했다. 기톡 + 1

<hr>
