# 캐치캐치

캡처(ㅋㅊ)한 정보를 캐치해 두는 보관함. 트위터·인스타 등에서 찍은 캡처나 링크를 올리면 AI가 이미지 속 글자를 읽고, 요약·태그를 붙여 폴더에 정리해 줍니다.

## GitHub Pages로 배포
1. 이 폴더의 파일을 모두 저장소 맨 위(루트)에 올립니다.
2. 저장소 **Settings → Pages**에서 Source를 `Deploy from a branch`, Branch를 `main` / `(root)`로 저장합니다.
3. 1~2분 뒤 `https://<아이디>.github.io/<저장소이름>/` 에서 열립니다.
4. 휴대폰 브라우저 메뉴에서 **홈 화면에 추가**하면 앱처럼 쓸 수 있어요.

## AI 정리 켜기
앱의 **설정**에서 Claude API 키(https://console.anthropic.com/settings/keys)를 넣으면 캡처 분석과 "AI에게 물어보기"가 동작합니다. 키는 그 기기의 브라우저에만 저장되며, 사용량만큼 요금이 나갑니다. 키가 없어도 직접 입력으로 저장·검색은 됩니다.

## 데이터
캡처와 이미지는 기기의 브라우저(IndexedDB)에만 저장됩니다. 설정의 **백업 파일 저장 / 불러오기**로 백업하거나 다른 기기로 옮기세요.

## 파일
- `index.html` 앱 전체
- `logo.svg`, `logo-white.svg` 로고 (밝은 배경용 / 어두운 배경용)
- `favicon.svg`, `favicon-32.png` 브라우저 탭 아이콘
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png` 홈 화면 아이콘
- `manifest.webmanifest` 홈 화면 앱 설정
