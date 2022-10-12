# Array `[A,r,r,a,y]`

## 배열 Array : 여러개의 `데이터`가 `순서`를 가지고 나열 된 집합

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

## Array의 기본 형태

- 0부터 시작합니다
- `[N]`

```Java script
let solfege =
['Do','re','Mi','fa']
// 0---1---2---3---4
```

```Java script
days [Monday. Tuesday, Wednesday];
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

//cna change like this 배열 []을 사용하면 요소를 바꿀 수 있음
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
//0번 배열에 num 0  + num 1 concat

console.log(makeNewArr())
```

### Inclues ➕

불리언 메서드 `True` or `false`

```jsx
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
cats.indexOf("kitty");
// 0

cats.indexOf("wow") - 1; //none
```

### Reverse 🔁

원본 배열을 변경함

```Java script
cats.reverse()
['meow','kitty']
```

### slice ✂️

`arr.slice([*begin*[, *end*]])`

- 배열의 일부를 복사 하는 방법
- 원본 배열 변경
- 정수는 정방향
- 음수는 역방향

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

```Java script
const airplaneSeats = [
    ['Ruth', 'Anthony', 'Stevie'],
    ['Amelia', 'Pedro', 'Maya'],
    ['Xavier', 'Ananya', 'Luis'],
    ['Luke', null, 'Deniz'],
    ['Rin', 'Sakura', 'Francisco']
];

airplaneSeats [3] [1] ='Hugo';
// 3번쨰 배열의 1번을 휴고로 변경
```

### Filter

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

> filter hard class

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

## Splice ⌫

- 인덱스 위치에 있는 항목 제거하기

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
```

<hr>

출처:

- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array
