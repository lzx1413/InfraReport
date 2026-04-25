# GitHub Stars 合并报告 - 2026-04-24

**合并日期**: 2026-04-25
**监控日期**: 2026-04-24
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


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1859
- **最后更新**: 2026-04-25T09:36:21Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2216
- **最后更新**: 2026-04-25T11:55:12Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: zhtshr

## AI分析总结

好的，这是对仓库 `ModelTC/LightX2V` 昨日提交记录的分析总结。

### 1. 主要更新类型

*   **功能新增**：这是本次更新的核心。具体包括：
    *   新增了分布式推理的配置文件和示例脚本。
    *   引入了动态工作负载模拟机制。
    *   增强了网络连接的可靠性和协议处理能力。
*   **性能优化**：通过支持分块数据传输，优化了大张量的传输效率。
*   **重构**：对`disagg`（解耦）连接逻辑进行了重构，以支持更复杂的分布式场景。

### 2. 关键变更点及其与项目整体方向的关系

*   **新增分布式推理配置文件**：为控制器、编码器、变换器和解码器四种模式分别创建了配置文件。这直接服务于项目“轻量级视频生成推理框架”的目标，通过将模型的不同组件解耦并独立配置，为在分布式环境中部署和扩展视频生成管线奠定了基础。
*   **引入动态工作负载模拟**：新增了 `wan22_i2v_workload_stages.json` 和 `run_user.py` 脚本。这允许开发者模拟真实世界中用户请求的波动（如预热、高峰期），这对于测试和验证框架在高并发、动态负载下的稳定性和性能至关重要，是项目走向生产环境的关键一步。
*   **增强`disagg`连接可靠性**：改进了IP地址处理（强制使用IPv4回环地址）、错误处理和状态同步。这些改动提升了框架在复杂网络环境（如混合IP协议）下的健壮性，减少了因网络问题导致的推理失败，直接提升了框架的可靠性。
*   **支持分块数据传输**：通过环境变量 `MOONCAKE_TRANSFER_CHUNK_BYTES` 控制。视频推理涉及大量张量数据，分块传输可以避免一次性发送巨大数据包导致的网络阻塞或内存溢出，是提升大规模视频生成任务性能的有效手段。
*   **更新ZMQ通信协议**：在消息中包含 `receiver_engine_rank` 信息。这确保了在分布式设置中，数据包能够被精确地路由到正确的目标引擎（如特定的编码器或变换器实例），是实现多节点、多引擎协同工作的核心。

### 3. 对项目的影响和潜在意义

*   **从单机走向分布式**：本次更新标志着项目从单机推理原型向分布式推理系统的实质性迈进。新增的配置、脚本和协议改进，为构建一个可扩展、可配置的分布式视频生成服务提供了核心组件。
*   **提升工程化水平**：动态负载模拟、健壮的网络连接和分块传输等特性，都是生产级推理系统所必需的。这些更新显著提升了项目的工程化成熟度，使其更接近实际部署和商业应用。
*   **增强可测试性和可调试性**：通过模拟动态负载和详细的配置，开发者可以更容易地对系统进行压力测试和性能调优，加速开发迭代。

### 4. 值得关注的技术点

*   **`DISAGG_FORCE_IPV4_LOOPBACK` 环境变量**：这个设计巧妙地解决了在同时支持IPv4和IPv6的混合网络环境中，因回环地址解析不一致导致的连接问题，是一个值得借鉴的健壮性设计。
*   **`MOONCAKE_TRANSFER_CHUNK_BYTES` 环境变量**：通过可配置的分块大小来优化网络传输，这是一种灵活且高效的性能调优手段，允许用户根据网络带宽和硬件特性进行调整。
*   **ZMQ多部分消息中的 `receiver_engine_rank`**：这是一种在分布式系统中实现精确消息路由的常见模式，确保了消息能够被目标组件正确处理，是解耦架构中通信的关键。

### 5. 基于项目背景，这些提交如何影响项目发展

根据README，`LightX2V` 的目标是成为一个**轻量级的视频生成推理框架**。本次提交的更新直接推动了这一目标的实现：

1.  **“轻量级”的体现**：通过解耦（disagg）架构，将庞大的视频生成模型拆分为独立的编码器、变换器等组件，每个组件可以独立部署和扩展。这使得系统可以根据实际需求灵活分配资源，避免了“一刀切”式的资源浪费，体现了“轻量级”和“高效”的理念。
2.  **“推理框架”的完善**：一个成熟的推理框架不仅需要能跑通模型，更需要具备处理真实世界复杂场景的能力。本次更新通过引入动态负载、增强网络健壮性、优化数据传输，极大地丰富了框架作为“推理服务”的功能，使其从一个研究原型向一个可部署、可运维的框架迈进了一大步。
3.  **为未来扩展铺路**：清晰的配置文件和模块化的通信协议，为未来支持更多类型的视频生成模型（如不同的扩散模型、变换器架构）提供了良好的架构基础。开发者可以轻松地为新模型添加配置，并利用现有的分布式通信机制。

**总结**：昨日的更新是 `LightX2V` 项目发展中的一个**里程碑式**的提交。它标志着项目从单机原型阶段正式进入**分布式、可配置、高可靠**的工程化阶段，极大地提升了项目的成熟度和应用潜力，使其向成为一个真正可用的轻量级视频生成推理框架迈出了坚实的一步。

## 详细提交记录

### [3566cd5](https://github.com/ModelTC/LightX2V/commit/3566cd5e1626965490debf91d36ea5cc11d71c46)

