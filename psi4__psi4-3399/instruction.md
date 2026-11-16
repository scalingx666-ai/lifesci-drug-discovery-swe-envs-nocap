# Issue

**Title:** Add mbis charges for atomic number > 37

## Description

# Extend MBIS to All Elements (Z=1–118)

Close #2728
Close #3135

## Description

*code and PR description written by Claude Sonnet 4.6 - High, proof read and validated by me*

Extends MBIS charge partitioning support from Z=1–36 (H–Kr) to Z=1–118 (H–Og) by adding initial [proatom](https://doi.org/10.1021/acs.jctc.6b00456) shell parameters for all elements through oganesson.

Previously, attempting MBIS on any molecule containing an element heavier than krypton raised a `PsiException`. After this change all 118 elements are supported with no API changes.

MBIS (Minimal Basis Iterative Stockholder, [doi:10.1021/acs.jctc.6b00456](https://doi.org/10.1021/acs.jctc.6b00456)) partitions the molecular electron density into atom-in-molecule contributions using an iterative Stockholder scheme. Each free atom is represented by a sum of exponential [proatom densities](https://doi.org/10.1021/acs.jctc.6b00456):

$$\rho_a^0(\mathbf{r}) = \sum_i \frac{N_{ai}\, \sigma_{ai}^{-3}}{8\pi} e^{-|\mathbf{r} - \mathbf{R}_a| / \sigma_{ai}}$$

The algorithm needs only the initial guesses for the per-shell populations $N_{ai}$ and inverse widths $1/\sigma_{ai}$; the converged values are determined self-consistently regardless of starting point.

Parameters for all Z=1–118 are taken verbatim from [denspart](https://github.com/theochem/denspart) (GPL-3.0):

> T. Verstraelen et al., `denspart/mbis.py`  
> <https://github.com/theochem/denspart/blob/main/src/denspart/mbis.py>  
> `INITIAL_MBIS_PARAMETERS` dict

## User API & Changelog headlines

- [ ] MBIS charges/multipoles now supported for all elements Z=1–118 (previously Z=1–36 only); no API changes

## Dev notes & details

- [ ] `get_mbis_params` refactored from per-shell lookup `(atomic_num, shell_num) → tuple` to whole-atom lookup `(atomic_num) → vector<tuple>`; parameter table is now a `static const` map (constructed once) covering all 118 elements
- [ ] `mA` derivation replaces hardcoded `if/else` range checks with `get_mbis_params(Z).size()`; parameter table is single source of truth for shell counts
- [ ] `Nai`/`Sai` inner vector size changed from literal `4` to `constexpr int max_shells = 7`; pattern unchanged from existing code (unused zero-initialized slots never read)
- [ ] Shell counts by period: Z=1–2: 1, Z=3–10: 2, Z=11–18: 3, Z=19–36: 4, Z=37–54: 5, Z=55–86: 5–6, Z=87–118: 6–7 (shell merging in upstream denspart optimization)
- [ ] Parameters for Z=1–36 are byte-identical to previous implementation; all 6 existing MBIS tests (mbis-1–6, covering H/O/Na/Cl/Zn) are unaffected
- [ ] Verified: script comparing all 589 shell parameters against denspart source reports no mismatches

  <details><summary>Verification script</summary>

  ```python
  #!/usr/bin/env python3
  """Verify oeprop.cc MBIS params match denspart's INITIAL_MBIS_PARAMETERS."""
  import ast, re, urllib.request

  src = urllib.request.urlopen(
      "https://raw.githubusercontent.com/theochem/denspart/main/src/denspart/mbis.py"
  ).read().decode()
  i = src.index("INITIAL_MBIS_PARAMETERS = {") + len("INITIAL_MBIS_PARAMETERS = ")
  chunk, depth, end = src[i:], 0, 0
  for j, c in enumerate(chunk):
      depth += (c == "{") - (c == "}")
      if depth == 0:
          end = j + 1
          break
  ref = {z: [(float(n), float(s)) for n, s in v]
         for z, v in ast.literal_eval(chunk[:end]).items()}

  with open("psi4/src/psi4/libmints/oeprop.cc") as f:
      cc = f.read()
  start = cc.index("static const std::map")
  psi4 = {}
  for line in cc[start : start + 60000].splitlines():
      m = re.match(r"\s*\{(\d+),", line)
      if m and 1 <= (z := int(m.group(1))) <= 118:
          psi4[z] = [(float(a), float(b))
                     for a, b in re.findall(r"\{([\d.]+),\s*([\d.]+)\}", line)]

  mismatches = []
  for z in range(1, 119):
      r, p = ref[z], psi4.get(z, [])
      if len(r) != len(p):
          mismatches.append(f"Z={z}: {len(p)} shells (expected {len(r)})")
          continue
      for i, ((rn, rs), (pn, ps)) in enumerate(zip(r, p)):
          if abs(rn - pn) > 1e-4 or abs(rs - ps) > 1e-4:
              mismatches.append(f"Z={z} shell {i+1}: ({pn},{ps}) != ({rn},{rs})")

  print("\n".join(mismatches) or
        f"OK — all {sum(len(v) for v in psi4.values())} shell parameters match.")
  ```

  </details>

## Questions

## Checklist

- [ ] Tests added for any new features
- [ ] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status

- [ ] Ready for review
- [ ] Ready for merge

## Related

- denspart: <https://github.com/theochem/denspart>
- theochem/AtomDB (free-atom density database used to derive parameters): <https://github.com/theochem/AtomDB>
- MBIS paper: Verstraelen et al., *J. Chem. Theory Comput.* **2016**, 12, 3894–3912. <https://doi.org/10.1021/acs.jctc.6b00456>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d9c3d8349b9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.