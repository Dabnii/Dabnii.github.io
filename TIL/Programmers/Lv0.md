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

## 🧩 Answer

### 🧩 Answer #1

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

### 🧩 Answer #3

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
