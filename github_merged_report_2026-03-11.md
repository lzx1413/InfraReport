# GitHub Stars 合并报告 - 2026-03-11

**合并日期**: 2026-03-12
**监控日期**: 2026-03-11
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


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1714
- **最后更新**: 2026-03-11T10:40:00Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: Ting, Yifan Pi

## AI分析总结

根据您提供的README摘要和提交记录，结合项目“VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo”的背景，以下是昨日更新的要点分析：

### 1. 主要更新类型
*   **功能新增 (Feature)**: 1项
*   **Bug修复 (Fix)**: 3项
*   **性能优化、文档更新、重构**: 无

### 2. 关键变更点及其与项目整体方向的关系
*   **新增模型支持 (`qwen3_5_moe`)**: 扩展了VeOmni支持的模型库，使其能够处理Qwen3.5 MoE架构的语言模型。这直接契合项目“Scaling Any Modality Model Training”的目标，通过增加新的模型配方来提升框架的通用性和覆盖面。
*   **数据转换逻辑修复 (两项)**: 修复了数据预处理流水线中`source_name`字段的优先级和回退逻辑。这确保了多模态数据（如图像、音频、文本）在进入模型前能被正确识别和转换，是支撑“Any Modality”训练稳定性的基础。
*   **模型输入形状修复 (Qwen3OmniMoE音频)**: 修正了Qwen3 Omni MoE模型在处理音频模态时的虚拟输入形状。这保证了特定多模态模型在训练或推理时输入张量的正确性，是模型正确运行的前提。

### 3. 对项目的影响和潜在意义
*   **增强框架能力**: 新增模型支持使VeOmni能服务于更广泛的用户和研发场景。
*   **提升鲁棒性与用户体验**: 连续的数据和模型相关修复，提高了框架在处理复杂、真实数据集时的稳定性和可靠性，减少了用户踩坑的可能。
*   **聚焦多模态与MoE架构**: 提交明显围绕**多模态数据处理**和**混合专家模型**展开，表明项目当前正深入优化对这些前沿、复杂技术的支持。

### 4. 值得关注的技术点
*   **MoE模型集成**: 对`qwen3_5_moe`的支持表明VeOmni正在积极集成高效的稀疏模型架构，这对于训练大规模模型至关重要。
*   **灵活的数据管道设计**: 数据转换中`kwargs`与样本字段的优先级设计，以及`source`键的回退机制，体现了框架为适配多样化的多模态数据源所做的灵活设计。
*   **模态特定输入处理**: 修复音频输入形状，凸显了在多模态模型中，不同模态数据预处理和模型接口适配的具体挑战。

### 5. 基于项目背景的提交影响分析
VeOmni旨在成为一个**模型中心化的分布式训练配方库**。昨日的提交完美体现了这一核心方向：
*   **“配方库”扩展**: 新增`qwen3_5_moe`支持，本质上是向“配方库”中添加了一个新的、重要的模型训练配方，丰富了生态。
*   **“模型中心化”实践**: 所有修复都紧密围绕**模型**（Qwen3 Omni MoE）的正确运行和**数据**如何适配模型展开，强化了以模型需求为核心来设计数据流程和分布式策略的理念。
*   **支撑“Any Modality”**: 对数据转换逻辑和音频输入的处理，直接针对多模态训练中的痛点，确保框架在支持任意模态组合时的基础牢固。

**总结**：昨日的更新是一次**扎实的迭代**，未改变项目核心架构，而是通过**扩展模型支持**和**夯实基础功能**，使VeOmni朝着其“成为支持任意模态、任何模型的大规模分布式训练通用解决方案”的愿景更迈进了一步。它反映出项目目前处于功能完善和生态建设阶段。

## 详细提交记录

### [8e85008](https://github.com/ByteDance-Seed/VeOmni/commit/8e85008bd4686edb2a26fce8653043c0a27034da)

