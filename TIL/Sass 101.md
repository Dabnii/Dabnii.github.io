# <p align="center"> 🦚 SASS

<p align="center"> <a href ="https://sass-lang.com/">📎 SASS</a>

## 🧞‍♀️ CSS Preprocessor

CSS전처리기:

- CSS의 불편한 문법을 보완 목적
- 전처리기 양식에 맞게 작성한 파일을 브라우저가 읽을 수 있는 CSS파일로 변환
- 여러 종류중 `SASS`를 소개 합니다.

## 🧞‍♀️ `SASS`

- `S`yntactically `A`wesome `S`tyle `S`heets
- 기존 CSS 파일의 취약점을 보완합니다

### 🧞‍♀️ `SASS` Install

```css
npm install sass
```

```json
//package.json -> dependencies 에서 sass 확인 필수
    "sass": "^4.14.1" 🔍
```

### 🧞‍♀️ `SASS` Basic syntax

- SASS의 두 가지 문법

| 문법       | 차이점                                        |
| ---------- | --------------------------------------------- |
| `.sass`    | `sass` 문법 활용                              |
| `.scss` 👍 | `cscc` 문법 활용 <br> 넓은 범용성 & CSS호환성 |

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

## 🧞‍♀️ `SASS` 적용하기

1. 기존의 CSS파일 확장자 SCSS로 변경

   - import한 CSS파일 → SCSS로 변경

1. 🤔 변환 후 발생하는 문제 해결하기

   - SPA 특성상 독립 되어있던 CSS가 router로 컴포넌트가 합쳐질 때 중복되는 선택자로 인한 오류 발생
   - className 변경
     - 많은양의 컴포넌트 관리가 어려움
     - 유지보수의 어려움 `에러발생 가능성이 높음`
   - 👍 CSS 자손결합자 사용

   ```js
   // src/pages/Login/Login.js

   import React from "react";
   import "./Login.scss";

   const Login = () => {
     return (
       <div className="login">
         {" "}
         // 1<h1 className="title">로그인 페이지입니다.</h1>
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

## 👍 CSS 자손결합자로 수정하기 | Sass nesting!

1. 최상위 부모 태그와 동일한 className 부여
   - 컴포넌트의 className은 중복이 불가 하다는 점을 이용
1. 컴포넌트와 CSS의 관계가 명확해짐

   - camelCase

1. `자손결합자`
   - 스타일을 적용하고 싶은 선택자 앞에 조상 선택자 ((부모의 부모 / 부모의 부모의 부모 ...)를 입력)
   - 정확하게 해당 요소를 선택할 수 있는 CSS 문법
   - `Sass nesting` 기능 : depth가 깊어 질 때

## Sass Nesting | Parents & child

- HTML과 비슷한 구조
- `자식`과 `자식관계`구조
- 내부의 다른 태그에 스타일을 적용&구현
- 오류 해결에 용이
  - 🛠 개발자도구: CSS로 변환된 것을 확인 가능

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

## Sass Nesting | 변수

- 변수 설정법 : `$NAME`
- 최상단에 선언
- 속성을 변수로 설정
- 여러 곳에서 사용되거나 오타가 나기 쉬운 속성에 유용
  - 색상, HEX 코드 등등...

```css
// Sass 변수 활용 예시

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

## Sass Nesting | `& 선택자`

- `&선택자` 부모 선택자로 치환

```scss
// Sass & 선택자 활용 예시

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

## Sass mixin | `그룹화`

- 중복되는 스타일 속성이 여러개일때 한번에 묶는 기능
- ` @mixin 변수 이름 { 여러 가지 스타일 속성 }`
- 인자를 넣어 `스타일 속성 유지 & 스타일 속성 적용 되는 값 변경`
  - 함수를 사용하는 것과 같이 속성에 인자값 넣어 적용
  - 중복되지만 속성값이 바뀌어야하는 경우에 적합

```css
@mixin flex() {
  //mixin
  //함수처럼 선언&호출
  display: flex;
  justify-content: center;
  align-items: center;
}
```

```css
// Sass mixin 활용 예시

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
// Sass mixin 인수 활용 예시

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

## Sass variable | `불러오기`

- 선언 하위, 하단에서 호출가능
- variables.css에 변수나 mixin등 공통에 적용되는 속성을 작성
- `@import` 사용하고자 하는 파일에 `import`하여 불러오기

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
@mixin flex($justify, $align) //mixin을 함수처럼 사용한 경우
 {
  display: flex;
  justify-content: $justify;
  align-items: $align;
}
.login {
// 변수 설정법 : $NAME;
// 최상단에 위치 하단에서 호출
$textColor: red;

// @mixin flex() {
//   //mixin
//   //함수처럼 선언&호출
//   display: flex;
//   justify-content: center;
//   align-items: center;
// }

@mixin flex($justify, $align) //mixin을 함수처럼 사용한 경우
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
      // 부모선택자
      width: 200px;
      background-color: aqua;
    }
    &_children {
      // 부모선택자
      background-color: grey;
    }
  }
}
```

<hr>
E.O.D
