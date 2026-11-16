# Issue

**Title:** Only add gpus if platform is set

## Description

I was encountering the following error when running on a machine without a GPU:

```
docker run -p 8080:8080 \
  --gpus all \
        --hostname job-Gq8JzK80Zv77jJQFFzPBvY6Q.dnanexus.cloud \
        --privileged \
        -v /home/dnanexus/AMPL/../work/:/work/ kartstig/ampl:cpu-pfda \
        /bin/bash -l -c "jupyter-notebook --ip=0.0.0.0 --no-browser --allow-root --port=8080"
docker: Error response from daemon: failed to create shim task: OCI runtime create failed: runc create failed: unable to start container process: error during container init: error running hook #0: error running hook: exit status 1, stdout: , stderr: nvidia-container-cli: initialization error: driver error: failed to process request: unknown.
ERRO[0001] error waiting for container:                 
make: *** [Makefile:73: jupyter-notebook] Error 125
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67b0e88aa95a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.