# <p align="center"> π WESTAGRAM clone project

<p align="center"> 2022.Oct. 24th ~

## π westagram | Vanila JS

1. `Login page`

   - HTML
   - CSS
   - Java script

2. `Feed page`

   - HTML
   - CSS
   - Java script

<hr>

## 1οΈβ£ Log-in page

- HTML | κ°λμ± λμ΄κΈ° π

  - π· `semantic tag`
  - μ μ§λ³΄μκ° μ¬μ΄ `νκ·Έμ΄λ¦ μ§κΈ°`

- CSS | κ°λμ± λμ΄κΈ° π

  - CSS μ»¨λ²€μ μ¬μ©
  - `λ€μ¬μ°κΈ°`λ₯Ό μ¬μ©
  - Layout-properties β Box-prop β visual prop β Typo-prop β Misc prop μ
  - μ νμλ€ μ¬μ΄ `<br>` ν μ€ λμ°κΈ°

  - CSS λ μ΄μμ
    - `display: flex` μ¬μ©μΌλ‘ μΆν λ°μνμ μ ν©νλλ‘ μ μ
    - `rem` λ¨μλ₯Ό μ¬μ©νμ¬ λ°μνμ μ μ

- JavaScript
  - π `Event` μ¬μ©
  - `addEventListner`λμκ³Ό μλ¦¬ μ΄ν΄
  - `μλ§μ νκ·Έλͺ` μ¬μ©
    - e.g. `thisIsPassword`, `thisIsLoginBtn`

<hr>

## HTML | 2022.Oct.24

```HTML
  <body>
    <section class="login-page">
      <div class="login-container">
        <h1 class="instagram-logo">westagram</h1>
        <div class="login-box">
          <input
            type="text"
            id="id-input"
            placeholder="μ νλ²νΈ, μ¬μ©μ μ΄λ¦ λλ μ΄λ©μΌ"
          />
          <input type="password" id="password-input" placeholder="λΉλ°λ²νΈ" />
          <button disabled class="button_beforeType login-btn">λ‘κ·ΈμΈνκΈ°</button>
          <h3 class="login-failure_help">λΉλ°λ²νΈλ₯Ό μμΌμ¨λμ?</h3>
        </div>
      </div>
    </section>
    <script src="app.js"></script>


```

## CSS

```CSS
* {
  box-sizing: border-box;
}
body {
  display: flex;
  width: 100vw;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  flex-wrap: nowrap;
  text-align: center;
  background-color: #fafafa;
}

h1 {
  font-family: "Lobster", cursive;
  font-size: 3rem;
  margin-top: 0;
  margin-bottom: 4rem;
  font-weight: 200;
}

h3 {
  font-family: "Noto Sans KR", sans-serif;
  font-size: 0.8rem;
  font-weight: 500;
  color: #003668;
  margin-top: 3rem;
}

.login-container {
  margin-top: 3rem;
  border: 0.5px solid #e6e6e6;
  background-color: white;
  padding: 3rem 2.5rem 1rem 2.5rem;
}

input {
  outline: none;
  appearance: unset;
  justify-items: center;
  width: 15rem;
  border: 1px solid #efefef;
  border-radius: 0.1rem;
  background-color: #fafafa;
  padding: 0.5rem;
}

input #text {
  color: #999999;
  font-size: small;
}

.login-box {
  display: flex;
  flex-wrap: nowrap;
  flex-direction: column;
  gap: 1rem;
}

.button_beforeType {
  appearance: unset;
  border: none;
  border-radius: 0.3rem;
  background-color: #2962ff;
  padding: 0.5rem;
  color: white;
  opacity: 30%;
}

.active {
  appearance: unset;
  border: none;
  border-radius: 0.3rem;
  background-color: #2962ff;
  padding: 0.5rem;
  color: white;
  opacity: 100%;
}

```

## β¨ JavaScript

### JavaScript νμκ΅¬ν ν­λͺ©

- id, pw μ κ°κ° ν κΈμ μ΄μ μ¨μΌ λ²νΌμ΄ νμ±ν λλλ‘ ν΄μ£ΌμΈμ.<br>
  μλ μ°ν νλμμ΄μλ€κ° -> νμ±ν λλ©΄ νλμμΌλ‘!π΅

