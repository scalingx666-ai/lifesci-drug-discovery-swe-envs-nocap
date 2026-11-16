# Issue

**Title:** Addresses #119 and prints quasiparticle weight

## Description

## Description
This PR addresses bug #119 related to the return value corresponding to the eigenvectors in the Davidson code. I have also added printing of the quasiparticle weight for the IP and EA as some sort of demonstration of the physicality of the returned eigenvectors.

## What are your new additions? Please provide a brief list.
* **New Features**
  - [x] Prints quasiparticle weight for IP and EA-ADC(2)

* **Changes**
  - [x] Fixes returned eigenvector space in `adc_helper.davidson`

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `304b16784463`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.