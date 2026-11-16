# Issue

**Title:** #2329 – System should throw an error in case of percent value defined for base not included to ambiguous monomer

## Description

## Generic request
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name does not contain '#'
- [x] base branch (master or release/xx) is correct
- [x] PR is linked with the issue
- [ ] task status changed to "In Review" — left to maintainers (not settable from a contributor account)
- [x] code follows product standards
- [x] regression tests updated

## What changed
A custom mixed base `(IUBcode:XXYYZZQQ)` gives the percentages of A, C, G and T/U (#1619). The IDT loader read only
the percentages of the bases the code stands for and dropped the rest, so `(Y:00333334)` — 33 % G for a base that is
C or T — loaded as if the G share were not there. A non-zero percentage for a base outside the code is now rejected:

`Invalid mixed base 'Y' - percentage is defined for G, but only C, T are allowed.`

For RNA the message names U instead of T (`r(R:00005050)` → `… defined for U, but only A, G are allowed.`). The check
walks the existing `IDT_BASE_TO_RATIO_IDX` table, so there is no second list of bases to keep in step; it runs once,
where the mixed base is defined, and not where it is referenced again.

Checked by hand on the fixed build — rejected: `(Y:00333334)`, `(Y:00505000)`, `(B1:50003000)`, `r(Y:00503020)`,
`r(R:00005050)`; loaded as before: `(Y:00500050)`, `r(Y:00500050)`, `(K:00005050)(K)`, `(R:50005000)`, `(N:25252525)(N)`,
`(N1:10002070)(N1)`.

**One existing test input changed.** In the error table of `idt_to_ket.py`, `r(B1:50003000)(B1)` checks that a mixed
base defined for RNA is not found when referenced as DNA (`Unknown mixed base 'B1'`). Its definition puts 50 % on A,
which `B` (C, G, T) excludes, so with this change it would fail on that instead and stop testing what it was written
for. It is now `r(B1:00503020)(B1)` — valid percentages, same expected error; the reference line changes only in the
input it echoes. A scan of every `(X:NNNNNNNN)` in the repository's test data found no other input the new rule rejects.

## Tests
`api/tests/integration/tests/formats/idt_to_ket.py`, plus the input change above:

- positive: `(Y1:00500050)(Y1)` — percentages only for the bases `Y` allows, checked with `compare_diff` against
  the new `tests/formats/ref/idt_ratio_y.ket`.
- negative: `(Y:00333334)` (DNA, the error names G) and `r(R1:50000050)(R1)` (RNA, the T/U percentage — the
  error names it U).

```
Suites     core GTest 566/566 · Python wrapper unittest 33/33 (setup.py test) · integration harness, all 319 files on this branch, CPython
Platforms  macOS arm64 (AppleClang 21, Ninja, Release)
Harness    formats/idt_to_ket.py fails on master and passes with the fix; compared with master built the same way,
           no test fails with the fix that passes on master. 40 tests fail on this Mac on master too (rendering 24,
           layout 7, formats 6, ketcher 2, fingerprints 1) — platform and environment.
Merge      this branch merged with #3932 (#2381, same file) builds and passes formats/idt_to_ket.py; the two PRs
           merge cleanly in either order.
Style      clang-format 14.0.6, black 24.3.0, isort 5.12.0: clean
Not run    Windows and Linux, Jython and IronPython — left to CI
Review     6813c844d adds the positive case and the RNA one (the #3931 review asked for positive and negative
           scenarios); formats/idt_to_ket.py rerun on macOS arm64 on this branch and merged with #3932: passes.
           The other references regenerate unchanged.
```

The issue carries "Test Automation affected": the error text is new, so a Ketcher test asserting on it will need it.
The sum check of #1619 (`XX+YY+ZZ+QQ=100`) is not part of this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0c22c698bb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.