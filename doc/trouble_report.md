# 아이하나 교회 (Ihana Church) 프로젝트 문제 해결 리포트 (Trouble Report)

본 문서는 프로젝트 진행 과정에서 발생한 버그, 성능 이슈, 설정 충돌 현상에 대한 원인 분석 및 해결 방법과 현재 존재하는 잠재적인 이슈(경고) 진단 결과를 정리한 문서입니다.

---

## 1. 해결된 이슈 내역 (Resolved Issues)

### A. 오시는 길 지도 HTML 들여쓰기 렌더링 오류
* **현상**: `content/location/_index.md` 등에서 Google Map의 iframe 소스 코드를 마크다운에 주입했을 때, 템플릿 렌더러가 들여쓰기를 오인하여 일반 텍스트나 원시 코드로 노출되거나 레이아웃이 붕괴되는 현상 발생.
* **원인**: Hugo의 마크다운 렌더러(Goldmark)는 들여쓰기가 적용된 HTML 요소를 코드 블록이나 일반 텍스트 문단으로 처리하는 속성이 있음.
* **해결책**:
  * 마크다운 내에 원시 HTML/iframe을 삽입할 때, 시작 및 끝 태그에 불필요한 앞 공백(들여쓰기)을 모두 제거하여 라인의 첫 칸부터 시작하도록 코드 정렬 수정.
  * `hugo.toml`에 `[markup.goldmark.renderer]` 하위 `unsafe = true` 옵션이 켜져 있는지 교차 확인.

### B. 서브 페이지 코드 블록 및 레이아웃 렌더링 오류
* **현상**: 단일 랜딩 페이지에서 다중 페이지(About, Worship 등) 레이아웃으로 변경하는 과정에서, 마크다운 콘텐츠 내부의 코드 구문 및 마크다운 기호가 의도와 다르게 렌더링되어 페이지가 깨지는 현상.
* **원인**: 테마 기본 템플릿의 섹션 렌더링 로직이 단일 페이지(Single page anchors) 중심이었기 때문에, 마크다운 내의 서식들이 템플릿과 결합하면서 구문 분석 에러를 야기함.
* **해결책**:
  * 서브 페이지들의 마크다운 파일 구성 형식을 개별 `_index.md` 파일 기반으로 통일.
  * 내부에 잔존하던 잘못된 문법 지시자나 테마 전용 숏코드 사용법을 디버깅하고 템플릿이 수용 가능한 순수 마크다운으로 재작성.

---

## 2. 현재 발생 중인 시스템 경고 및 대응 방안 (Active Warnings)

현재 로컬 개발 서버(`npm run start`) 실행 시 콘솔에 발생하는 경고 및 이를 해결하기 위한 지침입니다.

### A. 포트 충돌 및 대안 포트 실행 (Port 1313 occupied)
* **현상**: `port 1313 already in use, attempting to use an available port` 경고와 함께 다른 포트(예: 59792)로 서버가 실행됨.
* **원인**: 백그라운드에서 실행 중인 이전 Hugo 서버 인스턴스 또는 다른 프로세스가 기본 포트인 1313을 점유하고 있음.
* **해결책**:
  1. 포트를 점유 중인 프로세스의 PID(프로세스 ID)를 확인합니다.
     ```bash
     lsof -i :1313
     ```
  2. 조회된 PID를 강제 종료합니다.
     ```bash
     kill -9 <PID>
     ```
  3. 이후 로컬 서버를 재실행하면 정상적으로 `localhost:1313`을 사용할 수 있습니다.

### B. Unknown kind "footer" 경고
* **현상**: `WARN Unknown kind "footer" in outputs configuration.` 발생.
* **원인**: `hugo.toml` 설정 파일 17라인 부근에 `footer = []` 정의가 있으나, Hugo에서 지원하는 내장 Page Kind 종류(page, home, section, taxonomy, term 등)에 "footer"는 존재하지 않기 때문에 발생함.
* **해결책**:
  * `hugo.toml` 17라인의 `footer = []` 설정을 주석 처리하거나 제거해도 동작에 문제가 없다면 제거하는 방향으로 리팩토링 권장.

### C. Hugo 버전 업데이트에 따른 Deprecated 경고들
* **현상**:
  * `WARN deprecated: .Language.LanguageDirection was deprecated in Hugo v0.158.0... Use .Language.Direction instead.`
  * `WARN deprecated: .Site.Data was deprecated in Hugo v0.156.0... Use hugo.Data instead.`
  * `WARN deprecated: .Site.LanguageCode was deprecated in Hugo v0.158.0... Use .Site.Language.Locale instead.`
* **원인**: 현재 설치된 Hugo 버전(v0.163.0 이상)의 규격이 올라갔으나, `themes/adritian` 테마 내부에 작성된 기존 변수 선언 방식들이 이전 버전 스펙에 머물러 있어 발생함.
* **해결책**:
  1. 테마 소스코드를 직접 수정하는 대신, 템플릿 재정의(Override) 방식을 사용하여 `layouts/` 디렉토리 내에 경고를 발생시키는 템플릿(예: 헤더, 푸터 파일 등)을 복제한 뒤 변수명을 최신 규격으로 교체합니다.
  2. 또는 테마 업스트림(`adritian-free-hugo-theme`)의 업데이트가 있다면 서브모듈을 최신 버전으로 갱신합니다.
     ```bash
     git submodule update --remote --merge
     ```
