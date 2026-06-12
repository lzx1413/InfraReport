# GitHub Stars 合并报告 - 2026-06-12

**合并日期**: 2026-06-13
**监控日期**: 2026-06-12
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


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2013
- **最后更新**: 2026-06-12T15:55:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2377
- **最后更新**: 2026-06-12T23:16:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2125
- **最后更新**: 2026-06-12T05:46:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5783
- **最后更新**: 2026-06-12T20:45:39Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 4
- **主要提交者**: yifeis-nv, Guangyun Han, Lain

## AI分析总结

好的，作为专业的代码分析助手，以下是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增 (Feat):** 3项
- **Bug修复 (Fix):** 1项
- **重构/清理 (Chore):** 1项
- **性能优化/基准测试改进 (Perf/Bench):** 1项

### 2. 关键变更点及其与项目方向的关系

- **`[b87c54c]` 新增 MoE 的 MXFP8 量化支持:**
    - **变更点:** 在 `moe_a2a_combine` 内核中增加了直接输出 MXFP8 (Microscaling FP8) 格式的功能，并引入了 `output_dtype`, `output_scales`, `sf_layout` 等新API参数。
    - **与项目方向的关系:** 直接契合项目“为推理提供高性能GPU内核”的核心目标。MXFP8是一种新兴的低精度量化格式，能有效降低显存占用和带宽需求，同时保持模型精度。此更新使FlashInfer在支持最新、最高效的推理技术方面迈出重要一步。

- **`[ddee003]` 清理遗留的 C++ 源码:**
    - **变更点:** 移除了之前被更优的 `cutedsl` 实现所取代的“Gated Delta Rule”的旧版 C++ 内核源码。
    - **与项目方向的关系:** 这是代码库健康度的体现。通过清理冗余代码，降低了维护成本，减少了潜在的混淆，使项目更专注于其核心的、高性能的实现路径（如 `cutedsl`）。

- **`[992848a]` 引入 cuTile 后端:**
    - **变更点:** 为 `mm_bf16`, `bmm_bf16`, `gemm_fp8_nt_groupwise` 三个核心矩阵运算引入了全新的 `cuTile` 后端。该后端基于 NVIDIA 的 `cuda.tile` 公共API，不依赖 TileGym 运行时。
    - **与项目方向的关系:** 这是对项目技术栈的重大扩展。`cuTile` 后端在特定场景下（如小规模矩阵乘法 `mm_bf16`）展现出超越 cuDNN 和 tinygemm 的性能。这体现了项目在探索多种高性能实现路径上的前瞻性，旨在为用户提供更多、更优的底层计算选择，以应对不同的硬件和计算场景。

- **`[2461b2e]` 修复零长度序列的 Delta Rule 问题:**
    - **变更点:** 修复了 Gated Delta Net 内核在处理空序列或零长度序列时的潜在未定义行为。
    - **与项目方向的关系:** 这是一个重要的鲁棒性修复。在实际推理场景中，处理变长序列是常态，零长度序列是边界情况。此修复确保了内核在各种输入下的稳定性和正确性，是项目走向成熟、可靠的关键一步。

- **`[d65c3eb]` 改进 Gated Delta Rule 基准测试脚本:**
    - **变更点:** 增加了长单序列和大批量等更多测试用例，并引入了 CUDA Graph、冷却时间、旋转缓冲区等机制，以获取更准确、更全面的性能数据。
    - **与项目方向的关系:** 基准测试是衡量和驱动性能优化的基石。改进基准测试脚本，使其更贴近真实负载、更科学，有助于开发者更精确地定位瓶颈、验证优化效果，从而持续推动项目性能的边界。

- **`[ac554d5]` 修复 SM100 GDN Prefill 挂起问题:**
    - **变更点:** 修复了在 Blackwell (SM100) 架构上，由于GPU流水线生命周期管理错误导致的 Gated Delta Net Prefill 内核挂起问题。
    - **与项目方向的关系:** 这是一个关键的硬件兼容性修复。确保项目能在最新的NVIDIA GPU架构（如Blackwell）上稳定运行，是项目保持其“高性能”和“前沿性”标签的必要条件。此修复直接解决了用户在新硬件上可能遇到的严重问题。

### 3. 对项目的影响和潜在意义

- **性能与效率提升:** MXFP8 和 cuTile 后端的引入，为模型推理提供了新的性能优化路径，尤其是在显存带宽受限和特定计算形状的场景下。
- **稳定性与可靠性增强:** 修复零长度序列和SM100挂起问题，显著提升了项目在复杂、边界情况下的鲁棒性，增强了用户信心。
- **技术栈多元化:** cuTile 后端的加入，表明FlashInfer不局限于单一技术路线（如CUTLASS），而是积极拥抱社区和NVIDIA官方提供的新工具，以保持技术领先性。
- **代码库健康度:** 清理旧代码和优化基准测试，是项目长期健康发展的良好实践，有助于降低未来开发和维护的复杂度。

### 4. 值得关注的技术点

- **MXFP8 量化:** 这是一种比标准FP8更精细的量化方案，通过“共享指数”来提升精度。其在MoE场景中的应用，是低精度推理领域的前沿探索。
- **cuTile 后端:** 这是NVIDIA推出的一个较新的、基于Python的CUDA内核编写API。FlashInfer将其集成，展示了如何利用高级抽象来编写高性能内核，并可能降低未来内核开发的门槛。
- **`cutedsl` 与 `cuTile` 的对比:** 项目同时使用了CUTLASS DSL和cuTile两种方式实现内核，这

## 详细提交记录

### [b87c54c](https://github.com/flashinfer-ai/flashinfer/commit/b87c54ce80c23dbd2a7704d33c2027d34a2c6a0a)

