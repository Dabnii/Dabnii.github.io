# <p align="center"> 🌐 HTTP

## 💡 HTTP는 웹서비스 핵심 `프로토콜`

1.  HTTP의 특징인 `Stateless`를 설명할 수 있다.
    - HyperText Transger Protocol
      - How to we communicate?
      - HTML (Hyper Text Markup language)
    - 문서와 문서가 링크로 연결되어 있음을 뜻함
    - Transfer
      - HTML로 만든 웹페이지 문서 (파일)ㅇㄹ 보낸다
    - `Protocol` 약속 🤙
      - 컴퓨터끼리 어떻게 HTML을 주고 받을지 정함
2.  📢 Request, Response 구조에 대해 설명할 수 있다.

    - 📱 🌐 💻

      - Request 🔁 Responsive: 소통의 핵심은 `소통` 과 `응답`

    - `Stateless`
      - State(상태) + less(없음)
        - 기억력이 없다로 말할 수 있음
        - e.g. 카페의 직원이 매번 바뀌고 주문이 원활하게 안되는 상황
      - 매 통신마다 필요한 모든 정보를 담아서 요청을 전송
      - 로그인 토큰 또는 브라우저의 쿠키, 세션, 로컬스토리지 같은 기술이 필요
    - HTTP 개별통신은 모두 `독립`
      - HTTP와의 통신을 기억하지 않습니다.
      - 매 통신마다 사전에 필요한 모든 정보를 담아서 요청을 보내야만 합니다.
    - `토근`

- HTTP 메시지 구조
  - Start Line : 글의 head
    - HTTP Method | Request target | HTTP version
      - POST / login HTTP/ 1.1
      - Version ✨
  - Headers :
    - 요청의 메타데이터를 담고 있는 부분
    - {Key : value}의 형태
  - Body :
    - 요청의 실제 내용
      - body{ ”username” : “wecode” }
- HTTP Response
  - `Status line`
    - 응답의 상태
    1. **HTTP Version**: 요청의 **HTTP버전**과 동일
    2. **Status Code**: 응답 메세지의 **상태 코드**
    3. **Status Text**: 응답 메세지의 상태를 간략하게 설명해주는 **텍스트**
  - Headers :
    - 요청의 헤더와 동일
    - 응답의 추가 정보(메타 데이터)를 담고있는 부분
    - 응답에서만 사용되는 헤더의 정보들이 있습니다. (ex. 요청하는 브라우저의 정보가 담긴 User-Agent 대신, Server 헤더가 사용)
  - Body :
    - 요청의 Body와 일반적으로 동일
    - 요청의 메소드에 따라 Body가 항상 존재하지 않듯이 응답도 응답의 형태에 따라 데이터를 전송할 필요가 없는 경우엔 Body가 없을 수도 있습니다.
    - 가장 많이 사용되는 Body 의 데이터 타입은 **[JSON(JavaScript Object Notation)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/JSON)** 입니다.
    - **로그인 요청에 대해 성공했을 때 응답의 내용**

