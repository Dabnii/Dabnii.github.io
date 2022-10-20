# <p align="center"> 🔠 String ←→ 🔢 Number

## Java Script의 data type 유동성
- 데이터 타입에 엄격하지 않다.
- 장점: 다른 언어보다 편하고 쉽다 👍
- 단점: 오류발생이 쉽다 🤔

<br>

## 🔠 String → Number

### `typeof`
-  typeof 연산자는 피연산자의 평가 전 자료형을 나타내는 문자열을 반환합니다.

    ```javascript
    console.log(typeof 42);
    // expected output: "number"

    console.log(typeof 'blubber');
    // expected output: "string"
    ```
    > https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/typeof

<br>

### 🔢 Function `Number()`
 - `Number()` 생성자는 Number 객체를 생성합니다. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/Number">📎 see more</a> 

    ```javascript
        var birthYearInput = "2000";
        console.log(typeof birthYearInput);

        var numberBirthYear = Number(birthYearInput);
        console.log(typeof numberBirthYear);
    ```

### `parseInt`
- parseInt() 함수는 문자열 인자를 파싱하여 특정 진수(수의 진법 체계에서 기준이 되는 값)의 정수를 반환합니다.

### `parseFloat`
- parseFloat() 함수는 주어진 값을 필요한 경우 문자열로 변환한 후 부동소수점 실수로 파싱해 반환합니다.

    ```javascript
        parseInt("1.901");
        parseFloat("1.901");
        Number("1.901");
        parseInt("200") + 1;
    ```

### ➖ 빼기 연산자 특성 
- 빼기 연산자 특성을 사용하여 String → Number 

    ```javascript
        var numberAsNumber = "1234";
        var numberAsString = numberAsNumber - 0;


        console.log(numberAsNumber, typeof numberAsNumber);
        console.log(numberAsString, typeof numberAsString);
    ```

<hr>
<br>

## 🔢 Number → String

### `tostring()`
- The toString() 은 문자열을 반환하는 object의 대표적인 방법이다

    ```javascript
        var numberAsNumber = 1234;
        var numberAsString = numberAsNumber.toString();

        console.log(numberAsNumber, typeof numberAsNumber);
        console.log(numberAsString, typeof numberAsString);
    ```

### ➕ 연산의 특성
- 빼기 연산자 특성을 사용하여 Number → String

    ```javascript
        var numberAsNumber = 1234;
        var numberAsString = 1234 + "";

        console.log(numberAsNumber, typeof numberAsNumber);
        console.log(numberAsString, typeof numberAsString);
    ```




## 🖥 String ←→ Number test [1]

### nationalPensionRemainingYearCount 함수를 구현해주세요.

- 우리나라는 국민연금을 만 65세 부터 받을 수 있습니다.
- `nationalPensionRemainingYearCount` 는 `age_string` 이라는 input을 받습니다.
- `age_string` 은 나이 값인데 string형 값으로 되어 있습니다.
- 주어진 나이부터 몇년이 지나야 국민연금을 받을수 있는지 리턴 해주세요.
- 리턴 값은 다음과 같습니다.
    
    ```javascript
    "앞으로 20년 남으셨습니다"
    ```
    
- 예를 들어, `age_string` 값이 다음과 같다면:
    
    ```javascript
    "35"
    ```
    
    리턴 값은 다음과 같아야 합니다.
    
    ```javascript
    "앞으로 30년 남으셨습니다"
    ```

    ```javascript
    function nationalPensionRemainingYearCount(age_string) {
    const numberAsString = age_string.toString();
    let yearLeft = 65 - numberAsString;
    return "앞으로 " + yearLeft + "년 남으셨습니다";
    }
    ```
    
    1. 숫자인 `numberAsString`을 문자열로 변환
    2. `tostring` 연산자를 사용하여 가독성을 좋게 함


        > Template literals 사용 해보기
  
    <br>

    ```javascript
    // 줍줍 코드
    if(Number(age_string) < 65){
        return "앞으로 " + (65-Number(age_string)) + "년 남으셨습니다";
    ```
    -   65세 조건을 비교 연산자를 사용하는 방법도 있다!