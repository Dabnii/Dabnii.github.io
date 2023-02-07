## <p align="center"> 📆 2/5

## 🖼️ [Toy-project] Data create & delete program

- 데이터 태그 생성 기능
- 데이터 삭제 & 저장 기능

## 🖼️ Input placeholder가 없어지지 않는다!

> 인풋박스에 숫자를 입력하도록 유도하고 싶었으나, placeholder가 사라지지 않았다.

![Label + input](https://user-images.githubusercontent.com/110847597/217237776-d438652b-3466-44a0-9d04-e9a947d96282.gif)

#### ❕ `Label`로 해결

> 이전에 프로젝트 할 때, button과 radio 박스위에 label을 사용했던 점을 착안

1. label을 `on`
2. 인풋박스에 `onMouseEnter`될 때 `false`로 감춘다
3. displaypencil이 `OFF`라면 input 박스 보이기

### 📌 `htmlFor="(input id)"`

- 라디오 박스처럼 label이 대신 클릭되길 바란다면 React에선 htmlFor의 값을 해당하는 라디오박스 id와 일치하게 해주면 된다.

```jsx
const [displayPencil, setDisplayPencil] = useState(true);
//...
{
  displayPencil ? (
    <label htmlFor="numInput" onMouseEnter={() => setDisplayPencil(false)} />
  ) : (
    <>
      <input
        id="numInput"
        type="number"
        placeholder={0}
        step={1}
        min={0}
        max={possibleMax}
        onChange={handleInputChange}
        value={inputValue}
        onKeyDown={onReset}
        onBlur={onReset}
      />
      <div className="btnContainer">
        <button className="increase" onClick={() => onIncrease()}>
          +
        </button>
        <button className="decrease" onClick={() => onDecrease()}>
          -
        </button>
      </div>
    </>
  );
}
```

```scss
label {
  height: 50%;
  width: 50%;
  border-bottom: 2px solid black;
  padding-right: 20px;
  background-image: url("../../../public/image/pencil.svg");
  background-repeat: no-repeat;
  background-position: center;
  //시맨틱태그를 사용할 필요가 없어, background img를 사용
}

input[type="number"] {
  -webkit-appearance: textfield;
  -moz-appearance: textfield;
  appearance: textfield;
  animation: fadeOut 0.2s ease-in-out;
  text-align: right;
  border: none;
  width: 8rem;
  padding: 15px;
  background-color: transparent;
  font-family: inherit;
  font-size: 2rem;
  font-weight: 700;
  position: relative;
  -webkit-appearance: none;

  &::-webkit-inner-spin-button,
  &::-webkit-outer-spin-button {
    opacity: 0;
    // 1 이라면 항상 on
    // 0 이라면 off
    -webkit-appearance: none;
  }

  &:focus {
    outline: none;
    //못생긴 outline 삭제
  }
}
```

- `Boolean`으로 state를 관리

## 🖼️ Input min의 배신

- 예상 로직대로라면 `input min` 속성을 사용하여 `0`이상의 정수만 허용
- But, `min={0}` 이하 음수도 작성이 되어서 아래의 로직 추가
- `+` 범위 밖 값이면 팝업창 띄우기!

  ![popup](https://user-images.githubusercontent.com/110847597/217245839-add16c17-e34f-4712-9b0c-0ef45e22a39a.gif)

```jsx
const handleInputChange = e => {
  const input = Math.floor(e.target.value);

  if (input <= 0 || input > possibleMax) {
    setHandleWarning(true);
    setTimeout(() => setHandleWarning(false), 2000);
    return;
  }
  setInputValue(input);
  setDisplayPencil(false);
  setTimeout(() => getAutoDelData(inputValue), 0);
};
//
<input
  id="numInput"
  type="number"
  placeholder={0}
  step={1}
  min={0}
  max={possibleMax}
  onChange={handleInputChange}
  value={inputValue}
  onKeyDown={onReset}
  onBlur={onReset}
/>;
```

<details>
<summary>리팩토링 전 코드</summary>

```jsx
const onDecrease = () => {
  if (inputValue <= 0) {
    setInputValue(0);
  } else {
    setInputValue(prevNum => prevNum - 1);
  }
};
```

- 삼항연산자를 활용하지 못한 러프한 코드

```jsx
  const onDecrease = () => {
    setInputValue(prevNum => {
      return Number(prevNum - 1) >= 0 ? Number(prevNum - 1) : 0;
    });
    getAutoDelData(inputValue);
```

- 삼항연산자를 활용한 코드 ✨
</details>

### 🔍 돌아가는 코드도 다시보자!

![closeSHot](https://user-images.githubusercontent.com/110847597/217237782-d558300a-dd9d-4029-bd75-b2c52dfc64ac.gif)

> 0일때 연산하지 않는 문제점을 발견했다.
> 확인해 보니 숫자가 아닌 `string`으로 들어오고 있었다.
> `Number()` 사용으로 숫자로 변환완료

```jsx
//before
const onIncrease = () => {
  setInputValue(prevNum => {
    return prevNum + 1 <= possibleMax ? prevNum + 1 : prevNum;
  });
  getAutoDelData(inputValue);
};

//after
const onIncrease = () => {
  setInputValue(prevNum => {
    return prevNum + 1 <= possibleMax ? Number(prevNum + 1) : Number(prevNum);
  });
  getAutoDelData(inputValue);
};
```

### 🤓 가독성 좋은 코드를 쓰자

```jsx
//After ✨
function KeepDataComponent({ getAutoDelValue, getData }) {
  const total = getData.length;
  const keep = Number(total - getAutoDelValue);

  return <div>...</div>;
}

//before 😖
function KeepDataComponent({ getAutoDelValue, getData }) {
  const calculateData = getData.length - getAutoDelValue;

  return <div>...</div>;
}
```

- 한 줄이라고 다 좋은 코드는 아니다.

## <p align="center"> 📆 2/7

### 😖 useState의 동기
