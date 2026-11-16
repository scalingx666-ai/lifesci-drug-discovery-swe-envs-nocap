# Issue

**Title:** Isotopes 2

## Description

Optimises the binary data storage format for isotopes. We can store things as fixed precision with v. minimal accuracy lost (actually less than the existing doubles). Ideally I wanted to this all to be in a class file but there is too much data to do that a hybrid approach was used.

Common functions like average mass / major isotope get fast implementations that do not required the ``isotopes.dat``. We also have a small table of common isotopes (based from PubChem stats). The average mass one is a bit of a no brainer, currently if you were doing MolWt calcs on a big dataset every element was having it's average mass recalculated again and again.

Currently the data was lazily loaded and could through an exception. Really if the exception is thrown there is something badly wrong so I could have made it unchecked when I first did it - oh well. Anyways the lazy-init also wasn't great, the nicest way to get a singleton in Java is actually an enum - however it would be nice if we only loaded the isotope binary data when we needed it. We can do this with an inner-enum.

```java
IIsotope major = Isotopes.major(IElement.C);
System.err.println(major.getMassNumber() + " " + major.getExactMass() + " " + major.getNaturalAbundance());
System.err.println(Isotopes.get(IElement.C, 12));
System.err.println(Isotopes.get(IElement.C, 13));
System.err.println(Isotopes.get(IElement.C, 18)); // now loaded!!
```

Turn on `-Dcdk.debugging=true` we see this:

```
12 12.0 98.93
12-C isotope [12.0, 98.93%]
13-C isotope [13.00335484, 1.07%]
org.openscience.cdk.config.IsotopeFactory DEBUG: Loading data/isotopes.dat
18-C isotope [18.02676, 0.0%]
```

So only when 18C is requested does the data get loaded.

This loaded is quite efficient ~1ms on my M1 Pro Macbook and in reality any reasonable size database will probably have some odd isotope which needs the full data.

For good measure I've added a check to compare the binary data to the XML BODR data, should have probably had this already.

The class for generate all of this is now in ``cdk-extra`` rather than ``cdk-build-util``

There is perhaps a discussion to be had on ``null`` for unknown major isotopes / ``0`` for average mass. It is common to return something reasonable for the odd-ball elements (e.g. 98Tc) but for now I mirrored what we currently did. It's not unreasonable to make the user handled it but moving things over (next PR) there are many places where the caller just expects a major isotope to be non-null.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8dd9e04ae38`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.