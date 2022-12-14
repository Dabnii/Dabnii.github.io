# <p align=center> Object `{ Key : Property }`

## <p align=center> ๐ก ๊ฐ์ฒด Object : `Key` ๊ฐ๊ณผ `Value`๊ฐ์ ๊ฐ์ง `ํ๋กํผํฐ์งํฉ`

- Key ๊ฐ๊ณผ Value ๊ฐ์ ์์ผ๋ก ๊ฐ์ง๋ฉฐ, <br>
- ๋ฐฐ์ด๊ณผ๋ ๋ค๋ฅด๊ฒ ์์๊ฐ ์ค์ํ์ง ์์ต๋๋ค.

## Object ๊ฐ์ฒด์ ๋ฐฐ์ด์ ์ฐจ์ด์ 

| ๊ฐ์ฒด(Object)                       | ๋ฐฐ์ด(Array)                   |
| ---------------------------------- | ----------------------------- |
| {Key:value}๋ฅผ ๊ฐ์ง Property์ ์งํฉ | ๋ฐ์ดํฐํ์ : ์์๋ก ๋์ด      |
| `{ }` ์ค๊ดํธ                       | `[ ]` ๋๊ดํธ                  |
| ์์๊ฐ ์๋ค                        | ์์๊ฐ ์๋ค (์์๊ฐ ์ค์ํ๋ค) |

### { Key : Property `,` Key : Property }

- ์ผํ๋ฅผ ์ฌ์ฉํ์ฌ ๊ตฌ๋ถํฉ๋๋ค.

## ๐ ๊ฐ์ฒด๋ฆฌํฐ๋ด Object Literal

> ๊นจ์ tip:
>
> - ๋ฐฐ์ด๊ณผ ๊ฐ์ฒด๋ฅผ ํผํฉํ์ฌ ์ฌ์ฉํ๋ ๊ฒฝ์ฐ๊ฐ ๋ง์ต๋๋ค.
> - ๋๋ํ ์ฌ์ฉํ  ๋ ๊ฐ๋ ฅํด ์ง๋๋ค

```Java script
let person1 = {
  name: '๊น์ต๋ช',
  bloodType: 'Aํ',
  mbti: 'ENFP',
  favoriteCoffee: '์์ด์ค์๋ฉ๋ฆฌ์นด๋ธ'
}
```

<br>
<br>

# ๐ซ ๊ฐ์ฒด์ Properties์ ์ ๊ทผํ์!

## 1๏ธโฃ Dot Notation `.`

- Property identifies can only be alphanumeric (and `_` and `$`)
- Property identifiers cannot start with a number.
- Property identifiers cannot contain variables.
- OK ๐ โ `obj.prop_1`, `obj.prop$`
- Not OK ๐โโ๏ธ โ `obj.1prop`, `obj.prop name`

```Java script
let myself = {
	name : 'Code Kim',
	Country: 'South Korea',
	age: 30,
	cats: ['๋ฃจ์ด','๋๋น'],
	myKey: 'Hello'
}
let myKey = 'cat'
console.log(myself[cats]) // cats: ['๋ฃจ์ด','๋๋น']
console.log(myself.myKey) // 'Hello' Dot์ ๋ณ์์ฌ์ฉ ๋ถ๊ฐ -> key๋ก ์ธ์
```

<br>

## 2๏ธโฃ Bracket Notation `[ ]`

- Property identifiers have to be a String or a variable that references a String.
- It is okay to use variables, spaces, and Strings that start with numbers
- OK ๐ โ `obj["1prop"]`, `obj["prop name"]`

```Java script
myself['name'] // 'Code kim'
myself['age'] // 30
//e.g.
let myCats = myself['cats']
console.log(myCats)
// cats: ['๋ฃจ์ด','๋๋น']
```

```Java script
const person= {firstName: "Mick", lastName: "Jagger"}
person.firstName
//"Mick"
//or
person['fistName']
//"Mick"
//์์ ๋๊ฐ์ง ๋ฒ์ ์ ์ ํจํจ
โ person[firstName] //๋ฐ์ดํ๊ฐ ์์ด์ ์ ํจํ์ง ์์
```

<br>
<hr>
<br>

## โ๏ธ ๊ฐ์ฒด ์์ ํ๊ธฐ | Upadte & Edit

```Java script
const obj = {oldKey: 'value'};
obj['newKey'] = obj['oldKey'];
delete obj['oldKey'];
console.log(obj); // ๐๏ธ {newKey: 'value'}
// https://bobbyhadz.com/blog/javascript-rename-object-key
```

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
  // both correct! ๐ฅ
  myDog.name = "Happy Coder"
  return myDog.name;
}
```

<br>

## ๐ ๊ฐ์ฒด ์์ฑ ์ถ๊ฐ

```Java script
obj.key3 = "value3";
obj["key3"] = "value3";
```

<br>

## โ๏ธ ๊ฐ์ฒด ์์ฑ ์ญ์ 

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
  //delete myDog.tails; ๐
  delete myDog["tails"];
  return myDog;
}
```

<br>
<hr>
<br>

## ๐ป Code test

### ๐ ๊ฐ์ฒด ์์ ๊ฐ์ฒด ์ ๊ทผ

```Java script
// ๋ง๋ ํ์ด
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
  //๋ต์ "maps"
  return gloveBoxContents;
}
```

๐ค Pseudo code

> 1. ์ ์ธ๋ ํจ์ mystorage ์ ๊ทผ
> 2. car๋ก ๋ค์ด๊ฐ๋ค
> 3. inside์ ๋ค์ด๊ฐ์ ~~0๋ฒ ์ธ๋ฑ์ค์ธ ๊ธ๋ก๋ธ ๋ฐ์ค๋ฅผ ๊บผ๋ธ๋ค.~~ ๐คฆโโ๏ธ ๊ฐ์ฒด ์ด๋ฏ๋ก ์ธ๋ฑ์ค๋ถ๊ฐ.
> 4. bracket notation ์ผ๋ก ๊ธ๋ก๋ธ๋ฐ์ค ์ ๊ทผ
> 5. ์ฑ๊ณต! ๐
>    <br>

<hr>
<br>

### ๐ ๊ฐ์ฒด ์์ ๋ฐฐ์ด ์ ๊ทผ

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
  let foundValue = myPlants[1].list[1] //pine ๐
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

๐ค Pseudo code

> 1. myPlants ์ ๊ทผ
> 2. ~~์ธ๋ฑ์ค[1]๋ก ์ ๊ทผ?no. type["trees"].list[1]~~
> 3. ๋ฐฐ์ด ์ด๋ฏ๋ก `["trees"]` ์ฌ์ฉ ๋ถ๊ฐ.
> 4. ๋ฐฐ์ด๋ก ์ ๊ทผ ๋ฐ ์ฑ๊ณต ๐
>    <br>

<hr>
<br>

Quick review:

- Pseudo code ๋๋ถ์ ๋ผ๋ฆฌ์  ์ ๊ทผ์ด ์์ฐ์ค๋ฌ์์ก๋ค.<br>
- ๊ฐ์ฒด์ ์ค๋ธ์ ํธ์ ์ฐจ์ด๋ฅผ ํ์คํ ์ดํด<br>
- ์์ผ๋ก์ goal: ๋ธํธํ๊ณ  ๋ณต๊ธฐํ๊ธฐ!<br>

F.I.N ๐ช

<hr>
์ถ์ฒ

- https://codeburst.io/javascript-quickie-dot-notation-vs-bracket-notation-333641c0f781
