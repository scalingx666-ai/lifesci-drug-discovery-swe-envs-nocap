# Issue

**Title:** perf(trajectory): kill per-frame renderer rebuilds + conn deep-proxy tax (frame-supply round 1)

## Description

## 帧供给链三刀:每帧 renderer 重建 + 深代理税(接力 #518)

live trace + WebGL 计数器归因(19968 原子流式 zeolite 轨迹,dev :3300):

### 三刀

1. **`bond_state.bond_connectivity`: `$state` → `$state.raw`**。全库核实所有写点都是整数组重赋值(无 push/splice/下标写),重赋值反应性就是消费方需要的全部。深代理让每次 26k-bond conn 走查付 ~13 万 proxy trap——凡是从 getter(而非裸 frame cache)拿到数组的路径都中招。typed_direct 探针:160/40ms → **5-7ms**/帧。

2. **两个 renderer mount effect 的追踪泄漏(大头)**。`AtomManagerInstances` / `BondManagerInstances` 的 mount effect 在追踪上下文里跑构造器 + `force_full_resync()`,而它们读 manager 的类字段 `$state`(version/count)→ effect 被订阅到**每帧 version bump** → 每帧 dispose + 重建两个 renderer + 重建全部 instanced GL attribute:实测 **bufferData ~36MB/帧,5 秒 1.16GB**(capacity 级 12MB vec3 ×2 + 4MB + …)。修法:effect 只追踪 mesh 绑定 + manager 身份两个合法依赖,body 整体 `untrack`(cleanup 经由 untrack 返回)。修后 12 秒播放:**renderer 重建 0 次、bufferData 0 次 0 MB**。

3. **layout-change / positions 两个效应同病**:body 里的 `force_full_resync()` 让它们也订阅 version → 每帧在本职依赖之外再各多跑一遍全量矩阵写(trace 里 `#write_slot` ×3/帧)。body untrack,各回归单一职责。

### 验证

- vitest 4502 pass;svelte-check 0 err
- live:播放/暂停键几何全程干净(over-4Å = 0);mount 计数器(DEV `__amr_mount`)播放期 0 增量
- fps:测量窗口恰逢两个 subagent 满负荷抢占 CPU/GPU,绝对值失真;干净基准随后补(计数类指标不受争用影响,已可证结构性收益)

### 追因方法(备忘)

Svelte 5 类字段 `$state` 会把"在 effect 里调用读它的方法"变成隐式订阅——mount-once effect 里调 `force_full_resync()` 这类"读 manager 内部状态的方法"必须 untrack。同类隐患 grep 面:`new .*Renderer\(` / effect 内 `force_full_resync|sync\(`。

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70eeec8f9d35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.