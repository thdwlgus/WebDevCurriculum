# Quest 13. 웹 API의 응용과 GraphQL

## Introduction

- 이번 퀘스트에서는 차세대 웹 API의 대세로 각광받고 있는 GraphQL에 대해 알아보겠습니다.

## Topics

- GraphQL
  - Schema
  - Resolver
  - DataLoader
- Apollo

## Resources

- [GraphQL](https://graphql.org/)
- [GraphQL.js](http://graphql.org/graphql-js/)
- [DataLoader](https://github.com/facebook/dataloader)
- [Apollo](https://www.apollographql.com/)

## Checklist

- GraphQL API는 무엇인가요? REST의 어떤 단점을 보완해 주나요?
  - **GraphQL API :** 데이터 쿼리 및 조작을 위한 새로운 방식을 제공하는 웹 API
  - **첫째,** REST API에서는 여러 요청을 보내야 하는 경우가 많아 비효율적
  - **둘째,** REST API에서는 데이터가 계층적으로 구성되어 있을 때 중첩된 요청 전송
- GraphQL 스키마는 어떤 역할을 하며 어떤 식으로 정의되나요?
  - **스키마 :** GraphQL API의 계약에 대한 명확한 정의를 제공
  - 클라이언트는 스키마를 기반으로 어떤 데이터를 요청할 수 있는지, 그리고 서버가 어떤 데이터를 반환할 수 있는지 미리 알기 가능
  - **SDL (Schema Definition Language)** 라는 언어를 사용하여 정의
    - **타입 정의 부분 :** 데이터 모델 정의
      - 객체 타입, 인터페이스 타입, 스칼라 타입, 열거형 타입 등을 정의
    - **루트 타입 정의 :** API 에서 사용 가능한 쿼리 및 뮤테이션 정의
- GraphQL 리졸버는 어떤 역할을 하며 어떤 식으로 정의되나요?
  - **GraphQL 리졸버 :** GraphQL 스키마에서 정의한 필드에 대한 실제 데이터 조회 및 처리 로직을 담당하는 함수
    - 클라이언트가 요청한 쿼리나 뮤테이션에 대한 결과를 생성하는 역할
  - 스키마의 타입 정의 부분에서 정의된 필드와 연결
  - 일반적으로 객체로 구성된 Resolver Map이라는 구조체로 정의
- GraphQL 리졸버의 성능 향상을 위한 DataLoader는 무엇이고 어떻게 쓰나요?
  - **DataLoader :** GraphQL API에서 자주 사용되는 N+1 문제를 해결하기 위한 유틸리티 라이브러리
    - **N+1 문제 :** 데이터를 조회할 때 하나의 객체에 대한 조회가 여러 번 발생하는 현상
  - DataLoader 패키지를 설치, DataLoader 인스턴스를 생성
  - 각각의 리졸버 함수에서 데이터를 조회할 때, DataLoader 인스턴스를 사용하여 데이터를 일괄적으로 조회
  - 중복된 데이터를 캐시에 저장하고, 여러 번의 데이터베이스 조회를 최소화
- 클라이언트 상에서 GraphQL 요청을 보내려면 어떻게 해야 할까요?
  - HTTP POST 요청
  - HTTP GET 요청
- Apollo 프레임워크(서버/클라이언트)의 장점은 무엇일까요?
  - 강력한 GraphQL 지원
  - 데이터 관리
  - 성능
  - 커뮤니티
  - 유연성
- Apollo Client를 쓰지 않고 Vanilla JavaScript로 GraphQL 요청을 보내려면 어떻게 해야 할까요?
  - HTTP 클라이언트 라이브러리 설치
  - GraphQL 서버의 URL 가져오기
  - GraphQL 쿼리 작성
  - HTTP 클라이언트 라이브러리로 GraphQL 요청 보내기
- GraphQL 기반의 API를 만들 때 에러처리와 HTTP 상태코드 등은 어떻게 하는게 좋을까요?
  - GraphQL Errors
  - HTTP 상태 코드
  - 예외 처리
  - HTTP 상태 코드 반환
  - GraphQL Middleware

## Quest

- 메모장의 서버와 클라이언트 부분을 GraphQL API로 수정해 보세요.

## Advanced

- GraphQL이 아직 제대로 수행하지 못하거나 불가능한 요구사항에는 어떤 것이 있을까요?
- GraphQL의 경쟁자에는 어떤 것이 있을까요?
