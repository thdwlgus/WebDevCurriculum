# Quest 07. node.js의 기초

## Introduction

- 이번 퀘스트에서는 node.js의 기본적인 구조와 개념에 대해 알아 보겠습니다.

## Topics

- node.js
- npm
- CommonJS와 ES Modules

## Resources

- [About node.js](https://nodejs.org/ko/about/)
- [Node.js의 아키텍쳐](https://edu.goorm.io/learn/lecture/557/%ED%95%9C-%EB%88%88%EC%97%90-%EB%81%9D%EB%82%B4%EB%8A%94-node-js/lesson/174356/node-js%EC%9D%98-%EC%95%84%ED%82%A4%ED%85%8D%EC%B3%90)
- [npm](https://docs.npmjs.com/about-npm)
- [npm CLI commands](https://docs.npmjs.com/cli/v7/commands)
- [npm - package.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-json)
- [How NodeJS Require works!](https://www.thirdrocktechkno.com/blog/how-nodejs-require-works)
- [MDN - JavaScript Modules](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Modules)
- [ES modules: A cartoon deep-dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)
- [require vs import](https://www.geeksforgeeks.org/difference-between-node-js-require-and-es6-import-and-export/)

## Checklist

- node.js는 무엇인가요? node.js의 내부는 어떻게 구성되어 있을까요?
  - JavaScript 언어로 동작하는(JavaScript 엔진 기반의) 웹어플리케이션 프레임워크
  - 가장 강력한 기능이자 특징 : **single thread, asynchronized pattern**
  - 전통적인 web 프레임워크에 비해 훨씬 간단하고 효율적인 방식, 다수의 request 처리가 가능, 빠른 응답 구현 가능
- npm이 무엇인가요? `package.json` 파일은 어떤 필드들로 구성되어 있나요?
  - node package module, 노드패키지의 관리에 중점을 둔 명령어
  - **package.json 파일 :** npm에서 사용되는 패키지 메타데이터를 담고 있는 파일
    - 루트 디렉토리에 위치하며, 해당 프로젝트의 이름, 버전, 의존성 패키지 정보 등 정의 가능
- npx는 어떤 명령인가요? npm 패키지를 `-g` 옵션을 통해 글로벌로 저장하는 것과 그렇지 않은 것은 어떻게 다른가요?
  - node pacakage execution, 노드패키지의 실행에 중점을 둔 명령어
  - npm의 영구적인 설치, 관리 등의 부가적인 절차없이 원하는 패키지를 npm 레지스트리에 접근시켜 실행만 할 수 있도록 설치하는 일종의 **실행도구**
  - 실행목적의 실행도구이기 때문에, 빠른 실행결과를 보고자 할때 별도의 패키지 업데이트나 관리할 필요없이 손쉬운 실행이 가능
  - **npm install -g `<package>`**
    - node package를 전역적으로 설치 -> PC내부에서의 프로젝트 전역적으로 참조할 수 있는 package가 설치
    - window의 경우 전역 node_modules directory에 설치
  - **npm install `<package>`**
    - package가 지역적으로 설치 -> 해당 프로젝트 내부에서만 사용 가능
    - 프로젝트 내부 디렉토리(지역적) node_modules에 설치, 실행파일 역시 지역적 디렉토리에 설치
- 자바스크립트 코드에서 다른 파일의 코드를 부르는 시도들은 지금까지 어떤 것이 있었을까요? CommonJS 대신 ES Modules가 등장한 이유는 무엇일까요?
  - **CommonJS**
    - Node.js에서 처음 등장한 모듈 시스템
    - require()와 module.exports를 사용하여 다른 파일에서 작성한 코드를 불러오거나 내보내는 방식으로 동작
    - 동기적인 방식으로 모듈을 로딩, 브라우저 환경에서 사용할 경우에는 번들러(bundler)를 사용하여 모듈을 묶어서 전달해야 하는 불편함 존재
  - **ES Modules**
    - ECMAScript 2015(ES6)에서 도입된 모듈 시스템
    - import와 export 구문을 사용하여 다른 파일에서 작성한 코드를 불러오거나 내보내는 방식으로 동작
    - 비동기적인 방식으로 모듈을 로딩하며, 브라우저 환경에서도 네이티브하게 지원하기 때문에 번들러 없이도 사용 가능
- ES Modules는 기존의 `require()`와 동작상에 어떤 차이가 있을까요? CommonJS는 할 수 있으나 ES Modules가 할 수 없는 일에는 어떤 것이 있을까요?
  1. 정적 분석 가능
  2. 기본적으로 비동기적 로딩
  3. 모듈 로딩 시점에서 모듈 복사본 만들어 사용
  4. import 구문에서 상대 경로나 절대 경로 사용 불가
- node.js에서 ES Modules를 사용하려면 어떻게 해야 할까요? ES Modules 기반의 코드에서 CommonJS 기반의 패키지를 불러오려면 어떻게 해야 할까요? 그 반대는 어떻게 될까요?
  - 파일 확장자를 .mjs로 사용하거나 package.json 파일의 "type" 필드를 "module"로 설정
  - ES Modules 기반의 코드에서 CommonJS 기반의 패키지를 불러오려면, require() 함수 대신 import 구문 사용
  - CommonJS 기반의 코드에서 ES Modules 기반의 패키지를 불러오려면, require() 함수 대신 import 구문 사용 불가
    - import() 함수를 사용하여 동적으로 모듈을 로딩

## Quest

- 스켈레톤 코드에는 다음과 같은 네 개의 패키지가 있으며, 용도는 다음과 같습니다:
  - `cjs-package`: CommonJS 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `esm-package`: ES Modules 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `cjs-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, CommonJS 기반의 프로젝트입니다.
  - `esm-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, ES Modules 기반의 프로젝트입니다.
- 각각의 패키지의 `package.json`과 `index.js` 또는 `index.mjs` 파일을 수정하여, 각각의 `*-my-project`들이 `*-package`에 노출된 함수와 클래스를 활용할 수 있도록 만들어 보세요.

## Advanced

- node.js 외의 자바스크립트 런타임에는 어떤 것이 있을까요?
