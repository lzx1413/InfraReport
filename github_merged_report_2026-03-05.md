# GitHub Stars 合并报告 - 2026-03-05

**合并日期**: 2026-03-06
**监控日期**: 2026-03-05
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


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1700
- **最后更新**: 2026-03-06T09:38:00Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Yicheng Gong, Crystal-jiang, Bin Jia

## AI分析总结

根据您提供的README摘要和提交记录，结合VeOmni项目“为多模态模型训练提供模型中心的分布式配方库”的核心目标，以下是昨日更新的分析总结：

### 1. 主要更新类型
*   **Bug修复**：修复了NPU性能分析数据上传和配置文件加载路径的问题。
*   **功能新增**：为NPU（华为昇腾AI处理器）新增了对GLM-5大语言模型的支持。
*   **性能优化**：优化了NPU的性能分析（Profiling）流程。

### 2. 关键变更点及其与项目整体方向的关系
*   **扩展硬件支持与模型生态**：新增`GLM-5`模型对`NPU`的支持，直接呼应了项目“**Scaling Any Modality Model Training**”的愿景。这表明项目正积极扩展其支持的硬件平台（从常见的GPU到国产NPU）和主流模型家族，以增强其通用性和实用性。
*   **提升开发与调试体验**：修复`load_checkpoint_path`配置项和优化`npu profiling`上传，属于对**基础设施和工具链**的打磨。这对于一个旨在提供“**分布式配方库**”的项目至关重要，能降低用户的使用门槛，提升训练流程的稳定性和可调试性。

### 3. 对项目的影响和潜在意义
*   **拓宽用户基础**：支持NPU和GLM-5，有助于吸引使用国产AI硬件和智谱AI模型系列的开发者和研究者，扩大项目社区和影响力。
*   **增强生产就绪性**：修复配置和优化工具链问题，表明项目正从功能实现阶段向**稳定、易用**的阶段演进，这对于项目的长期采纳至关重要。
*   **强化“配方库”定位**：每次新增模型或修复，都是在丰富和夯实其核心的“**Model-Centric Distributed Recipe Zoo**”，使这个“配方库”更全面、更可靠。

### 4. 值得关注的技术点
*   **NPU深度适配**：连续两个提交（#504, #531）均围绕NPU，表明项目团队正在对华为昇腾平台进行**重点投入和深度优化**，以解决其特有的性能分析和模型适配挑战。
*   **配置系统的健壮性**：对`load_checkpoint_path`空值的修复（#537），反映了对**配置容错性**的关注，这对于管理复杂分布式训练任务尤为重要。

### 5. 基于项目背景的提交影响分析
这些提交共同推动了VeOmni项目向其既定目标迈进：
*   **“Any Modality”**：通过支持GLM-5（强大的语言模型），间接增强了处理语言模态的能力，并为未来融合更多模态打下基础。
*   **“Model-Centric Recipe Zoo”**：GLM-5的加入**丰富了配方库的模型目录**；而配置和工具链的修复则**提升了“配方”本身的可靠性和易用性**。
*   **“Scaling...Training”**：对NPU的持续优化（性能分析、模型支持）直接体现了项目帮助用户在**多样化的硬件平台上高效扩展训练**的承诺。

**总结**：昨日的更新是一次**有针对性的迭代**，重点在于**扩展生态兼容性**（NPU硬件+GLM-5模型）和**夯实基础体验**（修复Bug、优化工具）。这符合VeOmni作为一个旨在提供通用分布式训练解决方案的中台项目的健康发展路径——在拓宽边界的同时，不断巩固内核。

## 详细提交记录

### [3637fe4](https://github.com/ByteDance-Seed/VeOmni/commit/3637fe48a5de761595e5fabe0e33c22e8c0089b3)

