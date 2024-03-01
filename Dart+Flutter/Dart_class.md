## <p align="center">🏷️ Named parameter

```dart
void main() {
  void greet({required String name, int age = 20}) {
    //int age = 20;  위에서 바로 선언&초기화 가능, 주석된 코드와 같다.
    print('Hello $name, you are $age years old.');
  }

  greet(name: 'KIM', age: 30);
  greet(name: 'LEE');
}

// Name: KIM, Age: 30
// Name: LEE, Age: 20
```

## <p align="center">📛 typedef

- Alias를 붙이는 것!

```dart
typedef Calculate = int Function(int a, int b);

void printCalculation(Calculate calcFunc, int a, int b) {
  print('결과: ${calcFunc(a, b)}');
}

int add(int a, int b) {
  return a + b;
}

int subtract(int a, int b) {
  return a - b;
}

void main() {
  printCalculation(add, 10, 5);  // 출력: 결과: 15
  printCalculation(subtract, 10, 5);  // 출력: 결과: 5
}

```

## <p align="center">👉 CaseCade notation

- Cascade 문법 : 한 객체의 여러 속성을 연속적으로 설정하는 코드를 더 간결하게 작성 가능

```dart
final myButton = RaisedButton(
  onPressed: () {},
  child: const Text('Hello, World!'),
)..color = Colors.blue
..padding = const EdgeInsets.all(10.0);
```

```dart
final myList = List<int>.filled(0, 5)
  ..add(10)
  ..add(20)
  ..removeAt(0)
  ..sort();
```

## <p align="center">👷‍♂️ Constructor

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});
// Constructor!
// {} 로 감싸져 있으므로, 명명된 매개변수 표현 방법.

  @override
  Widget build(BuildContext context) {
// build 메소드, BuildContext를 매개 변수로 받고, return widget.
}
}
```

## <p align="center">👨‍👩‍👧 extends

```dart
class MyApp extends StatelessWidget {
//StatelessWidget를 extend함
// 부모 StatelessWidget, 인스턴스 MyApp

  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
  }
}
```

```dart
class MyApp extends StatefulWidget {
// StatefulWidget 상속!
//
  const MyApp({Key? key}) : super(key: key);
// Key를 super Key에 전달
// super로 전달
  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
    );
  }
}

```

## <p align="center">🎨 Mixin

#### mixin ≠ extend

| mixin                                                                            | extend                                  |
| -------------------------------------------------------------------------------- | --------------------------------------- |
| `with`                                                                           | `extend`                                |
| 단순히 복붙 하듯 메소드를 본인의 것처럼 사용할 수 있는 것                        | super을 사용하여 부모에 접근            |
| 부모 클래스가 부모, extend를 설정한 class는 자식이며 부모 클래스의 인스턴스가 됨 |
| `class MyApp with NewApp{}`                                                      | `class MyApp extends StatefulWidget {}` |

```dart
mixin MyMixin {
  void myMethod() {
    print('Mixin method');
  }
}

class _MyApp extends State<_MyApp> with MyMixin {
  @override
  Widget build(BuildContext context) {
    myMethod(); // 믹스인으로부터의 메소드 호출
    return Container();
  }
}
```

---

Ref

- [📎  nomadCode!](https://nomadcoders.co/dart-for-beginners)
