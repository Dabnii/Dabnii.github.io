# <p align="center"> ๐งข React Mock data!

## ๐งข React Mock data!

## ๐ Mock Data

- Mock data๋?
  - ํ๋ก ํธ์๋ ๊ฐ๋ฐ์๊ฐ ํ์์ ์ํด ์ํ๋ก ๋ง๋  `๋ชจ์กฐ ๋ฐ์ดํฐ`
- Mock Data ์ฌ์ฉ์ด์ 
  - ๋ฐฑ์๋ API๊ฐ ๋ฏธ์์ฑ ์ด๋ผ๋ `๋๊น์๋ ๊ฐ๋ฐ ์งํ ๊ฐ๋ฅ`
  - API์์ฑ ์ดํ ๊ธฐ์กด Mock Data ์ค์  API๋ก ์ํํ ์์  ๊ฐ๋ฅ
- ํ์ฉ ์์
  - ์ค์  API๋ฅผ ์์ฒญํ๋ฏ Mock Dat๋ ์ปดํฌ๋ํธ์์ ์์ ์ ๋ฐ๋ผ fetch ๋ฉ์๋ ํธ์ถ ํ์ฉ
  - ์ปดํฌ๋ํธ๊ฐ ๋ง์ดํธ ๋์ ๋, ํน์ ํน์  ๋ฒํผ์ด๋ ์ด๋ฒคํธ์ ๋ฑ๋ก ์ํค๋ ๋ฐฉ์์ผ๋ก ํ์ฉ
- ๊ด๋ฆฌ ๋ฐฉ๋ฒ
  - `public ํด๋์ ํ์ data ํด๋์์ ๊ด๋ฆฌ`

## ๐ Mock Data ๋ง๋ค๊ธฐ (FE)

1. ๋ฐฑ์๋ ๊ฐ๋ฐ์์ ์ปค๋ฎค๋์ผ์ด์ & API Key-value ํ์ธ
   1. ํ๋ฒ์ ๋ง์ ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌ ๋ฐ๊ธฐ์ ๋ฐฐ์ด, ๊ฐ์ฒด ํํ๋ก ๋ฐ์
2. ํ์ธ ๋ Key-value๋๋ก json ํ์ผ์ Mock data์์ฑ
3. ์์ฑ๋ Mock Data ๊ด๋ฆฌ
4. Mock Data Fetch ๋ฉ์๋ ํธ์ถ

   ### ๐ ์ ์ฅํ๋ ๋ฐฉ๋ฒ

   ```jsx
   fetch("/data/ํ์ผ๋ช.json")
     // api ์ฃผ์ ์ ๋ฌ
     .then((response) => response.json())
     // callback ์ ๋ฌ -> ๋งค๊ฐ๋ณ์ response์ JSONํํ์ ๋ฐ์ดํฐ๊ฐ ๋ค์ด์ด
     // body์ .json() ๋ฉ์๋๊ฐ JSON ํํ๋ฅผ ์๋ฐ์คํฌ๋ฆฝํธ ํํ๋ก ๋ณํํ๊ณ , ๋ฐํ
     .then((result) => setState(result));
   // ์ธ์๋ก callback์ ์ ๋ฌํ๊ณ , ๋งค๊ฐ๋ณ์์์ ์ฒซ๋ฒ์งธ .then์์ ๋ฐํ๋ ๊ฐ์ฒด๋ฅผ result๋ก ๋ฐ์ setStateํจ์๋ก result๋ฅผ state์ ์ ์ฅ
   // state์ Mock data๋ฅผ ์ ์ฅํ๊ณ , ์ธ์ ๋ ์ง ๊บผ๋ด ์ธ ์ ์๊ฒ ๋จ
   ```

5. `fetch` ๋ฉ์๋ ํธ์ถ ํ์ด๋ฐ

## ๐ Mock data ์ ์ฉ

