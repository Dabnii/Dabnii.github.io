# <p align="center"> Programmers Lv.0

## Q.1

<p align="center"> 2023/01/12 ⏰ 3min

- 정수 num1과 num2가 주어질 때, num1에서 num2를 뺀 값을 return하도록 soltuion 함수를 완성해주세요.

```jsx
//mine
function solution(num1, num2) {
  var answer = 0;
  return (answer = num1 - num2);
}
```

```jsx
//Better!
const solution = (num1, num2) => num1 - num2;
```

```jsx
const solution = (num1, num2) => {
  if (0 <= num1 <= 100 && 0 <= num2 <= 100) {
    return num1 * num2;
  }
};
```

- `const solution = (num1, num2) => num1 * num2;` 로 풀어도 좋겠지만, 조건이 주어졌을 때 조건을 엄격히 따르는 것도 중요하다. 나는 에러가 싫다.. 🫡

```jsx
const solution = (num1, num2) => {
  return (answer = num1 === num2 ? 1 : -1);
};
```

```jsx
const solution = numbers => numbers.map(number => number * 2);
```
