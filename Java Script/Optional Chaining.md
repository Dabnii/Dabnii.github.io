# <p align=center> ⛓️ Optional Chaining `?.`

<p align=center> ⛓️ Optional Chaining : 앞의 평가 대상이 undefined 나 null 이면 평가를 멈추고 undefined를 반환

### ⛓️ Optional Chaining 이란?

> The optional chaining `?.` operator accesses an object's property or calls a function. If the object is undefined or null, it returns `undefined` instead of throwing an error. <i>-MDN-</i>

- 옵셔널 체이닝(optional chaining) `?.`을 사용하면 프로퍼티가 없는 중첩 객체를 에러 없이 안전하게 접근할 수 있습니다. <i>-모던 자바스크립트-</i>
- 💡 `?.`은 ` ?.` `앞`의 평가 대상이 `undefined`나 `null`이면 평가를 멈추고 `undefined를` 반환합니다.
- 왼쪽 평가대상이 없어도 괜찮은 경우에만 `선택적`으로 사용합니다.
  - 없어도 되는 값에만 사용하며, 남용은 에러를 야기합니다.
- 변수가 선언 되어 있을 때 만 사용할 수 있습니다.
- 함수에도 사용할 수 있습니다.

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
  - 👀 낮은 가독성: `&&`을 사용하여 비교할 경우 코드가 길어지게 됨
  - 🪜 낮은 안정성 : 비교하는 값 중, 만약 `obj.first`가 `0` 즉 `falsy` 한 값이라면 오류가 발생할 수 있기 때문에 권장하지 않음

### ⛓️ 내가 사용한 Optional chaining

- 백엔드와 함께 통신 하기 전, Mock data를 사용할 때 아래 오류를 만났다.
- fetch한 데이터를 불러올 때 화면 렌더가 되지 않는 오류 발생

  - <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md#mock-data">Mock 데이터 사용중 발견한 오류 -22.11.22-</a>
  - <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md#-json-%EC%9D%B4%EC%8A%88">객체 데이터를 들고오면 터진다! -22.11.23-</a>


  📍 `Fetch`&`useEfect`&`Optional chaining` | 자바스크립트는 동기적 언어
    ```jsx
      import { Link, useParams } from "react-router-dom";

      useEffect(() => {
        fetch(`https://reqres.in/api/users/${userId}`, {
          method: "GET",
        })
          .then((response) => response.json())
          .then((data) => setPdData(data));
      }, []);

      //중략

      {
      pdData.images?.map((image, i) => (
        <img src={image} alt="thumbnail" className="detailsInfo" />
      ));
    }
    ```  
  1. 자바스크립트는 위에서 아래로, 동기적으로 실행됩니다.  
  1. 위의 코드에서의 실행 순서는 UI를 먼저 렌더링 합니다.
  1. `useEffect` `fetch`전이므로 전달 받은 데이터가 없습니다.
  1. 없는 데이터를 사용하여 맵을 하고자 하면 오류가 발생합니다.
      - 오류를 방지하기 위하여 임시로 `?.`를 사용하여 `null` 또는 `undefiend` 로 렌더를 진행합니다.
  1. UI 렌더가 진행 된 후 `useEffect의` `fetch`가 진행됩니다.
  1. paData의 값은 더 이상 null이 아닌 데이터가 되어 임시로 렌더 되었던 UI에 개발자가 원하는 데이터를 맵핑할 수 있게 됩니다.
  1. 📍 `Price?.` 사례

    ```jsx
    const [pdData, setPdData] = useState([]);

    {pdData[0]?.price}
    pdData의 '0' 번째 배열에서 price를 가져옵니다.
    
    //옵셔널 체이닝 📆 11/22
    ```
    - 위와 같은 이유로 옵셔널 체이닝을 사용하여 pdData의 값이 null일 때 렌더링의 블락커가 되지 않도록 합니다.  


### ⛓️ Optional chaining 주의할 점

  ```jsx
  // ReferenceError: user is not defined
  user?.address;
  //user?.anything을 사용하려면 let이나 const, var를 사용해 user를 정의해야 하죠. 이렇게 옵셔널 체이닝은 선언이 완료된 변수를 대상으로만 동작합니다.
  ```
- ⚠️ 옵셔널 체이닝을 남용하지 마세요.
  `?.`는 `존재하지 않아도 괜찮은 대상에만 사용`해야 합니다.
- 사용자 주소를 다루는 위 예시에서 논리상 user는 반드시 있어야 하는데 address는 필수값이 아닙니다. 그러니 `user.address?.street를 사용하는 것이 바람직`합니다.
  - 실수로 인해 user에 값을 할당하지 않았다면 바로 알아낼 수 있도록 해야 합니다. 그렇지 않으면 에러를 조기에 발견하지 못하고 디버깅이 어려워집니다.
- `?.앞의 변수는 꼭 선언`되어 있어야 합니다.
- 변수 user가 선언되어있지 않으면 `user?.anything` 평가시 에러가 발생합니다.<br>
<i>-모던 자바스크립트-</i>

### ⛓️ Optional chaining 그리고 폴리필 

![Need Optional chaining polyfill](https://user-images.githubusercontent.com/110847597/208449972-2eb86606-41c5-482d-9114-e447b8e4ed5e.png)
- 이럴 땐, optional chaining이 나오기 전의 방식으로 [&& 연산자를 사용한 test](https://github.com/Dabnii/Dabnii.github.io/blob/main/Java%20Script/Optional%20Chaining.md#%EF%B8%8F-optional-chaining%EC%9D%B4-%ED%95%84%EC%9A%94%ED%95%9C-%EC%9D%B4%EC%9C%A0) 하면 된다.
  ```javascript
  //&& 연산자를 사용한 test
  const nestedProp = obj.first && obj.first.second;
  ```


---

참고 자료:

- <a href="https://ko.javascript.info/optional-chaining">옵셔널체이닝'?.'</a>
- <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining">Optional chaining (?.)</a>
- <a href="https://www.youtube.com/watch?v=RA8RHgzPokk&t=5s">Optional Chaining Operator (?.) in JavaScript
</a>


---

<p align="center">E.O.D</p>
