# GitHub Stars 合并报告 - 2026-06-09

**合并日期**: 2026-06-10
**监控日期**: 2026-06-09
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


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2000
- **最后更新**: 2026-06-09T14:09:52Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: dzy00897185

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **文档更新 (Bug修复)**

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：修复了与昇腾（Ascend）硬件平台相关的文档错误（`[docs] fix: Ascend documents fix`）。
- **与项目方向的关系**：VeOmni 的目标是“扩展任意模态模型的训练”（Scaling Any Modality Model Training），并提供一个“以模型为中心的分布式配方库”（Model-Centric Distributed Recipe Zoo）。支持不同的硬件平台（如昇腾）是实现其“分布式”和“可扩展性”目标的关键。修复昇腾文档，直接服务于让用户能在该硬件上顺利使用VeOmni进行模型训练。

### 3. 对项目的影响和潜在意义
- **直接影响**：提高了文档的准确性和可用性，减少了用户在昇腾平台上部署和运行VeOmni时可能遇到的困惑和障碍。
- **潜在意义**：
    - **降低使用门槛**：清晰的文档是吸引和留住用户（尤其是使用非NVIDIA GPU的用户）的重要因素。
    - **增强生态兼容性**：表明项目团队正在积极维护和优化对昇腾等国产硬件的支持，这对于项目的长期发展和在中国市场的应用具有重要意义。
    - **提升项目成熟度**：及时修复文档错误是项目成熟和负责任的体现。

### 4. 值得关注的技术点
- **对昇腾（Ascend）硬件的支持**：这表明VeOmni的分布式训练框架不仅限于NVIDIA GPU，正在积极适配其他主流AI加速芯片。这对于希望使用国产硬件或特定硬件平台的用户来说是一个积极的信号。

### 5. 基于README了解的项目背景，这些提交如何影响项目发展
- **项目背景**：VeOmni 是一个旨在简化多模态模型大规模训练的框架，强调“模型中心”和“分布式”。
- **对项目发展的影响**：此次文档修复虽然是一个小更新，但它直接支持了项目的核心承诺——提供一个**可用**且**可扩展**的训练方案。通过确保昇腾平台的文档准确无误，项目能够吸引更广泛的用户群体，验证其“分布式配方库”在不同硬件上的有效性，从而推动项目向更通用、更强大的方向发展。这有助于巩固VeOmni作为多模态训练基础设施的地位。

## 详细提交记录

### [439d3a8](https://github.com/ByteDance-Seed/VeOmni/commit/439d3a87a2fdd6b26ab8e2bf8d8a97f68f39229e)

