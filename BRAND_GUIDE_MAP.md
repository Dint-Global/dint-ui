# DINT 브랜드 자료 안내 · DINT Brand Materials Map

> 같은 파일이 두 곳에 있습니다: GitHub `Dint-Global/dint-ui` 저장소와 공유 드라이브 `Z:\2. 전략기획 부서\14. 기타\21.etc\Brand_CI_DINT`.
> This same file is kept in two places: the GitHub repository `Dint-Global/dint-ui` and the shared drive folder `Z:\2. 전략기획 부서\14. 기타\21.etc\Brand_CI_DINT`.

---

## 한국어

DINT 브랜드 자료는 세 곳에 있습니다. 쓰는 사람과 목적이 다릅니다.

| 위치 | 누구를 위한 곳 | 무엇이 있나 |
|---|---|---|
| **CI 팩** (공유 드라이브 `Brand_CI_DINT`) | 디자이너, 기획·재무·영업 등 모든 직원, 외부 협력사 | CI 가이드(HTML·PDF), 로고 원본(.ai·PNG)과 SVG, 컬러 값, 서체, PowerPoint·Word 템플릿 |
| **dint-ui** (GitHub `Dint-Global/dint-ui`) | 개발자, 사내 앱·웹사이트 | 화면용 디자인 토큰(CSS), 컴포넌트, 웹 서체(Pretendard), 로고 SVG, 파비콘, 컬러·법인 정보 JSON |
| **디자인 시스템 페이지** (claude.ai의 "DINT UI") | 화면을 기획·디자인하는 사람, AI | dint-ui를 보기 쉽게 정리한 페이지: 색, 서체, 컴포넌트 미리보기, 로고. 비공개라서 쓰려면 소유자가 공유해야 합니다 |

### 이럴 때는 여기

| 하려는 일 | 쓸 곳 |
|---|---|
| 발표 자료, 보고서 만들기 | CI 팩 `04_Template` — PowerPoint 16:9, A4 세로, A4 가로 / Word (주식회사 딘트, DINT GLOBAL) |
| 문서·웹·PPT에 로고 넣기 | CI 팩 `01_Logo/svg` (SVG). SVG를 못 쓰는 프로그램은 `01_Logo/original`의 PNG |
| 인쇄·간판에 로고 쓰기 | CI 팩 `01_Logo/original`의 .ai 원본 |
| 컬러 값(HEX·RGB·CMYK) 찾기 | CI 팩 `02_Colour` 또는 CI 가이드 4쪽 |
| 사내에서 디자인 작업할 서체 | CI 팩 `03_Font/EN`, `03_Font/KR` (내부용) |
| 협력사·대행사에 서체 보내기 | CI 팩 `03_Font/FREE`만 보냅니다 (Cinzel, Questrial, Pretendard) |
| 법인명·주소·등록번호 쓰기 | CI 가이드 6쪽 (dint-ui `brand/entities.json`과 같은 내용) |
| 브랜드 규칙 확인 (로고 사용법, 골드 비율, 표기법) | CI 가이드 `DINT_Brand_CI_Spec.pdf` |
| 사내 앱·웹사이트 화면 만들기 | dint-ui 패키지 (`tokens.css`, `components.css`, `site.css`) |
| 화면 디자인 참고, 컴포넌트 모양 보기 | 디자인 시스템 페이지 |

### 지켜야 할 것
- **Trajan Pro 3** 서체 파일은 회사 밖으로 보내지 않고, GitHub에도 올리지 않습니다 (Adobe 유료 서체, 내부 디자인용).
- **Geosans Light**는 사내 디자인에만 쓰고, 웹사이트와 외부 파일에는 Questrial을 씁니다.
- 로고는 글자를 다시 입력하지 않고 반드시 로고 파일을 씁니다.
- 골드는 화면·페이지 면적의 10%를 넘지 않습니다.

