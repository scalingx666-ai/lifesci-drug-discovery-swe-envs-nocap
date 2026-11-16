# Issue

**Title:** Fix TPSA contributions for sulfur and phosphorus in three-membered rings

## Description

With default settings, `TPSADescriptor` returns `0.0` for both `C1CS1` and `CP1CC1`. [Ertl's Table 1](https://peter-ertl.com/reprints/Ertl-JMC-43-3714-2000.pdf#page=2) gives sulfur and phosphorus contributions of 25.30 Å² and 13.59 Å², respectively, without a separate three-membered-ring type for either element.

```java
var parser = new SmilesParser(SilentChemObjectBuilder.getInstance());
for (String smiles : new String[]{"C1CS1", "CP1CC1"})
    System.out.println(new TPSADescriptor().calculate(parser.parseSmiles(smiles)).getValue());
```

We now set the ring-specific profile field only for nitrogen and oxygen, so sulfur and phosphorus match their existing fragments. The new regression test fails before the fix and passes after it, and the molecular descriptor suite passes.

— [ChipLab](https://chiplab.donmakino.com/findings#clab-2026-1327)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf73c726634a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.