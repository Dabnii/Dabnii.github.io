# <p align="center"> 🔦 THIS

JavaScript에서 함수의 this 키워드는 다른 언어와 조금 다르게 동작합니다. 또한 엄격 모드와 비엄격 모드에서도 일부 차이가 있습니다.

대부분의 경우 this의 값은 함수를 호출한 방법에 의해 결정됩니다. 실행중에는 할당으로 설정할 수 없고 함수를 호출할 때 마다 다를 수 있습니다. ES5는 함수를 어떻게 호출했는지 상관하지 않고 this 값을 설정할 수 있는 bind 메서드를 도입했고, ES2015는 스스로의 this 바인딩을 제공하지 않는 화살표 함수를 추가했습니다(이는 렉시컬 컨텍스트안의 this값을 유지합니다).

| &#32;     | 📌 This            | <a href='https://github.com/Dabnii/Dabnii.github.io/blob/main/Computer%20Science/Closure.md#-%EC%83%81%EC%9C%84-%EC%8A%A4%EC%BD%94%ED%94%84%EC%9D%98-%EC%A0%95%EC%9D%98-in-js-'>Closure</a> |
| --------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 결정 방식 | `📢 호출`되는 시점 | (정의)선언한 위치에 따라 결정                                                                                                                                                               |

---

출처:

- [This_MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)
- [자바스크립트 this? 간단히 핵심만 파악하기](https://www.youtube.com/watch?v=PAr92molMHU)

- [Understanding “this” in JavaScript](https://medium.com/init-js/understanding-this-in-javascript-f2f41f6517a9)
