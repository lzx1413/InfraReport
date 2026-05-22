# GitHub Stars 合并报告 - 2026-05-21

**合并日期**: 2026-05-22
**监控日期**: 2026-05-21
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


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1938
- **最后更新**: 2026-05-21T22:03:51Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: 鐘天楽, Ting, Bin Jia

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日（基于提交时间）更新的分析总结：

### 1. 主要更新类型
- **功能新增 (Feat):** 核心更新，引入了新特性。
- **发布管理 (Chore/Release):** 发布了新版本。

### 2. 关键变更点及其与项目整体方向的关系

- **`[f34b427]` 预计算多模态前向元数据 (Dataloader)**
  - **变更点:** 在数据加载器（Dataloader）中预先计算多模态前向传播所需的元数据。
  - **与项目关系:** 直接对应项目核心目标“**Scaling Any Modality Model Training**”（扩展任意模态模型训练）。通过将元数据计算从训练循环中前置到数据加载阶段，可以显著减少GPU在数据准备上的空闲等待时间，提升多模态训练的整体吞吐量和效率。

- **`[25f50f7]` 支持 Qwen-Image 模型**
  - **变更点:** 新增了对 `qwen-image` 模型架构的支持。
  - **与项目关系:** 体现了项目“**Model-Centric Distributed Recipe Zoo**”（以模型为中心的分布式配方动物园）的理念。通过集成新的、流行的多模态模型（如Qwen系列），VeOmni的“配方库”得到扩充，使其能够覆盖更广泛的用户需求和模型生态，增强了项目的通用性和吸引力。

- **`[6ab293e]` 发布 v0.1.10 版本**
  - **变更点:** 将上述两个功能（可能还包括其他未列出的修复或优化）打包，发布了新的稳定版本。
  - **与项目关系:** 标志着项目进入了一个新的迭代周期，将最新的研究成果和工程改进交付给社区用户，是项目持续发展和维护的体现。

### 3. 对项目的影响和潜在意义

- **性能与效率提升:** `f34b427` 中的优化是典型的性能提升手段。在多模态训练中，数据预处理（尤其是不同模态数据的对齐和元数据生成）往往是瓶颈。此改动有望直接提升训练速度，降低训练成本，这对于“Scaling”大规模训练至关重要。
- **生态扩展与易用性:** `25f50f7` 的支持降低了用户使用VeOmni训练Qwen-Image模型的门槛。这有助于吸引更多用户，并验证VeOmni框架的灵活性和可扩展性，证明其“配方”可以快速适配新的模型架构。
- **项目成熟度:** `v0.1.10` 的发布表明项目正在稳定迭代，从实验性代码向更可靠、更易用的工程化工具演进。

### 4. 值得关注的技术点

- **`precompute multimodal forward metadata in dataloader`:** 这是一个值得深入研究的工程优化点。它可能涉及对数据加载器（如PyTorch DataLoader）的定制，通过多进程或异步方式，在数据被送入GPU之前，完成模态对齐、掩码生成、位置编码等计算密集型操作。这体现了“以数据为中心”的优化思路。
- **`support qwen-image`:** 关注点在于如何将一个新的、可能具有独特架构（如视觉编码器、语言模型、连接器）的模型无缝集成到VeOmni的“Recipe Zoo”中。这涉及到模型注册、配置解析、分布式策略适配等一系列工程实现。

### 5. 基于项目背景，这些提交如何影响项目发展

- **强化核心竞争力:** 项目README强调“**Model-Centric Distributed Recipe Zoo**”和“**Scaling Any Modality Model Training**”。昨日的提交从两个维度强化了这一核心：
  - **横向扩展（广度）:** 通过支持Qwen-Image，扩展了“Recipe Zoo”的覆盖范围，证明了其“Any Modality”的潜力。
  - **纵向优化（深度）:** 通过优化Dataloader，提升了“Scaling”训练的效率，解决了大规模多模态训练中的关键性能瓶颈。
- **推动从研究到工程化:** 发布新版本 (`v0.1.10`) 是将内部研究成果（如性能优化、新模型支持）转化为用户可用产品的关键一步。这有助于项目从学术论文走向实际应用，吸引更多开发者和企业用户，形成良性社区生态。
- **验证设计理念:** 这些提交的成功实施，验证了VeOmni“以模型为中心”的设计理念是可行的。它表明，通过精心设计的“配方”和通用的分布式训练引擎，可以高效地支持并优化多种多样的多模态模型，而无需为每个模型重写训练代码。

## 详细提交记录

### [f34b427](https://github.com/ByteDance-Seed/VeOmni/commit/f34b42755c12fd4caff79a697084698b37d59359)

