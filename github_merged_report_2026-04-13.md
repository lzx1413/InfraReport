# GitHub Stars 合并报告 - 2026-04-13

**合并日期**: 2026-04-14
**监控日期**: 2026-04-13
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


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1820
- **最后更新**: 2026-04-13T12:53:24Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bin Jia

## AI分析总结

根据提供的提交记录和README摘要，以下是针对仓库 `ByteDance-Seed/VeOmni` 昨日更新的分析总结：

### 1. 主要更新类型
- **文档更新**：具体为修复了PR（Pull Request）模板中的内容。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：在PR模板中明确列出了允许的模块和类型（`list allowed modules and types`）。
- **与项目方向的关系**：VeOmni 作为一个专注于“模型中心分布式配方库”的大规模多模态模型训练框架，强调标准化和可扩展性。规范PR模板有助于统一贡献流程，确保代码质量和项目结构的一致性，这与项目追求高效、可复现的分布式训练生态的目标相符。

### 3. 对项目的影响和潜在意义
- **短期影响**：提升贡献者提交PR的清晰度和效率，减少因模块或类型不符导致的沟通成本。
- **长期意义**：强化项目治理，促进社区协作的规范化，有助于维护大型开源项目的可持续发展和代码库的整洁性。

### 4. 值得关注的技术点
- 无直接技术代码变更；本次更新侧重于**项目管理与协作流程**的优化，反映了项目在成熟度提升过程中对开发流程的重视。

### 5. 基于项目背景的提交影响分析
- VeOmni 旨在为多模态模型训练提供分布式解决方案，其成功依赖于活跃的社区贡献和高质量的代码集成。此次文档修复虽小，但通过细化贡献指南，间接支持了项目的**可扩展性和协作效率**，有助于吸引更多开发者参与，并确保项目在快速迭代中保持结构稳定，符合其作为“配方库”的定位——即通过标准化流程积累和共享最佳实践。

---
**总结**：昨日更新是一次微小的文档维护，主要优化了PR模板，体现了项目在社区管理方面的细致化改进。虽然不涉及核心功能，但对促进项目长期健康发展具有积极意义。

## 详细提交记录

### [3cef8ef](https://github.com/ByteDance-Seed/VeOmni/commit/3cef8efa547237dc9c9460ddbde2d35407282fa3)

