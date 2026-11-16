# Issue

**Title:** PMI component bugfix: properly catch invalid mols

## Description

PMI component was giving me this error:

Traceback (most recent call last):
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/bin/reinvent", line 8, in <module>
    sys.exit(main())
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/lib/python3.10/site-packages/reinvent/Reinvent.py", line 334, in main
    runner(
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/lib/python3.10/site-packages/reinvent/runmodes/RL/run_staged_learning.py", line 367, in run_staged_learning
    terminate = optimize(package.terminator)
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/lib/python3.10/site-packages/reinvent/runmodes/RL/learning.py", line 118, in optimize
    results = self.score()
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/lib/python3.10/site-packages/reinvent/runmodes/RL/learning.py", line 192, in score
    results = self.scoring_function(
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/lib/python3.10/site-packages/reinvent/scoring/scorer.py", line 138, in compute_results
    transform_result = compute_transform(
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/lib/python3.10/site-packages/reinvent/scoring/compute_scores.py", line 101, in compute_transform
    component_results = compute_component_scores(
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/lib/python3.10/site-packages/reinvent/scoring/compute_scores.py", line 62, in compute_component_scores
    component_results = scoring_function(smilies_non_cached)
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/lib/python3.10/site-packages/reinvent_plugins/mol_cache.py", line 35, in wrapper
    return func(self, mols)
  File "/ceph/hpc/home/deklevad/miniforge3/envs/reinvent4/lib/python3.10/site-packages/reinvent_plugins/components/RDKit/comp_pmi.py", line 45, in __call__
    npr1 = Chem.CalcNPR1(mol3d)
RuntimeError: Pre-condition Violation
	molecule has no conformers
	Violation occurred on line 112 in file Code/GraphMol/Descriptors/PMI.cpp
	Failed Expression: mol.getNumConformers() >= 1
	RDKIT: 2023.09.5
	BOOST: 1_78

I noticed it wasn't properly catching invalid molecules that can't be embedded. I added a condition that if the embedding process returns -1 (which means it failed - according to rdkit docs), it raises ValueError and proceeds gracefully.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a1a50e88b93`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.