# Issue

**Title:** Bump pymatgen from 2023.10.11 to 2024.2.20

## Description

Bumps [pymatgen](https://github.com/materialsproject/pymatgen) from 2023.10.11 to 2024.2.20.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/materialsproject/pymatgen/releases">pymatgen's releases</a>.</em></p>
<blockquote>
<h2>v2024.2.20</h2>
<!-- raw HTML omitted -->
<h2>What's Changed</h2>
<p>This release addresses an important security issue that might affect some users of pymatgen who are parsing untrusted user input, for example a server using pymatgen to parse a user-uploaded CIF file. More information is available in the associated <a href="https://github.com/materialsproject/pymatgen/security/advisories/GHSA-vgv8-5cpj-qj2f">CVE</a>. Thank you to <a href="https://github.com/SteakEnthusiast"><code>William Khem-Marquez (@​SteakEnthusiast)</code></a> for the discovery and responsible disclosure of this issue.</p>
<h3>🐛 Bug Fixes</h3>
<ul>
<li>Revert back <code>TransformedStructure.__getattr__</code> by <a href="https://github.com/mjwen"><code>@​mjwen</code></a> in <a href="">materialsproject/pymatgen#3617</a></li>
<li>Fixed Incar object to allow for ML_MODE vasp tag by <a href="https://github.com/davidwaroquiers"><code>@​davidwaroquiers</code></a> in <a href="">materialsproject/pymatgen#3625</a></li>
<li>Add missing <code>MPSCANRelaxSet.yaml</code> parameters and alphabetize by <a href="https://github.com/Andrew-S-Rosen"><code>@​Andrew-S-Rosen</code></a> in <a href="">materialsproject/pymatgen#3615</a></li>
<li>Fix <code>bader_analysis_from_path</code> using warning as file path and reinstate test by <a href="https://github.com/janosh"><code>@​janosh</code></a> in <a href="">materialsproject/pymatgen#3632</a></li>
</ul>
<h3>🛠 Enhancements</h3>
<ul>
<li>Breaking: fix SubstrateAnalyzer film + substrate vectors not using original crystal coordinates by <a href="https://github.com/jinlhr542"><code>@​jinlhr542</code></a> in <a href="">materialsproject/pymatgen#3572</a></li>
<li>Handle invalid selective dynamics info in POSCAR by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a> in <a href="">materialsproject/pymatgen#3539</a></li>
<li>Return <code>self</code> from all <code>SiteCollection/Structure/Molecule</code> in-place modification methods by <a href="https://github.com/janosh"><code>@​janosh</code></a> in <a href="">materialsproject/pymatgen#3623</a></li>
<li>Make the POTCAR setup instructions clearer by <a href="https://github.com/Andrew-S-Rosen"><code>@​Andrew-S-Rosen</code></a> in <a href="">materialsproject/pymatgen#3630</a></li>
</ul>
<h3>🧹 House-Keeping</h3>
<ul>
<li>Refactors + types + fix doc string returns to use Google format by <a href="https://github.com/janosh"><code>@​janosh</code></a> in <a href="">materialsproject/pymatgen#3620</a></li>
</ul>
<h3>🚀 Performance</h3>
<ul>
<li>Speeding up <code>get_nn_info</code> in local_env.py by <a href="https://github.com/ftherrien"><code>@​ftherrien</code></a> in <a href="">materialsproject/pymatgen#3635</a></li>
</ul>
<h3>💥 Breaking Changes</h3>
<ul>
<li>Lobsterenv improvements by <a href="https://github.com/naik-aakash"><code>@​naik-aakash</code></a> in <a href="">materialsproject/pymatgen#3624</a></li>
</ul>
<h3>🤷‍♂️ Other Changes</h3>
<ul>
<li>Fix URL joining in OptimadeRester by <a href="https://github.com/rdamaral"><code>@​rdamaral</code></a> in <a href="">materialsproject/pymatgen#3613</a></li>
<li>Create a <code>CODEOWNERS</code> by <a href="https://github.com/Andrew-S-Rosen"><code>@​Andrew-S-Rosen</code></a> in <a href="">materialsproject/pymatgen#3616</a></li>
<li>Adds support for an <code>MSONAtoms</code> class that's an <code>MSONable</code> form of an ASE <code>Atoms</code> object by <a href="https://github.com/Andrew-S-Rosen"><code>@​Andrew-S-Rosen</code></a> in <a href="">materialsproject/pymatgen#3619</a></li>
<li>Lobster io improvements by <a href="https://github.com/naik-aakash"><code>@​naik-aakash</code></a> in <a href="">materialsproject/pymatgen#3627</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/jinlhr542"><code>@​jinlhr542</code></a> made their first contribution in <a href="">materialsproject/pymatgen#3572</a></li>
<li><a href="https://github.com/rdamaral"><code>@​rdamaral</code></a> made their first contribution in <a href="">materialsproject/pymatgen#3613</a></li>
<li><a href="https://github.com/ftherrien"><code>@​ftherrien</code></a> made their first contribution in <a href="">materialsproject/pymatgen#3635</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/materialsproject/pymatgen/compare/v2024.2.8...v2024.2.20">https://github.com/materialsproject/pymatgen/compare/v2024.2.8...v2024.2.20</a></p>
<h2>v2024.2.8</h2>
<!-- raw HTML omitted -->
<h2>What's Changed</h2>
<h3>🐛 Bug Fixes</h3>
<ul>
<li>Fix <code>Vasprun.get_potcars</code> search method; tweak fake POTCARs by <a href="https://github.com/esoteric-ephemera"><code>@​esoteric-ephemera</code></a> in <a href="">materialsproject/pymatgen#3587</a></li>
</ul>
<h3>🛠 Enhancements</h3>
<ul>
<li>Aims input sets by <a href="https://github.com/tpurcell90"><code>@​tpurcell90</code></a> in <a href="">materialsproject/pymatgen#3482</a></li>
<li>Add <code>SiteCollection.reduced_formula</code> property by <a href="https://github.com/janosh"><code>@​janosh</code></a> in <a href="">materialsproject/pymatgen#3610</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/materialsproject/pymatgen/blob/master/docs/CHANGES.md">pymatgen's changelog</a>.</em></p>
<blockquote>
<h2>v2024.2.20</h2>
<p>This release addresses an important security issue that might affect some users of pymatgen who are parsing untrusted user input, for example a server using pymatgen to parse a user-uploaded CIF file. More information is available in the associated <a href="https://github.com/materialsproject/pymatgen/security/advisories/GHSA-vgv8-5cpj-qj2f">CVE</a>. Thank you to <a href="https://github.com/SteakEnthusiast"><code>William Khem-Marquez (@​SteakEnthusiast)</code></a> for the discovery and responsible disclosure of this issue.</p>
<h3>🐛 Bug Fixes</h3>
<ul>
<li>Revert back <code>TransformedStructure.__getattr__</code> by <a href="https://github.com/mjwen"><code>@​mjwen</code></a> in <a href="">materialsproject/pymatgen#3617</a></li>
<li>Fixed Incar object to allow for ML_MODE vasp tag by <a href="https://github.com/davidwaroquiers"><code>@​davidwaroquiers</code></a> in <a href="">materialsproject/pymatgen#3625</a></li>
<li>Add missing <code>MPSCANRelaxSet.yaml</code> parameters and alphabetize by <a href="https://github.com/Andrew-S-Rosen"><code>@​Andrew-S-Rosen</code></a> in <a href="">materialsproject/pymatgen#3615</a></li>
<li>Fix <code>bader_analysis_from_path</code> using warning as file path and reinstate test by <a href="https://github.com/janosh"><code>@​janosh</code></a> in <a href="">materialsproject/pymatgen#3632</a></li>
</ul>
<h3>🛠 Enhancements</h3>
<ul>
<li>Breaking: fix SubstrateAnalyzer film + substrate vectors not using original crystal coordinates by <a href="https://github.com/jinlhr542"><code>@​jinlhr542</code></a> in <a href="">materialsproject/pymatgen#3572</a></li>
<li>Handle invalid selective dynamics info in POSCAR by <a href="https://github.com/DanielYang59"><code>@​DanielYang59</code></a> in <a href="">materialsproject/pymatgen#3539</a></li>
<li>Return <code>self</code> from all <code>SiteCollection/Structure/Molecule</code> in-place modification methods by <a href="https://github.com/janosh"><code>@​janosh</code></a> in <a href="">materialsproject/pymatgen#3623</a></li>
<li>Make the POTCAR setup instructions clearer by <a href="https://github.com/Andrew-S-Rosen"><code>@​Andrew-S-Rosen</code></a> in <a href="">materialsproject/pymatgen#3630</a></li>
</ul>
<h3>🧹 House-Keeping</h3>
<ul>
<li>Refactors + types + fix doc string returns to use Google format by <a href="https://github.com/janosh"><code>@​janosh</code></a> in <a href="">materialsproject/pymatgen#3620</a></li>
</ul>
<h3>🚀 Performance</h3>
<ul>
<li>Speeding up <code>get_nn_info</code> in local_env.py by <a href="https://github.com/ftherrien"><code>@​ftherrien</code></a> in <a href="">materialsproject/pymatgen#3635</a></li>
</ul>
<h3>💥 Breaking Changes</h3>
<ul>
<li>Lobsterenv improvements by <a href="https://github.com/naik-aakash"><code>@​naik-aakash</code></a> in <a href="">materialsproject/pymatgen#3624</a></li>
</ul>
<h3>🤷‍♂️ Other Changes</h3>
<ul>
<li>Fix URL joining in OptimadeRester by <a href="https://github.com/rdamaral"><code>@​rdamaral</code></a> in <a href="">materialsproject/pymatgen#3613</a></li>
<li>Create a <code>CODEOWNERS</code> by <a href="https://github.com/Andrew-S-Rosen"><code>@​Andrew-S-Rosen</code></a> in <a href="">materialsproject/pymatgen#3616</a></li>
<li>Adds support for an <code>MSONAtoms</code> class that's an <code>MSONable</code> form of an ASE <code>Atoms</code> object by <a href="https://github.com/Andrew-S-Rosen"><code>@​Andrew-S-Rosen</code></a> in <a href="">materialsproject/pymatgen#3619</a></li>
<li>Lobster io improvements by <a href="https://github.com/naik-aakash"><code>@​naik-aakash</code></a> in <a href="">materialsproject/pymatgen#3627</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/jinlhr542"><code>@​jinlhr542</code></a> made their first contribution in <a href="">materialsproject/pymatgen#3572</a></li>
<li><a href="https://github.com/rdamaral"><code>@​rdamaral</code></a> made their first contribution in <a href="">materialsproject/pymatgen#3613</a></li>
<li><a href="https://github.com/ftherrien"><code>@​ftherrien</code></a> made their first contribution in <a href="">materialsproject/pymatgen#3635</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/materialsproject/pymatgen/compare/v2024.2.8...v2024.2.20">https://github.com/materialsproject/pymatgen/compare/v2024.2.8...v2024.2.20</a></p>
<h2>v2024.2.8</h2>
<h3>🐛 Bug Fixes</h3>
<ul>
<li>Fix <code>Vasprun.get_potcars</code> search method; tweak fake POTCARs by <a href="https://github.com/esoteric-ephemera"><code>@​esoteric-ephemera</code></a> in <a href="">materialsproject/pymatgen#3587</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>013ccb5</code></a> v2024.2.20</li>
<li><a href=""><code>bde66a4</code></a> v2024.2.20</li>
<li><a href=""><code>38b9b58</code></a> Speeding up <code>get_nn_info</code> in local_env.py (<a href="">#3635</a>)</li>
<li><a href=""><code>bd88e0d</code></a> [WIP] Lobsterenv improvements (<a href="">#3624</a>)</li>
<li><a href=""><code>ff45527</code></a> Fix <code>bader_analysis_from_path</code> using warning as file path and reinstate test ...</li>
<li><a href=""><code>5514ff5</code></a> Make the POTCAR setup instructions clearer (<a href="">#3630</a>)</li>
<li><a href=""><code>170c701</code></a> Add missing <code>MPSCANRelaxSet.yaml</code> parameters and alphabetize (<a href="">#3615</a>)</li>
<li><a href=""><code>d44363e</code></a> Fixed Incar object to allow for ML_MODE vasp tag (<a href="">#3625</a>)</li>
<li><a href=""><code>988da0c</code></a> Fix NotImplementedError messages in InputSet subclasses</li>
<li><a href=""><code>0f474f6</code></a> Lobster io improvements (<a href="">#3627</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/materialsproject/pymatgen/compare/v2023.10.11...v2024.2.20">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pymatgen&package-manager=pip&previous-version=2023.10.11&new-version=2024.2.20)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/LopezGroup-ICIQ/care/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8b9a8e13a54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.