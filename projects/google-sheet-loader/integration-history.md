# Google Sheet Loader 프로젝트 적용 이력

Google Sheet Loader를 프로젝트에 적용하고 데이터 및 에셋 로드 구조를 개선한 내역입니다. 작성자 `cbs`의 Git 커밋을 기준으로 정리했으며 Merge Commit은 제외했습니다.

## 2026년 7월 3일

- `731b7d78` Google Sheet Loader 플러그인 추가
- `03504350` 범퍼 Blueprint 내부 이름 변경 및 테스트용 에셋 생성
  - `summon`을 `Effect`로 변경
- `cd844890` 범퍼 관련 Struct 데이터 분리
  - 범퍼, 트리거, 이펙트용 Data Asset 생성
- `0763c185` Editor Module과 데이터 Parser 추가
  - Editor에서 데이터 Parser 관리
- `f8e09ad7` Data Table을 관리하는 Developer Settings 클래스 추가
  - 등록된 Table의 Row를 검색하는 Subsystem 추가
- `b90480ef` Data Table 추가
  - Developer Settings에 Table 등록
  - Sheet로부터 Data Asset을 받아 Table 값 구성
  - Primary Asset을 Asset Manager에 등록
- `3c2385a1` Data Table 관련 파일을 `Table` 폴더로 이동
- `2b290b78` Table Parsing 클래스의 기능 분리
  - 부모 클래스 생성
  - 공통 기능을 Util로 이동
  - Parsing 클래스에는 최소한의 코드만 유지
- `f2fc5230` 세 개로 나뉜 범퍼 Data Asset을 하나로 통합
- `d9fd261d` 비동기 에셋 로드 Subsystem 구현

## 2026년 7월 6일

- `9bf86d7e` 범퍼 비동기 데이터 로드 적용
  - 전투 흐름을 관리하는 GameState 추가
  - GameState와 통신하는 GameMessage 추가
  - 플레이어 데이터 추가
  - 플레이어 데이터를 읽고 범퍼를 소환하는 클래스 추가
- `83c75182` 테스트용 메인 레벨과 범퍼 에셋 로드 테스트 맵 추가
- `57f3a395` GameState가 담당하던 비동기 로드 책임 이전
  - Bundle Name 헤더 선언 추가
  - Row ID와 Bundle 이름으로 에셋 로더를 호출하도록 수정
- `5c34861f` GameState가 담당하던 비동기 로드 책임 이전
  - Bundle Name 헤더 선언 추가
  - Row ID와 Bundle 이름으로 에셋 로더를 호출하도록 수정

## 2026년 7월 7일

- `e9fe9cfd` `BumperAssetLoader`를 `DataLoadSubsystem`으로 통합
  - Bundle Name Enum 접근 추가
  - Primary Asset Load Handle과 Cache를 Bundle 단위로 관리
- `bf5b0a62` `BumperAssetLoader`를 `DataLoadSubsystem`으로 통합
  - Bundle Name Enum 접근 추가
  - Primary Asset Load Handle과 Cache를 Bundle 단위로 관리
- `1f4b7be4` 범퍼 장착 Widget과 Push/Pop UI Manager 추가
  - Table의 전체 값을 반환하는 함수 추가
- `4cc83f03` 범퍼 테스트 레벨과 에셋 로드 테스트 Blueprint 제거

## 2026년 7월 8일

- `51904cd3` 에셋을 활용한 전투 맵 구성
- `d435e284` 범퍼 아이콘용 임시 Texture 추가 및 Data Asset 갱신
- `6b6bc720` 범퍼 아이콘용 임시 Texture에 맞춰 Google Sheet 데이터 갱신
- `0967e00c` 상점 이후 전투에서 범퍼가 로드되지 않던 오류 수정
- `dec054cb` Boss Table 데이터 등록

## 2026년 7월 9일

- `64b2eaee` Ball Primary Asset의 Cook Type을 `Always Cook`으로 변경
- `a2153e33` 범퍼 데이터의 로드 단계와 생성 단계 분리
  - `BumperSpawnController`를 `BumperSpawner`로 변경
- `fe3bbf3d` Developer Settings의 Data Table 초기화 책임을 `TableDataSubsystem`으로 이전
- `43c83674` 테스트를 위한 Cheat 기능 추가
  - `add default ball`: Ball 즉시 추가
  - `goScene int`: Scene 이동
  - `Print Async Load State`: 로드된 에셋 상태 확인
  - `Damage Boss int`: Boss에게 Damage 적용

## 2026년 7월 14일

- `2b135201` Skill 데이터 Parser 추가
  - Ball Primary Asset에 Skill Blueprint Class 추가
- `a80238cf` Skill 데이터 Parser 추가
  - Ball Primary Asset에 Skill Blueprint Class 추가

## 2026년 7월 15일

- `6f092fe6` 분신 Ball Skill 임시 구현
  - 범퍼와 Flipper가 `BallBase`를 통해 데이터에 접근하던 부분을 `IMovable`로 변경
  - 임시 Trail Particle 추가
- `c412659f` Skill 초기화 시 `BallInstanceData`를 사용하도록 수정
- `274639b6` 분신 Ball Skill 임시 구현
  - 범퍼와 Flipper가 `BallBase`를 통해 데이터에 접근하던 부분을 `IMovable`로 변경
  - 임시 Trail Particle 추가
- `7d8f2f5a` Ball 데이터 반영 및 Niagara 크기 조절

## 2026년 7월 20일

- `999a5ec0` Skill Sheet Parser 수정
- `c5b38082` Skill Sheet 데이터 로드
- `8a36086e` 전투 이후 Gold 보상 Popup 추가
  - Popup 함수 수정
  - `BattleExit` 전투 Phase 추가
  - 플레이어 데이터에 Gold 추가
- `50ab6af8` Synergy Icon Asset 추가
- `9863cd2a` Skill Parser가 Icon 경로를 확인한 후 적용하도록 수정
- `9c89db40` 범퍼 관련 Table과 Sheet Loader의 경로 및 이름 수정
- `8f24bb0c` 무적 Skill과 Buff 구현
  - `StatusEffect` 데이터 로더 범위 수정

## 2026년 7월 21일

- `88283a53` Skill Sheet 데이터 로드

## 2026년 7월 22일

- `9871a2f2` Sprite Data Asset Bundle에 `UI` Tag 추가
- `b219cad3` Skill 설명 데이터 적용
- `39459560` `SkillReady` 에셋 경로 이름 수정
- `ae55b3a0` `SkillReady` 에셋 경로 이름 수정

## 2026년 7월 23일

- `17683592` Boss 패턴 공격에 Sheet의 Damage가 적용되지 않는 문제 수정
- `dfdfb177` Boss, Skill, Ball의 1차 밸런싱 데이터 로드
- `9c34ad3d` 2차 밸런싱 데이터 로드
- `0ed616b0` 상점에서 `Gameplay` Tag까지 로드하던 부분 제거

## 2026년 7월 24일

- `d806e1f2` 게임 Clear 이후 전투가 시작되지 않고 Credit이 열리던 현상 수정
  - 범퍼에서 이미 로드된 데이터를 요청하면 실패로 처리하던 현상 수정
- `1938d7df` Boss에서 이미 로드된 에셋을 요청하면 실패로 처리하던 오류 수정
- `8f5fde87` Sheet 데이터 로드
