# boxoffice — KOBIS 박스오피스 조회 스킬

## 하는 일
- 날짜를 주고 박스오피스 1위를 물으면 그 날짜의 1위 영화 제목을 알려 줌
- 날짜와 영화 제목을 주고 관객 수를 물으면 그 영화의 그날 관객 수를 알려 줌 (영화진흥위원회 KOBIS 일별 박스오피스 기준)

## 들어 있는 파일
- .claude/skills/boxoffice/SKILL.md
- .claude/skills/boxoffice/scripts/boxoffice.py
- .claude/skills/boxoffice/LICENSE

## 필요한 것
- 파이썬 3 와 requests 패키지 (`pip install requests`)
- 프로젝트 폴더(스킬을 실행하는 폴더)에 tools.py — boxoffice.py 가 이 파일의 함수를 부름 (이 스킬 폴더에는 없음)
- 같은 폴더에 secret.py — KOBIS 키를 `API_KEY = "..."` 로 적은 파일 (직접 만들 것)

## 설치
- boxoffice 폴더를 프로젝트의 `.claude/skills/` 아래에 둠 → `.claude/skills/boxoffice/`
- 프로젝트 폴더에서 Claude Code 를 실행하고 "20261114 박스오피스 1위 알려 줘" 처럼 물으면 스킬이 쓰임
- 직접 돌려 볼 때: `python .claude/skills/boxoffice/scripts/boxoffice.py rank 20261114`

## 바깥으로 요청하는 곳
- `https://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json` 한 곳뿐임 (영화진흥위원회 오픈 API)
- 보내는 것: 내 API 키, 조회할 날짜

## 키
- 키는 프로젝트 폴더의 secret.py 에만 둠. 자기 키를 발급받아 secret.py 에 넣을 것
- 이 저장소에는 키가 없음 — secret.py 는 .gitignore 로 커밋에서 빠짐

## 권한
- SKILL.md 에 allowed-tools 가 없음 — 권한을 넓히지 않음
- 실행할 때 Claude Code 가 `python .claude/skills/boxoffice/scripts/boxoffice.py ...` 명령을 실행해도 되는지 물음 (Manual 모드). 명령 줄을 읽고 승인할 것

## 라이선스
- MIT License — `.claude/skills/boxoffice/LICENSE`
- 쓰고, 고치고, 나눌 수 있음. 저작권 표시와 라이선스 문구만 남기면 됨
