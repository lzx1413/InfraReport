# GitHub Stars 合并报告 - 2026-05-18

**合并日期**: 2026-05-19
**监控日期**: 2026-05-18
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


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1928
- **最后更新**: 2026-05-18T21:24:55Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Coach257, Ting

## AI分析总结

好的，这是对ByteDance-Seed/VeOmni仓库昨日提交记录的分析总结：

### 1. 主要更新类型

*   **功能新增 (feat):** 更新了 `qwen2.5omni` 和 `llama` 模型到v5版本。
*   **测试/质量保障 (test/ci):** 为 `qwen3_5` 模型生成的代码添加了隐式CUDA同步门控。

### 2. 关键变更点及其与项目整体方向的关系

*   **模型版本升级 (`066e2bf`)**:
    *   **变更点**: 将 `qwen2.5omni` 和 `llama` 模型更新至v5版本。
    *   **与项目方向的关系**: 该项目旨在“Scaling Any Modality Model Training”（扩展任意模态模型训练）。更新主流多模态模型（如Qwen2.5-Omni）和基础语言模型（Llama）的版本，是保持项目对最新、最先进模型支持的核心工作，直接服务于“Any Modality Model”的愿景。这确保了VeOmni的“配方动物园”（Recipe Zoo）能覆盖社区最关注的新模型。

*   **CUDA同步门控测试 (`bf5de0d`)**:
    *   **变更点**: 为 `qwen3_5` 模型生成的代码添加了隐式CUDA同步的检测或强制机制。
    *   **与项目方向的关系**: 分布式训练中，隐式的CUDA同步（如`cudaDeviceSynchronize`）是性能杀手，会严重拖慢训练速度。此提交通过添加测试门控，主动发现并防止此类问题，直接服务于项目“Scaling...Model Training”（扩展模型训练）的目标，确保大规模训练时的性能优化和稳定性。这体现了项目对训练效率的极致追求。

### 3. 对项目的影响和潜在意义

*   **提升模型支持度**: 升级Qwen2.5-Omni和Llama到v5，将使VeOmni的用户能够利用这些模型的最新架构、训练技巧和性能改进，从而在更多任务上取得更好效果。
*   **增强训练可靠性**: 添加CUDA同步门控测试，能有效预防因代码质量问题导致的性能下降或训练失败，尤其是在大规模分布式训练场景下。这提升了VeOmni作为训练框架的健壮性和用户信心。
*   **维护代码质量**: 在CI流程中加入此类测试，体现了项目对代码质量和长期可维护性的重视，这对于一个开源框架的健康发展至关重要。

### 4. 值得关注的技术点

*   **隐式CUDA同步**: 这是分布式深度学习训练中一个关键但容易被忽视的性能陷阱。VeOmni团队主动通过CI测试来防范，说明他们对底层GPU编程和训练性能优化有深入理解。
*   **模型版本管理**: 项目使用明确的版本号（如v5）来管理模型支持，这是一种清晰、可追溯的演进方式，方便用户了解项目支持了哪些模型的具体版本。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **巩固核心价值**: 根据README，VeOmni的核心是提供一个“以模型为中心的分布式配方动物园”。昨天的两个提交分别从“更新配方”（升级模型版本）和“优化配方烹饪过程”（提升训练性能与可靠性）两个维度，直接巩固了这一核心价值。
*   **吸引更广泛用户**: 支持最新的Qwen2.5-Omni和Llama v5，将吸引更多使用这些流行模型的研究者和工程师采用VeOmni。同时，对训练性能的极致优化，也符合工业界和学术界对大规模训练效率的迫切需求。
*   **建立技术壁垒**: 通过主动检测和预防隐式CUDA同步这类底层性能问题，VeOmni在训练框架的工程深度上建立了自己的技术优势，而不仅仅是提供模型代码的集合。这有助于项目在众多训练框架中脱颖而出。

## 详细提交记录

### [bf5de0d](https://github.com/ByteDance-Seed/VeOmni/commit/bf5de0d427fe0a42aee595950ddd5069b7347fbe)

