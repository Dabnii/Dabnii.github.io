## <p align="center"> `CGW` 📆 11/29

- `Stypled component` <a href="https://styled-components.com/">📎 공식문서</a>

### 💅 Styled-Components

- <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.12/Dec1stWeek.md#-styled-components-%EC%95%BD-%EC%9D%BC%EC%A3%BC%EC%9D%BC-%ED%9B%84%EA%B8%B0">💅 `Styled-Components`일주일 사용 후기</a>

- 설치

  ```jsx
  npm install --save styled-components
  ```

  ```jsx
  //mycode
  const Place = styled.p`
    line-height: 35px;
    font-size: 20px;
    font-weight: 600;
  `;
  ```

---

> 요새 뜨고 있는 CSS 전처리기. <br>
> 👍 내가 느낀 장점: 클래스명을 일일히 써주지 않아서 좋다 <br>
> 👎 내가 느낀 단점: 코드가 팔만대장경이 된다..<br>
> 👎 내가 느낀 단점 2: 네스팅을 추천 하지 않는다. 👎 ~~가독성~~

### 🌳 성장 포인트:

- 새로운 툴인 `Styled-Components` 에 생각보다 잘 적응 중
- 컴포넌트명 (클래스명) 작명의 중요성
- 새로운 전처리기의 학습의 재미 🥳
  - 개발자라면 새로운 것에 늘 시도하고 학습을 해야한다!

---

## <p align="center"> `CGW` 📆 11/30

### 📆 `React calendar API` <a href="https://github.com/wojtekmaj/react-calendar">📎 바로가기</a>

1. `install`

   ```jsx
   npm install react-calendar
   ```

2. `CSS import`

   ```jsx
   import "react-calendar/dist/Calendar.css";
   ```

3. `Basic usage` <a href="https://github.com/wojtekmaj/react-calendar#user-guide">📎 명세 바로가기</a>

   ```jsx
   import React, { useState } from "react";
   import Calendar from "react-calendar";

   function MyApp() {
     const [value, onChange] = useState(new Date());

     return (
       <div>
         <Calendar onChange={onChange} value={value} />
       </div>
     );
   }
   ```

4. `calendar` 컴포넌트

   ```jsx
   <Calendar className="calendar" onChange={changeDate} value={value} />
   ```

   - 실험 결과,`value={value}`를 삭제하면 터진다.💣

5. 위의 기본 세팅이 끝났으면 설정 시작!

   ```jsx
   const [value, setValue] = useState(new Date());

   const changeDate = (e) => {
     setValue(e);
   };

   console.log(value.getDay());
   ```

   - 컨벤션에 맞게 state의 이름을 수정
   - `value.getDay()` 값을 확인해 봅니다.
   - `value.getYear()`
   - `value.getDate()`등등 원하는 데이터를 호출해 찍어봅니다.

6. 📝 CSS 수정하기
   1. 🛠 개발자 도구에서 `element`의 클래스 명을 확인
   2. 임포트한 `css`를 진입
   3. ✨ 동일한 클래스 명을 복사하여, 나의 `css`에서 추가 + 수정
   4. 원본 css를 수정 하지 않음

### 📝 `spread operator` <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax"> 📎 전개 구문</a>

- 전개 구문은 반복 가능한 객체 ✨ `iterable`에 적용할 수 있는 문법
- 배열이나 문자를 풀어 `요소 하나하나로 전개` 가능!

  - `string`=`iterable`

  ```jsx
  function sum(x, y, z) {
    return x + y + z;
  }
  const numbers = [1, "Tree", "Apple"];

  console.log(sum(...numbers));
  //"1TreeApple"
  console.log(sum.apply(null, numbers));
  // expected output: 6
  ```

  ```jsx
  //2022.10 Login.js
  const handleUserInfo = (e) => {
    const { name, value } = e.target;
    setInputValue((prev) => ({ ...prev, [name]: value }));
  };
  ```

### 🌳 성장 포인트:

- 전개구문의 학습
- `iterable`학습
- calendar api 학습 👏

---

<p align="center">E.O.D</a>
<p align="center"><a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md">지난주 TIL: 2022.Dec.TIL<a></p>
<p align="center"><a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.12/Dec1stWeek.md">다음주 TIL: 2022.Dec.TIL<a></p>
