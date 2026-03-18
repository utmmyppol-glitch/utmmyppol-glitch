# 김보민 | Backend & Fullstack Developer

> 안 되면 될 때까지, 에러를 잡아낸 새벽의 쾌감을 아는 개발자

비전공자 출신으로 6개월 만에 WebSocket 실시간 채팅, Redis 세션 관리, AI 서버 연동까지 독학하며 성장했습니다.
3개의 프로젝트를 통해 기획부터 배포까지 전 과정을 경험했고, 실서비스 운영까지 해본 개발자입니다.

**Contact**: utmmyppol@naver.com | 010-4335-2920

-----

## Projects

### 1. 할인꿀팁 — 위치 기반 할인 정보 플랫폼

> 사용자 위치 반경 100m 이내 가맹점의 할인 정보를 실시간 푸시 알림으로 제공하는 O2O 플랫폼

**기간**: 2025.01 ~ 현재 운영 중  
**팀 구성**: 백엔드 1 + 프론트 1(본인) + 대표 1  
**투자 현황**: 정부 1곳 + 사설 2곳 투자 유치 스타트업  
**역할**: 백엔드 API 설계·개발, 프론트엔드 3개 클라이언트 개발, 배포 및 운영

**기술 스택**

|분류   |기술                                         |
|-----|-------------------------------------------|
|사용자 앱|Flutter, Dart, kakao_map_plugin            |
|사장님 앱|React Native, Expo                         |
|어드민 웹|React, Vite                                |
|백엔드  |Spring Boot, Java, JWT, Kakao Geocoding API|
|DB   |PostgreSQL (Neon)                          |
|인프라  |Google Cloud Run, Vercel, Firebase FCM     |

**핵심 기능**

- 카카오맵 기반 주변 매장 표시 + 반경 100m 근접 시 자동 푸시 알림
- 백그라운드 위치 추적 서비스 (60초 간격 서버 전송 → Haversine 거리 계산 → FCM 푸시)
- Android: CustomFcmService.kt 네이티브 알림 / iOS: Flutter onMessage 로컬 알림
- 커스텀 “할인” 사운드 알림 + 매장별 쿠폰 코드 발급
- 카카오·네이버 소셜 로그인 (OAuth 2.0)
- 사장님 앱: 매장 등록, 할인 정보 등록, 카카오 키워드 검색 (자동 좌표 변환)
- 어드민 웹: 가맹점 승인/거절, 푸시 알림 통계 대시보드

**트러블슈팅**

|문제               |원인                                                            |해결                                          |
|-----------------|--------------------------------------------------------------|--------------------------------------------|
|iOS 포그라운드 알림 미작동 |Android 전용 CustomFcmService 추가 시 NEARBY_DISCOUNT를 플랫폼 구분 없이 스킵|Platform.isAndroid 조건 추가 + FCM 리스너 초기화 순서 변경|
|Google 지오코딩 좌표 오류|Google API가 한국 주소 처리 부정확 + 키워드 검색 미지원                         |Kakao API로 전환, 주소 + 키워드 검색 이중 전략 적용         |
|Vercel SPA 404   |Chrome 직접 URL 접속 시 404                                        |vercel.json SPA rewrite 규칙 + map.html 예외 처리 |
|Cloud Run 403    |외부 요청 전체 차단                                                   |IAM 정책에 allUsers → roles/run.invoker 추가     |
|Expo SDK 버전 충돌   |Expo Go(54) ↔ 프로젝트(52) 불일치                                    |EAS Build로 전환, 실기기 직접 빌드                    |

**배포**

- iOS: Xcode Signing → Apple Developer → Bundle ID → APNs Key → EAS Build → TestFlight → App Store
- React Native: React → RN(Expo) 마이그레이션 → Vercel 정적 배포
- 백엔드: Docker → Google Cloud Run (asia-northeast3)

**성과**: 3개 클라이언트 단독 개발 / 28명 실 가맹점 사장님 가입 / 209개 매장 운영 / 서울 전역 커버

-----

### 2. IT-DA (잇다) — AI 기반 취미 커뮤니티 플랫폼

> 취미로 사람을 연결하는 AI 기반 모임 매칭 플랫폼

**기간**: 2024.12 ~ 2025.02  
**팀 구성**: 6명 (동원이와 구황작물들)  
**역할**: User CRUD, 실시간 채팅(WebSocket/STOMP), 팔로우 시스템, 뱃지 시스템, 알림 기능

**기술 스택**

|분류      |기술                                 |
|--------|-----------------------------------|
|Frontend|React 18, TypeScript, Vite, Zustand|
|Backend |Spring Boot, JPA, Spring Security  |
|AI      |Python, FastAPI                    |
|DB      |MySQL 8.0, Redis (세션 관리)           |
|실시간     |WebSocket, STOMP Protocol          |
|인프라     |AWS EC2, Docker, nginx             |

