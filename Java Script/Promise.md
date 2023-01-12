# <p align="center"> 🤙 JavaScript Promise 🏗️ ... </p>

## `Promise` 비동기

- 내장된 JavaScript의 object Asynchronous Operation

# <p align="center">🤙 Promise</p>

## 1️⃣ State

- 프로세스가 수행중인지, 완료, 실패, 성공 여부

## 2️⃣ Producer & Consumer

- `Producer`: 원하는 데이터를 제공하는 사람
- `Consumer`: 제공 된 데이터를 사용하는 사람

## 🚦 state:

1. pending
2. fulfilled or rejected

## <p align="center">🤙 promise </p>

## 🏃‍♀️ Producer

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
- promise를 만들 때 executor가 실행 됨
- 불필요한 네트워크가 발생 됨

## 🚏 Consumer:

1. `then`
2. `catch,`
3. `finally`(new!)

   ```jsx
   promise.then(value => {
     console.log(value); // elle
   });
   ```

4. Promise라는 변수를 만들어서 promise의 값이 정상적으로 받아온다면
5. `그러면` value에 값을 받아와서 원하는 기능을 수행하는 callback 함수 전달
6. `resolve(’elle’)`라는 값이 value로 들어옴

### 💡 `Then!`

- Promise가 정상적으로 잘 수행 되어서 마지막에 최종적으로 리졸브 라는 콜백 함수를 통해서 전달한 `resolve(’elle’)` 값이 then.의 value로 파라미터로 전달 되어 들어오게 됨

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
```

![Error img](https://user-images.githubusercontent.com/110847597/212047160-9f657980-1a54-4b08-9b94-71e7e31e2716.png)

- 🚨 Uncaught SyntaxError:
  - catch 구문을 추가 하여 에러핸들링을 진행해 주면 됨

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

- Promise의 then을 호출하게 되면, then은 결국 같은 promise를 리턴하기 때문에, 그 리턴된 promise의 catch를 다시 호출할 수 있음
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

- 프로미스 오브젝트를 만들 떄 비동기적으로 수행하려는 기능 코드를 작성 후, 성공했다면 resolve호출
- 실패했다면 에러를 전달함
- then, catch 를 받아와서 우리가 원하는대로 처리해주기

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

---

출처:

[자바스크립트 12. 프로미스 개념부터 활용까지 JavaScript Promise | 프론트엔드 개발자 입문편 (JavaScript ES6)](https://www.youtube.com/watch?v=JB_yU6Oe2eE&t=1218s)
