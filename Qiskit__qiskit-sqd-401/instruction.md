# Issue

**Title:** Test against qiskit pre-release wheels from PyPI

## Description

qiskit 2.6.0 broke this repository's notebook tests on Linux, and nothing in CI saw it coming even though `2.6.0rc1` had been on PyPI for two weeks.

`Development version tests` cannot catch this class of bug, however often it runs. It builds qiskit from a git checkout with `python -m build`, which does not enable the `mimalloc` feature the release pipeline does. mimalloc's C component is compiled `-ftls-model=initial-exec`, which sets `DF_STATIC_TLS` on the whole `_accelerate.abi3.so` and forces every thread-local in it — including the one that grew in 2.6.0 — into the small pool glibc reserves for libraries `dlopen`ed after startup. Built without mimalloc, that thread-local gets ordinary general-dynamic TLS and never touches the pool. I confirmed the dev job's build log shows no `--cfg feature="mimalloc"`, and no mimalloc crate compiled at all. See Qiskit/qiskit#17213.

So this installs the published pre-release wheel rather than building one. An exact `==` pin naming a pre-release opts in just that package: pip takes the rc wheel while every other dependency still resolves to a final release. `--pre` is not a substitute — it admits pre-releases of everything, transitive dependencies included.

It only runs while a pre-release is the newest qiskit on PyPI. Once the final release lands, `Latest version tests` resolves that same wheel and this would be redundant, so a gate job checks first and the test job is skipped.

Two details in the gate worth calling out:

- It reads PyPI, not the GitHub releases API. PyPI only lists a version once its wheels are uploaded, which is the artifact under test; a tag appears roughly an hour earlier and would start runs with nothing to install.
- Ordering is PEP 440 via `packaging`, not `sort -V`, which ranks `2.6.0rc1` above `2.6.0` and would leave a stale pre-release winning over its own final release forever.

Replaying the gate against the index as it stood on 2026-10-10 selects `2.6.0rc1`, so this would have run during the rc window and flagged the breakage around 2026-10-03.

The approach follows Qiskit/Qiskit.jl#86, which added an equivalent nightly there. This one is much simpler: that workflow has to build a `Qiskit_jll` through Yggdrasil, whereas here the pre-release wheel can just be installed from PyPI.

The matrix is deliberately narrower than `Latest version tests` — 3.10, 3.14, and macOS 3.14 — since this is a canary rather than full coverage.

`actionlint` is clean. The gate script and the pin are both verified directly; the assembled workflow has only been linted, which is what the `pull_request` path trigger is for — it exercises the workflow in this PR. On such a run with no pre-release outstanding it pins the newest final release instead of skipping, so the machinery still gets tested.

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4a10551fbe8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.