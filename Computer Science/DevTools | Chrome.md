# <p align="center"> ⚒️ DevTools | Chrome


- 각 브라우저는 개발자 도구(tool)를 가지고 있습니다.<br>
  - e.g. Chrome 개발자 도구, IE 개발자 도구, Safari 개발자도구.etc
- 즉각적으로 에러/문제 확인 가능  

> Chrome DevTools is a set of web developer tools built directly into the Google Chrome browser. DevTools can help you edit pages on-the-fly and diagnose problems quickly, which ultimately helps you build better websites, faster.


## ⚒️ DevTools을 열어보자!

 &#32; | 단축키
--|--|
Open DevTools | `cmd + option + i` / `ctrl + shift + i`
Open Elements Panel | `cmd + option + c`
Open Console Panel  | `cmd + option + j`


## ⚒️ DevTools의 자주 사용되는 대표 패널 4가지

  - Element panel
  - Console panel
  - Network panel
  - Application panel


# 📌 Element 패널

## 📌 `Elements`패널의 기능은?

- CSS와 HTML을 확인할 수 있는 창
- 최상단 좌측 (박스위 커서) 페이지와 스타일 검사 및 편집
- 웹 페이지의 구성 (DOM)
- 클릭으로 `특정요소`를 클릭하면 찾을 수 있음
- CSS 구조/수정 가능


## 📌 `Styles` 부분의 순서가 의미하는 것은?

- 하나의 요소에 여러개의 css 파일에서 스타일 적용 가능
- 가장 상단부터 css 파일의 우선 순위(구체적 → 추상적) 에 따른 순서
- cf) CSS Specificity - inline style > id > class > tag

## 📌 `user agent stylesheet` 란?

- 각 브라우저가 정해놓은 CSS 규칙
- 브라우저의 기본 스타일 값을 의미. 브라우저 마다 스타일 기본값이 상이
- Chrome, Safari, IE 등 브라우저의 종류에 따라 기본적으로 설정되어 있는 속성 값이 다르기 때문에 개발 시작 단계에서 reset.css 혹은 normalize.css 파일에서 기본 스타일 값을 모두 초기화 시키고 작업 시작. >>> 브라우저의 종류에 상관 없이 동일한 화면 출력 가능!


# ✏️ Console 패널
-  `console`은 객체!
- 자주 사용하는 `console.log`외 다양한 메소드가 있습니다.
   - `console.log` 일반 메시지를 출력합니다. 추가 매개변수와 함께 문자열 치환 사용 가능
   - `console.clear()` 콘솔의 내용을 지웁니다.
        - <a href="https://developer.mozilla.org/ko/docs/Web/API/Console">MDN | See more</a>

## ✏️ `Console` 패널의 기능은?

- 자바스크립트 즉시 테스트가능
- 오류 발생시 디버깅을 통하여 찾기 쉽다
- 단축키:
    - Windows 기준 `F12` 또는 `ctrl + shift + i`
    - MacOS 기준 `cmd + option + i`
    - 우클릭 → 검사
        - 에러에 친숙해 지기 💪

## ✏️ 화면을 새로고침 해도 `console` 내용이 지워지지 않고 남게 하는 방법은?

- 톱니바퀴 → 네트워크 → Preserve log (check)

## ✏️ 콘솔에 기록된 로그를 모두 지울 때 사용하는 메소드는?

- `console.clear`

## ✏️콘솔에서 `Warnings`, `Errors`내용을 제외하고 보는 방법은?

- Warning & Errors 메세지 체크

## ✏️ 다른 패널(ex. Elements panel)에서 
Console Panel 같이 보는 방법은?

- ESC 누르면 콘솔 패널 사용가능

### ✏️ `console.log()` 실제 활용 예시
- 프론트엔드의 경우 실제로 디버깅 시 다른 도구를 사용하는 것보다 console.log 를 활용하는 경우가 대부분입니다.
- 백엔드에서 보내주는 response(ex. 에러 메세지, status 코드)도 아래 예시와 같이 console.log를 활용해 확인 가능합니다.
- 그렇기 때문에 백엔드에서는 상황을 명확하게 알려주는 response 메세지와 적절한 status code를 전달하는 것이 중요합니다!


## 🌐 Network 패널의 기능은?

- `통신`과 관련된 패널
    - http 네트워크 통신 확인
    - 데이터를 서버에서 불러올 때
    - 디버깅 할 때
    - API 크롤링, 페이지 로딩 성능 테스트
    
    - 빨간불 🔴 : 기록중
    - 검정불 ⚫️ : 기록이 되지 않는 중
- Filter 와 Search
- Fetch :
    - FE: UI
    - BE: Data를 어떻게 줄지, 어떻게 데이터가 통신하는지 확인하는 패널
