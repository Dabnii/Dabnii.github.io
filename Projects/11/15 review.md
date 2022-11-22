## <p align="center"> `39cm` 📆 11/15

- 기능 구현사항 `11/15`
  - 네비게이션을 온 클릭으로 보여주고 감추기
  - `useState`로 값을 관리하자
    - 혼동했던 부분: X좌표값을 이용하여 제작하려 함 → CSS 적 사고 😧
    - useState 값을 변경하는 방법이 헷갈렸음
      - 평소엔 map이나 string으로 값을 관리 했기 때문
      - `const [showSearch, setShowSearch] = useState("")`
- `Boolean`으로 값을 보여주고, 숨기는 방법

```jsx
const [showSearch, setShowSearch] = useState(false ✨);
//불리언 값으로 보여줌을 관리합니다

//...
onClick={() => setShowSearch(true)}
//이벤트를 넣어줄 함수에 작성합니다 (클릭을 하면 true)-> 즉 보여주기로 바꾼다

//...
{showSearch && (//그려낼 UI
)
}
// 만약 showSearch가 ture 하면 '&&' 조건에 성립하기에 UI를 그려낸다
```

<hr>

## <p align="center"> `39cm` 📆 11/16

### 📌 SCSS: hover & firstchild

```css
.navCategoriesWrap {
    display: flex;
    padding: 0.5rem 4rem;
    align-items: center;
    justify-content: space-between;
    font-weight: 800;

    .navCategories {
      display: flex;
    }

    ul {
      gap: 1rem;
      cursor: default;

      li {
        font-size: 1.5rem;
        border: none;
        border-bottom: 0.25rem solid transparent;

        &:first-child {
          &:hover {
            border-bottom: 0.25rem solid transparent;
          }
        }

        &:hover {
          border-bottom: 0.25rem solid black;
        }
      }
```

### 📌 `<Ul>` 을 떠나자마자 드롭다운 메뉴가 사라지는 이슈 해결

```jsx
//상위
<section
 className="navContent"
 onMouseEnter={() => setShowHoverMenu(false)}
// 위의 div에 접근하면 enter를 false로 값을 꺼주자!
>
...
<ul className="navCategories">
  <li>BEST</li>
  <li onMouseEnter={() => setShowHoverMenu(true)}>WOMEN</li>
  <li onMouseEnter={() => setShowHoverMenu(true)}>MEN</li>
  <li onMouseEnter={() => setShowHoverMenu(true)}>UNISEX</li>
</ul>
```

### 💡 굿포인트:

- `const [showHoverMenu, setShowHoverMenu] = useState(false);`
- `<li onMouseEnter={() => setShowHoverMenu(true)}>WOMEN</li>`
- 어제 배운 `usestate`를 활용하여 적용&활용 ✅

### 📌 섹션별 메뉴에 맞는 드롭다운 보여주기

```javascript
//Nav.js;
const [showHoverMenu, setShowHoverMenu] = useState(0);
//...
<ul className="navCategories">
  <li onMouseEnter={() => setShowHoverMenu(0)}>BEST</li>
  <li onMouseEnter={() => setShowHoverMenu(1)}>WOMEN</li>
  <li onMouseEnter={() => setShowHoverMenu(2)}>MEN</li>
  <li onMouseEnter={() => setShowHoverMenu(3)}>UNISEX</li>
</ul>;

//DownNav.js
import "./Nav.scss";
import "./Nav";

export default function DownNav(props) {
  return (
    <>
      <div className="hoverMenu" {...props}>
        <div className="hovRow1">
          <ul className="categories">
            <li className="subcategory01">여성 > </li>
            <li className="subcategory02">상의</li>
            <li className="subcategory03">하의</li>
            <li className="subcategory04">신발</li>
          </ul>
        </div>
      </div>
    </>
  );
}
```

- state를 숫자로 관리 하게 되자, 위의 적용 방식에 문제가 생겼음
- Props를 사용하여 부모 요소를 자식에게 전달
  - SCSS, Html 요소를 바꿔 고치는 방법이 필요함 🤔
- `멘토님 의견` :
  - `ul` , `li` 섹션에 넣어 구조변경
    - 코드를 줄일 수 있음
  - 상수 데이터로 제작하여 `map()`으로 사용하는 방법

---

## <p align="center"> `39cm` 📆 11/17

### 반복되는 UI 상수데이로 사용

```jsx
//DropDownData.json

[
  {
    id: 1,
    category: "여성 >",
    top: "상의",
    bottom: "하의",
    shoes: "신발",
  },
  {
    id: 2,
    category: "남성 >",
    top: "상의",
    bottom: "하의",
    shoes: "신발",
  },
  {
    id: 3,
    category: "공용 >",
    top: "상의",
    bottom: "하의",
    shoes: "신발",
  },
];
```

```jsx
//DropDown.js

import React from "react";

const DropDown = ({ obj, mouseLeave }) => {
  return (
    <>
      <div onMouseLeave={mouseLeave} className="dropDown">
        <div className="dropDownRow">
          <ul className="dropDownCategories">
            <li className="category">{obj.category} </li>
            <li className="top">{obj.top}</li>
            <li className="bottom">{obj.bottom}</li>
            <li className="shoes">{obj.shoes}</li>
          </ul>
        </div>
      </div>
    </>
  );
};

export default DropDown;
```

