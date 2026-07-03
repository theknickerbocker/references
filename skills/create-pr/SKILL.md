---
name: create-pr
description: Use when writing a commit message or opening a pull request in this repo. Enforces Conventional Commits formatting restricted to the commitlint config-conventional type list, and requires screenshots for visual changes.
---

# Create PR

Guidance for authoring commits and pull requests.

## Commit message format

Follow [Conventional Commits v1.0.0](https://www.conventionalcommits.org/en/v1.0.0/#specification):

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

- The type/scope prefix is required: `type`, optional `(scope)`, optional `!`, then a required `: ` (colon + space).
- The description must immediately follow that prefix with a short, imperative summary (e.g. `fix(sheets): correct A5 margin overflow`, not `fixed` or `fixes`).
- An optional longer body may follow, separated from the description by **one blank line**. The body is free-form and may span multiple paragraphs.
- Optional footers follow the body, separated by one blank line. A footer token uses `-` in place of spaces (e.g. `Reviewed-by`), followed by `: ` or ` #`.
- Breaking changes are marked either both a `!` before the colon (`feat(api)!: ...`) and with a footer:
  ```
  BREAKING CHANGE: <description>
  ```
  `BREAKING CHANGE` (or `BREAKING-CHANGE`) is the one token that **must** stay uppercase — everything else is case-insensitive.

## Allowed types

Only use a type from the `type-enum` defined in [`@commitlint/config-conventional`](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional) — do not invent new types:

| Type | Use for |
|---|---|
| `build` | Changes to the build system or external dependencies |
| `chore` | Maintenance tasks that don't affect shipped code |
| `ci` | CI configuration/scripts |
| `docs` | Documentation only |
| `feat` | A new feature |
| `fix` | A bug fix |
| `perf` | A performance improvement |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `revert` | Reverting a previous commit |
| `style` | Formatting/whitespace changes with no code meaning change |
| `test` | Adding or correcting tests |

## Screenshots for visual changes

If the change being reviewed affects anything visual (UI, layout, styling, rendered output, printable sheets, etc.), the PR description **must** include one or more screenshots demonstrating the change — ideally a before/after pair. Render the change locally and attach the image(s) directly in the PR body; don't rely on a text description alone for visual review.

## PR description

- Title: a single Conventional Commits line summarizing the change (same rules as above).
- Body: summarize what changed and why, and include screenshots per the rule above when applicable.
- Check the repo for a PR template (`.github/pull_request_template.md` or `.github/PULL_REQUEST_TEMPLATE/`) and follow its structure if one exists.

## Merging

A submitted PR must only ever contain a single commit. Squash all commits on the branch down to one before opening the PR (or before it's reviewed, if fixups accumulated during review) — don't rely on the merge step to do this for you. Since squashing collapses the history, the PR title is what becomes the commit message — write it as a valid Conventional Commits line (per the rules above) so the resulting history stays clean and parseable.
