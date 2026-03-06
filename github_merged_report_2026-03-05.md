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
- **主要提交者**: Yicheng Gong, Bin Jia, Crystal-jiang

## AI分析总结

根据您提供的提交记录和README摘要，我对VeOmni项目昨日的更新分析如下：

### 1. 主要更新类型
- **性能优化**：优化了NPU（神经网络处理器）的性能分析数据上传流程。
- **功能新增**：为NPU平台新增了对GLM-5模型的支持。
- **Bug修复**：修复了配置文件中`load_checkpoint_path`参数为空时的设置问题。

### 2. 关键变更点及其与项目整体方向的关系
- **NPU生态强化**：两项提交（#504, #531）均围绕NPU展开，表明项目正积极适配国产AI硬件生态，这与README中“Scaling Any Modality Model Training”（扩展任意模态模型训练）的目标一致，旨在扩大硬件兼容性。
- **配置健壮性提升**：修复配置加载问题（#537）直接服务于项目“Model-Centric Distributed Recipe Zoo”（以模型为中心的分布式配方库）的核心定位，确保训练配方和配置的可靠性。

### 3. 对项目的影响和潜在意义
- **提升开发者体验**：优化NPU性能分析上传和修复配置错误，降低了用户在使用NPU或复杂配置时的操作门槛和故障率。
- **扩展模型覆盖范围**：引入GLM-5（智谱AI的大语言模型）支持，丰富了项目预置的模型库，增强了其作为“配方动物园”的实用性。
- **增强硬件适配竞争力**：持续投入NPU优化，有助于项目在国产化AI训练基础设施中占据更有利位置。

### 4. 值得关注的技术点
- **NPU深度集成**：提交显示项目正在进行NPU的专项优化（性能分析、模型适配），这可能涉及自定义内核或内存管理优化。
- **GLM-5模型适配**：将GLM-5集成到分布式训练框架中，可能涉及模型并行、优化器状态分区等分布式策略的适配工作。
- **配置系统容错**：对空配置路径的处理修复，反映了项目配置管理系统的成熟度在提高。

### 5. 基于项目背景的提交影响分析
VeOmni旨在成为一个**模型中心化的分布式训练配方库**。昨日的提交从三个层面推动这一目标：
- **基础设施层**（#504）：通过优化NPU性能工具链，提升了底层硬件的可观测性和训练效率，使“分布式”训练更稳定、更易调试。
- **模型层**（#531）：新增GLM-5支持，直接扩充了“配方库”的模型多样性，使用户能基于更多前沿模型进行多模态训练实验。
- **用户体验层**（#537）：修复配置错误，降低了使用“配方”的复杂度，使研究人员和工程师能更专注于模型本身而非框架问题。

**总结**：昨日的更新是一次聚焦于**NPU生态拓展和框架稳健性**的迭代。它强化了VeOmni作为硬件友好、模型丰富的分布式训练平台的特质，使其更贴近“一站式”多模态模型训练解决方案的愿景。特别是对GLM-5和NPU的支持，显示出项目紧跟国内大模型和AI硬件发展趋势的战略方向。

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
- **星标数**: 5088
- **最后更新**: 2026-03-06T08:06:48Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Julien Debache, Igor Shovkun, kahyun

## AI分析总结

根据对FlashInfer仓库昨日提交记录的分析，结合其作为**高性能GPU推理内核库**的项目背景，总结如下：

### 1. 主要更新类型
- **Bug修复**：修复了Mamba测试在特定GPU架构上的失败问题，以及TRTLLM融合MoE内核中的整数溢出导致的非法内存访问。
- **功能新增**：扩展了对更多MLA（Multi-Head Latent Attention）头维度的支持。
- **配置/维护更新**：更新了代码所有权配置，优化了项目维护流程。

