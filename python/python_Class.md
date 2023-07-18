## 👩‍🏫 Class

- 객체를 생성하기 위한 청사진, 템플릿 (붕어빵틀)
- 객체가 가질 특성(변수), 동작(함수)정의

  - `PascalCase`
  - `snake_case`

  ```python
  class User:
  ```

### 🏗️ Constructor

### `__init__(self)`

- 컨스트럭터라고 불리는 초기화를 위한 함수(메소드)
- 인스턴스화를 실시할 때 반드시 처음에 호출되는 특수한 함수
- 오브젝트 생성(인스턴스를 생성)과 관련하여 데이터의 초기를 실시하는 함수

```python
class Car:
	def __init__(self):
	# 초기화, param은 원하는 만큼 추가 가능
	# initialise attributes
```

```python
class User:

  def __init__(self, user_id, username):
    self.id = user_id
    self.username = username

user_1 = User("001", "Kim")
print(user_1.id) # 001
```

```python
class User:

  def __init__(self, user_id, username):
    self.id = user_id
    self.username = username
    self.followers = 0
    self.following = 0

  def follow(self, user):
    user.followers += 1
    self.following += 1

user_1 = User("001", "Kim")
user_2 = User("002", "Park")

user_1.follow(user_2)
```

```python
class Account:

  def __init__(self, owner, balance):
    self.owner = owner
    self.balance = balance

  def __repr__(self):
    return f'Account({self.owner!r}, {self.balance!r})'

  def deposit(self, amount):
    self.balance += amount

  def withdraw(self, amount):
    self.balance -= amount

  def inquiry(self):
    return self.balance


# Account 인스턴스 생성
my_account = Account("John Doe", 1000)

# 현재 잔액 조회
print(my_account.inquiry())  # 출력: 1000

# 예금 수행
my_account.deposit(500)

# 출금 수행
my_account.withdraw(200)

# 현재 잔액 조회
print(my_account.inquiry())  # 출력: 1300
```

- `Account`는 `owner`, `balance` 속성을 가짐
- `inquiry(self)`메서드를 가짐

## instance

- 클래스의 특정한 발생 또는 `실체화`
- 객체와 동의어
- 객체를 생성할 때 클래스의 인스턴스를 생성

```python
a = Account('Guido', 1000.0) #Account.__init__(a, 'Guido', 1000.0)을 호출
b = Account('Eva', 10.0) #Account.__init__(b, 'Eva', 10.0)을 호출
```

- `init()` 안에서 속성은 self에 할당되어 인스턴스에 추가된다. 예를 들어, `self.owner = owner`는 owner속성을 인스턴스에 추가한다. 일단 새로 만든 인스턴스가 반환되면, 속성`(.)` 연산자를 사용하여 클래스의 속성과 메서드에 접근할 수 있다.

```python
a.deposit(100.0) #Account.deposit(a, 100.0)을 호출
b.withdraw(50.00) #Account.withdraw(b.50.0)을 호출
owner = a.owner # 예금주를 가져옴
```

## object

- 객체는 클래스의 인스턴스
- 클래스의 청사진을 사용하여 특정한 객체를 나타냄
- 고유한 속성을 가지며 고유한 메서드의 동작 수행 가능
- `인스턴스화` 클래스를 함수처럼 호출하여 생성

```python
a = Account('Guido', 1000.0)
```

- `a` 는 `오브젝트(인스턴스)`
- `Account`는 `클래스`

---

Ref.

- 📘 파이써닉한 파이썬을 익히는 간결한 안내서 | 7. Class
- [9. Classes](https://docs.python.org/3/tutorial/classes.html)
