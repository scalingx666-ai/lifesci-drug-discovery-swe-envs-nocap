# Issue

**Title:** New option retain_ligand_protonation that skips babel and retains ligand protonation state

## Description

Hi Germano,
as talked about in our earlier email communications, I found that sometimes it is beneficial to retain the ligand protonation state specified in pose*.pdb files, and to skip some `babel` steps which remove hydrogen, add hydrogen, and determine ligand total charge. In my last commit I implemented this and added a option `retain_ligand_protonation` with default of not activating. I'd like to merge my changes to main branch of `BAT.py` to make them permanent and stay with future updates.
In my tests, when `retain_ligand_protonation` is not present in `input-sdr.in`, `BAT.py` behaves exactly the same as before this commit and prepared the system successfully; when `retain_ligand_protonation = yes` is present, `BAT.py` successfully retained protonation states and prepared the system successfully.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70edf0d29040`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.