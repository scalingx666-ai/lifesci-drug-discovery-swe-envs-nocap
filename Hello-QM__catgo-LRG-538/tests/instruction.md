# Issue

**Title:** fix(trajectory): indexed XYZ/extxyz loading keeps the lattice for files >2 MB

## Description

## 中文摘要

修复 #536:**>2 MB 的 .xyz/.extxyz 轨迹在索引式(lazy)加载路径上静默丢失晶格**。单提交 `27e6c786`,基于 `main`。

**故障域链条(修复前):**

```text
>2 MB XYZ/extxyz
        ↓
parse_trajectory_async: TEXT_INDEX_THRESHOLD = 2 MB → indexed/lazy loading
        ↓
frame-loader.ts load_xyz_frame()
        ↓
create_trajectory_frame(..., undefined, undefined, ...)  ← 晶格/pbc 硬传 undefined
        ↓
Lattice 丢失 → periodic bonds / cell box / supercell UI 一并退化
```

同一文件 <2 MB 走急切路径(`parsers/xyz.ts`)一切正常——行为以文件大小为分界,用户无法理解。

**修复(三处,+40/−22):**

1. `parsers/common.ts`:抽出共享 helper `parse_xyz_lattice(comment)`(`Lattice="9 值行主序"` → `Matrix3x3`,缺失/畸形返回 undefined)。
2. `parsers/frame-loader.ts`:`load_xyz_frame` 逐帧解析注释行晶格,连同 `pbc [true, true, true]` 传入 `create_trajectory_frame`——与急切路径约定完全一致;变胞轨迹天然正确(每帧解析自己的注释行)。
3. `parsers/xyz.ts`:急切路径换用同一 helper(volume 元数据计算留在调用点)——**单一事实源,两条路径此后不可能再分叉**。

**回归测试(新文件 `indexed-xyz-lattice.test.ts`,4 用例):**

- 强制索引路径的 lattice + pbc 与急切路径**逐值对齐**(parity 断言);
- 按需帧加载携带**各帧自己的**晶格(变胞:frame 0 → a=10,frame 5 → a=15);
- 分子 xyz(无 Lattice 字段)在索引路径上保持无晶格(不误加);
- **>2 MB extxyz 自动路由进索引加载器且晶格保留**——issue 验收要求的用户侧回归用例(2.66 MB 合成数据,断言真实越过 `TEXT_INDEX_THRESHOLD`)。

**验证:** trajectory 套件 433 pass / 1 skipped;`pnpm check` 0 errors;全量 vitest 4584 pass,仅有的 2 个红项为既知基线项(`cube/periodic-cube-lattice` worker 超时 = 已知环境豁免;`rdf` = 负载 flake,单独跑通过)——与 #537 中的裁决一致,与本改动无关。

**范围说明:** 按 #537 评审结论,本 PR 与 #533/#534(GPU/packet 渲染路径)分属不同故障域,独立成 PR。索引路径同样丢失 forces/move_mask 列的问题在排查中被观察到,但不属于 #536 的晶格范围,未纳入本 PR(如需要可另行立案)。

---

## English summary

: text trajectories above the 2 MB `TEXT_INDEX_THRESHOLD` route through the indexed loader, whose `load_xyz_frame` passed `undefined` lattice/pbc to `create_trajectory_frame` even though every extxyz frame comment carries a valid `Lattice="..."` field — so >2 MB files silently lost their cell (no cell box, non-periodic bonds, supercell controls gone) while the SAME file under 2 MB behaved correctly.

Fix: shared `parse_xyz_lattice` helper in `parsers/common.ts`, used by BOTH the indexed loader (now attaching per-frame lattice + `pbc [true,true,true]`, matching the eager convention; variable-cell works naturally) and the eager parser (deduped onto the helper — single source of truth). Four regression tests including the issue's acceptance case: a genuinely >2 MB extxyz that auto-routes through the indexed loader and keeps its lattice, plus eager/indexed parity, per-frame variable-cell lattices on on-demand loads, and a molecular-xyz guard.

trajectory suite 433 pass / 1 skipped; `pnpm check` 0 errors; full vitest 4584 pass with only the two known baseline items (cube worker timeout = known environment exemption; rdf = load flake, passes isolated) — same adjudication as #537. Known adjacent gap (indexed path also drops forces/move_mask columns) intentionally left out of scope.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcb6b687d9bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.