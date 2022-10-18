# 📍 All about Position & display(inline)

- position 속성

  - relative
  - absolute
  - fixed

- display
  - inline
  - inline-block
  - block

<hr>
<br>

## 📌 Position

CSS position 속성은 문서 상에 요소를 배치하는 방법을 지정합니다. <br>
top (en-US), right (en-US), bottom (en-US), left (en-US) <br>
속성이 요소를 배치할 최종 위치를 결정합니다.

| Static   | 요소를 문서 흐름에 맞추어 배치                                                                             |
| -------- | ---------------------------------------------------------------------------------------------------------- |
| relative | 이전 요소 (주로 부모 요소)에 `자연스럽게 연결`하여 위치를 지정                                             |
| absolute | `원하는 위치를 지정`해 배치                                                                                |
| fixed    | 지정한 `위치에 고정`하여 배치                                                                              |
| sticky   | 위치에 따라 동작방식이 달라짐. 요소의 임계점(scroll 박스 기준) 이전에는 <br> 그 이후에는 fixed와 같이 동작 |

<br>

```css
/* 상단 고정 네비게이션 만들기*/
position: sticky;
top: 0;
```

<br>
<hr>
<br>

# 🖥 Display

## `Inline`:

대표적으로 `<span>`이라는 태그의 성질로 content/text 크기만큼만 점유하고 동일 라인에 붙는 성질입니다.
'이 글씨는 두꺼운 효과를 주었다.'와 같이 text 내에 특정 부분에만 스타일을 간단히 줄때 많이 사용되죠.

🏷 inline tag

| Tag        | 설명                                                                   |
| ---------- | ---------------------------------------------------------------------- |
| `<span>`   | inline요소들을 그룹화하거나 영역을 나눌때 사용하는 태그입니다.         |
| `<a>`      | 링크를 통해 다른페이지, 문서 등을 연결해주는 태그입니다.               |
| `<img>`    | 이미지를 삽입하는 태그로 지정한 이미지경로를 통해 이미지를 불러옵니다. |
| `<button>` | 클릭할 수 있는 버튼을 생성하는 태그입니다.                             |
| `<br>`     | 줄바꿈할때 사용합니다.                                                 |
| `<input>`  | 사용자로부터 입력을 받을 때 사용하며 form태그 내부에서 많이 쓰입니다.  |
| `<script>` | javascript와 같은 스크립트 코드를 정의할때 사용합니다.                 |

- width/height 적용 불가
- margin/padding-top/bottom 적용 불가
- line-height 원하는 대로 적용 불가(span에 적용 불가, 감싸고 있는 div 전체 크기에만 영향)
  Width & Height are ignored. Margin & padding push elements away horizontally but not vertically.

  > 기타 inline tag <br> `<abbr>, <acronym>, <b>, <bdo>, <big>, <cite>, <code>, <dfn>, <em>, <i>, <kbd> , <label>, <map>, <object>, <output>, <q>, <samp>, <select>, <small>, <strong> , <sub>, <sup>, <textarea>, <time>, <tt>, <var>`

<br>

## `block` :

- block은 무조건 한 줄을 점유, 다음 태그는 다음 줄에 배치
- width, height값을 통해 크기를 지정할 수 있습니다.

🏷 Block tag

| Tag      | 설명                                          |
| -------- | --------------------------------------------- |
| `<div>`  | 영역을 나눌때 사용하는 태그 입니다            |
| `<p>`    | 문단 또는 문장을 나눌때 사용 <br>             |
| `<form>` | 사용자가 입력한 데이터를 서버로 전송하기 위함 |

> 기타 block 태그 <br> `<address>, <blockquote>, <canvas>, <fieldset>, <figcaption>, <figure>, <hr>, <main>, <noscript>, <pre> , <table>, <tfoot>, <video>`

Block elements break the flow tof a document. Width, Height, Width, Height, Margin & Padding are respected.

<br>

## `Inline-block` :

block 속성과 linine 속성을 모두 가지고 있는 형태 입니다.
block 속성처럼 width를 설정할 수 있으며 요소들이 순차적으로 가로로 배치됩니다.

- width/height 적용 가능
- margin/padding-top/bottom 적용 가능
- line-height 적용 가능
  다만 고려해야 할 것이 있습니다.
- inline-block 끼리 공백이 생기게 되는데, 이때는 상위 div에 { font-size: 0; } 를 적용하면 해결이 됩니다.
- inline-block 끼리 높이가 안맞을시 상위 공백이 생기는데, 이때는 { vertical-align: ---; } 값으로 top 등을 줘서 맞춰주시면 됩니다.

