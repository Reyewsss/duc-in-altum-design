# Duc in Altum design system

Tailwind v4 theme + component classes extracted from the foundation website, so dashboards and any connected site share the same look.

- `dia.css` — the whole system: `@theme` tokens, base styles, `@layer components`.
- `index.html` — live showcase of every token and component. Open it directly in a browser (uses the Tailwind browser CDN, no build).

## Use it

Build setup (Vite, Next, Astro, …):

```css
@import "tailwindcss";
@import "./dia.css";
```

No build:

```html
<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
<style type="text/tailwindcss">@import "./dia.css";</style>
```

## Tokens → utilities

| Token | Utilities |
|---|---|
| navy, deep-navy, night, gold, sunrise-gold, bronze, slate, ivory, sand, ink, muted, line, success, danger, warning | `bg-*`, `text-*`, `border-*`, with opacity `bg-gold/12` |
| serif (Georgia), sans (Inter) | `font-serif`, `font-sans` |
| h1, h2, lead, eyebrow sizes | `text-h1`, `text-h2`, `text-lead`, `text-eyebrow` |
| radius sm 8 / md 12 / lg 18 / xl 24 | `rounded-sm` … `rounded-xl` |
| shadows | `shadow-dia-sm`, `shadow-dia`, `shadow-gold` |
| page width 1180 | `.container-page` |

## Components

Marketing: `.eyebrow .lead .section .section-head .btn(-primary|-secondary|-outline|-navy|-ghost|-danger|-sm|-icon) .card .card-flat .card-ivory .card-dark .icon .quote-card .notice(-success|-warning|-danger) .criteria-item .dark-section .page-hero .cta-band .site-header .nav-links .brand .site-footer .sidebar .prose-dia .faq .toast`

Forms: `.form-card .form-grid .field(.full) .hint .error .check .form-note`, plus bare `input/select/textarea/label` are styled.

Data: `.table` (`.num` for right-aligned numbers), `.badge(-gold|-success|-danger|-muted|-navy)`, `.avatar`

Dashboard: `.dia-app .dia-sidenav .dia-sidenav-label .dia-main .dia-topbar .dia-crumbs .dia-stats .dia-stat(.accent) .dia-grid .dia-panel .dia-tabs .dia-progress .dia-list .dia-list-item .dia-empty`

Interactive state is by class/attribute only (no JS shipped): `.faq-item.open`, `.toast.show`, `aria-current="page"`, `aria-selected="true"`, `aria-invalid="true"`.
