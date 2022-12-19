## <p align="center"> `Internship` 📆 12/12

### ⏰ Setting time
1. install nvm: [https://github.com/creationix/nvm](https://github.com/creationix/nvm)
    ```jsx
    $ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash	
    ```    
2. install node stable version: `nvm install stable`
3. install yarn: `npm install -g yarn`
    ```jsx
    $ nvm install vNN.NN.N
    //사용하고자 하는 버전 으로 변환 합니다
    ```  
4. install requirements: `yarn install`
5. create `.env` according to `.env.example`
6. start project `yarn start`

## 📍 NVM 버전을 고정하기
1. 재부팅 후  접속시, 터미널의 nvm 버전이 바뀌는 것을 방지 하기 위함입니다.
1. 최신 버전이 아닌 특정 버전을 써야하는 경우에 필요합니다.

    ```jsx
    $ nvm list
    //현재 nvm 버전을 확인
    ```

    ```jsx
    $ nvm use v14
    //원하는 버전으로 변경 (임시적)
    ```

    ```jsx
    $ nvm alias default v14
    //원하는 버전으로 디폴트 값 고정 
    ```

    <img width="856" alt="재부팅" src="https://user-images.githubusercontent.com/110847597/207327527-45b7bedb-a64f-46bc-80cb-bd6415532f3b.png">
    > 가끔은 터미널도 재부팅이 필요하다 

### 🛥 Onboarding 
1. 깃허브 세팅이 완료 되었다면
1. 깃허브 `package.json` 을 둘러보며 사용되는 것들 확인하기!

🌳 성장 포인트

1.`yarn` `npm` 차이 학습
1.`redux`학습 필요!


---

## <p align="center"> `Internship` 📆 12/13


## 🛥 Onboarding 🌊🌊🌊

### 👀 미리 둘러 볼 것!

- [x] `packagelock.json`의 의존선 확인
- [x] `Git branch` 확인
- [x] `Pull Request` 컨벤션 확인
- [X] `Commit message` 컨벤션 확인

---

## <p align="center"> `Internship` 📆 12/16

### 📍 Class Components

```jsx
// App.js

import React from 'react';

class App extends React.Component {
  render() {
    return <h1>This is Class Component!</h1>;
  }
}
export default App;
```
> 클래스 컴포넌트에서는 위와 같이 반드시 render() 메서드가 있어야 하고, 그 안에서 화면에 보여줄 JSX(Javascript Syntax eXtension) 를 반환합니다. state 및 lifecycle(라이프사이클) API를 통해 관련 기능을 사용할 수 있습니다.


```jsx
    console.log(this.props);
    console.log(columns);
//위의 두가지로 알아낸 데이터 구조
```

🌳 성장 포인트 :

- 클래스 컴포넌트를 사용
    - 학습을 위하여 class component를 사용 중, 기존의 작업되어있는 프로젝트도 클래스 컴포넌트로 구성되어 있다.
- `console.log`를 찍어보며 어떤 데이터가 들어오는지 확인해 보는 습관을 가지자.
- `this`의 컴백

---

## <p align="center"> `Internship` 📆 12/19

### 📚 `antd table` library
엣헴... [📎 antd table: 공식 사이트](https://ant.design/components/table)

> 어쩐지... props로 어떤 값을 넣어도 오류가 났다.<br>
> 당연함, 라이브러리의 명세를 확인 했어야했다.<br>
> 오늘의 교훈, package-lock.json을 열심히 확인하고... 검색을 꼭 해보자.<br>
> 둘쨋날... 사수께서 확인해보라던게 이런 라이브러리가 있다는 걸 보란거였다. 하지만 아는만큼 보인다고 응애인 나는 몰랐다. antd를 자체적으로 만든건 줄 알았다.. 오늘이라도 알아서 다행이다.

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

공식문서를 따라 작성하면 짜잔, 이렇게 이미지가 뜬다. 👏👏👏
![after table screenshot](https://user-images.githubusercontent.com/110847597/208448995-d5fbacc8-0d0d-4702-bcb1-a7876419f791.png)

내일 할 일: 

- [ ] SCSS를 수정하기, 커밋하기

<br>

###  <p align="center">📛 `This.state?` `This.Props?`
> 현업 코드를 보다보니, this가 정말 많이 쓰이고 있었다.
> 어디서 호출하느냐에 따라 바인딩 되는것이 결정된다는데 더 적극적으로 공부를 해야겠다.

📝 This.state

1. `this.state` : state를 해당 컴포넌트에서 만들 때

🧚‍♀️ This.props

1. `this.props` : 부모 컴포넌트나, 리덕스에서 `해당 컴포넌트에 주입` 할 때

🌳 성장 포인트 :

- 내가 어렵다면, 어려운 것이 맞다! 
    - 그때마다 물어보고 또 알아보자!
- 라이브러리를 많이 써보고 친숙해 져야겠다.
- `this` 공부도 잊지 말자!

## <p align="center"> `Internship` 📆 12/20
