## <p align="center"> π 1/10

### π¨ 'react-dom' which is not supported

<img width="533" alt="react-dom is not supported" src="https://user-images.githubusercontent.com/110847597/211842990-a8022d9d-34d6-4f74-9a10-9b245debe996.png">

- React 18λ²μ  λΆν° `react-dom`μ λ μ΄μ μ§μνμ§ μλλ€.
- `react-dom/client`μΌλ‘ λ°λ₯΄κ² μν¬νΈ π
- μ¬μ€ κ΄λ ¨ κΈμ λ μ°Ύμλ³΄λ λΉλ¨ μ½λ ν λμ€λ‘ ν΄κ²°λλ κ²μ΄ μλλ€..
- λ κ°μ§μ λ°©λ²μ΄ μλλ° λ κ³΅λΆν  κ²μ΄ λμλ€!
  - `ReactDOM.render` VS `createRoot`
  - `hydration`

```jsx
//Before
import ReactDOM from "react-dom"; // ποΈ wrong import path
```

```jsx
//After π―
import ReactDOM from "react-dom/client"; // ποΈ right import path
```

### Overview

React 18 ships two root APIs, which we call the Legacy Root API and the New Root API.

> - Legacy root API: This is the existing API called with ReactDOM.render. This creates a root running in βlegacyβ mode, which works exactly the same as React 17. Before release, we will add a warning to this API indicating that itβs deprecated and to switch to the New Root API.
> - New root API: The new Root API is called with ReactDOM.createRoot. This creates a root running in React 18, which adds all of the improvements of React 18 and allows you to use concurrent features. This will be the root API moving forward.

### Why ship both?

Weβre shipping the legacy API in React 18 for two reasons:

> - Smooth upgrade: We want to avoid user upgrading to React 18 and immediately seeing a crash. Instead, weβre adding a warning to the legacy root API that recommends using the new API.
> - Experimentation: Some apps may choose to run a production experiment to compare the legacy root with the new root which includes performance improvements out of the box. By including both, itβs easier to run experiments.

[π Replacing render with createRoot #5](https://github.com/reactwg/react-18/discussions/5)

[π You are importing createRoot from 'react-dom' which is not supported](https://bobbyhadz.com/blog/react-you-are-importing-createroot-from-react-dom)

[π ReactDOMClient](https://reactjs.org/docs/react-dom-client.html)

[π React 18μ ReactDOMClient.createRoot](https://velog.io/@ggong/React-18%EC%97%90%EC%84%9C-ReactDOM.render-%EB%8C%80%EC%8B%A0-createRoot-%EC%93%B0%EA%B8%B0)

---

## <p align="center"> π 1/11

### βοΈ Upload Local Git to GitHub!

- λ‘μ»¬κ³Ό μκ²©μ μ₯μ μ°κ²°μ΄ μλ  λ
- π‘ μκ²© λ νμ§ν λ¦¬ λ§λ€ λ `README.md`λ₯Ό λΉΌκ³  μμ±νκΈ°

```jsx
$ git remote -v
//νμ¬ λ νμ§ν λ¦¬μ μκ²© λ§ν¬λ₯Ό νμΈ
//origin folk url
//upstream μλ λ νμ§ν λ¦¬ url
```

1. λ νμ§ν λ¦¬ urlμ νμΈνλ€
1. κΉ μ»€λ° β νΈμ¬λ₯Ό μ§ννλ€!
1. DONE!π

[π μκ²©μ μ₯μ μΆκ° - git remote add](https://shanepark.tistory.com/284)

---
