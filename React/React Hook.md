# <p align="center"> ๐งข React Hook

## ๐งข React Hook

### ๐ก Hook์ ํน์ง

1. โจ ํจ์ ์ปดํฌ๋ํธ์์๋ง ์ฌ์ฉ ๊ฐ๋ฅ (ํ์)
1. โจ `use-` ๋ก ์์ (ํ์)
1. ๋ด์ฅ `hook`์ด ์กด์ฌ
   - (`useState`, `useEffect` , โฆ )
1. `custom hook`
   - ์ธ๋ถ ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ ๋ด์ฅ Hook์ ์๋ ์ํ ๊ด๋ จ ๋ก์ง์ด ํ์ํ  ๋, ์ง์  hook์ผ๋ก ๋ง๋ค์ด ์ฌ์ฉํ๋ ๊ฒ

### ๐ก Hook ์ฌ์ฉ ๊ท์น

- `ํจ์์ปดํฌ๋ํธ` ๋๋ `custom hook` ์์์๋ง ์ฌ์ฉ ๊ฐ๋ฅ
- `at the top level` `์ต์์` ์์๋ง ํธ์ถ ํ  ์ ์์

```javascript
// useState Hook์ ์ต์์์์ ํธ์ถํ ๊ฒฝ์ฐ
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

- ์ฒซ๋ฒ์งธ ์ค๊ดํธ ๋ด๋ถ์ ์๊ธฐ ๋๋ฌธ์ ํธ์ถ ๊ฐ๋ฅ
  - return ํ์์์๋ ํธ์ถ ๋ถ๊ฐ
  - ์ฒซ๋ฒ์งธ ์ค๊ดํธ ๋ด๋ถ ์กฐ๊ฑด๋ฌธ, ๋ฐ๋ณต๋ฌธ ๋ฑ์ ์ค์ฒฉ๋๋ ์ฝ๋๋ธ๋ญ์์ ํธ์ถํ๊ฒ ๋๋ฉด ์๋ฌ๋ฐ์

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20%26%20Jsx.md"> ์ด์ ๊ธ: React & JSX </a>

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20Props.md"> ๋ค์๊ธ: React Props</a>

<hr>
<p align="center"> E.O.D
