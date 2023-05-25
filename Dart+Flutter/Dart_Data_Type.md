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

- `collection if` 는 List를 만들 때, if를 통해 존재할 수 있는 안 할수도 있는 요소를 만들 수 있다

🏗...