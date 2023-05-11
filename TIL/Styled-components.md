# <p align="center">👩‍🎨 Styled-component </p>

## <p align="center">🏃 Install </p>

> styled-components & styled-reset

```
$ npm install styled-components styled-reset
```

## ⚒️ Reset CSS Styled-components

- 크로스브라우징을 위한 CSS reset

```
브라우저 간의 차이를 최대한 없애는 코드를 넣어, 브라우저 요소들의 스타일이 0인 상태에서 디자인을 만들어 나가기 위해 생겨난 것입니다. 초기화 혹은 일반적으로 바꿔주도록 누군가 만들어 놓은 좋은 소스 중에 하나입니다.
```

1. 위에서 설치한 `reset`적용
2. `index.js` 또는 `App.js`에 글로벌 스타일을 적용

```jsx
//GlobalStyle
import { createGlobalStyle } from 'styled-components';
import reset from 'styled-reset';

const GlobalStyles = createGlobalStyle`
${reset}

    a{
        text-decoration: none;
        color: inherit;
    }
    *{
        box-sizing: border-box;
    }
    input, textarea {
    -moz-user-select: auto;
    -webkit-user-select: auto;
    -ms-user-select: auto;
    user-select: auto;
    }
    input:focus {
    outline: none;
    }

    button {
    border: none;
    background: none;
    padding: 0;
    cursor: pointer;
    }
`;

export default GlobalStyles;
```

```jsx
//src > index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import Router from './Router';
import GlobalStyles from './styles/GlobalStyle';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <GlobalStyles />
    <Router />
  </React.StrictMode>
);
```
