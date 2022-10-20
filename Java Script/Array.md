# <p align="center"> Array `[A,r,r,a,y]`

## <p align=center> 배열 Array : 여러개의 `데이터`가 `순서`를 가지고 나열 된 집합

<a href="https://github.com/BongsikB/BongsikB.github.io/blob/main/Java%20Script/Array.md#object-%EA%B0%9D%EC%B2%B4%EC%99%80-%EB%B0%B0%EC%97%B4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90">📎 배열과 객체의 차이</a> <br>
<a href="https://github.com/BongsikB/BongsikB.github.io/blob/main/Java%20Script/Object.md">📎 Object 객체 포스트 </a>

- Java Script의 `데이터 구조`
- `[]` 사이에 존재
- `순서`를 가짐

```Java script
//To make an empty array
let students = [];

//An array of strings
let colors = ['red', 'orange', 'yellow'];

//An array of numbers
let lottoNums = [19,22,56,12,51];

//A mixed array
let stuff = [ture, 67, 'cat', null];
```

## Array의 기본 형태 ✅

- 0부터 시작
- `[N]`

```Java script
let solfege =
['Do','re','Mi','fa']
// 0----1----2----3
```

```Java script
days [Monday, Tuesday, Wednesday];
"monday"[0] //m
days // 0Monday 1Tuesday 2Wednesday
days [0] // Monday
days [1] [0] // T
```

```Java script
let colors =['red', 'orange', 'green', 'yellow'];

colors[0] ='red';

colors[2] = 'yellow';
colors[3] = 'green';

colors[4] =; //undefined
colors[5] = 'blue';

//배열 []을 사용하여 요소를 바꿀 수 있음
let colors = ['rad', 'orange', 'yalloww'];
colors [0] = 'red' //변경가능

color[10] ='indigo' //추가됨
```

## ARRAY METHODS

| PUSH          | POP             | SHIFT             | UNSHIFT      |
| ------------- | --------------- | ----------------- | ------------ |
| Add to END    | Remove from END | Remove from START | ADD to START |
| 마지막에 추가 | 마지막을 삭제   | 시작을 삭제       | 시작에 추가  |

### Concat

- 2개의 배열을 붙여 제 `3의 배열을 제작`
- 기존의 array를 수정하지 않고 `새로운 배열 제작`

```jsx
// Array-prototype.includes()

let cats= ['Kitty','meow'];
let dogs= ['dal','bong'];
✨ cats.concat(dogs)
// ['Kitty'.'meow','dal','bong']
```

```Java script
let month1 = ['Jan', 'Feb', 'March', 'Apr', 'May', 'June'];
let month2 = ['July', 'Aug', 'Sept', 'Oct', 'Nov', 'Dec'];

function combineMonth() {
    return month2.concat(month1)
}

console.log(combineMonth())

let num = [[11, 12, 13], [14, 15, 16], [17, 18, 19]];

function makeNewArr () {
  return num[0].concat(num[1],num[2]) 👍👍👍
}
//0번 배열에 num 1  + num 2 concat

console.log(makeNewArr())
```

### Inclues ➕

- boolean method
- `True` or `false`

```java script
let cats = ["Kitty", "meow"];
let dogs = ["dal", "bong"];

cats.includes("kitty");
//true;

cats.includes("cheese");
//false;
```

### indexOf() 🔍

- Array 인덱스 배열을 찾아줌
- 반환값이 없다면 `-1` 반환

```Java script
//Basic syntax
arr.indexOf(searchElement[, fromIndex])
```

```Java script
let cats= ['Kitty','meow'];
let dogs= ['dal','bong'];

cats.indexOf("kitty");
// 0

cats.indexOf("wow")
// - 1 none
```

### Reverse 🔁

- 원본 배열을 변경함

```Java script
let cats= ['Kitty','meow'];
let dogs= ['dal','bong'];

cats.reverse()
['meow','kitty']
```

### slice ✂️

`arr.slice([*begin*[, *end*]])`

- `배열의 일부를 복사` 하는 방법
- 원본 배열 변경
- 정수는 `정방향`
- 음수는 `역방향`

```Java script
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// expected output: Array ["camel", "duck"]

console.log(animals.slice());
// expected output: Array ["ant", "bison", "camel", "duck", "elephant"]
```

```java script
const findFruits = () => {
  let foodBox = ['🍕', '🍤','🍇' ,'🥝','🍒','🍉','🍗', '🍟' ];
  let bye = foodBox.slice(2,6);
  //or
  //let bye = foodBox.slice(-6,-2);

  return bye;
}
// [ '🍇', '🥝', '🍒', '🍉' ]
```

