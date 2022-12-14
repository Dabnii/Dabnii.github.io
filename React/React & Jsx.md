# <p align="center"> ๐งข React & JSX

## ๐ `JSX` : (`J`avaScript `S`yntax e`X`tension)

- ๋ฆฌ์กํธ์์ ์ฌ์ฉํ๋ ์๋ฐ์คํฌ๋ฆฝํธ `ํ์ฅ ๋ฌธ๋ฒ`
- HTML๊ณผ ์๋ฐ์คํฌ๋ฆฝํธ ๋ก์ง์ `ํ๋์ ์๋ฐ์คํฌ๋ฆฝํธ ํ์ผ ์์์ ๋ชจ๋ ์ฒ๋ฆฌ` ๋ชฉ์ 
- `HTML๊ณผ ์ ์ฌํ ํํ๋ก` ์ฌ์ฉ
- ํ๋์ ์๋ฐ์คํฌ๋ฆฝํธ ํ์ผ์์ HTML๊ณผ ์๋ฐ์คํฌ๋ฆฝํธ `๋ก์ง์ ๋์`์ ์์ฑ
- JSX๋ก ์์ฑํ ์ฝ๋๋ Babel๋ก ์ผ๋ฐ ์๋ฐ์คํฌ๋ฆฝํธ ์ฝ๋ ํํ๋ก ๋ณํ

```jsx
const element = (
 <h1 className="greeting!">
	Hello, world!
 <h1>
);
```

```jsx
//Babel ๋ณํ
const element = React.creatElement(
  "h1",
  { className: "greeting" },
  "Hello, world!"
);
```

## ๐ `JSX` ํน์ง

- ํ๋์ ์๋ฐ์คํฌ๋ฆฝํธ ํ์ผ๋ก HTML, js ์์ฑ ๊ฐ๋ฅ
- ํ๋์ ์๋ฐ์คํฌ๋ฆฝํธ๋ฅผ ํตํด ๋ก์ง์ ์์ฑ์ผ๋ก ํธ๋ฆฌํจ

## ๐ `JSX` ๋ฌธ๋ฒ

<br>

### 1. JSX element

- ์๋ฐ์คํฌ๋ฆฝํธ์์ HTML ์์ฑ ๊ฐ๋ฅ ๐

```jsx
const hi = <p>Hi</p>;
```

<br>

### 2.`{ Javascript ํํ์ }`

- `{ ... JavaScript... }`

  - ์ ํจํ ์๋ฐ์คํฌ๋ฆฝํธ ํํ์ ์์ฑ ๊ฐ๋ฅ ๐

    ```jsx
    // Greetings.js
    import React from "react";

    const Greetings = () => {
      const name = "๊น๊ฐ๋ฐ";

      return <h1>{name}๋, Welcome to Wecode!</h1>;
    };

    export default Greetings;
    ```

### 3. JSX attribute

- attribute name(์์ฑ๋ช)์ `camelCase`๋ก ์์ฑ
- โจ `class` โ `className`

```jsx
//HTML
<h1 class="greetings">Welcome!</h1>

// JSX
<h1 className="greetings">Welcome!</h1>
```

### 4. Event ์ฒ๋ฆฌํ๊ธฐ

- `on` + `event`
- ํจ์ ์ด๋ฒ ํธ ํธ๋ค๋ฌ๋ฅผ ์ ๋ฌ

  ```jsx
  // JS
  const title = document.getElementsByClassName("title")[0];
  title.addEventListener("click", handleClick);

  // JSX
  <h1 className="title" onClick={handleClick}>
    Welcome to Wecode!
  </h1>;
  ```

### 5. Inline Styling

- camelCase๋ฅผ ์์๋ก ๊ฐ์ง๋ ์๋ฐ์คํฌ๋ฆฝํธ ๊ฐ์ฒด๋ฅผ ๋ฐ์
  - ์ค๊ดํธ๋ฅผ ๋ ๋ฒ ๊ฒน์น ํํ๋ก ์ฌ์ฉ
- `{ ๋ฐ๊นฅ }` = JSX ๋ฌธ๋ฒ
- `{ ์์ชฝ }`= JS obj
- CSS ๋ณด๋ค ์ฐ์ ์์ ๋๊ณ , ์ฑ๋ฅ์ด ๋ฎ์
- ~~๋์  ์คํ์ผ๋ง์ ์ฌ์ฉ์ง์~~

```javascript
// HTML
<h1 style="color:red;background-image:yellow">Welcome to Wecode!</h1>

// JSX
<h1 style={{ color: "red", backgroundImage: "yellow" }}>
  Welcome to Wecode!
</h1>
```

### 6. `<Self-Closing Tag / >`

- ์ด๋ค ํ๊ทธ๋  self-closing-tag ๊ฐ๋ฅ!

### 7. `<div>` Nested JSX `</div>`

- Why?
  - `virtual DOM`์ ์ปดํฌ๋ํธ ๋ณํ๋ฅผ ํจ์จ์ ์ผ๋ก ๋น๊ตํ  ์ ์๋๋ก ํ ์ปดํฌ๋ํธ๋ `ํ๋์ DOM ํธ๋ฆฌ ๊ตฌ์กฐ`๋ก ์ด๋ฃจ์ด์ ธ์ผ ํ๋ค๋ `๊ท์น`

```jsx
// Bad
const Greetings = () => {
  return (
    <h1>๊น๊ฐ๋ฐ๋!</h1>
    <h2>์์ฝ๋์ ์ค์  ๊ฑธ ํ์ํฉ๋๋ค!</h2>
  );
}

// Good
const Greetings = () => {
  return (
    <div>
      <h1>๊น๊ฐ๋ฐ๋!</h1>
      <h2>์์ฝ๋์ ์ค์  ๊ฑธ ํ์ํฉ๋๋ค!</h2>
    </div>
  );
}
```

### 8. `<>` React.Fragment `</>`

- ` <>``</> `
- ๋จ์ถ๋ ๋ฒ์ ์ผ๋ก ์์ฑ ๊ฐ๋ฅ
- ์ถ๊ฐ์ ์ธ DOM element๊ฐ ํ์์์
- ๊ฐ๋จํ๊ฒ ํ๋์ ์ปดํฌ๋ํธ์ ์ฌ๋ฌ ์์(์์)์ ๊ทธ๋ฃนํ

```jsx
const Greetings = () => {
  return (
    <>
      <h1>์ด๋ ๊ฒ</h1>
      <h2>์ฝ๊ฒ ๊ทธ๋ฃนํ ๊ฐ๋ฅ! ๐๐</h2>
    </>
  );
};
```

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20component.md"> ์ด์ ๊ธ: React Component </a>

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20Hook.md"> ๋ค์๊ธ: React Hook </a>

<hr>
<p align="center"> E.O.D
