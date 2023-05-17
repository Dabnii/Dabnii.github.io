# <p align="center"> 🧢 React + Vscode

1. `code` > `Preference` > `Configure User Snippets`
   > `$1` 및 `$2`는 커서의 초기 위치와 이동 순서를 정의하는 플레이스홀더
2. 원하는 파일을 찾아 설정
   <img width="596" alt="스크린샷 2023-05-17 오후 2 45 03" src="https://github.com/Dabnii/petures/assets/110847597/76a7063c-da0b-4205-93ee-ca756b201351">

```jsx
//My snippets
//clg로 치기도 귀찮다!
{
  "Console log": {
    "prefix": "cl",
    "body": "console.log($1);"
    //expected console.log(📍)
    //📍 핀이 있는 곳으로 커서가 바로 이동한다. 굿
  },
  "div className": {
    "prefix": "div.",
    "body": "<div className='$1'>$2</div>"
  }
}
```
