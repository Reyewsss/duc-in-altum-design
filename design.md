# Duc in Altum design system

Reference for any site or dashboard in the Duc in Altum family. The CSS lives in `src/dia.css` (Tailwind v4 `@theme` + component classes). This file explains the intent behind it so new pages stay consistent.

## Principles

- **Navy carries weight, gold carries attention.** Backgrounds, headers and sidebars are navy. Gold is for the primary action and small accents only. Never fill large areas with gold.
- **Warm paper, not white.** Page background is ivory (`#F8F5EF`); cards sit on it in white. Sand (`#EBE1D3`) is the default border, not grey.
- **Serif headings, sans body.** Georgia for `h1`-`h3`, Inter for everything else. Headings are navy, body text is ink, secondary text is muted.
- **Soft and rounded.** 24px radius on cards, pill buttons, one soft navy shadow. No hard edges, no drop shadows on text.
- **One system for marketing and app.** Marketing pages use `.section`, `.page-hero`, `.cta-band`. Dashboards use the `.dia-*` shell. Both share the same tokens and `.btn`, `.card`, `.badge`, `.table`, `.field`.

## Colors

| Token | Hex | Use |
|---|---|---|
| `navy` | `#112C54` | Headings, primary surfaces, links |
| `deep-navy` | `#0A1B34` | Sidenav, dark sections, footer |
| `night` | `#071426` | Darkest gradient stop |
| `gold` | `#C49A3A` | Primary button, accents |
| `sunrise-gold` | `#D8AA5A` | Gold on dark backgrounds, active nav |
| `bronze` | `#8C6B26` | Gold hover / text on light |
| `slate` | `#334A68` | Secondary navy text, icons |
| `ink` | `#142033` | Body text |
| `muted` | `#607086` | Secondary text, labels |
| `line` | `#C8D0DA` | Dividers on white |
| `sand` | `#EBE1D3` | Borders, subtle fills |
| `ivory` | `#F8F5EF` | Page background |
| `success` | `#2E6B54` | Approved, positive deltas |
| `danger` | `#8A3C3C` | Errors, rejected, destructive |

Utilities: `bg-navy`, `text-gold`, `border-sand`, etc. Keep contrast: gold text only on navy/deep-navy; on ivory use `bronze` or `navy`.

## Typography

| Role | Class / element | Spec |
|---|---|---|
| Eyebrow | `.eyebrow` | 12px, uppercase, letter-spaced, gold |
| H1 | `h1` | Georgia, `text-h1` (clamp 40-64px), navy |
| H2 | `h2` | Georgia, `text-h2` (clamp 28-40px), navy |
| Lead | `.lead` | 18-20px, muted, max 60ch |
| Body | default | Inter 16px / 1.6, ink |
| Small / meta | `small`, `.text-muted` | 13-14px muted |

Line length: keep prose under `.prose-dia` or ~65ch.

## Spacing and layout

- Content width `1180px` via `.container-page`. Side gutters 16px on mobile, 24px on desktop.
- Vertical rhythm: `.section` 96px, `.section-sm` 56px. Inside cards use 24-32px padding.
- Radii: `rounded-sm` 10px, `rounded-md` 16px, `rounded-lg` 24px (cards), `rounded-xl` 32px, pills for buttons and badges.
- Shadows: `shadow-dia-sm` for cards at rest, `shadow-dia` for hover/raised, `shadow-gold` for the primary CTA only.

## Components

**Buttons** `.btn` + one of `btn-primary` (gold), `btn-secondary` (ivory/sand), `btn-outline`, `btn-navy`, `btn-danger`, `btn-ghost`. Modifiers `btn-sm`, `btn-icon`. One primary per view.

**Surfaces** `.card` (white, shadow), `.card-flat` (no shadow), `.card-ivory`, `.card-dark` (deep-navy, light text), `.quote-card`. `.card-head` for title + action rows.

**Feedback** `.notice` + `notice-success | notice-danger | notice-warning`; `.toast` + `.show`; `.badge` + `badge-gold | badge-success | badge-danger | badge-muted | badge-navy`.

**Forms** `.form-card` > `.form-grid` > `.field` (`.full` to span). Inputs are styled globally; use `aria-invalid="true"` + `.error` for errors, `.hint` for help, `.check` for checkbox rows.

**Tables** `.table`, right-align numbers with `.num`. Put tables inside a `.card` or `.dia-panel`.

**Navigation** `.site-header` / `.nav-wrap` / `.brand` / `.nav-links` for sites; `.site-footer` with `.footer-title`, `.footer-links`, `.footer-bottom`. `.faq` / `.faq-item.open` for accordions.

**Marketing blocks** `.page-hero` (navy gradient, gold eyebrow), `.dark-section`, `.cta-band`, `.criteria-item`.

**Dashboard shell**
```
.dia-app
  .dia-sidenav   (260px, deep-navy; .dia-sidenav-label groups; aria-current on active link)
  .dia-main
    .dia-topbar  (78px; .dia-crumbs + actions)
    .dia-stats > .dia-stat(.accent) > .label / .value / .delta.up|.down
    .dia-grid  > .dia-panel (card with .card-head)
    .dia-tabs  (button[aria-selected])
    .dia-progress, .dia-list > .dia-list-item, .dia-empty
```
Sidenav collapses under `md`; topbar stays sticky.

## Do / don't

- Do use `aria-current`, `aria-selected`, `aria-invalid` for state; the CSS keys off them.
- Do keep mobile first: grids `grid-cols-1 md:grid-cols-2`, never fixed widths.
- Don't introduce new colors or fonts. Add a token to `@theme` in `src/dia.css` if truly needed, then document it here.
- Don't override component classes with inline styles; extend with Tailwind utilities.

## Adding to another site

1. `npm i tailwindcss @tailwindcss/vite`, add the plugin to Vite.
2. Copy `src/dia.css`; in your app CSS: `@import "tailwindcss"; @import "./dia.css";`
3. Load Inter (Google Fonts) or let it fall back to system sans. Georgia is system.
4. Copy the matching block from `src/routes/index.tsx` as a starting point.
