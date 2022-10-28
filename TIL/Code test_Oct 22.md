# <p align="center">✏️Code test

<p align="center"> 📆 2020.Oct.28 | 1h<br>

## Q.1

```jsx
짝수인지 판별하는 함수 isEven을 작성 주세요.

console.log(isEven(11)) // --> "짝수가 아닙니다."
console.log(isEven(10)) // --> "짝수 입니다."
```

```jsx
function isEven(num) {
  // 아래 코드를 입력해주세요.
  return num % 2 ? "짝수가 아닙니다." : "짝수 입니다.";
}
```

<hr>

## Q.2

```jsx
function calculateTotal(amount) {
  // 아래 코드를 작성해주세요.
  let totalAmount = amount + amount * 0.095 + amount * 0.15;
  return totalAmount;
}

console.log(calculateTotal(30));
```

```jsx
//오류답안
function calculateTotal(amount) {
  // 아래 코드를 작성해주세요.

  let totalAmount = amount + amount(amount * 0.095) + amount(amount * 0.15);
  //amount(arg)를 삽입시 함수가 아니라는 오류가 뜸!
  //당연함

  return totalAmount;
}

console.log(calculateTotal(30));
```

<hr>

## Q.3 ★★★

- `slice` 도 가능!

```jsx
function getPrefix(str) {
  // 아래 코드를 작성하세요.
  return str.split("-")[0];
}
console.log(getPrefix("BTC-KRW"));
```

`split`에 대한 이해가 필요 [[see more]](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/split)

```jsx
//1차 코드
const words = str.split("-");
// 선언할 필요가 없었는데 MDN 파일보고 헷갈렸다
// 유연한 사고가 필요하다
```

<hr>

## Q.4

```jsx
//2차 코드
//else 필요 유무를 알아보자
function getFind(filter, sentence) {
  // 아래 코드를 작성해주세요.
  for (let i = 0; i < sentence.length; i++) {
    if (sentence[i] === filter) {
      return i;
    }
  }
  return -1;
}
```

```jsx
// 1차 혼란스러움
function getFind(filter, sentence) {
  // 아래 코드를 작성해주세요.
 for (let i = 0; i <sentence.length; i++){
   if ( sentence[i] === filter ){
     return sentence[i]
   } else{
     return -1
   }
 }
```

<hr>

> `getFind` 함수를 작성하세요.
>
> 문자와 문자열이 주어졌을때, `getFind` 함수는 주어진 문자열에서 주어진 문자가 나타나는 첫번째 위치를 반환합니다.
>
> **Notes:** 문자열의 첫번째 문자는 인덱스 값 `0` 을 가집니다. 만약 문자열에 해당 문자가 여러번 나타나면, 첫번째로 나타나는 위치를 반환해야 합니다. 만약 문자가 문자열에 존재하지 않는다면, `-1` 을 반환해야 합니다.
>
> **중요!!** `indexOf` 함수를 사용하지 마세요.
>
> ```jsx
> const output = getFind("a", "I am a hacker");
> console.log(output); // --> 2
> ```

- 동기 SY님의 친절한 설명으로 이해 완료 ✅

```jsx
function get_find(filter, sentence) {
  return sentence.search(filter);
}

console.log(get_find("b", "apple")); //-1
console.log(get_find("a", "apple")); //0
```

## Q.5 ★★★★

pseudo code

✨ 가장 긴 길이 배열을 새 배열에 담는다

1.  배열의 길이만큼 배열을 순회 한다
2.  i 만큼 각 배열의 길이를 비교한다
3.  위의 가장 긴 길이 배열에 i 값을 담는다 😎

```jsx
find_longest_word 함수를 만들어 주세요.

주어진 리스트안에 있는 단어중 가장 긴 단어를 찾을수 있도록 함수를 완성해주세요.

console.log(find_longest_word(["PHP", "Exercises", "Backend"]))
// --> "Exercises"
```

```jsx
function find_longest_word(arr) {
  // 아래 코드를 구현해주세요.
  let longest = arr[0]
  // longest arr는 0부터 시작합니다!

  for (let i = 0; i< arr.length; i++){
   ✨ if (arr[i].length > longest.length){
    //i.length가 아님!
	 ✨	longest = arr[i]
    }
  } return longest;
}
```

- if (arr[i].length > longest.length)

<hr>

🌳 Learning Point :

- Prep-study
- 삼항연산자 완벽이해
- split 동작원리 이해
- 원시코드 → 발전된 코드
- pseudocode code ✨

<hr>
E.O.D
