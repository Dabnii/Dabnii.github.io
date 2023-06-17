# <p align="center">➡️ Next.js</p>

## Next.js 101

```
Next.js is a framework for building web applications
```

## 🪶 Main Features

1. Routing
2. Rendering
3. Data Fetching
4. Styling
5. Optimizations
6. Typescript
7. API Reference

### 🪄 Creat Next.js

```dart
$ npx create-next-app@latest --typescript
```

```dart
$ npx create-next-app@latest
```

- 생성 완료 후

```dart
$ npm run dev
```

> `url: http//localhost:3000` 으로 이동

### 📜 file structure

```dart
//package.json
"scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
    ...
}
```

### 💡 라이브러리와 프레임워크의 주요 차이점

- 주요 차이점은 `Inversion of Control`(통제의 역전)
- 📚 라이브러리에서 메서드를 호출하면 사용자가 제어 가능
- 그러나 🔧 프레임워크에서는 제어가 역전되어 프레임워크가 사용자를 호출

### 📚 라이브러리

- `사용자`가 파일 이름이나 구조 등을 정하고, `모든 결정`을 내림

### 🖼️ 프레임워크(Frame work)

- 파일 이름이나 구조 등을 정해진 `규칙`에 따라 만들고 따름

### 📄 Pages

- `index.js`
- 💡`파일명 = url`이 됨

```dart
export default function Home(){
    return "hi";
}
```

- 유저에게 보여주고 싶은것이 있다면 `export default function`을 사용해야 함
- `react import` 필수 아님
  - 프레임워크라 자동으로 불러 오기 때문

## Server Side Rendering

