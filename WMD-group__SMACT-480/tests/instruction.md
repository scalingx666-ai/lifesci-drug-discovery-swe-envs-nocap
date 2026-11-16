# Issue

**Title:** Bump pymatviz from 0.15.1 to 0.16.0

## Description

Bumps [pymatviz](https://github.com/janosh/pymatviz) from 0.15.1 to 0.16.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/janosh/pymatviz/releases">pymatviz's releases</a>.</em></p>
<blockquote>
<h2>v0.16.0</h2>
<!-- raw HTML omitted -->
<h2>What's Changed</h2>
<ul>
<li>Add <code>py-pkg-treemap()</code> <a href=""><code></code></a></li>
<li>Add <code>color_scale</code> param to allow for linear, logarithmic, arcsinh scaling of property values in <code>cluster_compositions</code> <a href=""><code></code></a></li>
<li>refactor cluster_compositions to take DataFrame as 1st arg, not composition list <a href=""><code></code></a></li>
<li>Test example scripts with <code>uv run</code> in CI <a href=""><code></code></a></li>
<li>New <code>cluster</code> module with functions for embedding, projecting and scattering compositions <a href=""><code></code></a></li>
<li>spacegroup_sunburst and chem_sys_sunburst: add keywords max_slices and max_slices_mode: other | none <a href=""><code></code></a></li>
<li>Multi-trace <code>plotly</code> powerups <a href=""><code></code></a></li>
<li><code>brillouin_zone_3d</code> now supports multiple structures/atoms in customizable grid layouts <a href=""><code></code></a></li>
<li>Add <code>max_cells: int | None</code> keyword to <code>chem_sys_treemap</code> <a href=""><code></code></a></li>
<li><code>structure_(2|3)d_plotly</code> enable gradient-colored bonds <a href=""><code></code></a></li>
<li>Auto font color for high contrast of element symbols in <code>ptable_heatmap_splits_plotly</code> <a href=""><code></code></a></li>
<li>Update <code>luminance</code> calculation to use WCAG 2.0 standard coefficients <a href=""><code></code></a></li>
<li>Fix <code>structure_2d_plotly</code> <code>rotation</code> keyword not applying to unit cell <a href=""><code></code></a></li>
<li><code>spglib</code> to <code>moyo</code> <a href=""><code></code></a></li>
<li>fix bond drawing in structure_3d_plotly with better image atom handling <a href=""><code></code></a></li>
<li>Use SI suffix number format in ptable colorbar tick labels <a href=""><code></code></a></li>
<li>fix error in docstring <a href=""><code></code></a></li>
<li>Remove <code>matplotlib</code>-based periodic table plotting functions <a href=""><code></code></a></li>
<li>Ward metallic glasses train/val/test splits <a href=""><code></code></a></li>
<li>Codecov <a href=""><code></code></a></li>
<li>Support per-split colorbars and colorscales in <code>ptable_heatmap_splits_plotly()</code> <a href=""><code></code></a></li>
<li>add <code>enhance_parity_plot()</code> powerup <a href=""><code></code></a></li>
<li>add treemap.py with new chem_sys_treemap plot function <a href=""><code></code></a></li>
<li>add chem_sys_sunburst() to pymatviz/sunburst.py to visualize chemical system distributions <a href=""><code></code></a></li>
<li>test metallic glass feature engineering and model evaluation <a href=""><code>f0c5174</code></a></li>
<li>better colorbar tick formatting and spacing in density_scatter_plotly <a href=""><code>d1d51b4</code></a></li>
<li>RDF plotting hide legend for single structure <a href=""><code>dc8a1a2</code></a></li>
<li>fix confusion_matrix() mismatch of false-positive/negative counts and heatmap color <a href=""><code>ae5b629</code></a></li>
<li><code>contrast_ratio()</code> in <code>pymatviz/utils/plotting.py</code> to calculate color contrast according to WCAG 2.0 <a href=""><code>b7c30cf</code></a></li>
<li>Add script to fetch and update papers citing pymatviz (<a href="">#277</a>) <a href=""><code>6a2b831</code></a></li>
<li>add examples/mlip_phonons.py <a href=""><code>608a12f</code></a></li>
<li>clean up examples/diatomics/calc_mlip_diatomic_curves.py and support multiple ML models <a href=""><code>d6fe3d9</code></a></li>
<li>add examples/compare_elastic_constants.py testing MACE vs MP PBE <a href=""><code>2861298</code></a></li>
<li>Refactor ROC and PR curve no-skill line plotting <a href=""><code>6d68cc1</code></a></li>
<li><code>readme.md</code> add links to source and example code for each plot function <a href=""><code>65ccb7c</code></a></li>
<li>add assets/scripts/key_enum_table.py to visualize Key enum attributes with Plotly <a href=""><code>0598bb5</code></a></li>
<li>delete unused enums Model + ElemColorMode <a href=""><code>ee296bc</code></a></li>
<li>fix ptable_heatmap_splits_plotly() incorrectly handling hide_f_block keyword resulting in missing tiles for Rf 104 through Og 118 <a href=""><code>b9ccbf0</code></a></li>
<li>force LabelEnums to have labels, gives .label type str causing less mypy headache <a href=""><code>a6825ff</code></a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/janosh/pymatviz/compare/v0.15.1...v0.16.0">https://github.com/janosh/pymatviz/compare/v0.15.1...v0.16.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/janosh/pymatviz/blob/main/changelog.md">pymatviz's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/janosh/pymatviz/compare/v0.15.1...v0.16.0">v0.16.0</a></h2>
<blockquote>
<p>2 May 2025</p>
</blockquote>
<ul>
<li>Add <code>py-pkg-treemap()</code> <a href=""><code></code></a></li>
<li>Add <code>color_scale</code> param to allow for linear, logarithmic, arcsinh scaling of property values in <code>cluster_compositions</code> <a href=""><code></code></a></li>
<li>refactor cluster_compositions to take DataFrame as 1st arg, not composition list <a href=""><code></code></a></li>
<li>Test example scripts with <code>uv run</code> in CI <a href=""><code></code></a></li>
<li>New <code>cluster</code> module with functions for embedding, projecting and scattering compositions <a href=""><code></code></a></li>
<li>spacegroup_sunburst and chem_sys_sunburst: add keywords max_slices and max_slices_mode: other | none <a href=""><code></code></a></li>
<li>Multi-trace <code>plotly</code> powerups <a href=""><code></code></a></li>
<li><code>brillouin_zone_3d</code> now supports multiple structures/atoms in customizable grid layouts <a href=""><code></code></a></li>
<li>Add <code>max_cells: int | None</code> keyword to <code>chem_sys_treemap</code> <a href=""><code></code></a></li>
<li><code>structure_(2|3)d_plotly</code> enable gradient-colored bonds <a href=""><code></code></a></li>
<li>Auto font color for high contrast of element symbols in <code>ptable_heatmap_splits_plotly</code> <a href=""><code></code></a></li>
<li>Update <code>luminance</code> calculation to use WCAG 2.0 standard coefficients <a href=""><code></code></a></li>
<li>Fix <code>structure_2d</code> <code>rotation</code> keyword not applying to unit cell <a href=""><code></code></a></li>
<li><code>spglib</code> to <code>moyo</code> <a href=""><code></code></a></li>
<li>fix bond drawing in structure_3d with better image atom handling <a href=""><code></code></a></li>
<li>Use SI suffix number format in ptable colorbar tick labels <a href=""><code></code></a></li>
<li>fix error in docstring <a href=""><code></code></a></li>
<li>Remove <code>matplotlib</code>-based periodic table plotting functions <a href=""><code></code></a></li>
<li>Ward metallic glasses train/val/test splits <a href=""><code></code></a></li>
<li>Codecov <a href=""><code></code></a></li>
<li>Support per-split colorbars and colorscales in <code>ptable_heatmap_splits_plotly()</code> <a href=""><code></code></a></li>
<li>add <code>enhance_parity_plot()</code> powerup <a href=""><code></code></a></li>
<li>add treemap.py with new chem_sys_treemap plot function <a href=""><code></code></a></li>
<li>add chem_sys_sunburst() to pymatviz/sunburst.py to visualize chemical system distributions <a href=""><code></code></a></li>
<li>test metallic glass feature engineering and model evaluation <a href=""><code>f0c5174</code></a></li>
<li>better colorbar tick formatting and spacing in density_scatter <a href=""><code>d1d51b4</code></a></li>
<li>RDF plotting hide legend for single structure <a href=""><code>dc8a1a2</code></a></li>
<li>fix confusion_matrix() mismatch of false-positive/negative counts and heatmap color <a href=""><code>ae5b629</code></a></li>
<li><code>contrast_ratio()</code> in <code>pymatviz/utils/plotting.py</code> to calculate color contrast according to WCAG 2.0 <a href=""><code>b7c30cf</code></a></li>
<li>Add script to fetch and update papers citing pymatviz (<a href="">#277</a>) <a href=""><code>6a2b831</code></a></li>
<li>add examples/mlip_phonons.py <a href=""><code>608a12f</code></a></li>
<li>clean up examples/diatomics/calc_mlip_diatomic_curves.py and support multiple ML models <a href=""><code>d6fe3d9</code></a></li>
<li>add examples/compare_elastic_constants.py testing MACE vs MP PBE <a href=""><code>2861298</code></a></li>
<li>Refactor ROC and PR curve no-skill line plotting <a href=""><code>6d68cc1</code></a></li>
<li><code>readme.md</code> add links to source and example code for each plot function <a href=""><code>65ccb7c</code></a></li>
<li>add assets/scripts/key_enum_table.py to visualize Key enum attributes with Plotly <a href=""><code>0598bb5</code></a></li>
<li>delete unused enums Model + ElemColorMode <a href=""><code>ee296bc</code></a></li>
<li>fix ptable_heatmap_splits_plotly() incorrectly handling hide_f_block keyword resulting in missing tiles for Rf 104 through Og 118 <a href=""><code>b9ccbf0</code></a></li>
<li>force LabelEnums to have labels, gives .label type str causing less mypy headache <a href=""><code>a6825ff</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2992f02</code></a> v0.16.0</li>
<li><a href=""><code>608a12f</code></a> add examples/mlip_phonons.py</li>
<li><a href=""><code>2d178de</code></a> Add <code>py-pkg-treemap()</code> (<a href="">#290</a>)</li>
<li><a href=""><code>ee296bc</code></a> delete unused enums Model + ElemColorMode</li>
<li><a href=""><code>3a0e734</code></a> Add <code>color_scale</code> param to allow for linear, logarithmic, arcsinh scaling of ...</li>
<li><a href=""><code>52259e9</code></a> refactor cluster_compositions to take DataFrame as 1st arg, not composition l...</li>
<li><a href=""><code>65ccb7c</code></a> <code>readme.md</code> add links to source and example code for each plot function</li>
<li><a href=""><code>c228b74</code></a> Test example scripts with <code>uv run</code> in CI (<a href="">#286</a>)</li>
<li><a href=""><code>f1710b4</code></a> New <code>cluster</code> module with functions for embedding, projecting and scattering ...</li>
<li><a href=""><code>2861298</code></a> add examples/compare_elastic_constants.py testing MACE vs MP PBE</li>
<li>Additional commits viewable in <a href="https://github.com/janosh/pymatviz/compare/v0.15.1...v0.16.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pymatviz&package-manager=pip&previous-version=0.15.1&new-version=0.16.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24d5a26abea1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.