### 2. 关键变更点及其与项目整体方向的关系
- **测试健壮性增强** (`124a2d3`)：通过引入运行时能力检查，确保测试在不同GPU架构（特别是`sm_120`及以下）上能正确跳过不支持的功能。这**强化了项目的跨平台兼容性和测试可靠性**，符合其作为底层高性能库需广泛适配硬件的目标。
- **大模型支持修复** (`1b02c56`)：修复了TRTLLM融合MoE管道中在处理**大规模专家混合模型**时的整数溢出问题。这直接**提升了库在处理前沿大模型（如MoE架构）时的稳定性和扩展性**，是项目支持高效、大规模推理的核心。
- **模型架构扩展** (`5e798b1`)：新增对特定MLA头维度（如128/256/64）的支持，并引入了更结构化的类型定义。这**体现了项目紧跟模型架构演进**（如DeepSeekV3, GLM-5），持续扩展其支持的注意力变体，以覆盖更广泛的模型需求。
- **项目管理优化** (`858d8ff`)：为特定目录设置代码所有者，**优化了大型开源项目的协作与审查流程**，有助于维护质量。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：两个Bug修复直接避免了运行时崩溃（IMA）和测试失败，增强了生产环境下的可靠性。
- **生态扩展**：对MLA新维度和大规模MoE的支持，使FlashInfer能更好地服务于**不断涌现的新模型和更大规模的部署场景**，巩固了其在推理加速生态中的竞争力。
- **开发者体验**：更精确的测试跳过机制和清晰的代码所有权，改善了贡献者和维护者的体验。

### 4. 值得关注的技术点
- **硬件兼容性精细检测**：新增`is_cvt_rs_supported`工具，用于检测GPU是否支持特定的运行时舍入路径，体现了对**硬件特性差异的精细处理**。
- **大规模计算的防溢出处理**：将索引计算从`int32`提升到`int64`，是处理**超大规模张量**（token数、专家数、维度乘积巨大）时的关键技术细节。
- **结构化类型定义**：为MLA维度引入专用类型，提升了代码的**类型安全性和可维护性**，是库走向更成熟设计的表现。

### 5. 基于项目背景的提交影响分析
FlashInfer的目标是提供**高性能的GPU推理内核**。昨日的更新整体上是一次**夯实基础、扩展前沿**的迭代：
- **夯实基础**：通过修复底层内核的溢出Bug和增强测试健壮性，**强化了核心基础设施的稳定性和鲁棒性**，这是高性能库的生命线。
- **扩展前沿**：通过支持新的MLA维度和修复大规模MoE问题，**积极适配了当前大模型领域快速发展的架构需求**（如更复杂的注意力机制和MoE模型）。这表明项目并非固守已有优化，而是持续演进以保持其技术领先性和实用性。
- **这些提交共同确保了FlashInfer能够在支持最新、最复杂模型的同时，维持其作为底层加速库所必需的高性能和可靠性**，直接推动了其“为推理提供高性能GPU内核”的核心使命。

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
- **主要提交者**: Ando, dg845, Sayak Paul

## AI分析总结

根据提供的提交记录和README摘要（Apache 2.0许可的开源项目），以下是针对huggingface/diffusers仓库昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增RAE（Regularized Autoencoder）自编码器实现（#13046）和LTX2条件生成管道（#13058）。
- **Bug修复/优化**：修复文档链接（#13213）、更新注意力后端依赖版本（#13161）。
- **代码质量/维护**：包含代码清理、测试修复、配置调整等多项改进。

### 2. 关键变更点及其与项目整体方向的关系
- **RAE自编码器**：实现了基于DINOv2、SigLIP2、MAE等预训练模型的三种编码器，支持图像重建和潜在表示学习，**扩展了diffusers在自监督学习和表示学习领域的能力**，与项目“提供先进扩散模型”的目标一致。
- **LTX2条件管道**：新增支持视频和音频条件的生成管道，**增强了多模态条件生成能力**，符合项目向视频、音频等复杂生成任务扩展的趋势。
- **注意力后端更新**：更新了注意力内核的依赖版本，**保持与底层高性能算子的兼容性和性能优化**。
- **文档修复**：维护文档准确性，提升用户体验。

### 3. 对项目的影响和潜在意义
- **技术生态扩展**：RAE自编码器为图像生成和编辑提供了新的潜在表示方案，可能提升生成质量或效率；LTX2管道拓宽了条件生成的应用场景（如视频合成）。
- **开发者体验**：提供了完整的训练脚本、转换脚本和示例，降低了研究和使用门槛。
- **性能与稳定性**：依赖更新和代码优化有助于维持库的稳定性和计算效率。

### 4. 值得关注的技术点
- **RAE的模块化设计**：支持多种预训练编码器（DINOv2、SigLIP2、MAE），便于扩展和实验。
- **潜在表示规范化**：使用均值/标准差约定，并注册无操作的规范化缓冲区，提高了灵活性和兼容性。
- **LTX2的条件融合机制**：在采样空间（而非速度空间）中融合去噪输出与潜在变量，可能影响生成效果。
- **多GPU支持**：RAE中修复了设备映射问题，支持分布式训练。

### 5. 基于项目背景的提交影响分析
- **强化核心优势**：diffusers致力于成为扩散模型的综合性库，新增RAE和LTX2管道**丰富了模型架构和生成范式**，巩固了其在生成式AI领域的领先地位。
- **推动研究与应用**：RAE自编码器作为研究项目（`research_projects/`），体现了项目对前沿探索的支持；LTX2管道则直接面向多模态生成应用，**加速技术落地**。
- **维护开源健康度**：通过文档修复、依赖更新和代码优化，**提升了项目的可靠性和社区协作效率**，符合Apache 2.0开源精神。

这些更新整体上**增强了diffusers在自编码器架构和多模态生成方面的能力**，同时保持了代码质量和用户体验，符合项目作为“最先进的扩散模型库”的长期愿景。

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
- **主要提交者**: Alison Shao, akhilg-nv, Mohammad Miadh Angkad

## AI分析总结

根据提供的仓库提交记录和README摘要（SGLang项目是一个专注于高效LLM推理的框架），以下是昨日更新的要点总结：

---

### 1. 主要更新类型
- **Bug修复**：修复了吞吐量指标计算、gRPC错误处理、参数名错误、图像编辑等多个问题。
- **性能优化**：调整了Triton内核的MOE填充大小，更新了注意力机制以包含SWA解码优化，提升了推理效率。
- **功能新增**：增加了对Ray actor调度器进程管理的支持、结构化JSON日志记录功能、AMD GPU的新测试项（Z-Image-Turbo、kv-cache-fp8等）。
- **代码/基础设施改进**：重构了NaN/越界检查逻辑、清理了调度指标、优化了CI流程（避免重复安装）、更新了代码所有者。
- **测试增强**：扩展了JIT KV缓存内核的测试覆盖，新增了AMD平台的夜间测试。

---

### 2. 关键变更点及其与项目整体方向的关系
- **性能优化**（如MOE填充调整、SWA解码优化）直接契合SGLang的核心目标——**提升LLM推理速度和吞吐量**。
- **多硬件支持**（新增AMD GPU测试）体现了项目向**多平台扩展**的趋势，增强框架的通用性和竞争力。
- **错误处理与日志改进**（gRPC状态码、JSON日志）提升了系统的**可靠性和可观测性**，对生产部署至关重要。
- **调度与进程管理**（Ray actor支持）加强了**分布式推理场景**的灵活性和资源管理能力。

---

### 3. 对项目的影响和潜在意义
- **用户体验**：更稳定的指标计算、更好的错误处理和日志功能，有助于开发者调试和监控推理任务。
- **性能提升**：内核级优化（如Triton、注意力机制）可能直接降低延迟、提高吞吐，尤其在MOE模型和长序列解码场景。
- **生态扩展**：对AMD GPU的持续测试支持，可能吸引更多硬件厂商和用户，降低使用门槛。
- **代码健康度**：重构和清理有助于长期维护，减少技术债务。

---

### 4. 值得关注的技术点
- **Triton内核优化**：针对MOE模型的填充策略调整，可能涉及内存对齐或计算效率改进。
- **SWA解码优化**：可能是一种新的注意力优化技术，用于加速自回归生成。
- **异步NaN/OOB检查**：通过环境变量控制检查逻辑，平衡了安全性与性能。
- **FP8量化支持**（AMD测试中提及）：低精度推理是当前LLM优化的重要方向。
- **Ray集成**：为分布式推理提供了更灵活的Actor模型支持。

---

### 5. 基于项目背景的提交影响分析
SGLang旨在成为**高效、可扩展的LLM推理框架**。昨日的更新整体强化了这一方向：
- **性能与效率**：多项内核优化和调度改进直接提升了推理性能，符合项目“高性能”定位。
- **可扩展性与兼容性**：新增AMD测试和Ray支持，体现了对多硬件、分布式场景的投入，有助于扩大用户基础。
- **稳定性与可维护性**：修复多个Bug、改进错误处理和日志，提升了生产环境可靠性，对框架的成熟度至关重要。
- **社区与协作**：更新CODEOWNERS、规范提交记录，反映了项目在规模化开发中的规范化努力。

