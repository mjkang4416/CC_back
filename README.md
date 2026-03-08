# CC_BACKEND

Campus Connect 서비스의 백엔드 API 서버입니다.  
사용자 인증, 커뮤니티 게시글, 실시간 기능(WebSocket) 등을 처리하는  
Spring Boot 기반 백엔드 서버입니다.

## 목차

- [프로젝트 소개](#프로젝트-소개)
- [주요 기능](#주요-기능)
- [서비스 화면](#서비스-화면)
- [기술 스택](#기술-스택)
- [아키텍처](#아키텍처)
- [프로젝트 구조](#프로젝트-구조)
- [데이터베이스 설계](#데이터베이스-설계)
- [API 도메인](#api-도메인)
- [실행 방법](#실행-방법)
- [환경 변수](#환경-변수)

---

# 프로젝트 소개

| 항목 | 내용 |
| --- | --- |
| 프로젝트 이름 | Campus Connect Backend |
| 역할 | Backend 개발 |
| 개발 인원 | Backend 1 |
| 핵심 스택 | Java 17, Spring Boot, JPA, Redis, WebSocket |

Campus Connect는 사용자 간 커뮤니티 활동과 실시간 소통을 지원하는  
**Spring Boot 기반 커뮤니티 서비스 백엔드**입니다.

게시글 기반 커뮤니티 기능과 함께  
**WebSocket 기반 실시간 통신**, **Spring Security 인증**, **Redis 캐시** 등을 적용하여  
확장성과 유지보수성을 고려한 백엔드 아키텍처를 설계했습니다.

---

# 주요 기능

- 사용자 인증 / 권한 관리
- 커뮤니티 게시글 CRUD
- WebSocket 기반 실시간 기능
- Redis 기반 데이터 처리
- Swagger 기반 API 문서 제공

---

# 서비스 화면

> 아래 이미지들은 `docs/images` 폴더에 업로드한 뒤 사용하세요.

### 메인 화면
![메인](docs/images/main.png)

### 게시글 화면
![게시글](docs/images/post.png)

---

# 기술 스택

## Backend

- Java 17
- Spring Boot
- Spring Data JPA
- Spring Security
- WebSocket / STOMP
- Redis

## Database

- MySQL

## Infra / DevOps

- AWS (EC2, RDS)

## Tools

- Swagger (springdoc-openapi)
- log4jdbc
- Logback

---

# 아키텍처

```mermaid
flowchart LR
    User[User] --> FE[Frontend]
    FE --> API[Spring Boot API]
    API --> SEC[Spring Security]
    API --> SERVICE[Service Layer]
    SERVICE --> REPO[JPA Repository]
    REPO --> DB[(MySQL)]
    API --> REDIS[(Redis)]
    API --> WS[WebSocket]
