## <p align="center"> `CGW` π 12/1

### π React + Styled-components

`input radio` & `label`

```jsx
<TimePick>
  <TimeRadio
    type="radio"
    name="radio"
    id="firstTime"
    defaultValue="firstTime"
    onChange={() => setPickTime({ pickedTime: "π 10:10 AM" })}
  />
  <TimeLabel htmlFor="firstTime">π 10:10 AM</TimeLabel>
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

- `&:checked` μΈν λ°μ€κ° μ ν λμμ λ λ°μ€ μμ λ³κ²½
- `input radio` & `label` νΌν©νμ¬ λ²νΌ λ°μ€μ²λΌ λ³΄μ΄λλ‘ ν¨
- `name="radio"` κ°μ nameμ κ°μ§ radio λ°μ€λ νλλ‘ μΈμν¨

- π£ React + input box error!

  > Warning: Failed prop type: You provided a checked prop to a form field without an onChange handler. This will render a read-only field. If the field should be mutable use defaultChecked. Otherwise, set either onChange or readOnly.

- π ν΄κ²°λ°©μ:

1. `checked` μμ± λμ  `deafultChecked` μμ± μ¬μ©
1. `onClick` μμ± λμ  `onChange` μ¬μ©
1. `onClick`μ μ¬μ©ν΄μΌνλ€λ©΄ `readOnly` μμ± μΆκ°

### π μ‘°κ±΄λΆ λ λλ§ μ¬ν

```jsx
  const [selectMenus, setSelectMenus] = useState({
    location: false,
    date: false,
  });

  const { location, date } = selectMenus;
  // κ΅¬μ‘° λΆν΄ ν λΉ
  const selectLocation = e => {
    const { value } = e.target;
    setSelectMenus(prev => ({ ...prev, location: true }));
    // 2οΈβ£ μ΄μ  κ°μ μ κ°κ΅¬λ¬Έ νκ³ , location κ°μ trueλ‘ λ°κΏμ€
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
    //1οΈβ£ onChange μ΄λ²€νΈ
  />
  <Label htmlFor="gangNam">κ°λ¨μ </Label>
  //input labelμ μμ μμΌλ‘ κΈ°μ΅νλ©΄ μ’κ² λ€.

  {location && (
    <Calendar/>
    //UI
    )}
    // 3οΈβ£ UI λ λ
    //input κ°μμ λ°κΏ μ€ selectLocation κ°μ΄ trueκ° λλ©΄ μ‘°κ±΄λΆ λ λλ§ μμ

```

- `htmlFor`μ inputμ idμ κ°κ² μμ  νλ©΄ λμΌ μμλ‘ μΈμ ν¨
- μ κ°κ΅¬λ¬Έμ νλ£¨ μ λ  κ³΅λΆ νκ³  μ€λ μ¨λ³΄λ κ°νκ° μλ‘­λ€.

### π Styled-components Props.

```jsx
  <Button
  primary={pickPlace === 'κ°λ¨μ '}
  />
	// νλ‘­μ€ κ°μ μ£ΌκΈ° μν΄μ μ‘°κ±΄λ¬Έμ λ£μ΄μ€μΌν¨
	// pickplace κ°μ΄ κ°λ¨μ μ΄ μλλΌλ©΄
	// μλ μ»΄ν¬λνΈμ μΌν­μ°μ°μμ true:false κ°μ λ°κΎΈκ² λμ΄ μλ ν¨

  //Styled-components
  background-color: ${props => (props.primary ? '#fb4357' : '#ecedf2')};
```

- νμ§λ§ inputμ CSSμμ `checked` μμ± μΆκ°λ‘ jsλ³΄λ€ μ½κ² μ μ© κ°λ₯
- μμ μ½λλ‘λ κ·Έ μΈ λ²νΌμμμ μ μ©νλ©΄ μ’κ³λ€.
- νμ§λ§, CSSλ₯Ό jsλ‘ λ°κΎΈλκ±΄ νλ₯­ν μ¬μμ μλ λ―

### π³ μ±μ₯ ν¬μΈνΈ

- κΆκΈνλ©΄ λ¬Όμ΄λ³΄μ, λκΈ°λ  λ©ν λ  μΈν°λ·μ΄λ !
  - input λ°μ€ μλ¬, μ€νμΌ μ»΄ν¬λνΈ props μ¬μ© λ², μ‘°κ±΄λΆ λ λλ§ λ± λ§μ ννΈλ₯Ό μ»μ΄ μ±κ³΅ν΄λ
- μ‘°κ±΄λΆ λ λλ§λ μ’μ§λ§ μΌν­ μ°μ°μλ₯Ό μ¬μ©νμ¬ μ€λ₯λ₯Ό μ΅μν νμ
  - `useState`λ₯Ό μ«μλ‘ κ΄λ¦¬νλ©΄, `0` μΌλ νλ©΄μ λ λλ§ λλ μ€λ₯κ° μκΈ° λλ¬Έ
  - μ€μ λ‘ λ΄κ° κ²ͺμ μ€λ₯ <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md#%EF%B8%8F-%EC%9D%B4%EC%8A%88-%EC%88%98%EC%A0%95">π 0μ΄ νλ©΄μ κ·Έλ €μ§λ€...</a>
  - κ·Έλ¦¬κ³  μ΄λ²μ£Ό μΆκ·ΌκΈΈμ μ½μ μ‘°κ±΄λΆλ λλ§ μν°ν΄ <a href="https://medium.com/geekculture/stop-using-for-conditional-rendering-in-react-a0f7b96200f8">π Stop Using β&&β for Conditional Rendering in React</a>

---

## <p align="center"> `CGW` π 12/2

### π μΌν­μ°μ°μλ₯Ό μ¬μ©ν νλ©΄ UI λ³κ²½

<img width="1159" alt="αα³αα³αα΅α«αα£αΊ 2022-12-03 αα©αα? 7 42 57" src="https://user-images.githubusercontent.com/110847597/205437000-9a1582de-d6de-4707-ad36-263034c8d5f3.png">

```jsx
//κΈ°μ‘΄ μ‘°κ±΄λΆ λ λλ§ UI
{
  location && (
    <Calendar className="calendar" value={value} onChange={changeDate} />
  );
}
```

- UIκ° λΉμ΄ λ³΄μ΄λ κ²μ΄ μ€λ₯λ‘ λ³΄μΈλ€.
  - λμλ€λ©΄ μ€λ₯μΈ μ€ μκ³  μλ‘κ³ μΉ¨μ μ¬λ¬λ² λλ₯Ό κ² κ°κ³ , νλ‘μ°μ λν΄μ κ΅μ₯ν νΌλμ€λ¬μΈ κ² κ°λ€. κ³ λ‘ λμ μλΉμ€ κ²½ν!
- μ¬μ©μμ νΌλμ μ€μ΄κΈ° μνμ¬ `location` κ°μ΄ false μΌ λ λ³΄μ¬μ€ UI μ μ
- μ λλ©μ΄μ μ μ©μΌλ‘ λ§€λλ¬μ΄ νΈλμ§μ μ μ©
- μ΄μ  μ¬λ¦° κΈμ <a href="https://medium.com/geekculture/stop-using-for-conditional-rendering-in-react-a0f7b96200f8">π Stop Using β&&β for Conditional Rendering in React</a> μν°ν΄μ μ°Έκ³ νμ¬, λ¬΄λΆλ³ν μ‘°κ±΄λΆ λ λλ§μ μ€μ΄κ³ μ νμμ
  - κ²°κ³Όλ λ§€μ° ν‘μ‘± π π

![μμ ν UI](https://user-images.githubusercontent.com/110847597/205437284-646c3d1f-eb44-4656-8b5f-7ea101df6702.gif)

```jsx
//μΌν­ μ°μ°μλ₯Ό μ μ©ν λ λ & UI λ³κ²½
{location ? (
    <Calendar
      className="calendar"
      value={value}
      onChange={changeDate}
    />
  ) : (
    <CalenderReadyBox>
      <CalendarReadyText>
        πΏ μνκ΄μ λ¨Όμ  μ νν΄μ£ΌμΈμ!
      </CalendarReadyText>
    </CalenderReadyBox>
  )}
</CalenderBox>
```

### π radio λ°μ€μ Valueλ₯Ό μμλ³΄μ!

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
  //μλμ μ½λλ₯Ό μμ± ν μμ μ½λ μμ±νλ€
  //λ©°μΉ  μ§Έ κΎΈμ€ν λ±μ₯νλ ((prev) => ({ ...prev, movieTime: true }))!
  // μ¦ movieTime: trueλ‘ λ°κΏμ£Όλ κ²!

  onChange={e => {
    console.log(e.target.value);
    setPickTime({ pickedTime: 'π 10:10 AM' });
  }}

};
```

### π λ¬λ ₯μ λ°μ΄ν°λ₯Ό κ°μ²΄μ λ΄μλ³΄μ!

```jsx
setPickDay((prev) => ({
  ...prev,
  time: { month: e.getMonth() + 1, day: e.getDate() },
}));
```

- `y((prev) => ({...prev,{ month: e.getMonth() + 1, day: e.getDate() }`
  - μμ μ½λλ‘ μμ±νλ©΄ μ λλ‘ μ€λ₯κ° μκΈ΄λ€.
  - μλ, object keyκ° μκΈ° λλ¬Έμ΄λ€!
  - keyλ₯Ό λ£μ΄μ€λ€λ©΄ μ λλ‘ λ΄κΈ΄λ€! π«‘

### π³ μ±μ₯ ν¬μΈνΈ

- μΌν­μ°μ°μ, μ‘°κ±΄λΆ λ λλ§μ λ μ μ°νκ² μ¬μ©νκ² λμλ€.
- useNavigateλ₯Ό μ¬μ©νμ¬ μ₯μβλ μ§βμκ° μ‘°κ±΄(νλ‘μ°)μ΄ μ±λ¦½λμ΄μΌ μ’μ μ νμΌλ‘ μ§νν  μ μλλ‘ νλ€.
- λ μ§ μ νμ `onChange` ν¨μμ κΈ°λ₯μ μΆκ° μ νν κΈ°λ₯ κ΅¬νμ μλ£νλ€.
- `e.target.value` value κ°μ νμΈνλ λ°©λ²! κΈ°μ΅ κΈ°μ΅!
  ```jsx
    onChange={e => {
    console.log(e.target.value);
    setPickTime({ pickedTime: 'π 10:10 AM' });
  }}
  ```
- μ λ§ μ΄μ λ³΄λ€ λμ κ°λ°μκ° λκ³ μλ€ πͺ

## <p align="center"> `CGW` π 12/3

### π λμ§ λ°μ΄ν°λ₯Ό λ¬Έμμ΄λ‘ κ°μ Έμ€κΈ°

```jsx
const changeDate = (e) => {
  setValue(e);
  setPickDay((prev) => ({
    ...prev,
    date: {
      year: `${e.getFullYear()}` + "λ",
      month: `${e.getMonth() + 1}` + "μ",
      day: `${e.getDate()}` + "μΌ",
    },
  }));

  setSelectMenus((prev) => ({ ...prev, movieDate: true }));
  console.log(pickDay);
  //year:2022
  //month: 12μ
  //day: 4μΌ
};
```

- μμ λ°©λ²μ ννλ¦Ώ λ¦¬ν°λ΄λ μ¬μ©νκ³ , ~~λ¦¬μ‘νΈκ° μ«μ΄νκ³ ~~ ν¨μ¨μ μ΄μ§ λͺ»ν κ² κ°λ€.
- μ€νΈλ§μΌλ‘ μ λ¬ ν΄μ£Όλ©΄ λλ κ²μ΄λΌ μλμ μ½λλ‘ μμ νκ³  μλ€.
- <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date">πMDN Date</a>
  - κ³΅μλ¬Έμλ₯Ό μμλ‘ νμΈ νμ!

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
  // 2022λ 12μ 4μΌ
};
```

- κ°μ²΄μ valueκ°μΌλ‘ μ μ₯λ κ°μ λ¬Έμμ΄λ‘ λ°κΏμ μ λ¬ν΄μΌνλ€.
- λλ²μ§Έ μ½λλ‘ μμ  μ€μ΄κ³ , μ΄λ κ² λ³΄λ΄λ κ²μ΄ λ§μ κ² κ°λ€!
- λ΄μΌ λλ λΉ λ₯Έ μμΌλ΄μ λ°±μλμ ν΅μ ν΄λ³΄λ©΄ λ  κ² κ°λ€.
- λ΄μΌμ useParams, μΏΌλ¦¬μ€νΈλ§μ μ¬μ©ν λμ  λΌμ°νμ ν  κ³νμ΄λ€.
- useEffect, fetchλ₯Ό μ¬μ©νμ¬ λ°μ΄ν° μ μ‘ κΈ°λ₯λ κ΅¬ν μμ 

### π³ μ±μ₯ ν¬μΈνΈ

- λ ν¨μ¨μ μΈ λ°©λ²μ μκ°νκ³  μ κ·Ό νκ³  μλ€.
- dateλ₯Ό μ½κ³  ν¨μ¨μ μΌλ‘ λ³ννκΈ° μνμ¬ κ³ λ―Όνλ©΄μ `κ΅¬κΈλ§`μ ν΅ν΄ λ§μ λμμ μ»μλ€.

## <p align="center"> `CGW` π 12/4

### π Styled-Components, μ½ μΌμ£ΌμΌ νκΈ°

![image](https://user-images.githubusercontent.com/110847597/205453442-b23ea134-6bc9-4b30-a62d-2b9d05fe5449.png)

> μ½ μΌμ£ΌμΌ μ¬μ© νκΈ°: <br>
> μ΅μμ μμ μ΅νλ¨κΉμ§ μμ§μ΄λ μμ§μ  λμ μ΄ λΆνΈνκΈ΄ νλ€. <br>
> νμ§λ§ κ·Έλ§νΌ ν΄λμ€ λ€μμ΄ μ€μΌ λμ§ μκ³  ν λ²λ§ μ§μ ν΄ μ£Όλ©΄ λλκΉ μ΄ λΆλΆμ΄ κ°μ₯ ν° μ₯μ  κ°λ€. <br> `But` μ»΄ν¬λνΈλ₯Ό μ μΈν¨κ³Ό λμμ μλλ¬ `styled.tag`λ₯Ό μ§μ ν΄μ£Όμ΄μΌ νλ€. κ·Έλ¬μ§ μμΌλ©΄ λ¦¬μ‘νΈ κ²½κ³ μ°½μ λ§λκ² λλ€. πππ (μ΄κ² μ΅μ)<br>
> κ·Έλμ μλλ¬ λ°°κ²½μμ΄λ , λλΉκ°μ΄λΌλ μ€μΌνλ€..

- <i>λμ μΌμ£ΌμΌ styled-components νκΈ°λ μ μ΄λ―Έμ§μ κ°λ€.
- λ­μΌ, λλ¬΄ κΈΈκ³  κ³μ μ€λ₯ λ¨μμ?
- μ΄? κ·Όλ° λ `ν΄λμ€ λ€μ νλ²λ§ μ¨μ£Όλ©΄ λλ€`κ³ ?
- κ·Έλλ `μμ§ λμ ` κ·μ°?λ€π€¨
- μ§κΈμ λ§ν  μ μλ€, λ μλ‘μ΄ ν΄μ΄ μ’λ€...~~μ μ ν΄~~π€«
- μ΄μ μ κΈ°μ, μ¬λ¬λΆμ΄ λ€ λ§μ΅λλ€...πββοΈ</i>

<br>

### πͺ λͺ¨λ¬μ°½μ λμλ³΄μ

```jsx
const [showSeat, setShowSeat] = useState(false);
//BookBλ₯Ό μ¨κΈ°λλ‘ falseλ‘ μ€λ€. 0μΌλ‘ μ£Όλ©΄ μ€λ₯λ¬λ€ μ£Όμ

