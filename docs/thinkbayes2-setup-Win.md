# ThinkBayes2 Environment Setup (Windows, venv, no Anaconda)

Windows equivalent of the Mac/Homebrew/Positron setup — same tools (venv + pip +
Positron), different OS syntax. No Anaconda required.

## 1. Clone the repo

```powershell
git clone https://github.com/AllenDowney/ThinkBayes2.git
cd ThinkBayes2
```

## 2. Check available Python installs

```powershell
py --list
py -3.13 --version
```

If 3.13 isn't listed, install it from python.org (check "Add to PATH" during
install) or via the Microsoft Store.

## 3. Create a virtual environment with 3.13 specifically

```powershell
py -3.13 -m venv .venv
```

## 4. Activate it

```powershell
.venv\Scripts\activate
python --version   # should confirm 3.13.x
```

If PowerShell blocks the activation script with an execution-policy error, run
this once (per user, not admin) and try again:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

## 5. Install dependencies

```powershell
pip install --upgrade pip
pip install -r requirements.txt
```

## 6. Smoke test

```powershell
python -c "import numpy, pandas, matplotlib, empiricaldist; print('ok')"
```

## 7. Open in Positron

Open the cloned folder, then open a notebook (e.g. `notebooks/chap01.ipynb`).
Positron should auto-detect `.venv` and offer it as the interpreter — select it
rather than any system-wide Python.

## Notes vs. Mac setup

- `py -3.13` (Windows launcher) replaces `/opt/homebrew/bin/python3.13`.
- `.venv\Scripts\activate` replaces `source .venv/bin/activate`.
- Everything else (pip, requirements.txt, Positron auto-detection) is identical.
