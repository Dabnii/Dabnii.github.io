## <p align="center"> 📆 2/5

## 🖼️ [Toy-project] Data create & delete program

- 데이터 태그 생성 기능
- 데이터 삭제 & 저장 기능

## 🖼️ Input placeholder가 없어지지 않는다!

> 인풋박스에 숫자를 입력하도록 유도하고 싶었으나, placeholder가 사라지지 않았다.

![Label + input](https://user-images.githubusercontent.com/110847597/217237776-d438652b-3466-44a0-9d04-e9a947d96282.gif)

#### ❕ `Label`로 해결

> 이전에 프로젝트 할 때, button과 radio 박스위에 label을 사용했던 점을 착안

1. label을 `on`
2. 인풋박스에 `onMouseEnter`될 때 `false`로 감춘다
3. displaypencil이 `OFF`라면 input 박스 보이기

### 📌 `htmlFor="(input id)"`

- 라디오 박스처럼 label이 대신 클릭되길 바란다면 React에선 htmlFor의 값을 해당하는 라디오박스 id와 일치하게 해주면 된다.

```jsx
const [displayPencil, setDisplayPencil] = useState(true);
//...
{
  displayPencil ? (
    <label htmlFor='numInput' onMouseEnter={() => setDisplayPencil(false)} />
  ) : (
    <>
      <input
        id='numInput'
        type='number'
        placeholder={0}
        step={1}
        min={0}
        max={possibleMax}
        onChange={handleInputChange}
        value={inputValue}
        onKeyDown={onReset}
        onBlur={onReset}
      />
      <div className='btnContainer'>
        <button className='increase' onClick={() => onIncrease()}>
          +
        </button>
        <button className='decrease' onClick={() => onDecrease()}>
          -
        </button>
      </div>
    </>
  );
}
```

```scss
label {
  height: 50%;
  width: 50%;
  border-bottom: 2px solid black;
  padding-right: 20px;
  background-image: url('../../../public/image/pencil.svg');
  background-repeat: no-repeat;
  background-position: center;
  //시맨틱태그를 사용할 필요가 없어, background img를 사용
}

input[type='number'] {
  -webkit-appearance: textfield;
  -moz-appearance: textfield;
  appearance: textfield;
  animation: fadeOut 0.2s ease-in-out;
  text-align: right;
  border: none;
  width: 8rem;
  padding: 15px;
  background-color: transparent;
  font-family: inherit;
  font-size: 2rem;
  font-weight: 700;
  position: relative;
  -webkit-appearance: none;

  &::-webkit-inner-spin-button,
  &::-webkit-outer-spin-button {
    opacity: 0;
    // 1 이라면 항상 on
    // 0 이라면 off
    -webkit-appearance: none;
  }

  &:focus {
    outline: none;
    //못생긴 outline 삭제
  }
}
```

- `Boolean`으로 state를 관리

## 🖼️ Input min의 배신

- 예상 로직대로라면 `input min` 속성을 사용하여 `0`이상의 정수만 허용
- But, `min={0}` 이하 음수도 작성이 되어서 아래의 로직 추가
- `+` 범위 밖 값이면 팝업창 띄우기!

  ![popup](https://user-images.githubusercontent.com/110847597/217245839-add16c17-e34f-4712-9b0c-0ef45e22a39a.gif)

```jsx
const handleInputChange = e => {
  const input = Math.floor(e.target.value);

  if (input <= 0 || input > possibleMax) {
    setHandleWarning(true);
    setTimeout(() => setHandleWarning(false), 2000);
    return;
  }
  setInputValue(input);
  setDisplayPencil(false);
  setTimeout(() => getAutoDelData(inputValue), 0);
};
//
<input
  id='numInput'
  type='number'
  placeholder={0}
  step={1}
  min={0}
  max={possibleMax}
  onChange={handleInputChange}
  value={inputValue}
  onKeyDown={onReset}
  onBlur={onReset}
/>;
```

<details>
<summary>리팩토링 전 코드</summary>

```jsx
const onDecrease = () => {
  if (inputValue <= 0) {
    setInputValue(0);
  } else {
    setInputValue(prevNum => prevNum - 1);
  }
};
```

- 삼항연산자를 활용하지 못한 러프한 코드

```jsx
  const onDecrease = () => {
    setInputValue(prevNum => {
      return Number(prevNum - 1) >= 0 ? Number(prevNum - 1) : 0;
    });
    getAutoDelData(inputValue);
```

- 삼항연산자를 활용한 코드 ✨
</details>

### 🔍 돌아가는 코드도 다시보자!

![closeSHot](https://user-images.githubusercontent.com/110847597/217237782-d558300a-dd9d-4029-bd75-b2c52dfc64ac.gif)

> `1`일때 정상적으로 연산하지 않는 문제점을 발견했다.
> 확인해 보니 숫자가 아닌 `string`으로 들어오고 있었다.
> `Number()` 사용으로 숫자로 변환완료

```jsx
//before
const onIncrease = () => {
  setInputValue(prevNum => {
    return prevNum + 1 <= possibleMax ? prevNum + 1 : prevNum;
  });
  getAutoDelData(inputValue);
};

//after
const onIncrease = () => {
  setInputValue(prevNum => {
    return prevNum + 1 <= possibleMax ? Number(prevNum + 1) : Number(prevNum);
  });
  getAutoDelData(inputValue);
};
```

### 🤓 가독성 좋은 코드를 쓰자

```jsx
//After ✨
function KeepDataComponent({ getAutoDelValue, getData }) {
  const total = getData.length;
  const keep = Number(total - getAutoDelValue);

  return <div>...</div>;
}

//before 😖
function KeepDataComponent({ getAutoDelValue, getData }) {
  const calculateData = getData.length - getAutoDelValue;

  return <div>...</div>;
}
```

- 한 줄이라고 다 좋은 코드는 아니다.

## <p align="center"> 📆 2/10

### Login Function ⚙️

- account를 switch로 리팩토링 해보고 싶다.

```jsx
const [account, setAccount] = useState({
  firstName: '',
  lastName: '',
  email: '',
  gender: '',
  password: '',
  passwordCheck: '',
});


<input
  type='text'
  name='lastName'
  className='lastName'
  placeholder='last name'
  maxLength={13}
  onChange={handleUserInfo}
  onBlur={() =>
    setIsValid({
      ...isValid,
      lastName:
        lastNameRex.test(account.lastName) === true
          ? true
          : null,
    })
  }
```

### 💨 `onBlur={}`

- `blur` [📎 blur](https://developer.mozilla.org/ko/docs/Web/API/Element/blur_event)
- blur 이벤트는 엘리먼트의 포커스가 해제되었을 때 발생합니다.
- 이 이벤트와 focusout 이벤트의 가장 다른점은 `focusout은 이벤트 버블링이 발생`합니다.

### 🔬 `regex` 활용한 유효성 검사

```jsx
  const [isValid, setIsValid] = useState({
    firstName: false,
    lastName: false,
    email: false,
    password: false,
    passwordConfirm: false,
  });

  const firstNameRex = /^[A-Za-z가-하]{2,}/;
  //이름은 한글, 영대소문자 무관으로 최소 2자 이상
  const lastNameRex = /^[A-Za-z가-하]/;
  //성은 한글, 영대소문자 무관, 자릿수 무관
  const emailRex = /^[a-zA-Z0-9+-_.]+@[a-zA-Z0-9-]+.[a-zA-Z0-9-.]+$/;
  // [a-zA-Z0-9+-_.]하나 이상의 문자로 시작
  // @ 필수 포함
  // @ 기호 뒤에 하나 이상의 문자 필수
  // 문자로 끝이나야함.
  const passwordRex =
    /^(?=.*[a-zA-Z])(?=.*\d)(?=.*[!@#$*])[a-zA-Z\d!@#$*]{8,}$/;
    //하나 이상의 대소문자 필수, 최소 1개의 숫자 필요, 지정한 특수문자 필수, 최소 8자


//input의 속성 이벤트로 사용
onBlur={() =>
  setIsValid({
    ...isValid,
    firstName:
      firstNameRex.test(account.firstName) === true
        ? true
        : null,
  })
}
```

## 📌 `test()`

- test() 메서드는 주어진 문자열이 정규 표현식을 만족하는지 판별하고, 그 여부를 `true` 또는 `false`로 반환합니다.
  [📎 Regex.test() MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test)

```
regexObj.test(str)
```

```jsx
let email = 'abc@e.com';
const valid = email => {
  return /^[a-zA-Z0-9+-_.]+@[a-zA-Z0-9-]+.[a-zA-Z0-9-.]+$/.test(email);
};
valid(email); // true
```

<details>
<summary>오늘도 밤새도록 돌아가는 console.log 공장 🏭 </summary>

```jsx
console.log(account);
// console.log(account.firstName);
// console.log('first name:' + firstNameRex.test(account.firstName));
// console.log('last name' + lastNameRex.test(account.lastName));
// console.log('email : ' + emailRex.test(account.email));
console.log('password: ' + passwordRex.test(account.password));
// console.log('passwordConfirm: ' + passwordRex.test(account.passwordConfirm));
// console.log('equal password: ' + equalPassword);
console.log('passwordCheck:  ' + passwordRex.test(account.passwordCheck));
// console.log(account.passwordCheck);
console.log('passwordConfirm:  ' + passwordConfirm);
//어지럽다..
```

</details>

## <p align="center"> 📆 2/9

### 🔥 Firebase

[📎 Firebase](https://console.firebase.google.com/?hl=ko)

- 코드과제를 위하여 파이어 베이스 입문
- 번거로운 백엔드 작업을 효율적으로 할 수 있는 플랫폼, 인증, 데이터베이스, 스토리지, 원격 구성, 푸쉬알림
- 여기서 내가 쓸 기능은 `인증`, `데이터베이스`, `스토리지` 정도로 추려진다.
- [📑 Firbase document](https://firebase.google.com/docs?authuser=0&hl=ko)
- 이니셜라이즈 하는 부분을 처음 배웠다.

```jsx
// 도큐먼트 세상
// 차근히 둘러보면 문서정리가 잘 되어있어 이해하기 쉽다...
import { getAuth, createUserWithEmailAndPassword } from 'firebase/auth';

const auth = getAuth();
createUserWithEmailAndPassword(auth, email, password)
  .then(userCredential => {
    // Signed in
    const user = userCredential.user;
    // ...
  })
  .catch(error => {
    const errorCode = error.code;
    const errorMessage = error.message;
    // ..
  });
```

### ✨ Initialize

- 함수, 클래스 컴포넌트만 사용하다 이렇게 이니셜라이즈 하는건 처음 해봤다.

```jsx
import { initializeApp } from 'firebase/app';
import { getAuth } from 'firebase/auth';
import { getFirestore } from 'firebase/firestore';
import { getStorage } from 'firebase/storage';

const firebaseConfig = {
  apiKey: //apiKey
  authDomain: //authDomain
  projectId: //projectId
  storageBucket: //storageBucket
  messagingSenderId: //messagingSenderId
  appId: //appId
};

export const app = initializeApp(firebaseConfig);
export const auth = getAuth();
export const storage = getStorage();
export const db = getFirestore();
```

> 그럼 이렇게 원하는 컴포넌트에 임포트 해주면 된다.

```jsx
import { createUserWithEmailAndPassword, updateProfile } from 'firebase/auth';
import { ref, uploadBytesResumable, getDownloadURL } from 'firebase/storage';
import { auth, storage, db } from '../Firebase';
import { doc, setDoc } from 'firebase/firestore';
```

### 🎊 가입정보 POST 하기

```jsx
const signup = async e => {
  e.preventDefault();

  try {
    const file = image;
    const res = await createUserWithEmailAndPassword(auth, email, password);
    const user = res.user;

    goToLogin();

    const storageRef = ref(storage, displayName);
    const uploadTask = uploadBytesResumable(storageRef, file);

    uploadTask.on(
      'state_changed',
      null,
      error => {
        console.log('error');
      },
      async () => {
        const downloadURL = await getDownloadURL(uploadTask.snapshot.ref);

        await updateProfile(user, {
          displayName: account.displayName,
          photoURL: downloadURL,
        });
        await setDoc(doc(db, 'users', res.user.uid), {
          uid: res.user.uid,
          displayName,
          email,
          photoURL: downloadURL,
        });
        await setDoc(doc(db, 'userChats', res.user.uid));
      }
    );
  } catch (error) {
    console.log('error!');
  }
};
```

- `firstName` & `lastName`으로 관리 하던 두 개의 `input`을 하나로 통일하고, 이름도 `displayName`으로 수정
- Firebase는 기본 auth 과정에서 `displayName`은 받지 않기에, `storage`를 통하여 업로드를 하였다.
  ```jsx
  //이 부분
  await updateProfile(user, {
    displayName: account.displayName,
    photoURL: downloadURL,
  });
  await setDoc(doc(db, 'users', res.user.uid), {
    uid: res.user.uid,
    displayName,
    email,
    photoURL: downloadURL,
  });
  ```

<details>
  <summary>리팩토링 전 회원가입 코드</summary>

```jsx
// 이메일, 패스워드로 인증하는 코드
// 날 것 그 자체
const signup = async e => {
  e.preventDefault();
  const file = image;
  const res = await createUserWithEmailAndPassword(auth, email, password)
    .then(userCredential => {
      const user = userCredential.user;
      alert('회원가입 성공!');
      goToLogin();
      console.log(user);
      const storageRef = ref(storage, displayName);
      const uploadTask = uploadBytesResumable(storageRef, file);
      uploadTask.on(
        error => {
          console.log('error');
        },
        () => {
          getDownloadURL(uploadTask.snapshot.ref).then(async downloadURL => {
            await updateProfile(res.user, {
              displayName: account.displayName,
              photoURL: downloadURL,
            });
          });
        }
      );
    })
    .catch(error => {
      console.log('error!');
      const errorCode = error.code;
      const errorMessage = error.message;
    });
};
```

</details>

## <p align="center"> 📆 2/10

### 🏞️ 이미지 띄워보기

- `profile` 이미지를 수집하긴 하는데, 들어가는지 너무 궁금했다.
- 확인 완료.

```jsx
const handleFile = e => {
  setImage(URL.createObjectURL(e.target.files[0]));
};

//...

<input type='file' onChange={handleFile} />;

{
  image && <img src={image} alt='selected image' />;
}
```

### 🔐 `로그인` 확인하기

- 백엔드와 통신할 때는 `token`이나 고유 auth 방법이 있었는데, Firebase는 token이 찍히지 않는다. 유일한 흔적은 `uid`
- `useState`를 활용하여 user의 상태를 관리한다.
- 그리고 `context`를 사용하여 상태관리중 23.02.15

```jsx
const [isLoggedIn, setIsLoggedIn] = useState(false);

onAuthStateChanged(auth, user => {
  if (user) {
    setIsLoggedIn(true);
  } else {
    setIsLoggedIn(false);
  }
});

const logout = () => {
  auth
    .signOut()
    .then(() => {
      console.log('Logged out');
    })
    .catch(error => {
      console.error(error);
    });
};

//

{
  isLoggedIn ? (
    <button className='logout' onClick={logout}>
      로그아웃
    </button>
  ) : (
    <>
      <li>
        <Link to='/login'>로그인</Link>
      </li>
      <li>
        <Link to='/signup'>회원가입</Link>
      </li>
    </>
  );
  //button과 link의 혼종
}
```

### 🤦‍♀️ 못생긴 `<Link to>` 스타일링

```
<Link to>는 a 링크이다
```

```scss
a {
  color: $pink;
  font-weight: 400;
}

a:-webkit-any-link {
  text-decoration: none;
  color: black;
}
```

> 👏👏👏👏

### 🔨 `<br/>` 쓰고 싶을 때

```scss
white-space: pre-wrap;
```

> CSS white-space 속성은 요소가 공백 문자를 처리하는 법을 지정합니다.

| &#32;        | 개행 문자 | 스페이스, 탭 | 자동 줄 바꿈 | 줄 끝의 공백 |
| ------------ | --------- | ------------ | ------------ | ------------ |
| normal       | 병합      | 병합         | 예           | 제거         |
| nowrap       | 병합      | 병합         | 아니오       | 제거         |
| pre          | 유지      | 유지         | 아니오       | 유지         |
| pre-wrap     | 유지      | 유지         | 예           | 넘침         |
| pre-line     | 유지      | 병합         | 예           | 제거         |
| break-spaces | 유지      | 유지         | 예           | 줄 바꿈      |

- `white-space` 속성 값 변경
- [📎 white-space](https://developer.mozilla.org/ko/docs/Web/CSS/white-space)

### state Value 전체를 `validation`로 쓰기

```jsx
const allValid = Object.values(isValid).every(Boolean);
```

## <p align="center"> 📆 2/14

## ☁️ Context

[📎 Context](https://ko.reactjs.org/docs/context.html#when-to-use-context)

```jsx
// Main.js
// before
const [isLoggedIn, setIsLoggedIn] = useState(false);
const [userName, setUserName] = useState('');

onAuthStateChanged(auth, user => {
  if (user) {
    setIsLoggedIn(true);
    setUserName(user.displayName);
  } else {
    setIsLoggedIn(false);
  }
});

// 로그인 여부를 확인하기 위해 onAuthStateChanged(auth, user) 를 확인하고, 값을 스테이트 담고
// 유저의 이름을 또 따로 저장하고... 😩
// 하지만 context로 한 줄로 해결했다.
// 물론 context는 여러줄이다.
```

```jsx
// Main.js
// after
const { currentUser } = useContext(AuthContext);
```

- 정말 간결해졌다.
- 로그인 정보를 → Nav애 전달하고 → Main 과 chat 컴포넌트에 사용해야한다
- 그럴때 필요한 context!

```
context를 이용하면 단계마다 일일이 props를 넘겨주지 않고도 컴포넌트 트리 전체에 데이터를 제공할 수 있습니다.
```

## 🤓 context 들여다보기

```jsx
import { createContext, useEffect, useState } from 'react';
import { auth } from '../pages/Firebase';
import { onAuthStateChanged } from 'firebase/auth';

export const AuthContext = createContext();

export const AuthContextProvider = ({ children }) => {
  const [currentUser, setCurrentUser] = useState({});

  useEffect(() => {
    const unsub = onAuthStateChanged(auth, user => {
      setCurrentUser(user);
      console.log(user);
    });

    return () => {
      unsub();
    };
  }, []);

  return (
    <AuthContext.Provider value={{ currentUser }}>
      {children}
    </AuthContext.Provider>
  );
};
```

### ⚠️ 고려할 점

- `context`의 주된 용도는 다양한 레벨에 *네스팅된 많은 컴포넌트에게 데이터를 전달*하는 것입니다. `context`를 사용하면 컴포넌트를 재사용하기가 어려워지므로 꼭 필요할 때만 쓰세요.

- 여러 레벨에 걸쳐 props 넘기는 걸 대체하는 데에 context보다 `컴포넌트 합성이 더 간단한 해결책`일 수도 있습니다.

### 📑 React.createContext API

```jsx
const MyContext = React.createContext(defaultValue);
```

- 트리 상위에서 가장 가까이 있는 짝이 맞는 Provider로부터 현재값을 읽습니다.
- 적절한 Provider를 찾지 못했을 때만 쓰이는 값

### ✨ Context.Provider

```jsx
<MyContext.Provider value={/* 어떤 값 */}>
```

- context의 변화를 알리는 역할
- Provider 하위에서 context를 구독하는 모든 컴포넌트는 Provider의 value prop가 바뀔 때마다 다시 렌더링

### ⚠️ 주의사항

- 다시 렌더링할지 여부를 정할 때 참조(reference)를 확인하기 때문에, Provider의 부모가 렌더링 될 때마다 불필요하게 하위 컴포넌트가 다시 렌더링 될 수 있음
- 이를 피하기 위해서는 값을 부모의 state로 끌어올리기

#### 그 외 오늘 한 일들

- [x] signup validation & function 90%
- [x] fixed: signup profile image upload
- [x] nav & main permission
- [x] scss mixin 적용
- [x] chat network flow check

### 🏞️ photoURL upload

- Issue #1
  - input file을 사용하여 이미지를 업로드 하지만, 데이터베이스에서 보이지 않았다.
- Issue #2

  - 선택된 file을 UI에 그려내고 싶었다.

- Try #1

  - 공식문서 활용, 실패
  - 이미 signup 함수에서 처리하고 있었다.

  ```jsx
  import { getStorage, ref } from 'firebase/storage';
  // Create a root reference
  const storage = getStorage();

  // Create a reference to 'mountains.jpg'
  const mountainsRef = ref(storage, 'mountains.jpg');

  // Create a reference to 'images/mountains.jpg'
  const mountainImagesRef = ref(storage, 'images/mountains.jpg');
  ```

- Try #2
  ```jsx
  e.target.files[0];
  ```
  - 업로드 된 파일의 0번 인덱스를 사용하는 것,

#### 📌 Solution

```jsx
const handleFile = e => {
  setImage(e.target.files[0]);
  setDisplayUserImg(URL.createObjectURL(e.target.files[0]));
};
```

- 두개의 state로 관리

| &#32; | image               | displayUserImg                            |
| ----- | ------------------- | ----------------------------------------- |
| 목적  | 데이터베이스 업로드 | UI rendering                              |
| code  | `e.target.files[0]` | `(URL.createObjectURL(e.target.files[0])` |

```jsx
await uploadBytesResumable(storageRef, file).then(() => {
  getDownloadURL(storageRef) //
    .then(async downloadURL => {
      try {
        await updateProfile(res.user, {
          displayName,
          photoURL: downloadURL,
        });

        await setDoc(doc(db, 'users', res.user.uid), {
          uid: res.user.uid,
          displayName,
          email,
          photoURL: downloadURL,
        });

        await setDoc(doc(db, 'userChats', res.user.uid), {});
        goToMain();
      } catch (err) {
        console.log(err);
      }
    });
});
```

> 무진장 길어진 통신 코드 😩

### ✨ 15일 todo list

- [] signup/signin refactoring
- [] signup loading UI design
- [] signup error UI design
- [] Chat function 마무리

---
