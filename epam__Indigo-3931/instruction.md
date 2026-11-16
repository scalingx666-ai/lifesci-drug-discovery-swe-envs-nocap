# Issue

**Title:** #455 – Improve error handling for SCN sections in molfiles

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
An `M  SCN` entry that names an Sgroup never declared by `M  STY` — index 0, an index past the last Sgroup, or any
index when the molfile has no Sgroups — made the V2000 loader fail with the internal
`array: invalid index N (size=M)`. It now reports `molfile loader: M SCN refers to undefined Sgroup N`.

Only the message changes: these inputs were rejected before as well, and an index that falls in a numbering gap
(below the highest declared Sgroup but without its own `M  STY`) keeps being ignored as it is today, so no file that
loads now stops loading.

The end-of-line fix proposed in the issue (moving the `id[2] == '\n'` check out of the SRU branch) is already on
master since 91c175a3a (#2732). The new test covers it too: an `M  SCN` line on a superatom that ends right after the
connectivity code, without the trailing space.

New error text: `M SCN refers to undefined Sgroup %d`, next to the existing `Unexpected end of M SCN` and
`Undefined Sgroup connectivity`.

## Tests
New `api/tests/integration/tests/formats/molfile_scn.py`, inputs in `tests/formats/molecules/455-scn-*.mol`:

- positive: an SRU with `HT` connectivity and the superatom case above. Both are saved and checked with
  `compare_diff` against `tests/formats/ref/455-scn-*.mol`, as `auto_3000.py` does; the SRU reference keeps
  its `M  SCN  1   1 HT` line.
- negative: index 0, an index past the last Sgroup, and no Sgroups at all. Each prints the loader error.

Against master's loader the three negative cases print `array: invalid index …` instead, so the test fails
there.

```
Suites     core GTest 566/566 · Python wrapper unittest 33/33 (setup.py test) · integration harness, all 320 files, CPython
Platforms  macOS arm64 (AppleClang 21, Ninja, Release)
Harness    formats/molfile_scn.py fails on master and passes with the fix; compared with master built the same way,
           no other test changes result. 41 tests fail on this Mac on master too (rendering 24, layout 7, formats 6,
           ketcher 2, cano 1, fingerprints 1) — platform and environment, identical with and without this change.
Style      clang-format 14.0.6 and 19.1.7, black 24.3.0, isort 5.12.0: clean; CI static analysis passed;
           pflake8 6.0.0.post1 does not start on Python 3.14 (configparser.SafeConfigParser is gone).
Not run    locally: Windows and Linux, Jython and IronPython — left to CI.
Jython     the first CI run failed the new test only: it printed a Python list, which Jython shows as
           [u'...']. b2f511e27 prints the lines instead; the other 310 tests passed under Jython.
Review     820349a59 replaces the generated inputs with molfiles and uses compare_diff; molfile_scn.py rerun
           on macOS arm64 against this branch (passes) and against master's loader (fails as above).
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0c22c698bb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.