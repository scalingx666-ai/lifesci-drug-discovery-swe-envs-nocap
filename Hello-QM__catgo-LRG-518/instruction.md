# Issue

**Title:** perf(trajectory): typed-direct bond topology writes — freeze the BondPair chain during playback

## Description

## 起飞终局:typed connectivity 直写 instanced buffer

接力 #514(typed WASM 键边界)/ #517(级联九刀)。trace 定位的最后一个每帧大头:键渲染链每帧 ×2 重建 ~26k `BondPair` 对象并全量流过 `visible → filtered → slot_map → 镜像 diff`(对象构造 + transform 矩阵 + 两张 26k Map + GC)。本 PR 在播放期把这条链整个冻结,连通性直接落到 `BondManager`。

### 机制

- **`conn_to_typed_topology`**(bond-computation-controller):帧连通性 → 共享 scratch 的 `(pairs: Uint32Array, jimages: Int8Array, count)`,过滤语义与对象链完全对齐:
  - stale-distance 预过滤(复用 `get_traj_max_dists` 的 conn-identity memo;NaN 半径 → 跳过检查)
  - 自像 starburst(a==b 且 jimage≠0)丢弃
  - `MAX_BOND_LENGTH` 硬帽(平方比较顺带丢 NaN 几何)
  - 端点越出帧缓冲覆盖(supercell 额外原子)→ 返回 null,调用方回退对象链
- **播放快路**(StructureScene `$effect.pre` 轨迹分支):资格 = 无 distance rules / manual / deleted / hidden(元素/site/属性)/ polyhedra / clip / h-bonds / bond orders / drag。命中则 `bond_manager.replace_auto_bonds(...)`——单次 version bump,渲染器本来就从 mgr 拓扑 + typed 原子 position/color 缓冲写矩阵,每帧剩下的就是两笔缓冲写。
- **`slot_to_filtered_idx` 闸**:typed-direct 期间返回共享空表(此前每次 version bump 都对着冻结的 filtered pairs 重建 26k 条目 Map)。消费方有界检查(gpu-picker-integration L418),拾取退化为 null。
- **暂停尾随同步(500ms debounce)**:最后一次直写 500ms 后重建一次对象管线,拾取/hover/框选恢复精确;随后 shadow sync diff 为 no-op,GPU 缓冲不动。恢复播放自动重进快路。
- **shadow sync 加 typed-direct 闸** + **visible_bond_pairs 无规则时不读 `trajectory_frame_positions`**:live 验证抓到的真 bug——`apply_bond_distance_rules` 无条件收 positions 参数,每帧新身份把 visible/filtered 从冻结的 entry-frame bond_pairs 重算出新数组,shadow sync 每帧醒来用 frame-0 拓扑盖掉 typed 直写 → frame-0 的键画在 frame-N 原子上(满屏拉伸长键,20k 原子 zeolite 轨迹 ~1100 根 >4Å)。两刀都补:无规则短路掐掉每帧依赖(顺带省一遍 26k 过滤),闸是 lbs 等其余 churn 的保险。
- **opacity 效应默认快路**(BondManagerInstances):无 overrides 且 periodic opacity=1 时跳过整个逐 slot 循环——此前每次 version bump 都造 ~26k 短命字符串键(typed-direct 下即每帧)。全 1 不变量由构造保证(`ensure_opacity`/扩容都 fill(1),`replace_auto_bonds` 不碰 opacity,本效应是唯一写入方)。

### 退出路径

资格破坏(加规则/隐藏原子/开 polyhedra…)→ 当帧退出并由对象链重建;轨迹卸载 → `exit_typed_direct()` + 既有 teardown;组件卸载 → timer 清理($effect cleanup)。

### 测试

- `trajectory-bond-pairs.test.ts` +6:拓扑对齐、stale 过滤、未知半径+硬帽、自像/NaN、越界 bail、scratch 复用契约
- 全量 vitest 4502 pass;svelte-check 0 err

### 预期

每帧键侧工作:26k×2 对象构造 + 2×26k Map + slot map 重建 + 26k 字符串 → 一次 26k 扁平循环(scratch,零对象)+ memcpy + 渲染器既有矩阵写。

### Live 实测(dev,:3300,19968 原子 zeolite 轨迹 dump.traj 100 帧)

- typed 直写探针:5.4ms/帧(25892 键,含转换+bulk 替换);键侧对象链每帧归零
- 播放全程 + 暂停态 over-4Å 长键 = 0(修复前 ~1100),mgr 拓扑每帧跟随过滤(25351→25457 波动)
- 播放 1.28fps vs 同景 main 1.0fps —— 剩余瓶颈已不在键渲染链:worker 边界(wasm 53-59ms / 总 500-620ms)+ 流式帧供给,即下一战(加载/供给审计 + prod 基准)。

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32907680690d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.