- [https://github.com/Dabnii/Dabnii.github.io/blob/main/Computer Science/SPA%2C CSR%2C SSR%2C SEO.md#-ssr--server-side-rendering](https://github.com/Dabnii/Dabnii.github.io/blob/main/Computer%20Science/SPA%2C%20CSR%2C%20SSR%2C%20SEO.md#-ssr--server-side-rendering)

## Pre-Rendering

- 미리 렌더링됨
  - 쉽게 말해, 빈 화면이 보이지 않음
- `static`
- 초기 상태로 pre-rendring 을 진행
- hydration
- 구글 엔진, SEO 유리

### Routing

```dart
import Link from 'next/link'
import { useRouter } from 'next/router';

export default function Navbar(){
const router = useRouter();
    return(
    <nav>
        <Link href="/">
           <a style={{color:router.pathname === "/" ? "red" : "blue"}}>Home</a>
        </Link>
        <Link href="/about">
        <a style={{color:router.pathname === "/about" ? "red" : "blue"}}>about</a>
        </Link>
    </nav>
    );
}
```

### CSS modules

- Next.js는[name].module.css 파일 명명 규칙을 사용하여 CSS Module을 지원
- `Scoped`컴포넌트 안에서 클래스 네임을 공유
  - 오염 되지 않음
- 무작위 클래스 네임을 제공

```dart
1. className={`${styles.link} ${router.pathname === "/" ? styles.active : ""}`}
2. [styles.link, router.pathname === "/" ? styles.active : ""].join(" ")
```

### styles jsx

```jsx
<style jsx>
  {`
        CSS 스타일..
		`}
</style>
```

```jsx
<nav className='{styles.nav}'>
  <Link href='/'>
    <a className={router.pathname === '/' ? 'active' : ''}>Home</a>
  </Link>
  <Link href='/about'>
    <a className={router.pathname === '/about' ? 'active' : ''}>about</a>
  </Link>
  <style jsx>
    {`
      nav {
        background-color: tomato;
      }
      a {
        text-decoration: none;
      }
      .active {
        color: yellow;
      }
    `}
  </style>
</nav>
```

### Built-In CSS Support (내장 CSS 지원)

```
Next.js를 사용하면 JavaScript 파일에서 CSS 파일을 가져올 수 있습니다.
이것은 Next.js가 import 개념을 JavaScript 이상으로 확장하기 때문에 가능합니다.
```

### CSS-in-JS

```
격리된 범위 CSS에 대한 지원을 제공하기 위해 styled-jsx를 번들로 제공합니다. 목표는 불행히도 서버 렌더링을 지원하지 않고 JS 전용인 Web Components와 유사한 "Shadow CSS"를 지원하는 것입니다.
```

- [🔗 CSS-in-JS](https://nextjs.org/docs/basic-features/built-in-css-support#css-in-js)

### styled-jsx

- [🔗 styled-js](https://github.com/vercel/styled-jsx)

### Adding Component-Level CSS

- Next.js는[name].module.css 파일 명명 규칙을 사용하여 CSS Module을 지원합니다.

### Sass Support

- ㄴ`Next.js를 사용하면.scss 및.sass 확장자를 모두 사용하여 Sass를 가져올 수 있습니다.`

### 📂 \_app.js

- `_app.js`
- global 속성
- props로 global을 사용

```jsx
<style jsx global>{
	`
		css:
	`
}
```

### App component

```jsx
export default function App({ Component, pageProps }) {
  reutrn(
    <div>
      <Component {...pageProps} />
      <span>hello</span>
    </div>
  );
}
```

### Patterns

- `layout pattern`
- `children` = props

  - component를 다른 component에 주입 할 때 사용

  ```jsx
  import Head from 'next/head';

  export default function Seo({ title }) {
    return (
      <Head>
        <title>{title} | Next movie</title>
      </Head>
    );
  }
  ```

  ```jsx
  import Seo from '../components/Seo';

  export default function Potato() {
    return (
      <div>
        <Seo title='About' />
        <h1> About</h1>
      </div>
    );
  }
  ```

### 🛜 Fetching Data

```jsx
import { useEffect } from 'react';
import { useState } from 'react';

const API_KEY = '10923b261ba94d897ac6b81148314a3f';

export default function Potato() {
  cosnt[(movies, setMovies)] = useState([]);

  useEffect(() => {
    async () => {
      const { results } = await (
        await fetch(
          `hhtp://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`
        )
      ).json();
      console.log(results);
      setMovies(results);
    };
  }, []);

  return (
    <div>
      {movies?.map(movie => (
        <div key={movie.id}>
          <h4>{movie.original_title}</h4>
        </div>
      ))}
    </div>
  );
}
```

### `next.config.js`

- Next.js에서 커스텀 설정을 하기 위해서는 프로젝트 디렉터리의 루트(package.json 옆)에 next.config.js 또는 next.config.mjs 파일을 만들 수 있습니다. next.config.js는 JSON 파일이 아닌 일반 Node.js 모듈입니다.
- Next.js 서버 및 빌드 단계에서 사용되며 브라우저 빌드에는 포함되지 않습니다.
- https://nextjs.org/docs/api-reference/next.config.js/introduction

# <P align="center"> 🔃 Redirect and Rewrite </p>

### 💡 구성요소 & 요약

1. `next.config.js`
2. `Redirects`- 💡 URL 변경
3. `Rewrites` - 💡URL 변경 X , URL 프록시 역할

| Redirects      | Rewrites          |
| -------------- | ----------------- |
| URL 변경       | URL 변경 X        |
| -              | URL 프록시 역할   |
| URL 이동       | URL 변경사항 표시 |
| 비동기         | 비동기            |
| 영구적& 일시적 |                   |

## 🗺️ Redirect | 비동기

```jsx
module.exports = {
  async redirects() {
    return [
      {
        source: '/about',
        destination: '/',
        permanent: true,
      },
    ];
  },
};
```

- 들어온 요청을 다른 path로 이동 `URL 이동`
- `next.config.js`의 `redirects`키를 사용
- `source` 요청이 들어 오는 곳
- `destination` 최종 목적지: 이동할 라우터
- `permanent` `true` or `false`
  - if `true` : `308 status` 영구적
  - if `false`: `307 status` 일시
- destination으로 이동해도 URL은 그대로, 유저는 모른다!

## 🌐 Server side render

```
getServerSideProps 함수 사용
```

### `getServerSideProps`

```jsx
export async function getServerSideProps() {
  //run on the server
  //only backend read
  //client에게 정보를 숨길 수 있음
}
```

```jsx
export default function Home({ result }) {
  //... result 값을 보내주는 곳
  //페이지 렌더
}

