# BLDGTYP Branding / Design System

## Links
- **Repo**: https://github.com/bldgtyp/bt-branding
- **Live site**: https://bldgtyp.github.io/bt-branding/
- **Deployed via**: GitHub Pages (`.github/workflows/deploy-pages.yml`)

## What this is
Single-page design system and brand reference for all BLDGTYP web products (bldgtyp.com, PH-Navigator, Design-Phase Reports). Contains CSS design tokens, reusable component classes, and a living demo page.

## File structure
- `index.html` — Design system demo page (all sections: colors, typography, components, patterns, usage, voice)
- `tokens/tokens.css` — CSS custom properties (colors, fonts, spacing). Zero selectors. This is the single source of truth for all color values.
- `tokens/components.css` — Reusable UI component classes built on tokens
- `tokens/tokens.json` — Machine-readable token export (must be kept in sync with tokens.css manually)
- `assets/` — Hero images (PNGs) and logos (SVGs)
- `assets/ph-tools-logo.svg` — PH-Tools molecular hexagon mark (Illustrator source, 550x455 viewBox)

## Local development
Start a local server from this directory:
```
python3 -m http.server 8080
```
Then open http://localhost:8080.

`index.html` uses **relative paths** (`tokens/tokens.css`, `tokens/components.css`) which resolve correctly both locally and on GitHub Pages. No path switching needed.

## Color architecture
Colors use a **semantic alias** pattern for accessible text rendering across themes:

- `--accent` / `--highlight` — base brand colors (theme-invariant, defined in `:root`)
- `--accent-dark` / `--highlight-dark` — darker variants for light backgrounds
- `--accent-text` / `--highlight-text` — **theme-aware aliases** that auto-switch:
  - Light mode: resolves to the `-dark` variant (higher contrast on white)
  - Dark mode: resolves to the base value (higher contrast on dark bg)

**Rule**: Use `--accent-text` / `--highlight-text` for any text-on-background. Use raw `--accent` / `--highlight` for decorative elements (borders, backgrounds, fills) where WCAG text contrast isn't required.

The stats bar is always dark regardless of theme — use base `--accent` there, not `--accent-text`.

## Graph paper backgrounds
The graph paper SVGs in `components.css` use hardcoded `rgba()` values matching the accent color. When changing `--accent`, also update:
- `rgba(R,G,B,0.06)` (minor grid lines) — 6 occurrences
- `rgba(R,G,B,0.12)` (major grid lines) — 3 occurrences

## Accessibility checker
`index.html` includes a live JS-based WCAG contrast ratio checker in the Accessibility section. It computes ratios from hardcoded hex pairs in the `pairs` array near the bottom of the `<script>` block. When changing colors, update those pairs to match.

## Editing colors (iteration workflow)
1. Start local server (`python3 -m http.server 8080`)
2. Edit `tokens/tokens.css` — change accent/highlight values and their variants
3. Update `components.css` — graph paper `rgba()` values to match new accent RGB
4. Update `index.html` — swatch hex values (inline styles in the Colors section) and contrast checker `pairs` array
5. Reload browser to verify; the a11y checker shows live contrast ratios
6. When satisfied, update `tokens/tokens.json` to match, then commit

## Fonts
Loaded from Google Fonts (not bundled): **Outfit** (primary) and **JetBrains Mono** (mono/UI labels).