```jsx
//DropDown.js

<ul className="navCategories">
  <li onMouseEnter={() => setShowHoverMenu(0)}>BEST</li>
  <li onMouseEnter={() => setShowHoverMenu(1)}>WOMEN</li>
  <li onMouseEnter={() => setShowHoverMenu(2)}>MEN</li>
  <li onMouseEnter={() => setShowHoverMenu(3)}>UNISEX</li>
</ul>;

//
{
  dropDownData.map((obj, index) => {
    if (obj.id === showHoverMenu) {
      return <DropDown obj={obj} key={index} />;
    }
  });
}

////DropDownData.json → obj임
```

```jsx
{dropDownData.map((obj, index) => {
          if (obj.id === showHoverMenu) {
            return (
              <DropDown
                obj={obj}
                key={index}
                mouseLeave={() => setShowHoverMenu(0)}
              />
            );
          }
```

### 🌳 성장포인트 :

- `useState`를 자유자재로 사용하고 있다
- `map()`을 사용한 조건부 렌더링을 다시 복습!

---

## <p align="center"> `39cm` 📆 11/18

### 📝 Daily Sprint meet up!

- 프로젝트가 시작 된 익일 화요일 부터 매일 데일리 스프린트를 진행하고 있다.
- 노션에 회의록 & task를 정리하여 간단하게 15분 내외로 진행하고 있다.
  - 기록하고 문서화를 좋아하는 나에게 너무 즐거운 시간 ✨
  - 팀원들의 태스크를 확인하고 적극적으로 질문 할 수 있고 이해할 수 있어 불필요한 소통이 줄었다
    - 작업하다가 다른 팀원에게 단발&불시로 질문하는것이 미안했는데 효율적이라 좋다.
    - 회의록을 읽어보면 놓쳤던 & 헷갈리던 부분도 체크 가능 🫡
