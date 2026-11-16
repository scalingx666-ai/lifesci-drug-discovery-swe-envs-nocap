# Issue

**Title:** Varattach matching

## Description

Adds support for variable attach matching in SMARTS. I've been doing some work on this at NextMove recently and need to support in CDK to get the highlight working correction Arthor. To get reasonable support it's not much code at all but allows us to support queries like:

![](https://www.simolecule.com/cdkdepict/depict/bot/svg?smi=n1ccc2c1cccc2.*c1ncccc1.*Cl%20%7Cm%3A9%3A0.1.2.3.4.5.6.7.8%2C16%3A10.11.12.13.14.15%7C&w=-1&h=-1&abbr=on&hdisp=S&zoom=1.3&annotate=none&r=0)

(chloro-pyrid-2-yl)-indole

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13b77a59422f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.