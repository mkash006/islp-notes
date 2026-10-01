# ISLP Notes

Notes and worked Python labs for *An Introduction to Statistical Learning with
Applications in Python* (ISLP), published as a Quarto website:

**<https://mkash006.github.io/islp-notes>**

## Contents

- `chapter_notes/` — markdown notes, one file per chapter, written in Obsidian
- `python_labs/` — Jupyter notebooks working through the end-of-chapter labs
- `figs/` — figures referenced in the notes
- `index.qmd` — site landing page and chapter progress table
- `_quarto.yml` — site configuration: navbar, sidebar, render list
- `theme.scss`, `styles.css` — styling, sharing the portfolio site's palette
- `.github/workflows/publish.yml` — renders and deploys on every push to `main`

## How the build works

The site is a Quarto website wrapped around the notes rather than a separate
copy of them. Three choices are worth knowing about if you edit this repo.

**Notes stay where Obsidian put them.** `_quarto.yml` renders
`chapter_notes/*.md` and `python_labs/*.ipynb` in place; nothing is copied,
renamed or preprocessed. Each note carries a small YAML block at the top giving
its title, which Obsidian reads as note properties and Quarto reads as the page
title. Writing a new chapter note means dropping a `.md` file into
`chapter_notes/` and adding one line to the `sidebar.contents` list.

**Notebooks are never re-executed.** `execute.enabled` is `false`, so Quarto
renders the outputs saved in each `.ipynb` as they stand. The consequence is
that a notebook has to be run in Jupyter and saved with its output before the
site will show any result — and in exchange, the build needs no Python
environment, no `ISLP` package and no datasets. That keeps the GitHub Actions
runner to a single Quarto install and keeps builds from breaking when a
dependency moves.

**Maths is LaTeX, rendered by MathJax.** Display equations get their own
horizontal scroll box in `theme.scss` so long matrices do not push the page
sideways on a phone.

## Building locally

```bash
quarto preview        # live reload at localhost
quarto render         # static build into _site/
```

`_site/` and `.quarto/` are generated and git-ignored; the published site comes
from the Actions workflow, not from a committed build directory.

## Source and credit

The book is by James, Witten, Hastie, Tibshirani and Taylor. The text, datasets
and official labs are freely available:

- Book website: <https://www.statlearning.com>
- `ISLP` package and official labs: <https://github.com/intro-stat-learning/ISLP>

All credit for the original material belongs to the authors; this repository
holds only my own notes and code.
