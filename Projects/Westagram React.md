# <p align="center"> π Westagram x React.js

## π Westagram | React.js `ver.1`

1. `Login page`

   - `SCSS`
   - `Java script & HTML`

2. `Feed page` π 

   - `SCSS`
   - `Java script & HTML`

<hr>

## 1οΈβ£ Log-in page

### π JavaScript νμκ΅¬ν ν­λͺ©

- JavaScript
  - `Props` + `State`λ₯Ό μ¬μ©ν λ‘κ·ΈμΈ μ λ³΄ μ μ₯ κΈ°λ₯
    > β `[Login]` μ¬μ©μ μλ ₯ λ°μ΄ν° μ μ₯
    >
    > λ€μμ μμμ λ§κ² μ½λλ₯Ό μμ±νμ¬ ID, Password `<input>`μ μλ ₯λ κ°μ stateμ μ μ₯ν΄μ£ΌμΈμ. <br>
    > ID `<input>`μμ onChange eventκ° λ°μν©λλ€.<br>
    > event λ°μ μ saveUserId ν¨μκ° μ€νλ©λλ€.<br>
    > saveUserId ν¨μλ μ΄λ²€νΈλ₯Ό μΈμλ‘ λ°μ΅λλ€.<br>
    > eventκ° μΌμ΄λ μμμ λ΄κΈ΄ `value κ°(event.target.value)μ state`μ μ μ₯ν©λλ€.<br>
    > μμ κ³Όμ μ Password `<input>` μλ λμΌνκ² μ μ©ν©λλ€.<br>
  - λ‘κ·ΈμΈ λ²νΌ νμ±ν `Validation`
    > β `[Login]` λ‘κ·ΈμΈ λ²νΌ νμ±ν(validation)
    >
    > μλ ₯ν μμ΄λμ λΉλ°λ²νΈκ° κΈ°μ€μ λ§λ κ²½μ°μλ§ λ‘κ·ΈμΈ λ²νΌ μμμ΄ νμ±νλ  μ μλλ‘ ν©λλ€. μμλΏ μλλΌ λ²νΌμ > `disabled` μ¬λΆλ κ°μ΄ μ‘°μν΄μ£ΌμΈμ.<br> `(e.g., ID - @ ν¬ν¨ / Password - 5κΈμ μ΄μ)`<br>
    > μΌν­ μ°μ°μλ₯Ό μ μ©ν΄μ μ‘°κ±΄μ λ°λΌ λ²νΌ μμμ λ³νλ₯Ό μ£ΌμκΈ° λ°λλλ€.<br>

<br>

## π JSX & HTML | 2022.Nov.6

### π μ½λ λ€μ¬λ€λ³΄κΈ°

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
  // -1μ μλ€, @κ° μμ§ μλ€λ©΄ && λΉλ°λ²νΈκ° κΈΈμ΄κ° 5μ μ΄μμ΄λΌλ©΄ λ²νΌ μ¨!

  const loginSucess = () => {
    isValid ? navigate("/main-dabin") : alert("λΉλ°λ²νΈλ₯Ό νμΈν΄μ£ΌμΈμ!");
    //navigateμ μλ¬Έμ
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
            placeholder="μμ΄λλ₯Ό μλ ₯ν΄μ£ΌμΈμ"
            onChange={saveUserId}
          />
          <input
            type="password"
            id="password-input"
            placeholder="λΉλ°λ²νΈ"
            onChange={savePwValue}
          />
          <button
            disabled={disable}
            className={"loginBtn"}
            onClick={loginSucess}
          >
            λ‘κ·ΈμΈνκΈ°
          </button>
          <h3 className="login-failure_help">λΉλ°λ²νΈλ₯Ό μμΌμ¨λμ?</h3>
        </form>
      </div>
    </div>
  );
}
```

```scss
//scss
@import url("https://fonts.googleapis.com/css2?family=Lobster&family=Lobster+Two:ital,wght@0,400;0,700;1,400;1,700&family=Noto+Sans+KR:wght@100;300;400;500;700;900&display=swap");

/* μ΅μμ div*/

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

  /* λ‘κ·ΈμΈ div */
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

    /* λ‘κ·ΈμΈ input form */

    .login-box {
      display: flex;
      flex-wrap: nowrap;
      flex-direction: column;
      gap: 1rem;
    }

    /* λ‘κ·ΈμΈ ID & PW input */

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

  /* λ‘κ·ΈμΈ btn */

  /* λ‘κ·ΈμΈ μ±κ³΅ btn */

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

### π ν΅μ¬ ν¬μΈνΈ

π `JXS`

