# <p align="center"> 🌈 Westagram x React.js


## 🌈 Westagram | React.js `ver.1`

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
- `SCSS` 부모 선택자를 사용한 `disabled`, 불 필요한 코드 삭제 
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

<p align="center"> E.O.D 2022/11/6
<hr>
<br>

### <p align="center"> 📆 2022.Nov.12

## 🌈 Westagram | React.js `ver.2` 

📝 update log:

1. `Code review` & `Live code 리뷰`
2. `계산된 속성명`
3. `전개 구문` 
5. `map` 반복되는 UI 
6. `Props` & `setState`
1. `fetch`

### 🗝 핵심 포인트

📝 Code review
  > 서로의 코드를 확인하고, 보완 &발전 목적 <br>
  > 마이너한 부분 부터, 코드 리팩토링에 훌륭한 리소스들을 얻은 유의미한 시간 

1. `SCSS`
  - 부모 선택자 사용 
  - `@mixin` & `@include`
  - `$Variable` 변수 선택자 활용
2. `JSX`
  - `includes()` 와 `indexOf()` method 차이점
    ```javascript
    //indexOf
      const isValid = username.indexOf('@') !== -1 && password.length >= 5;
    //includes
      const isValid = username.includes('@') && password.length >= 5;
    ```
3. 📌 `계산된 속성명` | `Computed property names` ES6~

- 계산된 속성명
  - 꺽쇠괄호`([])` 로 속성 이름을 감싸면 속성 이름을 `동적`으로 만듬
  - 꺽쇠괄호 안에는 자바스크립트 `내장 함수, 메서드, 계산식, 변수를 넣음`
  - 순서 번호가 붙는 속성 이름을 여러개 사용하는 객체를 생성하는 경우
    > The `computed property names` feature was introduced in ECMAScript 2015(ES6) that allows you to dynamically compute the names of the object properties in JavaScript object literal notation.<br>
    >A JavaScript object is just a `collection of key-value pairs called properties.` A property's key is a string or symbol (also known as property name), and 📌 `value can be anything.`
  - 계산된 속성명을 사용하지 하는 경우와 그렇지 않은 경우 👇
 
  ```javascript
  // 계산된 속성명 미사용, 기존코드
  function makeObject1(key,value) {
      const obj = {};
      obj[key] = value;
      return obj
  }

  // 계산된 속성명 사용
  function makeObject2(key,value) {
      return {[key]:value}        
      // 계산된 속성명 [key]
  }
  //[key]값이 key의 이름으로 동적으로 할당된다.
  ```

  ```javascript
  //예시 2
  let idx = 0;
  let obj = {["name" + ++idx]: idx, ["name" + ++idx]: idx, ["name" + ++idx]: idx};
  console.log(obj);

  //{ name1: 1, name2: 2, name3: 3 }
  ```
  - 📌 프로젝트에 적용한 코드 
    - 장점: 코드 가독성이 높아지고, 효율적인 작업 가능

  ```javascript
  //const [id, setId] = useState('');
  //const [password, setPassword] = useState('');
  // 위의 두 코드를 저장된 속성명을 적용하면 아래처럼 작성할 수 있다.
  const [userInfo, setUserInfo] = useState({
    id: '',
    pw: '',
  });
  ```
4. `전개 구문` | `spread syntax`
    > 전개 구문을 사용하면 배열이나 문자열과 같이 반복 가능한 문자를 0개 이상의 인수 (함수로 호출할 경우) 또는 요소 (배열 리터럴의 경우)로 확장하여, 0개 이상의 키-값의 쌍으로 객체로 확장시킬 수 있습니다.

    ```javascript
    // 펼칠 대상이 객체인 경우
    {...obj}

    // 펼칠 대상이 배열인 경우
    [...arr]

    // 혹은
    {...arr}
    ```

    ```javascript
    //function saveUserId(event) {
    //setId(event.target.value);
    //}
    //function saveUserPw(event) {
    //setPassword(event.target.value);
    //}

    const handleUserInfo = e => {
      const { name, value } = e.target;
      setUserInfo(prev => ({ ...prev, [name]: value }));
    };
    ```
    ```javascript
    //Feed.js
    const handleClickBtn = () => {
    const pushedComment = [...commentList, coText];
    setCommentList(pushedComment);
    setCoText('');
    };
    ```

