# Issue

**Title:** Added option for using ASE GUI for orientation

## Description

Adds \`--viewer ase\` flag to use ASE GUI as an alternative to vmol for interactive molecule orientation (\`-I\`). Closing the ASE window confirms the orientation. Updates docs and CLI reference accordingly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9b91231a273`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.