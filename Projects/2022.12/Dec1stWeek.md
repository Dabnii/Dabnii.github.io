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
    onChange={() => setPickTime({ pickedTime: "🌞 10:10 AM" })}
  />
  <TimeLabel htmlFor="firstTime">🌞 10:10 AM</TimeLabel>
</TimePick>;

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

  > Warning: Failed prop type: You provided a checked prop to a form field without an onChange handler. This will render a read-only field. If the field should be mutable use defaultChecked. Otherwise, set either onChange or readOnly.

- 📌 해결방안:

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

<img width="1159" alt="스크린샷 2022-12-03 오후 7 42 57" src="https://user-images.githubusercontent.com/110847597/205437000-9a1582de-d6de-4707-ad36-263034c8d5f3.png">

```jsx
//기존 조건부 렌더링 UI
{
  location && (
    <Calendar className="calendar" value={value} onChange={changeDate} />
  );
}
```

- UI가 비어 보이는 것이 오류로 보인다.
  - 나였다면 오류인 줄 알고 새로고침을 여러번 누를 것 같고, 플로우에 대해서 굉장히 혼란스러울 것 같다. 고로 나쁜 서비스 경험!
- 사용자의 혼란을 줄이기 위하여 `location` 값이 false 일 때 보여줄 UI 제작
- 애니메이션 적용으로 매끄러운 트랜지션 적용
- 어제 올린 글의 <a href="https://medium.com/geekculture/stop-using-for-conditional-rendering-in-react-a0f7b96200f8">📎 Stop Using “&&” for Conditional Rendering in React</a> 아티클을 참고하여, 무분별한 조건부 렌더링을 줄이고자 하였음
  - 결과는 매우 흡족 👍 👇

