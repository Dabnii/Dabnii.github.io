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

<details>
<summary>✈️ Flutter widget categories</summary>

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
</details>

### <p align="center">✈️ Flutter widget 두 가지 특징</p>

```dart
1. Stateless widget
2. Stateful widget
```

<details> 
<summary> Stateless Widget & Stateful Widget</summary>

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

</details>

# <p align="center">✈️ Flutter Naming Convention</p>

### File Naming Convention

- all 소문자
- snake_case

```dart
product_detail.dart
```

### Class Naming Convention

- 대문자로 시작
- Camel_Case

```dart
HomePage
```

### Fnc & Variables Naming Convention

- 소문자로 시작
- CamelCase

```dart
userName;
addTotal();
```

### Constant Naming Convention

- All caps

```dart
MAX_LENGTH;
MIN_LENGTH;
```

### Property Naming Convention

- 소문자로 시작
- CamelCase

```dart
name;
age;
```

### Widget Naming Convention

- 명사사용

```dart
Button
TextField
```

# <p align="center">✈️ Flutter Files</p>

## 🗂️ File Structure

```
flutter_app
    assets
    └── images
    android
    ios
    lib
    └── components
    │      └── login.dart
    └── main.dart
    test
    web
    ...
    pubspec.lock
    pubspec.yaml
```

### 🗽 `lib`

```dart
lib/components/
```

- app을 만들 떄 lib 폴더 안에서 작업

### 📍 pubspec.yaml

```dart
pubspec.yaml
```

- Flutter 프로젝트의 메타 데이터를 정의하고 관리하는 파일로써, Node의 package.json 과 비슷한 역할
  - 프로젝트의 버전, 프로젝트의 사용환경, dart 버전, 각종 dependency
  - 들여쓰기 룰이 존재 (주의)
    - `pub get` → `pubspec.yaml` 에 있는 내용을 다운로드, npm install와 비슷한 역할

### 💡 `main.dart`

```dart
lib/main.dart
```

- ✦ entry point, 프로그램이 시작되는 곳
- ✦ 가장 중요한 역할
- 필요한 라이브러리 또는 패키지를 가져옴
- 프로그램의 실행 흐름을 결정하는 코드 포함
- `test`
  - 제곧내, 테스트를 위함
- `android`,`ios`
  - 제곧내, 각 플랫폼에 맞게 앱플 배포하기 위함

### `runApp`

```dart
void main() => runApp(MyApp());
```

- 플러터 최상단에 위치
- 전달 되는 값이 위젯이어야 함
- `myApp`
  - 커스텀위젯

### material.dart

```dart
import 'package:flutter/material.dart';
```

- 구글이 제공하는 가이드라인
- flutter의 라이브러리
- SDK에 포함된 기본 위젯과 material 디자인 요소들 사용

---

## 🖌️ Draw SVG files using Flutter.

[flutter_svg | Flutter Package](https://pub.dev/packages/flutter_svg/install)

```dart
$ flutter pub add flutter_svg
```

```dart
dependencies:
  flutter_svg: ^2.0.6
```

```dart
$ flutter pub get
```

```dart
import 'package:flutter_svg/flutter_svg.dart';
```

---

### Text → ✨ New text

| old | ✨ new |
| --- | --- |
| headline1 | displayLarge |
| headline2 | displayMedium |
| headline3 | displaySmall |
| headline4 | headlineMedium |
| headline5 | headlineSmall |
| bodyText1 | bodyLarge |
| bodyText2 | bodyMedium |
| subtitle1 | titleMedium |
| subtitle2 | titleSmall |

[📎 TextTheme](https://api.flutter.dev/flutter/material/TextTheme-class.html)

---

### 📚 Ref

- [Flutter](https://docs.flutter.dev/ui/widgets-intro)
- [10 Best Flutter Widgets To Make App Development And Performance A Breeze](https://kodytechnolab.com/blog/top-10-flutter-widgets/)
