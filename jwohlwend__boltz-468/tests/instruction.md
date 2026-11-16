# Issue

**Title:** fix: pass full BoltzSteeringParams to affinity prediction

## Description

With the new recent updates, affinity prediction fails, when using the `force` option on pocket constraints (probably also for contact constraints and templates).

E.g.

```
File ".../lib/python3.11/site-packages/torch/nn/modules/module.py", line 1751, in _wrapped_call_impl
    return self._call_impl(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File ".../lib/python3.11/site-packages/torch/nn/modules/module.py", line 1762, in _call_impl
    return forward_call(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File ".../boltz/src/boltz/model/models/boltz2.py", line 533, in forward
    struct_out = self.structure_module.sample(
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File ".../boltz/src/boltz/model/modules/diffusionv2.py", line 306, in sample
    or steering_args["physical_guidance_update"]
       ~~~~~~~~~~~~~^^^^^^^^^^^^^^^^^^^^^^^^^^^^
KeyError: 'physical_guidance_update'
```

This PR introduces a quick fix by passing a full `BoltzSteeringParams` object (as dict) while keeping the previous default settings.

Should fix #469

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6fa9f4c19084`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.