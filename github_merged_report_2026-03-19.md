# GitHub Stars 合并报告 - 2026-03-19

**合并日期**: 2026-03-20
**监控日期**: 2026-03-19
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


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1740
- **最后更新**: 2026-03-19T17:42:56Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: 鐘天楽

## AI分析总结

根据提供的README摘要和提交记录，以下是针对VeOmni项目昨日更新的分析总结：

### 1. 主要更新类型
- **性能优化**：本次提交的核心是引入了一个融合的Triton内核，用于优化MoE（混合专家）模型的负载均衡损失计算。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：新增了针对MoE负载均衡损失的融合Triton内核实现（`fused Triton kernel for MoE load balancing loss`）。
- **与项目方向的关系**：VeOmni旨在为“任意模态模型训练”提供模型中心的分布式配方库。MoE是当前大规模多模态模型中的关键技术之一，用于高效扩展模型容量。本次优化直接提升了MoE训练核心组件的计算效率，与项目“**Scaling Any Modality Model Training**”（扩展任意模态模型训练）的核心目标高度一致，通过底层性能优化支持更大规模、更高效的模型训练。

### 3. 对项目的影响和潜在意义
- **直接影响**：预计将显著减少MoE模型在训练过程中计算负载均衡损失的开销，从而提升整体训练速度。
- **潜在意义**：
    - **降低训练成本**：更高的计算效率意味着在相同硬件资源下可以完成更多训练或降低训练时间，直接关联训练成本。
    - **提升项目竞争力**：在底层高性能计算（HPC）层面的持续优化，增强了VeOmni作为分布式训练配方库的技术深度和实用性。
    - **示范作用**：为社区贡献了一个针对特定难点（MoE负载均衡）的高性能实现方案，体现了项目在优化“配方”上的价值。

### 4. 值得关注的技术点
- **使用Triton**：Triton是开源的GPU编程语言和编译器，常用于编写高效的CUDA内核替代方案。选择Triton表明项目团队注重利用现代、灵活的高性能计算工具来获得最佳性能。
- **内核融合**：将多个计算步骤融合到一个内核中，是GPU优化中减少内存带宽瓶颈、提升计算密度的关键技术。
- **聚焦MoE负载均衡**：负载均衡是MoE模型训练中的关键挑战，确保专家被均衡使用。专门优化此损失函数，抓住了MoE训练的一个性能痛点。

### 5. 基于项目背景的提交影响分析
- **强化“配方库”定位**：README强调VeOmni是一个“**Model-Centric Distributed Recipe Zoo**”（以模型为中心的分布式配方库）。本次提交并非简单修复bug或增加功能，而是提供了一个**经过深度优化的、可复用的高性能计算“配方”**。这完美契合了项目作为优质“配方”集合体的根本定位。
- **支持“Scaling”目标**：项目目标中的“Scaling”不仅指模型规模，也指训练效率。此类底层内核优化是支撑高效扩展（Efficient Scaling）不可或缺的基础建设。
- **吸引专业开发者**：持续发布此类高性能优化代码，有助于吸引关注分布式训练和模型性能优化的研究人员和工程师，提升项目在专业社区的影响力。

**总结**：昨日更新是一个典型的**深度性能优化提交**，它通过引入先进的Triton融合内核，精准提升了MoE这一关键模型架构的训练效率。这直接强化了VeOmni项目作为**高性能分布式训练配方库**的核心价值，为其支持大规模多模态模型训练的目标提供了更坚实的技术基础。

## 详细提交记录

### [46f2ac6](https://github.com/ByteDance-Seed/VeOmni/commit/46f2ac6d73efb8d77f8d88d197905d86cace6066)

