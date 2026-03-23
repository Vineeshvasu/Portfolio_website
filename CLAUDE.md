# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running Locally

No build step required. Serve directly with any HTTP server:

```bash
python3 -m http.server 8000
# Then open http://localhost:8000
```

## Deployment

Push to `main` on GitHub — GitHub Pages deploys automatically to `vineeshvasu.com` (configured via `CNAME`).

## Architecture

**Vanilla HTML/CSS/JS static site** — no frameworks, no package manager, no build tooling.

- [index.html](index.html) — Main portfolio page (hero, about, services, work, experience, contact)
- [script.js](script.js) — All interactivity: theme toggle, custom cursor, scroll animations, counter animations, mobile menu, IntersectionObserver-based fade-ins
- [styles.css](styles.css) — All styles including CSS custom properties for theming; `data-theme` on `<html>` switches dark/light mode
- [case-study.css](case-study.css) — Supplementary styles imported by all four case study pages (alongside `styles.css`)
- [atlas-mobile.html](atlas-mobile.html), [vcardia.html](vcardia.html), [ecg-terminal.html](ecg-terminal.html), [one-mobile.html](one-mobile.html) — Individual case study pages

## Key Conventions

**CSS theming**: All colors, fonts, and transitions are defined as CSS variables (`--bg`, `--text`, `--accent`, `--border`, `--font-heading`, `--font-body`, `--ease`, etc.) at `:root`. Dark/light variants are under `[data-theme="light"]`.

**Scroll animations**: Elements use `data-animate="fade-up"` and `data-delay="100"` (ms) attributes; `script.js` wires these via `IntersectionObserver`.

**Theme persistence**: User's dark/light preference is stored in `localStorage` and applied on page load.

**Case study pages**: Each imports both `styles.css` and `case-study.css`. They don't include `script.js` — interactivity is minimal (mostly CSS-only).

**Accent colors**: Neon green `#d0ff71` (primary), purple `#5e67e6` (secondary). Keep these consistent across new sections.
