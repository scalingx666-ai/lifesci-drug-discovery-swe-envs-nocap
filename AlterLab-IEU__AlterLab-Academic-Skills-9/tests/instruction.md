# Issue

**Title:** fix(evals): honest --behavioral reporting (NA, usage-policy refusals, rubric delta)

## Description

## Summary

Running the behavioral eval lane on local Fable surfaced three reporting holes that made `--behavioral` overstate health. All three are fixed, with regression tests and docs.

1. **`NA` counted as success.** The summary printed `"N graded, 0 failed"` even when every call errored/timed out — a run verifying nothing read as green (the same "looks green, proves nothing" class the v2.2.0 README wording fix addressed). Now reports **passed / failed / inconclusive / env-refused**, plus a loud `WARNING: ... verifies NOTHING` when zero evals produce a gradeable verdict. Exit code unchanged — only `FAIL` fails the run, since an environment refusal isn't a skill defect.

2. **Usage-policy refusals were invisible.** The Claude Code CLI refuses benign **biomedical / clinical / genomics** prompts (PubMed E-utilities, nf-core/sarek variant calling, clinical-stats test selection) with a non-zero exit and the AUP text on **stdout** — which the old error path (reading `stderr`) dropped, leaving a content-less generic `NA`. Now detected and surfaced as a distinct **`env-refused`** outcome, with a `NOTE` directing those domains to the API runner.

3. **The delta could contradict its own verdict** (`skilled=FAIL ... NO DELTA both PASS`) because the delta is rubric-only while the verdict also weighs `should_trigger`/`should_not_trigger` assertions. Now labelled **`rubric:`** so it reads as the rubric comparison it is.

## Why this matters

The biomedical cluster (bioinformatics, clinical-research, cheminformatics, biomedical databases, lab-integrations) **cannot be self-graded on the local `claude` CLI** — its safety classifier refuses the prompts before the skill runs. Before this fix those runs printed "0 failed" and looked fine. Now they're unmistakable, and the docs say to use the API lane for those domains. General / methodology / writing / Turkish-academia skills grade fine locally (verified: `akademik-tesvik` 5/5, `venue-templates` 6/6 with real skill-beats-bare deltas).

## Test plan
- [x] `pytest` — 2807 passed (+2 new regression tests in `tests/test_evals.py`)
- [x] `ruff check scripts tests` — clean
- [x] `run_evals.py --strict` — unaffected, still 210/210
- [x] Live check on Fable: `_claude` maps a biomedical prompt → `ENV-REFUSED`, benign prompt → real answer

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc4fe54e2fb1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.