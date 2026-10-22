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
- **Notes per glyph**: leave a note, assign it to someone (*"Cacá, could you draw these?"*), resolve it with ✓. Notes are saved inside the project file, so they travel with it.
- **Export**: a TrueType (`.ttf`) writer built from scratch, no libraries. Cubic curves are converted to quadratics, contour directions are fixed automatically, empty glyphs are left out. The export dialog previews the real font before you download it.

## Keyboard

| Key | Action |
|---|---|
| `V` `P` `T` `H` | Select, Pen, Text, Hand (hold `Space` to pan) |
| `⌘Z` / `⇧⌘Z` | Undo / redo |
| `⌘←` / `⌘→` | Previous / next letter in the line |
| Arrows (`⇧` ×10) | Nudge selected nodes |
| `Delete` | Delete selected nodes or handles |
| `0` | Fit the line |
| `⌘↵` | Send a note |

## Project file

`.counter.json` is plain JSON: font metrics (`upm`, `ascender`, `capHeight`, `xHeight`, `descender`, `grid`) and glyphs. Each contour is a list of nodes with their own `in`/`out` handles, in font units, y up, baseline at 0.

## Validation

Exported fonts are checked by loading them in Chrome (which rejects malformed fonts), by [fontTools](https://github.com/fonttools/fonttools) (table parsing and contour direction) and by FreeType rendering.

## Roadmap

- [x] Glyph grid, editor, curves, text tester, TrueType export, notes
- [ ] Kerning (GPOS)
- [ ] Components for accented letters
- [ ] Import existing `.ttf`/`.otf` and UFO
- [ ] Masters and variable fonts
- [ ] Real-time collaboration

## Credits

- Product and design: **Lucas Campoi**
- Original 2020 concept (*Tenez*): Lucas Campoi, Felipe Casaprima, Rodrigo Saiani
- Notes per glyph: idea by Rodrigo Saiani
- Typeface of the interface: IBM Plex (SIL Open Font License)

## License

The code is released under the [MIT License](LICENSE). Fonts you make with Counter are yours.
