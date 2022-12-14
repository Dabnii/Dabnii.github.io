# <p align="center"> ๐ Event JavaScript

## Event JavaScript ์ ์

### ๐ก `EventTarget.addEventListener()`

1. EventTarget ์ธํฐํ์ด์ค์ addEventListener() ๋ฉ์๋๋ ์ง์ ํ ์ ํ์ `์ด๋ฒคํธ๋ฅผ ๋์์ด ์์ ํ  ๋๋ง๋ค ํธ์ถํ  ํจ์๋ฅผ ์ค์ `ํฉ๋๋ค.

2. ์ผ๋ฐ์ ์ธ ๋์์ Element, Document, Window์ง๋ง, XMLHttpRequest์ ๊ฐ์ด ์ด๋ฒคํธ๋ฅผ ์ง์ํ๋ `๋ชจ๋  ๊ฐ์ฒด๊ฐ ๋์`์ด ๋  ์ ์์ต๋๋ค.

3. e.g. addEventListener()๋ document์ ํน์ ์์(Id,class,tag ๋ฑ๋ฑ..) event(ex - clickํ๋ฉด ํจ์๋ฅผ ์คํํ๋ผ, ๋ง์ฐ์ค๋ฅผ ์ฌ๋ฆฌ๋ฉด ํจ์๋ฅผ ์คํํ๋ผ ๋ฑ๋ฑ.. )๋ฅผ ๋ฑ๋กํ  ๋ ์ฌ์ฉํฉ๋๋ค.

## ๋ํ Event ์ข๋ฅ <a href="https://developer.mozilla.org/en-US/docs/Web/Events">[See more MDN]</a>

### ๐ฅณ UI Event

| Event          | Description                                                              |
| -------------- | ------------------------------------------------------------------------ |
| ๐ <b>load</b> | ์นํ์ด์ง์ ๋ก๋๊ฐ ์๋ฃ๋์์ ๋                                          |
| unload         | ์นํ์ด์ง๊ฐ ์ธ๋ก๋๋  ๋(์ฃผ๋ก ์๋ก์ด ํ์ด์ง๋ฅผ ์์ฒญํ ๊ฒฝ์ฐ)                 |
| error          | ๋ธ๋ผ์ฐ์ ๊ฐ ์๋ฐ์คํฌ๋ฆฝํธ ์ค๋ฅ๋ฅผ ๋ง๋ฌ๊ฑฐ๋ ์์ฒญํ ์์์ด ์กด์ฌํ์ง ์๋ ๊ฒฝ์ฐ |
| resize         | ๋ธ๋ผ์ฐ์  ์ฐฝ์ ํฌ๊ธฐ๋ฅผ ์กฐ์ ํ์ ๋                                         |
| scroll         | ์ฌ์ฉ์๊ฐ ํ์ด์ง๋ฅผ ์์๋๋ก ์คํฌ๋กคํ  ๋                                   |
| select         | ํ์คํธ๋ฅผ ์ ํํ์ ๋                                                     |

### ๐ฅณ Keyboard Event

| Event           | Description            |
| --------------- | ---------------------- |
| keydown         | ํค๋ฅผ ๋๋ฅด๊ณ  ์์ ๋    |
| ๐ <b>keyup</b> | ๋๋ฅด๊ณ  ์๋ ํค๋ฅผ ๋ ๋ |
| keypress        | ํค๋ฅผ ๋๋ฅด๊ณ  ๋์ ๋    |

### ๐ฅณ Mouse Event

| Event          | Description                                                       |
| -------------- | ----------------------------------------------------------------- |
| ๐<b>click</b> | ๋ง์ฐ์ค ๋ฒํผ์ ํด๋ฆญํ์ ๋                                         |
| dbclick        | ๋ง์ฐ์ค ๋ฒํผ์ ๋๋ธ ํด๋ฆญํ์ ๋                                    |
| mousedown      | ๋ง์ฐ์ค ๋ฒํผ์ ๋๋ฅด๊ณ  ์์ ๋                                      |
| mouseup        | ๋๋ฅด๊ณ  ์๋ ๋ง์ฐ์ค ๋ฒํผ์ ๋ ๋                                   |
| mousemove      | ๋ง์ฐ์ค๋ฅผ ์์ง์ผ ๋ (ํฐ์น์คํฌ๋ฆฐ์์ ๋์ํ์ง ์๋๋ค)               |
| mouseover      | ๋ง์ฐ์ค๋ฅผ ์์ ์๋ก ์์ง์์ ๋ (ํฐ์น์คํฌ๋ฆฐ์์ ๋์ํ์ง ์๋๋ค)   |
| mouseout       | ๋ง์ฐ์ค๋ฅผ ์์ ๋ฐ์ผ๋ก ์์ง์์ ๋ (ํฐ์น์คํฌ๋ฆฐ์์ ๋์ํ์ง ์๋๋ค) |

### ๐ฅณ Focus Event

| Event                    | Description               |
| ------------------------ | ------------------------- |
| ๐ <b>focus</b>/focusin  | ์์๊ฐ ํฌ์ปค์ค๋ฅผ ์ป์์ ๋ |
| ๐ <b>blur</b>/foucusout | ์์๊ฐ ํฌ์ปค์ค๋ฅผ ์์์ ๋ |

### ๐ฅณ Form Event

