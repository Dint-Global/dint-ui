# DINT brand materials: instructions for AI agents

This file is kept, identical, in two places: the root of the GitHub repository `Dint-Global/dint-ui` and the root of
the CI pack on the shared drive (`Z:\2. 전략기획 부서\14. 기타\21.etc\Brand_CI_DINT`, reachable from office PCs).
If you change one, change the other. The repository may be public, so this file names no links, account details or
operational notes beyond that drive path; ask the user for those. People read `BRAND_GUIDE_MAP.md` (Korean and English) beside it; this file is
the same map with the detail an agent needs.

## The three places, and what each is the source of

| Place | Source of truth for | Audience |
|---|---|---|
| **CI pack** `Z:\…\Brand_CI_DINT` (shared drive) | Brand rules and wording (`DINT_Brand_CI_Spec.html` → `.pdf`), original logos (`01_Logo/original`: .ai, PNG), brand fonts (`03_Font`), Office templates (`04_Template`) | Staff, designers, partners |
| **dint-ui** (GitHub `Dint-Global/dint-ui`, branch `main`) | Screen values and code: `tokens.css` (`--dint-*`), `theme.css` (Tailwind v4), `components.css`, `site.css`, `fonts.css` + `fonts/pretendard/`, `brand/` (logo SVGs, favicons, `colours.json`, `entities.json`) | Developers, internal apps, websites |
| **Design system artifact** "DINT UI" on claude.ai (private; the owner shares the link) | Nothing: it is a published view of dint-ui (tokens, components, logos, copies of `colours.json` and `entities.json` under `assets/Data/`) | People designing screens; AI tools |

The owner decided (2026-11-17) to keep these separate and synchronise by hand. Do not merge them or move files between
them unless asked. Licensed fonts must never reach GitHub, which is the main reason the CI pack stays apart.

## Route the request

| Task | Go to |
|---|---|
| Deck or report | `04_Template`: `DINT_PPT_16x9.potx`, `DINT_PPT_A4.potx` (portrait), `DINT_PPT_A4_landscape.potx`, `DINT_Word_A4_Inc.dotx` (Korean, 주식회사 딘트), `DINT_Word_A4_GLOBAL.dotx` (English, DINT GLOBAL PTE. LTD.) |
| Logo for screen or document | SVG: `01_Logo/svg` or dint-ui `brand/logo/` (identical files, different names; see below) |
| Logo for print | `01_Logo/original` (.ai) |
| Colour values | dint-ui `tokens.css` for UI roles and dark mode; `brand/colours.json` (= CI `02_Colour/dint-colours.json`) for HEX, RGB, CMYK and chart order |
| Company names, addresses, numbers | dint-ui `brand/entities.json` (= CI guide page 6) |
| Brand rules | `DINT_Brand_CI_Spec.html` (v1.1); dint-ui `README.md` repeats the developer-facing subset |
| App or website UI | dint-ui classes and tokens; never hard-code brand hex values in app code |

## Keep the copies identical

When one of these changes, update every copy in the same piece of work and say which ones you touched:

| Data | Copies |
|---|---|
| Logo SVGs | dint-ui `brand/logo/*.svg` ↔ CI `01_Logo/svg/*.svg` ↔ artifact logo assets (uploads; re-upload and update the artifact index) |
| Colours | dint-ui `tokens.css` + `brand/colours.json` ↔ CI `02_Colour/dint-colours.css` + `dint-colours.json` ↔ CI guide colour page (04) ↔ artifact `project/tokens.json` + `assets/Data/colours.json` |
| Company details | dint-ui `brand/entities.json` ↔ CI guide entity page (06) ↔ Word template footers (`04_Template/_source/build_docx.js`, then rebuild) ↔ artifact `assets/Data/entities.json` |
| Brand rules | CI guide ↔ dint-ui `README.md` (developer rules) ↔ artifact `project/README.md` |

Logo file names map like this (dint-ui → CI pack): `dint-wordmark-black` → `DINT_wordmark_black`,
`dint-in-seoul-horizontal-black` → `DINT-IN-SEOUL_horizontal_black`, `dint-in-seoul-stacked-black` →
`DINT-IN-SEOUL_stacked_black`, `dint-inc-lockup-black` → `DINT-Inc_lockup_black`, `dint-global-lockup-black` →
`DINT-GLOBAL_lockup_black`, `dint-d-icon-black-bg` → `DINT_D-icon_black-bg` (same for `-white`, `-gold`, `-white-bg`).
Verify with a byte comparison (`cmp`) after copying.

