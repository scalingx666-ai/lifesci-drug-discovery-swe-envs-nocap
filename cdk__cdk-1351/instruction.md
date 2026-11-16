# Issue

**Title:** Bundle: merge META-INF/services so protein descriptors are registered

## Description

## Problem

`DescriptorEngine` discovers descriptors with `ServiceLoader`, i.e. from `META-INF/services/org.openscience.cdk.qsar.IMolecularDescriptor`. That file is provided by two modules:

- `descriptor/qsarmolecular` (the molecular descriptors)
- `descriptor/qsarprotein` (`protein.TaeAminoAcidDescriptor`, `molecular.AminoAcidCountDescriptor`)

The `bundle` module builds `cdk-<version>.jar` with `maven-shade-plugin` but without a `ServicesResourceTransformer`. For duplicate resource paths shade keeps only the first copy, so the `qsarprotein` entries are silently dropped. The classes are in the jar, but they are not registered.

## Observed with the 2.13 release jar

Compared with the 2.9 per-module jars, the merged `IMolecularDescriptor` service file in `cdk-2.13.jar` is missing exactly:

- `org.openscience.cdk.qsar.descriptors.protein.TaeAminoAcidDescriptor`
- `org.openscience.cdk.qsar.descriptors.molecular.AminoAcidCountDescriptor`

Consequences for consumers of the bundle jar:

- `DescriptorEngine` no longer finds these two descriptors.
- The `protein` dictionary class disappears, since `TaeAminoAcidDescriptor` is its only member. This was noticed in rcdk, where the descriptor categories dropped from 6 to 5.

I scanned every `META-INF/services/*` file in the 2.13 sources. `IMolecularDescriptor` is the only service file shipped by more than one module, so this is the only affected registration.

## Fix

Add `ServicesResourceTransformer` to the shade configuration in `bundle/pom.xml` so duplicate service files are concatenated.

## Verification

Built `mvn -pl bundle -am package -DskipTests` on current `main`. The resulting `cdk-2.14-SNAPSHOT.jar` has 53 entries in `META-INF/services/org.openscience.cdk.qsar.IMolecularDescriptor`, including both `TaeAminoAcidDescriptor` and `AminoAcidCountDescriptor`.

I have not run the full test suite. A regression test asserting that the bundle's service file lists these descriptors could be added if wanted.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bc74a728a47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.