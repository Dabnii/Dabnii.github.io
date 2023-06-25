# <p align="center">🐍 Python</p>

- `#` 주석
- `variable_name` → under_score
- `type()`

  ```python
  def my_foo:
      print("Hello world!")
  ```

### 🖨️ `print`

```python
print("Day 1 - Python Print \n Function")
#개행
```

### `input`

```python
print("hello" + input(", what's your name? : "))
# hello lee
```

```python
print(len(input("what's your name?")))
```

```python
a = input("a: ")
b = input("b: ")

c=a
a=b
b=c
```

```python
bmi = int(weight) / float(height)**2

bmi_as_int = int(bmi)

print(bmi_as_int)
```

### `f-string`

```python
name = "Alice"
age = 25
print(f"My name is {name} and I am {age} years old.")
```

```python
days = (365 * int(age))
days_1 = (32850 - days)

weeks = (52 * int(age))
weeks_1 = (4680 - weeks)

months = (12 * int(age))
months_1 = (1080 - months)
print(f"you have {days_1} days , {weeks_1} weeks, and {months_1} months left " )
```

### 🧾 Tip codes

```python
print("Welcome to the tip calculator!")
bill = float(input("What was the total bill? $"))
tip = int(input("How much tip would you like to give? 10, 12, or 15? "))
people = int(input("How many people to split the bill?"))

tip_as_percent = tip / 100
total_tip_amount = bill * tip_as_percent
total_bill = bill + total_tip_amount
bill_per_person = total_bill / people
final_amount = round(bill_per_person, 2)

print(f"Each person should pay: ${final_amount}")
```

## 🤙 `Conditional`, `if-else` & `elif`

### `modular`

```python
x = 10
result = "양수" if x > 0 else "음수"
print(result)
# 출력: 양수
```

### `elif` → `else if`

```python
x = 10

if x > 0:
    print("양수")
elif x < 0:
    print("음수")
else:
    print("0")
```

### `round`

```python
bmi = round(weigt/ height ** 2)
	if bmi <18.5:
			print(f"your {bmi}, a normal weight.")
	elif bmi < 25:
	  print(f"Your BMI is {bmi}, you have a normal weight.")
	elif bmi < 30:
	  print(f"Your BMI is {bmi}, you are slightly overweight.")
	elif bmi < 35:
	  print(f"Your BMI is {bmi}, you are obese.")
	else:
	  print(f"Your BMI is {bmi}, you are clinically obese.")
```

- `else`, `modular` test
  ```python
  if (year % 4 == 0) and (year % 100 != 0) or (year % 400 == 0):
      print("LEAP")
  else :
      print("NO leap")
  ```

## 🎲 Random

### `random.randint`

```python
import random

random_integer = random.randint(1, 10)
# 0~10의 난수
print(random.randint(0,5))
# 0~5의 난수
```

### `random.random()`

- 0~1 사이의 부동 난수

```python
print(random.random())
```

```python
import random

user_turn = random.randint(0,1)

if user_turn == 1:
  print('head!')
elif user_turn == 0:
  print('tails!')
```

## Data structure

### List

`[item, item]`

```python
# array in Js 유사!
# index로 아이템 접근 가능

city_name.append("Busan")
# 항목 하나를 마지막에 추가

city_name.extend(["California","Roma","Paris"])
# list 확장
```

- `split()`
  ```python
  names_string.split(",")
  ```

### **Setting maxsplit = value**

```python
input = "hello, Engineering and Medical, are two different disciplines"

# maxsplit = 1, returns a list with 2 elements..
i = input.split(",", 1)

print(i)

# input.split(0, -1)
```

### Nested list

```python
weekdays = ["Mon","Tue","Wed","Thur","Fri"]
weekends = ["Sun", "Sat"]

week = [weekdays, weekends]
# week = [['Mon', 'Tue', 'Wed', 'Thur', 'Fri'], ['Sun', 'Sat']]

```

```python
row1 = ["⬜️","️⬜️","️⬜️"]
row2 = ["⬜️","⬜️","️⬜️"]
row3 = ["⬜️️","⬜️️","⬜️️"]
map = [row1, row2, row3]
print(f"{row1}\n{row2}\n{row3}")

position = input("Where do you want to put the treasure? ")

horizontal = int(position[0])
vertical = int(position[1])

map[vertical - 1][horizontal - 1] = "X"

print(f"{row1}\n{row2}\n{row3}")
```

