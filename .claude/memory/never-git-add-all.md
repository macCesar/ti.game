---
name: never-git-add-all
description: Never stage with `git add -A` / `git add .` — name the paths, or a stray file lands in the commit
metadata:
  type: feedback
---

**Never stage with `git add -A`, `git add .` or `git commit -a`.** Stage the exact paths that belong to the change, listed one by one. Before every commit, run `git status --short` and account for each line: if I cannot say why a file is there, it does not go in.

**Why:** César drops files in the repo root to show me — screenshots, exports, scratch images. They are for looking at, never for committing. A blanket `add` sweeps them into the commit and they end up in the fork's history, and from there into any PR. **Error committed (ti.game, 2026-08-19)**: I had just warned him that `font-atlas-visible.png` would get swept in by my `git add -A`, and then committed `1-.png` exactly that way two commits later. His words: *"Por qué commiteaste hasta la captura de pantalla que puse para mostrártela???"*

**How to apply:** `git add path/one path/two`, never a wildcard over the tree. Untracked files that are ours-only (screenshots, session notes, generated previews) belong in `.git/info/exclude` — a local ignore list that is never committed — not in the repo's `.gitignore`, which on a fork belongs to the upstream maintainer.

Related: [[fork-main-mirrors-upstream]], [[respect-upstream-changes]]
