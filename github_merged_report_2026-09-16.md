# GitHub Stars 合并报告 - 2026-09-16

**合并日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库数量**: 12

## 目录

1. [ByteDance-Seed/VeOmni](#ByteDance-Seed-VeOmni)
2. [ModelTC/LightX2V](#ModelTC-LightX2V)
3. [aigc-apps/VideoX-Fun](#aigc-apps-VideoX-Fun)
4. [flashinfer-ai/flashinfer](#flashinfer-ai-flashinfer)
5. [hao-ai-lab/FastVideo](#hao-ai-lab-FastVideo)
6. [huggingface/diffusers](#huggingface-diffusers)
7. [modelscope/DiffSynth-Engine](#modelscope-DiffSynth-Engine)
8. [modelscope/DiffSynth-Studio](#modelscope-DiffSynth-Studio)
9. [sgl-project/sglang](#sgl-project-sglang)
10. [vipshop/cache-dit](#vipshop-cache-dit)
11. [vllm-project/vllm](#vllm-project-vllm)
12. [vllm-project/vllm-omni](#vllm-project-vllm-omni)

---

<a id="ByteDance-Seed-VeOmni"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2212
- **最后更新**: 2026-09-17T00:11:42Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Ting, Juncheng Wan

## AI分析总结

## 1. 主要更新类型

两笔提交均为 **Bug 修复**，聚焦于检查点（checkpoint）保存与并行参数注册两个关键子系统：

- `aa8bb43`：修复分阶段检查点保存（staged checkpoint）阻塞训练后端的问题。
- `30d2788`：修复别名参数名未注册 `ExtraParallel` 规格的问题。

## 2. 关键变更点及与项目方向的关系

- **检查点保存隔离**：原先 staged save 的集合通信（准备暂存目录、promotion 各阶段）跑在默认进程组上，导致不参与拷贝的 rank 长时间卡在 NCCL 集合操作中，慢速目标盘场景下可能触发 watchdog 中止进程。现改为在专用的 gloo 组上执行，并引入 `save_timeout_seconds` 作为超时上限，超时直接抛异常而非挂死。
- **异步保存排空一致性**：`raise_if_any_rank_failed` 增加 group 参数，各 slot 在自身写入所用的组上做归约，先完成的 rank 不再占用训练后端等待。
- **清理逻辑健壮性**：promotion 的清理从 always 阶段改为 `finally`，避免 gloo 超时抛出后跳过清理、导致暂存副本滞留 scratch 磁盘。
- **参数别名并行注册**：为别名参数名补齐 `ExtraParallel` 规格注册，保证并行策略在参数别名场景下正确生效。

这些改动直接服务于 VeOmni “以模型为中心的分布式配方库” 定位——训练稳定性与并行正确性是支撑任意模态大模型训练的基础设施。

## 3. 对项目的影响和潜在意义

- 消除了大规模分布式训练中因检查点保存引发的进程级中止风险，提升长时训练的可靠性。
- 超时语义从“静默挂死”变为“显式报错”，便于定位慢速存储或网络问题。
- 别名参数并行注册的修复，避免了并行策略在复杂模型结构下的静默错误，对多模态、多并行组合场景尤为重要。

## 4. 值得关注的技术点

- 用 **gloo 组** 承载检查点拷贝类集合通信，与训练用的 NCCL 后端解耦，是典型的“控制面与数据面分离”思路。
- `save_timeout_seconds` 的约束设计：必须为正整数，未启用 `stage_dir`/`save_async` 时告警，`stage_dir` 与 `save_async` 同时启用则在构造期直接拒绝，体现防御式配置校验。
- marker 在 agree 阶段前拷贝、失败时回退，避免“manifest + marker”被 resume 误判为完整——这是检查点一致性的细节保障。
- 超时组自身故障时保留本 rank 错误作为 cause，保证错误归因不丢失。

## 5. 基于项目背景的发展影响

VeOmni 目标是“扩展任意模态模型的训练”，其核心竞争力在于分布式配方的可靠性与可组合性。这两笔修复虽属细节，却直击大规模训练中最易被忽视的痛点：检查点 I/O 拖垮训练进程、并行规格遗漏导致策略失效。它们增强了框架在异构存储、超大规模集群下的鲁棒性，为后续支持更多模态与并行组合扫清了基础设施层面的障碍，符合项目向生产级训练框架演进的方向。

## 详细提交记录

### [aa8bb43](https://github.com/ByteDance-Seed/VeOmni/commit/aa8bb43c6ba457afde4b9bd35cceaf74823604cc)

- **作者**: Ting
- **时间**: 2026-09-16T09:42:03Z
- **提交信息**: [ckpt] fix: keep the staged-checkpoint copy off the training backend (#1176)

A staged save's collectives -- preparing the staging directory, then the
promotion's phases -- ran on the default process group, so every rank not
copying sat in an NCCL collective for the copy's whole duration; on a
destination far slower than local disk, long enough for the watchdog to abort
the process. They now run on a dedicated gloo group, created at the start of a
staged save, which raises on timeout instead, with the new
save_timeout_seconds as its deadline. Each save_async slot's gloo group is
created with the same timeout.

Draining an async save agrees the same way: raise_if_any_rank_failed takes a
group, and each drained slot reduces on the group its own write ran on, so the
ranks that finished first wait out the others there rather than on the training
backend. An agreement whose group is the thing that broke keeps this rank's own
error as the cause.

The promotion keeps its phases and frees the staged copy in a finally rather
than an always phase: a gloo timeout raises out of a phase, and as a phase the
cleanup would be skipped, stranding the staged copy on the scratch disk.
any_rank_failed takes an optional group. The markers are copied before the
phase that agrees on them, so the coordinator retracts them on any failing exit
it observes -- a step being rewritten still carries the previous run's
manifest, and manifest plus marker is what resume reads as complete. The marker
list is taken before the phases, since the retraction and the staged tree's
removal share one finally.

save_timeout_seconds must be a positive integer, and warns when neither
stage_dir nor save_async is enabled, since it bounds only the groups those two
create. stage_dir with save_async is rejected at construction rather than
save_steps steps into the run.

### [30d2788](https://github.com/ByteDance-Seed/VeOmni/commit/30d278890e36a1480d616e2818cc76124365405a)

- **作者**: Juncheng Wan
- **时间**: 2026-09-16T08:18:33Z
- **提交信息**: [parallel, ckpt] fix: register ExtraParallel specs for aliased parameter names (#1190)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2823
- **最后更新**: 2026-09-16T20:35:20Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

# LightX2V 昨日提交分析（第 1/1 批，共 2 条）

## 1. 主要更新类型
- **Bug 修复为主**：两条提交均为 `fix` 类型，分别针对 minimax-h3 模型和 CFG（无分类器引导）配置逻辑。
- 无新增功能、无文档更新，属于稳定性与正确性维护。

## 2. 关键变更点及与项目方向的关系
- **#1520（minimax-h3）**：将 processor 与 vision encoder 改为预加载。LightX2V 定位为“轻量视频生成推理框架”，推理效率与显存/加载时序是核心指标。预加载可避免推理过程中重复初始化，符合框架追求低延迟、高吞吐的方向。
- **#1519（CFG 设置）**：修复 CFG 配置未被正确遵循的问题，并跳过未使用的 guidance 准备工作。CFG 是扩散/视频生成质量的关键参数，正确响应配置并裁剪冗余计算，直接关系到生成质量与推理性能的平衡。

## 3. 对项目的影响和潜在意义
- 提升 minimax-h3 模型在多模态输入场景下的推理稳定性，减少因组件加载时机不当导致的报错或性能抖动。
- 修复 CFG 逻辑后，用户通过配置控制生成行为的预期得以兑现，避免“配置无效”类隐性 bug，增强框架可信度。
- 跳过无用 guidance 准备可带来实际的速度/资源收益，契合“Light”轻量化定位。

## 4. 值得关注的技术点
- **预加载策略**：processor 与 vision encoder 的预加载是否引入额外启动开销或显存占用，需关注其与懒加载的权衡。
- **CFG 条件分支**：跳过 guidance 准备意味着存在“不需要 guidance”的推理路径（如 CFG=1 或特定模式），说明框架在支持多种引导策略，值得关注其配置语义。
- 两条提交分别涉及模型适配层与通用推理配置层，反映项目在“多模型支持”与“统一推理管线”两条线上同步打磨。

## 5. 结合项目背景的发展影响
LightX2V 作为轻量视频生成推理框架，竞争力取决于**多模型覆盖广度**与**推理效率/正确性**。本次提交一方面修补 minimax-h3 这一具体模型的集成缺陷，扩展可用模型矩阵的可靠性；另一方面修正通用 CFG 逻辑，保障所有依赖 CFG 的模型生成质量。二者共同强化了框架“开箱即用、配置可信、推理高效”的核心价值，属于面向生产可用性的必要维护，为后续模型接入和性能优化奠定稳定基础。

**小结**：本批提交虽小，但精准命中推理框架的两大命脉——模型集成稳定性与配置正确性，方向清晰、风险可控。

## 详细提交记录

### [6214d38](https://github.com/ModelTC/LightX2V/commit/6214d38a756db39a4706b7116178dbd96f16e2f3)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-16T10:07:50Z
- **提交信息**: fix(minimax-h3): preload processor and vision encoder (#1520)

### [bb8301a](https://github.com/ModelTC/LightX2V/commit/bb8301a7dfe8180772bb864d269d8bd05a938f8e)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-16T07:23:13Z
- **提交信息**: fix: honor CFG settings and skip unused guidance preparation (#1519)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2249
- **最后更新**: 2026-09-16T07:29:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6424
- **最后更新**: 2026-09-17T00:23:49Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 10
- **主要提交者**: yichengj, Grace Ho, Yang Xu

## AI分析总结

# FlashInfer 昨日提交总结

## 一、主要更新类型

昨日共 12 个提交，覆盖**功能新增、性能优化、Bug 修复与工程清理**四类。功能侧启用 SM107（Rubin）GEMM 后端、为 `BatchDecodeWithPagedKVCacheWrapper` 增加 `backend="cudnn"` 选项、将 PrimTS 注意力 API 标记为实验性；性能侧优化 BF16 CuTeDSL 稠密 GEMM 调优成本、引入 cuDNN ragged prefill 图缓存；修复侧涉及 MNNVL fabric UUID 判定、TRTLLM MoE tactic 选择回归、SM120 融合 MoE 无效 tile 剪枝及 cuDNN 测试误报；此外补强了测试证据并清理了 vendored kernel 注释。

## 二、关键变更点

- **SM107 增量启用**：放宽 `mm_bf16` 的 `cute-dsl` 声明式门控，使 Rubin 平台可运行，服务 vLLM Kimi-K3 的 QKVG 投影。
- **BF16 GEMM 调优提速**：复用运行时 M、裁剪 Direct 预取配置（编译数 48→24）、回退磁盘缓存，B200 上 564s→173s，B300 上 548s→69s，精度损失≤0.167%。
- **TRTLLM MoE tactic 修复**：修正不规则 tile 阶梯导致的 128 行 tactic 缺失，Kimi-K3 偏斜分布提速 1.63x。
- **cuDNN 后端深度集成**：ragged prefill 通过 execute-time shape override 按长度类别复用图，避免每步 55–70ms 的 plan 重建；decode 从独立函数提升为 wrapper 的 `backend=` 选项，与 prefill 对齐。
- **SM120 剪枝**：剪除必然失败的 tile 候选，消除 autotuner 日志噪音，并按数据类型区分 FP8×FP4 的 K 对齐约束。
- **PrimTS 实验化**：29 个入口统一加 `@flashinfer_experimental_api`，为 API 整合铺路。

## 三、对项目的影响

硬件覆盖从 SM100/103 延伸至 **SM107（Rubin）**，巩固新 GPU 首发适配地位；GEMM 调优成本大幅下降，直接改善冷启动与自动调优体验；MoE tactic 修复提升大模型实际吞吐；MNNVL UUID 修复解决 GB300 多节点服务启动失败，保障通信可靠性。cuDNN 图缓存与 decode 后端统一，强化了在 chunked prefill、spec-decode、大 batch decode 等生产场景的竞争力，标志项目从"提供内核"向"提供端到端可服务、跨代 GPU 一致体验的推理后端"演进。

## 四、值得关注的技术点

- **声明式门控**：仅改需求列表即可启用新架构，无需改内核，是低风险扩展路径。
- **运行时 M 复用 + 配置裁剪**：在保持 tactic 特化的同时降低 JIT 编译量。
- **execute-time shape override**：绕开 SM100 SDPA 引擎不支持动态 shape 的限制。
- **`s_q == 1` 独立类别与 1024-token 桶化**：避免跨边界触发图重建或 `CUDNN_STATUS_NOT_SUPPORTED`。
- **计时器同批测量**：将两计时器包夹同一次执行，消除运行间方差。
- **UUID 判定**：以 `any(clusterUuid)` 替代首字节检查，避免前导零误判。

整体看，本批提交是面向新硬件与生产负载的务实迭代，兼顾性能、兼容性与工程规范。

## 详细提交记录

### [2b16e3c](https://github.com/flashinfer-ai/flashinfer/commit/2b16e3c765fd4bf79339a4b2536a2de68a9c85ee)

- **作者**: Grace Ho
- **时间**: 2026-09-16T21:14:26Z
- **提交信息**: feat(gemm): enable mm_bf16 cute-dsl backend on SM107 (Rubin) (#5222)

`mm_bf16(..., backend="cute-dsl")` is rejected on Rubin:

    flashinfer.utils.BackendSupportedError:
        mm_bf16 does not support backend 'cute-dsl' with capability 107

The rejection comes purely from the declarative gate on
`_cute_dsl_mm_bf16_requirement`, which still lists only [100, 103]; no
kernel is attempted. This blocks callers that request the backend
explicitly and have no fallback -- e.g. vLLM's Kimi-K3 KDA QKVG
projection (vllm/models/kimi_k3/nvidia/low_latency_gemm.py), which opts
SM107 into the SM103 tuning table and then calls mm_bf16 with
backend="cute-dsl" both during warmup autotune and on the decode path
for 3..14 token batches.

Verified on Vera Rubin with the gate widened, the kernel compiles and
runs -- no ptxas rejection -- FlashInfer autotuning completes and saves
35 configs, and an end-to-end Kimi-K3 server comes up healthy and serves
GPQA-diamond.

This follows the incremental SM107 enablement already in this file: 23
gates here list 107, and 7 still list only [100, 103].

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for CuTeDSL BF16 low-M backend checks on SM107 (Rubin)
devices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: grho <grho@nvidia.com>

### [273ed92](https://github.com/flashinfer-ai/flashinfer/commit/273ed92181c7552ae10d472c6bc3f64dcabc2ece)

- **作者**: Vedaanta Agarwalla
- **时间**: 2026-09-16T19:02:39Z
- **提交信息**: test(cudnn): evidence coverage for large-page and non-causal multi-token decode (#4626)

## 📌 Description

Two test-only regression suites documenting attention capabilities the
cuDNN backend already serves correctly, added as evidence for
backend-selection / fallback decisions:

1. **`tests/attention/test_cudnn_prefill_large_page.py`** — paged causal
prefill through `cudnn_batch_prefill_with_kv_cache` is correct at
`page_size` 128/256/512 with 4K–8K KV sequences, including per-request
KV lengths that are not page-size multiples, BF16 GQA `Hq=32/Hkv=2`,
`d=128`, validated against a dense torch SDPA reference over the
gathered pages. Context: #4347 reports the SM100 TRTLLM-gen causal paged
path skipping KV pages for page sizes above 128; this suite shows the
cuDNN backend is a safe fallback for that shape class. Honest scoping
(stated in the module docstring): cuDNN paged prefill serves
`head_dim_qk ∈ {128, 192}`, so #4347's `D=256` repro shape itself is
outside the cuDNN envelope.
2. **`tests/attention/test_cudnn_prefill_noncausal_decode.py`** —
decode-like multi-token generation works today through the existing
cuDNN prefill API on SM100: `causal=False` bidirectional paged GQA with
per-request q lengths in 1..16 against long KV contexts
(diffusion/DFlash block decoding, #3570); `causal=True` at `q_len ≤ 16`
matching a *bottom-right-aligned* reference and provably not matching a
top-left-aligned one (speculative-decode masking, #3335); and
`return_lse=True` writing finite LSE for all valid rows
(merge-readiness). BF16, `d=128`, page_size 16/32, validated against
dense fp32 torch references.

No library code changes.

## 🔍 Related Issues

Evidence for #4347 (cuDNN as large-page fallback), #3570
(bidirectional/diffusion multi-token decode), #3335 (non-causal
speculative decoding).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

(Hooks were run pinned to the repo config via `uvx pre-commit run
--files <changed files>` — all hooks pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Verified on SM100 (cc 10.0) with cuDNN backend 9.26 + cudnn-frontend
1.27: 7 passed (large-page) + 10 passed (non-causal decode), ~6s total.
Both files follow the existing skip conventions (compute capability and
cuDNN availability gates).

## Reviewer Notes

These suites intentionally pin behavior that gap-triage discussions rely
on ("can cuDNN serve this today?"). If a future cuDNN version regresses
either capability, these tests surface it directly rather than through a
serving-stack bug report.

AI-assisted (Claude Code), reviewed and tested end-to-end on hardware.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Added coverage for cuDNN paged prefill with large KV page sizes,
including full and partial pages.
* Added validation for causal and non-causal multi-token decoding with
paged grouped-query attention caches.
* Added checks for output accuracy, causal alignment, and valid
log-sum-exp results across varied sequence lengths and configurations.
* Improved regression protection for supported cuDNN attention workflows
on compatible CUDA hardware.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [8be5e54](https://github.com/flashinfer-ai/flashinfer/commit/8be5e542e5f688aa31cf650333b847f107379696)

- **作者**: Sam Shleifer
- **时间**: 2026-09-16T18:03:29Z
- **提交信息**: fix(comm): accept MNNVL fabric UUIDs with leading zero bytes (#5143)

<!-- .github/pull_request_template.md -->

## 📌 Description

`is_mnnvl_fabric_supported()` rejects a healthy MNNVL fabric when the
first byte of its binary cluster UUID is zero. For example,
`00112233-4455-6677-8899-aabbccddeeff` is nonzero, but `clusterUuid[0]
!= 0` returns false. Consumers can then reject MNNVL or select the wrong
handle type despite CUDA reporting FABRIC support and NVML reporting a
completed fabric.

Check `any(fabric_info.clusterUuid)` instead. This accepts UUIDs with
leading zero bytes while continuing to reject the all-zero UUID. The
CUDA capability check, fabric-state check, and NVML cleanup are
unchanged.

The affected predicate is present in both v0.6.17 and v0.6.18, and in
current main.

## 🔍 Related Issues

No existing issue. Found while investigating a multi-node serving
startup failure on GB300.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks were run with `pre-commit run --files
flashinfer/comm/mnnvl.py tests/comm/test_mnnvl_fabric_support.py`; the
repository-wide hook run is not claimed.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Focused regression suite:

```bash
python -m pytest tests/comm/test_mnnvl_fabric_support.py -q
```

- Before the fix: **2 failed, 4 passed**. Both failures are nonzero
UUIDs whose first byte is zero.
- After the fix: **6 passed**. Cases cover leading-zero UUIDs, a UUID
with only its final byte nonzero, an ordinary UUID, an all-zero UUID,
incomplete fabric state, and unsupported FABRIC handles. CUDA/NVML calls
are mocked, so these tests require no GPU allocation.
- Prior live driver/NVML validation on GB300: on four GPUs in a healthy
fabric with a zero-leading UUID, the original probe returned **False**
and the corrected probe returned **True**. Four GPUs on a fabric with a
nonzero first UUID byte returned **True** with both probes. A downstream
serving run using the same predicate correction successfully allocated
MNNVL memory and served requests on the affected fabric.

The full GPU test suite has not been run for this upstream checkout.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

This is a support-detection fix; it changes no kernels or public
signatures. AI-assisted implementation and test preparation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved detection of supported GPU fabrics when cluster UUIDs begin
with a zero byte.
  * Fabric support checks now handle binary UUID values more accurately.

* **Tests**
* Added coverage for fabric states, UUID values, and expected support
results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f7b1b46](https://github.com/flashinfer-ai/flashinfer/commit/f7b1b4637377c3b66419d52b5ffb71a6b87e3804)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-16T17:21:59Z
- **提交信息**: fix(tests): skip cuDNN GDN kernel-oracle test when CUDA < 13 (#5246)

## Problem

On the Blackwell × CUDA 12.9 CI lanes, every parametrization of

`tests/gdn/test_prefill_cudnn_backend.py::test_cudnn_backend_matches_default`
(added in #4968) fails:

```
E   NotImplementedError: Blackwell GDN prefill is only supported on CUDA 13+
```

The cuDNN backend under test is fine there. The failure is in the test's
**oracle**: this test compares the cuDNN result against FlashInfer's own
SM100
GDN kernel, reached through the default `backend="auto"`, and that
native path
is gated to CUDA 13+ in `flashinfer/gdn_prefill.py`:

```python
if _arch_major == 10:
    if _cuda_major < 13:
        raise NotImplementedError(
            "Blackwell GDN prefill is only supported on CUDA 13+"
        )
```

So the reference call raises before cuDNN is ever exercised. The
module-level
`requires_cudnn_linear_attention` gate covers the cuDNN engines
(package,
frontend version, device) but says nothing about the in-tree kernels the
cross-kernel tests compare against.

The KDA sibling test added in the same PR already handled exactly this
with a
`try/except NotImplementedError` → `pytest.skip`; the GDN test just did
not get
the same treatment.

## Fix

Promote KDA's ad-hoc guard into a shared `reference_kernel_or_skip`
helper in
`tests/test_helpers/cudnn_linear_attention.py`, next to the existing
availability gate, and use it at both oracle call sites.

Only the oracle call is guarded, not the module, so the CUDA 12.9 lane
keeps
running the rest of the file's cuDNN coverage — the serial-reference
numerics,
graph-cache-key, strided-layout and CUDA-graph tests all have
kernel-independent oracles and were already passing.

The GDN-2 and GDP cross-family comparisons also import
`chunk_gated_delta_rule`, but they pass `backend="cudnn"` explicitly and
never
reach the CUDA 13 path, so they need no guard.

## Verification

On a B200 / CUDA 13.0 box:

- Reproduced the CI failure locally by monkeypatching
`torch.version.cuda` to
`"12.9"` and calling the native kernel — it raises `NotImplementedError`
  matching `CUDA 13`, which the helper catches.
- Driving the exact failing parametrization
(`dtype1-True-16-4-4-seq_lens1`) under the same simulated CUDA 12.9 now
  yields a `Skipped` instead of an error.
- All 309 tests across `tests/gdn`, `tests/gdn2`, `tests/gdp` and the
KDA cuDNN
  file still collect; `ruff check` / `ruff format` clean.

The real numerics could not run on this box (cudnn-frontend 1.27 < the
required
1.29, so the module gate skips), so please run CI to confirm the CUDA
12.9
Blackwell column goes green:

`/bot run tests/gdn tests/kda`

## Note, out of scope

`backend="auto"` on SM100 with CUDA 12.x raises rather than falling back
to the
cuDNN engine that works there. Making `auto` fall back would fix this
test
without any guard and would help users on CUDA 12.x, but that is a
routing-policy change rather than a test fix, so it is left alone here.

cc @jhjpark

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Improved backend comparison tests by centralizing reference-kernel
execution and unavailable-backend handling.
* Tests now skip gracefully when the reference implementation is
unavailable, with the relevant exception reported.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [711d3bc](https://github.com/flashinfer-ai/flashinfer/commit/711d3bc94e6d2130af8607320eec612899600084)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-09-16T13:22:33Z
- **提交信息**: BF16 CuTeDSL Dense GEMM: use runtime M and revert kernel disk caching (#5231)

<!-- .github/pull_request_template.md -->

## 📌 Description

Reduce BF16 `cute-dsl` autotune compilation cost:

- Reuse Direct and warp kernels across runtime M; keep tactic
specialization and M≤32 support.
- Prune oversized Direct prefetch configurations, preserving defaults
and all K≤8192 candidates.
- Use one cuBLASLt fallback runner for M>32.
- Revert BF16 disk-cache/TVM-FFI integration from #5140; retain
in-process caching and its stage pruning.

### Performance

BF16 input/output, no bias, PDL on, cold L2; M buckets: 1/2/4/8/16/32.
First full autotune includes JIT, not model E2E.

| GPU / change | N × K | Before | After |
|---|---|---:|---:|
| B200: runtime M + cache rollback | 4608 × 8192 | 564.329 s | 172.993 s
|
| B300: Direct pruning | 8192 × 40960 | 548.096 s | 69.201 s |

Direct pruning reduced compilations **48 → 24**. Across 29 measured
cells, the best retained tactic was at most **0.167%** slower than the
full candidate set, using independent CUPTI remeasurement.

## 🔍 Related Issues

Follow-up to #5089 and #5140; reverts only #5140's BF16 disk-cache
integration.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

All applicable hooks passed on the changed files, including mypy and
Ruff. Repository-wide hooks have not been run for this draft.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

- 10 existing CuTeDSL accuracy tests passed on both B200 and B300.
- Local eager/graph checks: 1,152 warp cases (B200), 756 Direct cases
(B200/B300).
- Verified M=64 uses one cuBLASLt fallback runner (B200).
- No new tests; full CI has not been run.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

Keep draft. Native autotuning can still select slower configurations:
e.g. the B200 runtime-M comparison measured **9.088 → 10.784 µs** at
M=16, N=8192, K=2048 after a tactic change. This is not an all-shape
zero-regression claim.

Shared cache infrastructure is unchanged. Local benchmarks and logs are
excluded.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Performance**
  - Improved BF16 GEMM execution across varying matrix sizes.
  - Compiled kernels can now be reused across different row counts.
  - Added autotuning safeguards to avoid overly costly tactics.
- Streamlined kernel compilation and execution for improved runtime
efficiency.

- **Reliability**
- Improved handling of dynamic matrix dimensions during BF16 GEMM
execution.
- Updated kernel launch handling to use the active CUDA stream
consistently.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [068c1b6](https://github.com/flashinfer-ai/flashinfer/commit/068c1b6e41cdb605715e687805e8f82fedc95625)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-16T12:16:28Z
- **提交信息**: test(autotuner): time both timers on the same run (#4188)

## 📌 Description

Fixes #4170.


`tests/autotuner/test_global_timer.py::test_global_timer_vs_cuda_event[512x8192x8192-cudagraph]`
fails on `release-v0.6.16` rc1 (`unit_test_spark: [cu130]`):

```text
AssertionError: %globaltimer vs cudaEvent mean disagree:
globaltimer=8.3511ms cudaEvent=7.8525ms diff=0.4987ms > allowed=0.3926ms
```

### Root cause

This is not the two timers disagreeing. `time_cuda_event()` runs the
GEMMs, then `time_globaltimer()` runs them **again** — each timer
measures a *separate* execution. Any run-to-run variation in the work
itself is therefore attributed to the timers, and on a power-limited
part like Spark that variation is several percent.

Two details point at a systematic offset rather than random flakiness:

- The reported `allowed=0.3926ms` is exactly `0.05 × 7.8525`, so the
relative term dominated the `3 × combined SEM` term. The per-timer
samples were stable; the two *means* were consistently apart.
- The existing comment says interleaving makes "clock drift / thermal
ramp hit both timers alike", but alternating `event`-then-`globaltimer`
on every trial does not average the effect out — it fixes each timer's
position within the pair.

### Fix

Bracket a **single** execution with both timers, so workload variance
cancels rather than being charged to the timers. The stamps sit outside
the events, so the `%globaltimer` interval strictly contains the
`cudaEvent` interval and the expected residual is the bracket cost (two
stamp launches), positive by construction.

This is a test-only change; no autotuner or timing production code is
touched. It also makes the test measure the property the module
docstring already claims: that the two timers agree about *the same* GPU
work.

## 🔍 Related Issues

- Fixes #4170
- Test introduced by #3870

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

All hooks pass on the changed file.

## 🧪 Tests

- [x] Tests have been updated as needed.
- [x] All targeted tests are passing.

`pytest -q tests/autotuner/test_global_timer.py` → `5 passed` on **H100
NVL** and on **L40S**.

To confirm the mechanism rather than just the pass/fail, I measured the
relative difference of the means, `(globaltimer_mean − cudaEvent_mean) /
cudaEvent_mean`, over 8 repetitions per configuration (`512x8192x8192`,
cudagraph, `_REPEAT=10`):

| method | GPU | mean | spread |
|---|---|---|---|
| separate runs (before) | H100 NVL | −1.238% | −2.561 .. +0.541% |
| same run (after) | H100 NVL | +0.774% | +0.693 .. +0.940% |
| separate runs (before) | L40S | −0.311% | −0.673 .. +0.062% |
| same run (after) | L40S | +0.354% | +0.303 .. +0.395% |

Two things worth noting. The spread collapses (3.10pp → 0.25pp on H100),
which is the flakiness this issue is about. And the remaining offset is
about **10 µs on both parts** — 0.77% of 1.38 ms and 0.35% of 3.1 ms —
which matches two stamp-kernel dispatches. So the timers really do agree
to ~10 µs, and the larger separate-run swings were workload variance.

I also observed the current test consume 0.99 of its tolerance budget
once on H100, i.e. it is close to failing even on a datacenter GPU, not
only on Spark.

## Reviewer Notes

**This needs a Spark run to confirm, which I could not do.** Spark is
only in the internal CI, and the GitHub matrix here covers T4/A10G/H100,
so neither I nor this PR's CI exercises the configuration that failed.
@elvischenv, as the author of #3870, would you be able to run this on
Spark?

The one assumption I could not verify is the size of the bracket cost on
Spark. It is ~10 µs on H100/L40S, far below the 5% budget (393 µs for
the failing shape), but if Spark's stamp-kernel launch is dramatically
more expensive, the smaller `256x4096x11008` shape would be the tight
one. If that happens, the follow-up is to measure the empty-bracket
overhead once and subtract it, rather than to loosen the tolerance.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Improved timer comparison coverage by measuring global timer and CUDA
event results during the same execution.
* Added warm-up timing before trial measurements to improve consistency.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [26617bc](https://github.com/flashinfer-ai/flashinfer/commit/26617bc3f7771cf26edf4b2508127ea9eed48e8f)

- **作者**: Yuxian Qiu
- **时间**: 2026-09-16T11:11:14Z
- **提交信息**: [None][refactor] Mark PrimTS attention APIs as experimental (#5082)

## 📌 Description

Mark all 29 current logged entry points under
`flashinfer/attention/prims_ts/` with `@flashinfer_experimental_api`
before further experimental API consolidation. This covers
context/prefill, FMHA decode, MLA decode, and block-sparse attention,
including previously decorated wrapper methods and the new
QToken-KvBlock-Sparse-Attention helpers from main.

The existing experimental decorator preserves API logging, tensor
dumping, function signatures, and `fi_trace` dispatchers. Calling an API
is the opt-in and emits one `ExperimentalWarning` per decorated
function. No kernel, attention algorithm, workspace, or
runtime-validation implementation changes are included.

Update the stable trace inventory to exclude the newly experimental
PrimTS modules. Update registry tests to unwrap all decorator layers.
Keep the PrimTS guide link and replace generated stable-API reference
listings with the experimental contract.

The dedicated `tests/experimental/test_prims_ts_api.py` was removed as
requested in review. Its annotation checks and aggregate 72-variant
PrimTS signature/axis/CPU trace-completeness coverage are no longer
added by this PR. Existing attention correctness tests, remaining
targeted PrimTS trace tests, and generic experimental-decorator tests
are unchanged.

## 🔍 Related Issues

Follow-up to #4829. This is the annotation prerequisite for a separate
PR consolidating the standalone FMHA/MLA decode APIs. Backend relocation
and API consolidation are deliberately not included here.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

All applicable hooks were run on the changed files (including mypy and
Ruff), rather than modifying or reformatting unrelated files.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

After removing the dedicated PrimTS test file, scoped validation after
rebasing onto `main` (`46afca6a173c239aa33a3a087ec181efcab237c7`) on
2026-09-16: **711 passed** for:

```text
pytest -q tests/experimental/test_experimental_api.py \
  tests/trace/test_template_registry.py \
  tests/trace/test_fi_trace_template_consistency.py
```

Python 3.12, PyTorch 2.12.0a0, CUTLASS DSL 4.7.0. Independent review
also verified once-only warnings for the context/decode/MLA constructors
without any opt-in environment variable. No GPU accuracy or performance
claim is made for this decorator-only change.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it changes
`@flashinfer_experimental_api` entry points. Tracking context: #4829; a
separate graduation tracking issue is not created by this
annotation-only change.
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and this PR does not
add any automatic backend selection.
  - [x] **Test scope declared below.**

```experimental-tests
tests/experimental/test_experimental_api.py
```

## Reviewer Notes

Please review this as an annotation-only migration of an existing
experimental module. The existing backend implementation and GPU
correctness tests remain in their current locations; relocating them to
the experimental trees is outside this PR. Their placement and the
missing standalone graduation issue are explicitly left unchecked above,
not claimed as completed.

All 29 current logged entry points retain the signatures and function
bodies from rebased main; an AST comparison normalized only decorator
imports/names and module documentation. Existing trace arguments remain
intact. Runtime checks verified experimental metadata, preserved
signatures, and trace bindings for all 29 entries, plus one-time
warnings and identical outputs for the three new CPU sparse helpers.

Rebase audit: both original commits are retained. Conflicts in
`docs/api/attention.rst`, `flashinfer/attention/prims_ts/decode.py`, and
`tests/trace/test_fi_trace_template_consistency.py` preserve main's new
decode implementation and sparse-attention description while applying
the experimental classification and stable trace-inventory exclusion.
Follow-up commit `e328f4da` marks the three newly added sparse-metadata
entry points as experimental. No kernel changes or new dedicated PrimTS
test file were introduced. Targeted syntax checks, `git diff --check`,
and all applicable changed-file pre-commit hooks passed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Documentation**
- Updated task-scheduled attention documentation to clarify that these
APIs are experimental, require explicit opt-in through use, emit a
one-time warning, and do not guarantee compatibility.
  - Stable API reference entries are deferred until these APIs graduate.
  - Existing logging and tracing integrations remain available.

- **API Updates**
- Task-scheduled attention entry points are now marked as experimental
and may produce an `ExperimentalWarning` on first use.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>

### [7281e68](https://github.com/flashinfer-ai/flashinfer/commit/7281e687ac160a774f0f9f355c56c8e8de1de7db)

- **作者**: Anthony Chang
- **时间**: 2026-09-16T09:44:00Z
- **提交信息**: fix: perf regression from missing trtllm moe tactics (#5207)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix a TRTLLM backend tactic-selection regression caused by an irregular
supported-tile ladder.

For M=8192, top-k=16, and 896 local experts (Kimi-K3), the average is
`8192 * 16 / 896 = 146.29` routed rows per expert.

**Before:** The selector rounded to 256 and returned `{192, 256}`,
omitting the
supported 128-row TRTLLM tactic.

**After:** The selector centers on the first supported tile at or above
the
actual average, then applies the existing neighbor policy to return
`{128, 192, 256}`. Dense power-of-two lists are unchanged; fallback uses
128 in
this range.

On an NVIDIA B200, normal TRTLLM backend autotuning selected `[128,61]`.
Complete calls were captured in CUDA graphs and measured with CUDA
events over
20 warmups and 200 replays. The comparison used the previous autotuned
`[256,4]` tactic and the corrected autotuned 128-row tactic in the same
process.

The workload uses NVFP4 SiTU with M=8192, model dimension 3584,
intermediate
size 384, 896 experts, and top-k=16.

| Routing distribution | Previous TRTLLM `[256,4]` (ms) | Corrected
TRTLLM `[128,61]` (ms) | Speedup |
|---|---:|---:|---:|
| Uniform | 1.224829 | 1.112245 | 1.101x |
| Skewed | 1.637671 | 1.003464 | 1.632x |

For every token, the router selects 16 experts. In the skewed case, 12
of those
expert selections come from the same pool of 32 hot experts shared by
all
tokens. The other four selections come from the remaining 864 experts.

## 🔍 Related Issues

Follow-up to #5183.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up pre-commit, see the [pre-commit
documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Validated on NVIDIA B200:

```bash
pytest -q \
  tests/moe/test_trtllm_gen_moe_autotune_tactics.py::test_nvfp4_irregular_tile_ladder_brackets_average
# 6 passed

pytest -q \
  tests/autotuner/test_trtllm_fused_moe_autotuner_integration.py::test_bf16_moe_all_supported_tile_n_inference_succeed
# 4 passed

pytest -q \
  tests/moe/test_trtllm_gen_moe_autotune_tactics.py::test_nvfp4_per_token_all_tactics_are_correct
# 2 passed
```

## Reviewer Notes

The change only updates the shared candidate heuristic and input
validation. It
does not modify CUDA kernels, cubins, public APIs, cache or
generated-artifact
identity, or explicit tactic dispatch. Review should focus on the
lower-bound
boundary semantics, preservation of the existing center/+1/+2/-1
neighbor
policy, and the resulting smallest-candidate fallback on irregular
ladders.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved Mixture-of-Experts tile selection for workloads with
irregular supported tile sizes.
* Added safer handling when workload averages fall between available
tile sizes or exceed the largest supported option.
* Removed failures caused by requiring an exact power-of-two tile match.

* **Tests**
* Added coverage for multiple activation types and token counts to
verify correct tile selection across supported NVIDIA architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [24fb16c](https://github.com/flashinfer-ai/flashinfer/commit/24fb16cac987f0e626daa73fb6f53722086c72bd)

- **作者**: Yang Xu
- **时间**: 2026-09-16T09:04:29Z
- **提交信息**: perf(prefill): build the cuDNN ragged graph once per length class via execute-time shape override; keep single-token GQA rows off cuDNN (NVBug 6783545) (#5245)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #5133. `BatchPrefillWithRaggedKVCacheWrapper` with the
cuDNN backend (explicit, or `auto` on SM100) hands cuDNN the exact
`(batch, max_seq_len)` taken from the indptrs, and cuDNN finalizes one
execution plan per declared shape. In serving both values change every
step (chunked prefill picks a new request count and chunk lengths each
step; DCP + spec-decode verify runs this wrapper every decode step with
a varying batch), so every step paid a plan build. Measured on a 148-SM
SM100 board, cuDNN 9.27 / cudnn-frontend 1.30, GQA 32x8 d128 bf16:

- plan build per new shape: 55-70 ms (`build_plans` finalize; heuristics
is ~1.6 ms), ~1 s when a new kernel variant has to be compiled. FA2's
plan()+first run: 0.2-1 ms.
- the same wrapper re-planned for an already-seen shape: 0.16 ms.

cuDNN's dynamic-shape mode is not supported by the SDPA engines on SM100
("This engine currently does not support dynamic shape"), but its
**execute-time shape override** is (unified SDPA engine, cuDNN 9.22+;
`pygraph(is_override_shape_enabled=True)` in cudnn-frontend 1.29+). The
ragged token-indptr graph is now built once at a cache shape and every
execute passes the real shapes through
`override_uids/override_shapes/override_strides` (Q/K/V/O, the four
ragged offsets, both cu_seq_lens, and Stats + its ragged offset when
`return_lse`).

- Cache shape: batch 4096 (next power of two above if a caller exceeds
it), and the q and kv lengths classed separately as **1**, **128** or
**65536** (or the next power of two above the real maximum). `s_q == 1`
is its own class because cuDNN builds a distinct decode kernel for it
and rejects an override that crosses the `s_q == 1` boundary in either
direction (`CUDNN_STATUS_NOT_SUPPORTED_INVALID_DYNAMIC_SHAPE`,
confirmed). 128 vs 65536 because the heuristic selects the short-row
engine for a declared max_len <= 128 and another engine above it; the
flip sits between 128 and 256 on both SM100 and SM107 and does not
depend on batch, `return_lse` or head dims. q and kv are classed
independently so a short-q / long-kv step (chunked prefix, verify) is
not declared as short kv. Within a class, override matches a natively
built plan: q_len-4 rows 1.00x, 1k-token rows 0.64-0.81x (the large
declared length makes the heuristic pick a better config), 4k-8k rows
1.00-1.01x, all bit-identical.
- Workspace: the override graph reserves per-declared-batch TMA
descriptors (measured 1,065,728 bytes at batch 4096 / long class, 2.1
MiB at 8192, 0 for the short class). The wrapper's workspace is far
larger, but a direct caller's may not be, so the graph's requirement is
checked once per graph and a too-small workspace falls back to the
exact-shape graph.
- Scope: the fully ragged 16-bit path (3-D q/k/v, cu_seq_lens on both
sides, all four ragged offsets). Paged, per-batch-length and fp8 graphs
keep the exact declaration.
- `FLASHINFER_CUDNN_PREFILL_SHAPE_OVERRIDE=0` restores the exact
declaration, for bisection.
- Split-K is unaffected: cuDNN disables split-K under override, but the
engine already keeps factor 1 on the `cu_seq_len_q` path and whenever
Stats are produced, so nothing this wrapper reached is lost (checked in
`attentionDescriptors.cpp`; measured identical on both boards).

### Before / after

Serving-like stream on the same board (auto → cuDNN, GQA 32x8 d128 bf16;
300 steps per phase; prefill = 1-32 requests with random 16-2048-token
chunks under an 8192-token budget; verify = 1-128 requests of q_len 4).
"Steps with a build" = plan()+first run() > 20 ms host wall.

| phase | before: steps with a build (total) | after: steps with a build
(total) | plan+run host wall, all 300 steps: cuDNN / FA2 |
|---|---|---|---|
| prefill, 300 steps | 283 (17.9 s) | 2 (0.30 s, the two length-class
builds) | 0.38 s / 0.22 s |
| verify q_len=4, 300 steps | 117 (5.7 s) | 0 | 0.06 s / 0.04 s |
| prefill again, 300 steps | 287 (17.6 s) | 0 | 0.09 s / 0.11 s |

Override vs natively built graph, execute time, interleaved A/B/A
medians of 5 rounds (production B200, 148 SMs, cuDNN 9.27; a Rubin SM107
run agrees to within 1%):

| shape | native | override, cache 64x4096 | override, cache 4096x1M |
|---|---|---|---|
| d192/128 MHA 128 heads, b16 s1024 | 0.891 ms | 1.01x | 1.03x |
| d192/128 MHA 128 heads, b8 s4096 | 6.26 ms | 1.00x | 1.01x |
| d192/128 MHA 128 heads, b16 s4096 | 13.0 ms | 1.00x | 0.99x |
| d192/128 MHA 128 heads, b3 s8192 | 3.84 ms | – | 1.00x |
| GQA 32x8 d128, b16 s1024 / b32 s2048 / b1 s8192 | 0.164 / 1.00 / 0.425
ms | 1.00x / 1.00x / – | 1.00x / 1.06x / 0.98x |
| q_len 4 rows, b64 / b128 | 0.030 / 0.290 ms | 2.3x / 2.0x when served
by the long cache shape; 1.00x with the short one (hence the two
classes) | |

Split-K under override, same B200: on the `cu_seq_len` form this wrapper
uses, native and override pick the same plan (no split-K knob) and time
identically on every low-occupancy shape tried (b=1, h<=4, s up to 16k).
Only the per-batch `seq_len` form loses split-K under override
(1.18-1.63x on those shapes), and this wrapper never issues that form.

Numerics: override output is bit-identical to the natively built graph
for every shape above; against FA2 the new tests hold the usual bf16
tolerance (out 2e-2, LSE 5e-3) for zero-length rows, strided T3HD views,
causal / non-causal and d192/128.


### Single-token GQA rows stay off cuDNN (was #5254)

Found while adding the q_len-1 test, independent of the override (the
exact-shape graph gives the same values): with `s_q == 1`, GQA
(`num_qo_heads > num_kv_heads`) and `return_lse=True`, cuDNN's
decode-class kernel packs the q heads of each kv group and writes the
ragged Stats only for the first head of the group; the attention output
itself is correct. SM100, cuDNN 9.26 and 9.27: 32/8 heads → 24 of 32 LSE
entries per token wrong, 8/2 heads → 6 of 8, MHA (8/8) → all correct,
`q_len >= 2` → all correct. Filed as **NVBug 6783545**.

Why it matters: `auto` routes ragged prefill to cuDNN on Blackwell
(#5133), and a chunked-prefill or DCP step in which every request
contributes exactly one token (a chunk remainder) lands on this kernel;
vLLM's DCP prefill merges the new-token attention with the context part
by LSE, so such a step would produce a silently wrong merge for 3/4 of
the heads.

- `_blackwell_ragged_auto_upgrade` gets `single_token_gqa`; `auto` does
not select cuDNN when `max_qo_len == 1 and num_qo_heads != num_kv_heads`
(plan() cannot know whether run() will ask for the LSE, so the whole
step is routed elsewhere; MHA single-token rows stay eligible, the
kernel is correct there).
- Explicit `backend="cudnn"` raises `NotImplementedError` for that
combination when `return_lse=True`; the no-LSE call keeps working.
- The override test for q_len 1 checks the output but not the LSE for
that class.

## 🔍 Related Issues

Supersedes #5254 (merged into this PR so the guard and the override land
together; the guard alone is the second commit). Follow-up to #5133
(auto → cuDNN/CUTLASS ragged prefill on Blackwell). Same mechanism
FlashInfer's cuDNN GEMM path already uses (`gemm_base.py`,
`is_override_shape_enabled`); PyTorch's cuDNN SDPA integration solves
the same key-granularity problem with power-of-two rounding of
`s_q`/`s_kv`; #4625 does it for the cuDNN decode wrapper by bucketing
`max_seq_len_kv` to 1024 tokens. cuDNN LSE bug: NVBug 6783545.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

New `tests/attention/test_cudnn_ragged_shape_override.py`: cache-shape
function; a 24-step stream of random (batch, max_len) in both classes
builds no new graph (counted via
`flashinfer.cudnn.prefill._prefill_graph_builds`); the env kill-switch
rebuilds per shape as before; FA2 parity in both classes with and
without LSE (zero-length rows, causal / non-causal, d192/128, packed
T3HD views); short-q / long-kv rows with `kv_indptr != qo_indptr` for
q_len 1, 4 and 100, including a no-rebuild stream; a 256 KiB workspace
falls back to the exact-shape graph with identical numbers; CUDA-graph
capture and replay of `run()` in graph mode; growth to a larger cache
shape when a row exceeds it.

`tests/attention/test_auto_backend_upgrade.py` (guard):
`test_auto_declines_single_token_gqa_rows` (auto lands off cuDNN, output
and LSE match fa2; MHA single-token rows still take cuDNN and match),
`test_explicit_cudnn_refuses_single_token_gqa_lse` (raises with LSE,
correct output without), and a **strict xfail**
`test_cudnn_single_token_gqa_lse_is_correct` (`raises=AssertionError`)
against the low-level API so the guards are noticed the moment cuDNN
fixes the kernel.

SM100 (148 SMs), cuDNN 9.27, cudnn-frontend 1.30, both commits together:
`test_auto_backend_upgrade.py` 35 passed / 1 xfailed (the strict xfail);
new override file + auto file 66 passed / 1 xfailed;
`test_cudnn_prefill_token_indptr.py` + `test_cudnn_prefill.py` 423
passed / 288 skipped / 288 xfailed (unchanged).

## Reviewer Notes

- Graph build now happens on the first `run()` of a length class per
(heads, dims, dtype, strides, return_lse, causal, scale); a framework
warmup that runs one short-row and one long-row batch per layer config
removes even that from the serving path.
- The standalone `cudnn_batch_prefill_with_kv_cache` API gets the same
treatment automatically when called with cu_seq_lens + all four ragged
offsets (that is how the wrapper calls it); its other forms are
unchanged.
- The guard is on `auto` and on the explicit-cudnn LSE path only;
`cudnn_batch_prefill_with_kv_cache` (low level) is left as is so the
xfail can observe the kernel directly.
- `_build_prefill_graph` creates the override-enabled `pygraph` directly
instead of through the `cudnn.graph()` context manager, which has no
override argument; the data-type defaults are the same ones the context
manager sets.

<sub>note to self: claude::61d24ed2-7c90-4a97-9cbb-b91ae18136fd —
"flashinfer frost prefill/GEMM enablement" · cwd
/home/scratch.yanxu_libs/flashinfer · worktree
/home/scratch.yanxu_libs/flashinfer-wt-5133 (guard commit from
flashinfer-wt-q1guard)</sub>

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [06949c3](https://github.com/flashinfer-ai/flashinfer/commit/06949c37608a1f34a6c48280682edd3b1afb9613)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-16T08:49:21Z
- **提交信息**: chore: clean up stale comments and vendoring notes (#5223)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Housekeeping pass over comments and docs, mostly in the vendored kernel
trees:

- Drop leftover generator annotations and stale TODO notes that came
along with the vendored CuTe-DSL kernel drops (cute_dsl/attention,
moe_ep/kernel_src).
- Remove an unused example class from the sm120 MoE moe_utils.py sources
(dead code, no references).
- Tidy provenance wording in the `VENDOR.md` records and a couple of
design docs/benchmark notes.
- Reword a few code comments to reference public PTX documentation and
drop stale issue-tracker breadcrumbs that aren't actionable for external
contributors.


## 🔍 Related Issues

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Documentation**
- Updated MoE benchmark, integration, and runbook documentation to
reflect current B200 validation terminology and configurable cluster
login usage.
- Clarified cluster-launch-control semantics and vendored-source
provenance.

- **Refactor**
- Removed an internal-only tensor-map constructor and updated tensor-map
descriptor sizing in a kernel implementation.

- **Chores**
- Removed obsolete internal release markers, author attributions, issue
references, and stale platform or hostname references from comments and
supporting materials.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b037528](https://github.com/flashinfer-ai/flashinfer/commit/b0375280a0ec75b5b97dd4722db39e6d04b33af7)

- **作者**: yichengj
- **时间**: 2026-09-16T08:31:27Z
- **提交信息**: fix(moe): prune SM120 fused-MoE tile candidates that can never run (#4008)

## 📌 Description

On SM120/SM121, the fused-MoE autotuner is offered tile shapes that
always fail to dispatch. Each profiling pass probes them and throws,
producing the `[Autotuner]: Skipping tactic ... due to failure while
profiling` log noise reported in #3119 (with FP8 activations, 7 of the
10 candidates fail).

This PR filters the SM120 grouped-GEMM candidate list so the autotuner
only sees tiles that can run:

- `128x128x256B` and `256x128x128B` are removed for grouped GEMMs: they
exceed SM120 shared memory and have no dispatch case.
- The `...x64B` tiles are removed when activations are FP8 (the failing
combination shown in the #3119 logs): they break the K alignment the
mixed FP8×FP4 load requires. They stay available for FP4 activations,
where they are valid.

Kernel selection does not change: the surviving candidates are exactly
the ones that dispatched successfully before (verified on an RTX 5080).
Tuning just stops probing dead configs, and the warnings go away. Dense
(non-grouped) SM120 candidates are untouched.

## 🔍 Related Issues

#3119 (closed)

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

No new tests: the change only removes candidates that cannot dispatch,
and correctness is covered by the existing `test_moe_mxfp8_mxfp4`
(passing on RTX 5080 with the pruned list).

## Reviewer Notes

Verification for this change was done by forcing every advertised
gemm1/gemm2 tactic on an RTX 5080: before the change, exactly the pruned
tiles throw; after it, every advertised tactic runs.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance Improvements**
* Improved selection of optimized GPU execution configurations for FP4
workloads.
* Added pruning of configurations that cannot be used in grouped matrix
operations, reducing unnecessary dispatch attempts.
* Preserved fast-build behavior while improving configuration handling
across supported modes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [c039288](https://github.com/flashinfer-ai/flashinfer/commit/c039288594d3f97404166e1f8111f4c5c88143ad)

- **作者**: Vedaanta Agarwalla
- **时间**: 2026-09-16T07:38:07Z
- **提交信息**: feat(decode): backend="cudnn" for BatchDecodeWithPagedKVCacheWrapper; cudnn decode honors q.dtype + base-2 LSE (#4625)

## 📌 Description

Two parts, rebased onto current `main`:

### 1. `backend="cudnn"` for `BatchDecodeWithPagedKVCacheWrapper` (new)

Until now cuDNN decode was reachable only through the standalone
`flashinfer.decode.cudnn_batch_decode_with_kv_cache`; the wrapper's
`backend=` had no cuDNN option
(prefill got one in #5133). This adds it:

- `plan()` (`_plan_cudnn`): validates the supported envelope (fp16/bf16,
one dtype for q/kv/o,
`q_len_per_req == 1`, no RoPE / soft-cap / sliding window), stages the
per-request KV lengths
in a device buffer, and builds a dense `[batch, max_pages]` block table
from the CSR
`indptr/indices` (or uses a caller-passed `block_tables`).
`max_seq_len_kv` and the table width
are rounded up to a 1024-token bucket: cuDNN bakes both into the built
graph (they are part of
the graph-cache key), so without bucketing every decode step whose
longest sequence crossed a
  page boundary would rebuild the graph (~0.5 s).
- `run()`: calls `cudnn_batch_decode_with_kv_cache` with the planned
state; NHD caches are
presented as transposed views (the graph is stride-based, no copy);
`return_lse` supported;
`sinks` / NVFP4 / skip-softmax raise `NotImplementedError`. Only device
ops at run time, so it is
CUDA-graph capturable (test included; pass a fixed `block_tables` to
`plan()` in graph mode so
  the captured buffer is stable).
- Benchmark: `--backends cudnn` now goes through the wrapper; the
previous direct call is
`--backends cudnn-native` (mirrors prefill). fp16 output is no longer
gated out for cuDNN.
- Docs: `docs/api/cudnn.rst`, wrapper docstring.

Measured on B200 (SM100), cuDNN 9.26.0.51 / cudnn-frontend 1.29,
Qwen3-235B decode shape
(b=32, s_kv=4096, 64/4 heads, d128, page 16, CUDA graph): cudnn
(wrapper) 48 µs vs fa2_tc 58 µs vs
trtllm-gen 44 µs; refcheck passes. A broader sweep (6 model shapes ×
batch × s_kv) shows the wrapper
path at parity with trtllm-gen for d128 GQA at b≥32 and ahead of fa2_tc;
d256 shapes are slower
than fa2_tc today (cuDNN-side).

### 2. `cudnn_batch_decode_with_kv_cache`: honor `q.dtype`, add
`return_lse` (original PR content)

- Q/O cuDNN data types derived from `q.dtype` (fp16/bf16) instead of
hard-coded BF16 (fp16 callers
  got `cudnnGraphNotSupportedError` on 9.26).
- New keyword-only `return_lse` / `lse`: builds with `generate_stats`,
returns `(out, lse)`.
**LSE is base-2** — FlashInfer's contract (#4663 made the prefill path
base-2 for the same
reason: the cascade-merge kernels consume it). cuDNN's natural-log stats
are multiplied by
`log2(e)` after `graph.execute`. The wrapper test cross-checks the LSE
against the fa2 backend.
- Graph-cache key includes q/k/v dtypes, `return_lse`, v_cache shape,
block-table shape/dtype, k/v
  strides.

## 🔍 Related Issues

Decode-side counterpart of #5133 (backend="auto"/cudnn for prefill) and
#4663 (base-2 LSE).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] `ruff format` + `ruff check` (v0.12.8, the pinned pre-commit
version) clean on all touched
files; whitespace/EOF hooks applied. (The pre-commit hook environments
could not be installed
on the test box — network — so mypy was not re-run locally; CI will.)

## 🧪 Tests

- [x] `tests/attention/test_cudnn_decode.py` (44) +
`test_cudnn_graph_cache_key.py` pass on B200,
cuDNN 9.26.0.51 / FE 1.29. New: `test_cudnn_wrapper_matches_fa2`
(bf16/fp16 × HND/NHD ×
page 16/64 × 32/8, 64/4 heads; output + LSE vs fa2),
`test_cudnn_wrapper_replan_reuses_block_table_and_bucketed_max`,
`test_cudnn_wrapper_cuda_graph_with_user_block_tables`,
`test_cudnn_wrapper_rejects_unsupported`,
      `test_cudnn_wrapper_rejects_sinks_at_run`.
- [x] `benchmarks/flashinfer_benchmark.py --routine
BatchDecodeWithPagedKVCacheWrapper --backends cudnn cudnn-native fa2_tc
trtllm-gen --refcheck` passes.

## Reviewer Notes

- Not supported through the wrapper yet (cuDNN-side gaps measured on
9.26/9.27): `q_len_per_req > 1`
(cuDNN builds it but lands on a ~17× slower non-split-KV engine),
attention sinks at `s_q == 1`
(rejected by cudnn-frontend), fp8 KV (NVRTC compile failure for some
head configs, unsupported for
d>128). These raise `NotImplementedError` rather than silently
degrading.
- `backend="auto"` still never selects cuDNN for decode; that can follow
once the d256 perf gap is
  closed on the cuDNN side.

AI-assisted (Claude Code), reviewed and tested end-to-end on hardware.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added optional log-sum-exp (LSE) output for cuDNN decode operations,
including caller-provided buffers.
  * Added FP16 and BF16 support for cuDNN decode queries and outputs.
* Added cuDNN support to paged decode wrappers, including GQA, CUDA
graphs, and broader GPU compatibility.

* **Bug Fixes**
* Improved graph selection across shapes, strides, layouts, and data
types.
* Added validation and clear errors for unsupported configurations and
unavailable cuDNN features.
* Improved dtype consistency checks for query, key/value, and output
tensors.
  * Improved validation for user-provided block tables.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4439
- **最后更新**: 2026-09-16T23:19:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34531
- **最后更新**: 2026-09-16T20:36:45Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Dhruv Nair, hf-security-analysis[bot]

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批次两个提交均属于 **CI/CD 基础设施与安全加固**，不涉及模型代码、推理逻辑或文档内容的功能性变更。具体为：
- 安全修复（harden workflows）
- 重构与整合（合并机器人工作流）

### 2. 关键变更点及与项目方向的关系
- **安全加固**：针对 #14623 中被安全分析工具标记的 GitHub Actions 工作流文件进行修复，由安全分析机器人协作完成，属于供应链安全层面的防护。
- **机器人整合**：将原本分散的 style 检查、Serge 代码审查、GPU 测试三类机器人统一归口到 `@diffusers-bot` 名下，并拆分为独立工作流文件。

这与 diffusers 作为高频迭代、社区贡献密集的开源扩散模型库的整体方向一致——随着 PR 数量激增，CI 的稳定性、安全性和可维护性成为支撑快速合并的关键基础设施。

### 3. 对项目的影响和潜在意义
- 降低因工作流配置漏洞导致的密钥泄露或恶意注入风险，保护仓库与发布流程。
- 统一机器人身份后，权限管理与审计更清晰，减少多机器人配置带来的维护成本和潜在冲突。
- 拆分工作流有助于故障隔离，单个检查失败不会阻塞其他检查，提升 CI 反馈效率。

### 4. 值得关注的技术点
- 安全分析机器人（hf-security-analysis[bot]）参与修复，体现 HuggingFace 生态对自动化安全审计的实践。
- 工作流拆分（split bot workflows）是 GitHub Actions 中常见的解耦手段，可提升并行度与可读性。
- 提交信息中保留 PR 编号（#14623、#14788），便于追溯安全问题的完整上下文。

### 5. 基于项目背景的发展影响
diffusers 依赖大量社区 PR 与自动化测试来维持模型、调度器、管线的快速演进。CI 工作流既是质量守门人，也是安全边界。本次加固与整合虽不直接改变用户可见功能，但强化了项目“可持续快速迭代”的底层保障，符合其作为主流扩散模型库对工程规范与安全合规的长期要求。

## 详细提交记录

### [ae2e4c7](https://github.com/huggingface/diffusers/commit/ae2e4c7907ccc21e52ebe86b349d67e9b0b9f316)

- **作者**: hf-security-analysis[bot]
- **时间**: 2026-09-16T15:00:44Z
- **提交信息**: fix(ci): harden GitHub Actions workflows (#14623) (#14788)

fix(ci): harden workflow files flagged on #14623

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

### [5211641](https://github.com/huggingface/diffusers/commit/52116412724baa879ad7b1f5a960743938ba400d)

- **作者**: Dhruv Nair
- **时间**: 2026-09-16T08:46:37Z
- **提交信息**: [CI] Consolidate style, Serge review and GPU test bots under `@diffusers-bot` (#14623)

* [CI] Consolidate style, Serge review and GPU test bots under `@diffusers-bot`

* split bot workflows

* update

* update

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-08-31T08:28:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13125
- **最后更新**: 2026-09-16T13:59:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36067
- **最后更新**: 2026-09-17T00:25:29Z

## 提交统计

- **昨日提交总数**: 38
- **提交者数量**: 22
- **主要提交者**: Kan Wu, pllimax, vstone-w

## AI分析总结

# sglang 昨日提交分析总结（38 条）

## 1. 主要更新类型

- **功能新增（占比最大）**：dsv4.1 系列内核（FP8 matmul、RoPE/FP4 packing、compression/KV I/O、communication kernels、candidate indexer）、Ling-3.0-flash-VL 模型支持、gRPC 原生 pause 状态、OTLP 自定义 trace service name、PD 可选 KV 传输校验和、kv-shard 分片池。
- **Bug 修复**：Outlines 预校验允许闭合 schema、GLM5 mHC PP 前向、NIXL 初始化设备上下文、unifiedcache c128 radix 缓存、AMD FP8 wo_a 路径。
- **性能优化**：NPU Ascend 采样去同步、FlashInfer autotune 缓存合并、AMD Lean Attention 确定性、MORI grid 限制。
- **重构/CI**：sgl-router chat encoder→formatter 重命名、模型文件发现共享、CI 修复（elfutils、coverage、NPU docker）。

## 2. 关键变更点与项目方向

- **dsv4.1 内核矩阵成体系落地**（6 条相关提交）：从 matmul、RoPE、通信到压缩与索引，说明项目正为新一代 DeepSeek 模型做底层算子储备，延续 sglang 高性能推理引擎定位。
- **Router 能力持续强化**（约 10 条）：采样契约 1/3~3/3、SIGTERM 前 drain、饱和队列 pin、内存预算约束、HTTP 交换计数，体现 sglang-router 向生产级分布式调度演进。
- **多硬件后端并行推进**：AMD（ROCm/DSV4、Lean Attention）、NPU（采样、CI、docker）、CUDA 13.4，强化跨平台支持。

## 3. 对项目的影响与意义

- dsv4.1 内核与 kv-shard 分片池为大规模 KV 缓存与长上下文推理奠定基础，直接提升吞吐与显存效率。
- Router 系列改动显著增强 k8s 环境下的优雅关闭、负载均衡与内存稳定性，降低生产部署风险。
- 多后端修复（NIXL、AMD、NPU）提升异构集群可用性，扩大适用场景。

## 4. 值得关注的技术点

- **FP4 packing 与 FP8 matmul**：低精度算子对新一代 GPU 推理性能关键。
- **KV 传输校验和**：PD 分离架构下的数据完整性保障。
- **splice injection 免重序列化**：Router 采样注入的性能优化思路。
- **Lean Attention 确定性保持**：AMD 上兼顾性能与可复现性。

## 5. 结合 README 的项目发展影响

README 显示 sglang 定位为高性能 LLM 服务引擎，强调吞吐与多硬件支持。昨日提交高度契合该方向：dsv4.1 内核扩展模型覆盖与算子效率，Router 强化分布式服务能力，多后端修复巩固跨平台优势。整体呈现"新模型内核储备 + 生产级路由 + 异构硬件"三线并进，推动项目从单机推理向大规模生产部署持续演进。

## 详细提交记录

### [46ae84d](https://github.com/sgl-project/sglang/commit/46ae84df159e261fa67d5cce3647f3342fe365a7)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-16T23:54:19Z
- **提交信息**: dsv4.1: Hopper FP8 matmul kernels and tuning (#39657)

Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>

### [dc067c7](https://github.com/sgl-project/sglang/commit/dc067c7d8c525e49f557c1b17afe9197b70b436e)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-16T23:42:17Z
- **提交信息**: [Fix] Allow closed object schemas in Outlines prevalidation (#39869)

### [d78b350](https://github.com/sgl-project/sglang/commit/d78b35076a6f1dc3f18f9c5deaf55bbab99a7688)

- **作者**: Chunan Zeng
- **时间**: 2026-09-16T23:41:29Z
- **提交信息**: [CI] Fix missing elfutils headers in CUDA 13.4 DeepGEMM build (#39855)

### [c244345](https://github.com/sgl-project/sglang/commit/c2443458e1793deb72073a29f6cb7c53113ba695)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-16T23:17:12Z
- **提交信息**: dsv4.1: RoPE and FP4 packing kernels (#39656)

Co-authored-by: DarkSharpness <2040703891@qq.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>
Co-authored-by: BBuf <1182563586@qq.com>

### [f45aad4](https://github.com/sgl-project/sglang/commit/f45aad44bd8155a69764ff7d821bf3403813c52f)

- **作者**: William Arnold
- **时间**: 2026-09-16T22:16:52Z
- **提交信息**: [gRPC] Expose native pause status (#37488)

Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [35b7589](https://github.com/sgl-project/sglang/commit/35b7589e1abcc1d68b487b61c773cdb420229037)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-16T22:15:18Z
- **提交信息**: dsv4.1: candidate indexer library (#39671)

Co-authored-by: DarkSharpness <76582120+DarkSharpness@users.noreply.github.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [13d593b](https://github.com/sgl-project/sglang/commit/13d593b6cf885c5c4d50eea88c82b9e28cf5941e)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-16T20:54:07Z
- **提交信息**: dsv4.1: compression, KV I/O, and metadata kernels (#39652)

Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: DarkSharpness <76582120+DarkSharpness@users.noreply.github.com>

### [869674b](https://github.com/sgl-project/sglang/commit/869674b3a72ea8de4de63e3e302b1052e6b73392)

- **作者**: Justin Perlman
- **时间**: 2026-09-16T20:10:15Z
- **提交信息**: [Fix] Prevalidate JSON Schema support per grammar backend (#37839)

### [43390f6](https://github.com/sgl-project/sglang/commit/43390f63f57c7c56121f4479b6fe606d1e571e16)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-16T19:47:45Z
- **提交信息**: [qwen 3.8 next] change the testing model in test_qwen4_exp_models.py (#39662)

### [b02e16a](https://github.com/sgl-project/sglang/commit/b02e16a895add01a0cfe24bb74922de92ab4d895)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-16T16:59:48Z
- **提交信息**: [Router] Fleet-wide sampling contract 3/3: splice injection without re-serializing (#39002)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [3e03879](https://github.com/sgl-project/sglang/commit/3e03879f6892379707c52923aebfeaff50a57c72)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-16T16:59:26Z
- **提交信息**: [Router] Drain readiness before SIGTERM shutdown so k8s deregisters the pod first (#39016)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [279339f](https://github.com/sgl-project/sglang/commit/279339f113b79af84f27fd3ac92d0a13bd3f4cbd)

- **作者**: Kan Wu
- **时间**: 2026-09-16T16:36:11Z
- **提交信息**: [sgl-router] Share model-file discovery for chat formatters (#39485)

### [f0bf652](https://github.com/sgl-project/sglang/commit/f0bf652534c54fc71528fa9508330e8e980bc8cb)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-16T16:19:26Z
- **提交信息**: Add Ling-3.0-flash-VL model support (#38526)

### [1b78083](https://github.com/sgl-project/sglang/commit/1b78083b428a095d7b0599141b350ac7f09a2bf0)

- **作者**: cctry
- **时间**: 2026-09-16T15:53:30Z
- **提交信息**: [PD] Add optional KV transfer checksums (#39500)

### [a813224](https://github.com/sgl-project/sglang/commit/a813224e7808ff17c4fca27a228e6b076ceb930c)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-09-16T15:52:11Z
- **提交信息**: [ROCm][DSV4] Enable breakable CUDA graph prefill (#37810)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [ad94978](https://github.com/sgl-project/sglang/commit/ad94978adf54a65ee98f05bf0e421be861d09770)

- **作者**: Kan Wu
- **时间**: 2026-09-16T15:46:11Z
- **提交信息**: [sgl-router] Rename chat encoder to chat formatter (#39459)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5aaa182](https://github.com/sgl-project/sglang/commit/5aaa18207cbac182ad607021de593137791ff86f)

- **作者**: Ke Bao
- **时间**: 2026-09-16T15:41:50Z
- **提交信息**: Revert "[CI] Add e2e test for dp-attention local control broadcast" (#39828)

### [e41026f](https://github.com/sgl-project/sglang/commit/e41026f434d82194bbe499938ad697e56110eb65)

- **作者**: Kan Wu
- **时间**: 2026-09-16T14:49:41Z
- **提交信息**: [sgl-router] Forward input_ids only for string content; count tokenize errors only when forwardable (#39458)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [cc171fb](https://github.com/sgl-project/sglang/commit/cc171fbad0266e8eaabb031f4d3858557a23d7e8)

- **作者**: ymren
- **时间**: 2026-09-16T14:37:42Z
- **提交信息**: feat: support custom OTLP trace service name (#35802)

### [00a9a81](https://github.com/sgl-project/sglang/commit/00a9a81b67774e8374172646c092e14999472703)

- **作者**: pllimax
- **时间**: 2026-09-16T12:20:37Z
- **提交信息**: [NPU][CI] Fail fast and speed up long-running qwen3.6 accuracy cases (#39813)

### [e7f7447](https://github.com/sgl-project/sglang/commit/e7f744733333a5ebb63f1114d9632bfca7079a4a)

- **作者**: Shunkangz
- **时间**: 2026-09-16T11:22:23Z
- **提交信息**: [kv-shard 2/4] Sharded pools (#37615)

Co-authored-by: Zhangheng <hzh0425@apache.org>

### [76e06fe](https://github.com/sgl-project/sglang/commit/76e06febab732d28a61b75a61b7835284568cdfb)

- **作者**: Sam Shleifer
- **时间**: 2026-09-16T10:11:40Z
- **提交信息**: [CI] Add e2e test for dp-attention local control broadcast (#39437)

Co-authored-by: Sam Shleifer <sam@thinkingmachines.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7b76207](https://github.com/sgl-project/sglang/commit/7b7620774c1debbb274b28d6dcec33a25be9bae7)

- **作者**: Aurick Qiao
- **时间**: 2026-09-16T09:59:24Z
- **提交信息**: Fix device context during NIXL backend initialization (#38774)

Co-authored-by: Aurick Qiao <6137920+aurickq@users.noreply.github.com>

### [a3bf25d](https://github.com/sgl-project/sglang/commit/a3bf25dc620f31fc672aeced1465d6fe7c81d28f)

- **作者**: inkcherry
- **时间**: 2026-09-16T09:13:59Z
- **提交信息**: [AMD] Clamp MORI intranode grid GPUs (#39763)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [7d5696b](https://github.com/sgl-project/sglang/commit/7d5696b3a1638a7c980e46ed77eb876faad158a2)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-16T09:09:40Z
- **提交信息**: dsv4.1: communication kernels and wrappers (#39653)

Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: DarkSharpness <2040703891@qq.com>
Co-authored-by: DarkSharpness <76582120+DarkSharpness@users.noreply.github.com>
Co-authored-by: Ke Bao <ispobaoke@gmail.com>
Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>
Co-authored-by: Xiaoyu Zhang <xiaoyu.zhang@radixark.ai>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>
Co-authored-by: Zhichen Zeng <zczeng@uw.edu>
Co-authored-by: Ziyi Xu <ziyi.xu@radixark.ai>

### [5a0c1e2](https://github.com/sgl-project/sglang/commit/5a0c1e21e94ed8e5d807547093686c733ff4d382)

- **作者**: Bingxu Chen
- **时间**: 2026-09-16T09:09:08Z
- **提交信息**: [AMD] Preserve deterministic inference when Lean Attention is enabled (#37740)

### [2cbfaef](https://github.com/sgl-project/sglang/commit/2cbfaefbf93cc88bce551df791d40418c43c2f13)

- **作者**: Bingxu Chen
- **时间**: 2026-09-16T08:57:15Z
- **提交信息**: [AMD] Avoid the FP8 wo_a path when the weight is BF16 (#38453)

Signed-off-by: bingxche <bingxche@amd.com>

### [5212797](https://github.com/sgl-project/sglang/commit/5212797880ec6e71b1b557ce73e8a46e262e05ae)

- **作者**: Jensen
- **时间**: 2026-09-16T08:51:38Z
- **提交信息**: [NPU] fix npu docker workspace directory (#39732)

Signed-off-by: xiedeyantu <czjourney@163.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [fc5a979](https://github.com/sgl-project/sglang/commit/fc5a979f21218224b6b8852d661d5dcb3799d6dd)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-16T08:50:29Z
- **提交信息**: [misc] Merge FlashInfer autotune caches across spec workers, pad MXFP4 TP shards, drop dead ngram attrs (#39678)

Co-authored-by: BBuf <1182563586@qq.com>

### [0e528dc](https://github.com/sgl-project/sglang/commit/0e528dc9fff8bc822f0db0939e8acffc362db43b)

- **作者**: vstone-w
- **时间**: 2026-09-16T08:47:42Z
- **提交信息**: bugfix:fix unifiedcache c128 radix cache management (#39426)

### [8baeded](https://github.com/sgl-project/sglang/commit/8baeded6f3ce400e0a2976d8e4037ef2ba482dbb)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-16T08:16:24Z
- **提交信息**: [Router] Pin to the prefix owner when the whole fleet is queueing (--saturation-queue-floor) (#39169)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [ad28b91](https://github.com/sgl-project/sglang/commit/ad28b91faec29cd9e51ecc5b76b06327ed93389e)

- **作者**: Alison Shao
- **时间**: 2026-09-16T08:13:08Z
- **提交信息**: ci: fix always-failing coverage job, add by-GPU-count view (#39697)

### [9c8d464](https://github.com/sgl-project/sglang/commit/9c8d4641ff6415a640352a950b98e312479ddf6a)

- **作者**: Void
- **时间**: 2026-09-16T07:32:53Z
- **提交信息**: [Fix] Fix GLM5 mHC PP forward (#39720)

### [54f0d72](https://github.com/sgl-project/sglang/commit/54f0d72adfa0ec8e36e0540b7bcf03637cd8dd54)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-16T07:29:33Z
- **提交信息**: [Router] Fleet-wide sampling contract 2/3: enforce and inject per request (#39001)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7835f1d](https://github.com/sgl-project/sglang/commit/7835f1de9a2f9cbb92c649fc686e596e4ce225bb)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-16T07:26:50Z
- **提交信息**: [Router] Add the shutdown-drain configuration surface (#39015)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [5beb2fd](https://github.com/sgl-project/sglang/commit/5beb2fd5528bd39f9bffe16a5e2ed2cb50ab2953)

- **作者**: Jensen
- **时间**: 2026-09-16T07:15:16Z
- **提交信息**: [NPU] Avoid device synchronization in Ascend sampling (#39404)

### [e2d56bb](https://github.com/sgl-project/sglang/commit/e2d56bbbfc621a40994ee1216dfab1aa0dfac3d6)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-16T07:13:09Z
- **提交信息**: [Router] Bound the e2e worker memory budget so prefill graph capture stops OOMing (#39713)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [d634320](https://github.com/sgl-project/sglang/commit/d634320e483640b391d0e693110b65662b6ec064)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-16T07:04:38Z
- **提交信息**: [Router] Count open HTTP exchanges until their response body finishes (#39014)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1279
- **最后更新**: 2026-09-16T08:34:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91943
- **最后更新**: 2026-09-17T00:23:36Z

## 提交统计

- **昨日提交总数**: 51
- **提交者数量**: 41
- **主要提交者**: Shanshan Shen, yzong-rh, Adababy

## AI分析总结

# vLLM 昨日提交分析总结（共 51 条）

## 1. 主要更新类型分布

- **Bug 修复**（约 20 条）：占比最高，覆盖 KV Connector 死锁、ROCm 精度回退、CPU FP8 崩溃、Mamba 块分配、多模态 EXIF 解析、前端解析器边界 token 等。
- **功能新增**（约 10 条）：Responses API 逐请求指标、`/inference/v1/generate` 返回 prompt 元数据、`vllm chat` 思考模式、DCP 有效注意力块大小暴露、Rust 前端 gRPC 元数据。
- **性能优化**（约 6 条）：DSV4.1 MegaMoE 去 padding、GDN 投机输出 scatter、Sarvam MLA 路由优化、FlashMLA mega attention。
- **重构与工程化**（约 8 条）：移除未用接口、平台环境检查迁移、`_apply_hf_processor_main` 清理、no-op 自赋值清理。
- **CI/文档/构建**（约 7 条）：MI300 多模态分片、ruff pydocstyle 规则、Transformers 5.17 升级、DeepGEMM pin 更新。

## 2. 关键变更点与项目方向

- **前端 API 成熟化**：Responses API 指标、prompt 元数据、cache_write_tokens 兼容，表明 vLLM 正从"推理引擎"向"生产级服务网关"演进，强化 OpenAI 兼容与可观测性。
- **DeepSeek V4.1 深度优化**：MegaMoE、FlashMLA、NVFP4 压缩 KV、SWA 恢复等多条提交集中出现，说明团队正围绕该模型做端到端性能攻坚。
- **KV 缓存与 P/D 分离**：KV Connector 死锁修复、prefill worker 缓存命中上报、Mooncake 加载失败上报，体现 disaggregated serving 场景的稳定性投入。
- **平台与硬件扩展**：ROCm/AITER、XPU、CPU（zentorch/FP8）、Rust 前端并行推进，符合 README 中"for everyone"的跨平台普惠定位。

## 3. 对项目的影响与潜在意义

- 大量 Bugfix 集中在 KV 传输、缓存、死锁等**长尾稳定性问题**，直接提升生产环境可靠性。
- 前端指标与元数据暴露为**监控、计费、调试**提供基础，是走向企业级部署的关键一步。
- DSV4.1 系列优化与 LoRA 扩展（ModernBert、序列分类）拓宽**模型与微调生态**。
- 工程化清理（ruff 规则、no-op 移除、文档拆分）降低长期维护成本。

## 4. 值得关注的技术点

- **KVConnector + MTP 死锁修复**：涉及多 token 预测与 KV 压力下的并发正确性，是难点问题。
- **FlashMLA mega attention + NVFP4 压缩 KV**：代表注意力与量化前沿方向。
- **region-mapped pull 跨逻辑块对齐**：HiSparse/PD 场景下的分布式一致性细节。
- **LoRA modules_to_save 支持序列分类**：扩展了 LoRA 的适用任务边界。
- **pydocstyle 引入 ruff**：统一文档规范，反映代码质量治理升级。

## 5. 结合 README 的项目发展影响

README 强调 vLLM 是"Easy, fast, and cheap LLM serving for everyone"。本批提交从三个维度呼应这一目标：**fast**——DSV4.1、GDN、Sarvam 等性能优化持续压低延迟与显存；**easy**——前端 API、`vllm chat`、文档规范降低使用门槛；**for everyone**——ROCm/XPU/CPU/Rust 多平台并行推进。整体看，项目正从"高性能推理内核"稳步迈向"多硬件、多模型、生产就绪的统一服务框架"，稳定性与可观测性成为当前阶段的投入重心。

## 详细提交记录

### [91b96a5](https://github.com/vllm-project/vllm/commit/91b96a533cfb06579a360d3aefb2c8341fc89bdb)

- **作者**: Aarushi Jain
- **时间**: 2026-09-16T23:55:14Z
- **提交信息**: [ROCm][CI] Shard MI300 Multimodal Processor (#57056)

Signed-off-by: aarushjain29 <Aarushi.Jain2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [62f9482](https://github.com/vllm-project/vllm/commit/62f948258385418ed248d5cdfceab4d29c1b5bfd)

- **作者**: andrewor14
- **时间**: 2026-09-16T23:11:27Z
- **提交信息**: [Tests] Delete deprecate torchao tests for v1 configs (#52956)

Signed-off-by: andrewor14 <andrewor14@gmail.com>

### [fbf2c5e](https://github.com/vllm-project/vllm/commit/fbf2c5e8be9754f31c4e0f549189fc9f3bdd213c)

- **作者**: xinnywinne
- **时间**: 2026-09-16T22:52:05Z
- **提交信息**: [Frontend] Add per-request metrics to Responses API (#55084)

Signed-off-by: wxin <wxin@nvidia.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>

### [0983aef](https://github.com/vllm-project/vllm/commit/0983aef8da9b25ae5be72a5567e571a8f3f82963)

- **作者**: aoshen02
- **时间**: 2026-09-16T22:29:07Z
- **提交信息**: [Frontend] Return prompt metadata from /inference/v1/generate (#53187)

### [6c3d981](https://github.com/vllm-project/vllm/commit/6c3d9816afbb3e5499a573248d1cf6fcb00c05cd)

- **作者**: Robert Shaw
- **时间**: 2026-09-16T22:22:07Z
- **提交信息**: [BugFix][KV Connector] Fix Deadlock with KVConnector + MTP under KV Pressure (#57104)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5a6ccc5](https://github.com/vllm-project/vllm/commit/5a6ccc589281b4302791cc301e258adcbcc5fead)

- **作者**: yzong-rh
- **时间**: 2026-09-16T21:52:34Z
- **提交信息**: [Bugfix] Add Responses cache_write_tokens for API compat and CC parity (#57222)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [929aa2a](https://github.com/vllm-project/vllm/commit/929aa2a7ed3283913b6ca705ac0e63e4a923c6c4)

- **作者**: Yongye Zhu
- **时间**: 2026-09-16T21:49:35Z
- **提交信息**: [Build] Bump DeepGEMM pin to a6bbb80 (#57218)

### [24a63b3](https://github.com/vllm-project/vllm/commit/24a63b3340f07952a3623d0f28331492f3dab44e)

- **作者**: vllm-agent
- **时间**: 2026-09-16T21:20:28Z
- **提交信息**: [CI][Bugfix] Initialize _transfer_layer_group_ids in region_pull_worker fixture (#57211)

Signed-off-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>
Co-authored-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [e070573](https://github.com/vllm-project/vllm/commit/e0705731be04aac90838f318fcdae15c56a53080)

- **作者**: Flora Feng
- **时间**: 2026-09-16T21:00:48Z
- **提交信息**: [Refactor] Remove unused interface methods (#57194)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [2bdbbc8](https://github.com/vllm-project/vllm/commit/2bdbbc80804b2199cbf39b75e78cf7269d0383a4)

- **作者**: danisereb
- **时间**: 2026-09-16T19:31:43Z
- **提交信息**: [BugFix] Fix is_supported of cutlass FP8 linear (selected and fails on A100) (#55884)

Signed-off-by: Daniel Serebrenik <daserebrenik@nvidia.com>

### [30b847c](https://github.com/vllm-project/vllm/commit/30b847c1fa5461a590606cbc9b8dae4a490c6cdd)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-16T19:09:30Z
- **提交信息**: [Perf][DSV4.1] Remove MegaMoE padding and shared padding workaround (#57204)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [bc0f47c](https://github.com/vllm-project/vllm/commit/bc0f47cd03d6ae99f9f217f096684423bb4ebc2b)

- **作者**: Shanshan Shen
- **时间**: 2026-09-16T18:58:23Z
- **提交信息**: [ROCm][Bugfix] Revert #56433 + #51692 to fix accuracy breakdown for DeepSeek-V4 (#57132)

Signed-off-by: Shanshan Shen <87969357+shen-shanshan@users.noreply.github.com>

### [403f182](https://github.com/vllm-project/vllm/commit/403f182c02778a447cf72cfd08b72537eeba72f8)

- **作者**: cjackal
- **时间**: 2026-09-16T18:47:27Z
- **提交信息**: [MM] Keep raw pixels through dp-sharded ViT path (#56872)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [6b6bf6b](https://github.com/vllm-project/vllm/commit/6b6bf6b3c35ac72e4876a6fe0925608abcf8316f)

- **作者**: jxj
- **时间**: 2026-09-16T18:44:48Z
- **提交信息**: [Bugfix] Remove unsupported comma-separated detailed trace values (#55702)

Signed-off-by: git-jxj <65210887+git-jxj@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [9639cbd](https://github.com/vllm-project/vllm/commit/9639cbde04f58c185ea6e5122dbd2039908abb7a)

- **作者**: Alec
- **时间**: 2026-09-16T18:28:08Z
- **提交信息**: [Rust Frontend] Expose local DP size in gRPC Control metadata (#57116)

Signed-off-by: Alec Flowers <aflowers@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>

### [fc8132a](https://github.com/vllm-project/vllm/commit/fc8132a5e523294ea69decb5e7cbf50e9d3e135e)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-16T18:09:05Z
- **提交信息**: [Bugfix] Fix np.float64 leaking into the KV transfer metrics log (#57068)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [9f9e1da](https://github.com/vllm-project/vllm/commit/9f9e1dac26ff0379651dd7e8ca409b573ccfce54)

- **作者**: Juntian Liu
- **时间**: 2026-09-16T18:09:00Z
- **提交信息**: [Bugfix][Model] Restore causal image SWA for DeepSeek V4.1 (#57152)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [651a88c](https://github.com/vllm-project/vllm/commit/651a88c09ac6cbb13c5dd36f2fdbe61a2c68eeef)

- **作者**: Harry Mellor
- **时间**: 2026-09-16T17:57:24Z
- **提交信息**: [CI] Ignore ruff D209, rejoin the docstrings it split, and silence incompatible-rule warnings (#57212)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [1085b64](https://github.com/vllm-project/vllm/commit/1085b64425a9e6f5ca52876ad32e55fda5665f4e)

- **作者**: Misha Goin
- **时间**: 2026-09-16T17:21:43Z
- **提交信息**: [Benchmark] Retire stale benchmarks and consolidate RMSNorm (#57083)

Signed-off-by: Misha Goin <mgoin64@gmail.com>

### [0b9e018](https://github.com/vllm-project/vllm/commit/0b9e018fb941652441e5d661ef5b8397e4909ebd)

- **作者**: Cyrus Leung
- **时间**: 2026-09-16T17:21:00Z
- **提交信息**: [MM] Further cleanup _apply_hf_processor_main (#53610)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [6ca2b23](https://github.com/vllm-project/vllm/commit/6ca2b23e22aab8534e00a85e8ec5222508a6ecf3)

- **作者**: Rebecca Lee
- **时间**: 2026-09-16T16:48:30Z
- **提交信息**: [ROCm] Expose kFp8DynamicTokenSym on AITER PTPC linears (#54248)

Signed-off-by: Rebecca Lee <rebecca.lee@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [8c1557a](https://github.com/vllm-project/vllm/commit/8c1557a79c539ffe82d004d2a0c8d7b5e71159ce)

- **作者**: Harry Mellor
- **时间**: 2026-09-16T16:44:29Z
- **提交信息**: Add `pydocstyle` to the `ruff` rules (#52136)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Signed-off-by: Harry Mellor <hej.mellor@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [804e537](https://github.com/vllm-project/vllm/commit/804e5377aa0b0cea9544061beb2ebff162543c72)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-16T16:39:07Z
- **提交信息**: [Bugfix][HiSparse][PD] Align region-mapped pulls across logical block sizes (#57077)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [42919b4](https://github.com/vllm-project/vllm/commit/42919b49c573aa0b06710616a3b9785674f36ef5)

- **作者**: Robert Shaw
- **时间**: 2026-09-16T15:23:31Z
- **提交信息**: [P/D] Report prefill worker cache hits in prompt_tokens_details (#54222)

Signed-off-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [dff1bde](https://github.com/vllm-project/vllm/commit/dff1bde84dd6e34a49c150116d0f212507280910)

- **作者**: semerandre
- **时间**: 2026-09-16T15:07:52Z
- **提交信息**: [Model] Qwen4Exp: fp8_e4m3 main KV cache on the QSA path (#55557)

Signed-off-by: Andrea Semeraro <andrea.semeraro@sezione1.it>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [e97ff80](https://github.com/vllm-project/vllm/commit/e97ff8061344d1dbf954ad3c3174ab3b576aaf33)

- **作者**: Roberto L. Castro
- **时间**: 2026-09-16T14:24:59Z
- **提交信息**: [BugFix][PCP] Handle missing DP metadata in one-sided EP (#54016)

Signed-off-by: LopezCastroRoberto <robertol.c510@gmail.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [ca542ee](https://github.com/vllm-project/vllm/commit/ca542ee154e91c9a7757fb0b8f9d90ee578fb613)

- **作者**: linitra24
- **时间**: 2026-09-16T14:16:09Z
- **提交信息**: [Model][LoRA] Enable LoRA support for ModernBertModel (#57148)

Signed-off-by: linitra24 <renshuang.zhou@daocloud.io>

### [c81eb3e](https://github.com/vllm-project/vllm/commit/c81eb3e69c40ab17cb3c4cd8350e4a60b1be70d4)

- **作者**: linitra24
- **时间**: 2026-09-16T14:15:42Z
- **提交信息**: [LoRA] Support modules_to_save for sequence classification (#53555)

Signed-off-by: linitra24 <Joy25810@foxmail.com>
Signed-off-by: linitra24 <renshuang.zhou@daocloud.io>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [ec4a3a5](https://github.com/vllm-project/vllm/commit/ec4a3a537068db40afbc9374a67da719c8c9b964)

- **作者**: Harry Mellor
- **时间**: 2026-09-16T13:34:16Z
- **提交信息**: [CI] Bump Transformers version to 5.17.0 (#56108)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [f8b5c11](https://github.com/vllm-project/vllm/commit/f8b5c11468f665c75968e3a7c12f16ca074f3a30)

- **作者**: sashko-zakharchuk
- **时间**: 2026-09-16T13:24:48Z
- **提交信息**: [Bugfix][Kimi-K3] Do not classify a stateless first chunk as a decode (#51483)

Signed-off-by: Oleksandr Zakharchuk <oleksandr.zakharchuk@gmail.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

### [975dca5](https://github.com/vllm-project/vllm/commit/975dca5bb5db302077674cfa9afe851ee700ad73)

- **作者**: Arpan Tripathi
- **时间**: 2026-09-16T13:03:57Z
- **提交信息**: [Perf][GDN] Scatter mixed speculative outputs into the caller buffer (#57140)

Signed-off-by: Arpan Tripathi <tripathiarpan20@gmail.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Xavier Lyu <9938360+xavierlyu@users.noreply.github.com>
Co-authored-by: Bohdan Podziubanchuk <114604629+Danbog32@users.noreply.github.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Codex <noreply@openai.com>

### [8b1d188](https://github.com/vllm-project/vllm/commit/8b1d188046034b42024d22ee52fa6c3948b4acbd)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-16T12:55:40Z
- **提交信息**: [Bugfix][Mooncake] Report request-level KV load failures under HMA (#56855)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [903285f](https://github.com/vllm-project/vllm/commit/903285fbcc4e51332d562499bd90ec9a1513c813)

- **作者**: Vineeth Sai Varikuntla
- **时间**: 2026-09-16T12:14:54Z
- **提交信息**: [Bugfix] Let an optional Literal flag accept the None it advertises (#52370)

Signed-off-by: Vineeth Sai <vineethsai4444@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [6a2fdf9](https://github.com/vllm-project/vllm/commit/6a2fdf9ac6f929f937dbe4617f1993c068045f81)

- **作者**: Harshit Kedia
- **时间**: 2026-09-16T12:02:47Z
- **提交信息**: [Model] Optimize Sarvam MLA routing and preserve FP32 router logits (#56034)

Signed-off-by: Harshit Kedia <harshit@sarvam.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [3bb7826](https://github.com/vllm-project/vllm/commit/3bb782621492711485dc86791b5978128783814a)

- **作者**: Flora Feng
- **时间**: 2026-09-16T10:55:26Z
- **提交信息**: [Agent] Add agent instructions for parser directories (#56883)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [118e17f](https://github.com/vllm-project/vllm/commit/118e17f5ff301f67f1f4f5bdae2c9ae5e50242c5)

- **作者**: wangxiyuan
- **时间**: 2026-09-16T10:08:36Z
- **提交信息**: [Platform] Move env check function to platform interface (#48599)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d6a1677](https://github.com/vllm-project/vllm/commit/d6a1677d5504244c566eb900ca605cb5511f4ab4)

- **作者**: Yongye Zhu
- **时间**: 2026-09-16T10:07:50Z
- **提交信息**: [Model][DSv4.1] FlashMLA mega attention and the NVFP4 compressed KV cache (#56935)

Signed-off-by: Yongye Zhu <yongye@inferact.ai>
Signed-off-by: 云挚 <ningyunxiao.nyx@antgroup.com>
Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Yongye Zhu <yongye@inferact.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Yunxiao Ning <73625538+foraxe@users.noreply.github.com>
Co-authored-by: AI Assistant <noreply@openai.com>

### [ceb87de](https://github.com/vllm-project/vllm/commit/ceb87de065b9cbdaffd34a0e6aed86c99e772b95)

- **作者**: Adababy
- **时间**: 2026-09-16T09:17:07Z
- **提交信息**: [Misc] Remove no-op self-assignments across vLLM (#55988)

Signed-off-by: shaolila <shaolila@buaa.edu.cn>
Co-authored-by: shaolila <shaolila@buaa.edu.cn>

### [5f203ba](https://github.com/vllm-project/vllm/commit/5f203baedb29bd97f96243f2b83e73fb1bfec7f0)

- **作者**: Harry Mellor
- **时间**: 2026-09-16T09:16:32Z
- **提交信息**: [Docs] Split slash-combined docstring parameters (#57141)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [8273193](https://github.com/vllm-project/vllm/commit/82731931ae1a770ef0439a2afa88a54cb850cdfa)

- **作者**: Ganesh R
- **时间**: 2026-09-16T09:15:12Z
- **提交信息**: [Bugfix][CPU] Fall back to CpuPlatform when zentorch fails to import (#54923)

Signed-off-by: R <Ganesh.R@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [03f67b3](https://github.com/vllm-project/vllm/commit/03f67b3ad1e61d12c21d42e20e69cb5f99bdd82e)

- **作者**: Canlin Guo
- **时间**: 2026-09-16T09:08:42Z
- **提交信息**: [Perf][DSV4.1] Pad shared experts for native MegaMoE fusion (#56568)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [0384e72](https://github.com/vllm-project/vllm/commit/0384e72693985d0eddae70bd330b9cb283ff4313)

- **作者**: Misha Goin
- **时间**: 2026-09-16T08:54:10Z
- **提交信息**: [UX] Add thinking support to `vllm chat` (#57045)

### [35f6047](https://github.com/vllm-project/vllm/commit/35f6047c1a2df9bb26ebbefc2b4e64717010e0fe)

- **作者**: Jakub Byczkowski
- **时间**: 2026-09-16T08:54:02Z
- **提交信息**: [XPU][Bugfix] Fix Qwen2-Audio ValueError on audio clips longer than 30s (#56912)

Signed-off-by: Jakub Byczkowski <jakub.byczkowski@intel.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: Copilot <175728472+Copilot@users.noreply.github.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [f37c550](https://github.com/vllm-project/vllm/commit/f37c550bf6353d7d2a7289cbf256943e8c282fad)

- **作者**: JulienDarve
- **时间**: 2026-09-16T08:29:43Z
- **提交信息**: [Feature][Frontend] Expose effective attention block size for DCP (#56538)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Signed-off-by: Julien Darve <jdarve@NVIDIA.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [0d8173d](https://github.com/vllm-project/vllm/commit/0d8173d1537f60331084e12af6b72a6565978c9d)

- **作者**: wenjinhust
- **时间**: 2026-09-16T08:25:49Z
- **提交信息**: [Bugfix][Frontend] Lazy-import model_hosting_container_standards to prevent log suppression (#51366)

Signed-off-by: wenjinhust <wenjin.sh@huawei.com>

### [8be5205](https://github.com/vllm-project/vllm/commit/8be5205abbabf4c377c603d6c4180a99373f6415)

- **作者**: dev
- **时间**: 2026-09-16T08:17:22Z
- **提交信息**: [Parser] Fix: correct parser frontend handling of reasoning end and boundary tokens (#56635)

Signed-off-by: DEV TYAGI <devtyagi3909@gmail.com>

### [9ca6dbb](https://github.com/vllm-project/vllm/commit/9ca6dbba71329a7b08711e2acfa17b31e542553c)

- **作者**: Ama Senevirathne
- **时间**: 2026-09-16T07:56:50Z
- **提交信息**: fix(multimodal): tolerate malformed EXIF metadata during hashing (#56527) (#56576)

Signed-off-by: amasen02 <amasen02@users.noreply.github.com>
Co-authored-by: amasen02 <amasen02@users.noreply.github.com>

### [b684080](https://github.com/vllm-project/vllm/commit/b68408043d80faf9c99fc16c6aec1174336e9626)

- **作者**: Li, Jiang
- **时间**: 2026-09-16T07:49:17Z
- **提交信息**: [Bugfix][CPU] Add per-tensor FP8 W8A16 kernel to fix Ministral crash on CPU (#56985)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [f12fe10](https://github.com/vllm-project/vllm/commit/f12fe10c5c377ccd401b66c39df3ffb394fa067c)

- **作者**: MINJUN GIL
- **时间**: 2026-09-16T07:47:26Z
- **提交信息**: [Bugfix][KV Offload] Track cache recency once per request (#51787)

Signed-off-by: mindungil <alswnsrlf12@naver.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [ab35354](https://github.com/vllm-project/vllm/commit/ab35354c21cc3c36439e79e18070f85cfafc3af2)

- **作者**: Zheng Gong
- **时间**: 2026-09-16T07:26:56Z
- **提交信息**: [ROCm][AITER] Skip AITER norm kernels when flattening to 2D would copy (#55991)

Signed-off-by: Zheng Gong <zgong@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [f30a195](https://github.com/vllm-project/vllm/commit/f30a195bbb15b920d9c2c40e6a3466d8961ab101)

- **作者**: Wei Zhao
- **时间**: 2026-09-16T07:23:20Z
- **提交信息**: [Bugfix] Fix incorrect Mamba block allocation estimate that prevents request admission (#57050)

Signed-off-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-17
**监控日期**: 2026-09-16
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6830
- **最后更新**: 2026-09-17T00:30:52Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 24
- **主要提交者**: Wu JIAZHEN, nodeeeeee, H.Z

## AI分析总结

# vllm-omni 昨日提交批次分析（25 条）

## 1. 主要更新类型分布

- **Bug 修复（约 12 条，占比最高）**：覆盖 Qwen3-TTS 时间戳、Breeze-TTS-2 静音与 EOS、MOSS Realtime、Fish Speech NPU、Qwen3-Omni Thinker 状态、Qwen-Image RoPE、duplex 会话超长、benchmark 指标计数等。
- **功能新增（约 5 条）**：ComfyUI Generate Music 节点（MiniMax Music 3）、MiniMax H3 文生视频工作流、H3 Ref2VA 参考工作流、统一全双工框架、H3 分离式 VAE 编码器扩展。
- **性能优化（约 4 条）**：CosyVoice3 HiFT 声码器有界窗口流式、Qwen-Image-Edit select01 调制融合、Boogu-Image QKV/FFN 融合与 RMSNorm、H3 VSA 稀疏策略共享。
- **CI/工程杂项（约 3 条）**：MiniCPM-o 精度门限下调、清理 personaplex.yaml 死密钥、diffusion benchmark 预热失败拒绝。

## 2. 关键变更点与项目方向的关系

- **全双工（Full-duplex）能力持续加固**：统一全双工框架（#7413）是核心架构级提交，配合 duplex 会话超长保护（#7277）、duplex eval 本地数据集加载（#7331），显示项目正把实时双向交互作为差异化能力推进。
- **MiniMax-H3 生态快速铺开**：文生视频、Ref2VA、分离式 VAE 编码器、VSA 稀疏策略四条提交形成完整链路，说明 H3 已成为多模态生成的重点模型族。
- **TTS 家族全面稳定化**：Qwen3-TTS、Breeze-TTS-2、MOSS、Fish Speech、CosyVoice3、MiniCPM-o code2wav 均有修复或优化，呼应 README“omni-modality serving”定位。
- **前端集成深化**：ComfyUI 节点与工作流新增，表明项目在降低使用门槛、贴近创作者生态。

## 3. 对项目的影响与潜在意义

- 大量 Bugfix 集中在音频/TTS 边界处理（时间戳、静音、EOS、CFM 缓存），说明这些路径此前存在稳定性债务，本批次显著提升生产可用性。
- 全双工框架统一与超长会话保护，直接关系到“实时服务”场景的健壮性，是走向生产部署的关键一步。
- H3 与 ComfyUI 的结合，扩大了项目在视频生成与工作流编排上的覆盖面，有助于吸引非工程背景用户。

## 4. 值得关注的技术点

- **有界窗口增量 HiFT 声码器流式**（#7521）：流式 TTS 低延迟的关键优化。
- **CUDA 图缓存 + mel 帧分桶**（#7416）：解决 CFM 推理的图缓存不稳定问题。
- **H3 VSA 稀疏策略下沉到模型层并共享原语**（#7535）：注意力稀疏化的架构级抽象。
- **Qwen-Image-Edit 调制融合与 Boogu-Image QKV/FFN 融合**：面向 diffusion 的算子级性能工程。
- **deferred residual 纳入 Thinker 状态捕获**（#7304）：影响 Qwen3-Omni 推理正确性的细节修复。

## 5. 结合 README 的项目发展视角

README 强调“Easy, fast, and cheap omni-modality model serving”。本批次提交从三个维度支撑该目标：**Easy**——ComfyUI 节点与工作流降低使用门槛；**fast**——HiFT 流式、算子融合、稀疏注意力等性能优化；**cheap/稳定**——密集的 TTS 与 duplex Bugfix 保障服务可靠性。整体看，项目正从“支持多模型”走向“多模型生产级稳定 + 实时全双工 + 创作者友好前端”的成熟阶段，H3 与全双工框架是当前两条主线。

## 详细提交记录

### [c32aaeb](https://github.com/vllm-project/vllm-omni/commit/c32aaeb2da49235689f1aa0cb4c4cc116616601e)

- **作者**: Aman
- **时间**: 2026-09-16T22:07:52Z
- **提交信息**: [Bugfix] Fix Qwen3-TTS word timestamps with async chunking (#7544)

Signed-off-by: bezdarnost <amanurumbekov@gmail.com>

### [63032c9](https://github.com/vllm-project/vllm-omni/commit/63032c91c66bf7a4502744d138899554c26b5750)

- **作者**: Weiming Liao
- **时间**: 2026-09-16T20:43:43Z
- **提交信息**: [Frontend] Add ComfyUI Generate Music node with initial MiniMax Music 3 support (#7516)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [5aadcbb](https://github.com/vllm-project/vllm-omni/commit/5aadcbb0abae2e7065966483fcb90ac5ebcbd701)

- **作者**: Yueqian Lin
- **时间**: 2026-09-16T18:40:12Z
- **提交信息**: [Bugfix] Fix Breeze-TTS-2 repeated silence and audio EOS handling

### [a8434a6](https://github.com/vllm-project/vllm-omni/commit/a8434a60da1f40a0d118a326908fd20c9ebe75c7)

- **作者**: akshatvishu
- **时间**: 2026-09-16T18:39:51Z
- **提交信息**: [BugFix][TTS] Fix MOSS Realtime serving and generation (#5661)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>

### [04c55d0](https://github.com/vllm-project/vllm-omni/commit/04c55d0164e586373a2d3a3fdd8ab792b72017e8)

- **作者**: nodeeeeee
- **时间**: 2026-09-16T18:39:13Z
- **提交信息**: Preserve audio boundary embeddings in Qwen2.5-Omni interleaved input (#7510)

Signed-off-by: nodeeeeee <zhangkai.nodeee@gmail.com>

### [c97b5fc](https://github.com/vllm-project/vllm-omni/commit/c97b5fc741ea44acaed37efe520ef8600d1c2abf)

- **作者**: shiyichuan
- **时间**: 2026-09-16T18:38:45Z
- **提交信息**: [Bugfix][Frontend] Route synthetic aborts through final stage (#7006)

Signed-off-by: mershi <mershi@tencent.com>
Co-authored-by: mershi <mershi@tencent.com>

### [38c7eee](https://github.com/vllm-project/vllm-omni/commit/38c7eeee4c7662d28db0c8a3762ebce98d3a520a)

- **作者**: Lei Ke
- **时间**: 2026-09-16T18:38:06Z
- **提交信息**: [BugFix][NPU] Fix Fish Speech S2 Pro NPU support (#7546)

Signed-off-by: Lei Ke <1141466880@qq.com>

### [4392af5](https://github.com/vllm-project/vllm-omni/commit/4392af5ce37ea346a3b51914719a2679dd59d416)

- **作者**: Deep Shah
- **时间**: 2026-09-16T18:36:52Z
- **提交信息**: [Bugfix][Qwen3-Omni] Include deferred residual in captured Thinker states (#7304)

Signed-off-by: Deep Shah <deep@socratic.co>

### [d4dba0d](https://github.com/vllm-project/vllm-omni/commit/d4dba0ddb1d645b8e546a772f3b08e97835ac56c)

- **作者**: THUqliu
- **时间**: 2026-09-16T17:13:32Z
- **提交信息**: [Misc] Remove dead deploy keys from personaplex.yaml (#7454)

Signed-off-by: THUqliu <3298452736@qq.com>

### [2a68471](https://github.com/vllm-project/vllm-omni/commit/2a6847171516b5977f4e9e835f427f5e731d73f3)

- **作者**: hyw
- **时间**: 2026-09-16T17:09:23Z
- **提交信息**: [Bugfix] Reject failed diffusion benchmark warmups (#7092)

Signed-off-by: hyw <yuweih205@gmail.com>
Signed-off-by: HuangYuwei <yuweih205@gmail.com>
Signed-off-by: Alex Brooks <albrooks@redhat.com>
Co-authored-by: Alex Brooks <albrooks@redhat.com>

### [3d75254](https://github.com/vllm-project/vllm-omni/commit/3d75254a4401b9f146d22d5680c772251b8df82f)

- **作者**: y-null
- **时间**: 2026-09-16T16:00:45Z
- **提交信息**: [CI][MiniCPM-o] Lower the Daily-Omni accuracy gate to 0.77 (#7657)

Signed-off-by: y_null <y_null@qq.com>

### [81b5be2](https://github.com/vllm-project/vllm-omni/commit/81b5be274d88eeb73e84091ba3f1466dc6f5a184)

- **作者**: NumberWan
- **时间**: 2026-09-16T15:54:28Z
- **提交信息**: [Bugfix][Qwen-Image] Restore RotaryEmbedding CUDA RoPE for Diffusers e2e (#7513)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [1053f7b](https://github.com/vllm-project/vllm-omni/commit/1053f7b0bdf0a1ac18c09c536d08eefc32bc2995)

- **作者**: psv666
- **时间**: 2026-09-16T15:39:01Z
- **提交信息**: [Bugfix] Preserve benchmark metric sample counts in results (#7624)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [538eddd](https://github.com/vllm-project/vllm-omni/commit/538eddd74d57ac5a8fea0a8ac0d5288e20678ccb)

- **作者**: Zhengyuan Su (苏政渊)
- **时间**: 2026-09-16T12:49:04Z
- **提交信息**: [Perf][CosyVoice3] Bounded-window incremental HiFT vocoder streaming (#7521)

Signed-off-by: Zhengyuan Su <su.zhengyuan@u.nus.edu>

### [fa639b8](https://github.com/vllm-project/vllm-omni/commit/fa639b889e50d28a3cbe88b20b2e94cdc56bdf65)

- **作者**: Tianyao Wu
- **时间**: 2026-09-16T12:08:25Z
- **提交信息**: [Bugfix] Fail a duplex session that outgrows max_model_len instead of killing the EngineCore (#7277)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [e6cebf8](https://github.com/vllm-project/vllm-omni/commit/e6cebf8557c29f965399a931d85c4615cd86fc12)

- **作者**: RyanYun09
- **时间**: 2026-09-16T12:05:52Z
- **提交信息**: [Bugfix][Omni-DuplexEval] Load local Hugging Face dataset layouts in duplex eval loader (#7331)

Signed-off-by: RyanYun09 <RyanYun09@users.noreply.github.com>
Co-authored-by: RyanYun09 <RyanYun09@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [217a6af](https://github.com/vllm-project/vllm-omni/commit/217a6af52cae0d054d3f63b36de0ef653caafc96)

- **作者**: dongbo910220
- **时间**: 2026-09-16T11:06:28Z
- **提交信息**: [Diffusion] Fuse Qwen-Image-Edit select01 modulation for CUDA (#5921)

Signed-off-by: dongbo910220 <1275604947@qq.com>

### [249e84d](https://github.com/vllm-project/vllm-omni/commit/249e84d21b93fe8758bcd06503419367d538c2ac)

- **作者**: dengyunyang
- **时间**: 2026-09-16T10:13:54Z
- **提交信息**: [Boogu-Image] Fuse QKV/FFN projections + switch to diffusion RMSNorm (#6649)

Signed-off-by: dengyunyang <584797741@qq.com>

### [afa837f](https://github.com/vllm-project/vllm-omni/commit/afa837f15c37a1ebff99a4285df80a819a4a2192)

- **作者**: H.Z
- **时间**: 2026-09-16T10:04:52Z
- **提交信息**: [Frontend] Add MiniMax H3 ComfyUI text-to-video workflow (WF-01) (#7423)

Signed-off-by: Hu <hu.zhu@connect.polyu.hk>

### [d554e6b](https://github.com/vllm-project/vllm-omni/commit/d554e6b67eb325adf93945a06fb58faf457ea282)

- **作者**: Wu JIAZHEN
- **时间**: 2026-09-16T08:52:35Z
- **提交信息**: [feat] Extend disaggregated MiniMax-H3 stage with VAE encoders (#6939)

Signed-off-by: asukaqaq-s <1311722138@qq.com>
Signed-off-by: Jader <yjader@foxmail.com>
Co-authored-by: Jader <yjader@foxmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [e78a5d0](https://github.com/vllm-project/vllm-omni/commit/e78a5d01f785795b59bdcbc9f68214a3ce8cd06b)

- **作者**: Linze Shi
- **时间**: 2026-09-16T08:30:16Z
- **提交信息**: [Frontend] Add MiniMax-H3 references and Ref2VA workflow (#7483)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [5f7f62e](https://github.com/vllm-project/vllm-omni/commit/5f7f62e13cfb88bc1add00db5d3ac2e9ef1328f5)

- **作者**: y-null
- **时间**: 2026-09-16T08:24:31Z
- **提交信息**: [Bugfix][MiniCPM-o] Stabilize code2wav CFM CUDA graph caching with reference audio normalization and mel-frame bucketing (#7416)

Signed-off-by: y_null <y_null@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [507cb1d](https://github.com/vllm-project/vllm-omni/commit/507cb1d834db66f2dbb776602e82c62d58e92992)

- **作者**: SYLAR
- **时间**: 2026-09-16T07:47:31Z
- **提交信息**: [Attention] [P1] Keep H3 VSA policy in the model and share sparse primitives (#7535)

Signed-off-by: lishunyang12 <lishunyang12@users.noreply.github.com>
Co-authored-by: lishunyang12 <lishunyang12@users.noreply.github.com>

### [99ff4f3](https://github.com/vllm-project/vllm-omni/commit/99ff4f307040e85ba99e849ef013fdee89525378)

- **作者**: chickeyton
- **时间**: 2026-09-16T07:35:36Z
- **提交信息**: [Core][Frontend] Unified Full-duplex Framework (#7413)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [9005d78](https://github.com/vllm-project/vllm-omni/commit/9005d789033b8c3ec5876a7a68c4e2d9238f5c69)

- **作者**: linzhenpl07
- **时间**: 2026-09-16T07:01:11Z
- **提交信息**: [LingBot World] Reuse the text encode for a prompt already encoded (#6845)

Signed-off-by: linzhenpl07 <linzhenpl07@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

---