> ## π€pseudocode
>
> β μΌν­ μ°μ°μ μ¬μ© <br> `condition ? exprIfTrue : exprIfFalse`<br>
> μ΄λ©μΌκ³Ό λΉλ°λ²νΈ λ μ€ νλ μλ ₯μ΄ λλ€λ©΄ λ²νΌμ΄ νμ±ν λλλ‘ νκΈ° <br>
> If true : λ μ€ νλλΌλ μλ ₯ λμμ λ<br>
> If false : λ μ€ νλλΌλ μλ ₯ λμ§ μμμ λ<br>
> OR IDκ° 1κ°λΌλ μλ ₯ λμκ±°λ || PWκ° 1κ°λΌλ μλ ₯ λμλ€λ©΄ Btn on <br>
> λ§μ½ λ μ€ νλλΌκ³  μλ ₯μ΄ λμλ€λ©΄ ? λ²νΌ μ¨ : μλλΌλ©΄ λ²νΌ μ€ν λ°μ΄ <br>
> λ°μ€ login-box <br>
> λ‘κ·ΈμΈ μμ΄λ #id-input<br>
> λΉλ°λ²νΈ μμ΄λ #password-input<br>
> λ‘κ·ΈμΈ λ²νΌ ν΄λμ€ .login-btn<br>

```javascript
//3μ°¨ - λ©ν λ μ½μΉ­
const thisIsId = document.querySelector("#id-input");
const thisIsPassword = document.querySelector("#password-input");
const thisIsLoginBtn = document.querySelector(".login-btn");

function activeButton() {
  thisIsLoginBtn.classList.remove("button_a");
  thisIsLoginBtn.classList.add("active");
  thisIsLoginBtn.disabled = false;
}
function inactiveButton() {
  thisIsLoginBtn.classList.remove("active");
  thisIsLoginBtn.classList.add("button_a");
  thisIsLoginBtn.disabled = true;
}

function handleClick(event) {
  const inputID = document.querySelector("#id-input").value;
  const inputPW = document.querySelector("#password-input").value;
  console.log(inputID, inputPW);

  const isValid = inputID.length >= 1 && inputPW.length >= 8;

  isValid ? activeButton() : inactiveButton();
}

thisIsId.addEventListener("keyup", handleClick);
```

π ν΅μ¬ ν¬μΈνΈ

- `thisIsLoginBtn`.disabled = false; λ²νΌμ΄ μ λλ‘ νμ±ν λμ§ μμλ μ΄μ 
  - νκ²μ μ§μ ν΄ μ£Όμ§ μμμ
- `μΌν­μ°μ°μ` μ¬μ©μ μν ν¨μ μμ±
  - ` isValid ? activeButton() : inactiveButton();`
  - π¬ κ³Όμ  μΆμ  μλ νμλ νμνλ€

## π μ½λ λ€μ¬λ€λ³΄κΈ°

- `href`

  - λ€λ‘ κ°κΈ° κ°λ₯

- `replace`

  - λ€λ‘ κ°κΈ° λΆκ°
  - λ³΄μμ΄λ κΈ°νμλμ λ°λΌ μ΄μ νμ΄μ§ μ κ·Όμ λ§μ μ μμ

- `addEventListner`

  - μ¬λ¬ μ΄λ²€νΈ λ¦¬μ€λλ€μ ν¨μλ‘ μ μ΄ν  μ μμ

  ```javascript
  function init() {
    // μ΄λ²€νΈλ₯Ό μ½λ μ½λλ€μ μ§ν©
    //eventlistner...
  }
  init();
  ```

