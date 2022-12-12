# <p align=center> ⛓️ Optional Chaining `?.`

<p align=center> ⛓️ Optional Chaining : 왼쪽 평가대상이 없어도 괜찮은 경우에만 선택적으로 사용

### ⛓️ Optional Chaining 이란?

- The optional chaining `?.` operator accesses an object's property or calls a function. If the object is undefined or null, it returns `undefined` instead of throwing an error.

- 옵셔널 체이닝(optional chaining) `?.`을 사용하면 프로퍼티가 없는 중첩 객체를 에러 없이 안전하게 접근할 수 있습니다. <i>-모던 자바스크립트-</i>
- 💡 `?.`은 ` ?.` `앞`의 평가 대상이 `undefined`나 `null`이면 평가를 멈추고 `undefined를` 반환합니다.

### ⛓️ Optional Chaining syntax

```javascript
obj.val?.prop;
obj.val?.[expr];
obj.func?.(args);
```

### ⛓️ Optional Chaining이 필요한 이유

```javascript
//Optional Chaining
const nestedProp = obj.first?.second;
```

```javascript
//&& 연산자를 사용한 test
const nestedProp = obj.first && obj.first.second;
```

- 위 아래 코드는 같은 코드
- `&&` 사용을 권장하지 않는 이유:

  - 👀 가독성: `&&`을 사용하여 비교할 경우 코드가 길어지게 됨
  - 🪜 낮은 안정성 : 비교하는 값 중, 만약 `obj.first`가 `0` 즉 `falsy` 한 값이라면 오류가 발생할 수 있기 때문에 권장하지 않음

### ⛓️ 내가 사용한 Optional chaining

- 백엔드와 함께 통신 하기 전, Mock data를 사용할 때 아래 오류를 만났다.
- fetch한 데이터를 불러올 때 화면 렌더가 되지 않는 오류가 발생!

  - <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md#mock-data">Mock 데이터 사용중 발견한 오류 -22.11.22-</a>
  - <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md#-json-%EC%9D%B4%EC%8A%88">객체 데이터를 들고오면 터진다! -22.11.23-</a>

- 📍 `Price?.`

  ```jsx
  const [pdData, setPdData] = useState([]);

  {pdData[0]?.price}
  pdData의 '0' 번째 배열에서 price를 가져옵니다.

  `?.`

  //옵셔널 체이닝 📆 11/22
  ```

- `pdData`는 상품 데이터를 가지고 있다. 상품명, 가격, 이미지등

  ```jsx
    pdData.images?.map((image, i) => (
      <img src={image} alt="thumbnail" className="detailsInfo" />
    ));
  }
  ```

  - 📌 객체로 된 데이터라 때문에 조건부 실행을 원한다면 아래의 코드로 적어야한다.
    ```jsx
    {pdData[0] !== null && ()}
    ```
    - 배열은 `true`/`false` 값으로 들어온다
    - 객체는 `undefined`로 들어온다
    - 객체인 `{pdData[0] && }`로 조건부 렌더링을 사용하면 오류가 발생한다.
    - 어떠한 데이터 타입을 받아오는 지 파악하지 못하연 초보적인 실수가 반복된다. ☹️

  ```jsx
  const data = {};
  console.log(data.id); //
  console.log(data?.id); //undefined
  ```

### ⛓️ 남용금지 Optional chaining

- ⚠️ 옵셔널 체이닝을 남용하지 마세요.
  `?.`는 `존재하지 않아도 괜찮은 대상에만 사용`해야 합니다.

- 사용자 주소를 다루는 위 예시에서 논리상 user는 반드시 있어야 하는데 address는 필수값이 아닙니다. 그러니 `user.address?.street를 사용하는 것이 바람직`합니다.

- 실수로 인해 user에 값을 할당하지 않았다면 바로 알아낼 수 있도록 해야 합니다. 그렇지 않으면 에러를 조기에 발견하지 못하고 디버깅이 어려워집니다.

`?.앞의 변수는 꼭 선언`되어 있어야 합니다.

- 변수 user가 선언되어있지 않으면 `user?.anything` 평가시 에러가 발생합니다.

  ```jsx
  // ReferenceError: user is not defined
  user?.address;
  //user?.anything을 사용하려면 let이나 const, var를 사용해 user를 정의해야 하죠. 이렇게 옵셔널 체이닝은 선언이 완료된 변수를 대상으로만 동작합니다.
  ```

  <i>-모던 자바스크립트-</i>
  <br>

---

참고 자료:

- <a href="https://ko.javascript.info/optional-chaining">옵셔널체이닝'?.'</a>
- <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining">Optional chaining (?.)</a>

---

<p align="center">E.O.D</p>
