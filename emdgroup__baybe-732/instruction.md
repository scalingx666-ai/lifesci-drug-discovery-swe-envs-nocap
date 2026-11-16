# Issue

**Title:** Use Custom instead of OHE encoded categorical parameter for Non-SHAP tests

## Description

There seem to be machine-dependent non-deterministic failures for the LIME method which is part of our SHAP insight (as non-SHAP extension handled mostly via shap).

The failures do not indicate any particular problem on our side but some internal process causing NaN's when calculating model regression metrics. The test only seems to fail when there is the `Categorical_1` parameter involved, which is a 3 category,  OHE encoded parameter. This was replaced with the custom parameter as it avoids degenerate values which hopefully contribute to avoiding the NaN generations in LIME.

I've [tried this fix 3 times in the `Regular` action](https://github.com/emdgroup/baybe/actions/runs/21355269316) (had to ignore one pip-audit vulnerability to do so in a temporary commit which has been removed again). All runs had no issue, which I take as indication the fix worked. If the issue appears again I would probably add another parameter to the test searchspaces to avoid generation of degenerate points.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43a921e8be28`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.