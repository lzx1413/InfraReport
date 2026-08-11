# GitHub Stars 合并报告 - 2026-08-11

**合并日期**: 2026-08-12
**监控日期**: 2026-08-11
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


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2141
- **最后更新**: 2026-08-11T21:47:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2638
- **最后更新**: 2026-08-11T22:40:53Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 4
- **主要提交者**: Yang Yong (雍洋), Shiqiao Gu (谷石桥), Chernobyllight

## AI分析总结

### 主要更新类型
- **功能新增**：新增Hunyuan-Image3的TI2I和T2I混合并行入口
- **配置更新**：新增MiniMax H3配置（含FP8 VAE）、更新H3相关配置
- **性能优化**：VAE FP8量化及FP16+FP32混合精度支持、Wan TP RMS更新
- **文档更新**：README更新

### 关键变更点与项目方向
1. **Hunyuan-Image3混合并行**：实现四GPU下TI2I/T2I混合并行路径，采用TP2 ABAB布局加载官方检查点，自回归生成阶段使用TP4，去噪阶段通过多微融合MoE路径切换至TP2+SP2，且无需在阶段间移动权重。这直接服务于项目“轻量视频生成推理框架”的核心目标，通过灵活并行策略降低多卡部署门槛。
2. **VAE量化与精度优化**：新增FP8量化及FP16+FP32混合精度路径，在保证生成质量的同时减少显存占用，提升推理效率，符合框架轻量化定位。
3. **H3与MiniMax配置更新**：持续适配新模型架构，扩展框架支持的模型生态，增强通用性。

### 对项目的影响与潜在意义
- **降低部署门槛**：混合并行方案允许用户以更少GPU（4卡）运行高性能图像/视频生成任务，且无需权重迁移，简化了部署流程。
- **提升推理效率**：VAE量化与混合精度策略直接减少显存和计算开销，对长视频生成场景尤为关键。
- **扩展模型兼容性**：新增MiniMax H3配置和持续更新H3，表明框架正快速跟进前沿模型，巩固其作为多模型统一推理框架的定位。

### 值得关注的技术点
- **无权重迁移的并行切换**：在TP4与TP2+SP2之间动态切换时保持权重驻留，避免昂贵的通信开销，是分布式推理中的实用优化。
- **多微融合MoE路径**：去噪阶段利用MoE结构实现高效并行，体现对稀疏模型推理的深度优化。
- **FP8 VAE量化**：在VAE环节引入FP8，平衡精度与性能，是生成模型推理中较少见的精细化优化。

### 对项目发展的影响
结合README中“轻量视频生成推理框架”的定位，这些提交强化了LightX2V在**多卡并行效率**、**模型适配广度**和**资源占用优化**三方面的竞争力。通过支持更多模型（Hunyuan-Image3、MiniMax H3）和更灵活的并行策略，框架正从单一视频生成工具向**通用多模态生成推理平台**演进。同时，VAE量化与混合精度策略为在消费级GPU上运行高质量生成任务铺平道路，有望吸引更广泛的用户群体。整体上，这些更新体现了项目在**性能、兼容性和易用性**上的持续投入，符合其“Light”的核心理念。

## 详细提交记录

