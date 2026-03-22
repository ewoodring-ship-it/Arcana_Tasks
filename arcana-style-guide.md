# Arcana — Style Guide & Reference

---

## Midjourney Prompt Template

### Base Prompt

```
[SUBJECT], detailed line art illustration, fine cross-hatching technique,
[COLOR] linework on pure black background, front-facing symmetrical portrait,
engraving style, no shading fills, only parallel and cross-hatched strokes,
minimalist, high contrast, single color lines, dark moody atmosphere,
vector art quality --style raw --s 250 --ar 1:1
```

### Tips for Consistency

- Use `--seed` with the same value across all prompts once you get a result you like.
- If the hatching density doesn't match the dog illustration, try adding `in the style of vintage scientific illustration` or `copperplate engraving style`.
- Output should be 1:1 square, black background, single-color line art.

---

## Category Definitions

| Category   | Subject Description                                      | Status    |
|------------|----------------------------------------------------------|-----------|
| Miko       | Portrait of a blue heeler dog (blue linework)            | Done      |
| Health     | Anatomical human heart wrapped in botanical vines/leaves | Done      |
| Creative   | Quill feather pen with ink drops                         | Done      |
| Home       | Cottage with chimney, surrounded by trees and garden     | Done      |
| Work       | Open book with radiating light, ornate baroque frame     | Done      |
| Car        | Classic steering wheel with dashboard gauges             | Done      |
| Tennis     | Tennis racket with ball, close-up front view             | Done      |

---

## Color References

| Category   | Hex Code   | Line Color in Illustration | RGB              |
|------------|------------|----------------------------|------------------|
| Miko       | `#6FA8C8` | Steel blue (matches illustration) | 111, 168, 200    |
| Health     | `#2EBD8A` | Green                       | 46, 189, 138     |
| Creative   | `#8B6FE0` | Purple / violet             | 139, 111, 224    |
| Home       | `#D4880A` | Amber / warm gold           | 212, 136, 10     |
| Work       | `#5BA8A0` | Teal                        | 91, 168, 160     |
| Car        | `#C74545` | Crimson                     | 199, 69, 69      |
| Tennis     | `#C8CC4A` | Tennis ball yellow-green     | 200, 204, 74     |

---

## App Design Specs

### Typography
- **Headings / Card Titles:** Cinzel (serif, Roman inscriptions feel)
- **Body / UI:** DM Sans (light/regular weight)

### Key Colors
- **App Background:** `#0A0A14`
- **Card Background:** `#1E1E28` (charcoal violet)
- **Text:** `#DDDDF0`
- **Muted Text:** `#44445A`
- **Border:** `rgba(255,255,255,0.055)`
- **Border Highlight:** `rgba(255,255,255,0.12)`

### Card Dimensions
- **Shape:** Landscape — 224 × 152 px
- **Border Radius:** 14px
- **Top Rim:** 2.5px in category color
- **Icon Size:** 72 × 72 px (CSS-constrained)

### Image Format
- All 7 category icons are inline SVGs (converted via VTracer, optimized with SVGO).
- Black backgrounds removed for true transparency against card color.
- SVGs stored as raw markup in the `CATS` object `icon` field.
- File size ~7.7MB due to detailed vector paths — fine for local Pi kiosk use.

---

## File Inventory

| File             | Purpose                                      |
|------------------|----------------------------------------------|
| `arcana.html`    | Main dashboard — single self-contained file  |
| `arcana-style-guide.md` | This reference document             |

---

*Last updated: March 2026*
