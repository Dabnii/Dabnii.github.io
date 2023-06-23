# 🧑‍🍳 Flutter Async

- 비동기
- `Future`, `Stream`, `await`, `async`

### 🛸 Future!

- `미래`에 어느 시점에 완료될 때 계산 값을 반환
- 제네릭을 사용하여 미래에 발생할 데이터 타입 지정
    - 🤫 `Future<void>` → 반환값이 없을 때

### test code

```dart
import 'dart:async';

Future<int> sum() {
  return Future<int>(() {
    var sum = 0;
    Stopwatch stopwatch = Stopwatch();
    stopwatch.start();
    for (int i = 0; i < 5000000; i++) {
      sum += i;
    }
    stopwatch.stop();
    print("${stopwatch.elapsed}, result:$sum");
    return sum;
  });
}

void onPress() {
  print('onPress top...');
  sum();
  print('onPress bottom...');
}

void main() {
  onPress();
}
```

```dart
onPress top...
onPress bottom...
0:00:00.004400, result:12499997500000
```

### 🌇 FutureBuilder

- 데이터(결과)가 나올때 까지 대기 후 화면에 출력
- 화면을 가지지 않는 위젯

### FutureBuilder 생성자

```dart
const FutureBuilder<T>(
	{ Key?key, 
		 Future<T> future, 
		 T? initialData, 
	   required AsyncWidgetNuilder<T> builder}
)
```

### `AsyncWidgetBuilder` 정의

```dart
AsyncWidgetBuilder<T> Widget Function(
  BuildContext context,
  AsyncSnapshot<T> snapshot
)
```

1. **`AsyncWidgetBuilder<T>`** is a type alias representing a function that takes a **`BuildContext`** and an **`AsyncSnapshot<T>`** as parameters and returns a **`Widget`**. It's used as the type for the builder function in asynchronous Flutter widgets like **`FutureBuilder`**, **`StreamBuilder`**, etc.
2. **`BuildContext context`** represents the build context for the current build operation. It provides access to the widget tree and various utility methods.
3. **`AsyncSnapshot<T>`** represents the state of an asynchronous computation, such as a **`Future`** or a **`Stream`**. It contains the data received, the error (if any), and the connection state. The generic type **`T`** specifies the type of data being handled.

### 🖨️print `future data`

```dart
body: Center(
  child: FutureBuilder(
    future: calFun(),
    builder: (context, snapshot) {
      if (snapshot.hasData) {
        return Text('${snapshot.data}');
      }
      return CircularProgressIndicator();
    },
  ),
),
```

1. The child of the **`Center`** widget is a **`FutureBuilder`** widget. The **`FutureBuilder`** widget takes a **`future`** property, which should be a **`Future`** representing the asynchronous computation.
2. In the **`builder`** property of the **`FutureBuilder`**, an anonymous function is defined that takes the **`context`** and **`snapshot`** as parameters.
3. Inside the builder function, it checks if the **`snapshot`** has data using **`snapshot.hasData`**. If it does, it returns a **`Text`** widget displaying the data using **`snapshot.data`**.
4. If the **`snapshot`** doesn't have data yet (i.e., still loading), it returns a **`CircularProgressIndicator`** widget to show a loading indicator.

---

ref:

[📎Async_Await](https://dart.dev/codelabs/async-await)

[📎Future builder](https://api.flutter.dev/flutter/widgets/FutureBuilder-class.html)

### 실전 future code

```dart
//실전 코드
class _DetailScreenState extends State<DetailScreen> {
  List<String> posters = [
    "assets/images/big_buck_bunny_poster.jpg",
    "assets/images/les_miserables_poster.jpg",
    "assets/images/minari_poster.jpg",
    "assets/images/the_book_of_fish_poster.jpg",
  ];

  late VideoPlayerController _videoPlayerController;
  ChewieController? _chewieController;

  Future<void> initializePlayer() async {
    _videoPlayerController = VideoPlayerController.network(
        'https://flutter.github.io/assets-for-api-docs/assets/videos/butterfly.mp4');
    await Future.wait([_videoPlayerController.initialize()]);
    _chewieController = ChewieController(
      videoPlayerController: _videoPlayerController,
      autoPlay: true,
    );
    setState(() {});
  }

  @override
  void iniState() {
    super.initState();
    initializePlayer();
  }

  @override
  void dispose() {
    _videoPlayerController.dispose();
    _chewieController?.dispose();
    super.dispose();
  }
```

- [📎 Future](https://api.dart.dev/stable/3.0.2/dart-async/Future-class.html)
1. 이 함수 initializePlayer는 비디오 플레이어를 비동기적으로 초기화하기 위해 정의됩니다. 제공된 네트워크 URL에서 비디오를 재생하는 VideoPlayerController의 새 인스턴스로 _videoPlayerController를 설정합니다.
2. initialize() 메서드는 _videoPlayerController에서 호출되어 초기화되고 await는 진행하기 전에 초기화가 완료될 때까지 기다리는 데 사용됩니다.
3. 그 후 ChewieController의 새 인스턴스가 생성되고 _chewieController에 할당됩니다.
4. ChewieController의 videoPlayerController 매개변수는 _videoPlayerController로 설정되고 autoPlay는 true로 설정됩니다. 마지막으로 위젯을 다시 빌드하기 위해 setState()가 호출됩니다.