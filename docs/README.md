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

# Campus Connect Backend

Campus Connect 서비스의 백엔드 프로젝트입니다.  
사용자 커뮤니티 기능과 **챗봇 기반 상담 기능**을 제공하는 Spring Boot 기반 서버입니다.

---

# 서비스 화면

## 챗봇 대화 화면

<p align="center">
  <img src="images/chatbot-main.png" width="45%">
  <img src="images/chatbot-conversation.png" width="45%">
</p>

<br/>

## 챗봇 추천 결과

<p align="center">
  <img src="images/chatbot-recommend.png" width="45%">
  <img src="images/chatbot-product.png" width="45%">
</p>

<br/>

## 관리자 화면

<p align="center">
  <img src="images/admin-dashboard.png" width="45%">
  <img src="images/admin-statistics.png" width="45%">
</p>

---

# 챗봇 시스템 아키텍처

<p align="center">
  <img src="images/chatbot-architecture.png" width="800">
</p>

Campus Connect에서는 사용자 문의를 빠르게 처리하기 위해  
LLM 기반 챗봇을 활용한 상담 기능을 제공합니다.

챗봇 모델은 Python 서버에서 실행되며  
Spring Boot 서버는 **API Gateway 역할**을 수행합니다.

---

# 챗봇 서빙 흐름

```mermaid
flowchart LR
    User[User] --> FE[Frontend]
    FE --> API[Spring Boot API]

    API --> CHAT[Chatbot API]

    CHAT --> LLM[LLM Server]
    LLM --> DOCS[Knowledge Docs]
    LLM --> VECTOR[Vector DB]

    LLM --> CHAT
    CHAT --> API

### 메인 화면
![메인](https://github.com/mjkang4416/CC_back/blob/3220c7029269b171129110c785a118d9167015f7/docs/image.png)
![](https://github.com/mjkang4416/CC_back/blob/a57eb246ad82a6cbe27ca6ca1b9b239f5ae88067/docs/image1.png)
![](https://github.com/mjkang4416/CC_back/blob/1af0cb5cdd85acdf3bbce807c88e891c5df59450/docs/image3.png)

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
