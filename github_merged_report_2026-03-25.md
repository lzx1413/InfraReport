# GitHub Stars 合并报告 - 2026-03-25

**合并日期**: 2026-03-26
**监控日期**: 2026-03-25
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


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1762
- **最后更新**: 2026-03-25T19:05:24Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2103
- **最后更新**: 2026-03-25T16:11:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1978
- **最后更新**: 2026-03-25T13:37:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5215
- **最后更新**: 2026-03-25T21:28:37Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Jiangyun Zhu, Alex Yang, Yong Wu

## AI分析总结

根据FlashInfer仓库的README摘要（专注于“高性能GPU推理内核”）以及昨日（假设为提交记录对应的日期）的提交记录，以下是分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了特定版本GPU依赖库的兼容性问题。
- **构建/依赖优化**：调整了Python依赖覆盖和测试流程，提升构建稳定性和测试准确性。
- **功能增强**：扩展了对非连续状态解码的支持，提高了与外部框架（如vLLM）的兼容性。

### 2. 关键变更点及其与项目整体方向的关系
- **修复`nvidia-nvshmem-cu12`版本约束**：确保构建时使用兼容的GPU库版本，直接支持项目“高性能GPU内核”对稳定底层依赖的要求。
- **优化Python依赖和测试流程**：通过调整依赖覆盖和测试执行顺序，提升开发体验和测试可靠性，符合项目对高质量、可维护代码的追求。
- **支持非连续状态解码**：扩展了GDN（推测为GPU解码核心理念）功能，使其能处理非连续内存状态，增强了与vLLM等流行推理框架的集成能力，支持项目在更广泛推理场景中的应用。

### 3. 对项目的影响和潜在意义
- **提升稳定性和兼容性**：依赖修复减少了因库版本不匹配导致的构建失败或运行时错误，有利于用户和开发者部署。
- **改善开发与测试流程**：更可靠的测试环境降低了“flakiness”（非确定性测试失败），加速了持续集成和代码合并。
- **扩展应用场景**：非连续状态支持使FlashInfer能更好地适配vLLM等工作负载，可能吸引更多用户采用，增强项目在GPU推理生态中的竞争力。

### 4. 值得关注的技术点
- **GPU库版本管理**：对`nvidia-nvshmem-cu12`等底层依赖的显式版本约束，反映了对高性能计算环境稳定性的重视。
- **测试流程优化**：将测试发现和执行置于依赖解析之后，避免了因环境不一致导致的假性测试失败。
- **非连续内存支持**：在解码内核中处理非连续状态，可能涉及内存访问模式的优化，以保持高性能同时增加灵活性。

### 5. 基于项目背景的提交影响分析
FlashInfer旨在提供**高性能GPU推理内核**。昨日的提交整体上强化了这一目标：
- **维护性更新**（如依赖修复和测试优化）确保了项目基础稳固，使团队能更专注于核心性能开发。
- **功能增强**（非连续状态支持）直接扩展了内核的适用性，使FlashInfer能更无缝地集成到vLLM等现有推理框架中，这可能加速其采用，并巩固其作为高性能推理底层库的地位。

**总结**：昨日更新以维护和兼容性改进为主，辅以一项关键功能扩展，共同提升了项目的稳定性、开发体验和生态集成能力，支持FlashInfer作为高性能GPU推理内核库的长期发展。

## 详细提交记录

### [e82d33d](https://github.com/flashinfer-ai/flashinfer/commit/e82d33de1ef9b84ba45b7671953616ff12822895)

