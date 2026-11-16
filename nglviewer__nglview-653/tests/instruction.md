# Issue

**Title:** Docker container for nglview with jupyterlab

## Description

How to run?

```bash
docker pull hainm/nglview:1.0.a0 # only do once
docker run -it --rm -p 8888:8888 hainm/nglview:1.0.a0
```

You will see something similar below (in very end):
```bash
$ docker run -it --rm -p 8888:8888 hainm/nglview:1.0.a0
...
    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8888/?token=8561123c64045c134ef3aae8e1f54a7d500e5a547aa9e6f7
```

Just follow that. 

<img width="1278" alt="screen shot 2017-07-23 at 2 00 45 am" src="https://user-images.githubusercontent.com/4451957/28497062-ccf8dd1e-6f4a-11e7-9277-80c8cc5426c5.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a28c3b774f62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.