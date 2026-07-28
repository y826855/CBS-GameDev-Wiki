# Google Sheet Loader

Google Sheet 데이터를 Unreal Engine 프로젝트에서 사용할 수 있도록 불러오고, 파싱과 에셋 생성을 자동화하기 위해 진행한 작업입니다.

초기에는 프로젝트 내부 기능으로 Parser와 Fetcher를 구현했습니다. 이후 여러 시트 지원, Data Table 및 Data Asset 생성, 비동기 에셋 로드까지 고려하며 플러그인 구조로 개선했습니다.

## 문서 구성

- [개발 기록](development-log.md): 초기 구조, 개선 목표, 파싱 리팩터링과 Asset Bundle 설계 메모
- [프로젝트 적용 이력](integration-history.md): 실제 Git 커밋을 기준으로 정리한 기능 적용 및 변경 기록
