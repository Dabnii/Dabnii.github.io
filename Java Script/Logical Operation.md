# JS-Logical-operators

## JS Logical operators 논리연산자

<hr>

### Logical operators (논리연산자)

논리 연산자는 보통 불리언(논리) 값과 함께 사용해서 불리언 값을 반환합니다.<br>
실제로는 <span style="color:tomato"> `FALSY VALUES` </span> 와 <span style="color:orange"> `TRUTHY VALUES` </span> 의 값중 하나를 반환 하는 것이므로, 둘 중 하나가 불리언 값이 아니라면 논리 연산자의 반환 값도 불리언 값이 아닐 수 있습니다.

### <span style="color:orange">TRUTHY</span> AND <span style="color:tomato">FALSY </span>VALUES

<span style="color:tomato"> `FALSY VALUES` </span>

    - false
    - 0
    - “” (Empty string)
    - Null
    - Undefined
    - NaN

<span style="color:orange"> `TRUTHY VALUES` </span>

    - Everything else is truthy!

<hr>

## 논리연산자의 실행 순서

<span style="color:orange"> `&& AND` </span>
가 먼저 실행 되며 <span style="color:orange"> `|| OR` </span>
가 나중에 실행됩니다.

<hr>

<span style="color:orange"> `&& AND` </span>
Only both sides is true
두가지가 참이어야 참으로 성립

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

<span style="color:orange"> `|| OR` </span>

If one side is true, the entire thing is true <br>
어느 한 쪽이 true라면, 모두가 true가 됨.

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

<span style="color:orange"> `! NOT` </span>

! Expression returns true if expression is false <br>
거짓인 표현식 앞에 넣으면 결과가 참으로 나옴

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

<hr>