### Changing the CI guide
1. Copy the current `DINT_Brand_CI_Spec.html` and `.pdf` (and any data file you change) to `_archive/v<old version>/` first.
2. Edit the HTML. Bump the version on the cover, in the `<title>` and in every page footer (`DINT Brand CI v…`), and
   update the change note on the CI Pack page (07).
3. Regenerate the PDF with headless Edge, using Windows paths (a `file:///` URL with Korean characters fails):
   `msedge.exe --headless=new --disable-gpu --no-pdf-header-footer --user-data-dir=<temp dir> --print-to-pdf=<out.pdf> "Z:\…\Brand_CI_DINT\DINT_Brand_CI_Spec.html"`.
   The file appears a moment after the command returns. The guide is 9 A4 pages; if the count changes, a page overflowed.

### Committing in dint-ui
Commit and push only when asked. Branch from `main` first, then merge to `main` when told. End commit messages with the
attribution line the session asks for.

## Brand rules an agent must apply

- Black and white carry the page; gold (`#B8912F`) only points, under 10% of any screen or page. Primary actions are black.
- Small gold text on white uses Gold 700 `#8A6A1F`; on Gold 100 use Gold 800 `#7A5C17`. Never Gold 500 for small text on white.
- Status colours (ok, warn, danger) stay separate from gold. Sale red `#E32C2B` is for sale prices only.
- Never retype or redraw the logo; use the files. Gold logo on black only.
- Customer-facing text says DINT; contracts, invoices and tax documents use the exact legal names: 주식회사 딘트 / DINT Inc.,
  DINT GLOBAL PTE. LTD. Use the addresses in `brand/entities.json` exactly; they are confirmed.
- Dates: `2026. 11. 17.` (Korean), `17 Nov 2026` (English). Money: `1,234,567원`, `₩1,234,567`, `S$1,234.56`.
- Korean external documents use the formal 합니다 style; English uses plain, polite British English.

## Fonts and licences

| Font | Status |
|---|---|
| Trajan Pro 3 | Paid Adobe font, internal design only. Never commit, upload, self-host or send outside DINT. |
| Geosans Light | Internal design only. Don't use it on the web or in files sent outside; use Questrial. |
| Noto Sans CJK KR (`03_Font/KR`) | OFL. Body face for documents and print. |
| Cinzel, Questrial, Pretendard (`03_Font/FREE`) | OFL, safe to share. Cinzel replaces Trajan, Questrial replaces Geosans, Pretendard is the screen body face. |

Office templates use only Office fonts so they open anywhere: Malgun Gothic (body, Korean), Times New Roman in capitals
(display, for Trajan), Century Gothic (English labels, for Geosans).

## Rebuilding the Office templates

Sources are in `04_Template/_source/` (Node scripts `build_ppt.js` and `build_docx.js`, Python and PowerShell
helpers, logo PNGs). `build_ppt.js` also needs `apply_theme.js` from the Claude pptx skill beside it. Install with
`npm install` in that folder (pptxgenjs 3.12.0, docx 9.0.2). Then:

1. `node build_ppt.js`, then `python ea_wrap.py out/<deck>.pptx` for each deck. pptxgenjs tags text as `en-US`, which
   makes PowerPoint break Korean inside words; the script retags it `ko-KR`.
2. `ppt_export.ps1 -Dir <folder>` opens each deck in PowerPoint, exports slide PNGs and saves the `.potx`.
3. `node build_docx.js`, then `python word_wrap.py out/*.docx` (adds a Normal style with `<w:wordWrap/>` = true, East
   Asian layout and no auto-spacing, so Korean wraps by word and "12월" isn't spaced), then `python to_dotx.py out/*.docx`.
4. `word_pdf.ps1` exports PDFs, each in its own Word process with a time limit (Word via COM can hang on the first
   save of a session; stop a stuck WINWORD by its PID, never by name). `pdf_render.ps1` renders pages to PNG for review.
5. Look at every page before copying the `.potx`, `.dotx` and `preview/*.pdf` into `04_Template`.

## Don't

- Don't commit fonts other than Pretendard to dint-ui, or `.ai` files, Office templates or the CI PDF.
- Don't change brand values in only one place.
- Don't share the design system artifact or change its sharing; the owner does that.
- Don't stop processes by name (`taskkill /IM`); other apps may run on the same machine. Stop them by PID.
- Don't add links, account details or operational notes to this repository (the Z: drive path is fine); it may be public.
