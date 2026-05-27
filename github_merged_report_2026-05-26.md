# GitHub Stars 合并报告 - 2026-05-26

**合并日期**: 2026-05-27
**监控日期**: 2026-05-26
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


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1950
- **最后更新**: 2026-05-27T10:42:08Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Ting, 鐘天楽

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的要点分析：

### 1. 主要更新类型
- **Bug修复**：修复了在MoE（混合专家）和VLM（视觉语言模型）训练场景下，使用DCP（分布式检查点）保存时可能出现的HBM（高带宽内存）OOM（内存溢出）问题。
- **版本发布**：将项目版本从0.1.10升级到0.1.11。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更点**：
    - **`af84378`**：针对`ckpt`（检查点）和`trainer`（训练器）模块，修复了在MoE和VLM训练中，DCP保存操作导致HBM内存溢出的Bug。
    - **`f90b3dc`**：执行了版本号更新，标志着一次新的稳定版本发布。
- **与项目方向的关系**：
    - VeOmni的核心目标是“**Scaling Any Modality Model Training**”（扩展任意模态模型的训练）。MoE和VLM正是多模态和大型模型训练中的关键且资源密集的场景。
    - 修复DCP保存时的OOM问题，直接提升了项目在处理**大规模、高内存消耗**模型（如MoE和VLM）时的**稳定性和可靠性**。这确保了VeOmni能够真正支持“任意模态”模型的规模化训练，而不会在关键的检查点保存环节崩溃。

### 3. 对项目的影响和潜在意义
- **直接影响**：解决了用户在使用VeOmni训练MoE或VLM模型时，因保存检查点而导致的训练中断或失败问题。这显著提升了用户体验和训练任务的完成率。
- **潜在意义**：
    - **增强项目可信度**：修复此类高难度、资源敏感型Bug，证明了VeOmni在处理前沿模型架构（如MoE）和复杂多模态任务（如VLM）时的工程成熟度。
    - **降低使用门槛**：用户无需再为保存检查点而手动调整内存策略或担心训练白费，使得VeOmni对更大规模、更复杂模型的训练支持更加“开箱即用”。

### 4. 值得关注的技术点
- **DCP (Distributed Checkpoint)**：这是PyTorch等框架中用于分布式训练检查点保存的关键技术。修复其OOM问题，表明团队对分布式训练底层机制有深入理解。
- **MoE (Mixture of Experts) 与 VLM (Vision-Language Model)**：这两个模型架构通常具有极大的参数量和动态的计算图，对内存管理是巨大挑战。修复此Bug的技术难点在于如何在保存模型状态时，不额外占用大量HBM，避免与训练过程争抢内存。
- **HBM OOM**：这是大模型训练中最常见也最棘手的问题之一。此修复可能涉及了更高效的内存拷贝、序列化或流式保存策略。

### 5. 基于项目背景，这些提交如何影响项目发展
- **巩固核心能力**：VeOmni的定位是“Model-Centric Distributed Recipe Zoo”（以模型为中心的分布式配方动物园）。一个稳定、可靠的检查点系统是所有“配方”能够成功运行并从中断中恢复的基础。此次修复巩固了这一核心基础设施。
- **推动规模化训练**：通过解决MoE/VLM场景下的内存瓶颈，VeOmni向社区证明了它有能力处理当前AI领域最前沿、最“吃”内存的模型训练任务。这有助于吸引更多研究者和工程师使用VeOmni来探索更大规模的模型。
- **版本迭代信号**：从0.1.10到0.1.11的快速版本迭代，表明项目处于活跃开发期，并且团队重视稳定性和用户反馈。这为潜在用户和贡献者提供了信心。

## 详细提交记录

### [af84378](https://github.com/ByteDance-Seed/VeOmni/commit/af84378350e288d4fbef8bcd911594214688aaf1)

