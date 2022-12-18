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
