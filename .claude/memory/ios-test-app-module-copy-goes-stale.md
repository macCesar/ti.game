---
name: ios-test-app-module-copy-goes-stale
description: A hand-built Titanium host app keeps its own copy of the module; rebuilding the module does not update it
metadata: 
  node_type: memory
  type: project
  originSessionId: 65a12a27-d427-469d-9600-c52af437430d
  modified: 2026-08-27T03:37:57.987Z
---

`ti build -p ios -T simulator` from `ios/` fails at its internal `ti create`, so testing ti.game on iOS means a hand-assembled host app with the module unzipped into `modules/iphone/ti.game/<version>/`. That copy is a **snapshot**. Rebuilding the module writes `ios/build/ti.game.xcframework` and `ios/dist/*.zip` and leaves the host app's copy untouched.

The trap is that the JS *is* recopied on every app build, so edits to `example/*.js` show up immediately and everything looks current — while the native code silently stays hours old. On 2026-08-26 the simulator ran a binary from 20:56 against sources edited at 21:53, and I reported "verified by content" after checking only the installed `.js`.

**Why:** partial freshness reads as full freshness. A verification that covers one half of the artifact produces a conclusion about the whole.

**How to apply:** after any change to `ios/Classes/*`, re-unzip `ios/dist/ti.game-iphone-<v>.zip` into the host app and delete the app's `build/` before rebuilding. Verify by hashing, not by dates: `md5 -q` the `libti.game.a` inside the app's `.xcframework` against the one in `ios/build/` — identical means the app links exactly what you compiled. Install with `simctl uninstall` + `install` + `launch`; `ti build -T simulator` compiles correctly but can leave the previously installed bundle in place. Android has none of this — `ti build -p android` rebuilds the module from source every time. See [[verify-both-halves-of-an-artifact]].
