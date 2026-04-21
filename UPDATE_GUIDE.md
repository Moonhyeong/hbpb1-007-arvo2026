# HBPB1-007 · ARVO 2026 Landing Page — Update & Usage Guide

> 마지막 업데이트: 2026-04-21

---

## 📍 기본 URL

- **공개 URL (QR 타겟)**: https://moonhyeong.github.io/hbpb1-007-arvo2026/
- **GitHub Repository**: https://github.com/Moonhyeong/hbpb1-007-arvo2026
- **로컬 작업 폴더**: `C:\Users\Seo\Desktop\KIST\My valut\TDIP-portfolio\outputs\landing-page`

---

## 🎯 포스터에 QR 코드 삽입

### QR 파일 위치
두 폴더에 동일 파일이 있습니다:
- `C:\Users\Seo\Desktop\2026 ARVO\포스터\qr_hbpb1-007-arvo2026_navy.png` (포스터 pptx에 직접 삽입용)
- `outputs\landing-page\qr\` (repo 백업본)

PNG와 SVG 두 버전 제공:
- **PNG** (1960×1960): PowerPoint·PDF 작업 시 무난. 2.5 cm 이상 크기로 사용해도 300 dpi 이상 유지
- **SVG**: 벡터, 무한 확대 가능. Adobe Illustrator/Inkscape 사용 시 권장

### 포스터 삽입 절차 (PowerPoint 기준)

1. `ARVO_Poster_MHSeo_20260420_초안2.pptx` 열기
2. **Insert → Pictures → This Device…** 로 `qr_hbpb1-007-arvo2026_navy.png` 선택
3. 포스터 **우하단** 여백에 배치 (포스터 크기 대비 약 5~8% 권장)
   - 예: 가로 120 cm 포스터 → QR 6~10 cm
4. QR 아래에 라벨 텍스트 추가 (작은 글씨):
   ```
   Scan for full data
   hbpb1-007-arvo2026
   ```
5. QR 주변에 최소 1 cm 여백(quiet zone) 확보 — 다른 요소가 겹치지 않도록

### 스캔 테스트 권장
인쇄 전 반드시 확인:
- [ ] iPhone 기본 카메라로 스캔 (iOS 11+)
- [ ] Android 기본 카메라로 스캔
- [ ] 1 m, 2 m 거리에서 스캔
- [ ] 인쇄본(또는 실크스크린 시안)에서 스캔

실패 시 원인:
- 크기가 너무 작음 → 최소 2.5 cm × 2.5 cm 확보
- 주변 잡음 요소 → quiet zone 확보
- 인쇄 잉크 블리딩 → ECC-H이므로 30%까지 손상 복구 가능하나 극단적 저조도 인쇄는 피할 것

---

## 🔄 포스터 PDF 최종본 교체

포스터 완성 후 랜딩페이지의 `[Download Poster PDF]` 버튼이 최종본을 가리키도록 교체:

```bash
# 1. 로컬 폴더로 이동
cd "C:/Users/Seo/Desktop/KIST/My valut/TDIP-portfolio/outputs/landing-page"

# 2. 새 PDF로 덮어쓰기 (파일명은 poster.pdf 유지)
cp "C:/Users/Seo/Desktop/2026 ARVO/포스터/ARVO_Poster_FINAL.pdf" assets/poster.pdf

# 3. 변경사항 확인
git status
git diff --stat

# 4. 커밋 & 푸시
git add assets/poster.pdf
git commit -m "Replace poster PDF with final version"
git push origin main
```

푸시 후 1~2분 내 https://moonhyeong.github.io/hbpb1-007-arvo2026/assets/poster.pdf 가 최신 파일로 갱신됩니다. **URL 자체는 불변**이므로 QR 코드를 다시 만들 필요 없습니다.

---

## ✏️ 랜딩페이지 내용 업데이트하는 법

### 기본 워크플로우

모든 랜딩페이지 수정은 **3단계**로 끝납니다:

```
1. 로컬에서 파일 수정 → 2. Git 커밋 → 3. Push
                                    ↓
                              (1~2분 후 자동 반영)
