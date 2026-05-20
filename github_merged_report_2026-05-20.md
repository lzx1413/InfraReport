# GitHub Stars 合并报告 - 2026-05-20

**合并日期**: 2026-05-21
**监控日期**: 2026-05-20
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


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1934
- **最后更新**: 2026-05-20T16:08:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2275
- **最后更新**: 2026-05-20T15:26:52Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: Yang Yong (雍洋)

## AI分析总结

好的，根据您提供的README摘要和提交记录，以下是对昨日更新的要点分析：

### 1. 主要更新类型
本次更新全部为 **Bug修复**。

### 2. 关键变更点及其与项目整体方向的关系
- **修复MLU注意力机制（#1085）**：修复了在MLU（寒武纪机器学习单元）硬件上运行的注意力模块问题。这与项目“轻量级视频生成推理框架”的目标一致，旨在扩展对不同硬件（特别是国产AI芯片）的兼容性，提升框架的通用性和部署灵活性。
- **更新Animate模型，最后一段无需填充至77（#1084）**：优化了Animate模型的处理逻辑，去除了对最后一段序列不必要的填充操作。这直接关系到视频生成模型（如AnimateDiff）的推理效率，通过减少冗余计算来提升性能。
- **修复Animate模型分布式推理错误（#1083）**：解决了Animate模型在分布式推理场景下的一个Bug。这确保了框架在多卡、多节点环境下能够稳定运行，对于需要大规模、高效生成视频的应用场景至关重要。

### 3. 对项目的影响和潜在意义
- **提升稳定性和兼容性**：修复MLU和分布式推理的Bug，直接增强了框架在不同硬件和部署环境下的鲁棒性，降低了用户的使用门槛。
- **优化推理效率**：通过移除不必要的填充操作，减少了Animate模型的计算量，可能带来推理速度的提升和显存占用的降低，这对于视频生成这类计算密集型任务意义重大。
- **巩固核心模型支持**：所有修复都围绕“Animate模型”展开，表明项目正在积极打磨其核心支持的视频生成模型，确保其功能完整且高效。

### 4. 值得关注的技术点
- **硬件适配（MLU）**：项目明确支持MLU（寒武纪）硬件，体现了对国产AI生态的重视。修复其注意力机制，说明项目在底层算子层面进行了深度适配和优化。
- **序列长度优化**：`Last segment do not need pad to 77` 这一优化点，暗示了模型内部对输入序列有特定的长度约束（如77），而修复后避免了不必要的填充，这是一个典型的针对特定模型结构的性能优化技巧。
- **分布式推理**：修复分布式推理Bug，表明项目架构支持数据并行或模型并行，这是支撑大规模视频生成任务的基础能力。

### 5. 基于项目背景，这些提交如何影响项目发展
- **强化“轻量”与“高效”定位**：通过修复Bug和优化性能，项目朝着“轻量视频生成推理框架”的目标更进一步。这些更新让框架在更多硬件上运行得更快、更稳定，直接提升了其作为“推理框架”的实用价值。
- **提升开发者与用户信心**：快速修复关键模型（Animate）和硬件（MLU）上的问题，展示了项目团队的响应速度和维护能力，有助于吸引更多开发者和用户采用该框架进行视频生成应用的开发。
- **为未来扩展奠定基础**：对分布式推理和国产硬件的支持，为框架未来支持更复杂的模型、更大的分辨率和更长的视频生成任务铺平了道路。这些底层能力的完善是项目长期发展的基石。

## 详细提交记录

