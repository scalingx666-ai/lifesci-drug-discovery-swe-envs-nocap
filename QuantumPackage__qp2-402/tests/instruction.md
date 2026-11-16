# Issue

**Title:** ci(macos): cache dependencies and stop cancelling in-flight branch builds

## Description

Two commits, each independently droppable, aimed at the macOS job on GitHub-hosted runners.

## Why

Measured on the last green run (`42005019655`, 2026-11-05), 31.5 min total:

| stage | time |
|---|---|
| checkout + `brew install` | 40 s |
| `[1/4]` dependencies | **598 s** (ocaml 298, zlib 98, f77zmq 93, trexio 36, simple_gpu 25, zeromq 20, rest ~20) |
| `[2/4]` qmckl | 45 s |
| `[3/4]` configure | 3 s |
| `[4/4]` `ninja all` | **1231 s** |

Between 2026-10-31 and 2026-11-05, 7 of the 8 non-green `QP macOS` runs were `cancelled` by `cancel-in-progress: true`, not broken; the 8th sat 57.9 min in GitHub's macOS queue with no runner assigned.

## Commit 1 — stop cancelling in-flight branch builds

`cancel-in-progress` is now `${{ github.event_name == 'pull_request' }}`: pushes to `master`/`dev-stable` always run to completion (a cancelled run on a merge commit looks identical to a broken build), PR branches still supersede their own previous run. `workflow_dispatch` added for a manual re-run after a job stays queued.

## Commit 2 — cache the dependency prefix, drop the OCaml source build

**No more OCaml from source.** `configure -i all` includes `ocaml`, which wipes `external/opampack` and builds OCaml 4.12 from source: 298 s, half the dependency stage. It is only needed so that configure's validation gate finds `ocamlc` (the OCaml tools target is not part of `ninja all`). The workflow now installs `ocaml` from a Homebrew bottle and `ci/macos-ci.sh` passes the package list explicitly, minus `ocaml`.

**Dependency cache**, same idea as `configuration.yml` on x86: paths `lib/ include/ bin/ share/ libexec/ external/Python/` (~45 MB), key `qp2-macos-deps-v1-${{ hashFiles('configure', 'ci/macos-ci.sh') }}`.

`configure -i <pkg>` always reinstalls and never checks what is already installed, so a cache alone saves nothing: `ci/macos-ci.sh` now skips the install stage entirely when `lib/.qp2-ci-deps-ok` exists. That marker is written only after a complete install and lives *inside* the cached tree, so a run that dies half-way saves a cache without it and the next run reinstalls instead of trusting a partial tree.

Deliberately **no `restore-keys`**: a partial match could restore an older install together with its marker and pass the gate with stale libraries.

## Why a bad cache cannot produce a false green

On a cache hit, `./configure -c config/gfortran_macos.cfg` still runs the full validation block — `find_lib` for zmq/trexio/qmckl/f77zmq/gmp/z/simple_gpu, `find_exe` for cmake/ninja/ocamlc, `find_python_lib` for docopt/resultsFile — so a stale or incomplete tree fails loudly with the usual `X is not installed` message.

The cached libs embed `/Users/runner/work/qp2/qp2/...` absolute paths: the cache is valid on this repo's hosted runners only, which is the only place it is used. `share/rag` (91 MB of generated corpus) is not in the path list and is not produced by `configure -c`.

## Expected effect

~21.5 min warm, ~27 min for the first (cold) run that populates the cache. The remaining floor is `ninja all` at ~20.5 min on the 4-core hosted runner; it is untouched so the check still measures what users build (`MODE: OPT`, `-Ofast`, `-march=native` unchanged). A cheaper optimization section or the self-hosted Mini would cut further but change what CI means — out of scope here.

No change to the x86 workflows.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9524f23eb6bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.