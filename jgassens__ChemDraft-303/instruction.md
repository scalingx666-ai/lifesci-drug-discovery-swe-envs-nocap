# Issue

**Title:** Add a roadmap, rewrite the README and tidy the repository root

## Description

- **ROADMAP.md**: 1.1.1, 1.2, later 1.x and 2.0 plans.
- **README.md**: rewritten for 1.1.0 (the old one still described early development).
- **chemdraft.ai footer**: Roadmap link.
- **Root tidy**: removes `test-puppeteer.js` and the 0.3.7/0.3.8 release-notes files (no longer in the update feed); moves `PLAN-spin3d-forcefields.md` to `docs/plans/spin3d-forcefields.md` with references updated. The feed files and the 0.3.9/1.0.0/1.1.0 notes stay at the root because installed apps link to them there.

Reviewed by Kimi; its one finding (Reaxys named in the roadmap) was not taken, since Reaxys is a search service the app links to, not a competing drawing program.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e696133f3677`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.