## <p align="center"> 📆 1/10

### 🚨 'react-dom' which is not supported

<img width="533" alt="react-dom is not supported" src="https://user-images.githubusercontent.com/110847597/211842990-a8022d9d-34d6-4f74-9a10-9b245debe996.png">

- React 18버전 부터 `react-dom`을 더 이상 지원하지 않는다.
- `react-dom/client`으로 바르게 임포트 👏
- 사실 관련 글을 더 찾아보니 비단 코드 한 두줄로 해결되는 것이 아니다..
- 두 가지의 방법이 있는데 또 공부할 것이 늘었다!
  - `ReactDOM.render` VS `createRoot`
  - `hydration`

```jsx
//Before
import ReactDOM from "react-dom"; // 👈️ wrong import path
```

```jsx
//After 💯
import ReactDOM from "react-dom/client"; // 👈️ right import path
```

### Overview

React 18 ships two root APIs, which we call the Legacy Root API and the New Root API.

> - Legacy root API: This is the existing API called with ReactDOM.render. This creates a root running in “legacy” mode, which works exactly the same as React 17. Before release, we will add a warning to this API indicating that it’s deprecated and to switch to the New Root API.
> - New root API: The new Root API is called with ReactDOM.createRoot. This creates a root running in React 18, which adds all of the improvements of React 18 and allows you to use concurrent features. This will be the root API moving forward.

### Why ship both?

We’re shipping the legacy API in React 18 for two reasons:

> - Smooth upgrade: We want to avoid user upgrading to React 18 and immediately seeing a crash. Instead, we’re adding a warning to the legacy root API that recommends using the new API.
> - Experimentation: Some apps may choose to run a production experiment to compare the legacy root with the new root which includes performance improvements out of the box. By including both, it’s easier to run experiments.

[📎 Replacing render with createRoot #5](https://github.com/reactwg/react-18/discussions/5)

[📎 You are importing createRoot from 'react-dom' which is not supported](https://bobbyhadz.com/blog/react-you-are-importing-createroot-from-react-dom)

[📎 ReactDOMClient](https://reactjs.org/docs/react-dom-client.html)

[📎 React 18의 ReactDOMClient.createRoot](https://velog.io/@ggong/React-18%EC%97%90%EC%84%9C-ReactDOM.render-%EB%8C%80%EC%8B%A0-createRoot-%EC%93%B0%EA%B8%B0)

---

## <p align="center"> 📆 1/11

### ☁️ Upload Local Git to GitHub!

- 로컬과 원격저장소 연결이 안될 때
- 💡 원격 레파지토리 만들 때 `README.md`를 빼고 생성하기

```jsx
$ git remote -v
//현재 레파지토리의 원격 링크를 확인
//origin folk url
//upstream 원래 레파지토리 url
```

1. 레파지토리 url을 확인한다
1. 깃 커밋 → 푸쉬를 진행한다!
1. DONE!👏

[📎 원격저장소 추가 - git remote add](https://shanepark.tistory.com/284)

---
