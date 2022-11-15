## <p align="center"> `39cm`📆 11/15

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
