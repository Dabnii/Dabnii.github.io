# <p align="center"> ๐งข React State

## ๐งข React State

### ๐ก State ํน์ง

- state๋ ํด๋น ์ปดํฌ๋ํธ๊ฐ UI์ ๋ณด์ฌ์ค ์ ๋ณด๋ฅผ ๊ฒฐ์ ํ  ๋ ์ฌ์ฉํ๋ `์ํ๊ฐ`
  - ์ปดํฌ๋ํธ ๋ด์์ `์ ์ํ๊ณ  ์ฌ์ฉํ๊ณ  ์ธ์ ๋  ๋ณ๊ฒฝ` ๊ฐ๋ฅ
- useState hook์ ํธ์ถํ๊ณ , ๊ตฌ์กฐ ๋ถํด ํ ๋น์ ํตํด ๋ฐํ๋ ๊ฐ์ ์ฌ์ฉ ๊ฐ๋ฅ
- ์ฒซ ๋ฒ์งธ ์์์ธ state๋ฅผ ํตํด ๋์ ์ผ๋ก ๊ด๋ฆฌํ๊ณ ์ ํ๋ ๊ฐ์ ํ ๋น ๊ฐ๋ฅ
- ๋ ๋ฒ์งธ ์์์ธ setState function์ ํตํด state๋ฅผ ์๋ฐ์ดํธ ๊ฐ๋ฅ

### ๐ก State ์ ์ธ

```javascript
// Main.js

import React, { useState } from "react";

const Main = () => {
  // ๋ณ์ color, setColor๋ ๋ค๋ฆ ์ด๋ฆ์ผ๋ก ๋ฐ๋ ์ ์์ต๋๋ค.
  const [color, setColor] = useState("red");

  return <h1>์ฌ๊ธฐ๋ ๋ฉ์ธํ์ด์ง์๋๋ค.</h1>;
};

export default Main;
```

1. useStateํจ์๋ Hook์ ์ผ์ข

<br>

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20Props.md">์ด์ ๊ธ: React Props </a>

<hr>
<p align="center"> E.O.D
