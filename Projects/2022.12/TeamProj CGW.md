# <p align="center">🎫 CGW

<p align="center"> 📆 2022.11.28~ 12.9

<br>
<br>
<br>
  
<img width="1386px" alt="CGW main" align="center" src="https://user-images.githubusercontent.com/110847597/206863973-b5dc727d-037f-4ce5-9c9e-feb21622a4bc.gif"/>

<br>

## 🏆 CGW Goal

- 예매 그 정도, CGW
- 사용자를 위한 더 간편한 예약 페이지
  - 가독성을 높인 UI
  - 지도 API 가까운 영화관 안내
  - 소셜로그인, 소셜 결제를 활용한 구매 허들 낮추기

## 📼 DEMO

- <a href="https://vimeo.com/779910229">📎 시연 영상</a>

## 🙎‍♀️ Team CGW

`FE` 곽종범, 박지영, 이다빈, 이혜원 <br>
`BE` 김한솔, 임창현, 조상원

## 📌 CGW Features

- 🔵 `종범 FE` - 좌석 선택
- 🔵 `지영 FE` - 소셜 로그인& 지도 API Map 기능
- 🔵 `다빈 FE` - 영화 예매, 영화 검색 🙋‍♀️
- 🔵 `혜원 FE` - 결제, 예매내역
- 🟢 `한솔 BE` - 예매페이지 API, AWS
- 🟢 `창현 BE` - 카카오결제 API, 주문 API
- 🟢 `상원 BE` - 카카오로그인 API, 예매페이지 API

## 🛠 CGW Tools

- `Notion`, `Trello`, `Git`, `Slack`

## 🛠 CGW Engineering Stack

- 💻 BE:
  - `JavaScript`, `Node.js`, `AWS`, `MySql`
- 💻 FE:
  - `JavaScript`, `React`, `Styled-components`

## 👩‍💻 DB Modeling

<img width="1386" alt="CGW DB" src="https://user-images.githubusercontent.com/110847597/206862017-45340383-0d5d-49d2-aa46-4f8ff1ccf7e7.png">

## 🚀 구현 기능

1. 영화 예매, 영화 검색 🙋‍♀️
1. 좌석 선택
1. 소셜 로그인& 지도 API Map 기능
1. 카카오톡 결제, 예매내역

## 🥳 나의 제작파트

1. 🎫 영화 예매
   <img width="1386px" alt="CGW booking" align="center" src="https://user-images.githubusercontent.com/110847597/206864130-ba3268d0-ecb7-4c0d-b7da-67458f466509.gif"/>

   - 다시 고르기 기능
     <img width="1386px" alt="CGW booking-reselect" align="center" src="https://user-images.githubusercontent.com/110847597/206864567-cb62ee6c-833f-4cfb-a941-952b3b510d83.gif"/>

1. 🔍 영화 검색

  <img width="1386px" alt="CGW Searching" align="center" src="https://user-images.githubusercontent.com/110847597/206864375-e94a542a-10e7-485e-b58a-c16370670830.gif"/>

### 💪 위의 파트를 담당하게 된 이유

1. 밀집도가 높고, 작은 UI를 개선 하여 `예매율 상승` 목적
1. 브랜드 컬러를 사용한 브랜딩을 통한 `긍정적인 서비스 경험`
1. 영화 검색 기능 추가로 쉬운 영화 서치 및 `이탈율 감소`
1. 어렵고, 복잡한 기능을 구현하고 싶은 열정이 있었기에 도전하였습니다.

### 👀 나를 성장하게 한 코드 들여다보기

### 📍 `Nesting Map`

```javascript
{movieData?.map((movie, index) => (
    <PlacePickTextSeoul key={index}>
        <PlaceTextBox key={movie.region_id}>
        <PlacePickP>📍{movie.name}</PlacePickP>
        </PlaceTextBox>
        <PlacePickButtonContainer>
        <Pick>
        {movie.location.map(lo => {
        return (
            <>
            <Input
                type="radio"
                name="place"
                id={lo.branch_id}
                defaultValue={lo.branch_name}
                onChange={onChangeData}
            />
            <Label htmlFor={lo.branch_id}>{lo.branch_name}</Label>
            </>
        );
})}

```

