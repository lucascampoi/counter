# Counter

**An open-source font editor that runs in the browser.** Draw glyphs with Bézier tools, test them in real text, and export a TrueType font you can install. No sign-up, nothing to install, one HTML file.

> *Counter* is the typographic name for the enclosed space inside letters like **o**, **e** and **a**.

## Try it

Open `index.html` in any modern browser, or use the GitHub Pages link of this repository. Your work is saved in the browser automatically; use **Download project** to keep a `.counter.json` file.

## What it does

- **Glyph grid**: Latin letters, numbers and punctuation to start, filters by category, script and status, search by name, character or code point (`ç`, `00E7`).
- **Bézier editor**: Pen, Select, Text and Hand tools, corner and smooth nodes, handles, insert nodes on a segment, undo/redo, snap to a configurable grid and to metric lines.
- **Overlaps merge**: shapes that overlap join like a union; only a shape fully inside another becomes a counter.
- **Text tabs**: every tab is a line of text. Type letters straight into the canvas with the Text tool (`T`) and edit any letter in context. A live preview strip in the bottom bar, resizable from 48 to 100 px.
- **Spacing**: drag the side lines to change the left and right sidebearings, or type the advance width.
- **Components**: build a glyph from other glyphs (Á = A + ´). Counter suggests the parts for accented letters, centres the accent and lifts it for capitals. Change the base and every accented letter follows.
- **Kerning**: set a value for each pair (AV, To…) in the stats box; the line reflows live and the pairs are exported in the font's `kern` table.
- **Notes per glyph**: leave a note, assign it to someone (*"Cacá, could you draw these?"*), resolve it with ✓. Notes are saved inside the project file, so they travel with it.
- **Any Unicode character**: glyphs beyond the Basic Multilingual Plane (math letters, historic scripts, emoji) are exported with a format 12 `cmap`.
- **Controls screen**: press `?` (or the `?` under the tools) for a game-style map of every tool's keys and mouse moves, with the current tool highlighted.
- **Room to draw**: hide the font panel with `⌘\`; panning stops at the edges of the line, so you never get lost on the canvas.
- **Export**: a TrueType (`.ttf`) writer built from scratch, no libraries. Cubic curves are converted to quadratics, contour directions are fixed automatically, empty glyphs are left out. The export dialog previews the real font before you download it.

## Keyboard

| Key | Action |
|---|---|
| `V` `P` `T` `H` | Select, Pen, Text, Hand (hold `Space` to pan) |
| `⌘Z` / `⇧⌘Z` | Undo / redo |
| `⌘C` `⌘X` `⌘V` | Copy, cut and paste paths (also between glyphs) |
| `⌘←` / `⌘→` | Previous / next letter in the line |
| Arrows (`⇧` ×10) | Nudge selected nodes |
| `⌥` Click a node | Straight ↔ curve node |
| `⌥` Click a segment | Line ↔ curve segment |
| `Delete` | Delete selected nodes or handles |
| `0` | Fit the line |
| `⌘\` | Show / hide the font panel |
| `?` | Controls screen |
| `⌘↵` | Send a note |

## Project file

`.counter.json` is plain JSON: font metrics (`upm`, `ascender`, `capHeight`, `xHeight`, `descender`, `grid`) and glyphs. Each contour is a list of nodes with their own `in`/`out` handles, in font units, y up, baseline at 0.

## Validation

Exported fonts are checked by loading them in Chrome (which rejects malformed fonts), by [fontTools](https://github.com/fonttools/fonttools) (table parsing and contour direction) and by FreeType rendering.

## Roadmap

- [x] Glyph grid, editor, curves, text tester, TrueType export, notes
- [x] Kerning pairs (`kern` table)
- [ ] Kerning in GPOS and kerning classes
- [x] Components for accented letters
- [ ] Import existing `.ttf`/`.otf` and UFO
- [ ] Masters and variable fonts
- [ ] Real-time collaboration
- [x] Controls screen, collapsible font panel, bounded panning

## About this project

Counter is a learning project. I'm building it to learn how code and design come together, and to grow my own skills at that intersection.

The code is written with [Claude](https://claude.ai), Anthropic's AI assistant, under my direction: I define the product, design the interface in Figma and review every step, and Claude writes most of the code. I'm saying this up front so anyone reading or contributing knows how it was made.

If you'd like to talk about the project, [get in touch through my website](https://lucascampoi.me).

## Contributing

Contributions are welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) to run Counter locally, find your way around the code and open a pull request.

## Credits

- Product and design: **Lucas Campoi**
- Code: written with Claude (Anthropic), directed and reviewed by Lucas Campoi
- Original 2020 concept: Lucas Campoi
- Credits: Felipe Casaprima, Rodrigo Saiani
- Notes per glyph: idea by Rodrigo Saiani
- Typeface of the interface: IBM Plex (SIL Open Font License)

## License

The code is released under the [MIT License](LICENSE). Fonts you make with Counter are yours.
