# <p align="center"> π Date & Time method

## β° μ§κΈ μκ°μ μμλ³΄μ! Basic way

## `new Date()`

- μΈμλ₯Ό μ λ¬νμ§ μμΌλ©΄ ν λ μ§μ μκ°μ κ°λ μΈμ€ν΄μ€ λ°ν

```java script
let d;

d = new Date();

console.log(d.toString());
// Fri Oct 21 2022 22:07:41 GMT+0900 (νκ΅­ νμ€μ)
```

```java script
let today = new Date()
let birthday = new Date('December 17, 1995 03:24:00')
let birthday = new Date('1995-12-17T03:24:00')
let birthday = new Date(1995, 11, 17)            // μμ 0λΆν° μμ
let birthday = new Date(1995, 11, 17, 3, 24, 0)

//MDNμ date λ§λλ λ²
//https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date
```

## `new Date(milliseconds)`

- μΈμλ‘ μ«μ νμμ λ°λ¦¬μ΄λ₯Ό μ λ¬νλ©΄ 1970λ 1μ 1μΌ 00:00(UTC)μ κΈ°μ μΌλ‘ μΈμλ‘ μ λ¬λ λ°λ¦¬μ΄λ§νΌ κ²½κ³Όν λ μ§μ μκ°μ κ°μ§λ μΈμ€ν΄μ€λ₯Ό λ°ν ν©λλ€.

- milliseconds since January 1st 1970 UTC

- 86400000msλ 1dayλ₯Ό μλ―Ένλ€.
- 1s = 1,000ms
- 1m = 60s \_ 1,000ms = 60,000ms
- 1h = 60m \_ 60,000ms = 3,600,000ms
- 1d = 24h \* 3,600,000ms = 86,400,000ms

```java script
// KST(Korea Standard Time)λ GMT(κ·Έλ¦¬λμΉ νκ· μ: Greenwich Mean Time)μ 9μκ°μ λν μκ°μ΄λ€.

d = new Date();
d = new Date(1164411006456);
// λ°λ¦¬μ΄λ₯Ό μλ ₯νμ¬ λ¬Έμμ΄λ‘ λ³ν

console.log(d.toString())
//Sat Nov 25 2006 08:30:06 GMT+0900 (νκ΅­ νμ€μ)

```

## π DATE μμ±μ | <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#constructor">[Constructor]</a>

## `Date()`

ν¨μλ‘ νΈμΆν  κ²½μ°Β `new Date().toString()`κ³Ό λμΌνκ² νμ¬ λ μ§μ μκ°μ λνλ΄λ λ¬Έμμ΄μ λ°νν©λλ€.
<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/Date">[see more]</a>

## `new Date()`

μμ±μλ‘ νΈμΆν  κ²½μ° μλ‘μ΄Β `Date`Β κ°μ²΄λ₯Ό λ°νν©λλ€.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/Date">[see more]</a>

<br>

## π DATE | <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#static_methods">[μ μ  λ©μλ]</a>

## `Date.now()`

- 1970λ 1μ 1μΌ 00:00:00 UTCλ‘λΆν° μ§λ μκ°μ λ°λ¦¬μ΄ λ¨μμ μ«μ κ°μΌλ‘ λ°νν©λλ€.
- μ€μ΄λ λ¬΄μν©λλ€.
  <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/now">see more</a>

## `Date.parse`

- λ μ§λ₯Ό λνλ΄λ λ¬Έμμ΄μ λΆμν ν,
- ν΄λΉ λ μ§μ 1970λ 1μ 1μΌ 00:00:00 UTCμ μκ° μ°¨μ΄λ₯Ό λ°λ¦¬μ΄ λ¨μμ μ«μ κ°μΌλ‘ λ°νν©λλ€.<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/parse">see more</a>

<br>

## β° μΈμΈνκ² μ€μ ν΄λ³΄μ! +UTC

```java script
d = new Date ("2010-01-04T11:30:00+09:00")
//             "λ-μ-μΌ Tκ΅¬λΆμ T μ:λΆ:μ΄+GMT+0900(νκ΅­νμ€μ)

console.log(d.toString())
//Mon Jan 04 2010 11:30:00 GMT+0900 (νκ΅­ νμ€μ)
```

