# benjamin-stubbing.github.io

Personal website, built with [Quarto](https://quarto.org) and hosted on GitHub Pages.

## Working on the site

- Pages are `.qmd` files at the root. Essays that still live on Notion have
  placeholder pages in `writing/`, marked `draft: true` so they are not published.
- The theme is `styles/theme.scss`. Colours and type are set at the top of that file.
- The site header (name and navigation) lives in the template partials
  `styles/title-block.html` and `styles/site-nav.html`; the footer is set in `_quarto.yml`.
- `.claude/launch.json` starts `quarto preview` for the in-app browser.
- `resources/` holds PDFs linked from elsewhere; keep their paths stable.
- The page grid keeps Quarto's named columns, so Quarto's layout features work:
  `reference-location: margin` puts footnotes in the right margin as sidenotes,
  `.column-margin` places asides there, and `.column-page`, `.column-screen-inset`
  and friends span beyond the reading column. Margin content moves inline below 992px.

Preview locally:

```bash
quarto preview
```

## Publishing

`quarto render` writes the site to `docs/`, which is committed and served by
GitHub Pages (Settings → Pages → Source: branch `main`, folder `/docs`).
Render, then commit and push the source and `docs/` together.
