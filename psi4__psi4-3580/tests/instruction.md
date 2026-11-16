# Issue

**Title:** Reuse parsed basis entries within one BasisSet.construct call

## Description

## Description

`BasisSet.construct` called `Gaussian94BasisSetParser.parse` once **per atom**. That rescans the whole `.gbs` text even when every carbon wants the same `C` entry from the same file. This PR caches parser results by `(source, entry)` for the lifetime of **one** `construct` call and deep-copies each hit, so every atom still gets its own shell objects.

```diff
 for at in atoms:
   for bas in seek['basis']:          # source priority unchanged
     lines = names[index]             # text already cached per source (existing)
     for entry in seek['entry']:      # label before symbol, unchanged
-      result = parser.parse(entry, lines)
+      if (index, entry) not in parsed_entries:
+        parsed_entries[(index, entry)] = parser.parse(entry, lines)
+      result = copy.deepcopy(parsed_entries[(index, entry)])
       if shells is None: continue    # misses are cached too
       postfunc(shells)               # e.g. decontract, on the private copy
```

**Why it adds up.** `parse` always scans to the end of the file, so it can pick up an ECP block. One call therefore costs ~1.3 µs per line of the source, for a hit or a miss and for any element. Small orbital files are cheap, but `def2-universal-jkfit` is 9,330 lines, ~12 ms per call versus <1 ms for `6-31+G**`. It is the universal fallback fitting basis (Pople orbital bases, SAD), and workflows with many SCF solves rebuild it every solve. Ghosted monomers pay for every atom.

Ethylene–carbon-nanotube dimer (42 atoms), `6-31+G**`, `DF_BASIS_SCF def2-universal-jkfit`, `DF_BASIS_MP2 aug-cc-pvdz-ri`, `PUREAM true`. Basis construction was timed by wrapping `qcdb.BasisSet.construct`:

| workflow | SCF solves / basis builds | parse calls (master → PR) | basis construction (master → PR) |
|---|---|---|---|
| HF on dimer + both ghosted monomers | 3 / 12 | 504 → 24 | 2.85 s → 0.79 s |
| `energy("sapt(dft)")`, `SAPT_DFT_GRAC_COMPUTE iterative` | 17 / 69 | 1,890 → 138 | 11.5 s → 3.0 s |

`BasisSet.build` alone on a 96-atom (H2O)32 cluster: aug-cc-pVTZ 0.632 → 0.151 s, aug-cc-pVTZ-JKFIT 0.371 → 0.183 s, 6-31+G** `return_atomlist` 0.250 → 0.199 s.

For scale: this is a setup-cost fix, not an SCF speedup. Basis construction is 3.6–3.9x faster, but that is ~0.4% of the 36-minute SAPT(DFT) run above.

## User API & Changelog headlines
- [x] Faster basis-set construction for molecules with many atoms of the same element, most visible with large fitting-basis files such as `def2-universal-jkfit`. No change in results or input.

## Dev notes & details
- [x] `qcdb.BasisSet.construct` memoizes `parser.parse(entry, lines)` in a local dict keyed by `(index, entry)`. `index` is the existing per-construct key for the text source (`file <abspath>` / `inputblock <name>` / `bse <name>`). That text is fixed within one call, and the parser's only state (`forced_puream`) is fixed for the parser object, so `parse` is a pure function of the key.
- [x] The cache is a local variable, so it lives for one `construct` call only. A custom basis block, `PSIPATH`, or `puream` that changes between builds is honored on the next call.
- [x] Source priority, label-before-symbol lookup, fallback/default fitting search and misses are unchanged. Only the call is memoized.
- [x] Each hit is `copy.deepcopy`'d before postprocessing (`-decon`) and attachment. `cc-pvdz` and `cc-pvdz-decon` share one file and one cache key without seeing each other's results. Each label keeps independent `ShellInfo` objects in `BasisSet.atom_basis_shell`, as before.
- [x] Every basis set built by the nanotube workflow above (orbital, JKFIT, RIFIT, SAD orbital and SAD fit; each for the dimer, both ghosted monomers and both bare monomers; with and without `puream`) is bit-identical on master and this branch. The HF energies agree to 1e-10 Eh.
- [x] New `tests/pytests/test_basis_parse_reuse.py` (`psi api quick`, 11 tests): whole and atom-list bases; labels, ghosts and a redefined custom source; puream; two sources for one element; forced-puream parser; contracted and `-decon` variants sharing a file; six carbons on four library bases each matching a standalone build; repeated ECP atoms (`ncore`, exponents, coefficients, r-powers); per-label shell independence. Five of these fail on master (they assert parse counts), and the independence test fails if the `deepcopy` is removed.

## Questions
- [ ] None.

## AI
- [x] Claude Code (Anthropic) wrote the patch and tests, ran local validation, profiled the parse cost and drafted this description. I reviewed the change and the measurements and can answer questions about them.

## Checklist
- [x] Tests added for any new features
- [x] Docstring or narrative docs/sphinxman/source updated if needed (none needed; internal change)
- Local (Linux, Release, conda): `pytest -m quick` has the same failure set as master apart from the new parse-count tests, and those failures are environment-only (old `qcmanybody`). Basis/mints/decontract/SAD/guess/ghost/puream ctests pass, as do ECP ctests with `ENABLE_ecpint=ON` (`basis-ecp sapt-ecp scf-ecp scf-ecp2 scf-ecp3 mbis-ecp`).
- On my fork, Eco passes on all 5 platforms. A Linux job running the new tests, `pytest -m "quick and not addon"` (2132 passed) and 51 basis/ECP ctests also passes.

## Status
- [x] Ready for review

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66507f43f5c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.