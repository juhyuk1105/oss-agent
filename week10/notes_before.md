# notes_before.md — week09/tools.py 분석

## 개요
- KOBIS(영화진흥위원회) 오픈 API로 **일별 박스오피스** 정보를 가져오는 도구 모음
- API 키는 `secret.py`의 `API_KEY`에서 불러옴
- 요청 주소: `BASE_URL` (`searchDailyBoxOfficeList.json`)

## 함수 목록

### 1. `get_boxoffice_rank_1(date)`
- **역할**: 해당 날짜의 박스오피스 **1위 영화 제목**을 반환
- **입력**: `date` (str) — 8자리 날짜, 예: `"20261013"`
- **출력**: (str) 1위 영화 제목, 예: `"오디세이"`
- **동작**: API 호출 → `boxOfficeResult.dailyBoxOfficeList` 추출 → 첫 번째 항목의 `movieNm` 반환

### 2. `get_boxoffice(date)`
- **역할**: 해당 날짜의 박스오피스 **전체 목록**을 반환
- **입력**: `date` (str) — 8자리 날짜
- **출력**: (list[dict]) `dailyBoxOfficeList` 그대로 (순위, 영화명, 관객수 등 포함)
- **동작**: API 호출 → `dailyBoxOfficeList` 리스트 반환

## 현재 상태에서 눈에 띄는 점
- 두 함수가 API 호출 코드(params 구성, `requests.get`, `.json()`)를 **중복**해서 가지고 있음
- `get_boxoffice`의 docstring은 입력/출력 설명이 `get_boxoffice_rank_1`보다 간략함
- 오류 처리 없음: HTTP 오류, 잘못된 날짜, 결과가 빈 리스트일 때(`movies[0]` → `IndexError`) 대비가 없음
