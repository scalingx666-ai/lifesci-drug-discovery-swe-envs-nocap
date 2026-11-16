# Issue

**Title:** Change the docs style with navigation tabs

## Description

The old docs API is too messy with too many things on the left.
![image](https://user-images.githubusercontent.com/47570400/235508462-6483b8d3-bafb-4549-8571-dfdbdd15672a.png)

Most modern libraries use tabs at the top to organize, making the API a lot easier to follow.
![image](https://user-images.githubusercontent.com/47570400/235508511-c6c8442f-57de-4098-a200-4cb99ae6e14b.png)


Checklist:

- [ ] Was this PR discussed in a issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR. 
  - No, it's a single line of code
- [ ] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
  - Not needed
- [ ] Update the API documentation is a new function is added or an existing one is deleted.
  - Not needed
- [x] Added a `news` entry.

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e07e7c83ccdb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.