# <p align="center">π Code test

<p align="center"> π 2022.Oct.28 | 1h<br>

## Q.1

```jsx
μ§μμΈμ§ νλ³νλ ν¨μ isEvenμ μμ±

console.log(isEven(11)) // --> "μ§μκ° μλλλ€."
console.log(isEven(10)) // --> "μ§μ μλλ€."
```

```jsx
function isEven(num) {
  // μλ μ½λλ₯Ό μλ ₯ν΄μ£ΌμΈμ.
  return num % 2 ? "μ§μκ° μλλλ€." : "μ§μ μλλ€.";
}
```

<hr>

## Q.2

```jsx
function calculateTotal(amount) {
  let totalAmount = amount + amount * 0.095 + amount * 0.15;
  return totalAmount;
}

console.log(calculateTotal(30));
```

```jsx
//μ€λ₯λ΅μ
function calculateTotal(amount) {
  let totalAmount = amount + amount(amount * 0.095) + amount(amount * 0.15);
  //amount(arg)λ₯Ό μ½μμ ν¨μκ° μλλΌλ μ€λ₯κ° λΈ!
  //λΉμ°ν¨

  return totalAmount;
}

console.log(calculateTotal(30));
```

<hr>

## Q.3 βββ

- `slice` λ κ°λ₯!

```jsx
function getPrefix(str) {
  // μλ μ½λλ₯Ό μμ±νμΈμ.
  return str.split("-")[0];
}
console.log(getPrefix("BTC-KRW"));
```

`split`μ λν μ΄ν΄κ° νμ [[see more]](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/split)

```jsx
//1μ°¨ μ½λ
const words = str.split("-");
// μ μΈν  νμκ° μμλλ° MDN νμΌλ³΄κ³  ν·κ°λ Έλ€
// μ μ°ν μ¬κ³ κ° νμνλ€
```

<hr>

## Q.4

```jsx
//2μ°¨ μ½λ
//else νμ μ λ¬΄λ₯Ό μμλ³΄μ
function getFind(filter, sentence) {
  for (let i = 0; i < sentence.length; i++) {
    if (sentence[i] === filter) {
      return i;
    }
  }
  return -1;
}
```

```jsx
// 1μ°¨ νΌλμ€λ¬μ
function getFind(filter, sentence) {
 for (let i = 0; i <sentence.length; i++){
   if ( sentence[i] === filter ){
     return sentence[i]
   } else{
     return -1
   }
 }
```

<hr>

> `getFind`Β ν¨μλ₯Ό μμ±νμΈμ.
>
> λ¬Έμμ λ¬Έμμ΄μ΄ μ£Όμ΄μ‘μλ,Β `getFind`Β ν¨μλ μ£Όμ΄μ§ λ¬Έμμ΄μμ μ£Όμ΄μ§ λ¬Έμκ° λνλλ μ²«λ²μ§Έ μμΉλ₯Ό λ°νν©λλ€.
>
> **Notes:**Β λ¬Έμμ΄μ μ²«λ²μ§Έ λ¬Έμλ μΈλ±μ€ κ°Β `0`Β μ κ°μ§λλ€. λ§μ½ λ¬Έμμ΄μ ν΄λΉ λ¬Έμκ° μ¬λ¬λ² λνλλ©΄, μ²«λ²μ§Έλ‘ λνλλ μμΉλ₯Ό λ°νν΄μΌ ν©λλ€. λ§μ½ λ¬Έμκ° λ¬Έμμ΄μ μ‘΄μ¬νμ§ μλλ€λ©΄,Β `-1`Β μ λ°νν΄μΌ ν©λλ€.
>
> **μ€μ!!**Β `indexOf`Β ν¨μλ₯Ό μ¬μ©νμ§ λ§μΈμ.
>
> ```jsx
> const output = getFind("a", "I am a hacker");
> console.log(output); // --> 2
> ```

- λκΈ° SYλμ μΉμ ν μ€λͺμΌλ‘ μ΄ν΄ μλ£ β

```jsx
function get_find(filter, sentence) {
  return sentence.search(filter);
}

console.log(get_find("b", "apple")); //-1
console.log(get_find("a", "apple")); //0
```

## Q.5 ββββ

pseudo code

β¨Β κ°μ₯ κΈ΄ κΈΈμ΄ λ°°μ΄μ μ λ°°μ΄μ λ΄λλ€

1.  λ°°μ΄μ κΈΈμ΄λ§νΌ λ°°μ΄μ μν νλ€
2.  i λ§νΌ κ° λ°°μ΄μ κΈΈμ΄λ₯Ό λΉκ΅νλ€
3.  μμ κ°μ₯ κΈ΄ κΈΈμ΄ λ°°μ΄μ i κ°μ λ΄λλ€ π

```jsx
find_longest_word ν¨μλ₯Ό λ§λ€μ΄ μ£ΌμΈμ.

μ£Όμ΄μ§ λ¦¬μ€νΈμμ μλ λ¨μ΄μ€ κ°μ₯ κΈ΄ λ¨μ΄λ₯Ό μ°Ύμμ μλλ‘ ν¨μλ₯Ό μμ±ν΄μ£ΌμΈμ.

console.log(find_longest_word(["PHP", "Exercises", "Backend"]))
// --> "Exercises"
```

```jsx
function find_longest_word(arr) {
  let longest = arr[0]
  // longest arrλ 0λΆν° μμν©λλ€!

  for (let i = 0; i< arr.length; i++){
   β¨ if (arr[i].length > longest.length){
    //i.lengthκ° μλ!
	 β¨	longest = arr[i]
    }
  } return longest;
}
```

- if (arr[i].length > longest.length)

<hr>

π³ Learning Point :

- Prep-study
- μΌν­μ°μ°μ μλ²½μ΄ν΄
- split λμμλ¦¬ μ΄ν΄
- μμμ½λ β λ°μ λ μ½λ
- pseudocode code β¨

<hr>
E.O.D
