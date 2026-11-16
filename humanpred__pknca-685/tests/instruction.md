# Issue

**Title:** Let a secondary parameter's reference differ in named group columns (ref_vary)

## Description

## Summary

A secondary parameter's reference group was the requesting instance's own group with only the reference interval's columns swapped in. In an IV/oral crossover grouped by treatment, period and subject, the IV reference of an oral profile in period 2 was looked up in period 2, where that subject had no IV profile, and every bioavailability link stopped with "the value 'totdose' from the reference interval is not available".

- `interval_add_secondary(ref_vary = "period")` declares the group columns in which a link's reference may differ. The reference is matched on every other group column and on the reference interval's times, and takes whichever value of the varying columns has the source parameters' results. One candidate is used; more than one is `pknca_error_secondary_ref_vary_ambiguous` (or NA with the reason for an automatic link); none keeps the not-available error. A reference whose result is NA still counts as a candidate, so a replicate design with one unfitted administration stays ambiguous.
- A varying column the intervals carry is pinned by the reference interval, so naming the occasion in `reference` resolves a replicate design. The subject column may not vary.
- The declaration is stored per link in a `<param>_ref_vary` intervals column (names separated by commas or spaces; "" declares that nothing varies). `PKNCAdata(ref_vary = )` is the default for every link whose column is NA, including the links `pk.nca()` derives; `character(0)` is stored as NULL, and `print()` shows the line only when columns are named. The per-link form rejects a name containing a space or comma, with the reason and a pointer at the data-level form, which accepts such names.
- The automatic finder ignores varying columns when measuring distance, so a crossover steered by `group_ref` no longer ties. Nothing varies by default, so existing analyses are unchanged.
- `clear_orphan_ref_pointers()` now clears with a plain NA.
- Docs: the secondary-parameters vignette gains a crossover-by-period example; the design document records the rule as decision 11 and section 6.5, pointed to from the as-built section 3.16; NEWS describes the argument.
- Tests: an end-to-end `pk.nca()` run with a period column in the intervals pinning the reference, a per-link declaration overriding a different data-level default, an empty data-level value, the ambiguity and not-available errors, and the finder fixture at the top level of the test file.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bdde0560b03a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.