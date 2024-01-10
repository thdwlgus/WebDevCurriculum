# Quest 17-B. 배포 파이프라인

## Introduction

- 이번 퀘스트에서는 CI/CD 파이프라인이 왜 필요한지, 어떻게 구축할 수 있는지 등에 대해 다룹니다.

## Topics

- Continuous Integration
- Continuous Delivery
- AWS Codebuild

## Resources

- [AWS: Continuous Integration](https://aws.amazon.com/ko/devops/continuous-integration/)
- [AWS: Continuous Delivery](https://aws.amazon.com/ko/devops/continuous-delivery/)
- [AWS Codebuild](https://aws.amazon.com/ko/codebuild/getting-started/)

## Checklist

- CI/CD는 무엇일까요? CI/CD 시스템을 구축하면 어떤 장점이 있을까요?
  - application의 개발을 하는데 필요한 과정 중 하나, 지속통합(여러 개발사항을 반영한 각각의 branch(자체적으로 진행한 개발)들을 하나로 통합하는 것)과 지속배포
  - CI/CD와 CI/CD 자동화는 Devops를 하는데 반드시 필요한 개발방법론
  - CI의 자동화
  - CD의 자동화
- CI 시스템인 Travis CI, Jenkins, Circle CI, Github Actions, AWS Codebuild 의 차이점과 장단점은 무엇일까요?
  - **AWS Codebuiod**
    - AWS에서 제공하는 툴, 완전히 managed된 build service를 제공
    - 컴파일, 실행, 프로덕션까지 수행해주기 때문에 AWS Codebuild를 채택하면 별도의 build server를 관리하고 모니터링 불필요
  - **Circle CI**
    - CI/CD 플랫폼을 제공하는 소프트웨어
    - 소프트웨어를 활용하여 CI/CD 과정을 자동화할 수 있도록 지원
  - **Jenkins**
    - CI system에서 가장 많이 활용하는 open source - CI server
    - 코드의 build, test, deploy를 지원해주는 tool

## Quest

- AWS Codebuild를 이용하여, 특정 브랜치에 푸시를 하면 린트와 테스트를 거쳐 서버 이미지를 빌드한 뒤, 직전 퀘스트의 EC2 인스턴스에 배포되는 시스템을 만들어 보세요.

## Advanced

- 빅테크 회사들이 코드를 빌드하고 배포하는 시스템은 어떻게 설계되고 운영되고 있을까요?