---

**总结**：昨日的更新以**性能优化、多硬件支持、稳定性增强**为主线，紧密围绕SGLang作为高效LLM推理框架的核心目标，同时通过基础设施改进为长期发展奠定基础。这些变更进一步巩固了其在LLM推理领域的竞争力。

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
- **主要提交者**: Yanhong Li, Christian Munley, Andreas Karatzas

## AI分析总结

根据提供的提交记录和README摘要（vLLM项目旨在提供“简单、快速、经济的LLM服务”），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及模型推理、KV缓存、工具调用、工作流等多个核心模块。
- **功能新增/扩展**：新增模型支持、硬件后端扩展、API增强。
- **性能优化**：针对特定内核和内存分配进行优化。
- **文档与CI/CD**：文档构建逻辑、CI流程权限与稳定性、发布包管理。
- **代码质量与重构**：代码清理、类型修复、警告消除、模块重构。
- **硬件支持**：扩展对XPU和ROCm的适配。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **修复小KV缓存预热问题** (`#36176`) | 确保推理服务在极端配置下的**稳定性与可靠性**，是“可靠服务”的基础。 |
| **新增OLMo Hybrid模型支持** (`#32550`) | 扩展**模型生态**，让用户能服务更多样化的模型，符合“为所有人服务”的目标。 |
| **优化FusedMoE内核内存分配** (`#35794`) | 直接**提升MoE模型推理性能**，降低内存开销，强化“快速、经济”的核心优势。 |
| **启用XPU上的ModelRunnerV2** (`#36078`) | 扩大**硬件生态支持**，降低用户使用门槛，提升项目在异构计算环境中的适用性。 |
| **修复Qwen-Omni/VL等多模态模型问题** (`#35994`, `#36140`) | 完善对**多模态模型**的支持，这是当前LLM服务的重要前沿。 |
| **统一编译器配置、重构ROCm后端逻辑** (`#35810`, `#35246`) | 提升**后端统一性与可维护性**，为未来性能优化和扩展打下基础。 |
| **修复OpenAI API异常日志、KV加载等** (`#31164`, `#34616`) | 增强**API服务的健壮性**和**调度器正确性**，改善生产环境体验。 |

### 3. 对项目的影响和潜在意义
- **用户体验**：通过修复各类Bug（特别是多模态、工具调用、流式输出），直接提升了服务的稳定性和开发者体验。
- **性能与成本**：针对MoE和注意力后端的优化，有助于在高负载下维持高性能、低延迟，降低单位推理成本。
- **可扩展性**：对XPU的支持和ROCm后端重构，使项目能更好地拥抱多元化的硬件生态，避免锁定在单一平台上。
- **开发者生态**：完善文档、发布sdist包、规范CI流程，降低了贡献者和集成者的参与门槛。

### 4. 值得关注的技术点
- **MoE优化**：`FusedMoEModularKernel` 使用 `torch.empty` 优化输出张量，是底层内核级性能调优的体现。
- **硬件抽象化**：使用 `torch.accelerator.synchronize()` 替代 `torch.cuda.synchronize()`，是向更通用硬件抽象层迈进的一步。
- **编译部署**：关注编译器配置的一致性，对模型导出和部署的稳定性至关重要。
- **多模态服务**：对Qwen-Omni、Qwen-VL等模型问题的修复，反映了项目在复杂多模态输入处理上的持续投入。

### 5. 基于项目背景的提交影响分析
vLLM的目标是成为**普及化的高性能LLM服务引擎**。昨日的提交集合完美地服务于这一目标：
- **巩固核心**：大量Bug修复和性能优化确保了推理引擎的**坚固高效**，这是“快”和“便宜”的基石。
- **扩大边界**：通过支持新模型（OLMo）、新硬件（XPU）、完善多模态和API，**拓展了适用场景和用户群体**，向“为所有人”迈进。
- **夯实基础**：代码重构、文档和CI的改进，提升了项目的**长期可维护性和协作效率**，有助于社区健康发展。

**总结**：这是一次非常均衡的更新，既没有忽略对核心推理路径的“打磨”，也积极向新的模型、硬件和模态“探索”，同时持续改善开发体验，全方位支撑着vLLM作为行业领先LLM服务引擎的定位。

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
- **主要提交者**: Jack Lee, WeiQing Chen, Yueqian Lin

