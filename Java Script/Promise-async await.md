# <p align="center">🚦Async & await</p>

# 🚦Async & await 101

- ✨`promise`를 `간편`하게 사용 가능!
- `동기적`으로 실행되는 것 처럼 보이게 하는 것
- `🍭 Syntactic sugar`
  - 프로토타입을 베이스로 하여 `+` 덧 붙이는 것
  - 새로운 것이 아님!

```javascript
function fetchUser() {
  // do network request in 10 secs...
  return "elle";
}

const user = fetchUser();
```

```jsx
JavaScript는 동기 처리를 하기 때문에 위의 코드는 블락커가 됩니다.
```

```javascript
function fetchUser() {
  // do network request in 10 secs...
  return new Promise((resolve, reject) => {
    //이 코드 블럭안의 코드가 비동기 처리 됨
    //위의 상태로 진행하면 pending 상태 -> resolve, reject 행위가 없기 때문
  });
}

const user = fetchUser();
```

## 🎯 Async

```jsx
async function fetchUser() {
  return "elle";
}
//Promise {<fulfilled>: 'elle'}
const user = fetchUser();
```

- `async`는 function 앞에 `위치`합니다.
- `async` 키워드를 함수 앞에 쓰면, 코드 블럭이 자동으로 promise로 바뀝니다.

  ```javascript
  async function f() {
    return 1;
  }
  ```

- `function`앞에 `async`을 붙이면 해당 함수는 항상 `Promise`를 반환합니다.
- 프라미스가 아닌 값을 반환하더라도 이행 상태의 프라미스(resolved promise)로 값을 감싸 이행된 프라미스가 반환되도록 합니다.

## 🚦 await

```javascript
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function getApple() {
  await delay(3000);
  return "🍎";
}

async function getBanana() {
  await delay(3000);
  return "🍌";
}

async function pickFruits() {
  const apple = await getApple();
  const banana = await getBanana();
  return `${apple} + ${banana}`;
}
```

### ⚠️ `async` 이 붙은 함수 안에서만 사용할 수 있습니다.

- 일반 함수에서 사용 불가

```jsx
async function pickFruits(){
	try{
		const apple = await getApple();
		const banana = await getBanana();
	}
		catch(){
	return `${apple} + ${banana}`;
	}
}
```

- `await`의 병렬 처리

  - 순차적인 진행시 비효율 적 😩

  ```jsx
  async function pickFruits() {
    const applePromise = getApple();
    const bananapromise = getBanana();
    //Promise는 생성되지 마자 실행 됨

    const apple = await applePromise();
    const banana = await bananapromise();
    // 동기화를 시켜 줌
    // 병렬 실행 됨
    return `${apple} + ${banana}`;
  }
  ```

  - 효율적인 실행을 위해서는 promise api를 활용할 수 있습니다! 👇

# <p align="center">✨useFul promise API</p>

## ✅ `Promise.all`

- 여러 개의 프라미스가 모두 처리되길 기다려야 하는 상황이라면 이 프라미스들을 Promise.all로 감싸고 여기에 await를 붙여 사용할 수 있습니다.

```javascript
function pickAllFruits() {
  return Promise.all([getApple(), getBanana()]).then(fruits =>
    fruits.join("+")
  );
}
```

## 🏃‍♀️`Promise.race`

```javascript
function pickOnlyOne() {
  return Promise.race([getApple(), getBanana()]);
  //가장 먼저 전달 받는것만
}
```

# <p align="center"> 🚨 Error handling</p>

- 프라미스가 정상적으로 이행되면 `await promise`는 프라미스 객체의 result에 저장된 값을 반환합니다. 반면 프라미스가 거부되면 마치 throw문을 작성한 것처럼 에러가 던져집니다.

예시:

```javascript
async function f() {
  await Promise.reject(new Error("에러 발생!"));
}
```

위 코드는 아래 코드와 동일합니다.

```javascript
async function f() {
  throw new Error("에러 발생!");
}
```

- 실제 상황에선 프라미스가 거부 되기 전에 약간의 시간이 지체되는 경우가 있습니다. 이런 경우엔 `awai`t가 에러를 던지기 전에 지연이 발생합니다.

- await가 던진 에러는 `throw`가 던진 에러를 잡을 때처럼 `try..catch`를 사용해 잡을 수 있습니다.

```javascript
async function f() {
  try {
    let response = await fetch("http://유효하지-않은-주소");
  } catch (err) {
    alert(err); // TypeError: failed to fetch
  }
}

f();
```

- 에러가 발생하면 제어 흐름이 `catch` 블록으로 넘어갑니다. 여러 줄의 코드를 `try`로 감싸는 것도 가능합니다.

```javascript
async function f() {
  try {
    let response = await fetch("http://유효하지-않은-주소");
    let user = await response.json();
  } catch (err) {
    // fetch와 response.json에서 발행한 에러 모두를 여기서 잡습니다.
    alert(err);
  }
}

f();
```

- `try..catch`가 없으면 아래 예시의 async 함수 `f()`를 호출해 만든 프라미스가 거부 상태가 됩니다. `f()`에 `.catch`를 추가하면 거부된 프라미스를 처리할 수 있습니다.

```javascript
async function f() {
  let response = await fetch("http://유효하지-않은-주소");
}
// f()는 거부 상태의 프라미스가 됩니다.
f().catch(alert); // TypeError: failed to fetch // (\*)
```

- `.catch`를 추가하는 걸 잊으면 처리되지 않은 프라미스 에러가 발생합니다(콘솔에서 직접 확인해 봅시다). 이런 에러는 프라미스와 에러 핸들링 챕터에서 설명한 전역 이벤트 핸들러 `unhandledrejection`을 사용해 잡을 수 있습니다.

### ‼️ Need to know

1. await는 최상위 레벨 코드에서 작동하지 않습니다.

   ```jsx
   // 최상위 레벨 코드에선 문법 에러가 발생함
   let response = await fetch("/article/promise-chaining/user.json");
   let user = await response.json();
   ```

1. await는 ‘thenable’ 객체를 받습니다.
1. async 클래스 메서드

   - 메서드 이름 앞에 async를 추가하면 async 클래스 메서드를 선언할 수 있습니다.

   ```javascript
   class Waiter {
     async wait() {
       return await Promise.resolve(1);
     }
   }
   new Waiter(); //
   .wait().then(alert); // 1
   ```

   - async 메서드와 async 함수는 프라미스를 반환하고 await를 사용할 수 있다는 점에서 동일합니다.

[이전글: Promise](https://github.com/Dabnii/Dabnii.github.io/blob/main/Java%20Script/Promise.md)

---

출처:

- [async와 await](https://ko.javascript.info/async-await)
- [자바스크립트 13. 비동기의 꽃 JavaScript async 와 await 그리고 유용한 Promise APIs | 프론트엔드 개발자 입문편 (JavaScript ES6)](https://www.youtube.com/watch?v=aoQSOZfz3vQ)

```

```
