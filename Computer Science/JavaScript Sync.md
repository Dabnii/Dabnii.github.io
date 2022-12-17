# <p align="center"> 🪞 Why is JavaScript called synchronous?
<p align="center"> 🪞 왜 자바스크립트를 동기적 언어라고 부르나요? [작성중...]

<img src="https://user-images.githubusercontent.com/110847597/208118602-43311d4b-428c-4181-a55a-a5c5b2442092.png" width=1000px align="center" alt="동기비동기 이미지"/>

<p align="center">#자바스크립트 #동기 #싱글스레드 #인터프리터 #이벤트루프 #V8</p>

---

## ✨♻️ `Synchronous` 이란?
> ### `synchronous` [adjective]
>: happening, existing, or arising at precisely the same time
>: 정확히 동시에 발생하거나, 존재하거나, 발생하는
>>Webster https://www.merriam-webster.com/dictionary/synchronous

- `synchronous`의 한국어 번역은 정확히 동시에 발생하거나, 존재하거나, 발생하는 뜻을 가집니다.
- iCloud 또는 iPhone을 동기화 한다 라는 개념과는 차이가 있습니다.<br>
    - 한국어로 표현하는 `동기(同期)` 는 `같을 동(同)` `기약할 기(期)`를 사용하여, 대학 동기, 입사동기 등 같은 기간 이라는 뜻 입니다. 하지만 기계간의 주기를 같이 하는 것이 아니므로  흔히 알고 있는 `동기화`와 자바스크립트의 `동기`는 컴퓨터 공학에서 엄연히 다른 뜻 입니다.

