# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

NULL is a static HTML game archive/library site. There is no build system, no package manager, and no tests — it is purely static HTML/CSS/JS served directly from files.

## Architecture

- **index.html** — Landing page with a single "OPEN LIBRARY" button linking to the library.
- **library.html** — Main hub that displays game cards in a grid. Contains an inline game launcher that loads games in a fullscreen-capable iframe overlay. Uses [vanilla-tilt.js](https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.8.1/vanilla-tilt.min.js) from CDN for card hover effects.
- **Game pages** (granny.html, granny2.html, pvz.html, run3.html, driftboss.html, spacewaves.html) — Minimal wrapper pages that each embed an external game via iframe. pvz.html is unique in that it uses [Ruffle](https://unpkg.com/@ruffle-rs/ruffle) to run a Flash SWF file.

## Design Conventions

- Dark theme throughout: black/dark gray backgrounds (`#000`, `#1a1a1a`), light text (`#eee`, `#fff`).
- Accent color is blue (`#0074D9`, `#001f3f`) used for borders, glows, and hover states.
- All CSS and JS is inline within each HTML file — no external stylesheets or script files.
- Letter-spacing is used heavily on headings/buttons with a negative `margin-right` or reduced `padding-right` to compensate for trailing space.
- Font: Inter (system fallback to Arial/sans-serif).

## Adding a New Game

1. Create a new HTML wrapper page (iframe pointing to the game source, black background, no border).
2. Add a `.game-card` entry in library.html's `.card-container` div with an `onclick="launchGame('newgame.html')"` handler.