- Headers: API주소
    - method: 통신의 약어
- Preserve log
    - 체크시 로그를 유지한채 페이지 이동가능
        - 네트워크 상태에 맞춰 설정가능 | 기본값은 웹사이트 기본값에 맡김
    - 상태코드 200 정상수신 | 400 에러 | 500 서버 오류 💪


## 🌐 내부 살펴보기
- All, XHR, JS, CSS, Img, Media ...
- `XHR(Xml(Extensible Markup Language) Http Request)` - 브라우저와 서버가 HTTP 통신 할 때 request 전문이 어떻게 구성되어 서버로 전달 되는지, 서버로 부터 요청에 따른 response 결과를 확인할 때 사용한다. (HTTP 세션 시간에 관련 내용 자세하게 다룰 예정)

# 🗂 어플리케이션 패널

- 브라우저에 저장한 스토리지
- 로그인 유저 권한 저장할 때
- 브라우저에서 저장할 많은 저장소들과 캐시, 스토리지들이 많이 있다. 로그인과 관련해서 유저 정보에 대한 부분에도 많은 부분을 차지하기 때문에 `꼭 알아두어야 할 패널`


## 🗂 로컬스토리지 | 브라우저 저장소
> - 세가지 모두 키-값 데이터 저장소이지만, 데이터 저장 기한에서 가장 큰 차이를 보인다.<br>
> - storage : 브라우저의 저장소 

###  🗂 Local storage 
- Local Storage라는 컬렉션을 통해 저장과 조회
- 지속적으로 필요한 데이터(data persistant)(ex. ID 저장, 비회원 카트)
- UI 정보들(ex. 에어비앤비, 스카이스캐너 인천공항 - 베네치아 검색하면 그대로 유지)
- Local Storage는 브라우저를 종료해도 데이터는 보관되어 다음번 접속에도 그 데이터를 사용할 수 있다.
- 데이터의 영구성 보장
    - 저장한 데이터를 명시적으로 지우지 않는 이상 `영구적으로 보관 가능`
    - 만료일이 없는 데이터를 저장하고 JavaScript를 통해서만 삭제 가능
- `도메인마다 별도로 로컬 스토로지가 생성`
    - Local Storage는 도메인만 같으면 전역적으로 공유 가능
## 🗂 Session storage
- 보안이 중요한 임시 데이터 (은행 로그인,비로그인 장바구니). 민감한 데이터.
## 🍪 Cookie
- 빠른 처리가 필요한 임시 데이터(이벤트나 광고 팝업,서비스약관)
- ⚠️ (비밀번호와 같은 중요정보는 스토리지에 저장하면 안된다. 로컬스토리지나 세션 스토리지는 클라이언트 사이드이기에 쉽게 해킹당할 수 있다)
- indexDB & WeSQL은 클라이언트 side입니다.
- 데이터를 저장하는 방식은 회사 바이 회사 입니다. 

### 🗄 로컬스토리지 데이터 불러오기

- `setItem` 함수로 키와 값 주입
- `getItem` 함수로 지정한 키로 값을 가져온다.

### 🗄 로컬 스토리지에 특정데이터를 저장하고 저장한 데이터를 접근해서가져오는 방법
<✍️ 세팅하는 법>

- `localStorage.setItem("key", "value")`
- `sessionStorage.setItem("key", "value")setcookie("key","value","지속시간")`

<🔍 스토리지 접근해서 값 가져오는 법>
- `localStorage.getItem("key")`
- `sessionStorage.getItem("key")document.cookie`

<✂️ 스토리지 접근해서 값 지우기>
- `localStorage.removeItem(key)`

<br>

# 🗂 Session 스토리지

- 탭마다 세션 스토리지 쌓임
- 끄면 사라지는 휘발성 스토리지
- 일회성 조회
- 새로고침을 했을 땐 유지가 됨
- 브라우저가 열려있는 상황에는 유지
- Http/ https 차이로 다른 스토리지 세션에 저장이 됩니다

## 🍪 내가 만든 `쿠키`

- 웹페이지 방문시 `방문 기록같은 브러우저에서의 정보들이 저장된 텍스트 파일`
        - 웹서버가 브라우저에 보내저장했다가 서버의 요청이 있을때 다시 서버로 전송
- `4kb 이하의 작은 데이터`
- 서비스 직접적이지 않은 데이터, 오늘만 하는 이벤트 팝업, 서비스 약관에 동의했는지 등...

> ‼️ 클라이언트 사이드인 로컬&세션스토리지는 해킹이 쉬워 중요한 정보는 저장하지 않습니다.

<hr>
출처:

- https://developer.chrome.com/docs/devtools/
- https://www.youtube.com/watch?v=x4q86IjJFag&t=2698s