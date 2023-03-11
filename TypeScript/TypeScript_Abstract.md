### <p align="center">📆 3/11</p>

### playground

```typescript
class Player {
  constructor(
    private firstName: string,
    private lastName: string,
    public nickname: string
  ) {}
}

const dabin = new Player('Da-bin', 'Lee', '다람쥐');
```

```typescript
abstract class User {
  constructor(
    private firstName: string,
    private lastName: string,
    public nickname: string
  ) {}
}

class Player extends User {}
//Player가 User를 상속한다
//추상클래스: 다른 클래스가 상속받을 수 있는 클래스

const dabin = new User('Da-bin', 'Lee', '다람쥐');
//Error!
//생성불가
```
