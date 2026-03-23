# 김보민 ✦ Bomin Kim

**`Backend & Fullstack Developer`**

*안 되면 될 때까지, 에러를 잡아낸 새벽의 쾌감을 아는 개발자*

[![Gmail](https://img.shields.io/badge/utmmyppol@naver.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:utmmyppol@naver.com) [![GitHub](https://img.shields.io/badge/utmmyppol--glitch-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/utmmyppol-glitch)

-----

## 🧑‍💻 About Me

비전공자 출신으로 **6개월 만에** WebSocket 실시간 채팅, Redis 세션 관리, AI 서버 연동까지 독학하며 성장했습니다.  
3개의 프로젝트를 통해 **기획 → 개발 → 배포 → 운영**까지 전 과정을 경험했고, 실서비스 운영 중인 개발자입니다.

> 💡 *“될 때까지 하면, 안 되는 건 없다”*

-----

## 🛠 Tech Stack

**Backend**  
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![JPA](https://img.shields.io/badge/JPA-59666C?style=flat-square&logo=hibernate&logoColor=white) ![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white) ![JWT](https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

**Frontend**  
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black) ![React Native](https://img.shields.io/badge/React_Native-61DAFB?style=flat-square&logo=react&logoColor=black) ![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![Zustand](https://img.shields.io/badge/Zustand-443E38?style=flat-square&logo=react&logoColor=white)

**Database**  
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

**Realtime**  
![WebSocket](https://img.shields.io/badge/WebSocket-010101?style=flat-square&logo=socketdotio&logoColor=white) ![STOMP](https://img.shields.io/badge/STOMP-010101?style=flat-square) ![Firebase FCM](https://img.shields.io/badge/Firebase_FCM-FFCA28?style=flat-square&logo=firebase&logoColor=black)

**DevOps**  
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Cloud Run](https://img.shields.io/badge/Cloud_Run-4285F4?style=flat-square&logo=googlecloud&logoColor=white) ![AWS EC2](https://img.shields.io/badge/AWS_EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=white) ![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white) ![nginx](https://img.shields.io/badge/nginx-009639?style=flat-square&logo=nginx&logoColor=white)

**Auth**  
![OAuth 2.0](https://img.shields.io/badge/OAuth_2.0-EB5424?style=flat-square&logo=auth0&logoColor=white) ![Kakao](https://img.shields.io/badge/Kakao-FFCD00?style=flat-square&logo=kakao&logoColor=black) ![Naver](https://img.shields.io/badge/Naver-03C75A?style=flat-square&logo=naver&logoColor=white) ![Google](https://img.shields.io/badge/Google-4285F4?style=flat-square&logo=google&logoColor=white)

-----

## 🚀 Projects

### 1. 할인꿀팁 — 위치 기반 할인 정보 O2O 플랫폼

> 📍 반경 100m 이내 가맹점 할인 정보를 실시간 푸시 알림으로 제공

- **기간:** 2025.01 ~ 현재 운영 중
- **팀 구성:** 백엔드 1 + 프론트 1(본인) + 대표 1
- **투자:** 정부 1곳 + 사설 2곳 투자 유치
- **역할:** 백엔드 API 설계·개발, 프론트 3개 클라이언트, 배포·운영
- **Tech:** `Flutter` `React Native(Expo)` `React` `Spring Boot` `PostgreSQL(Neon)` `Cloud Run` `FCM`

**✨ 핵심 기능 & 성과**

- 카카오맵 기반 주변 매장 표시 + **반경 100m 자동 푸시 알림**
- 백그라운드 위치 추적 (60초 간격 → Haversine 거리 계산 → FCM 푸시)
- Android `CustomFcmService.kt` 네이티브 알림 / iOS Flutter `onMessage` 로컬 알림
- 커스텀 “할인” 사운드 알림 + 매장별 쿠폰 코드 발급
- 카카오·네이버 소셜 로그인 (OAuth 2.0)
- 사장님 앱: 매장·할인 등록, 카카오 키워드 검색 (자동 좌표 변환)
- 어드민 웹: 가맹점 승인/거절, 푸시 알림 통계 대시보드
- 🏆 **3개 클라이언트 단독 개발 / 28명 실 가맹점 / 209개 매장 / 서울 전역 커버**

**🔧 트러블슈팅**

- **iOS 포그라운드 알림 미작동** → Android 전용 로직 플랫폼 미분기 → `Platform.isAndroid` 조건 분기 + FCM 리스너 초기화 순서 변경
- **Google 지오코딩 좌표 오류** → Google API 한국 주소 처리 부정확 → Kakao API 전환, 주소+키워드 이중 전략
- **Vercel SPA 404** → URL 직접 접속 시 라우팅 실패 → `vercel.json` SPA rewrite + `map.html` 예외 처리
- **Cloud Run 403** → 외부 요청 전체 차단 → IAM `allUsers → roles/run.invoker` 추가
- **Expo SDK 버전 충돌** → Expo Go(54) ↔ 프로젝트(52) 불일치 → EAS Build 전환, 실기기 직접 빌드

-----

### 2. IT-DA (잇다) — AI 기반 취미 커뮤니티 플랫폼

> 🤝 취미로 사람을 연결하는 AI 모임 매칭 플랫폼

- **기간:** 2024.12 ~ 2025.02
- **팀 구성:** 6명 (동원이와 구황작물들)
- **역할:** User CRUD, 실시간 채팅(WebSocket/STOMP), 팔로우, 뱃지, 알림
- **Tech:** `React 18` `TypeScript` `Spring Boot` `MySQL` `Redis` `WebSocket/STOMP` `FastAPI` `AWS EC2` `Docker`

**✨ 핵심 기능**

- WebSocket/STOMP 기반 **1:1 실시간 채팅** (카카오톡 스타일, 읽음 처리, 자동 재연결)
- AI 장소 추천: 참여자 주소 → 중간 지점 계산 → 카카오 장소 API → 상위 3곳 추천
- **Redis 세션 관리**: JWT 대신 Redis Session (즉시 로그아웃, 강제 세션 만료)
- 팔로우/언팔로우 + 비공개 계정 팔로우 요청/수락 (WebSocket 실시간 알림)
- **뱃지 시스템**: 125개 뱃지, 모임 참여 횟수 기반 자동 부여, 포켓몬 도감 스타일 UI
- 소셜 로그인: 카카오, 네이버, 구글 OAuth 2.0

**🔧 트러블슈팅**

- **회원가입 복합 버그 4종** → DTO-Entity 매핑 누락, 비번 평문 저장, 좌표 null, 카카오 500 → Postman 추적 + `@Builder` + BCrypt + GeocodingService + OAuth 예외 처리
- **크롬↔사파리 팔로우 알림 불가** → WebSocket 구독 경로 불일치 → 구독 경로 정규화 + 브라우저별 테스트
- **채팅 읽음 “1” 안 사라짐** → `markAsRead` 브로드캐스트 누락 → 읽음 이벤트 양방향 전송 로직 추가
- **CORS + 세션 쿠키 문제** → Cross-Origin 쿠키 전달 불가 → SessionConfig Domain 제거 + `withCredentials` 설정

-----

### 3. 구구마켓 — 중고거래 플랫폼 (SPA)

> 🛒 위치 기반 지도 검색 + 실시간 채팅 중고거래

- **기간:** 2024.09 ~ 2024.11
- **팀 구성:** 6명 (팀 프로젝트)
- **역할:** 카카오맵 지도, 소셜 로그인, 회원 등급제, DB 설계
- **Tech:** `React 18` `Zustand` `Spring Boot` `JPA` `MySQL` `WebSocket/STOMP` `Kakao Map API`

**✨ 핵심 기능**

- 카카오맵 기반 **반경 km 필터링 + 가격별 필터링** 주변 상품 마커 표시
- WebSocket/STOMP 1:1 채팅 (0초 지연 실시간 메시지)
- **회원 등급제**: 거래 횟수 기반 알→아기새→성조 자동 승급 (Enum)
- 실시간 알림: 찜하기, 댓글 알림 (unread count 표시)
- 카카오 소셜 로그인 (OAuth 2.0)

**🔧 트러블슈팅**

- **지도 연속 클릭 시 앱 튕김** → 마커 클릭 이벤트 중복 발생 → debouncing(300ms) 적용
- **MVC → SSR 전환** → 아키텍처 변경 시 라우팅 충돌 → React Router v6 + SPA 구조로 재설계

-----

## 📊 GitHub Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=utmmyppol-glitch&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0D1117&title_color=58A6FF&icon_color=58A6FF&text_color=C9D1D9)

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=utmmyppol-glitch&layout=compact&theme=tokyonight&hide_border=true&bg_color=0D1117&title_color=58A6FF&text_color=C9D1D9)

-----

## 📫 Contact

**utmmyppol@naver.com** · **010-4335-2920**

*“코드 한 줄이 세상을 바꿀 수 있다고 믿습니다.”*