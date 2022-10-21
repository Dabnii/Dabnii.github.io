# <p align="center"> 📅 Date method

## ⏰ 지금 시간을 알아보자! Basic way


```java script
let d;

d = new Date();

console.log(d.toString());
// Fri Oct 21 2022 22:07:41 GMT+0900 (한국 표준시)
```

```java script
let today = new Date()
let birthday = new Date('December 17, 1995 03:24:00')
let birthday = new Date('1995-12-17T03:24:00')
let birthday = new Date(1995, 11, 17)            // 월은 0부터 시작
let birthday = new Date(1995, 11, 17, 3, 24, 0)

//MDN의 date 만드는 법
//https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date
```

- milliseconds since January 1st 1970 UTC

```java script
d = new Date();
d = new Date(1164411006456);
// 밀리초를 입력하여 문자열로 변환 

console.log(d.toString())
//Sat Nov 25 2006 08:30:06 GMT+0900 (한국 표준시)

```

## 📌 DATE 생성자 | **[Constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#constructor)**

`[Date()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/Date)`

함수로 호출할 경우 `new Date().toString()`과 동일하게 현재 날짜와 시간을 나타내는 문자열을 반환합니다.

`[new Date()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/Date)`

생성자로 호출할 경우 새로운 `Date` 객체를 반환합니다.

<br>

## 📌 DATE [정적 메서드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date#%EC%A0%95%EC%A0%81_%EB%A9%94%EC%84%9C%EB%93%9C) |**[Static methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#static_methods)**

`[Date.now()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/now)`1970년 1월 1일 00:00:00 UTC로부터 지난 시간을 밀리초 단위의 숫자 값으로 반환합니다. 윤초는 무시합니다.`[Date.parse()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/parse)`날짜를 나타내는 문자열을 분석한 후, 해당 날짜와 1970년 1월 1일 00:00:00 UTC의 시간 차이를 밀리초 단위의 숫자 값으로 반환합니다.

<br>

## ⏰ 세세하게 설정해보자! +UTC

```java script
d = new Date ("2010-01-04T11:30:00+09:00")
//             "년-월-일 T구분선T 시:분:초+GMT+0900(한국표준시)

console.log(d.toString())
//Mon Jan 04 2010 11:30:00 GMT+0900 (한국 표준시)
```

## ⏰ (년, 월, 일, 시간, 분, 초 )

```java script
d = new Date (2019, 7, 2, 11, 30, 27,0)

console.log(d.toString())

//Fri Aug 02 2019 11:30:27 GMT+0900 (한국 표준시)
```

### ⏰ 조금 더 간결하게 설정해보자!

```java script
let date3 = new Date(2019, 5, 1);
console.log(date3.toString())
//'Sat Jun 01 2019 00:00:00 GMT+0900 (한국 표준시)'
```

## 📅 Year 정보를 얻자!

```java script
d = new Date (2019, 7,2,11,30,27,0)

console.log(d.getFullYear()) // 2019
console.log(d.getMonth()) // 7
console.log(d.getDate()) // 2
console.log(d.getMinutes()) // 30
console.log(d.getSeconds()) // 27
//디바이스의 시간대에 맞춰나옴
```

## ⏰ 시간을 지정해 주자! 

- 데이터 객체를 수정하거나 조정할 때 유용

```java script
d.setMinutes(10);
d.setDate(5)

console.log(d.toString());

1564711827000
1564971027000
'Mon Aug 05 2019 11:10:27 GMT+0900 (한국 표준시)'
```

## 🌎 UTC version of time
   - Coordinated Universal Time/Universal Time Coordinated, UTC
   - 1972년 1월 1일부터 시행된 국제 표준시
   - 1970년 1월 1일 자정을 0 밀리초로 설정하여 기준을 삼아 그 후로 시간의 흐름을 밀리초로 계산 합니다.

- **`toISOString()`**
 메서드는 단순화한 확장 ISO 형식([ISO 8601](http://en.wikipedia.org/wiki/ISO_8601))의 문자열을 반환합니다. 반환값은 언제나 24글자 또는 27글자(각각 **`YYYY-MM-DDTHH:mm:ss.sssZ`** 또는 **`±YYYYYY-MM-DDTHH:mm:ss.sssZ`**)입니다. 시간대는 언제나 UTC이며 접미어 "`Z`"로 표현합니다. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/toISOString">MDN</a>

```javascript
console.log(d.toISOString())

//'2019-08-05T02:10:27.000Z'
```

## 🗣 Local language

- 시간을 표현하는 언어를 설정 할 수 있습니다.
- The **`toLocaleString()`**
 method returns a string with a language-sensitive representation of this date. In implementations with `[Intl.DateTimeFormat` API](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)
 support, this method simply calls `Intl.DateTimeFormat`.

```jsx
console.log(d.toLocaleString("ko-KR")) //'2019. 8. 5. 오전 11:10:27'
console.log(d.toLocaleString("en-US")) //'8/5/2019, 11:10:27 AM'
```

- Time zone 설정!

```javascript
console.log(d.toLocaleString("ko-KR", {
timeZone: "America/Los_Angeles"}))
//'2019. 8. 4. 오후 7:10:27'
```


<hr>

출처:

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleStrin

- https://www.youtube.com/watch?v=-eRsWqwcPuk