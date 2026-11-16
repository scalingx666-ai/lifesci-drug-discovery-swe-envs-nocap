# Issue

**Title:** k-point sampling for exact exchange

## Description

A first version of exact exchange for k-meshes beyond $\mathbf \Gamma$-only sampling.

Exchange couples k to k' via the momentum transfer q = k - k'.
Here, we add a q-point logic.

- build_qpoints (PlaneWaveBasis.jl) returns the unique q = k - k' plus a table kprime_mapping[ik, iq] giving the index of k' = k - q. 
- TermExactExchange stores one kernel per q. Energy and operator loop over q.
- Coulomb kernels take a q-point and are evaluated (e.g. $4\pi/(G+q)^2$) on the full FFT grid instead of the smaller spherical grid, since overlap densities require large G. This changed references values in the tests slightly (updated). 
- Coulomb kernels adapted: for instance, spherical cutoff uses the supercell volume for default radius, Wigner-Seitz truncates at the supercell WS cell, voxel averaging takes its mesh from the q-grid. 
- shifted_cholesky for the ACE compression (not sure if there are better solutions to avoid tiny negative eigenvalues...)
- new tests: kernels and energies of a k-grid vs. the equivalent supercell, collinear spin with k-points, AFM chain vs. supercell, explicit/shifted grids.
- 

Missing: 
* MPI parallelization over k-points
* GPU optimization (not tested at all)
* does not exploit any symmetry of BZ (currently requires symmetries=false)

Small example (finishes in about a minute):
```julia
using DFTK                                                                              
using AtomsBuilder                                                                      
using PseudoPotentialData                                                               
                                                                                        
pseudopotentials = PseudoFamily("dojo.nc.sr.pbe.v0_5.stringent.upf")                    
system = bulk(:Si)                                                                      
Ecut   = 15                                                                             
kgrid  = [2, 2, 2]                                                                      
                                                                                        
model_pbe  = model_DFT(system; pseudopotentials, functionals=PBE(), symmetries=false)   
basis_pbe  = PlaneWaveBasis(model_pbe; Ecut, kgrid)                                     
scfres_pbe = self_consistent_field(basis_pbe; tol=1e-6)                                 
                                                                                        
model  = model_HF(system; pseudopotentials, exx_kernel=WignerSeitzTruncatedCoulomb())   
basis  = PlaneWaveBasis(model; Ecut, kgrid)                                             
scfres = self_consistent_field(basis; scfres_pbe.ρ, scfres_pbe.ψ,                       
                               scfres_pbe.eigenvalues, scfres_pbe.occupation,           
                               is_converged=ScfConvergenceEnergy(1e-8),                 
                               exxalg=AceExx(), damping=0.4,                            
                               solver=DFTK.scf_damping_solver())                        
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12a100c96a3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.