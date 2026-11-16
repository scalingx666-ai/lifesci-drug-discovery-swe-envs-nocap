# Issue

**Title:** Bump @typescript-eslint/eslint-plugin from 5.45.1 to 5.52.0

## Description

Bumps [@typescript-eslint/eslint-plugin](https://github.com/typescript-eslint/typescript-eslint/tree/HEAD/packages/eslint-plugin) from 5.45.1 to 5.52.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/typescript-eslint/typescript-eslint/releases"><code>@​typescript-eslint/eslint-plugin</code>'s releases</a>.</em></p>
<blockquote>
<h2>v5.52.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.51.0...v5.52.0">5.52.0</a> (2023-02-13)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [no-import-type-side-effects] correctly ignore zero-specifier imports (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6444">#6444</a>) (<a href="">d5a6688</a>)</li>
<li><strong>eslint-plugin:</strong> [no-unnecessary-condition] account for optional chaining on potentially void values (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6432">#6432</a>) (<a href="">e1d9c67</a>), closes <a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5255">#5255</a></li>
<li><strong>eslint-plugin:</strong> [no-unnecessary-condition] fix false positive when checking indexed access types (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6452">#6452</a>) (<a href="">d569924</a>)</li>
<li><strong>eslint-plugin:</strong> fix key-spacing when type starts on next line (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6412">#6412</a>) (<a href="">3eb2eed</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [block-spacing] extending base rule for TS related blocks (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6195">#6195</a>) (<a href="">b2db3f5</a>)</li>
<li><strong>eslint-plugin:</strong> [explicit-function-return-type] add allowFunctionsWithoutTypeParameters option (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6105">#6105</a>) (<a href="">113640e</a>)</li>
<li><strong>eslint-plugin:</strong> [explicit-function-return-type] add allowIIFEs option (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6237">#6237</a>) (<a href="">a1b3f7b</a>)</li>
<li><strong>typescript-estree:</strong> add <code>.kind</code> to <code>TSModuleDeclaration</code> (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6443">#6443</a>) (<a href="">2f948df</a>)</li>
<li><strong>typescript-estree:</strong> allow specifying project: true (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6084">#6084</a>) (<a href="">dcd05f0</a>)</li>
</ul>
<h2>v5.51.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.50.0...v5.51.0">5.51.0</a> (2023-02-06)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [sort-type-constituents] fixed behavior change (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6384">#6384</a>) (<a href="">5bf7f7f</a>), closes <a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6339">#6339</a></li>
<li><strong>eslint-plugin:</strong> do not use .at(), Node 14 does not support it (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6402">#6402</a>) (<a href="">077ed1b</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [naming-convention] improve performance by removing unnecessary selectors (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6376">#6376</a>) (<a href="">3647a1c</a>)</li>
<li><strong>eslint-plugin:</strong> [no-floating-promises] error on logical expression (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6356">#6356</a>) (<a href="">f330e06</a>)</li>
<li><strong>eslint-plugin:</strong> [no-import-type-side-effects] add rule to warn against runtime side effects with <code>verbatimModuleSyntax</code> (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6394">#6394</a>) (<a href="">b14d3be</a>)</li>
<li><strong>eslint-plugin:</strong> [strict-boolean-expressions] add allow nullable enum to strict boolean expressions (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6096">#6096</a>) (<a href="">d4747cd</a>)</li>
<li><strong>typescript-estree:</strong> cache project glob resolution (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6367">#6367</a>) (<a href="">afae837</a>)</li>
</ul>
<h2>v5.50.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.49.0...v5.50.0">5.50.0</a> (2023-01-31)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>ast-spec:</strong> a JSXEmptyExpression is not a possible JSXExpression (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6321">#6321</a>) (<a href="">4b27777</a>)</li>
<li><strong>eslint-plugin:</strong> [ban-ts-comment] counts graphemes instead of <code>String.prototype.length</code> (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5704">#5704</a>) (<a href="">09d57ce</a>)</li>
<li><strong>eslint-plugin:</strong> [prefer-optional-chain] fix <code>ThisExpression</code> and <code>PrivateIdentifier</code> errors (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6028">#6028</a>) (<a href="">85e783c</a>)</li>
<li><strong>eslint-plugin:</strong> [prefer-optional-chain] fixer produces wrong logic (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5919">#5919</a>) (<a href="">b0f6c8e</a>), closes <a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/1438">#1438</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/CHANGELOG.md"><code>@​typescript-eslint/eslint-plugin</code>'s changelog</a>.</em></p>
<blockquote>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.51.0...v5.52.0">5.52.0</a> (2023-02-13)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [no-import-type-side-effects] correctly ignore zero-specifier imports (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6444">#6444</a>) (<a href="">d5a6688</a>)</li>
<li><strong>eslint-plugin:</strong> [no-unnecessary-condition] account for optional chaining on potentially void values (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6432">#6432</a>) (<a href="">e1d9c67</a>), closes <a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5255">#5255</a></li>
<li><strong>eslint-plugin:</strong> [no-unnecessary-condition] fix false positive when checking indexed access types (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6452">#6452</a>) (<a href="">d569924</a>)</li>
<li><strong>eslint-plugin:</strong> fix key-spacing when type starts on next line (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6412">#6412</a>) (<a href="">3eb2eed</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [block-spacing] extending base rule for TS related blocks (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6195">#6195</a>) (<a href="">b2db3f5</a>)</li>
<li><strong>eslint-plugin:</strong> [explicit-function-return-type] add allowFunctionsWithoutTypeParameters option (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6105">#6105</a>) (<a href="">113640e</a>)</li>
<li><strong>eslint-plugin:</strong> [explicit-function-return-type] add allowIIFEs option (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6237">#6237</a>) (<a href="">a1b3f7b</a>)</li>
</ul>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.50.0...v5.51.0">5.51.0</a> (2023-02-06)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [sort-type-constituents] fixed behavior change (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6384">#6384</a>) (<a href="">5bf7f7f</a>), closes <a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6339">#6339</a></li>
<li><strong>eslint-plugin:</strong> do not use .at(), Node 14 does not support it (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6402">#6402</a>) (<a href="">077ed1b</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [naming-convention] improve performance by removing unnecessary selectors (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6376">#6376</a>) (<a href="">3647a1c</a>)</li>
<li><strong>eslint-plugin:</strong> [no-floating-promises] error on logical expression (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6356">#6356</a>) (<a href="">f330e06</a>)</li>
<li><strong>eslint-plugin:</strong> [no-import-type-side-effects] add rule to warn against runtime side effects with <code>verbatimModuleSyntax</code> (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6394">#6394</a>) (<a href="">b14d3be</a>)</li>
<li><strong>eslint-plugin:</strong> [strict-boolean-expressions] add allow nullable enum to strict boolean expressions (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6096">#6096</a>) (<a href="">d4747cd</a>)</li>
</ul>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.49.0...v5.50.0">5.50.0</a> (2023-01-31)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [ban-ts-comment] counts graphemes instead of <code>String.prototype.length</code> (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5704">#5704</a>) (<a href="">09d57ce</a>)</li>
<li><strong>eslint-plugin:</strong> [prefer-optional-chain] fix <code>ThisExpression</code> and <code>PrivateIdentifier</code> errors (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6028">#6028</a>) (<a href="">85e783c</a>)</li>
<li><strong>eslint-plugin:</strong> [prefer-optional-chain] fixer produces wrong logic (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5919">#5919</a>) (<a href="">b0f6c8e</a>), closes <a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/1438">#1438</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c46c793</code></a> chore: publish v5.52.0</li>
<li><a href=""><code>b2db3f5</code></a> feat(eslint-plugin): [block-spacing] extending base rule for TS related block...</li>
<li><a href=""><code>d569924</code></a> fix(eslint-plugin): [no-unnecessary-condition] fix false positive when checki...</li>
<li><a href=""><code>a1b3f7b</code></a> feat(eslint-plugin): [explicit-function-return-type] add allowIIFEs option (#...</li>
<li><a href=""><code>e1d9c67</code></a> fix(eslint-plugin): [no-unnecessary-condition] account for optional chaining ...</li>
<li><a href=""><code>3eb2eed</code></a> fix(eslint-plugin): fix key-spacing when type starts on next line (<a href="">#6412</a>)</li>
<li><a href=""><code>113640e</code></a> feat(eslint-plugin): [explicit-function-return-type] add allowFunctionsWithou...</li>
<li><a href=""><code>d5a6688</code></a> fix(eslint-plugin): [no-import-type-side-effects] correctly ignore zero-speci...</li>
<li><a href=""><code>a9cb860</code></a> chore: publish v5.51.0</li>
<li><a href=""><code>d4747cd</code></a> feat(eslint-plugin): [strict-boolean-expressions] add allow nullable enum to ...</li>
<li>Additional commits viewable in <a href="https://github.com/typescript-eslint/typescript-eslint/commits/v5.52.0/packages/eslint-plugin">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@typescript-eslint/eslint-plugin&package-manager=npm_and_yarn&previous-version=5.45.1&new-version=5.52.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbe2c04b17dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.