# Issue

**Title:** Bump pylint from 4.0.8 to 4.0.9

## Description

Bumps [pylint](https://github.com/pylint-dev/pylint) from 4.0.8 to 4.0.9.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pylint-dev/pylint/releases">pylint's releases</a>.</em></p>
<blockquote>
<h2>v4.0.9</h2>
<h2>What's new in Pylint 4.0.9?</h2>
<p>Release date: 2026-09-23</p>
<h2>Security Fixes</h2>
<ul>
<li>Someone without access to the configuration or linted code, but with access
to the cache directory (predictable <code>PYLINT_HOME</code> on a multi-user host) can no
longer write a crafted pickle that will runs arbitrary code when pylint access its
stat cache. The result cache is now stored as JSON instead of pickle,
preventing code-execution. The workaround is upgrading or not pointing <code>PYLINT_HOME</code>
to an untrusted, shared, or group-writable directory. The default value, <code>~/.cache/pylint</code>,
is writable only by the user running pylint. (CVE with the same information pending)</li>
</ul>
<h2>False Positives Fixed</h2>
<ul>
<li>
<p>Fixed a false positive for <code>no-self-use</code> on a method that only uses
<code>self</code> before a locally defined class (or other nested method), because
the checker's could-be-a-function tracking state was not restored after
visiting the nested method.</p>
<p>Closes <a href="">#3705</a></p>
</li>
<li>
<p>Fix a false positive for :ref:<code>not-callable</code> when calling functions constructed with
<code>types.FunctionType</code> or <code>types.LambdaType</code>.</p>
<p>Closes <a href="">#7500</a></p>
</li>
<li>
<p>Fix a false positive for <code>unnecessary-direct-lambda-call</code> when a directly called
lambda in a class body wraps a comprehension containing an assignment expression.
PEP 572 makes that a <code>SyntaxError</code> without the lambda's scope, so following the
message produced code that would not compile.</p>
<p>Closes <a href="">#9294</a></p>
</li>
<li>
<p>Fix a false positive for :ref:<code>unnecessary-ellipsis</code> when an ellipsis is the
sole body statement of a method defined on a <code>Protocol</code>.</p>
<p>Closes <a href="">#9319</a></p>
</li>
<li>
<p>Fix a false positive for :ref:<code>bad-exception-cause</code> when the bases of the class
being raised from cannot be inferred, such as an exception deriving from a
C extension class. :ref:<code>raising-non-exception</code> and
:ref:<code>catching-non-exception</code> already guard the same <code>inherit_from_std_ex</code></p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>303703f</code></a> Bump pylint to 4.0.9, update changelog (<a href="">#11448</a>)</li>
<li><a href=""><code>b342384</code></a> Fix block-scoped disable leaking into sibling elif/else blocks (<a href="">#11429</a>) (<a href="">#11445</a>)</li>
<li><a href=""><code>58c87cf</code></a> Store the results cache as JSON instead of pickle</li>
<li><a href=""><code>e3f4942</code></a> [Backport maintenance/4.0.x] Fix crash on failed attribute inference (<a href="">#11443</a>)</li>
<li><a href=""><code>faf47f9</code></a> [Backport maintenance/4.0.x] Fix false positive no-self-use when a method con...</li>
<li><a href=""><code>20c7bb9</code></a> [Backport maintenance/4.0.x] Fix a crash in method-hidden for methods named a...</li>
<li><a href=""><code>47e6757</code></a> [Backport maintenance/4.0.x] Fix bad-exception-cause false positive when the ...</li>
<li><a href=""><code>ae3ee53</code></a> [Backport maintenance/4.0.x] Fix not-callable false positive for types.Functi...</li>
<li><a href=""><code>3e444be</code></a> [Backport maintenance/4.0.x] Fix a crash in unnecessary-default-type-args for...</li>
<li><a href=""><code>8f2dd4f</code></a> [Backport maintenance/4.0.x] Fix declare-non-slot false positives for ClassVa...</li>
<li>Additional commits viewable in <a href="https://github.com/pylint-dev/pylint/compare/v4.0.8...v4.0.9">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pylint&package-manager=pip&previous-version=4.0.8&new-version=4.0.9)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8124d790600a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.