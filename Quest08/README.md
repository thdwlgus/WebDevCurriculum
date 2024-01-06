# Quest 08. 웹 API의 기초

## Introduction

- 이번 퀘스트에서는 웹 API 서버의 기초를 알아보겠습니다.

## Topics

- HTTP Method
- node.js `http` module
  - `req`와 `res` 객체

## Resources

- [MDN - Content-Type Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)
- [MDN - HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
- [MDN - MIME Type](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type)
- [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop)
- [HTTP Node.js Manual & Documentation](https://nodejs.org/api/http.html)

## Checklist

- HTTP의 GET과 POST 메소드는 어떻게 다른가요?
  - 데이터 전송 방식
  - **GET**
    - 데이터를 검색하는 데 사용
    - URL 뒤에 쿼리 문자열을 추가하여 데이터를 전송 -> 쿼리 문자열은 서버로 전송되고, 서버는 이를 읽어 데이터를 검색
    - 주로 정적 데이터를 요청하는 데 사용
    - 브라우저의 주소 표시줄에서 직접 호출
  - **POST**
    - 데이터를 전송하는 데 사용
    - HTTP 본문을 통해 데이터를 전송 -> URL에 노출되지 않음
    - 주로 로그인, 회원가입, 글쓰기 등과 같은 데이터를 전송해야 하는 경우에 사용
    - 브라우저 캐시에 저장되지 않으며, 보안상의 이유로 요청이 브라우저에 저장되지 않음
    - 데이터가 HTTP 본문에 포함되어 있으므로, URL에 노출되지 않음
- 다른 HTTP 메소드에는 무엇이 있나요?
  - **HEAD :** GET과 비슷하지만, 서버에서 응답 바디를 제외한 헤더만 전송
  - **PUT :** 지정된 URI에 새로운 리소스 저장
  - **DELETE :** 지정된 URI의 리소스 삭제
  - **PATCH :** 지정된 URI의 일부 수정
  - **OPTIONS :** 지정된 URI가 지원하는 메소드 목록 검색
  - **CONNECT :** 대상 리소스로의 네트워크 연결 설정
  - **TRACE :** 클라이언트의 요청 메시지를 그대로 서버로 전송, 서버에서는 응답 메시지를 그대로 클라이언트로 전송. 이를 통해 클라이언트와 서버 간의 통신 디버깅 가능
- HTTP 서버에 GET과 POST를 통해 데이터를 보내려면 어떻게 해야 하나요?
  - GET 요청 보내기
  - POST 요청 보내기
- HTTP 요청의 `Content-Type` 헤더는 무엇인가요?
  - 다양한 **MIME 타입**을 지원
    - **text/plain :** 일반 텍스트 형식
    - **text/html :** HTML 문서 형식
    - **application/json :** JSON 데이터 형식
    - **application/xml :** XML 문서 형식
    - **multipart/form-data :** 파일 업로드 형식
- Postman에서 POST 요청을 보내는 여러 가지 방법(`form-data`, `x-www-form-urlencoded`, `raw`, `binary`) 각각은 어떤 용도를 가지고 있나요?
  - **form-data**
    - HTTP 요청의 본문을 key-value 형태로 전송
    - 파일 업로드나 멀티파트(form-data) 요청을 보낼 때 사용
  - **x-www-form-urlencoded**
    - HTTP 요청의 본문을 key=value 형태로 전송
    - 폼 데이터를 전송할 때 사용
  - **raw**
    - HTTP 요청의 본문을 문자열로 전송
    - 요청 바디가 JSON, XML, HTML 등의 형식을 갖는 경우 사용
  - **binary**
    - HTTP 요청의 본문을 이진 데이터(binary data)로 전송
    - 이미지나 동영상 등의 바이너리 데이터를 전송할 때 사용
- node.js의 `http` 모듈을 통해 HTTP 요청을 처리할 때,
  `req`와 `res` 객체에는 어떤 정보가 담겨있을까요?
  - 각각 요청과 응답에 대한 정보
  - **req 객체**
    - **req.url :** 요청된 URL 정보
    - **req.method :** 요청된 HTTP 메서드 정보 (GET, POST, PUT, DELETE 등)
    - **req.headers :** 요청 헤더 정보 -** req.body :** 요청 바디 정보 (POST, PUT 등의 요청에서만 존재)
  - **res 객체**
    - **res.statusCode :** 응답 상태 코드 (200, 404, 500 등)
    - **res.setHeader() :** 응답 헤더 설정 함수
    - **res.write() :** 응답 바디 데이터 전송 함수
    - **res.end() :** 응답 종료 함수
- GET과 POST에 대한 처리 형태가 달라지는 이유는 무엇인가요?
  - 각각의 HTTP 메서드가 요청하는 데이터의 형태와 전송 방식이 다르기 때문
  - **GET 요청 :** 일반적으로 URL을 통해 데이터를 전송
  - **POST 요청 :** 요청 바디에 데이터를 담아 전송
- 만약 API 엔드포인트(URL)가 아주 많다고 한다면, HTTP POST 요청의 `Content-Type` 헤더에 따라 다른 방식으로 동작하는 서버를 어떻게 정리하면 좋을까요?
  1.  **라우팅을 사용하여 구분 :** API 엔드포인트를 구분하기 위해 라우팅을 사용
  2.  **미들웨어를 사용하여 처리 :** 미들웨어는 요청과 응답의 중간에 위치하여 요청 처리 과정에서 추가적인 로직을 수행하는 것으
  3.  **컨트롤러를 사용하여 분리 :** 컨트롤러는 요청 처리 로직을 구현하는 것
- 그 밖에 서버가 요청들에 따라 공통적으로 처리하는 일에는 무엇이 있을까요? 이를 어떻게 정리하면 좋을까요?
  1. **요청 로깅 :** 서버에서 발생하는 모든 요청들을 로깅하여 추적
  2. **에러 처리 :** 서버에서 발생하는 모든 에러들을 처리하고, 에러가 발생할 경우 적절한 HTTP 응답 코드를 반환
  3. **인증 및 권한 관리 :** 인증 및 권한 관리를 통해 요청한 클라이언트가 유효한지 확인하고, 적절한 권한이 있는지를 판단
  4. **요청 파싱 및 검증 :** 요청 바디에서 필요한 데이터를 추출하고, 데이터의 유효성을 검증
  5. **응답 포맷팅 :** 클라이언트가 요청한 데이터를 적절한 포맷으로 응답

## Quest

- 다음의 동작을 하는 서버를 만들어 보세요.
  - 브라우저의 주소창에 `http://localhost:8080`을 치면 `Hello World!`를 응답하여 브라우저에 출력합니다.
  - 서버의 `/foo` URL에 `bar` 변수로 임의의 문자열을 GET 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/foo` URL에 `bar` 키에 임의의 문자열 값을 갖는 JSON 객체를 POST 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/pic/upload` URL에 그림 파일을 POST 하면 서버에 보안상 적절한 방법으로 파일이 업로드 됩니다.
  - 서버의 `/pic/show` URL을 GET 하면 브라우저에 위에 업로드한 그림이 뜹니다.
  - 서버의 `/pic/download` URL을 GET 하면 브라우저에 위에 업로드한 그림이 `pic.jpg`라는 이름으로 다운로드 됩니다.
- expressJS와 같은 외부 프레임워크를 사용하지 않고, node.js의 기본 모듈만을 사용해서 만들어 보세요.
- 처리하는 요청의 종류에 따라 공통적으로 나타나는 코드를 정리해 보세요.

## Advanced

- 서버가 파일 업로드를 지원할 때 보안상 주의할 점에는 무엇이 있을까요?
