# Campus Connect Backend (CC_back)

> Spring Boot 기반 커뮤니티 및 실시간 소통 서비스 백엔드

Campus Connect는 사용자 간 커뮤니티 활동과 실시간 소통을 지원하는\
Spring Boot 기반 백엔드 서비스입니다.

게시글 기반 커뮤니티 기능과 함께 **WebSocket 기반 실시간 통신**,\
**Spring Security 인증/인가**, **Redis 기반 데이터 처리**를 적용하여\
확장성과 유지보수성을 고려한 백엔드 구조를 설계했습니다.

------------------------------------------------------------------------

# 📌 프로젝트 개요

  항목            내용
  --------------- ---------------------------------------
  프로젝트 이름   Campus Connect Backend
  개발 인원       Backend 1명
  Repository      https://github.com/mjkang4416/CC_back

------------------------------------------------------------------------

# 🚀 주요 기능

## 사용자 인증 / 인가

-   Spring Security 기반 인증 처리
-   사용자 권한 관리
-   로그인 및 사용자 정보 관리

## 커뮤니티 기능

-   게시글 생성 / 조회 / 수정 / 삭제
-   커뮤니티 데이터 관리
-   DTO 기반 API 응답 구조

## 실시간 통신

-   WebSocket + STOMP 기반 실시간 이벤트 처리
-   사용자 간 실시간 메시지 전달

## 데이터 관리

-   JPA 기반 데이터 접근
-   Repository 계층 분리
-   Entity / DTO 기반 데이터 모델링

## 캐시 및 성능 개선

-   Redis 기반 데이터 처리
-   실시간 기능 보조 및 성능 개선

------------------------------------------------------------------------

# 🛠 기술 스택

## Backend

  기술                설명
  ------------------- ----------------------------
  Java 17             백엔드 개발 언어
  Spring Boot 3.2.7   백엔드 프레임워크
  Spring Data JPA     ORM
  Spring Security     인증 / 인가
  WebSocket / STOMP   실시간 통신
  Redis               캐시 및 실시간 데이터 처리

## Database

  기술    설명
  ------- ---------------------
  MySQL   관계형 데이터베이스

## API 문서 / 로깅

  기술               설명
  ------------------ -----------
  Swagger(OpenAPI)   API 문서
  log4jdbc           SQL 로깅
  Logback            로그 관리

## Build Tool

  기술     설명
  -------- ---------------
  Gradle   프로젝트 빌드

------------------------------------------------------------------------

# 📂 프로젝트 구조

    src/main/java/com/example/cc
    │
    ├── config
    │   ├── security
    │   ├── websocket
    │   └── redis
    │
    ├── controller
    ├── service
    ├── repository
    ├── entity
    ├── dto
    └── CcApplication.java

------------------------------------------------------------------------

# 🏗 아키텍처

    Client
       ↓
    Controller
       ↓
    Service
       ↓
    Repository
       ↓
    Database (MySQL)

계층형 아키텍처를 적용하여 유지보수성과 확장성을 고려했습니다.

------------------------------------------------------------------------

# 📑 API 문서

Swagger UI

    http://localhost:8080/swagger-ui/index.html

------------------------------------------------------------------------

# ⚙ 실행 방법

## 1. 프로젝트 클론

    git clone https://github.com/mjkang4416/CC_back.git

## 2. application.properties 설정

    spring.datasource.url=jdbc:mysql://localhost:3306/db_name
    spring.datasource.username=your_id
    spring.datasource.password=your_password

    spring.data.redis.host=localhost
    spring.data.redis.port=6379

## 3. 프로젝트 실행

    ./gradlew bootRun

또는

    CcApplication 실행

------------------------------------------------------------------------

# 📊 ERD

![ERD](./doc/images/erd.png)

------------------------------------------------------------------------

# 📷 서비스 화면

![main](./doc/images/main.png)

![community](./doc/images/community.png)

------------------------------------------------------------------------

# 🔧 트러블슈팅

### Spring Security 인증 흐름 설계

Spring Security 적용 과정에서 인증 처리 흐름과 권한 관리 구조를 설계하여
API 접근 제어를 구현했습니다.

### WebSocket 기반 실시간 기능 구현

WebSocket + STOMP 구조를 적용하여 사용자 간 이벤트 전달을 비동기
방식으로 처리했습니다.

### Redis 활용

Redis를 활용하여 실시간 데이터 처리와 데이터 접근 성능을 개선했습니다.

------------------------------------------------------------------------

# 📈 개선 방향

-   캐시 전략 고도화
-   API 응답 구조 통일
-   테스트 코드 추가
-   서비스 레이어 책임 분리

------------------------------------------------------------------------

# 👨‍💻 Developer

Backend Developer

GitHub\
https://github.com/mjkang4416
