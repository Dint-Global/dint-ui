# dint-ui

DINT's shared UI foundation for all internal apps (DINT Org, back office, KPI Tracker, Task Tracker): one set of
design tokens, a small set of component classes, and the Pretendard font. Plain CSS; no JavaScript.

| File | What |
|---|---|
| `tokens.css` | `--dint-*` CSS variables: colours (light and dark), type scale, radius, shadow, layout. The only place values live. |
| `theme.css` | Tailwind v4 `@theme`: maps the tokens to Tailwind names (`bg-surface`, `text-muted`, `border-line`, `rounded-card`, …). |
| `components.css` | Component classes in a cascade layer (Tailwind utilities still win): shell + sidebar, page header, card/section, buttons, badges, alerts, forms, filter bar, tables, read-only facts, empty state, stats. |
| `fonts.css`, `fonts/pretendard/` | Pretendard Variable 1.3.9 (OFL-1.1), dynamic subset: browsers fetch only the subsets a page uses. Each app serves `fonts/pretendard/` at `/fonts/pretendard/` (so a strict CSP `font-src 'self'` works). |

Foundations follow KRDS (the Korean government design system) where they concern Korean text: Pretendard, 1.6 line
height, `word-break: keep-all`, and WCAG AA contrast. The look is DINT's own: a dense admin style, navy brand, blue accent.

## Use

With Tailwind v4 (DINT Org, Task Tracker):

```css
@import "tailwindcss";
@import "dint-ui/fonts.css";
@import "dint-ui/tokens.css";
@import "dint-ui/theme.css";
@import "dint-ui/components.css";
```

Without Tailwind (back office, KPI Tracker): load `fonts.css`, `tokens.css` and `components.css` as stylesheets.

Install as a dependency: `"dint-ui": "file:../dint-ui"` (office PC), later `github:Dint-Global/dint-ui`. Copy
`node_modules/dint-ui/fonts/` into the app's public folder at build time.

Put `class="dint"` on `<body>`.

## Patterns

- **Shell:** `.shell` > `nav.sidebar` (`.brand`, `.nav-label`, `a.nav-item[aria-current=page]`, `.account`) + `main.main > .wrap`.
- **Page:** `.page-head` (`.crumbs`, `h1`, `p`, `.actions` on the right), then `.card.section` blocks with `.section-head`.
- **Lists:** `form.filters.card` (GET, so filters are in the URL and links can be shared), then `.card` > `.table-wrap` > `table.table`, `.table-foot` for counts.
- **Detail:** read-only first: `dl.props` in a section with an "편집" button that opens the edit form (`?edit=…`); actions with outside effects are separate buttons.
- **Status:** `.badge` + `-ok` (사용, 성공), `-warn` (대기, 외부), `-danger` (거부, 퇴사), `-accent` (리더, 강조), plain (사용 안 함).
- **Destructive actions:** `.btn-danger` in a form with a required `.check` box stating the consequence. No JavaScript confirm.
- **Messages:** `.alert-ok` after saving, `.alert-error` for form errors (keep the user's input), `.empty` for nothing to show.
- **Language:** Korean UI text; short labels; sentences end with a period; dates `2026. 10. 29.` (ko-KR, Asia/Seoul).
