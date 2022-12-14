# <p align="center"> π  String ββ π’ Number

## Java Scriptμ data type μ λμ±
- λ°μ΄ν° νμμ μκ²©νμ§ μλ€.
- μ₯μ : λ€λ₯Έ μΈμ΄λ³΄λ€ νΈνκ³  μ½λ€ π
- λ¨μ : μ€λ₯ λ°μμ΄ μ½λ€ π€

<br>

## π  String β Number

### `typeof`
-  typeof μ°μ°μλ νΌμ°μ°μμ νκ° μ  μλ£νμ λνλ΄λ λ¬Έμμ΄μ λ°νν©λλ€.

    ```javascript
    console.log(typeof 42);
    // expected output: "number"

    console.log(typeof 'blubber');
    // expected output: "string"
    ```
    > https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/typeof

<br>

### π’ Function `Number()`
 - `Number()` μμ±μλ Number κ°μ²΄λ₯Ό μμ±ν©λλ€. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/Number">π see more</a> 

    ```javascript
        var birthYearInput = "2000";
        console.log(typeof birthYearInput);

        var numberBirthYear = Number(birthYearInput);
        console.log(typeof numberBirthYear);
    ```

### `parseInt`
- parseInt() ν¨μλ λ¬Έμμ΄ μΈμλ₯Ό νμ±νμ¬ νΉμ  μ§μ(μμ μ§λ² μ²΄κ³μμ κΈ°μ€μ΄ λλ κ°)μ μ μλ₯Ό λ°νν©λλ€.

### `parseFloat`
- parseFloat() ν¨μλ μ£Όμ΄μ§ κ°μ νμν κ²½μ° λ¬Έμμ΄λ‘ λ³νν ν λΆλμμμ  μ€μλ‘ νμ±ν΄ λ°νν©λλ€.

    ```javascript
        parseInt("1.901");
        parseFloat("1.901");
        Number("1.901");
        parseInt("200") + 1;
    ```

### β λΉΌκΈ° μ°μ°μ νΉμ± 
- λΉΌκΈ° μ°μ°μ νΉμ±μ μ¬μ©νμ¬ String β Number 

    ```javascript
        var numberAsNumber = "1234";
        var numberAsString = numberAsNumber - 0;


        console.log(numberAsNumber, typeof numberAsNumber);
        console.log(numberAsString, typeof numberAsString);
    ```

<hr>
<br>

## π’ Number β String

### `tostring()`
- The toString() μ λ¬Έμμ΄μ λ°ννλ objectμ λνμ μΈ λ°©λ²μ΄λ€

    ```javascript
        var numberAsNumber = 1234;
        var numberAsString = numberAsNumber.toString();

        console.log(numberAsNumber, typeof numberAsNumber);
        console.log(numberAsString, typeof numberAsString);
    ```

### β μ°μ°μ νΉμ±
- λΉΌκΈ° μ°μ°μ νΉμ±μ μ¬μ©νμ¬ Number β String

    ```javascript
        var numberAsNumber = 1234;
        var numberAsString = 1234 + "";

        console.log(numberAsNumber, typeof numberAsNumber);
        console.log(numberAsString, typeof numberAsString);
    ```




## π₯ String ββ Number test [1]

### nationalPensionRemainingYearCount ν¨μλ₯Ό κ΅¬νν΄μ£ΌμΈμ.

- μ°λ¦¬λλΌλ κ΅­λ―Όμ°κΈμ λ§ 65μΈ λΆν° λ°μ μ μμ΅λλ€.
- `nationalPensionRemainingYearCount`Β λΒ `age_string`Β μ΄λΌλ inputμ λ°μ΅λλ€.
- `age_string`Β μ λμ΄ κ°μΈλ° stringν κ°μΌλ‘ λμ΄ μμ΅λλ€.
- μ£Όμ΄μ§ λμ΄λΆν° λͺλμ΄ μ§λμΌ κ΅­λ―Όμ°κΈμ λ°μμ μλμ§ λ¦¬ν΄ ν΄μ£ΌμΈμ.
- λ¦¬ν΄ κ°μ λ€μκ³Ό κ°μ΅λλ€.
    
    ```javascript
    "μμΌλ‘ 20λ λ¨μΌμ¨μ΅λλ€"
    ```
    
- μλ₯Ό λ€μ΄,Β `age_string`Β κ°μ΄ λ€μκ³Ό κ°λ€λ©΄:
    
    ```javascript
    "35"
    ```
    
    λ¦¬ν΄ κ°μ λ€μκ³Ό κ°μμΌ ν©λλ€.
    
    ```javascript
    "μμΌλ‘ 30λ λ¨μΌμ¨μ΅λλ€"
    ```

    ```javascript
    function nationalPensionRemainingYearCount(age_string) {
    const numberAsString = age_string.toString();
    let yearLeft = 65 - numberAsString;
    return "μμΌλ‘ " + yearLeft + "λ λ¨μΌμ¨μ΅λλ€";
    }
    ```
    
    1. μ«μμΈ `numberAsString`μ λ¬Έμμ΄λ‘ λ³ν
    2. `tostring` μ°μ°μλ₯Ό μ¬μ©νμ¬ κ°λμ±μ μ’κ² ν¨


        > Template literals μ¬μ© ν΄λ³΄κΈ°
  
    <br>

    ```javascript
    // μ€μ€ μ½λ
    if(Number(age_string) < 65){
        return "μμΌλ‘ " + (65-Number(age_string)) + "λ λ¨μΌμ¨μ΅λλ€";
    ```
    -   65μΈ μ‘°κ±΄μ λΉκ΅ μ°μ°μλ₯Ό μ¬μ©νλ λ°©λ²λ μλ€!