## β° (λ, μ, μΌ, μκ°, λΆ, μ΄)

```java script
d = new Date (2019, 7, 2, 11, 30, 27,0)

console.log(d.toString())

//Fri Aug 02 2019 11:30:27 GMT+0900 (νκ΅­ νμ€μ)
```

## β° μ‘°κΈ λ κ°κ²°νκ² μ€μ ν΄λ³΄μ!

```java script
let date3 = new Date(2019, 5, 1);
console.log(date3.toString())
//'Sat Jun 01 2019 00:00:00 GMT+0900 (νκ΅­ νμ€μ)'
```

## π Year μ λ³΄λ₯Ό μ»μ!

```java script
d = new Date (2019, 7,2,11,30,27,0)

console.log(d.getFullYear()) // 2019
console.log(d.getMonth()) // 7
console.log(d.getDate()) // 2
console.log(d.getMinutes()) // 30
console.log(d.getSeconds()) // 27
//λλ°μ΄μ€μ μκ°λμ λ§μΆ°λμ΄
```

## β° μκ°μ μ§μ ν΄ μ£Όμ!

- λ°μ΄ν° κ°μ²΄λ₯Ό μμ νκ±°λ μ‘°μ ν  λ μ μ©

```java script
d.setMinutes(10);
d.setDate(5)

console.log(d.toString());

1564711827000
1564971027000
'Mon Aug 05 2019 11:10:27 GMT+0900 (νκ΅­ νμ€μ)'
```

## π UTC version of time

- Coordinated Universal Time/Universal Time Coordinated, UTC
- 1972λ 1μ 1μΌλΆν° μνλ κ΅­μ  νμ€μ
- 1970λ 1μ 1μΌ μμ μ 0 λ°λ¦¬μ΄λ‘ μ€μ νμ¬ κΈ°μ€μ μΌμ κ·Έ νλ‘ μκ°μ νλ¦μ λ°λ¦¬μ΄λ‘ κ³μ° ν©λλ€.

## π GMT κ·Έλ¦¬μΉλ

- κ·Έλ¦¬λμΉ νκ· μ(Greenwich Mean Time, GMT)
- λ°λμ κΈ°μ , μ°λ§ν΄μ μ’μ μΌλ‘ νλ νμ  μΈκ³μμ λΉ λ₯Έμκ°

- **`toISOString()`**
  Β λ©μλλ λ¨μνν νμ₯ ISO νμ([ISO 8601](http://en.wikipedia.org/wiki/ISO_8601))μ λ¬Έμμ΄μ λ°νν©λλ€. λ°νκ°μ μΈμ λ 24κΈμ λλ 27κΈμ(κ°κ°Β **`YYYY-MM-DDTHH:mm:ss.sssZ`**Β λλΒ **`Β±YYYYYY-MM-DDTHH:mm:ss.sssZ`**)μλλ€. μκ°λλ μΈμ λ UTCμ΄λ©° μ λ―Έμ΄ "`Z`"λ‘ ννν©λλ€. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/toISOString">MDN</a>

```javascript
console.log(d.toISOString());

//'2019-08-05T02:10:27.000Z'
```

## π£ Local language

- μκ°μ νννλ μΈμ΄λ₯Ό μ€μ  ν  μ μμ΅λλ€.
- TheΒ **`toLocaleString()`**
  Β method returns a string with a language-sensitive representation of this date. In implementations withΒ `[Intl.DateTimeFormat`Β API](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)
  Β support, this method simply callsΒ `Intl.DateTimeFormat`.

```jsx
console.log(d.toLocaleString("ko-KR")); //'2019. 8. 5. μ€μ  11:10:27'
console.log(d.toLocaleString("en-US")); //'8/5/2019, 11:10:27 AM'
```

- Time zone μ€μ !

```javascript
console.log(
  d.toLocaleString("ko-KR", {
    timeZone: "America/Los_Angeles",
  })
);
//'2019. 8. 4. μ€ν 7:10:27'
```

<hr>

μΆμ²:

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleStrin

- https://www.youtube.com/watch?v=-eRsWqwcPuk
- https://poiemaweb.com/js-date
