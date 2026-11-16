# Issue

**Title:** Fix exit condition in calc_distances

## Description

Probably affects #621

Before patch, one distance were skipped between atoms `# N` and `# N-1`. For single-bonded systems (like H2) it is critical since it means that they were not bounded and then a lot of artefacts happen. 

. Changes in output:
```diff
  * 1 selected distances

      #   Z          #   Z                                           value/Å
-     0   0      0   0                                     0.0000000 (max)
+     1   1 H        2   1 H                                       0.7769870 (max)

- * 0 distinct bonds (by element types)
+ * 1 distinct bonds (by element types)

    Z      Z             #   av. dist./Å        max./Å        min./Å
+   1 H    1 H           1     0.7769870     0.7769870     0.7769870
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bb036e15ef2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.