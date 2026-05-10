# USANA 모바일 명함 (v2) · Cloudflare Pages 배포 가이드

하루허니 디자인 시스템을 기반으로 제작한 USANA 브랜드파트너 모바일 명함입니다.
크림 베이지 + 잉크 다크 + 골드 액센트의 따뜻하고 전문적인 톤.

---

## 📁 파일 구성

```
usana-mobile-card/
├── index.html          ← 명함 메인 페이지 (단일 HTML, 자급자족형)
├── assets/
│   └── portrait.jpg    ← 대표님 프로필 사진
├── _headers            ← Cloudflare Pages 캐시·보안 헤더
├── robots.txt          ← 검색엔진 크롤링 허용
└── README.md           ← 이 파일
```

---

## 🚀 Cloudflare Pages 배포 (3분이면 끝)

1. https://dash.cloudflare.com 로그인
2. 좌측 메뉴 **Workers & Pages** → **Create application** → **Pages** 탭 → **Upload assets** 클릭
3. 프로젝트 이름 입력 (예: `usana-card` → 자동으로 `usana-card.pages.dev` 주소 생성)
4. 이 ZIP 파일을 그대로 업로드하거나, 압축을 풀어서 **폴더 안의 모든 파일과 하위 폴더**를 드래그&드롭
5. **Deploy site** 클릭
6. 1~2분 후 배포 완료. 발급된 `.pages.dev` 주소를 클릭해서 확인

---

## 📦 섹션 구성

1. **HERO** — 인물사진을 배경 비주얼로, 영문 메인 헤드라인(Cormorant Garamond) + 한글 슬로건 + SCROLL 인디케이터
2. **ABOUT** — 짧은 자기소개 + 인물사진 스토리 카드(YOUR PARTNER 뱃지 + 캡션 + 인용구)
3. **CONNECT** — 카톡, 전화, 인스타, 유튜브, 유사나 사이트 5개 채널 (LinkTree 스타일)
4. **WHY USANA** — 통계 3카드(30+/25국/150+) + 인증 도장(FDA/NSF/USP/PDR) + 차별점 6가지
5. **USANA ATHLETES** — 다크 카드, 이정후 선수 + 후원팀 태그
6. **FOR YOU** — 4가지 추천 대상 (건강루틴/활력에너지/영양밸런스/사업기회)
7. **START NOW** — 메인 CTA(카톡 1:1 상담) + 보조 CTA(공식 사이트) + 오픈마켓 경고
8. **CONTACT** — 다크 잉크 배경, 전화·이메일·주소·운영시간 + 푸터

---

## ✏️ 배포 전 채워넣을 부분 (`index.html` 편집)

메모장이나 VS Code로 `index.html`을 열고, Ctrl+F / Cmd+F 로 검색해서 교체하세요.

### ① 대표님 성함
- 검색: `대표님 성함` → 본인 이름

### ② 전화번호
- 검색: `01000000000` → 본인 번호 (-없이, `tel:` 링크용)
- 검색: `010-0000-0000` → 화면에 표시되는 번호

### ③ 이메일
- 검색: `partner@usana.example` → 본인 이메일 (2곳)

### ④ 주소
- 검색: `서울특별시 (지역 입력)` → 본인 활동 지역

### ⑤ 카카오톡 채널 URL
- 검색: `class="channel-icon kakao"` 와 그 다음 `class="order-btn"`의 카톡 버튼
- 각 `href="#"` 부분을 카톡 채널 URL로 교체 (예: `https://pf.kakao.com/_xxxxx/chat`)

### ⑥ 인스타그램·유튜브·유사나 사이트
- CONNECT 섹션에서 각 채널의 `href="#"`를 본인 링크로
- 인스타: `@your_handle`도 실제 핸들로 교체

### ⑦ 프로필 사진 교체하고 싶으면
- `assets/portrait.jpg` 파일을 같은 이름으로 덮어쓰기
- 권장: 정사각형, 1200×1200px 이상, 1MB 이하

### ⑧ 메인 카피 톤 조정
- HERO 헤드라인: `TRUE HEALTH` / `EVERY DAY` (영문 디스플레이)
- ABOUT 인용구: `"건강은 약속이고..."` 등은 본인 톤에 맞게 자유롭게

---

## 🌐 본인 도메인 연결 (선택사항)

1. Pages 프로젝트 → **Custom domains** → **Set up a custom domain**
2. 도메인 입력 후 안내에 따라 DNS 설정
3. 5~10분 후 SSL 인증서까지 자동 적용

---

## 🎨 디자인 특징

- **모바일 전용** (최대 폭 480px, iPhone safe-area 대응)
- **Pretendard Variable** (한글) + **Cormorant Garamond** (영문 디스플레이)
- 컬러 팔레트: `#FBF7EE` 크림 / `#2A1F12` 잉크 / `#C8941E` 골드
- IntersectionObserver 기반 부드러운 등장 효과
- iOS 사파리 safe-area 흰띠 방지 (html/body 다크 배경)

---

## 🔄 명함 내용 수정 후 재배포

1. `index.html` 수정
2. Cloudflare Pages 프로젝트 → **Create deployment** → 파일 다시 업로드
3. 즉시 새 버전 적용 (이전 버전도 보존됨)

---

## ❓ 자주 묻는 질문

**Q. 무료인가요?**
A. 네. Cloudflare Pages는 개인 프로젝트 기준 무료이고, 트래픽 제한도 사실상 없습니다.

**Q. 카톡 공유 시 미리보기 사진이 안 떠요.**
A. 카카오톡은 미리보기를 캐싱합니다. https://developers.kakao.com/tool/clear/og 에서 캐시 초기화 후 다시 시도하세요.

**Q. 폰트가 깨져 보여요.**
A. 인터넷 연결 시 Pretendard와 Cormorant Garamond가 CDN에서 자동 로드됩니다. 오프라인에서는 시스템 기본 폰트로 폴백됩니다.

---

문의/수정 요청은 작업한 분께 연락주세요.
