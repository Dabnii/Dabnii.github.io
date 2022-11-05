# <p align="center"> 🧢 React Hook

## 🧢 React Hook

### 💡 Hook의 특징

1. ✨ 함수 컴포넌트에서만 사용 가능 (필수)
1. ✨ `use-` 로 시작 (필수)
1. 내장 `hook`이 존재
   - (`useState`, `useEffect` , … )
1. `custom hook`
   - 외부 라이브러리나 내장 Hook에 없는 상태 관련 로직이 필요할 때, 직접 hook으로 만들어 사용하는 것

### 💡 Hook 사용 규칙

- `함수컴포넌트` 또는 `custom hook` 안에서만 사용 가능
- `at the top level` `최상위` 에서만 호출 할 수 있음

```javascript
// useState Hook을 최상위에서 호출한 경우
// Test.js

import React, { useState } from "react";

const Test = () => {
  const [color, setColor] = useState("red");

  if (5 > 3) {
    console.log("true");
  }

  return <div>Hello!</div>;
};

export default Test;
```

- 첫번째 중괄호 내부에 있기 때문에 호출 가능
  - return 하위에서는 호출 불가
  - 첫번째 중괄호 내부 조건문, 반복문 등의 중첩되는 코드블럭에서 호출하게 되면 에러발생

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20%26%20Jsx.md"> 이전글: React & JSX </a>

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20Props.md"> 다음글: React Props</a>

<hr>
<p align="center"> E.O.D