- 중첩 map을 사용하여 버튼을 바르게 렌더했다.
- 수정 과정
  - Mock data의 구조를 바꾸어 렌더
  - 중첩 맵을 활용하여 객체안의 객체 데이터 (branch)를 렌더
  - 데이터가 가진 지점의 데이터는 1개이지만, UI는 2개 이기에 지점이 두 번 렌더 됨

💪 Before

<img width="1038" alt="IssueBefore" align="center" src="https://user-images.githubusercontent.com/110847597/206710723-c5c147ad-9d9d-460a-8850-247fa312cf07.png"/>

👍 After (내가 원했던 렌더 모습)

<img width="1038" alt="IssueAfter" align="center" src="https://user-images.githubusercontent.com/110847597/206710812-c12b221e-7e7e-4cd1-a04e-97b4b07ae650.png">

### 🫂 중첩 삼항연산자

  <img width="1386px" alt="CGW nesting map" align="center" src="https://user-images.githubusercontent.com/110847597/206713220-7804ec0d-dda7-48b9-9008-b75311ba419a.gif"/>

> Step 3 문구를 주목!

- 첫번째 삼항 연산자
  - 조건: `영화관`이 선택 되었다면
  - `true`일 때 해당 일자에 대한 영화 시간을 UI로 그려내고
    - ✨ `true` 이지만, 해당 영화 시간이 없다면 `영화가 매진 되었습니다` 라는 문구를 띄운다
  - `false`라면 `영화를 먼저 선택해 주세요!`라는 문구를 띄운다
    - 이러한 방법을 채택한 이유 <a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/Projects/2022.12/Dec1stWeek.md#-%EC%82%BC%ED%95%AD%EC%97%B0%EC%82%B0%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%ED%99%94%EB%A9%B4-ui-%EB%B3%80%EA%B2%BD">📎 빈칸은 오류로 보인다! 12/2</a>
      - 실제 영화 사이트 처럼 영화, 시간, 일자를 누를 때 마다 유연하게 데이터를 처리하면 좋겠지만, 난이도가 높아서 UI를 순차적으로 그려주는 것으로 진행했다.
      - 난이도 조절과 유저에게 우리가 원하는 flow로 진행 할 수 있어서 꽤 뿌듯하다.
  - 👏 사실 위의 기능을 뇌로는 이해했지만, 코드로 구현하지 못해서 답답한 부분이 있었다.
  - 하나씩 뜯어보고, 동기에게 많은 도움을 얻어 성공했다! 👇

```jsx
<TimePickContainer>
  {day ? (
    <TimePick>
      {timeFilter.length !== 0 ? (
        timeFilter.map((movieTime, i) => {
          return (
            <React.Fragment key={i}>
              {timeFilter[i].time.map((detailTime, index) => {
                return (
                  <React.Fragment key={index}>
                    <TimeRadio
                      type="radio"
                      name="time"
                      id={detailTime.time}
                      defaultValue={detailTime.time}
                      onChange={onChangeData}
                    />
                    <TimeLabel htmlFor={detailTime.time}>
                      {detailTime.time}
                    </TimeLabel>
                  </React.Fragment>
                );
              })}
            </React.Fragment>
          );
        })
      ) : (
        <TimePickReadyBox>
          <TimePickReady>🥲 매진 되었어요!</TimePickReady>
        </TimePickReadyBox>
      )}
    </TimePick>
  ) : (
    <TimePickReadyBox>
      <TimePickReady>📆 날짜를 먼저 정해주세요!</TimePickReady>
    </TimePickReadyBox>
  )}
</TimePickContainer>
```

- 영화시간이 없을 경우의 코드를 알럿으로 띄울 수 있었지만, 중첩 삼항 연산자를 사용하여 더 적은 코드로 메세지를 렌더링 했음!
- 하나의 함수 안에 처리해야할 데이터나 함수가 있다면 느리게 처리된다.
- `fetch`가 진행하는 비동기적 특성을 주말에 공부!
  - 자바스크립트는 동기적 언어이다
  - 브라우저 엔진에서 작동 할 때는 비동기적으로 처리 된다.