{
  movieTime ? (
    <SeatButton onClick={() => setShowSeat(true)}>μ’μ μ ν</SeatButton>
  ) : (
    //μ’μ μ ν λ²νΌμ΄ νμ±ν λμμ λ, μ¨ν΄λ¦­ μ΄λ²€νΈκ° λ°μνλ©΄ setShowSeatλ₯Ό Trueλ‘ λ°κΏμ€λ€
    <SeatButtonGrey onClick={() => alert("μλ§€ μ λ³΄λ₯Ό λͺ¨λ μ νν΄μ£ΌμΈμ!")}>
      μ’μ μ ν
    </SeatButtonGrey>
  );
}

{
  showSeat && <BookB />;
}
//showSeatκ° trueκ° λμλ€λ©΄ νλ©΄μ λ¬λ€!
```

- π μ€λλ§μ λ³΅κΈ°, μ‘°κ±΄λΆ λ λλ§

  - μΌν­μ°μ°μλ₯Ό μ°μ§ μμ μ΄μ , νμμλ€. μ΄κ² λ μ§§λ€
  - κ³ λ―Ό μΆκ°: λ€λ₯Έ νμμ΄ μμν μ»΄ν¬λνΈ μΈλ° λ«κΈ° λ²νΌ κΈ°λ₯ κ΅¬νμ΄ νμνλ€
  - μμ λ‘μ§λ³΄λ€ λ ν¨μ¨μ μΌλ‘ μΈ μ μλ λ°©λ²μ΄ μμ κ² κ°λ€.
  - μλ₯Ό λ€λ©΄, μλμ κ³μ°λ μμ±λͺμμ μ¬μ©κ°λ₯ν  κ² κ°λ€.
    - selectMenusμ `movieSeat`μ λ£λ λ°©μλ κ³ λ €ν΄λ΄μΌκ² λ€.

  ```jsx
  const [selectMenus, setSelectMenus] = useState({
    movieLocation: false,
    movieDate: false,
    movieTime: false,
  });

  const { movieLocation, movieDate, movieTime } = selectMenus;
  ```

### π³ μ±μ₯ ν¬μΈνΈ:

- μ λ§ λ§€ μκ°μ΄ μ±μ₯ ν¬μΈνΈλ€. λ΄κ° κΎΈμ€ν λ¨κΈ΄ κΈμ λμμ λ°κ³ μλ€. μλ₯Ό λ€λ©΄, μ΄μ μ κ΅¬νν΄λ΄€λ μ½λ, λ‘μ§μ νμ©νλ©΄μ μλ‘­κ² μ°κ³ μλ€.

---

## <p align="center"> `CGW` π 12/5

### βοΈ λ¦¬ν©ν λ§

- νλμ stateλ‘ κ° κ΄λ¦¬νκΈ°
- nesting map

  ```jsx
  //λ¦¬ν©ν λ§ μ 
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
  //λ¦¬ν©ν λ§ ν
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

