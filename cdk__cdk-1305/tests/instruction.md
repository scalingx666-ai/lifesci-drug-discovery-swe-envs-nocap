# Issue

**Title:** Fix atompairs count fp

## Description

This is the simplest "fix" I could come up with. Under normal operation the binary fingerprint only reports the distance certain atom pairs and only does this uniquely since you will find each pair twice. i.e. 4_C_O and 4_O_C (a carbon and oxygen 4 bonds away) is the same.

The binary fingerprint skip these paths before setting the bits but they were retained the raw fingerprint. This is perhaps reasonable but it messes up the count
fingerprint which ends up thinking there are path which exist which actually don't (you end up with a NPE).

There is a different fix which keeps the raw fingerprint unchanged and only removes the duplicates from the count fp however I consider the duplicates a bug and they should never have been recorded let alone reported.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09edb823cb2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.