# Semantic Web & Semantic Tag

- 시멘틱 태그와 시멘틱 웹의 차이
- `<img>` 태그를 사용하는 것과 `<div>` background-image 태그 사용 대한 차이점은 무엇일까?

### 🤔시멘틱의 뜻은 무엇일까요?

## 🔤 Semantic

relating to meaning in language or logic.

1. 의미의
2. 의미론의

<a href="https://www.google.com/search?q=What+does+semantic+meaning&rlz=1C5CHFA_enKR1020KR1020&oq=What+does+semantic+meaning&aqs=chrome..69i57j0i19i512j0i8i15i19i30.458j0j9&sourceid=chrome&ie=UTF-8">출처</a>

👆 '의미론적인 웹' 이라는 뜻으로. <br>
기계가 이해할 수 있는 형태로 제작된 웹을 의미합니다.

시맨틱 웹의 목표는 데이터의 의미에 대한 기계 이해 가능한 설명을 위한 수단을 정확하게 제공하는 것입니다. <br>

> The goal of the Semantic Web is exactly to provide means for machine understandable description of the meaning of data <br>
> finally, the Semantic Web is not really about the Web/HTML, it's about data - and in particular describing the meaning of data in a formal/unambiguous way <br>

### 시멘틱 웹의 목적

브라우저, 검색엔진, 개발자 모두에게 컨텐츠의 의미를 명확하게 전달하여 <br> `의미론 적` 으로 문서의 정보를 전달합니다.<br>
또한 검색엔진에 시맨틱 요소를 이용하여 효과적인 크롤링과 인덱싱에 용이하게 하는 기술입니다.

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

컴퓨터, 인간 모두가 쉽게 이해할 수 있도록 작성하는 것이 시멘틱 입니다.

## Semantic Elements in HTML

우리는 시멘틱 요소를 사용하여 `<div id="nav"> <div class="header"> <div id="footer">` 네비게이션, 헤더 그리고 푸터로 사용하는 것을 쉽게 볼수 있습니다.

HTML은 시멘틱 요소들이 웹페이지의 각 구간을 명확하게 설명하는 도구로 사용됩니다.

### HTML의 시멘틱 요소

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

## 시멘틱 태그와 시멘틱 웹의 차이

```html
<div>
  <img scr="#" alt="#" />
</div>
```

- 의미적요소 보다 디자인적 의미를 더 많이 가짐
- `alt`의 사용으로 이미지가 깨져도 어떠한 이미지 식별 가능

```css
a {
  backgound-image: #;
}
```

- 의미있는 태그가 아님
- 이미지가 깨지는 에러발생 시 아무런 정보를 노출 하지 않음
- 또한, 컴퓨터도 해당 태그 이미지를 이해할 수 없음

## 결론

에러발생시 사용자를 위해 어떠한 이미지인지 정보가 들어가야하고 <br>

- 웹을 검색엔진에 `더 많은`노출을 위하여 `시멘틱태그 img` 를 사용을 권장한다
- 의미가 없는, 디자인 요소 이미지 사용에는 background-image 사용이 적합하다.

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
