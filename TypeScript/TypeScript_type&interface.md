# Interface

상태: In progress
생성 일시: 2023년 3월 12일 오후 9:29

### Type

- 타입 `alias`를 생성 가능
- 오브젝트 모양을 묘사하는데 사용 가능
- 특정값을 가지도록 제한 가능
- interface보다 목적성이 다양함

```tsx
type Nickname = string;
type Job = string;
type Age = number;
type Friends = Array<string>;

type Player = {
  nickName: Nickname;
  job: Job;
};

const nico: Player = {
  nickname: 'nico',
  age: 20,
};
```

```tsx
type Team = "red" | "blue" | "white"
type age = 10 | 20 | 30

type Player = {
	nickname:string,
	team:Team
	health: Health
}

const lee:Player = {
	nickname:"nico"
	team:"red"
}
```

### Interface

- 오브젝트의 모양을 특정&설명할 때 사용

```tsx
interface Player {
	nickname:string,
	team:Team
	health: Health
}

interface Hello = string // wrong!
```

```tsx
interface User {
  name: string;
}

interface Player extends User {}

const nico: Player = {
  name: 'Lee',
};
```

```tsx
type User {
	name:string
}

type Player = User & {}

const nico: Player = {
	name:"Lee"
}
```
