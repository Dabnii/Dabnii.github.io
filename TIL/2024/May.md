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

## <p align="center">📆5/29</p>

- 이것저것 공부를 하고 오니 벌써 29일이네.. 시간이 무척 빠르다

## 🏞️ River pod!

- Provider와 riverpod중 RunTime오류가 없는, Provider 보완버전인 riverpod을 채택했습니다.

```dart
//main.dart
// 우산을 씌어주듯 적용할 범위를 지정해준다.
// 멋지게 MyApp 전체를 적용했다...
// 다시 보니 범위를 좁혀도 될 듯
 runApp(
    ProviderScope(
        child: const MyApp(),
      ),
  );
```

```dart
// My_State_nofitier.dart
// 나는 여기에 모아 정의하기로 했다
import 'package:flutter_riverpod/flutter_riverpod.dart';
// riverpod을 임포트 한다
// 당연히 그 전에 package 설치도 해야한다

// StateNotifier을 지정해준다
class MyStateNotifier extends StateNotifier<Map<String, dynamic>> {
  MyStateNotifier()
      : super({
          'A': '',
          'B': '',
        }) {
    initialize();
    // 초기화를 진행한다
  }

  Future<void> initialize() async {
   // do Something...
   // 나는 여기서 api를 get 하고 state에 변수를 담았다
    state = {
      // state는 컨벤션
      ...state,
     // another do something
      };
  }

}

//그리고 프로바이더도 야무지게 설정해줍니다
final myStateNotifierProvider = StateNotifierProvider<MyStateNotifier, Map<String, dynamic>>((ref) {
  return myStateNotifier();
});
```

```dart
//parent.dart

// 구독 상태로 만듭니다
// 기존 statefulwidget에 consumer를 적용한 모습
class ParentScreen extends ConsumerStatefulWidget {
  const ParentScreen({super.key});

//...
Column(
children: [
  Consumer(builder: (context, ref, child) {
    // ref.watch 👀 지켜보도록 업데이트할 ui를 감싸준다
    final state = ref.watch(myStateNotifierProvider);
    return ChildWidget(
      key: state['A'] ?? 'NEW A',
      // A값이 변한다면, 전체 화면 깜빡임임 없이 갱신된다
    );
  }),
],
),
```

```dart
//child.dart
//Read는 rebuild를 요청하지 않는다
    await ref.read(myStateProvider.notifier).foo('new foo');
//회고하며 느낀 점은 changeNotifier로 child screen state를 정의하는게 맞다라는 생각..
```

- 곧 더 명확한 코드로 돌아오겠습니다. 🙇‍♀️

## <p align="center">📆5/30</p>

## 🏞️ River pod! again

### 🔨 refactoring

```dart
//before
  Column(
  children: [
    Consumer(builder: (context, ref, child) {
      // ref.watch 👀 지켜보도록 업데이트할 ui를 감싸준다
      final state = ref.watch(myStateNotifierProvider);
      return ChildWidget(
        key: state['A'] ?? 'NEW A',
        // A값이 변한다면, 전체 화면 깜빡임임 없이 갱신된다
      );
    }),
  ],
),
```

```dart
//After
    Consumer(
      builder: (context, ref, child)
      {
         return ChildWidget(
        //명명된 계산자로 넘겨 줄 때, 변수에 담지 않고 provide를 바로 주입가능
        key: ref.watch(myStateNotifierProvider)['A'],
      );
    },
  ),
```
