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