### 📍 초기화 버튼 기능 수정

```jsx
//after
const deleteObj = () => {
  setSelectList({ place: "", day: "", time: "" });
};

//before
const deleteObj = () => {
  delete selectList.place;
  delete selectList.day;
  delete selectList.time;
};
```

- 🔍 `delete` 메소드는 `Key` & `Value`를 지운다. == null
- 그러하여 after 코드로 리팩토링
- 잘 짜여진 코드는 물 흐르듯 기존 기능들과 잘 작동한다
  - 리팩토링 한 코드는 초기값(true)으로 돌아가기에 uesEffect를 사용 할 필요도 없다!

## 📝 회고:

- 😍 좋았던 것(`L`iked)
  - 든든한 동기들과 함께 작성하는 코드
  - 어렵지만 1차 프로젝트 때 보다 심화 된 레벨의 프로젝트 (필터링& 동적라우팅)
  - 매일 아침 정각, 팀원들이 미리 작성한 스탠드업 템플릿을 기반으로 데일리 스탠드업을 진행 한 것
  - 애자일 개발을 위한 트렐로 사용 및 활용
  - 꾸준한 기록을 통해 어제는 이해하지 못했던 코드를 오늘은 작성해보고 이해하는 개발자가 되었다.
  - 끊임 없는 도전
  - 에러창 만나고 스스로 해결 하기
- 📚 배운 것(`L`earned)
  - 많이 넘어지고 에러창을 만나고 해결하면서 성장했다.
  - 코드 리팩토링을 통하여 더 좋은 코드는 수정이 되어도 물 흐르듯이 자연스럽게 작동하는 것
- 💦 부족했던 것(`L`acked)
  - 에러 대처법이 아직 미숙하고, console.log를 활용한 디버깅 숙련도가 낮음
  - 돌발 상황(e.g. 전달해야할 데이터 타입이 바뀌어야한다거나 또는 그 반대의 경우)에서 블락커를 많이 만났다.
  - 예를 들면, 내가 데이터 타입을 정체하는데 많은 리소스가 들고 비효율 적이라는 판단이 내려진다면, 백엔드에 데이터 변경을 요청해도 된다는 점
  - 외부 라이브러리를 완벽하게 핸들링 못한 점.
  - 처음이고, 기획 단계에서 완벽하다 생각한 부분에서도 변수가 늘 생겼기에 수시로 논의해보고 변수에 흔들리지 않는 마음가짐
    - > 제가 어렵다고 생각하는 부분은 모두가 어려운 것이 맞고, 고민이 깊어질 때면 팀원이든 멘토님과 의견을 나눠보는것도 방법이라는 것을 배웠습니다. 이건 여러분과 공유하면 좋을 것 같아 작성합니다..
      > 즉 혼자 깊게 고민하고 앓지 말기! 12/7 스탠드업 미팅 -나-
- 🕯 바라는 것(`L`onged for)
  - 기존 사이트의 복잡한 UI를 개선하여 사용자에게 예매를 직관화 하여 예매를 쉽게 하는 것
  - 처음부터 완벽한 코드를 작성하는것에 열중하지 말 것, 나도 모르게 주는 스트레스가 되어 의욕이 떨어질 수 있음!

🌳 앞으로의 목표

- 백엔드와 통신을 위하여 `ERD` 작성법과 읽는 법 학습!
  - 초기 기획단계에서 데이터 송수신 방식을 더 꼼꼼히 기획
    - e.g. 언제 어느 데이터를 주고 받고, 어떠한 데이터 타입으로 전달 받을지

<br>

---

### Reference

이 프로젝트는 CGV를 참조하여 학습목적으로 만들었습니다. 실무수준의 프로젝트이지만 학습용으로 만들었기 때문에 이 코드를 활용하여 이득을 취하거나 무단 배포할 경우 법적으로 문제될 수 있습니다.

---

<p align="center"> E.O.D
