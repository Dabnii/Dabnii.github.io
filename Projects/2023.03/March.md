## <p align="center"> 📆 3/4

### 🕹️ Tic Tac Toe | Grid + styled-components

```jsx
const MainContainer = styled.div`
  width: 100vw;
  height: 100vh;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(17rem, 1fr));
  gap: 0px;
  overflow: hidden;
  justify-content: center;
  align-items: center;
`;
```

## <p align="center"> 📆 3/5

### 🕹️ Tic Tac Toe

![render X!](https://user-images.githubusercontent.com/110847597/222921514-73fbbc86-0b19-418e-b67b-9724ccdd3d4b.gif)

```jsx
function Game() {
  const [markX, setMarkX] = useState(Array(GameRow.length).fill(''));

  const handleClick = index => {
    const newMarkX = [...markX];
    newMarkX[index] = 'x';
    setMarkX(newMarkX);
  };

  return (
    <GameContainer>
      <Board>
        {GameRow.map((item, index) => (
          <Square value={index} key={index} onClick={() => handleClick(index)}>
            {markX[index] === 'x' && 'x'}
          </Square>
        ))}
      </Board>
      <Score />
    </GameContainer>
  );
}
```

## <p align="center"> 📆 3/6

### `X`&`O` 를 이미지로 변경하기

![x0](https://user-images.githubusercontent.com/110847597/223368408-777dd87f-4a07-4768-8814-7d699e084b7d.gif)

> 못생긴 x,o 탈출

```jsx
{
  board.map((item, index) => (
    <Square value={index} key={index} onClick={() => changePlayer(index)}>
      {item === 'X' && <X src='/images/X.png' alt='X' />}
      {item === 'O' && <O src='/images/Ellipse.png' alt='O' />}
    </Square>
  ));
}
```

### ⏹️ `aspect-ratio: 1 / 1`

> The aspect-ratio CSS property sets a preferred aspect ratio for the box, which will be used in the calculation of auto sizes and some other layout functions.

#### ⏹️ 정사각형 만들기

1. `width`, `height` 값을 동일하게 설정
2. `aspect-ratio: 1 / 1`로 정사각형 생성
3. variable, style 설정으로 생성 가능

```scss
.box {
  height: 600px;
  aspect-ratio: 1 / 1;
}
```

출처:

- https://developer.mozilla.org/en-US/docs/Web/CSS/aspect-ratio

## <p align="center"> 📆 3/7

### 🏗️ Refactor `score.js`

#### ✨ `styled-components props`

```jsx
//after
  const isWinner = score !== null;
  const isXPlayer = xPlayer && !isWinner;
  const isOPlayer = !xPlayer && !isWinner;

  return (
    <ScoreContainer>
      <PlayerInfo>
        {isWinner ? (
          <Winner>
            <Trophy>🏆</Trophy>
            <PlayerImg
              src={score === 'X' ? '/images/X.png' : '/images/Ellipse.png'}
              alt={score}
            />
            <Status>Winner!</Status>
          </Winner>
        ) : (
          <>
            <PlayerImg src='/images/X.png' alt='X' show={isXPlayer} />
            <PlayerImg src='/images/Ellipse.png' alt='O' show={isOPlayer} />
            <Status>{isXPlayer ? 'Turn' : 'Turn'}</Status>
          </>
        )}
      </PlayerInfo>
    <ScoreContainer>
  )
```

```jsx
const PlayerImg = styled.img`
  width: auto;
  height: 108px;
  background-color: transparent;
  display: ${({ show }) => (show ? 'block' : 'none')};
`;
```

- `isXPlayer` , `isOPlayer` 있다면 PlayerImg display의 show로 display
- `styled-components`의 props를 사용

## <p align="center"> 📆 3/8

### 🍀 Re-load!

```javascript
location.reload();
```

```jsx
const handleRefreshClick = () => {
  window.location.reload();
};
```

> Location.reload() 메서드는 새로고침 버튼처럼 현재 리소스를 다시 불러옵니다.

출처:

- [📎 location.reload MDN](https://developer.mozilla.org/ko/docs/Web/API/Location/reload)

### 💡 Prevent click

```jsx
const changePlayer = index => {
  if (board[index] !== null || isWinner) {
    return;
  }
};
```

1. grid가 이미 클릭 되었거나 || 승자가 정해졌다면 → `아무런 행동을 하지 않음`

## <p align="center"> 📆 3/9

### 🤜 무승부! `every`

```jsx
const isTie = board.every(el => el !== null);
```

- `every()` 메서드는 배열 안의 모든 요소가 주어진 판별 함수를 통과하는지 테스트합니다. `Boolean 값을 반환`합니다.

---

출처:

- [📎 every MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/every)

## <p align="center"> 📆 3/11

### `hasOwnProperty`

- `hasOwnProperty()` 메소드는 객체가 특정 프로퍼티를 가지고 있는지를 나타내는 불리언 값을 반환한다.

```javascript
obj.hasOwnProperty(prop);
```

```javascript
const object1 = {};
object1.property1 = 42;

console.log(object1.hasOwnProperty('property1'));
// Expected output: true
```

## <p align="center"> 📆 3/21

### 🚨 Too many re-renders!

![Error](https://user-images.githubusercontent.com/110847597/226533984-15dbea2c-c167-4269-be2a-ed00ca6763bf.png)

> 매번 함수가 실행 되면서 많은 리 렌더링을 야기하는 오류.
> UseEffect를 사용하여 페이지가 마운트 될 때 마다 렌더링 하도록 수정!

```javascript
const [xWin, setXWin] = useState(0);
const [oWin, setOWin] = useState(0);

const winData = ['X', 'O', 'X', 'X', 'X'];

const countWinner = winData => {
  for (let i = 0; i < winData.length; i++) {
    if (winData[i] === 'X') {
      setXWin(prev => prev + 1);
    } else if (winData[i] === 'O') {
      setOWin(prev => prev + 1);
    }
  }
};

✨

useEffect(() => {
  countWinner(winData);
}, []);

//countWinner(winData);
//이렇게 쓰면 안된다.

```

---

## <p align="center"> 📆 3/27

<img width="900" alt="스크린샷 2023-03-27 오후 4 06 42" src="https://user-images.githubusercontent.com/110847597/227865984-0a4719c3-28a5-4f5b-b3bb-71162bf60e42.png">

## 💬 New game error

### 🚨 problem

1. 첫 게임이 끝난 후 모달창을 닫는다
2. 두번째 게임을 진행 하면 모달창(게임결과)이 뜨지 않는다.

### ✅ Solution

```javascript

```

---

## 💬 Score error

### 🚨 problem

1. `1+`씩 증가해야하는 점수가 불규칙적으로 증가한다
   ![scoreError](https://user-images.githubusercontent.com/110847597/227870301-1bbabd0a-7c06-4683-ad79-42d1c3497e24.gif)
   <img width="653" alt="scoreError2" src="https://user-images.githubusercontent.com/110847597/227870257-a9d9f9c4-722b-4868-aab6-a294c9d34f94.png">

### ✅ Solution

```javascript

```
