# <p align="center"> 🖌️ TypeScript </p>

## <p align="center"> 🔐 Type Safety </p>

- `엄격한 타입 검사`
  - Dynamic typing의 단점 개선
- 코드 버그가 줄어듬
- 생산성이 늘어남
- 런타임 에러 (콘솔에서 일어남)
  - 유저가 에러를 마주하게 됨

```jsx
console.log('' == 0);
//true
x = 10;
console.log(1 < x < 3)[1] + true; //true
//'1true' Awesome!
```

## <p align="center">🏃‍♀️ Run TypeScript </p>

- node.js
- `npm install -g typescript`
- `tsc -w`
  - 컴파일 역할
- `Ts` → `Js`
  - 브라우저는 JavaScript만 읽을 수 있음

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
let name: string = 'Lee';
```

```tsx
let a: number[] = [1, 2, 3];
let b: string[] = ['A', 'b', 'C'];
let c: boolean[] = [true];
```

### <p align="center"> Types by Inference</p>

```tsx
let helloWorld = 'Hello World';
//  ^?
```

### <p align="center">Defining Types</p>

```tsx
const user = {
  name: 'Hayes',
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
  name: 'kim',
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

const nico = playerMaker('Lee');
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
const user: User = new UserAccount('Murphy', 1);
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

let john: Member = { name: 'kim' };
```
