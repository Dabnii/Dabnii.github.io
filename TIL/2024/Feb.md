## <p align="center">📆 2/2</p>

## AbsorbPointer Widget

- 터치를 제어 할 때 사용
- ignorePointer와의 차이점은, 모든 터치를 `흡수` 하는 것!
- 나는 텍스틀 쓰다가 터치를 잠구고 싶을 때 사용했다.
  - opacity widget을 쓰면 d`is`able 시각적 효과를 극대화 할 수 있다.

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

## <p align="center">📆 2/8</p>

#### 코드를 고쳐 보았읍니다..

```dart
// 💩 굳이 if를 남발한 이유는? 중복코드 🫨
  if (_hasYResponse(_isSelected)) {
    return _myDialog(context, _answerY);
  }

  if (_hasNResponse(_isSelected)) {
    return _myDialog(context, _answerN);
  }
```

```dart
// 🪄 한 결 나아진 코드!
// 중복을 없애고, 변수명을 개선했다.
 Future<void> _onSave() async {
    if (!_hasResponse(_isSelected)) {
      return myDialog(context);
    }
  }

  void _showMyDialog(BuildContext context) {
    String? _userRes;

    if (_isYInclude(_isSelected)) {
      _userRes = _answerY;
    }
    if (_isNInclude(_isSelected)) {
      _userRes = _answerN;
    }

    if (_userRes != null) {
      return _myDialog(context, _userRes);
    }
  }
```

## <p align="center">📆 2/13</p>

## syncfusion gauge 활용!

- 조금 더 멋진 게이지바로 수정했슴.

![gosoa!](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/75c31760-dc5a-41a6-92ec-f7182b12ba7f)

```dart
Center(
  child: SizedBox(
    height: 150,
    width: 150,
    child: Stack(
      children: [
        Padding(
          padding: const EdgeInsets.only(bottom: 8.0),
          child: Align(alignment: Alignment.bottomCenter, child: Text('10,000', style: TextStyle(fontSize: 20))),
        ),
        SfRadialGauge(axes: <RadialAxis>[
          RadialAxis(
            pointers: <GaugePointer>[
              GaugeRangePointer(value: 6000) //value!
            ],
            annotations: <GaugeAnnotation>[
              GaugeAnnotation(
                  positionFactor: 0.1,
                  angle: 90,
                  widget: Text(
                    '6,000',
                    style: TextStyle(fontSize: 20),
                  ))
            ],
            minimum: 0,
            maximum: 100,
            showLabels: false,
            showTicks: false,
            axisLineStyle: AxisLineStyle(
              thickness: 0.2,
              cornerStyle: CornerStyle.bothCurve,
              color: Color.fromARGB(30, 0, 169, 181),
              thicknessUnit: GaugeSizeUnit.factor,
            ),
          ),
        ])
      ],
    ),
  ),
),

```

## <p align="center">📆 2/16</p>

## 라우팅을 다뤄보자

### 원했던 것:

1. 원하는 조건이 성립 하면
2. 다이얼로그가 등장
3. 버튼을 눌러 원하는 곳으로 라우팅

### 실제로 작동한 것:

1. 라우팅이 되지 않고 `context.pop()` 만 정상 작동

### 내가 추측 한 것:

- `BuildContext`를 적절히 받지 못하나?
- 그렇다면 `context.pop()`등 다른 함수를 작성해서 처리해야할까?

### 그리고 코드!

```dart
// 수정 코드
// 비동기처리
Future<void> _displayDialog(BuildContext context) async {
    String? result;

    if (_isYInclude(_isSelected)) {
//...

    if (_isNInclude(_isSelected)) {
      result = _answerN;
    }
    if (result != null) {
      bool isDone = await showResultDialog(context, result); // 내가 만든 다이얼로그
      if (!mounted) return;
// 여기서 비동기 처리를 진행 해 주며
// 라우팅 하는 로직으로 접근
      if (isDone) {
        while (context.canPop()) {
          context.pop();
        }
        context.push('/');
      }
      return;
    }
  }
```

### 결론

- dialog의 onTap context.go도 제대로 작동했다.
- 하지만 모달창이 닫히지 않아서 라우팅 되는 것으로 안보였던것.
- 고로 위의 로직을 추가하여 닫는다.

---

### 세로 화면으로 고정하자

```dart
/// 세로 화면으로 조정
  void _setPortrait() {
    if (MediaQuery.of(context).orientation == Orientation.landscape) {
      SystemChrome.setPreferredOrientations([
        DeviceOrientation.portraitUp,
        DeviceOrientation.portraitDown,
      ]);
    }
  }

  /// 원래 화면 방향으로 복원
  void _resetScreenType() {
    if (MediaQuery.of(context).orientation == Orientation.portrait) {
      SystemChrome.setPreferredOrientations([
        DeviceOrientation.landscapeLeft,
        DeviceOrientation.landscapeRight,
        DeviceOrientation.portraitUp,
        DeviceOrientation.portraitDown,
      ]);
    }
  }
```
