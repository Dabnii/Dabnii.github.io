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

- mock 데이터를 불러 올 때 경로 확인 필수
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

- 위의 코드가 오류가 생긴다면 감싸고 있는 div나 직계부모에 가서 `{pdData &&}` 조건부 렌더링 해주기

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

## <p align="center"> `39cm` 📆 11/23

### 📌 JSON 이슈

```jsx
const [pdData, setPdData] = useState([]);

{pdData[0]?.price}
pdData의 '0' 번째 배열에서 price를 가져옵니다.

?.
//옵셔널 체이닝
//2022.11.22 작성한 코드
```

- 💭 `fetch`로 목데이터를 들고와서 읽는 순간 오류가 발생

  ```JSON
  {
    "productName": " 숏다운 (3color)",
    "description": "포근하고 헤어리한 터치감의 우먼스 집업 가디건, YKK 투웨이 지퍼 사용",
    "price": 297000,
    "category": "상의",
    "likesNumber": "likesNumber",
    "images": [
      ".../.../png"
      ".../.../png"
      ".../.../png"
    ],
    "reviews": [
      {
        "reviewTitle": "제목",
        "reviewContent": "첫번째 리뷰의 내용입니다.",
        "reviewImage": "./.../jpg",
        "rating": "rating",
        "reviewUser": "@1234KIM"
      }
    ]
  }
  ```

- 📌 객체로 된 데이터라 때문에 조건부 실행을 원한다면 아래의 코드로 적어야한다.
  ```jsx
  {pdData[0] !== null && ()}
  ```
  - 배열은 `true`/`false` 값으로 들어온다
  - 객체는 `undefined`로 들어온다
  - `{pdData[0] && }`로 사용하면 오류가 발생한다.
  - 어떠한 객체를 받아오는지, 동기적 언어의 특성을 파악하지 못하연 초보적인 실수가 반복된다.
    - 시간을 효율적으로 쓰지 못하는 치명적인 단점

### 📌 `fetch`

- `fetch`는 `const` 함수 안에서도 쓸 수 있고, `useEffect` 컴포넌트가 렌더링 될 때 실행하도록 설정 할 수 있다.
  - 📌 컴퓨터 적으로 사고하기
  - 마운트, 언마운트 시점, 그리고 업데이트 될 때 세 가지 정도 생각해보면 좋겠다.
    - 장바구니, 결제 같은 경우는 특정한 이벤트가 있을 때 발생하면 좋겠다 → `onClickEvent`
    - 상품 리스트, 상품 정보는 첫 마운트 될 때 필요하다 → `useEffect`
    - 위의 개념이 어려웠으나, 이번 프로젝트 때 반복 학습 중

### 📌 `map()`

```jsx
{
  pdData.images?.map((image, i) => (
    <img src={image} alt="thumbnail" className="detailsInfo" />
  ));
}
```

### 🎠 carousel

```jsx
//detailProduct.js
const [current, setCurrent] = useState(0);
const [style, setStyle] = useState({ marginLeft: `-${current}00%` });

const imgSize = useRef(images.current.length);

//const images = useRef([]);
//위의 코드를 지우면 모래성 같은 내 코드들이 무너진다..

useEffect(() => {
  setStyle({ marginLeft: `-${current}00%` });
}, [current]);

const moveSlide = (i) => {
  let nextIndex = current + i;

  if (nextIndex < 0) nextIndex = imgSize.current - 1;
  else if (nextIndex >= imgSize.current) nextIndex = 0;

  setCurrent(nextIndex);
};

//캐러셀에 들어갈 이미지 맵하기
<div className="flexBox" style={style}>
  {pdData.images?.map((image, i) => (
    <img src={image} alt="thumbnail" />
  ))}
</div>;
```

- 맵을 이용한 이미지 가로 정렬
- 이미지의 current 값을 사용한 margin 이동 👏

### 🌳 성장 포인트:

- `객체조건부 실행` 근본적인 오류를 잡기 위하여 시간을 많이 쓴 시간이었다.
- `map()` 을 사용한 반복되는 UI 구현
- `fetch` 사용법
- 어제보다 나은 오늘의 나 💪

---

## <p align="center"> `39cm` 📆 11/24

### 📌 `useParams`

```jsx
const params = useParams();
const productId = params.productId;
```

> 상세페이지 작업

- 동적 라우팅을 위하여 `useParams()`를 사용하였다.
  - 기존에는 `/Main` 링크를 썼다.
  - 위의 경우로 진행하면 상품이 1,000개일때 마다 라우트를 해줄 수 없다!

```jsx
<Route path="/ProductDetail/:productId" element={<ProductDetail />} />
```

- `:productId`

- 컨벤션을 productId로 정한 이유:
  - 이미 뚜렷한 컨벤션이 있고, 룰이 있다면 좀 더 짧은 이름으로 대체 하면 좋겠지만 그렇지 않기에 다른 팀원이 `사전 지식 없이 열어서 읽어도 쉽게 읽기 위함`

### 📌 데이터 통신:

