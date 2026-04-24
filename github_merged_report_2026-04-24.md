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
- **最后更新**: 2026-04-24T09:05:12Z

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
- **星标数**: 2214
- **最后更新**: 2026-04-24T12:25:16Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: zhtshr

## AI分析总结

好的，根据您提供的项目背景和提交记录，以下是对昨日更新的分析总结：

### 1. 主要更新类型

*   **功能新增**：这是本次更新的核心。新增了调度机制、工作负载模拟、分布式推理配置以及网络协议改进。
*   **性能优化**：通过引入分块数据传输和更可靠的网络连接处理，提升了大规模数据传输的效率和稳定性。
*   **重构**：对解耦（disagg）连接逻辑进行了显著重构，包括IP地址规范化、错误处理和消息协议更新，以支持更复杂的分布式场景。

### 2. 关键变更点及其与项目整体方向的关系

*   **新增调度与工作负载机制**：引入了新的配置文件（控制器、编码器、变换器、解码器）和动态工作负载模拟脚本 (`run_user.py`)。这与项目“轻量级视频生成推理框架”的目标高度一致，旨在为分布式视频推理流水线提供可配置、可测试的调度和负载管理能力。
*   **增强解耦连接可靠性**：改进了 `_normalize_loopback_host` 逻辑，确保IPv4回环地址的一致性；增强了错误处理和状态同步。这直接服务于项目在分布式环境中部署视频推理管线的需求，提升了系统的健壮性。
*   **引入分块数据传输**：通过 `MOONCAKE_TRANSFER_CHUNK_BYTES` 环境变量支持分块传输，以更高效地处理大型张量。这对于视频推理中处理高分辨率、长时长的视频数据至关重要，直接优化了核心性能。
*   **更新协议与元数据**：在ZMQ通信中增加了 `receiver_engine_rank`，确保在分布式设置中消息的正确路由。这进一步完善了分布式推理的基础设施，是项目向可扩展、模块化架构演进的关键一步。

### 3. 对项目的影响和潜在意义

*   **提升可配置性与可测试性**：新增的配置文件和负载模拟脚本，使得开发者可以更方便地配置、测试和调优不同规模的分布式推理部署，加速了从开发到生产的流程。
*   **增强系统可靠性**：对网络连接、错误处理和状态同步的改进，显著降低了分布式推理管线在复杂网络环境下崩溃或数据丢失的风险，为生产级部署奠定了基础。
*   **优化大规模推理性能**：分块数据传输机制是处理视频等大型数据的关键优化，有望显著提升吞吐量并降低延迟，使框架能更好地应对高分辨率、长视频等计算密集型任务。
*   **推动架构演进**：这些更新共同推动项目从单机或简单分布式原型，向一个具备调度、负载管理和高可靠性的成熟分布式推理系统演进。

### 4. 值得关注的技术点

*   **`DISAGG_FORCE_IPV4_LOOPBACK` 环境变量**：用于强制使用IPv4回环地址，解决了混合协议（IPv4/IPv6）环境下的连接问题，是一个实用的网络兼容性解决方案。
*   **`MOONCAKE_TRANSFER_CHUNK_BYTES` 环境变量**：分块传输的引入，暗示了底层可能使用了类似RDMA的高性能网络协议，通过控制单次传输大小来优化性能，是性能调优的关键参数。
*   **`locust` 依赖**：新增的 `locust` 库表明项目开始引入成熟的负载测试工具，用于模拟真实用户行为，进行压力测试和性能基准测试。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **从“可用”到“好用”**：README 强调这是一个“轻量视频生成推理框架”。之前的版本可能侧重于核心推理功能。本次更新通过引入调度、负载模拟和可靠性改进，使框架从“能跑”向“能稳定、高效地跑在分布式环境中”迈进，大大提升了其实用性和易用性。
*   **支撑更大规模部署**：分布式推理是扩展视频生成服务的关键。这些提交为框架提供了必要的调度、网络和数据处理能力，使其能够支持更复杂的多节点、多GPU部署，为处理更大规模、更高质量的视频生成任务铺平了道路。
*   **强化“推理”而非“训练”定位**：更新内容（如负载模拟、分块传输、分布式配置）都紧密围绕“推理”场景，特别是视频推理中常见的动态负载和大型张量处理。这进一步巩固了项目作为专业推理框架的定位，与训练框架形成明确区分。

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
- **星标数**: 2039
- **最后更新**: 2026-04-24T10:56:34Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

好的，这是对仓库 `aigc-apps/VideoX-Fun` 提交记录 `199a43b` 的分析总结。

### 提交记录分析总结

