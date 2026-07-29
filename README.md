# Derma Agent 소개 페이지

중증 아토피피부염 환자 예후관리 서비스 **Derma Agent** 모바일 소개 페이지입니다.
QR 코드로 접속해 세로 스크롤로 읽는 원페이지 구조입니다.

## 파일 구성

```
├── index.html      # 페이지 본문 (HTML + CSS + JS 단일 파일)
├── assets/         # 로고 · 일러스트 · 앱 화면 이미지
├── .nojekyll       # GitHub Pages Jekyll 처리 비활성화
└── README.md
```

`assets/` 파일 이름 규칙

| 접두어 | 내용 |
| --- | --- |
| `logo-` | Derma Agent · ACRYL 로고 |
| `char-` | MaAi 캐릭터 |
| `illust-` | 일러스트 (환자, 좁은 문) |
| `drug-` | 생물학적 제제 제품 이미지 |
| `app-` | 앱 화면 스크린샷 |
| `card-` | 증상 요약 카드 |

## 배포 방법 (GitHub Pages)

1. GitHub에서 새 저장소를 만듭니다. (예: `derma-agent-intro`, Public)
2. 이 폴더의 파일 전체를 업로드합니다.
   - 웹 업로드: 저장소 → **Add file** → **Upload files** → `index.html`과 `assets` 폴더를 함께 드래그
   - CLI:
     ```bash
     git init
     git add .
     git commit -m "Derma Agent 소개 페이지"
     git branch -M main
     git remote add origin https://github.com/<계정>/<저장소>.git
     git push -u origin main
     ```
3. 저장소 → **Settings** → **Pages** → Source를 **Deploy from a branch**, Branch를 **main / (root)** 로 저장합니다.
4. 1~2분 후 아래 주소로 접속됩니다.
   ```
   https://<계정>.github.io/<저장소>/
   ```
5. 이 주소로 QR 코드를 생성해 배포합니다.

## 배포 후 확인 사항

- **모바일에서 실제 확인**: 섹션이 한 화면 단위로 스냅되는 동작과 앱 화면 캐러셀 스와이프
- **공유 미리보기(OG 이미지)**: `index.html`의 `og:image`를 절대 주소로 바꾸면 카카오톡·슬랙 공유 시 썸네일이 표시됩니다.
  ```html
  <meta property="og:image" content="https://<계정>.github.io/<저장소>/assets/logo-derma-vertical.png">
  ```
- **글꼴**: Pretendard를 CDN(jsdelivr)에서 불러옵니다. 사내망에서 CDN이 막히면 시스템 글꼴(맑은 고딕)로 대체 표시됩니다.

## 페이지 구조

| 순서 | 섹션 | 내용 |
| --- | --- | --- |
| 1 | 오프닝 | "모든 치료를 다 해본 사람만 아는 시간" + 16주 타임라인 |
| 2 | 산정특례 | 좁은 문 3단계 요건 (출처: 대한피부과학회 보험규정 안내 Ver 2.0) |
| 3 | 세 사람의 16주 | 환자 · 의사 · 간호사 카드 (자동 순환 캐러셀) |
| 4 | MaAi | 4개 에이전트 소개 + 진단·치료 비해당 고지 |
| 5 | 앱 화면 | 좌우 스와이프 5장 (QA · Pro-active · Triage · 일정 · Summary) |
| 6 | 클로징 | 브랜드 마무리 + 협력 병원 크레딧 |

## 수정 가이드

- **문구**: `index.html` 안에 섹션별 주석(`<!-- 1. 서사 오프닝 -->` 등)이 있습니다.
- **색상**: `:root` CSS 변수에서 일괄 변경 (`--pri: #5B6EDF`가 브랜드 인디고)
- **앱 화면 교체**: `assets/app-*.png` 파일을 같은 이름으로 덮어쓰면 됩니다. 세로 스크린샷(360px 폭 이상) 권장
- **캐러셀 슬라이드 추가**: `.car-slide` 블록을 복제하고, `.car-dots` 안의 `<span class="car-dot">`를 하나 늘립니다.

## 표기

- 제품 이미지 출처: 한국릴리 · 레오파마 · 사노피 제품 자료
- 협력: 가천대길병원 · 세종충남대병원 · 강원대병원
- 개발: ACRYL Inc.
- 본 서비스는 의학적 진단이나 치료를 제공하지 않으며, 환자의 자가관리를 돕는 보조 서비스입니다.
