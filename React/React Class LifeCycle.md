# <p align="center"> π§’ React Class component

<img width="1176" alt="react-lifecycle-methods-diagram" src="https://i.imgur.com/cNfpEph.png">

> μΆμ² [react-lifecycle-methods-diagram](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

## πβ»οΈ LifeCycle

- `LifeCycle` Method λ νκ΅­μ΄λ‘ `μλͺμ£ΌκΈ° λ©μλ` λΌκ³  λΆλ¦λλ€. μλͺμ£ΌκΈ° λ©μλλ μ»΄ν¬λνΈκ° λΈλΌμ°μ μμ λνλκ³ , μλ°μ΄νΈλκ³ , μ¬λΌμ§κ² λ  λ νΈμΆλλ λ©μλλ€ μλλ€. μΆκ°μ μΌλ‘ μ»΄ν¬λνΈμμ μλ¬κ° λ¬μ λ νΈμΆλλ λ©μλλ μμ΅λλ€.

  > [μΆμ²](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

- νμ ν¨μν μ»΄ν¬λνΈλ₯Ό μ¬μ©ν  λλ μλͺμ£ΌκΈ°λ₯Ό `useEffect` λ₯Ό μΌμλ€.
- ν΄λμ€μμ `useEffect`λ₯Ό μ¬λ©΄ μ€λ₯κ° λ°μνλ€.π© (λΉμ°ν¨)

  - <img width="529" alt="hook error" src="https://user-images.githubusercontent.com/110847597/209439247-53238109-44b3-4f61-a7d6-2091e8c65a17.png">

| &#32;          | Class Component        | Function Component |
| -------------- | ---------------------- | ------------------ |
| μμ± λ  λ     | `componentDidMount`    | `useEffect`        |
| μλ°μ΄νΈ ν  λ | `componentDidUpdate`   | `[dep]`            |
| μ κ±°ν  λ      | `componentWillUnmount` | `cleanup`          |

<br>

## <p align="center">π Class component</p>

### πΆβ `componentDidMount`

- μμ± λ  λ

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

### π’β¨ `componentDidUpdate`

- μλ°μ΄νΈ ν  λ

### ππ `componentWillUnmount`

- μ κ±° ν  λ

## <p align="center">βοΈ Function component</p>

### β¨ `useEffect`

- μμ‘΄μ± λ°°μ΄μ λ°μ΄ν°κ° μλ°μ΄νΈ λ  λ λ§λ€
- μμ‘΄μ± λ°°μ΄μ `[]`λ‘ μ€λ€λ©΄ λ§μ΄νΈ λ  λλ§ μ€ν

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

1. Mock dataλ₯Ό μ¬μ©νμ¬ νλ‘ νΈμμ μμ²΄μ μΌλ‘ λͺ©λ°μ΄ν°λ₯Ό μ μ
1. β¨ λΈλΌμ°μ μ λ§μ΄νΈ λμ λ§μ uiλ₯Ό κ·Έλ¦¬λλ‘ `fetch`μ¬μ©
1. `useEffect`μμμ `fetch` λ©μλ νΈμΆ
1. `stateμ μ μ₯`ν΄μ νμν λ°μ΄ν°λ₯Ό κ°μ Έλ€κ° `UI`λ‘ κ·Έλ €λ

---

μΆμ²:

- [Class component DidMount, DidUpdate, WillUnmount](https://velog.io/@qusehdgns/React-React-Hooks%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-componentDidMount-componentDidUpdate-componentWillUnmount-%EA%B5%AC%ED%98%84)

- [25. LifeCycle Method](https://react.vlpt.us/basic/25-lifecycle.html)

- μΆμ² [react-lifecycle-methods-diagram](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)
