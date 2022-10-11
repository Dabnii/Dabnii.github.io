# 💡 Object

### 📎 배열 Array : 여러개의 `데이터`가 `순서`를 가지고 나열 된 집합 `[]` 대괄호

<br>

### 💡 객체 Object : `Key` 값과 `Value`값을 가진 `프로퍼티 집합`

<hr>

## `{ Key : Property }`

Key 값과 Value 값을 쌍으로 가지며, 배열과는 다르게 순서가 중요하지 않습니다.

## { Key : Property `,` Key : Property }

- 쉼표를 사용하여 구분합니다.

## 📌 객체리터럴 Object Literal

- 배열과 객체를 혼합하여 사용하는 경우가 많음
- 나란히 사용할 때 강력해 짐

```Java script
let person1 = {
  name: '김익명',
  bloodType: 'A형',
  mbti: 'ENFP',
  favoriteCoffee: '아이스아메리카노'
}
```

<br>

# 🎫 객체의 Properties에 접근하자!

## 1️⃣ Dot Notation `.`

- Property identifies can only be alphanumeric (and `_` and `$`)
- Property identifiers cannot start with a number.
- Property identifiers cannot contain variables.
- OK — `obj.prop_1`, `obj.prop$`
- Not OK — `obj.1prop`, `obj.prop name`

```Java script
let myself = {
	name : 'Code Kim',
	Country: 'South Korea',
	age: 30,
	cats: ['냥','냥냥'],
	myKey: 'Hello'
}

let myKey = 'cat'

console.log(myself[cats]) // 	cats: ['냥','냥냥'],
soncole.log(myself.myKey) // 'Hello' Dot은 변수사용 불가 -> key로 인식
```

## 2️⃣ Bracket Notation `{ }`

- Property identifiers have to be a String or a variable that references a String.
- It is okay to use variables, spaces, and Strings that start with numbers
- OK — `obj["1prop"]`, `obj["prop name"]`

```Java script
myself['name'] // 'Code kim'
myself['age'] // 30

//e.g.
let myCats= myself['cats']
console.log(myCats)
// cats: ['냥','냥냥']
```

```Java script
const person= {firstName: "Mick", lastName: "Jagger"}

person.firstName
"Mick"
or
person['fistName']
"Mick"
//위의 두가지 버전은 유효함

🙅 person[firstName] //따옴표가 없어서 유효하지 않음
```

## ✏️ 객체 수정하기 | Upadte & Edit

```Java script
const midterms = {danielle;96, thomas:78}

midterms.ezra = 'B+'
midterms['antonio']='A-'
midterms.thomas ='C+'
```

```java script
function updateObject() {
  let myDog = {
    "name": "Coder",
    "legs": 4,
    "tails": 1,
    "friends": ["freeCodeCamp Campers"]
  };

  myDog["name"] = "Happy Coder"
  // both correct! 🔥
  myDog.name = "Happy Coder"

  return myDog.name;
}
```

## 🆕 객체 속성 추가

```Java script
obj.key3 = "value3";
obj["key3"] = "value3";
```

## ✂️ 객체 속성 삭제

```Java script
delete object.property
    delete object['property']
```

```Java script
function deleteProperty() {

  let myDog = {
    "name": "Happy Coder",
    "legs": 4,
    "tails": 1,
    "friends": ["Wecode Bootcamp"],
    "bark": "woof"
  };

  //delete myDog.tails; 👍
  delete myDog["tails"];

  return myDog;
}
```

<hr>

## 💻 Code test

### 📚 객체 안의 객체 접근

```Java script
// 맞는 풀이
function accessObject() {

  let myStorage = {
    "car": {
      "inside": {
        "glove box": "maps",
        "passenger seat": "crumbs"
      },
      "outside": {
        "trunk": "jack"
      }
    }
  };

  let gloveBoxContents = myStorage["car"].inside["glove box"];

  //답은 "maps"

  return gloveBoxContents;
}

```

🤔 Pseudo code

> 1. 선언된 함수 mystorage 접근
> 2. car로 들어간다
> 3. inside에 들어가서 ~~0번 인덱스인 글로브 박스를 꺼낸다.~~ 🤦‍♀️ 객체 이므로 인덱스불가.
> 4. bracket notation 으로 글로브박스 접근
> 5. 성공! 👍

<hr>

### 📚 객체 안의 배열 접근

```Java script
function accessArray() {
let myPlants = [
    {
      type: "flowers",
      list: [
        "rose",
        "tulip",
        "dandelion"
      ]
    },
    {
      type: "trees",
      list: [
        "fir",
        "pine",
        "birch"
      ]
    }
  ];

  let foundValue = myPlants[1].list[1] //pine 👍

  // answer = pine
  return foundValue;
}

//
let foundValue = myPlants[1] //
//[object Object] {
//  list: ["fir", "pine", "birch"],
//  type: "trees"
// }

```

🤔 Pseudo code

> 1. myPlants 접근
> 2. ~~인덱스[1]로 접근?no. type["trees"].list[1]~~
> 3. 배열 이므로 `["trees"]` 사용 불가.
> 4. 배열로 접근 및 성공 👍

<hr>

- Pseudo code로 접근하여 머리속으로 코드를 짤 수 있어 논리적 접근이 자연스러워졌다.<br>
- 객체와 오브젝트의 차이를 확실히 이해했다.<br>
- 앞으로의 goal: 노트하고 복기하기!<br>