**提交:** `199a43b`
**标题:** Update READMEs, add LongCatVideo multi-GPU inference, and fix import bugs (#485)

---

#### 1. 主要更新类型

本次提交是一次**综合性更新**，涵盖了以下类型：
- **功能新增**: 新增了 `LongCatVideo` 的多GPU推理支持。
- **Bug修复**: 修复了导入相关的错误。
- **文档更新**: 更新了多个README文件。

#### 2. 关键变更点及其与项目整体方向的关系

- **新增 `LongCatVideo` 多GPU推理**:
  - **变更点**: 为 `LongCatVideo` 功能增加了多GPU并行推理的能力。
  - **与项目方向的关系**: 项目README中提到了多个视频生成模型（如CogVideoX, Wan2.1），其核心目标是提供高效、可扩展的视频生成解决方案。`LongCatVideo` 很可能是一个用于生成长视频或拼接视频的功能模块。增加多GPU支持直接响应了**提升生成效率**和**处理更大规模任务**的需求，是项目从单卡演示走向生产级应用的关键一步。

- **修复导入Bug**:
  - **变更点**: 修正了代码中某些模块或库的导入错误。
  - **与项目方向的关系**: 项目代码库随着功能增加而变得复杂，导入错误是常见的开发问题。修复此类Bug是**保证项目稳定性和可用性**的基础，确保用户和开发者能顺利运行和扩展代码。

- **更新README文档**:
  - **变更点**: 对项目的多个语言版本的README文件进行了更新。
  - **与项目方向的关系**: 项目README强调了对多语言（中、英、日）的支持。更新文档是**提升项目可访问性和社区友好度**的重要举措，有助于吸引全球开发者，并清晰传达项目的最新进展和使用方法。

#### 3. 对项目的影响和潜在意义

- **性能与可扩展性提升**: `LongCatVideo` 的多GPU推理是本次更新的亮点。它意味着用户可以利用多张显卡显著缩短长视频的生成时间，或者生成更高质量、更长的视频内容。这对于需要处理复杂视频任务的用户（如影视制作、内容创作）具有**重大实用价值**。
- **稳定性增强**: 修复导入Bug降低了用户在使用过程中遇到环境配置或代码运行错误的概率，提升了项目的**健壮性**和**用户体验**。
- **社区吸引力增强**: 更新多语言README文档，特别是对新增功能的说明，能帮助不同语言的用户更快上手新特性，有助于**扩大项目影响力和用户基础**。

#### 4. 值得关注的技术点

- **多GPU推理实现**: 虽然提交信息没有透露具体实现细节，但如何将 `LongCatVideo` 的推理流程（可能涉及模型分片、数据并行、流水线并行等）扩展到多GPU，是一个值得关注的技术点。这通常涉及到分布式计算框架（如PyTorch DDP/FSDP）的应用。
- **`LongCatVideo` 模块本身**: 这个模块的具体功能（是视频拼接、长视频生成还是其他？）和其内部架构值得关注。理解它有助于评估多GPU支持带来的实际收益。

#### 5. 基于项目背景，这些提交如何影响项目发展

- **从“能用”到“好用”的跨越**: 根据README，项目提供了多种模型的Demo。本次提交通过增加多GPU支持，将 `LongCatVideo` 从一个可能仅适用于短片段或单卡演示的功能，提升为能够处理**实际生产级负载**的工具。这标志着项目在**工程化和实用性**上迈出了重要一步。
- **巩固核心定位**: 项目定位为“视频生成工具”。通过解决性能瓶颈（多GPU）和稳定性问题（Bug修复），项目正在强化其作为**可靠、高效视频生成解决方案**的核心价值，而不仅仅是提供一个模型演示平台。
- **促进社区贡献**: 清晰的文档和稳定的代码是吸引社区贡献的基础。本次提交同时兼顾了这两点，为项目后续吸引更多开发者参与、贡献新功能或优化现有功能创造了良好条件。

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
- **星标数**: 5494
- **最后更新**: 2026-04-24T21:21:55Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Ka-Hyun Nam, nv-yunzheq, Observer007

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bug Fixes):** 4项
- **功能新增 (New Features):** 2项
- **性能优化 (Performance):** 1项

### 2. 关键变更点及其与项目整体方向的关系

FlashInfer 项目旨在为 LLM 推理提供高性能 GPU 内核。这些提交紧密围绕这一目标，主要关注于**提升稳定性、扩展功能支持、以及优化性能**。