### [a9a2d9d](https://github.com/ModelTC/LightX2V/commit/a9a2d9d6fc8d1cc1df1efde2d8623896fb6232ea)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-05-20T15:18:27Z
- **提交信息**: Fix MLU Attention (#1085)

### [e286f34](https://github.com/ModelTC/LightX2V/commit/e286f34bb9f0e08f2f9e8ad0b6cf30e5ec3b7f26)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-05-20T14:38:17Z
- **提交信息**: Update animate model. Last segment do not need pad to 77 (#1084)

### [89d20a7](https://github.com/ModelTC/LightX2V/commit/89d20a7f090e069cab112209794bc1abd1abf215)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-05-20T13:44:25Z
- **提交信息**: Fix animate model dist infer bug (#1083)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2085
- **最后更新**: 2026-05-20T14:38:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5643
- **最后更新**: 2026-05-20T17:16:44Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: eigen, Brian K. Ryu

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结：

### 1. 主要更新类型

*   **功能新增 (feat):** 为MXFP4和MXFP8量化内核添加了新的`8x4`交错布局支持。
*   **Bug修复 (fix):** 修复了TGV（Triton GEMM Verification）和XQA MLA（Multi-head Latent Attention）参考正确性测试中的问题。

### 2. 关键变更点及其与项目整体方向的关系

*   **提交 `f925953` (功能新增):**
    *   **变更点:** 将CuTe-DSL（一种基于模板的GPU内核开发语言）后端的MXFP4和MXFP8量化内核，从仅支持`128x4`的交错布局，扩展到也支持`8x4`布局。这包括修改量化内核代码、添加JIT辅助函数来计算缩放因子偏移，并更新了编译缓存键。
    *   **与项目方向的关系:** FlashInfer的核心目标是提供高性能的GPU推理内核。支持更多的数据布局（如`8x4`）意味着它能适应更广泛的硬件特性和模型需求，从而提升在不同场景下的性能和灵活性。这直接服务于项目“高性能”和“通用性”的目标。

*   **提交 `fc9b2f6` (Bug修复):**
    *   **变更点:**
        1.  **TGV修复:** 修正了`tgv_gemm_sm100`跟踪中张量`b`的步幅（strides）设置，使其与内核的列主序（column-major）约定一致。同时，增加了布局断言，并修复了CUDA同步失败被错误跳过的问题。
        2.  **XQA MLA修复:** 在参考路径中保留了XQA MLA的beam维度，并移除了一个无效的64查询头的测试用例。
    *   **与项目方向的关系:** 这些修复确保了FlashInfer的测试框架（TGV）和核心注意力机制（XQA MLA）的正确性和可靠性。对于推理库而言，正确性是生命线。修复这些底层测试问题，为后续开发高性能、正确无误的内核提供了坚实基础，是项目走向成熟和稳定的关键一步。

### 3. 对项目的影响和潜在意义

*   **功能新增的影响:** 使CuTe-DSL后端在功能上与CUDA后端完全对齐，消除了一个功能差距。这为用户提供了更多选择，尤其是在需要特定布局以获得最佳性能的硬件（如B200）上。根据提交中的性能数据，`8x4`布局在某些场景下可能带来性能优势。
*   **Bug修复的影响:** 直接解决了两个已知问题（#3352, #3353），提升了测试套件的健壮性。这有助于开发者更早地发现和定位问题，避免将错误引入到生产级代码中。对于依赖FlashInfer的项目来说，这意味着更高的稳定性和可信度。

### 4. 值得关注的技术点

*   **CuTe-DSL与CUDA后端的对齐:** 项目正在积极地将CuTe-DSL后端的特性与成熟的CUDA后端对齐，这表明CuTe-DSL可能成为未来主要的开发方向，或者至少是一个同等重要的并行路径。
*   **JIT编译与缓存:** 提交中提到了`functools.cache`和JIT辅助函数，这表明FlashInfer大量使用了即时编译技术来生成针对特定硬件和布局优化的内核。`sf_layout`被加入到缓存键中，确保了不同布局的内核能被正确缓存和复用。
*   **测试框架的严谨性:** 修复TGV测试中关于张量步幅和CUDA错误处理的问题，体现了项目对测试质量的严格要求。TGV本身是一个用于验证Triton内核正确性的工具，其自身的正确性至关重要。
*   **量化技术的演进:** 支持MXFP4和MXFP8的多种交错布局，反映了业界对低精度、高吞吐量推理的持续追求。FlashInfer正在紧跟这一趋势，提供更灵活的量化内核。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **巩固“高性能”定位:** 通过增加新的布局支持，FlashInfer能够更好地利用现代GPU（如NVIDIA B200）的硬件特性，为用户提供更优的性能选择。这直接强化了其作为“高性能GPU内核库”的核心价值。
*   **提升“通用性”和“易用性”:**
    *   **通用性:** 支持更多布局意味着能适配更多模型和硬件配置。
    *   **易用性:** 修复测试框架的Bug，确保了开发者（包括FlashInfer团队自身）能够信赖测试结果，从而更高效地进行开发和调试。一个稳定可靠的测试套件是项目健康发展的基石。
*   **迈向更成熟的阶段:** 从“添加功能”到“修复测试框架的Bug”，这标志着项目正从快速迭代期进入一个更加注重稳定性、正确性和代码质量的成熟期。这对于一个旨在被广泛集成到生产环境中的推理库来说至关重要。

## 详细提交记录

### [f925953](https://github.com/flashinfer-ai/flashinfer/commit/f925953cec0cbad87fc185fd38d996477b98c715)

- **作者**: Brian K. Ryu
- **时间**: 2026-05-20T17:16:38Z
- **提交信息**: feat: Add 8x4 swizzle layout support to MXFP4 and MXFP8 CuTe-DSL kernels (#3357)

<!-- .github/pull_request_template.md -->

## 📌 Description
Brings the CuTe-DSL backend to parity with CUDA: `mxfp8_quantize` and
the MXFP4 path of `fp4_quantize` previously raised ValueError when asked
for 8x4. NVFP4 `cute-dsl` already supported 8x4.

### Changes ###
  
Kernels (`flashinfer/quantization/kernels/mxfp{4,8}_quantize.py`) --
Same pattern previously used for `NVFP4QuantizeSwizzledKernel`.
- Added `SF_LAYOUT_8x4` constant and threaded sf_layout through
`MXFP{4,8}QuantizeSwizzledKernel`.
- Added a `_compute_sf_offset` JIT helper that dispatches between
`compute_sf_index_swizzled_{128x4,8x4}_gpu`.
- Added `sf_layout` to the `@functools.cache` key on the compile
helpers.
  
Notes
- No public-API breakage (the new mxfp8 kwarg is keyword-only with False
default).
- High-level mxfp4_quantize still hardcodes 128x4 on both backends —
parity preserved; 8x4 reachable via fp4_quantize.

In all cases tested, the CUDA and CuTe-DSL backends have 100% bitwise
matches in quantized output and scale factor tensors. Perf numbers from
B200:
<details>
<summary>Backend performance comparisons from
bench_nvfp4_quantize_backend_comparison.py</summary>

<img width="1644" height="1477"
alt="nvfp4_quantize_backend_comparison_linear_bfloat16"
src="https://github.com/user-attachments/assets/c2da9699-f9df-4a0b-ba30-3991cc1a8fa6"
/>
<img width="1644" height="1478"
alt="nvfp4_quantize_backend_comparison_swizzled_128x4_bfloat16"
src="https://github.com/user-attachments/assets/320d4cae-dc8a-4dab-af90-82684704170d"
/>
<img width="1644" height="1478"
alt="nvfp4_quantize_backend_comparison_swizzled_8x4_bfloat16"
src="https://github.com/user-attachments/assets/b6e16502-6314-4d7b-afdb-f3af5a6e3685"
/>


</details>
<details>
<summary>Backend performance comparisons from
bench_mxfp4_quantize_backend_comparison.py</summary>

<img width="1644" height="1477"
alt="mxfp4_quantize_backend_comparison_linear_bfloat16"
src="https://github.com/user-attachments/assets/64841ea7-d023-491b-84f1-3fa65fa18721"
/>
<img width="1644" height="1478"
alt="mxfp4_quantize_backend_comparison_swizzled_128x4_bfloat16"
src="https://github.com/user-attachments/assets/5586914b-f698-4fc1-880f-68892440637a"
/>
<img width="1644" height="1478"
alt="mxfp4_quantize_backend_comparison_swizzled_8x4_bfloat16"
src="https://github.com/user-attachments/assets/15734f58-3ba9-47be-9653-76eafb98b3b9"
/>


</details>
<details>
<summary>Backend performance comparisons from
bench_mxfp8_quantize_backend_comparison.py</summary>
<img width="1644" height="1477"
alt="mxfp8_backend_comparison_linear_bfloat16"
src="https://github.com/user-attachments/assets/9af95a9c-fd66-4e2d-8277-3c1e8c1f7883"
/>
<img width="1644" height="1478"
alt="mxfp8_backend_comparison_swizzled_128x4_bfloat16"
src="https://github.com/user-attachments/assets/f32233e3-9dd4-4a11-8a8f-f17d8fd73185"
/>
<img width="1644" height="1478"
alt="mxfp8_backend_comparison_swizzled_8x4_bfloat16"
src="https://github.com/user-attachments/assets/b00f6ec8-1ce7-4215-999a-36b4ecddd455"
/>



</details>

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

<!-- Link any related issues here -->

#3356

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

### [fc9b2f6](https://github.com/flashinfer-ai/flashinfer/commit/fc9b2f64c15e9d2e9b2ecec47a9803317b63abfa)

- **作者**: eigen
- **时间**: 2026-05-20T17:11:46Z
- **提交信息**: fix(trace): repair TGV and XQA MLA reference tests (#3365)

## Summary
- construct `tgv_gemm_sm100` trace `b` with column-major strides,
matching the kernel contract
- add a TGV test layout assertion and avoid converting CUDA sync
failures into skips
- keep the XQA MLA beam dimension in the reference path and remove the
invalid 64-query-head positive case

Fixes #3352
Fixes #3353

## Testing
- reproduced the old TGV bad-layout failure on B200 with `torch
2.9.1+cu129`: `GPUassert: an illegal instruction was encountered`
- `python -m compileall flashinfer/trace/templates/page.py
tests/trace/test_tgv_gemm_sm100_reference_correctness.py
tests/trace/test_xqa_mla_reference_correctness.py`
- `FLASHINFER_WORKSPACE_BASE=/tmp/flashinfer-pr-cache
/tmp/flashinfer-cu129/bin/python -m pytest
tests/trace/test_tgv_gemm_sm100_reference_correctness.py -q -rs` -> 2
passed
- on SM120, reproduced `upstream/main` XQA MLA failure: `output with
shape [2, 1, 128, 512]` does not match broadcast shape `[2, 2, 128,
512]`
- on SM120, fix branch: `CUDA_VISIBLE_DEVICES=0
FLASHINFER_WORKSPACE_BASE=/tmp/flashinfer-sm120-fix-cache python -m
pytest tests/trace/test_xqa_mla_reference_correctness.py -q -rs
--tb=short` -> 2 passed

Co-authored-by: Avery Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3494
- **最后更新**: 2026-05-20T22:03:59Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Satyam Srivastava, Junda Su

## AI分析总结

好的，这是对 `hao-ai-lab/FastVideo` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **CI/自动化 (CI/Automation):** 主要更新集中在持续集成流程的改进上。
*   **Bug修复 (Bugfix):** 包含一个针对 Docker 构建上下文的修复。

### 2. 关键变更点及其与项目整体方向的关系

*   **新增 Dreamverse Docker 镜像工作流 (eef4732):**
    *   **变更点:** 为 `Dreamverse` 组件添加了自动构建 Docker 镜像的 CI 工作流。
    *   **与项目方向的关系:** 这与 FastVideo 提供“快速上手”和“文档”的目标高度一致。通过自动化构建 Docker 镜像，用户可以更便捷、更一致地部署和运行 `Dreamverse` 相关功能，降低了环境配置的门槛，符合项目“Fast”的核心理念。

*   **修复 Dreamverse Docker 上下文过大问题 (44fb84e):**
    *   **变更点:** 修复了上一个提交中引入的 Docker 构建上下文（context）过大的问题，这通常会导致构建速度慢或失败。
    *   **与项目方向的关系:** 这是一个典型的“快”的体现。优化 Docker 构建过程，确保 CI 流程高效、稳定，是保障项目快速迭代和用户快速部署的基础。

*   **组件时间性能 + 重置 HF 基线技能 (1c80371):**
    *   **变更点:** 在 CI 中增加了对组件性能（时间）的监控，并重置了与 Hugging Face (HF) 基线相关的技能或测试。
    *   **与项目方向的关系:** 这表明项目开始关注并量化各个组件的性能表现。通过 CI 自动化性能测试，可以防止性能退化，确保每次提交都不会拖慢模型训练或推理速度。重置 HF 基线技能可能意味着更新了与社区标准（Hugging Face）的对比基准，有助于项目在技术指标上保持竞争力。

### 3. 对项目的影响和潜在意义

*   **提升开发者体验:** Docker 镜像的自动化构建和修复，让开发者（尤其是新用户）能更快地搭建开发或测试环境，减少“在我机器上能跑”的问题。
*   **保障代码质量与性能:** 引入 CI 性能测试，意味着项目从“功能可用”向“性能可衡量、可优化”迈进。这有助于在早期发现性能瓶颈，维持项目“Fast”的声誉。
*   **增强项目可靠性:** 修复 Docker 上下文问题，避免了 CI 流程的潜在失败点，使整个自动化构建流水线更加健壮。

### 4. 值得关注的技术点

*   **Docker 构建上下文优化:** 这是一个常见的工程实践。通过 `.dockerignore` 文件或精细化的 `COPY` 指令来缩小构建上下文，可以显著提升 Docker 镜像的构建速度和 CI 效率。
*   **CI 中的性能回归测试:** 将性能测试集成到 CI 中是一个高级实践。它通常需要定义明确的性能指标（如每秒处理的帧数、训练一个 epoch 的时间）和阈值，当新代码导致性能下降时，CI 会发出告警。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **强化“快速上手”承诺:** 根据 README，项目强调“Quick Start”。Dreamverse Docker 镜像的自动化构建直接服务于这个目标，让用户能通过 `docker pull` 一步到位，无需手动安装复杂的依赖。
*   **支撑“文档”与“社区”生态:** 稳定、高效的 CI 是维护高质量文档和活跃社区的基础。当用户根据文档尝试使用 Docker 部署时，一个可靠、构建成功的镜像能极大提升信任感。同时，性能监控有助于项目在社区讨论（如 Weekly Dev Meeting）中提供数据支撑，证明其技术优势。
*   **迈向更成熟的工程化:** 从单纯的功能开发，到引入性能监控和优化 CI 流程，这些提交标志着 FastVideo 项目正从早期原型阶段，向一个更成熟、更注重工程质量和长期可维护性的开源项目演进。这有助于吸引更多企业级用户和贡献者。

## 详细提交记录

### [1c80371](https://github.com/hao-ai-lab/FastVideo/commit/1c80371b27a79eb9258a0222f069bc46ddecb88e)

- **作者**: Satyam Srivastava
- **时间**: 2026-05-20T20:51:11Z
- **提交信息**: [ci] Component time performance + reseed hf baseline skill (#1292)

Co-authored-by: Satyam Srivastava <satyam53@Satyams-MacBook-Air.local>

### [eef4732](https://github.com/hao-ai-lab/FastVideo/commit/eef473225db1fcf75ab34cda8be70869ca1f99b7)

- **作者**: Junda Su
- **时间**: 2026-05-20T20:50:02Z
- **提交信息**: [ci] Add Dreamverse Docker image workflow (#1369)

### [44fb84e](https://github.com/hao-ai-lab/FastVideo/commit/44fb84ef6ab63b4d372cda4dfca91ea1a0a05d91)

- **作者**: Junda Su
- **时间**: 2026-05-20T20:38:52Z
- **提交信息**: [bugfix]: shrink Dreamverse Docker context (#1368)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33674
- **最后更新**: 2026-05-20T23:22:02Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: Wang, Yi, Steven Liu, YiYi Xu

## AI分析总结

好的，根据您提供的 `huggingface/diffusers` 仓库的README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型

- **CI/CD 流程改进** (提交 1, 5)
- **Bug 修复** (提交 2)
- **文档更新** (提交 3, 6)
- **API 兼容性更新** (提交 4)

### 2. 关键变更点及其与项目整体方向的关系

-   **CI/CD 流程改进 (提交 1 & 5):**
    -   **变更点:** 修复了 `claude_review` CI 流程中，针对非Fork PR的后续PR总是从 `main` 分支创建，导致与PR基础分支冲突的问题。现在会直接以PR的源分支为目标。同时，将 `print_env` 步骤替换为 `diffusers-cli env` 命令。
    -   **与项目方向的关系:** 作为一个大型开源项目，稳定且高效的CI/CD流程是保障代码质量和开发效率的基石。这些改进直接提升了自动化审查（特别是AI辅助审查）的可靠性，并简化了环境信息收集，有助于维护团队更快地迭代和合并代码。

-   **Bug 修复 (提交 2):**
    -   **变更点:** 修复了GGUF量化参数形状检查时的错误信息。之前的错误信息是自指涉的（打印了 `inferred_shape` vs `loaded_param_shape`，而 `inferred_shape` 又源自 `loaded_param_shape`），无法提供有效信息。现在修正为打印 `current_param_shape`（模型期望的形状）和 `inferred_shape`（量化权重解码后的形状）。
    -   **与项目方向的关系:** 该项目支持多种模型格式（如GGUF），并致力于提供清晰的错误信息以帮助用户调试。这个修复直接提升了用户在使用量化模型时的调试体验，体现了项目对细节和用户体验的关注。

-   **文档更新 (提交 3 & 6):**
    -   **变更点:** 更新了 `agents docs` 中的 `pipelines.md`，明确了pipeline方法何时应为公开方法、私有方法或模块级函数。同时，移除了文档中的 `pipeline examples` 部分。
    -   **与项目方向的关系:** 清晰的文档是项目成功的关键。`pipelines.md` 的更新为开发者编写pipeline提供了更明确的指导，有助于保持代码库的一致性和可维护性。移除过时或冗余的示例部分，则是对文档结构的优化，使其更聚焦、更易于导航。

-   **API 兼容性更新 (提交 4):**
    -   **变更点:** 将 `safetensors.torch._tobytes` 更新为 `safetensors.torch._to_ndarray`，以适配 `safetensors 0.8.0rc0` 版本的API变更。
    -   **与项目方向的关系:** 该项目重度依赖 `safetensors` 库进行安全、高效的张量存储。及时跟进上游依赖的API变化，确保了项目对新版本库的兼容性，避免了因依赖版本升级而导致的潜在崩溃。

### 3. 对项目的影响和潜在意义

-   **提升开发效率:** CI流程的改进（特别是针对AI审查的修复）将减少因流程问题导致的失败，加速代码审查和合并过程。
-   **改善用户体验:** GGUF错误信息的修复让用户能更快地定位和解决模型加载问题，降低了使用门槛。
-   **增强代码健壮性:** 及时更新API调用，确保了项目与核心依赖库的兼容性，避免了未来可能出现的兼容性问题。
-   **维护项目健康度:** 文档的持续优化和清理，有助于新老贡献者更好地理解项目架构和最佳实践，对项目的长期健康发展至关重要。

### 4. 值得关注的技术点

-   **AI辅助代码审查的CI流程设计:** 提交1展示了如何设计一个与AI审查工具（Claude）协同工作的CI流程，特别是处理分支策略和Fork PR的边界情况，这对于其他希望引入AI辅助开发流程的项目有参考价值。
-   **GGUF量化参数形状检查的调试技巧:** 提交2修复的错误信息问题是一个典型的“调试信息本身有误”的案例，提醒我们在编写错误日志时，必须确保其内容能真实反映比较的双方，而不是循环引用。
-   **`safetensors` API 变更:** 关注 `safetensors` 库的API变化，特别是内部函数（以下划线开头）的变更，表明项目在紧跟上游发展，并愿意为兼容性做出及时调整。

### 5. 基于项目背景的综合影响

-   **作为核心库的稳定性保障:** `diffusers` 是HuggingFace生态中用于扩散模型的核心库。昨日的更新，特别是CI流程和API兼容性的修复，直接保障了库的稳定性和开发流程的顺畅，这对于一个被成千上万项目依赖的基础库至关重要。
-   **对模型格式的支持与优化:** 修复GGUF相关的错误信息，表明项目在持续关注并优化对非标准模型格式（如GGUF，常用于量化模型）的支持，这有助于扩大其用户群，特别是那些在资源受限设备上部署模型的用户。
-   **开发者体验的持续投入:** 文档的更新和CI流程的改进，都体现了项目团队对开发者体验（DX）的重视。通过降低贡献门槛、提供清晰指南和自动化工具，项目能够吸引更多社区贡献，形成良性循环，加速创新。

## 详细提交记录

### [fece08a](https://github.com/huggingface/diffusers/commit/fece08aa6252467b269ca74cc72cef41809e6aaf)

- **作者**: YiYi Xu
- **时间**: 2026-05-20T23:21:51Z
- **提交信息**: [CI] claude_review: target source PR's branch for follow-up PRs (#13774)

* [CI] claude_review: target source PR's branch for follow-up PRs

The follow-up PR was always cut from main, so once main moved on from the
PR's base the cherry-pick conflicted and the run failed (see run
26191835696). For non-fork PRs we now target the PR's own head branch
instead — Claude's edits apply cleanly regardless of how main has diverged,
and merging the follow-up folds them into the original PR. Fork PRs still
target the default branch since we can't push to a fork.

Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

* [CI] claude_review: skip COMMIT THIS on fork PRs

Falling back to main as the base for fork PRs hits the same cherry-pick
conflict pattern the previous commit fixed for source PRs, and we can't
push to the fork's branch anyway. Bail early with a friendly comment
pointing users to apply Claude's suggestions manually or open an issue.

Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [6a65a37](https://github.com/huggingface/diffusers/commit/6a65a3735b5352feedaeffbd669cfd614845615b)

- **作者**: Ricardo-M-L
- **时间**: 2026-05-20T22:03:10Z
- **提交信息**: fix(gguf): correct mismatched-shape error message in check_quantized_param_shape (#13504)

fix(gguf): correct mismatched-shape error message

check_quantized_param_shape compares inferred_shape against
current_param_shape, but the error message printed inferred_shape
vs loaded_param_shape — and inferred_shape is derived from
loaded_param_shape, so the reported mismatch was effectively
self-referential and gave no signal about the model's expected shape.

Print current_param_shape (what the model expected) vs inferred_shape
(what the quantized weight decodes to) so the two sides of the
comparison are actually visible.

Noted by @Vargol in #13001.

### [0b8c0c0](https://github.com/huggingface/diffusers/commit/0b8c0c0bc8331e2b6013e95dd624aed588669fba)

- **作者**: YiYi Xu
- **时间**: 2026-05-20T22:02:03Z
- **提交信息**: [agents docs] update pipelines.md:  (#13570)

* [agents docs] pipelines.md: be deliberate about pipeline methods

Adds a gotcha covering when a pipeline method should be public (a step
in __call__'s lifecycle) vs private/module-level (only used by another
method), and the preference to absorb single-use helpers when small.

Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

* Update .ai/pipelines.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update .ai/pipelines.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

---------

Co-authored-by: yiyi@huggingface.co <yiyi@ip-26-0-161-123.ec2.internal>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

### [37467de](https://github.com/huggingface/diffusers/commit/37467de2b6c1a3e3e07efa223fb8eb410d41744e)

- **作者**: Wang, Yi
- **时间**: 2026-05-20T11:08:55Z
- **提交信息**: update safetensors.torch._tobytes to safetensors.torch._to_ndarray (#13770)

since the api is changed in safetensors 0.8.0rc0

Signed-off-by: Wang, Yi <yi.a.wang@intel.com>

### [9c4e201](https://github.com/huggingface/diffusers/commit/9c4e201dd1cf7d16449c3f4e9affc556d7bc3404)

- **作者**: Dhruv Nair
- **时间**: 2026-05-20T11:01:43Z
- **提交信息**: [CI] Replace print_env step in CI with diffusers-cli env (#13662)

update

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [9a2923d](https://github.com/huggingface/diffusers/commit/9a2923d501f2abbc176441e7e12a9b2f5cfb7124)

- **作者**: Steven Liu
- **时间**: 2026-05-20T09:17:41Z
- **提交信息**: [docs] remove pipeline examples section (#13771)

* docs

* links

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
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


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12444
- **最后更新**: 2026-05-20T23:10:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 28060
- **最后更新**: 2026-05-20T23:24:01Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 21
- **主要提交者**: Kangyan-Zhou, BingjiaWang, Matt Van Horn

## AI分析总结

好的，这是对 `sgl-project/sglang` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **功能新增 (Feature)**: 支持通用worker发现、可插拔RadixCache后端、FlashInfer MoE runner、通用`num_tokens_per_bs`验证。
*   **Bug修复 (Bug Fix)**: 修复RadixTree LRU引用循环泄漏、Chunked Prefill不完整、请求状态泄漏、非流式推理内容问题、GLM-Image编辑支持、Docker镜像依赖缺失。
*   **性能优化 (Perf)**: 新增`prepare_prefill_qkv`钩子与FP8量化JIT内核、优化MQA Logits内存比例配置。
*   **重构 (Refactor)**: 将`NSA`重命名为`DSA`、清理`prepare_for_extend`中的死代码、合并`seq_lens_cpu/sum`维护逻辑。
*   **测试与CI (Test/CI)**: 新增前向占用率测试套件、整合核心与模型端到端测试、调整PR测试调度、为sgl-router添加PR测试工作流。
*   **其他**: 更新`CODEOWNERS`、添加CI权限、修复Docker镜像依赖。

### 2. 关键变更点及其与项目整体方向的关系

*   **可扩展性与灵活性增强**:
    *   `[SMG] Support regular worker discovery alongside PD workers` (b7d0df4): 在IGW模式下支持通用worker发现，使项目能更灵活地管理异构计算资源，符合其作为高性能推理引擎的定位。
    *   `[radix cache] pluggable RadixCache factory` (6e0b7f3): 引入可插拔的RadixCache后端，允许用户根据场景选择或自定义缓存策略，增强了系统的模块化和可定制性。
*   **性能与效率提升**:
    *   `[perf] prepare_prefill_qkv hook + fp8 quantize jit kernel` (1a17d75): 新增的钩子和FP8量化内核直接针对Prefill阶段进行优化，这是推理延迟的关键瓶颈，体现了项目对极致性能的追求。
    *   `[DSA] Make MQA logits free memory ratio configurable` (801d7e3): 将MQA Logits内存比例可配置化，允许用户根据硬件和模型调整内存占用，提升资源利用率。
*   **代码质量与维护性改进**:
    *   `[Refactor] Rename NSA → DSA` (8131641, bdacb1b): 大规模重命名，统一术语，减少混淆，提升代码库的清晰度和可维护性。
    *   `[Scheduler] fix chunked prefill not always being full` (371b6c9): 修复调度器核心逻辑，确保Chunked Prefill机制正确工作，直接影响推理吞吐和稳定性。
*   **强化测试与可靠性**:
    *   `[Test] Add fwd_occupancy sanity kit` (1bd4f94): 新增前向占用率测试，有助于及早发现性能回归。
    *   `[Test] Stage-a sanity kits; consolidate core/ + models_e2e/ tests` (614672f): 整合测试套件，提高测试效率和覆盖率，保障项目质量。

### 3. 对项目的影响和潜在意义

*   **提升生产环境适应性**: 通用worker发现、可配置内存比例、可插拔缓存等特性，使SGLang能更好地适应多样化的生产部署环境，降低运维复杂度。
*   **巩固高性能推理定位**: 针对Prefill阶段的FP8量化优化，以及Chunked Prefill的Bug修复，将进一步提升SGLang在长序列、高吞吐场景下的性能优势。
*   **改善开发者体验**: 大规模重命名和代码清理降低了新贡献者的理解门槛。新增的测试套件和CI工作流有助于维护代码质量，加速开发迭代。
*   **扩展模型支持**: 对GLM-Image编辑的修复和对Qwen3.5/3_next的NPU支持，表明项目正在持续扩展对不同模型和硬件的支持。

### 4. 值得关注的技术点

*   **FP8量化JIT内核**: 这是对Prefill阶段进行极致优化的尝试，可能涉及高度定制化的CUDA/Triton内核，值得关注其实现细节和性能收益。
*   **可插拔RadixCache工厂**: 这种设计模式允许社区贡献不同的缓存实现（如基于LRU、LFU或特定硬件优化的），是系统架构灵活性的重要体现。
*   **FlashInfer MoE Runner**: 集成FlashInfer的AlltoAll后端来处理MoE层，这可能是在大规模分布式推理场景下优化通信瓶颈的关键技术。
*   **`prepare_prefill_qkv` Hook**: 这种钩子机制为未来更复杂的优化（如动态量化、稀疏计算）提供了入口点，是一种前瞻性的设计。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **强化核心优势**: 项目README强调其高性能、低延迟和易用性。昨日的提交（特别是FP8优化、Chunked Prefill修复、可配置内存）直接强化了这些核心优势，使其在LLM推理引擎的竞争中保持领先。
*   **迈向更成熟的平台**: 通过引入可插拔组件、统一术语、增强测试，SGLang正从一个功能强大的工具，转变为一个架构更清晰、更易于扩展和维护的平台。这有助于吸引更多社区

## 详细提交记录

### [b7d0df4](https://github.com/sgl-project/sglang/commit/b7d0df4b6f378800586c65d2457cdf52bc1b10d3)

- **作者**: gruner
- **时间**: 2026-05-20T23:23:55Z
- **提交信息**: [SMG] Support regular worker discovery alongside PD workers in IGW mode (#25294)

Co-authored-by: Amit Gruner <agruner@crusoe.ai>

### [9f2bc24](https://github.com/sgl-project/sglang/commit/9f2bc24b3575f5240cd94af5a6bb2ee701c35b0c)

- **作者**: Kaixi
- **时间**: 2026-05-20T22:41:28Z
- **提交信息**: Fix/dsv4 flash eagle dummy ima (#25892)

### [ce7141e](https://github.com/sgl-project/sglang/commit/ce7141ef98767f756ccc949f5716f3633afad01e)

- **作者**: BingjiaWang
- **时间**: 2026-05-20T22:24:10Z
- **提交信息**: add git gemm warpper for dispatch_bf16_fp32_backend (#25860)

### [371b6c9](https://github.com/sgl-project/sglang/commit/371b6c9ea0b4484147b12264035042e4808ec9c6)

- **作者**: Hanming Lu
- **时间**: 2026-05-20T22:03:11Z
- **提交信息**: [Scheduler] fix chunked prefill not always being full (#25741)

### [1a17d75](https://github.com/sgl-project/sglang/commit/1a17d753f166c2df6e876af8acb95001a2a86f67)

- **作者**: Qiaolin Yu
- **时间**: 2026-05-20T21:20:49Z
- **提交信息**: [perf] prepare_prefill_qkv hook + fp8 quantize jit kernel (#25460)

### [dac7876](https://github.com/sgl-project/sglang/commit/dac78768f06a55d4b7de7f9ab1f6ffbd869693ff)

- **作者**: Yuzhen Zhou
- **时间**: 2026-05-20T19:45:09Z
- **提交信息**: [RL][TITO] Preserve whitespace in reasoning parser outputs (#24251)

### [801d7e3](https://github.com/sgl-project/sglang/commit/801d7e3eed3866423d92fc9f7c5e80c095371c85)

- **作者**: YAMY
- **时间**: 2026-05-20T19:27:16Z
- **提交信息**: [DSA] Make MQA logits free memory ratio configurable (#25859)

### [5e7bf73](https://github.com/sgl-project/sglang/commit/5e7bf73757394309c4a1a38e0f326d178d3b555b)

- **作者**: Ratish P
- **时间**: 2026-05-20T18:41:46Z
- **提交信息**: Fix bench_serving non-stream reasoning content (#25298)

### [1f209b4](https://github.com/sgl-project/sglang/commit/1f209b443331e32d0b2f6ac8a2c46a4ed52c682f)

- **作者**: jasonjk-park
- **时间**: 2026-05-20T18:34:45Z
- **提交信息**: Add support for generic num_tokens_per_bs in TARGET_VERIFY (#25681)

### [61ac679](https://github.com/sgl-project/sglang/commit/61ac6792e650a30759ca39821e1368e1f8e806c0)

- **作者**: Lianmin Zheng
- **时间**: 2026-05-20T18:19:43Z
- **提交信息**: Add DevashishLal-CB to CI_PERMISSIONS.json (#25908)

### [33c57b8](https://github.com/sgl-project/sglang/commit/33c57b8716ce78f1d3d7220f40a8e30dc7b5cc42)

- **作者**: Mark Smith
- **时间**: 2026-05-20T17:06:05Z
- **提交信息**: [Bug][RadixTree] Fix LRU list reference cycle leak in radix_cache (#25770)

Co-authored-by: zhangjiadong1@corp.netease.com <zhangjiadong1@corp.netease.com>

### [6e0b7f3](https://github.com/sgl-project/sglang/commit/6e0b7f35adaa7056ae662b16b0ad1eace2b38e5c)

- **作者**: Jialin Ouyang
- **时间**: 2026-05-20T17:05:04Z
- **提交信息**: [radix cache] pluggable RadixCache factory (--radix-cache-backend) (#25101)

### [ccbbae0](https://github.com/sgl-project/sglang/commit/ccbbae00eaeaff7f7c5cf3ded5877831f0db8239)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-20T14:15:25Z
- **提交信息**: [codex] Reland Wan2.2 ModelOpt CI checkpoints (#25857)

### [55ba03d](https://github.com/sgl-project/sglang/commit/55ba03db6a46a676470096a9da1fdae5ad7d0e6f)

- **作者**: Liwansi
- **时间**: 2026-05-20T12:22:10Z
- **提交信息**: [NPU]use triton split_qkvgate_gemma_rmsnorm_rope for Qwen3.5 and Qwen3_next (#23925)

### [34d3e23](https://github.com/sgl-project/sglang/commit/34d3e23232746bba5843414fbfa31f91c5a40da8)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-20T11:42:26Z
- **提交信息**: spec_v2: consolidate seq_lens_cpu/sum maintenance into helper (#25818)

### [9b005d3](https://github.com/sgl-project/sglang/commit/9b005d3608aa6f207b9ec131a520d6daab016faa)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-20T11:39:47Z
- **提交信息**: disagg prebuilt: drop dead prepare_for_extend shift (#25819)

### [eccd5c8](https://github.com/sgl-project/sglang/commit/eccd5c8253057603914c899e1dc677a43f0426a4)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-20T10:58:54Z
- **提交信息**: pr-test: schedule 3x -> 2x; fix extra gate skipped on schedule (#25872)

### [1bd4f94](https://github.com/sgl-project/sglang/commit/1bd4f94598a621cf5e8c27686311e92134e9edb0)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-20T10:34:37Z
- **提交信息**: [Test] Add fwd_occupancy sanity kit (#25886)

### [47979fb](https://github.com/sgl-project/sglang/commit/47979fb252ce0954d1076c67183879bb52e17476)

- **作者**: Chi McIsaac
- **时间**: 2026-05-20T09:11:51Z
- **提交信息**: [diffusion] fix: fix GLM-Image /v1/images/edits support (#25697)

### [614672f](https://github.com/sgl-project/sglang/commit/614672fea5e600ed3d2fa0a0ae89fd2b67216c7c)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-20T08:58:48Z
- **提交信息**: [Test] Stage-a sanity kits; consolidate core/ + models_e2e/ tests (#25831)

### [24d27c2](https://github.com/sgl-project/sglang/commit/24d27c203547cbb9fe23ad8adab1a981c4ee71a1)

- **作者**: Yuhong Guo
- **时间**: 2026-05-20T08:32:44Z
- **提交信息**: [BugFix] Fix rid_to_state leak for aborted queued requests (#24070)

### [e99f87c](https://github.com/sgl-project/sglang/commit/e99f87c974a07a5400eb96cea1a05f886c5d5b6a)

- **作者**: Matt Van Horn
- **时间**: 2026-05-20T07:46:32Z
- **提交信息**: fix: add missing distro dependency to runtime docker image (#25817)

Co-authored-by: Matt Van Horn <455140+mvanhorn@users.noreply.github.com>

### [044649c](https://github.com/sgl-project/sglang/commit/044649c23abe32d4596a6b0b6c5aa4a16b4d2d76)

- **作者**: Sam (Kesen Li)
- **时间**: 2026-05-20T07:36:26Z
- **提交信息**: feat: Support flashinfer_cutedsl MoE runner with flashinfer alltoall backend (#22669)

Co-authored-by: Trevor Morris <tmorris@nvidia.com>
Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>

### [bdacb1b](https://github.com/sgl-project/sglang/commit/bdacb1be4d27f4f488d2f9fa9f0b363c57a8fce9)

- **作者**: Cheng Wan
- **时间**: 2026-05-20T07:31:23Z
- **提交信息**: Update CODEOWNERS to replace 'nsa' with 'dsa' (#25861)

### [a184352](https://github.com/sgl-project/sglang/commit/a1843524a5ccba645b361d9e22ebbc833f1feaea)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-20T07:20:03Z
- **提交信息**: ci(sgl-router): add PR test workflow (pre-positioned for feature PR) (#25854)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [8131641](https://github.com/sgl-project/sglang/commit/8131641bc66eb07ba42cdaea58dca8a3c8c0340d)

- **作者**: Cheng Wan
- **时间**: 2026-05-20T07:18:04Z
- **提交信息**: [Refactor] Rename NSA → DSA: user-facing aliases, file/class/import rename (#25821)

Co-authored-by: Claude Sonnet 4.6 (1M context) <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1175
- **最后更新**: 2026-05-20T09:27:03Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 昨日更新要点总结

**1. 主要更新类型**
*   **功能新增 (Feature)**：本次提交引入了新的功能特性。

**2. 关键变更点及其与项目整体方向的关系**
*   **变更点**：使“逐层卸载（layerwise offload）”功能与PyTorch的 `torch.compile` 兼容。
*   **与项目方向的关系**：
    *   `cache-dit` 是一个面向 **Diffusion Transformers (DiTs)** 的推理引擎，其核心优势在于 **缓存、并行化和量化**。
    *   `torch.compile` 是PyTorch 2.0引入的关键优化技术，通过JIT编译将模型图编译成更高效的核函数，从而大幅提升推理速度。
    *   “逐层卸载”是一种内存优化技术，用于在显存有限的情况下，将模型的部分层（如注意力层）临时卸载到CPU内存，计算时再加载回来，从而支持更大模型或更大批量。
    *   **本次更新将这两者结合**，意味着用户现在可以在启用 `torch.compile` 进行图优化的同时，也使用“逐层卸载”来管理显存。这解决了之前两者可能冲突的问题，是项目在**性能优化**和**内存效率**两个关键方向上的重要融合。

**3. 对项目的影响和潜在意义**
*   **影响**：显著提升了 `cache-dit` 的实用性和性能上限。用户现在可以同时获得 `torch.compile` 带来的计算加速和“逐层卸载”带来的显存节省。
*   **潜在意义**：
    *   **降低硬件门槛**：允许在更小显存的GPU上运行更大的DiT模型，同时不牺牲编译带来的速度优势。
    *   **提升用户体验**：简化了用户配置，无需在“编译加速”和“显存节省”之间做二选一的权衡。
    *   **增强竞争力**：使 `cache-dit` 在处理大规模DiT模型推理时，相比其他方案更具优势。

**4. 值得关注的技术点**
*   **`torch.compile` 与自定义内存管理的兼容性**：`torch.compile` 通常要求模型图是静态的，而“逐层卸载”会动态改变内存布局和计算图。实现两者的兼容需要精细的工程技巧，例如可能涉及使用 `torch.compiler` 的特定API（如 `torch.compiler.disable` 或自定义的图断点）来标记卸载区域，或者确保卸载操作本身是“可编译”的。这是本次提交的核心技术难点。

**5. 基于项目背景，这些提交如何影响项目发展**
*   **强化核心定位**：`cache-dit` 定位为“PyTorch原生”的推理引擎。本次更新完美契合了这一理念，因为它拥抱了PyTorch生态中最强大的优化工具 `torch.compile`，而不是另起炉灶。
*   **推动规模化部署**：通过同时解决速度和内存两大瓶颈，该更新为 `cache-dit` 在需要高吞吐、低延迟且受限于显存的生产环境（如云服务、边缘设备）中部署更大型的DiT模型铺平了道路。
*   **巩固技术壁垒**：在“缓存”和“量化”之外，`cache-dit` 现在又多了一个独特的技术组合点：“编译加速 + 逐层卸载”。这使其在技术深度和实用性上进一步领先于简单的模型加载方案。

## 详细提交记录

### [36713e6](https://github.com/vipshop/cache-dit/commit/36713e62536aec484663d8150cf994fc1000d180)

- **作者**: DefTruth
- **时间**: 2026-05-20T09:13:40Z
- **提交信息**: feat: make layerwise offload compatible w/ compile (#1014)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 80579
- **最后更新**: 2026-05-20T23:18:03Z

## 提交统计

- **昨日提交总数**: 23
- **提交者数量**: 22
- **主要提交者**: xiangdong, hallerite, Aaron Hao

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **性能优化 (Performance):** 约 5 项，包括 FP8 内核优化、Triton 内核降级、FlashInfer 内核集成等。
*   **Bug 修复 (Bugfix):** 约 4 项，涉及 CI 导入、FP8 内核启用条件、结构化输出、工具解析器。
*   **功能新增 (Feature):** 约 3 项，包括自定义内存分配器、非 MTP 投机解码、路由专家支持。
*   **文档更新 (Documentation):** 约 2 项，包括 CLI 指南同步、Mermaid 图表支持、KV-cache 传输文档。
*   **重构与杂项 (Refactor/Misc):** 约 4 项，包括代码清理、依赖降级、代码所有者更新、CI 阈值调整。
*   **硬件支持 (Hardware Support):** 约 3 项，包括 ROCm、Intel GPU (XPU)、NVIDIA Blackwell (SM120/121) 相关更新。

### 2. 关键变更点及其与项目整体方向的关系

*   **性能与效率 (核心目标):**
    *   **FP8 内核优化 (commit 6, 12):** 优化了 `CutlassFP8ScaledMMLinearKernel`，在需要预权重处理时实现 13.5% 的 TTFT 提升。同时修复了 SM12.1 上 FP8 内核的启用条件。这直接服务于项目“快速、廉价”的 LLM 服务目标。
    *   **FlashInfer 内核集成 (commit 7):** 为 NVIDIA SM120/121 (Blackwell) 架构集成了 FlashInfer 的 MoE 和 FP4 GEMM 内核。这标志着 vLLM 对最新一代 NVIDIA 硬件的深度适配和性能挖掘。
    *   **投机解码扩展 (commit 15):** 为 NemotronH 模型支持非 MTP (Multi-Token Prediction) 的投机解码。这扩展了投机解码的适用范围，是提升推理吞吐量的关键技术。
    *   **依赖降级 (commit 2, 3):** 将 `nvidia-cutlass-dsl` 和 `triton_kernels` 降级到特定版本。这通常是为了规避新版本中的回归问题或兼容性问题，以维持当前性能基准的稳定性。

*   **功能与兼容性 (易用性):**
    *   **路由专家支持 (commit 9):** 在 OpenAI 兼容的 API 入口中添加了 `routed experts` 支持。这增强了 vLLM 对 MoE 架构模型的兼容性和控制能力，使其更易于集成到现有工作流中。
    *   **自定义内存分配器 (commit 16):** 支持手动启用 `cumem allocator`。这为高级用户提供了更精细的内存管理控制，有助于在特定场景下优化显存使用。
    *   **结构化输出修复 (commit 13):** 修复了结构化标签导致生成不受约束的 Bug。结构化输出是 LLM 服务的关键功能，此修复提升了其可靠性和实用性。

*   **硬件生态扩展 (广泛支持):**
    *   **ROCm 优化 (commit 1, 4):** 为 AMD ROCm 平台添加了 `QuickReduce` 的最小尺寸覆盖和编解码阈值，并更新了代码所有者。这体现了项目对 AMD 生态的持续投入和优化。
    *   **Intel GPU CI (commit 19):** 在 Intel GPU 的 CI 中增加了服务器模型测试。这表明 vLLM 正在积极扩展对 Intel 硬件的支持，并确保其稳定性。

*   **架构与稳定性 (工程实践):**
    *   **Libtorch ABI 迁移 (commit 22):** 继续将激活内核、GPTQ、GGUF 等模块迁移到 libtorch 稳定 ABI。这是一个长期的重构工作，旨在提升库的二进制兼容性和维护性。
    *   **代码清理 (commit 14):** 移除死代码，是持续提升代码质量和可维护性的体现。

### 3. 对项目的影响和潜在意义

*   **性能提升显著:** FP8 内核优化带来的 13.5% TTFT 提升，对于延迟敏感的应用场景（如对话、实时交互）意义重大。
*   **硬件支持领先:** 对 NVIDIA Blackwell 架构的快速适配（FlashInfer 内核集成）和 AMD ROCm 的持续优化，巩固了 vLLM 作为主流硬件平台首选推理引擎的地位。
*   **功能完善:** 路由专家、投机解码扩展和结构化输出修复，使 vLLM 在功能完整性和易用性上更接近生产级要求。
*   **工程稳健性:** 依赖降级、代码清理和 ABI 迁移等工作，虽然不直接带来新功能，但能有效减少潜在问题，提升项目的长期稳定性和可维护性。

### 4. 值得关注的技术点

*   **`CutlassFP8ScaledMMLinearKernel` 的预权重处理优化:** 这是一个具体的性能优化案例，值得关注其实现原理，可能对其他内核的优化有借鉴意义。
*   **FlashInfer 在 SM120/121 上的 MoE 和 FP4 内核:** 这是 vLLM 适配最新 NVIDIA 架构的关键一步，其性能表现将直接影响 Blackwell 用户的体验。
*   **非

## 详细提交记录

### [bde560e](https://github.com/vllm-project/vllm/commit/bde560ed6e1dc889debf68410ccbcb00b749513b)

- **作者**: akii96
- **时间**: 2026-05-20T22:46:51Z
- **提交信息**: [ROCm] Add QuickReduce min-size override and codec threshold (#41675)

Signed-off-by: <>

### [6dc0a71](https://github.com/vllm-project/vllm/commit/6dc0a71843878ef45e29d4732147290b797b70fd)

- **作者**: Jiangyun Zhu
- **时间**: 2026-05-20T21:19:50Z
- **提交信息**: [Misc] downgrade nvidia-cutlass-dsl to 4.5.0 (#43230)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [5774aad](https://github.com/vllm-project/vllm/commit/5774aad9c5b67c5bb67bb7d306a9652a035ed0aa)

- **作者**: Michael Goin
- **时间**: 2026-05-20T21:13:12Z
- **提交信息**: [Perf][gpt-oss] Downgrade triton_kernels to v3.5.1 (#43135)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [452baa8](https://github.com/vllm-project/vllm/commit/452baa860b1169787cc8540a1772c4d96f682c40)

- **作者**: Douglas Lehr
- **时间**: 2026-05-20T21:10:44Z
- **提交信息**: Add dllehr-amd to CODEOWNERS and committers list (#42772)

Signed-off-by: Douglas Lehr <Doug.Lehr@amd.com>

### [2a43b40](https://github.com/vllm-project/vllm/commit/2a43b407c5093b1255a172139da6a5151f410b7a)

- **作者**: Flora Feng
- **时间**: 2026-05-20T18:59:12Z
- **提交信息**: [Bugfix][CI] Add missing import of pad_nvfp4_activation_for_cutlass in flashinfer (#43237)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [53ff50f](https://github.com/vllm-project/vllm/commit/53ff50fcd3d2012a406e5053026ea6a46c88b2b6)

- **作者**: Wentao Ye
- **时间**: 2026-05-20T18:57:42Z
- **提交信息**: [Perf] Optimize `CutlassFP8ScaledMMLinearKernel` when padding needed by pre-weight processing, 13.5% TTFT improvement (#42651)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [363fc84](https://github.com/vllm-project/vllm/commit/363fc84407f8c966c1cee6786e45e9e6ab289684)

- **作者**: meena-at-work
- **时间**: 2026-05-20T17:21:11Z
- **提交信息**: Integrate flashinfer b12x MoE and FP4 GEMM kernels for SM120/121 (#40082)

Signed-off-by: Meenakshi Venkataraman <meenakshiv@nvidia.com>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [f2d5e3d](https://github.com/vllm-project/vllm/commit/f2d5e3d3aeac4cb1f6d285e4a567a502ae507777)

- **作者**: haosdent
- **时间**: 2026-05-20T17:00:24Z
- **提交信息**: [CI] Lower granite-4.0-h-tiny gsm8k threshold for Hybrid SSM NixlConnector PD accuracy tests (4 GPUs) (#43186)

Signed-off-by: haosdent <haosdent@gmail.com>
Signed-off-by: NickLucche <nlucches@redhat.com>
Co-authored-by: NickLucche <nlucches@redhat.com>

### [2d6b348](https://github.com/vllm-project/vllm/commit/2d6b3489b9a325988ad52507236409747d2098a7)

- **作者**: Aaron Hao
- **时间**: 2026-05-20T16:07:59Z
- **提交信息**: [R3] Add routed experts to openai entrypoint  (#38939)

Signed-off-by: ahao-anyscale <ahao@anyscale.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [9c78c99](https://github.com/vllm-project/vllm/commit/9c78c99995b70726f9ea929ff2e535d6303383d6)

- **作者**: Vadim Gimpelson
- **时间**: 2026-05-20T15:50:24Z
- **提交信息**: [MISC] Fix symm_mem cap-equal gate; log AR backend selection (#42993)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>

### [a10d691](https://github.com/vllm-project/vllm/commit/a10d69116cb25c8137eeb3f320add71d4e04fda9)

- **作者**: Flora Feng
- **时间**: 2026-05-20T14:21:00Z
- **提交信息**: [Bugfix] Use shared coerce_to_schema_type in DeepSeekV32 tool parser (#43019)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [644b2a2](https://github.com/vllm-project/vllm/commit/644b2a28e7eb3b11191f157416cfedebd2da995b)

- **作者**: Joel Smith
- **时间**: 2026-05-20T14:10:01Z
- **提交信息**: [Bugfix] Use enable_sm120_family for per-tensor FP8 CUTLASS kernels on SM12.1 (#41215)

Signed-off-by: j9smith <j.smith9103@outlook.com>
Signed-off-by: Joel Smith <j.smith9103@outlook.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [ded8712](https://github.com/vllm-project/vllm/commit/ded871201a424dd0d28a00aaf74c5786457a18ee)

- **作者**: rishitdholakia13
- **时间**: 2026-05-20T14:08:58Z
- **提交信息**: [Bug][Structured Outputs] Fix bug that leads to unconstrained generations with structural tags (#42452)

Signed-off-by: rishitdholakia13 <rishit+github@cohere.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [df84fb0](https://github.com/vllm-project/vllm/commit/df84fb07a6e57969941841c6363d1efbac1ba1e8)

- **作者**: Dipika Sikka
- **时间**: 2026-05-20T14:01:45Z
- **提交信息**: Remove additional dead code as a follow-up to #42889 (#43144)

Signed-off-by: Dipika Sikka <dipikasikka1@gmail.com>

### [0a50874](https://github.com/vllm-project/vllm/commit/0a508743d42a26786c1432bb7f2e93f8111b6383)

- **作者**: Benjamin Chislett
- **时间**: 2026-05-20T13:15:52Z
- **提交信息**: [Spec Decode] Support non-MTP speculation for NemotronH (#43130)

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>

### [19cf334](https://github.com/vllm-project/vllm/commit/19cf334207ed81d3ed75a473acd1a95c785d9ed3)

- **作者**: Kebe
- **时间**: 2026-05-20T12:58:30Z
- **提交信息**: [Feature] Support manually enabling the cumem allocator (#33648)

Signed-off-by: Kebe <mail@kebe7jun.com>

### [87e3145](https://github.com/vllm-project/vllm/commit/87e31455b056c6ce59bf5dcb3c622155431851db)

- **作者**: Ray Wang
- **时间**: 2026-05-20T09:32:03Z
- **提交信息**: [Doc] Sync CLI guide with actual help modes and launch subcommand (#40326)

Signed-off-by: Rui Wang <raygorous@gmail.com>
Co-authored-by: Rui Wang <raygorous@gmail.com>

### [cb600d1](https://github.com/vllm-project/vllm/commit/cb600d1cdbb079ab9432348f128e71c4e2e0a373)

- **作者**: hallerite
- **时间**: 2026-05-20T08:58:46Z
- **提交信息**: [Frontend] Forward X-data-parallel-rank header on /inference/v1/generate (#42330)

Signed-off-by: hallerite <git@hallerite.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [6f21558](https://github.com/vllm-project/vllm/commit/6f21558da1ec7362d2b4f3d012bce2b612a74459)

- **作者**: xiangdong
- **时间**: 2026-05-20T08:54:58Z
- **提交信息**: [XPU][CI] Add 2 server model test files in Intel GPU CI (#42499)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [1cb2244](https://github.com/vllm-project/vllm/commit/1cb224430bea0d037b57e24cf91001f47b69ddf3)

- **作者**: Artem Perevedentsev
- **时间**: 2026-05-20T08:46:55Z
- **提交信息**: [GDN] Enable FI Blackwell GDN prefill kernel (#40717)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [9b343dd](https://github.com/vllm-project/vllm/commit/9b343dd4f54a9870f3ba1e41f5a5b3f4a1e25340)

- **作者**: Harry Mellor
- **时间**: 2026-05-20T08:10:00Z
- **提交信息**: Enable mermaid diagrams in the docs (#43192)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [07aeaf9](https://github.com/vllm-project/vllm/commit/07aeaf9d4df870a76d5a0dc19d6a7e74b4be5d3b)

- **作者**: Chris Leonard
- **时间**: 2026-05-20T07:18:12Z
- **提交信息**: [6/n] Migrate activation kernels, gptq, gguf, non cutlass w8a8 to libtorch stable ABI (continued) (#42663)

Signed-off-by: Mikayla Gawarecki <mikaylagawarecki@gmail.com>
Signed-off-by: Chris Leonard <chleonar@redhat.com>
Co-authored-by: Mikayla Gawarecki <mikaylagawarecki@gmail.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [40651c0](https://github.com/vllm-project/vllm/commit/40651c020772b80f9ca80272aebe749fe01cd38a)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-05-20T07:02:36Z
- **提交信息**: [Docs][PD][NIXL] Bidirectional kv-cache transfer (#43097)

Signed-off-by: NickLucche <nlucches@redhat.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-21
**监控日期**: 2026-05-20
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4833
- **最后更新**: 2026-05-20T22:36:29Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: wangyu, Samit, WeiQing Chen

## AI分析总结

好的，作为专业的代码分析助手，以下是对仓库 `vllm-project/vllm-omni` 昨日提交记录的分析总结：

### 1. 主要更新类型

- **功能新增**: 1项 (Diffusion模型支持LoRA)
- **Bug修复**: 1项 (分布式多模态缓存路由)
- **性能优化**: 1项 (HY-Image模型的采样器优化)
- **文档更新**: 2项 (量化指南、CosyVoice3 TTS文档)
- **测试/CI**: 1项 (本地夜间测试脚本)
- **重构/清理**: 1项 (TTS YAML清理，移除旧模型)

### 2. 关键变更点及其与项目整体方向的关系

- **支持Diffusion模型的LoRA微调** (`083b5e3`): 这是对生成式AI模型（如图像生成）能力的重要扩展。结合项目“omni-modality”（全模态）的定位，这表明项目正积极将文生图/图生图等扩散模型纳入服务范围，并支持高效的LoRA适配，增强了模型的灵活性和定制化能力。
- **修复分布式多模态缓存路由** (`5cf4605`): 这是一个关键的底层Bug修复。多模态模型通常需要处理不同模态（文本、图像、音频）的数据，分布式缓存路由的正确性直接影响模型在多节点环境下的推理效率和正确性。修复此问题对保障大规模、多模态服务的稳定性和性能至关重要。
- **优化HY-Image模型的采样器同步** (`2aafe0b`): 针对特定图像模型（HY-Image）的采样过程进行性能优化，通过减少设备到主机（D2H）的同步开销来提升吞吐量。这体现了项目对特定模态模型进行精细化性能调优的承诺，直接提升了图像生成服务的效率。
- **完善量化文档** (`f74cba8`): 量化是降低模型部署成本和提升推理速度的关键技术。完善相关文档降低了用户使用量化功能的学习门槛，有助于推动项目在实际生产环境中的落地。
- **增加CosyVoice3 TTS文档并清理代码** (`fc8486c`): 为新的语音合成模型（CosyVoice3）提供在线文档，同时清理旧的TTS模型（VoxCPM v1）。这表明项目在语音模态上持续迭代，淘汰旧模型，引入并文档化新模型，保持技术栈的先进性和清晰度。
- **增加本地夜间测试脚本** (`e1c6bc7`): 通过提供与CI环境一致的本地测试脚本，提升了开发者的测试效率和代码质量保障。这对于一个快速发展的开源项目来说，是维护代码稳定性的重要基础设施。

### 3. 对项目的影响和潜在意义

- **扩展模型生态**: 支持Diffusion模型的LoRA，直接拓宽了vllm-omni的服务范围，使其不再局限于纯文本或简单多模态，而是向更复杂的生成式AI领域迈进，增强了项目的竞争力。
- **提升生产环境可靠性**: 修复分布式缓存路由Bug，解决了多节点部署下的一个潜在严重问题，这对于需要高可用性和一致性的生产环境至关重要。
- **加速特定模型推理**: 对HY-Image的性能优化，直接提升了该模型的服务效率，降低了延迟和成本，对图像生成场景的用户体验有显著改善。
- **降低用户使用门槛**: 完善量化、TTS等文档，使得新用户和开发者能更快地上手和使用这些高级功能，有助于扩大用户社区。
- **维护代码健康度**: 清理旧模型代码和增加测试脚本，是项目长期健康发展的必要投入，减少了技术债务，提高了代码的可维护性。

### 4. 值得关注的技术点

- **Diffusion模型的LoRA支持**: 这是将LoRA这种高效的微调技术应用于扩散模型，而非传统的LLM。其实现方式（`step-wise execution`）值得关注，可能涉及如何将LoRA权重注入到扩散模型的去噪步骤中。
- **分布式多模态缓存路由**: 这是一个复杂的技术问题。修复方案可能涉及如何根据请求的模态组合（如文本+图像）来正确路由和查找缓存，确保数据一致性。
- **采样器D2H同步优化**: 这是一个典型的GPU推理性能优化点。通过减少不必要的CPU-GPU同步，可以显著提高GPU利用率。其具体实现（例如使用异步拷贝或调整同步点）值得学习。

### 5. 基于项目背景，这些提交如何影响项目发展

- **强化“全模态”定位**: 项目README强调“Easy, fast, and cheap omni-modality model serving”。昨日的更新从**广度**（新增Diffusion模型）和**深度**（优化HY-Image性能、完善TTS文档）两个维度强化了这一核心定位。
- **走向成熟与稳定**: 修复分布式Bug、增加本地测试脚本、清理旧代码，这些是项目从早期快速迭代阶段走向成熟稳定阶段的重要标志。它们共同提升了项目的健壮性和可维护性，为吸引更多企业级用户奠定了基础。
- **降低部署与使用成本**: 性能优化（HY-Image）和文档完善（量化）直接或间接地降低了用户的使用和部署成本，这与项目“cheap”的承诺相符。
- **构建活跃的开发者生态**: 通过提供更好的测试工具和更清晰的文档，项目正在积极降低贡献门槛，吸引更多开发者参与到多模态模型服务的构建中来。

## 详细提交记录

### [083b5e3](https://github.com/vllm-project/vllm-omni/commit/083b5e363fbd32203e30cfaa3de2199370badec3)

- **作者**: Samit
- **时间**: 2026-05-20T14:26:18Z
- **提交信息**: [Diffusion] Support LoRA in step-wise execution (#3639)

Signed-off-by: samithuang <285365963@qq.com>

### [f74cba8](https://github.com/vllm-project/vllm-omni/commit/f74cba84ac31657751130d7f1c6f2d4d07e7d241)

- **作者**: WeiQing Chen
- **时间**: 2026-05-20T07:52:40Z
- **提交信息**: [Docs] Complete quantization nav and online guide (#3764)

Signed-off-by: David Chen <530634352@qq.com>

### [2aafe0b](https://github.com/vllm-project/vllm-omni/commit/2aafe0bf94989e1946c7e901c4a71391e7492ed2)

- **作者**: Canlin Guo
- **时间**: 2026-05-20T07:40:34Z
- **提交信息**: [Perf] Optimize sampler D2H sync for HY-Image (#3617)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [5cf4605](https://github.com/vllm-project/vllm-omni/commit/5cf4605bf918ffa2f0f9b3b83042557d9ad46c05)

- **作者**: bjf-frz
- **时间**: 2026-05-20T07:31:41Z
- **提交信息**: [Bugfix]Fix distributed stage0 multimodal cache routing (#3740)

Signed-off-by: bjf-frz <240110042+bjf-frz@users.noreply.github.com>
Co-authored-by: bjf-frz <240110042+bjf-frz@users.noreply.github.com>

### [e1c6bc7](https://github.com/vllm-project/vllm-omni/commit/e1c6bc7597eeffbc84df1d9162a55c860e168833)

- **作者**: wangyu
- **时间**: 2026-05-20T07:26:59Z
- **提交信息**: [Test] add run_nightly_jobs.sh for local nightly pytest parity (#3670)

Signed-off-by: wangyu <410167048@qq.com>

### [fc8486c](https://github.com/vllm-project/vllm-omni/commit/fc8486cf20d9014bb189ffceb042c109f7e6d340)

- **作者**: Yueqian Lin
- **时间**: 2026-05-20T07:24:06Z
- **提交信息**: [Doc][TTS] CosyVoice3 online docs + residual TTS yaml cleanup + remove VoxCPM v1 (#3748)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

---
