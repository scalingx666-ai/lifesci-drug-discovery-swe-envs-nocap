# Issue

**Title:** ci: match changed recipe dirs by prefix in changed-dirs matrix selection

## Description

## Summary

Fixes the silent no-op CI path in `BioNeMo Recipes CI`: PRs that touch **only files deeper than a recipe root** (e.g. `recipes/evo2_phage_gen/src/...`) were getting an **empty unit-tests matrix** and a vacuously green `verify-recipe-tests`.

Root cause: the `changed-dirs` job gets changed paths from `step-security/changed-files` with `dir_names: true, dir_names_max_depth: 3`, which emits depth-3 directory names like `recipes/evo2_phage_gen/src`. The selection jq then **exact-matched** those against recipe dirs (`recipes/evo2_phage_gen`):

```jq
map(select(. as $dir | $changed | index($dir) != null))
```

so deep-only changes never matched, `dirs` came out `[]`, and every downstream test job skipped (`unit-tests (${{ matrix.recipe.name }})` with the uninterpolated matrix name is the tell).

Observed in the wild:

- #1744 — touched `recipes/evo2_phage_gen/{src,tests}` and `recipes/evo2_megatron/examples`; [run 34363831860](https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/34363831860) skipped all test jobs and went green.
- #1742 — same story; that's how the pandas 3.0 breakage fixed in #1744 merged without recipe tests running. It only surfaced in the nightly `schedule` run ([34333760308](https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/34333760308)), which bypasses `changed-dirs` and tests everything.

## Fix

Prefix-match instead of exact-match (trailing slash prevents `recipes/evo2_megatron2` from matching `recipes/evo2_megatron`):

```jq
map(select(. as $dir | $changed | any(. == $dir or startswith($dir + "/"))))
```

This also flows through to the `notebook-tests (evo2_megatron)` gate, which requires `contains(dirs, 'recipes/evo2_megatron')`.

## Audit of the other workflows

- `unit-tests-interpretability-recipes.yaml` — already prefix-matches **full file paths** from `git diff --name-only`; correct as-is.
- `unit-tests-skills.yml` — uses native `on.push.paths` filters; correct.
- `convergence-tests.yml`, `build-dashboard.yml` — `workflow_dispatch` only; no path gating.
- `approvals.yml`, `blossom-ci.yml`, `gh-docs-deploy.yml`, `sync-labels.yml`, `trufflehog.yml` — no path-based job selection.

## Testing

Exercised the new jq expression against the old one on representative inputs:

| changed entries | old | new |
|---|---|---|
| `["recipes/evo2_phage_gen/src", "recipes/evo2_phage_gen/tests", "recipes/evo2_megatron/examples"]` (the #1744 case) | `[]` | `["recipes/evo2_megatron","recipes/evo2_phage_gen"]` |
| `["recipes/vit"]` (root-file change) | `["recipes/vit"]` | `["recipes/vit"]` |
| `["models/llama3/tests"]` | `[]` | `["models/llama3"]` |
| `["recipes/evo2_megatron2"]` (prefix trap) | `[]` | `[]` |
| `[]` | `[]` | `[]` |

Note on this PR's own CI: the change only affects which dirs get *selected*, so the meaningful validation is the table above plus code review. The `ciflow:all` label is applied simply to prove the full suite stays green with the new logic in place (with the label set, the selection branch is bypassed anyway).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fee884bbb0c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.