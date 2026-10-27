# 빛과 소금 교회 — 소개 웹사이트

서울 노원구 중계동 빛과 소금 교회의 정적 소개 페이지입니다.  
빌드 도구 없이 HTML/CSS/JS 파일만으로 구성되어 있습니다.

---

## 파일 구조

```
church/
├── index.html   ← 메인 페이지 (예배 안내, 직원, 오시는 길)
├── style.css    ← 스타일시트
├── favicon.svg  ← 파비콘
├── .gitignore
└── README.md
```

---

## 로컬 미리보기

### 방법 1 — VS Code Live Server (권장)
1. VS Code 확장 마켓플레이스에서 **Live Server** 설치
2. `index.html` 파일 열기 → 우하단 **Go Live** 버튼 클릭
3. 브라우저에서 `http://127.0.0.1:5500` 자동 열림

### 방법 2 — Python 내장 서버
```bash
# Python 3
python -m http.server 8080
# 브라우저에서 http://localhost:8080 접속
```

### 방법 3 — 파일 직접 열기
`index.html` 을 브라우저에 드래그하면 바로 열립니다.  
단, **주소 복사** 기능은 HTTPS 또는 localhost 환경에서만 동작합니다.

---

## GitHub Pages 배포 (무료)

> GitHub 계정이 없으면 https://github.com/join 에서 먼저 가입하세요.

### 1단계 — git 초기화 (최초 1회)

```bash
cd c:\church
git init
git add .
git commit -m "초기 배포: 빛과 소금 교회 소개 페이지"
```

### 2단계 — GitHub 저장소 생성

1. https://github.com/new 접속 (로그인 필요)
2. Repository name: `church` (원하는 이름)
3. **Public** 선택 → **Create repository** 클릭

### 3단계 — 원격 저장소 연결 & 푸시

```bash
# <YOUR_USERNAME> 을 본인 GitHub 계정명으로 교체
git remote add origin https://github.com/<YOUR_USERNAME>/church.git
git branch -M main
git push -u origin main
```

### 4단계 — GitHub Pages 활성화

1. 저장소 페이지 → **Settings** 탭
2. 왼쪽 메뉴 **Pages** 클릭
3. Source: **Deploy from a branch**
4. Branch: **main** / **/ (root)** 선택 → **Save**
5. 1~2분 후 `https://<YOUR_USERNAME>.github.io/church/` 에서 접속 가능

### 5단계 — og:url 메타태그 업데이트

배포 주소가 확정되면 `index.html` 상단의 TODO 주석을 실제 URL로 교체하세요:

```html
<!-- 변경 전 -->
<!-- TODO: og:url — 배포 후 실제 URL 로 교체 -->

<!-- 변경 후 -->
<meta property="og:url" content="https://<YOUR_USERNAME>.github.io/church/">
```

변경 후:
```bash
git add index.html
git commit -m "og:url 실제 주소로 업데이트"
git push
```

---

## 대안 배포 방법

### Cloudflare Pages
1. https://dash.cloudflare.com → **Pages** → **Create a project**
2. **Connect to Git** → GitHub 계정 연결 → 저장소 선택
3. Build command: 비워두기 (빌드 없음)
4. Build output directory: `/`
5. **Save and Deploy**
6. 배포 URL: `https://<project>.pages.dev`

### Netlify
1. https://app.netlify.com → **Add new site** → **Import an existing project**
2. GitHub 연결 → 저장소 선택
3. Build command: 비워두기, Publish directory: `.`
4. **Deploy site**
5. 배포 URL: `https://<random>.netlify.app`
6. Site settings → **Change site name** 으로 URL 변경 가능

---

## 내용 수정 방법

### 예배 시간 수정

`index.html` → `<section id="worship">` 섹션 내부의 `.worship-card` 를 찾아 수정합니다.

```html
<!-- 예: 주일 1부 예배 시간 변경 -->
<div class="worship-card">
  <span class="time-badge">오전 10:00</span>  ← 시간 수정
  <div class="info">
    <p class="name">주일 1부 예배</p>          ← 이름 수정
    <p class="note">비고 문구</p>              ← 비고 추가/수정/삭제
  </div>
</div>
```

예배를 추가하려면 `.worship-card` 블록 전체를 복사하여 같은 `.worship-grid` 안에 붙여넣으세요.

### 섬기는 분들 수정

`index.html` → `<section id="staff">` 섹션 내부의 `.staff-card` 를 찾아 수정합니다.

```html
<div class="staff-card">
  <span class="role-badge">담임목사</span>  ← 직책 수정
  <span class="staff-name">임 철</span>     ← 이름 수정
</div>
```

### 연락처·계좌 추가

`index.html` 하단 `<footer>` 안의 `TODO` 주석을 참고해 추가하세요.

---

## 배포 후 접속 확인

| 방법 | 내용 |
|------|------|
| PC 브라우저 | `https://<YOUR_USERNAME>.github.io/church/` 직접 입력 |
| 스마트폰 | 같은 URL을 카카오톡·문자로 전송 후 탭하여 열기 |
| OG 미리보기 | 카카오톡 채팅창에 URL 붙여넣기 → 미리보기 카드 확인 |
| 구글 검색 | 배포 1~3일 후 사이트명으로 검색하여 인덱싱 확인 |

---

## 향후 수정 시 배포 흐름

파일 수정 후 아래 명령어만 실행하면 자동으로 반영됩니다 (GitHub Pages 기준).

```bash
git add .
git commit -m "예배 시간 수정"
git push
```

GitHub Pages는 보통 1~2분 내에 반영됩니다.
