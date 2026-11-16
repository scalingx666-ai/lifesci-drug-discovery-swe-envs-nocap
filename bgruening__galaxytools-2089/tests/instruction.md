# Issue

**Title:** Flye: enable deterministic mode in remaining unstable tests

## Description

Flye tests 4, 5, 6, and 8 still run parallel disjointig assembly and have intermittent output-size assertion failures. #2035 enabled `--deterministic` in tests 1 and 3; this extends that setting to the other affected tests.

The November 3 harness run used `2.9.6+galaxy1`. Tests 1 and 3 passed, but test 6 produced a 418,007-byte GFA and 424,725-byte consensus, outside its existing bounds of 420,254 ± 2,000 and 427,131 ± 2,000 bytes. Earlier runs also recorded failures in tests 4, 5, and 8.

Enable deterministic mode and add command assertions for tests 4, 5, 6, and 8. Keep the production default, output assertions, and size tolerances unchanged.

Validation:

- Ran the full nine-test candidate suite on ea-dev through Galaxy's test harness, using the installed `2.9.6+galaxy1` runtime and revised test inputs. All original output, metadata, output-count, and existing command assertions passed.
- Repeated tests 4, 5, 6, and 8: all passed again, with byte-identical GFA, consensus, DOT graph, and assembly-info outputs between repeats.
- All 13 cases ran through GCP Batch at 20 cores with `quay.io/biocontainers/flye:2.9.6--py313h7fbb527_1`. Deterministic mode serializes disjointig assembly while later stages retain parallel execution.
- Test 6's deterministic GFA and consensus sizes match its existing expected values exactly: 420,254 and 427,131 bytes.
- Checked that all nine parsed branch tests match the validated effective inputs and original output definitions; the four new command assertions require the observed flag.
- `planemo shed_lint --tools --ensure_metadata --urls --fail_level warn --recursive tools/flye` and `git diff --check` pass.

Harness failure: https://anvilproject.github.io/galaxy-tests/tool-tests/anvil-test-ci-261103-130448/results.html

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27d268d1d450`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.