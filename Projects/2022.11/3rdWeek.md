## <p align="center"> `CGW` 📆 11/29

- `Stypled component` <a href="https://styled-components.com/">📎 공식문서</a>

### 💅 Styled-Components

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

## <p align="center"> `CGW` 📆 12/1

### 📍 React + Styled-components
`input radio` & `label`

```jsx
<TimePick>
    <TimeRadio
      type="radio"
      name="radio"
      id="firstTime"
      defaultValue="firstTime"
      onChange={() => setPickTime({ pickedTime: '🌞 10:10 AM' })}
    />
    <TimeLabel htmlFor="firstTime">🌞 10:10 AM</TimeLabel>
</TimePick>

    const TimeLabel = styled.label`
      display: flex;
      border: none;
      margin-bottom: 6px;
      padding: 5px;
      height: 50px;
      width: 200px;
      font-weight: 600;
      border-radius: 8px;
      background-color: #ecedf2;
      justify-content: center;
      align-items: center;
    `;

    const TimeRadio = styled.input`
      appearance: unset;

      &:checked + ${TimeLabel} {
        background-color: #fb4357;
        color: white;
      }
    `;
```

  - `&:checked` 인풋 박스가 선택 되었을 때 박스 색상 변경
  - `input radio` & `label` 혼합하여 버튼 박스처럼 보이도록 함
  - `name="radio"` 같은 name을 가진 radio 박스는 하나로 인식함

- 💣 React + input box error!
  >Warning: Failed prop type: You provided a checked prop to a form field without an onChange handler. This will render a read-only field. If the field should be mutable use defaultChecked. Otherwise, set either onChange or readOnly.

- 📌  해결방안:

1. `checked` 속성 대신 `deafultChecked` 속성 사용
1. `onClick` 속성 대신 `onChange` 사용
1. `onClick`을 사용해야한다면 `readOnly` 속성 추가


### 📍 조건부 렌더링 심화

```jsx
  const [selectMenus, setSelectMenus] = useState({
    location: false,
    date: false,
  });

  const { location, date } = selectMenus;
  // 구조 분해 할당
  const selectLocation = e => {
    const { value } = e.target;
    setSelectMenus(prev => ({ ...prev, location: true }));
    // 2️⃣ 이전 값을 전개구문 하고, location 값을 true로 바꿔줌
    setPickPlace(prev => ({ ...prev, value }));
  };

  const selectDate = () => {
    setSelectMenus(prev => ({ ...prev, date: true }));
  };

  <Input
    type="radio"
    name="placeRadio"
    id="gangNam"
    defaultValue="gangNam"
    onChange={selectLocation}
    //1️⃣ onChange 이벤트 
  />
  <Label htmlFor="gangNam">강남점</Label>
  //input label은 위와 쌍으로 기억하면 좋겠다.

  {location && (
    <Calendar/>
    //UI
    )}
    // 3️⃣ UI 렌더
    //input 값에서 바꿔 준 selectLocation 값이 true가 되면 조건부 렌더링 시작

```

- `htmlFor`을 input의 id와 같게 수정 하면 동일 요소로 인식 함
- 전개구문을 하루 전날 공부 하고 오늘 써보니 감회가 새롭다.


### 📍 Styled-components Props.

```jsx
  <Button
  primary={pickPlace === '강남점'}
  />
	// 프롭스 값을 주기 위해서 조건문을 넣어줘야함
	// pickplace 값이 강남점이 아니라면
	// 아래 컴포넌트의 삼항연산자의 true:false 값을 바꾸게 되어 작동 함

  //Styled-components
  background-color: ${props => (props.primary ? '#fb4357' : '#ecedf2')};
```

- 하지만 input은 CSS에서 `checked` 속성 추가로 js보다 쉽게 적용 가능
- 위의 코드로는 그 외 버튼요소에 적용하면 좋곘다.
- 하지만, CSS를 js로 바꾸는건 훌륭한 사안은 아닌 듯

### 🌳 성장 포인트 
  - 궁금하면 물어보자, 동기든 멘토든 인터넷이든!
    - input 박스 에러, 스타일 컴포넌트 props 사용 법, 조건부 렌더링 등 많은 힌트를 얻어 성공해냄
  - 조건부 렌더링도 좋지만 삼항 연산자를 사용하여 오류를 최소화 하자
    - `useState`를 숫자로 관리하면, `0` 일때 화면에 렌더링 되는 오류가 있기 떄문
    - 실제로 내가 겪은 오류 <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md#%EF%B8%8F-%EC%9D%B4%EC%8A%88-%EC%88%98%EC%A0%95">📎 0이 화면에 그려진다...</a>
    - 그리고 이번주 출근길에 읽은 조건부렌더링 아티클 <a href="https://medium.com/geekculture/stop-using-for-conditional-rendering-in-react-a0f7b96200f8">📎 Stop Using “&&” for Conditional Rendering in React</a>

---

## <p align="center"> `CGW` 📆 12/2


### 📍 삼항연산자를 사용한 화면 UI 변경

```jsx
//기존 조건부 렌더링 UI
 {location && (
  <Calendar
    className="calendar"
    value={value}
    onChange={changeDate}
  />
)}
```

- UI가 비어 보이는 것이 오류로 보인다.
- 사용자의 혼란을 줄이기 위하여 `location` 값이 false 일 때 보여줄 UI 제작
- 애니메이션 적용으로 매끄러운 트랜지션 적용
- 어제 올린 글의 <a href="https://medium.com/geekculture/stop-using-for-conditional-rendering-in-react-a0f7b96200f8">📎 Stop Using “&&” for Conditional Rendering in React</a> 의 의견을 착안하여, 무분별한 조건부 렌더링을 줄이고자 하였음
- 결과는 매우 흡족 👍