# <p align="center"> JavaScript Process

<p align="center"> 👩‍🍳Process & Processor

# 👩‍🍳 Process

### `#독립적` `#실행중인작업`

[Operation System](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcB9Isi%2FbtruUoLTJ8E%2F7pyzUTqv5XcWfrV41AB6AK%2Fimg.png)

### 📍 `1 Process 1 thread`

- 기본적으로 프로세스당 `1개`의 스레드(실행 단위)를 가짐
- 프로세스는 각각 독립된 메모리 영역 (Code, Data, Stack, Heap 구조)을 할당 받는다
- ☝️`독립적`
  - 프로세스는 별도의 주소 공간에서 실행되기 때문에 `다른 프로세스의 변수나 자료구조에 접근할 수 없다.`
  - 각각의 프로세스는 서로 `메모리를 공유하지 않는다`.
- 다른 프로세스의 자원에 접근하려면 프로세스간의 통신 (IPC)을 이용해야한다

- ## 👩‍🍳 Processor:

  - 프로세스 실행 담당 e.g. `요리사`

- ## 🍳 Process:
  - 컴퓨터에서 연속적으로 `실행`되고 있는 `컴퓨터 프로그램`
  - 운영체제로 부터 시스템 자원을 할당받는 작업의 단위
  - 실행중인 프로그램

## [&#60; 다음글: 🧶🪡 Thread &#47; &#62;](https://github.com/Dabnii/Dabnii.github.io/blob/main/Computer%20Science/JavaScript%20%7C%20Thread.md)

출처:

- [멀티 프로세스(Multi Process)와 멀티 스레드(Multi Thread)](https://wooody92.github.io/os/%EB%A9%80%ED%8B%B0-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EB%A9%80%ED%8B%B0-%EC%8A%A4%EB%A0%88%EB%93%9C/)
- [[JS] 자바스크립트 프로세스와 쓰레드 차이 - Jlog](https://artistjay.tistory.com/6)
- [Introduction to JavaScript Runtime Environments](https://www.codecademy.com/article/introduction-to-javascript-runtime-environments)
