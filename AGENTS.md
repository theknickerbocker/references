# AGENTS.md

This file provides guidance to AI coding agents working in this repository.

## Overview

`references` is a personal reference-material repository, not a software project. There is no build, lint, or test tooling — contents are static, self-contained reference documents (printable cheat sheets) and agent skill definitions. Treat every change as documentation/content authoring, not application development.

## Repository structure

- `sheets/` — Printable, single-page A5 cheat sheets (currently `neovim.html`, `tmux.html`).
- `skills/` — Agent skill definitions scoped to this repo (currently `create-pr`).
- `README.md`, `LICENSE` (MIT).

## Working with sheets/

- **Format**: one self-contained `.html` file per topic — all CSS inlined, no external assets. `@page { size: A5 portrait; ... }` sets the print page size directly in the CSS, so opening the file in a browser and printing (or "Save as PDF") needs no extra configuration.
- **Design system** (Apple HIG-inspired — follow this for new sheets rather than introducing a different style):
  - System sans-serif font stack (`-apple-system, BlinkMacSystemFont, "SF Pro Text", ...`), not monospace.
  - Grayscale palette (`#1d1d1f` text, `#86868b` secondary, `#d2d2d7`/`#f5f5f7` for borders/fills) with a single restrained accent color per sheet (used for keybinding chip text and a small dot bullet on each section heading).
  - Keybindings render as small rounded "chip" `<span>`s, not `<kbd>`/monospace text.
  - Hairline row dividers between entries, not zebra striping.
  - Layout: CSS multi-column (`columns: 2`) with each topic wrapped in a `<section>` using `break-inside: avoid` so a topic doesn't split across columns; inside each section, rows use a two-column grid (key chip(s) + description).
- **Single-page constraint**: content must fit on one A5 page. Browser screen rendering does not reflect `@page` print margins, so don't judge fit from a screenshot alone — render the actual PDF and check it.
- **Verifying a sheet** (no build step exists; render directly with headless Chromium):
  ```
  chromium --headless --disable-gpu --no-sandbox --print-to-pdf=out.pdf file:///path/to/sheet.html
  ```
  Then confirm the PDF is exactly one A5 page: `/MediaBox` should read `0 0 420 595` (A5 portrait in points) and the `/Pages` object's `/Count` should be `1`.
- `sheets/README.md` documents these conventions for humans — keep it in sync if the format changes.
