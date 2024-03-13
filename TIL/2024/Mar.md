## <p align="center">📆3/6</p>

#### build 이후에 함수 실행하기

- 비동기 작업이 필요할 때
- 프레임이 다 그려진 후 특정 처리를 하고 싶을 때
- 나는 렌더가 끝난 후, 그려진 해당 widget의 너비를 구하고자 사용했음

```dart
class _MyHomePageState extends State<MyHomePage> {
  @override
  void initState() {
    super.initState();

    WidgetsBinding.instance.addPostFrameCallback((_) async {
      //something
      _getWidth()
    });
  }
```

#### key의 currentContext 너비 얻기

```dart
  double? _getWidth() {
    if (_key.currentContext != null) {
      final RenderBox renderBox = _key.currentContext!.findRenderObject() as RenderBox;
      double width = renderBox.size.width;
      return width;
    }
    return null;
  }
```

- [addPostFrameCallback](https://api.flutter.dev/flutter/scheduler/SchedulerBinding/addPostFrameCallback.html)

#### 오랜만에 돌아온 python

```python
from requests import Response, get

results = {}

websites = (
    'google.com',
    'airbnb.com',
    'https://twitter.com',
    'facebook.com',
)

for website in websites:
  if not website.startswith('https://'):
    website = f"https://{website}"
  response = get(website)
  if response.status_code == 200:
    results[website] = 'ok'
  else:
    results[website] = 'failed'

print(results)
# 어째 많이 본 코드다
# {'https://google.com': 'ok', 'https://airbnb.com': 'failed', 'https://twitter.com': 'failed', 'https://facebook.com': 'ok'}
```

## <p align="center">📆3/8</p>

- `homebrew 설치`

```zsh
==> Next steps:
- Run these two commands in your terminal to add Homebrew to your PATH:
    (echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/user/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
- Run brew help to get started
- Further documentation:
    https://docs.brew.sh
```

- 무슨 말 인가 했더니..
- 터미널에 순서대로 넣어주면 되는 것이다.

```zsh
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/user/.zprofile
```

```zsh
eval "$(/opt/homebrew/bin/brew shellenv)"
```

## <p align="center">📆3/9</p>

### Node.js로 백엔드 해보기

```javascript
const express = require("express");
const app = express();
let posts = [];

app.use(express.json());

app.use(express.urlencoded({ extended: true }));

app.get("/", (req, res) => {
  res.json(posts);
});

app.post("/posts", (req, res) => {
  console.log(typeof req.body);
  const { title, name, text } = req.body;
  posts.push({ id: posts.length + 1, title, name, text, createdDt: Date() });
  res.json({ title, name, text });
  console.log(req.body);
});

app.delete("/posts/:id", (req, res) => {
  const id = req.params.id;
  const filteredPosts = posts.filter((post) => post.id !== +id);
  const isLengthChanged = posts.length !== filteredPosts.length;
  posts = filteredPosts;

  if (isLengthChanged) {
    res.json("OK");
    return;
  }
  res.json("NOT CHANGED");
});

app.listen(3000, () => {
  console.log("welcome board START!");
});
```

1. `node fileName.js`으로 실행한다
1. `Command + F5 (debug mode)` 시ㄹ행
1. `express` 터미널로 확인 (아래처럼!)

```shell
$ curl -X POST -H "Content-Type: application/x-www-fo
rm-urlencoded" -d "title=SUNDAY1&name=LEE&text=good morning" http://localhost:3000/posts

{"title":"SUNDAY1","name":"LEE","text":"good morning"}%
```

```json
[
  {
    "id": 1,
    "title": "SUNDAY1",
    "name": "LEE",
    "text": "good morning",
    "createdDt": "Sat Mar 09 2024 23:35:13 GMT+0900 (Korean Standard Time)"
  }
]
```

## <p align="center">📆3/13</p>

- 오늘의

```javascript
const axios = require("axios");

async function getTop20Movies() {
  const url =
    "http://raw.githubusercontent.com/wapj/jsbackend/main/movieinfo.json";
  try {
    const result = await axios.get(url);
    const { data } = result;
    if (!data.articleList || data.articleList.size == 0) {
      throw new Error("no data");
    }
    const movieInfos = data.articleList.map((article, ind) => {
      return { title: article.title, rank: ind + 1 };
    });

    for (let movieInfo of movieInfos) {
      console.log(`[${movieInfo.rank}위] ${movieInfo.title}`);
    }
  } catch (err) {
    throw new Error(err);
  }
}

getTop20Movies();

// [1위] 처음부터 잘했으면 얼마나 좋니
// [2위] <본즈 앤 올> 궁지로 내몰린 10대를 보는 시선
// [3위] 경이로운 생生의 의지로 창조해낸 ‘페르시아어’
// [4위] 뻔하지 않은 사랑 영화
// [5위] 우린 아무것도 모른다, 틀렸다는것만 증명할 뿐…에올
// [6위] [영화리뷰] <더 메뉴>를 보고
// [7위] 진실한 삶의 태도를 제시하다
// [8위] 중요한 건 꺾이지 않는 마음
// [9위] 치즈버거 세트의 행복
// [10위] 즐기거나 놀리거나,
// [11위] [영화감상]오늘 밤, 세계에서 이 사랑이 사라진다 해도
// [12위] 아들을 구하고 싶다면 달려라
// [13위] 인생은 아름다워(2022)
// [14위] 영화 <사도>, 죽음의 문턱에 와서야 닿는 마음에 대해
// [15위] 스타워즈: 안도르
// [16위] 죽음의 문턱에서 거짓말로 살아남은 자의 고백
// [17위] 닫힌 마음 - 영화 '체리향기'
// [18위] <오늘 밤, 세계에서 이 사랑이 사라진다 해도> 리뷰
// [19위] <더 메뉴> 180만 원짜리 먹으러 와서 사레 걸린기분
// [20위] 닭장을 나온 백호
```
