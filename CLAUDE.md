# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A collection of browser-based games and tools. Currently contains a coin flip game (`coin_flip.html`). No build system, bundler, or package manager — all games are self-contained single HTML files with inline CSS and JS.

## Running a game

```bash
open coin_flip.html        # macOS — opens in default browser
```

No server required. All files open directly from the filesystem.

## Architecture

Each game is a **single self-contained HTML file** with three co-located sections:

1. `<style>` — all CSS, including animations and responsive layout
2. `<body>` — semantic HTML structure
3. `<script>` — all game logic as plain vanilla JS, no frameworks or imports

**coin_flip.html** key mechanics:
- The coin is a CSS 3D `preserve-3d` element with two `.face` children (`.heads` front, `.tails` rotated 180° on Y). The CSS custom property `--end-rotation` is set before each animation so the coin always lands on the correct face.
- `void coin.offsetWidth` (line 219) forces a reflow to restart the CSS animation when re-flipping.
- Game state (`wins`, `losses`, `streak`, `flipping`) lives entirely in module-level JS variables — no localStorage, no backend.

When adding new games, follow the same single-file pattern.

## Git workflow (required every session)

After every meaningful code change:
1. Stage files by name (e.g. `git add coin_flip.html`)
2. Commit with an imperative-mood message under 72 chars
3. Push: `git push origin main`

GitHub remote: `https://github.com/brentrobingreen/gut-biome-app`
