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