- **作者**: 鐘天楽
- **时间**: 2026-03-19T17:09:03Z
- **提交信息**: [ops] feat: fused Triton kernel for MoE load balancing loss (#560)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2084
- **最后更新**: 2026-03-19T22:28:22Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: ziyanxzy

## AI分析总结

根据提供的 README 摘要和提交记录，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：支持 Intel PTL（可能指 PyTorch Lightning 或相关优化库）中的 **offloading（卸载）** 和 **feature caching（特征缓存）** 功能。
- **性能优化**：通过 offloading 和 caching 技术，旨在提升推理效率或降低资源占用。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：在 `wan 2.1`（可能指特定硬件或框架版本）中引入了 offloading 和 feature caching 支持。
- **与项目方向的关系**：LightX2V 定位为 **轻量级视频生成推理框架**，核心目标是高效、快速的视频生成。本次更新通过 **优化内存/计算资源管理**（offloading 将部分计算移至外部设备，caching 避免重复计算），直接强化了框架的 **轻量化与高性能** 特性，符合项目“⚡️ Light”的设计宗旨。

### 3. 对项目的影响和潜在意义
- **正面影响**：
  - **提升推理速度**：特征缓存可减少重复计算，加速生成流程。
  - **降低内存压力**：offloading 有助于在资源受限环境下运行更大模型或处理更高分辨率视频。
  - **扩展硬件兼容性**：针对 Intel 平台优化，可能提升在 Intel 硬件上的部署效率。
- **潜在意义**：为后续支持更复杂模型或实时视频生成场景奠定基础，同时吸引更多关注性能优化的开发者。

### 4. 值得关注的技术点
- **Offloading 机制**：如何将计算任务动态分配到不同设备（如 CPU 与 GPU 之间），以平衡负载和内存使用。
- **Feature Caching 策略**：缓存哪些特征、缓存粒度及失效策略，直接影响性能增益。
- **WAN 2.1 集成**：可能指特定硬件加速库或分布式训练/推理框架，需关注其与 PyTorch 生态的整合方式。

### 5. 基于项目背景的提交影响分析
- **背景回顾**：LightX2V 旨在提供 **轻量、高效** 的视频生成推理方案，强调低延迟、易部署。
- **发展影响**：
  - **强化核心优势**：通过资源优化技术，进一步凸显“轻量”与“高速”的框架定位。
  - **拓宽应用场景**：降低硬件门槛，使框架更适用于边缘设备或资源受限环境。
  - **生态建设**：针对 Intel 平台的优化可能吸引硬件厂商合作，促进框架在更多生产环境中的落地。

**总结**：本次更新是一次 **针对性强的性能优化**，通过引入 offloading 和 caching 机制，直接提升了框架的推理效率和资源利用率，紧密契合 LightX2V 作为轻量级视频生成框架的发展目标。

## 详细提交记录

### [0ad1d63](https://github.com/ModelTC/LightX2V/commit/0ad1d639358cfe8300d352cb7fa6aeb4e7cbbf48)

- **作者**: ziyanxzy
- **时间**: 2026-03-19T08:03:26Z
- **提交信息**: offloading and feature caching (#949)

support wan 2.1 in intel ptl feature： offloading and feature caching.

---------

Co-authored-by: helloyongyang <yongyang1030@163.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1967
- **最后更新**: 2026-03-19T11:05:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5182
- **最后更新**: 2026-03-19T21:20:34Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: danisereb, yanqinz2, Ka-Hyun Nam

## AI分析总结

根据FlashInfer仓库的README摘要（专注于“高性能GPU推理内核”）及昨日提交记录，以下是分析总结：

### 1. 主要更新类型
- **功能新增**：新增对TRTLLM MXFP8非门控MoE（带ReLU2激活）的支持；为cuDNN后端GEMM操作添加了override shape支持。
- **Bug修复**：修复了CUTLASS TMA描述符在特定硬件（如DGX Spark）上的崩溃问题；修复了VariableBlockSparseAttention中kv_lens_buffer的缓冲区溢出问题。
- **重构/优化**：清理并优化了Cute DSL NVFP4 MoE的实现；升级了CUTLASS依赖版本（4.2.1→4.4.2）；将PDL（预取依赖启动）从环境变量改为运行时参数。
- **工程/维护**：更新了代码所有权配置以解决团队权限问题。

### 2. 关键变更点及其与项目整体方向的关系
- **MoE（混合专家）内核增强**：新增MXFP8支持、优化NVFP4实现，并统一API设计（如PDL参数化）。这直接服务于项目“高性能GPU推理内核”的核心目标，扩展了对新兴模型（如Nemotron）和量化格式的支持。
- **硬件兼容性与稳定性**：修复SM120/SM121架构上的崩溃问题，澄清对Blackwell（SM100系列）的支持范围。确保项目在最新GPU架构（如NVIDIA Blackwell）上的可靠运行，这对保持高性能推理的领先地位至关重要。
- **运行时灵活性**：为cuDNN GEMM引入override shape支持，允许单一缓存图处理动态输入维度，减少了图重建开销。这提升了推理部署的效率和适应性。
- **底层依赖更新**：升级CUTLASS至4.4.2版本，可能带来了性能改进或新特性，保持与行业标准库的同步。

### 3. 对项目的影响和潜在意义
- **提升模型支持范围**：新增MXFP8 MoE支持，使FlashInfer能够更好地服务使用Nemotron等模型的推理场景，增强生态竞争力。
- **提高稳定性和可扩展性**：修复缓冲区溢出和硬件兼容性问题，降低了生产环境崩溃风险；动态缓冲区调整和override shape支持增强了处理大规模、可变输入的能力。
- **优化开发者体验**：API设计统一（如PDL参数化）、依赖更新和内部清理，使代码库更易于维护和扩展。
- **潜在性能收益**：CUTLASS升级和MoE策略调整可能带来内核性能提升，但需进一步基准测试验证。

### 4. 值得关注的技术点
- **MXFP8量化支持**：针对Nemotron模型的非门控MoE，扩展了FP8量化家族，反映了对新兴模型格式的快速适配。
- **Cute DSL优化**：对NVFP4 MoE的清理和策略调整，展示了对专用内核DSL的深度优化，可能影响未来内核设计模式。
- **cuDNN override shape**：允许GEMM图缓存复用，显著减少动态形状场景下的开销，适用于可变序列长度推理。
- **硬件架构明确**：澄清SM110不支持、SM100系列（Blackwell）支持，凸显项目对最新GPU架构的针对性优化。

### 5. 基于项目背景的提交影响分析
FlashInfer旨在提供**高性能GPU推理内核**，专注于效率、低延迟和广泛硬件支持。昨日的提交：
- **强化核心优势**：通过MoE扩展、量化支持和运行时优化，直接提升了内核的性能和功能覆盖，巩固了其在推理加速领域的竞争力。
- **确保生产就绪**：修复关键Bug（如缓冲区溢出、硬件崩溃）和升级依赖，增强了库的稳定性和可靠性，适用于大规模部署。
- **拥抱生态演进**：支持新模型（Nemotron）、新硬件（Blackwell）和新量化格式（MXFP8），显示项目紧跟AI推理技术趋势，保持相关性。
- **优化开发流程**：内部重构和工程改进，有助于长期维护和社区协作，支撑项目持续迭代。

**总结**：昨日更新以功能扩展和稳定性修复为主，紧密围绕项目的高性能推理使命，提升了代码质量、硬件兼容性和模型支持范围，为应对更复杂的推理场景奠定了基础。

## 详细提交记录

### [6f0928c](https://github.com/flashinfer-ai/flashinfer/commit/6f0928c17cdbc49444c60344825c2a025298a614)

- **作者**: nv-yunzheq
- **时间**: 2026-03-19T21:20:26Z
- **提交信息**: chore: cute dsl nvfp4 moe clean up (#2775)

<!-- .github/pull_request_template.md -->

## 📌 Description

This is to clean up cute dsl nvfp4 moe
1. Remove incorrect statement in code that sm110 is supported
2. Add cute dsl moe to benchmark script
3. Adjust autouning strategy and tactics. And use unit test to test all
tactics
4. Remove unused blockscaled fp4 grouped gemm in moe
5. Make pdl as a function parameter instead of environment variable to
align with the rest of library
6. Add CC support decorator to cute dsl moe function

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

* **New Features**
* Added CuteDSL FP4 block-scaled MoE variant with benchmark entries and
end-to-end test path
* Made PDL (prefetch-dependent launch) configurable via runtime
parameter across MoE APIs

* **Bug Fixes**
  * Disabled problematic tile-size 256 tactic
  * Clarified supported Blackwell architectures (SM100 family)

* **Refactor**
* Simplified MoE tactic selection to runtime validation and
deterministic tactic shapes
  * Replaced environment-based PDL flag with a runtime parameter

* **Tests**
* Added comprehensive MoE tactic validation tests and benchmark samples
(note: some entries duplicated)
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9276e44](https://github.com/flashinfer-ai/flashinfer/commit/9276e441898789e3ff21c397ca942103bf76cb12)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-03-19T17:59:18Z
- **提交信息**: Upgrade cutlass 4.2.1 -> 4.4.2 (#2798)

<!-- .github/pull_request_template.md -->

## 📌 Description

Upgrade cutlass 4.2.1 -> 4.4.1, also add "CUTLASS_ENABLE_GDC_" to
cutlass compilation flags.

Addresses this issue raised on slack: "Hi team, we're seeing CUTLASS TMA
descriptor crashes on DGX Spark ... the crash happens in
tma_warp_specialized_generic_moe_gemm_kernelLauncher<Sm120, fp4> from
fused_moe_120.so."

## 🔍 Related Issues

[[Bug] NVFP4 MoE models crash on GB10 (SM121) during CUDA graph capture
#2776](https://github.com/flashinfer-ai/flashinfer/issues/2776)](https://github.com/flashinfer-ai/flashinfer/issues/2776)

[[Bug] NVFP4 mm_fp4 GEMM broken on SM120 (RTX PRO 6000 Blackwell) - all
backends fail
#2577](https://github.com/flashinfer-ai/flashinfer/issues/2577)

https://github.com/flashinfer-ai/flashinfer/pull/2716/changes 


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
  * Updated CUTLASS subproject dependency to latest version.
* Applied internal namespace qualification adjustments for improved code
consistency.
  * Refined template parameter handling in extension modules.

No functional changes or end-user impacts.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d226a82](https://github.com/flashinfer-ai/flashinfer/commit/d226a82ee27252d4976d4e9bc3a87278a073d22a)

- **作者**: danisereb
- **时间**: 2026-03-19T17:49:43Z
- **提交信息**: feat: Add support for TRTLLM MXFP8 non-gated MoE with ReLU2 (#2707)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

This PR adds support for TRTLLM MXFP8 **non-gated MoE with ReLU2** (for
Nemotron models).

A PR for TRTLLM MXFP8 **gated** MoE is open in vLLM:
https://github.com/vllm-project/vllm/pull/35986

After this PR is merged and a new flashinfer version is released -
support for non-gated MoE will be added in vLLM.

New tests were added and all tests passed:
```
pytest tests/moe/test_trtllm_gen_fused_moe.py -k "mxfp8 and relu"
```

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
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Routed FP8 block-scale MoE execution path
  * New MXFP8 block-scale FP8 quantization mode

* **Enhancements**
* Activation-type now flows through MoE entry points enabling gated vs
non-gated behavior (affects valid config gating)
  * Dynamic top-k limits for DeepSeek routing based on expert count
  * Stricter weight/activation shape validation and clearer errors

* **Tests**
* New parity, routed, autotune, and smoke tests covering FP8/MXFP8 and
activation types
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [623db38](https://github.com/flashinfer-ai/flashinfer/commit/623db385bad4f49b364153f50a5df0547d34bcbf)

- **作者**: yanqinz2
- **时间**: 2026-03-19T15:56:38Z
- **提交信息**: Implement override shape support for cuDNN GEMM operations (#2790)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add override shape support for cudnn backend with test examples.

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
- [ ] All tests are passing (`unittest`, etc.).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* cuDNN override-shape support for GEMM so a single cached graph can
handle multiple M dimensions at runtime without rebuilds.
* Extended support to BF16, FP4 (NVFP4), MXFP8 and per-tensor FP8 data
types.
* Added a runtime availability check to safely gate override-shape usage
on unsupported backends.

* **Tests**
* Added end-to-end tests validating override-shape GEMM across supported
data types and dynamic M scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yanqin Zhai <yanqinz@nvidia.com>

### [8632015](https://github.com/flashinfer-ai/flashinfer/commit/8632015be0e581084f2ea1dc493cffadc8d3acd7)

- **作者**: Alex Yang
- **时间**: 2026-03-19T13:20:33Z
- **提交信息**: fix: Workaround org teams perm issue for approval purposes (#2816)

<!-- .github/pull_request_template.md -->

## 📌 Description

Workaround org teams perm issue for approval purposes

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/pull/2815

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

* **Chores**
* Updated code ownership configuration with new organizational structure
and guidelines.
  * Updated continuous integration workflow configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c4a159a](https://github.com/flashinfer-ai/flashinfer/commit/c4a159a8d3fa286b3b0076d2ee224ac96a136c11)

- **作者**: qsang-nv
- **时间**: 2026-03-19T09:08:03Z
- **提交信息**: [fix] Bugfix 1367: fix VariableBlockSparseAttention buffer overflow by dynamically resizing kv_lens_buffer (#2802)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
This PR fixes https://github.com/flashinfer-ai/flashinfer/issues/1367.

_kv_lens_buffer is statically allocated with a hardcoded size of 32768
in __init__. When len(kv_lens_arr_host) exceeds this limit (e.g.,
num_kv_heads * num_blocks_per_row = 48 * 768 = 36864 for variable block
sparse attention), the copy_() call in plan() raises a RuntimeError due
to shape mismatch.

The fix dynamically resizes _kv_lens_buffer in plan() when the required
size exceeds the current buffer capacity. The initial allocation of
32768 is preserved to avoid unnecessary reallocation for common cases.
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

* **Bug Fixes**
* Fixed potential buffer overflow in key-value length handling across
decode, prefill, and sparse attention operations. The system now
dynamically resizes internal buffers to safely accommodate
variable-length data without overflow errors, improving robustness when
processing larger sequences.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Qidi Sang <200703406+qsang-nv@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3244
- **最后更新**: 2026-03-19T22:25:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33103
- **最后更新**: 2026-03-19T21:58:40Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: dg845

## AI分析总结

根据提供的README摘要（HuggingFace Diffusers库）和提交记录，以下是对昨日更新的分析总结：

### 1. **主要更新类型**
- **功能新增**：核心更新是为**LTX-2.3模型系列**添加全面支持，包括新的注意力处理器、视频上采样模块、音频编解码器等。
- **Bug修复**：修复了LTX-2.3模型在推理过程中的多个问题（如DiT块前向传播、配置错误导致的像素抖动等）。
- **代码重构**：优化了文本连接器的归一化逻辑、视频VAE上采样器初始化等结构。
- **测试适配**：调整代码确保现有测试（如`test_components_function`）通过。

### 2. **关键变更点及其与项目方向的关系**
- **新增LTX-2.3模型支持**：包括DiT块、视频VAE、音频Vocoder、文本连接器等核心组件，**扩展了Diffusers对前沿视频生成模型的支持范围**。
- **引入新机制**：如扰动注意力处理器、跨时间步调制、空间潜在上采样器等，**增强了模型对多模态（视频、音频、文本）生成的控制能力**。
- **与项目方向一致性**：Diffusers旨在提供先进的扩散模型实现，本次更新**紧跟LTX-2.3（可能为大型视频生成模型）的最新进展**，强化了其在生成式AI领域的竞争力。

### 3. **对项目的影响和潜在意义**
- **功能扩展**：用户可直接在Diffusers中使用LTX-2.3进行视频生成、图像到视频等任务，**降低了使用最新模型的技术门槛**。
- **生态整合**：通过添加配置转换脚本，**促进了第三方模型（如LTX-2.3）与HuggingFace生态的集成**。
- **开发者体验**：修复的Bug和重构提高了代码稳定性，**为后续模型迭代奠定基础**。

### 4. **值得关注的技术点**
- **扰动注意力处理器**：可能用于提升生成质量或效率的新注意力机制。
- **带宽扩展音频编解码器**：针对音频生成的改进，可能提升音视频同步质量。
- **多模态特征提取器**：支持不同模态（文本、视频、音频）的特征统一处理。
- **引导缩放策略**：在采样空间（x0）进行引导调整，可能改善生成可控性。

### 5. **基于项目背景的提交影响分析**
- **背景关联**：Diffusers作为开源扩散模型库，核心目标是**集成最先进的生成模型**。LTX-2.3作为新兴视频生成模型，其加入**直接丰富了库的模型多样性**。
- **发展影响**：
  - **技术前沿性**：通过快速集成LTX-2.3，Diffusers保持了在**多模态生成领域的领先地位**。
  - **社区贡献**：更新包含大量社区协作（如Co-authored-by），体现了**开源协作的高效性**。
  - **应用扩展**：支持视频上采样、音频生成等细分功能，**拓宽了库在影视、创意工具等场景的应用潜力**。

---
**总结**：本次更新是Diffusers对LTX-2.3模型系列的一次**大规模功能集成**，不仅新增了多项先进生成技术，还通过修复和重构提升了代码质量。这强化了Diffusers作为**多模态扩散模型核心库**的地位，并加速了前沿研究成果向实践应用的转化。

## 详细提交记录

### [072d15e](https://github.com/huggingface/diffusers/commit/072d15ee4289ffdc3aa9d65f8b94bc9271319d21)

- **作者**: dg845
- **时间**: 2026-03-19T21:58:29Z
- **提交信息**: Add Support for LTX-2.3 Models (#13217)

* Initial implementation of perturbed attn processor for LTX 2.3

* Update DiT block for LTX 2.3 + add self_attention_mask

* Add flag to control using perturbed attn processor for now

* Add support for new video upsampling blocks used by LTX-2.3

* Support LTX-2.3 Big-VGAN V2-style vocoder

* Initial implementation of LTX-2.3 vocoder with bandwidth extender

* Initial support for LTX-2.3 per-modality feature extractor

* Refactor so that text connectors own all text encoder hidden_states normalization logic

* Fix some bugs for inference

* Fix LTX-2.X DiT block forward pass

* Support prompt timestep embeds and prompt cross attn modulation

* Add LTX-2.3 configs to conversion script

* Support converting LTX-2.3 DiT checkpoints

* Support converting LTX-2.3 Video VAE checkpoints

* Support converting LTX-2.3 Vocoder with bandwidth extender

* Support converting LTX-2.3 text connectors

* Don't convert any upsamplers for now

* Support self attention mask for LTX2Pipeline

* Fix some inference bugs

* Support self attn mask and sigmas for LTX-2.3 I2V, Cond pipelines

* Support STG and modality isolation guidance for LTX-2.3

* make style and make quality

* Make audio guidance values default to video values by default

* Update to LTX-2.3 style guidance rescaling

* Support cross timesteps for LTX-2.3 cross attention modulation

* Fix RMS norm bug for LTX-2.3 text connectors

* Perform guidance rescale in sample (x0) space following original code

* Support LTX-2.3 Latent Spatial Upsampler model

* Support LTX-2.3 distilled LoRA

* Support LTX-2.3 Distilled checkpoint

* Support LTX-2.3 prompt enhancement

* Make LTX-2.X processor non-required so that tests pass

* Fix test_components_function tests for LTX2 T2V and I2V

* Fix LTX-2.3 Video VAE configuration bug causing pixel jitter

* Apply suggestions from code review

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* Refactor LTX-2.X Video VAE upsampler block init logic

* Refactor LTX-2.X guidance rescaling to use rescale_noise_cfg

* Use generator initial seed to control prompt enhancement if available

* Remove self attention mask logic as it is not used in any current pipelines

* Commit fixes suggested by claude code (guidance in sample (x0) space, denormalize after timestep conditioning)

* Use constant shift following original code

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 388
- **最后更新**: 2026-03-19T15:54:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12033
- **最后更新**: 2026-03-19T22:29:34Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24762
- **最后更新**: 2026-03-19T23:03:54Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 15
- **主要提交者**: Shangming Cai, kk, Mohammad Miadh Angkad

## AI分析总结

根据 `sgl-project/sglang` 仓库的 README（摘要显示这是一个专注于高效语言模型推理和服务的项目，拥有自己的 logo 和活跃的社区指标）以及提供的昨日提交记录，以下是分析总结：

### 1. 主要更新类型
- **Bug修复**：占主导，涉及内存泄漏、GPU故障、多节点调度、日志过滤等核心稳定性问题。
- **功能新增/增强**：支持新的量化后端（`mm_fp4`）、增强特定模型（Kimi）的函数调用与推理检测、扩展CPU推理的批处理支持、新增专家专业化GEMM内核支持。
- **性能优化与重构**：简化服务器启动输出、优化CI测试流程和调度。
- **CI/CD与测试**：大量提交针对AMD平台CI的修复、测试调整和稳定性提升。
- **用户体验（UX）**：抑制无关的日志噪音。

### 2. 关键变更点及其与项目整体方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **修复Token泄漏与GPU故障** (`63c38ab`, `c8f0122`) | 直接关乎**推理服务的核心稳定性与可靠性**，是生产级服务的基础。 |
| **支持 `mm_fp4` 量化后端** (`b42b9f6`) | 符合项目**追求高效推理**的目标，通过更先进的量化技术降低显存占用、提升吞吐。 |
| **增强Kimi模型功能调用** (`c562e0d`) | 体现对**具体模型生态和高级应用场景**（如Agent、复杂推理）的支持深度。 |
| **修复多节点RayEngine调度** (`319bb49`) | 强化**分布式推理能力**，对大规模部署至关重要。 |
| **大量AMD CI修复与测试** (`2ee7f41`, `9e629d3`等) | 表明项目正**积极扩大硬件生态支持**，确保在AMD平台上的稳定性和兼容性。 |
| **简化输出、抑制噪音日志** (`0949b13`, `29ced9c`) | 提升**开发者与运维体验**，使系统更易监控和调试。 |

### 3. 对项目的影响和潜在意义
- **稳定性显著提升**：集中修复了从内存管理、GPU执行到分布式协调等多个层面的关键缺陷，降低了生产环境风险。
- **功能边界扩展**：新增的量化后端和模型特性支持，增强了框架的**技术先进性和应用范围**。
- **硬件生态巩固**：对AMD平台的持续投入，有助于吸引更广泛的用户和部署环境，**降低用户硬件锁定的顾虑**。
- **开发运维效率优化**：CI流程的改进和日志优化，提升了团队内部迭代效率和系统的可维护性。

### 4. 值得关注的技术点
- **`mm_fp4` 量化后端**：可能是一种新的4位浮点量化方案，用于在保持精度的同时极致压缩模型，是推理优化的前沿。
- **专家专业化Grouped GEMM** (`cb8105f`)：针对MoE（混合专家）模型的核心计算内核优化，能大幅提升此类先进架构的推理效率。
- **多节点Rank0调度与CUDA设备设置修复** (`319bb49`)：涉及分布式系统中最复杂的协同问题，解决方案对构建健壮的分布式服务有参考价值。
- **CPU推理批处理扩展** (`274581f`)：即使在专注GPU的项目中，优化CPU后备路径也能扩大适用场景。

### 5. 基于项目背景的提交影响分析
SGLang项目定位为**高性能语言模型服务与推理引擎**。昨日的提交整体上强烈呼应了这一目标：
- **夯实基础**：绝大多数Bug修复都在加固推理服务的**核心引擎**，确保其作为基础设施的稳定与高效，这是项目生存和发展的根本。
- **追求极致效率**：通过支持新的量化格式（`mm_fp4`）和优化核心计算内核（专家GEMM），项目在**性能前沿**持续探索，以保持技术竞争力。
- **拥抱开放生态**：积极修复AMD平台CI并增强对Kimi等模型的支持，表明项目不局限于单一硬件或模型，而是致力于构建一个**开放、兼容的推理生态系统**，这有利于社区的壮大和技术的普及。
- **提升开发者体验**：简化输出和日志管理，降低了使用和贡献门槛，有助于**促进社区活跃度和项目采用率**。

**总结**：昨日的更新是一次以**稳定性加固和硬件生态拓展**为核心，同时不忘**前沿性能优化和用户体验提升**的综合性迭代。这反映出SGLang项目正处于一个**从功能完善向生产稳定和生态繁荣迈进**的关键阶段。

## 详细提交记录

### [63c38ab](https://github.com/sgl-project/sglang/commit/63c38aba5edb26da3452914c898d4b039d51da68)

- **作者**: Leon Gao
- **时间**: 2026-03-19T22:37:27Z
- **提交信息**: Fix token leak with logprob_start_len=0 in streaming sessions (#20557)

### [62361e8](https://github.com/sgl-project/sglang/commit/62361e8fd5a82819ca1edda34377e69225cf0880)

- **作者**: Kangyan-Zhou
- **时间**: 2026-03-19T21:48:10Z
- **提交信息**: Temporarily adjust the scheulde for pr-test.yml to 12 hours (#20951)

### [b42b9f6](https://github.com/sgl-project/sglang/commit/b42b9f6e1a1ec91562dd5a5255a1ebf8fd279350)

- **作者**: Brayden Zhong
- **时间**: 2026-03-19T21:20:01Z
- **提交信息**: Support CuteDSL `mm_fp4` backend (#18801)

### [d8ece7f](https://github.com/sgl-project/sglang/commit/d8ece7fb22a63f9595ca3b162fe31974bfa5999a)

- **作者**: Yuwei An
- **时间**: 2026-03-19T20:20:49Z
- **提交信息**: [Tiny Fix] Filter lru related warning with pcg (#20940)

Signed-off-by: yuweia <ayw.sirius19@gmail.com>

### [0949b13](https://github.com/sgl-project/sglang/commit/0949b138af5b5cf7e3147dc1bab16f8f37937123)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-19T20:11:37Z
- **提交信息**: Simplify server startup output (#20885)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [a02cff7](https://github.com/sgl-project/sglang/commit/a02cff7f2b613e49cb4bc9f5b6641d23fbb5166f)

- **作者**: Xinyuan Tong
- **时间**: 2026-03-19T20:00:51Z
- **提交信息**: [Fix] Patch is_flash_attn_2_available for flash-attn-4 in VLM input format test (#20946)

### [c562e0d](https://github.com/sgl-project/sglang/commit/c562e0d13ba9c1513122ed583fabede207d8813a)

- **作者**: AlfredYong
- **时间**: 2026-03-19T19:57:57Z
- **提交信息**: [feat] Enhance Kimi-K2/K2.5 function call and reasoning detection (#19552)

Co-authored-by: alfredyyang <alfredyyang@tencent.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [2ee7f41](https://github.com/sgl-project/sglang/commit/2ee7f41e25521bec5c70e368519ef88e39ab6222)

- **作者**: billishyahao
- **时间**: 2026-03-19T18:52:25Z
- **提交信息**: [AMD] add mori ep normal tbo unittest (#20941)

### [9e629d3](https://github.com/sgl-project/sglang/commit/9e629d31fd93f7c4cf0fbee4632f150c8ba62c4b)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-03-19T18:50:19Z
- **提交信息**: [AMD] CI - Fix AMD CI (multimodal test, move flaky test to non-deterministic group) (#20815)

### [3b89c6d](https://github.com/sgl-project/sglang/commit/3b89c6d3eab976f4b61564f250e0dbceb0a97317)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-19T18:01:06Z
- **提交信息**: simplify and improve `pr-test.yml` (#20911)

### [29ced9c](https://github.com/sgl-project/sglang/commit/29ced9c162575459f50109f3e6fffb3b344d0982)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-03-19T17:58:41Z
- **提交信息**: [UX] Suppress noisy `httpx`/`httpcore` INFO logs (#20944)

### [319bb49](https://github.com/sgl-project/sglang/commit/319bb4974c0d2841f5b6b2b22f400516b847a3c9)

- **作者**: Xinyu Zhang
- **时间**: 2026-03-19T17:27:16Z
- **提交信息**: [Fix] RayEngine multi-node: co-locate rank0 scheduler with Engine and fix CUDA device setting (#20722)

### [274581f](https://github.com/sgl-project/sglang/commit/274581fb776fefcc9f2175cc1a6e1d39c074a478)

- **作者**: Cao E
- **时间**: 2026-03-19T16:50:56Z
- **提交信息**: Add support for more batch sizes in cpu_graph_runner (#13881)

### [4c52b7f](https://github.com/sgl-project/sglang/commit/4c52b7fcc694ebcbc9db5039759e30a73c7d5498)

- **作者**: Shangming Cai
- **时间**: 2026-03-19T11:12:50Z
- **提交信息**: [CI] Improve PP consistency check success rate (#20838)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [671bd26](https://github.com/sgl-project/sglang/commit/671bd266c18909d5fa97e4ce76bd1286e5b6dcf9)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-03-19T10:10:17Z
- **提交信息**: [AMD] CI - update amd nightly cronjob (#20928)

Co-authored-by: Bingxu Chen <bingxche@amd.com>

### [c8f0122](https://github.com/sgl-project/sglang/commit/c8f0122acf481e8712491dcd6aebc0bd97df430c)

- **作者**: kk
- **时间**: 2026-03-19T09:36:12Z
- **提交信息**: Fix gpu-fault issue when run deepseek-r1 and enable dp (#20841)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [cb8105f](https://github.com/sgl-project/sglang/commit/cb8105fe282fc373b5baed63d5df38682418a373)

- **作者**: Qi Yuhang
- **时间**: 2026-03-19T07:39:52Z
- **提交信息**: [sgl-kernel][6/7]Support Expert Specialization Grouped GEMM (#15471)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1098
- **最后更新**: 2026-03-19T12:31:48Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据仓库README摘要（PyTorch-native推理引擎，专注于DiTs的混合缓存加速和大规模并行）及提交记录，以下是昨日更新的分析总结：

### 1. 主要更新类型
- **性能优化**：移除缓存块中的手动图断点，以提升编译和推理性能。
- **工具/配置改进**：为`max-autotune`添加别名，优化用户使用体验。
- **维护性更新**：抑制TorchAO警告，减少日志干扰。

### 2. 关键变更点及其与项目整体方向的关系
- **移除手动图断点（#885）**：直接优化了核心缓存加速机制，减少了PyTorch编译时的图分裂，有助于提升DiT模型推理的效率和并行度，符合项目“高性能推理引擎”的目标。
- **添加`tune`别名（#884）**：简化了自动调优配置，降低了用户使用门槛，支持更灵活的性能调优，与项目强调的“易用性”和“大规模并行”方向一致。
- **抑制TorchAO警告（#883）**：属于代码维护优化，提升日志清晰度，间接改善开发体验，确保核心功能日志更突出。

### 3. 对项目的影响和潜在意义
- **性能提升**：移除图断点可能减少编译开销，加速缓存块执行，对高吞吐DiT推理场景有积极影响。
- **用户体验优化**：别名添加使调优配置更直观，有助于用户快速启用高级优化选项。
- **代码健壮性**：警告抑制减少了无关输出，使调试和监控更聚焦，但需注意潜在依赖兼容性问题。

### 4. 值得关注的技术点
- **PyTorch图编译优化**：手动图断点的移除反映了对PyTorch编译器（如TorchDynamo/Inductor）的深入利用，可能涉及动态形状支持或算子融合改进。
- **自动调优集成**：`max-autotune`别名的添加暗示项目深度集成PyTorch的自动性能调优工具，以发挥硬件（如GPU）极限性能。
- **与TorchAO的协作**：警告抑制表明项目依赖或借鉴TorchAO（PyTorch加速库），需关注其更新对稳定性的影响。

### 5. 基于项目背景的提交影响分析
- **加速核心路径**：作为DiT专用推理引擎，缓存机制是关键创新点。移除图断点直接优化了缓存块的执行效率，可能提升混合缓存加速的实际效果，强化项目在高效推理领域的竞争力。
- **降低使用门槛**：通过别名简化配置，使更多用户（如研究人员、工程师）能轻松启用高级优化，促进项目在社区中的采用，符合开源项目的发展需求。
- **维护可持续发展**：警告清理虽小，但体现了代码库的持续维护，有助于长期稳定性和开发者协作，支撑项目作为“PyTorch-native”引擎的可靠性。

**总结**：昨日更新聚焦于性能优化和用户体验，通过编译优化和配置简化，进一步巩固了项目作为高效DiT推理引擎的定位，同时维护了代码质量，为大规模部署和社区扩展奠定基础。

## 详细提交记录

### [f96060b](https://github.com/vipshop/cache-dit/commit/f96060b53c4a3382e2a37f4478d110064d719055)

- **作者**: DefTruth
- **时间**: 2026-03-19T12:31:40Z
- **提交信息**: remove manually graph break in cache blocks (#885)

* remove manually graph break in cache blocks

* remove manually graph break in cache blocks

### [cd9fbbc](https://github.com/vipshop/cache-dit/commit/cd9fbbc0d2d622750f4dc5573a93eea85a471b25)

- **作者**: DefTruth
- **时间**: 2026-03-19T09:27:11Z
- **提交信息**: chore: add tune alias for max-autotune (#884)

### [174ae6c](https://github.com/vipshop/cache-dit/commit/174ae6ceddada5249a3cc551018ab1aa65cbeefe)

- **作者**: DefTruth
- **时间**: 2026-03-19T07:22:42Z
- **提交信息**: chore: suppress torchao warnings (#883)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 73721
- **最后更新**: 2026-03-19T23:22:10Z

## 提交统计

- **昨日提交总数**: 44
- **提交者数量**: 33
- **主要提交者**: Lucas Kabela, Wei Zhao, Harry Mellor

## AI分析总结

根据提供的 vLLM 项目提交记录，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及模型支持、硬件兼容性、配置解析等。
- **性能优化**：包括 Triton 自动调优缓存、日志优化、内存管理。
- **CI/CD 与测试**：持续集成流程改进、测试结构调整、环境问题修复。
- **代码重构与清理**：模型加载逻辑简化、配置和处理器清理、后端重命名。
- **功能增强**：新增对特定模型（如 Nemotron-3-VL）视频压缩的支持。
- **文档更新**：重新组织部分文档结构。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **修复 Qwen3.5 GDN 层与量化模型的 AttributeError** | 提升对流行模型（Qwen）和量化技术的支持，增强易用性和兼容性。 |
| **默认启用 Triton 自动调优磁盘缓存** | 直接提升推理性能，符合“快速”的核心目标。 |
| **多项 AMD ROCm 相关修复与 CI 清理** | 加强对 AMD GPU 的支持，体现“为所有人服务”的跨平台愿景。 |
| **修复多种模型加载与解析问题** | 扩大模型生态支持（Kimi, Nemotron, MXFP8等），提升稳定性。 |
| **CPU 后端 UX 改进（避免因未预加载库而崩溃）** | 改善 CPU 部署的用户体验，降低使用门槛。 |
| **MoE（混合专家）相关重构与修复** | 优化 MoE 模型的支持，这是高性能服务的关键特性。 |
| **推测解码（Speculative Decoding）和 PD 解耦相关修复** | 优化前沿推理技术，提升吞吐量和成本效益。 |

### 3. 对项目的影响和潜在意义
- **稳定性与可靠性提升**：大量 Bug 修复直接提高了生产环境的稳定性。
- **性能基准持续优化**：性能优化提交确保 vLLM 在速度上保持领先。
- **生态系统扩展**：对更多模型、硬件（AMD, CPU）和特性（视频压缩）的支持，扩大了适用场景。
- **开发者体验改善**：CI/CD 优化、日志调整、错误信息处理使贡献和调试更顺畅。
- **技术债务偿还**：代码清理和重构有助于长期维护和功能迭代。

### 4. 值得关注的技术点
- **Triton 自动调优磁盘缓存**：首次默认启用，可能显著减少内核编译时间，提升冷启动性能。
- **FP8 精度与 MoE 的兼容性修复**：结合了低精度计算和 MoE 架构，是追求极致性能与效率的前沿方向。
- **推测解码（MRV2）中使用 fp32 存储草稿 logits**：平衡了精度与性能，优化了推测解码流程。
- **CPU 后端对 tcmalloc/libiomp 的依赖处理**：使 CPU 部署更健壮，降低了依赖管理的复杂度。
- **`torch.compile` 缓存冲突的解决**：有助于提升动态模型加载和编译场景下的体验。

### 5. 结合项目背景的分析
vLLM 的目标是“**为所有人提供简单、快速、廉价的大语言模型服务**”。昨日的提交完美地服务于这一目标：
- **简单（Easy）**：通过修复各种模型加载错误、改进 CPU 部署的 UX、简化配置和清理代码，降低了用户和开发者的使用与集成门槛。
- **快速（Fast）**：性能优化（Triton 缓存、`hasattr` 优化）、推测解码改进、内核兼容性修复等，都直接致力于提升推理速度。
- **廉价（Cheap）**：支持更多硬件（AMD、CPU），优化资源利用（如 KV 缓存卸载修复），有助于降低部署成本。
- **为所有人（for everyone）**：积极修复 AMD ROCm 生态问题、扩展模型支持范围（Qwen, Kimi, Nemotron等）、完善 CI 测试，体现了对多元化硬件、模型和贡献者生态的投入。

**总结**：昨日的更新是一次典型的“**夯实基础、优化体验、扩展边界**”的迭代。它没有引入颠覆性新功能，而是通过大量修复和优化，巩固了 vLLM 作为高性能 LLM 服务引擎的**稳定性、性能领先性和生态兼容性**，稳步推进其核心使命。

## 详细提交记录

### [4120a05](https://github.com/vllm-project/vllm/commit/4120a05ff1d03797dbcd506110f0a997520a6395)

- **作者**: Jim Smith
- **时间**: 2026-03-19T23:21:14Z
- **提交信息**: Fix AttributeError in Qwen3.5 GDN layers with quantized models (#37448)

Signed-off-by: Jim Smith <jim@joshua8.ai>
Signed-off-by: mgoin <mgoin64@gmail.com>
Signed-off-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Xin Yang <105740670+xyang16@users.noreply.github.com>

### [98ff042](https://github.com/vllm-project/vllm/commit/98ff0429175b98169e1ebffd5ff32d0635bd39cc)

- **作者**: rasmith
- **时间**: 2026-03-19T23:12:45Z
- **提交信息**: [CI][BugFix][AMD] Don't set VLLM_ROCM_USE_AITER anymore in test_rocm_aiter_topk since its not necessary (#36996)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>

### [b55156e](https://github.com/vllm-project/vllm/commit/b55156eae9aa586b8fbeb752ecb369179442c521)

- **作者**: Artem Perevedentsev
- **时间**: 2026-03-19T21:36:28Z
- **提交信息**: [Performance] Enable Triton autotuning disk cache by default (#37188)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [112944f](https://github.com/vllm-project/vllm/commit/112944fab91e63c5daaeed3c0d85478af4e13f50)

- **作者**: Laith Sakka
- **时间**: 2026-03-19T21:28:45Z
- **提交信息**: test Qwen/Qwen3-4B-Instruct-2507 for unbacked (#36064)

Signed-off-by: Laith Sakka <lsakka@meta.com>

### [91be5f9](https://github.com/vllm-project/vllm/commit/91be5f9be3e5bf44fd00b696bf47f0e41edae3bf)

- **作者**: bnellnm
- **时间**: 2026-03-19T19:50:34Z
- **提交信息**: [MoE Refactor] Rename "naive" all2all backend (#36294)

Signed-off-by: Bill Nell <bnell@redhat.com>

### [4ee847e](https://github.com/vllm-project/vllm/commit/4ee847e40094c66669f6095c034a4ff7ef8ad39f)

- **作者**: Aaron Hao
- **时间**: 2026-03-19T19:46:07Z
- **提交信息**: Comment fix for async rl example (#35244)

Signed-off-by: hao-aaron <ahao@anyscale.com>

### [040a505](https://github.com/vllm-project/vllm/commit/040a505ff536b7fa872f18cfb9cba345956758e5)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-19T19:30:58Z
- **提交信息**: [ROCm][CI] Cleaning and restructuring amd-ci legacy pipeline (#34839)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [9279c59](https://github.com/vllm-project/vllm/commit/9279c59a0e81cdc846416ab310b1f9f9c00edfbb)

- **作者**: bnellnm
- **时间**: 2026-03-19T19:07:44Z
- **提交信息**: [MoE Refactor] DefaultMoERunner simplifcation (#33049)

Signed-off-by: Bill Nell <bnell@redhat.com>

### [7454096](https://github.com/vllm-project/vllm/commit/7454096199fcc79a63d2e1aa413e12881966cabd)

- **作者**: Wentao Ye
- **时间**: 2026-03-19T19:04:59Z
- **提交信息**: [Log] Log once in local node by default (#37568)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [fb8b5e0](https://github.com/vllm-project/vllm/commit/fb8b5e05fcd697ed1e0002a7950cf42c36d77e6b)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-19T19:00:20Z
- **提交信息**: [CI] Add retry with 4x backoff to HTTP fetches for transient failures (#37218)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [e5d96dc](https://github.com/vllm-project/vllm/commit/e5d96dc8fce24043dd50d1671a7674bda1728f7f)

- **作者**: Harry Mellor
- **时间**: 2026-03-19T18:04:40Z
- **提交信息**: Fix `SpeculatorsConfig` now that `PreTrainedConfig` is a `dataclass` in Transformers (#37574)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [daa05bf](https://github.com/vllm-project/vllm/commit/daa05bf340cb74b062db727395dce89a7387a832)

- **作者**: EdalatiAli
- **时间**: 2026-03-19T17:58:33Z
- **提交信息**: [Bugfix] Fix AttributeError when serving MXFP8 models with DeepGEMM installed (#37358)

Signed-off-by: EdalatiAli <aliedalati@cohere.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [7769b58](https://github.com/vllm-project/vllm/commit/7769b58307c9604ac833ba790f511cea3989c0e6)

- **作者**: Lucas Kabela
- **时间**: 2026-03-19T17:26:12Z
- **提交信息**: [torch.compile][BE][Multimodal] Remove requirement to set_model_tag to avoid cache conflict (#37345)

Signed-off-by: Lucas Kabela <lucaskabela@meta.com>

### [2f9f946](https://github.com/vllm-project/vllm/commit/2f9f946b22cc39506ae9c0e8e3730376e652a87d)

- **作者**: Chauncey
- **时间**: 2026-03-19T16:41:20Z
- **提交信息**: [P/D] AnthropicMessages add kv_transfer_params for PD disaggregation (#37535)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [2890aec](https://github.com/vllm-project/vllm/commit/2890aecce5d1fe1dcdb61be4bedbe2d46700e51c)

- **作者**: Fadi Arafeh
- **时间**: 2026-03-19T16:35:45Z
- **提交信息**: [CPU][UX] Do not crash when tcmalloc/libiomp are not ldpreloaded (#37561)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>

### [34f093b](https://github.com/vllm-project/vllm/commit/34f093b417d492d9cba2d9b54d126a2d87e7e012)

- **作者**: Harry Mellor
- **时间**: 2026-03-19T16:21:57Z
- **提交信息**: [CI] Gate pre-commit on `ready` label or number of contributions (#37544)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [4dce832](https://github.com/vllm-project/vllm/commit/4dce8321a919a1838cc31551064ec87c3e25713a)

- **作者**: Harry Mellor
- **时间**: 2026-03-19T16:19:50Z
- **提交信息**: Run MacOS smoke test on daily `cron` job instead of every commit (#37567)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [657855a](https://github.com/vllm-project/vllm/commit/657855ab417988834a4d0ff99de27fd66c6a6b3c)

- **作者**: Cyrus Leung
- **时间**: 2026-03-19T15:45:23Z
- **提交信息**: [Misc] Cleanup more configs and processors (#37560)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [e27b8ba](https://github.com/vllm-project/vllm/commit/e27b8ba3d17df1330c81adf755988e8ee0fd6ab8)

- **作者**: Wei Zhao
- **时间**: 2026-03-19T15:43:06Z
- **提交信息**: [Bug] Fix fp8 trtllm MoE modular kernel supported routing methods (#37346)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>

### [40b8363](https://github.com/vllm-project/vllm/commit/40b8363b45a9c59984907603b00b736e41d25065)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-19T15:41:21Z
- **提交信息**: [MRV2] Use fp32 for draft logits (#37526)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [8b10e4f](https://github.com/vllm-project/vllm/commit/8b10e4fb316c14cfdb3109ac6f87722ec2a6c3c8)

- **作者**: mikaylagawarecki
- **时间**: 2026-03-19T15:27:26Z
- **提交信息**: [1/n] Migrate permute_cols to libtorch stable ABI (#31509)

Signed-off-by: Mikayla Gawarecki <mikaylagawarecki@gmail.com>

### [104605c](https://github.com/vllm-project/vllm/commit/104605cbf2046d09436a41a2367a975f73116138)

- **作者**: Ifta khairul Alam Adil
- **时间**: 2026-03-19T15:20:08Z
- **提交信息**: Remove deprecated reasoning_content message field(part-2) (#37480)

Signed-off-by: JartX <sagformas@epdcenter.es>
Signed-off-by: Ifta Khairul Alam Adil <ikaadil007@gmail.com>
Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>
Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Philip Ottesen <phiott256@gmail.com>
Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Signed-off-by: Michael Goin <mgoin64@gmail.com>
Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Signed-off-by: Andy Lo <andy@mistral.ai>
Signed-off-by: Thillai Chithambaram <thillaichithambaram.a@gmail.com>
Signed-off-by: sihao.li <sihao.li@intel.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: JartX <sagformas@epdcenter.es>
Co-authored-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Philip Ottesen <phiott256@gmail.com>
Co-authored-by: Woosuk Kwon <woosuk.kwon@berkeley.edu>
Co-authored-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: Giancarlo Delfin <32987265+TheEpicDolphin@users.noreply.github.com>
Co-authored-by: Andy Lo <andy@mistral.ai>
Co-authored-by: Thillai Chithambaram <79466435+thillai-c@users.noreply.github.com>
Co-authored-by: sihao_li <165983188+1643661061leo@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [96266f1](https://github.com/vllm-project/vllm/commit/96266f119bb93516703328f9e37ec99cce45f792)

- **作者**: Jee Jee Li
- **时间**: 2026-03-19T15:18:06Z
- **提交信息**: [LoRA] Minor improvements to LoRA log (#37557)

Signed-off-by: Jee Jee Li <pandaleefree@gmail.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>

### [7c0cf3b](https://github.com/vllm-project/vllm/commit/7c0cf3bcd0867b5420e6ad4f2ff6b2b25e73b022)

- **作者**: Sage Moore
- **时间**: 2026-03-19T14:42:57Z
- **提交信息**: Cap the number of API servers to 1 when using Elastic EP. (#37466)

Signed-off-by: Sage Moore <sage@neuralmagic.com>

### [572b432](https://github.com/vllm-project/vllm/commit/572b4329133915cc21d7d588d0514d9e8e86dd75)

- **作者**: Harry Mellor
- **时间**: 2026-03-19T14:04:03Z
- **提交信息**: Stop bench CLI from recursively casting all configs to `dict` (#37559)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [9515c20](https://github.com/vllm-project/vllm/commit/9515c208684c7d289b7c482e3ee2d201d9a5c497)

- **作者**: Cyrus Leung
- **时间**: 2026-03-19T13:30:20Z
- **提交信息**: [Misc] Clean up processing logic (#37541)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [c63ca2b](https://github.com/vllm-project/vllm/commit/c63ca2b2e696e8dd1ae0f5ace08fd57a6a95a65f)

- **作者**: DorBernsohn
- **时间**: 2026-03-19T13:08:00Z
- **提交信息**: [Bugfix] Add Kimi-K2.5 reasoning/tool parser aliases and tool_call_id support (#37438)

Signed-off-by: DorBernsohn <dor.bernsohn@gmail.com>

### [a32eaf5](https://github.com/vllm-project/vllm/commit/a32eaf5bb288fd925d66716a7050cc4444a7dfb1)

- **作者**: Harry Mellor
- **时间**: 2026-03-19T12:55:07Z
- **提交信息**: [CI] Merge `cleanup_pr_body.yml` and `reminder_comment.yml` (#37552)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [e390742](https://github.com/vllm-project/vllm/commit/e390742c5906df0edad8fc77b203e0623559ce79)

- **作者**: XueLiang Yang
- **时间**: 2026-03-19T12:05:07Z
- **提交信息**: Fix KV Offloading + MLA AssertionError by using num_kv_heads=1 in cpu… (#37536)

Signed-off-by: xueliangyang-oeuler <yxl546827391@gmail.com>
Co-authored-by: xueliangyang-oeuler <yxl546827391@gmail.com>

### [7a6ebcb](https://github.com/vllm-project/vllm/commit/7a6ebcbfcf2e74876d8493903d444625cd221e7e)

- **作者**: Cyrus Leung
- **时间**: 2026-03-19T12:00:36Z
- **提交信息**: [Model] Remove unnecessary `get_language_model` (#37545)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [c7bc12c](https://github.com/vllm-project/vllm/commit/c7bc12c20f6c0a4b4d9286c87160db5d934c2ead)

- **作者**: Cyrus Leung
- **时间**: 2026-03-19T11:36:11Z
- **提交信息**: [CI/Build] Split out MM pooling tests (#37542)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [f9e2a38](https://github.com/vllm-project/vllm/commit/f9e2a383869c56a1fbee048afc9501ced9194c7e)

- **作者**: wang.yuqi
- **时间**: 2026-03-19T11:25:47Z
- **提交信息**: [Docs] Reorganize pooling docs. (#35592)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: wang.yuqi <noooop@126.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [4426447](https://github.com/vllm-project/vllm/commit/4426447bba144cbf8dd849046caf31ad073aa26b)

- **作者**: Harry Mellor
- **时间**: 2026-03-19T10:38:29Z
- **提交信息**: Don't log `exc_info` when vLLM tries to doenload a file that doesn't exist (#37458)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [3322e26](https://github.com/vllm-project/vllm/commit/3322e26420bc9ea22c5033e9199cd9fb8be5f424)

- **作者**: Li, Jiang
- **时间**: 2026-03-19T10:24:39Z
- **提交信息**: [Bugfix] Avoid more OpenMP thread reallocation in CPU torch compile  (#37538)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [765e461](https://github.com/vllm-project/vllm/commit/765e4610651b02fefe9ebe3b3d322fc398038af6)

- **作者**: Cyrus Leung
- **时间**: 2026-03-19T09:55:29Z
- **提交信息**: [Bugfix] Fix Nemotron Parse loading (#37407)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [6a9cceb](https://github.com/vllm-project/vllm/commit/6a9cceb219fcbd6b1eb540ddfdc77ec160f0e209)

- **作者**: Duyi-Wang
- **时间**: 2026-03-19T09:49:27Z
- **提交信息**: [Bugfix][ROCm] Fix MoRI + AITER FP8 dispatch compatibility for defer_input_quant (#37418)

Signed-off-by: Duyi-Wang <duyi.wang@amd.com>

### [199f914](https://github.com/vllm-project/vllm/commit/199f914183e1f50f0a63a7fa0dd9b025952d8689)

- **作者**: yassha
- **时间**: 2026-03-19T09:45:06Z
- **提交信息**: fix(cpu): add null check for aligned_alloc in ScratchPadManager (#37369)

Signed-off-by: yassha <50112520+yassha@users.noreply.github.com>

### [ca21483](https://github.com/vllm-project/vllm/commit/ca21483bf900b269dd1876352ee335ab62df2ebb)

- **作者**: Kunshang Ji
- **时间**: 2026-03-19T09:23:24Z
- **提交信息**: [MISC] fix pin_memory=torch.cuda.is_available(), use is_pin_memory_available (#37415)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [da70c87](https://github.com/vllm-project/vllm/commit/da70c87e81a84138ea1f745e116bdaa41ec0180e)

- **作者**: TJian
- **时间**: 2026-03-19T09:21:55Z
- **提交信息**: [CI] Fix wrong path test file, missing `rlhf_async_new_apis.py` (#37532)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [0b6d526](https://github.com/vllm-project/vllm/commit/0b6d52629fe84f0071ce41a954162e59dc98157e)

- **作者**: Collin McCarthy
- **时间**: 2026-03-19T08:02:19Z
- **提交信息**: Support temporal compression for Nemotron-3-VL videos (#36808)

Signed-off-by: Collin McCarthy <cmccarthy@nvidia.com>

### [d3cc379](https://github.com/vllm-project/vllm/commit/d3cc379567cdf8787b1e9e688536cdf7c179f474)

- **作者**: Ziming Huang
- **时间**: 2026-03-19T07:43:48Z
- **提交信息**: [Perf] Fix slow hasattr in CUDAGraphWrapper.__getattr__ (#37425)

Signed-off-by: 智鸣 <hzm414167@alibaba-inc.com>

### [354cd58](https://github.com/vllm-project/vllm/commit/354cd580d53abd9b1b5896afc8a9dba61a9063df)

- **作者**: cdpath
- **时间**: 2026-03-19T07:23:35Z
- **提交信息**: fix(anthropic): remove non-standard 'data: [DONE]' from Anthropic streaming (#37510)

Signed-off-by: cdpath <cdpath@outlook.com>

### [d49f273](https://github.com/vllm-project/vllm/commit/d49f27314454afa687fb0323cfce7819e123c1c9)

- **作者**: zhanqiuhu
- **时间**: 2026-03-19T07:22:00Z
- **提交信息**: [SSM/Mamba] Follow-up: N-1 prefill for P/D disaggregation (#37310)

### [b21d384](https://github.com/vllm-project/vllm/commit/b21d3843048001101713e70597fc9484332a5f7e)

- **作者**: Flora Feng
- **时间**: 2026-03-19T07:19:36Z
- **提交信息**: [Refactor] Relocate endpoint tests to mirror serving code directory structure (#37504)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-20
**监控日期**: 2026-03-19
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 3253
- **最后更新**: 2026-03-19T22:54:27Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 12
- **主要提交者**: rongfu.leng, 汪志鹏, rein yang

## AI分析总结

根据提供的README摘要和提交记录，以下是对vllm-omni仓库昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增Voxtral TTS模型支持；为DiT模型（Z-Image & Qwen-Image）添加Int8量化支持。
- **Bug修复**：修复了在线服务器无法返回多张图片、Qwen3-Omni精度问题、Ovis图像生成崩溃、Helios视频生成使用CPU设备、离线与在线扩散推理配置不一致等多个关键问题。
- **性能优化**：修复了CUDAGraphWrapper中缓慢的`hasattr`调用，提升性能。
- **CI/CD与测试**：为ROCm平台设置CI流水线；将BAGEL测试拆分为虚拟/真实权重层级（L2/L3）。
- **硬件支持扩展**：更新BAGEL建模以移除CUDA硬编码，添加XPU支持。
- **基础设施**：为H100任务添加Hugging Face令牌。

### 2. 关键变更点及其与项目整体方向的关系
- **多模态模型扩展**：新增**Voxtral TTS（文本转语音）模型**，直接强化了项目的“全模态”（omni-modality）服务能力，从视觉、语言进一步扩展到音频生成。
- **量化与性能优化**：**DiT模型的Int8量化支持**有助于降低显存占用、提升推理速度，与项目“快速、廉价”（fast, and cheap）的目标高度一致。
- **跨平台与硬件支持**：**XPU支持更新**和**ROCm CI流水线**的建立，表明项目正积极向英伟达CUDA生态之外扩展（如Intel、AMD硬件），提升其服务“所有人”（for everyone）的普适性。
- **稳定性与正确性修复**：一系列Bug修复（特别是多图像返回、配置对齐、精度问题）直接提升了**在线服务**的可靠性和用户体验，这是生产级模型服务的核心。

### 3. 对项目的影响和潜在意义
- **功能矩阵更加完善**：TTS模型的加入补全了“全模态”的关键一环（语音合成），使项目能处理文本、图像、视频、音频的生成与理解，竞争力显著增强。
- **降低部署与使用成本**：Int8量化为大图像扩散模型（DiT）提供了更经济的部署方案，潜在扩大了用户基础。
- **增强企业级可靠性**：针对在线服务、配置一致性、硬件兼容性的修复和优化，使项目更适用于生产环境，吸引更多企业用户。
- **生态扩展信号**：积极适配XPU、完善ROCm支持，显示出项目旨在构建一个**硬件无关的推理后端**，避免被单一厂商绑定，有利于长期生态发展。

### 4. 值得关注的技术点
- **Voxtral TTS的集成**：如何将语音合成模型高效集成到vLLM的调度与服务框架中。
- **DiT模型的Int8量化**：对扩散Transformer这类相对较新且计算密集的模型进行量化，并保证质量，具有技术挑战性。
- **CUDAGraphWrapper性能优化**：针对底层图捕获机制的微优化，反映了对高性能推理极致细节的关注。
- **离线/在线配置对齐**：确保训练/微调与推理服务的配置一致性，是模型服务中一个常见但关键的实际问题。

### 5. 基于项目背景的提交影响分析
项目定位为“**为所有人提供简单、快速、廉价的全模态模型服务**”。昨日的提交集体推动了这一愿景：
- **“全模态”**：通过添加**Voxtral TTS**，项目在“全模态”覆盖上迈出坚实一步，从多模态理解走向多模态生成全覆盖。
- **“快速、廉价”**：**Int8量化**直接降低计算成本和提升速度；**性能Bug修复**（如CUDAGraphWrapper）优化了推理效率；**XPU支持**为用户提供了更多高性价比的硬件选择。
- **“为所有人”**：**跨平台CI（ROCm）**和**多硬件支持（XPU）** 降低了使用门槛；**关键Bug修复**提升了服务的稳定性和易用性，使更广泛的开发者能可靠地使用该项目。
- **“服务”**：针对**在线服务器**、**配置一致性**的修复，以及**CI测试分层**，都体现了对生产级服务稳定性和可维护性的高度重视，使项目不仅是一个研究框架，更是一个可靠的服务平台。

**总结**：昨日的更新是一次**全面且目标明确的迭代**，在扩展模态边界、提升性能与效率、增强跨平台能力、夯实服务稳定性四个维度同时推进，紧密围绕项目“简单、快速、廉价的全模态服务”的核心目标，推动vllm-omni向更成熟、更通用的生产级模型服务平台进化。

## 详细提交记录

### [e9fe78e](https://github.com/vllm-project/vllm-omni/commit/e9fe78e28c9d1be804aa9f1a17279f44542e24b8)

- **作者**: Chen-Yo Sun
- **时间**: 2026-03-19T20:02:11Z
- **提交信息**: [Model] Add Voxtral TTS model (#1803)

Signed-off-by: Chen-Yo Sun <chenyo.sun@mistral.ai>

### [b766c47](https://github.com/vllm-project/vllm-omni/commit/b766c4702c34fa3b04b92336b920c54521be2942)

- **作者**: JuboYu
- **时间**: 2026-03-19T14:58:29Z
- **提交信息**: Int8 Quantization Support for DiT (Z-Image & Qwen-Image) (#1470)

Signed-off-by: juboyu <767868009@qq.com>
Signed-off-by: JuboYu <767868009@qq.com>
Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: WeiQing Chen <40507679+david6666666@users.noreply.github.com>

### [0239057](https://github.com/vllm-project/vllm-omni/commit/0239057cba548bbfcc7434ca9d79bfa10b2fd47e)

- **作者**: TJian
- **时间**: 2026-03-19T14:26:31Z
- **提交信息**: [CI] [ROCm] Setup `test-ready.yml` and `test-merge.yml` (#2017)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [99cc766](https://github.com/vllm-project/vllm-omni/commit/99cc76690d22fe9c0b78d5b8bf9a5f9be62f8770)

- **作者**: Hui.
- **时间**: 2026-03-19T10:57:04Z
- **提交信息**: [Bugfix]Fix bug of online server can not return mutli images (#2007)

Signed-off-by: Hui <1779066624@qq.com>
Co-authored-by: AlvisGong <gwly0401@163.com>

### [60a8c01](https://github.com/vllm-project/vllm-omni/commit/60a8c01a968c46f26546620bb14789a118c8b72d)

- **作者**: rein yang
- **时间**: 2026-03-19T09:34:01Z
- **提交信息**: [Bugfix] revert PR#1758 which introduced the accuracy problem of qwen3-omni (#2009)

Signed-off-by: Rein Yang <ruiruyang2@gmail.com>

### [89fff09](https://github.com/vllm-project/vllm-omni/commit/89fff09628208e924d723ebd00146b28edc37ed3)

- **作者**: Ziming Huang
- **时间**: 2026-03-19T09:10:08Z
- **提交信息**: [Fix] Fix slow hasattr in CUDAGraphWrapper.__getattr__ (#1982)

Signed-off-by: ZeldaHuang <hzm414167@alibaba-inc.com>

### [ba5a66b](https://github.com/vllm-project/vllm-omni/commit/ba5a66b15b3a7c64133769c13880c445d5fd835b)

- **作者**: Chendi.Xue
- **时间**: 2026-03-19T08:55:16Z
- **提交信息**: [XPU] update bagel modeling to remove cuda hardcode, add xpu stage_config (#1931)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [f926882](https://github.com/vllm-project/vllm-omni/commit/f9268822cdbdb02a1ddf3ca94582fbbea7e32adc)

- **作者**: rongfu.leng
- **时间**: 2026-03-19T08:51:45Z
- **提交信息**: [Bugfix] fix helios video generate use cpu device (#1915)

Signed-off-by: rongfu.leng <lenronfu@gmail.com>

### [48b3969](https://github.com/vllm-project/vllm-omni/commit/48b3969717984d51480f890959f9e93461ea9ad5)

- **作者**: Dnoob
- **时间**: 2026-03-19T08:51:02Z
- **提交信息**: [Bugfix] Fix Ovis Image crash when guidance_scale is set without negative_prompt (#1956)

Signed-off-by: Dnoob <dxpouo@gmail.com>

### [b1ceaa7](https://github.com/vllm-project/vllm-omni/commit/b1ceaa7b345359ebf2645ee66267707a374c7734)

- **作者**: Kevin H. Luu
- **时间**: 2026-03-19T08:25:14Z
- **提交信息**: Add HF token to H100 jobs (#2008)

Signed-off-by: khluu <khluu000@gmail.com>

### [5699fe7](https://github.com/vllm-project/vllm-omni/commit/5699fe7a96ad88bc6d5bc0981a1cfdc4d836ec6f)

- **作者**: Samit
- **时间**: 2026-03-19T08:00:26Z
- **提交信息**: [Bugfix] Fix config misalignment between offline and online diffusion inference (Wan2.2, Qwen-Image series) (#1979)

Signed-off-by: samithuang <285365963@qq.com>
Signed-off-by: Samit <285365963@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [81793f1](https://github.com/vllm-project/vllm-omni/commit/81793f1918760c1f6db754d5be95a411e875027e)

- **作者**: 汪志鹏
- **时间**: 2026-03-19T07:32:48Z
- **提交信息**: [CI] Split BAGEL tests into dummy/real weight tiers (L2/L3) (#1998)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

---