- **Bug修复 (提升稳定性与兼容性):**
    - **修复 JIT 缓存构建问题 (`8eedd64`):** 修复了在特定构建流程中，由于缺少符号链接导致 AOT 编译失败的问题。这直接关系到项目的**可部署性和构建流程的健壮性**，确保用户能顺利安装和使用。
    - **修复 MoE 内核的越界访问 (`364081c`):** 修复了 vLLM 中报告的 MoE 路由内核的越界内存访问问题。这直接关系到**与主流推理框架 (vLLM) 的兼容性**和**运行时的稳定性**，是生产环境部署的关键。
    - **修复 Blackwell GDN 内核精度问题 (`3516d2b`):** 修复了一个深藏在 `sCumprod` 计算中的坐标错误，导致 Blackwell 架构上的 GDN 内核精度不达标。这体现了项目对**最新硬件架构 (Blackwell) 的支持**和对**计算精度的极致追求**。
    - **修复 MoE MXFP8 权重形状检查 (`0798a7d`):** 修复了在使用非门控激活函数时，CUTLASS 融合 MoE 后端对 MXFP8 量化权重的形状检查错误。这扩大了**量化 MoE 内核的适用范围**，使其能支持更多激活函数类型。

- **功能新增 (扩展能力与集成):**
    - **为 TopK 操作添加新参数 (`ef46793`):** 为 TopK 操作添加了 `row_starts` 和 `dsa_graph_safe` 参数，以支持 SGLang 的 DSA (Dynamic Speculative Attention) 集成。这表明项目正积极与**其他推理框架 (SGLang)** 进行深度集成，并支持更高级的推理优化技术。
    - **为 tinygemm_bf16 添加无偏置路径 (`cc682da`):** 为 `tinygemm_bf16` 内核添加了专用的无偏置路径，避免了在 Python 层创建零偏置张量的开销。这直接**优化了特定场景下的性能**，并增强了内核的灵活性。

- **性能优化 (提升效率):**
    - **优化 MoE alltoall 构建 (`ef3e37b`):** 为 `mnnvl_moe_alltoall` 模块添加了缺失的依赖 (`logger.cpp`, `stringUtils.cpp`)，以解决链接问题。这属于**构建系统的优化**，确保新模块能正确编译和链接，是性能优化的基础。

### 3. 对项目的影响和潜在意义

- **稳定性和可靠性显著提升:** 多个 Bug 修复（特别是越界访问和精度问题）直接提升了内核在复杂场景下的稳定性和数值可靠性，这对于生产级推理服务至关重要。
- **生态兼容性增强:** 修复与 vLLM 的兼容性问题，并主动为 SGLang 添加新功能，表明项目正积极融入更广泛的 LLM 推理生态，降低用户集成成本。
- **前沿硬件支持:** 针对 Blackwell 架构的精度修复，展示了项目对最新 NVIDIA GPU 架构的快速跟进和支持能力。
- **量化推理能力扩展:** 修复 MXFP8 权重形状检查，使得更广泛的激活函数可以与高效的量化 MoE 内核结合，为用户提供了更多样的性能-精度权衡选择。

### 4. 值得关注的技术点

- **JIT 缓存构建的复杂性:** 提交 `8eedd64` 揭示了 FlashInfer 混合 AOT (Ahead-of-Time) 和 JIT (Just-in-Time) 编译策略的复杂性。构建系统需要精心处理符号链接和依赖关系，才能确保在不同环境下都能成功编译。
- **`sCumprod` 的坐标计算:** 提交 `3516d2b` 修复的 Bug 非常隐蔽，涉及到对 `sCumprod` 张量最后一个坐标的正确获取。这提醒我们，在编写高性能 CUDA 内核时，对底层数据结构和坐标变换的理解必须非常精确。
- **`dsa_graph_safe` 的设计:** 提交 `ef46793` 引入的 `dsa_graph_safe` 参数，通过禁用某些优化路径来确保在 DSA 图执行环境下的安全性。这是一种常见的权衡：为了兼容更高级的图执行框架，有时需要牺牲部分微基准性能。
- **无偏置路径的优化:** 提交 `cc682da` 通过在 C++ 内核层直接处理 `bias=None` 的情况，避免了 Python 层的零张量创建和拷贝开销。这是一种典型的“零开销抽象”实践，将性能优化下沉到最底层。

### 5. 基于项目背景的总结与展望

结合 README 中“为推理提供高性能 GPU 内核”的目标，昨日的更新清晰地展示了 FlashInfer 项目的发展方向：

1.  **从“能用”到“好用”**: 项目在提供高性能内核的同时，正投入大量精力修复 Bug、增强稳定性、

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
- **星标数**: 3419
- **最后更新**: 2026-04-24T17:14:18Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Junda Su, William Lin

## AI分析总结

好的，这是对 `hao-ai-lab/FastVideo` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **Bug修复**：修复了图像到视频（I2V）VAE编码中的一个类型问题。
*   **功能新增**：为LTX-2模型添加了类型化的续写状态和流式会话存储功能。

### 2. 关键变更点及其与项目方向的关系

