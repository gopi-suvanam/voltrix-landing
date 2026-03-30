# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML landing page for **Voltrix** — a Financial Intelligence API. There is no build system, no package manager, and no framework. The entire site is a single file: `index.html`.

The site is deployed via GitHub Pages at `quantforge.scribbler.live` (configured via `CNAME`).

## Development

No build or install step required. Edit `index.html` directly and open it in a browser to preview. Pushing to `main` triggers automatic GitHub Pages deployment.

## Architecture

Everything lives in `index.html` (~1300 lines), structured as:

1. **`<head>`** — Tailwind CDN, Google Fonts (Inter, JetBrains Mono), inline Tailwind config, inline CSS
2. **`<body>`** — 9 page sections: Hero, Offerings, Stats, Features, Endpoints, Agents, Testimonials, Pricing, CTA
3. **`<script>` (end of body)** — Vanilla JS for the interactive API endpoint switcher (`showEndpoint(key)`)

### Styling

- **Tailwind CSS** loaded from CDN (`https://cdn.tailwindcss.com`) with a custom config block in a `<script type="text/javascript">` tag (lines 9–51)
- Custom colors: `forge` (neon green `#00ff87`), `teal`, `blue`, `purple`, `red`, `gold`
- Custom animations: `marquee`, `float`, `glow-pulse`, `slide-up`, `fade-in`
- Reusable CSS classes (defined in inline `<style>`): `.glass`, `.glass-strong`, `.glow-border`, `.glow-border-active`, `.grid-bg`
- Dark background: `#030712`

### Interactive Elements

The only JavaScript is the endpoint switcher:
- `showEndpoint(key)` — toggles visible API example panels (`blackscholes`, `bondprice`, `implied`, `health`)
- Active endpoint gets `.glow-border-active` class and highlighted background

### Key Section IDs

- `#features` — API feature cards
- `#endpoints` — interactive endpoint viewer
- `#agents` — agent-based functionality
- `#pricing` — pricing tiers

All content (text, API examples, pricing) is hardcoded in HTML — there is no backend or dynamic data fetching.
