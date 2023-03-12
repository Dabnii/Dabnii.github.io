# <p align="center">📆 3/9 Challenge</p>

<details>
<summary> 📃 Homework 01</summary>

```typescript
type Last = {
  <T>(arr: T[]): T | undefined;
};

type Prepend = {
  <T>(arr: T[], item: T): T[];
};

const last: Last = arr => {
  return arr[arr.length - 1];
};

const prepend: Prepend = (arr: any, item: any) => {
  return [item, ...arr];
};

let arr = [1, 2, 3];
```

</details>

# <p align="center">📆 3/11 Challenge</p>

<details>
<summary>📃 Homework 02</summary>

```typescript
type Words = {
  [key: string]: string;
};

class Dict {
  private words: Words;
  constructor() {
    this.words = {};
  }

  add(word: Word) {
    if (this.words[word.term] === undefined) {
      this.words[word.term] = word.def;
      return console.log(`${word.term} added!`);
    } else {
      return console.log(`${word.term} already exists!`);
    }
  }

  def(term: string) {
    return this.words[term];
  }

  del(term: string) {
    delete this.words[term];
    return console.log(`${term} deleted`);
  }

  update(word: Word) {
    if (this.words.hasOwnProperty(word.term)) {
      this.words[word.term] = word.def;
      return console.log(`${word.term} updated!`);
    } else {
      return console.log(`${word.term} does not exists`);
    }
  }

  showAll() {
    for (let [key, value] of Object.entries(this.words))
      return console.log(`${key}: ${value}`);
  }
  count() {
    return Object.keys(this.words).length;
  }

  upsert(word: Word) {
    if (this.words.hasOwnProperty(word.term)) {
      this.update(word);
      return console.log(`${word.term} added!`);
    } else {
      this.add(word);
      return console.log(`${word.term} already exists`);
    }
  }

  exists(term: string) {
    this.words.hasOwnProperty(term)
      ? console.log(`${term} exists !`)
      : console.log(`${term} dose not exists 😢`);
  }

  bulkAdd(words: Word[]) {
    for (let word of words) {
      this.add(word);
    }
  }

  bulkDelete(terms: string[]) {
    for (let term of terms) {
      this.del(term);
    }
  }
}

class Word {
  constructor(public term: string, public def: string) {}
}

const kimchi = new Word('Kimchi', 'Korean traditional food');
const ramen = new Word('Ramen', 'noodle');
const coffee = new Word('Coffee', 'drug!!');
const latte = new Word('Latte', 'coffee with milk');

const dict = new Dict();
```

</details>

```typescript
  exists(term: string){
    return (this.words.hasOwnProperty(term))? `${term} exists`: "${term} doesn't exist"
  }
```

> 백엔드빛의 code
> 역시 빛...

### ✅ `hasOwnProperty`

- `hasOwnProperty()` 메소드는 객체가 특정 프로퍼티를 가지고 있는지를 나타내는 불리언 값을 반환한다.

```javascript
obj.hasOwnProperty(prop);
```

```javascript
const object1 = {};
object1.property1 = 42;

console.log(object1.hasOwnProperty('property1'));
// Expected output: true
```

---

출처:

- [📎 hasOwnProperty() MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)
