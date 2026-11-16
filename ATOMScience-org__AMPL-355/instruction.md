# Issue

**Title:** Add dockerfiles. Makefile + CI Build script

## Description

- Fixes 
- Relates to 

This brings over some of the work that I did while getting Precision FDA running. There are a couple main points:
1. New Dockerfiles
The major differences here are that bypassing a virtualenv (since we are using Docker), and I'm cleaning up some things after build in order to reduce image size
2. Added Makefile
This is handy when I need to perform certain commands which can be comprised of multiple steps. Some of these types of solutions already exist in other scripts, but I think this might be a good place to consolidate all your developer scripts. I created some documentation around this in `Makefile.md`
3. Action on `release` to build and upload using GithubActions
Whenever a release is created a build will run on Actions and do all the docker build steps for you. You will need to configure the `DOCKER_USERNAME` and `DOCKER_PASSWORD` 

I'm happy to walk through all of this and give a demo of the Makefile

## TODO:
- [x] Trim up dev_requirements.txt (mordred, MolVS, etc...)
- [x] Bring over `./install_dev_dependencies.sh`
- [x] Add `linux/arm64` platform to docker build
- [x] Default to OS architecture

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ad3a01d2c0d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.