# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Arcana is a tarot-card-themed daily task manager — a single self-contained HTML file (`arcana_20.html`) with inline CSS and JS. It is designed for local use on a Raspberry Pi kiosk. There is no build step, bundler, or package manager.

## Running

Open the HTML file directly in a browser:
```
open arcana_20.html
```

## Architecture

- **Single file:** All markup, styles, and logic live in `arcana_20.html` (~727 lines).
- **State:** Tasks are stored in `localStorage`, keyed per month (`arcana-YYYY-MM`). Old months are auto-cleaned.
- **Rendering:** A `render()` function rebuilds the board HTML from the `state` object on every change — no framework, just template literals and `innerHTML`.
- **Categories (`CATS` object):** Each category has a `label`, `color`, and inline SVG `icon`. Categories are: personal (Miko), health, creative, home, work, car, tennis.

### UI Components
- **Card grid:** Landscape flip-cards (224×152px) with 3D CSS transforms. Front shows icon + title; back shows category + details.
- **Detail overlay:** Expanded card view with a "Done" button.
- **Add modal:** Form for creating new tasks (title, category, details, date).
- **Date strip:** Bottom calendar row with month navigation.
- **Done deck:** Completed tasks collect as small icons at the bottom.

## Style Guide

### Midjourney Prompt Template (for generating new category icons)
```
[SUBJECT], detailed line art illustration, fine cross-hatching technique,
[COLOR] linework on pure black background, front-facing symmetrical portrait,
engraving style, no shading fills, only parallel and cross-hatched strokes,
minimalist, high contrast, single color lines, dark moody atmosphere,
vector art quality --style raw --s 250 --ar 1:1
```
- Use `--seed` with the same value for consistency across icons.
- Output: 1:1 square, black background, single-color line art.

### Category Colors

| Category | Hex | Description |
|----------|---------|------------------------|
| Miko | `#6FA8C8` | Steel blue |
| Health | `#2EBD8A` | Green |
| Creative | `#8B6FE0` | Purple / violet |
| Home | `#D4880A` | Amber / warm gold |
| Work | `#5BA8A0` | Teal |
| Car | `#C74545` | Crimson |
| Tennis | `#C8CC4A` | Tennis ball yellow-green |

### App Design Tokens

| Token | Value |
|-------|-------|
| Background | `#0A0A14` |
| Card BG | `#1E1E28` |
| Text | `#DDDDF0` |
| Muted | `#44445A` |
| Border | `rgba(255,255,255,0.055)` |
| Border highlight | `rgba(255,255,255,0.12)` |

### Typography
- **Card titles / headings:** Cinzel (serif)
- **Body / UI:** DM Sans (light/regular weight)

### Card Specs
- Landscape: 224 × 152 px, border-radius 14px
- Top rim: 2.5px in category color
- Icon size: 72 × 72 px (CSS-constrained)
- Vignette + grain overlays via `::before` / `::after` pseudo-elements

### Icon Format
- All category icons are inline SVGs stored in the `CATS` object's `icon` field.
- Converted via VTracer, optimized with SVGO.
- Black backgrounds removed for transparency against card color.
- Total file size ~7.7MB due to detailed vector paths (acceptable for local kiosk use).
