# Google OAuth 2.0 설정 가이드 📋

이 가이드는 Japanese Lyrics Study 앱에서 Google OAuth 인증이 정상 작동하도록 Google Cloud Console을 설정하는 방법을 안내합니다.

## 🔧 Google Cloud Console 설정

### 1단계: Google Cloud Project 생성 또는 선택
1. [Google Cloud Console](https://console.cloud.google.com/) 접속
2. 기존 프로젝트를 선택하거나 새 프로젝트 생성
3. 프로젝트 이름: `japanese-lyrics-study` (예시)

### 2단계: Google+ API 및 OAuth 동의 화면 설정
1. **API 및 서비스 > 라이브러리** 이동
2. "Google+ API" 검색 후 활성화 (더 이상 필요 없지만 호환성을 위해)
3. **OAuth 동의 화면** 이동
4. 사용자 유형: **외부** 선택
5. 필수 정보 입력:
   - **앱 이름**: `AI Japanese Lyrics Study`
   - **사용자 지원 이메일**: `jaceyoung0705@gmail.com`
   - **개발자 연락처 정보**: `jaceyoung0705@gmail.com`
6. **저장 후 계속**

### 3단계: 스코프 설정
1. **범위 추가 또는 삭제** 클릭
2. 다음 스코프들 추가:
   - `../auth/userinfo.email`
   - `../auth/userinfo.profile`
   - `openid`
3. **업데이트** 클릭

### 4단계: 테스트 사용자 추가
1. **테스트 사용자** 섹션에서 **사용자 추가**
2. `jaceyoung0705@gmail.com` 추가
3. **저장**

### 5단계: OAuth 클라이언트 ID 생성
1. **API 및 서비스 > 사용자 인증 정보** 이동
2. **사용자 인증 정보 만들기 > OAuth 클라이언트 ID** 클릭
3. 애플리케이션 유형: **웹 애플리케이션**
4. 이름: `Japanese Lyrics Study Web Client`
5. **승인된 자바스크립트 원본** 추가:
   
   **개발 환경 (로컬 테스트용):**
   ```
   http://localhost:3000
   http://localhost:5000
   http://localhost:8000
   http://127.0.0.1:3000
   http://127.0.0.1:5000
   http://127.0.0.1:8000
   ```
   
   **프로덕션 환경 (GitHub Pages):**
   ```
   https://architectofthoughts.github.io
   https://architectofthoughts.github.io/lyricsstudyapp
   ```
   
   ⚠️ **중요**: `file://`는 Google OAuth에서 지원되지 않으므로 제외

6. **승인된 리디렉션 URI** (필요한 경우):
   ```
   https://architectofthoughts.github.io/lyricsstudyapp/
   http://localhost:3000/callback
   http://localhost:5000/callback
   ```
7. **만들기** 클릭
8. **클라이언트 ID**를 복사해서 안전한 곳에 보관

### 6단계: 앱 게시 (선택사항)
1. **OAuth 동의 화면**으로 돌아가기
2. **앱 게시**를 클릭하여 프로덕션으로 전환
3. 아니면 테스트 모드에서 계속 사용 (테스트 사용자만 로그인 가능)

## 🚀 앱에 적용

### 클라이언트 ID 교체
생성된 클라이언트 ID를 `LyricsStudy.html` 파일의 다음 부분에 교체:

```javascript
// 이 부분을 찾아서
const GOOGLE_CLIENT_ID = 'YOUR_NEW_CLIENT_ID_HERE';
// 실제 클라이언트 ID로 교체
```

### GitHub Pages 배포 후 도메인 추가

#### 실제 GitHub Pages URL:
```
https://architectofthoughts.github.io/lyricsstudyapp/
```

#### OAuth 설정에 추가할 도메인:
```
https://architectofthoughts.github.io
https://architectofthoughts.github.io/lyricsstudyapp
```

#### 커스텀 도메인 사용 시 (선택사항):
```
https://yourdomain.com
https://www.yourdomain.com
```

## 🔍 문제 해결

### "OAuth 2.0 policy" 오류가 발생하는 경우:
1. **OAuth 동의 화면**에서 모든 필수 필드가 입력되었는지 확인
2. **테스트 사용자**에 이메일이 추가되었는지 확인
3. **승인된 자바스크립트 원본**에 현재 사용 중인 도메인/포트가 포함되었는지 확인
4. 브라우저 캐시 및 쿠키 삭제 후 재시도

### "redirect_uri_mismatch" 오류가 발생하는 경우:
1. 승인된 리디렉션 URI에 현재 페이지 URL이 포함되어 있는지 확인
2. 프로토콜(http/https) 및 포트가 정확한지 확인

### "origin=file://" 오류가 발생하는 경우:
- **원인**: Google OAuth는 `file://` 프로토콜을 지원하지 않음
- **해결책**: 
  1. 로컬 웹 서버 실행: `python -m http.server 8000`
  2. GitHub Pages 배포: `https://username.github.io/repo-name/`
  3. 다른 웹 호스팅 서비스 사용

### 개발 중 localhost에서 테스트할 때:
- `http://localhost:포트번호`와 `http://127.0.0.1:포트번호` 모두 추가
- ⚠️ **중요**: `file://`는 더 이상 지원되지 않음

## 📝 참고사항

- Google OAuth 2.0은 보안 정책이 엄격하므로 모든 설정이 정확해야 함
- 테스트 모드에서는 추가된 테스트 사용자만 로그인 가능
- 프로덕션 모드로 전환하려면 개인정보처리방침 등 추가 정보 필요
- 클라이언트 ID는 공개되어도 상관없지만, 클라이언트 시크릿은 절대 노출하면 안 됨

이 가이드를 따라 설정하면 Google OAuth 인증이 정상적으로 작동할 것입니다!

Client ID : 926600143546-4hj7lceacp4um51pru7qfkn70jgmcg08.apps.googleusercontent.com
Client PW : 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