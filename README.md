<!DOCTYPE html>

<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>김보민 | Developer Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600&family=Noto+Sans+KR:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }

:root {
–bg: #0a0a0f;
–bg-card: #12121a;
–bg-card-hover: #1a1a26;
–border: #1e1e2e;
–text: #e4e4ef;
–text-dim: #6b6b80;
–accent: #4af2c8;
–accent-2: #7c6aff;
–accent-3: #ff6b9d;
–gradient-1: linear-gradient(135deg, #4af2c8, #7c6aff);
–gradient-2: linear-gradient(135deg, #7c6aff, #ff6b9d);
}

html { scroll-behavior: smooth; }

body {
font-family: ‘Noto Sans KR’, ‘Outfit’, sans-serif;
background: var(–bg);
color: var(–text);
overflow-x: hidden;
line-height: 1.7;
}

/* ── Grain overlay ── */
body::before {
content: ‘’;
position: fixed;
inset: 0;
background-image: url(“data:image/svg+xml,%3Csvg viewBox=‘0 0 256 256’ xmlns=‘http://www.w3.org/2000/svg’%3E%3Cfilter id=‘n’%3E%3CfeTurbulence type=‘fractalNoise’ baseFrequency=‘0.9’ numOctaves=‘4’ stitchTiles=‘stitch’/%3E%3C/filter%3E%3Crect width=‘100%25’ height=‘100%25’ filter=‘url(%23n)’ opacity=‘0.04’/%3E%3C/svg%3E”);
pointer-events: none;
z-index: 9999;
}

/* ── Floating orbs ── */
.orb {
position: fixed;
border-radius: 50%;
filter: blur(80px);
opacity: 0.15;
pointer-events: none;
z-index: 0;
animation: orbFloat 20s ease-in-out infinite;
}
.orb-1 { width: 500px; height: 500px; background: var(–accent); top: -100px; left: -100px; }
.orb-2 { width: 400px; height: 400px; background: var(–accent-2); bottom: -50px; right: -100px; animation-delay: -7s; }
.orb-3 { width: 300px; height: 300px; background: var(–accent-3); top: 50%; left: 60%; animation-delay: -14s; }

@keyframes orbFloat {
0%, 100% { transform: translate(0, 0) scale(1); }
33% { transform: translate(30px, -40px) scale(1.05); }
66% { transform: translate(-20px, 30px) scale(0.95); }
}

/* ── Container ── */
.container {
max-width: 900px;
margin: 0 auto;
padding: 0 24px;
position: relative;
z-index: 1;
}

/* ── Hero ── */
.hero {
min-height: 100vh;
display: flex;
align-items: center;
justify-content: center;
text-align: center;
padding: 60px 0;
}

.hero-inner {
animation: fadeUp 1s ease-out;
}

@keyframes fadeUp {
from { opacity: 0; transform: translateY(40px); }
to { opacity: 1; transform: translateY(0); }
}

.avatar-ring {
width: 130px;
height: 130px;
border-radius: 50%;
padding: 3px;
background: var(–gradient-1);
margin: 0 auto 32px;
animation: ringPulse 3s ease-in-out infinite;
}

@keyframes ringPulse {
0%, 100% { box-shadow: 0 0 0 0 rgba(74, 242, 200, 0.3); }
50% { box-shadow: 0 0 0 12px rgba(74, 242, 200, 0); }
}

.avatar-ring img {
width: 100%;
height: 100%;
border-radius: 50%;
object-fit: cover;
border: 3px solid var(–bg);
}

.avatar-placeholder {
width: 100%;
height: 100%;
border-radius: 50%;
background: var(–bg-card);
border: 3px solid var(–bg);
display: flex;
align-items: center;
justify-content: center;
font-size: 48px;
font-weight: 700;
background: linear-gradient(135deg, #1a1a26, #12121a);
color: var(–accent);
font-family: ‘Outfit’, sans-serif;
}

.hero h1 {
font-family: ‘Outfit’, sans-serif;
font-size: 3.2rem;
font-weight: 800;
letter-spacing: -1px;
margin-bottom: 8px;
background: var(–gradient-1);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
background-clip: text;
}

.hero .subtitle {
font-family: ‘JetBrains Mono’, monospace;
font-size: 0.95rem;
color: var(–text-dim);
letter-spacing: 2px;
text-transform: uppercase;
margin-bottom: 24px;
}

.hero .tagline {
font-size: 1.1rem;
color: var(–text-dim);
max-width: 520px;
margin: 0 auto 36px;
font-weight: 300;
line-height: 1.8;
}

.hero .tagline em {
color: var(–accent);
font-style: normal;
font-weight: 500;
}

.contact-links {
display: flex;
gap: 12px;
justify-content: center;
flex-wrap: wrap;
}

.contact-links a {
display: inline-flex;
align-items: center;
gap: 8px;
padding: 10px 20px;
border: 1px solid var(–border);
border-radius: 100px;
color: var(–text-dim);
text-decoration: none;
font-size: 0.85rem;
font-family: ‘JetBrains Mono’, monospace;
transition: all 0.3s ease;
background: rgba(18, 18, 26, 0.6);
backdrop-filter: blur(10px);
}

.contact-links a:hover {
border-color: var(–accent);
color: var(–accent);
transform: translateY(-2px);
box-shadow: 0 4px 20px rgba(74, 242, 200, 0.15);
}

/* ── Section ── */
section {
padding: 80px 0;
}

.section-label {
font-family: ‘JetBrains Mono’, monospace;
font-size: 0.75rem;
color: var(–accent);
letter-spacing: 3px;
text-transform: uppercase;
margin-bottom: 12px;
}

.section-title {
font-family: ‘Outfit’, sans-serif;
font-size: 2rem;
font-weight: 700;
margin-bottom: 48px;
color: var(–text);
}

/* ── Tech Stack ── */
.stack-category {
margin-bottom: 32px;
}

.stack-category-name {
font-family: ‘JetBrains Mono’, monospace;
font-size: 0.8rem;
color: var(–text-dim);
letter-spacing: 1px;
margin-bottom: 12px;
text-transform: uppercase;
}

.stack-pills {
display: flex;
flex-wrap: wrap;
gap: 8px;
}

.pill {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 8px 16px;
background: var(–bg-card);
border: 1px solid var(–border);
border-radius: 100px;
font-size: 0.85rem;
font-weight: 500;
color: var(–text);
transition: all 0.3s ease;
cursor: default;
}

.pill:hover {
border-color: var(–accent);
transform: translateY(-2px);
box-shadow: 0 4px 16px rgba(74, 242, 200, 0.1);
}

.pill .dot {
width: 8px;
height: 8px;
border-radius: 50%;
flex-shrink: 0;
}

/* ── Project Cards ── */
.project-card {
background: var(–bg-card);
border: 1px solid var(–border);
border-radius: 20px;
padding: 40px;
margin-bottom: 32px;
transition: all 0.4s ease;
position: relative;
overflow: hidden;
}

.project-card::before {
content: ‘’;
position: absolute;
top: 0;
left: 0;
right: 0;
height: 3px;
border-radius: 20px 20px 0 0;
opacity: 0;
transition: opacity 0.4s ease;
}

.project-card:nth-child(1)::before { background: var(–gradient-1); }
.project-card:nth-child(2)::before { background: var(–gradient-2); }
.project-card:nth-child(3)::before { background: linear-gradient(135deg, #ff6b9d, #ffb86c); }

.project-card:hover {
border-color: #2a2a3a;
transform: translateY(-4px);
box-shadow: 0 20px 60px rgba(0,0,0,0.3);
}

.project-card:hover::before {
opacity: 1;
}

.project-num {
font-family: ‘Outfit’, sans-serif;
font-size: 4rem;
font-weight: 800;
line-height: 1;
margin-bottom: 16px;
opacity: 0.08;
position: absolute;
top: 20px;
right: 32px;
}

.project-badge {
display: inline-block;
padding: 4px 12px;
border-radius: 100px;
font-size: 0.7rem;
font-family: ‘JetBrains Mono’, monospace;
font-weight: 600;
letter-spacing: 1px;
text-transform: uppercase;
margin-bottom: 16px;
}

.badge-live {
background: rgba(74, 242, 200, 0.1);
color: var(–accent);
border: 1px solid rgba(74, 242, 200, 0.2);
}

.badge-complete {
background: rgba(124, 106, 255, 0.1);
color: var(–accent-2);
border: 1px solid rgba(124, 106, 255, 0.2);
}

.project-card h3 {
font-family: ‘Outfit’, sans-serif;
font-size: 1.6rem;
font-weight: 700;
margin-bottom: 8px;
}

.project-card .project-desc {
font-size: 0.95rem;
color: var(–text-dim);
margin-bottom: 24px;
font-weight: 300;
}

.project-meta {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
gap: 16px;
margin-bottom: 28px;
}

.meta-item {
font-size: 0.85rem;
}

.meta-item .meta-label {
color: var(–text-dim);
font-size: 0.75rem;
font-family: ‘JetBrains Mono’, monospace;
text-transform: uppercase;
letter-spacing: 1px;
margin-bottom: 4px;
}

.meta-item .meta-value {
color: var(–text);
font-weight: 500;
}

.project-tech {
display: flex;
flex-wrap: wrap;
gap: 6px;
margin-bottom: 28px;
}

.tech-tag {
padding: 4px 12px;
background: rgba(255,255,255,0.04);
border: 1px solid var(–border);
border-radius: 6px;
font-size: 0.78rem;
font-family: ‘JetBrains Mono’, monospace;
color: var(–text-dim);
}

.features-title {
font-size: 0.85rem;
font-weight: 600;
color: var(–text);
margin-bottom: 12px;
display: flex;
align-items: center;
gap: 8px;
}

.feature-list {
list-style: none;
margin-bottom: 24px;
}

.feature-list li {
position: relative;
padding-left: 20px;
margin-bottom: 8px;
font-size: 0.9rem;
color: var(–text-dim);
line-height: 1.6;
}

.feature-list li::before {
content: ‘▸’;
position: absolute;
left: 0;
color: var(–accent);
font-weight: 700;
}

.feature-list li strong {
color: var(–text);
font-weight: 500;
}

.achievement {
background: rgba(74, 242, 200, 0.05);
border: 1px solid rgba(74, 242, 200, 0.15);
border-radius: 12px;
padding: 16px 20px;
font-size: 0.9rem;
color: var(–accent);
font-weight: 500;
display: flex;
align-items: center;
gap: 10px;
}

/* ── Troubleshooting ── */
.trouble-toggle {
background: none;
border: 1px solid var(–border);
border-radius: 10px;
padding: 12px 20px;
color: var(–text-dim);
font-family: ‘JetBrains Mono’, monospace;
font-size: 0.8rem;
cursor: pointer;
width: 100%;
text-align: left;
transition: all 0.3s ease;
margin-top: 16px;
display: flex;
align-items: center;
justify-content: space-between;
}

.trouble-toggle:hover {
border-color: var(–accent);
color: var(–accent);
}

.trouble-toggle .arrow {
transition: transform 0.3s ease;
}

.trouble-toggle.open .arrow {
transform: rotate(180deg);
}

.trouble-content {
max-height: 0;
overflow: hidden;
transition: max-height 0.5s ease;
}

.trouble-content.open {
max-height: 2000px;
}

.trouble-item {
padding: 16px 0;
border-bottom: 1px solid var(–border);
}

.trouble-item:last-child {
border-bottom: none;
}

.trouble-problem {
font-weight: 600;
font-size: 0.88rem;
color: var(–text);
margin-bottom: 6px;
}

.trouble-detail {
font-size: 0.82rem;
color: var(–text-dim);
line-height: 1.6;
}

.trouble-detail span.cause {
color: var(–accent-3);
}

.trouble-detail span.fix {
color: var(–accent);
}

/* ── Stats ── */
.stats-grid {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 16px;
margin-bottom: 60px;
}

.stat-card {
background: var(–bg-card);
border: 1px solid var(–border);
border-radius: 16px;
padding: 24px;
text-align: center;
transition: all 0.3s ease;
}

.stat-card:hover {
border-color: var(–accent);
transform: translateY(-2px);
}

.stat-num {
font-family: ‘Outfit’, sans-serif;
font-size: 2.2rem;
font-weight: 800;
background: var(–gradient-1);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
background-clip: text;
line-height: 1.2;
}

.stat-label {
font-size: 0.75rem;
color: var(–text-dim);
margin-top: 4px;
font-family: ‘JetBrains Mono’, monospace;
letter-spacing: 0.5px;
}

/* ── Education ── */
.edu-item {
display: flex;
gap: 20px;
align-items: flex-start;
padding: 20px 0;
border-bottom: 1px solid var(–border);
}

.edu-item:last-child { border-bottom: none; }

.edu-year {
font-family: ‘JetBrains Mono’, monospace;
font-size: 0.8rem;
color: var(–accent);
min-width: 60px;
padding-top: 2px;
}

.edu-info h4 {
font-size: 1rem;
font-weight: 600;
margin-bottom: 4px;
}

.edu-info p {
font-size: 0.85rem;
color: var(–text-dim);
}

/* ── Footer ── */
footer {
text-align: center;
padding: 60px 0 40px;
border-top: 1px solid var(–border);
}

footer .quote {
font-size: 1rem;
color: var(–text-dim);
font-weight: 300;
font-style: italic;
margin-bottom: 20px;
}

footer .copy {
font-size: 0.75rem;
color: var(–text-dim);
opacity: 0.5;
font-family: ‘JetBrains Mono’, monospace;
}

/* ── Responsive ── */
@media (max-width: 768px) {
.hero h1 { font-size: 2.2rem; }
.project-card { padding: 28px; }
.project-num { font-size: 3rem; }
.stats-grid { grid-template-columns: repeat(2, 1fr); }
.project-meta { grid-template-columns: 1fr; }
}

@media (max-width: 480px) {
.hero h1 { font-size: 1.8rem; }
.section-title { font-size: 1.5rem; }
.stats-grid { grid-template-columns: repeat(2, 1fr); gap: 10px; }
.stat-card { padding: 16px; }
.stat-num { font-size: 1.6rem; }
}

/* ── Scroll animations ── */
.reveal {
opacity: 0;
transform: translateY(30px);
transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1);
}

.reveal.visible {
opacity: 1;
transform: translateY(0);
}
</style>

</head>
<body>

<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<!-- ══════ HERO ══════ -->

<section class="hero">
  <div class="container">
    <div class="hero-inner">
      <div class="avatar-ring">
        <div class="avatar-placeholder">BM</div>
      </div>
      <h1>김보민</h1>
      <p class="subtitle">Backend & Fullstack Developer</p>
      <p class="tagline">
        안 되면 될 때까지, 에러를 잡아낸 새벽의 쾌감을 아는 개발자.<br>
        비전공자 출신으로 <em>6개월 만에</em> WebSocket 실시간 채팅, Redis 세션 관리,<br>
        AI 서버 연동까지 독학하며 성장했습니다.
      </p>
      <div class="contact-links">
        <a href="mailto:utmmyppol@naver.com">✉ utmmyppol@naver.com</a>
        <a href="https://github.com/utmmyppol-glitch">⟁ GitHub</a>
        <a href="tel:010-4335-2920">☏ 010-4335-2920</a>
      </div>
    </div>
  </div>
</section>

<!-- ══════ STATS ══════ -->

<div class="container">
  <div class="stats-grid reveal">
    <div class="stat-card">
      <div class="stat-num">3</div>
      <div class="stat-label">Projects</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">209</div>
      <div class="stat-label">Stores Live</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">3</div>
      <div class="stat-label">Investments</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">6</div>
      <div class="stat-label">Months Growth</div>
    </div>
  </div>
</div>

<!-- ══════ TECH STACK ══════ -->

<section class="container">
  <div class="reveal">
    <p class="section-label">// skills</p>
    <h2 class="section-title">Tech Stack</h2>

```
<div class="stack-category">
  <p class="stack-category-name">Backend</p>
  <div class="stack-pills">
    <span class="pill"><span class="dot" style="background:#ED8B00"></span>Java</span>
    <span class="pill"><span class="dot" style="background:#6DB33F"></span>Spring Boot</span>
    <span class="pill"><span class="dot" style="background:#59666C"></span>JPA</span>
    <span class="pill"><span class="dot" style="background:#6DB33F"></span>Spring Security</span>
    <span class="pill"><span class="dot" style="background:#fff"></span>JWT</span>
    <span class="pill"><span class="dot" style="background:#DC382D"></span>Redis</span>
  </div>
</div>

<div class="stack-category">
  <p class="stack-category-name">Frontend</p>
  <div class="stack-pills">
    <span class="pill"><span class="dot" style="background:#61DAFB"></span>React</span>
    <span class="pill"><span class="dot" style="background:#61DAFB"></span>React Native</span>
    <span class="pill"><span class="dot" style="background:#02569B"></span>Flutter</span>
    <span class="pill"><span class="dot" style="background:#3178C6"></span>TypeScript</span>
    <span class="pill"><span class="dot" style="background:#764ABC"></span>Zustand</span>
  </div>
</div>

<div class="stack-category">
  <p class="stack-category-name">Database</p>
  <div class="stack-pills">
    <span class="pill"><span class="dot" style="background:#4479A1"></span>MySQL</span>
    <span class="pill"><span class="dot" style="background:#4169E1"></span>PostgreSQL</span>
  </div>
</div>

<div class="stack-category">
  <p class="stack-category-name">Realtime & DevOps</p>
  <div class="stack-pills">
    <span class="pill"><span class="dot" style="background:#fff"></span>WebSocket</span>
    <span class="pill"><span class="dot" style="background:#FFCA28"></span>Firebase FCM</span>
    <span class="pill"><span class="dot" style="background:#2496ED"></span>Docker</span>
    <span class="pill"><span class="dot" style="background:#4285F4"></span>Cloud Run</span>
    <span class="pill"><span class="dot" style="background:#FF9900"></span>AWS EC2</span>
    <span class="pill"><span class="dot" style="background:#000"></span>Vercel</span>
    <span class="pill"><span class="dot" style="background:#009639"></span>nginx</span>
  </div>
</div>

<div class="stack-category">
  <p class="stack-category-name">Auth</p>
  <div class="stack-pills">
    <span class="pill"><span class="dot" style="background:#EB5424"></span>OAuth 2.0</span>
    <span class="pill"><span class="dot" style="background:#FFCD00"></span>Kakao</span>
    <span class="pill"><span class="dot" style="background:#03C75A"></span>Naver</span>
    <span class="pill"><span class="dot" style="background:#4285F4"></span>Google</span>
  </div>
</div>
```

  </div>
</section>

<!-- ══════ PROJECTS ══════ -->

<section class="container">
  <div class="reveal">
    <p class="section-label">// work</p>
    <h2 class="section-title">Projects</h2>
  </div>

  <!-- Project 1 -->

  <div class="project-card reveal">
    <div class="project-num">01</div>
    <span class="project-badge badge-live">● LIVE</span>
    <h3>할인꿀팁</h3>
    <p class="project-desc">위치 기반 할인 정보 O2O 플랫폼 — 반경 100m 이내 가맹점의 할인 정보를 실시간 푸시 알림으로 제공</p>

```
<div class="project-meta">
  <div class="meta-item">
    <p class="meta-label">Period</p>
    <p class="meta-value">2025.01 ~ 운영 중</p>
  </div>
  <div class="meta-item">
    <p class="meta-label">Team</p>
    <p class="meta-value">BE 1 + FE 1(본인) + 대표 1</p>
  </div>
  <div class="meta-item">
    <p class="meta-label">Investment</p>
    <p class="meta-value">정부 1 + 사설 2곳 유치</p>
  </div>
  <div class="meta-item">
    <p class="meta-label">Role</p>
    <p class="meta-value">백엔드 API + 프론트 3개 + 배포</p>
  </div>
</div>

<div class="project-tech">
  <span class="tech-tag">Flutter</span>
  <span class="tech-tag">React Native</span>
  <span class="tech-tag">React</span>
  <span class="tech-tag">Spring Boot</span>
  <span class="tech-tag">PostgreSQL</span>
  <span class="tech-tag">Cloud Run</span>
  <span class="tech-tag">FCM</span>
</div>

<p class="features-title">✨ 핵심 기능</p>
<ul class="feature-list">
  <li>카카오맵 기반 주변 매장 표시 + <strong>반경 100m 자동 푸시 알림</strong></li>
  <li>백그라운드 위치 추적 (60초 간격 → Haversine 거리 계산 → FCM 푸시)</li>
  <li>Android <strong>CustomFcmService.kt</strong> 네이티브 알림 / iOS Flutter onMessage 로컬 알림</li>
  <li>커스텀 "할인" 사운드 알림 + 매장별 쿠폰 코드 발급</li>
  <li>카카오·네이버 소셜 로그인 (OAuth 2.0)</li>
  <li>사장님 앱: 매장·할인 등록, 카카오 키워드 검색 (자동 좌표 변환)</li>
  <li>어드민 웹: 가맹점 승인/거절, 푸시 알림 통계 대시보드</li>
</ul>

<div class="achievement">🏆 3개 클라이언트 단독 개발 · 28명 실 가맹점 · 209개 매장 · 서울 전역 커버</div>

<button class="trouble-toggle" onclick="toggleTrouble(this)">
  🔧 트러블슈팅 보기 <span class="arrow">▾</span>
</button>
<div class="trouble-content">
  <div class="trouble-item">
    <p class="trouble-problem">iOS 포그라운드 알림 미작동</p>
    <p class="trouble-detail"><span class="cause">원인:</span> Android 전용 로직 플랫폼 미분기 → <span class="fix">해결:</span> Platform.isAndroid 조건 분기 + FCM 리스너 초기화 순서 변경</p>
  </div>
  <div class="trouble-item">
    <p class="trouble-problem">Google 지오코딩 좌표 오류</p>
    <p class="trouble-detail"><span class="cause">원인:</span> Google API 한국 주소 처리 부정확 → <span class="fix">해결:</span> Kakao API 전환, 주소+키워드 이중 전략</p>
  </div>
  <div class="trouble-item">
    <p class="trouble-problem">Vercel SPA 404</p>
    <p class="trouble-detail"><span class="cause">원인:</span> URL 직접 접속 시 라우팅 실패 → <span class="fix">해결:</span> vercel.json SPA rewrite + map.html 예외 처리</p>
  </div>
  <div class="trouble-item">
    <p class="trouble-problem">Cloud Run 403</p>
    <p class="trouble-detail"><span class="cause">원인:</span> 외부 요청 전체 차단 → <span class="fix">해결:</span> IAM allUsers → roles/run.invoker 추가</p>
  </div>
  <div class="trouble-item">
    <p class="trouble-problem">Expo SDK 버전 충돌</p>
    <p class="trouble-detail"><span class="cause">원인:</span> Expo Go(54) ↔ 프로젝트(52) 불일치 → <span class="fix">해결:</span> EAS Build 전환, 실기기 직접 빌드</p>
  </div>
</div>
```

  </div>

  <!-- Project 2 -->

  <div class="project-card reveal">
    <div class="project-num">02</div>
    <span class="project-badge badge-complete">✓ COMPLETE</span>
    <h3>IT-DA (잇다)</h3>
    <p class="project-desc">AI 기반 취미 커뮤니티 플랫폼 — 취미로 사람을 연결하는 AI 모임 매칭</p>

```
<div class="project-meta">
  <div class="meta-item">
    <p class="meta-label">Period</p>
    <p class="meta-value">2024.12 ~ 2025.02</p>
  </div>
  <div class="meta-item">
    <p class="meta-label">Team</p>
    <p class="meta-value">6명 (동원이와 구황작물들)</p>
  </div>
  <div class="meta-item">
    <p class="meta-label">Role</p>
    <p class="meta-value">User CRUD, 채팅, 팔로우, 뱃지, 알림</p>
  </div>
</div>

<div class="project-tech">
  <span class="tech-tag">React 18</span>
  <span class="tech-tag">TypeScript</span>
  <span class="tech-tag">Spring Boot</span>
  <span class="tech-tag">MySQL</span>
  <span class="tech-tag">Redis</span>
  <span class="tech-tag">WebSocket</span>
  <span class="tech-tag">FastAPI</span>
  <span class="tech-tag">AWS EC2</span>
  <span class="tech-tag">Docker</span>
</div>

<p class="features-title">✨ 핵심 기능</p>
<ul class="feature-list">
  <li>WebSocket/STOMP 기반 <strong>1:1 실시간 채팅</strong> (카카오톡 스타일, 읽음 처리, 자동 재연결)</li>
  <li>AI 장소 추천: 참여자 주소 → 중간 지점 계산 → 카카오 장소 API → 상위 3곳 추천</li>
  <li><strong>Redis 세션 관리</strong>: JWT 대신 Redis Session (즉시 로그아웃, 강제 세션 만료)</li>
  <li>팔로우/언팔로우 + 비공개 계정 팔로우 요청/수락 (WebSocket 실시간 알림)</li>
  <li><strong>뱃지 시스템</strong>: 125개 뱃지, 모임 참여 횟수 기반 자동 부여</li>
  <li>소셜 로그인: 카카오, 네이버, 구글 OAuth 2.0</li>
</ul>

<button class="trouble-toggle" onclick="toggleTrouble(this)">
  🔧 트러블슈팅 보기 <span class="arrow">▾</span>
</button>
<div class="trouble-content">
  <div class="trouble-item">
    <p class="trouble-problem">회원가입 복합 버그 4종</p>
    <p class="trouble-detail"><span class="cause">원인:</span> DTO-Entity 매핑 누락, 비번 평문 저장, 좌표 null, 카카오 500 → <span class="fix">해결:</span> Postman 추적 + @Builder + BCrypt + GeocodingService</p>
  </div>
  <div class="trouble-item">
    <p class="trouble-problem">크롬↔사파리 팔로우 알림 불가</p>
    <p class="trouble-detail"><span class="cause">원인:</span> WebSocket 구독 경로 불일치 → <span class="fix">해결:</span> 구독 경로 정규화 + 브라우저별 테스트</p>
  </div>
  <div class="trouble-item">
    <p class="trouble-problem">채팅 읽음 "1" 안 사라짐</p>
    <p class="trouble-detail"><span class="cause">원인:</span> markAsRead 브로드캐스트 누락 → <span class="fix">해결:</span> 읽음 이벤트 양방향 전송 로직 추가</p>
  </div>
  <div class="trouble-item">
    <p class="trouble-problem">CORS + 세션 쿠키 문제</p>
    <p class="trouble-detail"><span class="cause">원인:</span> Cross-Origin 쿠키 전달 불가 → <span class="fix">해결:</span> SessionConfig Domain 제거 + withCredentials 설정</p>
  </div>
</div>
```

  </div>

  <!-- Project 3 -->

  <div class="project-card reveal">
    <div class="project-num">03</div>
    <span class="project-badge badge-complete">✓ COMPLETE</span>
    <h3>구구마켓</h3>
    <p class="project-desc">중고거래 플랫폼 (SPA) — 위치 기반 지도 검색 + 실시간 채팅</p>

```
<div class="project-meta">
  <div class="meta-item">
    <p class="meta-label">Period</p>
    <p class="meta-value">2024.09 ~ 2024.11</p>
  </div>
  <div class="meta-item">
    <p class="meta-label">Team</p>
    <p class="meta-value">6명</p>
  </div>
  <div class="meta-item">
    <p class="meta-label">Role</p>
    <p class="meta-value">카카오맵, 소셜 로그인, 등급제, DB 설계</p>
  </div>
</div>

<div class="project-tech">
  <span class="tech-tag">React 18</span>
  <span class="tech-tag">Zustand</span>
  <span class="tech-tag">Spring Boot</span>
  <span class="tech-tag">JPA</span>
  <span class="tech-tag">MySQL</span>
  <span class="tech-tag">WebSocket</span>
  <span class="tech-tag">Kakao Map API</span>
</div>

<p class="features-title">✨ 핵심 기능</p>
<ul class="feature-list">
  <li>카카오맵 기반 <strong>반경 km + 가격 필터링</strong> 주변 상품 마커 표시</li>
  <li>WebSocket/STOMP 1:1 채팅 (0초 지연 실시간 메시지)</li>
  <li><strong>회원 등급제</strong>: 거래 횟수 기반 알→아기새→성조 자동 승급 (Enum)</li>
  <li>실시간 알림: 찜하기, 댓글 알림 (unread count 표시)</li>
  <li>카카오 소셜 로그인 (OAuth 2.0)</li>
</ul>

<button class="trouble-toggle" onclick="toggleTrouble(this)">
  🔧 트러블슈팅 보기 <span class="arrow">▾</span>
</button>
<div class="trouble-content">
  <div class="trouble-item">
    <p class="trouble-problem">지도 연속 클릭 시 앱 튕김</p>
    <p class="trouble-detail"><span class="cause">원인:</span> 마커 클릭 이벤트 중복 발생 → <span class="fix">해결:</span> debouncing(300ms) 적용</p>
  </div>
  <div class="trouble-item">
    <p class="trouble-problem">MVC → SSR 전환 충돌</p>
    <p class="trouble-detail"><span class="cause">원인:</span> 아키텍처 변경 시 라우팅 충돌 → <span class="fix">해결:</span> React Router v6 + SPA 구조로 재설계</p>
  </div>
</div>
```

  </div>
</section>

<!-- ══════ EDUCATION ══════ -->

<section class="container">
  <div class="reveal">
    <p class="section-label">// education</p>
    <h2 class="section-title">Education</h2>

```
<div class="edu-item">
  <span class="edu-year">2024</span>
  <div class="edu-info">
    <h4>하이미디어 아카데미</h4>
    <p>풀스택 개발 과정 수료</p>
  </div>
</div>
<div class="edu-item">
  <span class="edu-year">—</span>
  <div class="edu-info">
    <h4>로이문화예술실용전문학교</h4>
    <p>이벤트기획과</p>
  </div>
</div>
```

  </div>
</section>

<!-- ══════ FOOTER ══════ -->

<footer class="container">
  <p class="quote">"코드 한 줄이 세상을 바꿀 수 있다고 믿습니다."</p>
  <p class="copy">© 2025 김보민 · Built with passion</p>
</footer>

<script>
function toggleTrouble(btn) {
  const content = btn.nextElementSibling;
  btn.classList.toggle('open');
  content.classList.toggle('open');
}

// Scroll reveal
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>

</body>
</html>