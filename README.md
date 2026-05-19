# ORCA User Guide

Source for the **ORCA User Guide** — a [Quarto book](https://quarto.org/docs/books/)
covering installation and local runs of TransLink's regional activity-based
modeling workflow. The rendered guide is published to GitHub Pages on every
push to `main`.

## Repository layout

```
.
├── _quarto.yml                   # book definition: chapter order, theme, formats
├── index.qmd                     # landing page / preface
├── chapters/
│   ├── 01-setup.qmd              # Chapter 1 — Setup
│   └── 02-run-model.qmd          # Chapter 2 — Running the Model
├── images/                       # shared figures (referenced from chapters)
├── .github/workflows/publish.yml # CI: render + deploy to GitHub Pages
└── _book/                        # render output (git-ignored)
```

Reading order is controlled by the `chapters:` list in `_quarto.yml`. The
`NN-` filename prefixes only keep things tidy on disk and in pull requests —
they don't determine order on their own.

## Prerequisites

- [Quarto CLI](https://quarto.org/docs/get-started/) 1.4 or newer.
- No Python/Jupyter needed — chapters are prose plus non-executed shell snippets.

## Preview locally

```bash
quarto preview
```

Starts a live-reloading server; edit any `.qmd` and the browser refreshes.

## Build

```bash
quarto render
```

Writes the static site to `_book/` (git-ignored).

## Add a chapter

1. Create `chapters/NN-topic.qmd` with minimal front matter:

   ```yaml
   ---
   title: "Your Chapter Title"
   ---
   ```

2. Add its path to the `chapters:` list in `_quarto.yml`, in the position
   you want it to appear.

## Publishing

`.github/workflows/publish.yml` renders the book and deploys it via GitHub
Pages. **One-time setup after creating the GitHub remote:**

1. Push this repo to GitHub.
2. Go to **Settings → Pages** and set **Source = GitHub Actions**.
3. *(Optional)* Uncomment the `repo-url` / `repo-actions` block in
   `_quarto.yml` and point it at the repo URL to enable the "Edit this page"
   and "Report an issue" margin links.

Every later push to `main` rebuilds and redeploys automatically.
