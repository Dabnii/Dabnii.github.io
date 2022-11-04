# <p align="center"> 🧢 React Props

## 🧢 React Props

- 컴포넌트의 속성값 Object
  - `부모 컴포넌트로부터 전달 받은 데이터`를 지니고 있는 `객체`
- 모든 타입의 데이터와 함수까지 어떤 값이든 자식 컴포넌트에 전달 가능
  - e.g. 문자, 숫자, 변수, 함수 등
- 2개 이상의 값일 때 `띄어쓰기로` 구분&전달
  - e.g.`<Child pet={animal} englishName='tiger' />`

### 💡 부모 컴포넌트에서의 데이터 전달

- `pet={animal}`과 같이 자식 컴포넌트에 속성 값을 추가
- 직접 값을 할당`(’tiger’)`해서 넘겨줄 수 있음
- 모든 데이터 타입을 넘겨줄 수 있음
- 2개 이상의 값일 때 `띄어쓰기로` 구분&전달

```javascript
// Parent.js(부모 컴포넌트)

import React from "react";

const Parent = () => {
  const animal = "호랑이";

  return (
    <>
      <h1>부모 컴포넌트입니다.</h1>
      <p>{animal}</p>
    </>
  );
};

export default Parent;
```

### 💡 자식 컴포넌트에서의 전달 받은 데이터 적용

- 함수 컴포넌트 또한 `const Child = (매개변수) ⇒ {}` 와 같이 부모 컴포넌트에서 보내준 데이터를 받아서 사용할 수 있음
- 부모 컴포넌트가 전달해 준 props는 `하나의 객체로 합쳐져서 함수 컴포넌트에 전달`
- 명시적으로 나타내기 위해 `const Child = (props) ⇒ {}`라고 매개변수 이름을 짓는 것이 컨벤션

```javascript
// Child.js(자식 컴포넌트)

import React from "react";

const Child = (props) => {
  console.log(props); // {pet: '호랑이', englishName: 'tiger'}

  return (
    <>
      <h2>자식 컴포넌트입니다.</h2>
      <p>{props.pet}</p> // 호랑이
      <p>{props.englishName}</p> // tiger
    </>
  );
};

export default Child;
```

### 💡 함수 전달과 적용

```javascript
import React from "react";
import Child from "./Child";

const Parent = () => {
  const testConsole = () => {
    console.log("테스트 입니다.");
  };

  return (
    <>
      <h1>부모 컴포넌트입니다.</h1>
      <button onClick={testConsole}>클릭</button>
      <Child test={testConsole} />
    </>
  );
};

export default Parent;
```

1.  부모 컴포넌트에서는 testConsole이라는 함수를 선언
2.  이 함수가 버튼을 클릭할 때마다 실행될 수 있도록 클릭 이벤트 핸들러
3.  함수를 자식 컴포넌트에서도 사용해야 하는 상황
4.  `부모 컴포넌트`에서는 전달하고자 하는 testConsole이라는 함수를 `어떤 이름으로 넘겨줄지만 정해`주면 됨

```javascript
// Child.js (자식 컴포넌트)

import React from "react";

const Child = (props) => {
  console.log(props); // {test: () => {console.log('테스트 입니다.')}}

  return (
    <>
      <h2>자식 컴포넌트입니다.</h2>
      <button onClick={props.test}>클릭</button>
    </>
  );
};

export default Child;
```

1. 부모 컴포넌트에서는 전달하고자 하는 함수를 `test라는 그릇에 담아 전달`
2. 부모 컴포넌트에서 선언된 함수이지만 `자식 컴포넌트에서도 사용할 수 있음`
3. `button 태그에 클릭 이벤트 핸들러`를 걸어줌
4. 해당 태그를 클릭할 때 마다 실행되는 함수를 `부모로부터 받은 test 함수로 정의`
5. ✨ 실제로 button 태그가 클릭될 때마다 실행되는 함수는 부모 컴포넌트에 있는 testConsole이라는 함수가

### 🍯 Props 꿀팁

- 컴포넌트별(js) 별로 구분하는 것을 권장

  - 유지 보수를 위함
  - 컴포넌트의 정의가 재활용이 가능한 UI 장점 사용

  <br>

<a href=""> 이전글: React & Hook </a>

<a href=""> 다음글: React & State </a>

<hr>
<p align="center"> E.O.D
