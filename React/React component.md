# <p align="center"> π§’ React Component

## π Component

- β¨ `μ¬νμ© κ°λ₯ν UI κ΅¬μ±λ¨μ`
- μ μ§λ³΄μμ μ©μ΄ν¨ : `λλ¦½μ μΌλ‘ μ¬μ©`ν  μ μμ
- λΆλͺ¨/μμ κ΄κ³ μ±λ¦½κ°λ₯: λ€λ₯Έ μ»΄ν¬λνΈλ₯Ό ν¬ν¨ν  μ μμ
- νμ΄μ§ κ΅¬μ± νμΈμ΄ μ¬μ

## π Component types

| &#32;    | Class component                | Function component            |
| -------- | ------------------------------ | ----------------------------- |
| λμ΄λ   | μ¬ν λ° νμ!                  | μ΄μ¬μμκ² μΆμ²               |
| νμμ¬ν­ | β¨Β `render()` λ©μλ           | &#32;                         |
| νΉμ§     | State & Lifecycle API μ¬μ©κ°λ₯ | Hook λ±μ₯μ΄ν `state`μ¬μ©κ°λ₯ |

## π¨βπ« Class component

```jsx
import React from "react";

class App extends React.Component {
  β¨ render() {
    return <h1>This is Class Component!</h1>;
  }
}

export default App;
```

## π¦ Function component

```jsx
import React from "react";

const App = () => {
  return <h1>This is Function Component!</h1>;
};

export default App;
```

<hr>

## π Component μ¬μ©νκΈ°

1. κ·μΉ:

- μ»΄ν¬λνΈμ μ²« κΈμλ `λ λ¬Έμ`
  - `<Title />` Component
  - `<button>` HTML tag

2. Basic syntax

   ### β¨ `const,let name = <tag eventlisner function console.log > text <closing tag>`

```jsx
const element = (
 <h1 className="greeting!">
	Hello, world!
 <h1>
);
```

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20101.md#"> μ΄μ κΈ: React 101</a>

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20%26%20Jsx.md"> λ€μκΈ: React & JSX</a>

<hr>
<p align="center"> E.O.D
