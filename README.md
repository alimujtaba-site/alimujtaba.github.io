# Portfolio

Static site. No build step, no dependencies — publish as-is.

## Files

| Path | Purpose |
|---|---|
| `index.html` | Publish this. WebP for browsing, PNG for HD zoom. |
| `lossless.html` | PNG-only variant. Identical layout, ~3.4x heavier. |
| `assets/*.png` | Original page scans, 2481x3508 (A4 @ 300dpi), lossless. |
| `assets/webp/*.webp` | Display tier, same pixel dimensions. |
| `.nojekyll` | Stops GitHub Pages running Jekyll over the assets. |

## How quality is preserved

Pages render from WebP but every page is wrapped in `<picture>` with the PNG as
the `<img>` fallback. Clicking a page opens the zoom modal, which reads
`data-hd` and loads the untouched PNG at full 2481px. Browsers without WebP
support skip the `<source>` and load the PNG directly.

The PNGs are byte-identical to the ones originally embedded in the source HTML.

## Deploy

    git init && git add -A && git commit -m "portfolio"
    git branch -M main
    git remote add origin git@github.com:<user>/<repo>.git
    git push -u origin main

Then Settings -> Pages -> Source: `main` / root.

## Local preview

    python3 -m http.server 8000
