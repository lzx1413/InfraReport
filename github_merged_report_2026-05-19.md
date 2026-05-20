# GitHub Stars 合并报告 - 2026-05-19

**合并日期**: 2026-05-20
**监控日期**: 2026-05-19
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


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1929
- **最后更新**: 2026-05-19T23:30:59Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Bin Jia, Coach257, Ting

## AI分析总结

好的，这是对ByteDance-Seed/VeOmni仓库昨日提交记录的分析总结：

### 1. 主要更新类型

- **性能优化与Bug修复**：提交 `a4ed599` 和 `47f821c` 专注于移除生产路径中的CPU同步操作，这既是性能优化，也修复了潜在的同步问题。
- **重构与重大变更**：提交 `a27a564` 标记为 `[BREAKING]`，是一个名为“cleanup v4”的重构操作，意味着引入了不向后兼容的变更。
- **文档更新**：提交 `666fc2b` 修复了文档构建问题，属于文档维护。

### 2. 关键变更点及其与项目整体方向的关系

- **移除生产路径CPU同步**：
  - **变更点**：在 `Qwen3-VL`、`VL-MoE`、`Omni-MoE` 以及 `Qwen3.5`、`Qwen3.5-MoE` 等模型补丁中，移除了生产路径上的CPU同步操作。
  - **与项目方向的关系**：VeOmni的目标是“Scaling Any Modality Model Training”（扩展任意模态模型训练），核心是提供高效的分布式训练方案。CPU同步是分布式训练中常见的性能瓶颈，移除它们直接提升了训练效率和吞吐量，与项目核心目标高度一致。

- **“Cleanup v4”重构**：
  - **变更点**：这是一个标记为 `[BREAKING]` 的重大重构，涉及CI（持续集成）和模型模块。
  - **与项目方向的关系**：作为“v4”版本的重构，这通常意味着对代码库进行大规模清理、模块化或架构调整。这为未来支持更多模型、更复杂的训练策略（如更大的模型规模、更多模态）奠定更清晰、更可维护的基础。虽然短期内可能带来兼容性问题，但长期看是项目健康发展的必要步骤。

- **修复文档构建**：
  - **变更点**：修复了文档构建过程中的问题。
  - **与项目方向的关系**：VeOmni提供了详细的文档（`Documentation-blue` 徽章指向 `veomni.readthedocs.io`）。确保文档能够正确构建，是保证用户和开发者能够顺利上手、理解和使用该项目的基础，对项目的推广和社区建设至关重要。

### 3. 对项目的影响和潜在意义

- **性能提升**：移除CPU同步将直接减少GPU等待时间，提高模型训练时的GPU利用率，从而加快训练速度。这对于需要大规模训练的多模态模型尤为重要。
- **代码质量与可维护性提升**：“Cleanup v4”重构虽然带来破坏性变更，但会显著提升代码库的整洁度、模块化程度和可扩展性，降低未来开发和维护的成本。
- **用户体验改善**：修复文档构建确保了文档的可用性，降低了新用户的学习门槛，有助于吸引更多用户和贡献者。
- **潜在风险**：`[BREAKING]` 变更意味着用户需要更新其代码或配置才能适配新版本，短期内可能造成不便。

### 4. 值得关注的技术点

- **生产路径CPU同步**：这是一个典型的分布式训练性能优化点。在PyTorch等框架中，不当的`.item()`调用或同步操作会导致CPU和GPU之间不必要的等待。VeOmni团队主动识别并移除这些瓶颈，体现了其对性能的极致追求。
- **模型补丁（Patches）**：提交中多次提到“patches”，说明VeOmni通过补丁机制来适配不同的模型架构（如Qwen3-VL, VL-MoE等）。这种设计模式使得项目能够灵活地支持新模型，同时保持核心框架的稳定。
- **`[BREAKING]` 标记**：这是一个清晰的版本管理信号，表明项目进入了新的发展阶段，开发者需要关注版本迁移指南。

### 5. 基于项目背景，这些提交如何影响项目发展

- **强化核心优势**：VeOmni的定位是“Model-Centric Distributed Recipe Zoo”（以模型为中心的分布式配方动物园）。通过持续优化性能（移除CPU同步）和重构代码（Cleanup v4），项目正在不断打磨其核心的分布式训练引擎，使其更高效、更健壮。这直接增强了其作为“配方动物园”的吸引力——用户不仅能有现成的训练配方，还能获得顶级的训练性能。
- **为扩展性铺路**：多模态模型（如Qwen3-VL、VL-MoE）的训练复杂度极高。通过重构和性能优化，VeOmni正在为其“Scaling Any Modality”的愿景扫清障碍。一个更干净、更高效的代码库，能够更容易地集成新的模型架构、新的模态（如视频、音频）以及更大规模的训练任务。
- **提升项目成熟度**：从“Cleanup v4”和文档修复可以看出，项目正在从快速原型阶段向更稳定、更成熟的工程化阶段迈进。这对于吸引企业级用户和严肃的学术研究者至关重要。

## 详细提交记录

### [a4ed599](https://github.com/ByteDance-Seed/VeOmni/commit/a4ed599119afb21f5e559f15e95635f0edbbc5c6)

