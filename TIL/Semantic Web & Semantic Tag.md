# <p align="center"> Semantic Web & Semantic Tag

- 시멘틱 태그와 시멘틱 웹의 차이
- `<img>` 태그를 사용하는 것과 `<div>` background-image 태그 사용 대한 차이점은 무엇일까?

### 🤔시멘틱의 뜻은 무엇일까요?
# 🔤 Semantic

relating to meaning in language or logic.

1. 의미의
2. 의미론의 <a href="https://www.google.com/search?q=What+does+semantic+meaning&rlz=1C5CHFA_enKR1020KR1020&oq=What+does+semantic+meaning&aqs=chrome..69i57j0i19i512j0i8i15i19i30.458j0j9&sourceid=chrome&ie=UTF-8">... 출처</a>

🔍 '의미론적인 웹' 이라는 뜻으로. <br>
기계가 이해할 수 있는 형태로 제작된 웹을 의미합니다.

`시맨틱 웹`의 목표는 데이터의 의미와 관련성를 부여하며,<br>
나아가 기계(컴퓨터)가 이해 가능한 설명을 위한 수단을 정확하게 제공하는 것입니다.

> The goal of the Semantic Web is exactly to provide means for machine understandable description of the meaning of data. finally, the Semantic Web is not really about the Web/HTML, it's about data - and in particular describing the meaning of data in a formal/unambiguous way <br>

<br>

## 🔍 시멘틱 웹의 목적

- 검색엔진 최적화 (SEO)
  - 크롤링
  - 인덱싱
- 컴퓨터와 인간의 명확한 이해

브라우저, 검색엔진, 개발자 모두에게 컨텐츠의 의미를 명확하게 전달하여 <br> `의미론 적` 으로 문서의 정보를 전달합니다.<br>
또한 검색엔진에 시맨틱 요소를 이용하여 효과적인 크롤링과 인덱싱에 용이하게 하는 기술입니다.
<br>

## Semantic and Non-semantic

```html
<!-- 의미 없는 요소 사용 예 -->
<div id="header">
 <span>오늘은 월요일 입니다<span>
</div>
```

```html
<!-- 시맨틱 태그 사용 예 -->
<header>
  <h1>오늘은 월요일 입니다</h1>
</header>
```

위의 두가지 코드를 확인 해 보았을 때, <br>
시멘틱 태그에서 확연한 차이를 찾을 수 있습니다.<br>

아래의 코드는 코드에 의미와 관련성이 추가 되어 있어
인간과 컴퓨터가 쉽게 이해할 수 있습니다.

즉, 컴퓨터와 인간 모두가 `쉽게 이해할 수 있도록 작성하는 것이 시멘틱` 입니다.

또한, 시멘틱 웹은 웹에 존재하는 수많은 웹페이지들에 `메타데이터(Metadata)`를 부여하여,<br>
기존의 잡다한 데이터 집합이었던 웹페이지를 `의미`와 `관련성`을 가지는 거대한 데이터베이스로 구축하고자 하는 발상입니다.<br>

> https://poiemaweb.com/html5-semantic-web

<br>

## 🌐 Semantic Elements in HTML

우리는 시멘틱 요소를 사용하여 <br>
`<div id="nav"> <div class="header"> <div id="footer">` <br>
네비게이션, 헤더 그리고 푸터로 사용하는 것을 쉽게 볼수 있습니다.<br>

HTML은 시멘틱 요소들이 웹페이지의 각 구간을 명확하게 설명하는 도구로 사용됩니다.<br>
<br>

### 🏷 HTML의 시멘틱 요소 (tag)

💡 `form`, `table`, `img` 등이 있으며 이들 태그는 content의 의미를 명확히 설명한다.

- `<article>`
- `<details>`
- `<aside>`
- `<figcaption>`
- `<figure>`
- `<footer>`
- `<header>`
- `<main>`
- `<mark>`
- `<nav>`
- `<section>`
- `<summary>`
- `<time>`

### non-semantic 요소

💡 `<div>`, `span`등 content에 대하여 어떠한 설명도 하지 않는다

## 시멘틱 태그와 시멘틱 웹의 차이

```html
<div>
  <img scr="#" alt="#" />
</div>
```

- 의미적요소 `정보` 사용으로 컴퓨터가 이해 가능
- `alt`의 사용으로 이미지가 깨져도 어떠한 이미지 식별 가능

```css
a {
  backgound-image: #;
}
```

- 의미있는 태그가 아님
- 이미지가 깨지는 에러발생 시 아무런 정보를 노출 하지 않음
- 컴퓨터도 해당 태그 이미지를 이해할 수 없음

## 결론

- 에러발생시 사용자를 위해 어떠한 이미지인지 정보가 들어가야하고 <br> 웹을 검색엔진에 `더 많은`노출을 위하여 `시멘틱태그 img` 를 사용을 권장한다
- 의미가 없는, 디자인 요소 이미지 사용에는 background-image tag 사용이 적합하다.

<hr>
출처:
  
- https://poiemaweb.com/html5-semantic-web
  
- https://chanho-yoon.github.io/web/web-semanticWeb-semanticTag/

- https://velog.io/@anhesu11/%EC%8B%9C%EB%A7%A8%ED%8B%B1-%EC%9B%B9%EA%B3%BC-%EC%8B%9C%EB%A9%98%ED%8B%B1-%ED%8B%B0%EA%B7%B8

- https://www.quora.com/What-are-the-main-differences-between-semantic-web-and-HTML-tags

- https://www.quora.com/What-is-difference-between-ordinary-web-and-semantic-web

- https://fierycoding.tistory.com/m/55

- https://www.w3schools.com/html/html5_semantic_elements.asp

E.O.D