- **作者**: dzy00897185
- **时间**: 2026-06-09T12:11:49Z
- **提交信息**: [docs] fix: Ascend documents fix (#830)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2353
- **最后更新**: 2026-06-09T11:37:55Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Shiqiao Gu (谷石桥)

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是针对昨日更新的要点分析：

### 昨日更新要点总结

1.  **主要更新类型**
    *   **功能新增 (Feature)**：本次提交属于新功能集成。

2.  **关键变更点及其与项目整体方向的关系**
    *   **变更点**：在 `infinitetalk` 模块中，新增了对 `LightX2V` 框架的支持，该支持由 `skill` 和 `Codex` 驱动（`feat(infinitetalk): add LightX2V support guided by skill and Codex (#1138)`）。
    *   **与项目方向的关系**：`LightX2V` 项目本身是一个**轻量级视频生成推理框架**。本次提交将 `LightX2V` 作为推理后端集成到 `infinitetalk`（一个可能专注于长视频或无限对话生成的模块）中，这直接扩展了 `LightX2V` 的应用场景，使其能够服务于更复杂的、需要持续生成或交互的视频任务。这符合项目“轻量级”和“推理框架”的核心定位，通过模块化集成增强了框架的实用性和生态兼容性。

3.  **对项目的影响和潜在意义**
    *   **影响**：`infinitetalk` 模块现在可以直接利用 `LightX2V` 的高效推理能力，可能显著提升其在视频生成任务中的性能和效率。
    *   **潜在意义**：
        *   **能力增强**：使 `LightX2V` 从单纯的视频生成工具，向支持更高级应用（如无限对话视频生成）的组件演进。
        *   **生态建设**：通过 `skill` 和 `Codex` 的引导，表明项目正在构建一个更灵活、可编程的框架，允许用户通过技能（Skill）和代码（Codex）来定制和驱动视频生成过程，这有助于吸引开发者社区，构建更丰富的应用生态。

4.  **值得关注的技术点**
    *   **“guided by skill and Codex”**：这是一个值得深入关注的技术细节。它暗示了 `LightX2V` 的集成不仅仅是简单的API调用，而是引入了一种**基于技能和代码的引导机制**。这可能意味着：
        *   **Skill**：预定义或可学习的视频生成能力模块（如特定风格、动作、场景）。
        *   **Codex**：一种用于编排这些技能、控制生成流程的脚本或配置语言。
        *   这种设计模式使得视频生成过程更加可控、可组合，是迈向更高级AI Agent或工作流的重要一步。

5.  **基于README了解的项目背景，这些提交如何影响项目发展**
    *   `LightX2V` 的愿景是成为一个**轻量级**的视频生成推理框架。本次提交通过集成 `infinitetalk`，展示了其**轻量级和模块化**设计的优势：能够轻松地被其他系统或模块调用，作为核心推理引擎。
    *   这标志着项目从“提供基础推理能力”向“构建可组合的应用生态”迈出了关键一步。通过支持 `infinitetalk` 这样的高级应用，`LightX2V` 不再只是一个孤立的工具，而是成为了一个更宏大视频生成解决方案的基石，这有助于提升项目的知名度和实际应用价值，吸引更多开发者基于它构建上层应用。

## 详细提交记录

### [3db8710](https://github.com/ModelTC/LightX2V/commit/3db87106bafd980f0eeaffdb0d61dd26b364290c)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-06-09T11:37:46Z
- **提交信息**: feat(infinitetalk): add LightX2V support guided by skill and Codex (#1138)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2119
- **最后更新**: 2026-06-09T07:20:09Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 1. 主要更新类型
*   **功能新增**：本次提交主要引入了新的训练功能和模型更新。

### 2. 关键变更点及其与项目整体方向的关系
*   **Ode training (ODE训练)**：新增了ODE（常微分方程）训练方法。这通常与扩散模型（如CogVideoX、Wan2.1）的采样过程优化相关，旨在提升生成视频的质量或效率。
*   **Update Lens model (更新Lens模型)**：更新了“Lens”模型。结合项目背景（视频生成），这可能是一个用于视频理解、条件控制或质量增强的辅助模型，其更新有助于提升生成视频的语义对齐或视觉效果。
*   **Update LTX2 upsampler (更新LTX2上采样器)**：更新了LTX2上采样器。上采样器用于提升视频分辨率，这与项目“视频生成”的核心目标直接相关，旨在生成更高清、更细腻的视频内容。

**与项目方向的关系**：这些变更均直接服务于项目的核心目标——**高质量视频生成**。ODE训练优化生成过程，Lens模型增强条件控制或理解，上采样器提升最终输出质量，三者共同推动项目向更专业、更高质量的视频生成工具发展。

### 3. 对项目的影响和潜在意义
*   **提升生成质量**：ODE训练和上采样器更新将直接改善生成视频的清晰度、流畅度和细节表现。
*   **增强模型能力**：Lens模型的更新可能意味着项目在视频内容理解或条件控制方面取得了进展，使得生成结果更符合用户意图。
*   **扩展应用场景**：更高质量的生成能力（如高清、高保真）将使项目更适用于影视制作、广告创意、虚拟内容生产等专业领域。

### 4. 值得关注的技术点
*   **ODE训练**：这是扩散模型领域的一个前沿技术方向，关注其如何与CogVideoX或Wan2.1等模型结合，以及具体带来了哪些性能提升（如采样步数减少、质量提升）。
*   **LTX2上采样器**：这是一个具体的模型组件更新，值得关注其架构或训练数据的变化，以及相比之前版本在超分辨率效果上的提升。

### 5. 基于项目背景，这些提交如何影响项目发展
*   **巩固技术领先性**：通过引入ODE训练等先进技术，项目在视频生成领域的专业性和技术深度得到加强，有助于在开源社区中保持竞争力。
*   **完善产品功能链**：从训练（ODE）到条件控制（Lens）再到后处理（上采样），本次更新覆盖了视频生成流程中的多个关键环节，使项目从一个“能生成”的工具，向一个“能生成高质量、可控视频”的完整解决方案迈进。
*   **吸引更多用户**：更高的生成质量和更丰富的功能，将吸引更多对视频质量有高要求的开发者和创作者使用该项目，从而扩大社区影响力。

## 详细提交记录

### [1fd9ed9](https://github.com/aigc-apps/VideoX-Fun/commit/1fd9ed9208ba280f6b48c542a7739e636f4e2a14)

- **作者**: Bubbliiiing
- **时间**: 2026-06-09T07:20:04Z
- **提交信息**: Ode training && Update Lens model && Update LTX2 upsampler (#497)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5768
- **最后更新**: 2026-06-09T23:06:22Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Andrew Gu, Yong Wu, Brian K. Ryu

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **性能优化**：提交 `49cb250` 和 `3111f8f` 均旨在提升核心推理操作的性能。
- **Bug修复**：提交 `0b29eed` 修复了一个关键的共享内存竞态条件（race condition）问题。
- **功能新增**：提交 `97b7de6` 引入了一个全新的“Trace Apply”功能，用于优化API调用分发。

### 2. 关键变更点及其与项目整体方向的关系

FlashInfer 的核心目标是提供**高性能的 GPU 推理内核**。这些提交都紧密围绕这一目标：

- **`49cb250` (性能优化 - 采样)**:
    - **变更**: 为 `top_k_top_p_sampling` 函数增加了一个更快的路径。当 `top_k` 值远小于词表大小时，该路径不再处理整个词表，而是先通过高效的并行基数选择（radix top-k）选出前 `k` 个候选，然后仅在这 `k` 个候选中进行 `top_p` 采样。
    - **与项目方向关系**: 直接提升了推理中关键采样步骤的性能，尤其是在大词表、小 `top_k` 的常见场景下（如LLM推理），速度提升可达2-4倍。这完全符合项目“高性能”的定位。

- **`3111f8f` (性能优化 - MLA解码)**:
    - **变更**: 优化了多头潜在注意力（MLA）解码时的workspace内存管理，避免在非性能分析（profiling）模式下进行不必要的workspace重置。
    - **与项目方向关系**: 针对MLA这种先进注意力机制进行微优化，提升了其在推理时的性能（从73.2 TFLOPs/s提升到91.4 TFLOPs/s），体现了项目对前沿模型架构（如DeepSeek-R1）的支持和性能追求。

- **`0b29eed` (Bug修复 - TopK内核)**:
    - **变更**: 修复了 `FilteredTopK` 内核在溢出修正（overflow refinement）路径中的一个共享内存（smem）竞态条件。该问题由 `compute-sanitizer` 工具发现，可能导致数据竞争和结果错误。
    - **与项目方向关系**: 修复了核心内核的稳定性问题，确保了结果的正确性和可靠性。这对于一个提供底层算子的库至关重要，是“高性能”的基础。

- **`97b7de6` (功能新增 - Trace Apply)**:
    - **变更**: 引入了一个名为“Trace Apply”的运行时框架。它允许用户通过环境变量或API启用，将特定的API调用（如注意力、采样）智能地分发给预定义的、经过优化的解决方案（solutions）。这些解决方案可以是Python代码或编译后的后端。
    - **与项目方向关系**: 这是一个重要的架构性更新。它旨在解决“一刀切”的优化策略无法在所有场景下最优的问题。通过“Trace Apply”，FlashInfer可以针对不同的模型、硬件或配置，动态选择或应用最合适的实现，从而在更广泛的场景下实现“高性能”。

### 3. 对项目的影响和潜在意义

- **性能提升**: 采样和MLA解码的性能优化直接提升了最终用户的推理速度，降低了延迟。
- **稳定性增强**: 修复TopK内核的竞态条件，提高了库的健壮性和结果的可靠性，这对于生产环境部署至关重要。
- **架构演进**: “Trace Apply”功能的引入标志着FlashInfer从一个提供固定内核的库，向一个更智能、更灵活的**高性能推理调度框架**演进。这为未来支持更多硬件后端、模型变体和自定义优化策略奠定了基础，具有长远的战略意义。

### 4. 值得关注的技术点

- **`49cb250` 中的采样优化策略**: 这是一种典型的“分而治之”思想。通过先缩小问题规模（从V到k），再在缩小后的空间上执行复杂操作（top-p采样），从而大幅降低计算量。其关键在于使用了高效的并行基数选择算法来快速获取top-k。
- **`0b29eed` 中的竞态条件**: 这是一个典型的GPU编程问题。在循环中，不同轮次对同一块共享内存既有读取（用于更新状态）又有写入（用于清零），如果没有正确的同步（`__syncthreads()`），就会导致数据竞争。修复方法是在读取和写入操作之间添加同步屏障。
- **`97b7de6` 中的“Trace Apply”架构**: 该功能的核心是“Plan/run”模式。它允许在“Plan”阶段捕获API调用的输入（如张量形状、数据类型），然后在“Run”阶段根据这些信息选择并执行最优的“Solution”。这为动态形状、模型编译等高级优化场景提供了可能。

### 5. 基于项目背景，这些提交如何影响项目发展

- **巩固核心优势**: 采样和MLA的优化直接强化了FlashInfer在LLM推理领域的性能优势，使其在与其他库（如vLLM、TensorRT-LLM）的竞争中更具吸引力。
- **提升可靠性**: 修复竞态条件表明项目团队对代码质量有严格要求，这对于一个被广泛依赖的底层库来说，是建立用户信任的关键。
- **开启新篇章**: “Trace Apply”功能是项目发展的重要里程碑。它使FlashInfer从一个“提供高性能内核”的库，升级为一个“**能够智能组合和调度高性能内核**”的平台。这为未来支持更复杂的模型结构、更灵活的

## 详细提交记录

### [49cb250](https://github.com/flashinfer-ai/flashinfer/commit/49cb250fa00d63b5f732a5d0c3e81af84f2f2c52)

- **作者**: Brian K. Ryu
- **时间**: 2026-06-09T23:06:18Z
- **提交信息**: perf(sampling): Optimize top_k_top_p_sampling_from_logits/from_probs for large-vocab small-k sampling (#3461)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

### Summary
Adds a faster `filter_apply_order="top_k_first"` path for
`top_k_top_p_sampling_from_logits` and
`top_k_top_p_sampling_from_probs`. For modest `top_k` over a large
vocabulary, instead of masking/renormalizing the full vocab and running
rejection sampling across it, we select the top-k entries with the
parallel radix top-k kernel and run top-p **over only those k
survivors**. This is distribution-equivalent to the existing path but
2–4× faster for `from_logits` (see benchmarks).

Addresses the slow small-batch top-k/top-p sampling reported in #3389.

### Motivation

The existing `top_k_first` path keeps everything in full-vocab layout:
- `from_logits`: `top_k_mask_logits` → `torch.softmax` (full vocab) →
`top_p_sampling_from_probs` (single-CTA rejection over full vocab)
- `from_probs`: `top_k_renorm_probs` → `top_p_sampling_from_probs`
(single-CTA rejection over full vocab)

After top-k, only `k` entries are relevant, but the general full-vocab
kernels still process all `V` elements — a full-vocab softmax (logits)
and a multi-round single-CTA rejection scan (both). At small batch the
rejection kernel launches one CTA per request and underutilizes the GPU.

### Changes

A gated fast path in `flashinfer/sampling.py` (no kernel changes):

1. Select top-k via `flashinfer.top_k(..., sorted=True)` (parallel radix
selection, returns the `k` values + their indices).
2. Normalize over the `k` survivors — `softmax` (logits) or renorm
(probs); these are mathematically identical to the masked full-vocab
versions.
3. Run `top_p_sampling_from_probs` over the `k`-element distribution,
then map the local choice back to the global vocab index via `gather`.
Both entry points route through the same helper with `sorted=True`, so
they reduce to the same `probs_k` and stay **sample-aligned** with each
other.

### Accuracy
- **Distribution-equivalent** to the original `top_k_first` path
(validated: total-variation distance ≈ 0.007 vs. the analytic target
over 40k draws).
- **Per-seed sample values may differ** from previous versions (the RNG
now maps over a `k`-element domain, and radix top-k may break
k-th-boundary ties differently). The two APIs remain aligned with each
other.
- **CUDA-graph compatible**: the default vectorized top-k captures into
a graph; the graph-safe fallback is only requested for the
non-deterministic cluster path.

### Benchmarks
  
`top_k=50`, `top_p=0.9`, CUDA-graph mode, median ms. "before" = original
path, "after" = fast path.

### B200 (SM100)

| API | dtype | bs | vocab | before | after | speedup |
|---|---|---|---|---|---|---|
| from_logits | bf16 | 1 | 128k | 0.121 | 0.059 | 2.05× |
| from_logits | bf16 | 8 | 128k | 0.139 | 0.064 | 2.17× |
| from_logits | bf16 | 32 | 128k | 0.147 | 0.066 | 2.23× |
| from_logits | bf16 | 256 | 128k | 0.431 | 0.180 | 2.39× |
| from_logits | bf16 | 1 | 256k | 0.206 | 0.067 | 3.07× |
| from_logits | bf16 | 32 | 256k | 0.294 | 0.075 | 3.92× |
| from_logits | fp32 | 1 | 128k | 0.126 | 0.057 | 2.21× |
| from_logits | fp32 | 8 | 128k | 0.131 | 0.063 | 2.08× |
| from_logits | fp32 | 32 | 128k | 0.163 | 0.068 | 2.40× |
| from_logits | fp32 | 256 | 128k | 0.453 | 0.122 | 3.71× |
| from_logits | fp32 | 1 | 256k | 0.208 | 0.061 | 3.41× |
| from_logits | fp32 | 32 | 256k | 0.296 | 0.113 | 2.62× |
| from_probs | fp32 | 1 | 128k | 0.076 | 0.064 | 1.19× |
| from_probs | fp32 | 8 | 128k | 0.077 | 0.067 | 1.15× |
| **from_probs** | fp32 | 32 | 128k | 0.088 | 0.105 | **0.84×** |
| from_probs | fp32 | 256 | 128k | 0.365 | 0.155 | 2.35× |
| from_probs | fp32 | 1 | 256k | 0.099 | 0.067 | 1.48× |
| from_probs | fp32 | 32 | 256k | 0.235 | 0.116 | 2.03× |

### RTX PRO 6000 (SM120)

| API | dtype | bs | vocab | before | after | speedup |
|---|---|---|---|---|---|---|
| from_logits | bf16 | 1 | 128k | 0.096 | 0.042 | 2.29× |
| from_logits | bf16 | 8 | 128k | 0.111 | 0.044 | 2.52× |
| from_logits | bf16 | 32 | 128k | 0.143 | 0.054 | 2.65× |
| from_logits | bf16 | 256 | 128k | 0.454 | 0.173 | 2.62× |
| from_logits | bf16 | 1 | 256k | 0.159 | 0.042 | 3.79× |
| from_logits | bf16 | 32 | 256k | 0.232 | 0.081 | 2.86× |
| from_logits | fp32 | 1 | 128k | 0.101 | 0.041 | 2.46× |
| from_logits | fp32 | 8 | 128k | 0.126 | 0.045 | 2.80× |
| from_logits | fp32 | 32 | 128k | 0.162 | 0.079 | 2.05× |
| from_logits | fp32 | 256 | 128k | 0.631 | 0.287 | 2.20× |
| from_logits | fp32 | 1 | 256k | 0.171 | 0.042 | 4.07× |
| from_logits | fp32 | 32 | 256k | 0.287 | 0.113 | 2.54× |
| from_probs | fp32 | 1 | 128k | 0.056 | 0.043 | 1.30× |
| from_probs | fp32 | 8 | 128k | 0.061 | 0.048 | 1.27× |
| from_probs | fp32 | 32 | 128k | 0.110 | 0.083 | 1.33× |
| from_probs | fp32 | 256 | 128k | 0.405 | 0.293 | 1.38× |
| from_probs | fp32 | 1 | 256k | 0.080 | 0.044 | 1.82× |
| from_probs | fp32 | 32 | 256k | 0.252 | 0.115 | 2.19× |

### Commands to reproduce results above
```
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 1   --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype bfloat16
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 8   --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype bfloat16
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 32  --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype bfloat16
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 256 --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype bfloat16
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 1   --vocab_size 256000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype bfloat16
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 32  --vocab_size 256000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype bfloat16
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 1   --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype float32
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 8   --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype float32
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 32  --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype float32
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 256 --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype float32
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 1   --vocab_size 256000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype float32
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 32  --vocab_size 256000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first --input_dtype float32
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_probs --batch_size 1   --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_probs --batch_size 8   --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_probs --batch_size 32  --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_probs --batch_size 256 --vocab_size 128000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_probs --batch_size 1   --vocab_size 256000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first
python flashinfer_benchmark.py --routine top_k_top_p_sampling_from_probs --batch_size 32  --vocab_size 256000 --top_k 50 --top_p 0.9 --filter_apply_order top_k_first
```

## 🔍 Related Issues

<!-- Link any related issues here -->

#3389

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
* Added an automatic fast path that speeds up sampling when using
top‑k‑first filtering with a scalar k on large vocabularies. Sampling
now selects and renormalizes a smaller candidate set for faster draws,
preserves determinism/tie‑breaking and validity flags when requested,
falls back to the original flow when not applicable, and introduces no
public API changes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [3111f8f](https://github.com/flashinfer-ai/flashinfer/commit/3111f8fdb582ac8ea47e3f29182d32f2105d6357)

- **作者**: Vincent
- **时间**: 2026-06-09T20:44:23Z
- **提交信息**: Avoid workspace reset for standalone MLA decode (#3465)

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

Running the benchmark before and after on a B200 machine gives:
```
python3 flashinfer_benchmark.py \
  --routine BatchMLAPagedAttentionWrapper \
  --backends trtllm-native \
  --page_size 64 --batch_size 1 \
  --s_qo 1 --s_kv 8192 \
  --num_qo_heads 128 --num_kv_heads 128 \
  --head_dim_ckv 512 --head_dim_kpe 64 \
  --random_actual_seq_len -vv --refcheck \
  --q_dtype fp8_e4m3 --kv_dtype fp8_e4m3 \
  --generate_repro_command --case_tag DeepSeek-R1 \
  --num_iters 100 --dry_run_iters 20 \
```
- Before: 0.016 ms, 73.2 TFLOPs/s
- After: 0.013 ms, 91.4 TFLOPs/s

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved workspace memory handling for MLA decode: the buffer region
used for profiling is now cleared only during profiling runs. This
prevents unnecessary memory operations during normal inference, reduces
interference in shared-workspace scenarios, and improves performance and
stability during autotuning/profile measurements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0b29eed](https://github.com/flashinfer-ai/flashinfer/commit/0b29eed266f41fa762a512725bdc8ac098a9e812)

- **作者**: Andrew Gu
- **时间**: 2026-06-09T19:06:49Z
- **提交信息**: Fix smem race in `FilteredTopK` overflow refinement (#3529)

<!-- .github/pull_request_template.md -->

## 📌 Description
The `FilteredTopK` overflow refinement path has an smem race (flagged by
`racecheck`).

In the overflow refinement loop, each round reuses `s_histogram`
([code](https://github.com/flashinfer-ai/flashinfer/blob/a28703432faab15fda7edd71b6c80be0206df973/include/flashinfer/topk.cuh#L2733)):
- near the end of round `r`, threads read `s_histogram` to update
`topk_remain`:
  ```cpp
  topk_remain -= static_cast<uint32_t>(s_histogram[threshold + 1]);
  ```
- at the start of round `r + 1`, threads clear `s_histogram`:
  ```cpp
  if (tx < RADIX + 1) s_histogram[tx] = 0;
  ```

This PR fixes by adding a `__synchtreads()` after the `topk_remain`
decrement before the loop can either break or continue to the next
round.

---

<details>

<summary> Repro Script </summary>

```bash
compute-sanitizer --tool racecheck --target-processes all uv run python repro_flashinfer_topk_race.py
```

```
#!/usr/bin/env python3
"""Minimal FlashInfer radix top-k racecheck repro.

This script intentionally uses a tie-heavy input so FlashInfer's filtered top-k
kernel enters the shared-memory overflow refinement path.

Example:
    python repro_flashinfer_topk_race.py

Run under NVIDIA Compute Sanitizer:
    compute-sanitizer --tool racecheck --target-processes all \
        python repro_flashinfer_topk_race.py

Affected FlashInfer versions report shared-memory hazards in the radix top-k
kernel. The script does not use any project-specific wrappers.
"""

from __future__ import annotations

import argparse
import sys
from importlib import metadata

import torch

DTYPES = {
    "float32": torch.float32,
    "float16": torch.float16,
    "bfloat16": torch.bfloat16,
}


def parse_args() -> argparse.Namespace:
    parser = argparse.ArgumentParser()
    parser.add_argument("--rows", type=int, default=512)
    parser.add_argument("--vocab", type=int, default=131072)
    parser.add_argument("--k", type=int, default=128)
    parser.add_argument("--dtype", choices=sorted(DTYPES), default="float32")
    parser.add_argument("--iters", type=int, default=1)
    parser.add_argument("--deterministic", action="store_true", default=True)
    parser.add_argument("--nondeterministic", dest="deterministic", action="store_false")
    parser.add_argument("--sorted", action="store_true")
    return parser.parse_args()


def main() -> int:
    args = parse_args()
    if not torch.cuda.is_available():
        print("CUDA is required for this repro.", file=sys.stderr)
        return 1

    import flashinfer
    from flashinfer.topk import can_implement_filtered_topk, get_topk_module

    device = torch.device("cuda")
    dtype = DTYPES[args.dtype]

    try:
        flashinfer_version = metadata.version("flashinfer")
    except metadata.PackageNotFoundError:
        flashinfer_version = getattr(flashinfer, "__version__", "unknown")

    print(f"torch={torch.__version__}")
    print(f"flashinfer={flashinfer_version} ({flashinfer.__file__})")
    print(f"cuda_device={torch.cuda.get_device_name(device)}")
    print(f"can_implement_filtered_topk={can_implement_filtered_topk()}")
    print(
        "case="
        f"rows={args.rows}, vocab={args.vocab}, k={args.k}, dtype={args.dtype}, "
        f"sorted={args.sorted}, deterministic={args.deterministic}"
    )

    # All zeros force all logits into the same radix bucket. For vocab=128K and
    # k=128 this enters the overflow refinement loop that reuses s_histogram.
    # The default 512 rows give racecheck enough CTAs to report the hazard
    # reliably on affected versions.
    logits = torch.zeros((args.rows, args.vocab), dtype=dtype, device=device)

    topk_module = get_topk_module()
    row_states_buffer = torch.zeros(1024 * 1024, dtype=torch.uint8, device=device)
    output_values = torch.empty((args.rows, args.k), dtype=dtype, device=device)

    indices = None
    for _ in range(args.iters):
        indices = topk_module.radix_topk(
            logits,
            args.k,
            args.sorted,
            args.deterministic,
            row_states_buffer,
            output_values,
        )
        torch.cuda.synchronize()

    assert indices is not None
    assert output_values.shape == (args.rows, args.k)
    assert indices.shape == (args.rows, args.k)
    assert indices.dtype == torch.int32
    assert bool(torch.all(output_values == 0).item())
    assert bool(torch.all((indices >= 0) & (indices < args.vocab)).item())

    print("completed")
    return 0


if __name__ == "__main__":
    raise SystemExit(main())
```

</details>

<details>

<summary> Example Output </summary>

```
========= COMPUTE-SANITIZER
========= Variable environment CUDA_COREDUMP_FILE is not supported by compute-sanitizer, clearing it before target process launch.
========= Variable environment CUDA_COREDUMP_GENERATION_FLAGS is not supported by compute-sanitizer, clearing it before target process launch.
========= Variable environment CUDA_ENABLE_COREDUMP_ON_EXCEPTION is not supported by compute-sanitizer, clearing it before target process launch.
torch=2.11.0+cu130
flashinfer=0.6.8.post1 (/tmp/.../lib/python3.12/site-packages/flashinfer/__init__.py)
cuda_device=NVIDIA GB300
can_implement_filtered_topk=True
case=rows=512, vocab=131072, k=128, dtype=float32, sorted=False, deterministic=True
========= Error: Race reported between Read access at void flashinfer::sampling::FilteredTopKUnifiedKernel<float, int, (int)4, (bool)1, (flashinfer::sampling::FilteredTopKMode)0>(const T1 *, T2 *, T1 *, const T2 *, long, const T2 *, const T2 *, unsigned int, unsigned int, unsigned int)+0x111e0
=========     and Write access at void flashinfer::sampling::FilteredTopKUnifiedKernel<float, int, (int)4, (bool)1, (flashinfer::sampling::FilteredTopKMode)0>(const T1 *, T2 *, T1 *, const T2 *, long, const T2 *, const T2 *, unsigned int, unsigned int, unsigned int)+0x11230 [3852 hazards]
========= 
========= Error: Race reported between Read access at void flashinfer::sampling::FilteredTopKUnifiedKernel<float, int, (int)4, (bool)1, (flashinfer::sampling::FilteredTopKMode)0>(const T1 *, T2 *, T1 *, const T2 *, long, const T2 *, const T2 *, unsigned int, unsigned int, unsigned int)+0x137a0
=========     and Write access at void flashinfer::sampling::FilteredTopKUnifiedKernel<float, int, (int)4, (bool)1, (flashinfer::sampling::FilteredTopKMode)0>(const T1 *, T2 *, T1 *, const T2 *, long, const T2 *, const T2 *, unsigned int, unsigned int, unsigned int)+0x137f0 [3596 hazards]
========= 
========= Error: Race reported between Read access at void flashinfer::sampling::FilteredTopKUnifiedKernel<float, int, (int)4, (bool)1, (flashinfer::sampling::FilteredTopKMode)0>(const T1 *, T2 *, T1 *, const T2 *, long, const T2 *, const T2 *, unsigned int, unsigned int, unsigned int)+0x16160
=========     and Write access at void flashinfer::sampling::FilteredTopKUnifiedKernel<float, int, (int)4, (bool)1, (flashinfer::sampling::FilteredTopKMode)0>(const T1 *, T2 *, T1 *, const T2 *, long, const T2 *, const T2 *, unsigned int, unsigned int, unsigned int)+0x161a0 [3560 hazards]
========= 
completed
========= RACECHECK SUMMARY: 3 hazards displayed (3 errors, 0 warnings)
```

</details>


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

## Bug Fixes

* Improved reliability of top-k filtering operations by resolving a
synchronization issue in the multi-round fallback path to ensure
accurate results across all computational scenarios.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [97b7de6](https://github.com/flashinfer-ai/flashinfer/commit/97b7de6846e72a9f5cbb536ac8eff04d2e9535bb)

- **作者**: Yong Wu
- **时间**: 2026-06-09T14:45:41Z
- **提交信息**: feat: add FlashInfer Trace Apply (#3240)

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

Co-authored-by: Yixin Dong <yixind@andrew.cmu.edu>
Co-authored-by: Zihao Ye <zihaoy@nvidia.com>


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Opt-in "Trace Apply" runtime to dispatch select API calls to curated
solutions; enable via env var or API.
* Solution loaders for Python and compiled backends; per-solution
caching and safe materialization.
* Stateful plan/run support: capture/reuse plan-time inputs for run-time
dispatch.

* **Behavior Changes**
* Strict dispatch semantics: matched solutions execute (errors
propagate); unmatched calls fall back.
* Templates: outputs can bind to API params; several attention templates
now optionally return LSE.

* **Documentation**
  * Added comprehensive Trace Apply guide.

* **Tests**
  * Extensive unit and integration tests for Trace Apply and loaders.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yixin Dong <yixind@andrew.cmu.edu>
Co-authored-by: Zihao Ye <zihaoy@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3698
- **最后更新**: 2026-06-09T22:36:22Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: William Lin, Aryan Kumar

## AI分析总结

好的，这是对 `hao-ai-lab/FastVideo` 仓库昨日提交记录的分析总结：

### 1. 主要更新类型

-   **功能新增 (feat):** 1项
-   **Bug修复 (bugfix):** 1项
-   **模型支持 (model):** 1项

### 2. 关键变更点及其与项目整体方向的关系

-   **新增 Lucy Edit 推理框架 (7f53942):**
    -   **变更点:** 为名为“Lucy Edit”的功能添加了推理（inference）的脚手架代码。这通常意味着提供了运行该功能的基础代码结构、接口或示例。
    -   **与项目方向关系:** 该项目名为“FastVideo”，核心目标是加速视频生成和处理。新增编辑功能（Edit）的推理框架，表明项目正在从单纯的生成向更复杂的视频编辑和后期处理能力扩展，符合“快速视频处理”的定位。

-   **修复训练中 VSA Tile 缓存释放问题 (19a838f):**
    -   **变更点:** 修复了一个Bug，该Bug导致在训练过程中，VSA（可能指某种注意力机制或特征处理模块）的Tile（分块）缓存没有被正确释放。
    -   **与项目方向关系:** 训练效率是“FastVideo”的核心。内存泄漏（缓存未释放）会随着训练时间增长导致内存耗尽、训练中断或性能下降。修复此Bug直接提升了训练过程的稳定性和资源利用效率，是项目追求“快速”和“稳定”的关键一环。

-   **移植 Flux2 Klein 模型 (d922ab2):**
    -   **变更点:** 将名为“Flux2 Klein”的模型移植到了项目中。这通常意味着为该模型添加了加载、运行和推理的支持。
    -   **与项目方向关系:** 持续集成和适配最新的、高质量的生成模型是视频生成项目保持竞争力的关键。移植新模型（Flux2 Klein）直接扩展了FastVideo支持的模型生态，为用户提供了更多选择和可能性，符合项目作为一站式视频生成/处理平台的愿景。

### 3. 对项目的影响和潜在意义

-   **Lucy Edit:** 标志着项目从“生成”迈向“编辑”的重要一步。这可能会吸引更多需要视频后期处理、风格迁移或局部修改的用户，拓宽了应用场景。
-   **VSA Tile 缓存修复:** 直接影响所有使用该模块进行训练的用户。修复后，训练过程将更加稳定，尤其对于需要长时间、大规模训练的任务（如微调模型），意义重大。
-   **Flux2 Klein 移植:** 直接提升了项目的模型库丰富度。如果Flux2 Klein在特定任务（如高分辨率、特定风格）上有优势，这将增强FastVideo在该领域的竞争力。

### 4. 值得关注的技术点

-   **Lucy Edit:** 其具体的编辑能力（如图文编辑、局部重绘、风格迁移等）和实现方式值得关注。这可能是基于扩散模型的编辑技术，其推理框架的设计思路对后续开发有参考价值。
-   **VSA Tile 缓存:** 这个Bug的修复点（`release VSA tile cache`）暗示了项目在训练中使用了分块（tiling）技术来处理高分辨率视频或图像，以节省显存。了解其缓存管理机制对优化训练性能有启发。
-   **Flux2 Klein:** 需要关注这个模型的具体架构和特点，以及它与其他已支持模型（如CogVideoX）的性能对比。这反映了项目团队对前沿模型动态的跟进速度。

### 5. 基于项目背景的综合分析

-   **从“生成”到“编辑”的演进:** 结合README中“快速视频生成”的定位，Lucy Edit的加入是项目能力边界的自然延伸。这表明FastVideo不满足于只做生成器，而是希望成为一个更全面的视频创作工具，这与社区对“一站式”视频AI工具的需求相符。
-   **稳定性和生态是基石:** 修复训练Bug和移植新模型是项目发展的两条腿。前者保证了核心功能的健壮性（“快”且“稳”），后者则不断扩充生态（“多”种模型）。这两项工作共同支撑了项目作为“快速视频处理平台”的长期目标。
-   **社区协作模式:** 提交记录中出现了多位贡献者（Aryan Kumar, Gnav3852, Mac Lee）以及自动化合并机器人（mergify），表明项目采用了积极的社区协作和自动化CI/CD流程，这有助于加快开发迭代速度，与“Fast”的理念一脉相承。

## 详细提交记录

### [7f53942](https://github.com/hao-ai-lab/FastVideo/commit/7f539424cb8d327d3030e95a050140bb043b0ddf)

- **作者**: Aryan Kumar
- **时间**: 2026-06-09T22:21:43Z
- **提交信息**: [feat]: add Lucy Edit inference scaffold (#1363)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [19a838f](https://github.com/hao-ai-lab/FastVideo/commit/19a838f54f03b4270481d8beac5645218d0d8a24)

- **作者**: Aryan Kumar
- **时间**: 2026-06-09T22:01:22Z
- **提交信息**: [bugfix]: release VSA tile cache during training (#1434)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d922ab2](https://github.com/hao-ai-lab/FastVideo/commit/d922ab2cbc0d936b66d48691b733fd7215066b02)

- **作者**: William Lin
- **时间**: 2026-06-09T21:55:55Z
- **提交信息**: [model] Flux2 Klein Port (#1349)

Co-authored-by: Gnav3852 <63612880+Gnav3852@users.noreply.github.com>
Co-authored-by: Mac Lee <macthecadillac@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33816
- **最后更新**: 2026-06-09T23:23:14Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 3
- **主要提交者**: Dhruv Nair, Akshan Krithick, Hz_Zhang

## AI分析总结

好的，根据您提供的 `huggingface/diffusers` 仓库提交记录和README摘要，以下是昨日更新的要点分析：

### 1. 主要更新类型

- **重构 (Refactoring):** 这是昨日更新的绝对主体，共有4次提交涉及代码重构。
- **Bug修复 (Bug Fix):** 有1次提交专门修复了一个训练脚本中的崩溃问题。

### 2. 关键变更点及其与项目整体方向的关系

- **重构CI测试 (提交 1, 2, 3, 5):**
    - **变更点:** 对多个模型的Transformer和UNet测试进行了重构。涉及的模型包括：SD3、Skyreels、Lumina、Ominigen、Mochi、Chroma、LongCat、HiDream以及一个通用的 `unet_spatiotemporal`。
    - **与项目方向的关系:** `diffusers` 作为一个支持海量扩散模型的库，其核心挑战之一就是维护测试的健壮性和可维护性。随着模型数量激增（如README中提到的“state-of-the-art pretrained diffusion models”），测试代码很容易变得臃肿和重复。这次大规模的重构旨在**统一测试模式、减少代码冗余、提高测试执行效率**，从而确保库在不断扩展新模型时，其核心质量保障体系（CI）依然稳定可靠。

- **修复训练脚本Bug (提交 4):**
    - **变更点:** 修复了 `train_dreambooth_lora.py` 脚本在 `fp16` 混合精度训练下，执行验证步骤后导致梯度缩放器 (`GradScaler`) 崩溃的问题。
    - **与项目方向的关系:** DreamBooth + LoRA 是社区最常用的微调方法之一。该Bug会导致训练中断，严重影响用户体验。修复此问题直接**提升了库的稳定性和易用性**，确保用户能顺利完成微调任务，这与 `diffusers` 致力于提供“简单易用”的API和训练脚本的目标一致。

### 3. 对项目的影响和潜在意义

- **提升代码质量与开发效率:** 测试重构将显著降低未来添加新模型或修改现有模型时的测试维护成本，并减少因测试代码不一致导致的误报或漏报。这为项目的长期健康发展奠定了基础。
- **增强用户信任:** 修复DreamBooth训练脚本的Bug，直接解决了用户在实际使用中遇到的痛点，有助于提升用户对库的稳定性和可靠性的信心。
- **为后续扩展铺路:** 标准化的测试结构使得新模型的集成流程更加清晰和自动化，能够加速未来新模型（如README中提到的Stable Diffusion、Imagen等）的加入。

### 4. 值得关注的技术点

- **`fp16` 与 `GradScaler` 的交互细节:** 提交4揭示了一个非常隐蔽的Bug：在 `fp16` 模式下，LoRA层被强制保持在 `fp32` 精度。然而，验证函数 `log_validation` 在构建pipeline时，对共享的 `unet` 对象调用了 `.to(dtype=torch_dtype)`，导致这些 `fp32` 的LoRA参数被错误地降级为 `fp16`。这导致后续反向传播产生 `fp16` 梯度，而 `GradScaler` 期望处理 `fp32` 梯度，从而引发崩溃。这个修复展示了在混合精度训练中，**共享模型参数时精度管理的重要性**。
- **测试重构的模式:** 从提交信息（如“Refactor ... Tests”）和共同作者（Sayak Paul）来看，这是一次有计划的、系统性的测试清理工作。这种“先重构，后扩展”的模式是成熟开源项目的典型特征。

### 5. 基于项目背景，这些提交如何影响项目发展

- **强化“一站式”平台定位:** `diffusers` 的目标是成为“最先进的预训练扩散模型”的集大成者。通过重构测试，项目能够更高效、更安全地集成更多模型（如Skyreels、Lumina等），从而巩固其作为社区首选模型库的地位。
- **降低用户使用门槛:** 修复训练脚本Bug直接降低了用户进行模型微调的门槛。结合README中强调的“简单易用”设计哲学，这次修复确保了用户从“推理”到“训练”的整个流程都足够顺畅。
- **保障项目长期健康:** 随着模型数量爆炸式增长，测试的维护成本会线性增加。这次重构是对项目“技术债务”的一次主动偿还，确保了项目在快速迭代的同时，不会因测试问题而陷入混乱，为未来的可持续发展提供了保障。

## 详细提交记录

### [2c7efb9](https://github.com/huggingface/diffusers/commit/2c7efb95349296cf6bcce981ea036275a82a94df)

- **作者**: Dhruv Nair
- **时间**: 2026-06-09T12:30:23Z
- **提交信息**: [CI] Refactor SD3 Transformer Test (#13340)

* update

* update

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [c07f09c](https://github.com/huggingface/diffusers/commit/c07f09cf9f42b3364d7fa9ba39b0795e62de6011)

- **作者**: Dhruv Nair
- **时间**: 2026-06-09T11:58:16Z
- **提交信息**: [CI] Refactor Skyreels, Lumina, Ominigen, Mochi transformer tests (#13348)

* update

* update

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [47538fc](https://github.com/huggingface/diffusers/commit/47538fc21d9b8df6ada2482b7748f4377b8e9adc)

- **作者**: Dhruv Nair
- **时间**: 2026-06-09T11:35:32Z
- **提交信息**: [CI] Refactor Chroma , LongCat and HiDream Transformer Tests (#13345)

* update

* update

* update

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [e377c0a](https://github.com/huggingface/diffusers/commit/e377c0a4ab097b929470cbdca7835a6547fb7d80)

- **作者**: Hz_Zhang
- **时间**: 2026-06-09T10:43:08Z
- **提交信息**: Fix fp16 LoRA unscale crash after validation in train_dreambooth_lora.py (#13895)

When training with `--mixed_precision="fp16"` and `--validation_prompt`,
the first optimizer step after a validation run fails with
`ValueError: Attempting to unscale FP16 gradients`.

Under fp16, `cast_training_params` keeps the trainable LoRA params in
fp32. The in-loop validation pipeline is built with the same live `unet`
object, and `log_validation` then calls `pipeline.to(device, dtype=torch_dtype)`,
which downcasts those fp32 LoRA params back to fp16. The next backward
therefore produces fp16 grads and `GradScaler.unscale_` raises.

Drop the dtype cast from that `.to(...)` so the shared `unet` keeps its
fp32 LoRA params. This matches train_dreambooth_lora_sdxl.py, which moves
the validation pipeline with `.to(accelerator.device)` only.

Fixes #13124

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [3759fab](https://github.com/huggingface/diffusers/commit/3759fab56d3170a04d747e918a13e55fda6681e2)

- **作者**: Akshan Krithick
- **时间**: 2026-06-09T09:22:11Z
- **提交信息**: refactor unet_spatiotemporal tests (#13891)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
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


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12554
- **最后更新**: 2026-06-09T22:15:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 28903
- **最后更新**: 2026-06-09T23:52:41Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 23
- **主要提交者**: AndyLi429, Liangsheng Yin, Lianmin Zheng

## AI分析总结

好的，这是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bug Fixes):** 数量最多，覆盖了多个模块和硬件平台。
- **新功能/特性 (New Features/Enhancements):** 包括新的测试、监控指标、以及特定模型的支持改进。
- **性能优化 (Performance Optimizations):** 涉及CUDA Graph、内存使用、以及特定硬件（如AMD）的算子优化。
- **重构/代码清理 (Refactoring/Cleanup):** 移除旧的workaround，迁移测试代码。
- **文档/示例更新 (Documentation/Examples):** 更新了AMD平台的Qwen3.5使用指南。

### 2. 关键变更点及其与项目整体方向的关系

- **多硬件平台支持 (Multi-HW Support):**
    - **AMD:** 大量提交（`9ab7a64`, `2fef951`, `5babb90`, `17d8c58`）专注于修复AMD平台上的问题、优化算子（如用FP8 MHA替换FP8 MLA）、更新文档。这表明项目正积极扩展对AMD GPU的支持，并解决其特有的兼容性和性能问题。
    - **NPU (Ascend):** 提交 `fdcd28a`, `c6be251`, `cd6efcb` 专注于NPU平台，包括启用扩散模型测试、强化学习权重更新、以及修复Qwen3混合模型的MTP精度问题。这显示了项目向华为昇腾等国产AI芯片生态的拓展。
- **推测解码 (Speculative Decoding) 演进:**
    - 提交 `53a4b51`, `decb88e`, `2218622` 围绕推测解码技术进行迭代。包括修复GLM模型的NextN Draft模型维度、支持Frozen-KV MTP的Spec v2并移除旧的v1 worker、以及修复Spec v2的停止输出边界。这表明项目在持续优化和稳定其核心的推理加速技术。
- **性能与稳定性 (Performance & Stability):**
    - **CUDA Graph:** 提交 `4455abd` 支持FlashInfer的piecewise CUDA graphs，`fde4004` 修复了CUDA graph runner中batch size变化时的tensor重置问题，`d981b7b` 则避免在非CUDA设备上应用CUDA graph优化。这些提交旨在提升CUDA Graph的兼容性和鲁棒性，这是高性能推理的关键。
    - **内存优化:** 提交 `aa18a68` 通过使用 `channels_last_3d` 格式加速LTX-2 VAE解码并降低峰值内存，直接优化了扩散模型的内存效率。
- **监控与可观测性 (Observability):**
    - 提交 `badab6b` 为实验性的 `sgl-router` 增加了请求、TTFT（首Token生成时间）和工作节点指标，并集成了Grafana仪表盘。这为生产环境下的负载均衡和性能监控提供了基础，是项目走向成熟和可运维的重要一步。
- **测试与质量保障 (Testing & Quality):**
    - 提交 `ca716f4` 增加了TP（Tensor Parallelism）服务器GPU进程的回归测试，`1368717` 增加了chunked prefill的测试，`609f5f5` 增加了mixed-prefix GSM8K评估和CPU单元测试。这些提交显著增强了项目的测试覆盖，有助于防止回归，保证代码质量。

### 3. 对项目的影响和潜在意义

- **提升稳定性和可靠性:** 大量的Bug修复（特别是针对特定硬件和模型）将直接提升SGLang在不同场景下的稳定性和可用性，降低用户在生产环境中遇到问题的概率。
- **扩大硬件生态:** 对AMD和NPU的持续投入，使SGLang不再局限于NVIDIA GPU，能够服务于更广泛的用户群体，这对于项目的长期发展至关重要。
- **巩固核心优势:** 对推测解码和CUDA Graph的持续优化，巩固了SGLang在推理速度和效率方面的核心优势，使其在LLM推理框架竞争中保持领先。
- **迈向生产就绪:** 增加监控指标和Grafana集成，表明项目正在从研究原型向生产级推理服务框架演进，满足了企业级部署的需求。
- **降低使用门槛:** 更新AMD平台的文档（cookbook）和增加更多测试用例，有助于降低新用户的上手难度和开发者的贡献门槛。

### 4. 值得关注的技术点

- **`dflash piecewise cuda graphs support`:** 这是一个值得关注的技术点。`dflash` 可能是一种新的或优化的注意力机制，将其与CUDA Graph结合，可能带来显著的推理延迟改善。
- **`Frozen-KV MTP` 的Spec v2支持:** 这表明项目在探索更高级的推测解码架构，`Frozen-KV` 可能是一种优化KV Cache使用的技术，与MTP（Multi-Token Prediction）结合，有望进一步提升吞吐量。
- **`channels_last_3d` 优化:** 这是一个非常具体且有效的内存布局优化，展示了项目团队对底层硬件和算子库的深入理解，能带来立竿见影的性能提升。
- **`Defer DeepGEMM PDL setup to worker init`:** 将昂贵的初始化操作（如DeepGEMM的PDL设置）延迟到工作进程初始化时执行，这是一种常见的延迟优化技巧，可以加快主进程启动速度，提高资源利用率。

### 5. 结合项目背景，这些提交如何影响项目发展

根据README，

## 详细提交记录

### [365b7da](https://github.com/sgl-project/sglang/commit/365b7dab9a1759a3acac524d55931bc4dde5d4f7)

- **作者**: Muqi Li
- **时间**: 2026-06-09T23:52:35Z
- **提交信息**: fix(schema): update tokens_after_end (#27017)

Co-authored-by: zqlcode <1309223143@qq.com>

### [bc82086](https://github.com/sgl-project/sglang/commit/bc82086ef8c87f7b157f556a1aad2a982bd8b358)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-09T23:48:49Z
- **提交信息**: Remove FlashInfer GB transport workaround (#27453)

Signed-off-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [98fe7e3](https://github.com/sgl-project/sglang/commit/98fe7e326ed4ec7ea872f15e351c10611d23a5fe)

- **作者**: Wenqi
- **时间**: 2026-06-09T23:30:13Z
- **提交信息**: fix(gemma4): register image/video/audio token_regex for HF-expanded prompts  (#26320)

Co-authored-by: wenqi <wenqi@convergence.ai>

### [9ab7a64](https://github.com/sgl-project/sglang/commit/9ab7a64ee1e380997f49560caad038996a759e8a)

- **作者**: Thomas Wang
- **时间**: 2026-06-09T23:26:33Z
- **提交信息**: [AMD] Update amd qwen3.5 cookbook (#27660)

### [ca716f4](https://github.com/sgl-project/sglang/commit/ca716f4734dfe260e5d210aea8fb389c552b1710)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-09T23:25:27Z
- **提交信息**: Add TP server GPU process regression test (#27721)

### [53a4b51](https://github.com/sgl-project/sglang/commit/53a4b51f8ce0260c758120a6823502ee1b5513c2)

- **作者**: Yueming Yuan
- **时间**: 2026-06-09T23:13:37Z
- **提交信息**: Fix GLM NextN draft value head dim (#26049)

### [4455abd](https://github.com/sgl-project/sglang/commit/4455abd16403ef152a3ef4b9daac60dd324a1880)

- **作者**: David Wang
- **时间**: 2026-06-09T22:44:19Z
- **提交信息**: dflash piecewise cuda graphs support (#27468)

### [decb88e](https://github.com/sgl-project/sglang/commit/decb88e0e3069f332a5cd49f18b5b009b3e53963)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-09T22:30:20Z
- **提交信息**: Support spec v2 for Frozen-KV MTP; remove v1 worker (#27607)

Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [7f730ed](https://github.com/sgl-project/sglang/commit/7f730edfdccf859a6f3a7e39e4d25ef4bd1717fb)

- **作者**: Ricardo-M-L
- **时间**: 2026-06-09T22:24:39Z
- **提交信息**: fix: correct off-by-one in vocab boundary check for token validation (#22367)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: fzyzcjy <ch271828n@outlook.com>

### [fde4004](https://github.com/sgl-project/sglang/commit/fde4004429400051a555632858ddcaf950d71901)

- **作者**: weizhoublue
- **时间**: 2026-06-09T22:03:58Z
- **提交信息**: [Fix] Reset positions tensor in CUDA graph runner when batch size differs from captured size (#24401)

Signed-off-by: weizhoublue <weizhou.lan@daocloud.io>

### [2fef951](https://github.com/sgl-project/sglang/commit/2fef951fe8a86b27ab20a5fe2dfda20526e3ee69)

- **作者**: jacky.cheng
- **时间**: 2026-06-09T21:46:41Z
- **提交信息**: [AMD] Replace fp8 mla with fp8 mha kernel for diffusion model aiter backend (#23927)

### [4232294](https://github.com/sgl-project/sglang/commit/42322947aa32b99e3d8d98731a070507fe67b535)

- **作者**: ziang663
- **时间**: 2026-06-09T21:03:38Z
- **提交信息**: [BUG FIX]Fix DSA CPU offload mamba indices signature (#27645)

### [eb8dced](https://github.com/sgl-project/sglang/commit/eb8dceda44a50c89bb640a454fa0f937c59aa26b)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-09T20:52:30Z
- **提交信息**: Defer DeepGEMM PDL setup to worker init (#27671)

Co-authored-by: lmzheng <lmzheng@fb.com>

### [186f1e3](https://github.com/sgl-project/sglang/commit/186f1e300a68c3474691249d8c1eaa1a8a0a68a1)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-09T19:37:39Z
- **提交信息**: [CI] Move JIT kernel tests + benchmarks to test/registered/jit; add in-package guard (#27644)

### [8ae328e](https://github.com/sgl-project/sglang/commit/8ae328e5f0425a3c80ae930fd761400d3cdb3d22)

- **作者**: Bi Xue
- **时间**: 2026-06-09T18:26:48Z
- **提交信息**: [sgl] Fix kimi-k2.5 EAGLE3 MLA draft embeds for batched MM prefill (#27647)

### [5babb90](https://github.com/sgl-project/sglang/commit/5babb902a9587e1d96729b9b11d9a9541272499b)

- **作者**: Michael
- **时间**: 2026-06-09T17:31:00Z
- **提交信息**: [AMD] fix: handle per-frame 4D shift in native scale-shift kernel (#27581)

### [aa18a68](https://github.com/sgl-project/sglang/commit/aa18a68ac52cd3d4cb56bac551be4e43fe0d7516)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-09T15:26:40Z
- **提交信息**: [diffusion] Run LTX-2 VAE decode in channels_last_3d (faster decode, lower peak memory) (#27431)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [17d8c58](https://github.com/sgl-project/sglang/commit/17d8c5801d0ab9fb859c03dffe563a28f90f7c41)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-09T15:12:35Z
- **提交信息**: [AMD] Fix test_deepseek_r1_mxfp4_8gpu.py : disable async-assert probes on AMD CI (#27505)

### [badab6b](https://github.com/sgl-project/sglang/commit/badab6b136cc514663e9dc8abfb44a924f0e68e8)

- **作者**: Kangyan-Zhou
- **时间**: 2026-06-09T14:25:56Z
- **提交信息**: [router] Add request/TTFT/worker metrics + Grafana dashboard to experimental sgl-router (#27591)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [1368717](https://github.com/sgl-project/sglang/commit/1368717248846786af863a98244aaed394605831)

- **作者**: fzyzcjy
- **时间**: 2026-06-09T12:19:30Z
- **提交信息**: Add more testing for chunked prefill (#27506)

### [609f5f5](https://github.com/sgl-project/sglang/commit/609f5f549c3c6a4e837fc03ba0c02bc33eeb8eaa)

- **作者**: fzyzcjy
- **时间**: 2026-06-09T12:17:41Z
- **提交信息**: Add mixed-prefix gsm8k eval and its CPU unit test (#27502)

### [fdcd28a](https://github.com/sgl-project/sglang/commit/fdcd28a08d2dcc56fd0e59aaa91292b17bd7d76b)

- **作者**: Elizaveta Martirosian
- **时间**: 2026-06-09T12:01:45Z
- **提交信息**: [NPU] Enable consistency checking for diffusion tests (#27283)

Co-authored-by: Elizaveta Martirosian <elizaveta.martirosian@gmail.com>
Co-authored-by: Elizaveta Martirosian <you@example.com>

### [c6be251](https://github.com/sgl-project/sglang/commit/c6be251c5bc6d5285d10e97aea29c7d19e6a34f4)

- **作者**: McZyWu
- **时间**: 2026-06-09T08:52:36Z
- **提交信息**: [NPU] RL update_weights_from_disk/ tensor /distributed (#26717)

### [cd6efcb](https://github.com/sgl-project/sglang/commit/cd6efcb947d01bc761b31f7b579dcc7f1372abf3)

- **作者**: AndyLi429
- **时间**: 2026-06-09T07:47:23Z
- **提交信息**: [NPU][Bugfix] fix MTP accuracy regression on Qwen3 hybrid models (#27202)

### [2218622](https://github.com/sgl-project/sglang/commit/2218622f50f7a755aca20e470c6794ffa9de9322)

- **作者**: gq112
- **时间**: 2026-06-09T07:32:21Z
- **提交信息**: Fix spec v2 stop output boundary (#25980)

Co-authored-by: gss <2783977641@qq.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [d981b7b](https://github.com/sgl-project/sglang/commit/d981b7b9c43a1816e4ef17f8b8b39eb16e0d2546)

- **作者**: Zaili Wang
- **时间**: 2026-06-09T07:24:55Z
- **提交信息**: [Fix] Avoid applying cuda graph input-buffer registry on non-cuda devices (#27549)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1191
- **最后更新**: 2026-06-09T15:30:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 82361
- **最后更新**: 2026-06-10T00:02:42Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 28
- **主要提交者**: Charlie Fu, Kunshang Ji, Maria Guevara

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bugfix):** 数量最多，覆盖了模型加载、内存溢出、推理崩溃、CI测试等多个方面。
- **性能优化 (Perf/Kernel):** 针对特定模型和硬件（如H100、AMD ROCm）的算子融合与调优。
- **功能新增 (Feat):** 主要集中在Rust前端（新API端点、API密钥认证）和基准测试工具。
- **安全修复 (Security):** 修复了图像处理和音频处理中的安全漏洞。
- **文档更新 (Docs):** 新增了KV卸载的使用指南。
- **硬件/平台适配 (ROCm/XPU):** 持续优化对AMD和Intel GPU的支持，包括CI稳定性和新特性。
- **重构/清理:** 移除废弃代码、清理文档链接。

### 2. 关键变更点及其与项目整体方向的关系

- **核心推理引擎优化:**
    - **`[Kernel][Perf] Tune fused_moe FP8 config for Qwen3-Next-80B`**: 针对特定大模型（Qwen3-Next-80B）在H100上进行了FP8配置调优，在特定批次大小下性能提升25%。这直接服务于项目“快速、低成本”的目标，通过精细化的硬件适配榨取性能。
    - **`[Perf] fuse qk rmsnorm rope gate for qwen3.5`**: 对Qwen3.5模型进行算子融合，减少内核启动和数据搬运开销，提升推理速度。
    - **`[Kernel] Speed up silu_and_mul_per_block_quant`**: 通过warp-shuffle归约和向量化I/O加速一个关键激活函数，这是一个通用的性能提升，惠及所有使用该算子的模型。

- **模型支持与兼容性:**
    - **`[Bugfix] fix qwen3.5 ep weight loading`**: 修复了Qwen3.5模型权重加载的Bug，确保了对新模型的支持。
    - **`[Cohere] Fix Cohere2MoE weight loading`**: 修复了Cohere模型与新版Transformers库的兼容性问题，体现了项目紧跟上游生态，保持兼容性的努力。
    - **`Fix MiDashengLM TP>1 crash`**: 修复了特定模型在张量并行（TP）模式下的崩溃问题，提升了多GPU部署的稳定性。

- **硬件平台扩展 (ROCm & XPU):**
    - **`[ROCm][V2] Fix failed assertion in Llama models when using EAGLE`**: 修复了AMD GPU上使用投机解码（EAGLE）时的断言失败问题，提升了AMD平台的功能完整性。
    - **`[ROCm][Perf] Use fused softplus-sqrt-topk router under AITER fused-MoE`**: 为AMD GPU的MoE层引入融合路由算子，提升性能。
    - **`[WIP][XPU] upgrade torch-xpu to 2.12`**: 升级Intel GPU的PyTorch后端，紧跟Intel的软件栈更新。
    - 这些提交表明vLLM正积极扩展对AMD和Intel硬件的支持，践行“为所有人”提供服务的愿景，降低对NVIDIA硬件的依赖。

- **功能与安全性增强:**
    - **`[Rust Frontend] Add /tokenize and /detokenize endpoints`**: 新增了分词/逆分词API，使Rust前端功能更完善，向成为独立、高性能的推理服务器迈进。
    - **`[Rust Frontend] Support API key authentication`**: 为Rust前端增加了API密钥认证，提升了生产环境下的安全性。
    - **`[Security] Fix image EXIF orientation and tRNS transparency handling`**: 修复了图像处理中的安全漏洞，防止恶意图片导致信息泄露或拒绝服务。
    - **`[Security] Fix DoS via audio decompression bomb`**: 修复了音频处理中的拒绝服务漏洞，防止通过构造特殊音频文件耗尽服务器资源。

- **基础设施与CI:**
    - **`[CI/Docs] Remove stale disagg prefill links`**: 清理过时的文档链接，保持项目文档的整洁和准确性。
    - **`[ROCm][CI] Stabilize ModernBERT token-classification parity`**: 稳定AMD GPU上的CI测试，确保代码质量。

### 3. 对项目的影响和潜在意义

- **提升稳定性和可靠性:** 大量的Bug修复，特别是针对内存溢出（OOM）、模型加载失败、多GPU崩溃等关键问题的修复，直接提升了vLLM在生产环境中的稳定性和可靠性。
- **性能持续领先:** 针对热门模型（Qwen、Cohere）和硬件（H100、AMD GPU）的持续性能调优，巩固了vLLM作为高性能推理引擎的领先地位。
- **扩大硬件生态:** 对ROCm和XPU的持续投入，使得vLLM能够服务于更广泛的用户群体，不再局限于NVIDIA生态，这对于项目的长期发展至关重要。
- **增强安全性与可观测性:** 安全漏洞的修复和Rust前端新功能的加入（如API认证、分词端点），使得vLLM更适合企业级部署，满足了生产环境对安全和可观测性的要求。
- **推动技术演进:** 算子融合、FP8调优、投机解码修复等提交，反映了vLLM在LLM推理技术前沿的持续探索和落地。

### 4. 值得关注的技术点

- **`f

## 详细提交记录

### [d7607ad](https://github.com/vllm-project/vllm/commit/d7607ad2730ff26b5cb8730354179a4d42dc45d1)

- **作者**: Wentao Ye
- **时间**: 2026-06-09T22:47:06Z
- **提交信息**: [Bug] Fix deepseek v4 OOM issue (#44914)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [d955745](https://github.com/vllm-project/vllm/commit/d955745d58c2b8e8973ff96284d475f0a9f4cc6b)

- **作者**: Charlie Fu
- **时间**: 2026-06-09T21:53:46Z
- **提交信息**: [ROCm][CI] fix test_rope_kvcache_fusion.py (#44678)

Signed-off-by: charlifu <charlifu@amd.com>
Co-authored-by: Rohan Potdar <66227218+Rohan138@users.noreply.github.com>

### [e1ed89d](https://github.com/vllm-project/vllm/commit/e1ed89dbee7190f356c6f19da02e60bd457a365e)

- **作者**: Micah Williamson
- **时间**: 2026-06-09T21:12:06Z
- **提交信息**: Revert "[Kernel] Speed up silu_and_mul_per_block_quant with warp-shuf… (#45066)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [1c2ffc6](https://github.com/vllm-project/vllm/commit/1c2ffc6f8891809fa819d71ba360d08129d476ac)

- **作者**: Jimmy
- **时间**: 2026-06-09T21:00:07Z
- **提交信息**: feat(multi-turn-bench): add api_key and custom headers for multi turn benchmark (#44516)

Signed-off-by: Jimmy <jinmingyi1998@sina.cn>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: simon-mo <simon.mo@hey.com>

### [ca4cfd8](https://github.com/vllm-project/vllm/commit/ca4cfd873163cc1911f98385e776fba6e7300f9f)

- **作者**: Jiangyun Zhu
- **时间**: 2026-06-09T20:55:30Z
- **提交信息**: [Bugfix] fix qwen3.5 ep weight loading (#45002)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [c9c1540](https://github.com/vllm-project/vllm/commit/c9c1540e61b229def0d16395a3489c68a1581f0f)

- **作者**: Micah Williamson
- **时间**: 2026-06-09T18:30:52Z
- **提交信息**: [ROCm][V2] Fix failed assertion in Llama models when using EAGLE with `ROCM_AITER_FA` (#44936)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [c1d754d](https://github.com/vllm-project/vllm/commit/c1d754d681108096d8a125054f01a51afd60c618)

- **作者**: Dao007forever
- **时间**: 2026-06-09T18:05:36Z
- **提交信息**: [Mooncake] Use all HCAs on multi-NIC hosts instead of GPU-indexed RNIC selection (#43799)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [01d8cd9](https://github.com/vllm-project/vllm/commit/01d8cd92dd963140bddc1e82df7df55d0efa920c)

- **作者**: Fangzhou Ai
- **时间**: 2026-06-09T17:53:05Z
- **提交信息**: [ROCm][Perf] Use fused softplus-sqrt-topk router under AITER fused-MoE (#44945)

Co-authored-by: vLLM Contributor <contributor@vllm.ai>

### [a4b14b9](https://github.com/vllm-project/vllm/commit/a4b14b98c6f6a10bee1f48154baf4098b7e117ca)

- **作者**: SII-yangdian
- **时间**: 2026-06-09T17:41:26Z
- **提交信息**: [Kernel] Speed up silu_and_mul_per_block_quant with warp-shuffle reduction + vectorized I/O (#44173)

Signed-off-by: SII-yangdian <yangdian@sii.edu.cn>
Co-authored-by: SII-yangdian <yangdian@sii.edu.cn>

### [cf1c906](https://github.com/vllm-project/vllm/commit/cf1c90672404548aa3bc51f92c4745576a65ee26)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-06-09T16:34:44Z
- **提交信息**: [Security] Fix image EXIF orientation and tRNS transparency handling (#44974)

Signed-off-by: jperezde <jperezde@redhat.com>

### [766ce2b](https://github.com/vllm-project/vllm/commit/766ce2bb6bb614075fa7b0998c06d257f9c49f22)

- **作者**: Michał Ganczarenko
- **时间**: 2026-06-09T16:29:14Z
- **提交信息**: Fix MiDashengLM TP>1 crash in audio encoder attention (#44408)

Signed-off-by: Michał Ganczarenko <michal.ganczarenko@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [3d119f7](https://github.com/vllm-project/vllm/commit/3d119f78f77cd460c39a1c8ba8303724ad1f88bc)

- **作者**: Ronen Schaffer
- **时间**: 2026-06-09T16:20:23Z
- **提交信息**: [Docs] Add KV offloading usage guide (single- and multi-tier) (#44415)

Signed-off-by: Ronen Schaffer <ronen.schaffer@ibm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1b1359c](https://github.com/vllm-project/vllm/commit/1b1359c33269446f13c05da9a90c25174cbea590)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-06-09T16:18:53Z
- **提交信息**: [Security] Fix DoS via audio decompression bomb in speech-to-text endpoint (#44970)

Signed-off-by: jperezde <jperezde@redhat.com>

### [cad4ca1](https://github.com/vllm-project/vllm/commit/cad4ca12b89523793b009129d954492fdcaf1026)

- **作者**: Tyko Niemi
- **时间**: 2026-06-09T15:57:00Z
- **提交信息**: [Bugfix] Add X-Session-ID from conversation_id in multi-turn benchmark (#44663)

Signed-off-by: Tyko Niemi <tyko.niemi@amd.com>

### [b697119](https://github.com/vllm-project/vllm/commit/b6971198008e37637b80b0cdc183bf4bad11376e)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-09T15:52:36Z
- **提交信息**: [ROCm][CI] Stabilize ModernBERT token-classification parity against Hugging Face (#44040)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [b4c6dc6](https://github.com/vllm-project/vllm/commit/b4c6dc64548c46be62abcf5b0bafa7d6ec1a8ae6)

- **作者**: Kunshang Ji
- **时间**: 2026-06-09T15:51:39Z
- **提交信息**: [WIP][XPU] upgrade torch-xpu to 2.12 (#42262)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Signed-off-by: Kunshang Ji <jikunshang95@gmail.com>

### [2ee5106](https://github.com/vllm-project/vllm/commit/2ee51063722c9e6d28f71340966942394f330c0e)

- **作者**: Raushan Turganbay
- **时间**: 2026-06-09T15:01:04Z
- **提交信息**: Remove `raw_inputs` from transformers backend (#39425)

Signed-off-by: raushan <raushan@huggingface.co>

### [7a89b72](https://github.com/vllm-project/vllm/commit/7a89b72564a2c39d170b9478e947382216710ee2)

- **作者**: Jiangyun Zhu
- **时间**: 2026-06-09T14:12:17Z
- **提交信息**: [Perf] fuse qk rmsnorm rope gate for qwen3.5 (#44176)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [dc10e46](https://github.com/vllm-project/vllm/commit/dc10e467a9859f220ba9d36c31c50fb22bc38373)

- **作者**: Jee Jee Li
- **时间**: 2026-06-09T13:43:46Z
- **提交信息**: [Bugfix] Fix minimax_qk_norm_fusion (#44983)

### [ee4d7df](https://github.com/vllm-project/vllm/commit/ee4d7df2b5211448a4f9bb34e807c1dc1a360de1)

- **作者**: Terrence Zhao
- **时间**: 2026-06-09T13:32:18Z
- **提交信息**: [Cohere] Cohere2 moe parser fix (#44907)

Signed-off-by: Terrencezzj <terrence@cohere.ai>

### [3e8afdf](https://github.com/vllm-project/vllm/commit/3e8afdf78598afc8be999a6a049be3a5fe182e48)

- **作者**: Terrence Zhao
- **时间**: 2026-06-09T13:27:40Z
- **提交信息**: [Cohere] Fix Cohere2MoE weight loading when using Transformers ≥5.10 (#44747)

Signed-off-by: Terrencezzj <terrence@cohere.ai>

### [6690a0c](https://github.com/vllm-project/vllm/commit/6690a0c4de37ac965475a6ea90ad4271de77a767)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-06-09T13:10:06Z
- **提交信息**: [PD][Bugfix] Fix KV Cache sharing with HMA (#44629)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [1c23c42](https://github.com/vllm-project/vllm/commit/1c23c4203007d16d96b1f07847f5bf1b663ad0d7)

- **作者**: Maria Guevara
- **时间**: 2026-06-09T12:31:26Z
- **提交信息**: [Rust Frontend] Support Kimi K2 tool call IDs (#44901)

### [b12e42d](https://github.com/vllm-project/vllm/commit/b12e42d13277a691226e0f6654ad04f790acadd6)

- **作者**: xiangdong
- **时间**: 2026-06-09T12:20:32Z
- **提交信息**: [XPU][CI] Refine docker image build and pull/create lock mechanism in Intel GPU CI (#44481)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [69fdaff](https://github.com/vllm-project/vllm/commit/69fdaffbcd8cb406a9750685370a831fe8978a0a)

- **作者**: TanNgocDo
- **时间**: 2026-06-09T12:11:37Z
- **提交信息**: [Rust Frontend] Add /tokenize and /detokenize endpoints (#44222)

Signed-off-by: Tan Ngoc Do <darkknightkhtn2008@gmail.com>
Signed-off-by: TanNgocDo <darkknightkhtn2008@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [80e2c44](https://github.com/vllm-project/vllm/commit/80e2c4462dd9a94252b4b0061d00ed66908131c1)

- **作者**: Markus Hartikainen
- **时间**: 2026-06-09T12:06:56Z
- **提交信息**: [ROCm][Compile] Fuse AR + RMSNorm + per-group FP8 quant (+ DSv3.2 indexer fan-out) (#42864)

Signed-off-by: Markus Hartikainen <markus.hartikainen@amd.com>
Co-authored-by: Frida Andersson <fanderss@amd.com>

### [5b3807e](https://github.com/vllm-project/vllm/commit/5b3807e862fe70f51139ac518a5dd361e57de2e5)

- **作者**: Sage
- **时间**: 2026-06-09T11:39:52Z
- **提交信息**: [KV Events] Switch event structs from array to map encoding (#42892)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [59401ac](https://github.com/vllm-project/vllm/commit/59401ac9f18c246dceffce28bc878881179405e4)

- **作者**: Qiuyang Yue
- **时间**: 2026-06-09T11:15:51Z
- **提交信息**: [Kernel][Perf] Tune fused_moe FP8 config for Qwen3-Next-80B tp=4 on H100 (+25% at batch 96-512) (#44830)

Signed-off-by: Qiuyang Yue <yueqiuyang1389@gmail.com>

### [d841386](https://github.com/vllm-project/vllm/commit/d841386d272200dd381a5791833771db9a47adf7)

- **作者**: Chao-Ju Chen
- **时间**: 2026-06-09T10:15:20Z
- **提交信息**: [Rust Frontend] Support API key authentication (#44321)

Signed-off-by: RickyChen / 陳昭儒 <ricky.chen@infinirc.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [fff9210](https://github.com/vllm-project/vllm/commit/fff9210b2a5f0acbfbd6e972c985e81f04ae17c8)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-09T10:05:53Z
- **提交信息**: [CI/Docs] Remove stale disagg prefill links (#44918)

Signed-off-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [70db148](https://github.com/vllm-project/vllm/commit/70db1488c5d5f428b23b86223ec6bd4ec89b210f)

- **作者**: Ma Jian
- **时间**: 2026-06-09T09:23:17Z
- **提交信息**: [DSV4][XPU] Add MHC fused_post_pre support (#44144)

Signed-off-by: Ma Jian <jian1.ma@intel.com>

### [2385e14](https://github.com/vllm-project/vllm/commit/2385e140d6965c279b48f9c50f51e2fddfcf66bd)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-09T08:51:12Z
- **提交信息**: [ROCm][CI] Stabilize sleep-mode memory release (#43022)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [dab60fc](https://github.com/vllm-project/vllm/commit/dab60fc65894e7dadcc9a126f68b138af839d500)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-06-09T07:57:34Z
- **提交信息**: [Bugfix][CI] Fix `test_offloading_connector.py::test_fs_tiering_offloading` (#44903)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [996222f](https://github.com/vllm-project/vllm/commit/996222f4bffc7b0c1e50bb18b42e9f0f09867d7b)

- **作者**: wang.yuqi
- **时间**: 2026-06-09T07:46:11Z
- **提交信息**: [CI] Reorganize entrypoints CI (#44947)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-10
**监控日期**: 2026-06-09
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5052
- **最后更新**: 2026-06-09T23:45:52Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 9
- **主要提交者**: weizhoublue, Guanzhe (Leo) Huang, Juan Pablo Zuluaga

## AI分析总结

好的，这是对 `vllm-project/vllm-omni` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bugfix)**: 3项
- **性能优化 (Perf)**: 2项
- **功能新增 (Feature)**: 2项
- **硬件/平台支持 (Platform Support)**: 2项 (ROCm, XPU)
- **文档更新 (Documentation)**: 1项 (README typo fix)

### 2. 关键变更点及其与项目整体方向的关系

- **Bug修复与性能优化 (核心推理路径)**:
    - **Qwen3-TTS 热路径优化**: 修复了前缀缓存 (prefix-cache) 的OOM问题，并对talker/orchestrator组件进行了微优化。这直接提升了多模态对话模型的稳定性和效率。
    - **HunyuanImage3 CoT截断修复**: 修复了思维链 (CoT) 在解码器去除停止符时被错误截断的问题，确保了模型输出的完整性。
    - **LTX RMSNorm权重注册**: 修复了权重注册为buffer的问题，保证了模型正确加载和运行。
    - **Lance模型性能优化**: 对文生图 (t2i) 和图生图 (i2i) 流程进行了性能优化，提升了图像生成速度。
- **功能新增 (模型与能力扩展)**:
    - **SenseNova-U1 LoRA支持**: 为SenseNova-U1模型添加了低秩适配 (LoRA) 支持，这是对模型微调部署能力的扩展，符合项目“为所有人提供易用、快速、廉价的模型服务”的愿景。
    - **LTX-2.3 VAE并行解码**: 为LTX-2.3模型添加了VAE解码并行化功能，这能显著提升视频生成模型的解码速度。
- **硬件/平台支持 (生态扩展)**:
    - **ROCm CI增强**: 为ROCm (AMD GPU) 的持续集成 (CI) 添加了分组和环境特性，提升了AMD平台上的开发与测试效率。
    - **XPU Sage Attention后端**: 为Intel XPU添加了Sage Attention后端，扩展了对Intel硬件的支持，扩大了项目的硬件生态。
- **文档与配置修复**:
    - **HunyuanVideo I2V量化传播修复**: 修复了HunyuanVideo-1.5 I2V Transformer的量化配置传播问题，确保FP8层能正确启用，这对模型部署的精度和性能至关重要。
    - **README typo修复**: 修正了文档中的拼写错误，提升了项目文档质量。

### 3. 对项目的影响和潜在意义

- **提升核心模型稳定性和性能**: 对Qwen3-TTS、HunyuanImage3等关键模型的Bug修复和性能优化，直接提升了这些模型在实际服务中的稳定性和响应速度，增强了用户体验。
- **扩展模型生态**: 新增对SenseNova-U1的LoRA支持和LTX-2.3的并行解码，表明项目正在积极集成更多样化的多模态模型（文本、图像、视频），巩固其作为“全模态模型服务”平台的地位。
- **拓宽硬件兼容性**: 对ROCm和XPU的持续投入，降低了用户对特定硬件的依赖，使项目能服务于更广泛的用户群体，符合“为每个人”的宗旨。
- **提升开发与部署效率**: CI的改进和量化配置的修复，有助于开发者和运维人员更高效地进行开发和部署，减少配置错误。

### 4. 值得关注的技术点

- **Qwen3-TTS的Prefix-cache OOM防护**: 这是一个在长序列或高并发场景下常见且棘手的问题，其解决方案对其他模型的类似问题有参考价值。
- **LTX-2.3的VAE Decode并行化**: 这是视频生成模型加速的关键技术，其实现方式值得关注。
- **XPU的Sage Attention后端**: 这是Intel在AI加速领域的重要技术，其集成方式展示了项目对不同硬件加速库的兼容能力。
- **HunyuanVideo I2V的FP8量化传播修复**: 量化配置的正确传播是保证模型精度和性能一致性的关键，这个修复点出了模型部署中一个容易被忽视的细节。

### 5. 基于项目背景的综合分析

结合README中“Easy, fast, and cheap omni-modality model serving for everyone”的愿景，昨日的更新清晰地展示了项目在三个核心方向上的进展：

1.  **“Fast” (快速)**: 通过优化Qwen3-TTS、Lance和LTX-2.3的性能，直接提升了模型推理速度，这是“fast”的直接体现。
2.  **“Easy” (易用)**: 通过修复各种Bug（如CoT截断、权重注册、量化传播），降低了用户部署和使用模型时可能遇到的障碍，使服务更“easy”。同时，对LoRA的支持也简化了模型微调后的部署流程。
3.  **“Cheap” (廉价) & “for everyone” (为每个人)**: 通过扩展对ROCm (AMD) 和XPU (Intel) 等非NVIDIA硬件的支持，为用户提供了更多低成本的选择，使项目能服务于更广泛的硬件生态，真正践行“for everyone”的理念。

总的来说，昨日的更新是一次扎实的“修修补补”与“添砖加瓦”相结合的工作。在修复现有模型稳定性和性能问题的同时，积极引入新模型和硬件支持，稳步推进项目成为更强大、更普适的全模态模型服务平台

## 详细提交记录

### [57227dc](https://github.com/vllm-project/vllm-omni/commit/57227dc7f32e61110b120ab82931cfc51a65c65e)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-06-09T17:36:57Z
- **提交信息**: [Perf][Bugfix] qwen3-tts hot path: prefix-cache OOM guards + talker/orchestrator micro-opts (#3689)

Signed-off-by: JuanPZuluaga <juanz9312@gmal.com>
Co-authored-by: JuanPZuluaga <juanz9312@gmal.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [ca75623](https://github.com/vllm-project/vllm-omni/commit/ca75623ff3c95cb22b45ab3af487f50fcc6f2c30)

- **作者**: Zeng Chuang
- **时间**: 2026-06-09T15:30:25Z
- **提交信息**: [BugFix] Fix HunyuanImage3 CoT truncation when stop token stripped by detokenizer (#4260)

Signed-off-by: zengchuang <zengchuang3@huawei.com>

### [3753b21](https://github.com/vllm-project/vllm-omni/commit/3753b21c3d4a0581a08c7025ce7421e62a486c91)

- **作者**: Guanzhe (Leo) Huang
- **时间**: 2026-06-09T14:36:35Z
- **提交信息**: [Feature] LoRA support for SenseNova-U1 (#3971)

Signed-off-by: leohuang257 <masugchds@gmail.com>
Signed-off-by: Guanzhe (Leo) Huang <116847811+leohuang257@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Yuanheng Zhao <54058983+yuanheng-zhao@users.noreply.github.com>

### [e0fde88](https://github.com/vllm-project/vllm-omni/commit/e0fde88a5f582113963b1f3ee63997b780b13e9b)

- **作者**: TJian
- **时间**: 2026-06-09T14:17:55Z
- **提交信息**: [ROCm] [CI] Add group feature and envs feature (#4208)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [bf03413](https://github.com/vllm-project/vllm-omni/commit/bf03413c3651bc01dc1f690f951cf98eee61dd45)

- **作者**: Mu GuanLin
- **时间**: 2026-06-09T13:14:16Z
- **提交信息**: [Feat] Add vae-decode-parallel for LTX-2.3 (#4277)

Signed-off-by: mglyn <1203789601@qq.com>

### [f174ee5](https://github.com/vllm-project/vllm-omni/commit/f174ee54b06654136dbf06146598b87d4253fc87)

- **作者**: Chendi.Xue
- **时间**: 2026-06-09T11:28:18Z
- **提交信息**: [XPU] Add sage_attn backend (#3785)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [6ddaf61](https://github.com/vllm-project/vllm-omni/commit/6ddaf6188d1455ce306e88113610eb53dedb9473)

- **作者**: Samit
- **时间**: 2026-06-09T10:08:09Z
- **提交信息**: Fix README.md typo (#4292)

### [02eb7a4](https://github.com/vllm-project/vllm-omni/commit/02eb7a4ecb5cd602d1e3dc296b0ee03928e9218b)

- **作者**: Mu GuanLin
- **时间**: 2026-06-09T09:09:39Z
- **提交信息**: [Bugfix] Register LTX RMSNorm identity weight as buffer (#4278)

Signed-off-by: mglyn <1203789601@qq.com>

### [cb1c5a0](https://github.com/vllm-project/vllm-omni/commit/cb1c5a0c39c535f6ca3298ac57757db5293d7cdd)

- **作者**: yangjianjuan
- **时间**: 2026-06-09T08:31:57Z
- **提交信息**: [Perf] lance perf optimize (t2i & i2i) (#4214)

Signed-off-by: yangjianjuan <510818155@qq.com>

### [1b85df0](https://github.com/vllm-project/vllm-omni/commit/1b85df051027a18a413f7b7988dc76c89c184973)

- **作者**: weizhoublue
- **时间**: 2026-06-09T07:28:32Z
- **提交信息**: fix: Propagate Quantization Configuration to HunyuanVideo-1.5 I2V Transformer to Enable FP8 Layers (#4245)

Signed-off-by: weizhoublue <weizhou.lan@daocloud.io>

---
