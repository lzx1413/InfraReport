# GitHub Stars 合并报告 - 2026-04-23

**合并日期**: 2026-04-24
**监控日期**: 2026-04-23
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


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1857
- **最后更新**: 2026-04-23T22:03:25Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Ting

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **功能新增 (Feat)**: 提交 `1866a25` 引入了全新的“基于注册的内核替换框架”。
- **重构 (Refactor)**: 提交 `06b83eb` 对MoE（混合专家）模块的实现类型进行了重构，使其更具扩展性。
- **破坏性变更 (BREAKING)**: 提交 `1866a25` 被标记为 `BREAKING`，意味着该变更可能不向后兼容，需要用户注意适配。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点1 (06b83eb)**: 将 `moe_implementation` 的类型从 `Literal`（字面量）放宽为 `str`（字符串）。
  - **与项目方向的关系**: 项目VeOmni的目标是“扩展任意模态模型训练”。放宽类型限制，使得用户或开发者可以更容易地引入和指定自定义的MoE实现，而无需修改核心代码库。这直接支持了项目的“可扩展性”和“配方多样性”目标。

- **变更点2 (1866a25)**: 创建了一个基于注册的内核替换框架。
  - **与项目方向的关系**: 这是对项目核心架构的一次重要升级。通过注册机制，用户可以灵活地替换模型中的特定算子（Kernel），而无需改动模型本身的代码。这与VeOmni作为“以模型为中心的分布式配方库”的理念高度契合，允许用户为不同硬件、不同模态或不同性能需求，轻松组合和替换最优的计算内核。

### 3. 对项目的影响和潜在意义
- **提升可扩展性与灵活性**: 两个提交共同增强了VeOmni的模块化程度。开发者可以像搭积木一样，通过注册新的MoE实现或替换内核，来适配新的模型架构或硬件平台。
- **降低定制化门槛**: 内核替换框架的引入，意味着用户无需深入理解VeOmni的整个分布式训练逻辑，就能对特定算子进行性能优化或功能增强。这降低了为项目贡献新特性的门槛。
- **可能带来兼容性成本**: `BREAKING` 标记表明，依赖旧版内核加载方式的用户或插件需要更新。这是为了长期架构健康而付出的短期代价。

### 4. 值得关注的技术点
- **注册机制 (Registration-based)**: 这是软件工程中一种强大的解耦模式。在深度学习框架中，它允许将算子的定义（如CUDA kernel）与模型的定义分离，通过一个中央注册表进行管理。这种模式在PyTorch等框架中也有应用，是构建可扩展系统的最佳实践。
- **`Literal` 到 `str` 的转变**: 这个看似微小的改动，体现了从“强约束”到“开放接口”的设计思路转变。`Literal` 类型用于枚举有限的选项，而 `str` 则允许无限的可能性，为未来的扩展预留了空间。

### 5. 基于项目背景，这些提交如何影响项目发展
- **加速“配方”生态建设**: VeOmni的核心是“配方（Recipe）”。内核替换框架是构建“配方”的关键基础设施。未来，社区可以围绕这个框架贡献针对不同硬件（如NVIDIA H100, AMD MI300）或不同模型（如视觉Transformer, 多模态大模型）的优化内核“配方”，极大地丰富VeOmni的生态。
- **巩固“以模型为中心”的定位**: 通过将内核实现与模型定义解耦，VeOmni让模型开发者可以更专注于模型架构本身，而将性能优化工作交给内核专家。这强化了其作为“模型中心”训练框架的定位，而非一个“算子中心”的框架。
- **为多模态扩展铺平道路**: 不同模态（文本、图像、视频、音频）的模型对算子的需求差异巨大。一个灵活的内核替换框架，使得VeOmni能够优雅地支持这些多样化的计算需求，而不会让核心代码变得臃肿。这是实现“扩展任意模态模型训练”这一宏大目标的关键一步。

## 详细提交记录

### [06b83eb](https://github.com/ByteDance-Seed/VeOmni/commit/06b83ebb6bb8ac738d726ce6e22ecf98b0295dd4)

