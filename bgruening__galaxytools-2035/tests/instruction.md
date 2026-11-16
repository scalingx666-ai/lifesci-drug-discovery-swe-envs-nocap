# Issue

**Title:** Flye: expose --deterministic and enable in tests 1 and 3

## Description

Expose Flye's upstream `--deterministic` flag in the wrapper (`2.9.6+galaxy1`) and enable it in Test 01 (`pacbio-raw`) and Test 03 (`reduce coverage`) along with `<assert_command>` checks.

### Background
In Flye `2.9.6`, Stage 1 disjointig assembly (`Extender::assembleDisjointigs()` in `src/assemble/extender.cpp`) launches `numThreads` worker threads that concurrently pull seed reads from `allReads` and update the shared `_innerReads` cuckoo hash map (`cuckoohash_map<FastaRecord::Id, size_t>`). When `--threads` (`${GALAXY_SLOTS:-4}`) is high (e.g., 20 cores on multi-core test runners) relative to the small ~420–467 kb *E. coli* test datasets:
- **Test 01 (`pacbio-raw`)**: 20 concurrent threads extend overlapping seeds simultaneously and collide mid-extension, producing 3 fragmented disjointigs instead of 2 and changing the final `assembly_graph.gfa` topology (`446,578` bytes / 106 diff lines vs `result1_assembly_graph.gfa`'s `446,555` bytes with `lines_diff="10"`).
- **Test 03 (`reduce coverage`)**: 20 concurrent threads fragment Stage 1 into 22–27 disjointigs (vs 19 at low thread counts), causing non-deterministic run-to-run variance in `assembly_graph.gfa` (`415,436`–`422,554` bytes vs `420,752 ± 100`) and `consensus.fasta` (`422,197`–`429,405` bytes vs `427,580 ± 100`).

Upstream Flye provides `--deterministic` (`flye/assembly/assemble.py`), which runs Stage 1 (`flye-modules assemble`) single-threaded (`--threads 1`) while keeping Stages 2–5 (`consensus`, `repeat`, `contigger`, `polishing`) multi-threaded (`-t ${GALAXY_SLOTS:-4}`).

### Changes
- `tools/flye/macros.xml`: Bump `@SUFFIX_VERSION@` from `0` to `1` (`2.9.6+galaxy1`).
- `tools/flye/flye.xml`:
  - Expose `--deterministic` boolean parameter (`checked="false"` by default).
  - Enable `deterministic="true"` and `<assert_command><has_text text="--deterministic"/></assert_command>` in Test 01 and Test 03.

### Validation
- `planemo shed_lint --tools --ensure_metadata --urls --fail_level warn --recursive tools/flye` passes with zero warnings.
- Verified with `quay.io/biocontainers/flye:2.9.6--py311h2de2dd3_0` at `-t 20` (both standalone and via Galaxy `2.9.6+galaxy1` with `cores=20`):
  - Test 01 deterministically produces `assembly_graph.gfa = 446,555` bytes (SHA256 `419835a985b3b197c193b0e9e2e6e1e251661ebe50b02c9823dd69d0f747edd0`), matching `result1_assembly_graph.gfa` with **0 diff lines**.
  - Test 03 deterministically produces `assembly_info.txt = 232` bytes (`286 ± 100`), `assembly_graph.dot = 1,796` bytes (`1,840 ± 100`), `assembly_graph.gfa = 420,767` bytes (`420,752 ± 100`), and `consensus.fasta = 427,596` bytes (`427,580 ± 100`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b85231e12e69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.