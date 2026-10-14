---
name: titanium-lander-drives-ti-game-feedback
description: ti.game is pre-1.0 and Michael invites renames/removals; we are effectively its only other consumer, via Titanium Lander
metadata:
  type: project
---

Michael (m1ga) said, 2026-08-18, about `ti.game`: the `TODO.md` list is **not** in priority order — it is a running note list where newer items got appended at the bottom, and the word "priority" in it is stale. He explicitly invites us to *"implement whatever you'll need first or needs a fix"*, and kept the module at **0.x.0 on purpose so things can still be renamed or removed before 1.0.0**. He also reckons we are the only other people building something real with it.

**Why:** this is standing authorization to reorder and reprioritize `TODO.md`, and to propose API changes (including renames) rather than only additive ones. It also means our field report carries unusual weight — there is no other consumer contradicting it.

**How to apply:** keep `docs/ti-game-0.3.0-field-report.md` current as upstream closes the gaps it names, and treat `TODO.md` ordering as ours to improve. What we learn building Titanium Lander is the source of that input — the merged PRs came out of hitting real limits, not from reading the code.

Related: [[respect-upstream-changes]]
