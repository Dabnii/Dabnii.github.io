## <p align="center">📆 2/2</p>

## AbsorbPointer Widget

- 터치를 제어 할 때 사용
- ignorePointer와의 차이점은, 모든 터치를 `흡수` 하는 것!
- 나는 텍스틀 쓰다가 터치를 잠구고 싶을 때 사용했다.
  - opacity widget을 쓰면 disable 시각적 효과를 극대화 할 수 있다.

![mov](https://github.com/Dabnii/Dabnii.github.io/assets/134585116/a3781490-7097-4da8-9125-a9e4ec79f37b)

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Demo'),
        ),
        body: Center(
          child: MyWidget(),
        ),
      ),
    );
  }
}

class MyWidget extends StatefulWidget {
  @override
  _MyWidgetState createState() => _MyWidgetState();
}

class _MyWidgetState extends State<MyWidget> {
  bool _isLocked = false;

  void _toggleLock() {
    setState(() {
      _isLocked = !_isLocked;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        IconButton(
          icon: _isLocked ? Icon(Icons.lock) : Icon(Icons.lock_open_rounded),
          onPressed: _toggleLock,
        ),
        AbsorbPointer(
          absorbing: _isLocked,
          child: TextField(
            decoration: InputDecoration(
              border: OutlineInputBorder(),
              labelText: '메모장',
            ),
          ),
        ),
      ],
    );
  }
}

```

## <p align="center">📆 2/6</p>

#### 순차적으로 하나씩 펼쳐진다! +`opacity`를 곁들임.

![555](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/bc43426e-1b10-4a2d-966e-929d98059a8c)

#### 이미 펼쳐진 타일, 그리고 닫을 때는 해당사항이 없다

![001](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/1c0df8d7-340e-4464-ae38-c8d1e9914c73)

- 간략한 로직:
  - 데이터의 길이 만큼, `List<bool>`를 만든다. 초기값은 `false`
  - `data[0]` 즉, 첫 번째 인덱스는 언제나 true가 되도록 초기화 한다.
  - 인덱스가 list길이보다 짧다면 `index+1` = 즉 다음 tile을 `true`로 바꾼다.
  ```dart
    void _onVisibleTile(int index) {
      setState(() {
        if (index < _isVisible.length - 1) {
          _isVisible[index + 1] = true;
        }
      });
    }
  ```

```dart
return AnimatedOpacity(
    opacity: _isVisible[index] ? 1.0 : 0.0,
    duration: const Duration(seconds: 1),
    child: Stack(
      children: [
//...
```
