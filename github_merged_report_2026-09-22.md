# GitHub Stars 合并报告 - 2026-09-22

**合并日期**: 2026-09-23
**监控日期**: 2026-09-22
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


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2222
- **最后更新**: 2026-09-22T13:07:55Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: ruchu127

## AI分析总结

**1. 主要更新类型**
   * **功能新增与文档更新**：本次提交为项目新增了一个名为“可复用文档审计技能”的自动化工具或流程，并配套更新了相关文档。

**2. 关键变更点及其与项目整体方向的关系**
   * **关键变更**：在项目中引入了一个智能代理（agent）驱动的文档审计技能。此技能旨在自动化检查项目文档的质量、一致性和规范性。
   * **与项目方向的关系**：VeOmni作为一个开源的分布式训练框架，其文档（如API文档、使用指南、贡献指南等）的清晰度、准确性和一致性至关重要，直接影响开发者体验和社区贡献效率。该提交直接服务于提升项目文档的标准化和可维护性这一基础设施目标，是支撑项目长期发展和社区健康度的重要一环。

**3. 对项目的影响和潜在意义**
   * **直接影响**：提供了文档质量的自动化守门员，有助于在提交或发布前及时发现并修正文档中的错误、不一致或过时内容。
   * **潜在意义**：
     * **降低维护成本**：减少了人工审阅文档的工作量，使维护者能更专注于核心功能开发。
     * **提升项目专业性**：确保对外文档始终保持高质量，增强项目的专业形象和可信度。
     * **促进社区协作**：为贡献者提供了明确的文档规范，并通过自动化反馈降低了参与贡献的门槛。

**4. 值得关注的技术点**
   * **智能代理（Agent）集成**：提交信息中提及“agent”，表明此审计技能可能具备一定的自主判断或上下文理解能力，而不仅仅是基于静态规则的检查，代表了工程实践中利用AI提升开发运维效率的趋势。
   * **技能的“可复用”设计**：强调“reusable”，意味着该文档审计逻辑被设计为模块化、可配置，未来可能易于扩展到其他类型的文档或被其他项目复用。

**5. 基于项目背景对项目发展的影响**
   VeOmni旨在通过提供一个“模型为中心的分布式食谱库”来赋能任何模态模型的训练。要维持这样一个开放、活跃的社区和复杂的代码库，高质量的文档是确保**可发现性**、**可用性**和**可贡献性**的基石。
   本次提交通过引入自动化文档审计，**强化了项目的工程化实践和可持续发展能力**。它确保了随着项目功能不断扩展，其文档也能同步演进并保持质量，从而保障开发者能够准确、高效地利用VeOmni的框架和功能，最终**降低用户的使用门槛，促进项目生态的繁荣**。这是一个从“功能实现”向“工程卓越”迈进的关键步骤。

## 详细提交记录

### [49cc654](https://github.com/ByteDance-Seed/VeOmni/commit/49cc654afa22168d28b6e02df23c6aebae15d3fb)

