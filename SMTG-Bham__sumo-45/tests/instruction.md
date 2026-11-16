# Issue

**Title:** ENH: Enable secret points on band structure path

## Description

Allows a special point to be left unmarked on electronic bandplot
by using a label beginning with an '@' character.

This is intended to provide a workaround for a specific problem:
specifying custom k-point paths where some high-symmetry points have
multiple definitions.

For example, in a zincblende cell the U and K points are equivalent
but have different standard coordinates to represent the direction
they are typically approached from. In order to present a band
structure in which the U|K point is simply labelled 'K', one can
set up an appropriate KPOINTS file with

  sumo-kgen --labels "\Gamma,X,K|@U,\Gamma" --kpoints "0 0 0, 0.5 0.0 0.5, 0.625 0.25 0.625 | 0.375 0.375 0.75, 0 0 0"

However, hidden points do not have to be located at discontinuities
and the labels of other special points might be hidden in the same way
in order to create a cleaner plot while exploring specific tours
through the Brillouin zone.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6176c6aff0dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.