- **作者**: Alex Yang
- **时间**: 2026-03-25T21:28:31Z
- **提交信息**: fix: (backinteg from 0.6.7) nvidia-nvshmem-cu12 3.6.5 seems broken (#2893)

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

* **Chores**
* Updated GPU-related build dependency constraint to specify a supported
version range, improving build compatibility and stability.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [aacc355](https://github.com/flashinfer-ai/flashinfer/commit/aacc3550c13420a880401b9a2831d583164f25a8)

- **作者**: Yong Wu
- **时间**: 2026-03-25T16:59:23Z
- **提交信息**: chore: fix the python dependency override (#2651)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Fix the python dependency override

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

* **Chores**
* Adjusted unit test flow so test discovery and execution occur after
dependencies and overrides are finalized, improving accuracy of which
tests run.
* Ensured test environment overrides are re-applied after dependency
installation to maintain consistent test conditions and reduce
flakiness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d505e4e](https://github.com/flashinfer-ai/flashinfer/commit/d505e4e6d5cfe7bfbf0ca3c569c52a4a6b8d70e4)

- **作者**: Jiangyun Zhu
- **时间**: 2026-03-25T16:12:54Z
- **提交信息**: [gdn] support non-contiguous state for decoding (#2727)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
vllm uses non-contiguous state for gdn. Make flashinfer also support it
## 🔍 Related Issues
https://github.com/flashinfer-ai/flashinfer/pull/2521
https://github.com/flashinfer-ai/flashinfer/issues/2687

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

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3307
- **最后更新**: 2026-03-25T21:43:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33160
- **最后更新**: 2026-03-25T16:56:57Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Kashif Rasul, Sayak Paul, Steven Liu

## AI分析总结

根据提供的提交记录和README上下文（Diffusers库是HuggingFace的扩散模型工具库），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增LLaDA2离散文本扩散生成管道及配套调度器。
- **Bug修复**：修复LLaDA2注意力掩码格式、数据类型兼容性等问题。
- **文档更新**：更新内核文档、LLaDA2文档及调度器文档。
- **重构**：合并训练脚本、移除重复代码、遵循库的调度器设计模式。
- **CI/工具更新**：在CI中集成Claude。

### 2. 关键变更点及其与项目方向的关系
| 变更点 | 说明 | 与项目方向的关系 |
|--------|------|------------------|
| **新增LLaDA2管道** (`5d207e7`) | 添加了`LLaDA2Pipeline`和`BlockRefinementScheduler`，支持基于置信度的离散文本扩散生成和编辑。 | 扩展了Diffusers在**文本生成**领域的能力，从传统的图像扩散模型向多模态/文本生成扩散模型拓展，符合项目“扩散模型工具箱”的定位。 |
| **调度器抽象化** | 将置信度提交逻辑从管道提取到专用`BlockRefinementScheduler`中。 | 遵循Diffusers的**模块化设计哲学**（管道、模型、调度器分离），提升代码复用性和可维护性。 |
| **文档修复与增强** (`cbf4d9a`, `762ae05`) | 修复文档错误，增加使用示例和参数说明。 | 提升**开发者体验**和**易用性**，帮助用户快速上手新功能，是开源项目成熟度的体现。 |
| **注意力掩码格式修复** | 将LLaDA2的注意力掩码从`0/-inf`改为`1/0`格式。 | 确保与**HuggingFace Transformer模型**的兼容性，维护生态一致性。 |
| **训练脚本整合** | 将多个训练脚本合并为统一的`train_block_refinement.py`。 | 减少冗余，降低用户选择成本，提升**代码库的整洁度**。 |

### 3. 对项目的影响和潜在意义
- **技术生态扩展**：将Diffusers的应用场景从图像/音频扩散正式扩展到**文本扩散生成**，吸引了NLP社区的用户。
- **模型生产化**：提供了完整的训练、推理、调度工具链，使LLaDA2类模型更容易被集成和使用。
- **开发者友好性**：通过文档和示例的完善，降低了使用门槛，可能促进更多相关模型的贡献。
- **代码质量提升**：重构和Bug修复增强了系统的稳定性和可维护性。

### 4. 值得关注的技术点
- **离散扩散模型**：LLaDA2使用离散token空间的扩散过程，不同于连续空间的传统扩散模型。
- **置信度驱动的块细化**：`BlockRefinementScheduler`采用基于置信度的token提交机制，支持可编辑的文本生成。
- **与Transformer生态集成**：直接支持HuggingFace的`AutoModelForCausalLM`，便于利用现有预训练语言模型。
- **调度器设计模式**：延续了Diffusers将生成逻辑抽象为独立调度器的架构思想。

### 5. 基于项目背景的提交影响分析
- **README中强调**：Diffusers旨在提供“扩散模型的最先进、模块化工具箱”，支持多种模态。
- **这些提交的影响**：
  - **功能扩展**：从图像/音频扩散到文本扩散，实现了**模态拓展**，使工具箱更加通用。
  - **架构一致性**：通过调度器抽象，保持了库的**模块化设计原则**，便于未来扩展其他离散扩散模型。
  - **社区协作**：大量代码审查和合并记录（来自YiYi Xu、dg845等贡献者）体现了**开源协作模式**，确保代码质量。
  - **生产就绪**：提供训练脚本、文档、测试，使LLaDA2不再是实验性代码，而是**可投入生产的功能**。

**总结**：昨日更新是Diffusers库向**多模态扩散模型平台**迈进的重要一步，通过新增文本扩散管道、完善工具链、修复兼容性问题，不仅丰富了库的功能，也巩固了其作为扩散模型标准工具库的地位。

## 详细提交记录

### [cbf4d9a](https://github.com/huggingface/diffusers/commit/cbf4d9a3c384ef97d6b0e40c9846dd9e0e41886a)

- **作者**: Steven Liu
- **时间**: 2026-03-25T16:31:54Z
- **提交信息**: [docs] kernels (#13139)

* kernels

* feedback

### [426daab](https://github.com/huggingface/diffusers/commit/426daabad9cda17caa502f071a107b7dd0c48e9d)

- **作者**: Sayak Paul
- **时间**: 2026-03-25T16:00:06Z
- **提交信息**: [ci] claude in ci. (#13297)

* claude in ci.

* review feedback.

### [762ae05](https://github.com/huggingface/diffusers/commit/762ae059fa98049e8991e1580a5b055dde840fb8)

- **作者**: Kashif Rasul
- **时间**: 2026-03-25T12:19:31Z
- **提交信息**: [LLADA2] documentation fixes (#13333)

documentation fixes

### [5d207e7](https://github.com/huggingface/diffusers/commit/5d207e756e13041065bb28af36f86989e04b9f79)

- **作者**: Kashif Rasul
- **时间**: 2026-03-25T10:47:50Z
- **提交信息**: [Discrete Diffusion] Add LLaDA2 pipeline (#13226)

* feat: add LLaDA2 and BlockRefinement pipelines for discrete text diffusion

Add support for LLaDA2/LLaDA2.1 discrete diffusion text generation:
- BlockRefinementPipeline: block-wise iterative refinement with confidence-based
  token commitment, supporting editing threshold for LLaDA2.1 models
- LLaDA2Pipeline: convenience wrapper with LLaDA2-specific defaults
- DiscreteDiffusionPipelineMixin: shared SAR sampling utilities (top-k, top-p,
  temperature) and prompt/prefix helpers
- compute_confidence_aware_loss: CAP-style training loss
- Examples: sampling scripts for LLaDA2 and block refinement, training scripts
  with Qwen causal LM
- Docs and tests included

* feat: add BlockRefinementScheduler for commit-by-confidence scheduling

Extract the confidence-based token commit logic from BlockRefinementPipeline
into a dedicated BlockRefinementScheduler, following diffusers conventions.

The scheduler owns:
- Transfer schedule computation (get_num_transfer_tokens)
- Timestep management (set_timesteps)
- Step logic: confidence-based mask-filling and optional token editing

The pipeline now delegates scheduling to self.scheduler.step() and accepts
a scheduler parameter in __init__.

* test: add unit tests for BlockRefinementScheduler

12 tests covering set_timesteps, get_num_transfer_tokens, step logic
(confidence-based commits, threshold behavior, editing, prompt masking,
batched inputs, tuple output).

* docs: add toctree entries and standalone scheduler doc page

- Add BlockRefinement and LLaDA2 to docs sidebar navigation
- Add BlockRefinementScheduler to schedulers sidebar navigation
- Move scheduler autodoc to its own page under api/schedulers/

* feat: add --revision flag and fix dtype deprecation in sample_llada2.py

- Add --revision argument for loading model revisions from the Hub
- Replace deprecated torch_dtype with dtype for transformers 5.x compat

* fix: use 1/0 attention mask instead of 0/-inf for LLaDA2 compat

LLaDA2 models expect a boolean-style (1/0) attention mask, not an
additive (0/-inf) mask. The model internally converts to additive,
so passing 0/-inf caused double-masking and gibberish output.

* refactor: consolidate training scripts into single train_block_refinement.py

- Remove toy train_block_refinement_cap.py (self-contained demo with tiny model)
- Rename train_block_refinement_qwen_cap.py to train_block_refinement.py
  (already works with any causal LM via AutoModelForCausalLM)
- Fix torch_dtype deprecation and update README with correct script names

* fix formatting

* docs: improve LLaDA2 and BlockRefinement documentation

- Add usage examples with real model IDs and working code
- Add recommended parameters table for LLaDA2.1 quality/speed modes
- Note that editing is LLaDA2.1-only (not for LLaDA2.0 models)
- Remove misleading config defaults section from BlockRefinement docs

* feat: set LLaDA2Pipeline defaults to recommended model parameters

- threshold: 0.95 -> 0.7 (quality mode)
- max_post_steps: 0 -> 16 (recommended for LLaDA2.1, harmless for 2.0)
- eos_early_stop: False -> True (stop at EOS token)

block_length=32, steps=32, temperature=0.0 were already correct.
editing_threshold remains None (users enable for LLaDA2.1 models).

* feat: default editing_threshold=0.5 for LLaDA2.1 quality mode

LLaDA2.1 is the current generation. Users with LLaDA2.0 models can
disable editing by passing editing_threshold=None.

* fix: align sampling utilities with official LLaDA2 implementation

- top_p filtering: add shift-right to preserve at least one token above
  threshold (matches official code line 1210)
- temperature ordering: apply scaling before top-k/top-p filtering so
  filtering operates on scaled logits (matches official code lines 1232-1235)
- greedy branch: return argmax directly when temperature=0 without
  filtering (matches official code lines 1226-1230)

* refactor: remove duplicate prompt encoding, reuse mixin's _prepare_input_ids

LLaDA2Pipeline._prepare_prompt_ids was a near-copy of
DiscreteDiffusionPipelineMixin._prepare_input_ids. Remove the duplicate
and call the mixin method directly. Also simplify _extract_input_ids
since we always pass return_dict=True.

* formatting

* fix: replace deprecated torch_dtype with dtype in examples and docstrings

- Update EXAMPLE_DOC_STRING to use dtype= and LLaDA2.1-mini model ID
- Fix sample_block_refinement.py to use dtype=

* remove BlockRefinementPipeline

* cleanup

* fix readme

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* removed DiscreteDiffusionPipelineMixin

* add support for 2d masks for flash attn

* Update src/diffusers/training_utils.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/training_utils.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* fix issues from review

* added tests

* formatting

* add check_eos_finished to scheduler

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/schedulers/scheduling_block_refinement.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/schedulers/scheduling_block_refinement.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* fix renaming issues and types

* remove duplicate check

* Update docs/source/en/api/pipelines/llada2.md

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/pipelines/llada2/pipeline_llada2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

---------

Co-authored-by: YiYi Xu <yixu310@gmail.com>
Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 387
- **最后更新**: 2026-03-24T05:55:47Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12096
- **最后更新**: 2026-03-25T21:32:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 25017
- **最后更新**: 2026-03-25T23:25:22Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 9
- **主要提交者**: Baizhou Zhang, YC Yen-Ching Tseng, Mick

## AI分析总结

根据提供的提交记录和README摘要（SGLang是一个专注于高效语言模型推理的项目），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **性能优化**：占比最高，涉及扩散模型、解码内核和调度器。
- **Bug修复**：包括CI流程、GPU清理和特定测试用例。
- **CI/CD改进**：增强测试稳定性、资源管理和变更检测。
- **文档更新**：更新示例文档和整合扩散模型文档。
- **代码质量/重构**：清理JIT编译标志，优化内核代码。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **扩散模型性能优化**（#21318, #21323, #21248） | 强化多模态支持，提升图像生成等任务的推理效率，符合项目“高效推理”的核心目标。 |
| **解码内核优化**（#21103） | 直接提升语言模型解码阶段的吞吐量/延迟，是项目最核心的优化路径。 |
| **CI/CD稳定性增强**（#21338, #21345, #21393） | 确保大规模、多后端（如AMD GPU）测试的可靠性，为项目稳健迭代和高质量交付奠定基础。 |
| **AMD GPU支持修复**（#19868） | 扩展硬件生态兼容性，吸引更广泛的用户和部署场景。 |

### 3. 对项目的影响和潜在意义
- **正面影响**：整体推理性能（尤其是扩散模型）得到提升，用户体验更流畅；CI系统更健壮，降低了回归风险；文档更完善，有助于用户上手。
- **潜在意义**：密集的性能优化提交表明项目正进入深度打磨阶段，专注于核心推理路径的极致效率。对AMD和高端GPU的差异化处理显示出对异构计算环境的细致适配。

### 4. 值得关注的技术点
- **FA3解码优化**（#21103）：`get_scheduler_metadata`的暴露可能用于更精细的批处理调度，对高并发服务场景关键。
- **Triton内核调制**（#21318）：使用Triton编写高性能定制内核，是突破框架通用性瓶颈、榨取硬件性能的典型手段。
- **AKO4ALL内核优化技能**（#21323）：可能引入了新的自动化或半自动化内核优化技术。
- **条件请求与ETag**（#21345）：在CI中应用此HTTP技术，可减少不必要的数据传输，加速流程。

### 5. 基于项目背景的提交影响分析
SGLang的目标是成为**高效、可扩展的LM服务引擎**。昨日的提交集体指向这一目标的实现：
- **强化核心优势**：多项内核与调度优化直接提升了项目的核心竞争力——**推理效率**。
- **提升工程化水平**：大量的CI修复和优化（如资源泄漏、重试机制）表明项目正从“实现功能”向“**生产就绪**”迈进，注重稳定性和可维护性。
- **生态扩展与用户体验**：修复AMD支持、更新文档（如Nemotron示例），有助于**扩大用户基础**并改善开发者体验。
- **聚焦重点领域**：对**扩散模型**的持续优化（性能跟踪、内核提速、文档整合）显示项目正积极将高效推理能力从纯文本LLM扩展到**多模态生成领域**，这符合当前AI应用的发展趋势。

**总结**：昨日的更新是一次以**性能优化和系统稳固**为主题的迭代。它不仅在核心推理路径上深耕，还通过完善CI和文档来夯实项目基础，整体上推动SGLang朝着更高效、更稳定、更易用的生产级推理引擎发展。

## 详细提交记录

### [75682f1](https://github.com/sgl-project/sglang/commit/75682f1d2f60797fb438da8fd6fe40e92e1a26fe)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-25T23:25:16Z
- **提交信息**: Remove noisy streaming backlog warning log (#21432)

### [4dd4e06](https://github.com/sgl-project/sglang/commit/4dd4e06f1d5fd1d294cb82a84b803256760cbfff)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-25T23:22:44Z
- **提交信息**: [CI] Fix resource leak when setUpClass fails (#21338)

### [d5c5683](https://github.com/sgl-project/sglang/commit/d5c5683d2bdc6b916faf39dc93f20aaeafddd25c)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-25T21:40:07Z
- **提交信息**: [CI] Use ETag conditional requests in `wait-for-jobs` and add CI infra to check-changes (#21345)

### [a12fea2](https://github.com/sgl-project/sglang/commit/a12fea21ed08f1a5a808de2ed21bf8e43165e159)

- **作者**: Minglei Zhu
- **时间**: 2026-03-25T20:17:27Z
- **提交信息**: perf(sgl-kernel): expose get_scheduler_metadata for FA3 decode optimization (#21103)

### [e90cba7](https://github.com/sgl-project/sglang/commit/e90cba715c68b97bf86f256cfc8877bb21f88ee6)

- **作者**: Baizhou Zhang
- **时间**: 2026-03-25T19:00:20Z
- **提交信息**: Revert "[Bugfix] Disable ci for .md files" (#21420)

### [f1f13f8](https://github.com/sgl-project/sglang/commit/f1f13f89662dd22953e8418fdc263cdf8bc996f2)

- **作者**: Артем Савкин
- **时间**: 2026-03-25T17:19:44Z
- **提交信息**: [Bugfix] Disable ci for .md files (#21410)

### [77872a8](https://github.com/sgl-project/sglang/commit/77872a8d55081c235e4b45397f9e3bf6af75c17a)

- **作者**: Nave Assaf
- **时间**: 2026-03-25T16:03:19Z
- **提交信息**: Update Nemotron Example docs to include Super v3 and Nano 4B (#21416)

Signed-off-by: Nave Assaf <nassaf@nvidia.com>

### [68f7f00](https://github.com/sgl-project/sglang/commit/68f7f00174b354bebcd2bb2b0564359b32bf2c43)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-25T12:48:39Z
- **提交信息**: [Diffusion] Speed up Qwen select01 Triton modulation kernels (#21318)

### [04eb728](https://github.com/sgl-project/sglang/commit/04eb72801f6c712f6c8a9428727d163f68acf43d)

- **作者**: Mick
- **时间**: 2026-03-25T11:01:33Z
- **提交信息**: [diffusion] CI: add performance tracking job to nightly (#21091)

### [689e9ef](https://github.com/sgl-project/sglang/commit/689e9ef05cd27add25c3c704adef3de8e8842cca)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-25T10:46:21Z
- **提交信息**: [Diffusion] Add AKO4ALL kernel optimization skill (#21323)

### [e4ad105](https://github.com/sgl-project/sglang/commit/e4ad10520b8d409c6d32079a9c46ec7bdc0463ed)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-25T10:45:30Z
- **提交信息**: [diffusion] Skip automatic Wan/MOVA DiT layerwise offload on high-end GPUs (#21248)

### [3d2a61c](https://github.com/sgl-project/sglang/commit/3d2a61cbf6ae10b48d2528107096e103a499b185)

- **作者**: DarkSharpness
- **时间**: 2026-03-25T10:08:40Z
- **提交信息**: [Chore] Clean up JIT compilation flags (#21022)

### [4480e6c](https://github.com/sgl-project/sglang/commit/4480e6c2379d710d6ec5460b22867e1d0fac3284)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-25T09:16:20Z
- **提交信息**: [CI] Add retry loop to `killall_sglang` GPU cleanup verification (#21393)

### [c494e47](https://github.com/sgl-project/sglang/commit/c494e478433f066ecd5a8010613767fce54e33a5)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-03-25T08:10:21Z
- **提交信息**: [AMD] Fix stage-b-test-small-1-gpu-amd (test_tool_choice.py) (#19868)

### [6425df5](https://github.com/sgl-project/sglang/commit/6425df5c8a25812efb1574667ec2d821859f1caa)

- **作者**: Mick
- **时间**: 2026-03-25T08:01:32Z
- **提交信息**: [diffusion] doc: consolidate documentation  (#21373)

### [f5c225e](https://github.com/sgl-project/sglang/commit/f5c225eeba3c6f027e5e7691784249d6a667026f)

- **作者**: Baizhou Zhang
- **时间**: 2026-03-25T07:04:59Z
- **提交信息**: [CI] Fix TestQwen35WithHiCache (#21371)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1108
- **最后更新**: 2026-03-25T09:18:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 74324
- **最后更新**: 2026-03-25T23:13:58Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 24
- **主要提交者**: Wentao Ye, Fadi Arafeh, Ekagra Ranjan

## AI分析总结

根据您提供的 vLLM 项目提交记录和 README 摘要（项目定位为“为所有人提供简单、快速、经济的 LLM 服务”），以下是对昨日更新的分析总结：

### 1. 主要更新类型
昨日提交以**功能新增**和**平台/硬件支持扩展**为主，同时包含大量**Bug修复**、**性能优化**和**代码质量/基础设施**改进。
*   **功能新增 (5项)**：如支持 Cohere-Transcribe、NumPy 数组嵌入、EPLB GPU支持、每草案模型MoE后端等。
*   **平台/硬件支持 (7项)**：主要集中在 **AMD ROCm** 和 **Intel XPU/GPU** 的优化、Bug修复和功能启用，体现了对异构硬件的深度适配。
*   **Bug修复 (8项)**：涉及多个组件（ROCm MoE、CUDA架构、离线模式、权重绑定检查等），提升稳定性。
*   **性能优化 (4项)**：包括内核优化（MLA、GEMM）、内存对齐、默认启用tcmalloc等。
*   **代码重构/质量 (4项)**：如错误处理重构、Mypy类型修复、输入重组、重命名常量以提高可读性。
*   **文档/CI/测试 (7项)**：更新文档、改进CI流程、增加测试覆盖。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向（易用、快速、经济、普适）的关系 |
| :--- | :--- |
| **支持 Cohere-Transcribe 和 NumPy 数组嵌入** | **易用性 & 生态扩展**：集成更多商业API（Cohere）并增强多模态输入的灵活性（NumPy），降低用户使用门槛，丰富应用场景。 |
| **密集的 ROCm/XPU 优化与Bug修复** | **经济性 & 普适性**：通过深度优化AMD和Intel硬件支持，为用户提供更多高性价比的部署选择，减少对单一硬件（NVIDIA）的依赖，使服务更“经济”且广泛可用。 |
| **EPLB支持、每草案模型MoE后端** | **功能强大性 & 灵活性**：增强了对复杂推理（推测解码、专家混合模型）的支持，使vLLM能服务于更高级、更定制化的LLM应用场景。 |
| **内核优化（MLA、FP8 GEMM）、默认启用tcmalloc** | **快速性**：直接优化计算和内存管理核心路径，提升吞吐量和降低延迟，是维持其“快速”核心优势的关键。 |
| **CUDA架构后缀修复、KV连接器错误处理重构** | **稳定性 & 健壮性**：修复底层关键Bug和改进错误处理，确保核心服务在各种环境（如新硬件）下稳定运行，是项目可靠性的基石。 |

### 3. 对项目的影响和潜在意义
*   **扩大硬件生态护城河**：对ROCm和XPU的持续投入，使vLLm在支持多硬件架构方面领先，可能吸引更多云厂商和成本敏感用户。
*   **提升企业级适用性**：通过增强稳定性（Bug修复）、可维护性（重构、类型检查）和安全性（CI/CD改进），项目正朝着更成熟、更可靠的企业级服务框架演进。
*   **拓展应用边界**：新增的API集成（Cohere）和模型支持（JAIS, Plamo等）意味着vLLm正在从“纯推理服务器”向更广泛的“LLM服务编排与集成平台”延伸。

### 4. 值得关注的技术点
1.  **异构计算优化**：`[ROCm] Utilize persistent MLA kernel`、`[XPU] support MLA model` 显示了跨AMD/Intel/NVIDIA的通用内核优化策略。
2.  **前沿推理技术集成**：`Flashinfer nvfp4 cutedsl moe kernel integration` 和 `per-draft-model MoE backend` 涉及推测解码和MoE的高效实现，是推理前沿。
3.  **量化与性能深度结合**：`Migrate per_token_group_quant to torch stable ABI` 和 `Optimize SM120 CUTLASS blockwise FP8 GEMM` 体现了在保持精度下的极致性能追求。
4.  **部署友好性改进**：`Enable tcmalloc by default` (CPU) 和 `Align memory usage with cuda on xpu` 降低了部署调优门槛。

### 5. 基于项目背景的提交影响分析
这些提交共同推动 vLLM 朝其“**为所有人提供简单、快速、经济的 LLM 服务**”的愿景迈进：
*   **简单/易用**：通过文档更新 (`Add guide for editing agent instruction files`)、更灵活的输入支持 (`numpy array embeddings`)、更少的配置需求（默认tcmalloc）来达成。
*   **快速**：通过底层内核优化（ROCm/XPU/CUDA）、新内核集成（Flashinfer MoE）和性能Bug修复（`Fix MoE kernel test failures`）来持续强化。
*   **经济**：通过对 AMD 和 Intel 硬件的深度优化与支持，为用户提供了强大且低成本的替代方案，直接降低了硬件采购和运营成本。
*   **为所有人**：通过扩大硬件支持（ROCm, XPU）、修复各类环境下的Bug（ARM CPU, 不同CUDA arch）、完善CI/CD对不同架构（aarch64）的支持，使项目能在更广泛的环境中开箱即用，真正服务“

## 详细提交记录

### [7b54f60](https://github.com/vllm-project/vllm/commit/7b54f60db0f55d74dac8aa3040c02363b7a9f6ec)

- **作者**: Ekagra Ranjan
- **时间**: 2026-03-25T23:13:51Z
- **提交信息**: [Cohere] Enable Cohere-Transcribe (#38120)

Signed-off-by: Ekagra Ranjan <3116519+ekagra-ranjan@users.noreply.github.com>

### [a0e8c74](https://github.com/vllm-project/vllm/commit/a0e8c74005f5782fad30be912c12cd37fc2813e9)

- **作者**: Rohan Potdar
- **时间**: 2026-03-25T20:58:44Z
- **提交信息**: [ROCm]: Update rope+kvcache fusion conditions and disable custom op by default (#36716)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>

### [70a2152](https://github.com/vllm-project/vllm/commit/70a2152830959d0d5e25d60869f2fb3e2fa3733c)

- **作者**: Guillaume Guy
- **时间**: 2026-03-25T20:13:04Z
- **提交信息**: [MultiModal] add support for numpy array embeddings (#38119)

Signed-off-by: guillaume_guy <guillaume.guy@airbnb.com>
Signed-off-by: Guillaume Guy <guillaume.c.guy@gmail.com>
Co-authored-by: guillaume_guy <guillaume.guy@airbnb.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>

### [978fc18](https://github.com/vllm-project/vllm/commit/978fc18bf000dbe36d361e32995b7178dbdde20c)

- **作者**: Sathish Sanjeevi
- **时间**: 2026-03-25T19:00:42Z
- **提交信息**: [ROCm] Utilize persistent MLA kernel from AITER (#36574)

Signed-off-by: Sathish Sanjeevi <sathish.krishnan.p.s@gmail.com>

### [7d6917b](https://github.com/vllm-project/vllm/commit/7d6917bef552d6aff70142ab9fb8af648081d4db)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-25T18:46:40Z
- **提交信息**: [ROCm] Fix MoE kernel test failures on gfx950 (#37833)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Woosuk Kwon <woosuk.kwon@berkeley.edu>
Co-authored-by: Matthew Wong <Matthew.Wong2@amd.com>

### [e38817f](https://github.com/vllm-project/vllm/commit/e38817fadbe10393ec8ef2fd52fe9a086d7365c1)

- **作者**: Mark McLoughlin
- **时间**: 2026-03-25T18:20:48Z
- **提交信息**: [Core][KV Connector] Remove use of num_cached_tokens in error handling (#38096)

Signed-off-by: Mark McLoughlin <markmc@redhat.com>

### [72cad44](https://github.com/vllm-project/vllm/commit/72cad44d3c6eaac69d8353981b9f2b4439d12ecd)

- **作者**: Nick Hill
- **时间**: 2026-03-25T18:14:41Z
- **提交信息**: [Frontend] Move APIServerProcessManager target server fn (#38115)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [ba2f0ac](https://github.com/vllm-project/vllm/commit/ba2f0acc2d69cb11f2c1bce895521550fa73bcc3)

- **作者**: Cyrus Leung
- **时间**: 2026-03-25T17:22:54Z
- **提交信息**: [Misc] Reorganize inputs (#35182)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [678b3c9](https://github.com/vllm-project/vllm/commit/678b3c99e82e1b1dd6cc95ff98c114393b788be4)

- **作者**: Yongye Zhu
- **时间**: 2026-03-25T17:16:40Z
- **提交信息**: [MoE Kernel] Flashinfer nvfp4 cutedsl moe kernel integration (#38050)

### [bf4cc9e](https://github.com/vllm-project/vllm/commit/bf4cc9ed2d1f2075a1dbdeed233a9a44a7d48247)

- **作者**: mikaylagawarecki
- **时间**: 2026-03-25T17:15:13Z
- **提交信息**: [2/n] Migrate per_token_group_quant to torch stable ABI (#36058)

Signed-off-by: Mikayla Gawarecki <mikaylagawarecki@gmail.com>

### [1ac2ef2](https://github.com/vllm-project/vllm/commit/1ac2ef2e5335ca0af99aee438998c9305461f563)

- **作者**: Ben Browning
- **时间**: 2026-03-25T16:24:42Z
- **提交信息**: [CI/Docs] Improve aarch64/DGX Spark support for dev setup (#38057)

Signed-off-by: Ben Browning <bbrownin@redhat.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [6e37c46](https://github.com/vllm-project/vllm/commit/6e37c46b35e2ee799fb280180f4d582219bea3f0)

- **作者**: Richard Zou
- **时间**: 2026-03-25T16:02:22Z
- **提交信息**: [compile] Add some more startup tests for top models (#38046)

Signed-off-by: Richard Zou <zou3519@gmail.com>

### [1bf2ddd](https://github.com/vllm-project/vllm/commit/1bf2ddd0ee24cf878a87b643536b749676e8f902)

- **作者**: Wentao Ye
- **时间**: 2026-03-25T15:41:44Z
- **提交信息**: [Refactor] Rename `WAITING_FOR_FSM` to `WAITING_FOR_STRUCTURED_OUTPUT_GRAMMAR` (#38048)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [e722118](https://github.com/vllm-project/vllm/commit/e7221180e1d67a91e84a93aea08841fef8c67680)

- **作者**: Necofish
- **时间**: 2026-03-25T15:20:04Z
- **提交信息**: [Kernel] Optimize SM120 CUTLASS blockwise FP8 GEMM (#37970)

Signed-off-by: Necofish <liuxiangyang@mail.ustc.edu.cn>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [4a76ad1](https://github.com/vllm-project/vllm/commit/4a76ad12e00109f3bb06ccbd7089fc3612564e31)

- **作者**: RobTand
- **时间**: 2026-03-25T15:18:25Z
- **提交信息**: [Bugfix] Preserve CUDA arch suffix (a/f) for SM12x — fixes NVFP4 NaN on desktop Blackwell (#37725)

Signed-off-by: Rob Tand <robert.tand@icloud.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [d7e93e1](https://github.com/vllm-project/vllm/commit/d7e93e13fb5c92243682466c1b3100b963445a17)

- **作者**: Wentao Ye
- **时间**: 2026-03-25T15:16:39Z
- **提交信息**: [Feature] EPLB Support for GPU Model Runner v2 (#37488)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [cd76430](https://github.com/vllm-project/vllm/commit/cd7643015e583c1e78d437118a6ce8282cb85663)

- **作者**: Andrii Skliar
- **时间**: 2026-03-25T14:31:52Z
- **提交信息**: [Feature] Support per-draft-model MoE backend via `--speculative-config` (#37880)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Signed-off-by: [Andrii Skliar] <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>

### [a1a2566](https://github.com/vllm-project/vllm/commit/a1a25664471fb9c0b7b2059321635ec86580e3cc)

- **作者**: Ben Browning
- **时间**: 2026-03-25T13:54:09Z
- **提交信息**: [Docs] Add guide for editing agent instruction files (#37819)

Signed-off-by: Ben Browning <bbrownin@redhat.com>

### [b745e8b](https://github.com/vllm-project/vllm/commit/b745e8b5d35a22095b99e63493e53c97bb1542a7)

- **作者**: yjz
- **时间**: 2026-03-25T13:24:07Z
- **提交信息**: [KVTransfer][Mooncake] Add heterogeneous TP support for disaggregated P/D in MooncakeConnector (#36869)

Signed-off-by: JianDan0212 <zhangyj0212@gmail.com>

### [d215d1e](https://github.com/vllm-project/vllm/commit/d215d1efca7a18eb2a19007f229bbb070bfbee93)

- **作者**: Harry Mellor
- **时间**: 2026-03-25T13:14:43Z
- **提交信息**: [Mypy] Better fixes for the `mypy` issues in `vllm/config` (#37902)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [34d317d](https://github.com/vllm-project/vllm/commit/34d317dcec3935e588d6c8ee8a7a57abb7a3e731)

- **作者**: Fadi Arafeh
- **时间**: 2026-03-25T12:39:57Z
- **提交信息**: [CPU][UX][Perf] Enable tcmalloc by default (#37607)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>

### [7ac48fd](https://github.com/vllm-project/vllm/commit/7ac48fd3577f35e235ef96e690c3fc9b847fd26a)

- **作者**: grYe99
- **时间**: 2026-03-25T12:38:40Z
- **提交信息**: [Model] Add AutoWeightsLoader support for jais (#38074)

Signed-off-by: grYe99 <guorongye99@gmail.com>
Co-authored-by: grYe99 <guorongye99@gmail.com>

### [d6bb2a9](https://github.com/vllm-project/vllm/commit/d6bb2a9d9a3453b86e40bc7b37d39ab7bd6f0969)

- **作者**: Harry Mellor
- **时间**: 2026-03-25T12:29:49Z
- **提交信息**: Fix Plamo 2/3 & LFM2 for Transformers v5 (#38090)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [1e673a4](https://github.com/vllm-project/vllm/commit/1e673a43ce0197d0ff05041e862e5022c57c1e07)

- **作者**: Harry Mellor
- **时间**: 2026-03-25T12:07:23Z
- **提交信息**: Better weight tying check for multimodal models (#38035)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [04417ec](https://github.com/vllm-project/vllm/commit/04417ecd5f492c2c216faa7200a0589f7241a302)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-25T12:05:46Z
- **提交信息**: [ROCm][CI] Rename filepath test to point to correct file (#38102)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [242c93f](https://github.com/vllm-project/vllm/commit/242c93f74494e32569cc836d5075a88ccddc53a7)

- **作者**: R0CKSTAR
- **时间**: 2026-03-25T11:54:36Z
- **提交信息**: [Docs] Adds vllm-musa to custom_op.md (#37840)

Signed-off-by: Xiaodong Ye <yeahdongcn@gmail.com>

### [a889b7f](https://github.com/vllm-project/vllm/commit/a889b7f58426e612b55aa67d7d243dbbceaf1184)

- **作者**: Matthias Gehre
- **时间**: 2026-03-25T11:42:58Z
- **提交信息**: [Bugfix] Pass drafter quant_config to ParallelLMHead in Eagle3 (#37280)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>

### [ba2910f](https://github.com/vllm-project/vllm/commit/ba2910f73a0341b46525a3441da2e7cb66698d58)

- **作者**: Harry Mellor
- **时间**: 2026-03-25T11:39:48Z
- **提交信息**: Fix offline mode test for Transformers v5 (#38095)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [f262a62](https://github.com/vllm-project/vllm/commit/f262a62aa191b4fc3070a5fd7f418246cb326f06)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-25T10:55:51Z
- **提交信息**: [ROCm][CI] Fix flaky Cohere/OpenAI embedding parity test (#37616)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [9ac2fca](https://github.com/vllm-project/vllm/commit/9ac2fcafbb193692fdebe03b3da58625e26382f0)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-25T10:24:33Z
- **提交信息**: [CI] Fix realtime WebSocket timeout deadlock and unhandled model validation errors (#37483)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [e9ae3f8](https://github.com/vllm-project/vllm/commit/e9ae3f80779711eef52fa40741ed15cc025fb784)

- **作者**: Kunshang Ji
- **时间**: 2026-03-25T10:14:29Z
- **提交信息**: [Hardware][XPU] Align memory usage with cuda on xpu (#37029)

Signed-off-by: Kunshang Ji <jikunshang95@gmail.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [04cec4f](https://github.com/vllm-project/vllm/commit/04cec4f927cc8d1df85518450d8a48a6ae4f52bf)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-25T10:06:58Z
- **提交信息**: [ROCm][CI] Increase OpenAPI schema test timeouts (#38088)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [14771f7](https://github.com/vllm-project/vllm/commit/14771f715085f5026919d30048329c3e822d4b3c)

- **作者**: Kunshang Ji
- **时间**: 2026-03-25T09:43:42Z
- **提交信息**: [XPU] support MLA model on Intel GPU (#37143)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [189ddef](https://github.com/vllm-project/vllm/commit/189ddefbfdf74e676c8f74ebe89826e94bf44ccf)

- **作者**: Gregory Shtrasberg
- **时间**: 2026-03-25T09:42:56Z
- **提交信息**: [ROCm] Attention selector reordering (#36702)

Signed-off-by: Gregory Shtrasberg <Gregory.Shtrasberg@amd.com>
Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-26
**监控日期**: 2026-03-25
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 3824
- **最后更新**: 2026-03-25T23:08:34Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 12
- **主要提交者**: Sy03, Hui., Markus / Mark

## AI分析总结

根据 vllm-omni 仓库的 README 摘要（“Easy, fast, and cheap omni-modality model serving for everyone”）可知，该项目旨在为多模态模型提供高效、易用且经济的推理服务。结合昨日的提交记录，分析总结如下：

### 1. 主要更新类型
- **Bug 修复**：4 项（#2178, #2025, #2041, #2171）
- **功能新增/增强**：2 项（#1227, #1911）
- **性能优化**：1 项（#2145）
- **测试与 CI**：4 项（#2191, #2192, #2120, #2138）
- **文档更新**：1 项（#2148）
- **代码清理**：1 项（#2161）

### 2. 关键变更点及其与项目整体方向的关系
- **多模态语音功能增强**（#1227）：为语音和语音合成 API 添加说话人嵌入支持，直接强化了项目的“omni-modality”（全模态）服务能力，使语音模型能更好地处理个性化语音生成与识别。
- **TTS 性能优化**（#2145）：针对 Fish Speech S2 Pro 语音克隆模型优化首次令牌生成时间（TTFP），提升了语音服务的响应速度，符合“fast”的目标。
- **模型架构与设备初始化修复**（#2178, #2025）：确保模型架构正确注入 Hugging Face 覆盖配置，并使多阶段设备初始化遵循可见 GPU 设置，提高了系统稳定性和资源利用率，支持“cheap”部署。
- **空输入提示修复**（#2041）：处理空提示输入场景，增强 API 的健壮性，提升用户体验。

### 3. 对项目的影响和潜在意义
- **提升语音模态成熟度**：语音相关功能（说话人嵌入、TTS 性能优化、Qwen-TTS 测试）的集中更新，表明语音服务正成为项目重点，有助于吸引语音应用开发者。
- **增强生产环境可靠性**：多项 Bug 修复和 CI 测试优化减少了潜在运行时错误，提高了服务稳定性，有利于生产部署。
- **优化资源管理**：设备初始化修复确保 GPU 资源被正确识别和利用，降低了部署成本，符合“cheap”目标。

### 4. 值得关注的技术点
- **说话人嵌入集成**（#1227）：可能涉及声纹特征提取与模型适配，为个性化语音交互提供了基础。
- **TTS 首令牌延迟优化**（#2145）：针对 Fish Speech 模型的推理优化，可能涉及缓存、预热或计算图优化技术。
- **多阶段设备初始化**（#2025）：涉及分布式或异构环境下的 GPU 资源管理，对大规模部署很重要。

### 5. 基于项目背景的提交影响分析
vllm-omni 致力于成为**全模态、高性能、低成本的模型服务平台**。昨日的提交整体推动了这一愿景：
- **全模态扩展**：语音功能增强（说话人嵌入、TTS 测试与优化）丰富了模态支持，强化了“omni-modality”定位。
- **高性能保障**：TTS 性能优化和多项稳定性修复直接提升了服务速度与可靠性，支持“fast”目标。
- **低成本优化**：设备初始化修复避免了 GPU 资源浪费，测试 CI 优化减少了维护成本，间接支持“cheap”目标。
- **开发者体验**：文档更新（#2148）和 API 健壮性修复（#2041）降低了使用门槛，促进项目生态增长。

**总结**：昨日更新以**语音模态功能增强和系统稳定性提升**为核心，紧密围绕项目“全模态、快速、经济”的定位，推动了平台在语音服务方向的成熟度与整体可靠性。

## 详细提交记录

### [b569cb5](https://github.com/vllm-project/vllm-omni/commit/b569cb56b6a01fbe5b0441fbd58314fea3455469)

- **作者**: rongfu.leng
- **时间**: 2026-03-25T19:05:28Z
- **提交信息**: [Bugfix] add inject model_arch to hf_overrides (#2178)

Signed-off-by: rongfu.leng <lenronfu@gmail.com>

### [29936a3](https://github.com/vllm-project/vllm-omni/commit/29936a3edd53749b7b38897f7aa99f92ee0aadff)

- **作者**: Markus / Mark
- **时间**: 2026-03-25T19:02:48Z
- **提交信息**: [Frontend] Speaker embedding support for speech and voices APIs (#1227)

Signed-off-by: marksverdhei <marksverdhei@hotmail.com>
Signed-off-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>
Signed-off-by: linyueqian <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>
Co-authored-by: linyueqian <linyueqian@outlook.com>

### [d2b9f9f](https://github.com/vllm-project/vllm-omni/commit/d2b9f9ff0f432c22cd84ed16f6a7bdacca8ab9c6)

- **作者**: Gao Han
- **时间**: 2026-03-25T16:20:26Z
- **提交信息**: [CI] Skip test_sd3_expansion due to CI failure 5148 (#2191)

Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>

### [18d2d08](https://github.com/vllm-project/vllm-omni/commit/18d2d082aa7bdd41bd1dd29d804c09e42f731f00)

- **作者**: Yueqian Lin
- **时间**: 2026-03-25T16:10:16Z
- **提交信息**: Revert "[Test] Add Qwen-tts test cases and unify the style of existing test cases" (#2192)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [fc32da7](https://github.com/vllm-project/vllm-omni/commit/fc32da76247e53b85d42755f48a2aabcdbe8e90d)

- **作者**: Sy03
- **时间**: 2026-03-25T15:41:10Z
- **提交信息**: [Perf] [TTS] Improve Fish Speech S2 Pro voice cloning TTFP (#2145)

Signed-off-by: Sy03 <1370724210@qq.com>

### [5466ed4](https://github.com/vllm-project/vllm-omni/commit/5466ed419bbbc9ffc9184fdf867f3752eb538ae7)

- **作者**: wangyu
- **时间**: 2026-03-25T15:27:33Z
- **提交信息**: [Test] Add Qwen-tts test cases and unify the style of existing test cases (#1911)

Signed-off-by: yenuo26 <410167048@qq.com>
Signed-off-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Signed-off-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>
Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: yenuo26 <410167048@example.com>
Co-authored-by: R2-Y <ruiruyang2@gmail.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [c09b039](https://github.com/vllm-project/vllm-omni/commit/c09b039f3776a7bb73e81349ec52fd694dc3e6c6)

- **作者**: Alex Brooks
- **时间**: 2026-03-25T09:56:13Z
- **提交信息**: [BugFix] Make Stage Device Initialization Respect Visible GPUs (#2025)

Signed-off-by: Alex Brooks <albrooks@redhat.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [0adbac3](https://github.com/vllm-project/vllm-omni/commit/0adbac33a5ba0493c0e1966516d981467f6a8960)

- **作者**: Hui.
- **时间**: 2026-03-25T08:42:04Z
- **提交信息**: [Bug-Fix]fix bug of empty prompt input (#2041)

Signed-off-by: AlvisGong <gwly0401@163.com>
Signed-off-by: Hui <1779066624@qq.com>
Signed-off-by: Hui. <1779066624@qq.com>
Co-authored-by: AlvisGong <gwly0401@163.com>

### [91a8186](https://github.com/vllm-project/vllm-omni/commit/91a818629c09db1764069fee9089c196fc69515d)

- **作者**: Yueqian Lin
- **时间**: 2026-03-25T08:26:38Z
- **提交信息**: [Cleanup] Remove stray test file from engine directory (#2161)

Signed-off-by: linyueqian <linyueqian@outlook.com>
Co-authored-by: Canlin Guo <canlinguosdu@gmail.com>

### [ed8cfdf](https://github.com/vllm-project/vllm-omni/commit/ed8cfdfb1b2debf6a9b557e9e164cdc0c32dd07c)

- **作者**: Bingyu (Spencer) Liu
- **时间**: 2026-03-25T08:19:06Z
- **提交信息**: [CI] Add Stable Diffusion 3.5 Tests (#2120)

Signed-off-by: LiuBingyu <liubingyu62@gmail.com>

### [c2888a8](https://github.com/vllm-project/vllm-omni/commit/c2888a8a36186ab5d3605bfb9b50adbb4c7c7db3)

- **作者**: dongbo910220
- **时间**: 2026-03-25T07:46:15Z
- **提交信息**: [Docs] refine UAA documentation (#2148)

Signed-off-by: dongbo910220 <1275604947@qq.com>
Co-authored-by: Didan Deng <33117903+wtomin@users.noreply.github.com>

### [6d439eb](https://github.com/vllm-project/vllm-omni/commit/6d439ebad8b1625b69951b951fc723e483408fc5)

- **作者**: Junhong Liu
- **时间**: 2026-03-25T07:37:50Z
- **提交信息**: [Fixbug] increase qwen2 5 online test timeout limit (#2171)

Signed-off-by: Junhong Liu <98734602+LJH-LBJ@users.noreply.github.com>
Signed-off-by: Junhong Liu <ljh_lbj@163.com>

### [61092ac](https://github.com/vllm-project/vllm-omni/commit/61092acd822f89a79dfc7725c1839485f2bd76a4)

- **作者**: zhumingjue138
- **时间**: 2026-03-25T07:14:02Z
- **提交信息**: [CI] Fix examples tests error (#2138)

Signed-off-by: zhumingjue <zhumingjue@huawei.com>

---
