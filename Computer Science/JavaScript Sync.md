# <p align="center"> 🪞 Why is JavaScript called synchronous?
<p align="center"> 🪞 왜 자바스크립트를 동기적 언어라고 부르나요?


<img src="https://user-images.githubusercontent.com/110847597/208118602-43311d4b-428c-4181-a55a-a5c5b2442092.png" width=1000px align="center" alt="동기비동기 이미지"/>

### <p align="center"> 🟨 자바스크립트는 어떤 언어인가요? | #동기적언어 #싱글스레드 

---

<p align="center">🤔 실제로 멀티 스레드 처럼 사용하는데 어떻게 사용하나요? 

## 👩‍🍳Process

![spongebob is cooking](https://media1.giphy.com/media/ud6EmjRF8CICI/giphy.gif?cid=ecf05e47iffxdsawyvbnij2q51iedjfsjpml6qn9amtjl9p9&rid=giphy.gif&ct=g)
- 기본적으로 프로세스당 1개의 스레드를 가짐
- 프로세스는 각각 독립된 메모리 영역 (Code, Data, Stack, Heap 구조)을 할당 받는다
- 프로세스는 별도의 주소 공간에서 실행되기 때문에 다른 프로세스의 변수나 자료구조에 접근할 수 없다.
- 다른 프로세스의 자원에 접근하려고 프로세스간의 통신 (IPC)을 이용해야한다 
    - 👩‍🍳 Proecess: 
        - 컴퓨터에서 연속적으로 실행되고 있는 컴퓨터 프로그램
        - 운영체제로 부터 시스템 자원을 할당받는 작업의 단위 
        - 실행중인 프로그램  
            - 👩‍🍳 Processor는 프로세스를 담당합니다
## 🧶🪡 Thread
- 프로세스 내에서 실행되는 흐름의 단위
    - 패티굽는 스레드
    - 빵과 야채를 준비하는 스레드
    - 소스를 바르는 스레드      
    - 스레드는 프로세스 내에서 각각 stack만 따로 할당 받고 나머지 영역은 `공유`한다
    - 스레드는 프로세스 내의 주소공간이나 자원들을 같은 프로세스 내에 스레드 끼리 공유하면서 실행된다 
- 싱글스레드 vs 멀티스레드 
    ### 🪡 싱글스레드: 
    -  직렬 형태로 하나의 스레드가 하나의 작업만 수행하며 순서대로 처리
    - 공유자원 접근에 대한 동기화문제로부터 자유롭다 (순서 신경을 쓸 필요가 없다) → 비교적 프로그래밍 난이도가 쉽다
    - 효율성이 떨어진다.
    ### 🧶 멀티스레드:
    - 병렬로 일을 처리하며 여러가지 스레드를 한꺼번에 처리
    - 공유 자원 접근에 대한 동기화문제를 신경써야한다 → 비교적 프로그래밍 난이도가 어렵다.
    - 에러 발생 시 새로운 스레드를 생성하여 극복할 수 있다
    - 효율적 운영이 가능하다    

## ✨♻️  `동기 Synchronous` vs `비동기 Asynchronous`
<img src="https://user-images.githubusercontent.com/110847597/208118602-43311d4b-428c-4181-a55a-a5c5b2442092.png" width=1000px align="center" alt="동기비동기 이미지"/>

![spongebob ticket](https://media0.giphy.com/media/xT3i0XldZ29FX3X3C8/giphy.gif?cid=ecf05e47npvilyzm6ssjgshj8osafimnovudvt5ruas6phpq&rid=giphy.gif&ct=g)

### ✨♻️ `동기 Synchronous`:
- 현재 실행중인 테스크가 종료할 때 까지 다음에 실행될 테스크가 대기하는 방식
- 속도가 느리다
- 실행 순서가 보장된다
- 진행방향이 단방향이기에 코드에서 에러 파악이 쉽다
### ✨♻️ `비동기 Asynchronous`
- 현재 실행중인 테스크가 종료되지 않은 상태라 해도 다음 테스크를 곧바로 실행하는 방식
- 속도가 빠르다 
- 어느것이 먼저 끝나고 진행되는지 모르기에 진행 방향을 예상하기 힘들다 즉 에러 파악이 어렵다
### ✨⚙️ JavaScript Engine `V8`
- 🧐 자바스크립트 코드를 해석하고 실행하는 인터프리터
    - 자바스크립트 코드를 실행하는 프로그램
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
- Primanry type vs Reference type!
- 비동기적으로 실행이 되는 것을 동기적으로 코딩하는 방법이 있나요? 
    - 웹 브라우저의 Web API에서 제공하는 AJAX통신, setTimeOut함수, DOM이벤트 함수를 이용해 동기적 언어인 자바스크립트를 비동기적으로 사용할 수 있음
    - 멀티스레드로 작동하는 Web API와 상호연동 하며 멀티스레드의 동시성을 지닐 수 있음\
    ![event Loop img](https://res.cloudinary.com/practicaldev/image/fetch/s--0TQg9sD0--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://thepracticaldev.s3.amazonaws.com/i/ek7ji4zrimozpp2yzk0a.png)

    ```jsx
    console.log(1);

    setTimeout(()=> {
        console.log(2)
    }, 1000)

    console.log(3)

    1
    3
    2
    ```
    ![event loop gif](https://res.cloudinary.com/practicaldev/image/fetch/s--BLtCLQcd--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif14.1.gif)
    >https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif

- Event Loop에 대해서 알고 있으신가요?
    - 자바스크립트 코드가 진행되는 자바스크립트 엔진의 뒤편에서 일어나는 어떤 거대한 문맥의 일부로써 동작하는 하나의 장치
    - 콜 스택 콜백큐를 계속 주시하고 있다
    - 콜스택이 비어있으면 먼저 들어온 순서대로 콜백큐에 콜백함수들을 콜스택으로 집어 넣는다

---

출처: 

[✨♻️ JavaScript Visualized: Event Loop - Lydia Hallie](https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif)