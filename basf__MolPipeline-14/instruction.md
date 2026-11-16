# Issue

**Title:** utils: add own _print_elapsed_time

## Description

- sklearn changed location of private _print_elapsed_time
      function in sklearn 1.5, which is breaking our code.
    - To stay consistent but robust against such changes we
      adapted the print functions and implement them ourselves.
      This stops future code breaks due to location changes
      and we stick to a similar logging style as sklearn.
    - If sklearn is doing major changes to their logging style
      we might should adapt in the future. However, that's
      rather unlikely.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3c700708550`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.