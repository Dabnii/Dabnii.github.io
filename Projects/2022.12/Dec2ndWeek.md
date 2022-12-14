## <p align="center"> `Internship` π 12/12

### β° Setting time

1. install nvm:Β [https://github.com/creationix/nvm](https://github.com/creationix/nvm)
   ```jsx
   $ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
   ```
2. install node stable version:Β `nvm install stable`
3. install yarn:Β `npm install -g yarn`
   ```jsx
   $ nvm install vNN.NN.N
   //μ¬μ©νκ³ μ νλ λ²μ  μΌλ‘ λ³ν ν©λλ€
   ```
4. install requirements:Β `yarn install`
5. createΒ `.env`Β according toΒ `.env.example`
6. start projectΒ `yarn start`

## π NVM λ²μ μ κ³ μ νκΈ°

1. μ¬λΆν ν μ μμ, ν°λ―Έλμ nvm λ²μ μ΄ λ°λλ κ²μ λ°©μ§ νκΈ° μν¨μλλ€.
1. μ΅μ  λ²μ μ΄ μλ νΉμ  λ²μ μ μ¨μΌνλ κ²½μ°μ νμν©λλ€.

   ```jsx
   $ nvm list
   //νμ¬ nvm λ²μ μ νμΈ
   ```

   ```jsx
   $ nvm use v14
   //μνλ λ²μ μΌλ‘ λ³κ²½ (μμμ )
   ```

   ```jsx
   $ nvm alias default v14
   //μνλ λ²μ μΌλ‘ λν΄νΈ κ° κ³ μ 
   ```

   <img width="856" alt="μ¬λΆν" src="https://user-images.githubusercontent.com/110847597/207327527-45b7bedb-a64f-46bc-80cb-bd6415532f3b.png">
   > κ°λμ ν°λ―Έλλ μ¬λΆνμ΄ νμνλ€

### π₯ Onboarding

1. κΉνλΈ μΈνμ΄ μλ£ λμλ€λ©΄
1. κΉνλΈ `package.json` μ λλ¬λ³΄λ©° μ¬μ©λλ κ²λ€ νμΈνκΈ°!

π³ μ±μ₯ ν¬μΈνΈ

1.`yarn` `npm` μ°¨μ΄ νμ΅ 1.`redux`νμ΅ νμ!

---

## <p align="center"> `Internship` π 12/13

## π₯ Onboarding πππ

### π λ―Έλ¦¬ λλ¬ λ³Ό κ²!

- [x] `packagelock.json`μ μμ‘΄μ± νμΈ
- [x] `Git branch` νμΈ
- [x] `Pull Request` μ»¨λ²€μ νμΈ
- [x] `Commit message` μ»¨λ²€μ νμΈ

---

## <p align="center"> `Internship` π 12/16

### π Class Components

```jsx
// App.js

import React from "react";

class App extends React.Component {
  render() {
    return <h1>This is Class Component!</h1>;
  }
}
export default App;
```

> ν΄λμ€ μ»΄ν¬λνΈμμλ μμ κ°μ΄ λ°λμ render() λ©μλκ° μμ΄μΌ νκ³ , κ·Έ μμμ νλ©΄μ λ³΄μ¬μ€ JSX(Javascript Syntax eXtension) λ₯Ό λ°νν©λλ€. state λ° lifecycle(λΌμ΄νμ¬μ΄ν΄) APIλ₯Ό ν΅ν΄ κ΄λ ¨ κΈ°λ₯μ μ¬μ©ν  μ μμ΅λλ€.

```jsx
console.log(this.props);
console.log(columns);
//μμ λκ°μ§λ‘ μμλΈ λ°μ΄ν° κ΅¬μ‘°
```

π³ μ±μ₯ ν¬μΈνΈ :

- ν΄λμ€ μ»΄ν¬λνΈλ₯Ό μ¬μ©
  - νμ΅μ μνμ¬ class componentλ₯Ό μ¬μ© μ€, κΈ°μ‘΄μ μμλμ΄μλ νλ‘μ νΈλ ν΄λμ€ μ»΄ν¬λνΈλ‘ κ΅¬μ±λμ΄ μλ€.
- `console.log`λ₯Ό μ°μ΄λ³΄λ©° μ΄λ€ λ°μ΄ν°κ° λ€μ΄μ€λμ§ νμΈν΄ λ³΄λ μ΅κ΄μ κ°μ§μ.
- `this`μ μ»΄λ°±

---

## <p align="center"> `Internship` π 12/19

### π `antd table` library

μ£ν΄... [π antd table: κ³΅μ μ¬μ΄νΈ](https://ant.design/components/table)

> μ΄μ©μ§... propsλ‘ μ΄λ€ κ°μ λ£μ΄λ μ€λ₯κ° λ¬λ€.<br>
> λΉμ°ν¨, λΌμ΄λΈλ¬λ¦¬μ λͺμΈλ₯Ό νμΈ νμ΄μΌνλ€.<br>
> μ€λμ κ΅ν, package-lock.jsonμ μ΄μ¬ν νμΈνκ³ ... κ²μμ κΌ­ ν΄λ³΄μ.<br>
> λμ¨λ ... μ¬μκ»μ νμΈν΄λ³΄λΌλκ² μ΄λ° λΌμ΄λΈλ¬λ¦¬κ° μλ€λ κ±Έ λ³΄λκ±°μλ€. νμ§λ§ μλλ§νΌ λ³΄μΈλ€κ³  μμ μΈ λλ λͺ°λλ€. antdλ₯Ό μμ²΄μ μΌλ‘ λ§λ κ±΄ μ€ μμλ€.. μ€λμ΄λΌλ μμμ λ€νμ΄λ€.

```jsx
<Table
  className="table table_small"
  rowSelection={rowSelection}
  columns={columns}
  dataSource={data}
  onRow={record => ({
    onClick: () => {
      this.selectRow(record);
    },
  })}
/>
```

```jsx
    const data = [
      {
        key: '1',
        SCHEDULE_NAME: 'test1',
        CREATED: '2022/12/25',
        SCHEDULE_TAG: 32,
      },
      {
        key: '2',
        SCHEDULE_NAME: 'test2',
        CREATED: '2022/12/30',
        SCHEDULE_TAG: 42,
      },
...
    ];

    const columns = [
      {
        title: 'SCHEDULE NAME',
        dataIndex: 'SCHEDULE_NAME',
        key: 'SCHEDULE_NAME',
      },
      {
        title: 'SCHEDULE TAG',
        dataIndex: 'SCHEDULE_TAG',
        key: 'SCHEDULE_TAG',
      },
...
    ];
```

κ³΅μλ¬Έμλ₯Ό λ°λΌ μμ±νλ©΄ μ§μ, μ΄λ κ² μ΄λ―Έμ§κ° λ¬λ€. πππ
![after table screenshot](https://user-images.githubusercontent.com/110847597/208448995-d5fbacc8-0d0d-4702-bcb1-a7876419f791.png)

λ΄μΌ ν  μΌ:

- [ ] SCSSλ₯Ό μμ νκΈ°, μ»€λ°νκΈ°

<br>

### <p align="center">π `This.state?` `This.Props?`

> νμ μ½λλ₯Ό λ³΄λ€λ³΄λ, thisκ° μ λ§ λ§μ΄ μ°μ΄κ³  μμλ€.
> μ΄λμ νΈμΆνλλμ λ°λΌ λ°μΈλ© λλκ²μ΄ κ²°μ λλ€λλ° λ μ κ·Ήμ μΌλ‘ κ³΅λΆλ₯Ό ν΄μΌκ² λ€.

π This.state

1. `this.state` : stateλ₯Ό ν΄λΉ μ»΄ν¬λνΈμμ λ§λ€ λ

π§ββοΈ This.props

1. `this.props` : λΆλͺ¨ μ»΄ν¬λνΈλ, λ¦¬λμ€μμ `ν΄λΉ μ»΄ν¬λνΈμ μ£Όμ` ν  λ

π³ μ±μ₯ ν¬μΈνΈ :

- λ΄κ° μ΄λ ΅λ€λ©΄, μ΄λ €μ΄ κ²μ΄ λ§λ€!
  - κ·Έλλ§λ€ λ¬Όμ΄λ³΄κ³  λ μμλ³΄μ!
- λΌμ΄λΈλ¬λ¦¬λ₯Ό λ§μ΄ μ¨λ³΄κ³  μΉμν΄ μ ΈμΌκ² λ€.
- `this` κ³΅λΆλ μμ§ λ§μ!

## <p align="center"> `Internship` π 12/21

### π class components Error + `this`

### π μ€λ λ§λ μλ¬

_`Uncaught RefereceError:isStagingSchedulingTableShown`μ΄ μ μΈλμ§ μμλ€λ κ²._
<img width="1000px" alt="Error!!" src="https://user-images.githubusercontent.com/110847597/208923021-1b281f3d-db2f-494d-b0a9-23cab8b6a201.png" align="center">

π€ νμ§λ§ λ λΆλͺ μ μΈμ νλλ°?
μ΄λ κ² λ§μ΄λ€! π
<img width="1000px" alt="Error!!2" src="https://user-images.githubusercontent.com/110847597/208923028-c15f834d-f8e7-485b-9a67-e710c3dd7d4d.png" align="center">

π§ μ°¨κ·Όν μ½λλ₯Ό νμ΄λ³΄λ€, `this`λ₯Ό μ¬μ©νλ€λκ±Έ μκ² λμκ³  ν¨μν μ»΄ν¬λνΈμλ λ€λ¦μ μκ² λμλ€.
<img width="1000px" alt="Error!!3" src="https://user-images.githubusercontent.com/110847597/208923033-9a6026af-92a1-42ac-bfd2-b5dc1dc09cf7.png" align="center">

μλμ κ°μ΄ this.state μ΄ μ»΄ν¬λνΈμμ λ§λ€κ³ , μ μΈνκ² μμ μ»΄ν¨ν°μκ² μλ Έλ€.
<img width="1000px" alt="Error!!fix!" src="https://user-images.githubusercontent.com/110847597/208923037-cf51b5e3-3585-4b75-8fa1-3ce7eb44d8ce.png" align="center">

μ ν΄κ²°νμλ€. λΏλ― πͺ

```jsx
//Counter.js
import React, { Component } from "react";

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = {
      increaseNum: 0,
      decreaseNum: 100,
    };
  }

  render() {
    const { increaseNum, decreaseNum } = this.state;
    return (
      <div>
        <h1>μ¦κ°νλ κ° : {increaseNum}</h1>
        <h2>κ°μνλ κ° : {decreaseNum}</h2>
        <button
          onClick={() => {
            this.setState({
              increaseNum: increaseNum + 1,
              decreaseNum: decreaseNum - 1,
            });
          }}
        >
          Increase / Decrease
        </button>
      </div>
    );
  }
}

export default Counter;
```

> [[React] ν΄λμ€ν μ»΄ν¬λνΈμμ state μ¬μ©νκΈ°](https://velog.io/@choie0423/React-%ED%81%B4%EB%9E%98%EC%8A%A4%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%97%90%EC%84%9C-state-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)

### π³ μ±μ₯ ν¬μΈνΈ :

- μλ¬μ λΉν©νμ§ μκ³  μ½μ΄λ³΄κ³ , κ²μνκ³  μ½λλ₯Ό νλμ© μ²΄ν¬νλ©° μ€μ€λ‘ ν΄κ²°νκ³  μλ€.
- λΉλ‘ ν΄λμ€ μ»΄ν¬λνΈλ₯Ό λ§μ΄ μ¬μ©νμ§ μλ μΆμΈμ΄μ§λ§, λΆλͺνλ³΄κ³  κ²½ννκ³  μμ΄ λ§μ΄ λ°°μ°κ³  μλ€.

μΆμ²:

- [[React] ν΄λμ€ν μ»΄ν¬λνΈμμ state μ¬μ©νκΈ°](https://velog.io/@choie0423/React-%ED%81%B4%EB%9E%98%EC%8A%A4%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%97%90%EC%84%9C-state-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)

## <p align="center"> `Internship` π 12/22

### π class components `componentDidMount()`

- `uncaught invariant violation: hooks can only be called inside`

  - ν΅μ  μ€λΉλ₯Ό μνμ¬ `useEffectμ` `fetch`λ₯Ό μμ±νκ³  λ λ νλ μκ°, λ°μλ μ€λ₯
    <img width="529" alt="KakaoTalk_Photo_2022-12-23-00-14-51" src="https://user-images.githubusercontent.com/110847597/209169628-7c2a358b-1bba-49e7-ad13-95cb3f83f52e.png">
  - μ½λλ₯Ό μλ¬΄λ¦¬ νμΈ ν΄λ, λ΄ hookμ ν¨μ λ΄λΆμ μ μΈ λμ΄ μμλ€.
  - ν΄λμ€ μ»΄ν¬λνΈμ ν¨μν μ»΄ν¬λνΈμ μ°¨μ΄λ₯Ό λͺΈμ λ°°μ°λ μκ°μ΄μλ€.
  - ν¨μνκ³Ό ν΄λμ€ μ»΄ν¬λνΈμ κ°μ₯ ν° μ°¨μ΄μ μ, μλͺμ£ΌκΈ°λ₯Ό κ΄λ¦¬ ν  μ μλ Hookμ μ°¨μ΄

    - Hookμ΄ λ±μ₯νκΈ° μ  κΉμ§, ν΄λμ€ μ»΄ν¬λνΈλ§ μλͺμ£Όλ¦¬λ₯Ό κ΄λ¦¬ν  μ μμλ€κ³  νλ€.
    - Hookμ λ±μ₯μΌλ‘ ν¨μ μ»΄ν¬λνΈκ° λ§μ΄ νμ±ν λμλ€κ³  νλ€.
    - μ¦, Hookμ΄ λμ€κΈ° μ μλ ν¨μ μ»΄ν¬λνΈμμ μλͺμ£ΌκΈ°λ₯Ό κ΄λ¦¬νκΈ° μ΄λ €μ λ€λκ²!

    ### π Component types

    | &#32;    | Class component                | Function component            |
    | -------- | ------------------------------ | ----------------------------- |
    | λμ΄λ   | μ¬ν λ° νμ!                  | μ΄μ¬μμκ² μΆμ²               |
    | νμμ¬ν­ | β¨Β `render()` λ©μλ           | &#32;                         |
    | νΉμ§     | State & Lifecycle API μ¬μ©κ°λ₯ | Hook λ±μ₯μ΄ν `state`μ¬μ©κ°λ₯ |

    - [My TIL:π§’ React Component](https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20component.md)

    ```jsx
    componentDidMount() {
      fetch('../../../api/requests/MockDataSchedule.json').then(res =>
        tagReadData(res).then(console.log('Saved!')),
      );
    }
    ```

    [Ref: Fetching Data in React using Hooks](https://blog.bitsrc.io/fetching-data-in-react-using-hooks-c6fdd71cb24a?gi=bc14f2a9db99)

    > ν΄λμ€μ»΄ν¬λνΈλ₯Ό μ¬μ©νκ² λμ΄μ μκ΄μ΄λ€. ν¨μ μ»΄ν¬λνΈλ₯Ό μΈ λ λ³΄λ€ λ λ§μ΄ λμ΄μ§μ§λ§, νμ€ν λ§μ΄ λ°°μκ°λ€. νΉνλ `this`μ κ°λμ΄ νλ¦½λλ μ€.

    ![KakaoTalk_Photo_2022-12-23-00-14-40 002](https://user-images.githubusercontent.com/110847597/209169661-13f590b6-db7d-452a-966b-2f87dd34a2bc.png)

    <img width="519" alt="KakaoTalk_Photo_2022-12-23-00-14-40 001" src="https://user-images.githubusercontent.com/110847597/209169666-6735970f-9fd5-46ad-946e-d81bf9ebd156.png">

    - κ·Έλ¦¬κ³  μ½μλ‘κ·Έλ₯Ό λ§μ΄ μ°μ΄λ³΄λ©°, μ½λ©νλ μ€μλλ€.

    ![KakaoTalk_Photo_2022-12-23-00-14-40 004](https://user-images.githubusercontent.com/110847597/209169654-30fbbff1-5745-4c94-ade7-aecd424ac119.png)

    <img width="514" alt="KakaoTalk_Photo_2022-12-23-00-14-40 007" src="https://user-images.githubusercontent.com/110847597/209169643-d20127ee-c18b-48d8-9b84-3c58a82fc5fc.png">

    - λ΄κΈ°μ§ μμμ΅λλ€. μ¬νλλ€.

## <p align="center"> `Internship` π 12/23

### π class components

- `object` + `map`

```jsx
//Parent
state = {
    responseType: null,
  };
//μ΅μμμμ stateλ₯Ό μ μΈν©λλ€.

const {
      responseType,
    } = this.state;
//κ΅¬μ‘°λΆν΄ ν λΉμ ν΅νμ¬ this.stateμ responseTypeμ λ£μ΅λλ€

const typeList = [
  {
    label: 'Retraining',
    value: 'retraining',
  },
  { label: 'Batch Prediction',
		value: 'batch_prediction' },
];

//κΈ°μ‘΄μ νλμ½λ© νλ λΆλΆμ, λ§΅μ λλ € μ¬μ©ν©λλ€.
<div className="tabs-menu__item">
    {typeList.map(item => {
      return (
        <button
          key={item.value}
          type="button"
          className="button-menu__link link_active"
          value={item.value}
          onClick={() =>
            this.setState({ responseType: item.value })
          }
        >
          <div className="tab-text">
            <span className="tab-menu__item">
              <span>{item.label}</span>
            </span>
          </div>
        </button>
      );
    })}
</div>

		<SchedulingTag
        workspaceId={workspaceId}
        projectId={projectId}
        responseType={responseType}
      />
```

2. μμ λΆλͺ¨ μ»΄ν¬λνΈμμ μμμ΄ λλ¬λ€λ©΄, μμ μ»΄ν¬λνΈμ νλ‘­μ€λ‘ μ λ¬ ν©λλ€.

```jsx
//child
componentWillMount() {
    const { workspaceId, projectId, responseType } = this.props;
    this.getTableApi({ workspaceId, projectId });
  }
//μ λ¬ λ°μ νλ‘­μ€ κ΅¬μ‘°λΆν΄ν λΉμ ν΄μ€λλ€

//responseTypeμ fetchλ₯Ό μ¬μ©ν  λ
`url${workspaceId}/projects/${projectId}/tags/type/${responseType}`,
//μΆκ°: νλ₯­ν λ€μμΌλ‘ λ°κΎΈλ κ²μ΄ μ’κ² κ΅°μ...
```

### π§’π `try & catch`

- `try...catch` λ¬Έμ μ€νν  μ½λλΈλ­μ νμνκ³  μμΈ(exception)κ° λ°μ(throw)ν  κ²½μ°μ μλ΅μ μ§μ ν©λλ€.
- `μ€λ₯ λ° μμΈλ₯Ό μ²λ¦¬` ν¨ λκ² κ°μ΄ μμ©ν¨ [Try...catch MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/try...catch)
- μ¬μ©νκ² λ μ΄μ λ, μ ν¨ν urlμ νΈμΆ νμ§λ§ μλλλ‘ λμ§ μμ νμΈμ μνμ¬ μ¬μ©νλ€.

```jsx
try {
  nonExistentFunction();
} catch (error) {
  console.error(error);
  // expected output: ReferenceError: nonExistentFunction is not defined
  // Note - error messages will vary depending on browser
  // MDN
}
```

```jsx
try {
  hello.toUpperCase();
} catch {
  console.log("Error");
}
```

```jsx
function yell(msg) {
  try {
    console.log(msg.toUpperCase().repeat(3));
  } catch (e) {
    console.log("try again");
  }
}
```

### π«‘ μ€μ  try catchλ₯Ό νμ©ν μ½λ

```jsx
//child
//Try & Catch
getTableApi = async ({ projectId, workspaceId, responseType }) => {
  const authToken = localStorage.getItem("auth_token");
  try {
    const response = await fetch(`url`, {
      method: "GET",
      headers: {
        Authorization: authToken,
        "client-server": "application/json",
      },
    });

    const tagReadData = await response.json();
  } catch (err) {
    console.log(err);
  }
};
//async awaitλ μ¬μ©νμ¬ λλ¬΄λ λ°κ°μ λ€.
```

- π© μμ§ λ΄κ° ν·κ°λ¦¬λ ννΈ
  - `this.setState({ responseType: item.value })`
  - μ΄μ  λ΄μ§ λͺ»ν λ°μ΄ν°λ₯Ό λ΄μλ€! π
- `fetch`ν  λ ν μ€μλ€:
  - 1οΈβ£ `fetch url`μ κ°μΈλ μ€κ΄νΈκ° λ κ° μλ€.
    - λͺ©λ°μ΄ν°μ©, μ€μ  νμ€νΈμ©μ λ³΅λΆνμ¬ μμ±νλ€ μκΈ΄ μ€μμλ€.
  - 2οΈβ£ `postman`μ λ±λ‘λ λ°μ΄ν°κ° μλ urlμμ λ°μ΄ν°λ₯Ό νΈμΆνλ€.
    - νλμ½λ©μΌλ‘ μ£Όμλ₯Ό κ³ μ νμ¬ νμ€νΈ νμ

### π³ μΈν΄ λμ§Έ μ£Ό νκ³  :

### π μν κ²:

- `π©βπ« class component`λ₯Ό μ¬μ©νκΈ°λ‘ ν κ²
  - λ§μ μ°¨μ΄μ λ€μ λͺΈμ λλ μ μμκ³ , μλ‘­κ³  μ΄λ ΅κΈ°μ κΎΈμ€ν λκΈ°λΆμ¬κ° λλ€.
  - κΎΈμ€ν TILμ μ°κ³  μκ³  μΆν΄κ·Ό μκ°μ λ³΅κΈ°νκ³  μλ€!
- `πββοΈ ν¨μ¨μ μΈ μ§λ¬Έ`
  - λͺ¨λμ μκ°μ κΈ. μ¬μμ μκ°λ κΈμ΄κΈ°μ μΆ©λΆν μλν΄λ³΄κ³ , λΈλ ₯ν ν κ°κ³½μ μΌλ‘ μ λ¦¬νμ¬ λ¬Όμ΄λ΄€λ€.
    - μλ₯Ό λ€μ΄, μ΄λ¬ν κΈ°λ₯μ κ΅¬ννλ €κ³  λΆλͺ¨, μμ μ»΄ν¬λνΈλ νμΈ νκ³  μ½μλ‘ νμΈ νλλ° λ λ²μ§Έ λΆν° μ°νμ§ μλλ€.

### πͺ μμ¬μ΄ κ²:

- `π°οΈ μκ° κ΄λ¦¬`
  - μΌμ μ μΈμΈνκ² μ§κ³  μ§ν νμ§λ§, μμΈμ μλ¬μ μ΄μλ‘ μΌμ μ΄ μ‘°κΈμ© λλ μ΄ λκ³  μλ€.
  - νΉν λΌμ΄λΈλ¬λ¦¬ CSS κ΅¬κ°μμ μκ°μ λ§μ΄ μμνλλ°, μμΌλ‘ λνμΌμ κΈ°λ₯ κ΅¬ν μ΄νμ νλ κ²μΌλ‘...

---

## <p align="center"> `Internship` π 12/26

### π antd table β checkbox

```jsx
//νμ°Έ μ°Ύμ input κ° λ°°μ΄μ λ£κΈ°!
state = {
  keys: [],
};

<Table
  columns={columns}
  dataSource={tagReadData.results}
  rowSelection={{
    type: "radio",
    selectedRowKeys: this.state.keys,
    onChange: this.onRowKeysChange,
  }}
  rowKey={record => record.id}
  onRow={record => ({
    onClick: () => {
      this.selectRow(record);
    },
  })}
/>;
```

- `keys`λ₯Ό λ°°μ΄λ‘ μ μΈ ν©λλ€.
- `rowselection={{ type: 'radio'}}`λ‘ λν΄νΈ κ°μ λ°κΏμ€λλ€.

### π Fetch!

```jsx
getTableApi = async ({ projectId, workspaceId, responseType }) => {
  console.log("table api ν΅μ  μμ!!!");
  const authToken = localStorage.getItem("auth_token");

  try {
    const response = await fetch(`url`, {
      method: "GET",
      headers: {
        Authorization: authToken,
        "client-server": "application/json",
      },
    });

    const tagReadData = await response.json();
    console.log(tagReadData.results);
    this.setState({ tagReadData });
  } catch (err) {
    console.log(err);
  }
};

const { selectedRowKeys, tagReadData } = this.state;
//λ λνλ κ³³μμ κ΅¬μ‘°λΆν΄ ν λΉμ ν΄μ£Όμ΄μΌν¨.
```

## <p align="center"> `Internship` π 12/27

```jsx
uploadTagCreate = async () => {
  const { workspaceId, projectId } = this.props;
  const { responseType, keyDataFromChild } = this.state;
  console.log(keyDataFromChild);
  await api({
    url: `url`,
    method: "post",
    headers: { "content-type": "application/json" },
    data: {
      tag_id: keyDataFromChild[0],
    },
  }).then(response => {
    const { data } = response;
  });
};
//200 OK π«‘
```

![200OK!](https://user-images.githubusercontent.com/110847597/209746568-7568e051-a34f-45fe-8922-6453cbd94f33.png)

### π axios

```jsx
//fetchλ‘ λ°μν  μ μλ μ€λ₯λ₯Ό λ°©μ§νκΈ° μνμ¬ axios νμ©
sortTagsApi = async () => {
  const { workspaceId, projectId } = this.props;
  const { responseType, schedulingTagList } = this.state;

  await api({
    url: `url`,
    method: "get",
    headers: { "content-type": "application/json" },
  }).then(response => {
    const { data } = response;
    this.setState({ schedulingTagList: data.results });
    // tagID : Num
  });
};
```

### π©βπ©βπ§βπ¦ μμμμ λΆλͺ¨λ‘ λ°μ΄ν° λ³΄λ΄κΈ°

```jsx
//parent
state = {
  keyDataFromChild: [],
};

uploadTagCreate = async () => {
  const { keyDataFromChild } = this.state;

  await api({
    url: `url`,
    method: "post",
    headers: { "content-type": "application/json" },
    data: {
      tag_id: keyDataFromChild[0],
    },
  }).then(response => {
    const { data } = response;
  });
};

const getKeyData = value => {
  this.setState({ keyDataFromChild: value });
};

//child
state = {
  keys: [],
};

onRowKeysChange = keys => {
  this.setState({ keys });
  const { getKeyData } = this.props;
  getKeyData(keys);
};
```

### π‘ μμλ°©νΈ λ‘μ§

```jsx
const { invalid } = this.props;
// invalidλ form fieldμ κ°λ€μ μ²΄ν¬νκ³  μλ‘λ λ²νΌμ μ μ΄νκ³  μλ€
// λλ¬΄ κΉμ νλ‘­μ€μΈ κ΄κ³λ‘ μ μΆμ²λ₯Ό μ°Ύμ§ λͺ»νλ€.
// κ·Έλ¬νμ¬ μλμ μμ λ°©νΈ λ°©μμΌλ‘ ν΄κ²°..

const { invalidCheck: true } = this.state
// invalidμ μμλ°©νΈμΌλ‘ μ¬μ©ν  μλ‘μ΄ μ€νμ΄νΈλ₯Ό μ μΈ

const getKeyData = value => {
  this.setState({ keyDataFromChild: value });
  this.state.keyDataFromChild !== []
    ? this.setState({ invalidCheck: false })
    : this.setState({ invalidCheck: true });
};
// μμ μμ± ν, μμ μμμμ λ°μμ¨ keysκ°μ λ΄μ μ€νμ΄νΈλ₯Ό μ¬μ©
// keyDataFromChildκ° λΉ κ°μ΄ μλλΌλ©΄ (μ¦, keyκ°μ΄ λ°°μ΄μ μλ€λ©΄)
// invalidCheckμ κ°μ falseκ° λμ΄ disabledλ₯Ό ν΄μ ν©λλ€.
// TMI λμ μ΅μ  μΌν­
<BlueButton
  type="submit"
  className="button_uppercase"
  disabled={invalid || invalidCheck}
  onClick={onClickButton}
>
```

### π³ μ±μ₯ ν¬μΈνΈ :

- console.logλ₯Ό μ°μΌλ©° μ΄λ€ λ¬Έμ κ° μλμ§ νμΈ!
- νΌμμ ν΄λΌ μ μλ κ²λ€μ΄ λ§μμ§κ³  μλ€. π₯Ή
  - fetchλ νΌμμ μ²μ².. 200 ok μ§λ¦Ώ
- μμμμ λΆλͺ¨λ‘ λκΈ°κΈ° κΉμ§ μ±κ³΅
- μμλ°©νΈ λ‘μ§λ μμ±νλ€.
  - λλ... μ μ§λ³΄μκ° μ½κ² μ½λλ₯Ό μΈκ²μ΄λ€.
  - λμκ°λ μ½λ λ§κ³ , μ μ§μ¬μ§ μ½λλ₯Ό μ°μ.

## <p align="center"> `Internship` π 12/29

- `retraining_batch` λΌλ©΄ λΆν  νμ¬ `retraining`,`batch_prediction`λ‘ λ λ
- νκ·Έκ° νλμΌ λ `matchingTag` νλμ λ°μ€λ‘ λ λνκΈ°
- μ²μμ `for`μ μ¬μ©νμ¬ λ§€ν νλ € νμ§λ§, μ‘°κ±΄μ΄ 2κ°μ§κ° λκΈ° λλ¬Έμ μλμ μ½λλ‘ μμ .

```jsx
state = {
  matchingTag: "",
  // νλμ νκ·ΈμΌ κ²½μ°μ μ€νμ΄νΈ
  matchingTags: "",
  retrainingTag: "",
  // λκ°μ§ κ²½μ° μΌ λ, retrainingTag κ°μ λ΄λ κ³³
  batchPredictionTag: "",
  // λκ°μ§ κ²½μ° μΌ λ, batchPredictionTag κ°μ λ΄λ κ³³
};

mapApiData = () => {
  const { scheduleDetails } = this.props;
  const scheduleType = scheduleDetails.type;
  const scheduleTags = scheduleDetails.tags;

  if (scheduleType === "retraining_batch") {
    scheduleTags.map((el, i) => {
      if (el.type === "retraining") {
        this.setState({ retrainingTag: el.tag });
      }
      if (el.type === "batch_prediction") {
        this.setState({ batchPredictionTag: el.tag });
      }
    });
  } else {
    scheduleDetails.map((el, i) => {
      this.setState({ matchingTag: el.tag });
    });
  }
};
```

```jsx
<div className="ant-form-item-control-wrapper">
  {scheduleDetails.type === "retraining_batch" ? (
    //λ¦¬μ‘νΈμμ μΌν­ μ‘°κ±΄μ μ£Όμ΄ λ λλ§ ν  μ μμ
    <>
      <input
        className="tagInput"
        name="name"
        type="text"
        placeholder={this.state.retrainingTag}
        readOnly
      />
      <input
        className="tagInput"
        name="name"
        type="text"
        placeholder={this.state.batchPredictionTag}
        readOnly
      />
    </>
  ) : (
    <input
      className="tagInput"
      name="name"
      type="text"
      placeholder={this.state.matchingTag}
      readOnly
    />
  )}
</div>
```

## <p align="center"> `Internship` π 12/27

```jsx
if (Number.isInteger(keepCount) === false) {
  inputValue = Math.round(keepCount);
}
```

- total λ°μ΄ν° μ μ μ¬μ©μκ° μλ ₯νλ κ°μ μ°μ°νμ¬ λ¨λ κ°μ λ λλ§ ν΄μΌνλ€.
  - κ°λ¨ν΄ λ³΄μμ§λ§ μ‘°κ±΄μ΄ μ¬λ¬κ°μ§κ° νμνλ€.
  - μμμ¬μΌ νλ€ β μμμ  μ΄λΌλ©΄ λ°μ¬λ¦Ό νλ€
    - `isInteger`μ νμ©νμ¬ λ‘μ§μ μ§°μ§λ§ μλνμ§ μλλ€.
    - `while`μ μ¬μ©νμ¬ κ°μ΄ μ°Έμ΄λ©΄ κ³μ μ‘°κ±΄μ μννκ² ν μ§ κ³ λ―Όμ΄λ€.
  - μ§μΈ κ°μ΄ κ°μ§ λ°μ΄ν° κ°λ³΄λ€ ν΄ μ μλ€

### π³ μΈν΄ μμ§Έ μ£Ό νκ³  :

### π μν μ 

1. λΌμ΄λΈλ¬λ¦¬μ λν μ΄ν΄λ up
1. κ°λ°μμ μλ¬΄ νκ²½ μ΄ν΄
1. μ»΄ν¨ν μ¬κ³ λ ₯ up
1. κ²μνκ³  μ§λ¬Ένλ μ©κΈ°

### πͺ μμ¬μ΄ μ 

1. λκ° λ΄λ μ΄ν΄νκΈ° μ¬μ΄ μ½λλ₯Ό μμ±νλ κ²μ΄ μμ§μ λΆμ‘±νλ€.
1. λ¦¬ν©ν λ§ ν μ½λλ₯Ό λ³΄λ©΄ λ `μ... μ΄λ κ² μ μ κ±Έ` μ΄λΌλ μμ¬μ

### π μμΌλ‘μ λ€μ§

1. λ μ κ·Ήμ μΌλ‘ μ§λ¬Ένκ³ , κ³ λ―ΌνκΈ°
1. μ λμ μΈ μ½λ μμ± μκ° λλ¦¬κΈ°!

   - νλ‘ μλ μκ°μ μ€μ΄λ κ²

1. κΈ°λ‘κ³Ό νκ³ λ₯Ό ν΅ν λ³΅μ΅
   <img width="427" alt="αα³αα³αα΅α«αα£αΊ 2023-01-02 αα©αα₯α« 11 09 22" src="https://user-images.githubusercontent.com/110847597/210249410-a8992621-ad6f-4bb7-a969-85217e67360f.png">

## <p align="center"> `Internship` π 1/2

## β¨ λ©λ΄ν­ CSS λ°κΎΈκΈ°

```jsx
className={classNames('tab-menu__link', {
          'tab-menu__link_active': type === 'retrainedModels',
        })}
```

### π useEffect + state μλ°μ΄νΈ

```jsx
useEffect(() => {
  if (createCount >= predictionKeepModel) {
    setPreDeleteCount(createCount - predictionKeepModel);
  }
}, [createCount, predictionKeepModel]);
//useEffectμ μμ‘΄μ± λ°°μ΄μ νμ© ν ui λ λ

<input
  type="number"
  className="delQuality"
  placeholder={0}
  id="delQuality"
  step={1}
  min={0}
  max={createCount}
  value={retrainingKeepModel}
  onChange={e => setRetrainingKeepModel(Number(e.target.value))}
/>;
```

### π― `Input`

- `step={1}`μ λ£μΌλ©΄ 1μ© μ»€μ§λ€.
- `max={createCount}`
- inputμ νμ΄νλ₯Ό κ³μ λ³΄μ¬μ£Όλ λ°©λ²μ `opacity: 1`

```jsx
input[type='number']::-webkit-inner-spin-button,
input[type='number']::-webkit-outer-spin-button {
    opacity: 1;
}
```

### π μ‘°κ±΄λΆ λ λ: scheduleType νμμ λ°λ₯Έ

```jsx
//scheduleMethodTob.js
const scheduleType = scheduleDetails.type;

//index.js
{
  scheduleType && scheduleType.includes("prediction") ? (
    <div className="studio-container_auto_del">
      <div className="title-wrap">
        <span className="title-wrap-text">Enable Prediction Auto-delete</span>
      </div>
      {predictionAutoDeletion && (
        <ScheduleAutoDeleteViewOption
          prediction={scheduleType.includes("prediction")}
          createCount={schedulingOptions.createCount}
          predictionKeepModel={predictionKeepModel}
          setPredictionKeepModel={setPredictionKeepModel}
        />
      )}
    </div>
  ) : (
    <></>
  );
}
```

### π antd table CSS

```jsx
 {
    title: 'CREATED',
    dataIndex: 'created_at',
    key: 'created_at',
    render: text => getFormattedDateTimeTable(text),
    className: 'tag-columns-custom',
  }
```

### π³ μ±μ₯ ν¬μΈνΈ :

- ν CSSλ₯Ό μ»€μ€ν νλ λμ€, μ€λ₯λ₯Ό λ§λ¬λ€.
- ν΄λμ€λ€μμ κ³΅μ νκ³  μμ΄ μ μ²΄ cssμ μ μ©μ΄ λλ κ².
- `row`λ₯Ό μμ νμ§ μκ³  `column`μ μμ νλ λ°©λ²μΌλ‘ λ³κ²½ ν μ±κ³΅!
- λΌμ΄λΈλ¬λ¦¬ λͺμΈλ₯Ό νμΈνμ¬ μμ μ½λ 4λ²μ§Έ μ½λ `className:'tag-columns-custom'`λ‘ μμ±νμ¬ μ΄μ μμ  ν¨!
  - `key`λ₯Ό νμ©νμ¬ dateμ ν¬λ§· λ³νλ μλ£
  - λΌμ΄λΈλ¬λ¦¬λ μ΄λ ΅μ§λ§ λ μ½λ€. π₯²
- κ²μκ³Ό μ§λ¬Έλ μ½λ©μ΄λ€.
- μΌλ§ μλ¨μ λ§λ¬΄λ¦¬μ `QA`λ₯Ό μ λ§λ¬΄λ¦¬ ν  κ²

## <p align="center"> `Internship` π 1/3

### π§βπ Hot Fix: MAXλ μλ ₯κ°κ³Ό 6κ° μ¬μ΄

```jsx
//Parent
const [retrainingKeepModel, setRetrainingKeepModel] = useState(1);
//child
const MAX_KEEP = 6;
const possibleMax = Math.min(MAX_KEEP, createCount);
//...
<input
  type="number"
  className="delQuality"
  placeholder={1}
  id="delQuality"
  step={1}
  min={1}
  max={possibleMax}
  value={retrainingKeepModel}
  onChange={e => setRetrainingKeepModel(Number(e.target.value))}
/>;
```

### `Math.min()` [MDN Math.min()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/min)

```jsx
Math.min([value1[, value2[, ...]]])
```

> Math.min() ν¨μλ μ£Όμ΄μ§ μ«μλ€ μ€ κ°μ₯ μμ κ°μ λ°νν©λλ€.

### `yarn build`

> "yarn build Bundles the app into static files for production." from Create React App by MAD9135.
>
> > https://stackoverflow.com/questions/54693223/what-does-yarn-build-command-do-are-npm-build-and-yarn-build-similar

### π³ μ±μ₯ ν¬μΈνΈ :

- `μλ λ§νΌ κ°λμ±μ΄ μ’μμ§λ μ½λ`
  - μ²μ μμ κΈ°λ₯μ κ΅¬νν  λ `if (κ°μ§κ° <= μλ ₯κ°) {...} if(κ°μ§κ°.μ μκ° μλ λ)` λ± λ³΅μ‘ν λ‘μ§μ μμ±νλ€. (μ½ 7μ€)
  - μμ°μ€λ½κ² whileκ³Ό μλ μμ μ λν΄μ κ³ λ―Όμ΄ κΉμ΄μ‘κ³ , κ°λ¨ν μμ μ¬ν­μ΄μλλ° λ³΅μ‘νκ² λκ»΄μ‘λ€.
  - νμ§λ§ Inputμ `min`, `max`, `step`μ νμ©νμ¬ μ½λλ λ κ°κ²°ν΄μ‘λ€.
  - λν `const possibleMax = Math.min(MAX_KEEP, createCount)` μ½λλ₯Ό μμ±νμ¬ `μ μκ° μλ λ, μλ ₯κ°μ΄ κ°μ§ κ° λ³΄λ€ ν΄ λ` λ κ°μ§ μ‘°κ±΄μ ν μ€λ‘ ν΄κ²°νμλ€. (μ μΈκΉμ§ 3μ€)
  - _Kepp It Simple, Stupid_ μ κΈ°μ΅νλ©° μ€λλ μ΄μ¬ν κ³΅λΆλ₯Ό!

---

## <p align="center"> `Internship` π `Retrospective`

### 4L: Liked, Learned, Lacked, Longed for

- π μ’μλ κ²(Liked)
  - νμ μ½λλ₯Ό μ§μ  μ²΄ν ν΄ λ³Έ κ²
  - λΌμ΄λΈλ¬λ¦¬λ₯Ό μ¬μ© ν κ²
  - ν΅μ μ ν΅νμ¬ λ°°ν¬κΉμ§ μ§ν ν κ²
- π λ°°μ΄ κ²(Learned)
  - λ¦¬μ‘νΈ νμ΅
  - μ€λ¬΄μ ν΅μ (postman, μΈν°νμ΄μ μ°Έκ³ μ, κΈ°νμ νμ©)
    - μλ₯Ό λ€μ΄, Backμκ² μ μ‘ν΄μΌ ν  λ°μ΄ν°κ° `console.log`μ μ°μ΄μ λ³΄μ΄μ§ μλλ€λ©΄, νλ‘ νΈμμ μ μνλ κ²μ΄ μλ μμ²­μ΄λ μ§λ¬Έμ ν΅νμ¬ λ°μ΄ν° μ μ‘ λ°©μμ λΌμν΄μΌν¨
- π¦ λΆμ‘±νλ κ²(Lacked)
  - λ¦¬μ‘νΈ νμ΅
  - λ°μ΄ν° ν΅μ μ νμ΄λ°
- π― λ°λΌλ κ²(Longed for)
  - μ κ·Ήμ μΌλ‘ μ§λ¬Ένκ³ , κ²μνλ κ³Όμ μμ λ§μ΄ λ°°μ λ€. μ΄μ μ νλ μ€μλ₯Ό λ€μ νμ§ μλλ‘ λ³΅μ΅νκ³  λ λΈλ ₯νκΈ°!
  - μ§§μ 4μ£Όλμ μ ν΄μ£Όμκ³  λ§μ΄ λ°°μΈ μ μμ΄ λλ¬΄ κ°μ¬νμ΅λλ€. :) κ°λ°μ§±μ΄ λμ΄ λ€μ λ§λμ..

---

E.O.D
