# Issue

**Title:** update maven-compiler-plugin configuration to use <release> instead of <source> and <target>

## Description

I noticed a bootstrap warning when compiling cdk-base;
`bootstrap class path not set in conjunction with -source 8`

ttbomk using `release` instead of `source `/ `target `is best practice.

Setting `<release>8</release>` is essentially equivalent to:
1. Setting `<source>1.8</source>`.
2. Setting `<target>1.8</target>`.
3. Additionally, it also configures the compiler to use the platform APIs of the specified Java version (Java 8 in this case), preventing accidental use of APIs from a newer JDK. This is accomplished by setting the `--release` flag of the compiler, which correctly configures the bootstrap classpath. `javac`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe44b813cfd7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.