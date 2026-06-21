# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Static single-page website for Hotel Jireh Bacalar (Quintana Roo, Mexico). The entire site lives in one file: `index.html`. There is no build step, no package manager, and no JavaScript framework.

## Development

Open `index.html` directly in a browser — no server required. To preview with a local server:

```bash
python3 -m http.server 8080
```

## Architecture

Everything is self-contained in `index.html`:

- **Inline CSS** — all styles in a single `<style>` block in `<head>`. CSS custom properties (`--naranja`, `--crema`, `--tierra`, etc.) define the color palette.
- **JSON-LD structured data** — two `<script type="application/ld+json">` blocks: one `Hotel` schema and one `FAQPage` schema, both optimized for AI/LLM citation (GEO — Generative Engine Optimization).
- **No JavaScript** — no scripts, no interactivity beyond CSS hover states and smooth scroll.
- **Images** — all referenced from the `images/` folder as relative paths.

## Key design conventions

- Language: Spanish (`lang="es-MX"`), all copy is in Mexican Spanish.
- Font stack: `'Fraunces Display'` (headings/prices) and `'Inter Body'` (body text) — loaded via system font fallbacks; no external font CDN.
- Primary color: `--naranja` (`#E8732B`). Accent/hover: `--naranja-oscuro` (`#C2571B`).
- Breakpoints: 760 px (hides nav, adjusts gallery) and 880 px (hero two-column layout).
- All reservation CTAs link to `https://wa.me/529831019716` (WhatsApp) or `tel:+529831019716`.

## Content and SEO

- Prices, room names, distances, check-in/check-out times, and amenities appear in **three places** that must stay in sync: the visible HTML, the `Hotel` JSON-LD schema, and the `FAQPage` JSON-LD schema.
- The canonical URL is `https://www.hoteljirehbacalar.com/`.
- `og:image` and structured data images reference absolute production URLs, not relative paths.