- **作者**: Lain
- **时间**: 2026-06-12T20:45:25Z
- **提交信息**: feat: add mxfp8 quant to moe a2a combine (#3376)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR aims to allow `moe_a2a_combine` to directly output mxfp8
results.

Additionally, the `kMaxPayloads` is increased to be compatible with
per-token quantization dispatch.

**API changes**

- In `moe_a2a_combine`, added `output_dtype`, `output_scales`, and
`sf_layout`

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

* **New Features**
* MXFP8-quantized output for MOE all-to-all combine with optional
per-vector scale emission and selectable swizzle/layout; supports
FP16/BF16 payloads when using MXFP8.
* Combine API extended to accept optional output dtype, output scales,
and swizzle/layout parameters.
  * Increased supported payload capacity.

* **Tests**
* Added tests validating MXFP8 combine behavior, per-rank scale
emission, and larger-payload dispatch scenarios.

* **Chores**
* Enabled BF16-related build flag and relaxed GPU architecture guard for
wider hardware support.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Siyuan Fu <siyuanf@nvidia.com>
Signed-off-by: root <siyuanf@nvidia.com>

### [ddee003](https://github.com/flashinfer-ai/flashinfer/commit/ddee0033ec9991544a51992589eee343f48126e5)

- **作者**: Guangyun Han
- **时间**: 2026-06-12T16:42:23Z
- **提交信息**: chore: remove leftover cpp srcs from #3477 (#3613)

## 📌 Description

Remove gated delta rule C++ implementation source. In favor cutedsl
implementation added in #3477.


### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

## Release Notes

* **Removals**
* Removed GDN prefill kernel support and associated SM90A optimizations
  * Removed delta rule prefill kernel implementation
* Removed infrastructure components and utilities supporting the above
features

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [992848a](https://github.com/flashinfer-ai/flashinfer/commit/992848ad3d0e21650f2d6cd2e03becae187cf743)

- **作者**: yifeis-nv
- **时间**: 2026-06-12T15:50:35Z
- **提交信息**: feat(cutile): introduce cuTile backend (mm_bf16 + bmm_bf16 + gemm_fp8_nt_groupwise) (#3426)

Adds **cuTile** (CUDA Tile Python) backend support for three GEMM
operations in FlashInfer, porting kernels from NVIDIA TileGym to use the
public `cuda.tile` API without TileGym runtime dependencies:

- `mm_bf16(backend="cutile")`
- `bmm_bf16(backend="cutile")`
- `gemm_fp8_nt_groupwise(backend="cutile")` — K-major scale only

Performance:


All measurements: CUDA event timing, warmup=20, repeats=50, median
latency. Cosine similarity = 1.000 on all shapes.

### `mm_bf16` — H100 NVL (sm_90)

| Shape (M×N×K) | cuDNN (µs) | tinygemm (µs) | **cuTile (µs)** | vs
cuDNN | vs tinygemm |
|---|---|---|---|---|---|
| 64×2048×2048 | 99.71 | 66.30 | **58.88** | +1.69× | +1.13× |
| 128×4096×4096 | 98.94 | 120.35 | **58.82** | +1.68× | +2.04× |

> Geomean: **1.69× vs cuDNN**, **1.52× vs tinygemm**  
> tgv not supported on sm_90 (skipped). Larger shapes (K=11008, M≥512)
hit memory limits on this node.

### `gemm_fp8_nt_groupwise` K-major — B300 SXM6 AC (sm_103)

| Shape (M×N×K) | cutlass (µs / TFLOPS) | **cuTile (µs / TFLOPS)** |
cuTile / cutlass |
|---|---|---|---|
| 256×1024×1024 | 60.64 / 8.85 | **64.29 / 8.35** | 1.06× (≈ tied) |
| 1024×4096×4096 | 68.10 / 504.6 | **71.33 / 481.7** | 1.05× (≈ tied) |
| 2048×4096×4096 | 69.06 / 995.1 | **88.54 / 776.1** | 1.28× slower |
| 4096×4096×4096 | 78.50 / 1750.9 | **173.06 / 794.2** | 2.20× slower |

> cuTile is within ~5% of cutlass for M ≤ 1024. Performance gap widens
at larger M — autotune config investigation ongoing.

## Build system note: PEP 517 isolation

`build_backend.py` installs the `cuda-tile` compile chain (nvcc,
tileiras, nvvm…)
with `--no-deps` to avoid pulling in `nvidia-cuda-runtime-cu13`, which
conflicts
with torch's `nvidia-cuda-runtime-cu12` (both expose `libcudart.so` at
different
major versions, breaking cudnn at import time).

When `pip install` runs **without `--no-build-isolation`** (the
default), pip
creates a clean PEP 517 build environment that contains only the
declared build
dependencies such as `setuptools` and `packaging` — it does **not**
include `pip`
itself or `uv`. As a result, we cannot invoke `pip install` from within
that
environment to resolve this conflict. The function therefore falls back
to a
warn-and-continue approach: the compile chain is pre-installed on CI
images, and
a clean PyPI install will surface a clear `ImportError` at first cuTile
use rather
than aborting the build.

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [2461b2e](https://github.com/flashinfer-ai/flashinfer/commit/2461b2e09b26eeba7349daa21d728846b4c7d3ad)

- **作者**: Guangyun Han
- **时间**: 2026-06-12T14:35:45Z
- **提交信息**: feat: delta rule work with zero length sequence (#3536)

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

* **Bug Fixes**
* Fixed kernel handling of empty or zero-length sequences to prevent
undefined behavior and ensure correct state management.

* **Tests**
* Added test coverage for zero-length sequence scenarios in the Gated
Delta Net kernel.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d65c3eb](https://github.com/flashinfer-ai/flashinfer/commit/d65c3ebe37e400af0f8b453b9f195893ac30dbc5)

- **作者**: Guangyun Han
- **时间**: 2026-06-12T12:02:08Z
- **提交信息**: feat: improve gated delta rule benchmark script (#3616)

## 📌 Description

1. Add more benchmark cases, long single seq and large batch are now
covered.
2. Use cuda graph because cutedsl and fla both have large launch
overhead.
3. Add cooling time due internal machine overheat.
4. Use rotation buffer to avoid L2 caching effect.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

## Benchmark Improvements

* **Chores**
* Enhanced the benchmark harness with improved timing and memory
management capabilities.
* Added new command-line options including cooling time intervals, CUPTI
profiling, and CUDA graph support.
* Updated benchmark configurations targeting larger sequence lengths and
new performance patterns.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ac554d5](https://github.com/flashinfer-ai/flashinfer/commit/ac554d5a2f71de77d8ca28e271829f808c190849)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-06-12T07:37:41Z
- **提交信息**: [fix] Fix SM100 GDN prefill hang (#3581)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix https://github.com/flashinfer-ai/flashinfer/issues/3565 
Root cause:
`o_store_producer` is owned by the CG1 -> epilogue pipeline. CG0 never
acquires or commits this pipeline, so tailing it from CG0 can corrupt
pipeline lifetime state and trigger a hang.
The bug was shown on CUTLASS DSL 4.5.2. 

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

## Release Notes

* **Refactor**
  * Optimized GPU kernel computation sequence for improved efficiency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3703
- **最后更新**: 2026-06-12T13:26:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33837
- **最后更新**: 2026-06-12T21:25:26Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: YiYi Xu

## AI分析总结

好的，这是对 `huggingface/diffusers` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **文档更新**：更新了贡献指南（README）和Pull Request (PR) 模板。
*   **流程/工具优化**：为AI编码代理（AI Agent）引入了新的工作流和自检（Self-Review）机制。
*   **重构**：移除了一个实验性的 `parity-testing` 技能，并将其中的有用部分整合到其他文档中。

### 2. 关键变更点及其与项目整体方向的关系

*   **变更点1：为AI Agent贡献者优化流程**
    *   **内容**：在README和PR模板中，明确引导AI Agent（如Claude、Codex）使用项目预设的 `.ai/` 目录下的约定和 `make claude`/`make codex` 命令。PR模板新增了“是否使用了AI Agent？”的复选框，并要求其遵循项目规范。
    *   **与项目方向的关系**：`diffusers` 是一个社区驱动的、快速迭代的项目，AI Agent已成为代码贡献的主要方式之一。此变更旨在**标准化和规范化AI Agent的贡献流程**，确保它们生成的代码符合项目长期积累的编码规范、架构约定和最佳实践，从而减少人工审查的负担，提高代码质量和合并效率。

*   **变更点2：引入AI Agent自检（Self-Review）技能**
    *   **内容**：在 `.ai/` 目录下新增了 `self-review` 技能。该技能会模拟CI（持续集成）的审查规则（来自 `review-rules.md`），在AI Agent提交PR前，对其生成的代码进行自检，报告需要修复的阻塞性问题、死代码等。
    *   **与项目方向的关系**：这是对变更点1的深化。它不仅仅是“要求”AI Agent遵守规范，而是**提供了一个工具**让AI Agent在提交前就能自我纠错。这体现了项目在拥抱AI带来的效率提升的同时，也积极构建**质量保障的闭环**，将质量控制左移到开发的最早期阶段。

*   **变更点3：清理和重构 `.ai/` 目录**
    *   **内容**：移除了不成熟的 `parity-testing`（数值一致性测试）技能，将其中的数值差异排查要点整理为 `model-integration/pitfalls.md`。同时，重构了模型集成、流水线等指南，使其结构更清晰、更模块化。
    *   **与项目方向的关系**：这体现了项目对内部工具和文档的**持续维护和精益求精**。移除不成熟的功能，保留其精华，并重构文档结构，使得 `.ai/` 目录作为AI Agent的“操作手册”更加清晰、实用、易于维护。这直接提升了AI Agent贡献的质量上限。

### 3. 对项目的影响和潜在意义

*   **提升AI Agent贡献质量**：这是最直接的影响。通过流程引导和自检工具，AI Agent生成的PR将更少地出现与项目约定不符的问题，从而减少人工审查的重复劳动。
*   **降低贡献门槛**：对于希望使用AI Agent为 `diffusers` 做贡献的新手，清晰的指引和自检工具能帮助他们更快地上手，并产出符合规范的代码。
*   **构建人机协作的典范**：`diffusers` 正在探索一种高效的开发者与AI Agent协作模式。这些提交表明，项目不仅仅是在“使用”AI，而是在**主动设计一套系统**来管理和引导AI的贡献，使其成为项目发展的可靠助力。
*   **为未来扩展奠定基础**：`.ai/` 目录的标准化和结构化，为未来引入更多AI辅助技能（如自动化测试生成、文档编写等）提供了清晰的框架。

### 4. 值得关注的技术点

*   **`.ai/` 目录的约定**：`diffusers` 项目通过 `.ai/` 目录来封装AI Agent的“知识”和“技能”，这是一种值得关注的项目管理实践。它使得AI Agent的配置、规则和工具与项目代码本身一同版本化，便于维护和同步。
*   **`self-review` 技能的实现思路**：它通过模拟CI审查规则，实现了“左移”的质量控制。这种“在提交前模拟审查”的思路，对于任何希望利用AI Agent进行开发的项目都有借鉴意义。
*   **`review-rules.md` 的角色**：这个文件成为了连接人类审查者（`@claude` CI）和AI Agent（`self-review` 技能）的**共同标准**，确保了审查标准的一致性。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **背景回顾**：`diffusers` 是一个旨在让所有人（包括非专业研究者）都能轻松使用、训练和分享扩散模型的库。它强调社区贡献和快速迭代。
*   **影响分析**：
    *   **加速社区贡献**：通过优化AI Agent的贡献流程，项目实际上是在**赋能**一个庞大的“AI开发者”社区。这有望大幅增加有效PR的数量和质量，加速新模型、新Pipeline的集成。
    *   **维护项目健康度**：在拥抱AI带来的速度优势的同时，通过自检和规范化流程，项目有效地**对冲了AI可能带来的代码质量风险**。这确保了项目在高速发展时，不会因为代码风格混乱、架构偏离而陷入技术债务。
    *   **巩固领导地位**：作为最流行的扩散模型库，`diffusers` 率先探索并实践了与AI Agent协作的成熟模式，这有助于其**

## 详细提交记录

### [41add34](https://github.com/huggingface/diffusers/commit/41add3410424cc33d748a7fd3409132d2f6b4ad2)

- **作者**: YiYi Xu
- **时间**: 2026-06-12T17:02:11Z
- **提交信息**: update PR template and highlight AI-agent setup for contributors (#13913)

* docs: surface AI-agent setup for contributors

Most code contributions now involve a coding agent, but the agent setup
(`make claude`/`make codex`, the conventions in `.ai/`) is opt-in and easy
to miss, so agents run without project context and produce PRs that ignore
conventions. Surface it where contributors will see it:

- README: pointer to `.ai/` / `make claude` in the contribution section
- PR template: an AI-agent setup + self-review checkbox (now the first item),
  folding the typo/docs exception into the philosophy-doc check, and dropping
  the deprecated JAX reviewer routing (Flax is slated for removal in v0.40.0;
  MPS kept)

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* docs: nest the AI-agent checklist into a parent + sub-items

Make the AI-agent item a parent checkbox ("Did you use an AI agent?") with
two sub-checkboxes (point it at .ai/ conventions; self-review against
.ai/review-rules.md).

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [141852f](https://github.com/huggingface/diffusers/commit/141852f532e8fc9b708e7fc2d58d3e1bddcc458d)

- **作者**: YiYi Xu
- **时间**: 2026-06-12T17:01:52Z
- **提交信息**: [.ai] add self-review skill (#13917)

* [.ai] add self-review skill, retire parity-testing skill, and tighten the agent guides

- New `self-review` skill mirroring the `@claude` CI review (rubric from
  review-rules.md, call-path dead-code analysis), report-only, with the report
  flagging what to fix before submitting (blocking + dead code) vs what to leave
  for the actual review.
- Remove the WIP `parity-testing` skill; preserve its pitfalls as
  `model-integration/pitfalls.md` (numerical-discrepancy reference).
- model-integration: restructure around a grouped checklist, default-to-modular,
  an overall file-structure sketch (details deferred to the guides), a
  fresh-conversion `Model parity test` example (internal, not shipped), and a
  filled-in weight/checkpoint-conversion section.
- Centralize the loading rule (from_pretrained / from_single_file, no custom
  loaders) in models.md; add per-folder File structure sections to models.md /
  pipelines.md; default-to-modular note in pipelines.md.
- AGENTS.md: dedicated 'Self-review before a PR' and 'Reference guides' sections.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* [.ai] simplify pitfalls #6 and drop the model-storage / injection-test entries

Trim pitfall #6 to the essential point (small dtype diffs compound into a large
final difference), remove the `/tmp` model-storage and incomplete-injection-test
pitfalls, and renumber 1-16 with cross-references updated.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* [.ai] drop parity-harness-specific pitfalls

With the parity-testing skill gone, remove the stale-test-fixtures pitfall (saved
tensors / cross-pipeline fixtures no longer apply) and de-jargon the noise-dtype
detection note. Keeps the pitfalls list generic to numerical discrepancy.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* [.ai] trim pitfalls to a concise possible-causes reference

Drop the variable-shadowing and decoder-config pitfalls and the noise-dtype
'Detection' aside, tighten the remaining entries, renumber 1-12 (cross-refs
updated), and reframe the intro as a non-checklist reference list of possible
causes to consult only when outputs don't match.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Apply suggestion from @yiyixuxu

* Apply suggestion from @yiyixuxu

* [docs] update contributing guide for the self-review skill

Replace the retired parity-testing skill with self-review in the skills list, and
add a 'Self-review before opening' step to the AI-assisted contributions section:
run the self-review skill / review-rules, fix blocking issues + dead code, and
treat the @claude CI review as a non-authoritative helper (note any intentional
skips in the PR for the reviewer).

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Apply suggestions from code review

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* [.ai] fix dangling pitfalls ref and broaden self-review scope

- Drop the broken 'pitfalls.md #10' reference in the conversion step (the /tmp
  model-storage pitfall was removed); save to a local path instead.
- Self-review now reviews the whole diff, not just src/diffusers/ and .ai/ — a
  contributor should review their own tests/docs/scripts too (the CI's scoping is
  a safety measure for untrusted PRs). Reword to 'same rubric as the CI'.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 414
- **最后更新**: 2026-06-09T03:21:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12572
- **最后更新**: 2026-06-12T15:02:52Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

好的，这是对 `modelscope/DiffSynth-Studio` 仓库昨日提交记录的分析总结。

### 提交记录分析总结

**提交：** `c2a8020` - ACE-Step Enhancement (#1491)

#### 1. 主要更新类型
- **功能新增 (Feature Enhancement)**：本次提交是对现有“ACE-Step”功能的增强，主要增加了对新模板的支持和音频时长控制。

#### 2. 关键变更点及其与项目整体方向的关系
- **支持 ACE-Step 模板 (support acestep templates)**：为 `ACE-Step` 功能引入了模板系统。这很可能意味着用户现在可以通过预定义的模板或配置文件，更方便、更标准化地使用 `ACE-Step` 进行视频/图像生成或编辑。
- **添加最大音频时长参数 (add max_audio_duration)**：在 `ACE-Step` 的训练或推理流程中，新增了 `max_audio_duration` 参数。这表明 `ACE-Step` 功能可能涉及音频处理（如视频生成中的音频同步或基于音频的驱动），该参数用于控制输入音频的最大长度，以优化资源使用和模型性能。

**与项目方向的关系**：`DiffSynth-Studio` 的核心目标是提供高效、高质量的图像和视频合成工具。`ACE-Step` 很可能是项目中一个重要的视频/图像生成或编辑管线。本次更新通过引入模板和音频时长控制，**提升了该管线的易用性、灵活性和鲁棒性**，使其更接近一个成熟、可配置的工业级工具。

#### 3. 对项目的影响和潜在意义
- **降低使用门槛**：模板的引入使得非专业用户也能快速上手 `ACE-Step` 功能，无需深入了解底层参数配置，这有助于扩大项目的用户基础。
- **提升生成质量与可控性**：`max_audio_duration` 参数的加入，暗示了项目在探索“音频驱动”或“音视频同步”的生成能力。这为未来实现更复杂的、基于音频内容（如音乐、语音）的动态视频生成奠定了基础，是项目从“图像/视频合成”向“多模态内容生成”演进的重要一步。
- **代码质量提升**：提交中包含了代码审查（Co-authored-by），表明项目遵循良好的协作开发流程，有助于保证代码的稳定性和可维护性。

#### 4. 值得关注的技术点
- **模板化设计**：`acestep templates` 的实现方式值得关注。它是通过配置文件（如 YAML/JSON）还是代码层面的类/函数抽象来实现的？这反映了项目在模块化和可扩展性方面的设计思路。
- **音频处理集成**：`max_audio_duration` 参数的出现，意味着 `DiffSynth-Studio` 正在将音频处理能力集成到其核心的视频生成管线中。这涉及到音频特征提取、与视频内容的对齐、以及可能的多模态模型融合等复杂技术。

#### 5. 基于项目背景，这些提交如何影响项目发展
- **从“合成”走向“智能创作”**：`DiffSynth-Studio` 的README强调了其作为“合成工作室”的定位。本次更新通过引入音频控制，标志着项目正在从单纯的“视觉合成”向“多模态智能创作”平台迈进。用户未来可能不仅能控制“画面”，还能通过“声音”来驱动和影响生成内容。
- **巩固在视频生成领域的竞争力**：在视频生成领域，如何实现精准的音频-视频同步是一个关键挑战。`ACE-Step` 对音频时长的支持，表明项目正在积极攻克这一难题，这有助于提升其在同类开源项目（如 Stable Video Diffusion 等）中的技术竞争力。
- **推动社区贡献与生态建设**：模板的引入为社区贡献者提供了更清晰的扩展点。开发者可以基于现有模板创建新的、针对特定场景（如音乐视频、口播视频）的 `ACE-Step` 模板，从而丰富项目的应用生态。

## 详细提交记录

### [c2a8020](https://github.com/modelscope/DiffSynth-Studio/commit/c2a8020fdfa03edce9059553ca205a7aac677db5)

- **作者**: Zhongjie Duan
- **时间**: 2026-06-12T07:19:57Z
- **提交信息**: ACE-Step Enhancement (#1491)

* support acestep templates

* add max_audio_duration

* Update examples/ace_step/model_training/train.py

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

---------

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 28939
- **最后更新**: 2026-06-12T23:11:53Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 25
- **主要提交者**: Alex Nails, liuxpro, ybyang

## AI分析总结

好的，作为专业的代码分析助手，我对 `sgl-project/sglang` 仓库昨日的提交记录进行了分析。结合项目背景（一个专注于 LLM 推理和服务的高性能框架），以下是昨日更新的要点总结：

### 1. 主要更新类型

- **Bug修复 (Bug Fixes):** 占比最高，涉及 MoE、推测解码 (Speculative Decoding)、AMD 平台、KV Cache、内存泄漏等多个方面。
- **功能新增 (New Features):** 支持了新的模型架构（Nemotron DP attention & MTP），并增加了新的演示示例（CoVe）。
- **性能优化 (Performance Improvements):** 针对 Cutlass FP8 GEMM 内核、推测解码的显存占用等进行了优化。
- **文档更新 (Documentation):** 更新了 Nemotron 和 Kimi K2.7 的 Cookbook，以及模型文档和最佳实践。
- **CI/基础设施 (CI/Infrastructure):** 为 AMD 平台增加了新的 CI 测试层级，并修复了 CI 工作流中的问题。
- **重构 (Refactoring):** 对推测解码模块的输入捕获逻辑进行了集中化和重构。

### 2. 关键变更点及其与项目整体方向的关系

- **推测解码 (Speculative Decoding) 增强与修复：**
    - **变更：** 修复了 `EagleDraftWorker` 的注意力后端分配问题 (`#28096`)，集中化了虚拟验证输入捕获逻辑 (`#28032`)，并安装了新的 `EagleDraftExtendInput` 作为 V2 规范信息 (`#24860`)。
    - **关系：** 推测解码是 SGLang 提升推理吞吐量的核心技术。这些提交表明项目正在积极完善和稳定其推测解码实现，特别是针对更复杂的 EAGLE 架构，以提供更可靠和高效的加速能力。

- **AMD 平台支持深化：**
    - **变更：** 修复了 DeepSeek-V4-Flash-FP8 在 MI300 上的问题 (`#27972`)，修复了 CI 中的 `fwd_occupancy` 问题 (`#28075`)，并增加了新的 CI 测试层级 (`#27822`)。
    - **关系：** 这与项目 README 中强调的“支持多种硬件后端”方向高度一致。持续投入 AMD 平台（特别是 MI300 系列）的兼容性和性能，表明 SGLang 致力于成为跨平台的高性能推理引擎，不局限于 NVIDIA GPU。

- **新模型架构支持：**
    - **变更：** 支持了 Nemotron 的 DP attention 和 MTP (Multi-Token Prediction) (`#24955`)。
    - **关系：** 这是对项目模型支持范围的重大扩展。Nemotron 是 NVIDIA 发布的重要开源模型，其 MTP 架构与 SGLang 的推测解码技术有天然的协同效应。支持该模型可以吸引更多用户和社区贡献。

- **性能与效率优化：**
    - **变更：** 优化了 Cutlass FP8 GEMM 内核，跳过了不必要的 padding 操作 (`#27896`)；修复了 EAGLE 模型 KV Cache 的显存占用计算问题 (`#23862`)。
    - **关系：** 性能优化是 SGLang 的核心目标。这些优化直接作用于底层计算内核和显存管理，有助于提升模型推理的吞吐量和降低延迟，巩固其在高性能推理框架中的地位。

- **API 兼容性与修复：**
    - **变更：** 修复了 Responses API (`#25881`) 和 Anthropic Messages API (`#25876`) 的请求处理问题。
    - **关系：** 这表明 SGLang 不仅提供高性能推理，也致力于提供与主流 API 标准兼容的服务接口，方便用户集成和迁移，提升其作为服务框架的易用性和通用性。

### 3. 对项目的影响和潜在意义

- **稳定性和可靠性提升：** 大量的 Bug 修复，尤其是在 MoE、推测解码和 AMD 平台等关键模块上，将显著提升项目的稳定性和可靠性，减少用户在生产环境中遇到的问题。
- **硬件生态扩展：** 对 AMD 平台的持续投入，有助于 SGLang 在非 NVIDIA 硬件生态中建立影响力，降低用户对单一硬件供应商的依赖。
- **模型生态扩展：** 支持 Nemotron 等新模型，特别是其 MTP 特性，将吸引更多模型开发者和用户，丰富项目的应用场景。
- **性能天花板提升：** 底层 GEMM 内核的优化和推测解码的完善，有望在现有基础上进一步提升推理性能，尤其是在高吞吐量场景下。
- **开发者体验改善：** 文档更新、最佳实践修订和 CI 修复，都直接改善了开发者和用户的体验，降低了上手和贡献的门槛。

### 4. 值得关注的技术点

- **`FlashInfer A2A` 的鲁棒性修复 (`#27945`)：** 修复了 MoE 模型中 `global_num_tokens` 为 NaN 的问题，这是一个关键的稳定性修复，可能影响所有使用 FlashInfer 的 MoE 模型。
- **`EagleDraftExtendInput` 作为 V2 规范信息 (`#24860`)：** 这表明 SGLang 的推测解码模块正在进行架构升级，引入更清晰的接口和数据结构，为未来更复杂的推测策略打下基础。
- **`carries_draft_hidden_states` 的引入 (`#28032`)：** 这个新属性暗示了未来可能支持在推测解码过程中传递草稿模型的隐藏状态，这可能是实现更高级的验证

## 详细提交记录

### [f23f48d](https://github.com/sgl-project/sglang/commit/f23f48df98f702496c85d34e67069f6b8d94979e)

- **作者**: YAMY
- **时间**: 2026-06-12T23:11:44Z
- **提交信息**: fix(moe): make FlashInfer A2A robust to collapsed global_num_tokens (moe_dense_tp_size NaN) (#27945)

### [d601eda](https://github.com/sgl-project/sglang/commit/d601edab73b2225eb153998b1534a306876f9216)

- **作者**: Cheng Wan
- **时间**: 2026-06-12T22:47:05Z
- **提交信息**: [Spec] Fix EagleDraftWorker draft-extend attn backend assignment (#28096)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [fd977ad](https://github.com/sgl-project/sglang/commit/fd977adbd604b6da69e11892f14b85de575f2bbc)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-12T22:39:33Z
- **提交信息**: Fix PR-close cancellation skipping workflows beyond the first 30 (#27785)

### [b0b8436](https://github.com/sgl-project/sglang/commit/b0b8436f1c031caba61c4cadb10d22ba097cd960)

- **作者**: Kangyan-Zhou
- **时间**: 2026-06-12T22:20:36Z
- **提交信息**: [Fix] Unquote ResponseTool annotation breaking lint on all PRs (#28095)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [54989b1](https://github.com/sgl-project/sglang/commit/54989b1fd025d40c51774f47acf866e17a3fc3fd)

- **作者**: Michael
- **时间**: 2026-06-12T22:12:56Z
- **提交信息**: [AMD] ci: add label-gated extra-a tier (kv_canary + mock_model unit tests) (#27822)

### [95867f0](https://github.com/sgl-project/sglang/commit/95867f0932a6204ef281d086ce64c08a4430bf01)

- **作者**: Brayden Zhong
- **时间**: 2026-06-12T21:51:58Z
- **提交信息**: [Doc] Fix some inconsistencies in the Nemotron Cookbook (#28087)

Co-authored-by: Brayden Zhong <brayden.zhong@radixark.ai>

### [85712fa](https://github.com/sgl-project/sglang/commit/85712fa5b034a826d989ff858e8f6556d9a7164d)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-12T21:47:55Z
- **提交信息**: Fix Responses API request handling (#25881)

Co-authored-by: Kai-Hsun Chen <kaihsun@apache.org>
Co-authored-by: Kristin Cowalcijk <kristincowalcijk@gmail.com>
Co-authored-by: aerosta <63026763+aerosta@users.noreply.github.com>
Co-authored-by: glaziermag <glaziermag@users.noreply.github.com>
Co-authored-by: Blake Ledden <blake.ledden@gmail.com>
Co-authored-by: PanJason <pyyjason@gmail.com>
Co-authored-by: Leoyzen <leoyzen@gmail.com>
Co-authored-by: kennyu <966806+kennyu@users.noreply.github.com>

### [b327026](https://github.com/sgl-project/sglang/commit/b3270264e4d2417bf051f5660015071aeda40120)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-12T21:46:57Z
- **提交信息**: Fix Anthropic Messages API compatibility (#25876)

Co-authored-by: Jairo David Campaña Rosero <jairocampana10001@gmail.com>
Co-authored-by: Karan Bansal <3264937+karanb192@users.noreply.github.com>
Co-authored-by: eason <85663565+mango766@users.noreply.github.com>
Co-authored-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>
Co-authored-by: qingchanghan <17794466+qingchanghan@users.noreply.github.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
Co-authored-by: Ajay Anubolu <124525760+AjAnubolu@users.noreply.github.com>
Co-authored-by: Ravitez Dondeti <13931987+dondetir@users.noreply.github.com>
Co-authored-by: Ratish P <114130421+Ratish1@users.noreply.github.com>
Co-authored-by: Xiaoshuai Zhang <15795935+jetd1@users.noreply.github.com>
Co-authored-by: Ricardo-M-L <69202550+Ricardo-M-L@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuan.tong@radixark.ai>

### [caf5975](https://github.com/sgl-project/sglang/commit/caf59759ea043c96a4aa0cc7ac84f2f516b170d8)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-12T21:23:29Z
- **提交信息**: [Spec] Centralize dummy verify-input capture; add `carries_draft_hidden_states` (#28032)

### [65d76bd](https://github.com/sgl-project/sglang/commit/65d76bd3f6943f5394638c79c6901c5b3ace6ced)

- **作者**: Michael
- **时间**: 2026-06-12T21:14:34Z
- **提交信息**: [AMD] Fix CI base-a `fwd_occupancy`: disable `SGLANG_SANITIZE_NAN_LOGITS` in AMD CI (#28075)

### [1e71c1a](https://github.com/sgl-project/sglang/commit/1e71c1a8598298cf07309dbab154b3f65b1b4523)

- **作者**: ybyang
- **时间**: 2026-06-12T21:08:36Z
- **提交信息**: fix(pd): disable overlap for spec+grammar in disagg decode loop (#28039)

### [cb9140e](https://github.com/sgl-project/sglang/commit/cb9140ee610819b4244903e496b09c3bbbd9d54a)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-12T20:51:50Z
- **提交信息**: Enable PDL for GPT-OSS tinygemm router (#27941)

### [9d37e71](https://github.com/sgl-project/sglang/commit/9d37e710b7761212bd77ff9a8e588570b78326ba)

- **作者**: shuwenn
- **时间**: 2026-06-12T20:44:38Z
- **提交信息**: [Bench] Add consistent p90/p95/p99 percentiles for all latency metrics (#27662)

### [627ed34](https://github.com/sgl-project/sglang/commit/627ed3476b0567609ca81a15d584eb4abb036e97)

- **作者**: Zach Zhu
- **时间**: 2026-06-12T20:44:11Z
- **提交信息**: Fix invalid KVFP4QuantizeUtil references (#28013)

Signed-off-by: Zach Zhu <zzqshu@126.com>

### [3be5a7e](https://github.com/sgl-project/sglang/commit/3be5a7ec8976278196e7022a15671cfed83e8782)

- **作者**: Vedant V Jhaveri
- **时间**: 2026-06-12T19:30:47Z
- **提交信息**: Respect explicit --max-running-requests instead of clamping to heuristic (#27399)

Co-authored-by: Vedant Jhaveri <vjhaveri@linkedin.com>

### [6e0fa5a](https://github.com/sgl-project/sglang/commit/6e0fa5afe1c615aa3407b8a8474f841f5f590153)

- **作者**: Zhichen Zeng
- **时间**: 2026-06-12T19:21:12Z
- **提交信息**: Support Nemotron DP attention and MTP (#24955)

Co-authored-by: Jiajun Li <48857426+guapisolo@users.noreply.github.com>
Co-authored-by: Zhichenzzz <northwesterniemsteaching@gmail.com>

### [bb33594](https://github.com/sgl-project/sglang/commit/bb33594c1a57ad0034afd6b999ddaab1d5c512c7)

- **作者**: David Wang
- **时间**: 2026-06-12T18:35:05Z
- **提交信息**: flashinfer swa kv pool fix (dflash gemma 4) (#27737)

### [fa4273d](https://github.com/sgl-project/sglang/commit/fa4273d2dbb51e1033d38efc1cf3b3540252a110)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-12T18:19:44Z
- **提交信息**: [Docs] Add Kimi K2.7 Code cookbook (#28064)

Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [75998d0](https://github.com/sgl-project/sglang/commit/75998d0421b1edc7267e75dff7245b6202184b9c)

- **作者**: cctry
- **时间**: 2026-06-12T17:35:48Z
- **提交信息**: Fix --mem-fraction-static not accounting for EAGLE draft model KV cache       (#23862)

### [533b59d](https://github.com/sgl-project/sglang/commit/533b59d00c666bbcf30875940a9ad89ba65b23c0)

- **作者**: Alex Nails
- **时间**: 2026-06-12T17:28:58Z
- **提交信息**: Add @alexnails as codeowner for srt/platforms (#28066)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [c80d8fe](https://github.com/sgl-project/sglang/commit/c80d8fe78ae22411d660c58dd4024fbfa2edb8f2)

- **作者**: Yuan Luo
- **时间**: 2026-06-12T16:01:53Z
- **提交信息**: [Perf] Skip per-call mat_a/scales_a padding in cutlass FP8 blockwise GEMM (#27896)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [9f6b233](https://github.com/sgl-project/sglang/commit/9f6b2339f9ecf2d1b52a59f4679b24ba3376a61c)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-12T15:42:23Z
- **提交信息**: docs(minimax-m3): warm-steady-state benchmark numbers (#28062)

### [50815d5](https://github.com/sgl-project/sglang/commit/50815d54a7b6502342aa037cf462cb1677190a82)

- **作者**: Yuhao Yang
- **时间**: 2026-06-12T13:19:40Z
- **提交信息**: docs (#28061)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [dba617f](https://github.com/sgl-project/sglang/commit/dba617f2ec2bc957f4a7a443d669dcd78e693fcd)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-12T13:14:35Z
- **提交信息**: doc: update docs for new model (#28060)

### [fcae676](https://github.com/sgl-project/sglang/commit/fcae6767d530634a52306d0b82279924eb97c46f)

- **作者**: qiaozp
- **时间**: 2026-06-12T12:34:55Z
- **提交信息**: Add bucketed multi-dir layout for NIXL file storage (#27672)

Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [18989f3](https://github.com/sgl-project/sglang/commit/18989f3d4812f144d862a63c873bf1f93034ebc0)

- **作者**: luoroger37
- **时间**: 2026-06-12T10:20:24Z
- **提交信息**: [PD] Fix resource leak on prealloc/transfer abort and idle check (#28022)

### [f308abc](https://github.com/sgl-project/sglang/commit/f308abc05212c2f5f455de22a525e14afa63ee4f)

- **作者**: ming_wang
- **时间**: 2026-06-12T09:12:33Z
- **提交信息**: Revise the mimo-v2-flash best practice (#28016)

### [83c0007](https://github.com/sgl-project/sglang/commit/83c0007f8df751345273957516a84129a83dcd5a)

- **作者**: liuxpro
- **时间**: 2026-06-12T08:57:33Z
- **提交信息**: examples: add Chain-of-Verification (CoVe) hallucination reduction demo (#27866)

Co-authored-by: unknown <liuxiao.209@360buyad.local>

### [371b96e](https://github.com/sgl-project/sglang/commit/371b96e210d460d9598f73e9f6cf846078735234)

- **作者**: Xinyi Song
- **时间**: 2026-06-12T08:51:32Z
- **提交信息**: [AMD] Fix DeepSeek-V4-Flash-FP8 on MI300 (#27972)

### [694cea8](https://github.com/sgl-project/sglang/commit/694cea8656373bbef2d1073cab92a6a6857c3d63)

- **作者**: Joectwm
- **时间**: 2026-06-12T08:16:14Z
- **提交信息**: Add EPD disaggregated encode tracing (#25994)

### [60e4f14](https://github.com/sgl-project/sglang/commit/60e4f1495319462bd70b5e2f1f93a4d122f77521)

- **作者**: iridiumine
- **时间**: 2026-06-12T08:05:06Z
- **提交信息**: [NPU][Bugfix] Fix accuracy issue in no-graph with MTP (#27752)

### [a52ccd2](https://github.com/sgl-project/sglang/commit/a52ccd21791c14a718ec955ca2a1c7cfd0506552)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-12T07:46:16Z
- **提交信息**: [Spec] Install `EagleDraftExtendInput` as the V2 draft-extend `spec_info` (#24860)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1196
- **最后更新**: 2026-06-12T14:02:22Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 昨日更新要点总结

#### 1. 主要更新类型
- **功能新增 (feat)**：核心功能增强。
- **项目配置 (chore)**：新增配置文件。

#### 2. 关键变更点及其与项目整体方向的关系
- **SVDQuant支持DTensor (PyTorch TP)**：
    - **变更点**：为量化模块 `SVDQuant` 增加了对 `DTensor`（PyTorch的张量并行表示）的支持。
    - **与项目方向的关系**：项目目标是构建一个“原生PyTorch推理引擎”，并强调“并行化 (Parallelism)”。此更新直接实现了PyTorch原生的张量并行（TP）能力，是项目核心架构的重要演进。
- **新增并行 + SVDQuant配置文件**：
    - **变更点**：添加了用于同时启用并行化和SVDQuant的YAML配置文件。
    - **与项目方向的关系**：这表明项目正在将“并行化”和“量化”这两个核心特性进行组合与标准化，为用户提供开箱即用的最佳实践配置，降低了使用门槛。

#### 3. 对项目的影响和潜在意义
- **性能与可扩展性飞跃**：`SVDQuant` 支持 `DTensor` 意味着量化后的模型可以无缝地在多个GPU上进行张量并行推理。这能显著提升大模型（DiTs）的推理速度，并支持处理更大分辨率的图像生成任务，是项目从单卡推理迈向多卡分布式推理的关键一步。
- **易用性提升**：提供组合配置文件，让用户无需手动配置复杂的并行和量化参数，即可快速体验项目的最强性能模式，有助于吸引更多用户和开发者。

#### 4. 值得关注的技术点
- **PyTorch DTensor**：这是PyTorch 2.x引入的原生张量并行抽象。项目选择直接支持 `DTensor`，而非使用 `FSDP` 或第三方库，体现了其“PyTorch-native”的核心理念，与项目README中的定位高度一致。
- **SVDQuant + 并行化组合**：将低秩分解量化（SVDQuant）与张量并行（TP）结合，是一种先进的优化策略。量化减少了单卡的计算和显存压力，而并行化则利用多卡算力弥补量化可能带来的精度损失，两者协同工作，有望在保持生成质量的同时大幅提升吞吐量。

#### 5. 基于项目背景，这些提交如何影响项目发展
- **从“单机优化”到“分布式优化”的跨越**：根据README，项目最初聚焦于“缓存、量化、CPU卸载”等单机优化手段。此次更新标志着项目正式进入分布式并行推理领域，极大地拓宽了其应用场景，使其能够服务于更大规模、更高要求的DiT模型部署。
- **巩固“PyTorch-native”定位**：通过原生支持 `DTensor`，项目避免了引入复杂的分布式框架依赖，保持了代码的简洁性和与PyTorch生态的兼容性，这对于吸引PyTorch用户群体至关重要。
- **形成完整的技术栈**：`并行化 + 量化` 配置文件的出现，意味着项目正在将各个独立的优化技术（缓存、量化、并行）整合成一个统一的、可组合的解决方案。这标志着项目从“功能集合”向“成熟推理引擎”的转变。

## 详细提交记录

### [33eacf7](https://github.com/vipshop/cache-dit/commit/33eacf7e74f2e139bd3a9c635f1a9fc2a3cc7cc3)

- **作者**: DefTruth
- **时间**: 2026-06-12T11:20:33Z
- **提交信息**: chore: add parallel + svdq config yaml (#1052)

* chore: add parallel + svdq config yaml

* chore: add parallel + svdq config yaml

* chore: add parallel + svdq config yaml

* chore: add parallel + svdq config yaml

### [234b808](https://github.com/vipshop/cache-dit/commit/234b8088c8a93500d0952ce9ade7ad519e0be2f4)

- **作者**: DefTruth
- **时间**: 2026-06-12T07:37:29Z
- **提交信息**: feat: SVDQuant support DTensor (PyTorch TP) (#1051)

* feat: SVDQuant support DTensor (PyTorch TP)

* feat: SVDQuant support DTensor (PyTorch TP)

* feat: SVDQuant support DTensor (PyTorch TP)

* feat: SVDQuant support DTensor (PyTorch TP)

* feat: SVDQuant support DTensor (PyTorch TP)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 82723
- **最后更新**: 2026-06-12T23:16:10Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 32
- **主要提交者**: Isotr0py, qizixi, Thillai Chithambaram

## AI分析总结

好的，作为专业的代码分析助手，以下是对 `vllm-project/vllm` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **Bug修复 (Bugfix):** 约 10 项，涉及内存管理、CPU/XPU兼容性、前端错误处理、Docker构建等。
*   **性能优化 (Perf):** 约 5 项，集中在 AMD ROCm、NVIDIA SM100 等特定硬件的算子融合与解码路径优化。
*   **功能新增 (Feature):** 约 8 项，包括新模型支持 (Dflash, Qwen3Next)、新工具解析器 (Granite4)、结构化输出支持、KV Cache 传输等。
*   **重构与迁移 (Refactor/Migration):** 约 6 项，包括模型运行器 (Model Runner) 从 v1 到 v2 的迁移、GGUF 量化插件化、Machete 内核 ABI 迁移等。
*   **文档更新 (Docs):** 约 3 项，涉及 KV Connector 指标记录、编码风格指南等。
*   **指标与监控 (Metrics):** 约 3 项，新增了 MLA 注意力、KV Cache 容量等关键性能指标。

### 2. 关键变更点及其与项目整体方向的关系

*   **模型支持与生态扩展：**
    *   **新增模型：** 支持 `Dflash` 和 `Qwen3Next` 模型，并移除了旧的 `Mono-InternVL` 模型。这表明项目持续跟进最新、最流行的开源模型，同时清理技术债务。
    *   **工具调用增强：** 为 `ResponsesAPI` 和通用工具调用添加了“严格模式”，并新增了 `Granite4` 工具解析器。这直接响应了 LLM 服务中 Agent 和 Function Calling 场景的迫切需求，增强了 vLLM 作为生产级推理引擎的实用性。

*   **性能与硬件适配：**
    *   **AMD ROCm 深度优化：** 融合了 DeepSeek V4 的逆 RoPE 和缓存操作，并升级了 PyTorch 版本。这体现了 vLLM 对 AMD 生态的持续投入，旨在缩小与 NVIDIA 平台的性能差距。
    *   **NVIDIA SM100 优化：** 为 `next_n > 2` 场景启用了原生 DSA indexer 解码路径，这是对最新 NVIDIA 硬件架构的针对性优化。
    *   **CPU 支持增强：** 支持了 CPU 上的 W4A16 INT4 MoE 模型，并修复了 arm64 镜像构建问题。这扩展了 vLLM 在非 GPU 环境下的部署能力，符合“为每个人提供 LLM 服务”的愿景。

*   **架构演进与稳定性：**
    *   **Model Runner v2 迁移：** 这是持续进行的重大架构重构，本次提交将 Qwen 和 DeepSeek V2 MoE 模型迁移至新架构。这旨在统一代码路径、提升可维护性并为未来特性奠定基础。
    *   **KV Connector 功能增强：** 支持了 Prefill 节点向 Decode 节点的 KV 推送，并修复了调度器侧的统计聚合问题。这是实现“分离式推理”（Disaggregated Serving）的关键一步，能显著提升长序列场景下的吞吐和效率。
    *   **结构化输出支持：** 为 Beam Search 添加了结构化输出支持，扩展了高级解码策略的可用性。

### 3. 对项目的影响和潜在意义

*   **提升生产环境可靠性：** 大量 Bug 修复（如内存过早释放、前端错误处理、超时参数传递）直接提升了 vLLM 在复杂生产环境下的稳定性和鲁棒性。
*   **降低部署门槛：** CPU 支持和更广泛的硬件适配（AMD, Intel XPU）使得更多用户可以在不同硬件上部署 vLLM，扩大了用户基础。
*   **增强竞争力：** 对 DeepSeek V4、Qwen3Next 等热门模型的快速支持和优化，以及对 Agent 场景（工具调用）的深度打磨，使 vLLM 在 LLM 推理服务市场中保持领先地位。
*   **为未来架构铺路：** Model Runner v2 和 KV Connector 的持续迁移与增强，是 vLLM 向更高效、更灵活的分布式推理架构演进的核心步骤。

### 4. 值得关注的技术点

*   **`[Model Runner v2]` 迁移：** 这是一个长期、影响深远的重构，值得关注其进展和对模型兼容性的影响。
*   **`[KV Connector]` 的 Prefill/Decode 分离：** 这是实现“分离式推理”架构的关键技术，对优化长序列推理的显存和计算效率至关重要。
*   **`[Kernel]` 级别的优化：** 如 `Marlin` 线程块填充、`Helion` 动态量化内核、`Machete` ABI 迁移等，这些底层优化是 vLLM 性能优势的基石。
*   **`[Metrics]` 的精细化：** 新增的 `MLA attention metrics` 和 `group-aware KV cache capacity` 指标，为 DeepSeek 等复杂模型的性能分析和容量规划提供了更精确的数据支持。

### 5. 基于项目背景，这些提交如何影响项目发展

结合 README 中 “Easy, fast, and cheap LLM serving for everyone

## 详细提交记录

### [1a36978](https://github.com/vllm-project/vllm/commit/1a369783e9a09cfd9ebed9799a7b8bbffdc9896f)

- **作者**: Nick Hill
- **时间**: 2026-06-12T22:39:40Z
- **提交信息**: [BugFix] Avoid prematurely freeing cached mm encoder outputs (#45347)

Signed-off-by: Roger Wang <hey@rogerw.io>
Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [e3e31e5](https://github.com/vllm-project/vllm/commit/e3e31e54b05391d21a4b492d3bde612f47696975)

- **作者**: Kevin H. Luu
- **时间**: 2026-06-12T21:51:45Z
- **提交信息**: [Bugfix][CPU] Don't build triton-cpu on arm64 release image (#45401)

Signed-off-by: khluu <khluu000@gmail.com>

### [badddd2](https://github.com/vllm-project/vllm/commit/badddd254f744d26b6523b464c596f19015370f1)

- **作者**: Fangzhou Ai
- **时间**: 2026-06-12T20:57:09Z
- **提交信息**: [ROCm][DSV4][Perf] Fuse inverse-RoPE and cache bf16 wo_a in o-projection (#45103)

Signed-off-by: Fangzhou Ai <fangzhouai@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [c906500](https://github.com/vllm-project/vllm/commit/c90650088dafc8ad5fc372b412b67170c5ad3f4a)

- **作者**: Michael Goin
- **时间**: 2026-06-12T20:48:15Z
- **提交信息**: Add the QuantizedActivation linear-kernel contract (#44260)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [9eaacb2](https://github.com/vllm-project/vllm/commit/9eaacb23ec1826ddac31657e0eab699de6de3c59)

- **作者**: Michael Goin
- **时间**: 2026-06-12T20:46:21Z
- **提交信息**: [Kernel] Consolidate Marlin thread-tile padding across all dense Marlin paths (#45295)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [78739c1](https://github.com/vllm-project/vllm/commit/78739c1946cfa88fba8ccd4ca7d6c4230f816a3c)

- **作者**: Wentao Ye
- **时间**: 2026-06-12T20:44:52Z
- **提交信息**: [Model Runner v2] Migration from v1 to v2, with Qwen and DSv2 MOE models [3/N] (#42667)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [cf567cb](https://github.com/vllm-project/vllm/commit/cf567cbc71a467d8479411062917e9190ee11376)

- **作者**: Matthew Bonanni
- **时间**: 2026-06-12T20:24:25Z
- **提交信息**: [Attention] Improve attention benchmarks: configs and profiling (#39336)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [39cb9bf](https://github.com/vllm-project/vllm/commit/39cb9bf292ec5811b0df9e5461b9504801c1cf91)

- **作者**: Micah Williamson
- **时间**: 2026-06-12T20:22:26Z
- **提交信息**: [ROCm] Bump Torch to 2.11 (#45362)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [6e4a547](https://github.com/vllm-project/vllm/commit/6e4a54717689b9f3de5f778fb030bd2c2c6ec20f)

- **作者**: Flora Feng
- **时间**: 2026-06-12T20:15:41Z
- **提交信息**: [Refactor] Deprecate ResponsesParser wrapper, inline parsing into ParsableContext (#45431)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [aab639c](https://github.com/vllm-project/vllm/commit/aab639c705dd5df1ca52f77e281ac23413a1993c)

- **作者**: Ryan Rock
- **时间**: 2026-06-12T20:13:31Z
- **提交信息**: [Core][AMD] Propagate shutdown timeout to MultiprocExecutor (#43154)

Signed-off-by: Ryan Rock <ryan.rock@amd.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [efe7adb](https://github.com/vllm-project/vllm/commit/efe7adb5e145de0de2a691cc86756f088f4f01d0)

- **作者**: qizixi
- **时间**: 2026-06-12T19:54:00Z
- **提交信息**: [Perf] Use native DSA indexer decode path for next_n > 2 on SM100 (#45322)

Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [6635279](https://github.com/vllm-project/vllm/commit/6635279d8a75b9e567080a4c36c74d33b35b0bbd)

- **作者**: Isotr0py
- **时间**: 2026-06-12T19:02:21Z
- **提交信息**: [Migration] Migrate GGUF quantization support to plugin (#39612)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [d6fd7ce](https://github.com/vllm-project/vllm/commit/d6fd7ce8daccb290e10c03cbf017d1eb65be4487)

- **作者**: Jonas I. Liechti
- **时间**: 2026-06-12T17:30:09Z
- **提交信息**: [Model][Dflash] Enable Dflash support for Qwen3NextForCausalLM targets (#45319)

Signed-off-by: Jonas I. Liechti <j-i-l@t4d.ch>

### [272c169](https://github.com/vllm-project/vllm/commit/272c16953eac7c46db7719d284d8a0ff19e63446)

- **作者**: Xiaohong (Sean) Chen
- **时间**: 2026-06-12T16:50:06Z
- **提交信息**: [Kernel][Helion][1/N] Add Helion kernel for dynamic_per_token_scaled_fp8_quant (#33790)

Signed-off-by: Sean Chen <seachen@redhat.com>
Co-authored-by: Yanan Cao <gmagogsfm@gmail.com>

### [053e7da](https://github.com/vllm-project/vllm/commit/053e7daa79208fa33ec5fb1801520c4f5da4d9ca)

- **作者**: Yi Zhong
- **时间**: 2026-06-12T16:17:26Z
- **提交信息**: [Model] Add encoder CUDA graph support to Lfm2VL (#44930)

Signed-off-by: vincentzed <207368749+vincentzed@users.noreply.github.com>

### [5af4aec](https://github.com/vllm-project/vllm/commit/5af4aec141cb1047b90e17f069974f99135cd48a)

- **作者**: Tahsin Tunan
- **时间**: 2026-06-12T16:16:36Z
- **提交信息**: [Rust Frontend] Add standalone `granite4` tool parser (#45216)

Signed-off-by: Tahsin Tunan <tahsintunan@gmail.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [a30addc](https://github.com/vllm-project/vllm/commit/a30addc7548a9a8b9b3323a7bc3eb7d7c4895d1c)

- **作者**: Sai Sridhar Tarra
- **时间**: 2026-06-12T15:39:11Z
- **提交信息**: [Docs][KV Connector][NIXL] document KV Transfer stat logging and Prometheus metrics (#44055)

Signed-off-by: Sai Sridhar <tarrasridhar1154@gmail.com>

### [3b8fc3f](https://github.com/vllm-project/vllm/commit/3b8fc3fe6d4afe6680cfc96f5b15fccf4bfff46f)

- **作者**: Chauncey
- **时间**: 2026-06-12T14:59:59Z
- **提交信息**: [Frontend] Support strict mode for tool calling with ResponsesAPI (#45396)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [9ff278b](https://github.com/vllm-project/vllm/commit/9ff278b1d2304ae606a13e8eebab75fcde2d2281)

- **作者**: Srinivas Krovvidi
- **时间**: 2026-06-12T14:51:55Z
- **提交信息**: [Core][KV Connector] fix scheduler KV connector stats aggregation (#43877)

Fixes scheduler-side KV connector stats collection so that:

1. update_connector_output() runs before scheduler-side stats are collected.
2. worker-side and scheduler-side KV connector stats are aggregated when both are present.
3. scheduler-only KV connector stats are still emitted when no worker-side stats exist.

Signed-off-by: srinivas_oo7 <sklinkedin0120@gmail.com>
Co-authored-by: srinivas_oo7 <sklinkedin0120@gmail.com>

### [c7aa3d2](https://github.com/vllm-project/vllm/commit/c7aa3d263049ac9eefd0f59a10f5ecc6a78927df)

- **作者**: Guan-Ming (Wesley) Chiu
- **时间**: 2026-06-12T13:56:25Z
- **提交信息**: [Core] Support structured outputs for beam search (#35022)

Signed-off-by: Guan-Ming (Wesley) Chiu <guanmingchiu@gmail.com>
Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>

### [fbc3a19](https://github.com/vllm-project/vllm/commit/fbc3a1907aeb6beff59461e535045f17ac14306e)

- **作者**: Wentao Ye
- **时间**: 2026-06-12T13:38:12Z
- **提交信息**: [Bug] Migrate Reset cache for both v2 and v1 model runner (#42759)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4171ae4](https://github.com/vllm-project/vllm/commit/4171ae406cdcec1c9952ed6fc00cd9ac91e3e342)

- **作者**: Thillai Chithambaram
- **时间**: 2026-06-12T13:28:40Z
- **提交信息**: [V1][Metrics] Add MLA attention metrics for DeepSeek MFU estimation (#39457)

Signed-off-by: Thillai Chithambaram <thillaichithambaram.a@gmail.com>
Co-authored-by: Mark McLoughlin <markmc@redhat.com>

### [b7f9b6a](https://github.com/vllm-project/vllm/commit/b7f9b6ab271faa621f4cc438fd5ea7ecaf72db8e)

- **作者**: Ethan Feng
- **时间**: 2026-06-12T11:49:44Z
- **提交信息**: [Metrics] Add group-aware KV cache capacity to vllm:cache_config_info (#42206)

The startup log already reports the correct group-aware KV cache capacity for
hybrid models, but Prometheus did not expose matching info in 'vllm:cache_config_info`.

This PR adds kv_cache_size_tokens and kv_cache_max_concurrency.

Signed-off-by: Ethan Feng <ethan.fengch@gmail.com>

### [8af550b](https://github.com/vllm-project/vllm/commit/8af550b39997d15808802cf8527a9cf6182c406b)

- **作者**: liuzhenwei
- **时间**: 2026-06-12T11:45:01Z
- **提交信息**: [BUGFIX][XPU] Update fa interface for compatibility (#45394)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [f1e13f7](https://github.com/vllm-project/vllm/commit/f1e13f7df9ad360df756ffeced301df97b209414)

- **作者**: Tiezhen WANG
- **时间**: 2026-06-12T10:41:09Z
- **提交信息**: [Model] Remove Mono-InternVL (InternLM2VEForCausalLM) (#45129)

Signed-off-by: Xianbao QIAN <xianbao.qian@gmail.com>
Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [88ed636](https://github.com/vllm-project/vllm/commit/88ed63621866d1e4bdaacc560c911f7b8859c53d)

- **作者**: snadampal
- **时间**: 2026-06-12T10:38:41Z
- **提交信息**: [KV Connector]: Support KV push from Prefill to Decode node using Nixl KV Connector (#35264)

Signed-off-by: Sunita Nadampalli <nadampal@amazon.com>
Signed-off-by: NickLucche <nlucches@redhat.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [a014ddd](https://github.com/vllm-project/vllm/commit/a014dddbaa67661236a8a7d0dc3d5773d4e0f60a)

- **作者**: Chris Leonard
- **时间**: 2026-06-12T10:36:49Z
- **提交信息**: [11b/n] Migrate Machete kernels to torch stable ABI (#45304)

Signed-off-by: Chris Leonard <chleonar@redhat.com>
Signed-off-by: Shengqi Chen <harry-chen@outlook.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [a37b4a9](https://github.com/vllm-project/vllm/commit/a37b4a940e6e7b3b3641e6f7b05a1e2507ee7e94)

- **作者**: Thomas Parnell
- **时间**: 2026-06-12T10:23:04Z
- **提交信息**: [Doc] AGENTS.md: add section about coding style (#45301)

Signed-off-by: Thomas Parnell <tpa@zurich.ibm.com>

### [f715f25](https://github.com/vllm-project/vllm/commit/f715f25f290d2a610b142656eb0a4c99ae0d110d)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-06-12T09:58:08Z
- **提交信息**: Fix misleading error for audio duration limit rejection (#45113)

Signed-off-by: jperezde <jperezde@redhat.com>

### [462ef83](https://github.com/vllm-project/vllm/commit/462ef83d58e6fadeb6e216dc583554a6980a0af9)

- **作者**: Fynn Schmitt-Ulms
- **时间**: 2026-06-12T08:05:19Z
- **提交信息**: Update hidden states extraction integration test triggers (#45294)

Signed-off-by: Fynn Schmitt-Ulms <fschmitt@redhat.com>

### [1ae1051](https://github.com/vllm-project/vllm/commit/1ae1051b4bf6e7e98d61b15527040f63eda73a0b)

- **作者**: JinYan Su
- **时间**: 2026-06-12T07:53:11Z
- **提交信息**: [Bugfix][Rust Frontend] Return 400 for prompt-validation submit errors (#45286)

Signed-off-by: xiaguan <751080330@qq.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [2043258](https://github.com/vllm-project/vllm/commit/2043258decb048d0ad2cfb02c8fe1ba3a63aad94)

- **作者**: Chauncey
- **时间**: 2026-06-12T07:51:48Z
- **提交信息**: [Frontend]  Support strict mode for tool calling (#45003)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [bd59c91](https://github.com/vllm-project/vllm/commit/bd59c913bc0338b90bdabdb0e83e5061ce31f9c1)

- **作者**: Michael Goin
- **时间**: 2026-06-12T07:42:18Z
- **提交信息**: [CI] ci-fetch-log.sh: fetch all failed jobs from a build URL or PR number (#45274)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [04cec9e](https://github.com/vllm-project/vllm/commit/04cec9e4d846947e70cc9beebce0a51230905c68)

- **作者**: Ma Jian
- **时间**: 2026-06-12T07:41:36Z
- **提交信息**: [XPU][DeepSeek-V4] Fix MTP: sync with upstream fixes #44821 and #43746 (#45240)

Signed-off-by: Ma Jian <jian1.ma@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [87b98d6](https://github.com/vllm-project/vllm/commit/87b98d6d6cd91768b81e614e0d34d3e7e487dc50)

- **作者**: Will Eaton
- **时间**: 2026-06-12T07:39:27Z
- **提交信息**: [Rust Frontend][Bugfix] Forward --shutdown-timeout and --disable-log-stats to the managed Python engine (#45300)

Signed-off-by: Will Eaton <weaton@redhat.com>

### [0cd9b7a](https://github.com/vllm-project/vllm/commit/0cd9b7af25cd3c47a84e2164392f755415c74fd2)

- **作者**: Yuwen Zhou
- **时间**: 2026-06-12T07:12:37Z
- **提交信息**: [CPU] Support CPU W4A16 INT4 MoE (#43409)

Signed-off-by: yuwenzho <yuwen.zhou@intel.com>

### [a2c72d4](https://github.com/vllm-project/vllm/commit/a2c72d43883e21f3e36f3b970008d2394a714282)

- **作者**: Isotr0py
- **时间**: 2026-06-12T07:10:18Z
- **提交信息**: [Bugfix] Fix Dockerfile dependency graph pre-commit error (#45374)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-13
**监控日期**: 2026-06-12
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5120
- **最后更新**: 2026-06-12T21:43:20Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 6
- **主要提交者**: Samit, wangyu, zyz111222

## AI分析总结

好的，作为专业的代码分析助手，以下是对仓库 `vllm-project/vllm-omni` 昨日提交记录的分析总结。

### 昨日更新要点总结

#### 1. 主要更新类型

- **Bug修复**：修复了特定模型在非CUDA平台上的兼容性问题。
- **平台适配**：为Ascend 310P等特定硬件适配了TTS模型，并修复了平台检测逻辑。
- **重构**：对多模态输出处理流程进行了第二阶段的重构。
- **CI/测试**：跳过了已知问题的测试用例，并优化了CI作业的分配策略。

#### 2. 关键变更点及其与项目整体方向的关系

- **`[Hardware][Ascend] Adapt Qwen3 TTS for 310P`**：将Qwen3 TTS模型适配到Ascend 310P硬件上。这与项目README中“Easy, fast, and cheap omni-modality model serving for everyone”的愿景高度一致，通过支持更多硬件平台（特别是国产AI芯片），降低了用户的使用门槛和成本。
- **`[Refactor] Output Processor Phase 2: separate multimodal output channel`**：对多模态输出处理模块进行重构，将不同模态的输出通道分离。这是对项目核心架构的优化，旨在提升代码的可维护性和扩展性，为未来支持更多复杂的多模态输出（如视频、音频流）奠定基础。
- **`[bugfix] VoxCPM2 audio encoder adapt other than CUDA`** & **`[platform] fix: set UnspecifiedOmniPlatform device_type to cpu`**：修复了VoxCPM2音频编码器在非CUDA平台（如CPU、Ascend）上的运行问题，并修正了平台检测逻辑。这直接提升了项目的跨平台兼容性，是“cheap”和“for everyone”目标的具体体现。
- **`[CI] ...`**：CI相关的提交（跳过测试、优化作业队列）是项目工程化成熟度的体现。通过管理已知问题（`skip MOSS-TTS-Nano E2E tests pending issue#4361`）和优化资源利用（`migrate single-GPU tests to gpu_1_queue`），确保了开发流程的稳定和高效。

#### 3. 对项目的影响和潜在意义

- **扩大硬件生态**：对Ascend 310P的适配，标志着项目开始积极拥抱国产AI芯片生态，这对于吸引国内用户和企业用户至关重要，是项目走向“everyone”的关键一步。
- **提升稳定性与兼容性**：修复非CUDA平台的bug，使得项目不再局限于NVIDIA GPU，能运行在更广泛的硬件上，显著增强了项目的鲁棒性和实用性。
- **架构演进**：输出处理器的重构是长期技术投资。虽然短期内用户可能感受不到变化，但它为未来支持更复杂、更灵活的多模态交互（如同时生成语音和图像）铺平了道路。
- **开发效率提升**：CI的优化和测试管理，减少了开发过程中的噪音和等待时间，让开发者能更专注于核心功能开发。

#### 4. 值得关注的技术点

- **`Output Processor Phase 2`**：这是一个重要的架构变更。`separate multimodal output channel` 意味着项目正在从“一个模型输出多种模态”的简单模式，向“为每种模态设计独立、可插拔的输出处理管道”的复杂模式演进。这涉及到数据流、内存管理和模型调度的重新设计。
- **`UnspecifiedOmniPlatform` 的 `device_type` 默认值设为 `cpu`**：这是一个巧妙的降级策略。当无法识别硬件平台时，默认使用CPU运行，保证了基本功能可用，而不是直接报错，体现了良好的容错设计。

#### 5. 基于项目背景，这些提交如何影响项目发展

- **从“可用”到“好用”**：项目README强调“Easy, fast, and cheap”。昨日的提交中，硬件适配（Ascend）和bug修复（非CUDA）直接降低了“cheap”的门槛；CI优化和架构重构则是为了长期的“fast”和“easy”做铺垫。
- **生态扩张**：对Ascend的支持是项目生态扩张的明确信号。这表明项目团队不仅关注技术前沿，也关注实际部署场景和用户需求，致力于成为一个真正普适的“omni-modality”服务框架。
- **技术成熟度提升**：从修复简单bug到进行核心模块重构，再到优化CI流程，这些提交共同描绘了一个项目从快速原型阶段向成熟、稳定、可扩展的工程化产品阶段迈进的图景。

## 详细提交记录

### [9577ccb](https://github.com/vllm-project/vllm-omni/commit/9577ccba500eb1bbc4fbd79a4f00fd6f4c10c977)

- **作者**: wangyu
- **时间**: 2026-06-12T16:07:57Z
- **提交信息**: [CI] skip MOSS-TTS-Nano E2E tests pending issue#4361 (#4391)

### [54a9d24](https://github.com/vllm-project/vllm-omni/commit/54a9d241c000293407dfae6afcdd4f0d84744919)

- **作者**: wangyu
- **时间**: 2026-06-12T11:05:43Z
- **提交信息**: [CI] Diff-gate L2/L3 E2E jobs and migrate single-GPU tests to gpu_1_queue (#4365)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [6de0ca3](https://github.com/vllm-project/vllm-omni/commit/6de0ca36bb3f60f7f9aefd62bf7fcc930cf56c0b)

- **作者**: zyz111222
- **时间**: 2026-06-12T09:39:21Z
- **提交信息**:  [Hardware][Ascend] Adapt Qwen3 TTS for 310P (#4283)

Signed-off-by: zouyizhou <zouyizhou@huawei.com>
Co-authored-by: Canlin Guo <canlinguosdu@gmail.com>

### [2933967](https://github.com/vllm-project/vllm-omni/commit/293396737de7f914cf3e8ff9441fc1004e9ae80d)

- **作者**: ChenWenjing
- **时间**: 2026-06-12T09:14:33Z
- **提交信息**: [ci]skip voxcpm2 pcm hnr test  (#4375)

Signed-off-by: CHEN <116010019@link.cuhk.edu.cn>

### [aa59dc5](https://github.com/vllm-project/vllm-omni/commit/aa59dc50c781ed11ac6eed3a8baa9fa2ceb26429)

- **作者**: tanhaoan333
- **时间**: 2026-06-12T08:54:29Z
- **提交信息**: [bugfix]VoxCPM2 audio encoder adapt other than CUDA (#4374)

Signed-off-by: tanhaoan333 <tanhaoan@huawei.com>

### [f44f3ef](https://github.com/vllm-project/vllm-omni/commit/f44f3ef9f7dc4609b52861fc1d85809b026361f9)

- **作者**: Samit
- **时间**: 2026-06-12T08:40:00Z
- **提交信息**: [platform] fix: set UnspecifiedOmniPlatform device_type to cpu (#4357)

Signed-off-by: samithuang <285365963@qq.com>

### [8f869c8](https://github.com/vllm-project/vllm-omni/commit/8f869c8ea5de06d1ab0d1914b0e1c5b62833c90d)

- **作者**: Megha Agarwal
- **时间**: 2026-06-12T07:19:14Z
- **提交信息**:  [Refactor] Output Processor Phase 2: separate multimodal output channel (#1601) (#2744)

Signed-off-by: Megha Agarwal <agarwalmegha1308@gmail.com>
Signed-off-by: meghaagr13 <divyanshsinghvi@gmail.com>
Signed-off-by: Taichang Zhou <tzhouam@connect.ust.hk>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: meghaagr13 <divyanshsinghvi@gmail.com>
Co-authored-by: Boao Shi <aoibosh@connect.hku.hk>
Co-authored-by: Taichang Zhou <tzhouam@connect.ust.hk>
Co-authored-by: Cursor <cursoragent@cursor.com>

---
