# GitHub Stars 合并报告 - 2026-06-19

**合并日期**: 2026-06-20
**监控日期**: 2026-06-19
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


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2027
- **最后更新**: 2026-06-19T14:09:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2426
- **最后更新**: 2026-06-19T08:57:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2138
- **最后更新**: 2026-06-19T20:12:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5824
- **最后更新**: 2026-06-19T23:11:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3731
- **最后更新**: 2026-06-19T21:27:06Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Satyam Srivastava, alexzms

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
*   **功能新增 (Feature)**: 提交 `dc66cd9` 引入了新的FP8 QAT线性训练功能。
*   **CI/基础设施 (CI/Infrastructure)**: 提交 `0557f7a` 为CI系统添加了性能仪表盘元数据和可视化功能。

### 2. 关键变更点及其与项目整体方向的关系
*   **FP8 QAT线性训练 (dc66cd9)**: 这是对模型训练流程的核心增强。QAT（量化感知训练）允许模型在训练过程中学习量化带来的精度损失，从而在推理时使用更高效的FP8（8位浮点数）格式。这与FastVideo作为高性能视频生成/处理框架的目标高度一致，旨在**降低模型部署和推理的成本与延迟**，同时保持模型质量。
*   **性能仪表盘 (0557f7a)**: 为CI系统增加了性能数据的可视化。这表明项目团队开始**系统性地追踪和优化性能**，确保每次代码变更不会引入性能退化。这对于一个追求“Fast”的项目至关重要，是项目走向成熟和稳定的标志。

### 3. 对项目的影响和潜在意义
*   **提升模型部署效率**: FP8 QAT训练功能的加入，意味着用户未来可能能够训练出更小、更快、更适合在边缘设备或低功耗服务器上运行的视频模型，而不会显著牺牲生成质量。这直接响应了项目“Fast”的核心理念。
*   **保障项目长期性能**: 性能仪表盘将帮助开发者在开发过程中持续监控性能指标（如训练速度、推理吞吐量）。这能**防止性能回退**，确保项目在功能迭代的同时，其“快速”的核心优势得以保持和优化。

### 4. 值得关注的技术点
*   **FP8 QAT**: 这是一个前沿的模型压缩和加速技术。在视频生成这类计算密集型任务中，FP8相比传统的FP16或FP32能显著减少显存占用和计算时间。QAT是解决FP8量化精度损失的关键技术。
*   **CI/CD性能监控**: 将性能测试集成到CI流程中，并生成可视化仪表盘，是一种先进的工程实践。它表明项目采用了**数据驱动的开发方法**，而非仅凭感觉优化。

### 5. 基于README了解的项目背景，这些提交如何影响项目发展
*   **强化“Fast”品牌定位**: 结合README中强调的“FastVideo”和“Quick Start”，这两个提交都直接服务于“快”这一核心价值。FP8 QAT让模型**运行得更快**，性能仪表盘让开发过程**迭代得更快、更稳**。
*   **推动项目从“可用”走向“易用”和“高效”**: README提供了文档和快速开始指南，这是让项目“可用”。而FP8 QAT和性能仪表盘则是在此基础上，进一步解决用户在实际部署和长期开发中遇到的**效率瓶颈**，使项目在“高效”和“专业”的维度上更进一步。
*   **吸引更广泛的用户和贡献者**: 性能仪表盘展示了项目对代码质量的承诺，FP8 QAT则提供了前沿的技术能力。这两点都能吸引对**高性能计算和模型优化**感兴趣的开发者和研究者，从而壮大社区。

## 详细提交记录

### [0557f7a](https://github.com/hao-ai-lab/FastVideo/commit/0557f7a7d93703c20e1389a77771f09b211cc42e)

