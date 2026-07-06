# ThinkBayes2 Environment Setup (Homebrew, no Anaconda)

Setup path for running Allen Downey's _Think Bayes 2_ notebooks on macOS (Apple
Silicon), using Homebrew Python and Positron — no Anaconda/conda involved.

## 1. Clone the repo

```zsh
git clone https://github.com/AllenDowney/ThinkBayes2.git
cd ThinkBayes2
```

## 2. Check available Python installs

```zsh
brew list | grep -i -E 'python|conda|mamba|miniforge'
which python3
python3 --version
```

Result: Homebrew had `python@3.13` and `python@3.14` installed, with `python3`
on PATH resolving to 3.14.6. No conda/mamba present.

## 3. Choose Python 3.13, not 3.14

3.14 is very new; some scientific packages (numpy/pandas/matplotlib) can lag on
wheel support for a just-released Python version. 3.13 is the safer, more
compatible choice for this course.

## 4. Create a virtual environment with 3.13 specifically

```zsh
/opt/homebrew/bin/python3.13 -m venv .venv
```

## 5. Activate it (zsh)

```zsh
source .venv/bin/activate
python --version   # confirms 3.13.5
```

## 6. Install dependencies

```zsh
pip install --upgrade pip
pip install -r requirements.txt
```

(The repo also ships an `environment.yml` for conda users — skipped here since
there's no conda on this machine; `requirements.txt` + venv is the pip-native
equivalent.)

## 7. Smoke test

```zsh
python -c "import numpy, pandas, matplotlib, empiricaldist; print('ok')"
```

Printed `ok` — environment confirmed working.

## 8. Open in Positron

Open a notebook (e.g. `notebooks/chap01.ipynb`) and select the `.venv`
interpreter/kernel when prompted — not the system Python 3.14.

## 9. Fork the repo (optional, for your own copy on GitHub)

The original clone points at Allen Downey's repo, not yours — nothing pushes to
your own GitHub until you fork.

1. On GitHub, open `https://github.com/AllenDowney/ThinkBayes2` and click
   **Fork**. This creates a copy under your account (e.g.
   `github.com/cjtinant/ThinkBayes2`).

2. Point your local repo's `origin` at your fork instead of Allen's:

```zsh
   git remote set-url origin https://github.com/cjtinant/ThinkBayes2.git
```

3. Add Allen's original as a separate remote, so you can still pull his future
   updates:

```zsh
   git remote add upstream https://github.com/AllenDowney/ThinkBayes2.git
```

4. Confirm:

```zsh
   git remote -v
```

`origin` should show your fork; `upstream` should show Allen's repo.

5. Push your local state to your fork:

```zsh
   git push -u origin master
```
