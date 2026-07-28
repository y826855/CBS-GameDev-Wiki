# Google Sheet Loader 개발 기록

원본 작업 메모에 남아 있던 TODO, 완료 표시, 질문, 오류 기록을 시기와 주제에 따라 정리했습니다.

## 초기 Parser와 Fetcher 구조

> 2026년 4월 17일

초기 구조는 에셋 생성, 데이터 파싱, HTTP 요청의 책임을 다음과 같이 분리했습니다.

- `FAssetGenerationHelper`: 지정한 경로에 에셋 생성
- `GoogleSheetParserBase`: 데이터 파싱을 담당하는 부모 객체
  - `ItemDataParser`: 아이템 형태로 데이터 파싱
- `GoogleSheetFetcher`: HTTP 요청 처리

Widget에서 Subsystem을 호출할 때는 `Event Pre Construct`를 사용해야 합니다. 일반 `Construct`에서 호출하면 초기화 순서로 인해 오류가 발생했습니다.

## Data Table과 Asset 자동 생성

> 2026년 4월 17일

### 당시 구현 목표

1. Google Sheet 데이터를 가져오는 클래스 제작
2. 골드 및 상점 시스템 구현
   - 상점 NPC와 가까이 있을 때 상호작용
   - 상점 UI 구성

테스트에 사용한 Paper Sprite 경로:

```text
/Script/Paper2D.PaperSprite'/Game/WorkSpace/Item/Texture/ItemAtlas_Item_Icon_0'
```

### 확인이 필요했던 문제

- Data Table 자동 생성
- Data Table 내부 값이 초기화되지 않는 현상
- Parser 클래스 생성 시 `Init`을 통해 값 주입

`DataTableRowHandle`을 사용하면 다른 Data Table에서 Row 값을 참조할 수 있습니다.

게임의 Asset Manager에는 Blueprint Subsystem으로 등록한 객체를 함께 등록하는 방안을 검토했습니다.

## 플러그인 개선 목표

> 2026년 5월 6일

Google Sheet 데이터 로드 기능을 플러그인으로 분리하기 위해 다음 항목을 검토했습니다.

- 플러그인 사용 방법 확인
- JSON 데이터 파싱
- OAuth 연동 시도
- 기존 기능의 플러그인화

### 필요한 기능

1. 여러 페이지를 로드할 수 있도록 페이지 정보를 복수로 등록
2. 에셋 데이터 자동 추가
   - 기존 구현을 활용하되 저장 위치 지정 방식 개선
3. 성공과 실패 여부를 더 명확하게 전달

## Parsing 개선

> 2026년 7월 3일 전후로 추정

### 완료한 작업

- 폴더 구조 수정
- 파싱 로직을 함수로 분리
- 문서 작성

### 추가 개선 사항

- 데이터의 첫 행을 Header로 변환하는 로직 수정
- 세 개로 나뉜 Data Asset을 하나로 통합

## Asset Bundle 설계

> 2026년 7월 6일 전후로 추정

상점과 Gameplay에서 사용하는 에셋의 수명 주기를 분리하기 위해 Asset Bundle 구성을 검토했습니다.

### 상점 UI에서 필요한 흐름

1. 선택지에서 Ball과 UI 에셋을 로드
2. 선택한 Ball을 획득
3. 상점을 벗어날 때 상점에서만 사용한 Ball 에셋을 언로드

에셋은 약 20개이며 `UI`, `Shop`, `Gameplay` Bundle로 구분하는 방안을 고려했습니다. 하나의 에셋에 `("UI", "Gameplay")`처럼 여러 Bundle을 지정하는 방식도 검토했습니다.

### 검토가 필요했던 부분

- 필요한 클래스를 Bundle로 구성하는 방법
- Bundle이 중첩될 때 Load와 Unload를 처리하는 방법
- 플레이어 보유 Ball과 상점에서 임시로 로드한 Ball을 구분하는 방법

전투 UI에는 다음 정보가 필요했습니다.

- 범퍼 타격 횟수
- 체력과 MP
- 골드와 현재 층

Table Subsystem에서는 Developer Settings에 등록된 값을 읽어 저장하도록 설계했습니다.