Behaved like an inline element except Width, Height, Marign & Padding are respected.

```css
/* inline to block or block to inline*/
h1 **{ display:iline;}**
or
span **{ display: block;}**
```

```css
/*인라인 요소는 가로세로가 적용되지 않아 인라인 블락을 사용*/
div {
  border: 5px solid #black;
  display: inline-block;
  /*margin: 10px;*/
}
```

```css
h1 {
  display: none;
}
/* Hide elements */
```

<br>
<hr>
<br>

# 🔁 Flex-box

- 플렉스박스(Flexbox)는 요소를 단일 차원(행 또는 열)에 배치합니다. <br>
- 💡 `Flexbox` :✨MAIN AXIS (본축) & CROSS AXIS (교차)✨ 하는 두 축으로 구성
- ✔️ 본축의 기본 방향은 왼쪽에서 오른쪽
- Flexbox is one-dimensional layout method for laying out items in rows or columns
  - 깨알 팁 💡 `grid`
    - grid는 2차원 레이아웃 시스템(수직, 수평 둘 다 가능)으로 분류
    - grid는 항목을 두 방향으로 레이아웃 할 수있는 반면 flex는 한 방향만 가능

## `Flex direction`

컨테이너 안에서 본축 방향을 결정하는 속성

```css
flex-direction: row; /* [디폴트] 좌-우 */
flex-direction: row-reverse; /*우-좌*/
flex-direction: column; /*상-하*/
flex-direction: column-reverse; /*하-상*/
```

### Justify-content

주축을 기준으로 요소와 콘텐츠를 어떻게 배치 할지 결정하는 속성 | 매번 좌 정렬이 아님 주축에따라 다름

```css
justify-content: flex-start;
justify-content: flex-end;
justify-content: center;
justify-content: space-between; /*컨테이너 끝 여백을 없애고 요소 사이에 여백을 만듬*/
justify-content: space-around; /*요소의 둘레에 같은 여백을 부여 | 오차가 발생함*/
justify-content: space-evenly; /*요소, 컨테이너 사이에 균등한 여백 부여*/
```

### WRAP

💡 **flex-wrap: wrap;**
주축이 수평일 때 새로운 행을 만들어 요소를 정렬하고 주축이 수직일 때는 새로운 열을 만들어 요소를 정렬하는 속성.

```css
flex-wrap: wrap-reverse;
flex-wrap: nowrap;
```

### `ALIGN ITEMS` | 교차축을 따라 아이템을 배열

**flex 컨테이너** 에 지정하는 속성이며, 교차축을 따라 **flex 항목**열을 정렬하는 방식을 지정합니다.

```css
align-tiems: flex-start;
align-tiems: flex-end;
align-items: baseline; /*텍스트라인에 정렬*/
```

### `ALIGN CONTENT`

행이나 열이 여러 개일 때 교차축을 중심으로 정렬하는 align-content

주축을 따라 **flex 항목** 행을 정렬하는 방식을 지정합니다.

```css
align-content: spcae-between;
align-content: flex-start;
align-content: center; /*랩 리벌스나 플레스가 적용 되어있어야 함*/
align-self: flex-end; /*한 아이템만 끝점에 맺음*/
```

### Flex sizing properties

```css
flex-grow: 1;
flex-shrink: 2; /*0을 넣으면 줄지 않는다능!*/
```

## `Flex basis`

Defines the initial size of an element before additional space is distributed. | 항목의 크기를 결정

## `Flex grow`

Controls the amount of available space an element should take up. Accepts a unit- less number value | 요소에 **공간이 있을 때**, 얼마나 차지 할지 결정 Flex basis보다 큰 값으로 늘어남 (비율값)

## `Flex shrink`

If items are larger than the container, they shrink according to flex-shrink. | 요소에 **공간이 없을 때**, 요소들이 줄어드는 비율을 통제, 값을 가진 요소가 먼저 줄어듬 (비율값)

### Flex 속기

```css
/* one value, width/height: flex-basis*/
flex:10em;
flex: 30%;
flex: min-content;

/*Two calues: flex-grow | flex-shrink */
flex: 1 30px

/*Three values: flex-grow | flex-shrink | flex-basis */
flex:2 2 10%
```

<hr>
출처:

- https://poiemaweb.com/css3-flexbox
- https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=leesd88&logNo=220682157303
- https://engkimbs.tistory.com/m/922
- https://calmdawnstudio.tistory.com/m/51
- https://developer.mozilla.org/ko/docs/Glossary/Flexbox
