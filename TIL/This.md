# <p align="center"> 🔦 THIS

JavaScript에서 함수의 this 키워드는 다른 언어와 조금 다르게 동작합니다. 또한 엄격 모드와 비엄격 모드에서도 일부 차이가 있습니다.

대부분의 경우 this의 값은 함수를 호출한 방법에 의해 결정됩니다. 실행중에는 할당으로 설정할 수 없고 함수를 호출할 때 마다 다를 수 있습니다. ES5는 함수를 어떻게 호출했는지 상관하지 않고 this 값을 설정할 수 있는 bind 메서드를 도입했고, ES2015는 스스로의 this 바인딩을 제공하지 않는 화살표 함수를 추가했습니다(이는 렉시컬 컨텍스트안의 this값을 유지합니다).

| &#32;     | 📌 This            | <a href='https://github.com/Dabnii/Dabnii.github.io/blob/main/Computer%20Science/Closure.md#-%EC%83%81%EC%9C%84-%EC%8A%A4%EC%BD%94%ED%94%84%EC%9D%98-%EC%A0%95%EC%9D%98-in-js-'>Closure</a> |
| --------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 결정 방식 | `📢 호출`되는 시점 | (정의)선언한 위치에 따라 결정                                                                                                                                                               |

## this

### this가 뭔가요?

this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수이다.

this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다.

this는 자바스크립트 엔진에 의해 암묵적으로 생성되며, 코드 어디서든 참조할 수 있다.

단 this가 가리키는 값, 즉 this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.

<br/>

### this 바인딩이란?

바인딩이란 식별자(변수)와 값(원시 값 또는 객체)을 연결하는 과정을 의미한다.

예를 들어, 변수 선언은 변수 이름(식별자)과 확보된 메모리 공간의 주소를 바인딩하는 것이다.

this 바인딩은 this(키워드로 분류되지만 식별자 역할을 한다)와 this가 가리킬 객체를 바인딩하는 것이다.

<br/>

### this는 동적으로 바인딩이 된다고 하는데 바인딩되는 객체가 어떻게 다르나요?

| 함수 호출 방식                                             | this 바인딩                                                            |
| :--------------------------------------------------------- | :--------------------------------------------------------------------- |
| 일반 함수 호출                                             | 전역 객체(window/ global)                                              |
| 콜백 함수 호출                                             | 전역 객체(window/ global)                                              |
| 내부 함수 호출                                             | 전역 객체(window/ global)                                              |
| 메서드 호출                                                | 메서드를 호출한 객체                                                   |
| 생성자 함수 호출                                           | 생성자 함수가 (미래에) 생성할 인스턴스                                 |
| Function.prototype.apply/call/bind 메서드에 의한 간접 호출 | Function.prototype.apply/call/bind 메서드에 첫 번째 인수로 전달한 객체 |

---

<aside>
💡 this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가르키는 자기 참조 변수 self-referencing varibale다. this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다.

</aside>

- 자바스크립트 엔진에 의하여 암묵적으로 생성 되며, 코드 어디서든 참조 할 수 있다.
- `this` 바인딩은 함수 호출 방식에 의헤 동적으로 결정 된다.
  - 바인딩이란 식별자와 값을 연결하는 과정을 의미한다. 예를 들어, 변수 선언은 변수 이름 (식별자)과 확보된 메모리 공간의 주소를 바인딩하는 것이다. this바인딩은 this(키워드로 분류되지만 식별자 역할을 한다)와 this가 가르킬 객체를 바인딩하는 것이다.
  -  <aside>
     💡 렉시컬스코프와 this 바인딩은 결정 시기가 다르다.
     함수의 상위 스코프를 결정하는 방식인 렉시컬 lexical scope는 함수 정의가 평가되어 함수 객체가 생성되는 시점에 상위 스포크를 결정한다. 하지만 this 바인딩은 함수 호출 시점에 결정된다.
     
     </aside>
     
     - 동일한 함수도 다양한 방식으로 호출할 수 있다는 것
         1. 일반 함수 호출 : `global obejct` 전역개체 바인딩
         2. 메서드 호출 : `this.` 앞에 기술한 객체가 바인딩 
         3. 생성자 함수 호출 : 생성자 함수가 (미래에) 생성할 인스턴스
         4. `function.prototype.apply/call/bind` 메서드에 의한 간접 호출 : 메서드에 첫번째 인수로 전달한 객체
- ***

출처:

- [This_MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)
- [자바스크립트 this? 간단히 핵심만 파악하기](https://www.youtube.com/watch?v=PAr92molMHU)

- [Understanding “this” in JavaScript](https://medium.com/init-js/understanding-this-in-javascript-f2f41f6517a9)

- [메서드와 th                                                        ](https://ko.javascript.info/object-methods)

- [this](https://github.com/Dabnii/prepare_frontend_interview/blob/main/js.md#this)