- **作者**: zhtshr
- **时间**: 2026-04-24T08:57:28Z
- **提交信息**: Add scheduling mechanism and new workload (#1025)

This pull request introduces several new configuration files and
significant updates to the disaggregated (disagg) connection logic and
workload orchestration for the LightX2V project. The main focus is on
supporting distributed inference with improved network handling, chunked
data transfer, and dynamic workload simulation. The changes enhance
reliability, configurability, and usability for running and testing
disaggregated video inference pipelines.

**Key changes:**

### New configuration and workload simulation

* Added four new configuration files for disaggregated controller,
encoder, transformer, and decoder modes, each specifying model
parameters, quantization settings, RDMA protocol details, and
distributed ranks.
[[1]](diffhunk://#diff-440d18d9304ad8fbc166e4de7ec8269aa7219d6a6e5a88462cf0a716634bb1a5R1-R58)
[[2]](diffhunk://#diff-d572d987f2b9dbc6221429d35d2ca572a229e075ad8ae71157ff4775216b6a7cR1-R58)
[[3]](diffhunk://#diff-6fc0f74620b78b925329ce7d5642aa6c36646cd38186d876151ae3d6f6f6658bR1-R58)
[[4]](diffhunk://#diff-a7a24a5c453ee5f04be754b15e016adb89aba716ab856b91a1489ebc303c1b0fR1-R58)
* Introduced a workload staging configuration
(`wan22_i2v_workload_stages.json`) to define warmup and change phases
for dynamic load testing.
* Added `run_user.py` example script to simulate dynamic user workloads,
sending requests to the controller based on stage specifications and
supporting configurable request rates.

### Disagg connection reliability and protocol improvements

* Implemented `_normalize_loopback_host` to ensure consistent use of
IPv4 loopback addresses, controlled by the `DISAGG_FORCE_IPV4_LOOPBACK`
environment variable, improving local and mixed-protocol deployments.
[[1]](diffhunk://#diff-a5e5778ac7adc9b8f2c175153e932db47158abebba325b47298001bc80e89ba7R85-R92)
[[2]](diffhunk://#diff-a5e5778ac7adc9b8f2c175153e932db47158abebba325b47298001bc80e89ba7L544-R583)
* Enhanced error handling in the transfer loop and status
synchronization, logging exceptions and preventing crashes during data
transfer and status updates.
* Added support for chunked data transfer in `send_data`, controlled by
the `MOONCAKE_TRANSFER_CHUNK_BYTES` environment variable, to handle
large tensors more efficiently and robustly.

### Protocol and metadata updates

* Updated ZMQ communication to include `receiver_engine_rank` in
multipart messages for both encoder and transformer threads, ensuring
correct routing and status updates in distributed settings.
[[1]](diffhunk://#diff-a5e5778ac7adc9b8f2c175153e932db47158abebba325b47298001bc80e89ba7R364-R383)
[[2]](diffhunk://#diff-a5e5778ac7adc9b8f2c175153e932db47158abebba325b47298001bc80e89ba7R392-R393)
[[3]](diffhunk://#diff-a5e5778ac7adc9b8f2c175153e932db47158abebba325b47298001bc80e89ba7R439-R458)
[[4]](diffhunk://#diff-a5e5778ac7adc9b8f2c175153e932db47158abebba325b47298001bc80e89ba7R467-R468)
[[5]](diffhunk://#diff-a5e5778ac7adc9b8f2c175153e932db47158abebba325b47298001bc80e89ba7R600)
* Improved local IP detection logic in `mooncake.py` to better select a
non-loopback IPv4 address for outbound connections, enhancing
compatibility in multi-host environments.

### New libs
* locust


These changes collectively improve the flexibility, reliability, and
scalability of the disaggregated inference pipeline, making it easier to
configure, test, and deploy in distributed environments.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2040
- **最后更新**: 2026-04-25T05:51:15Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 昨日更新要点分析

1.  **主要更新类型**
    *   **功能新增**: 新增了多GPU推理支持。
    *   **Bug修复**: 修复了导入相关的错误。
    *   **文档更新**: 更新了README文件。

2.  **关键变更点及其与项目整体方向的关系**
    *   **关键变更点**:
        *   **多GPU推理支持**: 为`LongCatVideo`功能添加了多GPU推理能力。
        *   **导入Bug修复**: 修复了代码中的导入错误。
        *   **README更新**: 更新了项目的说明文档。
    *   **与项目方向的关系**:
        *   **多GPU推理**直接服务于项目“快速开始”和“推理”的核心目标。`LongCatVideo`（长猫视频？可能指长视频生成）是一个高级功能，多GPU支持意味着用户可以使用更多计算资源来生成更复杂、更长的视频，这显著提升了项目的实用性和可扩展性。
        *   **Bug修复**是项目稳定性和可用性的基础保障，确保用户能顺利运行代码。
        *   **README更新**是项目维护的常规工作，有助于新用户快速上手，符合项目“欢迎”和“快速开始”的定位。

3.  **对项目的影响和潜在意义**
    *   **对项目的影响**:
        *   **性能与能力提升**: 多GPU支持是性能优化的重要一步，使得`LongCatVideo`这类资源密集型任务变得可行，直接提升了项目的处理上限。
        *   **稳定性增强**: 修复导入Bug减少了用户遇到的障碍，提升了用户体验。
    *   **潜在意义**:
        *   **吸引专业用户**: 多GPU支持是面向专业用户和需要处理大规模视频生成任务用户的关键特性，有助于项目从实验性工具向生产级应用迈进。
        *   **为未来扩展铺路**: 多GPU架构的引入为未来支持更大模型、更高分辨率或更复杂视频生成任务奠定了基础。

4.  **值得关注的技术点**
    *   **多GPU推理的实现**: 这是本次更新的核心技术点。需要关注其实现方式（例如，是数据并行、模型并行还是流水线并行），以及它如何与`LongCatVideo`的特定逻辑结合。这关系到代码的架构设计和性能表现。
    *   **导入Bug的根因**: 了解修复的导入错误类型（例如，循环导入、路径错误、模块缺失），可以反映项目代码组织或依赖管理方面可能存在的问题。

5.  **基于README了解的项目背景，这些提交如何影响项目发展**
    *   **项目定位**: VideoX-Fun旨在提供易于使用、功能强大的视频生成工具，并提供了Hugging Face Spaces的在线体验。
    *   **影响与发展**:
        *   **从“可用”到“好用”**: 修复Bug和更新文档是让项目“可用”的基础。而多GPU支持则是让项目“好用”和“强大”的关键一步，它直接回应了用户对处理复杂、长视频任务的需求。
        *   **增强竞争力**: 在视频生成领域，性能是关键。多GPU支持使得VideoX-Fun在处理大规模任务时更具竞争力，能够与更专业的解决方案看齐。
        *   **社区发展**: 多GPU支持是一个重要的里程碑，可能会吸引更多有计算资源的开发者和研究者参与贡献，推动项目生态的繁荣。同时，稳定的代码和清晰的文档有助于降低社区贡献的门槛。

## 详细提交记录

### [199a43b](https://github.com/aigc-apps/VideoX-Fun/commit/199a43b544d5db4109bc1de4dd9bd029b6d25cff)

- **作者**: Bubbliiiing
- **时间**: 2026-04-24T07:54:22Z
- **提交信息**: Update READMEs, add LongCatVideo multi-GPU inference, and fix import bugs (#485)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5498
- **最后更新**: 2026-04-25T07:56:34Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Observer007, Christian Heimes, nv-yunzheq

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bug Fixes):** 共4项，是本次更新的主要部分。
- **功能新增 (New Features):** 共1项。
- **性能优化 (Performance):** 共1项。
- **构建/CI修复 (Build/CI Fix):** 共1项。

### 2. 关键变更点及其与项目整体方向的关系

FlashInfer 的目标是提供**高性能的 GPU 推理内核**。本次更新紧密围绕这一目标，在提升稳定性、扩展功能和支持新硬件方面取得了进展。

- **修复关键Bug，提升稳定性与兼容性:**
    - **`[fix] fix blackwell gdn accuracy issue (#3156)`**: 修复了Blackwell架构上GDN（门控差分网络）内核的精度问题。这是一个深藏的Bug，修复后大幅提升了数值精度（MAE从`2.82e-03`降至`3.05e-05`）。这直接关系到项目对**最新NVIDIA Blackwell架构**的支持质量。
    - **`fix: fix OOB issue for vLLM (#2762)`**: 修复了vLLM集成中的越界（OOB）内存访问问题。这增强了与**主流推理框架vLLM**的兼容性，对项目的生态整合至关重要。
    - **`fix: guard MXFP8 fc1 weight shape check for non-gated activations (#3082)`**: 修复了在使用MXFP8量化且非门控激活函数时，CUTLASS融合MoE后端的权重形状校验错误。这完善了**量化推理**和**MoE（混合专家模型）** 场景的支持，扩大了项目适用面。
    - **`fix (CICD): ensure data/ symlinks exist before jit-cache AOT compilation (#3158)`**: 修复了JIT缓存构建流程中的一个CI/CD问题，确保在AOT编译前正确创建符号链接。这提升了**项目的构建可靠性和开发者体验**。

- **新增功能，扩展应用场景:**
    - **`feat: Add row_starts and dsa_graph_safe to topk (#3133)`**: 为Top-K操作新增了`row_starts`和`dsa_graph_safe`参数。这是为了支持**SGLang的DSA（动态稀疏注意力）集成**，表明项目正在积极与**新兴推理框架（如SGLang）** 进行深度整合，以支持更复杂的推理模式。

- **性能优化，追求极致效率:**
    - **`perf: Add no-bias path for tinygemm_bf16 (#3151)`**: 为`tinygemm_bf16`内核添加了无偏置（no-bias）路径。当用户不提供偏置时，可以避免不必要的零偏置分配和计算，从而**减少开销，提升性能**。这体现了项目对**微调性能**的持续追求。

### 3. 对项目的影响和潜在意义

- **提升核心稳定性和可靠性:** 多个Bug修复，特别是Blackwell精度问题和vLLM的OOB问题，直接提升了FlashInfer在关键场景下的稳定性和可靠性，增强了用户信心。
- **巩固生态地位:** 修复与vLLM的兼容性问题，并主动适配SGLang，表明项目正积极融入主流推理生态，这对于一个底层库的成功至关重要。
- **拓展硬件支持:** 修复Blackwell架构的Bug，表明项目紧跟NVIDIA最新硬件发展，确保了在下一代GPU上的领先性能。
- **完善高级特性:** 修复MXFP8 MoE的Bug和新增Top-K功能，完善了量化推理和MoE等高级特性的支持，使其更易于被生产环境采用。

### 4. 值得关注的技术点

- **Blackwell GDN精度Bug:** 该Bug的根因是使用了错误的`max_coord`，修复后精度从`ulp: 9040`降至`ulp: 74`，这是一个巨大的提升。这提醒我们，在复杂的GPU内核中，即使是看似微小的逻辑错误也可能导致严重的精度问题。
- **CUTLASS MoE MXFP8校验:** 该Bug揭示了在快速迭代中，为特定场景（门控激活）编写的代码在扩展到通用场景（非门控激活）时可能失效。修复方式（引入`fc1_n_mult`变量）体现了良好的代码设计原则。
- **`dsa_graph_safe`:** 这个参数通过禁用某些优化（如clusters fast-path）来确保在DSA图执行环境下的安全性。这是一种在**性能**和**执行安全性**之间做权衡的典型设计模式。
- **`no-bias`路径:** 这是一个典型的性能优化技巧，通过避免不必要的内存分配和计算来提升效率。对于高频调用的内核，这种微小的优化可以累积成显著的性能提升。

### 5. 基于项目背景，这些提交如何影响项目发展

结合README中“**High-Performance GPU Kernels for Inference**”的定位，这些提交清晰地展示了项目的发展方向：

1.  **巩固“高性能”核心:** 通过修复精度Bug和添加`no-bias`路径，项目在**正确性**和**效率**两个维度上持续打磨，确保其作为高性能内核库的基石稳固。
2.  **拥抱“推理”生态:** 修复vLLM Bug和适配SGLang，表明项目不再仅仅是一个孤立的库，而是积极融入**vLLM、SGLang**等主流推理框架的生态

## 详细提交记录

### [8eedd64](https://github.com/flashinfer-ai/flashinfer/commit/8eedd6468be47992b3b7392d0111aac7862b0bf7)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-04-24T21:21:49Z
- **提交信息**: fix (CICD): ensure data/ symlinks exist before jit-cache AOT compilation (#3158)

<!-- .github/pull_request_template.md -->

## 📌 Description

The jit-cache wheel build (`scripts/build_flashinfer_jit_cache_whl.sh`)
runs `python -m build --wheel` without first installing the main
flashinfer package. The AOT compilation imports flashinfer directly from
the source tree, but the `flashinfer/data/` symlinks are never created
because the main `build_backend._create_data_dir()` is never called.
This wasn't a problem before the CCCL submodule because CUTLASS/spdlog
headers are self-contained — there's no CTK-bundled copy to shadow them.
CCCL is different: the CTK also ships CCCL headers at
`$cuda_home/include/`, so when the vendored `data/cccl` symlink is
missing, `#include <cuda/cmath>` silently falls through to the CTK copy,
which on older toolkits doesn't have `cuda::fast_mod_div`.

Call the main build_backend._create_data_dir() before importing
flashinfer.aot to ensure all symlinks are in place.

Made-with: Cursor

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/3159

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
* Ensure the JIT cache build now initializes required filesystem layout
and data directories before compilation so builds succeed even when the
package hasn't been previously installed.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ef3e37b](https://github.com/flashinfer-ai/flashinfer/commit/ef3e37b4c2eb7953835e74945b8bcdeaba7ecd37)

- **作者**: Christian Heimes
- **时间**: 2026-04-24T19:06:33Z
- **提交信息**: Build mnnvl_moe_alltoall with logger and stringUtils (#2807)

## 📌 Description

The `mnnvl_moe_alltoall` module uses `Logger::getLogger` and `fmtstr`
symbols. Add dependencies to `logger.cpp` and `stringUtils.cpp` to
include the symbols in the shared library.

## 🔍 Related Issues

#2804

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ x I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

I have not tested the build locally, yet.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated internal compilation configuration to include additional
utility source files in the MOE alltoall module build.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Christian Heimes <cheimes@redhat.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

### [364081c](https://github.com/flashinfer-ai/flashinfer/commit/364081cdbe414d31c2d6ba32daec661fee0580b9)

- **作者**: nv-yunzheq
- **时间**: 2026-04-24T16:15:35Z
- **提交信息**: fix: fix OOB issue for vLLM (#2762)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix https://github.com/vllm-project/vllm/issues/35706, by adding back
boundary check

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
* Improved bounds checking in the MOE (Mixture of Experts) backend
kernel to prevent out-of-bounds memory access during routing operations,
enhancing system stability and reliability.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [3516d2b](https://github.com/flashinfer-ai/flashinfer/commit/3516d2bca61f297579c7fb18019c0939c195c578)

- **作者**: Observer007
- **时间**: 2026-04-24T14:19:18Z
- **提交信息**: [fix] fix blackwell gdn accuracy issue (#3156)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixed the accuracy issue in blackwell gdn kernel found by @bestzsq. 

The root cause is that the legacy `max_coord` is not the actual last
coord of the `sCumprod`. We change to the last coord instead. It's a
deeply hidden bug that we hadn't discovered previously. Thanks to
@bestzsq.


Reproducer test link from @bestzsq:
https://github.com/flashinfer-ai/flashinfer/pull/3001#discussion_r3130754402

Reproducer test output before this pr:
```
# flash-linear-attention==0.4.2
fla vs cute64: mae: 2.82288e-03, ulp: 9040.0
fla vs cute128: mae: 3.05176e-05, ulp: 74.0
# flash-linear-attention==0.5.0
fla vs cute64: mae: 2.82288e-03, ulp: 9064.0
fla vs cute128: mae: 3.05176e-05, ulp: 74.0
```

Reproducer test output after this pr:
```
# flash-linear-attention==0.4.2
fla vs cute64: mae: 3.05176e-05, ulp: 74.0
fla vs cute128: mae: 3.05176e-05, ulp: 74.0
# flash-linear-attention==0.5.0
fla vs cute64: mae: 3.05176e-05, ulp: 74.0
fla vs cute128: mae: 3.05176e-05, ulp: 74.0
```

Previous local test tolerance loosen from `1e-3` to `2e-3` in #3001 :
https://github.com/flashinfer-ai/flashinfer/pull/3001/changes#diff-d3d322c588f461c03200b8a16ce676dbcab99e11a6b225d230ea0d51c9e8dbf6L132

This pr tightenes the tolerance from `2e-3` to `1e-3`:
https://github.com/flashinfer-ai/flashinfer/pull/3156/changes#diff-d3d322c588f461c03200b8a16ce676dbcab99e11a6b225d230ea0d51c9e8dbf6R148

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

## Release Notes

* **Refactor**
* Improved kernel computation efficiency by consolidating internal
calculation steps and removing redundant intermediate operations,
reducing code complexity while preserving all existing functionality and
performance characteristics.

* **Tests**
* Strengthened numerical validation by reducing tolerance thresholds in
computational accuracy tests for greater precision, ensuring more
stringent verification of output correctness and numerical consistency
across test scenarios.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0798a7d](https://github.com/flashinfer-ai/flashinfer/commit/0798a7d1460907e8a591e0caefdcafa7b2a9e0f7)

- **作者**: Yiyang "Ian" Liu
- **时间**: 2026-04-24T11:44:20Z
- **提交信息**: fix: guard MXFP8 fc1 weight shape check for non-gated activations (#3082)

Fixes #2731.

## What's broken?

When using the CUTLASS fused MoE backend with **non-gated activations**
(e.g., Relu2, Gelu, Silu) and MXFP8 quantization, the fc1 weight shape
validation unconditionally rejects the input — even when the shape is
correct.

## Who is affected?

Anyone using the **CUTLASS fused MoE** path with:
- **Quantization**: `WMxfp8AMxfp8`, `WMxfp4AFp8`, or `WMxfp4AMxfp8`
- **Activation**: any non-gated type (Relu2, Gelu, Silu, etc.)

Not affected: gated activations (Swiglu, Geglu, SwigluBias), or other
quant modes (NVFP4 already handles this correctly).

## Where is the bug?


`csrc/fused_moe/cutlass_backend/flashinfer_cutlass_fused_moe_binding.cu`,
inside `getQuantParams()` — the fc1 weight block N-dimension check
hardcodes `* 2` at three MXFP8 branches (~L898, ~L1004, ~L1063).

## Why does it happen?

PR #2581 introduced MXFP8 support when only gated activations (Swiglu)
existed, so `inter_size * 2` was correct. Later, non-gated activation
support was added to the trtllm-gen backend (PR #2707), but the CUTLASS
backend's validation was never updated. The NVFP4 path in the same file
(line ~1131) already handles this correctly with an `if
(isGatedActivation(...))` guard.

## How did we fix it?

For each of the 3 MXFP8 quant branches:
1. Extract `int const fc1_n_mult =
isGatedActivation(base_activation_type) ? 2 : 1;`
2. Replace the hardcoded `* 2` with `* fc1_n_mult`
3. Update error messages: gated shows `"inter_size * 2"`, non-gated
shows `"inter_size"`

**Before:**
```cpp
fc1_weight_block.size(1) == alignToSfDim(inter_size, ...) * 2
```

**After:**
```cpp
int const fc1_n_mult = isGatedActivation(base_activation_type) ? 2 : 1;
fc1_weight_block.size(1) == alignToSfDim(inter_size, ...) * fc1_n_mult
```

## How do we know it works?

- `pre-commit run` passes (clang-format, lint, etc.)
- Gated activations (default Swiglu): `fc1_n_mult = 2` — identical to
old behavior, no regression
- Non-gated activations: `fc1_n_mult = 1` — shape check now accepts
correct `inter_size` dimension
- Full GPU test suite requires CI (`@flashinfer-bot run`)

## Related

- Builds on the approach identified in #2753 (stale ~27 days, CI
unresolved).
- Addresses the Gemini review feedback from #2753 by extracting the
multiplier to a local variable before the validation checks.

cc @aleozlx @nv-yunzheq


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed weight block size validation for Mixture of Experts (MOE) to
correctly handle both gated and non-gated activation types, ensuring
proper support across different activation configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Yiyang Liu <37043548+ianliuy@users.noreply.github.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [ef46793](https://github.com/flashinfer-ai/flashinfer/commit/ef46793b618751839633990e5d0f119877872c7b)

- **作者**: Ziang Li
- **时间**: 2026-04-24T10:32:00Z
- **提交信息**: feat: Add `row_starts` and `dsa_graph_safe` to topk (#3133)

<!-- .github/pull_request_template.md -->

## 📌 Description
@humansand
Parent PR: https://github.com/flashinfer-ai/flashinfer/pull/3095
SGLang PR: https://github.com/sgl-project/sglang/pull/22851

Add `row_starts` and `dsa_graph_safe` for SGLang DSA integration.
<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues
https://github.com/sgl-project/sglang/pull/22851#issuecomment-4286264825

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
* Added dsa_graph_safe flag to top-k APIs to opt into DSA-graph safe
execution.
* Added optional row_starts parameter to page-table and ragged top-k
transforms to support per-row score offsets.

* **Behavior**
* When dsa_graph_safe=True the optimized clusters fast-path is disabled
to ensure safe execution.

* **Tests**
* Added tests covering row_starts behavior for page-table and ragged
transforms.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [cc682da](https://github.com/flashinfer-ai/flashinfer/commit/cc682da57a11534a957f5a40b67533435e724b6c)

- **作者**: Brian K. Ryu
- **时间**: 2026-04-24T08:53:23Z
- **提交信息**: perf: Add no-bias path for tinygemm_bf16 (#3151)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

This PR updates tinygemm_bf16 to use a dedicated no-bias kernel path
when `bias=None`, **avoiding the previous zero-bias materialization in
the Python wrapper**. It also adds shared benchmark-harness support and
benchmark smoke coverage for `tinygemm_bf16`, while keeping the branch
scoped to BF16-only changes.

If you want, I can also turn that into a full PR body with Summary and
Test plan sections.

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
* Added a BF16 GEMM routine with benchmarking and optional correctness
validation.
  * Added a no-bias GEMM variant to run without requiring a bias tensor.

* **Performance**
* Reduced overhead when bias is absent by avoiding unnecessary bias
allocation.

* **Compatibility**
* BF16 routine is available only on supported GPU
backends/architectures.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3422
- **最后更新**: 2026-04-25T07:40:06Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Junda Su, William Lin

## AI分析总结

好的，这是对 `hao-ai-lab/FastVideo` 仓库昨日提交记录的分析总结。

### 昨日更新要点总结

1.  **主要更新类型**
    *   **Bug修复**: 修复了图像到视频（I2V）VAE编码中的一个问题。
    *   **功能新增**: 为LTX-2模型添加了类型化的连续状态和流式会话存储功能。

2.  **关键变更点及其与项目方向的关系**
    *   **Bug修复 (I2V VAE编码)**: 修复了在图像到视频生成流程中，对`uint8`格式的PIL图像进行VAE编码时可能出现的错误。这直接关系到**图像到视频生成**这一核心功能的稳定性和正确性。
    *   **功能新增 (LTX-2流式支持)**: 为LTX-2模型引入了“类型化的连续状态”和“流式会话存储”。这表明项目正在为LTX-2模型构建更高级、更稳定的**流式推理**或**长视频生成**能力，使其能够处理更长的视频序列，并可能在生成过程中保持状态。

3.  **对项目的影响和潜在意义**
    *   **提升I2V功能的可靠性**: 修复I2V VAE编码的bug，能直接提升用户在使用图像生成视频功能时的体验，减少因数据格式问题导致的失败。
    *   **强化LTX-2模型能力**: 新增的流式会话存储功能是LTX-2模型走向实用化的关键一步。它使得模型能够支持**无限长视频生成**或**交互式视频编辑**等高级应用场景，显著扩展了FastVideo在长视频生成领域的竞争力。

4.  **值得关注的技术点**
    *   **`uint8` PIL图像处理**: 修复点在于处理PIL图像时，需要确保其数据类型（`uint8`）在送入VAE编码器前被正确处理或归一化。这是一个常见的图像预处理细节，但容易出错。
    *   **类型化连续状态**: 为流式处理引入类型化状态，意味着项目采用了更严谨的工程实践来管理模型在长序列生成中的内部状态，这有助于提高代码的健壮性和可维护性。
    *   **流式会话存储**: 这暗示了FastVideo可能正在构建一个会话管理系统，用于保存和恢复生成过程中的中间状态，这对于支持暂停、恢复或回溯生成过程至关重要。

5.  **对项目发展的影响**
    *   结合README中提到的“快速开始”和“文档”链接，以及项目专注于视频生成的目标，这些提交表明FastVideo正在从“能跑通”向“跑得稳、跑得长”的方向发展。
    *   修复I2V bug巩固了其**图像到视频**这一基础功能。
    *   为LTX-2添加流式支持，则是在**长视频生成**这一前沿领域进行技术布局，旨在解决现有视频生成模型普遍存在的时长限制问题。这符合项目“FastVideo”的名称，旨在提供更快、更长的视频生成能力。

## 详细提交记录

### [e17cd26](https://github.com/hao-ai-lab/FastVideo/commit/e17cd2633c7ec805f19431734034d3c932fa22ed)

- **作者**: Junda Su
- **时间**: 2026-04-24T09:16:01Z
- **提交信息**: [bugfix]: normalize uint8 pil_image in I2V VAE encoding (#1249)

Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e0dc5f2](https://github.com/hao-ai-lab/FastVideo/commit/e0dc5f2b0cf56fb0c0859817ef780569a676e7e9)

- **作者**: William Lin
- **时间**: 2026-04-24T08:28:07Z
- **提交信息**: [feat] Add typed LTX-2 continuation state and streaming session store (#1250)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33442
- **最后更新**: 2026-04-25T11:46:39Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, Remy

## AI分析总结

好的，作为一名专业的代码分析助手，我将结合 `huggingface/diffusers` 项目的背景，为您分析昨日提交记录。

### 昨日更新要点总结

**1. 主要更新类型**

*   **Bug修复**：修复了特定注意力后端（Flash Attention）在环形并行（Ring CP）下的问题。
*   **CI/CD优化**：简化了发布工作流和文档构建工作流。
*   **重构/清理**：对CI脚本和依赖版本进行了小幅调整。

**2. 关键变更点及其与项目整体方向的关系**

*   **`[f7fd76a]` 修复Flash Attention的环形并行（Ring CP）**：
    *   **变更点**：修复了在 `flash` 和 `flash_3` 注意力后端下，环形上下文并行（Ring Context Parallelism）无法正常工作的问题。提交者添加了相关的测试用例来确保修复的有效性。
    *   **与项目方向的关系**：`diffusers` 项目致力于提供最先进、高性能的扩散模型推理和训练能力。注意力机制是扩散模型（尤其是DiT类模型）的核心。支持多种注意力后端（如Flash Attention）和并行策略（如Ring CP）是提升模型训练和推理效率、支持更大模型和更长序列的关键。此修复直接保障了这些高级功能的稳定性和可靠性。

*   **`[dad80d7]` 简化发布工作流**：
    *   **变更点**：简化了CI/CD中的发布流程，移除了不必要的步骤（如确定最新分支），并调整了权限和触发条件。
    *   **与项目方向的关系**：作为一个被广泛使用的开源库，稳定、高效的发布流程至关重要。简化工作流可以减少人为错误，加快发布速度，使新功能、修复和改进能更快地到达用户手中，体现了项目对工程化质量和开发者体验的持续关注。

*   **`[d0c9cba]` 更新文档构建依赖**：
    *   **变更点**：将主文档构建工作流中的 `doc-builder` 依赖版本（SHA）进行了升级。
    *   **与项目方向的关系**：文档是项目成功的关键。保持文档构建工具链的最新状态，可以确保文档生成过程的稳定性，并可能获得新功能（如更好的格式支持、性能提升等），从而提升用户阅读和学习体验。

**3. 对项目的影响和潜在意义**

*   **直接影响**：
    *   **用户**：使用Flash Attention进行训练或推理的用户，在启用环形并行时不会再遇到相关错误。
    *   **开发者/维护者**：发布流程更简洁、更可靠，减少了维护负担和发布风险。
    *   **文档**：文档构建过程更健壮。
*   **潜在意义**：
    *   **性能与可扩展性**：修复Ring CP问题，为未来支持更大规模、更长序列的扩散模型（如视频生成、高分辨率图像生成）铺平了道路。
    *   **项目成熟度**：持续优化CI/CD和文档基础设施，是项目走向成熟和稳定的标志。

**4. 值得关注的技术点**

*   **注意力后端的模块化设计**：`diffusers` 将注意力计算抽象为不同的后端（`flash`, `flash_3`, `sdpa`, `xformers` 等），这种设计允许用户根据硬件和需求灵活选择，也方便集成社区最新的优化。此提交修复了特定后端与并行策略的兼容性问题，体现了这种模块化设计的复杂性。
*   **环形上下文并行（Ring CP）**：这是一种在多个设备间高效切分和计算长序列注意力机制的技术，对于处理高分辨率图像或长视频等需要巨大上下文窗口的任务至关重要。
*   **CI/CD最佳实践**：简化发布工作流（如移除不必要的步骤、使用SHA而非分支名）是提升CI/CD可靠性和安全性的常见做法。

**5. 基于README背景，这些提交如何影响项目发展**

*   **README核心目标**：`diffusers` 的目标是成为最先进、最易用的扩散模型库，支持从研究到生产的全流程。
*   **影响分析**：
    *   **技术先进性**：通过修复Flash Attention的Ring CP问题，`diffusers` 保持了其在性能优化方面的领先地位，确保用户能利用最新的硬件特性（如NVIDIA H100/B200上的Flash Attention-3）进行高效计算。这直接支持了其“最先进”的目标。
    *   **易用性与可靠性**：简化发布流程和更新文档构建，虽然不直接面向最终用户，但确保了项目能持续、稳定地交付高质量代码和文档，提升了整体的“易用性”和可靠性。
    *   **社区与生态**：这些提交体现了项目维护者对代码质量和工程效率的重视，有助于吸引更多开发者贡献代码，并让用户对项目的长期维护更有信心，从而巩固其作为扩散模型核心生态的地位。

**总结：** 昨日的更新是一次典型的“修修补补”与“基础设施优化”的结合。虽然看起来不引人注目，但修复了核心性能功能（Flash Attention + Ring CP）的Bug，并提升了项目的工程化水平，这对于一个成熟、高标准的开源项目来说是至关重要的日常维护工作。

## 详细提交记录

### [f7fd76a](https://github.com/huggingface/diffusers/commit/f7fd76adcd288494a1a13c82d06e37579170aaf3)

- **作者**: Sayak Paul
- **时间**: 2026-04-24T23:35:08Z
- **提交信息**: [attention backends] fix ring CP for flash and flash 3 (#13182)

* tests: add cp backend and attention backend tests.

* up

* up

* up

* fix ring for flash and flash_3

* generate.

* Apply suggestions from code review

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

* up

* up

---------

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

### [dad80d7](https://github.com/huggingface/diffusers/commit/dad80d728df16bac506b84b363561e536609bcd9)

- **作者**: Sayak Paul
- **时间**: 2026-04-24T22:56:20Z
- **提交信息**: [ci] simplify release workflow. (#13329)

* simplify release workflow.

* up

* trigger on branches too.

* restrict permissions to read.

* use sha

* remove determination step of latest branch

* resolve rest

### [d0c9cba](https://github.com/huggingface/diffusers/commit/d0c9cbad28d7d3bba28db94622e13500c4179075)

- **作者**: Remy
- **时间**: 2026-04-24T12:42:48Z
- **提交信息**: chore: bump doc-builder SHA for main doc build workflow (#13555)

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 398
- **最后更新**: 2026-04-25T04:39:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12306
- **最后更新**: 2026-04-25T08:32:29Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

好的，这是对仓库 `modelscope/DiffSynth-Studio` 昨日提交记录的分析总结。

### 昨日更新要点分析

1.  **主要更新类型**
    *   **Bug修复**：本次提交是一个明确的Bug修复。

2.  **关键变更点及其与项目整体方向的关系**
    *   **变更点**：修复了 `transformers` 库的版本兼容性问题（`#1412`）。
    *   **与项目方向的关系**：`DiffSynth-Studio` 作为一个依赖众多深度学习库（如 `transformers`）的视频/图像合成工具，其稳定性和易用性至关重要。修复版本兼容性问题，是为了确保项目能够顺利安装和运行，避免因上游库的更新而导致功能异常。这直接关系到项目的**可用性**和**用户基础**的维护。

3.  **对项目的影响和潜在意义**
    *   **直接影响**：解决了用户可能遇到的安装失败或运行时错误，提升了项目的稳定性。
    *   **潜在意义**：表明项目团队在积极维护，关注依赖库的生态变化，并及时响应社区反馈（`#1412` 通常指代一个Issue编号）。这有助于建立用户信任，鼓励更多人尝试和使用该项目。

4.  **值得关注的技术点**
    *   **版本锁定与兼容性**：虽然本次提交是修复，但背后反映了一个常见的技术挑战——如何管理复杂项目的依赖关系。一个健康的项目通常会通过 `requirements.txt` 或 `setup.py` 中的版本范围声明来平衡“使用新特性”和“保持稳定”之间的关系。这次修复可能涉及调整了某个依赖库的版本上限或下限。

5.  **基于README了解的项目背景，这些提交如何影响项目发展**
    *   **项目背景**：`DiffSynth-Studio` 是一个旨在提供视频/图像合成能力的开源工具，其README强调了通过PyPI安装的便捷性。
    *   **对项目发展的影响**：这次Bug修复虽然小，但非常关键。它直接保障了用户能够通过 `pip install DiffSynth` 这一核心入口顺利安装和使用项目。如果版本问题不解决，新用户可能第一步就卡住，严重影响项目的推广和社区增长。因此，这是一个**维护项目基础健康度**的提交，为后续的功能迭代和用户增长扫清了障碍。

## 详细提交记录

### [5b66f22](https://github.com/modelscope/DiffSynth-Studio/commit/5b66f223b629548f1497461745a9ebbb452d8a8f)

- **作者**: Zhongjie Duan
- **时间**: 2026-04-24T09:01:08Z
- **提交信息**: fix version issue of transformers (#1412)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 26415
- **最后更新**: 2026-04-25T11:52:11Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 15
- **主要提交者**: Kangrui Du, Siju Samuel, Shangming Cai

## AI分析总结

好的，这是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结。

### 1. 主要更新类型

-   **功能新增 (Features):** 支持 Hy3 预览、支持 LTX 2.3 的 LoRA、为扩散模型添加强化学习（RL）的逐步 rollout 选项、实验性的可中断分段 CUDA Graph。
-   **Bug 修复 (Bug Fixes):** AMD ROCm 版本门控修复、AMD 夜间版本标签选择修复、统一 LTX-2.3 HQ 代码路径门控。
-   **性能优化 (Performance):** 消除注意力机制的 DtoD 拷贝、为 Intel GPU 启用流水线并行（后因问题回滚）。
-   **文档更新 (Documentation):** 更新 DeepSeek V4 的 FP8 检查点 cookbook。
-   **重构/弃用 (Refactoring/Deprecation):** 弃用 `--collect-tokens-histogram` 参数，改为自动收集。
-   **基础设施 (Infrastructure):** 为 HiCache & HybridModel 添加 3FS 后端支持 DSA 和 Mamba 模型、修复 CI 测试。

### 2. 关键变更点及其与项目整体方向的关系

-   **硬件兼容性扩展 (AMD & Intel GPU):**
    -   **变更点:** 修复 AMD ROCm 版本兼容性问题，并尝试为 Intel XPU 启用流水线并行（虽然后续回滚）。
    -   **关系:** 直接对应项目README中提到的支持多种硬件后端（NVIDIA, AMD, Intel）的目标。这些提交表明项目正在积极扩展和稳定对非NVIDIA GPU的支持。

-   **模型支持深化 (DeepSeek, Diffusion, Mamba):**
    -   **变更点:** 更新 DeepSeek V4 的 FP8 检查点文档、支持 LTX 2.3 的 LoRA 微调、为 HiCache 和 HybridModel 添加 Mamba 模型支持。
    -   **关系:** 项目致力于支持最新的前沿模型（如 DeepSeek V4）和多样化的模型架构（如扩散模型、Mamba）。这些提交体现了项目紧跟AI领域发展，不断扩展其模型覆盖范围的承诺。

-   **性能优化与创新 (CUDA Graph, Attention):**
    -   **变更点:** 引入实验性的“可中断分段 CUDA Graph”和优化注意力机制以减少内存拷贝。
    -   **关系:** 项目核心目标是提供“最快的推理速度”。这些性能优化直接服务于这一目标，通过减少计算和内存开销来提升吞吐量和降低延迟。`Breakable Piecewise Cuda Graph` 是一个值得关注的创新点，旨在解决传统CUDA Graph的灵活性限制。

-   **功能迭代与易用性 (Metrics, RL):**
    -   **变更点:** 弃用旧的指标收集参数，改为自动收集；为扩散模型添加RL训练支持。
    -   **关系:** 这些更新提升了项目的易用性和功能完整性。自动收集指标简化了用户配置，而RL支持则扩展了项目在生成式AI训练领域的应用场景，符合其“服务、推理和训练”的定位。

### 3. 对项目的影响和潜在意义

-   **正面影响:**
    -   **扩大用户基础:** 对AMD和Intel GPU的持续支持将吸引更多非NVIDIA用户。
    -   **提升竞争力:** 性能优化（特别是CUDA Graph和Attention）将巩固其在推理速度上的领先地位。
    -   **增强吸引力:** 支持更多前沿模型（DeepSeek V4, Mamba, LTX 2.3 LoRA）和训练功能（RL）将使项目对研究者和开发者更具吸引力。
-   **潜在风险:**
    -   **稳定性问题:** 新功能（如Intel流水线并行）可能需要更多迭代才能稳定，回滚操作也说明了这一点。实验性功能（如Breakable Piecewise Cuda Graph）可能引入不确定性。
    -   **维护成本:** 支持更多硬件和模型架构会增加代码库的复杂性和维护成本。

### 4. 值得关注的技术点

-   **`Breakable Piecewise Cuda Graph` (实验性):** 这是一个非常有趣的技术方向。传统的CUDA Graph是静态的，一旦捕获就无法修改。这个“可中断分段”的概念可能允许在Graph执行过程中动态插入或修改操作，从而在保持高性能的同时获得更大的灵活性。这可能是解决动态形状或控制流问题的一种新思路。
-   **`eliminate attention DtoD copy`:** 通过传递预分配的输出给FlashAttention来避免一次设备到设备的拷贝。这是一个典型的“零开销”优化技巧，对于长序列和批量推理场景，这种微小的优化可以累积成显著的性能提升。
-   **`3FS backend support DSA & mamba model`:** 3FS（可能是一个分布式文件系统）后端支持，结合HiCache和HybridModel，表明项目正在探索更高级的模型部署和缓存策略，可能用于处理超大模型或实现高效的模型混合推理。

### 5. 基于项目背景，这些提交如何影响项目发展

-   **巩固“最快推理”的定位:** 性能优化（#21985, #22218）是直接服务于项目核心目标的，确保其在技术上的领先性。
-   **践行“多硬件、多模型”的愿景:** 对AMD、Intel GPU的支持以及对DeepSeek V4、Mamba、LTX 2.3等模型的跟进，展示了项目正在努力成为一个真正通用的、不受限于特定硬件或模型类型的推理引擎。


## 详细提交记录

### [76da28f](https://github.com/sgl-project/sglang/commit/76da28f6d61650747f39af4c28e68f7b5e2c27f5)

- **作者**: Xinyi Song
- **时间**: 2026-04-24T20:26:16Z
- **提交信息**: [AMD][bugfix] add gate rocm >= 7.2 for bpreshuffle (#23671)

### [f7e8406](https://github.com/sgl-project/sglang/commit/f7e840682cdded8d38d942cb6862f77120f8a28b)

- **作者**: jhchouuu
- **时间**: 2026-04-24T20:12:20Z
- **提交信息**: [AMD][MoRI] bump MoRI to v1.1.1 (#23642)

### [587fd15](https://github.com/sgl-project/sglang/commit/587fd15bd272d03f78dcc58a3e771a88d0c40f64)

- **作者**: Jia Guo
- **时间**: 2026-04-24T19:05:16Z
- **提交信息**: perf: eliminate attention DtoD copy by passing pre-allocated output to FA (#21985)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [6d03861](https://github.com/sgl-project/sglang/commit/6d038614760f0a24d86ca0264d9dbe7dc42281a5)

- **作者**: Xinyuan Tong
- **时间**: 2026-04-24T19:03:24Z
- **提交信息**: support Hy3 preview (#23533)

Co-authored-by: pengmeng <pengmeng@tencent.com>
Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>
Co-authored-by: chengvjiang <chengvjiang@tencent.com>
Co-authored-by: russellfeng <russellfeng@tencent.com>

### [6344b54](https://github.com/sgl-project/sglang/commit/6344b546c844fc4630fde99a9b15b1d5832a1ee2)

- **作者**: Lianmin Zheng
- **时间**: 2026-04-24T19:00:16Z
- **提交信息**: Deprecate --collect-tokens-histogram, auto-collect with --enable-metrics (#23595)

### [0569652](https://github.com/sgl-project/sglang/commit/05696527eadff3dbdb78646120e70d1f22402230)

- **作者**: Mick
- **时间**: 2026-04-24T17:52:41Z
- **提交信息**: [diffusion] feat: support LoRA for LTX2.3 (#23649)

### [baa0aa6](https://github.com/sgl-project/sglang/commit/baa0aa670f856beff07a7857e3740688baab243d)

- **作者**: Kang Yifei
- **时间**: 2026-04-24T16:48:01Z
- **提交信息**: [HiCache & HybridModel] 3FS backend support DSA & mamba model (#23241)


Co-authored-by: 墨已 <kangyifei.kyf@alibaba-inc.com>
Co-authored-by: hzh0425 <hzh0425@apache.org>

### [92d262f](https://github.com/sgl-project/sglang/commit/92d262f710241e16983d6745a639d9e37f66a04b)

- **作者**: Kangrui Du
- **时间**: 2026-04-24T15:26:16Z
- **提交信息**: [diffusion] RL: add per-step rollout options for SDE and trajectory capture (#23151)

### [bca3dd9](https://github.com/sgl-project/sglang/commit/bca3dd958ab8585ca9523bdc8ae1ebbce3079ca6)

- **作者**: Siju Samuel
- **时间**: 2026-04-24T11:52:44Z
- **提交信息**: [Intel GPU] Enable pipeline parallelism on XPU (#23645)

### [60bbb80](https://github.com/sgl-project/sglang/commit/60bbb800db812e1a8a9069abad4b2e391b894578)

- **作者**: Yuwei An
- **时间**: 2026-04-24T11:33:05Z
- **提交信息**: [Experimental] Breakable Piecewise Cuda Graph (#22218)

Signed-off-by: Oasis-Git <ayw.sirius19@gmail.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [b3b0336](https://github.com/sgl-project/sglang/commit/b3b03369a5f2bae3351e26fe08a514c7b097121b)

- **作者**: Mick
- **时间**: 2026-04-24T09:44:08Z
- **提交信息**: [diffusion] fix: unify LTX-2.3 HQ codepath gates for all LTX-2.3 variants (#23624)

### [b060a5c](https://github.com/sgl-project/sglang/commit/b060a5ccfd4a7cda1d01497c5f6d64cc78fa854e)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-04-24T09:39:47Z
- **提交信息**: [AMD] Fix nightly version tag selection (#23644)

Co-authored-by: bingxche <bingxche@amd.com>

### [b8d8833](https://github.com/sgl-project/sglang/commit/b8d883398da8a852f6e73fd4ebb9e27ac36e27a0)

- **作者**: Shangming Cai
- **时间**: 2026-04-24T09:36:35Z
- **提交信息**: Revert "[Intel GPU] Enable pipeline parallelism on XPU" (#23641)

### [1758856](https://github.com/sgl-project/sglang/commit/175885676288b249a6cd3f99d0714cd38fe1e3c3)

- **作者**: Ziang Li
- **时间**: 2026-04-24T09:02:11Z
- **提交信息**: [CI] Fix mxfp8 TrtllmGenMoe test (#23125)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [92bb5c6](https://github.com/sgl-project/sglang/commit/92bb5c6bbee94b05248b5b4d500489c8223b82ea)

- **作者**: fzyzcjy
- **时间**: 2026-04-24T07:58:04Z
- **提交信息**: Update pro fp8 checkpoint in DeepSeek V4 cookbook (#23634)

### [3a620cb](https://github.com/sgl-project/sglang/commit/3a620cb761ff6f2d7cda709cc7ed0940e090e2a0)

- **作者**: fzyzcjy
- **时间**: 2026-04-24T07:12:35Z
- **提交信息**: Again update DeepSeek V4 cookbook (#23622)

### [1a37e57](https://github.com/sgl-project/sglang/commit/1a37e57fb1ae9b937db566df0f42d6a87a83a2ac)

- **作者**: zijiexia
- **时间**: 2026-04-24T07:06:30Z
- **提交信息**: [codex] docs: note H200 DeepSeek-V4 checkpoint (#23628)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
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


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 78093
- **最后更新**: 2026-04-25T11:40:24Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 22
- **主要提交者**: Jiangyun Zhu, Wentao Ye, Itay Alroy

## AI分析总结

好的，作为专业的代码分析助手，以下是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bugfix):** 数量最多，共7项，涉及MoE路由、模型推理、CI测试、平台兼容性等多个方面。
- **重构 (Refactor):** 2项，包括清理死代码和统一注意力机制的内核。
- **功能新增 (Feature):** 2项，包括新的量化内核和前端功能。
- **构建/CI (Build/CI):** 3项，包括支持新Python版本、更新CUDA版本和新增端到端测试。
- **文档更新 (Docs):** 1项，新增了关于上下文扩展方法的文档。
- **性能优化 (Performance):** 1项，通过统一内核来优化注意力计算。
- **模型支持 (Model):** 1项，为Gemma4模型添加了新的视觉注意力机制。

### 2. 关键变更点及其与项目整体方向的关系

- **核心推理引擎优化与修复：**
    - **[Refactor] 统一2D/3D注意力内核 (914d046):** 将Triton实现的注意力内核统一，简化代码并可能提升性能。这与项目“快速 (fast)”的目标一致。
    - **[Bugfix] 修复MoE路由选择偏差 (333529d):** 修复了`fused_moe`路由器中的副本选择偏差，确保专家负载均衡更准确，直接影响模型推理质量和效率。
    - **[Bugfix] 修复MoE共享专家输出填充问题 (e8eb049):** 修复了MoE模型中共享专家添加前的输出对齐问题，这是对核心模型架构的精确性修复。
    - **[Bugfix] 修复DSA + MTP中的IMA问题 (7d3195e):** 修复了动态稀疏注意力与多Token预测结合时的潜在错误，体现了对前沿推理技术的持续打磨。

- **模型支持与兼容性扩展：**
    - **[Model] Gemma4双向视觉注意力 (512f522):** 为Gemma4模型添加了更复杂的视觉注意力机制，表明vLLM正在积极支持最新的多模态大模型，扩展其“为所有人 (for everyone)”的愿景。
    - **[Bugfix] 修复GLM-5.1在ROCm上的错误 (095d2f8):** 修复了特定模型在AMD ROCm平台上的运行错误，体现了对多硬件平台的支持承诺。
    - **[Bugfix] 修复Mistral工具解析器 (2ec18f5):** 修复了与HuggingFace分词器的兼容性问题，确保了对流行开源模型生态的兼容性。

- **基础设施与构建现代化：**
    - **[Build] 支持Python 3.14 (2179252):** 前瞻性地将Python 3.14加入支持列表，表明项目紧跟语言生态发展。
    - **[Build] 更新CUDA至13.0.2 (6dec49f):** 与PyTorch 2.11.0对齐，确保在最新的NVIDIA GPU软件栈上获得最佳性能和兼容性。
    - **[Frontend] 委托给vLLM Omni (5e11b40):** 当传递`--omni`参数时，将请求委托给vLLM Omni，这可能是为了整合或过渡到一个更统一、更强大的前端服务，简化用户操作。

- **量化与性能提升：**
    - **[Quantization] 添加Humming量化内核 (9f771b3):** 引入新的量化方法，旨在降低模型部署成本（“便宜 (cheap)”）和提升推理速度（“快速 (fast)”）。

### 3. 对项目的影响和潜在意义

- **稳定性和可靠性提升：** 大量的Bug修复，尤其是在MoE和注意力等核心模块，将显著提升vLLM在生产环境中的稳定性和推理结果的准确性。
- **性能优化持续进行：** 统一注意力内核、修复路由偏差等优化，将直接转化为更低的延迟和更高的吞吐量，巩固vLLM在性能上的领先地位。
- **生态兼容性增强：** 对ROCm、新Python版本、新CUDA版本以及更多模型（Gemma4, GLM）的支持，扩大了vLLM的适用场景，吸引了更广泛的用户和开发者社区。
- **技术前瞻性：** 支持Python 3.14和最新的CUDA版本，表明项目团队致力于保持技术栈的先进性，为未来的性能提升和功能扩展铺平道路。

### 4. 值得关注的技术点

- **`fused_moe` 路由偏差修复 (333529d):** 对于使用MoE架构的模型（如Mixtral），这是一个关键的修复，直接影响模型输出的质量和专家负载的均衡性。
- **`triton_unified_attention` 内核统一 (914d046):** 这是对底层计算内核的深度优化，可能对长序列或高并发场景下的性能有显著影响。
- **`kv_offload+HMA` 支持多KV组 (51adca7):** 这是对KV缓存卸载和异构内存访问的持续改进，对于处理超长上下文或降低显存占用至关重要。
- **`Humming` 量化内核 (9f771b3):** 引入新的量化技术，值得关注其精度和性能表现，可能成为未来部署低精度模型的新选择。

### 5. 基于项目背景，这些提交如何影响项目发展

vLLM的目标是“**Easy, fast, and cheap LLM serving for everyone**

## 详细提交记录

### [a474da2](https://github.com/vllm-project/vllm/commit/a474da28131f61684849b31e29af0eebaaedc383)

- **作者**: Wentao Ye
- **时间**: 2026-04-24T23:28:18Z
- **提交信息**: [Refactor] Remove unused dead code (#40640)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [ce6a199](https://github.com/vllm-project/vllm/commit/ce6a199ecc0996254efcf6fe532c40d9b9432922)

- **作者**: Lucas Kabela
- **时间**: 2026-04-24T23:25:03Z
- **提交信息**: [BE][Bugfix] Respect TORCH_COMPILE_DISABLE env var at the vLLM config level for torch 2.12 (#40715)

Signed-off-by: Lucas Kabela <lucaskabela@meta.com>

### [f88763e](https://github.com/vllm-project/vllm/commit/f88763efc35f8da4d3cfe611a0497d3d3251b9e9)

- **作者**: Ignacio Sica
- **时间**: 2026-04-24T23:13:52Z
- **提交信息**: [Bugfix] add seq_lens_cpu_upper_bound to CommonAttentionMetadata in mla_runner.py (#40844)

Signed-off-by: ignaciosica <mignacio.sica@gmail.com>

### [333529d](https://github.com/vllm-project/vllm/commit/333529deae59cd4100df540f225470c9bc539bee)

- **作者**: Artem Perevedentsev
- **时间**: 2026-04-24T22:06:41Z
- **提交信息**: [EPLB] Fix replica selection bias in fused_moe router (#40810)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [8825608](https://github.com/vllm-project/vllm/commit/88256082058fdbd41281c4f1f9a19663a4d7a668)

- **作者**: Zhang Jian
- **时间**: 2026-04-24T20:40:07Z
- **提交信息**: [Bugfix][CI] Fix wrong residual shape in TestFusedAddRMSNorm.example_inputs that causes flaky test (#40629)

Signed-off-by: Zhang Jian <jianmusings@gmail.com>

### [095d2f8](https://github.com/vllm-project/vllm/commit/095d2f87e8519de27f1fc39d9d22b299efdf0010)

- **作者**: qli88
- **时间**: 2026-04-24T19:54:40Z
- **提交信息**: [Bug] Fix GLM-5.1 running error on ROCm platform (#40763)

Signed-off-by: Qiang Li <qiang.li2@amd.com>

### [2179252](https://github.com/vllm-project/vllm/commit/21792520e727676e4d4e8bd24a8fe29da4dab152)

- **作者**: Neil Schemenauer
- **时间**: 2026-04-24T17:24:05Z
- **提交信息**: [Build] Add Python 3.14 to supported version list. (#34770)

Signed-off-by: Neil Schemenauer <nas@arctrix.com>
Co-authored-by: Simon Mo <simon.mo@hey.com>

### [5e11b40](https://github.com/vllm-project/vllm/commit/5e11b403657ebd5507e07200c2ba2b8f186d07da)

- **作者**: Alex Brooks
- **时间**: 2026-04-24T16:30:00Z
- **提交信息**: [Frontend] Delegate to vLLM Omni When `--omni` Passed (#40744)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [f768b44](https://github.com/vllm-project/vllm/commit/f768b4473e1bd55023dcaff63984cfdd08902fc8)

- **作者**: labAxiaoming
- **时间**: 2026-04-24T15:26:09Z
- **提交信息**: [Docs] Add docs for context extension using the yarn method (#37430)

Signed-off-by: xiaoming <1259730330@qq.com>
Signed-off-by: labAxiaoming <34019940+labAxiaoming@users.noreply.github.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>

### [914d046](https://github.com/vllm-project/vllm/commit/914d0464c1b1ec77d1560b485624f32002532b83)

- **作者**: JartX
- **时间**: 2026-04-24T15:18:06Z
- **提交信息**: [Refactor] Unify 2D/3D kernels in triton_unified_attention (#40631)

Signed-off-by: JartX <sagformas@epdcenter.es>

### [9f771b3](https://github.com/vllm-project/vllm/commit/9f771b3ab92d26a7d91a8255572c5d8d2b3ad601)

- **作者**: Jinzhen Lin
- **时间**: 2026-04-24T13:29:44Z
- **提交信息**: [Quantization] add humming quantization kernel (#34556)

### [c9d3c6e](https://github.com/vllm-project/vllm/commit/c9d3c6e6af7fb848d3f03e256484f68a00201020)

- **作者**: Itay Alroy
- **时间**: 2026-04-24T13:05:31Z
- **提交信息**: fused_moe: treat NIXL EP as batched experts (#40412)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>

### [51adca7](https://github.com/vllm-project/vllm/commit/51adca74e6be951c86e920046a83bfc061193ba2)

- **作者**: Or Ozeri
- **时间**: 2026-04-24T12:32:29Z
- **提交信息**: [kv_offload+HMA][9/N]: Support lookup with multiple KV groups (#39401)

Signed-off-by: Or Ozeri <oro@il.ibm.com>

### [e8eb049](https://github.com/vllm-project/vllm/commit/e8eb0490ce098b1add05877363b185f3a7b570c5)

- **作者**: Netanel Haber
- **时间**: 2026-04-24T11:53:23Z
- **提交信息**: [Bugfix][MoE] Unpad routed output before shared expert add [Fixes #35949] (#40794)

Signed-off-by: Netanel Haber <nhaber@nvidia.com>

### [e8ee2a7](https://github.com/vllm-project/vllm/commit/e8ee2a78dbc08d398d5e798a149657b8aa821850)

- **作者**: Jiangyun Zhu
- **时间**: 2026-04-24T11:25:55Z
- **提交信息**: [Attention] use diff kv backend for mimo v2 flash (#40045)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [2ec18f5](https://github.com/vllm-project/vllm/commit/2ec18f5df43e7f6c51e95125759904d39bd01630)

- **作者**: Thomas
- **时间**: 2026-04-24T11:01:56Z
- **提交信息**: [Bugfix][Parser] Fix Mistral tool parser for HF tokenizers (#39294)

Signed-off-by: thomasmaindron <thomasmaindron@users.noreply.github.com>
Co-authored-by: thomasmaindron <thomasmaindron@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [6dec49f](https://github.com/vllm-project/vllm/commit/6dec49f27ece339c59d5eb92f33120c11c0c3b74)

- **作者**: Dmitry Tokarev
- **时间**: 2026-04-24T10:27:11Z
- **提交信息**: [Build] Bump CUDA to 13.0.2 to match PyTorch 2.11.0 (#40669)

Signed-off-by: Dmitry Tokarev <dtokarev@nvidia.com>

### [b5587e1](https://github.com/vllm-project/vllm/commit/b5587e1013d0e352bb33c30b456d5221aebecd8c)

- **作者**: Shanshan Shen
- **时间**: 2026-04-24T10:12:14Z
- **提交信息**: [CI/Build] Add e2e test for ViT CUDA graph (#40780)

Signed-off-by: shen-shanshan <467638484@qq.com>

### [9ad5abe](https://github.com/vllm-project/vllm/commit/9ad5abe7722ba4eb9cb484689dd90529e76c41c5)

- **作者**: milesial
- **时间**: 2026-04-24T09:18:55Z
- **提交信息**: Fix Nano Nemotron VL static image inputs (#40724)

Signed-off-by: Alexandre Milesi <milesial@users.noreply.github.com>

### [7d3195e](https://github.com/vllm-project/vllm/commit/7d3195ea9fc88e31131099d2d2122fe38558a87a)

- **作者**: Woosuk Kwon
- **时间**: 2026-04-24T08:40:20Z
- **提交信息**: [Bugfix] Fix IMA in DSA + MTP (#40772)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [512f522](https://github.com/vllm-project/vllm/commit/512f52219240b0aa1be687955ab52fcdd0c5a40e)

- **作者**: Luciano Martins
- **时间**: 2026-04-24T08:27:46Z
- **提交信息**: [Model] Gemma4: add bidirectional vision attention for sliding layers with window guard (#40534)

Signed-off-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Signed-off-by: Luciano Martins <lucianomartins@google.com>
Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Co-authored-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Isotr0py <2037008807@qq.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [4c34b2f](https://github.com/vllm-project/vllm/commit/4c34b2f6fc63435c791c9054c579ca3f8c902bb6)

- **作者**: Yuwen Zhou
- **时间**: 2026-04-24T08:26:16Z
- **提交信息**: [XPU] Enable torch.compile for XPU GDN attention (#39466)

Signed-off-by: yuwenzho <yuwen.zhou@intel.com>
Signed-off-by: Yuwen Zhou <yuwen.zhou@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-04-25
**监控日期**: 2026-04-24
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4476
- **最后更新**: 2026-04-25T11:21:55Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 10
- **主要提交者**: NumberWan, 汪志鹏, Yueqian Lin

## AI分析总结

好的，根据您提供的仓库背景和提交记录，以下是对昨日更新的要点分析：

### 1. 主要更新类型

- **功能新增 (Feature):** 3项
- **Bug修复 (Bugfix):** 4项
- **基准测试 (Benchmark):** 1项
- **重构 (Refactor):** 2项
- **文档更新 (Docs):** 1项
- **性能优化 (Perf):** 1项
- **CI/测试 (CI):** 1项

### 2. 关键变更点及其与项目整体方向的关系

- **多模态能力扩展 (Feature):**
    - **流式视频输入 (7b87632):** 实现了基于EVS帧过滤的流式视频输入功能。这直接服务于项目“omni-modality”（全模态）的核心目标，使模型能够处理实时或长视频流，而非仅限静态图像或短片段。
    - **通用TTS基准测试 (39e3fd3):** 为Qwen3-TTS和VoxCPM2模型增加了包含语音克隆、默认和设计三种任务类型的通用基准测试。这表明项目正在系统性地评估和集成语音合成能力，是完善“全模态”中“音频输出”环节的关键一步。
    - **Coordinator PUB机制优化 (678af19):** 优化了协调器的发布机制。这属于底层架构优化，旨在提升多模型、多模态服务场景下的通信效率和稳定性，是支撑复杂多模态工作流的基础。

- **硬件与生态兼容性 (Feature):**
    - **torch.accelerator支持 (d388583):** 增加了对MUSA加速器的支持。这体现了项目“for everyone”的愿景，通过支持更多硬件平台（如国产GPU），降低使用门槛，扩大用户基础。

- **稳定性与可靠性提升 (Bugfix):**
    - **多阶段引擎优雅关闭 (b33d536):** 修复了多阶段引擎进程的优雅关闭问题。这对于生产环境至关重要，能防止资源泄漏和服务中断，提升服务的可靠性。
    - **GLM-Image在线生成失败 (0fe7685):** 修复了GLM-Image模型在多阶段在线生成时失败的问题。直接提升了特定模型的服务稳定性。
    - **Flux2klein文本输入处理 (77e8ba0) 和 T5文本编码器 (c6edb34):** 修复了FLUX系列模型中的文本输入处理问题。FLUX是当前热门的图像生成模型，这些修复确保了项目能稳定支持前沿模型。

- **代码库清理与维护 (Refactor):**
    - **移除冗余基准测试 (b8bd6fb):** 清理了Qwen3-Omni模型中的冗余基准测试，有助于保持代码库的整洁和可维护性。
    - **移除bagel配置 (37e5954) 和 sentinel默认优先级 (22ffb85):** 属于配置重构的一部分，旨在简化配置系统，使其更清晰、更易用。

- **文档与开发者体验 (Docs):**
    - **更新TTS模型添加指南 (e8d22d4):** 更新了添加TTS模型的技能文档和贡献指南，引入了“单阶段模式”。这降低了社区贡献者的门槛，鼓励更多人参与TTS模型的集成，加速生态建设。

### 3. 对项目的影响和潜在意义

- **加速“全模态”愿景落地:** 流式视频和TTS基准测试的加入，是项目从“支持多种模态”向“高效、流畅地处理复杂多模态任务”迈进的关键步骤。这使vllm-omni不仅能服务简单的图文任务，也能胜任视频理解、语音交互等更复杂的场景。
- **提升生产环境可靠性:** 多个Bug修复，特别是优雅关闭和在线生成失败的修复，显著提升了项目在生产环境中的稳定性和可用性，这对于吸引企业用户至关重要。
- **降低硬件门槛，扩大生态:** 对MUSA加速器的支持，直接响应了国产化需求，有助于项目在更广泛的硬件生态中推广。
- **优化开发者体验:** 文档更新和代码库清理，降低了社区贡献的难度，有助于吸引更多开发者参与，形成良性循环。

### 4. 值得关注的技术点

- **流式视频处理 (EVS):** 这是实现实时视频分析的核心技术。RFC #2201的Phase 2-4落地，表明项目在视频处理架构上取得了实质性进展，值得关注其实现细节和性能表现。
- **多阶段引擎进程管理:** 优雅关闭的Bug修复，揭示了项目在多进程、多阶段引擎架构上的复杂性。这是高性能推理服务的一个关键挑战，其解决方案对其他类似项目有参考价值。
- **Coordinator PUB机制优化:** 这是分布式推理系统中的关键组件，其优化可能涉及消息队列、负载均衡或状态同步等底层技术，直接影响系统的吞吐量和延迟。

### 5. 基于项目背景，这些提交如何影响项目发展

- **巩固“Easy, fast, and cheap”的定位:** 通过支持更多硬件（MUSA）和优化底层架构（Coordinator），项目在“cheap”（低成本）和“fast”（快速）上持续进步。通过修复Bug和优化文档，项目在“Easy”（易用）上不断改善。
- **从“多模态支持”走向“多模态服务”:** 早期的提交可能侧重于“能否支持某种模型”，而昨日的提交（如流式视频、TTS基准测试）表明项目重心已转向“如何高效、稳定地服务复杂多模态任务”。这是项目成熟度提升的重要标志。
- **构建活跃的社区生态

## 详细提交记录

### [39e3fd3](https://github.com/vllm-project/vllm-omni/commit/39e3fd3d12112be64864fb239261c927086df3ed)

- **作者**: Yueqian Lin
- **时间**: 2026-04-24T15:35:33Z
- **提交信息**: [Benchmark] Universal TTS benchmark: Qwen3-TTS + VoxCPM2 with 3 task types (voice-clone/default/design) (#2835)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Signed-off-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [d388583](https://github.com/vllm-project/vllm-omni/commit/d388583e0b7dfd151fc780ed2e9c721f9c6a2d6e)

- **作者**: R0CKSTAR
- **时间**: 2026-04-24T15:31:45Z
- **提交信息**: [MUSA][Feat] torch.accelerator support (#3101)

Signed-off-by: Xiaodong Ye <yeahdongcn@gmail.com>
Signed-off-by: Canlin Guo <961750412@qq.com>
Co-authored-by: Canlin Guo <961750412@qq.com>

### [7b87632](https://github.com/vllm-project/vllm-omni/commit/7b876324c24d129d6bfa1b5778d8169b2e42bbde)

- **作者**: Sy03
- **时间**: 2026-04-24T14:54:35Z
- **提交信息**: [Feature] Streaming video input with EVS frame filtering (RFC #2201 Phase 2-4) (#2342)

Signed-off-by: Sy03 <1370724210@qq.com>
Co-authored-by: shimei.jmh <shimei.jmh@taobao.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [b8bd6fb](https://github.com/vllm-project/vllm-omni/commit/b8bd6fbbdb6213e3780940edb359c29affa2fc93)

- **作者**: amy-why-3459
- **时间**: 2026-04-24T13:22:03Z
- **提交信息**: [Refactor] Remove redundant benchmarks from Qwen3-Omni (#3108)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [37e5954](https://github.com/vllm-project/vllm-omni/commit/37e5954acfe6de8954831b6f7bf4d2d29f5dbc6b)

- **作者**: 汪志鹏
- **时间**: 2026-04-24T13:21:30Z
- **提交信息**: [Config Refactor]: Remove bagel yaml (#2936)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [22ffb85](https://github.com/vllm-project/vllm-omni/commit/22ffb850635eaeeb00bb40dce17c37b0bfaabbe4)

- **作者**: Haco
- **时间**: 2026-04-24T12:07:24Z
- **提交信息**: [Config Refactor] sentinel default precedence (#3078)

Signed-off-by: lishunyang <lishunyang12@163.com>
Signed-off-by: xiaohajiayou <923390377@qq.com>
Co-authored-by: lishunyang <lishunyang12@163.com>

### [b33d536](https://github.com/vllm-project/vllm-omni/commit/b33d536f63810cc62a569e7806aec7ce7531236f)

- **作者**: Lancer
- **时间**: 2026-04-24T12:01:01Z
- **提交信息**: [Bugfix] graceful shutdown for  multi-stage engine processes (#3001)

Signed-off-by: Lancer <maruixiang6688@gmail.com>

### [0fe7685](https://github.com/vllm-project/vllm-omni/commit/0fe76857acc0447419829710d50d8a482266be93)

- **作者**: Lancer
- **时间**: 2026-04-24T12:00:14Z
- **提交信息**: [Bugfix] fix GLM-Image multi-stage online generation fail (#3084)

Signed-off-by: Lancer <maruixiang6688@gmail.com>

### [e8d22d4](https://github.com/vllm-project/vllm-omni/commit/e8d22d4fa8992db621e285460290fbb49564b7fc)

- **作者**: Yueqian Lin
- **时间**: 2026-04-24T11:56:32Z
- **提交信息**: docs: update add-tts-model skill and contributing guide with single-stage patterns (#2806)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Signed-off-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [77e8ba0](https://github.com/vllm-project/vllm-omni/commit/77e8ba0a7bcc15e5eb8052f9e986d27eee042cac)

- **作者**: Alex Brooks
- **时间**: 2026-04-24T11:54:41Z
- **提交信息**: [Bugfix] Fix Flux2klein Text Input Processing (#3098)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [c6edb34](https://github.com/vllm-project/vllm-omni/commit/c6edb34d044dd475f961e388f802d6ffa0e7ed72)

- **作者**: Lancer
- **时间**: 2026-04-24T10:01:52Z
- **提交信息**: [Bugfix] T5 text encoder to render correct text in FLUX.1-dev (#2760)

Signed-off-by: Lancer <maruixiang6688@gmail.com>

### [fb4204e](https://github.com/vllm-project/vllm-omni/commit/fb4204ebf658ccff4b7cffb19473adc77da72f62)

- **作者**: bjf-frz
- **时间**: 2026-04-24T08:58:45Z
- **提交信息**: [CI][Perf] Add Wan22 i2v perf nightly ci (#3063)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [e24f86a](https://github.com/vllm-project/vllm-omni/commit/e24f86ae2e269ddab24d90f9026b40b440b18cff)

- **作者**: bjf-frz
- **时间**: 2026-04-24T08:30:24Z
- **提交信息**: [Enhancement]modify profiling.md (#3051)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [678af19](https://github.com/vllm-project/vllm-omni/commit/678af192404cea9ba86fb6f03fa1b139c3b863d4)

- **作者**: NumberWan
- **时间**: 2026-04-24T07:09:23Z
- **提交信息**: [Feature] Coordinator PUB mechanism optimization (#2442)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

---