```Java script
const airplaneSeats = [
    ['Ruth', 'Anthony', 'Stevie'],
    ['Amelia', 'Pedro', 'Maya'],
    ['Xavier', 'Ananya', 'Luis'],
    ['Luke', null, 'Deniz'],
    ['Rin', 'Sakura', 'Francisco']
];

airplaneSeats [3] [1] = 'Hugo';
// 3번쨰 배열의 1번을 Hugo로 변경
```

## Filter

- 조건에 맞는 요소들만 모아서 `새로운 배열을 반환`
- 만약 조건에 부합되는 요소가 아무것도 없다면 `빈 배열을 반환`

```java script
let fruits = ['apple', 'banana', 'grapes', 'mango', 'orange'];

function filtered() {
  let result = fruits.filter((value) => value.includes('ap'));
  return result;
}

console.log(filtered())
//[ 'apple', 'grapes' ]
```

### Filter 2

```Java script
let courses = [
{level:'easy', subject: "English" },
{level:'hard', subject: "Mathmatic" },
{level:'medium', subject: "Literature" },
{level:'hard', subject: "Science" },
{level:'medium', subject: "Socialogy" }
];

function filtered() {
  let hardCourse = courses.filter((difficult) => difficult.level === 'hard')
  return hardCourse;
}

console.log(filtered())

//[{ level: 'hard', subject: 'Mathmatic' },{ level: 'hard', subject: 'Science' }]
```

## Splice ⌫ [1]

- 인덱스 위치에 있는 항목 제거하기

```java script
//Splice syntax
array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

```java script
let basket = [['양파','곰팡이'],['곰팡이','빵','딸기잼'],['귤','곰팡이','사과']];

function removeGerm(arr) {
  for(i=0; i<arr.length; i++) {
    for(j=0; j<arr[i].length; j++)
      if(arr[i][j] === '곰팡이') {
        arr[i].splice(j, 1)
      }
  }
  return arr;
}

console.log(removeGerm(basket))
// [ [ '양파' ], [ '빵', '딸기잼' ], [ '귤', '사과' ] ];
//매개변수 arr로 작성하는 것이 중요💡
```

## 💡 핵심 코드

```java script
arr[i].splice(j, 1)
// arr[i]의 j를 1개 삭제
```

<br>

## Splice ⌫ [2]

```java script
function getElement() {
  let arr = [3, [4, ["array", 9], 2 + 3], [0]];
  return arr[1][1][0]
}
```

```javascript
function getElement() {
  let arr = [3, [4, ["array", 9], 2 + 3], [0]];
  return arr[1][1][0];
  ss;
}
```

## 💡 핵심 코드

```javascript
myArray.slice(-1)[0];
```

- `slice(-1)`는 마지막 요소만 있는 배열을 리턴하기 때문에, <br>
  배열에서 요소만 가져오려면 아래와 같이 `slice(-1)[0]`으로 가져옴

> Assignment <br>
>
> - `getElement` 함수안에 `arr` 변수를 선언했습니다.
> - `arr` 변수는 배열을 할당했고요, 배열에는 다양한 데이터 타입의 요소가 들어있네요!
> - 배열이 담긴 `arr` 변수에 접근하여 `getElement` 함수가 `"array"` 라는 문자열을 `return` 할 수 있도록 해주세요.

### 2. `addFirstAndLast` 함수를 작성해주세요.

- `addFirstAndLast` 함수에 주어진 인자 `myArray`는 숫자 값으로만 이루어진 array 입니다.
- `addFirstAndLast` 함수에 주어진 인자 `myArray` 의 첫번째 element와 마지막 element의 값을 더한 값을 리턴해주세요.
- 만일 `myArray`에 한 개의 요소만 있다면 해당 요소의 값을 리턴해 주시고 요소가 없는 비어있는 array라면 0을 리턴해주세요.
- Hint) array의 길이를 구하는 방법은 다음을 참조하세요 : [https://community.wecode.co.kr/t/js-array/200/2](https://community.wecode.co.kr/t/js-array/200/2)

## Object 객체와 배열의 차이점

| 객체(Object)                       | 배열(Array)               |
| ---------------------------------- | ------------------------- |
| {Key:value}를 가진 Property의 집합 | 데이터타입 : 순서로 나열  |
| `{ }` 중괄호                       | `[ ]` 대괄호              |
| 순서가 없다                        | 순서가 있다 (순서가 중요) |

<br>

<hr>

출처:

- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array

- https://codechacha.com/ko/javascript-get-last-element-in-array/
