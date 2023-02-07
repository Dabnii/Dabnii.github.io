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

## <p align="center">📚 삼각형의 완성조건 (1)</p>

```javascript
선분 세 개로 삼각형을 만들기 위해서는 다음과 같은 조건을 만족해야 합니다.
가장 긴 변의 길이는 다른 두 변의 길이의 합보다 작아야 합니다.
삼각형의 세 변의 길이가 담긴 배열 sides이 매개변수로 주어집니다.
세 변으로 삼각형을 만들 수 있다면 1,
만들 수 없다면 2를 return하도록 solution 함수를 완성해주세요.
```

| sides          | result |
| -------------- | ------ |
| [1, 2, 3]      | 2      |
| [3, 6, 2]      | 2      |
| [199, 72, 222] | 1      |

## 🧩 My Answer

```javascript
const solution = sides => {
  let sorting = sides.sort((a, b) => a - b);
  return (answer = sorting[0] + sorting[1] > sorting[2] ? 1 : 2);
};
```

#### 😩 중간 코드

```javascript
// return answer = (sides.reduce((accu, curr)=> accu + curr) - Math.max(...sides)) < Math.max(...sides)
```

1. 다시 시작된 `reduce`에 대한 ~~집착~~ 열정.
1. 늘어나는 코드와 더 간단한 로직을 구현하기 위하여 [🧩 My Answer](https://github.com/Dabnii/Dabnii.github.io/blob/main/TIL/Programmers/Lv.0-1%20Feb.md#-my-answer-6) 로 로직 변경
1. `Max`와 `reduce`로 나눠 구성했다면 성공 예상
   1. 코드테스트 꿀잼 ✨ ~~과연 레벨2+ 에서도 이 말을 할까..~~

## 🧩 줍줍 Answer

```javascript
function solution(sides) {
  sides = sides.sort((a, b) => a - b);
  return sides[0] + sides[1] > sides[2] ? 1 : 2;
}
```

> 나와 같은 로직이지만 let 선언이 없음

## 🧩 줍줍 Answer 2

```javascript
function solution(sides) {
  var answer = 0;
  const max = Math.max(...sides);
  const sum = sides.reduce((a, b) => a + b, 0) - max;

  answer = max < sum ? 1 : 2;

  return answer;
}
```

> 스프레드 연산자를 자꾸만 까먹는다면.. 외사랑 `reduce` 등장

## <p align="center">📚 중복된 숫자 개수 </p>

```javascript
정수가 담긴 배열 array와 정수 n이 매개변수로 주어질 때,
array에 n이 몇 개 있는 지를 return 하도록 solution 함수를 완성해보세요.
```

| array              | n   | result |
| ------------------ | --- | ------ |
| [1, 1, 2, 3, 4, 5] | 1   | 2      |
| [0, 2, 3, 4]       | 1   | 0      |

## 🧩 My Answer

```javascript
const solution = (array, n) => {
  return (answer = array.reduce(
    (accu, curr) => (n === curr ? accu + 1 : accu),
    0
  ));
};
```

> 꽤 오래 시간동안 고민한 문제
> `reduce`에 대한 나의 외사랑은... 계속 된다

## 🧩 줍줍 Answer

```javascript
const solution = (array, n) => {
  return array.filter(el => el === n).length;
};
```

> 아마 출제의도는 `filter` 사용이라 생각 됨

## <p align="center">📚 옷가게 할인 받기 </p>

```javascript
머쓱이네 옷가게는 10만 원 이상 사면 5%,
30만 원 이상 사면 10%,
50만 원 이상 사면 20%를 할인해줍니다.

구매한 옷의 가격 price가 주어질 때,
지불해야 할 금액을 return 하도록 solution 함수를 완성해보세요.
```

| price   | result  |
| ------- | ------- |
| 150,000 | 142,500 |
| 580,000 | 464,000 |

## 🧩 My Answer

```javascript
const solution = price => {
  switch (true) {
    case price >= 500000:
      return (answer = price * 0.8);
    case price >= 300000:
      return (answer = price * 0.9);
    case price >= 100000:
      return (answer = price * 0.95);
  }
  return Math.floor(answer);
};
```

> 로직 플로우를 잘 확인해야한다.
> switch에 미치다...🫡

```javascript
const discounts = [
  [500000, 20],
  [300000, 10],
  [100000, 5],
];

const solution = price => {
  for (let discount of discounts) {
    if (price >= discount[0])
      return Math.ceil(price - (price * discount[1]) / 100);
  }
  return price;
};
```

> 할인 기준과 할인율을 배열로 관리

## <p align="center">📚 숨어있는 숫자의 덧셈(1) </p>

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
.