- **作者**: Ting
- **时间**: 2026-04-23T22:03:20Z
- **提交信息**: [ops, model] refactor: relax moe_implementation Literal to str for extensibility (#689)

### [1866a25](https://github.com/ByteDance-Seed/VeOmni/commit/1866a257bdac6f9a408df31e2bd88f7fa4f099e9)

- **作者**: Ting
- **时间**: 2026-04-23T15:17:03Z
- **提交信息**: [BREAKING][ops, model] feat: registration-based kernel replacement framework (#678)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2210
- **最后更新**: 2026-04-23T17:12:37Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: yihuiwen

## AI分析总结

好的，这是对仓库 `ModelTC/LightX2V` 昨日提交记录的分析总结：

### 1. 主要更新类型
- **功能新增**：两项提交均为新增功能，没有Bug修复或性能优化。

### 2. 关键变更点及其与项目整体方向的关系
- **支持 OpenAI 接口 (`f35e4d1`)**：新增了对 OpenAI API 格式的兼容。这直接服务于项目“轻量级视频生成推理框架”的目标，通过提供标准化的接口，极大地降低了外部应用和开发者集成 `LightX2V` 的门槛，使其能像调用 OpenAI 服务一样使用本框架。
- **添加服务端同步方法脚本 (`fe8e642`)**：新增了一个用于服务端同步的脚本。这增强了框架的部署和运维能力，使其更适合作为生产环境中的服务运行，是项目从“可用”走向“易用”和“可部署”的关键一步。

### 3. 对项目的影响和潜在意义
- **提升生态兼容性**：OpenAI 接口已成为行业事实标准。支持该接口意味着 `LightX2V` 可以无缝接入现有的 AI 应用生态（如各类 AI 前端、自动化工具链），无需用户进行复杂的适配工作。
- **增强服务化能力**：服务端同步脚本的加入，表明项目正在向成熟的、可独立部署的推理服务演进。这对于希望将视频生成能力集成到自身产品中的企业用户至关重要。
- **吸引更多开发者**：标准化的接口和便捷的部署脚本，降低了使用门槛，有助于吸引更多社区贡献者和用户，加速项目发展。

### 4. 值得关注的技术点
- **接口标准化**：`f35e4d1` 提交中，如何实现与 OpenAI API 的兼容是核心。这通常涉及请求/响应格式的映射、认证方式的适配以及可能的参数转换。这是将复杂推理引擎封装成简洁服务的关键技术。
- **服务化架构**：`fe8e642` 提交暗示了项目内部可能采用了客户端-服务器（C/S）架构。同步脚本的加入，意味着需要处理请求排队、并发控制、状态管理等服务端常见问题。

### 5. 基于项目背景，这些提交如何影响项目发展
- **从“框架”到“产品”的转变**：`LightX2V` 的 README 定位为“推理框架”。昨日提交标志着它正从一个需要深度集成的底层框架，向一个提供标准化接口、易于部署的“产品级”服务演进。
- **聚焦于“易用性”和“可部署性”**：在具备核心视频生成能力后，项目当前的发展重点明显转向了提升用户体验和降低使用门槛。这两项更新直接解决了“如何用”和“如何部署”的核心痛点。
- **为商业化或大规模应用铺路**：支持 OpenAI 接口和提供服务端脚本，是任何视频生成服务走向商业化或大规模应用的必要条件。这些更新为 `LightX2V` 在更广泛场景下的应用打下了坚实基础。

## 详细提交记录

### [f35e4d1](https://github.com/ModelTC/LightX2V/commit/f35e4d1995e0058c184d973d096736ffb789995c)

- **作者**: yihuiwen
- **时间**: 2026-04-23T10:24:45Z
- **提交信息**: support openai interface (#1037)

Co-authored-by: yihuiwen <yihuiwen@sensetime.com>

### [fe8e642](https://github.com/ModelTC/LightX2V/commit/fe8e642794c6ca03b9c41925d85ea01f8e3b814e)

- **作者**: yihuiwen
- **时间**: 2026-04-23T08:54:45Z
- **提交信息**: add server sync method script (#1036)

Co-authored-by: yihuiwen <yihuiwen@sensetime.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2036
- **最后更新**: 2026-04-23T19:41:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5483
- **最后更新**: 2026-04-23T20:20:00Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Jinyang Yuan, Perkz Zheng, Jonathan Dierksen

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **性能优化** (PR #3084)
- **功能新增** (PR #2563)
- **Bug修复** (PR #3089)
- **工程/测试改进** (PR #3105)

### 2. 关键变更点及其与项目整体方向的关系

- **性能优化：优化 SM90 (Hopper) 架构上的 MoE 内核 (PR #3084)**
    - **变更点**：为 `cutlass_fused_moe` 后端引入了新的 LDSM (Load-Store Multiple) + 交错查找表 (interleaved-LUT) 权重加载流水线，专门针对 4-bit 权重 (MXFP4, INT4) 与 16/8-bit 激活值的混合精度计算。同时，调整了启发式策略以选择更优的 CUDA 核心配置。
    - **与项目方向的关系**：FlashInfer 的核心目标是提供**高性能的推理 GPU 内核**。MoE (Mixture-of-Experts) 是当前大模型推理的关键技术，而 Hopper (SM90) 是最新的 GPU 架构。此提交直接针对这一关键场景进行深度优化，是项目核心目标的直接体现。

- **功能新增：支持分布式通信原语的组合 (PR #2563)**
    - **变更点**：新增了对 `allreduce`、`allgather` 和 `reducescatter` 等 NCCL 通信原语及其组合（如 `allreduce + allgather`）的支持。为提升性能，实现了基于 NVSHMEM 和 CUDA IPC 的节点内融合内核，并支持流水线以重叠节点内和节点间通信。
    - **与项目方向的关系**：大模型推理正从单卡向多卡、多节点扩展。此提交将 FlashInfer 的能力从单 GPU 内核扩展到了**分布式推理**领域，使其能更好地支持张量并行 (TP) 和流水线并行 (DP) 等策略，是项目向更完整推理解决方案发展的重要一步。

- **Bug修复：修复 FMHA 中 Context SWA 的 page-skip 问题 (PR #3089)**
    - **变更点**：更新了 TensorRT-LLM 生成的 FMHA (Flash Multi-Head Attention) 的 cubin 文件，并同步了相关的头文件，以修复在上下文阶段使用滑动窗口注意力 (SWA) 时出现的 page-skip 错误。
    - **与项目方向的关系**：注意力机制是 Transformer 模型的核心。修复此类 Bug 确保了 FlashInfer 在复杂注意力模式（如 SWA）下的**正确性和稳定性**，这对于其在生产环境中的可靠应用至关重要。

- **工程改进：改进测试报告，处理无结果测试 (PR #3105)**
    - **变更点**：改进了并行测试运行器的报告逻辑，将“无结果”（通常因 OOM 被系统杀死）的测试文件与“失败”的测试文件区分开来，并确保在存在无结果测试时，CI 流程也能正确报告状态。
    - **与项目方向的关系**：这是一个**基础设施改进**。通过更精确地识别和报告测试问题，特别是内存不足 (OOM) 这类资源问题，有助于开发者更快地定位和解决稳定性隐患，从而提升项目的整体质量和开发效率。

### 3. 对项目的影响和潜在意义

- **显著提升 Hopper 架构上的 MoE 推理性能**：PR #3084 带来的 2.66x 到 3.11x 的性能提升，将使 FlashInfer 在 NVIDIA H100/H200 等 Hopper GPU 上运行混合精度 MoE 模型时具有极强的竞争力，吸引更多用户。
- **奠定分布式推理基础**：PR #2563 新增的分布式通信能力，使 FlashInfer 从一个单 GPU 内核库向**多 GPU 推理框架**迈出了关键一步。这为未来支持更大规模模型、更复杂的并行策略（如 TP + DP）铺平了道路。
- **提升生产环境的可靠性**：PR #3089 的 Bug 修复和 PR #3105 的测试改进，共同提升了项目的稳定性和可维护性，这对于将 FlashInfer 集成到生产级推理系统（如 SGLang, vLLM）至关重要。

### 4. 值得关注的技术点

- **LDSM + Interleaved-LUT 流水线**：这是一种针对 Hopper 架构的、用于高效加载低精度权重的先进技术，通过减少内存访问次数和利用硬件特性来提升吞吐量。
- **NVSHMEM 与 CUDA IPC 的融合通信**：在分布式通信中，利用 NVSHMEM 和 CUDA IPC 实现节点内的高效、低延迟通信，并通过流水线技术重叠节点内和节点间通信，是高性能分布式计算中的前沿实践。
- **启发式内核选择**：PR #3084 中对 `cutlass_heuristic.cpp` 的修改，展示了如何通过运行时启发式策略，根据具体问题（如数据类型、矩阵形状）动态选择最优的 CUDA 核心配置，以实现最佳性能。

### 5. 这些提交如何影响项目发展

- **巩固核心优势**：PR #3084 和 PR #3089 分别从性能和正确性两个维度，进一步巩固了 FlashInfer 在**单 GPU 推理内核**领域的领先地位，尤其是在最热门的 MoE 和注意力机制上。
-

## 详细提交记录

### [53bc819](https://github.com/flashinfer-ai/flashinfer/commit/53bc8194761e3eff229180fd6b26799ce83ec55d)

- **作者**: Jonathan Dierksen
- **时间**: 2026-04-23T20:19:54Z
- **提交信息**: Report unit test files with no result (#3105)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Currently, we have a handful of tests during parallel runs that are
being OOM killed due to high memory usage. I previously attempted to
resolve it in https://github.com/flashinfer-ai/flashinfer/pull/2961, but
some of the tests will need a little more pruning before they can be
added in solo as they take too long in addition to consuming tons of
memory.
## 🔍 Related Issues

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
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
* Clearly separate passed/failed tests from tests that produced no
result artifacts; exclude "no result" from failed counts and ensure exit
status reflects both failures and no-result conditions.
* Remove stale result files before runs to prevent misleading outcomes.

* **Chores**
* Improved sequential and parallel test runners and enhanced execution
summary reporting, including explicit counts and listings for test files
with no result.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b809821](https://github.com/flashinfer-ai/flashinfer/commit/b809821333b5ab1c290d2d51cd54b46189891ea7)

- **作者**: Perkz Zheng
- **时间**: 2026-04-23T17:14:38Z
- **提交信息**: [Fmha] update trtllm-gen FMHA cubins and sync headers for context SWA fix (#3089)

<!-- .github/pull_request_template.md -->

## 📌 Description

The branch has 2 commits:
1. Update trtllm-gen FMHA cubins to fix context SWA page-skip — updates
artifacts.py path + checksum
2. Sync trtllm FMHA headers with latest trtllm-gen (from PR #2711) —
cherry-picks header changes to match the new cubin MetaInfo struct

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
* Fixed sparse-attention truncation so sequence-length top-K is applied
correctly when sparse-attention is enabled.

* **Improvements**
* Standardized sparse-attention parameter naming and selection logic to
make behavior more consistent across launches and kernel choices.
* Skip incompatible kernel variants during runtime kernel loading to
avoid incorrect selections.

* **Chores**
* Updated FMHA runtime artifact paths and their checksums for validation
and downloads.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>

### [c9eb3cd](https://github.com/flashinfer-ai/flashinfer/commit/c9eb3cd92e7b798ccf5341122ce4b6c0975a34e0)

- **作者**: Jinyang Yuan
- **时间**: 2026-04-23T16:50:06Z
- **提交信息**: feat: Add support for the combinations of allreduce, allgather, and reducescatter (#2563)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
This PR adds support for the combinations of allreduce,allgather, and
reducescatter:
- allreduce
- allgather
- reducescatter
- allreduce + allgather
- reducescatter + allreduce

The last two communication patterns occur when TP and DP are both
enabled in the attention part.

Besides combining existing NCCL kernels, this PR also implements fused
kernels:
- Intra-node communications are implemented using multicast or CUDA IPC
- Inter-node communications are implemented using NVSHMEM
- Pipeline is implemented to overlap intra-node and inter-node
communications when the message size is large enough
- To support more use cases, the inputs and outputs are not required to
be on symmetric memory even when multicast is used (internal buffers are
on symmetric memory)
- The size of internal buffers is independent of message size because
these buffers are reused

**Update**
Besides using unit tests to verify correctness, the correctness has also
been verified by running GSM8K and GPQA tests using SGLang:
https://github.com/jinyangyuan-nvidia/sglang/tree/dev/mixed_comm

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
* Distributed mixed-communication primitives (all-reduce, all-gather,
reduce-scatter) with fused GPU kernels, NVSHMEM-enabled intra-node
optimizations, topology-aware TP/DP handling, and an autotune path to
pick optimal modes.
* Public APIs to configure/query parallel topology and run mixed-comm
workloads.

* **New Tools**
* Executable benchmark for mixed communication across GPUs/ranks and
improved multi-rank GPU timing aggregation for accurate cluster
measurements.

* **Tests**
* Distributed correctness and cross-mode consistency tests covering
multiple dtypes and local sizes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Jinyang Yuan <154768711+jinyangyuan-nvidia@users.noreply.github.com>

### [d454492](https://github.com/flashinfer-ai/flashinfer/commit/d4544921ca2abee84077679988bfc91f69acd5e8)

- **作者**: Sam (Kesen Li)
- **时间**: 2026-04-23T16:26:57Z
- **提交信息**: perf: optimize MXFP4xBF16 & INT4xFP8 CUTLASS MoE backend for SM90 (#3084)

## Summary

Port [TensorRT-LLM PR
#12451](https://github.com/NVIDIA/TensorRT-LLM/pull/12451) to
FlashInfer's `cutlass_fused_moe` SM90 path. Adds an LDSM +
interleaved-LUT weight-load pipeline for 4-bit weights × 16/8-bit
activations, plus the two preprocessing helpers the new kernel layout
requires.

## Changes

### Kernel
- `mixed_input_utils.hpp` /
`sm90_mma_array_tma_gmma_rs_warpspecialized_mixed_input_.hpp` — sync
with TRT-LLM PR #12451 (LDSM path + FP4/INT4 → BF16 LUT converter).
- `moe_gemm_mixed_utils.{cu,h}` (new) — per-row CUDA kernels for
FP4/INT4 byte interleave.
- `cutlass_heuristic.cpp` — for `has_w4afp8`, skip `CtaShape128x128x128B
+ COOPERATIVE` (register overflow on SM90) and pick COOP / PINGPONG per
tile.
- `moe_gemm_tma_ws_mixed_input_launcher.inl` —
`scheduler.max_swizzle_size = 2`, `raster_order = Heuristic`.

### Python
`flashinfer/fused_moe/core.py` exposes two helpers (re-exported by the
package):
- `interleave_moe_weights_for_hopper_mixed_gemm(weight, quant_type)` —
byte-level interleave for `"fp4"` / `"int4"` packed uint8 weights;
delegates to the C++ kernel above.
- `interleave_moe_scales_for_hopper_mixed_gemm(scales, group_size=32)` —
pure PyTorch reshape + permute matching TRT-LLM's
`WFP4A16FusedMoEMethod.load_quant_scales`, factor = `128 // group_size`.

### Tests — inside `tests/moe/test_trtllm_cutlass_fused_moe.py` (18 new)
- `test_moe_bf16_mxfp4_hopper_correctness` (5 shapes, strict
`assert_close` vs a GPU-side dequantized reference that only
materialises active experts to stay under H200 memory at e=256).
- `test_moe_bf16_mxfp4_hopper_coverage` (5 shapes, percent-based ≥
99.9%).
- `test_moe_bf16_mxfp4_hopper_activations` (3 SwiGLU variants).
- `test_moe_w4a8_hopper_correctness` (2 shapes × bf16/fp16) — envelope
matches the upstream CI shape (h = inter = 512, e = 2); larger exceeds
strict tolerance because of FP8 + INT4 accumulation noise, same as the
existing `test_moe_w4a8`.
- `test_moe_w4a8_hopper_autotune` — smoke that `autotune(True)` doesn't
break the W4A8 path.

All 18 green on H200 in 5.2 s cache-hot.

## Performance

H200 (SM90 / HBM3e), `hidden = 4096, intermediate = 2048, experts = 256,
topk = 6`, bf16 output, MXFP4 weights. `cutlass_fused_moe` median over
`bench_gpu_time`. Weight + scale interleave is a one-shot model-load
step and is excluded from timing. `autotune` column runs one pass under
`autotune(True)` to populate the tactic cache before timing.

| batch | main no-autotune | main autotune | **PR no-autotune** | **PR
autotune** | **speedup (autotune)** |

|------:|-----------------:|--------------:|-------------------:|----------------:|-----------------------:|
| 4 | 0.791 ms | 0.513 ms | **0.221 ms** | **0.193 ms** | **2.66×** |
| 16 | 1.598 ms | 1.607 ms | **0.530 ms** | **0.532 ms** | **3.02×** |
| 64 | 3.761 ms | 3.757 ms | **1.200 ms** | **1.207 ms** | **3.11×** |

---------

Signed-off-by: Jiang Shao <91270701+StudyingShao@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Jiang Shao <91270701+StudyingShao@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3415
- **最后更新**: 2026-04-23T19:43:02Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

好的，根据您提供的项目背景和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
*   **功能新增 (feat)**：本次提交属于新功能开发的一部分。

### 2. 关键变更点及其与项目整体方向的关系
*   **变更点**：改进了API，具体包括：
    *   为LTX-2模型添加了公开预设（public preset）。
    *   完成了资产连接（asset wiring）。
    *   实现了GPU池的翻译/映射（gpu_pool translation）。
*   **与项目方向的关系**：FastVideo项目旨在提供快速、易用的视频生成和微调工具。本次更新直接服务于**提升API的可用性和灵活性**，特别是针对LTX-2模型。通过提供预设和更好的资源管理，降低了用户使用该模型的门槛，并优化了底层资源调度。

### 3. 对项目的影响和潜在意义
*   **影响**：使得LTX-2模型的调用更加标准化和便捷。用户无需手动配置所有参数，可以直接使用预设。同时，资产连接和GPU池映射的改进，为更复杂的多GPU或分布式推理/训练场景奠定了基础。
*   **潜在意义**：这是项目向“生产级”工具迈进的一步。通过抽象化底层资源（如GPU池），项目可以更好地支持大规模部署和资源优化，这对于吸引企业用户和高级开发者至关重要。

### 4. 值得关注的技术点
*   **LTX-2 公开预设**：这表明项目正在为特定模型（LTX-2）建立标准化的配置模板，是提升用户体验的关键设计。
*   **GPU池翻译**：这很可能是一个资源抽象层，允许API根据不同的后端（如单卡、多卡、云服务）自动或手动映射GPU资源，增强了系统的可扩展性和可移植性。

### 5. 基于项目背景，这些提交如何影响项目发展
*   **加速模型落地**：结合README中提到的“快速开始”和“文档”，本次更新直接增强了LTX-2模型的可用性，使得用户能更快地基于该模型进行推理或微调，符合项目“Fast”的核心理念。
*   **完善基础设施**：资产连接和GPU池管理是视频生成工具链中重要的基础设施。这些改进表明项目正在从“能用”向“好用、易扩展”发展，为未来支持更多模型和更复杂的计算场景（如大规模并行生成）打下了坚实基础。
*   **增强社区吸引力**：更友好的API和预设配置会降低新用户的尝试成本，有助于吸引更多社区成员参与使用和贡献，推动项目生态的繁荣。

## 详细提交记录

### [70ee5d2](https://github.com/hao-ai-lab/FastVideo/commit/70ee5d230cda9651b88ada04be97ed94179bc482)

- **作者**: William Lin
- **时间**: 2026-04-23T18:36:45Z
- **提交信息**: [feat] [6/n] Improve API: LTX-2 public preset + asset wiring + gpu_pool translation (#1239)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33423
- **最后更新**: 2026-04-23T17:18:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 397
- **最后更新**: 2026-04-23T16:31:28Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12291
- **最后更新**: 2026-04-23T16:33:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 26323
- **最后更新**: 2026-04-23T21:53:04Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 13
- **主要提交者**: Byron Hsu, Jie Hao, zijiexia

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型

- **Bug修复 (Bug Fix)**: 占比最高，涉及多个后端和功能模块。
- **功能新增 (Feature)**: 包括新的硬件支持、性能优化和可观测性功能。
- **性能优化 (Performance)**: 针对特定硬件（AMD）和推理模式（Disaggregated Prefill）的优化。
- **文档更新 (Documentation)**: 新增了模型使用指南（Cookbook）和硬件配置说明。
- **CI/基础设施 (CI/Infrastructure)**: 工作流整合和修复，提升开发效率。

### 2. 关键变更点及其与项目整体方向的关系

- **`[PD+DP] Allow PrefillDelayer in disaggregated-prefill mode`**: 在分离式预填充（Disaggregated Prefill）模式下，允许使用“预填充延迟器”（PrefillDelayer）。这与项目追求的高效、灵活推理架构方向一致，旨在优化资源利用率和吞吐量。
- **`[AMD] Use bpreshuffle FP8 blockscale GEMM to replace ABScale GEMM`**: 为AMD硬件引入了新的FP8块缩放GEMM内核，替换了原有的ABScale GEMM。这直接响应了项目README中提到的“支持AMD GPU”的目标，是提升AMD平台推理性能的关键一步。
- **`feat: add OpenTelemetry tracing to DiffGenerator`**: 为扩散模型生成器（DiffGenerator）添加了OpenTelemetry追踪功能。这表明项目在关注核心推理性能的同时，也开始重视可观测性和运维能力，这对于生产环境部署至关重要。
- **`[bug fix] has_fp8_weights_in_checkpoint: handle HF repo IDs, not just local paths`**: 修复了FP8权重检查点检测函数，使其能处理Hugging Face仓库ID。这增强了与Hugging Face生态的兼容性，降低了用户使用FP8模型的门槛。
- **`docs: add Hunyuan 3 Preview cookbook`**: 新增了混元3预览版的Cookbook。这体现了项目积极跟进并支持最新、最热门的开源模型，以保持其生态的活力和吸引力。

### 3. 对项目的影响和潜在意义

- **提升AMD平台竞争力**: 通过引入新的FP8 GEMM内核，SGLang在AMD GPU上的推理性能有望得到显著提升，这对于吸引AMD用户、扩大硬件生态覆盖范围具有重要战略意义。
- **增强生产环境可靠性**: 修复了多个Bug（如Ascend后端、NVML内存查询、GLM-5模型崩溃等），并增加了OpenTelemetry追踪，这些改进共同提升了项目的稳定性和可运维性，使其更适合在生产环境中部署。
- **降低用户使用门槛**: 修复FP8权重检查点对HF仓库ID的支持，以及新增模型Cookbook，都直接降低了用户使用高级功能（如FP8量化）和新模型的难度，有助于吸引更多用户。
- **优化资源调度**: 在分离式预填充模式下引入PrefillDelayer，为更精细化的资源调度和负载均衡提供了可能，有助于提升集群整体效率。

### 4. 值得关注的技术点

- **FP8 GEMM内核替换**: `bpreshuffle FP8 blockscale GEMM` 是一种针对AMD架构优化的矩阵乘法实现。关注其性能对比数据，可以了解SGLang在AMD平台上的优化深度。
- **分离式预填充 (Disaggregated Prefill)**: 这是当前大模型推理领域的热门技术，通过将预填充和解码阶段分离到不同节点，可以显著提升吞吐量。`PrefillDelayer` 的引入是对该模式的进一步精细化控制。
- **OpenTelemetry集成**: 这表明项目开始采用行业标准的可观测性框架。未来，用户可以通过Jaeger、Prometheus等工具监控SGLang服务的性能瓶颈和运行状态。
- **Ascend NPU支持**: 多个提交涉及Ascend后端的Bug修复，表明项目对华为昇腾硬件的支持正在持续完善中。

### 5. 基于项目背景，这些提交如何影响项目发展

根据README，SGLang是一个专注于**快速、高效的大模型推理框架**，强调**灵活性**和**易用性**，并明确支持**NVIDIA、AMD、Intel、Ascend**等多种硬件。

- **强化核心优势**: 对AMD FP8 GEMM的优化、分离式预填充的改进，直接强化了项目在“高性能推理”这一核心优势上的竞争力。
- **拓宽生态边界**: 修复FP8权重检查点、新增模型Cookbook、完善Ascend后端，这些工作都在不断降低用户使用门槛，拓宽SGLang的模型和硬件生态边界，使其成为一个更通用的推理平台。
- **迈向生产就绪**: 增加OpenTelemetry追踪、修复多个稳定性Bug，标志着项目正从“功能可用”向“生产就绪”迈进，这对于吸引企业级用户至关重要。
- **保持技术前沿**: 快速跟进并支持混元3等最新模型，体现了项目团队对技术趋势的敏锐洞察，有助于维持SGLang在社区中的领先地位。

**总结**: 昨日的更新是SGLang项目在**性能、兼容性、稳定性和可观测性**四个维度上的一次均衡推进。这些工作共同巩固了其作为高性能、多硬件、易用的大模型推理框架的地位，并为其向更成熟的生产级平台演进奠定了坚实基础。

## 详细提交记录

### [6428392](https://github.com/sgl-project/sglang/commit/6428392b6fd4170117a2a0f26b853a209cbc543b)

- **作者**: Jia Guo
- **时间**: 2026-04-23T21:52:58Z
- **提交信息**: ci: fix cu129 wheel tagging + pipefail-abort in install script (follow-up to #23497) (#23587)

### [1721035](https://github.com/sgl-project/sglang/commit/17210350fde2b7a19220cfffdc45985e174401c2)

- **作者**: Byron Hsu
- **时间**: 2026-04-23T21:51:16Z
- **提交信息**: [PD+DP] Allow PrefillDelayer in disaggregated-prefill mode (#23588)

### [2882a13](https://github.com/sgl-project/sglang/commit/2882a136bf6cffae898d9330ff14bf3c50c99dfb)

- **作者**: Kangyan-Zhou
- **时间**: 2026-04-23T21:06:01Z
- **提交信息**: [CI] Consolidate Docker release workflows into reusable workflow (#22541)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [579bd0b](https://github.com/sgl-project/sglang/commit/579bd0b152a1e70c7a30fbb47e359e6057500a14)

- **作者**: Alex Nails
- **时间**: 2026-04-23T19:56:49Z
- **提交信息**: [bug fix] has_fp8_weights_in_checkpoint: handle HF repo IDs, not just local paths (#23542)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [9b2f7f8](https://github.com/sgl-project/sglang/commit/9b2f7f8a91d426b51bb78fe1360541a629e08565)

- **作者**: zijiexia
- **时间**: 2026-04-23T19:01:58Z
- **提交信息**: docs: split MI300X and MI325X options in GLM-5.1 generator (#23540)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [80125fe](https://github.com/sgl-project/sglang/commit/80125febb16c6c1e0950d77361229a16083b3051)

- **作者**: WangHao-hw
- **时间**: 2026-04-23T17:23:35Z
- **提交信息**: [BUGFIX]Fix Ascend backend pre-allocated range in NPU Graph Mode. (#22778)

### [c6872fc](https://github.com/sgl-project/sglang/commit/c6872fc8fb9aca25ac6c035ea876ee34f021f923)

- **作者**: Jinghong Li
- **时间**: 2026-04-23T16:26:04Z
- **提交信息**: Fix: fallback to torch API when NVML memory query is not supported (#23426)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [86ed068](https://github.com/sgl-project/sglang/commit/86ed0680d7b873241425e9bdf70a82ce74951e3e)

- **作者**: Jie Hao
- **时间**: 2026-04-23T16:25:23Z
- **提交信息**: feat: add OpenTelemetry tracing to DiffGenerator (#21254)

### [76e4c5a](https://github.com/sgl-project/sglang/commit/76e4c5a1f8565232584d46671aa07d3fe2c20422)

- **作者**: Arseniy Mironov
- **时间**: 2026-04-23T16:21:30Z
- **提交信息**: [Diffusion][NPU][Bugfix] Ascend_fa crashes when sequence parallelism is used. (#23572)

Co-authored-by: Napkin-AI <arseniy.mironov.dev@gmail.com>

### [54e21bb](https://github.com/sgl-project/sglang/commit/54e21bb3a585b7e9588f4ba7f5ce8dbe5492e047)

- **作者**: Baichuan
- **时间**: 2026-04-23T11:30:57Z
- **提交信息**: [fix] Fix dynamic chunking profiling crash on GLM-5 models (#23060)

Co-authored-by: liubaichuan <liubaichuan@infini-ai.com>

### [4868e36](https://github.com/sgl-project/sglang/commit/4868e367f85181cd6bd8f6aaddca6a7e02db18ed)

- **作者**: Xinyuan Tong
- **时间**: 2026-04-23T09:44:47Z
- **提交信息**: docs: add Hunyuan 3 Preview cookbook (#23532)

### [cd459af](https://github.com/sgl-project/sglang/commit/cd459af4e272ea7449e1a61e7999a0a0aa55e3d1)

- **作者**: Xinyi Song
- **时间**: 2026-04-23T08:51:30Z
- **提交信息**: [AMD] Use bpreshuffle FP8 blockscale GEMM to replace ABScale GEMM (#23319)

Co-authored-by: HaiShaw <hixiao@gmail.com>

### [fd88a1c](https://github.com/sgl-project/sglang/commit/fd88a1c5623fc1d341404dd9f1ddfbf968189b33)

- **作者**: Bingxu Chen
- **时间**: 2026-04-23T07:43:23Z
- **提交信息**: [AMD] skip deterministic inference for MLA FP8 test (#23382)

Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1152
- **最后更新**: 2026-04-23T10:52:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 77885
- **最后更新**: 2026-04-23T21:51:58Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 19
- **主要提交者**: Nicolò Lucchesi, Kunshang Ji, almayne

## AI分析总结

好的，根据您提供的 `vllm-project/vllm` 仓库的README摘要和昨日提交记录，以下是分析总结：

### 1. 主要更新类型

-   **Bug修复 (Bugfix):** 4项
-   **功能新增 (Feature):** 2项 (模型支持、CLI参数)
-   **重构 (Refactor):** 3项 (MoE、编译、模型架构识别)
-   **硬件支持 (Hardware Support):** 4项 (NVIDIA Jetson, AMD ROCm, Intel XPU, CPU)
-   **CI/测试 (CI/Test):** 2项
-   **构建/编译 (Build/Compilation):** 2项 (CUDA版本、编译缓存)
-   **性能优化 (Performance):** 1项 (CPU exp计算)

### 2. 关键变更点及其与项目方向的关系

-   **核心性能与稳定性：**
    -   **[Bugfix] 修复工作区resize导致GPU内存泄漏 (7ff65b1):** 直接提升了服务稳定性和内存效率，符合“cheap”和“fast”的目标。
    -   **[Bugfix] 注意力后端自动选择考虑批次不变性 (b7a2605):** 优化了不同batch size下的推理性能，是“fast”方向的关键优化。
    -   **[Bugfix] 编译缓存键包含inductor/functorch配置 (424033f):** 确保编译缓存的正确性，避免因配置不同导致错误，提升开发和生产环境的可靠性。

-   **硬件生态扩展：**
    -   **[NVIDIA] 新增Jetson Thor (sm_110) 支持 (7f95a66):** 扩展了vLLM在边缘计算和机器人等嵌入式AI领域的应用。
    -   **[ROCm] 实现GPU到NUMA节点检测 (0098db9) & 新增gfx1102/gfx1103支持 (4b7869d):** 强化了对AMD GPU的支持，特别是NUMA感知能力对多卡场景的性能至关重要，符合“for everyone”的愿景。
    -   **[XPU] 升级torch 2.11 (53ecc80):** 保持对Intel GPU的兼容性，跟随上游框架发展。
    -   **[CPU] 低精度数据类型快速exp计算 (2f314bc):** 优化了CPU推理性能，扩大了vLLM在无GPU环境下的适用性。

-   **模型与架构演进：**
    -   **[Model] 支持Hy3 preview (d0009dd):** 紧跟最新模型发展，保持vLLM对前沿模型的支持。
    -   **[MoE Refactor] 移动XPU MoE代码 & 重命名函数 (1b1c01d, 1c2c1eb):** 对混合专家模型（MoE）代码进行模块化和规范化重构，为未来更复杂的MoE支持（如DeepSeek-V2）打下基础。
    -   **[Misc] 使用模型架构转换器识别双向模型 (da1e731):** 自动化模型架构识别，减少手动配置，提升易用性。

-   **部署与易用性：**
    -   **[DP][Ray] 将控制bundle固定到首个GPU bundle节点 (e9ba519):** 优化了Ray分布式部署的稳定性，避免控制节点与GPU节点分离导致的网络延迟或失败。
    -   **[Misc] 支持人类可读的JSON CLI参数 (9c2492e):** 提升命令行使用体验，例如直接输入`1G`代替`1073741824`，更直观。
    -   **[Build] 默认CUDA切换至13.0 (3ed5231):** 拥抱最新CUDA生态，为未来性能优化和新特性铺路。

### 3. 对项目的影响和潜在意义

-   **稳定性与可靠性提升：** 内存泄漏修复和编译缓存修复直接减少了生产环境中的潜在故障，对“cheap”（减少资源浪费）和“easy”（减少运维负担）有直接贡献。
-   **性能优化持续深化：** 注意力后端选择优化和CPU exp计算优化表明vLLM在持续挖掘不同硬件和场景下的性能潜力，巩固其“fast”的定位。
-   **硬件支持版图扩张：** 对NVIDIA Jetson、AMD最新GPU、Intel XPU的持续投入，以及CPU性能优化，显著扩大了vLLM的潜在用户群，完全符合“for everyone”的使命。
-   **代码架构健康度提升：** MoE重构和模型架构识别重构是内部工程质量的体现，为未来更复杂、更高效的功能开发提供了更清晰、更可维护的基础。

### 4. 值得关注的技术点

-   **NUMA感知 (0098db9):** 在多插槽服务器上，GPU和CPU之间的NUMA拓扑对性能影响巨大。vLLM实现此检测，可以更智能地分配内存和计算任务，是高性能推理的关键技术。
-   **注意力后端自动选择 (b7a2605):** 这是一个非常实用的优化。不同batch size下，FlashAttention、PagedAttention等后端的性能表现不同。让框架自动选择最优后端，能显著提升吞吐量和延迟表现。
-   **MoE代码重构 (1b1c01d, 1c2c1eb):** 将特定硬件（XPU）的MoE实现移入通用`fused_moe`模块，并统一命名规范。这表明vLLM正在将Mo

## 详细提交记录

### [7ff65b1](https://github.com/vllm-project/vllm/commit/7ff65b19003be4955d2d5d1428e7d94d082559d0)

- **作者**: czhu-cohere
- **时间**: 2026-04-23T20:50:05Z
- **提交信息**: [Bugfix] Fix workspace resize leaking reserved GPU memory (#39226)

Signed-off-by: root <conway.zhu@cohere.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7f95a66](https://github.com/vllm-project/vllm/commit/7f95a66cbffcd111c6d37abdcb7ca297cec47b78)

- **作者**: Johnny
- **时间**: 2026-04-23T19:42:14Z
- **提交信息**: [NVIDIA] Add sm_110 (Jetson Thor) to CUDA 13.0 build targets (#39233)

### [1b1c01d](https://github.com/vllm-project/vllm/commit/1b1c01de39425f5ccce2ffc45f0ce3eb9fc2ce2c)

- **作者**: Jackmin801
- **时间**: 2026-04-23T17:38:10Z
- **提交信息**: [MoE] Move xpu moe to fused_moe/experts/ (#40568)

Signed-off-by: Jackmin801 <ongjackm@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [e9ba519](https://github.com/vllm-project/vllm/commit/e9ba519f450fd0c3eea5cda44e73eec3ad34f654)

- **作者**: shaharmor98
- **时间**: 2026-04-23T17:21:13Z
- **提交信息**: [DP][Ray] Pin DP control bundle to same node as first GPU bundle (#39167)

Signed-off-by: Shahar Mor <smor@nvidia.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5ef33ab](https://github.com/vllm-project/vllm/commit/5ef33ab250b3904da375ecb18bdda00a4a73c3a8)

- **作者**: Or Ozeri
- **时间**: 2026-04-23T17:00:45Z
- **提交信息**: [kv_offload+HMA][10/N]: Support load with multiple KV groups (#39402)

Signed-off-by: Or Ozeri <oro@il.ibm.com>

### [1c2c1eb](https://github.com/vllm-project/vllm/commit/1c2c1eb8b9fdd2e67c45afb6123ccc07c0177555)

- **作者**: bnellnm
- **时间**: 2026-04-23T15:22:34Z
- **提交信息**: [MoE Refactor] Rename FusedMoE.make_expert_params_mapping to fused_moe_make_expert_params_mapping (#40671)

Signed-off-by: Bill Nell <bnell@redhat.com>

### [8824f50](https://github.com/vllm-project/vllm/commit/8824f50f1f1475fb07cc0c20da260e2e5a355cbb)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-04-23T15:20:12Z
- **提交信息**: [CI] Split disaggregated tests into own test-area (#40623)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [0098db9](https://github.com/vllm-project/vllm/commit/0098db9ec1b19138843fee3147b61bbdbec0cd05)

- **作者**: pschlan-amd
- **时间**: 2026-04-23T15:08:48Z
- **提交信息**: [ROCm] Implement GPU-to-NUMA-node detection (#40015)

Signed-off-by: Patrick Schlangen <pschlan@amd.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [53ecc80](https://github.com/vllm-project/vllm/commit/53ecc807c0e323aea2f2a48dfdae71be838c4f5c)

- **作者**: Kunshang Ji
- **时间**: 2026-04-23T15:07:35Z
- **提交信息**: [XPU] Upgrade torch 2.11 for xpu (#37947)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [b7a2605](https://github.com/vllm-project/vllm/commit/b7a26050200e20917871a4a6b09df0bc9ea3fdc7)

- **作者**: Srreyansh Sethi
- **时间**: 2026-04-23T14:57:03Z
- **提交信息**: [Bugfix] Make Attention Backend Auto-Selection Batch-Invariance-Aware (#40193)

Signed-off-by: Srreyansh Sethi <srreyansh.sethi@gmail.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d0009dd](https://github.com/vllm-project/vllm/commit/d0009ddb0b96e95bcfae6038e9b8673bd2263058)

- **作者**: stevenkuang
- **时间**: 2026-04-23T14:08:26Z
- **提交信息**: [Model] Support Hy3 preview (#40681)

Signed-off-by: stevenkuang <stevenkuang@tencent.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [424033f](https://github.com/vllm-project/vllm/commit/424033f4fceeb5a1469fa77dfa7fc0c5d60f002d)

- **作者**: Richard Zou
- **时间**: 2026-04-23T13:52:59Z
- **提交信息**: [Bugfix] Include inductor and functorch configs in compilation cache key (#40627)

Signed-off-by: Richard Zou <zou3519@gmail.com>

### [da1e731](https://github.com/vllm-project/vllm/commit/da1e7311cad640e008284c2fb1754f5f692259c8)

- **作者**: Isotr0py
- **时间**: 2026-04-23T13:42:52Z
- **提交信息**: [Misc] use model arch converter for bidi models identification (#40701)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [01cb41d](https://github.com/vllm-project/vllm/commit/01cb41dcf5a3dc81a0e3f2fc484554ce2d6466b4)

- **作者**: xiangdong
- **时间**: 2026-04-23T13:42:22Z
- **提交信息**: [XPU][CI]Temporary disable 3 cases on Intel GPU in CI (#40683)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [2f314bc](https://github.com/vllm-project/vllm/commit/2f314bc5e6706bffe77933ae5b13756d04641ed8)

- **作者**: almayne
- **时间**: 2026-04-23T13:14:44Z
- **提交信息**: [CPU] Added faster exp routine for lower precision data types. (#38112)

Signed-off-by: Anna Mayne <anna.mayne@arm.com>
Co-authored-by: Fadi Arafeh <fadi.arafeh@arm.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [2196bac](https://github.com/vllm-project/vllm/commit/2196bac1359a62a29f76936f37380235cc47f096)

- **作者**: BadrBasowid
- **时间**: 2026-04-23T13:10:36Z
- **提交信息**: [Compilation] Refactor SiluMul activation+quant Fusion Pass (#39684)

Signed-off-by: BadrBasowid <badr.basowid@gmail.com>

### [4b7869d](https://github.com/vllm-project/vllm/commit/4b7869d6bc64f5b124e2403891b4c2e29713bbf5)

- **作者**: Matthias Gehre
- **时间**: 2026-04-23T08:32:04Z
- **提交信息**: [ROCm] Add gfx1102/gfx1103 support (#40037)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>

### [4a79262](https://github.com/vllm-project/vllm/commit/4a79262e0f560c50a9831ee672a853e598047ee5)

- **作者**: liuzhenwei
- **时间**: 2026-04-23T08:22:28Z
- **提交信息**: [UT][Hardware] let torchrun example tests use the default backend (#39879)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [3ed5231](https://github.com/vllm-project/vllm/commit/3ed5231c6a7a9042a6ac4000e569ad2d85a21b9a)

- **作者**: Shengqi Chen
- **时间**: 2026-04-23T07:51:28Z
- **提交信息**: [Build] Switch default CUDA to 13.0, update CUDA architecture lists, clean up stale build-args (#39878)

Signed-off-by: Shengqi Chen <harry-chen@outlook.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [9c2492e](https://github.com/vllm-project/vllm/commit/9c2492e501d91d5c69a163084123a06fd9ce25d3)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-04-23T07:42:23Z
- **提交信息**: [Misc] Support Human-readable (k/K/m/M..) json cli arg (#40473)

Signed-off-by: NickLucche <nlucches@redhat.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-04-24
**监控日期**: 2026-04-23
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4452
- **最后更新**: 2026-04-23T21:58:34Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: Hui., Ricardo Noriega, yuefeng Wu

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型

*   **性能优化 (Performance):** 3项
*   **Bug修复 (BugFix):** 1项
*   **功能新增 (Feature):** 1项
*   **测试 (Test):** 1项

### 2. 关键变更点及其与项目整体方向的关系

*   **性能优化 (核心方向):**
    *   **[Wan2.2] 融合RMSNorm:** 针对NVIDIA NPU (华为昇腾) 优化了Wan2.2模型的RMSNorm算子，通过融合操作提升性能。
    *   **[通用] 融合RoPE:** 使用`mindiesd`库的融合RoPE (旋转位置编码) 和缓存机制，提升模型推理效率。这通常对Transformer类模型有广泛影响。
    *   **与项目方向的关系:** 项目目标是“Easy, fast, and cheap omni-modality model serving”。性能优化直接服务于“fast”和“cheap”的目标，通过降低计算开销和延迟，使多模态服务更高效、成本更低。

*   **Bug修复 (稳定性保障):**
    *   **[Qwen3-TTS] 修复`code2wav`失败:** 修复了当`enforce_eager`参数为`false`时，Qwen3-TTS模型在生成音频时出现的错误。这确保了模型在非Eager模式（通常用于图模式优化）下的正确性。
    *   **与项目方向的关系:** 修复Bug是保障“Easy”使用体验的关键。确保不同配置下模型都能稳定运行，降低了用户的使用门槛和调试成本。

*   **功能新增 (扩展能力):**
    *   **[LTX-2.3] 视频生成模型支持:** 新增了对LTX-2.3视频生成模型的支持。
    *   **与项目方向的关系:** 这直接扩展了项目的“omni-modality”能力。从文本、图像、音频扩展到视频生成，使项目覆盖了更广泛的多模态场景，朝着“服务于所有人的全模态模型”目标迈进。

*   **测试 (质量保证):**
    *   **[稳定性测试] 新增测试用例:** 为Wan2.2, Qwen-TTS, Qwen3-Omni, Qwen-Image等模型添加了稳定性测试用例，并修改了测试框架配置。
    *   **与项目方向的关系:** 测试是保障“Easy”和“cheap”的基础。通过自动化测试，可以及早发现回归问题，确保模型服务的稳定性和可靠性，降低维护成本。

### 3. 对项目的影响和潜在意义

*   **性能提升:** 针对特定硬件（NPU）和通用算子的优化，将显著提升Wan2.2等模型的推理速度和吞吐量，降低服务成本。
*   **稳定性增强:** 修复Qwen3-TTS的Bug，并增加稳定性测试，提升了项目整体的健壮性和用户体验，使其更适合生产环境。
*   **生态扩展:** 支持LTX-2.3视频生成模型，标志着项目从“文本/图像/音频”向“视频”领域的重要拓展，吸引了更广泛的用户群体和开发者社区。
*   **硬件适配深化:** 对NPU的专项优化（Wan2.2）表明项目正在积极适配不同硬件平台，以提供更灵活、更低成本的部署选项。

### 4. 值得关注的技术点

*   **`fused RMSNorm`:** 这是一种将归一化层中的多个操作合并为单个内核的技术，能有效减少内存访问和内核启动开销，是高性能推理的常见优化手段。
*   **`mindiesd` 库:** 这是一个来自华为昇腾生态的算子库，用于提供高性能的融合算子。项目引入该库，表明其正在深度利用特定硬件（NPU）的软件栈来优化性能。
*   **`enforce_eager` 参数:** 这是vLLM等推理框架中的一个关键参数，用于控制是否强制使用Eager模式（逐层执行）而非图模式（编译优化）。修复其相关Bug，确保了图模式优化的可用性。
*   **LTX-2.3模型:** 这是一个新兴的视频生成模型，其架构和推理方式与传统的图像/语言模型不同。支持它意味着项目需要处理视频编解码、帧序列管理等新的技术挑战。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **巩固“Fast”和“Cheap”的核心优势:** 性能优化（RMSNorm, RoPE）是项目持续打磨其核心竞争力的体现。通过不断降低延迟和计算成本，vllm-omni旨在成为多模态模型服务领域最高效的选择。
*   **践行“Easy”的承诺:** Bug修复和稳定性测试的投入，表明项目不仅追求速度，也重视可靠性和易用性。这有助于吸引更多非专业用户，降低他们部署复杂多模态模型的心理和技术门槛。
*   **迈向真正的“Omni-modality”:** 新增视频生成模型支持是项目发展路径上的一个里程碑。它标志着vllm-omni正在从一个支持多种模态的“多模态”服务，向一个能处理、生成和理解所有主流模态（文本、图像、音频、视频）的“全模态”服务演进。
*   **构建开放的硬件生态:** 针对NPU的优化，显示了项目不局限于单一硬件（如NVIDIA GPU），而是积极拥抱多样化的硬件生态（如华为昇腾）。这增强了项目的适应性和生命力，使其能在更广泛的云

## 详细提交记录

### [19980bb](https://github.com/vllm-project/vllm-omni/commit/19980bb37c334b9120ada91b1a78578a639364ef)

- **作者**: lyj-jjj
- **时间**: 2026-04-23T18:25:10Z
- **提交信息**: [Perf][Wan2.2] Add fused RMSNorm replace WanRMS_norm on npu (#3067)

Signed-off-by: lyj-jjj <liuyingjun5@huawei.com>

### [c8efdbd](https://github.com/vllm-project/vllm-omni/commit/c8efdbd671473d534d7c464e86158427ef22441c)

- **作者**: yuefeng Wu
- **时间**: 2026-04-23T13:54:56Z
- **提交信息**: [BugFix]: Fix Qwen3-TTS code2wav fails when enforce_eager: false (#2868)

Signed-off-by: wuyuefeng <565948592@qq.com>

### [95a07f7](https://github.com/vllm-project/vllm-omni/commit/95a07f7732900974d9e608b39f36e5b2e6518442)

- **作者**: Hui.
- **时间**: 2026-04-23T09:47:43Z
- **提交信息**: [PERF]use mindiesd fused rope and rope cache (#2571)

Signed-off-by: Hui <1779066624@qq.com>
Signed-off-by: Hui. <62495465+Hu1Lcode@users.noreply.github.com>
Co-authored-by: WeiQing Chen <40507679+david6666666@users.noreply.github.com>

### [47edee1](https://github.com/vllm-project/vllm-omni/commit/47edee1a79423343a75ee9922ae529e13718acc5)

- **作者**: zhumingjue138
- **时间**: 2026-04-23T09:14:48Z
- **提交信息**: [Test] add stability test case for wan2.2, qwen-tts, qwen3-omni and qwen-image model and modified conftest.py in test/dfx/ (#2817)

Signed-off-by: zhumingjue <zhumingjue@huawei.com>
Signed-off-by: zhumingjue138 <zhumingjue@huawei.com>

### [05c6c9a](https://github.com/vllm-project/vllm-omni/commit/05c6c9a0b63a0ae05b393764f93e563f78243a75)

- **作者**: Ricardo Noriega
- **时间**: 2026-04-23T08:51:51Z
- **提交信息**: feat: add LTX-2.3 video generation model support (#2893)

Signed-off-by: Ricardo Noriega De Soto <rnoriega@redhat.com>

---
