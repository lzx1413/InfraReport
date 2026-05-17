# GitHub Stars 合并报告 - 2026-05-16

**合并日期**: 2026-05-17
**监控日期**: 2026-05-16
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


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1925
- **最后更新**: 2026-05-17T11:30:52Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: wxy

## AI分析总结

好的，这是对仓库 `ByteDance-Seed/VeOmni` 昨日提交记录的分析总结。

### 提交分析总结

**提交记录**: `[5243b27] [parallel] feat: add cpu offload for fsdp2 (#753)`

---

#### 1. 主要更新类型

-   **功能新增 (Feature)**：为 FSDP2（Fully Sharded Data Parallelism v2）策略添加了 CPU 卸载（CPU Offload）功能。

#### 2. 关键变更点及其与项目整体方向的关系

-   **关键变更点**：在项目的并行训练模块（`[parallel]`）中，为 FSDP2 实现了 CPU 卸载能力。这意味着在训练过程中，可以将部分模型参数、梯度或优化器状态从 GPU 显存转移到 CPU 内存中。
-   **与项目方向的关系**：VeOmni 的目标是“**扩展任意模态模型的训练**”（Scaling Any Modality Model Training）。这意味着它需要支持训练超大模型，而显存往往是主要瓶颈。CPU 卸载是解决显存瓶颈的关键技术之一，允许在有限的 GPU 显存下训练更大的模型或使用更大的批次大小。此提交直接服务于项目“**扩展性**”的核心目标。

#### 3. 对项目的影响和潜在意义

-   **降低硬件门槛**：用户可以使用更少或更便宜的 GPU 来训练原本因显存不足而无法训练的模型。
-   **提升模型规模上限**：对于拥有固定 GPU 资源的用户，CPU 卸载允许他们尝试训练参数量更大的模型。
-   **增强 FSDP2 的实用性**：FSDP2 是 PyTorch 中较新的并行策略，此功能使其在显存受限场景下更具竞争力，丰富了 VeOmni 的“**分布式训练菜谱**”（Distributed Recipe Zoo）。

#### 4. 值得关注的技术点

-   **FSDP2 与 CPU Offload 的结合**：FSDP2 本身通过分片参数来节省显存，而 CPU 卸载是另一种正交的显存优化手段。两者的结合可以产生叠加效果，进一步压榨显存使用。
-   **性能权衡**：CPU 卸载虽然节省了显存，但会引入 CPU-GPU 之间的数据传输开销，可能影响训练速度。该提交的实现需要关注如何最小化这种开销（例如，异步传输、分层卸载策略等），以在显存和速度之间取得平衡。

#### 5. 基于项目背景，该提交如何影响项目发展

-   **完善核心能力**：VeOmni 作为一个专注于“**模型中心**”（Model-Centric）的分布式训练框架，其核心价值在于提供高效、易用的并行策略组合。添加 FSDP2 的 CPU 卸载功能，是完善其核心并行策略能力的重要一步。
-   **吸引更广泛的用户**：该功能使得 VeOmni 对资源受限的学术实验室和中小企业更具吸引力，有助于扩大用户基础，从而推动社区发展和项目迭代。
-   **为未来优化铺路**：此提交为未来实现更高级的显存优化技术（如激活值卸载、混合精度卸载等）奠定了基础，使 VeOmni 在应对未来更大规模、更复杂模型（如多模态大模型）的训练挑战时更具优势。

## 详细提交记录

### [5243b27](https://github.com/ByteDance-Seed/VeOmni/commit/5243b276aea02cd799dbb3705fc113fd900e8ea6)