- **作者**: Ting
- **时间**: 2026-05-19T23:30:54Z
- **提交信息**: [model, perf] fix: remove production-path CPU syncs from Qwen3-VL / VL-MoE / Omni-MoE patches (#764)

### [47f821c](https://github.com/ByteDance-Seed/VeOmni/commit/47f821c6f9ced56347dd128e3d8e78a3bc106dc2)

- **作者**: Ting
- **时间**: 2026-05-19T20:54:46Z
- **提交信息**: [model, perf] fix: remove production-path CPU syncs from Qwen3.5 / Qwen3.5-MoE patches (#762)

### [a27a564](https://github.com/ByteDance-Seed/VeOmni/commit/a27a564b8f80b338f3fa218f3dad0c9ba1dae18a)

- **作者**: Coach257
- **时间**: 2026-05-19T11:20:04Z
- **提交信息**: [BREAKING][ci, model] feat: cleanup v4 (#768)

### [666fc2b](https://github.com/ByteDance-Seed/VeOmni/commit/666fc2b51fd4f54562625e878e36193e0e0b8866)

- **作者**: Bin Jia
- **时间**: 2026-05-19T07:48:56Z
- **提交信息**: [docs] fix: fix doc build (#769)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2275
- **最后更新**: 2026-05-19T11:42:25Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: xly

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 1. 主要更新类型

*   **Bug修复**：两项提交均属于Bug修复。`#1078` 修复了INT8 Triton GEMM内核中的逻辑缺陷，`#1077` 修复了Wan视频生成模型特征缓存中的条件控制状态管理问题。
*   **代码重构/清理**：`#1077` 移除了冗余的独立状态标志，将状态管理统一到调度器，属于代码重构。

### 2. 关键变更点及其与项目整体方向的关系

*   **`#1078` (INT8 Triton GEMM修复)**：
    *   **变更点**：修复了`EVEN_K`（判断K维度是否对齐）的计算逻辑，从硬编码判断改为基于内核参数动态计算；修正了默认输出数据类型为`torch.float16`；增强了非对齐形状下的内存访问安全性。
    *   **与项目方向关系**：LightX2V是一个**轻量级视频生成推理框架**，其核心目标之一是**高性能**。INT8量化是提升推理速度、降低显存占用的关键技术。此修复确保了INT8内核在更多样化的模型形状（如非对齐的K维度）下也能正确、稳定地运行，直接支撑了框架的**高性能和通用性**目标。

*   **`#1077` (Wan特征缓存CFG状态修复)**：
    *   **变更点**：将Wan模型中特征缓存的条件/无条件（CFG）状态来源，从Transformer内部维护的独立标志，改为统一读取调度器（`scheduler`）的状态。
    *   **与项目方向关系**：Wan是一个流行的视频生成模型。特征缓存是提升视频生成效率（特别是长视频生成）的关键优化。此修复解决了因状态不同步导致的**生成错误或质量下降**问题，确保了框架对Wan等先进模型的高效、正确支持，体现了项目**对主流模型生态的兼容性和稳定性**的重视。

### 3. 对项目的影响和潜在意义

*   **`#1078`**：
    *   **影响**：提升了INT8推理的**鲁棒性和正确性**，尤其是在处理非标准形状的模型时。同时，通过更精确的`EVEN_K`判断，可能在某些场景下带来微小的性能提升。
    *   **潜在意义**：为未来支持更多需要INT8量化的视频生成模型铺平了道路，增强了框架作为高性能推理后端的可靠性。

*   **`#1077`**：
    *   **影响**：彻底解决了Wan模型在使用特征缓存时可能出现的**状态不一致Bug**，提高了生成结果的稳定性和可复现性。
    *   **潜在意义**：通过将状态管理逻辑集中到调度器，简化了模型代码，降低了未来维护和扩展的复杂性。这体现了项目在架构设计上追求**清晰、解耦**的工程理念。

### 4. 值得关注的技术点

*   **`triton.heuristics`**：`#1078` 使用Triton的`heuristics`装饰器来动态决定`EVEN_K`，这是一种优雅且高效的Triton内核优化技巧，避免了在Python包装层进行硬编码判断。
*   **单一事实来源（Single Source of Truth）**：`#1077` 的核心思想是将状态管理统一到调度器，这是软件工程中一个重要的设计原则，可以有效避免因状态分散导致的Bug。
*   **测试覆盖**：两个提交都强调了测试。`#1078` 增加了对多种K值和非对齐形状的测试；`#1077` 重写了回归测试。这表明项目对代码质量和正确性有严格要求。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **巩固基础，提升可靠性**：LightX2V定位为“轻量级”和“推理框架”。`#1078` 对核心算子的修复和`#1077` 对模型集成逻辑的修复，共同提升了框架的**稳定性和正确性**，这是任何框架赢得用户信任的基础。
*   **加速主流模型支持**：Wan是当前热门的视频生成模型。`#1077` 的修复确保了LightX2V能**稳定、高效地运行Wan模型**，这对于吸引用户、验证框架价值至关重要。
*   **为性能优化扫清障碍**：INT8是重要的性能优化手段。`#1078` 的修复确保了这项优化是**正确且鲁棒**的，使得开发者可以放心地依赖INT8来加速推理，而不用担心产生错误结果。这直接推动了项目“高性能”目标的实现。
*   **体现工程严谨性**：两个提交都涉及对细节的打磨（如数据类型、状态同步），并附有详细的验证步骤。这表明项目团队注重代码质量和工程实践，这对于一个开源框架的长期健康发展非常有利。

## 详细提交记录

### [522609e](https://github.com/ModelTC/LightX2V/commit/522609ecc121b49c20d201b3f00c3dc052821bce)

- **作者**: xly
- **时间**: 2026-05-19T09:03:07Z
- **提交信息**: Fix INT8 Triton GEMM review follow-ups for #896 (#1078)

## Summary
- keep the #896 correctness fix and tighten the Triton `EVEN_K` decision
per autotune config with `triton.heuristics`
- keep masked scale / bias loads for non-tile `M/N` safety
- extend CUDA coverage for bias/no-bias, `K=64/127/129/192`, non-tile
`M/N`, and random scale / bias cases

## Details
- compute `EVEN_K` as `K % (BLOCK_K * SPLIT_K) == 0` inside the INT8
Triton kernels instead of hard-coding the wrapper decision against `128`
- preserve the corrected default output dtype of `torch.float16`
- add dtype-aware tolerances for random correctness tests

## Validation
- `conda run -n exp_env env CUDA_VISIBLE_DEVICES=1 python -m pytest -q
test_cases/test_int8_triton_kernels.py`
- `git diff --check`
- `pre-commit run --files lightx2v/common/ops/mm/triton_kernels.py
test_cases/test_int8_triton_kernels.py`
- local performance sanity against `main` for aligned `K=128` shapes
showed no meaningful regression

### [d9f6816](https://github.com/ModelTC/LightX2V/commit/d9f68165307aa588d6eb9537ad858eacd570ae34)

- **作者**: xly
- **时间**: 2026-05-19T08:42:30Z
- **提交信息**: Fix Wan feature cache CFG status toggle (#1077)

## Summary
This PR fixes the Wan feature-caching CFG state handling by using
`scheduler.infer_condition` as the single source of truth.

`WanModel._infer_cond_uncond()` already sets
`self.scheduler.infer_condition` before each conditional/unconditional
inference pass. The feature-caching transformer now reads that scheduler
state directly instead of keeping a separate `infer_conditional` flag.

## Changes
- remove the separate Wan transformer `infer_conditional` /
`switch_status()` state
- update Wan feature-caching branches to read
`self.scheduler.infer_condition` directly
- replace the old switch-status regression test with a scheduler-state
regression test for `WanTransformerInferFirstBlock`

## Validation
- reproduced the original missing-state issue before the first fix
- verified the updated regression test with:
  ```bash
  HOME=/tmp XDG_CACHE_HOME=/tmp SKIP_PLATFORM_CHECK=1 \
conda run -n exp_env python -B -m unittest
test_cases.test_wan_feature_cache_cfg_state
  ```
- verified there are no remaining `infer_conditional` / `switch_status`
references under Wan code
- ran `pre-commit run --files` on the touched files

## Notes
This PR only changes the CFG state source used by Wan feature caching.
It does not change `BaseTransformerInfer` or `scheduler.infer_condition`
setup.

Closes #902

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2083
- **最后更新**: 2026-05-20T00:01:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5638
- **最后更新**: 2026-05-19T21:54:15Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Duncan Moss, Jiahan Chang (Cyrus), Igor Shovkun

## AI分析总结

好的，作为专业的代码分析助手，以下是对仓库 `flashinfer-ai/flashinfer` 昨日提交记录的分析总结。

### 项目背景回顾
FlashInfer 是一个专注于**高性能 GPU 推理内核**的库。其核心目标是提供针对大语言模型（LLM）推理场景优化的、高度优化的 CUDA 内核，以提升吞吐量和降低延迟。项目通常与 vLLM 等推理框架深度集成。

### 昨日更新要点分析

#### 1. 主要更新类型
- **功能新增**：这是昨日更新的核心。新增了 Mamba2 模型专用的 `checkpointing_ssu` 融合内核，并为 Gemma/Qwen3.5 模型扩展了 RMSNorm 融合功能。
- **Bug 修复**：修复了 BF16 数据类型在解码时对非连续状态池（padded/non-contiguous state pool）的处理问题。
- **性能优化**：通过融合内核（`checkpointing_ssu`）和减少 HBM 访问（条件性状态写入），显著优化了 Mamba2 模型的推理性能。
- **依赖/集成更新**：更新了 TensorRT-LLM (trtllm) 的 FMHA (Flash Multi-Head Attention) 内核的二进制文件（cubins）和参数 ABI，以保持与上游框架的兼容性。

#### 2. 关键变更点及其与项目方向的关系
- **Mamba2 `checkpointing_ssu` 内核 (PR #3324)**:
    - **变更**: 引入了一个全新的、高度融合的 CUDA 内核，用于 Mamba2 模型的选择性状态更新（SSU）操作。该内核集成了“重放”（Replay）和“检查点”（Checkpointing）功能。
    - **与项目方向的关系**: 这直接体现了 FlashInfer 的核心目标——为新兴的、复杂的模型架构（如状态空间模型 Mamba2）提供高性能推理内核。通过将原本需要多个 Triton 内核的操作融合为一个 CUDA 内核，并利用条件性写入来避免不必要的 HBM 访问，极大地提升了 Mamba2 在推理场景（特别是推测性解码）中的效率。

- **Gemma/Qwen3.5 RMSNorm 融合 (PR #3322)**:
    - **变更**: 为 AllReduce 和 RMSNorm 的融合操作添加了对 `weight_bias` 参数的支持。
    - **与项目方向的关系**: 这体现了项目对主流和新兴模型架构的持续适配。Gemma 和 Qwen3.5 等模型使用了带偏置的 RMSNorm，此更新确保了 FlashInfer 的融合内核能够正确支持这些模型，从而在分布式推理场景中提供性能优势。

- **BF16 解码修复 (PR #3268)**:
    - **变更**: 修复了 BF16 解码内核在处理非连续（padded/strided）状态池时的错误。
    - **与项目方向的关系**: 这是对现有功能的完善和健壮性提升。确保在复杂的内存布局下（如 vLLM 等框架中常见的分页缓存）也能正确工作，是保证项目在生产环境中稳定可靠的关键。

- **TRTLLM FMHA 更新 (PR #3317)**:
    - **变更**: 更新了与 TensorRT-LLM 集成的 FMHA 内核的二进制文件和参数 ABI。
    - **与项目方向的关系**: 这体现了 FlashInfer 作为底层内核库，需要与上层推理框架（如 TensorRT-LLM）保持紧密的集成和同步。更新 cubins 和 ABI 是为了确保兼容性和利用最新的优化。

#### 3. 对项目的影响和潜在意义
- **显著增强 Mamba2 推理能力**: `checkpointing_ssu` 内核是 Mamba2 模型推理性能的关键突破。它通过减少内核启动次数、降低 HBM 带宽占用，有望将 Mamba2 的推理吞吐量提升到一个新的水平，使其在长序列和推测性解码场景中更具竞争力。
- **扩展模型支持范围**: 对 Gemma/Qwen3.5 RMSNorm 的支持，使 FlashInfer 能够服务于更广泛的用户群体和模型生态，增强了项目的通用性和吸引力。
- **提升稳定性和兼容性**: BF16 修复和 TRTLLM 更新虽然看似微小，但它们是保证项目在复杂、真实的生产环境中稳定运行的基础，对于维护项目声誉和用户信任至关重要。

#### 4. 值得关注的技术点
- **`checkpointing_ssu` 内核的融合设计**: 该内核将“重放”（从历史状态恢复）和“检查点”（决定是否写入新状态）两个逻辑融合在一个内核中，并通过运行时条件判断（`must_checkpoint`）来动态选择执行路径，避免了不必要的 HBM 写入。这是一种非常高级的 GPU 优化技巧。
- **量化状态路径**: 该内核支持 int8/fp8 等量化状态，并集成了随机舍入（Stochastic Rounding）以保持模型精度。这表明 FlashInfer 正在积极拥抱低精度推理以换取更高性能。
- **`D_SPLIT` 和 `M-shard` 等高级并行策略**: 内核针对不同数据类型（16/32-bit vs 8-bit）采用了不同的 warp 分块策略（`Layout<_1, _4>` vs `Layout<_4, _1>`），以适配不同的计算和内存访问模式，体现了对 GPU 微架构的深刻理解。
- **与 vLLM 的深度集成**: 内核原生支持 vLLM 

## 详细提交记录

### [9035311](https://github.com/flashinfer-ai/flashinfer/commit/9035311e975a6aeb2d229f5162e999dfb7c9a733)

- **作者**: Duncan Moss
- **时间**: 2026-05-19T21:54:08Z
- **提交信息**: Update trtllm FMHA cubins (#3317)

<!-- .github/pull_request_template.md -->

## 📌 Description

Updates the trtllm FMHA artifact path and checksum to the newer cubins.
Aligns the FMHA parameter ABI expected by those cubins and uses dense
mask selection for MLA decode generation kernels.

## 🔍 Related Issues

None.

## 🧪 Tests

- `pre-commit run --all-files`
- `pytest
tests/attention/test_cute_dsl_mla_decode.py::test_cute_dsl_vs_trtllm_gen[True-128-1]
tests/attention/test_trtllm_ragged_kv_stride.py -q -ra --tb=short`
- every fifth collected tracked `tests/attention/*.py` item after `-k
trtllm`: `18314 passed, 22979 skipped, 342803 deselected, 686 warnings`
- H64 BF16 Q + FP8 KV ULP sweep: `7/7 PASS`, all mismatches `0`

## Reviewer Notes

None.

Co-authored-by: Duncan Moss <djmmoss@gmail.com>

### [f5e533c](https://github.com/flashinfer-ai/flashinfer/commit/f5e533ce8511674c39aba4ab13cf201f54f6eafd)

- **作者**: ameynaik-hub
- **时间**: 2026-05-19T21:33:55Z
- **提交信息**: Ameyn/gdn bf16 dispatcher and 4d pool (#3268)

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Fixed BF16 decode to correctly handle padded/non-contiguous state
pools and to reuse caller-provided BF16 output buffers without
unnecessary copies.

* **Optimizations**
* Kernel compilation now differentiates pool memory layouts to produce
correct, efficient code for strided pools.

* **Tests**
* Added a CUDA regression test validating BF16 decoding with
padded/strided pool layouts.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3268?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [194930c](https://github.com/flashinfer-ai/flashinfer/commit/194930ce26d07a7d9d558f29d98f0502baf9a22a)

- **作者**: Igor Shovkun
- **时间**: 2026-05-19T16:47:01Z
- **提交信息**: checkpointing_ssu kernel: fused replay + conditional state-write for Mamba2 (#3324)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds `flashinfer.mamba.checkpointing_ssu` — a fused CUDA kernel for the
Mamba2 selective-state-update (SSU) operation with two distinct
features:

1. **Replay** — fast-forward the SSM state through previously-cached
tokens
without re-running the upstream model layers, then process the new
tokens
in the same launch. Used for speculative decoding (MTP) and re-attempt
   flows where the model needs to "rewind and replay" recent history.
2. **Checkpointing** — at runtime, decide per request whether the new
tokens
fit in the cache or not. If they fit, skip the state HBM write entirely
   (the cache still has enough headroom).  If they overflow, write the
post-replay state to HBM and reset the cache. Eliminates the state-write
   path on most steps under typical workloads.

Replaces an upstream two-kernel Triton reference (precompute + main)
with a
single Ampere-class `mma.sync.m16n8k16` kernel that does the entire
`replay(prev_k) → output(new_T)` recurrence in one launch.

### What it computes

Per `(batch, head)`, unrolling the SSD recurrence to closed form:

```
h_t[d,n] = h_0[d,n] * exp(cumAdt[t])
         + Σ_{j≤t} exp(cumAdt[t] - cumAdt[j]) * dt_proc[j] * B[j,n] * x[j,d]
y[t,d]   = decay[t] * Σ_n C[t,n] * h_0[d,n]      (init_out — matmul-3)
         + Σ_{j≤t} CB_scaled[t,j] * x[j,d]        (cb_out   — matmul-4)
         + D[d] * x[t,d]
y[t,d]  *= z[t,d] * sigmoid(z[t,d])
```

with `CB_scaled[t,j] = exp(cumAdt[t]-cumAdt[j]) * dt_proc[j] * <C[t,:],
B[j,:]>`
the lower-triangular `[T,T]` scaling matrix.

**Replay** fast-forwards `h_0` with `prev_k` previously-cached tokens
*before*
the new `T` tokens are processed:

```
h_0 ← h_0 * exp(total_old_cumAdt) + old_x^T @ (coeff * old_B)
```

This decomposes into four matmuls per call:

| # | Op | Shape |

|----|---------------------------------|-----------------------------------|
| 1 | C @ Bᵀ (precompute CB_scaled) | `[T,N] @ [N,T] → [T,T]` |
| 2 | old_xᵀ @ dB_scaled (replay) | `[D,K] @ [K,N] → [D,N]` |
| 3 | C @ stateᵀ (init_out) | `[T,N] @ [N,D] → [T,D]` |
| 4 | CB_scaled @ x (cb_out) | `[T,T] @ [T,D] → [T,D]` |

All four ride `mma.sync.m16n8k16.f32.bf16/f16` (Ampere;
forward-compatible to
Hopper/Blackwell).  Hopper `wgmma` (M ≥ 64) and Blackwell `tcgen05.mma`
(≥ 64×64) are too coarse for these tile sizes (M ≤ 16, K = 16).

### Checkpointing semantics

The cache holds up to `MAX_WINDOW` historical tokens per sequence
(double-buffered).  Each call to the kernel can:

* **Append** the `seq_len` new tokens to the active buffer at offset
  `prev_k` (no-checkpoint path: `must_checkpoint = False`).  State stays
  in registers, no HBM write.
* **Checkpoint** to the staging buffer at offset 0, flipping the
  double-buffer pointer (checkpoint path: `must_checkpoint = True`).
  Post-replay state gets written to HBM (the only path that touches
  state gmem on the write side).

The trigger is computed per CTA at runtime:

```cpp
must_checkpoint = (prev_k + seq_len > MAX_WINDOW)
```

Under typical serving load (long context, small new-token chunks), most
calls hit Branch B and never touch state HBM.  Branch A only fires when
the cache fills up.

The kernel is template-specialized on the dispatch — `if constexpr
(must_checkpoint)` is **runtime**, dispatched via two helper functions
(`ssu_checkpoint{,_8bit}` / `ssu_nocheckpoint{,_8bit}`) on the per-CTA
boolean, so warp divergence inside the dispatch is balanced.

### Architecture: two kernel headers

The kernel is split into **two source files** because the 8-bit state
path
needs a fundamentally different MMA layout from the 16/32-bit path:

#### `kernel_checkpointing_ssu.cuh` — bf16 / fp16 / fp32 state

* **N-shard replay** (`Layout<_1, _4>` warp tiling): each warp owns a
contiguous slice of the `dstate` axis. Loads state from smem into a B-
fragment, hits HMMA in fp32 accumulation, writes back as bf16/fp16/fp32.
* `D_SPLIT ∈ {1, 2}` supported.  Splits each head's DIM axis across
multiple CTAs to lift small-batch occupancy (`D_SPLIT=4` deferred — the
  output MMA's `_1×4` warp layout needs `D_PER_CTA ≥ 32`).
* Philox stochastic rounding via PTX `cvt.rs.f16x2.f32` is wired in for
  fp16 state (HW path on sm_100a / Blackwell B200+, software emulation
  elsewhere).

#### `kernel_checkpointing_ssu_8bit.cuh` — int8 / fp8_e4m3fn state
(1-byte)

* **M-shard replay chain** (`Layout<_4, _1>` warp tiling): each warp
owns
  16 D-rows of the post-replay state, the chain matmul-3 happens *in
  registers* (replay's fp32 C-frag is converted to bf16 A-frag in place
  via `convert_layout_acc_Aregs_sm80` — no smem.new_state staging).
* Followed by a transposed matmul-4 (`x` as A with M=D, CBᵀ as B) →
  `output^T(D, T)` in regs → smem transpose → cooperative STG.128 to
  `(T, D)` gmem.
* Per-(head, dim) channel decode scale computed from the post-replay
  amax; stored alongside the quantized state.
* `D_SPLIT=1` only (the M-shard replay needs `D_PER_CTA ≥ 64`).
* Philox stochastic rounding:
  * **int8** / **int16**: pure `floor(x + uniform_noise)` —
    runs anywhere.
* **fp8_e4m3fn**: PTX `cvt.rs.satfinite.e4m3x4.f32` packs 4 fp32 values
    + 32-bit random seed into one fp8 vector store (HW path on sm_100a,
    bit-exact SW emulation elsewhere).

#### `kernel_checkpointing_ssu_common.cuh` — shared infrastructure

`load_data` (cp.async load of `x`/`dt`/`B`/`C`/`z` + cache scalars),
`compute_CB_scaled_2warp` (the `[T, T]` causal-masked CB precompute),
`compute_CB_old_2warp` (the no-write path's `CB_old @ old_x` extension),
`store_old_x` / `store_old_B` (cache writebacks), `precompute_dB_coeff`,
swizzle layouts, MMA traits.

#### Public dispatcher: `launch_checkpointing_ssu.cuh`

Routes on `(d_split, varlen)`:

* `d_split` switch reads `params.d_split` (1 or 2 for the 16/32-bit
path,
  always 1 for the 8-bit path).
* `varlen` switch reads `params.cu_seqlens != nullptr`.

Both `D_SPLIT` and `VARLEN` are kernel template parameters; the same
`.so`
holds all four `(D_SPLIT, VARLEN)` specializations.

### Quantized state path (int8 / int16 / fp8_e4m3fn)

For 8-bit states the state HBM is `int8` or `fp8_e4m3fn`; bandwidth
drops
~4× vs fp32 for the same recurrence.  Quantization is **per-(cache_slot,
head, dim) channel** — one decode scale per channel, broadcast over
`dstate`.  The kernel computes scale + quantize on checkpoint steps:

```
amax        = max(|state[d, :]|)  over dstate
encode      = quant_max / amax     (quant_max = 127 for int8, 448 for fp8)
state_q     = round_or_sr(state * encode)
state_scale = 1 / encode           (stored, broadcast over dstate on read)
```

On read, state is `state_q * state_scale` (decode_scale factored out of
the matmul inner product — applied post-matmul as a single FMUL per
output column).

### Varlen support

When `cu_seqlens` is provided, inputs are **packed** as `(1,
total_tokens,
nheads, dim)` / `(1, total_tokens, ngroups, dstate)` — vLLM's "no
padding"
batch ABI.  Each `cu_seqlens[i]` gives the token-axis base of sequence
`i`; `seq_len_i = cu_seqlens[i+1] - cu_seqlens[i]`.

Implementation:

* `VARLEN` is a kernel template parameter; dispatched at launch time.
* The wrapper picks `*_stride_seq = x.stride(0)` (per-batch) in
non-varlen
  or `x.stride(1)` (per-token) in varlen.  Kernel uses one uniform
  formula `outer * *_stride_seq` regardless of mode.
* `NPREDICTED` stays compile-time (max `seq_len` the caller commits to);
  per-sequence variable `T` realized via masking, not by re-sizing smem
  or MMA tiles.
* `must_checkpoint` uses the tighter `prev_k + seq_len > MAX_WINDOW`
  (vs. the conservative `prev_k + NPREDICTED > MAX_WINDOW`) — avoids
  unnecessary checkpoint rotation when a sequence ends short.

### Files

#### CUDA

* `include/flashinfer/mamba/checkpointing_ssu.cuh` — params struct
* `include/flashinfer/mamba/kernel_checkpointing_ssu.cuh` — 16/32-bit
kernel
* `include/flashinfer/mamba/kernel_checkpointing_ssu_8bit.cuh` — 8-bit
kernel
* `include/flashinfer/mamba/kernel_checkpointing_ssu_common.cuh` —
shared helpers
* `include/flashinfer/mamba/launch_checkpointing_ssu.cuh` — public
dispatcher
* `csrc/checkpointing_ssu.cu` — TVM-FFI binding (input validation +
param population)
* `csrc/checkpointing_ssu_kernel_inst.cu` — explicit kernel template
instantiation
* `csrc/checkpointing_ssu_jit_binding.cu` — JIT FFI export
* `csrc/checkpointing_ssu_customize_config.jinja` — JIT-stamped
constants
  (`NPREDICTED`, `MAX_WINDOW`, `DIM`, `DSTATE`, `HEADS_PER_GROUP`,
  `PHILOX_ROUNDS`, state dtypes)

#### Python

* `flashinfer/jit/mamba/checkpointing_ssu.py` — JIT module generator
(URI + config render)
* `flashinfer/mamba/checkpointing_ssu.py` — `checkpointing_ssu()` user
API + dispatch
* `flashinfer/mamba/__init__.py` — exports

#### Triton reference

* `tests/mamba/triton_reference/checkpointing_state_update.py` —
independent
  reference implementation.  Supports the same dtype matrix (fp16, bf16,
  fp32, int8, int16, fp8_e4m3fn), the same Philox SR paths, and the same
  varlen (`cu_seqlens` + `max_seqlen`) interface.  Used as the
  cross-validation oracle for the CUDA kernel.

### API

```python
flashinfer.mamba.checkpointing_ssu(
    state,                         # (cache, nheads, dim, dstate) — updated in-place
    old_x,                         # (cache, T, nheads, dim) cache, single-buffered
    old_B,                         # (cache, 2, T, ngroups, dstate) double-buffered
    old_dt_proc,                   # (cache, 2, nheads, T) f32
    old_cumAdt,                    # (cache, 2, nheads, T) f32
    cache_buf_idx,                 # (cache,) int32 — which buffer is "active"
    prev_num_accepted_tokens,      # (cache,) int32 — how many old tokens in active
    x, dt, A, B, C, out,           # standard SSU inputs/outputs
    D=None, z=None, dt_bias=None,
    dt_softplus=False,
    state_batch_indices=None,      # (batch,) — optional paged-cache mapping
    pad_slot_id=-1,
    state_scale=None,              # (cache, nheads, dim) f32 — required for int8/fp8 state
    rand_seed=None,                # single-element int64 CUDA tensor — enables Philox SR
    philox_rounds=10,
    d_split=None,                  # {1, 2} for 16/32-bit; auto-heuristic
    cu_seqlens=None,               # (batch+1,) int32 — enables varlen mode
    max_seqlen=None,               # upper bound on max(cu_seqlens diff), required in varlen
)
```

## 🔍 Related Issues

Replaces the discarded [#3217 `ssu_incremental`
PR](https://github.com/flashinfer-ai/flashinfer/pull/3217).

### Differences from #3217

The original PR added an "always-write replay" path (every call wrote
post-replay state to HBM, no conditional checkpoint logic).  This branch
extends that with:

1. **Conditional checkpointing** — runtime `must_checkpoint` decision
   per CTA; Branch B skips state HBM write entirely.
2. **8-bit quantized state** (int8, fp8_e4m3fn) with per-channel decode
   scales and stochastic rounding (Philox-driven SR; PTX
   `cvt.rs.satfinite.e4m3x4.f32` on Blackwell + bit-exact SW emulation
   elsewhere).
3. **int16 state** support (via the same per-channel scale
infrastructure
   as int8).
4. **Varlen** support (cu_seqlens) for vLLM's packed-batch ABI.
5. **Independent Triton reference** with full feature parity (was a
   replay-only Triton ref in the original PR).
6. Renamed `ssu_incremental` → `checkpointing_ssu` throughout to match
   the v19 split (checkpoint / no-checkpoint paths).

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

`tests/mamba/test_checkpointing_ssu.py` — 138 cases covering the CUDA
kernel + the merged Triton reference.

### CUDA kernel correctness

* **`test_checkpointing_ssu_max_window_gt_npredicted`** (12 cases) —
the main correctness sweep. `(NPREDICTED, MAX_WINDOW) ∈ {(4,8),
(10,16)}`
  × `state_dtype ∈ {fp16, bf16, fp32}` × `paged_cache ∈ {True, False}`.
  Inner loop sweeps `prev_k ∈ [0, NPREDICTED]` crossing the
  `must_checkpoint` boundary — exercises Branch A and Branch B in the
  same test.  Compared against Triton reference.
* **`test_checkpointing_ssu_int8_rn_parity`** (8 cases) — int8 state
with
round-to-nearest quantization. Cross-validated against the fp32 Triton
  reference path with explicit per-channel dequantization on the state.
* **`test_checkpointing_ssu_fp8_rn_parity`** (8 cases) — same as int8
but
  fp8_e4m3fn.  Skipped on SM < 89 (Ada/Hopper/Blackwell required for the
  fp32↔fp8 cvt PTX).
* **`test_checkpointing_ssu_int8_philox`** / **`…_fp8_philox`** /
**`…_philox`** (8 + 8 + 8 cases) — Philox stochastic rounding for int8 /
fp8 / bf16 state.
* **`test_checkpointing_ssu_philox_no_checkpoint`** (4 cases) — fp16
  Philox in Branch B (no-write).  Validates that state HBM stays
  byte-identical when must_checkpoint=False.
* **`test_checkpointing_ssu_philox_with_checkpoint`** (4 cases) — fp16
  Philox in Branch A across different `(prev_k, NPREDICTED, MAX_WINDOW)`
  triples that cross the must_checkpoint boundary.
* **`test_checkpointing_ssu_mixed_checkpoint_batch`** (8 cases) — mixed
  `prev_k` across the batch so different CTAs hit different branches
  in the same launch.

### Statistical SR unbiasedness

* **`test_philox_rounding_unbiased`** /
**`test_checkpointing_ssu_int8_philox_unbiased`**
  / **`test_checkpointing_ssu_fp8_philox_unbiased`** — verify that
  Philox SR preserves the expected value (mean residual ≈ 0) over many
  samples.

### Varlen (vLLM packed-batch ABI)

* **`test_checkpointing_ssu_varlen_mixed_no_checkpoint`** (5 cases) —
  mixed `seq_lens=[3,1,4,2,4]` with `prev_ks=[0,5,10,12,8]` chosen so
  that every sequence stays in Branch B.  Compares CUDA varlen against
  per-batch padded CUDA non-varlen.  Sweeps all 5 dtypes.
* **`test_checkpointing_ssu_varlen_mixed_checkpoint`** (5 cases) — same
  pattern with `prev_ks` chosen to force every sequence into Branch A.
* **`test_checkpointing_ssu_varlen_cuda_vs_triton_no_checkpoint`** (5
cases)
  / **`...checkpoint`** (5 cases) — **independent reference** check:
  CUDA varlen vs Triton varlen.  Catches bugs that the
  CUDA-vs-CUDA-padded tests wouldn't (e.g. a math error present in both
  varlen and non-varlen CUDA branches).

### Stride / layout

* **`test_checkpointing_ssu_noncontig`** (4 cases) — every batch-side
  tensor (`x`, `dt`, `B`, `C`, `z`, `out`, plus cache-side `old_x`,
  `old_B`, `old_dt_proc`, `old_cumAdt`) gets a different outer-dim
  padding → distinct non-default strides.  Bit-exact comparison
  against the contiguous-clone reference.  Sweeps `{varlen, non-varlen}
  × {bf16, int8}`.
* **`test_checkpointing_ssu_d_split2`** (1 case) — smoke test for the
  `D_SPLIT=2` D-output-split path.
* **`test_checkpointing_ssu_heads_per_group`** (1 case) — smoke test
  with `HPG = nheads/ngroups = 8` to cover the multi-group routing
  (all other tests trivially hit `group_idx = 0` with HPG=16).
* **`test_checkpointing_ssu_contiguous`** (1 case) — sanity that fully
  contiguous inputs work end-to-end.

### Boundary / input validation

* **`test_checkpointing_ssu_rejects_large_T`** (3 cases) — wrapper
  rejects `T > MAX_WINDOW_CAP = 16` with a clear error.
* **`test_checkpointing_ssu_int8_smoke`** — minimal end-to-end smoke for
  int8 state.

### Triton-reference tests (no CUDA JIT)

* **`test_checkpointing_state_update`** (30 cases) — explicit-tuple
  parametrization (was a 288-element cartesian; trimmed to 30
  representatives covering each dtype × T-bucket × write_ckpt × paged
corner). Cross-validates the merged Triton `checkpointing_state_update`
  against the upstream `selective_state_update` reference.
* **`test_checkpointing_state_update_philox`** (12 cases) — Philox
  variant of the above.
* **`test_checkpointing_philox_rounding_unbiased`** (4 cases) —
statistical
  SR unbiasedness on the Triton reference.

### How to run

```bash
# Full checkpointing_ssu suite (138 cases)
uv run pytest tests/mamba/test_checkpointing_ssu.py -v

# Just the CUDA kernel paths (varlen + non-varlen)
uv run pytest tests/mamba/test_checkpointing_ssu.py -v \
    -k "not (state_update and not _ssu_)"
```

Cold-rebuild estimate: ~5-10 min for the unique JIT keys
(`state_dtype × NPREDICTED × MAX_WINDOW × philox_rounds ×
heads_per_group`).
Warm-cache run: ~3-5 min.

## Reviewer Notes

### Architecture support

The JIT module gen (`flashinfer/jit/mamba/checkpointing_ssu.py`) sets a
single `-gencode` arch list: SM 80+ (Ampere → Blackwell).  No
dtype-specific subset — every fp32-to-narrow cvt the kernel uses has
both a hardware PTX path on the relevant architecture and a software
fallback for older arches.

| Op | Hardware path | Software fallback |

|-----------------------------------|--------------------------------------------|--------------------------------------------------|
| fp32 → fp16 SR (`cvt_rs_f16_f32`) | `cvt.rs.f16x2.f32`, sm_100a+ |
`cvt_rs_f16_sw` (`conversion.cuh:148`, bit-exact) |
| fp32 → fp8 e4m3 SR (`cvt_rs_e4m3x4_f32`) |
`cvt.rs.satfinite.e4m3x4.f32`, sm_100a+ | `cvt_rs_e4m3_sw`
(`conversion.cuh:270`, bit-exact) |
| fp32 → fp8 e4m3 RN (`__nv_fp8_e4m3(x)`) |
`cvt.rn.satfinite.e4m3x2.f32`, sm_89+ | cuda_fp8 lib SW path
(`cuda_fp8.hpp:263+`) |
| fp32 → int8 RN (`cvt_rni_sat_s8`) | `cvt.rni.sat.s8.f32`, SM 80+ |
`__float2int_rn` + clamp |
| fp32 → int8 / int16 SR | (no HW PTX op) | uniform-noise + libdevice
floor (runs anywhere) |

Every dtype × rounding-mode the kernel supports runs on any SM80+ arch.
The HW PTX paths are performance optimizations on Blackwell / Ada, not
correctness gates.  Bit-exact SW fallbacks for fp16 / fp8 SR are
validated against hardware on sm_100a.

The kernel source uses `#ifdef __CUDA_ARCH__ >= 1000 &&
__CUDA_ARCH_FEAT_SM100_ALL` guards in `conversion.cuh` to pick between
HW and SW at compile time, so nvcc only emits the HW PTX where it's
legal.

Perf target: SM100 (B200).  Correctness target: SM80+.

### Other notes

* `HEADS_PER_GROUP` is JIT-stamped (one specialization per `.so`,
  vs. the 7-way `dispatchRatio` in the original design) — cuts compile
  time ~7× per `.so`.
* Kernel-launch overhead: 1 launch (was 2 in the Triton precompute+main
  reference) — saves ~1-2 µs out of a ~10-30 µs end-to-end budget.
* No gmem round-trip for `CB_scaled` / `decay_vec` (kept in smem).
* Branch B (no-checkpoint) saves the state HBM write entirely on most
steps under typical workload patterns (`prev_k + seq_len ≤ MAX_WINDOW`).
* Quantized state (int8 / fp8) saves ~4× state HBM bandwidth vs fp32.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Checkpointing SSU: JIT-backed kernels, Torch custom-op, runtime
dispatch for checkpoint/replay selective state updates;
varlen/fixed-length and 8-bit/FP8 paths.
* Benchmarks: new benchmark comparing incremental/checkpointing backends
and runtime GPU bandwidth detection.
* Quantization: expanded int8/FP8 e4m3 support with stochastic rounding
and extended Philox-offset handling.

* **Tests**
* New Philox-offset and FP8 stochastic-rounding reference tests
(hardware + SW fallback).

* **Documentation**
  * Updated CODEOWNERS for MAMBA-related kernel paths.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3324)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [7b9e054](https://github.com/flashinfer-ai/flashinfer/commit/7b9e054db2dd825a460b6c2ea63f3bc57cbf41b1)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-05-19T16:13:18Z
- **提交信息**: [feat] Add gemma RMS AR fusion (#3322)

<!-- .github/pull_request_template.md -->

## 📌 Description

Verified from framework side. See perf at
https://github.com/vllm-project/vllm/pull/42646

Add weight bias to RMS norm AR fusion to support gemma and qwen3.5 RMS

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
* Added a GPU benchmark to compare fused vs unfused AllReduce+RMSNorm
performance.
* Introduced an optional weight_bias parameter to AllReduce-fusion APIs
to support alternate RMSNorm scaling.

* **Tests**
* Added a distributed correctness test for Gemma/Qwen3.5-style RMSNorm
AllReduce fusion.
* Extended AllReduce fusion tests to validate weight_bias variants
(e.g., 0.0 and 1.0).

* **Documentation**
* Updated reference traces and docstrings to describe weight_bias
behavior.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3322?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: jiahanc <173873397+jiahanc@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3491
- **最后更新**: 2026-05-19T14:08:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33669
- **最后更新**: 2026-05-19T18:49:41Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: kaixuanliu

## AI分析总结

好的，这是对 `huggingface/diffusers` 仓库昨日提交记录的分析总结。

### 昨日更新要点分析

**提交记录：** `65aff37` - fix device mismatch issue for HiDreamTransformerTests

---

#### 1. 主要更新类型

*   **Bug修复**：本次提交的核心是修复一个测试用例中的设备不匹配问题。

#### 2. 关键变更点及其与项目整体方向的关系

*   **变更点**：修复了 `HiDreamTransformerTests` 测试中，模型张量（tensor）可能位于不同计算设备（如CPU和GPU）上导致的错误。
*   **与项目方向的关系**：`diffusers` 项目致力于提供稳定、易用的扩散模型工具。修复测试中的设备不匹配问题，直接提升了项目在**多设备环境（特别是Intel硬件）下的兼容性和可靠性**。这符合项目支持多种硬件后端（如CUDA、Intel XPU）的长期目标。

#### 3. 对项目的影响和潜在意义

*   **直接影响**：确保 `HiDreamTransformer` 相关的单元测试能够在不同设备配置下正确运行，避免了因设备问题导致的测试失败。
*   **潜在意义**：
    *   **提升代码质量**：修复了潜在的、可能在生产环境中出现的设备不匹配Bug，增强了模型的鲁棒性。
    *   **支持Intel硬件**：提交者来自Intel，修复针对的是Intel硬件上的测试，表明项目正在积极解决特定硬件上的兼容性问题，这对于扩大用户基础（特别是Intel平台用户）至关重要。
    *   **维护测试可靠性**：可靠的测试是项目健康发展的基石，此修复维护了测试套件的有效性。

#### 4. 值得关注的技术点

*   **设备不匹配（Device Mismatch）**：这是一个在深度学习框架（如PyTorch）中常见的错误。当模型参数、输入数据或中间结果位于不同的设备（例如，模型在GPU，输入在CPU）时，进行运算会抛出异常。此修复通过确保所有相关张量被显式地移动到同一设备上来解决此问题。
*   **测试用例的硬件感知**：优秀的测试用例应该能够感知并适应不同的硬件环境。此修复体现了在编写测试时需要考虑跨设备兼容性的最佳实践。

#### 5. 基于项目背景，这些提交如何影响项目发展

*   **增强项目稳定性与可信度**：`diffusers` 作为一个被广泛使用的库，其稳定性至关重要。修复此类底层兼容性问题，能减少用户在使用过程中遇到的意外错误，提升用户体验和项目口碑。
*   **促进多硬件生态发展**：通过积极解决Intel等非NVIDIA硬件上的问题，`diffusers` 正在构建一个更加开放和多元的硬件生态。这有助于吸引更广泛的开发者社区，并推动扩散模型在不同计算平台上的应用。
*   **为未来功能开发扫清障碍**：一个健壮、经过充分测试的基础是进行新功能开发的前提。修复测试中的Bug，相当于为后续对 `HiDreamTransformer` 模型进行优化或添加新特性铺平了道路。

## 详细提交记录

### [65aff37](https://github.com/huggingface/diffusers/commit/65aff37d03e2f7314d3db379f6363bf36578afd7)

- **作者**: kaixuanliu
- **时间**: 2026-05-19T18:49:25Z
- **提交信息**: fix device mismatch issue for HiDreamTransformerTests (#13766)

* fix device mismatch issue for HiDreamTransformerTests

Signed-off-by: Liu, Kaixuan <kaixuan.liu@intel.com>

* refine code

Signed-off-by: Liu, Kaixuan <kaixuan.liu@intel.com>

---------

Signed-off-by: Liu, Kaixuan <kaixuan.liu@intel.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 403
- **最后更新**: 2026-05-11T08:48:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12435
- **最后更新**: 2026-05-19T22:03:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 28022
- **最后更新**: 2026-05-19T23:51:37Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 21
- **主要提交者**: Xiaoyu Zhang, huangtingwei, amote-i

## AI分析总结

好的，这是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增 (Feature)**：支持新的模型架构和并行策略，如 DeepSeek V4 MTP、Gemma4 Pipeline Parallelism、GLM-Image 并行。
- **Bug修复 (Bug Fix)**：修复了多个模型（如 Qwen3.5、DeepSeek V4、Gemma4）在特定场景下的冲突、错误和崩溃问题。
- **性能优化 (Performance)**：优化了 NSA 注意力机制的显存查询、FlashInfer 的 MoE 内核。
- **文档更新 (Documentation)**：改进了 Ascend NPU 文档的可用性，移除了过时的基准测试文档。
- **重构与清理 (Refactor/Cleanup)**：移除了过时的 DeepSeek V4 JIT 内核，升级了 Transformers 库版本。
- **CI/CD 改进 (CI/CD)**：优化了 PR 状态通知和测试触发逻辑，提高了测试稳定性。

### 2. 关键变更点及其与项目整体方向的关系

- **DeepSeek V4 支持深化**：提交 `#24934`、`#25729`、`#25396` 和 `#25764` 表明项目正在积极跟进并完善对最新 DeepSeek V4 模型的支持，包括 MTP (Multi-Token Prediction)、CP (Context Parallelism) 和流水线并行 (PP) 的适配，同时清理了旧代码。这与项目“支持最新模型”的核心目标一致。
- **Gemma4 支持增强**：提交 `#25286` 和 `#25284` 为 Google 的 Gemma4 模型添加了 FP8 Triton 缩放布局修复和流水线并行支持，表明项目正在快速适配主流新模型。
- **NPU (Ascend) 生态扩展**：多个提交（`#25524`、`#23482`、`#25592`、`#25735`、`#25778`）专注于 Ascend NPU 的适配，包括 MTP 加载对齐、扩散模型注意力后端、HunyuanVideo 崩溃修复和文档改进。这体现了项目对国产硬件生态的重视和投入。
- **推理性能与效率优化**：提交 `#25299` (NSA 注意力优化) 和 `#22918` (FlashInfer MoE 内核) 直接针对推理过程中的关键瓶颈进行优化，符合项目“高性能推理”的定位。
- **代码健壮性与稳定性**：提交 `#25809` (去抖动测试)、`#25465` (同步逻辑修复)、`#25756` (包卸载修复) 和 `#25695` (JIT 内核错误修复) 表明项目在持续提升代码质量和系统稳定性。

### 3. 对项目的影响和潜在意义

- **提升模型支持广度与深度**：对 DeepSeek V4 和 Gemma4 的深度支持，使 SGLang 能更好地服务使用这些前沿模型的用户，巩固其在 LLM 推理框架中的领先地位。
- **扩大硬件生态覆盖**：对 Ascend NPU 的持续投入，将吸引更多国内用户和开发者，尤其是在信创和国产化替代场景下，具有重要的战略意义。
- **降低推理成本与延迟**：通过优化注意力机制和 MoE 内核，可以显著降低大模型推理的计算开销和显存占用，从而降低部署成本并提升用户体验。
- **提升开发与运维效率**：CI/CD 的改进和 Bug 修复减少了开发者的困扰，提高了项目的迭代速度和可靠性。

### 4. 值得关注的技术点

- **MTP (Multi-Token Prediction)**：DeepSeek V4 和 Qwen3 都采用了 MTP 技术，SGLang 对其的支持（`#24934`, `#25524`）是跟进前沿模型架构的关键。
- **NSA (Native Sparse Attention)**：对 NSA 的优化（`#25299`）表明项目在探索更高效的稀疏注意力机制，这可能是未来长上下文推理的重要方向。
- **FlashInfer v0.6.11 与 NVFP4 MoE**：集成最新的 FlashInfer 库并支持 NVFP4 精度的 MoE 内核（`#22918`），体现了项目紧跟底层计算库和硬件特性（如 Blackwell 架构）的更新。
- **HiSparse 内存池**：支持大于 1 的主机页（`#23606`），这是对 PD (Prefill-Decode) 分离架构下内存管理的重要优化，有助于提升吞吐量。
- **Transformers v5 适配**：升级到 Transformers 5.8.1（`#25451`）并适配 HFRunner（`#23922`），确保与 Hugging Face 生态的兼容性，这是项目长期维护的基础。

### 5. 基于项目背景，这些提交如何影响项目发展

- **强化“最新模型”标签**：README 强调支持最新模型，昨日的提交通过快速适配 DeepSeek V4 和 Gemma4 等前沿模型，有力地证明了这一点，有助于吸引追求技术前沿的用户。
- **兑现“高性能”承诺**：针对 NSA、MoE 等核心算子的优化，直接服务于 README 中“高性能推理”的目标，通过降低延迟和显存占用，提升了框架的竞争力。
- **拓展“多硬件”支持**：对 Ascend NPU 的持续投入，是 README 中未明确提及但实际

## 详细提交记录

### [425dffb](https://github.com/sgl-project/sglang/commit/425dffbde33954bcdd3a4c82dddbf1e4571ca66e)

- **作者**: Paiiii
- **时间**: 2026-05-19T23:51:31Z
- **提交信息**: DeepSeek V4 MTP Support CP (#24934)

Co-authored-by: zengpai <zengpai@baidu.com>

### [beaff00](https://github.com/sgl-project/sglang/commit/beaff003317b11934a08ecabf3a1e227227950af)

- **作者**: YAMY
- **时间**: 2026-05-19T23:04:13Z
- **提交信息**: [NSA] Avoid repeated NSA MQA logits memory queries (#25299)

### [3ef832f](https://github.com/sgl-project/sglang/commit/3ef832f8853d95dc4490ad00b682ca1cfaf85600)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-19T22:57:16Z
- **提交信息**: pr-states: dispatch from pr-test* notify job (fix rerun status) (#25812)

### [b9d470f](https://github.com/sgl-project/sglang/commit/b9d470f4a2f45c3737cfe594f0839bcc8ecfc6f0)

- **作者**: nagisa-kunhah
- **时间**: 2026-05-19T22:23:17Z
- **提交信息**: Support spec v2 for FlashMLA speculative decoding (#24640)

Co-authored-by: Jackey Hua <zhendonghua@users.noreply.github.com>
Co-authored-by: Depend <yu-depend@users.noreply.github.com>

### [2f70902](https://github.com/sgl-project/sglang/commit/2f70902329dfbf813bf6b5a527a5d020528cf641)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-19T22:19:01Z
- **提交信息**: deflake priority below-threshold test (#25809)

### [b9c2bf7](https://github.com/sgl-project/sglang/commit/b9c2bf717ba49a20d0975de86b1fe4f70e95a1f4)

- **作者**: yiheng
- **时间**: 2026-05-19T22:09:49Z
- **提交信息**: [BugFix] Resolve adaptive speculative decoding conflicts for Qwen3.5 (hybrid GDN) (#23331)

Signed-off-by: EanWang211123 <wangyiheng@sangfor.com.cn>
Co-authored-by: shuwenn <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: shuwenn <2508695655@qq.com>

### [16bcc45](https://github.com/sgl-project/sglang/commit/16bcc4583ecf7b7c92a40c68660cb8275c8870a2)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-19T21:57:45Z
- **提交信息**: verify_done: wait not synchronize (#25465)

### [fab097d](https://github.com/sgl-project/sglang/commit/fab097d66d0cf0d808b718221f921aa9c6999c33)

- **作者**: Ratish P
- **时间**: 2026-05-19T21:00:23Z
- **提交信息**: [Gemma4]: Fix FP8 Triton scale layout (#25286)

### [8322fe0](https://github.com/sgl-project/sglang/commit/8322fe09a7b6931faedb00582a86174f39c4843b)

- **作者**: ybyang
- **时间**: 2026-05-19T20:52:00Z
- **提交信息**: fix(dsv4): upgrade forward metadata on main stream for large PP size (#25729)

### [cd012ad](https://github.com/sgl-project/sglang/commit/cd012ada58ac317dd2e9df4ac87b71c104874e39)

- **作者**: Baizhou Zhang
- **时间**: 2026-05-19T17:01:38Z
- **提交信息**: [Fix] Fix extra uninstall of cutlass packages (#25756)

### [4c0ce03](https://github.com/sgl-project/sglang/commit/4c0ce0345d0d842d91d3802fdeec29bfc5caa5b0)

- **作者**: Yuan Luo
- **时间**: 2026-05-19T14:40:11Z
- **提交信息**: Support Gemma4 Pipeline Parallelism (#25284)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [3b62604](https://github.com/sgl-project/sglang/commit/3b62604ceca8f27ccdaf94c004a010cb5e03a87a)

- **作者**: Makcum888e
- **时间**: 2026-05-19T14:27:21Z
- **提交信息**: [Diffusion] Support parallelism for GLM-Image (#25645)

### [aad00b0](https://github.com/sgl-project/sglang/commit/aad00b0ed8f61112d0176414bc4325f3cbb92a4d)

- **作者**: Xinyuan Tong
- **时间**: 2026-05-19T14:20:30Z
- **提交信息**: Upgrade transformers to 5.8.1 (#25451)

### [2bcb6d2](https://github.com/sgl-project/sglang/commit/2bcb6d2f8244a09deb7f8fdc2ec88986a951055e)

- **作者**: Yuxuan Zhang
- **时间**: 2026-05-19T13:47:01Z
- **提交信息**: [Bug Fix] Align glm4_moe_nextn NPU MTP loading with qwen3 MTP (#25524)

### [de3fc46](https://github.com/sgl-project/sglang/commit/de3fc46e3d2f922bcc54abd9a2a05288953b7c38)

- **作者**: amote-i
- **时间**: 2026-05-19T12:48:43Z
- **提交信息**: [NPU] [DOC] remove Qwen3-235B-A22B 2K+2K 100ms mixed mode benchmark (#25778)

### [e0273dc](https://github.com/sgl-project/sglang/commit/e0273dcd316be010bbf461879f2ee5c4c7ab50f3)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-19T12:15:55Z
- **提交信息**: pr-test-extra: re-trigger on labeled event (#25732)

### [0e4d1b4](https://github.com/sgl-project/sglang/commit/0e4d1b49d301b741fe64108f88c34aaf11a3f1ff)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-19T12:04:32Z
- **提交信息**: [Codex] Remove stale DeepSeek V4 JIT kernels (#25764)

### [45a85ef](https://github.com/sgl-project/sglang/commit/45a85efc3aee65c57a374bcd274a6d1243b461c0)

- **作者**: Arseniy Mironov
- **时间**: 2026-05-19T09:46:55Z
- **提交信息**: [Diffusion][NPU]Add attention backends for diffusion models for Ascend NPU (#23482)

Co-authored-by: Napkin-AI <arseniy.mironov.dev@gmail.com>

### [58b5fe3](https://github.com/sgl-project/sglang/commit/58b5fe3e2999e5591da3e094df5ef6c1798fb589)

- **作者**: Thomas
- **时间**: 2026-05-19T09:40:43Z
- **提交信息**: [Diffusion] [NPU] Fix HunyuanVideo crash on NPU (#25592)

### [5073c82](https://github.com/sgl-project/sglang/commit/5073c82a3757796385ad950d990e3ff383dda9e9)

- **作者**: jianzhao-xu
- **时间**: 2026-05-19T09:07:38Z
- **提交信息**: transformers v5 adapt HFRunner (#23922)

### [7e08180](https://github.com/sgl-project/sglang/commit/7e0818038a4527bb374a5c1d55fdf7901b55f299)

- **作者**: shiyu7
- **时间**: 2026-05-19T09:04:21Z
- **提交信息**: fix: fix deepseek v4 CP  error (#25396)

### [67fd005](https://github.com/sgl-project/sglang/commit/67fd005b976011b5be527fbc3642d66aba4ba7c8)

- **作者**: huangtingwei
- **时间**: 2026-05-19T08:29:35Z
- **提交信息**: [HiSparse & PD] Support hisparse memory pool host page > 1 (#23606)

Co-authored-by: hzh0425 <hzh0425@apache.org>
Co-authored-by: Zhiqiang Xie <xiezhq@stanford.edu>

### [1f7bf15](https://github.com/sgl-project/sglang/commit/1f7bf155c3a27ba87ce896ee581d6c1d28854038)

- **作者**: amote-i
- **时间**: 2026-05-19T08:22:22Z
- **提交信息**: [NPU] [DOCS] Improved the usability of Ascend NPU documents (#25735)

### [78cb38e](https://github.com/sgl-project/sglang/commit/78cb38ed5ec4ca5b220ed2765b19b367dc704f79)

- **作者**: Ziang Li
- **时间**: 2026-05-19T08:04:48Z
- **提交信息**: [FlashInfer v0.6.11] [RL] Support FlashInfer per-token NVFP4 MoE (#22918)

### [fbfddfd](https://github.com/sgl-project/sglang/commit/fbfddfd5c7dcdf01903c2696d75f72caf334f324)

- **作者**: Kevin Li
- **时间**: 2026-05-19T07:23:52Z
- **提交信息**: fix (jit kernel): elementwise activation C++ error (#25695)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1174
- **最后更新**: 2026-05-19T11:24:11Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，根据您提供的项目背景和提交记录，以下是针对 `vipshop/cache-dit` 仓库昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增了一个技能（skill）模块。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：提交 `[f5712a3]` 新增了 `triton-kernel` 技能（skill）。
- **与项目方向的关系**：
    - 项目 `cache-dit` 是一个面向扩散变换器（Diffusion Transformers）的 PyTorch 原生推理引擎，其核心能力包括**缓存（Cache）**、**并行化（Parallelism）** 和**量化（Quantization）**。
    - 新增 `triton-kernel` 技能，意味着项目正在将 **Triton**（一种用于编写自定义高性能GPU内核的语言和编译器）作为其底层优化手段之一。这直接服务于项目“性能优化”的核心目标，通过编写更高效的GPU内核来加速推理过程。

### 3. 对项目的影响和潜在意义
- **性能提升潜力**：Triton 内核通常比原生 PyTorch 操作具有更低的开销和更高的计算效率，尤其是在处理注意力机制、层归一化等复杂算子时。此更新为项目提供了进一步榨干 GPU 性能的途径。
- **扩展性与灵活性**：将 Triton 内核封装为独立的“技能”（skill），表明项目采用了模块化、可插拔的设计思想。这使得未来可以轻松添加更多基于 Triton 或其他技术（如 FlashAttention）的优化技能，增强了项目的扩展性和灵活性。
- **降低推理延迟**：对于扩散变换器这类计算密集型模型，更高效的 GPU 内核能直接转化为更低的推理延迟，这对于实时或近实时的图像/视频生成应用至关重要。

### 4. 值得关注的技术点
- **Triton 编程模型**：Triton 允许开发者以接近 Python 的语法编写高性能 GPU 内核，同时自动处理内存合并、并行化等底层细节。`cache-dit` 引入此技能，表明其开发团队具备或正在引入高级 GPU 优化能力。
- **“技能”（Skill）架构**：这是一个值得关注的设计模式。将不同的优化策略（如缓存、量化、Triton内核）抽象为“技能”，可能意味着项目存在一个统一的调度或组合框架，允许用户根据模型和硬件灵活组合这些技能。

### 5. 基于项目背景，这些提交如何影响项目发展
- **强化核心优势**：`cache-dit` 的定位是“PyTorch-native”且高性能。通过集成 Triton 内核，项目在保持 PyTorch 生态兼容性的同时，进一步缩小了与纯 CUDA 实现（如 TensorRT）的性能差距，巩固了其作为高性能推理引擎的定位。
- **推动技术演进**：这表明项目不再满足于仅使用 PyTorch 的 JIT 或 `torch.compile` 进行优化，而是开始深入底层，通过自定义内核来针对扩散变换器的特定计算模式（如长序列注意力、时间步长嵌入等）进行极致优化。这标志着项目在技术深度上迈出了重要一步。
- **吸引高级用户**：对于追求极致性能的研究人员和工程师，`triton-kernel` 技能是一个极具吸引力的特性。这有助于项目从众多基于 PyTorch 的推理方案中脱颖而出，吸引更多对底层优化有需求的用户和贡献者。

## 详细提交记录

### [f5712a3](https://github.com/vipshop/cache-dit/commit/f5712a36faa525ce25b162b411dd55044e1c5156)

- **作者**: DefTruth
- **时间**: 2026-05-19T11:24:04Z
- **提交信息**: skills: add triton-kernel skill (#1013)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 80499
- **最后更新**: 2026-05-19T23:58:10Z

## 提交统计

- **昨日提交总数**: 21
- **提交者数量**: 20
- **主要提交者**: Fadi Arafeh, Nick Hill, wang.yuqi

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bugfix):** 修复了动态NTK缩放、FlashInfer MoE、AsyncScheduler、top logprobs等问题。
- **功能新增 (Feature):** 新增了FP8 per-tensor Q scale支持、OpenVLA模型支持、EAGLE-3投机解码架构支持。
- **性能优化 (Performance):** 消除了GPU与CPU之间的同步点，优化了XPU图使用。
- **文档更新 (Docs):** 修复了Arm CPU的安装命令，更新了MooncakeStoreConnector的示例文档。
- **重构 (Refactor):** 提取了工具解析器中的通用工具，重构了DeepSeek V4模型代码（重命名、移动操作）。
- **CI/测试 (CI/Test):** 移动了语言模型测试，添加了MTP+PD分离测试，临时禁用了FlashInfer的持久化缓存。
- **其他 (Misc):** 添加了`humming`依赖，移除了CLIPAttention中的冗余代码。

### 2. 关键变更点及其与项目整体方向的关系

- **模型支持扩展 (Model Support):**
    - **OpenVLA支持 (#42654):** 新增了对视觉-语言-动作（VLA）模型的支持，这直接呼应了README中“Easy, fast, and cheap LLM serving for everyone”的目标，将vLLM的服务能力从纯文本模型扩展到多模态和具身智能领域。
    - **EAGLE-3投机解码 (#42764):** 支持EAGLE-3的后归一化架构，持续优化投机解码（Speculative Decoding）技术，这是提升LLM推理吞吐量的关键方向。
    - **DeepSeek V4重构 (#43077, #43073):** 对DeepSeek V4模型代码进行重构，是项目持续进行模型架构优化和代码库整洁化的一部分，为未来更复杂的模型支持打下基础。

- **性能与效率提升 (Performance & Efficiency):**
    - **消除GPU-CPU同步 (#42347):** 这是性能优化系列的一部分，通过减少不必要的同步等待，可以显著提升GPU利用率和端到端推理速度，直接服务于“cheap”和“fast”的目标。
    - **FP8 per-tensor Q scale支持 (#42080):** 为Triton注意力后端添加FP8量化支持，这是降低模型部署成本和内存占用的关键步骤，符合“cheap”的目标。
    - **XPU图优化 (#43043):** 针对Intel XPU硬件的优化，体现了项目对多样化硬件平台的支持承诺。

- **稳定性与可靠性 (Stability & Reliability):**
    - **修复AsyncScheduler Bug (#42117):** 修复了暂停生成后恢复时丢失token的问题，这直接关系到服务的稳定性和正确性，是生产环境部署的关键。
    - **修复FlashInfer MoE Bug (#42976):** 修复了MoE层间workspace共享问题，确保了使用FlashInfer后端时的正确性。
    - **修复动态NTK缩放 (#41277):** 修复了位置编码缩放的一个关键错误，确保了长上下文推理的正确性。

- **开发者体验与文档 (Developer Experience & Docs):**
    - **Arm CPU安装文档修复 (#43115):** 修复了Arm架构的安装命令，降低了特定硬件用户的入门门槛。
    - **工具解析器重构 (#43025):** 提取通用工具，简化了未来新模型（如Minimax M2）的集成工作。

### 3. 对项目的影响和潜在意义

- **正面影响：**
    - **模型生态更丰富：** OpenVLA的加入标志着vLLM正式进入具身智能推理领域，可能吸引新的用户群体。
    - **推理性能持续领先：** 消除同步、FP8支持等优化，巩固了vLLM作为高性能推理引擎的地位。
    - **稳定性和正确性提升：** 多个Bug修复直接提升了服务可靠性，对生产环境用户至关重要。
    - **代码库健康度提升：** 重构和清理工作降低了未来维护和扩展的成本。

- **潜在意义：**
    - **多模态推理成为重点：** OpenVLA的加入可能预示着vLLM将投入更多资源支持视觉、语音等多模态模型。
    - **对新兴硬件的支持：** XPU优化表明vLLM正积极适配非NVIDIA硬件，以覆盖更广泛的部署场景。
    - **投机解码技术成熟：** 对EAGLE-3的持续支持表明投机解码正从实验性功能走向生产就绪。

### 4. 值得关注的技术点

- **`[Perf][4/n] Eliminate various GPU<->CPU syncs (#42347)`:** 这是一个系列性能优化的一部分，值得关注其后续提交，了解vLLM团队是如何系统性地分析和消除性能瓶颈的。
- **`[feat] Add FP8 per-tensor Q scale support to Triton attention backend (#42080)`:** FP8量化是当前降低大模型推理成本的热门技术，vLLM在Triton后端实现此功能，表明其正在积极跟进前沿技术。
- **`[Model] Openvla support (#42654)`:** 这是vLLM支持具身智能模型的第一步，其实现方式和性能表现值得关注，可能为未来支持更多类似模型（如RT-2、Octo）铺平道路。
- **`[Model Refactoring] Rename deepseek_v4.py to model.py [

## 详细提交记录

### [be16785](https://github.com/vllm-project/vllm/commit/be16785998087f80ffac08b980603241e5da16ab)

- **作者**: Fadi Arafeh
- **时间**: 2026-05-19T23:31:15Z
- **提交信息**: [CPU][DOC] Fix installation commands for Arm CPUs (#43115)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>

### [117afee](https://github.com/vllm-project/vllm/commit/117afeea4665367a3066c1df58d4082d07fcc946)

- **作者**: Max de Bayser
- **时间**: 2026-05-19T21:27:54Z
- **提交信息**: Fix error in Dynamic NTK scaling (#41277)

Signed-off-by: Max de Bayser <mbayser@br.ibm.com>
Signed-off-by: Max de Bayser <maxdebayser@gmail.com>
Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: wang.yuqi <yuqi.wang@daocloud.io>

### [1242196](https://github.com/vllm-project/vllm/commit/12421962955ac28b6f80a0307f554fad939174dd)

- **作者**: Doğaç Eldenk
- **时间**: 2026-05-19T20:39:00Z
- **提交信息**: [Model] Support post-norm architecture for EAGLE-3 supeculators (#42764)

Signed-off-by: Doğaç Eldenk <dogacel@gmail.com>

### [a65093c](https://github.com/vllm-project/vllm/commit/a65093c1a39a8ddd8455365128ecbe259350e22c)

- **作者**: Kevin H. Luu
- **时间**: 2026-05-19T18:51:34Z
- **提交信息**: [ci] Move language models tests (hybrid) back to L4 (#43129)

Signed-off-by: Kevin H. Luu <khluu000@gmail.com>

### [9aaf83e](https://github.com/vllm-project/vllm/commit/9aaf83ef502fc37bc647f6e474314d48ba36cd1c)

- **作者**: Wei Zhao
- **时间**: 2026-05-19T18:44:32Z
- **提交信息**: [CI failure] Temporarily disable using persistent cache for flashinfer autotune (#43119)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Signed-off-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [f54721b](https://github.com/vllm-project/vllm/commit/f54721bcc3e072d71b0e09c0b0bd6d692eb06161)

- **作者**: tomeras91
- **时间**: 2026-05-19T18:43:04Z
- **提交信息**: [Bugfix][MoE] FlashInfer one-sided: workspace union across heterogeneous layers (#42976)

Signed-off-by: Tomer Asida <57313761+tomeras91@users.noreply.github.com>

### [aed2eb3](https://github.com/vllm-project/vllm/commit/aed2eb355a9d9136c8e17690b932983b55fb343f)

- **作者**: Dao007forever
- **时间**: 2026-05-19T18:14:43Z
- **提交信息**: [Docs] Fix MooncakeStoreConnector role in disaggregated example (#42994)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d247a93](https://github.com/vllm-project/vllm/commit/d247a931cc25e7253feccbd6260d48216ff5c081)

- **作者**: Dom Brown
- **时间**: 2026-05-19T16:02:05Z
- **提交信息**: [feat] Add FP8 per-tensor Q scale support to Triton attention backend (#42080)

Signed-off-by: Dom Brown <3886319+DomBrown@users.noreply.github.com>

### [8200fbe](https://github.com/vllm-project/vllm/commit/8200fbe1ac73f00a46b1cdd6c4c93bdaf2c33022)

- **作者**: Jinzhen Lin
- **时间**: 2026-05-19T15:36:47Z
- **提交信息**: [Misc] add humming to dependencies (#42540)

Signed-off-by: Jinzhen Lin <jinzhen.ljz@antgroup.com>

### [42b4f1f](https://github.com/vllm-project/vllm/commit/42b4f1fdf7269de8aa83755a805555fe78add28b)

- **作者**: Flora Feng
- **时间**: 2026-05-19T15:21:12Z
- **提交信息**: [Refactor] Extract extract_types_from_schema utility from Minimax M2 tool parser (#43025)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [1c61580](https://github.com/vllm-project/vllm/commit/1c6158083a6fc3aff408660d2defd7602f78f556)

- **作者**: Wang Yiwen
- **时间**: 2026-05-19T15:17:42Z
- **提交信息**: [Model] Openvla support (#42654)

Signed-off-by: Wang Yiwen <121547057+yiwen101@users.noreply.github.com>

### [d740e2c](https://github.com/vllm-project/vllm/commit/d740e2c02919cfba5a86a40d1c12439d03f5ac07)

- **作者**: Xinyu Chen
- **时间**: 2026-05-19T15:09:07Z
- **提交信息**: [XPU] update xpu graph usage (#43043)

Signed-off-by: Xinyu Chen <xinyu1.chen@intel.com>

### [b82e908](https://github.com/vllm-project/vllm/commit/b82e908b4c65a1f162e2d35a8106f09d95d8aa02)

- **作者**: Nick Hill
- **时间**: 2026-05-19T14:35:54Z
- **提交信息**: [Perf][4/n] Eliminate various GPU<->CPU syncs (#42347)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [a78b842](https://github.com/vllm-project/vllm/commit/a78b842d0e85d287176031334f4721cd96b6e47d)

- **作者**: Sage
- **时间**: 2026-05-19T10:21:49Z
- **提交信息**: [Bugfix] Fix top logprobs token placeholders in `/inference/v1/generate` (#42887)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [129019f](https://github.com/vllm-project/vllm/commit/129019f3342f1b7346ed8f4c1ac9fdefd8fe6ef8)

- **作者**: zhanqiuhu
- **时间**: 2026-05-19T09:44:33Z
- **提交信息**: [CI] Add MTP + PD disagg test for Qwen3.5 (#42677)

Signed-off-by: ZhanqiuHu <zhu@redhat.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [ef54a4d](https://github.com/vllm-project/vllm/commit/ef54a4d604ef3725bd52aa2893f71d671bf5329a)

- **作者**: Shanshan Shen
- **时间**: 2026-05-19T08:43:16Z
- **提交信息**: [Misc][MM] Remove redundant code in CLIPAttention (#43046)

Signed-off-by: shen-shanshan <467638484@qq.com>

### [07beaed](https://github.com/vllm-project/vllm/commit/07beaed8422d2df34a20e8ebd22b7924d563a566)

- **作者**: Woosuk Kwon
- **时间**: 2026-05-19T08:12:46Z
- **提交信息**: [Model Refactoring] Rename deepseek_v4.py to model.py [4/N] (#43077)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [056bc2e](https://github.com/vllm-project/vllm/commit/056bc2e16646599a96ac94e761c953e680e6fba9)

- **作者**: Yifan Qiao
- **时间**: 2026-05-19T08:07:46Z
- **提交信息**: [KVConnector][DSV4] HMA support for Mooncake store connector (#42828)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>

### [f34623b](https://github.com/vllm-project/vllm/commit/f34623bf3cac5b33451a761e802c9531e83d1c68)

- **作者**: Aaron Hao
- **时间**: 2026-05-19T08:06:21Z
- **提交信息**: [bug] AsyncScheduler drops first post-resume token after pause_generation + clear_cache (#42117)

Signed-off-by: hao-aaron <ahao@anyscale.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b14be81](https://github.com/vllm-project/vllm/commit/b14be81c1f63b70668d26d65a377b6383fbca936)

- **作者**: Woosuk Kwon
- **时间**: 2026-05-19T07:52:54Z
- **提交信息**: [Model Refactoring] Move deepseek_v4_ops to models/deepseek_v4 [3/N] (#43073)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [301d986](https://github.com/vllm-project/vllm/commit/301d986473a0ffc1df563422e01eac4a1efd59e0)

- **作者**: wang.yuqi
- **时间**: 2026-05-19T07:37:40Z
- **提交信息**: [Frontend] Consolidate beam search by BeamSearchMixin. (#42946)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-20
**监控日期**: 2026-05-19
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4813
- **最后更新**: 2026-05-19T17:30:01Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Schatten, WeiQing Chen, dengyunyang

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型

*   **功能新增 (Feature Addition):** 新增了扩散模型量化输出比较工具，以及新的模型配方（Recipe）。
*   **Bug修复 (Bug Fix):** 修复了多模态CLI（命令行界面）在获取KV缓存时的超时问题。
*   **代码清理/重构 (Code Cleanup/Refactoring):** 移除了不再使用的构建引擎参数，并清理了Qwen-Image模型中文本编码器中未使用的视觉塔。
*   **CI/基础设施改进 (CI/Infrastructure Improvement):** 改进了Buildkite测试用例的统计报告。

### 2. 关键变更点及其与项目整体方向的关系

*   **新增扩散模型量化工具:** 项目目标是“为所有人提供简单、快速、便宜的**全模态**模型服务”。扩散模型是图像/视频生成领域的关键技术。新增量化输出比较工具，直接服务于**降低模型部署成本**和**保证量化后模型质量**的目标，是推动扩散模型高效服务的关键一步。
*   **修复多模态CLI超时:** 多模态CLI是用户与模型交互的核心入口。修复此Bug直接提升了**用户体验的稳定性和可靠性**，确保“简单”和“快速”的承诺得以兑现。
*   **新增Qwen-Image-Edit配方:** 这体现了项目对**主流开源多模态模型**的快速跟进和支持能力。Qwen-Image-Edit是一个图像编辑模型，支持它扩展了vllm-omni在**图像处理**领域的服务能力，丰富了“全模态”的内涵。
*   **清理Qwen-Image模型:** 移除未使用的视觉塔，是一种**模型适配的优化**。这有助于减少模型加载时的资源浪费，提升推理效率，符合“快速”和“便宜”的目标。
*   **改进CI报告:** 这是**项目工程化成熟度**的体现。更好的测试报告能帮助开发者更快定位问题，保障代码质量，从而支持项目长期稳定发展。

### 3. 对项目的影响和潜在意义

*   **加速扩散模型服务落地:** 量化工具的出现，为在vllm-omni框架内高效、低成本地部署扩散模型（如Stable Diffusion系列）铺平了道路，可能吸引更多生成式AI应用开发者。
*   **提升核心功能稳定性:** 修复CLI超时问题，直接改善了所有使用多模态CLI用户的体验，减少了生产环境中的故障风险。
*   **扩展模型生态:** 支持Qwen-Image-Edit，使vllm-omni的模型库更加丰富，覆盖了从理解（如Qwen-VL）到生成（如Qwen-Image-Edit）的更多场景，增强了项目的竞争力。
*   **提升开发效率:** 代码清理和CI改进虽然对用户不直接可见，但能降低内部维护成本，加快未来新功能的开发速度。

### 4. 值得关注的技术点

*   **扩散模型量化:** 这是一个技术难点。如何在对扩散模型（通常对量化更敏感）进行量化后，通过工具比较其输出与原始模型的差异，是保证服务质量的关键。这个工具的具体实现方法值得关注。
*   **多模态CLI与KV缓存:** 修复“get kv”超时问题，可能涉及到多模态模型（如视觉语言模型）在生成过程中KV缓存的管理和同步机制，这是一个复杂的工程问题。
*   **模型配方 (Recipe):** 项目使用“Recipe”来定义如何加载和适配一个新模型。`Qwen-Image-Edit`的Recipe展示了如何将一个特定的、可能经过微调的模型集成到vllm-omni框架中，这为社区贡献新模型提供了模板。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **强化“全模态”定位:** 通过支持图像编辑模型（Qwen-Image-Edit）和优化扩散模型部署（量化工具），vllm-omni正在从单纯的**多模态理解**（如VLM）向**多模态生成**（如图像编辑）领域拓展，使其“全模态”的定位更加名副其实。
*   **夯实“快速、便宜”基础:** 模型清理（减少冗余计算）和量化工具（降低显存和计算需求）都是直接服务于“快速”和“便宜”这两个核心承诺。这表明项目在追求功能丰富的同时，没有忽视性能和成本优化。
*   **提升工程成熟度:** 修复Bug和改进CI，表明项目正从早期功能开发阶段，进入一个更加注重**稳定性、可靠性和开发效率**的成熟阶段。这对于吸引企业级用户至关重要。
*   **构建社区生态:** 新增模型配方和提供量化工具，降低了社区用户贡献和使用新模型的门槛，有助于围绕vllm-omni形成一个活跃的开发者社区，推动项目长期发展。

## 详细提交记录

### [a3d4ed8](https://github.com/vllm-project/vllm-omni/commit/a3d4ed809d56977eb632e8a63aae1fc090a790e3)

- **作者**: WeiQing Chen
- **时间**: 2026-05-19T16:14:08Z
- **提交信息**: [Quantization][tools] Add diffusion quantization output comparison tool (#3175)

Signed-off-by: david6666666 <530634352@qq.com>
Signed-off-by: David Chen <530634352@qq.com>

### [3c58868](https://github.com/vllm-project/vllm-omni/commit/3c58868c9a4fb7f0b1754d07738d1f87d3af5dae)

- **作者**: dengyunyang
- **时间**: 2026-05-19T14:22:27Z
- **提交信息**: [BugFix] fix mult cli timeout with get kv (#3741)

Signed-off-by: dengyunyang <584797741@qq.com>

### [da53618](https://github.com/vllm-project/vllm-omni/commit/da5361879395d45d5017fb575a7446cb36774bf4)

- **作者**: Shin
- **时间**: 2026-05-19T11:56:38Z
- **提交信息**: [Recipe] Qwen/Qwen-Image-Edit (#3684)

Signed-off-by: yixiaoer <shin@yixiaoer.sg>

### [18186db](https://github.com/vllm-project/vllm-omni/commit/18186db216319684e3e0d2c268d6a0409525fc2e)

- **作者**: Schatten
- **时间**: 2026-05-19T11:23:45Z
- **提交信息**: [Cleanup] Remove unused build_base_engine_args after #1115 (#3720)

Signed-off-by: Schatten <czhengt@qq.com>

### [14e5bac](https://github.com/vllm-project/vllm-omni/commit/14e5baceaf240e78d1a0c5dcc883563db23eb703)

- **作者**: Lu
- **时间**: 2026-05-19T11:19:58Z
- **提交信息**: [Qwen-Image] Drop unused vision tower from text encoder (#3608)

Signed-off-by: lulugoodcoder <luludachiever@gmail.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [2af2a50](https://github.com/vllm-project/vllm-omni/commit/2af2a50e0e2981ec2eef32e704f5a66c3d451c95)

- **作者**: wangyu
- **时间**: 2026-05-19T07:22:02Z
- **提交信息**: [CI] improve Buildkite testcase statistics reports (#3543)

Signed-off-by: wangyu <410167048@qq.com>

---
