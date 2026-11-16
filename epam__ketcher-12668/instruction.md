# Issue

**Title:** #6533 - System implicitly export canvas to mol v3000 if loaded from mol v2000

## Description

<img width="959" height="500" alt="Screenshot 2026-11-09 105441" src="https://github.com/user-attachments/assets/4cb4532c-3187-4fe0-be20-81ae9b644d04" />

## Summary

Saving as MDL Molfile, Rxnfile or RDF **V2000** now always produces V2000. These three formats sent Indigo no `molfile-saving-mode`, so Indigo fell back to `auto` and wrote V3000 whenever the structure held something V2000 cannot express, such as enhanced-stereo groups. The V3000 formats and SDF V2000 (since #7939) already set the mode. This PR does the same for `mol`, `rxn` and `rdf`, as the Indigo team suggested on the issue.

```
formatProperties.ts      mol / rxn / rdf  +{ 'molfile-saving-mode': '2000' }   (molAuto stays 'auto')
formatterFactory.ts      case mol:  1. over 999 atoms/bonds  -> server, molAuto   (checked first now)
                                    2. query properties      -> server, mol ('2000')
                                    3. otherwise             -> local MolfileV2000Formatter
```

The order swap keeps an oversized structure with query properties valid. Before, it reached Indigo as plain `mol` and `auto` upgraded it to V3000. With `'2000'` it would have become an invalid V2000, so the size check now runs first and sends it through `molAuto` as before.

Plain MOL saves still use Ketcher's own V2000 writer and are unchanged. That is why the issue's file on its own already saved as V2000 on master. The bug showed wherever the save went through Indigo: MOL with query properties (including an implicit H count), and every RXN and RDF V2000 save.

## Evidence

- **Before:** Save dialog on master: the issue's file with one atom's Implicit H count set to 1, saved as MDL Molfile V2000, gives `V3000`. An enhanced-stereo reaction (`C[C@H](O)CC>>C[C@@H](O)CC |&1:1,r,&2:6|`) saved as MDL Rxnfile V2000 or RDF V2000 also gives `V3000`. 5 of the new unit tests fail on master.
  **After:** all three give `V2000`, and all formatter tests pass (34/34; 1226 in ketcher-core).

### Verified in the app

Molecules mode, Save Structure dialog. The issue's file with Implicit H count 1 shows a preview starting with `-INDIGO-` whose counts line ends in `V2000`. The issue's file as it is still shows `V2000`, written by Ketcher. The enhanced-stereo reaction saved as Rxnfile V2000 and as RDF V2000 shows `V2000`.

## Merge Danger

**Door:** one-way

It changes MOL, RXN and RDF V2000 output. Data V2000 cannot hold, such as enhanced-stereo groups, is no longer kept by silently switching to V3000. It is dropped from the V2000 file, as the user chose V2000.

**Blast Radius:** export

Only saves that go through Indigo as MOL, RXN or RDF V2000. Local MOL V2000 saves, the auto-detect MOL format (`getMolfile()` without arguments) and structures over 999 atoms or bonds are unchanged. Macromolecules mode offers only MOL V3000. Autotests that check a V2000 Save preview containing enhanced stereo or query features could show a different preview.

---



Memory bank: `.memory-bank/modules/serialization.md`

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b93c2a5be47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.