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
