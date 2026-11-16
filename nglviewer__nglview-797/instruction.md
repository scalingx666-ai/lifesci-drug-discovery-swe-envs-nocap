# Issue

**Title:** show_iodata, show_qcelemental, show_openbabel, show_psi4

## Description

add show_iodata
    add show_qcelemental
    add show_openbabel
    add show_psi4
    respect kwargs for show_[...]

![iodata](https://user-images.githubusercontent.com/4451957/57161877-a6207380-6dba-11e9-8a54-7c2a3b9f82d6.png)

![openbabel](https://user-images.githubusercontent.com/4451957/57161880-a882cd80-6dba-11e9-8704-33de340c72ca.png)

![psi4](https://user-images.githubusercontent.com/4451957/57161884-ab7dbe00-6dba-11e9-9d10-76cfb36d6724.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49ffb66a0026`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.