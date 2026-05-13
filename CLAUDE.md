# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the game

Open `index.html` directly in a browser — no build step, no server, no dependencies.

```bash
open index.html        # macOS
```

## Architecture

Everything lives in a single file (`index.html`): HTML structure, CSS, and JavaScript are all inline. There is no bundler, framework, or package manager.

**Game state** is held in three module-level variables:
- `board` — 9-element array of `''`, `'X'`, or `'O'`
- `current` — whose turn it is (`'X'` or `'O'`)
- `over` — boolean, blocks clicks after the game ends

**Win detection** (`checkWin`) compares the board against `WINS`, a hardcoded array of the 8 winning index triplets. It returns the matching triplet (used to highlight cells) or `null`.

**Score** (`scores = { X, O, D }`) persists across rounds in memory only — it resets on page reload.

**DOM mapping:** cells are `<div data-i="N">` elements. CSS classes drive all visual state: `.taken` disables hover, `.x`/`.o` set the mark color, `.win` adds the glow highlight, and `#status.winner` turns the status line red.

## Git & GitHub workflow

Commits are pushed to `https://github.com/wisewalk/tictactoe`. After every change:

```bash
git add index.html
git commit -m "short imperative description of what changed"
git push
```

Keep commit messages in the imperative mood ("add AI opponent", not "added AI opponent").
