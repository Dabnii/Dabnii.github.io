# <p align="center"> 🤙 JavaScript Promise </p>

## `Promise` = `Asynchronous`

- 내장된 JavaScript의 object `Asynchronous Operation`

### 🤔 비동기 `Promise` 사용하는 이유

- 💻 `통신`은 성공, 실패 여부 그리고 언제 종료될지 예측하기 어렵기 때문에 비동기 처리해야 합니다.
  - [📎 Why is JavaScript called synchronous? -My TIL](https://github.com/Dabnii/Dabnii.github.io/blob/main/Computer%20Science/JavaScript%20Sync.md)
- status code는 성공과 실패에 따라 코드 분류가 명확하기 때문에 response는 status code에 따라 분기 처리하는 게 좋습니다.

### 🚏 `Throw`, `try`, `Catch`

- `try` 문은 코드블록의 오류를 테스트할 수 있다.
- `catch` 문은 오류를 처리하게 해준다.
- `throw` 문은 사용자 지정 오류를 생성할 수 있다.
- `.then()`는 `Promise`를 리턴하고 `두 개의 콜백 함수`를 `인수`로 받는다.

## 1️⃣ State

- 프로세스가 수행중인지, 완료, 실패, 성공 여부
  1. `pending`
  2. `fulfilled` or `rejected`

## 2️⃣ Producer & Consumer

- `Producer`: 원하는 데이터를 제공하는 사람
- `Consumer`: 제공 된 데이터를 사용하는 사람

## <p align="center">🏃‍♀️ Producer </p>

```jsx
//When new Promise is created, the executor runs automatically!
const promise = new Promise (resolve, reject) => {
// executor 라는 callback 함수가 바로 실행 됨
// doing something heavy work()
// synchronous -> blocking
// Network, read files -> 비동기로 처리하는 것을 추천
console.log('doing something')
setTimeout(()=> {
	resolve('elle')
}, 2000);
// 2초 대기 후 callback 함수인 'elle' 도출함
// 즉,이 로직에서 setTimeout은 promise임
// Promise라는 producer 생성완료
}
```

### 💡 주의사항

- 생성되는 순간 바로 실행 되는 특성이 있음
- `promise를` 만들 때 `executor가` 실행 됨
  - 불필요한 네트워크가 발생 됨

## <p align="center">🚏 Consumer</p>

1. `.then()`
2. `.catch()`
3. `.finally()`(new!)

   ```jsx
   promise.then(value => {
     console.log(value); // elle
   });
   ```

4. Promise라는 변수를 만들고 promise의 값이 정상적으로 받아`온다면`
5. `then` `그러면` value에 값을 받아와서 원하는 기능을 수행하는 callback 함수 전달
6. `resolve(’elle’)`라는 값이 value로 들어옴

## <p align="center">💡 `Then!`

```jsx
// .then() 메서드 문법
.then(function onFullfilled, [function onRejected])
```

- `.then()` Promise를 처리할 수 있는 method
- Promise return 하고 두 개의 콜백함수를 인자로 받음
  - ☝️ Promise가 이행 되었을 때 (성공)
  - ✌️ 다른 하나는 거부했을 때 (실패)
- `Chaining` 가능
  - 첫번째 `.then()` 에서 반환 된 값을 두 번째 `.then()` 에서 이어서 처리 가능
- `reject는` 네트워크 통신 중 오류를 처리할 때 사용

```jsx
const promise = new Promise (resolve, reject) => {
		console.log('doing something')
			setTimeout(()=> {
				//resolve('elle')
				reject(New Error('no network'))
				//보통 reject는 error 라는 오브젝트를 통해 값을 전달 함
				//에러 클래스는 자바스크립트 내의 내장 오브젝트임
				//에러를 명확히 명시해줘야함
}, 2000);
//Promise가 정상적으로 잘 수행 되어서 마지막에 최종적으로 리졸브 라는 콜백 함수를 통해서 전달한 `resolve(’elle’)` 값이 .then의 value로 파라미터로 전달 되어 들어오게 됨
```

![Error img](https://user-images.githubusercontent.com/110847597/212047160-9f657980-1a54-4b08-9b94-71e7e31e2716.png)

- 🚨 `Uncaught SyntaxError:`
  - `.catch()` 구문을 추가 하여 에러핸들링을 진행하기

```jsx
const promise = new Promise (resolve, reject) => {
		console.log('doing something')
			setTimeout(()=> {
				reject(New Error('no network'))
    }, 2000);

promise
.then((value) => {
	console.log(value);
})

.catch(error => {
	console.log(error);
});
```

- `catch` 함수를 이용하여 에러 발생 시 어떻게 처리할 것인지 콜백 함수를 등록해주면 됨

## <p align="center">⛓️ `Chaining`</p>

- `Promise`의 `.then()`을 호출하게 되면, then은 결국 같은 promise를 리턴하기 때문에, 그 리턴된 promise의 catch를 다시 호출할 수 있음

  - 아래와 같은 동작 원리

  ```jsx
  {
    const result = students
      .map(student => student.score)
      .sort((a, b) => b - a)
      .join();
    console.log(result);
  }
  ```

1. then을 호출하게 되면
2. promise 리턴
3. 리턴 된 promise 에 catch를 등록

### 💡`resolve` & `reject`

- `resolve`: 🙌 성공 했을 때
- `reject`: 🚨 실패 했을 때

### 🤓 How to work

- 프로미스 오브젝트를 만들 떄 비동기적으로 수행하려는 기능 코드를 작성 후, 성공했다면 `resolve`호출
- 실패했다면 에러를 전달함
- `then`, `catch` 를 받아와서 우리가 원하는대로 처리해주기

### 🙌 `finally` (New!)

- 성공,실패 상관 유무 없이 무조건 마지막에 호출 됨
- 어떤 기능을 마지막으로 수행하고 싶을 때 `finally` 사용

  ```jsx
  const promise = new Promise (resolve, reject) => {
          console.log('doing something')
              setTimeout(()=> {
                  reject(New Error('no network'))
  }, 2000);

  promise.then((value) => {
      console.log(value);
  })

  .catch(error => {
      console.log(error);
  });

  .finally(()=> {
      console.log('finally')
  });
  ```

### 💡 활용: `.then()` 분기처리

```jsx
fetch("로그인 API", {
  method: "post",
  body: JSON.stringify({
    id: "qwerty",
    password: "123456",
  }),
})
  .then(response => {
    if (response.ok === true) {
      return response.json();
    }
    throw new Error("에러 발생!");
    //reponse.ok가 true가 아닐 경우 error를 throw
  })
  .catch(error => console.log(error))
  //throw된 error를 받아서 console에 출력
  .then(data => {
    //통신에 성공해서 JSON을 객체로 변환했다면, 변환된 객체를 활용해서 분기 처리할 수 있습니다.
    if (data.message === "login success") {
      localStorage.setItem("TOKEN", data.token);
      alert("로그인 성공");
    } else {
      alert("로그인 실패");
    }
  });
```

## <p align="center">💯 오류를 잘 처리하자!</p>

```jsx
const getHen = () =>
  new Promise((resolve, reject) => {
    setTimeout(() => resolve("🐓"), 1000);
  });

const getEgg = hen =>
  new Promise((resolve, reject) => {
    setTimeout(() => reject(new Error(`error! ${hen}=> 🥚`)), 1000);
  });

const cook = egg =>
  new Promise((resolve, reject) => {
    setTimeout(() => resolve(`${egg} => 🍳`), 1000);
  });

getHen()
  .then(getEgg) // hen=>getEgg(hen)
  .catch(error => {
    // 에러 핸들링
    return "🍞";
  })
  .then(cook)
  //egg => cook(egg)
  .then(console.log) // meal => console.log(meal)
  .catch(console.log);
```

---

출처:

- [자바스크립트 12. 프로미스 개념부터 활용까지 JavaScript Promise | 프론트엔드 개발자 입문편 (JavaScript ES6)](https://www.youtube.com/watch?v=JB_yU6Oe2eE&t=1218s)
- [JavaScript Errors - Throw 와 Try to Catch](http://jun.hansung.ac.kr/CWP/Javascript/JavaScript%20Errors%20Try%20Catch%20Throw.html)
- [프라미스와 에러 핸들링](https://ko.javascript.info/promise-error-handling)
