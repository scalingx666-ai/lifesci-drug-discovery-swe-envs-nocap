# Issue

**Title:** Depict background

## Description

A small fix but some users complained that in CDK it would give strange colours in InkScape when using a transparent background. The ``rgba`` I think is only correct in web SVG and we should use the ``opacity=`` attribute.

I also added a null check to the Rectangle generation to allow setting of "no" background.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3c100920361`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.