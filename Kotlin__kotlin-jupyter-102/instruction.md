# Issue

**Title:** Allow REPL/Kernel to be embedded and share classes/variables with its caller

## Description

Currently the Kotlin kernel supports something similar to [IPython.start_kernel](https://ipython.readthedocs.io/en/stable/api/generated/IPython.html#IPython.start_kernel). This PR aims to support something that covers the use cases of [IPython.embed_kernel](https://ipython.readthedocs.io/en/stable/api/generated/IPython.html#IPython.embed_kernel).



#### What this PR provides

An application can now call `org.jetbrains.kotlin.jupyter.iKotlin.kernelServer` directly and pass a desired `KernelConfig` and the runtime properties where the `embedded` property is set to `true` and return the `KernelConfig` as a standard JSON to user in an application specific way.
The user can then run `jupyter console --existing=path/to/kernelconfig.json` to attach a Kotlin REPL to the kernel and run arbitrary Kotlin code inside the application context with the same state as the the application. 


#### What this PR does not allow

This does not allow attaching a Jupyter Notebook to the Kernel. This is a [limitation of Jupyter Notebooks](https://stackoverflow.com/questions/31382405/ipython-notebook-how-to-connect-to-existing-kernel/31385337#31385337) and not the Kotlin kernel.


### Status

This should work already, but I'm currently still writing the actual embedding code for the application I want to use it in, so until then I still consider this PR a draft, but appreciate an feedback on the general idea and current implementation.

EDIT:
The first proof of concept for this already works and I think anything else I wanted to achieve is an issue with the application embedding the kernel. This embedding could be simplified by allowing the embedding Java Application to acess `defaultRuntimeProperties`. I am also feeling unsure if the runtimeproperties is really the right place for the embedding option, and if `KernelArgs`/`KernelConfig` wouldn't be a better place.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9945222ac5cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.