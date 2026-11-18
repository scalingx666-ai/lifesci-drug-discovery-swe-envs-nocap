# Issue

**Title:** Pin jinja2 to fix failing docs

## Description

## Description
Pin jinja2 to fix failing docs:
https://github.com/volkamerlab/teachopencadd/runs/5686402020?check_suite_focus=true#step:8:42

## Todos
- [x] Pin jinja2
- [x] Use mamba as resolver in docs CI
- [x] Do not convert warnings into errors (remove -W from SPHINXOPTS, see ): https://www.sphinx-doc.org/en/master/man/sphinx-build.html#cmdoption-sphinx-build-W
- [x] README links broken - Binder instances: Add `<!-- markdown-link-check-disable-next-line -->` as described here: https://github.com/gaurav-nelson/github-action-markdown-link-check#disable-check-for-some-links

## Status
Note: In this PR, only the docs CI needs to pass.
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81c6562d944e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.