- `indexOf()`
  - Idμ μ°Ύκ³ μ νλ string κ°μ²΄μμ μ£Όμ΄μ§ κ°κ³Ό μΌμΉνλ μ²« μΈλ±μ€λ₯Ό λ°ν, μΌμΉνλ κ°μ΄ μλ€λ©΄ -1 λ°ν
- `disabled`
  - On/Off μΆκ° css μμ±μ΄ νμμμ
- `navigate`
  - μ‘°κ±΄μ ν΅ν νμ΄μ§ μ΄λμ μ¬μ©
- `event.target.value`

π `SCSS`

- μμ μ νμ `&:`λ₯Ό μ΄μ©ν `disabled` λ²νΌμ μμ λ³κ²½

  - λΆνμν λ λ€λ₯Έ SCSS λ²νΌμ μμ±μ μ§μ λͺ©μ 
  - defaultλ‘ νμ±ν β disabled

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

### π³ μ±μ₯ ν¬μΈνΈ

- `input` μ€λΈμ νΈ κ° νμΈ λ°©λ²

  ```jsx
  const saveUserId = (event) => {
    setUsername(event.target.value);
  };
  ```

- `preventDefault`λ btnμ΄ μλ `form`μ μ€μ 
- `SCSS` λΆλͺ¨ μ νμλ₯Ό μ¬μ©ν `disabled`, λΆ νμν μ½λ μ­μ 
- `React`μ μ₯μ μΈ μ μΈμ  κ°λ° νκ²½ μ΄ν΄
- `Hook` νμ΅
  - 1οΈβ£ `import React, { useState } from "react"` : μ΅μμ
  - 2οΈβ£ `const [username, setUsername] = useState("")` : `return` μ
  - `useState("")` β μ€νΈλ§μΌλ‘ κ°μ λ°μ
  - `useState([])` β λ°°μ΄λ‘ λ°μ
    - κ°μ μ΄λ»κ² λ°μμ§ λ―Έλ¦¬ μμ
- `Props` & `State` νμ΅

  - `const savePwValue = (event) => { setPassword(event.target.value); }`
  - idμλ ₯ μ°½μ valueλ₯Ό userId `stateμ μ μ₯ν΄μ£Όλ ν¨μ`

- `onChange` : inputμ λ³κ²½μ λ°μνλ μ΄λ²€νΈ

<p align="center"> E.O.D 2022/11/6
<hr>
<br>

### <p align="center"> π 2022.Nov.12

## π Westagram | React.js `ver.2`

π update log:

1. `Code review` & `Live code λ¦¬λ·°`
2. `κ³μ°λ μμ±λͺ`
3. `μ κ° κ΅¬λ¬Έ`
4. `map` λ°λ³΅λλ UI
5. `Props` & `setState`
6. `fetch`

### π ν΅μ¬ ν¬μΈνΈ

π Code review

> μλ‘μ μ½λλ₯Ό νμΈνκ³ , λ³΄μ &λ°μ  λͺ©μ  <br>
> λ§μ΄λν λΆλΆ λΆν°, μ½λ λ¦¬ν©ν λ§μ νλ₯­ν λ¦¬μμ€λ€μ μ»μ μ μλ―Έν μκ°

1. `SCSS`

- λΆλͺ¨ μ νμ μ¬μ©
- `@mixin` & `@include`
- `$Variable` λ³μ μ νμ νμ©

2. `JSX`

- `includes()` μ `indexOf()` method μ°¨μ΄μ 
  ```javascript
  //indexOf
  const isValid = username.indexOf("@") !== -1 && password.length >= 5;
  //includes
  const isValid = username.includes("@") && password.length >= 5;
  ```

3. π `κ³μ°λ μμ±λͺ` | `Computed property names` ES6~