![수정후 UI](https://user-images.githubusercontent.com/110847597/205437284-646c3d1f-eb44-4656-8b5f-7ea101df6702.gif)

```jsx
//삼항 연산자를 적용한 렌더 & UI 변경
{location ? (
    <Calendar
      className="calendar"
      value={value}
      onChange={changeDate}
    />
  ) : (
    <CalenderReadyBox>
      <CalendarReadyText>
        🍿 영화관을 먼저 선택해주세요!
      </CalendarReadyText>
    </CalenderReadyBox>
  )}
</CalenderBox>
```

### 🔍 radio 박스의 Value를 알아보자!

```jsx
  const [selectMenus, setSelectMenus] = useState({
    location: false,
    date: false,
    movieTime: false,
  });

const selectTime = (e) => {
  const { value } = e.target;
  setPickTime((prev) => ({ ...prev, pickedTime: value }));
  setSelectMenus((prev) => ({ ...prev, movieTime: true }));
  //아래의 코드를 작성 후 위의 코드 작성했다
  //며칠 째 꾸준히 등장하는 ((prev) => ({ ...prev, movieTime: true }))!
  // 즉 movieTime: true로 바꿔주는 것!

  onChange={e => {
    console.log(e.target.value);
    setPickTime({ pickedTime: '🌞 10:10 AM' });
  }}

};
```

### 📆 달력의 데이터를 객체에 담아보자!

```jsx
setPickDay((prev) => ({
  ...prev,
  time: { month: e.getMonth() + 1, day: e.getDate() },
}));
```

- `y((prev) => ({...prev,{ month: e.getMonth() + 1, day: e.getDate() }`
  - 위의 코드로 작성하면 제대로 오류가 생긴다.
  - 왜냐, object key가 없기 때문이다!
  - key를 넣어준다면 제대로 담긴다! 🫡

### 🌳 성장 포인트

- 삼항연산자, 조건부 렌더링을 더 유연하게 사용하게 되었다.
- useNavigate를 사용하여 장소→날짜→시간 조건(플로우)이 성립되어야 좌석 선택으로 진행할 수 있도록 했다.
- 날짜 선택의 `onChange` 함수에 기능을 추가 정확한 기능 구현을 완료했다.
- `e.target.value` value 값을 확인하는 방법! 기억 기억!
  ```jsx
    onChange={e => {
    console.log(e.target.value);
    setPickTime({ pickedTime: '🌞 10:10 AM' });
  }}
  ```
- 정말 어제보다 나은 개발자가 되고있다 💪

## <p align="center"> `CGW` 📆 12/3

### 📍 닐짜 데이터를 문자열로 가져오기

```jsx
const changeDate = (e) => {
  setValue(e);
  setPickDay((prev) => ({
    ...prev,
    date: {
      year: `${e.getFullYear()}` + "년",
      month: `${e.getMonth() + 1}` + "월",
      day: `${e.getDate()}` + "일",
    },
  }));

  setSelectMenus((prev) => ({ ...prev, movieDate: true }));
  console.log(pickDay);
  //year:2022
  //month: 12월
  //day: 4일
};
```

- 위의 방법은 템플릿 리터럴도 사용하고, ~~리액트가 싫어하고~~ 효율적이지 못한 것 같다.
- 스트링으로 전달 해주면 되는 것이라 아래의 코드로 수정하고 있다.
- <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date">📎MDN Date</a>
  - 공식문서를 수시로 확인 하자!

```jsx
const changeDate = (e) => {
  const options = {
    weekday: "long",
    year: "numeric",
    month: "long",
    day: "numeric",
  };
  setValue(e);

  setPickDay((prev) => ({
    ...prev,
    date: e.toLocaleDateString("ko-KO", options),
  }));

  setSelectMenus((prev) => ({ ...prev, movieDate: true }));

  console.log(pickDay);
  console.log(e.toLocaleDateString("ko-KO", options));
  // 2022년 12월 4일
};
```

- 객체의 value값으로 저장된 값을 문자열로 바꿔서 전달해야한다.
- 두번째 코드로 수정 중이고, 이렇게 보내는 것이 맞을 것 같다!
- 내일 또는 빠른 시일내에 백엔드와 통신해보면 될 것 같다.
- 내일은 useParams, 쿼리스트링을 사용한 동적 라우팅을 할 계획이다.
- useEffect, fetch를 사용하여 데이터 전송 기능도 구현 예정

### 🌳 성장 포인트

- 더 효율적인 방법을 생각하고 접근 하고 있다.
- date를 쉽고 효율적으로 변환하기 위하여 고민하면서 `구글링`을 통해 많은 도움을 얻었다.

## <p align="center"> `CGW` 📆 12/4

### 💅 Styled-Components, 약 일주일 후기

![image](https://user-images.githubusercontent.com/110847597/205453442-b23ea134-6bc9-4b30-a62d-2b9d05fe5449.png)

> 약 일주일 사용 후기: <br>
> 최상위 에서 최하단까지 움직이는 수직적 동선이 불편하긴 하다. <br>
> 하지만 그만큼 클래스 네임이 오염 되지 않고 한 번만 지정해 주면 되니까 이 부분이 가장 큰 장점 같다. <br> `But` 컴포넌트를 선언함과 동시에 서둘러 `styled.tag`를 지정해주어야 한다. 그러지 않으면 리액트 경고창을 만나게 된다. 😒😒😒 (이게 최악)<br>
> 그래서 서둘러 배경색이든, 너비값이라도 줘야한다..

- <i>나의 일주일 styled-components 후기는 위 이미지와 같다.
- 뭐야, 너무 길고 계속 오류 뜨잖아?
- 어? 근데 또 `클래스 네임 한번만 써주면 된다`고?
- 그래도 `수직 동선` 귀찮네🤨
- 지금은 말할 수 있다, 난 새로운 툴이 좋다...~~신선해~~🤫
- 이의 제기시, 여러분이 다 맞습니다...🙇‍♀️</i>

<br>

### 🪟 모달창을 띄워보자

```jsx
const [showSeat, setShowSeat] = useState(false);
//BookB를 숨기도록 false로 준다. 0으로 주면 오류뜬다 주의

{
  movieTime ? (
    <SeatButton onClick={() => setShowSeat(true)}>좌석 선택</SeatButton>
  ) : (
    //좌석 선택 버튼이 활성화 되었을 때, 온클릭 이벤트가 발생하면 setShowSeat를 True로 바꿔준다
    <SeatButtonGrey onClick={() => alert("예매 정보를 모두 선택해주세요!")}>
      좌석 선택
    </SeatButtonGrey>
  );
}

{
  showSeat && <BookB />;
}
//showSeat가 true가 되었다면 하면에 뜬다!
```

- 📌 오랜만의 복기, 조건부 렌더링

  - 삼항연산자를 쓰지 않은 이유, 필요없다. 이게 더 짧다
  - 고민 추가: 다른 팀원이 작업한 컴포넌트 인데 닫기 버튼 기능 구현이 필요하다
  - 위의 로직보다 더 효율적으로 쓸 수 있는 방법이 있을 것 같다.
  - 예를 들면, 아래의 계산된 속성명에서 사용가능할 것 같다.
    - selectMenus에 `movieSeat`을 넣는 방식도 고려해봐야겠다.

  ```jsx
  const [selectMenus, setSelectMenus] = useState({
    movieLocation: false,
    movieDate: false,
    movieTime: false,
  });

  const { movieLocation, movieDate, movieTime } = selectMenus;
  ```

### 🌳 성장 포인트:

- 정말 매 순간이 성장 포인트다. 내가 꾸준히 남긴 글의 도움을 받고있다. 예를 들면, 이전에 구현해봤던 코드, 로직을 활용하면서 새롭게 쓰고있다.

---

## <p align="center"> `CGW` 📆 12/5

### ⚒️ 리팩토링

- 하나의 state로 값 관리하기
- nesting map

  ```jsx
  //리팩토링 전
  const [showSeat, setShowSeat] = useState(false);

  const [selectMenus, setSelectMenus] = useState({
    movieLocation: false,
    movieDate: false,
    movieTime: false,
    movieSeat: false,
  });

  const { movieLocation, movieDate, movieTime, movieSeat } = selectMenus;

  const selectLocation = (e) => {
    const { value } = e.target;
    setSelectMenus((prev) => ({ ...prev, movieLocation: true }));
    setPickPlace((prev) => ({ ...prev, value }));
    console.log(pickPlace);
  };

  const changeDate = (e) => {
    const options = {
      weekday: "long",
      year: "numeric",
      month: "long",
      day: "numeric",
    };
    setValue(e);

    setPickDay((prev) => ({
      ...prev,
      date: e.toLocaleDateString("ko-KO", options),
    }));

    setSelectMenus((prev) => ({ ...prev, movieDate: true }));

    console.log(pickDay);
  };

  const selectTime = (e) => {
    const { value } = e.target;
    setPickTime((prev) => ({ ...prev, pickedTime: value }));
    setSelectMenus((prev) => ({ ...prev, movieTime: true }));
    console.log(pickTime);
  };
  ```

  ```jsx
  //리팩토링 후
  const BookARsv = () => {
    const [movieData, setMovieData] = useState([]);
    const [value, setValue] = useState(new Date());
    const [showSeat, setShowSeat] = useState(false);

    const [selectList, setSelectList] = useState({
      place: "",
      day: "",
      time: "",
    });

    const { place, time, day } = selectList;

    const selectLocation = (e) => {
      const { name, value } = e.target;
      setSelectList((prev) => ({ ...prev, [name]: value }));
    };

    console.log(selectList);

    const changeDate = (e) => {
      setValue(e);
      setSelectList((prev) => ({ ...prev, day: e }));
    };


    if (movieData == null) return null;
  ```

- 육안으로도 보이는 가독성이 좋아진 코드!
- 가장 인상 깊었던 부분은 하나의 state로 값을 관리하고, 그 값을 활용하여 조건부 렌더링을 사용하는 것.
  - 많은 공부를 해서 가독성 좋고 제대로 작동하는 코드를 작성하자! 💪

### 🌳 성장 포인트

- 좋은 코드는 짧지만 효율적이고 제대로 기능한다.
- 초기화 버튼 기능 구현 중 `delete` 메소드를 찾았다!
  - 하지만 위의 값이 바뀌면 UI가 재 렌더링 되어야하는데 useEffect에 state 값을 넣으면 ... 터지기 때문에 새로운 방법을 고안해야한다.

## <p align="center"> `CGW` 📆 12/6

### 📍 `Not 연산자`

```jsx
//bafore
if (movieData == null) return null;

//after
if (!movieData) return null;
```

- 두 코드는 같다.
  - 매번 선언 할 필요 없이 `return`위에 선언
  - 작은것도 다시 생각해보는 습관이 필요하다

### 📍 초기화 버튼 기능 수정

```jsx
//after
const deleteObj = () => {
  setSelectList({ place: "", day: "", time: "" });
};

//before
const deleteObj = () => {
  delete selectList.place;
  delete selectList.day;
  delete selectList.time;
};
```

- 🔍 `delete` 메소드는 `Key` & `Value`를 지운다.
- 그러하여 after 코드로 리팩토링
- 잘 짜여진 코드는 물 흐르듯 기존 기능들과 잘 작동한다
  - 리팩토링 한 코드는 초기값(true)으로 돌아가기에 uesEffect를 사용 할 필요도 없다!

### 📍 `Nesting Map`

```jsx
  {movieData?.map((movie, index) => (
    <PlacePickTextSeoul key={index}>
      <PlaceTextBox key={movie.region_id}>
        <PlacePickP>📍{movie.name}</PlacePickP>
      </PlaceTextBox>
      <PlacePickButtonContainer>
        <Pick>
      {movie.location.map(lo => {
        return (
          <>
            <Input
              type="radio"
              name="place"
              id={lo.branch_id}
              defaultValue={lo.branch_name}
              onChange={onChangeData}
            />
            <Label htmlFor={lo.branch_id}>{lo.branch_name}</Label>
          </>
      );
  })}
```

- 중첩 map을 사용하여 버튼을 바르게 렌더했다.
- 수정 과정
  - Mock data의 구조를 바꾸어 렌더
  - 중첩 맵을 활용하여 객체안의 객체 데이터 (branch)를 렌더
  - 데이터가 가진 지점의 데이터는 1개이지만, UI는 2개 이기에 지점이 두 번 렌더 됨

💪 Before

![Issue](https://user-images.githubusercontent.com/110847597/206710723-c5c147ad-9d9d-460a-8850-247fa312cf07.png)

👍 After (내가 원했던 렌더 모습)

<img width="1038" alt="스크린샷 2022-12-09 오후 10 08 47" src="https://user-images.githubusercontent.com/110847597/206710812-c12b221e-7e7e-4cd1-a04e-97b4b07ae650.png">

<br>

```js
//before
[
  {
    id: 1,
    thumbnail: "/images/insideOut.jpg",
    title: "inside Out",
    region: "서울",
    branch: "CGW 강남",
    rooms: "3관",
    date: "2022년 12월 6일(금)",
    date_times: "10:30",
    seat: "D6",
    price: "12000",
    ageLimit: 19,
    rate: 4.5,
  },
  {
    id: 2,
    thumbnail: "/images/insideOut.jpg",
    title: "insideOut",
    region: "서울",
    branch: "CGW 선릉",
    rooms: "3관",
    date: "2022년 12월 6일(금)",
    date_times: "22:40",
    seat: "D6",
    price: "12000",
  },
];
```

```js
[
  {
    "region_id": 1,
    "name": "서울",
    "location": [
      {
        "branch_id": 1,
        "branch_name": "강남"
      },
      {
        "branch_id": 2,
        "branch_name": "강변"
      }
    ]
  },
  {
    "region_id": 2,
    "name": "경기",
    "location": [
      {
        "branch_id": 3,
        "branch_name": "경기광주"
      },
      {
        "branch_id": 4,
        "branch_name": "고양행신"
      }
    ]
]
```

### 💪 일정 시간 예매 가능/불가능 버튼 구현 🤯🤯🤯

```jsx
let todayHour = new Date().getHours();
let today = todayHour;

let movieTime = new Date("August 19, 1975 14:15:30");
let movieHour = movieTime.getHours();

const calcTime = () => {
  let leftTime = todayHour - movieHour;
  if (leftTime < 1) {
    console.log("예매가 마감된 영화입니다!");
  } else {
    console.log("OK");
  }
};

console.log(calcTime());
console.log(todayHour);
console.log(movieHour);
```

1. `new Date()` 현재 값과 영화 상영 시간을 비교하여 연산
2. `filter`를 사용하여 특정한 조건에 부합하는 것만 찾을 수 있다.
3. 여기엔 여러가지 솔루션이 있는데
   1. 위의 코드들을 활용하여 기능 구현 (🤔 유지보수 부분이나 가독성 부분에서 훌륭한 방법은 아닌 것 같다.)
   1. BE에게 데이터 수정을 요청한다 (현재 받는 time의 값은 `08:30`, `11:24` 스트링으로 들어온다)
   1. BE 팀에게 영화 상영 시간에 대한 필터링 기능 구현을 요청한다
4. 교훈: 내가 어려운 건 어려운 것이 맞다.
5. 기획 부분에서 더 꼼꼼히 (데이터를 어떻게 받는지) 논의 했다면 수정 과정이 줄어들었을 것 같다.

### 🌳 성장 포인트

- 데이터 구조에 따른 UI 렌더 방식과 정제 과정...
- Map 메소드를 중첩 할 수 있다
- 프론트엔드에서 데이터를 어느정도 정제 할 수 있지만, best는 기획단계(통신 방법과 데이터 타입, 구조)에 대해서 더 이야기를 나눠볼 것!

## <p align="center"> `CGW` 📆 12/7

### 🫂 중첩 삼항연산자

- 첫번째 삼항 연산자
  - 조건: `영화관`이 선택 되었다면
  - `true`일 때 해당 일자에 대한 영화 시간을 UI로 그려내고
    - ✨ `true` 이지만, 해당 영화 시간이 없다면 `영화가 매진 되었습니다` 라는 문구를 띄운다
  - `false`라면 `영화를 먼저 선택해 주세요!`라는 문구를 띄운다
    - 이러한 방법을 채택한 이유 <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.12/Dec1stWeek.md#-%EC%82%BC%ED%95%AD%EC%97%B0%EC%82%B0%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%ED%99%94%EB%A9%B4-ui-%EB%B3%80%EA%B2%BD">📎 빈칸은 오류로 보인다! 12/2</a>
      - 실제 영화 사이트 처럼 영화, 시간, 일자를 누를 때 마다 유연하게 데이터를 처리하면 좋겠지만, 난이도가 높아서 UI를 순차적으로 그려주는 것으로 진행했다.
      - 난이도 조절과 유저에게 우리가 원하는 flow로 진행 할 수 있어서 꽤 뿌듯하다.
  - 👏 사실 위의 기능을 뇌로는 이해했지만, 코드로 구현하지 못해서 답답한 부분이 있었다.
  - 하나씩 뜯어보고, 동기에게 많은 도움을 얻어 성공했다! 👇

```jsx
<TimePickContainer>
  {day ? (
    <TimePick>
      {timeFilter.length !== 0 ? (
        timeFilter.map((movieTime, i) => {
          return (
            <React.Fragment key={i}>
              {timeFilter[i].time.map((detailTime, index) => {
                return (
                  <React.Fragment key={index}>
                    <TimeRadio
                      type="radio"
                      name="time"
                      id={detailTime.time}
                      defaultValue={detailTime.time}
                      onChange={onChangeData}
                    />
                    <TimeLabel htmlFor={detailTime.time}>
                      {detailTime.time}
                    </TimeLabel>
                  </React.Fragment>
                );
              })}
            </React.Fragment>
          );
        })
      ) : (
        <TimePickReadyBox>
          <TimePickReady>🥲 매진 되었어요!</TimePickReady>
        </TimePickReadyBox>
      )}
    </TimePick>
  ) : (
    <TimePickReadyBox>
      <TimePickReady>📆 날짜를 먼저 정해주세요!</TimePickReady>
    </TimePickReadyBox>
  )}
</TimePickContainer>
```

### 🌳 성장 포인트

- 영화시간이 없을 경우의 코드를 알럿으로 띄울 수 있었지만, 중첩 삼항 연산자를 사용하여 더 적은 코드로 메세지를 렌더링 했음!
- 하나의 함수 안에 처리해야할 데이터나 함수가 있다면 느리게 처리된다. (당연함)
- `fetch`가 진행하는 비동기적 특성을 주말에 공부!
  - 자바스크립트는 동기적 언어이다
  - 브라우저 엔진에서 작동 할 때는 비동기적으로 처리 된다.
  - 그리고 fetch... 비동기적... 공부를 하지 않으려야 하지 않을 수가 없는 매력적인 조합이다🔥
  - ~~따뜻한 아이스아메리카노~~ ~~화려하지만 심플한~~

## <p align="center"> `CGW` 📆 12/8

### 🔍 `filter` 검색어로 영화 리스트를 찾자!

```jsx
const [showList, setShowList] = useState(false);

{
  showList && (
    <SearchList
      onMouseOut={() => {
        setShowList(false);
      }}
      onMouseOver={() => {
        setShowList(true);
      }}
    >
      <ListOverContainer>
        {movieList.map((list, index) => {
          if (list.title.toLowerCase().includes(inputState)) {
            return (
              <StyledLink key={index} to={`/times/${list.id}`}>
                <MovieFiltered>
                  <MovieInfoBox>
                    <ThumbsImg>
                      <Thumb src={list.thumbnail} alt="thumb nail" />
                    </ThumbsImg>
                    <MatchedTitle>{list.title}</MatchedTitle>
                  </MovieInfoBox>
                  <BookNow>🎫 예매하기</BookNow>
                </MovieFiltered>
              </StyledLink>
            );
          } else {
            return null;
          }
        })}
      </ListOverContainer>
    </SearchList>
  );
}
```

- `if (list.title.toLowerCase().includes(inputState))`
  - 1차 프로젝트 때, 아리송 했던 코드가 이젠 명확하게 이해가 된다!
- `<StyledLink key={index} to={`/times/${list.id}`}>`
  - 받아오는 데이터의 영화 `id`와 `const params = useParams()` 코드!
- `SearchList`에서 마우스가 떠난다면, 해당 div를 사라지게 하기
  - [이슈] 추천 검색 list div에 마우스가 오버 되면 SearchList가 사라졌다.

```jsx
//after
      <Form.Control
        style={{ height: '35px' }}
        type="search"
        placeholder="Search"
        className="me-2"
        aria-label="Search"
        onChange={e => {
          setInputState(e.target.value);
          if (e.target.value.length > 0) {
            setShowList(true);
          } else {
            setShowList(false);
          }
        }}
        value={inputState}
      />
      <Button
        variant="danger"
        style={{
          height: '35px',
          width: '80px',
          padding: '2px 8px',
        }}
      >
        검색
      </Button>
    </Form>
  </Navbar.Collapse>
  {showList && (
    <SearchList
      onMouseOut={() => {
        setShowList(false);
      }}
      onMouseOver={() => {
        setShowList(true);
      }}
    >
```

- `SearchList`에서 마우스가 떠난다면, 해당 div를 사라지게 하기
  - [해결] state로 인풋값을 변환하지만, 어떠한 값으로 바뀌는지 정확히 전달 하지 않았음.
  - 아래의 값과 조건을 주어 렌더링 하기
  ```jsx
  if (e.target.value.length > 0) {
    setShowList(true);
  } else {
    setShowList(false);
  }
  ```
  - 박, 심교수님 절 올립니다🙇‍♀️
    - 얼른 코흘리개에서 벗어나서 도움을 주는 개발짱이 되겠습니다.

### 🌳 성장 포인트

- `useParams`를 사용한 filter 기능에서 링크 연결
- 간단해 보이지만 구현은 그렇지 않은 영화 검색 기능
- 홀로 작성하고 방법을 찾아내고 구현해내는 코드들이 늘어나고 있다 👍👍

## <p align="center"> `CGW` 📆 12/9 `The last day!`

Big day

### 2주간의 프로젝트 회고하기 : 나에 대한 회고

> <a href="https://www.marimba.team/kr/blog/top-retrospective-templates/">📎 애자일 회고(Agile Retrospective)를 위한 템플릿 추천</a>

## 1️⃣ Continue – Stop – Start

- 팀이 지속해서 유지해야 할 것, 그만 두어야할 것, 그리고 새롭게 시작해보아야 할 것 이렇게 세 가지 항목으로 회고를 구성하여 진행해보세요.
- 팀원들로부터 더 나은 팀을 만들기 위한 새로운 제안, 개선점 등을 이끌어내기 아주 좋은 방법이 될 거예요😉

## 2️⃣ 4L: Liked, Learned, Lacked, Longed for

- 😍 좋았던 것(`L`iked)
- 📚 배운 것(`L`earned)
- 💦 부족했던 것(`L`acked)
- 🕯 바라는 것(`L`onged for)
  - 오로지 내가 수행했던 일에만 집중해서 솔직하게 정리해보세요!

## 3️⃣ KPT (Keep – Problem – Try)

- 지속할 것(Keep), 해결할 것(Problem), 시도할 것(Try)!
- 지난 프로젝트를 되돌아보며 세 가지로 나눠 정리하고 함께 되짚어봅니다.
- ❤️ 지속할 것 (Keep)
  - 좋았던 점을 기반으로 앞으로 프로젝트를 진행할 때 계속 유지해야 할 사항!
  - 잘한 부분에는 칭찬과 박수 마구마구 보내주기, 잊지 마세요.
- 🧐 해결할 것 (Problem)
  - 아쉬웠던 점을 기반으로 앞으로 프로젝트를 진행할 때 개선되어야 할 사항!
  - 단순히 일어난 사건뿐만 아니라 사건에 이르기까지의 과정을 나누는 게 좋아요.
- 🙌 시도할 것 (Try)
  - 앞서 이야기한 해결할 문제들의 원인을 파악하여 앞으로 시도해볼 만한 사항!
  - 회고 이후 액션 아이템을 구체화하는 것이 포인트입니다.

## 1️⃣ Continue – Stop – Start

- `Continue` : 끊임 없는 도전, 에러창 만나고 스스로 해결 하기, TIL을 더 꼼꼼히 작성하기
- `Stop` : 처음부터 완벽한 코드를 기대하는 것, 스스로에게 은연중 스트레스를 준다
- `Start` : 백엔드와 통신을 위하여 `ERD` 작성법과 읽는 법 공부

## 2️⃣ 4L: Liked, Learned, Lacked, Longed for

- 😍 좋았던 것(`L`iked)
  - 든든한 동기들과 함께 작성하는 코드
  - 어렵지만 1차 프로젝트 때 보다 심화 된 레벨의 프로젝트 (필터링& 동적라우팅)
  - 매일 아침 정각, 팀원들이 미리 작성한 스탠드업 템플릿을 기반으로 데일리 스탠드업을 진행 한 것
  - 애자일 개발을 위한 트렐로 사용 및 활용
- 📚 배운 것(`L`earned)
  - 많이 넘어지고 에러창을 만나고 해결하면서 성장했다.
  - 코드 리팩토링을 통하여 더 좋은 코드는 수정이 되어도 물 흐르듯이 자연스럽게 작동하는 것
- 💦 부족했던 것(`L`acked) - 에러 대처법이 아직 미숙하고, console.log를 활용한 디버깅 숙련도가 낮음 - 돌발 상황(e.g. 전달해야할 데이터 타입이 바뀌어야한다거나 또는 그 반대의 경우)에서 블락커를 많이 만났다. - 예를 들면, 내가 데이터 타입을 정체하는데 많은 리소스가 들고 비효율 적이라는 판단이 내려진다면, 백엔드에 데이터 변경을 요청해도 된다는 점 - 처음이고, 기획 단계에서 완벽하다 생각한 부분에서도 변수가 늘 생겼기에 수시로 논의해보고 변수에 흔들리지 않는 마음가짐
  - > 제가 어렵다고 생각하는 부분은 모두가 어려운 것이 맞고, 고민이 깊어질 때면 팀원이든 멘토님과 의견을 나눠보는것도 방법이라는 것을 배웠습니다. 이건 여러분과 공유하면 좋을 것 같아 작성합니다..
    > 즉 혼자 깊게 고민하고 앓지 말기! 12/7 스탠드업 미팅 -나-
- 🕯 바라는 것(`L`onged for)
  - 기존 사이트의 복잡한 UI를 개선하여 사용자에게 예매를 직관화 하여 예매를 쉽게 하는 것
  - 에러나 문제없이 잘 돌아가는 예매사이트 🔥

---

<p align="center">E.O.D
