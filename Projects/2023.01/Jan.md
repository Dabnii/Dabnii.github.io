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

## <p align="center"> 📆 1/23

### ⚒️ Refactoring Time!

> 연휴내내 미루었던 리팩토링을 시작헀습니다!

## <p align="center">⚒️ Time to Refactoring 🏗️</p>

미루었던 리팩토링을 시작했습니다. `작동한다면 되는거 아닌가?`는 더 나은 개발자가 되기 위해서 제일 지양해야할 생각입니다. 돌아가는 코드 말고 `더 나은 코드`를 개발하는 개발자가 되고 싶습니다.

### 💡 리팩토링을 왜 배워야 하는걸까?

1. `문제 파악` → 🕵️ 나쁜 코드의 냄새를 맡을 수 있다
1. `문제 해결 가능` → 💩 더러운 코드를 깨끗하게 개선할 수 있다
1. `좋은 습관` → 처음부터 깨끗한 코드로 작성한다!
1. 🫡 즉 이해, 수정이 용이하고 재사용이 가능하도록 작성하는 것!

## <p align="center">🏜️ D.R.Y 🌵</p>

<p align="center">Don't Repeat Yourself</p>

```jsx
DRY is about the duplication of knowledge, of intent. It’s about expressing the same thing in two different places, possibly in two totally different ways.

Every piece of knowledge must have a single, unambiguous, authoritative representation within a system

-by The Pragmatic Programmer
```

- `유지보수성` 한 곳에서만 로직을 작성하여 DRY하게 사용한다면, 한 곳에서만 수정하면 됨

### 🙅‍♀️ `W`rite `E`very `T`ime

- 매번 작성하고, 모든 걸 두번씩 작성하는 것

## <p align="center">😘K.I.S.S</p>

<p align="center">Keep It simple, Stupid</p>

```jsx
대부분의 시스템은 복잡하게 보다는 심플하게 만들어졌을 때 최고로 잘 동작한다.
불필요한 복잡성은 피해야 한다.
```

### 가장 간단하게, 그리고 가장 멍청하게!

- Code
- Function
- Class
- View
- Service
- System

```jsx
//💩
function getFirst (array, isEven) {
return array. find(x => (isEven ? × % 2 === 0 : × % 2 !== 0));
}
```

```jsx
//✨✨✨
function getFirstOdd (array) {
return array.find(x => × % 2 !== 0) ;
function getFirstEven (array) {
return array.find(x => × % 2 === 0) ;}
```

> 위의 예시를 확인해 보며, 작업했던 프로젝트의 코드들을 어떻게 바꾸면 좋을지 감이 잡혔다.

#### Proj. CGW

- [x] `KISS` 한 함수에, 하나의 기능만 담도록 리팩토링 중!

#### Proj. 39cm

- [x] 하드코딩 삭제 👋
- [x] `💨 Swiper` 추가
- [x] `⭐️ ReactStars` 추가

  ```jsx
  //After 별점
  <ReactStars
    className="reactStarts"
    value={5}
    edit={false}
    color2={"orangered"}
  />
  ```

- [코딩 잘하는법 (개발자답게 코딩하려면?)](https://www.youtube.com/watch?v=WF_bzlpaW0I&list=PL1QuuH44oPS3Ss2l8__ai4bbpSe0bUHmU&index=3)
- [깨끗한 코딩 하는법 (리팩토링 최종정리판 강의, 드루와🥳)](https://www.youtube.com/watch?v=81gaY3Du6OI)

---

## <p align="center"> 📆 1/24

## ♻️ Swiper

> 리팩토링을 진행하며 하드코딩 되어 있던 캐러셀을 라이브러리로 수정

<img align="center" src="https://user-images.githubusercontent.com/110847597/214536618-e989c78e-8735-4127-9336-6be9ec28f933.gif" alt="gif-swiper" />

```jsx
import React, { useState } from "react";
import { Swiper, SwiperSlide } from "swiper/react";

export default function App({ pdData }) {
  const [swiperRef, setSwiperRef] = useState([]);

  const prevHandler = () => {
    swiperRef.slidePrev();
  };

  const nextHandler = () => {
    swiperRef.slideNext();
  };

  return (
    <>
      <div className="arrowsSet">
        <button className="arrowLeft" onClick={prevHandler}></button>
        <button className="arrowRight" onClick={nextHandler}></button>
      </div>
      <Swiper
        className="swiper"
        loop={true}
        slidesPerView={1}
        navigation
        onSwiper={swiper => setSwiperRef(swiper)}
      >
        {images.map((image, index) => {
          <SwiperSlide className="swiper-slide">
            <img
              key={index}
              src={image.image}
              alt="thumbNail"
              width={400}
              height={400}
            />
          </SwiperSlide>;
        })}
      </Swiper>
    </>
  );
}
```

> 인라인 스타일링을 지양하고 싶다.

### 👻 기존 스와이퍼 버튼을 display none으로 감추기

```scss
.swiper-button-next::after,
.swiper-button-prev::after {
  display: none;
}
```

### 🦋 Arrow custom css

```scss
//mixin.scss
@mixin backgroundSetting($background-size, $background-position) {
  background-color: white;
  background-size: $background-size;
  background-position: $background-position;
  background-repeat: no-repeat;
}
//Swiper
.arrowsSet {
  @include flex(space-between, center);
  width: 100%;
  position: absolute;
  left: 0;
  top: 50%;
  align-content: center;
  transform: translateY(-50%);
  z-index: 99999;

  .arrowLeft {
    @include widHeight(2rem, 3rem);
    align-items: center;
    border: none;
    background-image: url(../../../images/arrowLeft.png);
    @include backgroundSetting(30%, 40%);
  }

  .arrowRight {
    @include widHeight(2rem, 3rem);
    align-items: center;
    border: none;
    background-image: url(../../../images/arrowRight.png);
    @include backgroundSetting(30%, 60%);
  }
}
```

- 아무런 정보가 필요없는 이미지기에 background로 이미지 추가
- `background-repeat: no-repeat`로 반복 해제

### 🌳 성장 포인트:

- 클린 코드를 해야하는 이유는 높은 확률로 내가 작성한 코드를 6개월 후에 내가 보기 때문!
  - 컴포넌트 분리와 더 깔끔한 로직을 위하여 많은 시간을 할애했다. 그 만큼 성장! 🦒 앞으론 초석을 잘 다져야지..
