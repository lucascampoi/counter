# Contributing to Counter

Thanks for wanting to help. Counter is small on purpose, so contributing is simple.

## Run it

There is no build step. Clone the repository and open `index.html` in a browser.

```sh
git clone https://github.com/lucascampoi/counter
cd counter
open index.html        # or: python3 -m http.server, then visit localhost:8000
```

Everything lives in that one file: styles, markup and script. The only external request is IBM Plex from Google Fonts.

## Before you start

- **Small things** (a bug, a shortcut, a tweak): open a pull request directly.
- **Bigger things** (a new panel, a change to the `.counter.json` format, a new export table, a refactor): open an issue first so we can agree on the approach.
- `main` is published straight to GitHub Pages, so it must always work.

## How the code is organised

Search `index.html` for these names to find your way around:

| Area | Where to look |
|---|---|
| Data model and saving | `normalize()`, `localStorage` key `counter.font.v4` |
| Shapes (own contours + components) | `glyphOutline(g)` — every reader of a shape goes through it |
| Text line layout and kerning | `layout(tab)` |
| Canvas, zoom and pan | `renderEditor()`, `toScreen` / `toFont`, `clampView()` |
| Tools and pointer input | `onDown`, `onMove`, `onUp` |
| Keyboard shortcuts | the `keydown` handler and the `CONTROLS` array |
| TrueType export | `buildTTF()`, `cubicToQuads()` |

## Product rules

These keep Counter coherent. Please follow them, or say in the PR why a rule should change.

1. **New projects start empty.** Never ship pre-drawn glyphs.
2. **Overlapping shapes merge** (nonzero, direction fixed by nesting). Nothing is ever excluded.
3. **Snap to the grid** and to metric lines is always available.
4. **Saving and exporting are downloads**, not text to copy.
5. **Every tool and icon button has a hover tip** with its shortcut (`data-tip`).
6. **Every new shortcut goes in three places:** the `keydown` handler, the `CONTROLS` array (the `?` screen) and the Keyboard table in the README.
7. **Interface text, code, comments and commits are in English.**
8. **No dependencies.** If you need a library, open an issue first.

## Test before you push

There is no test suite in the repository yet. Before opening a PR:

1. Open the page with the browser console visible: **no errors**.
2. Try your change the way a user would (click, drag, type), in light and dark mode.
3. If you touched shapes, kerning or components, export a font and check that the preview in the export dialog renders it.
4. If you touched `buildTTF()`, also open the exported `.ttf` with [fontTools](https://github.com/fonttools/fonttools):

   ```sh
   pip install fonttools
   python3 -c "from fontTools.ttLib import TTFont; f=TTFont('MyFont-Regular.ttf'); print(f.keys(), f.getBestCmap())"
   ```

## Commits and pull requests

- One topic per commit, with a short message that says what changed and why.
- Keep pull requests focused. Screenshots or a short GIF help a lot for anything visual.
- If you used an AI tool to write code, that is fine — say so in the PR, as this project does in the README.

## Design

The interface is designed in Figma first. If your change adds or reshapes UI, mention it in the PR so the Figma file can be updated to match.

## License

By contributing, you agree that your contribution is released under the [MIT License](LICENSE).