| Event            | Description                                                                                                       |
| ---------------- | ----------------------------------------------------------------------------------------------------------------- |
| ๐ <b>input</b>  | - input ๋๋ textarea ์์์ ๊ฐ์ด ๋ณ๊ฒฝ๋์์ ๋<br> - contenteditable ์ดํธ๋ฆฌ๋ทฐํธ๋ฅผ ๊ฐ์ง ์์์ ๊ฐ์ด ๋ณ๊ฒฝ๋์์ ๋ |
| ๐ <b>change</b> | select box, checkbox, radio button์ ์ํ๊ฐ ๋ณ๊ฒฝ๋์์ ๋                                                         |
| submit           | form์ submitํ  ๋ (๋ฒํผ ๋๋ ํค)                                                                                 |
| ~~eset~~         | ~~reset ๋ฒํผ์ ํด๋ฆญํ  ๋ (์ต๊ทผ์๋ ์ฌ์ฉ ์ํจ)~~                                                                   |

## Clipboard Event

| Event | Description            |
| ----- | ---------------------- |
| cut   | ์ฝํ์ธ ๋ฅผ ์๋ผ๋ด๊ธฐํ  ๋ |
| copy  | ์ฝํ์ธ ๋ฅผ ๋ณต์ฌํ  ๋     |
| paste | ์ฝํ์ธ ๋ฅผ ๋ถ์ฌ๋ฃ๊ธฐํ  ๋ |

```javascript
canvas.addEventListener("dblclick", onDoubleClick);
canvas.addEventListener("mousemove", onMove);
canvas.addEventListener("mousedown", startPainting);
canvas.addEventListener("mouseup", cancelPainting);
canvas.addEventListener("mouseleave", cancelPainting);
canvas.addEventListener("click", onCanvasClick);
```

MouseEvent.offsetX
The offsetX read-only property of the MouseEvent interface provides the offset in the X coordinate of the mouse pointer between that event and the padding edge of the target node.

Value
A double floating point value.

```javascript
ctx.lineTo(event.offsetX, event.offsetY);
```

EventTarget()
EventTarget() ์์ฑ์๋ ์๋ก์ด EventTarget ๊ฐ์ฒด ์ธ์คํด์ค๋ฅผ ์์ฑํฉ๋๋ค.

```
new EventTarget();

```

mouse ์ด๋ ์ด๋ฒคํธ

`mousemove`

1. ClientX, ClientY
   ํด๋ผ์ด์ธํธ ์์ญ(ํ์ฌ ๋ณด์ฌ์ง๋ ๋ธ๋ผ์ฐ์  ํ๋ฉด ๊ธฐ์ค)์ ๊ธฐ์ค์ผ๋ก ๊ฐ๋ก, ์ธ๋ก ์ขํ๋ฅผ ์ ๊ณต

clientX - ์คํฌ๋กค์ ๋ฌด์ํ๊ณ  ํด๋นํ์ด์ง ์๋จ์ 0์ผ๋ก ์ธก์ ํ์ฌ ํด๋ผ์ด์ธํธ ์์ญ์์ X์์น๋ฅผ ๋ฐํ

clientY - ์คํฌ๋กค์ ๋ฌด์ํ๊ณ  ํด๋นํ์ด์ง ์๋จ์ 0์ผ๋ก ์ธก์ ํ์ฌ ํด๋ผ์ด์ธํธ ์์ญ์์ Y์์น๋ฅผ ๋ฐํ

2. OffsetX, OffsetY
   ์ด๋ฒคํธ ๋์์ ๊ธฐ์ค์ ์ขํ ex) ํ๋ฉด ์ค์์ ๋ฐ์ค ์์์์ ํด๋ฆญํ ์์น๋ฅผ ์ฐพ์ผ๋ฉด ๋ฐ์ค์ ์ผ์ชฝ ๋ชจ์๋ฆฌ ์ขํ๊ฐ 0์ผ๋ก ์ธก์ ๋จ

offsetX - ์ด๋ฒคํธ ๋์์ ๊ธฐ์ค์ผ๋ก ์๋์  ๋ง์ฐ์ค x์ขํ ๋ฐํ

offsetY - ์ด๋ฒคํธ ๋์์ ๊ธฐ์ค์ผ๋ก ์๋์  ๋ง์ฐ์ค y์ขํ ๋ฐํ

3. pageX, pageY
   ์คํฌ๋กค์ ํฌํจํ ์ ์ฒด ๋ฌธ์๋ฅผ ๊ธฐ์ค์ผ๋ก x,y ์ขํ๋ฅผ ๋ฐํ

pageX - ๋ธ๋ผ์ฐ์  ์ ์ฒด ํ์ด์ง์์ x์ขํ ๋ฐํ

pageY - ๋ธ๋ผ์ฐ์  ์ ์ฒด ํ์ด์ง์์ y์ขํ ๋ฐํ

4. screenX, screenY
   ๋ชจ๋ํฐ ํ๋ฉด์ ๊ธฐ์ค์ผ๋ก ์ขํ์ ๊ณต

screenX - ์ ์ฒด ๋ชจ๋ํฐ ์คํฌ๋ฆฐ์์ x์ขํ ๋ฐํ

screenY - ์ ์ฒด ๋ชจ๋ํฐ ์คํฌ๋ฆฐ์์ y์ขํ ๋ฐํ

<hr>
์ถ์ฒ:

- https://hmk1022.tistory.com/entry/clientX-offsetX-pageX-screenX-%EC%B0%A8%EC%9D%B4%EC%A0%90
- https://developer.mozilla.org/ko/docs/Web/API/EventTarget/addEventListener
- https://kyounghwan01.github.io/blog/JS/JSbasic/addEventListener/
- https://poiemaweb.com/js-event
- https://nomadcoders.co/javascript-for-beginners-2
- https://developer.mozilla.org/en-US/docs/Web/Events
