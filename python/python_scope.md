# <p align="center">🐍 Python | Scope</p>

## <p align="center"> 🔭 Scope</p>

## 🔭 Scope

- `유효범위`
- 변수는 생성된 영역 내 `스코프` 에서만 사용할 수 있음
- A variable is only available from inside the region it is created. This is called `scope`.

### 🌏 Global scope

- 파이썬 코드 본문에 생성된 변수는 `전역 변수`이며 `전역 범위`에 속함
- 전역 변수는 전역과 로컬을 막론하고 `모든 범위에서 사용`

```python
x = 300

def myfunc():
  print(x)

myfunc()

print(x)
# 300
```

### 📌 Local scope

- 함수내에 존재
- 해당 함수내에 서만 사용
    
    ```python
    def myfunc():
      x = 300
      print(x)
    
    myfunc()
    # 300
    ```
    
    ```python
    hello = "World"
    
    def greeting():
      hi = "good to see you"
      print(hi)
    
    print(hi)
    # NameError: name 'hi' is not defined
    ```
    

### 🏷️ Naming Variables

- 함수 내부와 외부에서 동일한 변수 이름으로 작업하는 경우 Python은 이를 두 개의 `개별 변수로 취급`
- 하나는 `전역 범위`(함수 외부)에서 사용
- 다른 하나는 `로컬 범위`(함수 내부)에서 사용

```python
x = 300

def myfunc():
  x = 200
  print(x)

myfunc()

print(x)

# 200
# 300
```

### 🙅 block scope 는 없다

- 블록 스코프는 존재하지 않는다
- `둘러싼 함수와 같은 유효범위`
- `if` , `while` , `for` 와 같이 콜론과 들여쓰기가 있는 모든 코드 블록은 `지역 범위를 만드는 것으로 간주하지 않음`
- `if`, `else`, `for`, `while` 코드 블록은 내부와 외부가 동일

```python
if 3 > 2:
	a_variable = 10
```

```python
game_level = 3
enemies = ["Skeleton", "Zombie", "Alien"]

if game_level < 5:
    new_enemy = enemies[0]

print(new_enemy)
# Skeleton
```

```python
game_leve = 3
def create_enemy():
	enemies = ["Skeleton", "Zombie", "Alien"]
	if game_level < 5:
		new_enemy = enemies[0]

print(new_enemy)
# error
# NameError: name 'new_enemy' is not defined
```

## Global Keyword

- 전역 변수를 만들어야 하지만 로컬 범위에 갇혀 있는 경우 전역 키워드를 사용할 수 있습니다.
- `전역 키워드는 변수를 전역으로 수정` 함
    - 또한 함수 내에서 전역 변수를 변경하려면 전역 키워드를 사용
- 버그와 오류를 야기

```python
def myfunc():
  global x
  x = 300

myfunc()

print(x)
# 300
```

## 전역범위

- `상수` ⇒ 대문자 변수

```python
PI = 3.14159
URL = "http://www.goggle.com"
```

---

Ref

- [📎 scope](https://www.w3schools.com/python/python_scope.asp)