# Issue

**Title:** Bump immutable and ketcher-react in /utils/indigo-service/frontend/ui

## Description

Bumps [immutable](https://github.com/immutable-js/immutable-js) to 4.3.9 and updates ancestor dependency [ketcher-react](https://github.com/epam/ketcher/tree/HEAD/packages/ketcher-react). These dependencies need to be updated together.

Updates `immutable` from 4.3.0 to 4.3.9
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/immutable-js/immutable-js/releases">immutable's releases</a>.</em></p>
<blockquote>
<h2>v4.3.9</h2>
<h1>What's changed</h1>
<ul>
<li>fix(List): guard oversized bounds in setListBounds. Fixes CVE <a href="https://github.com/immutable-js/immutable-js/security/advisories/GHSA-v56q-mh7h-f735">https://github.com/immutable-js/immutable-js/security/advisories/GHSA-v56q-mh7h-f735</a></li>
<li>perf(Map): index large hash-collision buckets for faster lookups. Fixes CVE <a href="https://github.com/immutable-js/immutable-js/security/advisories/GHSA-xvcm-6775-5m9r">https://github.com/immutable-js/immutable-js/security/advisories/GHSA-xvcm-6775-5m9r</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/immutable-js/immutable-js/compare/v4.3.8...v4.3.9">https://github.com/immutable-js/immutable-js/compare/v4.3.8...v4.3.9</a></p>
<h2>v4.3.8</h2>
<p>Fix Improperly Controlled Modification of Object Prototype Attributes ('Prototype Pollution') in immutable</p>
<h2>v4.3.7</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix issue with slice negative of filtered sequence by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#2006</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/immutable-js/immutable-js/compare/v4.3.6...v4.3.7">https://github.com/immutable-js/immutable-js/compare/v4.3.6...v4.3.7</a></p>
<h2>v4.3.6</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix Repeat(<!-- raw HTML omitted -->).equals(undefined) incorrectly returning true by <a href="https://github.com/butchler"><code>@​butchler</code></a> in <a href="">immutable-js/immutable-js#1994</a></li>
</ul>
<h3>Internals</h3>
<ul>
<li>change youtube image by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#1973</a></li>
<li>Upgrade eslint and ignore no-constructor-return rule for actual constructors by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#1974</a></li>
<li>upgrate documentation website to next 14 by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#1975</a></li>
<li>start migrating to nextjs app router by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#1976</a></li>
<li>upgrade next sitemap by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#1978</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/butchler"><code>@​butchler</code></a> made their first contribution in <a href="">immutable-js/immutable-js#1994</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/immutable-js/immutable-js/compare/v4.3.5...v4.3.6">https://github.com/immutable-js/immutable-js/compare/v4.3.5...v4.3.6</a></p>
<h2>v4.3.5</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix Set.fromKeys types with Map constructor in TS 5.0 by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#1971</a></li>
<li>upgrade to TS 5.1 by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#1972</a></li>
<li>fix dist-stats command by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#1964</a></li>
<li>fix Read the Docs link on readme by <a href="https://github.com/joshding"><code>@​joshding</code></a> in <a href="">immutable-js/immutable-js#1970</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/joshding"><code>@​joshding</code></a> made their first contribution in <a href="">immutable-js/immutable-js#1970</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/immutable-js/immutable-js/compare/v4.3.4...v4.3.5">https://github.com/immutable-js/immutable-js/compare/v4.3.4...v4.3.5</a></p>
<h2>4.3.4</h2>
<h2>What's Changed</h2>
<ul>
<li>Rollback toJS type due to circular reference error by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#1958</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/immutable-js/immutable-js/blob/main/CHANGELOG.md">immutable's changelog</a>.</em></p>
<blockquote>
<h2>4.3.9</h2>
<ul>
<li>fix(List): guard oversized bounds in setListBounds. Fixes CVE <a href="https://github.com/immutable-js/immutable-js/security/advisories/GHSA-v56q-mh7h-f735">https://github.com/immutable-js/immutable-js/security/advisories/GHSA-v56q-mh7h-f735</a></li>
<li>perf(Map): index large hash-collision buckets for faster lookups. Fixes CVE <a href="https://github.com/immutable-js/immutable-js/security/advisories/GHSA-xvcm-6775-5m9r">https://github.com/immutable-js/immutable-js/security/advisories/GHSA-xvcm-6775-5m9r</a></li>
</ul>
<h2>5.1.7</h2>
<ul>
<li>fix(Repeat): lastIndexOf returned size instead of size - 1 by <a href="https://github.com/chatman-media"><code>@​chatman-media</code></a> in <a href="">immutable-js/immutable-js#2227</a>. Fixes CVE <a href="https://github.com/immutable-js/immutable-js/security/advisories/GHSA-wf6x-7x77-mvgw">CVE-2026-29063 </a></li>
<li>fix(IndexedCollection): <code>has(index)</code> on a lazy <code>Seq</code> of unknown size now checks index existence instead of searching for a value equal to the index <a href="">#2203</a></li>
<li>[TypeScript]: <code>reduce</code>/<code>reduceRight</code> without an initial value now infer the result type from the collection's values when the reducer returns a value (e.g. <code>list.reduce((a, b) =&gt; a + b)</code> infers <code>number</code>), matching <code>Array#reduce</code>. Previously an explicit type argument was required. <a href="">#2205</a></li>
</ul>
<h2>5.1.6</h2>
<ul>
<li>fix(reverseFactory): read <code>reversedSequence.size</code> in <code>__iterator</code> instead of this <a href="">#2196</a></li>
</ul>
<h2>5.1.5</h2>
<ul>
<li>Fix Improperly Controlled Modification of Object Prototype Attributes ('Prototype Pollution') in immutable</li>
</ul>
<h2>5.1.4</h2>
<ul>
<li>Migrate some files to TS by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#2125</a>
<ul>
<li>Iterator.ts</li>
<li>PairSorting.ts</li>
<li>toJS.ts</li>
<li>Math.ts</li>
<li>Hash.ts</li>
</ul>
</li>
<li>Extract CollectionHelperMethods and convert to TS by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#2131</a></li>
<li>Use npm <a href="https://docs.npmjs.com/trusted-publishers">trusted publishing only</a> to avoid token stealing.</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix/a11y issues by <a href="https://github.com/lyannel"><code>@​lyannel</code></a> in <a href="">immutable-js/immutable-js#2136</a></li>
<li>Doc add Map.get signature update by <a href="https://github.com/borracciaBlu"><code>@​borracciaBlu</code></a> in <a href="">immutable-js/immutable-js#2138</a></li>
<li>fix(doc):minor-issues#2132 by <a href="https://github.com/JayMeDotDot"><code>@​JayMeDotDot</code></a> in <a href="">immutable-js/immutable-js#2133</a></li>
<li>Fix algolia search by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#2135</a></li>
<li>Typo in OrderedMap by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#2144</a></li>
</ul>
<h3>Internal</h3>
<ul>
<li>chore: Sort all imports and activate eslint import rule by <a href="https://github.com/jdeniau"><code>@​jdeniau</code></a> in <a href="">immutable-js/immutable-js#2119</a></li>
</ul>
<h2>5.1.3</h2>
<h3>TypeScript</h3>
<ul>
<li>fix: allow readonly map entry constructor by <a href="https://github.com/septs"><code>@​septs</code></a> in <a href="">immutable-js/immutable-js#2123</a></li>
</ul>
<h3>Documentation</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5da7919</code></a> 4.3.9</li>
<li><a href=""><code>794a1a9</code></a> Merge commit from fork</li>
<li><a href=""><code>3dd7e56</code></a> perf(Map): index large hash-collision buckets for faster lookups</li>
<li><a href=""><code>62d0b58</code></a> fix ts in tests</li>
<li><a href=""><code>8c0e5f8</code></a> Merge commit from fork</li>
<li><a href=""><code>f0bc997</code></a> Merge commit from fork</li>
<li><a href=""><code>8ac83f4</code></a> change tag</li>
<li><a href=""><code>f7373e5</code></a> use id-token to deploy 4.x version</li>
<li><a href=""><code>2f545ad</code></a> changelog</li>
<li><a href=""><code>485cbe0</code></a> 4.3.8</li>
<li>Additional commits viewable in <a href="https://github.com/immutable-js/immutable-js/compare/v4.3.0...v4.3.9">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for immutable since your current version.</p>
</details>
<br />

Updates `ketcher-react` from 2.25.0-rc.5 to 3.17.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/epam/ketcher/releases">ketcher-react's releases</a>.</em></p>
<blockquote>
<h2>Ketcher 3.17.1 July 16, 2026</h2>
<h2>What's Changed</h2>
<ul>
<li>Backmerge: <a href="">#10482</a> - XSS executes if open monomer with vulnerable label in KET file</li>
</ul>
<h2>Ketcher 3.17.0 July 13, 2026</h2>
<h2>What's Changed</h2>
<h3>New features</h3>
<ul>
<li><a href="">#8855</a> – Add preset-specific error messages in monomer creation wizard</li>
<li><a href="">#8922</a> – Add Edit Instance prefill for monomer creation wizard</li>
<li><a href="">#9456</a> – Add BILN format and monomer alias support</li>
<li><a href="">#6784</a> – Home and End keys support in Sequence mode</li>
</ul>
<h3>Bugfixes and improvements</h3>
<ul>
<li><a href="">#8779</a> – Allow moving selected S-groups and monomers in molecules mode</li>
<li><a href="">#9779</a> – Add an additional amino acid (E*) and assign it and D* a new modification type</li>
<li><a href="">#9757</a> – App crashes while editing sequence containing particular ambiguous monomers</li>
<li><a href="">#7726</a> – Bond thickness is less than others on monomer preview</li>
<li><a href="">#8006</a> – LGAs label numerals are not subscripted</li>
<li><a href="">#9820</a> – Adding bond to atom could ended with wrong bond angle if user slightly moved mouse during click</li>
<li><a href="">#9692</a> – RNA Builder: Impossible to specify the phosphate position before any preset components are added</li>
<li><a href="">#9990</a> – Undo has no effect on bond type changes</li>
<li><a href="">#9738</a> – Swap stereo labels and stereo atoms when bond is flipped</li>
<li><a href="">#8251</a> – Monomer should be selected on the canvas after creation</li>
<li><a href="">#9489</a> – Nucleotide presets: Creating preset with the same component codes replaces properties of the existing preset</li>
<li><a href="">#7546</a> – Canvas does not reset scroll position after using “Clear canvas” - added monomers appear offset</li>
<li><a href="">#9751</a> – RNA Builder: Missing &quot;Switch to right/left&quot; tooltips when hovering over the phosphate position picker options</li>
<li><a href="">#9731</a> – Rotation tool: Rotation center of partially selected structure changes color when hovering over</li>
<li><a href="">#9383</a> – Rotation tool: After moving the rotation center the rotation handle is not set to the starting position and rotation circle does not cross the dashed line</li>
<li><a href="">#8181</a> – It is possible to define preset (group) name more than 200 symbols</li>
<li><a href="">#6273</a> – Thick foreground bonds do not work if the atoms are not carbons</li>
<li><a href="">#9837</a> – Correct the warning message for unusual base leaving group</li>
<li><a href="">#8199</a> – System allow to upload monomer that has IDT alises that is longer than allowed (it shouldn't!)</li>
<li><a href="">#4309</a> – Delete and Backspace hotkeys deletes elements under mouse cursor (hover), but not selected ones</li>
<li><a href="">#8198</a> – It is possible to add monomer with HELM alias is too long</li>
<li><a href="">#5849</a> – Expanded monomer inconsistent behaviour</li>
<li><a href="">#8600</a> – Single Up bond between two monomers painted wrong</li>
<li><a href="">#4093</a> – Keep loading indicator visible until paste completes</li>
<li><a href="">#9349</a> – Stereo group labels are overlapped</li>
<li><a href="">#5468</a> – Multi-Tailed Arrow can't be selected if Structure Selection Tool is used and clicking on tails or head</li>
<li><a href="">#8778</a> – Only show the possible monomer properties in the attributes panel in the monomer creation wizard</li>
<li><a href="">#8173</a> – IDT alias could be longer than 10 symbols without slashes</li>
<li><a href="">#10134</a> – Update the help document (3.16.)</li>
<li><a href="">#9991</a> – Remove &quot;Highlight&quot; checkbox from monomer creation wizard</li>
<li><a href="">#10054</a> – Nucleotide preset: R-group labels disappear when switching component tabs</li>
<li><a href="">#9299</a> – Fixes on new lexical library</li>
<li><a href="">#10102</a> – Type combobox is empty if S-Group Properties` dialog opened for Copolymer s-group for edit</li>
<li><a href="">#7940</a> – Export to HELM of monomer with attached micromolecule should cause warning message: The molecule will be exported using inline SMILES, and on load will appear as a CHEM monomer</li>
<li><a href="">#10260</a> – Warning message for unusual base leaving group incorrectly refers to &quot;hydroxyl&quot; instead of &quot;hydrogen&quot;</li>
<li><a href="">#10146</a> – Migrate to Indigo v1.45.0 in-browser module</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>37b6fc4</code></a> Backmerge: <a href="">#10482</a> - XSS executes if open monomer with vulnerable label in KET...</li>
<li><a href=""><code>a3ad48c</code></a> Update Ketcher to public version 3.17.0 (<a href="">#10426</a>)</li>
<li><a href=""><code>39c0fc5</code></a> <a href="">#10260</a> - Warning message for unusual base leaving group incorrectly refers to...</li>
<li><a href=""><code>e27d059</code></a> <a href="">#10146</a> - Migrate to Indigo v1.45.0-rc.2 in-browser module (<a href="">#10147</a>)</li>
<li><a href=""><code>08e78d8</code></a> <a href="">#10102</a> - Type combobox is empty if S-Group Properties` dialog opened for Copo...</li>
<li><a href=""><code>8387a1b</code></a> <a href="">#9299</a> - Fixes on new lexical library (<a href="">#9819</a>)</li>
<li><a href=""><code>f51e7eb</code></a> <a href="">#10054</a> - Fix R-group labels disappearing on tab switch (<a href="">#10145</a>)</li>
<li><a href=""><code>3cd7f2b</code></a> <a href="">#9927</a> - Refactor: Bunch of sonar problems (<a href="">#9981</a>)</li>
<li><a href=""><code>796898c</code></a> <a href="">#9991</a> - Remove &quot;Highlight&quot; checkbox from monomer creation wizard (<a href="">#10130</a>)</li>
<li><a href=""><code>d8b4c30</code></a> Refactor: fix circular deps in ketcher-react, add check (<a href="">#10135</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/epam/ketcher/commits/v3.17.1/packages/ketcher-react">compare view</a></li>
</ul>
</details>
<br />

You can trigger a rebase of this PR by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/Indigo/network/alerts).

</details>

> **Note**
> Automatic rebases have been disabled on this pull request as it has been open for over 30 days.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5db2bf7f35e5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.