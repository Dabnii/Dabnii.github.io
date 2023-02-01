# <p align="center"> Programmers Lv.0

## Warming up tests

```javascript
//mine
function solution(num1, num2) {
  var answer = 0;
  return (answer = num1 - num2);
}
```

```javascript
//Better!
const solution = (num1, num2) => num1 - num2;
```

```javascript
const solution = (num1, num2) => {
  if (0 <= num1 <= 100 && 0 <= num2 <= 100) {
    return num1 * num2;
  }
};
```

- `const solution = (num1, num2) => num1 * num2;` 로 풀어도 좋겠지만, 조건이 주어졌을 때 조건을 엄격히 따르는 것도 중요하다. 나는 에러가 싫다.. 🫡

```javascript
const solution = (num1, num2) => {
  return (answer = num1 === num2 ? 1 : -1);
};
```

```jsx
const solution = numbers => numbers.map(number => number * 2);
```

---

<br>

## <p align="center">📚 최빈값 구하기</p>

<p align="center">📆2023/01/13

```jsx
최빈값은 주어진 값 중에서 가장 자주 나오는 값을 의미합니다. 정수 배열 array가 매개변수로 주어질 때, 최빈값을 return 하도록 solution 함수를 완성해보세요. 최빈값이 여러 개면 -1을 return 합니다.
```

## 🧩 Answer

```javascript
function solution(array) {
  const setArr = [...new Set(array)];
  const obj = {};

  for (let i of setArr) {
    obj[i] = array.filter(item => item === i).length;
  }

  const max = Math.max(...Object.values(obj));
  const answer = Object.keys(obj).filter(key => obj[key] === max);

  return answer.length !== 1 ? -1 : Number(answer);
}
```

### 🙌 풀이 [@Seoya0512](https://github.com/Seoya0512/TIL/blob/master/01_%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8%EC%97%B0%EC%8A%B5/javascript/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4/%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8%EC%9E%85%EB%AC%B8/Day3.md#%ED%95%B4%EA%B2%B0--1)

`key`값 과 `value`를 가지는 객체(Object)를 사용하는 방법을 생각했다.

1. `new Set` 으로 array에 중복을 없앤다.
1. 반복문을 통해 `setArr`의 요소는 key 값으로, 그 요소의 count 숫자 값은 value 값을 가지는 `obj`를 만든다. ✨
1. `Math.max`를 사용해 `obj`의 value값의 최대값을 찾고, 이후 `filter`를 사용해 해당 max값을 가지는 key값을 찾는다.
1. key값이 하나인 경우 그 값을 return 하고 그렇지 않으면, -1을 return 하도록 한다.
   객체의 key와 value를 유연하게 사용함으로 이전 로직 보다 훨씬 간결하고 빠르게 답을 찾을 수 있었다.

### 🌳 성장 포인트

1. `Set()` 중복이 허용되지 않는 객체
   1. `const setArr = [...new Set(array)];`
1. `Object.keys()`
   1. The Object.keys() static method returns an array of a given object's own enumerable string-keyed property names.
1. `filter` & `find` 차이

   1. `find` `첫 번째 요소 값`만 반환
   1. `filter` `판별 함수를 만족하는 요소`들을 배열로 반환

1. `new Set()`

   ```javascript
     for (let i of setArr) {
    obj[i] = array.filter(item => item === i).length;
   }

   1. Create a new JavaScript object.
   2. Loop through the setArr array.
   3. ✨ For each element in the array, check if it’s in the array.
   4. ✨ If it is, increment the count by 1.
   5. ✨ Otherwise, set the count to 1.
   6. Return the object.
   ```

