# <p align="center"> 🌈 Westagram x React.js

## 🌈 Westagram | React.js

1. `Login page`

   - `SCSS`
   - `Java script & HTML`

2. `Feed page` 🛠

   - `SCSS`
   - `Java script & HTML`

<hr>

## 1️⃣ Log-in page

### 📌 JavaScript 필수구현 항목

- JavaScript
  - `Props` + `State`를 사용한 로그인 정보 저장 기능
    > ✅ `[Login]` 사용자 입력 데이터 저장
    >
    > 다음의 순서에 맞게 코드를 작성하여 ID, Password `<input>`에 입력된 값을 state에 저장해주세요. <br>
    > ID `<input>`에서 onChange event가 발생합니다.<br>
    > event 발생 시 saveUserId 함수가 실행됩니다.<br>
    > saveUserId 함수는 이벤트를 인자로 받습니다.<br>
    > event가 일어난 요소에 담긴 `value 값(event.target.value)을 state`에 저장합니다.<br>
    > 위의 과정을 Password `<input>` 에도 동일하게 적용합니다.<br>
  - 로그인 버튼 활성화 `Validation`
    > ✅ `[Login]` 로그인 버튼 활성화(validation)
    >
    > 입력한 아이디와 비밀번호가 기준에 맞는 경우에만 로그인 버튼 색상이 활성화될 수 있도록 합니다. 색상뿐 아니라 버튼의 > `disabled` 여부도 같이 조작해주세요.<br> `(e.g., ID - @ 포함 / Password - 5글자 이상)`<br>
    > 삼항 연산자를 적용해서 조건에 따라 버튼 색상에 변화를 주시기 바랍니다.<br>

<br>

## 📌 JSX & HTML | 2022.Nov.6

### 📝 코드 들여다보기

```jsx
//jsx
import React, { useState } from "react";
import { Navigate, useNavigate } from "react-router-dom";
import "./Logindabin.scss";

export default function Login() {
  const [username, setUsername] = useState("");
  //Hook
  const [password, setPassword] = useState("");
  const navigate = useNavigate();

  const saveUserId = (event) => {
    setUsername(event.target.value);
  };
  const savePwValue = (event) => {
    setPassword(event.target.value);
  };

  const isValid = username.indexOf("@") !== -1 && password.length >= 5;
  // -1은 없다, @가 없지 않다면 && 비밀번호가 길이가 5자 이상이라면 버튼 온!

  const loginSucess = () => {
    isValid ? navigate("/main-dabin") : alert("비밀번호를 확인해주세요!");
    //navigate의 소문자
  };

  const disable = isValid ? false : true;

  return (
    <div className="body">
      <div className="login-container">
        <h1 className="instagram-logo">westagram</h1>
        <form
          className="login-box"
          onSubmit={(event) => {
            event.preventDefault();
          }}
        >
          <input
            id="id-input"
            type="text"
            placeholder="아이디를 입력해주세요"
            onChange={saveUserId}
          />
          <input
            type="password"
            id="password-input"
            placeholder="비밀번호"
            onChange={savePwValue}
          />
          <button
            disabled={disable}
            className={"loginBtn"}
            onClick={loginSucess}
          >
            로그인하기
          </button>
          <h3 className="login-failure_help">비밀번호를 잊으셨나요?</h3>
        </form>
      </div>
    </div>
  );
}
```

```scss
//scss
@import url("https://fonts.googleapis.com/css2?family=Lobster&family=Lobster+Two:ital,wght@0,400;0,700;1,400;1,700&family=Noto+Sans+KR:wght@100;300;400;500;700;900&display=swap");

/* 최상위 div*/

@mixin backgroundColor {
  background-color: #fafafa;
}

@mixin loginBtnAtr {
  background-color: #2962ff;
  appearance: unset;
  border: none;
  border-radius: 0.3rem;
  padding: 0.5rem;
  color: white;
}

body {
  display: flex;
  width: 100vw;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  flex-wrap: nowrap;
  text-align: center;
  @include backgroundColor;

  /* 로그인 div */
  .login-container {
    margin-top: 3rem;
    border: 0.5px solid #e6e6e6;
    background-color: white;
    padding: 3rem 2.5rem 1rem 2.5rem;

    .instagram-logo {
      font-family: "Lobster", cursive;
      font-size: 3rem;
      margin-top: 0;
      margin-bottom: 4rem;
      font-weight: 200;
    }

    /* 로그인 input form */

    .login-box {
      display: flex;
      flex-wrap: nowrap;
      flex-direction: column;
      gap: 1rem;
    }

    /* 로그인 ID & PW input */

    input {
      outline: none;
      appearance: unset;
      justify-items: center;
      width: 15rem;
      padding: 0.5rem;
      border: 1px solid #efefef;
      border-radius: 0.1rem;
      @include backgroundColor;
    }

    input #text {
      color: #999999;
      font-size: small;
    }
  }

  /* 로그인 btn */

  /* 로그인 성공 btn */

  .loginBtn {
    @include loginBtnAtr;
    opacity: 100%;

    &:disabled {
      @include loginBtnAtr;
      opacity: 30%;
    }
  }

  .login-failure_help {
    font-family: "Noto Sans KR", sans-serif;
    font-size: 0.8rem;
    font-weight: 500;
    color: #003668;
    margin: 2rem 0 1rem 0;
  }
}

/* E.O.D */
```

### 🗝 핵심 포인트

📌 `JXS`

- `indexOf()`
  - Id에 찾고자 하는 string 객체에서 주어진 값과 일치하는 첫 인덱스를 반환, 일치하는 값이 없다면 -1 반환
- `disabled`
  - On/Off 추가 css 작성이 필요없음
- `navigate`
  - 조건을 통한 페이지 이동시 사용
- `event.target.value`

📌 `SCSS`

- 자손 선택자 `&:`를 이용한 `disabled` 버튼의 색상 변경

  - 불필요한 또 다른 SCSS 버튼을 생성을 지양 목적
  - default로 활성화 → disabled

    ```SCSS
    .loginBtn {
        @include loginBtnAtr;
        opacity: 100%;

        &:disabled {
        @include loginBtnAtr;
        opacity: 30%;
        }
    }
    ```

    ```jsx
    <button
        disabled={disable}
        className={"loginBtn"}
        onClick={loginSucess}
    >
    ```

### 🌳 성장 포인트

- `input` 오브젝트 값 확인 방법

  ```jsx
  const saveUserId = (event) => {
    setUsername(event.target.value);
  };
  ```

- `preventDefault`는 btn이 아닌 `form`에 설정
- `SCSS` 자손 선택자를 사용한 `disabled`, 불 필요한 코드 삭제
- `React`의 장점인 선언적 개발 환경 이해
- `Hook` 학습
  - 1️⃣ `import React, { useState } from "react"` : 최상위
  - 2️⃣ `const [username, setUsername] = useState("")` : `return` 위
  - `useState("")` → 스트링으로 값을 받음
  - `useState([])` → 배열로 받음
    - 값을 어떻게 받을지 미리 암시
- `Props` & `State` 학습

  - `const savePwValue = (event) => { setPassword(event.target.value); }`
  - id입력 창의 value를 userId `state에 저장해주는 함수`

- `onChange` : input의 변경에 반응하는 이벤트

<hr>
<p align="center"> E.O.D 2022/11/6
