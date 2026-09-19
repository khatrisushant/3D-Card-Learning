# CardLab

An interactive 3D web experience that teaches the physical anatomy of payment cards — what each part is called, where it sits, what it does, and why it exists.

Built with Three.js (WebGL). The card is real extruded geometry with layered meshes, not an image or a CSS transform.

**Live demo:** https://YOUR-USERNAME.github.io/cardlab/

## Features

- Real 3D card: rounded corners, bevels, layered construction, procedural studio environment map, soft shadows
- Custom orbit controls — drag to rotate, wheel or pinch to zoom, double-click to focus, arrow keys to orbit
- 12 interactive hotspots across the front and back, each with an eased camera move and an information panel
- Flip animation, exploded view, and x-ray mode revealing the antenna loop and chip module
- Guided tour through every component
- Credit vs debit comparison with two live 3D cards in one scene
- Animated payment-flow walkthrough and a card-security section
- 12-question quiz answered by clicking the card itself
- Text-only version and a 2D fallback when WebGL is unavailable
- Keyboard shortcuts: `F` flip · `X` x-ray · `E` explode · `R` reset · arrows orbit · `+` / `-` zoom · `Esc` close

## Running it

No build step. It is one self-contained HTML file.

```bash
git clone https://github.com/YOUR-USERNAME/cardlab.git
cd cardlab
python3 -m http.server 8000   # then open http://localhost:8000
```

Opening `index.html` directly from the file system also works.

## Structure

Educational content is kept separate from rendering. All copy lives in data arrays near the top of the page script:

| Array | Holds |
| --- | --- |
| `CARD_SPECS` | Per-card sample data and palette (credit, debit) |
| `CARD_PARTS` | Every component: `id`, `title`, `side`, `category`, `hotspot`, `cam`, and the teaching copy |
| `FLOW_STAGES` | Stages of the payment-flow section |
| `SEC_TOPICS` | Security topics |
| `QUIZ` | Quiz questions, each referencing a part `id` |
| `COMPARE_ROWS` | Credit vs debit comparison rows |

To add a component, append an entry to `CARD_PARTS`. The 3D viewer, hotspot layer, guided tour, quiz, text version and 2D fallback all read from it. To add a new card type, add an entry to `CARD_SPECS`.

`hotspot: [x, y]` is in card-local units (x ±1.7, y ±1.07). For back-side parts, x is measured as seen when looking at the back.

## Disclaimer

CardLab is an educational demonstration. The bank, card numbers, names, dates and network shown are fictional and do not correspond to any real card or institution. The app never asks for, stores or transmits real card numbers, security codes, PINs, one-time codes or passwords. Illustrations of internal construction are simplified teaching models, not exact representations of any particular card.

## Licence

MIT
