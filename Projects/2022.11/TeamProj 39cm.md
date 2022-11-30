# <p align="center">🛍️ 39cm

<P align="center">📆 2022.11.14~25

<br>

<img src="https://user-images.githubusercontent.com/110847597/204074927-6682e061-9a54-44bd-ae1a-a86b5b980afe.gif" width="1000px">

<br>

## 🏆 39cm Goal

- 큐레이팅 아이템, 당신의 하이엔드 클로젯
- 네이티브 리뷰 사진 강조하여 구매 증대를 목표

## 📼 DEMO

- <a href="https://www.youtube.com/watch?v=uIBfznhRL5o">📎 시연 영상</a>


## 👩‍👩‍👧‍👦 39cm 팀

- `BE` 이동근, 한상엽 / `FE` 김동기, 심동섭, 이다빈

## 📌 39cm Features

- 🟢 `동근 BE` - DB구축, 회원가입, 로그인, 찜하기, 마이페이지 유저정보
- 🟢 `상엽 BE` - DB구축, 상품리스트 조회, 장바구니, 결제
- 🔵 `동기 FE` - 베스트 상품 페이지 리스트, 마이페이지
- 🔵 `동섭 FE` - 장바구니, 결제페이지, 회원가입, 로그인, 메인
- 🔵 `다빈 FE` - 제품 상세 페이지, 네비게이션, 네비게이션 검색 바, 메인 페이지

## 🛠 39cm Tools

- `Notion`, `Trello`, `Git-book`, `Table plus`, `Git`, `Slack`

## 🛠 39cm Engineering Stack

- 💻 BE:
  - `JavaScript`, `Node.js`, `AWS`, `MySql`
- 💻 FE:
  - `JavaScript`, `React`, `SCSS`

## 👩‍💻 DB Modeling