- **作者**: Bin Jia
- **时间**: 2026-04-13T11:50:26Z
- **提交信息**: [docs] fix: list allowed modules and types in PR template (#645)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2163
- **最后更新**: 2026-04-13T15:18:08Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Yang Yong (雍洋), Shiqiao Gu (谷石桥)

## AI分析总结

根据提供的README摘要和提交记录，以下是针对 `ModelTC/LightX2V` 仓库昨日更新的分析总结：

### 1. 主要更新类型
*   **功能新增**：新增了 `lingbot-fast` 功能。
*   **性能优化/扩展性增强**：支持了 `seq parallel for neo++`，这属于对模型并行训练/推理能力的扩展和优化。

### 2. 关键变更点及其与项目整体方向的关系
*   **支持序列并行 (`seq parallel for neo++`)**：
    *   **关键点**：为 `neo++` 模型引入了序列并行 (`sequence parallel`) 支持。这是一种分布式训练技术，用于处理超长序列（如长视频生成），通过将长序列切分到不同设备上并行计算，突破单设备内存限制。
    *   **与项目方向关系**：直接契合 `LightX2V` 作为 **“轻量级视频生成推理框架”** 的核心目标。通过支持更先进的并行策略，提升了框架处理**复杂、长序列视频生成任务**的能力和效率，是向高性能、可扩展性方向的重要迈进。
*   **新增 `lingbot-fast` 功能**：
    *   **关键点**：引入了一个名为 `lingbot-fast` 的新组件或功能。结合项目名称和上下文推测，这可能是一个**快速文本到视频 (`text-to-video`) 的生成模型或推理管线**。
    *   **与项目方向关系**：丰富了框架的**模型生态或应用场景**。`LightX2V` 旨在提供一个高效的视频生成框架，新增一个“快速”的文本到视频模型，直接增强了框架的**实用性和终端用户价值**，提供了更快捷的视频生成选项。

### 3. 对项目的影响和潜在意义
*   **技术能力提升**：`seq parallel` 的支持显著提升了框架处理**长视频或高分辨率视频**的潜力，降低了硬件门槛，使研究和大规模应用成为可能。
*   **用户体验与选择丰富**：`lingbot-fast` 的加入为用户提供了一个新的、可能更高效的视频生成工具，**拓宽了框架的适用面**，可能吸引更多开发者或用户尝试。
*   **社区与生态建设**：持续集成新的模型 (`lingbot-fast`) 和优化技术 (`seq parallel`)，表明项目在积极**扩展其技术栈和模型库**，有助于构建更活跃的开发者社区和更强大的生态系统。

### 4. 值得关注的技术点
*   **序列并行 (`Sequence Parallelism`)**：这是处理Transformer类模型长序列瓶颈的前沿分布式技术。其实现在 `LightX2V` 中，意味着框架正在集成业界最新的**大规模模型训练/推理优化方案**，技术选型较为先进。
*   **`neo++` 模型集成**：提交明确针对 `neo++` 模型进行优化。需要关注 `neo++` 是否是 `LightX2V` 主推或自研的某个视频生成模型架构，此次优化可能标志着该模型能力的重大升级。
*   **`lingbot-fast` 的设计**：值得关注其“快”体现在何处——是模型架构更轻量、推理步骤更少，还是利用了特定的加速技术（如蒸馏、量化）。这反映了项目在**推理效率优化**上的具体实践。

### 5. 基于项目背景的提交影响分析
`LightX2V` 定位为 **“轻量级”** 和 **“推理框架”**。昨日的两次提交完美地服务于这两个核心：
1.  **强化“轻量级/高效”属性**：
    *   `seq parallel for neo++` 通过分布式技术，从**系统层面**让大模型、长序列任务变得“可处理”，间接实现了在有限资源下的高效运行。
    *   `lingbot-fast` 很可能从**模型层面**提供了一个速度更快的选择，直接兑现“快速生成”的承诺。
2.  **巩固“框架”定位**：
    *   这两项更新都不是简单的Bug修复，而是**能力扩展**。一个优化了底层并行计算能力，一个增加了上层应用模型。这表明 `LightX2V` 正在从一个基础实现，向一个**功能更全面、性能更强大的视频生成平台**演进。
3.  **促进项目发展**：
    *   **吸引研究人员**：先进的并行技术支持有助于吸引需要处理复杂任务的研究人员。
    *   **吸引应用开发者**：提供开箱即用的快速模型 (`lingbot-fast`) 降低了使用门槛，有利于框架的推广和实际应用落地。
    *   **提升竞争力**：在视频生成框架竞争激烈的环境下，持续集成最新优化技术和模型，是保持项目**技术活力和竞争力**的关键。

**总结**：昨日的更新是一次“**上下结合**”的升级——底层框架支持更强大的并行计算能力，上层应用提供更快速的生成模型。这双管齐下，显著增强了 `LightX2V` 框架处理复杂视频生成任务的潜力与终端用户体验，紧密围绕其打造高效、实用视频生成工具的核心目标。

## 详细提交记录

### [d3d01db](https://github.com/ModelTC/LightX2V/commit/d3d01db760f86f98810d8b4379690f40912446db)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-04-13T14:47:15Z
- **提交信息**: support seq parallel for neo++ (#1007)

### [43090c0](https://github.com/ModelTC/LightX2V/commit/43090c0ebdaaf0b69d9346af1c60a80e124c0092)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-04-13T08:19:23Z
- **提交信息**: add lingbot-fast (#1005)

Co-authored-by: gushiqiao <975033167>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2015
- **最后更新**: 2026-04-13T14:22:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5383
- **最后更新**: 2026-04-13T23:02:28Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: Andrii Skliar, Yufeng He, amitz-nv

## AI分析总结

根据提供的提交记录和README摘要（FlashInfer是一个专注于推理的高性能GPU内核项目），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：新增Blackwell架构的GDN（Gated Delta-Net）预填充内核；扩展MoE（Mixture of Experts）的All-to-All通信支持更多`top_k`值；为BF16融合MoE添加Relu2激活函数支持。
- **Bug修复**：修复SM120架构上MXFP4/MXFP8数据类型的GEMM操作失败问题；修复CI中mypy类型检查错误；修复编译时缺少`<optional>`头文件的问题。
- **性能优化**：通过扩展MoE的All-to-All通信特化、优化归约逻辑和调整配置，提升大规模MoE模型的通信效率。
- **构建/兼容性更新**：更新项目配置以支持Blackwell（SM100）架构，优化CUDA 12.9+的架构后缀处理。

### 2. 关键变更点及其与项目整体方向的关系
- **Blackwell GDN预填充内核**：针对NVIDIA新一代Blackwell GPU（SM100）优化，专门支持Qwen系列模型（头尺寸为128）。这与FlashInfer“高性能GPU推理内核”的核心目标高度一致，旨在利用最新硬件提升大模型推理效率。
- **MoE功能扩展**：通过支持更多`top_k`值（6、10、16、22）和Relu2激活函数，增强了项目对复杂MoE模型（如DeepSeekV3、Nemotron）的适配能力。这体现了项目紧跟前沿模型架构趋势，优化分布式推理场景。
- **数据类型与架构兼容性修复**：修复MXFP4/MXFP8在SM120上的问题，确保低精度格式在更多GPU上的可靠性。这强化了项目对高效推理数据类型的广泛支持。

### 3. 对项目的影响和潜在意义
- **硬件生态扩展**：正式引入Blackwell GPU支持，使FlashInfer保持与NVIDIA最新硬件的同步，为未来B200等芯片上的高性能推理奠定基础。
- **模型覆盖提升**：通过对Qwen系列、MoE模型的深度优化，项目能更好地服务当前热门的大模型，增强其在生产环境中的实用性。
- **稳定性增强**：修复了编译、类型检查和特定架构下的运行时错误，提高了代码库的健壮性和开发体验。

### 4. 值得关注的技术点
- **Cutlass DSL编写内核**：Blackwell内核使用Cutlass DSL实现，体现了项目采用现代GPU编程范式以兼顾性能与可维护性。
- **动态特化调度**：MoE的All-to-All通信根据`top_k`值进行特化分发，展示了针对不同负载的精细化性能优化策略。
- **低精度计算支持**：持续优化MXFP4/MXFP8等新兴低精度格式，有助于降低内存占用和提升计算吞吐量。

### 5. 基于项目背景的提交影响分析
FlashInfer的目标是提供**高性能、通用的GPU推理内核**。昨日的更新从以下方面推动了这一发展：
- **前沿硬件适配**：新增Blackwell内核直接响应了硬件迭代，确保项目在最新GPU上仍能提供领先的性能（如提交中的性能对比显示，多数场景有显著加速）。
- **复杂模型支持**：对MoE和GDN等特定模型组件的优化，使FlashInfer不仅能处理标准Transformer，还能高效支持结构更复杂、参数规模更大的模型，扩大了其应用场景。
- **工程质量与兼容性**：修复构建和类型错误，提升了项目的稳定性和跨平台/架构的兼容性，这对于需要长期维护和广泛部署的开源项目至关重要。

**总结**：昨日的更新围绕**支持新硬件（Blackwell）、优化复杂模型组件（MoE/GDN）和提升系统稳定性**展开，紧密贴合FlashInfer打造高性能、通用GPU推理内核的愿景，巩固了其在快速演进的大模型推理生态中的技术竞争力。

## 详细提交记录

### [7c562d5](https://github.com/flashinfer-ai/flashinfer/commit/7c562d502513343c40281d15f4f846af38ecebe1)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-04-13T23:02:22Z
- **提交信息**: [feat] Add blackwell GDN prefill kernel (#3001)

<!-- .github/pull_request_template.md -->

## 📌 Description

- Add Blackwell GDN prefill kernel written in cutedsl

```
GPU: NVIDIA B200 [Blackwell (SM100)]
Models: Qwen3.5 family (397B, 122B, 35B, 27B, 9B, 4B, 2B, 0.8B), d=128
FLA 0.4.2, Triton 3.5.1, PyTorch 2.11.0+cu130

Heads            Seqlens           h_qk  h_v    FI Blackwell (SM100)   TFLOPS  FLA/Triton   Speedup
---------------------------------------------------------------------------------------------------
397B/122B TP8    1x8192               2    8                  0.330ms    12.8      0.338ms     1.02x
397B/122B TP8    1x4096               2    8                  0.180ms    12.0      0.215ms     1.19x
397B/122B TP8    1x2048               2    8                  0.101ms    10.7      0.213ms     2.11x
397B/122B TP8    6144+2048            2    8                  0.258ms    16.6      0.285ms     1.10x
397B/122B TP8    4096+4096            2    8                  0.179ms    23.9      0.239ms     1.34x
397B/122B TP8    2048+6144            2    8                  0.256ms    16.8      0.285ms     1.11x
397B/122B TP8    1024+7168            2    8                  0.296ms    14.5      0.308ms     1.04x
397B/122B TP8    2048x4               2    8                  0.101ms    42.3      0.208ms     2.06x
397B/122B TP8    1024x8               2    8                  0.063ms    68.2      0.214ms     3.40x

397B/122B TP4    1x8192               4   16                  0.368ms    23.3      0.424ms     1.15x
397B/122B TP4    1x4096               4   16                  0.178ms    24.2      0.235ms     1.32x
397B/122B TP4    1x2048               4   16                  0.100ms    21.4      0.220ms     2.20x
397B/122B TP4    6144+2048            4   16                  0.257ms    33.5      0.377ms     1.47x
397B/122B TP4    4096+4096            4   16                  0.179ms    47.9      0.329ms     1.84x
397B/122B TP4    2048+6144            4   16                  0.259ms    33.2      0.376ms     1.45x
397B/122B TP4    1024+7168            4   16                  0.298ms    28.9      0.401ms     1.35x
397B/122B TP4    2048x4               4   16                  0.104ms    83.0      0.334ms     3.21x
397B/122B TP4    1024x8               4   16                  0.068ms   126.3      0.342ms     5.03x

397B/122B TP2    1x8192               8   32                  0.336ms    51.1      0.602ms     1.79x
397B/122B TP2    1x4096               8   32                  0.180ms    47.7      0.334ms     1.86x
397B/122B TP2    1x2048               8   32                  0.102ms    42.3      0.228ms     2.24x
397B/122B TP2    6144+2048            8   32                  0.258ms    66.5      0.605ms     2.35x
397B/122B TP2    4096+4096            8   32                  0.182ms    94.4      0.605ms     3.32x
397B/122B TP2    2048+6144            8   32                  0.260ms    66.0      0.606ms     2.33x
397B/122B TP2    1024+7168            8   32                  0.299ms    57.4      0.606ms     2.03x
397B/122B TP2    2048x4               8   32                  0.107ms   160.8      0.613ms     5.73x
397B/122B TP2    1024x8               8   32                  0.124ms   138.7      0.605ms     4.88x

397B/122B TP1    1x8192              16   64                  0.339ms   101.4      1.021ms     3.01x
397B/122B TP1    1x4096              16   64                  0.182ms    94.4      0.539ms     2.96x
397B/122B TP1    1x2048              16   64                  0.103ms    83.2      0.302ms     2.93x
397B/122B TP1    6144+2048           16   64                  0.263ms   130.6      1.017ms     3.87x
397B/122B TP1    4096+4096           16   64                  0.187ms   184.0      1.021ms     5.46x
397B/122B TP1    2048+6144           16   64                  0.265ms   129.5      1.022ms     3.86x
397B/122B TP1    1024+7168           16   64                  0.304ms   113.0      1.024ms     3.37x
397B/122B TP1    2048x4              16   64                  0.203ms   169.4      1.033ms     5.09x
397B/122B TP1    1024x8              16   64                  0.235ms   146.0      1.031ms     4.39x

35B/9B/4B TP1    1x8192              16   32                  0.339ms    50.7      0.602ms     1.78x
35B/9B/4B TP1    1x4096              16   32                  0.181ms    47.5      0.333ms     1.84x
35B/9B/4B TP1    1x2048              16   32                  0.102ms    42.2      0.220ms     2.16x
35B/9B/4B TP1    6144+2048           16   32                  0.259ms    66.3      0.605ms     2.34x
35B/9B/4B TP1    4096+4096           16   32                  0.181ms    94.7      0.604ms     3.34x
35B/9B/4B TP1    2048+6144           16   32                  0.261ms    65.8      0.606ms     2.32x
35B/9B/4B TP1    1024+7168           16   32                  0.300ms    57.3      0.607ms     2.02x
35B/9B/4B TP1    2048x4              16   32                  0.106ms   162.6      0.613ms     5.78x
35B/9B/4B TP1    1024x8              16   32                  0.123ms   139.6      0.606ms     4.93x

27B TP1          1x8192              16   48                  0.338ms    76.3      0.847ms     2.51x
27B TP1          1x4096              16   48                  0.180ms    71.7      0.461ms     2.56x
27B TP1          1x2048              16   48                  0.102ms    63.2      0.254ms     2.49x
27B TP1          6144+2048           16   48                  0.261ms    98.9      0.789ms     3.02x
27B TP1          4096+4096           16   48                  0.184ms   140.4      0.850ms     4.62x
27B TP1          2048+6144           16   48                  0.262ms    98.5      0.853ms     3.26x
27B TP1          1024+7168           16   48                  0.300ms    85.8      0.854ms     2.85x
27B TP1          2048x4              16   48                  0.200ms   129.1      0.801ms     4.01x
27B TP1          1024x8              16   48                  0.180ms   143.6      0.812ms     4.51x

2B/0.8B TP1      1x8192              16   16                  0.334ms    25.7      0.424ms     1.27x
2B/0.8B TP1      1x4096              16   16                  0.178ms    24.1      0.235ms     1.32x
2B/0.8B TP1      1x2048              16   16                  0.100ms    21.4      0.222ms     2.22x
2B/0.8B TP1      6144+2048           16   16                  0.255ms    33.7      0.378ms     1.48x
2B/0.8B TP1      4096+4096           16   16                  0.179ms    48.0      0.330ms     1.84x
2B/0.8B TP1      2048+6144           16   16                  0.255ms    33.7      0.377ms     1.48x
2B/0.8B TP1      1024+7168           16   16                  0.294ms    29.2      0.401ms     1.36x
2B/0.8B TP1      2048x4              16   16                  0.102ms    84.3      0.335ms     3.28x
2B/0.8B TP1      1024x8              16   16                  0.066ms   129.6      0.342ms     5.18x

Sym h32          1x8192              32   32                  0.335ms    51.3      0.602ms     1.80x
Sym h32          1x4096              32   32                  0.179ms    48.0      0.334ms     1.87x
Sym h32          1x2048              32   32                  0.101ms    42.4      0.221ms     2.19x
Sym h32          6144+2048           32   32                  0.258ms    66.6      0.604ms     2.34x
Sym h32          4096+4096           32   32                  0.181ms    94.7      0.605ms     3.34x
Sym h32          2048+6144           32   32                  0.258ms    66.6      0.605ms     2.35x
Sym h32          1024+7168           32   32                  0.296ms    58.0      0.606ms     2.05x
Sym h32          2048x4              32   32                  0.106ms   162.3      0.613ms     5.78x
Sym h32          1024x8              32   32                  0.123ms   139.5      0.605ms     4.92x
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
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added Blackwell (SM100/SM100A) GPU path for chunked gated delta-net
prefill (requires head_size=128, CUDA 13+).

* **Chores**
* Optional kernel imports made more robust; package exposes SM100 probe
flags and optional support.
* Project and installer updated to declare and install SM100-capable
CUTLASS extras when appropriate.

* **Tests**
  * Test skips updated for SM100; relaxed numeric tolerances.

* **Benchmarks**
* New SM100-focused benchmark scripts and updated benchmark
headers/output.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: jiahanc <173873397+jiahanc@users.noreply.github.com>

### [04f4c0c](https://github.com/flashinfer-ai/flashinfer/commit/04f4c0c9a6669f374bbb4a1cab5100c6972ff79a)

- **作者**: Andrii Skliar
- **时间**: 2026-04-13T22:22:05Z
- **提交信息**: fix: MXFP4/MXFP8 failures in SM120 FAST_BUILD and expand all_tiles[]                                                   (#2994)

**Problem**
MXFP4 and MXFP8 GEMM operations were failing on SM120 because:
- The FAST_BUILD path returned a single hardcoded CtaShape128x128x64B
tile regardless of GROUPED_GEMM, and that tile is not valid for all
MXFP4/MXFP8 configurations
- The full-build all_tiles[] table was missing tiles needed by those
dtypes (128x128x128B, 128x128x64B, 256x128x64B),
leaving the autotuner with no viable candidate in some cases
**Fix**
- FAST_BUILD: differentiate grouped vs. non-grouped paths with tiles
known to work for MXFP4/MXFP8:
- Grouped: 128x128x128B + 128x128x64B
- Non-grouped: 128x128x256B + 128x128x64B
- Full-build all_tiles[]: add the three missing tiles so the autotuner
has a complete candidate set for MXFP4/MXFP8
workloads

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance & Optimizations**
* More predictable kernel candidate selection and expanded
tile/configuration options for SM120-class GPUs to improve tuning and
performance.
* Broadened handling of grouped computation patterns to enable
additional configuration choices.

* **Build/Compatibility**
* Refined CUDA 12.9+ architecture suffixing for more accurate build
targeting.

* **Chores**
* Added type annotations and minor signature clarifications (no runtime
behavior changes).

* **Bug Fixes**
* MoE fusion path now forwards additional tensors/parameters to improve
fused operation correctness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: samuellees <lsam@nvidia.com>

---------

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Sam (Kesen Li) <lsam@nvidia.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

### [19055a6](https://github.com/flashinfer-ai/flashinfer/commit/19055a650750eb3998bbfcdc1e19d910ef3bf8a2)

- **作者**: Bo Li
- **时间**: 2026-04-13T22:17:52Z
- **提交信息**: feat: extend moe alltoall top-k specializations (#3021)

## Summary
- extend moe alltoall dispatch launch specialization to `top_k` values
6, 10, 16, and 22
- add explicit combine reduction trees for `top_k` values 6, 10, 16, and
22 while keeping the generic fallback for other valid cases
- align combine regression coverage with representative MoE model
parameter sets and targeted Qwen coverage for dtype and workspace
staging

## Test plan
- `python3 -m py_compile tests/comm/test_trtllm_moe_alltoall.py`
- GPU pytest not run in this environment

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance & Optimization**
* Increased MOE all-to-all capacity to support larger top-k scenarios
(up to 22).
* Reworked reduction logic for more efficient vectorized accumulation,
improving communication throughput.
* Adjusted internal configuration sizing to better support larger
workloads.

* **Tests**
* Expanded test coverage with new model-driven parameter cases and
increased max world size from 8 to 16.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ede2225](https://github.com/flashinfer-ai/flashinfer/commit/ede2225a160736af5bf53cc1ad471e1c714a4c2d)

- **作者**: amitz-nv
- **时间**: 2026-04-13T19:34:13Z
- **提交信息**: Add support for Relu2 in BF16 fused MoE (#2864)

<!-- .github/pull_request_template.md -->

## 📌 Description
* Added support for Relu2 non-gated activation in BF16 Fused MoE by
adding `activation_type` to external API:
  * `trtllm_bf16_moe`
  * `trtllm_bf16_routed_moe`
  * `Bf16MoeLauncher::init`
* Updated trtllm-gen batched GEMM kernels
* Updated
`tests/moe/test_trtllm_gen_fused_moe.py::test_deepseekv3_routing` to
include BF16 with Nemotron config, fixed nemotron config
`intermediate_size` test param to match Nemotron 3 Super.
* Fixed import issues found by `pre-commit run --all-files`
* Required change from trtllm-gen batched GEMM update: Changed
`options.mNumStages == 4` to `options.mNumStagesA == 4 &&
options.mNumStagesB == 4` in `prioritizePredefinedConfigs` function in
`csrc/trtllm_batched_gemm_runner.cu`.

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
* MoE APIs now accept a validated runtime activation_type, enabling
selectable activation functions for BF16 and FP8 inference.

* **Tests**
* Expanded DeepSeekV3 routing tests and added BF16 to non-gated
activation coverage.
  * Updated test parameters to reflect new compatibility.

* **Bug Fixes**
* Adjusted kernel configuration prioritization for a specific
corner-case path.

* **Refactor**
  * Internal enum imports reorganized to a shared enums module.

* **Chores**
  * Updated batched GEMM artifact path and checksum.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: amitz-nv <203509407+amitz-nv@users.noreply.github.com>

### [e64ae8b](https://github.com/flashinfer-ai/flashinfer/commit/e64ae8b8920034c2efc3f43326423ac5d8873b24)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-04-13T14:23:34Z
- **提交信息**: [chore] Fix CI pre-commit mypy error (#3040)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix CI pre-commit mypy error
``` bash
mypy.....................................................................Failed
- hook id: mypy
- exit code: 1

flashinfer/jit/core.py: note: In member "__init__" of class "JitSpecRegistry":
flashinfer/jit/core.py:164:9: note: By default the bodies of untyped functions are not checked, consider using --check-untyped-defs  [annotation-unchecked]
flashinfer/jit/core.py:165:9: note: By default the bodies of untyped functions are not checked, consider using --check-untyped-defs  [annotation-unchecked]
flashinfer/autotuner.py: note: In member "__init__" of class "AutoTuner":
flashinfer/autotuner.py:579:9: note: By default the bodies of untyped functions are not checked, consider using --check-untyped-defs  [annotation-unchecked]
flashinfer/autotuner.py:581:9: note: By default the bodies of untyped functions are not checked, consider using --check-untyped-defs  [annotation-unchecked]
flashinfer/comm/allreduce.py: note: In function "allreduce_fusion":
flashinfer/comm/allreduce.py:713:13: error: Missing positional arguments "quant_out", "scale_out", "routed_scaling_factor" in call to "trtllm_moe_finalize_allreduce_fusion"  [call-arg]
flashinfer/aot.py: note: In function "main":
flashinfer/aot.py:979:5: note: By default the bodies of untyped functions are not checked, consider using --check-untyped-defs  [annotation-unchecked]
Found 1 error in 1 file (checked 193 source files)
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
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Fixed an issue in MOE finalization to ensure correct parameter
handling during fused finalization steps, improving stability and
correctness of final outputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: jiahanc <173873397+jiahanc@users.noreply.github.com>

### [5678471](https://github.com/flashinfer-ai/flashinfer/commit/56784716a12a6a15dfb674a2251d28a27e3f15e3)

- **作者**: Yufeng He
- **时间**: 2026-04-13T09:18:00Z
- **提交信息**: Fix compilation error: add missing <optional> header (#2772)

`trtllm_allreduce_fusion.cuh` and `trtllm_moe_allreduce_fusion.cuh` use
`std::optional` and `std::nullopt` but only include
`<cuda/std/optional>`, which conditionally includes the standard
`<optional>` header based on `__cpp_lib_optional`. When that macro is
not defined (varies by CUDA toolkit version and compiler),
`std::optional` is undefined and compilation fails.

Add the standard `<optional>` include directly.

Fixes #2767

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Chores**
* Small internal compatibility update to enhance optional-type support
across the codebase, improving build robustness and maintainability
without changing runtime behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yufeng He <40085740+universeplayer@users.noreply.github.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3372
- **最后更新**: 2026-04-13T20:59:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33316
- **最后更新**: 2026-04-13T23:09:35Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: hlky

## AI分析总结

根据提供的提交记录和README背景，以下是针对huggingface/diffusers仓库昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：引入了名为“FlashPack”的新功能模块，涉及模型加载、保存、下载及管道集成。
- **代码优化与维护**：包括代码风格修复（ruff）、测试添加和错误处理优化（ignore_cleanup_errors）。

### 2. 关键变更点及其与项目整体方向的关系
- **FlashPack模块实现**：新增了`FlashPack`类及相关方法（如`save_pretrained`、`load_flashpack_checkpoint`），支持高效模型打包与部署。
- **管道集成**：将FlashPack整合到现有pipeline系统中，增强了diffusers的模型管理能力。
- **测试与错误处理**：添加了测试用例并优化了清理错误处理，提升了代码健壮性。
- **与项目方向关系**：diffusers专注于扩散模型工具库开发，FlashPack的加入强化了模型存储、共享和部署流程，符合项目提升易用性和效率的目标。

### 3. 对项目的影响和潜在意义
- **用户体验提升**：简化了模型的保存、加载和分发流程，可能降低用户使用门槛。
- **维护性增强**：通过测试和错误处理改进，提高了代码可靠性。
- **社区协作体现**：提交包含代码审查建议和自动化风格修复，反映了活跃的社区开发模式。

### 4. 值得关注的技术点
- **dtype作为属性管理**：可能优化了模型精度控制。
- **flashpack_kwargs参数化**：增加了模块的灵活性和可配置性。
- **下载与日志功能**：提升了模块的实用性和可调试性。

### 5. 基于项目背景的提交影响分析
- **背景参考**：README显示项目专注于扩散模型库开发，强调易用性、模块化和高性能。
- **发展影响**：
  - **功能扩展**：FlashPack丰富了模型生命周期管理工具，支持项目向更完整的生态系统演进。
  - **性能与效率**：通过优化模型处理流程，可能间接提升扩散模型的部署效率。
  - **社区驱动发展**：提交记录显示多人协作和自动化流程，有助于加速项目迭代和标准化。

总结：本次更新以功能新增为主，通过引入FlashPack模块强化了模型的打包与管理能力，贴合diffusers作为扩散模型工具库的定位，旨在提升开发效率和用户体验，同时通过代码维护增强了项目可持续性。

## 详细提交记录

### [5063aa5](https://github.com/huggingface/diffusers/commit/5063aa5566f068b68bba799b6604e9ac14eaf37c)

- **作者**: hlky
- **时间**: 2026-04-13T15:12:17Z
- **提交信息**: FlashPack (#12700)

* FlashPack

* setup

* save_pretrained

* dtype is property

* destination_path

* logging

* pipeline

* ruff

* flashpack_kwargs

* download

* Fix docstring

* Apply suggestions from code review

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

* tests

* ignore_cleanup_errors

* -load_flashpack_checkpoint

* Apply style fixes

---------

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>
Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 393
- **最后更新**: 2026-04-11T11:44:47Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12220
- **最后更新**: 2026-04-13T20:09:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 25751
- **最后更新**: 2026-04-13T23:10:38Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 19
- **主要提交者**: Liwansi, ishandhanani, Thomas Wang

## AI分析总结

根据您提供的 `sgl-project/sglang` 仓库的提交记录和 README 摘要（项目为 SGLang，一个用于高效运行大型语言模型的框架/运行时），以下是昨日更新的要点总结：

### 1. 主要更新类型
昨日的提交涵盖了多种类型，体现了项目在快速迭代和生态扩展：
*   **功能新增**：支持 Stable Diffusion 3 Medium 扩散模型、为 Minimax 模型新增融合的 TP QK 归一化 JIT 内核、为 AMD 后端添加 MoE 权重填充。
*   **Bug 修复**：修复了 GLM4.7 Flash 的格式检测、NPU 上 Qwen3 模型的文档错误、版本检测逻辑、Docker 构建问题等。
*   **性能优化/重构**：迁移 CPU 亲和性设置到环境变量并重构模型配置构建、优化 TRT-LLM 注意力后端的内存操作、为 JIT 内核添加缓存。
*   **文档更新**：大量更新了 NPU（Ascend）部署相关的参数说明、默认值和运行指南。
*   **配置/工具链更新**：调整环境变量控制 SWA 驱逐间隔、回滚 CI 的默认 CUDA 版本、更新 CODEOWNERS、移除 Docker 中不必要的缓存复制。

### 2. 关键变更点及其与项目整体方向的关系
*   **多硬件后端支持深化**：提交中涉及 **AMD、NPU（Ascend）、NVIDIA（TRT-LLM）** 等多个硬件平台，特别是 NPU 相关更新非常密集（文档、参数约束、bug修复）。这**强烈契合** SGLang 作为高效 LLM 运行时，旨在**支持多种硬件以最大化性能和可及性**的整体方向。
*   **模型与架构扩展**：新增对 **Stable Diffusion 3 Medium** 的支持，表明项目正从纯文本 LLM 向**多模态（文生图）领域拓展**。同时，针对 **MoE（混合专家）模型** 的优化（LoRA 虚拟专家、AMD 权重填充）和 **Minimax** 模型的专用内核开发，显示其致力于**覆盖更前沿、复杂的模型架构**。
*   **系统稳定性与可维护性提升**：多项重构（如配置构建）、环境变量抽象化、缓存优化和 CI/CD 调整，旨在**提升框架本身的健壮性、可配置性和开发体验**，这是项目成熟度增长的标志。

### 3. 对项目的影响和潜在意义
*   **拓宽应用场景**：支持扩散模型将吸引更多生成式 AI 应用开发者，不再局限于文本生成。
*   **降低部署门槛**：对 NPU 等国产硬件的深度支持和完善的文档，有助于项目在更广泛的国产化环境中落地。
*   **提升专业领域性能**：为 MoE、Minimax 等特定模型架构的优化，能直接提升相关用户在 SGLang 上的推理效率和体验，增强框架在细分领域的竞争力。
*   **巩固基础设施**：持续的系统级优化和修复为未来更大规模的模型支持和更复杂的特性打下了更稳定的基础。

### 4. 值得关注的技术点
*   **虚拟专家（Virtual experts）**：在 MoE 模型中结合 LoRA，这是一种**高效的参数微调与扩展技术**，能在控制成本的同时提升模型能力。
*   **融合的 TP QK 归一化 JIT 内核**：针对 Minimax 模型的**定制化内核优化**，体现了 SGLang 在算子层面进行深度性能调优的能力。
*   **多硬件抽象层的持续打磨**：从 AMD、NPU 到 NVIDIA，提交显示团队正在**同步推进不同后端的成熟度**，处理各自的特有问题（如权重填充、格式检测、参数约束）。

### 5. 基于项目背景的提交影响分析
SGLang 的目标是成为“LLM 操作系统的运行时”。昨日的提交完美地诠释了这一愿景：
1.  **作为“操作系统”**：它正在**扩展其“驱动程序”**（支持更多硬件如 NPU）和**系统服务**（优化资源管理如 CPU 亲和性、SWA 间隔）。
2.  **作为“运行时”**：它正在**增加其“可执行文件”格式**的支持（Stable Diffusion 3, Minimax 模型）并**优化“执行引擎”**（针对 MoE、特定内核的 JIT 优化）。
3.  **整体发展**：这些更新表明 SGLang 正沿着 **“横向扩展”（支持更多硬件和模型）** 与 **“纵向深化”（优化底层性能和稳定性）** 两个维度快速发展。这有助于其构建更强大的生态，吸引不同硬件厂商和模型开发者的加入，最终巩固其作为高效、通用 LLM 部署基础设施的地位。密集的 NPU 相关更新尤其值得注意，可能意味着在该硬件平台上的合作或应用取得了重要进展。

## 详细提交记录

### [8f9553b](https://github.com/sgl-project/sglang/commit/8f9553bccbf98e7c25dd9e8a0c152cc7722d8ce5)

- **作者**: Lianmin Zheng
- **时间**: 2026-04-13T23:10:31Z
- **提交信息**: [Misc] Migrate SGLANG_SET_CPU_AFFINITY to envs and refactor model config building (#22730)

### [f4f9e68](https://github.com/sgl-project/sglang/commit/f4f9e681891673ecb2d92dca1fe00e65c171eff8)

- **作者**: mqhc2020
- **时间**: 2026-04-13T22:50:15Z
- **提交信息**: [AMD] Add MoE weights and scales padding (#21097)

Co-authored-by: HAI <hixiao@gmail.com>

### [b1efce3](https://github.com/sgl-project/sglang/commit/b1efce342ce3946c40c27e00812f0468d735c1e1)

- **作者**: Yilong Zhao
- **时间**: 2026-04-13T22:37:59Z
- **提交信息**: env: add knob to control SWA eviction interval (#22645)

### [f81b6e8](https://github.com/sgl-project/sglang/commit/f81b6e8f51705e58dcc589259277d4f732b53887)

- **作者**: Lianmin Zheng
- **时间**: 2026-04-13T21:42:49Z
- **提交信息**: [Misc] Add @cache_once to is_arch_support_pdl in jit_kernel (#22724)

### [b441317](https://github.com/sgl-project/sglang/commit/b441317aa43084d9c43709ef00ec692b8f3ff20e)

- **作者**: Baizhou Zhang
- **时间**: 2026-04-13T21:39:24Z
- **提交信息**: Revert "Upgrade CI default CUDA version from 12.9 to 13.0" (#22727)

### [ba7bcca](https://github.com/sgl-project/sglang/commit/ba7bcca6b36a663f45f573537d9c4a0707065661)

- **作者**: Lianmin Zheng
- **时间**: 2026-04-13T21:29:12Z
- **提交信息**: Use reshape instead of contiguous().view() in TRTLLMHAAttnBackend (#22517)

### [ff13dfe](https://github.com/sgl-project/sglang/commit/ff13dfee45df4be0f85ea0da3cd630c5a4912eaf)

- **作者**: Kurt Shuster
- **时间**: 2026-04-13T21:19:30Z
- **提交信息**: [lora][moe] Virtual experts for LoRA MoE (#22122)

Co-authored-by: Yusheng Su <yushengsu.thu@gmail.com>

### [6b2bf66](https://github.com/sgl-project/sglang/commit/6b2bf66cd9cd0448b0e9f3af8a54e9e10686fdf2)

- **作者**: ishandhanani
- **时间**: 2026-04-13T20:10:07Z
- **提交信息**: fix[glm4.7 flash]: properly detect `gfx95_quant_format` (#22720)

### [f51ce2c](https://github.com/sgl-project/sglang/commit/f51ce2c92f9ced73db0678f607919ed6f12c6576)

- **作者**: R0CKSTAR
- **时间**: 2026-04-13T19:41:07Z
- **提交信息**: Update CODEOWNERS for musa/mlx (#22593)

Signed-off-by: Xiaodong Ye <yeahdongcn@gmail.com>

### [90ef8ce](https://github.com/sgl-project/sglang/commit/90ef8ce54de7dc4eb41f4ad1b6ba5abbad583769)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-04-13T16:48:22Z
- **提交信息**: [Docker] Remove flashinfer cache copy (#22653)

### [3981076](https://github.com/sgl-project/sglang/commit/39810762d2cd4ad6a513566b54b5f50fc6be328d)

- **作者**: Asish Kumar
- **时间**: 2026-04-13T16:45:45Z
- **提交信息**: fix: use describe mode for SGLang version detection (#22600)

Signed-off-by: Asish Kumar <officialasishkumar@gmail.com>

### [13a4aaf](https://github.com/sgl-project/sglang/commit/13a4aafdbe693da7a7bbc80952383c1bcabf39a1)

- **作者**: 看海的人
- **时间**: 2026-04-13T14:53:24Z
- **提交信息**: [NPU]  update glm5 running guide (#22712)

### [c6403a1](https://github.com/sgl-project/sglang/commit/c6403a11cbfc76c245ede585bfd66a89890f52e0)

- **作者**: chx96642264
- **时间**: 2026-04-13T14:50:48Z
- **提交信息**: Modify the optional values and constraints of parameter. (#22705)

### [b6a91b1](https://github.com/sgl-project/sglang/commit/b6a91b1afefc3caac396f720aa9beeb798aabf75)

- **作者**: jianzhao-xu
- **时间**: 2026-04-13T14:42:34Z
- **提交信息**: [NPU] --attn-cp-size --init-expert-location --eplb-algorithm  parameter docs update (#22704)

Co-authored-by: Jianzhao Xu <xujianchao@huawei.com>

### [8d904e5](https://github.com/sgl-project/sglang/commit/8d904e50f2d937991c424f69fa1c052836d11bd7)

- **作者**: Liwansi
- **时间**: 2026-04-13T14:20:17Z
- **提交信息**: [NPU]qwen3-8b and 32b md bugfix (#22687)

### [2089ac8](https://github.com/sgl-project/sglang/commit/2089ac86a7cd325a1a4150508e41f7d06e2ddb51)

- **作者**: loading66
- **时间**: 2026-04-13T14:02:56Z
- **提交信息**: Improve parameters usage constraints for npu deployment (#22700)

Co-authored-by: h30064329 <hanbing45@h-partners.com>

### [56c97c7](https://github.com/sgl-project/sglang/commit/56c97c7738c471f0c11691166b5c6518a75de17b)

- **作者**: 看海的人
- **时间**: 2026-04-13T13:55:38Z
- **提交信息**: [NPU] update npu doc (#22697)

Co-authored-by: zhsurpass <zhsurpass@users.noreply.github.com>

### [d01b2bf](https://github.com/sgl-project/sglang/commit/d01b2bf257e7d12bc7513ed69e8296be963b4b90)

- **作者**: xdtbynd
- **时间**: 2026-04-13T13:22:37Z
- **提交信息**: [Docs] Fix default values and options in Ascend server arguments documentation (#22698)

Co-authored-by: xdtbynd <supercluster@vip.qq.com>

### [314d6ec](https://github.com/sgl-project/sglang/commit/314d6ecf0880eefbd9d56cdc21e1b57bb390df80)

- **作者**: DarkSharpness
- **时间**: 2026-04-13T12:29:47Z
- **提交信息**: [Feature][JIT Kernel] Fused TP QK norm For Minimax (#20673)

Co-authored-by: Mingyang Jiang <13463932+jmydurant@users.noreply.github.com>

### [4df6043](https://github.com/sgl-project/sglang/commit/4df60434d7e15284f56f72b881db7c218eac7563)

- **作者**: Xiaole Guo
- **时间**: 2026-04-13T08:07:06Z
- **提交信息**: [diffusion] model: support stable-diffusion-3-medium-diffusers (#19225)

Co-authored-by: zhaochenyang20 <zhaochen20@outlook.com>
Co-authored-by: Kangrui Du <kangruidu@gmail.com>
Co-authored-by: Xiaole Guo <gxlvera@gmail.com>

### [9e6d1c0](https://github.com/sgl-project/sglang/commit/9e6d1c066ec3445b534eef6ccdcd752f1bddae1f)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-13T07:37:29Z
- **提交信息**: TestStreamingSessionAbortLeakRepro: inherit stdout/stderr instead of tempfile (#22668)

### [4a746ea](https://github.com/sgl-project/sglang/commit/4a746ea462882106c85724f8228eae1079414f05)

- **作者**: Thomas Wang
- **时间**: 2026-04-13T07:01:37Z
- **提交信息**: [AMD] Remove aiter hotfixes in Dockerfile covered by aiter v0.1.12.post1 (#22657)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache acceleration, parallelism and quantization for DiTs.
- **语言**: Python
- **星标数**: 1136
- **最后更新**: 2026-04-13T12:18:48Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

### 1. 主要更新类型
- **功能新增**：在示例中支持 `svdq-calib` 选项，并扩展 SVDQ PTQ 至 SVDQ DQ 功能。
- **Bug修复**：修复 W4A4 线性层对 3D 输入/输出的支持问题。

### 2. 关键变更点及其与项目整体方向的关系
- **支持 `svdq-calib` 选项**：增强了量化校准的灵活性，与项目“量化”目标一致，便于用户进行模型优化。
- **扩展 SVDQ PTQ 至 SVDQ DQ**：提升了量化方法的适用范围，支持动态量化，进一步优化推理效率。
- **修复 3D 输入/输出支持**：确保 W4A4 线性层能处理更复杂的数据结构，提升框架的鲁棒性和通用性。

### 3. 对项目的影响和潜在意义
- **提升用户体验**：通过示例选项和功能扩展，降低了量化配置的复杂度。
- **增强框架兼容性**：修复 3D 支持问题，减少潜在错误，提高模型部署的稳定性。
- **推动量化技术应用**：扩展 SVDQ 功能，为高效推理提供更多工具，可能吸引更多开发者采用。

### 4. 值得关注的技术点
- **SVDQ（奇异值分解量化）**：一种先进的量化方法，可能结合缓存和并行技术，进一步提升 DiT 模型推理性能。
- **W4A4 线性层优化**：针对低精度（4位权重和激活）的线性运算优化，是高效推理的关键组件。

### 5. 基于项目背景的提交影响分析
- **项目背景**：Cache-DiT 是一个专注于扩散变换器（DiT）的 PyTorch 原生推理引擎，核心目标是通过缓存、并行化和量化技术提升推理速度与效率。
- **影响分析**：
  - **强化量化生态**：提交围绕量化功能（SVDQ、W4A4）展开，直接支持项目的“量化”支柱，有助于降低模型内存占用和加速计算。
  - **提升工程可用性**：通过示例和错误修复，降低了用户使用门槛，促进框架的实践应用。
  - **技术前瞻性**：扩展 SVDQ 至动态量化，显示了项目在高效推理技术上的持续探索，可能为未来性能突破奠定基础。

这些更新整体上巩固了 Cache-DiT 作为高效 DiT 推理引擎的定位，通过功能增强和问题修复，推动项目向更稳定、易用、高性能的方向发展。

## 详细提交记录

### [f031b2d](https://github.com/vipshop/cache-dit/commit/f031b2da89e64172b440b710db2ec34dc0a8e2fb)

- **作者**: DefTruth
- **时间**: 2026-04-13T10:54:17Z
- **提交信息**: chore: support svdq-calib option in examples (#976)

* support svdq-calib option in examples

* support svdq-calib option in examples

* support svdq-calib option in examples

* support svdq-calib option in examples

* support svdq-calib option in examples

* support svdq-calib option in examples

* support svdq-calib option in examples

* support svdq-calib option in examples

### [20cc904](https://github.com/vipshop/cache-dit/commit/20cc904f7033395a0b82b5d6ca158ea3769acb1b)

- **作者**: DefTruth
- **时间**: 2026-04-13T09:22:42Z
- **提交信息**: fix: support 3D input/output for W4A4 linear (#975)

* feat: extend SVDQ PTQ -> SVDQ DQ

* feat: extend SVDQ PTQ -> SVDQ DQ

* support 3D input/output for W4A4 linear

### [f88df6e](https://github.com/vipshop/cache-dit/commit/f88df6e32d24391b0fa9c85c10eec36dd1a1cc3f)

- **作者**: DefTruth
- **时间**: 2026-04-13T09:00:45Z
- **提交信息**: feat: extend SVDQ PTQ -> SVDQ DQ (#974)

* feat: extend SVDQ PTQ -> SVDQ DQ

* feat: extend SVDQ PTQ -> SVDQ DQ

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 76448
- **最后更新**: 2026-04-13T23:23:26Z

## 提交统计

- **昨日提交总数**: 21
- **提交者数量**: 21
- **主要提交者**: Yi Liu, Giancarlo Delfin, zhanqiuhu

## AI分析总结

根据提供的提交记录和README摘要（vLLM项目专注于“易用、快速、经济的LLM服务”），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占主导（约12项），涉及内存/权重损坏、张量形状不匹配、数据类型/后端兼容性、流处理、模型加载、指标计算等多个核心模块。
- **性能优化**：2项（Eagle预填充CUDA图支持、ParakeetExtractor增强）。
- **功能新增/增强**：3项（等待请求细分指标暴露、多轮基准测试输出、重排请求新增参数）。
- **重构**：2项（简化解析逻辑、创建专用量化方法）。
- **文档更新**：1项（修复Python构建文档链接）。
- **内核/量化支持扩展**：2项（ROCm Triton内核修复、新增XPU MXFP8 GEMM内核）。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向（易用、快速、经济）的关系 |
| :--- | :--- |
| **Eagle预填充完整CUDA图支持** (`#37588`) | **快速**：通过CUDA图优化推理关键路径，减少内核启动开销，提升吞吐量。 |
| **多项内存/权重损坏修复** (如`#39650`, `#39418`) | **稳定/经济**：防止静默数据损坏，确保服务可靠性，避免因错误导致的资源浪费。 |
| **等待请求细分指标暴露** (`#38435`) | **易用/可观测性**：提供更细粒度的监控指标，帮助用户诊断性能瓶颈和优化资源配置。 |
| **多后端/硬件支持修复与扩展** (如ROCm、FlashInfer、XPU、UMA GPU检测) | **广泛适用/经济**：增强对AMD、Intel等硬件的支持，为用户提供更多低成本部署选择。 |
| **稀疏注意力与推测解码修复** (`#39542`, `#39225`) | **快速/经济**：修复了用于提升吞吐量的高级优化技术中的问题，确保其正确性和性能收益。 |

### 3. 对项目的影响和潜在意义
- **稳定性大幅提升**：批量Bug修复覆盖了从内核、调度到API的广泛层面，直接增强了生产环境的健壮性。
- **性能持续优化**：对Eagle（推测解码）和音频处理等组件的优化，巩固了vLLM在高吞吐、低延迟方面的领先优势。
- **生态兼容性扩展**：积极修复和适配不同硬件（ROCm, XPU）及推理后端（FlashInfer），降低了用户的使用门槛和成本。
- **可观测性增强**：新的指标和基准测试输出功能，使运维和性能调优更加数据驱动。

### 4. 值得关注的技术点
- **CUDA Graph深度集成**：将其支持扩展到Eagle预填充阶段，表明vLLM正在系统性地消除推理过程中的动态开销。
- **量化与混合精度演进**：出现了针对MOE模型和Intel XPU硬件的专用量化方法(`#39604`)与新内核(`#38707`)，显示量化支持正走向精细化和硬件定制化。
- **复杂优化技术的正确性保障**：修复涉及**稀疏注意力**、**推测解码**、**KV缓存压缩**等高阶特性，说明项目在追求极致性能的同时，高度重视底层正确性。
- **多硬件架构支持**：单日提交同时涉及NVIDIA、AMD和Intel GPU的修复与特性，体现了其作为通用推理引擎的架构设计。

### 5. 结合项目背景的发展影响
这些提交紧密围绕vLLM“**让LLM服务更易用、更快速、更经济**”的核心目标：
- **“快速”**：通过CUDA图、内核修复、性能优化直接提升推理速度。
- **“经济”**：通过扩展硬件支持（如XPU）、修复内存损坏（减少浪费）、推进量化（降低显存）来帮助用户降低部署成本。
- **“易用”**：通过修复API、流处理、模型加载错误和增强文档，改善开发者体验；通过暴露更多指标，提升运维便利性。

**总体而言**，这是一次以**夯实基础、修复缺陷**为主，并**伴随关键性能优化和生态扩展**的更新。它反映了vLLM项目在快速发展、增加复杂功能的同时，高度重视代码质量和系统稳定性，正在从一个高性能原型向成熟、可靠的生产级服务平台稳步演进。

## 详细提交记录

### [ccf90ba](https://github.com/vllm-project/vllm/commit/ccf90ba784900324e8ff4e6495d13b47b27b941a)

- **作者**: Giancarlo Delfin
- **时间**: 2026-04-13T23:01:24Z
- **提交信息**: [Model Runner V2] Add full cuda graph support for eagle prefill (#37588)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [6adacfc](https://github.com/vllm-project/vllm/commit/6adacfcb65c1d40aa5e6d99249abba9cf3e350da)

- **作者**: Netanel Haber
- **时间**: 2026-04-13T21:37:35Z
- **提交信息**: ParakeetExtractor performance and UX enhancements (#39423)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>

### [14cb86c](https://github.com/vllm-project/vllm/commit/14cb86c1872cbe0da1cf8030721b4aa2ab9ffbb8)

- **作者**: Flora Feng
- **时间**: 2026-04-13T21:02:13Z
- **提交信息**: [Refactor][Parser] Simplify parse_delta (#39728)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [8213e8f](https://github.com/vllm-project/vllm/commit/8213e8f88023726799ae48e2ebef06ef0c021128)

- **作者**: Monishver
- **时间**: 2026-04-13T20:50:08Z
- **提交信息**: Bug/test eagle dp v0 (#38938)

Signed-off-by: Monishver Chandrasekaran <monishverchandrasekaran@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [3693f92](https://github.com/vllm-project/vllm/commit/3693f922ff0e15b1e395cdc862f7c6e492a11bf4)

- **作者**: Pedram Razavi
- **时间**: 2026-04-13T19:37:27Z
- **提交信息**: [Bugfix][Pooling] Fix silent weight corruption with buffer-reusing iterators (#39650)

Signed-off-by: Pedram Razavi <pedram.razavi@gmail.com>

### [5c18b96](https://github.com/vllm-project/vllm/commit/5c18b961d692cf45df0a1ecca7d1688f6168ae0f)

- **作者**: mukesh-hai
- **时间**: 2026-04-13T19:30:55Z
- **提交信息**: [Core][Metrics] expose waiting request breakdown via labeled metric (capacity/deferred) (#38435)

Signed-off-by: Mukesh Baphna <mukesh@hippocraticai.com>
Signed-off-by: Mark McLoughlin <markmc@redhat.com>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>
Co-authored-by: Mark McLoughlin <markmc@redhat.com>

### [f72b209](https://github.com/vllm-project/vllm/commit/f72b20976c49f5cc522281b59df4863cabed8df2)

- **作者**: Tyler Michael Smith
- **时间**: 2026-04-13T19:13:51Z
- **提交信息**: [Bugfix] Reject non-nvfp4 dtypes when using the flashinfer_nvlink_one_sided all2all backend (#39717)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [610a3ef](https://github.com/vllm-project/vllm/commit/610a3efcafed501ea90ee87e114f22ffe9348cd9)

- **作者**: Yuyi Ao
- **时间**: 2026-04-13T19:09:31Z
- **提交信息**: [Doc] Fix Python-only build 404 fallback guidance (#38052)

Signed-off-by: George-ao <yuyiao772@gmail.com>
Signed-off-by: Yuyi Ao <yuyiao772@gmail.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [f414f90](https://github.com/vllm-project/vllm/commit/f414f90601b9ef766017f1fb9398c1bed9bc871a)

- **作者**: JartX
- **时间**: 2026-04-13T18:29:45Z
- **提交信息**: [Bugfix][Kernel][ROCm] Fix triton_w4a16 scales mismatch when BLOCK_K > group_size (#39705)

Signed-off-by: JartX <sagformas@epdcenter.es>

### [8625ec2](https://github.com/vllm-project/vllm/commit/8625ec267b35a158721467e81d5a74ee53091a73)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-04-13T18:15:23Z
- **提交信息**: [Misc] Multi-turn benchmark output performance json (#39572)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [995e9a2](https://github.com/vllm-project/vllm/commit/995e9a209e68a95ffa03c73f3401472837a4072b)

- **作者**: haosdent
- **时间**: 2026-04-13T18:07:40Z
- **提交信息**: [Bugfix] Use is_integrated to detect UMA GPUs for memory reporting (#35356)

Signed-off-by: haosdent <haosdent@gmail.com>
Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>
Co-authored-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [739e594](https://github.com/vllm-project/vllm/commit/739e5945dc4b3ba30d84bdf6e637657abd4136b8)

- **作者**: Yongye Zhu
- **时间**: 2026-04-13T16:53:58Z
- **提交信息**: [Quantization] [Refactor] Create special "GptOssMxfp4MoeMethod" (#39604)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>

### [4d042ed](https://github.com/vllm-project/vllm/commit/4d042ed85f3b8fe8c73b6a4a365e65cf1811823e)

- **作者**: Santino Ramos
- **时间**: 2026-04-13T15:57:38Z
- **提交信息**: [Bugfix] Fix tensor shape mismatch in sparse attention with speculative decoding (#39542)

Signed-off-by: Santino Ramos <santinor@inferact.ai>

### [10d9872](https://github.com/vllm-project/vllm/commit/10d9872d3aee629a47374347c523964eed8cad00)

- **作者**: zhanqiuhu
- **时间**: 2026-04-13T15:16:56Z
- **提交信息**: [CI][Metrics] Fix local_cache_hit assertion after prompt tokens metrics updates (#39709)

Signed-off-by: ZhanqiuHu <zhu@redhat.com>

### [ccd0d1d](https://github.com/vllm-project/vllm/commit/ccd0d1d9067a0bf24330a87044dca272e4a5228c)

- **作者**: Wentao Ye
- **时间**: 2026-04-13T14:53:45Z
- **提交信息**: [Bug] Fix rocm sparse attn indexer issue (#39225)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [d8ddb31](https://github.com/vllm-project/vllm/commit/d8ddb316444e83ce69e5bf20290d1589cbca3db4)

- **作者**: Yi Liu
- **时间**: 2026-04-13T14:50:16Z
- **提交信息**: [Bugfix][CT] Fix KV cache scale handling (#39418)

Signed-off-by: yiliu30 <yi4.liu@intel.com>

### [1ce0318](https://github.com/vllm-project/vllm/commit/1ce0318c6811e8291d6d56777b1f33efb4a0e0f9)

- **作者**: Ekagra Ranjan
- **时间**: 2026-04-13T14:20:07Z
- **提交信息**: [Bugfix] stream failure when model name not in audio endpoints (#36679)

Signed-off-by: Ekagra Ranjan <3116519+ekagra-ranjan@users.noreply.github.com>

### [8d825b8](https://github.com/vllm-project/vllm/commit/8d825b87d6590ca971823890f9705988b8709add)

- **作者**: Tihomir Elek
- **时间**: 2026-04-13T11:13:21Z
- **提交信息**:  [Bug] Fix TypeError when hf_config.architectures is None during model loading (#38849)

Signed-off-by: Tihomir Elek <tiho.elek@gmail.com>

### [1b19bd7](https://github.com/vllm-project/vllm/commit/1b19bd758936496751432eccabf8adb7b5d8936a)

- **作者**: zofia
- **时间**: 2026-04-13T08:59:20Z
- **提交信息**: [MXFP8] [XPU] add a new compressed tensor schema and add a xpu mxfp8 gemm kernel (#38707)

Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>

### [200a727](https://github.com/vllm-project/vllm/commit/200a727e9490d266e3279281c547272b7877c9f0)

- **作者**: Yufeng He
- **时间**: 2026-04-13T08:46:33Z
- **提交信息**: [Bugfix] Fix Responses API instructions leaking through previous_response_id (#37727)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [edbc1ab](https://github.com/vllm-project/vllm/commit/edbc1abd1c206db43dd4d297d773532edbb226a2)

- **作者**: Jesus Federico
- **时间**: 2026-04-13T08:24:09Z
- **提交信息**: feat: add max_tokens_per_doc in rerank request. (#38827)

Signed-off-by: Jesus Federico <jefp@amazon.com>
Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: wang.yuqi <yuqi.wang@daocloud.io>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-04-14
**监控日期**: 2026-04-13
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4270
- **最后更新**: 2026-04-13T22:37:50Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 9
- **主要提交者**: Yuanheng Zhao, 汪志鹏, Didan Deng

## AI分析总结

根据提供的README摘要和提交记录，以下是vllm-omni项目昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：修复了Voxtral TTS输入处理、阶段启动锁释放等问题。
- **性能优化**：提升了VoxCPM2 TTS性能并支持PagedAttention。
- **功能新增**：支持Flux.2-dev的tea_cache、Bagel模型的“思考模式”单阶段部署。
- **文档更新**：更新了异步块设计图。
- **测试与重构**：更新了端到端测试、性能测试用例，清理了单元测试工具，并开始了通信层的重构。

### 2. 关键变更点及其与项目整体方向的关系
- **TTS（文本转语音）增强**：针对Voxtral和VoxCPM2模型的修复与优化，直接支持了项目的“全模态”（omni-modality）目标，提升了语音生成功能的稳定性和效率。
- **多模态模型支持扩展**：对Flux.2-dev（图像生成模型）和Bagel（多模态模型）的更新，进一步丰富了项目支持的模型生态，符合“为所有人提供全模态模型服务”的愿景。
- **底层架构优化**：通信层重构和PagedAttention支持，旨在提升服务端的整体性能和可扩展性，是“快速、廉价”服务目标的技术基础。

### 3. 对项目的影响和潜在意义
- **用户体验提升**：TTS相关修复和性能优化将直接改善语音生成任务的响应速度和输出质量。
- **系统稳定性增强**：多个Bug修复（如锁释放、测试更新）有助于减少运行时错误，提高生产环境可靠性。
- **开发者体验改善**：测试工具统一和文档更新，使项目更易于维护和贡献。
- **架构现代化**：通信层重构为未来更高性能、更分布式的服务部署铺平了道路。

### 4. 值得关注的技术点
- **PagedAttention支持**：这是vLLM生态的核心优化技术之一，将其扩展到TTS任务，可能显著提升长序列语音生成的显存利用率和推理速度。
- **tea_cache for Flux.2-dev**：可能是一种针对图像生成模型的特定缓存优化机制，有助于降低重复生成的成本。
- **通信层重构**：这通常是分布式系统性能瓶颈的关键部分，此次重构可能为后续支持更大规模并发和更复杂的多模态推理管道打下基础。

### 5. 基于项目背景的提交影响分析
vllm-omni旨在成为**易用、快速、廉价的全模态模型服务框架**。昨日的更新紧密围绕这一核心：
- **“全模态”覆盖**：提交聚焦于**语音（TTS）和图像（Flux）** 模态，强化了项目在多模态领域的竞争力，而不仅仅是文本LLM服务。
- **“快速”与“廉价”**：性能优化（如PagedAttention、缓存支持）和底层重构直接服务于提升吞吐、降低延迟和减少计算资源消耗的目标。
- **“易用”与稳定**：Bug修复、测试完善和文档更新，降低了用户和开发者的使用门槛与维护成本，使服务更加可靠。
- **生态扩展**：支持Bagel的“思考模式”等新特性，表明项目正积极集成和优化前沿的多模态模型，保持其技术生态的活力与吸引力。

**总结**：昨日的更新是一次**以优化和巩固为核心**的推进，重点打磨了语音和图像模态的功能与性能，同时着手进行底层架构的现代化改造。这体现了项目在快速扩张功能的同时，并未忽视核心系统的稳健性与效率，正朝着其“全模态高效服务”的愿景稳步迈进。

## 详细提交记录

### [dd13891](https://github.com/vllm-project/vllm-omni/commit/dd1389173b4e2893d21cf742979c89ab0255a5d5)

- **作者**: Chen-Yo Sun
- **时间**: 2026-04-13T22:37:45Z
- **提交信息**: [Voxtral TTS] Fix Voxtral TTS input with text and ref_audio (#2750)

Signed-off-by: Chen-Yo Sun <chenyo.sun@mistral.ai>

### [14f7910](https://github.com/vllm-project/vllm-omni/commit/14f79109000f64f61ca78045abdf5518c0b4fceb)

- **作者**: Sy03
- **时间**: 2026-04-13T21:16:47Z
- **提交信息**: [Perf]: Speedup VoxCPM2 TTS performance and Support PagedAttention (#2690)

Signed-off-by: Sy03 <1370724210@qq.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [c9e2e3e](https://github.com/vllm-project/vllm-omni/commit/c9e2e3e8d764875764ab89c1bfbb294314959e44)

- **作者**: Chen-Yo Sun
- **时间**: 2026-04-13T17:53:35Z
- **提交信息**: [Voxtral TTS] Correct decode steps param in Voxtral TTS (#2524)

Signed-off-by: Chen-Yo Sun <chenyo.sun@mistral.ai>

### [6b5a52a](https://github.com/vllm-project/vllm-omni/commit/6b5a52ae31185a66131eac899b28160e958524bb)

- **作者**: Didan Deng
- **时间**: 2026-04-13T12:50:38Z
- **提交信息**: [Bugfix] Update Flux2-dev & Dynin_omni L4 e2e test (#2723)

Signed-off-by: Didan Deng <33117903+wtomin@users.noreply.github.com>

### [2a1d506](https://github.com/vllm-project/vllm-omni/commit/2a1d5060abbae97648d86f57d70fe5af57d41467)

- **作者**: amy-why-3459
- **时间**: 2026-04-13T12:43:40Z
- **提交信息**: [skip ci][doc]Update async_chunk design diagram (#2420)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [e0cdbe9](https://github.com/vllm-project/vllm-omni/commit/e0cdbe9a5d7ec654bbbe26c2fb6e76abe41446d2)

- **作者**: Yuanheng Zhao
- **时间**: 2026-04-13T11:21:42Z
- **提交信息**: [Misc] Cleanup: use consistent pytest-mock in unit tests (#2698)

Signed-off-by: yuanheng <jonathan.zhaoyh@gmail.com>

### [2c67c30](https://github.com/vllm-project/vllm-omni/commit/2c67c30550ad91e62a5919b0008caba459a09049)

- **作者**: 汪志鹏
- **时间**: 2026-04-13T11:15:49Z
- **提交信息**: [Bagel]: Support `think mode` in single stage deployment of Bagel (#2650)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [ef3f72b](https://github.com/vllm-project/vllm-omni/commit/ef3f72b9ae0bee0baf45258abde55bec3ae6752d)

- **作者**: amy-why-3459
- **时间**: 2026-04-13T11:03:13Z
- **提交信息**: [Tests][Qwen3-Omni]Modify Qwen3-Omni performance test cases (#2600)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [155583f](https://github.com/vllm-project/vllm-omni/commit/155583f49f9a20477ea95a0119a7abfddbf0c646)

- **作者**: Chenguang Zheng
- **时间**: 2026-04-13T10:35:59Z
- **提交信息**: [Bugfix] Release stage launch lock before handshake (#2717)

Signed-off-by: Chenguang ZHENG <645327136@qq.com>

### [cd2761e](https://github.com/vllm-project/vllm-omni/commit/cd2761e15c8e49ea7c53cd551f820318155b4988)

- **作者**: JohnJan
- **时间**: 2026-04-13T09:51:48Z
- **提交信息**: [Feature]: support Flux.2-dev tea_cache (#1871)

Co-authored-by: wuzhongjian <wuzhongjian@cmss.chinamobile.com>

### [0d4e975](https://github.com/vllm-project/vllm-omni/commit/0d4e975e1bf6c574babc7e8279db2b4ff612dd22)

- **作者**: NATURE
- **时间**: 2026-04-13T08:01:14Z
- **提交信息**: [core]refactor communication layer: PR1(Added Refactor Infra Only) (#1555)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
