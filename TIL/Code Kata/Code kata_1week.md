# <p align="center">📖 Code Kata

<p align="center"> 📆 2022.Nov.7 | 50min<br>

## Week 2 | test #1

> ### Q.1 로마자에서 숫자로 바꾸기
>
> 1~3999 사이의 로마자 s를 인자로 주면 그에 해당하는 숫자를 반환해주세요. 로마 숫자를 숫자로 표기하면 다음과 같습니다.<br>
>
> ### 💡 Symbol Value<br>
>
> I 1<br>
> V 5<br>
> X 10<br>
> L 50<br>
> C 100<br>
> D 500<br>
> M 1000<br>
> 로마자를 숫자로 읽는 방법은 로마자를 왼쪽부터 차례대로 더하면 됩니다. III = 3 XII = 12 XXVII = 27 입니다.<br>
> 그런데 4를 표현할 때는 IIII가 아니라 IV 입니다. 뒤의 숫자에서 앞의 숫자를 빼주면 됩니다. 9는 IX입니다.
> I는 V와 X앞에 와서 4, 9 X는 L, C앞에 와서 40, 90 C는 D, M앞에 와서 400, 900

### 💡 핵심 키워드 :

- 데이터를 담는 객체를 활용.
- `[]` Bracket Notation 활용.
- IV 4, IX 9 경우는 앞 자리가 뒷 자리보다 작다.
- ✨ 복잡해 보이지만, 간단한 2가지의 조건만 충족 하면 된다.

| s    | i [0]   | i + 1 [1]        | 숫자 |
| ---- | ------- | ---------------- | ------ |
| I    | I (1)   | null             | 1      |
| II   | I (1)   | I (1)            | 2      |
| III  | I (1)   | I (1) ... + I(i) | 3      |
| `IV` | `I (1)` | `V (5)`          | `4`    |
| `IX` | `I (1)` | `X (10)`         | `9`    |

- 1️⃣ : 앞 자리가 뒷 자리 보다 작은 경우 `뒤에서 앞 자리를 뺀다`
- 2️⃣ : 앞 자리가 뒷 자리 보다 큰 경우 더 한다

```javascript
function romanToNum(s) {
  const romeNum = {
    I: 1,
    V: 5,
    X: 10,
    L: 50,
    C: 100,
    D: 500,
    M: 1000,
  };

  let result = 0;

  for (let i = 0; i < s.length; i++) {
    if (romeNum[s[i]] < romeNum[s[i + 1]]) {
      result -= romeNum[s[i]];
      //result  = result - romeNum[s[i]]
    } else {
      result += romeNum[s[i]];
    }
  }
  return result;
}
```

## 🌳 성장 포인트

- `+=` & `-=`
  - `result  = result - romeNum[s[i]]`
  - `result  = result + romeNum[s[i]]`
- 복잡해 보이는 문제 조건을 간단하게 생각하는 방법
  - 함정에 빠지지 말자 🕳
- 동기들에게 한 수 배우는 날 🙇‍♀️