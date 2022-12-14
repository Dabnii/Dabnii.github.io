# <p align="center"> π§’ React Props

## π§’ React Props

- μ»΄ν¬λνΈμ μμ±κ° Object
  - `λΆλͺ¨ μ»΄ν¬λνΈλ‘λΆν° μ λ¬ λ°μ λ°μ΄ν°`λ₯Ό μ§λκ³  μλ `κ°μ²΄`
- λͺ¨λ  νμμ λ°μ΄ν°μ ν¨μκΉμ§ μ΄λ€ κ°μ΄λ  μμ μ»΄ν¬λνΈμ μ λ¬ κ°λ₯
  - e.g. λ¬Έμ, μ«μ, λ³μ, ν¨μ λ±
- 2κ° μ΄μμ κ°μΌ λ `λμ΄μ°κΈ°λ‘` κ΅¬λΆ&μ λ¬
  - e.g.`<Child pet={animal} englishName='tiger' />`

### π‘ λΆλͺ¨ μ»΄ν¬λνΈμμμ λ°μ΄ν° μ λ¬

- `pet={animal}`κ³Ό κ°μ΄ μμ μ»΄ν¬λνΈμ μμ± κ°μ μΆκ°
- μ§μ  κ°μ ν λΉ`(βtigerβ)`ν΄μ λκ²¨μ€ μ μμ
- λͺ¨λ  λ°μ΄ν° νμμ λκ²¨μ€ μ μμ
- 2κ° μ΄μμ κ°μΌ λ `λμ΄μ°κΈ°λ‘` κ΅¬λΆ&μ λ¬

```javascript
// Parent.js(λΆλͺ¨ μ»΄ν¬λνΈ)

import React from "react";

const Parent = () => {
  const animal = "νΈλμ΄";

  return (
    <>
      <h1>λΆλͺ¨ μ»΄ν¬λνΈμλλ€.</h1>
      <p>{animal}</p>
    </>
  );
};

export default Parent;
```

### π‘ μμ μ»΄ν¬λνΈμμμ μ λ¬ λ°μ λ°μ΄ν° μ μ©

- ν¨μ μ»΄ν¬λνΈ λνΒ `const Child = (λ§€κ°λ³μ) β {}`Β μ κ°μ΄ λΆλͺ¨ μ»΄ν¬λνΈμμ λ³΄λ΄μ€ λ°μ΄ν°λ₯Ό λ°μμ μ¬μ©ν  μ μμ
- λΆλͺ¨ μ»΄ν¬λνΈκ° μ λ¬ν΄ μ€ propsλ `νλμ κ°μ²΄λ‘ ν©μ³μ Έμ ν¨μ μ»΄ν¬λνΈμ μ λ¬`
- λͺμμ μΌλ‘ λνλ΄κΈ° μν΄Β `const Child = (props) β {}`λΌκ³  λ§€κ°λ³μ μ΄λ¦μ μ§λ κ²μ΄ μ»¨λ²€μ

```javascript
// Child.js(μμ μ»΄ν¬λνΈ)

import React from "react";

const Child = (props) => {
  console.log(props); // {pet: 'νΈλμ΄', englishName: 'tiger'}

  return (
    <>
      <h2>μμ μ»΄ν¬λνΈμλλ€.</h2>
      <p>{props.pet}</p> // νΈλμ΄
      <p>{props.englishName}</p> // tiger
    </>
  );
};

export default Child;
```

### π‘ ν¨μ μ λ¬κ³Ό μ μ©

```javascript
import React from "react";
import Child from "./Child";

const Parent = () => {
  const testConsole = () => {
    console.log("νμ€νΈ μλλ€.");
  };

  return (
    <>
      <h1>λΆλͺ¨ μ»΄ν¬λνΈμλλ€.</h1>
      <button onClick={testConsole}>ν΄λ¦­</button>
      <Child test={testConsole} />
    </>
  );
};

export default Parent;
```

1.  λΆλͺ¨ μ»΄ν¬λνΈμμλΒ testConsoleμ΄λΌλ ν¨μλ₯Ό μ μΈ
2.  μ΄ ν¨μκ° λ²νΌμ ν΄λ¦­ν  λλ§λ€ μ€νλ  μ μλλ‘Β ν΄λ¦­ μ΄λ²€νΈ νΈλ€λ¬
3.  ν¨μλ₯Ό μμ μ»΄ν¬λνΈμμλ μ¬μ©ν΄μΌ νλ μν©
4.  `λΆλͺ¨ μ»΄ν¬λνΈ`μμλ μ λ¬νκ³ μ νλ testConsoleμ΄λΌλ ν¨μλ₯Ό `μ΄λ€ μ΄λ¦μΌλ‘ λκ²¨μ€μ§λ§ μ ν΄`μ£Όλ©΄ λ¨

```javascript
// Child.js (μμ μ»΄ν¬λνΈ)

import React from "react";

const Child = (props) => {
  console.log(props); // {test: () => {console.log('νμ€νΈ μλλ€.')}}

  return (
    <>
      <h2>μμ μ»΄ν¬λνΈμλλ€.</h2>
      <button onClick={props.test}>ν΄λ¦­</button>
    </>
  );
};

export default Child;
```

1. λΆλͺ¨ μ»΄ν¬λνΈμμλ μ λ¬νκ³ μ νλ ν¨μλ₯ΌΒ `testλΌλ κ·Έλ¦μ λ΄μ μ λ¬`
2. λΆλͺ¨ μ»΄ν¬λνΈμμ μ μΈλ ν¨μμ΄μ§λ§ `μμ μ»΄ν¬λνΈμμλ μ¬μ©ν  μ μμ`
3. `button νκ·Έμ ν΄λ¦­ μ΄λ²€νΈ νΈλ€λ¬`λ₯Ό κ±Έμ΄μ€
4. ν΄λΉ νκ·Έλ₯Ό ν΄λ¦­ν  λ λ§λ€ μ€νλλ ν¨μλ₯Ό `λΆλͺ¨λ‘λΆν° λ°μ test ν¨μλ‘ μ μ`
5. β¨ μ€μ λ‘ button νκ·Έκ° ν΄λ¦­λ  λλ§λ€ μ€νλλ ν¨μλ λΆλͺ¨ μ»΄ν¬λνΈμ μλ testConsoleμ΄λΌλ ν¨μκ°

### π― Props κΏν

- μ»΄ν¬λνΈλ³(js) λ³λ‘ κ΅¬λΆνλ κ²μ κΆμ₯

  - μ μ§ λ³΄μλ₯Ό μν¨
  - μ»΄ν¬λνΈμ μ μκ° μ¬νμ©μ΄ κ°λ₯ν UI μ₯μ  μ¬μ©

  <br>

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20Hook.md"> μ΄μ κΈ: React Hook </a>

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20State.md"> λ€μκΈ: React State </a>

<hr>
<p align="center"> E.O.D
