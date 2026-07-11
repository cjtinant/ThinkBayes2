# Faster Terminal Workflows in Positron

Two ways to avoid manually copy/pasting commands from scratch notes into the
terminal.

## 1. Send lines/selections directly to the terminal

Positron (VS Code-based) can run text straight from an editor into the terminal,
no copy/paste required.

- Place the cursor on a line in any file (e.g. `scratch.md`) and press
  `Cmd+Enter` — sends that line to the terminal and runs it.
- Select multiple lines first to send/run them as a block.

Works in any file type, including `.md`, `.py`, `.sh` — handy for keeping a
running scratch file of commands you're actively iterating on.

## 2. Turn recurring sequences into scripts

For command sequences you reuse across sessions (not just one-offs), a small
shell script beats re-copying from notes each time.

```zsh
#!/usr/bin/env zsh
# scripts/setup-env.sh
python3.13 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Make it executable once:

```zsh
chmod +x scripts/setup-env.sh
```

Then run it with a single command:

```zsh
./scripts/setup-env.sh
```

### Or use the Makefile

This repo already has a `Makefile` pattern (see root `Makefile`). Adding a
target gives the same effect with an even shorter invocation:

```make
setup:
	python3.13 -m venv .venv
	source .venv/bin/activate && pip install -r requirements.txt
```

Run with:

```zsh
make setup
```

## When to use which

- **Send-to-terminal (`Cmd+Enter`)**: best while a sequence is still in flux —
  exploring, debugging, one-off diagnostics.
- **Script or Makefile target**: best once a sequence has stabilized and you'll
  run it the same way repeatedly (env setup, render steps, etc.).
