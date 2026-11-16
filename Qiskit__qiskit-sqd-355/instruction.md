# Issue

**Title:** Bump pylint from 4.0.6 to 4.0.8

## Description

Bumps [pylint](https://github.com/pylint-dev/pylint) from 4.0.6 to 4.0.8.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pylint-dev/pylint/releases">pylint's releases</a>.</em></p>
<blockquote>
<h2>v4.0.8</h2>
<h2>What's new in Pylint 4.0.8?</h2>
<p>Release date: 2026-08-29</p>
<h2>False Positives Fixed</h2>
<ul>
<li>
<p>Fix a false positive for :ref:<code>unspecified-encoding</code> when an <code>open</code> call uses a mode
argument that cannot be inferred.</p>
<p>Closes <a href="">#10201</a></p>
</li>
<li>
<p>Fix a false positive for <code>invalid-name</code> (C0103) on names assigned in an
<code>if __name__ == &quot;__main__&quot;:</code> block. Such a block reads like a script body, so
a name there is now accepted if it matches either the constant or the variable
naming style.</p>
<p>Closes <a href="">#10766</a></p>
</li>
<li>
<p>Fix false positives for :ref:<code>invalid-str-returned</code>, :ref:<code>invalid-repr-returned</code>,
:ref:<code>invalid-format-returned</code>, :ref:<code>invalid-bytes-returned</code>, :ref:<code>invalid-hash-returned</code>,
:ref:<code>invalid-index-returned</code>, :ref:<code>invalid-length-returned</code>,
:ref:<code>invalid-length-hint-returned</code>, :ref:<code>invalid-getnewargs-returned</code> and
:ref:<code>invalid-getnewargs-ex-returned</code> when the returned value is an instance of a
subclass of the expected builtin type, such as <code>self</code> in a <code>str</code> subclass or a
<code>namedtuple</code>.</p>
<p>Closes <a href="">#11306</a></p>
</li>
<li>
<p>Fix false positives for :ref:<code>bad-string-format-type</code> when the argument is an
instance of a subclass of <code>int</code>, <code>float</code> or <code>str</code>, such as <code>bool</code> or an
<code>IntEnum</code> member formatted with <code>%d</code>.</p>
<p>Closes <a href="">#11315</a></p>
</li>
</ul>
<h2>False Negatives Fixed</h2>
<ul>
<li>
<p><code>redundant-unittest-assert</code> now also flags <code>assertEqual</code> and <code>assertNotEqual</code>
when both compared values are constants, e.g. <code>self.assertEqual(5, 5)</code>.</p>
<p>Closes <a href="">#11321</a></p>
</li>
</ul>
<p>Other Bug Fixes</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ecb84ba</code></a> Bump pylint to 4.0.8, update changelog (<a href="">#11355</a>)</li>
<li><a href=""><code>989e9c5</code></a> [Backport maintenance/4.0.x] Support isort 9 (<a href="">#11354</a>)</li>
<li><a href=""><code>8c1ee95</code></a> Flag assertEqual and assertNotEqual between two constants in W1503</li>
<li><a href=""><code>eadefe3</code></a> Fix false positive bad-string-format-type for subclasses of builtin types</li>
<li><a href=""><code>db00e3b</code></a> [Backport maintenance/4.0.x] fix(docparams): guard decorated_with_property ag...</li>
<li><a href=""><code>7909c17</code></a> Accept subclass instances in the invalid-*-returned checks</li>
<li><a href=""><code>d19640d</code></a> [Backport maintenance/4.0.x] Fix <code>invalid-name</code> false positive in `if _<em>name</em>...</li>
<li><a href=""><code>94e5704</code></a> Skip unspecified-encoding for unknown open modes (<a href="">#11163</a>)</li>
<li><a href=""><code>d59b329</code></a> fix(refactoring): handle non-AssignName targets in use-yield-from (<a href="">#11286</a>) (#...</li>
<li><a href=""><code>eea0569</code></a> [Backport maintenance/4.0.x] Fix crash in docparams on raising a non-exceptio...</li>
<li>Additional commits viewable in <a href="https://github.com/pylint-dev/pylint/compare/v4.0.6...v4.0.8">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pylint&package-manager=pip&previous-version=4.0.6&new-version=4.0.8)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8a7a40bf701`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.