1. HTTP request method의 종류와 차이점

   - `GET` | 장바구니에 담은 제품을 조회

     - 데이터를 받아오기만 할 때 사용
     - 웹페이지에 접속해서 필요한 데이터를 불러올 때 사용

     ```jsx
     // (축약된 요청 메세지)
     GET /shop/bag HTTP/1.1
     Headers: {
         "HOST": "https://www.apple.com/kr",
         "Authroization": "kldiduajsadm@9df0asmzm" (유저가 본인임을 증명할 수 있는 인증/인가 토큰)
     }

     // (축약된 응답 메시지)
     HTTP/1.1 200 OK
     Body: {
         "message": "SUCCESS",
         "carts": [
             {
               "productId": 10
               "name": "Pro Display XDR - Nano-texture 글래스"
               "price": "₩7,899,000"
               "quantity": 1
            },
            {
              "productId": 20
              "name": "Mac Pro"
              "price": "₩73,376,000"
              "quantity": 2
            }
         ]
     }
     ```

   - `POST` | 장바구니에 맘에 드는 상품을 담는다

     - 데이터를 생성 | 수정할 때
     - 데이터를 생성 빛 수정 할 때 많이 사용 되기 때문에 대부분의 경우 요청에 body가 포함되서 보내집니다

     ```jsx
     POST /shop/bag HTTP/1.1
     Headers: {
       "HOST":
       "https://www.apple.com/kr"
       "Authroization":
       "kldiduajsadm@9df0asmzm" (유저가 본인임을 증명할 수 있는 인증/인가 토큰)
     }
     Body: {
       product: {
         "productId": 30
         "name": "12.9형 iPad Pro Wi-Fi + Cellular 128GB"
         "color": "스페이스 그레이"
         "price": "₩1,499,000"
         "quantity": 1
       }
     }

     // (축약된 응답 메시지)
     HTTP/1.1 201 Created
     Body: {
       "message": "SUCCESSFULLY CARTS UPDATED"
     ```

   - `DELETE` | 장바구니에서 제품을 삭제한다

     - 특정 데이터를 서버에서 삭제 요청을 보낼 때 쓰는 메소드 입니다.

     ```jsx
     // (축약된 요청 메세지)
     DELETE /shop/bag HTTP/1.1
     Headers: {
       "HOST": "https://www.apple.com/kr"
       "Authroization": "kldiduajsadm@9df0asmzm" (유저가 본인임을 증명할 수 있는 인증/인가 토큰)
     }
     Body: {
       productId: 30
     }

     // (축약된 응답 메시지)
     HTTP/1.1 204 No Content
     ```

# 2. 대표적인 Status code의 종류

## Response Status Code

💡실제 프로젝트를 진행할 때 가장 많이 보게 될 응답의 상태 코드 들입니다.<br> Status Code의 숫자에 각각 의미가 내포되어 있습니다.<br> Status Code 만 보아도 응답이 제대로 됐는지 안 됐는지를 파악할 수 있습니다.<br>

## 1. Success

### `1-1. 200: OK`

- 가장 자주 보게되는 Status Code
- 문제없이 요청에 대한 처리가 백엔드 서버에서 이루어지고 나서 오는 응답코드입니다.

### `1-2. 201: Created`

- 무언가가 잘 생성되었을 때에(Successfully Created) 오는 Status Code
- 대게 POST 메소드의 요청에 따라 백엔드 서버에 데이터가 잘 생성 또는 수정 되었을 때에 보내는 코드입니다.

### `1-3. 204: No Content`

- 요청이 성공했으며 제공할 응답메세지가 없을 경우 사용하는 Status Code
- 주로 DELETE 메소드의 요청으로 성공적으로 삭제되어서 응답으로 제공할 컨텐츠가 없을 때 사용된다.

## `2. Client Error`

### `2-1. 400: Bad Request`

- 해당 요청이 잘못되었을 때 보내는 Status Code
- 주로 요청의 Body에 보내는 내용이 잘못되었을 때 사용되는 코드입니다.
- ex) 전화번호를 보내야 하는데 숫자가 아닌 문자열의 주소가 대신 Body에 담겼을 경우

### `2-2. 401: Unauthorized`

- 유저가 해당 요청을 진행하려면 먼저 로그인을 하거나 회원가입이 필요하다는 의미를 나타내는 Status Code
- ex) wish list, 좋아요 기능은 회원이 아니면 요청을 보낼 수 없습니다.

### `2-3. 403: Forbidden`

- 유저가 해당 요청에 대한 권한이 없다는 의미를 나타내는 Status Code
- 접근 불가능한 정보에 접근했을 경우를 의미합니다.
- ex) 오직 유료회원만 접근할 수 있는 데이터를 요청 했을 때

### `2-4. 404: Not Found`

- 요청된 URI 가 존재하지 않는다는 의미를 나타내는 Status Code

## `3. Server Error`

### `3-1. 500: Internal Server Error` 🥲

---