5. `map()` 반복되는 UI 
    - 작업을 하다 보니, 피드, 댓글과 같이 반복되는 UI, 컴포넌트가 있었다
    - 하드 코딩하지 않고 제작 하기 위하여 `map` `state` `props` 사용
    ```javascript
    //Feed.js
    import React from 'react';
    import './Comment.scss';

    export default function Comment(props) {
      const { contents } = props;
      return (
        <li>
          <span>0713.jpg </span>
          {contents}
        </li>
      );
    }
    ```
    ```javascript
    //FeedList.js
    import React from 'react';
    import { useState } from 'react';
    import { useEffect } from 'react';
    import Feed from './Feed';

    const FeedList = () => {
      const [feedData, setFeedData] = useState([]);

      useEffect(() => {
        fetch('/data/data.json')
          .then(response => response.json())
          .then(result => setFeedData(result));
      }, []);
      return feedData.map((feedinfo, i) => <Feed key={i} feedinfo={feedinfo} />);
    };

    export default FeedList;
    ```
6. `Props` & `setState`

    ```javascript
      //값을 바꾸고 싶으면 set함수를 사용
      //새로운 배열을 넣어야함 

      const handleClickBtn = () => {
        commentList.push(commentList);
        const pushedComment=[]
        setCommentList([...commentList]);
      //아래로 표현 가능 👇

        const pushedComments = [...commentList];
        setCommentList(pushedComments);
        setCommentInput('')
        // 코멘트 값 지워주기 ... value={commentInput}
        // state를 공통으로 넣어주기
        // 순환이 됨

        // 	 const pushedComments = [...commentList, commentInput];
        // 코멘트 리스트 뒤에 인풋을 추가, 배열처럼 추가하는 것
    ```

  1. 상수 데이터 
      > 동적으로 변하지 않아 백엔드 API 등을 통해서 가져올 필요가 없는 `정적인 데이터`<br>
      > 반복되는 UI 구조는 상수 데이터와 `map 메서드를 활용해 간결하게 표현` 가능<br>
      > UI를 효율적으로, 확장성 있게 구성 가능 `유지보수가 용이`<br>
      > 컴포넌트 파일 내부에서 선언하거나, 별도의 파일로 분리해서 사용<br>

      ```javascript
      //data.js
      const ASIDE_LIST = [
      { id: 1, text: '소개' },
      { id: 2, text: '도움말' },
      { id: 3, text: '홍보 센터' },
      { id: 4, text: 'API' },
      { id: 5, text: '채용 정보' },
      { id: 6, text: '개인정보처리방침' },
      { id: 7, text: '약관' },
      { id: 8, text: '위치' },
      { id: 9, text: '인기 계정' },
      { id: 10, text: '해시태그' },
      { id: 11, text: '언어' },
      ];
      export default ASIDE_LIST;
      ```  
      ```javascript
      //Main.js
      import ASIDE_LIST from './data'; 
      //...
      <ul className="aside_list">
        {ASIDE_LIST.map(el => {
          return <li key={el.id}>{el.text}•</li>;
        })}
      </ul>
      //다시 등장한 map
      //UI를 그려주고 싶은 곳에 상수 데이터를 넣어준다
      ```

  1. `Fetch`  
      - Fetch: 특정정보가 필요할 때 클라이언트는 서버에 HTTP 통신으로 요청 리퀘스트를 보내고 정보 응답을 받음.
      - `데이터 생성,수정,삭제` 가능

      ```javascript
      fetch(”API주소”, {
      method:”post”,
      headers: 해당 통신에 대한 대략적인 정보(//부가적인정보/콘첸츠의 타입),
      body: 실질적인 데이터 
      //body: JSON
      // id, password 
      })

      //보낼 때 JSON으로 넘겨야 함
      //JavaScript→ Json으로 보낼 때  
      JSON.stringfy(id,password)
      ({userId:id, userPassword:password})
      ```
<p align="center"> E.O.D 2022/11/6

  


<hr>
출처: 

- https://attacomsian.com/blog/javascript-computed-property-names

- https://velog.io/@kwonh/ES6-%EB%8B%A8%EC%B6%95%EC%86%8D%EC%84%B1%EB%AA%85-%EA%B3%84%EC%82%B0%EB%90%9C%EC%86%8D%EC%84%B1%EB%AA%85-%EB%B9%84%EA%B5%AC%EC%A1%B0%ED%99%94%ED%95%A0%EB%8B%B9-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0

- https://blogpack.tistory.com/640

- https://bigtop.tistory.com/

- https://www.daleseo.com/js-window-fetch/