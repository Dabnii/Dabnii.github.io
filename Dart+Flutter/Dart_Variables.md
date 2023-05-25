# <p align="center">🎯 Dart Variables</p>

## <p align="center">📢 Variables</p>

```dart
var name = 'Voyager I';
var year = 1977;
var antennaDiameter = 3.7;
var flybyObjects = ['Jupiter', 'Saturn', 'Uranus', 'Neptune'];
var image = {
  'tags': ['saturn'],
  'url': '//path/to/saturn.jpg'
};
```

- `String` 명시적 타입 지정
- `int`정수
- `double` 소수점 까지
- `num` 정수 + 더블 (소수점)
- `boolean` true/false
- `var` 처음 정한 값의 데이터 타입으로 적용 됨 (지양)

## <p align="center">💡타입지정

```dart
var
```

- 함수나 메소드 `내부에 지역변수를 선언` 할 때

```dart
String
```

- `class`에서 변수나 property를 선언 할 때

## <p align="center">💡 dynamic</p>

```dart
void main(){
  dynamic name;
  name = "lee";
}
```

- `var`, `dynamic`
- 변수를 선언할 때 dynamic을 쓰거나 값을 지정하지 않으면 dynamic 타입을 가진다
- 여러가지 타입을 가질 수 있는 변수에 쓰는 키워드
  - 해당 변수의 타입을 알 수 없을 때 (e.g. json)
  - 타입스크립트 any와 비슷하게 특수한 경우에만 사용 권장

## <p align="center"> 💡const & final</p>

## 💡const

```dart
void main(){
	const max_allowed_price= 120;
}
```

- 💎불변
- `컴파일 시점에 초기화`
  - compile-time constant 생성
  - **여행 가기 전에 결정**, 여행 과정에서 결정 불가능 → 결정 후 `변경불가`
  - 즉, const는 compile-time에 알고 있는 값이어야 함
  - e.g. 앱스토어에 **올리기 전에 알고 있는 값** = `const`
  - e.g. 앱스토어에 올려 **사용자가 입력해야 알 수 있는 값** = `final || var`
- `const in Js ≠= const in Dart` ⭐

## 🚩 final

```dart
final name = 'Bob'; // Without a type annotation
final String nickname = 'Bobby';
```

- 💎불변
- 프로그램이 실행 될 때(runtime) 초기화
  - 여행 가기 전에 정하지 않고, **여행 과정에서 결정 가능** → 결정 후 `변경불가`
- `const` in JS

## <p align="center">🔒Null safety</p>

```dart
bool isEmpty(String string) => string.length == 0;

main() {
  isEmpty(null);
}
```

- 어떤 변수, 혹은 데이터가 null이 될 수 있음을 명시
- null == 값의 부재
- null을 참조할 수 없도록 하는 것

```dart
void main(){
	String? dabin= 'dabin';
	dabin= null;
}
// dabin 은 null || string
```

- `?`
- dart의 변수는 기본적으로 nullable이 아님

## <p align="center">🛌Late</p>

```dart
void main(){
  late final String name;
  //do something, go to api
  name = '';
  print(name);
}
```

- dart 언어의 특징
- 초기 데이터 없이 먼저 변수를 생성하고 추후에 데이터를 넣을 때 사용
- Flutter로 데이터를 fetching 할 때 유용
  - e.g. late 변수를 만들고, API에 요청을 보낸 뒤 api에서 값을 보내주면 그 응답값을 late 변수에 넣어 사용

```dart
1. name 변수를 만든다
2. API에 요청을 보낸다
3. 응답받은 데이터를 late 변수에 주입
```

### <p align="center">🖨️ Print</p>

```dart
void main(){
  late final String name;
  name = '';
  print(name);
}
```

- 값을 프린트 할 때 사용한다.

📚 Ref

- [https://nomadcoders.co/dart-for-beginners/lectures/4094](https://nomadcoders.co/dart-for-beginners/lectures/4094)
- [https://velog.io/@cccodaisy/Dart-언어-기본](https://velog.io/@cccodaisy/Dart-%EC%96%B8%EC%96%B4-%EA%B8%B0%EB%B3%B8)
