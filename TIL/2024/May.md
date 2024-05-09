## <p align="center">📆5/1</p>

### Python 으로 'the' 찾기,

- 'the' 찾기, 'their,them'등은 제외

```python
sentence = input().split()
# 입력받은 문장을 split

count = 0
for i in sentence:
  if i.strip(',.') == 'the':
  # 각 단어에서 구두점(쉼표, 마침표)를 제거한 후에 그 단어가 "the"인지를 확인
    count += 1
print(count)
```

## <p align="center">📆5/9</p>

## fetch 개선

```
TL;DR:
  ChangeNotifier는 최선의 선택이 아니라 Provider나 다른 방법을 강구 해야함.
  아쉬우니 기록하는 글
```

### Issue

- focus를 다시 얻을 때 마다 전체 갱신되는 문제
- 잦은 리프레쉬로 인한 화면 블랭킹 현상

### 나의 생각

- 상태관리가 필요한 시점이라 판단
- ValueNotifier, Provider
- focusDetector 제거 후 `ValueNotifier` 를 적용 고려
- StreamBuilder와 Stream 사용고려

### 결론

- 다른 방법을 찾아야함
- DB까지 받아 갱신해야 함...
- 그리고 매번 main Route를 감싼다는게 비효율적같음

## 1. ValueNotifier 예시

[ChangeNotifier class - foundation library - Dart API](https://api.flutter.dev/flutter/foundation/ChangeNotifier-class.html)

---

```dart
//main.dart
final ValueNotifier notifierValue = ValueNotifier<int>(0);

GoRoute(
    path: '/firstpage',
    name: '첫페이지',
    builder: (context, state) {
      return ValueListenableBuilder<dynamic>(
        valueListenable: notifierValue,
        builder: (context, value, child) {
          return firstScreen(value: value);
        },
      );
    },
    routes: [
      GoRoute(
        path: 'child',
        name: 'child페이지',
        builder: (context, state) => child(notifier: notifierValue),
      ),
    ]),
```

```dart
//middle.dart
//기타 정의 코드

ValueListenableBuilder<dynamic>(
    valueListenable: widget.notifier,
    builder: (context, value, child) => Column(
      children: [
          Text('Received value: $value'),
      ],
    ),
  ),

```

```dart
//child.dart
//..기타 정의 코드
  ElevatedButton(
    onPressed: () => widget.notifier.value++,
    child: const Text('touch me'),
  ),

//print('HELLO THIS IS notifier ${widget.notifier.value}');
// HELLO THIS IS notifier 7
```
