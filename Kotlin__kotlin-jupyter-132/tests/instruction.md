# Issue

**Title:** Make embedKernel arguments nullable

## Description

EmptyResolutionInfoProvider is created by an [object declaration](https://kotlinlang.org/docs/object-declarations.html#object-declarations) which fails to import in pure java code. The `embedKernel` method is intended to be called inside pure Java code that simply has the compiled kotlin kernel jars available as a dependency, but the former signature after the refactor in  makes this impossible. This commit makes the `resolutionInfoProvider` nullable again, which also means that existing code using the method and passing null, still works with the the signature using `ResolutionInfoProvider`

edit 1: I can't see the build details, so I can't debug why this fails, it builds for me locally and `./gradlew check` passes

edit 2: I now know about `.INSTANCE`, so I can just use `resolutionInfoProvider.INSTANCE` instead and it works without requiring this PR. I would argue that allowing a signature that violates the typical Kotlin style in this specific case is still reasonable to make it as easy as possible for Java projects and devs to just call `embedKernel` from an existing Java application without being familiar with the nuances of embedding Kotlin code into a Java project.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea1382ae9b77`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.