### [6aff9df](https://github.com/ModelTC/LightX2V/commit/6aff9df9574d508b508717a46d679fc0e9da42a3)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-08-11T16:06:05Z
- **提交信息**: Update README.md (#1367)

### [9b5f938](https://github.com/ModelTC/LightX2V/commit/9b5f938ba26eed3f1d9dadbace87b56dea628c1d)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-08-11T16:04:02Z
- **提交信息**: update h3 (#1366)

### [63d54ff](https://github.com/ModelTC/LightX2V/commit/63d54ff4c528548c3bc491f78de9b0e2e3d07bcc)

- **作者**: Chernobyllight
- **时间**: 2026-08-11T11:58:10Z
- **提交信息**: feat(hunyuan-image3): add TI2I and T2I hybrid parallel entry (#1365)

Adds a four-GPU TI2I and T2I hybrid-parallel path that loads the
official checkpoint once in a TP2 ABAB layout, runs autoregressive
generation with TP4, and switches denoising to TP2+SP2 through the
multi-micro fused MoE path without moving weights between phases.

### [f22963a](https://github.com/ModelTC/LightX2V/commit/f22963a46775fb30af5b1b23c63ed37ce4c78bc6)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-11T11:24:01Z
- **提交信息**: add: minimax h3 config with fp8 vae (#1364)

### [497b31b](https://github.com/ModelTC/LightX2V/commit/497b31b873a90f57b51fb781251c4db17411e618)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-08-11T10:03:10Z
- **提交信息**: update wan tp rms (#1361)

### [2cce744](https://github.com/ModelTC/LightX2V/commit/2cce74430445909af8d076549b8c11febb920540)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-11T07:51:22Z
- **提交信息**: vae fp8 quant and vae fp16+ fp32 (#1360)

### [887849d](https://github.com/ModelTC/LightX2V/commit/887849da82ef6daa0b633bcf498af193a88b3a9e)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-08-11T07:26:15Z
- **提交信息**: update h3 (#1359)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2193
- **最后更新**: 2026-08-11T07:55:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6146
- **最后更新**: 2026-08-11T22:22:01Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: ameynaik-hub, Hiki, Yong Wu

## AI分析总结

# 提交分析总结

## 1. 主要更新类型

本批提交涵盖**性能优化**（2项）、**功能新增**（1项）、**CI基础设施改进**（2项），无Bug修复或文档更新。

## 2. 关键变更点及与项目方向的关系

- **GDN模型投机解码优化**（d57bfb1）：为Gated DeltaNet模型实现专用缓存解码内核，通过环形缓冲区存储每token的小型中间量而非完整状态副本，大幅降低投机解码的回滚成本。
- **CUTLASS MoE内存受限内核优化**（e9fb62b）：解决Triton实现性能反超的问题，通过显式向量化（LDG.E.128）和动态block size选择提升Hopper平台BF16性能。
- **tinygemm2 STAGES=16内核层级**（78e463b）：为单波次大K形状新增第三档环形深度，在GB300/B200上超越参考实现。
- **CI测试分片支持**（1b92281）与**移除spot实例**（db9293d）：提升测试可靠性和效率。

## 3. 对项目的影响和潜在意义

性能优化直接回应了与Triton的竞争压力，巩固FlashInfer在推理内核领域的性能优势。GDN投机解码优化降低了显存带宽消耗，使长上下文投机解码更实用。CI改进减少了误报和重试成本，提升开发效率。

## 4. 值得关注的技术点

- **环形缓冲区设计**：通过游标只读+构造性避免冲突，无需跨CTA同步，设计精巧。
- **向量化显式化**：揭示编译器自动向量化的局限性，手动优化SASS级访存模式。
- **动态block size**：根据每行工作量自适应线程数，减少非活动warp。
- **精确计算能力门控**：修正SM107误判问题，确保架构兼容性。

## 5. 对项目发展的影响

这些提交体现了FlashInfer从"通用内核库"向"针对特定模型架构深度优化"的演进。GDN和MoE优化表明项目正从通用Attention内核扩展到更广泛的推理场景，而tinygemm2优化则强化了在Blackwell平台上的竞争力。CI基础设施的完善为快速迭代提供了保障，整体上推动项目在性能、覆盖面和工程成熟度三个维度同步发展。

## 详细提交记录

### [d57bfb1](https://github.com/flashinfer-ai/flashinfer/commit/d57bfb191bb1ea680283b92c1af04af59744c78a)

- **作者**: ameynaik-hub
- **时间**: 2026-08-11T22:21:56Z
- **提交信息**: feat(gdn): u/d cache spec-decode kernels for replayssm (#4081)

## 📌 Description
Two CuTe-DSL kernels that make speculative decoding cheap for GDN
(Gated DeltaNet) models, plus tests and a benchmark.

The problem: during speculative decoding, the engine must be able to
roll back rejected draft tokens. For GDN models the naive way is to
save a full copy of the recurrent state for every draft position — but
GDN states are megabytes per layer per request, so those copies eat
both memory capacity and bandwidth.

The idea: do not save states at all. Save only the small per-token
ingredients (update vector u, normalized key k, decay g) in a small
ring per request. One kernel launch per layer per decode step then does
everything: computes the verify output for the draft tokens, appends
the new ingredients to the ring, and — only when a request's live
window is full, roughly once every 3-5 steps — folds the window into
the single checkpoint state. Rejected tokens cost nothing (just a
cursor that does not advance).

Ring layout and cursors: the ring has 32 physical slots per request
(`RING_SLOTS`), of which at most 16 are ever live (`W_RING`, the max
history window). Two per-request int32 cursors describe the window:
`cache_base` (where it starts) and `hist_len` (how long it is); row j
lives at physical slot `(cache_base + j) & 31`. The kernel treats both
cursors as READ-ONLY: history is read through the rotation, and new
tokens are always appended past the live window at
`(cache_base + hist_len + s) & 31` — for folding and non-folding
requests alike. Since window (≤16) plus appends (≤8) always fit in 32
slots, an append can never touch a slot any of the request's sibling
CTAs is still reading — the fold/append overlap is impossible by
construction, with no inter-CTA synchronization needed.

Cursor commits happen OUTSIDE the launch, after acceptance is known:
fold → `cache_base = (cache_base + hist_len) & 31; hist_len =
n_accepted`; no fold → `hist_len += n_accepted`. These are exactly the
cursor semantics of vLLM's Triton ReplaySSM spec backend, so a serving
integration can share one cursor set between that backend and this
kernel. For standalone use the wrapper can apply the fold commit for
you (`restart_hist_on_flush=True`); this path requires a caller-owned
`cache_base` tensor and validates `hist_len ∈ [0, 16]` /
`cache_base ∈ [0, 32)` (validation is skipped while a CUDA graph is
capturing; the eager warmup calls cover it). The serving path
(`restart_hist_on_flush=False`) stays sync-free.

Included:
- gdn_decode_bf16_wy_ucache_flush.py — the main fused verify+flush
  kernel (32-slot ring as above)
- gdn_decode_bf16_wy_ucache.py — a verify-only variant. NOTE: this
  variant still uses the legacy 16-deep flat layout (history at rows
  [0, hist_len), no cache_base) and is NOT ring-format compatible with
  the flush kernel — do not share one ring allocation between them.
- tests/gdn/test_decode_ucache.py — correctness vs a simple fp32
  reference, including wrapped-window cases (base+len crossing the ring
  boundary), a fold-never-overwrites-the-live-window property test, the
  strided (chunk-view) q/k/v + a/b path, and negative tests for the
  cursor-misuse guards
- benchmarks/bench_gdn_ucache_flush.py — latency benchmark
  (`--no-commit` times the pure kernel; `--base` measures wrapped
  windows)

Supported precision modes (`g_cache` is fp32 in every mode):

| # | mode / arm name | env knobs | q/k/v + output | SSM state | u/k
cache | g (gate) |
|---|---|---|---|---|---|---|
| 1 | bf16 (default) | (none) | bf16 | bf16 | bf16 | fp32 |
| 2 | fp16_io | `IO_DTYPE=fp16` | fp16 | fp16 | fp16 | fp32 |
| 3 | fp16_state | `STATE_DTYPE=fp16` | bf16 | fp16 | bf16 | fp32 |
| 4 | ring_fp16 (cache) | `RING_DTYPE=fp16` | bf16 | bf16 | fp16 | fp32
|
| 5 | fp16_state_cache | `STATE_DTYPE=fp16 + RING_DTYPE=fp16` | bf16 |
fp16 | fp16 | fp32 |

The fp16-state ("mixed") mode is the analogue of
mamba_ssm_cache_dtype=float16 in serving frameworks: only the
checkpoint gains fp16's extra mantissa bits; everything else stays bf16.

How to run:
  pytest tests/gdn/test_decode_ucache.py -v
python benchmarks/bench_gdn_ucache_flush.py --arm bf16 --iters 1000
--no-commit
python benchmarks/bench_gdn_ucache_flush.py --arm fp16_state --iters
1000 --no-commit

Benchmark — us per layer per decode step, 1x B200, Qwen3.5-122B GDN
geometry at TP1 (H=16 key heads, HV=64 value heads, K=V=128, T=4 draft
window, 32-slot ring / 16-row window); columns = fraction of requests
folding their window that step, scattered at exact counts (CUDA-graph
replay, CUPTI cold-L2, median of 1000, `--no-commit` = pure kernel
time; the cursor commit is caller-owned in serving and excluded here).
Wrapped windows (base near the ring boundary) measure the same as
base=0.

| batch | 0% fold | 20% fold | 40% fold | 80% fold |
|------:|--------:|---------:|---------:|---------:|
|     8 |     9.4 |     13.3 |     14.2 |     14.5 |
|    32 |    22.6 |     27.7 |     30.9 |     36.9 |
|    64 |    40.4 |     48.0 |     55.3 |     67.6 |
|   128 |    70.9 |     86.4 |    100.3 |    125.6 |
|   256 |   131.5 |    162.0 |    188.5 |    243.8 |

Scope/limits: validated on B200 (SM100), head dims K=V=128, draft
windows T in {4, 8}. Ring depth is fixed at 32 slots with a 16-row max
window (sized for T ≤ 8). The verify-only variant has not been
converted to the ring layout. Dtype selection via env vars and a couple
of API stubs are known follow-ups.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary

- **New Features**
- Added SM90+ Gated Delta-Net ucache support with conditional
“verify+flush” (folding history into state) and configurable
IO/state/ring dtype specialization.
- Introduced new public decode entry point for verify+flush with options
to control cache base and flush commit behavior.
- **Benchmarking**
- Added a CUDA verify+flush benchmark sweeping batch sizes and flush
rates, including configurable ring modes and cursor commit controls.
- **Tests**
- Added fp32-oracle correctness and regression coverage for outputs,
folded committed state, ring overwrite safety, and strided vs compact
execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1b92281](https://github.com/flashinfer-ai/flashinfer/commit/1b92281bcdb64bb6285818ce36fe7047114ad877)

- **作者**: Adrian
- **时间**: 2026-08-11T20:09:17Z
- **提交信息**: test: Add sharding support to scripts/task_run_unit_tests.sh (#4359)

## 📌 Description

Allow PyTest to run in shards optionally. The jobs in each shard are
allocated to make the shards in balanced load. The output JUnit XML
remains in a compatible format.

## 🔍 Related Issues

Various, including
[PR#3936](https://github.com/flashinfer-ai/flashinfer/issues/3936)

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [X] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [X] I have installed the hooks with `pre-commit install`.
- [X] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [X] Tests have been added or updated as needed.
- [X] All tests are passing (`unittest`, etc.).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added a deterministic, duration-balanced test runner with planning,
sharding, resumable attempts, deadlines, and coordinated workers.
- Added source-aware, solo, long-running, and GPU-capable scheduling
with resource monitoring.
- Added detailed progress, summaries, diagnostics, timing data, capacity
metrics, and standardized statuses.
  - Added artifact scanning and runtime/overhead estimate refresh tools.
- **Reliability**
- Improved validation, state recovery, timeout handling, artifact
safety, and infrastructure-error reporting.
- Added legacy manifest compatibility and clearer command-line
validation.
- **Tests**
- Expanded coverage for sharding, recovery, reporting, process cleanup,
and deterministic trace-template discovery.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [db9293d](https://github.com/flashinfer-ai/flashinfer/commit/db9293dffb01fa359fdcecafc1b560caaa7032b7)

- **作者**: Yong Wu
- **时间**: 2026-08-11T16:26:12Z
- **提交信息**: remove spot instances from pr-test, use on-demand only (#4454)

<!-- .github/pull_request_template.md -->

Spot terminations surfaced as a red X on the PR and needed an automatic
on-demand rerun to recover, which made CI results confusing to read. The
measured savings did not justify that, so pr-test now requests on-demand
runners directly.
- AOT, A10G and T4 jobs move from the spot to the on-demand runner pools
- drop the six analyze/rerun jobs that existed only to recover from a
reclaimed instance, plus the background termination monitor step
- delete scripts/task_monitor_spot.sh and scripts/task_analyze_spot.sh


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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Tests**
- Automated validation now runs across AOT, A10G, T4, and H100
configurations using a dynamic test matrix.
- Results provide clearer aggregate status reporting, with successful
and skipped checks recognized appropriately.
- Test execution includes configuration-specific handling and improved
cleanup.

- **Chores**
- Removed spot-instance execution, termination monitoring, failure
analysis, and on-demand rerun automation.
- Updated repository checkout and test setup behavior for more
consistent automated runs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e9fb62b](https://github.com/flashinfer-ai/flashinfer/commit/e9fb62b74e47444eba83da71a573c9437e71cb3b)

- **作者**: Hiki
- **时间**: 2026-08-11T10:29:38Z
- **提交信息**: perf(moe): optimize CUTLASS fused MoE mem-bound kernels (#3761)

<!-- .github/pull_request_template.md -->

## 📌 Description

### Key Findings

We observed that the Triton implementation outperforms the FlashInfer
CUTLASS fused MoE backend on Hopper for BF16 data types (#3521), and
thus we started investigating kernel optimization opportunities related
to the associated kernels. Here are some key findings regarding the
helper memory-bound kernels:
* Lack of vectorization: In kernels such as `expandInputRowsKernel` and
`doActivationKernel`, vectorization is not actually enabled. The
generated SASS shows occurrences of four contiguous `LDG.E` instructions
rather than a single `LDG.E.128`.
* Inactive warp: The `doActivationKernel` is currently hardcoded to use
256 threads per row. For workloads with small intermediate sizes, this
can be excessive and can result in inactive warps and suboptimal
occupancy.

### Changes Made

This PR improves the performance of the CUTLASS fused MoE
input-expansion and activation kernels.
* Explicitly vectorize global/store in `expandInputRowsKernel` and
`doActivationKernel`.
* This did not work on `finalizeMoeRoutingKernel` as it was observed to
increase register usage and did not improve perf.
* Select the activation kernel block size based on the work required per
row, which reduces inactive warps and improves occupancy for smaller
intermediate dimensions (e.g., 768 for `Qwen/Qwen3-30B-A3B`). Also, cap
the grid size 8~32 blocks (which was constantly 8) per SM based on block
size. This limits unnecessary warp-scheduling pressure.

## 🔍 Related Issues

<!-- Link any related issues here -->

#3521

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

## ⚡ Performance

### SASS verification (SM100, CUDA 13.2)

| row-data access | before (main) | after (this PR) |
|---|---|---|
| expandInputRows (bf16→bf16), per 16B copy | 4× `LDG.E` + 4× `STG.E` |
1× `LDG.E.128` + 1× `STG.E.128` |
| doActivation (bf16, Swiglu), per 16B of fc1/linear/bias | 4× `LDG.E`
each | 1× `LDG.E.128` each |
| doActivation (fp8 out, Swiglu), per 32B gemm vector | 8× `LDG.E` | 2×
`LDG.E.128` |
| doActivation (nvfp4 out, Swiglu), fp4 output + SF | unchanged (`STG.E`
packed + `STG.E.U8`) | unchanged |

### benchmarks/flashinfer_benchmark.py

#### Setup
* Single B100 (SM100), clocks locked at 1400 MHz SM / 4000 MHz mem, CUDA
13.2
  * Autotune off so both builds run identical default GEMM tactics
  * Baseline = main @ 2e97a607d
  * Cell = median of per-pair speedups

#### Result
* Achieved up to 1.08x end-to-end speedup
* No regression observed

| case | M=1 | M=16 | M=128 | M=512 | M=2048 | M=8192 | M=16384 |
|---|---|---|---|---|---|---|---|
| qwen3_tp1 | 1.00x | 0.99x | 1.00x | 0.99x | 1.02x | 1.04x | 1.05x |
| qwen3_tp2 | 1.01x | 1.00x | 1.01x | 1.01x | 1.04x | 1.05x | 1.05x |
| qwen3_tp4 | 1.00x | 1.00x | 1.01x | 1.01x | 1.04x | 1.04x | 1.05x |
| qwen3_tp2_fp8 | 1.00x | 1.03x | 1.00x | 1.02x | 1.02x | 1.04x | 1.05x
|
| qwen3_tp4_fp8 | 1.00x | 1.00x | 1.01x | 1.03x | 1.06x | **1.07x** |
**1.07x** |
| dsv3_nvfp4 | 1.01x | 1.03x | 1.04x | 1.06x | **1.08x** | 1.01x | 1.05x
|
| mixtral_tp4 (guard) | 1.00x | 1.00x | 1.00x | 1.00x | 1.01x | 1.02x |
1.01x |

### vLLM end-to-end benchmarking on H200x8

#### Setup

```
vllm bench throughput --model Qwen/Qwen3-30B-A3B --dataset-name random --moe-backend <backend> -tp <tp>
```

#### Result

| TP | main | this PR | gain | vs triton backend |
|---:|---:|---:|---:|---:|
| 1 | 41.52 | 42.09 | **+1.4%** | +1.5% |
| 2 | 60.92 | 61.69 | **+1.3%** | −3.3% (was −4.5%) |
| 4 | 69.36 | 71.51 | **+3.1%** | ~parity |
| 8 | 74.17 | 75.74 | **+2.1%** | −2.4% |

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Improved Mixture-of-Experts processing with vectorized memory
operations for quantized, unquantized, and FP8 data paths.
* Optimized activation workload distribution, memory access, and scaling
across available GPU resources.

* **Bug Fixes**
* Added validation for memory alignment in MoE inputs, outputs, and
biases.
* Improved rounding utilities to support a broader range of integral
values.

* **Tests**
* Added regression coverage confirming that improperly aligned inputs
produce a clear diagnostic.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Haobin Guo <haobing@nvidia.com>

### [78e463b](https://github.com/flashinfer-ai/flashinfer/commit/78e463b874df7266cfe6e21517812ebff66d1660)

- **作者**: Shanli Xing
- **时间**: 2026-08-11T08:03:29Z
- **提交信息**: perf(cake_tinygemm2): add a STAGES=16 kernel tier for single-wave large-K shapes (#4423)

## 📌 Description

Adds a third ring-depth tier to the `tinygemm2_sm100` family (#4274) and
moves ring selection into the binding. All six kernels are regenerated
from
the current CAKE generator state, which also updates the tensor-map
parameter passing to a single by-value `__grid_constant__` pack.

- **New STAGES=16 ring for single-wave large-K shapes.** The 4/8-stage
rings were tuned for K up to ~4K; at larger K the 8-deep ring no longer
covers the weight-stream latency when the working set is not
L2-resident,
and trails the reference kernel's own 16-deep configuration. The new
tier
closes that: at N=8/M=128/K=7168 (bias path) it measures **4.93 µs vs
the
reference's 5.22 µs on GB300, and 5.31 µs vs 5.56 µs on B200** (cold-L2
  CUPTI).
- **Ring selection in the binding**, following the reference
`csrc/tinygemm2.cu` launcher convention: stage 4 for K <= 1024 or grids
  past 2x the SM count (unchanged), stage 16 for single-wave grids with
K >= 4608 (measured crossover on both GB300 and B200), stage 8
otherwise.
  The Python dispatcher becomes a single call into the combined op.
- **Dispatch gates on exact compute capabilities (10, 0)/(10, 3).**
SM107
passes the previous `major == 10` predicate but must keep the reference
  path instead of erroring in the binding.
- The dynamic-SMEM attribute is now set once per (kernel, device)
instead
  of on every launch.

**Correctness contract unchanged: bitwise equality with
`csrc/tinygemm2.cu`** — verified per-variant and through the dispatcher
(`torch.equal`, batch 1-64, K to 7168, M to 4096, on B200 and GB300),
and
end-to-end in SGLang serving with zero token flips (gpt-oss-120b, and
Mistral-Large-3 whose router GEMM sits in the new tier).
`tests/model_optimizations/test_tinygemm2_sm100.py` extends to the
stage-16
variants and long-K parity shapes. compute-sanitizer synccheck is clean
on
all six variants.

Limitations: unchanged from #4274 — the nobias path stays on the
reference
kernel.

## 📊 End-to-end serving validation — Mistral-Large-3 (675B FP8), SGLang,
TP4, GB300

(CUDA graphs on, production defaults)

**Correctness**: 32 fixed greedy prompts — token streams bitwise
identical between arms; GSM8K-200: CAKE 0.950 / ref 0.945.

**Performance** (CAKE = this PR's kernels via default dispatch, ref =
reference `tinygemm2`; throughput in mean output tok/s, ITL is median in
ms):

| concurrency | throughput (CAKE) | throughput (ref) | ITL (CAKE) | ITL
(ref) |
|---|---|---|---|---|
| 1 | 100.7 | 101.0 | 9.47 | 9.48 |
| 8 | 488.6 | 487.9 | 15.47 | 15.48 |
| 32 | 1068 | 1073 | 28.90 | 28.92 |
| 128 | 3000 | 2997 | 41.31 | 41.44 |

## 🔍 Related Issues

Follow-up to #4274. Related to #4254 (CAKE-generated kernel progress
tracker).

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

## Reviewer Notes

The generated device sections are frozen artifacts (regeneration happens
outside this repo, as with #4262/#4274); review focus is best spent on
the
binding section of `csrc/tinygemm2_sm100.cu` (pack construction, stage
selection, launch attributes), the dispatcher in
`flashinfer/gemm/routergemm.py`, and the test additions. The single-TU
merge follows the mechanical transform documented in the file header.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for larger matrix workloads through new stage16
execution variants.
* Automatically selects the appropriate execution stage based on
workload size and hardware.
  * Added direct launch support for all available execution variants.
* Expanded compatibility for supported compute capabilities and newer
CUDA versions.

* **Bug Fixes**
  * Improved handling of large reduction sizes and deep-ring workloads.

* **Tests**
* Added coverage for larger K dimensions, including 7168 and 14336, and
stage16 variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3939
- **最后更新**: 2026-08-11T22:04:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34287
- **最后更新**: 2026-08-11T22:18:05Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, Funtowicz Morgan

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **功能新增**：LTX-2.4模型支持（核心更新）
- **文档更新**：NVIDIA Spark (ARM64)设备安装说明

### 2. 关键变更点
- **LTX-2.4支持**：复用现有LTX2模型和pipeline类，通过新增配置标志实现版本差异，包括`ff_bias`/`audio_ff_bias`（控制视频FFN偏置）和`use_prompt_adaln_single`（切换时间步依赖的提示词交叉注意力调制）
- **文本编码器升级**：从Gemma 3切换到Gemma 4，LTX-2.4的微调编码器仅用于条件生成，需借助独立的google/gemma-4-E2B-it检查点进行提示词增强
- **提示词增强功能扩展**：将原本仅T2V支持的`prompt_enhancer`组件扩展到I2V pipeline，并优化了GPU内存释放逻辑

### 3. 项目影响与意义
- **架构一致性**：通过配置标志而非新建类的方式支持新版本，保持了代码库的简洁性和可维护性，符合diffusers作为统一扩散模型库的定位
- **生态适配**：紧跟LTX系列模型迭代，确保HuggingFace生态对最新视频生成模型的支持
- **硬件覆盖**：新增ARM64设备安装说明，扩大了对边缘计算和低功耗设备的支持范围

### 4. 值得关注的技术点
- **缓存优化**：`use_prompt_adaln_single`关闭时，交叉注意力K/V可跨去噪步骤缓存，这是对视频生成性能的重要优化
- **内存管理**：增强器使用后立即释放GPU内存，且与accelerate卸载钩子兼容，体现了对资源效率的精细考量
- **向后兼容**：所有新参数默认保持2.3行为，确保现有用户无感升级

### 5. 对项目发展的影响
diffusers作为HuggingFace核心的生成模型库，此次更新体现了其**快速跟进前沿模型**的策略。通过灵活的配置机制支持模型版本迭代，而非频繁重构，有助于维持庞大的用户基础。同时，对ARM64设备的支持反映了项目向**多平台覆盖**和**边缘部署**方向拓展的意图。LTX-2.4的提示词增强机制分离，也展示了项目在处理复杂多模态模型时的工程化思维——将不同职责的组件解耦，便于灵活组合和资源管理。整体上，这些提交巩固了diffusers在视频生成领域的领先地位，并为后续更多LTX系列模型的集成铺平了道路。

## 详细提交记录

### [175fe6b](https://github.com/huggingface/diffusers/commit/175fe6b2419a01db9c2ceabd01ec37d2c0305fc2)

- **作者**: Funtowicz Morgan
- **时间**: 2026-08-11T22:17:59Z
- **提交信息**: docs: add installation instructions for NVIDIA Spark (ARM64) devices (#14448)

### [7564fb0](https://github.com/huggingface/diffusers/commit/7564fb016dabda0c943416190fc92398c50b1b20)

- **作者**: Sayak Paul
- **时间**: 2026-08-11T17:10:00Z
- **提交信息**: Ltx 2.5 (#14447)

* Add LTX-2.4 support to the LTX2 transformer, pipelines, and conversion script

LTX-2.4 reuses the existing LTX2 model and pipeline classes. The delta over
2.3 is a small set of additive config flags plus a Gemma 3 -> Gemma 4 text
encoder swap, so no new model or pipeline classes are introduced.

- transformer_ltx2.py: add `ff_bias`/`audio_ff_bias` (2.4's video FFN drops
  its bias) and `use_prompt_adaln_single` (toggles timestep-dependent prompt
  cross-attention modulation; when off, cross-attention K/V becomes
  timestep-independent and cacheable across denoising steps for a given
  prompt). Both default to their 2.3 behavior. The flag is read back from
  `self.config` rather than mirrored onto an instance attribute, and all
  three new constructor args are documented.

- pipeline_ltx2.py / pipeline_ltx2_image2video.py: add an optional
  `prompt_enhancer` component to both pipelines (previously T2V-only).
  LTX-2.4's fine-tuned text encoder is conditioning-only, so enhancement
  uses a separate off-the-shelf google/gemma-4-E2B-it checkpoint with its
  own message format and decoding recipe -- unlike LTX-2.0/2.3, where one
  checkpoint serves both roles. `enhance_prompt()` resolves the format and
  `.generate` kwargs from whichever model is active, and frees a dedicated
  enhancer from GPU memory right after use (guarded so it does not interfere
  with accelerate's offload hooks), mirroring the existing text_encoder
  handling.

  Both `__call__`s gain `enable_prompt_enhancement: bool | None = None`,
  which resolves to `True` when a dedicated `prompt_enhancer` is configured
  (LTX-2.4) or when `system_prompt` was passed explicitly (matching prior
  LTX-2.0/2.3 behavior exactly), and `False` otherwise. Explicit `False`
  disables enhancement even on 2.4. When enabled with no `system_prompt` on
  a 2.4 pipeline, the matching default system prompt is injected.

  `max_new_tokens`/`seed` keep their literal defaults (512/10)
  unconditionally: greedy decoding consumes no randomness, so `seed` is
  inert for the dedicated-enhancer case, and 512 tokens comfortably covers
  the target caption length. No public API or default changes were needed
  for LTX-2.0/2.3.

  Validation of the enhancement arguments happens in `check_inputs`, so an
  unsatisfiable request fails before the prompt is encoded rather than
  partway through generation. Text encoder, tokenizer, processor and
  enhancer type hints name the concrete Gemma classes they accept.

- utils.py: add a `PromptEnhancementConfig` dataclass plus
  `GEMMA3_PROMPT_ENHANCEMENT_CONFIG`/`GEMMA4_PROMPT_ENHANCEMENT_CONFIG` as
  the single source of truth for each model's message prefix and `.generate`
  kwargs, shared by both pipelines. Add the validated "capstyle_plus"
  LTX2_4_T2V/I2V_DEFAULT_SYSTEM_PROMPT strings, marked `docstyle-ignore` so
  `doc-builder style` cannot re-wrap them -- the prompts must stay
  byte-for-byte identical to the reference, newlines included.

- convert_ltx2_to_diffusers.py: add a "2.4" branch to all five
  get_ltx2_*_config functions. Transformer/VAE/vocoder configs are
  structurally identical to 2.3 (verified against the checkpoint's own
  safetensors metadata); only `ff_bias=False` differs. Connector
  `caption_channels`/`text_proj_in_factor` are now derived from the live
  Gemma text config rather than hardcoded, since 2.4's text encoder is not
  pinned to a single checkpoint the way Gemma-3-12B is for 2.0/2.3. Swap
  `Gemma3ForConditionalGeneration`/`Gemma3Processor` for
  `AutoModelForImageTextToText`/`AutoProcessor` so one path covers Gemma 3
  and Gemma 4. Raise a clear error when --version 2.4 is requested without
  pointing --text_encoder_model_id at a Gemma 4 (gemma4_unified) checkpoint,
  and add --prompt_enhancer_model_id, required whenever --version 2.4 is
  combined with --add_processor, since falling back to
  --text_encoder_model_id (correct for 2.0/2.3) would pair 2.4 with the
  wrong enhancement model. Also fixes a pre-existing vocoder
  class-selection bug that only checked for "2.3", and `processor` never
  being passed into the --full_pipeline LTX2Pipeline(...) construction.

- docs/source/en/api/pipelines/ltx2.md: add an "LTX-2.4" section covering
  what carries over from 2.3 unchanged (guidance recommendations, aside
  from a different STG block index) and what does not (a single-stage
  checkpoint only, with no two-stage or distilled workflow yet), plus the
  corrected prompt-enhancement recipe and its enabled-by-default behavior
  for both LTX2Pipeline and LTX2ImageToVideoPipeline.

* Fix resolution-dependent timestep shift being a no-op in all LTX2 pipelines

Every LTX2Pipeline variant's `mu = calculate_shift(...)` call passed the
scheduler's `max_image_seq_len` config value as the `image_seq_len`
argument instead of the current generation's actual packed sequence
length. Since calculate_shift's formula is a line through
(base_seq_len, base_shift) and (max_seq_len, max_shift), passing
image_seq_len == max_seq_len always evaluates to exactly max_shift --
so `mu` was pinned to a constant (2.05 for the LTX-2.4 scheduler config)
regardless of height/width/num_frames, even though `use_dynamic_shifting:
true` is set specifically to make this resolution-dependent.

Found while benchmarking LTX-2.4 diffusers output against the reference
pipeline with bit-identical starting noise: the reference computes this
shift from the real video token count (ltx_core's LTX2Scheduler.execute),
which diverges substantially from the constant diffusers was using at
any resolution other than exactly the checkpoint's max-anchor token
count. For a 768x512, 121-frame video (6144 tokens), the reference lands
on mu ~= 2.78 versus diffusers' constant 2.05.

Fixed by passing the current call's actual packed video latent length
(`latents.shape[1]`) as `image_seq_len`, matching the pattern already
used correctly in pipeline_flux.py (the source this was copied from).
Applies to all 5 LTX2 pipeline variants, each with their own independent
`__call__` (not linked via `# Copied from` for this method).

* Add LTX-2.4 duration head for automatic num_frames prediction

LTX-2.4 checkpoints ship a small regression head (~1.9M params) that predicts
the natural duration of the shot implied by a caption, from the same text
connector output the transformer is conditioned on. With it converted, a caller
can let the model choose the video length instead of picking `num_frames`.

- duration_head.py: `LTX2DurationHead` (a `ModelMixin` optional pipeline
  component) plus the `LTX2AutoDuration` request object. Modality-specific
  projections map the video and audio connector streams into a shared pooler
  dim, learnable modality embeddings tag them, one learnable query cross-attends
  the concatenation, and a small MLP regresses a log-duration. `forward` returns
  seconds as a tensor; `predict_num_frames` clamps to bounds and snaps to the
  VAE's causal temporal grid.

  The attention pooler uses explicit to_q/to_k/to_v/to_out with
  `dispatch_attention_fn` rather than `torch.nn.MultiheadAttention`, which both
  reference implementations use because that is the layout the checkpoint ships.
  `nn.MultiheadAttention` is documented in diffusers as breaking
  `enable_sequential_cpu_offload`; the split form also gets backend dispatch.

  Two details are load-bearing for numerical parity: the GELU must be
  tanh-approximated (the exact GELU gives different numbers against the
  JAX-trained head), and the clamp must precede the grid snap (a clamped frame
  count is not necessarily grid-aligned). Where narrow bounds convert to a frame
  window containing no grid point -- at 24 fps [1.0s, 1.02s] rounds to [24, 24],
  and 24 is not 8k + 1 -- the nearest grid point is used and a warning logged,
  rather than refusing to generate over a rounding artifact.

  The output MLP's config argument is `mlp_hidden_dim`, not the reference's
  `mlp_hidden`: the submodule keeps the checkpoint's `mlp_hidden` name, and
  `ModelMixin.__getattr__` resolves config keys ahead of submodules, so the two
  colliding would shadow the `nn.Linear` with an `int`.

- pipeline_ltx2.py / pipeline_ltx2_image2video.py: `num_frames` becomes
  `int | LTX2AutoDuration | None`. Omitting it auto-predicts when the checkpoint
  ships a head and keeps the legacy 121 otherwise, mirroring the reference --
  whose CLI also defaults to auto-prediction -- and matching the resolution
  these pipelines already do for `enable_prompt_enhancement`, which likewise
  switches on the presence of an optional LTX-2.4 component. Pre-2.4 pipelines
  have no head, so nothing changes for them.

  The prediction runs immediately after the connectors and before `num_frames`
  is first read. Only the positive half of the CFG-concatenated batch is used,
  and rows past the first are `num_videos_per_prompt` duplicates.

  Auto-duration is rejected from `check_inputs` -- before prompt enhancement and
  encoding, so a bad request costs nothing -- when there is no head, and when
  more than one prompt is supplied: the batch carries a single temporal
  dimension, so prompts with different natural lengths cannot share one frame
  count. Batched prompts with an explicit integer `num_frames` are unaffected.

- convert_ltx2_to_diffusers.py: `--duration_head` (with
  `--duration_head_prefix`) alongside the other per-component flags. The head's
  keys sit at the checkpoint top level rather than under the DiT prefix, so the
  existing prefix helper handles them. The checkpoint's fused `in_proj_weight`
  is split into separate q/k/v, and dimensions are read back from weight shapes
  since checkpoint metadata carries no duration_head config; only
  `num_pooler_heads` is not recoverable and is fixed at 4. Pre-2.4 checkpoints
  yield no keys and are skipped rather than failing.

Verified against ltx_core on the real 2.4 checkpoint: fed the reference's
recorded connector tokens, the converted head predicts 12.9375s (video only),
2.671875s (audio only) and 3.515625s (both) -- bit-identical to the reference --
and the same frame counts through the clamp/snap path at 24/25/30/8 fps. The
snapping arithmetic matches the reference `seconds_to_clamped_num_frames` across
260 combinations of duration, frame rate and bounds.

* Add LTX-2 modular video and audio decoder blocks

Add the first blocks of the LTX-2 modular pipeline under
modular_pipelines/ltx2/decoders.py:

- LTX2VaeDecoderStep: unpacks and decodes video latents (or returns
  latents for output_type="latent"), applying the optional decode-time
  noise on normalized latents before denormalizing, matching the
  standard LTX2Pipeline decode stage.
- LTX2AudioDecoderStep: unpacks and decodes audio latents into a
  waveform via the audio VAE and vocoder in a single block.

Pack/unpack/denormalize helpers are redefined at module level rather
than imported, since modular blocks must not import from
diffusers.pipelines.* (the vocoder class is imported from the pipelines
path for now, flagged for relocation to models/).

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Add LTX-2 modular pipeline (t2v + i2v) and parity harnesses

Add the LTX-2 modular pipeline package under modular_pipelines/ltx2/,
covering the joint video+audio text-to-video and image-to-video
workflows for LTX-2.4:

- encoders.py: dedicated Gemma-4 prompt enhancer (t2v/i2v), Gemma text
  encoder, text connectors, and the i2v image VAE encoder.
- before_denoise.py: text-input expansion, flow-match timesteps (with a
  deep-copied audio scheduler), video/audio latent prep, and RoPE coords.
- denoise.py: the joint video+audio denoise loop with manual guidance
  (CFG + spatio-temporal + modality-isolation), shared across t2v/i2v.
- decoders.py: video VAE decode and audio VAE + vocoder decode.
- modular_blocks_ltx2.py: LTX2Blocks (t2v), LTX2ImageToVideoBlocks (i2v),
  and LTX2AutoBlocks (both, default), plus the auto/conditional wrappers.
- modular_pipeline.py: LTX2ModularPipeline with the compression-ratio and
  patch-size properties the blocks read.

Wire up lazy imports and register the pipeline (top-level diffusers
exports, modular_pipelines __init__, MODULAR_PIPELINE_MAPPING, and dummy
objects).

Also add integrations/ (temporary, for-visibility) parity harnesses that
compare the modular t2v/i2v blocksets against the standard LTX-2
pipelines by sharing the same loaded components. This directory is meant
to be removed before the final integration.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Add script to create tiny LTX-2.4 test pipeline ckpt (under assumption that it inherits all configs from LTX-2.3)

* make fix-copies

* Run modular connector once on CFG-concatenated batch for bitwise parity

Run the LTX-2 text connector once on the CFG-concatenated `[uncond, cond]`
batch (as `LTX2Pipeline` does) instead of once per branch, then split the
outputs back into uncond/cond. The connector is applied per batch element, so
both forms are mathematically equivalent, but its GEMM/attention kernels round
identically for a given row only at batch >= 2; running the branches separately
diverged from the standard pipeline by ~1e-6 at `num_videos_per_prompt=1`. The
modular path is now bitwise-identical to the standard pipeline at any batch size.

Also extend the T2V/I2V parity harnesses with a `--num_videos_per_prompt`
argument and a `--check_tensor_stats` flag for per-output min/mean/std/max.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Use tiny LTX2VocoderWithBWE in the LTX-2.4 test checkpoint

Swap the placeholder LTX2Vocoder for a scaled-down LTX2VocoderWithBWE that
mirrors LTX-2.3's vocoder (snakebeta + antialiasing, no final activation/bias,
16kHz -> 48kHz bandwidth extension) while keeping the same in/out channel
shapes. Dimensions are reduced but the shape invariants the two-stage forward
requires are preserved: in_channels = audio_vae.output_channels * mel_bins,
bwe_in_channels = out_channels * num_mel_channels, filter_length == window_length,
and prod(bwe_upsample_factors) == (output_sr // input_sr) * hop_length so the BWE
residual and the resampled stage-1 skip line up.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Match LTX-2.4 transformer flags in the test checkpoint

Only `ff_bias=False` is a transformer-level delta from LTX-2.3 per the
authoritative LTX-2.4 config in `scripts/convert_ltx2_to_diffusers.py`;
`audio_ff_bias` and `use_prompt_adaln_single` keep their `True` defaults.
The test checkpoint was incorrectly overriding both to `False`, so drop
those two overrides. T2V/I2V modular-vs-standard parity remains bitwise.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Add CPU offload flag to parity scripts to be able to load full checkpoints

* Support dynamic timestep shift and duration head in LTX-2 modular pipeline

Track two recent additions to the standard LTX-2.4 pipelines in the
modular blocks (t2v + i2v):

- Resolution-aware timestep shift: LTX2SetTimestepsStep now computes `mu`
  from the actual packed video sequence length (derived from
  height/width/num_frames and the transformer patch sizes) instead of a
  constant, matching the standard pipeline's `latents.shape[1]`-based
  shift. Uses the compute-from-dims approach (like LTX-1 / Flux2), so no
  block reordering is needed.

- Optional duration head: add LTX2DurationStep, which predicts a concrete
  `num_frames` from the connector text conditioning via the `duration_head`
  component when `num_frames` is an `LTX2AutoDuration` request, and
  re-emits it. Wrapped in the LTX2AutoDurationStep conditional (skipped for
  an integer `num_frames`) and wired into all three blocksets after the
  connector step, so `num_frames` is resolved before the shift and latent
  prep run.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Add duration predictor support for tiny checkpoint and parity scripts

* Refactor LTX-2 modular guidance into video/audio guiders

Replace the manual multi-term guidance in `LTX2LoopDenoiser` with a
`LTX2Guidance` guider (in `guider.py`), instantiated once as the video
`guider` and once as the `audio_guider`. Each combines CFG + spatio-temporal
guidance (STG) + modality-isolation via the delta formulation in x0 space; the
denoiser owns a `plan_guidance_passes` union plan across the two guiders, runs
each transformer pass, converts velocity->x0, and delegates the per-modality
combine to the guiders. Guidance scales are now guider config, not `__call__`
kwargs. Parity harnesses updated to configure the guiders accordingly.

Parity investigation (not yet resolved):
- The refactor runs every guidance pass as its own single-batch transformer
  forward, whereas the standard `LTX2Pipeline` batches the cond+uncond CFG pair
  into one forward and runs STG/modality-isolation as separate single-batch
  passes. STG and modality already match (single-batch in both).
- The change is mathematically equivalent, not a logic bug: in fp32 the
  denoised latents match to ~8e-6 mean abs diff (sparse outliers up to
  ~3.5e-4), and disabling STG does not move the diff.
- But GPU matmul is not batch-invariant, so cond computed alone differs from
  cond computed inside a batch-of-2. Negligible in fp32 (~1e-6/op); ~1e-2/op in
  bf16, where amplification by the CFG delta and accumulation over sampler steps
  drives the modular vs. standard bf16 latents to ~10% mean-relative divergence.
- Net: numerical, but the modular pipeline does NOT reproduce the standard
  pipeline bitwise in bf16 (the real inference dtype). Restoring parity would
  require re-batching the cond+uncond pair into a single forward to match the
  reference execution, keeping STG/modality single-batch.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Batch cond+uncond CFG forward to mirror standard LTX-2 pipeline

Restore fp32 bitwise parity with `LTX2Pipeline` in the modular denoiser by
running the cond+uncond CFG pair as a single batched transformer forward
(`torch.cat([latents] * 2)` + `.chunk(2)`), keeping STG and modality-isolation
as separate single-batch conditional forwards -- matching the reference
op-for-op (batch sizes, repeated coords, cache-context names).

`plan_guidance_passes` now emits forward-groups (`identifiers` / `conditioning`
aligned lists + `flags` + `cache_context`) instead of one entry per pass; the
denoiser runs each group once and chunks the CFG forward back into its
`[uncond, cond]` identifiers. The `LTX2Guidance` combine is unchanged -- only
how the four x0 tensors are obtained changed.

Parity results:
- fp32: bitwise (0.0 max abs diff), verified at full-checkpoint scale including
  under CPU offload. This is the authoritative parity gate.
- bf16: the previous single-batch-per-pass design diverged ~10% mean-relative
  from the standard pipeline (GPU matmul is not batch-invariant: cond alone vs.
  cond in a batch-of-2). Batching the CFG pair removes that gap; a smaller
  ~1% (tiny) / ~5% (full) bf16 gap remains. It is not a logic difference (fp32
  is bitwise across scale and offload); it is a bf16-kernel effect -- coarser
  mantissa amplifying non-associative accumulation order, plus bf16 using
  different kernels than fp32 (tensor-core GEMM algorithm selection, fused
  attention). bf16 is therefore a close-but-not-bitwise check, not a gate.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Drive LTX-2 modular guidance through the guider API (per-pass inputs)

Replace the batched-CFG denoiser with one that runs each guidance pass as its
own single-batch transformer forward, driven end-to-end through the standard
guider API. `LTX2Guidance.prepare_inputs(guider_inputs)` builds one identifier-
tagged batch per active pass from a dict whose values are 4-tuples indexed by
pass [cond, uncond, stg, modality]; the per-pass model flags
(`spatio_temporal_guidance_blocks`, `isolate_modalities`) ride in those tuples
alongside the encoder inputs, so a pass fully describes its own forward. The
denoiser unions both guiders' passes by identifier, runs each once (storing
video+audio x0 on the batch), and combines each modality via its guider's
`forward`/`__call__`, filtered to that guider's active passes so the batch count
matches `num_conditions`.

Removes the bespoke `plan_guidance_passes` union helper and the empty-dict
`prepare_inputs_from_block_state` call: the plan is now expressed as the
`guider_inputs` tuples + `active_predictions()`, so guidance logic lives behind
the guider API rather than in the denoiser.

Parity trade vs. the previous batched-CFG design:
- Batched CFG matched the standard pipeline op-for-op and was fp32-bitwise.
  Running every pass single-batch is mathematically equivalent but, since GPU
  matmul is not batch-invariant, cond computed alone differs from cond inside a
  batch-of-2: ~1e-4 mean-relative in fp32 on a full checkpoint (sparse outliers
  up to ~3.5e-4 max), ~10% mean-relative in bf16.
- This is numerical, not a logic difference, and fp32-within-tolerance (not
  bitwise) is the modular-ecosystem norm. The trade buys end-to-end guider-API
  usage (swappable within the LTX-2 guidance family, per-pass flags carried the
  same way as encoder inputs) at the cost of the bitwise guarantee.

Parity harnesses: gate on magnitude-aware stats (mean abs diff relative to mean
magnitude, plus a loose max-abs ceiling) instead of assert_close's near-bitwise
fp32 defaults, which no single-batch design can clear. fp32 is the authoritative
gate (1e-3/1e-3); bf16 is a loose sanity check (0.15/0.5). `--atol`/`--rtol`
become `--mean_rel_tol`/`--max_abs_tol`; motivation documented in-file.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Drive LTX-2 modular guidance via prepare_inputs_from_block_state

Move `LTX2LoopDenoiser` onto the standard Wan/Z-Image guider idiom: the
denoiser now owns a `guider_input_fields` map (transformer arg -> per-pass
block-state attribute names, indexed [cond, uncond, stg, modality]) and calls
`guider.prepare_inputs_from_block_state(block_state, guider_input_fields)`
instead of hand-building a literal `guider_inputs` dict in `__call__`. This
lifts the cond/uncond/stg/modality field mapping to a construction-time arg
(swappable per workflow) and resolves the connector_*->encoder_hidden_states
name mismatch via the map keys.

The two per-pass model flags (`spatio_temporal_guidance_blocks`,
`isolate_modalities`) are pass-identity constants, not block-state
conditioning, so they can't ride the name-referenced field map; the denoiser
sets them on each batch by identifier after preparation, via a
`pass_flags.get(identifier, (None, False))` lookup. The plain-conditional
default keeps this correct for any guider that emits a subset of passes (e.g.
a swapped-in `ClassifierFreeGuidance` -> just pred_cond/pred_uncond gets no STG
and no modality isolation).

`LTX2Guidance` gains `prepare_inputs_from_block_state` (names, via the base
`_prepare_batch_from_block_state` helper); `prepare_inputs` (literals) is
retained so both halves of the guider data-prep API are implemented. Pass
structure and numerics are unchanged (still four single-batch forwards), so the
fp32/bf16 parity story is untouched; user-confirmed parity OK.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Route LTX-2 batch-invariant denoiser kwargs via denoiser_input_fields

Tag the three upstream-produced, batch-invariant transformer kwargs
(`audio_num_frames` from the audio-latents step; `video_coords` / `audio_coords`
from the coords step) with `kwargs_type="denoiser_input_fields"`, and have
`LTX2LoopDenoiser` collect them from `block_state.denoiser_input_fields` filtered
against the transformer's forward signature (à la qwenimage/cosmos3) instead of
listing them as explicit inputs. This drops three explicit `InputParam`s in favor
of one `denoiser_input_fields` template input.

Per-pass conditioning (cond/uncond/stg/modality) stays on the guider field map --
the tag only delivers a flat dict, so it can't do the cond/uncond split or the
connector_*->encoder_hidden_states rename. The locally-computed latent dims
(num_frames/height/width/fps) are still supplied in-denoiser: they aren't upstream
outputs and their names would clash with the pixel-space values in state.

Parity unchanged (validated T2V + multi-frame I2V): the tagged values reach the
transformer identically; the first-forward capture shows them bitwise-equal.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Fix LTX-2 parity harnesses: guidance overrides reach both pipelines

The CLI guidance flags (`--guidance_scale`, etc.) only fed the modular guiders;
the standard pipeline was always called with the hardcoded GUIDANCE dict. So
`--guidance_scale 1.0` disabled CFG on the modular side only, comparing
standard-with-full-CFG (batch-2) against modular-no-CFG (batch-1) -- an
apples-to-oranges run that manifested as a huge (but spurious) I2V mismatch.

Add `_resolve_guidance(args)` (CLI overrides on top of GUIDANCE) and drive BOTH
the standard call and `_make_guiders` from the one resolved dict, in both the t2v
and i2v harnesses. With CFG correctly disabled on both sides, multi-frame I2V is
bitwise-ish (~5e-6 mean-rel), confirming the default-guidance ~8e-3 divergence is
the documented cond/uncond batch-invariance (amplified by I2V's per-token masked
timestep + clean anchor frame), not a logic bug.

Also:
- i2v: loosen the fp32 gate to (2e-2, 1.5e-1) to fit that amplified-but-numerical
  multi-frame divergence, with a comment pointing at the CFG-off run as the tight
  bug-catching gate.
- i2v: add `--debug_forward`, which diffs the first transformer forward
  (inputs + outputs) between the two runs via a forward hook -- the diagnostic
  that pinpointed the batch-shape mismatch above.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Document denoiser_input_fields standalone-run caveat for LTX-2 denoiser

`audio_num_frames` / `video_coords` / `audio_coords` reach `LTX2LoopDenoiser`
via the `denoiser_input_fields` tag, not as named inputs. Note in the docstring
that a standalone run (without the upstream tagging blocks) must pass them
through `denoiser_input_fields={...}`; plain named kwargs are silently ignored
(modular.md's kwargs_type standalone gotcha).

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Address LTX-2 modular self-review: fix dead enhancer trigger + docstrings

Blocking fix: `enable_prompt_enhancement` was declared only as a
`block_trigger_inputs` entry / `select_block` param, never as an `InputParam`,
so it was not an accepted pipeline input -- `pipe(enable_prompt_enhancement=True)`
was dropped as "unexpected" and the prompt enhancer could never run. Declare it
on both enhancer sub-blocks so it reaches `select_block` (mirrors how the `image`
trigger is declared).

Also from the self-review:
- Regenerate the modular auto-docstrings: the guidance knobs (guidance_scale,
  stg_scale, ...) that moved onto the guider no longer show as block inputs, and
  the enhancer trigger now appears.
- Add descriptions to the 16 `InputParam`s that rendered as "TODO: Add
  description." in the generated docstrings (conversion checklist requires none).
- Drop the defensive `getattr(tokenizer, "padding_side", "left")` (a declared
  tokenizer always has it; gotcha #7).
- Rewrite two ephemeral comments (the connector-output "reconcile when denoise.py
  is written" NOTE, now resolved; the guider "batched-CFG variant in git history"
  pointer) into standing rationale.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Fix stale I2V parity-harness --help text for the loosened fp32 gate

The `--mean_rel_tol` / `--max_abs_tol` help strings still advertised the old
fp32 defaults (1e-3, 1e-3); the I2V gate is now (2e-2, 1.5e-1). Update the help
to match the actual DTYPE_TOLERANCES so `--help` doesn't misreport the gate.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* make style and make quality

* Add the LTX-2.4 diffusion VAE decoder with a native-parity harness

* Add a converter for the LTX-2.4 diffusion VAE decoder

* Initialise use_slicing and document the diffusion VAE decisions

* Record real-weight parity against the reference decoder

* Add model-level tests for the LTX-2.4 diffusion VAE decoder

The generated test file needed three decisions rather than fill-ins: the class had no forward() for the
mixins to call, the decoder denoises so forward has to take a generator for any output comparison to mean
anything, and MemoryTesterMixin.test_group_offloading reused one inputs_dict across four forwards without
re-seeding it. The last is fixed in the mixin, reusing the helper test_group_offloading_with_disk already
had for the same reason, now module-level and reading the signature off the class (offloading replaces
model.forward with a *args wrapper).

* Fold the diffusion VAE converter into convert_ltx2_to_diffusers.py

--diffusion_vae now sits beside --vae instead of shipping a second script. It also drops the standalone
script's --encoder-vae: the encoder is in the same checkpoint and goes through the conv VAE's own rename
rules, with its config pinned in get_ltx2_diffusion_video_vae_config. Output verified bitwise identical to
the standalone script's on the rc2 checkpoint, 491/491 tensors and the same config.json.

* Make the diffusion decoder work through LTX2Pipeline

The documented usage -- LTX2Pipeline.from_pretrained(repo, vae=diffusion_vae) -- had never been run: every
real-weight run so far called vae.decode() directly. Through the pipeline it raised on
vae.config.timestep_conditioning, which this decoder has no reason to carry, and would have bound the
positional decode timestep to the decoder's generator. The decode step now branches on the decoder type,
skipping the decode_timestep pre-noising and passing the generator instead, which also makes decoding
seed-reproducible; two full runs from one seed agree bitwise. The conv path's own statements are unchanged.

* Make the diffusion decoder work through the modular decode step

Same fix as the standard pipeline, in LTX2VaeDecoderStep: skip the decode_timestep pre-noising and pass the
generator instead of a timestep. Verified on rc2 weights by injecting the decoder into
LTX2Blocks().init_pipeline() with update_components, the route the modular parity harness already uses -- two
runs at 320x448x17 from one seed agree bitwise, so no modular_model_index.json repo was needed to run this.

* Note that the pipeline decode block predates the LTX-2.4 integration PR

* Address diffusers self-review on the diffusion VAE decoder

Four things the project's own rules catch:

- models.md forbids unconditional torch.float64 in a model (MPS/NPU/Neuron cannot run it). The RoPE
  frequency base now goes through maybe_adjust_dtype_for_device, the helper flux/flux2/wan use for exactly
  this. Measured cost of the downcast where it applies: 1.5e-08 on the frequencies, 1e-06 on the angles.
- rope_dim_split was threaded through five classes but was never a config entry, so it was always None and
  always fell back to the default split. Removed, and the default-split helper inlined into its one caller.
- FromOriginalModelMixin was declared with no SINGLE_FILE_LOADABLE_CLASSES entry, so from_single_file raised
  rather than working. Dropped; single-file support can come with its own mapping later.
- set_attention_backend() overwrites the processor's _attention_backend, which handed the neighborhood
  BlockMask to backends that cannot read it. Guarded like AnyFlowCausalAttnProcessor does.

Also runs make fix-copies, which was missing the dummy object for the new class.

* Add the API doc page for AutoencoderKLLTX2VideoDiffusionDecoder

* Mark the parity harness transient and drop the notes doc from the diff

Matches the header the other integrations/ harnesses on this branch already carry, and states that the file
imports the native reference package. The notes doc goes to the PR description instead: the self-review skill
is explicit that it never ships in the diff.

* Accept the diffusion decoder in the image-to-video pipeline too

Same branch as the text-to-video pipeline: skip the decode_timestep pre-noising and pass the generator instead
of a timestep. The remaining LTX2 pipelines that share this decode block (condition, hdr_lora, ic_lora,
latent_upsample) are deliberately left for later, so the surface stays the two pipelines this PR actually
exercises.

* Reorganize LTX-2 modular blocks into coarser component-aligned phases

Regroup the top-level LTX-2 block assemblies so each direct child of
LTX2AutoBlocks is a coherent, component-aligned phase, mirroring Flux 2's
[text_encoder, vae_encoder, denoise, decode] shape:

- New LTX2TextConditioningStep wraps [text_encoder, text_input, connectors] as
  one "text_encoder" phase (LTX-2's text conditioning is genuinely a three-step
  model chain; text_input must precede connectors for batch-invariant parity, so
  the whole chain lives here rather than pushing text_input into denoise).
- New LTX2DecoderStep wraps [video_decode, audio_decode] as one "decode" phase.
- duration stays a top-level child: it is component-aligned (duration_head) and a
  ConditionalPipelineBlocks that self-skips for concrete num_frames, so it is a
  cleanly optional phase alongside prompt_enhancer / vae_encoder -- keeping it
  out of the (mandatory) denoise block.

Top-level children become:
  t2v:  [text_encoder, duration, denoise, decode]
  i2v:  [text_encoder, duration, vae_encoder, denoise, decode]
  auto: [prompt_enhancer, text_encoder, duration, vae_encoder, denoise, decode]

Also reorder the class definitions to follow this flow, keeping the core-denoise
trio (LTX2CoreDenoiseStep, LTX2Image2VideoCoreDenoiseStep, LTX2AutoCoreDenoiseStep)
contiguous instead of split by LTX2AutoVaeEncoderStep.

Pure re-grouping: no block bodies change and intermediate outputs still propagate,
so t2v/i2v parity is bit-identical to before (user-confirmed at 17 frames).
Docstrings regenerated.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Enable LTX-2 prompt enhancement by default when the enhancer is loaded

Mirror the standard pipeline's tri-state prompt-enhancement default
(pipeline_ltx2.py:559-560), where `enable_prompt_enhancement` defaults to
auto-on when a `prompt_enhancer` component is present (LTX-2.4) and off
otherwise, and wire the enhancer into the t2v/i2v assemblies.

- Both enhancer sub-blocks: default `enable_prompt_enhancement=None` (tri-state).
  Resolve `None` against component presence inside `__call__` -- select_block
  cannot see components, so the gate dispatches for None/True and the sub-block
  decides. `None` + no enhancer -> pass the prompt through unchanged (the
  Cosmos3 optional-component pattern); explicit `True` + no enhancer -> a clear
  ValueError instead of the previous cryptic `NoneType` crash from within the
  enhance helper.
- LTX2AutoPromptEnhancerStep.select_block: skip only on an explicit `False`.
- Add LTX2AutoPromptEnhancerStep to LTX2Blocks and LTX2ImageToVideoBlocks so all
  three assemblies share the prompt_enhancer-first shape (previously only
  LTX2AutoBlocks had it; passing the flag to the others was silently ignored).
- Parity harnesses: force `enable_prompt_enhancement=False` on the modular run
  too (the modular sets now carry an enhancer), and fix the now-stale
  "contains no enhancer block" docstrings.

Only the dedicated-enhancer (LTX-2.4) path is wired; the standard pipeline's
text_encoder-as-enhancer fallback for LTX-2.0/2.3 remains a follow-up. Parity
unchanged (both pipelines run with enhancement disabled in the harnesses).
Docstrings regenerated.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Rename LTX-2.4 product identifiers to LTX-2.5.

Update conversion --version, model ids, system-prompt constant names, and docs/comments to the public 2.5 name. Behavior is unchanged in this commit.

* Add image-conditioning H.264 CRF matching Lightricks training.

Resolve CRF 18 for LTX-2.5 (Gemma 4) and 33 for earlier generations, and apply the PyAV re-compress path for I2V and single-frame Condition/IC keyframes.

* Align LTX-2 pipelines with the Lightricks reference behavior.

Extract shared prompt-enhancement and check_inputs mixins; enable Condition duration+enhancement and IC enhancement (HDR remains encode-only); match enhancement recipe and LTX-2.3/2.5 sampling defaults.

* Update LTX-2 docs for 2.5 naming, defaults, and opt-in enhancement.

Document LTX_2_3/2.5 sampling defaults, STG block 28, and enable_prompt_enhancement=True as the opt-in path.

* Replace LTX2AutoDuration with min_seconds/max_seconds call args.

Drop the dataclass wrapper and expose duration bounds directly on the T2V, I2V, and Condition pipelines.

* Align LTX-2 modular blocks with the merged standard-pipeline changes

The standard LTX-2 pipelines moved to shared `LTX2PromptEnhancementMixin` /
`LTX2CheckInputsMixin`, dropped `LTX2AutoDuration`, adopted the Lightricks
reference defaults, and gained H.264 CRF re-compression of image
conditionings. Port all of that to the modular blocks.

- Prompt enhancement: re-derive `_enhance_prompt` from the new mixin -- the
  `user prompt:` / `User Raw Input Prompt:` templates, 896px long-side image
  prep, left-padding to a multiple of 8 for Flash Attention, `clean_response`
  on the decoded output, and `max_new_tokens=None` resolving to the Gemma-4
  budget of 600.
- Revert `enable_prompt_enhancement` to a plain `False` opt-in, matching the
  reference pipelines (the tri-state auto-on default is gone upstream). The
  friendly error for `True` with no enhancer loaded is kept.
- Auto-duration: trigger on an omitted `num_frames` instead of an
  `LTX2AutoDuration` sentinel, with `min_seconds`/`max_seconds` as call args.
  `LTX2DurationStep` raises when no `duration_head` is loaded rather than
  silently falling back to 121 frames.
- Every `num_frames` InputParam default becomes `None`: input defaults are
  seeded into the pipeline state before any block runs, so a default of 121
  would leave the auto-duration branch permanently unreachable.
- Defaults sweep: `num_inference_steps` 40 -> 30, `use_cross_timestep`
  False -> True, and the video/audio guider ComponentSpec configs updated to
  the reference guidance stack.
- `LTX2VaeEncoderStep` gains `image_crf` and re-compresses the conditioning
  image before preprocess, declaring `text_encoder` only to resolve the model
  default CRF.
- Rename LTX-2.4 -> LTX-2.5 throughout, following the upstream product rename.

Parity harnesses updated for the new duration arguments, plus an `--image_crf`
flag on the i2v harness defaulting to 0 so the comparison isolates block logic
from the PyAV codec round-trip. Verified against a real checkpoint: t2v, i2v at
`--image_crf 0`, and i2v at `--image_crf -1` all pass.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Evaluate the decoder's SwiGLU in token tiles

Decode-only peak VRAM at 121 frames and 512x768 was 24.6 GiB, and 17.0 GiB of that was one transient
inside the first stage-5 block: `w_gate(x)` and `w_up(x)` are both hidden-width and their product makes
a third, so the whole video's worth of hidden activations was live three times over. At that size each
one is 2,973,696 tokens x 1024 x 2 bytes = 5.67 GiB.

The MLP is pointwise across tokens, so tiling it is exact -- it changes only how many hidden-width
elements exist at once. Measured on a full-size decode: peak 24.8 -> 19.4 GiB (-22%), wall clock 2.79 ->
2.84 s (+1.6%), output bit-identical (max abs diff 0.000e+00). That also puts the diffusion decoder
below the conv decoder, which needs 23.8 GiB at the same size.

Tile size 16384 tokens is the reference decoder's own default (`DEFAULT_SWIGLU_TILE_SIZE`). Bounding a
token count rather than a number of tiles keeps peak memory independent of resolution.

This is the first of the two transients the reference's default decode mode avoids; the other is the
full-volume QKV projection plus RoPE's fp32 upcast, which it addresses by chunking attention along
width. That one is not bit-exact (it reassociates NATTEN's accumulation), so it is left for a follow-up
rather than changed here.

* Declare _no_split_modules on the diffusion decoder

Both block types close over a residual add that combines outputs from different children, which is the
case models.md says has to stay co-located, so neither can be split across devices.

Unskips three memory tests that were gated on the attribute: the file goes from 35 passed / 7 skipped to
38 passed / 4 skipped, and the three (test_cpu_offload, test_disk_offload_with_safetensors,
test_disk_offload_without_safetensors) pass.

* Match the encoder defaults to the published LTX-2.4 config

block_out_channels was (256, 512, 1024, 2048) and layers_per_block was (4, 6, 6, 2, 2); both were
inherited from the 2.0 conv VAE. The published vae_diffusion/config.json has (256, 512, 1024, 1024) and
(4, 6, 4, 2, 2). Real loads were unaffected because the config sets these explicitly, but the defaults
described a model that does not exist.

All 27 __init__ defaults that appear in the published config now match it.

* Cover the token-tiled SwiGLU path in the tests

The dummy video is 9x48x48, so its stage-5 grid is 5184 tokens against a 16384-token tile size: every
other test in the file takes the untiled branch and the tiling loop ran nowhere in CI. This shrinks the
tile size to force ~41 tiles and requires torch.equal against the untiled evaluation, since the MLP is
pointwise across tokens and tiling must be exact rather than close.

Checked the test is not vacuous: sabotaging the tiled branch alone (silu on w_up instead of w_gate)
fails it at 8.83e-01.

* Let the parity harness run against the LTX-2.5 reference too

The harness only spoke LTX-2.4's decoder API and died on `forward_pre_diffusion` against 2.5, so it could
not check the release the port is now targeted at. Three shims absorb the differences:

* 2.5 selects a decode pathway by swapping `__class__` on every block, so an as-constructed decoder has no
  `forward_combined`. Install the COMBINED pathway explicitly, uncompiled, since that is the pathway this
  port implements.
* stages 1-4 split into `forward_stages_1_to_3` + `forward_stage_4`, so the chunked pathway can defer
  stage 4.
* the trailing NATTEN ghost pad moved out to the caller while its crop stayed behind
  `forward_stage_4(pad_trailing=True)`; the two have to be paired or the context loses real frames (3 of
  17 survive at this config, which is how the mismatch first showed up).

Same numbers against both references -- context 5.367e-04, step 7.337e-04 -- which is the check that the
shims are semantically right and not just shape-compatible.

* Add LTX-2.X modular condition blocks

Ports LTX2ConditionPipeline to the modular pipeline system, including the
LTX-2.5 additions (per-condition CRF, conditions-sourced prompt enhancement,
auto-duration, the Lightricks reference defaults).

New blocks:
  - encoders.py: LTX2ConditionEncoderStep (resize/center-crop, single-frame
    H.264 re-compression at the model CRF, temporal trim, VAE encode) and
    LTX2ConditionPromptEnhancerStep (grounds the rewrite in the first PIL
    frame found in `conditions`, text-only otherwise).
  - before_denoise.py: LTX2ConditionPrepareLatentsStep (first-frame overwrite
    + keyframe token append with their own RoPE coords, emitting
    conditioning_mask / clean_latents / appended_coords / base_token_count),
    LTX2ConditionSetTimestepsStep, LTX2ConditionPrepareAudioLatentsStep,
    LTX2ConditionPrepareCoordsStep, and the _prepare_keyframe_coords helper.
  - denoise.py: LTX2ConditionLoopBeforeDenoiser (mask-scaled per-token video
    timestep), LTX2ConditionLoopAfterDenoiser (x0 blend against the clean
    condition latents, then a full-sequence scheduler step),
    LTX2ConditionDenoiseStep.
  - decoders.py: LTX2TrimConditionTokensStep.
  - modular_blocks_ltx2.py: LTX2ConditionAutoPromptEnhancerStep,
    LTX2ConditionCoreDenoiseStep, LTX2ConditionDecoderStep, LTX2ConditionBlocks.

LTX2LoopDenoiser is reused unchanged: the two LTX2Guidance guiders already
express the whole CFG + STG + modality-isolation stack the condition pipeline
uses, and the transformer takes the longer packed sequence with the base
num_frames/height/width exactly as the standard pipeline does. The standard
pipeline's CFG batch duplication (conditioning mask, coords) has no modular
counterpart, since each guidance pass is its own single-batch forward.

Block ordering: prepare-latents runs *before* set-timesteps, unlike the
text-to-video and image-to-video core denoise steps. The resolution-aware
shift `mu` is computed from the packed latent sequence length, which here
includes the appended keyframe tokens, so the latents must exist first. This
mirrors LTX2ConditionPipeline (its section 4 precedes section 5). The
text-to-video and image-to-video blocksets are unaffected: with no appended
tokens the grid-derived sequence length already equals latents.shape[1].

Two subtleties the parity harness surfaced:

  - The condition pipeline samples audio noise directly in packed shape
    [B, L, C * M], while the text-to-video and image-to-video pipelines sample
    unpacked [B, C, L, M] and pack afterwards. Both draw the same number of
    values from the generator but lay them out differently, so reusing the
    shared LTX2PrepareAudioLatentsStep silently desynchronizes the audio noise
    and, through the joint attention, the video too (1.4 mean-rel on audio,
    0.13 on video before the fix). Hence a standalone condition audio block.

  - `noise_scale` means different things across workflows: 0.0 for
    text-to-video/image-to-video, `None -> sigmas[0] or 1.0` for conditions.
    A blockset keeps the first non-None default across its blocks, so a 0.0
    would have shadowed the condition resolution and left the latents
    unnoised. Both condition-path blocks declare None; prepare-latents
    resolves once and writes the value back for the audio step.

Keyframe tokens, masks and coords are expanded to the generation batch (the
pattern the in-context pipeline already uses for reference tokens). The
standard pipeline builds them at batch 1 and cats them onto a batch-B
sequence, so it raises for num_videos_per_prompt > 1 with any condition at
latent index > 0; the modular blocks handle that case.

Verification: integrations/ltx2_condition_parity.py (transient, removed before
merge) compares LTX2ConditionBlocks against LTX2ConditionPipeline on shared
component objects. Eight cases on a tiny checkpoint -- first-frame only,
keyframe only, both plus a multi-frame video condition, two keyframes, no
conditions, --crf -1, --predict_duration, num_videos_per_prompt=2 -- all pass
at 3e-7 to 1.3e-6 mean-rel. On a full checkpoint at 768x512x17 with two
conditions through the CRF path: video 8.7e-04 mean-rel / 1.1e-02 max-abs,
audio 1.5e-04 / 2.1e-03, in line with the image-to-video figures at the same
frame count.

make style, make quality and make fix-copies are clean; auto-docstrings
regenerated with no TODO placeholders.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Add LTX-2.X modular in-context (IC-LoRA) blocks

Ports LTX2InContextPipeline to the modular pipeline system on top of the
condition blocks, and fixes two bugs in the standard in-context pipeline that
the parity harness surfaced.

New blocks:
  - encoders.py: LTX2ReferenceEncoderStep (preprocess, VAE-encode and pack each
    reference video, compute the coords that map its tokens into the target
    space, and build the per-token cross-attention strengths), plus the
    _downsample_mask_to_latent helper.
  - before_denoise.py: LTX2InContextPrepareLatentsStep (frame conditions as in
    the condition step, then the reference tokens appended last) and
    LTX2BuildVideoSelfAttentionMaskStep.
  - modular_blocks_ltx2.py: LTX2AutoReferenceEncoderStep,
    LTX2AutoBuildVideoSelfAttentionMaskStep, LTX2InContextCoreDenoiseStep,
    LTX2InContextBlocks.

LTX2ConditionDenoiseStep is reused unchanged: with the blend gate fixed below,
reference tokens are pinned by exactly the same x0 blend as frame conditions,
matching the reference implementation where VideoConditionByReferenceLatent and
VideoConditionByKeyframeIndex produce the same (denoise_mask, clean_latent) pair
and post_process_latent runs unconditionally. The condition encoder, timesteps,
audio-latents, coords and decoder blocks are shared as well.
video_self_attention_mask reaches the transformer through the
denoiser_input_fields tag, so LTX2LoopDenoiser needed no change.

`reference_conditions` is optional, matching LTX2InContextPipeline: IC-LoRAs
that carry their behavior in the adapter weights (camera control, style) take
no reference video, which is the shape of the standard pipeline's own docstring
example. The reference encoder and the attention-mask step are both skipped when
it is absent. There is no duration step (the in-context pipeline ships without a
duration_head), so LTX2ConditionEncoderStep now raises a concise error if
`num_frames` is still None by the time the conditions are encoded.

Per-reference token counts come from the encoder rather than an equal split of
the total, so references of differing lengths (a reference video shorter than
num_frames) get the right strengths.

Standard-pipeline fixes in pipeline_ltx2_ic_lora.py:

  - The x0 blend was gated on `has_conditions` alone, so with reference
    conditions and no frame conditions the reference tokens were seeded clean
    and given a zeroed timestep but never re-pinned. Their x0 prediction error,
    divided by sigma each step, then accumulated and drifted them away from the
    encoded reference. Now gated on `has_conditions or num_ref_tokens > 0`, in
    line with the surrounding gates and the reference implementation.

  - video_self_attention_mask was rebound in the loop rather than expanded into
    a per-pass local. The main pass expanded it to the CFG-doubled batch, after
    which the STG pass's expand() to `latents.shape[0]` raised
    "RuntimeError: The expanded size of the tensor (1) must match the existing
    size (2)". Any run combining an attention mask with STG or modality
    guidance -- i.e. the default guidance settings -- died on the first step.

Also removed the unused has_appended_tokens local and replaced the "# - TODO"
placeholder above the attention-mask construction with the block structure,
which the reference confirms.

Verification: integrations/ltx2_in_context_parity.py (transient, removed before
merge). Twelve cases on a tiny checkpoint -- reference only, reference at
partial strength, scalar attention strength, pixel-space attention mask,
downscale factor 2, references plus first-frame and keyframe conditions, two
references, the CRF path, and four reference-free variants -- all pass at 3.4e-7
to 1.3e-6 mean-rel. The seven-case condition suite still passes. On a full
checkpoint at 768x512x17 with a reference plus two conditions: video 4.4e-05
mean-rel / 5.6e-04 max-abs, audio 3.2e-05 / 2.4e-04.

Known limitation, not addressed here: transformer_ltx2.py converts the
multiplicative [0, 1] self-attention mask to an additive bias linearly, as
(1 - mask) * -10000, whereas the reference uses log space (bias = log(mask),
finfo.min at zero). Intermediate strengths therefore saturate to "fully masked",
making conditioning_attention_strength effectively binary and spatially varying
masks inert beyond their zero/non-zero pattern. Parity is unaffected -- both
pipelines feed the same mask into the same transformer -- but the feature does
not currently work as documented.

make style, make quality and make fix-copies are clean; auto-docstrings
regenerated with no TODO placeholders.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Make the diffusion decoder a decode pipeline instead of a VAE

Addresses the review: a full diffusion model should not be an AutoencoderKL that hides its denoising
behind `.decode()`, and it should not have to be threaded into every LTX-2 pipeline as a `vae`.

AutoencoderKLLTX2VideoDiffusionDecoder becomes LTX2VideoDiffusionDecoderModel, a plain ModelMixin with
no encoder. Encoding stays with AutoencoderKLLTX2Video, whose latent space this consumes unchanged, so
latents remain interchangeable between the two decoders. Dropping the encoder also removes the
converter's awkwardness of sourcing encoder weights and the real block_out_channels from the conv
`vae/` folder: ten encoder-only config keys are gone.

LTX2VideoDiffusionDecodePipeline drives it, shaped like LTX2LatentUpsamplePipeline: run any LTX-2
pipeline with output_type="latent", then decode. `vae` is an optional component, since it is only ever
consulted for the latent statistics, and the decoder carries its own `latents_mean` / `latents_std`
buffers to fall back on. That means a decode-only workflow never loads a second autoencoder.

The `vae=` path is removed accordingly: the isinstance branches in LTX2Pipeline,
LTX2ImageToVideoPipeline and the modular decode step are gone, along with the fixtures that built a
diffusion decoder to pass as `vae`. The model's slicing/tiling test class went with them, since
enable_tiling was an AutoencoderMixin concern and this is no longer an autoencoder.

Tests: 37 passed / 3 skipped on the model, 83 passed / 2 skipped across the t2v and i2v pipelines.

Still to come: mapping the 2.5 checkpoint to a blockset that selects the diffusion decode block, and
the KandinskyCombinedPipeline pattern for running the two-step flow by default in the standard API.

* Add a modular decode block for the LTX-2 diffusion decoder

The previous commit removed the `isinstance(vae, ...)` branch that let the diffusion decoder stand in
as the modular `vae`, which was the right call twice over: it is what the review objected to, and
modular.md says a new case gets a new block rather than a branch inside an existing one. But removing
it without a replacement left modular with no route to the diffusion decoder at all.

LTX2DiffusionVaeDecoderStep is that replacement. It declares the decoder as its own
`diffusion_decoder` component rather than borrowing the `vae` slot, and passes a generator instead of
a decode timestep, since this decoder draws the noise it denoises. `LTX2VaeDecoderStep` is untouched,
so the convolutional path is unaffected.

What is still missing is the wiring: a blockset using this block, and an `_ltx2_map_fn` so a
checkpoint that ships the diffusion decoder selects it automatically instead of the user choosing.
That lands in modular_blocks_ltx2.py, which #12 is reorganizing, so it needs sequencing against that
PR rather than racing it.

* Test the diffusion decode pipeline, and give it a video-only output

The decode pipeline had no coverage: it was never actually run. Writing the tests immediately turned
up a bug, which is that it returned `LTX2PipelineOutput`, whose `audio` field is required. This
pipeline decodes video only, so it now returns a video-only `LTX2VideoDecodeOutput` instead of
passing a meaningless `audio=None`.

Four tests: decode with no `vae` (the fallback to the decoder's own latent statistics), decode with a
`vae` supplied (its statistics take precedence, checked by making the two disagree rather than
asserting a shape), reproducibility under a seeded generator plus divergence under a different seed,
and `denormalize=False` actually skipping the statistics. The decoder's stat buffers are set to
non-trivial values in the fixture so a run that silently skipped denormalization could not pass by
coincidence.

* Fix the decode example: output_type="latent" is already denormalized

The example in the docs and the pipeline docstring both showed `output_type="latent"` feeding straight
into the decode pipeline on its defaults. That path denormalizes twice: `LTX2Pipeline` applies the
latent statistics before returning latents (pipeline_ltx2.py), and the decode pipeline applies them
again because `denormalize` defaults to True. Every channel ends up scaled by its own std a second
time, so e.g. channel 0 (std 0.238) comes out roughly 4x too small.

Passing `denormalize=False` in the example and saying so in both docstrings. Caught by running the
flow end to end on real rc4 weights, which is also where the two decoders agree at 0.9978 once the
statistics are applied only once.

Whether the *default* should flip, or `output_type="latent"` should stop denormalizing instead, is a
contract question across both pipelines and is still open.

* Fix IC-LoRA video self-attention mask grouping

The video self-attention mask deviated from the reference implementation
(`ltx_core.conditioning.mask_utils.build_attention_mask`) in two ways. Both
predate the modular blocks and applied to `LTX2InContextPipeline` as well; the
modular block had ported the same construction.

1. Keyframe conditions cross-attended with reference tokens. `num_noisy_tokens`
   was derived as `latents.shape[1] - num_ref_tokens`, which folds the appended
   keyframe tokens into the noisy group, so they received the reference cross
   mask. The reference takes `num_noisy_tokens` from the target latent shape --
   generated-video tokens only -- and tracks the extras offset separately, so
   keyframe <-> reference is 0.0. Split the two quantities apart:
   `_build_video_self_attention_mask` now takes `num_prefix_tokens` alongside
   `num_noisy_tokens`.

2. Multiple reference conditions fully attended to each other. All references
   were passed as a single attention group with a 1.0 self-block. The reference
   wraps each `LTX2ReferenceCondition` in its own
   `ConditioningItemAttentionStrengthWrapper`, building the mask once per item,
   so reference_i <-> reference_j is 0.0. The call site now splits
   `ref_cross_mask` into one group per reference before building the mask.

Threading per-reference token counts out of `_encode_reference_conditions` also
removes the equal-split assumption in `prepare_latents` and
`prepare_reference_latents`, which assigned the wrong per-token strengths when
references encoded to different token counts (reachable when a reference video
is shorter than `num_frames`).

API impact
----------

`prepare_latents` returns a 7-tuple instead of a 6-tuple, adding
`ref_token_counts` (`list[int]`) as the new final element. Elements 1-6 keep the
types they have on `main`; in particular `ref_cross_mask` remains the
concatenated `[1, num_ref_tokens]` tensor. Callers that unpack the tuple fail
immediately with a `ValueError` rather than silently receiving a changed type.

`_encode_reference_conditions` (private) likewise gains `reference_token_counts`
as a fourth return element. `prepare_reference_latents` keeps its documented
4-tuple unchanged.

Verification
------------

Correctness against the reference. Both the standard helper and the modular
block were checked for exact tensor equality (`torch.equal`) against
`build_attention_mask`, driven the way `ic_lora.py` drives it -- one
`ConditioningItemAttentionStrengthWrapper` per reference, so the reference
builds iteratively with `existing_mask` carried forward. Five layouts, all
matching, exercised through the same concatenate-then-split path the call site
uses:

  - references only, 1 reference
  - keyframes + 1 reference          (exercises fix 1)
  - keyframes + 2 references         (exercises fixes 1 and 2)
  - 2 references of unequal length   (exercises fix 2 and the token counts)
  - no keyframes, 3 references       (exercises fix 2)

Standard/modular parity on a real checkpoint, 512x512x17, fp32, via
`integrations/ltx2_in_context_parity.py`. Video latents (1, 128, 3, 16, 16),
audio latents (1, 8, 18, 16); gates are mean-rel 2e-2 and max-abs 1.5e-1:

  --reference 1.0 9 --condition 2 0.5 9 --conditioning_attention_strength 0.5
    video: max abs 4.822e-05, mean rel 7.851e-06
    audio: max abs 1.875e-04, mean rel 1.773e-05

  --reference 1.0 9 --reference 0.8 9 --conditioning_attention_strength 0.5
    video: max abs 1.953e-04, mean rel 9.101e-05
    audio: max abs 9.251e-05, mean rel 1.026e-05

The first case is the layout where `num_prefix_tokens != num_noisy_tokens`; a
wrong prefix/base split would have placed the group blocks at the wrong offsets
with valid shapes, surfacing as a parity mismatch. The returned video shape also
unpacks from exactly 768 base tokens (3 x 16 x 16), confirming
`base_token_count` is the quantity now fed as `num_noisy_tokens`.

Scope of the parity runs: both sides share this construction, so parity shows
they did not desynchronize, not that either matches the reference -- that rests
on the equality test above. Both references in the second case are 9 frames and
so encode to equal token counts, meaning the equal-split and per-count paths
coincide; the token-count change is not discriminated by these runs. A reference
pair of differing lengths (e.g. `--reference 1.0 9 --reference 0.8 17`, giving
512 vs 768 tokens) would separate them, and would have failed parity before this
commit since the modular block already used per-reference counts while the
standard pipeline split evenly.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Add LTX25AutoBlocks and LTX25ModularPipeline

Following the review: LTX-2.5 is a new checkpoint, so it gets its own blockset and pipeline rather
than a config flag inside the LTX-2 ones.

LTX25AutoBlocks subclasses LTX2AutoBlocks and overrides exactly one entry, `video_decode`, to
LTX2DiffusionVaeDecoderStep. Every other leaf block is reused, so the two blocksets have identical
block_names and cannot drift apart. That makes the diffusion decoder the default for LTX-2.5, which
matches what the checkpoint ships natively, without the user having to pass a decoder at all.

Going the other way stays a one-line swap rather than a second official blockset:

    blocks.sub_blocks["video_decode"] = LTX2VaeDecoderStep()

LTX25ModularPipeline carries `default_blocks_name = "LTX25AutoBlocks"` and a new "ltx2.5" key in
MODULAR_PIPELINE_MAPPING, so a repo shipping `modular_model_index.json` routes straight to the new
blockset.

The condition and in-context workflows belong in this blockset too, but those blocks live in the
modular condition/IC PR, so folding them in belongs there rather than as a competing change here.

* Drop the encoder half in the diffusion decoder converter

The converter still assembled the whole VAE checkpoint, encoder included, and handed it to a strict
`load_state_dict`. That was correct while the class was an autoencoder; after it became decoder-only
the ~84 `encoder.*` keys have nowhere to land and the load raises. Nothing caught it because no test
converts anything and every other check loads pre-converted weights, where unexpected keys are only
warned about.

Now the encoder is discarded rather than remapped, keeping the `decoder.` half and the per-channel
statistics that become `latents_mean` / `latents_std`. `strict=True` stays, since it is what guards
against a botched rename rule.

Verified by actually running it: pulled the 395 `vae.*` tensors out of the native rc4 checkpoint by
byte range, converted, and diffed against the already-published folder. 407/407 parameters, max abs
difference 0.000e+00, so the fix changes nothing about the weights it produces.

Also added a regression test, since the absence of any converter coverage is why this slipped.

* Share the neighborhood attention mask and parameterise the AdaLN chunk count

Two of the resolved review threads. Both are internal to the decoder modules and are unaffected by
the pipeline-vs-model question still open on the thread above them.

Build the FlexAttention mask once per stage instead of once per block. The mask depends only on the
grid and the kernel, both fixed within a stage, so 24 builds collapse to 5; measured at 768x512x121
that is 582ms to 132ms. build_block_mask returns None for NATTEN, which encodes the window in its
kernel. That is not merely an optimisation: create_block_mask materialises O(N^2) uncompiled, so a
69x64x96 stage would ask for 167 GiB and stage 5 for 8.2 TiB, and the mask must never be built for a
path that would not read it.

Make the AdaLN chunk count a constructor argument, num_chunks on the shared AdaLN and num_mod_params
on the diffusion block, with the decoder passing shared_adaln.num_chunks through so the two cannot
drift. num_mod_params is already the name LTX2AdaLayerNormSingle uses. The block's forward still
destructures exactly seven chunks and reads four of them, which is the reference's shape.

Decoding the test fixture is bitwise identical to before (max abs diff 0.000e+00). 39 passed, 4
skipped.

* Export the LTX-2.5 modular classes from the top-level namespace

`ModularPipeline.from_pretrained` resolves a repo's `_class_name` with
`getattr(importlib.import_module("diffusers"), class_name)`, so a class that is only reachable from
`diffusers.modular_pipelines.ltx2` cannot be selected by a checkpoint. `LTX25ModularPipeline` and
`LTX25AutoBlocks` were exported there but not from `diffusers` itself, which left the whole
checkpoint-to-blockset mapping dead: loading a repo whose index names them raised
`AttributeError: module diffusers has no attribute LTX25ModularPipeline`.

Exported alongside `LTX2ModularPipeline` / `LTX2AutoBlocks`, which is how the loader already …

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-08-11T01:47:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12915
- **最后更新**: 2026-08-11T13:39:32Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

1. **主要更新类型**：功能新增（支持新模型版本）。

2. **关键变更点**：新增对Minimax-H3剪枝版本的支持，包括添加模型定义、重命名模型文件，并修复推理脚本。这与项目“提供多样化扩散模型工具”的方向一致，扩展了模型库覆盖范围。

3. **对项目的影响**：剪枝版本通常体积更小、推理更快，可能降低用户使用门槛，吸引更多资源受限场景的开发者。同时，修复推理脚本提升了开箱即用的可靠性。

4. **值得关注的技术点**：剪枝模型的集成方式（如何平衡精度与速度）、模型命名规范（重命名可能影响兼容性），以及推理脚本的适配逻辑。

5. **对项目发展的影响**：DiffSynth-Studio定位为多模型合成工具，新增Minimax-H3剪枝版可增强其在视频生成或图像编辑任务中的竞争力，尤其适合需要高效推理的移动端或实时应用。这有助于项目在生态中保持模型多样性优势，并吸引对轻量化模型有需求的用户群体，推动社区采用率提升。

## 详细提交记录

### [660b603](https://github.com/modelscope/DiffSynth-Studio/commit/660b60364d1a8e91e4ef29aa632723149e0ed121)

- **作者**: Hong Zhang
- **时间**: 2026-08-11T07:09:35Z
- **提交信息**: Support Minimax-H3 pruned version (#1582)

* add minimax-h3 pruned

* rename model

* fix inference script

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31690
- **最后更新**: 2026-08-11T22:42:01Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 23
- **主要提交者**: Douglas Yang, gjsheu, ilyasher-harmonic

## AI分析总结

# sglang 仓库提交分析报告

## 一、主要更新类型

本次提交涵盖**新模型支持**（Muse Glimmer、Ling-3.0系列、NVIDIA Nemotron 3.5）、**性能优化**（FP32 LM head优化、slot分配O(1)算法、diffusion模型多项优化）、**Bug修复**（CUDA 13.0兼容性、NPU HiCache修复、默认dtype恢复）、**文档更新**（Kimi-K3、Hunyuan3、Ling-3.0 recipes）以及**基础设施改进**（CI工作流、依赖升级、JIT内核迁移）。

## 二、关键变更点与项目方向

1. **新模型支持**：Muse Glimmer、Ling-3.0系列、Nemotron 3.5的加入，持续扩展模型生态覆盖，符合项目“服务多种LLM”的核心定位。
2. **性能优化**：FP32 LM head优化、O(1) slot分配、diffusion模型多项融合优化（denoise时间降低2.8%-18.8%），直接提升推理效率。
3. **JIT内核迁移**：FP8量化从AOT迁移至JIT，提升灵活性和可维护性。
4. **HiSparse/HiCache改进**：共享索引预取、Mamba边界簿记修复，强化稀疏注意力支持。
5. **多平台适配**：NPU、AMD ROCm、CUDA 13.0兼容性修复，扩大硬件支持范围。

## 三、项目影响与意义

- **性能提升显著**：diffusion模型多项优化实现bit-exact且大幅降低denoise时间，对生产环境有直接价值。
- **生态扩展**：新增多个模型支持和硬件平台适配，增强项目通用性和吸引力。
- **稳定性增强**：多项Bug修复和测试改进（flaky测试修复、stale PR清理）提升代码质量和CI可靠性。
- **架构演进**：JIT内核迁移和diffusion执行能力重构，为未来扩展奠定基础。

## 四、值得关注的技术点

1. **diffusion模型优化**：fused modulate、rotate-half RoPE融合、weight-only FP8延迟反量化等，展示了深度性能优化的方法论。
2. **O(1) slot分配**：ReqToTokenPool.alloc()算法改进，对高并发场景的吞吐提升至关重要。
3. **HiSparse IndexShare预取**：plan-then-IO策略，优化稀疏注意力场景的内存访问模式。
4. **PD disaggregation socket上限可配置**：通过环境变量提升zmq socket容量，增强分布式部署灵活性。
5. **bit-exact测试**：新增hicache logprob一致性测试，确保优化不引入精度损失。

## 五、对项目发展的影响

sglang作为高性能LLM推理框架，本次提交体现了**“性能优先、生态扩展、多平台适配”**的发展战略。性能优化持续巩固其在高吞吐推理场景的竞争力；新模型和硬件支持扩大用户基础；基础设施改进（CI、依赖管理）保障项目长期可维护性。特别是diffusion模型和稀疏注意力方向的深耕，显示项目正从纯LLM推理向多模态、长上下文场景拓展，符合AI推理技术演进趋势。整体来看，这些提交将增强sglang在AI推理框架市场中的技术领先地位和生态吸引力。

## 详细提交记录

### [fde9ad2](https://github.com/sgl-project/sglang/commit/fde9ad253161c3d866727dfb4be2772623d57ca4)

- **作者**: sglang-bot
- **时间**: 2026-08-11T22:41:52Z
- **提交信息**: [Feature] Add Muse Glimmer model support (#34262)

Co-authored-by: sglang-bot <232288953+sglang-bot@users.noreply.github.com>
Co-authored-by: Brayden Zhong <brayden.zhong@radixark.ai>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [9c1517d](https://github.com/sgl-project/sglang/commit/9c1517df4aa4a6210831e92091b84c81d9e5f7b5)

- **作者**: Hanming Lu
- **时间**: 2026-08-11T22:27:32Z
- **提交信息**: Raise PD zmq per-context socket cap via SGLANG_DISAGGREGATION_ZMQ_MAX_SOCKETS (#34450)

### [7fb6e61](https://github.com/sgl-project/sglang/commit/7fb6e61b953e6598aa6b0bffad4c9db0435e734e)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-11T22:16:34Z
- **提交信息**: Fix CUDA 13.0 VMM handle type compatibility (#34431)

### [9ced8d0](https://github.com/sgl-project/sglang/commit/9ced8d0981aae63f5bba54206d03b10c26f8eef7)

- **作者**: ilyasher-harmonic
- **时间**: 2026-08-11T22:14:50Z
- **提交信息**: Optimize FP32 LM head for bf16/fp16 (#32370)

### [2c07ca5](https://github.com/sgl-project/sglang/commit/2c07ca5e8da3757bd60426ed4763083b318fdebd)

- **作者**: gongwei1027
- **时间**: 2026-08-11T22:05:04Z
- **提交信息**: [Fix] Allow flashinfer_sparse_mla DSA backend for HiSparse on SM120 FP8 KV (#33075)

### [59450c4](https://github.com/sgl-project/sglang/commit/59450c4f186f71cde2b63a5c9e970613c4561f9a)

- **作者**: Douglas Yang
- **时间**: 2026-08-11T19:23:41Z
- **提交信息**: docs(cookbook): Kimi-K3 — drop --enable-symm-mem from the GB cells (#34444)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [d5d41d0](https://github.com/sgl-project/sglang/commit/d5d41d07edaef5ec629f1ef73f62e8e4f7b8003c)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-11T19:16:03Z
- **提交信息**: [Docs] Add Ling-3.0-tiny INT4 recipes (#34395)

### [93c1bff](https://github.com/sgl-project/sglang/commit/93c1bff1d44f5984ff1b41fa1d4ec5e6ab52af21)

- **作者**: Hao Zhang
- **时间**: 2026-08-11T18:33:04Z
- **提交信息**: Fix default dtype restoration after model loader errors (#34440)

Co-authored-by: zhisbug <1654062+zhisbug@users.noreply.github.com>
Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [c58953d](https://github.com/sgl-project/sglang/commit/c58953d90a56c03576b0a002581342a74bd01a23)

- **作者**: Dmitrii Sergeev
- **时间**: 2026-08-11T18:26:05Z
- **提交信息**: O(1) slot allocation in ReqToTokenPool.alloc() (#32208)

Co-authored-by: Zhiqiang Xie <xiezhq@stanford.edu>

### [aadb972](https://github.com/sgl-project/sglang/commit/aadb9720fe6c56395bfcebb88a4dbe8148531f78)

- **作者**: Jeremy Zhang
- **时间**: 2026-08-11T18:15:16Z
- **提交信息**: fix: route scheduler aborts to multi-tokenizer workers (#33940)

### [f9153df](https://github.com/sgl-project/sglang/commit/f9153df62e735a0731510548e28da97517c77f7e)

- **作者**: Ke Bao
- **时间**: 2026-08-11T17:54:45Z
- **提交信息**: Add bit-exact hicache logprob-consistency test (#34356)

### [8f3d3a3](https://github.com/sgl-project/sglang/commit/8f3d3a31f4c8867784a9bd2d75d805054bf00b8d)

- **作者**: huangtingwei
- **时间**: 2026-08-11T16:36:48Z
- **提交信息**: [HiCache] Fix Mamba track-boundary bookkeeping under overlap scheduling (#29792)

Co-authored-by: Hanming Lu <hanminglu@meta.com>

### [a3bd7d9](https://github.com/sgl-project/sglang/commit/a3bd7d94011db60fc1803a33ada0b5a714c46ad5)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-11T16:35:35Z
- **提交信息**: Bump CuTeDSL to 4.6.2 (#34372)

### [8267d76](https://github.com/sgl-project/sglang/commit/8267d76c2c7bc8921ec75c646b809089790cf3b4)

- **作者**: Mick
- **时间**: 2026-08-11T16:14:07Z
- **提交信息**: [VLM] replace deprecated image processor use_fast (#34175)

### [b20c375](https://github.com/sgl-project/sglang/commit/b20c375c10443e4f4a5656689a04d514194364fd)

- **作者**: Ke Bao
- **时间**: 2026-08-11T13:47:01Z
- **提交信息**: Fix flaky decode cache-hit check in Inkling test (#34405)

### [f148eb6](https://github.com/sgl-project/sglang/commit/f148eb6e6ea51eff7ef8725a77c71818e3fe6fe3)

- **作者**: Jinyan Yi
- **时间**: 2026-08-11T13:20:30Z
- **提交信息**: Add Hunyuan3 On Ascend Doc (#30223)

### [a50ab9c](https://github.com/sgl-project/sglang/commit/a50ab9cec7d61649b9f149891eda363bd90bb681)

- **作者**: gjsheu
- **时间**: 2026-08-11T13:09:45Z
- **提交信息**: [npu] [bugfix] Fix HiCache MHA backup for NPU (#34341)

### [3add7e1](https://github.com/sgl-project/sglang/commit/3add7e19ffa1d146e8d317987aec43ec143552e8)

- **作者**: Faradawn Yang
- **时间**: 2026-08-11T13:00:57Z
- **提交信息**: Add NVIDIA Nemotron 3.5 Lightning cookbook (#33481)

Signed-off-by: Faradawn Yang <73060648+faradawn@users.noreply.github.com>
Signed-off-by: Ryan Stewart <rystewart@nvidia.com>
Co-authored-by: Ryan Stewart <rystewart@nvidia.com>

### [2d19307](https://github.com/sgl-project/sglang/commit/2d193077f70fbd6dba25977b4acbc9b77aa46a8f)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-11T12:40:40Z
- **提交信息**: [JIT Kernel] Migrate per-token FP8 quantization from AOT to JIT (#34257)

### [a0a76e4](https://github.com/sgl-project/sglang/commit/a0a76e44851879bcc2055a61505172c2bab5c361)

- **作者**: Kaixi
- **时间**: 2026-08-11T12:10:19Z
- **提交信息**: [DSV4] perf: Enable alt stream during BCG prefill (#29070)

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [546965f](https://github.com/sgl-project/sglang/commit/546965fc72a73b147323fc839ad0aa955ef64aff)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-11T10:23:08Z
- **提交信息**: [diffusion] LTX-2: mount the bit-exact fused modulate at the 8 bare adaLN sites (ltx23-one-stage denoise -2.8% H100 / -2.6% H200) (#34315)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [dd8c584](https://github.com/sgl-project/sglang/commit/dd8c5849af99d9a2cdcc39a1a480ca19af82adef)

- **作者**: Mick
- **时间**: 2026-08-11T10:20:43Z
- **提交信息**: [diffusion] refactor: move dit execution capabilities to runtime models (#34249)

### [071f0f1](https://github.com/sgl-project/sglang/commit/071f0f1e9d69a7f6f5babfae7ace21119742f237)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-11T10:18:37Z
- **提交信息**: [diffusion] ERNIE-Image: fuse rotate-half RoPE + GELU-mul and hoist rope cos/sin (denoise -16.2% H100 / -12.7% H200, bit-exact) (#34306)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [ba3dc16](https://github.com/sgl-project/sglang/commit/ba3dc16401659a2c582ceffebdda92e9536b0b49)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-11T10:15:26Z
- **提交信息**: [diffusion] weight-only FP8: dequantize linear weights once at first use (Ideogram-4 denoise -18.8% H200 / -7.8% H100, bit-exact) (#34305)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [5469fae](https://github.com/sgl-project/sglang/commit/5469faec45c89110be1ebc3828ee409932077435)

- **作者**: Zhiqiang Xie
- **时间**: 2026-08-11T08:58:28Z
- **提交信息**: HiSparse: shared-index (IndexShare) plan-then-IO swap-in prefetch (#34329)

Co-authored-by: Tingwei Huang <huangtingwei9988@gmail.com>

### [396722e](https://github.com/sgl-project/sglang/commit/396722e4903fb8ad076393763250e22f824d13e0)

- **作者**: Cherry_ming
- **时间**: 2026-08-11T08:38:15Z
- **提交信息**: [NPU] Disable failed test cases (#34377)

Co-authored-by: Even Zhou <even.y.zhou@outlook.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [6f3fe13](https://github.com/sgl-project/sglang/commit/6f3fe13a9c81f761ba8df751ddfd0de1a914f38b)

- **作者**: Bingxu Chen
- **时间**: 2026-08-11T08:36:45Z
- **提交信息**: [AMD] Install AITER's pinned Triton wheel in the ROCm 7.2 image (#34364)

Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>

### [d8a61c2](https://github.com/sgl-project/sglang/commit/d8a61c26a662de2cc3791c33235b024c25bd61d7)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-11T07:54:02Z
- **提交信息**: [CI] Add a scheduled workflow to close stale PRs (#34380)

### [e74ea5b](https://github.com/sgl-project/sglang/commit/e74ea5b1d709c5476973fd383b6204398d0c31cf)

- **作者**: Hsiu-Chun, Hung
- **时间**: 2026-08-11T07:51:57Z
- **提交信息**: [ROCm/gfx95] Fix fp8 per-channel attention for Kimi-K2.7-code-mxfp4 o… (#31105)

Co-authored-by: Hung <Emmanuel0612@users.noreply.github.com>
Co-authored-by: HaiShaw <hixiao@gmail.com>

### [1c06c16](https://github.com/sgl-project/sglang/commit/1c06c160f99c35c910014c7c6c339078d7d9adea)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-11T07:35:27Z
- **提交信息**: [Docs] Add Ling-3.0-flash INT4 and MXFP4 recipes (#34363)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1246
- **最后更新**: 2026-08-11T12:09:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88796
- **最后更新**: 2026-08-11T22:26:12Z

## 提交统计

- **昨日提交总数**: 41
- **提交者数量**: 35
- **主要提交者**: Jiangyun Zhu, David Holtz, Taneem Ibrahim

## AI分析总结

## 提交分析总结

### 一、主要更新类型

本批次共41个提交，涵盖**Bug修复**（约15个）、**性能优化**（约8个）、**功能新增**（约6个）、**重构与清理**（约5个）、**CI/测试改进**（约4个）、**文档更新**（约3个）。

### 二、关键变更点与项目方向

**1. KV-Cache布局重构持续推进**：多个提交围绕KV缓存布局重构展开，包括通过class-changing replace helper提升本地KV缓存规格、将KV块清零泛化到AttentionSpec、修复KV-first注意力块在混合模型中的分页问题。这与vLLM追求高性能推理的核心目标一致，是底层架构演进的重要环节。

**2. ROCm/AMD平台支持显著增强**：大量提交针对ROCm平台，包括FlyDSL解码注意力内核（支持4-bit TurboQuant KV缓存）、移除过时的SDPA和skinny GEMM workarounds、修复DeepSeek V4 DSpark启动问题、MoE专家映射修复等。这表明项目正积极扩展AMD硬件生态。

**3. MoE（混合专家）模型优化**：多个提交修复MoE相关问题，包括fused block-scale方向、FlashInfer B12x MoE的GELU tanh支持、共享专家重叠、MoE输出契约定义等，反映项目对大规模MoE模型推理的持续投入。

**4. 推理性能与调度优化**：默认`_max_num_batched_tokens`从8192提升至16384，生成输入在昂贵计算前进行边界约束，避免重复多模态提示更新扫描，这些直接提升服务吞吐量和响应效率。

**5. 新模型与硬件支持**：启用MiniCPMV的CI测试、为Keye模型添加tower和connector LoRA支持、Inkling HF-config兼容、XPU平台多项修复，体现项目对多模型、多硬件平台的广泛适配。

### 三、项目影响与潜在意义

- **架构现代化**：KV-Cache布局重构系列提交为未来更高效的缓存管理奠定基础，可能带来显存利用率和推理速度的显著提升。
- **生态扩展**：ROCm和XPU平台的持续优化，使vLLM从NVIDIA独占走向多硬件支持，扩大用户覆盖面。
- **模型覆盖加深**：对DeepSeek V4、MiniCPMV、Keye等前沿模型的支持，巩固vLLM作为主流LLM服务框架的地位。
- **工程成熟度提升**：大量Bug修复和CI改进表明项目正从快速迭代转向稳定性优先，对生产环境部署至关重要。

### 四、值得关注的技术点

1. **Triton Proton profiling后端**：新增最小化profiling后端，为性能分析提供新工具。
2. **JIT warmup基础设施**：引入新的JIT预热框架，支持谓词过滤，并迁移Inkling FA4，可能显著减少运行时编译开销。
3. **FlashAttention FP8 descales转发**：修复per-head FP8 descales在FA4中的传递，对低精度推理精度有积极意义。
4. **MRV2编码器计时统计**：模型运行器V2支持编码器计时，为多模态模型性能分析提供数据基础。
5. **AR speculator多步解码CUDA图融合**：将自回归推测解码多步融合为单个CUDA图，可能大幅降低推测解码延迟。

### 五、对项目发展的整体影响

vLLM正沿着“**高性能、多硬件、广模型**”的战略路径快速演进。本批次提交体现了三个清晰信号：一是底层架构（KV-Cache、Attention）持续重构以支撑更高性能；二是AMD ROCm和Intel XPU平台投入显著增加，打破GPU厂商绑定；三是对MoE、多模态等前沿模型架构的适配加速。同时，大量Bug修复和CI改进表明项目正从“功能优先”转向“稳定与性能并重”，这对vLLM作为生产级LLM服务框架的定位至关重要。整体来看，这些提交将巩固vLLM在开源LLM推理领域的领先地位，并为其在更广泛硬件生态中的部署铺平道路。

## 详细提交记录

### [a367cdb](https://github.com/vllm-project/vllm/commit/a367cdbca0824c8c428fe15b4552fbc4b824d718)

- **作者**: 鐘天楽
- **时间**: 2026-08-11T21:51:57Z
- **提交信息**: [Profiler] Add minimal Triton Proton profiling backend (#48789)

Signed-off-by: Luossu <zhluosuu@outlook.com>

### [61874f9](https://github.com/vllm-project/vllm/commit/61874f9842bd084cc5e9e348de4b3b6a8f46cdc8)

- **作者**: Lucas Wilkinson
- **时间**: 2026-08-11T21:29:29Z
- **提交信息**: [4/N][KV-Cache Layout Refactor] Promote local KV cache specs via a class-changing replace helper (#51612)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [cb30f6f](https://github.com/vllm-project/vllm/commit/cb30f6f8ddca45fd2e2acc3c43735a7c3b2ecdd3)

- **作者**: Richard Zou
- **时间**: 2026-08-11T21:16:09Z
- **提交信息**: [Testing] Fix test_sharded_state_loader (#51736)

Signed-off-by: Richard Zou <zou3519@gmail.com>

### [3e372c5](https://github.com/vllm-project/vllm/commit/3e372c5ff23438eeeafc86c7d8d51026f3dacb6a)

- **作者**: stefankoncarevic
- **时间**: 2026-08-11T20:52:30Z
- **提交信息**: [Bugfix][ROCm] Give KV-first attention blocks their own page in hybrid models (#51837)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [0f0cb91](https://github.com/vllm-project/vllm/commit/0f0cb918b7c6d08aabb86ec4eff4bae05f6736d9)

- **作者**: Rohan Potdar
- **时间**: 2026-08-11T20:33:02Z
- **提交信息**: [ROCm][MoE] Fix expert_map vs AITER expert_mask for non-AITER experts under EP (#49758)

Signed-off-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [36f4630](https://github.com/vllm-project/vllm/commit/36f4630d8926b8bd16fd6fc80b71e9defce2ad92)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-11T20:05:38Z
- **提交信息**: [Bugfix][MoE] Fix fused block-scale orientation (#50727)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [fd04ede](https://github.com/vllm-project/vllm/commit/fd04edef3e62c8dec19cddd76253c0fc6d56ab62)

- **作者**: Wentao Ye
- **时间**: 2026-08-11T19:44:26Z
- **提交信息**: [Refactor] Delete dead code in models (#51838)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [ded6c45](https://github.com/vllm-project/vllm/commit/ded6c452c3657aad7149cedaf50e88aa83336f8f)

- **作者**: Michael Goin
- **时间**: 2026-08-11T19:32:28Z
- **提交信息**: [Bugfix] Support HF-config compat for Inkling (#51850)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [b2ab096](https://github.com/vllm-project/vllm/commit/b2ab0960178cc737d8537208f1e1de79404ca1ac)

- **作者**: Harry Mellor
- **时间**: 2026-08-11T19:22:56Z
- **提交信息**: [Docs] Fix broken autorefs cross-reference in TurboQuant v2 docstring (#51857)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [cc668c5](https://github.com/vllm-project/vllm/commit/cc668c5b72e7353569a388bb609f1a7644376756)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-11T18:54:56Z
- **提交信息**: [CI][Bugfix][V1] Remove stale FlashAttention metadata arguments (#51854)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [1ab2801](https://github.com/vllm-project/vllm/commit/1ab2801ddebe31b75dd6022c69113b610bbdc950)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-11T18:19:16Z
- **提交信息**: [ROCm] Remove stale SDPA and skinny GEMM workarounds (#50907)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [4f2f31b](https://github.com/vllm-project/vllm/commit/4f2f31b82e03917ef33c9008337909ae418dc323)

- **作者**: Yi Liu
- **时间**: 2026-08-11T18:05:20Z
- **提交信息**: [Bugfix][Attention] Forward per-head FP8 descales through FA4 (#51363)

Signed-off-by: yiliu30 <yi4.liu@intel.com>
Signed-off-by: Yi Liu <yi4.liu@intel.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [52be12c](https://github.com/vllm-project/vllm/commit/52be12cfac0c5a18ba906814b2d2bcadb40a9c4b)

- **作者**: Julien Debache
- **时间**: 2026-08-11T17:06:22Z
- **提交信息**: feat: allow shared expert overlapping for FlashInfer one-sided all-to-all (#50569)

Signed-off-by: jdebache <jdebache@nvidia.com>

### [9cc347a](https://github.com/vllm-project/vllm/commit/9cc347ae424e1c8649b2394fe7fb175e93f59066)

- **作者**: Harry Mellor
- **时间**: 2026-08-11T16:30:39Z
- **提交信息**: Enable `MiniCPMV` for vLLM in CI (#45042)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [ca9c8cb](https://github.com/vllm-project/vllm/commit/ca9c8cbd1bfb6a3fdcd3abf64b7204d967f539f0)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-11T16:25:14Z
- **提交信息**: [CI] Support partial torch requirement contexts (#51832)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [e3fe212](https://github.com/vllm-project/vllm/commit/e3fe212eaf0dc06da03d4df615f7d3d1e8bd5f20)

- **作者**: Michael Goin
- **时间**: 2026-08-11T16:13:09Z
- **提交信息**: [Bugfix] Generalize KV block zeroing to `AttentionSpec` (#51749)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [513f83e](https://github.com/vllm-project/vllm/commit/513f83e7ecee5e39be727fcb7b7de660bd851cf2)

- **作者**: Nick Hill
- **时间**: 2026-08-11T16:10:46Z
- **提交信息**: [Bugfix] Take the sliding window from the layer, not the KV cache group (#51756)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [c65aa2e](https://github.com/vllm-project/vllm/commit/c65aa2ee6cd8286ebe83615afdfab9b77d21f035)

- **作者**: Harry Mellor
- **时间**: 2026-08-11T16:00:51Z
- **提交信息**: Bump Transformers version to 5.15.0 (#51668)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [457a5f3](https://github.com/vllm-project/vllm/commit/457a5f34db04b082239c11ee34601e5ee5754a7c)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-08-11T16:00:49Z
- **提交信息**: [Bugfix][MRV2] Support encoder timing stats in model runner V2 (#50020)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5426311](https://github.com/vllm-project/vllm/commit/5426311d9115c597c561967ec3f277ee6e970420)

- **作者**: aditi-amd
- **时间**: 2026-08-11T15:45:39Z
- **提交信息**: [Kernel][ROCm][Perf] FlyDSL decode-attention kernel for 4-bit TurboQuant KV cache  (#47896)

Signed-off-by: root <root@smci355-ccs-aus-m02-09.cs-aus.dcgpu>
Co-authored-by: root <root@smci355-ccs-aus-m02-09.cs-aus.dcgpu>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d648236](https://github.com/vllm-project/vllm/commit/d648236199da3146af2abd236a6e32ce17cbb178)

- **作者**: liuzhenwei
- **时间**: 2026-08-11T15:40:29Z
- **提交信息**: [XPU][CI] Fix ExampleConnector KV cache device selection (#51806)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [5af7c8d](https://github.com/vllm-project/vllm/commit/5af7c8dad798bf899813f8f3c6b9eaf08a748e17)

- **作者**: Jiangyun Zhu
- **时间**: 2026-08-11T15:35:30Z
- **提交信息**: [Bugfix] Align Qwen GDN gates with speculative tokens (#51812)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [5b5eae2](https://github.com/vllm-project/vllm/commit/5b5eae23944e94f618895c05a69331bb06d1e3bd)

- **作者**: pmanczak
- **时间**: 2026-08-11T15:19:14Z
- **提交信息**: [Misc] Enable test_silu_mul_fp8_quant_deep_gemm on XPU (#49444)

Signed-off-by: pmanczak <pawel.manczak@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [4988df2](https://github.com/vllm-project/vllm/commit/4988df2eb80a8d1debae7de85c3b242fa436f3c1)

- **作者**: Wentao Ye
- **时间**: 2026-08-11T15:09:34Z
- **提交信息**: [Config] Update default `_max_num_batched_tokens` from 8192 to 16384 (#51726)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [0fb9897](https://github.com/vllm-project/vllm/commit/0fb9897df12963e9bd0d58547fc997e0702d95ec)

- **作者**: Andrii Skliar
- **时间**: 2026-08-11T15:07:58Z
- **提交信息**: [Bugfix][MoE] Support GELU tanh in FlashInfer B12x MoE (#51819)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [87668ab](https://github.com/vllm-project/vllm/commit/87668ab69b3e2c849a607ece36e8a43bde7c7ee5)

- **作者**: Woosuk Kwon
- **时间**: 2026-08-11T14:34:44Z
- **提交信息**: [Bugfix] Guard DeepSeek V4 MRV1 piecewise CUDA graphs (#51768)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [dd7cc85](https://github.com/vllm-project/vllm/commit/dd7cc85f1720ebcb65b1822cbc5054af66ae292d)

- **作者**: Jee Jee Li
- **时间**: 2026-08-11T14:23:59Z
- **提交信息**: Add MoE output contract for MoE tail fusion (#51407)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [12bea3e](https://github.com/vllm-project/vllm/commit/12bea3eedcdf8e049f2478739b45ccb1456c03c0)

- **作者**: Tuukka Sarvi
- **时间**: 2026-08-11T14:15:31Z
- **提交信息**: [Bugfix][ROCm] Fix DeepSeek V4 DSpark probabilistic startup (#51145)

Signed-off-by: Tuukka Sarvi <tuukka.sarvi@amd.com>

### [b64a270](https://github.com/vllm-project/vllm/commit/b64a2708b06b6329420702bffce994543c1ec6d2)

- **作者**: Clinton Thomas
- **时间**: 2026-08-11T14:03:50Z
- **提交信息**: Bound generation inputs before expensive work (#51447)

Signed-off-by: Clinton Thomas <1033162+KernelClint@users.noreply.github.com>
Co-authored-by: Lucas Bourtoule <35483370+dhalf@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5b184f7](https://github.com/vllm-project/vllm/commit/5b184f775ae0f71d20cee222314b8866fb2b9d3c)

- **作者**: Louie Tsai
- **时间**: 2026-08-11T13:53:51Z
- **提交信息**: connects vLLM Recipes with vLLM's native config-based deployment and benchmark (#51308)

Signed-off-by: louie-tsai <louie.tsai@intel.com>

### [f863387](https://github.com/vllm-project/vllm/commit/f863387250cfc24c04d07b3593ea18a541ba2b8a)

- **作者**: Chaojun Zhang
- **时间**: 2026-08-11T13:48:44Z
- **提交信息**: [XPU] Fix UVA weight offloading (non-pinned-tensor views and static Triton launcher) (#51770)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [78e7fdd](https://github.com/vllm-project/vllm/commit/78e7fdd1ab81d4203a7522c2bf197b3a4b2b48cb)

- **作者**: Kush Zingade
- **时间**: 2026-08-11T13:35:07Z
- **提交信息**: [Bugfix][CPU] Make the Apple Silicon BF16 probe fall back instead of raising (#51627)

Signed-off-by: Kush Zingade <kush.zingade@gmail.com>

### [6c95a64](https://github.com/vllm-project/vllm/commit/6c95a641e95c0faa6f3aa802d1fd3cce3f3bc3ce)

- **作者**: Roberto L. Castro
- **时间**: 2026-08-11T11:46:07Z
- **提交信息**: [2/N][Feat][Perf] Add new warmup infrastructure for JITs. Add predicate filtering for JIT warmup, and migrate Inkling FA4 (#49315)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Signed-off-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d8f8400](https://github.com/vllm-project/vllm/commit/d8f840071efd631f71b06d4b31cb6dba2275a356)

- **作者**: liushujia122
- **时间**: 2026-08-11T10:35:59Z
- **提交信息**: [Model] Enable tower and connector LoRA for Keye (#51780)

Signed-off-by: shujialiu <liushujia0122@163.com>

### [0fec3d6](https://github.com/vllm-project/vllm/commit/0fec3d652babd3a4a2919ff7b19a35701b298426)

- **作者**: AlexHuang
- **时间**: 2026-08-11T10:22:15Z
- **提交信息**: [Bugfix][KV Offload] Centralize shared mmap cleanup in CPU worker (#51622)

Signed-off-by: Alex <jihui.huang@daocloud.io>

### [ce07118](https://github.com/vllm-project/vllm/commit/ce07118669a8a0a7d8ea66d2ac08787c88c25938)

- **作者**: Dao007forever
- **时间**: 2026-08-11T10:15:24Z
- **提交信息**: [Bugfix][Core] Preserve Mamba running CoW after external hits (#51766)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [490259c](https://github.com/vllm-project/vllm/commit/490259c1f63faf025b8050504db63d81c817d781)

- **作者**: David Holtz
- **时间**: 2026-08-11T09:38:58Z
- **提交信息**: profiler: add PrivateUse1 activity support for custom backends (#50977)

Signed-off-by: David Holtz <56723830+dmholtz@users.noreply.github.com>

### [3fb7bb4](https://github.com/vllm-project/vllm/commit/3fb7bb46d6202e23988c96746891ec788ee6aaf5)

- **作者**: Tianyu Guo
- **时间**: 2026-08-11T09:23:24Z
- **提交信息**: [Perf] Avoid repeated multimodal prompt update scans (#51774)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [52c70b2](https://github.com/vllm-project/vllm/commit/52c70b210ce9d66e9afb9d18e086c3d05408c492)

- **作者**: zofia
- **时间**: 2026-08-11T08:43:33Z
- **提交信息**: [XPU] [Linear] enable torch linear backend for blockwise  gemm on xpu (#50826)

Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [529d010](https://github.com/vllm-project/vllm/commit/529d0103511429f0086a308b6ef2698a87fec4b9)

- **作者**: Kyungmin Lee
- **时间**: 2026-08-11T08:17:05Z
- **提交信息**: [Doc] Fix typos in speculative decoding docs (#51500)

Signed-off-by: lkm2835 <lkm2835@gmail.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [a311916](https://github.com/vllm-project/vllm/commit/a311916a291c1fed3dbfb72e60f74cd778c8419d)

- **作者**: Yizhou
- **时间**: 2026-08-11T07:06:22Z
- **提交信息**: [MRV2][Spec] Fuse AR speculator multi-step decodes back into one CUDA graph (#46849)

Signed-off-by: Yizhou Liu <liu_yizhou@outlook.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-12
**监控日期**: 2026-08-11
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6042
- **最后更新**: 2026-08-11T22:19:24Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 9
- **主要提交者**: Zhou Taichang, Weiyan, Nick Cao

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本次提交涵盖**功能新增**（LoRA支持、新模型接入、MUSA硬件适配）、**性能优化**（注意力掩码跳过）、**文档更新**（用户指南、模型配方）、**代码重构**（Rebase至vLLM 0.27.0）、**测试完善**（MiniCPM-o测试对齐、FluxKontextPipeline测试构建器）以及**硬件平台扩展**（MUSA接口补全）六大类。

### 2. 关键变更点与项目方向的关系

- **Rebase至vLLM 0.27.0**：这是最核心的变更，确保vllm-omni与上游vLLM保持同步，为后续功能开发和性能优化奠定基础，直接支撑项目“易用、快速、低成本”的定位。
- **MUSA硬件支持**（两项提交）：补全Omni平台接口并启用Qwen3-Omni的FP8推理，体现项目对多硬件生态的重视，扩大部署场景覆盖面。
- **蒸馏LoRA支持**：为扩散模型引入蒸馏LoRA能力，契合项目“低成本”目标——用户可通过轻量化微调适配模型，降低推理资源消耗。
- **LongCat-Video-Avatar-1.5接入**：新增音频到视频、音频到文本到视频能力，强化全模态（omni-modality）服务能力，与项目核心定位一致。
- **性能优化**：跳过注意力掩码以避免varlen路径，针对Flux2和HunyuanVideo1.5的推理加速，体现项目对生成式模型性能的持续关注。

### 3. 对项目的影响和潜在意义

- **生态兼容性提升**：Rebase确保与最新vLLM特性兼容，避免因版本滞后导致的功能缺失或bug。
- **硬件覆盖扩大**：MUSA支持使项目可运行于更多国产硬件平台，增强在国内市场的适用性。
- **模型丰富度增强**：新模型接入和LoRA支持吸引更多用户和开发者，形成正向社区循环。
- **测试体系完善**：新增测试构建器和测试对齐，提升代码质量保障，降低回归风险。

### 4. 值得关注的技术点

- **蒸馏LoRA与扩散模型的结合**：这是较新的技术方向，可能涉及权重合并、推理加速等复杂实现，值得关注其设计思路。
- **MUSA平台FP8推理**：FP8量化在国产硬件上的落地，涉及算子适配和精度调优，技术含量较高。
- **注意力掩码跳过优化**：通过避免varlen路径减少计算开销，属于细粒度性能调优，对长序列生成场景收益明显。
- **Rebase过程中的冲突处理**：涉及多文件合并，需关注是否有功能遗漏或行为变更。

### 5. 对项目发展的影响

结合README中“为每个人提供简单、快速、低成本的omni模态模型服务”的愿景，本次提交从三个维度推动项目前进：**广度**上扩展硬件支持和模型类型，**深度**上通过性能优化和Rebase提升底层效率，**厚度**上完善测试和文档增强可靠性。特别是MUSA支持和蒸馏LoRA，分别对应“低成本”和“易用”两大关键词，有助于项目在竞争激烈的多模态推理框架中建立差异化优势。整体来看，这些提交体现了项目在保持技术前沿性的同时，注重实用性和生态建设，为后续吸引更多硬件厂商和模型开发者参与奠定了良好基础。

## 详细提交记录

### [1ff2753](https://github.com/vllm-project/vllm-omni/commit/1ff275346923cb5c9339bd38e0a594b9aaaa427b)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-11T16:20:56Z
- **提交信息**: docs: align User Guide feature taxonomy (#6045)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [4697bd1](https://github.com/vllm-project/vllm-omni/commit/4697bd1be0606b4d4f1fd52b5b8394870016b5ad)

- **作者**: SYLAR
- **时间**: 2026-08-11T15:53:58Z
- **提交信息**: [Docs] Add MiniMax-H3 recipe for RTX PRO 5000 (#5857)

Signed-off-by: lishunyang12 <lishunyang12@163.com>

### [2ce15ab](https://github.com/vllm-project/vllm-omni/commit/2ce15ab7a023d4fb800629e36c06bbe75a4324e2)

- **作者**: Zhou Taichang
- **时间**: 2026-08-11T15:23:46Z
- **提交信息**: [Rebase] Rebase to vllm 0.27.0 (#5976)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [584d78c](https://github.com/vllm-project/vllm-omni/commit/584d78c673fe7836809c2a197c3f4843e2fd9ac4)

- **作者**: Nick Cao
- **时间**: 2026-08-11T14:59:09Z
- **提交信息**: [Test] Add tiny model builder for FluxKontextPipeline (#5823)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [89015d5](https://github.com/vllm-project/vllm-omni/commit/89015d5cad0a55dc970fdde1badaf74d39b8c4f7)

- **作者**: Jerry Song
- **时间**: 2026-08-11T14:23:43Z
- **提交信息**: [Feature]: Adds distilled LoRA support for diffusion models (#2783)

Signed-off-by: Songrui625 <songrui625@gmail.com>

### [348cf95](https://github.com/vllm-project/vllm-omni/commit/348cf95a895061a403ce3b611b45b36fb24ebc61)

- **作者**: amy-why-3459
- **时间**: 2026-08-11T13:11:39Z
- **提交信息**: [CI][MiniCPM-o] Align MiniCPM-o 4.5 online serving tests with minicpm… (#6056)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [22dd96e](https://github.com/vllm-project/vllm-omni/commit/22dd96ec5c0fa25667ef186c31e199ba7809ae50)

- **作者**: R0CKSTAR
- **时间**: 2026-08-11T12:46:42Z
- **提交信息**: [Hardware][MUSA] Complete Omni platform interfaces (#6058)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [e04210d](https://github.com/vllm-project/vllm-omni/commit/e04210d690d619d6da34cbce3ae98e6fa31398bb)

- **作者**: R0CKSTAR
- **时间**: 2026-08-11T09:19:09Z
- **提交信息**: [Hardware][MUSA] Enable Qwen3-Omni ModelOpt FP8 inference (#5671)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4ab1b4f](https://github.com/vllm-project/vllm-omni/commit/4ab1b4ff9cfc2ca233cccb5a4ba1f845288278fc)

- **作者**: Kristoffer
- **时间**: 2026-08-11T07:31:02Z
- **提交信息**: [Perf][Flux2][HunyuanVideo1.5] Skip attention-mask to avoid varlen path (#4645)

Signed-off-by: kTorp <Kristoffer.Torp@amd.com>
Signed-off-by: Didan Deng <33117903+wtomin@users.noreply.github.com>
Co-authored-by: Didan Deng <33117903+wtomin@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [06e733d](https://github.com/vllm-project/vllm-omni/commit/06e733d3cd4400bb0029f8418e2207f1441a39c0)

- **作者**: Weiyan
- **时间**: 2026-08-11T07:17:17Z
- **提交信息**: [Model] Add LongCat-Video-Avatar-1.5 ai2v,  at2v support (#4099)

Signed-off-by: weiyan <weiyanlin117@gmail.com>
Signed-off-by: Didan Deng <33117903+wtomin@users.noreply.github.com>
Co-authored-by: Didan Deng <33117903+wtomin@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