- **作者**: Yifan Pi
- **时间**: 2026-03-11T10:39:55Z
- **提交信息**: [model] feat: Add qwen3_5_moe support (language model only) (#547)

### [0492d32](https://github.com/ByteDance-Seed/VeOmni/commit/0492d32836f585c9f67a4609ba865ec9723fbbb9)

- **作者**: Ting
- **时间**: 2026-03-11T10:02:29Z
- **提交信息**: [data] fix: prioritize kwargs source_name over sample fields in data transform (#554)

### [29d396a](https://github.com/ByteDance-Seed/VeOmni/commit/29d396a2b93d95eda539407b406df3cc85d712a2)

- **作者**: Ting
- **时间**: 2026-03-11T08:41:41Z
- **提交信息**: [data] fix: fallback to "source" key when "source_name" is missing in data transform (#553)

### [153c8ec](https://github.com/ByteDance-Seed/VeOmni/commit/153c8ec042daf389015485e99d78fec1e111df3f)

- **作者**: Ting
- **时间**: 2026-03-11T07:02:51Z
- **提交信息**: [data, model] fix: Fix Qwen3OmniMoE audio dummy input shape (#550)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2051
- **最后更新**: 2026-03-11T15:24:22Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: LiangLiu

## AI分析总结

根据提供的仓库README摘要和提交记录，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：修复了内存泄漏问题。

### 2. 关键变更点及其与项目整体方向的关系
- **修复 `ltx2 stop_signal` 导致的内存泄漏**：该问题涉及框架在停止信号处理时未能正确释放内存，可能导致长时间运行或高负载下资源耗尽。
- **与项目方向的关系**：LightX2V 作为轻量级视频生成推理框架，核心目标之一是高效、稳定地处理视频生成任务。修复内存泄漏直接提升了框架的**稳定性和资源效率**，符合其“轻量、高效”的定位，确保在持续推理场景下可靠运行。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：减少因内存泄漏导致的崩溃或性能下降风险，增强框架在生产环境中的可靠性。
- **资源优化**：避免无效内存占用，可能降低长期运行成本，尤其对部署在资源受限环境（如边缘设备）有益。
- **用户体验改善**：用户无需手动处理内存问题，提升了使用体验。

### 4. 值得关注的技术点
- **内存管理机制**：修复涉及信号处理（`stop_signal`）与内存释放的交互，可能涉及异步操作或资源生命周期管理，值得开发者关注类似场景下的最佳实践。
- **问题定位（#938）**：通过 Issue 编号可见该问题已被跟踪，反映项目有较好的问题管理流程。

### 5. 基于项目背景的提交影响分析
- **README 背景**：LightX2V 旨在提供高效的视频生成推理框架，强调轻量化和性能。
- **影响发展**：
  - **巩固核心优势**：修复此类底层 Bug 有助于维护框架“轻量高效”的声誉，避免因稳定性问题影响用户采纳。
  - **促进长期采用**：稳定的内存管理是框架能否支持大规模或持续应用的关键，此次修复可能吸引更多注重可靠性的用户或企业级应用。
  - **技术债减少**：及时修复内存泄漏有助于保持代码库健康，为后续功能迭代（如性能优化或新模型支持）奠定基础。

**总结**：昨日更新虽仅涉及一个 Bug 修复，但针对关键的内存泄漏问题，直接强化了框架的稳定性和效率，与 LightX2V 的轻量高效目标高度一致，是一次对项目长期健康发展有积极影响的维护性提交。

## 详细提交记录

### [ca39ec4](https://github.com/ModelTC/LightX2V/commit/ca39ec400116cf57a4ee47e3f8d7f20bcd28f77e)

- **作者**: LiangLiu
- **时间**: 2026-03-11T07:33:26Z
- **提交信息**: fix ltx2 stop_signal -> mermory leak (#938)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1955
- **最后更新**: 2026-03-10T14:14:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5122
- **最后更新**: 2026-03-11T21:33:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3144
- **最后更新**: 2026-03-11T09:29:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 32998
- **最后更新**: 2026-03-11T20:48:54Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Alvaro Bartolome, Dhruv Nair, Miguel Martin

## AI分析总结

### 1. 主要更新类型
- **功能新增**：添加了 `PRXPipeline` 到自动文本到图像管道映射中。
- **文档更新**：修复并更新了 NVIDIA Cosmos 的文档和示例。
- **功能增强**：为上下文并行（Context Parallel）添加了自定义设备网格（device mesh）支持。

### 2. 关键变更点及其与项目整体方向的关系
- **`PRXPipeline` 集成**：扩展了 `diffusers` 库支持的文本到图像生成管道类型，符合项目作为“最先进的扩散模型工具箱”的定位，旨在提供广泛、易用的预训练模型和管道。
- **NVIDIA Cosmos 文档更新**：优化了与硬件/云平台（如 NVIDIA）集成的文档，有助于提升用户体验和部署效率，支持项目在工业级应用中的易用性目标。
- **自定义设备网格支持**：增强了分布式训练（特别是上下文并行）的灵活性，允许用户根据硬件配置自定义设备拓扑，这符合项目对高性能和可扩展性的追求，特别是在大规模模型训练场景中。

### 3. 对项目的影响和潜在意义
- **生态扩展**：`PRXPipeline` 的加入丰富了文本到图像生成的选择，可能吸引更多开发者使用该库进行创意或研究应用。
- **用户体验提升**：更新的文档有助于降低用户在使用特定硬件（如 NVIDIA Cosmos）时的门槛，促进更广泛的采用。
- **性能优化潜力**：自定义设备网格支持为高级用户提供了更精细的分布式控制，可能提升训练效率，特别是在异构硬件环境中。

### 4. 值得关注的技术点
- **`AUTO_TEXT2IMAGE_PIPELINES_MAPPING`**：这是一个自动化映射机制，用于简化管道调用，体现了库的模块化和易用性设计。
- **上下文并行（Context Parallel）**：这是一种分布式训练策略，专注于处理长序列或大上下文模型，自定义设备网格支持增强了其适应性。
- **NVIDIA Cosmos 集成**：可能涉及硬件加速或云原生部署优化，反映了项目与业界硬件平台的深度协作。

### 5. 基于项目背景的提交影响分析
- **项目背景**：`diffusers` 旨在提供扩散模型的标准化、高性能实现，支持从研究到生产全流程。README 强调其易用性、模块化和社区驱动特性。
- **影响分析**：
  - **功能新增**（如 `PRXPipeline`）直接扩大了库的覆盖范围，支持更多模型架构，增强了其作为“工具箱”的全面性。
  - **文档更新** 降低了外部平台集成的使用障碍，符合项目“易于上手”的目标，可能促进企业级应用。
  - **自定义设备网格支持** 提升了分布式训练的灵活性，有助于处理更大模型或数据集，支持项目在高性能计算方向的发展，同时保持代码的模块化。

这些更新共同强化了 `diffusers` 在扩散模型领域的领先地位：既通过生态扩展吸引更广泛用户，又通过技术深化满足高级需求，平衡了易用性与性能。

## 详细提交记录

### [81c354d](https://github.com/huggingface/diffusers/commit/81c354d8796d7c30336f0628241b768df4e00476)

- **作者**: Alvaro Bartolome
- **时间**: 2026-03-11T17:39:24Z
- **提交信息**: Add `PRXPipeline` in `AUTO_TEXT2IMAGE_PIPELINES_MAPPING` (#13257)

### [0a2c26d](https://github.com/huggingface/diffusers/commit/0a2c26d0a4105bed9b4c046a9517c3374fe70a86)

- **作者**: Miguel Martin
- **时间**: 2026-03-11T16:14:56Z
- **提交信息**: Update Documentation for NVIDIA Cosmos (#13251)

* fix docs

* update main example

### [07c5ba8](https://github.com/huggingface/diffusers/commit/07c5ba8eee8e0059d41c481575d201489121d65a)

- **作者**: Dhruv Nair
- **时间**: 2026-03-11T11:12:11Z
- **提交信息**: [Context Parallel] Add support for custom device mesh (#13064)

* add custom mesh support

* update

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 378
- **最后更新**: 2026-03-02T11:35:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 11966
- **最后更新**: 2026-03-11T19:46:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24338
- **最后更新**: 2026-03-11T22:13:14Z

## 提交统计

- **昨日提交总数**: 21
- **提交者数量**: 20
- **主要提交者**: Matt Van Horn, Alison Shao, qy-seu

## AI分析总结

根据 `sgl-project/sglang` 仓库的提交记录和README摘要（SGLang是一个用于高效运行大型语言模型的框架/系统），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占主导，涉及内存管理、解码逻辑、CI/CD、依赖和文档链接等（如提交1, 3, 4, 5, 9, 10, 14, 18）。
- **功能新增**：包括对NPU（神经网络处理器）的深度支持、新API集成、网络抽象和健康检查逻辑（如提交2, 7, 16, 17, 19, 20, 21）。
- **性能优化/扩展**：针对特定硬件（NPU、H200）和模型（DeepSeek-V3）的优化与支持（如提交5, 9, 15, 16, 21）。
- **文档更新**：修正文档错误，补充硬件支持信息（如提交5, 12, 13, 14）。
- **依赖/工具更新**：升级依赖版本以解决兼容性问题（如提交8, 15）。

### 2. 关键变更点及其与项目整体方向的关系
- **硬件生态扩展**：多项提交强化了对**NPU**（如华为昇腾）和**国产硬件**（Moore Threads）的支持，包括量化、图像预处理和内核版本升级。这与SGLang作为高效LLM服务框架的目标一致，旨在**扩大硬件兼容性**，降低部署门槛。
- **系统稳定性与健壮性**：修复了内存不足（OOM）时的请求中止、解码无限循环、调度器跟踪等问题，提升了生产环境的**可靠性**。
- **分布式与并行能力**：新增对数据并行秩（`X-Data-Parallel-Rank`）的支持，并集成了**Elastic NIXL-EP**（推测为NVIDIA的弹性推理扩展），强化了**大规模分布式推理**能力。
- **模型与后端扩展**：增加了对`deepseek-v3`（128K长度）和`sglang-embedding`后端的支持，体现了对**前沿模型和多样化任务**的快速适配。

### 3. 对项目的影响和潜在意义
- **对用户**：更稳定的服务、更广泛的硬件选择（尤其利于国产化环境）、对新模型（如DeepSeek-V3.2、QwenVL）的更好支持。
- **对开发者**：CI/CD更稳定，提供了IPv6等网络抽象工具，降低了开发与集成的复杂度。
- **对生态**：通过支持更多硬件厂商（NVIDIA、华为、Moore Threads）和分布式方案，**增强了框架的行业渗透力和竞争力**。

### 4. 值得关注的技术点
- **NPU深度集成**：提交15、16、21显示了对NPU上W4A4 MoE量化、图像预处理等**高性能推理**的持续投入。
- **弹性推理集成**：提交17的“Elastic NIXL-EP”可能代表与NVIDIA生态的深度整合，用于**动态资源调度**。
- **内存与解码优化**：提交1、3、10针对大模型服务中常见的**内存管理和解码错误恢复**场景进行了修复。
- **网络抽象**：提交20引入`NetworkAddress`，为**IPv6和复杂网络环境**提供了更好的支持。

### 5. 基于项目背景的提交影响分析
SGLang旨在成为**高效、可扩展的LLM服务引擎**。昨日的更新紧密围绕这一目标：
- **性能与效率**：通过NPU优化、量化支持和解码修复，直接提升了**推理性能和资源利用率**。
- **可扩展性与兼容性**：新增的硬件支持、分布式头部和网络抽象，使框架能适应**从云到边缘的多种部署场景**。
- **开发者体验与稳定性**：修复CI、文档和关键Bug，降低了使用门槛，增强了**生产环境信心**。
- **生态构建**：通过支持更多硬件和模型，**吸引更广泛的社区和厂商合作**，巩固其作为开源LLM服务框架的地位。

**总结**：本次更新以**增强系统鲁棒性、扩展硬件生态、优化前沿模型支持**为核心，体现了SGLang在保持高性能的同时，积极向多硬件平台、大规模分布式场景演进的战略方向。

## 详细提交记录

### [acab24a](https://github.com/sgl-project/sglang/commit/acab24a76a109e7c39026c3826003a386f14b656)

- **作者**: shuwenn
- **时间**: 2026-03-11T22:13:03Z
- **提交信息**: fix: gracefully abort last request in retract_decode on OOM (#19881)

### [88d2fc1](https://github.com/sgl-project/sglang/commit/88d2fc19b137919dddc9a3fe3d1d0ab15e38e656)

- **作者**: doujiang24
- **时间**: 2026-03-11T21:53:33Z
- **提交信息**: feature: support X-Data-Parallel-Rank header to specific dp-rank. (#19832)

Signed-off-by: doujiang24 <doujiang24@gmail.com>

### [af4c289](https://github.com/sgl-project/sglang/commit/af4c28904d3ad03f3586450eac04c7a8fe55a6c6)

- **作者**: Shangming Cai
- **时间**: 2026-03-11T21:11:19Z
- **提交信息**: [PD] Fix the infinite loop in deocde resolve_pending_reqs (#20371)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [ab4b863](https://github.com/sgl-project/sglang/commit/ab4b863546438fe3831f9aa76a7b9d42768ba16a)

- **作者**: Rain Jiang
- **时间**: 2026-03-11T20:37:33Z
- **提交信息**: fix ci by removing nvidia-cutlass-dsl-libs-base and force reinstall n… (#20380)

### [2720ea2](https://github.com/sgl-project/sglang/commit/2720ea2667dc8ae2129730326491f3c6e7364cdd)

- **作者**: Mook
- **时间**: 2026-03-11T20:35:20Z
- **提交信息**: [Typo] Fix H200 doc links pointing to H20 section in deepseek_v3.md (#20383)

### [252ef90](https://github.com/sgl-project/sglang/commit/252ef90fc2ea8dad02ef571279313e3753a3d06a)

- **作者**: haNa-meister
- **时间**: 2026-03-11T20:15:50Z
- **提交信息**: [Generative Score API] Fix on prefill-only scheduler running batch loss track problem (#14320)

Co-authored-by: Wenyan Yao <wenyao@linkedin.com>
Co-authored-by: Sundara Raman Ramachandran <sundar24295@gmail.com>

### [a54d71e](https://github.com/sgl-project/sglang/commit/a54d71e967e27291c1d38eb6b5d866095ef0d27c)

- **作者**: satyamk7054
- **时间**: 2026-03-11T20:13:16Z
- **提交信息**: [Benchmark] Add sglang-embedding backend to bench_serving (#20017)

Co-authored-by: Satyam Kumar <satyamk@linkedin.com>

### [61b2282](https://github.com/sgl-project/sglang/commit/61b228239e48578a32779502d0340ef8a2a96ee4)

- **作者**: Rain Jiang
- **时间**: 2026-03-11T20:08:09Z
- **提交信息**: bump sgl-fa4 version to 4.0.5 to loose torch deps (#20378)

### [006bd44](https://github.com/sgl-project/sglang/commit/006bd44cf92064bdd32a96f150a1aa77c2eb7cde)

- **作者**: BingjiaWang
- **时间**: 2026-03-11T19:56:33Z
- **提交信息**: [deepseekv3.2] fix get_k_and_s_triton kenel for 128K seqlen case bug (#19319)

Co-authored-by: abing <wangbingjia.wbj@alibaba-inc.com>

### [e6a6cd1](https://github.com/sgl-project/sglang/commit/e6a6cd1f0ce4c208e43e89db74c24d79bf1cdf7c)

- **作者**: Kazami Michiru
- **时间**: 2026-03-11T19:42:21Z
- **提交信息**: [Fix] Reset `output_ids` for requests with `input_embeds` during retraction (#14110)

### [7b44bc9](https://github.com/sgl-project/sglang/commit/7b44bc923e9afd3cb0ed3727a4f2520924853b7f)

- **作者**: Alison Shao
- **时间**: 2026-03-11T19:35:21Z
- **提交信息**: Relax flaky B200 GSM8K accuracy thresholds (#20304)

Co-authored-by: Alison Shao <alisonshao@Mac.attlocal.net>

### [d093e70](https://github.com/sgl-project/sglang/commit/d093e700672defeb9bfedce9c084b3ee00a3d326)

- **作者**: Matt Van Horn
- **时间**: 2026-03-11T17:40:35Z
- **提交信息**: [Doc] Add DSA/NSA attention backend to support matrix (#20326)

Co-authored-by: Matt Van Horn <455140+mvanhorn@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [dae5c6c](https://github.com/sgl-project/sglang/commit/dae5c6cadf5dc4e5c97c0e36f0c4574219f27765)

- **作者**: R0CKSTAR
- **时间**: 2026-03-11T17:15:15Z
- **提交信息**: [diffusion] doc: add Moore Threads as a supported vendor (#20146)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [05e4092](https://github.com/sgl-project/sglang/commit/05e40922b31ecd9b1eafba44aa7fcfd6b4ed7d91)

- **作者**: Thomas
- **时间**: 2026-03-11T15:30:45Z
- **提交信息**: [Doc] Fix wrong link and cmd description (#20365)

### [6cfc21b](https://github.com/sgl-project/sglang/commit/6cfc21ba74f2aff58a2f8f9410758a6054d929d0)

- **作者**: Even Zhou
- **时间**: 2026-03-11T14:28:21Z
- **提交信息**: [NPU] Bump SGL-Kernel-NPU version to 2026.03.10.rc1 (#20362)

### [ed42af9](https://github.com/sgl-project/sglang/commit/ed42af99a92fa6f69c5de7f05d023b5a673ddf6b)

- **作者**: Артем Савкин
- **时间**: 2026-03-11T13:52:35Z
- **提交信息**: [NPU] [Quantization] w4a4 MoE layer support (#18924)

### [9991deb](https://github.com/sgl-project/sglang/commit/9991debde37b0ea1ecca8e13f0aef24c6b498d17)

- **作者**: Yoray Zack
- **时间**: 2026-03-11T09:37:43Z
- **提交信息**: [Feature] Integrate Elastic NIXL-EP into SGLang (#19248)

Signed-off-by: Barak Biber <bbiber@nvidia.com>
Signed-off-by: Yoray Zack <yorayz@nvidia.com>
Signed-off-by: Itay Alroy <ialroy@nvidia.com>
Co-authored-by: Barak Biber <bbiber@nvidia.com>

### [680d9d9](https://github.com/sgl-project/sglang/commit/680d9d98e4683bfe3b63d25ae78dc0a7139f548c)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-11T08:17:35Z
- **提交信息**: Fix cutedsl ci error (#20309)

Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [456934f](https://github.com/sgl-project/sglang/commit/456934fed59eb828e06c116f88c73fc09060d002)

- **作者**: qy-seu
- **时间**: 2026-03-11T07:23:22Z
- **提交信息**: feat: fix update last_receive_tstamp logic for health-check in multi-token-worker mode (#20256)

### [61cad15](https://github.com/sgl-project/sglang/commit/61cad15d28874fb6cdfc544a29673e3ee64ed176)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-11T07:07:37Z
- **提交信息**: [Utils] Add `NetworkAddress` abstraction for IPv6-safe address handling (#20306)

### [55e6acf](https://github.com/sgl-project/sglang/commit/55e6acf8347873f41e0ca90401170592a3ef2e57)

- **作者**: Kurkur
- **时间**: 2026-03-11T07:03:08Z
- **提交信息**: [NPU][QwenVL] Support qwen image preprocess on npu (#20189)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1081
- **最后更新**: 2026-03-11T17:08:20Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据 `vipshop/cache-dit` 仓库的 README 摘要（一个专注于为 DiTs 提供混合缓存加速和大规模并行化的 PyTorch 原生推理引擎）以及昨日的提交记录，以下是分析总结：

### 1. 主要更新类型
- **版本发布与维护**：核心是发布新版本 `v1.3.0`（提交 #864、#865）。
- **Bug修复**：修复了注意力调度环境变量拼写错误（提交 #866）。
- **文档更新**：更新了服务相关文档（提交 #863）。

### 2. 关键变更点及其与项目整体方向的关系
- **版本升级至 v1.3.0**：表明项目处于活跃迭代阶段，可能引入了新功能、性能改进或重要修复，与项目“持续优化推理性能与稳定性”的方向一致。
- **修复环境变量拼写错误**：涉及注意力（`attn`）调度机制，这是 DiT 模型推理的关键组件，修复确保了缓存加速和并行化功能的正确配置。
- **更新服务文档**：完善了部署和使用指南，有助于提升用户体验和项目易用性，符合开源项目推广的需求。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：环境变量修复避免了因配置错误导致的运行时问题，增强了系统可靠性。
- **版本迭代信号**：`v1.3.0` 发布可能包含未在提交记录中明示的底层优化（如缓存策略或并行处理改进），有望提升推理效率。
- **文档完善**：降低了用户部署门槛，可能吸引更多开发者采用，促进社区生态发展。

### 4. 值得关注的技术点
- **注意力调度机制**：环境变量修复（`attn dispatch`）暗示项目可能支持可配置的注意力计算后端（如 FlashAttention、内存高效注意力），这是优化大规模 DiT 推理性能的关键。
- **版本管理**：连续提交多个版本升级（#864、#865）可能涉及自动化发布流程或版本号同步问题，反映项目维护的规范性。

### 5. 基于项目背景的提交影响分析
- **加速推理核心目标**：环境变量修复直接关联混合缓存与并行化执行路径，确保性能优化功能按预期工作。
- **开源生态建设**：文档更新和服务指南完善，有助于扩大项目在生成式 AI（DiT 常用于图像生成）领域的应用场景。
- **版本迭代节奏**：频繁版本发布显示项目正快速响应需求或修复问题，有利于保持技术竞争力。

---

**总结**：昨日更新以版本发布和细节修复为主，虽无重大功能新增，但通过维护性工作巩固了项目的稳定性与可用性，间接支持了其作为高性能 DiT 推理引擎的核心使命。

## 详细提交记录

### [1a9f717](https://github.com/vipshop/cache-dit/commit/1a9f717836b25635f3ad050799c0af5964f6143a)

- **作者**: DefTruth
- **时间**: 2026-03-11T09:54:46Z
- **提交信息**: chore: fix attn dispatch env typo (#866)

### [6c8549b](https://github.com/vipshop/cache-dit/commit/6c8549b12a6faedc3b1e5b1c69e3c2c070d86a25)

- **作者**: DefTruth
- **时间**: 2026-03-11T09:39:44Z
- **提交信息**: chore: Bump up cache-dit to v1.3.0 (#865)

### [e735049](https://github.com/vipshop/cache-dit/commit/e735049728649f158548acef80f78284c9404880)

- **作者**: DefTruth
- **时间**: 2026-03-11T09:17:09Z
- **提交信息**: chore: Bump up cache-dit to v1.3.0 (#864)

* chore: Bump up cache-dit to v1.3.0

* chore: Bump up cache-dit to v1.3.0

* chore: Bump up cache-dit to v1.3.0

### [2c4842e](https://github.com/vipshop/cache-dit/commit/2c4842e2897eef5bbc323c56329cf1d1c5e351f2)

- **作者**: DefTruth
- **时间**: 2026-03-11T08:52:55Z
- **提交信息**: chore: update serving docs (#863)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 72857
- **最后更新**: 2026-03-11T22:33:34Z

## 提交统计

- **昨日提交总数**: 54
- **提交者数量**: 39
- **主要提交者**: Itay Alroy, Ethan T., Yanan Cao

## AI分析总结

根据您提供的 vLLM 仓库昨日提交记录，结合其“为所有人提供简单、快速、经济的 LLM 服务”的项目目标，以下是分析总结：

### 1. 主要更新类型
昨日提交以 **Bug修复** 和 **功能新增/增强** 为主，辅以性能优化、重构和少量文档更新，体现了项目在快速迭代中持续提升稳定性和扩展能力。
*   **Bug修复 (约14项)**：覆盖了测试、内核、模型支持、缓存、调度等多个核心模块。
*   **功能新增/增强 (约12项)**：主要集中在支持新模型（特别是MLA架构）、扩展硬件支持（XPU、ROCm）、以及Model Runner V2等新特性。
*   **性能优化 (约5项)**：涉及内核编译、缓存、内存分配等方面。
*   **重构与代码清理 (约5项)**：移除死代码，优化API和内部结构。
*   **其他**：包括CI/CD、文档、配置更新等。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向（易用、快速、经济、普适）的关系 |
| :--- | :--- |
| **支持新模型与架构**（如Mistral Large 3 Eagle, Qwen3.5 Eagle3, Kimi K2.5, DeepSeek v3.2, Whisper, Bagel等） | **扩大生态与普适性**：持续集成热门及前沿模型，是保持项目竞争力和吸引用户的关键。 |
| **硬件与内核优化**（ROCm CDNA4调优、XPU MLA支持、Triton回退修复、FakeTensor应用） | **提升速度与经济性**：通过深度优化AMD、Intel等硬件支持，降低使用门槛和成本，践行“为所有人”的目标。 |
| **Model Runner V2 推进**（添加Whisper状态、概率拒绝采样） | **架构演进与性能**：下一代推理引擎的持续开发，旨在为未来提供更优的性能和灵活性。 |
| **MLA (Multi-Latent Attention) 相关增强**（维度支持、稀疏后端、性能优化） | **拥抱高效架构**：积极支持MLA这类高效注意力变体，有助于在相同硬件上服务更大模型或获得更高吞吐。 |
| **Bug修复覆盖广泛**（异步调度、KV卸载、缓存、长上下文、模型格式等） | **提升稳定性与易用性**：修复影响服务稳定性和用户体验的深层次问题，是生产就绪性的基础。 |

### 3. 对项目的影响和潜在意义
*   **用户体验**：大量Bug修复直接提升服务稳定性；对新模型和硬件的支持让用户有更多选择。
*   **开发者体验**：重构、死代码清理和编译优化（如`torch.compile`支持）使代码库更健壮，便于贡献和维护。
*   **性能与成本**：针对特定硬件（AMD, Intel）的内核优化和MLA支持，有望在非NVIDIA生态上获得更好性价比。
*   **技术债务**：积极移除废弃代码（如Molmo2包装器、未使用的方法），有助于项目轻量化。

### 4. 值得关注的技术点
1.  **FakeTensorMode的应用**（#36563, #36093）：在配置计算和编译时避免实际GPU内存分配，**显著降低开发/编译阶段的资源消耗和启动时间**。
2.  **MLA生态的蓬勃发展**：多个提交涉及MLA对不同模型（Mistral, Qwen, Kimi, DeepSeek）和硬件（XPU）的支持，显示其已成为**高效推理的重要技术路线**。
3.  **概率拒绝采样用于推测解码**（#35461）：在Model Runner V2中引入，可能提升**推测解码的准确性和效率**，是推理加速的前沿方向。
4.  **异构混合模型支持**（#35744）：修复Mamba+Attention混合模型的路由专家捕获问题，显示对**复杂模型架构**的适配能力。

### 5. 基于项目背景的提交影响分析
vLLM的核心是**降低高性能LLM服务的门槛**。昨日的提交集体指向这一目标的多个维度：
*   **“易用”**：通过修复模型格式（#36782）、推理参数（#36789）、LoRA（#36402）等各类Bug，减少用户踩坑。通过推断本地检查点数据类型（#36218）提升易用性。
*   **“快速”**：通过内核级优化（ROCm, XPU）、MLA支持、编译优化（#36551, #36093）和下一代引擎（Model Runner V2）开发，持续追求极致的推理速度。
*   **“经济”**：加强对AMD ROCm和Intel XPU的优化，为用户提供了**更具成本效益的GPU替代方案**，直接降低了硬件投入成本。
*   **“为所有人”**：支持更广泛的模型（从Gemma到国产模型）、更多硬件架构、以及修复各种边缘情况，都在**扩大其潜在用户和适用场景**，使技术红利惠及更广泛的开发者群体。

**总结**：昨日的更新是vLLM项目在“快速”和“普适”两个核心方向上的一次典型迭代。它不仅在巩固现有功能的稳定性，更在积极拓展对新硬件（AMD/Intel）和新模型架构（MLA系列）的支持边界，这完全符合其打破算力垄断、让LLM服务更普及的长期愿景。同时，对Model Runner V2和编译优化等底层技术的投入，为其未来的性能突破奠定基础

## 详细提交记录

### [d6b61e5](https://github.com/vllm-project/vllm/commit/d6b61e5166ac3eec7f828d0a102c30a76f6aecf3)

- **作者**: Aaron Hao
- **时间**: 2026-03-11T22:06:10Z
- **提交信息**: [BUG] Fix async rlhf tests (#35811)

Signed-off-by: ahao-anyscale <ahao@anyscale.com>

### [cf63249](https://github.com/vllm-project/vllm/commit/cf632499ee31e50f421fe21127876688290c6496)

- **作者**: Yanan Cao
- **时间**: 2026-03-11T21:25:29Z
- **提交信息**: [Kernel] [Helion] [15/N] Split config files into per-platform files (#36698)

Signed-off-by: Yanan Cao <gmagogsfm@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [a3774a8](https://github.com/vllm-project/vllm/commit/a3774a819897ff60ab12a7622f587452f6208680)

- **作者**: Yanan Cao
- **时间**: 2026-03-11T21:25:16Z
- **提交信息**: [Kernel] [Helion] [12/N] Use FakeTensorMode to avoid GPU allocation during config key computation (#36563)

Signed-off-by: Yanan Cao <gmagogsfm@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [0ce21c4](https://github.com/vllm-project/vllm/commit/0ce21c46a055c4dc89d58b38f3ff62759011801b)

- **作者**: Yanan Cao
- **时间**: 2026-03-11T21:25:04Z
- **提交信息**: [Kernel] [Helion] [14/N] Set autotune_ignore_errors=True during autotuning (#36683)

Signed-off-by: Yanan Cao <gmagogsfm@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [55eed6b](https://github.com/vllm-project/vllm/commit/55eed6b7a52463e0eecb5adc45710c61f546b1ec)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-11T21:20:38Z
- **提交信息**: [Model Runner V2] Add WhisperModelState [6/N] (#35790)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [c77181e](https://github.com/vllm-project/vllm/commit/c77181e534597f7347fc03b7d26600fb3cea9981)

- **作者**: Giancarlo Delfin
- **时间**: 2026-03-11T21:04:32Z
- **提交信息**: [Model Runner V2] Add probabilistic rejection sampling for spec decoding (#35461)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [12001f2](https://github.com/vllm-project/vllm/commit/12001f2ebc606b471476d47edc22a79af6aca66c)

- **作者**: maobaolong
- **时间**: 2026-03-11T20:45:20Z
- **提交信息**: [LMCache] Pass TP size in lookup for MLA multi-reader locking (#36129)

Signed-off-by: baoloongmao <baoloongmao@tencent.com>
Co-authored-by: Yihua Cheng <yihua98@uchicago.edu>

### [7ee5d50](https://github.com/vllm-project/vllm/commit/7ee5d5093b369d5c55199bc4613c9afdecabe0b7)

- **作者**: Or Ozeri
- **时间**: 2026-03-11T20:43:40Z
- **提交信息**: [BugFix][kv_offload] Fix offloading decodes with async scheduling (#33881)

Signed-off-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [428bc71](https://github.com/vllm-project/vllm/commit/428bc718bd4a736c1bc129a23c51963c4f0b71b9)

- **作者**: jennyyyyzhen
- **时间**: 2026-03-11T20:37:31Z
- **提交信息**: [Bugfix][ROCm] Strip block_size before attention backend validation (#36274)

Signed-off-by: jennyyyyzhen <yzhen@hmc.edu>
Co-authored-by: Lu Fang <30275821+houseroad@users.noreply.github.com>

### [ff1e3d9](https://github.com/vllm-project/vllm/commit/ff1e3d9c6386cb1e643d298ddf357a23f741d011)

- **作者**: 汪志鹏
- **时间**: 2026-03-11T19:55:59Z
- **提交信息**: [BugFix]: add bagel to MM_PREFIX_LM_MODELS (#36316)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [35bdca5](https://github.com/vllm-project/vllm/commit/35bdca5431e652b4c00267489a632c1bf5522103)

- **作者**: Wentao Ye
- **时间**: 2026-03-11T19:40:17Z
- **提交信息**: [Refactor] Remove dead code in KV connector (#36424)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [8a24842](https://github.com/vllm-project/vllm/commit/8a24842765ba9b45b0116d65b16c2d5b1fcb7e05)

- **作者**: Amanzhol Salykov
- **时间**: 2026-03-11T19:00:08Z
- **提交信息**: [ROCm] add tuned moe_wna16_triton kernel configs for CDNA4 (#35093)

Signed-off-by: salykova <amsalykov@gmail.com>
Signed-off-by: amd-asalykov <asalykov@amd.com>

### [65986db](https://github.com/vllm-project/vllm/commit/65986db6ba71abf4cf0639c5fd1477b0d8df8f5e)

- **作者**: Harry Mellor
- **时间**: 2026-03-11T18:12:43Z
- **提交信息**: Make Gemma and Gemma 2 accept `inputs_embeds` like Gemma 3 (#36787)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [9556af8](https://github.com/vllm-project/vllm/commit/9556af87d5d5a38128db0d09eeb7f2fe16f16589)

- **作者**: Luka Govedič
- **时间**: 2026-03-11T17:56:55Z
- **提交信息**: [torch.compile] Add support for non-contiguous fused RMSNorm + group quant (#36551)

Signed-off-by: Luka Govedič <lgovedic@redhat.com>
Signed-off-by: Luka Govedič <ProExpertProg@users.noreply.github.com>
Co-authored-by: Copilot <198982749+Copilot@users.noreply.github.com>
Co-authored-by: ProExpertProg <11367180+ProExpertProg@users.noreply.github.com>

### [a1a3523](https://github.com/vllm-project/vllm/commit/a1a3523a5647a58e00096ca7430e9f1ad4a50a97)

- **作者**: Or Ozeri
- **时间**: 2026-03-11T17:36:37Z
- **提交信息**: [KVConnector] Support worker -> scheduler metadata (#31964)

Signed-off-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [741f4e0](https://github.com/vllm-project/vllm/commit/741f4e046bb7e5c5a6093d9fc294865ad7a8e721)

- **作者**: tianshu-Michael-yu
- **时间**: 2026-03-11T17:28:38Z
- **提交信息**: fix: align lfm2 thumbnail token counting with HF (#36707)

### [a5d06dc](https://github.com/vllm-project/vllm/commit/a5d06dc557f9b04685e10793d3182358a47f7ba6)

- **作者**: Julien Denize
- **时间**: 2026-03-11T17:21:22Z
- **提交信息**: Add 320 dimension size support to MLA (#36161)

Signed-off-by: Julien Denize <julien.denize@mistral.ai>

### [5efa206](https://github.com/vllm-project/vllm/commit/5efa206a8cc5501563a79f667a5ae2f87dba2108)

- **作者**: Harry Mellor
- **时间**: 2026-03-11T17:10:23Z
- **提交信息**: Fix `ExaoneMoeMTP` test that never ran in Transformers v4 (#36792)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [196802d](https://github.com/vllm-project/vllm/commit/196802dfa68c512b5360546003b2a35259de66da)

- **作者**: Cyrus Leung
- **时间**: 2026-03-11T16:39:29Z
- **提交信息**: [Misc] Clean up renderers (#36770)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [c84b519](https://github.com/vllm-project/vllm/commit/c84b519cf314ad6568f0db6f762d82f356038309)

- **作者**: Isotr0py
- **时间**: 2026-03-11T16:30:51Z
- **提交信息**: [Bugfix] Fix negative max_tokens when input prompt is too long (#36789)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [741ecf0](https://github.com/vllm-project/vllm/commit/741ecf06304097454e4e11a4714918a0ac55e17d)

- **作者**: Flora Feng
- **时间**: 2026-03-11T16:27:36Z
- **提交信息**: [CI] Add bfcl tool call correctness eval (#36560)

Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [b7e5a58](https://github.com/vllm-project/vllm/commit/b7e5a588d89003223bebc9b163413529f3db4cae)

- **作者**: Robert Shaw
- **时间**: 2026-03-11T16:07:14Z
- **提交信息**: [Bugfix] Fix DP/EP Shared Expert With Monolithic Kernels (#36061)

Signed-off-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>

### [822e250](https://github.com/vllm-project/vllm/commit/822e250ab74899af4bc28aa5d738ec4c0e8c646e)

- **作者**: Richard Zou
- **时间**: 2026-03-11T16:07:09Z
- **提交信息**: [torch.compile] Use FakeTensors instead of real GPU tensors for single-size compilation (#36093)

Signed-off-by: Richard Zou <zou3519@gmail.com>

### [bea02cd](https://github.com/vllm-project/vllm/commit/bea02cdf93bcf9fe94a0efb3240f22facd5e1ac2)

- **作者**: Hongxin Xu
- **时间**: 2026-03-11T15:53:10Z
- **提交信息**: Fix routed experts capture for hybrid models (Mamba + Attention) (#35744)

Signed-off-by: arlenxu <arlenxu@tencent.com>
Signed-off-by: xhx1022 <1737006628@qq.com>
Co-authored-by: arlenxu <arlenxu@tencent.com>

### [a3ea760](https://github.com/vllm-project/vllm/commit/a3ea760ea59a8253058c80240a9f0f2aa1fbc3c0)

- **作者**: Julien Denize
- **时间**: 2026-03-11T15:45:34Z
- **提交信息**: Add 'none' reasoning effort to ChatCompletionRequest (#36238)

Signed-off-by: Julien Denize <julien.denize@mistral.ai>

### [35db669](https://github.com/vllm-project/vllm/commit/35db669f1def3fb56f1585f00cac40c199623822)

- **作者**: Harry Mellor
- **时间**: 2026-03-11T15:43:28Z
- **提交信息**: Correct link to supported hardware on vllm.ai (#36798)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [afebeff](https://github.com/vllm-project/vllm/commit/afebeffbfbf2dd61bad940ce13942af8a8931524)

- **作者**: Julien Denize
- **时间**: 2026-03-11T15:42:56Z
- **提交信息**: Add support to Mistral large 3 eagle with dense layers (#36163)

Signed-off-by: juliendenize <julien.denize@mistral.ai>
Signed-off-by: Julien Denize <40604584+juliendenize@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [5573894](https://github.com/vllm-project/vllm/commit/557389473755bff50b6d00c03ca5c68e5c37c9a0)

- **作者**: Jhao-Ting Chen
- **时间**: 2026-03-11T15:36:11Z
- **提交信息**: Kimi k2.5 MLA based eagle3 (#36361)

Signed-off-by: Izzy Putterman <iputterman@nvidia.com>
Signed-off-by: Jhao-Ting Chen <jhaotingc@nvidia.com>
Co-authored-by: Izzy Putterman <iputterman@nvidia.com>

### [d5816c8](https://github.com/vllm-project/vllm/commit/d5816c8c2fa8dba84dc518c481a21bc6e5439acb)

- **作者**: Harry Mellor
- **时间**: 2026-03-11T15:10:26Z
- **提交信息**: Fix tied weights in weight mapping test for Transformers v5 (#36788)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [8ccbcda](https://github.com/vllm-project/vllm/commit/8ccbcda5c0d460b0189f274bfbfe4947b45bd5cb)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-11T15:02:44Z
- **提交信息**: [Model Runner V2] Remove unused warmup_for_prefill method (#36762)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [a9e532a](https://github.com/vllm-project/vllm/commit/a9e532afe2a1ae65c917ae977bf9090806e14721)

- **作者**: tvirolai-amd
- **时间**: 2026-03-11T14:43:03Z
- **提交信息**: [ROCm][Perf] Allow MTP lens > 1 in Sparse MLA (#36681)

Signed-off-by: Teemu Virolainen <teemu.virolainen@amd.com>

### [f3163bb](https://github.com/vllm-project/vllm/commit/f3163bba6729b7bfd1e355f8b7f6670a6beb4715)

- **作者**: Harry Mellor
- **时间**: 2026-03-11T13:53:23Z
- **提交信息**: Disable docs build skipping until a better solution is found (#36790)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [700a1dd](https://github.com/vllm-project/vllm/commit/700a1ddc65dfbf3590ff746013cd4070fb41c01d)

- **作者**: Martin Hickey
- **时间**: 2026-03-11T13:37:46Z
- **提交信息**: [Misc] Use envs module to get VLLM_DISABLED_KERNELS (#35776)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [f33251f](https://github.com/vllm-project/vllm/commit/f33251ffc851405a36a95560975ea6963d8a2706)

- **作者**: Silvia Colabrese
- **时间**: 2026-03-11T11:47:52Z
- **提交信息**: [Bugfix] Fix Mistral-small `--format` (#36782)

Signed-off-by: 12010486 <silvia.colabrese@intel.com>

### [e584dce](https://github.com/vllm-project/vllm/commit/e584dce52b9584ffb0fc4a1a4cd31163d4257a41)

- **作者**: Wuxun Zhang
- **时间**: 2026-03-11T11:19:15Z
- **提交信息**: Add XPU MLA Sparse backend for DeepSeek v3.2 (#33230)

Signed-off-by: Zhang, Wuxun <wuxun.zhang@intel.com>

### [40c0461](https://github.com/vllm-project/vllm/commit/40c0461f24b27df3c86918d30826d2a412c40e5f)

- **作者**: Ning Xie
- **时间**: 2026-03-11T10:14:34Z
- **提交信息**: [openapi] refactor render related openapi [3/N] (#36749)

Signed-off-by: Andy Xie <andy.xning@gmail.com>

### [7247596](https://github.com/vllm-project/vllm/commit/724759684cd97a7a8625513c9a61bf95eaa396f1)

- **作者**: Weiguang Li
- **时间**: 2026-03-11T10:13:06Z
- **提交信息**: [Bugfix] Fix Qwen3-VL timestamp mismatch when using num_frames without fps (#36136)

Signed-off-by: OiPunk <codingpunk@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [9c34e9d](https://github.com/vllm-project/vllm/commit/9c34e9d24fcd72834daf8b54f52667e3fa009d5f)

- **作者**: Michael Goin
- **时间**: 2026-03-11T10:12:23Z
- **提交信息**: Disable cascade attention by default (#36318)

### [09b6f99](https://github.com/vllm-project/vllm/commit/09b6f9985225109fbe2c30bc3956501433128aa4)

- **作者**: Richard Zou
- **时间**: 2026-03-11T10:12:03Z
- **提交信息**: [compile] aot_compile should respect VLLM_DISABLE_COMPILE_CACHE (#36358)

Signed-off-by: Richard Zou <zou3519@gmail.com>

### [c87fb51](https://github.com/vllm-project/vllm/commit/c87fb515edb180bd66168484e9cae86f384f6215)

- **作者**: Ethan T.
- **时间**: 2026-03-11T10:11:27Z
- **提交信息**: fix(lora): use replaced_module_name in pooling model name check (#36402)

Signed-off-by: gambletan <ethanchang32@gmail.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [5353c9b](https://github.com/vllm-project/vllm/commit/5353c9b0160586cee8413bfcbc1a11ef1076df47)

- **作者**: Itay Alroy
- **时间**: 2026-03-11T10:08:55Z
- **提交信息**: platforms: Fix Ray DP startup crash (#36665)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>

### [13e79fc](https://github.com/vllm-project/vllm/commit/13e79fc8111b9eb3a2a5a367ea08f5d7fbf57281)

- **作者**: Angela Yi
- **时间**: 2026-03-11T10:08:16Z
- **提交信息**: [ci] Update rtol for test_classification (#36556)

Signed-off-by: angelayi <yiangela7@gmail.com>
Co-authored-by: Richard Zou <zou3519@users.noreply.github.com>

### [9d07a3d](https://github.com/vllm-project/vllm/commit/9d07a3d6e472c8e5a231a34ec9c38084605b037d)

- **作者**: Rahul Tuli
- **时间**: 2026-03-11T10:07:42Z
- **提交信息**: Add: Eagle3 support for Qwen3.5 (#36658)

Signed-off-by: Rahul-Tuli <rtuli@redhat.com>

### [646b855](https://github.com/vllm-project/vllm/commit/646b85544b05a18b3cb652debd3f1d078948a781)

- **作者**: Cyrus Leung
- **时间**: 2026-03-11T10:07:20Z
- **提交信息**: [Refactor] Remove Molmo2 processor wrapper (#36667)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [4286cc5](https://github.com/vllm-project/vllm/commit/4286cc5ec24cf7a6d7c1a47e89dba914881be89a)

- **作者**: tc-mb
- **时间**: 2026-03-11T10:06:28Z
- **提交信息**: fix(minicpmv): fix audio inference by handling meta device in init_re… (#36751)

Signed-off-by: caitianchi <caitianchi@modelbest.cn>

### [545d18d](https://github.com/vllm-project/vllm/commit/545d18d81bf11761e51c2b11a006573c2ae366c1)

- **作者**: LoganJane
- **时间**: 2026-03-11T09:48:05Z
- **提交信息**: [Bugfix] Support other quantization methods in glm41v (#36321)

Signed-off-by: g00887675/loganJane <g00887675/loganJane73@hotmail.com>
Co-authored-by: g00887675/loganJane <g00887675/loganJane73@hotmail.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [e661b9e](https://github.com/vllm-project/vllm/commit/e661b9ee83d9d3c6c84c4e1acbe7e0280832e7c4)

- **作者**: roikoren755
- **时间**: 2026-03-11T09:44:41Z
- **提交信息**: [NemotronH] Small fix reasoning parser (#36635)

Signed-off-by: Roi Koren <roik@nvidia.com>

### [c910eeb](https://github.com/vllm-project/vllm/commit/c910eeb125003ebe19e0f4e6d27d335061597e81)

- **作者**: YiSheng5
- **时间**: 2026-03-11T09:17:46Z
- **提交信息**: [XPU]Bug fix for some unexpected error when use AgRs backend on XPU device. (#36593)

Signed-off-by: yisheng <yi.sheng@intel.com>

### [f4ae58b](https://github.com/vllm-project/vllm/commit/f4ae58b38b8ab1d36707344518d699e9019201cc)

- **作者**: Harry Mellor
- **时间**: 2026-03-11T08:51:19Z
- **提交信息**: Remove unused config field from Gemma2 (#36672)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [e568cf8](https://github.com/vllm-project/vllm/commit/e568cf88bc65531a95403110b186cd54dbfdc0e6)

- **作者**: Isotr0py
- **时间**: 2026-03-11T08:50:04Z
- **提交信息**: [UX] Infer dtype for local checkpoint (#36218)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [098d844](https://github.com/vllm-project/vllm/commit/098d844731c535c40c30498181de8f11f4b92cbb)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-03-11T08:11:23Z
- **提交信息**: [NIXL][1/N] Refactor `kernel_block_size` detection (#35752)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [a40ee48](https://github.com/vllm-project/vllm/commit/a40ee486f273eaaa885dafd0526f42f3a5b960c9)

- **作者**: JartX
- **时间**: 2026-03-11T07:45:57Z
- **提交信息**: [Bugfix] Add Multiple of 16 block_size to triton fallback on rocm Attention to support qwen3_5 (#35923)

Signed-off-by: JartX <sagformas@epdcenter.es>
Co-authored-by: akaratza <akaratza@amd.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [eac2dc2](https://github.com/vllm-project/vllm/commit/eac2dc2b410dc11af4b424802e86ef9d36bac28a)

- **作者**: pschlan-amd
- **时间**: 2026-03-11T07:25:00Z
- **提交信息**: AITER MLA backend: Avoid CPU sync in _build_decode (#35765)

Signed-off-by: Patrick Schlangen <pschlan@amd.com>

### [d5080ae](https://github.com/vllm-project/vllm/commit/d5080aeaa4d80f285d436ef66159fb2de4ffd3f7)

- **作者**: Flora Feng
- **时间**: 2026-03-11T07:11:41Z
- **提交信息**: [Refactor] Remove deadcode in Responses API serving (#36726)

Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: Signed-off-by: yewentao256 <zhyanwentao@126.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-12
**监控日期**: 2026-03-11
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 3097
- **最后更新**: 2026-03-11T19:00:36Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 6
- **主要提交者**: Didan Deng, Yueqian Lin, Samit

## AI分析总结

根据 `vllm-omni` 仓库的 README 摘要（“Easy, fast, and cheap omni-modality model serving for everyone”）可知，该项目旨在为多模态（omni-modality）模型提供高效、易用且经济的推理服务框架。昨日的提交记录围绕这一核心目标，在多模态模型支持、测试验证、前端集成和问题修复等方面进行了更新。

以下是具体分析总结：

### 1. 主要更新类型
- **Bug修复**：4项（#1812, #1645, #1771, #1808）
- **测试与验证**：3项（#1812, #1700, #1682）
- **功能新增**：2项（#1573, #1596）
- **文档更新**：1项（#1811）

### 2. 关键变更点及其与项目整体方向的关系
- **Qwen系列模型支持深化**：新增 Qwen3-TTS 的基准测试脚本（#1573）和夜间性能测试（#1700），并针对 Qwen3-omni 的已知问题（#1367）暂时跳过验证（#1812）。这表明项目正积极集成并验证最新的多模态模型（尤其是语音和图像编辑），强化其“全模态”服务能力。
- **前端与用户体验增强**：为 ComfyUI 添加视频和 LoRA 支持（#1596），降低了用户使用扩散模型（如图像生成/编辑）的门槛，符合项目“易用”（Easy）的目标。
- **系统稳定性与正确性提升**：
    - 修复 omni 模型任务报告逻辑，避免不必要的聊天初始化（#1645），提升服务效率。
    - 修复扩散模型服务中的 `base_model_paths` 属性暴露问题（#1771）和 Z-Image 张量并行度的差异阈值（#1808），确保多GPU推理的稳定性和正确性。
- **测试覆盖完善**：完成了 Qwen-Image-Edit 模型的完整扩散功能测试（#1682），确保复杂多模态功能的可靠性。

### 3. 对项目的影响和潜在意义
- **强化多模态服务生态**：对 Qwen 系列（TTS、图像编辑）的持续集成和测试，使项目能更好地支持前沿的多模态任务，吸引更多用户和开发者。
- **提升生产环境可靠性**：多项 Bug 修复和阈值调整直接针对推理服务的核心模块（模型加载、并行计算），减少了潜在的服务中断或错误输出风险。
- **降低使用门槛**：通过 ComfyUI 集成，为不熟悉代码的用户提供了可视化操作界面，扩大了项目受众。
- **保障持续交付质量**：完善的测试套件（包括性能基准和功能测试）为项目的快速迭代提供了质量保障。

### 4. 值得关注的技术点
- **张量并行度（Tensor Parallelism）调优**（#1808）：针对 Z-Image 模型的调整，反映了项目在优化大规模多模态模型分布式推理性能方面的持续努力。
- **模型任务动态报告**（#1645）：通过准确报告模型支持的任务，智能跳过不必要的初始化，这是一种针对“全模态”模型服务的高效资源管理策略。
- **ComfyUI 与 vllm-omni 的集成**（#1596）：将流行的可视化工作流工具与高性能推理后端结合，是提升开发者体验和推广项目的重要技术路径。

### 5. 基于项目背景的提交影响分析
这些提交共同推动了 `vllm-omni` 向 **“为所有人提供简单、快速、经济的全模态模型服务”** 的愿景迈进：
- **“Easy” (简单)**：ComfyUI 集成（#1596）和文档修复（#1811）直接改善了用户体验和入门难度。
- **“Fast” (快速)**：性能基准测试（#1700）和并行计算调优（#1808）关注推理速度的监控与优化。
- **“Cheap” (经济)**：通过修复不必要的初始化（#1645）和确保分布式推理的稳定性（#1808），间接降低了计算资源的浪费。
- **“Omni-modality” (全模态)**：对 Qwen 系列 TTS、图像编辑模型的深度集成与测试（#1573, #1682, #1700），是扩展模态支持范围的核心体现。

**总结**：昨日的更新是一次以 **“巩固基础、扩展边界、提升体验”** 为核心的迭代。项目在稳步修复底层引擎问题的同时，积极拥抱前沿模型（Qwen3系列）和流行工具链（ComfyUI），并构建了更完善的测试体系来保障服务质量，这非常符合一个处于快速发展期的全模态推理服务框架的发展路径。

## 详细提交记录

### [da4a077](https://github.com/vllm-project/vllm-omni/commit/da4a0771559de231ee37971bc9afd63e66dfc3c6)

- **作者**: wangyu
- **时间**: 2026-03-11T19:00:13Z
- **提交信息**: [Test] Skip the qwen3-omni relevant validation for a known issue 1367. (#1812)

Signed-off-by: yenuo26 <410167048@qq.com>

### [acde431](https://github.com/vllm-project/vllm-omni/commit/acde431668f74e0b4c28bef0f4a67d21feff376a)

- **作者**: Yueqian Lin
- **时间**: 2026-03-11T17:09:26Z
- **提交信息**: Add Qwen3-TTS benchmark scripts (#1573)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [f144f5e](https://github.com/vllm-project/vllm-omni/commit/f144f5effe04fbb48af45614fb39b71393ea50eb)

- **作者**: Yueqian Lin
- **时间**: 2026-03-11T17:07:47Z
- **提交信息**: [Test] Add Qwen3-TTS nightly performance benchmark (#1700)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [a6b5519](https://github.com/vllm-project/vllm-omni/commit/a6b55196167815f8f44901f43956942c65e7bb95)

- **作者**: Yueqian Lin
- **时间**: 2026-03-11T17:06:20Z
- **提交信息**: [Bugfix] Report supported tasks for omni models to skip unnecessary chat init (#1645)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [0f7c9c7](https://github.com/vllm-project/vllm-omni/commit/0f7c9c755de30a7d212b2cc1c39227d1efe404c4)

- **作者**: Lancer
- **时间**: 2026-03-11T12:52:10Z
- **提交信息**: [Bugfix] Expose base_model_paths property in _DiffusionServingModels (#1771)

Signed-off-by: Lancer <maruixiang6688@gmail.com>

### [af9784c](https://github.com/vllm-project/vllm-omni/commit/af9784c03f9163e41f656af710e8021f781034b2)

- **作者**: Didan Deng
- **时间**: 2026-03-11T12:30:54Z
- **提交信息**: [Bugfix] Adjust Z-Image Tensor Parallelism Diff Threshold (#1808)

Signed-off-by: Didan Deng <33117903+wtomin@users.noreply.github.com>

### [74eedd3](https://github.com/vllm-project/vllm-omni/commit/74eedd3ef1fef6f9a865975abd6f9d260ed59c2c)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-03-11T10:22:45Z
- **提交信息**: [Frontend] ComfyUI video & LoRA support (#1596)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>

### [a190982](https://github.com/vllm-project/vllm-omni/commit/a19098233b62a6381ebb771c6dbf5813ad436264)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-03-11T10:10:06Z
- **提交信息**: [Test] L4 complete diffusion feature test for Qwen-Image-Edit models (#1682)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [b313279](https://github.com/vllm-project/vllm-omni/commit/b313279af757c3b202f01179219221069709bc85)

- **作者**: Samit
- **时间**: 2026-03-11T09:32:12Z
- **提交信息**: [skip ci][Docs] doc fix for example snippets (#1811)

Signed-off-by: samithuang <285365963@qq.com>
Signed-off-by: Samit <285365963@qq.com>

---