- **作者**: Satyam Srivastava
- **时间**: 2026-06-19T21:27:01Z
- **提交信息**: [ci] Add performance dashboard metadata and visualizations (#1470)

### [dc66cd9](https://github.com/hao-ai-lab/FastVideo/commit/dc66cd97efe945f20045e4c6f8776355752fc049)

- **作者**: alexzms
- **时间**: 2026-06-19T08:03:51Z
- **提交信息**: [feat] QAD 5090: FP8 QAT linear training (14/12) (#1464)

Co-authored-by: William Lin <SolitaryThinker@users.noreply.github.com>
Co-authored-by: Loay Rashid <42599591+loaydatrain@users.noreply.github.com>
Co-authored-by: Kaiqin Kong <k1kong@ucsd.edu>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33886
- **最后更新**: 2026-06-19T22:02:54Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hz_Zhang

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的要点分析：

### 1. 主要更新类型

*   **Bug修复**：本次提交的核心是修复一个因`torch.autocast`（自动混合精度）导致的数值精度崩溃问题。

### 2. 关键变更点及其与项目整体方向的关系

*   **修复了`Ideogram4MRoPE`、`ernie_image`、`helios`和`Cosmos3VLTextRotaryEmbedding`中的RoPE（旋转位置编码）计算精度问题。**
    *   **关系**：`diffusers`是一个用于生成图像、视频、音频的扩散模型库。这些模型（如Ideogram4、Cosmos等）都依赖于Transformer架构，而RoPE是Transformer中编码位置信息的关键组件。修复此Bug确保了这些模型在训练和推理时，其位置编码的准确性，直接关系到生成内容的质量（尤其是空间结构）。

*   **通过`torch.autocast(enabled=False)`或`float64`计算，强制RoPE相关计算在`float32`或更高精度下进行。**
    *   **关系**：项目支持多种硬件和精度模式（如`bfloat16`、`float16`），以优化性能和显存。但此修复表明，项目在追求性能优化的同时，也高度重视数值稳定性，特别是对于对精度敏感的组件（如位置编码）。这体现了项目在“性能”与“质量”之间寻求平衡的工程实践。

### 3. 对项目的影响和潜在意义

*   **直接影响**：修复了在使用`torch.autocast`（尤其是在`bfloat16`模式下）训练或运行`Ideogram4`、`Cosmos`等模型时，生成图像退化为“纯色”或质量严重下降的严重Bug。
*   **潜在意义**：
    *   **提升模型鲁棒性**：确保这些模型在各种常见的混合精度训练/推理设置下都能稳定工作，降低了用户的使用门槛和调试成本。
    *   **保障生成质量**：恢复了模型对空间位置信息的正确感知，这对于生成具有复杂空间结构（如人物、场景）的图像至关重要。
    *   **树立代码规范**：为项目中其他可能受`autocast`影响的数值敏感操作（如其他RoPE变体、归一化层等）提供了修复范本，有助于提升整个代码库的健壮性。

### 4. 值得关注的技术点

*   **`bfloat16`的精度陷阱**：`bfloat16`在表示大整数（如`65536`）时，步长（step）很大（为512），导致相邻位置编码无法区分。这是一个典型的因低精度浮点数表示范围有限而导致的数值问题。
*   **`torch.autocast`的作用域**：修复者通过精确地将`autocast(enabled=False)`包裹在关键的矩阵乘法（matmul）或爱因斯坦求和（einsum）操作上，而不是整个函数，这是一种精细且高效的修复方式，避免了不必要的精度切换对性能的影响。
*   **`float64`作为备选方案**：在讨论中，`float64`被提出作为另一种解决方案。它不会被`autocast`降精度，且与`float32`结果一致，但最终选择了更精确的作用域控制，体现了对性能的考量。

### 5. 基于README了解的项目背景，这些提交如何影响项目发展

*   **维护项目核心价值**：`diffusers`的核心价值是提供高质量、易用且可靠的生成模型。这个Bug修复直接维护了这一价值，防止了用户因使用常见的混合精度优化而遭遇“模型失效”的糟糕体验。
*   **支持模型生态的健康发展**：`Ideogram4`、`Cosmos`等是社区中较新或重要的模型。及时修复它们的基础设施问题，有助于这些模型在`diffusers`生态中稳定发展，吸引更多用户和贡献者。
*   **提升项目工程成熟度**：此类对底层数值精度问题的深入排查和修复，是项目从“能用”走向“工程化、可靠”的标志。它表明项目团队不仅关注模型架构，也关注底层计算细节，这对于一个被广泛使用的库至关重要。
*   **总结**：这次更新虽然只涉及一个提交，但解决了一个影响多个模型的、具有代表性的数值精度Bug。它巩固了`diffusers`作为可靠、高质量生成模型库的声誉，并为其支持更复杂、更大规模的模型训练和部署扫清了障碍。

## 详细提交记录

### [6e8c8c4](https://github.com/huggingface/diffusers/commit/6e8c8c4cace3176488fa62760e7b9276fe3da233)

- **作者**: Hz_Zhang
- **时间**: 2026-06-19T22:02:31Z
- **提交信息**: Fix `Ideogram4MRoPE` collapsing under `torch.autocast` (compute rotary in float32) (#13922)

* Fix `Ideogram4MRoPE` collapsing under `torch.autocast` (compute rotary in float32)

Ideogram4 builds image-token positions as IMAGE_POSITION_OFFSET (65536) + (t, h, w).
`Ideogram4MRoPE.forward` casts its operands to float32, but the rotary matmul (and
cos/sin) is on autocast's downcast list, so under torch.autocast("cuda", bfloat16) —
common in training and pipeline code — it runs in bfloat16 anyway. bfloat16's step at
65536 is 512, so every image position in a <=512 grid rounds to the same value: all
image tokens get identical rotary embeddings, spatial information is lost, and the
decoded image degenerates to a flat color.

Wrap the frequency computation in torch.autocast(enabled=False) so the rotary
embeddings are always computed in float32, matching how transformers guards its RoPE
modules. Added a regression test that fails on main and passes with the fix.

Fixes #13920

* Compute the rotary frequencies in float64 instead of disabling autocast

Per review: replace the torch.autocast(enabled=False) guard with a float64 computation,
which autocast does not downcast — matching the float64 rope path used elsewhere (Flux).
The autocast and float32 paths stay bit-identical (max|delta|=0).

* Disable autocast for Ideogram4 rope matmul instead of using float64

Per review, use torch.autocast(enabled=False) around the rotary matmul (as
the original implementation did) rather than computing in float64, and adopt
the clearer comment describing the bfloat16 collapse at the 65536 offset.

* Disable autocast for ernie_image and helios rope einsum

Extend the Ideogram4 fix: ernie_image's `rope` and helios's
`get_frequency_batched` build rotary freqs with an unguarded float32
einsum over raw position ids. Under an ambient autocast the einsum runs in
bfloat16 on CUDA, which cannot represent consecutive integers past 256, so
positions degrade — the same bug, matching the guards mochi/omnigen already
have. Wrap each in torch.autocast(enabled=False).

* Disable autocast for Cosmos3 VL-text rope matmul

Cosmos3VLTextRotaryEmbedding builds its interleaved-mrope freqs with an
unguarded position-id matmul (same shape as Ideogram4), so an ambient autocast
downcasts it to bfloat16 and collapses positions past 256. Wrap in
torch.autocast(enabled=False).

* Tighten autocast(enabled=False) to just the rope matmul

Per review, scope the guard to the precision-sensitive position-id matmul
in Ideogram4 and Cosmos3 rather than the whole freqs block (ernie_image and
helios already wrap only the einsum).

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 416
- **最后更新**: 2026-06-16T09:13:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12601
- **最后更新**: 2026-06-19T22:34:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29324
- **最后更新**: 2026-06-19T23:16:52Z

## 提交统计

- **昨日提交总数**: 31
- **提交者数量**: 17
- **主要提交者**: Michael, Vladislav Nosivskoy, Kangyan-Zhou

## AI分析总结

好的，根据您提供的仓库README摘要和昨日（基于提交时间推断）的提交记录，以下是对 `sgl-project/sglang` 项目昨日更新的分析总结：

### 1. 主要更新类型

- **重构 (Refactor)**: 这是昨日最核心的更新类型，涉及Runner模块的深度重构。
- **功能新增 (Feature)**: 主要集中在Router（路由）和AMD GPU支持方面。
- **性能优化 (Performance)**: 包括Router的Tokenize优化、AMD平台的内核适配和Runner的静态缓冲区重用。
- **Bug修复 (Bug Fix)**: 修复了模型加载、CUDA图执行、NPU测试等问题。
- **CI/测试 (CI/Testing)**: 大量CI相关更新，包括新增AMD测试、调整GPU池、发布性能追踪、升级Action版本等。
- **文档/规范 (Documentation/Governance)**: 新增了行为准则（CODE_OF_CONDUCT.md）。
- **其他**: 包括代码清理、基准测试工具迁移、Speculative Decoding路径统一等。

### 2. 关键变更点及其与项目整体方向的关系

- **Runner模块深度重构 (提交 14, 27, 28, 11, 12, 13)**:
    - **变更**: 将原有的Runner拆分为`BaseRunner`、`BaseCudaGraphRunner`和`EagerRunner`，并重构了预热、缓冲区管理等逻辑。
    - **关系**: 这与README中强调的“高效推理”核心目标高度一致。通过模块化和多态化，为未来支持更多硬件后端（如AMD、NPU）和不同的执行模式（Eager vs. CUDA Graph）奠定了更清晰、可扩展的架构基础。

- **Router (路由层) 优化与增强 (提交 1, 3, 20)**:
    - **变更**: 1. 在入口处一次性完成Tokenize，并将`input_ids`直接转发给引擎，避免重复计算。2. 将聊天体上限提升至5 MiB以支持超长上下文。3. 对齐Router的TTFT（首Token延迟）指标桶与引擎的网格。
    - **关系**: 这些改进直接提升了作为“服务网关”的Router的性能和准确性。一次性Tokenize和提升上下文上限，对于处理长文档、复杂对话等场景至关重要，符合项目支持“长上下文”和“高吞吐”的定位。

- **AMD GPU 支持强化 (提交 4, 16, 17, 22)**:
    - **变更**: 为AMD GPU注册了更多CI测试，移植了关键的`kv_canary`内核，启用了`HiSparse`（一种稀疏计算技术），并使可中断的CUDA图能够在ROCm上运行。
    - **关系**: 这表明项目正在积极扩展硬件生态，降低对单一GPU厂商的依赖。AMD在AI推理领域的市场份额正在增长，此更新对吸引AMD用户、提升项目在特定场景下的性价比至关重要。

- **CI/CD 基础设施优化 (提交 5, 6, 10, 26)**:
    - **变更**: 新增4-GPU MI35X运行器以平衡负载，发布4-GPU的夜间性能追踪，升级GitHub Action版本，以及优化失败重跑流程。
    - **关系**: 这些是项目健康发展的“幕后”工作。更高效的CI意味着更快的迭代速度和更稳定的代码质量，对大型开源项目至关重要。

### 3. 对项目的影响和潜在意义

- **架构清晰度与可维护性**: Runner的重构是影响深远的内部改进。它将使未来的功能开发（如支持新硬件、新执行模式）更加容易，降低代码耦合和引入Bug的风险。
- **性能与用户体验**: Router的优化将直接降低端到端延迟，尤其是在处理长上下文时。这对于构建实时聊天机器人、代码助手等应用的用户体验提升显著。
- **硬件兼容性**: AMD支持的加强，使项目不再局限于NVIDIA GPU，扩大了潜在用户群和部署场景（如使用AMD服务器的数据中心）。
- **项目成熟度**: 新增行为准则、优化CI流程、发布性能追踪等，都是项目走向成熟、规范化的标志，有助于吸引更多贡献者和企业用户。

### 4. 值得关注的技术点

- **`EagerRunner` 的引入**: 这是对现有CUDA Graph执行路径的补充。Eager模式（逐算子执行）虽然可能慢一些，但调试更友好，且在某些动态场景下可能更灵活。这种“双轨制”设计是高性能推理框架的常见做法。
- **Router的“一次Tokenize”策略**: 这是一种典型的“去重”优化，通过将Tokenization前置并复用结果，减少了引擎的重复计算，是提升Router吞吐的有效手段。
- **`HiSparse` 在AMD上的启用**: 稀疏计算是减少模型计算量和内存占用的关键技术。将其移植到AMD平台，意味着AMD用户也能享受到这一性能红利。
- **Speculative Decoding路径统一**: 将推测性语法Token的接受路径统一，简化了代码逻辑，有助于未来集成更复杂的推测解码策略。

### 5. 基于项目背景，这些提交如何影响项目发展

- **巩固“高性能推理引擎”的核心定位**: Runner重构和Router优化直接服务于“更快、更高效”的目标。这些是项目的立身之本。
- **拓展“多硬件平台”的战略方向**: 对AMD的持续投入，是项目从“NVIDIA专属”向“硬件无关”转变的关键一步。这能吸引更广泛的社区，并降低用户的硬件采购成本。
- **提升“生产级服务”的成熟

## 详细提交记录

### [364bf97](https://github.com/sgl-project/sglang/commit/364bf976be6f2fce2e291c0721fca492a4e91ca0)

- **作者**: Kangyan-Zhou
- **时间**: 2026-06-19T23:07:17Z
- **提交信息**: [router] Tokenize prompt once at ingress; forward input_ids to the engine (all policies) (#28744)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [c3bae61](https://github.com/sgl-project/sglang/commit/c3bae61e1668c074523888d1693a2bd2f768a28a)

- **作者**: Shu Wang
- **时间**: 2026-06-19T22:57:45Z
- **提交信息**: [Bug] fix(DummyModelLoader): run post_load_weights before process_weights_after_loading (#28665)

### [abf7011](https://github.com/sgl-project/sglang/commit/abf7011cdd10c544fac24350e437ecd46607bb43)

- **作者**: Kangyan-Zhou
- **时间**: 2026-06-19T22:50:34Z
- **提交信息**: [router] Raise chat body cap to 5 MiB for long contexts (#28742)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [4200048](https://github.com/sgl-project/sglang/commit/420004827c4e5b116f31ed0a52c516dd6998ceb2)

- **作者**: Michael
- **时间**: 2026-06-19T22:45:16Z
- **提交信息**: [AMD] register 3 tests to stage-b-test-1-gpu-large-amd (batch-6) (#28736)

### [13aab2f](https://github.com/sgl-project/sglang/commit/13aab2fc069c0135f31eb5fd2d8649cfdf6c3050)

- **作者**: Michael
- **时间**: 2026-06-19T22:41:19Z
- **提交信息**: ci: add 4-GPU mi35x runner and rebalance off the saturated 8-GPU pool (#28745)

Co-authored-by: michaelzhang-ai <michaelzhang-ai@users.noreply.github.com>

### [3a57484](https://github.com/sgl-project/sglang/commit/3a574846ff58cdcedf7568bffaf5132e002a9a3e)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-19T22:27:24Z
- **提交信息**: [CI] Publish 4-GPU nightly profiler traces (#28738)

### [b225f48](https://github.com/sgl-project/sglang/commit/b225f48fccd2bf5731123d9e7ca095089c9845d7)

- **作者**: Elizaveta Martirosian
- **时间**: 2026-06-19T22:14:26Z
- **提交信息**: [NPU][FIX CI] Set the warm-up mode to "request" for NPU diffusion tests (#28724)

Co-authored-by: Elizaveta Martirosian <elizaveta.martirosian@gmail.com>

### [3ed46f5](https://github.com/sgl-project/sglang/commit/3ed46f599f08b83bedd7be6872ab7d0daf237179)

- **作者**: Jonny Kong
- **时间**: 2026-06-19T22:12:07Z
- **提交信息**: [core] Don't force seq_lens_cpu publication under piecewise CUDA graph (#28633)

Co-authored-by: jonnykong <jonnykong@fb.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [d271de6](https://github.com/sgl-project/sglang/commit/d271de64fe92678ad3236ec965c0edd9cfe1b505)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-19T21:19:29Z
- **提交信息**: [misc] Move bench_one_batch_server into sglang/benchmark/ with a back-compat shim (#28625)

### [c9c2445](https://github.com/sgl-project/sglang/commit/c9c244514669900e9a50ab835d4b76ee0e649a3e)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-19T21:18:37Z
- **提交信息**: [CI] Bump actions/github-script to v8 (Node 24 runtime) (#28741)

### [6fdcb99](https://github.com/sgl-project/sglang/commit/6fdcb9934cee42bdb1c5247d323d21b554d58da4)

- **作者**: Cheng Wan
- **时间**: 2026-06-19T20:23:26Z
- **提交信息**: fix(runner): size eager static buffers for prefill budget and MLP-sync autotune (#28677)

### [2aa7b58](https://github.com/sgl-project/sglang/commit/2aa7b58aa7981b0df4428de83ba8fe20cfcd4f55)

- **作者**: Cheng Wan
- **时间**: 2026-06-19T20:16:07Z
- **提交信息**: refactor(runner): reuse a prepared static buffer for every dummy run (#28740)

### [856b0dc](https://github.com/sgl-project/sglang/commit/856b0dc74b774cfbacc4b4d01d43224f000de14a)

- **作者**: Cheng Wan
- **时间**: 2026-06-19T20:13:13Z
- **提交信息**: refactor(runner): move kernel warmup into the shared runner lifecycle (warmup()) (#28739)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [d705a91](https://github.com/sgl-project/sglang/commit/d705a91de19a3b3de05325252a6bacd7529490b2)

- **作者**: Cheng Wan
- **时间**: 2026-06-19T20:05:43Z
- **提交信息**: refactor(runner): add EagerRunner, own the eager path, polymorphic dispatch (#28386)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [ab0714d](https://github.com/sgl-project/sglang/commit/ab0714d0ee7484b49e387cce649ec9d508aa7622)

- **作者**: Alison Shao
- **时间**: 2026-06-19T19:24:38Z
- **提交信息**: ci: run GB300 nightly suite in the standard Nvidia nightly workflow (#28536)

Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [7c505c2](https://github.com/sgl-project/sglang/commit/7c505c2927728e2d5ebf7de21a46f857f8f37bba)

- **作者**: Michael
- **时间**: 2026-06-19T19:19:37Z
- **提交信息**: [AMD] fix(jit): port kv_canary write/verify/plan kernels to ROCm (#28357)

### [c436a81](https://github.com/sgl-project/sglang/commit/c436a8161ab824efc1555b22d394a8b25e3446f6)

- **作者**: Clint
- **时间**: 2026-06-19T18:59:45Z
- **提交信息**: [AMD] Enable HiSparse on ROCm (#26639)

Co-authored-by: clintg6 <7388379+clintg6@users.noreply.github.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [ca88b7f](https://github.com/sgl-project/sglang/commit/ca88b7f1d2ccefde7857feb644933173ff57c163)

- **作者**: Jaybe
- **时间**: 2026-06-19T17:41:51Z
- **提交信息**: fix: remove manual rope parameters injection in `PretrainedConfig` (#23910)

### [2ad9a5b](https://github.com/sgl-project/sglang/commit/2ad9a5b576d61d61ac8132e1c1440a0cfd85dd9a)

- **作者**: Vladislav Nosivskoy
- **时间**: 2026-06-19T16:18:01Z
- **提交信息**: [UnifiedTree] Use dense model for HiCache+CP KL tests  (#28726)

### [cab6285](https://github.com/sgl-project/sglang/commit/cab62855f589b47e3b11a97ea6bbc3f9d7b2dea0)

- **作者**: Kangyan-Zhou
- **时间**: 2026-06-19T15:53:46Z
- **提交信息**: [router] Align sgl_router_ttft_seconds buckets with engine TTFT grid (#28717)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [88c261c](https://github.com/sgl-project/sglang/commit/88c261c3f34cc5b05b35654e4defa6fe6c534bf1)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-19T15:39:09Z
- **提交信息**: Fix IndexCache PP topk handoff (#28532)

### [3af991f](https://github.com/sgl-project/sglang/commit/3af991fb3eede82357568ec28882f11fe7830365)

- **作者**: Oguz Ulgen
- **时间**: 2026-06-19T14:16:00Z
- **提交信息**: [AMD] Make breakable CUDA graph run on ROCm/HIP (#28173)

### [5eaae5b](https://github.com/sgl-project/sglang/commit/5eaae5bacd1244cc05c8845f31c051df5b761979)

- **作者**: sglang-bot
- **时间**: 2026-06-19T14:08:05Z
- **提交信息**: Add CODE_OF_CONDUCT.md (#28728)

Co-authored-by: Claude Sonnet 4.6 (1M context) <noreply@anthropic.com>

### [9bb9d17](https://github.com/sgl-project/sglang/commit/9bb9d17e1ab26d50b91e5672b7ffcac800faafc7)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-19T09:49:40Z
- **提交信息**: [Spec] Unify speculative grammar token-accept path in decode processing (#28682)

### [941a11a](https://github.com/sgl-project/sglang/commit/941a11ada3fcc301958ffe7d36c6c7b3f478aac4)

- **作者**: shuwenn
- **时间**: 2026-06-19T09:46:04Z
- **提交信息**: [HiCache] refactor: remove unused transfer buffer (#26003)

### [0146692](https://github.com/sgl-project/sglang/commit/0146692cc9e3a5351642b0cc699151e5dba2938b)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-19T09:07:52Z
- **提交信息**: [CI] Fail fast on empty install_script in Rerun Test workflow (#28721)

### [a6db86d](https://github.com/sgl-project/sglang/commit/a6db86d535c92fd1520dcfa147a8e2ddf4d0c48e)

- **作者**: Cheng Wan
- **时间**: 2026-06-19T09:04:15Z
- **提交信息**: refactor(runner): split BaseRunner (shared) from BaseCudaGraphRunner (#28385)

### [1c6331c](https://github.com/sgl-project/sglang/commit/1c6331cbd67f34863703f82fe0786694974f41dd)

- **作者**: Cheng Wan
- **时间**: 2026-06-19T08:45:04Z
- **提交信息**: refactor(runner): rename runner replay/load/can_run for the shared surface (#28384)

### [31c0a98](https://github.com/sgl-project/sglang/commit/31c0a980665b4f40e10e161aa5a4cb6b2857e0a6)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-19T08:37:59Z
- **提交信息**: [codex] Update diffusion skills for latest main (#28711)

### [b6be5dd](https://github.com/sgl-project/sglang/commit/b6be5dd20f314f8cc7ac50652489bdf6d7116e7f)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-19T08:26:44Z
- **提交信息**: [codex] Remove outdated SGLang SOTA skill (#28719)

### [af2ec2a](https://github.com/sgl-project/sglang/commit/af2ec2a0ddbd0249ba8e8a755765fa685a79a426)

- **作者**: Mick
- **时间**: 2026-06-19T07:41:47Z
- **提交信息**: [diffusion] perf: merge LTX-2 stage-1 distilled LoRA into the base in original mode (#28594)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1205
- **最后更新**: 2026-06-18T14:38:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 83354
- **最后更新**: 2026-06-19T22:52:48Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 10
- **主要提交者**: Ben Browning, Harry Mellor, Tyler Michael Smith

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bugfix):** 修复了内存泄漏、字符编码问题、文档链接失效和参数验证错误。
- **硬件适配 (ROCm/XPU):** 针对 AMD ROCm 和 Intel XPU 平台进行了多项修复、测试优化和功能增强。
- **测试与CI (Test/CI):** 迁移测试框架、优化 CI 流程、修复特定硬件上的测试问题。
- **功能增强 (Feature):** 为 DeepSeek V4 模型实现了 KV 缓存打包优化。
- **重构 (Refactor):** 完成了 `_C` 库内核的最终迁移。
- **文档更新 (Documentation):** 修复了文档中的死链接，并移动了 CI 故障诊断文档。

### 2. 关键变更点及其与项目整体方向的关系

- **DeepSeek V4 KV 缓存优化 (commit 9):** 将 KV 缓存打包成连续的、按块分配的内存。这与 vLLM 的核心目标——**高效、低成本地服务大模型**——高度一致。通过优化内存布局，可以显著提升 DeepSeek V4 这类长上下文模型的推理吞吐量和内存利用率。
- **ROCm 平台持续改进 (commits 1, 2, 4, 6):** 修复了 AMD GPU 上的内存泄漏、跳过了不兼容的测试、并优化了 FP8 量化精度测试。这体现了 vLLM 致力于 **“为所有人”** 提供服务的愿景，通过积极适配 AMD 硬件，扩大了其用户基础，降低了对 NVIDIA 硬件的依赖。
- **`_C` 库内核迁移完成 (commit 10):** 完成了将核心内核从 `_C` 库迁移到更现代、更易维护的架构中。这是重要的**重构**工作，旨在提升代码库的可维护性和长期性能，为未来的优化和功能扩展奠定基础。
- **Bug修复与健壮性提升 (commits 3, 7, 11):** 修复了解析器中的字符编码泄漏、文档死链接和参数验证错误。这些修复直接提升了 vLLM 的**稳定性和易用性**，是提供“简单易用”服务体验的关键保障。

### 3. 对项目的影响和潜在意义

- **性能与效率提升:** DeepSeek V4 的 KV 缓存优化是本次更新中最具性能影响力的变更，有望显著降低该模型的内存占用并提高推理速度。
- **硬件生态扩展:** 对 ROCm 和 XPU 的持续投入，巩固了 vLLM 作为多硬件平台 LLM 服务框架的领先地位，这对于项目的长期发展和社区建设至关重要。
- **代码质量与可维护性:** `_C` 库迁移的完成和测试框架的升级，表明项目在快速迭代的同时，也在持续关注代码质量和长期健康度。这降低了未来的维护成本和技术债务。
- **用户体验提升:** 修复文档链接和参数验证错误，直接改善了开发者和用户的日常使用体验，减少了困惑和调试时间。

### 4. 值得关注的技术点

- **DeepSeek V4 的 KV 缓存打包策略:** 这是针对特定模型架构（MoE，长上下文）的深度优化。其实现细节（如何实现“连续按块分配”）值得关注，可能成为未来其他长上下文模型优化的参考。
- **`_C` 库内核迁移的最终状态:** 了解迁移后的新架构（commit 10 是 `12/n` 系列的最后一步），可以洞察 vLLM 未来内核开发的模式和方向。
- **ROCm 上的 FP8 量化:** commit 6 提到“使用 vLLM 的 fp8 量化最大值”，这表明 vLLM 正在建立自己的一套 FP8 量化标准，以确保在不同硬件（NVIDIA/AMD）上的一致性和准确性。
- **Schemathesis 4.x 迁移:** 这是一个测试框架的升级，表明项目正在采用更先进的测试工具来保证 API 的健壮性。

### 5. 结合项目背景，这些提交如何影响项目发展

根据 README，vLLM 的目标是 **“为每个人提供简单、快速、廉价的 LLM 服务”**。昨日的更新从多个维度推动了这一目标的实现：

- **“快速”与“廉价”**: DeepSeek V4 的 KV 缓存优化直接提升了速度并降低了内存成本。`_C` 库迁移为未来的性能优化铺平了道路。
- **“为每个人”**: 对 ROCm 和 XPU 的持续投入，打破了硬件壁垒，让更多使用非 NVIDIA 硬件的用户也能享受到 vLLM 的高性能服务。修复各种 Bug 和文档问题，降低了所有用户的使用门槛。
- **“简单”**: 修复参数验证错误和文档死链接，让 API 更易用，文档更可靠，简化了用户的开发和部署流程。

**总结来说，昨日的更新体现了 vLLM 项目在追求极致性能（通过模型特定优化和架构重构）的同时，也高度重视项目的健壮性、可维护性和硬件生态的多样性，这正是其成为主流 LLM 服务框架的关键。**

## 详细提交记录

### [0fbf42a](https://github.com/vllm-project/vllm/commit/0fbf42af841993ab1c189efca34de6b9799526b7)

- **作者**: djramic
- **时间**: 2026-06-19T22:20:59Z
- **提交信息**: [ROCm] Fix VRAM not freed in test_phi3v (#46046)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [e6cd891](https://github.com/vllm-project/vllm/commit/e6cd8913ddfe63b4620e45ff8c2da1d37318dbe5)

- **作者**: Charlie Fu
- **时间**: 2026-06-19T22:20:10Z
- **提交信息**: [ROCm][CI] Skip Qwen3.5-35B-A3B-MXFP4-AITER-TP2 for non gfx950 (#46109)

Signed-off-by: charlifu <charlifu@amd.com>

### [859e4d4](https://github.com/vllm-project/vllm/commit/859e4d436ba0fb0da8a655a80d5c4fab12adc82e)

- **作者**: Ben Browning
- **时间**: 2026-06-19T22:09:28Z
- **提交信息**: [Bugfix][Parser] Fix U+FFFD leak at reasoning-to-content transition in engine parsers (#46159)

Signed-off-by: Ben Browning <bbrownin@redhat.com>

### [4a083cc](https://github.com/vllm-project/vllm/commit/4a083cc858f075209dd964ade48c0f8ec87c3393)

- **作者**: Micah Williamson
- **时间**: 2026-06-19T20:20:06Z
- **提交信息**: [ROCm][CI] Pin `test_rocm_compressed_tensors_w8a8` to TRITON_ATTN (#46180)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [ca7e1f2](https://github.com/vllm-project/vllm/commit/ca7e1f2c43834d1e720b7377e2832097978c1e35)

- **作者**: Vadim Gimpelson
- **时间**: 2026-06-19T20:12:40Z
- **提交信息**: Move CI failure diagnosis docs into ci-fails-buildkite skill (#45975)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>

### [dec860f](https://github.com/vllm-project/vllm/commit/dec860fb19fcd8a39c62a2204c5939feb4781f14)

- **作者**: djramic
- **时间**: 2026-06-19T18:24:02Z
- **提交信息**: [ROCm] Use vLLM's fp8 quant max in AITER hipBLASLt accuracy test (#46176)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [0a49fb2](https://github.com/vllm-project/vllm/commit/0a49fb2b13e474be71723c589cec5f4df1b5341d)

- **作者**: Harry Mellor
- **时间**: 2026-06-19T18:16:09Z
- **提交信息**: Fix dead link in docs (#46181)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [4a8abf3](https://github.com/vllm-project/vllm/commit/4a8abf37c75b4a2587bfdad48bc6b442dc71332a)

- **作者**: Ben Browning
- **时间**: 2026-06-19T18:05:18Z
- **提交信息**: [Test] Migrate test_openai_schema.py to schemathesis 4.x (#46173)

Signed-off-by: Ben Browning <bbrownin@redhat.com>

### [0119213](https://github.com/vllm-project/vllm/commit/01192139bf022bec84e2cca3a3e36e8bb5293b5c)

- **作者**: Tyler Michael Smith
- **时间**: 2026-06-19T16:55:42Z
- **提交信息**: [DSv4] Pack KV caches into contiguous per-block allocations for DeepSeek V4 (#44577)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [b9a7cd4](https://github.com/vllm-project/vllm/commit/b9a7cd464c9ae9b1b450f8982b76d7be4de73724)

- **作者**: Chris Leonard
- **时间**: 2026-06-19T13:57:26Z
- **提交信息**: [12/n]  final _C library kernel migration (#45415)

### [69bdd34](https://github.com/vllm-project/vllm/commit/69bdd345428408a2fdf745e225c87defbc2c07d0)

- **作者**: Muhammad Fawaz
- **时间**: 2026-06-19T11:11:11Z
- **提交信息**: [Bugfix] Fall back to Pydantic loc for param in validation errors (#46038)

Signed-off-by: professorsab <135441198+professorsab@users.noreply.github.com>
Co-authored-by: Mahad Durrani <114791389+mahadrehmann@users.noreply.github.com>

### [ec67d7a](https://github.com/vllm-project/vllm/commit/ec67d7ae619435f5f27279081f40e3a733ca9ab7)

- **作者**: Kunshang Ji
- **时间**: 2026-06-19T07:37:20Z
- **提交信息**: [xpu] bump up vllm-xpu-kernels v0.1.10 and upgrade 2618 umd (#40367)

Signed-off-by: Kunshang Ji <jikunshang95@gmail.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-20
**监控日期**: 2026-06-19
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5211
- **最后更新**: 2026-06-19T22:56:49Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Kwokho Tsui, Yueqian Lin

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
*   **Bug修复**
*   **代码清理与重构**

### 2. 关键变更点及其与项目整体方向的关系

*   **提交 `7e152ca` [Bugfix] Fix HSDP + FP8 online quantization compatibility**
    *   **变更点**: 修复了**HSDP (混合分片数据并行)** 与 **FP8在线量化** 同时使用时的兼容性问题。
    *   **与项目方向的关系**: 该项目旨在提供“Easy, fast, and cheap”的全模态模型服务。FP8量化是实现“fast”和“cheap”（低延迟、低成本）的关键技术，而HSDP是支持大规模模型“fast”训练和推理的分布式策略。修复两者兼容性，直接服务于项目核心目标，确保在追求高性能和低成本时，系统稳定可靠。

*   **提交 `2089322` [Chore][TTS] Reference recipes.vllm.ai recipes, remove dead code, and fix stale references**
    *   **变更点**: 针对**TTS (文本转语音)** 模块，更新了文档引用（指向 `recipes.vllm.ai`），移除了无用代码，并修复了过时的引用。
    *   **与项目方向的关系**: 该项目定位为“omni-modality”（全模态），TTS是其中的关键模态之一。此提交通过清理代码和更新文档，提升了TTS模块的**可维护性**和**易用性**（Easy），符合项目“Easy”的承诺。移除死代码也有助于提升代码质量和潜在性能。

### 3. 对项目的影响和潜在意义

*   **稳定性提升**: 修复HSDP与FP8的兼容性问题，直接提升了在分布式环境下使用量化模型进行推理的稳定性，这对于生产环境部署至关重要。
*   **代码质量改善**: TTS模块的代码清理和文档更新，降低了后续开发的维护成本，并为用户提供了更准确、更易遵循的参考（通过 `recipes.vllm.ai`），有助于吸引和留住开发者与用户。
*   **潜在性能优化**: 移除死代码可能间接带来微小的性能提升，并减少潜在的bug来源。

### 4. 值得关注的技术点

*   **HSDP + FP8 兼容性**: 这是一个相对前沿的组合。HSDP在模型并行和数据并行之间提供了更灵活的权衡，而FP8量化是降低显存占用和计算开销的有效手段。修复它们的兼容性问题，表明项目在探索和优化高性能推理的先进技术栈。
*   **`recipes.vllm.ai`**: 这表明项目正在建立一个集中的、标准化的使用指南或示例库，有助于统一最佳实践，降低用户上手门槛。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **巩固“Fast”和“Cheap”的承诺**: 通过修复HSDP+FP8的bug，项目在“快速”和“廉价”这两个核心价值上迈出了坚实的一步，使其在竞争激烈的模型服务市场中更具吸引力。
*   **完善“Easy”的体验**: TTS模块的代码和文档清理，直接提升了“易用性”。对于全模态服务来说，每个模态的易用性都至关重要，这有助于构建一个更友好、更成熟的生态系统。
*   **推动全模态战略**: 这两个提交分别针对了**性能优化**（FP8/HSDP）和**模态完善**（TTS），共同推动了项目向“全模态、高性能、易使用”的最终目标前进。这表明项目不仅在横向扩展支持的模态，也在纵向深入优化每个模态的服务质量。

## 详细提交记录

### [7e152ca](https://github.com/vllm-project/vllm-omni/commit/7e152ca64b6627eaf80eb7d94d271bd504f16b1a)

- **作者**: Kwokho Tsui
- **时间**: 2026-06-19T07:06:27Z
- **提交信息**: [Bugfix] Fix HSDP + FP8 online quantization compatibility (#4494)

Signed-off-by: Kwokho Tsui <kh_tsui@163.com>
Co-authored-by: Kwokho Tsui <kh_tsui@163.com>

### [2089322](https://github.com/vllm-project/vllm-omni/commit/208932210f118940cd88880c3f7ab52960903327)

- **作者**: Yueqian Lin
- **时间**: 2026-06-19T07:05:26Z
- **提交信息**: [Chore][TTS] Reference recipes.vllm.ai recipes, remove dead code, and fix stale references (#4567)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

---
