# Issue

**Title:** Fix IndexError in coordinate extraction and improve robustness of line-ending

## Description

- This PR fixes a bug where _extract_symbol_coords throws an IndexError when parsing non-coordinate header lines (e.g., "final structure:"). Original line 93 'if "final structure:" in line:' appeared to cause this bug in "mol/sdf" mode (require line_split[3]).

- The previous implementation was susceptible to failure if lines contained trailing spaces. Using .strip() ensures that any line containing only whitespace is correctly identified as an empty line. The previous implementation failed to detect end_of_structure_block in my xTB log in "xyz" mode because of  an extra space.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07832d8dc13f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.