```javascript
//2μ°¨ μμ±μ½λ 2022.Oct.27
const thisIsId = document.querySelector("#id-input");
const thisIsPassword = document.querySelector("#password-input");
const thisIsLoginBtn = document.querySelector(".login-btn");

function handleClick(event) {
  const inputID = document.querySelector("#id-input").value;
  const inputPW = document.querySelector("#password-input").value;

  if (inputID.length >= 1 && inputPW.length >= 8) {
    //μλμ νμ§λ§ μμ΄λμ κΈΈμ΄κ° 1μ΄μμ΄ μλ 3μμ, ν¨μ€μλλ 8μ΄μμμ λ²νΌμ΄ νμ±ν λλ€.
    // μΈλ±μ€κ° [0] μΌλ‘ μμνκΈ° λλ¬Έμ΄λΌκ³  μ μΆνλ€.
    // 28μΌ λ©ν λμ κ·μ°?κ² ν  μμ .. :)
    thisIsLoginBtn.classList.remove("button_beforeType");
    thisIsLoginBtn.classList.add("active");
    disabled = false;
  } else {
    thisIsLoginBtn.classList.remove("active");
    thisIsLoginBtn.classList.add("button_beforeType");
    disabled = true;
  }
}

thisIsId.addEventListener("keyup", handleClick);
```

```Javascript
//2μ°¨ μμ±μ½λ 2022.Oct.26
const thisIsId = document.querySelector("#id-input");
const thisIsPassword = document.querySelector("#password-input");
const thisIsLoginBtn = document.querySelector(".login-btn");

thisIsLoginBtn.addEventListener("click", () => {
  const inputID = document.querySelector("#id-input").value;
  const inputPW = document.querySelector("#password-input").value;

  if (inputID.length > 1 && inputPW.length > 1) {
    console.log("hi");
  }

if (inputID.length >= 1 && inputPW.length >= 1) {
  document.getElementsByClassName("login-btn").disabled = false;
  //disable defaultκ°μ true λΉνμ±νμΈμν.
  //disableμ μκ°μ μΌλ‘λ λ³΄μ΄λ μ΄λ²€νΈλ¦¬μ€λκ° μλνμ§ μλ 'λ¬΄'μ μνμ κ°κΉλ€.
  //κ³ λ‘ μμ μ½λλ μμ μ΄ νμ
}
});

thisIsId.addEventListener("keyup", handleClick);
```

```HTML
<button disabled class="button_beforeType login-btn" disabled>λ‘κ·ΈμΈνκΈ°</button>
```

`disabled` μ±νν μ΄μ :

- `disabled`μ μ¬μ©νμ¬ HTML νκ·Έ μ¬μ©λ²μ νμ΅ νκ³ μ νμλ€.
- JavaScriptμμ `λμ  μμ`μ `disabled`μ νμ₯μ±μ νμ΅νμλ€.

<hr>

## 2οΈβ£ Feed-in page

- HTML | κ°λμ± λμ΄κΈ° π

  - π· `semantic tag`
  - μ§κ΄μ μΈ `νκ·Έμ΄λ¦ μ§κΈ°`

- CSS | κ°λμ± λμ΄κΈ° π

  - CSS μ»¨λ²€μ μ¬μ©
  - `λ€μ¬μ°κΈ°`λ₯Ό μ¬μ©
  - Layout-properties β Box-prop β visual prop β Typo-prop β Misc prop μ
  - μ νμλ€ μ¬μ΄ `<br>` ν μ€ λμ°κΈ°

- JavaScript

  - π `Event` μ¬μ©
  - `appendChild`λμκ³Ό μλ¦¬ μ΄ν΄
  - `innerHTML`λμκ³Ό μλ¦¬ μ΄ν΄
  - `μλ§μ νκ·Έλͺ` μ¬μ©

### Javascript

```javascript
//νμ κ΅¬ν ν­λͺ© : λκΈ μΆκ°
const commentInput = document.querySelector(".main__feed_comments_input");
const commentForm = document.querySelector(".main__feed_comments_form");
const commentBtn = document.querySelector(".main__feed_comments_enter");
const commentArea = document.querySelector(".comment_area");
const addComment = document.getElementsByClassName("letAddNewComment");
let commentValue = "";
//κ°μ΄ μλ€λ‘ μμνκΈ° μν¨

commentInput.addEventListener("keyup", function () {
  commentValue = commentInput.value;
  if (commentValue.length > 0) {
    commentBtn.disabled = false;
    commentBtn.style.cursor = "pointer";
    commentBtn.style.color = "#488bff";
  } else {
    commentBtn.disabled = true;
    commentBtn.style.cursor = "default";
    commentBtn.style.color = "#488bff";
  }
});

commentForm.addEventListener("submit", (event) => {
  event.preventDefault();
  const newCommentCtx = commentInput.value;
  const newComment = document.createElement("li");
  newComment.innerHTML = `<li> <span><b>0713.jpg</b></span>   ${newCommentCtx} </li>`;
  addComment[0].appendChild(newComment);
});
```

