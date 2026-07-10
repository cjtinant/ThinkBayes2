# PDF → Markdown → Notebook Workflow

Three related workflows: converting a PDF to markdown, running/editing that
markdown in Positron, and pairing markdown with a Jupyter notebook using
jupytext.

## 1. PDF to markdown with pdftotext

`pdftotext` (part of poppler) extracts text while preserving layout, which holds
up reasonably well on structured documents (labs, assignments) — better than
tools like `markitdown` for text-heavy PDFs with numbered problems.

```zsh
brew install poppler
pdftotext -layout yourfile.pdf output.txt
```

This gives plain text, not real markdown — expect to hand-edit afterward:

- Add `#`/`##` headers where the original used bold/section titles.
- Fix code blocks: `pdftotext` sometimes collapses multiple lines onto one (e.g.
  `import sys import os` instead of two separate lines) — restore proper line
  breaks and wrap in triple-backtick fences (` ```Python `).
- Rebuild bullet lists: multi-line bullet sections sometimes flatten into a
  single paragraph with inline `-` separators — split back into a real markdown
  list.

Rename `output.txt` to `output.md` once cleaned up.

## 2. Running the .md file in Positron

Positron opens `.md` files directly. Code blocks with a language tag
(` ```Python `) get syntax highlighting, but they are **not** executable in a
plain markdown file — markdown alone has no cell concept. To actually _run_ the
code interactively, either:

- Copy/paste the relevant block into a notebook cell, or
- Pair the file with a notebook using jupytext (below), which turns fenced code
  blocks into real, runnable cells.

## 3. Pairing files with jupytext

Jupytext keeps a `.md` and `.ipynb` version of the same content in sync — edit
either one, run cells in the notebook, and the markdown version stays readable
and git-diff-friendly.

**Install (once per environment):**

```zsh
pip install jupytext
```

**Pair an existing notebook:**

```zsh
jupytext --set-formats ipynb,md notes/chap01_ans.ipynb
```

This creates `chap01_ans.md` alongside `chap01_ans.ipynb` and writes a small
metadata block into the notebook linking the two. From here, opening either file
in Positron and editing/running it keeps both in sync automatically.

**Converting a plain markdown file into a notebook (one-off, no pairing):**

```zsh
jupytext --to notebook yourfile.md
```

Note: for this to produce a useful notebook, the markdown needs real fenced code
blocks (` ```python ... ``` `) — jupytext treats those as code cells and
everything else as markdown/prose cells. A file that's mostly prose with inline
code snippets (not fenced) will convert into one large markdown cell rather than
separate runnable code cells.

**Gotcha: the language tag must be lowercase and exact.** Jupytext only splits a
fenced block into an executable code cell when the tag matches the notebook's
kernel language exactly — `python`, not `Python`. This is easy to miss after
cleaning up a `pdftotext` extraction by hand, since capitalizing "Python" reads
naturally in prose. If a converted notebook comes out as one giant markdown cell
instead of separate code/text cells, check for this first:
`grep '```Python' yourfile.md` and lowercase any matches before reconverting.
