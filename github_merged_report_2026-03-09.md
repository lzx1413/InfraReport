# GitHub Stars 合并报告 - 2026-03-09

**合并日期**: 2026-03-10
**监控日期**: 2026-03-09
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


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1707
- **最后更新**: 2026-03-09T18:13:57Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Ting, Bin Jia, 鐘天楽

## AI分析总结

根据您提供的仓库README摘要和提交记录，结合VeOmni项目“为任意模态模型训练提供模型中心的分布式配方库”的核心目标，以下是昨日更新的分析总结：

### 1. 主要更新类型
*   **功能新增**：为Qwen3-MoE模型增加了MoE负载均衡监控功能；新增了AI编程智能体使用指南文档。
*   **重构**：对配置参数结构进行了重大重构（标记为BREAKING CHANGE）。
*   **文档更新**：新增了`AGENTS.md`文档。

### 2. 关键变更点及其与项目整体方向的关系
*   **MoE负载均衡监控 (#539)**：这是对**混合专家模型**这一重要架构的深度支持。监控负载均衡是保证MoE模型训练效率和效果的关键，此功能直接强化了VeOmni作为“**模型中心**”配方库的核心能力，即针对特定先进模型架构提供专业、可观测的分布式训练方案。
*   **配置参数重构 (#538)**：作为**破坏性变更**，这表明项目在快速迭代中正致力于**优化用户体验和代码可维护性**。一个清晰、合理的配置结构是复杂分布式训练系统易用性和可扩展性的基础，这与项目旨在成为广泛可用“**配方库**”的目标高度一致。
*   **AI编程智能体指南 (#544)**：新增此文档表明项目开始重视并系统化**开发者体验与协作效率**。引导开发者使用AI辅助工具，能加速配方开发、问题排查和项目贡献，间接推动生态建设，符合开源项目的发展需求。

### 3. 对项目的影响和潜在意义
*   **对用户**：配置重构短期内可能带来迁移成本，但长期将提升配置的清晰度和易用性。MoE监控功能为相关模型的研究者与工程师提供了关键的可观测性工具。
*   **对项目本身**：标志着项目从提供基础分布式训练能力，向**提供更深度、更专业的模型级优化方案**迈进。同时，通过文档和结构优化，项目正变得更加**成熟和易于参与**。

### 4. 值得关注的技术点
*   **MoE负载均衡监控的具体实现**：监控的指标维度（如专家利用率、路由分布）、数据采集与呈现方式，能反映其对大规模MoE训练问题理解的深度。
*   **配置结构重构的具体内容**：新的参数组织逻辑如何更好地分类（如模型、数据、并行、优化器）、是否支持更灵活的覆盖和继承机制，这关系到配方复用的便捷性。
*   **“AI Coding Agent”的定位**：文档是否定义了使用AI辅助开发VeOmni配方或使用VeOmni的最佳实践，这可能成为项目倡导的一种新型协作范式。

### 5. 基于项目背景的提交影响分析
VeOmni的目标是构建一个**模型中心**的分布式训练**配方库**。昨日的更新完美地体现了这一方向：
1.  **深化模型中心能力**：`MoE load balance monitoring for Qwen3-Moe` 是针对具体前沿模型（Qwen3-MoE）的**专项、深度优化**，而非通用功能。这丰富了配方库的内容，增强了其专业价值。
2.  **夯实配方库基础**：`modify args structure` 是对配方“**元数据**”和用户接口的重构。一个良好的配置系统是配方可组合、易复用的基石，此举旨在提升整个配方库的**质量、一致性和可维护性**。
3.  **拓展生态与协作边界**：`add AGENTS.md` 超越了传统技术文档范畴，引入了**AI增强开发**的工作流指导。这有助于吸引更多开发者，以更高效率为配方库贡献内容，加速项目生态发展。

**总结**：昨日的更新是一次**“向内深化核心能力，向外优化开发者体验”** 的均衡迭代。项目在持续强化其对复杂模型（如MoE）分布式训练的专业支持的同时，也开始系统性地关注其作为开源项目的易用性和协作友好性，这符合其建设一个活跃、实用配方库的长期愿景。

## 详细提交记录

### [7853fc6](https://github.com/ByteDance-Seed/VeOmni/commit/7853fc6881f927f77ef918447a0fa20d6a5220f3)

- **作者**: 鐘天楽
- **时间**: 2026-03-09T16:47:52Z
- **提交信息**: [model, logging] feat: MoE load balance monitoring for Qwen3-Moe (#539)

### [374c2d9](https://github.com/ByteDance-Seed/VeOmni/commit/374c2d94fc146100864fcfc6bebfb7177ca2ddc2)

- **作者**: Ting
- **时间**: 2026-03-09T08:03:40Z
- **提交信息**: [docs] feat: add AGENTS.md for AI coding agent instructions (#544)

### [085f3c2](https://github.com/ByteDance-Seed/VeOmni/commit/085f3c23a1ef5223f60a6a981beb891cbb3e70f7)

- **作者**: Bin Jia
- **时间**: 2026-03-09T07:59:35Z
- **提交信息**: [BREAKING][config] refactor: modify args structure (#538)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2038
- **最后更新**: 2026-03-09T08:44:33Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Chengtao Lv

## AI分析总结

根据提供的提交记录和README摘要，以下是针对仓库 'ModelTC/LightX2V' 昨日更新的分析总结：

### 1. 主要更新类型
- **文档更新**：提交 `66701fe` 的主要内容是上传了“ar document”（推测为“AR文档”，可能是“架构文档”或“自述文档”的简称）。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：新增或更新了项目的文档文件（可能涉及架构说明、使用指南或内部设计文档）。
- **与项目方向的关系**：LightX2V 定位为“轻量级视频生成推理框架”，强调高效、易用。完善的文档是开源项目成熟和推广的关键，有助于降低用户上手门槛、明确架构设计，这与项目追求“轻量、易用、高效”的整体方向一致。

### 3. 对项目的影响和潜在意义
- **积极影响**：
  - 提升项目的可访问性和易用性，帮助开发者和用户更快理解框架结构和使用方法。
  - 增强项目的专业性，促进社区协作和外部贡献。
- **潜在意义**：可能为后续功能扩展、API 标准化或社区文档体系建立基础。

### 4. 值得关注的技术点
- 本次提交为纯文档更新，无直接代码变更，因此无具体技术点可分析。但可关注文档中是否涉及：
  - 框架架构设计（如模块划分、流程说明）。
  - 性能优化指南或部署建议。
  - 与 README 中提到的“轻量推理”特性相关的设计决策。

### 5. 基于项目背景的提交影响分析
- **项目背景**（基于 README）：LightX2V 旨在提供高效的视频生成推理框架，注重轻量化、易用性和性能。
- **提交如何影响发展**：
  - **短期**：通过完善文档，提升项目形象和用户体验，可能吸引更多用户尝试或贡献。
  - **长期**：清晰的文档有助于项目维护和迭代，为框架的稳定性和生态发展奠定基础，支持其成为更成熟的视频生成工具。

---
**总结**：昨日更新是一次常规的文档维护，虽不涉及代码功能，但对项目的长期发展和用户体验有积极意义，符合开源项目成熟化的常见路径。

## 详细提交记录

### [66701fe](https://github.com/ModelTC/LightX2V/commit/66701fed28352a3320111491fafc6281e7804b5a)

- **作者**: Chengtao Lv
- **时间**: 2026-03-09T08:44:29Z
- **提交信息**: upload ar document (#931)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1950
- **最后更新**: 2026-03-09T10:43:12Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5109
- **最后更新**: 2026-03-09T16:55:51Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Martin Vit, Tian Zheng

## AI分析总结

根据对FlashInfer仓库README摘要（专注于高性能GPU推理内核）和昨日提交记录的分析，总结如下：

### 1. 主要更新类型
- **功能新增**：支持NVFP4（4位）KV缓存，扩展了低精度推理支持。
- **Bug修复**：修复了CUTLASS GEMM内核在高并发下因缺少GDC编译标志导致的NaN输出问题。

### 2. 关键变更点及其与项目整体方向的关系
- **NVFP4 KV缓存支持**：新增对4位量化KV缓存（`torch.uint8` dtype）的支持，并引入可选的缩放张量（`k_sf_cache`/`v_sf_cache`）。这与项目“高性能GPU推理内核”的目标高度一致，通过降低内存带宽需求来提升推理效率。
- **GDC编译标志修复**：为多个CUTLASS GEMM JIT模块添加了`-DCUTLASS_ENABLE_GDC_FOR_SM100=1`和`-DCUTLASS_ENABLE_GDC_FOR_SM90=1`标志，确保程序化依赖启动（PDL）的同步屏障正确生效。这直接关系到项目在高并发场景下的**稳定性和正确性**，是高性能内核可靠运行的基础。

### 3. 对项目的影响和潜在意义
- **性能与效率提升**：NVFP4支持进一步降低了KV缓存的内存占用，有助于处理更长的上下文或部署更大的模型，直接提升推理吞吐量。
- **稳定性增强**：修复了SM120（Blackwell）等新一代GPU上高并发时可能出现的严重竞态条件，防止了NaN/垃圾数据输出，提升了生产环境下的可靠性。
- **生态兼容性**：修复与SGLang等上层框架的集成问题（#2708及相关issue），增强了FlashInfer在复杂推理服务栈中的适用性。

### 4. 值得关注的技术点
- **低精度量化推理**：NVFP4（4位）KV缓存是前沿的模型压缩与加速技术，体现了对极致推理性能的追求。
- **硬件特定优化**：针对SM120（Blackwell架构）的专门支持和问题修复，表明项目紧跟最新GPU硬件发展。
- **并发安全机制**：深入利用了CUTLASS的**程序化依赖启动（PDL）**和**网格依赖控制（GDC）**等底层CUDA特性，凸显了项目对GPU内核并发编程细节的深度掌控。

### 5. 基于项目背景的提交影响分析
FlashInfer的核心目标是提供**高性能的GPU推理内核**。昨日的更新从两个关键维度推动了这一目标：
- **广度扩展（功能新增）**：通过支持**NVFP4 KV缓存**，项目覆盖了更先进的低精度推理场景，满足了业界对降低大模型推理成本与延迟的迫切需求，巩固了其作为高性能内核库的技术前沿地位。
- **深度夯实（Bug修复）**：通过修复**高并发下的GEMM竞态条件**，项目解决了在新一代硬件（SM120）上大规模服务时可能出现的根本性稳定性问题。这确保了其高性能内核在追求极致吞吐（高并发）时结果的**正确性**，这是所有性能优化的前提，对于赢得用户信任、用于生产环境至关重要。

**总结**：昨日更新是一次典型的“攻守兼备”迭代，既积极拓展了新的高性能技术前沿（NVFP4），又扎实修复了底层稳定性隐患，共同强化了FlashInfer作为**可靠、高效、前沿GPU推理内核基础设施**的定位。

## 详细提交记录

### [2bb3e9e](https://github.com/flashinfer-ai/flashinfer/commit/2bb3e9e67aa5f7b05b7f867cac780bba74bf3920)

- **作者**: Tian Zheng
- **时间**: 2026-03-09T16:55:46Z
- **提交信息**: Support NVFP4 KV cache decode on SM120 (#2520)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Supports NVFP4 KV cache.

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
* xqa and decode APIs now accept optional NVFP4 (4-bit) KV-cache scaling
tensors (k_sf_cache/v_sf_cache / kv_cache_sf); torch.uint8 KV-cache
dtype supported with runtime SM 12.x guard; docstrings updated.

* **Tests**
* Added/extended tests exercising NVFP4 KV-cache quantization, scaling
factors, uint8 KV-cache paths, and decode integration.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Tian Zheng <29906817+Tom-Zheng@users.noreply.github.com>

### [4c4013b](https://github.com/flashinfer-ai/flashinfer/commit/4c4013be053e499c919bced20ed5ed6d5f5026fb)

- **作者**: Martin Vit
- **时间**: 2026-03-09T16:44:19Z
- **提交信息**: fix(jit): GEMM kernels produce NaN under concurrency — missing GDC flags cause PDL synchronization barriers to compile as no-ops (#2716)

## Summary

All CUTLASS GEMM templates use `enablePDL=true` (Programmatic Dependent
Launch), but the JIT compilation is missing
`-DCUTLASS_ENABLE_GDC_FOR_SM100=1` and `-DCUTLASS_ENABLE_GDC_FOR_SM90=1`
compile flags. Without these flags, `wait_on_dependent_grids()` and
`launch_dependent_grids()` in CUTLASS `grid_dependency_control.h`
compile as **empty no-ops**, eliminating the synchronization barriers
needed for safe PDL execution.

## Root Cause

In `cutlass/include/cutlass/arch/grid_dependency_control.h`:

```cpp
CUTLASS_DEVICE void wait_on_dependent_grids() {
#if (defined(CUTLASS_GDC_ENABLED))  // only defined when CUTLASS_ENABLE_GDC_FOR_SM100 is set
  asm volatile("griddepcontrol.wait;");
#endif
}
```

The `CUTLASS_GDC_ENABLED` macro is only defined when
`CUTLASS_ENABLE_GDC_FOR_SM100` is passed as a compile flag. Without it,
PDL launches kernels with overlap enabled at the host level
(`cudaLaunchAttributeProgrammaticStreamSerialization`), but the
device-side synchronization barriers are compiled out — creating a race
condition.

## Symptoms

On SM120 (Blackwell RTX PRO 6000 / RTX 5090) with high concurrency (64+
simultaneous requests in SGLang with TP=8):
- CUTLASS FP4 GEMM intermittently fails to write output tiles
- Unwritten tiles contain uninitialized memory (NaN/garbage)
- NaN blocks are always contiguous and 128-aligned, matching CTA tile
boundaries
- `CUDA_LAUNCH_BLOCKING=1` eliminates the bug (confirms race condition)
- cudnn backend is unaffected (does not use CUTLASS PDL)
- Retry with identical inputs produces correct output

## Fix

Add `-DCUTLASS_ENABLE_GDC_FOR_SM100=1` and
`-DCUTLASS_ENABLE_GDC_FOR_SM90=1` to all affected GEMM JIT modules:
- `fp4_gemm_cutlass` (SM100)
- `fp4_gemm_cutlass_sm103` (SM103)
- `fp4_gemm_cutlass_sm120` (SM120)
- `fp8_gemm_cutlass` (SM100)
- `mxfp8_gemm_cutlass` (SM100)
- `gemm_sm120` (SM120 FP8 groupwise)

The `tgv_gemm` module already had `DCUTLASS_ENABLE_GDC_FOR_SM100`.

Note: `DCUTLASS_ENABLE_GDC_FOR_SM90` is needed because the SM120 CUTLASS
kernel (`sm120_gemm_tma_warpspecialized_cooperative_asymmetric_dma.hpp`)
guards `launch_dependent_grids()` with `#ifdef
CUTLASS_ENABLE_GDC_FOR_SM90` instead of `SM100` (upstream CUTLASS bug).

## Verification

| Configuration | Result |
|---|---|
| PDL=true, no GDC flags (current) | **NaN crash** under high
concurrency |
| PDL=false (workaround) | OK |
| PDL=true + GDC flags (this PR) | **OK** — tested with 64 concurrent
requests, multiple SGLang restarts from JIT cache |
| `CUDA_LAUNCH_BLOCKING=1` | OK (confirms race condition) |

## Environment

- Hardware: 8x NVIDIA RTX PRO 6000 Blackwell (SM120, 96GB)
- FlashInfer 0.6.4, CUTLASS 4.4.1
- SGLang with TP=8, EAGLE-v2, GLM-5-NVFP4-MTP model
- PyTorch 2.12.0.dev, CUDA 12.8+

## Related

- #2708
- https://github.com/sgl-project/sglang/issues/20043
- https://github.com/sgl-project/sglang/pull/20047

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

## Release Notes

**Chores**
- Updated CUDA compilation configuration for SM100 and SM90 GPU
architectures, enhancing build optimization and extending hardware
compatibility for GPU acceleration workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3135
- **最后更新**: 2026-03-09T22:16:46Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: alexzms

## AI分析总结

根据提供的仓库信息与提交记录，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **重构**：对训练框架进行了重构，将其整合到 `fastvideo/train` 目录下。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：将训练框架代码重组至 `fastvideo/train`，实现模块化。
- **与项目方向的关系**：FastVideo 项目旨在提供高效的视频处理工具（如文档和快速入门所示），重构训练框架符合其提升代码可维护性、便于用户和开发者使用的目标，有助于项目向更结构化、易扩展的方向发展。

### 3. 对项目的影响和潜在意义
- **积极影响**：
  - 提高代码组织性，降低后续开发与维护成本。
  - 为未来功能迭代（如新增训练模块或优化）奠定基础。
- **潜在意义**：可能预示着项目正进入更成熟的阶段，注重内部架构优化以支持长期发展。

### 4. 值得关注的技术点
- **模块化设计**：通过重构将训练逻辑集中管理，可能引入了更清晰的接口或配置方式。
- **协作开发**：提交由多人合作完成（Co-authored-by），反映团队协作模式。

### 5. 基于项目背景的提交影响分析
- 从 README 看，FastVideo 强调文档、快速入门和社区互动（如周会、Slack），本次重构虽不直接影响终端用户功能，但通过改善代码结构：
  - **提升开发者体验**：使贡献者更易理解和修改训练部分。
  - **支持项目可扩展性**：为后续添加视频处理相关训练特性（如模型优化、新数据集支持）提供便利，间接促进项目目标——构建高效视频工具生态的实现。

---
**总结**：昨日更新是一次以重构为主的基础设施改进，旨在优化项目内部结构，虽不直接新增用户功能，但通过增强代码组织性为 FastVideo 的长期发展和社区协作打下更好基础。

## 详细提交记录

### [bc27a03](https://github.com/hao-ai-lab/FastVideo/commit/bc27a032c587de330fd29b70dea5c02eeae6c59f)

- **作者**: alexzms
- **时间**: 2026-03-09T22:16:42Z
- **提交信息**: [feat] Refactor training framework into fastvideo/train (#1159)

Co-authored-by: Peiyuan Zhang <a1286225768@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 32972
- **最后更新**: 2026-03-09T22:04:59Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Dhruv Nair, YiYi Xu, Sayak Paul

## AI分析总结

根据提供的提交记录和README摘要（项目为HuggingFace的Diffusers库，专注于扩散模型），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：添加了Helios模块化组件（提交1）。
- **Bug修复**：修复了Helios中CPU生成器的兼容性问题（提交2）。
- **CI/CD优化**：更新了PR测试的工作流权限（提交3）。
- **测试改进**：在模块化测试中使用`tmp_path`夹具，提升测试可靠性（提交4）。

### 2. 关键变更点及其与项目整体方向的关系
- **Helios模块化集成**：新增Helios作为模块化组件，符合Diffusers库的模块化设计哲学，旨在提供灵活、可组合的扩散模型工具。
- **CPU生成器支持**：修复允许传递CPU生成器，增强了硬件兼容性，确保库能在不同资源环境下运行。
- **CI权限调整**：优化了自动化测试流程，有助于提高代码质量和安全审查效率。
- **测试标准化**：使用`tmp_path`夹具替代临时路径管理，提升测试的稳定性和可维护性，符合项目对测试严谨性的要求。

### 3. 对项目的影响和潜在意义
- **功能扩展**：Helios的加入可能引入了新的扩散模型功能或优化，丰富了库的生态系统。
- **用户体验提升**：CPU生成器修复降低了使用门槛，支持更广泛的部署场景（如无GPU环境）。
- **开发效率**：CI和测试改进有助于加速迭代，减少回归错误，促进协作开发。
- **社区贡献友好**：模块化设计和测试优化降低了外部贡献者的参与难度。

### 4. 值得关注的技术点
- **模块化架构**：Helios的实现可能涉及新的扩散模型组件或采样策略，值得关注其API设计和集成方式。
- **硬件兼容性处理**：修复中通过“patch”方式支持CPU生成器，反映了库在设备抽象层的设计考量。
- **测试最佳实践**：使用pytest的`tmp_path`夹具，体现了对测试隔离性和可重复性的重视。

### 5. 基于项目背景的提交影响分析
Diffusers库旨在提供**易用、高效的扩散模型工具**。这些提交共同推动了以下发展：
- **模块化增强**：Helios扩展了库的模块化能力，使用户能更灵活地组合扩散流程，符合项目“可定制”的核心目标。
- **稳定性和兼容性**：Bug修复和测试优化提升了库的可靠性，这对于依赖Diffusers的生产应用和研究人员至关重要。
- **自动化与协作**：CI更新强化了开发流程，支持项目在快速迭代中保持质量，适应开源社区的协作需求。

**总结**：昨日更新以功能扩展和基础设施优化为主，巩固了Diffusers作为**扩散模型标准库**的地位，同时通过兼容性改进和测试强化，提升了项目的健壮性和可访问性。

## 详细提交记录

### [068c6ef](https://github.com/huggingface/diffusers/commit/068c6ef6c16a79340d00d1069b3aa22f7acbe937)

- **作者**: YiYi Xu
- **时间**: 2026-03-09T20:37:56Z
- **提交信息**: [modular] helios (#13216)

* add helios modular

* upup

* revert change in guider

* up

* fix for real

* fix batch test

* Apply suggestion from @yiyixuxu

---------

Co-authored-by: yiyi@huggingface.co <yiyi@ip-26-0-163-127.ec2.internal>

### [94bcb89](https://github.com/huggingface/diffusers/commit/94bcb8941e2e41603671808361131e5ea348cf41)

- **作者**: DefTruth
- **时间**: 2026-03-09T20:30:56Z
- **提交信息**: fix: allow pass cpu generator for helios (#13228)

* allow pass cpu generator for helios

* allow pass cpu generator for helios

* allow pass cpu generator for helios

* patch

### [8ea908f](https://github.com/huggingface/diffusers/commit/8ea908f323ba51404b151cf2140de53fb212c88d)

- **作者**: Dhruv Nair
- **时间**: 2026-03-09T12:21:42Z
- **提交信息**: [CI] Add Workflow permissions to PR tests (#13233)

[CI] Add workflow permissions to PR tests

Co-authored-by: Copilot Autofix powered by AI <62310815+github-advanced-security[bot]@users.noreply.github.com>

### [a08c274](https://github.com/huggingface/diffusers/commit/a08c274c3326579c69b065701f0a7e1982be632a)

- **作者**: Sayak Paul
- **时间**: 2026-03-09T09:47:59Z
- **提交信息**: [tests] Use `tmp_path` fixture modular tests (#13194)

* add a test to check modular index consistency

* check for compulsory keys.

* use fixture for tmp_path in modular tests.

* remove unneeded test.

* fix code quality.

* up

* up

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 378
- **最后更新**: 2026-03-02T11:35:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 11945
- **最后更新**: 2026-03-09T18:30:36Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

根据提供的README摘要和提交记录，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增了LTX2.3版本的图像到视频（i2v）训练脚本和固定帧率（FPS）的帧重采样功能。
- **Bug修复**：修复了LTX2.3版本中训练与推理一致性的问题，并优化了视频加载兼容性。
- **代码重构**：对帧重采样器进行了重构，提升了代码结构清晰度。

### 2. 关键变更点及其与项目整体方向的关系
- **i2v训练支持**：新增LTX2.3的i2v训练脚本，扩展了模型的训练能力，符合项目作为**AI视频生成与编辑工具**的方向，增强了从静态图像生成动态视频的功能。
- **固定FPS帧重采样**：引入了按固定帧率重采样视频帧的功能，提高了视频处理的灵活性和可控性，与项目注重**高质量视频合成**的目标一致。
- **训练-推理一致性修复**：解决了LTX2.3中首帧训练与推理不一致的问题，提升了模型输出的稳定性和可靠性，支持项目向**生产级应用**发展。

### 3. 对项目的影响和潜在意义
- **功能增强**：i2v训练和固定FPS支持使项目能处理更复杂的视频生成任务，拓宽了应用场景（如影视制作、动态内容生成）。
- **稳定性提升**：Bug修复和兼容性改进减少了运行时错误，提高了用户体验和开发效率。
- **技术扩展**：为后续视频生成模型的迭代（如更高版本LTX）奠定了基础，可能吸引更多开发者贡献和用户采用。

### 4. 值得关注的技术点
- **帧重采样器重构**：可能优化了视频帧处理的性能或可维护性，值得关注其实现细节（如插值算法、内存管理）。
- **LTX2.3的LoRA支持**：提交中提到“ic lora inference&train”，暗示集成了LoRA（Low-Rank Adaptation）技术，可用于高效模型微调，适合资源受限场景。
- **视频加载兼容性**：`LoadVideo`模块支持非固定帧率视频，增强了数据处理的鲁棒性。

### 5. 基于项目背景的提交影响分析
- README显示项目聚焦于**Diffusion模型驱动的视频合成与编辑**，昨日更新直接强化了核心能力：
  - **i2v训练**：丰富了模型从图像到视频的生成链路，支持更灵活的创意工作流。
  - **固定FPS处理**：提升了视频输出的标准化程度，有助于商业应用中的格式统一需求。
  - **Bug修复**：通过提高一致性，增强了项目作为**开源视频生成框架**的可靠性，可能促进社区信任和协作。

**总结**：昨日更新以功能扩展和稳定性优化为主，紧密围绕项目“AI视频生成”的核心方向，通过增强训练能力、改进视频处理流程，推动了项目向更成熟、易用的工具发展。

## 详细提交记录

### [b272253](https://github.com/modelscope/DiffSynth-Studio/commit/b272253956d1ff9fea7156b6b38e23dff8ef6fe6)

- **作者**: Hong Zhang
- **时间**: 2026-03-09T12:32:02Z
- **提交信息**: Ltx2.3 i2v training and sample frames with fixed fps (#1339)

* add 2.3 i2v training scripts

* add frame resampling by fixed fps

* LoadVideo: add compatibility for not fix_frame_rate

* refactor frame resampler

* minor fix

### [7bc5611](https://github.com/modelscope/DiffSynth-Studio/commit/7bc5611fb8ec06b6e47eec7f6ea4b3c7b9957b42)

- **作者**: Hong Zhang
- **时间**: 2026-03-09T08:33:19Z
- **提交信息**: ltx2.3 bugfix & ic lora (#1336)

* ltx2.3 ic lora inference&train

* temp commit

* fix first frame train-inference consistency

* minor fix

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24235
- **最后更新**: 2026-03-09T21:53:15Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 16
- **主要提交者**: Mohammad Miadh Angkad, luoyuyan, Ke Bao

## AI分析总结

根据提供的提交记录和README摘要（SGLang是一个专注于高效推理和部署大语言模型的项目），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：支持新的模型/硬件（GLM5、AMD NPU、LongContext Flash Lite）、新增评估参数（min_p, chat-template）、支持返回Mamba中间状态。
- **Bug修复**：修复音频加载、扩散模型工作流、FP4 GEMM后端选择、Qwen3.5模型问题等。
- **性能优化**：针对AMD/NPU硬件的内核优化、CUDA图捕获优化、解耦架构中的队列健康检查跳过。
- **代码质量/维护**：修复lint问题、替换服务器参数突变hack为显式配置、更新CI/CD镜像位置、添加代码所有者。
- **依赖/工具更新**：视频解码库从decord替换为torchcodec。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **多硬件支持扩展** (AMD, NPU, Blackwell) | 紧扣SGLang作为“**性能导向的LLM推理框架**”的定位，通过扩展硬件生态（特别是AMD和国产NPU）来提升适用性和竞争力。 |
| **模型支持增强** (GLM5, Mamba状态返回) | 体现对**前沿模型架构**（如状态空间模型Mamba）和**热门模型**（如GLM5）的快速集成能力，保持框架的时效性。 |
| **推理优化与稳定性** (LongContext优化、注意力阈值控制、内存池配置) | 直接服务于项目的核心目标——**高效、稳定的LLM服务**。优化长上下文处理、改进资源管理，提升生产环境可靠性。 |
| **多模态后端改进** (音频、视频、扩散模型) | 强化SGLang作为**多模态推理框架**的能力，修复关键路径上的问题，确保视觉、音频等任务的稳定运行。 |

### 3. 对项目的影响和潜在意义
- **生态扩展**：加强对AMD和NPU硬件的支持，有助于吸引更广泛的用户和开发者群体，降低部署门槛。
- **生产就绪度提升**：多项Bug修复和稳定性优化（如解耦架构队列管理、显式配置）增强了框架在复杂负载下的**鲁棒性**，更适用于企业级部署。
- **开发者体验**：通过添加`CODEOWNERS`、清理代码库（lint修复、替换hack）来改善项目维护性，有利于长期发展。
- **性能边界推进**：针对Blackwell架构、长上下文、特定硬件的优化，持续**推动推理性能的极限**，巩固其技术优势。

### 4. 值得关注的技术点
1. **硬件适配精细化**：针对特定硬件架构（如SM120/Blackwell）的FP4 GEMM后端自动选择，体现了深度的性能调优。
2. **解耦架构优化**：`Skip health check enqueue when PD disagg queues have backlog`，这是对**解耦式推理架构**中流控机制的优化，对高并发场景有意义。
3. **状态空间模型支持深化**：`Return intermediate Mamba states` 为基于Mamba的模型提供了更灵活的操控能力，可能用于高级推理技巧。
4. **视频解码栈切换**：从decord迁移到torchcodec，可能出于**性能、许可证或维护性**的考虑，是多媒体处理栈的重要变更。

### 5. 基于项目背景的提交影响分析
SGLang旨在成为“LLM推理的CUDA”，即**底层高效、上层易用的推理引擎**。昨日的更新完美体现了这一战略：
- **强化核心优势**：几乎所有提交都围绕“**性能**”和“**扩展性**”展开。无论是支持新硬件、优化内核，还是修复影响稳定性的Bug，都在夯实其作为高性能推理后端的基础。
- **扩大应用场景**：通过完善多模态支持（音视频修复）和更多模型集成，使框架能覆盖更广泛的AIGC应用场景，从纯文本扩展到多模态生成。
- **构建开发者信任**：通过代码质量维护和显式API配置（替换`server_args` hack），提升了代码的**可维护性和可预测性**，这对于吸引企业用户和社区贡献者至关重要。
- **拥抱行业趋势**：积极集成GLM5、优化AMD/NPU支持，表明项目紧跟中国市场和异构计算的发展趋势，有助于其在快速变化的AI基础设施领域保持相关性。

**总结**：昨日的更新是一次典型的“夯实基础、扩展边界”的迭代。它没有引入颠覆性特性，而是通过一系列扎实的工程工作，在**硬件兼容性、运行时稳定性、模型覆盖度和代码质量**等多个维度同时推进，稳步增强SGLang作为生产级LLM推理框架的竞争力。

## 详细提交记录

### [ca997b7](https://github.com/sgl-project/sglang/commit/ca997b7ba9a4611f34208194658c42d342514a42)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-03-09T21:53:09Z
- **提交信息**: Add min_p and chat-template kwargs support to run_eval (#19571)

### [be63f98](https://github.com/sgl-project/sglang/commit/be63f982b7b7f0451a3ccbb13f6fe2ecf6c39796)

- **作者**: Baizhou Zhang
- **时间**: 2026-03-09T21:36:10Z
- **提交信息**: [V32/GLM5] Control the threshold of applying dense attention with an environ (#20062)

### [d39ed07](https://github.com/sgl-project/sglang/commit/d39ed074cf11ae9247dbcb04170e6921ca727559)

- **作者**: Martin Vit
- **时间**: 2026-03-09T21:13:08Z
- **提交信息**: fix: default FP4 GEMM backend to flashinfer_cudnn on SM120 (Blackwell) (#20047)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [61d530e](https://github.com/sgl-project/sglang/commit/61d530e8ac071dd580221ed7d74566a532ecf79f)

- **作者**: Baizhou Zhang
- **时间**: 2026-03-09T21:09:59Z
- **提交信息**: [CI] Fix lint (#20209)

### [3e8abc7](https://github.com/sgl-project/sglang/commit/3e8abc71ca50c7e3e155ffafe7b5eeac30a28b8f)

- **作者**: ybyang
- **时间**: 2026-03-09T19:58:10Z
- **提交信息**: [Disagg] Skip health check enqueue when PD disagg queues have backlog (#20191)

### [f0153ad](https://github.com/sgl-project/sglang/commit/f0153ad225bdcbdd652245e07a101379430cc0c9)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-03-09T19:52:05Z
- **提交信息**: [AMD][Feature] support fp4 dispatch and fp8 combine in moriep (#19757)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [ffb4b6f](https://github.com/sgl-project/sglang/commit/ffb4b6f4c166c6ebdd6213b169484fcf4d0baeac)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-09T18:45:54Z
- **提交信息**: [Core] Replace `server_args` mutation hack with explicit `MemoryPoolConfig` for draft worker init (#20183)

### [ecca8c5](https://github.com/sgl-project/sglang/commit/ecca8c553dc148821ad7eb3804b115968c933fd4)

- **作者**: Yuhao Yang
- **时间**: 2026-03-09T16:51:48Z
- **提交信息**: [diffusion] fix: fix diffusers backend issues in diffusion ci gt workflow (#20173)

### [f947bcb](https://github.com/sgl-project/sglang/commit/f947bcbd89e2dc5f987d14b6e90309ce95602572)

- **作者**: Ke Bao
- **时间**: 2026-03-09T15:05:47Z
- **提交信息**: Move stop words to args in send one (#20193)

### [2e444bd](https://github.com/sgl-project/sglang/commit/2e444bdced321e78283ab29bc3e6b2890a624cbf)

- **作者**: Ke Bao
- **时间**: 2026-03-09T15:05:32Z
- **提交信息**: Move stop words to args in send one (#20193)

### [eb4ba1b](https://github.com/sgl-project/sglang/commit/eb4ba1bde2548c7bf22767677f811c9451b24fbb)

- **作者**: sjqgogogogo
- **时间**: 2026-03-09T15:00:11Z
- **提交信息**: Feature/support longcat flash lite (#17838)

Co-authored-by: sunjiaqi11 <sunjiaqi11@meituan.com>
Co-authored-by: ispobock <ispobaoke@gmail.com>

### [11b76d2](https://github.com/sgl-project/sglang/commit/11b76d24dc110a9d7f77b5125b0ae9e6d3edb7f8)

- **作者**: wenxuewuhd
- **时间**: 2026-03-09T14:41:05Z
- **提交信息**: [NPU] [DLLM]DLLM LLaDA2.x graph mode support with NPU speedup modifications (#18485)

Co-authored-by: Zhang-Xiaoxue <xiaoxuezhang17@outlook.com>
Co-authored-by: dawncc <dawn.cc022@gmail.com>
Co-authored-by: lixinqi7 <li_xinqi7@163.com>
Co-authored-by: rangejay <rangejay1st@163.com>

### [d116a8c](https://github.com/sgl-project/sglang/commit/d116a8cd9442c4c273aba835cb1115dc8a38326f)

- **作者**: Xinyuan Tong
- **时间**: 2026-03-09T11:24:20Z
- **提交信息**: [Bugfix] Fix load_audio: mono before resample + use torchaudio (#20054)

### [4a75799](https://github.com/sgl-project/sglang/commit/4a757990a1d37c00a3b6ce9432d18b46d9ea2595)

- **作者**: Xinyuan Tong
- **时间**: 2026-03-09T11:23:49Z
- **提交信息**: [VLM] Replace decord with torchcodec for video decoding (#20055)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: BakerBunker <17872844+BakerBunker@users.noreply.github.com>

### [2d6eb7d](https://github.com/sgl-project/sglang/commit/2d6eb7dff0bdfe3126811844f6bc1e54b7cceffd)

- **作者**: Bingxu Chen
- **时间**: 2026-03-09T08:30:08Z
- **提交信息**: [AMD] Add lmsysorg/sglang-daily as A New AMD Daily Image Release Location (#20156)

### [b719219](https://github.com/sgl-project/sglang/commit/b719219de9fdd4306f04b24a79c71366c1c0a323)

- **作者**: Yuzhen Zhou
- **时间**: 2026-03-09T08:09:04Z
- **提交信息**: [ROCm] Use unreg path for aiter custom all-reduce during CUDA graph capture (#20155)

### [cabe171](https://github.com/sgl-project/sglang/commit/cabe171b6ce3b0d4fb25ff9c88d5743430efaca6)

- **作者**: luoyuyan
- **时间**: 2026-03-09T08:05:32Z
- **提交信息**: Fix qwen3.5 mtp eplb related issues (#19767)

### [c76251f](https://github.com/sgl-project/sglang/commit/c76251f70c68060cc452e15b211dc580600cb6b7)

- **作者**: roikoren755
- **时间**: 2026-03-09T08:04:36Z
- **提交信息**: Return intermediate Mamba states (#19716)

### [484f53c](https://github.com/sgl-project/sglang/commit/484f53c40e84b52a1062dead5b571145e2edce3c)

- **作者**: sglang-bot
- **时间**: 2026-03-09T07:27:34Z
- **提交信息**: [Minor] Add CODEOWNERS for attention/vision.py (#20166)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: 🤗 A PyTorch-native and Flexible Inference Engine with Hybrid Cache Acceleration and Parallelism for DiTs.
- **语言**: Python
- **星标数**: 1078
- **最后更新**: 2026-03-09T11:58:20Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 2
- **主要提交者**: Zhang Jason, DefTruth

## AI分析总结

根据仓库README摘要和昨日提交记录，以下是分析总结：

### 1. 主要更新类型
- **功能新增**：新增AMD GPU支持。
- **文档更新**：添加AMD GPU用户指南。
- **重构/优化**：更新架构图（v2）、移除冗余日志、抑制Torch编译日志。
- **工具/配置改进**：优化日志抑制逻辑（仅在CLI模式下生效）。

### 2. 关键变更点及其与项目整体方向的关系
- **AMD GPU支持**：扩展硬件兼容性，使项目从仅支持NVIDIA GPU扩展到AMD平台，符合“灵活推理引擎”的定位。
- **架构图更新**：反映内部架构优化，可能涉及缓存或并行机制的改进，与“混合缓存加速与并行”的核心目标一致。
- **日志优化**：减少冗余日志输出，提升用户体验和调试效率，体现对生产环境友好性的关注。

### 3. 对项目的影响和潜在意义
- **扩大用户群体**：AMD GPU支持可吸引更多开发者使用，提升项目在异构计算环境中的适用性。
- **提升稳定性与可维护性**：日志优化和架构更新有助于降低噪音，简化部署和调试流程。
- **生态扩展**：为AMD用户提供官方指南，降低入门门槛，增强社区支持。

### 4. 值得关注的技术点
- **硬件兼容性扩展**：如何通过PyTorch原生方式实现AMD GPU适配，可能涉及ROCm或HIP后端集成。
- **架构优化细节**：v2架构图可能揭示了缓存策略或并行调度的改进，值得深入查看代码变更。
- **日志抑制策略**：区分CLI与库模式的日志控制，避免影响其他PyTorch组件的调试。

### 5. 基于项目背景的提交影响分析
- **项目背景**：Cache-DiT是一个专注于DiT（Diffusion Transformers）推理加速的PyTorch原生引擎，核心优势是混合缓存和并行化。
- **发展影响**：
  - **功能完善**：AMD GPU支持使项目向“硬件无关”迈进一步，增强其作为通用推理引擎的竞争力。
  - **用户体验提升**：文档和日志优化降低了使用门槛，符合开源项目易用性迭代趋势。
  - **技术前瞻性**：架构更新可能为后续性能优化（如缓存效率、多GPU并行）奠定基础，保持技术领先性。

**总结**：昨日更新以功能扩展和体验优化为主，强化了项目的硬件兼容性和易用性，符合其作为高效、灵活推理引擎的长期目标。

## 详细提交记录

### [9891269](https://github.com/vipshop/cache-dit/commit/9891269ef9ddfa3c9dac142f8c907f856060fb2b)

- **作者**: DefTruth
- **时间**: 2026-03-09T11:58:11Z
- **提交信息**: chore: update arch v2 (#846)

### [59607e8](https://github.com/vipshop/cache-dit/commit/59607e88a608df511098d2f0d7b6f0a7c00ca701)

- **作者**: DefTruth
- **时间**: 2026-03-09T11:54:46Z
- **提交信息**: docs: Add AMD GPUs user guide (#845)

### [5dfacca](https://github.com/vipshop/cache-dit/commit/5dfaccace231d4f03bda3296980bb68e66bba97f)

- **作者**: Zhang Jason
- **时间**: 2026-03-09T11:37:21Z
- **提交信息**: feat: Add AMD GPU support (#841)

### [fef1695](https://github.com/vipshop/cache-dit/commit/fef16959599b2afaeb96ba9ba75d11db745a2895)

- **作者**: DefTruth
- **时间**: 2026-03-09T10:39:45Z
- **提交信息**: chore: remove noisy loggs (#844)

### [90bcdc4](https://github.com/vipshop/cache-dit/commit/90bcdc4702825d704a74cfbd625ab7ff1041e8a7)

- **作者**: DefTruth
- **时间**: 2026-03-09T10:04:26Z
- **提交信息**: suppress torch compile loggers (#843)

### [e0273ae](https://github.com/vipshop/cache-dit/commit/e0273ae6be24fb626b1f87595aed5da1cd8ea408)

- **作者**: DefTruth
- **时间**: 2026-03-09T09:46:10Z
- **提交信息**: chore: only suppress loggers while using cache-dit cli (#842)

* chore: only suppress loggers while using cache-dit cli

* chore: only suppress loggers while using cache-dit cli

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 72610
- **最后更新**: 2026-03-09T22:30:42Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 20
- **主要提交者**: Matthew Bonanni, Taoyu Zhu, Kevin H. Luu

## AI分析总结

根据提供的提交记录和项目README摘要（vLLM是一个致力于“Easy, fast, and cheap LLM serving for everyone”的高性能LLM推理服务引擎），以下是昨日（假设提交记录代表昨日更新）更新的要点分析：

### 1. 主要更新类型
- **性能优化**：占比最高，涉及注意力机制、CUDA图、ROCm后端等核心组件。
- **Bug修复**：包括内存管理、配置验证、脚本错误等。
- **功能新增/增强**：如支持新模型解析器、音频处理、前端预热等。
- **重构与代码清理**：包括模型运行器V2重构、重复代码合并、弃用旧功能。
- **文档更新**：安全指南增强、文档构建修复。
- **CI/测试改进**：针对ROCm、CUDA等后端的测试调整与验证。

### 2. 关键变更点及其与项目整体方向的关系
| 关键变更点 | 与项目方向的关系 |
|------------|------------------|
| **Model Runner V2 相关提交**（#36544, #35959, #35930, #36520） | 核心架构演进，旨在提升推理效率和可扩展性，直接支撑“fast and cheap”目标。 |
| **DeepSeek-V3.2 性能优化**（#34917, #35290） | 针对热门模型进行内核级优化，体现对前沿模型的高性能适配能力。 |
| **ROCm 后端改进**（#36025, #36101, #36292, #36253） | 加强对AMD硬件的支持，扩大硬件生态覆盖，符合“for everyone”的跨平台愿景。 |
| **多模态与音频支持**（#36319, #36472） | 扩展多模态（视觉、音频）推理能力，丰富应用场景。 |
| **解析器与工具链优化**（#36393, #36436, #35634） | 提升模型兼容性和开发者体验，降低集成成本。 |

### 3. 对项目的影响和潜在意义
- **性能提升**：通过CUDA图优化、注意力内核改进、ROCm后端调优，进一步降低延迟与成本。
- **稳定性增强**：修复内存管理、配置验证等Bug，减少生产环境风险。
- **生态扩展**：支持Nemotron V3等新模型，强化ROCm支持，吸引更广泛的用户与硬件厂商。
- **架构现代化**：Model Runner V2重构为未来功能迭代奠定基础，提高代码可维护性。
- **安全与文档**：细化安全配置指南，提升部署安全性。

### 4. 值得关注的技术点
- **CUDA图与内存管理优化**（#36544, #36416）：在高并发场景下可显著减少内核启动开销。
- **向量化CUDA内核替代`torch.cat`**（#34917）：针对DeepSeek-V3.2的查询拼接优化，体现深度硬件适配。
- **ROCm注意力后端默认切换准备**（#36025）：预示ROCm后端可能成为AMD平台默认选项。
- **非门控混合专家（MoE）Triton支持修复**（#36412）：对MoE模型推理性能有积极影响。
- **前端预热集成到Renderer**（#36482）：可能改善Web服务冷启动体验。

### 5. 基于项目背景的提交影响分析
vLLM的核心目标是**高效、低成本、易用的LLM服务**。昨日提交整体围绕该目标展开：
- **“Fast”方面**：多数性能优化（DeepSeek内核、ROCm优化、CUDA图）直接提升推理速度。
- **“Cheap”方面**：硬件支持扩展（ROCm）和内核优化有助于降低硬件门槛与运营成本。
- **“Easy”方面**：解析器增强、文档更新、代码重构降低了集成与维护难度。
- **“For everyone”方面**：多模态支持、安全指南完善、跨平台（AMD/Intel/NVIDIA）适配使项目更通用。

这些提交显示vLLM正从**纯文本LLM推理引擎**向**支持多模态、多硬件、多模型的全栈推理平台**演进，同时持续夯实核心性能与稳定性基础。

## 详细提交记录

### [2a194dd](https://github.com/vllm-project/vllm/commit/2a194ddd72a0cc5b6c404a694a64197d0c572f5b)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-09T22:14:51Z
- **提交信息**: [Model Runner V2] Add model_state inputs to CUDA graph capture (#36544)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [203a7f2](https://github.com/vllm-project/vllm/commit/203a7f27dac2197ddcf5bb1cfd105596a19ea990)

- **作者**: Shaun Kotek
- **时间**: 2026-03-09T22:11:41Z
- **提交信息**: add nemotron v3 reasoning parser (#36393)

Signed-off-by: Shaun Kotek - Nvidia <skotek@nvidia.com>
Co-authored-by: root <root@gpu-259.slurm-workers-slurm.slurm.svc.cluster.local>

### [483463f](https://github.com/vllm-project/vllm/commit/483463f735c41c36a41431044fa537dc4c81fc3c)

- **作者**: Lucas Wilkinson
- **时间**: 2026-03-09T20:58:45Z
- **提交信息**: [MRV2] Extensible CG dispatch rework  (#35959)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>

### [4e571ce](https://github.com/vllm-project/vllm/commit/4e571ce6433b6768950becda40d55cb4f24741ce)

- **作者**: Matthew Bonanni
- **时间**: 2026-03-09T18:43:06Z
- **提交信息**: [MTP][Misc] Clean up dead code (#36507)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [4ff9b04](https://github.com/vllm-project/vllm/commit/4ff9b045fe7a9da9b5a7737407ed4e7ef203ffad)

- **作者**: Micah Williamson
- **时间**: 2026-03-09T18:27:55Z
- **提交信息**: [ROCm][CI] Prep Tests For Change To ROCM_ATTN As New Default Backend On ROCm (#36025)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [3fd03f1](https://github.com/vllm-project/vllm/commit/3fd03f1ec29cf9ac20584ad68156fc7279387979)

- **作者**: Lucas Kabela
- **时间**: 2026-03-09T18:22:05Z
- **提交信息**: [BE] Rename `should_torch_compile_mm_vit` to `should_torch_compile_mm_encoder` (#36281)

Signed-off-by: Lucas Kabela <lucaskabela@meta.com>

### [10a5f4d](https://github.com/vllm-project/vllm/commit/10a5f4d53d0dc7390802ad99bf5d27b2423094e9)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-09T18:17:34Z
- **提交信息**: [Model Runner V2] Use NamedTuple for `execute_model_state` (#35930)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [fe0c085](https://github.com/vllm-project/vllm/commit/fe0c085c28dc5703da33ac3c329fb4370a798798)

- **作者**: Simon Mo
- **时间**: 2026-03-09T18:16:50Z
- **提交信息**: [Docs] Remove the reo beacon (#36528)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [8d6b3d5](https://github.com/vllm-project/vllm/commit/8d6b3d5dda293231c7c2fc9301002113f270a534)

- **作者**: Taneem Ibrahim
- **时间**: 2026-03-09T18:14:11Z
- **提交信息**: [Misc] Refactored 5 duplicate helper functions that were copied-pasted across multiple parsers (#36436)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [4b87ffb](https://github.com/vllm-project/vllm/commit/4b87ffbefb3881a0a33f9c1cb7121429bddad666)

- **作者**: Copilot
- **时间**: 2026-03-09T18:04:40Z
- **提交信息**: [torch.compile] Rename `compile_ranges_split_points` to `compile_ranges_endpoints` (#36027)

Signed-off-by: Luka Govedič <ProExpertProg@users.noreply.github.com>
Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>
Co-authored-by: ProExpertProg <11367180+ProExpertProg@users.noreply.github.com>
Co-authored-by: Luka Govedič <ProExpertProg@users.noreply.github.com>

### [fa02820](https://github.com/vllm-project/vllm/commit/fa028207aa9d4baa6cfc4863f6f54c4277884e6e)

- **作者**: Shaun Kotek
- **时间**: 2026-03-09T18:01:18Z
- **提交信息**: Fix/resupport nongated fused moe triton (#36412)

Signed-off-by: Shaun Kotek - Nvidia <skotek@nvidia.com>
Signed-off-by: Natan Bagrov <nbagrov@nvidia.com>
Signed-off-by: Daniel Serebrenik <daserebrenik@nvidia.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Signed-off-by: liweiguang <codingpunk@gmail.com>
Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: wang.yuqi <noooop@126.com>
Signed-off-by: Alex Brooks <albrooks@redhat.com>
Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>
Signed-off-by: cong-or <conchubhar.gannon@gmail.com>
Signed-off-by: Tushar Shetty <tushar.shetty@abbyy.com>
Signed-off-by: Tushar Shetty <54362365+tusharshetty61@users.noreply.github.com>
Signed-off-by: jiang1.li <jiang1.li@intel.com>
Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Signed-off-by: Xin Yang <xyangx@amazon.com>
Signed-off-by: Kevin H. Luu <khluu000@gmail.com>
Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Co-authored-by: nvnbagrov <nbagrov@nvidia.com>
Co-authored-by: Sage <80211083+sagearc@users.noreply.github.com>
Co-authored-by: danisereb <daserebrenik@nvidia.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Weiguang Li <codingpunk@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>
Co-authored-by: wang.yuqi <yuqi.wang@daocloud.io>
Co-authored-by: Alex Brooks <albrooks@redhat.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: cong-or <conchubhar.gannon@gmail.com>
Co-authored-by: Tushar Shetty <54362365+tusharshetty61@users.noreply.github.com>
Co-authored-by: liuzhenwei <zhenwei.liu@intel.com>
Co-authored-by: Xin Yang <105740670+xyang16@users.noreply.github.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [d460a18](https://github.com/vllm-project/vllm/commit/d460a18fc656f7fb217b977d4c2ee1003af2a5b6)

- **作者**: Russell Bryant
- **时间**: 2026-03-09T17:43:42Z
- **提交信息**: [Docs] Expand --allowed-media-domains security guidance with threat details (#36506)

Signed-off-by: Russell Bryant <rbryant@redhat.com>

### [6e956d9](https://github.com/vllm-project/vllm/commit/6e956d9eca398005929d29f123607d1029800cc7)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-09T17:20:13Z
- **提交信息**: [Model Runner V2] Add dummy profile_cudagraph_memory API (#36520)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [1e0f917](https://github.com/vllm-project/vllm/commit/1e0f917b349338ac09377dd277ded5e1e62df77e)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-09T17:07:44Z
- **提交信息**: [ROCm][CI] Fix logprob divergence for TitanML/tiny-mixtral under AITER rms_norm (#36101)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [c174d54](https://github.com/vllm-project/vllm/commit/c174d54f86aa10e63ae236dc09f05f821134d469)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-09T17:02:41Z
- **提交信息**: [ROCm][CI] Fix ROCm attention backend validation for head sizes, block sizes, and compute capability checks (#36292)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [55d27cc](https://github.com/vllm-project/vllm/commit/55d27cca55310a04fb82c90d26a5afed90f01de7)

- **作者**: SoluMilken
- **时间**: 2026-03-09T17:00:12Z
- **提交信息**: [Misc] fix typo: dependant -> dependent (2 lines change) (#36511)

Signed-off-by: SoluMilken <ypiheyn.imm02g@g2.nctu.edu.tw>

### [580864d](https://github.com/vllm-project/vllm/commit/580864d81eb03d9fb1383e1782636ff6a9425fa2)

- **作者**: Roberto L. Castro
- **时间**: 2026-03-09T16:50:36Z
- **提交信息**: [Attention][Perf][Kernel] Replace torch.cat with vectorized CUDA kernel MLA query concat - DeepSeek-V3.2 (#34917)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Signed-off-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [2b28b9b](https://github.com/vllm-project/vllm/commit/2b28b9b269e18cfe42c7e945d1da8d1c40989efa)

- **作者**: Roberto L. Castro
- **时间**: 2026-03-09T16:46:57Z
- **提交信息**: [Attention][Perf] Optimize cp_gather_and_upconvert_fp8_kv_cache - DeepSeek-v3.2 (#35290)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [70485a1](https://github.com/vllm-project/vllm/commit/70485a11bd83afa50e6ecc8e9619d9bdd0ff2039)

- **作者**: Taoyu Zhu
- **时间**: 2026-03-09T16:30:35Z
- **提交信息**: [ROCM] Optimize the fused_topk_bias to use aiter instead of fallback torch ops. (#36253)

Signed-off-by: zhutaoyu <zhutaoyu97@gmail.com>

### [74a9f54](https://github.com/vllm-project/vllm/commit/74a9f54cdb07eca31036d96390db968b780e44f5)

- **作者**: Harry Mellor
- **时间**: 2026-03-09T16:06:19Z
- **提交信息**: [CI] Fix edge case that could lead to broken docs builds on main (#36515)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [00c4cb5](https://github.com/vllm-project/vllm/commit/00c4cb5606ae4f7ba80485f4a2756df33a2d4065)

- **作者**: Matthew Bonanni
- **时间**: 2026-03-09T15:56:00Z
- **提交信息**: [Bugfix] Clear stale CG keys after memory profiling (#36416)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [941e52c](https://github.com/vllm-project/vllm/commit/941e52c29813ed75b3382f2a0d74ad5f168fc046)

- **作者**: Wentao Ye
- **时间**: 2026-03-09T15:33:46Z
- **提交信息**: [Refactor] Simplify `chat_completion_full_generator` for tool parsers (#35634)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [be292b7](https://github.com/vllm-project/vllm/commit/be292b7c14e08e6e6883d5ebee79240d04814159)

- **作者**: Wentao Ye
- **时间**: 2026-03-09T15:17:45Z
- **提交信息**: [Bug] Fix pooling model benchmark script (#36300)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [77a7345](https://github.com/vllm-project/vllm/commit/77a73458e3ae8b5b7a2a13f78d3a6b4d39b1414d)

- **作者**: Matthew Bonanni
- **时间**: 2026-03-09T14:17:14Z
- **提交信息**: Reapply [Attention] Refactor `check_and_update_config` (#35122)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [5578f2a](https://github.com/vllm-project/vllm/commit/5578f2a4d33b3451203fa5d43e4e6847c00b55c6)

- **作者**: Tianyu Guo
- **时间**: 2026-03-09T14:16:44Z
- **提交信息**: Support online use_audio_in_video (#36319)

Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [3ec2115](https://github.com/vllm-project/vllm/commit/3ec2115015334e26b00bb2b4cadc2587138c5948)

- **作者**: Cyrus Leung
- **时间**: 2026-03-09T13:03:21Z
- **提交信息**: [Frontend] Move warmup into Renderer (#36482)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [b0906d8](https://github.com/vllm-project/vllm/commit/b0906d8b02681d8d8f0709f0cc730f5fe845b5b1)

- **作者**: Isotr0py
- **时间**: 2026-03-09T10:43:44Z
- **提交信息**: [MM Encoder] Default to use TORCH_SDPA backend for ViT on Volta/Turing GPU (#36472)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [aaf5fa9](https://github.com/vllm-project/vllm/commit/aaf5fa9abfb7c265ccfe00480c349870a72b7209)

- **作者**: Kevin H. Luu
- **时间**: 2026-03-09T10:43:26Z
- **提交信息**: [ci] Bound openai dependency to 2.24.0 (#36471)

Signed-off-by: Kevin H. Luu <khluu000@gmail.com>

### [f96c3ab](https://github.com/vllm-project/vllm/commit/f96c3ab08cc75f18d40892ef59b6f295e71ffe83)

- **作者**: Cyrus Leung
- **时间**: 2026-03-09T10:43:23Z
- **提交信息**: [Deprecation][1/2] Remove items deprecated in v0.18 (#36470)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-10
**监控日期**: 2026-03-09
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 2976
- **最后更新**: 2026-03-09T19:58:47Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 10
- **主要提交者**: Samit, Yuanheng Zhao, Ricardo Noriega

## AI分析总结

根据提供的 `vllm-project/vllm-omni` 仓库的提交记录和 README 摘要（项目定位为“为所有人提供简单、快速、廉价的全模态模型服务”），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：新增 Stable Audio Diffusion 在线服务端点、为 Kubernetes 部署添加 Helm Chart、支持 Bagel 模型的多阶段图生图功能。
- **Bug修复**：修复 Qwen3-TTS 模型上下文问题、修复扩散模型中 CPU 卸载与 Cache-DiT 的兼容性问题、解决 Whisper 模型 GPU 内存未释放及 Qwen3-omni 模型测试精度问题。
- **性能优化**：针对单阶段扩散模型服务（Wan2.2）减少 IPC 开销。
- **文档更新**：修正 CLI 参数命名风格。
- **其他/维护**：在 CI 配置中禁用 mm processor cache、开发分支的 rebase 操作。

### 2. 关键变更点及其与项目整体方向的关系
- **扩展服务能力**：新增 `v1/audio/generate` 音频生成端点，直接强化了项目的“全模态”服务能力，从文本/图像扩展至音频。
- **提升部署灵活性**：引入 Helm Chart，使项目能更便捷地部署在 Kubernetes 集群上，这与“为所有人”提供服务的易用性和可扩展性目标高度一致。
- **增强模型功能与稳定性**：对 Qwen3-TTS、扩散模型、Whisper、Qwen3-omni 等多个核心模型的修复和功能增强，确保了多模态服务的可靠性和功能完整性。
- **优化服务性能**：针对扩散模型服务的 IPC 优化，直接服务于“快速”和“廉价”（资源高效）的核心目标。

### 3. 对项目的影响和潜在意义
- **用户体验提升**：用户现在可以更稳定地使用音频生成、图生图等高级功能，并且部署选择更多样化（Kubernetes）。
- **开发者体验改善**：文档修正和部署工具（Helm）的加入，降低了使用和集成的门槛。
- **系统健壮性增强**：一系列内存管理和模型精度的修复，减少了生产环境中的潜在故障点，提升了服务可靠性。
- **性能基准提高**：针对特定模型的性能优化，为处理高负载场景提供了更好的基础。

### 4. 值得关注的技术点
- **多模态模型深度集成**：提交涉及音频（Stable Audio Diffusion, Qwen3-TTS, Whisper）、图像（Diffusion, Bagel, Wan2.2）等多种模态，体现了项目在统一服务框架下整合复杂模型的工程能力。
- **资源管理优化**：`CPU offloading and Cache-DiT` 的兼容性修复及 `IPC overhead` 的减少，展示了在有限硬件资源下高效运行大模型的精细调优。
- **云原生部署**：`Helm Chart` 的引入标志着项目正式拥抱云原生生态，便于在现代化基础设施上规模化部署。
- **测试与质量保障**：专门提交解决模型测试中的内存和精度问题，说明项目对服务质量的重视。

### 5. 基于项目背景的提交影响分析
vLLM-Omni 的目标是成为**简单、快速、廉价的全模态模型服务框架**。昨日的更新从多个维度推动了这一目标：
- **“全模态” (Omni-modality)**：通过新增音频生成端点和支持更复杂的图生图流程，**丰富了所支持的模态和任务**，使框架更加“全能”。
- **“为所有人” (for everyone)**：提供 Helm Chart 极大地**简化了在主流云平台上的部署流程**，降低了使用门槛。修复各种模型 Bug 则**提升了服务的普适性和稳定性**，让更多用户和开发者能可靠地使用。
- **“快速”和“廉价” (fast, and cheap)**：对扩散模型服务的 IPC 优化和内存管理修复，直接**提升了推理效率并优化了资源利用率**，有助于降低延迟和运行成本。
- **整体发展**：这些提交表明项目正处于**功能快速扩展、系统持续稳定化、并积极构建开发者生态**的阶段。它正从一个核心推理引擎，向一个包含完整部署工具链和覆盖更广模态的成熟服务平台演进。

## 详细提交记录

### [7a56049](https://github.com/vllm-project/vllm-omni/commit/7a560492a2fd4fb17ffd2ded65a214f915567cff)

- **作者**: Ekagra Ranjan
- **时间**: 2026-03-09T17:36:46Z
- **提交信息**: Add online serving to Stable Audio Diffusion and introduce `v1/audio/generate` endpoint (#1255)

### [761eff9](https://github.com/vllm-project/vllm-omni/commit/761eff930a341469da25328196140ea1088a798e)

- **作者**: Sy03
- **时间**: 2026-03-09T17:36:27Z
- **提交信息**: [Fix][Qwen3-TTS] Preserve ref_code decoder context for Base ICL (#1731)

### [112a9aa](https://github.com/vllm-project/vllm-omni/commit/112a9aa237049f790bf50fcdf3c1a905aa50e1f4)

- **作者**: Ricardo Noriega
- **时间**: 2026-03-09T16:02:23Z
- **提交信息**: [Feature] Add Helm Chart to deploy vLLM-Omni on Kubernetes (#1337)

Signed-off-by: Ricardo Noriega De Soto <rnoriega@redhat.com>

### [e79ad8d](https://github.com/vllm-project/vllm-omni/commit/e79ad8d59a9be3e5b437a5d49f887c643cfd6f14)

- **作者**: Didan Deng
- **时间**: 2026-03-09T15:35:45Z
- **提交信息**: [Doc] CLI Args Naming Style Correction (#1750)

Signed-off-by: Didan Deng <33117903+wtomin@users.noreply.github.com>

### [82f63a4](https://github.com/vllm-project/vllm-omni/commit/82f63a4403624ee3b81b2315909a89a27dacac1b)

- **作者**: Yuanheng Zhao
- **时间**: 2026-03-09T14:25:41Z
- **提交信息**: [BugFix] Enable CPU offloading and Cache-DiT together on Diffusion Model (#1723)

Signed-off-by: Yuanheng Zhao <jonathan.zhaoyh@gmail.com>
Signed-off-by: yuanheng <jonathan.zhaoyh@gmail.com>

### [7271116](https://github.com/vllm-project/vllm-omni/commit/727111697359c783b7f28428c4a2124ba11cf429)

- **作者**: 汪志鹏
- **时间**: 2026-03-09T14:23:50Z
- **提交信息**: [Bagel]: Support multistage img2img (#1669)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>

### [5628d41](https://github.com/vllm-project/vllm-omni/commit/5628d41242cf1d30a82e50f46fc75967f0d560ad)

- **作者**: wangyu
- **时间**: 2026-03-09T13:52:56Z
- **提交信息**: [Test] Solving the Issue of Whisper Model's GPU Memory Not Being Successfully Cleared and the Occasional Accuracy Problem of the Qwen3-omni Model Test (#1744)

Signed-off-by: yenuo26 <410167048@qq.com>

### [155856f](https://github.com/vllm-project/vllm-omni/commit/155856ff3008617b8a275cec698926e74bb76814)

- **作者**: Samit
- **时间**: 2026-03-09T11:03:51Z
- **提交信息**: [Perf] Reduce IPC overhead for single-stage diffusion serving for Wan2.2 (#1715)

Signed-off-by: samithuang <285365963@qq.com>
Signed-off-by: Samit <285365963@qq.com>

### [89b527e](https://github.com/vllm-project/vllm-omni/commit/89b527e53301878bba33ba4a5a30a1c3207376dc)

- **作者**: Zhou Taichang
- **时间**: 2026-03-09T09:29:38Z
- **提交信息**: Dev/rebase v0170 (#1639)

Signed-off-by: Taichang Zhou <tzhouam@connect.ust.hk>
Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: Zhou Taichang <tzhouam@connect.ust.hk>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>

### [4db10d6](https://github.com/vllm-project/vllm-omni/commit/4db10d6dec8c8293df9cafe9781b990ac38440f6)

- **作者**: Yueqian Lin
- **时间**: 2026-03-09T07:42:15Z
- **提交信息**: Disable mm processor cache in CI stage configs (#1739)

Signed-off-by: linyueqian <linyueqian@outlook.com>

---
