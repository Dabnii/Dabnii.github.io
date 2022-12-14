# <p align="center"> ๐ฆ SASS

<p align="center"> <a href ="https://sass-lang.com/">๐ SASS</a>

## ๐งโโ๏ธ CSS Preprocessor

CSS์ ์ฒ๋ฆฌ๊ธฐ:

- CSS์ ๋ถํธํ ๋ฌธ๋ฒ์ ๋ณด์ ๋ชฉ์ 
- ์ ์ฒ๋ฆฌ๊ธฐ ์์์ ๋ง๊ฒ ์์ฑํ ํ์ผ์ ๋ธ๋ผ์ฐ์ ๊ฐ ์ฝ์ ์ ์๋ CSSํ์ผ๋ก ๋ณํ
- ์ฌ๋ฌ ์ข๋ฅ์ค `SASS`๋ฅผ ์๊ฐ ํฉ๋๋ค.

## ๐งโโ๏ธ `SASS`

- `S`yntactically `A`wesome `S`tyle `S`heets
- ๊ธฐ์กด CSS ํ์ผ์ ์ทจ์ฝ์ ์ ๋ณด์ํฉ๋๋ค

### ๐งโโ๏ธ `SASS` Install

```css
npm install sass
```

```json
//package.json -> dependencies ์์ sass ํ์ธ ํ์
    "sass": "^4.14.1" ๐
```

### ๐งโโ๏ธ `SASS` Basic syntax

- SASS์ ๋ ๊ฐ์ง ๋ฌธ๋ฒ

| ๋ฌธ๋ฒ       | ์ฐจ์ด์                                         |
| ---------- | --------------------------------------------- |
| `.sass`    | `sass` ๋ฌธ๋ฒ ํ์ฉ                              |
| `.scss` ๐ | `cscc` ๋ฌธ๋ฒ ํ์ฉ <br> ๋์ ๋ฒ์ฉ์ฑ & CSSํธํ์ฑ |

```css

/* SASS */

nav
  ul
    margin: 0
    padding: 0
    list-style: none

  li
    display: inline-block

  a
    display: block
    padding: 6px 12px
    text-decoration: none
```

```css
/* SCSS */

nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li {
    display: inline-block;
  }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

## ๐งโโ๏ธ `SASS` ์ ์ฉํ๊ธฐ

1. ๊ธฐ์กด์ CSSํ์ผ ํ์ฅ์ SCSS๋ก ๋ณ๊ฒฝ

   - importํ CSSํ์ผ โ SCSS๋ก ๋ณ๊ฒฝ

1. ๐ค ๋ณํ ํ ๋ฐ์ํ๋ ๋ฌธ์  ํด๊ฒฐํ๊ธฐ

   - SPA ํน์ฑ์ ๋๋ฆฝ ๋์ด์๋ CSS๊ฐ router๋ก ์ปดํฌ๋ํธ๊ฐ ํฉ์ณ์ง ๋ ์ค๋ณต๋๋ ์ ํ์๋ก ์ธํ ์ค๋ฅ ๋ฐ์
   - className ๋ณ๊ฒฝ
     - ๋ง์์์ ์ปดํฌ๋ํธ ๊ด๋ฆฌ๊ฐ ์ด๋ ค์
     - ์ ์ง๋ณด์์ ์ด๋ ค์ `์๋ฌ๋ฐ์ ๊ฐ๋ฅ์ฑ์ด ๋์`
   - ๐ CSS ์์๊ฒฐํฉ์ ์ฌ์ฉ

   ```js
   // src/pages/Login/Login.js

   import React from "react";
   import "./Login.scss";

   const Login = () => {
     return (
       <div className="login">
         {" "}
         // 1<h1 className="title">๋ก๊ทธ์ธ ํ์ด์ง์๋๋ค.</h1>
       </div>
     );
   };

   export default Login;
   ```

   ```js
   // src/pages/Login/Login.scss

   .login .title {                                      // 2
   color: red;
   }

   ```

## ๐ CSS ์์๊ฒฐํฉ์๋ก ์์ ํ๊ธฐ | Sass nesting!

1. ์ต์์ ๋ถ๋ชจ ํ๊ทธ์ ๋์ผํ className ๋ถ์ฌ
   - ์ปดํฌ๋ํธ์ className์ ์ค๋ณต์ด ๋ถ๊ฐ ํ๋ค๋ ์ ์ ์ด์ฉ
1. ์ปดํฌ๋ํธ์ CSS์ ๊ด๊ณ๊ฐ ๋ชํํด์ง

   - camelCase

1. `์์๊ฒฐํฉ์`
   - ์คํ์ผ์ ์ ์ฉํ๊ณ  ์ถ์ ์ ํ์ ์์ ์กฐ์ ์ ํ์ ((๋ถ๋ชจ์ ๋ถ๋ชจ / ๋ถ๋ชจ์ ๋ถ๋ชจ์ ๋ถ๋ชจ ...)๋ฅผ ์๋ ฅ)
   - ์ ํํ๊ฒ ํด๋น ์์๋ฅผ ์ ํํ  ์ ์๋ CSS ๋ฌธ๋ฒ
   - `Sass nesting` ๊ธฐ๋ฅ : depth๊ฐ ๊น์ด ์ง ๋

## Sass Nesting | Parents & child

- HTML๊ณผ ๋น์ทํ ๊ตฌ์กฐ
- `์์`๊ณผ `์์๊ด๊ณ`๊ตฌ์กฐ
- ๋ด๋ถ์ ๋ค๋ฅธ ํ๊ทธ์ ์คํ์ผ์ ์ ์ฉ&๊ตฌํ
- ์ค๋ฅ ํด๊ฒฐ์ ์ฉ์ด
  - ๐  ๊ฐ๋ฐ์๋๊ตฌ: CSS๋ก ๋ณํ๋ ๊ฒ์ ํ์ธ ๊ฐ๋ฅ

```scss
// src/pages/Login/Login.scss

nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li {
    display: inline-block;
  }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

## Sass Nesting | ๋ณ์

- ๋ณ์ ์ค์ ๋ฒ : `$NAME`
- ์ต์๋จ์ ์ ์ธ
- ์์ฑ์ ๋ณ์๋ก ์ค์ 
- ์ฌ๋ฌ ๊ณณ์์ ์ฌ์ฉ๋๊ฑฐ๋ ์คํ๊ฐ ๋๊ธฐ ์ฌ์ด ์์ฑ์ ์ ์ฉ
  - ์์, HEX ์ฝ๋ ๋ฑ๋ฑ...

```css
// Sass ๋ณ์ ํ์ฉ ์์

$primary-color: #333;

body {
  border: 1px solid black;
  color: $primary-color;
}

.inverse {
  background-color: $primary-color;
  color: white;
}
```

## Sass Nesting | `& ์ ํ์`

- `&์ ํ์` ๋ถ๋ชจ ์ ํ์๋ก ์นํ

```scss
// Sass & ์ ํ์ ํ์ฉ ์์

button {
  width: 200px;
  height: 50px;

  &:hover {
    width: 400px;
    height: 100px;
  }
}

/* Compile to CSS */

button {
  width: 200px;
  height: 50px;
}

button:hover {
  width: 400px;
  height: 100px;
}
```

## Sass mixin | `๊ทธ๋ฃนํ`

- ์ค๋ณต๋๋ ์คํ์ผ ์์ฑ์ด ์ฌ๋ฌ๊ฐ์ผ๋ ํ๋ฒ์ ๋ฌถ๋ ๊ธฐ๋ฅ
- ` @mixin ๋ณ์ ์ด๋ฆ { ์ฌ๋ฌ ๊ฐ์ง ์คํ์ผ ์์ฑ }`
- ์ธ์๋ฅผ ๋ฃ์ด `์คํ์ผ ์์ฑ ์ ์ง & ์คํ์ผ ์์ฑ ์ ์ฉ ๋๋ ๊ฐ ๋ณ๊ฒฝ`
  - ํจ์๋ฅผ ์ฌ์ฉํ๋ ๊ฒ๊ณผ ๊ฐ์ด ์์ฑ์ ์ธ์๊ฐ ๋ฃ์ด ์ ์ฉ
  - ์ค๋ณต๋์ง๋ง ์์ฑ๊ฐ์ด ๋ฐ๋์ด์ผํ๋ ๊ฒฝ์ฐ์ ์ ํฉ

```css
@mixin flex() {
  //mixin
  //ํจ์์ฒ๋ผ ์ ์ธ&ํธ์ถ
  display: flex;
  justify-content: center;
  align-items: center;
}
```

```css
// Sass mixin ํ์ฉ ์์

@mixin flexCenter {
  display: flex;
  justify-content: center;
  align-items: center;
}

.info {
  @include flexCenter;
}
```

```css
// Sass mixin ์ธ์ ํ์ฉ ์์

@mixin flexSort($justify, $alignItems) {
  display: flex;
  justify-content: $justify;
  align-items: $alignItems;
}

.info {
  @include flexSort("space-between", "center");
}

.feed {
  @include flexSort("space-around", "center");
}
```

## Sass variable | `๋ถ๋ฌ์ค๊ธฐ`

- ์ ์ธ ํ์, ํ๋จ์์ ํธ์ถ๊ฐ๋ฅ
- variables.css์ ๋ณ์๋ mixin๋ฑ ๊ณตํต์ ์ ์ฉ๋๋ ์์ฑ์ ์์ฑ
- `@import` ์ฌ์ฉํ๊ณ ์ ํ๋ ํ์ผ์ `import`ํ์ฌ ๋ถ๋ฌ์ค๊ธฐ

```css
// src/styles/variables.scss

$primary-color: #333;

@mixin flexCenter {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

```css
// src/pages/Login/Login.scss

@import "../../styles/variables.scss" body {
  border: 1px solid black;
  color: $primary-color;
}

.inverse {
  @include flexCenter;
  color: white;
}
```

### Sass test codes!

```css
@mixin flex($justify, $align) //mixin์ ํจ์์ฒ๋ผ ์ฌ์ฉํ ๊ฒฝ์ฐ
 {
  display: flex;
  justify-content: $justify;
  align-items: $align;
}
.login {
// ๋ณ์ ์ค์ ๋ฒ : $NAME;
// ์ต์๋จ์ ์์น ํ๋จ์์ ํธ์ถ
$textColor: red;

// @mixin flex() {
//   //mixin
//   //ํจ์์ฒ๋ผ ์ ์ธ&ํธ์ถ
//   display: flex;
//   justify-content: center;
//   align-items: center;
// }

@mixin flex($justify, $align) //mixin์ ํจ์์ฒ๋ผ ์ฌ์ฉํ ๊ฒฝ์ฐ
 {
  display: flex;
  justify-content: $justify;
  align-items: $align;
}
.login {
  @include flex(space-around, flex-end);
  .title {
    background-color: purple;
    color: $textColor;
  }

  .article {
    background-color: green;
    color: $textColor;
    &:hover {
      // ๋ถ๋ชจ์ ํ์
      width: 200px;
      background-color: aqua;
    }
    &_children {
      // ๋ถ๋ชจ์ ํ์
      background-color: grey;
    }
  }
}
```

<hr>
E.O.D
