## <p align="center">📚 최댓값과 최솟값 </p>

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
//첫번째 풀이
const solution = s => {
  let num = s.split(/\s/g).map(digit => {
    return Math.floor(digit);
  });
  let min = Math.min(...num);
  let max = Math.max(...num);
  return (answer = `${min} ${max}`);
};
```

```javascript
//두번째 풀이
const solution = s => {
  let num = s.split(/\s/g);
  return Math.min(...num) + " " + Math.max(...num);
};
```

> 규식이 공부에 심취하여 굳이 써본 `/\s/g` 👩‍💻 <br> `+3` 을 받은 영광스러운 답!
> ![3점을 받았습니다! 하지만 아직 응애](https://user-images.githubusercontent.com/110847597/216099696-3c2251e7-60f6-4ce1-aebe-80784a0c9746.png)

## 🧩 줍줍 Answer

```javascript
//👏👏👏
function solution(s) {
  const arr = s.split(" ");
  return Math.min(...arr) + " " + Math.max(...arr);
}
```

## <p align="center">📚 아이스아메리카노 </p>

```javascript
머쓱이는 추운 날에도 아이스 아메리카노만 마십니다.
아이스 아메리카노는 한잔에 5,500원입니다.
머쓱이가 가지고 있는 돈 money가 매개변수로 주어질 때,
머쓱이가 최대로 마실 수 있는 아메리카노의 잔 수와 남는 돈을
순서대로 담은 배열을 return 하도록 solution 함수를 완성해보세요.
```

| money  | result    |
| ------ | --------- |
| 5,500  | [1, 0]    |
| 15,000 | [2, 4000] |

## 🧩 My Answer

```javascript
function solution(money) {
  let aCoffee = 5500;
  return (answer = [Math.floor(money / aCoffee), money % aCoffee]);
}
```

```javascript
answer[0] = Math.floor(money / aCoffee);
answer[1] = money % aCoffee;
//위의 코드로 더 간결히 작성할 수 있다.
```

## <p align="center">📚 문자열 자르기</p>

```javascript
문자열 my_string과 문자 letter이 매개변수로 주어집니다.
my_string에서 letter를 제거한 문자열을 return하도록 solution 함수를 완성해주세요.
```

| my_string | letter | result  |
| --------- | ------ | ------- |
| "abcdef"  | "f"    | "abcde" |
| "BCBdbe"  | "B"    | "Cdbe"  |

## 🧩 My Answer

```javascript
const solution = (my_string, letter) => {
  return (answer = my_string.split(letter).join(""));
};
```

## <p align="center">📚 문자열 정렬하기 (2)</p>

## 🧩 My Answer

```javascript
const solution = my_string => {
  return (answer = my_string.toLowerCase().split("").sort().join(""));
};
```

> `sort()`는 function 이 아니다!
> `return answer.sort((a,b)=>a,b))` 😩

## 🧩 Better Answer

```javascript
function solution(s) {
  return [...s.toLowerCase()].sort().join("");
}
```

> 스프레드 연산자 활용, 배열안에 문자열을 넣어 바로 `[ 'b', 'c', 'a', 'd' ]`으로 변환 🔥 <br> `split("")` 대체가능

## <p align="center">📚 피자 나눠 먹기 (1)</p>

## 🧩 My Answer

```javascript
// 1차 시도
const solution = n => {
  return (answer = n % 7 === 0 ? Math.floor(n / 7) : Math.ceil(n / 7));
};
```

```javascript
//2차 시도!
const solution = n => {
  return (answer = Math.ceil(n / 7));
};
```

## <p align="center">📚 점의 위치 구하기 </p>

## 🧩 My Answer

```javascript
const solution = dot => {
  switch (true) {
    case dot[0] > 0 && dot[1] > 0:
      return 1;
    case dot[0] < 0 && dot[1] > 0:
      return 2;
    case dot[0] < 0 && dot[1] < 0:
      return 3;
    case dot[0] > 0 && dot[1] < 0:
      return 4;
  }
};
```

#### `switch (true) { }` `true` ✨

> The use of `return` in a `switch` statement immediately terminates the execution of the `switch` statement and returns the specified value. In this case, `break` _statements are not necessary._
> 별안간 `switch`에 꽂힌 사람 됨

## 🧩 줍줍 Answer

```javascript
function solution(dot) {
  const [num, num2] = dot;
  const check = num * num2 > 0;
  return num > 0 ? (check ? 1 : 4) : check ? 3 : 2;
}
```