- **作者**: Ting
- **时间**: 2026-05-21T22:03:45Z
- **提交信息**: [model, data, trainer] feat: precompute multimodal forward metadata in dataloader (#772)

### [25f50f7](https://github.com/ByteDance-Seed/VeOmni/commit/25f50f7da5fab52a66a5b4d348485ef0d5515e98)

- **作者**: Bin Jia
- **时间**: 2026-05-21T08:28:15Z
- **提交信息**: [model] feat: support qwen-image (#770)

### [6ab293e](https://github.com/ByteDance-Seed/VeOmni/commit/6ab293ecdfdd90ef3941fc81065d9f947b5b4e4f)

- **作者**: 鐘天楽
- **时间**: 2026-05-21T07:19:25Z
- **提交信息**: [release] chore: release v0.1.10 (#759)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2281
- **最后更新**: 2026-05-21T16:45:33Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: helloyongyang

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **Bug修复**：两次提交均明确为“fix”，属于缺陷修复。

### 2. 关键变更点及其与项目整体方向的关系
- **修复动画生成中的调度器问题**：
  - `caf1056` 修复了 `WanStepDistillScheduler`（万步蒸馏调度器）的动画功能。
  - `4724697` 修复了通用的动画功能（`animate 77`，可能指代某个特定版本或配置的动画问题）。
- **与项目方向的关系**：LightX2V 是一个**轻量级视频生成推理框架**。动画生成是视频生成的核心功能。修复调度器问题直接保障了框架生成视频的**正确性和稳定性**，是支撑项目“轻量级”和“高效推理”目标的基础。

### 3. 对项目的影响和潜在意义
- **直接影响**：修复了用户在使用特定调度器（`WanStepDistillScheduler`）或特定动画配置时可能遇到的崩溃、错误或生成结果异常问题。
- **潜在意义**：
  - **提升可靠性**：使框架在更广泛的场景下能稳定运行，增强用户信心。
  - **为后续优化铺路**：调度器是控制生成过程的核心组件，修复其动画功能是进行性能优化或添加新功能（如更长的视频、更快的生成速度）的前提。

### 4. 值得关注的技术点
- **`WanStepDistillScheduler`**：这是一个名为“万步蒸馏”的调度器，暗示其可能采用了**知识蒸馏**技术来加速或简化视频生成过程。修复它表明项目正在积极维护和优化其核心算法组件。
- **`animate 77`**：这个编号可能指向一个特定的动画模块、API版本或内部测试用例。修复它说明项目有明确的版本管理和问题追踪机制。

### 5. 基于项目背景，这些提交如何影响项目发展
- **巩固核心能力**：作为“轻量视频生成推理框架”，稳定、正确的动画生成是立身之本。这些修复直接解决了用户可能遇到的核心痛点，避免了因基础功能缺陷而影响项目声誉。
- **推动技术落地**：`WanStepDistillScheduler` 这类高级调度器的修复，有助于将更前沿的生成技术（如蒸馏）稳定地集成到框架中，从而让用户能更便捷地使用这些技术，推动项目从“可用”向“好用”发展。
- **维护项目健康度**：持续的Bug修复表明项目处于活跃维护状态，这对于吸引开发者贡献、建立社区信任至关重要。

## 详细提交记录

### [caf1056](https://github.com/ModelTC/LightX2V/commit/caf1056d042931a50bf14c95d1501d3a5be926fa)

- **作者**: helloyongyang
- **时间**: 2026-05-21T16:45:01Z
- **提交信息**: fix animate WanStepDistillScheduler

### [4724697](https://github.com/ModelTC/LightX2V/commit/4724697a01d17d9de7930a84763bd51edbbbfc69)

- **作者**: helloyongyang
- **时间**: 2026-05-21T07:51:44Z
- **提交信息**: fix animate 77

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2087
- **最后更新**: 2026-05-21T17:35:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5652
- **最后更新**: 2026-05-21T22:48:54Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 6
- **主要提交者**: Prasun Gera, Lee Nau, Perkz Zheng

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **功能新增 (Feature)**:
    *   新增 `RMSNorm + RoPE` 融合算子，专为视频生成扩散模型（如 WAN）优化。
    *   新增 DeepSeek V4 稀疏 MLA (Multi-head Latent Attention) 解码内核。
    *   为 MoE (Mixture of Experts) 的 `trtllm` 后端添加 LoRa (Low-Rank Adaptation) delta 支持。
    *   恢复并重构了 CuTe-DSL 的 MLA 解码内核，并新增了 `sinks` 支持。
*   **Bug 修复 (Bug Fix)**:
    *   修复了 `cute-dsl` 的弃用警告，解决了日志刷屏问题。
    *   修复了 CuTe-DSL MoE 包装器中的引用循环，防止 CUDA 图资源泄漏。
*   **性能优化 (Performance Optimization)**:
    *   在 CuTe-DSL MoE 自动调优器中重新启用 `use_cold_l2_cache`，以获得更稳健的冷缓存性能。
*   **错误处理改进 (Error Handling Improvement)**:
    *   为 b12x MoE 内核添加了明确的错误提示，拒绝不支持的专家并行 (EP) 配置。

### 2. 关键变更点及其与项目整体方向的关系

FlashInfer 项目旨在为推理场景提供高性能 GPU 内核。这些提交紧密围绕此目标，主要聚焦于：

*   **扩展模型支持**: 新增的 `RMSNorm + RoPE` 融合算子（提交 `f6f01a4`）和 DeepSeek V4 稀疏 MLA 内核（提交 `9c76c99`）直接响应了业界对视频生成模型（如 WAN）和最新一代大语言模型（如 DeepSeek V4）的推理需求。这与项目“为推理提供高性能内核”的使命高度一致。
*   **提升推理效率和鲁棒性**: 对 MoE 内核的优化（提交 `41e5aa2`、`18f4534`）和 LoRa 支持（提交 `6f651b6`）旨在提升模型推理的吞吐量和稳定性，尤其是在生产环境下的冷启动和微调场景中。
*   **增强灵活性与兼容性**: 恢复并重构 CuTe-DSL MLA 内核（提交 `e91ac8f`）为用户提供了更多选择，允许在“模块化”和“整体式”实现之间切换，并增加了对 `sinks` 功能的支持，增强了与 TRT-LLM 后端的兼容性。
*   **改善开发者与用户体验**: 修复弃用警告（提交 `bc4dc97`）和添加明确的错误提示（提交 `3a81c3e`）直接提升了库的可用性和调试体验，降低了集成门槛。

### 3. 对项目的影响和潜在意义

*   **巩固在视频生成推理领域的地位**: `RMSNorm + RoPE` 融合算子的加入，使 FlashInfer 成为 WAN 等主流视频生成模型推理的关键加速库，有望吸引更多该领域的用户和贡献者。
*   **紧跟前沿模型架构**: 对 DeepSeek V4 稀疏 MLA 的支持，表明项目能够快速适配最新的模型架构（如稀疏注意力），这对于保持其在 LLM 推理领域的竞争力至关重要。
*   **提升生产环境可靠性**: 修复引用循环和优化冷缓存性能，解决了实际部署中可能遇到的资源泄漏和性能抖动问题，增强了项目在关键业务场景下的可靠性。
*   **降低集成成本**: 明确的错误提示和弃用警告修复，减少了开发者在集成 FlashInfer 时可能遇到的困惑和调试时间，有助于扩大用户基础。

### 4. 值得关注的技术点

*   **`use_cold_l2_cache` 机制**: 这是一个重要的性能调优技巧。在自动调优时清空 L2 缓存，可以模拟生产环境中“冷缓存”的真实情况，从而选出在各种条件下都表现稳健的 kernel 策略，而非仅在缓存命中率高时表现优异的策略。
*   **`weakref` 解决引用循环**: 使用 `weakref` 来打破 Python 对象间的强引用循环，是一种优雅且高效的内存管理方式，尤其适用于管理 CUDA 图等重量级资源，避免了依赖 Python 的垃圾回收机制可能带来的延迟和不确定性。
*   **`RMSNorm + RoPE` 融合的架构设计**: 该提交不仅实现了功能，还详细说明了其架构支持范围（SM80-SM121）、已知限制（`num_heads ≤ 32`）以及针对不同架构（如 Blackwell 的 FFMA2）的优化路径，体现了扎实的工程实践。
*   **稀疏 MLA 的实现**: 对 DeepSeek V4 稀疏 MLA 的支持，涉及了滑动窗口注意力（SWA）、压缩 KV 池、拼接稀疏索引等复杂技术，这代表了注意力机制工程实现的前沿方向。

### 5. 基于项目背景的分析：这些提交如何影响项目发展

*   **从通用推理向特定领域深化**: 项目最初可能更侧重于通用的 LLM 推理加速。`RMSNorm + RoPE` 融合算子的加入，标志着项目开始向**视频生成**等特定领域深化，提供针对性的优化方案，这有助于项目在更广阔的市场中建立影响力。
*   **从支持主流模型到支持前沿模型**: 对 DeepSeek V4 的支持，表明项目不再满足于仅支持已广泛

## 详细提交记录

### [41e5aa2](https://github.com/flashinfer-ai/flashinfer/commit/41e5aa29a0e218bde2e2045316ed88e3f4dc8ca2)

- **作者**: Lee Nau
- **时间**: 2026-05-21T22:48:49Z
- **提交信息**: feat(cute_dsl/moe): re-enable use_cold_l2_cache in CuteDslMoEWrapper TuningConfig (#3384)

## 📌 Description

Sets `use_cold_l2_cache=True` on the autotuner `TuningConfig` in
`flashinfer/fused_moe/cute_dsl/tuner.py`, matching TRT-LLM's
`CuteDslFusedMoENvfp4Runner.tuning_config`. With cold-L2 ON, the
autotuner flushes L2 between profile iterations and measures
conservative timings, so the picked tactic is robustly fast under
cold-cache conditions; without it, back-to-back iterations of the same
tactic benefit from L2-hit reuse and bias the pick toward tactics that
look fast during profiling but aren't faster in production.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/pull/3286
https://github.com/flashinfer-ai/flashinfer/pull/3340

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
* Improved tuner's cold L2 cache measurement behavior for more accurate
performance profiling.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3384?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [bc4dc97](https://github.com/flashinfer-ai/flashinfer/commit/bc4dc972713bb4a73ce8ea7d6b3206fafe995638)

- **作者**: Brayden Zhong
- **时间**: 2026-05-21T21:59:01Z
- **提交信息**: fix deprecation warnings from cute-dsl (#3333)

Fix https://github.com/flashinfer-ai/flashinfer/issues/3298

github.com/flashinfer-ai/flashinfer/pull/3300 seeems to be not tested on
hardware

Currently, it's flooding our logs (we use the FP4 GEMM)

Now, it will be fine:
```
[2026-05-15 13:17:21 TP5] KV Cache is allocated. #tokens: 4636736, KV size: 186.50 GB
[2026-05-15 13:17:21 TP5] Memory pool end. avail mem=30.16 GB
[2026-05-15 13:17:21 TP4] KV Cache is allocated. #tokens: 4636736, KV size: 186.50 GB
[2026-05-15 13:17:21 TP4] Memory pool end. avail mem=30.16 GB
[2026-05-15 13:17:21 TP2] KV Cache is allocated. #tokens: 4636736, KV size: 186.50 GB
[2026-05-15 13:17:21 TP2] Memory pool end. avail mem=30.16 GB
[2026-05-15 13:17:21 TP7] Running FlashInfer autotune with cache: /root/.cache/sglang/flashinfer/autotune/0.6.11/sm103/73d446d6004c95bb/rank_tp7_pp0_dp0.json
[2026-05-15 13:17:21 TP5] Running FlashInfer autotune with cache: /root/.cache/sglang/flashinfer/autotune/0.6.11/sm103/73d446d6004c95bb/rank_tp5_pp0_dp0.json
[2026-05-15 13:17:21 TP0] Running FlashInfer autotune with cache: /root/.cache/sglang/flashinfer/autotune/0.6.11/sm103/73d446d6004c95bb/rank_tp0_pp0_dp0.json
[2026-05-15 13:17:21 TP2] Running FlashInfer autotune with cache: /root/.cache/sglang/flashinfer/autotune/0.6.11/sm103/73d446d6004c95bb/rank_tp2_pp0_dp0.json
[2026-05-15 13:17:21 TP1] Running FlashInfer autotune with cache: /root/.cache/sglang/flashinfer/autotune/0.6.11/sm103/73d446d6004c95bb/rank_tp1_pp0_dp0.json
[2026-05-15 13:17:21 TP3] Running FlashInfer autotune with cache: /root/.cache/sglang/flashinfer/autotune/0.6.11/sm103/73d446d6004c95bb/rank_tp3_pp0_dp0.json
[2026-05-15 13:17:21 TP4] Running FlashInfer autotune with cache: /root/.cache/sglang/flashinfer/autotune/0.6.11/sm103/73d446d6004c95bb/rank_tp4_pp0_dp0.json
[2026-05-15 13:17:21 TP6] Running FlashInfer autotune with cache: /root/.cache/sglang/flashinfer/autotune/0.6.11/sm103/73d446d6004c95bb/rank_tp6_pp0_dp0.json
2026-05-15 13:17:24,197 - CUTE_DSL - WARNING - [handle_import_error] - Unexpected error during package walk: cutlass.cute.experimental
[2026-05-15 13:17:24 TP2] Unexpected error during package walk: cutlass.cute.experimental
2026-05-15 13:17:24,217 - CUTE_DSL - WARNING - [handle_import_error] - Unexpected error during package walk: cutlass.cute.experimental
[2026-05-15 13:17:24 TP5] Unexpected error during package walk: cutlass.cute.experimental
2026-05-15 13:17:24,231 - CUTE_DSL - WARNING - [handle_import_error] - Unexpected error during package walk: cutlass.cute.experimental
[2026-05-15 13:17:24 TP3] Unexpected error during package walk: cutlass.cute.experimental
2026-05-15 13:17:24,240 - CUTE_DSL - WARNING - [handle_import_error] - Unexpected error during package walk: cutlass.cute.experimental
[2026-05-15 13:17:24 TP6] Unexpected error during package walk: cutlass.cute.experimental
2026-05-15 13:17:24,357 - CUTE_DSL - WARNING - [handle_import_error] - Unexpected error during package walk: cutlass.cute.experimental
[2026-05-15 13:17:24 TP4] Unexpected error during package walk: cutlass.cute.experimental
2026-05-15 13:17:24,413 - CUTE_DSL - WARNING - [handle_import_error] - Unexpected error during package walk: cutlass.cute.experimental
[2026-05-15 13:17:24 TP7] Unexpected error during package walk: cutlass.cute.experimental
2026-05-15 13:17:24,512 - CUTE_DSL - WARNING - [handle_import_error] - Unexpected error during package walk: cutlass.cute.experimental
[2026-05-15 13:17:24 TP0] Unexpected error during package walk: cutlass.cute.experimental
2026-05-15 13:17:24,703 - CUTE_DSL - WARNING - [handle_import_error] - Unexpected error during package walk: cutlass.cute.experimental
[2026-05-15 13:17:24 TP1] Unexpected error during package walk: cutlass.cute.experimental
/usr/local/lib/python3.12/dist-packages/torch/distributed/c10d_logger.py:83: UserWarning: barrier(): using the device under current context. You can specify `device_id` in `init_process_group` to mute this warning.
  return func(*args, **kwargs)
[rank0]:[W515 13:17:30.584756157 ProcessGroupNCCL.cpp:5188] Guessing device ID based on global rank. This can cause a hang if rank to GPU mapping is heterogeneous. You can specify device_id in init_process_group()
[2026-05-15 13:17:32 TP2] FlashInfer workspace initialized for rank 2, world_size 8, backend trtllm
[2026-05-15 13:17:32 TP7] FlashInfer workspace initialized for rank 7, world_size 8, backend trtllm
[2026-05-15 13:17:32 TP4] FlashInfer workspace initialized for rank 4, world_size 8, backend trtllm
[2026-05-15 13:17:32 TP3] FlashInfer workspace initialized for rank 3, world_size 8, backend trtllm
[2026-05-15 13:17:32 TP6] FlashInfer workspace i
```

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
* Refined tensor-memory allocator pointer handling in GPU kernel
implementations to ensure correct pointer passing for memory allocation
and deallocation operations across multiple compute kernels.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3333)

<!-- review_stack_entry_end -->

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: b8zhong <b8zhong@users.noreply.github.com>

### [f6f01a4](https://github.com/flashinfer-ai/flashinfer/commit/f6f01a46bfc0eb0d4ecb434f2347630d2061ac95)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-05-21T20:28:45Z
- **提交信息**: feat: RMSNorm + RoPE fusion for WAN: flashinfer.diffusion_ops.fused_qk_rmsnorm_rope (#3148)

<!-- .github/pull_request_template.md -->

## 📌 Description
https://github.com/flashinfer-ai/flashinfer/issues/2971

Add a fused CUDA kernel for across-heads QK RMSNorm + 3D Rotary Position
Embeddings (RoPE) + V copy, targeting video generation DIT (Diffusion
Transformer) self-attention workloads such as WAN 2.1/2.2.

This kernel fuses three operations into a single launch:
1. **Across-heads RMSNorm** on Q and K (normalizes over the full
`hidden_dim = num_heads * head_dim`, not per-head)
2. **3D RoPE** with frame/height/width spatial decomposition (each head
dimension is split into temporal, height, and width frequency channels)
3. **V passthrough copy** to a contiguous output buffer

Optional **FP8 E4M3 quantized output** with SM89+ vectorized PTX
conversion and SM100+ Blackwell FFMA2 intrinsics (all with scalar
fallbacks for SM80+).

### API

User-facing API follows the `dsv3_ops` pattern — implementation lives in
`flashinfer/norm/` (alongside `rmsnorm`, `gemma_rmsnorm`, etc.) with a
re-export facade at `flashinfer/diffusion_ops/`:

```python
from flashinfer.diffusion_ops import fused_qk_rmsnorm_rope

q, k, v = fused_qk_rmsnorm_rope(
    qkv,               # [batch, seq_len, (nq+nk+nv)*head_dim] or [num_tokens, ...]
    q_weight, k_weight, # RMSNorm weights [num_heads_x * head_dim]
    ppf=5, pph=12, ppw=32,
    num_frame_channels=44, num_height_channels=42, num_width_channels=42,
    num_heads_q=24, num_heads_k=24, num_heads_v=24,
    head_dim=128,
)
```

### Benchmark Results (B200 (sm100), CUPTI)

```
python /workspace/flashinfer/benchmarks/bench_fused_qk_rmsnorm_rope.py
GPU: NVIDIA B200
Config: WAN 2.2 5B (num_heads=24, head_dim=128)

Shape                                                Eager (ms)   Fused (ms)    Speedup
------------------------------------------------------------------------------------------
B=1 5x12x32= 1920 (480p production (1920 tokens))        0.2420       0.0389      6.22x
B=1 5x12x8=  480 (480p small (480 tokens))               0.2363       0.0114     20.68x
B=1 5x48x32= 7680 (720p large (7680 tokens))             0.4948       0.1462      3.38x
B=2 5x12x32= 1920 (batch=2 (3840 tokens))                0.2864       0.0750      3.82x
B=1 5x6x4=  120 (tiny (120 tokens))                      0.2467       0.0045     54.67x
B=4 5x12x32= 1920 (batch=4 (7680 tokens))                0.4770       0.1462      3.26x
B=1 5x12x16=  960 (half seq (960 tokens))                0.2376       0.0207     11.49x
B=1 10x12x32= 3840 (double frames (3840 tokens))         0.2823       0.0749      3.77x
------------------------------------------------------------------------------------------
```

### Bug Fix

Found and fixed a bug in the NeoX (non-interleaved) RoPE path: `pos_id`
was computed from `dim_idx_x`'s mapped value but reused for `dim_idx_y`
without recomputation. Since the `(dim_idx * 2) & mask` mapping can
place adjacent elements in a float2 pair into different spatial slices
(e.g., height vs width), the y component received an incorrect position
ID. Fix: one line to recompute `pos_id` from `dim_idx_y`. The
interleaved path (used in production) was unaffected.

### Architecture Support

| SM | Architecture | Support Level |
|----|-------------|--------------|
| SM80 | Ampere (A100) | Full — BF16 path, FP8 via software emulation |
| SM86 | Ampere (RTX 3090) | Same as SM80 |
| SM89 | Ada (L40, RTX 4090) | + native FP8 conversion |
| SM90 | Hopper (H100) | Primary target |
| SM100 | Blackwell (B200, GB200, RTX 5090) | Primary target + FFMA2 |
| SM103 | Blackwell (B300, GB300) | Primary target + FFMA2 |
| SM110–SM121 | Blackwell variants | Expected to work (FFMA2 + FP8) |

### Known Limitations

- **`num_heads ≤ 32`**: The kernel uses one warp per head, so `max_heads
× 32 = 1024` threads per block (CUDA maximum). WAN 14B (40 heads) is
unsupported. Supporting it would require a kernel redesign (multi-head
per warp).
- **BF16 input only**: FP16/FP32 input would need new template
instantiations.
- **3D RoPE is specialized**: The frame/height/width decomposition
targets video-gen DIT models. This is not a general-purpose RoPE.

### Files Changed

```
include/flashinfer/fused_qk_rmsnorm_rope.cuh     # CUDA kernel + utilities (754 lines)
csrc/norm.cu                                    # TVM-FFI launcher (added to norm module)
csrc/flashinfer_norm_binding.cu                 # TVM-FFI export (added to norm module)
flashinfer/norm/fused_qk_rmsnorm_rope.py           # Python API with validation
flashinfer/norm/__init__.py                     # Re-export
flashinfer/diffusion_ops/__init__.py            # User-facing facade (like dsv3_ops/)
tests/norm/test_fused_qk_rmsnorm_rope.py           # 26 tests
benchmarks/bench_fused_qk_rmsnorm_rope.py          # Benchmark script
```

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/2971

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

**Test summary: 26 tests (25 pass, 1 xfail)**
- 8 interleaved correctness shapes (WAN 2.2 5B config)
- 3 NeoX (non-interleaved) correctness shapes
- V passthrough (exact BF16 copy)
- Destination-passing style
- 2D `[num_tokens, hidden]` input
- 3 FP8 output scales (1.0, 0.5, 2.0)
- RoPE-only mode (`is_qk_norm=False`)
- 3 multi-config: WAN 1.3B (12 heads), WAN 5B (24 heads), WAN 14B (40
heads — xfail, exceeds 32-head limit)
- 5 error-case validation tests

**Validated on 3 GPU architectures:**
- NVIDIA A100 (SM80, Ampere)
- NVIDIA L40S (SM89, Ada)
- NVIDIA H100 NVL (SM90, Hopper)
- NVIDIA B200 (sm100, Blackwell)

## Reviewer Notes

- The kernel compiles as part of the existing `norm` JIT module
(`gen_norm_module()`), so no new JIT spec or AOT registration is needed.
- The NeoX RoPE bugfix is a one-line change in
`fused_qk_rmsnorm_rope.cuh` — reviewers may want to verify the `pos_id`
recomputation logic for `dim_idx_y`.
- The `diffusion_ops/` facade follows the exact same pattern as
`dsv3_ops/` — pure re-export, no implementation.
- Future video-gen kernels (e.g., fused cross-attention, `rmsnorm_silu`
for WAN) can be added to `diffusion_ops/`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Fused Q/K RMSNorm + 3D rotary embeddings for video self-attention with
optional scaling and FP8 E4M3 output modes.
* Public Python API and package re-exports for easy invocation; outputs
can be preallocated or auto-allocated and V is passed through unchanged.
* GPU benchmark script to compare fused implementation vs. reference
timings across representative shapes.

* **Tests**
* Comprehensive CUDA test suite validating BF16/FP8 modes, RoPE
variants, correctness, output semantics, and many error cases.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Cursor <cursoragent@cursor.com>

### [e91ac8f](https://github.com/flashinfer-ai/flashinfer/commit/e91ac8f15da1d64e2e61ae7373e4943389e7b768)

- **作者**: Prasun Gera
- **时间**: 2026-05-21T20:20:49Z
- **提交信息**: Restore monolithic CuTe-DSL MLA decode alongside modular, gated by cute_dsl_impl= (#3296)

## Summary

PR #2805 refactored the monolithic CuTe-DSL MLA decode kernel into a
modular structure and removed the original implementation. The original
authors want it kept available because the modular path is still
maturing. This PR restores it under the existing
\`backend=\"cute-dsl\"\` user surface (no new backend name) and exposes
implementation selection via a new \`cute_dsl_impl=\` keyword argument
on \`trtllm_batch_decode_with_kv_cache_mla\`.

- **\"auto\"** (default): monolithic by default, automatically promoted
to modular when the call uses a modular-only feature (currently
\`sinks\`).
- **\"modular\"**: strict, always run the modular kernels.
- **\"monolithic\"**: strict, always run the monolithic kernels; raises
\`ValueError\` if the call uses any modular-only feature.

The dispatcher strips modular-only kwargs (\`sinks=None\`) before
forwarding to monolithic, so callers can pass \`sinks=\` unconditionally
without breaking the monolithic path.

### Sinks support on cute-dsl backend

\`trtllm_batch_decode_with_kv_cache_mla(sinks=...)\` on
\`backend=\"cute-dsl\"\` now constructs an \`AttentionWithSink\` variant
inside the modular standalone, instead of being rejected at the API
boundary. \`AttentionWithSink\` gained value-based
\`__hash__\`/\`__eq__\` (keyed on \`(type, shape, dtype)\`) so
\`@functools.cache\` on \`_compile_mla_kernel\` correctly reuses
compiled kernels across invocations with the same shape — without this,
a fresh variant per call hashed by object identity, JIT-recompiled the
kernel on every iteration, and made cuda-graph + sinks bench
measurements appear to hang.

### Layout

\`\`\`
flashinfer/cute_dsl/attention/
  monolithic/         - restored kernels (verbatim from before #2805,
                        relocated to live next to the modular code).
                        Includes the H<128 / Kimi K2.5 fix from #3235
                        backported.
  wrappers/           - existing modular standalone + wrapper.
  mla_dispatch.py     - new dispatcher in front of both impls.
\`\`\`

### Bench

\`benchmarks/bench_trtllm_gen_mla.py\` grows a focused 6-cell
\`with_sinks=True\` sub-sweep (B in {1,16,128} × S in {1024,8192} at
q_len=1, page=64, bf16) on top of the existing main sweep, instead of
doubling the full grid. Argument list deduplicated into a
\`common_kwargs\` dict so warmup and benchmark calls cannot drift.

Sinks overhead is ~free on both backends (worst case +1.9% at the
smallest cell). Cross-backend ranking does not change with sinks
enabled.

## Test plan

Existing standalone and public-API tests in
\`tests/attention/test_cute_dsl_mla_decode.py\` now parametrize over
modular/monolithic via a \`cute_dsl_impl\` fixture, doubling coverage on
the same shapes. New minimal sinks tests pin the auto/modular dispatch
branches and the monolithic+sinks \`ValueError\` contract. Wrapper sinks
numerics remain covered by the pre-existing
\`test_cute_dsl_mla_decode_attention_sink\`.

- [x] All pre-commit hooks pass on changed files (mypy, ruff check, ruff
format, EOF, whitespace, etc.).
- [x] \`pytest tests/attention/test_cute_dsl_mla_decode.py -v\` — full
sweep (544 cases incl. parametrized modular/monolithic) passes on B200.
- [x] \`pytest tests/attention/test_cute_dsl_mla_decode.py -k sinks\` —
3 new sinks integration tests pass.
- [x] \`pytest tests/attention/test_trtllm_gen_mla.py -v\` — unaffected,
passes.
- [x] H=64 / Kimi K2.5 backport on monolithic exercised via the existing
\`num_heads ∈ [128, 64]\` parametrization ×
\`cute_dsl_impl=monolithic\`.
- [x] Bench \`benchmarks/bench_trtllm_gen_mla.py --backend cute-dsl\`
and \`--backend trtllm-gen\` both run cleanly through the focused sinks
sub-sweep.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Optional "sinks" support for an alternate softmax path and a
cute_dsl_impl option to choose/auto-select modular vs monolithic MLA
decode implementations.
  * New monolithic CuTe-based MLA kernel targeting Blackwell hardware.

* **Performance / Reliability**
* Improved kernel caching/variant keying to enable reuse across variant
instances.
* Benchmark updated to exercise sinks-enabled and sinks-disabled paths.

* **Tests**
* Added tests for implementation selection, sinks behavior, and related
error/shape validations.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3296?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [6f651b6](https://github.com/flashinfer-ai/flashinfer/commit/6f651b63fce45753f47c0ed7d7651a6daa2f1cf8)

- **作者**: Daniel Stokes
- **时间**: 2026-05-21T20:19:16Z
- **提交信息**: feat: Add support for LoRa delta in MOE mxint4 x bf16, MXFP8 & BF16 to trtllm backend (#3153)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

This PR exposes a LoRa delta parameter in the `trtllm_*_moe_routed` APIs
for MXINT4xBF16 and BF16. It also returns the result of FC1 (after
activation) for the consumption when calculating LoRa deltas for FC2.

The intended use-case is for frameworks to implement calculating
per-token LoRa deltas and have the trtllm MOE backed consume them.

Key points:

1. LoRa deltas are expected in expanded format: `[num_tokens, top_k,
intermediate_size * 2]`
2. LoRa deltas are applied before activation, and only support swiglu
activation
3. Using LoRa requires frameworks to calculate the routing. This
prevents issues where different top-k results are calculated
4. The framework should parse the expanded FC1 output according to the
returned permuted indices map


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

* **New Features**
* Added LoRA GEMM1 delta support for routed Mixture of Experts
operations
  * Introduced MXINT4 block-scale MoE kernel implementation
* Enhanced MoE kernels with optional activation output return capability

* **Improvements**
* Enhanced bias-aware kernel configuration filtering for GEMM operations
  * Refined GEMM1 bias handling with row index permutation support
* Updated MoE kernel launchers with extended parameter plumbing for bias
modes

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3153?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [18f4534](https://github.com/flashinfer-ai/flashinfer/commit/18f45345ebb40529b52baad2a19a8a237d5edcd5)

- **作者**: Lee Nau
- **时间**: 2026-05-21T16:56:58Z
- **提交信息**: fix(cute_dsl): avoid MoE wrapper runner reference cycle (#3340)

<!-- .github/pull_request_template.md -->

## 📌 Description

`CuteDslMoEWrapper` currently passes `self._forward_with_tactic` as a
bound method into `CuteDslFusedMoENvfp4Runner`, creating a strong
reference cycle: `wrapper -> runner -> bound method -> wrapper`. When
the wrapper is used with `use_cuda_graph=True`, this can keep
wrapper-owned CUDA graph resources alive after user code has dropped the
wrapper, until Python cyclic GC eventually runs.

This PR replaces that bound-method callback with a weakref trampoline.
The runner can still call into a live wrapper, but it no longer owns the
wrapper lifetime. This prevents stale wrapper CUDA resources from
surviving across same-process tests or later autotune runs.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/pull/3286
https://github.com/flashinfer-ai/flashinfer/pull/3301
https://github.com/flashinfer-ai/flashinfer/pull/3252

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

Adds a focused regression test that warms a CUDA-graph wrapper, verifies
it is finalized before cyclic GC, and then runs a subsequent autotuned
wrapper call to ensure the output remains NaN-free.

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved handling and cleanup of CUDA-graph wrappers to prevent
resource leaks and provide a clear error when a wrapper is no longer
available.

* **Tests**
* Added lifetime tests covering CUDA-graph wrappers before and after
autotune; verify stable, non-NaN outputs during autotune.

* **Documentation**
* Updated comment about cold-L2 cache behavior and noted follow-up to
re-enable it once a related issue is addressed.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3340?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [3a81c3e](https://github.com/flashinfer-ai/flashinfer/commit/3a81c3ec57c510a8ca664c09f115de54acc2cdf0)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-05-21T10:47:02Z
- **提交信息**: Reject EP configurations in b12x MoE with a clear error (#3302)

<!-- .github/pull_request_template.md -->

## 📌 Description

The b12x fused MoE kernel does not yet support Expert Parallelism
(num_local_experts != num_experts). Previously, passing EP-sliced
weights would hit a confusing shape mismatch deep inside the CuTe DSL
compiled kernel or cause cudaErrorIllegalAddress. Add an explicit
NotImplementedError at the API boundary so users get an actionable
message directing them to use a different backend.

## 🔍 Related Issues

Fixes #3294 (temporary).

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
* Added validation to reject unsupported Expert Parallel configurations,
preventing execution with incompatible settings and improving error
clarity during initialization.

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3302)

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9c76c99](https://github.com/flashinfer-ai/flashinfer/commit/9c76c994b6d64fcfc071214ed5a29af124e680ee)

- **作者**: Perkz Zheng
- **时间**: 2026-05-21T07:52:55Z
- **提交信息**: Add DeepSeek V4 sparse MLA TRTLLM-GEN kernels (#3269)

## Summary
- Add DeepSeek V4 sparse MLA TRTLLM-GEN decode support for BF16 and
per-tensor FP8 paths.
- Plumb SWA and compressed KV pools, concatenated sparse indices, and
per-query sparse top-k lengths through FlashInfer.
- Add DeepSeek V4 sparse MLA tests covering SWA-only and compressed
top-k cases with variable Q/KV lengths.

## Tests
- `python -m pytest -q --tb=short -k 'not xqa and not cute and not
trtllm-native' tests/attention/test_trtllm_gen_sparse_mla_dsv4.py`: 57
passed
- `python -m pytest -q --tb=short -k 'not xqa and not cute and not
trtllm-native' tests/attention/test_attention_sink_blackwell.py`: 144
passed
- `python -m pytest -q --tb=short -k 'not xqa and not cute and not
trtllm-native' tests/attention/test_trtllm_gen_mla.py`: 7686 passed,
12672 deselected
- `python -m pytest -q --tb=short -n 8 -k 'not xqa and not cute and not
trtllm-native' tests/attention/test_trtllm_gen_attention.py`: 75736
passed, 30800 skipped


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added DeepSeek V4 sparse MLA decode support with variable top-k
behavior and sliding-window KV cache integration.
* Enhanced kernel selection with dynamic token-per-page support for
improved performance flexibility.

* **Tests**
* Added comprehensive test suite for DeepSeek V4 sparse MLA decode
across multiple configurations.

* **Chores**
  * Updated environment variable priority for CUBIN directory selection.
  * Added backward-compatibility alias for MLA decode function.

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3269)
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Perkz Zheng <perkzz@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3498
- **最后更新**: 2026-05-21T17:59:18Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Wenxuan Tan

## AI分析总结

好的，这是对仓库 `hao-ai-lab/FastVideo` 昨日提交记录的分析：

### 1. 主要更新类型
- **性能优化**：本次提交主要针对分布式训练场景下的权重加载过程进行优化。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更点**：优化了多节点训练中的分布式权重加载 (`distributed weight loading`)。
- **与项目方向的关系**：`FastVideo` 项目旨在提供高效的视频生成与训练框架。多节点训练是扩展模型规模、加速训练过程的关键技术。优化权重加载可以显著减少训练启动和恢复时的等待时间，直接提升了大规模训练的效率，这与项目追求“快速”的核心目标高度一致。

### 3. 对项目的影响和潜在意义
- **直接影响**：减少了多节点训练任务在初始化或从检查点恢复时的耗时。对于需要频繁调整或中断后恢复的大规模训练任务，这一优化能显著提升GPU利用率和整体训练吞吐量。
- **潜在意义**：降低了用户进行大规模分布式训练的门槛和成本。更快的启动和恢复速度意味着研究人员可以更频繁地进行实验迭代，从而加速视频生成模型的研发进程。

### 4. 值得关注的技术点
- **分布式权重加载**：在多节点训练中，模型权重通常需要从存储系统（如NFS、云存储）加载到所有GPU上。优化点可能包括：并行读取、减少节点间通信开销、更高效的数据分发策略等。这通常涉及到对PyTorch DDP/FSDP或DeepSpeed等分布式框架底层加载逻辑的改进。

### 5. 基于README背景，提交如何影响项目发展
- **强化核心竞争力**：`FastVideo` 的README强调其“快速”的特性。本次优化直接强化了这一核心卖点，使其在处理大规模视频生成模型训练时更具竞争力。
- **推动社区采用**：通过解决多节点训练中的一个常见痛点（加载慢），该项目对需要大规模算力的研究团队和企业用户更具吸引力，有助于扩大社区和用户基础。
- **支撑更大规模模型**：高效的分布式加载是训练更大、更复杂视频生成模型（如长视频、高分辨率视频）的基础设施保障。此提交为项目未来支持更大规模的模型训练铺平了道路。

## 详细提交记录

### [af2ee9c](https://github.com/hao-ai-lab/FastVideo/commit/af2ee9c78a55ba4922ac36f40e99d07438410904)

- **作者**: Wenxuan Tan
- **时间**: 2026-05-21T16:59:48Z
- **提交信息**: [feat] Optimize distributed weight loading in multi-node training (#572)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33680
- **最后更新**: 2026-05-21T23:03:32Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

好的，这是对 `huggingface/diffusers` 仓库昨日提交记录的分析总结。

### 提交记录分析总结

**提交:** `216e245`

**1. 主要更新类型**
*   **Bug修复 / 依赖管理优化**：本次提交主要解决了一个与依赖安装相关的持续集成（CI）问题。

**2. 关键变更点及其与项目整体方向的关系**
*   **变更点**：在持续集成（CI）配置中，使用 `uv`（一个快速的 Python 包安装器）的 `overrides` 功能，强制将 `tokenizers` 库的安装版本限制在 `<=0.23.0`。
*   **与项目方向的关系**：`diffusers` 项目重度依赖 `transformers` 库，而 `transformers` 又依赖 `tokenizers` 来处理文本。此变更确保了在特定的子流程（subs）中，`tokenizers` 的版本不会意外升级到 `0.23.0` 以上，从而避免了因新版本引入的潜在不兼容性或错误，保证了 CI 流程的稳定性和可靠性。这直接关系到项目的**开发效率和稳定性**。

**3. 对项目的影响和潜在意义**
*   **直接影响**：修复了 CI 中的一个潜在故障点，确保所有自动化测试和构建流程能够顺利通过。这对于一个大型开源项目至关重要，因为 CI 是代码质量的第一道防线。
*   **潜在意义**：这表明项目团队正在积极维护依赖的兼容性，并采用了现代化的工具（`uv`）来精细化管理依赖关系。这有助于减少因上游库更新导致的意外问题，提升开发体验。

**4. 值得关注的技术点**
*   **`uv` 工具的使用**：`uv` 是一个新兴的、性能优异的 Python 包管理器。`diffusers` 项目在 CI 中使用 `uv` 并利用其 `overrides` 功能，展示了项目对高效工具链的追求。`overrides` 是一种强大的依赖锁定机制，允许在不修改 `requirements.txt` 或 `pyproject.toml` 的情况下，临时或针对特定环境覆盖依赖版本。
*   **版本锁定策略**：通过 `<=0.23.0` 而非 `==0.23.0` 来锁定版本，是一种较为灵活的策略，允许安装该版本范围内的补丁版本，在保证兼容性的同时也能获取一些小的修复。

**5. 基于项目背景，这些提交如何影响项目发展**
*   **维护稳定性**：`diffusers` 作为一个广泛使用的扩散模型库，其核心价值在于稳定性和易用性。本次提交通过修复 CI 问题，直接保障了项目开发流程的稳定性，使得开发者可以更专注于新功能的开发和模型的支持，而不是被环境问题所困扰。
*   **提升开发效率**：一个稳定、快速的 CI 流程能显著缩短从代码提交到验证的周期。使用 `uv` 和 `overrides` 正是为了优化这一环节，让项目团队能够更快地迭代和发布新版本。
*   **保障用户体验**：虽然这是一个内部 CI 的修复，但它间接保障了最终用户的使用体验。因为 CI 的稳定意味着代码合并前经过了充分的测试，减少了将带有依赖问题的代码发布到生产环境的风险。

## 详细提交记录

### [216e245](https://github.com/huggingface/diffusers/commit/216e245c742cb226ba2a7d0721fb9b10569fa8e0)

- **作者**: Sayak Paul
- **时间**: 2026-05-21T12:50:37Z
- **提交信息**: ci: use uv overrides to make sure tokenizers install from <=0.23.0 under subs (#13767)

* ci: use uv overrides to make sure tokenizers install from <=0.23.0 under subs

* up

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 404
- **最后更新**: 2026-05-21T08:16:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12453
- **最后更新**: 2026-05-21T12:46:15Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增/脚本更新**：更新了与“acestep”相关的LoRA脚本。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：提交 `[9a17306]` 更新了 `acestep lora scripts`。
- **与项目方向的关系**：
  - **LoRA（Low-Rank Adaptation）** 是一种高效的模型微调技术，常用于在不改变基础模型权重的情况下，为特定风格或任务定制模型。这与DiffSynth-Studio作为视频/图像合成工具，需要支持用户自定义风格和效果的目标高度一致。
  - **“acestep”** 可能是一个特定的模型、算法或工作流名称。更新其LoRA脚本，意味着项目正在增强对该特定功能的支持，可能是为了优化其性能、修复问题或增加新的使用方式。

### 3. 对项目的影响和潜在意义
- **直接影响**：用户在使用与“acestep”相关的功能时，可以更稳定、更高效地应用LoRA微调，从而获得更好的合成效果。
- **潜在意义**：
  - **提升易用性**：更新脚本通常意味着简化了用户的操作流程或提供了更清晰的示例，降低了使用门槛。
  - **扩展生态**：持续更新LoRA脚本，表明项目正在积极构建一个围绕核心合成能力的“插件”或“风格”生态，让用户能更方便地分享和复用定制化模型。

### 4. 值得关注的技术点
- **LoRA脚本的更新内容**：虽然提交信息未详细说明，但值得关注的是更新了哪些具体参数、优化了哪些训练/推理步骤，或者是否引入了新的LoRA变体（如LoRA、LoCon、LoHa等）。这反映了项目在模型微调技术上的跟进和选择。

### 5. 基于README了解的项目背景，这些提交如何影响项目发展
- **项目定位**：DiffSynth-Studio是一个视频/图像合成工具，其核心是提供强大的生成能力。
- **影响**：此次更新直接服务于项目的核心目标。通过更新LoRA脚本，项目在“可控性”和“定制化”方面迈出了一步。这有助于：
  - **吸引高级用户**：那些希望使用特定风格（如“acestep”风格）进行创作的艺术家和开发者会因此受益。
  - **构建社区**：完善的LoRA支持是构建活跃社区的关键，因为用户可以基于此分享自己的定制模型。
  - **巩固技术基础**：持续优化LoRA这类高效微调方法，是保持项目在快速发展的AI生成领域竞争力的重要举措。

**总结**：本次提交是一次聚焦于特定功能（acestep）的LoRA脚本更新，属于功能增强和维护性质。它直接提升了项目的可定制性和易用性，符合DiffSynth-Studio作为强大且灵活的合成工具的发展方向。

## 详细提交记录

### [9a17306](https://github.com/modelscope/DiffSynth-Studio/commit/9a173067c643436737772fe31537933b9d546bfa)

- **作者**: Zhongjie Duan
- **时间**: 2026-05-21T08:00:35Z
- **提交信息**: update acestep lora scripts (#1453)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 28095
- **最后更新**: 2026-05-21T23:38:49Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 19
- **主要提交者**: amote-i, zijiexia, YC Yen-Ching Tseng

## AI分析总结

好的，作为专业的代码分析助手，我将结合项目背景，对 `sgl-project/sglang` 仓库昨日的提交记录进行分析和总结。

### 昨日更新要点总结

#### 1. 主要更新类型

-   **功能新增 (Feat):** 支持 `HybridLinearKVPool` 的分块前缀缓存处理；为 DeepSeek-V4 模型切换 FP4 推理后端。
-   **重构 (Refactor):** 注意力机制初始化顺序优化；模型运行器 `ForwardBatch` 解耦；MoE 模块中废弃 NPU 相关代码；JIT 内核清理。
-   **性能优化 (Perf):** 默认将 MegaMoE 配置为 W4A8 以最大化吞吐量；调整扩散模型的层卸载策略。
-   **Bug 修复 (Fix):** 限制 Kimi-K2.5 模型的专家融合仅适用于特定检查点；修复 Nixl 的 MLA key 和备份跳过问题；修复 CI 工具中的状态判断错误。
-   **文档更新 (Docs):** 更新 DeepSeek-V4 的 FP4 推理文档；删除 NPU 已废弃的参数文档；新增 NPU 性能分析和算子开发指南。
-   **CI/基础设施 (CI):** 改进 cherry-pick 机器人；启用 Nixl 解聚合测试；放宽 AMD CI 的超时限制；修复 CI 中的依赖冲突。

#### 2. 关键变更点及其与项目整体方向的关系

-   **核心架构解耦与重构 (提交 1, 2, 3, 4, 5, 23):**
    -   **变更:** 将 `ForwardBatch` 中的 `pool/backend` 引用迁移到 `ForwardContext`；统一 `FutureMap` 中的 `output_tokens_buf`；优化注意力机制的初始化顺序。
    -   **与项目方向的关系:** 这与 SGLang 追求高性能、低延迟推理的目标一致。通过解耦核心组件，可以更灵活地支持不同的注意力后端和内存池策略，为未来的硬件适配和性能优化奠定更清晰的基础。`FutureMap` 的改进则直接服务于推测解码 (Speculative Decoding) 等高级特性，提升其稳定性和效率。

-   **MoE (混合专家模型) 支持深化 (提交 6, 7, 8, 9, 10):**
    -   **变更:** 为 DeepSeek-V4 切换 FP4 推理后端；限制特定模型的专家融合；默认启用 W4A8 量化以最大化吞吐；废弃 NPU 相关的 MoE 代码；移除 LoRA MoE 中的同步操作。
    -   **与项目方向的关系:** SGLang 明确支持 DeepSeek 等大型 MoE 模型。这些提交表明项目正积极优化 MoE 模型的推理效率，特别是在量化（W4A8, FP4）和算子融合方面。废弃 NPU 特定代码，意味着 MoE 的实现正在向更通用、更统一的架构演进，这有助于降低维护成本并提升跨平台兼容性。

-   **硬件平台支持扩展 (提交 11, 16, 20, 21, 22, 27):**
    -   **变更:** 调整扩散模型在 NPU 上的层卸载策略；为 AMD 平台升级 AITER 库并放宽 CI 超时；新增 NPU 性能分析和算子开发指南；支持 NPU 上的 DeepSeek-OCR 模型。
    -   **与项目方向的关系:** 这表明 SGLang 正在积极扩展对非 NVIDIA GPU（如 AMD、Ascend NPU）的支持。提供详细的开发指南和性能分析工具，是吸引更多开发者和用户使用 SGLang 在这些平台上部署模型的关键步骤。对 DeepSeek-OCR 的支持也体现了项目紧跟最新模型发展的能力。

#### 3. 对项目的影响和潜在意义

-   **性能提升:** W4A8 量化默认配置和 MoE 代码清理将直接提升大模型的推理吞吐量，降低部署成本。
-   **稳定性增强:** `FutureMap` 的清理和 CI 工具的修复，减少了推测解码等高级功能出现错误的可能性，提升了整体系统的健壮性。
-   **开发者体验改善:** 核心架构的重构使得代码更清晰、模块化，降低了新贡献者理解和修改代码的门槛。NPU 和 AMD 平台的文档指南也极大地改善了这些平台上的开发者体验。
-   **生态扩展:** 对 AMD 和 Ascend NPU 的持续投入，是 SGLang 从单一 NVIDIA GPU 生态向多元化硬件生态发展的关键一步，有助于扩大其用户基础。

#### 4. 值得关注的技术点

-   **`HybridLinearKVPool`:** 这是一种新的 KV 缓存管理策略，结合了分块前缀缓存，可能对处理长序列和共享前缀的场景有显著的性能提升。
-   **`FutureMap` 重构:** 这是 SGLang 实现高效推测解码的核心数据结构。本次重构（`#25879`, `#25922`, `#25962`）统一了其行为并修复了潜在问题，值得深入理解其设计。
-   **W4A8 量化:** 这是目前大模型推理中非常流行的量化方案，在保持较低精度损失的同时，能显著提升计算和内存效率。SGLang 将其作为 MegaMoE 的默认配置，体现了对实用性的追求。
-   **`forward_npu` 废弃:** 这是一个重要的架构决策信号。它意味着 SGLang 正在将 NPU 的支持整合

## 详细提交记录

### [7cf193f](https://github.com/sgl-project/sglang/commit/7cf193fe1faf681f76eaa68f01a13a524c7e8b27)

- **作者**: nohup
- **时间**: 2026-05-21T23:17:26Z
- **提交信息**: feat: support HybridLinearKVPool in chunked prefix cache handling (#25753)

### [d765dfd](https://github.com/sgl-project/sglang/commit/d765dfd043a47334a121a83ebab04ccc8f3311ca)

- **作者**: Cheng Wan
- **时间**: 2026-05-21T23:03:42Z
- **提交信息**: refactor(attn): init hisparse_coordinator before attn_backend; replace lazy property with init-time capture (#26012)

Co-authored-by: Claude Sonnet 4.6 (1M context) <noreply@anthropic.com>

### [c5251a9](https://github.com/sgl-project/sglang/commit/c5251a98a9d499d600beb557835ac5874e0c3f36)

- **作者**: Cheng Wan
- **时间**: 2026-05-21T21:01:49Z
- **提交信息**: feat(model_runner): remove pool/backend refs from ForwardBatch via ForwardContext (#25983)

Co-authored-by: Claude Sonnet 4.6 (1M context) <noreply@anthropic.com>

### [44ec2ee](https://github.com/sgl-project/sglang/commit/44ec2ee18dc456a18b0f1f6ac6f03472c12cee60)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-21T20:56:44Z
- **提交信息**: [core] Unify output_tokens_buf in FutureMap (#25922)

### [c9a0e55](https://github.com/sgl-project/sglang/commit/c9a0e55eb597f3fe1a29fbeae546b2b294c16355)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-21T20:56:22Z
- **提交信息**: [Spec] Polish FutureMap after #25879: rename callback, async guard, cleanup (#25962)

### [17dadeb](https://github.com/sgl-project/sglang/commit/17dadebd4e53f78f849841895b91a976a25f6761)

- **作者**: zijiexia
- **时间**: 2026-05-21T20:51:40Z
- **提交信息**: [Docs] DeepSeek-V4: switch H200 FP4 Pro to flashinfer_mxfp4, Flash Balanced too (#25923)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [1a85586](https://github.com/sgl-project/sglang/commit/1a85586738181212829fd4ddb776495eeef76eee)

- **作者**: Jimmy Shong
- **时间**: 2026-05-21T20:07:45Z
- **提交信息**: [Fix]: Restrict Kimi-K2.5 shared-experts fusion to Quark MXFP4 checkpoints (#25974)

### [81d686d](https://github.com/sgl-project/sglang/commit/81d686d9fa2f5602ae4cfac1430a96f3195d8b17)

- **作者**: Yuhao Yang
- **时间**: 2026-05-21T18:54:16Z
- **提交信息**: Default MegaMoE to W4A8 for Max-Throughput recipe (#26004)

### [b765fae](https://github.com/sgl-project/sglang/commit/b765faee30490ad3e49124257457603b265279da)

- **作者**: Cheng Wan
- **时间**: 2026-05-21T17:25:17Z
- **提交信息**: [MoE Refactor] deprecate forward_npu and NpuFuseEPMoE (#25678)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [a24c374](https://github.com/sgl-project/sglang/commit/a24c374f844455ba1a6994a94b491a36ccb8afea)

- **作者**: Ethan (Yusheng) Su
- **时间**: 2026-05-21T15:58:57Z
- **提交信息**: [lora] Remove synchronous .any().item() guard in LoRA MoE prefill path (#25531)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [ca9dc17](https://github.com/sgl-project/sglang/commit/ca9dc17be497da8f96a0e0a87e75ef025830fa09)

- **作者**: Mick
- **时间**: 2026-05-21T15:48:58Z
- **提交信息**: [diffusion] chore: adjust layer wise-offload strategy (#25930)

### [049bb83](https://github.com/sgl-project/sglang/commit/049bb83134b39fea1a31a5cccf66ed717257af3a)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-21T14:58:21Z
- **提交信息**: [CI] bot-cherry-pick: surface created PR number/URL in job summary (#26001)

Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>

### [32f996b](https://github.com/sgl-project/sglang/commit/32f996b75a77b0661b5311b2b9fdf12494bca173)

- **作者**: liuxianglong17
- **时间**: 2026-05-21T14:10:23Z
- **提交信息**: Avoiding the problem of printing a large number of compatibility warn… (#25956)

### [caa9f08](https://github.com/sgl-project/sglang/commit/caa9f082940819d4da0fc29cfdd376971ead5166)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-21T14:01:42Z
- **提交信息**: [CI] Force-reinstall nvidia-cutlass-dsl-libs-cu13 last to avoid wheel-mix TypeError (#25958)

Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [ac83d8a](https://github.com/sgl-project/sglang/commit/ac83d8a3392ae3881b645e3b7597aee617d018c3)

- **作者**: amote-i
- **时间**: 2026-05-21T12:20:29Z
- **提交信息**: docs: delete deprecated args from npu supported features (#25995)

### [32352f7](https://github.com/sgl-project/sglang/commit/32352f7edfd8b236f2a7d257966f6890d7ae4ecf)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-21T12:10:12Z
- **提交信息**: [CI] Fix bot-cherry-pick: use state == "MERGED" instead of invalid `merged` field (#25987)

### [fbebdd5](https://github.com/sgl-project/sglang/commit/fbebdd5105dafde32e0cada86184b6c53458e98a)

- **作者**: Shangming Cai
- **时间**: 2026-05-21T11:29:24Z
- **提交信息**: [CI] Enable nixl disaggregation test for decode radix cache (#25990)

### [2e0d2d4](https://github.com/sgl-project/sglang/commit/2e0d2d4c18f6987a4e64801105ba5765b52d4111)

- **作者**: loading66
- **时间**: 2026-05-21T11:08:10Z
- **提交信息**: [NPU][DOCS]Add best practice and benchmark result parameter description (#25875)

### [64f21b1](https://github.com/sgl-project/sglang/commit/64f21b1589c04fe2d65708041bd2b4c91312c743)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-21T10:32:57Z
- **提交信息**: [CI] Improve bot-cherry-pick: accept PR number, require merged, explicit title (#25981)

### [8562d5a](https://github.com/sgl-project/sglang/commit/8562d5ae94e57ae19efafce081a178a19d9d5395)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-05-21T09:32:51Z
- **提交信息**: [AMD] Relaxing Timeout for AMD stage-a (#25978)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: Bingxu Chen <Bingxu.Chen@amd.com>
Co-authored-by: bingxche <bingxche@amd.com>

### [f66881f](https://github.com/sgl-project/sglang/commit/f66881f03c171a4c956faa49fb635b464cc361cc)

- **作者**: jianzhao-xu
- **时间**: 2026-05-21T09:32:25Z
- **提交信息**: [NPU]Ascend NPU Performance Profiling Guide and Ascend NPU Operator Development Guide (#25384)

### [e72e314](https://github.com/sgl-project/sglang/commit/e72e3145a0a056eaf43da75111e043341d98801b)

- **作者**: Bingxu Chen
- **时间**: 2026-05-21T09:10:43Z
- **提交信息**: [AMD] Upgrade AITER (#25896)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [baeac17](https://github.com/sgl-project/sglang/commit/baeac179f781f464d19f258c0aaed78e83caaa0e)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-21T08:51:40Z
- **提交信息**: [Spec] Route seq_lens through FutureMap; drop verify_done.wait (#25879)

### [19f55c0](https://github.com/sgl-project/sglang/commit/19f55c0e6d6fe5cf9a0f9ab6fc148cc004facb7b)

- **作者**: DarkSharpness
- **时间**: 2026-05-21T08:14:31Z
- **提交信息**: [Refactor] major JIT kernel clean up for dsv4 (#25884)

Co-authored-by: Claude <noreply@anthropic.com>

### [1b3d8da](https://github.com/sgl-project/sglang/commit/1b3d8da827165d599ea2f8867e48723d00eab00c)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-21T08:13:37Z
- **提交信息**: cap API quota for runner-utilization / amd-ci-job-monitor (#25965)

### [c3f9bc9](https://github.com/sgl-project/sglang/commit/c3f9bc9818c935975995baa6fb1bbc26ffaffacf)

- **作者**: hxie
- **时间**: 2026-05-21T07:48:28Z
- **提交信息**: Fix nixl mla key and backup skipping (#24376)

### [b9ae835](https://github.com/sgl-project/sglang/commit/b9ae8353d2af311a6484c96399966b59274c1bf5)

- **作者**: 看海的人
- **时间**: 2026-05-21T07:21:20Z
- **提交信息**: [NPU] Support model DeepSeek-OCR and DeepSeek-OCR-2 (#25257)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1178
- **最后更新**: 2026-05-21T19:54:12Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 80669
- **最后更新**: 2026-05-21T23:58:50Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 16
- **主要提交者**: Zheng Luo, velonica0, xiangdong

## AI分析总结

好的，作为专业的代码分析助手，以下是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

-   **Bug修复 (Bugfix):** 5项
-   **性能优化 (Perf):** 2项
-   **功能新增 (Feature):** 1项
-   **前端/集成 (Frontend):** 1项
-   **核心架构 (Core):** 1项
-   **CI/测试 (CI/Test):** 4项
-   **弃用/清理 (Deprecation):** 1项
-   **硬件适配 (Hardware Support):** 3项 (CPU, XPU, RISC-V)
-   **其他修复:** 1项 (FlashInfer/TRTLLM集成)

### 2. 关键变更点及其与项目整体方向的关系

项目目标：**Easy, fast, and cheap LLM serving for everyone** (为所有人提供简单、快速、廉价的LLM服务)。

-   **性能与效率 (Fast & Cheap):**
    -   `[Perf] zeros -> empty`: 通过将张量初始化从`zeros`改为`empty`，减少了不必要的内存清零操作，直接提升了性能。这符合“快速”和“廉价”（降低计算开销）的目标。
    -   `[Perf] [Hybrid] Fused Triton kernel for GPU-side Mamba state postprocessing`: 为Mamba模型（一种状态空间模型）引入了融合的Triton内核，用于GPU端的状态后处理。这直接优化了特定模型架构的性能，体现了项目对新兴模型的支持和性能追求。

-   **易用性与可靠性 (Easy & Reliable):**
    -   `[Bugfix] Zero stale is_prefilling in padded CUDA graph rows for Mamba`: 修复了Mamba模型在CUDA Graph中一个可能导致错误的预填充状态问题，提升了模型的稳定性和正确性。
    -   `[Bugfix] Use correct logprobs for logprob_token_ids`: 修复了logprobs计算中的错误，确保了API返回结果的准确性，这对用户（尤其是开发者）至关重要。
    -   `[Bugfix] Add early validation to reject incompatible runner types for embedding models`: 增加了早期验证，防止用户为embedding模型配置不兼容的运行器，提升了用户体验和错误提示的清晰度。
    -   `[Feature] Add --cpu-distributed-timeout-seconds CLI Option`: 新增了CPU分布式超时时间的CLI选项，增强了在CPU环境下部署的灵活性和可控性，降低了使用门槛。

-   **硬件支持与生态扩展 (For Everyone):**
    -   `[CPU][RISC-V] Add VLEN=256 support to RVV attention kernels`: 为RISC-V架构的CPU增加了对256位向量长度的支持，扩展了vLLM的硬件覆盖范围，向“为所有人”的目标迈进。
    -   `[XPU] ...`: 多项针对Intel XPU（GPU）的修复和依赖更新，表明项目正在积极适配和稳定对Intel硬件的支持。
    -   `Disable build isolation to bypass CUDA related deps for vllm-tpu`: 为TPU（Google的AI加速器）构建时绕过CUDA依赖，简化了TPU用户的安装流程，体现了对多样化硬件平台的支持。

-   **架构与集成 (Core & Frontend):**
    -   `[Core] Add native ModelExpress load format`: 新增了原生`ModelExpress`加载格式，这可能是为了支持一种新的或特定的模型序列化格式，增强了模型加载的灵活性。
    -   `[Frontend] Rework fastokens integration`: 重构了与`fastokens`（一个高性能分词库）的集成，这可能会影响API的响应速度和整体性能。
    -   `[Deprecation] Mark env vars covered by --moe-backend / --linear-backend`: 将一些环境变量标记为弃用，引导用户使用更统一的CLI参数，简化了配置方式，提升了易用性。

### 3. 对项目的影响和潜在意义

-   **稳定性提升：** 多个Bug修复（特别是Mamba和logprobs相关）直接提升了服务的稳定性和输出结果的正确性，这对于生产环境部署至关重要。
-   **性能边际改善：** `zeros -> empty`这类优化虽然看似微小，但在大规模部署中能累积显著的性能提升和资源节省。
-   **硬件生态扩展：** 对RISC-V和Intel XPU的持续投入，表明vLLM不满足于仅支持NVIDIA GPU，而是致力于成为一个真正跨平台的LLM推理引擎，这对其长期发展和社区吸引力有重大意义。
-   **用户体验优化：** 新增CLI选项、早期验证和弃用旧环境变量，都旨在让用户更简单、更直观地使用vLLM，降低了学习成本和出错概率。
-   **模型支持深化：** 对Mamba模型的专项优化（Bug修复和性能优化）表明，vLLM正在紧跟模型架构的发展趋势，不仅支持Transformer，也积极优化状态空间模型等新架构。

### 4. 值得关注的技术点

-   **Mamba模型的双重优化：** 同时有Bug修复和性能优化提交，说明Mamba模型是当前开发的重点之一，其CUDA Graph和Triton内核的实现值得关注。
-   **`fastokens`集成重构：** 这是一个前端核心组件的改动，可能会影响所有用户的tokenization性能，值得关注其后续效果。
-   **`ModelExpress`加载格式：** 这是一个

## 详细提交记录

### [39d5fa9](https://github.com/vllm-project/vllm/commit/39d5fa96a7c687f9ed7e14a5a52064965356cede)

- **作者**: Lanze Liu
- **时间**: 2026-05-21T22:42:42Z
- **提交信息**: [Bugfix] Zero stale is_prefilling in padded CUDA graph rows for Mamba (#41873)

Signed-off-by: Lanze Liu <lanzetech@gmail.com>

### [565b745](https://github.com/vllm-project/vllm/commit/565b745ec5d28dafd14585f1b695b159ba336a04)

- **作者**: Nick Hill
- **时间**: 2026-05-21T22:42:20Z
- **提交信息**: [BugFix] Use correct logprobs for `logprob_token_ids` (#43125)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [e26e1f0](https://github.com/vllm-project/vllm/commit/e26e1f09280b6c54e1bc1d1fbc0118f7e309cb10)

- **作者**: fangyuchu
- **时间**: 2026-05-21T22:42:07Z
- **提交信息**: [Feature] Add `--cpu-distributed-timeout-seconds` CLI Option for CPU Process Group Timeout (#42968)

Signed-off-by: fangyuchu <fangyuchu@qq.com>
Signed-off-by: zWaNg3 <389750525@qq.com>
Co-authored-by: zWaNg3 <389750525@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0f66623](https://github.com/vllm-project/vllm/commit/0f66623b0d739dc94afddb67863c37d6f5816579)

- **作者**: Nick Hill
- **时间**: 2026-05-21T22:36:58Z
- **提交信息**: [Frontend] Rework fastokens integration (#43168)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [0b59fc4](https://github.com/vllm-project/vllm/commit/0b59fc45dd475f96f6f46f2c3e699d7bc13b3b04)

- **作者**: ylangtsou
- **时间**: 2026-05-21T22:00:52Z
- **提交信息**: Disable build isolation to bypass CUDA related deps for vllm-tpu (#43038)

Signed-off-by: Ylang Tsou <ylangt@google.com>
Co-authored-by: Ylang Tsou <ylangt@google.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [17b6982](https://github.com/vllm-project/vllm/commit/17b69828a013acb7af0cd1d16d24ecc8d7582094)

- **作者**: Zheng Luo
- **时间**: 2026-05-21T20:05:01Z
- **提交信息**: [Core] Add native ModelExpress load format (#43105)

Signed-off-by: Zheng Luo <zheluo@nvidia.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [b29cbf0](https://github.com/vllm-project/vllm/commit/b29cbf06525254693f29d98686e038eaf225be8c)

- **作者**: Wentao Ye
- **时间**: 2026-05-21T20:00:29Z
- **提交信息**: [Perf] `zeros` -> `empty` to remove additional fill (#42988)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [9b54e50](https://github.com/vllm-project/vllm/commit/9b54e50e2c1c61ea3b7def032fbafc56dd3179c1)

- **作者**: Michael Goin
- **时间**: 2026-05-21T19:51:12Z
- **提交信息**: [Deprecation] Mark env vars covered by --moe-backend / --linear-backend (#43148)

Signed-off-by: mgoin <mgoin64@gmail.com>
Signed-off-by: Michael Goin <mgoin64@gmail.com>

### [1c78f76](https://github.com/vllm-project/vllm/commit/1c78f76c29a642379ad0ec953a77af9bc44376b6)

- **作者**: anish
- **时间**: 2026-05-21T15:07:46Z
- **提交信息**: [Bugfix] Add early validation to reject incompatible runner types for embedding models (#43079)

Signed-off-by: anish <anishesg@users.noreply.github.com>
Signed-off-by: Your Name <ak8686@princeton.edu>
Signed-off-by: anish <145943060+anishesg@users.noreply.github.com>
Co-authored-by: anish <anishesg@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [9b9d5db](https://github.com/vllm-project/vllm/commit/9b9d5dbaab852a1c615fe83a7f92881d353503db)

- **作者**: haosdent
- **时间**: 2026-05-21T14:28:34Z
- **提交信息**: [CI] Fix CPU tests failing on `tl.exp2` import (#43311)

Signed-off-by: haosdent <haosdent@gmail.com>

### [b730c46](https://github.com/vllm-project/vllm/commit/b730c4635288d75da4788bc28d8d26b5e5c3726c)

- **作者**: Francesco Fusco
- **时间**: 2026-05-21T11:50:54Z
- **提交信息**: [Perf] [Hybrid] Fused Triton kernel for GPU-side Mamba state postprocessing (#40172)

Signed-off-by: Francesco Fusco <ffu@zurich.ibm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c68c55d](https://github.com/vllm-project/vllm/commit/c68c55d43e504745dbfc2d46b552e80acb74d4b9)

- **作者**: velonica0
- **时间**: 2026-05-21T11:50:49Z
- **提交信息**: [CPU][RISC-V] Add VLEN=256 support to RVV attention kernels (#42943)

Signed-off-by: velonica0 <like@mail.nankai.edu.cn>
Signed-off-by: velonica0 <47554626+velonica0@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [5ecd8e9](https://github.com/vllm-project/vllm/commit/5ecd8e9c708821916323d25d5f7beddb7f41d22b)

- **作者**: xiangdong
- **时间**: 2026-05-21T10:41:38Z
- **提交信息**: [XPU][CI]Fix Docker image pull-to-run race in Intel GPU CI (#43266)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [caf6982](https://github.com/vllm-project/vllm/commit/caf69823d61119ac3f4b066f20a910b62078e41c)

- **作者**: haosdent
- **时间**: 2026-05-21T10:38:07Z
- **提交信息**: [CI] Pin protoc binary in rust-build stages (#43292)

Signed-off-by: haosdent <haosdent@gmail.com>

### [68e07d5](https://github.com/vllm-project/vllm/commit/68e07d59161a8d268b773c181fab17994a7c5d0a)

- **作者**: Wentao Ye
- **时间**: 2026-05-21T08:58:09Z
- **提交信息**: [Bug] Fix ci issue `assert output_size is not None` AssertionError (#43261)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [ebbfb34](https://github.com/vllm-project/vllm/commit/ebbfb34e3e058bd539db9e5015d0c18b7ce5a5e0)

- **作者**: Kevin H. Luu
- **时间**: 2026-05-21T08:57:47Z
- **提交信息**: [Test] Replace zephyr-7b-beta (7B) with SmolLM2-135M in tokenization test (#43085)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [edafea3](https://github.com/vllm-project/vllm/commit/edafea35550fab0b185b885711ec048dfd2e1a4d)

- **作者**: zhangxin81
- **时间**: 2026-05-21T08:17:12Z
- **提交信息**: Fix FlashInfer TRTLLM NvFP4 monolithic MoE routing (#43223)

Signed-off-by: zhangxin81 <115389973+zhangxin81@users.noreply.github.com>

### [b719b16](https://github.com/vllm-project/vllm/commit/b719b1635b4899e2372905def0badf96d4dd242a)

- **作者**: zexplorerhj
- **时间**: 2026-05-21T08:16:27Z
- **提交信息**: Update KDA chunk prefill decay to use exp2 semantics (#43195)

Signed-off-by: zexplorerhj <19794632+zexplorerhj@users.noreply.github.com>
Co-authored-by: zexplorerhj <19794632+zexplorerhj@users.noreply.github.com>

### [0a54df2](https://github.com/vllm-project/vllm/commit/0a54df28471be07b3d668ea21c5e411569d3baea)

- **作者**: Kunshang Ji
- **时间**: 2026-05-21T07:14:13Z
- **提交信息**: [XPU] add setuptools-rust for xpu dependency (#43287)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-22
**监控日期**: 2026-05-21
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4848
- **最后更新**: 2026-05-21T21:18:26Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Siyuan Kong, Hongsheng Liu, Liang Lv

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型

*   **Bug修复**：2项（MiMo-Audio语音不稳定、Qwen2.5-Omni权重加载）
*   **功能新增**：2项（LTX-2在线量化、WAN2.2 W4A16量化模型支持）
*   **其他**：1项（新增提交者到治理页面）、1项（基准测试路由优化）

### 2. 关键变更点及其与项目整体方向的关系

*   **Bug修复 (MiMo-Audio & Qwen2.5-Omni)**：
    *   **变更点**：修复了多模态音频模型（MiMo-Audio）的语音生成不稳定问题，以及Qwen2.5-Omni模型的权重加载错误。
    *   **与项目方向关系**：直接提升了多模态模型（尤其是音频和视觉-语言模型）的**稳定性和可用性**，符合项目“为所有人提供**易用、快速、廉价**的全模态模型服务”的核心目标。修复权重加载是确保模型正确运行的基础。

*   **功能新增 (量化支持)**：
    *   **变更点**：为LTX-2模型增加了在线量化（FP8/INT8）支持，并为WAN2.2模型增加了W4A16量化支持。
    *   **与项目方向关系**：量化技术是降低模型部署成本和加速推理的关键手段。支持更多模型的量化（特别是W4A16这种更激进的量化）直接服务于“**廉价**”和“**快速**”的目标，扩大了项目可高效服务的模型范围。

*   **基准测试优化**：
    *   **变更点**：在扩散模型基准测试服务中，将图像到图像（i2i）和文本到图像（ti2i）的路由正确指向`POST /v1/images/edits`端点。
    *   **与项目方向关系**：这属于基础设施优化，确保基准测试的准确性和API的规范性，间接支持了项目“**易用**”和“**快速**”的评估与迭代。

### 3. 对项目的影响和潜在意义

*   **提升核心模型稳定性**：修复MiMo-Audio和Qwen2.5-Omni的Bug，直接提升了这两个重要多模态模型在实际服务中的可靠性，对用户体验至关重要。
*   **降低部署门槛与成本**：新增的量化支持（LTX-2在线量化、WAN2.2 W4A16）允许用户在更低的硬件成本下运行这些模型，或是在相同硬件上获得更高的吞吐量，这极大地增强了项目的实用性和吸引力。
*   **增强项目治理透明度**：新增提交者到治理页面，表明项目社区正在成长，治理结构更加规范，有利于长期健康发展。

### 4. 值得关注的技术点

*   **MiMo-Audio的修复细节**：修复涉及“随机局部采样器”和“编解码流上下文”，这表明问题出在音频生成的采样策略和流式处理逻辑上，是音频模型服务中的典型难点。
*   **在线量化 (Online Quantization)**：为LTX-2支持在线量化，意味着用户可以在模型加载时动态进行量化，无需预先准备量化后的模型权重，这大大简化了部署流程。
*   **W4A16量化**：支持WAN2.2的W4A16（权重4比特，激活16比特）量化，这是一种非常激进的量化方式，能显著减少模型大小和内存带宽需求，但实现难度高，容易导致精度损失。成功支持表明项目在模型压缩技术上取得了进展。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **巩固“全模态”定位**：通过修复MiMo-Audio和Qwen2.5-Omni的问题，项目在音频和视觉-语言这两个关键模态上的服务能力得到加强，使其“全模态”的定位更加坚实可靠。
*   **加速“低成本”普及**：新增的量化支持直接降低了LTX-2和WAN2.2等模型的部署成本，这与项目“廉价”的愿景高度一致。这能吸引更多资源有限的开发者和企业用户，扩大项目生态。
*   **提升“易用性”体验**：在线量化和Bug修复都简化了用户的使用流程，减少了配置和调试的麻烦，让“易用”不仅仅停留在口号上。
*   **总结**：昨日的更新是**一次典型的“稳基础、拓能力”的迭代**。一方面通过修复Bug稳固了现有核心模型的可靠性，另一方面通过引入先进的量化技术，扩展了项目在低成本、高效率服务方面的能力边界。这有助于vllm-omni在竞争激烈的多模态模型服务领域，巩固其“**全、快、省**”的差异化优势。

## 详细提交记录

### [e949ccf](https://github.com/vllm-project/vllm-omni/commit/e949ccf087b4fd0f3b45293d71e603511fa3a9e8)

- **作者**: Jialong Liu
- **时间**: 2026-05-21T14:18:00Z
- **提交信息**: [Bugfix] Fix MiMo-Audio voice instability: stochastic local_sampler + codec streaming context (#3686)

Signed-off-by: Galleons2029 <Galleons777@gmail.com>
Signed-off-by: Jialong Liu <88185941+Galleons2029@users.noreply.github.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [bd1617c](https://github.com/vllm-project/vllm-omni/commit/bd1617ce2b96d65d9a808ad2e327410c7028de23)

- **作者**: Hongsheng Liu
- **时间**: 2026-05-21T14:06:01Z
- **提交信息**: Add new committers to governance page (#3749)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [2bc9cb7](https://github.com/vllm-project/vllm-omni/commit/2bc9cb7f13e2db487c35f05a5973db620043ec9d)

- **作者**: Yuanheng Zhao
- **时间**: 2026-05-21T11:52:21Z
- **提交信息**: [Feat] Support online quantization (fp8/int8) for LTX-2 (#3700)

Signed-off-by: Yuanheng Zhao <jonathan.zhaoyh@gmail.com>
Signed-off-by: yuanheng <jonathan.zhaoyh@gmail.com>

### [8297570](https://github.com/vllm-project/vllm-omni/commit/8297570c2b8deca12d7dcf4fb12ee417128984ba)

- **作者**: Liang Lv
- **时间**: 2026-05-21T09:54:41Z
- **提交信息**: [AutoRound] Support WAN2.2 W4A16 quantization model (#3353)

Signed-off-by: lvliang-intel <liang1.lv@intel.com>
Signed-off-by: hyh_hh <huyinghong1@huawei.com>
Co-authored-by: hxhhhlalala <hyh_hh@163.com>
Co-authored-by: hyh_hh <huyinghong1@huawei.com>

### [474710d](https://github.com/vllm-project/vllm-omni/commit/474710dda90beb628f94255b8a3d5de54f033656)

- **作者**: NumberWan
- **时间**: 2026-05-21T09:18:02Z
- **提交信息**: [Benchmark] Route i2i/ti2i to POST /v1/images/edits in diffusion_benchmark_serving (#3693)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [7d9d8ae](https://github.com/vllm-project/vllm-omni/commit/7d9d8aee79d02d4616018ff277e9d32971c6da17)

- **作者**: Siyuan Kong
- **时间**: 2026-05-21T08:43:33Z
- **提交信息**: [Bugfix] Fix qwen2_5_omni weight loading (#3598)

Signed-off-by: ksiyuan <ksiyuan@umich.edu>

---
