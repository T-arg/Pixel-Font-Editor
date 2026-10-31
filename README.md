# Pixel Font Editor

A browser-based editor for small pixel fonts, made for the Arduboy by TEAM a.r.g. Same look as the sprite, tracker and sound editors.

**Open `docs/index.html`** (or the GitHub Pages site) to use it.

## Features
- Every pixel is white, black or transparent (left / right colour swatches like the sprite editor). Draw every glyph on a grid (pencil, eraser, line, rectangle, fill), shift / flip / invert, copy / paste, undo / redo. Typing a character selects its glyph.
- Cell size up to 24x24, any character range 0-255, per-glyph advance width (proportional fonts) with Trim.
- Live 128x64 Arduboy preview of your own text.
- Import: `.h` font arrays (sprite sheet or ID-20 style one-pixel-wide column frames, with optional `_mask` / `_plus_mask` data), PNG/JPG/GIF sheets, TTF/OTF/WOFF fonts (rasterised), `.atmfont` projects.
- Export: Arduboy `.h` (sprite sheet or compact column frames, optional width table, optional "only these characters", `drawText()` helper and the ID-20 `charBox` ticker), PNG sheet, `.atmfont` project.
- Projects are autosaved in the browser.

## Arduboy formats
- **Mask**: none (white pixels only, `drawSelfMasked`), separate `_mask` array (`drawExternalMask`) or interleaved `_plus_mask` (`drawPlusMask`) when the font has black pixels.
- **Sprite sheet**: one Sprites frame per glyph. `Sprites::drawSelfMasked(x, y, font, c - FONT_FIRST)`.
- **Column frames (ID-20 style)**: the font is a sprite sheet of 1-pixel-wide frames, frame 0 is blank. A 3x5 glyph costs 3 bytes. Frame numbers are 8-bit in Arduboy2, so at most 255 columns.

## Build
`build.py` rebuilds `docs/index.html` from `template.html` (logo and donate buttons are read from `../spriteEditor/docs/index.html`, the example font from the ID-20 game's `font.h`).
