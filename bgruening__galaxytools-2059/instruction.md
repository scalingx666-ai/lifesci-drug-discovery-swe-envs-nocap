# Issue

**Title:** agat: update tool wrapper (issue #2058)

## Description

The `functional_analysis` mode (agat_sp_functional_statistics.pl) failed with `No such file or directory` whenever the input annotation used feature combinations other than `gene@transcript`, because the wrapper hard-coded that path while AGAT names its output sub-directories after the L1@L2 combinations actually present (e.g. `gene@mrna`, `gene@trna`, `region`). The command now concatenates `temp_output/*/table_per_feature_type.txt` so all tables AGAT produces are captured regardless of feature types. Also removed the unused `mkdir ./statistics` call and fixed wrapper validation issues (`detect_errors="aggressive"`, `format="markdown"` on help, and empty `value` attributes on the optional upstream/downstream parameters, which remain optional with no default). Added regression test 17 using a crafted GFF containing `gene@mrna`, `gene@trna`, and a standalone `region` feature, reproducing the original failure scenario. Output for the existing test 09 is byte-identical with the glob-based command, and the wrapper version is bumped to `1.7.0+galaxy1`. .

---

## Working on this tool

To review or improve this tool locally:

**If you don't have the repo yet** (forks and clones in one step):

```bash
gh repo fork bgruening/galaxytools --clone
cd galaxytools
git checkout tool-bot/issue-2058
```

**If you already have the repo:**

```bash
git fetch origin
git checkout tool-bot/issue-2058
```

The tool files are in `tools/agat/`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e50b2852a154`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.