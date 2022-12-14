# <p align="center"> ๐ For loop

## ๐ Loops allow us to repeat code

- print โhelloโ 10 times
- Sum all numbers in an array

<br>

## ์๋ฐ์คํฌ๋ฆฝํธ๊ฐ ์ง์ํ๋ ๋ฐ๋ณต๋ฌธ

1. for ๋ฌธ
1. do...while ๋ฌธ
1. while ๋ฌธ
1. ๋ ์ด๋ธ ๋ฌธ
1. break ๋ฌธ
1. continue ๋ฌธ
1. for...in ๋ฌธ
1. for...of ๋ฌธ

## โ ๊ธฐ๋ณธ ๊ตฌ๋ฌธ

```java script
for (
		[initialExpression];
		[condition];
		[increantExpession]
)
```

### ์์ ์ฝ๋

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

+) `Pseudocode`๋ฅผ ์ํํ!

### ์, ์ด์  ๊ธฐ๋ณธ์ ๋. ์ค์  ์ฝ๋๋ก ๋์! ๐ฅ

<br>

> ์์ฅ์ ๋ด์๋๋ฐ ๋ฐ๊ตฌ๋๋ฅผ ๋ณด๋ ๊ณฐํก์ด๊ฐ ํผ์ด์์ต๋๋ค. <br>
> ๋ฐ๊ตฌ๋์์ ๊ณฐํก์ด๋ฅผ ์ ๊ฑฐํ๋ ํจ์๋ฅผ ์์ฑํด์ฃผ์ธ์!

<br>

## ๐ป For loop test #1

```java script
let basket = [['์ํ','๊ณฐํก์ด'],['๊ณฐํก์ด','๋นต','๋ธ๊ธฐ์ผ'],['๊ทค','๊ณฐํก์ด','์ฌ๊ณผ']];

function removeGerm(arr) {
  // ์ฌ๊ธฐ์ ์ฝ๋๋ฅผ ์์ฑํด์ฃผ์ธ์!
  for( i=0; i<arr.length; i++) {
    for( j=0; j<arr[i].length; j++)
      if(arr[i][j] === '๊ณฐํก์ด') {
        arr[i].splice(j, 1)
      }
  }
  return arr;
}

console.log(removeGerm(basket))
//๋งค๊ฐ๋ณ์ arr๋ก ์์ฑํ๋ ๊ฒ์ด ์ค์๐ก
```

```java script
//Splice
array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

```java script
๐ก ํต์ฌ ์ฝ๋
arr[i].splice(j, 1)
// arr[i]์ j๋ฅผ 1๊ฐ ์ญ์ 
```

<hr>

## ๐ป For loop test #2

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

> ๊ฐ๋จํ์ง๋ง ๋ง์ ์๊ฐ์ ํ๋น ํ ๊ตฌ๊ฐ. <br>
> ํต์ฌ์ `strArray.push(str[i])` <br>
> ๊ฐ๋จํ์ง๋ง ๊ธฐ๋ณธ์ ๋์ณ์ ์์ฌ์์ด ์ปธ๋ค.<br>
> โฐ ์๊ฐ์ ๋ ํจ์จ์ ์ผ๋ก ์ฐ์!

<br>
<hr>
<br>

## ๐ป For loop test #3

๐ก pseudocode

- HelloBot ํจ์๋ฅผ ์ฌ์ฉ
- For๋ฌธ ์ฌ์ฉ
- result ๋ฐฐ์ด์ greetings์ ๋ค์ด์๋ ์ธ์ฟ๋ง์ ์ฑ์ฐ๊ธฐ
- ์ธ์๋ `0` ๊ณผ `1`
- 0 = '์๋ํ์ธ์'
- 1 = '๋ ๋ง๋๋ค์'
- Empty array `result` + `push` string
- `if 0 = 'Hi'` `else = 'again'`

```Java script
let group1 = [0,1,1,0,0]

const helloBot = people => {
  let result = [];
  for (let i= 0 ; i < people.length; i++){
    if (people[i] == 0){
       result.push('์๋ํ์ธ์')
    } else {
      result.push('๋ ๋ง๋๋ค์')
    }
  } return result;
}

console.log(helloBot(group1))
```

> pseudocode์ฝ๋๋ก ์ ๋ฆฌํ๊ณ  ๋์ ํ์ฌ ๋ ๋ฒ ๋ง์ test pass! ๐ <br>
> people๋ ๋งค๊ฐ๋ณ์ ์ด๋ฆ์ด๋ค. ๐คซ
>
> > ์ฒซ ์๋์ ๋ฌด์์  group1 ๋ฐฐ์ด์ ๋ฃ์ด ๋ถ์์ ํ์.
> > <br>

## ๐ป For loop test #4

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

> findSmallestElement ํจ์๋ฅผ ๊ตฌํํด ์ฃผ์ธ์.

- `findSmallestElement`ย ์ย `arr`ย ์ธ์๋ ์ซ์ ๊ฐ์ผ๋ก๋ง ์ด๋ฃจ์ด์ง ๋ฐฐ์ด์๋๋ค.
- `arr`ย ์ ๊ฐ๋ค ์ค ๊ฐ์ฅ ์์ ๊ฐ์ ๋ฆฌํด ํด์ฃผ์ธ์.
- ๋ง์ผย `arr`ย ๊ฐ ๋น์ด์์ผ๋ฉด 0์ ๋ฆฌํด ํด์ฃผ์ธ์.
- ์๋ฅผ ๋ค์ด, ๋ค์๊ณผ ๊ฐ์ ๋ฐฐ์ด์ด ์ธ์(input)์ผ๋ก ๋ค์ด์๋ค๋ฉด 1์ด ๋ฆฌํด ๋์ด์ผ ํฉ๋๋ค.
  - `for (let i = 0; i <= arr.length; i++)` โจ
  - ์ญ๋ฐฉํฅ for โจ

<hr>

### ์ค๋์ ๊ตํ: ์ฝ๋๋ฅผ ๋ฌด์์  ์ฐ์ง ๋ง๊ณ  `pseudocode`๋ก ๋ผ๋ฆฌ๋ฅผ ์ ๋ฆฌํ์.

๋-.
