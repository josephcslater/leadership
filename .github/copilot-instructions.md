# Copilot instructions for this repository

This repo is **not a software project** — it holds the content and source
files for a personal presentation, "Compassion as a Superpower" (also titled
"Leadership: as I see it" / "Leadership 101"), by Joseph C. Slater. There is
no build system, package manifest, linter, or test suite. Do not introduce
one unless explicitly asked.

## Content layout

All working files live in `Compassion as a superpower/`:

- `leadership.md` — the canonical, human-edited source. It is a **Jupytext
  MyST-flavored Markdown** file (see the YAML front matter: `formats:
  ipynb,md:myst`). Slides are delimited by MyST cell breaks:
  `+++ {"slideshow": {"slide_type": "slide"}}` starts a new slide, and each
  slide's content is a `#`-level Markdown heading followed by bullets.
- `leadership.ipynb` — the paired Jupyter notebook representation of the same
  content, kept in sync with `leadership.md` via Jupytext. **Edit one and
  regenerate/mirror the other** — don't let them drift; the notebook and the
  `.md` file are two views of the same source (Jupytext's `formats:
  ipynb,md:myst` pairing).
- `leadership.slides.html` — a generated reveal.js slide deck (large,
  generated file — don't hand-edit).
- `reveal.raw.css`, `revealjs-myst.css` — supporting stylesheets for the
  reveal.js export.
- `leadership.pdf`, `leadership.pptx`, `leadership.docx` — generated exports
  of the same content in other formats. Treat these as build artifacts, not
  sources of truth.
- `leadership` (no extension, executable) — a plain-text outline/earlier
  draft of the talk ("Leadership 101"), kept for reference.
- `bibliography.md` — a flat, alphabetized (by author surname) Markdown
  bullet list of book references in APA-like style: `- Author, A. A.
  (Year). *Title*. Publisher.` New citations should be inserted in
  alphabetical order following this exact format.

## Working conventions

- When adding or editing slide content, edit `leadership.md` (the MyST
  source), matching the existing structure: a `# Heading` for the slide
  title, preceded by a `+++ {"slideshow": {"slide_type": "slide"}}` cell
  break, with bullet points (`-`, nested with two-space indents) for content.
- Keep new references added to `bibliography.md` in the same citation style
  and alphabetical order as the existing entries.
- There is no build/test/lint tooling in this repo; do not add npm/Python
  tooling or CI unless the user asks for it.
- `jupytext` and `jupyter-book` are installed as isolated `uv tool`s (not
  system/repo-managed dependencies) and are available on `PATH` via
  `~/.local/bin`:
  - Sync `leadership.md` and `leadership.ipynb`, e.g.
    `jupytext --sync leadership.md` or
    `jupytext --to md:myst leadership.ipynb`.
  - Regenerate the reveal.js deck (`leadership.slides.html`) via
    `jupyter-book`. Confirm the exact invocation with the user before
    overwriting the generated HTML.