## AI分析总结

根据 `vllm-omni` 仓库的 README 摘要（“为所有人提供简单、快速、经济的全模态模型服务”）和昨日的提交记录，以下是分析总结：

### 1. 主要更新类型
- **功能新增**：支持 Qwen3-TTS 灵活任务类型配置 (#1197)；支持 LTX-2 文本/图像到视频模型 (#841)。
- **Bug修复**：修复全静音 TTS 输出 (#1664)；修复 `create_speech` 的 HTTP 状态码返回 (#1687)；修复 LongCat 序列并行问题 (#1631)。
- **性能优化**：减少 Qwen3-TTS 的首次音频生成时间 (#1583)；优化 Qwen3-Omni 的异步分块延迟 (#1656)。
- **文档更新**：新增测试指南文档 (#1376)。
- **重构/清理**：将 CosyVoice3 测试移至模型子目录 (#1666)；移除 `logits_processor_pattern` 字段 (#1675)。
- **用户体验**：为扩散模型添加进度条 (#1652)。
- **CI/测试调整**：临时移除高并发测试 (#1683)。

### 2. 关键变更点及其与项目整体方向的关系
- **全模态支持扩展**：新增对 **LTX-2（文本/图像到视频）** 模型的支持，直接强化了项目的“全模态”核心定位，从语音、文本扩展到视频生成。
- **TTS 功能增强与优化**：针对 **Qwen3-TTS** 的多项改进（灵活配置、减少延迟），提升了语音合成这一重要模态的易用性和响应速度，符合“快速、经济”的目标。
- **稳定性和可靠性提升**：修复了 TTS 静音输出、HTTP 状态码、序列并行等关键 Bug，增强了服务端的鲁棒性和用户体验，是“为所有人提供...服务”的基础保障。
- **开发者体验优化**：新增测试指南、清理代码结构、优化 CI，有助于降低贡献门槛和维护成本，支持项目生态的健康发展。

### 3. 对项目的影响和潜在意义
- **功能矩阵更加完善**：视频生成能力的加入，使 vllm-omni 在“文本、图像、语音、视频”的全模态服务拼图上更进一步。
- **生产就绪度提高**：针对 TTS 和 HTTP API 的修复与优化，直接提升了核心服务的稳定性和专业性，有利于生产环境部署。
- **性能基准提升**：减少 TTFA（首次音频生成时间）和网络延迟的优化，直接兑现了“快速”的承诺，改善了终端用户感知。
- **社区与协作**：清晰的测试文档和代码清理，有利于吸引和引导更多开发者参与项目。

### 4. 值得关注的技术点
- **灵活的任务类型配置**：允许 Qwen3-TTS 模型在运行时动态适应不同任务，提高了模型的灵活性和适用范围。
- **异步分块延迟优化**：针对流式传输场景的网络层优化，对实时音频/视频服务至关重要。
- **Float32 用于语音分词器解码**：一个具体的 Bug 修复点，揭示了在低精度计算中保持语音质量的关键细节。
- **LongCat 序列并行修复**：涉及大规模模型推理中的分布式计算优化，对支持长序列和大型模型有重要意义。

### 5. 基于项目背景的提交影响分析
vllm-omni 的目标是成为**统一、高效的全模态模型服务平台**。昨日的提交集体推动了这一愿景：
- **广度上**：通过集成 **LTX-2 视频模型**，直接扩展了所支持的模态范围，向真正的“Omni”（全能）迈进。
- **深度上**：对已有核心模态（如 **Qwen3-TTS**）进行**功能增强、性能优化和稳定性修复**，深耕了语音赛道的用户体验和技术成熟度。
- **基石上**：通过**修复关键 Bug、优化代码结构、完善文档**，夯实了项目的基础设施和开发者体验，这是项目能够持续、稳定发展的关键。

**总结**：昨日的更新是一次典型的“**扩疆域、深耕耘、固根基**”的组合拳。它不仅增加了新的视频生成能力，还显著提升了核心语音服务的质量和性能，同时通过一系列修复和优化确保了平台的稳定性和可维护性。这些变化紧密围绕项目“简单、快速、经济的全模态服务”的使命，使其在功能完整性和技术可靠性上都得到了加强。

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
