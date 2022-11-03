# <p align="center"> 🧢 React Component

## 📌 Component

- ✨ `재활용 가능한 UI 구성단위`
- 유지보수의 용이함 : `독립적으로 사용`할 수 있음
- 부모/자식 관계 성립가능: 다른 컴포넌트를 포함할 수 있음
- 페이지 구성 확인이 쉬움

## 📌 Component types

| &#32;    | Class component                | Function component            |
| -------- | ------------------------------ | ----------------------------- |
| 난이도   | 심화 및 필수!                  | 초심자에게 추천               |
| 필수사항 | ✨ `render()` 메서드           | &#32;                         |
| 특징     | State & Lifecycle API 사용가능 | Hook 등장이후 `state`사용가능 |

## 👨‍🏫 Class component

```jsx
import React from "react";

class App extends React.Component {
  ✨ render() {
    return <h1>This is Class Component!</h1>;
  }
}

export default App;
```

## 📦 Function component

```jsx
import React from "react";

const App = () => {
  return <h1>This is Function Component!</h1>;
};

export default App;
```

<hr>

## 📌 Component 사용하기

1. 규칙:

- 컴포넌트의 첫 글자는 `대 문자`
  - `<Title />` Component
  - `<button>` HTML tag

2. Basic syntax

   ### ✨ `const,let name = <tag eventlisner function console.log > text <closing tag>`

```jsx
const element = (
 <h1 className="greeting!">
	Hello, world!
 <h1>
);
```

<a href="#"> 이전글: React 101</a>

<a href="#"> 다음글: React 101</a>

<hr>
<p align="center"> E.O.D