- **作者**: wxy
- **时间**: 2026-05-16T14:55:11Z
- **提交信息**: [parallel] feat: add cpu offload for fsdp2 (#753)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2268
- **最后更新**: 2026-05-17T09:21:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2078
- **最后更新**: 2026-05-16T12:51:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5623
- **最后更新**: 2026-05-17T13:38:00Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Ka-Hyun Nam

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **Bug修复 (Bug Fix)**

### 2. 关键变更点及其与项目整体方向的关系

*   **变更点**: 修复了在特定CI容器（如Spark、5090、Thor）中运行单元测试时，因用户ID（UID）未映射到`/etc/passwd`文件而导致的 `KeyError: 'getpwuid(): uid not found: 996'` 崩溃问题。
*   **与项目方向的关系**: FlashInfer 是一个专注于高性能推理的GPU内核库，其稳定性和可靠性至关重要。CI（持续集成）是保证代码质量、防止回归的核心环节。此修复确保了CI流程在各种容器化环境中都能稳定运行，直接支撑了项目“高性能”和“可靠”的核心目标。

### 3. 对项目的影响和潜在意义

*   **直接影响**: 修复了 `test_b12x_fused_moe` 等关键测试在特定CI环境下的运行时崩溃问题，使得这些测试能够正常通过。
*   **潜在意义**:
    *   **提升CI健壮性**: 消除了CI基础设施中的一个环境依赖性问题，使得测试环境更加通用和鲁棒。
    *   **保障代码质量**: 确保所有测试（特别是涉及 `fused_moe` 等核心算子的测试）都能被正确执行，从而更有效地捕获潜在的回归错误。
    *   **支持更广泛的部署**: 表明项目团队关注并解决了在非标准或受限环境（如容器）中运行的问题，这有助于FlashInfer在更广泛的用户环境中被采用。

### 4. 值得关注的技术点

*   **问题根因**: `torch._dynamo` 初始化时会调用 `getpass.getuser()`，该函数在未设置 `USER` 环境变量时会回退到 `pwd.getpwuid(os.getuid())`。在CI容器中，如果宿主机UID在容器内没有对应的`/etc/passwd`条目，此调用就会失败。
*   **解决方案**: 在 `torch._dynamo` 被导入之前，显式设置一个备用的 `USER` 环境变量。这利用了 `getpass.getuser()` 会优先检查环境变量的特性，从而绕过了对 `getpwuid` 的调用。
*   **技术启示**: 这是一个典型的“环境依赖”问题，展示了在容器化、多用户环境下进行Python开发时，需要留意系统级调用（如 `getpwuid`）可能因环境差异而失败。通过环境变量进行“软”配置是一种优雅的解决方案。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **巩固基础设施**: 作为高性能推理库，FlashInfer 的发展高度依赖其CI系统来验证新功能（如新的CUDA内核）和优化（如性能调优）的正确性。此修复清除了CI中的一个“定时炸弹”，确保了开发流程的顺畅，为后续更复杂、更激进的性能优化和功能开发提供了稳定的测试基础。
*   **提升开发者体验**: 对于在类似容器化环境中进行本地开发或调试的贡献者而言，这个修复也避免了他们在本地重现CI失败时的困惑，降低了参与项目的门槛。
*   **增强项目成熟度**: 主动解决这种边缘环境下的兼容性问题，体现了项目对工程严谨性的追求，是项目走向成熟和广泛采用的重要标志。

## 详细提交记录

### [de541f1](https://github.com/flashinfer-ai/flashinfer/commit/de541f13d915c8e85479bd52eed95c6c9cb37c27)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-05-16T23:47:39Z
- **提交信息**: fix(CI unit tests, cute_dsl, spark): set USER env var before torch._dynamo import for unmapped UIDs (#3314)

<!-- .github/pull_request_template.md -->

## 📌 Description

Summary
Follow-up to #3290. The lazy wrapper in #3290 fixed the import-time
crash (KeyError: 'getpwuid(): uid not found: 996') for all tests by
deferring torch._dynamo.disable from module load time to first call.
However, test_b12x_fused_moe still hit the same error at runtime because
it's the only test that actually calls current_cuda_stream(), which
triggers the lazy wrapper and imports torch._dynamo.

The root cause is that torch._dynamo initialization calls
getpass.getuser(), which falls back to pwd.getpwuid(os.getuid()) when no
username env var is set. In .dlfw_runners CI containers (Spark, 5090,
Thor) running with -u $(id -u):$(id -g), the host UID (996) has no
/etc/passwd entry.

This fix sets a fallback USER env var before the torch._dynamo import so
getpass.getuser() returns from its env-var check and never reaches the
failing getpwuid call.

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

* **Bug Fixes**
* Improved reliability in containerized environments by enhancing how
user environment information is detected, preventing failures when
running in containers.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3314)

<!-- review_stack_entry_end -->

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Alex Yang <aleyang@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3481
- **最后更新**: 2026-05-17T14:50:12Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Shao Duan

## AI分析总结

好的，这是对 `hao-ai-lab/FastVideo` 仓库昨日提交记录的分析总结：

### 1. 主要更新类型
- **功能新增 (Feature)**

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**: 在评估（eval）模块中新增了音频指标（audio metrics）。
- **与项目方向的关系**: FastVideo 是一个专注于视频生成和处理的框架。增加音频评估指标表明项目正在向**多模态**方向扩展，不仅仅关注视频的视觉质量，也开始重视视频的**音频质量**。这符合构建更完整、更高质量的“视频”生成体验的目标，因为视频天然包含视觉和听觉两个维度。

### 3. 对项目的影响和潜在意义
- **影响**: 使得 FastVideo 的评估体系更加完善。现在，用户和开发者不仅可以评估生成视频的视觉保真度，还可以量化其音频质量（例如，音质、同步性等）。
- **潜在意义**:
    - **提升生成质量**: 为视频生成模型提供音频维度的反馈，可以引导模型在训练或微调时同时优化视觉和音频部分，从而生成更真实、沉浸感更强的视频。
    - **扩展应用场景**: 支持音频评估是迈向“文生视频+音频”或“图生视频+音频”等更复杂任务的关键一步，使项目能服务于更广泛的创作需求（如电影制作、游戏内容生成等）。

### 4. 值得关注的技术点
- **评估指标的实现**: 需要关注具体实现了哪些音频指标（例如：FAD - Frechet Audio Distance, CLAP score, 音质指标等）。这些指标的选择直接决定了评估的维度和有效性。
- **与现有视频评估流程的集成**: 该功能如何与 FastVideo 已有的视频评估管道（pipeline）结合，是作为一个独立模块运行，还是可以无缝集成到统一的评估脚本中。

### 5. 基于项目背景，这些提交如何影响项目发展
- **从“视频”到“视听”的演进**: 根据 README，项目专注于“FastVideo”。此次提交标志着项目从单纯的“快速视频生成”向“快速、高质量的视听内容生成”迈出了实质性的一步。这提升了项目的技术壁垒和独特性。
- **增强竞争力**: 在视频生成领域，大多数开源项目仍主要关注视觉质量。率先引入系统化的音频评估，能让 FastVideo 在功能完整性和专业性上领先于同类项目，吸引更多对音视频同步、高质量视频制作有需求的用户和研究者。
- **为未来功能铺路**: 音频评估是音频生成和音频-视频对齐的基础。这次更新为后续可能推出的“视频配音”、“音频驱动视频生成”等高级功能奠定了评估基础，指明了项目清晰的发展路线图。

## 详细提交记录

### [6b2c731](https://github.com/hao-ai-lab/FastVideo/commit/6b2c731596e7c4f8c6f49f78e8d7e885d2a641f1)

- **作者**: Shao Duan
- **时间**: 2026-05-16T21:47:37Z
- **提交信息**: [feat] eval: add audio metrics (#1352)

Co-authored-by: klhhhhh <1412841649@qq.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33634
- **最后更新**: 2026-05-17T15:20:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
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


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12416
- **最后更新**: 2026-05-17T14:17:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 27920
- **最后更新**: 2026-05-17T15:38:47Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 12
- **主要提交者**: Xiaoyu Zhang, Liangsheng Yin, Zheng Luo

## AI分析总结

好的，这是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (BugFix):** 修复了 DeepSeek V4 HiCache 层数逻辑、PD分离中KV池的end_layer问题、DP注意力空闲rank的间隔处理等。
- **文档更新 (Docs):** 更新了 DeepSeek V4 的 cookbook，包括环境变量清理、MegaMoE 开关、统一 Docker 镜像等。
- **性能优化 (Performance):** 优化了 LTX2 的 split rotary kernel，调整了 swa_radix_cache 的 kl_div_thres 阈值。
- **重构/清理 (Refactor/Cleanup):** 清理了 speculative decoding 的 draft-window-size 处理逻辑，将 spec 参数设置提取到 arg_groups。
- **功能新增/调整 (Feature/Adjustment):** 将 ModelExpress 加载委托给包，解耦 Mega MoE 与 DeepEP 后端。
- **CI/DevOps:** 拆分 diffusion 量化 CI 覆盖，修复 nightly CI，更新发布分支切割脚本。

### 2. 关键变更点及其与项目整体方向的关系

- **DeepSeek V4 支持深化 (提交 #25497, #25477, #25412, #25410):**
    - **变更:** 修复 HiCache 层数逻辑，更新 cookbook 文档（环境变量、MegaMoE 开关、Docker 镜像），调整 swa_radix_cache 的 kl_div_thres 阈值。
    - **关系:** 项目 README 强调支持 DeepSeek V3/V4 等前沿模型。这些提交表明项目正在积极跟进 DeepSeek V4 的最新进展，修复其推理中的具体问题，并优化其配置和部署体验，以保持对最新模型的支持和性能优势。

- **MoE 架构解耦 (提交 #25406):**
    - **变更:** 将 Mega MoE 从 DeepEP 后端解耦。
    - **关系:** 项目核心是高性能 LLM 推理，MoE 是其关键特性。解耦 Mega MoE 意味着项目正在构建更模块化、更灵活的 MoE 实现，允许用户或开发者在不依赖特定通信库（DeepEP）的情况下使用 Mega MoE，提升了架构的通用性和可维护性。

- **注意力后端优化 (提交 #25321, #25488):**
    - **变更:** 尝试避免初始化父类的 workspace buffer，但随后回滚了该更改。
    - **关系:** 注意力机制是 LLM 推理的核心瓶颈。项目持续在注意力后端（如 FlashInfer）上进行优化尝试，即使某些尝试被回滚，也体现了项目在底层性能调优上的积极探索和严谨态度。

- **Speculative Decoding 清理 (提交 #25424):**
    - **变更:** 清理了 draft-window-size 的处理逻辑，并将 spec 参数设置提取到 arg_groups。
    - **关系:** Speculative Decoding 是加速 LLM 推理的重要技术。清理和重构相关代码，使其更清晰、更易配置，有助于提升该功能的稳定性和易用性，是项目持续优化推理速度的体现。

### 3. 对项目的影响和潜在意义

- **提升模型支持成熟度:** 对 DeepSeek V4 的持续修复和文档更新，将显著提升该模型在 SGLang 上的稳定性和易用性，吸引更多用户使用 SGLang 部署该模型。
- **增强架构灵活性:** Mega MoE 与 DeepEP 的解耦，降低了组件间的耦合度，为未来支持更多 MoE 变体和通信后端铺平了道路，增强了项目的长期可扩展性。
- **改善开发与测试流程:** CI 覆盖的拆分、Nightly CI 的修复以及发布脚本的更新，直接提升了项目的开发效率和代码质量，减少了回归风险，对项目的健康发展至关重要。
- **潜在的性能波动:** 对注意力后端的优化尝试（尽管被回滚）和 kernel 优化，表明项目在持续追求极致性能，这些努力最终会转化为用户的推理速度提升。

### 4. 值得关注的技术点

- **`kl_div_thres` 调整:** 在 `swa_radix_cache` 中调整 KL 散度阈值，可能是在平衡缓存命中率与计算精度，这是一个精细的性能调优点。
- **`HiCache` 层数逻辑:** 修复 DeepSeek V4 的 HiCache 层数逻辑，暗示了该模型在分层缓存方面有特殊设计，需要精确的工程实现。
- **`Mega MoE` 与 `DeepEP` 解耦:** 这是一个重要的架构决策，值得关注后续是否会引入新的 MoE 后端或通信库。
- **`arg_groups` 的使用:** 将 spec 参数设置提取到 `arg_groups`，表明项目正在采用更结构化的参数管理方式，可能为未来支持更复杂的配置组合做准备。

### 5. 基于项目背景，这些提交如何影响项目发展

- **巩固“前沿模型首选框架”的定位:** 通过快速跟进 DeepSeek V4 的更新并修复其特定问题，SGLang 强化了其作为支持最新、最复杂模型（如 DeepSeek V4）的领先推理框架的形象。
- **夯实“高性能推理”的核心竞争力:** 对注意力后端、MoE 架构、Speculative Decoding 等核心组件的持续优化和重构，直接服务于项目“高性能”的目标，确保其在推理速度上保持竞争力

## 详细提交记录

### [0c017db](https://github.com/sgl-project/sglang/commit/0c017db9163854880b7ee6983e7e9a2ccfb4200e)

- **作者**: Cheng Wan
- **时间**: 2026-05-16T23:43:12Z
- **提交信息**: Update kl_div_thres to 0.02 in swa_radix_cache (#25497)

### [9869ef0](https://github.com/sgl-project/sglang/commit/9869ef08495c6d3210e4a7698e5af3aff156e77a)

- **作者**: Qiaolin Yu
- **时间**: 2026-05-16T20:05:42Z
- **提交信息**: Revert "[attn backend] avoid initing parent class's workspace buffer" (#25488)

### [57eb5bd](https://github.com/sgl-project/sglang/commit/57eb5bdaf6cc3f9a182d3c80e248ccdcc7fce4d6)

- **作者**: Yuhao Yang
- **时间**: 2026-05-16T18:28:05Z
- **提交信息**: [Doc] DSV4 cookbook: clean up env vars, add MegaMoE toggle, unify docker image (#25412)

### [9f26697](https://github.com/sgl-project/sglang/commit/9f26697d6a6ac18686c8b97334f0a06a757f3fb5)

- **作者**: zijiexia
- **时间**: 2026-05-16T18:17:51Z
- **提交信息**: [Docs] Update DeepSeek V4 cookbook to use the latest docker image (#25410)

### [435ea41](https://github.com/sgl-project/sglang/commit/435ea41cf0c515dd0de37c9bc8fc11a3c7d5d9ee)

- **作者**: Zheng Luo
- **时间**: 2026-05-16T18:16:44Z
- **提交信息**: Delegate ModelExpress loading to package (#24723)

Signed-off-by: Zheng Luo <zheluo@nvidia.com>

### [0be5390](https://github.com/sgl-project/sglang/commit/0be539024faf50db2d4c220b68a082dd8ee817bf)

- **作者**: Zhangheng
- **时间**: 2026-05-16T15:50:01Z
- **提交信息**: [BugFix]: Fix DeepSeek V4 HiCache layer count logic (#25477)

### [2fc217d](https://github.com/sgl-project/sglang/commit/2fc217df4d3056aa6e428ee4b3d5226d77601285)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-16T14:05:02Z
- **提交信息**: [codex] Split diffusion quant CI coverage (#24599)

Co-authored-by: Codex <codex@example.com>

### [596b45b](https://github.com/sgl-project/sglang/commit/596b45b373c2861dba167d761f059e7cc6dadf5c)

- **作者**: Chi McIsaac
- **时间**: 2026-05-16T13:55:31Z
- **提交信息**: [diffusion] fix: change default qwen-image vae precision to bf16 (#25411)

### [93bacc2](https://github.com/sgl-project/sglang/commit/93bacc25ed16f6513cfbe59892b62b5a17cd88e0)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-16T12:58:38Z
- **提交信息**: [codex] Optimize LTX2 split rotary kernel (#24732)

### [0f50ed8](https://github.com/sgl-project/sglang/commit/0f50ed86c91efd7163e41f6e7705872a993ef6c0)

- **作者**: ybyang
- **时间**: 2026-05-16T11:49:26Z
- **提交信息**: fix(pd): fix kv pools without end_layer (#25476)

### [90d3d42](https://github.com/sgl-project/sglang/commit/90d3d42ac1151460dd49d1f97e55b6a406fe0bcc)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-16T10:34:52Z
- **提交信息**: pr-states: workflow_dispatch refresh on slash cmds (#25475)

### [2f81718](https://github.com/sgl-project/sglang/commit/2f81718773ab51109f221091290760c18ad21af5)

- **作者**: Qiaolin Yu
- **时间**: 2026-05-16T10:30:33Z
- **提交信息**: [attn backend] avoid initing parent class's workspace buffer (#25321)

### [aec4022](https://github.com/sgl-project/sglang/commit/aec4022e58c6f74c72f9b7be449ad3e81238c14e)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-16T10:23:48Z
- **提交信息**: [Spec] Clean up draft-window-size handling; extract spec arg setup to arg_groups (#25424)

### [d1eb472](https://github.com/sgl-project/sglang/commit/d1eb472a7ab462057739b635404316bc1164a0f1)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-16T09:08:01Z
- **提交信息**: fix(overlap): skip empty future interval for dp attention idle ranks (#25473)

### [7f37ffa](https://github.com/sgl-project/sglang/commit/7f37ffae9db52ad7f87dc7eacb443bc0c2e8c9f2)

- **作者**: Mick
- **时间**: 2026-05-16T08:55:30Z
- **提交信息**: [diffusion] CI: fix nightly CI (#25241)

### [af26b71](https://github.com/sgl-project/sglang/commit/af26b71ae83ea43c982566cbaed423b66ca3c3b5)

- **作者**: Baizhou Zhang
- **时间**: 2026-05-16T07:51:48Z
- **提交信息**: [Misc] Update release branch cut script (#25468)

### [b2c6db0](https://github.com/sgl-project/sglang/commit/b2c6db0cc42992687f9ed2c80dce7058c3009df6)

- **作者**: Yuhao Yang
- **时间**: 2026-05-16T07:18:43Z
- **提交信息**: [MoE] Decouple Mega MoE from DeepEP backend (#25406)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1174
- **最后更新**: 2026-05-15T10:21:00Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 80250
- **最后更新**: 2026-05-17T15:37:19Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 6
- **主要提交者**: Taneem Ibrahim, weizhoublue, Artem Perevedentsev

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增与增强**：`[KV Connector]` 支持磁盘卸载；`[Experimental]` 可中断 CUDA 图。
- **Bug 修复**：修复了 Ultravox 模型中固定模型版本未正确传播的问题。
- **CI/构建与基础设施**：升级了 FlashInfer 依赖；为 ROCm 平台移除了有问题的命令覆盖机制；从源码构建 `mooncake-transfer-engine`。
- **测试**：为池化器激活函数添加了单元测试。

### 2. 关键变更点及其与项目整体方向的关系

- **`[KV Connector] Support disk offloading in MooncakeStoreConnector`**：为 MooncakeStore 连接器增加了将 KV 缓存卸载到磁盘的功能。这与 vLLM 追求“**便宜 (cheap)**”和“**快速 (fast)**”的目标一致。磁盘卸载允许在内存不足时使用更便宜的存储介质，从而支持更大的模型或更长的上下文，同时通过减少内存压力来提升整体吞吐量。
- **`[Experimental] Breakable CUDA graph`**：引入了可中断的 CUDA 图功能。CUDA 图是 vLLM 实现高性能推理的关键技术，但传统上它缺乏灵活性。此实验性功能允许在 CUDA 图执行过程中进行中断和恢复，这可能是为了支持更复杂的调度策略（如抢占、动态批处理），从而在保持高性能的同时增加系统的灵活性和鲁棒性。
- **`Fix: Propagate pinned model revisions into Ultravox secondary weight loading`**：修复了一个 Bug，确保在加载 Ultravox 模型的辅助权重时，用户指定的固定模型版本（`pinned model revision`）能被正确使用。这直接关系到模型的**易用性 (easy)** 和**正确性**，确保用户能可靠地复现和部署特定版本的模型。
- **`[CI/Build] Bump flashinfer to v0.6.11.post2`**：升级了关键的注意力计算库 FlashInfer。这通常是为了获取性能提升、Bug 修复或对新硬件架构的支持，直接服务于“**快速 (fast)**”的目标。
- **`[Docker][KVConnector] Build mooncake-transfer-engine from source`**：将 `mooncake-transfer-engine` 的构建方式改为从源码编译。这增强了项目的可移植性和可定制性，尤其是在多节点推理场景下，确保 KV 缓存传输组件能与特定环境（如硬件、内核）最佳匹配。

### 3. 对项目的影响和潜在意义

- **提升大规模部署的可行性**：`MooncakeStoreConnector` 的磁盘卸载功能，对于需要处理超长上下文或超大模型的多节点推理场景至关重要。它降低了内存瓶颈，使得在有限资源下运行更大规模的服务成为可能。
- **增强推理引擎的灵活性**：`Breakable CUDA graph` 是一个重要的技术探索。如果成功，它将打破 CUDA 图在动态场景下的限制，为未来实现更高级的调度、抢占和资源管理功能铺平道路，从而在性能和灵活性之间取得更好的平衡。
- **提高模型兼容性和可靠性**：修复 Ultravox 模型的版本传播问题，直接提升了 vLLM 对多模态模型的支持质量，确保用户能稳定地使用特定版本的模型，增强了项目的可靠性。
- **巩固基础设施**：升级 FlashInfer 和从源码构建关键组件，是持续优化性能和确保平台兼容性的常规但重要的工作，为项目的长期稳定发展打下基础。

### 4. 值得关注的技术点

- **`Breakable CUDA graph`**：这是一个高级特性。它的实现可能涉及在 CUDA 图的关键点插入“检查点”或“中断点”，允许调度器在需要时（如新请求到达）暂停当前图的执行，插入新的操作，然后恢复。这比传统的、不可中断的 CUDA 图更复杂，但潜力巨大。
- **`MooncakeStoreConnector` 的磁盘卸载**：这涉及到如何高效地将 KV 缓存数据从 GPU 内存卸载到磁盘（如 NVMe SSD），并在需要时快速加载回来。其性能（卸载/加载速度、对推理延迟的影响）是衡量该功能成功与否的关键。

### 5. 基于项目背景的综合分析

vLLM 的使命是“**为每个人提供简单、快速、便宜的 LLM 服务**”。昨日的更新从多个维度推动了这一使命：

- **“快速 (fast)”**：通过升级 FlashInfer 和实验性的 `Breakable CUDA graph`，持续追求推理性能的极致。
- **“便宜 (cheap)”**：`MooncakeStoreConnector` 的磁盘卸载功能直接降低了大规模部署的内存成本，使得在更经济的硬件上运行大型模型成为可能。
- **“简单 (easy)”**：修复 Ultravox 模型的 Bug 和添加池化器测试，提升了模型的兼容性和代码的健壮性，让用户能更轻松、更可靠地使用各种模型。

总体来看，这些提交体现了 vLLM 项目在追求高性能的同时，也在积极解决大规模部署中的实际工程挑战（如内存管理、模型兼容性），并探索更灵活的执行模型，以应对未来更复杂的服务需求。项目正朝着一个更强大、更可靠、更经济的 LLM 服务基础设施方向稳步前进。

## 详细提交记录

### [0867497](https://github.com/vllm-project/vllm/commit/0867497368f390212a3f9684e2e05f698f8d1149)

- **作者**: Artem Perevedentsev
- **时间**: 2026-05-16T21:55:12Z
- **提交信息**: [CI/Build] Bump flashinfer to v0.6.11.post2 (#41711)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>

### [36e74c9](https://github.com/vllm-project/vllm/commit/36e74c9ea4feb5ade38ffa1ea96f24dd73316e02)

- **作者**: Zhewen Li
- **时间**: 2026-05-16T20:34:15Z
- **提交信息**: [KV Connector] Support disk offloading in MooncakeStoreConnector (#42689)

Signed-off-by: Zhewen Li <zhewenli@inferact.ai>
Co-authored-by: Zhewen Li <zhewenli@inferact.ai>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [787bc0d](https://github.com/vllm-project/vllm/commit/787bc0d0313840c16e403dfa2d135781d41d3614)

- **作者**: Taneem Ibrahim
- **时间**: 2026-05-16T18:58:16Z
- **提交信息**: Add unit tests for pooler activation functions (#42824)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [d1586e1](https://github.com/vllm-project/vllm/commit/d1586e1a1242754d2f6ac51f4f16680f7d4b129b)

- **作者**: weizhoublue
- **时间**: 2026-05-16T17:02:54Z
- **提交信息**: Fix: Propagate pinned model revisions into Ultravox secondary weight loading (#42830)

### [8a56da3](https://github.com/vllm-project/vllm/commit/8a56da3845270837424ef4b7ee83ca97a7883025)

- **作者**: Jiangyun Zhu
- **时间**: 2026-05-16T14:04:12Z
- **提交信息**: [Experimental] Breakable CUDA graph (#42304)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [4db300e](https://github.com/vllm-project/vllm/commit/4db300e95fd29f5b1a4a7c34f4fbe91b7e9abb24)

- **作者**: Andreas Karatzas
- **时间**: 2026-05-16T09:35:05Z
- **提交信息**: [ROCm][CI] Removed problematic command override mechanism (#42807)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [657b42b](https://github.com/vllm-project/vllm/commit/657b42b5922d21fef00529144ef5bb5633ad04b1)

- **作者**: Zhewen Li
- **时间**: 2026-05-16T07:26:25Z
- **提交信息**: [Docker][KVConnector] Build mooncake-transfer-engine from source (#42114)

Signed-off-by: Zhewen Li <zhewenli@inferact.ai>
Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Zhewen Li <zhewenli@inferact.ai>
Co-authored-by: khluu <khluu000@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-17
**监控日期**: 2026-05-16
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4787
- **最后更新**: 2026-05-17T15:36:50Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 10
- **主要提交者**: wuhang, Nick Cao, Zhou Taichang

## AI分析总结

好的，作为专业的代码分析助手，我将结合项目背景，对 `vllm-project/vllm-omni` 仓库昨日的提交记录进行分析和总结。

### 昨日更新要点总结

#### 1. 主要更新类型

-   **重构 (Refactor)**：`[Config Refactor]` 和 `[Refactor]` 两个提交，对配置系统和TTS模型配置进行了重构和清理。
-   **功能新增 (Feat)**：`[Feat]` 提交，为Helios模型增加了缓存DiT（Diffusion Transformer）的支持。
-   **Bug修复 (Bugfix)**：`[Bugfix]` 提交，修复了DiT阶段进程命名、内联引擎下的扩散工作进程检测、以及异步chunk请求处理等问题。
-   **CI/测试 (CI/Accuracy)**：`[CI][Accuracy]` 提交，为Qwen-Image和HunyuanImage模型增加了像素级别的精度测试。
-   **版本升级/兼容性 (Rebase/Upgrade)**：`[Rebase]` 和 `[ROCm]` 提交，将项目基础版本升级到vllm v0.21.0，并同步升级了ROCm支持。

#### 2. 关键变更点及其与项目整体方向的关系

-   **配置系统重构** (`[Config Refactor]`): 支持引擎参数的递归合并。这增强了配置的灵活性和可扩展性，为支持更多样化的模型和复杂的参数组合奠定了基础，符合项目“易用”和“服务所有模态模型”的目标。
-   **TTS模型配置清理** (`[Refactor]`): 迁移并清理了CosyVoice3、OmniVoice、VoxCPM等TTS模型的配置。这表明项目正在持续整合和标准化对多种语音合成模型的支持，是“全模态”愿景的重要一环。
-   **Helios缓存DiT支持** (`[Feat]`): 为Helios模型添加了缓存DiT的功能。DiT是扩散模型的核心组件，缓存机制可以显著提升推理速度和效率，直接服务于“快速”和“廉价”的模型服务目标。
-   **基础版本升级** (`[Rebase]`): 将项目基础从vllm旧版本升级到v0.21.0。这是保持项目生命力和兼容性的关键操作，可以获取上游vllm的新特性、性能优化和Bug修复，确保项目能持续受益于vllm生态的发展。
-   **精度测试增强** (`[CI][Accuracy]`): 为Qwen-Image和HunyuanImage模型增加了精度测试。这体现了项目对模型服务质量和可靠性的重视，确保在快速迭代中不会引入回归问题，是“专业”和“可靠”的体现。

#### 3. 对项目的影响和潜在意义

-   **提升开发效率与稳定性**：配置重构和TTS配置清理降低了代码复杂度，提高了可维护性。基础版本升级和精度测试的加入，则直接提升了项目的稳定性和可靠性。
-   **扩展模型支持范围**：对Helios、Qwen-Image、HunyuanImage等模型的持续支持，以及TTS模型的整合，表明项目正在稳步扩展其“全模态”模型生态，覆盖图像生成、图像编辑、语音合成等多个领域。
-   **优化性能与成本**：Helios的缓存DiT功能是性能优化的一个具体例子，有助于降低推理延迟和计算成本，兑现项目“快速”和“廉价”的承诺。
-   **强化平台兼容性**：升级到ROCm 7.2.2，确保了对AMD GPU平台的良好支持，扩大了项目的硬件适用范围。

#### 4. 值得关注的技术点

-   **递归合并引擎参数**：这是一个值得深入研究的配置设计模式，它允许用户通过分层、覆盖的方式灵活地配置复杂的模型服务引擎。
-   **DiT缓存机制**：了解Helios模型如何实现DiT缓存，以及这种缓存策略对推理速度和显存占用的具体影响，对于优化其他扩散模型服务有借鉴意义。
-   **异步chunk请求处理**：`[BugFix]` 中修复的“无pad-token注入”问题，涉及到流式文本生成（如TTS）中一个精细的处理逻辑，对于保证输出质量和稳定性至关重要。

#### 5. 这些提交如何影响项目发展

基于README中“Easy, fast, and cheap omni-modality model serving for everyone”的项目目标，这些提交从多个维度推动了项目发展：

-   **迈向“全模态”**：通过清理TTS配置、增加图像模型（Qwen-Image, HunyuanImage）的测试，项目正在系统性地构建一个覆盖文本、图像、语音等多种模态的服务平台。
-   **追求“快速”与“廉价”**：Helios的缓存DiT支持是性能优化的直接体现。基础版本升级也意味着可以享受到上游vllm社区在性能方面的最新成果。
-   **保障“易用”**：配置系统的重构使得用户能以更灵活、更直观的方式配置复杂的模型，降低了使用门槛。
-   **确保“稳定可靠”**：大量的Bug修复和精度测试的引入，是项目走向成熟、可被信赖的关键步骤。基础版本升级也确保了项目不会因依赖过时而变得不稳定。

**总结**：昨日的更新是一次典型的“夯实基础、扩展边界”的迭代。项目在通过重构和Bug修复提升内部质量的同时，积极引入新模型支持和性能优化，并紧跟上游vllm的发展步伐，稳步朝着构建一个易用、快速、廉价且覆盖全模态的模型服务平台迈进。

## 详细提交记录

### [9c5e35f](https://github.com/vllm-project/vllm-omni/commit/9c5e35f485a7d2037330ea74535e8373c739f350)

- **作者**: Alex Brooks
- **时间**: 2026-05-16T23:33:03Z
- **提交信息**: [Config Refactor] Support Recursive Merging for Engine Args (#3009)

Signed-off-by: Alex Brooks <albrooks@redhat.com>
Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [a64ebf1](https://github.com/vllm-project/vllm-omni/commit/a64ebf103b35fa48f42accf444e4f027c992009e)

- **作者**: Yuanheng Zhao
- **时间**: 2026-05-16T23:32:34Z
- **提交信息**: [Refactor] Migrate and clean up TTS configs: CosyVoice3, OmniVoice, VoxCPM (#3338)

Signed-off-by: yuanheng <jonathan.zhaoyh@gmail.com>
Signed-off-by: Yuanheng Zhao <jonathan.zhaoyh@gmail.com>

### [c08959e](https://github.com/vllm-project/vllm-omni/commit/c08959ee040281ecd310293adeb82067fa2e5932)

- **作者**: TJian
- **时间**: 2026-05-16T15:15:59Z
- **提交信息**: [ROCm] [CI] [Bugfix] Upgrade vllm version to v0.21.0 and ROCm 7.2.2 (#3659)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [c5ac295](https://github.com/vllm-project/vllm-omni/commit/c5ac295e3c9f0b3425843b15964824a89cd271ae)

- **作者**: rongfu.leng
- **时间**: 2026-05-16T13:11:34Z
- **提交信息**: [Feat] Add helios support cache dit (#3470)

Signed-off-by: rongfu.leng <lenronfu@gmail.com>

### [ea35a0c](https://github.com/vllm-project/vllm-omni/commit/ea35a0cc4a35dcdb674af76d8279c084a6aaa181)

- **作者**: Zeng Chuang
- **时间**: 2026-05-16T12:51:31Z
- **提交信息**: [Bugfix]update process name for dit stage (#3602)

Signed-off-by: zengchuang <zengchuang3@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [0f4853f](https://github.com/vllm-project/vllm-omni/commit/0f4853ff86f3fd840f9404535c89961a48eb13e2)

- **作者**: wuhang
- **时间**: 2026-05-16T12:50:29Z
- **提交信息**: [Bugfix] Support diffusion worker dead detect when use inline engine (#3214)

Signed-off-by: wuhang <wuhang6@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [b5e163c](https://github.com/vllm-project/vllm-omni/commit/b5e163cfcabbfdea73469c014766d104d2231e10)

- **作者**: WeiQing Chen
- **时间**: 2026-05-16T12:08:51Z
- **提交信息**: [CI][Accuracy] Add Qwen-Image-2512 Qwen-Image-Edit-2511 pixel accuracy tests (#3502)

Signed-off-by: david6666666 <530634352@qq.com>

### [d647e7e](https://github.com/vllm-project/vllm-omni/commit/d647e7e4cfa3c50bed50cc07e465365bc9627f0b)

- **作者**: dengyunyang
- **时间**: 2026-05-16T11:35:05Z
- **提交信息**: [Hunyuanimage 3.0] hunyuan accuracy test (#3655)

Signed-off-by: dengyunyang <584797741@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [33220b1](https://github.com/vllm-project/vllm-omni/commit/33220b1e39c51d87b982dd1d5e6abd8e20aa8b5a)

- **作者**: Nick Cao
- **时间**: 2026-05-16T11:34:04Z
- **提交信息**: [BugFix] Finish async_chunk requests without pad-token injection (#3613)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [eb4e60e](https://github.com/vllm-project/vllm-omni/commit/eb4e60ee64f2e5cd785b43fdd3af9ff7822b5a4f)

- **作者**: Zhou Taichang
- **时间**: 2026-05-16T10:18:43Z
- **提交信息**: [Rebase] Rebase to vllm v0.21.0 (#3530)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Signed-off-by: Zhou Taichang <tzhouam@connect.ust.hk>
Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Signed-off-by: Divyansh Singhvi <divyanshsinghvi@gmail.com>
Signed-off-by: dsinghvi <divyanshsinghvi@gmail.com>
Signed-off-by: Dnoob <dxpouo@gmail.com>
Signed-off-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>
Signed-off-by: knlnguyen1802 <knlnguyen1802@gmail.com>
Signed-off-by: rein yang <ruiruyang2@gmail.com>
Signed-off-by: Nick Cao <ncao@redhat.com>
Signed-off-by: zhumingjue <zhumingjue@huawei.com>
Signed-off-by: Ricardo Noriega De Soto <rnoriega@redhat.com>
Signed-off-by: lyj-jjj <liuyingjun5@huawei.com>
Signed-off-by: gcanlin <canlinguosdu@gmail.com>
Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: weizhoublue <weizhoublue@github.com>
Signed-off-by: weizhou.lan@daocloud.io <weizhou.lan@daocloud.io>
Signed-off-by: dengyunyang <584797741@qq.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>
Signed-off-by: David Chen <530634352@qq.com>
Signed-off-by: Jie Liu <33612777+keeper-jie@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Signed-off-by: bjf-frz <frz123db@gmail.com>
Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Signed-off-by: KexiongYu <yukexiong1@huawei.com>
Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Signed-off-by: Zeyu Huang | 黃澤宇 <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>
Co-authored-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: dsinghvi <divyanshsinghvi@gmail.com>
Co-authored-by: Dnoob <dxpouo@gmail.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: knlnguyen1802 <knlnguyen1802@gmail.com>
Co-authored-by: Samit <285365963@qq.com>
Co-authored-by: rein yang <73573651+R2-Y@users.noreply.github.com>
Co-authored-by: Nick Cao <ncao@redhat.com>
Co-authored-by: zhumingjue138 <zhumingjue@huawei.com>
Co-authored-by: Ricardo Noriega <rnoriega@redhat.com>
Co-authored-by: lyj-jjj <liuyingjun5@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: gcanlin <canlinguosdu@gmail.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Co-authored-by: weizhoublue <45163302+weizhoublue@users.noreply.github.com>
Co-authored-by: weizhoublue <weizhoublue@github.com>
Co-authored-by: dengyunyang <584797741@qq.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: WeiQing Chen <40507679+david6666666@users.noreply.github.com>
Co-authored-by: Jie Liu <33612777+keeper-jie@users.noreply.github.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: NATURE <wzliu@connect.hku.hk>
Co-authored-by: bjf-frz <frz123db@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Y. Fisher <yukexiong1@huawei.com>
Co-authored-by: Zeyu Huang | 黃澤宇 <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>

---
