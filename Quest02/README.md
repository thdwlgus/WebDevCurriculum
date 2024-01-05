# Quest 02. CSS의 기초와 응용

## Introduction

- CSS는 Cascading StyleSheet의 약자입니다. 웹브라우저에 표시되는 HTML 문서의 스타일을 지정하는 (거의) 유일하지만 다루기 쉽지 않은 언어입니다. 이번 퀘스트를 통해 CSS의 기초적인 레이아웃 작성법을 알아볼 예정입니다.

## Topics

- CSS의 기초 문법과 적용 방법
  - Inline, `<style>`, `<link rel="stylesheet" href="...">`
- CSS 규칙의 우선순위
- 박스 모델과 레이아웃 요소
  - 박스 모델: `width`, `height`, `margin`, `padding`, `border`, `box-sizing`
  - `position`, `left`, `top`, `display`
  - CSS Flexbox와 Grid
- CSS 표준의 역사
- 브라우저별 Developer tools

## Resources

- [MDN - CSS](https://developer.mozilla.org/ko/docs/Web/CSS)
- [Centering in CSS: A Complete Guide](https://css-tricks.com/centering-css-complete-guide/)
- [A complete guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [그리드 레이아웃과 다른 레이아웃 방법과의 관계](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Grid_Layout/%EA%B7%B8%EB%A6%AC%EB%93%9C_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83%EA%B3%BC_%EB%8B%A4%EB%A5%B8_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83_%EB%B0%A9%EB%B2%95%EA%B3%BC%EC%9D%98_%EA%B4%80%EA%B3%84)

## Checklist

- CSS를 HTML에 적용하는 세 가지 방법은 무엇일까요?
  - **내부스타일 시트 :** HTML 문서의 `<head>` 태그 내부에서 `<style>` 태그를 사용하여 CSS 코드 작성 가능 -> 한 문서 내에서 스타일 적용시 유용
  - **외부스타일 시트 :** HTML 문서와 별도로 CSS 파일 작성, HTML 문서에서 CSS 파일 참조 -> 여러 문서에서 동일한 스타일 적용시 유용
  - **인라인 스타일 :** HTML 요소의 `<style>` 속성을 사용하여 CSS 코드 작성 -> 특정 요소에만 스타일 적용시 유용
- 세 가지 방법 각각의 장단점은 무엇일까요?
  - **내부스타일 시트**
    - **장점 :** 한 문서 내에서 스타일 적용 편리, 스타일 시트가 HTML 파일에 내장되어 있기 때문에 파일 다운로드 하는 시간 감소, 성능 향상
    - **단점 :** 여러 문서에서 동일한 스타일 적용시, 모든 문서에 동일한 내부 스타일 시트 작성해야하기 때문에 유지보수 어려움, 스타일시트 HTML 파일 내부에 있기 때문에, HTML 코드와 혼재하여 가독성 하락
  - **인라인 스타일**
    - **장점 :** 특정 요소에만 스타일 적용 가능, HTML 태그 안에서 스타일 작성, CSS 파일 별도 로드 불필요
    - **단점 :** 여러 요소에 동일한 스타일 적용시, 모든 요소에 인라인 스타일 작성해야하기 때문에 유지보수 어려움, HTML 코드와 스타일이 혼재하여 가독성 하락, 인라인 스탕리 사용시 스타일 내용과 분리되지 않기 때문
- CSS 규칙의 우선순위는 어떻게 결정될까요?
  1. **중요도(Importance) :** !important 규칙이 적용된 스타일은 다른 모든 스타일보다 우선
  2. **명시도(Specificity) :** 스타일 규칙이 구체적일수록 우선순위 상위
  3. **선언 순서(Declaration Order) :** 동일한 우선순위를 가지는 스타일 규칙일 경우, 나중에 작성된 규칙이 우선순위 상위
- CSS의 박스모델은 무엇일까요? 박스가 화면에서 차지하는 크기는 어떻게 결정될까요?
  - **콘텐츠(Content) :** 텍스트, 이미지 등의 실제 콘텐츠가 들어가는 영역
  - **패딩(Padding) :** 콘텐츠와 테두리(border) 사이의 여백
  - **테두리(Border) :** 박스의 경계선
  - **마진(Margin) :** 박스와 주변 요소 간의 여백
- `float` 속성은 왜 좋지 않을까요?
  - 레이아웃 깨짐
  - 반응형 디자인 어려움
  - 접근성 문제
  - 코드의 복잡성 증가
- Flexbox(Flexible box)와 CSS Grid의 차이와 장단점은 무엇일까요?
  - **Flexbox :** 1차원적인 레이아웃 다루는데 사용, 주로 요소를 수평 또는 수직 축을 기준으로 배치할 때 사용
    - **장점**
      1. 간단 레이아웃 만들 때 유용
      2. 좋은 브라우저 호환성
      3. 유연한 레이아웃 조정
    - **단점**
      1. 복잡한 레이아웃에 미적합
      2. 다루기 어려운 다차원 레이아웃
      3. 일부 속성의 동작이 예상과 다를 가능성
  - **CSS Grid :** 2차원적인 레이아웃 다루는 데 사용, 행과 열 모두 사용하여 레이아웃 조정 가능
    - **장점**
      1. 다양한 레이아웃 생성 가능
      2. 레이아웃 쉽게 변경 가능
      3. 다루기 쉬운 다차원 레이아웃
    - **단점**
      1. 좋지 않은 브라우저 호환성
      2. 초기 설정 복잡 가능성
      3. Flexbox에 비해 학습곡선 상위
- CSS의 비슷한 요소들을 어떤 식으로 정리할 수 있을까요?
  - **Display 속성**
    - block : 블록 레벨 요소
    - inline : 인라인 요소
    - inline-block : 인라인 블록 요소
    - none: 화면에서 숨기는 요소
  - **Position 속성**
    - static : 기본값으로, 위치 지정 없이 요소 배치
    - relative : 요소를 이동시키면서 원래 위치를 기준으로 배치
    - absolute : 가장 가까운 조상 요소를 기준으로 위치 지정
    - fixed : 뷰포트를 기준으로 위치 고정
    - sticky : 스크롤 위치에 따라 동적으로 상대적인 위치 지정
  - **Box Model 속성**
    - margin : 요소의 외부 여백 지정
    - padding : 요소의 내부 여백 지정
    - border : 요소의 테두리 지정
  - **Text 속성**
    - color : 글자 색상 지정
    - font-size : 글자 크기 지정
    - font-family : 글꼴 지정
  - **Flexbox 속성**
    - display : flex; 요소를 플렉스 컨테이너로 생성
    - flex-direction : 플렉스 아이템의 배치 방향 지정
    - justify-content : 플렉스 아이템 수평 정렬
    - align-items : 플렉스 아이템 수직 정렬
  - **Grid 속성**
    - display : grid; 요소를 그리드 컨테이너로 생성
    - grid-template-rows : 그리드 행의 크기 지정
    - grid-template-columns : 그리드 열의 크기 지정
    - grid-gap : 그리드 아이템 사이의 간격 지정

## Quest

- Quest 01에서 만들었던 HTML을 바탕으로, [이 그림](screen.png)의 레이아웃과 CSS를 최대한 비슷하게 흉내내 보세요. 꼭 완벽히 정확할 필요는 없으나 align 등의 속성은 일치해야 합니다.
- **주의사항: 되도록이면 원래 페이지의 CSS를 참고하지 말고 아무것도 없는 백지에서 시작해 보도록 노력해 보세요!**

## Advanced

- 왜 CSS는 어려울까요?
- CSS의 어려움을 극복하기 위해 어떤 방법들이 제시되고 나왔을까요?
- CSS가 브라우저에 의해 해석되고 적용되기까지 내부적으로 어떤 과정을 거칠까요?
- 웹 폰트의 경우에는 브라우저 엔진 별로 어떤 과정을 통해 렌더링 될까요?
