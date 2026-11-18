# Issue

**Title:** [DL Edition] Add thumbnails

## Description

## Description
Added thumbnails for all DL talktorials and T011. 
For new thumbnails: add .png file to docs/_static/images/thumbnails/ and add path in docs/conf.py (nbsphinx_thumbnails), see: https://nbsphinx.readthedocs.io/en/0.8.8/gallery/thumbnail-from-conf-py.html
Solves #391 and #381 

## Todos
- [x] Added missing thumbnails for T038, T011
- [x] Changed thumbnails for T033-T037
- [x] Updated papers on talktorial collection page  
- [x] Added instructions in #185  


## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9bdffcfc2915`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.