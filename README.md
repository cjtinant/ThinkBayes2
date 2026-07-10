# ThinkBayes2 (Jason's fork)

This is a personal fork of Allen Downey's
[Think Bayes 2](http://allendowney.github.io/ThinkBayes2), used while auditing
the Bayesian statistics course (Math 452/552) with Kyle Caudle at SD Mines. It
documents my own environment and workflow choices, distinct from the course's
standard Anaconda setup, for my own reference and for anyone else curious about
the alternative path.

**All original book content, notebooks, and license terms are Allen Downey's.**
See [the original repo](https://github.com/AllenDowney/ThinkBayes2) and
[the free HTML version of the book](http://allendowney.github.io/ThinkBayes2)
for the canonical source. Licensed under
[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).

## What's different in this fork

- **Environment**: Homebrew Python + a project-local `venv`, not Anaconda. See
  [`docs/thinkbayes2-setup.md`](docs/thinkbayes2-setup.md) (Mac) and
  [`docs/thinkbayes2-setup-Win.md`](docs/thinkbayes2-setup-Win.md) (Windows) for
  step-by-step setup, plus reasoning on why venv vs. conda.
- **Editor**: [Positron](https://positron.posit.co/), not Jupyter Notebook —
  auto-detects the `.venv` interpreter directly, no separate kernel registration
  step required.
- **`notes/`**: my own worked answers to the book's chapter exercises. Some are
  paired with [jupytext](https://jupytext.readthedocs.io/) so a `.md` version
  sits alongside the `.ipynb` — lets me edit/diff in markdown while still
  running cells in Positron.
- **`math552_labs/`**: lab writeups for Kyle's course, converted from PDF
  assignment sheets to markdown.

## Running the notebooks

Follow [`docs/thinkbayes2-setup.md`](docs/thinkbayes2-setup.md) (or the Windows
equivalent) to set up the environment, then open any notebook in `notebooks/` or
`notes/` in Positron.

For the standard Anaconda-based path (what the course officially uses), see the
[original repo's README](https://github.com/AllenDowney/ThinkBayes2) and
`environment.yml`.
