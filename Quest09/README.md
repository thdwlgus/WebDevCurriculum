# Quest 09. 서버와 클라이언트의 대화

## Introduction

- 이번 퀘스트에서는 서버와 클라이언트의 연동, 그리고 웹 API의 설계 방법론 중 하나인 REST에 대해 알아보겠습니다.

## Topics

- expressJS, fastify
- AJAX, `XMLHttpRequest`, `fetch()`
- REST, CRUD
- CORS

## Resources

- [Express Framework](http://expressjs.com/)
- [Fastify Framework](https://www.fastify.io/)
- [MDN - Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [MDN - XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
- [REST API Tutorial](https://restfulapi.net/)
- [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete)
- [MDN - CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

## Checklist

- 비동기 프로그래밍이란 무엇인가요?
  - 프로그램의 실행 흐름과 관련된 개념으로, 여러 작업이 동시에 실행되도록 하고 작업 완료 시 결과를 처리하는 방식
- 콜백을 통해 비동기적 작업을 할 때의 불편한 점은 무엇인가요? 콜백지옥이란 무엇인가요?
  - **콜백 지옥(callback hell)**
    - 콜백 함수를 중첩해서 사용하는 코드가 복잡해져서 가독성이 떨어지고 유지보수가 어려워지는 현상
- 자바스크립트의 Promise는 어떤 객체이고 어떤 일을 하나요?
  - 비동기적인 작업을 처리하고 그 결과를 반환하기 위한 객체
  - 비동기 작업이 완료되면 성공 결과나 실패 결과를 처리하기 위한 메서드를 제공
  - 콜백 함수를 중첩하지 않고 비동기적인 작업을 처리할 수 있어 코드의 가독성이 향상
    - **대기(pending) :** Promise 객체가 생성되고 비동기 작업이 수행 중인 상태
    - **이행(fulfilled) :** 비동기 작업이 성공적으로 완료된 상태
    - **거부(rejected) :** 비동기 작업이 실패한 상태
- 자바스크립트의 `async`와 `await` 키워드는 어떤 역할을 하며 그 정체는 무엇일까요?
  - ES2017(ES8)에서 추가된 자바스크립트의 키워드로, 비동기 처리를 좀 더 간결하게 작성 가능
  - **async 키워드**
    - 함수 선언 앞에 붙이며, 이를 통해 해당 함수가 비동기적으로 처리됨 표시
    - 내부에서 Promise 객체를 반환
  - **await 키워드**
    - 함수 내부에서 사용되며, Promise 객체의 결과값을 기다린 후에 다음 코드를 실행
    - 콜백이나 Promise 체이닝을 사용하지 않고도 비동기 코드를 동기적으로 작성 가능
- 브라우저 내 스크립트에서 외부 리소스를 가져오려면 어떻게 해야 할까요?
  - **XMLHttpRequest 객체**나 **fetch API**를 사용 가능
  - 비동기적으로 데이터를 가져오는 기능을 제공
  - **XMLHttpRequest 객체**
    - 콜백 함수를 사용하여 비동기적으로 처리
  - **fetch API**
    - Promise 기반으로 비동기 처리
- 브라우저의 `XMLHttpRequest` 객체는 무엇이고 어떻게 동작하나요?
  - 브라우저에서 제공하는 네트워크 통신을 위한 JavaScript 객체
  - **open(method, url[, async[, user[, password]]])**
    - 요청의 준비를 위해 초기화
    - **method :** HTTP 요청 방식(GET, POST 등)
    - **url :** 요청을 보낼 URL을 지정
    - **async :** 비동기 여부
    - **user와 password :** 인증을 위한 사용자 이름과 암호를 지정
  - **send([body])**
    - 요청을 서버로 전송
    - **body :** 요청 본문을 지정하는데 사용
  - **abort()**
    - 요청을 취소
  - **setRequestHeader(name, value)**
    - HTTP 요청 헤더를 설정
    - **name :** 헤더 이름
    - **value :** 헤더 값
  - **onreadystatechange**
    - 요청 상태가 변경될 때 호출되는 콜백 함수
    - 요청 상태가 변경될 때마다 호출
    - eadyState와 status 속성을 사용하여 응답 상태를 확인 가능
  - **readyState**
    - 요청 상태를 나타내는 속성
    - 0부터 4까지의 값이 존재, 상태 변경 이벤트마다 값을 갱신
  - **status**
    - 서버로부터 받은 HTTP 응답 상태 코드를 나타내는 속성
- `fetch` API는 무엇이고 어떻게 동작하나요?
  - 브라우저 내장 API로서, 네트워크를 통해 리소스를 가져오거나 전송하기 위해 사용
  - API를 사용하면 AJAX 요청을 보내고, JSON 데이터를 가져오거나 파일 업로드 등 가능
  - XMLHttpRequest 객체를 대체할 수 있는 비동기적인 HTTP 요청 처리 API로, 프로미스(Promise)를 기반으로 동작
    - 비동기적인 처리를 더욱 쉽게 다룰 수 있게 해주는 장점
- REST는 무엇인가요?
  - 웹 기반 애플리케이션에서 자주 사용되는 아키텍처 스타일
  - 클라이언트와 서버 간의 통신 방식, 네트워크 상에서 분산되어 있는 리소스들을 표현하고 상호작용하는 데에 적합
- REST API는 어떤 목적을 달성하기 위해 나왔고 어떤 장점을 가지고 있나요?
  - 자원을 CRUD(Create, Read, Update, Delete) 기능을 통해 관리할 수 있으며, HTTP 메서드(GET, POST, PUT, DELETE)를 사용하여 이를 구현
  - 플랫폼과 언어에 독립적
  - 서로 다른 플랫폼이나 언어 간의 통신이 가능하며, 이는 웹 서비스의 확장성과 유연성 증가
  - 캐싱을 지원하기 때문에 서버의 부하를 줄이고 성능을 향상
- RESTful한 API 설계의 단점은 무엇인가요?
  - 복잡성
  - 캐싱
  - 보안
  - 서버 부하
  - 문서화
- CORS란 무엇인가요? 이러한 기능이 왜 필요할까요? CORS는 어떻게 구현될까요?
  - 웹 브라우저에서 실행되는 스크립트에서 다른 출처(origin)의 리소스에 접근할 때 발생하는 보안 정책
  - 서버가 특정 출처의 리소스에 대한 요청을 허용
  - 서버에서 응답 헤더를 이용해 구현
  - 요청의 종류(GET, POST 등)와 같은 다른 정보도 함께 검사

## Quest

- 이번 퀘스트는 Midterm에 해당하는 과제입니다. 분량이 제법 많으니 한 번 기능별로 세부 일정을 정해 보고, 과제 완수 후에 그 일정이 얼마나 지켜졌는지 스스로 한 번 돌아보세요.
  - 이번 퀘스트부터는 skeleton을 제공하지 않습니다!
- Quest 05에서 만든 메모장 시스템을 서버와 연동하는 어플리케이션으로 만들어 보겠습니다.
  - 클라이언트는 `fetch` API를 통해 서버와 통신합니다.
  - 서버는 8000번 포트에 REST API를 엔드포인트로 제공하여, 클라이언트의 요청에 응답합니다.
  - 클라이언트로부터 온 새 파일 저장, 삭제, 다른 이름으로 저장 등의 요청을 받아 서버의 로컬 파일시스템을 통해 저장되어야 합니다.
    - 서버에 어떤 식으로 저장하는 것이 좋을까요?
  - API 서버 외에, 클라이언트를 띄우기 위한 서버가 3000번 포트로 따로 떠서 API 서버와 서로 통신할 수 있어야 합니다.
  - Express나 Fastify 등의 프레임워크를 사용해도 무방합니다.
- 클라이언트 프로젝트와 서버 프로젝트 모두 `npm i`만으로 디펜던시를 설치하고 바로 실행될 수 있게 제출되어야 합니다.
- 이번 퀘스트부터는 앞의 퀘스트의 결과물에 의존적인 경우가 많습니다. 제출 폴더를 직접 만들어 제출해 보세요!

## Advanced

- `fetch` API는 구현할 수 없지만 `XMLHttpRequest`로는 구현할 수 있는 기능이 있을까요?
- REST 이전에는 HTTP API에 어떤 패러다임들이 있었을까요? REST의 대안으로는 어떤 것들이 제시되고 있을까요?
