# <p align="center"> 🧢 React Class component

<img width="1176" alt="react-lifecycle-methods-diagram" src="https://i.imgur.com/cNfpEph.png">

> 출처 [react-lifecycle-methods-diagram](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

## 🔌♻️ LifeCycle

- `LifeCycle` Method 는 한국어로 `생명주기 메서드` 라고 부릅니다. 생명주기 메서드는 컴포넌트가 브라우저상에 나타나고, 업데이트되고, 사라지게 될 때 호출되는 메서드들 입니다. 추가적으로 컴포넌트에서 에러가 났을 때 호출되는 메서드도 있습니다.

  > [출처](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

- 평소 함수형 컴포넌트를 사용할 떄는 생명주기를 `useEffect` 를 썼었다.
- 클래스에서 `useEffect`를 쉬면 오류가 발생한다.😩 (당연함)

  - <img width="529" alt="hook error" src="https://user-images.githubusercontent.com/110847597/209439247-53238109-44b3-4f61-a7d6-2091e8c65a17.png">

| &#32;          | Class Component        | Function Component |
| -------------- | ---------------------- | ------------------ |
| 생성 될 때     | `componentDidMount`    | `useEffect`        |
| 업데이트 할 때 | `componentDidUpdate`   | `[dep]`            |
| 제거할 떄      | `componentWillUnmount` | `cleanup`          |

<br>

## <p align="center">📚 Class component</p>

### 👶➕ `componentDidMount`

- 생성 될 때

```jsx
class App extends Component {

     this.state = {
          data: []
     }
    componentDidMount() {
        fetch("/api/data").then(
            res => this.setState({...this.state, data: res.data})
        )
    }
    render() {
        return (
            <>
                {this.state.data.map( d => <div>{d}</div>)}
            </>
        )
    }
}
```

### 📢✨ `componentDidUpdate`

- 업데이트 할 때

### 🔌🔚 `componentWillUnmount`

- 제거 할 떄

## <p align="center">⚙️ Function component</p>

### ✨ `useEffect`

- 의존성 배열의 데이터가 업데이트 될 때 마다
- 의존성 배열을 `[]`로 준다면 마운트 될 때만 실행

  ```jsx
  import React, { useEffect, useState } from "react";

  const user =() => {
      useEffect(()=> {
      fetch("/data/useInforList.json")
      .then((response)=> response.json())
      .then((result)=> setUserInforList(result)
      }, []);

  const [userInforList, setUserInforList]= useState([]);
  return (
  ...
  <div> User
          {userInforList.map((userInfor)=> {
       return(<ul>
               <li>{userInfor.name}</li>
               <li>{userInfor.eamil}</li>
               <li>{userInfor.number}</li>
               </ul>
       )})};
     ...
   )
  }
  ```

1. Mock data를 사용하여 프론트에서 자체적으로 목데이터를 제작
1. ✨ 브라우저에 마운트 되자 마자 ui를 그리도록 `fetch`사용
1. `useEffect`안에서 `fetch` 메서드 호출
1. `state에 저장`해서 필요한 데이터를 가져다가 `UI`로 그려냄

---

출처:

- [Class component DidMount, DidUpdate, WillUnmount](https://velog.io/@qusehdgns/React-React-Hooks%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-componentDidMount-componentDidUpdate-componentWillUnmount-%EA%B5%AC%ED%98%84)

- [25. LifeCycle Method](https://react.vlpt.us/basic/25-lifecycle.html)

- 출처 [react-lifecycle-methods-diagram](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)
