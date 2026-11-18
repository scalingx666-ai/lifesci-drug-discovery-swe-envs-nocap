# Issue

**Title:** Download site: feature list, screenshots and Spin 3D recording

## Description

Adds a **What ChemDraft does** section right after the download button:

- Five groups of short feature bullets — Draw, Inspect, Predict, Spin 3D, Open. Each claim was checked against the code.
- Real screenshots: a Suzuki coupling on the page, the Molecular Inspector's isotope envelope for diclofenac, and its pKa view.
- A looping GIF of Spin 3D turning a helicene, from a screen recording of the Mac app.

Only `site/` changes. Checked locally: no horizontal scroll at 375 px.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43fbb5a27345`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.