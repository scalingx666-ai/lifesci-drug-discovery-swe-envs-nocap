# Issue

**Title:** fix: superposition converges instead of hanging when tlast < tau with auc.type "AUClast"

## Description

.

The steady-state loop's zeros guard reset the convergence tolerance every iteration, so structural zeros from `auc.type = "AUClast"`/`"AUCall"` tail handling (when a subject's tlast < tau) made `n.tau = Inf` loop forever. The tolerance logic now distinguishes zeros that can still accumulate (previous behavior kept) from zeros originating after tlast, which can never become nonzero — those converge on the nonzero concentrations with a warning naming the persisting zeros, tlast, and auc.type. A generous 10,000-interval cap errors informatively as a backstop.

Verification: nine reference results (AUCinf steady state, finite n.tau, dose-scaled, multi-subject) are byte-identical before/after, verified by stash-toggling the source; the formerly-hanging Theoph case now returns in ~0.05 s with the expected warning; the cap error path is exercised in tests. Full superposition + TSS test files pass.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34a0394647db`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.