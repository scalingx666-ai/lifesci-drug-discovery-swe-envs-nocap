# Issue

**Title:** #12461 - Refactor: unicorn/prefer-smaller-scope rule violation clean up

## Description

## Summary

Move 11 variable declarations into the narrower loop or conditional blocks where they are used. Type aliases remain unchanged.

- **Loop-local values:** Declare drawing, geometry, distance, and serialization temporaries at their assignment.
- **Conditional values:** Narrow values used only within a branch, including `defaultHeight` and `chainsCollection`.

## Evidence

- **Before:** `let val;` declared before the loop, then assigned and read inside a branch.
- **After:**
  ```ts
  if (rg & (1 << rgi)) {
    const val = rgi + 1;
    res.push(val);
  }
  ```

Verified in the app: n/a — no user-visible behavior changes.

## Merge Danger

**Door:** Two-way

The changes only narrow local variable scope; no public API, serialized output, or persisted settings change.

**Blast Radius:** Low

Impact is limited to the edited local variables.

---

Memory bank: not needed

<!-- START COPILOT CODING AGENT SUFFIX -->

-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc71de9518e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.