# Issue

**Title:** support supervised fragmentation

## Description

This adds support for a feature request from Syngenta. They have a set of chemical groups they are interested in, as a set of fragment SMILES, and would like to limit the cuts to those groups, rather than use a more general fragmentation pattern.

These fragment SMILES are rooted using a "*" wildcard atom. For examples, `*c1ccc(O)cc1` for phenol and `*C(C)C` for isopropyl.

The new code converts the fragment SMILES into a SMARTS pattern which matches that SMARTS exactly, for examples, `*-!@[cH0v4]1:[cHv4]:[cHv4]:[cH0v4](-[OHv2]):[cHv4]:[cHv4]:1` and `*-!@[CHv4](-[CH3v4])-[CH3v4]` respectively. (The valence and hydrogen counts must match exactly.)

It then combines the SMARTS into a single recursive SMARTS, like `*-!@[$([cH0v4]1:[cHv4]:[cHv4]:[cH0v4](-[OHv2]):[cHv4]:[cHv4]:1),$([CHv4](-[CH3v4])-[CH3v4])]`, which can be used by the normal mmpdb fragmentation algorithm. The fragmentation format and database schema are unchanged - this is a front-end modification only.

The fragment SMILES can be specified on the "`mmpdb fragment`" command-line either using one `--cut-rgroup` for each SMILES, or by putting the fragment SMILES into a file (one SMILES per line) and specifying the fragment name as `--cut-rgroup-file`.

There is also a new helper command, "`mmpdb rgroup2smarts`" to help users understand the conversion process from rgroup fragment SMILES to SMARTS.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b9bdcae041b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.