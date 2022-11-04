# <p align="center"> 🧢 React State

## 🧢 React State

### 💡 State 특징

- state란 해당 컴포넌트가 UI에 보여줄 정보를 결정할 때 사용하는 `상태값`
  - 컴포넌트 내에서 `정의하고 사용하고 언제든 변경` 가능
- useState hook을 호출하고, 구조 분해 할당을 통해 반환된 값을 사용 가능
- 첫 번째 요소인 state를 통해 동적으로 관리하고자 하는 값을 할당 가능
- 두 번째 요소인 setState function을 통해 state를 업데이트 가능

### 💡 State 특징

```javascript
// Main.js

import React, { useState } from "react";

const Main = () => {
  // 변수 color, setColor는 다름 이름으로 바뀔 수 있습니다.
  const [color, setColor] = useState("red");

  return <h1>여기는 메인페이지입니다.</h1>;
};

export default Main;
```
