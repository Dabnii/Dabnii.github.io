# <p align="center"> JS-Logical-operators | 논리 연산자

논리 연산자는 보통 불리언(논리) 값과 함께 사용해서 불리언 값을 반환합니다.<br>
실제로는 `FALSY VALUES`와 `TRUTHY VALUES` 의 값중 하나를 반환 하는 것이므로,<br>
둘 중 하나가 불리언 값이 아니라면 논리 연산자의 반환 값도 불리언 값이 아닐 수 있습니다.

| 연산자     | 사용법 | 설명                                                                                                                                                                                                 |
| ---------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `논리 AND` | &&  | expr1 && expr2 expr1을 false로 변환할 수 있으면 expr1을 반환합니다. 그 외의 경우에는 expr2를 반환합니다. <br> 따라서 불리언 값과 함께 사용한 경우, 둘 다 참일 때 true를, 그 외에는 false를 반환합니다.    |
| `논리 OR`  | &#124; &#124;  | expr1 expr2 expr1을 true로 변환할 수 있으면 expr1을 반환합니다. 그 외의 경우에는 expr2를 반환합니다. <br> 따라서 불리언 값과 함께 사용한 경우, 둘 중 하나가 참일 때 true를, 그 외에는 false를 반환합니다. |
| `논리 NOT` | !   | !expr 단일 피연산자를 true로 변환할 수 있으면 false를 반환합니다. <br>그 외에는 true를 반환합니다.                                                                                                       |

> false로 변환할 수 있는 표현식은 평가 결과가 null, 0, NaN, 빈 문자열(""), undefined인 경우입니다.

### 논리연산자의 실행 순서

> `&& AND` ➡️ `|| OR`

<br>

# 💡 `TRUTHY` AND `FALSY VALUES`

## `FALSY VALUES` 🤔

    - false
    - 0
    - “” (Empty string)
    - Null
    - Undefined
    - NaN

## `TRUTHY VALUES` 🙆‍♀️

    - Everything else is truthy!

<br>
<hr>
<br>

## 💡 `&& AND`

### `두가지가 참이어야 참`으로 성립

```java script
true && true -> true
true && false -> false
false && false -> false

1 <= 4 && 'a' === 'a' // T
9 > 10 && 9 <= 9; //F
'abc'.length === 3 && 1+1 === 4; //F
```

```java script
// &&응용버전
const password= prompt ("Enter your password");
if (password >= 6 && password.indexOf('') === -1) {

// 위와 같이 한줄로 축약가능, 1번이 거짓이면 2번은 자동으로 스킵
// 두가지 모두가 참이어야 하는 속성이기 때문에
// -1 은 스페이스가 없다는 속성임

} else {
 console.log ("INCORRECT FORMAT FOR PASSWORD!");
}
```

<hr>

## 💡 `|| OR`

### 어느 한 쪽이 `true라면, 모두가 true`가 됨

```java script
//only one side needs to be true!

1 !== 1 || 10 === 10 //true
10/2 === 5 || null //true
0 || undefined  //false
```

```javascript
// Ticket Price

// 0-5 free
// 5-10 $10
// 10-65 $20
// 65+ free

const age = 100;
if ((age >= 0 && age < 5) || age >= 65) {
  // 나이의 범위를 0-5로 AND로 연결 그리고 FREE 인 5세 65을 ||로 결합

  console.log("FREE");
} else if (age >= 5 && age < 10) {
  console.log("$10");
} else if (age >= 10 && age < 65) {
  console.log("$20");
} else {
  console.log("INVALID AGE!");
}
```

<hr>

## `! NOT`

### ! Expression returns true if expression is false <br>

### `거짓인 표현식 앞에 넣으면 결과가 참`으로 나옴

```java script
!null //true
! (0 === 0) // false
!(3 <= 4) //false
```

```java script
const age = 8;
if (!(age >= 0 && age < 5 || age >= 65)) {
// 0-5세 또는 65세 이상이 '아닌' 사람지정
    console.log("YOU ARE NOT A BABY OR A SENIOR!")
}
```

<hr>

