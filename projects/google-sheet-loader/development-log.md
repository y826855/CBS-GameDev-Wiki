# Google Sheet Loader 작업 일지

플러그인 저장소의 `dev` 브랜치 커밋을 기준으로 날짜별 작업을 정리했습니다. Merge Commit은 제외했으며, 플러그인 작업 특성상 기록 사이에 시간 간격이 있습니다.

## 2026년 5월 8일

- Unreal Engine 테스트 프로젝트와 Google Sheet Loader 플러그인의 초기 구조를 생성했습니다.
- HTTP를 통해 Sheet 데이터를 가져오는 기능을 구현했습니다.
- 가져온 데이터를 프로젝트에 맞게 처리할 수 있도록 Parser Base와 Item Data Parser를 구현했습니다.
- Sheet 설정을 저장하는 Data Asset과 Details Customization을 추가했습니다.
- 임시 Sheet, Struct, Data Asset, Data Table 및 Sprite를 구성해 파싱과 에셋 생성을 테스트했습니다.
- 자동 생성된 Data Asset을 확인하고 README와 MIT License를 작성했습니다.

관련 커밋: `f9d6c3c`, `69bd386`, `f4692c5`, `f8254af`, `5f2e634`, `05953d6`, `381ed9e`, `1f234f3`, `a9f8daf`

## 2026년 5월 25일

- Sheet 데이터를 불러오는 동안 진행 상태를 보여주는 Progress 창을 추가했습니다.
- 진행 중인 작업을 취소할 수 있도록 처리했습니다.
- 데이터 갱신 이후 자동 저장하는 기능을 추가했습니다.
- 모든 Google Sheet Config를 한 번에 확인하는 Dashboard를 제작했습니다.
- `Tools → GoogleSheet Dashboard`에서 여러 Config를 한 번에 갱신할 수 있도록 구성했습니다.
- 플러그인용 `.gitignore`를 정리했습니다.

관련 커밋: `dff1d19`, `7942b46`, `440de49`

## 2026년 6월 4일

- Google Sheet Config에 빈 값이나 `None` 값이 있을 때 발생하던 Crash를 예외 처리했습니다.
- 플러그인 소개와 사용 방법을 문서화했습니다.

관련 커밋: `2865ffe`, `2c60044`

## 2026년 7월 2일

- 파싱이 끝난 뒤 `ParsedRow` 데이터를 비우도록 수정했습니다.
- Slate UI의 List와 Lambda가 `UObject`의 Raw Pointer를 직접 보관하던 문제를 수정했습니다.
- Parser에서 데이터 경로를 지정할 때 Unreal Content Browser의 폴더 선택기를 사용할 수 있도록 예제를 변경했습니다.
- README를 보완하고 Google Sheet Loader 아이콘을 추가했습니다.
- 플러그인 버전을 `1.1`에서 `1.1.1`로 올렸습니다.

관련 커밋: `fd76352`, `3fd42a1`, `c507b44`, `ca25bce`, `29177b2`, `dec2f6c`, `7ed38cb`, `f9f7667`
