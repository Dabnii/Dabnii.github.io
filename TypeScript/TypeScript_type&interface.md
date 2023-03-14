# <p align="center"> 💬 Interface </p>

- `타입의 구조를 정의`
- 💡 새 property 추가를 위해 `다시 선언될 수 없음`
  - `extends`로 확장할 수 있음
- 언제나 👪 상속 가능
- 중복 선언 가능
  - `stack`됨

```tsx
interface Player {
  nickname: string;
  team: Team;
  health: Health;
}

type User {
	name:string
}

interface Hello = string // wrong!

interface Player extends User {}

type Player = User & {}
// type으로 구현 하고 싶다면

const lee: Player = {
	name:"dabin"
}
```

## <p align="center">💡 Implement | 형태 충족 확인</p>

- `implements` 절을 사용하여 클래스가 특정 인터페이스를 `만족하는지 확인`
  - ⚠️ 클래스가 올바르게 구현하지 못하면 오류가 발생
- 클래스와 인터페이스 사이에는 존재합니다. [JS에는 존재하지 않습니다 | 기능이 없습니다.]
- 특정 인터페이스를 사용하여 개체를 생성하려는 경우 해당 인터페이스에 필요한 메서드 및 속성을 정의할 수 있습니다.
- 클래스의 유형이나 메서드는 전혀 변경하지 않습니다.
- JS로 컴파일되면 사라집니다.
- 가볍습니다 (downsizing)
- 클래스와 클래스가 의도한 목적을 달성하기 위해 어떤 메서드와 속성을 가져야 하는지 지정하는 것이다.

  - [📎 TypeScript : Implement](https://www.typescriptlang.org/docs/handbook/2/classes.html#implements-clauses)

```typescript
interface User {
  firstName: string;
  lastName: string;
  sayHi(name: string): string;
  fullName(): string;
}

interface Human {
  health: number;
}

class Player implements User, Human {
  constructor(
    public firstName: string,
    public lastName: string,
    public health: number
  ) {}
  fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
  sayHi(name: string) {
    return `hello ${name} my name is ${this.fullName}`;
  }
}
```
