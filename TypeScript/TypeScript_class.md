# <p align="center">👩‍🏫 Class | 클래스</p>

### 💡 Class | 클래스

- 타입스크립트의 클래스는 속성과 메소드가 있는 객체를 정의하는 데 사용됩니다.
- 이것은 주로 행동이 연관된 `객체의 인스턴스를 만드는 데 사용`됩니다.
- 클래스는 `캡슐화`, `상속` 및 `다형성과` 같은 객체 지향 프로그래밍(OOP) 개념을 구현하는 데 사용됩니다.
- 구성요소
  - `constructor`
    - Class constructors are very similar to `functions`. You can `add parameters` with type `annotations`, `default values`, and `overloads`:
  - `{}` 초기화

### 💡 접근 가능한 위치

|           | 선언한 클래스 내 | 상속받은 클래스 내 | 인스턴스 |
| --------- | ---------------- | ------------------ | -------- |
| private   | ⭕ 　            | ❌                 | ❌       |
| protected | ⭕ 　            | ⭕ 　              | ❌       |
| public    | ⭕ 　            | ⭕ 　              | ⭕ 　    |

```tsx
class Player {
  constructor(
    private firstName: string,
    private lastName: string,
    public nickName: string
  ) {}
}

//result
//"use strict";
class player {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
}
```

- private는 컴파일 되면서 사라짐
  - 실제로 JS에서 사용하지 않음
  - property & method 에서 작동

## <p align="center">🖌️ Abstract class | 추상 클래스</p>

- 다른 클래스가 상속받을 수 있는 클래스
- 새로운 인스턴스를 만들 수 없음
  - e.g. `new User("","")` 작동하지 않음

```tsx
abstract class User {
  constructor(
    private firstName: string,
    private lastName: string,
    public nickName: string
  ) {}
  private getFullName() {
    return `${this.firstName} + ${this.lastName}`;
  }
}

class Player extends User {}

const lee = new Player('lee', 'Kim', 'park');

//result
('use strict');
class User {
  constructor(firstName, lastName, nickName) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.nickName = nickName;
  }
  getFullName() {
    return `${this.firstName} + ${this.lastName}`;
  }
}
class Player extends User {}
const lee = new Player('lee', 'Kim', 'park');

lee.getFullName();
```

<img width="678" alt="스크린샷 2023-02-25 오후 8 22 17" src="https://user-images.githubusercontent.com/110847597/221357603-41854435-0b41-44d3-8368-71f4099d235b.png">

### <p align="center">Abstract method</p>

- 추상클래스를 상속받는 모든것들이 구현을 해야하는 메소드를 의미
- 메소드를 클래스 안에서 구현하지 않는다
  - method: 클래스 안에 존재하는 함수
- 메소드의 call signature 만 작성해야함
- 인스턴스화 불가
- 추상 메서드는 추상 클래스를 상속받는 클래스들이 반드시 구현(implement)해야하는 메서드이다.

### 🔐 Private

- private
- Class 인스턴스나 메소드 접근 가능

```tsx
abstract class User {
  constructor(
    protected firstName: string,
    protected lastName: string,
    protected nickName: string
  ) {}

  abstract getNickName(): void;

  getFullName() {
    return `${this.firstName} + ${this.lastName}`;
  }
}

class Player extends User {
  getNickName() {
    console.log(this.nickName);
  }
}

const lee = new Player('lee', 'Kim', 'park');

lee.getFullName();
```

### 🛡️ Protected

- 필드가 외부에서 보호 됨
- 다른 자식 클래스에서 사용가능

```tsx
type Words = {
  [key: string]: string;
  //property의 이름을 모르지만, 타입만을 알 때 사용함 [key:"string"]
};

class Dict {
  private words: Words;
  //1. words를 initializer 없이 선언
  constructor() {
    //2. constructor 수동으로 초기화
    this.words = {};
  }

  add(word: Word) {
    if (this.words[word.term] === undefined) {
      this.words[word.term] = word.def;
    }
    //만약 등록되지 않은 term이라면 새로 add
  }
  def(term: string) {
    return this.words[term];
  }
}

class Word {
  constructor(public term: string, public def: string) {}
}

const kimchi = new Word('kimchi', '한국전통음식');
const dict = new Dict();

dict.add(kimchi);
dict.def('kimchi');
```

---

출처:

- [https://www.typescriptlang.org/docs/handbook/2/classes.html](https://www.typescriptlang.org/docs/handbook/2/classes.html)