- **作者**: Yicheng Gong
- **时间**: 2026-03-05T13:15:08Z
- **提交信息**: [misc] fix: optimize npu profiling uploading (#504)

### [d21ea17](https://github.com/ByteDance-Seed/VeOmni/commit/d21ea17e4d7ca58e330af067cc06438f10771f2c)

- **作者**: Crystal-jiang
- **时间**: 2026-03-05T12:24:01Z
- **提交信息**: [model] feat: Add glm-5 model support for NPU (#531)

### [97d6c55](https://github.com/ByteDance-Seed/VeOmni/commit/97d6c556a8b5fb227e7a93fd0f8df735e4d971d5)

- **作者**: Bin Jia
- **时间**: 2026-03-05T08:38:19Z
- **提交信息**: [config] fix: fix empty load_checkpoint_path setting (#537)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2031
- **最后更新**: 2026-03-06T09:43:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1943
- **最后更新**: 2026-03-06T08:13:43Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5089
- **最后更新**: 2026-03-06T11:01:42Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Xingyu Liu, kahyun, Igor Shovkun

## AI分析总结

根据FlashInfer仓库的README摘要（专注于高性能GPU推理内核）及昨日提交记录，以下是分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了Mamba随机舍入测试在特定GPU架构上的兼容性问题（#2699），以及TRTLLM融合MoE内核中的整数溢出导致的非法内存访问（#2642）。
- **功能新增**：扩展了对MLA（多头注意力）头维度的支持，新增了特定配置（如nope头维度128、压缩维度256、RoPE维度64）（#2677）。
- **管理/配置更新**：更新了代码所有权配置，为特定目录（Qwen3.5 GDN相关）指定了负责人（#2680）。

### 2. 关键变更点及其与项目整体方向的关系
- **测试健壮性提升**（#2699）：通过引入运行时能力检查（`is_cvt_rs_supported`），确保测试在支持的GPU上正确运行，避免因硬件差异导致的失败。这强化了项目对多GPU架构的兼容性，符合其作为高性能、可移植推理库的定位。
- **大规模模型支持**（#2642）：修复整数溢出问题，使内核能够处理更大规模的MoE配置（如256全局专家、高token数）。这直接支持了项目处理现代大模型（如MoE架构）的核心目标。
- **模型架构扩展**（#2677）：新增对更多MLA头维度的支持，覆盖了DeepSeekV3、GLM-5等模型变体。这表明项目正积极跟进前沿模型架构，扩展其适用性。
- **项目管理优化**（#2680）：通过明确代码所有权，提升特定组件的维护效率，有助于项目在快速迭代中保持代码质量。

### 3. 对项目的影响和潜在意义
- **稳定性增强**：修复的整数溢出和测试兼容性问题减少了运行时崩溃风险，提升了库在生产环境中的可靠性。
- **生态兼容性扩展**：新增的MLA维度支持使FlashInfer能适配更多新兴模型，增强了其在推理生态中的竞争力。
- **开发者体验改善**：更精确的测试跳过机制和清晰的代码所有权有助于减少开发摩擦，加速集成和调试流程。

### 4. 值得关注的技术点
- **硬件感知的测试逻辑**：通过动态检测GPU计算能力（如`sm_120`）来跳过不支持的测试，体现了对异构计算环境的精细适配。
- **大规模张量索引处理**：将`int32`升级为`int64_t`以防止溢出，是高性能内核中处理极端规模数据的典型优化。
- **结构化类型定义**：引入MLA维度类型（如`MlaHeadDims`），提升了代码可读性和配置安全性，便于后续扩展。

### 5. 基于项目背景的提交影响分析
FlashInfer旨在提供**高性能GPU推理内核**，专注于效率与跨架构兼容性。昨日的提交：
- **强化了核心使命**：通过修复MoE内核溢出和扩展MLA支持，直接提升了库处理**大规模、复杂模型**的能力，这是推理性能的关键场景。
- **提升了工程成熟度**：测试健壮性和代码所有权管理优化，反映了项目从“功能实现”向“稳定交付”过渡，有助于吸引企业级用户。
- **紧跟技术趋势**：对Mamba、MoE、MLA等前沿模型组件的持续适配，确保项目在快速演变的大模型生态中保持相关性。

这些更新共同推动了FlashInfer向更**稳定、可扩展、生产就绪**的高性能推理库发展，巩固了其作为专业GPU内核优化工具的地位。

## 详细提交记录

### [124a2d3](https://github.com/flashinfer-ai/flashinfer/commit/124a2d32a4189ba8f16e6c9fb37b5a1fb5968113)

- **作者**: Igor Shovkun
- **时间**: 2026-03-05T22:48:03Z
- **提交信息**: HOTFIX: Skip mamba Stochastic Rounding tests on sm_120 (#2699)

<!-- .github/pull_request_template.md -->

## 📌 Description

I added a checker `is_cvt_rs_supported` that is used to skip mamba tests
that use Triton is a reference.
FlashInfer implementation already has fallback software-emulated SR
emulation, whereas the Triton reference does not, which leads to test
failures. Previously, we only checked that the main SM version is larger
or equal than 100.

## 🔍 Related Issues



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
* Added a utility to detect CUDA compute capability and whether a device
supports a specific runtime rounding path.

* **Tests**
* Updated tests to use the new runtime capability check, improving when
GPU-dependent stochastic rounding and related references are exercised
or skipped.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [858d8ff](https://github.com/flashinfer-ai/flashinfer/commit/858d8ff9834c2bd1a1b605e2219b6cf96b0b9a3c)

- **作者**: kahyun
- **时间**: 2026-03-05T18:10:04Z
- **提交信息**: Give knam codeowner override for Qwen3.5 (gdn) related directories (#2680)

<!-- .github/pull_request_template.md -->

## 📌 Description

Title 

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

* **Chores**
* Updated repository code ownership configuration to expand coverage for
GDN-related components and associated tests, ensuring clearer ownership
and review routing for those areas.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1b02c56](https://github.com/flashinfer-ai/flashinfer/commit/1b02c56bdbbdafca53ee083eaa26282d23a3063f)

- **作者**: Xingyu Liu
- **时间**: 2026-03-05T18:09:38Z
- **提交信息**: [fp8_blockwise]Fix int32 overflow in TRTLLM fused MoE activation kernel (#2642)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix CUDA Illegal Memory Access (IMA) caused by int32 overflow in
activationKernel and activationDeepSeekKernel in the TRTLLM fused MoE
pipeline.

Root cause: The index computation `permutedIdx * params.innerDim +
hiddenIdx` uses int32 arithmetic. With large MoE configurations (e.g.
256 global experts, topK=8, DP=2, EP=2), the values can exceed
INT32_MAX:
- num_tokens = 65536 (max_num_batched_tokens * DP)
- totalNumPaddedTokens up to 524,288 65536 * 8, worst case all tokens
route to local experts)
- innerDim =   2 * intermediate_size, suppose its >5k
- 524,287 * innerDim may be > INT32_MAX (2,147,483,647)


The overflow produces a negative index, causing out-of-bounds memory
access.
Fix: Cast permutedIdx to int64_t before the multiplication in both
activationKernel (line 82) and activationDeepSeekKernel (line 337).

The overflow may also cause issue in other places, e.g.
https://github.com/flashinfer-ai/flashinfer/pull/2643, but I don't have
time to validate https://github.com/flashinfer-ai/flashinfer/pull/2643
yet.

## 🔍 Related Issues

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x ] I have installed the hooks with `pre-commit install`.
- [ x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

Verified locally with the same model, works 

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed integer overflow issues in tensor indexing calculations,
enabling proper support for larger tensor dimensions without overflow
errors. Improves stability for large-scale tensor processing operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5e798b1](https://github.com/flashinfer-ai/flashinfer/commit/5e798b1ffaccece8abac1e3d2b22c02103bc1655)

- **作者**: Julien Debache
- **时间**: 2026-03-05T17:40:26Z
- **提交信息**: feat: add support for more MLA head dimensions (#2677)

<!-- .github/pull_request_template.md -->

## 📌 Description

### Primary Goal

Adds TRTLLM Gen support for MLA heads with nope head dimension `128`,
compressed dimension `256` and RoPE dimension `64`.

### Changes
- Updating the hash for TRTLLM Gen FMHA artifacts to point to a set of
generated kernels that supports the new dimensions
- Adjusted assertions to reflect the additional supported dimensions
- Introduced a type denoting the dimensions of an MLA head and an MLA
layer
- Introduced 3 instances of supported MLA layer: DeepSeekV3, GLM-5 and
our new smaller dimensions
- Added tests for new dimensions and refactored the tests to use the new
types above for parametrization
- Minor type hints fixes

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [X] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [X] I have installed the hooks with `pre-commit install`.
- [X] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [X] Tests have been added or updated as needed.
- [X] All tests are passing (`unittest`, etc.).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Broader support for trtllm-native and additional MLA/head-size
configurations.

* **Improvements**
* Formalized MLA dimension structures with expanded validation and
clearer messages.
* FP8-aware output handling: safer FP8→bf16 defaults, stricter output
shape/dtype checks.
* Relaxed allowances for sparse and non-sparse head-dimension
combinations.

* **Tests**
* Expanded and typed tests to cover MLA variants, head-size
permutations, and backend paths.

* **Chores**
  * Updated FMHA artifact references and checksums.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3127
- **最后更新**: 2026-03-06T08:27:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 32944
- **最后更新**: 2026-03-06T10:26:29Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Sayak Paul, Shenghai Yuan, Ando

## AI分析总结

根据提供的 `huggingface/diffusers` 仓库提交记录和 README 摘要（项目为开源扩散模型库），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增 RAE（Regularized Autoencoder）自动编码器实现（#13046）和 LTX2 条件生成管道（#13058）。
- **Bug修复/优化**：修复文档链接（#13213）、更新注意力后端依赖版本（#13161）。
- **代码质量/维护**：包含代码清理、测试更新、配置调整等。

### 2. 关键变更点及其与项目整体方向的关系
- **RAE 自动编码器**：引入了基于 DINOv2、SigLIP2、MAE 等预训练视觉编码器的新型自动编码器，支持图像重建和潜在表示学习。这与项目“提供先进扩散模型组件”的目标一致，扩展了模型架构多样性。
- **LTX2 条件管道**：新增支持视频和音频条件的生成管道，实现了多模态条件生成。强化了项目在**多模态扩散模型**领域的覆盖能力。
- **注意力后端更新**：确保使用最新的优化内核，提升计算效率，符合项目对**性能优化**的持续追求。
- **文档修复**：维护文档准确性，提升用户体验。

### 3. 对项目的影响和潜在意义
- **技术生态扩展**：RAE 和 LTX2 管道为研究者和开发者提供了新的工具，可能促进在图像/视频生成、跨模态应用等方面的创新。
- **性能与稳定性**：注意力后端更新有助于提升训练/推理速度；代码优化增强了模块的健壮性。
- **社区贡献导向**：多个提交由社区成员共同完成，体现了项目开放协作的特点。

### 4. 值得关注的技术点
- **RAE 设计**：采用“均值-方差”潜在表示约定，支持冻结编码器、潜在归一化缓冲等特性，与 VAE 等传统自动编码器形成互补。
- **LTX2 条件机制**：在潜在空间融合视频/音频条件，实现更灵活的多模态控制生成。
- **工程细节**：如设备映射多 GPU 支持、状态字典兼容性处理等，反映了生产级代码的考量。

### 5. 基于项目背景的提交影响分析
Diffusers 库旨在成为**扩散模型的标准化工具箱**。昨日更新：
- **强化了核心模型能力**：通过新增自动编码器和条件管道，丰富了模型架构选择，支持更复杂的生成任务。
- **紧跟研究前沿**：RAE 基于近期视觉表示学习进展（如 DINOv2），LTX2 涉及多模态生成，体现了项目对学术前沿的快速集成。
- **提升可用性与性能**：文档修复和依赖更新维护了用户体验；后端优化确保了库的运行效率。
- **促进社区研究**：新增示例训练脚本和研究项目文档，降低了使用门槛，鼓励社区参与和实验。

**总结**：昨日更新以功能扩展为主，同时包含维护性改进，整体推动了项目在**多模态生成**和**高效自动编码器**方向的发展，巩固了其作为扩散模型生态系统核心工具的地位。

## 详细提交记录

### [8ec0a5c](https://github.com/huggingface/diffusers/commit/8ec0a5ccad96957c10388d2d2acc7fdd8e0fab84)

- **作者**: Ando
- **时间**: 2026-03-05T14:47:14Z
- **提交信息**: feat: implement rae autoencoder. (#13046)

* feat: implement three RAE encoders(dinov2, siglip2, mae)

* feat: finish first version of autoencoder_rae

* fix formatting

* make fix-copies

* initial doc

* fix latent_mean / latent_var init types to accept config-friendly inputs

* use mean and std convention

* cleanup

* add rae to diffusers script

* use imports

* use attention

* remove unneeded class

* example traiing script

* input and ground truth sizes have to be the same

* fix argument

* move loss to training script

* cleanup

* simplify mixins

* fix training script

* fix entrypoint for instantiating the AutoencoderRAE

* added encoder_image_size config

* undo last change

* fixes from pretrained weights

* cleanups

* address reviews

* fix train script to use pretrained

* fix conversion script review

* latebt normalization buffers are now always registered with no-op defaults

* Update examples/research_projects/autoencoder_rae/README.md

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* Update src/diffusers/models/autoencoders/autoencoder_rae.py

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* use image url

* Encoder is frozen

* fix slow test

* remove config

* use ModelTesterMixin and AutoencoderTesterMixin

* make quality

* strip final layernorm when converting

* _strip_final_layernorm_affine for training script

* fix test

* add dispatch forward and update conversion script

* update training script

* error out as soon as possible and add comments

* Update src/diffusers/models/autoencoders/autoencoder_rae.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* use buffer

* inline

* Update src/diffusers/models/autoencoders/autoencoder_rae.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* remove optional

* _noising takes a generator

* Update src/diffusers/models/autoencoders/autoencoder_rae.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* fix api

* rename

* remove unittest

* use randn_tensor

* fix device map on multigpu

* check if the key is missing in the original state dict and only then add to the allow_missing set

* remove initialize_weights

---------

Co-authored-by: wangyuqi <wangyuqi@MBP-FJDQNJTWYN-0208.local>
Co-authored-by: Kashif Rasul <kashif.rasul@gmail.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>
Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [29b9109](https://github.com/huggingface/diffusers/commit/29b91098f68847f4e50d099735532c7d5735b17e)

- **作者**: Sayak Paul
- **时间**: 2026-03-05T13:53:07Z
- **提交信息**: [attention backends] change to updated repo and version. (#13161)

* change to updated repo and version.

* fix version and force updated kernels.

* propagate version.

### [ae5881b](https://github.com/huggingface/diffusers/commit/ae5881ba77fc26df801f0f76a9955cd66ddf68f0)

- **作者**: Shenghai Yuan
- **时间**: 2026-03-05T13:28:13Z
- **提交信息**: Fix Helios paper link in documentation (#13213)

* Fix Helios paper link in documentation

Updated the link to the Helios paper for accuracy.

* Fix reference link in HeliosTransformer3DModel documentation

Updated the reference link for the Helios Transformer model paper.

* Update Helios research paper link in documentation

* Update Helios research paper link in documentation

### [ab6040a](https://github.com/huggingface/diffusers/commit/ab6040ab2d84b1c6ce26a1f401dabad52cde4df5)

- **作者**: dg845
- **时间**: 2026-03-05T08:42:55Z
- **提交信息**: Add LTX2 Condition Pipeline (#13058)

* LTX2 condition pipeline initial commit

* Fix pipeline import error

* Implement LTX-2-style general image conditioning

* Blend denoising output and clean latents in sample space instead of velocity space

* make style and make quality

* make fix-copies

* Rename LTX2VideoCondition image to frames

* Update LTX2ConditionPipeline example

* Remove support for image and video in __call__

* Put latent_idx_from_index logic inline

* Improve comment on using the conditioning mask in denoising loop

* Apply suggestions from code review

Co-authored-by: Álvaro Somoza <asomoza@users.noreply.github.com>

* make fix-copies

* Migrate to Python 3.9+ style type annotations without explicit typing imports

* Forward kwargs from preprocess/postprocess_video to preprocess/postprocess resp.

* Center crop LTX-2 conditions following original code

* Duplicate video and audio position ids if using CFG

* make style and make quality

* Remove unused index_type arg to preprocess_conditions

* Add # Copied from for _normalize_latents

* Fix _normalize_latents # Copied from statement

* Add LTX-2 condition pipeline docs

* Remove TODOs

* Support only unpacked latents (5D for video, 4D for audio)

* Remove # Copied from for prepare_audio_latents

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>
Co-authored-by: Álvaro Somoza <asomoza@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
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


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 11922
- **最后更新**: 2026-03-06T10:10:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24158
- **最后更新**: 2026-03-06T10:31:11Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 20
- **主要提交者**: Ajay Anubolu, Chi McIsaac, akhilg-nv

## AI分析总结

根据提供的仓库提交记录和README摘要（SGLang项目是一个专注于高效LLM推理的框架），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及性能指标、gRPC错误处理、参数名、注意力机制、图像编辑等多个模块。
- **性能优化**：针对Triton内核的MOE性能、注意力机制（SWA解码优化）和调度器进行了优化。
- **功能新增**：增加了Ray actor支持、JSON日志记录功能、AMD GPU测试支持等。
- **代码/基础设施维护**：包括CI流程优化、代码清理、所有权文件更新、测试覆盖增强等。
- **重构**：对Speculative Decoding中的NaN/OOB检查进行了异步化重构。

### 2. 关键变更点及其与项目整体方向的关系
- **性能与稳定性**：多项修复和优化（如`bench_one_batch_server`的吞吐量指标、Triton MOE性能、注意力机制修复）直接服务于项目的核心目标——**高效、稳定的LLM推理**。
- **扩展性与部署**：新增Ray actor支持（#17684）和JSON日志（#19968）增强了项目的**分布式部署能力**和**可观测性**，符合生产级应用的需求。
- **硬件生态支持**：新增针对AMD GPU的测试（#19733, #19834），体现了项目在**多硬件平台支持**上的持续投入，有助于扩大用户基础。
- **代码质量与维护**：大量的修复和清理工作（如gRPC错误处理、代码清理、测试增强）提升了项目的**健壮性和可维护性**。

### 3. 对项目的影响和潜在意义
- **用户体验**：性能优化和Bug修复将带来更稳定、更高效的推理体验。
- **开发者体验**：结构化JSON日志和更好的错误处理（gRPC状态码）方便了系统监控和调试。
- **社区与协作**：更新CODEOWNERS和详细的提交记录（多作者合作）显示了活跃的社区协作和规范的流程。
- **生产就绪度**：对分布式调度（Ray）、可观测性（日志）和硬件兼容性的加强，使项目更贴近企业级部署要求。

### 4. 值得关注的技术点
- **异步化重构**（#19899）：将Speculative Decoding中的检查改为异步，可能提升流水线效率。
- **混合注意力机制修复**（#19369）：涉及底层核心算子的正确性，对推理结果质量至关重要。
- **量化修复**（#19844）：FP32向下转型问题修复，影响量化模型的精度和性能。
- **调度器集成**（#17684）：引入Ray进行进程管理，是向灵活分布式调度迈进的一步。

### 5. 基于项目背景的提交影响分析
SGLang旨在成为“LLM推理的操作系统”，追求**高性能、低延迟、易部署**。昨日的更新紧密围绕这一愿景：
- **强化核心引擎**：绝大多数提交针对推理后端（性能、正确性、扩展性），确保其作为可靠“操作系统内核”的地位。
- **拓展生态系统**：通过支持AMD和增强调度（Ray），项目正在构建一个**不依赖于单一硬件或编排工具**的开放生态系统。
- **提升成熟度**：在快速迭代中同时注重修复Bug、清理代码和增加测试，表明项目在向**稳定、可维护的成熟阶段**过渡。

**总结**：昨日更新以**夯实基础、优化性能、扩展生态**为主，是一次典型的“质量迭代”。它没有引入颠覆性特性，而是通过大量细致的工作，使SGLang作为一个LLM推理框架的**可靠性、效率和适用范围**得到了全面提升，与其打造高效、通用推理系统的目标高度一致。

## 详细提交记录

### [13af7cb](https://github.com/sgl-project/sglang/commit/13af7cbb025b6d948df29e8cba75cbaff33720b4)

- **作者**: Ajay Anubolu
- **时间**: 2026-03-05T23:58:17Z
- **提交信息**: fix: use consistent time denominator for throughput metrics in bench_one_batch_server (#19223)

### [dd2bbe6](https://github.com/sgl-project/sglang/commit/dd2bbe6d627d2d51c65e43e11e911ed5df4fc1dc)

- **作者**: Chang Su
- **时间**: 2026-03-05T22:53:18Z
- **提交信息**: fix(grpc): use context.abort() with proper status codes instead of in-band errors (#19972)

Signed-off-by: Chang Su <chang.s.su@oracle.com>

### [46dced6](https://github.com/sgl-project/sglang/commit/46dced64ea5a3cf345464b1cf5392f9b6682cfae)

- **作者**: Qiaolin Yu
- **时间**: 2026-03-05T22:50:40Z
- **提交信息**: Adjust padding size to improve triton_kernels moe performance (#19174)

### [346a413](https://github.com/sgl-project/sglang/commit/346a4131cfbac5fe2f42ba01d7c4062853e2ded5)

- **作者**: kpham-sgl
- **时间**: 2026-03-05T21:51:05Z
- **提交信息**: [Spec] Refactor NaN/OOB checks to async `maybe_detect_*` with env-var control (#19899)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [1c1712d](https://github.com/sgl-project/sglang/commit/1c1712d8e54124c1c0b6c6cd89165a77970523ab)

- **作者**: Alison Shao
- **时间**: 2026-03-05T21:30:44Z
- **提交信息**: [CI] Skip flashinfer-cubin reinstall when version matches (#19470)

Co-authored-by: Alison Shao <alisonshao@MacBook-Pro-D2W773R9CD.local>
Co-authored-by: Alison Shao <alisonshao@Mac.attlocal.net>
Co-authored-by: Alison Shao <alisonshao@mac.lan>

### [b3cfad0](https://github.com/sgl-project/sglang/commit/b3cfad0a80069a0952b4eadb275316dc16b59abe)

- **作者**: Xinyu Zhang
- **时间**: 2026-03-05T21:21:23Z
- **提交信息**: Add Ray actor support for scheduler process management (DP=1) (#17684)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [07e7603](https://github.com/sgl-project/sglang/commit/07e7603c0cda0e09086b5301a6d0148a778c12ba)

- **作者**: Minglei Zhu
- **时间**: 2026-03-05T20:45:25Z
- **提交信息**: Update sgl-attn to include SWA decode optimizations (#19655)

### [ebb66cc](https://github.com/sgl-project/sglang/commit/ebb66cc1de9d9572f7a674ec4e68827f5c7ea77c)

- **作者**: sglang-bot
- **时间**: 2026-03-05T20:42:42Z
- **提交信息**: [misc] Priority scheduling metrics cleanup (#19927)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [ff6048f](https://github.com/sgl-project/sglang/commit/ff6048fb9c3fda17f7f0048bc6dce58993e8ede0)

- **作者**: danielafrimi
- **时间**: 2026-03-05T19:27:07Z
- **提交信息**: rename  nemotron reasoning parser (#19865)

Signed-off-by: dafrimi <dafrimi@nvidia.com>

### [e58391d](https://github.com/sgl-project/sglang/commit/e58391dd7d18f1e98e236a7f3f262b1ca5c1123b)

- **作者**: Jonathan Lee
- **时间**: 2026-03-05T19:24:12Z
- **提交信息**: Add --json-log flag to enable structured JSON logging (#19968)

Co-authored-by: github_username <github_email>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [41fd53f](https://github.com/sgl-project/sglang/commit/41fd53fe37293681bff52aed1493229b8cd19c43)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-03-05T18:34:06Z
- **提交信息**: Fix `profile_activities` parameter name in `bench_one_batch_server_internal.py` (#19954)

### [d605d81](https://github.com/sgl-project/sglang/commit/d605d811fb332423e264f7d5862fa33b6890662f)

- **作者**: Mick
- **时间**: 2026-03-05T18:19:05Z
- **提交信息**: update CODEOWNERS (#19969)

### [203cd8e](https://github.com/sgl-project/sglang/commit/203cd8eb02a424bb39145cf46f8f577a468de5b5)

- **作者**: Michael
- **时间**: 2026-03-05T16:36:17Z
- **提交信息**: [AMD] [Z-Image-Turbo Day 0] Add Z-Image-Turbo nightly test for AMD GPUs (#19733)

### [73d272b](https://github.com/sgl-project/sglang/commit/73d272bddb6f23d4ce98e19e698494d07b76af9c)

- **作者**: akhilg-nv
- **时间**: 2026-03-05T16:05:35Z
- **提交信息**: Revised fix for HybridAttnBackend forward for linear attn (#19369)

### [b5edab5](https://github.com/sgl-project/sglang/commit/b5edab57f2ff7baa8ac5aeee149aab0dc59e61dd)

- **作者**: YC Tseng
- **时间**: 2026-03-05T15:09:57Z
- **提交信息**: [AMD] CI - Add MI35x nightly/PR tests for kv-cache-fp8 and allreduce-fusion (DeepSeek) (#19834)

Co-authored-by: bingxche <Bingxu.Chen@amd.com>

### [0de0d74](https://github.com/sgl-project/sglang/commit/0de0d741959c6c6337ae8251a01e4f32c9c2698b)

- **作者**: Zheng Wengang
- **时间**: 2026-03-05T13:12:30Z
- **提交信息**: [EPD][Feat]support adaptive forward (#18118)

### [806d41a](https://github.com/sgl-project/sglang/commit/806d41ab65728b5597561b29d6a4e44bfcf4f9ee)

- **作者**: StonyPort
- **时间**: 2026-03-05T09:54:59Z
- **提交信息**: [quant] fix fp32 downcasting (#19844)

Co-authored-by: qiuxuan.lzw <qiuxuan.lzw@alibaba-inc.com>

### [472eef4](https://github.com/sgl-project/sglang/commit/472eef4071ed94cb809a95031612f51779d799ad)

- **作者**: Rain Jiang
- **时间**: 2026-03-05T09:54:25Z
- **提交信息**: fa4 cleanup (#19727)

### [c36de62](https://github.com/sgl-project/sglang/commit/c36de62bfcfc5721bcf30825f3a5399975ee010d)

- **作者**: Chi McIsaac
- **时间**: 2026-03-05T08:56:39Z
- **提交信息**: [diffusion] fix images/edit with 2 images (#17520)

Signed-off-by: Chi McIsaac <chixie.mcisaac@gmail.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [dbc896f](https://github.com/sgl-project/sglang/commit/dbc896f204eacb2ad2aa9de80c033fc3187ab0c5)

- **作者**: xingsy97
- **时间**: 2026-03-05T08:17:15Z
- **提交信息**: [Test] Enhance JIT kvcache store kernel test coverage (#19630)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: 🤗 A PyTorch-native and Flexible Inference Engine with Hybrid Cache Acceleration and Parallelism for DiTs.
- **语言**: Python
- **星标数**: 1069
- **最后更新**: 2026-03-06T09:34:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 72207
- **最后更新**: 2026-03-06T10:49:09Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 27
- **主要提交者**: Yanhong Li, Paco Xu, Ajay Anubolu

## AI分析总结

根据提供的提交记录和README摘要（vLLM项目旨在提供“简单、快速、经济的LLM服务”），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占主导地位（约12项），涉及KV缓存、注意力后端、模型支持、工具调用、流处理等多个核心模块。
- **性能优化**：2项，针对MoE内核和编译配置。
- **功能新增**：2项，新增OLMo Hybrid模型支持和XPU平台支持。
- **文档更新**：3项，包括文档构建流程、集成指南和基准测试。
- **重构/代码质量**：4项，涉及代码清理、类型修复、警告消除和硬件API统一。
- **CI/发布流程**：3项，包括测试稳定性、权限设置和PyPI发布。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向（易用、快速、经济、普适）的关系 |
| :--- | :--- |
| **修复小KV缓存预热问题** (`#36176`) | 确保在极端配置下推理的**稳定性与性能**，提升“快速”服务的可靠性。 |
| **统一已保存/加载后端的编译配置** (`#35810`) | 增强模型部署的**一致性和可移植性**，支持“简单”的模型服务。 |
| **新增OLMo Hybrid模型支持** (`#32550`) | 扩展**模型生态**，让用户能服务更多类型的模型，提升“普适性”。 |
| **优化FusedMoE内核输出张量创建** (`#35794`) | 直接优化MoE模型的**计算性能**，是“快速”服务的核心。 |
| **在XPU上启用ModelRunnerV2** (`#36078`) | 扩大**硬件支持范围**（Intel GPU），使服务更“经济”和普适。 |
| **修复多个模型特定问题** (Qwen-Omni, Qwen-VL, FunASR) | 提升对**多模态/语音模型**的支持质量，巩固“为所有人服务”的愿景。 |
| **修复KV连接器调度器令牌计数** (`#34616`) | 修复异步KV加载的核心调度逻辑，保障**高吞吐量服务**的准确性。 |

### 3. 对项目的影响和潜在意义
- **稳定性大幅提升**：大量Bug修复覆盖了从底层内核到上层API的广泛场景，直接提高了生产环境的可靠性。
- **性能与效率优化**：针对MoE和编译流程的优化，有助于降低延迟、提升资源利用率，巩固其“快速”的优势。
- **生态持续扩展**：新增对OLMo Hybrid模型和Intel XPU的官方支持，降低了用户使用新模型和新硬件的门槛，吸引更广泛的开发者群体。
- **开发者体验改善**：文档更新、CI问题修复和代码质量提升，使项目更易于贡献和维护。

### 4. 值得关注的技术点
- **硬件抽象化**：提交 `#36085` 将 `torch.cuda.synchronize()` 替换为 `torch.accelerator.synchronize`，是向**多硬件后端统一**迈出的重要一步。
- **注意力后端精细化**：提交 `#35246` 重构ROCm注意力后端选择逻辑，`#36146` 为特定场景禁用FlashInfer路径，显示了对**不同硬件性能调优**的深度关注。
- **编译部署流程**：提交 `#35810` 确保编译配置的一致性，这对**模型预编译、保存和跨环境部署**的流程至关重要。
- **多模态/长上下文支持**：针对Qwen-Omni（音频）和Qwen-VL（视觉）的修复，体现了对**复杂输入和长序列处理**场景的持续投入。

### 5. 基于项目背景的提交影响分析
vLLM的核心目标是降低高性能LLM服务的门槛。昨日的提交集合**紧密围绕这一目标**：
- **巩固核心优势**：通过修复KV缓存、调度器和注意力内核的Bug，并优化MoE性能，**直接强化了其推理引擎的“快”与“稳”**，这是项目立身之本。
- **拓展服务边界**：支持新模型（OLMo Hybrid）、修复多模态模型问题、支持新硬件（XPU），**使“为所有人服务”的承诺更加落地**，扩大了潜在用户和用例范围。
- **完善项目基建**：改进CI、文档、发布流程和代码质量，**提升了项目的成熟度和可维护性**，这对于一个快速增长的开源项目至关重要，有助于吸引和留住贡献者。

**总结**：昨日更新是一次以**稳定性修复和生态扩展**为主的常规推进。它没有引入颠覆性特性，而是扎实地**打磨核心引擎、拓宽支持范围、完善项目基础**，这正是一个成熟项目在追求“易用、快速、经济、普适”目标过程中健康、可持续的发展方式。

## 详细提交记录

### [a73af58](https://github.com/vllm-project/vllm/commit/a73af584fe6d4c1c2781d537c35e3cc85f58480b)

- **作者**: Nick Hill
- **时间**: 2026-03-05T22:48:10Z
- **提交信息**: [Model Runner V2] Fix warmup for very small kvcache and/or blocksizes (#36176)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [a97954b](https://github.com/vllm-project/vllm/commit/a97954b6a8fa41a162ebf58f80a1460a98e0baf0)

- **作者**: Zhengxu Chen
- **时间**: 2026-03-05T20:08:12Z
- **提交信息**: [compile] Consistent compiler config for saved/loaded vllm backends. (#35810)

Signed-off-by: zhxchen17 <zhxchen17@fb.com>

### [a911f4d](https://github.com/vllm-project/vllm/commit/a911f4dd20d0a0fcfee362f096e9c6fd23d59590)

- **作者**: Yanhong Li
- **时间**: 2026-03-05T19:51:06Z
- **提交信息**: [Model] Add support for OLMo Hybrid (#32550)

### [5395471](https://github.com/vllm-project/vllm/commit/5395471d29f703f19213da629102edc6e9b944be)

- **作者**: Russell Bryant
- **时间**: 2026-03-05T19:08:48Z
- **提交信息**: [CI] Add explicit permissions to macOS smoke test workflow (#35775)

Signed-off-by: Russell Bryant <rbryant@redhat.com>

### [a57c877](https://github.com/vllm-project/vllm/commit/a57c877f18188cb7bafc0fc5309b6c88fe2a8f66)

- **作者**: Frank Wang
- **时间**: 2026-03-05T19:05:56Z
- **提交信息**: [BugFix] Fallback from FA4->FA2 for Batch Invariance (#36059)

Signed-off-by: frankwang28 <frank.wbb@hotmail.com>

### [f917020](https://github.com/vllm-project/vllm/commit/f9170209834af0e8e53a6d16ccd17eacc0db2c67)

- **作者**: Xin Yang
- **时间**: 2026-03-05T18:47:53Z
- **提交信息**: [Perf] Optimize FusedMoEModularKernel output tensor using torch.empty (#35794)

Signed-off-by: Xin Yang <xyangx@amazon.com>

### [86483ca](https://github.com/vllm-project/vllm/commit/86483ca7749b3d7a2ae16283a7896c203983f1ef)

- **作者**: tomeras91
- **时间**: 2026-03-05T17:49:05Z
- **提交信息**: [Bugfix] Disable FlashInfer TRTLLM BF16 path for non-gated MoE (#36146)

Signed-off-by: Tomer Asida <57313761+tomeras91@users.noreply.github.com>

### [b93a9e6](https://github.com/vllm-project/vllm/commit/b93a9e6f6d91baf59e39089ce8dbf2f2a3f0f6c9)

- **作者**: Netanel Haber
- **时间**: 2026-03-05T17:29:30Z
- **提交信息**: ParakeetProjection.norm = RMSNorm instead of nn.LayerNorm (#36133)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>

### [d8839ef](https://github.com/vllm-project/vllm/commit/d8839ef7d964dd98b82e671e743b42754be3350c)

- **作者**: Xinyu Chen
- **时间**: 2026-03-05T17:19:18Z
- **提交信息**: [XPU] Enable ModelRunnerV2 on XPU (#36078)

Signed-off-by: Xinyu Chen <xinyu1.chen@intel.com>

### [e998fa7](https://github.com/vllm-project/vllm/commit/e998fa76b99a73ba923adeb7457376228269cc9c)

- **作者**: Avery Miao
- **时间**: 2026-03-05T17:16:29Z
- **提交信息**: [BUGFIX]Fix Qwen-Omni models audio max_token_per_item estimation error leading to encoder_cache_size is 0 (#35994)

Signed-off-by: Miao, Avery <avery.miao@intel.com>

### [6a89519](https://github.com/vllm-project/vllm/commit/6a895197fafa7069be75ff615709b77546bcec30)

- **作者**: Jiayi Yan
- **时间**: 2026-03-05T17:05:46Z
- **提交信息**: [Bugfix][CI] fix typos (#34934)

Signed-off-by: 1195343015 <1195343015@qq.com>
Signed-off-by: Jiayi Yan <66017932+1195343015@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [8c760b6](https://github.com/vllm-project/vllm/commit/8c760b6ab6993c6a0d5f639747baefedb4612525)

- **作者**: Sage Moore
- **时间**: 2026-03-05T16:51:26Z
- **提交信息**: [ROCm] Refactor ROCm attention backend selection logic (#35246)

Signed-off-by: Sage Moore <sage@neuralmagic.com>

### [3ee6859](https://github.com/vllm-project/vllm/commit/3ee68590c7fafe05f1db1f1bee019c7b3a83ec96)

- **作者**: AllenDou
- **时间**: 2026-03-05T16:07:37Z
- **提交信息**: refactor funasr model. (#36108)

Signed-off-by: zixiao <shunli.dsl@alibaba-inc.com>
Co-authored-by: zixiao <shunli.dsl@alibaba-inc.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [7196348](https://github.com/vllm-project/vllm/commit/719634815791ad97cf1e35ad52d4e39e630aeafd)

- **作者**: Cyrus Leung
- **时间**: 2026-03-05T16:07:19Z
- **提交信息**: [Bugfix] Fix Qwen-VL tokenizer implementation (#36140)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [176c799](https://github.com/vllm-project/vllm/commit/176c799f4c512daf0904556940fc9a2c938af5ce)

- **作者**: Ning Xie
- **时间**: 2026-03-05T16:00:12Z
- **提交信息**: [openai api] log exception in exception handler (1/N) (#31164)

Signed-off-by: Andy Xie <andy.xning@gmail.com>

### [612e772](https://github.com/vllm-project/vllm/commit/612e7729c2a548a7b6c9baa1821f419909777ffa)

- **作者**: Or Ozeri
- **时间**: 2026-03-05T14:25:15Z
- **提交信息**: [KVConnector] Scheduler: Fix num_computed_tokens after async KV load (#34616)

Signed-off-by: Or Ozeri <oro@il.ibm.com>

### [ecde7af](https://github.com/vllm-project/vllm/commit/ecde7af9c492077bbf1bd8df16d941b1b441b60b)

- **作者**: Harry Mellor
- **时间**: 2026-03-05T13:59:44Z
- **提交信息**: Fix import that was moved in Transformers 5.2.0 (#36120)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [8df5233](https://github.com/vllm-project/vllm/commit/8df523351f6e665ea5b07f1b731aa2449d197624)

- **作者**: Harry Mellor
- **时间**: 2026-03-05T13:58:16Z
- **提交信息**: [Docs] Only build docs if `documentation` or `ready` labels are present (#36135)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [b03ff6a](https://github.com/vllm-project/vllm/commit/b03ff6a96bb090676cab07c432b4b0937abb7011)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-05T13:52:49Z
- **提交信息**: [CI] Stabilize test_no_args_tool_call and add ROCm-specific server args (#36107)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [ed81d5e](https://github.com/vllm-project/vllm/commit/ed81d5edd16b0d933d0e1115003c258dcecd991c)

- **作者**: Ajay Anubolu
- **时间**: 2026-03-05T12:14:20Z
- **提交信息**: [Bugfix] Fix RunAI streamer crash with S3-hosted model paths (#35976)

Signed-off-by: AjAnubolu <anuboluajay@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [3c23ac8](https://github.com/vllm-project/vllm/commit/3c23ac840e758e7b4ff34752e25d9eac12e4a3da)

- **作者**: Shiyan Deng
- **时间**: 2026-03-05T11:37:47Z
- **提交信息**: [Bugfix] Fix mypy errors in hermes_tool_parser.py (#36114)

Signed-off-by: Shiyan Deng <dsy842974287@meta.com>

### [a708ef5](https://github.com/vllm-project/vllm/commit/a708ef59443377aeda2d8ece804fa1e916881577)

- **作者**: cjackal
- **时间**: 2026-03-05T10:55:31Z
- **提交信息**: [Misc] Fix SyntaxWarning - invalid escape sequence '\e' (#36020)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [66a2209](https://github.com/vllm-project/vllm/commit/66a2209645438e9ad20b1bfb8fa4eca219944d46)

- **作者**: Kunshang Ji
- **时间**: 2026-03-05T10:36:39Z
- **提交信息**: [Hardware] Replace `torch.cuda.synchronize()` api with `torch.accelerator.synchronize` (#36085)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [0bfa229](https://github.com/vllm-project/vllm/commit/0bfa229bf1f6b12f215d045f4acb4b9607937f32)

- **作者**: Doug Smith
- **时间**: 2026-03-05T09:43:50Z
- **提交信息**: [Release] Include source distribution (sdist) in PyPI uploads (#35136)

Signed-off-by: dougbtv <dosmith@redhat.com>
Co-authored-by: Daniele Trifirò <dtrifiro@redhat.com>

### [7493c51](https://github.com/vllm-project/vllm/commit/7493c51c5532c25e2f2573eb274461e39f7e2a0b)

- **作者**: Paco Xu
- **时间**: 2026-03-05T09:39:50Z
- **提交信息**: [Docs] add Dynamo/aibrix integration and kubeai/aks link (#32767)

Signed-off-by: Paco Xu <paco.xu@daocloud.io>

### [ac773bb](https://github.com/vllm-project/vllm/commit/ac773bbe8095b4493c258abbf35c2a2d10d2faab)

- **作者**: Reagan Lee
- **时间**: 2026-03-05T09:38:25Z
- **提交信息**: [Docs] Update docs to include mm processor + encoder benchmarks  (#34083)

Signed-off-by: Reagan <reaganjlee@gmail.com>

### [48e376a](https://github.com/vllm-project/vllm/commit/48e376a007173910330a8c83f53474b21e4279c0)

- **作者**: Christian Munley
- **时间**: 2026-03-05T09:06:57Z
- **提交信息**: qwen3coder tool parser fix anyOf double encoded parameters (#36032)

Signed-off-by: Christian Munley <cmunley@nvidia.com>

### [21eb2c3](https://github.com/vllm-project/vllm/commit/21eb2c3372fb6447ef36bee44ff7af79a330ffec)

- **作者**: Isotr0py
- **时间**: 2026-03-05T08:55:04Z
- **提交信息**: [Chore] Correct MTP models test registry ordering (#36115)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-06
**监控日期**: 2026-03-05
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 2937
- **最后更新**: 2026-03-06T10:42:37Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 12
- **主要提交者**: rongfu.leng, Alicia, Ziming Huang

## AI分析总结

根据 `vllm-omni` 仓库的 README 摘要（“为所有人提供简单、快速、经济的全模态模型服务”）和昨日的提交记录，以下是分析总结：

### 1. 主要更新类型
- **功能新增**：3项（支持Qwen3-TTS灵活任务类型、支持LTX-2文本/图像转视频、Qwen3TTS减少首字延迟）
- **Bug修复**：4项（修复全静音TTS输出、修复HTTP状态码、修复LongCat序列并行问题、修复高并发测试问题）
- **性能优化**：2项（优化Qwen3-Omni异步分块延迟、移除冗余字段）
- **文档/测试**：3项（添加测试指南文档、清理测试目录、为扩散模型添加进度条）
- **CI/代码清理**：2项（移除高并发测试、清理代码结构）

### 2. 关键变更点及其与项目整体方向的关系
- **全模态支持强化**：新增对 **LTX-2文本/图像转视频模型** 的支持，直接扩展了项目的“全模态”能力边界，从语音进一步覆盖到视频生成。
- **TTS体验优化**：针对Qwen3-TTS模型的多项改进（灵活任务配置、减少首字延迟TTFA），提升了语音合成的**易用性和响应速度**，符合“快速、简单”的服务目标。
- **服务稳定性与正确性**：修复了TTS静音输出、HTTP状态码、序列并行等关键Bug，增强了服务的**可靠性和用户体验**，是生产级服务的基础。
- **开发者体验**：添加测试指南、进度条、清理测试结构，降低了贡献和使用的门槛，支持“为所有人”的开放生态。

### 3. 对项目的影响和潜在意义
- **功能矩阵扩展**：视频生成能力的加入，使vllm-omni从“文本+语音+图像”向更完整的“全模态”平台迈进。
- **生产就绪度提升**：对延迟、稳定性、错误处理的持续优化，表明项目正从功能实现阶段向**性能打磨和稳定交付**阶段过渡。
- **社区协作活跃**：多个提交由不同贡献者签署并合作完成，显示社区参与度高，项目发展健康。

### 4. 值得关注的技术点
- **灵活任务类型配置**（#1197）：允许Qwen3-TTS模型动态适应不同任务，提高了模型部署的灵活性。
- **异步分块延迟优化**（#1656）：针对流式响应场景优化网络传输，对实时语音/视频服务至关重要。
- **Float32精度修复**（#1664）：在TTS解码中强制使用float32避免静音输出，揭示了特定场景下精度对生成质量的影响。
- **LongCat序列并行修复**（#1631）：涉及大规模序列处理的底层并行逻辑，对支持长上下文模型有重要意义。

### 5. 基于项目背景的提交影响分析
vllm-omni旨在成为**统一、高效的全模态模型服务引擎**。昨日的更新整体上：
- **正向推进核心使命**：通过增加视频模型支持和优化语音合成，**直接强化了“全模态”和“快速”两大标签**。
- **夯实工程基础**：大量Bug修复和优化工作提升了系统的健壮性，这是大规模服务“为所有人”的前提。
- **优化开发者旅程**：文档和测试的改进降低了参与门槛，有助于吸引更多开发者和用户，促进生态增长。
- **体现技术前瞻性**：对序列并行、异步传输等底层性能的优化，为未来支持更复杂、更大的多模态模型做好了技术储备。

**总结**：昨日更新是一次**均衡的迭代**，既在功能前沿（视频生成）进行拓展，又在核心体验（TTS质量、服务稳定性）上深耕细作，同时不忘改善开发者体验，完全符合其打造易用、高效、全面全模态服务平台的长期愿景。

## 详细提交记录

### [8536dce](https://github.com/vllm-project/vllm-omni/commit/8536dce759fb8c02fa4085ebe2e0fc1e5c3dc67e)

- **作者**: Yueqian Lin
- **时间**: 2026-03-05T20:28:22Z
- **提交信息**: [Cleanup] Move cosyvoice3 tests to model subdirectory (#1666)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [c0b714a](https://github.com/vllm-project/vllm-omni/commit/c0b714a8aced43bbbafe54d6f44a06e6d006c195)

- **作者**: Jack Lee
- **时间**: 2026-03-05T18:39:09Z
- **提交信息**: [Feature] Support flexible task_type configuration for Qwen3-TTS models (#1197)

Signed-off-by: Jack Lee <695697442@qq.com>
Signed-off-by: jackleehal <695697442@qq.com>
Co-authored-by: google-labs-jules[bot] <161369871+google-labs-jules[bot]@users.noreply.github.com>
Co-authored-by: JackLeeHal <15664755+JackLeeHal@users.noreply.github.com>

### [e643aae](https://github.com/vllm-project/vllm-omni/commit/e643aaec1561747079f70815986419dc7cb6a768)

- **作者**: zhanqiuhu
- **时间**: 2026-03-05T16:04:26Z
- **提交信息**: [Bugfix] Fix all-silence TTS output: use float32 for speech tokenizer decoder (#1664)

Signed-off-by: Zhanqiu Hu <zh338@cornell.edu>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [d5ddc19](https://github.com/vllm-project/vllm-omni/commit/d5ddc190f9ace1aac9edb58dcdd47534c0ed1b65)

- **作者**: Canlin Guo
- **时间**: 2026-03-05T15:56:14Z
- **提交信息**: [UX] Add progress bar for diffusion models (#1652)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [ea317e4](https://github.com/vllm-project/vllm-omni/commit/ea317e455202772d31c4d154df0570f1fd61bec2)

- **作者**: wangyu
- **时间**: 2026-03-05T15:41:36Z
- **提交信息**: [Doc] Add the test guide document. [skip ci] (#1376)

Signed-off-by: yenuo26 <410167048@qq.com>

### [28c2200](https://github.com/vllm-project/vllm-omni/commit/28c2200b47c9ae8acb87ad761462fe20b7290db0)

- **作者**: Lidang Jiang
- **时间**: 2026-03-05T15:38:20Z
- **提交信息**: [BugFix] Return proper HTTP status for ErrorResponse in create_speech (#1687)

Signed-off-by: Lidang-Jiang <lidangjiang@gmail.com>

### [83fe7d0](https://github.com/vllm-project/vllm-omni/commit/83fe7d005b9d92980390d652742ba0a42fedabb6)

- **作者**: WeiQing Chen
- **时间**: 2026-03-05T15:31:48Z
- **提交信息**: [Model] support LTX-2 text-to-video image-to-video (#841)

Signed-off-by: David Chen <530634352@qq.com>
Signed-off-by: WeiQing Chen <40507679+david6666666@users.noreply.github.com>

### [6a45efb](https://github.com/vllm-project/vllm-omni/commit/6a45efb287ef6722e4a59a2d388750688184b3b1)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-03-05T15:14:41Z
- **提交信息**: [Feat][Qwen3TTS] reduce TTFA with flexible initial phase (#1583)

Signed-off-by: pablo <pablo@agigo.ai>
Co-authored-by: pablo <pablo@agigo.ai>

### [070ea0d](https://github.com/vllm-project/vllm-omni/commit/070ea0ddc310afb317382f57f334697e14990258)

- **作者**: Ziming Huang
- **时间**: 2026-03-05T14:26:30Z
- **提交信息**: [Optimize][Qwen3-Omni] Reduce inter-packet latency in async chunk  (#1656)

Signed-off-by: ZeldaHuang <hzm414167@alibaba-inc.com>

### [e674d60](https://github.com/vllm-project/vllm-omni/commit/e674d600087dd9c46bf14726cdcd72a6b1e590f2)

- **作者**: Alicia
- **时间**: 2026-03-05T09:46:37Z
- **提交信息**: [CI] Remove high concurrency tests before issue #1374 fixed. (#1683)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [562136d](https://github.com/vllm-project/vllm-omni/commit/562136d390b2e902d124e6e710dffb706005283e)

- **作者**: rongfu.leng
- **时间**: 2026-03-05T09:36:19Z
- **提交信息**: [Misc] remove logits_processor_pattern this field, because vllm have … (#1675)

Signed-off-by: rongfu.leng <lenronfu@gmail.com>

### [fa944bd](https://github.com/vllm-project/vllm-omni/commit/fa944bd8e8bbaaa990b86ea743cfb1e2bac00d79)

- **作者**: Alex Brooks
- **时间**: 2026-03-05T09:31:00Z
- **提交信息**: [BugFix] Fix LongCat Sequence Parallelism / Small Cleanup (#1631)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

---
