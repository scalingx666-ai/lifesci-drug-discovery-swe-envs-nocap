# Issue

**Title:** fix(optimade): retry providers on cold start so Search-Database isn't PubChem-only

## Description

## 问题

冷启动后立即打开 Fetch Structure → Search Database，弹窗只显示 PubChem，所有 OPTIMADE 数据库（MP / Alexandria / MC3D / 2DMatpedia …）不显示。关闭再开则全部正常。100% 复现（Windows 桌面 full backend）。

## 根因（与上报分析不同）

上报推测「OPTIMADE router 比 PubChem router 晚注册 ~12s」。**代码层面不成立**：

- `optimade_router` 与 `pubchem_router` 都是 eager import，在 `server/main.py:574-575` **连续、模块加载期**注册，早于 uvicorn 绑定端口。无注册时序差。
- PubChem 能显示是因为弹窗**客户端硬编码**了一个 PubChem 合成条目（`OptimadeSearchModal.svelte`），不需要后端；OPTIMADE 列表需后端往返。这才是真正的不对称。
- 后端 `/optimade/providers` 一旦挂载，任何异常都返回 `FALLBACK_PROVIDERS`，不会报错。

**真正触发**：桌面冷启动时 Python sidecar（Tauri 拉起，PyInstaller 解包 + 重导入）还没监听，用户已点开弹窗 → 前端 `fetch_optimade_providers()` 被 socket 拒绝 → catch → 返回 `[]` → 只剩硬编码 PubChem。旧的重载守卫 `providers.length === 0` 此时长度为 1 → **永不重试**，降级状态卡死。

（`relay_fetch` 注释里记录过一次「只剩 PubChem」——那是**移动端 CORS** 场景，早已修复。同症状，不同触发。）

## 修复（前端自愈，对应上报 6.2）

1. **`fetch_optimade_providers`**：后端拉取加退避重试（3 次，0/400/800ms），首次失败不再放弃；失败/空结果绝不缓存，下次打开可恢复。
2. **`OptimadeSearchModal`**：新增 `optimade_loaded` 标志，重载 `$effect` 守卫改为 `!optimade_loaded`（而非 `providers.length`），降级成只剩 PubChem 时**每次重开都会重试**直到真列表到；并加并发拉取守卫。
3. **测试**：冷启动重试成功 + 空结果不缓存可恢复。

未采纳上报 6.1（后端 readiness 探针）：其前提（router 时序）不成立，且 sidecar 启动延迟不可消除，前端自愈是正确层。

## 验证

- `optimade.test.ts` 套件 10/10 通过
- 全量 vitest **4356 通过 / 0 失败**（真实 CI 门槛）
- 未真机冷启动复现（开发机为 Linux，跑不了 Windows 桌面冷启动）；已对死代码路径逐条确认逻辑

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `119c70fe5977`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.