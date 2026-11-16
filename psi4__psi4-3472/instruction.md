# Issue

**Title:** Support for Dimension range-based for loop

## Description

## Description

Allows the following syntax:
```c++
for (auto& h : nmopi_) { h *= 2; }
```
Or for einsums-type quantities
```c++
std::vector<size_t> dim(nirreps_);
for (auto&& [h, d] : std::views::zip(nsopi_, dim)) {
    d = static_cast<size_t>(2*h);
}
ComplexMatrix D_{"Density", dim, dim};
```
This showed up in my ComplexWavefunction work a bit and I think it makes things a bit easier.

## User API & Changelog headlines

- [x] Added `Dimension::begin()` and `::end()`. Forwards to internal `blocks_.begin()` and `end()`. Allows for range-based for loops over Dimension objects.

## AI
None

## Checklist
- [x] Tests added for any new features

## Status
- [x] Ready for review

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a264c0517ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.