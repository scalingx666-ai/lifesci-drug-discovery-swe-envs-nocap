# Issue

**Title:** Bump mypy from 1.14.1 to 1.15.0

## Description

Bumps [mypy](https://github.com/python/mypy) from 1.14.1 to 1.15.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python/mypy/blob/master/CHANGELOG.md">mypy's changelog</a>.</em></p>
<blockquote>
<h1>Mypy Release Notes</h1>
<h2>Next Release</h2>
<h3>Different Property Getter and Setter Types</h3>
<p>Mypy now supports using different types for property getter and setter.</p>
<pre lang="python"><code>class A:
    value: int
<pre><code>@property
def f(self) -&amp;gt; int:
    return self.value
@f.setter
def f(self, x: str | int) -&amp;gt; None:
    try:
        self.value = int(x)
    except ValueError:
        raise Exception(f&amp;quot;'{x}' is not a valid value for 'f'&amp;quot;)
</code></pre>
<p></code></pre></p>
<p>Contributed by Ivan Levkivskyi (PR <a href="">18510</a>)</p>
<h3>Selectively Disable Deprecated Warnings</h3>
<p>It's now possible to selectively disable warnings generated from
<a href="https://docs.python.org/3/library/warnings.html#warnings.deprecated"><code>warnings.deprecated</code></a>
using the <a href="https://mypy.readthedocs.io/en/stable/command_line.html#cmdoption-mypy-deprecated-calls-exclude"><code>--deprecated-calls-exclude</code></a>
option.</p>
<pre lang="python"><code># mypy --enable-error-code deprecated
#      --deprecated-calls-exclude=foo.A
import foo
<p>foo.A().func()  # OK, the deprecated warning is ignored</p>
<h1>file foo.py</h1>
<p>from typing_extensions import deprecated<br />
class A:<br />
<a href="https://github.com/deprecated"><code>@​deprecated</code></a>(&quot;Use A.func2 instead&quot;)<br />
def func(self): pass<br />
</code></pre></p>
<p>Contributed by Marc Mueller (PR <a href="">18641</a>)</p>
<h2>Mypy 1.15</h2>
<p>We’ve just uploaded mypy 1.15 to the Python Package Index (<a href="https://pypi.org/project/mypy/">PyPI</a>).</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9397454</code></a> remove +dev from version ahead of final release</li>
<li><a href=""><code>686b591</code></a> remove &quot;unreleased&quot; from 1.15 changelog entry</li>
<li><a href=""><code>cb4b243</code></a> Various small updates to 1.15 changelog (<a href="">#18599</a>)</li>
<li><a href=""><code>1a26502</code></a> Prepare changelog for 1.15 release (<a href="">#18583</a>)</li>
<li><a href=""><code>d4515e4</code></a> Fix a few PR links in the changelog (<a href="">#18586</a>)</li>
<li><a href=""><code>f83b643</code></a> Add object self-type to tuple test fixture (<a href="">#18592</a>)</li>
<li><a href=""><code>ebc2cb8</code></a> Prevent crash on generic NamedTuple with unresolved typevar bound (<a href="">#18585</a>)</li>
<li><a href=""><code>63c251e</code></a> empty commit to trigger wheel rebuild</li>
<li><a href=""><code>c30573e</code></a> Fix literal context for ternary expressions (for real) (<a href="">#18545</a>)</li>
<li><a href=""><code>23d862d</code></a> Fix isinstance with explicit (non generic) type alias (<a href="">#18512</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/python/mypy/compare/v1.14.1...v1.15.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=mypy&package-manager=pip&previous-version=1.14.1&new-version=1.15.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eedfcf980fb3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.