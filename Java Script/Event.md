# <p align="center"> 🎉 Event Javascript

EventTarget.addEventListener()
EventTarget 인터페이스의 addEventListener() 메서드는 지정한 유형의 이벤트를 대상이 수신할 때마다 호출할 함수를 설정합니다.

일반적인 대상은 Element, Document, Window지만, XMLHttpRequest와 같이 이벤트를 지원하는 모든 객체가 대상이 될 수 있습니다.

addEventListener()는 document의 특정요소(Id,class,tag 등등..) event(ex - click하면 함수를 실행하라, 마우스를 올리면 함수를 실행하라 등등.. )를 등록할 때 사용합니다.

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
EventTarget() 생성자는 새로운 EventTarget 객체 인스턴스를 생성합니다.

```
new EventTarget();

```

mouse 이동 이벤트

`mousemove`

1. ClientX, ClientY
   클라이언트 영역(현재 보여지는 브라우저 화면 기준)을 기준으로 가로, 세로 좌표를 제공

clientX - 스크롤은 무시하고 해당페이지 상단을 0으로 측정하여 클라이언트 영역에서 X위치를 반환

clientY - 스크롤은 무시하고 해당페이지 상단을 0으로 측정하여 클라이언트 영역에서 Y위치를 반환

2. OffsetX, OffsetY
   이벤트 대상을 기준의 좌표 ex) 화면 중앙의 박스 요소에서 클릭한 위치를 찾으면 박스위 왼쪽 모서리 좌표가 0으로 측정됨

offsetX - 이벤트 대상을 기준으로 상대적 마우스 x좌표 반환

offsetY - 이벤트 대상을 기준으로 상대적 마우스 y좌표 반환

3. pageX, pageY
   스크롤을 포함한 전체 문서를 기준으로 x,y 좌표를 반환

pageX - 브라우저 전체 페이지에서 x좌표 반환

pageY - 브라우저 전체 페이지에서 y좌표 반환

4. screenX, screenY
   모니터 화면을 기준으로 좌표제공

screenX - 전체 모니터 스크린에서 x좌표 반환

screenY - 전체 모니터 스크린에서 y좌표 반환

https://hmk1022.tistory.com/entry/clientX-offsetX-pageX-screenX-%EC%B0%A8%EC%9D%B4%EC%A0%90

https://developer.mozilla.org/ko/docs/Web/API/EventTarget/addEventListener
https://kyounghwan01.github.io/blog/JS/JSbasic/addEventListener/

https://poiemaweb.com/js-event
