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
