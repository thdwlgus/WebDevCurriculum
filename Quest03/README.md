# Quest 03. 자바스크립트와 DOM

## Introduction

- 자바스크립트는 현재 웹 생태계의 근간인 프로그래밍 언어입니다. 이번 퀘스트에서는 자바스크립트의 기본적인 문법과, 자바스크립트를 통해 브라우저의 실제 DOM 노드를 조작하는 법에 대하여 알아볼 예정입니다.

## Topics

- 자바스크립트의 역사
- 기본 자바스크립트 문법
- DOM API
  - `document` 객체
  - `document.getElementById()`, `document.querySelector()`, `document.querySelectorAll()` 함수들
  - 기타 DOM 조작을 위한 함수와 속성들
- 변수의 스코프
  - `var`, `let`, `const`

## Resources

- [자바스크립트 첫걸음](https://developer.mozilla.org/ko/docs/Learn/JavaScript/First_steps)
- [자바스크립트 구성요소](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Building_blocks)
- [Just JavaScript](https://justjavascript.com/)

## Checklist

- 자바스크립트는 버전별로 어떻게 변화하고 발전해 왔을까요?
  - 초기부터 현재까지 지속적으로 발전
  - 이전 버전들에 새로운 기능이 추가, 기존 기능이 개선되면서 현재의 모습으로 생성
- 자바스크립트의 버전들을 가리키는 ES5, ES6, ES2016, ES2017 등은 무엇을 이야기할까요?
  - **ECMAScript**의 버전을 가리키는 용어
  - **ECMAScript :** 자바스크립트를 포함하는 스크립트 언어의 규격을 정의하는 표준화 기구
    - **ES5 :** 2009년에 발표된 ECMAScript 5 버전
    - **ES6 :** 2015년에 발표된 ECMAScript 6 버전
    - **ES2016, ES2017 :** ES6 이후의 버전을 가리키는 용어
- 자바스크립트의 표준은 어떻게 제정될까요?
  - **ECMA International**에서 제정
  - **ECMA International**
    - 정보통신 기술 표준을 제정하는 비영리 표준화 기구
    - ECMAScript라는 이름으로 자바스크립트 언어의 표준 규격을 제정
    - 자바스크립트 언어의 표준화를 총괄적으로 담당, 새로운 기능을 제안, 기존 기능의 수정/개선에 대한 의견을 제시
    - 표준화 과정에서는 다양한 이해관계자들의 의견을 수렴, 이를 바탕으로 규격 개정
- 자바스크립트의 문법은 다른 언어들과 비교해 어떤 특징이 있을까요?
  - 동적 타입 지정 언어
  - 프로토타입 기반 객체 지향 언어
  - 함수가 일급 객체
  - 콜백 함수
  - 간결한 문법
  - 느슨한 문법 규칙
- 자바스크립트에서 반복문을 돌리는 방법은 어떤 것들이 있을까요?
  - for 문
  - while 문
  - do-while 문
  - for...in 문
  - for...of 문
- 자바스크립트를 통해 DOM 객체에 CSS Class를 주거나 없애려면 어떻게 해야 하나요?
  - **CSS Class 추가하기 :** DOM 객체에 CSS Class를 추가하려면 classList.add() 메서드 사용
  - **CSS Class 제거하기 :** DOM 객체에서 CSS Class를 제거하려면 classList.remove() 메서드 사용
  - **CSS Class 토글하기 :** DOM 객체에서 CSS Class를 토글(추가/제거)하려면 classList.toggle() 메서드 사용
  - **CSS Class 존재 여부 확인하기 :** DOM 객체에 특정 CSS Class가 존재하는지 여부를 확인하려면 classList.contains() 메서드 사용
- IE9나 그 이전의 옛날 브라우저들에서는 어떻게 해야 하나요?
  - **classList** 속성이 지원되지 않으므로 다른 방법을 사용
    - **CSS Class 추가하기 :** DOM 객체에 CSS Class를 추가하려면 className 속성 사용
    - **CSS Class 제거하기 :** DOM 객체에서 CSS Class를 제거하려면 className 속성 사용
    - **CSS Class 토글하기 :** DOM 객체에서 CSS Class를 토글하려면 className 속성 사용
    - **CSS Class 존재 여부 확인하기 :** DOM 객체에 특정 CSS Class가 존재하는지 여부를 확인하려면 className 속성 사용
- 자바스크립트의 변수가 유효한 범위는 어떻게 결정되나요?
  - **전역 범위(Global Scope) :** 전역 범위에서 선언된 변수는 어느 곳에서나 접근 가능, 변수 선언시 var 키워드 사용
  - **지역 범위(Local Scope) :** 지역 범위에서 선언된 변수는 해당 지역 내에서만 접근 가능, 변수 선언시 let, const 키워드 사용
  - **블록 범위(Block Scope) :** ES6에서는 let 키워드나 const 키워드를 사용하여 블록 범위의 변수 선언, 선언 변수는 해당 블록 내부에서만 접근 가능
- `var`과 `let`으로 변수를 정의하는 방법들은 어떻게 다르게 동작하나요?
  - **변수의 유효 범위(scope) :** var로 선언된 변수는 함수 범위(Function Scope) 보유, let으로 선언된 변수는 블록 범위(Block Scope) 보유. 함수 범위는 해당 함수 내에서만 유효한 범위, 블록 범위는 해당 블록 내에서만 유효한 범위
  - **변수의 호이스팅(Hoisting) :** var로 선언된 변수는 함수, 전역 범위에서 변수 선언 코드 이전에도 변수 사용 가능. 하지만 선언과 초기화가 분리되어 있을 때 변수의 값은 undefined. let으로 선언된 변수는 호이스팅 미발생
  - **변수의 중복 선언 :** var로 선언된 변수는 같은 이름의 변수를 여러 번 선언해도 오류 미발생. 하지만 let으로 선언된 변수는 같은 이름의 변수를 중복 선언시 오류 발생
- 자바스크립트의 익명 함수는 무엇인가요?
  - 이름이 없는 함수를 의미
  - 함수 표현식을 사용하여 함수를 정의하고 변수에 할당할 때 함수 이름을 지정하지 않는 것
- 자바스크립트의 Arrow function은 무엇일까요?
  - 함수 표현식의 간단한 문법적 변로, 함수를 정의하는 또 다른 방법
  - ES6(ES2015)에서부터 도입

## Quest

- (Quest 03-1) 초보 프로그래머의 영원한 친구, 별찍기 프로그램입니다.
  - [이 그림](jsStars.png)과 같이, 입력한 숫자만큼 삼각형 모양으로 콘솔에 별을 그리는 퀘스트 입니다.
    - 줄 수를 입력받고 그 줄 수만큼 별을 그리면 됩니다. 위의 그림은 5를 입력받았을 때의 결과입니다.
  - `if`와 `for`와 `function`을 다양하게 써서 프로그래밍 하면 더 좋은 코드가 나올 수 있을까요?
  - 입력은 `prompt()` 함수를 통해 받을 수 있습니다.
  - 출력은 `console.log()` 함수를 통해 할 수 있습니다.
- (Quest 03-2) skeleton 디렉토리에 주어진 HTML을 조작하는 스크립트를 완성해 보세요.
  - 첫째 줄에 있는 사각형의 박스들을 클릭할 때마다 배경색이 노란색↔흰색으로 토글되어야 합니다.
  - 둘째 줄에 있는 사각형의 박스들을 클릭할 때마다 `enabled`라는 이름의 CSS Class가 클릭된 DOM 노드에 추가되거나 제거되어야 합니다.
- 구현에는 여러 가지 방법이 있으나, 다른 곳은 건드리지 않고 TODO 부분만 고치는 방향으로 하시는 것을 권장해 드립니다.

## Advanced

- Quest 03-1의 코드를 더 구조화하고, 중복을 제거하고, 각각의 코드 블록이 한 가지 일을 전문적으로 잘하게 하려면 어떻게 해야 할까요?
- Quest 03-2의 스켈레톤 코드에서 `let` 대신 `var`로 바뀐다면 어떤 식으로 구현할 수 있을까요?
