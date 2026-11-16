# Issue

**Title:** Bump @typescript-eslint/parser from 5.37.0 to 5.43.0

## Description

Bumps [@typescript-eslint/parser](https://github.com/typescript-eslint/typescript-eslint/tree/HEAD/packages/parser) from 5.37.0 to 5.43.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/typescript-eslint/typescript-eslint/releases"><code>@​typescript-eslint/parser</code>'s releases</a>.</em></p>
<blockquote>
<h2>v5.43.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.42.1...v5.43.0">5.43.0</a> (2022-11-14)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [no-shadow] handle false positives on generics and parameters (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5902">#5902</a>) (<a href="">769e8c8</a>)</li>
<li><strong>eslint-plugin:</strong> [promise-function-async] handle keyword token (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5907">#5907</a>) (<a href="">f25a94f</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [consistent-type-imports] support fixing to inline types (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5050">#5050</a>) (<a href="">75dcdf1</a>)</li>
<li><strong>eslint-plugin:</strong> [naming-convention] add support for &quot;override&quot; and &quot;async&quot; modifiers (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5310">#5310</a>) (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5610">#5610</a>) (<a href="">c759da1</a>)</li>
<li><strong>eslint-plugin:</strong> [prefer-optional-chain] support suggesting <code>!foo || !foo.bar</code> as a valid match for the rule (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5594">#5594</a>) (<a href="">923d486</a>)</li>
</ul>
<h2>v5.42.1</h2>
<h2><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.42.0...v5.42.1">5.42.1</a> (2022-11-07)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>ast-spec:</strong> correct misnamed ExportNamedDeclaration AST type (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5913">#5913</a>) (<a href="">e88f4fa</a>)</li>
<li><strong>eslint-plugin:</strong> isTypeReadonly stack overflow (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5875">#5875</a>) (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5876">#5876</a>) (<a href="">2d9a33c</a>)</li>
</ul>
<h2>v5.42.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.41.0...v5.42.0">5.42.0</a> (2022-10-31)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>ast-spec:</strong> add TSQualifiedName to TypeNode union (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5906">#5906</a>) (<a href="">5c316c1</a>)</li>
<li><strong>eslint-plugin:</strong> [no-extra-parens] handle type assertion in extends clause (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5901">#5901</a>) (<a href="">8ed7219</a>)</li>
<li><strong>typescript-estree:</strong> don't allow single-run unless we're in type-aware linting mode (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5893">#5893</a>) (<a href="">891b087</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [member-ordering] add natural sort order (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5662">#5662</a>) (<a href="">1eaae09</a>)</li>
<li><strong>eslint-plugin:</strong> [no-invalid-void-type] better report message for void used as a constituent inside a function return type  (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5274">#5274</a>) (<a href="">d806bda</a>)</li>
<li><strong>typescript-estree:</strong> clarify docs and error for program project without matching TSConfig (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5762">#5762</a>) (<a href="">67744db</a>)</li>
<li><strong>utils:</strong> add <code>RuleTester</code> API for top-level dependency constraints (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5896">#5896</a>) (<a href="">0520d53</a>)</li>
</ul>
<h2>v5.41.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.40.1...v5.41.0">5.41.0</a> (2022-10-24)</h1>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/parser/CHANGELOG.md"><code>@​typescript-eslint/parser</code>'s changelog</a>.</em></p>
<blockquote>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.42.1...v5.43.0">5.43.0</a> (2022-11-14)</h1>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
<h2><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.42.0...v5.42.1">5.42.1</a> (2022-11-07)</h2>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.41.0...v5.42.0">5.42.0</a> (2022-10-31)</h1>
<h3>Features</h3>
<ul>
<li><strong>scope-manager:</strong> ignore ECMA version (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5881">#5881</a>) (<a href="">3b8d449</a>)</li>
</ul>
<h3>Reverts</h3>
<ul>
<li>Revert &quot;feat(scope-manager): ignore ECMA version&quot; (<a href="">#5888</a>) (<a href="">2ee81df</a>), closes <a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5888">#5888</a> <a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5881">#5881</a></li>
</ul>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.40.1...v5.41.0">5.41.0</a> (2022-10-24)</h1>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
<h2><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.40.0...v5.40.1">5.40.1</a> (2022-10-17)</h2>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.39.0...v5.40.0">5.40.0</a> (2022-10-10)</h1>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.38.1...v5.39.0">5.39.0</a> (2022-10-03)</h1>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
<h2><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.38.0...v5.38.1">5.38.1</a> (2022-09-26)</h2>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.37.0...v5.38.0">5.38.0</a> (2022-09-19)</h1>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8af1b4d</code></a> chore: publish v5.43.0</li>
<li><a href=""><code>b8b24c2</code></a> chore: publish v5.42.1</li>
<li><a href=""><code>1e5e9ea</code></a> chore: publish v5.42.0</li>
<li><a href=""><code>2ee81df</code></a> Revert &quot;feat(scope-manager): ignore ECMA version&quot; (<a href="">#5888</a>)</li>
<li><a href=""><code>3b8d449</code></a> feat(scope-manager): ignore ECMA version (<a href="">#5881</a>)</li>
<li><a href=""><code>fcf3f9d</code></a> docs: Mention wide globs performance implications in monorepos docs and parse...</li>
<li><a href=""><code>9eea5f4</code></a> chore: publish v5.41.0</li>
<li><a href=""><code>0be356b</code></a> chore: publish v5.40.1</li>
<li><a href=""><code>56f89d6</code></a> chore: nx migrate latest (14.8.4) (<a href="">#5798</a>)</li>
<li><a href=""><code>6ac0aa7</code></a> chore: publish v5.40.0</li>
<li>Additional commits viewable in <a href="https://github.com/typescript-eslint/typescript-eslint/commits/v5.43.0/packages/parser">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@typescript-eslint/parser&package-manager=npm_and_yarn&previous-version=5.37.0&new-version=5.43.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9cf03c14b28e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.