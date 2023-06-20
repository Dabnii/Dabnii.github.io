# <p align="center">✈️ Flutter Widget</p>

### <p aligh="center">✈️ Flutter Widget</p>

[📎 Flutter widgets](https://docs.flutter.dev/ui/widgets)


|　|　|　|　|　|
|--|--|--|--|--|
|Accessibility|Animation and Motion|Assets, Images, and Icons|Async|Basics|
|Cupertino(iOS)|Input|Interaction Models|Layout|Material Components|
|Painting|Scrolling|Styling|Text|　|

### 📝 Google Font [📎Flutter | Doc](https://pub.dev/packages/google_fonts)

- `installing`

    ```dart
    $ flutter pub add google_fonts
    ```

    ```dart
    //import
    import 'package:google_fonts/google_fonts.dart';
    ```

    ```dart
        Text(
    'This is Google Fonts',
    style: GoogleFonts.lato(),
    ),
    ```

### 🖼 Asset 등록하기

```dart
assets:
  - assets/
  - assets/images
```


### TextButton

```dart
TextButton(
    onPressed: () {
    if (_formKey.currentState!.validate()) {
        Navigator.pushNamed(context, "/home");
    }
    },
    child: Text("Login"))
```
