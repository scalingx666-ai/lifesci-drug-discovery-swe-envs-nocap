# Issue

**Title:** Bump pylint from 4.0.9 to 4.1.3

## Description

Bumps [pylint](https://github.com/pylint-dev/pylint) from 4.0.9 to 4.1.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pylint-dev/pylint/releases">pylint's releases</a>.</em></p>
<blockquote>
<h2>v4.1.3</h2>
<h2>What's new in Pylint 4.1.3?</h2>
<p>Release date: 2026-10-11</p>
<h2>False Positives Fixed</h2>
<ul>
<li>
<p>Fixed a false positive for <code>attribute-defined-outside-init</code> when an
attribute is assigned inside the setter of an old-style, non-decorator
<code>property(fget, fset)</code> call. The decorator form (<code>@property</code> /
<code>@x.setter</code>) was already exempted by the fix for <a href="">#409</a>; the classic
call form was not.</p>
<p>Closes <a href="">#3325</a></p>
</li>
<li>
<p>Fix a false positive for <code>used-before-assignment</code> when a name bound by an earlier
target of the same assignment is used by a later target, as in <code>a = b[a] = 0</code>.</p>
<p>Closes <a href="">#5955</a></p>
</li>
<li>
<p>Fix a <code>no-member</code> false positive in a comprehension inside a branch that
cannot run, such as <code>if sys.platform == &quot;win32&quot;:</code> on Linux. Like the rest of
the branch, the comprehension is no longer checked for missing members.</p>
<p>Closes <a href="">#7240</a></p>
</li>
<li>
<p>Fix a false positive for <code>used-before-assignment</code> when a name bound by a tuple
or list target of a <code>with</code> item is used by a later item of the same <code>with</code> statement.</p>
<p>Closes <a href="">#7545</a></p>
</li>
<li>
<p>Fix false positives such as <code>not-callable</code>, <code>not-an-iterable</code>,
<code>unpacking-non-sequence</code> and <code>no-member</code> on the result of a function whose
body is only <code>...</code>, like <code>@overload</code> and <code>.pyi</code> stubs. Such calls were
inferred as returning <code>None</code>. This affected <code>sqlalchemy.func</code>,
<code>pydantic.Field</code>, and the <code>torch</code> functions wrapped by <code>_add_docstr</code>,
such as <code>torch.linalg.qr</code>.</p>
<p>Closes <a href="">#8138</a>
Closes <a href="">#9218</a>
Closes <a href="">#9354</a>
Closes <a href="">#10087</a></p>
</li>
<li>
<p>Fix a false positive for <code>protected-access</code> when a subclass of a subscripted
generic base, such as <code>class Child(Parent[T])</code>, accesses a protected member
through that base, such as <code>Parent._foo(self)</code>.</p>
<p>Closes <a href="">#8600</a></p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e75de10</code></a> Bump pylint to 4.1.3, update changelog (<a href="">#11637</a>)</li>
<li><a href=""><code>591f6e2</code></a> [Backport maintenance/4.1.x] Fix protected-access false positive through a su...</li>
<li><a href=""><code>a537920</code></a> [Backport maintenance/4.1.x] Ignore discard variable type redefinitions (<a href="">#11635</a>)</li>
<li><a href=""><code>4a8f61c</code></a> [Backport maintenance/4.1.x] Fix duplicate-code crash when min-similarity-lin...</li>
<li><a href=""><code>41fa1c4</code></a> [Backport maintenance/4.1.x] [pyreverse] Fix hang/RecursionError with --all-a...</li>
<li><a href=""><code>a05e2f3</code></a> [Backport maintenance/4.1.x] Fix <code>used-before-assignment</code> false positive for ...</li>
<li><a href=""><code>ea7996b</code></a> [Backport maintenance/4.1.x] Error when several output formats write to stdou...</li>
<li><a href=""><code>479c037</code></a> [Backport maintenance/4.1.x] Fix IndexError when Enum <strong>init</strong> has no argumen...</li>
<li><a href=""><code>e6aa780</code></a> [Backport maintenance/4.1.x] Fix unreachable false positive for raising gener...</li>
<li><a href=""><code>fc58d0b</code></a> [Backport maintenance/4.1.x] Fix pyreverse crash on classes with EmptyNode in...</li>
<li>Additional commits viewable in <a href="https://github.com/pylint-dev/pylint/compare/v4.0.9...v4.1.3">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67c95c975724`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.