*   **Bug修复 (#1249)**：修复了在I2V（图像到视频）流程中，当输入图像为`uint8`类型的PIL图像时，VAE编码器可能出现的错误。这直接关系到项目的核心功能——从图像生成视频的稳定性和正确性。
*   **功能新增 (#1250)**：为LTX-2模型引入了“类型化续写状态”和“流式会话存储”。这表明项目正在增强对长视频生成或连续生成场景的支持，通过保存和恢复生成状态，可以实现更长的、更可控的视频生成过程。

### 3. 对项目的影响和潜在意义

*   **提升稳定性**：Bug修复直接解决了I2V流程中的一个潜在崩溃点，提高了该核心功能的鲁棒性，对依赖此功能的用户至关重要。
*   **扩展能力边界**：LTX-2的新功能是向“生产级”视频生成工具迈出的重要一步。它允许用户进行更复杂的操作，例如暂停、续写、或基于之前生成的内容进行迭代，而不是每次从头开始。这极大地提升了用户体验和项目的实用性。

### 4. 值得关注的技术点

*   **`uint8` 类型处理**：在深度学习框架中，图像数据通常需要归一化到`[0, 1]`的浮点数。这个Bug修复暗示了在I2V的VAE编码入口处，可能缺少对`uint8` PIL图像的自动类型转换或归一化处理，修复确保了数据管道的健壮性。
*   **流式会话存储**：这是一个架构层面的增强。`StreamingSessionStore` 和 `TypedLTX-2ContinuationState` 的设计，意味着项目正在构建一个状态管理机制，这对于支持长时间、可中断/恢复的视频生成任务至关重要，可能涉及序列化、反序列化以及高效的状态增量更新。

### 5. 结合项目背景的分析

*   **项目目标**：FastVideo 旨在提供一个快速、高效的视频生成框架。README 中强调了“Quick Start”和“Documentation”，表明其注重易用性和社区发展。
*   **更新如何影响发展**：
    *   **Bug修复** 直接提升了项目的可靠性和用户信任度，是维护项目健康发展的基础工作。
    *   **LTX-2新功能** 则直接响应了视频生成领域对“长视频”和“可控生成”的更高需求。通过引入状态管理和续写能力，FastVideo 不再局限于生成短视频片段，而是向更复杂的视频创作工作流迈进。这与其“Fast”的定位并不矛盾，反而通过提供更高级的功能，吸引需要深度控制能力的专业用户，从而拓宽了项目的应用场景和社区基础。

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
- **星标数**: 33439
- **最后更新**: 2026-04-24T22:56:24Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Remy, Sayak Paul

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 1. 主要更新类型
- **CI/CD优化**：简化了发布工作流。
- **文档构建**：更新了文档构建工具的版本。

### 2. 关键变更点及其与项目整体方向的关系
- **`dad80d7` - 简化发布工作流**：
  - **变更点**：重构了项目的自动化发布流程，移除了不必要的步骤（如确定最新分支），并限制了权限。
  - **与项目方向的关系**：`diffusers` 是一个快速迭代的社区驱动项目，频繁发布新版本。简化发布流程能减少人工干预和出错概率，使团队能更高效、稳定地将新功能（如新的扩散模型、Pipeline、调度器）交付给用户，符合项目“易用性”和“快速迭代”的核心目标。
- **`d0c9cba` - 更新文档构建工具**：
  - **变更点**：将主文档构建工作流中使用的 `doc-builder` SHA（版本）升级。
  - **与项目方向的关系**：`diffusers` 拥有庞大且复杂的文档（包括API参考、教程、概念指南）。更新文档构建工具通常是为了修复构建错误、支持新文档特性或提升构建速度，这直接关系到项目文档的质量和可访问性，是项目维护“高质量文档”这一核心承诺的体现。

### 3. 对项目的影响和潜在意义
- **提升发布效率与可靠性**：简化的发布工作流意味着从代码合并到用户获得新版本的时间更短，且流程更健壮，减少了因流程复杂导致的发布失败风险。
- **保障文档质量**：及时更新文档构建工具，可以确保文档能正确生成，避免因工具版本过旧导致的格式错误或功能缺失，从而维持用户良好的学习与使用体验。
- **降低维护成本**：移除不必要的步骤和限制权限，减少了CI/CD脚本的复杂度，降低了未来维护这些脚本的认知负担和潜在安全风险。

### 4. 值得关注的技术点
- **CI/CD 最佳实践**：`dad80d7` 中提到的“限制权限为只读”和“使用SHA而非分支名”是CI/CD安全性和可复现性的良好实践。使用SHA可以避免因分支被强制推送而导致的构建失败，限制权限则遵循了最小权限原则。
- **`doc-builder` 工具**：这是Hugging Face生态中用于构建文档的专用工具。关注其版本更新，可以了解Hugging Face在文档基础设施上的改进方向。

### 5. 基于项目背景，这些提交如何影响项目发展
- **加速核心功能交付**：`diffusers` 的核心是提供各种扩散模型的实现。一个高效、可靠的发布流程（`dad80d7`）是项目持续发展的基石。它允许开发者将精力集中在实现新的模型架构（如Stable Diffusion 3、Sora等）和优化现有Pipeline上，而不是被繁琐的发布流程所困扰。
- **巩固社区生态**：高质量的文档（`d0c9cba`）是吸引和留住开发者的关键。对于`diffusers`这样一个旨在降低扩散模型使用门槛的项目，清晰的文档能帮助用户快速上手、理解原理并进行二次开发。持续优化文档构建流程，直接促进了项目社区的健康成长和生态繁荣。
- **总结**：这两次提交虽然不涉及任何用户可见的功能变更，但它们属于**基础设施优化**。它们通过提升内部开发效率和文档质量，间接但有力地推动了`diffusers`项目朝着“更易用、更可靠、迭代更快”的方向发展。

## 详细提交记录

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
- **星标数**: 397
- **最后更新**: 2026-04-23T16:31:28Z

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
- **星标数**: 12304
- **最后更新**: 2026-04-24T20:37:19Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

好的，这是对 `modelscope/DiffSynth-Studio` 仓库昨日提交记录的分析总结。

### 昨日更新要点分析

1.  **主要更新类型**
    *   **Bug修复**：本次提交明确为修复一个版本兼容性问题。

2.  **关键变更点及其与项目整体方向的关系**
    *   **变更点**：修复了 `transformers` 库的版本问题（`fix version issue of transformers`）。
    *   **与项目方向的关系**：`DiffSynth-Studio` 是一个基于扩散模型的视频/图像合成工具，其核心功能高度依赖 `transformers` 库（用于加载和管理各种预训练模型，如CLIP、Stable Diffusion等）。版本不兼容会导致模型加载失败、API调用错误或生成结果异常。修复此问题直接保障了项目核心功能的稳定运行，是维护项目可用性的基础操作。

3.  **对项目的影响和潜在意义**
    *   **直接影响**：解决了用户因 `transformers` 库版本不匹配而遇到的安装或运行错误，提升了项目的稳定性和用户体验。
    *   **潜在意义**：表明项目团队正在积极响应用户反馈或依赖库的更新，进行主动的维护和兼容性适配。这有助于降低用户的使用门槛，避免因依赖问题导致的“开箱即用”失败，对于吸引和留住用户至关重要。

4.  **值得关注的技术点**
    *   **依赖管理**：该提交强调了在快速发展的AI开源项目中，精确管理依赖库版本的重要性。一个微小的版本差异可能导致整个工作流崩溃。项目可能通过 `requirements.txt` 或 `setup.py` 中的版本约束（如 `transformers>=4.21.0,<4.30.0`）来避免此类问题，而本次修复可能是放宽或调整了这些约束。

5.  **基于README了解的项目背景，这些提交如何影响项目发展**
    *   **项目背景**：`DiffSynth-Studio` 是一个旨在提供高质量、易用的扩散模型合成工具的项目，其README展示了活跃的社区（Trendshift徽章）和PyPI发布。
    *   **对项目发展的影响**：这种“修复Bug”的提交虽然看似微小，但却是项目健康发展的基石。它直接支撑了README中承诺的“易用性”和“稳定性”。如果版本问题不解决，用户可能无法成功运行项目，导致负面评价和社区流失。因此，这类维护性提交是项目从“可用”走向“好用”的关键步骤，为后续的功能迭代和新特性发布提供了稳定的基础。

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
- **星标数**: 26376
- **最后更新**: 2026-04-24T22:33:57Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 15
- **主要提交者**: Lianmin Zheng, YC Yen-Ching Tseng, Kangrui Du

## AI分析总结

好的，这是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结。

### 1. 主要更新类型

-   **功能新增 (Features):** 支持 Hy3 预览版、支持 LTX 2.3 的 LoRA、为扩散模型添加强化学习 (RL) 的逐步 rollout 选项、支持可中断的分段 CUDA Graph。
-   **Bug 修复 (Bug Fixes):** 修复 AMD ROCm 版本门控问题、修复 LTX 2.3 代码路径统一问题、修复 Intel XPU 流水线并行问题（后回滚）、修复 CI 测试。
-   **性能优化 (Performance):** 消除注意力机制中的 DtoD 内存拷贝。
-   **硬件/平台适配 (Hardware/Platform Support):** 为 AMD GPU 更新 MoRI 库、为 Intel GPU 启用流水线并行（后回滚）、为 3FS 后端支持 DSA 和 Mamba 模型。
-   **文档/配置更新 (Docs/Config):** 更新 DeepSeek V4 的 FP8 检查点文档、废弃 `--collect-tokens-histogram` 参数。
-   **重构 (Refactoring):** 废弃旧的直方图收集参数，将其集成到 `--enable-metrics` 中。

### 2. 关键变更点及其与项目整体方向的关系

-   **硬件生态扩展 (AMD & Intel GPU):**
    -   `[AMD][bugfix]` 和 `[AMD][MoRI]`: 持续优化对 AMD GPU 的支持，修复版本兼容性问题并更新关键库，表明项目致力于成为多硬件平台（不仅仅是 NVIDIA）的推理引擎。
    -   `[Intel GPU]`: 尝试为 Intel XPU 启用流水线并行，虽然被回滚，但显示了项目对 Intel 硬件生态的重视和探索。
-   **模型能力增强 (Diffusion & MoE):**
    -   `[diffusion] feat: support LoRA for LTX2.3`: 为扩散模型引入 LoRA 支持，这是对生成式 AI 模型（如图像/视频生成）推理能力的扩展，符合项目“通用推理引擎”的定位。
    -   `[diffusion] RL: add per-step rollout options`: 将强化学习能力引入扩散模型推理，这是一个前沿方向，可能用于模型微调或推理策略优化。
    -   `support Hy3 preview`: 支持新的模型架构，保持与最新模型生态的同步。
-   **性能与效率提升:**
    -   `perf: eliminate attention DtoD copy`: 通过直接传递预分配的输出给 FlashAttention，消除了不必要的显存拷贝，这是一个典型的底层性能优化，能直接提升推理吞吐量。
    -   `[Experimental] Breakable Piecewise Cuda Graph`: 引入实验性的“可中断分段 CUDA Graph”，旨在解决动态形状下 CUDA Graph 的局限性，是提升推理性能的关键技术探索。
-   **基础设施与可观测性:**
    -   `Deprecate --collect-tokens-histogram`: 简化配置，将指标收集自动化，提升了项目的易用性和可观测性。

### 3. 对项目的影响和潜在意义

-   **提升硬件兼容性:** 对 AMD 和 Intel GPU 的持续投入，将吸引更广泛的用户群体，降低对单一硬件（NVIDIA）的依赖。
-   **扩展模型支持范围:** 支持 Hy3 和 LTX 2.3 的 LoRA，使项目能服务于更多类型的生成式 AI 模型（如视频生成、图像生成），而不仅仅是大型语言模型。
-   **增强推理性能:** 消除 DtoD 拷贝和实验性 CUDA Graph 优化，有望在特定场景下显著提升推理速度和资源利用率，这是推理引擎的核心竞争力。
-   **推动前沿技术落地:** 将 RL 与扩散模型结合，以及探索可中断 CUDA Graph，表明项目不仅关注当前主流需求，也在为未来的技术趋势做准备。

### 4. 值得关注的技术点

-   **`Breakable Piecewise Cuda Graph` (提交 `60bbb80`):** 这是一个非常值得关注的技术点。传统的 CUDA Graph 要求静态图，无法处理动态形状。这个实验性功能试图打破这个限制，如果成功，将极大提升 CUDA Graph 在真实场景（如变长输入）下的适用性和性能。
-   **`eliminate attention DtoD copy` (提交 `587fd15`):** 这是一个典型的“零成本抽象”优化。通过修改接口，让 FlashAttention 直接使用预分配的内存，避免了数据搬运，原理简单但效果显著。
-   **`[diffusion] RL` (提交 `92d262f`):** 将强化学习用于扩散模型的推理过程（如逐步 rollout），这可能是一种新的推理策略或模型微调方法，值得关注其后续发展和效果。

### 5. 基于项目背景的综合分析

根据 README，SGLang 是一个旨在提供**快速、高效、灵活**的推理服务的项目，其核心是 **SGLang Runtime (SRT)**。

-   **强化核心性能:** 提交 `587fd15` (消除 DtoD 拷贝) 和 `60bbb80` (可中断 CUDA Graph) 直接服务于“快速”和“高效”的目标，通过底层优化提升 SRT 的吞吐量和延迟表现。
-   **扩展服务边界:** 对 `Hy3`、`LTX 2.3` (扩散模型) 的支持，以及引入 `RL`

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
- **星标数**: 78034
- **最后更新**: 2026-04-24T23:18:44Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 20
- **主要提交者**: labAxiaoming, Yuwen Zhou, qli88

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 昨日更新要点总结

#### 1. 主要更新类型

-   **Bug修复 (Bugfix):** 数量最多，共6个，涉及MoE路由、注意力元数据、模型推理、测试稳定性等多个方面。
-   **新功能/模型支持 (Feature/Model):** 新增了Humming量化内核、Gemma4模型的双向视觉注意力、以及通过`--omni`参数委托给vLLM Omni的功能。
-   **构建与CI (Build/CI):** 更新了支持的Python版本（3.14）和CUDA版本（13.0.2），并添加了新的端到端测试。
-   **重构 (Refactor):** 统一了Triton注意力内核的2D/3D实现。
-   **文档 (Docs):** 新增了关于使用YaRN方法进行上下文扩展的文档。
-   **性能优化 (Performance):** 通过修复MoE路由偏差、优化KV卸载查找等，间接提升了性能。

#### 2. 关键变更点及其与项目方向的关系

-   **MoE (Mixture-of-Experts) 稳定性与性能提升:**
    -   `[EPLB] Fix replica selection bias` 和 `[Bugfix][MoE] Unpad routed output` 修复了MoE专家路由和输出处理中的关键错误。这与vLLM“快速、廉价”的目标直接相关，因为MoE是提升模型容量和推理效率的核心技术。
-   **新硬件与平台支持:**
    -   `[Bug] Fix GLM-5.1 running error on ROCm platform` 和 `[XPU] Enable torch.compile for XPU GDN attention` 表明vLLM正在积极扩展对AMD ROCm和Intel XPU等非NVIDIA平台的支持，体现了其“为所有人服务”的愿景。
-   **前沿模型与量化技术:**
    -   `[Model] Gemma4: add bidirectional vision attention` 和 `[Quantization] add humming quantization kernel` 显示vLLM正在紧跟模型发展（如Gemma 4）和量化技术（Humming），以支持最新、最高效的模型推理。
-   **基础设施现代化:**
    -   `[Build] Add Python 3.14` 和 `[Build] Bump CUDA to 13.0.2` 表明项目在积极维护和升级其基础依赖，确保与最新的开发环境和PyTorch生态兼容，这是项目长期健康发展的关键。

#### 3. 对项目的影响和潜在意义

-   **提升稳定性和可靠性:** 大量的Bug修复，特别是针对MoE和特定模型（如GLM、Nano Nemotron）的修复，将直接减少用户在生产环境中遇到的错误，提升vLLM作为服务框架的可靠性。
-   **扩大生态覆盖范围:** 对ROCm和XPU的支持，以及Python 3.14的适配，将吸引更广泛的用户群体，降低使用门槛，符合“为所有人服务”的宗旨。
-   **增强模型推理能力:** Gemma4的双向注意力支持、Humming量化内核的引入，以及上下文扩展文档的完善，都直接增强了vLLM处理最新、最复杂模型的能力，巩固其在LLM推理领域的领先地位。
-   **优化核心性能:** 对MoE路由偏差的修复和注意力内核的重构，有望在特定场景下带来显著的性能提升和内存效率优化，直接兑现“快速、廉价”的承诺。

#### 4. 值得关注的技术点

-   **`fused_moe` 路由偏差修复:** 这是一个关键的算法级Bug修复，可能对使用MoE架构的模型（如Mixtral、DeepSeek-V2）的推理质量和负载均衡产生重大影响。
-   **`triton_unified_attention` 重构:** 统一2D/3D内核是代码库的重要演进，有助于减少维护成本，并为未来支持更复杂的注意力模式（如MQA、GQA）打下基础。
-   **`kv_offload+HMA` 支持多KV组查找:** 这是KV缓存卸载（KV offload）功能的重要进展，对于在有限显存下处理超长上下文序列至关重要，是vLLM实现“廉价”服务的关键技术路径之一。
-   **`Humming` 量化内核:** 作为一种新的量化方法，它的加入可能提供比现有方法（如AWQ、GPTQ）更好的精度-速度权衡，值得关注其后续的性能基准测试结果。

#### 5. 这些提交如何影响项目发展

结合README中“Easy, fast, and cheap LLM serving for everyone”的目标，这些提交清晰地展示了vLLM的发展路径：

-   **Fast (快速):** 通过修复MoE性能瓶颈、重构注意力内核、引入新的量化方法，持续优化核心推理速度。
-   **Cheap (廉价):** 通过支持KV卸载、优化内存使用（如MoE unpadding），以及支持更广泛的硬件（AMD, Intel），降低推理成本，让更多用户能够负担得起。
-   **Easy (易用):** 通过修复各种平台和模型兼容性Bug、更新文档、支持更多模型（Gemma 4），降低用户部署和使用的门槛。
-   **For Everyone (为所有人):** 通过积极适配非NVIDIA平台、支持前沿模型和量化技术，确保vLLM能服务于最广泛的用户群体和最新的AI模型。

总而言之，昨日的更新是一次典型的“夯实基础、拓展边界”的迭代。大量Bug

## 详细提交记录

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
- **星标数**: 4473
- **最后更新**: 2026-04-24T19:21:53Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 10
- **主要提交者**: amy-why-3459, Yueqian Lin, 汪志鹏

## AI分析总结

好的，作为专业的代码分析助手，以下是对仓库 `vllm-project/vllm-omni` 昨日提交记录的分析总结。

### 昨日更新要点分析

#### 1. 主要更新类型

- **功能新增 (Feature)**: 3项
- **Bug修复 (Bugfix)**: 4项
- **性能优化/基准测试 (Benchmark/Perf)**: 2项
- **重构 (Refactor)**: 2项
- **文档更新 (Docs)**: 2项
- **配置重构 (Config Refactor)**: 2项

#### 2. 关键变更点及其与项目整体方向的关系

项目 `vllm-omni` 的目标是提供“**简单、快速、廉价的全模态模型服务**”。昨日更新紧密围绕这一核心目标展开：

- **强化全模态能力**:
    - **新增TTS基准测试**：为Qwen3-TTS和VoxCPM2模型增加了涵盖语音克隆、默认和设计三种任务类型的通用基准测试。这表明项目正在系统性地评估和验证其文本转语音（TTS）能力，是完善“全模态”服务的重要一环。
    - **新增流式视频输入**：实现了基于EVS帧过滤的流式视频输入功能。这直接扩展了项目对视频模态的支持，从静态图像处理迈向动态视频流处理，是“全模态”服务的关键技术突破。

- **提升易用性与效率**:
    - **`torch.accelerator` 支持**：为MUSA架构增加了对 `torch.accelerator` 的支持。这简化了多硬件平台（如摩尔线程GPU）的适配，降低了用户在不同硬件上部署的门槛，符合“简单”和“快速”的目标。
    - **优雅关闭多阶段引擎**：修复了多阶段引擎进程的优雅关闭问题。这提升了服务的稳定性和可靠性，是生产环境部署的关键。
    - **Coordinator PUB机制优化**：对协调器的发布机制进行了优化。这有助于提升多模态模型服务中不同组件间的通信效率，间接提升整体服务性能。

- **修复关键模型问题**:
    - **修复GLM-Image多阶段在线生成失败**：解决了特定模型（GLM-Image）在多阶段推理时的错误，确保了模型服务的可用性。
    - **修复Flux2klein文本输入处理**：修复了文本输入处理问题，保证了特定图像生成模型的正确运行。
    - **修复FLUX.1-dev的T5文本编码器**：确保了FLUX.1-dev模型能正确渲染文本，这是图像生成模型的核心功能。

- **清理与重构，提升项目健康度**:
    - **移除冗余基准测试和配置**：从Qwen3-Omni中移除冗余基准测试，并删除了不再需要的 `bagel yaml` 配置文件。这有助于保持代码库的整洁和可维护性。
    - **配置默认优先级重构**：重构了 `sentinel` 配置的默认优先级，使配置管理更清晰、更符合预期。

- **完善文档**:
    - **更新TTS模型添加指南**：更新了添加TTS模型的技能指南和贡献指南，引入了单阶段模式。这降低了社区贡献者的参与门槛，有助于项目生态发展。
    - **修改性能分析文档**：更新了性能分析文档，帮助用户更好地理解和优化模型性能。

#### 3. 对项目的影响和潜在意义

- **提升项目成熟度**：大量的Bug修复和性能优化（如优雅关闭、Coordinator优化）表明项目正从功能原型向稳定、可靠的生产级服务演进。
- **扩展应用场景**：流式视频输入和TTS基准测试的加入，使得项目能够支持更丰富的应用场景，如实时视频会议、语音助手、内容生成等。
- **降低使用门槛**：对MUSA等非NVIDIA硬件的支持，以及文档的完善，都直接降低了用户的使用和贡献门槛，有助于吸引更广泛的用户和开发者社区。
- **巩固技术基础**：通过重构和清理冗余，项目的代码质量和架构清晰度得到提升，为未来更复杂的功能开发奠定了更坚实的基础。

#### 4. 值得关注的技术点

- **流式视频处理**：`EVS帧过滤` 是一个值得关注的技术点。它可能是一种高效的视频帧选择策略，用于在保证服务质量的同时，减少计算和带宽开销。这可能是项目在视频处理上的一个创新点。
- **多阶段引擎的优雅关闭**：`graceful shutdown for multi-stage engine processes` 是一个重要的系统工程问题。其实现方式（如信号处理、资源清理）对于保障服务的高可用性至关重要。
- **`torch.accelerator` 支持**：这是PyTorch生态中一个重要的抽象层，旨在统一不同硬件加速器的后端。vllm-omni对其的支持，表明其架构设计具有前瞻性，易于适配未来新的硬件。

#### 5. 对项目发展的影响

结合README中“**Easy, fast, and cheap omni-modality model serving for everyone**”的愿景，这些提交清晰地展示了项目的发展路径：

- **从“核心”到“全面”**：项目最初可能聚焦于文本和图像，现在正积极向语音（TTS）和视频（流式输入）扩展，逐步兑现“全模态”的承诺。
- **从“能用”到“好用”**：大量的Bug修复、性能优化、配置重构和文档更新，都是在将项目从“能跑通模型”的阶段，推向“稳定、高效、易于部署和使用”的生产级阶段。
- **拥抱开放生态**：支持MUSA等

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
