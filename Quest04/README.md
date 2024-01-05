# Quest 04. OOP의 기본

## Introduction

- 이번 퀘스트에서는 바닐라 자바스크립트의 객체지향 프로그래밍에 대해 알아볼 예정입니다.

## Topics

- 객체지향 프로그래밍
  - 프로토타입 기반 객체지향 프로그래밍
  - 자바스크립트 클래스
    - 생성자
    - 멤버 함수
    - 멤버 변수
  - 정보의 은폐
  - 다형성
- 코드의 재사용

## Resources

- [MDN - Classes](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes)
- [MDN - Inheritance and the prototype chain](https://developer.mozilla.org/ko/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [MDN - Inheritance](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Inheritance)
- [Polymorphism](https://medium.com/@viktor.kukurba/object-oriented-programming-in-javascript-3-polymorphism-fb564c9f1ce8)
- [Class Composition](https://alligator.io/js/class-composition/)
- [Inheritance vs Composition](https://woowacourse.github.io/javable/post/2020-05-18-inheritance-vs-composition/)

## Checklist

- 객체지향 프로그래밍은 무엇일까요?
  - **객체지향 프로그래밍(Object-Oriented Programming, OOP) :** 컴퓨터 프로그래밍 패러다임 중 하나, 객체(Object)를 중심으로 프로그래밍 하는 방법
- `#`로 시작하는 프라이빗 필드는 왜 필요한 것일까요? 정보를 은폐(encapsulation)하면 어떤 장점이 있을까요?
  - **#로 시작하는 프라이빗 필드(Private Field) :** 해당 필드가 선언된 클래스 내부에서만 접근 가능하도록 제한하는 접근 제한자(Access Modifier).
  - 프라이빗 필드를 사용하여 **정보 은폐(encapsulation)** 구현 가능
  - **정보 은폐(encapsulation)**
    - 프라이빗 필드를 사용하여 해당 필드에 접근하는 메소드(Getter, Setter)를 제공하는 것이 대표적인 방법
    - 외부에서는 객체의 내부 상태를 변경할 수 없고, Getter를 통해 필요한 정보만 가져오기 가능
    - 객체의 불변성과 안정성을 보장, 객체의 내부 구현 방법 변경에 유연하게 대처 가능
    - 코드의 가독성과 유지보수성 향상 도움
- 다형성이란 무엇인가요? 다형성은 어떻게 코드 구조의 정리를 도와주나요?
  - 객체지향 프로그래밍의 개념 중 하나, 하나의 인터페이스나 클래스가 여러 개의 구현체를 가질 수 있는 성질 의미
  - 같은 인터페이스나 클래스를 사용하여 다양한 구현체를 다룰 수 있는 것
  - 코드의 재사용성과 유지보수성을 높이는 데 큰 도움 제공
  - **다형성 구현 방법**
    - **상속(Inheritance)** 과 **인터페이스(Interface)**
- 상속이란 무엇인가요? 상속을 할 때의 장점과 단점은 무엇인가요?
  - 객체지향 프로그래밍에서 기존 클래스를 확장하여 새로운 클래스를 생성하는 기법
  - 기존 클래스의 필드와 메소드를 재사용하여 새로운 클래스를 만들 수 있으며, 이를 통해 코드의 중복을 줄이고 코드의 재사용성 향상
  - **장점**
    1. 코드 재사용성 증가
    2. 기존 클래스 기능 확장, 수정 가능
    3. 클래스 간 계층 구조 구성, 객체 지향 프로그래밍 다형성 구현 가능
    4. 클랫 간 의존성 줄이기 가능
  - **단점**
    1. 클래스 간 결합도 증가로 인해 하위 클래스에서 상위 클래스의 변경사항에 민감해질 가능성 존재
    2. 하위 클래스에서 상위 클래스의 private 멤버 접근 불가
    3. 상위 클래스의 변경사항이 전체 시스템여 영향 미칠 가능성 존재
- OOP의 합성(Composition)이란 무엇인가요? 합성이 상속에 비해 가지는 장점은 무엇일까요?
  - 객체 지향 프로그래밍에서 하나의 클래스가 다른 클래스의 객체를 포함하여 기능을 구현하는 것
  - 클래스 간에 느슨한 결합도를 유지, 코드의 재사용성과 유지보수성 향상
- 자바스크립트의 클래스는 어떻게 정의할까요?
  - 클래스를 사용하면 객체의 속성과 메소드 정의, 이를 바탕으로 객체 생성 가능
  - 클래스를 사용하여 객체를 생성하려면 new 키워드 사용
  - 클래스의 상속은 extends 키워드 사용하여 정의
- 프로토타입 기반의 객체지향 프로그래밍은 무엇일까요?
  - 체지향 프로그래밍의 한 방식으로, 객체를 생성하는 기반이 프로토타입(Prototype) 기반
  - 객체를 생성하는 데 사용되는 원형(Prototype) 객체로, 다른 객체에게 상속 가능
- 자바스크립트의 클래스는 이전의 프로토타입 기반의 객체지향 구현과 어떤 관계를 가지고 있나요?
  - class가 없던 Javascript는 객체를 생성할 때 별도의 내부 생성자없이 바로 객체를 생성하였고, 이에 따른 속성이나 행동 값들을 부여
  - ES6이후 생긴 class에서는 constructor 생성자를 통해 정의해줄 수 있고, 외부 생성자인 new를 통해 class를 생성하거나 상속받기 가능

## Quest

- 웹 상에서 동작하는 간단한 바탕화면 시스템을 만들 예정입니다.
- 요구사항은 다음과 같습니다:
  - 아이콘은 폴더와 일반 아이콘, 두 가지의 종류가 있습니다.
  - 아이콘들을 드래그를 통해 움직일 수 있어야 합니다.
  - 폴더 아이콘은 더블클릭하면 해당 폴더가 창으로 열리며, 열린 폴더의 창 역시 드래그를 통해 움직일 수 있어야 합니다.
  - 바탕화면의 생성자를 통해 처음에 생겨날 아이콘과 폴더의 개수를 받을 수 있습니다.
  - 여러 개의 바탕화면을 각각 다른 DOM 엘리먼트에서 동시에 운영할 수 있습니다.
  - Drag & Drop API를 사용하지 말고, 실제 마우스 이벤트(mouseover, mousedown, mouseout 등)를 사용하여 구현해 보세요!

## Advanced

- 객체지향의 역사는 어떻게 될까요?
- Smalltalk, Java, Go, Kotlin 등의 언어들로 넘어오면서 객체지향 패러다임 측면에서 어떤 발전이 있었을까요?
