# Issue

**Title:** Add outer constructors for "state" types

## Description

When playing around at the REPL, it's nice to not need to specify
the type-parameter in state objects. This provides an outer constructor
that fills the parameters in from the arguments.

One missing case is SmartsParserState, but that seems to be a good case
for forcing the user to supply them directly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da0cfbc006d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.