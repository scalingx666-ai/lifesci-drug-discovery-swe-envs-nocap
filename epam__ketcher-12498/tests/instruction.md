# Issue

**Title:** chore(deps): bump postcss-selector-parser

## Description

Bumps  and [postcss-selector-parser](https://github.com/postcss/postcss-selector-parser). These dependencies needed to be updated together.
Updates `postcss-selector-parser` from 6.0.15 to 7.1.7
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/postcss/postcss-selector-parser/releases">postcss-selector-parser's releases</a>.</em></p>
<blockquote>
<h2>7.1.7</h2>
<ul>
<li>fix: <code>lossless: true</code> preserves trailing whitespace in a selector that ends empty, such as <code>:not(a, )</code>. Note that <code>:not( )</code> now yields a selector holding one empty string node rather than an empty selector (<a href="">#337</a> by <a href="https://github.com/theRizwan"><code>@​theRizwan</code></a>)</li>
<li>fix: consume the whitespace that terminates a hexadecimal escape, so <code>[x=&quot;\000061 b&quot;]</code> unescapes to <code>ab</code> (<a href="">#340</a> by <a href="https://github.com/jakezwang"><code>@​jakezwang</code></a>)</li>
<li>fix: set the parent on every node passed to <code>insertBefore</code> and <code>insertAfter</code>, not only the first (<a href="">#343</a> by <a href="https://github.com/feritcemkahraman"><code>@​feritcemkahraman</code></a>)</li>
<li>fix: assigning <code>combinator.value</code> clears the stale raw spelling instead of being ignored (<a href="">#342</a> by <a href="https://github.com/SAY-5"><code>@​SAY-5</code></a>)</li>
<li>fix: keep whitespace around the namespace separator in attribute selectors, so <code>[ foo | bar ]</code> round-trips (<a href="">#339</a> by <a href="https://github.com/dkryaklin"><code>@​dkryaklin</code></a>)</li>
</ul>
<h2>7.1.6</h2>
<ul>
<li>fix: parse flat selectors in linear time, closing a CPU exhaustion vulnerability (<a href="https://github.com/advisories/GHSA-rj75-hqrm-r3gf">GHSA-rj75-hqrm-r3gf</a>, reported by Wayde Shi)</li>
</ul>
<h2>7.1.5</h2>
<ul>
<li>fix: don't treat a non-prefix token before <code>|</code> as a namespace (<a href="">#324</a> by <a href="https://github.com/spokodev"><code>@​spokodev</code></a>)</li>
<li>fix: preserve whitespace before a <code>*</code> namespace in attribute selectors (<a href="">#325</a> by <a href="https://github.com/spokodev"><code>@​spokodev</code></a>)</li>
<li>fix: TypeError on unclosed <code>[</code>, <code>(</code> and trailing <code>|</code> (<a href="">#330</a> by <a href="https://github.com/theRizwan"><code>@​theRizwan</code></a>)</li>
</ul>
<h2>7.1.4</h2>
<ul>
<li>fix: tolerate non-node children when serializing selectors</li>
</ul>
<h2>7.1.3</h2>
<ul>
<li>Improve fix CVE-2026-9358 (NVD) / SNYK-JS-POSTCSSSELECTORPARSER-16873882 (clone/walk)</li>
</ul>
<h2>7.1.2</h2>
<ul>
<li>Fix <a href="https://github.com/advisories/GHSA-w9m9-85wc-3x92">CVE-2026-9358</a> (NVD) / SNYK-JS-POSTCSSSELECTORPARSER-16873882 (<a href="">#316</a> by <a href="https://github.com/MoOx"><code>@​MoOx</code></a>)</li>
</ul>
<h2>v7.1.1</h2>
<h1>7.1.1</h1>
<ul>
<li>perf: replace startsWith with strict equality (<a href="">#308</a>)</li>
<li>fix(types): add walkUniversal declaration (<a href="">#311</a>)</li>
</ul>
<h2>v7.1.0</h2>
<h1>7.1.0</h1>
<ul>
<li>feat: insert(Before|After) support multiple new node</li>
</ul>
<h2>v7.0.0</h2>
<h1>7.0.0</h1>
<ul>
<li>Feat: make insertions during iteration safe (major)</li>
</ul>
<h2>6.1.5</h2>
<ul>
<li>fix: parse flat selectors in linear time, closing a CPU exhaustion vulnerability (<a href="https://github.com/advisories/GHSA-rj75-hqrm-r3gf">CVE-2026-104844</a> / GHSA-rj75-hqrm-r3gf, reported by Wayde Shi), backported from 7.1.6 (<a href="">#346</a> by <a href="https://github.com/bradyshutt"><code>@​bradyshutt</code></a>)</li>
</ul>
<h3>The 6.x line is now in security-only maintenance</h3>
<p>This release exists because the advisory above covers every published 6.x
version, and until now the only remediation on offer was an upgrade to 7.x.
<strong>6.1.5 is the patched version for the 6.x line.</strong></p>
<p>The line is kept alive for the installed base that cannot move to 7 yet, Tailwind</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/postcss/postcss-selector-parser/blob/main/CHANGELOG.md">postcss-selector-parser's changelog</a>.</em></p>
<blockquote>
<h2>7.1.7 - 2026-10-19</h2>
<ul>
<li>fix: <code>lossless: true</code> preserves trailing whitespace in a selector that ends empty, such as <code>:not(a, )</code>. Note that <code>:not( )</code> now yields a selector holding one empty string node rather than an empty selector (<a href="">#337</a> by <a href="https://github.com/theRizwan"><code>@​theRizwan</code></a>)</li>
<li>fix: consume the whitespace that terminates a hexadecimal escape, so <code>[x=&quot;\000061 b&quot;]</code> unescapes to <code>ab</code> (<a href="">#340</a> by <a href="https://github.com/jakezwang"><code>@​jakezwang</code></a>)</li>
<li>fix: set the parent on every node passed to <code>insertBefore</code> and <code>insertAfter</code>, not only the first (<a href="">#343</a> by <a href="https://github.com/feritcemkahraman"><code>@​feritcemkahraman</code></a>)</li>
<li>fix: assigning <code>combinator.value</code> clears the stale raw spelling instead of being ignored (<a href="">#342</a> by <a href="https://github.com/SAY-5"><code>@​SAY-5</code></a>)</li>
<li>fix: keep whitespace around the namespace separator in attribute selectors, so <code>[ foo | bar ]</code> round-trips (<a href="">#339</a> by <a href="https://github.com/dkryaklin"><code>@​dkryaklin</code></a>)</li>
</ul>
<h2>7.1.6 - 2026-09-03</h2>
<ul>
<li>fix: parse flat selectors in linear time, closing a CPU exhaustion vulnerability (<a href="https://github.com/advisories/GHSA-rj75-hqrm-r3gf">CVE-2026-104844</a> / GHSA-rj75-hqrm-r3gf, reported by Wayde Shi)</li>
</ul>
<h2>7.1.5 - 2026-08-07</h2>
<ul>
<li>fix: don't treat a non-prefix token before <code>|</code> as a namespace (<a href="">#324</a> by <a href="https://github.com/spokodev"><code>@​spokodev</code></a>)</li>
<li>fix: preserve whitespace before a <code>*</code> namespace in attribute selectors (<a href="">#325</a> by <a href="https://github.com/spokodev"><code>@​spokodev</code></a>)</li>
<li>fix: TypeError on unclosed <code>[</code>, <code>(</code> and trailing <code>|</code> (<a href="">#330</a> by <a href="https://github.com/theRizwan"><code>@​theRizwan</code></a>)</li>
</ul>
<h2>7.1.4 - 2026-06-11</h2>
<ul>
<li>fix: tolerate non-node children when serializing selectors</li>
</ul>
<h2>7.1.3 - 2026-06-11</h2>
<ul>
<li>Improve fix CVE-2026-9358 (NVD) / SNYK-JS-POSTCSSSELECTORPARSER-16873882 (clone/walk)</li>
</ul>
<h2>7.1.2 - 2026-06-09</h2>
<ul>
<li>Fix <a href="https://github.com/advisories/GHSA-w9m9-85wc-3x92">CVE-2026-9358</a> (NVD) / SNYK-JS-POSTCSSSELECTORPARSER-16873882 (<a href="">#316</a> by <a href="https://github.com/MoOx"><code>@​MoOx</code></a>)</li>
</ul>
<h2>7.1.1</h2>
<ul>
<li>perf: replace startsWith with strict equality (<a href="">#308</a>)</li>
<li>fix(types): add walkUniversal declaration (<a href="">#311</a>)</li>
</ul>
<h2>7.1.0</h2>
<ul>
<li>feat: insert(Before|After) support multiple new node</li>
</ul>
<h2>7.0.0</h2>
<ul>
<li>Feat: make insertions during iteration safe (major)</li>
</ul>
<h2>6.1.2</h2>
<ul>
<li>Fixed: erroneous trailing combinators in pseudos</li>
</ul>
<h2>6.1.1</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>154c2b0</code></a> 7.1.7</li>
<li><a href=""><code>e8dc65f</code></a> docs: add CVE-2026-104844 to the 7.1.6 changelog entry</li>
<li><a href=""><code>d5122b0</code></a> fix: keep whitespace around the namespace separator in attribute selectors (#...</li>
<li><a href=""><code>80ab254</code></a> fix: invalidate stale raw spelling on combinator value assignment (<a href="">#342</a>)</li>
<li><a href=""><code>ba353c7</code></a> fix: set parents for all variadic inserted nodes (<a href="">#343</a>)</li>
<li><a href=""><code>8b2d16d</code></a> Consume whitespace after hexadecimal CSS escapes (<a href="">#340</a>)</li>
<li><a href=""><code>8f10b8d</code></a> fix: lossless mode drops whitespace when a selector ends empty (<a href="">#337</a>)</li>
<li><a href=""><code>15c2b45</code></a> chore(deps-dev): bump source-map-js from 1.2.1 to 1.2.2 (<a href="">#347</a>)</li>
<li><a href=""><code>4eb3468</code></a> 7.1.6</li>
<li><a href=""><code>62b1917</code></a> fix: parse flat selectors in linear time, closing a CPU exhaustion vulnerability</li>
<li>Additional commits viewable in <a href="https://github.com/postcss/postcss-selector-parser/compare/v6.0.15...7.1.7">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~moox">moox</a>, a new releaser for postcss-selector-parser since your current version.</p>
</details>
<details>
<summary>Install script changes</summary>
<p>This version modifies <code>prepare</code> script that runs during installation. Review the package contents before updating.</p>
</details>
<br />

Updates `postcss-selector-parser` from 7.1.5 to 7.1.7
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/postcss/postcss-selector-parser/releases">postcss-selector-parser's releases</a>.</em></p>
<blockquote>
<h2>7.1.7</h2>
<ul>
<li>fix: <code>lossless: true</code> preserves trailing whitespace in a selector that ends empty, such as <code>:not(a, )</code>. Note that <code>:not( )</code> now yields a selector holding one empty string node rather than an empty selector (<a href="">#337</a> by <a href="https://github.com/theRizwan"><code>@​theRizwan</code></a>)</li>
<li>fix: consume the whitespace that terminates a hexadecimal escape, so <code>[x=&quot;\000061 b&quot;]</code> unescapes to <code>ab</code> (<a href="">#340</a> by <a href="https://github.com/jakezwang"><code>@​jakezwang</code></a>)</li>
<li>fix: set the parent on every node passed to <code>insertBefore</code> and <code>insertAfter</code>, not only the first (<a href="">#343</a> by <a href="https://github.com/feritcemkahraman"><code>@​feritcemkahraman</code></a>)</li>
<li>fix: assigning <code>combinator.value</code> clears the stale raw spelling instead of being ignored (<a href="">#342</a> by <a href="https://github.com/SAY-5"><code>@​SAY-5</code></a>)</li>
<li>fix: keep whitespace around the namespace separator in attribute selectors, so <code>[ foo | bar ]</code> round-trips (<a href="">#339</a> by <a href="https://github.com/dkryaklin"><code>@​dkryaklin</code></a>)</li>
</ul>
<h2>7.1.6</h2>
<ul>
<li>fix: parse flat selectors in linear time, closing a CPU exhaustion vulnerability (<a href="https://github.com/advisories/GHSA-rj75-hqrm-r3gf">GHSA-rj75-hqrm-r3gf</a>, reported by Wayde Shi)</li>
</ul>
<h2>7.1.5</h2>
<ul>
<li>fix: don't treat a non-prefix token before <code>|</code> as a namespace (<a href="">#324</a> by <a href="https://github.com/spokodev"><code>@​spokodev</code></a>)</li>
<li>fix: preserve whitespace before a <code>*</code> namespace in attribute selectors (<a href="">#325</a> by <a href="https://github.com/spokodev"><code>@​spokodev</code></a>)</li>
<li>fix: TypeError on unclosed <code>[</code>, <code>(</code> and trailing <code>|</code> (<a href="">#330</a> by <a href="https://github.com/theRizwan"><code>@​theRizwan</code></a>)</li>
</ul>
<h2>7.1.4</h2>
<ul>
<li>fix: tolerate non-node children when serializing selectors</li>
</ul>
<h2>7.1.3</h2>
<ul>
<li>Improve fix CVE-2026-9358 (NVD) / SNYK-JS-POSTCSSSELECTORPARSER-16873882 (clone/walk)</li>
</ul>
<h2>7.1.2</h2>
<ul>
<li>Fix <a href="https://github.com/advisories/GHSA-w9m9-85wc-3x92">CVE-2026-9358</a> (NVD) / SNYK-JS-POSTCSSSELECTORPARSER-16873882 (<a href="">#316</a> by <a href="https://github.com/MoOx"><code>@​MoOx</code></a>)</li>
</ul>
<h2>v7.1.1</h2>
<h1>7.1.1</h1>
<ul>
<li>perf: replace startsWith with strict equality (<a href="">#308</a>)</li>
<li>fix(types): add walkUniversal declaration (<a href="">#311</a>)</li>
</ul>
<h2>v7.1.0</h2>
<h1>7.1.0</h1>
<ul>
<li>feat: insert(Before|After) support multiple new node</li>
</ul>
<h2>v7.0.0</h2>
<h1>7.0.0</h1>
<ul>
<li>Feat: make insertions during iteration safe (major)</li>
</ul>
<h2>6.1.5</h2>
<ul>
<li>fix: parse flat selectors in linear time, closing a CPU exhaustion vulnerability (<a href="https://github.com/advisories/GHSA-rj75-hqrm-r3gf">CVE-2026-104844</a> / GHSA-rj75-hqrm-r3gf, reported by Wayde Shi), backported from 7.1.6 (<a href="">#346</a> by <a href="https://github.com/bradyshutt"><code>@​bradyshutt</code></a>)</li>
</ul>
<h3>The 6.x line is now in security-only maintenance</h3>
<p>This release exists because the advisory above covers every published 6.x
version, and until now the only remediation on offer was an upgrade to 7.x.
<strong>6.1.5 is the patched version for the 6.x line.</strong></p>
<p>The line is kept alive for the installed base that cannot move to 7 yet, Tailwind</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/postcss/postcss-selector-parser/blob/main/CHANGELOG.md">postcss-selector-parser's changelog</a>.</em></p>
<blockquote>
<h2>7.1.7 - 2026-10-19</h2>
<ul>
<li>fix: <code>lossless: true</code> preserves trailing whitespace in a selector that ends empty, such as <code>:not(a, )</code>. Note that <code>:not( )</code> now yields a selector holding one empty string node rather than an empty selector (<a href="">#337</a> by <a href="https://github.com/theRizwan"><code>@​theRizwan</code></a>)</li>
<li>fix: consume the whitespace that terminates a hexadecimal escape, so <code>[x=&quot;\000061 b&quot;]</code> unescapes to <code>ab</code> (<a href="">#340</a> by <a href="https://github.com/jakezwang"><code>@​jakezwang</code></a>)</li>
<li>fix: set the parent on every node passed to <code>insertBefore</code> and <code>insertAfter</code>, not only the first (<a href="">#343</a> by <a href="https://github.com/feritcemkahraman"><code>@​feritcemkahraman</code></a>)</li>
<li>fix: assigning <code>combinator.value</code> clears the stale raw spelling instead of being ignored (<a href="">#342</a> by <a href="https://github.com/SAY-5"><code>@​SAY-5</code></a>)</li>
<li>fix: keep whitespace around the namespace separator in attribute selectors, so <code>[ foo | bar ]</code> round-trips (<a href="">#339</a> by <a href="https://github.com/dkryaklin"><code>@​dkryaklin</code></a>)</li>
</ul>
<h2>7.1.6 - 2026-09-03</h2>
<ul>
<li>fix: parse flat selectors in linear time, closing a CPU exhaustion vulnerability (<a href="https://github.com/advisories/GHSA-rj75-hqrm-r3gf">CVE-2026-104844</a> / GHSA-rj75-hqrm-r3gf, reported by Wayde Shi)</li>
</ul>
<h2>7.1.5 - 2026-08-07</h2>
<ul>
<li>fix: don't treat a non-prefix token before <code>|</code> as a namespace (<a href="">#324</a> by <a href="https://github.com/spokodev"><code>@​spokodev</code></a>)</li>
<li>fix: preserve whitespace before a <code>*</code> namespace in attribute selectors (<a href="">#325</a> by <a href="https://github.com/spokodev"><code>@​spokodev</code></a>)</li>
<li>fix: TypeError on unclosed <code>[</code>, <code>(</code> and trailing <code>|</code> (<a href="">#330</a> by <a href="https://github.com/theRizwan"><code>@​theRizwan</code></a>)</li>
</ul>
<h2>7.1.4 - 2026-06-11</h2>
<ul>
<li>fix: tolerate non-node children when serializing selectors</li>
</ul>
<h2>7.1.3 - 2026-06-11</h2>
<ul>
<li>Improve fix CVE-2026-9358 (NVD) / SNYK-JS-POSTCSSSELECTORPARSER-16873882 (clone/walk)</li>
</ul>
<h2>7.1.2 - 2026-06-09</h2>
<ul>
<li>Fix <a href="https://github.com/advisories/GHSA-w9m9-85wc-3x92">CVE-2026-9358</a> (NVD) / SNYK-JS-POSTCSSSELECTORPARSER-16873882 (<a href="">#316</a> by <a href="https://github.com/MoOx"><code>@​MoOx</code></a>)</li>
</ul>
<h2>7.1.1</h2>
<ul>
<li>perf: replace startsWith with strict equality (<a href="">#308</a>)</li>
<li>fix(types): add walkUniversal declaration (<a href="">#311</a>)</li>
</ul>
<h2>7.1.0</h2>
<ul>
<li>feat: insert(Before|After) support multiple new node</li>
</ul>
<h2>7.0.0</h2>
<ul>
<li>Feat: make insertions during iteration safe (major)</li>
</ul>
<h2>6.1.2</h2>
<ul>
<li>Fixed: erroneous trailing combinators in pseudos</li>
</ul>
<h2>6.1.1</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>154c2b0</code></a> 7.1.7</li>
<li><a href=""><code>e8dc65f</code></a> docs: add CVE-2026-104844 to the 7.1.6 changelog entry</li>
<li><a href=""><code>d5122b0</code></a> fix: keep whitespace around the namespace separator in attribute selectors (#...</li>
<li><a href=""><code>80ab254</code></a> fix: invalidate stale raw spelling on combinator value assignment (<a href="">#342</a>)</li>
<li><a href=""><code>ba353c7</code></a> fix: set parents for all variadic inserted nodes (<a href="">#343</a>)</li>
<li><a href=""><code>8b2d16d</code></a> Consume whitespace after hexadecimal CSS escapes (<a href="">#340</a>)</li>
<li><a href=""><code>8f10b8d</code></a> fix: lossless mode drops whitespace when a selector ends empty (<a href="">#337</a>)</li>
<li><a href=""><code>15c2b45</code></a> chore(deps-dev): bump source-map-js from 1.2.1 to 1.2.2 (<a href="">#347</a>)</li>
<li><a href=""><code>4eb3468</code></a> 7.1.6</li>
<li><a href=""><code>62b1917</code></a> fix: parse flat selectors in linear time, closing a CPU exhaustion vulnerability</li>
<li>Additional commits viewable in <a href="https://github.com/postcss/postcss-selector-parser/compare/v6.0.15...7.1.7">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~moox">moox</a>, a new releaser for postcss-selector-parser since your current version.</p>
</details>
<details>
<summary>Install script changes</summary>
<p>This version modifies <code>prepare</code> script that runs during installation. Review the package contents before updating.</p>
</details>
<br />

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/ketcher/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09d9da19c905`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.