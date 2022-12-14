# <p align="center"> π data type

## π‘ Primitive types

- number
- string
- boolean
- null
- undefined
- SymbolΒ (ECMAScript 6 μ μΆκ°)
  - βοΈ λ³λλ‘Β Object(κ°μ²΄)

## typeof μ°μ°μ

- `typeof`Β μ°μ°μλ₯Ό ν΅ν΄ μ΄ κ°, μ΄ λ³μλ λ¬΄μ¨ λ°μ΄ν° νμμΈμ§ μ μ μμ΅λλ€.
- `typeof`Β μ°μ°μλ₯Ό μ μ©νλ©΄ λ€μ λ¬Έμμ΄ μ€ νλλ₯Ό λ°νν©λλ€.
  1. `undefined` : μ μλμ§ μμ λ³μ
  2. `boolean`
  3. `string`
  4. `number`
  5. `object"`: ν¨μλ₯Ό μ μΈν κ°μ²΄ λλ `object`
  6. `function`
- `typeof`Β μ°μ°μλ λ€μκ³Ό κ°μ΄ μ¬μ©ν©λλ€.

```javascript
let msg = "message";

console.log(typeof msg); // "string"
console.log(typeof 100); // "number"
```

## π typeof null

- `typeof null`Β βΒ `"object"`
- null μ΄λΌλ λ°μ΄ν° νμμ΄ `object` λ‘ λ°νλ©λλ€.
- null μΒ `λΉ κ°μ²΄λ₯Ό μ°Έμ‘°`νκ³  μμ΄μ κ·Έλ μ΅λλ€.

## π Array λ°μ΄ν° νμ

```
console.log(typeof [])
```

- λ°°μ΄μ typeμ νμΈν΄λ³΄λ©΄Β `"object"`μλλ€.
- μλνλ©΄Β `μ¬μ€ λ°°μ΄μ νμ₯λ κ°μ²΄` μλλ€.

## π’ Number (μ«μ)

- Number λΌλ λ°μ΄ν° νμμ μ«μλ₯Ό μλ―Έν©λλ€.
- Number νμμμ μ€μν κ²μΒ **μ°μ°**μλλ€.
- μ°μ  μ°μ°μλ₯Ό μ¬μ©νμ¬ Number νμμ λν μ°μ°μ μλμ κ°μ΄ μμ±ν©λλ€.

```
1 + 1 // λνκΈ°
2 - 1 // λΉΌκΈ°
2 * 4 // κ³±νκΈ°
6 / 2 // λλκΈ°
```

- λνκΈ°(+)λ μΌμͺ½ κ°κ³Ό μ€λ₯Έμͺ½ κ°μ λν΄μ νλμ κ°μ λ§λ λ€λ μ μμ `μ΄ν­ μ°μ°μ` λΌκ³  λΆλ¦λλ€.
- μ΄ν­ μ°μ°μ μ€μμ μ°μλ₯Ό νλ κ²μ΄κΈ° λλ¬ΈμΒ `μ°μ  μ°μ°μ`λΌκ³  λΆλ¦λλ€.

## π€ String (λ¬Έμμ΄)

- Strings are another primitave type in JavaScrip. They represent text, and must be wrapped in quotes.
- `ββ` or `ββ` ν­μ μμΌλ‘ νμν©λλ€.
- μ°μ  μ°μ°μλ₯Ό ν΅ν΄ μ«μ λ°μ΄ν° νμμ νμ©νλ κ²μ²λΌ λ¬Έμμ΄ νμμλ λ€μν κΈ°λ₯μ΄ μμ΅λλ€.

```javascript
let userdame = "danny";
//username λ³μκ° λ¬Έμμ΄λ‘ μ€μ  λ¨
let firstName = "Zaggy"; // Double quotes work
let msg = "please do no feed the chimps!";
let anmimal = "Dumbo Octopus"; //so do single quotes //with quotes available use space
```

<hr>

### π¨ `String Methods` | κ³ μ ν κΈ°μ  [[see more]](https://developer.mozilla.org/ko/docs/Glossary/Method)

Methods are build-in actions we can perform with indiviusal strings

- Searching within a string
- Replacing part of a string
- Changing the casing of a string

### `()` κ΄νΈλ₯Ό μ¬μ©νμ¬ μ κ·Ό

```jsx
let msg = "I am king";
let yellMsg = msg.toUpperCase();

let angry = "LeAvE mE aLoNe!";
angry.toLowerCase();
```

## βοΈ `Trim`

### thing.method(arg)| μΈμκ° μλ λ¬Έμμ΄ κ·μΉ [[see more]](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

> Some methods accept arguments that modify their hebavior. Think of them as inputs that we can pass in. We pass these arguments inside of the parentheses.

- μΈμλ λ©μλλ‘ μ λ¬λμ΄μ λ©μλμ λμμ λ³κ²½νλ μλ ₯ κ°

```jsx
let tvShow = "catdog";

tvShow.indexOf("cat"); //0
tvShow.indexOF("dog"); //3
tvShow.indexOf("z"); //-1 (not found)
//μ€λ³΅λλ λ¬Έμκ° μμ΄λ μ΅μ΄μ μΈλ±μ€λ§ λΈμΆ
```

π‘ `str.length`

```javascript
// λ¬Έμμ΄ λ°μ΄ν° νμ λ³μ μ μΈ
let name = "wecode";

// .length >> λ¬Έμμ΄μ΄ λͺ κΈμλ‘ λμ΄ μλμ§ νμΈ
name.length; // 5

// .toUpperCase >> λ¬Έμμ΄μ λλ¬Έμλ‘ μΆλ ₯
name.toUpperCase(); // "WECODE"

// .indexOf >> νΉμ  νμ€νΈμ ν¬ν¨ μ λ¬΄ λ° μμΉ νμΈ
name.indexOf("c"); // 2
name.indexOf("j"); // -1
```