![39cm DB modeling](https://user-images.githubusercontent.com/110847597/203906351-09a7dd29-fc7f-4959-a0d7-83225021cbbb.png)


## 🚀 구현 기능

1. 로그인, 회원가입 기능 구현
1. 장바구니, 바로구매 기능
1. 필터 & 검색 기능 
1. 마이페이지
1. 상품 디테일 페이지 🙋‍♀️
1. 리뷰, 좋아요 기능 🙋‍♀️
1. 메인 페이지 🙋‍♀️

## 🥳 나의 제작파트

1. Nav & Main
    <img src="https://user-images.githubusercontent.com/110847597/204074927-6682e061-9a54-44bd-ae1a-a86b5b980afe.gif" width="1000px">

2. Nav search
  ![search-gif](https://user-images.githubusercontent.com/110847597/204092994-329bcc28-8516-4a46-a492-7543c028bf7b.gif)

3. Product detail page
  ![detailPageOpt](https://user-images.githubusercontent.com/110847597/204094096-115bca16-c02e-47d0-a6d7-3592681c69d2.gif)
  ![detailpage](https://user-images.githubusercontent.com/110847597/204095154-891e2359-04cd-4e8d-8402-5741b0094114.gif)



### 💪 위의 파트를 담당하게 된 이유:

- 평소에 관심있던 Nav 파트를 진행하며 `map()`과 드롭다운 기능을 구현
- 제품 상세페이지 (product detail)를 진행할 때 캐러셀이미지, 상품 선택 옵션 구현
- 구매 유도를 위하여 리뷰 사진 이미지를 강조 UI로 변경


### 👀 나를 성장하게 한 코드 들여다보기 

  ### `fetch`
  - 💭 `fetch`로 목데이터를 들고와서 읽는 순간 오류가 발생한다

    ```JSON
    //product.json
    {
      "productName": " 숏다운 (3color)",
      "description": "포근하고 헤어리한 터치감의 우먼스 집업 가디건, YKK 투웨이 지퍼 사용",
      "price": 297000,
      "category": "상의",
      "likesNumber": "likesNumber",
      "images": [
        ".../.../png"
        ".../.../png"
        ".../.../png"
      ],
      "reviews": [
        {
          "reviewTitle": "제목",
          "reviewContent": "첫번째 리뷰의 내용입니다.",
          "reviewImage": "./.../jpg",
          "rating": "rating",
          "reviewUser": "@1234KIM"
        }
      ]
    }
    ```

  - 📌 객체로 된 데이터라 때문에 조건부 실행을 원한다면 아래의 코드로 적어야한다.
      ```jsx
      //productdetail.js
      {pdData[0] !== null && ()}
      ```
    - 배열은 `true`/`false` 값으로 들어온다
    - 객체는 `undefined`로 들어온다
    - `{pdData[0] && }`로 사용하면 오류가 발생한다.
    - 어떠한 객체를 받아오는지, 비동기 언어의 특성을 파악하지 못하면 초보적인 실수가 반복된다.
      - 시간을 효율적으로 쓰지 못하는 치명적인 단점
    - 실제로 많은 동기들이 나와같은 현상을 겪었기에 누군가에게 도움이 되길 바란다!
 
 ### `fetch` & `useEffect`
 - 이번 프로젝트를 하면서 가장 혼란스럽고 중요했던 부분입니다.
    ```jsx
      useEffect(() => {
      //통신용입니다
      // fetch(`https://reqres.in/api/users/${productId}`)
      fetch("/data/product.json")
        .then((response) => response.json())
        .then((data) => setPdData(data));
    }, []);
    ```
    - 위의 데이터는 상품에 대한 정보이기 때문에 마운트가 될 때 필요합니다.
    - 의존성 배열을 넣어 최초 마운트 시 데이터를 가져오도록 했습니다.
    - 특정 이벤트에서만 `fetch`를 진행하고 싶다면 함수로 선언한 후 이벤트에 넣어 사용합니다.<br>
  
    ```jsx
    //productdetail.js
    useEffect(() => {
        const ipAddress = "%ip%";

      //통신용입니다
      fetch(`http://${ipAddress}:3000/products/${productId}`, {
        headers: {
          productId: productId,
        },
      })
        .then((response) => response.json())
        .then((data) => {
          console.log(data);
          setPdData(data.product[0]);
        });

      fetch(`http://${ipAddress}:3000/likes/product/${productId}`, {
        headers: {
          authorization: localStorage.getItem("TOKEN"),
        },
      })
        .then((response) => response.json())
        .then((result) => {
          console.log(result.isLiked);
          setLikePd(result.isLiked);
      });
    }, [productId]);
    ```    
<br>

## 📝 회고:

👍 잘한 점
- 개발자의 소통방식을 배웠다
- 플래닝 미팅, 데일리 스탠드 업, 회고 미팅을 통한 일정 관리를 루틴으로 만들었다.
   <img src="https://user-images.githubusercontent.com/110847597/202833938-368cc3fb-9907-459f-a5dd-21a1cfa70300.png">
  - 매일 오전 아침 15분 내외로 짧은 데일리 미팅을 진행하고 매일 기록했다.
  - 불필요한 의사소통이 줄고 방향성을 확립하는데 많은 도움을 받았다.
  - 단순히 일정을 체크하고 작업 진행률을 묻는 것이 아닌 `어떠한 기능을 구현하기 위하여 각자의 리소스와 역량, 한계를 가졌는지 나눠보는 시간` 이었다.
  - 물론 일정 소통과 블락커 해소도 중요한 부분 중 하나이다.
- 👍 개발 일지, Notion, 트렐로를 사용하여 일정과 회의를 문서화하여 서로 헤매는 부분이 적었다.
  - 문서화, 정리된 글은 서로의 `신뢰도` 그리고 함께 한다는 `협력감`도 생기게 해주었다.
- 바쁜 와중에도 팀원들이 적극적으로 프로젝트에 대하여 의논하고 협업했다.

💪 아쉬운 점
- 기획에서 서비스의 차별점을 구현하지 못한 게 아쉽다.
- 구매에 많은 영향을 미치는 리뷰 기능을 개선하여 구매자의 리뷰 사진을 강조할 수 있는 리뷰 UI로 개선하여 매출 증대로 연결 짓고 싶었다.
- 사전에 더 꼼꼼히 고려했다면 프론트 & 백엔드 팀과 싱크가 맞아 진행했을 수도 있다고 생각한다.
- 위의 과정을 결과로 다음 프로젝트에서는 우선 순위와 필요한 기능에 대하여 확립하고 진행할 것이다.
- 컴포넌트 분리 및 가독성 좋은 코드를 쓰지 못한 점도 아쉽다.

🌳 다음 프로젝트 각오: 
- 초석을 잘 다지는 것처럼, 작업할 때에 컴포넌트를 계획하고 분리 할 것입니다.
- 한 줄을 쓰더라도 가독성에 집중할 것이다.
- 다시 한번, 아는 만큼 쓸 수 있는 코드!
- 주말 동안 부족했던 부분을 더 공부하고 다음 프로젝트에 임할 예정!
- 39cm팀 고생 많았습니다! 🙇‍♀️
 
---
<p align="center"> E.O.D 
