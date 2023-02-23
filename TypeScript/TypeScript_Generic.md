### <p align="center"> 💡 Polymorphism </p>

- 여러 타입을 받아들임으로써 여러 형태를 가지는 것을 의미
- 다형성을 위하여 제너릭을 사용함
- Polymorphism is the ability to create a class that has more than one form. Or in other words, classes have the same methods but different implementations.

```tsx
type SuperPrint = {
  (arr: number[]): void;
  (arr: boolean[]): void;
};

const superPrint: SuperPrint = arr => {
  arr.forEach(i => console.log(i));
};
```

### 💡 Concrete type

| Concrete type               |         |            |         |           |
| --------------------------- | ------- | ---------- | ------- | --------- |
|                             | numbers | string     | boolean | interface |
|                             | null    | undefined  | classes | arrays    |
| call signature에 명시필요 X | ✨ void | ✨ unknown |         |           |

</br>

## <p align="center">🕵️ Generic </p>

### <p align="center">💡 제네릭은 선언 시점이 아니라 `생성 시점에 타입을 명시`하여</br> 하나의 타입만이 아닌 `다양한 타입을 사용할 수 있도록 하는 기법`</p>

- use as `place holder`
- 확실한 타입을 모를 때 사용
- `타입스크립트가 타입 유추` call signature로 수시로 명시 하지 않음
- 제네릭은 타입에 변수를 제공하는 방법

## <p align="center"> 💡 Basic syntax </p>

- `<T, V>` 와 같이 변수명과 같이 자유롭게 사용가능
- TypeScript가 type을 유추하도록 하는 것이 Best

```tsx
type Sample = {
  <T>(arr: T[]): T;
};
```

```tsx
type StringArray = Array<string>;
type NumberArray = Array<number>;
type ObjectWithNameArray = Array<{ name: string }>;
```

<details>
<summary>example codes</summary>

```tsx
type SuperPrint = {
  <typePlaceholder>(arr: typePlaceholder[]): void;
};

const superPrint: SuperPrint = arr => {
  arr.forEach(i => console.log(i));
};

superPrint([1, 2, true, false]);
superPrint([1, 2, 3, 4]);
superPrint([true, true, true, false]);
```

```tsx
type SuperPrint = { (arr: T[]): void };
type SuperReturn = { (arr: T[]): T };

const superPrint: SuperPrint = arr => {
  arr.forEach(i => console.log(i));
};
const superReturn: SuperReturn = arr => arr[0];

superPrint([1, 2, false, true]);
console.log(superReturn([1, 2, 3, 4]));
```

</details>

```tsx
function superPrint<v>(a: V[]) {
  return a[0];
}

const a = superPrint<boolean>([1, 2, 3, 4]);
// overwriting는 불필요하다
// Ts가 유추하도록 하는 것이 Best
```

- `타입을 생성` 하거나 `타입 확장` 할 수 있음
- 코드를 저장하기도 함
- 타입간의 `재사용` 가능

### <p align="center">➕ Generic 활용한 확장</p>

```tsx
type Player<T> = {
  name: string;
  extraInfo: T;
};

type ParkExtra = {
  favFood: string;
};

type ParkInfo = Player<ParkExtra>;

const park: Player<{ favFood: string }> = {
  name: 'park',
  extraInfo: {
    favFood: 'Kimchi',
  },
};

const lee: Player<null> = {
  name: 'lee',
  extraInfo: null,
};
//다수의 타입 중, 달라질 수 있는 타입에 제네릭을 사용함
```

```tsx
type A = Array<number>;

let a: A = [1, 2, 3, 4];

function parintAllNumbers(arr: Array<number>) {}
```

## <p align="center"> ✨ useState + Generic </p>

```jsx
useState<number>();
```

```jsx
type Information = { name: string, description: string };
const [info, setInformation] = (useState < Information) | (null > null);
//그러니까...
//이렇게도 된다는 것
```

- 상태가 `null`일 수도 있고 아닐수도 있을때 Generics 를 활용하시면 좋습니다. 👏

---

- [🔗 제네릭 Generics ](<[https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html?](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html?#%EC%A0%9C%EB%84%A4%EB%A6%AD-generics)>)
- [🔗 Polymorphism With TypeScript (OOP) ](<[https://blog.bitsrc.io/polymorphism-in-typescript-oop-17646dcda307](https://blog.bitsrc.io/polymorphism-in-typescript-oop-17646dcda307)>)
- [🔗 3. 타입스크립트로 리액트 상태 관리하기 ](<[https://react.vlpt.us/using-typescript/03-ts-manage-state.html](https://react.vlpt.us/using-typescript/03-ts-manage-state.html)>)
