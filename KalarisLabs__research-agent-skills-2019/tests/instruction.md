# Issue

**Title:** deps: bump ruff from 0.17.1 to 0.17.4

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.17.1 to 0.17.4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.17.4</h2>
<h2>Release Notes</h2>
<p>Released on 2026-11-05.</p>
<h3>Preview features</h3>
<ul>
<li>[<code>flake8-logging-format</code>] Avoid behavior changes and syntax errors in fixes (<code>G004</code>) (<a href="">#27419</a>)</li>
<li>[<code>security</code>] Implement <code>tarfile-ignore-zeros-true</code> (<a href="">#28680</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Accept a bare raise before a semicolon (<a href="">#29761</a>)</li>
<li>Allow match identifiers after a semicolon (<a href="">#29760</a>)</li>
<li>Fix panic on BOM-prefixed files in diagnostic renderer (<a href="">#30017</a>)</li>
<li>[<code>flake8-simplify</code>] Report collapsible <code>elif</code> clauses after a multi-statement <code>if</code> branch (<code>SIM102</code>) (<a href="">#29814</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>Show more nonprinting characters in diagnostic fix diffs (<a href="">#30062</a>)</li>
</ul>
<h3>Performance</h3>
<ul>
<li>Coalesce source slices when formatting attributes (<a href="">#29841</a>)</li>
<li>Collect return statements with a statement-only visitor (<a href="">#29911</a>)</li>
<li>[<code>pyflakes</code>] Defer value comparisons for repeated dictionary keys (<code>F601</code>, <code>F602</code>) (<a href="">#29739</a>)</li>
<li>Format node fields directly when comment handling is unnecessary (<a href="">#29853</a>)</li>
<li>Reduce formatter source-slice overhead (<a href="">#29855</a>)</li>
<li>Reuse a callee's qualified name across lint rules (<a href="">#29916</a>)</li>
<li>Skip invalid string character checks when the source contains none (<a href="">#29883</a>)</li>
<li>Use a Bloom filter for formatter comment lookups (<a href="">#29852</a>)</li>
<li>Use a concrete buffer for ordinary writes (<a href="">#29819</a>)</li>
</ul>
<h3>CLI</h3>
<ul>
<li>Give <code>NO_COLOR</code> precedence in Ruff and ty diagnostics (<a href="">#29898</a>)</li>
<li>Honor <code>CLICOLOR=0</code> in Ruff and ty diagnostics (<a href="">#29910</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Correct the documented <code>version</code> and <code>src</code> defaults for <code>ruff-action</code> (<a href="">#29880</a>)</li>
<li>[<code>flake8-bugbear</code>] Make <code>B014</code> example error out-of-the-box (<a href="">#29941</a>)</li>
<li>[<code>flake8-no-pep420</code>] Document preview behavior (<code>INP001</code>) (<a href="">#29764</a>)</li>
<li>[<code>isort</code>] Expand <code>I001</code> documentation (<a href="">#29843</a>)</li>
</ul>
<h3>Other changes</h3>
<ul>
<li>[syntax-errors] Extend <code>__debug__</code> write check to attribute targets (<a href="">#27908</a>)</li>
</ul>
<h3>Contributors</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/blob/main/CHANGELOG.md">ruff's changelog</a>.</em></p>
<blockquote>
<h2>0.17.4</h2>
<p>Released on 2026-11-05.</p>
<h3>Preview features</h3>
<ul>
<li>[<code>flake8-logging-format</code>] Avoid behavior changes and syntax errors in fixes (<code>G004</code>) (<a href="">#27419</a>)</li>
<li>[<code>security</code>] Implement <code>tarfile-ignore-zeros-true</code> (<a href="">#28680</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Accept a bare raise before a semicolon (<a href="">#29761</a>)</li>
<li>Allow match identifiers after a semicolon (<a href="">#29760</a>)</li>
<li>Fix panic on BOM-prefixed files in diagnostic renderer (<a href="">#30017</a>)</li>
<li>[<code>flake8-simplify</code>] Report collapsible <code>elif</code> clauses after a multi-statement <code>if</code> branch (<code>SIM102</code>) (<a href="">#29814</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>Show more nonprinting characters in diagnostic fix diffs (<a href="">#30062</a>)</li>
</ul>
<h3>Performance</h3>
<ul>
<li>Coalesce source slices when formatting attributes (<a href="">#29841</a>)</li>
<li>Collect return statements with a statement-only visitor (<a href="">#29911</a>)</li>
<li>[<code>pyflakes</code>] Defer value comparisons for repeated dictionary keys (<code>F601</code>, <code>F602</code>) (<a href="">#29739</a>)</li>
<li>Format node fields directly when comment handling is unnecessary (<a href="">#29853</a>)</li>
<li>Reduce formatter source-slice overhead (<a href="">#29855</a>)</li>
<li>Reuse a callee's qualified name across lint rules (<a href="">#29916</a>)</li>
<li>Skip invalid string character checks when the source contains none (<a href="">#29883</a>)</li>
<li>Use a Bloom filter for formatter comment lookups (<a href="">#29852</a>)</li>
<li>Use a concrete buffer for ordinary writes (<a href="">#29819</a>)</li>
</ul>
<h3>CLI</h3>
<ul>
<li>Give <code>NO_COLOR</code> precedence in Ruff and ty diagnostics (<a href="">#29898</a>)</li>
<li>Honor <code>CLICOLOR=0</code> in Ruff and ty diagnostics (<a href="">#29910</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Correct the documented <code>version</code> and <code>src</code> defaults for <code>ruff-action</code> (<a href="">#29880</a>)</li>
<li>[<code>flake8-bugbear</code>] Make <code>B014</code> example error out-of-the-box (<a href="">#29941</a>)</li>
<li>[<code>flake8-no-pep420</code>] Document preview behavior (<code>INP001</code>) (<a href="">#29764</a>)</li>
<li>[<code>isort</code>] Expand <code>I001</code> documentation (<a href="">#29843</a>)</li>
</ul>
<h3>Other changes</h3>
<ul>
<li>[syntax-errors] Extend <code>__debug__</code> write check to attribute targets (<a href="">#27908</a>)</li>
</ul>
<h3>Contributors</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>05cdc36</code></a> Bump version to 0.17.4 (<a href="">#30073</a>)</li>
<li><a href=""><code>c6b17c2</code></a> [ty] Freshen method typevars before owner specialization (<a href="">#29543</a>)</li>
<li><a href=""><code>4b0b407</code></a> [ty] Preserve unions inferred during fixpoint iteration (<a href="">#29927</a>)</li>
<li><a href=""><code>1dd3e9e</code></a> Show more nonprinting characters in diagnostic fix diffs (<a href="">#30062</a>)</li>
<li><a href=""><code>32be8e7</code></a> [ty] Skip fixpoint iteration for simple generic calls (<a href="">#30054</a>)</li>
<li><a href=""><code>926ccc8</code></a> [ty] Handle output errors when generating shell completions (<a href="">#29997</a>)</li>
<li><a href=""><code>c86652a</code></a> [ty] Skip active Conda and Pixi environments during discovery if the environm...</li>
<li><a href=""><code>c9150f0</code></a> Add project walltime benchmarks for Ruff (<a href="">#30061</a>)</li>
<li><a href=""><code>64989ec</code></a> [ty] Report invalid module globs once per override pattern (<a href="">#30031</a>)</li>
<li><a href=""><code>367a563</code></a> [ty] Fix conditional type and tuple annotations (<a href="">#29987</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.17.1...0.17.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=uv&previous-version=0.17.1&new-version=0.17.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

</details>

<!-- codesmith:footer -->
---
<a href="https://backend.blacksmith.sh/track/enable-autofix?expires=1797090355&installation_model_id=444357&pr_number=2019&ref=codesmith_pr_footer&repository=KalarisLabs%2Fresearch-agent-skills&return_to=https%3A%2F%2Fgithub.com%2FKalarisLabs%2Fresearch-agent-skills%2Fpull%2F2019&signature=300fa13d2afcfbdac9cfe527c2ba3a3c8786ef33b2e3f5110b868c3bcacb601c"><picture><source media="(prefers-color-scheme: dark)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-light.svg"><img alt="Autofix with [code]smith" src="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark-3x.png" width="190" height="28"></picture></a>
<sup><a href="https://app.blacksmith.sh/KalarisLabs/codesmith/research-agent-skills/pr/2019?autoLogin=true&ref=codesmith_pr_footer">Open in [code]smith</a> · Need help on this PR? Tag <code>@codesmith-bot</code> with what you need.</sup>

<!-- codesmith:autofix:disabled -->
<!-- /codesmith:footer -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d98cda600723`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.