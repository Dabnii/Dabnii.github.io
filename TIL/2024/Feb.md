## <p align="center">📆 2/2</p>

## AbsorbPointer Widget

- 터치를 제어 할 때 사용
- ignorePointer와의 차이점은, 모든 터치를 `흡수` 하는 것!
- 나는 텍스틀 쓰다가 터치를 잠구고 싶을 때 사용했다.
  - opacity widget을 쓰면 `disable` 시각적 효과를 극대화 할 수 있다.

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

## <p align="center">📆 2/20</p>

## UI를 Bottom-up으로 위로 쌓기

![ddd](https://github.com/Dabnii/Dabnii.github.io/assets/134585116/055cbaad-a9d4-47d3-a9d0-967639b933fd)

- 그렇습니다. 아직 expandListTile 작업을 하고 있습니다..
- 오늘의 수정사항은: 아래에서 위로 쌓기!
- `SlideAnimation`사용

```dart
/// 커스텀 슬라이드 애니메이션
class _SlideAnimationState extends State<_SlideAnimation> with SingleTickerProviderStateMixin {
  //ticker 공급자 ^ 애니메이션에 사용

  late AnimationController _controller;
  late Animation<Offset> _offsetAnimation;

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(duration: const Duration(milliseconds: 900), vsync: this);

    //첫 타일의 애니메이션 무효화
    if (widget.index == 0) {
      _offsetAnimation = Tween<Offset>(begin: Offset.zero, end: Offset.zero).animate(CurvedAnimation(parent: _controller, curve: Curves.easeInOut));
    } else {
      _offsetAnimation = Tween<Offset>(begin: const Offset(1.2, 0.0), end: Offset.zero).animate(CurvedAnimation(parent: _controller, curve: Curves.easeInOut));
      _controller.forward();
    }
  }

  @override
  Widget build(BuildContext context) {
    return SlideTransition(
      position: _offsetAnimation,
      child: _MyCustomWidget(
      //...
        myCallback: (bool value) {
          setState(() {
            widget.myCallback(value);
            if (widget.index != 0) {
              _controller.reset(); //초기화
              _controller.forward(); //실행
            }
          });
        },
      ),
    );
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }
  // 컨트롤러 해제
}
```

```dart
// 💡
// 가장 겉을 감싸는 widget
ListView.builder(
    reverse: true,
    //역순으로 쌓기 위함
    physics: const NeverScrollableScrollPhysics(),
    shrinkWrap: true,
    itemCount: _myList.length,
    itemBuilder: (BuildContext context, int index) {
      return _isVisible[index]
          ? _SlideAnimation(
              index: index,
              //index를 넘겨 내가 원하는 로직을 구현한다
              myCallback: (bool value) {
                setState(() {
                   //.. 내 함수
                });
              },
            )
          : const SizedBox.shrink();
          // 가장 작은 sizedBox를 생성하여 완성
    },
  ),
```

### 위젯으로 구분한 이유

- 아래와 같이 구현 하면 오류가 발생한다.

```shell
🚨 error
The following assertion was thrown during paint():
RenderBox was not laid out: RenderTransform#12f09 relayoutBoundary=up4
'package:flutter/src/rendering/box.dart':
Failed assertion: line 1972 pos 12: 'hasSize'
```

```shell
🚨 error
Duplicate GlobalKey detected in widget tree.
```

- ListView.builder의 Stack은 최대 공간을 요구, AnimatedPositioned는 공간 제약X 하여 충돌
- 동일한 GlobalKey가 위제트리에서 2회 이상 사용 되는 문제

```dart
//🚨
ListView.builder(
  itemCount: 10,
  itemBuilder: (context, index) {
    return Stack(
      children: [
        AnimatedPositioned(
          duration: Duration(seconds: 1),
          top: index * 10.0,
//...
```

- ListView.builder의 lazyLoad유지
- 우 > 좌로 들어오는 애니메이션 구현을 위하여 각 항목을 위젯으로 분리 하여 구현! 몹시 잘 된다.
- `AnimatedPositioned`는 stack의 직접(?) 자손이 되어야하는데, 그러면 렌더링 자체가 되지 않았다.
- 다양한 방법이 있어 고민하고 성공했다.

## <p align="center">📆 2/21</p>

- `initState`와 `_initializeAnimation를` 분리 했다.
- `_controller`는 반드시 생성해주고, dispose도 할 것!

```dart
void initState() {
    super.initState();
    _controller = AnimationController(duration: const Duration(milliseconds: 800), vsync: this);
    _initializeAnimation();
  }

  ///첫 타일의 애니메이션 무효화
  Animation<Offset> _initializeAnimation() {
    if (widget.index == 0) {
      _offsetAnimation = Tween<Offset>(begin: Offset.zero, end: Offset.zero).animate(CurvedAnimation(parent: _controller, curve: Curves.easeInOut));
    } else {
      _offsetAnimation = Tween<Offset>(begin: const Offset(1.0, 0.0), end: Offset.zero).animate(CurvedAnimation(parent: _controller, curve: Curves.easeInOut));
      _controller.forward();
    }
    return _offsetAnimation;
  }
```

## <p align="center">📆 2/24</p>

## GoLang

### 선언

- `const`
- `var`
  ```Go
  surname := "kim"
  ```

```go
package main

import (
	"fmt"
	"strings"
)

func multiply(a, b int) int {
	return a * b
}

// multy return
func lenAndUpper(name string) (length int, uppercase string) {
	defer fmt.Println("done!")
	length = len(name)
	uppercase = strings.ToUpper(name)
	return
}

func main() {
	totalLength, up := lenAndUpper("LEE")
  // ------
  // totalLength, upperName := lenAndUpper("LEE")
  // lenAndUpper 함수의 반환값을 totalLength와 upperName 변수에 각각 할당
  // ---- 즉 아래와 같다
  // var totalLength int
  // var upperName string
  // totalLength, upperName = lenAndUpper("LEE")
  // ------
	fmt.Println(totalLength, up)
}
```

## <p align="center">📆 2/26</p>

### 🔨 코드 재개발

- 다시 돌아온, expandTile 코드 시간
- 구조와 변수명을 점검하는 시간.

#### 👀 Key point

1. 범용 코드 판별하기

- 현재 범용으로 쓸 수 있도록 코드를 관리하고 있다. 하지만 단 한 곳에서 해당 함수를 사용하고 있다면 과감히 작업하는 파일에 이관한다.

2. `함수명` 💡💡💡

- 함수명이 중요한 것을 알아서 신중하게 작성했지만, 역시 실무의 코드는 더 간결해야했다.
- prefix: `is~` 는 bool 일 때 사용한다.
- List를 다룬다면 `_somethingList`
  - 또는 `displayNextList` or `displayList`도 괜찮을 것 같다.

3. 🔍 구조를 확인해 본다.

   - 생각보다 사용하지 않는 함수들이 많았다. 확실히 flutter 자체의 클래스를 복사 붙여넣기 했던 expansionTile에서 대거 확인 되었다.
   - 잡초를 뽑습니다 🌱

4. context 걷어내기
   - stateless widget에서 context는 없어도 되니 생략 가능!

### 중복코드를 걷어내다

```dart
  /// answer 유무에 맞도록 display
  void _isAnswerExist(int index) {
    // 🫨 나의 멋-진 함수명
    _questions[index]['answer'] != ''
        ? setState(() {
            _expandedList[index] = true;
            _answerList[index] = 'Y';
          })
        : setState(() {
            _answerList[index] = 'Y';
          });
  }

  void _onYSelect(int index) {
    _onVisibleTile(index);
    _isAnswerExist(index);
  }

  void _onNSelect(int index) {
    _onVisibleTile(index);
    setState(() {
      _expandedList[index] = false;
      _answerList[index] = 'N';
    });
  }
```

### ^ 위 두 함수를 하나로 합치기

- 늘 고치고 싶던 코드였는데 드디어 고칠 수 있어 기쁘다.

```dart
 void _onAnswered(int index, String value) {
    _answerList[index] = value; // 답변 기록
    // 다음 질문 display
    if (_answerList[index] == '') return; // 답변 기록 안되면 리턴
    setState(() {
      if (index < _displayList.length - 1) {
        _displayList[index + 1] = true; // 다음 index를 true로 변경하여 display
      }
    });
  }
```

### 또 다른 구조 고치기!

```dart
ListView.builder(
    itemCount: _questions.length,
    itemBuilder: (BuildContext context, int index) {
      return _displayList[index]
      // 💡 여기 고친 함수명!
          ? _SlideAnimation(
              isAnimated: index != 0,
              // 아래 코드에서 계속 ...
              child: _CustomExpansionPanel(
                index: index,
                onAnswered: _onAnswered,
              ),
            )
)//...
// 바로 아래와 같이 관리하고 있습니다
class _SlideAnimation extends StatefulWidget {
  const _SlideAnimation({required this.child, this.isAnimated = true});
  final bool isAnimated;
  final Widget child;
  //심지어 반복되던 구조도 child로 한번에 정리
  //...
  @override
  // 빌드를 살펴보면 이러합니다
  Widget build(BuildContext context) {
    return SlideTransition(
      position: _offsetAnimation,
      child: widget.child,
    );
  }
}
//...
```

## 궁극의 버튼 기능 구현하기

```dart
  /// 사용자 응답 중 '' 포함 확인
  bool _onValidate() {
    return _answerList.contains('');
  }
  Button(
  disabled: _onValidate(),
  )
  //..
```

```dart
// 💩
Button(
  text: '확인 했어요',
  onPressed: _onSave,
  disabled: (_isEmptyList(_answerList)),
  // 사실 이 코드가 말이 안되어서 시작한 리팩토링이다... 민망
  )
//
```

- 하나를 고치기 위해 전체를 손 봤는데 그 과정에서 가독성 좋은 구조를 고민하고 설계하는 방법을 습득했다.
- 예컨대, 복잡한 class를 반복하여 작성 하여 자연스레 나는 불 필요한 코드를 쉽게 인지 하지 못했다. 변수명도 혼란했고 비슷한 기능을 가진 함수들이 많았다.
- 다음엔 시간을 더 들여서 코드를 고쳐 보도록!
- 👟 기존에 작성된 변수명들을 정리 해야겠다.
