# <p align="center"> 📈 data type

## 💡 Primitive types

- number
- string
- boolean
- null
- undefined
- Symbol (ECMAScript 6 에 추가)
  - ✔️ 별도로 Object(객체)

## typeof 연산자

- `typeof` 연산자를 통해 이 값, 이 변수는 무슨 데이터 타입인지 알 수 있습니다.
- `typeof` 연산자를 적용하면 다음 문자열 중 하나를 반환합니다.
  1. `undefined` : 정의되지 않은 변수
  2. `boolean`
  3. `string`
  4. `number`
  5. `object"`: 함수를 제외한 객체 또는 `object`
  6. `function`
- `typeof` 연산자는 다음과 같이 사용합니다.

```javascript
let msg = "message";

console.log(typeof msg); // "string"
console.log(typeof 100); // "number"
```

## 📈 typeof null

- `typeof null` → `"object"`
- null 이라는 데이터 타입이 `object` 로 반환됩니다.
- null 은 `빈 객체를 참조`하고 있어서 그렇습니다.

## 📈 Array 데이터 타입

```
console.log(typeof [])
```

- 배열의 type을 확인해보면 `"object"`입니다.
- 왜냐하면 `사실 배열은 확장된 객체` 입니다.

## 🔢 Number (숫자)

- Number 라는 데이터 타입은 숫자를 의미합니다.
- Number 타입에서 중요한 것은 **연산**입니다.
- 산술 연산자를 사용하여 Number 타입에 대한 연산은 아래와 같이 작성합니다.

```
1 + 1 // 더하기
2 - 1 // 빼기
2 * 4 // 곱하기
6 / 2 // 나누기
```

- 더하기(+)는 왼쪽 값과 오른쪽 값을 더해서 하나의 값을 만든다는 점에서 `이항 연산자` 라고 부릅니다.
- 이항 연산자 중에서 산수를 하는 것이기 때문에 `산술 연산자`라고 부릅니다.

## 🔤 String (문자열)

- Strings are another primitave type in JavaScrip. They represent text, and must be wrapped in quotes.
- `“”` or `‘’` 항상 쌍으로 필요합니다.
- 산술 연산자를 통해 숫자 데이터 타입을 활용하는 것처럼 문자열 타입에도 다양한 기능이 있습니다.

```javascript
let userdame = "danny";
//username 변수가 문자열로 설정 됨
let firstName = "Zaggy"; // Double quotes work
let msg = "please do no feed the chimps!";
let anmimal = "Dumbo Octopus"; //so do single quotes //with quotes available use space
```

<hr>

### 🔨 `String Methods` | 고유한 기술 [[see more]](https://developer.mozilla.org/ko/docs/Glossary/Method)

Methods are build-in actions we can perform with indiviusal strings

- Searching within a string
- Replacing part of a string
- Changing the casing of a string

### `()` 괄호를 사용하여 접근

```jsx
let msg = "I am king";
let yellMsg = msg.toUpperCase();

let angry = "LeAvE mE aLoNe!";
angry.toLowerCase();
```

## ✂️ `Trim`

### thing.method(arg)| 인수가 있는 문자열 규칙 [[see more]](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

> Some methods accept arguments that modify their hebavior. Think of them as inputs that we can pass in. We pass these arguments inside of the parentheses.

- 인수는 메서드로 전달되어서 메서드의 동작을 변경하는 입력 값

```jsx
let tvShow = "catdog";

tvShow.indexOf("cat"); //0
tvShow.indexOF("dog"); //3
tvShow.indexOf("z"); //-1 (not found)
//중복되는 문자가 있어도 최초의 인덱스만 노출
```

💡 `str.length`

```javascript
// 문자열 데이터 타입 변수 선언
let name = "wecode";

// .length >> 문자열이 몇 글자로 되어 있는지 확인
name.length; // 5

// .toUpperCase >> 문자열을 대문자로 출력
name.toUpperCase(); // "WECODE"

// .indexOf >> 특정 텍스트의 포함 유무 및 위치 확인
name.indexOf("c"); // 2
name.indexOf("j"); // -1
```
