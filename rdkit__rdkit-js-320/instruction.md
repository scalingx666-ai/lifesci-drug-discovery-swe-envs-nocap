# Issue

**Title:** Bump @typescript-eslint/eslint-plugin from 5.54.0 to 5.57.0

## Description

Bumps [@typescript-eslint/eslint-plugin](https://github.com/typescript-eslint/typescript-eslint/tree/HEAD/packages/eslint-plugin) from 5.54.0 to 5.57.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/typescript-eslint/typescript-eslint/releases"><code>@​typescript-eslint/eslint-plugin</code>'s releases</a>.</em></p>
<blockquote>
<h2>v5.57.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.56.0...v5.57.0">5.57.0</a> (2023-03-27)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [no-unnecessary-boolean-literal-compare] simplify fixer and add support for double negation (<a href="">#6620</a>) (<a href="">81c8519</a>)</li>
<li><strong>eslint-plugin:</strong> correct crashes with getTypeArguments for ts &lt; 3.7 (<a href="">#6767</a>) (<a href="">59eab58</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [consistent-type-assertions] add suggestions for objectLiteralTypeAssertions (<a href="">#6642</a>) (<a href="">720e811</a>)</li>
<li><strong>eslint-plugin:</strong> [consistent-type-assertions] autofix angle bracket assertions to as (<a href="">#6641</a>) (<a href="">ad8ea64</a>)</li>
<li><strong>eslint-plugin:</strong> add <code>no-duplicate-type-constituents</code> rule (<a href="">#5728</a>) (<a href="">bc31078</a>)</li>
</ul>
<h2>v5.56.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.55.0...v5.56.0">5.56.0</a> (2023-03-20)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [member-ordering] check order when optionalityOrder is present with no optional members (<a href="">#6619</a>) (<a href="">6aff431</a>)</li>
<li><strong>eslint-plugin:</strong> [no-misused-promises] avoid unnecessary calls to getContextualType (<a href="">#6193</a>) (<a href="">745cfe4</a>)</li>
<li><strong>eslint-plugin:</strong> [no-misused-promises] fix incorrect detection of void functions in JSX attributes (<a href="">#6638</a>) (<a href="">9e41cee</a>)</li>
<li><strong>eslint-plugin:</strong> [strict-boolean-expression] support falsy and truthy literals simultaneously (<a href="">#6672</a>) (<a href="">62ef487</a>)</li>
<li><strong>eslint-plugin:</strong> [strict-boolean-expressions] handle truthy enums (<a href="">#6618</a>) (<a href="">0d0639f</a>)</li>
<li><strong>eslint-plugin:</strong> [naming-convention] add TSPropertySignature with TSFunctionType annotation to <code>typeMethod</code> selector (<a href="">#6645</a>) (<a href="">3fc5c63</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [restrict-template-expressions] add option <code>allowNever</code> (<a href="">#6554</a>) (<a href="">423f164</a>)</li>
</ul>
<h2>v5.55.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.54.1...v5.55.0">5.55.0</a> (2023-03-13)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [no-confusing-void-expression] check sequence expressions for void is in last position (<a href="">#6597</a>) (<a href="">d73d7d3</a>)</li>
<li><strong>eslint-plugin:</strong> [no-unnecessary-boolean-literal-compare] fixer should handle parentheses (<a href="">#6569</a>) (<a href="">2d8c196</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [lines-around-comment] add extension rule (<a href="">#5327</a>) (<a href="">d55211c</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/CHANGELOG.md"><code>@​typescript-eslint/eslint-plugin</code>'s changelog</a>.</em></p>
<blockquote>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.56.0...v5.57.0">5.57.0</a> (2023-03-27)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [no-unnecessary-boolean-literal-compare] simplify fixer and add support for double negation (<a href="">#6620</a>) (<a href="">81c8519</a>)</li>
<li><strong>eslint-plugin:</strong> correct crashes with getTypeArguments for ts &lt; 3.7 (<a href="">#6767</a>) (<a href="">59eab58</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [consistent-type-assertions] add suggestions for objectLiteralTypeAssertions (<a href="">#6642</a>) (<a href="">720e811</a>)</li>
<li><strong>eslint-plugin:</strong> [consistent-type-assertions] autofix angle bracket assertions to as (<a href="">#6641</a>) (<a href="">ad8ea64</a>)</li>
<li><strong>eslint-plugin:</strong> add <code>no-duplicate-type-constituents</code> rule (<a href="">#5728</a>) (<a href="">bc31078</a>)</li>
</ul>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.55.0...v5.56.0">5.56.0</a> (2023-03-20)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [member-ordering] check order when optionalityOrder is present with no optional members (<a href="">#6619</a>) (<a href="">6aff431</a>)</li>
<li><strong>eslint-plugin:</strong> [no-misused-promises] avoid unnecessary calls to getContextualType (<a href="">#6193</a>) (<a href="">745cfe4</a>)</li>
<li><strong>eslint-plugin:</strong> [no-misused-promises] fix incorrect detection of void functions in JSX attributes (<a href="">#6638</a>) (<a href="">9e41cee</a>)</li>
<li><strong>eslint-plugin:</strong> [strict-boolean-expression] support falsy and truthy literals simultaneously (<a href="">#6672</a>) (<a href="">62ef487</a>)</li>
<li><strong>eslint-plugin:</strong> [strict-boolean-expressions] handle truthy enums (<a href="">#6618</a>) (<a href="">0d0639f</a>)</li>
<li><strong>eslint-plugin:</strong> add TSPropertySignature with TSFunctionType annotation to typeMethod selector (<a href="">#6645</a>) (<a href="">3fc5c63</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> add allowNever support to restrict-template-expressions (<a href="">#6554</a>) (<a href="">423f164</a>)</li>
</ul>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.54.1...v5.55.0">5.55.0</a> (2023-03-13)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [no-confusing-void-expression] check sequence expressions for void is in last position (<a href="">#6597</a>) (<a href="">d73d7d3</a>)</li>
<li><strong>eslint-plugin:</strong> [no-unnecessary-boolean-literal-compare] fixer should handle parentheses (<a href="">#6569</a>) (<a href="">2d8c196</a>)</li>
</ul>
<h3>Features</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>69f827c</code></a> chore: publish v5.57.0</li>
<li><a href=""><code>59eab58</code></a> fix(eslint-plugin): correct crashes with getTypeArguments for ts &lt; 3.7 (<a href="">#6767</a>)</li>
<li><a href=""><code>f5631e9</code></a> docs(eslint-plugin): [lines-around-comment] fix typo (<a href="">#6776</a>)</li>
<li><a href=""><code>bc31078</code></a> feat(eslint-plugin): add <code>no-duplicate-type-constituents</code> rule (<a href="">#5728</a>)</li>
<li><a href=""><code>d8e563b</code></a> chore(website): preserve RulesTable filters state in searchParams (<a href="">#6568</a>)</li>
<li><a href=""><code>720e811</code></a> feat(eslint-plugin): [consistent-type-assertions] add suggestions for objectL...</li>
<li><a href=""><code>ad8ea64</code></a> feat(eslint-plugin): [consistent-type-assertions] autofix angle bracket asser...</li>
<li><a href=""><code>81c8519</code></a> fix(eslint-plugin): [no-unnecessary-boolean-literal-compare] simplify fixer a...</li>
<li><a href=""><code>75eb5b5</code></a> docs(eslint-plugin): [lines-around-comment option] cleaned up docs (<a href="">#6674</a>)</li>
<li><a href=""><code>efdf2cf</code></a> chore: publish v5.56.0</li>
<li>Additional commits viewable in <a href="https://github.com/typescript-eslint/typescript-eslint/commits/v5.57.0/packages/eslint-plugin">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@typescript-eslint/eslint-plugin&package-manager=npm_and_yarn&previous-version=5.54.0&new-version=5.57.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `575ca10b6b01`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.