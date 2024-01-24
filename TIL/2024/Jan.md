## <p align="center">📆 1/5</p>

### 🎆 Splash 적용하기

[Android Asset Studio](https://romannurik.github.io/AndroidAssetStudio)

- 반응형(?) 으로 만들었다.
  - 배경색, 로고 투명 png가 얹어지는 형태임
- 위의 링크에서 파일을 생성
- 복붙 (파일명은 바꾸지 않도록..)
  ![Untitled (1)](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/48b4476b-9b9e-4b0b-bf4e-ddcf7396d963)

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Modify this file to customize your launch splash screen -->
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="?android:colorBackground" />

    <!-- You can insert your own image assets here -->
    <!-- <item>
        <bitmap
            android:gravity="center" :여기서 안됨....
            android:src="@mipmap/launch_image" />
    </item> -->
</layer-list>
```

### splash 배경색 바꾸기

`values > colors.xml`

```xml
<?xml version="1.0" encoding="utf-8" ?>
<resources>
    <color name="launch_color">#ffff00</color>
</resources>
<!-- colors.xml -->
```

## <p align="center">📆 1/15</p>

### <p align="center"> 🛝 slider thumbnail 바꾸기<p>

- 시작하기에 앞서, 커스텀을 위하여 Custom class를 생성하여 슬라이더의 thumb을 사용자화 하기로 함
- N차 오류 발생. 하나씩 뜯어보겠습니다. 🎉

### 1️⃣ Paint Issue

- 당연히 작동해야하는 코드가 작동하지 않습니다.
- 패키지 버전의 문제로 착각하고, 업데이트를 진행했지만 원인은 그대로!
  - 당연함, 그 문제가 아니었음.

```dart
// 🚨 error
224:8: Error: The method '_CustomThumbShape.paint' doesn't have the named parameter 'currentValue' of overridden method 'SfThumbShape.paint'.
  void paint(
       ^
```

#### 그리고 이론상 완벽했던, 나의 코드 👇

```dart
// 🫨 대혼란
class _CustomThumbShape extends SfThumbShape {
  final ImageProvider imageProvider;

  _CustomThumbShape({required this.imageProvider});

  @override
  void paint(
    PaintingContext context,
    Offset center, {
    required RenderBox parentBox,
    required RenderBox? child,
    required SfSliderThemeData sliderThemeData,
    required SfThumb thumb,
    required Animation<double> enableAnimation,
    required TextDirection textDirection,
    required double elevation,
    required double pressedElevation,
    required double hoveredElevation,
    required bool isHovered,
    required bool isPressed,
    required bool isDisabled,
  }) {
    final canvas = context.canvas;

    imageProvider.resolve(ImageConfiguration()).addListener(
      ImageStreamListener(
        (info, _) {
          canvas.drawImage(info.image, Offset(center.dx - (info.image.width / 2), center.dy - (info.image.height / 2)), Paint());
        },
      ),
    );
  }
}
```

- param으로 currenvalue를 전달 받지 못하는 것일까? 👉 변수명이 틀렸나? (사고의 흐름)
  - 빌드를 여러번 해봐도 해결하지 못했다.
- 괜찮습니다.. 🧐 천천히 오류 메세지를 읽어보면 됩니다.

### 💡 해결!

```dart
@override
void paint(
    PaintingContext context,
    Offset center, {
    Animation<double> activationAnimation,
    Animation<double> enableAnimation,
    bool isDiscrete,
    TextPainter labelPainter,
    RenderBox parentBox,
    Size sizeWithOverflow, 💡 /*The missing link*/
    double textScaleFactor, 💡 /*And the missing link I missed*/
    SliderThemeData sliderTheme,
    TextDirection textDirection,
    double value,
  }) //...
```

#### Ref:

- [🖼️ Paint issue after updating Flutter](https://stackoverflow.com/questions/63306463/paint-issue-after-updating-flutter)

### 🚨 hot build!... 그리고 또 오류!

```xml
**Error: The parameter 'textDirection' of the method '_CustomThumbShape.paint' has type 'TextDirection/*1*/', which does not match the corresponding type, 'TextDirection/*2*/', in the overridden method, 'SliderComponentShape.paint'.**
------
**'TextDirection/*1*/' is from 'package:intl/src/intl/text_direction.dart' ('../../../AppData/Local/Pub/Cache/hosted/pub.dev/intl-0.18.1/lib/src/intl/text_direction.dart').'TextDirection/*2*/' is from 'dart:ui'. Change to a supertype of 'TextDirection/*2*/', or, for a covariant parameter, a subtype. required TextDirection textDirection, ^ /C:/src/flutter/packages/flutter/lib/src/material/slider_theme.dart:906:8: Context: This is the overridden method ('paint'). void paint( ^**
```

> ![I'm not crying](https://pbs.twimg.com/media/EAmr-PAWsAEoiWR.jpg)

- 다시... 오류를 읽어봅니다
- 난 괜찮다..

### 💡 해결\_해결!

> 해당 오류는 TextDirection 타입이 충돌하여 발생하는 오류입니다. intl 패키지의 TextDirection과 dart:ui의 TextDirection 상이 함.

```dart
import 'dart:async';
import 'dart:ui' as ui;
//하지만 as로 캐스팅하는건 내 스타일이 아님
```

해서 해결했습니다.
끗—! 🥰
run창이 부지런히 올라가고 빌드 성공!

ㅎㅎ
ㅎㅎ

### 🫨 는, 또 다른 이슈

![Sfslider error](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/cd64734a-de54-4d35-8032-6a5c0df8d446)

![Flutter slider class](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/ad4d9b2b-b803-4c9b-96da-ddf4e1a000ed)

- 월요일 부터 신나는 오류와의 싸움
- 내일 할 일은 futurebuilder를 사용하요 비동기 처리를 해주는 것 입니다.
  - 얍삽하게 future~ late로 하면 안되나~ 했는데 될 리가 없다! 🫨
- Flutter slider 클래스가 비동기 오류가 없다. 하지만 커스텀의 한계가 있어 아마 sfslider + FutureBuild의 조합으로 보완할 예정.
- 난 그래도 순정 flutter class 사용을 지향.
- 반나절을 쓴 고군분투 였지만, 기록하고 나니 생각보다 소소하다. 그래도 짧은시간 동안 집중해서 해결해냈음!

---

## <p align="center">📆 1/16</p>

## 🪄 FutureBuilder

#### 🥰 Solved!

---

![solved](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/d5ac2f3a-314b-4fde-89ea-517c386d2577)

- 🙂 행복합니다.
- 로직은 간단.

```dart
@override
Widget build(BuildContext context) {
  return FutureBuilder<ui.Image>(
      future: _loadImage,
      builder: (context, snapshot) {
        if (snapshot.hasData || snapshot.data != null) {
          // 기존 조건문은 3가지로 구분되어있어, 플리커 현상이 반복됐다.
          // 여기서는 데이터가 있고, Null이라면 바로 이미지를 로드하도록 했다.
          return SliderTheme(
            data: SliderThemeData(
              trackHeight: 28,
              inactiveTrackColor: Colors.grey.shade300,
              activeTrackColor: const Color(0xFFFFE900),
              thumbShape: SliderThumbImage(snapshot.data!),
              //이 부분 중요.
            ),
            child: Slider(
	             // ...
              onChanged: (value) {},
            ),
          );
        }
	      // null이면 플러터가 화낸다. 뭐라도 return 해야한다
        return const SizedBox.shrink();
      });
}
```

#### 🦄 이미지 비동기 처리하기

```dart
Future<List<ui.Image>> loadImages(List<ImageProvider> providers) async {
  //  다수의 이미지를 동시에 로드
  final images = await Future.wait(
    providers.map((ImageProvider provider) async {
      final Completer<ui.Image> completer = Completer<ui.Image>();
      final ImageStream stream = provider.resolve(ImageConfiguration());
      ImageStreamListener? listener;

      listener = ImageStreamListener((ImageInfo info, bool _) {
        completer.complete(info.image);
        stream.removeListener(listener!);
      }, onError: (dynamic error, StackTrace? stackTrace) {
        completer.completeError(error);
        stream.removeListener(listener!);
      });

      stream.addListener(listener);
      return completer.future;
    }).toList(),
  );
  return images;
}
```

Ref:

- [Flutter change slider thumb to image](https://stackoverflow.com/questions/70786192/flutter-change-slider-thumb-to-image)

## <p align="center">📆 1/19</p>

## `TextFormField` + `focusNode`

1. 🫤 onChange를 활용할 때, 입력값이 계속 바뀌면서 예상과 다르게 작동
1. `완료`, `저장` 할 때 두 값을 바꾸도록 사용성 개선!
1. focusNode를 활용해서 포커스를 잃으면 적용.
1. 💡 focus가 유지 된 채, 저장을 누르면 강제로 포커스를 해제하도록 함.
1. 🥰 오예.

![333](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/fe209bd0-ec4f-4efd-8193-c2ebc044e9ae)
![2222](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/9316d4a9-f612-4c3b-b0c7-9153be7017ec)

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        body: Center(
          child: MyWidget(),
        ),
      ),
    );
  }
}

class MyWidget extends StatefulWidget {
  @override
  State<MyWidget> createState() => _MyWidgetState();
}

class _MyWidgetState extends State<MyWidget> {
  final _formKey = GlobalKey<FormState>();
  final TextEditingController textController = TextEditingController();
  FocusNode _focusNode = FocusNode();

 @override
  void initState() {
    super.initState();
    _focusNode.addListener(_focusListener);
  }

  @override
  void dispose() {
    super.dispose();
    _focusNode.dispose();
  }

  void _focusListener() {
    if (!_focusNode.hasFocus) {
      print('focus lost');
    }
  }


  Future<void> _onSave() async {
    if (FocusScope.of(context).hasFocus) {
      FocusScope.of(context).unfocus();
    }

    if (_formKey.currentState!.validate()) {
      _formKey.currentState!.save();
      print('👏 저장완료!');
      print('saved ! ${textController.text}');
    } else {
      print('🫨 저장 실패');
    }

    _resetTextField();
  }

  void _resetTextField() {
    textController.text = '';
  }

  @override
  Widget build(BuildContext context) {
    return Container(
      margin: const EdgeInsets.all(40),
      height: 150,
      width: 250,
      decoration: BoxDecoration(
        color: Colors.white,
        border: Border.all(color: Colors.black, width: 2),
        borderRadius: BorderRadius.circular(10),
      ),
      child: Form(
        key: _formKey,
        child: Padding(
          padding: const EdgeInsets.all(20),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceBetween,
            children: [
              TextFormField(
                focusNode: _focusNode,
                controller: textController,
                validator: (String? value) {
                  return (value == null || value.isEmpty) ? '다시 입력!' : null;
                },
              ),
              TextButton(
                onPressed: _onSave,
                child: const Text('저장', style: TextStyle(color: Colors.white)),
                style: TextButton.styleFrom(backgroundColor: Colors.black),
              )
            ],
          ),
        ),
      ),
    );
  }
}
```

## <p align="center">📆 1/23</p>

## ExpansionTile

- 펼쳐지는 타일을 구현했습니다.
- 오늘도 많은 역경이 있었습니다.
- [ExpansionTile class](https://api.flutter.dev/flutter/material/ExpansionTile-class.html)

### Issue!

- 구현을 하고 보니, 타이틀을 눌러도 expand 된다.
- 원래 목적은 trailing의 버튼으로만 컨트롤 하는 것
- 🧐 내가 생각한 방법은
  - ListTile을 활용해, height를 조건부로 펼친다
  - ignorePoint를 사용해, 타이틀 터치를 disabled
  - ExpansionPanelList 사용하기...
- 그리고 모든 방법이 다 적합하지 않음

#### solution 1 : ListTile 활용하기

- 문제:
  - height를 하드코딩 해야한다.
  - 반응형으로 높이가 달라질 것이라 탈락.

```dart
  //...
  ListTile(
    title: Text('Title'),
  ),
  //...
  AnimatedContainer(
        duration: Duration(milliseconds: 300),
        height: _isExpanded ? 150.0 : 0.0,
        // 🫨🫨🫨🫨🫨
        child: _isExpanded ? CustomWidget() : SizedBox.shrink(),
      ),
```

#### solution 2 : ListTile 활용하기

- ignorePoint로 세부적인 컨트롤이 불가하다.
  - 하위 위젯요소가 모두 disabled 됨
  - 다른 widget이라면 적용이 가능했을 듯.
  ```dart
     IgnorePointer(
            ignoring: true,
            child: ExpansionTile(
              title: Text('Title'),
            )
            //...
  ```

#### solution 3 : ExpansionPanelList 활용하기

- ~~생각해보니, 이거 해보면 될거같다.~~
- 취소합니다. trailing 커스텀 안됩니다.

```dart
ExpansionPanelList(
        expansionCallback: (int index, bool isExpanded) {
          setState(() {
            _isExpanded = !isExpanded;
          });
        },
      )
        //...
```

#### solution 4 : 그럴싸하게 기능 정리하기

- title을 눌러서 expand 되는 것을 응용했다.
- onExpansionChanged 활용

```dart
ExpansionTile(
    controller: _expansionController, // 컨트롤러
    onExpansionChanged: (bool expanding) {
      setState(() {
        _isExpanded = expanding;
        _isSelected = expanding;
      });
    },
),
// 아이콘 버튼
IconButton(
  onPressed: () {
    setState(() {
      _isSelected = false;
      _isExpanded = false;
    });
    return _expansionController.collapse();
  },
),
```

![해냄](https://github.com/Dabnii/Dabnii.github.io/assets/134585116/dd59b23c-e726-4981-bc7c-916bc88f3cb0)

- 타이틀, 버튼을 누르면 버튼도 같이 작동하도록 했다.

## <p align="center">📆 1/24</p>

- `SingleChildScrollView + ListView.builder`
- expand 넣으면 SingleChildScrollView와 충돌한다.

```dart
Widget build(BuildContext context) {
    return Scaffold(
      body: Stack(
        children: <Widget>[
          SingleChildScrollView(
            child: Column(
              children: <Widget>[
                ListView.builder(
                  physics: NeverScrollableScrollPhysics(),
                   // 스크롤뷰 충돌방지
                  shrinkWrap: true,
                  itemCount: items.length,
                  itemBuilder: (context, index) {
                    return ListTile(
                      title: Text('${items[index]}'),
                    );
                  },
                ),
              ],
            ),
          ),
          Align(
            alignment: Alignment.bottomCenter,
            child: TextButton(
              onPressed: () {},
              child: Text('Button'),
            ),
          )
        ],
      ),
    );
  }
```
