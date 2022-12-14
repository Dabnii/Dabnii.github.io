## <p align="center"> `CGW` π 11/29

- `Stypled component` <a href="https://styled-components.com/">π κ³΅μλ¬Έμ</a>

### π Styled-Components

- <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.12/Dec1stWeek.md#-styled-components-%EC%95%BD-%EC%9D%BC%EC%A3%BC%EC%9D%BC-%ED%9B%84%EA%B8%B0">π `Styled-Components`μΌμ£ΌμΌ μ¬μ© νκΈ°</a>

- μ€μΉ

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

> μμ λ¨κ³  μλ CSS μ μ²λ¦¬κΈ°. <br>
> π λ΄κ° λλ μ₯μ : ν΄λμ€λͺμ μΌμΌν μ¨μ£Όμ§ μμμ μ’λ€ <br>
> π λ΄κ° λλ λ¨μ : μ½λκ° νλ§λμ₯κ²½μ΄ λλ€..<br>
> π λ΄κ° λλ λ¨μ  2: λ€μ€νμ μΆμ² νμ§ μλλ€. π ~~κ°λμ±~~

### π³ μ±μ₯ ν¬μΈνΈ:

- μλ‘μ΄ ν΄μΈ `Styled-Components` μ μκ°λ³΄λ€ μ μ μ μ€
- μ»΄ν¬λνΈλͺ (ν΄λμ€λͺ) μλͺμ μ€μμ±
- μλ‘μ΄ μ μ²λ¦¬κΈ°μ νμ΅μ μ¬λ―Έ π₯³
  - κ°λ°μλΌλ©΄ μλ‘μ΄ κ²μ λ μλνκ³  νμ΅μ ν΄μΌνλ€!

---

## <p align="center"> `CGW` π 11/30

### π `React calendar API` <a href="https://github.com/wojtekmaj/react-calendar">π λ°λ‘κ°κΈ°</a>

1. `install`

   ```jsx
   npm install react-calendar
   ```

2. `CSS import`

   ```jsx
   import "react-calendar/dist/Calendar.css";
   ```

3. `Basic usage` <a href="https://github.com/wojtekmaj/react-calendar#user-guide">π λͺμΈ λ°λ‘κ°κΈ°</a>

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

4. `calendar` μ»΄ν¬λνΈ

   ```jsx
   <Calendar className="calendar" onChange={changeDate} value={value} />
   ```

   - μ€ν κ²°κ³Ό,`value={value}`λ₯Ό μ­μ νλ©΄ ν°μ§λ€.π£

5. μμ κΈ°λ³Έ μΈνμ΄ λλ¬μΌλ©΄ μ€μ  μμ!

   ```jsx
   const [value, setValue] = useState(new Date());

   const changeDate = (e) => {
     setValue(e);
   };

   console.log(value.getDay());
   ```

   - μ»¨λ²€μμ λ§κ² stateμ μ΄λ¦μ μμ 
   - `value.getDay()` κ°μ νμΈν΄ λ΄λλ€.
   - `value.getYear()`
   - `value.getDate()`λ±λ± μνλ λ°μ΄ν°λ₯Ό νΈμΆν΄ μ°μ΄λ΄λλ€.

6. π CSS μμ νκΈ°
   1. π  κ°λ°μ λκ΅¬μμ `element`μ ν΄λμ€ λͺμ νμΈ
   2. μν¬νΈν `css`λ₯Ό μ§μ
   3. β¨ λμΌν ν΄λμ€ λͺμ λ³΅μ¬νμ¬, λμ `css`μμ μΆκ° + μμ 
   4. μλ³Έ cssλ₯Ό μμ  νμ§ μμ

### π `spread operator` <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax"> π μ κ° κ΅¬λ¬Έ</a>

- μ κ° κ΅¬λ¬Έμ λ°λ³΅ κ°λ₯ν κ°μ²΄ β¨ `iterable`μ μ μ©ν  μ μλ λ¬Έλ²
- λ°°μ΄μ΄λ λ¬Έμλ₯Ό νμ΄ `μμ νλνλλ‘ μ κ°` κ°λ₯!

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

### π³ μ±μ₯ ν¬μΈνΈ:

- μ κ°κ΅¬λ¬Έμ νμ΅
- `iterable`νμ΅
- calendar api νμ΅ π

---

<p align="center">E.O.D</a>
<p align="center"><a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md">μ§λμ£Ό TIL: 2022.Dec.TIL<a></p>
<p align="center"><a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.12/Dec1stWeek.md">λ€μμ£Ό TIL: 2022.Dec.TIL<a></p>
