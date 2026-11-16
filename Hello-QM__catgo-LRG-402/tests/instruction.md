# Issue

**Title:** fix(dos): parse adjacent signed PROCAR floats

## Description

## Summary

This PR fixes a PROCAR parsing bug in DOS/PDOS analysis when VASP outputs adjacent signed floating-point values without whitespace.

Author: XCai@JXNU  
Email: 690857@163.com

## Problem

Some PROCAR files contain numeric fields where two float values are directly connected, for example:

0.00000000-0.00000000
0.00000000-0.40000000
0.30000000-0.10000000
1.25E-03-2.50E+01

The previous parser relied mainly on whitespace splitting. When values were concatenated like this, Python tried to parse the whole string as one float and failed with errors such as:

could not convert string to float: '0.00000000-0.00000000'

## Root Cause

VASP PROCAR output can use fixed-width numeric formatting. In some cases, especially for negative values or scientific notation, adjacent float fields may be printed without a separating space.

This is valid PROCAR-style output, but the parser treated whitespace as the only field boundary.

## Solution

This PR adds two layers of protection:

1. Normalize adjacent signed float fields before parsing by inserting missing whitespace between connected numbers.
2. Use regex-based float extraction for sensitive PROCAR sections, including k-point coordinates and projection rows.

The normalization preserves exponent signs, so values like 1.25E-03 are not incorrectly split.

## Verification

The following checks were performed locally:

git diff --check
py -m py_compile extensions/dos-analysis/catgo_dos/io.py

A manual parser assertion was also tested with adjacent signed floats and scientific notation, including:

0.30000000-0.10000000
1.25E-03-2.50E+01
3.0e+02+4.0

All checks passed.

Note: pytest was not run locally because pytest is not installed in the current Python environment.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca53d1fbef94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.