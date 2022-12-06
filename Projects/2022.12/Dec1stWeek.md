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
  - 
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

  const selectLocation = e => {
    const { value } = e.target;
    setSelectMenus(prev => ({ ...prev, movieLocation: true }));
    setPickPlace(prev => ({ ...prev, value }));
    console.log(pickPlace);
  };

  const changeDate = e => {
    const options = {
      weekday: 'long',
      year: 'numeric',
      month: 'long',
      day: 'numeric',
    };
    setValue(e);

    setPickDay(prev => ({
      ...prev,
      date: e.toLocaleDateString('ko-KO', options),
    }));

    setSelectMenus(prev => ({ ...prev, movieDate: true }));

    console.log(pickDay);
  };

  const selectTime = e => {
    const { value } = e.target;
    setPickTime(prev => ({ ...prev, pickedTime: value }));
    setSelectMenus(prev => ({ ...prev, movieTime: true }));
    console.log(pickTime);
  };
  ```
    ```jsx
  //리팩토링 후 
    const [selectList, setSelectList] = useState({
      place: "",
      day: "",
      time: "",
    });
  ```

```jsx
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

  useEffect(() => {
    fetch("/data/movieData.json")
      .then((res) => res.json())
      .then((data) => {
        setMovieData(data);
      });
  }, []);

  if (movieData == null) return null;

  return (
    <>
      <ReservationContainer>
        <PlaceSelect>
          <StepTitle>STEP1</StepTitle>
          <SubTitle>지역/영화관 선택</SubTitle>
          <PlacePick>
            {movieData?.map((data, index) => (
              <PlacePickTextSeoul key={index}>
                <PlaceTextBox key={data.id}>
                  <PlacePickP>📍{data.region}</PlacePickP>
                </PlaceTextBox>
                <PlacePickButtonContainer>
                  <Pick>
                    <Input
                      type="radio"
                      name="place"
                      id="theater"
                      defaultValue={data.branch}
                      onChange={selectLocation}
                    />
                    <Label htmlFor={data.branch}>{data.branch}</Label>
                    <Input
                      type="radio"
                      name="place"
                      id={data.branch}
                      defaultValue={data.branch}
                      onChange={selectLocation}
                    />
                    <Label htmlFor={data.branch}>{data.branch}</Label>
                  </Pick>
                </PlacePickButtonContainer>
              </PlacePickTextSeoul>
            ))}
          </PlacePick>
        </PlaceSelect>
        <CalendarContainer>
          <PlaceText>
            <StepTitle>STEP2</StepTitle>
            <SubTitle>날짜 선택</SubTitle>
          </PlaceText>
          <CalenderBox>
            {place ? (
              <Calendar
                className="calendar"
                value={value}
                onChange={changeDate}
                minDate={new Date()}
                maxDate={new Date(2022, 11, 16)}
                minDetail="year"
              />
            ) : (
              <CalenderReadyBox>
                <CalendarReadyText>
                  🍿 영화관을 먼저 선택해주세요!
                </CalendarReadyText>
              </CalenderReadyBox>
            )}
          </CalenderBox>
        </CalendarContainer>
        <SelectTime>
          <StepTitle>STEP3</StepTitle>
          <SubTitle>시간 선택</SubTitle>
          <TimePickContainer>
            {day ? (
              <TimePick>
                <TimeRadio
                  type="radio"
                  name="time"
                  id={movieData[0].date_times}
                  defaultValue={movieData[0].date_times}
                  onChange={selectLocation}
                />
                <TimeLabel htmlFor={movieData[0].date_times}>
                  🌞 {movieData[0].date_times}
                </TimeLabel>
                <TimeRadio
                  type="radio"
                  name="time"
                  id={movieData[1].date_times}
                  defaultValue={movieData[1].date_times}
                  onChange={selectLocation}
                />
                <TimeLabel htmlFor={movieData[1].date_times}>
                  🌙 {movieData[1].date_times}
                </TimeLabel>
              </TimePick>
            ) : (
              <TimePickReadyBox>
                <TimePickReady>📆 날짜를 먼저 정해주세요!</TimePickReady>
              </TimePickReadyBox>
            )}
          </TimePickContainer>
        </SelectTime>
      </ReservationContainer>
      <ButtonBox>
        {time ? (
          <SeatButton onClick={() => setShowSeat(true)}>좌석 선택</SeatButton>
        ) : (
          <SeatButtonGrey
            onClick={() => alert("예매 정보를 모두 선택해주세요!")}
          >
            좌석 선택
          </SeatButtonGrey>
        )}
      </ButtonBox>
      {showSeat && <BookB setShowSeat={setShowSeat} />}
    </>
  );
};

export default BookARsv;
```

### 🌳 성장 포인트

- 좋은 코드는 짧지만 효율적이다.
- 


## <p align="center"> `CGW` 📆 12/6

