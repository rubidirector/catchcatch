# 캐치캐치

캡처(ㅋㅊ)한 정보를 캐치해 두는 보관함. 트위터·인스타 등에서 찍은 캡처나 링크를 올리면 Gemini가 이미지 속 글자를 읽고, 요약·태그를 붙여 폴더에 정리해 줍니다. 구글로 로그인하면 캡처가 내 계정에 저장돼서 어느 기기에서든 같은 보관함을 볼 수 있어요.

## 1. GitHub Pages로 배포
1. 이 폴더의 파일을 모두 저장소 맨 위(루트)에 올립니다.
2. 저장소 **Settings → Pages**에서 Branch를 `main` / `(root)`로 저장합니다.
3. 1~2분 뒤 `https://<아이디>.github.io/<저장소이름>/` 에서 열립니다.

## 2. 구글 로그인 연결 (Firebase, 처음 한 번)
Firebase 콘솔(https://console.firebase.google.com)에서 프로젝트를 열고:

1. **프로젝트 설정(톱니) → 일반 → 내 앱**에서 웹 앱(`</>`)을 추가합니다. 이름은 `캐치캐치`. 나오는 `firebaseConfig` 코드를 복사해 둡니다.
2. **Authentication → 시작하기 → 로그인 방법**에서 **Google**을 사용 설정합니다.
3. **Authentication → 설정 → 승인된 도메인**에 `<아이디>.github.io`를 추가합니다.
4. **Firestore Database → 데이터베이스 만들기** (위치는 `asia-northeast3 (서울)` 추천). 만든 뒤 **규칙** 탭에 아래를 붙여넣고 **게시**합니다.

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{uid}/{document=**} {
      allow read, write: if request.auth != null
                         && request.auth.uid == uid;
    }
  }
}
```

5. 사이트를 열면 나오는 첫 화면에 `firebaseConfig` 코드를 붙여넣고 **연결하기 → Google 계정으로 시작하기**.

**다른 기기에서도 설정 없이 쓰려면** `index.html`의 `const FIREBASE_CONFIG = null;` 을 복사한 설정 객체로 바꿔 올리세요. Firebase 웹 설정값은 공개돼도 괜찮은 값이고, 데이터는 위 보안 규칙으로 본인만 읽고 쓸 수 있어요.

## 3. AI 정리 켜기 (Gemini, 무료)
1. https://aistudio.google.com/app/apikey 에서 **Create API key**.
2. 앱 **설정 → AI 정리 · Gemini**에 붙여넣고 **저장 → 연결 테스트**.

키는 내 계정에 함께 저장돼서 다른 기기에서 다시 넣지 않아도 돼요. 무료 키로 보낸 내용은 구글이 서비스 개선에 쓸 수 있어요.

## 데이터 / 비용
- 캡처 목록과 이미지는 Firestore의 `users/<내 uid>/` 아래에 저장됩니다. 이미지는 저장할 때 용량을 줄여(최대 약 650KB) 보관해요.
- Firebase 무료(Spark) 요금제 안에서 동작합니다. 무료 한도는 저장 1GB, 하루 읽기 5만 번·쓰기 2만 번 수준이라 혼자 쓰기에는 충분해요.
- 설정의 **백업 파일 저장**으로 전체를 파일 하나로 받아둘 수 있어요.

## 파일
- `index.html` 앱 전체
- `logo.svg`, `logo-white.svg` 로고 (밝은 배경용 / 어두운 배경용)
- `favicon.svg`, `favicon-32.png` 브라우저 탭 아이콘
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png` 홈 화면 아이콘
- `manifest.webmanifest` 홈 화면 앱 설정
