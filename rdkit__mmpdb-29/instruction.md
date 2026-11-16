# Issue

**Title:** Use generator for stats_info instead of list

## Description

The stats_info list used too much memory; when loading a table with 1000
structures and 7 properties, it took about 8 gb, and it scales
quadratically.

We now use a stats_info generator, so the stats are inserted into the
database as soon as they are generated, using a limited amount of
memory.

An incompatible, but arguably cosmetic side effect is that the log
messages are slightly less informative because we don't know how many
rows of stats were generated before we start inserting them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f57ebb633efc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.