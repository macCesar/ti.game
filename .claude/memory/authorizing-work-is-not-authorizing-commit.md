---
name: authorizing-work-is-not-authorizing-commit
description: "Go ahead" on a task authorises writing the change, never committing it — César reviews first, always
metadata:
  type: feedback
---

When César approves a piece of work — *"arrancamos con X"*, *"dale"*, *"sí"* — he is authorising me to **write** the change. He is not authorising the commit. Make the edits, show what changed, and stop. The commit waits for the word.

**Why:** he reads every diff that goes into a repository, and more so when it is headed for someone else's project under his name. **Error committed (ti.game, 2026-08-19)**: he said *"OK.. arrancamos con la documentación"*, I wrote two files and committed them in the same turn. His reply: *"hiciste los cambios y commiteaste TODO??? NI siquiera ví qué cambios le hiciste.."* The global CLAUDE.md already forbids this; the gap was reading approval-of-task as approval-of-commit.

**How to apply:** end the turn with the diff summarised and the tree dirty. Say what changed and where, not "shall I commit?" — that question is the other anti-pattern. If a commit already happened, `git reset --mixed HEAD~1` puts the decision back in his hands without losing a line.

Related: [[never-git-add-all]]
