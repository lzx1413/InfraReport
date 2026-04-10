# GitHub Stars 合并报告 - 2026-04-10

**合并日期**: 2026-04-11
**监控日期**: 2026-04-10
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


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1814
- **最后更新**: 2026-04-10T10:19:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2150
- **最后更新**: 2026-04-10T16:53:57Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Yang Yong (雍洋), yihuiwen, fuheaven

## AI分析总结

根据仓库 `ModelTC/LightX2V` 的 README 摘要（一个专注于轻量级视频生成推理的框架）以及昨日的提交记录，以下是分析总结：

### 1. 主要更新类型
- **功能新增**：为 `disagg` 功能添加了博客文章（#1002）；在服务器中添加了新的指标（#1000）。
- **Bug修复**：修复了 `disagg` 英文名称相关的 bug（#1003）。
- **模型更新**：更新了 `neo moe` 模型（#1001）。
- **文档更新**：新增了 `disagg` 相关的博客内容（#1002）。

### 2. 关键变更点及其与项目整体方向的关系
- **`disagg` 功能完善**：通过修复 bug 和添加博客，增强了 `disagg`（可能指“解耦”或分布式相关功能）的可用性和文档支持，符合项目作为**轻量级推理框架**对高效、模块化设计的追求。
- **模型更新**：更新 `neo moe` 模型（可能指一种混合专家模型），体现了项目持续优化**视频生成模型**性能的方向，以提升生成质量或效率。
- **服务器指标添加**：在服务器中集成新指标，有助于**监控和优化推理性能**，强化了框架在生产环境中的可观测性，与项目强调“推理框架”的定位一致。

### 3. 对项目的影响和潜在意义
- **用户体验提升**：Bug 修复和博客添加使 `disagg` 功能更稳定、易理解，可能降低用户使用门槛。
- **性能与可维护性增强**：模型更新可能带来更好的视频生成效果；服务器指标有助于实时监控，为后续性能调优提供数据支持。
- **社区与文档丰富**：新增博客内容促进了知识分享，可能吸引更多开发者关注或贡献。

### 4. 值得关注的技术点
- **`neo moe` 模型更新**：可能涉及模型架构或参数的优化，值得关注其如何平衡轻量化与视频生成质量。
- **`disagg` 功能**：可能指解耦设计或分布式推理组件，其改进可能影响框架的模块化和扩展性。
- **服务器指标集成**：暗示项目正加强运维支持，可能涉及 Prometheus、日志系统等监控工具的结合。

### 5. 基于项目背景的提交影响分析
LightX2V 旨在提供**轻量、高效的视频生成推理框架**。昨日提交：
- **强化核心能力**：通过模型更新和服务器指标，直接提升了框架的**推理性能与可观测性**，支持更高效的视频生成部署。
- **完善生态工具**：`disagg` 相关更新可能优化了框架的模块化设计，帮助用户灵活定制推理流程，符合轻量级框架的**易用性和可扩展性**目标。
- **促进推广与协作**：博客添加增强了文档生态，有助于扩大项目影响力，吸引社区参与，推动框架的持续迭代。

**总结**：昨日更新聚焦于功能优化、Bug 修复和文档丰富，整体上加强了 LightX2V 作为视频生成推理框架的**性能、稳定性和用户体验**，与其轻量化、高效的核心目标高度一致。

## 详细提交记录

### [08d16b0](https://github.com/ModelTC/LightX2V/commit/08d16b0060b6ac08249dfdbe2e7ef04be92c1a2d)

