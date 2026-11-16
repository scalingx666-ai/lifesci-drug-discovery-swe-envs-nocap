# Issue

**Title:** perf(trajectory): round 2 — heartbeat push dedupe + in-memory open dedelay

## Description

Round 2(接 #518/#519)。

1. **MCP bridge heartbeat 去重**:push_loop 每 5s 无条件三连 POST + 全结构 JSON.stringify(播放期 structure 冻结、内容恒等 → 纯序列化税,trace 实测 ~550ms/30s;#516 的闸只盖了反应式 pusher,没盖这条循环)。现在 heartbeat 在 (structure 身份 + selection) 未变时跳过;`request_push()`(真实编辑)永远照推。
2. **内存路径秒开**(browser file-picker / 小文件 indexed 打开走 parse.ts,不经 remote loader):plot-metadata 全帧扫描同样从 await 改 `plot_metadata_promise` 随行(Trajectory.svelte 采纳 effect 已在 #519 就位,两条路径共用);初始急加载帧 10→4。streaming 测试更新到延迟契约。

### 实测(dev,19968 原子 100 帧 dump.traj)

- **缓存圈帧消费上限:20 fps**(scrubber 驱动 200 帧/10s,绕开播放 interval),键几何全程干净——今晚全部轮次(#514→#519+本 PR)叠加后的架构上限,起点 0.27
- 首访帧仍付一次性转换+检测(~380ms/帧,首圈 2.6fps)→ follow-up = 空闲预热转换
- prod build 基准数字随后补

vitest 4521+ 全绿(1 个测试按新契约更新);svelte-check 0 err。

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b76a742c2003`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.