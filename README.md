# dint-ui

DINT's shared UI foundation and brand kit for every DINT app and website: internal apps (DINT Org, back office,
KPI Tracker, Task Tracker) and customer-facing sites (dint.co.kr, dintkorea.com, campaigns). One set of design
tokens, component classes, a website layer, logo and favicon files, and the Pretendard font. Plain CSS; no JavaScript.

The look follows the **DINT Brand CI Guidelines v1.0** (2026-11): black & white base, gold as the point colour.
The full guide (logo, colour, type, entity names) is kept in the strategy team's CI folder as
`Brand_CI_DINT/DINT_Brand_CI_Spec.pdf`.

| File | What |
|---|---|
| `tokens.css` | `--dint-*` CSS variables: brand palette, role colours (light and dark), type, radius, shadow, layout. The only place values live. |
| `theme.css` | Tailwind v4 `@theme`: maps the tokens to Tailwind names (`bg-surface`, `text-muted`, `text-gold-ink`, `font-display`, …). |
| `components.css` | App component classes in a cascade layer (Tailwind utilities still win): shell + sidebar, page header, card/section, buttons, badges, alerts, forms, filter bar, tables, read-only facts, empty state, stats. |
| `site.css` | Website layer: header, announcement bar, hero, bands, display type, eyebrow, gold rule, product grid/card, price, footer. Load after `components.css`. |
| `brand/logo/` | Outlined SVG logos taken from the original .ai (no font needed; "IN" is smaller than DINT / SEOUL, as in the original): `dint-in-seoul-horizontal`, `dint-in-seoul-stacked`, `dint-wordmark`, `dint-inc-lockup`, `dint-global-lockup`, each `-black`, `-white`, `-gold`; `dint-d-icon`. |
| `brand/favicon/`, `brand/site.webmanifest`, `brand/og-image.png` | Favicon SVG + PNG 32/180/192/512, web manifest, 1200×630 share image. |
| `brand/colours.json` | Brand colours with HEX/RGB/CMYK and roles (for design tools, charts, docs). |
| `brand/entities.json` | Official company details for footers and documents: (주)딘트 / DINT Inc., DINT GLOBAL PTE. LTD. |
| `fonts.css`, `fonts/pretendard/` | Pretendard Variable 1.3.9 (OFL-1.1), dynamic subset. Each app serves `fonts/pretendard/` at `/fonts/pretendard/` (so a strict CSP `font-src 'self'` works). |
| `examples/` | `app.html` (internal app) and `site.html` (website). Serve the repo root and open `/examples/…`. |

## Brand rules for developers

- **Colour:** black (`--dint-black` #111111) and white carry the page. **Gold** (`--dint-gold` #B8912F) only points:
  rules under headings, the current menu item, focus rings, one key number, one gold button per screen. Keep gold
  under ~10% of any screen. Small gold text on white uses `--dint-gold-ink` (#8A6A1F, AA), on gold-soft
  `--dint-gold-on-soft`. Never Gold 500 for small text on white.
- **Primary actions are black** (`.btn-primary`); `.btn-gold` is for a single brand call to action.
- **Status colours** (ok / warn / danger) stay separate from gold. `--dint-sale` red is for sale prices only.
- **Logo:** always an SVG from `brand/logo/`, never retyped in a font. White version on dark/photo backgrounds; gold
  version on black only. The SVGs include their clear space (the cap height on every side), so the letters are a
  third of the image height; minimum horizontal logo width is 160px. On a surface that follows dark mode (sidebar,
  site header), switch to the white logo with `<picture>` (no JavaScript, CSP-safe):

  ```html
  <picture>
    <source srcset="/brand/logo/dint-wordmark-white.svg" media="(prefers-color-scheme: dark)">
    <img src="/brand/logo/dint-wordmark-black.svg" alt="DINT">
  </picture>
  ```
- **Type:** Pretendard for Korean and body text. Display caps use `--dint-font-display` (Trajan Pro 3 → Cinzel →
  Times New Roman) with wide tracking; English labels and menus use `--dint-font-label` (Geosans Light →
  Century Gothic). **Trajan Pro 3 is an Adobe licence and must not be committed or self-hosted** without a web
  licence; Geosans Light's commercial terms need checking before it is served as a web font. Until then the
  fallbacks are used.
- **Entity names:** customer-facing pages say DINT; legal footers and documents use the exact names in
  `brand/entities.json` (DINT Inc., DINT GLOBAL PTE. LTD.).

## Use

With Tailwind v4 (DINT Org, Task Tracker):

```css
@import "tailwindcss";
@import "dint-ui/fonts.css";
@import "dint-ui/tokens.css";
@import "dint-ui/theme.css";
@import "dint-ui/components.css";
@import "dint-ui/site.css"; /* websites only */
```

Without Tailwind (back office, KPI Tracker): load `fonts.css`, `tokens.css`, `components.css` (and `site.css` for
websites) as stylesheets.

Install as a dependency: `"dint-ui": "file:../dint-ui"` (office PC), later `github:Dint-Global/dint-ui`. Copy
`node_modules/dint-ui/fonts/` and `node_modules/dint-ui/brand/` into the app's public folder at build time.

Put `class="dint"` on `<body>` (apps) or `class="dint site"` (websites). In the `<head>`:

```html
<link rel="icon" href="/brand/favicon/favicon.svg" type="image/svg+xml">
<link rel="icon" href="/brand/favicon/favicon-32.png" sizes="32x32" type="image/png">
<link rel="apple-touch-icon" href="/brand/favicon/apple-touch-icon.png">
<link rel="manifest" href="/brand/site.webmanifest">
<meta name="theme-color" content="#111111">
<meta property="og:image" content="/brand/og-image.png">
```

## Patterns

- **Shell:** `.shell` > `nav.sidebar` (`.brand` with the DINT wordmark in a `<picture>`, black / white in dark mode, + `.brand-app` name, `.nav-label`, `a.nav-item[aria-current=page]`, `.account`) + `main.main > .wrap`.
- **Page:** `.page-head` (`.crumbs`, `h1`, `p`, `.actions` on the right), then `.card.section` blocks with `.section-head`.
- **Lists:** `form.filters.card` (GET, so filters are in the URL and links can be shared), then `.card` > `.table-wrap` > `table.table`, `.table-foot` for counts.
- **Detail:** read-only first: `dl.props` in a section with an "편집" button that opens the edit form (`?edit=…`); actions with outside effects are separate buttons.
- **Status:** `.badge` + `-ok` (사용, 성공), `-warn` (대기, 외부), `-danger` (거부, 퇴사), `-accent` (리더, 강조 — gold), plain (사용 안 함).
- **Key number:** `.card.stat.key` — gold value and top rule; one per screen.
- **Destructive actions:** `.btn-danger` in a form with a required `.check` box stating the consequence. No JavaScript confirm.
- **Messages:** `.alert-ok` after saving, `.alert-error` for form errors (keep the user's input), `.alert-info` (gold edge) for notices, `.empty` for nothing to show.
- **Website:** `.announce`, `header.site-header` (`.site-logo`, `nav.site-nav`), `.hero` (`.eyebrow`, `h1.display`, `hr.gold-rule`, `.btn-outline-light`), `section.band` (`-alt`, `-dark`) with `.section-title`, `.product-grid` > `a.product` (`.thumb`, `.code`, `.name`, `.price` with `.was`/`.sale`), `footer.site-footer` (`.cols`, `.legal`).
- **Language:** Korean UI text; short labels; sentences end with a period; dates `2026. 10. 29.` (ko-KR, Asia/Seoul). English sites: `16 Nov 2026`, `S$1,234.56`.