- **作者**: fuheaven
- **时间**: 2026-04-10T14:27:33Z
- **提交信息**: update disagg EN name and fix bug (#1003)

### [1ba565e](https://github.com/ModelTC/LightX2V/commit/1ba565ee469c4c406c6083ece2f64a8626e2c76f)

- **作者**: fuheaven
- **时间**: 2026-04-10T14:10:24Z
- **提交信息**: add blogs for disagg (#1002)

### [e8f6bc4](https://github.com/ModelTC/LightX2V/commit/e8f6bc4fc30159544870566eaa3f026c4c4bf241)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-04-10T13:05:22Z
- **提交信息**: update neo moe model (#1001)

### [41ec78a](https://github.com/ModelTC/LightX2V/commit/41ec78ae5b9d09d48d80d295bc3135462ef6fe0a)

- **作者**: yihuiwen
- **时间**: 2026-04-10T08:40:03Z
- **提交信息**: add metrics to server (#1000)

Co-authored-by: yihuiwen <yihuiwen@sensetime.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2012
- **最后更新**: 2026-04-10T15:44:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5367
- **最后更新**: 2026-04-10T23:03:17Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: qsang-nv, Brian K. Ryu, Lee Nau

## AI分析总结

根据对FlashInfer仓库昨日提交记录的分析，结合其作为**高性能GPU推理内核库**的项目定位，总结如下：

### 1. 主要更新类型
昨日提交全部为**性能优化**和**Bug修复**，没有新增功能、文档更新或重构。
- **性能优化**：提交 #3014 和 #3026 专注于优化CUTLASS MoE（混合专家）和FP4 GEMM内核的性能。
- **Bug修复**：提交 #3025 和 #2857 修复了内存溢出和CUDA图兼容性问题。

### 2. 关键变更点及其与项目方向的关系
| 提交 | 关键变更点 | 与项目方向的关系 |
| :--- | :--- | :--- |
| **#3025** | 修复MoE自动调优器缓冲区溢出，防止模型权重损坏。 | 提升**推理稳定性**和**可靠性**，是高性能内核的基础。 |
| **#2857** | 修复`torch.compile` CUDA图兼容性，移除全局缓存。 | 增强与PyTorch生态的**兼容性**，支持更现代的优化技术。 |
| **#3014** | 优化CUTLASS MoE辅助内核，针对小批量解码工作负载。 | 直接优化**解码阶段性能**（生成/推理的核心场景），提升资源利用率。 |
| **#3026** | 移植TRT-LLM的FP4 GEMM优化参数，启用PDL。 | 引入业界（NVIDIA TRT-LLM）**最佳实践**，针对SM120/121架构进行深度优化。 |

**整体关系**：所有变更都紧密围绕项目的核心目标——**提供最高性能、最稳定的GPU推理内核**。优化针对实际推理瓶颈（如解码、小批量），修复确保生产环境安全，体现了项目从“可用”到“高效可靠”的演进。

### 3. 对项目的影响和潜在意义
- **直接影响**：
    - **性能提升**：在特定场景（如小批量解码、NVFP4格式）下获得显著加速（部分案例达1.05x-1.24x）。
    - **稳定性增强**：避免了内存越界导致的静默数据损坏和CUDA图错误。
    - **兼容性扩展**：更好地支持`torch.compile`等PyTorch高级特性。
- **潜在意义**：
    - **巩固技术领先性**：通过吸收TRT-LLM的优化，保持在推理内核性能竞赛中的前沿地位。
    - **拓宽应用场景**：对小批量、MoE模型推理的优化，有助于服务长尾、低延迟的实时推理需求。
    - **降低使用门槛**：修复兼容性问题，使高级用户能更无缝地集成FlashInfer到其优化流水线中。

### 4. 值得关注的技术点
1.  **MoE内核的精细优化**：#3014 揭示了为对齐而进行的无效“N维填充”是巨大性能开销来源，其移除验证了**深入理解硬件（CUTLASS GEMM访问模式）才能实现极致优化**。
2.  **架构特定优化**：#3026 表明针对特定GPU架构（SM120/121）的模板参数调优能带来巨大收益（RTX 5090上FP4 GEMM提升达1.24x），体现了**为硬件量身定制**的重要性。
3.  **内存安全与性能的平衡**：#3025 和 #2857 都涉及缓存/预分配策略。修复方案（动态回退、移除全局缓存）体现了在追求性能时，**必须优先保证正确性和与系统交互的鲁棒性**。
4.  **PDL（Programmatic Dependent Launch）的启用**：这是一种高级CUDA编程技术，用于优化内核间依赖和调度。#3026 启用PDL是向更复杂、更高效内核执行模型迈进的一步。

### 5. 基于项目背景的提交影响分析
FlashInfer旨在成为**LLM及大模型推理的底层高性能基石**。昨日的提交从三个维度强化了这一角色：

1.  **强化核心价值（性能）**：
    - 对**解码阶段**（#3014）和**新硬件架构**（#3026）的优化，直接攻击当前LLM服务（尤其是自回归生成）的**核心性能瓶颈**，提升了项目的核心竞争力。

2.  **提升工业可用性**：
    - 修复缓冲区溢出（#3025）和CUDA图兼容性（#2857）问题，解决了在生产部署中可能遇到的**棘手且危险的错误**，使库更健壮，更适合用于关键业务。

3.  **紧跟技术生态演进**：
    - 吸收TRT-LLM优化、支持`torch.compile`，表明项目积极**融入NVIDIA和PyTorch主导的AI开发生态**，确保其技术不落伍，并能被主流框架更好地利用。

**总结**：昨日的更新是一次高质量的“练内功”。它没有增加新功能，而是通过**修复隐患、优化瓶颈、吸收先进实践**，使FlashInfer作为推理基础设施的**性能更高、底盘更稳、兼容性更好**，巩固了其作为追求极致性能的团队首选底层库的地位。这符合项目从“功能实现”向“性能打磨”和“生产就绪”阶段发展的自然路径。

## 详细提交记录

### [a1166dc](https://github.com/flashinfer-ai/flashinfer/commit/a1166dc0169b479aa3220b61759547d04c64e473)

- **作者**: Lee Nau
- **时间**: 2026-04-10T21:46:39Z
- **提交信息**: Prevent MoE autotuner buffer overflow on large token buckets (#3025)

<!-- .github/pull_request_template.md -->

## 📌 Description

CuteDslMoEWrapper pre-allocates intermediate buffers sized for
max_num_tokens, but the autotuner can probe buckets larger than that
(e.g. 8192 tokens vs 2048 max). The GEMM kernels then write past
buffer bounds, silently corrupting model weights and eventually
triggering cudaErrorIllegalAddress.

Two fixes:
- Check num_tokens <= max_num_tokens before reusing pre-allocated
  buffers; fall back to dynamic allocation when exceeded.
- Move tuning_config to instance level so dummy expert IDs span all
  local experts (randint(0, num_experts)) instead of a hardcoded 8,
  which concentrated routing and inflated permutation buffer sizes.

## 🔍 Related Issues

[feat: cuteDSL fp4 moe for better DSR1
performance.](https://github.com/flashinfer-ai/flashinfer/pull/2398)

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

* **Performance Improvements**
* CUDA-graph preallocation now respects input-size limits to avoid
over-allocation and improve memory behavior for larger token batches.
* Memory gating refined to prevent oversized buffer reuse, improving
inference stability under varying workloads.

* **Stability & Tuning**
* Auto-tuner configuration is now per-run, improving tuning accuracy and
consistency.
* Runtime tuning initialization adapts to the configured expert count
for more representative profiling.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9dc802c](https://github.com/flashinfer-ai/flashinfer/commit/9dc802c471e318c0ef8866730b13f4b75bea8124)

- **作者**: qsang-nv
- **时间**: 2026-04-10T17:38:37Z
- **提交信息**: [fix] bugfix 541: Make single_prefill/decode compatible with torch.compile CUDA graphs (#2857)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
This PR fixes https://github.com/flashinfer-ai/flashinfer/issues/541.

single_prefill_with_kv_cache and single_decode_with_kv_cache fail with
RuntimeError: live storage data ptrs in the cudagraph pool but not
accounted for when used with torch.compile(mode="reduce-overhead").

The root cause is two module-level cached allocations inside these
standalone functions:

_get_cache_buf(...) caches a 32MB workspace buffer in a global dict
_get_cache_alibi_slopes_buf(...) caches ALiBi slopes in the same global
dict
When torch.compile records a CUDA graph, the kernel references these
cached tensors. The graph pool tracker then rejects them as "unaccounted
live pointers" because the global dict holds references that outlive the
graph recording.

The fix replaces cached allocations with local ones in standalone
functions only. Batch wrappers are unaffected -- their plan() runs
outside graph capture, so caching is safe.

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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Refactor**
* Switched workspace allocation to a fixed-size kernel temporary buffer
and supply ALiBi positional slopes only when ALiBi mode is active; added
a configurable kernel-temp size.

* **Tests**
* Added torch.compile (CUDA-graph) regression tests for decode and
prefill kernel paths to ensure correctness under compiled CUDA
execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Qidi Sang <200703406+qsang-nv@users.noreply.github.com>
Co-authored-by: yzh119 <zihaoy@nvidia.com>
Co-authored-by: Zihao Ye <expye@outlook.com>

### [6248936](https://github.com/flashinfer-ai/flashinfer/commit/6248936f92a0076f9ea5cdc2e6a973597c80d634)

- **作者**: Brian K. Ryu
- **时间**: 2026-04-10T15:47:38Z
- **提交信息**: perf: Optimize CUTLASS MoE helper kernels for small-batch decode workloads (#3014)

<!-- .github/pull_request_template.md -->

## 📌 Description

### Summary
Ported optimizations from TRTLLM and expanded a bit:

- Remove unnecessary N-dim SF padding loops from `expandInputRowsKernel`
and `doActivationKernel` — the CUTLASS grouped GEMM never reads scale
factors beyond `tokens_to_expert`
- Add M=0 early exit in `computeStridesTmaWarpSpecializedKernel` to skip
stride/pointer setup for experts with no assigned tokens
- Spread `computeStrides` work across multiple SMs (4 blocks instead of
1)
- Add `__launch_bounds__` to `doActivationKernel` for better register
allocation
- Add new test coverage for N-dim padding safety to confirm that
skipping N-dim SF padding is safe.

### Motivation

When running CUTLASS MoE during the generation phase, three MoE helper
kernels were severely underutilized:

| Kernel  | Issue |
|--------|-------|
| `expandInputRowsKernel` | 87% of time writing zero SF padding for TMA
alignment |
| `doActivationKernel`  | 63% of time writing zero SF padding |
| `computeStridesTmaWarpSpecializedKernel` | grid=1 (single SM), no
early exit for 120 empty experts |

The N-dim SF padding loops iterated over `MinNDimAlignment x num_experts
= 128 x 128 = 16384` potential padding slots to zero scale factors for
token rows beyond each expert's actual token count. This padding was
unnecessary — the CUTLASS grouped GEMM sets `gemm_m = tokens_to_expert`
per expert and never reads scale factors for rows beyond that boundary.


## Changes

**`expandInputRowsKernel` + `doActivationKernel` -- Remove N-dim SF
padding:**
Deleted the entire N-dim SF padding section (after
`griddepcontrol.launch_dependents`) from both kernels. The CUTLASS
grouped GEMM's problem shapes bound the MMA tile access to
`tokens_to_expert` rows per expert; padding rows are never read. Removed
dead `num_padding_tokens` variables from both launchers and simplified
grid formulas to be driven purely by the expanded token count.

K-dim SF padding (inside the per-token main loop) is preserved — MMA
tiles can straddle the `inter_size` boundary within valid rows,
requiring those positions to be zeroed.

**`doActivationKernel` -- `__launch_bounds__`:**
Added `__launch_bounds__(ACTIVATION_THREADS_PER_BLOCK)` to help the
compiler optimize register allocation.

**`computeStridesTmaWarpSpecializedKernel` -- M=0 early exit:**
After writing `problem_shapes[expert]` and `int4_groupwise_params.shape`
(which CUTLASS needs for all experts to traverse the problem list),
experts with `gemm_m == 0` return immediately — skipping
`setupFP4BlockScalingFactors`, `computeTmaWarpSpecializedInputStrides`,
and `computeTmaWarpSpecializedInputPointers` for both GEMMs. For decode
with 128 experts and top_k=8, this skips ~120 experts' full setup.

**`computeStridesTmaWarpSpecializedKernel` -- block size:**
Changed `std::min(1024, num_experts_per_node)` to `std::min(32,
num_experts_per_node)`, spreading 128 experts across 4 blocks on 4 SMs
instead of 1 block on 1 SM.

## Correctness

The N-dim padding removal was validated with 0xFF poisoning: the SF
buffer was filled with 0xFF (worst-case FP8 scale factor values of
+/-448) before the kernel wrote real SFs to valid positions. With
padding positions containing 0xFF, all tests pass with the same error
rates as the original code — confirming the CUTLASS GEMM never reads the
padding positions.

K-dim SF padding is preserved because MMA tiles straddle the K boundary
within valid rows. The original author confirmed: "Tests should fail if
the K dimension padding is disabled, but not if the N dimension stuff
is."

All changes preserve PDL (`griddepcontrol`) overlap — no
`cudaMemsetAsync` or stream operations are introduced.

### Large-batch regression safety

All optimizations are unconditionally beneficial or neutral for large
batches:
- N-dim padding removal: unconditionally removes dead code — the padding
was unnecessary at all batch sizes
- Grid formulas: at large batch, `expanded_tokens` dominates and the
grid remains at `smCount * 8`
- M=0 early exit: doesn't trigger when experts have many tokens
- `__launch_bounds__`: unconditionally better

### Performance Numbers

<details>

<summary>Click to view `flashinfer_benchmark.py` test cases used to
collect the data</summary>

```
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant fp8 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant fp8 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant fp8 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant fp8 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant fp8 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant fp8 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant fp8 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant fp8 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant fp8 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 5120 --intermediate_size 8192 --num_experts 128 --top_k 1 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant fp8 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant fp8 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant fp8 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype float16 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --ep_size 4 --ep_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --cutlass_variant base --input_dtype float16 --tp_size 4 --tp_rank 0 --autotune --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 2048 --intermediate_size 768 --num_experts 128 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype bfloat16 --activation-type Swiglu --tp_size 1 --tp_rank 0 --ep_size 1 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 2048 --intermediate_size 768 --num_experts 128 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype bfloat16 --activation-type Swiglu --tp_size 1 --tp_rank 0 --ep_size 1 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 2048 --intermediate_size 768 --num_experts 128 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype bfloat16 --activation-type Swiglu --tp_size 1 --tp_rank 0 --ep_size 1 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1 --hidden_size 2048 --intermediate_size 1536 --num_experts 128 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype bfloat16 --activation-type Swiglu --tp_size 1 --tp_rank 0 --ep_size 1 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 128 --hidden_size 2048 --intermediate_size 1536 --num_experts 128 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype bfloat16 --activation-type Swiglu --tp_size 1 --tp_rank 0 --ep_size 1 --ep_rank 0 --use_cuda_events --no_cuda_graph
--routine cutlass_fused_moe --num_tokens 1024 --hidden_size 2048 --intermediate_size 1536 --num_experts 128 --top_k 8 --cutlass_variant nvfp4 --quantized_input --input_dtype bfloat16 --activation-type Swiglu --tp_size 1 --tp_rank 0 --ep_size 1 --ep_rank 0 --use_cuda_events --no_cuda_graph
```

</details>

<details>
<summary>Click to view perf data on RTX Pro 6000 SM120) and Spark
(SM121)</summary>

Perf data demonstrated that untargeted cases have no performance impact.
Targeted (NVFP4) CUTLASS MoE cases see speedup on decode cases.

Summary table:
| Category | Count | Spark Geomean | RTX P6K Geomean |
 |----------|-------|---------------|-----------------|
 | Targeted NVFP4 (decode-optimized) | 6 | **1.051x** | **1.021x** |
| Unaffected (base/fp8/large batch) | 72 | 1.008x | 1.006x |
 | All cases | 78 | 1.011x | 1.007x |

Full table:
| # | Test Case | Spark Before (ms) | Spark After (ms) | Spark Speedup |
RTX P6K Before (ms) | RTX P6K After (ms) | RTX P6K Speedup | Category |

|---|-----------|-------------------|------------------|---------------|---------------------|--------------------|--------------------|----------|
| 1 | T=1 H=5120 I=8192 E=128 k=1 base | 1.3061 | 1.3256 | 0.985x |
0.3041 | 0.3033 | 1.003x | |
| 2 | T=1 H=5120 I=8192 E=128 k=1 fp8 | 0.8187 | 0.8264 | 0.991x |
0.2152 | 0.2153 | 0.999x | |
| 3 | T=1 H=5120 I=8192 E=128 k=1 nvfp4 | 0.4329 | 0.4157 | 1.041x |
0.1300 | 0.1331 | 0.977x | |
| 4 | T=1 H=5120 I=8192 E=128 k=1 nvfp4qi | 0.4335 | 0.4127 | 1.051x |
0.1311 | 0.1320 | 0.993x | |
| 5 | T=1 H=5120 I=8192 E=128 k=1 base ep4 | 0.0144 | 0.0152 | 0.950x |
0.0154 | 0.0142 | 1.086x | |
| 6 | T=1 H=5120 I=8192 E=128 k=1 base tp4 | 0.3676 | 0.3757 | 0.978x |
0.1817 | 0.1833 | 0.991x | |
| 7 | T=128 H=5120 I=8192 E=128 k=1 base | 93.9090 | 91.7755 | 1.023x |
12.7980 | 12.8000 | 1.000x | |
| 8 | T=128 H=5120 I=8192 E=128 k=1 fp8 | 55.0527 | 54.1031 | 1.018x |
6.5404 | 6.5444 | 0.999x | |
| 9 | T=128 H=5120 I=8192 E=128 k=1 nvfp4 | 25.2912 | 25.2012 | 1.004x |
3.7753 | 3.7632 | 1.003x | |
| 10 | T=128 H=5120 I=8192 E=128 k=1 nvfp4qi | 25.1966 | 25.2118 |
0.999x | 3.7776 | 3.7699 | 1.002x | |
| 11 | T=128 H=5120 I=8192 E=128 k=1 base ep4 | 22.4435 | 22.5981 |
0.993x | 3.1017 | 3.1058 | 0.999x | |
| 12 | T=128 H=5120 I=8192 E=128 k=1 base tp4 | 22.4918 | 22.6853 |
0.991x | 3.2777 | 3.2813 | 0.999x | |
| 13 | T=1024 H=5120 I=8192 E=128 k=1 base | 144.5477 | 145.0290 |
0.997x | 21.3314 | 21.3340 | 1.000x | |
| 14 | T=1024 H=5120 I=8192 E=128 k=1 fp8 | 82.2042 | 81.8906 | 1.004x |
11.0048 | 11.0082 | 1.000x | |
| 15 | T=1024 H=5120 I=8192 E=128 k=1 nvfp4 | 39.7629 | 39.8295 | 0.998x
| 6.3147 | 6.2995 | 1.002x | |
| 16 | T=1024 H=5120 I=8192 E=128 k=1 nvfp4qi | 39.6928 | 39.8489 |
0.996x | 6.3218 | 6.2758 | 1.007x | |
| 17 | T=1024 H=5120 I=8192 E=128 k=1 base ep4 | 36.2588 | 36.4861 |
0.994x | 5.4456 | 5.4447 | 1.000x | |
| 18 | T=1024 H=5120 I=8192 E=128 k=1 base tp4 | 35.4185 | 35.4508 |
0.999x | 5.4314 | 5.4313 | 1.000x | |
| 19 | T=1 H=7168 I=2048 E=256 k=8 base | 3.2219 | 3.2369 | 0.995x |
0.8597 | 0.8597 | 1.000x | |
| 20 | T=1 H=7168 I=2048 E=256 k=8 fp8 | 1.8355 | 1.8222 | 1.007x |
0.3420 | 0.3417 | 1.001x | |
| 21 | T=1 H=7168 I=2048 E=256 k=8 nvfp4 | 1.0445 | 0.9912 | 1.054x |
0.2591 | 0.2437 | 1.063x | |
| 22 | T=1 H=7168 I=2048 E=256 k=8 nvfp4qi | 1.0440 | 0.9820 | 1.063x |
0.2591 | 0.2448 | 1.059x | |
| 23 | T=1 H=7168 I=2048 E=256 k=8 base ep4 | 1.2269 | 1.2545 | 0.978x |
0.3676 | 0.3670 | 1.001x | |
| 24 | T=1 H=7168 I=2048 E=256 k=8 base tp4 | 0.8725 | 0.8841 | 0.987x |
0.2396 | 0.2396 | 1.000x | |
| 25 | T=128 H=7168 I=2048 E=256 k=8 base | 97.3592 | 97.6644 | 0.997x |
14.6278 | 14.6295 | 1.000x | |
| 26 | T=128 H=7168 I=2048 E=256 k=8 fp8 | 52.8793 | 52.3160 | 1.011x |
7.4488 | 7.4495 | 1.000x | |
| 27 | T=128 H=7168 I=2048 E=256 k=8 nvfp4 | 27.4207 | 27.1848 | 1.009x
| 4.3588 | 4.3220 | 1.009x | |
| 28 | T=128 H=7168 I=2048 E=256 k=8 nvfp4qi | 27.5014 | 27.1511 |
1.013x | 4.3604 | 4.3237 | 1.008x | |
| 29 | T=128 H=7168 I=2048 E=256 k=8 base ep4 | 23.9165 | 23.8423 |
1.003x | 3.7266 | 3.7261 | 1.000x | |
| 30 | T=128 H=7168 I=2048 E=256 k=8 base tp4 | 24.0706 | 24.1821 |
0.995x | 3.7711 | 3.7720 | 1.000x | |
| 31 | T=1024 H=7168 I=2048 E=256 k=8 base | 126.3262 | 127.5760 |
0.990x | 17.5073 | 17.4586 | 1.003x | |
| 32 | T=1024 H=7168 I=2048 E=256 k=8 fp8 | 68.2070 | 68.9878 | 0.989x |
8.3225 | 8.3213 | 1.000x | |
| 33 | T=1024 H=7168 I=2048 E=256 k=8 nvfp4 | 30.1287 | 30.1583 | 0.999x
| 4.8560 | 4.8396 | 1.003x | |
| 34 | T=1024 H=7168 I=2048 E=256 k=8 nvfp4qi | 29.9361 | 29.7770 |
1.005x | 4.8430 | 4.8278 | 1.003x | |
| 35 | T=1024 H=7168 I=2048 E=256 k=8 base ep4 | 30.0261 | 29.8761 |
1.005x | 4.1991 | 4.1916 | 1.002x | |
| 36 | T=1024 H=7168 I=2048 E=256 k=8 base tp4 | 29.5162 | 29.1558 |
1.012x | 4.2802 | 4.2811 | 1.000x | |
| 37 | T=1 H=5120 I=8192 E=128 k=1 base | 1.2212 | 1.2314 | 0.992x |
0.2519 | 0.2519 | 1.000x | |
| 38 | T=1 H=5120 I=8192 E=128 k=1 fp8 | 0.6404 | 0.6404 | 1.000x |
0.1475 | 0.1484 | 0.994x | |
| 39 | T=1 H=5120 I=8192 E=128 k=1 nvfp4 | 0.4505 | 0.4197 | 1.073x |
0.1252 | 0.1230 | 1.018x | |
| 40 | T=1 H=5120 I=8192 E=128 k=1 nvfp4qi | 0.4541 | 0.4108 | 1.106x |
0.1251 | 0.1215 | 1.030x | |
| 41 | T=1 H=5120 I=8192 E=128 k=1 base ep4 | 0.0175 | 0.0174 | 1.006x |
0.0132 | 0.0123 | 1.070x | |
| 42 | T=1 H=5120 I=8192 E=128 k=1 base tp4 | 0.3666 | 0.3687 | 0.994x |
0.0901 | 0.0891 | 1.011x | |
| 43 | T=128 H=5120 I=8192 E=128 k=1 base | 90.6373 | 91.2210 | 0.994x |
12.7805 | 12.7817 | 1.000x | |
| 44 | T=128 H=5120 I=8192 E=128 k=1 fp8 | 44.6182 | 44.7585 | 0.997x |
6.4339 | 6.4344 | 1.000x | |
| 45 | T=128 H=5120 I=8192 E=128 k=1 nvfp4 | 25.6261 | 25.4186 | 1.008x
| 3.7643 | 3.7560 | 1.002x | |
| 46 | T=128 H=5120 I=8192 E=128 k=1 nvfp4qi | 25.6532 | 25.3584 |
1.012x | 3.7627 | 3.7540 | 1.002x | |
| 47 | T=128 H=5120 I=8192 E=128 k=1 base ep4 | 22.2766 | 21.8055 |
1.022x | 3.1002 | 3.0995 | 1.000x | |
| 48 | T=128 H=5120 I=8192 E=128 k=1 base tp4 | 22.5305 | 22.3909 |
1.006x | 3.2462 | 3.2461 | 1.000x | |
| 49 | T=1024 H=5120 I=8192 E=128 k=1 base | 140.0064 | 139.6009 |
1.003x | 21.2091 | 21.2116 | 1.000x | |
| 50 | T=1024 H=5120 I=8192 E=128 k=1 fp8 | 69.0247 | 69.4502 | 0.994x |
10.7856 | 10.8737 | 0.992x | |
| 51 | T=1024 H=5120 I=8192 E=128 k=1 nvfp4 | 40.2212 | 39.9195 | 1.008x
| 6.2956 | 6.2756 | 1.003x | |
| 52 | T=1024 H=5120 I=8192 E=128 k=1 nvfp4qi | 40.2185 | 39.9197 |
1.007x | 6.3109 | 6.2855 | 1.004x | |
| 53 | T=1024 H=5120 I=8192 E=128 k=1 base ep4 | 35.2440 | 34.7130 |
1.015x | 5.3981 | 5.3986 | 1.000x | |
| 54 | T=1024 H=5120 I=8192 E=128 k=1 base tp4 | 35.0929 | 34.7923 |
1.009x | 5.3969 | 5.3954 | 1.000x | |
| 55 | T=1 H=7168 I=2048 E=256 k=8 base | 3.1447 | 3.1472 | 0.999x |
0.5619 | 0.5993 | 0.938x | |
| 56 | T=1 H=7168 I=2048 E=256 k=8 fp8 | 1.6363 | 1.6096 | 1.017x |
0.3256 | 0.3256 | 1.000x | |
| 57 | T=1 H=7168 I=2048 E=256 k=8 nvfp4 | 1.0844 | 1.0019 | 1.082x |
0.2468 | 0.2355 | 1.048x | |
| 58 | T=1 H=7168 I=2048 E=256 k=8 nvfp4qi | 1.0869 | 1.0040 | 1.083x |
0.2499 | 0.2336 | 1.069x | |
| 59 | T=1 H=7168 I=2048 E=256 k=8 base ep4 | 1.2902 | 1.2902 | 1.000x |
0.1956 | 0.1956 | 1.000x | |
| 60 | T=1 H=7168 I=2048 E=256 k=8 base tp4 | 0.8631 | 0.8637 | 0.999x |
0.2005 | 0.1997 | 1.004x | |
| 61 | T=128 H=7168 I=2048 E=256 k=8 base | 95.4863 | 95.3204 | 1.002x |
14.5634 | 14.5612 | 1.000x | |
| 62 | T=128 H=7168 I=2048 E=256 k=8 fp8 | 46.0011 | 45.9304 | 1.002x |
7.3332 | 7.3367 | 1.000x | |
| 63 | T=128 H=7168 I=2048 E=256 k=8 nvfp4 | 27.3023 | 26.9143 | 1.014x
| 4.3172 | 4.2922 | 1.006x | |
| 64 | T=128 H=7168 I=2048 E=256 k=8 nvfp4qi | 27.4191 | 26.9065 |
1.019x | 4.3254 | 4.2943 | 1.007x | |
| 65 | T=128 H=7168 I=2048 E=256 k=8 base ep4 | 24.3881 | 24.2863 |
1.004x | 3.7139 | 3.7150 | 1.000x | |
| 66 | T=128 H=7168 I=2048 E=256 k=8 base tp4 | 23.5841 | 23.6456 |
0.997x | 3.7500 | 3.7499 | 1.000x | |
| 67 | T=1024 H=7168 I=2048 E=256 k=8 base | 104.3629 | 104.1310 |
1.002x | 15.7031 | 15.7159 | 0.999x | |
| 68 | T=1024 H=7168 I=2048 E=256 k=8 fp8 | 49.5421 | 49.4592 | 1.002x |
7.9900 | 7.9933 | 1.000x | |
| 69 | T=1024 H=7168 I=2048 E=256 k=8 nvfp4 | 30.2330 | 29.8347 | 1.013x
| 4.7944 | 4.7812 | 1.003x | |
| 70 | T=1024 H=7168 I=2048 E=256 k=8 nvfp4qi | 29.9776 | 29.6689 |
1.010x | 4.7790 | 4.7718 | 1.002x | |
| 71 | T=1024 H=7168 I=2048 E=256 k=8 base ep4 | 26.2313 | 26.3157 |
0.997x | 3.9859 | 3.9855 | 1.000x | |
| 72 | T=1024 H=7168 I=2048 E=256 k=8 base tp4 | 27.7164 | 27.7785 |
0.998x | 4.2291 | 4.2261 | 1.001x | |
| 73 | T=1 H=2048 I=768 E=128 k=8 nvfp4qi | 0.2232 | 0.1987 | **1.123x**
| 0.0705 | 0.0686 | **1.028x** | **TARGETED** |
| 74 | T=128 H=2048 I=768 E=128 k=8 nvfp4qi | 1.6925 | 1.6194 |
**1.045x** | 0.3602 | 0.3553 | **1.014x** | **TARGETED** |
| 75 | T=1024 H=2048 I=768 E=128 k=8 nvfp4qi | 2.2461 | 2.2195 |
**1.012x** | 0.4055 | 0.3941 | **1.029x** | **TARGETED** |
| 76 | T=1 H=2048 I=1536 E=128 k=8 nvfp4qi | 0.3179 | 0.2878 |
**1.105x** | 0.0967 | 0.0886 | **1.092x** | **TARGETED** |
| 77 | T=128 H=2048 I=1536 E=128 k=8 nvfp4qi | 3.1408 | 3.1017 |
**1.013x** | 0.5934 | 0.5847 | **1.015x** | **TARGETED** |
| 78 | T=1024 H=2048 I=1536 E=128 k=8 nvfp4qi | 4.0100 | 3.9479 |
**1.016x** | 0.6842 | 0.6788 | **1.008x** | **TARGETED** |

</details>

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

#3013
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

* **Performance**
* Reduced unnecessary work for empty experts and tightened
activation/grid sizing so only required entries are processed, improving
memory efficiency and GPU utilization.
* **Bug Fixes**
* Fixed edge cases that could produce incorrect outputs when many
experts are empty and removed unsafe padding work that risked
uninitialized values.
* **Tests**
* Added CUDA-architecture gated tests verifying numerical correctness
and memory-safety (including poisoning checks) for the modified paths.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c0adda7](https://github.com/flashinfer-ai/flashinfer/commit/c0adda7d866084326d8e4d81e173767a76634d85)

- **作者**: Brian K. Ryu
- **时间**: 2026-04-10T15:46:31Z
- **提交信息**: perf: Port TRT-LLM SM120/SM121 FP4 CUTLASS GEMM optimizations. Add PDL (#3026)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

### Summary

- Port TRT-LLM's SM120 CUTLASS FP4 GEMM template parameters for better
kernel performance
- [TRT-LLM reference file:
nvfp4_nvfp4_gemm_template_sm120.h](https://github.com/NVIDIA/TensorRT-LLM/blob/0de88a283141888a3e4b55bb03e862068c18eb1b/cpp/tensorrt_llm/kernels/cutlass_kernels/fp4_gemm/nvfp4_nvfp4_gemm_template_sm120.h)
- Enable PDL (programmatic dependent launch) for SM120/SM121 FP4 GEMM
### Details

#### TRT-LLM kernel parameter port

Updated the SM120 FP4 GEMM kernel template (`fp4_gemm_template_sm120.h`)
to match TRT-LLM's optimized configuration:

| Parameter | Before | After |
|-----------|--------|-------|
| Mainloop schedule | `KernelScheduleAuto` |
`KernelTmaWarpSpecializedCooperative` |
| Stage count | `StageCount<2>` (fixed) |
`StageCountAutoCarveout<sizeof(EpilogueSharedStorage)>` |
| Tile scheduler | `void` (data-parallel) | `StaticPersistentScheduler`
|
| Epilogue schedule | `EpilogueScheduleAuto` | `TmaWarpSpecialized` |
| Epilogue OpClass | `OpClassBlockScaledTensorOp` | `OpClassTensorOp` |

1. `KernelScheduleAuto` → `KernelTmaWarpSpecializedCooperative` —
Removes auto-resolution ambiguity. Explicitly selects the cooperative
warp-specialized mainloop where dedicated warps handle TMA loads while
others run MMA.
2. `StageCount<2>` →
`StageCountAutoCarveout<sizeof(EpilogueSharedStorage)>` — Instead of a
hardcoded 2-stage pipeline, dynamically computes how many stages fit in
shared memory after reserving space for the epilogue. More stages =
better latency hiding of TMA loads behind MMA compute.
3. void (scheduler) → `StaticPersistentScheduler` — The old void
scheduler launches one CTA per output tile (data-parallel). The
persistent scheduler launches fewer CTAs that loop over multiple tiles,
reducing kernel launch overhead — most impactful at small M where the
kernel is short.
4. `EpilogueScheduleAuto` → `TmaWarpSpecialized` — Explicitly selects
TMA-based epilogue with warp specialization for output writes, rather
than relying on auto-resolution.
5. `OpClassBlockScaledTensorOp` → `OpClassTensorOp` (in epilogue builder
only) — The epilogue doesn't need the block-scaled op class (that's only
for the mainloop MMA). Using OpClassTensorOp matches what TRT-LLM uses
and avoids potential misrouting in the epilogue collective builder.

The persistent scheduler reduces launch overhead (most impactful for
small M), dynamic stage carveout adapts pipeline depth to available
smem, and explicit cooperative warp specialization avoids
auto-resolution ambiguity.

#### PDL enablement

Changed `enablePDL=false` → `enablePDL=true` in `runFp4GemmImpl`. The
`CUTLASS_ENABLE_GDC_FOR_SM100=1` compile flag is already set (since PR
#2780), and both SM100 FP4 GEMM and SM120 MXFP8 GEMM already run with
PDL enabled. The `false` was a stale leftover.

#### Performance Numbers on RTX 5090 (SM120) and DGX Spark (SM121)

Performance changes most relevant to SM120. Very minor on Spark

<details>

<summary>Click to view non-autotune backend=cutlass data</summary>

| M | N | K | RTX 5090 Before (us) | RTX 5090 After (us) | RTX 5090
Speedup | Spark Before (us) | Spark After (us) | Spark Speedup |

|--:|--:|--:|---------------------:|--------------------:|-----------------:|-------------------:|-----------------:|--------------:|
| 1 | 512 | 7168 | 33.44 | 24.21 | 1.38x | 40.51 | 32.56 | 1.24x |
| 1 | 896 | 1024 | 7.41 | 6.26 | 1.18x | 11.49 | 10.93 | 1.05x |
| 1 | 896 | 5120 | 25.41 | 18.22 | 1.39x | 39.22 | 36.40 | 1.08x |
| 1 | 1024 | 7168 | 34.30 | 24.11 | 1.42x | 57.07 | 56.47 | 1.01x |
| 1 | 1280 | 8192 | 39.25 | 27.49 | 1.43x | 77.92 | 68.90 | 1.13x |
| 1 | 1792 | 5120 | 26.43 | 19.22 | 1.38x | 63.62 | 60.80 | 1.05x |
| 1 | 2560 | 8192 | 40.54 | 29.12 | 1.39x | 117.75 | 118.08 | 1.00x |
| 1 | 3584 | 5120 | 27.81 | 21.89 | 1.27x | 99.25 | 102.31 | 0.97x |
| 1 | 4608 | 7168 | 39.87 | 32.24 | 1.24x | 156.40 | 165.52 | 0.94x |
| 1 | 5120 | 640 | 7.02 | 6.56 | 1.07x | 25.98 | 27.81 | 0.93x |
| 1 | 5120 | 1024 | 9.52 | 8.10 | 1.18x | 34.85 | 36.08 | 0.97x |
| 1 | 5120 | 1280 | 10.78 | 9.09 | 1.19x | 44.58 | 44.08 | 1.01x |
| 1 | 5120 | 2048 | 15.28 | 12.13 | 1.26x | 61.92 | 66.31 | 0.93x |
| 1 | 5120 | 2560 | 18.67 | 14.69 | 1.27x | 74.34 | 79.49 | 0.94x |
| 1 | 5120 | 4096 | 26.08 | 18.72 | 1.39x | 112.26 | 114.30 | 0.98x |
| 1 | 5120 | 5120 | 32.96 | 23.81 | 1.38x | 134.56 | 128.22 | 1.05x |
| 1 | 5120 | 8192 | 44.27 | 33.86 | 1.31x | 185.91 | 186.32 | 1.00x |
| 1 | 5120 | 16384 | 76.08 | 58.78 | 1.29x | 363.43 | 350.37 | 1.04x |
| 1 | 7168 | 256 | 5.25 | 4.83 | 1.09x | 16.83 | 17.01 | 0.99x |
| 1 | 7168 | 512 | 7.15 | 6.83 | 1.05x | 29.23 | 30.48 | 0.96x |
| 1 | 7168 | 4608 | 33.82 | 25.71 | 1.32x | 164.31 | 160.51 | 1.02x |
| 1 | 7168 | 5120 | 36.64 | 27.81 | 1.32x | 172.45 | 168.47 | 1.02x |
| 1 | 8192 | 1024 | 10.86 | 9.76 | 1.11x | 52.06 | 53.04 | 0.98x |
| 1 | 8192 | 2048 | 17.25 | 14.74 | 1.17x | 93.04 | 97.04 | 0.96x |
| 1 | 8192 | 3584 | 28.30 | 21.94 | 1.29x | 146.85 | 145.09 | 1.01x |
| 1 | 8192 | 4096 | 30.96 | 23.94 | 1.29x | 157.25 | 156.91 | 1.00x |
| 1 | 8192 | 7168 | 47.34 | 38.13 | 1.24x | 237.52 | 225.07 | 1.06x |
| 1 | 8192 | 8192 | 50.40 | 42.67 | 1.18x | 275.88 | 257.28 | 1.07x |
| 1 | 8192 | 14336 | 83.90 | 70.38 | 1.19x | 434.72 | 392.92 | 1.11x |
| 1 | 8192 | 28672 | 160.99 | 135.05 | 1.19x | 829.34 | 744.18 | 1.11x |
| 1 | 9216 | 7168 | 50.96 | 45.76 | 1.11x | 245.39 | 247.07 | 0.99x |
| 1 | 10240 | 8192 | 55.50 | 50.74 | 1.09x | 333.86 | 295.54 | 1.13x |
| 4 | 512 | 7168 | 33.33 | 24.29 | 1.37x | 40.15 | 32.53 | 1.23x |
| 4 | 896 | 1024 | 7.38 | 6.21 | 1.19x | 12.19 | 10.86 | 1.12x |
| 4 | 1024 | 7168 | 34.35 | 24.37 | 1.41x | 60.08 | 57.09 | 1.05x |
| 4 | 4608 | 7168 | 39.84 | 32.24 | 1.24x | 161.06 | 156.94 | 1.03x |
| 4 | 7168 | 256 | 5.12 | 5.04 | 1.02x | 16.62 | 16.42 | 1.01x |
| 4 | 7168 | 512 | 7.15 | 6.91 | 1.03x | 28.90 | 30.21 | 0.96x |
| 4 | 7168 | 2304 | 18.38 | 14.93 | 1.23x | 94.98 | 98.29 | 0.97x |
| 4 | 7168 | 4608 | 33.97 | 25.07 | 1.35x | 165.94 | 164.06 | 1.01x |
| 4 | 9216 | 7168 | 50.80 | 45.89 | 1.11x | 253.52 | 252.55 | 1.00x |
| 8 | 896 | 5120 | 25.62 | 18.45 | 1.39x | 38.56 | 37.52 | 1.03x |
| 8 | 1280 | 8192 | 39.02 | 27.62 | 1.41x | 79.87 | 70.10 | 1.14x |
| 8 | 1792 | 5120 | 26.32 | 19.17 | 1.37x | 63.01 | 59.20 | 1.06x |
| 8 | 2560 | 8192 | 40.42 | 28.91 | 1.40x | 120.05 | 118.18 | 1.02x |
| 8 | 3584 | 5120 | 27.55 | 21.82 | 1.26x | 102.66 | 101.36 | 1.01x |
| 8 | 5120 | 640 | 7.14 | 6.34 | 1.13x | 25.58 | 27.07 | 0.95x |
| 8 | 5120 | 1024 | 9.44 | 8.00 | 1.18x | 35.81 | 36.62 | 0.98x |
| 8 | 5120 | 1280 | 11.12 | 9.23 | 1.20x | 42.69 | 44.38 | 0.96x |
| 8 | 5120 | 2048 | 15.06 | 11.76 | 1.28x | 63.92 | 67.30 | 0.95x |
| 8 | 5120 | 2560 | 18.54 | 14.14 | 1.31x | 73.60 | 78.85 | 0.93x |
| 8 | 5120 | 4096 | 26.27 | 18.70 | 1.40x | 115.06 | 112.67 | 1.02x |
| 8 | 5120 | 5120 | 33.33 | 23.62 | 1.41x | 132.08 | 132.91 | 0.99x |
| 8 | 5120 | 8192 | 43.94 | 34.35 | 1.28x | 191.14 | 182.59 | 1.05x |
| 8 | 5120 | 16384 | 76.32 | 58.82 | 1.30x | 368.77 | 302.40 | 1.22x |
| 8 | 7168 | 5120 | 36.64 | 26.14 | 1.40x | 172.30 | 175.75 | 0.98x |
| 8 | 8192 | 1024 | 10.80 | 9.55 | 1.13x | 50.45 | 53.57 | 0.94x |
| 8 | 8192 | 2048 | 17.01 | 14.40 | 1.18x | 93.47 | 95.66 | 0.98x |
| 8 | 8192 | 3584 | 28.21 | 21.26 | 1.33x | 144.23 | 147.04 | 0.98x |
| 8 | 8192 | 4096 | 30.94 | 23.38 | 1.32x | 154.69 | 151.47 | 1.02x |
| 8 | 8192 | 7168 | 47.23 | 37.18 | 1.27x | 244.32 | 223.83 | 1.09x |
| 8 | 8192 | 8192 | 50.08 | 42.03 | 1.19x | 280.23 | 267.97 | 1.05x |
| 8 | 8192 | 14336 | 83.30 | 69.89 | 1.19x | 418.08 | 403.96 | 1.03x |
| 8 | 8192 | 28672 | 159.25 | 132.94 | 1.20x | 829.61 | 726.61 | 1.14x |
| 8 | 10240 | 8192 | 54.66 | 51.71 | 1.06x | 328.87 | 301.07 | 1.09x |
| 16 | 512 | 7168 | 33.34 | 24.21 | 1.38x | 40.51 | 33.52 | 1.21x |
| 16 | 896 | 1024 | 7.49 | 6.37 | 1.18x | 11.89 | 11.41 | 1.04x |
| 16 | 1024 | 7168 | 34.54 | 24.51 | 1.41x | 60.06 | 56.43 | 1.06x |
| 16 | 4608 | 7168 | 39.82 | 32.34 | 1.23x | 163.44 | 166.00 | 0.98x |
| 16 | 7168 | 256 | 5.22 | 5.26 | 0.99x | 17.66 | 17.79 | 0.99x |
| 16 | 7168 | 512 | 6.96 | 6.99 | 1.00x | 28.75 | 29.84 | 0.96x |
| 16 | 7168 | 2304 | 18.53 | 14.45 | 1.28x | 94.67 | 97.73 | 0.97x |
| 16 | 7168 | 4608 | 34.05 | 24.14 | 1.41x | 163.09 | 158.32 | 1.03x |
| 16 | 9216 | 7168 | 49.70 | 42.75 | 1.16x | 253.16 | 237.79 | 1.06x |
| 64 | 512 | 7168 | 33.18 | 24.14 | 1.37x | 42.99 | 36.46 | 1.18x |
| 64 | 896 | 1024 | 7.76 | 6.42 | 1.21x | 12.22 | 11.07 | 1.10x |
| 64 | 896 | 5120 | 25.36 | 18.24 | 1.39x | 40.54 | 38.53 | 1.05x |
| 64 | 1280 | 8192 | 38.89 | 27.33 | 1.42x | 79.94 | 71.98 | 1.11x |
| 64 | 1792 | 5120 | 26.22 | 19.20 | 1.37x | 66.29 | 61.71 | 1.07x |
| 64 | 2560 | 8192 | 40.29 | 28.72 | 1.40x | 120.77 | 116.37 | 1.04x |
| 64 | 3584 | 5120 | 27.98 | 22.18 | 1.26x | 101.94 | 104.29 | 0.98x |
| 64 | 4608 | 7168 | 39.97 | 32.61 | 1.23x | 160.07 | 162.56 | 0.98x |
| 64 | 5120 | 640 | 7.06 | 6.48 | 1.09x | 28.54 | 30.43 | 0.94x |
| 64 | 5120 | 1024 | 9.52 | 7.78 | 1.22x | 38.27 | 39.98 | 0.96x |
| 64 | 5120 | 1280 | 10.91 | 8.75 | 1.25x | 44.70 | 46.42 | 0.96x |
| 64 | 5120 | 2048 | 15.17 | 11.44 | 1.33x | 63.87 | 68.66 | 0.93x |
| 64 | 5120 | 2560 | 18.88 | 14.08 | 1.34x | 76.58 | 81.49 | 0.94x |
| 64 | 5120 | 4096 | 26.24 | 19.07 | 1.38x | 111.94 | 114.82 | 0.97x |
| 64 | 5120 | 5120 | 33.06 | 23.41 | 1.41x | 133.20 | 130.75 | 1.02x |
| 64 | 5120 | 8192 | 44.27 | 34.56 | 1.28x | 185.28 | 185.75 | 1.00x |
| 64 | 5120 | 16384 | 76.03 | 58.94 | 1.29x | 359.46 | 345.33 | 1.04x |
| 64 | 7168 | 256 | 5.28 | 5.12 | 1.03x | 22.58 | 20.67 | 1.09x |
| 64 | 7168 | 512 | 7.10 | 6.61 | 1.08x | 34.05 | 32.66 | 1.04x |
| 64 | 7168 | 2304 | 18.37 | 13.71 | 1.34x | 97.34 | 96.88 | 1.00x |
| 64 | 7168 | 4608 | 34.11 | 24.24 | 1.41x | 165.67 | 161.65 | 1.02x |
| 64 | 7168 | 5120 | 36.83 | 25.38 | 1.45x | 172.74 | 168.59 | 1.02x |
| 64 | 8192 | 1024 | 10.91 | 9.02 | 1.21x | 53.84 | 58.08 | 0.93x |
| 64 | 8192 | 2048 | 17.01 | 12.93 | 1.32x | 94.61 | 100.69 | 0.94x |
| 64 | 8192 | 3584 | 28.40 | 18.94 | 1.50x | 148.11 | 145.75 | 1.02x |
| 64 | 8192 | 4096 | 31.44 | 21.38 | 1.47x | 160.27 | 157.68 | 1.02x |
| 64 | 8192 | 7168 | 47.04 | 34.53 | 1.36x | 240.47 | 225.95 | 1.06x |
| 64 | 8192 | 8192 | 49.84 | 35.57 | 1.40x | 273.67 | 266.80 | 1.03x |
| 64 | 8192 | 14336 | 83.20 | 67.71 | 1.23x | 424.20 | 393.78 | 1.08x |
| 64 | 8192 | 28672 | 159.34 | 128.72 | 1.24x | 822.04 | 832.97 | 0.99x
|
| 64 | 9216 | 7168 | 49.31 | 35.46 | 1.39x | 249.94 | 245.95 | 1.02x |
| 64 | 10240 | 8192 | 52.86 | 38.69 | 1.37x | 327.35 | 310.00 | 1.06x |
| 256 | 512 | 7168 | 35.41 | 24.53 | 1.44x | 55.46 | 48.11 | 1.15x |
| 256 | 896 | 1024 | 7.74 | 6.66 | 1.16x | 17.84 | 17.95 | 0.99x |
| 256 | 1024 | 7168 | 35.87 | 24.75 | 1.45x | 76.00 | 63.39 | 1.20x |
| 256 | 4608 | 7168 | 42.16 | 34.30 | 1.23x | 164.87 | 163.31 | 1.01x |
| 256 | 7168 | 256 | 5.25 | 5.20 | 1.01x | 41.76 | 42.86 | 0.97x |
| 256 | 7168 | 512 | 7.26 | 7.09 | 1.02x | 50.51 | 49.62 | 1.02x |
| 256 | 7168 | 2304 | 18.99 | 16.06 | 1.18x | 104.43 | 101.62 | 1.03x |
| 256 | 7168 | 4608 | 34.98 | 27.58 | 1.27x | 163.86 | 162.93 | 1.01x |
| 256 | 9216 | 7168 | 50.67 | 40.33 | 1.26x | 260.03 | 271.68 | 0.96x |
| 512 | 896 | 5120 | 26.91 | 18.96 | 1.42x | 60.56 | 54.32 | 1.11x |
| 512 | 1280 | 8192 | 41.28 | 28.72 | 1.44x | 105.22 | 90.66 | 1.16x |
| 512 | 1792 | 5120 | 28.21 | 20.16 | 1.40x | 97.89 | 91.62 | 1.07x |
| 512 | 2560 | 8192 | 42.99 | 30.00 | 1.43x | 152.29 | 141.06 | 1.08x |
| 512 | 3584 | 5120 | 32.16 | 24.62 | 1.31x | 135.03 | 122.02 | 1.11x |
| 512 | 5120 | 640 | 8.16 | 7.98 | 1.02x | 63.87 | 61.34 | 1.04x |
| 512 | 5120 | 1024 | 10.48 | 10.29 | 1.02x | 66.77 | 68.75 | 0.97x |
| 512 | 5120 | 1280 | 12.90 | 11.87 | 1.09x | 73.70 | 71.49 | 1.03x |
| 512 | 5120 | 2048 | 16.37 | 14.54 | 1.13x | 92.21 | 89.97 | 1.02x |
| 512 | 5120 | 2560 | 19.70 | 16.67 | 1.18x | 101.78 | 99.81 | 1.02x |
| 512 | 5120 | 4096 | 28.40 | 23.65 | 1.20x | 135.20 | 132.02 | 1.02x |
| 512 | 5120 | 5120 | 35.23 | 30.22 | 1.17x | 161.71 | 157.74 | 1.03x |
| 512 | 5120 | 8192 | 47.73 | 43.36 | 1.10x | 247.28 | 219.99 | 1.12x |
| 512 | 5120 | 16384 | 87.04 | 83.89 | 1.04x | 514.40 | 455.68 | 1.13x |
| 512 | 7168 | 5120 | 55.14 | 48.03 | 1.15x | 196.05 | 190.27 | 1.03x |
| 512 | 8192 | 1024 | 17.60 | 15.31 | 1.15x | 89.22 | 90.63 | 0.98x |
| 512 | 8192 | 2048 | 27.54 | 23.38 | 1.18x | 119.07 | 116.29 | 1.02x |
| 512 | 8192 | 3584 | 42.91 | 34.70 | 1.24x | 172.43 | 161.55 | 1.07x |
| 512 | 8192 | 4096 | 46.62 | 39.22 | 1.19x | 181.83 | 170.42 | 1.07x |
| 512 | 8192 | 7168 | 74.46 | 70.08 | 1.06x | 294.77 | 290.51 | 1.01x |
| 512 | 8192 | 8192 | 81.47 | 80.03 | 1.02x | 361.88 | 318.24 | 1.14x |
| 512 | 8192 | 14336 | 142.05 | 127.65 | 1.11x | 595.53 | 590.39 | 1.01x
|
| 512 | 8192 | 28672 | 264.89 | 245.31 | 1.08x | 1418.62 | 1580.70 |
0.90x |
| 512 | 10240 | 8192 | 86.21 | 85.76 | 1.01x | 421.49 | 386.77 | 1.09x |
| 1024 | 512 | 7168 | 36.18 | 25.02 | 1.45x | 79.36 | 78.77 | 1.01x |
| 1024 | 896 | 1024 | 8.27 | 6.86 | 1.21x | 34.40 | 34.05 | 1.01x |
| 1024 | 1024 | 7168 | 36.22 | 26.24 | 1.38x | 116.93 | 115.79 | 1.01x |
| 1024 | 4608 | 7168 | 71.78 | 70.90 | 1.01x | 284.24 | 245.55 | 1.16x |
| 1024 | 7168 | 256 | 13.07 | 12.82 | 1.02x | 101.09 | 102.47 | 0.99x |
| 1024 | 7168 | 512 | 18.40 | 18.18 | 1.01x | 110.42 | 105.12 | 1.05x |
| 1024 | 7168 | 4608 | 72.54 | 72.72 | 1.00x | 294.99 | 255.68 | 1.15x |
| 1024 | 9216 | 7168 | 133.60 | 128.05 | 1.04x | 488.16 | 440.69 | 1.11x
|

**RTX 5090 (SM120) geomean: 1.24x** (147 shapes)
**DGX Spark (SM121) geomean: 1.03x** (147 shapes)

</details>

<details>

<summary>Click to view autotuned backend=cutlass data</summary>

| M | N | K | RTX 5090 Before (us) | RTX 5090 After (us) | RTX 5090
Speedup | Spark Before (us) | Spark After (us) | Spark Speedup |

|--:|--:|--:|---------------------:|--------------------:|-----------------:|-------------------:|-----------------:|--------------:|
| 1 | 512 | 7168 | 18.02 | 18.22 | 0.99x | 33.23 | 33.76 | 0.98x |
| 1 | 896 | 1024 | 7.66 | 6.29 | 1.22x | 11.46 | 11.15 | 1.03x |
| 1 | 896 | 5120 | 19.04 | 18.11 | 1.05x | 38.30 | 32.75 | 1.17x |
| 1 | 1024 | 7168 | 18.50 | 18.43 | 1.00x | 53.86 | 49.82 | 1.08x |
| 1 | 1280 | 8192 | 20.62 | 20.61 | 1.00x | 78.66 | 58.50 | 1.34x |
| 1 | 1792 | 5120 | 17.73 | 17.71 | 1.00x | 50.85 | 50.85 | 1.00x |
| 1 | 2560 | 8192 | 23.30 | 23.36 | 1.00x | 119.12 | 102.22 | 1.17x |
| 1 | 3584 | 5120 | 21.01 | 21.41 | 0.98x | 89.30 | 89.87 | 0.99x |
| 1 | 4608 | 7168 | 31.65 | 31.52 | 1.00x | 144.53 | 146.66 | 0.99x |
| 1 | 5120 | 640 | 7.39 | 7.01 | 1.05x | 25.14 | 27.23 | 0.92x |
| 1 | 5120 | 1024 | 9.22 | 7.84 | 1.18x | 30.08 | 31.68 | 0.95x |
| 1 | 5120 | 1280 | 11.41 | 9.44 | 1.21x | 36.99 | 37.17 | 1.00x |
| 1 | 5120 | 2048 | 11.87 | 11.84 | 1.00x | 54.77 | 57.01 | 0.96x |
| 1 | 5120 | 2560 | 14.03 | 13.95 | 1.01x | 66.35 | 67.98 | 0.98x |
| 1 | 5120 | 4096 | 20.51 | 20.24 | 1.01x | 103.73 | 104.11 | 1.00x |
| 1 | 5120 | 5120 | 25.06 | 25.06 | 1.00x | 123.17 | 126.34 | 0.97x |
| 1 | 5120 | 8192 | 37.23 | 37.17 | 1.00x | 174.11 | 174.40 | 1.00x |
| 1 | 5120 | 16384 | 48.45 | 51.06 | 0.95x | 283.86 | 322.80 | 0.88x |
| 1 | 7168 | 256 | 5.39 | 5.39 | 1.00x | 15.90 | 15.71 | 1.01x |
| 1 | 7168 | 512 | 7.09 | 6.48 | 1.09x | 24.83 | 25.63 | 0.97x |
| 1 | 7168 | 4608 | 26.02 | 26.13 | 1.00x | 153.87 | 151.95 | 1.01x |
| 1 | 7168 | 5120 | 27.74 | 27.76 | 1.00x | 161.59 | 161.07 | 1.00x |
| 1 | 8192 | 1024 | 10.78 | 9.25 | 1.17x | 45.50 | 46.02 | 0.99x |
| 1 | 8192 | 2048 | 14.43 | 14.74 | 0.98x | 84.37 | 84.59 | 1.00x |
| 1 | 8192 | 3584 | 21.06 | 20.85 | 1.01x | 135.01 | 143.39 | 0.94x |
| 1 | 8192 | 4096 | 22.69 | 22.58 | 1.00x | 145.15 | 153.68 | 0.94x |
| 1 | 8192 | 7168 | 41.78 | 41.63 | 1.00x | 217.84 | 220.16 | 0.99x |
| 1 | 8192 | 8192 | 39.95 | 39.60 | 1.01x | 236.24 | 241.62 | 0.98x |
| 1 | 8192 | 14336 | 68.69 | 68.91 | 1.00x | 382.00 | 369.38 | 1.03x |
| 1 | 8192 | 28672 | 107.68 | 115.58 | 0.93x | 678.04 | 660.97 | 1.03x |
| 1 | 9216 | 7168 | 39.46 | 39.70 | 0.99x | 232.34 | 235.35 | 0.99x |
| 1 | 10240 | 8192 | 46.58 | 46.62 | 1.00x | 271.54 | 272.16 | 1.00x |
| 4 | 512 | 7168 | 18.11 | 18.19 | 1.00x | 33.54 | 32.96 | 1.02x |
| 4 | 896 | 1024 | 7.54 | 6.34 | 1.19x | 11.55 | 12.13 | 0.95x |
| 4 | 1024 | 7168 | 18.53 | 18.56 | 1.00x | 52.91 | 50.34 | 1.05x |
| 4 | 4608 | 7168 | 28.35 | 28.35 | 1.00x | 151.09 | 151.84 | 1.00x |
| 4 | 7168 | 256 | 5.23 | 5.20 | 1.01x | 13.65 | 15.89 | 0.86x |
| 4 | 7168 | 512 | 7.10 | 6.90 | 1.03x | 24.40 | 24.98 | 0.98x |
| 4 | 7168 | 2304 | 14.67 | 14.50 | 1.01x | 85.19 | 84.83 | 1.00x |
| 4 | 7168 | 4608 | 25.12 | 25.29 | 0.99x | 152.78 | 154.56 | 0.99x |
| 4 | 9216 | 7168 | 43.81 | 44.06 | 0.99x | 234.69 | 229.35 | 1.02x |
| 8 | 896 | 5120 | 18.78 | 17.94 | 1.05x | 38.53 | 32.77 | 1.18x |
| 8 | 1280 | 8192 | 20.82 | 20.74 | 1.00x | 79.50 | 69.73 | 1.14x |
| 8 | 1792 | 5120 | 17.90 | 17.81 | 1.01x | 59.34 | 51.36 | 1.16x |
| 8 | 2560 | 8192 | 24.88 | 24.94 | 1.00x | 114.83 | 117.66 | 0.98x |
| 8 | 3584 | 5120 | 21.02 | 21.20 | 0.99x | 101.44 | 99.06 | 1.02x |
| 8 | 5120 | 640 | 7.33 | 6.58 | 1.11x | 25.76 | 26.70 | 0.96x |
| 8 | 5120 | 1024 | 9.39 | 8.06 | 1.16x | 30.50 | 31.87 | 0.96x |
| 8 | 5120 | 1280 | 11.57 | 9.74 | 1.19x | 36.91 | 35.79 | 1.03x |
| 8 | 5120 | 2048 | 11.87 | 11.65 | 1.02x | 56.43 | 56.43 | 1.00x |
| 8 | 5120 | 2560 | 14.02 | 13.90 | 1.01x | 68.37 | 68.45 | 1.00x |
| 8 | 5120 | 4096 | 20.16 | 20.13 | 1.00x | 103.52 | 103.87 | 1.00x |
| 8 | 5120 | 5120 | 24.75 | 24.94 | 0.99x | 121.55 | 119.50 | 1.02x |
| 8 | 5120 | 8192 | 37.07 | 37.20 | 1.00x | 173.04 | 172.53 | 1.00x |
| 8 | 5120 | 16384 | 51.33 | 50.30 | 1.02x | 283.96 | 326.53 | 0.87x |
| 8 | 7168 | 5120 | 27.49 | 27.66 | 0.99x | 161.65 | 159.49 | 1.01x |
| 8 | 8192 | 1024 | 10.62 | 9.47 | 1.12x | 44.70 | 46.62 | 0.96x |
| 8 | 8192 | 2048 | 14.32 | 14.06 | 1.02x | 84.16 | 86.10 | 0.98x |
| 8 | 8192 | 3584 | 20.64 | 20.50 | 1.01x | 131.86 | 139.46 | 0.95x |
| 8 | 8192 | 4096 | 22.30 | 22.03 | 1.01x | 145.59 | 150.77 | 0.97x |
| 8 | 8192 | 7168 | 38.27 | 38.40 | 1.00x | 214.35 | 218.35 | 0.98x |
| 8 | 8192 | 8192 | 43.68 | 43.84 | 1.00x | 243.68 | 241.41 | 1.01x |
| 8 | 8192 | 14336 | 61.98 | 62.03 | 1.00x | 367.09 | 369.95 | 0.99x |
| 8 | 8192 | 28672 | 108.59 | 119.36 | 0.91x | 655.06 | 666.76 | 0.98x |
| 8 | 10240 | 8192 | 46.66 | 46.54 | 1.00x | 272.71 | 274.53 | 0.99x |
| 16 | 512 | 7168 | 18.35 | 18.16 | 1.01x | 34.06 | 34.77 | 0.98x |
| 16 | 896 | 1024 | 7.52 | 6.29 | 1.20x | 11.55 | 11.46 | 1.01x |
| 16 | 1024 | 7168 | 18.66 | 18.59 | 1.00x | 56.22 | 52.14 | 1.08x |
| 16 | 4608 | 7168 | 32.10 | 32.02 | 1.00x | 145.23 | 144.00 | 1.01x |
| 16 | 7168 | 256 | 5.31 | 5.20 | 1.02x | 16.34 | 15.82 | 1.03x |
| 16 | 7168 | 512 | 6.88 | 6.80 | 1.01x | 25.22 | 24.83 | 1.02x |
| 16 | 7168 | 2304 | 14.78 | 14.45 | 1.02x | 86.53 | 88.06 | 0.98x |
| 16 | 7168 | 4608 | 25.57 | 25.33 | 1.01x | 155.12 | 150.93 | 1.03x |
| 16 | 9216 | 7168 | 38.93 | 39.15 | 0.99x | 233.67 | 236.93 | 0.99x |
| 64 | 512 | 7168 | 18.22 | 18.37 | 0.99x | 35.49 | 35.09 | 1.01x |
| 64 | 896 | 1024 | 7.60 | 6.27 | 1.21x | 12.72 | 12.06 | 1.05x |
| 64 | 896 | 5120 | 19.07 | 17.73 | 1.08x | 47.81 | 34.64 | 1.38x |
| 64 | 1280 | 8192 | 20.66 | 20.42 | 1.01x | 82.32 | 80.67 | 1.02x |
| 64 | 1792 | 5120 | 17.95 | 19.47 | 0.92x | 64.10 | 53.47 | 1.20x |
| 64 | 2560 | 8192 | 21.90 | 21.76 | 1.01x | 106.39 | 104.69 | 1.02x |
| 64 | 3584 | 5120 | 21.01 | 20.88 | 1.01x | 102.77 | 102.61 | 1.00x |
| 64 | 4608 | 7168 | 28.14 | 25.92 | 1.09x | 152.87 | 158.67 | 0.96x |
| 64 | 5120 | 640 | 7.41 | 6.82 | 1.09x | 27.22 | 29.89 | 0.91x |
| 64 | 5120 | 1024 | 9.55 | 7.68 | 1.24x | 37.41 | 35.33 | 1.06x |
| 64 | 5120 | 1280 | 9.50 | 8.98 | 1.06x | 43.71 | 46.82 | 0.93x |
| 64 | 5120 | 2048 | 15.18 | 11.20 | 1.36x | 58.35 | 59.60 | 0.98x |
| 64 | 5120 | 2560 | 18.18 | 13.33 | 1.36x | 68.53 | 71.06 | 0.96x |
| 64 | 5120 | 4096 | 20.35 | 20.18 | 1.01x | 104.83 | 107.23 | 0.98x |
| 64 | 5120 | 5120 | 23.62 | 21.65 | 1.09x | 125.73 | 127.04 | 0.99x |
| 64 | 5120 | 8192 | 33.65 | 31.90 | 1.05x | 175.30 | 177.41 | 0.99x |
| 64 | 5120 | 16384 | 51.46 | 50.45 | 1.02x | 283.51 | 338.10 | 0.84x |
| 64 | 7168 | 256 | 5.38 | 5.36 | 1.00x | 18.59 | 19.66 | 0.95x |
| 64 | 7168 | 512 | 7.02 | 6.74 | 1.04x | 33.78 | 29.65 | 1.14x |
| 64 | 7168 | 2304 | 14.21 | 14.08 | 1.01x | 106.10 | 90.93 | 1.17x |
| 64 | 7168 | 4608 | 24.83 | 24.83 | 1.00x | 163.09 | 155.30 | 1.05x |
| 64 | 7168 | 5120 | 27.68 | 27.50 | 1.01x | 161.51 | 161.57 | 1.00x |
| 64 | 8192 | 1024 | 10.62 | 8.80 | 1.21x | 54.75 | 52.88 | 1.04x |
| 64 | 8192 | 2048 | 13.57 | 12.86 | 1.05x | 88.58 | 88.56 | 1.00x |
| 64 | 8192 | 3584 | 19.84 | 19.15 | 1.04x | 134.35 | 154.62 | 0.87x |
| 64 | 8192 | 4096 | 21.76 | 21.49 | 1.01x | 143.79 | 154.64 | 0.93x |
| 64 | 8192 | 7168 | 40.48 | 37.44 | 1.08x | 217.87 | 223.06 | 0.98x |
| 64 | 8192 | 8192 | 42.66 | 42.58 | 1.00x | 235.81 | 243.09 | 0.97x |
| 64 | 8192 | 14336 | 65.49 | 65.01 | 1.01x | 369.62 | 361.91 | 1.02x |
| 64 | 8192 | 28672 | 108.33 | 113.45 | 0.95x | 667.00 | 664.82 | 1.00x
|
| 64 | 9216 | 7168 | 44.46 | 43.31 | 1.03x | 235.20 | 230.72 | 1.02x |
| 64 | 10240 | 8192 | 51.12 | 49.84 | 1.03x | 271.65 | 276.34 | 0.98x |
| 256 | 512 | 7168 | 20.96 | 20.90 | 1.00x | 49.90 | 50.00 | 1.00x |
| 256 | 896 | 1024 | 7.66 | 6.26 | 1.23x | 17.71 | 17.74 | 1.00x |
| 256 | 1024 | 7168 | 22.19 | 22.27 | 1.00x | 73.68 | 71.20 | 1.03x |
| 256 | 4608 | 7168 | 34.67 | 32.51 | 1.07x | 170.64 | 156.79 | 1.09x |
| 256 | 7168 | 256 | 5.49 | 5.52 | 0.99x | 38.90 | 39.28 | 0.99x |
| 256 | 7168 | 512 | 7.41 | 7.28 | 1.02x | 52.51 | 47.41 | 1.11x |
| 256 | 7168 | 2304 | 14.56 | 15.98 | 0.91x | 109.94 | 99.42 | 1.11x |
| 256 | 7168 | 4608 | 35.25 | 27.57 | 1.28x | 159.07 | 153.97 | 1.03x |
| 256 | 9216 | 7168 | 40.30 | 40.94 | 0.98x | 250.43 | 235.38 | 1.06x |
| 512 | 896 | 5120 | 18.94 | 18.90 | 1.00x | 61.30 | 53.65 | 1.14x |
| 512 | 1280 | 8192 | 23.07 | 22.99 | 1.00x | 91.09 | 92.77 | 0.98x |
| 512 | 1792 | 5120 | 22.64 | 22.83 | 0.99x | 97.03 | 87.98 | 1.10x |
| 512 | 2560 | 8192 | 34.77 | 29.50 | 1.18x | 143.19 | 138.42 | 1.03x |
| 512 | 3584 | 5120 | 32.75 | 24.94 | 1.31x | 136.55 | 129.43 | 1.06x |
| 512 | 5120 | 640 | 9.31 | 9.30 | 1.00x | 61.04 | 60.90 | 1.00x |
| 512 | 5120 | 1024 | 11.07 | 11.23 | 0.99x | 62.82 | 65.34 | 0.96x |
| 512 | 5120 | 1280 | 11.57 | 12.18 | 0.95x | 75.86 | 73.46 | 1.03x |
| 512 | 5120 | 2048 | 16.08 | 14.35 | 1.12x | 89.41 | 85.70 | 1.04x |
| 512 | 5120 | 2560 | 15.90 | 16.19 | 0.98x | 99.34 | 96.16 | 1.03x |
| 512 | 5120 | 4096 | 22.69 | 22.62 | 1.00x | 128.18 | 135.65 | 0.94x |
| 512 | 5120 | 5120 | 28.24 | 29.98 | 0.94x | 157.41 | 153.09 | 1.03x |
| 512 | 5120 | 8192 | 40.10 | 40.30 | 0.99x | 201.84 | 204.10 | 0.99x |
| 512 | 5120 | 16384 | 80.00 | 80.09 | 1.00x | 385.19 | 450.56 | 0.85x |
| 512 | 7168 | 5120 | 45.28 | 40.22 | 1.13x | 175.25 | 176.79 | 0.99x |
| 512 | 8192 | 1024 | 14.98 | 13.92 | 1.08x | 84.94 | 88.22 | 0.96x |
| 512 | 8192 | 2048 | 22.69 | 19.49 | 1.16x | 121.91 | 114.98 | 1.06x |
| 512 | 8192 | 3584 | 36.18 | 28.99 | 1.25x | 154.24 | 157.12 | 0.98x |
| 512 | 8192 | 4096 | 38.70 | 32.43 | 1.19x | 168.34 | 168.74 | 1.00x |
| 512 | 8192 | 7168 | 60.58 | 56.67 | 1.07x | 261.33 | 257.76 | 1.01x |
| 512 | 8192 | 8192 | 65.92 | 63.39 | 1.04x | 288.55 | 296.61 | 0.97x |
| 512 | 8192 | 14336 | 112.25 | 108.30 | 1.04x | 470.79 | 471.16 | 1.00x
|
| 512 | 8192 | 28672 | 212.93 | 202.01 | 1.05x | 980.86 | 1103.15 |
0.89x |
| 512 | 10240 | 8192 | 75.14 | 78.35 | 0.96x | 338.56 | 339.22 | 1.00x |
| 1024 | 512 | 7168 | 22.05 | 22.02 | 1.00x | 76.56 | 80.66 | 0.95x |
| 1024 | 896 | 1024 | 8.29 | 6.67 | 1.24x | 32.16 | 32.45 | 0.99x |
| 1024 | 1024 | 7168 | 25.74 | 23.15 | 1.11x | 104.77 | 106.29 | 0.99x |
| 1024 | 4608 | 7168 | 59.04 | 56.91 | 1.04x | 239.03 | 239.97 | 1.00x |
| 1024 | 7168 | 256 | 12.45 | 12.85 | 0.97x | 100.98 | 101.36 | 1.00x |
| 1024 | 7168 | 512 | 17.39 | 18.02 | 0.97x | 104.19 | 105.27 | 0.99x |
| 1024 | 7168 | 4608 | 67.54 | 69.47 | 0.97x | 249.79 | 251.81 | 0.99x |
| 1024 | 9216 | 7168 | 115.14 | 117.41 | 0.98x | 423.97 | 433.32 | 0.98x
|

**RTX 5090 (SM120) geomean: 1.04x** (147 shapes)
**DGX Spark (SM121) geomean: 1.01x** (147 shapes)

</details>


## 🔍 Related Issues

#3013

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

* **Optimizations**
* Optimized FP4 GEMM kernel execution by refining scheduler
configuration, epilogue fusion operations, and memory staging parameters
to improve performance and resource utilization.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3366
- **最后更新**: 2026-04-10T21:37:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33296
- **最后更新**: 2026-04-10T21:27:24Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Xyc2016, Sayak Paul, Akshan Krithick

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：修复了HunyuanVideo 1.5 I2V模型的图像预处理问题。
- **文档更新**：修正了LoRA文档中的语法错误。
- **测试优化**：加强了依赖测试的严格性。

### 2. 关键变更点及其与项目整体方向的关系
- **HunyuanVideo修复**：将图像预处理从潜在分辨率改为像素分辨率，确保模型输入符合预期。这符合项目支持多样化扩散模型（如视频生成）的方向，提升了特定模型的可用性。
- **LoRA文档修正**：微调文档细节（如复数形式和代词），提高文档可读性。这有助于项目维护高质量的文档，降低用户学习成本。
- **依赖测试加强**：通过更严格的测试确保依赖兼容性，减少因依赖问题导致的运行时错误。这强化了项目的稳定性和可靠性。

### 3. 对项目的影响和潜在意义
- **Bug修复**：直接解决了HunyuanVideo 1.5 I2V模型可能存在的生成错误，提升了该功能的可靠性。
- **文档更新**：虽是小改动，但有助于提升用户体验，减少理解歧义。
- **测试优化**：长期看能减少依赖冲突问题，提高代码库的健壮性，尤其对依赖复杂的扩散模型项目至关重要。

### 4. 值得关注的技术点
- **图像预处理策略**：从潜在分辨率切换到像素分辨率，可能涉及对模型输入管道的调整，反映了对模型底层处理逻辑的深入理解。
- **依赖测试强化**：可能引入了更严格的依赖版本检查或测试覆盖，有助于预防兼容性问题。

### 5. 基于项目背景的提交影响分析
- **项目背景**：Diffusers是一个专注于扩散模型（如图像、视频生成）的库，旨在提供易用、模块化且高性能的实现。
- **影响分析**：
  - **功能完善**：修复HunyuanVideo模型问题，直接支持了视频生成功能，符合项目扩展多模态生成能力的目标。
  - **质量提升**：文档和测试的改进虽不直接影响功能，但增强了项目的整体质量和可维护性，有助于吸引更多用户和贡献者。
  - **生态建设**：这些更新共同推动了项目向更稳定、用户友好的方向发展，巩固了其在扩散模型生态中的核心地位。

## 详细提交记录

### [87beae7](https://github.com/huggingface/diffusers/commit/87beae7771f8827c335d960db7abea2967efa848)

- **作者**: Akshan Krithick
- **时间**: 2026-04-10T19:54:36Z
- **提交信息**: Fix HunyuanVideo 1.5 I2V by preprocessing image at pixel resolution i… (#13440)

Fix HunyuanVideo 1.5 I2V by preprocessing image at pixel resolution instead of latent resolution

### [251676d](https://github.com/huggingface/diffusers/commit/251676dfda152c062ee1096cf90c2eace157df25)

- **作者**: Xyc2016
- **时间**: 2026-04-10T16:18:30Z
- **提交信息**: Fix grammar in LoRA documentation (#13423)

Fix grammar in LoRA documentation (LoRA's → LoRAs, trigger it → trigger them)

### [896fec3](https://github.com/huggingface/diffusers/commit/896fec351bc2f94564bd57296bb91d98fe989cbb)

- **作者**: Sayak Paul
- **时间**: 2026-04-10T12:42:12Z
- **提交信息**: [tests] tighten dependency testing. (#13332)

* tighten dependency testing.

* invoke dependency testing temporarily.

* f

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 392
- **最后更新**: 2026-04-09T13:58:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12212
- **最后更新**: 2026-04-10T12:02:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 25627
- **最后更新**: 2026-04-10T23:20:43Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 27
- **主要提交者**: ori, Qiaolin Yu, Bi Xue

## AI分析总结

根据 `sgl-project/sglang` 仓库的README摘要（这是一个专注于高效大语言模型推理和服务的项目）以及提供的昨日提交记录，以下是分析总结：

### 1. 主要更新类型
昨日提交以**性能优化**和**Bug修复**为主，同时包含**功能新增**、**CI/CD增强**和**文档更新**。
*   **性能优化 (9项)**：涉及内存、注意力机制、内核融合、调度策略等。
*   **Bug修复 (7项)**：修复了内存、服务器崩溃、输出重复、精度等问题。
*   **功能新增 (6项)**：增加了对新硬件（MUSA/GB200）、新模型（MiniMax-M2.5, Flux）、新算子（FA3, LoRA调优）等的支持。
*   **CI/CD与基础设施 (5项)**：新增了性能回归管道、工作流更新、权限配置等。
*   **文档更新 (1项)**：更新了用户指南。

### 2. 关键变更点及其与项目整体方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **支持新硬件与后端** (MUSA AI Tensor Engine, AMD HIP, Intel GPU, GB200) | 体现了项目**追求硬件兼容性与极致性能**的核心目标，旨在扩大部署范围和利用最新算力。 |
| **优化内存与计算效率** (减少MoE内存、预计算元数据、内核融合、移除冗余操作) | 直接服务于项目的**高效推理**宗旨，通过降低资源消耗和提升计算速度来优化服务成本与吞吐量。 |
| **增强模型与特性支持** (MiniMax-M2.5, Diffusion/Flux模型FP8支持， LoRA调优， HiCache CP支持) | 显示了项目**紧跟前沿模型与技术**（如MoE, 扩散模型， 参数高效微调），并致力于提供生产级的高效服务方案。 |
| **修复核心组件Bug** (注意力机制、推测解码、token处理、服务器崩溃) | 保障了**推理服务的稳定性与正确性**，这是任何生产系统的基础，尤其对于高并发、低延迟的SGLang服务至关重要。 |
| **完善可观测性与测试** (添加pending token计数， 新增whisper测试， 组件精度引导) | 提升了系统的**可维护性与可靠性**，有助于开发者监控、调试和保证服务质量，符合成熟框架的发展路径。 |

### 3. 对项目的影响和潜在意义
*   **正面影响**：
    *   **性能提升**：多项优化将直接降低推理延迟、提升吞吐量并减少GPU内存占用，改善用户体验和部署经济性。
    *   **生态扩展**：对新硬件、新模型和新特性（如扩散模型）的支持，吸引了更广泛的用户和开发者社区。
    *   **稳定性增强**：关键Bug的修复减少了生产环境中的潜在风险，提高了服务SLA。
    *   **开发体验改善**：CI/CD管道的完善和可观测性增强，使项目内部开发和外部贡献更加高效、可靠。
*   **潜在挑战**：
    *   **复杂度增加**：支持越来越多的硬件和模型变体可能增加代码维护和测试的复杂度。
    *   **兼容性风险**：快速集成新特性（如FA3、MATE后端）需注意与现有功能的兼容性和长期支持。

### 4. 值得关注的技术点
1.  **MUSA AI Tensor Engine (MATE)**：新增对国产MUSA计算平台及FA3注意力后端的支持，是硬件生态扩展的重要一步。
2.  **FP8与低精度计算**：在Diffusion模型（Flux）和MoE层中支持FP8，并优化BF16传递，显示了在降低显存和带宽消耗方面的持续深耕。
3.  **推测解码 (Speculative Decoding) 优化**：针对 `mamba_track_indices` 的性能改进，直接作用于提升解码速度这一关键瓶颈。
4.  **水平融合 (Horizontal Fusion) 与组合内核 (Combo Kernels)**：通过启用Inductor的组合内核进行水平融合，是编译器级深度优化，有望带来显著的性能收益。
5.  **HiCache 的 CP (Checkpoint) 支持**：可能意味着缓存机制变得更加健壮和可恢复，对长上下文或持续服务场景有益。

### 5. 基于项目背景的提交影响分析
SGLang 定位为“用于LLM推理的高效编排和执行引擎”，旨在**降低延迟、提升吞吐**。昨日的提交**高度契合这一目标**：
*   **强化核心优势**：绝大部分优化和修复都直接作用于推理管道的关键路径（注意力、内存管理、内核执行），巩固了其性能领先的定位。
*   **拓展应用边界**：通过支持**扩散模型**（Flux）和**多模态组件精度测试**，项目正从纯文本LLM推理向**多模态生成领域**谨慎拓展，这与AIGC发展趋势一致。
*   **构建生产就绪能力**：新增的**可观测性指标**（pending token计数）、**自动化的性能回归测试**（GB200 pipeline）和**每周CI时间预估更新**，表明项目正从“高性能原型”向“稳定、可运维的生产系统”演进。
*   **拥抱异构计算**：积极适配MUSA、AMD、Intel等多种硬件，反映出项目旨在成为**跨平台的高性能推理标准**的野心，避免被单一硬件生态绑定。

**总结**：昨日的更新是一次密集的、面向生产的迭代，核心是**夯实性能基础、修复

## 详细提交记录

### [b4a1d8f](https://github.com/sgl-project/sglang/commit/b4a1d8fd714d39ef11bec6fc444443254ed04b3f)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-10T23:20:33Z
- **提交信息**: [mem] Fix idle token_usage missing mamba_usage; add FIXME for naming (#22555)

### [0af9166](https://github.com/sgl-project/sglang/commit/0af91664747a7cd23d14e55e9319a3f99f7fed0d)

- **作者**: Alex Nails
- **时间**: 2026-04-10T22:46:12Z
- **提交信息**: [tokenizer] improve non streaming request processing + some small fixes. (#20310)

### [4513205](https://github.com/sgl-project/sglang/commit/451320596fda120458e4790bbf3b01969eea0365)

- **作者**: Sahithi Chigurupati
- **时间**: 2026-04-10T22:12:24Z
- **提交信息**: [CI] Add GB200 nightly perf regression pipeline (#22461)

### [3f39b3d](https://github.com/sgl-project/sglang/commit/3f39b3d811ecbdfa6a72cd8500277d1be8bb487c)

- **作者**: Cheng Wan
- **时间**: 2026-04-10T22:03:37Z
- **提交信息**: feat: add weekly workflow to update CI test est_time values (#22545)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [f7a1740](https://github.com/sgl-project/sglang/commit/f7a1740101273f5f171c1acd67a58918a1c85599)

- **作者**: ori
- **时间**: 2026-04-10T21:18:39Z
- **提交信息**: [MUSA][9/N] Add FA3 attention backend support through MATE (MUSA AI Tensor Engine) (#22051)

Co-authored-by: zhiguo.qin <zhiguo.qin@mthreads.com>

### [6af34b9](https://github.com/sgl-project/sglang/commit/6af34b95b6536d096bc768797c097dc68c432a9c)

- **作者**: Minglei Zhu
- **时间**: 2026-04-10T20:57:54Z
- **提交信息**: perf: precompute FA3 scheduler_metadata to eliminate per-layer prepare_varlen_num_blocks (#21104)

Co-authored-by: zminglei <zminglei@linkedin.com>

### [4ace144](https://github.com/sgl-project/sglang/commit/4ace144faef826b77a6809ec87f415a82ef1d35b)

- **作者**: Zhongdongming Dai
- **时间**: 2026-04-10T20:45:05Z
- **提交信息**: feat: update ModelExpress metadata API to SourceIdentity-based schema (#21222)

### [6d8330b](https://github.com/sgl-project/sglang/commit/6d8330bdb73fe38e30d2624495ad18ca6cb2360a)

- **作者**: satyamk7054
- **时间**: 2026-04-10T20:43:50Z
- **提交信息**: Update CI_PERMISSIONS.json (#22465)

Co-authored-by: Satyam Kumar <satyamk@linkedin.com>

### [6d95602](https://github.com/sgl-project/sglang/commit/6d95602ea3b1923baaa3a99545fed191d95e14ae)

- **作者**: Cheng Wan
- **时间**: 2026-04-10T20:23:23Z
- **提交信息**: Reduce GPU memory for MoE parallel groups (#22515)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [059b287](https://github.com/sgl-project/sglang/commit/059b287e25751c7e60431d589e884e7197d422a6)

- **作者**: satyamk7054
- **时间**: 2026-04-10T20:10:43Z
- **提交信息**: Add offline auto-tuning for LoRA CSGMV kernel (#20391)

Co-authored-by: Satyam Kumar <satyamk@linkedin.com>

### [d883135](https://github.com/sgl-project/sglang/commit/d8831355a3a54c9ac3fd85e8b05f384dd40629fb)

- **作者**: Qiaolin Yu
- **时间**: 2026-04-10T19:44:52Z
- **提交信息**: Fix multi_layer_eagle_worker_v2 draft extend selection, add chain style multi layer mtp test (#22340)

Co-authored-by: 0xNullPath <luyan@nvidia.com>

### [7dbd0dd](https://github.com/sgl-project/sglang/commit/7dbd0dd9f01a9a5f2c1009de175f9dbdc2b25604)

- **作者**: Trevor Morris
- **时间**: 2026-04-10T19:41:27Z
- **提交信息**: MiniMax-M2.5 - Support dp attention, dp reduce scatter, FP4 all gather, AR fusion in prepare_attn (#20067)

### [a937ec3](https://github.com/sgl-project/sglang/commit/a937ec31bed48c3418d983ddb70e5106cf376970)

- **作者**: KrishnanPrash
- **时间**: 2026-04-10T18:42:23Z
- **提交信息**: fix: server crash when stop_token_ids contains null (#22175)

Signed-off-by: Krishnan Prashanth <kprashanth@nvidia.com>

### [5cb4ea1](https://github.com/sgl-project/sglang/commit/5cb4ea1d4df55e06c0b033044367a203fca473a6)

- **作者**: Jia Guo
- **时间**: 2026-04-10T17:01:14Z
- **提交信息**: perf: enable inductor combo_kernels for horizontal fusion (#21977)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [2ba9413](https://github.com/sgl-project/sglang/commit/2ba94136ce21abaa069b93941fafc9beb842d290)

- **作者**: Tarushii Goel
- **时间**: 2026-04-10T16:39:53Z
- **提交信息**: [sgl] improve mamba_track_indices perf in specdec (#22380)

### [f652135](https://github.com/sgl-project/sglang/commit/f652135d5220cd8df36d5831f10597ed0c28e133)

- **作者**: Bi Xue
- **时间**: 2026-04-10T16:26:18Z
- **提交信息**: [sgl] fix using symmetric memory issues for attention_tp (#22286)

### [8227187](https://github.com/sgl-project/sglang/commit/8227187d472da41a9c56ab6a0d1ba11efc574dd5)

- **作者**: Ratish P
- **时间**: 2026-04-10T15:08:31Z
- **提交信息**: [SKILL]: add component accuracy guidance to the diffusion add-model skill (#22460)

### [cf5ad12](https://github.com/sgl-project/sglang/commit/cf5ad12612b01a88ed14e15191433232fdc60cfc)

- **作者**: Ratish P
- **时间**: 2026-04-10T15:06:03Z
- **提交信息**: [diffusion][CI]: route multimodal component accuracy through run_suite (#21960)

### [84194c2](https://github.com/sgl-project/sglang/commit/84194c25c1cd5f9d1242dbbf075759eacd27227d)

- **作者**: kingkingleeljj
- **时间**: 2026-04-10T14:21:19Z
- **提交信息**: [BugFix] fix the bug of minimax_m2.5 model that causes repeated outputs when using tp16 (#20967)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [1ff5155](https://github.com/sgl-project/sglang/commit/1ff51555f2bcfb4c474d43bc123cdd876ec33016)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-04-10T12:56:57Z
- **提交信息**: [Diffusion] modelopt diffusion fp8 support for flux1/flux2 and wan2.2 (#22365)

### [8ba9646](https://github.com/sgl-project/sglang/commit/8ba96460440c6f83ed523b33ed07b05e302ad690)

- **作者**: Yujun Dong
- **时间**: 2026-04-10T10:58:13Z
- **提交信息**: Make GDN support non-continuous B/A Tensor input to fix the accuracy regression of Qwen3.5-27B (#22312)

Signed-off-by: cs-cat <118669451+cs-cat@users.noreply.github.com>

### [0668a7f](https://github.com/sgl-project/sglang/commit/0668a7f51ac5b88dd8406a832941a3af64d4d2d3)

- **作者**: Jincong Chen
- **时间**: 2026-04-10T09:53:57Z
- **提交信息**: [Perf] Remove two operations in gdn_backend extend verify path (#22444)

### [1c76f32](https://github.com/sgl-project/sglang/commit/1c76f322df5c3ee5887ef1e979d760041ffab139)

- **作者**: Shangming Cai
- **时间**: 2026-04-10T09:52:51Z
- **提交信息**: [HiCache] Add CP support for HiCache (#20977)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [37107be](https://github.com/sgl-project/sglang/commit/37107bee6f46881b0d6bd6dbee7a24dfeacd64ea)

- **作者**: Cheng Wan
- **时间**: 2026-04-10T09:05:21Z
- **提交信息**: [Observability] Add pending token count to prefill log and get_load (#22480)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [c554dc5](https://github.com/sgl-project/sglang/commit/c554dc5c64b661f2c53225b03a76359eaddc39e4)

- **作者**: Lee Nau
- **时间**: 2026-04-10T08:35:56Z
- **提交信息**: Add dedicated FlashInferCuteDslMoE layer for standard-path FP4 MoE (#21339)

### [7c6b5c0](https://github.com/sgl-project/sglang/commit/7c6b5c095c9e32b3d76788cac4a3272fca6e7bab)

- **作者**: Mick
- **时间**: 2026-04-10T08:16:51Z
- **提交信息**: [diffusion] fix: fix flux2 i2i accuracy (#22423)

### [6cf7f21](https://github.com/sgl-project/sglang/commit/6cf7f210bfc85f975484b69a4901c6a29c689dd9)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-10T08:16:04Z
- **提交信息**: Add page_size to admission token budget check (#22495)

### [dd41764](https://github.com/sgl-project/sglang/commit/dd41764487447740cfe7e8141f62c627fd54ce09)

- **作者**: Jacob0226
- **时间**: 2026-04-10T08:08:32Z
- **提交信息**: [AMD][HIP] NSA: bf16 passthrough from RMSNorm to eliminate FP8 dequantization (#22258)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [f5fd5ab](https://github.com/sgl-project/sglang/commit/f5fd5ab62265be23db0a3f4584e5178382b2c937)

- **作者**: Yuhao Yang
- **时间**: 2026-04-10T07:34:53Z
- **提交信息**: add whisper test (#22302)

### [2ab1415](https://github.com/sgl-project/sglang/commit/2ab141547d5992f66a2323af4ab539ea9e78b0f6)

- **作者**: jianan-gu
- **时间**: 2026-04-10T07:16:05Z
- **提交信息**: [CPU] Add apply_routed_scaling_factor_on_output support for biased_grouped_topk fusion (#22413)

Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [599cce4](https://github.com/sgl-project/sglang/commit/599cce4d82383adc1cf250fb4e4fd792f19e68f0)

- **作者**: Polisetty V R K Jyothendra Varma
- **时间**: 2026-04-10T07:10:00Z
- **提交信息**: [Intel GPU] import flash_attn functions from sgl_kernel only (#22438)

### [5ba7d4e](https://github.com/sgl-project/sglang/commit/5ba7d4e523d56a20af5e83a2d7e2b8970be88c42)

- **作者**: Zhangheng
- **时间**: 2026-04-10T07:06:43Z
- **提交信息**: [HiSparse]: Update HiSparse's user-guide (#22499)

Co-authored-by: Zhiqiang Xie <xiezhq@stanford.edu>
Co-authored-by: 晟海 <huangtingwei.htw@antgroup.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache acceleration, parallelism and quantization for DiTs.
- **语言**: Python
- **星标数**: 1129
- **最后更新**: 2026-04-10T13:02:24Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据提供的提交记录和README摘要，以下是针对仓库 `vipshop/cache-dit` 昨日更新的分析总结：

### 1. 主要更新类型
- **重构**：本次提交（`d986fb0`）的核心是对分布式代码库进行了重构，属于代码结构优化。

### 2. 关键变更点及其与项目整体方向的关系
- **分布式代码库重构**：提交信息显示对分布式相关代码进行了重构，可能涉及模块化、代码清晰度或可维护性改进。
- **与项目方向的关系**：项目 `cache-dit` 是一个专注于 **Diffusion Transformers 推理优化** 的 PyTorch 原生引擎，强调 **缓存、并行化和量化**。分布式计算是并行化的关键组成部分，因此重构分布式代码库直接支持项目的 **高性能并行推理** 目标，有助于提升系统在分布式环境下的稳定性和扩展性。

### 3. 对项目的影响和潜在意义
- **积极影响**：
  - 提升代码可维护性和可读性，便于后续功能迭代。
  - 可能为未来分布式性能优化（如多GPU/多节点推理）奠定基础。
- **潜在意义**：重构可能隐含对现有分布式逻辑的改进，为支持更大规模模型或更高吞吐量的推理场景做准备。

### 4. 值得关注的技术点
- **分布式架构设计**：重构可能涉及 PyTorch 分布式通信（如 `torch.distributed`）的优化，值得关注是否引入了更高效的并行策略。
- **与缓存和量化的集成**：需关注重构后分布式代码如何与项目的核心特性（缓存、量化）协同工作，以确保端到端推理效率。

### 5. 基于项目背景的提交影响分析
- **项目背景**：`cache-dit` 旨在为 Diffusion Transformers 提供高效的推理引擎，重点优化速度与资源利用。
- **提交如何影响发展**：
  - **强化并行化能力**：分布式重构直接增强项目的 **并行化** 支柱，可能提升多设备推理性能，符合项目“高性能推理”的愿景。
  - **促进工程化成熟度**：代码重构通常意味着项目向更稳定、可扩展的生产环境迈进，有助于吸引企业级用户。
  - **为未来优化铺路**：更清晰的分布式代码结构可能为后续集成高级特性（如动态负载均衡、异构计算支持）提供便利。

### 总结
昨日更新是一次 **以重构为主的工程优化**，重点提升了分布式代码的质量。虽然未直接新增功能或修复漏洞，但通过改善代码基础，间接支持了项目的 **并行推理核心目标**，并为未来的性能扩展和稳定性提升奠定了基础。

## 详细提交记录

### [d986fb0](https://github.com/vipshop/cache-dit/commit/d986fb02bf9b06918d933747a679c0ceb8ac57ff)

- **作者**: DefTruth
- **时间**: 2026-04-10T13:02:17Z
- **提交信息**: bc: refactor distributed codebase (#971)

* bc: refactor distributed codebase

* bc: refactor distributed codebase

* bc: refactor distributed codebase

* bc: refactor distributed codebase

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 76041
- **最后更新**: 2026-04-10T22:47:03Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 25
- **主要提交者**: Jee Jee Li, Peter Nguyen, Harry Mellor

## AI分析总结

根据提供的提交记录和项目README摘要（vLLM：面向所有人的简单、快速、经济的LLM服务），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增 (7项)**：新增模型支持、新硬件支持、新配置选项。
- **Bug修复 (4项)**：修复关键运行时错误和逻辑缺陷。
- **性能优化 (4项)**：针对特定硬件和场景的优化。
- **代码/基础设施 (7项)**：包括重构、CI/CD测试、目录结构调整、编译优化等。
- **文档更新 (1项)**：安装指南的微小修正。
- **其他 (3项)**：如所有权文件更新、版本回退。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向（易用、快速、经济、普适）的关系 |
| :--- | :--- |
| **新增模型支持** (Gemma4 Eagle3, jina-reranker-v3, FireRedLID, Qwen3ASR LoRA) | **扩大生态兼容性**：支持更多前沿和专用模型，使框架对更广泛的用户和用例“易用”。 |
| **硬件生态扩展** (AMD ROCm新增设备ID、TritonW4A16LinearKernel、ZenCPU补丁) | **提升普适性与经济性**：加强对AMD硬件的支持，为用户提供更多低成本、高性能的硬件选择。 |
| **性能优化** (MOE调优、减少内存拷贝、移除冗余零填充、TRTLLM内核移植) | **强化“快速”核心优势**：针对混合专家模型、内存带宽、特定算子进行优化，直接提升推理速度和效率。 |
| **架构与可扩展性** (PluggableLayer应用、GGUF非标准量化支持、编译时优化) | **增强灵活性与可维护性**：模块化设计便于集成新组件，支持更多模型格式，降低长期维护成本，契合“服务于所有人”的目标。 |
| **Bug修复与稳定性** (修复FlashInfer崩溃、KV缓存NaN写入、预提交触发系统) | **保障服务可靠性**：修复底层内核和系统关键问题，是提供稳定、可投入生产服务的基石。 |
| **测试覆盖强化** (新增MultiConnector、Nixl+Offloading等e2e测试) | **提升交付质量**：针对复杂的多连接器和卸载场景增加测试，确保新功能在复杂环境下稳定，支撑项目快速迭代。 |

### 3. 对项目的影响和潜在意义
- **积极影响**：
    - **用户体验提升**：更多模型和硬件开箱即用，选择更自由。
    - **性能基准提高**：针对专业硬件（如Blackwell、AMD）和场景（MOE）的优化，巩固了其在高性能推理领域的竞争力。
    - **代码健康度与可扩展性增强**：重构（如MXFP8 GEMM管理）、模块化（PluggableLayer）和基础设施改进，为未来功能集成铺平道路。
    - **社区与厂商合作深化**：提交者来自Red Hat、AMD、Intel、腾讯、阿里等，显示其正成为业界广泛参与的核心基础设施。
- **潜在挑战**：
    - **复杂度增加**：支持更多硬件、模型和配置可能增加维护和测试负担。
    - **兼容性风险**：如AITER版本回退，表明在集成第三方依赖时需谨慎处理版本问题。

### 4. 值得关注的技术点
- **MXFP8 GEMM管理的重构** (`#39205`)：将特定数据类型的核心计算逻辑封装到独立内核，是代码解耦和性能优化的典型做法。
- **PluggableLayer的推进** (`#33465`)：将可插拔层应用到LLM头部和词表嵌入层，标志着向更彻底模块化架构迈出重要一步，有利于自定义优化。
- **针对特定硬件的极致优化**：如为**NVIDIA RTX PRO 6000 Blackwell** 调优MOE配置 (`#39183`)，体现了为高端硬件量身定制的性能挖掘。
- **GGUF量化格式的扩展支持** (`#39471`)：支持非标准量化类型前缀，增强了对多样化量化模型文件的兼容性，对部署压缩模型至关重要。
- **MultiConnector与Offloading测试** (`#39343`, `#39200`)：反映了项目对**异构计算**和**资源卸载**等高级部署场景的重视。

### 5. 基于项目背景的提交影响分析
vLLM的目标是成为**简单、快速、经济的LLM服务标准**。昨日的提交集体指向这一目标的多个维度：
- **“快速”与“经济”**：通过**性能优化**（MOE调优、内存拷贝减少）和**硬件生态扩展**（AMD、新NVIDIA卡），直接在速度和成本上创造价值。
- **“简单”与“面向所有人”**：通过**新增模型支持**（如Gemma4, Jina Reranker）和**修复易用性问题**（安装文档、崩溃Bug），降低了用户的使用门槛和适配工作量。
- **可持续发展**：通过**架构重构**、**增强测试**和**改善编译**，提升了代码库的健壮性和可维护性，确保项目在快速发展的AI生态中能持续集成创新。

**总结**：昨日的更新是一次全面的迭代，不仅通过新模型和新硬件支持**横向扩展**了项目边界，更通过底层优化、架构改进和稳定性修复**纵向深化**了其核心优势。这完全符合vLLM致力于成为高效、

## 详细提交记录

### [7f0b8f2](https://github.com/vllm-project/vllm/commit/7f0b8f20205c340f2a4eed88fcf8b8df40f011f2)

- **作者**: Michael Goin
- **时间**: 2026-04-10T22:27:02Z
- **提交信息**: [Docs] Use `--torch-backend=auto` for editable install docs (#39511)

Signed-off-by: Michael Goin <mgoin64@gmail.com>

### [11e2375](https://github.com/vllm-project/vllm/commit/11e2375fe28d2a39fecd80125bc65eab5aa30d75)

- **作者**: Michael Goin
- **时间**: 2026-04-10T21:02:03Z
- **提交信息**: [Refactor] Move MXFP8 GEMM management into MxFp8LinearKernel (#39205)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [fc645f1](https://github.com/vllm-project/vllm/commit/fc645f1acc0f3250210738a026f812db37ae97f6)

- **作者**: Harry Mellor
- **时间**: 2026-04-10T20:46:41Z
- **提交信息**: Add structure to `requirements/` directory (#39024)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [2d80cf9](https://github.com/vllm-project/vllm/commit/2d80cf9d6ede128f1dd70ced97d3780b7ce61db8)

- **作者**: Fynn Schmitt-Ulms
- **时间**: 2026-04-10T19:54:49Z
- **提交信息**: Fix pre-commit labeled trigger system (#39523)

Signed-off-by: Fynn Schmitt-Ulms <fschmitt@redhat.com>

### [e7cfd7c](https://github.com/vllm-project/vllm/commit/e7cfd7c5b9a18c4fb6eb7dd3108002793989e0eb)

- **作者**: Fynn Schmitt-Ulms
- **时间**: 2026-04-10T19:35:35Z
- **提交信息**: Add Gemma4 Eagle3 support (#39450)

Signed-off-by: Rahul-Tuli <rtuli@redhat.com>
Signed-off-by: Fynn Schmitt-Ulms <fschmitt@redhat.com>
Co-authored-by: Rahul-Tuli <rtuli@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e816a88](https://github.com/vllm-project/vllm/commit/e816a8811f2fbe9a8fa7f5d5f37a25cd410805d8)

- **作者**: yzong-rh
- **时间**: 2026-04-10T18:50:47Z
- **提交信息**: [Bugfix] Fix FlashInfer crash with kv_cache_dtype_skip_layers (#39002)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [e281cb7](https://github.com/vllm-project/vllm/commit/e281cb721ca21f39afff53b02f59ddedb3977172)

- **作者**: zhanqiuhu
- **时间**: 2026-04-10T17:35:03Z
- **提交信息**: [CI] Add MultiConnector (Nixl+Offloading) e2e edge case tests (#39343)

Signed-off-by: ZhanqiuHu <zhu@redhat.com>

### [51cfc0e](https://github.com/vllm-project/vllm/commit/51cfc0e76c8dbd2c2875092a60747db835a02aaf)

- **作者**: Manu
- **时间**: 2026-04-10T17:32:42Z
- **提交信息**: perf(moe): add tuned fused_moe config for RTX PRO 6000 Blackwell Server Edition (#39183)

Signed-off-by: manu <fortin.emmanuel@gmail.com>

### [b87575d](https://github.com/vllm-project/vllm/commit/b87575d24b752ee2afffaec00bfb244570d5c95a)

- **作者**: Jesus Federico
- **时间**: 2026-04-10T17:21:14Z
- **提交信息**: feat: add logit_scale to PoolerConfig for affine score calibration (#39435)

Signed-off-by: Jesus Federico <jefp@amazon.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [42c6bb4](https://github.com/vllm-project/vllm/commit/42c6bb4b7510995b46cf991c2e48cc4322d08b92)

- **作者**: TJian
- **时间**: 2026-04-10T16:25:52Z
- **提交信息**: [ROCm] [AITER] Revert AITER version to v0.1.10.post3 (#39509)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [ecd1ea1](https://github.com/vllm-project/vllm/commit/ecd1ea13634e6f9f6048dc8aecb94ce64a06b69e)

- **作者**: Jee Jee Li
- **时间**: 2026-04-10T16:20:20Z
- **提交信息**: [Kernel] Porting the TRTLLM minimax_allreduce_rms kernels (#37045)

Signed-off-by: Jee Jee Li <pandaleefree@gmail.com>

### [8f121f7](https://github.com/vllm-project/vllm/commit/8f121f7879669b5b6aced90f3d47a518ffd7f95d)

- **作者**: zhrrr
- **时间**: 2026-04-10T15:27:15Z
- **提交信息**: [Model Runner V2] support auto resolve cudagraph mode/sizes based on attn backend (#32936)

Signed-off-by: zhuhaoran <zhuhaoran.zhr@alibaba-inc.com>

### [cb5f750](https://github.com/vllm-project/vllm/commit/cb5f7501cbc80a394afbce0c877593be8cf6175c)

- **作者**: wang.yuqi
- **时间**: 2026-04-10T15:20:40Z
- **提交信息**: [New Model]: jinaai/jina-reranker-v3 (#38800)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [8d0f908](https://github.com/vllm-project/vllm/commit/8d0f908b98cd692204753421dd39695f3094c8f0)

- **作者**: Peter Nguyen
- **时间**: 2026-04-10T14:34:31Z
- **提交信息**: [Model] Implement LoRA support for Qwen3ASRForConditionalGeneration (#37247)

Signed-off-by: Peter Nguyen <petern0408@gmail.com>

### [c9dddc1](https://github.com/vllm-project/vllm/commit/c9dddc144b01bbbb3ee70f529575aeda95ed1778)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-04-10T13:40:40Z
- **提交信息**: [CI] Add Nixl+OffloadingConnector e2e integration tests (#39200)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [c1cc734](https://github.com/vllm-project/vllm/commit/c1cc7344fb720547051bb44a2e102278ae9b7a6a)

- **作者**: Ravitez Dondeti
- **时间**: 2026-04-10T11:35:07Z
- **提交信息**: [ROCm] Add RDNA 3.5/4 device IDs (gfx1150, gfx1151, gfx1201) (#38455)

Signed-off-by: rdondeti <ravitez.dondeti@gmail.com>
Signed-off-by: Ravitez Dondeti <ravitez.dondeti@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f976e3b](https://github.com/vllm-project/vllm/commit/f976e3b98ba45677a2213673a442c6cbff141e8e)

- **作者**: xaguilar-amd
- **时间**: 2026-04-10T11:27:35Z
- **提交信息**: [Performance] Remove unnecessary zero-fill of MLA decode output tensor in Aiter backend (#37539)

Signed-off-by: xaguilar-amd <xaguilar@amd.com>

### [d468322](https://github.com/vllm-project/vllm/commit/d468322dc1c89377f65488973d2f1927e9bbe5cb)

- **作者**: jatseng-ai
- **时间**: 2026-04-10T10:25:27Z
- **提交信息**: [Kernel][Hardware][AMD] Add TritonW4A16LinearKernel for ROCm (#37352)

Signed-off-by: jatseng-ai <jatseng@amd.com>
Signed-off-by: jatseng-ai <janet.tseng@amd.com>
Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Matthias Gehre <matthias.gehre@amd.com>

### [967146e](https://github.com/vllm-project/vllm/commit/967146e7bdfb0cc3cb16fb5cc547bff9667ae0a2)

- **作者**: PatchyTIS
- **时间**: 2026-04-10T08:43:58Z
- **提交信息**: [model] support FireRedLID (#39290)

Signed-off-by: PatchouliTaisa <patchychen@tencent.com>
Co-authored-by: PatchouliTaisa <patchychen@tencent.com>

### [8e8a3be](https://github.com/vllm-project/vllm/commit/8e8a3becd1e499a539bf1b9b0e4d135b82228727)

- **作者**: Lalithnarayan C
- **时间**: 2026-04-10T08:29:35Z
- **提交信息**: [ZenCPU] Make PT Backport Patch Accessible to vLLM (#38205)

Signed-off-by: Lalithnarayan C <Lalithnarayan.C@amd.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Luka Govedič <ProExpertProg@users.noreply.github.com>

### [1dfd64c](https://github.com/vllm-project/vllm/commit/1dfd64c1cccb02c022f703628898094f02a7da3f)

- **作者**: Hexiang Wang
- **时间**: 2026-04-10T08:12:59Z
- **提交信息**: [PluggableLayer][3/N] Apply PluggableLayer to llm_head and vocab embedding layer (#33465)

Signed-off-by: whx-sjtu <2952154980@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [ad720ae](https://github.com/vllm-project/vllm/commit/ad720aefe909e5a49629944fc45c09f5ee31d857)

- **作者**: Elvir Crnčević
- **时间**: 2026-04-10T08:09:46Z
- **提交信息**: [Bugfix] Fix V1 dummy run writing NaN to KV cache null block (#39444)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>
Co-authored-by: Claude Sonnet 4 <noreply@anthropic.com>

### [270e8a4](https://github.com/vllm-project/vllm/commit/270e8a41025436c86de96b76317a0029b30416c9)

- **作者**: milesial
- **时间**: 2026-04-10T07:31:19Z
- **提交信息**: Nemotron Nano VL: Streamline pixel shuffle (#37580)

Signed-off-by: milesial <milesial@users.noreply.github.com>

### [f44afef](https://github.com/vllm-project/vllm/commit/f44afef6d61faa40be65c14800307f42fa64ca55)

- **作者**: Richard Zou
- **时间**: 2026-04-10T07:26:37Z
- **提交信息**: [compile] Allow strings in custom ops without regressing compilation times (#38123)

Signed-off-by: Richard Zou <zou3519@gmail.com>

### [447ce22](https://github.com/vllm-project/vllm/commit/447ce22212e55e145a324488f076cb4e28e7d3e8)

- **作者**: Injae Ryou
- **时间**: 2026-04-10T07:22:53Z
- **提交信息**: [GGUF] Support non-standard quant types with prefix (e.g. UD-IQ1_S) (#39471)

Signed-off-by: Injae Ryou <injaeryou@gmail.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [65e4e46](https://github.com/vllm-project/vllm/commit/65e4e46f6662dce90f9cbc874bc2fd68c7fe9332)

- **作者**: Chendi.Xue
- **时间**: 2026-04-10T07:05:31Z
- **提交信息**: update CODEOWNERS file (#39439)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [49d2034](https://github.com/vllm-project/vllm/commit/49d20346e411099a09acd55031b4f1a507bad99c)

- **作者**: Chaofan Wang
- **时间**: 2026-04-10T07:03:26Z
- **提交信息**: [Perf] Reduce H2D pageable memory copies (#38794)

Signed-off-by: jackcfwang <jackcfwang@tencent.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-04-11
**监控日期**: 2026-04-10
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4212
- **最后更新**: 2026-04-10T21:11:37Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Jinheng, bjf-frz, fan2956

## AI分析总结

根据 `vllm-project/vllm-omni` 仓库的 README 摘要（“Easy, fast, and cheap omni-modality model serving for everyone”）可知，该项目旨在为**多模态模型**提供统一、高效、经济的推理服务框架。昨日的提交记录体现了项目在**稳定性、性能优化和工具链完善**方面的持续迭代。

以下是具体分析总结：

### 1. 主要更新类型
- **重构 (Refactor)**：1 项（移除 `librosa` 依赖）
- **Bug 修复 (Bugfix)**：3 项（扩散模型视频分析、MindIeSD 注意力机制、配置清理）
- **功能/工具新增**：1 项（添加 Nsight Systems 性能分析支持）
- **CI/CD 流程更新**：1 项（优化流水线合并条件）

### 2. 关键变更点及其与项目整体方向的关系
| 提交 | 关键变更点 | 与项目方向的关系 |
|------|-----------|----------------|
| **移除 librosa 依赖** | 减少音频处理库的强制依赖，可能转向更轻量或统一的音频处理方案。 | 符合“**Easy**”和“**cheap**”目标，降低部署复杂度和依赖冲突风险，提升框架的轻量化与灵活性。 |
| **清理扩散模型配置** | 从扩散阶段的配置中移除仅适用于纯文本 LLM 的引擎参数。 | 体现“**omni-modality**”特性，确保多模态（如图像/视频生成）配置的纯净性与正确性，避免参数误用。 |
| **添加 Nsight Systems 支持** | 集成英伟达性能分析工具，支持服务端性能剖析。 | 强化“**fast**”目标，为性能调优提供专业工具支持，有助于优化多模态服务的推理延迟与吞吐量。 |
| **修复扩散模型视频分析 Bug** | 修正扩散管道在视频生成任务中的性能分析结果输出。 | 提升多模态（视频生成）服务的**稳定性与可观测性**，确保性能监控准确。 |
| **修复 MindIeSD 注意力错误** | 解决特定模型（MindIeSD）中激光注意力（LaserAttention）不支持的问题。 | 扩展对**异构模型架构**的兼容性，支持更广泛的模型部署，符合“for everyone”的包容性目标。 |
| **优化 CI 合并条件** | 在非主分支的流水线脚本中增加 `merge-test` 标签作为合并条件。 | 提升**开发协作效率**，使测试流程更灵活，加速功能集成与验证。 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：多项 Bug 修复直接增强了扩散模型视频生成、特定模型支持的可靠性，减少运行时错误。
- **性能优化基础**：引入 Nsight Systems 支持为深度性能调优铺平道路，有助于长期提升服务效率。
- **依赖与配置净化**：移除冗余依赖和无效配置，降低维护成本，提升部署体验。
- **协作流程改进**：CI 条件优化有助于团队更高效地进行代码集成与测试。

### 4. 值得关注的技术点
- **Nsight Systems 集成**：表明项目开始重视**生产级性能剖析**，可能针对 GPU 利用率、内核执行等进行深度优化。
- **多模态配置隔离**：清理 LLM-only 参数从扩散配置中移除，反映项目在架构上**严格区分不同模态的推理路径**，避免技术债务。
- **注意力机制兼容性修复**：针对 MindIeSD 的 LaserAttention 修复，显示项目正在处理**新兴或定制化模型架构**的集成挑战。

### 5. 基于项目背景的提交影响分析
- **整体发展**：这些提交共同推动项目向 **“稳定、高效、易用的多模态服务平台”** 迈进：
  - **功能新增**（Nsight 支持）和 **Bug 修复** 直接提升服务**性能与可靠性**，支撑核心目标。
  - **重构与配置清理** 减少技术负担，使项目更**易于维护与扩展**。
  - **CI 优化** 加速迭代流程，促进社区或团队协作。
- **多模态服务强化**：针对扩散模型（图像/视频）和特定模型（MindIeSD）的修复，体现了项目在**视觉模态**和**模型兼容性**上的持续投入，巩固其作为“omni-modality”服务框架的定位。

**总结**：昨日更新以**Bug 修复和工具链增强**为主，显著提升了框架的稳定性、性能可观测性和开发体验，与项目“为所有人提供简单、快速、经济的多模态模型服务”的愿景高度一致。

## 详细提交记录

### [2bc183f](https://github.com/vllm-project/vllm-omni/commit/2bc183f6f0e91f43aa7e74040c47fdac4a6b1f59)

- **作者**: Nick Cao
- **时间**: 2026-04-10T18:11:31Z
- **提交信息**: [Refactor] Remove dependency on librosa (#2273)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [687405c](https://github.com/vllm-project/vllm-omni/commit/687405c5f2c12068701da4d3b7a12e1a6521b85b)

- **作者**: Yiyang "Ian" Liu
- **时间**: 2026-04-10T13:36:29Z
- **提交信息**: [Config] Remove invalid LLM-only engine_args from diffusion stage configs (#2622)

Signed-off-by: Yiyang Liu <yiyangliu@microsoft.com>
Co-authored-by: Yiyang Liu <yiyangliu@microsoft.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [78bef62](https://github.com/vllm-project/vllm-omni/commit/78bef62f8260fc9be6ec25de819bdbce9826f7e9)

- **作者**: Jinheng
- **时间**: 2026-04-10T10:13:12Z
- **提交信息**: [Profiler] Add Nsight Systems support for serving (#1098)

Signed-off-by: Jinheng Li <ahengljh@gmail.com>
Signed-off-by: Canlin Guo <961750412@qq.com>
Co-authored-by: Claude Opus 4.5 <noreply@anthropic.com>
Co-authored-by: Canlin Guo <961750412@qq.com>

### [fbb5dd5](https://github.com/vllm-project/vllm-omni/commit/fbb5dd57949085c8353ca4d5ffefbc0e73d32c25)

- **作者**: bjf-frz
- **时间**: 2026-04-10T08:48:06Z
- **提交信息**: [Bugfix]: modify diffusion pipeline profiler result in videos (#2647)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [c2ae58b](https://github.com/vllm-project/vllm-omni/commit/c2ae58bb84ce56d55f2d9ce3fb62af1fd6519362)

- **作者**: fan2956
- **时间**: 2026-04-10T08:18:27Z
- **提交信息**: [Bugfix] fix mindiesd laserattention unsupported error (#2673)

Signed-off-by: fan2956 <zhoufan53@huawei.com>

### [c1da480](https://github.com/vllm-project/vllm-omni/commit/c1da480bbf3d82a812a27c842e3b675aa7024788)

- **作者**: wangyu
- **时间**: 2026-04-10T07:03:25Z
- **提交信息**: [CI] Update merge condition in upload_pipeline_with_skip_ci.sh to include 'merge-test' label for non-main branches (#2667)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