- **作者**: ruchu127
- **时间**: 2026-09-22T10:12:42Z
- **提交信息**: [agent, docs] feat: add reusable documentation audit skill (#1157)

Co-authored-by: ruchu127 <319100715+ruchu127@users.noreply.github.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2850
- **最后更新**: 2026-09-22T22:01:31Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Yang Yong (雍洋)

## AI分析总结

基于提供的项目背景（LightX2V为一个轻量级视频生成推理框架）和提交记录，现总结分析如下：

**1. 主要更新类型**
*   **文档更新**：两笔提交均明确为对项目主README文件的更新。

**2. 关键变更点及其与项目整体方向的关系**
*   **关键变更点**：核心变更为在项目首页README中添加或完善了`Ask DeepWiki`（AI文档助手）和`Doc`（官方文档）的徽章与链接。
*   **与项目方向的关系**：此举直接服务于项目“易用性”和“开发者友好”的核心目标。通过集成外部AI问答入口（DeepWiki）和明确指向详细文档的链接，显著降低了新用户理解和使用该框架的门槛，是完善项目基础设施的关键一步。

**3. 对项目的影响和潜在意义**
*   **影响**：提升了项目的专业形象和用户体验，使信息获取路径更加清晰、直接。
*   **潜在意义**：有利于吸引和留住开发者用户，通过降低文档查询难度，可以加速框架的传播和社区采纳，为后续的功能迭代和社区贡献打下基础。

**4. 值得关注的技术点**
*   本次提交本身不涉及代码逻辑或算法变更，因此无直接的技术实现点。其价值主要体现在**项目管理与社区工程**层面，反映了维护者对项目可访问性和用户体验的重视。

**5. 对项目发展的影响（结合README背景）**
*   项目README是开发者接触框架的**第一窗口**。本次更新优化了这一窗口，提供了更强大的信息获取工具（DeepWiki）和官方知识库入口。这对于一个旨在简化视频生成模型部署和推理的框架至关重要，因为它能有效帮助用户快速解决问题，减少初期使用障碍，从而推动框架从“可用”向“易用”和“好用”演进，符合其“轻量”与“便捷”的长期发展方向。

## 详细提交记录

### [1013f83](https://github.com/ModelTC/LightX2V/commit/1013f83fca0d7cdf52efd66d2dba98fcf565f816)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-22T10:13:08Z
- **提交信息**: update readme (#1552)

### [c2527aa](https://github.com/ModelTC/LightX2V/commit/c2527aaaebb91dd8f7d3f944f2d2d6f2f31206e0)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-22T10:07:06Z
- **提交信息**: update readme (#1551)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2255
- **最后更新**: 2026-09-22T13:06:43Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

基于提供的提交记录和项目README摘要，现对VideoX-Fun仓库昨日更新分析如下：

**1. 主要更新类型**
本次更新包含**功能新增**与**文档更新**两大类型。核心提交(#511)集中于扩展项目对新模型与新功能的支持，属于重要的功能迭代；而#517则是配套的文档维护。

**2. 关键变更点及其与项目整体方向的关系**
*   **多模型与新架构支持**：新增了对`Qwen-Image2.1`（图像生成）、`Wan2.2`（视频生成）及其配套`2.2VAE`的支持。这直接响应了项目README中展示的、作为多模态生成（CogVideoX-Fun, Wan-Fun）综合平台的目标，通过集成更多前沿模型来丰富工具链。
*   **控制能力增强**：新增了`Minimax-H3`的新控制支持。这强化了项目在可控视频生成领域的核心能力，与README中强调的“Fun”（即创意与可控）方向一致。
*   **开发体验优化**：统一更新了所有训练代码的`tqdm`进度条，属于对开发者工作流的优化与重构。

**3. 对项目的影响和潜在意义**
*   **直接影响**：项目功能边界显著扩大，能够支持生成更多类型和更高质量的视觉内容，为用户和开发者提供了更强大的工具选择。
*   **潜在意义**：通过积极跟进和集成如`Wan2.2`等新版本模型，表明项目处于活跃维护状态，技术栈保持更新。这有助于提升项目在开源AIGC社区中的吸引力与竞争力，巩固其作为视频生成“瑞士军刀”的地位。

**4. 值得关注的技术点**
*   **新模型集成**：`Qwen-Image2.1`与`Wan2.2/2.2VAE`的集成，可能涉及模型接口适配、推理流程优化以及与现有功能的融合，是技术实现的重点。
*   **训练代码重构**：对所有训练代码的更新，旨在统一开发规范、提升代码可维护性，这对于一个长期演进的多模型平台至关重要。

**5. 基于项目背景的提交影响分析**
README表明VideoX-Fun是一个致力于提供多样化、易用的视频生成与编辑工具的开源项目。此次提交完美契合了这一愿景：**功能更新**直接增强了项目“工具箱”的丰富度和先进性，使其能支持更现代、更专业的生成任务；**文档更新**则确保了新用户和贡献者能够获取准确的信息。两者结合，共同推动了项目向更强大、更易用、更开放的综合AIGC应用平台发展。

## 详细提交记录

### [bce42b3](https://github.com/aigc-apps/VideoX-Fun/commit/bce42b301f59af70f543ac964792e45954c36b2b)

- **作者**: Bubbliiiing
- **时间**: 2026-09-22T13:06:38Z
- **提交信息**: Update Readme (#517)

### [2beb171](https://github.com/aigc-apps/VideoX-Fun/commit/2beb171099e932faf95030b604fb44e04e961276)

- **作者**: Bubbliiiing
- **时间**: 2026-09-22T12:41:39Z
- **提交信息**: Support Qwen-Image2.1 && Support new Control for Minimax-H3 && Support Wan2.2 with 2.2VAE && Update new tqdm for All Training Code (#511)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6484
- **最后更新**: 2026-09-23T00:27:39Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 10
- **主要提交者**: Jonathan Dierksen, CarstyYou, Brian K. Ryu

## AI分析总结

根据仓库 `flashinfer-ai/flashinfer` 昨日的 14 个提交，合并分析如下：

**主要更新与关键变更**

本次更新主要聚焦于**扩展 MoE 模型支持、适配最新 GPU 架构**，并持续**优化核心性能与可靠性**。具体包括：
1.  **MoE 支持全面增强**：新增了对 **FP8、MXFP8/MXFP4** 等计算精度的支持，并为 **Blackwell (SM120/121)** 架构引入了专属的 MoE 内核与注意力机制。同时，实现了 **CUDA 图** 的初步集成，提升了执行效率。
2.  **新硬件架构适配**：为 **SM100/SM103 (B200/B300)** 架构添加了稀疏注意力内核，确保项目能利用最新硬件的计算能力。
3.  **核心性能优化**：
    *   **数据布局优化**：为 MoE 的 GEMM2 操作设计了“专家排序缓冲区”，优化了大批次下的显存访问模式，解决了 gather 操作导致的带宽浪费问题。
    *   **主机端调度优化**：重构了 `plan()` 函数，将 Python 循环替换为高效的 `Tensor.max()` 运算，使高并发下的调度耗时降低一个数量级，显著提升端到端吞吐。
4.  **正确性与可靠性修复**：
    *   修复了分组 GEMM 内核在特定边界条件下的**越界读取**问题，通过智能索引钳制确保安全。
    *   修复了内联汇编函数 `ld_shared` 缺失的 `has_side_effects` 声明，防止编译器错误优化，保障了底层计算的正确性。
5.  **模型与场景支持**：新增了针对 **Qwen3.5-35B-A3B** 模型在特定配置（TP=2，7个草稿token）下的专用解码内核，展示了为具体部署场景进行细粒度调优的能力。

**对项目的影响与意义**

*   **提升技术竞争力与适用范围**：对 MoE 和新硬件的全面支持，使 FlashInfer 能更好地服务下一代大模型推理。FP8 等量化精度的完善和 CUDA 图的引入，拓宽了其在不同部署场景（精度-吞吐权衡、高并发低延迟）下的适用性。
*   **深化性能与稳定性**：从主机调度到设备内核的多层次性能优化，直接提升了推理效率。关键 Bug 的修复增强了项目，特别是涉及底层优化代码时的可靠性，巩固了其作为生产级推理基座的稳健性。
*   **推动项目向更全面的推理基座演进**：这些变更共同推动了 FlashInfer 从一个强大的注意力内核库，向一个能更高效、更稳定地支持复杂模型结构（如 MoE）和前沿硬件的**全面 GPU 推理基座**演进。

**值得关注的技术点**

1.  **通过数据布局优化计算**：为 MoE 准备专家局部连续的中间数据，是典型的应用驱动内存布局优化以提升计算效率的案例。
2.  **异构计算优化思路**：将主机端的简单循环逻辑迁移为设备端的向量化操作，是降低异构系统开销的典范。
3.  **CUDA 图的状态管理**：设计 `MoEEpSplitGraphState` 来管理捕获与重放过程中的资源，体现了对 CUDA 图复杂生命周期的精细把控。
4.  **内核与编译器的交互**：正确使用 `has_side_effects` 等标记与 LLVM 编译器交互，是编写可靠底层内核的关键实践。
5.  **内核的特定化调优**：为特定模型、并行策略和算法参数生成专用内核并通过选择器自动路由，展示了在追求极致性能时进行细粒度定制的工程能力。

## 详细提交记录

### [b761ac6](https://github.com/flashinfer-ai/flashinfer/commit/b761ac61558e8c83961eeeb213fa94ad9652dfe8)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-22T23:52:48Z
- **提交信息**: feat(moe): add cuTile FP8 and MXFP8 precision support (#5332)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

This PR adds five cuTile fused-MoE precision combinations across all
unified-MoE activations:

- Per-tensor FP8 weights with BF16 or per-tensor FP8 activations.
- MXFP8 weights with BF16 or MXFP8 activations.
- MXFP4 weights with MXFP8 activations.
- Dynamically quantized A8 execution, fused and persistent execution
modes, staged GEMM autotuning, and bounded token-shape compilation for
serving workloads.
- Tighten shared cuTile routing workspace and launch geometry so empty
experts do not incur padding blocks; this affects the existing BF16/FP4
paths as well as the new FP8 paths.
- Unified-MoE benchmark, documentation, and correctness coverage.

| Weight format | Activation format | SM89 | SM90 | SM120 | SM121 |
|---|---|:---:|:---:|:---:|:---:|
| FP8 per tensor | BF16 | ✓ | ✓ | ✓ | ✓ |
| FP8 per tensor | FP8 per tensor |  | ✓ | ✓ | ✓ |
| MXFP8 | BF16 | ✓ | ✓ | ✓ | ✓ |
| MXFP8 | MXFP8 |  |  | ✓ | ✓ |
| MXFP4 | MXFP8 |  |  | ✓ | ✓ |

The five configurations are included in the default backend search.
Consequently, `backend="auto"` may autotune and select cuTile for
existing per-tensor-FP8 and MXFP8 workloads when the precision pair and
architecture are supported.

### Performance Numbers

All times are inclusive median latency in microseconds with both
backends autotuned, cold L2, one invocation per CUDA-graph replay, and
reference checking enabled. Qwen uses SwiGLU with H=2048, I=512, E=256,
top-k=8; Nemotron uses ReLU2 with H=2688, I=1856, E=128, top-k=6.

Speedup is shown only for directly compatible precision and shape
comparisons and is `CUTLASS / cuTile`. Proxy comparisons report raw
latency without a speedup ratio.

<details>
<summary><strong>L40S (SM89)</strong></summary>

### FP8PerTensor × BF16

Comparator: CUTLASS BF16 × BF16 proxy.

| Model | Tokens | cuTile (µs) | CUTLASS proxy (µs) |
|---|---:|---:|---:|
| Qwen | 1 | 102.8 | 121.1 |
| Qwen | 2 | 145.2 | 219.8 |
| Qwen | 4 | 269.4 | 413.2 |
| Qwen | 8 | 459.0 | 706.4 |
| Qwen | 16 | 820.4 | 1265.5 |
| Qwen | 32 | 1498.6 | 2380.5 |
| Qwen | 64 | 1528.0 | 2395.9 |
| Qwen | 128 | 1523.2 | 2412.5 |
| Qwen | 256 | 1559.0 | 2449.3 |
| Qwen | 512 | 1595.9 | 2518.9 |
| Qwen | 1024 | 1685.2 | 2739.8 |
| Qwen | 2048 | 3036.7 | 2947.7 |
| Qwen | 4096 | 5321.2 | 3368.4 |
| Qwen | 8192 | 10489.5 | 4529.0 |
| Nemotron | 1 | 173.7 | 261.0 |
| Nemotron | 2 | 340.1 | 494.1 |
| Nemotron | 4 | 550.7 | 840.2 |
| Nemotron | 8 | 946.6 | 1526.3 |
| Nemotron | 16 | 1744.2 | 2894.1 |
| Nemotron | 32 | 2289.3 | 3817.8 |
| Nemotron | 64 | 2301.2 | 3837.5 |
| Nemotron | 128 | 2316.6 | 3870.6 |
| Nemotron | 256 | 2347.4 | 3929.5 |
| Nemotron | 512 | 2389.4 | 4032.1 |
| Nemotron | 1024 | 7219.7 | 4196.5 |
| Nemotron | 2048 | 10593.4 | 4417.7 |
| Nemotron | 4096 | 21586.6 | 5021.7 |
| Nemotron | 8192 | 25969.9 | 6709.7 |

### MXFP8 × BF16

Comparator: CUTLASS BF16 × BF16 proxy.

| Model | Tokens | cuTile (µs) | CUTLASS proxy (µs) |
|---|---:|---:|---:|
| Qwen | 1 | 114.5 | 121.1 |
| Qwen | 2 | 154.0 | 219.8 |
| Qwen | 4 | 283.1 | 413.2 |
| Qwen | 8 | 484.2 | 706.4 |
| Qwen | 16 | 852.6 | 1265.5 |
| Qwen | 32 | 1567.6 | 2380.5 |
| Qwen | 64 | 1571.5 | 2395.9 |
| Qwen | 128 | 1588.7 | 2412.5 |
| Qwen | 256 | 1616.4 | 2449.3 |
| Qwen | 512 | 1661.3 | 2518.9 |
| Qwen | 1024 | 1763.0 | 2739.8 |
| Qwen | 2048 | 3073.1 | 2947.7 |
| Qwen | 4096 | 5333.9 | 3368.4 |
| Qwen | 8192 | 10491.1 | 4529.0 |
| Nemotron | 1 | 225.2 | 261.0 |
| Nemotron | 2 | 434.0 | 494.1 |
| Nemotron | 4 | 676.5 | 840.2 |
| Nemotron | 8 | 1125.0 | 1526.3 |
| Nemotron | 16 | 2052.7 | 2894.1 |
| Nemotron | 32 | 2703.3 | 3817.8 |
| Nemotron | 64 | 2713.4 | 3837.5 |
| Nemotron | 128 | 2731.2 | 3870.6 |
| Nemotron | 256 | 2769.4 | 3929.5 |
| Nemotron | 512 | 2826.2 | 4032.1 |
| Nemotron | 1024 | 4472.2 | 4196.5 |
| Nemotron | 2048 | 6682.1 | 4417.7 |
| Nemotron | 4096 | 13972.6 | 5021.7 |
| Nemotron | 8192 | 27167.4 | 6709.7 |

</details>

<details>
<summary><strong>H100 (SM90)</strong></summary>

### FP8PerTensor × BF16

Comparator: CUTLASS BF16 × BF16 proxy.

| Model | Tokens | cuTile (µs) | CUTLASS proxy (µs) |
|---|---:|---:|---:|
| Qwen | 1 | 35.3 | 54.8 |
| Qwen | 2 | 42.9 | 65.7 |
| Qwen | 4 | 72.4 | 95.4 |
| Qwen | 8 | 115.0 | 150.3 |
| Qwen | 16 | 194.4 | 259.6 |
| Qwen | 32 | 353.6 | 473.6 |
| Qwen | 64 | 358.2 | 476.7 |
| Qwen | 128 | 378.2 | 483.1 |
| Qwen | 256 | 390.6 | 489.5 |
| Qwen | 512 | 411.5 | 506.4 |
| Qwen | 1024 | 529.7 | 586.1 |
| Qwen | 2048 | 691.3 | 717.8 |
| Qwen | 4096 | 1202.8 | 908.8 |
| Qwen | 8192 | 2219.8 | 1553.2 |
| Nemotron | 1 | 42.2 | 73.7 |
| Nemotron | 2 | 70.5 | 106.1 |
| Nemotron | 4 | 123.2 | 175.4 |
| Nemotron | 8 | 216.3 | 304.5 |
| Nemotron | 16 | 399.9 | 577.0 |
| Nemotron | 32 | 525.6 | 752.9 |
| Nemotron | 64 | 538.1 | 759.7 |
| Nemotron | 128 | 545.5 | 762.6 |
| Nemotron | 256 | 565.2 | 783.7 |
| Nemotron | 512 | 709.7 | 809.4 |
| Nemotron | 1024 | 920.2 | 935.6 |
| Nemotron | 2048 | 1670.7 | 1169.9 |
| Nemotron | 4096 | 2513.2 | 1750.8 |
| Nemotron | 8192 | 5294.9 | 3064.5 |

### FP8PerTensor × FP8PerTensor

Comparator: CUTLASS FP8PerTensor × FP8PerTensor (exact).

| Model | Tokens | cuTile (µs) | CUTLASS (µs) | Speedup |
|---|---:|---:|---:|---:|
| Qwen | 1 | 55.4 | 72.5 | 1.31× |
| Qwen | 2 | 58.5 | 80.3 | 1.37× |
| Qwen | 4 | 86.0 | 99.7 | 1.16× |
| Qwen | 8 | 127.9 | 135.6 | 1.06× |
| Qwen | 16 | 203.8 | 194.8 | 0.96× |
| Qwen | 32 | 350.4 | 315.7 | 0.90× |
| Qwen | 64 | 354.4 | 324.3 | 0.92× |
| Qwen | 128 | 380.2 | 326.2 | 0.86× |
| Qwen | 256 | 385.6 | 339.5 | 0.88× |
| Qwen | 512 | 405.1 | 354.9 | 0.88× |
| Qwen | 1024 | 554.7 | 417.7 | 0.75× |
| Qwen | 2048 | 575.4 | 521.7 | 0.91× |
| Qwen | 4096 | 875.8 | 719.9 | 0.82× |
| Qwen | 8192 | 1471.1 | 1301.6 | 0.88× |
| Nemotron | 1 | 64.4 | 81.2 | 1.26× |
| Nemotron | 2 | 86.2 | 102.2 | 1.19× |
| Nemotron | 4 | 137.1 | 140.2 | 1.02× |
| Nemotron | 8 | 232.6 | 206.4 | 0.89× |
| Nemotron | 16 | 391.9 | 342.5 | 0.87× |
| Nemotron | 32 | 505.7 | 438.2 | 0.87× |
| Nemotron | 64 | 510.9 | 438.6 | 0.86× |
| Nemotron | 128 | 525.3 | 449.3 | 0.86× |
| Nemotron | 256 | 535.9 | 459.2 | 0.86× |
| Nemotron | 512 | 708.2 | 482.3 | 0.68× |
| Nemotron | 1024 | 689.9 | 574.8 | 0.83× |
| Nemotron | 2048 | 963.7 | 756.7 | 0.79× |
| Nemotron | 4096 | 1366.5 | 1277.0 | 0.93× |
| Nemotron | 8192 | 2947.8 | 2166.1 | 0.73× |

### MXFP8 × BF16

Comparator: CUTLASS BF16 × BF16 proxy.

| Model | Tokens | cuTile (µs) | CUTLASS proxy (µs) |
|---|---:|---:|---:|
| Qwen | 1 | 42.0 | 54.8 |
| Qwen | 2 | 48.9 | 65.7 |
| Qwen | 4 | 77.5 | 95.4 |
| Qwen | 8 | 128.7 | 150.3 |
| Qwen | 16 | 222.5 | 259.6 |
| Qwen | 32 | 416.4 | 473.6 |
| Qwen | 64 | 419.0 | 476.7 |
| Qwen | 128 | 420.9 | 483.1 |
| Qwen | 256 | 440.9 | 489.5 |
| Qwen | 512 | 462.3 | 506.4 |
| Qwen | 1024 | 534.5 | 586.1 |
| Qwen | 2048 | 733.2 | 717.8 |
| Qwen | 4096 | 1245.8 | 908.8 |
| Qwen | 8192 | 2298.9 | 1553.2 |
| Nemotron | 1 | 49.5 | 73.7 |
| Nemotron | 2 | 79.0 | 106.1 |
| Nemotron | 4 | 140.7 | 175.4 |
| Nemotron | 8 | 248.6 | 304.5 |
| Nemotron | 16 | 462.8 | 577.0 |
| Nemotron | 32 | 616.9 | 752.9 |
| Nemotron | 64 | 620.8 | 759.7 |
| Nemotron | 128 | 632.6 | 762.6 |
| Nemotron | 256 | 645.4 | 783.7 |
| Nemotron | 512 | 762.2 | 809.4 |
| Nemotron | 1024 | 1007.4 | 935.6 |
| Nemotron | 2048 | 1870.5 | 1169.9 |
| Nemotron | 4096 | 3113.5 | 1750.8 |
| Nemotron | 8192 | 5949.3 | 3064.5 |

</details>

<details>
<summary><strong>RTX PRO 6000 (SM120)</strong></summary>

### FP8PerTensor × BF16

Comparator: CUTLASS BF16 × BF16 proxy.

| Model | Tokens | cuTile (µs) | CUTLASS proxy (µs) |
|---|---:|---:|---:|
| Qwen | 1 | 42.8 | 72.1 |
| Qwen | 2 | 67.3 | 116.1 |
| Qwen | 4 | 116.5 | 206.3 |
| Qwen | 8 | 208.1 | 346.8 |
| Qwen | 16 | 363.8 | 608.4 |
| Qwen | 32 | 667.3 | 1134.2 |
| Qwen | 64 | 668.8 | 1137.7 |
| Qwen | 128 | 682.1 | 1146.6 |
| Qwen | 256 | 693.3 | 1157.9 |
| Qwen | 512 | 715.5 | 1188.4 |
| Qwen | 1024 | 749.7 | 1239.4 |
| Qwen | 2048 | 873.2 | 1343.7 |
| Qwen | 4096 | 1472.8 | 1571.8 |
| Qwen | 8192 | 2584.9 | 2191.4 |
| Nemotron | 1 | 74.6 | 134.4 |
| Nemotron | 2 | 131.9 | 242.0 |
| Nemotron | 4 | 237.3 | 400.4 |
| Nemotron | 8 | 408.2 | 714.8 |
| Nemotron | 16 | 752.3 | 1344.8 |
| Nemotron | 32 | 980.8 | 1771.4 |
| Nemotron | 64 | 983.8 | 1776.0 |
| Nemotron | 128 | 1006.2 | 1787.7 |
| Nemotron | 256 | 1005.1 | 1808.6 |
| Nemotron | 512 | 1022.0 | 1846.2 |
| Nemotron | 1024 | 1113.5 | 1909.8 |
| Nemotron | 2048 | 1374.2 | 2050.6 |
| Nemotron | 4096 | 2822.6 | 2357.0 |
| Nemotron | 8192 | 6996.3 | 3353.7 |

### FP8PerTensor × FP8PerTensor

Comparator: CUTLASS FP8PerTensor × FP8PerTensor (exact).

| Model | Tokens | cuTile (µs) | CUTLASS (µs) | Speedup |
|---|---:|---:|---:|---:|
| Qwen | 1 | 55.9 | 73.0 | 1.31× |
| Qwen | 2 | 80.2 | 95.3 | 1.19× |
| Qwen | 4 | 129.0 | 141.8 | 1.10× |
| Qwen | 8 | 219.4 | 233.1 | 1.06× |
| Qwen | 16 | 374.8 | 372.1 | 0.99× |
| Qwen | 32 | 641.6 | 641.2 | 1.00× |
| Qwen | 64 | 642.8 | 645.7 | 1.00× |
| Qwen | 128 | 652.1 | 650.9 | 1.00× |
| Qwen | 256 | 663.9 | 657.1 | 0.99× |
| Qwen | 512 | 689.3 | 673.9 | 0.98× |
| Qwen | 1024 | 722.9 | 725.2 | 1.00× |
| Qwen | 2048 | 844.8 | 832.5 | 0.99× |
| Qwen | 4096 | 1218.8 | 1084.1 | 0.89× |
| Qwen | 8192 | 1914.4 | 1716.2 | 0.90× |
| Nemotron | 1 | 85.7 | 104.2 | 1.22× |
| Nemotron | 2 | 142.1 | 158.8 | 1.12× |
| Nemotron | 4 | 245.9 | 261.2 | 1.06× |
| Nemotron | 8 | 417.2 | 423.9 | 1.02× |
| Nemotron | 16 | 755.8 | 740.8 | 0.98× |
| Nemotron | 32 | 980.4 | 967.3 | 0.99× |
| Nemotron | 64 | 997.0 | 968.6 | 0.97× |
| Nemotron | 128 | 994.0 | 968.2 | 0.97× |
| Nemotron | 256 | 1006.2 | 982.3 | 0.98× |
| Nemotron | 512 | 1025.5 | 1017.7 | 0.99× |
| Nemotron | 1024 | 1089.1 | 1083.8 | 1.00× |
| Nemotron | 2048 | 1252.1 | 1218.5 | 0.97× |
| Nemotron | 4096 | 1765.2 | 1546.7 | 0.88× |
| Nemotron | 8192 | 3028.8 | 2722.7 | 0.90× |

### MXFP8 × BF16

Comparator: CUTLASS BF16 × BF16 proxy.

| Model | Tokens | cuTile (µs) | CUTLASS proxy (µs) |
|---|---:|---:|---:|
| Qwen | 1 | 44.1 | 72.1 |
| Qwen | 2 | 69.5 | 116.1 |
| Qwen | 4 | 118.4 | 206.3 |
| Qwen | 8 | 211.8 | 346.8 |
| Qwen | 16 | 372.5 | 608.4 |
| Qwen | 32 | 677.2 | 1134.2 |
| Qwen | 64 | 681.2 | 1137.7 |
| Qwen | 128 | 688.3 | 1146.6 |
| Qwen | 256 | 701.8 | 1157.9 |
| Qwen | 512 | 726.9 | 1188.4 |
| Qwen | 1024 | 764.8 | 1239.4 |
| Qwen | 2048 | 895.2 | 1343.7 |
| Qwen | 4096 | 1517.4 | 1571.8 |
| Qwen | 8192 | 2567.9 | 2191.4 |
| Nemotron | 1 | 80.0 | 134.4 |
| Nemotron | 2 | 139.0 | 242.0 |
| Nemotron | 4 | 242.7 | 400.4 |
| Nemotron | 8 | 422.7 | 714.8 |
| Nemotron | 16 | 777.2 | 1344.8 |
| Nemotron | 32 | 1013.8 | 1771.4 |
| Nemotron | 64 | 1030.9 | 1776.0 |
| Nemotron | 128 | 1028.2 | 1787.7 |
| Nemotron | 256 | 1041.8 | 1808.6 |
| Nemotron | 512 | 1060.6 | 1846.2 |
| Nemotron | 1024 | 1201.2 | 1909.8 |
| Nemotron | 2048 | 1551.7 | 2050.6 |
| Nemotron | 4096 | 3036.3 | 2357.0 |
| Nemotron | 8192 | 4751.4 | 3353.7 |

### MXFP8 × MXFP8

Comparator: CUTLASS FP8PerTensor × FP8PerTensor proxy.

| Model | Tokens | cuTile (µs) | CUTLASS proxy (µs) |
|---|---:|---:|---:|
| Qwen | 1 | 51.4 | 73.0 |
| Qwen | 2 | 81.1 | 95.3 |
| Qwen | 4 | 129.3 | 141.8 |
| Qwen | 8 | 219.8 | 233.1 |
| Qwen | 16 | 376.4 | 372.1 |
| Qwen | 32 | 652.2 | 641.2 |
| Qwen | 64 | 660.2 | 645.7 |
| Qwen | 128 | 667.5 | 650.9 |
| Qwen | 256 | 679.4 | 657.1 |
| Qwen | 512 | 702.7 | 673.9 |
| Qwen | 1024 | 735.2 | 725.2 |
| Qwen | 2048 | 840.8 | 832.5 |
| Qwen | 4096 | 1239.1 | 1084.1 |
| Qwen | 8192 | 2165.1 | 1716.2 |
| Nemotron | 1 | 92.3 | 104.2 |
| Nemotron | 2 | 149.5 | 158.8 |
| Nemotron | 4 | 252.0 | 261.2 |
| Nemotron | 8 | 431.7 | 423.9 |
| Nemotron | 16 | 786.7 | 740.8 |
| Nemotron | 32 | 1021.4 | 967.3 |
| Nemotron | 64 | 1040.9 | 968.6 |
| Nemotron | 128 | 1034.4 | 968.2 |
| Nemotron | 256 | 1048.9 | 982.3 |
| Nemotron | 512 | 1075.5 | 1017.7 |
| Nemotron | 1024 | 1158.5 | 1083.8 |
| Nemotron | 2048 | 1324.9 | 1218.5 |
| Nemotron | 4096 | 1979.4 | 1546.7 |
| Nemotron | 8192 | 4094.7 | 2722.7 |

### MXFP4 × MXFP8

Comparator: CUTLASS MXFP4 × MXFP8.

#### Qwen — direct comparison

| Tokens | cuTile (µs) | CUTLASS (µs) | Speedup |
|---:|---:|---:|---:|
| 1 | 40.7 | 50.5 | 1.24× |
| 2 | 55.8 | 60.8 | 1.09× |
| 4 | 83.2 | 85.5 | 1.03× |
| 8 | 132.8 | 135.0 | 1.02× |
| 16 | 228.1 | 235.4 | 1.03× |
| 32 | 391.8 | 384.3 | 0.98× |
| 64 | 394.0 | 386.5 | 0.98× |
| 128 | 408.1 | 389.8 | 0.96× |
| 256 | 413.9 | 394.4 | 0.95× |
| 512 | 438.2 | 414.5 | 0.95× |
| 1024 | 498.6 | 439.3 | 0.88× |
| 2048 | 630.8 | 527.6 | 0.84× |
| 4096 | 1053.1 | 691.6 | 0.66× |
| 8192 | 1912.7 | 1171.3 | 0.61× |

#### Nemotron — aligned-shape proxy

| Tokens | cuTile I=1856 (µs) | CUTLASS I=1920 proxy (µs) |
|---:|---:|---:|
| 1 | 57.5 | 65.5 |
| 2 | 88.3 | 95.2 |
| 4 | 154.8 | 157.5 |
| 8 | 262.7 | 264.6 |
| 16 | 445.6 | 442.2 |
| 32 | 571.5 | 562.5 |
| 64 | 578.8 | 566.9 |
| 128 | 580.3 | 569.6 |
| 256 | 595.6 | 586.1 |
| 512 | 640.7 | 606.6 |
| 1024 | 761.8 | 657.5 |
| 2048 | 1058.9 | 794.5 |
| 4096 | 1683.6 | 1153.1 |
| 8192 | 3423.0 | 2020.1 |

</details>

## 🔍 Related Issues

<!-- Link any related issues here -->

Progress towards #4857

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

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added cuTile FP8, MXFP8, and mixed MXFP4/MXFP8 support for
Mixture-of-Experts workloads.
- Added BF16 and quantized activation combinations, CUDA Graph
preparation, and expanded autotuning.
- Added benchmark variants and reporting for prequantized and
runtime-quantized timings.

- **Documentation**
- Expanded API, design, and benchmark documentation with quantization
modes, hardware requirements, and usage details.

- **Tests**
- Expanded coverage for quantization, routing, precision, CUDA Graphs,
validation, and unified-layer execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7f59dc9](https://github.com/flashinfer-ai/flashinfer/commit/7f59dc945c5dc069fe721dc5c42ca4ebf1eb1abb)

- **作者**: Adrian
- **时间**: 2026-09-22T22:25:37Z
- **提交信息**: test: prune sampling parameter matrix (#5428)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/utils/test_sampling.py` to `parametrize_product`. Regular pytest
runs use deterministic pairwise coverage, while `pytest --full` retains
the exhaustive matrices for nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Repository commit hooks passed for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

### [48c29d2](https://github.com/flashinfer-ai/flashinfer/commit/48c29d2efaf70d53c61054b28ba67b8392ee37fa)

- **作者**: CarstyYou
- **时间**: 2026-09-22T21:05:51Z
- **提交信息**: feat(moe): add SM12x (SM120/SM121) fp8 + mxfp8_mxfp4 grouped-MoE kernels (#4720)

## Summary

Ports 8 CuTe-DSL grouped-MoE ops for Blackwell SM120/SM121 into
`blackwell_sm12x`, covering both currently supported precisions:

- `cute_dsl_sm12x_moe_gemm_{fp8,mxfp8_mxfp4}`
- `cute_dsl_sm12x_fc1_act_{fp8,mxfp8_mxfp4}` (gate-up GEMM fused with
SwiGLU/SiTU-GLU)
- `cute_dsl_sm12x_fc1_act_q1_{fp8,mxfp8_mxfp4}` (fc1_act with fused
fp8/mxfp8 requantize for fc2)
- `cute_dsl_sm12x_fc2_finalize_{fp8,mxfp8_mxfp4}` (down-projection GEMM
fused with routing-weighted token finalize)

All 8 are exported through the public `flashinfer.fused_moe` namespace.

<!-- sm12x-5kp-benchmark-figures:start -->
## 5kp Benchmark Figures

Data source: `dsv4_5kp_sweep_wrapperopt_cooldown100ms.csv` (sha256:
`820cef55cc0739324ccbd79bdb5198ede1beda5fc7d8d5655e55e488a443e111`).
Plotted TP: 1/2/4. Latency metric: `median_us`; speedup metric:
`(DeepGEMM median / FlashInfer median - 1) * 100%`.

<img width="2262" height="1874" alt="image"
src="https://github.com/user-attachments/assets/8cb64af9-d7a9-4d38-8203-34c0d7a836b0"
/>
<img width="2354" height="1758" alt="image"
src="https://github.com/user-attachments/assets/7dd900c0-6f20-4361-a1b9-319b7138b405"
/>

<!-- sm12x-5kp-benchmark-figures:end -->


## Test plan

- [x] Added `tests/moe/test_sm12x_{op}_{precision}.py` (one file per op
x precision) verifying each op against a pure-torch reference — fp8
reuses `flashinfer.testing.utils` quant helpers, mxfp8_mxfp4 uses inline
MXFP8/MXFP4 quant matching the moe_gemm SFA/SFB packing ABI.
- [x] All 8 tests pass on an SM120a device (RTX PRO 6000 Blackwell).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added Blackwell SM12x fused MoE support for FP8 and MXFP8×MXFP4
workloads.
* Added grouped GEMM, gated FC1 activation, quantized outputs, and FC2
finalization.
* Added SiLU and SiTU activation support, automatic tile selection, and
optional autotuning.
* Made the new operations publicly available when CuTe-DSL is installed.

* **Tests**
* Added SM120 validation, smoke tests, and reference-based correctness
coverage across supported data formats.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: CarstyYou <186021327+CarstyYou@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [eded617](https://github.com/flashinfer-ai/flashinfer/commit/eded6174660cd96e5bae19b2316e8d6a57a3d532)

- **作者**: Adrian
- **时间**: 2026-09-22T21:03:11Z
- **提交信息**: test: prune top-k parameter matrix (#5429)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/utils/test_topk.py` to `parametrize_product`. Regular pytest runs
use deterministic pairwise coverage, while `pytest --full` retains the
exhaustive matrices for nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Repository commit hooks passed for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

### [8e9293d](https://github.com/flashinfer-ai/flashinfer/commit/8e9293deb634cd10ddce72a61604c21380c0c8c8)

- **作者**: Anerudhan Gopal
- **时间**: 2026-09-22T20:58:03Z
- **提交信息**: feat(moe_ep): CUDA-graph support for the split layer (nccl_ep + nixl_ep) (#5287)

## Summary

`MoEEpSplitLayer.forward()` created a `Handle` per call and destroyed it
in a
`finally`. A CUDA graph records the device pointers it sees at capture
time, so
that handle's buffers were freed the moment capture ended and every
replay
dereferenced dead memory — silent at capture, an illegal memory access
at
replay.

`tests/moe_ep/test_moe_ep_cudagraph_multirank.py` already covered the
capture
recipe one layer down, driving `Fleet`/`Handle` directly, *precisely
because*
the layer could not express it — its own docstring says so. This PR adds
the
layer-level API that closes that gap, for **both** split comm backends.

## What changed

**`MoEEpSplitLayer.create_graph_state()` → `MoEEpSplitGraphState`.**
Holds one
long-lived handle across forwards: the allocating half runs outside the
capture
and `Handle.update()` is recorded inside it, mirroring NCCL-EP's own
recipe
(`ncclEpInitHandle` outside, `ncclEpUpdateHandle` inside —
`contrib/nccl_ep/ep_test.cu --use_cuda_graph`). The state also pins the
buffers
the graph binds — `topk_weights` is bound into the handle at creation,
`out` is
the address combine writes — and `forward()` re-checks those addresses
every
call, because a caller that silently passed a fresh tensor would
otherwise get a
graph still serving the old one.

```python
state = layer.create_graph_state(t)      # outside any capture, ALL ranks
layer.forward(t, graph_state=state)      # warmup, still eager
torch.cuda.synchronize()

g = torch.cuda.CUDAGraph()
with torch.cuda.graph(g):
    y = layer.forward(t, graph_state=state)

t.hidden_states.copy_(new_x)             # in place — same buffers
t.topk_ids.copy_(new_ids)
g.replay()
```

`forward()` without a `graph_state` is **unchanged**.

**Three silent failures now raise at the point of the mistake:**
capturing
`forward()` without a graph state (previously faulted at replay),
rebinding a
tensor the graph already bound, and `enable_timing` under capture — it
synchronizes the device to read its CUDA events, which capture forbids.

**`NixlEpHandle.update()`.** NIXL-EP needs no `ncclEpUpdateHandle`
analogue: LL
dispatch recomputes routing in-kernel from `topk_idx`, and its recv
buffers live
in the Buffer's persistent RDMA arena. So `update()` instead guarantees
the
*binding* that makes replay correct — the int64→int32 ids cast now lands
in a
handle-owned buffer rather than a fresh allocation per call, so the
address the
graph captured keeps receiving the new routing.

Under capture the handle uses `return_recv_hook=False`, which launches
the
send and receive phases together and joins them back to the compute
stream.
Calling the receive hook during capture would also record its kernel
launch;
the combined path avoids deferred host orchestration and preserves the
same
device-side arrival waits. `async_finish=False` preserves the
transport's
compute-stream join; the older asynchronous caller overwrote dispatch's
event
before ordering the expert GEMM after dispatch.

**Also:** `benchmarks/bench_moe_ep.py --cuda-graph`, and a runbook
section.

## Prior validation — 4×GB200

`tests/moe_ep/test_split_layer_cudagraph_multirank.py`, **7/7**:
nccl_ep (low_latency + high_throughput) and nixl_ep (low_latency, MVP),
across
capture, the un-stated-forward rejection, and the rebound-buffer
rejection.

The assertion that matters is not "capture completes" or even "replay
matches
eager" — it is that the activations are rewritten **in place** between
replays
and the output tracks the change. A graph that replayed nothing would
leave the
previous contents in the output buffer and still pass the first two.

nixl_ep's capturability was established by direct probe before any code
was
written. `return_recv_hook=False` is bit-identical to the shipped hook
path
eagerly, and capture+replay reproduced eager exactly while tracking a
rewritten
input by precisely the predicted delta.

## W4A16: capturing the whole chain

`test_split_layer_cudagraph_multirank.py` captures the layer with the
*identity*
inner kernel, which isolates the transport. A second test captures the
**whole
chain** — dispatch → quantized grouped GEMM → combine — with real expert
weights, using weight-only quantization:
`QuantConfig(weight=NVFP4, activation=BF16)`. Activations cross the wire
as BF16
(`mxfp8_dispatch` off) and reach the MMA as BF16; only the weights are
4-bit.

No new kernel was needed — `prepare.py` already allows the `(NVFP4,
BF16)` pair
and quantizes a canonical BF16 weight pack at construction, and
`build_activation_pack` already passes BF16 rows through for both W4A16
encodings. `CuteDslConfig` is pinned as the sole backend candidate
rather than
left to autotune: on SM100 it is the backend that serves this pair
(verified on
GB200 — `MoELayer` resolves to `[CuteDslRunner]`), so the default list
would
make coverage depend on whichever backend won autotune.

**3/3 on 4×GB200**, covering nccl_ep and nixl_ep plus a routing-rewrite
case
that isolates the dispatch half — activations alone cannot witness it,
since a
changed `x` moves the output even if routing were ignored.

Note this path needs `nvidia-cutlass-dsl >= 4.7.0a0` (which
`pyproject.toml`
already requires). On 4.5.2 the W4A16 kernel fails inside the DSL at
`cute.copy`.

## Previously reported perf — 4×GB300 (theia, sm103)

These measurements predate the September 22 follow-up. They were taken
after
the earlier LL output-retention fix. Hardware note: figures earlier in
this
PR's history were 4×GB200 (sm100).
16 experts, hidden 4096, intermediate 2048, top-k 4, world 4, repeat 50.

Three modes, because the middle one answers @djns99's question:
`eager` = handle created/destroyed per forward (default);
`stated` = persistent handle, **no capture**; `graph` = captured replay.
µs, median of 50.

| quant | backend | tok/rank | eager | stated | graph | stated/eager |
**graph/eager** |
|---|---|---|---|---|---|---|---|
| identity | nccl_ep | 32 | 195.4 | 116.8 | 48.5 | 1.67 | **4.03** |
| identity | nccl_ep | 128 | 208.7 | 130.9 | 80.7 | 1.59 | **2.59** |
| identity | nccl_ep | 512 | 340.8 | 266.3 | 195.6 | 1.28 | **1.74** |
| identity | nccl_ep | 1024 | 489.6 | 415.7 | 344.0 | 1.18 | **1.42** |
| identity | nixl_ep | 32 | 149.7 | 125.1 | 47.3 | 1.20 | **3.16** |
| identity | nixl_ep | 128 | 154.2 | 134.5 | 79.5 | 1.15 | **1.94** |
| identity | nixl_ep | 512 | 291.4 | 266.2 | 210.5 | 1.09 | **1.38** |
| identity | nixl_ep | 1024 | 462.2 | 447.8 | 390.4 | 1.03 | **1.18** |
| w4a16 | nccl_ep | 32 | 684.5 | 589.5 | 100.5 | 1.16 | **6.81** |
| w4a16 | nccl_ep | 128 | 749.7 | 620.5 | 207.2 | 1.21 | **3.62** |
| w4a16 | nccl_ep | 512 | 935.0 | 831.3 | 609.8 | 1.12 | **1.53** |
| w4a16 | nccl_ep | 1024 | 1302.1 | 1208.0 | 1121.2 | 1.08 | **1.16** |
| w4a16 | nixl_ep | 32 | 627.1 | 595.3 | 97.7 | 1.05 | **6.42** |
| w4a16 | nixl_ep | 128 | 623.5 | 589.5 | 197.1 | 1.06 | **3.16** |
| w4a16 | nixl_ep | 512 | 828.6 | 811.9 | 571.1 | 1.02 | **1.45** |
| w4a16 | nixl_ep | 1024 | 1188.9 | 1157.3 | 1072.0 | 1.03 | **1.11** |

Reading:

- **The win concentrates at decode-sized batches** and is largest for
W4A16
(**6.8×** at 32 tok/rank), because the inner kernel adds per-forward
launch
  cost a graph removes. It narrows to ~1.1–1.4× at 1024, where GPU work
  dominates.
- **The persistent handle alone is worth having for nccl_ep**
(1.59–1.67× at
decode sizes) and close to free for nixl_ep (1.02–1.20×) — nccl_ep pays
  `ncclEpInitHandle`, a host-side allocation, per forward, while
  `NixlEpHandle.__init__`/`destroy` are nearly pure Python.
- **Every row now has `amort ≤ per_call`.** An earlier revision of this
table
did not, and chasing that is what surfaced the memo-retention issue
below. The graph
speedup at 128 tok/rank amortized **fell from 5.18× to 2.30×** once the
eager baseline stopped being inflated by that bug — the old number was
partly
  measuring a defect rather than a benefit of capture.

Reproduce: `benchmarks/bench_moe_ep.py --cuda-graph` (and `--quant
w4a16`).

## NCCL output memo: bounded retention of per-call buffers

`NcclEpHandle._wrap` memoizes FFI descriptors keyed by `(data_ptr,
dtype,
shape)`, and the wrapper keeps its torch tensor alive. Eager `forward()`
allocates a fresh `out` per call, so caching it **pinned** it, the
allocator
could not hand that address back, the next forward got a new one, and
the memo
missed 100% of the time while retaining one output buffer per forward
until
cache eviction. The memo's
premise is that addresses get recycled; for `out` the memo was what
prevented
the recycling.

The cache clears after exceeding its 256-entry threshold and bypasses
tensors
larger than 2 MiB, so this is bounded retention/churn (roughly 512 MiB),
not
unbounded growth. The stability gate now covers both LL and HT combine
and
only accepts explicitly supplied output buffers. Transient dispatch
payloads,
expert outputs, and routing inputs still use the existing bounded memo;
changing their caching policy remains a separate follow-up. Eviction now
removes only address-keyed wrappers and preserves named receive buffers,
counters, and configs: clearing those workspaces let a later eager
forward
free allocations still referenced by a captured graph. LL/HT regressions
cover
forced eviction followed by eager execution and replay.

Measured at 128 tok × 4096 hidden: 50/50 distinct `out` pointers, +1
memo entry
per forward, torch allocated **27 → 227 MiB over 200 forwards**, and
`empty_like` going from 1.1 µs to ~103 µs once predecessors were pinned.
Only
128 tok/rank showed it clearly (512/1024 exceed `_WRAP_MEMO_MAX_BYTES`
and take
the bypass; 32 pins 8× less). **nixl_ep has no such memo and never
showed it** —
that asymmetry is what identified the mechanism.

Fixed by asking rather than inferring:
`CombineInputParams.out_is_stable`, set
True only where the buffer genuinely persists, defaulting to False.
Eager
amortized at 128 tok/rank improves **356.8 → 158.0 µs (2.26×)**.
Pre-existing
code, not introduced here, but this PR's benchmark is what surfaced it
and the
graph path already avoided it.

## Review follow-up

Persistent state remains explicit because it changes output ownership
and
lifetime: each forward reuses `state.out`, input buffers stay bound, and
all
ranks must coordinate state creation and retirement. The existing
measurements
show a benefit for the measured shapes; opt-in preserves ordinary eager
callers' independent outputs. A pointer-keyed implicit cache cannot
infer when
captured buffers are safe to replace.

Graph-state validation now snapshots input/output pointers and tensor
metadata
(shape, stride, dtype, device), including the retained tensors used by
the
handle. It rejects same-address reinterpretations, in-place storage
rebinding,
and invalid custom output devices/layouts before transport work.

Replay tests now compare against eager numerical references for
rewritten
activations, routing IDs, and routing weights. The smoke harness
includes the
new graph and LL/HT output-retention tests, honors backend selection,
and gates
W4A16 to Blackwell. This harness is not called by the checked-in GitHub
workflow;
a four-GPU CUDA 13 environment is still needed for distributed
execution.

Local validation for this follow-up: **183 tests passed** across the
NCCL/NIXL
host-path suites, graph-state validation, and layer/config tests. This
includes
real single-GPU CUDA graph routing-copy replay with both NIXL index
widths,
using a stub transport. Five new output-cache regressions and both LL/HT
workspace-eviction
regressions fail against their old implementations. Changed-file
pre-commit checks (including mypy and Ruff) pass;
the smoke harness's backend selection and shell syntax checks pass.
The prior four-GPU results and performance table above are historical
results,
not a rerun of this follow-up. A fresh four-rank B200 validation job is
now
submitted on prenyx as job `2495008` using source `439e9bbae` in an
isolated
checkout. It remains queued; no fresh distributed result is claimed.
GitHub
pre-commit, public API, documentation, and CodeRabbit checks pass on
this head;
the explicitly retriggered full CI run is still in progress.

## Constraint worth knowing

nixl_ep's C++ Buffer toggles a **host-side** double-buffer index
(`buffer_idx ^= 1`) on every dispatch and combine. Replays run no host
code, so
every replay reuses the slot current at capture. That stays consistent
only
while all EP ranks run the same sequence of eager calls and replays —
ordinary
collective discipline, but sharper here. Documented in the runbook.

## Not covered

- Not yet wired through vLLM; that adapter still relies on per-forward
handles,
  and vLLM pins a released flashinfer.
- nixl_ep is LL-only (MVP), so HT capture is nccl_ep-only.
- Single-node only (4 ranks, NVLink); multi-node capture untested.
- No multi-size-graph split-layer test yet (one state per shape is
documented
  and enforced).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added CUDA Graph capture and replay for MoE expert-parallel split
layers.
- Added reusable graph-state management with validation for ownership,
warmup, routing updates, and lifecycle.
  - Added public access to the split-layer graph state API.
- Added W4A16 quantization support for compatible MoE expert-parallel
benchmarks.
- Benchmarks now support CUDA Graph mode and identify graph or eager
execution in results.

- **Bug Fixes**
- Improved CUDA Graph compatibility when routing inputs and output
buffers are reused.
  - Prevented unnecessary memory growth during repeated eager forwards.

- **Documentation**
- Expanded CUDA Graph configuration, validation, troubleshooting, and
retirement guidance.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [dd4fb7a](https://github.com/flashinfer-ai/flashinfer/commit/dd4fb7a7d7dc5447fa863ec64579eb81fa221871)

- **作者**: eigen
- **时间**: 2026-09-22T20:30:49Z
- **提交信息**: feat(cake_sage): add SM100 and SM103 Sage-FP8 block-sparse attention with fused quantizer (#5442)

## Summary

Source-only **Cake (Weave-generated) SM100/SM103 Sage-FP8 block-sparse
attention** for B200 / B300, plus a **fused Sage-FP8 quantizer**, wired
into the existing `sm100_blk64` API.

- `bsa_attn_sm100_blk64_fwd(..., backend="cake")` runs the Sage-FP8 path
(E4M3 Q/K/V + per-token Q / per-16-token K / per-channel V scales) with
the CuTe kernel's limits lifted: any batch size and head count, GQA
(`num_heads % num_kv_heads == 0`), unaligned `seqlen_q` / `seqlen_k` (no
64-token padding requirement), per-row KV counts via `q2k_block_nums`
(empty rows give exact zeros / `-inf` LSE), rank-1/2/3 `block_sizes`
token masks, optional LSE. `backend="cute"` (default) is unchanged.
-
`flashinfer.cute_dsl.sparse.bsa_sage_sm100_cake.sage_fp8_quantize_sm100(q,
k, v)` fuses the Sage Q/K/V quantization into two launches (scales
bit-exact with the torch recipe used by
`tests/attention/test_vsa_block_sparse.py`).
- Generated sources:
`csrc/cake_sage_block_sparse_attention/{sm_100a,sm_103a}/` +
`cake_sage_block_sparse_attention_sm100_manifest.json`
(checksum-attested, excluded from clang-format like the other Cake
exports). Loader: `flashinfer/jit/cake_sage_block_sparse_attention.py`
(`load_cake_sage_sm100_module(arch, stage)`).
- One variable-shape M64xN128 `tcgen05` kernel per architecture
(two-stage softmax ping-pong, FP8 P.V MMA, 16 warps, 77 KB SMEM); no
per-shape clones.

## Performance

_CUPTI, cold L2, `Sq = Sk = 4096`, head_dim 128, uniform selected K64
blocks per Q64 row._

Baseline = the existing CuTe-DSL Sage path (`bsa_attn_sm100_blk64_fwd`,
default backend) on the same node. The CuTe Sage path only accepts
`batch == 1` and `num_head in (4, 8)`, so the B8/H32 rows run it as 32
contiguous B1/H8 calls and report the **sum of the 32 per-call medians**
(each call timed alone with a cold L2; timing the launch span of all 32
calls would charge CuTe for host gaps). Timing the 32 calls back-to-back
and summing kernel durations instead gives 1.34x / 1.56x / 2.89x on B200
and 1.39x / 1.64x / 3.03x on B300 at 58 / 32 / 6 selected blocks.
Reproduce with `python
benchmarks/bench_cake_sage_sm100_block_sparse_attention.py`.

**B8 / H32 / S4096**

| GPU | selected / 64 | Cake ms (TFLOPS) | CuTe ms (32 calls) | speedup
|
|---|---|---|---|---|
| B200 (sm_100a) | 6 (10%) | 0.446 (462) | 1.301 | **2.92x** |
| | 32 (50%) | 1.284 (856) | 2.060 | **1.60x** |
| | 58 (90%) | 2.149 (927) | 3.012 | **1.40x** |
| B300 (sm_103a) | 6 (10%) | 0.405 (509) | 1.232 | **3.04x** |
| | 32 (50%) | 1.141 (964) | 1.877 | **1.65x** |
| | 58 (90%) | 1.900 (1049) | 2.688 | **1.41x** |

**B1 / H8 / S4096 (one call each side)**

| GPU | 6 / 64 | 32 / 64 | 58 / 64 |
|---|---|---|---|
| B200 | 0.0249 vs 0.0405 ms (1.63x) | 0.0565 vs 0.0642 (1.14x) | 0.0885
vs 0.0941 (1.06x) |
| B300 | 0.0234 vs 0.0383 (1.64x) | 0.0506 vs 0.0585 (1.16x) | 0.0785 vs
0.0840 (1.07x) |

**Fused quantizer vs the torch recipe (B8 / H32 / S4096)**

| GPU | fused ms | torch recipe ms (GPU span) | speedup |
|---|---|---|---|
| B200 | 0.279 | 5.497 | 19.7x |
| B300 | 0.280 | 5.414 | 19.3x |

On sm_100a the softmax P tile evaluates the last quarter of each
64-value fragment with a packed f32x2 polynomial exp2 instead of
`MUFU.EX2` (the schedule is SFU-bound at high density); this lifted B200
by 3-6% across densities with unchanged max-abs error. sm_103a has twice
the SFU exp throughput and keeps the all-hardware path, so the two
architectures ship different generated kernels from one source. The
low-density rows are dominated by the CuTe kernel's fixed per-call cost,
which the persistent Cake schedule amortizes.

## Correctness

- `tests/attention/test_cake_sage_block_sparse_attention_sm100.py`:
exact-P dequantized FP32 reference on aligned, ragged (Sq/Sk in
257/1000, 100/257, 65/96, 320/1024), per-row counts with empty rows,
block_sizes rank 1/2/3, GQA H4/Hkv2 and H8/Hkv1, LSE; cross-check
against the CuTe backend on its own shape; fused quantizer vs the torch
recipe (bit-exact scales, values within one E4M3 step);
manifest/file-hash consistency (CPU).
- compute-sanitizer synccheck + memcheck: 0 errors on both architectures
(Cake-side gate).

`tests/attention/test_cake_sage_block_sparse_attention_sm100.py`: 12
passed on B200 (sm_100a) and 12 passed on B300 (sm_103a), FlashInfer
main `5871b667`, container `nvcr.io/nvidia/sglang:26.07-py3` (CUDA 13,
nvidia-cutlass-dsl 4.8.0.dev0).

## Notes

- The fused quantizer's per-channel V scale is `[B, Hkv, 128]`; the CuTe
path takes `[H, 128]` (`v_scale[0]` for batch 1), the Cake path accepts
both.
- `kv_splits` / `use_clc` do not apply to the Cake backend (persistent
single-kernel schedule).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9607113](https://github.com/flashinfer-ai/flashinfer/commit/9607113a934d02dd7e8f423255b315f6a4c97f97)

- **作者**: Lee Yong Jun
- **时间**: 2026-09-22T20:12:35Z
- **提交信息**: perf(moe): feed cuTile BF16 GEMM2 from an expert-sorted buffer at large M (#5129)

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Adds an expert-sorted intermediate layout to the cuTile BF16 fused MoE
(`flashinfer/fused_moe/cutile/moe.py`) and enables it from the runner
for large routing batches.

While profiling the #4646 testlist on an RTX PRO 6000 (SM120) for #4857,
GEMM2 was the slow kernel at 8192 tokens: it reached 176-204 TFLOPS
against 282-288 for GEMM1 (cuBLAS bf16 on that card is about 409).
GEMM2's A operand is one activation row per assignment, read through
`ct.gather` with no reuse, and the tactics the tuner picks at large M
use tile_k=32, so each gathered row segment is only 64 bytes. GEMM1's
token rows are shared across top_k assignments and hit L2, which is why
it did not show the same problem. The W4A4 path already avoids this with
its sorted-IO buffers; the BF16 path did not have an equivalent.

With `sorted_io=True`, GEMM1 scatters its output tiles into the padded
expert-sorted row space (the same scatter as before, only with sorted
row indices), the activation runs on that buffer, and GEMM2 loads its A
tiles with `ct.load(..., allow_tma=True)`. The GEMM2 epilogue still
scatters to assignment order, so `combine` is untouched and the two
paths produce bitwise-identical outputs (covered by a new test). Padded
rows only feed GEMM2 rows that the epilogue drops. The workspace grows
the GEMM1/activation buffers to the padded row space only when the
runner asks for the sorted path.

`CuTileBf16Runner` turns it on for `num_assignments >= 32768` and
`intermediate_size >= 1024`; both constants live in `runners.py`. Below
that the gather is fine and the padded buffers would only add traffic.
In my measurements a TMA `ct.store` for the sorted GEMM1 tile was 13-18%
slower than the scatter it would replace, so the sorted output keeps the
scatter; I left a comment in the kernel about that since it is not
obvious.

Measured on an RTX PRO 6000 Blackwell (SM120), cuTile BF16,
Nemotron-3.5-Lightning shape (H=2688, I=1856, E=128, top_k=6, ReLU2),
CUDA graph timing, both autotuned:

| Tokens | before (us) | after (us) | GEMM2 kernel, fixed tactic (us) |
|---:|---:|---:|---|
| 2048 | 1905 | 1920 | 904 -> 917 (path off) |
| 4096 | 2709 | 2703 | 1519 -> 1513 (path off) |
| 8192 | 4375 | **4140** | 2789 -> **2256** |

Qwen3.6-35B-A3B (I=512) stays on the gather path; with the sorted path
forced on it lost about 3% there, which is what the intermediate-size
condition is for. I might be missing a shape family where the threshold
should differ, so happy to adjust either constant.

## 🔍 Related Issues

<!-- Link any related issues here -->
#4857 (cuTile MoE performance on SM120). Baseline numbers and the
per-kernel breakdown are from the #4646 testlist.

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

New `test_cutile_bf16_sorted_io_matches_unsorted` runs SwiGLU and ReLU2
on a shape with partial tiles on every GEMM edge (H=192, I=96, 64 tokens
x top_k 2 over 4 experts) with the sorted path forced on and off and
asserts bitwise equality. `pytest tests/moe/test_unified_moe_cutile.py`
passes on the RTX PRO 6000 (81 passed). The benchmark reference check
passes for the Nemotron shape at 2048/4096/8192 tokens with the path on.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added optional sorted-I/O execution for BF16 Mixture-of-Experts
workloads.
* Automatically enables the optimized mode for sufficiently large
workloads while retaining standard processing for smaller inputs.
* Added support for configuring sorted-I/O behavior when allocating
workspace and running MoE operations.

* **Bug Fixes**
* Verified that sorted-I/O and standard execution produce matching,
finite results across supported activation functions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0d7df3d](https://github.com/flashinfer-ai/flashinfer/commit/0d7df3db16a9224401ade6c6130a7a9327d08414)

- **作者**: Jonathan Dierksen
- **时间**: 2026-09-22T19:08:22Z
- **提交信息**: ci: diagnose stalled JIT-cache provider builds (#5274)

## 📌 Description

Diagnose and bound JIT-cache provider builds that stop making observable
progress, without imposing a wall-clock limit on valid CUDA compiler
invocations.

Addresses #5367 but may need further investigation.

- Restore the normal server-side sccache execution model for both C++
and CUDA compilation.
- Wrap provider wheel builds in a 90-minute no-output watchdog; any
build output resets the timer.
- Before terminating a stalled build, capture the process tree,
per-process and per-thread `/proc` state, wait channels, syscalls,
kernel stacks, open file descriptors, sccache statistics, memory/CPU/I/O
pressure, cgroup memory events, filesystem state, and newest build
outputs.
- Send TERM to the build process group and KILL after a two-minute grace
period.
- Bound the final sccache statistics and shutdown commands so a stuck
daemon cannot hide the watchdog result until the six-hour job timeout.
- Upload the watchdog report and sccache statistics from release and
nightly provider jobs even when the build fails.
- Preserve the raw Ninja log and generated manifests on every provider
build, with JSON/text reports for longest edges, completion gaps, tail
completions, percentiles, and observed parallelism.
- Add elapsed, finished, running, and unstarted edge counts to each
Ninja status line.

## 🔍 Related Issues

Originally observed in [Nightly Release job
104677497471](https://github.com/flashinfer-ai/flashinfer/actions/runs/35059219970/job/104677497471).
The same near-completion stall recurred in [job
105482987504](https://github.com/flashinfer-ai/flashinfer/actions/runs/35306860005/job/105482987504)
and [job
106023662663](https://github.com/flashinfer-ai/flashinfer/actions/runs/35489728650/job/106023662663).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
[pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All focused tests are passing.

Validated locally with:

- `pre-commit run --files` on all changed files.
- `pytest --noconftest -q tests/test_collect_ninja_diagnostics.py
tests/test_run_with_output_watchdog.py` — 5 passed.
- `bash -n` and `shellcheck` on the three changed shell scripts.
- Ruff lint and format checks on the watchdog, Ninja collector, and
their tests.
- YAML parsing for both changed workflows.
- A mocked `setup_sccache` invocation verifying server-side mode and
both launchers.

The full provider matrix requires the CI manylinux/CUDA environments and
is left to GitHub Actions.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

The failed 90-minute experiment timed out dozens of legitimate cold
compiles at once because all 61 parallel compiler commands started
together. The public nightly hangs have a different signature: Ninja
reaches the final few edges, then emits nothing for more than five
hours. A whole-build inactivity threshold distinguishes those cases and
preserves the live state needed to determine whether the stall is in
Ninja, sccache, nvcc, a CUDA subtool, resource pressure, or I/O.

Automatic retry is intentionally not part of this revision. Once the
watchdog artifact identifies whether the failure is transient and leaves
the runner clean, a retry limited to watchdog exit 124 is
straightforward to add without retrying deterministic compiler failures.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Build Improvements**
* Provider builds now detect stalled output and collect system, process,
and build diagnostics before terminating unresponsive builds.
* Builds report a timeout status after the configured no-output period
and termination grace period.
  * Provider compilation now uses server-side sccache compilation.

* **Diagnostics**
* Release and nightly workflows upload sccache and Ninja diagnostics,
including for failed builds.
* Diagnostics are retained for seven days, with warnings when
unavailable.

* **Workflow Updates**
* Pull-request dry runs now also trigger when build-diagnostics tooling
changes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8afea06](https://github.com/flashinfer-ai/flashinfer/commit/8afea067e10238ea87c8784e4398f792d91e4665)

- **作者**: Jimmy Zhou
- **时间**: 2026-09-22T18:39:14Z
- **提交信息**: fix(gemm): clamping sfa load row index for blackwell fp8 grouped gemm (#5387)

<!-- .github/pull_request_template.md -->

## 📌 Description

### Problem

`BlockwiseContiguousGroupedGemmKernel` reads past the end of `a_scale`
when the row count is not a multiple of 128.

The scale-producer warp has two fetch paths. The `scale_kg == 1` path
predicates each row against `mSFA_mkl.shape[0]`. The faster `scale_kg >
1` path, which stages 4 K-blocks per lane in one 16-byte `cp.async`,
indexes `(_m0 + _r) * _sfa_m_st` for `_r` in 0..127 with no bound at
all, and never consults the existing `scale_always_inbounds` flag. On
the tail tile it reads up to 127 rows off the end.

`_pick_config` enables the fast path whenever `k` is a multiple of 512,
without reference to `m`, so any `m % 128 != 0` problem with `k % 512 ==
0` trips it. Present since the kernel landed in #4734.

The read is read-only and the stale rows are discarded by the epilogue,
so results are unaffected — but it faults when `a_scale` ends near a
mapping boundary.

### Fix

Clamp the row index to the last valid row, under `cutlass.const_expr(not
self.scale_always_inbounds)` so aligned-`m` codegen is unchanged.
Clamping rather than predicating keeps the producer's inner loop
divergence-free. No new JIT variants: `_COMPILED`'s key already includes
`m % 128 == 0`.

## 🔍 Related Issues

nvbug 6794559 — reported by the GB200 sanitizer job.

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

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->

### [97e7d5b](https://github.com/flashinfer-ai/flashinfer/commit/97e7d5b750a3f47d2dddb44b10b7c52e8054981f)

- **作者**: Jonathan Dierksen
- **时间**: 2026-09-22T17:52:38Z
- **提交信息**: docs(gemm): use Vera Rubin NVL72 nomenclature (#5457)

## Summary
- use the approved Vera Rubin NVL72 platform name in the SM107 FP4
tuning note
- no runtime behavior changes

## Validation
- python3 -m py_compile flashinfer/gemm/kernels/utils.py
- repository pre-commit hooks passed

## Coordination
- flashinfer-ci job naming update:
https://gitlab-master.nvidia.com/dl/flashinfer/flashinfer-ci/-/merge_requests/446
- ci-bot compatibility and display-name update:
https://gitlab-master.nvidia.com/dl/flashinfer/ci-bot/-/merge_requests/21

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Style**
* Removed trailing whitespace from an internal code comment. No
user-facing behavior changed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ee9aeb0](https://github.com/flashinfer-ai/flashinfer/commit/ee9aeb0e12f26f41e03ab738f2f97af36ee423a0)

- **作者**: Jonathan Dierksen
- **时间**: 2026-09-22T17:18:25Z
- **提交信息**: ci: reuse cubin caches after key changes (#5273)

## Summary

- restore the newest platform-compatible cubin cache when the exact
artifacts.py key changes
- checksum-verify restored files and download only missing or invalid
artifacts
- prune stale cache files before packaging so older artifact pins cannot
leak into the wheel
- apply the fallback consistently to nightly and release workflows

## Validation

- python -m pytest tests/test_artifacts.py -q (10 passed)
- pre-commit run on all changed files
- parsed both workflow files with Ruby YAML
- git diff --check

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Improvements**
* Release builds can now reuse compatible cached artifacts when an exact
match is unavailable, improving cache recovery across runs.
* Cached artifacts are verified before use, and outdated files are
automatically removed to help ensure packages contain only current build
outputs.

* **Tests**
* Added coverage confirming that stale cached artifacts and their empty
directories are cleaned up.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d0099ab](https://github.com/flashinfer-ai/flashinfer/commit/d0099ab2828c6055ac37d1ddbd7767f8b28a54e8)

- **作者**: Greg Fishman
- **时间**: 2026-09-22T16:54:22Z
- **提交信息**: perf(attention): use Tensor.max() for the longest lengths in plan() (#5043)

<!-- .github/pull_request_template.md -->

## 📌 Description

`plan()` finds the longest query and KV length with Python's built-in
`max()`.
That is a Python loop over the batch.
At large batches it is most of the host time of `plan()`.

This PR uses `Tensor.max()` instead. Same result, one call.
The ragged prefill wrapper already does this.

Five lines change: two in paged prefill, three in paged decode.

`seq_lens` is documented as uint32. Torch cannot compare or reduce
uint32 on CPU, so `plan()` already failed on uint32 input with two or
more requests.
This PR converts `seq_lens` to int32 once on entry. For int32 input this
is a no-op.

Host time of one `plan()` call, RTX 4090:

| batch size | prefill, before | prefill, after | decode, before |
decode, after |
| --- | --- | --- | --- | --- |
| 64 | 281 µs | 90 µs | 173 µs | 76 µs |
| 256 | 850 µs | 99 µs | 461 µs | 87 µs |
| 1,024 | 3,118 µs | 130 µs | 1,605 µs | 112 µs |

In vLLM with MTP at 64 to 256 concurrent requests: ITL is 1.2% to 2.4%
lower, output is 1.3% to 2.5% higher.

<details>
<summary>Benchmark details</summary>

`plan()` timing: Ryzen 9 5950X, torch 2.14. KV length 512 to 4,096, page
size 16, 8 heads, head dim 128. Median of 6 runs. Decode uses tensor
cores.

| batch size | prefill, before | prefill, after | decode, before |
decode, after |
| --- | --- | --- | --- | --- |
| 1 | 89 µs | 87 µs | 75 µs | 75 µs |
| 8 | 115 µs | 87 µs | 90 µs | 75 µs |

End to end: vLLM 0.29.0, Qwen3.5-0.8B, MTP with 3 draft tokens,
FlashInfer backend, RTX 4090. Random prompts, 6 rounds per arm, arms
alternated. Only the five lines differ. 95% confidence intervals:

| prompt / output tokens | concurrency | median ITL | output tokens/s |
| --- | --- | --- | --- |
| 128 / 128 | 64 | -2.2% [-2.6, -1.8] | +2.4% [+1.6, +3.1] |
| 128 / 128 | 256 | -2.4% [-3.3, -1.4] | +2.5% [+1.3, +3.6] |
| 1,024 / 128 | 64 | -1.9% [-2.6, -1.1] | +1.5% [-0.1, +3.1] |
| 1,024 / 128 | 256 | -1.2% [-1.9, -0.5] | +1.3% [+0.6, +1.9] |

Why it shows: without TRTLLM attention kernels, vLLM sends speculative
verify rows through the prefill wrapper. `plan()` then runs every step,
one row per request.

No measurable change: concurrency 8 to 16, 8,192-token prompts, or no
speculative decoding.

Script for the `plan()` timing:

```python
"""Host time of BatchPrefillWithPagedKVCacheWrapper.plan() and
BatchDecodeWithPagedKVCacheWrapper(use_tensor_cores=True).plan() when the caller
does not pass the longest lengths. Prints one CSV row per configuration:
wrapper,batch_size,median_us,p10_us,p90_us"""

import statistics
import sys
import time

import torch

import flashinfer

PAGE, HEADS, HEAD_DIM, CALLS, WARMUP = 16, 8, 128, 2000, 200


def inputs(bs):
    g = torch.Generator().manual_seed(bs)
    kv = torch.randint(512, 4097, (bs,), dtype=torch.int32, generator=g)
    q = torch.randint(1, 5, (bs,), dtype=torch.int32, generator=g)
    pages = (kv + PAGE - 1) // PAGE
    kv_indptr = torch.nn.functional.pad(torch.cumsum(pages, 0, dtype=torch.int32), (1, 0))
    qo_indptr = torch.nn.functional.pad(torch.cumsum(q, 0, dtype=torch.int32), (1, 0))
    last = kv - (pages - 1) * PAGE
    indices = torch.arange(int(kv_indptr[-1]), dtype=torch.int32, device="cuda")
    return qo_indptr, kv_indptr, indices, last


def timeit(fn):
    for _ in range(WARMUP):
        fn()
    torch.cuda.synchronize()
    ts = []
    for _ in range(CALLS):
        t0 = time.perf_counter()
        fn()
        ts.append((time.perf_counter() - t0) * 1e6)
        torch.cuda.synchronize()
    ts.sort()
    return statistics.median(ts), ts[len(ts) // 10], ts[len(ts) * 9 // 10]


def main():
    ws = torch.empty(256 * 1024 * 1024, dtype=torch.uint8, device="cuda")
    for bs in (1, 8, 64, 256, 1024):
        qo, kvp, idx, last = inputs(bs)
        pre = flashinfer.BatchPrefillWithPagedKVCacheWrapper(ws, "NHD")
        dec = flashinfer.BatchDecodeWithPagedKVCacheWrapper(ws, "NHD", use_tensor_cores=True)
        # indptr and last-page lengths on the CPU, as serving engines pass them.
        p = lambda: pre.plan(qo, kvp, idx, last, HEADS, HEADS, HEAD_DIM, PAGE, causal=True, q_data_type=torch.float16)
        d = lambda: dec.plan(kvp, idx, last, HEADS, HEADS, HEAD_DIM, PAGE, q_data_type=torch.float16)
        for name, fn in (("prefill", p), ("decode_tensor_cores", d)):
            med, p10, p90 = timeit(fn)
            print(f"{name},{bs},{med:.1f},{p10:.1f},{p90:.1f}", flush=True)


if __name__ == "__main__":
    print(f"# flashinfer={flashinfer.__file__} torch={torch.__version__} gpu={torch.cuda.get_device_name(0)}", file=sys.stderr)
    main()
```

</details>

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

New tests pin the lengths `plan()` computes:

-
`tests/attention/test_batch_prefill_kernels.py::test_batch_prefill_plan_max_lens`
-
`tests/attention/test_tensor_cores_decode.py::test_batch_decode_tensor_cores_plan_max_kv_len`

They run with `seq_lens` omitted, int32 and uint32. The uint32 cases
fail without the int32 conversion.

Existing prefill and decode tests: same results before and after, 0
failures (RTX 4090).

<details>
<summary>Test counts</summary>

| file | passed | skipped | xfailed |
| --- | --- | --- | --- |
| `test_tensor_cores_decode.py` | 2,448 | 0 | 0 |
| `test_batch_decode_kernels.py` | 3,180 | 82 | 0 |
| `test_batch_prefill_kernels.py` | 8,791 | 1,329 | 5,760 |

</details>

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

- The cute-dsl and trtllm-gen decode lines were not run here. They need
SM100 or CuTe DSL hardware.
- In vLLM only the prefill lines are on the per-step path.

Generated with Claude Code and Human In The Loop 🙈

---------

Co-authored-by: gf239 <gf239@users.noreply.github.com>

### [87f80a7](https://github.com/flashinfer-ai/flashinfer/commit/87f80a75557b8ff4db77288e39ed40b6aecb9684)

- **作者**: replica
- **时间**: 2026-09-22T16:16:13Z
- **提交信息**: fix(cute-dsl): use has_side_effects to prevent wrong llvm optimisation (#5125)

PLEASE ANALYSE THE ATTACHED ZIP FILES, WHICH IS SELF-CONTAINED. (You can
ask an agent to do it.)


[flashinfer-inline-asm-evidence.zip](https://github.com/user-attachments/files/32085057/flashinfer-inline-asm-evidence.zip)


# [CuTeDSL] Shared-load inline-asm helpers omit effects, allowing
stale-load reuse

`ld_shared_v2_u32` and `ld_shared_v4_u32` read shared memory, but both
emit
`llvm.inline_asm` with `has_side_effects=False`, register-only inputs,
and no
memory clobber. I can demonstrate elimination of a required second read
using
the actual FlashInfer helpers with NVIDIA's public CuTeDSL bindings.

This report concerns the helpers' compiler-visible contract. It does not
claim
that NVIDIA's normal CuTeDSL JIT currently fails the full FlashInfer
test, or
that LLVM is violating the contract it receives.

## Affected source and connection to FlashInfer

Verified at FlashInfer v0.6.18, commit

[`69ff11fc4954396d98326656dc85debd2223f637`](https://github.com/flashinfer-ai/flashinfer/blob/69ff11fc4954396d98326656dc85debd2223f637/flashinfer/cute_dsl/fp4_common.py#L305-L359).
A read-only check of public `main` at

[`40d7876acaf33f3895088cff92698fe2d5c094fe`](https://github.com/flashinfer-ai/flashinfer/blob/40d7876acaf33f3895088cff92698fe2d5c094fe/flashinfer/cute_dsl/fp4_common.py#L305-L359)
found the identical helper file. Runtime results below use the pinned
v0.6.18.

For example, `ld_shared_v4_u32` emits:

```python
"ld.shared.v4.u32 {$0, $1, $2, $3}, [$4];",
"=r,=r,=r,=r,r",
has_side_effects=False,
```

This is used by the [NVFP4 TMA quantization
consumer](https://github.com/flashinfer-ai/flashinfer/blob/69ff11fc4954396d98326656dc85debd2223f637/flashinfer/quantization/kernels/nvfp4_quantize.py#L1300-L1343).
When a pipeline stage is reused, the address may repeat while its
contents change.

The attached evidence repository's `emit_from_flashinfer.py` **calls the
imported
FlashInfer helpers**, using NVIDIA CuTeDSL 4.5.2. It constructs only the
small
surrounding LLVM function and records source hashes. The helper file
SHA-256 is
`a430b3171c7c972a2b98a176e5a47ddcaf36ac71e6231420e961e269d0d045d1`,
matching the
pinned source. No downstream compiler or workaround pass is involved in
emission.
The `.ll` files are obtained by translating this LLVM-dialect MLIR; they
are not
claimed to be NVIDIA full-JIT LLVM IR dumps.

## Minimal reproduction

The test performs:

```text
write A to shared address p
first = FlashInfer.ld_shared_v4_u32(p)
write B to p
second = FlashInfer.ld_shared_v4_u32(p)
return both snapshots
```

Both stores explicitly declare side effects and a memory clobber. The
numerical
check uses one GPU thread and 16-byte-aligned shared storage, removing
TMA and
inter-thread synchronization as confounders.

With the attached repository and the pinned Python packages:

```bash
python -m pytest tests -q            # 2 failures on unpatched v0.6.18
python -m pytest tests -q --patched  # 2 passes with the source flag changed
```

These tests need no GPU or separate LLVM build: they use NVIDIA's own
bundled
`builtin.module(cse)` pass. The baseline emits two loads and CSE leaves
one.
Changing only `has_side_effects` in the two helper definitions preserves
both.
`--patched` applies this source change only in the test process.

A second route translates the same original MLIR **without first running
CSE**:

```bash
mlir-translate --mlir-to-llvmir v4.original.mlir -o before.ll
opt -O2 -S before.ll -o after.ll
llc -O3 -mcpu=sm_80 after.ll -o after.ptx
```

In the recorded LLVM 22.1.6 run, the two calls become one in `GVNPass`,
and the
PTX contains one `ld.shared.v4.u32`. Direct `llc -O3` on `before.ll`
also emits
one load. Version output, binary hashes, pass traces, and both
input/output IR
are included; these CLI binaries are an existing source build, not a
certified
official binary distribution. The NVIDIA-only CSE test is independent of
them.

On B200, the numerical v4 result is:

```text
Expected: [11, 12, 13, 14, 101, 102, 103, 104]
Original: [11, 12, 13, 14,  11,  12,  13,  14]
Patched:  [11, 12, 13, 14, 101, 102, 103, 104]
```

The v2 helper exhibits the same issue. All returned components are
observed, so
this is not deletion of an unused result.

## Proposed change

Set `has_side_effects=True` in both shared-load helpers. The attached
patch changes
only those two lines, and both NVIDIA CSE regression tests pass with
that change.

We also checked adding `~{memory}` alone: it preserves both loads on the
direct
LLVM route, but the tested MLIR CSE still merges them. Thus a
memory-clobber-only
change does not cover both layers. This proposal does not replace
barriers or
claim to audit every ordering requirement; it ensures these hidden
memory reads
are not treated as effect-free operations in the tested paths.

See [LLVM's inline-asm
contract](https://llvm.org/docs/LangRef.html#inline-assembler-expressions)
and [the MLIR
operation](https://mlir.llvm.org/docs/Dialects/LLVM/#llvminline_asm-llvminlineasmop).
The address is passed in an ordinary register, so the PTX spelling of a
load
cannot by itself communicate the memory dependency to generic
optimizations.

## Why existing NVIDIA runs can pass

A passing normal JIT run is useful baseline evidence, but it does not
test every
optimization shape. The recovered original TMA case retained a consumer
loop in
NVIDIA PTX; its four static load sites execute again on subsequent
iterations.
In the alternate pipeline, unrolling exposed repeated stage addresses.
Archived
artifacts show 4 input LLVM load sites, 32 after `opt`, and 16 in final
PTX. A
memory-aware control has 4 → 32 → 32.

That historical elimination occurred during code generation, whereas
this new,
straight-line reproducer also triggers MLIR CSE and LLVM GVN
independently. The
repository labels these as separate experiments and includes sanitized
historical
artifacts as supplementary evidence. The minimized test and source patch
are the
primary basis for this report.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability of shared-memory data loading by ensuring
required load operations are preserved and executed in the correct
order.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: jun.chi <chijun.cj@alibaba-inc.com>

### [963d916](https://github.com/flashinfer-ai/flashinfer/commit/963d916f4c145fd17316a5f3e900b15756ef423a)

- **作者**: eigen
- **时间**: 2026-09-22T11:07:45Z
- **提交信息**: feat(cake_gdn): add Qwen3.5 TP2 seven-token decode rows for SM100 and SM103 (#5378)

## Summary

Add the Qwen3.5-35B-A3B TP=2 speculative-verify rows to the Cake GDN
decode package (`csrc/gdn/cake`) and its selector.

SGLang runs Qwen3.5-35B-A3B with `--tp 2 --speculative-num-draft-tokens
7`; each GDN layer then verifies T=7 tokens per step per rank with H=8 /
HV=16, K=V=128, a BF16 state pool, a seven-step BF16 checkpoint cache,
and `disable_state_update=True`. Those rows fell outside the promoted
table (T≤4, H/HV ∈ {16/32, 16/64, 4/8}) and always took the CuTe BF16
MTP kernel.

- New generated variants (source-only, TVM FFI host shims,
SM100a/SM103a):
- `gdn_decode_pretranspose_t4_bf16state_tile16` with `T_STEPS=7` and
`T_STEPS=8` (H=8/HV=16, strided inputs, cache depth == T) — full-warp
tile-v16 route for B≤4
- `gdn_decode_pretranspose_mtp_t4_bf16state_wide128` with `T_STEPS=7`,
`TILE_V_WIDE=32` for H=8/HV=16 (B≥5) and H=16/HV=32 (TP=1)
- `flashinfer/jit/cake_gdn.py`: promoted rows `(B, 7, 8, 16, strided,
True, True, 7)` for B=1..8, `(1, 8, 8, 16, …, 8)`, `(1, 7, 16, 32, …,
7)`; B≤4 TP2 rows resolve to
`flashinfer.gdn_decode.indexed_bf16_verify_t{T}.tile16_fullwarp`, the
rest to `…verify_t7.wide32`.
- `flashinfer/gdn_decode.py`: derive the launch `tile_v` from the
resolved route (`.tile16_fullwarp` → 16) instead of the hard-coded 4/8
head test; gate the per-call `torch._assert_async` slot validation of
the decode adapters behind `FLASHINFER_CAKE_GDN_VALIDATE_SLOTS=1` (see
Evidence — it cost ~40 us of GPU time per call).
- `tests/gdn/test_cake_gdn_decode_gpu.py`: the isolated invalid-slot
tests set that variable; `csrc/gdn/cake/README.md` documents the
default.

Upstream GPU tests on this branch (B200, same container):
`tests/gdn/test_cake_gdn_decode_gpu.py -k invalid_cuda_slots` 8 passed
(the fail-closed path still trips the device-side assert when enabled,
eager and CUDA graph); the rest of `test_cake_gdn_decode_gpu.py` 64
passed, 2 skipped.
- The same rows are promoted for contiguous inputs
(`strided_inputs=False`, i.e. the `[B, T, H, K]` views SGLang passes)
onto the same `STRIDED_INPUTS=1` variants, mirroring the existing
`bf16_sglang_qwen_tp4_verify_t4_b5_contiguous` row; the T≥7 wide32 route
forces `STRIDED_INPUTS=1` for the same reason.
- Manifest: +4 variants, +20 contract rows (10 strided + 10
`_contiguous`); loader checksum/counts updated.

The generating Cake change (kernels generalized to T≤8, selector,
contract rows, B200 evidence) is Cake MR 823
(https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/823,
CAKE-458).

## Evidence (B200)

Kernel-level, Cake source tree, fixed-101 cold-L2 CUPTI, live CuTe
`gated_delta_rule_mtp` at `8044d94b` as baseline, ABBA×4:

| row | Cake ms | CuTe ms | speedup |
|---|---|---|---|
| TP2 B1/T7 (exact) | 0.007232 | 0.009280 | 1.283x (hot-L2 1.288x, CUDA
Graph 1.266x) |
| TP2 B2/T7 | 0.007744 | 0.009584 | 1.238x |
| TP2 B4/T7 | 0.008959 | 0.010752 | 1.200x |
| TP2 B1/T8 | 0.007808 | 0.009823 | 1.258x |
| TP1 B1/T7 | 0.008528 | 0.009744 | 1.143x |

Both implementations match an independent FP32 sequential oracle at BF16
1e-2/1e-2 with the pool preserved bit-exactly.

Public-API check on this branch
(`gated_delta_rule_decode_pretranspose(..., backend="cake_gdn")` vs
`backend="flashinfer"`): all seven rows (the six new TP2/TP1 rows plus
the pre-existing TP4 `(1, 4, 8, 16, …, 4)` control) pass correctness
against the FP32 sequential oracle at BF16 1e-2/1e-2 with the state pool
preserved bit-exactly, in eager mode and after CUDA-graph capture/replay
(B200, `nvcr.io/nvidia/sglang:26.07-py3`, this branch as a source
overlay, `bench_gpu_time_with_cupti`, cold L2, 3×101 samples):

| row | cake_gdn correct | cake_gdn eager ms | CuTe eager ms | cake_gdn
graph ms | CuTe graph ms | speedup (graph) |
|---|---|---|---|---|---|---|
| B1 H8/HV16 T7 | pass | 0.144960 | 0.009120 | 0.041696 | 0.009184 |
0.220x |
| B2 H8/HV16 T7 | pass | 0.192032 | 0.009600 | 0.050208 | 0.009664 |
0.192x |
| B4 H8/HV16 T7 | pass | 0.140415 | 0.010880 | 0.051104 | 0.011040 |
0.216x |
| B8 H8/HV16 T7 | pass | 0.153215 | 0.012928 | 0.054944 | 0.013024 |
0.237x |
| B1 H8/HV16 T8 | pass | 0.142656 | 0.009920 | 0.052064 | 0.010016 |
0.192x |
| B1 H16/HV32 T7 | pass | 0.160287 | 0.009824 | 0.051808 | 0.009920 |
0.191x |
| B1 H4/HV8 T4 | pass | 0.141216 | 0.005856 | 0.041760 | 0.005984 |
0.143x |

**The `cake_gdn` API path is slower than CuTe on every row, including
the pre-existing TP4 variant, and the cause is not the kernel.** A
per-kernel breakdown of one `backend="cake_gdn"` call (B1 H8/HV16 T7)
shows 15 GPU activities: the Cake kernel itself takes 4.8 us (CuTe: 6.0
us), and the other 14 activities (~40 us of GPU time, ~0.4 ms of eager
span) come from the two `_cake_gdn_assert_state_slots` calls in
`_run_cake_gdn_decode_pretranspose` — each `torch._assert_async(((idx ==
-1) | ((idx >= 0) & (idx < pool)).all())` expands to five elementwise
kernels, a DtoD memcpy and a 9.6 us `_assert_async_cuda_kernel`. Under
CUDA-graph replay the launch gaps disappear but the ~40 us of validation
kernels remain, so the API path measures 0.042 ms against CuTe's 0.009
ms. Stubbing out the two slot-validation calls (measurement only)
confirmed the diagnosis before the fix — same call, one kernel,
kernel-level speedups recovered:

| row | cake_gdn correct | cake_gdn eager ms | CuTe eager ms | cake_gdn
graph ms | CuTe graph ms | speedup (graph) |
|---|---|---|---|---|---|---|
| B1 H8/HV16 T7 | pass | 0.007264 | 0.009120 | 0.007392 | 0.009217 |
1.247x |
| B2 H8/HV16 T7 | pass | 0.007808 | 0.009599 | 0.007904 | 0.009632 |
1.219x |
| B4 H8/HV16 T7 | pass | 0.009024 | 0.010912 | 0.008992 | 0.011008 |
1.224x |
| B8 H8/HV16 T7 | pass | 0.011808 | 0.012896 | 0.011904 | 0.013024 |
1.094x |
| B1 H8/HV16 T8 | pass | 0.007777 | 0.009952 | 0.007840 | 0.010016 |
1.278x |
| B1 H16/HV32 T7 | pass | 0.008608 | 0.009856 | 0.008768 | 0.009952 |
1.135x |
| B1 H4/HV8 T4 | pass | 0.004864 | 0.005887 | 0.004960 | 0.005952 |
1.200x |


This overhead predates this PR (it is upstream behaviour for every
promoted `cake_gdn` decode row), but it decides whether these rows help
or hurt a real server, so this PR also fixes it: the decode adapters now
trust caller-provided slots by default, exactly like the CuTe decode
kernels they replace, and run the asynchronous fail-closed check only
when `FLASHINFER_CAKE_GDN_VALIDATE_SLOTS=1` (the invalid-slot tests set
it). The prefill adapter is unchanged (its kernels run for milliseconds,
so the check is negligible there). The generated kernels are untouched;
moving the range check into the host shim or the kernel itself (which
already reads every slot index) is the longer-term follow-up in the Cake
exporter. Re-measured on the final revision of this branch (default
adapter mode, strided and contiguous inputs) — one kernel per call,
correct and pool-exact in eager and CUDA-graph mode, faster than CuTe on
every promoted row:

| row | cake_gdn correct | cake_gdn eager ms | CuTe eager ms | cake_gdn
graph ms | CuTe graph ms | speedup (graph) |
|---|---|---|---|---|---|---|
| B1 H8/HV16 T7 | pass | 0.007424 | 0.009280 | 0.007488 | 0.009344 |
1.248x |
| B1 H8/HV16 T7 contiguous | pass | 0.007360 | 0.009344 | 0.007520 |
0.009440 | 1.255x |
| B2 H8/HV16 T7 | pass | 0.007903 | 0.009760 | 0.007905 | 0.009792 |
1.239x |
| B2 H8/HV16 T7 contiguous | pass | 0.008000 | 0.009920 | 0.008064 |
0.010016 | 1.242x |
| B4 H8/HV16 T7 | pass | 0.008992 | 0.011008 | 0.009056 | 0.011136 |
1.230x |
| B4 H8/HV16 T7 contiguous | pass | 0.009024 | 0.010849 | 0.009056 |
0.010976 | 1.212x |
| B8 H8/HV16 T7 | pass | 0.011872 | 0.012992 | 0.011968 | 0.013183 |
1.102x |
| B8 H8/HV16 T7 contiguous | pass | 0.011776 | 0.012864 | 0.011967 |
0.013088 | 1.094x |
| B1 H8/HV16 T8 | pass | 0.007935 | 0.010176 | 0.008032 | 0.010304 |
1.283x |
| B1 H8/HV16 T8 contiguous | pass | 0.007936 | 0.010080 | 0.008096 |
0.010207 | 1.261x |
| B1 H16/HV32 T7 | pass | 0.008800 | 0.010016 | 0.008832 | 0.010113 |
1.145x |
| B1 H16/HV32 T7 contiguous | pass | 0.008736 | 0.009952 | 0.008832 |
0.010080 | 1.141x |
| B1 H4/HV8 T4 | pass | 0.004896 | 0.005792 | 0.004929 | 0.005920 |
1.201x |
| B1 H4/HV8 T4 contiguous | not promoted upstream (fails closed, as
before this PR) | | 0.005984 | | 0.006048 | |


## End-to-end (2×B200 TP=2, SGLang 0.5.14 + this branch as source
overlay)

`Qwen/Qwen3.5-35B-A3B`, `--tp 2 --speculative-algorithm NEXTN
--speculative-num-steps 6 --speculative-eagle-topk 1
--speculative-num-draft-tokens 7 --mamba-ssm-dtype bfloat16`,
`bench_serving` random ISL 60000 / OSL 400, 4 prompts, concurrency 1,
second repetition (first repetition includes JIT/graph warm-up), same
node.

Two SGLang-side facts gate this comparison and are **not** fixed by this
PR:

1. SGLang's FlashInfer GDN `target_verify` calls
`flashinfer.gdn_kernels.gdn_decode_bf16_state.gated_delta_rule_mtp`
directly on SM100, never reaching `gated_delta_rule_decode_pretranspose`
and its `backend="auto"` Cake dispatch. Both arms below therefore run a
measurement shim that routes verify through the public API
(`SGLANG_GDN_VERIFY_VIA_PRETRANSPOSE=1`).
2. SGLang passes contiguous `q/k/v` views, which the selector keys as
`strided_inputs=False` — the first revision of this branch only promoted
the strided keys and silently fell back to CuTe in serving; the
contiguous twins are now promoted (see Summary).
3. SGLang passes `dt_bias` as BF16; the Cake decode contract requires
FP32 `A_log`/`dt_bias` (the CuTe kernel accepts BF16), so without a
`dt_bias.float()` the auto dispatch silently falls back to CuTe. The
shim casts it (SGLang would cache the FP32 copy once per layer).

| metric (rep 2, concurrency 1) | baseline (CuTe verify) | Cake rows
(this PR) | delta |
|---|---|---|---|
| Median TPOT (ms) | 0.96 | 0.80 | -16.7% |
| Mean TPOT (ms) | 0.96 | 0.81 | -15.6% |
| Median ITL (ms) | 0.96 | 0.78 | -18.7% |
| Median E2E latency (ms) | 656.96 | 597.29 | -9.1% |
| Output token throughput (tok/s) | 513.93 | 557.18 | +8.4% |
| Accept length | 6.02 | 6.90 | +14.6% |

Both arms ran on the same 2×B200 node (allocation 2017306) with shared
FlashInfer JIT and autotune caches; the Cake arm's server log shows
`decode_gdn_decode_pretranspose_t4_bf16state_tile16_16e0085ad1e7`
selected for every B≤4 verify call and the wide32 variant for the B≥5
CUDA-graph captures (`CAKE_GDN_ROUTE` lines), the baseline arm none.
Accept length differs between the arms although both prompts/decoding
are deterministic (greedy, seed 42): the two verify kernels accumulate
in different orders and the random-token prompts make the target argmax
fragile, so per-token acceptance flips; both kernels match the FP32
oracle at BF16 1e-2 on these exact shapes (above). A controlled check on
real prompts with `--output-details` is the follow-up before reading
anything into the accept-length gap.

The GDN verify kernel is ~30 launches of 5–9 us inside a ~5 ms
speculative step (accept length 6.0 of 7), so the kernel-level 1.25x is
at most ~1% of TPOT and below the run-to-run noise of this benchmark;
the e2e result is a correctness/route check, not a speedup claim.

## Not covered

- `compute-sanitizer` was not available in the validation container; the
new rows are covered by the same host-shim shape/stride contracts as the
existing tile16/wide128 variants.
- sm_103a numbers are pending.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added optimized BF16 GDN decode paths for Qwen3.5 speculative
verification across additional batch sizes and supported hardware.
- Added specialized tiled and wide-state decoding options, with
automatic route selection.

- **Bug Fixes**
- Invalid state slots now safely fall back for reads while preventing
invalid state, intermediate-state, and output writes.

- **Documentation**
- Updated slot-validation behavior, performance considerations, and
supported decode configurations.

- **Configuration**
- Decode slot validation remains disabled by default and can be enabled
with `FLASHINFER_CAKE_GDN_VALIDATE_SLOTS=1`.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4496
- **最后更新**: 2026-09-22T03:27:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34581
- **最后更新**: 2026-09-22T21:49:54Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Nianze Wu

## AI分析总结

针对仓库 'huggingface/diffusers' 昨日提交记录“Fix Wuerstchen LoRA scheduler steps for distributed epochs”的分析总结如下：

1.  **主要更新类型**：**Bug修复**。该提交专门解决了一个在特定模型（Wuerstchen）与特定微调方法（LoRA）结合进行分布式训练时出现的技术问题。

2.  **关键变更点及其关系**：核心修复是**校正了LoRA训练场景下调度器（scheduler）的步数（steps）在分布式训练环境中的缩放计算**。这直接关系到Diffusers项目的核心目标之一：为用户提供**稳定、可靠且易于扩展**的扩散模型训练与推理工具。该修复确保了在使用多GPU进行大规模、长周期（distributed epochs）微调时，模型能遵循正确的去噪流程，避免因步数计算错误导致的训练不稳定或质量下降。

3.  **对项目的影响和潜在意义**：此次修复提升了Wuerstchen模型与LoRA技术结合使用的**可靠性和生产就绪度**。对于需要利用分布式训练来加速大型模型微调的用户和研究者而言，这是一个重要的稳定性保障。它潜在地**鼓励了更广泛的社区采用这种高效的微调组合**，从而促进在该架构上进行更多的定制化生成模型开发。

4.  **值得关注的技术点**：该修复揭示了在**分布式深度学习训练框架**下，将模型组件（如调度器）与训练循环（特别是涉及LoRA这种适配器的方法）正确集成的复杂性。确保全局训练步数与模型内部调度步数同步是一个关键且容易出错的技术点，此次修复体现了项目维护者对分布式训练场景的深入关注和优化。

5.  **对项目发展的意义**：从README可知，Diffusers致力于提供顶尖的生成式AI工具。此次看似微小的Bug修复，实则是**维护工具包核心价值——“可靠易用”——的重要实践**。它表明项目团队不仅在积极添加新功能，更在持续夯实现有功能的稳定性，尤其是在高级、高性能的使用场景（如分布式LoRA微调）下。这种对细节和边缘情况的打磨，有助于巩固Diffusers作为扩散模型领域标准工具包的地位，确保其生态系统的稳健发展。

## 详细提交记录

### [8b3c707](https://github.com/huggingface/diffusers/commit/8b3c707ebd3ec4881f4190cf42931da07eaf3b65)

- **作者**: Nianze Wu
- **时间**: 2026-09-22T08:56:27Z
- **提交信息**: Fix Wuerstchen LoRA scheduler steps for distributed epochs (#14748)

Fix Wuerstchen LoRA scheduler step scaling

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-08-31T08:28:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13168
- **最后更新**: 2026-09-22T23:28:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36332
- **最后更新**: 2026-09-22T23:48:50Z

## 提交统计

- **昨日提交总数**: 47
- **提交者数量**: 37
- **主要提交者**: Yuwei An, pllimax, tom.jen

## AI分析总结

### 主要更新类型
*   **硬件支持与优化**：大量提交聚焦于AMD（ROCm）平台的特性启用、性能优化与Day 0支持（如GLM-5.3-Flash模型、EAGLE投机解码、DSA索引器等），同时扩展了对NVIDIA新硬件（GB200/GB300）的支持。
*   **内存与缓存系统重构**：对内存缓存（`mem_cache`）进行了重要清理，移除了实验性C++基数树、未使用的`HiRadixCache`及统一基数树的旧代码，旨在简化架构、减少维护负担。
*   **分布式推理与服务稳定性**：增强了PD（推测为Prefill-Decode）分离架构的健壮性（如处理KV传输、异常中止），并改进了Router/Worker的资源隔离（`CUDA_VISIBLE_DEVICES`）。
*   **模型与功能适配**：修复了与特定模型（如DeepSeek DSML）和功能（如函数调用、分块MQA元数据）相关的Bug，并新增了对离线引擎API的tokenizer多线程支持。
*   **文档与CI**：更新了快速启动指南、基准测试表格，并为渲染器（Renderer）组件配置了独立的CI流水线。

### 关键变更点及其与项目整体方向的关系
1.  **AMD平台的深度适配**：提交数量众多且具体，表明sglang正积极扩大其硬件生态，降低对单一硬件的依赖，这对开源框架的普及至关重要。
2.  **缓存架构的简化与统一**：移除实验性代码和遗留功能，是项目走向成熟、代码库更清晰可维护的标志，有助于集中资源优化核心性能。
3.  **分布式系统的可靠性增强**：PD相关修复和Worker隔离改进，直接关系到大规模在线服务的稳定性，是项目向生产环境迈进的关键一步。

### 对项目的影响和潜在意义
*   **提升硬件兼容性**：增强了在AMD GPU上部署和运行大模型的能力，为用户提供了更多选择。
*   **代码库健康度提升**：通过清理冗余和实验性代码，降低了技术债，使项目结构更清晰。
*   **服务可靠性增强**：分布式推理和内存管理方面的修复，有助于在实际生产环境中提供更稳定、高效的服务。
*   **开发者体验改善**：文档更新和CI流程完善，降低了新用户的上手门槛和贡献者的协作成本。

### 值得关注的技术点
*   **性能优化细节**：如FP4索引器跳过不可见tiles、复用KV gather索引、避免主机同步等，体现了对推理效率的极致追求。
*   **架构设计选择**：选择移除实验性的C++基数树并清理相关代码，显示了项目在长期维护和短期特性之间的权衡。
*   **资源隔离机制**：确保e2e workers严格运行在分配的`CUDA_VISIBLE_DEVICES`内，是多租户或混合部署场景下的重要保障。
*   **新硬件支持**：为SM120 GPU添加FP8注意力后端、支持零RoPE TileLang DSA等，展示了框架对未来硬件趋势的跟进。

### 基于项目背景的提交影响
SgLang作为一个致力于提供高效大模型推理服务的开源框架，本次提交批量显著推动了其项目目标的实现。**广泛且深入的AMD硬件支持**直接扩展了其目标用户群和部署场景。**内存与缓存系统的重构**旨在为高性能和稳定性打下更坚实的代码基础。**分布式推理服务的多项修复**则是在实际生产验证中不断打磨产品可靠性的体现。总体而言，这些提交共同推动SgLang从一个功能丰富的框架，向一个**支持广泛硬件、架构清晰、服务稳定可靠的生产级推理平台**演进。

## 详细提交记录

### [06008c1](https://github.com/sgl-project/sglang/commit/06008c170dae333e22caceb51f36224071f9b5b3)

- **作者**: Qi Sun
- **时间**: 2026-09-22T23:48:43Z
- **提交信息**: [dsv4.1]Optimize FP4 indexer by skipping invisible tiles (#40431)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [4ce2354](https://github.com/sgl-project/sglang/commit/4ce23542bfc9efa82487594ef9ac952356032a20)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-22T23:17:12Z
- **提交信息**: [HiCache] Remove the unused HiRadixCache (#40787)

### [7b977ce](https://github.com/sgl-project/sglang/commit/7b977ce5dcce6e61f0a5f8ef8b4235e42eb00299)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-22T23:02:17Z
- **提交信息**: [Fix] Decide the MoE padded-row bound from the layer scatter mode (#40672)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [d34f7b2](https://github.com/sgl-project/sglang/commit/d34f7b2326a10cb5f3ba8ec95efb31c761237750)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-22T22:40:57Z
- **提交信息**: [mem_cache] Clean up SWA/Mamba radix cache leftovers and drop SGLANG_ENABLE_UNIFIED_RADIX_TREE (#40780)

### [19ee4b5](https://github.com/sgl-project/sglang/commit/19ee4b566b142aee0299417f50cc65e80293bd39)

- **作者**: Kevin Flansburg
- **时间**: 2026-09-22T22:38:44Z
- **提交信息**: fix(function_call): buffer complete DeepSeek DSML invokes (#39632)

Co-authored-by: Xinyuan Tong <justintong0323@gmail.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [b77833c](https://github.com/sgl-project/sglang/commit/b77833c5046238f4aae8074e006c4fdd19016c9d)

- **作者**: Jialin Ouyang
- **时间**: 2026-09-22T22:12:07Z
- **提交信息**: [MM] Keep scheduler padding in packed token arrays (#40357)

### [c19dc43](https://github.com/sgl-project/sglang/commit/c19dc43cc732a3a7e9b487ba26f4af866cbe620b)

- **作者**: Jacob0226
- **时间**: 2026-09-22T22:07:51Z
- **提交信息**: [AMD] [GLM-5.3-Flash Day 0] Load the MXFP4 MTP draft layer (#39779)

Co-authored-by: Thomas Wang <thomawan@amd.com>
Co-authored-by: CHANG <jacchang@crsuse2-slog-003.us-east2-a.compute.internal>
Co-authored-by: Kevin Mi <mikevin920@yahoo.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>

### [01275aa](https://github.com/sgl-project/sglang/commit/01275aab6b2075d3525bcf7423f454fce7f21718)

- **作者**: jain-ria
- **时间**: 2026-09-22T21:57:38Z
- **提交信息**: fix(grpc): expose native response timeout as a server argument (#40644)

Signed-off-by: jain-ria <riajain@NVIDIA.com>

### [9a53f75](https://github.com/sgl-project/sglang/commit/9a53f7512445218b7613682c0a2eff9fe04d5723)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-22T21:19:45Z
- **提交信息**: [mem_cache] Remove the experimental C++ radix tree (#40775)

### [d72629e](https://github.com/sgl-project/sglang/commit/d72629e4badee54bfba1817e781d7f940bdfc6ae)

- **作者**: Faradawn Yang
- **时间**: 2026-09-22T21:16:43Z
- **提交信息**: Add GB200/GB300 hardware to Qwen3.5 (#40770)

Signed-off-by: Faradawn Yang <73060648+faradawn@users.noreply.github.com>

### [c08ffef](https://github.com/sgl-project/sglang/commit/c08ffef70904e2c523a381b0351c1178c9d686da)

- **作者**: sglang-bot
- **时间**: 2026-09-22T21:14:07Z
- **提交信息**: docs: sync LMSYS SGLang blog cards (#40655)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [542c817](https://github.com/sgl-project/sglang/commit/542c817bfae2d9c49c284a26be882db57ce939d0)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-22T21:07:47Z
- **提交信息**: [Docs] Fix benchmark table column overflow in cookbook deployment panel (#40114)

Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>

### [3afdde5](https://github.com/sgl-project/sglang/commit/3afdde5f0548c953b31fe4d9f9082dac0801e279)

- **作者**: Jacob0226
- **时间**: 2026-09-22T20:14:30Z
- **提交信息**: [AMD] [GLM-5.3-Flash Day 0] Enable the k-pool DSA indexer on gfx950 (#39341)

Co-authored-by: Yikai Zhang <ykzhang12@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Raiden-Makoto <Raiden-Makoto@users.noreply.github.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>
Co-authored-by: Kevin Mi <mikevin920@yahoo.com>

### [077c319](https://github.com/sgl-project/sglang/commit/077c31991406d09d0dd70a9e5cb6934fcaa818a3)

- **作者**: Jacob0226
- **时间**: 2026-09-22T20:10:39Z
- **提交信息**: [AMD] [GLM-5.3-Flash Day 0] Enable speculative decoding (MTP) on ROCm (#39778)

Co-authored-by: Thomas Wang <thomawan@amd.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>

### [d6cc283](https://github.com/sgl-project/sglang/commit/d6cc283da704e2254ac27cc7cabe105c29196672)

- **作者**: Raiden Makoto
- **时间**: 2026-09-22T20:08:25Z
- **提交信息**: [AMD] [GLM-5.3-Flash Day 0] Enable zero-RoPE TileLang DSA on gfx950 (#38547)

Co-authored-by: Raiden-Makoto <Raiden-Makoto@users.noreply.github.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>
Co-authored-by: Kevin Mi <mikevin920@yahoo.com>
Co-authored-by: Kevin Mi <kevin.mi@radixark.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4cbf290](https://github.com/sgl-project/sglang/commit/4cbf290fb9e71518f1f8f133025f507d69f9b409)

- **作者**: Yuwei An
- **时间**: 2026-09-22T19:59:04Z
- **提交信息**: [Fix] Handle chunked paged MQA metadata in DSV4.1 eager forwards (#40637)

### [720617b](https://github.com/sgl-project/sglang/commit/720617bb5bc73676473a3dd650dae8a8c8e9d48b)

- **作者**: zijie
- **时间**: 2026-09-22T19:08:05Z
- **提交信息**: [AMD] Reuse KV gather indices across ASM context prefill layers (#39901)

Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>

### [5c18780](https://github.com/sgl-project/sglang/commit/5c18780c31d6b0116a91ba4c3c1d31a6e3cedb8f)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-22T18:32:12Z
- **提交信息**: [Router] Keep e2e workers inside the job's CUDA_VISIBLE_DEVICES allotment (#40686)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [db73f35](https://github.com/sgl-project/sglang/commit/db73f35f4a52b6492491d55986d3ac573669ac01)

- **作者**: Cheng Wan
- **时间**: 2026-09-22T18:22:07Z
- **提交信息**: Fix the Inkling per-expert sync test and collect it in the weekly CPU run (#40725)

### [6f4c2b9](https://github.com/sgl-project/sglang/commit/6f4c2b9b91ec06a45496145ae901149142e1fb4d)

- **作者**: Shangming Cai
- **时间**: 2026-09-22T18:18:58Z
- **提交信息**: [HiCache] Demote internal-node mamba states on write_back eviction (#40680)

### [91c329c](https://github.com/sgl-project/sglang/commit/91c329cc866957a4750a929d158978a3ac69f45d)

- **作者**: Cheng Wan
- **时间**: 2026-09-22T17:55:21Z
- **提交信息**: Take the model config out of the parallel group build, and finish retiring the parallel getters (#40707)

### [66454d7](https://github.com/sgl-project/sglang/commit/66454d704b85c77c11e24297ce3ac05efdf43302)

- **作者**: Pei Li
- **时间**: 2026-09-22T17:50:01Z
- **提交信息**: [Feature] Support --tokenizer-worker-num > 1 in the offline Engine API (#40260)

### [b4701d6](https://github.com/sgl-project/sglang/commit/b4701d672d03752bc3578d67459174caf15b5cba)

- **作者**: Sage
- **时间**: 2026-09-22T17:48:28Z
- **提交信息**: [rust-renderer] decouple renderer sampling from protocols (#40747)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [8ab21c8](https://github.com/sgl-project/sglang/commit/8ab21c8a942b014b2c8b56223f83de1ba75b1f8f)

- **作者**: Sage
- **时间**: 2026-09-22T16:48:12Z
- **提交信息**: [ci] publish renderer image (#40639)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [a7b96fd](https://github.com/sgl-project/sglang/commit/a7b96fdad781d667e17d6145a10aa8714cb90fbf)

- **作者**: Sage
- **时间**: 2026-09-22T16:47:48Z
- **提交信息**: [ci] run cpu ci for renderer-only changes (#40636)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [6fd98c9](https://github.com/sgl-project/sglang/commit/6fd98c98b95f12b8e88b07dfa917581936c87376)

- **作者**: YAMY
- **时间**: 2026-09-22T15:46:44Z
- **提交信息**: [Qwen3.8-Next] Pipeline-parallel serving and PD-prefill MTP for Qwen4-Exp (#40501)

Co-authored-by: zhangxiaolei <zhangxiaolei.666@bytedance.com>

### [c79510c](https://github.com/sgl-project/sglang/commit/c79510cc2a334191ef515b99127420491795b841)

- **作者**: Yuan Luo
- **时间**: 2026-09-22T14:06:06Z
- **提交信息**: [DSv4.1] Score prefill consumer index layers on candidate blocks with DeepGEMM (#40352)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>
Co-authored-by: DarkSharpness <76582120+DarkSharpness@users.noreply.github.com>

### [4a1b69a](https://github.com/sgl-project/sglang/commit/4a1b69abc87f7cc3e2b82985791ffff0de613e37)

- **作者**: Mick
- **时间**: 2026-09-22T12:32:59Z
- **提交信息**: [diffusion] docs: correct the resident-layer help text to match its scope (#40593)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [244db08](https://github.com/sgl-project/sglang/commit/244db08d60cc05275f71079fba0dabc2bbde1eb9)

- **作者**: pllimax
- **时间**: 2026-09-22T12:15:11Z
- **提交信息**: [NPU][CI] Constrain evalscope dependency versions (#40133)

### [bc3a63e](https://github.com/sgl-project/sglang/commit/bc3a63ebdbd0420f763d246408e43b404517b530)

- **作者**: Wookje Han
- **时间**: 2026-09-22T12:11:40Z
- **提交信息**: [Fix] Missing SWA eviction during decode preallocation (#40309)

### [ddebc52](https://github.com/sgl-project/sglang/commit/ddebc52f237a1dbb56533469ab2ec2a7b856c4ab)

- **作者**: Shunkangz
- **时间**: 2026-09-22T11:57:44Z
- **提交信息**: [kv-shard 3/4] Enable Control plane (#38468)

### [2524b61](https://github.com/sgl-project/sglang/commit/2524b61f9b7f58342031207611d43991897e176e)

- **作者**: Mick
- **时间**: 2026-09-22T11:56:21Z
- **提交信息**: [diffusion] feat: allow a component use retain its layerwise resident set (#40592)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [861b11f](https://github.com/sgl-project/sglang/commit/861b11f087af2822cb545ea1895059a721831014)

- **作者**: Shangming Cai
- **时间**: 2026-09-22T11:08:47Z
- **提交信息**: [PD] Simplify late-abort quiescent ack branch to else (#40711)

### [cb8dab0](https://github.com/sgl-project/sglang/commit/cb8dab06be6f7d708bccf4d4e955780642daba8b)

- **作者**: amote-i
- **时间**: 2026-09-22T11:04:17Z
- **提交信息**: [NPU] [DOC] Remove duplicated features in npu docs (#40714)

### [8ef6d31](https://github.com/sgl-project/sglang/commit/8ef6d31cb9c1a2e1fb0adb0a39e207e1b8142f96)

- **作者**: cctry
- **时间**: 2026-09-22T10:46:07Z
- **提交信息**: [PD] Preserve abort ACKs until in-flight KV transfers drain (#40645)

### [9d58189](https://github.com/sgl-project/sglang/commit/9d58189c12e4e14a7eea20f24f9aa7b17e221778)

- **作者**: Emre Albayrak
- **时间**: 2026-09-22T09:44:37Z
- **提交信息**: [diffusion] attention: add fp8_fa_sm120 FP8 backend for SM120 GPUs (#40175)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [debbb5c](https://github.com/sgl-project/sglang/commit/debbb5cde984f21ef4909c007c69ab44e151f95a)

- **作者**: siliangchen-amd
- **时间**: 2026-09-22T09:43:31Z
- **提交信息**: [AMD] Drop the redundant scale zero-fill before AITER per-tensor FP8 quant (#40557)

Co-authored-by: siliangchen-amd <{"message":"Although you appear to have the correct authorization credentials, the `amd-eng-emu` enterprise has an IP allow list enabled, and your IP address is not permitted to access this resource.","documentation_url":"https://docs.github.com/rest/users/users#get-the-authenticated-user","status":"403"}siliangchen-amd@users.noreply.github.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [3f00fb7](https://github.com/sgl-project/sglang/commit/3f00fb7e2ef2fe54ef84be1fbb130c9f8276586f)

- **作者**: Michael
- **时间**: 2026-09-22T09:16:31Z
- **提交信息**: [AMD] Register unified KV page-zeroing test in PR CI (#40123)

### [70a2bb2](https://github.com/sgl-project/sglang/commit/70a2bb2a303d9f56958cc66b74cb00dafc12ba41)

- **作者**: Zhaoyi Li
- **时间**: 2026-09-22T09:15:18Z
- **提交信息**: [AMD][DI] Keep loopback in UCX_NET_DEVICES (#40641)

### [790551c](https://github.com/sgl-project/sglang/commit/790551c38230d025bc8bdff5f26278a2380aed7a)

- **作者**: jacky.cheng
- **时间**: 2026-09-22T08:57:37Z
- **提交信息**: [AMD] Skip full-vocab softmax in EAGLE topk==1 draft on ROCm (#35872)

Co-authored-by: chuyeh <chuyeh@users.noreply.github.com>

### [c2f14bf](https://github.com/sgl-project/sglang/commit/c2f14bfbc4e82ade955c4dacfaefd8e0a19abddf)

- **作者**: chuyeh
- **时间**: 2026-09-22T08:49:59Z
- **提交信息**: [AMD] Use exact CU share for gfx950 segment-plan headroom (#39503)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [367e370](https://github.com/sgl-project/sglang/commit/367e3700cfb6a0b03b2fa41a4524febf18ec1f15)

- **作者**: inkcherry
- **时间**: 2026-09-22T08:20:49Z
- **提交信息**: avoid host sync in DSpark prefill slot expansion (#40111)

### [d00adfd](https://github.com/sgl-project/sglang/commit/d00adfd19cb6ea56de2f2fe814924f0c9a1664f8)

- **作者**: tom.jen
- **时间**: 2026-09-22T08:07:25Z
- **提交信息**: [AMD] Fix deferred Kimi-K3 forget gate in fused in-projection (#39525)

Co-authored-by: Tom Jen <tomjen12@localhost.localdomain>
Co-authored-by: HAI <hixiao@gmail.com>

### [6412ad8](https://github.com/sgl-project/sglang/commit/6412ad8c6481db616cac8b7095fe336bcd708562)

- **作者**: zijie
- **时间**: 2026-09-22T07:52:40Z
- **提交信息**: [AMD] Pack Qwen3.5 GDN input projections on ROCm (#39902)

Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>

### [771c9d7](https://github.com/sgl-project/sglang/commit/771c9d782d9ecf0324e70b7f5a08c32644d652c5)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-09-22T07:12:29Z
- **提交信息**: [PD] Validate Mooncake EFA allocator compatibility (#39973)

### [1815e49](https://github.com/sgl-project/sglang/commit/1815e490de39707d4e5f37af9f1203bc761ca87f)

- **作者**: Suraj
- **时间**: 2026-09-22T07:08:01Z
- **提交信息**: [observability] Fix negative queue_time for retracted requests (#39312)

### [c948114](https://github.com/sgl-project/sglang/commit/c948114d58dcd192ec32c81cd88ae12bbc5179dc)

- **作者**: jshn9515
- **时间**: 2026-09-22T07:00:35Z
- **提交信息**: [DOC] Update quickstart guide to use `sglang serve` for launching the server (#40647)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1284
- **最后更新**: 2026-09-21T06:50:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92452
- **最后更新**: 2026-09-23T00:31:15Z

## 提交统计

- **昨日提交总数**: 40
- **提交者数量**: 34
- **主要提交者**: Juntian Liu, Jack Hu, Divakar Verma

## AI分析总结

基于vLLm项目“提供简单、快速且低成本的LLM服务”的核心目标，昨日的40次提交主要围绕**平台兼容性增强、系统稳定性与性能优化**展开，具体总结如下：

1.  **主要更新类型**：
    *   **平台支持与优化**：大量提交集中在[ROCm]平台，涵盖内核实现、构建镜像、CI测试修复等，旨在提升AMD硬件的可用性与性能。
    *   **Bug修复**：提交数量最多的类型，涉及多个核心组件（如结构化输出、Speculative Decoding、模型加载、注意力计算）的正确性问题。
    *   **性能优化**：包含消除同步、融合计算内核、优化显存管理等，旨在提升推理速度和资源利用率。
    *   **功能新增**：包括对新模型架构的支持（如DiffusionGemma）、数据并行权重缓存等新能力。
    *   **重构与CI改进**：清理代码、调整测试策略以提升代码质量和构建稳定性。

2.  **关键变更点及其与项目方向的关系**：
    *   **ROCm生态全面增强**：从底层内核（如`silu_and_mul`、稀疏注意力）到高层功能（MXFP4/MXFP8支持），再到构建（Triton版本升级）和CI，系统性提升了vLLM在AMD GPU上的生产就绪度，与项目“为所有人提供服务”的普惠性目标一致。
    *   **结构化输出与Speculative Decoding的健壮性提升**：修复了多个导致错误输出或请求被错误拒绝的bug（如空tag验证、并发调度限制、语法轮询阻塞），确保了这些核心特性在生产环境中的可靠性，服务于“低成本”和“易用性”。
    *   **性能与资源管理优化**：通过融合内核（如逆RoPE）、消除CPU-GPU同步、优化权重卸载等手段，直接降低了推理延迟和内存开销，紧扣“快速、低成本”的项目目标。

3.  **对项目的影响和潜在意义**：
    *   **扩大硬件支持范围与稳定性**：显著提升了vLLM对AMD ROCm平台的支持深度和广度，有助于降低用户硬件成本，扩大项目适用场景。
    *   **提升服务整体质量与用户体验**：大量Bug修复增强了系统在不同配置（如多卡、异构模型）下的稳定性和输出正确性，降低了用户的使用和调试门槛。
    *   **巩固核心技术优势**：在投机解码、结构化生成等先进特性上的持续优化，保持了vLLM在推理效率方面的技术领先地位。

4.  **值得关注的技术点**：
    *   **计算内核融合**：例如将逆RoPE计算融合到稀疏解码的reduce操作中（#57435），以及MXFP8权重GEMM与序列并行reduce-scatter的融合（#57428），展示了对底层算子的深度优化。
    *   **平台适配技巧**：在ROCm上为不同操作（如SoftCap、FP8量化）提供CUDA回退实现或平台特定范围（#58136, #58153），是保证跨平台功能一致性的常见模式。
    *   **并发与同步控制**：修复结构化输出语法轮询的阻塞问题（#55931）和保持`batch_invariant`下特定集合通信的启用（#58179），体现了对多线程、分布式计算中复杂状态管理的重视。

5.  **对项目发展的影响**：
    这些提交共同推动vLLM朝着一个**更健壮、更跨平台、更高性能**的生产级LLM服务引擎发展。通过持续修复边界条件下的bug和优化关键路径，项目在“易用性”和“可靠性”上打下了更坚实的基础。同时，对AMD等新平台的大力投入，直接响应了市场对多样化、低成本算力的需求，有望加速项目在更广泛用户群体中的普及，与其“为所有人提供服务”的愿景高度契合。

## 详细提交记录

### [d110c2f](https://github.com/vllm-project/vllm/commit/d110c2f19c4f47b92b2dbce2ab24f2014589bf0c)

- **作者**: Tres
- **时间**: 2026-09-22T23:30:14Z
- **提交信息**: [ROCm] Use silu_and_mul_with_clamp's torch._C op (#52052)

Signed-off-by: Tres Popp <tres.popp@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [1c0eee9](https://github.com/vllm-project/vllm/commit/1c0eee919db320ea3e2df37f800465c7842a650a)

- **作者**: Jack Hu
- **时间**: 2026-09-22T23:08:51Z
- **提交信息**: [ROCm][Model][Bugfix] Enable GLM-5.2-MXFP4 on the deepseek_v32 path and fix sparse attention correctness (#51915)

Signed-off-by: Jack Hu <Jack.Hu@amd.com>
Signed-off-by: Jack Hu <jack.hu@amd.com>
Signed-off-by: Douglas Lehr <Doug.Lehr@amd.com>
Co-authored-by: James E T Smith <jamesETsmith@users.noreply.github.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: Douglas Lehr <Doug.Lehr@amd.com>

### [9646f53](https://github.com/vllm-project/vllm/commit/9646f5306475d95de6baf03a81da4203f30928a8)

- **作者**: stefankoncarevic
- **时间**: 2026-09-22T23:05:33Z
- **提交信息**: [Bugfix][ROCm] Use the platform FP8 range in the concat MLA q test (#58153)

Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [111d7d7](https://github.com/vllm-project/vllm/commit/111d7d7be2d4cfa439ac0e0cbd2b14a474bfab6e)

- **作者**: rasmith
- **时间**: 2026-09-22T23:05:13Z
- **提交信息**: [ROCm][Build][The Rock] Bump Triton version to 3.8.x tip-of-tree with source build in The Rock image (#58006)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>

### [d421a2e](https://github.com/vllm-project/vllm/commit/d421a2e8fc0fd17c46c131d5c0884af5cf075fca)

- **作者**: Michael Lapshin
- **时间**: 2026-09-22T22:34:19Z
- **提交信息**: [Perf] Remove CPU-GPU sync in heterogeneous vocabulary speculative decoding (#57396)

### [4edb551](https://github.com/vllm-project/vllm/commit/4edb55169f69c76bb87ab9f154585917cb01bb17)

- **作者**: Thang Nguyen
- **时间**: 2026-09-22T21:50:18Z
- **提交信息**: [CI] Shard (H200 MIG 18GB) Spec Decode Draft Model across whole-directory replicas (#58193)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [4ec0b95](https://github.com/vllm-project/vllm/commit/4ec0b95c447fe70b92b2d12164c31255bb178e21)

- **作者**: Thang Nguyen
- **时间**: 2026-09-22T21:49:06Z
- **提交信息**: [CI] Split LM Eval TurboQuant KV Cache into per-config jobs (#57113)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Kimi <noreply@moonshot.ai>

### [5c3b61e](https://github.com/vllm-project/vllm/commit/5c3b61e9c438a605b52d6d1c2639b2dcb5bbf575)

- **作者**: Misha Goin
- **时间**: 2026-09-22T21:35:23Z
- **提交信息**: [Core] Disable JIT warmup in eager mode (#58197)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [01e15bc](https://github.com/vllm-project/vllm/commit/01e15bc94cd29cd1fcbbab484e96acb5b4f6bb14)

- **作者**: Misha Goin
- **时间**: 2026-09-22T21:26:49Z
- **提交信息**: [Bugfix] Backport Inductor custom-op pattern matching fix (#58189)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [ecdd11d](https://github.com/vllm-project/vllm/commit/ecdd11d0e0a84d73d3c1348d4f37317c5140d32a)

- **作者**: Andrey Talman
- **时间**: 2026-09-22T21:15:57Z
- **提交信息**: [CI] Build the torch-nightly image on Ubuntu 24.04 (#58204)

### [25965ee](https://github.com/vllm-project/vllm/commit/25965ee583b154c0ce356466d4cf2d25f6815c60)

- **作者**: Misha Goin
- **时间**: 2026-09-22T21:07:34Z
- **提交信息**: [Kernel] Remove AllSpark INT8 W8A16 GEMM backend (#58001)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [1b3b88e](https://github.com/vllm-project/vllm/commit/1b3b88ec2b7457aa030db4d0e7d8aaf04f6d0fb8)

- **作者**: Matt Mastracci
- **时间**: 2026-09-22T20:51:17Z
- **提交信息**: [Core] structured generation mode for DiffusionGemma model (Jev-like) (#57250)

Signed-off-by: Matt Mastracci <matthew@mastracci.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Signed-off-by: Razorback16 <razorback16@protonmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Razorback16 <razorback16@protonmail.com>

### [fae5cbf](https://github.com/vllm-project/vllm/commit/fae5cbfc8b7e957c891ad88881969f3a41de065e)

- **作者**: Wentao Ye
- **时间**: 2026-09-22T20:36:03Z
- **提交信息**: [Refactor] Remove dead code multiple places (#58002)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [276db94](https://github.com/vllm-project/vllm/commit/276db94fb22f032a933c3c17e6ed377a8fc612fb)

- **作者**: lucamotz
- **时间**: 2026-09-22T20:08:27Z
- **提交信息**: [Bugfix][Model][Spec Decode] Defer disposable GLM MTP head (#55442)

Signed-off-by: Luca Motz <luca.motz@icloud.com>

### [71a2392](https://github.com/vllm-project/vllm/commit/71a239284507e4f9477f8256e04fd28d1aa9a2db)

- **作者**: hcl
- **时间**: 2026-09-22T19:45:04Z
- **提交信息**: [Bugfix][V1] Read ModelState max_model_len from model config (#58149)

Signed-off-by: Chenglun Hu <chenglunhu@gmail.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [d1f63f2](https://github.com/vllm-project/vllm/commit/d1f63f2af98540082473cfa4aed3e55eb21dce8b)

- **作者**: Divakar Verma
- **时间**: 2026-09-22T19:39:13Z
- **提交信息**: [ROCm][CI] Add GELU activation for AiterExperts in the modular-kernel coverage (#58030)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [415e11c](https://github.com/vllm-project/vllm/commit/415e11c6f1256e8e007ee88f2350049c51f11a56)

- **作者**: pengyihang
- **时间**: 2026-09-22T19:34:31Z
- **提交信息**: [Bugfix][V1] Honor enable_jit_warmup for V2 kernel warmup (#55146)

Co-authored-by: mgoin <mgoin64@gmail.com>

### [bc162b3](https://github.com/vllm-project/vllm/commit/bc162b3f9280c2dc05dfd5aa282d29551f8f6d33)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-22T19:01:20Z
- **提交信息**: [MRV2] Release weight offloader on shutdown (#57834)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [f944491](https://github.com/vllm-project/vllm/commit/f944491db914880dc5f12c0b53c1aac113014a4b)

- **作者**: Guanxin Li
- **时间**: 2026-09-22T18:44:00Z
- **提交信息**: [Bugfix] batch_invariant: keep non-AllReduce collectives enabled on NCCL >= 2.31 (#58179)

Signed-off-by: Guanxin Li <38149783+guanxingithub@users.noreply.github.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [c024cfd](https://github.com/vllm-project/vllm/commit/c024cfdb02e32ef5c804d31b28846003894276aa)

- **作者**: siyu
- **时间**: 2026-09-22T18:19:40Z
- **提交信息**: [Fast Start] Support data parallelism in the weight cache daemon  (#57386)

Signed-off-by: liusy58 <mg21330037@smail.nju.edu.cn>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [ca831d1](https://github.com/vllm-project/vllm/commit/ca831d1c55714aa10acd826389674ce8f6a4f872)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-22T18:05:11Z
- **提交信息**: [ROCm][DSv4.1][Perf] Fuse the inverse RoPE into the sparse decode reduce (#57435)

Signed-off-by: Fangzhou Ai <fangzhou.ai@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [72675c4](https://github.com/vllm-project/vllm/commit/72675c4706e4c158a3e363b261370d06ad02c87f)

- **作者**: stefankoncarevic
- **时间**: 2026-09-22T17:49:11Z
- **提交信息**: [Bugfix][ROCm] Dispatch the QuantFP8 CUDA fallback on the class (#58136)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [74370a0](https://github.com/vllm-project/vllm/commit/74370a0e3044c16b6ba58f9c144b02ab733cd73a)

- **作者**: Gilles Turpin
- **时间**: 2026-09-22T16:48:20Z
- **提交信息**: [Bugfix] hadacore_transform: respect inplace parameter to fix garbage outputs with QuIP transforms (#43462)

Signed-off-by: Gilles Turpin <turpingilles15@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [a6131b0](https://github.com/vllm-project/vllm/commit/a6131b0e656e18eeb3797b8856aa3dbc69efd8e5)

- **作者**: Juntian Liu
- **时间**: 2026-09-22T16:19:09Z
- **提交信息**: [Bugfix][Engram] Fall back when /dev/shm is absent before sharing tables (#57914)

Signed-off-by: Juntian Liu <juntianl@inferact.ai>
Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [066ee91](https://github.com/vllm-project/vllm/commit/066ee911975133dc148433ed9e65061b4587c969)

- **作者**: Kushal
- **时间**: 2026-09-22T16:11:05Z
- **提交信息**: [Bugfix][Attention] Avoid NaN in the Triton softcap for large attention logits (#56579)

Signed-off-by: Kushal Dabbe <72650064+kushaldabbe@users.noreply.github.com>
Co-authored-by: opencode <noreply@opencode.ai>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [c42f528](https://github.com/vllm-project/vllm/commit/c42f5285ec9851dacfa370e163e7837e87fd7b6d)

- **作者**: Tony Lin
- **时间**: 2026-09-22T15:38:04Z
- **提交信息**: [Bugfix] prioritize architecture capability before DeepGEMM availability check (#58073)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [feb87b1](https://github.com/vllm-project/vllm/commit/feb87b1934c10046a19cfef610c44f1710b825b8)

- **作者**: aoshen02
- **时间**: 2026-09-22T15:09:39Z
- **提交信息**: [Bugfix] Narrow AuxOutput KV restrictions to known PD connectors (#58150)

Signed-off-by: aoshen02 <aoshen@inferact.ai>

### [5c121e9](https://github.com/vllm-project/vllm/commit/5c121e962a31ed0b5fe70d743b6e194686d2b473)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-22T15:07:31Z
- **提交信息**: [SpecDecode] Restore residual-logits comments in _resample_kernel (#58166)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e4340e4](https://github.com/vllm-project/vllm/commit/e4340e41c9a32b2247cc2442b35aa91b081c424f)

- **作者**: Tony Lin
- **时间**: 2026-09-22T15:06:54Z
- **提交信息**: [Feat][XPU] VLLM_BATCH_INVARIANT support for Dense/MoE models (#55881)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [1ea7c63](https://github.com/vllm-project/vllm/commit/1ea7c63f4af7bb4fd6f025c8db44434ab274cb51)

- **作者**: Artem Perevedentsev
- **时间**: 2026-09-22T14:00:05Z
- **提交信息**: [Bugfix][Structured Output] Disallow MRV1 + PP>1 + async sched + structured output (#56250)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: CNE Pierre FICHEPOIL <pierre-1.fichepoil@gendarmerie.interieur.gouv.fr>

### [c9b34fd](https://github.com/vllm-project/vllm/commit/c9b34fdb2d0c9fdcc20fae6454bf0895a5faf6f5)

- **作者**: Jared Wen
- **时间**: 2026-09-22T13:58:21Z
- **提交信息**: [Bugfix][GLM-5.3-Flash] Run the dense MLP layers on the sequence-parallel shard (#58061)

Signed-off-by: Jared Wen <w13431838023@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d90f0ea](https://github.com/vllm-project/vllm/commit/d90f0eade5b56ca83ba03839591fe111c51790b3)

- **作者**: Jee Jee Li
- **时间**: 2026-09-22T13:13:07Z
- **提交信息**: [Build] Fix CUDA 12 KV connector dependency selection (#57945)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [e548298](https://github.com/vllm-project/vllm/commit/e548298f8144cae77d26949078c264d819d3993c)

- **作者**: linyafeng
- **时间**: 2026-09-22T13:09:39Z
- **提交信息**: [Bugfix][Structured Outputs] Reject empty `structural_tag` at request validation (#47450)

Signed-off-by: linnea-lin-00638949 <15521435947@163.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [362a64b](https://github.com/vllm-project/vllm/commit/362a64b21d5038691c929521478b63dcb4828e58)

- **作者**: xiangdong
- **时间**: 2026-09-22T11:56:01Z
- **提交信息**: [XPU][CI]Remove model_runner_v2 test from Intel GPU CI (#58050)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [9815732](https://github.com/vllm-project/vllm/commit/9815732c16ca076c60b65fccd787167d6a9c5328)

- **作者**: ubwzwd
- **时间**: 2026-09-22T11:39:47Z
- **提交信息**: [BugFix][Core] Make the structured-output grammar poll non-blocking (#55931)

Signed-off-by: ubwzwd <ubwzwd@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [81d7293](https://github.com/vllm-project/vllm/commit/81d7293c2167e39f3ffddc9a82d633f94e8a1eaa)

- **作者**: Bugen Zhao
- **时间**: 2026-09-22T10:01:53Z
- **提交信息**: [Rust Frontend] Construct model-owned vision processors through specs (#58109)

Co-authored-by: Codex <noreply@openai.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [6dc34b6](https://github.com/vllm-project/vllm/commit/6dc34b6334fe9439a46748a0df290bc785dd69df)

- **作者**: Louie Tsai
- **时间**: 2026-09-22T09:37:15Z
- **提交信息**: [CPU] Add device-memory-utilization CLI alias (#56547)

Signed-off-by: louie-tsai <louie.tsai@intel.com>
Signed-off-by: Louie Tsai <louie.tsai@intel.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [91d7324](https://github.com/vllm-project/vllm/commit/91d7324cb19d301c72d849e457221ee8dd645024)

- **作者**: Jared Wen
- **时间**: 2026-09-22T09:03:59Z
- **提交信息**: [perf] wire FA and FlashMLA for sm90 GLM5Next NoPE SparseMLA (#55385)

Signed-off-by: JaredforReal <w13431838023@gmail.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>
Co-authored-by: Leoyzen <leoyzen@gmail.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [64a48b1](https://github.com/vllm-project/vllm/commit/64a48b19b41005f1e783a69b9fdd0b5364aea4cf)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-22T08:37:34Z
- **提交信息**: [CI] Emit a kernel symbol map from the csrc build (opt-in, for test selection) (#58097)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f92b78f](https://github.com/vllm-project/vllm/commit/f92b78f6ef9c9b28f60668da77af5b65645b1a45)

- **作者**: Canlin Guo
- **时间**: 2026-09-22T08:07:17Z
- **提交信息**: [Kernel][DSV4.1] Fuse MXFP8 wo_b GEMM with sequence-parallel reduce-scatter (#57428)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Signed-off-by: Canlin <canlinguosdu@gmail.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-23
**监控日期**: 2026-09-22
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7002
- **最后更新**: 2026-09-23T00:11:29Z

## 提交统计

- **昨日提交总数**: 18
- **提交者数量**: 15
- **主要提交者**: Sicheng Hua, MaciejBalaNV, Clodagh Walsh

## AI分析总结

基于对提交记录的分析，vllm-project/vllm-omni 仓库在昨日集中进行了多项关键维护、优化与增强工作，项目整体朝着更稳定、高效且功能完善的方向发展。具体总结如下：

**1. 主要更新类型**
本次提交以 **Bug修复** 和**性能优化**为核心，同时包含了**功能增强**、**基础设施维护**与**文档完善**。其中Bug修复占比最高，涉及语音、视频、图像等多模态处理的多个模块。

**2. 关键变更点及其与项目整体方向的关系**
*   **多模态功能稳定性提升**：修复了语音克隆、音频输出合并、视频流音频完整性等关键问题，直接强化了项目“提供统一多模态服务”的核心能力。
*   **性能与硬件适配优化**：针对FP8内核、Wan 2.2 VAE解码以及特定硬件（Ascend）进行了优化，旨在降低推理延迟和成本，契合项目“快速且低成本”的目标。
*   **版本对齐与生态兼容**：通过 Rebase 合并到上游 vLLM 0.30.0，确保了与主框架的版本同步和长期兼容性，这对项目的可持续发展至关重要。
*   **测试与基准设施加固**：修复了多项基准测试和CI中的错误，并增强了测试稳定性，为持续的质量保障和性能度量打下了基础。

**3. 对项目的影响和潜在意义**
这些变更显著提升了 vllm-omni 作为多模态推理服务的**可靠性、性能基准和可维护性**。修复的Bug直接改善了用户体验，优化降低了部署成本，而版本对齐则确保了能持续受益于上游生态的改进。整体来看，项目正从快速功能迭代转向更注重**稳定、高效和工程化成熟度**的阶段。

**4. 值得关注的技术点**
*   **模型与内核级优化**：如对特定VAE（Wan 2.2）的解码优化、FP8量化内核在上下文并行下的修复，体现了对计算效率的深度追求。
*   **并发与资源调度**：在“duplex”（全双工）场景下，对异步预热和提示处理进行了精细调整，反映了对复杂实时交互模式的技术深化。
*   **多模态数据流水线**：对音频、视频流在生成和传输过程中数据完整性的多次修复，显示了对多模态数据流处理复杂性的重视。

**5. 对项目发展的综合影响**
本次提交集中的修复与优化，系统性地加固了 vllm-omni 的技术底座。它们不仅解决了已知痛点，更通过性能调优和硬件适配拓展了其应用场景，同时通过与上游对齐和基础设施完善保障了长期的演进能力。这标志着项目在实现其“为每个人提供简单、快速、廉价的多模态模型服务”的愿景上，迈出了更为稳健和扎实的一步。

## 详细提交记录

### [d2aa071](https://github.com/vllm-project/vllm-omni/commit/d2aa07159c82f816b3c22c78e636aa3ef90994f5)

- **作者**: Sicheng Hua
- **时间**: 2026-09-22T23:19:37Z
- **提交信息**: [Bugfix][Qwen3-TTS] Ignore voice labels for inline Base cloning (#6974)

Signed-off-by: sc-hua <sc_hua@qq.com>

### [7d6e2ad](https://github.com/vllm-project/vllm-omni/commit/7d6e2ade6c31bc03cb7222dfa6ab035b6e243196)

- **作者**: MaciejBalaNV
- **时间**: 2026-09-22T18:38:17Z
- **提交信息**: [bugfix] Fix FP8 Quack kernels when using Context Parallelism and reduce number of recompilations (#7458)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [c482626](https://github.com/vllm-project/vllm-omni/commit/c482626450e20f35e5b59df52f51a766829bfe8a)

- **作者**: MaciejBalaNV
- **时间**: 2026-09-22T18:37:49Z
- **提交信息**: [optimization] Added Wan 2.2 VAE decode optimizations (#7056)

Signed-off-by: Maciej Bala <mbala@nvidia.com>
Signed-off-by: MaciejBalaNV <mbala@nvidia.com>

### [7b6a5ee](https://github.com/vllm-project/vllm-omni/commit/7b6a5ee8944719b62fe24b532d9ec945987bd90b)

- **作者**: Jiaqian Liu
- **时间**: 2026-09-22T17:24:01Z
- **提交信息**: [Hardware][Ascend] Add opt-in chunked anti-alias FIR upsampling (#7896)

Signed-off-by: Jiaqian Liu <591998922@qq.com>

### [8422887](https://github.com/vllm-project/vllm-omni/commit/8422887d9f3defe076e8e23a7bd0db0bc973c1f8)

- **作者**: shiyichuan
- **时间**: 2026-09-22T17:23:26Z
- **提交信息**: [Bugfix] Merge audio final output into the matching text choice (#7376) (#7879)

Signed-off-by: mershi <mershi@tencent.com>
Co-authored-by: mershi <mershi@tencent.com>

### [b44cf97](https://github.com/vllm-project/vllm-omni/commit/b44cf97b314f17cb237873ebe4eeccedba5b3cdb)

- **作者**: Deep Shah
- **时间**: 2026-09-22T17:19:16Z
- **提交信息**: [Bugfix] Preserve all video-stream audio deltas (#7532)

Signed-off-by: Deep Shah <deep@socratic.co>

### [59db6a4](https://github.com/vllm-project/vllm-omni/commit/59db6a4285e9086391efc85a6eff6030a6294878)

- **作者**: Zhou Taichang
- **时间**: 2026-09-22T15:52:01Z
- **提交信息**: [Rebase] Rebase to vLLM 0.30.0 (#7820)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [ca14e63](https://github.com/vllm-project/vllm-omni/commit/ca14e635f5302abe2e63a1306fe45be4eca864ef)

- **作者**: yanbao1217
- **时间**: 2026-09-22T14:57:50Z
- **提交信息**: [Doc] Correct the SessionClosed admission-slot guarantee (#7636 Issue 22) (#7869)

Signed-off-by: yanbao1217 <yanliuwebsite493@gmail.com>
Co-authored-by: yanbao1217 <yanliuwebsite493@gmail.com>

### [d278aa8](https://github.com/vllm-project/vllm-omni/commit/d278aa8057a0be158e1747f0360a42ccdf0e0fa2)

- **作者**: Sun
- **时间**: 2026-09-22T14:56:30Z
- **提交信息**: [Bugfix] Mark image edit benchmark stream errors as failed (#8015)

Signed-off-by: levius <2114377220@qq.com>

### [f1057b1](https://github.com/vllm-project/vllm-omni/commit/f1057b1e0dcba89843c1bde6a41dfc5a06f6c97d)

- **作者**: Si Chen
- **时间**: 2026-09-22T13:45:55Z
- **提交信息**: [Bugfix] Restore GLM-Image unshifted timesteps after set_timesteps (#7953)

Signed-off-by: sinksilk <785976238@qq.com>

### [03ccce9](https://github.com/vllm-project/vllm-omni/commit/03ccce9a993b99f9b961b19faf34c80c7488c08e)

- **作者**: Sun
- **时间**: 2026-09-22T13:28:18Z
- **提交信息**: [Bugfix] Mark Omni chat benchmark streams with error events as failed (#8000)

Signed-off-by: levius <2114377220@qq.com>

### [7af2c3d](https://github.com/vllm-project/vllm-omni/commit/7af2c3d3512d6c5ba67a8384c8541abbdd4b79b2)

- **作者**: Clodagh Walsh
- **时间**: 2026-09-22T13:07:35Z
- **提交信息**: [CI][Voxtral] Resolve failing test_prepare_speech_generation_awaits_voxtral_async  (#7601)

Signed-off-by: Clodagh Walsh <clodaghwalsh17@gmail.com>

### [3032b4a](https://github.com/vllm-project/vllm-omni/commit/3032b4a0139077bd03cd6c404a15e3c6b3a1eb60)

- **作者**: Yueqian Lin
- **时间**: 2026-09-22T12:38:08Z
- **提交信息**: [CI] Bump the public env var snapshot count after #6848 landed (#7964)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [0582844](https://github.com/vllm-project/vllm-omni/commit/0582844a419c33cd28f915f5cf5b7537c934a48a)

- **作者**: ZacheryAU
- **时间**: 2026-09-22T10:04:22Z
- **提交信息**: [Frontend][Benchmark] Add duplex performance metrics to refactored full-duplex framework (#7714)

Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [9ebef4b](https://github.com/vllm-project/vllm-omni/commit/9ebef4b1d3cb69181bcc2eb159cc6ef35f272b6f)

- **作者**: Wang  fuyin
- **时间**: 2026-09-22T09:21:42Z
- **提交信息**: [Feat] Add prefetch for Mooncake cross-stage paged KV transfer in HunyuanImage3 (#7637)

Signed-off-by: Acerak01-fy <wfy2003324@163.com>

### [f7e2834](https://github.com/vllm-project/vllm-omni/commit/f7e28348ada4d67938d3899863ab30a290dcae7e)

- **作者**: vOv
- **时间**: 2026-09-22T08:11:42Z
- **提交信息**: [Bugfix] Stabilize NIXL manager receiver tests (#7984)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>

### [939e6ba](https://github.com/vllm-project/vllm-omni/commit/939e6ba56e3d61dbc89aceced46d6ccd35a9f8e1)

- **作者**: vOv
- **时间**: 2026-09-22T07:47:00Z
- **提交信息**: [CI/Build] Give diffusion CPU tests more timeout headroom (#7983)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>

### [ba5b748](https://github.com/vllm-project/vllm-omni/commit/ba5b7485a7f31aa2ddd90e328e873d189f23ceaf)

- **作者**: Tianyao Wu
- **时间**: 2026-09-22T07:36:42Z
- **提交信息**: [Bugfix] Keep resumable duplex prompts out of async-chunk prewarm (#7992)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>

---