- 📝 멘토님의 오늘 스프린트 밋업 피드백

  - 👏 Good
    - 회의록을 남기고 있고, 필요한 부분들을 현업과 비슷하게 진행하고 있는 것
    - Blocking 컨트롤이 좋다
    - Trello에서 백&프론트 통합적으로 관리가 잘 되고 있음!
      - 세부 task를 입력해도 좋겠다
  - 💪 Try it!
    - 아쉬운 점은, 나 혼자 서기를 하고 있다는 점인데 이 부분은 밋업 직전 슬랙 리마인드를 보내 팀원들 선 작성을 요청 할 예정!
  - 회의록 자랑 👇
    ![img](https://user-images.githubusercontent.com/110847597/202833938-368cc3fb-9907-459f-a5dd-21a1cfa70300.png)

---

### 💻 코드 들여다보기

- closeBtn을 누르면 뜨는 `0` 이슈 해결
- `Fetch` 사용 & 학습
- `Token` 유무를 사용한 로그인/로그아웃 버튼 상태 변환

```javascript
{
  NavIconList.map((el) => {
    if (el.id !== 3) {
      return (
        <div key={el.id}>
          <Link className="unsetLink" to={el.url}>
            <img src={el.img} alt="icon-img" />
            <span>{el.text}</span>
          </Link>
        </div>
      );
    }
  });
}
{
  localStorage.getItem("TOKEN") && (
    <div>
      <Link
        className="unsetLink"
        to={"/Login"}
        onClick={() => localStorage.removeItem("TOKEN")}
      >
        <img src="/images/leedabin/logout.png" alt="icon-img" />
        <span>LOGOUT</span>
      </Link>
    </div>
  );
}
{
  !localStorage.getItem("TOKEN") && (
    <div>
      <Link className="unsetLink" to={"/login"}>
        <img src="/images/leedabin/login.png" alt="icon-img" />
        <span>LOGIN</span>
      </Link>
    </div>
  );
}
```

1. `Token` BackEnd 에서 토큰을 받지 못하여 임시로 개발자 도구로 생성

- 🧩 드디어 맞춰진 퍼즐!
- 1주차에 학습한 `개발자도구`중 내가 발표&정리한 어플리케이션 패널을 적극 활용하는 타임
- 📎 <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Computer%20Science/DevTools%20%7C%20Chrome.md#-%EC%96%B4%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98-%ED%8C%A8%EB%84%90">DevTools | Chrome by. me</a>

  - 🗄 로컬 스토리지에 특정데이터를 저장하고 저장한 데이터를 접근해서가져오는 방법

  - `✍️ 세팅하는 법`

    1. localStorage.setItem("key", "value")
    2. sessionStorage.setItem("key", "value")setcookie("key","value","지속시간")

    `🔍 스토리지 접근해서 값 가져오는 법`

    1. localStorage.getItem("key")
    2. sessionStorage.getItem("key")document.cookie

    `✂️ 스토리지 접근해서 값 지우기`

    1. localStorage.removeItem(key)

  - console패널에서

    1.  `localStorage.setItem("TOKEN", "Pw")` 를 임시로 생성
    2.  `localStorage.getItem("TOKEN")` 으로 토큰 생성 확인
    3.  작업중인 사이트에서 로그인성공 여부 확인 → `Logout` 버튼으로 바뀌었다면 성공
    4.  `Logout` 버튼을 눌러 로그아웃을 확인 & 토근 삭제 확인 👏
    5.  위의 코드에서 작동 로직을 확인 할 수 있다
        - 아쉬운 점은.. 굳이 `map()`로 돌리지 않아도 됐을거라는 추측
        - 코드가 길다고 나쁜건 아닌데 비효율적으로 판단

### ⚒️ 이슈 수정

- closeBtn을 누르면 `0`이 등장함

```javascript
<img
  alt="closeBtn"
  className="searchCloseBtn"
  src="/images/leedabin/closeBtn.png"
  onClick={() => setShowSearch(false)}
/>
```

- 해결 방법:
  - 원인: ` onClick={() => setShowSearch(0)}`를 적으면 0이 UI에 그려진다 😧
  - `0`을 기입한 이유는 `false` 사이드 서치바를 사라지게 하는 목적이었기 때문에 `false`로 수정하면 된다!

### 🌳 성장포인트 :

- 조각조각 단편적으로 공부했던 부분들이 하나의 큰 퍼즐이 되어가는 즐거움
- `state` 작성과 원리를 학습
- `조건부 렌더링` `&&` 학습
- 고민 보다 코드를 써보는 시간을 늘려보자
- `MockData`, `fetch`의 적절한 사용 예시를 학습

---

## <p align="center"> `39cm` 📆 11/20

### Product detail page

```javascript
const hendleScrollUp = (e) => {
  if (!window.scrollY) return;

  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
};

const handleScrollDown = (e) => {
  if (window.scrollY) return;

  window.scrollTo({
    top: document.documentElement.scrollHeight,
    behavior: "smooth",
  });
};
```

- 개발자 사고 필요:
  - 처음 ScrollDown 기능을 구현 할 때, `Bottom`도 넣어보고 `top` 4000 넣어봤다.(미작동)
  - `Bottom` 인자를 인식 하지 않는다.
  - `top` 4000은 인식하지만 개발자가 지향해야할 방식은 아니라 구글링으로 ` top: document.documentElement.scrollHeight,` 코드를 착안하게 됨.
    - <a href="https://stackabuse.com/how-to-scroll-to-top-in-react-with-a-button-component">📎참고 사이트</a>

---

## <p align="center"> `39cm` 📆 11/22

```jsx
useEffect(() => {
  fetch("/data/product.json", {
    method: "GET",
  })
    .then((response) => response.json())
    .then((data) => setPdData(data));
}, []);
```

- moct 데이터를 불러 올 때 경로를 확인 필수
- Get은 단독 일 때 생략가능

```jsx
const token = localStorage.getItem("TOKEN");
//이렇게 할당하여 부르는 것이 유지보수에 도움이 됩니다
//어제의 피드백 반영완료

<img
    className="heartLineIcon"
    alt="heart"
    onClick={() => {
      setLikePd((prev) => !prev);
    }}
    src={
      likePd === false
        ? "/images/leedabin/heartLine.png"
        : "/images/leedabin/heartOrange.png"
    }
  />
) : (
  <img
    className="heartLineIcon"
    alt="heart"
    src="/images/leedabin/heartLine.png"
    onClick={() => alert("로그인이 필요한 서비스 입니다!")}
  />
)}
```

### Mock data

```jsx
const [pdData, setPdData] = useState([]);

{pdData[0]?.price}
pdData의 '0' 번째 배열에서 price를 가져옵니다.

?.
//옵셔널 체이닝
```

```jsx
//prodectDetail.js
import { Link, useParams } from "react-router-dom";

//prodectDetail.js
useEffect(() => {
  fetch(`https://reqres.in/api/users/${userId}`, {
    method: "GET",
  })
    //  fetch(/2nd/fetch/), 이렇게 연결해서 작성 가능
    .then((response) => response.json())
    .then((data) => setPdData(data));
}, []);

//router
<Route path="/ProductDetail/:productId" element={<ProductDetail />} />;
```

- `:`뒤로 사용자가 정의할 수 있다.

### 📌 세자리 마다 콤마 붙여주기 000,000

```jsx
{
  (pdData[0]?.price * amount).toLocaleString();
}

{
  (pdData[0]?.price).toLocaleString();
}
```

- 위의 코드가 오류가 생긴다면 감싸고 있는 div나 가까운 상위에 가서 `{pdData &&}` 조건부 렌더링 해주기

```jsx
const [amount, setAmount] = useState(0);

const onIncrease = () => {
  setNumber((prevNum) => prevNum + 1);
  setAmount(amount + 1);
};

const onDecrease = () => {
  if (number <= 0) {
    setNumber(0);
  } else {
    setNumber((prevNum) => prevNum - 1);
    setAmount(amount - 1);
  }
};
```

- 음수까지 진행되던 연산 이슈 해결
  - ✨ `if (number <= 0) {setNumber(0)}`

---
