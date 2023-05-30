# <p align="center">✈️ Flutter 101</p>

### <p align="center">✈️ Flutter 특징</p>

1. Cross-platform development
   - 하나의 코드베이스로 iOS,Android,Web,desktop 등
2. Fast development and hot reload
   - 개발 내용을 즉시 반영한 핫리로드
3. UI 최적화
   - 다양하고 풍부한 UI
4. Dart programming language
   - Just in Time
   - Ahead Of Time

### <p align="center">✈️ Flutter Hello world!</p>

```dart
void main() {
  runApp(
    const Center(
      child: Text(
        'Hello, world!',
        textDirection: TextDirection.ltr,
      ),
    ),
  );
}
```

### ✈️ Flutter Basic widgets

- `Text`
- `Row`, `Column`
- `Stack`
  - absolute positioning (web)
- `Container`

### ✈️ Flutter widget categories

- Accessibility;
- Assets, Images, and Icons;
- Async;
- Animation and Motion;
- Basics;
- Input;
- Interaction Models;
- Layout;
- Cupertino widget; (iOS)
- Material Components; (android)
- Painting and Effects;
- Scrolling;
- Styling;
- Text;

### <p align="center">✈️ Flutter widget 두 가지 특징</p>

```dart
1. Stateless widget
2. Stateful widget
```

### Stateless Widget

1. Stateless
1. 한 번 그려진 후에는 변경불가
1. 상태가 변하지 않는 정적 요소
   - e.g. 텍스트 레이블, 버튼, 아이콘 등이 Stateless 위젯
1. Stateless 위젯은 `StatelessWidget` 클래스를 상속받아 구현

### Stateful Widget:

1. Stateful 위젯은 내부 상태 가짐
1. 상태가 변경될 때마다 UI가 다시 그려짐
1. 사용자 입력, 데이터 변경 등과 같이 동적인 상황에 맞게 UI를 업데이트해야 할 때 주로 사용
   - e.g. 사용자가 입력한 내용을 반영하는 폼 필드나 동적으로 데이터를 로딩하고 표시하는 리스트
1. Stateful 위젯은 `StatefulWidget` 클래스를 상속받아 구현

> Stateful 위젯은 `createState()` 메서드를 사용하여 State 객체를 생성하고, 이 객체는 해당 위젯의 상태를 유지합니다. 상태가 변경될 때마다 build() 메서드가 호출되어 UI를 다시 그립니다. State 객체는 변경 가능한 상태를 저장하고, 상태가 변경될 때마다 UI를 업데이트하는 데 사용됩니다.

### setState method

- 상태변화를 알리는 코드

```dart
@protected
    void setState(
        VoidCallback fn
)
```

```dart
setState(() { _myState = newValue; });

```

---

### 📚 Ref

- [Flutter](https://docs.flutter.dev/ui/widgets-intro)
- [10 Best Flutter Widgets To Make App Development And Performance A Breeze](https://kodytechnolab.com/blog/top-10-flutter-widgets/)
