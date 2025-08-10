# GitHub Pages 배포 가이드 🚀

이 가이드는 AI 일본어 가사 학습 도우미를 GitHub Pages에 배포하여 Google OAuth 인증이 정상 작동하도록 하는 방법을 설명합니다.

## 🎯 왜 GitHub Pages인가?

### file:// 프로토콜의 한계
- Google OAuth는 보안상 `file://` 프로토콜을 지원하지 않음
- HTTPS 환경에서만 OAuth 인증이 가능
- GitHub Pages는 무료 HTTPS 호스팅 제공

### GitHub Pages의 장점
- ✅ 무료 HTTPS 호스팅
- ✅ 단일 HTML 파일 구조 유지
- ✅ 모바일 완벽 지원
- ✅ 빠른 CDN 배포
- ✅ 자동 SSL 인증서

## 📋 배포 단계

### 1단계: 기존 Repository 확인

현재 프로젝트는 이미 GitHub에 연결되어 있습니다:
- **GitHub 계정**: `architectofthoughts`
- **Repository**: `lyricsstudyapp`
- **URL**: `https://github.com/architectofthoughts/lyricsstudyapp`

### 2단계: 파일 커밋 및 푸시

현재 작업 디렉토리의 파일들을 GitHub에 업로드:
```
lyricsstudyapp/
├── index.html (메인 페이지, LyricsStudy.html로 리다이렉트)
├── LyricsStudy.html (실제 앱)
├── README.txt (프로젝트 설명)
├── GOOGLE_OAUTH_SETUP.md (OAuth 설정 가이드)
├── CLAUDE.md (개발 문서)
├── DEPLOYMENT.md (이 파일)
└── .gitignore (Git 제외 파일)
```

**Git 명령어:**
```bash
git add .
git commit -m "Add GitHub Pages deployment files and OAuth setup"
git push origin master
```

### 3단계: GitHub Pages 활성화

1. **Repository Settings** 이동: `https://github.com/architectofthoughts/lyricsstudyapp/settings`
2. **Pages** 섹션 찾기
3. **Source** 설정:
   - Source: `Deploy from a branch`
   - Branch: `master`
   - Folder: `/ (root)`
4. **Save** 클릭

### 4단계: 배포 URL 확인

배포 완료 후 다음 URL로 접근 가능:
```
https://architectofthoughts.github.io/lyricsstudyapp/
```

## 🔐 OAuth 설정 업데이트

### Google Cloud Console 설정

1. **Google Cloud Console** 접속
2. **API 및 서비스 > 사용자 인증 정보**
3. **OAuth 클라이언트 ID** 편집
4. **승인된 JavaScript 원본**에 다음 추가:
   ```
   https://architectofthoughts.github.io
   https://architectofthoughts.github.io/lyricsstudyapp
   ```

### 도메인 예시
실제 GitHub Pages URL:
```javascript
// 승인된 JavaScript 원본에 추가할 URL들
https://architectofthoughts.github.io
https://architectofthoughts.github.io/lyricsstudyapp
```

## 🧪 테스트 방법

### 1. 로컬 테스트 (개발용)
```bash
# Python으로 로컬 서버 실행
python -m http.server 8000

# 또는 Node.js 사용
npx http-server -p 8000

# http://localhost:8000 접속
```

### 2. GitHub Pages 테스트 (실제 배포)
```
https://architectofthoughts.github.io/lyricsstudyapp/
```

### 3. OAuth 인증 테스트
1. GitHub Pages URL 접속
2. "Google 계정으로 로그인" 클릭
3. `jaceyoung0705@gmail.com` 계정으로 로그인
4. 인증 성공 확인

## 🔄 업데이트 방법

### 코드 수정 후 배포
1. **로컬에서 파일 수정**
2. **GitHub Repository에 업로드**
   - Git 사용: `git add . && git commit -m "Update" && git push`
   - 웹 인터페이스: 직접 파일 편집 또는 업로드
3. **자동 배포** (5-10분 소요)

### 배포 상태 확인
- Repository의 **Actions** 탭에서 배포 진행 상황 확인
- **Settings > Pages**에서 배포 상태 확인

## ⚡ 성능 최적화

### CDN 활용
GitHub Pages는 글로벌 CDN을 통해 빠른 로딩 제공

### 캐싱 최적화
- 브라우저 캐싱 자동 적용
- 정적 파일 압축 자동 적용

### 모바일 최적화
- 반응형 디자인 유지
- PWA 기능 추가 가능

## 🔧 문제 해결

### 일반적인 문제

#### 1. 404 오류
- **원인**: 파일 경로 문제
- **해결**: index.html과 LyricsStudy.html이 같은 디렉토리에 있는지 확인

#### 2. OAuth 오류
- **원인**: 승인된 JavaScript 원본 설정 문제
- **해결**: GitHub Pages URL을 정확히 OAuth 설정에 추가

#### 3. HTTPS 인증서 오류
- **원인**: GitHub Pages 설정 미완료
- **해결**: Repository Settings > Pages에서 "Enforce HTTPS" 확인

### 디버깅 방법

#### 브라우저 콘솔 확인
```
F12 → Console 탭에서 오류 메시지 확인
```

#### 네트워크 요청 확인
```
F12 → Network 탭에서 API 호출 상태 확인
```

## 📱 모바일 지원

### PWA 기능 (선택사항)
향후 Progressive Web App 기능 추가 가능:
- 오프라인 지원
- 홈 화면에 설치
- 네이티브 앱 같은 경험

### 모바일 브라우저 최적화
- 터치 친화적 인터페이스
- 반응형 레이아웃
- 빠른 로딩 시간

## 🌐 커스텀 도메인 (선택사항)

### 개인 도메인 연결
1. **도메인 구매** (예: `lyrics-study.com`)
2. **DNS 설정**: GitHub Pages IP 주소로 연결
3. **Repository Settings**: Custom domain 설정
4. **OAuth 설정**: 새 도메인 추가

## 📊 분석 및 모니터링

### Google Analytics 연동 (선택사항)
```html
<!-- Google Analytics 코드 추가 -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
```

### 사용자 피드백 수집
- GitHub Issues를 통한 버그 리포트
- 사용자 제안 수집

---

이 가이드를 따라 배포하시면 Google OAuth 인증이 정상적으로 작동하는 웹 애플리케이션을 운영할 수 있습니다! 🎉