- κ³μ°λ μμ±λͺ

  - κΊ½μ κ΄νΈ`([])` λ‘ μμ± μ΄λ¦μ κ°μΈλ©΄ μμ± μ΄λ¦μ `λμ `μΌλ‘ λ§λ¬
  - κΊ½μ κ΄νΈ μμλ μλ°μ€ν¬λ¦½νΈ `λ΄μ₯ ν¨μ, λ©μλ, κ³μ°μ, λ³μλ₯Ό λ£μ`
  - μμ λ²νΈκ° λΆλ μμ± μ΄λ¦μ μ¬λ¬κ° μ¬μ©νλ κ°μ²΄λ₯Ό μμ±νλ κ²½μ°
    > The `computed property names` feature was introduced in ECMAScript 2015(ES6) that allows you to dynamically compute the names of the object properties in JavaScript object literal notation.<br>
    > A JavaScript object is just a `collection of key-value pairs called properties.` A property's key is a string or symbol (also known as property name), and π `value can be anything.`
  - κ³μ°λ μμ±λͺμ μ¬μ©νμ§ νλ κ²½μ°μ κ·Έλ μ§ μμ κ²½μ° π

  ```javascript
  // κ³μ°λ μμ±λͺ λ―Έμ¬μ©, κΈ°μ‘΄μ½λ
  function makeObject1(key, value) {
    const obj = {};
    obj[key] = value;
    return obj;
  }

  // κ³μ°λ μμ±λͺ μ¬μ©
  function makeObject2(key, value) {
    return { [key]: value };
    // κ³μ°λ μμ±λͺ [key]
  }
  //[key]κ°μ΄ keyμ μ΄λ¦μΌλ‘ λμ μΌλ‘ ν λΉλλ€.
  ```

  ```javascript
  //μμ 2
  let idx = 0;
  let obj = {
    ["name" + ++idx]: idx,
    ["name" + ++idx]: idx,
    ["name" + ++idx]: idx,
  };
  console.log(obj);

  //{ name1: 1, name2: 2, name3: 3 }
  ```

  - π νλ‘μ νΈμ μ μ©ν μ½λ
    - μ₯μ : μ½λ κ°λμ±μ΄ λμμ§κ³ , ν¨μ¨μ μΈ μμ κ°λ₯

  ```javascript
  //const [id, setId] = useState('');
  //const [password, setPassword] = useState('');
  // μμ λ μ½λλ₯Ό μ μ₯λ μμ±λͺμ μ μ©νλ©΄ μλμ²λΌ μμ±ν  μ μλ€.
  const [userInfo, setUserInfo] = useState({
    id: "",
    pw: "",
  });
  ```

4.  `μ κ° κ΅¬λ¬Έ` | `spread syntax`

    > μ κ° κ΅¬λ¬Έμ μ¬μ©νλ©΄ λ°°μ΄μ΄λ λ¬Έμμ΄κ³Ό κ°μ΄ λ°λ³΅ κ°λ₯ν λ¬Έμλ₯Ό 0κ° μ΄μμ μΈμ (ν¨μλ‘ νΈμΆν  κ²½μ°) λλ μμ (λ°°μ΄ λ¦¬ν°λ΄μ κ²½μ°)λ‘ νμ₯νμ¬, 0κ° μ΄μμ ν€-κ°μ μμΌλ‘ κ°μ²΄λ‘ νμ₯μν¬ μ μμ΅λλ€.

    ```javascript
    // νΌμΉ  λμμ΄ κ°μ²΄μΈ κ²½μ°
    {...obj}

    // νΌμΉ  λμμ΄ λ°°μ΄μΈ κ²½μ°
    [...arr]

    // νΉμ
    {...arr}
    ```

    ```javascript
    //function saveUserId(event) {
    //setId(event.target.value);
    //}
    //function saveUserPw(event) {
    //setPassword(event.target.value);
    //}

    const handleUserInfo = (e) => {
      const { name, value } = e.target;
      setUserInfo((prev) => ({ ...prev, [name]: value }));
    };
    ```

    ```javascript
    //Feed.js
    const handleClickBtn = () => {
      const pushedComment = [...commentList, coText];
      setCommentList(pushedComment);
      setCoText("");
    };
    ```

5.  `map()` λ°λ³΅λλ UI

    - μμμ νλ€ λ³΄λ, νΌλ, λκΈκ³Ό κ°μ΄ λ°λ³΅λλ UI, μ»΄ν¬λνΈκ° μμλ€
    - νλ μ½λ©νμ§ μκ³  μ μ νκΈ° μνμ¬ `map` `state` `props` μ¬μ©

    ```javascript
    //Feed.js
    import React from "react";
    import "./Comment.scss";

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
    import React from "react";
    import { useState } from "react";
    import { useEffect } from "react";
    import Feed from "./Feed";

    const FeedList = () => {
      const [feedData, setFeedData] = useState([]);

      useEffect(() => {
        fetch("/data/data.json")
          .then((response) => response.json())
          .then((result) => setFeedData(result));
      }, []);
      return feedData.map((feedinfo, i) => (
        <Feed key={i} feedinfo={feedinfo} />
      ));
    };

    export default FeedList;
    ```

