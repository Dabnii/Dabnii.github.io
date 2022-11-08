# <p align="center"> 🧢 React Mock data!

## 🧢 React Mock data!

## 🗂 Mock Data

- Mock data란?
  - 프론트엔드 개발자가 필요에 의해 샘플로 만든 `모조 데이터`
- Mock Data 사용이유
  - 백엔드 API가 미완성 이라도 `끊김없는 개발 진행 가능`
  - API완성 이후 기존 Mock Data 실제 API로 원활한 수정 가능
- 활용 예시
  - 실제 API를 요청하듯 Mock Dat는 컴포넌트에서 시점에 따라 fetch 메소드 호출 활용
  - 컴포넌트가 마운트 됐을 때, 혹은 특정 버튼이나 이벤트에 등록 시키는 방식으로 활용
- 관리 방법
  - `public 폴더의 하위 data 폴더에서 관리`

## 🗂 Mock Data 만들기 (FE)

1. 백엔드 개발자와 커뮤니케이션 & API Key-value 확인
   1. 한번에 많은 데이터를 전달 받기에 배열, 객체 형태로 받음
2. 확인 된 Key-value대로 json 파일에 Mock data생성
3. 생성된 Mock Data 관리
4. Mock Data Fetch 메서드 호출

   ### 🗂 저장하는 방법

   ```jsx
   fetch("/data/파일명.json")
     // api 주소 전달
     .then((response) => response.json())
     // callback 전달 -> 매개변수 response에 JSON형태의 데이터가 들어옴
     // body에 .json() 메서드가 JSON 형태를 자바스크립트 형태로 변환하고, 반환
     .then((result) => setState(result));
   // 인자로 callback을 전달하고, 매개변수에서 첫번째 .then에서 반환된 객체를 result로 받아 setState함수로 result를 state에 저장
   // state에 Mock data를 저장하고, 언제든지 꺼내 쓸 수 있게 됨
   ```

5. `fetch` 메서드 호출 타이밍

## 🗂 Mock data 적용

1. data 파일 생성
2. `userInfoList` 파일에 목업 데이터 파일을 넣음

   ```jsx
   //예시
   public
   └── data
       ├── userInfoList.json
       └── ...
   //data를 담은 폴더/파일 생성
   ```

   ```jsx
   src
   └── User.js
   //그려질 UI 구성하기

   return = (
   <div>
           <ul>
                   <li></li>
                   <li></li>
                   <li></li>
           </ul>
       </div>
   )
   ```

### 📌 브라우저에 컴포넌트가 마운트 되었을 때 유저 정보를 보여주고 싶을 때 👇

1. ✨ `useEffect`

   ```jsx
   import React, { useEffect, ✨useState } from "react";

   const user =() => {
   //컴포넌트 안에서 useEffect 작성
       useEffect(()=> {
       fetch("/data/useInforList.json")
       .then((response)=> response.jsson())
       .then((result)=> setUserInforList(result)
       //console.log(userInforList);
       }, []);
   //1️⃣ 인자로 콜백함수를 넣고, 바디에 fetch 호출문을 넣음
   //2️⃣ 마운트 후, 1회만 호출되면 되기 때문에 dependencie array는 빈 배열로 둠
   //3️⃣ fetch 메서드에 첫번째 인자는 api 주소 입력
   //4️⃣ then.메서드 콜백 넣고 매개는 response. body response.json()
   //5️⃣ 위의 .json()메서드가 JSON 형태의 데이터를 JS가 읽을 수 있는 형태로 변환해주는 메소드
   //6️⃣ then. 콜백을 넘기고 매개는 result, body는 콘솔로그로 매개변수 result 확인 먼저 하겠음
   //7️⃣ mock data 확인 후,
   //8️⃣ usestate Hook 사용/작성 useState

   const [userInforList, setUserInforList]= useState([]);
   // State에 저장하고 활용

   //매개변수로 받은 result를 setUserInfoList의 인자로 보내, state에 저장

   return (
   ...
   <div> User
           {userInforList.map((userInfor)=> {
   // Mock data가 저장된 state인 userInoforList 입력
   //인자로 콜백을 넣고
   //매개변수에는 배열의 길이만큼 객체로 이루어진 유저정보가 들어오기 때문에 userInfor입력
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

<hr>

## 🪧 Constant Data

### 상수 데이터

- UI 구성에 필요하지만 동적으로 `변하지 않아서` 백엔드 API 등을 통해서 가져올 필요가 없는 `정적인 데이터`
  - 상수 데이터임을 나타내기 위해서 변수명은 `UPPER_SNAKE_CASE` 사용
  - 객체 형태 뿐만 아니라 숫자, 문자열, 배열 등 가능
- 반복되는 UI 구조는 `상수 데이터와 map 메서드를 활용`해 `간결`하게 표현 가능
- 상수 데이터를 활용하면 UI를 효율적으로, 확장성 있게 구성할 수 있으며 유지보수가 용이
- 상수 데이터는 컴포넌트 파일 내부에서 선언 & 별도의 파일로 분리해서 사용 가능

### map 메서드에서 return하는 javascript를 컴포넌트화하고, props로 넘겨주는 방식 활용 👇

```javascript
// Footer.js

import React from "react";

const Footer = () => {
  return (
    <footer>
      {/* 생략 */}
      <ul>
        {FOOTER_INFO_LIST.map((info) => (
          <FooterInfo key={info.id} link={info.link} text={info.text} />
        ))}
      </ul>
    </footer>
  );
};

export default Footer;
```

### 🗣 선언위치

- 컴포넌트의 `state`나 `props` 등, `컴포넌트 리렌더링 시 변하는 값을 포함하는 상수 데이터는 컴포넌트 내부`에서 작성
- 컴포넌트가 리렌더링 될 때마다 새로 선언되고 할당될 필요가 없는 `상수 데이터는 컴포넌트 외부`에서 작성

```javascript
// Footer.js

import React from "react";

const Footer = () => {
  return (
    <footer>
      {/* 생략 */}
      <ul>
        {FOOTER_INFO_LIST.map((info) => (
          <FooterInfo key={info.id} link={info.link} text={info.text} />
        ))}
      </ul>
    </footer>
  );
};

export default Footer;

const FOOTER_INFO_LIST = [
  { id: 1, link: "https://github.com/terms", text: "Terms" },
  { id: 2, link: "https://github.com/privacy", text: "Privacy" },
  ...{ id: 11, link: "https://github.com/about", text: "About" },
];
```
