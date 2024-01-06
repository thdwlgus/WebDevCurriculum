# Quest 05. OOP 특훈

## Introduction

- 이번 퀘스트에서는 바닐라 자바스크립트의 객체지향 프로그래밍을 조금 더 훈련해 보겠습니다.

## Topics

- Separation of Concerns
- 객체지향의 설계 원칙
  - SOLID 원칙
- Local Storage

## Resources

- [Separation of concerns](https://jonbellah.com/articles/separation-of-concerns/)
- [SOLID](https://en.wikipedia.org/wiki/SOLID)
- [객체지향 설계 5원칙](https://webdoli.tistory.com/210)
- [MDN - Local Storage](https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage)

## Checklist

- 관심사의 분리 원칙이란 무엇인가요? 웹에서는 이러한 원칙이 어떻게 적용되나요?
  - **관심사의 분리(Separation of Concerns) 원칙**
    - 소프트웨어 공학에서 사용되는 개념, 시스템을 작은 단위로 분할하여 각 단위가 서로 다른 관심사를 처리하도록 하는 디자인 원칙
    - 각 단위는 다른 단위와 독립적으로 존재, 변경이 발생할 때 다른 단위에 영향을 미치지 않도록 구현
  - **Model-View-Controller(MVC)** 패턴과 같은 디자인 패턴을 사용하여 관심사의 분리 적용
  - 코드의 유지 보수성과 확장성을 향상시키는 데 큰 역할 기여
- 객체지향의 SOLID 원칙이란 무엇인가요? 이 원칙을 구체적인 예를 들어 설명할 수 있나요?
  - 객체지향 프로그래밍에서 유지보수 가능하고 확장 가능한 소프트웨어를 설계하기 위한 원칙의 앞 글자를 따서 만들어진 약어
    - **단일 책임 원칙 (Single Responsibility Principle, SRP) :** 하나의 책임만 가져야 한다는 것을 의미
    - **개방-폐쇄 원칙 (Open-Closed Principle, OCP) :** 소프트웨어 엔티티(클래스, 모듈, 함수 등)는 확장에는 열려 있어야 하고 변경에는 닫혀 있어야 한다는 것을 의미
    - **리스코프 치환 원칙 (Liskov Substitution Principle, LSP) :** 서브 타입은 언제나 자신의 기반 타입으로 대체할 수 있어야 한다는 것을 의미
    - **인터페이스 분리 원칙 (Interface Segregation Principle, ISP) :** 클라이언트는 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안 된다는 것을 의미
    - **의존 역전 원칙 (Dependency Inversion Principle, DIP) :** 추상화된 것은 구체적인 것에 의존하면 안 된다는 것을 의미
- 로컬 스토리지란 무엇인가요? 로컬 스토리지의 내용을 개발자 도구를 이용해 확인하려면 어떻게 해야 할까요?
  - 웹 브라우저에 저장되는 클라이언트 사이드 데이터 저장소
  - 브라우저를 닫거나 페이지를 새로 고침해도 데이터 유지

## Quest

- 외부 라이브러리나 프레임워크를 사용하지 않고, 자바스크립트를 이용하여 간단한 웹브라우저 기반의 텍스트 에디터를 만들어 보겠습니다.
  - 기본적으로 VSCode와 같이 탭을 이용해 여러 개의 파일을 동시에 편집할 수 있습니다.
  - 탭을 눌러 열려 있는 다른 파일을 편집할 수 있으며 탭을 언제든지 닫을 수 있습니다.
  - VSCode와 같이 새 파일, 로드, 저장, 다른 이름으로 저장 등의 기능을 가집니다. 저장은 웹 브라우저의 로컬 스토리지를 이용합니다.
  - VSCode와 같이 탭이 수정되었는데 저장되기 이전일 경우 이를 알려주는 인디케이터가 작동합니다.
  - 같은 이름의 파일을 저장할 경우 에러를 표시해야 합니다.
- 이번 퀘스트의 결과물은 앞으로의 많은 퀘스트에서 재사용되게 되니, 주의깊게 코드를 작성해 보세요!

## Advanced

- 웹 프론트엔드 개발에서 이러한 방식의 패턴을 더 일반화해서 정리할 수 있을까요? 이 퀘스트에서 각각의 클래스들이 공통적으로 수행하게 되는 일들에는 무엇이 있을까요?
