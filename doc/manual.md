# 아이하나 교회 (Ihana Church) 홈페이지 제작 매뉴얼

본 문서는 해외한인장로회(KPCA) 소속 **아이하나 교회**의 공식 홈페이지 구축 및 운영을 위한 제작 매뉴얼입니다.

---

## 1. 기술 스택 및 환경
* **Static Site Generator**: Hugo (v0.150.0 이상 권장, extended 버전 필요)
* **Theme**: [Adritian Free Hugo Theme](https://github.com/zetxek/adritian-free-hugo-theme)
* **Styling**: Bootstrap 5.3 (SCSS), Custom Vanilla CSS (`assets/css/custom.css`)
* **Package Manager**: npm

---

## 2. 프로젝트 디렉토리 구조
```text
ihana/
├── assets/
│   └── css/
│       └── custom.css       # 웹사이트 커스텀 스타일 정의 (컬러 테마 등)
├── content/                 # 각 페이지별 마크다운 콘텐츠
│   ├── about/               # 교회 소개 page
│   ├── worship/             # 예배 안내 page
│   ├── sermons/             # 설교/말씀 page
│   ├── location/            # 오시는 길 page
│   ├── giving/              # 헌금 안내 page
│   ├── prayer/              # 기도 요청 page
│   ├── contact/             # 문의하기 page
│   └── _index.md            # 메인 홈 화면 설정
├── doc/
│   ├── manual.md            # 본 제작 매뉴얼
│   └── trouble_report.md    # 문제 해결 리포트
├── themes/
│   └── adritian/            # Adritian 테마 소스 (Git Submodule)
├── hugo.toml                # Hugo 환경 설정 파일
└── package.json             # npm 패키지 및 개발 스크립트 설정
```

---

## 3. 핵심 구성 정보
### A. Mount 설정 (`hugo.toml`)
Adritian 테마와 Bootstrap SCSS/JS 및 로컬 자산을 매핑하기 위해 `hugo.toml` 내 `[[module.mounts]]` 설정을 사용합니다.
* Bootstrap의 SCSS 경로와 JS 경로가 `node_modules`로부터 `assets/scss/bootstrap` 및 `assets/js/bootstrap`으로 바인딩되어 있어, 테마가 빌드될 때 이를 참조합니다.
* 프로젝트 루트의 `archetypes`, `assets`, `i18n`, `layouts`, `static` 등의 폴더가 테마 내부 폴더보다 우선하도록 이중 마운트되어 있습니다.

### B. 멀티페이지 전환 및 네비게이션
기본 Adritian 테마는 Single Page형 랜딩 페이지 레이아웃을 가지지만, 이 프로젝트는 다중 페이지(Multi-page) 구조로 전환되어 있습니다.
* 각 서브 디렉토리(`about`, `worship` 등) 하위의 `_index.md` 구조로 빌드하여 독립적인 라우팅 주소(`/about/`, `/worship/` 등)를 생성합니다.
* `hugo.toml`의 `[languages.ko.menus]` 섹션에 등록된 헤더 메뉴 구조를 통해 각 페이지 간 유기적인 이동을 처리합니다.

---

## 4. 로컬 개발 및 빌드 명령어
프로젝트 루트 폴더에서 아래 명령어들을 수행합니다.

### A. 의존성 설치
테마가 요구하는 Bootstrap 및 CSS 빌드 도구들을 설치합니다.
```bash
npm install
```

### B. 로컬 개발 서버 구동
코드 수정 사항을 실시간 반영(Live Reload)하는 로컬 서버를 켭니다.
```bash
npm run start
# 또는 직접 실행:
hugo server
```
* 기본적으로 `http://localhost:1313/`로 실행되나, 1313 포트가 사용 중일 경우 비어 있는 랜덤 포트로 실행됩니다. 서버 로그의 URL을 확인하세요.

### C. 프로덕션 빌드
배포용 정적 파일 생성 및 경량화(Minify)를 수행합니다. 생성물은 `public/` 디렉토리에 저장됩니다.
```bash
npm run build
# 또는 직접 실행:
hugo --minify
```

---

## 5. 작업 히스토리 (Changelog)
프로젝트 내 기능 추가 및 변경 이력입니다. *새로운 작업 완료 시 이 섹션 아래에 자동으로 이력이 추가됩니다.*

<!-- changelog-start -->
### 2026-07-20: plan.md 수정 (Commit: 92433e7)
* **작업자**: 내이름
* **내용**: (상세 내용 없음)


### 2026-07-13: 첫 푸시 (Commit: 6532ac9)
* **작업자**: 내이름
* **내용**: (상세 내용 없음)


### 2026-07-13: 디자인 수정 (Commit: 03de875)
* **작업자**: 내이름
* **내용**: (상세 내용 없음)


### 2026-07-06: 공통 푸터 폼 제거 및 오시는 길 접속자 실시간 위치 기반 길찾기 연동
* **작업자**: Antigravity (AI Agent)
* **내용**:
  * 공통 푸터 마크다운(`content/footer/footer.md` 및 `footer.es.md`) 파일에서 모든 페이지 하단에 붙어 나오던 공통 `'Reach out'` 문의 폼 영역(`contact-section` 쇼트코드)을 완벽히 제거.
  * '문의하기' 페이지(`content/contact/_index.md`)에 개별 설계된 전용 상담/문의 폼만 단독 작동되게 하여 폼 중복 노출 문제를 해소.
  * '오시는 길' 페이지(`content/location/_index.md`)의 외부 길찾기 링크를 구글 맵 Directions API(`origin=My+Location`)로 연동하여 클릭 시 현재 위치에서 교회까지의 길찾기 경로가 자동 연출되도록 변경.
  * '오시는 길' 페이지 하단에 브라우저 HTML5 Geolocation API 기반 자바스크립트 로직을 이식하여, 접속자가 기기 위치 정보 권한 수락 시 내부 `<iframe>` 구글 지도가 `[접속자 위치 &rarr; 교회 주소]`의 실시간 최적 이동 경로 지도로 자동 갱신되도록 개선(권한 미수락 시에는 기존 포트리 교회 단독 마커 지도로 안전하게 Fallback).

### 2026-07-06: 교회 로고 벡터화 디지털 복원 및 메뉴바 적용 (브랜드 텍스트 추가)
* **작업자**: Antigravity (AI Agent)
* **내용**:
  * 사용자가 업로드한 삐뚤어지고 노이즈가 있던 원본 로고 이미지를 대칭과 여백이 보정된 미려한 벡터 그래픽(`static/img/logo.svg`)으로 디지털 복원 및 제작.
  * `i18n/ko.yaml` 언어 파일을 오버라이드하여 기존 "Adritian 데모" 문구를 지우는 대신, 로고 옆에 선명하게 노출될 새 브랜드 텍스트인 `"IHANA CHURCH"` 를 추가.
  * `hugo.toml` 메인 params 스코프에 `logo = '/img/logo.svg'` 설정 적용 (person 하위 스코프에 묶이던 버그 해결).
  * 테마 헤더 템플릿(`themes/adritian/layouts/partials/header.html`) 내 로고 경로 지정을 `absURL`에서 `relURL`로 수정하여 로컬 개발 환경(`localhost`)에서도 깨지지 않고 잘 로드되도록 조치.
  * `custom.css`에 메뉴바 전용 로고 크기 조율(`.navbar-brand .logo`) 스타일 및 시스템 다크 테마 전환 시 로고 색상을 자동으로 반전시키는 CSS 필터 효과 및 다크 테마 메뉴바 배경색 스타일 보강.
  * `custom.css`에 로고 옆 브랜드 텍스트 전용 타이포그래피 스타일(`.navbar-brand span`)을 선언하고, 라이트/다크 모드별 전용 컬러 및 자간 설정을 부여하여 일체감 있는 헤더 브랜딩 구현.

### 2026-07-06: 홈페이지 첫 화면 안내 콘텐츠 추가 및 레이아웃 수정
* **작업자**: Antigravity (AI Agent)
* **내용**:
  * `content/_index.md`에 `type: "home"` 프런트매터를 명시하여 홈페이지 템플릿과의 연동이 올바르게 작동하도록 해결.
  * 기존 Tailwind CSS 클래스로 작성되어 깨지던 메인 화면 구조를 Bootstrap 5 그리드 및 카드로 재구축.
  * 교회를 대표하는 깔끔한 연파랑 단색 히어로 배너 영역 추가 및 "조용한 위로와 회복의 자리" CTA 버튼 연동.
  * 주일 예배 일정을 요약한 '예배 시간 안내' 카드 컴포넌트 추가.
  * 주소 및 주차/교통 안내 요약과 함께 반응형 구글 지도(Google Map)를 직접 임베드한 '오시는 길' 카드 추가.
  * `assets/css/custom.css`에 홈페이지 전용 레이아웃 덮어쓰기(`.home-container`), 히어로 단색 배경, 카드 디자인 토큰 선언.
  * **추가 개선**: 스티키 헤더 메뉴바와의 텍스트 겹침 방지를 위해 히어로 영역의 상단 여백(`padding-top`)을 대폭 확대(240px)하고 z-index 오작동 버그를 해결했습니다. 이때 Bootstrap의 `py-5` 유틸리티가 `custom.css`를 덮어쓰고 있던 우선순위 충돌 문제를 파악하여 마크업에서 `py-5`를 제거함으로써 여백 스타일이 온전히 적용되도록 완료했습니다.

### 2026-06-29: Convert landing page layout to multi-page navigation and fix code block rendering on all subpages (Commit: e46faca)
* **작업자**: Gihyun Park
* **내용**: (상세 내용 없음)


### 2026-06-29: Initial Commit
* **작업자**: Gihyun Park
* **내용**:
  * Adritian Hugo 테마를 기반으로 아이하나 교회 웹사이트 셋업.
  * 기획서(`plan.md`) 스펙에 맞춰 `about`, `worship`, `prayer`, `giving` 등의 기초 마크다운 콘텐츠 생성 및 연동.
  * 오시는 길 페이지의 지도 내 HTML 들여쓰기 버그 수정.
  * 기본 CSS 커스터마이징 구조 마련 (`assets/css/custom.css`).

### 2026-06-29: 멀티페이지 네비게이션 전환 및 렌더링 수정
* **작업자**: Gihyun Park
* **내용**:
  * 단일 페이지(Single Page) 랜딩 레이아웃에서 다중 페이지(Multi-page) 메뉴 이동 구조로 전환.
  * 모든 서브 페이지의 마크다운 내 코드 블록 렌더링 오작동 문제 해결.
  * `hugo.toml` 내 다국어 메뉴 경로 구조 재설정.
<!-- changelog-end -->
