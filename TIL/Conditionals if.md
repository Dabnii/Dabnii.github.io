# <p align="center"> 📑 Conditionals | 조건문

## 💡 If

- if 문은 지정한 조건이 참인 경우 명령문(statement)을 실행합니다.
- 조건이 거짓인 경우 또 다른 명령문이 실행 될 수 있습니다.
- Making decisions with code
- `if` Only runs code if given condition is true

```javascript
//Basic syntax
    if (condition)
       statement1
    [else
       statement2]

```

```java script
let rating =3;
if (rating === 3) {
	console.log("you are a superstar!");
}
```

```java script
funtion isEven(num){
	if(num%2==0){
	console.log("even")
	}
}
```

```java script
function evenOrOdd(num) {
  return (num % 2)? "Odd":"Even";
}
//num % 2 !== 0 Could work
//짝수일 때만 even 이라는 값을 노출하라
//num%2 조건문으로 나머지가 0이면 짝수, 1이면 홀수
//정수가 2로 나눠서 0이 나오면 : 짝수
//정수가 2로 나눠서 1이 나오면 : 홀수
```

## 2️⃣ ELSE IF

- if 문이 틀렸을 경우에 else if 문이 작용

```javascript
const dayOfWeek = "Monday";
if (dayOfWeek === "Monday") {
  console.log("Ugg I hate Mondays!");
} else if (dayOfWeek === "Saturday") {
  console.log("yay I love Saturday!");
}
```

```javascript
//0-5 Free
//5-10 child $10
//10-65 adult $20
//65+ senior $10

const age = 8;
if (age < 5) {
  console.log("you are a baby. You get in for free!");
} else if (age < 10) {
  console.log("You are a child. You pay $10");
} else if (age < 65) {
  console.log("You are an adult. you pay $20");
} else {
  console.log("");
}
```

## 3️⃣ ELSE

```javascript
const dayOfWeek = prompt("ENTER A DAY").toLowerCase();

if (dayOfWeek === "monday") {
  console.log("UGHHH I HATE MONDAYS!");
} else if (dayOfWeek === "saturday") {
  console.log("YAY I LOVE SATURDAYS!");
} else if (dayOfWeek === "friday") {
  console.log("FRIDAYS ARE DECENT, ESPECIALLY AFTER WORK!");
} else {
  console.log("MEH");
}
```

```javascript
function getColor(phrase) {
  if (phrase == "stop") {
    console.log("red");
  } else if (phrase == "slow") {
    console.log("yellow");
  } else if (phrase == "go") {
    console.log("green");
  } else {
    console.log("purple");
  }
}
```

## ✚ NESTING | 중첩 If 조건문

We can nest coditionals inside conditionals | 조건문 안에 조건문 넣기

```javascript
const password = prompt("please enter a new password");

// Password must be 6+ characters
if (password.length >= 6) {
  // Password cannot include space
  if (password.indexOf(" ") === -1) {
    //   ^ 비밀번호가 충분히 길때만 실행됨
    console.log("Valid Password!");
  } else {
    console.log("Password cannot contain spaces!");
    //      ^ 충분히 길고 공백이 있다면 실행됨
  }
} else {
  console.log("PASSWORD TOO SHORT! Must be 6+ characters");
}
```

```java script
//수수께끼 조건문
const num = 102; // THIS IS THE ONLY LINE YOU SHOULD CHANGE :)
if (num <= 100) {
  if (num >= 50);
  console.log("Try again! lower");
} else {
  if (num < 103) {
    if (num % 2 === 0) {
      console.log("YOU GOT ME!");
    }
  }
}

```

## 💡 if문 순서의 중요성

```javascript
// 맞는 풀이
// ✨ if 조건문 속 , , 콤마 연산자를 사용하는 것이 아닌 &&을 사용합니다. 
function meetAt(year, month, date) {
  if (year && month && date) {
    return year + "/" + month + "/" + date;
  } else if (year && month) {
    return year + "년 " +  month + "월";
  } else if (year) {
    return year + "년";
  }
}
```

```javascript
//잘못된 풀이
// year 조건이 성립하여 처음 조건에서 멈추었기 때문

function meetAt(year, month, date) {
  if (year){
    return year + “년”;
  } else if (year, month){
    return year + “년” + month + “월”;
  } else if (year , month , date){
    return year + “/” + month + “/” + date;
  }
}
```

> index.js에서 meetAt 함수를 만들어주세요. <br>
> 인자를 세개 받습니다.<br>
>
> 1. 첫번째 인자는 년도에 해당하는 숫자입니다.<br>
> 1. 두번째 인자는 월에 해당하는 숫자입니다.<br>
> 1. 세번째 인자는 일에 해당하는 숫자입니다.<br>
>
> - 년도 인자만 받았을 경우 → "1234년" 과 같은 형식의 문자열을 리턴 해주세요.<br>
> - 년도,월 인자를 받았을 경우 → 년도와 월을 조합해서 "1234년 5월" 과 같은 형식의 문자열을 리턴 해주세요.<br>
> - 년도,월,일 인자를 전부 받았을 경우 → 년도,월,일을 조합해서 "1234/5/6" 과 같은 형식의 문자열을 리턴 해주세요.

<br>
<hr>
출처:

- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/if...else
