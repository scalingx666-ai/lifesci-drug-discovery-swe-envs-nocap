# Issue

**Title:** Bump pymatgen from 2025.3.10 to 2025.4.24

## Description

Bumps [pymatgen](https://github.com/materialsproject/pymatgen) from 2025.3.10 to 2025.4.24.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/materialsproject/pymatgen/releases">pymatgen's releases</a>.</em></p>
<blockquote>
<h2>v2025.4.24</h2>
<ul>
<li>Structure now has a calc_property method that enables one to get a wide range of elasticity, EOS, and phonon properties using matcalc. Requires matcalc to be
installed.</li>
<li>Bug fix and expansion of pymatgen.ext.matproj.MPRester. Now property_data is always consistent with the returned entry in get_entries. Summary data, which is not
always consistent but is more comprehensive, can be obtained via a summary_data kwarg.</li>
<li>PR <a href="">#4378</a> Avoid merging if a structure has only one site by <a href="https://github.com/kmu"><code>@​kmu</code></a>
This PR fixes an error that occurs when calling <code>merge_sites</code> on a structure with only one site. For example:</li>
<li>PR <a href="">#4372</a> Reapply update to ptable vdw radii CSV source and JSON with CRC handbook by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a>
<ul>
<li>Update ptable vdw radii CSV source, to fix <a href="">#4370</a></li>
<li>[x] Revert <a href="">#4345</a> and apply changes to CSV
vdw radii data source:</li>
</ul>
<blockquote>
<p>John R. Rumble, ed., CRC Handbook of Chemistry and Physics, 105th Edition (Internet Version 2024), CRC Press/Taylor &amp; Francis, Boca Raton, FL.
If a specific table is cited, use the format: &quot;Physical Constants of Organic Compounds,&quot; in CRC Handbook of Chemistry and Physics, 105th Edition (Internet Version 2024), John R. Rumble, ed., CRC Press/Taylor &amp; Francis, Boca Raton, FL.</p>
</blockquote>
</li>
</ul>
<h2>v2025.4.20</h2>
<ul>
<li>Updated <code>perturb</code> method to be in parity for Structure and Molecule.</li>
<li>PR <a href="">#4226</a> Fix file existence check in ChargemolAnalysis to verify directory instead. by <a href="https://github.com/lllangWV"><code>@​lllangWV</code></a></li>
<li>PR <a href="">#4324</a> GibbsComputedStructureEntry update to handle float temperature values by <a href="https://github.com/slee-lab"><code>@​slee-lab</code></a></li>
<li>PR <a href="">#4303</a> Fix mcl kpoints by <a href="https://github.com/dgaines2"><code>@​dgaines2</code></a>
Fixed errors in two of the k-points for the MCL reciprocal lattice (according to Table 16 in Setyawan-Curtarolo 2010)
M2 and D1 aren't included in the recommended k-point path, but third-party software that plots k-point paths using pymatgen labelled M2 in the path instead of M1 due to it being the &quot;same&quot; k-point.</li>
<li>PR <a href="">#4344</a> Update &quot;electron affinities&quot; in <code>periodic_table.json</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4365</a> Python 3.13 support by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
</ul>
<h2>v2025.4.19</h2>
<ul>
<li>MPRester.get_entries and get_entries_in_chemsys now supports property_data. inc_structure, conventional_only and</li>
<li>PR <a href="">#4367</a> fix perturb bug that displaced all atoms equally by <a href="https://github.com/skasamatsu"><code>@​skasamatsu</code></a></li>
<li>PR <a href="">#4361</a> Replace <code>pybtex</code> with <code>bibtexparser</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4362</a> fix(MVLSlabSet): convert DIPOL vector to pure Python list before writing INCAR by <a href="https://github.com/atulcthakur"><code>@​atulcthakur</code></a></li>
<li>PR <a href="">#4363</a> Ensure <code>actual_kpoints_weights</code> is <code>list[float]</code> and add test by <a href="https://github.com/kavanase"><code>@​kavanase</code></a></li>
<li>PR <a href="">#4345</a> Fix inconsistent &quot;Van der waals radius&quot; and &quot;Metallic radius&quot; in <code>core.periodic_table.json</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4212</a> Deprecate <code>PymatgenTest</code>, migrate tests to <code>pytest</code> from <code>unittest</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
</ul>
<h2>v2025.4.17</h2>
<ul>
<li>Bug fix for list based searches in MPRester.</li>
</ul>
<h2>v2025.4.16</h2>
<ul>
<li>Major new feature and breaking change: Legacy MP API is no longer supported. Pymatgen also no longer support mp-api in the backend. Instead, Pymatgen's MPRester now
has nearly 100% feature parity with mp-api's document searches. One major difference is that pymatgen's MPRester will follow the documented REST API end points exactly, i.e., users just need to refer to <a href="https://api.materialsproject.org/docs">https://api.materialsproject.org/docs</a> for the exact field names.</li>
<li>PR <a href="">#4360</a> Speed up <code>Vasprun</code> parsing by <a href="https://github.com/kavanase"><code>@​kavanase</code></a></li>
<li>PR <a href="">#4343</a> Drop duplicate <code>iupac_ordering</code> entries in <code>core.periodic_table.json</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4348</a> Remove deprecated grain boundary analysis by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4357</a> Fix circular import of <code>SymmOp</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
</ul>
<h2>v2025.4.10</h2>
<ul>
<li>Parity with MPRester.materials.summary.search in MPResterBasic.</li>
<li>PR <a href="">#4355</a> Fix round-trip constraints handling of <code>AseAtomsAdaptor</code> by <a href="https://github.com/yantar92"><code>@​yantar92</code></a>
<ul>
<li>src/pymatgen/io/ase.py (AseAtomsAdaptor.get_structure): When no explicit constraint is given for a site in ASE Atoms object, use &quot;T T T&quot; selective dynamics (no constraint).  The old code is plain wrong.</li>
<li>tests/io/test_ase.py (test_back_forth): Add new test case.
Fixes <a href="">#4354</a>.</li>
</ul>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/materialsproject/pymatgen/blob/master/docs/CHANGES.md">pymatgen's changelog</a>.</em></p>
<blockquote>
<h2>v2025.4.24</h2>
<ul>
<li>Structure now has a calc_property method that enables one to get a wide range of elasticity, EOS, and phonon properties using matcalc. Requires matcalc to be
installed.</li>
<li>Bug fix and expansion of pymatgen.ext.matproj.MPRester. Now property_data is always consistent with the returned entry in get_entries. Summary data, which is not
always consistent but is more comprehensive, can be obtained via a summary_data kwarg.</li>
<li>PR <a href="">#4378</a> Avoid merging if a structure has only one site by <a href="https://github.com/kmu"><code>@​kmu</code></a>
This PR fixes an error that occurs when calling <code>merge_sites</code> on a structure with only one site. For example:</li>
<li>PR <a href="">#4372</a> Reapply update to ptable vdw radii CSV source and JSON with CRC handbook by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a>
<ul>
<li>Update ptable vdw radii CSV source, to fix <a href="">#4370</a></li>
<li>[x] Revert <a href="">#4345</a> and apply changes to CSV
vdw radii data source:</li>
</ul>
<blockquote>
<p>John R. Rumble, ed., CRC Handbook of Chemistry and Physics, 105th Edition (Internet Version 2024), CRC Press/Taylor &amp; Francis, Boca Raton, FL.
If a specific table is cited, use the format: &quot;Physical Constants of Organic Compounds,&quot; in CRC Handbook of Chemistry and Physics, 105th Edition (Internet Version 2024), John R. Rumble, ed., CRC Press/Taylor &amp; Francis, Boca Raton, FL.</p>
</blockquote>
</li>
</ul>
<h2>v2025.4.20</h2>
<ul>
<li>Updated <code>perturb</code> method to be in parity for Structure and Molecule.</li>
<li>PR <a href="">#4226</a> Fix file existence check in ChargemolAnalysis to verify directory instead. by <a href="https://github.com/lllangWV"><code>@​lllangWV</code></a></li>
<li>PR <a href="">#4324</a> GibbsComputedStructureEntry update to handle float temperature values by <a href="https://github.com/slee-lab"><code>@​slee-lab</code></a></li>
<li>PR <a href="">#4303</a> Fix mcl kpoints by <a href="https://github.com/dgaines2"><code>@​dgaines2</code></a>
Fixed errors in two of the k-points for the MCL reciprocal lattice (according to Table 16 in Setyawan-Curtarolo 2010)
M2 and D1 aren't included in the recommended k-point path, but third-party software that plots k-point paths using pymatgen labelled M2 in the path instead of M1 due to it being the &quot;same&quot; k-point.</li>
<li>PR <a href="">#4344</a> Update &quot;electron affinities&quot; in <code>periodic_table.json</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4365</a> Python 3.13 support by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
</ul>
<h2>v2025.4.19</h2>
<ul>
<li>MPRester.get_entries and get_entries_in_chemsys now supports property_data. inc_structure, conventional_only and</li>
<li>PR <a href="">#4367</a> fix perturb bug that displaced all atoms equally by <a href="https://github.com/skasamatsu"><code>@​skasamatsu</code></a></li>
<li>PR <a href="">#4361</a> Replace <code>pybtex</code> with <code>bibtexparser</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4362</a> fix(MVLSlabSet): convert DIPOL vector to pure Python list before writing INCAR by <a href="https://github.com/atulcthakur"><code>@​atulcthakur</code></a></li>
<li>PR <a href="">#4363</a> Ensure <code>actual_kpoints_weights</code> is <code>list[float]</code> and add test by <a href="https://github.com/kavanase"><code>@​kavanase</code></a></li>
<li>PR <a href="">#4345</a> Fix inconsistent &quot;Van der waals radius&quot; and &quot;Metallic radius&quot; in <code>core.periodic_table.json</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4212</a> Deprecate <code>PymatgenTest</code>, migrate tests to <code>pytest</code> from <code>unittest</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
</ul>
<h2>v2025.4.17</h2>
<ul>
<li>Bug fix for list based searches in MPRester.</li>
</ul>
<h2>v2025.4.16</h2>
<ul>
<li>Major new feature and breaking change: Legacy MP API is no longer supported. Pymatgen also no longer support mp-api in the backend. Instead, Pymatgen's MPRester now
has nearly 100% feature parity with mp-api's document searches. One major difference is that pymatgen's MPRester will follow the documented REST API end points exactly, i.e., users just need to refer to <a href="https://api.materialsproject.org/docs">https://api.materialsproject.org/docs</a> for the exact field names.</li>
<li>PR <a href="">#4360</a> Speed up <code>Vasprun</code> parsing by <a href="https://github.com/kavanase"><code>@​kavanase</code></a></li>
<li>PR <a href="">#4343</a> Drop duplicate <code>iupac_ordering</code> entries in <code>core.periodic_table.json</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4348</a> Remove deprecated grain boundary analysis by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
<li>PR <a href="">#4357</a> Fix circular import of <code>SymmOp</code> by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a></li>
</ul>
<h2>v2025.4.10</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>34f5171</code></a> Update docs</li>
<li><a href=""><code>0b03a6c</code></a> Updated changelog.</li>
<li><a href=""><code>86bf5db</code></a> Add elasticity.</li>
<li><a href=""><code>9ff249e</code></a> Skip calc_prop test if matcalc is not installed.</li>
<li><a href=""><code>f86d515</code></a> Add calc_property method for Structure that enables you to use matcalc</li>
<li><a href=""><code>594633c</code></a> Allow best of both worlds - property data and summary data.</li>
<li><a href=""><code>eb954e4</code></a> modernize MPRester tests.</li>
<li><a href=""><code>e3e1160</code></a> Add test for uncorrected_energy_per_atom verfiication.</li>
<li><a href=""><code>b54ac3e</code></a> Use thermo endpoint for property_data. Fixes <a href="">#4379</a>.</li>
<li><a href=""><code>59d04ad</code></a> Skip AIMS set test on Windows. Weird bug and not critical to test on all</li>
<li>Additional commits viewable in <a href="https://github.com/materialsproject/pymatgen/compare/v2025.3.10...v2025.4.24">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pymatgen&package-manager=pip&previous-version=2025.3.10&new-version=2025.4.24)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6daf173abb7e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.