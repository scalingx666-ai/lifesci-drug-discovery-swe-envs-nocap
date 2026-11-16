# Issue

**Title:** Docker prep

## Description

- Updated the docker files and makefile after tests.
- CPU has been tested and pushed to docker hub. The other platforms have not been tested <cuda|rocm|mchip>.
- Updated some documents wrt the updates.

Example:

To build:

```
make build-docker PLATFORM=cpu ENV=prod
```

To start a docker container:

```
docker run -it -p 8888:8888 -v ${PWD}:/home atomsci/atomsci-ampl:v1.8.0-cpu bas
```

Once the container is tested,

To push:

```
make push-docker PLATFORM=cpu ENV=prod
```

To verify:

Go to [https://hub.docker.com/r/atomsci/atomsci-ampl](https://hub.docker.com/r/atomsci/atomsci-ampl) and check if the versions/tags exist on docker hub.

To pull:

```
docker pull atomsci/atomsci-ampl:latest
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e77c69642dc3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.