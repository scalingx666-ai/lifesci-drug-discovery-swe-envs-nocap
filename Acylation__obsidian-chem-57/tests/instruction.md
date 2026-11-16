# Issue

**Title:** Support inline smiles

## Description

Introduce the inline syntax for smiles rendering, something like
```markdown
`$smiles=c1cccccc1`
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b463490d6042`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.