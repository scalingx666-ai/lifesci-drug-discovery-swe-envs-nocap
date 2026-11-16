# Issue

**Title:** Add DFT-D3 dispersion correction via a SimpleDFTD3 extension

## Description

**AI disclaimer.** This is mostly agent-generated code, with the goal of making D3 easy to use in DFTK. It might be that this is the completely wrong approach for how this should be done in DFTK, so please review carefully. I did not carefully check all the code as some of this is beyond my expertise. 

**Summary.** This PR adds the DFT-D3 dispersion correction as a package extension using [SimpleDFTD3.jl](https://github.com/JuliaMolSim/SimpleDFTD3.jl) so that it can be used like this:
```julia
using DFTK, SimpleDFTD3
model = model_DFT(system; functionals=PBE(), pseudopotentials, extra_terms=[DFTD3()])
```
`DFTD3()` picks the D3(BJ) parameters for the model's functional. Other dampings and cutoffs can be passed, e.g. `DFTD3(RationalDamping("pbe"; atm=true))`. If the functional is modified (scaled, or with custom exact exchange), a damping has to be given explicitly.

**Design.** Core DFTK only gets an empty, documented `DFTD3` function (like `run_wannier90`), since extensions can't export new names. Everything else is in `ext/DFTKSimpleDFTD3Ext.jl`. D3 adds to energies, forces and stresses but doesn't change the SCF.

**Limitations.** Phonons, elastic constants, derivatives of the D3 forces and non-3D systems raise an error. Results computed with an explicit damping can't be reloaded with `load_scfres`, since SimpleDFTD3 dampings are handles to C memory.

**Tests and docs.** Tests compare against the Python `dftd3` package. A new docs example computes the interlayer binding of graphite. Not tested locally: MPI, and the plotting lines of the example.

**Before merging.** SimpleDFTD3 isn't registered yet (JuliaRegistries/General#173384), so the `[sources]` entries in `Project.toml` and `docs/Project.toml` are temporary, and Julia 1.10 CI fails until then. (this is why the PR is still a draft)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9fd115c7ce1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.