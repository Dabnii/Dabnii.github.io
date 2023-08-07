# <p align="center"> 🖌️ TypeScript </p>

## <p align="center"> 🔐 Type Safety </p>

- `엄격한 타입 검사`
  - Dynamic typing의 단점 개선
- 코드 버그가 줄어듬
- 생산성이 늘어남

|          | JavaScript                                 | TypeScript              |
| -------- | ------------------------------------------ | ----------------------- |
| 특징     | Dynamic typing (동적)                      | Static typing (정적)    |
| 오류타입 | 런타임 에러                                | 컴파일 에러             |
| 오류특징 | 최악의 경우 화면이 멈춤, 최악의 사용자경험 | 개발단계에서 핸들링가능 |

- JavaScript의 치명적 오류 👇

```jsx
console.log("" == 0);
//true
x = 10;
console.log(1 < x < 3)[1] + true; //true
//'1true' Awesome!
```

## <p align="center">🏃‍♀️ Run TypeScript </p>

- ✨ `node.js`
- `npm install -g typescript`
- `tsc -w`
  - 컴파일 역할
- `Ts` → `Js`
  - 브라우저는 JavaScript만 읽을 수 있어 변환이 필요함

```tsx

  {
    "complierOptions: {
      "target" : "es5",
      "module" : "commonjs",
    }
  }

```

## <p align="center"> Implicit Types vs Explicit Types </p>

### <p align="center"> string

```tsx
let name: string = "Lee";
```

```tsx
let a: number[] = [1, 2, 3];
let b: string[] = ["A", "b", "C"];
let c: boolean[] = [true];
```

### <p align="center"> Types by Inference</p>

```tsx
let helloWorld = "Hello World";
//  ^?
```

### <p align="center">Defining Types</p>

```tsx
const user = {
  name: "Hayes",
  id: 0,
};
```

이 객체의 형태를 명시적으로 나타내기 위해서는 `interface` 로 선언합니다. 👇

```tsx
interface User {
  name: string;
  id: number;
}
```

## <p align="center">Basic syntax</p>

- `:TypeName` 을 사용하여 선언

```tsx
:TypeName
```

```tsx
interface User {
name: string;
id: number;
}

class UserAccount {
	name: string;
	id: number;
		constructor(name: string, id: number) {
			[this.name](http://this.name/) = name;
			[this.id](http://this.id/) = id;
	}
}

const user: User = new UserAccount("Murphy", 1);
```

```tsx
let a :
let a : number[] = [1,2]
```

## <p align="center"> Optional (Parameter) type </p>

- 값의 유무가 확실하지 않을 때

```tsx
?:
```

```tsx
const user = {
	name: 'string',
	age?: number,
} = {
	name: 'kim'
}

//bad
// if (player.age < 10) {
//
// }

//good
if {player.age && play.age < 10}{}
```

## <p align="center"> ✨ Alias Type</p>

- 첫 글자는 대문자 컨벤션
- 변수에 담아 사용할 수 있음
- 불필요하게 반복되는 코드를 줄일 수 있음

```tsx
type Player = {
  name: string;
  age?: number;
};
//
const Kim: player = {
  name: "kim",
  age: 16,
};

type VarType = string | number;
let name: varType = 123;
```

## <p align="center"> 함수형 </p>

- 함수에 타입지정 가능

```tsx
function playerMaker(number: string): Player {
  return {
    name,
  };
}

const nico = playerMaker("Lee");
const playerMaker = (name: string): Player => {
  name;
};

function foo(x: number) {
  return x * 2;
}
//함수에 타입지정 가능

function foo(x: number): number {
  return x * 2;
}
//리턴값도 미리체크 가능
//파라미터 옆에 설정해줌
```

- player를 리턴 즉 리턴값 지정
  - `playerMaker(number:string) : Player`

## readonly

- 👓 읽기전용
- 수정불가

```tsx
type Age = number;
type Name = string;

type Player = {
	readonly = name: Name
	age?: Age
}
```

### Class 형

```tsx
interface User {
  name: string;
  id: number;
}

class UserAccount {
  name: string;
  id: number;

  constructor(name: string, id: number) {
    this.name = name;
    this.id = id;
  }
}
const user: User = new UserAccount("Murphy", 1);
```

### <p align="center"> Tuple </p>

```tsx
type Member = [member, boolean];
let jhon: Member = [123, true];
//tuple
//Array에 사용
```

```tsx
type Member = {
  [key: string]: string;
  //모든 오브젝트 속성
};

let john: Member = { name: "kim" };
```

### Readonly Tuple

```tsx
const player: readonly [string, number, boolean];
```

```tsx
type Member = {
  [key: string]: string;
  //모든 오브젝트 속성
};

let john: Member = { name: "kim" };
```

### undefined, null, any

```tsx
let a = [];
// a = any
```

`any`: 아무 타입

`undefined`: 선언X 할당X

