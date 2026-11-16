# Issue

**Title:** Torchani lazy model loading

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Only load/instantiate TorchANI models when one is actually used. Currently, all models get instantiated, even though only one ultimately gets used (and cached) in a `compute` call.

Besides the performance hit, the current implementation also appears to cause frequent issues on networked filesystems due to the many individual file reads required to instantiate the models. For :

```
count : 578

geomeTRIC run_json error:
Traceback (most recent call last):
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/geometric/run_json.py", line 225, in geometric_run_json
geometric.optimize.Optimize(coords, M, IC, engine, None, params)
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/geometric/optimize.py", line 1331, in Optimize
return optimizer.optimizeGeometry()
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/geometric/optimize.py", line 1293, in optimizeGeometry
self.calcEnergyForce()
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/geometric/optimize.py", line 1002, in calcEnergyForce
spcalc = self.engine.calc(self.X, self.dirname)
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/geometric/engine.py", line 873, in calc
return self.calc_new(coords, dirname)
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/geometric/engine.py", line 865, in calc_new
raise QCEngineAPIEngineError("QCEngineAPI computation did not execute correctly. Message: " + ret["error"]["error_message"])
geometric.errors.QCEngineAPIEngineError: QCEngineAPI computation did not execute correctly. Message: QCEngine Execution Error:
Traceback (most recent call last):
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/qcengine/util.py", line 115, in compute_wrapper
yield metadata
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/qcengine/compute.py", line 91, in compute
output_data = executor.compute(input_data, config)
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/qcengine/programs/torchani.py", line 110, in compute
model = self.get_model(method)
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/qcengine/programs/torchani.py", line 76, in get_model
"ani1ccx": torchani.models.ANI1ccx(),
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/torchani/models.py", line 312, in ANI1ccx
return BuiltinEnsemble._from_neurochem_resources(info_file, periodic_table_index)
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/torchani/models.py", line 238, in _from_neurochem_resources
ensemble_prefix, ensemble_size)
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/torchani/neurochem/__init__.py", line 271, in load_model_ensemble
models.append(load_model(species, network_dir))
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/torchani/neurochem/__init__.py", line 253, in load_model
models[i] = load_atomic_network(filename)
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/torchani/neurochem/__init__.py", line 232, in load_atomic_network
load_param_file(layer, in_size, out_size, wfn, bfn)
File "/data/homezvol0/tgokey/.local/miniconda3/envs/qcf/lib/python3.7/site-packages/torchani/neurochem/__init__.py", line 203, in load_param_file
w = struct.unpack('{}f'.format(wsize), fw.read())
struct.error: unpack requires a buffer of 81920 bytes
```

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
`TorchANIHarness` now lazily loads models as requested for compute.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66f10d2f0cdd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.