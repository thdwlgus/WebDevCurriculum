# Quest 19-B. 서버 아키텍쳐 패턴

## Introduction

- 이번 퀘스트에서는 현대적인 서버 아키텍쳐 패턴에 대해 익혀 보도록 하겠습니다.

## Topics

- Microservice Architecture
- Serverless Architecture
- AWS Lambda
- Service Mesh

## Resources

- [Jeff Bezos의 이메일](https://news.hada.io/topic?id=638)
- [마이크로서비스란?](https://www.redhat.com/ko/topics/microservices/what-are-microservices)
- [AWS Lambda](https://docs.aws.amazon.com/ko_kr/lambda/latest/dg/welcome.html)
- [AWS API Gateway](https://docs.aws.amazon.com/ko_kr/apigateway/latest/developerguide/welcome.html)

## Checklist

- 마이크로서비스 아키텍쳐란 무엇일까요? 어떤 식으로 서비스를 구성할 수 있을까요? 어떤 장점을 가지고 있을까요?
  - 각각 독립적이고 느슨한 관계의 MicroService들이 모여 하나의 체계를 이룬 개념으로 보는 설계 방법론
  - application 하나가 부모입장에서 종속된 모든 service를 제공하는 방식이 아닌, 독립적인 microservices들이 모여 하나의 체계를 이룬 개념으로 보는 것
  - microservices들은 독립적으로 배포할 수 있으며, 하나의 프로그램에 통합하는 build 과정을 거치지 않고도 기존 service들을 update 가능
  - **장점**
    - 변경점을 적용해야 할 부분만 반영하면 되기 때문에 유지보수가 더 수월
    - 체계적으로 시스템 및 파일관리가 가능
    - 유지관리가 더 잘되기 때문에, 서비스의 신뢰도 증가
  - 하나의 application을 독립적인 service들로 구성
- 서버리스 아키텍쳐란 무엇일까요? 어떤 식으로 서비스를 구성할 수 있을까요? 어떤 장점을 가지고 있을까요?
  - 서버(인프라)를 따로 구축하거나 관리할 필요없이 application과 service 운영에만 집중할 수 있는 설계 형태
  - **Backend as a Service**
    - DB 및 Social service 등 백엔드 관련(데이터 저장 및 추출 등) 기능(API)을 제공하여, 별도의 server 개발을 하지 않고도 백엔드 구축
    - 정적인 용량에 대한 비용 지불이 아닌, 유동적인 사용량에 근거하여 비용을 지불
    - 가장 대표적인 플랫폼으로 Firebase
  - **장점**
    - Firebase와 같은 백엔드 시스템이(데이터를 저장하고 이를 활용할 수 있는 공간) 이미 구축되어 있는 상태라면, 별도의 서버구축비용이 들지 않고 사용비용만 지불
    - 서버구축에 대한 개발비용도 들지 않으므로 효율적일 수 있고, 일정 용량까지는 무료이므로 학습용/연습용으로 유용하게 사용
  - **Funcion as a Service**
    - 프로젝트를 여러 개의 함수로 쪼개서 분산된 컴퓨팅 환경(가상환경)에 등록한 후, 이 함수들이 실행하는 만큼 비용을 내는 플랫폼
    - 하나의 기능을 제공한다는 개념
    - 클라우드 환경에 사용자가 등록한 함수에 대한 API를 제공하고, 해당 함수가 실행될 때마다 비용을 지불하는 형태로 진행
  - **장점**
    - 따로 서버를 구축하지 않아도 된다는 점에서 BaaS와 유사하지만, BaaS는 하나의 저장소(所)나 플랫폼이 아닌 함수(API)를 제공하며 해당 함수가 호출될 경우에만 실행이 된다는 특징
    - 자체적으로 로그분석 및 실시간 모니터링 시스템을 적용하여, 특정 함수 호출 시 알람을 발생하게 하는 등 추가적인 기능도 연동 가능
- AWS Lambda는 어떤 서비스일까요? 이러한 서비스는 어떤 특징을 가지고, 어디에 쓰일 수 있을까요?
  - AWS에서 제공하는 FaaS의 일종
  - application 및 mobile app의 백엔드를 별도 구축없이 빠르게 구현할 수 있는 서비스
- API Gateway는 어떤 서비스인가요? 어떤 설정을 할 수 있을까요?
  - Microservice의 경계 외부(최후방)에서 오는 API호출을 제어하고, 각 servcies에게 메시지를 보내는 서비스
- 많은 마이크로서비스들을 복잡하게 연결할 경우 관리상에 어떤 난점이 생길 수 있을까요? 서비스 메쉬는 무엇이고 이러한 난점을 어떻게 해결하려는 시도일까요?
  - Microservice의 경계 내부(네트워크)에서의 트래픽을 관리하는 서비스

## Quest

- 메모장 시스템을 JWT 발급을 위한 마이크로서비스와 실제 비즈니스 로직을 처리하는 마이크로서비스로 나누어 보세요.
- JWT 토큰 발급의 역할을 하는 마이크로서비스를 AWS Lambda와 API Gateway를 이용하여 구축해 보세요.

## Advanced

- Istio는 어떤 툴일까요? 이 툴을 Kubernetes와 함께 사용하여 어떤 구조를 구현할 수 있을까요?
