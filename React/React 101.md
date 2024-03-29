# <p align="center"> 🧢 React 101

## 🧢 React 정의

### 💡 UI를 만들기 위한 자바스크립트의 `라이브러리`

- ✨ `선언적 개발 환경`
- 자동 UI 업데이트
- `Virtual DOM 가상돔`
- ✨`Component(컴포넌트)` 기반 개발 환경
- 복잡한 UI를 효과적으로 구성가능
- `JSX 문법`으로 컴포넌트 작성의 편리

<br>

| 📝 절차적/명령적 (JavaScript)  | 🏆 선언적 (React)                                                  |
| ------------------------------ | ------------------------------------------------------------------ |
| 자바스크립트로 `직접 DOM 조작` | 1. 원하는 `결과를 선언` → 2.DOM조작(React 위임)                    |
| 어떻게 도달하는지에 초점       | `최종적 결과 고려` 필요 <br> DOM을 절차적으로 선언하는 개발과 상이 |

e.g. 📝 `절차적/명령적` :

- 이 방향으로 직진해서 두 번째 블록에서 우회전해주시고, [...] 소방서가 있는 블록에서 우회전 후 300m 앞에서 내려주세요.

e.g. 🏆 `선언적` :

- 선언적 : OOO으로 가주세요

<hr>
<br>

## 📌 Virtual DOM

1. 목적

   - 전체적인 프로세스 개선 및 성능저하 방지
   - DOM요소에 변화를 주기 전, 내부적으로 가상 DOM을 이용해 `실제 DOM에 일어날 변화 계산`

2. 진행 순서

   - 기존 웹화면의 업데이트 방식:
     1. DOM요소에 변화가 생기면 다시 렌더트리 (DOM 트리 + CSSOM 트리)
     2. 레이아웃 위치 계산 (layout)
     3. 화면에 그리는 (Paint)

- 이전 UI 상태를 메모리에 유지하는 가상 DOM사용
  - UI의 최소집합 계산
  - DOM 처리 횟수를 최소화
  - 효율성 극대화 👏

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20%EB%93%B1%EC%9E%A5%EB%B0%B0%EA%B2%BD.md"> 이전글: React의 등장 배경 & Library</a>

<a href="https://github.com/Dabnii/Dabnii.github.io/blob/main/React/React%20component.md"> 다음글: React 컴포넌트</a>

<hr>
<p align="center"> E.O.D