### Rock, scissors paper!

```python
bot_turn = random.randint(0, 2)

user_turn = int(input('"rock is 0" "scissors is 1" "paper is 2"\n'))

if (user_turn == 0 and bot_turn == 1):
    print("user win!")
elif (user_turn == 1 and bot_turn == 2):
    print("user win!")
elif (user_turn == 2 and bot_turn == 0):
    print("bot win!")
elif (bot_turn == 0 and user_turn == 1):
    print("bot win!")
elif (bot_turn == 0 and user_turn == 2):
    print("bot win!")
else:
    print("tight!")
```

- `int` → 입력 값 정수로 변경
- `and` → boolean logical conjuction

## 🔃 Loops!

![Loop Animation](https://github.com/Dabnii/Dabnii.github.io/assets/110847597/4fed8f0f-9b1e-412a-9095-b96f8bfc83c4)


```python
# Iterating over a sequence
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Iterating over a range of numbers
for i in range(1, 6):
    print(i)
```

### 🐝 tips

```python
sum(list) #list sum
len(list) #list length
```

### Average height

```python
student_heights = input("Input a list of student heights ").split()
for n in range(0, len(student_heights)):
  student_heights[n] = int(student_heights[n])
###
total_height=0
for height in student_heights:
  total_height += height
print(f"total height = {total_height}")

number_of_students=0
for student in student_heights:
  number_of_students +=1
print(f"number of students = {number_of_students}")

average_of_height = round(total_height / number_of_students)
print(average_of_height)
```

### highest score

```python
student_scores = input("Input a list of student scores ").split()
for n in range(0, len(student_scores)):
  student_scores[n] = int(student_scores[n])
print(student_scores)
# 🚨 Don't change the code above 👆
heighest_score = 0
for score in student_scores:
  if score > heighest_score:
    heighest_score = score
print(f"the highest score is {heighest_score}")
```

### `range()`

```python
range(5, 10)
   # 5, 6, 7, 8, 9

range(0, 10, 3)
   # 0, 3, 6, 9

range(-10, -100, -30)
  # -10, -40, -70
```

- https://docs.python.org/ko/3.6/tutorial/controlflow.html#the-range-function

### `range()` 증가폭 사용하기

```python
>>> for i in range(0, 10, 2):
# 0부터 8까지 2씩 증가
# ...
print('Hello, world!', i)
# ...
# Hello, world! 0
# Hello, world! 2
# Hello, world! 4
# Hello, world! 6
# Hello, world! 8
```

```python
# 짝수 더하기
total_num = 0
for i in range(2,101,2):
  total_num += i
print(total_num)

total_num =0
for i in range(1,101):
  if i % 2 == 0 :
    total_num += i
print(total_num)
```

### FizzBuzz!

```python
for i in range (1, 101):
  if i % 5 == 0 and i % 5 == 0 :
    print("FizzBuzz")
  elif i % 3 == 0:
    print("Fizz")
  elif i % 5 == 0:
    print("Buzz")
  else:
    print(i)

# 1
# 2
# Fizz
# 4
# Buzz
# Fizz
# 7
# 8
# Fizz
# Buzz
# 11
# Fizz
# 13
# 14
# FizzBuzz
```

### **`randint(a, b)`**

- Returns a random integer between **a** and **b** (both inclusive). This also raises a `ValueError` if `a` > `b`.

### `random.choice('abcd')`

- _`Choose a random element`_

### `random.shuffle(item)`

```python
new_pw = ""

for char in range(1, nr_letters + 1):
    new_pw += random.choice(letters)

for char in range(1, nr_symbols + 1):
    new_pw += random.choice(symbols)

for char in range(1, nr_numbers + 1):
    new_pw += random.choice(numbers)

print(new_pw)
```

---

Ref

- [📎 python string split function](https://www.askpython.com/python/string/python-string-split-function)
- [📎 random module generate](https://www.askpython.com/python-modules/python-random-module-generate-random-numbers-sequences)

# <p align="center"> 🤖 function, code block, while loops</p>

- `def` → 나만의 함수 생성 키워드
- `:` → 함수의 정의 마무리
- `들여쓰기` → 들여쓰기를 한 코드는 함수에 속함

```python
def foo():
 # do this
 # do this too
 # done!
```

- [🔗 내장 함수](https://docs.python.org/ko/3/library/functions.html)

### not

```python
while not at_goal():
	jump()

while at_goal != true:
	jump()
```

# `while` or `for in`?

### `while`:

- 설정한 조건에 도달할 때 까지 수 없이 반복할 때 적합
- 실행횟수 미지(위험성)

### `for in`

- 출력과 간단한 작업을 할 때 적합
- 실행횟수 고정

- The functions **`move()`** and **`turn_left()`**.
- The conditions **`front_is_clear()`** or **`wall_in_front()`**, **`at_goal()`**, and their negation.
- How to use a **`while`** loop and an **`if`** statement.

```python
def turn_right():
    turn_left()
    turn_left()
    turn_left()

def jump():
    turn_left()
    move()
    turn_right()
    move()
    turn_right()
    move()
    turn_left()

while not at_goal():
    if wall_in_front():
        jump()
    else:
        move()
```

```python
def turn_right():
    turn_left()
    turn_left()
    turn_left()

def jump():
    turn_left()
    while wall_on_right():
        move()

    turn_right()
    move()
    turn_right()

    while front_is_clear():
        move()
    turn_left()

while not at_goal():
    if wall_in_front():
        jump()
    else:
        move()
```

---
## Prime number!

```python
def is_prime_number(num):
    for i in range(2, num):
        if num % i == 0:
            return print("value is not primeNumber")
    return print("value is PrimNumber")
```
<details>
<summary>dart: prime number</summary>

```dart
//별안간 다트로 작성해본 primenumber 찾기

main() {
  List<int> numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  
  for (int num in numbers) {
    bool isPrime = true;
    
    if (num < 2) {
      isPrime = false;
    } else {
      for (int i = 2; i <= num % 2; i++) {
        if (num % i == 0) {
          isPrime = false;
          break;
        }
      }
    }
    
    if (isPrime) {
      print("$num is a prime number");
    } else {
      print("$num is not a prime number");
    }
  }
}
```

</details>


## 📔 Dictionaries & nesting

### 📔Dictionaries

- `key:value` 를 가짐
- `immutable` 한 키(key)와` mutable한 값(value)`으로 맵핑되어 있는 순서가 없는 집합
- immutable data type as keys (e.g., strings, numbers, tuples)
- 중복되는 값은 마지막 값으로 덮어씌워짐
- `key`로 접근

```python
sample = {"Key": "value"}
```

```python
# key에 접근
sample["keyname"]

# 값 추가
d['ghi'] = 999
d
{'abc': 5, 'def': 2, 'ghi': 999}
```

### ✨ Create empty dictionary

```dart
my_dict = dict()
```

```python
sample = {"Key": "value"}
```

```python
# key에 접근
sample["keyname"]

# 값 추가
d['ghi'] = 999
d
{'abc': 5, 'def': 2, 'ghi': 999}
```

```dart
for key in sample_dictionary:
	print(key)
	// key
	print(sample_dictionary[key])
	// value
```

```python
student_scores = {
  "Harry": 81,
  "Ron": 78,
  "Hermione": 99, 
  "Draco": 74,
  "Neville": 62,
}

for student in student_scores:
  score = student_scores[student]
  if score > 90:
    student_grades[student] = "OutStanding"
  elif score < 90 and score > 81:
    student_grades[student] = "Exceds Expectations!"
  elif score < 80 and score > 70:
    student_grades[student] = "Acceptable"
  else:
    student_grades[student] = "Fail"    
```

### 📁Nesting

```python
nested_dict = {}
nested_dict['person1'] = {}
nested_dict['person1']['name'] = 'John'
nested_dict['person1']['age'] = 30
nested_dict['person1']['city'] = 'New York'

nested_dict = {
    'person1': {
        'name': 'John',
        'age': 30,
        'city': 'New York'
    },
    'person2': {
        'name': 'Alice',
        'age': 25,
        'city': 'London'
    },
    'person3': {
        'name': 'Bob',
        'age': 35,
        'city': 'Paris'
    }
}
```

```python
artist_dict = {
    'Leonardo da Vinci': 'Mona Lisa',
    'Vincent van Gogh': 'Starry Night',
    'Pablo Picasso': 'Guernica',
    'Michelangelo': 'David',
    'Claude Monet': 'Water Lilies',
    'Salvador Dali': 'The Persistence of Memory',
    'Frida Kahlo': 'The Two Fridas',
    'Edvard Munch': 'The Scream',
    'Georgia O\'Keeffe': 'The Black Iris',
    'Andy Warhol': 'Campbell\'s Soup Cans'
}

artist_dict['Kim'] = "untitle"
# 'kim' : 'untitle'
```

### add items on list + dictionary

- `append`

```python
travel_log = [
    {
        "country": "France",
        "visits": 12,
        "cities": ["Paris", "Lille", "Dijon"]
    },
    {
        "country": "Germany",
        "visits": 5,
        "cities": ["Berlin", "Hamburg", "Stuttgart"]
    },
]

def add_new_country(country_visited, times_visited, citied_visited):
    new_country = {}
    new_country["country"] = country_visited
    new_country["visits"] = times_visited
    new_country["cities"] = citied_visited
    travel_log.append(new_country)

add_new_country("Russia", 2, ["Moscow", "Saint Petersburg"])
print(travel_log)
```

---

- [📎 Dictionary](https://wikidocs.net/16043)

### The highest bidding!

1. `Bool` → 옥션 진행 여부
2. `bids` → `{name: bidding}` dictionary
3. int `highest_bid`
4. winner = `bidder`(`bidding_record Key == name`)

```python
bidding_finished = False
bids = {}

def find_highest_bidder(bidding_record):
    highest_bid = 0
    winner = ""
    for bidder in bidding_record:
        bid_amount = bidding_record[bidder]
    if bid_amount > highest_bid:
        highest_bid = bid_amount
        winner = bidder
    print(f"the winner is {winner} with ${highest_bid}")

while not bidding_finished:
    name = input("name?")
    price = int(input("What is your bid?"))
    bids[name] = price
    should_continue = input("Are there any other bidders? 'Y' or 'N'.")

    if should_continue == "N":
        bidding_finished = True
        find_highest_bidder(bids)
    elif should_continue == "Y":
        clear()
```

---

- [📎 Dictionary](https://wikidocs.net/16043)

## 🏁 Return

- `return` == 함수의 마지막
- 하나 이상을 가질 수 있음
    
    ```python
    def format_name(f_name, l_name):
      if f_name == "" or l_name== "":
        return "you didn't provide valid inputs."
      formated_f_name = f_name.title()
      formated_l_name = l_name.title()
      return f"{formated_f_name} {formated_l_name}"
    
    print(format_name("lee", "john"))
    ```
    

### 🌙 leap year refactor

```python
def is_leap(year):
  if year % 4 == 0:
    if year % 100 == 0:
      if year % 400 == 0:
        return True
      else:
        return False
    else:
        return True
  else:
    return False
    
def days_in_month(year, month):
  month_days = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
  if month > 12 or month < 1:
    return "Invalid month entered."
  if month == 2 and is_leap(year):
    return 29
  return month_days[month - 1]

year = int(input("Enter a year: "))
month = int(input("Enter a month: "))
days = days_in_month(year, month)
print(days)
```

### 🧮 Calculator

```python
def add(n1, n2):
    return n1 + n2

def divide(n1, n2):
    return n1 / n2

def takeaway(n1, n2):
    return n1 - n2

def multiply(n1, n2):
    return n1 * n2

n1 = int(input("Enter the first number: "))
purpose_symbol = input("Enter the operation symbol (+, -, *, /): ")
n2 = int(input("Enter the second number: "))

purpose = {"+": add, "-": takeaway, "*": multiply, "/": divide}

# 💡
if purpose_symbol not in purpose:
    print("Invalid operation symbol.")
else:
    calculation_func = purpose[purpose_symbol]
    answer = calculation_func(n1, n2)
    print(f"{n1} {purpose_symbol} {n2} = {answer}")
```