6.  `Props` & `setState`

    ```javascript
      //κ°μ λ°κΎΈκ³  μΆμΌλ©΄ setν¨μλ₯Ό μ¬μ©
      //μλ‘μ΄ λ°°μ΄μ λ£μ΄μΌν¨

      const handleClickBtn = () => {
        commentList.push(commentList);
        const pushedComment=[]
        setCommentList([...commentList]);
      //μλλ‘ νν κ°λ₯ π

        const pushedComments = [...commentList];
        setCommentList(pushedComments);
        setCommentInput('')
        // μ½λ©νΈ κ° μ§μμ£ΌκΈ° ... value={commentInput}
        // stateλ₯Ό κ³΅ν΅μΌλ‘ λ£μ΄μ£ΌκΈ°
        // μνμ΄ λ¨

        // 	 const pushedComments = [...commentList, commentInput];
        // μ½λ©νΈ λ¦¬μ€νΈ λ€μ μΈνμ μΆκ°, λ°°μ΄μ²λΌ μΆκ°νλ κ²
    ```

7.  μμ λ°μ΄ν°

    > λμ μΌλ‘ λ³νμ§ μμ λ°±μλ API λ±μ ν΅ν΄μ κ°μ Έμ¬ νμκ° μλ `μ μ μΈ λ°μ΄ν°`<br>
    > λ°λ³΅λλ UI κ΅¬μ‘°λ μμ λ°μ΄ν°μ `map λ©μλλ₯Ό νμ©ν΄ κ°κ²°νκ² νν` κ°λ₯<br>
    > UIλ₯Ό ν¨μ¨μ μΌλ‘, νμ₯μ± μκ² κ΅¬μ± κ°λ₯ `μ μ§λ³΄μκ° μ©μ΄`<br>
    > μ»΄ν¬λνΈ νμΌ λ΄λΆμμ μ μΈνκ±°λ, λ³λμ νμΌλ‘ λΆλ¦¬ν΄μ μ¬μ©<br>

    ```javascript
    //data.js
    const ASIDE_LIST = [
      { id: 1, text: "μκ°" },
      { id: 2, text: "λμλ§" },
      { id: 3, text: "νλ³΄ μΌν°" },
      { id: 4, text: "API" },
      { id: 5, text: "μ±μ© μ λ³΄" },
      { id: 6, text: "κ°μΈμ λ³΄μ²λ¦¬λ°©μΉ¨" },
      { id: 7, text: "μ½κ΄" },
      { id: 8, text: "μμΉ" },
      { id: 9, text: "μΈκΈ° κ³μ " },
      { id: 10, text: "ν΄μνκ·Έ" },
      { id: 11, text: "μΈμ΄" },
    ];
    export default ASIDE_LIST;
    ```

    ```javascript
    //Main.js
    import ASIDE_LIST from "./data";
    //...
    <ul className="aside_list">
      {ASIDE_LIST.map((el) => {
        return <li key={el.id}>{el.text}β’</li>;
      })}
    </ul>;
    //λ€μ λ±μ₯ν map
    //UIλ₯Ό κ·Έλ €μ£Όκ³  μΆμ κ³³μ μμ λ°μ΄ν°λ₯Ό λ£μ΄μ€λ€
    ```

8.  `Fetch`  
     - Fetch: νΉμ μ λ³΄κ° νμν  λ ν΄λΌμ΄μΈνΈλ μλ²μ HTTP ν΅μ μΌλ‘ μμ²­ λ¦¬νμ€νΈλ₯Ό λ³΄λ΄κ³  μ λ³΄ μλ΅μ λ°μ. - `λ°μ΄ν° μμ±,μμ ,μ­μ ` κ°λ₯

          ```javascript
          fetch(βAPIμ£Όμβ, {
          method:βpostβ,
          headers: ν΄λΉ ν΅μ μ λν λλ΅μ μΈ μ λ³΄(//λΆκ°μ μΈμ λ³΄/μ½μ²ΈμΈ μ νμ),
          body: μ€μ§μ μΈ λ°μ΄ν°
          //body: JSON
          // id, password
          })

          //λ³΄λΌ λ JSONμΌλ‘ λκ²¨μΌ ν¨
          //JavaScriptβ JsonμΌλ‘ λ³΄λΌ λ
          JSON.stringfy(id,password)
          ({userId:id, userPassword:password})
          ```

    <p align="center"> E.O.D 2022/11/11

<hr>
μΆμ²:

- https://attacomsian.com/blog/javascript-computed-property-names

- https://velog.io/@kwonh/ES6-%EB%8B%A8%EC%B6%95%EC%86%8D%EC%84%B1%EB%AA%85-%EA%B3%84%EC%82%B0%EB%90%9C%EC%86%8D%EC%84%B1%EB%AA%85-%EB%B9%84%EA%B5%AC%EC%A1%B0%ED%99%94%ED%95%A0%EB%8B%B9-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0

- https://blogpack.tistory.com/640

- https://bigtop.tistory.com/

- https://www.daleseo.com/js-window-fetch/