`null`: 선언O 할당X

## <p align="center"> Exclusive Typescript type checker </p>

### unknown

- unknown타입은 모든 값을 나타냅니다. 이것은 any타입과 비슷하지만 any보다 unknown이 더 안전합니다. 이유는 unknown값으로 작업을 수행하는 것은 합법적이지 않기 때문입니다.

```tsx
let a: unknown;
```

### void

- 아무것도 return 하지 않는 함수
- 선언할 필요 없음

```tsx
function hello() {
  console.log("x");
}
//function hello():void
```

### never

- 함수가 절대 return 하지 않을 때
- 함수에서 exception(예외) 발생할 때
- 일부 함수는 값을 반환하지 않습니다.
- 이는 함수가 예외를 throw하거나 프로그램 실행을 종료함을 의미합니다.

```tsx
function fail(msg: string): never {
  throw new Error(msg);
}
```

### 🪟 Call Signatures

![Untitled](https://user-images.githubusercontent.com/110847597/220637736-d9ae0b64-a5a4-4168-a2f6-9914022e4aaa.png)

- 함수 타입, argument 타입, 반환 타입을 명시 ✨
- 함수위에 마우스를 올렸을 때 보게 되는 것
- `장점`: 타입을 만들 수 있고, 함수의 작동방식을 서술 가능

  ```tsx
  type Add = (a: number, b: number) => number;

  const add: Add = (a, b) => a + b;
  ```

  > 타스는 알고있다😎

### Overloading

- `Function(=Method) Overloading`은 직접 작성하기보다 외부 라이브러리에 자주 보이는 형태
- 함수가 서로 다른 다수의 call signatures를 가지고 있을 때 발생

```tsx
type Add = {
  (a: number, b: number): number;
};

const add: Add = (a, b) => a + b;
```

```tsx
//nextjs
Router.push({
	path: "/home",
	state: 1
})

.push("/home")

type Config = {
	(path:string):void,
	//return nothing
	state: object
}

type Push = {
	(path:string):void
	(config: Config):void;
}

const push:Push = (config) => {
	if(typeof config  === "string"){ console.log(config)
		} else	{
		console.log(config.
	}
}
```

```tsx
type Add = {
  (a: number, b: number): number;
  (a: number, b: number, c: number): number;
};

const add: Add = (a, b, c?: number) => {
  if (c) return a + b + c;
  return a + b;
};

add(1, 2);
add(1, 2, 3);
```

| Type      | JS  | TS  | Description                                                                                                                                  |
| --------- | --- | --- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| boolean   | O   | O   | T/F                                                                                                                                          |
| null      | O   | O   | 값이 없음을 명시                                                                                                                             |
| undefined | O   | O   | 값을 할당하지 않은 변수의 초기값                                                                                                             |
| number    | O   | O   | 숫자(정수와 실수, infinity, NaN)                                                                                                             |
| string    | O   | O   | 문자열                                                                                                                                       |
| symbol    | O   | O   | 고유하고 수정 불가능한 데이터 타입,<br/>객체 프로퍼티들의 식별자로 사용 (ES6추가)                                                            |
| object    | O   | O   | 객체(참조형)                                                                                                                                 |
| array     |     | O   | 배열                                                                                                                                         |
| tuple     |     | O   | 고정된 요소수 만큼의 타입을 미리 선언 후 배열을 표현                                                                                         |
| enum      |     | O   | 열거형, 숫자값 집합에 이름을 지정한 것                                                                                                       |
| any       |     | O   | 타입추론(type inference)할 수 없거나<br/>타입 체크가 필요없는 변수에 사용.<br/>var키워드로 선언한 변수와 같이 어떤 타입의 값이라도 할당 가능 |
| void      |     | O   | 일반적으로 함수에서 반환값이 없을 경우                                                                                                       |
| never     |     | O   | 결코 발생하지 않는 값                                                                                                                        |

---

출처:

- [https://poiemaweb.com/typescript-typing](https://poiemaweb.com/typescript-typing)

### TypeScript : `type asserstion`

### 단점 💩

1. 타입을 개발자가 명시적으로 지정
1. 오직 컴파일 과정에서만 사용

### 방법1: `angle-bracket`

```typescript
let someValue: any = "hello";
let strLength: number = (<string>someValue).length;
```

### 방법2: `as`

```typescript
let someValue: any = "hello";
let strLength: number = (someValue as string).length;
```

### 👍 pros

- 유연성 :

  - 특정 상황에서 유연성 제공
  - 타임을 추론하기 어려울 때
  - 외부 라이브러리에서 사용

### 💩 cons

- 타입 안정성 저하:
  - 남용하여 타입 안정성을 저하시킬 수 있음
- 가독성 저하
- 🚨 잠재적 버그 유발

  - `컴파일러가 타입 검사를 하지 않음`

- [TypeScript Guidebook](https://yamoo9.gitbook.io/typescript/types/type-assertions)
