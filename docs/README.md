# CC Backend

Campus Connect의 백엔드 서버입니다.\
Spring Boot 기반 커뮤니티 서비스이며 **LLM 기반 챗봇 기능**을
제공합니다.

사용자 인증, 게시글 기능, 실시간 기능(WebSocket), 챗봇 서빙 연동을
담당합니다.

------------------------------------------------------------------------

# 프로젝트 소개

## 프로젝트 소개

| 항목 | 내용 |
| --- | --- |
| 프로젝트 이름 | Campus Connect Backend |
| 역할 | Backend 개발 |
| 개발 인원 | Backend 2 |
| 핵심 스택 | Java 17, Spring Boot, JPA, Redis, WebSocket |

------------------------------------------------------------------------

# 서비스 화면

<p align="center">
  <img src="https://github.com/mjkang4416/CC_back/blob/3220c7029269b171129110c785a118d9167015f7/docs/image.png" width="30%">
  <img src="https://github.com/mjkang4416/CC_back/blob/a57eb246ad82a6cbe27ca6ca1b9b239f5ae88067/docs/image1.png" width="30%">
  <img src="https://github.com/mjkang4416/CC_back/blob/1af0cb5cdd85acdf3bbce807c88e891c5df59450/docs/image3.png" width="30%">
</p>

------------------------------------------------------------------------

# 기술 스택

### Backend

-   Java 17
-   Spring Boot
-   Spring Data JPA
-   Spring Security
-   WebSocket / STOMP
-   Redis

### AI / Chatbot

-   Python
-   FastAPI
-   LLM 기반 응답 생성

### Database

-   MySQL

### Infra

-   AWS EC2
-   AWS RDS

### Tools

-   Swagger (springdoc-openapi)
-   log4jdbc
-   Logback

------------------------------------------------------------------------

# 시스템 아키텍처

``` mermaid
flowchart LR
User --> FE
FE --> API
API --> Service
Service --> Repository
Repository --> DB[(MySQL)]
API --> Redis
API --> WebSocket
```

# 챗봇 시스템 아키텍처

``` mermaid
flowchart LR
User --> Frontend
Frontend --> SpringBoot
SpringBoot --> ChatbotServer
ChatbotServer --> LLM
LLM --> KnowledgeBase
```

Campus Connect에서는 사용자 문의를 빠르게 처리하기 위해\
**LLM 기반 챗봇 상담 기능**을 제공합니다.

챗봇 모델은 **Python 서버**에서 실행되며\
Spring Boot 서버는 **API Gateway 역할**을 수행합니다.

------------------------------------------------------------------------

# 프로젝트 구조

    src/main/java/com/example/cc
    ├── config
    │   ├── security
    │   ├── websocket
    │   └── redis
    ├── controller
    ├── service
    ├── repository
    ├── entity
    ├── dto
    └── CcApplication.java

------------------------------------------------------------------------

# 실행 방법

### 요구사항

-   JDK 17
-   MySQL
-   Redis

### 실행

``` bash
./gradlew clean build
./gradlew bootRun
```

------------------------------------------------------------------------

# 환경 변수

    DB_URL=
    DB_USERNAME=
    DB_PASSWORD=

    REDIS_HOST=
    REDIS_PORT=

    JWT_SECRET=

    CHATBOT_SERVER_URL=

------------------------------------------------------------------------

# 트러블슈팅 / 개선 포인트

-   Spring Security 인증 흐름 정리
-   WebSocket 기반 실시간 기능 구현
-   Redis 캐싱을 통한 응답 성능 개선
-   챗봇 서버와 백엔드 서버 분리를 통한 확장성 확보
