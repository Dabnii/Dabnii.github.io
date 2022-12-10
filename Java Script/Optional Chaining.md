# <p align=center> Optional Chaining `?.`

<p align=center> ⛓️ Optional Chaining : 왼쪽 평가대상이 없어도 괜찮은 경우에만 선택적으로 사용

### Optional Chaining 이란?

- 옵셔널 체이닝(optional chaining) `?.`을 사용하면 프로퍼티가 없는 중첩 객체를 에러 없이 안전하게 접근할 수 있습니다. -모던 자바스크립트

### Optional Chaining이 필요할 때

- 백엔드와 함께 통신 하기 전, Mock data를 사용할 때 위 오류를 만났다.
- 분명히 fetch한 데이터를 불러올 때 예상치 못한 오류가 발생했다.
  - <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md#mock-data">Mock 데이터 사용중 발견한 오류 -22.11.22-</a>
  - <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.11/1stWeek.md#-json-%EC%9D%B4%EC%8A%88">객체 데이터를 들고오면 터진다! -22.11.23-</a>

### 내가 사용한 Optional chaining

```jsx
const [pdData, setPdData] = useState([]);

{pdData[0]?.price}
pdData의 '0' 번째 배열에서 price를 가져옵니다.

`?.`
//옵셔널 체이닝
//📆 11/22
```

```jsx
  pdData.images?.map((image, i) => (
    <img src={image} alt="thumbnail" className="detailsInfo" />
  ));
}
```

- `pdData`는 상품 데이터를 가지고 있다. 상품명, 가격, 이미지등
-

- 📌 객체로 된 데이터라 때문에 조건부 실행을 원한다면 아래의 코드로 적어야한다.
  ```jsx
  {pdData[0] !== null && ()}
  ```
  - 배열은 `true`/`false` 값으로 들어온다
  - 객체는 `undefined`로 들어온다
  - `{pdData[0] && }`로 사용하면 오류가 발생한다.
  - 어떠한 객체를 받아오는지, 동기적 언어의 특성을 파악하지 못하연 초보적인 실수가 반복된다.
    - 시간을 효율적으로 쓰지 못하는 치명적인 단점

### 남용금지 Optional chaining

<br>

---

참고 자료:

- <a href="https://ko.javascript.info/optional-chaining">옵셔널체이닝'?.'</a>