- `useEffect` & `fetch`
- 어제와 같이 객체 데이터를 state에 저장하고 사용할 때가 조금 헷갈린다.

  ```jsx
  //productdetail.js
  const addCart = () => {
    fetch("http://127.0.0.1:3000/cart", {
      method: "POST",
      headers: {
        authorization: localStorage.getItem("TOKEN"),
        "Content-Type": "application/json;charset=utf-8",
      },
      body: JSON.stringify({
        productId: productId,
        //Backend의 데이터 명세를 참조하여 작성합니다.
        amount: amount,
      }),
    })
      .then((response) => {
        if (response.status !== 200) {
          //Backend의 데이터 명세를 참조하여 작성합니다.
          throw new Error("에러 발생!");
        } else {
          navigator("/Cart");
        }
      })
      .catch((error) => alert("장바구니 추가에 실패하였습니다."));
  };
  ```

  - 왜 위의 코드는 `useEffect`로 쓰지 않았을까?
  - 📌 `호출시점`
  - useEffect는 렌더링이 끝난후 어떠한 작동을 목적
  - 즉, `결제 버튼을 누를 때 마다 fetch를 진행`해야 한다.
    - 결제는 렌더링이 끝난다고 진행되는것이 아니다.
  - `fetch` + `useEffect`는 쌍이라고 생각하던 사고를 깨주는 코드였다.
  - 간략하게 `useEffect`를 정리하자면...
    1. 의존성 배열이 전달되지 않았다면 매 렌더링마다 콜백 함수를 호출한다.
    2. 의존성 배열이 전달되었다면 의존성 배열의 값을 검사한다.
    - a. 의존성 배열에 있는 값 중 `하나라도 이전 렌더링과 비교했을 때 달라졌다면` 콜백 함수를 호출한다.
    - b. 의존성 배열에 있는 값이 `이전 렌더링과 비교했을 때 모두 다 같다면` 콜백 함수를 호출하지 않는다.
  - 선언한 `addCart` 함수를 `onClick` 이벤트에 넣어 클릭시 작동하도록 합니다.👇

  ```jsx
  <button className="addCartBtn" type="button" onClick={addCart}>
  ```

- `fetch` + `useEffect`

  ```jsx
  useEffect(() => {
    //통신용입니다
    // fetch(`https://reqres.in/api/users/${productId}`)
    fetch("/data/product.json")
      .then((response) => response.json())
      .then((data) => setPdData(data));
  }, []);
  ```

  - 의존성 배열을 넣어 최초 마운트 시 데이터를 가져 오도록 했습니다.
  - 또한 마찬가지로, 백엔드의 데이터 명세를 따릅니다.
  - `${productId}`는 최상단에 선언한 `const params = useParams()`, `const productId = params.productId` usePrams 입니다.
  - 위의 데이터는 상품에 대한 정보이기 때문에 마운트가 될 때 필요합니다.

  ```jsx
  //productdetail.js
  useEffect(() => {
    const ipAddress = "%ip%";

    //통신용입니다
    fetch(`http://${ipAddress}:3000/products/${productId}`, {
      headers: {
        productId: productId,
      },
    })
      // fetch("/data/product.json")
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        setPdData(data.product[0]);
      });

    fetch(`http://${ipAddress}:3000/likes/product/${productId}`, {
      headers: {
        authorization: localStorage.getItem("TOKEN"),
      },
    })
      .then((response) => response.json())
      .then((result) => {
        console.log(result.isLiked);
        setLikePd(result.isLiked);
      });
  }, [productId]);
  ```

  ```jsx
  const setPaymentItem = () => {
    if (localStorage.getItem("TOKEN")) {
      localStorage.setItem(
        "orderList",
        JSON.stringify({
          productId: productId,
          productName: pdData.productName,
          productPrice: pdData.price,
          images: pdData.images,
          brandName: pdData.brandName,
          amount: amount,
        })
      );
      navigator("/Payment");
    } else alert("로그인이 필요한 서비스 입니다.");
  };
  ```

  - `JSON.stringify()`는 자바스크립트의 값을 JSON 문자열로 변환한다.

### 📝 회고:

- 👍 잘한 점

  - 개발자의 소통방식을 배웠다
    - 단순히 일정을 체크하고 작업진행률을 묻는 것이 아닌 어떠한 기능을 구현하기 위하여 각자가 어떤 리소스와 역량, 한계를 가지고 있는지 나눠보는 것이었다.
    - 물론 일정 소통과 블락커 해소도 중요한 부분 중 하나이다.
    - 👍 개발 일지 (Notion)와 트렐로를 사용하여 일정과 회의를 문서화 하여 서로 헤매는 부분이 적었다.

- 💪 아쉬운 점

  - 기획에서 서비스의 차별점을 구현 하지 못한게 아쉽다

    - 마케팅 측면 에서 `리뷰`의 힘이 강력한데, 위 사이트는 상품에 리뷰를 게시글 목록 형태로 보여준다.
    - 인스타그램 피드처럼 상품의 착용사진이나, 네이티브한 사진을 보여주지 않는 점이 아쉬웠다.
    - 그래서 `리뷰 기능을 개선하여 매출 증대로 연계하고 싶었다.`
    - 막상 진행하려고 하니 단순히 리뷰를 UI를 개선하는 것 보다 등록, 수정, 삭제 기능을 추가해야했다.
    - 사전에 더 꼼꼼히 고려했다면 프론트&백엔드 팀과 싱크가 맞아 진행했을 수도 있다고 생각한다.
    - 위의 과정을 결과로 다음 프로젝트에서는 우선순위와 기능에 대하여 논의를 할 것이다.

  - 컴포넌트 분리 및 가독성 좋은 코드를 쓰지 못한 점
    - 개선 방법: 초석을 잘 다지는 것 처럼, 작업시에 컴포넌트를 계획하고 분리 습관을 만들 예정
    - 한 줄을 쓰더라도 가독성과 간결함에 집중 할 것이다.
  - 다시 한 번, 아는 만큼 쓸 수 있는 코드.
  - 주말 동안 부족했던 부분을 더 공부 하고 다음 프로젝트에 임할 예정!
  - 39cm팀 고생 많았습니다!

  ***

  <p align="center">E.O.D
