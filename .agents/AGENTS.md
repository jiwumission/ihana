# 아이하나 교회 프로젝트 규칙 (Project-Scoped Rules)

> [!IMPORTANT]
> 이 프로젝트에서 소스 코드 변경, 페이지 추가/수정, 또는 버그 수정을 완료한 후에는 반드시 문서들을 자동 업데이트해야 합니다.

## 자동 업데이트 지침 (Auto-Update Guidelines)

1. **작업 이력 기록 (`doc/manual.md`)**:
   - 어떤 작업이 완료되면, 반드시 `doc/manual.md` 파일의 `## 5. 작업 히스토리 (Changelog)` 섹션 아래 (`<!-- changelog-start -->`와 `<!-- changelog-end -->` 사이)에 작업 날짜, 작업자(Agent), 작업 내용을 기록해야 합니다.
   - 기록 형식 예시:
     ```markdown
     ### YYYY-MM-DD: [요약 제목]
     * **작업자**: Antigravity (AI Agent)
     * **내용**:
       * 세부 내용 1
       * 세부 내용 2
     ```

2. **문제 상황 기록 (`doc/trouble_report.md`)**:
   - 개발 혹은 빌드 중 발생한 오류나 경고를 해결했을 경우, `doc/trouble_report.md` 파일에 버그 해결 사례로 추가 기록해야 합니다.
   - 예외 상황이나 문제 진단에 대한 세부 사항도 리포트에 반영하십시오.