export async function getServerSideProps() {
  const { result } = await (await fetch(`local/host...`)).json();
  return {
    props: {
      results,
      //data
      //프롭스로써 page에게 주게 됨
    },
  };
}
```

## ✏️ Rewrites

- 위치를 변경하지 않은 것 처럼 보이게 함
- URL를 매핑하듯 mask하여 유저에게 노출 하지 않음

```jsx
module.exports = {
  async rewrites() {
    return [
      {
        source: '/about',
        destination: '/',
      },
    ];
  },
};
```

```jsx
// next.config.js
const API_KEY = process.env.API_KEY;

module.exports = {
  //redirection에 필요
  reactStrictMode: true,
  async redirects() {
    return [
      {
        source: '/old-blog/:path*',
        destination: '/new-sexy-blog/:path*',
        permanent: false,
      },
    ];
  },
  async rewrites() {
    return [
      {
        source: '/api/movies',
        destination: `https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`,
      },
      {
        source: '/api/movies/:id',
        destination: `https://api.themoviedb.org/3/movie/:id?api_key=${API_KEY}`,
      },
    ];
  },
};
```

- `getServerSideProps` 에서 반환됨 데이터 ⇒ 📜 `requst`에서 해당 페이지 pre-render
- 서버측에서만 실행 ≠ 브라우저 실행
- [🔗next.config.js Options](https://nextjs.org/docs/pages/api-reference/next-config-js)

### `getServerSideProps`를 사용하여 request시 데이터 fetch하기

다음 예는 request 시 데이터를 fetch하고 결과를 pre-render하는 방법을 보여줍니다.

```jsx
//example #1
export default function Home({ data }) {
  // 데이터 렌더링
}

// 매 request마다 실행
export async function getServerSideProps() {
  const res = await fetch(`https://.../data`);
  const data = await res.json();
  // props를 통해 page에 data전달
  return { props: { data } };
}
```

```jsx
//example #2
import type { InferGetServerSidePropsType, GetServerSideProps } from 'next'

type Repo = {
  name: string
  stargazers_count: number
}

export const getServerSideProps: GetServerSideProps<{
  repo: Repo
}> = async () => {
  const res = await fetch('https://api.github.com/repos/vercel/next.js')
  const repo = await res.json()
  return { props: { repo } }
}

export default function Page({
  repo,
}: InferGetServerSidePropsType<typeof getServerSideProps>) {
  return repo.stargazers_count
}
```

- https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props#using-getserversideprops-to-fetch-data-at-request-time
- https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props

## 🏄‍♂️ Dynamic Routes

- 정확한 segment name을 모를 때 동적 라우팅을 하려는 경우 Dynamic segment를 설정할 수 있다
- Nest Route와 비슷하다

### 🤙 Convention

- `[slug].js` ⇒ 폴더 이름을 대괄호로 묶어 생성

  ```jsx
  import { useRouter } from 'next/router';

  export default function Page() {
    const router = useRouter();
    return <p>Post: {router.query.slug}</p>;
  }
  ```

  | Route                | Example URL | params        |
  | -------------------- | ----------- | ------------- |
  | pages/blog/[slug].js | /blog/a     | { slug: 'a' } |
  | pages/blog/[slug].js | /blog/b     | { slug: 'b' } |
  | pages/blog/[slug].js | /blog/c     | { slug: 'c' } |

### ⚾ Catch-all Segments

- `catch-all` 로 확장할 수 있음
- `[…folderName].js`
- For example, `pages/shop/[...slug].js` will match `/shop/clothes`, but also `/shop/clothes/tops`, `/shop/clothes/tops/t-shirts`, and so on.

  | Route                   | Example URL | params                    |
  | ----------------------- | ----------- | ------------------------- |
  | pages/shop/[...slug].js | /shop/a     | { slug: ['a'] }           |
  | pages/shop/[...slug].js | /shop/a/b   | { slug: ['a', 'b'] }      |
  | pages/shop/[...slug].js | /shop/a/b/c | { slug: ['a', 'b', 'c'] } |

- `[variable].js` `[movieID].js`

  - URL에 변수를 넣는 방법
  - `[variable].js` == query!

    ```jsx
    import { useRouter } from 'next/router';

    export default function Detail() {
      const router = useRouter();
      return 'detail';
    }
    ```

---

Ref:

- [Lecture – 노마드 코더 Nomad Coders](https://nomadcoders.co/nextjs-fundamentals/lectures/3454)
- [Next.js by Vercel - The React Framework](https://nextjs.org/)
- [Docs](https://nextjs.org/docs)