> 📍 Synchronize, Synchronization, Synchronous 등 Synchro를 공유하는 이 단어들이 공통적으로 가지는 뉘앙스는 바로 동시에 똑같이 진행되는 느낌이다. 그것이 상태이든 동작이든 사건이든 `동시에 똑같이 진행되는` 느낌을 말하는 것이다. -[동기(Synchronous)는 정확히 무엇을 의미하는걸까?](https://evan-moon.github.io/2019/09/19/sync-async-blocking-non-blocking/)-


## 🤔 그러면, JavaScript는 왜 `동기적` 언어일까?
그리고 어떻게 작동할까?

### 🧐💻 컴퓨터 공학에서의 동기

<img src="https://user-images.githubusercontent.com/110847597/208141588-9d5d17c3-32a1-4deb-a92f-4980ba9743bf.png" align="center"/>

- 동기 방식은 현재 작업의 응답과 다음 작업의 요청의 타이밍을 맞추는 방식이다.
    - [동기(Synchronous)는 정확히 무엇을 의미하는걸까?](https://evan-moon.github.io/2019/09/19/sync-async-blocking-non-blocking/)-



### ✨♻️ `동기 Synchronous`
![spongebob ticket](https://media0.giphy.com/media/xT3i0XldZ29FX3X3C8/giphy.gif?cid=ecf05e47npvilyzm6ssjgshj8osafimnovudvt5ruas6phpq&rid=giphy.gif&ct=g)

> 징징이는 손님을 한 명씩 응대합니다. 이것이 동기와 가장 비슷한 형태 입니다. 징징이는 하나 이지만 손님이 100명이 몰린다면 속도가 느려집니다. 동기 언어인 자바스크립트도 그러합니다.

- 현재 실행중인 테스크가 종료할 때 까지 다음에 실행될 테스크가 대기하는 방식
- 속도가 느리다
- 실행 순서가 보장된다
- 진행방향이 단방향이기에 코드에서 에러 파악이 쉽다


### ✨♻️ `비동기 Asynchronous`
<img src="https://media1.giphy.com/media/ud6EmjRF8CICI/giphy.gif?cid=ecf05e47iffxdsawyvbnij2q51iedjfsjpml6qn9amtjl9p9&rid=giphy.gif&ct=g)" align="center" alt="spongebob cooking"/>

> ~~비록 스폰지밥 혼자 햄버거를 만들지만~~ 패티가 구워지는 동안, 스폰지밥은 춤을 추거나 다음 재료를 준비하거나 등 다른 일을 할 수 있습니다.

- 현재 실행중인 테스크가 종료되지 않은 상태라 해도 다음 테스크를 곧바로 실행하는 방식
- 속도가 빠르다 
- 어느것이 먼저 끝나고 진행되는지 모르기에 진행 방향을 예상하기 힘들다 즉 에러 파악이 어렵다.

### ✨⚙️ JavaScript Engine `V8`
- 🧐 자바스크립트 코드를 해석하고 실행하는 인터프리터
    - 자바스크립트 코드를 실행하는 프로그램
    - Complile 언어는 엔진 내부에서 컴파일 과정이 있다.
- `Call stack`과 `Heap`으로 이루어짐
- 각 브라우저마다 엔진의 종류가 다름
    - Crhome → `V8`
    - Safari → `Webkit`

### ✨🧱 Call Stack (콜 스택)

- 코드가 실행 될 때 마다 호출 스팩이 쌓이는 곳 (함수가 호출되면 쌓이는 곳)
- 원시타입(숫자등)데이터가 저장 됨 
- 변수 식별자 (이름) 저장
- Heap (힙)
    - 변수와 객체의 메모리 할당이 일어나느 부분
    - 참조타입(객체등) 데이터가 저장 됨
    - 메모리 할당이 일어나는 곳
- `Primanry type` vs `Reference type`!
    

---
 
# 🧶🪡 Thread 란?
- 프로세스 내에서 실행되는 흐름의 단위
    - 패티굽는 스레드
    - 빵과 야채를 준비하는 스레드
    - 소스를 바르는 스레드      
    - 스레드는 프로세스 내에서 각각 stack만 따로 할당 받고 나머지 영역은 `공유`한다
    - 스레드는 프로세스 내의 주소공간이나 자원들을 같은 프로세스 내에 스레드 끼리 공유하면서 실행된다 

# <p align="center">  🪡싱글스레드 vs 🧶멀티스레드
## 🪡 싱글스레드: 
-  직렬 형태로 하나의 스레드가 하나의 작업만 수행하며 순서대로 처리
- 공유자원 접근에 대한 동기화문제로부터 자유롭다 (순서 신경을 쓸 필요가 없다) → 비교적 프로그래밍 난이도가 쉽다
- 효율성이 떨어진다.
## 🧶 멀티스레드:
- 병렬로 일을 처리하며 여러가지 스레드를 한꺼번에 처리
- 공유 자원 접근에 대한 동기화문제를 신경써야한다 → 비교적 프로그래밍 난이도가 어렵다.
- 에러 발생 시 새로운 스레드를 생성하여 극복할 수 있다
- 효율적 운영이 가능하다    

### <p align="center">🤔 싱글스레드인 자바스크립트, 실제로 멀티 스레드 처럼 사용하는데 우리는 어떻게 멀티스레드처럼 자바스크립트를 사용할 수 있나요?
![event Loop img](https://res.cloudinary.com/practicaldev/image/fetch/s--0TQg9sD0--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://thepracticaldev.s3.amazonaws.com/i/ek7ji4zrimozpp2yzk0a.png)
- 웹 브라우저의 Web API에서 제공하는 `AJAX통신, setTimeOut함수, DOM이벤트 함수`를 이용해 동기적 언어인 자바스크립트를 `비동기적으로 사용할 수 있음`
- 멀티스레드로 작동하는 Web API와 상호연동 하며 멀티스레드의 동시성을 지닐 수 있음

---

## <p align="center">🤔 Event Loop에 대해서 알고 있으신가요?
- 자바스크립트 코드가 진행되는 자바스크립트 엔진의 뒤편에서 일어나는 어떤 거대한 문맥의 일부로써 동작하는 하나의 장치
- 콜 스택 콜백큐를 계속 주시하고 있다
- 콜스택이 비어있으면 먼저 들어온 순서대로 콜백큐에 콜백함수들을 콜스택으로 집어 넣는다
```jsx
console.log(1);

setTimeout(()=> {
    console.log(2)
}, 1000)

console.log(3)

//1
//3
//2
```
![event loop gif](https://res.cloudinary.com/practicaldev/image/fetch/s--BLtCLQcd--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif14.1.gif)
>https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif


---

출처: 

- [✨♻️ JavaScript Visualized: Event Loop - Lydia Hallie](https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif)
- [자바스크립트는 왜 싱글 쓰레드일까?](https://chanyeong.com/blog/post/44)
- [JavaScript, 인터프리터 언어일까?](https://www.oowgnoj.dev/review/advanced-js-1) 
- [동기식 처리 모델 vs 비동기식 처리 모델](https://poiemaweb.com/js-async)
- [자바스크립트란?](https://ko.javascript.info/intro)
- [동기(Synchronous)는 정확히 무엇을 의미하는걸까?](https://evan-moon.github.io/2019/09/19/sync-async-blocking-non-blocking/)

---


[다음글: JavaScript Process](https://github.com/Dabnii/Dabnii.github.io/blob/8a5069aaafb3ab808d525d2e28a2c54b8a8f1b48/Computer%20Science/JavaScript%20Process.md)