# Issue

**Title:** Psi4NumPy contributor guidelines & license update

## Description

This PR accomplishes:
- [x] adds issue/PR templates, 
- [x] updates the repo license file from GPL 3.0 to BSD-3C, 
- [x] adds installation instructions & repo organization info to main README, and
- [x] adds contributor guidelines discussing GH workflow, requirements for new ref implementations & tutorials, and styleguides for commit messages, headers, citations, Python, and docs.

Hoping to get the ball rolling on some discussion of the proposed guidelines.  I thought I would write a more thorough contribution doc at first, we can always pare it down later.

Questions:
- [ ] Should we add a code of conduct? I don't think there are any current issues, but it seems like several open-source packages I looked at have adopted the [Contributor Covenant](http://contributor-covenant.org/)

Issues:
- [ ] A large portion of the current repo violates the proposed guidelines in some form or another.  If accepted, I'll go through and create organized issues so that I can convert the repo w/o missing anything

Status:
- [x] Complete contributing document, addresses all relevant facets of devel cycle
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4795df448d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.