## <p align="center">📆4/4</p>

## Python Dict!

```python
keys = input().split()
values = list(map(float, input().split()))

res = dict(zip(keys, values))
# print(res)
keys, values = zip(*res.items())
# 무려 unzip도 할 수 있다고요?
print(keys, values)

# health mana melee attack_speed magic_resistance
# 573.6 308.8 600 0.625 35.7

#### Zip ####
### key, values를 매치하여 dict로 만들어준다
# {'health': 573.6, 'mana': 308.8, 'melee': 600.0, 'attack_speed': 0.625, 'magic_resistance': 35.7}

#### Unzip ####

# ('health', 'mana', 'melee', 'attack_speed', 'magic_resistance') (573.6, 308.8, 600.0, 0.625, 35.7)
```

## <p align="center">📆4/15</p>

### python 으로 별 찍기

```python
repeat = int(input())

for i in range(repeat):  #세로방향
  for j in reversed(range(repeat)):  #reversed가 핵심
    if j > i:
      print(' ', end='')  #공백이 핵심
    else:
      print('*', end='')
    if j < i:
      print('*', end='')
  print()

# 3
# 결과
#   *
#  ***
# *****
# 입력
# 5
# 결과
#     *
#    ***
#   *****
#  *******
# *********

```

### 화면 재진입할 때 이벤트 주고 싶다면?

```dart
void didChangeAppLifecycleState(AppLifecycleState state) { }
```

```dart
  @override
  void didChangeAppLifecycleState(AppLifecycleState state) {
    super.didChangeAppLifecycleState(state);
    if (state == AppLifecycleState.resumed) {
      // 앱이 다시 화면에 그려지고 사용자의 응답을 받을 준비 함
      print('THIS STATE IS +++++ resumed');
    }
    if (state == AppLifecycleState.inactive) {
      // 앱이 비활성화 된 상태
      // inactive => paused 발생
      // 보기가 하나 이상 표시 되지만 입력상태가 없을 때
      print('THIS STATE IS +++++ inactive');
    }
    if (state == AppLifecycleState.detached) {
      // Flutter 엔진에서는 호출 되지만, 호스트 view에서는 분리 된 상태
      print('THIS STATE IS +++++ detached');
    }
    if (state == AppLifecycleState.paused) {
      // 사용자에게 현재 보여지지 않음
      // 또한 사용자의 입력에 응답하지 않음
      print('THIS STATE IS +++++ paused');
    }
    if (state == AppLifecycleState.hidden) {
      // 가려진 상태
      // 일시정지 예정이거나 모든 보기가 숨겨졌을 때
      print('THIS STATE IS +++++ hidden');
    }
  }
```

---

- [AppLifecycleListener class](https://api.flutter.dev/flutter/widgets/AppLifecycleListener-class.html)

- [AppLifecycleState](https://api.flutter.dev/flutter/dart-ui/AppLifecycleState.html)

## <p align="center">📆4/16</p>

## 🧪Flask

1. `python -m venv venv`
2. `cd venv`
3. `cd scripts`
4. `activate.bat`
5. 인터프리터 설정 F1 > `Python N.N.N (’venv’: venv)`
6. 상위폴더에서 `flask run`
7. 가상환경 안에 모듈 설치 `python -m pip install —upgrade pip`
8. `pip install flask`
9. 👇 아래 `app.py` 실행

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return 'this is home!'

if __name__ == '__main__':
    app.run('0.0.0.0')

# ---
# WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
#  * Running on all addresses (0.0.0.0)
#  * Running on http://127.0.0.1:5000
# 헤헤 해냄
```
