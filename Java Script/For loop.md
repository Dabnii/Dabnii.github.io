# <p align="center"> 🔁 For loop

## 🔁 Loops allow us to repeat code

- print ‘hello’ 10 times
- Sum all numbers in an array

<br>

## 자바스크립트가 지원하는 반복문

1. for 문
1. do...while 문
1. while 문
1. 레이블 문
1. break 문
1. continue 문
1. for...in 문
1. for...of 문

## ✅ 기본 구문

```java script
for (
		[initialExpression];
		[condition];
		[increantExpession]
)
```

### 예시 코드

```java script
//start at 1 | stop at 10 | add 1 each time
for ( let i =1; i <= 10; i ++) {
		console.log(i);
}

// Print out "Da ba dee da ba daa" 6 times |  using a for loop
for ( let i =1; i <= 6; i ++) {
	console.log("Da ba dee da ba daa");
}

// start at 100 | stop at 0 | take away 10 each time
for ( let i =100; i >= 0; i -=10) {
	console.log(i);
}
// start at 10 | stop at 100 | multiply i each time
for ( let i =10; i <= 100; i *=10) {
	console.log(i);
}
```

<br>

# Code tests & quick review

+) `Pseudocode`를 생활화!

### 자, 이제 기본은 끝. 실전 코드로 돌입! 🔥

<br>

> 시장을 봐왔는데 바구니를 보니 곰팡이가 피어있습니다. <br>
> 바구니에서 곰팡이를 제거하는 함수를 작성해주세요!

<br>

## 💻 For loop test #1

```java script
let basket = [['양파','곰팡이'],['곰팡이','빵','딸기잼'],['귤','곰팡이','사과']];

function removeGerm(arr) {
  // 여기에 코드를 작성해주세요!
  for( i=0; i<arr.length; i++) {
    for( j=0; j<arr[i].length; j++)
      if(arr[i][j] === '곰팡이') {
        arr[i].splice(j, 1)
      }
  }
  return arr;
}

console.log(removeGerm(basket))
//매개변수 arr로 작성하는 것이 중요💡
```

```java script
//Splice
array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

```java script
💡 핵심 코드
arr[i].splice(j, 1)
// arr[i]의 j를 1개 삭제
```

<hr>

## 💻 For loop test #2

```java script
function getAllLetters(str) {
  let strArray = [];

  for (let i = 0; i < str.length; i++) {
    strArray.push(str[i]);
  }

  return strArray;
// ['R', 'a', 'd', 'a', 'g', 'a', 's', 't']
}
```

> 간단하지만 많은 시간을 허비 한 구간. <br>
> 핵심은 `strArray.push(str[i])` <br>
> 간단하지만 기본을 놓쳐서 아쉬움이 컸다.<br>
> ⏰ 시간을 더 효율적으로 쓰자!

<br>
<hr>
<br>

## 💻 For loop test #3

💡 pseudocode

- HelloBot 함수를 사용
- For문 사용
- result 배열에 greetings에 들어있는 인삿말을 채우기
- 인자는 `0` 과 `1`
- 0 = '안녕하세요'
- 1 = '또 만나네요'
- Empty array `result` + `push` string
- `if 0 = 'Hi'` `else = 'again'`

```Java script
let group1 = [0,1,1,0,0]

const helloBot = people => {
  let result = [];
  for (let i= 0 ; i < people.length; i++){
    if (people[i] == 0){
       result.push('안녕하세요')
    } else {
      result.push('또 만나네요')
    }
  } return result;
}

console.log(helloBot(group1))
```

> pseudocode코드로 정리하고 도전하여 두 번 만에 test pass! 👏 <br>
> people는 매개변수 이름이다. 🤫
>
> > 첫 시도에 무작정 group1 배열을 넣어 불완전했음.
> > <br>

## 💻 For loop test #4

<br>

```javascript
function findSmallestElement(arr) {
  for (let i = 0; i <= arr.length; i++) {
    if (arr.length < 1) {
      return 0;
    } else if (arr.length >= 1) {
      return Math.min.apply(Math, arr);
    }
  }
}
```

> findSmallestElement 함수를 구현해 주세요.

- `findSmallestElement` 의 `arr` 인자는 숫자 값으로만 이루어진 배열입니다.
- `arr` 의 값들 중 가장 작은 값을 리턴 해주세요.
- 만일 `arr` 가 비어있으면 0을 리턴 해주세요.
- 예를 들어, 다음과 같은 배열이 인자(input)으로 들어왔다면 1이 리턴 되어야 합니다.
  - `for (let i = 0; i <= arr.length; i++)` ✨
  - 역방향 for ✨

<hr>

### 오늘의 교훈: 코드를 무작정 쓰지 말고 `pseudocode`로 논리를 정리하자.

끗-.
