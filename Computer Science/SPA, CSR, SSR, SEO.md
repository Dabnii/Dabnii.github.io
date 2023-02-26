# <p align="center"> 🌐 SPA | SSR | CSR | SEO </p>

```
💡 Single-Page Application, SPA
- 👆하나의 HTML 페이지와 애플리케이션 실행에 필요한 JavaScript와 CSS 같은 모든 자산을 로드하는 애플리케이션
- 필요한 부분만 새롭게 로드 됨
```

## 👩‍🎨 CSR | Client Side Rendering

- SPA 트렌드 + CPU 성능 상승 + JS 표준화 (리액트, 뷰, 앵귤러등 프레임워크)의 발전
- `클라이언트`(사용자)가 모두 처리하는 것
- 서버에서 `전체 페이지를 렌더링 후`, `사용자가 요청할 때 마다 리소스를 서버에서 제공` 받아 클라이언트가 해석하고 렌더링 함
- 브라우저에서 자바스크립트로 콘텐츠를 렌더링 하는 것

### 👍 장점:

- 네이티브앱과 비슷한 인터렉션을 구현
- (서버)트래픽을 감소시키고 더 빠른 인터랙션을 제공
- 새로고침이 발생하지 않아 네이티브와 비슷한 경험을 할 수 있습니다

### 😮‍💨 단점:

- 사용자가 첫 화면을 보기까지 시간이 오래 걸릴 수 있다는 것 ( 첫 요청시 전체 페이지에 대한 모든 파일을 받기 때문)
- SEO (Searching Engine Optimization)에 취약
  - `검색엔진최적화` 검색엔진에서 찾기 쉽도록 사이트를 개선하는 프로세스
  - 비어있는 html 때문에, 검색엔진들이 웹페이지를 분석하는데 어려움을 겪음

### 📌 SEO: Solution

- `SSR` 적용
- 동적렌더링 [임시방안] (복잡하고 리소스가 많이 든다)

## 🌐 SSR | Server Side Rendering

- 클라이언트가 모든것을 처리하지 않고, 웹사이트에 접속하면 서버에서 필요한 데이터를 모두 가져와서 html을 만들고, 만들어진 HTML과 HTML파일을 동적으로 제어할 수 있는 소스코드와 함께 클라이언트에게 보낸다. 클라이언트는 잘 만들어진 HTML 문서를 사용자에게 바로 보여주게 된다.
- ✨ `서버`가 화면(view)을 그리는 `주체`가 됩니다

### 👍 장점:

- 페이지 로딩이 빠르다
- HTML에 모든 정보가 담겨 있어 SEO 가능

### 😮‍💨 단점:

- `Blinking issue`
  - 새로고침할 때 서버에서 데이터를 가져오는 동안 화면이 없어지는 현상
- 서버 과부화
  - 사용자가 서버에 데이터를 요청하는 횟수가 많아지기 때문
- TTV & TVI의 공백시간이 길다.
  - Time To View & Time To Interact
  - HTML → JS download → React → Now Interactive
  - 위의 순서로 진행되기 때문에 JS를 다 읽어도 동적으로 제어할 수 있는 자바스크립트 파일을 받아오지 않기 때문에 사용자가 클릭해도 처리할 수 없는 상태가 된다. 최종적으로 자바스크립트를 받아와야지만 사용자가 원하는 것을 처리할 수 있는 인터랙티브가 가능해진다.

---

CSR: 최종적으로 번들링 해서 사용자에게 보내주는 자바스크립트 파일을 어떻게 하면 효율적으로 많이 분할해서 첫번째로 사용자가 사이트를 보기 위해서 필요한 필수적인 요소들만 보낼 수 있을 지 에 대한 고민이 필요하다

SSR: TTV & TVI 공백시간을 줄이기 위한 고민

---

출처:

- https://ko.reactjs.org/docs/glossary.html#single-page-application
- https://medium.com/@NeotericEU/single-page-application-vs-multiple-page-application-2591588efe58
- https://www.ascentkorea.com/seo-for-spa/
- https://ctdlog.tistory.com/46
- https://www.youtube.com/watch?v=iZ9csAfU5Os
