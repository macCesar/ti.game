---
name: respect-upstream-changes
description: On ti.game, always keep Michael's (m1ga) upstream design; only adjust it with a strong, forward-looking reason
metadata:
  type: feedback
---

On `ti.game`, **always respect the changes Michael (m1ga) makes upstream**. Do not rework, replace or "improve" his design because a different shape seems cleaner. Only adjust something of his when there is a genuinely good reason that serves us later — and say what that reason is.

**Why:** he is the maintainer and the module is his. Our leverage comes from being a real consumer that finds real gaps (six PRs merged so far), not from redesigning his internals. Fighting his design is how a PR gets bounced; building on it is how ours have landed.

**How to apply:** when upstream ships something that overlaps work in progress, the default is to adopt his primitive and delete ours, not to keep a parallel implementation. Before proposing a rework, check whether our code merely *needs fixing up* against his change — usually it does, and calling that a "rebuild" overstates it. If we do keep our own version, the reason goes in `docs/project/decisions.md`.

Related: [[titanium-lander-drives-ti-game-feedback]]
