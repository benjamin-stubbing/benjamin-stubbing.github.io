# benjamin-stubbing.github.io

Personal website, built with [Quarto](https://quarto.org) and hosted on GitHub Pages.

## Working on the site

- Pages are `.qmd` files at the root; essays live in `writing/`. The annual
  `coolest-things-20**` essays still link to Notion and retain `draft: true`
  placeholders. Other essays are Markdown Quarto pages with
  `reference-location: margin` for their notes; images live in `static/writing/`.
- Retired essays and their images are preserved in `_archive/writing/`, outside
  the project’s render paths and public resources.
- The theme is `styles/theme.scss`. Colours and type are set at the top of that file.
- The site header (name and navigation) lives in the template partials
  `styles/title-block.html` and `styles/site-nav.html`; the footer is set in `_quarto.yml`.
- `.claude/launch.json` starts `quarto preview` for the in-app browser.
- `resources/` holds PDFs linked from elsewhere; keep their paths stable.
- The page grid keeps Quarto's named columns, so Quarto's layout features work:
  `reference-location: margin` puts footnotes in the right margin as sidenotes,
  `.column-margin` places asides there, and `.column-page`, `.column-screen-inset`
  and friends span beyond the reading column. Margin content moves inline below 992px.

## Essay formatting

- Keep essay text in Markdown in `writing/`; the shared theme and title partials
  provide the website’s typography, navigation, and layout.
- Main-text block quotations use italic prose, with a separate muted attribution:

  ```markdown
  > *Quoted passage.*
  >
  > [— Author, *Work*]{.attribution}
  ```

- Use Markdown paragraph breaks and hard line breaks for quoted paragraphs,
  verse, and dialogue rather than Notion-specific markup.
- Use Markdown footnotes with `reference-location: margin` for numbered notes.
  The theme leaves a `3rem` gap between the reading column and the margin;
  `--site-note-gap` in `styles/theme.scss` controls this spacing.
- In `writing/rules-for-life.qmd`, margin quotations are plain text in quotation
  marks, with muted attributions, rather than italic block quotes. The introductory
  “N.B.” note is attached to the last sentence of the introduction.
- Long supporting material in Rules for Life lives in numbered appendices,
  linked from the relevant rule using stable heading IDs. Preserve those IDs.
- Quarto groups margin notes for an entire ordered list. Rules for Life uses
  continued lists separated by empty HTML comments before and after rules with
  footnotes, inside `.rules-list`. Preserve explicit numbering and these breaks:
  they keep notes close to their references without changing the visual spacing.

## Retiring an essay

Move its source and any images used only by that essay into `_archive/writing/`,
update the archived image links, and remove public links to the essay. Render the
full site so its old HTML, search entry, and sitemap entry disappear. The archive
is preserved in the repository but excluded from the generated website. See
[`_archive/README.md`](_archive/README.md) for restoration instructions.

Preview locally:

```bash
quarto preview
```

## Publishing

`quarto render` writes the site to `docs/`, which is committed and served by
GitHub Pages (Settings → Pages → Source: branch `main`, folder `/docs`).
Render the full site, check the affected pages and local links, then commit and
push the source, assets, documentation, archive changes, and `docs/` together to
`main`. Avoid editing generated HTML directly or committing local session files.
GitHub Pages deploys the updated `docs/` after the push; confirm the deployment
and the live pages before considering publication complete.
