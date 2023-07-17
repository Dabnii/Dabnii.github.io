## 👩‍🏫 Class

- `PascalCase`
- `snake_case`

  ```python
  class User:
  ```

### 🏗️ Constructor

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
