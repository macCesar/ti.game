---
name: one-branch-for-related-work
description: "César wants work that is verified together shipped on one branch/PR, never split into PRs that depend on each other"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: daca672b-90d9-4027-90ce-56a5f2c20820
  modified: 2026-08-26T22:56:28.381Z
---

When a plan splits related changes into several branches or PRs, consolidate them into one unless the pieces are genuinely independent. On ti.game (2026-08-24) a plan proposed three separate upstream proposals — the sheet grid fix, density-variant support, and `renderScale` parity. His reaction: *«Pues sería lo mejor NO?? Porque TODO va relacionado.. NO tiene caso mandar un PR para solucionar una cosa que depende de otra en otro PR!!»*

**Why:** a PR whose fix depends on another PR being merged first is unmergeable in practice, and on his side it means installing several module builds to test one story. Things verified by the same run on the same device belong in the same branch.

**How to apply:** before creating a second branch, ask whether the two halves are tested by the same run. If yes, one branch. If genuinely independent — `debug-hud` on that repo is upstream issue #6 and neither half depends on the other — keeping them apart is right, but say the reasoning out loud and offer to merge them. Also expect him to check: he asked separately whether the branch left aside would still be rebased onto the latest `main`. Keep every long-lived branch at zero commits behind upstream. Related: [[fork-main-mirrors-upstream]], [[authorizing-work-is-not-authorizing-commit]].

**The one branch never to rebase: one with an open PR.** Rebasing rewrites the commit, and pushing that rewrites someone else's open pull request. On 2026-08-26 a sync loop rebased every branch that was behind upstream and swept up `docs/feature-interactions`, the branch behind open PR #18, changing its commit from `5295135` to `7aa4630`. Nothing was pushed and it was restored with `git branch -f <branch> origin/<branch>`, but a force-push would have rewritten Michael's PR under him. Before rebasing, check `gh pr list --head <branch>` or simply whether the branch tracks `origin` with a PR open. A branch already published for review is finished work waiting on someone else — GitHub merges it against current `main` on its own, so it never needed the rebase in the first place.