## π μ½λ λ€μ¬λ€λ³΄κΈ°

1. `κ²μ` λ²νΌμ λλ¬ λκΈ μλ ₯

- form λΆλͺ¨ νκ·Έμ input & button μμ μ€μ 
- π€ Submitμ΄ λμ§ μλ μ΄μ:
  - from νκ·Έμ μ΄λ²€νΈ λ¦¬μ€λλ₯Ό μ§μ νμ§ μμκΈ° λλ¬Έ
  - `eventPrevent` μ­μ μλνμ§ μμμ

2. μμ±λ λκΈμ νλ©΄μ λμ°κΈ°

   - `<ul><li></li></ul>`

   - ulμμ appendChild: - `newComment.innerHTML = <li> ${newCommentCtx} </li>`

   - `<li>`μ μλ‘μ΄ λκΈ λ΄μ©μ μλ ₯ν©λλ€

3. λκΈμ νλ©΄μ λμ°κΈ°

   - `document.appendCHild`μλλ° κ·Έ λ»μ μ μ²΄ νλ©΄μ λ?μ΄ μμ΄λ€ λΌλ μλ―Έ

     - π‘ `addCommnetμ 0λ² μΈλ±μ€`μμ κ°μ Έμ€λλ‘ μμ 

   - `getElementbyclassname`μμ β λ°°μ΄λ‘
   - `const addComment = document.getElementsByClassName("letAddNewComment")`
   - ulμ΄ μ€λ³΅ μ¬μ©λμκΈ° λλ¬Έμ ν΄λμ€λ€μμ ν λΉ

<hr>

### π³ μ±μ₯ ν¬μΈνΈ

- `μλ§¨ν± νκ·Έ` μ¬μ©μ ν΅νμ¬ μ¬λκ³Ό μ»΄ν¨ν°μκ² μλ―Έλ₯Ό μ λ¬νλ HTML μμ±
- κ°λμ±μ λμΈ `λ€μ¬μ°κΈ°`, `CSS μ»¨λ²€μ`μ κ·μΉμ μ μ©νμ¬ μΆν `μ μ§λ³΄μμ μ©μ΄`νλλ‘ ν¨
- κ° HTML, CSS, JavaScriptμ μ­ν μ μ΄ν΄νμμΌλ©°, JavaScriptμμ methodν΅νμ¬ κ°μ λ³κ²½νλ νμ₯μ±μ μ€μ 
- JavaScriptμ κ½, `Event`,`addEventListner`λμκ³Ό μλ¦¬λ₯Ό μ΄ν΄
- μΌν­μ°μ°μλ₯Ό μ¬μ©ν κ°λμ±μ΄ μ’μ μ½λ μμ±
- `μλνλ μ½λκ° μλ λ λμ μ½λ` πͺ
  - `semantic tag` & `μΌν­μ°μ°μ` & `tag convention`
- μλ°μ€ν¬λ¦½νΈμ κΈ°λ³Έ λ¬Έλ²λ€μ μμ©νλ κ³Όμ μ΄ ν₯λ―Έλ‘­λ€.
  - λ³΅κΈ°μ μμ©μ΄ λ°°μμ μλλ ₯μ΄ λλ€!
  - μλκ³Ό μ±κ³΅ λν νλ₯­ν μλλ ₯
- λμ λ³΄ν­μ λ§λ μλλ‘ μ°¨κ·Όν μκ°νκ³  μ½λ μμ±μ΄ λμμ΄ λμλ€.
- <i> I never lose, Either I win or lean.</i>