### 바뀌면 함께 고칠 곳
두 곳에 같은 내용이 있으므로, 바뀌면 **모두** 고칩니다.

| 바뀐 것 | 고칠 곳 |
|---|---|
| 로고 | CI 팩 `01_Logo/svg` · dint-ui `brand/logo/` · 디자인 시스템 페이지 |
| 컬러 | CI 팩 `02_Colour` + CI 가이드 4쪽 · dint-ui `tokens.css`, `brand/colours.json` · 디자인 시스템 페이지 |
| 법인 정보 (이름·주소·번호) | CI 가이드 6쪽 · dint-ui `brand/entities.json` · Word 템플릿 꼬리말 · 디자인 시스템 페이지 |
| 브랜드 규칙 | CI 가이드 (PDF 다시 만들기, 표지 버전·날짜 갱신) · 필요하면 dint-ui `README.md` |

CI 가이드를 고치면 이전 판을 `_archive/`에 남기고, 표지의 버전과 날짜를 바꿉니다.

---

## English

DINT brand materials live in three places, each for a different audience.

| Place | For | What's in it |
|---|---|---|
| **CI pack** (shared drive `Brand_CI_DINT`) | Designers, all staff (planning, finance, sales), outside partners | The CI guide (HTML and PDF), original logos (.ai, PNG) and SVGs, colour values, fonts, PowerPoint and Word templates |
| **dint-ui** (GitHub `Dint-Global/dint-ui`) | Developers; internal apps and websites | Screen design tokens (CSS), components, the web font (Pretendard), logo SVGs, favicons, colour and company JSON |
| **Design system page** ("DINT UI" on claude.ai) | People planning or designing screens; AI tools | A readable view of dint-ui: colours, type, component previews, logos. It is private; the owner must share it before others can open it |

### Where to go for what

| You want to | Use |
|---|---|
| Make a presentation or report | CI pack `04_Template`: PowerPoint 16:9, A4 portrait, A4 landscape; Word (DINT Inc., DINT GLOBAL) |
| Put the logo in a document, web page or slide | CI pack `01_Logo/svg` (SVG); PNG from `01_Logo/original` where SVG isn't supported |
| Use the logo in print or signage | The .ai master in CI pack `01_Logo/original` |
| Look up colour values (HEX, RGB, CMYK) | CI pack `02_Colour`, or page 4 of the CI guide |
| Design in-house with the brand fonts | CI pack `03_Font/EN`, `03_Font/KR` (internal only) |
| Send fonts to a partner or agency | Only CI pack `03_Font/FREE` (Cinzel, Questrial, Pretendard) |
| Write legal names, addresses, registration numbers | Page 6 of the CI guide (same data as dint-ui `brand/entities.json`) |
| Check a brand rule (logo use, gold ratio, formats) | The CI guide, `DINT_Brand_CI_Spec.pdf` |
| Build an internal app or website screen | The dint-ui package (`tokens.css`, `components.css`, `site.css`) |
| See how screens and components should look | The design system page |

### Rules
- Never send the **Trajan Pro 3** font files outside DINT or commit them to GitHub (paid Adobe font, internal design use only).
- Use **Geosans Light** for in-house design only; websites and files sent outside use Questrial.
- Never retype the logo; always use a logo file.
- Gold stays under 10% of any screen or page.

### When something changes, update every copy

| What changed | Update |
|---|---|
| A logo | CI pack `01_Logo/svg` · dint-ui `brand/logo/` · design system page |
| A colour | CI pack `02_Colour` + CI guide page 4 · dint-ui `tokens.css`, `brand/colours.json` · design system page |
| Company details (names, addresses, numbers) | CI guide page 6 · dint-ui `brand/entities.json` · Word template footers · design system page |
| A brand rule | The CI guide (regenerate the PDF, update version and date on the cover) · dint-ui `README.md` if it applies |

When the CI guide changes, keep the previous edition in `_archive/` and update the version and date on its cover.
