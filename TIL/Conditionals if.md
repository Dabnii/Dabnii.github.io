# <p align="center"> ๐ Conditionals | ์กฐ๊ฑด๋ฌธ

## ๐ก If

- if ๋ฌธ์ ์ง์ ํ ์กฐ๊ฑด์ด ์ฐธ์ธ ๊ฒฝ์ฐ ๋ช๋ น๋ฌธ(statement)์ ์คํํฉ๋๋ค.
- ์กฐ๊ฑด์ด ๊ฑฐ์ง์ธ ๊ฒฝ์ฐ ๋ ๋ค๋ฅธ ๋ช๋ น๋ฌธ์ด ์คํ ๋  ์ ์์ต๋๋ค.
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
//์ง์์ผ ๋๋ง even ์ด๋ผ๋ ๊ฐ์ ๋ธ์ถํ๋ผ
//num%2 ์กฐ๊ฑด๋ฌธ์ผ๋ก ๋๋จธ์ง๊ฐ 0์ด๋ฉด ์ง์, 1์ด๋ฉด ํ์
//์ ์๊ฐ 2๋ก ๋๋ ์ 0์ด ๋์ค๋ฉด : ์ง์
//์ ์๊ฐ 2๋ก ๋๋ ์ 1์ด ๋์ค๋ฉด : ํ์
```

## 2๏ธโฃ ELSE IF

- if ๋ฌธ์ด ํ๋ ธ์ ๊ฒฝ์ฐ์ else if ๋ฌธ์ด ์์ฉ

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

## 3๏ธโฃ ELSE

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

## โ NESTING | ์ค์ฒฉ If ์กฐ๊ฑด๋ฌธ

We can nest coditionals inside conditionals | ์กฐ๊ฑด๋ฌธ ์์ ์กฐ๊ฑด๋ฌธ ๋ฃ๊ธฐ

```javascript
const password = prompt("please enter a new password");

// Password must be 6+ characters
if (password.length >= 6) {
  // Password cannot include space
  if (password.indexOf(" ") === -1) {
    //   ^ ๋น๋ฐ๋ฒํธ๊ฐ ์ถฉ๋ถํ ๊ธธ๋๋ง ์คํ๋จ
    console.log("Valid Password!");
  } else {
    console.log("Password cannot contain spaces!");
    //      ^ ์ถฉ๋ถํ ๊ธธ๊ณ  ๊ณต๋ฐฑ์ด ์๋ค๋ฉด ์คํ๋จ
  }
} else {
  console.log("PASSWORD TOO SHORT! Must be 6+ characters");
}
```

```java script
//์์๊ป๋ผ ์กฐ๊ฑด๋ฌธ
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

## ๐ก if๋ฌธ ์์์ ์ค์์ฑ

```javascript
// ๋ง๋ ํ์ด
// โจ if ์กฐ๊ฑด๋ฌธ ์ , , ์ฝค๋ง ์ฐ์ฐ์๋ฅผ ์ฌ์ฉํ๋ ๊ฒ์ด ์๋ &&์ ์ฌ์ฉํฉ๋๋ค. 
function meetAt(year, month, date) {
  if (year && month && date) {
    return year + "/" + month + "/" + date;
  } else if (year && month) {
    return year + "๋ " +  month + "์";
  } else if (year) {
    return year + "๋";
  }
}
```

```javascript
//์๋ชป๋ ํ์ด
// year ์กฐ๊ฑด์ด ์ฑ๋ฆฝํ์ฌ ์ฒ์ ์กฐ๊ฑด์์ ๋ฉ์ถ์๊ธฐ ๋๋ฌธ

function meetAt(year, month, date) {
  if (year){
    return year + โ๋โ;
  } else if (year, month){
    return year + โ๋โ + month + โ์โ;
  } else if (year , month , date){
    return year + โ/โ + month + โ/โ + date;
  }
}
```

> index.js์์ meetAt ํจ์๋ฅผ ๋ง๋ค์ด์ฃผ์ธ์. <br>
> ์ธ์๋ฅผ ์ธ๊ฐ ๋ฐ์ต๋๋ค.<br>
>
> 1. ์ฒซ๋ฒ์งธ ์ธ์๋ ๋๋์ ํด๋นํ๋ ์ซ์์๋๋ค.<br>
> 1. ๋๋ฒ์งธ ์ธ์๋ ์์ ํด๋นํ๋ ์ซ์์๋๋ค.<br>
> 1. ์ธ๋ฒ์งธ ์ธ์๋ ์ผ์ ํด๋นํ๋ ์ซ์์๋๋ค.<br>
>
> - ๋๋ ์ธ์๋ง ๋ฐ์์ ๊ฒฝ์ฐ โ "1234๋" ๊ณผ ๊ฐ์ ํ์์ ๋ฌธ์์ด์ ๋ฆฌํด ํด์ฃผ์ธ์.<br>
> - ๋๋,์ ์ธ์๋ฅผ ๋ฐ์์ ๊ฒฝ์ฐ โ ๋๋์ ์์ ์กฐํฉํด์ "1234๋ 5์" ๊ณผ ๊ฐ์ ํ์์ ๋ฌธ์์ด์ ๋ฆฌํด ํด์ฃผ์ธ์.<br>
> - ๋๋,์,์ผ ์ธ์๋ฅผ ์ ๋ถ ๋ฐ์์ ๊ฒฝ์ฐ โ ๋๋,์,์ผ์ ์กฐํฉํด์ "1234/5/6" ๊ณผ ๊ฐ์ ํ์์ ๋ฌธ์์ด์ ๋ฆฌํด ํด์ฃผ์ธ์.
	
### ์ผํ ์ฐ์ฐ์  
์ผํ ์ฐ์ฐ์๋ ๊ฐ๊ฐ์ ํผ์ฐ์ฐ์๋ฅผ ์ผ์ชฝ์์ ์ค๋ฅธ์ชฝ ์์๋ก ํ๊ฐํ๊ณ , `๋ง์ง๋ง ์ฐ์ฐ์์ ๊ฐ์ ๋ฐํ`ํฉ๋๋ค.



<br>
<hr>
์ถ์ฒ:

- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/if...else
