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
