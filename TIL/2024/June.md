## <p align="center">📆6/3</p>

### 오늘도 RiverPod! Refactoring time

```dart
//before
class MyStateProvider extends StateNotifier<Map<String, String>> {
  MyStateProvider() : super(MyStateProvider(
    // some thing initialize...
  )) {
    initialize();
  }

  Future<void> initialize() async {
     // api...
      state = MyClass.fromJson(result);
  }
}

// parent.dart
ref.watch(MyStateProvider.notifier).initialize();
//부모에서 이렇게 다시 한 번 호출 하고 있었다
```

```dart
//after
class MyStateProvider extends StateNotifier<MyClass> {
  MyStateProvider() : super(MyStateProvider('', '', '')) {
    _initialize();
    //private로 바꿔 내부에서만 사용하게 했다
    //그리고 초기화를 바로 진행하도록 했다.
  }

  Future<void> _initialize() async {
     // api...
      state = MyClass.fromJson(result);
  }
}

//당연히 클래스도 선언을 해야한다!
class MyClass ...
//..data
```
