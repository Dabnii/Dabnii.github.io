# <p align="center">🎯 Dart Data types</p>

## <p align="center">📜 List</p>

1. List를 사용한 선언
2. var을 사용한 선언

```dart
void main(){
  List evenNums = [1,2,3];
  var oddNums = [1,3,5];
	List<int> myFavoriteNum = [7];
}
```

```dart
void main() {
  var giveMeFive = true;
  List item = [
    1,
    2,
    3,
    if (giveMeFive) 99,
		// giveMeFive가 true이면 99을 넣음
  ];
  print(item);
}
```

## <p align="center">`collection if` & `collection for`</p>

```
collection if :
  List를 만들 때, if를 통해 존재할 수 있는 안 할 수도 있는 요소를 만들 수 있다
```

## <p align="center">`collection for`</p>

- **리스트 내에 for 문을 사용하여 반복적으로 요소를 추가**
- UI를 만들 때 유용 🥳

```dart
void main() {
  var weekdays = [
    'Monday',
    'Tuesday',
    'Wednesday',
    'Thursday',
    'Friday',
  ];
  var weekends = [
    'Saturday',
    'Sunday',
    for(var week in weekdays) "$week"
		//...weekdays.map((week)=>"$week")
  ];
  print(weekends);
}

//[Saturday, Sunday, Monday, Tuesday, Wednesday, Thursday, Friday]
```

## <p align="center"> ✍️ String interpolation</p>

```
text에 변수를 추가할 때
```

```dart
void main() {
  var name = "lee";
  var age = 10;
  var greeting = "hello! this is $name! i'm ${age + 5} years old!";
  print(greeting);
	//hello! this is lee! i'm 15 years old!
}
```

- `$변수` : 이미 있는 값
- `${변수}` : 계산을 실행할 때의 문법

## <p align="center"> 🗺️ Maps</p>

- dart maps = Object in JS&TS, dictionary in Python
- dart object = <any> in TypeScript
  - dart에서 object는 기본적으로 `어떤 자료형이든 될 수 있다`

```dart
void main() {
  Map<int, bool> player = {
    1: true,
    2: false,
    3: false,
    4: true,
  };
}

void main() {
  var player = {
	//컴파일러가 key, value의 자료유형 유추
    1: true,
    2: false,
    3: false,
    4: true,
  };
}
```

- method와 property를 가짐

```dart
void main() {
  List<Map<String, Object>> players = [
    {
      'name': 'lee',
      'mood': 'nice',
    },
    {
      'name': 'kim',
      'mood': 'happy',
    },
  ];

  print(players);
}
```

### 🎒 Set

- Sequence(순서)가 있으며 모든 요소가 유니크 함
- `Dart Set === JS in Set`
  > A set in Dart is an unordered collection of `unique items`. Dart support for sets is provided by set literals and the `[Set](https://api.dart.dev/stable/dart-core/Set-class.html)`

```dart
1. var 사용
var halogens = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'};

2. 자료형 명시
Set halogens = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'};
```

---

출처:

- [https://dart.dev/language/collections#sets](https://dart.dev/language/collections#sets)