- **作者**: Ting
- **时间**: 2026-05-26T14:14:53Z
- **提交信息**: [ckpt, trainer] fix: avoid HBM OOM during DCP save under MoE / VLM training (#791)

### [f90b3dc](https://github.com/ByteDance-Seed/VeOmni/commit/f90b3dc6fbb0ce693745223cc7a94064123dbf4d)

- **作者**: 鐘天楽
- **时间**: 2026-05-26T07:41:34Z
- **提交信息**: [release] chore: bump version to 0.1.11 (#792)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2300
- **最后更新**: 2026-05-27T13:32:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2098
- **最后更新**: 2026-05-27T12:57:37Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5689
- **最后更新**: 2026-05-27T11:49:57Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Vincent, Brian K. Ryu, Wenxuan Tan

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **性能优化**: 提交 `[d53f106]` 和 `[0b755de]` 的核心目标。
- **Bug修复**: 提交 `[96ab2ce]` 修复了处理超大张量时的整数溢出问题。
- **功能新增**: 提交 `[d53f106]` 为 MNNVL 引入了 FP8/NVFP4 量化融合功能；提交 `[0b755de]` 为 MLA Decode 增加了自动调优功能。
- **工具/调试改进**: 提交 `[c802a05]` 优化了性能分析器 (Profiler) 的 Perfetto 追踪输出。

### 2. 关键变更点及其与项目整体方向的关系

FlashInfer 项目的核心目标是提供**高性能的 GPU 推理内核**。所有提交都紧密围绕这一目标：

- **`[d53f106]` MNNVL Allreduce 量化融合与性能优化**:
    - **变更**: 优化了 MNNVL (多节点 NVLink) 场景下的 Allreduce 通信内核。通过使用命名屏障、避免冗余数据加载、调整线程块调度策略，并扩展了 FP8/NVFP4 量化融合支持。
    - **与项目方向**: 直接提升了**大规模分布式推理**的性能和效率，这是现代大模型部署的关键瓶颈。量化融合进一步减少了显存占用和带宽需求。

- **`[0b755de]` MLA Decode 跨后端自动调优**:
    - **变更**: 为 MLA (Multi-head Latent Attention) Decode 操作引入了自动调优功能，使其能在 `trtllm-gen` 和 `cute-dsl` 两个后端之间自动选择性能更优的一个。
    - **与项目方向**: 体现了项目对**极致性能**的追求。通过自动化、细粒度的后端选择，确保在不同硬件和模型配置下都能获得最佳性能，提升了项目的通用性和易用性。

- **`[96ab2ce]` 修复大输入张量的地址计算溢出**:
    - **变更**: 修复了在归一化 (Norm) 内核中，当输入张量元素数量超过 2^31 时，因使用 32 位整数计算地址而导致的 `cudaErrorIllegalAddress` 错误。
    - **与项目方向**: 这是对**正确性和鲁棒性**的关键修复。随着模型规模增长，处理超大张量是必然需求，此修复确保了 FlashInfer 能稳定支持更大规模的模型推理。

- **`[c802a05]` 优化 Profiler 追踪输出**:
    - **变更**: 改进了 Perfetto 追踪的展示方式，将线程块按 SM (Streaming Multiprocessor) 分组，并合并事件轨道，使 SM 利用率一目了然。
    - **与项目方向**: 虽然不直接提升推理性能，但**改进了开发者体验和调试效率**。清晰的性能分析工具能帮助开发者更快地定位性能瓶颈，从而进行后续优化，间接支持了项目的高性能目标。

### 3. 对项目的影响和潜在意义

- **性能提升**: MNNVL 优化和 MLA 自动调优将直接带来可量化的性能提升，尤其是在多节点、大规模部署和特定注意力机制场景下。
- **扩展性与可靠性**: 修复大张量地址溢出问题，为 FlashInfer 支持更大规模的模型（如万亿参数级）扫清了障碍，增强了项目的可靠性。
- **功能完整性**: 引入 MNNVL 量化融合和 MLA 自动调优，填补了在分布式推理和高级注意力机制优化方面的功能空白，使 FlashInfer 成为一个更全面的推理加速库。
- **开发者友好度**: Profiler 的改进降低了性能分析的门槛，有助于吸引更多开发者贡献和优化。

### 4. 值得关注的技术点

- **命名屏障 (Named Barrier) 与集群屏障 (Cluster Barrier)**: 在 `[d53f106]` 中用于替代简单的 `__syncthreads()`，是 CUDA 高级同步原语，能实现更细粒度的线程块间同步，减少不必要的等待，是提升 GPU 通信效率的关键技术。
- **模板化快速路径 (Template-based fast path)**: 在 `[d53f106]` 中，针对 `world size <= 8` 的情况使用模板化路径，避免了运行时分支和动态计算，是典型的编译时优化技巧。
- **自动调优 (Autotuning)**: `[0b755de]` 展示了如何通过自动调优解决“没有银弹”的问题，即不同后端在不同配置下各有优劣，通过运行时或编译时自动选择最优方案。
- **Int64 地址计算**: `[96ab2ce]` 的修复强调了在处理现代大模型时，必须警惕 32 位整数溢出的陷阱，尤其是在计算内存偏移量时，使用 `int64` 是必要的。

### 5. 这些提交如何影响项目发展

结合 README 中“高性能 GPU 推理内核”的定位，这些提交清晰地展示了 FlashInfer 的发展方向：

1.  **从单机到多机**: `[d53f106]` 表明项目正积极应对**多节点 (MNNVL)** 推理的挑战，这是从单 GPU 优化向分布式系统优化的自然演进，以满足大模型部署的实际需求。
2.  **从通用

## 详细提交记录

### [c802a05](https://github.com/flashinfer-ai/flashinfer/commit/c802a05d9806a3d8ec72014f9cec4d67da0d5e8e)

- **作者**: Wenxuan Tan
- **时间**: 2026-05-26T23:41:09Z
- **提交信息**: profiler: group perfetto traces by SM, one row per block (#3038)

## Summary
- Group blocks by SM ID in perfetto trace hierarchy instead of one
top-level group per block. Blocks on the same SM appear as adjacent rows
under a single `SM_XXX` tab.
- Collapse all events for a (block, group) pair onto one track instead
of one track per event type, reducing visual clutter from O(blocks ×
groups × events) to O(blocks × groups).

**Before:** `block_0 > group_0 > [separate track per event]` — blocks
scattered, no SM locality visible.

**After:** `SM_042 > blk0_g0` (all events inline) — co-located blocks
are visually adjacent, SM utilization visible at a glance.
<img width="2564" height="282" alt="image"
src="https://github.com/user-attachments/assets/80c6d50d-77d0-4612-ba83-a01ec0350881"
/>

## Test plan
- [ ] Open a profiler trace in Perfetto UI and verify blocks are grouped
by SM
- [ ] Verify all events for a block appear on a single track line
- [ ] Compare with old layout to confirm no data loss

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Perfetto traces now group events by SM, consolidating related events
and reducing duplicated tracks by sharing a single track per block/group
for clearer profiling timelines.
  * More consistent and accurate profiling output for improved analysis.

* **Chores**
* MOE finalize flow now sends explicit null placeholders for certain
optional outputs to the backend, ensuring consistent runtime behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Zihao Ye <expye@outlook.com>

### [0b755de](https://github.com/flashinfer-ai/flashinfer/commit/0b755de7060980b6ced02359aac6921aef5418d2)

- **作者**: Vincent
- **时间**: 2026-05-26T21:18:19Z
- **提交信息**: MLA Decode Autotuning Across TRTLLM-Gen and CuTe Backends (#3355)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

This PR enables autotuning between the "trtllm-gen" and "cute-dsl"
backends in the `trtllm_batch_decode_with_kv_cache_mla` API when running
with `backend="auto"` and `flashinfer.autotune(true)`.

## Autotuner Performance Results

With a cold kernel cache, each layer takes ~5 minutes to autotune.
Otherwise with a warm kernel cache, autotuning the layer takes 5
seconds.

The following table contains the speedups of running
`trtllm_batch_decode_with_kv_cache_mla` with `backend="auto"` and
`flashinfer.autotune(true)` before vs. after this PR on a B200 machine.

  | batch \ s_kv | 512 | 1024 | 2048 | 4096 | 8192 |
  |---:|---:|---:|---:|---:|---:|
  | **1** | 1.17× | 1.31× | 1.21× | 1.44× | 1.50× |
  | **2** | 1.17× | 1.31× | 1.27× | 1.29× | 1.60× |
  | **4** | 1.15× | 1.36× | 1.38× | **1.63×** | 1.17× |
  | **8** | 1.14× | 1.44× | **1.68×** | 1.17× | 1.12× |
  | **16** | 1.12× | **1.53×** | 1.08× | 1.06× | 1.06× |
  | **32** | 1.00× | 1.04× | 1.06× | 1.06× | 1.04× |
  | **64** | 1.14× | 1.10× | 1.08× | 1.08× | 1.07× |
  | **128** | 0.95× | 1.00× | 1.02× | 1.02× | 1.00× |
  | **256** | 1.00× | 1.00× | 1.00× | 1.00× | 0.99× |

This aligns with expectations, as previously we found the "cute-dsl"
backend to be faster for smaller batch sizes.

## 🔍 Related Issues

<!-- Link any related issues here -->

This is requested in [issue
2891](https://github.com/flashinfer-ai/flashinfer/issues/2891#event-24551929489).

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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a --autotune CLI to the MLA paged-attention benchmark to run
warmup/autotune passes before timing.
* Enabled autotuning for MLA batch decode with automatic backend
dispatch and dynamic batch tuning; expanded backend availability on
select hardware.

* **Tests**
* Added end-to-end autotune smoke tests for MLA decode using the auto
backend.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3355?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [96ab2ce](https://github.com/flashinfer-ai/flashinfer/commit/96ab2cedc0f35def8929d12f831d299493ad261c)

- **作者**: Brian K. Ryu
- **时间**: 2026-05-26T20:49:17Z
- **提交信息**: fix(norm): widen address arithmetic to int64 for large contiguous inputs > 2**31 elements (#3392)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Fix cudaErrorIllegalAddress in the cute-DSL norm kernels (`rmsnorm`,
`gemma_rmsnorm`, `rmsnorm_quant`, `fused_add_rmsnorm`,
`gemma_fused_add_rmsnorm`, `fused_add_rmsnorm_quant`, `layernorm`, and
`qk_rmsnorm`) when the input tensor's flat element count exceeds
`2**31`.

**Root Cause**
The compact (contiguous) compile path bakes the row stride in as a
Python constexpr integer, and M / B / N were declared as `Int32`
everywhere. The row coord materialized into the offset comes from
`cute.arch.block_idx()`, which is intrinsically `int32`, so the compiler
emits `row * H` in `int32` and overflows whenever `M * H > INT32_MAX`.
For shape (175000, 12288) fp16 (174999 * 12288 ≈ 2.15e9) this manifests
as `cudaErrorIllegalAddress` on the first `cudaStreamSynchronize`. The
strided compile path was already safe because its row stride was already
a dynamic `sym_int64`, but the contiguous path was not.

A secondary bug existed in `flashinfer/norm/utils.py::get_ptr_as_int64`,
which truncated its offset parameter to Int32 before adding it to the
base pointer — so even a correctly-computed `int64` element offset was
being downcast in the rmsnorm-quant kernels' manual FP8 store path.

## 🔍 Related Issues

<!-- Link any related issues here -->

#3391

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Resolved integer-overflow issues in normalization (RMSNorm, LayerNorm,
fused Add+RMSNorm and FP8-quantized variants) for very large tensors,
preventing illegal memory accesses and ensuring correct addressing for
huge row counts.
* Forced a safe compilation/execution path for contiguous inputs when
dimensions exceed 32-bit limits.

* **Tests**
* Added regression tests that detect contiguous overflow scenarios
across normalization variants, with VRAM-aware gating and spot-check
validation.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3392?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d53f106](https://github.com/flashinfer-ai/flashinfer/commit/d53f10682cfdc13c12d3463b2559355b9eb1671d)

- **作者**: Shiyu Li
- **时间**: 2026-05-26T17:24:42Z
- **提交信息**: feat: MNNVL Allreduce quant fusion and performance optimization  (#3385)

<!-- .github/pull_request_template.md -->

## 📌 Description
- Use named barrier and cluster barrier instead of a sync.
- Avoid loading local buffer again in oneshot, use template-based fash
path for world size <= 8.
- Adjust grid dispatch policy to use more SMs at the cost of single SM
occupancy for small batch sizes.
- Extended allreduce_fusion so MNNVL supports standard FP8/NVFP4 quant
patterns while keeping MoE and packed-group quant paths TRTLLM-only.
(replace #2263 )
- Added Hopper/Blackwell-only JIT arch gating.
- Added focused correctness coverage for quant fusion across dtype,
strategy, layout, shape, and norm-output variants, plus NVFP4 validation
for padded swizzled scale buffers.

**Performance Change Dashboard:
[report.html](https://github.com/user-attachments/files/28164512/report.html)**

For M <= 8, fused oneshot is 6.24% faster latency-weighted and ar_only
oneshot is 4.26% faster. The main benefit is from avoiding loading the
local buffer in lamport polling.
Fused two-shot gets benefit for relatively larger batch size. The main
benefit is from reducing CTA sync overhead by using named barrier
instead of syncthread.
 
## 🔍 Related Issues

None
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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* FP8 and NVFP4 quantized AllReduce + residual-add + RMSNorm fusion with
optional quant outputs, scale outputs, and configurable scale layouts;
expanded fusion patterns and execution strategies (oneshot/twoshot).

* **Behavior / Validation**
* Stricter shape/dtype/layout checks, default swizzled layout, explicit
errors for unsupported quant/layout/CUDA combos, and enforced coupling
of quantization with RMSNorm and scale tensors.

* **Documentation**
* Updated API docs and examples describing quantization patterns,
layouts, and strategy/reduction-order behavior.

* **Tests**
* End-to-end FP8/NVFP4 tests added, including negative tests validating
invalid NVFP4/scale cases.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3385?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Shiyu Li <shili@nvl72d081-T12.cm.cluster>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3516
- **最后更新**: 2026-05-27T08:18:45Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Shao Duan, alexzms, William Lin

## AI分析总结

好的，这是对 `hao-ai-lab/FastVideo` 仓库昨日提交记录的分析总结：

### 1. 主要更新类型

- **功能新增 (feat):** 2项
- **文档更新 (docs):** 2项
- **Bug修复 (bug fixes):** 1项（包含在功能提交中）

### 2. 关键变更点及其与项目整体方向的关系

- **评估系统升级 (3668279):**
    - **变更点:** 改进了评估（eval）模块的输入易用性（ergonomics），新增了评估器（Evaluator）功能，并修复了相关Bug。
    - **与项目关系:** 评估是衡量模型性能、指导迭代优化的核心环节。此提交直接提升了FastVideo作为视频生成框架的**可测试性和迭代效率**，是项目走向成熟和易用的关键一步。

- **Blackwell架构性能优化 (be548a7):**
    - **变更点:** 为NVIDIA最新的Blackwell架构GPU实现了VSA-256的快速路径（fastpath），该路径利用了FA4 (Flash Attention 4) 的CuTe块稀疏注意力（block-sparse attention）技术。
    - **与项目关系:** 这表明FastVideo致力于**紧跟最新硬件趋势**，并利用前沿的稀疏计算技术来最大化性能。这直接关系到项目在高端硬件上的**推理/训练速度**和**竞争力**。

- **文档与开发者体验提升 (0ef1357, a75d197):**
    - **变更点:** 将“激活追踪（activation-trace）”工具集成到“添加模型”的技能文档中，并将其纳入了MkDocs导航，同时补充了性能/故障排查文档。
    - **与项目关系:** 这些更新显著降低了新模型接入的门槛，并提供了性能调优的指导。这有助于**扩大社区贡献**，并提升**开发者使用体验**，符合项目README中强调的“Quick Start”和文档化目标。

### 3. 对项目的影响和潜在意义

- **评估系统升级:** 使得用户和开发者能更便捷、更准确地评估模型效果，加速模型迭代和优化，对提升最终生成视频的质量有直接帮助。
- **Blackwell性能优化:** 确保了FastVideo在下一代NVIDIA GPU上的领先性能，吸引了高端用户和开发者，并展示了项目在底层优化上的技术深度。
- **文档更新:** 降低了新开发者的参与门槛，使项目更易上手，有助于构建更活跃的社区生态，并提升项目的专业形象。

### 4. 值得关注的技术点

- **FA4 CuTe块稀疏注意力:** 这是一个非常前沿的技术点。它利用NVIDIA的CuTe库和Flash Attention 4，通过块稀疏的方式计算注意力，在保证精度的同时大幅减少计算量，是实现Blackwell VSA-256 fastpath的核心技术。
- **激活追踪 (activation-trace) 工具:** 这是一个用于性能分析和调试的实用工具，能帮助开发者理解模型在运行时的行为，对优化和排查问题至关重要。

### 5. 基于项目背景，这些提交如何影响项目发展

- **从“能用”到“好用”:** 评估系统的易用性改进和文档的完善，标志着FastVideo正从功能实现阶段，向**提升用户体验和开发者友好度**的阶段迈进。
- **抢占技术制高点:** 对Blackwell架构的快速适配，体现了项目团队对**前沿硬件和算法**的敏锐度。这不仅能吸引追求极致性能的用户，也为项目在未来的技术竞争中占据了有利位置。
- **构建良性循环:** 更好的评估工具和更完善的文档，会吸引更多开发者贡献新模型和优化方案。而针对新硬件的性能优化，则能吸引更多用户使用，从而形成**用户增长 -> 社区贡献 -> 项目进步**的良性循环。

## 详细提交记录

### [3668279](https://github.com/hao-ai-lab/FastVideo/commit/36682797a0bcb86ae2450d670602953708933d5e)

- **作者**: Shao Duan
- **时间**: 2026-05-26T20:59:45Z
- **提交信息**: [feat] eval: input ergonomics + Evaluator features + bug fixes (#1392)

### [0ef1357](https://github.com/hao-ai-lab/FastVideo/commit/0ef1357a772bd8c1523e05d43f820d66a4da0474)

- **作者**: William Lin
- **时间**: 2026-05-26T20:45:12Z
- **提交信息**: [docs]: surface activation-trace utility in add-model skills (#1399)

### [a75d197](https://github.com/hao-ai-lab/FastVideo/commit/a75d19786a99694ce45c7f442fde9269fa3168a6)

- **作者**: William Lin
- **时间**: 2026-05-26T20:14:36Z
- **提交信息**: [docs]: Wire activation trace into mkdocs nav + perf/troubleshooting (#1304)

### [be548a7](https://github.com/hao-ai-lab/FastVideo/commit/be548a78eab190c4d03e48d5a284c78e06b69990)

- **作者**: alexzms
- **时间**: 2026-05-26T19:58:29Z
- **提交信息**: [feat] VSA-256 fastpath on Blackwell via FA4 CuTe block-sparse attention (#1354)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33710
- **最后更新**: 2026-05-27T14:05:08Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: hf-dependantbot-rollout[bot]

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **基础设施/流程优化**：本次提交属于项目维护和自动化流程改进，而非直接的功能新增或Bug修复。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：启用了Dependabot对GitHub Actions进行每周自动更新（`chore: enable Dependabot weekly GitHub Actions bumps`）。
- **与项目方向的关系**：`diffusers` 作为一个快速迭代、依赖众多（如PyTorch、Transformers等）的扩散模型库，其CI/CD流程的稳定性至关重要。通过自动化更新GitHub Actions依赖，可以减少手动维护成本，确保构建、测试和发布流程始终使用最新的、安全的Action版本，这直接支持了项目“提供可靠、易用的扩散模型工具”的核心目标。

### 3. 对项目的影响和潜在意义
- **直接影响**：减少因GitHub Actions版本过旧导致的CI失败或安全漏洞风险。
- **潜在意义**：
    - **提升开发效率**：开发者无需手动关注Action更新，可更专注于模型和功能开发。
    - **增强项目健壮性**：自动化更新有助于保持CI管道的健康状态，确保每次提交都能得到可靠的测试反馈。
    - **良好的开源实践**：体现了项目团队对代码质量和长期可维护性的重视，符合Hugging Face一贯的工程规范。

### 4. 值得关注的技术点
- **Dependabot配置**：虽然本次提交未展示具体配置，但值得关注的是，项目选择了**每周**更新频率，而非每日。这平衡了“及时更新”与“避免频繁CI变动”的需求，是一种较为稳健的自动化策略。
- **GitHub Actions生态**：该提交表明项目严重依赖GitHub Actions生态（如测试、发布、文档构建等），其稳定性直接影响项目交付。

### 5. 基于项目背景，这些提交如何影响项目发展
- **支撑快速迭代**：`diffusers` 社区活跃，新模型和功能不断加入。一个稳定、自动化的CI系统是支撑这种高速发展的基石。本次提交正是加固了这一基石。
- **降低维护负担**：随着项目规模扩大，手动维护CI配置的成本会线性增长。自动化更新GitHub Actions是一种“技术债”的预防性偿还，让核心维护团队能将精力投入到更有价值的模型研究和社区支持上。
- **提升用户信任**：一个持续维护、CI稳定的项目更容易获得用户和贡献者的信任，从而吸引更多社区参与，形成良性循环。

**总结**：本次提交虽小，但意义重大。它是一次典型的基础设施优化，通过自动化手段提升了项目的长期可维护性和开发效率，为`diffusers`的持续演进提供了更可靠的保障。

## 详细提交记录

### [4b3dd38](https://github.com/huggingface/diffusers/commit/4b3dd3804274f37ee5d357e2d46d8161225e1580)

- **作者**: hf-dependantbot-rollout[bot]
- **时间**: 2026-05-26T15:43:07Z
- **提交信息**: chore: enable Dependabot weekly GitHub Actions bumps (#13812)

Co-authored-by: hf-dependantbot-rollout[bot] <285970069+hf-dependantbot-rollout[bot]@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 406
- **最后更新**: 2026-05-27T06:18:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12486
- **最后更新**: 2026-05-27T13:14:44Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

好的，这是对仓库 `modelscope/DiffSynth-Studio` 昨日提交记录的分析总结。

### 提交记录分析总结

**提交记录：** `adbfd4a` - support multi-logger (#1464)

---

#### 1. 主要更新类型
- **功能新增 (Feature Enhancement)**

#### 2. 关键变更点及其与项目整体方向的关系
- **变更点：** 引入了“多日志记录器 (multi-logger)”支持，并特别处理了多GPU环境下的兼容性问题。
- **与项目方向的关系：** DiffSynth-Studio 是一个专注于视频/图像合成与编辑的框架，其核心功能通常涉及复杂的模型训练和推理流程。日志记录是监控训练过程、调试模型、分析性能的关键基础设施。支持多日志记录器意味着：
    - **可扩展性：** 允许用户同时将日志输出到多个目标（例如，同时输出到控制台、文件、TensorBoard、Weights & Biases等），满足不同场景下的监控需求。
    - **鲁棒性：** 在多GPU训练场景下，确保日志记录的正确性和一致性，避免日志混乱或丢失，这对于大规模实验至关重要。

#### 3. 对项目的影响和潜在意义
- **提升开发与调试效率：** 用户和开发者可以更灵活地配置日志系统，方便在开发、训练和部署阶段进行更全面的监控和问题排查。
- **增强实验管理能力：** 支持将日志同步到外部平台（如TensorBoard、WandB）是进行实验追踪和对比的基础。此更新为未来集成更强大的实验管理工具铺平了道路。
- **降低多GPU使用门槛：** 明确处理多GPU情况，表明项目团队在积极优化分布式训练的用户体验，这对于需要大规模计算资源的视频生成任务尤为重要。

#### 4. 值得关注的技术点
- **多GPU兼容性：** 提交信息中特别提到“support multi-logger on multi-gpu”，这是一个重要的技术细节。在多进程（多GPU）环境下，确保日志记录器被正确初始化、避免进程间冲突、以及保证日志输出的有序性，是需要仔细处理的工程问题。这表明开发者考虑了实际使用中的复杂场景。
- **模块化设计：** 实现“multi-logger”通常意味着对原有的日志模块进行了重构，使其支持注册和切换不同的日志后端。这是一种良好的模块化设计实践，有利于代码的维护和扩展。

#### 5. 结合项目背景，这些提交如何影响项目发展
- **强化基础设施，支撑复杂应用：** 根据README，DiffSynth-Studio 旨在提供强大的视频合成能力。随着模型越来越复杂（如长视频生成、高分辨率处理），训练和推理过程会变得更长、更复杂。一个健壮、灵活的日志系统是支撑这些复杂应用的基础。此更新是项目在“工程化”和“易用性”方面迈出的坚实一步。
- **吸引更广泛的用户群体：** 对于专业研究人员和高级用户而言，能够自定义日志输出、集成到自己的实验管理流程中是一个重要的吸引力。此更新降低了这类用户的使用门槛，有助于项目从“可用”向“好用”发展。
- **为未来功能打下基础：** 良好的日志系统是后续实现如“自动超参数调优”、“模型性能监控”、“异常检测”等高级功能的前提。这次更新为项目的长期发展奠定了更稳固的技术基础。

## 详细提交记录

### [adbfd4a](https://github.com/modelscope/DiffSynth-Studio/commit/adbfd4a086a07d91177e661c7a4aae163cb8c9bc)

- **作者**: Zhongjie Duan
- **时间**: 2026-05-26T11:56:28Z
- **提交信息**: support multi-logger (#1464)

* support multi-logger

* support multi-logger on multi-gpu

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 28347
- **最后更新**: 2026-05-27T14:13:59Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 25
- **主要提交者**: Venkatesh Guduru, Shangming Cai, Joel Schlosser

## AI分析总结

好的，根据您提供的 `sgl-project/sglang` 仓库的README摘要和昨日提交记录，以下是为您整理的更新要点分析。

### 1. 主要更新类型

- **性能优化 (Performance Optimization):** 这是昨日更新的核心主题，涉及多个方面。
- **Bug修复 (Bug Fix):** 修复了多个关键路径上的崩溃和逻辑错误。
- **新功能/特性 (New Feature/Enhancement):** 引入了对新型模型架构和硬件的支持。
- **重构 (Refactor):** 对调度器、数据并行逻辑等核心模块进行了重构，以提升代码可维护性和可扩展性。
- **文档更新 (Documentation):** 更新了特定模型的使用指南和硬件配置说明。
- **CI/工程化 (CI/Engineering):** 调整了CI流程和依赖版本。

### 2. 关键变更点及其与项目整体方向的关系

- **性能优化：**
    - **投机解码 (Speculative Decoding):** 提交 `dd6f073` 重新引入了在EAGLE草案模型中，当 `topk == 1` 时跳过全词汇表softmax的优化。这直接减少了投机解码的计算开销，提升了推理吞吐量。
    - **MoE (Mixture-of-Experts):** 提交 `1371685` 优化了 `cutlass_moe_fp4` 的性能，通过改进权重路由应用方式，直接提升了FP4精度下MoE层的计算效率。
    - **流水线并行 (Pipeline Parallelism, PP):** 提交 `98eb844` 为纯分块预填充批次跳过了PP输出通信。这减少了不必要的通信开销，优化了长序列预填充场景下的性能。
    - **FlashMLA 集成:** 提交 `b66f8e0` 引入了 `Sgl flashmla`，这很可能是一个针对特定硬件或场景优化的FlashAttention变体，旨在提升注意力计算速度。

- **Bug修复：**
    - **PD分离 (Pre-fill Decode Separation):** 提交 `c47f0e7` 修复了预填充路径中 `top_logprobs` 的崩溃问题；提交 `c8c1aed` 修复了跨rank队列的同步问题。这些修复对于保证PD分离架构的稳定性和正确性至关重要。
    - **MoE崩溃:** 提交 `6c81286` 修复了当 `intermediate_size_per_partition` 不是16对齐时，`flashinfer_cutlass` MoE内核的崩溃问题，增强了MoE实现的鲁棒性。
    - **工具调用:** 提交 `64c7c68` 修复了工具调用中非标准JSON Schema类型的规范化问题，提升了与外部工具集成的兼容性。

- **新功能/特性：**
    - **模型支持:** 提交 `468c565` 为LFM2和LFM2-MoE模型引入了YARN rope参数；提交 `499eecc` 为NemotronH V3 Omni模型添加了权重映射器和配置支持。这体现了项目持续扩展对最新模型架构支持的努力。
    - **硬件支持:** 提交 `25` 支持了SM100 (NVIDIA下一代架构) 上的CuTeDSL GDN Prefill Kernel；提交 `13` 支持了L3 HiStorage框架。这表明项目正积极适配最新的硬件特性和存储架构。
    - **编码器批处理:** 提交 `dabdd91` 为EPD (Encoder-Prefill-Decode) 架构中的图像/音频编码器实现了跨请求批处理，这对于多模态模型的高效推理非常重要。

- **重构：**
    - **调度器重构:** 提交 `d9c8293` 提取了调度器的初始化方法并加强了拆分逻辑，这有助于提高调度器的模块化和可测试性，为未来更复杂的调度策略打下基础。
    - **数据并行 (DP) 重构:** 提交 `1a05b51` 重构了空闲批次逻辑，优化了数据并行下的资源管理。

- **文档与CI：**
    - **文档:** 提交 `47617cc` 和 `6afebc2` 分别更新了Qwen3在Xeon CPU上的使用指南和DeepSeek-V4在GB200 Pro上的配置说明，降低了用户的使用门槛。
    - **CI:** 提交 `a269131` 和 `d25a220` 分别修复了Lint工作流和放宽了AMD CI的超时限制，提升了工程效率。

### 3. 对项目的影响和潜在意义

- **性能提升:** 多项性能优化（投机解码、MoE、PP通信）将直接转化为更高的推理吞吐量和更低的延迟，尤其是在长序列、大规模模型和特定硬件上，这符合SGLang作为高性能推理引擎的核心定位。
- **稳定性增强:** 修复PD分离和MoE的崩溃问题，显著提升了系统在生产环境下的稳定性和可靠性，这对于服务化部署至关重要。
- **生态扩展:** 支持更多模型（LFM2, NemotronH）和硬件（SM100, L3 HiStorage）表明SGLang正在积极扩大其生态覆盖范围，吸引更多用户和场景。
- **架构演进:** 对调度器、DP逻辑的重构，以及对EPD编码器批处理的支持，表明项目正在为更复杂、更高效的推理架构（如多模态、长上下文）进行底层架构准备。

### 4. 值得关注的技术点

- **EAGLE投机解码的Softmax优化:** 这是一个典型的“知其然，知其所以然”的性能优化，通过利用 `

## 详细提交记录

### [468c565](https://github.com/sgl-project/sglang/commit/468c565168c28bc4328b517047731148c1a505ec)

- **作者**: Piotr Mazurek
- **时间**: 2026-05-26T23:00:22Z
- **提交信息**: Wire YARN rope_parameters through LFM2 and LFM2-MoE attention (#26187)

### [6989fed](https://github.com/sgl-project/sglang/commit/6989fede3ce75187f9394d0e076437de2a9cc36a)

- **作者**: Joel Schlosser
- **时间**: 2026-05-26T21:58:57Z
- **提交信息**: Purge usage of pytorch named tensors (#25911)

### [1a05b51](https://github.com/sgl-project/sglang/commit/1a05b511e412b55489d7283c2b79f4b494ca9c55)

- **作者**: Yilong Zhao
- **时间**: 2026-05-26T21:22:25Z
- **提交信息**: dp: refactor idle batch logic (#25025)

Co-authored-by: happierpig <zhaoyilong217@sjtu.edn.cn>

### [dd6f073](https://github.com/sgl-project/sglang/commit/dd6f073377f376fb1033195061a31c80b3b7e12f)

- **作者**: Qiaolin Yu
- **时间**: 2026-05-26T21:14:48Z
- **提交信息**: Reland "[perf][spec decoding] Skip full-vocab softmax in EAGLE draft when topk == 1 (#26235)" (#26397)

### [499eecc](https://github.com/sgl-project/sglang/commit/499eecce22ea9973f182c2e2b7f3334ae401ed04)

- **作者**: Serge Panev
- **时间**: 2026-05-26T20:34:05Z
- **提交信息**: [NemotronH] V3 Omni wrapper: WeightsMapper + config round-trip (#25023)

Co-authored-by: Yihao Wang <42559837+AgainstEntropy@users.noreply.github.com>

### [2b1e53c](https://github.com/sgl-project/sglang/commit/2b1e53c98d76c1237309c369908837abacfdb6ce)

- **作者**: Ziang Li
- **时间**: 2026-05-26T20:30:08Z
- **提交信息**: [RL] Fix FP8 skip matching for trailing-dot prefixes (#26287)

### [47617cc](https://github.com/sgl-project/sglang/commit/47617cc4df1e5c249d11ea5970ce26c32c8757af)

- **作者**: Zaili Wang
- **时间**: 2026-05-26T19:14:07Z
- **提交信息**: [CPU Doc]Add Xeon CPU info in Qwen3 Cookbook (#25971)

### [0753182](https://github.com/sgl-project/sglang/commit/0753182b50f041be7f8c6e7f5c01ff79e655ecfb)

- **作者**: sglang-bot
- **时间**: 2026-05-26T19:10:16Z
- **提交信息**: chore: bump sgl-kernel version to 0.4.3 (#26414)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [6afebc2](https://github.com/sgl-project/sglang/commit/6afebc278ad9a56cc7d4462635851671668e675b)

- **作者**: zijiexia
- **时间**: 2026-05-26T19:08:48Z
- **提交信息**: [docs] DeepSeek-V4 cookbook: note cu129 image for GB200 Pro DeepEP backend (#26413)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [b66f8e0](https://github.com/sgl-project/sglang/commit/b66f8e0b96c9bbc7aa51970d1fc65de1fa6c9ec1)

- **作者**: Chunan Zeng
- **时间**: 2026-05-26T19:00:23Z
- **提交信息**: Sgl flashmla (#26132)

### [ec6f8d6](https://github.com/sgl-project/sglang/commit/ec6f8d61f707952a87fedd2a3491d1e28130c86a)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-26T18:34:03Z
- **提交信息**: [Spec] Async-assert probes across EAGLE/MTP; zero `tgt_cache_loc` (#26335)

### [6c81286](https://github.com/sgl-project/sglang/commit/6c8128650e1f4a87313b52e6f6a2bdb7f01e8bea)

- **作者**: Venkatesh Guduru
- **时间**: 2026-05-26T16:58:33Z
- **提交信息**: [Bugfix] Fix flashinfer_cutlass MoE crash when intermediate_size_per_partition is not 16-aligned (#22627)

Co-authored-by: vguduruTT <venkatesh.guduru@mulitcorewareinc.com>

### [38f32c3](https://github.com/sgl-project/sglang/commit/38f32c38abd41a296bd21186b5d8c5e6af1f8997)

- **作者**: Zhangheng
- **时间**: 2026-05-26T14:38:00Z
- **提交信息**: [UnifiedRadixTree]: Support L3 HiStorage framework (#26062)

### [c47f0e7](https://github.com/sgl-project/sglang/commit/c47f0e7cdde48ddc718e3c6ee8bc87bebee2e8ff)

- **作者**: Jun Liu
- **时间**: 2026-05-26T14:01:10Z
- **提交信息**: [PD] Fix top logprobs crash in prefill path (#26299)

### [c8c1aed](https://github.com/sgl-project/sglang/commit/c8c1aed5e908a4dfec88781bff3ae053b589e867)

- **作者**: Shangming Cai
- **时间**: 2026-05-26T13:59:42Z
- **提交信息**: [PD] Fix cross-rank queue divergence by gating metadata readiness before all-reduce (#26394)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [98eb844](https://github.com/sgl-project/sglang/commit/98eb84497dca431aa1eebcd8c694cdcc3f9bb796)

- **作者**: Yongfei Xu
- **时间**: 2026-05-26T13:59:18Z
- **提交信息**: [PP] Skip PP output communication for pure chunked prefill batches (#26148)

### [a269131](https://github.com/sgl-project/sglang/commit/a26913158bd9ec537b37ce5f3ef7d4838c4fb0c6)

- **作者**: zijiexia
- **时间**: 2026-05-26T12:06:54Z
- **提交信息**: fix(ci): enforce legacy docs/ gate in Lint workflow (#26322)

### [9409969](https://github.com/sgl-project/sglang/commit/9409969fd5a0089017ad20d2ce0760afe0a02ea8)

- **作者**: Michael
- **时间**: 2026-05-26T09:47:52Z
- **提交信息**: Revert "[perf][spec decoding] Skip full-vocab softmax in EAGLE draft when topk == 1 (#26235)" (#26358)

### [d9c8293](https://github.com/sgl-project/sglang/commit/d9c82934c8a76a91f85e8169150ffc3b9d440bb4)

- **作者**: fzyzcjy
- **时间**: 2026-05-26T09:45:09Z
- **提交信息**: Extract Scheduler init methods and add skills to enforce the splitting requirements (#26271)

### [48f3264](https://github.com/sgl-project/sglang/commit/48f3264807eac6bdef161aeaf5f272de6e4bda6f)

- **作者**: Chao Shi
- **时间**: 2026-05-26T09:44:15Z
- **提交信息**: [HiCache]: Check return code of cudaHostRegister (#26301)

### [d25a220](https://github.com/sgl-project/sglang/commit/d25a220fdbe91f7847f64ebe21b1589a6f435485)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-05-26T09:25:05Z
- **提交信息**: [AMD] Relaxing timeout for AMD CI (#26392)

### [e958f45](https://github.com/sgl-project/sglang/commit/e958f4561f93c1607f07fa83d27adfa042cf7ace)

- **作者**: roikoren755
- **时间**: 2026-05-26T08:03:29Z
- **提交信息**: [feat] Support `extra_buffer` in Mamba2-based models (#15829)

Signed-off-by: Roi Koren <roik@nvidia.com>

### [7e6e5ef](https://github.com/sgl-project/sglang/commit/7e6e5efe51e2f6e478c505858050b15e44557c9b)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-26T07:49:41Z
- **提交信息**: Revert "fix(tool_call): normalize non-standard JSON Schema types in tool params" (#26379)

### [dabdd91](https://github.com/sgl-project/sglang/commit/dabdd91ef34e134a13e383cae0a2679bc5b7740a)

- **作者**: Zhonghua Deng
- **时间**: 2026-05-26T07:38:59Z
- **提交信息**: [EPD] Cross-request batching for image/audio encoder (#25964)

### [d34d4d9](https://github.com/sgl-project/sglang/commit/d34d4d9f5f366af3291433650546b8b5f9ed58b4)

- **作者**: Yuan Luo
- **时间**: 2026-05-26T07:38:29Z
- **提交信息**: [GDN] Support SM100 CuTeDSL GDN Prefill Kernel (#26200)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [64c7c68](https://github.com/sgl-project/sglang/commit/64c7c6851b7bf2720e510b0296529294ebe6f373)

- **作者**: Xinyuan Tong
- **时间**: 2026-05-26T07:23:59Z
- **提交信息**: fix(tool_call): normalize non-standard JSON Schema types in tool params (#23476)

### [1371685](https://github.com/sgl-project/sglang/commit/137168539a732ea5688d09998eb0c49ef5a3fad7)

- **作者**: chengchao23
- **时间**: 2026-05-26T07:07:49Z
- **提交信息**: [Perf][Moe]improve cutlass_moe_fp4 performance by using apply_router_weight_on_i… (#19493)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1181
- **最后更新**: 2026-05-27T03:14:14Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，这是对 `vipshop/cache-dit` 仓库昨日提交记录的分析总结：

### 昨日更新要点总结

#### 1. 主要更新类型
- **功能增强**：为 Ray 分布式执行环境增加了更灵活的初始化能力。
- **Bug 修复**：移除了重复的 Ray API 调用，清理了代码逻辑。
- **文档更新**：补充了关于 `torch.compile` 在模型卸载（offload）场景下的使用说明。

#### 2. 关键变更点及其与项目整体方向的关系
- **`[493d731] API: remove dup ray api call (#1021)`**
  - **变更点**：删除了 Ray 相关代码中重复的 API 调用。
  - **与项目方向的关系**：`cache-dit` 是一个面向 Diffusion Transformers 的推理引擎，其核心优势之一是通过**并行化**（Parallelism）加速推理。Ray 是实现分布式并行计算的关键组件。移除重复调用可以**提升代码健壮性**，避免潜在的错误或性能开销，确保并行执行逻辑的正确性。

- **`[8db3b2f] docs: add torch.compile section to offload docs (#1020)`**
  - **变更点**：在模型卸载（offload）的文档中增加了关于 `torch.compile` 的章节。
  - **与项目方向的关系**：`cache-dit` 旨在通过**缓存**（Cache）和**量化**（Quantization）等技术优化推理。模型卸载是一种内存优化策略，而 `torch.compile` 是 PyTorch 2.0 引入的 JIT 编译技术，可以显著提升模型执行速度。将两者结合使用，体现了项目在**性能优化**上的深入探索，为用户提供了更全面的加速方案。

- **`[77b0fca] ray: allow pass init_fn to ray wrapper (#1019)`**
  - **变更点**：允许用户向 Ray 的封装器（wrapper）传递一个 `init_fn` 初始化函数。
  - **与项目方向的关系**：这增强了 `cache-dit` 的**灵活性和可扩展性**。用户现在可以在 Ray 工作节点启动时执行自定义的初始化逻辑（例如，加载特定资源、设置环境变量等）。这对于需要复杂环境配置的**分布式推理**场景至关重要，使得 `cache-dit` 能更好地适应不同的部署需求。

#### 3. 对项目的影响和潜在意义
- **提升稳定性和效率**：修复重复 API 调用，减少了潜在的错误源，使 Ray 并行执行更加稳定可靠。
- **降低用户使用门槛**：通过文档明确 `torch.compile` 与模型卸载的配合使用，帮助用户更容易地组合多种优化技术，获得更好的推理性能。
- **增强部署灵活性**：允许自定义 `init_fn`，使得 `cache-dit` 在复杂的生产环境（如多GPU集群、异构计算节点）中部署更加便捷，扩大了其应用场景。

#### 4. 值得关注的技术点
- **Ray 的 `init_fn` 机制**：这是一个典型的“钩子”（hook）模式，允许用户在框架的生命周期关键节点插入自定义逻辑。对于需要精细控制分布式环境的开发者来说，这是一个非常实用的功能。
- **`torch.compile` 与 Offload 的结合**：这代表了 PyTorch 生态中两种主流优化策略（编译优化与内存卸载）的协同。关注其文档，可以了解如何在实际应用中平衡计算速度与显存占用。

#### 5. 基于项目背景，这些提交如何影响项目发展
- **巩固核心优势**：`cache-dit` 的定位是“PyTorch-native”且集成了“Cache, Parallelism, Quantization”。昨日更新直接强化了 **Parallelism**（通过修复和增强 Ray 集成）和 **Quantization/Performance**（通过文档指导 `torch.compile` 使用）这两个核心特性。
- **向生产级成熟度迈进**：移除重复调用、增加初始化灵活性、完善文档，这些都是一个项目从原型走向稳定、可部署的生产级工具所必须经历的步骤。这些提交表明开发团队正在积极打磨 `cache-dit` 的工程质量和用户体验。
- **构建更开放的生态**：通过允许用户自定义 Ray 初始化，`cache-dit` 不再是封闭的“黑盒”，而是提供了扩展点，让社区用户可以根据自己的硬件和业务需求进行定制，这有助于吸引更多开发者并构建更丰富的生态。

## 详细提交记录

### [493d731](https://github.com/vipshop/cache-dit/commit/493d73127833bf29c6e7b16f0414bb7543843ec4)

- **作者**: DefTruth
- **时间**: 2026-05-26T10:28:30Z
- **提交信息**: API: remove dup ray api call (#1021)

### [8db3b2f](https://github.com/vipshop/cache-dit/commit/8db3b2f4ce01c5b2f922a9fb9f2d5ea83dec09b4)

- **作者**: DefTruth
- **时间**: 2026-05-26T09:28:17Z
- **提交信息**: docs: add torch.compile section to offload docs (#1020)

### [77b0fca](https://github.com/vipshop/cache-dit/commit/77b0fcadd1cb083fabf876bfd57c0858d7adf6e6)

- **作者**: DefTruth
- **时间**: 2026-05-26T09:16:30Z
- **提交信息**: ray: allow pass init_fn to ray wrapper (#1019)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 81153
- **最后更新**: 2026-05-27T14:19:44Z

## 提交统计

- **昨日提交总数**: 24
- **提交者数量**: 19
- **主要提交者**: Chaojun Zhang, Hank_, Kevin H. Luu

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日（基于提交时间）更新的分析总结。

### 1. 主要更新类型

- **Bug修复**: 修复了多API服务器启动时的端口冲突、Eagle3模型推理错误、以及无效的思考预算值等问题。
- **功能新增/改进**: 新增了LM Head量化支持、CuTe DSL稀疏压缩器、自定义图像基准数据集支持、以及DeepSeek V4的Q Pad融合等。
- **重构与清理**: 对MoE（混合专家）模块进行了大规模重构（迁移至Oracle模式），清理了DeepSeek压缩器和MooncakeStore中的无用代码。
- **性能优化**: 通过内核融合（如`fuse_minimax_qk_norm`）和启用HMA（异构内存访问）来提升推理速度。
- **基础设施与CI**: 新增了ARM64 CI镜像，软化了AMD入口测试，扩展了ROCm测试覆盖。
- **文档更新**: 更新了AGENTS.md的格式限制，并新增了MoRI-IO连接器的使用指南。
- **平台支持**: 修复了XPU（Intel）上的MoE LoRA内核崩溃问题，并移除了ROCm上不兼容的MegaMoE集成。

### 2. 关键变更点及其与项目整体方向的关系

- **MoE重构（Oracle模式）**: 提交 `[f51bbc6]` 和 `[b226dda]` 将W4A8和ModelOpt的MoE实现迁移到“Oracle”模式。这符合项目“易用、快速、廉价”的目标，通过统一和优化MoE内核架构，为未来支持更多量化方案和硬件平台打下基础，同时提升推理效率。
- **DeepSeek V4深度优化**: 提交 `[6ab6ffb]`（融合Q Pad）、`[c8414a8]`（移除不兼容的MegaMoE）和 `[97e4022]`（修复Eagle3推理）。这表明项目正积极跟进并优化最前沿的模型架构（如DeepSeek V4），确保vLLM能高效、稳定地运行这些高价值模型，是其“快速”和“廉价”目标的具体体现。
- **多平台与硬件支持**: 提交 `[e19b9b1]`（ARM64 CI）、`[445ded1]`（ROCm测试）、`[861b977]`（XPU修复）和 `[d565357]`（MoRI-IO文档）。这些更新直接服务于项目“为每个人”服务的愿景，通过扩展对ARM、AMD、Intel等不同硬件的支持，降低了用户的使用门槛，使vLLM能在更广泛的硬件生态中运行。
- **量化与压缩技术**: 提交 `[6f5b533]`（LM Head量化）和 `[a37e471]`（CuTe稀疏压缩器）。这些是降低模型部署成本和内存占用的关键技术，直接对应“廉价”的目标。LM Head量化能进一步压缩模型，而CuTe稀疏压缩器则利用NVIDIA的CuTe库优化稀疏计算，提升性能。
- **稳定性与可靠性**: 提交 `[812e7e7]`（修复`EADDRINUSE`竞态条件）和 `[739af5c]`（拒绝无效思考预算）。这些修复提升了多服务器部署的稳定性和推理过程的鲁棒性，是项目走向生产环境的关键保障。

### 3. 对项目的影响和潜在意义

- **性能与效率提升**: MoE重构和DeepSeek V4的融合优化将直接提升这两类重要模型的推理速度和吞吐量，降低延迟。
- **硬件生态扩展**: ARM64 CI和ROCm/XPU的修复与测试，将吸引更多使用非NVIDIA硬件的用户和开发者，扩大社区影响力。
- **部署成本降低**: 新的量化支持和稀疏压缩技术，使得在相同硬件上可以运行更大或更多的模型，或使用更便宜的硬件运行现有模型，直接降低用户的运营成本。
- **生产环境就绪度提升**: 对竞态条件和无效输入的修复，以及更完善的CI测试，增强了vLLM在生产环境中的稳定性和可靠性。

### 4. 值得关注的技术点

- **MoE Oracle模式**: 这是MoE内核架构的一次重要重构，值得关注其设计思路和未来对其他MoE变体的支持计划。
- **CuTe DSL稀疏压缩器**: 利用NVIDIA的CuTe库进行稀疏计算优化，这是一个相对较新的技术方向，其性能表现和通用性值得关注。
- **HMA（异构内存访问）默认启用**: 对于支持HMA的KV传输连接器，默认启用可以显著提升跨设备数据传输效率，是分布式推理的重要优化。
- **DeepSeek V4的Q Pad融合**: 将Padding操作融合进内核，减少了显存访问和内核启动开销，是典型的性能优化技巧。

### 5. 基于项目背景，这些提交如何影响项目发展

- **巩固“快速”优势**: 通过MoE重构、内核融合和稀疏压缩等优化，vLLM在推理性能上的领先地位得到进一步巩固，尤其是在处理DeepSeek V4这类复杂模型时。
- **践行“廉价”承诺**: 新增的量化支持和压缩技术，直接降低了模型部署的硬件门槛和运营成本，使更多个人和中小企业能够负担得起LLM服务。
- **拓宽“易用”边界**: 对ARM、AMD、Intel等平台的支持，以及更完善的文档和CI，降低了用户在不同硬件上使用vLLM的难度，使“为每个人

## 详细提交记录

### [e19b9b1](https://github.com/vllm-project/vllm/commit/e19b9b1045f6b8c2b5a647cc3a819bb919a718ac)

- **作者**: Kevin H. Luu
- **时间**: 2026-05-26T21:38:09Z
- **提交信息**: [ci] Add arm64 ci image (#41303)

Signed-off-by: khluu <khluu000@gmail.com>
Signed-off-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [812e7e7](https://github.com/vllm-project/vllm/commit/812e7e73648573142808fdeea0ffc30adb247ba3)

- **作者**: Vadim Gimpelson
- **时间**: 2026-05-26T21:06:00Z
- **提交信息**: [Bugfix][V1] Fix TOCTOU race causing intermittent `EADDRINUSE` on multi-API-server DP startup (#42585)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Signed-off-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [d98cbf4](https://github.com/vllm-project/vllm/commit/d98cbf472b65b124b140c4e582ea38416e5c5cae)

- **作者**: Zhewen Li
- **时间**: 2026-05-26T20:40:21Z
- **提交信息**: [KV Connector] MooncakeStore: drop dead discard_partial_chunks parameter (#43627)

Signed-off-by: Zhewen Li <zhewen@inferact.ai>
Co-authored-by: Zhewen Li <zhewen@inferact.ai>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [6e50386](https://github.com/vllm-project/vllm/commit/6e503868caa46f3afa87e8d3365495464fd75fb3)

- **作者**: Jee Jee Li
- **时间**: 2026-05-26T20:16:03Z
- **提交信息**: [Kernel] Porting  fuse_minimax_qk_norm  to manual fusion (#43410)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [49b4882](https://github.com/vllm-project/vllm/commit/49b488277922b47bcac320ae8d4b7288bf70dc3c)

- **作者**: Kevin H. Luu
- **时间**: 2026-05-26T20:08:48Z
- **提交信息**: [CI] Soft-fail AMD entrypoints mirror tests (#43709)

Signed-off-by: Kevin Luu <kevin@inferact.ai>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [193ce88](https://github.com/vllm-project/vllm/commit/193ce8812eb4b43fc48039757072c71ac2eb0a28)

- **作者**: Woosuk Kwon
- **时间**: 2026-05-26T17:11:25Z
- **提交信息**: [DSv4] Drop _get_compressed_kv_buffer in DeepseekCompressor (#43690)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [3aea37d](https://github.com/vllm-project/vllm/commit/3aea37d28e44f0b8389e2cfa9876c3faa62543f4)

- **作者**: Woosuk Kwon
- **时间**: 2026-05-26T16:31:23Z
- **提交信息**: [Doc] Add line limit to AGENTS.md (#43635)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Signed-off-by: Mark McLoughlin <markmc@redhat.com>
Co-authored-by: Mark McLoughlin <markmc@redhat.com>

### [6f5b533](https://github.com/vllm-project/vllm/commit/6f5b533241929d26f13948e6a48290f6a4f4eefe)

- **作者**: Wei-Ming Chen
- **时间**: 2026-05-26T16:21:05Z
- **提交信息**: Add LM head quantization support for ModelOpt (#42124)

Signed-off-by: weimingc <17592131+meenchen@users.noreply.github.com>

### [c8414a8](https://github.com/vllm-project/vllm/commit/c8414a82712bd775b7243b19a264d9623c3bb369)

- **作者**: Woosuk Kwon
- **时间**: 2026-05-26T15:56:04Z
- **提交信息**: [ROCm] Remove MegaMoE integration in deepseek v4 (#43629)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [f51bbc6](https://github.com/vllm-project/vllm/commit/f51bbc694d9704daeefc0549229858b657bce20c)

- **作者**: bnellnm
- **时间**: 2026-05-26T15:15:42Z
- **提交信息**: [MoE Refactor] W4a8 int8 oracle (#42789)

Signed-off-by: Bill Nell <bnell@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [b226dda](https://github.com/vllm-project/vllm/commit/b226ddacfda921b8eef7b75794c33d49ae51186a)

- **作者**: bnellnm
- **时间**: 2026-05-26T15:14:14Z
- **提交信息**: [MoE Refactor] Migrate ModelOptMxFp8FusedMoE to oracle (#42768)

Signed-off-by: Bill Nell <bnell@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [6ab6ffb](https://github.com/vllm-project/vllm/commit/6ab6ffb428be5ed3c5d6c3cc029c5afe7ff59eee)

- **作者**: Yongye Zhu
- **时间**: 2026-05-26T15:12:54Z
- **提交信息**: [Feat][DSV4] Fuse q pad into deepseek v4 fused kernel (#43162)

### [445ded1](https://github.com/vllm-project/vllm/commit/445ded18c1184a5a44d0f41010d614adbd107ca7)

- **作者**: Andreas Karatzas
- **时间**: 2026-05-26T13:57:13Z
- **提交信息**: [ROCm][CI] Extend ROCm quick reduce coverage (#40990)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [d565357](https://github.com/vllm-project/vllm/commit/d565357a9013c20dbbec839a9d8376905b9beed1)

- **作者**: Simon Danielsson
- **时间**: 2026-05-26T13:52:30Z
- **提交信息**: [Docs][ROCm] MoRI-IO Connector Usage Guide (#43603)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Signed-off-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [a970fb5](https://github.com/vllm-project/vllm/commit/a970fb5a1a5800c552c74cf3278d6ee7c1c3fca1)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-05-26T12:59:40Z
- **提交信息**: Fix CuPy runtime deps and restore humming (#43530)

Signed-off-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [861b977](https://github.com/vllm-project/vllm/commit/861b97765d6cd2587ba74e7787a89d9b8aa1c9d4)

- **作者**: Chaojun Zhang
- **时间**: 2026-05-26T10:40:32Z
- **提交信息**: [XPU] Fix fused MoE LoRA kernel crash on XPU by using platform-agnos num_compute_units (#43646)

Signed-off-by: Chaojun,Zhang <chaojun.zhang@intel.com>

### [ebd0692](https://github.com/vllm-project/vllm/commit/ebd0692f80e6d0ce3f70144e0e271c3fc8f3ab40)

- **作者**: Javier De Jesus
- **时间**: 2026-05-26T10:39:26Z
- **提交信息**: [Model] Use AutoWeightsLoader for InternLM2 (#38278)

Signed-off-by: Jesus De Jesus <dejesus.9297@gmail.com>
Signed-off-by: javierdejesusda <javier.dejesusj9@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [739af5c](https://github.com/vllm-project/vllm/commit/739af5c7e1603b6c9a4d376b52dc7f4b19e1403d)

- **作者**: linzm1007
- **时间**: 2026-05-26T10:37:30Z
- **提交信息**: [Reasoning] [Bugfix] Reject invalid thinking_token_budget values (#43402)

Signed-off-by: linzm1007 <linzm1007@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5d09f47](https://github.com/vllm-project/vllm/commit/5d09f471f4ec44edfb0aa8917a985bda7c897195)

- **作者**: Thibault Castells
- **时间**: 2026-05-26T10:37:25Z
- **提交信息**: [Misc] Support interleaved custom image benchmark datasets (#43636)

Signed-off-by: ThibaultCastells <thib.castells@icloud.com>

### [681d7dd](https://github.com/vllm-project/vllm/commit/681d7dd38b596df4439301f8f47e60177792ebf3)

- **作者**: Simon Danielsson
- **时间**: 2026-05-26T10:33:35Z
- **提交信息**: [Misc][Refactor][ROCm] Convert MoRI-related envvars to extra config args (#43303)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [755043c](https://github.com/vllm-project/vllm/commit/755043cf3cd68e6cd93bfcfde2152f28c9fb42bd)

- **作者**: Ethan Feng
- **时间**: 2026-05-26T10:28:51Z
- **提交信息**: [KV Transfer] Enable HMA by default for connectors that support it (#41847)

Signed-off-by: Ethan Feng <ethan.fengch@gmail.com>

### [97e4022](https://github.com/vllm-project/vllm/commit/97e4022c6ccb7b2cf1a1fc0a13a17a2a06d74f0d)

- **作者**: Yubo Wang
- **时间**: 2026-05-26T07:46:10Z
- **提交信息**: [Bugfix] Apply fc_norm in Eagle3DeepseekV2 combine_hidden_states (#43482)

Signed-off-by: Yubo Wang <yubowang2019@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b326945](https://github.com/vllm-project/vllm/commit/b3269454b1eff2ce651b8ff3d0858c40ff81bc6a)

- **作者**: Hank_
- **时间**: 2026-05-26T07:13:46Z
- **提交信息**: [chores][log] change registry log from `warning` to `debug` (#43045)

Signed-off-by: Hank <hcc.mayday@gmail.com>

### [a37e471](https://github.com/vllm-project/vllm/commit/a37e47100ca1f941671a4418dbdfd7a5afca4811)

- **作者**: Jie Fang
- **时间**: 2026-05-26T07:11:12Z
- **提交信息**: Add CuTe DSL sparse compressor support (#43584)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-27
**监控日期**: 2026-05-26
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: 无法获取仓库信息

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---
