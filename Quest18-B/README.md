# Quest 18-B. 서비스의 운영: 로깅과 모니터링

## Introduction

- 이번 퀘스트에서는 서비스의 운영을 위해 로그를 스트리밍하는 법에 대해 다루겠습니다.

## Topics

- ElasticSearch
- AWS ElasticSearch Service
- Grafana

## Resources

- [ElasticSearch](https://www.elastic.co/kr/what-is/elasticsearch)
- [ElasticSearch 101](https://www.elastic.co/kr/webinars/getting-started-elasticsearch)
- [Grafana Panels](https://grafana.com/docs/grafana/latest/panels/)

## Checklist

- ElasticSearch는 어떤 DB인가요? 기존의 RDB와 어떻게 다르고 어떤 장단점을 가지고 있나요?
  - **ElasticSearch**
    - 분산형 RESTful 검색/분석 엔진으로, 차세대 데이터 플랫폼이라 불리우는 Elastic stack의 가장 핵심적인 요소
    - 방대한 양의 데이터를 신속하게, NRT(Near Real Time, 거의 실시간)한 속도로 데이터 저장/검색/분석 가능
  - **Logstash**
    - 데이터를 정제하고 전처리하여 ElasticSearch에게 전달
    - DB, .csv 등의 로그 및 트랜잭션 데이터를 parsing하는 역할을 담당
  - **ElasticSeach**
    - 데이터 검색/분석뿐만 아니라 저장소역할까지 담당
    - Logstash로 부터 받은 데이터를 검색/집계하여 필요 정보를 획득
  - **Kibana**
    - ElasticSearch에 저장된 데이터를 시각화 및 모니터링
  - **ElasticSearch/RDB**
    - 사실상 이름만 다르고, 전체적인 원리나 개념은 비슷
  - **ElasticSearch와 RDB의 다른점**
    - RDB는 행(속성, Column)을 기반으로 데이터를 저장하는 반면, ElasticSearch는 단어를 기반으로 데이터를 저장
    - 따라서 데이터 자체를(데이터는 우리가 선별하고자 하는 객체가 될 수 있고, 그 객체를 포함하는 전체 속성이 될 수 있다) 다루는데는(수정/삭제) RDB가 유용할 수는 있으나, 검색 측면에서는 객체 확인을 계속 반복하기 때문에 비효율적
    - 데이터를 단어 기반으로 저장하는 ElasticSearch에서의 검색, 수집 등은 RDB에 비해 훨씬 효율적
    - 해당 단어를 검색한다면 단어가 존재하는 행을 찾는 방식이 ElasticSearch이고, 반대로 행에서 단어를 찾는 방식이라면 RDB
- AWS의 ElasticSearch Service는 어떤 서비스인가요? ElasticSearch를 직접 설치하거나 elastic.co에서 직접 제공하는 클라우드 서비스와 비교하여 어떤 장단점이 있을까요?
  - 라이센스가 바뀐 ElasticSearch의 접근성, 사용자 편의, 관련 서비스 제공을 위해 AWS가 주도하는 OpenSearch 프로젝트의 일환
  - ElasticSearch는 원래 Apache Lucene 기반의 서비스였으나, 2021년 1월 라이센스를 변경하여 Elastic을 통해 서비스를 제공
  - ElasticSearch를 직접 설치할 경우 관련 인프라나 클러스터 등을 사용자가 직접 제어해야하고, 회사에서 제공하는 서비스를 받을 경우 완전관리 형태로 이용 가능
- Grafana의 Panel 형식에는 어떤 것이 있을까요? 로그를 보기에 적합한 판넬은 어떤 형태일까요?
  - **Grafana**
    - 데이터 시각화를 위한 대시보드를 제공해주는 오픈소스 툴 킷
    - 오픈소스인 만큼 사용자가 만든 대시보드를 import하여 사용할 수 있고, 커스터마이징까지 가능
    - plugin을 통한 내부적으로 확장하여 사용 가능

## Quest

- 우리의 웹 서버가 stdout으로 적절한 로그를 남기도록 해 보세요.
- ElasticSearch Service 클러스터를 작은 사양으로 하나 만들고, 도커 컨테이너의 stdout으로 출력된 로그가 ElasticSearch로 스트리밍 되도록 해 보세요.
- Grafana를 이용해 ElasticSearch의 로그를 실시간으로 볼 수 있는 페이지를 만들어 보세요.

## Advanced

- ElasticSearch와 Grafana는 어떤 라이센스로 배포되고 있을까요? AWS와 같은 클라우드 제공자들이 이러한 오픈소스를 서비스화 하는 것을 둘러싼 논란은 어떤 논점일까요?