**핵심 기능**

- WebSocket/STOMP 기반 1:1 실시간 채팅 (카카오톡 스타일, 읽음 처리, 자동 재연결)
- AI 장소 추천: 참여자 주소 → 중간 지점 계산 → 카카오 장소 API → 선호도 매칭 → 상위 3곳 추천
- Redis 세션 관리: JWT 대신 Redis Session 선택 (즉시 로그아웃, 강제 세션 만료 가능)
- 팔로우/언팔로우 + 비공개 계정 팔로우 요청/수락 (WebSocket 실시간 알림)
- 뱃지 시스템: 125개 뱃지, 모임 참여 횟수 기반 자동 부여, 포켓몬 도감 스타일 UI
- 소셜 로그인: 카카오, 네이버, 구글 OAuth 2.0
- 모임 상태 실시간 업데이트 (진행 예정 → 진행 중 → 완료)

**트러블슈팅**

|문제               |원인                                                 |해결                                                                               |
|-----------------|---------------------------------------------------|---------------------------------------------------------------------------------|
|회원가입 4가지 복합 버그   |DTO-Entity 매핑 누락, 비밀번호 평문 저장, 위도경도 null, 카카오 500 에러|Postman으로 데이터 흐름 추적, @Builder 패턴 적용, BCrypt 암호화, GeocodingService 구현, OAuth 예외 처리|
|크롬↔사파리 팔로우 알림 안 감|WebSocket 구독 경로 불일치                                |구독 경로 정규화 + 브라우저별 테스트                                                            |
|채팅 읽음 “1” 안 사라짐  |markAsRead 웹소켓 브로드캐스트 누락                           |읽음 이벤트 양방향 전송 로직 추가                                                              |
|CORS + 세션 쿠키 문제  |Cross-Origin 환경에서 쿠키 전달 불가                         |SessionConfig Domain 제거, SecureCookie false, withCredentials 설정                  |

-----

### 3. 구구마켓 — 중고거래 플랫폼 (SPA)

> 위치 기반 지도 검색과 실시간 채팅을 갖춘 중고거래 플랫폼

**기간**: 2024.09 ~ 2024.11  
**팀 구성**: 6명 (팀 프로젝트)  
**역할**: 카카오맵 지도 기능, 소셜 로그인, 회원 등급제, DB 설계

**기술 스택**

|분류      |기술                                                  |
|--------|----------------------------------------------------|
|Frontend|React 18, Zustand, React Router, Axios              |
|Backend |Java 21, Spring Boot, JPA/Hibernate, Spring Security|
|실시간     |WebSocket, STOMP                                    |
|DB      |MySQL 8.0                                           |
|지도      |Kakao Map API                                       |

**핵심 기능**

- 카카오맵 기반 지도 검색: 반경 km 필터링 + 가격별 필터링으로 주변 상품 마커 표시
- WebSocket/STOMP 1:1 채팅: 폴링 방식 대신 웹소켓으로 0초 지연 실시간 메시지
- 회원 등급제: Enum 클래스로 등급 관리, 거래 횟수에 따라 알→아기새→성조 자동 승급
- 실시간 알림: WebSocket으로 찜하기, 댓글 알림 실시간 전송 (unread count 표시)
- 공유하기: 유틸 컴포넌트로 분리하여 재사용성 극대화
- 신고하기 + 관리자 처리: resolve 메서드로 신고 접수/처리 기능
- 카카오 소셜 로그인 (OAuth 2.0)

**트러블슈팅**

|문제             |원인              |해결                           |
|---------------|----------------|-----------------------------|
|지도 연속 클릭 시 앱 튕김|마커 클릭 이벤트 중복 발생 |debouncing(300ms) 적용         |
|MVC → SSR 전환   |아키텍처 변경 시 라우팅 충돌|React Router v6 + SPA 구조로 재설계|

-----

## Tech Stack Summary

```
Backend     : Java, Spring Boot, JPA, Spring Security, JWT, Redis
Frontend    : React, React Native, Flutter, TypeScript, Zustand
Database    : MySQL, PostgreSQL (Neon)
Realtime    : WebSocket, STOMP, Firebase FCM
Map/Geo     : Kakao Maps API, Kakao Geocoding API
AI          : Python, FastAPI
Deploy      : Google Cloud Run, Vercel, AWS EC2, Docker, nginx
Auth        : OAuth 2.0 (Kakao, Naver, Google)
Tools       : Git, GitHub, Xcode, EAS Build
```

-----

## Education

**하이미디어 아카데미** — 풀스택 개발 과정 수료 (2024)  
**로이문화예술실용전문학교** — 이벤트기획과