[📎 동기와 함께한 최빈값 풀이! W/@Seoya0512](https://github.com/Seoya0512/TIL/blob/master/01_%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8%EC%97%B0%EC%8A%B5/javascript/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4/%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8%EC%9E%85%EB%AC%B8/Day3.md#problem-2--%EC%B5%9C%EB%B9%88%EA%B0%92-%EA%B5%AC%ED%95%98%EA%B8%B0-)

---

출처:

- [Object.keys()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
- [Array.prototype.filter()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
- [for...in](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...in)
- [자바스크립트에서 Set 활용하기](https://minhanpark.github.io/today-i-learned/javascript-set/)

## <p align="center">📚 중앙값 구하기</p>

<p align="center">📆2023/01/13

```jsx
중앙값은 어떤 주어진 값들을 크기의 순서대로 정렬했을 때 가장 중앙에 위치하는 값을 의미합니다. 예를 들어 1, 2, 7, 10, 11의 중앙값은 7입니다. 정수 배열 array가 매개변수로 주어질 때, 중앙값을 return 하도록 solution 함수를 완성해보세요.
```

## 🧩 Answer

```javascript
const solution = array => {
  array.sort((a, b) => a - b);
  let middleIndex = Math.floor(array.length / 2);
  return array[middleIndex];
};
```

### 🙌 풀이

1. array의 숫자를 오름차 순으로 정렬 합니다.
1. array의 길이를 2로 나누어 중앙 값을 구합니다.
   1. 홀수의 길이이기 때문에 `Math.floor()`숫자와 같거나 작은 정수 중에서 가장 큰 수를 반환
1. return `array[middleIndex]`

### 🌳 성장 포인트

1. `sort()`

   - 배열의 요소를 적절한 위치에 정렬한 후 그 배열을 반환합니다
   - ✨ `arr.sort([compareFunction])`

- ```jsx
  var numbers = [4, 2, 5, 1, 3];
  numbers.sort(function (a, b) {
    return a - b;
  });
  console.log(numbers);
  // [1, 2, 3, 4, 5]
  ```
  ![score +5](https://user-images.githubusercontent.com/110847597/212275422-63469b3b-0336-4ade-91ce-8c1f15839eae.png)

---

출처:

- [Array.prototype.sort()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

> 👏 `+5`점을 얻었다!

---

## <p align="center">📚 각도기</p>

<p align="center">📆2023/01/14

## 🧩 Answer #1

```jsx
// return 과 && 연산자
const solution = angle => {
  return 0 < angle && angle < 90
    ? 1
    : angle === 90
    ? 2
    : 90 < angle && angle < 180
    ? 3
    : angle === 180
    ? 4
    : null;
};
```

### 🧩 Answer #2

```javascript
const solution = angle => {
  let answer = 0;
  if (0 < angle && angle < 90) {
    return 1;
  } else if (angle === 90) {
    return 2;
  } else if (90 < angle && angle < 180) {
    return 3;
  } else if (angle === 180) {
    return 4;
  }
  return answer;
};
```

## 🧩 줍줍 코드들

### 🙌 Better!

```jsx
function solution(angle) {
  return angle < 90 ? 1 : angle === 90 ? 2 : angle < 180 ? 3 : 4;
}
```

### 🙌 Best!

```jsx
function solution(angle) {
  return [0, 90, 91, 180].filter(x => angle >= x).length;
}
// filter를 활용하여 배열의 인덱스를 활용함
// 아마 출제의도와 가장 근접한 것 같다
```

### 🌳 성장 포인트

- 물음표 연산자?를 여러 개 연결하면 복수의 조건을 처리할 수 있습니다.
- `return`을 넣어주는 것 잊지말기

---

출처:

- [📎 다중 ‘?’](https://ko.javascript.info/ifelse#ref-159)

---

## <p align="center">📚 양꼬치</p>

<p align="center">📆2023/01/18

```
머쓱이네 양꼬치 가게는 10인분을 먹으면 음료수 하나를 서비스로 줍니다.
양꼬치는 1인분에 12,000원, 음료수는 2,000원입니다.
정수 n과 k가 매개변수로 주어졌을 때, 양꼬치 n인분과 음료수 k개를 먹었다면 총얼마를 지불해야 하는지 return 하도록 solution 함수를 완성해보세요.
```

## 🧩 Answer #1

```javascript
const solution = (n, k) => {
  let answer = 0;
  if (n >= 10) {
    k -= Math.floor(n / 10);
  }
  return (answer = n * 12000 + k * 2000);
};
```

### 🌳 성장 포인트

- `n % 10 === 0` 을 활용하여, 나머지 연산자를 사용하여 해결하려 했지만, 정확한 답이 나오지 않아 1차 실패. 나머지연산자는 배수확인은 가능했다
- `k -= Math.floor(n / 10)`를 활용하여 양꼬치가 10보다 클 경우를 정수로 반환하여 k 음료수에서 연산된 값만을 빼준다.
- ✨ `Math.floor() == ~~` ~~ tilt 연산자
  - ```jsx
    let num = "293.903";
    console.log(~~num); // 293
    console.log(Math.floor(num)); //293
    ```

## <p align="center">📚 머쓱이보다 키 큰 사람</p>

<p align="center">📆2023/01/21

```javascript
머쓱이는 학교에서 키 순으로 줄을 설 때 몇 번째로 서야 하는지 궁금해졌습니다.
머쓱이네 반 친구들의 키가 담긴 정수 배열 array와 머쓱이의 키 height가 매개변수로 주어질 때,
머쓱이보다 키 큰 사람 수를 return 하도록 solution 함수를 완성해보세요.
```

### 입출력 예

| array                | height | result |
| -------------------- | ------ | ------ |
| [149, 180, 192, 170] | 167    | 3      |
| [180, 120, 140]      | 190    | 0      |

```javascript
const solution = (array, height) => {
  // let combArr = array.concat(height).sort() 😩
  const answer = array.filter(el => el > height).length;
};
```

### 🌳 성장 포인트

- `let combArr = array.concat(height).sort()`
  - 위의 코드가 없어도 된다. 왜냐, 이런 조건이 없다.
  - `filter()` 메소드에서 `height` 보다 큰 값을 출력한다.
  - 전국 메소드 지식 자랑이 되었다.

## <p align="center">📚 문자 반복 출력하기</p>

<p align="center">📆2023/01/21

```javascript
문자열 my_string과 정수 n이 매개변수로 주어질 때,
my_string에 들어있는 각 문자를 n만큼 반복한 문자열을 return 하도록
solution 함수를 완성해보세요.
```

```javascript
const solution = (my_string, n) => {
  return (answer = [...my_string].map(el => el.repeat(n)).join(""));
};
```

### 🌳 성장 포인트

- `repeat()`
  - [📎 repeat MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)
- 직전에 풀었던 문제에서 활용한 `[...]` 스프레드 연산자, 전개구문을 적극 활용
- 어제보다 더 나은 코테를 하는 나!

## <p align="center">📚 머쓱이보다 키 큰 사람</p>

<p align="center">📆2023/01/21

```javascript
정수 배열 numbers가 매개변수로 주어집니다.
numbers의 원소 중 두 개를 곱해 만들 수 있는 최댓값을 return하도록
solution 함수를 완성해주세요.
```

```javascript
const solution = numbers => {
  return (answer =
    numbers.sort((a, b) => b - a)[0] * numbers.sort((a, b) => b - a)[1]);
};
```

## <p align="center">📚 배열 자르기</p>

<p align="center">📆2023/01/21

```javascript
정수 배열 numbers와 정수 num1, num2가 매개변수로 주어질 때,
numbers의 num1번 째 인덱스부터 num2번째 인덱스까지 자른 정수 배열을 return 하도록 solution 함수를 완성해보세요.
```

```javascript
function solution(numbers, num1, num2) {
  return (answer = numbers.slice(num1, num2 + 1));
}
```

## <p align="center">📚 유클리드호제법 </p>

---

The Euclidean algorithm is an ancient and efficient method for finding the greatest common divisor (GCD) of two or more integers. It is named after the Greek mathematician Euclid, who first described it in his book "Elements" over 2,000 years ago. The algorithm works by repeatedly dividing the larger number by the smaller number and taking the remainder until the smaller number becomes zero. The last non-zero remainder is the GCD.

```javascript
To find the GCD of 60 and 48:
1. Divide 60 by 48: 60 / 48 = 1 with a remainder of 12
2. Replace the larger number with the smaller number (48) and the smaller number with the remainder (12)
3. Repeat step 1: 48 / 12 = 4 with a remainder of 0
4. The last non-zero remainder is 12, so the GCD of 60 and 48 is 12.
```

The Euclidean algorithm has many practical applications, such as reducing fractions, solving linear Diophantine equations, and cryptography. It is also the foundation of the extended Euclidean algorithm, which can find the greatest common divisor and the coefficients of the Bézout's identity for two numbers.

> 라고 ChatGPT가 말했다.
