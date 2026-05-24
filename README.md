# BLDGTYP Design System

The canonical brand and UI reference for all BLDGTYP web products.

**Live site:** https://bldgtyp.github.io/bt-branding/

## What's here

```
bt-branding/
├── index.html              ← Design system site (GitHub Pages)
├── tokens/
│   ├── tokens.css          ← CSS custom properties (colors, fonts, spacing)
│   ├── components.css      ← Reusable component classes (buttons, cards, etc.)
│   └── tokens.json         ← Machine-readable design tokens
├── assets/
│   ├── hero-drafting.png
│   ├── detail-foundation.png
│   └── detail-wall-section.png
└── README.md
```

## Quick start

```html
<!-- 1. Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@200;300;400;500;600;700&family=JetBrains+Mono:wght@300;400&display=swap" rel="stylesheet">

<!-- 2. Tokens (required) -->
<link rel="stylesheet" href="https://bldgtyp.github.io/bt-branding/tokens/tokens.css">

<!-- 3. Components (optional) -->
<link rel="stylesheet" href="https://bldgtyp.github.io/bt-branding/tokens/components.css">

<!-- 4. Set theme -->
<html data-theme="light">
```

**Tokens only** — if you just need colors, fonts, and spacing variables:

```css
@import url('https://bldgtyp.github.io/bt-branding/tokens/tokens.css');
```

Then use custom properties like `var(--accent)`, `var(--bg-page)`, `var(--font-primary)`, etc.

## Architecture

The system is split into two layers so consuming apps can opt in to what they need:

**`tokens.css`** — Pure CSS custom properties. Zero selectors, zero side-effects. Import this everywhere.

**`components.css`** — Reusable UI classes built on top of the tokens. Import this when you want pre-built buttons, cards, typography, etc.

## Available components

### Buttons
- `.btn-primary` — Accent background, white text CTA
- `.btn-ghost` — Transparent with subtle border

### Links
- `.link` — Bold (700), highlight color, dotted underline; solid on hover

### Icon buttons
- `.icon-btn` — 32px square with SVG icon
- `.nav-icons` — Flex container for grouping icon buttons

### Service card
- `.service-card` — Card with accent bottom border, highlight top on hover
- `.service-card__title` — Uppercase, accent-colored title
- `.service-card__subtitle` — Medium weight subtitle
- `.service-card__body` — Body text

### Stats bar
- `.stats-bar` — Always-dark stats grid container
- `.stats-bar__number` — Large accent-colored number
- `.stats-bar__label` — Mono uppercase muted label

### Section label
- `.section-label` — Mono, uppercase, accent-colored section marker

### Graph paper backgrounds
- `.graph-paper` — Standard density (20px minor / 100px major)
- `.graph-paper--medium` — Medium density (12px / 60px)
- `.graph-paper--fine` — Fine density (6px / 30px)

### Typography helpers
- `.type-hero` — Hero title (clamp 3rem–5.5rem)
- `.type-heading` — Section heading (42px)
- `.type-subheading` — Subheading (20px)
- `.type-body` — Standard body (16px)
- `.type-body-lg` — Large body (17px)
- `.type-mono-label` — Mono uppercase accent label
- `.type-mono-nav` — Mono nav link with hover state

### Theme toggle
- `.theme-toggle` — 32px square theme-switch button

## Design tokens (JSON)

For tooling, code generation, or non-CSS consumers:

```
https://bldgtyp.github.io/bt-branding/tokens/tokens.json
```

## Products using this system

| Product | Repo | Status |
|---------|------|--------|
| bldgtyp.com | — | Reference implementation |
| PH-Navigator | [ph-navigator](https://github.com/bldgtyp/ph-navigator) | Planned |
| Design-Phase Reports | — | Planned |

## Fonts

Load from Google Fonts (not bundled to avoid duplication):

```html
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@200;300;400;500;600;700&family=JetBrains+Mono:wght@300;400&display=swap" rel="stylesheet">
```

---

*Building-Type LLC · 2026*