- μ‘μμΌλ‘λ λ³΄μ΄λ κ°λμ±μ΄ μ’μμ§ μ½λ!
- κ°μ₯ μΈμ κΉμλ λΆλΆμ νλμ stateλ‘ κ°μ κ΄λ¦¬νκ³ , κ·Έ κ°μ νμ©νμ¬ μ‘°κ±΄λΆ λ λλ§μ μ¬μ©νλ κ².
  - λ§μ κ³΅λΆλ₯Ό ν΄μ κ°λμ± μ’κ³  μ λλ‘ μλνλ μ½λλ₯Ό μμ±νμ! πͺ

### π³ μ±μ₯ ν¬μΈνΈ

- μ’μ μ½λλ μ§§μ§λ§ ν¨μ¨μ μ΄κ³  μ λλ‘ κΈ°λ₯νλ€.
- μ΄κΈ°ν λ²νΌ κΈ°λ₯ κ΅¬ν μ€ `delete` λ©μλλ₯Ό μ°Ύμλ€!
  - νμ§λ§ μμ κ°μ΄ λ°λλ©΄ UIκ° μ¬ λ λλ§ λμ΄μΌνλλ° useEffectμ state κ°μ λ£μΌλ©΄ ... ν°μ§κΈ° λλ¬Έμ μλ‘μ΄ λ°©λ²μ κ³ μν΄μΌνλ€.

