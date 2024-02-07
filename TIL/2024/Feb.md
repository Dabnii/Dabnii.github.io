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

## <p align="center">📆 2/7</p>

### 드디어 class 커스텀!

- 디자인이 수정되었는데, row 구성에서 column으로 바뀌었다.
- 적용하려니 한계가 있어 기존 expansionTile 복제 후 사용 시작

```dart
import 'package:flutter/material.dart'; // 위 임포트로 대체 한다!

/// expand icon 삭제를 위한 기존 expansionTile 복제
const double _kPanelHeaderCollapsedHeight = kMinInteractiveDimension;
const EdgeInsets _kPanelHeaderExpandedDefaultPadding = EdgeInsets.symmetric(
  vertical: 64.0 - _kPanelHeaderCollapsedHeight,
);
const EdgeInsets _kExpandIconPadding = EdgeInsets.all(12.0);

class _SaltedKey<S, V> extends LocalKey {
  //... 설정들
}

class MyExpansionPanel {
  // 클래스명을 바꾼다
  MyExpansionPanel({
    required this.headerBuilder,
    required this.body,
    this.isExpanded = false,
    this.canTapOnHeader = false,
    this.backgroundColor,
  });

  final ExpansionPanelHeaderBuilder headerBuilder;
  final Widget body;
  final bool isExpanded;
  final bool canTapOnHeader;
  final Color? backgroundColor;
}
 //... 설정들

class _MyExpansionPanelListState extends State<MyExpansionPanelList> {
  ExpansionPanelRadio? _currentOpenPanel;

  @override
  void initState() {
   //... 설정들
  }

  @override
  void didUpdateWidget(MyExpansionPanelList oldWidget) {
      //... 설정들
  }
      //... 설정들
      Widget expandIconContainer = Container(
        margin: const EdgeInsets.all(0),
        width: 0, // 여기가 진짜 헬이었음 여기 고쳐서 해결함.
        // 기존 코드는 margin left 16에, 사이즈도 가지고 있었다.
        child: ExpandIcon(
          color: Colors.transparent,
          isExpanded: _isChildExpanded(index),
          padding: _kExpandIconPadding,
          onPressed: !child.canTapOnHeader ? (bool isExpanded) => _handlePressed(isExpanded, index) : null,
        ),
      );
          //...
```

- 나의 첫 class 커스텀마이징
- 과연 나의 expandedTile과의 인연은 언제까지 일까..
- 사실 근본(?) 문제를 찾아 해결하니, 이전에 ignorePoint... Stack등 불필요한 코드들을 많이 제거할 수 있었다. 👏