```

### 사례별 가이드

#### Case 1: 텍스트 수정 (오타, 문구 변경, 수치 업데이트)
```bash
cd "C:/Users/Seo/Desktop/KIST/My valut/TDIP-portfolio/outputs/landing-page"
# index.html을 아무 편집기(VSCode, Notepad++)로 열어 수정
# 저장 후:
git add index.html
git commit -m "Update [섹션명] text"
git push origin main
```

#### Case 2: 그림 교체 (피겨, 로고)
```bash
cd "C:/Users/Seo/Desktop/KIST/My valut/TDIP-portfolio/outputs/landing-page"
# 기존 파일과 동일한 이름으로 images/ 에 덮어쓰기
cp /path/to/new_efficacy.png images/efficacy.png
git add images/efficacy.png
git commit -m "Update efficacy figure with revised panel"
git push origin main
```

파일명을 바꾸려면 `index.html`의 `<img src>` 경로도 함께 수정 후 커밋.

#### Case 3: 새 섹션 추가 / 구조 변경
`index.html`의 HTML 구조 직접 편집. 변경 후 로컬에서 미리보기 권장:

```bash
# 로컬 서버 (포트 8000)
python -m http.server 8000 --directory outputs/landing-page
# 브라우저: http://localhost:8000
```

확인 후 커밋·푸시.

#### Case 4: Claude에게 수정 의뢰
이 터미널에서 다음처럼 자연어로 지시 가능:
```
"랜딩페이지의 Pipeline 섹션에서 2027년 milestone을 "IND-enabling studies" 로 바꿔줘"
"Hero 아래에 새 배지를 추가해줘: "BIO International 2026 Selected""
```
Claude가 index.html을 편집하고 커밋·푸시까지 자동 수행합니다. push 시 인증은 Git Credential Manager에 캐시되어 있어 재로그인 불필요.

---

## 🔐 인증 관련 참고

- **GitHub 인증**: Windows Git Credential Manager가 OAuth 토큰을 캐시. 재설치 전까지 `git push` 시 추가 로그인 불필요.
- **커밋 author email**: `224478598+Moonhyeong@users.noreply.github.com` (개인정보 보호를 위해 GitHub noreply 이메일 사용 중)
- 새 기기에서 작업하려면:
  1. `git clone https://github.com/Moonhyeong/hbpb1-007-arvo2026.git`
  2. `git config user.email "224478598+Moonhyeong@users.noreply.github.com"`
  3. `git config user.name "Moon-hyeong Seo"`

---

## 📊 방문자 통계 (선택)

현재는 미설치. 나중에 추가하려면:

**Google Analytics 4 (무료)**
1. analytics.google.com 에서 property 생성
2. Measurement ID 발급 (G-XXXXXXXX)
3. `index.html`의 `</head>` 위에 GA4 스니펫 삽입

**Plausible (프라이버시 친화, $9/월)**
- 쿠키 없음, GDPR 준수
- 1줄 스크립트로 설치

필요 시 알려주세요.

---

## 🚨 긴급 롤백 (잘못 배포했을 때)

이전 커밋으로 되돌리기:

```bash
cd "C:/Users/Seo/Desktop/KIST/My valut/TDIP-portfolio/outputs/landing-page"
git log --oneline -5           # 이전 커밋 확인
git revert HEAD                 # 마지막 커밋을 되돌리는 새 커밋 생성 (안전)
git push origin main
```

`git reset --hard` 류의 파괴적 명령은 가급적 사용하지 말 것. `revert`가 안전합니다.

---

## 📞 문의

- Moon-Hyeong Seo · mhseo@kist.re.kr
- Repository issue: https://github.com/Moonhyeong/hbpb1-007-arvo2026/issues