## <p align="center"> `CGW` π 12/6

### π `Not μ°μ°μ`

```jsx
//bafore
if (movieData == null) return null;

//after
if (!movieData) return null;
```

- λ μ½λλ κ°λ€.
  - λ§€λ² μ μΈ ν  νμ μμ΄ `return`μμ μ μΈ
  - μμκ²λ λ€μ μκ°ν΄λ³΄λ μ΅κ΄μ΄ νμνλ€

### π μ΄κΈ°ν λ²νΌ κΈ°λ₯ μμ 

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

- π `delete` λ©μλλ `Key` & `Value`λ₯Ό μ§μ΄λ€.
- κ·Έλ¬νμ¬ after μ½λλ‘ λ¦¬ν©ν λ§
- μ μ§μ¬μ§ μ½λλ λ¬Ό νλ₯΄λ― κΈ°μ‘΄ κΈ°λ₯λ€κ³Ό μ μλνλ€
  - λ¦¬ν©ν λ§ ν μ½λλ μ΄κΈ°κ°(true)μΌλ‘ λμκ°κΈ°μ uesEffectλ₯Ό μ¬μ© ν  νμλ μλ€!

### π `Nesting Map`

```jsx
{movieData?.map((movie, index) => (
  <PlacePickTextSeoul key={index}>
    <PlaceTextBox key={movie.region_id}>
      <PlacePickP>π{movie.name}</PlacePickP>
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

- μ€μ²© mapμ μ¬μ©νμ¬ λ²νΌμ λ°λ₯΄κ² λ λνλ€.
- μμ  κ³Όμ 
  - Mock dataμ κ΅¬μ‘°λ₯Ό λ°κΎΈμ΄ λ λ
  - μ€μ²© λ§΅μ νμ©νμ¬ κ°μ²΄μμ κ°μ²΄ λ°μ΄ν° (branch)λ₯Ό λ λ
  - λ°μ΄ν°κ° κ°μ§ μ§μ μ λ°μ΄ν°λ 1κ°μ΄μ§λ§, UIλ 2κ° μ΄κΈ°μ μ§μ μ΄ λ λ² λ λ λ¨

πͺ Before

![Issue](https://user-images.githubusercontent.com/110847597/206710723-c5c147ad-9d9d-460a-8850-247fa312cf07.png)

π After (λ΄κ° μνλ λ λ λͺ¨μ΅)

<img width="1038" alt="αα³αα³αα΅α«αα£αΊ 2022-12-09 αα©αα? 10 08 47" src="https://user-images.githubusercontent.com/110847597/206710812-c12b221e-7e7e-4cd1-a04e-97b4b07ae650.png">

<br>

```js
//before
[
  {
    id: 1,
    thumbnail: "/images/insideOut.jpg",
    title: "inside Out",
    region: "μμΈ",
    branch: "CGW κ°λ¨",
    rooms: "3κ΄",
    date: "2022λ 12μ 6μΌ(κΈ)",
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
    region: "μμΈ",
    branch: "CGW μ λ¦",
    rooms: "3κ΄",
    date: "2022λ 12μ 6μΌ(κΈ)",
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
    "name": "μμΈ",
    "location": [
      {
        "branch_id": 1,
        "branch_name": "κ°λ¨"
      },
      {
        "branch_id": 2,
        "branch_name": "κ°λ³"
      }
    ]
  },
  {
    "region_id": 2,
    "name": "κ²½κΈ°",
    "location": [
      {
        "branch_id": 3,
        "branch_name": "κ²½κΈ°κ΄μ£Ό"
      },
      {
        "branch_id": 4,
        "branch_name": "κ³ μνμ "
      }
    ]
]
```

### πͺ μΌμ  μκ° μλ§€ κ°λ₯/λΆκ°λ₯ λ²νΌ κ΅¬ν π€―π€―π€―

```jsx
let todayHour = new Date().getHours();
let today = todayHour;

let movieTime = new Date("August 19, 1975 14:15:30");
let movieHour = movieTime.getHours();

const calcTime = () => {
  let leftTime = todayHour - movieHour;
  if (leftTime < 1) {
    console.log("μλ§€κ° λ§κ°λ μνμλλ€!");
  } else {
    console.log("OK");
  }
};

console.log(calcTime());
console.log(todayHour);
console.log(movieHour);
```

1. `new Date()` νμ¬ κ°κ³Ό μν μμ μκ°μ λΉκ΅νμ¬ μ°μ°
2. `filter`λ₯Ό μ¬μ©νμ¬ νΉμ ν μ‘°κ±΄μ λΆν©νλ κ²λ§ μ°Ύμ μ μλ€.
3. μ¬κΈ°μ μ¬λ¬κ°μ§ μλ£¨μμ΄ μλλ°
   1. μμ μ½λλ€μ νμ©νμ¬ κΈ°λ₯ κ΅¬ν (π€ μ μ§λ³΄μ λΆλΆμ΄λ κ°λμ± λΆλΆμμ νλ₯­ν λ°©λ²μ μλ κ² κ°λ€.)
   1. BEμκ² λ°μ΄ν° μμ μ μμ²­νλ€ (νμ¬ λ°λ timeμ κ°μ `08:30`, `11:24` μ€νΈλ§μΌλ‘ λ€μ΄μ¨λ€)
   1. BE νμκ² μν μμ μκ°μ λν νν°λ§ κΈ°λ₯ κ΅¬νμ μμ²­νλ€
4. κ΅ν: λ΄κ° μ΄λ €μ΄ κ±΄ μ΄λ €μ΄ κ²μ΄ λ§λ€.
5. κΈ°ν λΆλΆμμ λ κΌΌκΌΌν (λ°μ΄ν°λ₯Ό μ΄λ»κ² λ°λμ§) λΌμ νλ€λ©΄ μμ  κ³Όμ μ΄ μ€μ΄λ€μμ κ² κ°λ€.

### π³ μ±μ₯ ν¬μΈνΈ

- λ°μ΄ν° κ΅¬μ‘°μ λ°λ₯Έ UI λ λ λ°©μκ³Ό μ μ  κ³Όμ ...
- Map λ©μλλ₯Ό μ€μ²© ν  μ μλ€
- νλ‘ νΈμλμμ λ°μ΄ν°λ₯Ό μ΄λμ λ μ μ  ν  μ μμ§λ§, bestλ κΈ°νλ¨κ³(ν΅μ  λ°©λ²κ³Ό λ°μ΄ν° νμ, κ΅¬μ‘°)μ λν΄μ λ μ΄μΌκΈ°λ₯Ό λλ λ³Ό κ²!

## <p align="center"> `CGW` π 12/7

### π« μ€μ²© μΌν­μ°μ°μ

![αα?αΌαα₯αΈαα‘α·αα‘αΌαα§α«αα‘α«-αα³α―αα©αα?αα²αα©](https://user-images.githubusercontent.com/110847597/206713220-7804ec0d-dda7-48b9-9008-b75311ba419a.gif)

> Step 3 λ¬Έκ΅¬λ₯Ό μ£Όλͺ©!

- μ²«λ²μ§Έ μΌν­ μ°μ°μ
  - μ‘°κ±΄: `μνκ΄`μ΄ μ ν λμλ€λ©΄
  - `true`μΌ λ ν΄λΉ μΌμμ λν μν μκ°μ UIλ‘ κ·Έλ €λ΄κ³ 
    - β¨ `true` μ΄μ§λ§, ν΄λΉ μν μκ°μ΄ μλ€λ©΄ `μνκ° λ§€μ§ λμμ΅λλ€` λΌλ λ¬Έκ΅¬λ₯Ό λμ΄λ€
  - `false`λΌλ©΄ `μνλ₯Ό λ¨Όμ  μ νν΄ μ£ΌμΈμ!`λΌλ λ¬Έκ΅¬λ₯Ό λμ΄λ€
    - μ΄λ¬ν λ°©λ²μ μ±νν μ΄μ  <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.12/Dec1stWeek.md#-%EC%82%BC%ED%95%AD%EC%97%B0%EC%82%B0%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%ED%99%94%EB%A9%B4-ui-%EB%B3%80%EA%B2%BD">π λΉμΉΈμ μ€λ₯λ‘ λ³΄μΈλ€! 12/2</a>
      - μ€μ  μν μ¬μ΄νΈ μ²λΌ μν, μκ°, μΌμλ₯Ό λλ₯Ό λ λ§λ€ μ μ°νκ² λ°μ΄ν°λ₯Ό μ²λ¦¬νλ©΄ μ’κ² μ§λ§, λμ΄λκ° λμμ UIλ₯Ό μμ°¨μ μΌλ‘ κ·Έλ €μ£Όλ κ²μΌλ‘ μ§ννλ€.
      - λμ΄λ μ‘°μ κ³Ό μ μ μκ² μ°λ¦¬κ° μνλ flowλ‘ μ§ν ν  μ μμ΄μ κ½€ λΏλ―νλ€.
  - π μ¬μ€ μμ κΈ°λ₯μ λλ‘λ μ΄ν΄νμ§λ§, μ½λλ‘ κ΅¬ννμ§ λͺ»ν΄μ λ΅λ΅ν λΆλΆμ΄ μμλ€.
  - νλμ© λ―μ΄λ³΄κ³ , λκΈ°μκ² λ§μ λμμ μ»μ΄ μ±κ³΅νλ€! π

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
          <TimePickReady>π₯² λ§€μ§ λμμ΄μ!</TimePickReady>
        </TimePickReadyBox>
      )}
    </TimePick>
  ) : (
    <TimePickReadyBox>
      <TimePickReady>π λ μ§λ₯Ό λ¨Όμ  μ ν΄μ£ΌμΈμ!</TimePickReady>
    </TimePickReadyBox>
  )}
</TimePickContainer>
```

### π³ μ±μ₯ ν¬μΈνΈ

- μνμκ°μ΄ μμ κ²½μ°μ μ½λλ₯Ό μλΏμΌλ‘ λμΈ μ μμμ§λ§, μ€μ²© μΌν­ μ°μ°μλ₯Ό μ¬μ©νμ¬ λ μ μ μ½λλ‘ λ©μΈμ§λ₯Ό λ λλ§ νμ!
- νλμ ν¨μ μμ μ²λ¦¬ν΄μΌν  λ°μ΄ν°λ ν¨μκ° μλ€λ©΄ λλ¦¬κ² μ²λ¦¬λλ€. (λΉμ°ν¨)
- `fetch`κ° μ§ννλ λΉλκΈ°μ  νΉμ±μ μ£Όλ§μ κ³΅λΆ!
  - μλ°μ€ν¬λ¦½νΈλ λκΈ°μ  μΈμ΄μ΄λ€
  - λΈλΌμ°μ  μμ§μμ μλ ν  λλ λΉλκΈ°μ μΌλ‘ μ²λ¦¬ λλ€.
  - κ·Έλ¦¬κ³  fetch... λΉλκΈ°μ ... κ³΅λΆλ₯Ό νμ§ μμΌλ €μΌ νμ§ μμ μκ° μλ λ§€λ ₯μ μΈ μ‘°ν©μ΄λ€π₯
  - ~~λ°λ»ν μμ΄μ€μλ©λ¦¬μΉ΄λΈ~~ ~~νλ €νμ§λ§ μ¬νν~~

## <p align="center"> `CGW` π 12/8

### π `filter` κ²μμ΄λ‘ μν λ¦¬μ€νΈλ₯Ό μ°Ύμ!

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
                  <BookNow>π« μλ§€νκΈ°</BookNow>
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
  - 1μ°¨ νλ‘μ νΈ λ, μλ¦¬μ‘ νλ μ½λκ° μ΄μ   λͺννκ² μ΄ν΄κ° λλ€!
- `<StyledLink key={index} to={`/times/${list.id}`}>`
  - λ°μμ€λ λ°μ΄ν°μ μν `id`μ `const params = useParams()` μ½λ!
- `SearchList`μμ λ§μ°μ€κ° λ λλ€λ©΄, ν΄λΉ divλ₯Ό μ¬λΌμ§κ² νκΈ°
  - [μ΄μ] μΆμ² κ²μ list divμ λ§μ°μ€κ° μ€λ² λλ©΄ SearchListκ° μ¬λΌμ‘λ€.

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
        κ²μ
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

- `SearchList`μμ λ§μ°μ€κ° λ λλ€λ©΄, ν΄λΉ divλ₯Ό μ¬λΌμ§κ² νκΈ°
  - [ν΄κ²°] stateλ‘ μΈνκ°μ λ³ννμ§λ§, μ΄λ ν κ°μΌλ‘ λ°λλμ§ μ νν μ λ¬ νμ§ μμμ.
  - μλμ κ°κ³Ό μ‘°κ±΄μ μ£Όμ΄ λ λλ§ νκΈ°
  ```jsx
  if (e.target.value.length > 0) {
    setShowList(true);
  } else {
    setShowList(false);
  }
  ```
  - λ°, μ¬κ΅μλ μ  μ¬λ¦½λλ€πββοΈ
    - μΌλ₯Έ μ½νλ¦¬κ°μμ λ²μ΄λμ λμμ μ£Όλ κ°λ°μ§±μ΄ λκ² μ΅λλ€.

### π³ μ±μ₯ ν¬μΈνΈ

- `useParams`λ₯Ό μ¬μ©ν filter κΈ°λ₯μμ λ§ν¬ μ°κ²°
- κ°λ¨ν΄ λ³΄μ΄μ§λ§ κ΅¬νμ κ·Έλ μ§ μμ μν κ²μ κΈ°λ₯
- νλ‘ μμ±νκ³  λ°©λ²μ μ°Ύμλ΄κ³  κ΅¬νν΄λ΄λ μ½λλ€μ΄ λμ΄λκ³  μλ€ ππ

## <p align="center"> `CGW` π 12/9 `The last day!`

Big day

### 2μ£Όκ°μ νλ‘μ νΈ νκ³ νκΈ° : λμ λν νκ³ 

> <a href="https://www.marimba.team/kr/blog/top-retrospective-templates/">π μ μμΌ νκ³ (Agile Retrospective)λ₯Ό μν ννλ¦Ώ μΆμ²</a>

## 1οΈβ£ Continue β Stop β Start

- νμ΄ μ§μν΄μ μ μ§ν΄μΌ ν  κ², κ·Έλ§ λμ΄μΌν  κ², κ·Έλ¦¬κ³  μλ‘­κ² μμν΄λ³΄μμΌ ν  κ² μ΄λ κ² μΈ κ°μ§ ν­λͺ©μΌλ‘ νκ³ λ₯Ό κ΅¬μ±νμ¬ μ§νν΄λ³΄μΈμ.
- νμλ€λ‘λΆν° λ λμ νμ λ§λ€κΈ° μν μλ‘μ΄ μ μ, κ°μ μ  λ±μ μ΄λμ΄λ΄κΈ° μμ£Ό μ’μ λ°©λ²μ΄ λ  κ±°μμπ

## 2οΈβ£ 4L: Liked, Learned, Lacked, Longed for

- π μ’μλ κ²(`L`iked)
- π λ°°μ΄ κ²(`L`earned)
- π¦ λΆμ‘±νλ κ²(`L`acked)
- π― λ°λΌλ κ²(`L`onged for)
  - μ€λ‘μ§ λ΄κ° μννλ μΌμλ§ μ§μ€ν΄μ μμ§νκ² μ λ¦¬ν΄λ³΄μΈμ!

## 3οΈβ£ KPT (Keep β Problem β Try)

- μ§μν  κ²(Keep), ν΄κ²°ν  κ²(Problem), μλν  κ²(Try)!
- μ§λ νλ‘μ νΈλ₯Ό λλμλ³΄λ©° μΈ κ°μ§λ‘ λλ  μ λ¦¬νκ³  ν¨κ» λμ§μ΄λ΄λλ€.
- β€οΈ μ§μν  κ² (Keep)
  - μ’μλ μ μ κΈ°λ°μΌλ‘ μμΌλ‘ νλ‘μ νΈλ₯Ό μ§νν  λ κ³μ μ μ§ν΄μΌ ν  μ¬ν­!
  - μν λΆλΆμλ μΉ­μ°¬κ³Ό λ°μ λ§κ΅¬λ§κ΅¬ λ³΄λ΄μ£ΌκΈ°, μμ§ λ§μΈμ.
- π§ ν΄κ²°ν  κ² (Problem)
  - μμ¬μ λ μ μ κΈ°λ°μΌλ‘ μμΌλ‘ νλ‘μ νΈλ₯Ό μ§νν  λ κ°μ λμ΄μΌ ν  μ¬ν­!
  - λ¨μν μΌμ΄λ μ¬κ±΄λΏλ§ μλλΌ μ¬κ±΄μ μ΄λ₯΄κΈ°κΉμ§μ κ³Όμ μ λλλ κ² μ’μμ.
- π μλν  κ² (Try)
  - μμ μ΄μΌκΈ°ν ν΄κ²°ν  λ¬Έμ λ€μ μμΈμ νμνμ¬ μμΌλ‘ μλν΄λ³Ό λ§ν μ¬ν­!
  - νκ³  μ΄ν μ‘μ μμ΄νμ κ΅¬μ²΄ννλ κ²μ΄ ν¬μΈνΈμλλ€.

## 1οΈβ£ Continue β Stop β Start

- `Continue` : λμ μλ λμ , μλ¬μ°½ λ§λκ³  μ€μ€λ‘ ν΄κ²° νκΈ°, TILμ λ κΌΌκΌΌν μμ±νκΈ°
- `Stop` : μ²μλΆν° μλ²½ν μ½λλ₯Ό κΈ°λνλ κ², μ€μ€λ‘μκ² μμ°μ€ μ€νΈλ μ€λ₯Ό μ€λ€
- `Start` : λ°±μλμ ν΅μ μ μνμ¬ `ERD` μμ±λ²κ³Ό μ½λ λ² κ³΅λΆ

## 2οΈβ£ 4L: Liked, Learned, Lacked, Longed for

- π μ’μλ κ²(`L`iked)
  - λ λ ν λκΈ°λ€κ³Ό ν¨κ» μμ±νλ μ½λ
  - μ΄λ ΅μ§λ§ 1μ°¨ νλ‘μ νΈ λ λ³΄λ€ μ¬ν λ λ λ²¨μ νλ‘μ νΈ (νν°λ§& λμ λΌμ°ν)
  - λ§€μΌ μμΉ¨ μ κ°, νμλ€μ΄ λ―Έλ¦¬ μμ±ν μ€ν λμ ννλ¦Ώμ κΈ°λ°μΌλ‘ λ°μΌλ¦¬ μ€ν λμμ μ§ν ν κ²
  - μ μμΌ κ°λ°μ μν νΈλ λ‘ μ¬μ© λ° νμ©
- π λ°°μ΄ κ²(`L`earned)
  - λ§μ΄ λμ΄μ§κ³  μλ¬μ°½μ λ§λκ³  ν΄κ²°νλ©΄μ μ±μ₯νλ€.
  - μ½λ λ¦¬ν©ν λ§μ ν΅νμ¬ λ μ’μ μ½λλ μμ μ΄ λμ΄λ λ¬Ό νλ₯΄λ―μ΄ μμ°μ€λ½κ² μλνλ κ²
- π¦ λΆμ‘±νλ κ²(`L`acked)
  - μλ¬ λμ²λ²μ΄ μμ§ λ―Έμνκ³ , console.logλ₯Ό νμ©ν λλ²κΉ μλ ¨λκ° λ?μ
  - λλ° μν©(e.g. μ λ¬ν΄μΌν  λ°μ΄ν° νμμ΄ λ°λμ΄μΌνλ€κ±°λ λλ κ·Έ λ°λμ κ²½μ°)μμ λΈλ½μ»€λ₯Ό λ§μ΄ λ§λ¬λ€.
  - μλ₯Ό λ€λ©΄, λ΄κ° λ°μ΄ν° νμμ μ μ²΄νλλ° λ§μ λ¦¬μμ€κ° λ€κ³  λΉν¨μ¨ μ μ΄λΌλ νλ¨μ΄ λ΄λ €μ§λ€λ©΄, λ°±μλμ λ°μ΄ν° λ³κ²½μ μμ²­ν΄λ λλ€λ μ 
  - μ²μμ΄κ³ , κΈ°ν λ¨κ³μμ μλ²½νλ€ μκ°ν λΆλΆμμλ λ³μκ° λ μκ²ΌκΈ°μ μμλ‘ λΌμν΄λ³΄κ³  λ³μμ νλ€λ¦¬μ§ μλ λ§μκ°μ§
    - > μ κ° μ΄λ ΅λ€κ³  μκ°νλ λΆλΆμ λͺ¨λκ° μ΄λ €μ΄ κ²μ΄ λ§κ³ , κ³ λ―Όμ΄ κΉμ΄μ§ λλ©΄ νμμ΄λ  λ©ν λκ³Ό μκ²¬μ λλ λ³΄λκ²λ λ°©λ²μ΄λΌλ κ²μ λ°°μ μ΅λλ€. μ΄κ±΄ μ¬λ¬λΆκ³Ό κ³΅μ νλ©΄ μ’μ κ² κ°μ μμ±ν©λλ€..
      > μ¦ νΌμ κΉκ² κ³ λ―Όνκ³  μμ§ λ§κΈ°! 12/7 μ€ν λμ λ―Έν -λ-
- π― λ°λΌλ κ²(`L`onged for)
  - κΈ°μ‘΄ μ¬μ΄νΈμ λ³΅μ‘ν UIλ₯Ό κ°μ νμ¬ μ¬μ©μμκ² μλ§€λ₯Ό μ§κ΄ν νμ¬ μλ§€λ₯Ό μ½κ² νλ κ²
  - μλ¬λ λ¬Έμ μμ΄ μ λμκ°λ μλ§€μ¬μ΄νΈ π₯

## π ν νκ³ ! `Agile Retrospective`

### β¨ νμ νκ³  μμ½:

- π μ’μλ κ²(`L`iked)
  - μ²΄κ³μ μΈ Standing-up meeting `Every weekday at 10am`
    - νμλ‘ μ  μμ±
    - λ§€μΌ μ€μ  10μ μ½ 10λΆ λ΄μΈ
  - μ€μκ΄λ¦¬ μ²΄μ 
    - `Notion`
    - `Trello`
  - νλ ₯ π€
    - `Blocker`ν΄μλ₯Ό μν΄ λͺ¨λ  νμλ€μ΄ νμνλ€
- π λ°°μ΄ κ²(`L`earned)
  - `FE` `BE` μνΈ μν΅ λ°©μ (λ°μ΄ν° μ λ¬)
  - `FE`: μλ°μ€ν¬λ¦½νΈ κ΅¬νμ μ΄λ €μ
  - `BE`: μ¬λκΉμ `ERD` νμ΅
- π¦ λΆμ‘±νλ κ²(`L`acked)
  - `FE` `BE` μνΈ μν΅, λ°μ΄ν° μ‘μμ 
    - μνν μν΅μ μνμ¬ `BE`λ `FE` μμμ, `FE`λ `BE` μμμ μ΄ν΄κ° νμνλ€
- π― λ°λΌλ κ²(`L`onged for)
  - μ΄κΈ° κΈ°νλ¨κ³μμ λ°μ΄ν° μ‘μμ  λ°©μμ λ κΌΌκΌΌν κΈ°ν
    - e.g. μΈμ  μ΄λ λ°μ΄ν°λ₯Ό μ£Όκ³  λ°κ³ , μ΄λ ν λ°μ΄ν° νμμΌλ‘ μ λ¬ λ°μμ§

### π ν μ€ μ λ¦¬

- νλμ κΈ°λ₯μ λͺ°μνλ νλ‘μ νΈμμ΅λλ€. μ΄μ  μμ±νμ§ λͺ»νλ μ½λλ₯Ό μ€λμ μ§μ  μμ±ν΄λ³΄κ³  μλ¬λ₯Ό ν΄κ²°νλ λͺ¨μ΅μμ νλ£¨νλ£¨ λΉ λ₯΄κ² μ±μ₯νκ³  μμμ λ°°μ μ΅λλ€. μ¬μ©μμ νλ©΄μ λμΈ UIμ κΈ°λ₯μ λμ΄, λ°±μ€λ μν΅νλ©° λ°μ΄ν°λ₯Ό κ°κ³΅νκ³  λ λ νλ κ°μΉλ₯Ό μκ² λμμ΅λλ€. λ¨μν κΈ°νμλ‘λ§ μ§ννλ κ²μ΄ μλλΌ `μ μ΄λ° κΈ°λ₯μ μ΄λ κ² κ΅¬ννμκΉ?` `μ μ΄λ° κΈ°λ₯μ μμκΉ?` κ°μ νλ‘λνΈ μ κ·Όμ μ§ννμ΅λλ€.

- μΌμ  κ΄λ¦¬ λΆλΆμλ λ§μ μ κ²½μ μΌμ΅λλ€. μλ‘μ μ λ’°μ ν¨μ¨μ μΈ λ¦¬μμ€ λΆλ°°λ₯Ό μνμ¬ `agile` λ°©μμ μ ννμμ΅λλ€. λ§€μΌ μ€μ  10μ, μ€ν λμ λ―Ένμ μ§ννλ©° λΈλ‘μ»€λ₯Ό ν¨κ» ν΄κ²°νκ³  κ³ λ―Όνλ μκ°μ κ°μ‘μ΅λλ€. λ§€μ£Ό κΈμμΌμ νκ³  μκ°μ κ°μ§λ©° μ°λ¦¬ νμμ νμν κΈ°λ₯, λΆνμν κ²μ κ΄νμ¬ μ΄μΌκΈ°λ₯Ό λλ΄μ΅λλ€.

- λ°μΌλ¦¬ μ€ν λ μ λ―Ένμ μ§κ°μ μμ΄ λ§€μΌ μ μμ μ§ννκ³ , λ°μΌλ¦¬λ―Ένμ΄ λμμ΄ λμλ€κ³  λ§ν΄μ£Όλ νμλ€μ΄ μμ΄ μ κ²½ μ΄ λ§νΌ λ³΄λ΅λ°λ κΈ°λΆμλλ€. μμΌλ‘ λ μ’μ ννλ¦Ώμ΄λ λ―Έν λ°©μμ΄ μλ€λ©΄ μ μ©ν΄λ³΄κ³  ν¨μ¨μ μΈ κ°λ°μ μ΄λκ³  μΆμ΅λλ€.

---

<p align="center">E.O.D
