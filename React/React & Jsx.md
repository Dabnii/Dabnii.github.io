# <p align="center"> 🧢 React & JSX

## 📌 `JSX` : (`J`avaScript `S`yntax e`X`tension)

- 리액트에서 사용하는 자바스크립트 `확장 문법`
- HTML과 자바스크립트 로직을 `하나의 자바스크립트 파일 안에서 모두 처리` 목적
- `HTML과 유사한 형태로` 사용
- 하나의 자바스크립트 파일에서 HTML과 자바스크립트 `로직을 동시`에 작성
- JSX로 작성한 코드는 Babel로 일반 자바스크립트 코드 형태로 변환

```jsx
const element = (
 <h1 className="greeting!">
	Hello, world!
 <h1>
);
```

```jsx
//Babel 변환
const element = React.creatElement(
  "h1",
  { className: "greeting" },
  "Hello, world!"
);
```

## 📌 `JSX` 특징

- 하나의 자바스크립트 파일로 HTML, js 작성 가능
- 하나의 자바스크립트를 통해 로직을 작성으로 편리함

## 📌 `JSX` 문법

<br>

### 1. JSX element

- 자바스크립트에서 HTML 작성 가능 👇

```jsx
const hi = <p>Hi</p>;
```

<br>

### 2.`{ Javascript 표현식 }`

- `{ ... JavaScript... }`

  - 유효한 자바스크립트 표현식 작성 가능 👇

    ```jsx
    // Greetings.js
    import React from "react";

    const Greetings = () => {
      const name = "김개발";

      return <h1>{name}님, Welcome to Wecode!</h1>;
    };

    export default Greetings;
    ```

### 3. JSX attribute

- attribute name(속성명)은 `camelCase`로 작성
- ✨ `class` → `className`

```jsx
//HTML
<h1 class="greetings">Welcome!</h1>

// JSX
<h1 className="greetings">Welcome!</h1>
```

### 4. Event 처리하기

- `on` + `event`
- 함수 이베트 핸들러를 전달

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

- camelCase를 요소로 가지는 자바스크립트 객체를 받음
  - 중괄호를 두 번 겹친 형태로 사용
- `{ 바깥 }` = JSX 문법
- `{ 안쪽 }`= JS obj
- CSS 보다 우선순위 높고, 성능이 낮음
- ~~동적 스타일링시 사용지양~~

```javascript
// HTML
<h1 style="color:red;background-image:yellow">Welcome to Wecode!</h1>

// JSX
<h1 style={{ color: "red", backgroundImage: "yellow" }}>
  Welcome to Wecode!
</h1>
```

### 6. `<Self-Closing Tag / >`

- 어떤 태그든 self-closing-tag 가능!

### 7. `<div>` Nested JSX `</div>`

- Why?
  - `virtual DOM`의 컴포넌트 변화를 효율적으로 비교할 수 있도록 한 컴포넌트는 `하나의 DOM 트리 구조`로 이루어져야 한다는 `규칙`

```jsx
// Bad
const Greetings = () => {
  return (
    <h1>김개발님!</h1>
    <h2>위코드에 오신 걸 환영합니다!</h2>
  );
}

// Good
const Greetings = () => {
  return (
    <div>
      <h1>김개발님!</h1>
      <h2>위코드에 오신 걸 환영합니다!</h2>
    </div>
  );
}
```

### 8. `<>` React.Fragment `</>`

- ` <>``</> `
- 단축된 버전으로 작성 가능
- 추가적인 DOM element가 필요없음
- 간단하게 하나의 컴포넌트에 여러 요소(자식)을 그룹화

```jsx
const Greetings = () => {
  return (
    <>
      <h1>이렇게</h1>
      <h2>쉽게 그룹화 가능! 👏👏</h2>
    </>
  );
};
```

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20component.md"> 이전글: React Component </a>

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20Hook.md"> 다음글: React Hook </a>

<hr>
<p align="center"> E.O.D
