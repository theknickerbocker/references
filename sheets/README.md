# sheets

Cheat sheet references. Each sheet is a self-contained, printable A5 page.

## Format

- Source: a single self-contained `.html` file per topic, styled for A5 portrait printing (`@page { size: A5 }`) with all CSS inlined.
- Printing: open the `.html` file in a browser and print (or "Save as PDF") — the page size and margins are already set, so no extra configuration is needed. Select A5 paper in the print dialog if your printer defaults to Letter/A4.
- Why HTML instead of a committed PDF: HTML stays readable and diffable in git and on GitHub; a PDF is a rendered binary output you can regenerate anytime by printing the page.

## Sheets

- [`neovim.html`](neovim.html) — Neovim keybindings (modes, movement, editing, search, windows/buffers, marks/macros)
- [`tmux.html`](tmux.html) — tmux keybindings (sessions, windows, panes, copy mode)
- [`macos.html`](macos.html) — macOS system-wide shortcuts (system, window management, Mission Control, screenshots, Finder, text editing)