```java script
function isEitherEvenAndLessThan9(num1, num2) {
	if(9 > num1 && num2 < 9){
		if(num1 % 2 == 0 || num2 % 2 == 0) {
			} console.log("true")
	} else {
		console.log("false")
	}
}

isEitherEvenAndLessThan9(8,8)//true
isEitherEvenAndLessThan9(9,10)//false

// 함수의 인자로 숫자 두개가 주어졌을때 함수는 2가지 조건을 검사합니다.
// 우선 두 숫자 중 적어도 하나가 짝수인지 확인합니다.
// 그리고 두 숫자 모두 9보다 작은지를 확인합니다.
// 두 조건을 모두 만족하는 경우만 true를 반환합니다.
```

```java script
function isEitherEvenAndLessThan9(num1, num2) {
  if ((num1 % 2 == 0 || num2 % 2 == 0) && (9 > num1 && num2 < 9)){
    return true;
  }
  else{
    return false;
  }
}
isEitherEvenAndLessThan9(8,8)
```

<br>

```java script
//가독성있게 바꾼 코드
if (age > 65 || (age < 21 && res === "한국"))


//두 번째 해석이 원했던 결과라면 아래와 같이 괄호를 묶어주셔야 합니다.

if ((age > 65 || age < 21) && res === "한국"))
```

<br>

index.js에 있는 가위 바위 보 게임 함수를 아래 조건에 맞게 구현해주세요.

```java script
function rps(player1, player2) {
  if (
    (player2 === "가위" && player1 === "보") ||
    (player2 === "바위" && player1 === "가위") ||
    (player2 === "보" && player1 === "바위")
  ) {
    return "player2";
  } else {
    return "player1";
  }
}
// player2가 이기는 경우의 수가 player1보다 적음을 이용한 코드
// player1이 이기는 경우는 [가위바위보의 승리] 그리고 [비기는 경우]
// 가위바위보승리와 비기는 경우를 else 로 작성
// player1에 승리에 대한 정보가 없지만 짧고 간결함을 추구함 
```

> - `rockPaperScissors` 함수를 구현해서 가위 바위 보 게임을 구현해주세요.
> - **가능하면 || 와 && 연산자 둘다 사용해주세요.**
> - player1과 player2 중 이긴 사람이 누군지 리턴해주세요.
> - 예를 들어, player1이 이겼으면 "player1" 이 리턴 되고 그 반대의 경우라면 "player2"가 리턴이 되어야 합니다.
> - 만일 비기는 경우에는 무조건 "player1"이 리턴 되어야 합니다.
> - player1 과 player2 의 값은 다음 셋 중 하나 입니다.
    - "가위"
    - "바위"
    - "보"
> - 예를 들어, player1은 "가위" 이고 player2는 "보" 이면 "player1" 이 리턴 되어야 합니다.

## 💡 `조건 (삼항) 연산자`

- JavaScript에서 세 개의 피연산자를 취할 수 있는 유일한 연산자
- 맨 앞에 조건문 들어가고. 그 뒤로 물음표(`?`)와 조건이 참`truthy`이라면 실행할 식이 물음표 뒤로 들어갑니다.
- 바로 뒤로 콜론(`:`)이 들어가며 조건이 거짓`falsy`이라면 실행할 식이 마지막에 들어갑니다.
- 보통 `if`명령문의 단축 형태로 쓰입니다.

```java script
condition ? exprIfTrue : exprIfFalse
```

```java script
var status = age >= 18 ? '성인' : '미성년자';
//위의 명령문은 age가 18 이상이라면 status 변수에 "성인"을 할당하고, 그렇지 않으면 "미성년자"를 할당합니다.
```

```java script
function evenOrOdd(num) {
  return (num % 2)? "Odd":"Even";
}
```

```java script
const isSnakeEyes = (die1, die2) => {
	return dies1+die2 ===2 ? "Snake eyes!" : "not Snake eyes!"
}
```

<hr>
출처:

- https://poiemaweb.com/js-operator
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Expressions_and_Operators#%EB%85%BC%EB%A6%AC_%EC%97%B0%EC%82%B0%EC%9E%90
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator
