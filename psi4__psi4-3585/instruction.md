# Issue

**Title:** Fix Psi4's cuEST interface clobbering the hybrid exchange fraction with non-DF SCF_TYPE

## Description

cuESTJK is built only for SCF_TYPE MEM_DF/DISK_DF (jk.cc:141).  With any other SCF_TYPE, USE_CUEST still routes the XC quadrature to the GPU but J and K come from an ordinary CPU JK.  RHF::form_G/compute_E and the UHF twins nonetheless forced alpha and beta to 1.0 whenever the USE_CUEST *option* was set:

    if (options_.get_bool("USE_CUEST")) { alpha = 1.0; beta = 1.0; }

The premise holds for cuESTJK -- it passes exchange_fraction and lrc_exchange_fraction to cuEST with the DF integral plan, so its K already carries both coefficients and the long-range term.  It is false for every other JK, which returns a bare exchange matrix.  Keying on the option rather than on the JK object therefore replaced B3LYP's alpha = 0.20 with 1.00: the SCF converged cleanly against a Fock matrix carrying 100% exact exchange on top of the full B3LYP XC functional.

    water/cc-pVDZ b3lyp, scf_type direct, use_cuest true  -76.420390 ->
                                                          -83.780347

Reproducible to 14 digits, so it looked like a converged answer.

Blast radius, measured before/after on an H200: every hybrid and every range-separated functional, at every non-DF SCF_TYPE, RHF and UHF alike. direct/pk/out_of_core agree to 1e-13 (the GPU was contributing nothing to J/K); cd differs at the Cholesky tolerance.  Plain HF escapes because its alpha is already 1.0, pure GGAs because the K branch is never taken.  For range-separated functionals the same sniff drove the is_x_lrc conditionals, so wK was dropped from the Fock build entirely.  Gradients were wrong by the same mechanism, via the converged density; scf_grad.cc:253 is not affected, having had the SCF_TYPE guard all along.

Fix: a predicate on the JK base class that defaults to the safe answer,

    // jk.h
    virtual bool exchange_is_prescaled() const { return false; }
    // cuESTJK.h
    bool exchange_is_prescaled() const override { return true; }

with all eight sites (rhf.cc and uhf.cc x form_G, compute_E, twoel_Hx_full, openorbital_scf) asking the JK object instead of the option.  This states the requirement rather than the implementation, keeps cuEST headers out of libscf_solver, and makes the safe answer the default for any future JK.  The #ifdef USING_cuEST guards at those sites drop out: in a build without cuEST the base-class false is byte-identical to the old #else branch.

Also, separately, a reporting defect visible in the same runs.  A cuEST MolecularGrid is GPU-resident, so npoints_/blocks_/max_points_ are all legitimately 0 and must stay 0 -- npoints_ is what every host consumer loops over.  But MolecularGrid::print() printed those zeros unconditionally, so every cuEST run looked like it had no quadrature grid, and the XC GRID TOTAL POINTS psivar was set to 0.  Accumulate the nominal quadrature size as the per-atom grids are handed to cuEST, in a member kept strictly separate from npoints_, and report it labelled:

    Total Points           =          67950  (GPU-resident, pre-screening)
    Grid Residency         = cuEST / device

against 66188 for the equivalent host grid.  cuEST prunes on the device and psi4 prunes on the host, so the counts are not directly comparable and the label says so.

Verified against cuEST 0.2.2: the reported 3x2x2 matrix now reproduces the CPU reference at ordinary GPU XC precision (B3LYP direct closes from 7.36 Eh to 1.4e-06, matching PBE direct at 1.5e-06 and B3LYP df at 1.4e-06); gradients give max|dG| 1.1e-05 for B3LYP at both direct and df, i.e. the XC-gradient difference only.  pytest -m "cuest or pycuest" 98 passed, ctest -R dft 42/42 passed.

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Correct energies for non-DF SCF_TYPEs when USE_CUEST=true
- [x] Report grid size for cuEST. Note that this is pre-screening size whereas the CPU number is post-screening.

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] Fed it the bug report (thanks, Zackary Childs!) and let it diagnose and fix.

## Checklist
- [ ] Tests added for any new features
- [ ] Docstring or narrative docs/sphinxman/source updated if needed
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [ ] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `180415074c4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.