# Issue

**Title:** Fix torchrl v0.11 PPO/A2C loss kwargs

## Description

Update torchrl loss kwargs for v0.11:
critic_coef → critic_coeff
entropy_coef → entropy_coeff

This only occurs in `scripts/ppo/ppo.py` and `scripts/a2c/a2c.py`.

Keep config names unchanged (cfg.critic_coef, cfg.entropy_coef, and other _coefs)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `970f324fda95`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.