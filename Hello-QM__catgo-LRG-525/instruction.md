# Issue

**Title:** fix(scene): prod TDZ crash — hoist Set-prop bridges above the bond-pairs effect (site down)

## Description

**生产站崩溃热修**(app.catgo-ucsd.org 加载即 `ReferenceError: Cannot access 'cE' before initialization`)。

根因:#518 在 build_bond_pairs `$effect.pre` 里加的 typed-direct 资格检查读了四个 hidden/deleted Set 桥接 `$state`,而它们声明在组件 ~350 行之后。dev 调度掩盖 TDZ;Rollup 产物任何 StructureScene 一渲染即炸 = 全站白屏。

修:四个桥接声明搬到效应之前 + 高音量注释(键管线效应读的每个 $state 必须声明在效应之上)。

验证:同款部署向量(`VITE_STATIC_ONLY` 构建→静态服务→浏览器加载)修前必现、修后无 TDZ、落地页正常;vitest 4529 全绿;svelte-check 0 err。合并后 deploy-cloudflare 自动重部。

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f6569e0602f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.