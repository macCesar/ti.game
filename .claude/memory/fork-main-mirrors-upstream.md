---
name: fork-main-mirrors-upstream
description: On a fork, main must stay an exact mirror of upstream; our notes never get committed to it
metadata:
  type: feedback
---

On a fork of someone else's project, **`main` is a mirror of upstream and nothing else**. No notes, no reports, no screenshots, no edits to their `AGENTS.md`. Work goes on branches cut from `upstream/main`, never from our `main`.

**Why:** anything committed to our `main` propagates into every branch cut from it, and from there into pull requests. On `ti.game` this produced 507 lines of ours — the four `docs/project/*` session files, a field report, and ten lines added to the maintainer's own `AGENTS.md` — sitting in a branch destined for his repo. César's read is the right one: *"El NO lo usa y NO le va a gustar que metamos lo que para él sería 'basura'."* A diverged fork main also breeds phantom "N commits ahead" counts and duplicate commits when GitHub's sync rebases instead of fast-forwarding.

**How to apply:** keep `docs/project/*` and any report on disk but **untracked**, listed in `.git/info/exclude` so the ignore itself never gets committed either. The `session-log` skill recommends tracking those files in git — that advice assumes the repo is ours, and does not apply to a fork. When a branch is ready for a PR, confirm it carries only code: `git diff --stat upstream/main..branch` should show no `docs/`, no stray images, no context-file edits.

Related: [[never-git-add-all]], [[titanium-lander-drives-ti-game-feedback]]
