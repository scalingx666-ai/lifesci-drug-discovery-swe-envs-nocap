# Issue

**Title:** Dimension deprecation: use new `dpd_init` in `libtrans`

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->

> [!IMPORTANT]
> Essentially identical fixes that were done in #3358. I just missed some cases.

It appears that I missed a few cases that should have went in that PR. I think many of these misses were caused by the deprecation warnings just not being emitted by the compiler.

In this case, I strongly suspect it might be due to the use of `extern` linkage. It makes me wonder, perhaps we need a different way of deprecating functions. If the purpose of deprecation is to let plugin developers have time to adjust their code before breaking changes, they might never know. For example, `std::make_shared<Matrix>(deprecated, constructor, params)` does *not* show up as a deprecation warning for GCC (though does for clang). Maybe we could have
1. Some idempotent outfile/stdout print statement in the function body, perhaps cached until the end of the calculation so that it's the last thing printed. For example, `"Your code called the deprecated <function> at <file>:<lineno>. Bug a developer until they fix it!"`
2. `pragma message`, supported by all compilers
3. combination of the above

Something foolproof that actually applies to the people using the deprecated code, not just compiling it.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
*None*

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
*None*

## Checklist
- [x] Tests added for any new features
- [x] Docstring or narrative docs/sphinxman/source updated if needed
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a264c0517ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.