1. data ํ์ผ ์์ฑ
2. `userInfoList` ํ์ผ์ ๋ชฉ์ ๋ฐ์ดํฐ ํ์ผ์ ๋ฃ์

   ```jsx
   //์์
   public
   โโโ data
       โโโ userInfoList.json
       โโโ ...
   //data๋ฅผ ๋ด์ ํด๋/ํ์ผ ์์ฑ
   ```

   ```jsx
   src
   โโโ User.js
   //๊ทธ๋ ค์ง UI ๊ตฌ์ฑํ๊ธฐ

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

### ๐ ๋ธ๋ผ์ฐ์ ์ ์ปดํฌ๋ํธ๊ฐ ๋ง์ดํธ ๋์์ ๋ ์ ์  ์ ๋ณด๋ฅผ ๋ณด์ฌ์ฃผ๊ณ  ์ถ์ ๋ ๐

1. โจ `useEffect`

   ```jsx
   import React, { useEffect, โจuseState } from "react";

   const user =() => {
   //์ปดํฌ๋ํธ ์์์ useEffect ์์ฑ
       useEffect(()=> {
       fetch("/data/useInforList.json")
       .then((response)=> response.json())
       .then((result)=> setUserInforList(result)
       //console.log(userInforList);
       }, []);
   //1๏ธโฃ ์ธ์๋ก ์ฝ๋ฐฑํจ์๋ฅผ ๋ฃ๊ณ , ๋ฐ๋์ fetch ํธ์ถ๋ฌธ์ ๋ฃ์
   //2๏ธโฃ ๋ง์ดํธ ํ, 1ํ๋ง ํธ์ถ๋๋ฉด ๋๊ธฐ ๋๋ฌธ์ dependencie array๋ ๋น ๋ฐฐ์ด๋ก ๋ 
   //3๏ธโฃ fetch ๋ฉ์๋์ ์ฒซ๋ฒ์งธ ์ธ์๋ api ์ฃผ์ ์๋ ฅ
   //4๏ธโฃ then.๋ฉ์๋ ์ฝ๋ฐฑ ๋ฃ๊ณ  ๋งค๊ฐ๋ response. body response.json()
   //5๏ธโฃ ์์ .json()๋ฉ์๋๊ฐ JSON ํํ์ ๋ฐ์ดํฐ๋ฅผ JS๊ฐ ์ฝ์ ์ ์๋ ํํ๋ก ๋ณํํด์ฃผ๋ ๋ฉ์๋
   //6๏ธโฃ then. ์ฝ๋ฐฑ์ ๋๊ธฐ๊ณ  ๋งค๊ฐ๋ result, body๋ ์ฝ์๋ก๊ทธ๋ก ๋งค๊ฐ๋ณ์ result ํ์ธ ๋จผ์  ํ๊ฒ ์
   //7๏ธโฃ mock data ํ์ธ ํ,
   //8๏ธโฃ usestate Hook ์ฌ์ฉ/์์ฑ useState

   const [userInforList, setUserInforList]= useState([]);
   // State์ ์ ์ฅํ๊ณ  ํ์ฉ

   //๋งค๊ฐ๋ณ์๋ก ๋ฐ์ result๋ฅผ setUserInfoList์ ์ธ์๋ก ๋ณด๋ด, state์ ์ ์ฅ

   return (
   ...
   <div> User
           {userInforList.map((userInfor)=> {
   // Mock data๊ฐ ์ ์ฅ๋ state์ธ userInoforList ์๋ ฅ
   //์ธ์๋ก ์ฝ๋ฐฑ์ ๋ฃ๊ณ 
   //๋งค๊ฐ๋ณ์์๋ ๋ฐฐ์ด์ ๊ธธ์ด๋งํผ ๊ฐ์ฒด๋ก ์ด๋ฃจ์ด์ง ์ ์ ์ ๋ณด๊ฐ ๋ค์ด์ค๊ธฐ ๋๋ฌธ์ userInfor์๋ ฅ
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

1. Mock data๋ฅผ ์ฌ์ฉํ์ฌ ํ๋ก ํธ์์ ์์ฒด์ ์ผ๋ก ๋ชฉ๋ฐ์ดํฐ๋ฅผ ์ ์
1. โจ ๋ธ๋ผ์ฐ์ ์ ๋ง์ดํธ ๋์ ๋ง์ ui๋ฅผ ๊ทธ๋ฆฌ๋๋ก `fetch`์ฌ์ฉ
1. `useEffect`์์์ `fetch` ๋ฉ์๋ ํธ์ถ
1. `state์ ์ ์ฅ`ํด์ ํ์ํ ๋ฐ์ดํฐ๋ฅผ ๊ฐ์ ธ๋ค๊ฐ `UI`๋ก ๊ทธ๋ ค๋

<hr>

## ๐ชง Constant Data

### ์์ ๋ฐ์ดํฐ

- UI ๊ตฌ์ฑ์ ํ์ํ์ง๋ง ๋์ ์ผ๋ก `๋ณํ์ง ์์์` ๋ฐฑ์๋ API ๋ฑ์ ํตํด์ ๊ฐ์ ธ์ฌ ํ์๊ฐ ์๋ `์ ์ ์ธ ๋ฐ์ดํฐ`
  - ์์ ๋ฐ์ดํฐ์์ ๋ํ๋ด๊ธฐ ์ํด์ ๋ณ์๋ช์ `UPPER_SNAKE_CASE` ์ฌ์ฉ
  - ๊ฐ์ฒด ํํ ๋ฟ๋ง ์๋๋ผ ์ซ์, ๋ฌธ์์ด, ๋ฐฐ์ด ๋ฑ ๊ฐ๋ฅ
- ๋ฐ๋ณต๋๋ UI ๊ตฌ์กฐ๋ `์์ ๋ฐ์ดํฐ์ map ๋ฉ์๋๋ฅผ ํ์ฉ`ํด `๊ฐ๊ฒฐ`ํ๊ฒ ํํ ๊ฐ๋ฅ
  - `Array.map()`
- ์์ ๋ฐ์ดํฐ๋ฅผ ํ์ฉํ๋ฉด UI๋ฅผ ํจ์จ์ ์ผ๋ก, ํ์ฅ์ฑ ์๊ฒ ๊ตฌ์ฑํ  ์ ์์ผ๋ฉฐ ์ ์ง๋ณด์๊ฐ ์ฉ์ด
- ์์ ๋ฐ์ดํฐ๋ ์ปดํฌ๋ํธ ํ์ผ ๋ด๋ถ์์ ์ ์ธ & ๋ณ๋์ ํ์ผ๋ก ๋ถ๋ฆฌํด์ ์ฌ์ฉ ๊ฐ๋ฅ

### ์์๋ฐ์ดํฐ ์ ์ธ

```javascript
const FOOTER_INFO_LIST = [
  { id: 1, link: "https://github.com/terms", text: "Terms" },
  { id: 2, link: "https://github.com/privacy", text: "Privacy" },
  ...{ id: 11, link: "https://github.com/about", text: "About" },
];
```

```javascript
// Footer.js

import React from "react";

const Footer = () => {
  return (
    <footer>
      {/* ์๋ต */}
      <ul>
        {FOOTER_INFO_LIST.map((info) => (
          <li key={info.id}>
            <a href={info.link}>{info.text}</a>
          </li>
        ))}
      </ul>
    </footer>
  );
};

export default Footer;
```

> ๊ฐ์ฒด ํํ ๋ฟ๋ง ์๋๋ผ ์ซ์, ๋ฌธ์์ด, ๋ฐฐ์ด ๋ฑ ๊ฐ๋ฅ

### map ๋ฉ์๋์์ returnํ๋ javascript๋ฅผ ์ปดํฌ๋ํธํํ๊ณ , props๋ก ๋๊ฒจ์ฃผ๋ ๋ฐฉ์ ํ์ฉ ๐

```javascript
// Footer.js

import React from "react";

const Footer = () => {
  return (
    <footer>
      {/* ์๋ต */}
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

### ๐ฃ ์ ์ธ์์น

- ์ปดํฌ๋ํธ์ `state`๋ `props` ๋ฑ, `์ปดํฌ๋ํธ ๋ฆฌ๋ ๋๋ง ์ ๋ณํ๋ ๊ฐ์ ํฌํจํ๋ ์์ ๋ฐ์ดํฐ๋ ์ปดํฌ๋ํธ ๋ด๋ถ`์์ ์์ฑ
- ์ปดํฌ๋ํธ๊ฐ ๋ฆฌ๋ ๋๋ง ๋  ๋๋ง๋ค ์๋ก ์ ์ธ๋๊ณ  ํ ๋น๋  ํ์๊ฐ ์๋ `์์ ๋ฐ์ดํฐ๋ ์ปดํฌ๋ํธ ์ธ๋ถ`์์ ์์ฑ

  ```javascript
  // Footer.js

  import React from "react";

  const Footer = () => {
    return (
      <footer>
        {/* ์๋ต */}
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
