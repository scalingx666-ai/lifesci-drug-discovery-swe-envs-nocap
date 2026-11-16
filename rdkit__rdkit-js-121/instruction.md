# Issue

**Title:** Bump @rdkit/rdkit from 0.0.0-use.local to 2022.3.2

## Description

Bumps [@rdkit/rdkit](https://github.com/rdkit/rdkit) from 0.0.0-use.local to 2022.3.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rdkit/rdkit/releases"><code>@​rdkit/rdkit</code>'s releases</a>.</em></p>
<blockquote>
<h2>2022_03_3 (Q1 2022) Release</h2>
<h1>Release_2022.03.3</h1>
<p>(Changes relative to Release_2022.03.2)</p>
<h2>Acknowledgements</h2>
<p>Andy Cai, David Cosgrove, JP Ebejer, Emanuele Guidotti, Per Johnsson, Gareth
Jones, Brian Kelley, Ricardo Rodriguez-Schmidt, Paolo Tosco, Antonio Trande</p>
<h2>Bug Fixes:</h2>
<ul>
<li>DrawMorganBit returns empty image for &quot;isolated&quot; fingerprints
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/4242">#4242</a> from eguidotti)</li>
<li>Fix for RGD dummy atom bug in RDKit::replaceCore
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5154">#5154</a> from jones-gareth)</li>
<li>Standardization via RDKit breaks molecules
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5169">#5169</a> from malteseunderdog)</li>
<li>Fix duplicate non thread safe check in VarianceDataForLabel
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5212">#5212</a> from ricrogz)</li>
<li>RDKit::Utils::LocaleSwitcher is not thread safe
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5214">#5214</a> from ricrogz)</li>
<li>Core with query atoms and no user definded attachment points may create poor decompostions
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5222">#5222</a> from jones-gareth)</li>
<li>Fix qt build under VS2019
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5238">#5238</a> from ricrogz)</li>
<li>Precondition violation on chiral Atoms with zero order bonds
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5239">#5239</a> from ricrogz)</li>
<li>pyForceFieldConstraints test failed
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5252">#5252</a> from sagitter)</li>
<li>drawReaction() should not hit a PRECONDITION with prepareMolsBeforeDrawing=false
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5259">#5259</a> from ptosco)</li>
<li>Atom annotations poorly placed on highlighted atoms
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5269">#5269</a> from DavidACosgrove)</li>
<li>make the catch tests build faster
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5284">#5284</a> from greglandrum)</li>
<li>rdMolDraw2D.PrepareMolForDrawing(None) causes segmentation fault
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5298">#5298</a> from perjo)</li>
<li>make the logging tests more robust
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5312">#5312</a> from greglandrum)</li>
<li>MolStandardize: uncharger failing in molecules with zwitterionic sulfone
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5317">#5317</a> from greglandrum)</li>
<li>MolStandardize: some operations throwing on non-standardized molecules
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5318">#5318</a> from greglandrum)</li>
<li>MolStandardize: cleanup() function not correctly reassigning stereochemistry
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5320">#5320</a> from greglandrum)</li>
<li>MolFromMolBlock should correctly assign stereochemistry to 3D molecules
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5327">#5327</a> from greglandrum)</li>
<li>assignChiralTypesFrom3D() ignores wiggly bonds
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5328">#5328</a> from greglandrum)</li>
<li>Molzip segfaults instead of throwing an error when multiple bonds are formed to the same pairs of atoms
(github <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/5334">#5334</a> from loluwot)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rdkit/rdkit/blob/master/ReleaseNotes.md"><code>@​rdkit/rdkit</code>'s changelog</a>.</em></p>
<blockquote>
<h1>Release_2022.09.1</h1>
<p>(Changes relative to Release_2022.03.1)</p>
<h2>Backwards incompatible changes</h2>
<ul>
<li><code>GetBestRMS()</code> by default now treats terminal conjugated functional groups
like carboxylate and nitro symmetrically. For example, the group
<code>C(=[O:1])[O-:2]</code> can match in either orientation. The SMARTS pattern which is
used to recognize affected groups is:
<code>[{atomP};$([{atomP}]-[*]=[{atomP}]),$([{atomP}]=[*]-[{atomP}])]~[*]</code> where
<code>{atomP}</code> is <code>O,N;D1</code>. The previous behavior can be restored using by setting
the <code>symmetrizeConjugatedTerminalGroups</code> argument to false when calling
<code>GetBestRMS()</code></li>
</ul>
<h2>Code removed in this release:</h2>
<ul>
<li>The C++ class <code>RDLog::BlockLogs</code> has been removed. Please use the class <code>RDLog::LogStateSetter</code>. The Python class rdBase.BlockLogs() is still available and supported.</li>
<li>Python function <code>rdkit.Chem.WrapLogs()</code> has been removed. Please use
<code>rdkit.rdBase.LogToPythonStderr()</code>. <code>rdkit.rdBase.WrapLogs()</code> also exists, but
unless you need the old teeing behavior, prefer the former.</li>
<li>Python function <code>rdkit.Chem.LogWarningMsg()</code> has been removed. Please use
<code>rdkit.rdBase.LogWarningMsg()</code>.</li>
<li>Python function <code>rdkit.Chem.LogErrorMsg()</code> has been removed. Please use
<code>rdkit.rdBase.LogErrorMsg()</code>.</li>
</ul>
<h2>Deprecated code (to be removed in a future release):</h2>
<h1>Release_2022.03.1</h1>
<p>(Changes relative to Release_2021.09.1)</p>
<h2>Backwards incompatible changes</h2>
<ul>
<li>When running in Jupyter Notebook, logs are now sent only to Python's
standard error stream, and no longer include the <code>RDKit LEVEL</code> prefix.</li>
<li>The Debug and Info logs are now disabled by default. If you would like to
enable them within your code you can call <code>rdBase.EnableLog(&quot;rdApp.info&quot;)</code>
and/or <code>rdBase.EnableLog(&quot;rdApp.debug&quot;)</code>.</li>
<li>The MolHash functions now reassign stereochemistry after modifying the
molecule and before calculating the hash. Previous versions would still
include information about atom/bond stereochemistry in the output hash even if
that no longer applies in the modified molecule.</li>
<li>The rules for aromaticity in rings containing dummy atoms have been changed.
The general intention of the new handling is that aromaticity will not be
perceived for rings containing dummy atoms unless it's clear that the dummies
should be aromatic. As an example: the SMILES <code>C1=C*2=CC=CC=*2C=C1</code> is
perceived to be aromatic while the SMILES <code>C1=C*2C=CC=C*2C=C1</code> (which does not
have any double bonds to the dummy atoms) is not; in previous RDKit releases
both of these structures were aromatic. There's more information about this in
the discussion of PR <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/4722">#4722</a> (<a href="https://github-redirect.dependabot.com/rdkit/rdkit/pull/4722">rdkit/rdkit#4722</a>) and
Issue <a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/4721">#4721</a> (<a href="https://github-redirect.dependabot.com/rdkit/rdkit/issues/4721">rdkit/rdkit#4721</a>).</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/rdkit/rdkit/commits">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@rdkit/rdkit&package-manager=npm_and_yarn&previous-version=0.0.0-use.local&new-version=2022.3.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ac67f2a9aa7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.