# Issue

**Title:** fix issue with empty annotation in depiction

## Description

Without any code changes in the non-test space of the code `DepictionTest::testAtomPropertyEmptyStringAnnotationLabel` fails:

```
java.lang.ArrayIndexOutOfBoundsException: Index -2 out of bounds for length 2

	at java.desktop/sun.font.StandardGlyphVector.getGlyphsOutline(StandardGlyphVector.java:1173)
	at java.desktop/sun.font.StandardGlyphVector.getGlyphOutline(StandardGlyphVector.java:433)
	at org.openscience.cdk.renderer.generators.standard.TextOutline.getGlyphCenter(TextOutline.java:196)
	at org.openscience.cdk.renderer.generators.standard.TextOutline.getLastGlyphCenter(TextOutline.java:183)
	at org.openscience.cdk.renderer.generators.standard.StandardGenerator.generateAnnotation(StandardGenerator.java:824)
	at org.openscience.cdk.renderer.generators.standard.StandardGenerator.generateAtomSymbols(StandardGenerator.java:684)
	at org.openscience.cdk.renderer.generators.standard.StandardGenerator.generate(StandardGenerator.java:272)
	at org.openscience.cdk.renderer.generators.standard.StandardGenerator.generate(StandardGenerator.java:103)
	at org.openscience.cdk.depict.DepictionGenerator.generate(DepictionGenerator.java:771)
	at org.openscience.cdk.depict.DepictionGenerator.generate(DepictionGenerator.java:787)
	at org.openscience.cdk.depict.DepictionGenerator.depict(DepictionGenerator.java:384)
	at org.openscience.cdk.depict.DepictionGenerator.depict(DepictionGenerator.java:326)
	at org.openscience.cdk.depict.DepictionTest.testAtomPropertyEmptyStringAnnotationLabel(DepictionTest.java:147)
	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1596)
```

I looked through the stack trace and put in a simple check that prevents the `ArrayIndexOutOfBoundsException`. However, I am not sure if this is the proper place to fix this.

One could ask the question if it is a user input mistake to add an empty `String` as a property to an atom (`atom.setProperty(CDKConstants.COMMENT, "")`). In this particular case, preventing the exception from bubbling to the surface seems like a good choice to me.

I also implemented a few code cleanups in the 2nd commit (unused imports, API call simplifications, method references).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbda1cd61b41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.