- **作者**: Ting
- **时间**: 2026-05-18T21:24:50Z
- **提交信息**: [model, ci] test: add implicit CUDA sync gate for qwen3_5 generated modeling (#760)

### [066e2bf](https://github.com/ByteDance-Seed/VeOmni/commit/066e2bf4d38b406cf578f3822dd911fe3ec0cf55)

- **作者**: Coach257
- **时间**: 2026-05-18T08:56:17Z
- **提交信息**: [model] feat: update  qwen2.5omni & llama to v5 (#767)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2271
- **最后更新**: 2026-05-18T22:39:11Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: helloyongyang

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **功能更新/配置调整**：本次提交属于对推理配置的更新，而非全新的功能或Bug修复。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：更新了推理配置文件 (`infer config`)。
- **与项目方向的关系**：LightX2V 是一个**轻量级视频生成推理框架**。推理配置是决定模型如何加载、运行以及输出质量的核心参数。更新配置直接服务于项目的核心目标——**提供高效、可用的视频生成推理能力**。这可能是为了适配新的模型、优化推理速度或改善生成效果。

### 3. 对项目的影响和潜在意义
- **直接影响**：用户或开发者在使用该框架进行视频生成推理时，将应用新的配置，可能带来性能或效果上的变化。
- **潜在意义**：
    - **模型适配**：可能意味着框架开始支持新的视频生成模型，或对现有模型（如CogVideoX）的推理参数进行了优化。
    - **易用性提升**：更新后的配置可能提供了更合理的默认值，降低了用户的使用门槛。
    - **性能调优**：可能调整了如`num_inference_steps`、`guidance_scale`等关键参数，以在生成质量和速度之间取得更好的平衡。

### 4. 值得关注的技术点
- **配置文件的变更内容**：虽然提交信息未详细说明，但值得关注具体修改了哪些参数（例如：采样步数、分类器自由引导尺度、是否启用内存优化等）。这能直接反映框架的优化方向。
- **与训练流程的关联**：提交信息中标注了`[Train]`，暗示该推理配置的更新可能与训练流程有关（例如，训练后更新了推理时的默认配置）。

### 5. 基于项目背景，这些提交如何影响项目发展
- **推动项目成熟度**：作为一个“轻量级”框架，持续优化推理配置是提升其**实用性**和**竞争力**的关键步骤。这有助于吸引更多用户，并推动项目从实验性阶段向更稳定、更易用的生产级工具发展。
- **强化核心能力**：通过不断调整推理配置，项目团队正在精细打磨其核心的“视频生成推理”能力，这是项目长期发展的基石。这比添加外围功能更能体现项目的价值。
- **保持与前沿模型同步**：更新配置可能意味着框架正在积极适配社区中最新、最流行的视频生成模型，确保项目不会落后于技术发展潮流。

## 详细提交记录

### [bba32c2](https://github.com/ModelTC/LightX2V/commit/bba32c2fcd960e933037d208ebd16237eaf283b3)

- **作者**: helloyongyang
- **时间**: 2026-05-18T07:12:46Z
- **提交信息**: [Train]: update infer config

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2081
- **最后更新**: 2026-05-19T00:07:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5634
- **最后更新**: 2026-05-18T23:47:33Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Anerudhan Gopal, leonardHONG, Lee Nau

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增**: 为 MoE (Mixture-of-Experts) 模块添加了高性能的 `moe_output_memset_inplace` 操作。
- **Bug修复**: 修复了在 SM121 架构上调用 `mm_fp4` 时因架构检查过于严格而导致的 `ValueError`。
- **测试增强**: 扩展了 `bmm_mxfp8` 的测试覆盖范围，使其能在 SM12x 架构上测试 cutlass 后端。
- **架构/基础设施**: 引入了新的 EP (Expert Parallelism) API 设计，并更新了构建依赖。

### 2. 关键变更点及其与项目整体方向的关系

- **`feat(cute_dsl/moe): add moe_output_memset_inplace`**: 这是对 MoE 核心路径的性能优化。通过使用 `cudaMemsetAsync` 替代 PyTorch 的 `zero_()` 操作，减少了内核启动开销（约2-3微秒），并确保了正确的流同步，这对于 CUDA Graph 捕获至关重要。这与 FlashInfer 为 LLM 推理提供高性能 GPU 内核的目标高度一致。
- **`Fix/3170 dense blockscaled sm12x`**: 修复了 SM121 架构上的兼容性问题。这表明项目正在积极扩展对最新 GPU 架构（如 Blackwell 系列）的支持，确保用户能在新硬件上无缝使用 FlashInfer 的核心功能（如 FP4 矩阵乘法）。
- **`test: enable bmm_mxfp8 cutlass backend coverage on SM12x`**: 这是一个重要的测试基础设施改进。它确保了 FlashInfer 的 `bmm_mxfp8` 操作在 SM12x 架构上能正确使用其 cutlass 后端，填补了测试空白，提高了代码的健壮性和对新硬件的信心。
- **`Ep api design - Build Infra dependencies`**: 这标志着项目在架构层面为专家并行（EP）做准备。EP 是 MoE 模型分布式推理的关键技术，引入其 API 设计表明 FlashInfer 正在向更高级的分布式推理场景演进。

### 3. 对项目的影响和潜在意义

- **性能提升**: `moe_output_memset_inplace` 的引入直接优化了 MoE 推理中的一个热点路径，对于需要频繁执行 MoE 前向传播的 LLM 服务，可以累积带来显著的延迟改善。
- **硬件兼容性增强**: 修复 SM121 问题和增加 SM12x 测试覆盖，确保了 FlashInfer 在最新的 NVIDIA Blackwell GPU 上能提供稳定、高性能的服务，这对于吸引和留住使用最新硬件的用户至关重要。
- **架构演进**: EP API 的设计是项目向更复杂、更完整的推理解决方案迈出的重要一步。这表明 FlashInfer 不仅仅关注单 GPU 上的算子优化，也开始关注多 GPU 环境下的模型并行策略。

### 4. 值得关注的技术点

- **`cudaMemsetAsync` vs `tensor.zero_()`**: 这是一个典型的性能优化案例。`cudaMemsetAsync` 是一个更底层的 CUDA API，其调用开销远低于 PyTorch 的 `zero_()`，后者会启动一个完整的 CUDA kernel。在延迟敏感的 MoE 路径中，这种微优化很有价值。
- **显式流管理**: `moe_output_memset_inplace` 通过参数显式传递 CUDA stream，避免了因内部使用不同流获取方式而导致的潜在同步问题。这对于 CUDA Graph 的正确捕获和执行至关重要，体现了对高级 CUDA 特性的深入理解。
- **SM12x 架构兼容性**: 提交记录中多次提到 SM120 和 SM121 共享相同的计算规范（MMA atoms, SMEM），因此可以复用相同的 kernel。这反映了对 GPU 微架构的深刻理解，是进行高效跨架构兼容性修复的基础。

### 5. 基于项目背景的分析

- **强化核心优势**: FlashInfer 的核心定位是为 LLM 推理提供高性能 GPU 内核。昨日的更新（特别是 MoE 优化和 FP4 修复）直接强化了这一核心优势，使其在 MoE 模型推理和低精度计算（FP4）场景下更具竞争力。
- **拓展应用边界**: EP API 的设计表明 FlashInfer 正在从单 GPU 算子库向支持分布式推理的框架演进。这使其能更好地服务于大规模 MoE 模型的部署需求，与当前 LLM 领域向更大、更稀疏模型发展的趋势相吻合。
- **紧跟硬件发展**: 对 SM12x 架构的积极适配和测试，体现了项目对最新硬件生态的重视。这确保了 FlashInfer 能持续为使用最新 NVIDIA GPU 的用户提供最佳性能，保持其技术领先地位。
- **提升工程质量和可靠性**: 测试覆盖的增强（如 `bmm_mxfp8` 测试）和代码质量的改进（如修复架构检查），表明项目在快速迭代功能的同时，也在持续提升其稳定性和可靠性，这对于一个被广泛依赖的基础库至关重要。

## 详细提交记录

### [9c3eb00](https://github.com/flashinfer-ai/flashinfer/commit/9c3eb0046d5d993a5f2f2749a386bdf177bce94e)

- **作者**: Anerudhan Gopal
- **时间**: 2026-05-18T23:47:28Z
- **提交信息**: Ep api design - Build Infra dependencies (#3315)

### [7b83d0c](https://github.com/flashinfer-ai/flashinfer/commit/7b83d0c54941afefa5ab1a0e0ac418aa55ee4f41)

- **作者**: leonardHONG
- **时间**: 2026-05-18T21:21:55Z
- **提交信息**: test: enable bmm_mxfp8 cutlass backend coverage on SM12x (#3183)

## 📌 Description

`test_bmm_mxfp8.py` only parametrizes `backend=["cudnn"]` and skips
`cap[0] in [11, 12]` outright, so the cutlass backend (which is the one
actually supported on SM12x — see `gemm_base.py:7570`) was never
exercised. The cudnn backend is supported on `[100, 103]` only, so
simply removing the skip would have failed on SM12x.

This adds `cutlass` to the backend parametrize and replaces the
unconditional skip with per-backend CC gating that mirrors the
`@supported_compute_capability` decorators:

  - `cudnn` backend: `cap[0] != 10` → skip
  - `cutlass` backend: `cap[0] != 12` → skip

  After the change:
  - SM10x: runs cudnn (unchanged), skips cutlass
  - SM12x: skips cudnn, runs cutlass (newly covered)
  - SM110: skipped on both (separate gap, not addressed here)

  Verified on RTX Pro 6000 (sm_120, CUDA 12.9):
  - cutlass backend: **288 passed, 0 failed**
  - cudnn backend: 288 skipped (as expected on sm_120)

  ## 🔍 Related Issues

  Refs #3170 (Action Item 7 / T3).

  ## 🚀 Pull Request Checklist

  ### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
  - [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

  ## 🧪 Tests

  - [ ] Tests have been added or updated as needed.
  - [x] All tests are passing (`unittest`, etc.).

  ## Reviewer Notes



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Expanded test coverage to include an additional GPU computation
backend, validating batch matrix multiplication across backends.
* Strengthened GPU compatibility checks with backend-specific
requirements and added conditions for a particular memory layout,
ensuring tests run only on supported hardware/configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Ka-Hyun Nam <knam@nvidia.com>

### [9a463df](https://github.com/flashinfer-ai/flashinfer/commit/9a463df0d2643a43fc70c0da01e63fa3238aa320)

- **作者**: leonardHONG
- **时间**: 2026-05-18T21:21:04Z
- **提交信息**: Fix/3170 dense blockscaled sm12x (#3180)

## 📌 Description

  After #3113 extended the b12x decorator to SM121, calling `mm_fp4(...,
  backend="b12x")` on sm_121 still trips the dispatch-side check in
  `dense_blockscaled_gemm_sm120_b12x.py:1591`:

  ```
  ValueError: dense_gemm launch only supports sm_120, got sm_121
  ```

SM120 and SM121 share the same 12.x spec (MMA atoms, SMEM), so the same
kernel applies. Allow sm_121 through the check. The error message is
updated to match.

  Other call sites in this file (`sm_version="sm_120"` at line 1875,
`get_smem_capacity_in_bytes("sm_120")` at lines 122/1461) are left alone
— they work for both arches.

  ## 🔍 Related Issues

  Refs #3170 (Action Item 4). Follows up on #3113.

  ## 🚀 Pull Request Checklist

  ### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
  - [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

  ## 🧪 Tests

  - [ ] Tests have been added or updated as needed.
  - [ ] All tests are passing (`unittest`, etc.).

No new tests; no SM121 hardware locally. Existing sm_120 path unchanged.

  ## Reviewer Notes

Same audit cleanup batch as #3173 / #3174 / #3175.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Improvements**
* Expanded GPU architecture support to include additional SM12x devices
(sm_120 and sm_121).

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [34fe1ff](https://github.com/flashinfer-ai/flashinfer/commit/34fe1ff09b3e157c63df7476cbed344045f94b7c)

- **作者**: Lee Nau
- **时间**: 2026-05-18T21:17:38Z
- **提交信息**: feat(cute_dsl/moe): add `moe_output_memset_inplace` dense memset wrapper (#3328)

## 📌 Description

Adds `moe_output_memset_inplace`, a thin C++ binding around
`cudaMemsetAsync` for zeroing the active MoE output slice before GEMM2
finalize, and uses it to replace the two `moe_output.zero_()` call sites
in `_moe_core_impl`. Mirrors TRT-LLM's `moe_output_memset_inplace` Path
A (`cuteDslMoeUtilsOp.cpp` at the `!enable_alltoall || ep_size <= top_k`
branch). Functionally equivalent to `tensor.zero_()` but with lower
per-call launch overhead (one `cudaMemsetAsync` vs PyTorch's
`FillFunctor<c10::BFloat16>` kernel) — saves ~2-3 µs per call at the
cells where memset cost is visible.

**Stream selection**: the C++ binding takes an explicit
`cuda_stream_ptr` parameter (PyTorch's current stream); the Python
wrapper passes `_get_cuda_stream_ptr()`. This is required because the
underlying `get_current_stream()` C++ helper resolves through
`TVMFFIEnvGetStream`, not `at::cuda::getCurrentCUDAStream()` — so the
Python `torch.cuda.stream(...)` context manager would otherwise not
propagate to the `cudaMemsetAsync` call and aux-stream memset overlap
with surrounding GEMM work would be silently nullified. Same pattern as
`moe_sort` / `flashinfer_moe_sort` in this same file.

**Scope**: this entry point exposes only Path A. Current callers of the
monolithic CuteDSL MoE API handle all-to-all outside this function, so
TRT-LLM's internal-alltoall Path B (the sparse `moeOutputMemset` kernel)
is not part of this API. The existing sparse `moe_output_memset`
bindings remain available if a future internal-alltoall integration
needs them.

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

* `TestMoeOutputMemsetInplace` (GPU): parametrized correctness across
bf16/fp16 × 2 shapes, unsupported-dtype guard, and CUDA-graph
capture/replay verification (which would fail if the wrapper routed to
any stream other than the capture stream).
* `TestMoeOutputMemsetInplaceContract` (CPU/mock-only): deterministic
contract test that monkeypatches the FFI dispatch + stream-ptr getter
and asserts the wrapper passes `_get_cuda_stream_ptr()` as the 4th FFI
argument.

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an optimized, dense-only asynchronous buffer-clear operation for
mixture-of-experts outputs with CUDA-graph-compatible stream handling.

* **Tests**
* Added tests verifying zeroing behavior across supported dtypes/shapes,
erroring for unsupported dtypes, and correct behavior under CUDA graph
capture.

* **Documentation**
* Clarified generated module docstring to better describe existing
sparse zeroing behavior and retention for future integrations.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3328)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3488
- **最后更新**: 2026-05-18T20:22:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33655
- **最后更新**: 2026-05-18T17:50:30Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: jiqing-feng, Sayak Paul, Dev-X25874

## AI分析总结

好的，这是对 `huggingface/diffusers` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **功能新增**：为 TorchAO 量化器实现了 `_dequantize` 方法。
*   **Bug 修复**：
    *   修复了 DreamBooth 示例中，在使用先验保持损失（Prior Preservation Loss）时，Flux 和 SD3 模型的 LoRA 训练中权重张量（`weighting`）缺失的问题。
    *   修复了量化测试中，由于 `float16` 精度导致梯度下溢（underflow）的问题。
    *   修复了 Hub 测试中 LFS 指针被拒绝的问题。

### 2. 关键变更点及其与项目整体方向的关系

*   **TorchAO 量化器 `_dequantize` 功能**：
    *   **变更点**：为 `TorchAoHfQuantizer` 添加了 `_dequantize()` 方法，能将量化后的 `TorchAOBaseTensor` 权重还原为标准的 `nn.Parameter`。同时修复了 `_verify_if_layer_quantized` 方法，使其能正确识别已反量化的层。
    *   **与项目方向的关系**：`diffusers` 致力于提供高性能的模型推理和训练方案。量化是减少模型大小和加速推理的关键技术。此提交完善了量化功能的生命周期管理，允许用户在量化后灵活地恢复模型权重，这对于模型微调、部署和实验的灵活性至关重要。

*   **DreamBooth 训练脚本修复**：
    *   **变更点**：在 `examples/dreambooth` 的 Flux 和 SD3 LoRA 训练脚本中，当使用先验保持损失时，确保 `weighting` 张量与 `model_pred` 和 `target` 张量一起被正确地切片（chunk）。
    *   **与项目方向的关系**：DreamBooth 是 `diffusers` 支持的核心个性化微调方法之一。此修复确保了该高级功能（先验保持）在最新的 Flux 和 SD3 模型上能正确工作，维护了项目作为最先进模型训练工具集的可靠性。

*   **量化测试梯度下溢修复**：
    *   **变更点**：将 `_test_quantization_training` 测试中的 `autocast` 数据类型从 `float16` 改为 `bfloat16`。
    *   **与项目方向的关系**：量化模型的训练是一个复杂且易出错的过程。此修复通过使用动态范围更广的 `bfloat16`，解决了 `float16` 在量化张量操作中导致梯度消失的问题，确保了量化训练测试的稳定性和有效性，从而保障了量化功能的可靠性。

*   **Hub 测试 LFS 指针问题修复**：
    *   **变更点**：修复了与 Hub 集成的测试中，由于 LFS (Large File Storage) 指针问题导致的测试失败。
    *   **与项目方向的关系**：`diffusers` 与 Hugging Face Hub 深度集成，用于模型和数据的存储与分发。修复此类基础设施问题，保证了 CI/CD 流程的稳定性，是项目健康发展的基础。

### 3. 对项目的影响和潜在意义

*   **提升量化功能的可用性**：`_dequantize` 的实现使得量化不再是“单向”操作，用户可以更灵活地在量化模型上进行微调或进行其他需要标准权重的操作，降低了量化技术的使用门槛。
*   **增强核心训练脚本的健壮性**：DreamBooth 脚本的修复直接解决了用户在使用 Flux 和 SD3 进行个性化训练时可能遇到的错误，提升了用户体验和项目声誉。
*   **提高测试套件的可靠性**：修复量化测试中的梯度下溢和 Hub 测试中的 LFS 问题，使得自动化测试能更准确地反映代码质量，减少了“假阳性”失败，有助于开发者快速定位真正的问题。

### 4. 值得关注的技术点

*   **量化与反量化的对称性**：`_dequantize` 的实现表明，`diffusers` 的量化设计考虑了完整的生命周期，不仅仅是推理加速，也支持后续的模型修改。
*   **精度选择对训练的影响**：`float16` vs `bfloat16` 的选择是一个经典问题。此提交再次强调了在涉及量化张量等复杂操作时，`bfloat16` 因其更大的动态范围而成为更稳健的选择。
*   **DreamBooth 先验保持的复杂性**：该修复揭示了在实现像先验保持这样的高级损失函数时，需要仔细处理多个张量（预测、目标、权重）之间的维度对齐，尤其是在多模态模型（如 Flux）中。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **巩固技术领先地位**：`diffusers` 的目标是成为最全面、最易用的扩散模型工具库。通过及时修复 Flux 和 SD3 等最新模型的训练问题，并完善量化等高级功能，项目保持了其在快速发展的 AI 领域中的技术领先地位。
*   **提升开发者体验**：修复测试基础设施和训练脚本中的 Bug，直接提升了开发者和用户的体验。一个稳定、可靠的工具库更能吸引社区贡献和用户采用。
*   **推动量化技术落地**：`_dequantize` 功能的加入，使得量化不再是一个“黑盒”，而是可以灵活集成到更复杂的训练和部署流水线中。这有助于推动量化技术在扩散模型领域的实际应用，符合项目降低模型部署成本、提升效率的长期目标。

## 详细提交记录

### [907c0c2](https://github.com/huggingface/diffusers/commit/907c0c2c76e7a24a22e3280ac40f7f2f800a4b01)

- **作者**: jiqing-feng
- **时间**: 2026-05-18T13:09:50Z
- **提交信息**: Implement _dequantize for TorchAO quantizer (#13538)

* Implement _dequantize for TorchAO quantizer

- Add _dequantize() method in TorchAoHfQuantizer that dequantizes
  TorchAOBaseTensor weights back to standard nn.Parameter
- Fix _verify_if_layer_quantized to check isinstance(weight, TorchAOBaseTensor)
  so dequantized layers are correctly detected as non-quantized

* enable dequantize for TorchAO tester mixin

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>

* check dequantize

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>

* fix dequantize: clear is_quantized flag and cast dtype after dequantize

* fix

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>

* fix error report

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>

---------

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [387a471](https://github.com/huggingface/diffusers/commit/387a47156e58f002c87b25a3293d38886b959eb8)

- **作者**: Dev-X25874
- **时间**: 2026-05-18T10:51:13Z
- **提交信息**: examples/dreambooth: fix missing `weighting` chunk when using prior preservation in Flux and SD3 LoRA training (#13743)

* examples/dreambooth: chunk weighting tensor alongside model_pred and target when using prior preservation (flux LoRA)

* examples/dreambooth: chunk weighting tensor alongside model_pred and target when using prior preservation (SD3 LoRA)

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [2f4a717](https://github.com/huggingface/diffusers/commit/2f4a7177f085f7f603f736e621d553e01191db03)

- **作者**: jiqing-feng
- **时间**: 2026-05-18T09:50:07Z
- **提交信息**: Fix training gradient underflow in quantization tests (#13539)

* Fix training gradient underflow in quantization tests

Change autocast dtype from float16 to bfloat16 in _test_quantization_training.
Float16's limited dynamic range causes gradients to underflow to zero when
passing through quantized tensor subclass operations.

* fix autocast dtype check

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>

---------

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [0ad0a32](https://github.com/huggingface/diffusers/commit/0ad0a32c67ccfd4640f19558c00119b02576157b)

- **作者**: Sayak Paul
- **时间**: 2026-05-18T09:26:57Z
- **提交信息**: fix lfs pointer rejection problems for hub tests (#13733)

* fix lfs pointer rejection problems for hub tests

* fix more

* Delete .claude directory

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
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


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12427
- **最后更新**: 2026-05-18T22:44:16Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

好的，这是对仓库 `modelscope/DiffSynth-Studio` 昨日提交记录的分析总结。

### 昨日更新要点分析

1.  **主要更新类型**
    *   **功能新增**：本次提交引入了“Offload Training”（卸载训练）功能。

2.  **关键变更点及其与项目整体方向的关系**
    *   **关键变更点**：新增了对“Offload Training”的支持。这通常意味着在模型训练过程中，可以将部分模型参数、梯度或优化器状态从GPU显存卸载到CPU内存或硬盘上。
    *   **与项目方向的关系**：`DiffSynth-Studio` 是一个专注于视频和图像合成（Diffusion模型）的库，其核心挑战之一是处理高分辨率、长序列的视频数据，这通常需要巨大的GPU显存。该功能直接回应了用户在使用大型模型或处理高分辨率素材时遇到的显存瓶颈问题，与项目“让更多人能使用先进合成技术”的潜在目标高度一致。

3.  **对项目的影响和潜在意义**
    *   **降低硬件门槛**：这是最直接的影响。用户现在可以使用显存更小的GPU（甚至消费级显卡）来训练或微调大型模型，极大地扩展了项目的用户基础。
    *   **提升开发效率**：对于开发者而言，可以在有限的硬件资源下尝试更大的模型或更长的视频序列，加速实验和迭代过程。
    *   **增强项目竞争力**：在视频生成领域，显存优化是核心痛点之一。提供“Offload Training”功能使 `DiffSynth-Studio` 在易用性和资源效率上更具竞争力。

4.  **值得关注的技术点**
    *   **实现方式**：虽然提交信息未透露具体实现细节，但常见的“Offload Training”技术包括：
        *   **ZeRO Offload**：将优化器状态和梯度卸载到CPU。
        *   **模型层卸载**：在训练过程中，将不参与当前计算的模型层临时卸载。
        *   **异步卸载**：通过流水线方式，在GPU计算的同时进行数据卸载，以隐藏数据传输延迟。
    *   **性能权衡**：卸载训练通常会引入CPU-GPU数据传输的开销，导致训练速度下降。该功能的实现质量将体现在如何平衡显存节省与训练速度之间。

5.  **基于README的项目背景，这些提交如何影响项目发展**
    *   **推动普及化**：`DiffSynth-Studio` 的目标是成为一个强大的合成工具。通过解决显存限制这一关键障碍，该提交将项目从“需要高端硬件”的专家工具，向“更广泛用户可访问”的普及化工具迈进了一大步。这有助于吸引更多社区贡献者和用户，形成良性发展循环。
    *   **支持更大规模实验**：该功能为未来支持更大、更复杂的模型（如超高清视频生成、长视频生成）铺平了道路。开发者可以更自由地探索模型架构和训练策略，而不必被硬件资源所束缚。
    *   **强化生态定位**：在ModelScope生态中，`DiffSynth-Studio` 通过提供实用的显存优化方案，能够更好地与其他模型和工具链集成，服务于更复杂的AI应用场景。

## 详细提交记录

### [699e9e1](https://github.com/modelscope/DiffSynth-Studio/commit/699e9e1b5cc9b4ce5cdc251c3c65c47bf45507ac)

- **作者**: Zhongjie Duan
- **时间**: 2026-05-18T08:18:43Z
- **提交信息**: Offload Training (#1444)

* Support Offload Training

---------

Co-authored-by: mi804 <1576993271@qq.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 27980
- **最后更新**: 2026-05-18T23:51:38Z

## 提交统计

- **昨日提交总数**: 65
- **提交者数量**: 19
- **主要提交者**: Gaoji Liu, fzyzcjy, Mick

## AI分析总结

好的，作为专业的代码分析助手，我将结合 `sgl-project/sglang` 项目的背景，对昨日的提交记录进行分析和总结。

### 1. 主要更新类型

-   **重构 (Refactoring):** 这是昨日更新的绝对主力。提交 `#25610` 到 `#25639` 以及 `#25603` 到 `#25608` 等，对核心的 `scheduler.py` 文件进行了大规模的重构，将其拆分为多个职责单一的子模块。
-   **Bug修复 (Bug Fix):** 包括修复 `cutedsl` 包兼容性 (`#25690`)、序列并行的 `runtime_max_tokens_per_rank` 问题 (`#25685`)、PD分离预热 (`#25542`)、Gemma4注意力后端 (`#25547`)、Eagle3解码偏移 (`#25454`)、数据并行缓冲区 (`#25585`)、PD分离卡死 (`#25561`) 以及日志统计 (`#25641`) 等多个问题。
-   **功能新增 (Feature):** 新增了对 `cutlass_moe_fp4` 的 `no_combine` 支持 (`#25688`)、`DeepSeekV4` 融合 MoE 的 Triton 自动调优 (`#25569`)、`SMG` 的模型名称发现回退 (`#25293`)、`Qwen3Next` 的 `output_gate_type` (`#25401`)、以及 `SGLANG_SIMULATE_UNIFORM_EXPERTS` 基准测试工具 (`#25571`)。
-   **性能优化 (Performance):** 为 `tokenspeed_mla` 注意力后端支持草稿扩展CUDA图 (`#25489`)，并在CI中为8-GPU H200启用了权重预取 (`#25684`)。
-   **AMD 支持 (AMD Support):** 合并了针对 DeepSeek V4 的重磅支持 (`#24933`)，并修复了 MI300X 上的 OOM 问题 (`#25301`) 和 KIMI-K2.5 模型的共享专家融合 (`#25390`)。
-   **CI/文档/杂项 (CI/Docs/Misc):** 修复了CI状态管理 (`#25687`, `#25586`)，更新了macOS安装文档 (`#25178`)，并增加了对Hopper架构单批次重叠的错误提示 (`#25509`)。

### 2. 关键变更点及其与项目整体方向的关系

-   **Scheduler 大规模重构 (提交 `#25610` - `#25639`):**
    -   **变更点:** 将庞大的 `scheduler.py` 文件拆解成 `SchedulerRequestReceiver`, `SchedulerDPAttnAdapter`, `SchedulerProfilerManager`, `SchedulerWeightUpdaterManager`, `SchedulerPoolStatsObserver`, `SchedulerInvariantChecker`, `SchedulerKvEventsPublisher`, `SchedulerLoadInquirer`, `SchedulerMetricsReporter`, `SchedulerLogprobResultProcessor`, `SchedulerOutputStreamer`, `SchedulerBatchResultProcessor` 等十几个独立的类。
    -   **与项目方向的关系:** 这与项目追求高性能、高可扩展性的目标一致。一个模块化、职责清晰的调度器是支持复杂推理策略（如PD分离、序列并行、DP注意力）和未来功能扩展的基础。这显著提升了代码的可维护性和可测试性。

-   **AMD DeepSeek V4 支持 (提交 `#24933`):**
    -   **变更点:** 这是一个大型合并，旨在让 DeepSeek V4 模型在 AMD GPU 上高效运行。
    -   **与项目方向的关系:** 项目README强调支持多种硬件后端。此提交直接兑现了这一承诺，将SGLang的硬件支持从NVIDIA扩展到AMD，特别是针对当前最先进的DeepSeek模型，这对于扩大用户基础至关重要。

-   **PD分离 (Pre-fill / Decode Disaggregation) 修复与增强 (提交 `#25542`, `#25561`, `#25599`):**
    -   **变更点:** 修复了预热问题（设置`request_name`）和解码卡死问题（`prealloc pressure`），并为fake KV后端添加了`conclude_state`。
    -   **与项目方向的关系:** PD分离是SGLang实现高吞吐、低延迟推理的核心特性之一。持续的修复和增强表明该项目正在积极完善这一关键功能，使其在生产环境中更加稳定可靠。

-   **Eagle3 和 Speculative Decoding 优化 (提交 `#25566`, `#25489`, `#25454`):**
    -   **变更点:** 修复了Eagle3的aux layer ID偏移，支持`tokenspeed_mla`后端的草稿扩展CUDA图，并重构了`can_run_cuda_graph`逻辑。
    -   **与项目方向的关系:** 投机解码是提升LLM推理速度的前沿技术。SGLang对Eagle系列的支持和持续优化，体现了其作为高性能推理引擎的技术领先性。

### 3. 对项目的影响和潜在意义

-   **提升代码质量和可维护性:** Scheduler的重构是“内功”修炼，虽然不直接带来性能提升，但为未来更复杂的调度逻辑（如更精细的PD分离、多模态调度）铺平了道路，降低了引入新Bug的风险。
-   **扩大硬件生态:** 对AMD DeepSeek V4的支持是里程碑式的，直接打开了AMD GPU用户市场，特别是那些

## 详细提交记录

### [b79e4b1](https://github.com/sgl-project/sglang/commit/b79e4b1e687baa4cd36554856665b53acd9ce9b5)

- **作者**: Baizhou Zhang
- **时间**: 2026-05-18T23:51:32Z
- **提交信息**: [Fix] Try to fix error caused by latest cutedsl packages  (#25690)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [314dedf](https://github.com/sgl-project/sglang/commit/314dedf7c6ecb19561499f965d4af84d4383b154)

- **作者**: Lianmin Zheng
- **时间**: 2026-05-18T23:00:54Z
- **提交信息**: Use SGLANG_CACHE_DIR env for gpu_p2p_access_cache path (#25686)

Co-authored-by: Ian O'Connell <ianoc@meta.com>
Co-authored-by: ianoc <ianoc@fb.com>

### [745abd6](https://github.com/sgl-project/sglang/commit/745abd6cc00d51bf4536c30fa7dca80a48df0ee3)

- **作者**: Lianmin Zheng
- **时间**: 2026-05-18T22:59:55Z
- **提交信息**: Add no_combine support to cutlass_moe_fp4 (#25688)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>

### [878e6b8](https://github.com/sgl-project/sglang/commit/878e6b8886fff5e23ee89126add7cefb549b74d0)

- **作者**: Lianmin Zheng
- **时间**: 2026-05-18T22:59:33Z
- **提交信息**: [SP] Fix runtime_max_tokens_per_rank for sequence parallelism (#25685)

Co-authored-by: Ming Yang <minos.future@gmail.com>
Co-authored-by: Yinghai Lu <yinghai@meta.com>

### [6f89204](https://github.com/sgl-project/sglang/commit/6f892047ecad16e265bfc5461c5051714fc5c60b)

- **作者**: Baizhou Zhang
- **时间**: 2026-05-18T21:51:32Z
- **提交信息**: [misc] Throw error when single batch overlap is enabled on Hopper  (#25509)

### [c904fdd](https://github.com/sgl-project/sglang/commit/c904fdd20eef167d5b129769905f22938426f01c)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-18T21:42:29Z
- **提交信息**: ci: pr-states match renamed "PR Test Base" workflow_run (#25687)

### [9e3bb9a](https://github.com/sgl-project/sglang/commit/9e3bb9a3073554686ec48373032bbfd20e511377)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-18T21:24:54Z
- **提交信息**: [Spec] fold can_run_cuda_graph into EagleVerifyOutput; drop dead extend-after-decode check (#25566)

### [b7267e8](https://github.com/sgl-project/sglang/commit/b7267e8fce6f02fd9497377ed1687936ec1aa857)

- **作者**: Cheng Wan
- **时间**: 2026-05-18T21:12:45Z
- **提交信息**: [CI] Enable weight prefetch for 8-gpu-h200 basic tests (#25684)

### [1f185c6](https://github.com/sgl-project/sglang/commit/1f185c6ba83cba1b4d4f553f647fe054314f15ac)

- **作者**: Qiaolin Yu
- **时间**: 2026-05-18T18:26:16Z
- **提交信息**: Support draft extend cuda graph for tokenspeed_mla attention backend (#25489)

### [f504970](https://github.com/sgl-project/sglang/commit/f5049709b3239cd754f09f779bd85644b01ac4a2)

- **作者**: Qiaolin Yu
- **时间**: 2026-05-18T18:25:51Z
- **提交信息**: fix(eagle3): drop +1 offset on aux layer ids when first id != 1 (#25454)

### [86c6c77](https://github.com/sgl-project/sglang/commit/86c6c77f2f197f66c85813b0cc1d4463216f0fcd)

- **作者**: Shangming Cai
- **时间**: 2026-05-18T18:08:10Z
- **提交信息**: [Bugfix] Fix missing group arg in get dp buffer (#25585)

### [b29e41e](https://github.com/sgl-project/sglang/commit/b29e41e8b3f10f7f20ae5102477ed08ed5ccc35f)

- **作者**: Khoa Pham
- **时间**: 2026-05-18T17:46:25Z
- **提交信息**: Respect user override for Gemma4 attention backend (#25547)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [f21fe6a](https://github.com/sgl-project/sglang/commit/f21fe6ad4d1d6ef5cdfc6c2a5f39247dd1674df8)

- **作者**: Lianmin Zheng
- **时间**: 2026-05-18T16:49:56Z
- **提交信息**: Fix PD disaggregation warmup: set request_name and improve error logging (#25542)

### [3e2a109](https://github.com/sgl-project/sglang/commit/3e2a1096369f36e05208d508e98a0ff6f9c1cd40)

- **作者**: Gaoji Liu
- **时间**: 2026-05-18T16:18:08Z
- **提交信息**: Add output_gate_type to Qwen3NextConfig and update models to utilize it (#25401)

### [d96e593](https://github.com/sgl-project/sglang/commit/d96e593fd0176c7245935aab2411913494adc5da)

- **作者**: Byron Hsu
- **时间**: 2026-05-18T16:16:12Z
- **提交信息**: [Benchmark] Add SGLANG_SIMULATE_UNIFORM_EXPERTS for balanced expert routing with dummy weights (#25571)

Co-authored-by: Byron Hsu <byronhsu@Byrons-MacBook-Pro.local>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [866793c](https://github.com/sgl-project/sglang/commit/866793c502b76699109df739345454ecd79a0d45)

- **作者**: kk
- **时间**: 2026-05-18T16:15:07Z
- **提交信息**: Amd/deepseek v4 rebase main 0509 (#24933)

Co-authored-by: root <root@smci355-ccs-aus-m12-33.cs-aus.dcgpu>
Co-authored-by: wunhuang <wunhuang@amd.com>
Co-authored-by: Thomas Wang <1am9trash@gmail.com>
Co-authored-by: Xinyi Song <86638975+RolaoDenthu@users.noreply.github.com>
Co-authored-by: HaiShaw <hixiao@gmail.com>
Co-authored-by: amd-danli103 <danli103@amd.com>
Co-authored-by: Lin, Soga <soga.lin@amd.com>
Co-authored-by: Raiden-Makoto <Raiden-Makoto@users.noreply.github.com>
Co-authored-by: Hubert Lu <55214931+hubertlu-tw@users.noreply.github.com>
Co-authored-by: yichiche@amd.com <jacky.cheng>
Co-authored-by: yctseng0211 <yctseng@amd.com>
Co-authored-by: Bingxu Chen <bingxche@amd.com>

### [110bbdc](https://github.com/sgl-project/sglang/commit/110bbdcad7e677f67ce417fafa2f586ec2efb403)

- **作者**: Mick
- **时间**: 2026-05-18T15:05:29Z
- **提交信息**: [diffusion] fix: use dynamic LoRA for LTX2 original stage-two (#25591)

### [d1acd62](https://github.com/sgl-project/sglang/commit/d1acd62d29aa2634d6e19dcdb3d0a2823723f7b3)

- **作者**: ybyang
- **时间**: 2026-05-18T14:57:22Z
- **提交信息**: fix(disagg): unstuck decode aborts under prealloc pressure (#25561)

### [0ab427d](https://github.com/sgl-project/sglang/commit/0ab427d0e1b6ec77541d849520b59ef92e3dbe3e)

- **作者**: gruner
- **时间**: 2026-05-18T14:02:35Z
- **提交信息**: [SMG] Add /v1/models fallback for model name discovery (#25293)

Co-authored-by: Amit Gruner <agruner@crusoe.ai>

### [ba2ffcf](https://github.com/sgl-project/sglang/commit/ba2ffcf156b5b77291967ab4af4de24e8401fab7)

- **作者**: xieminghe1
- **时间**: 2026-05-18T13:35:32Z
- **提交信息**: Add DeepSeekV4 fused MoE Triton autotune support (#25569)

Co-authored-by: undefined <zhouchen.arrebol@jd.com>
Co-authored-by: xq25478 <xq25478@qq.com>
Co-authored-by: xieminghe.simon <xieminghe.simon@jd.com>

### [f04c522](https://github.com/sgl-project/sglang/commit/f04c522534e65417bbbce2a808740d3ec4f7540e)

- **作者**: Shangming Cai
- **时间**: 2026-05-18T11:56:42Z
- **提交信息**: [PD] Add conclude_state to fake KV backend (#25599)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [be64d87](https://github.com/sgl-project/sglang/commit/be64d875ad8d17ab3671724c247adaae54884807)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T11:23:48Z
- **提交信息**: Fix flush_cache AttributeError on is_stats_logging_rank (#25641)

### [79b6749](https://github.com/sgl-project/sglang/commit/79b67496699fcd31d57a951dfc432bd6e6d91718)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-18T11:23:16Z
- **提交信息**: ci: pr-states no longer overwrites running run state when label is removed (#25586)

### [8b94e1d](https://github.com/sgl-project/sglang/commit/8b94e1d0cf4a56c0ae4377d446cf64c2f06b52e6)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:50:23Z
- **提交信息**: Delete the now-unused is_work_request from scheduler.py (#25639)

### [c54b34c](https://github.com/sgl-project/sglang/commit/c54b34c007fa881265dac4ae5cbd2f2f661f0d59)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:45:38Z
- **提交信息**: Move module-level helpers out of scheduler.py (#25638)

### [99ad2b0](https://github.com/sgl-project/sglang/commit/99ad2b0894c497a47d4aa24f2344f87bee3be683)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:45:01Z
- **提交信息**: Move batch-result processing to SchedulerBatchResultProcessor and retire output_processor mixin (#25637)

### [7d0b0b6](https://github.com/sgl-project/sglang/commit/7d0b0b699175bc0964449c5582c2740b905f8081)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:44:41Z
- **提交信息**: Carve out SchedulerBatchResultProcessor for batch-result state (#25636)

### [18a7eb9](https://github.com/sgl-project/sglang/commit/18a7eb9e58aa3016c9e0a4cfa61af484eb40ac03)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:44:07Z
- **提交信息**: Move output streaming to SchedulerOutputStreamer (#25635)

### [dc88b4e](https://github.com/sgl-project/sglang/commit/dc88b4eeb4646b6216cd5459387a64ab8a727a17)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:43:48Z
- **提交信息**: Stand up SchedulerOutputStreamer; migrate output-streaming state to it (#25634)

### [2cbe01d](https://github.com/sgl-project/sglang/commit/2cbe01d0444024e096fd9fb99d84b2a48bc97265)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:43:27Z
- **提交信息**: Move logprob assembly to SchedulerLogprobResultProcessor (#25633)

### [e737f61](https://github.com/sgl-project/sglang/commit/e737f61b297e4d16ccb6196306349fe4bcbf4b35)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:42:59Z
- **提交信息**: Introduce SchedulerLogprobResultProcessor to own logprob state (#25632)

### [cf12070](https://github.com/sgl-project/sglang/commit/cf12070a0f8ceea5da4b67d6d73512ae93eb077b)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:42:34Z
- **提交信息**: Move idle-metrics logging to SchedulerMetricsReporter (#25631)

### [fd97fbb](https://github.com/sgl-project/sglang/commit/fd97fbb096bd70b925abc12e59e2fc3346e49563)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:42:08Z
- **提交信息**: Move metrics reporting to SchedulerMetricsReporter and retire metrics mixin (#25630)

### [780d969](https://github.com/sgl-project/sglang/commit/780d969699008ede2ca7bff4cfd28d7bfb4288c9)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:41:35Z
- **提交信息**: Add SchedulerMetricsReporter and route metrics state through it (#25629)

### [8357d07](https://github.com/sgl-project/sglang/commit/8357d07569b855dbb64b5bae597651285d829688)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:41:12Z
- **提交信息**: Move queue-load reporting to SchedulerLoadInquirer (#25628)

### [bde932c](https://github.com/sgl-project/sglang/commit/bde932cbbbe80c03283d999bad90bdae8606aa69)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:40:46Z
- **提交信息**: Carve out SchedulerLoadInquirer for queue-load state (#25627)

### [1213277](https://github.com/sgl-project/sglang/commit/1213277879e230e0cac412fc5182a197e12cb4ec)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:40:20Z
- **提交信息**: Move KV-cache event emission to SchedulerKvEventsPublisher (#25626)

### [0f88844](https://github.com/sgl-project/sglang/commit/0f888442c2d0922f6de8a279657698fd1ba33750)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:39:50Z
- **提交信息**: Stand up SchedulerKvEventsPublisher; migrate KV-event state to it (#25625)

### [f3dce08](https://github.com/sgl-project/sglang/commit/f3dce0828321c45f32235c34f468c455e74f7a1e)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:39:24Z
- **提交信息**: Move invariant checks to SchedulerInvariantChecker and retire runtime_checker mixin (#25624)

### [8a20046](https://github.com/sgl-project/sglang/commit/8a200464fd0ac1ff6c71e21b185ab10fe405e688)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:38:57Z
- **提交信息**: Introduce SchedulerInvariantChecker to own invariant-check state (#25623)

### [b463740](https://github.com/sgl-project/sglang/commit/b463740953171494d0a80ae0bd63a2f8a54747fa)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:38:26Z
- **提交信息**: Move create_scheduler_watchdog from runtime_checker mixin to scheduler.py (#25622)

### [ee392a1](https://github.com/sgl-project/sglang/commit/ee392a1e144f11f43b958618cdac33f55461ed37)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:37:50Z
- **提交信息**: Move pool-stats sampling to SchedulerPoolStatsObserver (#25621)

### [9fdf73f](https://github.com/sgl-project/sglang/commit/9fdf73f3931af2302e315a1470e2497e5a3e9b04)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:36:36Z
- **提交信息**: Add SchedulerPoolStatsObserver and route pool-stats state through it (#25619)

### [c58b47b](https://github.com/sgl-project/sglang/commit/c58b47bc86d08b5a07ee6bf18eb16a64e728c000)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:35:27Z
- **提交信息**: Move PoolStats dataclass to scheduler_components.pool_stats_observer (#25618)

### [95d86e5](https://github.com/sgl-project/sglang/commit/95d86e5c4395014e1b17b6070192bfa2fb91c02b)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:34:58Z
- **提交信息**: Move on_idle from runtime_checker mixin into Scheduler (#25617)

### [7851ba0](https://github.com/sgl-project/sglang/commit/7851ba09f7cbf4aabec39d08bab82e782a27060a)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:34:15Z
- **提交信息**: Move weight-update RPC handlers to SchedulerWeightUpdaterManager (#25616)

### [56f2763](https://github.com/sgl-project/sglang/commit/56f27635b8819f5f9caef0153abd1a0f5fb306c5)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:33:48Z
- **提交信息**: Carve out SchedulerWeightUpdaterManager for weight-update state (#25615)

### [a35690f](https://github.com/sgl-project/sglang/commit/a35690f07075a75b406e78901db655ecc6bee564)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:33:17Z
- **提交信息**: Move profiler controls to SchedulerProfilerManager (#25614)

### [b0a5115](https://github.com/sgl-project/sglang/commit/b0a511560cbd2f020387fad95ea97a82a21416cd)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:32:46Z
- **提交信息**: Stand up SchedulerProfilerManager; migrate profiler state to it (#25613)

### [4d6eec7](https://github.com/sgl-project/sglang/commit/4d6eec7b329baa22004ee038071f58f71eb2f603)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:32:16Z
- **提交信息**: Move DP-attention adapter methods to SchedulerDPAttnAdapter (#25612)

### [8f37a8a](https://github.com/sgl-project/sglang/commit/8f37a8a3f3eae0469868f5041478a96256764c33)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:31:45Z
- **提交信息**: Introduce SchedulerDPAttnAdapter to own DP-attention state (#25611)

### [0e9eab1](https://github.com/sgl-project/sglang/commit/0e9eab19a971ba1f4802dc463b34059c12de80ed)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:31:17Z
- **提交信息**: Move request-ingress methods to SchedulerRequestReceiver (#25610)

### [e6f3dcd](https://github.com/sgl-project/sglang/commit/e6f3dcd79062d27b381fcbdfdb79267b7d9a5bda)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:30:43Z
- **提交信息**: Add SchedulerRequestReceiver and route request-ingress state through it (#25609)

### [768d347](https://github.com/sgl-project/sglang/commit/768d3475655c1f14ee5ee3191da11ed89ce0fd62)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:29:58Z
- **提交信息**: Pre-declare mode-conditional Scheduler fields with explicit defaults (#25608)

### [3e3661f](https://github.com/sgl-project/sglang/commit/3e3661fd2fbaa373bd66d8b5092923ebcdb1cd62)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:29:30Z
- **提交信息**: Move build_kv_cache to mem_cache.kv_cache_builder (#25607)

### [fed1197](https://github.com/sgl-project/sglang/commit/fed1197474c195890ed2c08d56a1839ac177672d)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:28:58Z
- **提交信息**: Reshape init_cache_with_memory_pool to match the future build_kv_cache signature (#25606)

### [60337ab](https://github.com/sgl-project/sglang/commit/60337abe246106db2bb71d775a01dab91e1d7415)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:28:26Z
- **提交信息**: Hoist hisparse and decode-offload setup out of init_cache_with_memory_pool (#25605)

### [8692bdd](https://github.com/sgl-project/sglang/commit/8692bdd3de7836ad6a050cc01f1d99946c08eaaf)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:27:58Z
- **提交信息**: Move maybe_register_hicache_draft to mem_cache.kv_cache_builder (#25604)

### [189e0a4](https://github.com/sgl-project/sglang/commit/189e0a424068e6f2cbc13d9ff5b185a721d5b477)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:27:29Z
- **提交信息**: Decouple _maybe_register_hicache_draft from self (#25603)

### [062f6f7](https://github.com/sgl-project/sglang/commit/062f6f7ae8ea24e06b5e4d035e8abe27c4aa7360)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:27:01Z
- **提交信息**: Move get_draft_kv_pool to mem_cache.kv_cache_builder (#25602)

### [d1c04de](https://github.com/sgl-project/sglang/commit/d1c04deba742dd0f4f3b95791b26f780b3268258)

- **作者**: fzyzcjy
- **时间**: 2026-05-18T10:26:20Z
- **提交信息**: Decouple _get_draft_kv_pool from self before extraction (#25601)

### [abe2ec2](https://github.com/sgl-project/sglang/commit/abe2ec2aff6f10d3a9c719a3b505d23858d797b6)

- **作者**: sogalin_codegen
- **时间**: 2026-05-18T08:30:58Z
- **提交信息**: [AMD] Enable shared-experts fusion with new KIMI-K2.5-MXFP4 model. (#25390)

### [e558984](https://github.com/sgl-project/sglang/commit/e5589843a3c7a8360f53bb07fcecae6dab92403b)

- **作者**: Douglas Yang
- **时间**: 2026-05-18T08:20:09Z
- **提交信息**: feature: upstream cancel (#19524)

Co-authored-by: Kangyan Zhou <zky314343421@gmail.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [54eb290](https://github.com/sgl-project/sglang/commit/54eb2904a46e430e85fca8365b9142292a21c021)

- **作者**: JINO ROHIT
- **时间**: 2026-05-18T07:48:59Z
- **提交信息**: minor: docs include mac installation (#25178)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Kangyan-Zhou <zky314343421@gmail.com>

### [7adb37b](https://github.com/sgl-project/sglang/commit/7adb37bb5274dd0a78a6f3b34a11bee694cea468)

- **作者**: billishyahao
- **时间**: 2026-05-18T07:42:11Z
- **提交信息**: [AMD] fix moriep unittest oom on mi300x ci (#25301)

Co-authored-by: Bingxu Chen <bingxche@amd.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1174
- **最后更新**: 2026-05-18T16:14:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 80386
- **最后更新**: 2026-05-18T23:58:22Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 34
- **主要提交者**: Rishapveer Singh, Wei Zhao, wenjun liu

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日（基于提交时间）vllm-project/vllm 仓库更新的分析总结：

### 1. 主要更新类型

-   **Bug修复 (Bugfix):** 数量最多，涉及模型兼容性、特定后端、量化、模型运行器等多个方面。
-   **性能优化 (Perf):** 第二大类别，包括量化内核、CUDA Graph捕获、FlashInfer自动调优等。
-   **重构 (Refactor):** 清理死代码、提取公共工具函数、模块化量化方案。
-   **模型/功能新增 (Model/Feature):** 新增了Apertus工具解析器，并改进了对Cohere、DeepSeek、Qwen等模型的支持。
-   **CI/构建 (CI/Build):** 更新依赖库版本，调整CI测试策略。
-   **文档更新 (Docs):** 更新了项目归属信息。
-   **其他:** 包括对特定硬件（ROCm, CPU, XPU）的适配和优化，以及模型运行器（Model Runner）的演进。

### 2. 关键变更点及其与项目整体方向的关系

-   **性能优化是核心主题：**
    -   **`[Perf] Padded nvfp4 quant kernel...`**: 通过填充NVFP4量化内核，减少了数据拷贝，带来了2.4%~5.7%的端到端性能提升。这直接服务于项目“快速（fast）”和“廉价（cheap）”的目标，通过优化底层计算来降低推理成本。
    -   **`[Perf][MLA] Enable FULL cudagraph capture for TRITON_MLA decode`**: 为MLA（Multi-head Latent Attention）解码启用完整的CUDA Graph捕获，这是对DeepSeek等模型的关键性能优化，体现了项目对前沿模型架构的深度优化。
    -   **`[Perf] Re-enable flashinfer autotune by default...`**: 重新启用FlashInfer的自动调优，旨在为不同硬件和模型自动选择最优的注意力算法，是提升通用性能的关键。

-   **模型支持与兼容性持续扩展：**
    -   **`[BugFix] support PP for Cohere vision model`**: 修复了Cohere视觉模型的流水线并行（PP）支持，表明项目正在积极适配多模态模型。
    -   **`[Bugfix] fix swiglu limit issue for humming backend + deepseek v4`** 和 **`[Bugfix] Fix DSV4 MTP after ROCm mHC integration`**: 针对DeepSeek V4模型及其多Token预测（MTP）功能的修复，显示项目紧跟社区最热门的模型。
    -   **`[Model] Add Apertus Tool Parser`**: 新增工具解析器，扩展了模型与外部工具交互的能力，这与LLM Agent和Function Calling的发展趋势一致。

-   **架构重构与代码质量提升：**
    -   **`[Refactor] Extract shared coerce_to_schema_type utility...`**: 提取公共工具函数，减少代码重复，提高可维护性。
    -   **`[Refactor] Remove dead code`** 和 **`[Refactor] Remove dead cuda kernels`**: 清理无用代码，降低维护成本和编译时间，是项目成熟化的标志。
    -   **`Refactor AWQ Marlin MoE onto modular WNA16 oracle`**: 将AWQ Marlin MoE量化方案重构到模块化的WNA16框架上，这有助于统一量化接口，方便未来支持更多量化格式。

-   **硬件生态的持续投入：**
    -   **`[ROCm] Guard AITER GDN decode fast path by layout`** 和 **`[ROCm][Quantization][3/N] Refactor quark_moe w4a4...`**: 持续优化AMD ROCm平台的性能和量化支持，表明项目致力于多硬件平台（不仅是NVIDIA）。
    -   **`[CPU] Add MXFP4 W4A16 MoE support`**, **`[CPU Backend] Improve cpu thread utilization`**, **`[CPU] Add fused GDN support for AMX CPU platform`**: 大量针对CPU后端的优化，特别是对Intel AMX指令集和MXFP4格式的支持，旨在让LLM推理能在更广泛的硬件上运行，降低使用门槛。

### 3. 对项目的影响和潜在意义

-   **性能提升直接惠及用户：** NVFP4内核优化、FlashInfer自动调优等性能改进，将直接转化为更低的延迟和更高的吞吐量，使vLLM在LLM服务领域保持竞争力。
-   **模型兼容性增强扩大用户群：** 对DeepSeek V4、Cohere多模态、Mamba等模型的支持和修复，能吸引更多使用这些模型的开发者和企业。
-   **架构重构为未来发展铺路：** 模块化量化方案（如WNA16 oracle）和清理死代码，为未来更高效地集成新算法、新硬件提供了更干净、更灵活的代码基础。
-   **硬件多元化降低总体拥有成本：** 对CPU和AMD ROCm的持续优化，为用户提供了NVIDIA GPU之外的更多选择，特别是CPU推理对于成本敏感或资源受限的场景意义重大。

### 4. 值得关注的技术点

-   **NVFP4量化内核优化：** 这是一种4-bit浮点量化格式，其性能优化对于在保持模型精度的同时大幅降低显存和计算开销至关重要。
-   **MLA（Multi-head Lat

## 详细提交记录

### [f85c76d](https://github.com/vllm-project/vllm/commit/f85c76d701fc049a722c17b3affd9401380be1bf)

- **作者**: Artem Perevedentsev
- **时间**: 2026-05-18T23:58:15Z
- **提交信息**: [CI/Build] Bump nvidia-cutlass-dsl to 4.5.1 (#42991)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [a171e6b](https://github.com/vllm-project/vllm/commit/a171e6b52dff47dc567657e7d51f641bdcb22774)

- **作者**: shanjiaz
- **时间**: 2026-05-18T23:39:09Z
- **提交信息**: Add parallel drafting to v2 model runner unsupported features (#43010)

Signed-off-by: shanjiaz <zsjwpianpian@gmail.com>

### [37ece59](https://github.com/vllm-project/vllm/commit/37ece593c105b5bb818aa94885617b863d390d7f)

- **作者**: Wentao Ye
- **时间**: 2026-05-18T23:38:12Z
- **提交信息**: [Perf] Padded nvfp4 quant kernel to remove additional copy, 2.4%~5.7% e2e performance improvement (#42774)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [57fef4e](https://github.com/vllm-project/vllm/commit/57fef4e0bf0bfaddf117dfdc9367e1fb957b423f)

- **作者**: Flora Feng
- **时间**: 2026-05-18T21:55:39Z
- **提交信息**: [Refactor] Extract shared coerce_to_schema_type utility from Minimax M2 tool parser (#43006)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [0191354](https://github.com/vllm-project/vllm/commit/0191354827560fe38f68b4e7207f8824d6152ca3)

- **作者**: haosdent
- **时间**: 2026-05-18T21:29:10Z
- **提交信息**: [Perf][MLA] Enable FULL cudagraph capture for TRITON_MLA decode (#42885)

Signed-off-by: haosdent <haosdent@gmail.com>

### [cd49a05](https://github.com/vllm-project/vllm/commit/cd49a05d5aa3cc296912297b3c2b577efe4183c8)

- **作者**: Wentao Ye
- **时间**: 2026-05-18T20:41:22Z
- **提交信息**: [Refactor] Remove dead code (#42889)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [8474748](https://github.com/vllm-project/vllm/commit/84747489ded65265ee7d43815bfa3373b0d42279)

- **作者**: Ronen Schaffer
- **时间**: 2026-05-18T19:41:58Z
- **提交信息**: Tier offload followup (#42529)

Signed-off-by: Ronen Schaffer <ronen.schaffer@ibm.com>

### [8fc1c28](https://github.com/vllm-project/vllm/commit/8fc1c284b94668b60c30737e178cb7e6cd651e89)

- **作者**: Tuukka Sarvi
- **时间**: 2026-05-18T18:56:22Z
- **提交信息**: [ROCm] Guard AITER GDN decode fast path by layout (#42880)

Signed-off-by: Tuukka Sarvi <tuukka.sarvi@amd.com>

### [ce88f01](https://github.com/vllm-project/vllm/commit/ce88f01c9ac4fcde9dd43a983074d4e893cde65d)

- **作者**: Amit Portnoy
- **时间**: 2026-05-18T18:22:56Z
- **提交信息**: [Docs] update attribution to reflect EDEN foundation (#41666)

Signed-off-by: amitport <1131991+amitport@users.noreply.github.com>

### [00e20e7](https://github.com/vllm-project/vllm/commit/00e20e76f775b88f47469ae9fcb0f1ecd7580bb9)

- **作者**: Wentao Ye
- **时间**: 2026-05-18T18:14:21Z
- **提交信息**: [Refactor] Remove dead cuda kernels (#42767)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [9758a6e](https://github.com/vllm-project/vllm/commit/9758a6e5c5a556275c030db456d5d434ee999d58)

- **作者**: czhu-cohere
- **时间**: 2026-05-18T18:12:06Z
- **提交信息**: [BugFix] support PP for Cohere vision model (#42819)

Signed-off-by: <conway.zhu@cohere.com>
Signed-off-by: root <conway.zhu@cohere.com>

### [a2c8fc6](https://github.com/vllm-project/vllm/commit/a2c8fc66573664395f491a94da1882fdf92e034b)

- **作者**: Bowen Bao
- **时间**: 2026-05-18T17:46:13Z
- **提交信息**: [ROCm][Quantization][3/N] Refactor quark_moe w4a4 w/ oracle (#41436)

Signed-off-by: Bowen Bao <bowenbao@amd.com>

### [6859ca7](https://github.com/vllm-project/vllm/commit/6859ca76159fdd403b687c0c296e5a12850ba24e)

- **作者**: Jinzhen Lin
- **时间**: 2026-05-18T17:32:26Z
- **提交信息**: [Bugfix] fix swiglu limit issue for humming backend + deepseek v4 (#42541)

Signed-off-by: Jinzhen Lin <jinzhen.ljz@antgroup.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [67f58ce](https://github.com/vllm-project/vllm/commit/67f58ce23f469e118688a50687ef0fbb14a1c028)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-05-18T17:02:01Z
- **提交信息**: [Bugfix] Fix DSV4 MTP after ROCm mHC integration (#42930)

Signed-off-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [8c296de](https://github.com/vllm-project/vllm/commit/8c296de63b47664fc5979831e1ae2d2a14a05b1a)

- **作者**: Wei Zhao
- **时间**: 2026-05-18T16:12:27Z
- **提交信息**: [Perf] Re-enable flashinfer autotune by default and cleanup (#42857)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>

### [b12745e](https://github.com/vllm-project/vllm/commit/b12745e4f31ffacf401cc20a97c592d6a49f3269)

- **作者**: Harry Mellor
- **时间**: 2026-05-18T15:56:09Z
- **提交信息**: Fix `--convert` passed without `--runner` on causal models (#42935)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [e267369](https://github.com/vllm-project/vllm/commit/e26736973a1981dbb4054dc1ac430e78d8006ef2)

- **作者**: Wentao Ye
- **时间**: 2026-05-18T15:27:21Z
- **提交信息**: [Model Runner V2] Fix prompt logprobs calculation `Sizes of tensors must match` error (#42778)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [47829b1](https://github.com/vllm-project/vllm/commit/47829b1159335a010521ea3e5361d51744a36b0a)

- **作者**: Netanel Haber
- **时间**: 2026-05-18T15:26:00Z
- **提交信息**: [Bugfix] mamba: run single-token extends as decodes (#42430)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>

### [4a39b4f](https://github.com/vllm-project/vllm/commit/4a39b4f55374d48ebaa2ca02312e24639db8e0b8)

- **作者**: Blanc Swan
- **时间**: 2026-05-18T15:20:04Z
- **提交信息**: [Model] Add Apertus Tool Parser (#41154)

Signed-off-by: Blanc <swan.blanc@infomaniak.com>

### [78e7a7b](https://github.com/vllm-project/vllm/commit/78e7a7b9b0b9c285bf6978c3fc09eeecea3ff230)

- **作者**: Siddharth Bedekar
- **时间**: 2026-05-18T15:02:43Z
- **提交信息**: Refactor AWQ Marlin MoE onto modular WNA16 oracle (#42483)

Signed-off-by: Siddharth Bedekar <bedeksid@gmail.com>
Signed-off-by: Siddharth Bedekar <104613085+bedeks@users.noreply.github.com>
Co-authored-by: Robert Shaw <robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [f5d3dc7](https://github.com/vllm-project/vllm/commit/f5d3dc7115cf77472ba5e274f6becbbeddbf4bd5)

- **作者**: Michael Goin
- **时间**: 2026-05-18T14:26:07Z
- **提交信息**: [Model Runner v2] Support update_config (#42783)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [1ac10f1](https://github.com/vllm-project/vllm/commit/1ac10f159a09897baada01b14b6a0dd6442aefd6)

- **作者**: vllm-agent
- **时间**: 2026-05-18T13:02:51Z
- **提交信息**: Revert "[torch.compile] Add patch for fullgraph compilation" (#42686) (#42913)

Co-authored-by: Luka Govedič <luka.govedic@gmail.com>
Co-authored-by: Zhewen Li <zhewenli@inferact.ai>

### [e541765](https://github.com/vllm-project/vllm/commit/e5417657e55ec2f42809816e4aa5c9753f390cdd)

- **作者**: liranschour
- **时间**: 2026-05-18T12:59:42Z
- **提交信息**: [KV Connector][Offloading] Flush all pending jobs on last step (#42611)

Signed-off-by: Liran Schour <lirans@il.ibm.com>
Signed-off-by: liranschour <liranschour@users.noreply.github.com>
Co-authored-by: Or Ozeri <or@ozery.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2e40faf](https://github.com/vllm-project/vllm/commit/2e40faf08b2cae4ff6e27a255fe10833365de0e8)

- **作者**: xiangdong
- **时间**: 2026-05-18T12:34:48Z
- **提交信息**: [XPU][CI] Temporarily skip test_moe_lora_align_block_size_mixed_base_and_lora[1] in Intel GPU CI (#42954)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [69c91d0](https://github.com/vllm-project/vllm/commit/69c91d010a596bb74b553fe157497a1fd6edb47c)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-05-18T12:34:16Z
- **提交信息**: [MRv2] Default to MRv1 when a connector is present (#42955)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [737bfa3](https://github.com/vllm-project/vllm/commit/737bfa3a43ce386bd1894792f3302d9f3f9d73fa)

- **作者**: roikoren755
- **时间**: 2026-05-18T11:54:00Z
- **提交信息**: [Bugfix][Hybrid][NemotronH] Fix mamba_cache_mode=all + speculative decoding crash (#41233)

Signed-off-by: Roi Koren <roik@nvidia.com>

### [e414e1f](https://github.com/vllm-project/vllm/commit/e414e1f1c020108593526b706efaf89e427c05a2)

- **作者**: Kfir Toledo
- **时间**: 2026-05-18T11:36:02Z
- **提交信息**: [Bugfix][KV Offload] count appended GPU blocks in store group_sizes (#42945)

Signed-off-by: Kfir Toledo <kfir.toledo@ibm.com>

### [df852ed](https://github.com/vllm-project/vllm/commit/df852ed503ac1a79e568271cd6f136a7b2698f5e)

- **作者**: inisis
- **时间**: 2026-05-18T10:33:29Z
- **提交信息**: fix: remove unused norm for dpskv4 (#41710)

Signed-off-by: inisis <desmond.yao@buaa.edu.cn>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [88a860d](https://github.com/vllm-project/vllm/commit/88a860d7545aad69661daad7a1c2b04f59c76144)

- **作者**: Yuwen Zhou
- **时间**: 2026-05-18T10:04:45Z
- **提交信息**: [CPU] Add MXFP4 W4A16 MoE support (#41922)

Signed-off-by: yuwenzho <yuwen.zhou@intel.com>
Signed-off-by: Yuwen Zhou <yuwen.zhou@intel.com>

### [cac81b6](https://github.com/vllm-project/vllm/commit/cac81b6eda418fb5ca86b81197914dd02666353e)

- **作者**: Tianmu Li
- **时间**: 2026-05-18T10:04:41Z
- **提交信息**: [CPU Backend] Improve cpu thread utilization (#42666)

Signed-off-by: Li, Tianmu <tianmu.li@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b4601ad](https://github.com/vllm-project/vllm/commit/b4601ad43ff7ff2b9e2f52379144481e45bcf6c5)

- **作者**: Li, Jiang
- **时间**: 2026-05-18T10:04:36Z
- **提交信息**: [CPU] Add fused GDN support for AMX CPU platform (#42707)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [2267f70](https://github.com/vllm-project/vllm/commit/2267f70070bdee8057b4afae69cba9b847add587)

- **作者**: Jee Jee Li
- **时间**: 2026-05-18T10:04:31Z
- **提交信息**: [Kernel] Pack topk id/weights triton kernel (#42527)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [965d076](https://github.com/vllm-project/vllm/commit/965d076148326f4511b6b832cbe7d974db74dbe9)

- **作者**: Tony Lin
- **时间**: 2026-05-18T09:38:54Z
- **提交信息**: [CPU] Specify required KV cache layout for CPU attention backend (#42740)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [c38bed4](https://github.com/vllm-project/vllm/commit/c38bed4248e97e5ed981569777d035d31ace5368)

- **作者**: wenjun liu
- **时间**: 2026-05-18T08:36:45Z
- **提交信息**: delete xpu ci (#42582)

Signed-off-by: wenjun.liu <wenjun.liu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [998714b](https://github.com/vllm-project/vllm/commit/998714b21b413c78db8eb7af7f384dc90c0b10dc)

- **作者**: Xin Yang
- **时间**: 2026-05-18T08:32:46Z
- **提交信息**: [Perf] Add do_not_specialize in fused FP8 RoPE kernel (#42849)

Signed-off-by: Xin Yang <xyangx@amazon.com>

### [9537542](https://github.com/vllm-project/vllm/commit/9537542537728af9fac418ecf1604ad8e8d9ff93)

- **作者**: Harry Mellor
- **时间**: 2026-05-18T08:31:06Z
- **提交信息**: Revert checkpoint specific workaround in Transformers modelling backend (#42923)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [5ab6d1b](https://github.com/vllm-project/vllm/commit/5ab6d1b3fd407404cd78488bf6f4cbcde6d912b7)

- **作者**: Rishapveer Singh
- **时间**: 2026-05-18T08:14:36Z
- **提交信息**: [Model] [Perf] Use flatten for Qwen3.5's GDN output projection (#42311)

Signed-off-by: Rishapveer Singh <singhrishapveer@gmail.com>

### [7d5b033](https://github.com/vllm-project/vllm/commit/7d5b033782681acee274f4f379c9fadc557fd7e8)

- **作者**: Jee Jee Li
- **时间**: 2026-05-18T07:22:26Z
- **提交信息**: [LoRA] Support 2D and 3D MoE LoRA adapter  at the same time (#42242)

Signed-off-by: Jee Jee Li <pandaleefree@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [e3aeee5](https://github.com/vllm-project/vllm/commit/e3aeee5ff8bf7e89fea231d2a965701248eb43c0)

- **作者**: Nguyễn Thế Duy
- **时间**: 2026-05-18T07:17:53Z
- **提交信息**: [Bugfix] moe lora align kernel grid (#40131)

Signed-off-by: TheDuyIT <nduy250299@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Signed-off-by: dtnguyen <dtnguyen@nvidia.com>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-19
**监控日期**: 2026-05-18
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4806
- **最后更新**: 2026-05-18T23:58:20Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: lyj-jjj, Chendi.Xue, amy-why-3459

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是针对 `vllm-project/vllm-omni` 仓库昨日更新的分析总结：

### 1. 主要更新类型

-   **Bug修复 (Bugfix)**：这是昨日更新的主要部分，共涉及4个提交，修复了从模型推理到基准测试的多个问题。
-   **功能新增 (Feature)**：有1个提交为特定硬件（NPU）和模型（Hunyuan Image3.0）增加了新的量化支持。
-   **性能优化 (Performance)**：有1个提交针对特定硬件（XPU）优化了扩散模型的注意力机制后端。
-   **CI/测试 (CI/Testing)**：有1个提交专门修复了持续集成（CI）中的偶发失败问题，提升了项目稳定性。

### 2. 关键变更点及其与项目整体方向的关系

-   **模型兼容性与鲁棒性增强**：
    -   **[Qwen3-Omni] 修复短Code2Wav块输出**：修复了Qwen3-Omni模型在处理短音频块时可能出现的错误，直接提升了该多模态模型在实际应用中的稳定性和可用性。
    -   **[SenseNova U1] 修复导入错误**：修复了因`SupportsModuleOffload`功能变更导致的导入失败问题，确保了模型加载的兼容性。
    -   **与项目方向的关系**：这些修复直接服务于项目“为所有人提供易用、快速、便宜的**全模态**模型服务”的核心目标。确保主流多模态模型（如Qwen3-Omni）的稳定运行是项目成功的关键。

-   **硬件适配与性能优化**：
    -   **[XPU] 设置Flash Attention为默认扩散注意力后端**：针对Intel XPU硬件，将Flash Attention设为默认后端，并修复了交叉注意力中的`k_len`问题。这能显著提升在Intel硬件上运行扩散模型（如图像生成）的速度和效率。
    -   **[Hunyuan Image3.0] 支持NPU上的FA-FP8量化**：为华为NPU硬件上的Hunyuan Image3.0模型增加了FP8量化支持，这可以大幅降低显存占用并提升推理速度。
    -   **与项目方向的关系**：这些变更直接体现了项目“**便宜**”和“**快速**”的承诺。通过适配不同硬件（XPU, NPU）并利用其特定优化（Flash Attention, FP8量化），项目能够覆盖更广泛的用户群体，并降低他们的使用成本。

-   **基准测试与质量保证**：
    -   **[TTS] 删除语音端点基准测试中无意义的TTFT**：修正了语音合成（TTS）服务的基准测试指标，移除了不适用于流式场景的“首Token时间”（TTFT），使性能评估更准确、更有意义。
    -   **[Diffusion] 修复扩散量化基准测试**：修复了针对Omni输出的扩散模型量化基准测试，确保量化效果的评估是正确和可靠的。
    -   **[CI] 修复偶发CI失败**：提升了自动化测试的稳定性，保障了项目开发流程的顺畅。
    -   **与项目方向的关系**：这些工作虽然不直接面向最终用户，但它们是项目长期健康发展的基石。准确的基准测试能指导开发者进行正确的优化，稳定的CI能保证代码质量，最终都是为了提供“**易用**”和“**可靠**”的服务。

### 3. 对项目的影响和潜在意义

-   **提升用户体验**：修复了多个模型（Qwen3-Omni, SenseNova U1）的实际运行错误，直接改善了用户的使用体验。
-   **降低部署门槛和成本**：对XPU和NPU的优化，特别是FP8量化支持，使得用户可以在更多样、更经济的硬件上部署和运行多模态模型，降低了使用门槛和推理成本。
-   **增强项目可信度**：修复基准测试和CI问题，表明项目团队注重代码质量和性能评估的准确性，这有助于建立社区对项目的信任。
-   **加速开发迭代**：稳定的CI环境是快速迭代的基础，此次修复为未来的开发工作扫清了障碍。

### 4. 值得关注的技术点

-   **Flash Attention 在扩散模型中的应用**：将Flash Attention作为XPU上扩散模型的默认后端，这是一个重要的性能优化方向。这表明项目团队正在积极将先进的注意力机制优化技术（通常用于LLM）迁移到多模态模型的生成任务中。
-   **FP8量化在多模态模型上的实践**：在Hunyuan Image3.0上支持FA-FP8，展示了项目在模型压缩和加速方面的前沿探索。FP8量化是降低大模型推理成本的关键技术之一。
-   **针对流式场景的基准测试修正**：删除TTS基准测试中的TTFT，反映了项目对服务类型（如流式 vs. 非流式）的深刻理解，并据此设计了更合理的性能评估体系。

### 5. 这些提交如何影响项目发展

结合README中“Easy, fast, and cheap omni-modality model serving for everyone”的愿景，昨日的更新从多个维度推动了项目发展：

-   **“Easy” (易用)**：通过修复各种Bug（Qwen3-Omni, SenseNova U1），用户在使用这些模型时遇到的障碍更少，体验更流畅。
-   **“Fast” (快速)**：通过为XPU启用Flash Attention和为NPU启用FP8量化，显著提升了在特定硬件上的推理速度，让服务更快。
-   **“Cheap” (

## 详细提交记录

### [475a400](https://github.com/vllm-project/vllm-omni/commit/475a4002b0136235b4feb22d4a1e4b221ca5e112)

- **作者**: Chendi.Xue
- **时间**: 2026-05-18T23:58:15Z
- **提交信息**: [XPU] set flash_attn as default diffusion attn backend and fix k_len for cross_attn (#3525)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [ab59673](https://github.com/vllm-project/vllm-omni/commit/ab59673f21d804729557ac53d4c839e6d7353afb)

- **作者**: Sy03
- **时间**: 2026-05-18T18:59:23Z
- **提交信息**: [Bugfix][Qwen3-Omni] Handle short Code2Wav chunk outputs (#3687)

Signed-off-by: Sy03 <1370724210@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [8212867](https://github.com/vllm-project/vllm-omni/commit/821286794f1afaac7d44d7a75371e87527b30d22)

- **作者**: lyj-jjj
- **时间**: 2026-05-18T16:35:30Z
- **提交信息**: [HY-Imgae3.0] support hunyuan image3 dit fa-fp8 on npu (#3540)

Signed-off-by: lyj-jjj <liuyingjun5@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [309e5c3](https://github.com/vllm-project/vllm-omni/commit/309e5c38c665b91a9818f03dd5c515878caf0e53)

- **作者**: amy-why-3459
- **时间**: 2026-05-18T13:25:37Z
- **提交信息**: [BugFix][CI]Fixing occasional CI failures (#3623)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [f4115bd](https://github.com/vllm-project/vllm-omni/commit/f4115bd7716e1d29c8233bc8a69125dfdd35b3d1)

- **作者**: Ding Zuhao
- **时间**: 2026-05-18T13:12:46Z
- **提交信息**: [Bugfix] Fix SenseNova U1 broken import after SupportsModuleOffload  (#3691)

Signed-off-by: nussejzz <nussejzz@users.noreply.github.com>
Co-authored-by: nussejzz <nussejzz@users.noreply.github.com>

### [dbc589d](https://github.com/vllm-project/vllm-omni/commit/dbc589dbca09df88714ba433ee241c3aa6690235)

- **作者**: Lancer
- **时间**: 2026-05-18T09:23:40Z
- **提交信息**: [Bugfix] fix diffusion quantization benchmarking for Omni outputs (#3653)

Signed-off-by: Lancer <maruixiang6688@gmail.com>

### [990566a](https://github.com/vllm-project/vllm-omni/commit/990566aef10c69ac1fa3073437be0a3333b3dc15)

- **作者**: Yueqian Lin
- **时间**: 2026-05-18T09:18:18Z
- **提交信息**: [Bugfix][TTS] Drop meaningless TTFT from speech-endpoint benchmarks (#3674)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

---
