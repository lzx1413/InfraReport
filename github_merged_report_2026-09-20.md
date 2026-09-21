# GitHub Stars 合并报告 - 2026-09-20

**合并日期**: 2026-09-21
**监控日期**: 2026-09-20
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


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2215
- **最后更新**: 2026-09-21T03:06:20Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Feng, qcm1

## AI分析总结

根据提交记录和项目背景，分析总结如下：

1.  **主要更新类型**
    *   **功能新增**：为项目核心训练框架添加了针对特定模型（Qwen3.5）的新训练范式（MTP）支持。
    *   **Bug修复**：修复了特定模型（DiT）在训练恢复（resume）过程中的关键技术缺陷，涉及设备状态和随机数生成器（RNG）状态的持久化。

2.  **关键变更点及其与项目整体方向的关系**
    *   **支持MTP训练**：这直接扩展了VeOmni“Scaling Any Modality Model Training”的核心能力。MTP是一种先进的训练技术，此更新使框架能够适配并支持使用该技术的最新模型，体现了项目在功能兼容性上的主动跟进。
    *   **修复DiT恢复问题**：此修复确保了在使用分布式框架进行长时间、中断可恢复训练时的**可靠性和可复现性**。这是“Model-Centric Distributed Recipe Zoo”中“分布式”方案能否在生产环境稳定使用的基石。

3.  **对项目的影响和潜在意义**
    *   **提升框架的先进性与兼容性**：通过支持Qwen3.5等采用新技术范式的模型，VeOmni保持了与前沿模型生态的同步，增强了其作为通用训练基础架构的吸引力。
    *   **增强生产可用性**：修复训练恢复中的状态持久化问题，直接提升了框架在处理大规模、长周期训练任务时的稳定性和用户信任度，是从“研究工具”向“生产工具”演进的重要一步。

4.  **值得关注的技术点**
    *   **MTP训练集成**：MTP机制的具体实现方式及其与框架分布式策略的协同是技术亮点。
    *   **跨重启的RNG状态管理**：在分布式训练场景下，准确持久化并恢复设备、条件模型以及随机数生成器状态，是保证训练数学一致性且避免调试困难的关键技术。

5.  **基于项目背景对项目发展的影响**
    *   这两项提交共同推动了VeOmni向其**核心愿景**的迈进：一个既能广泛支持最新模型与训练方法（如MTP），又能提供高度稳定可靠的分布式训练体验的平台。功能新增拓宽了其支持的“食谱”范围，而可靠性修复则保障了这些“食谱”能够被成功、可重复地执行，共同增强了项目在开源社区中的实用价值和竞争力。

## 详细提交记录

### [262b4a5](https://github.com/ByteDance-Seed/VeOmni/commit/262b4a537f53a6e46382fde1e0c71901b4cbf023)

- **作者**: qcm1
- **时间**: 2026-09-20T10:01:31Z
- **提交信息**: [model] feat: support mtp training for Qwen3.5 dense and moe model (#1088)

### [c21de9a](https://github.com/ByteDance-Seed/VeOmni/commit/c21de9a79e748e69bf732d2fd692df9a0c7184f4)

- **作者**: Feng
- **时间**: 2026-09-20T10:01:21Z
- **提交信息**: [ckpt, trainer] fix: persist device and condition-model RNG across DiT resume (#1189)

Co-authored-by: Feng0w0 <Feng0w0@users.noreply.github.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2841
- **最后更新**: 2026-09-21T11:57:04Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 3
- **主要提交者**: Yang Yong (雍洋), Bilang ZHANG, STwangyingrui

## AI分析总结

基于提供的提交记录和项目背景，以下是对本次提交的总结分析：

1.  **主要更新类型**：本次提交批次以**性能优化**和**功能新增**为核心，同时辅以必要的**文档更新**与小幅改进。

2.  **关键变更点与项目方向**：
    *   **核心优化**：对`Qwen-Image-2.1`模型在NVIDIA RTX 5090上进行了深度的**FP8推理优化**，包括新增CPU卸载、多种后端支持以及量化的专用配置。这直接响应了项目“Light（轻量）”和“高性能”的核心目标。
    *   **功能扩展**：为`MiniMax-H3`模型新增了流式推理支持，并为`Qwen-Image-2.1`添加了预热和编译支持，显著提升了框架的**功能完备性**和**推理稳定性**。
    *   **生态兼容**：调整了`Qwen-Image-2.1`的输出格式以与`diffusers`库对齐，体现了项目对主流工具链的**兼容性考虑**。

3.  **对项目的影响和潜在意义**：
    *   **性能标杆**：针对最新消费级显卡RTX 5090的优化，使项目在尖端硬件上保持性能领先，对吸引用户和开发者有重要意义。
    *   **易用性提升**：通过补充启动脚本、配置文件和文档，降低了优化功能的使用门槛，使得高级优化更容易被采纳。
    *   **模型支持广度**：持续完善对`Qwen-Image-2.1`和`MiniMax-H3`等模型的支持，巩固了项目作为多模型、高性能推理平台的地位。

4.  **值得关注的技术点**：
    *   **RTX 5090 FP8优化路径**：集成了`fp8-sgl`后端和SM120架构的FP16累积技术，展示了前沿的硬件适配能力。
    *   **条件编码器CPU卸载**：在DiT去噪前释放显存，是一种有效的资源调度策略。
    *   **动态稀疏与SageAttention3**：作为实验性选项提供，体现了项目在探索更激进优化方案上的开放性。

5.  **对项目发展的影响**：
    这些提交共同推动项目向三个关键方向发展：**更广的硬件覆盖**（从支持多款GPU到深度优化最新型号）、**更强的模型性能**（针对特定模型的深度调优）以及**更好的开发者体验**（更完善的文档与配置）。这完全符合README中“轻量、高效视频/图像生成推理框架”的定位，并有助于其在日益激烈的开源AI推理框架竞争中建立差异化优势。

## 详细提交记录

### [8d0c1a5](https://github.com/ModelTC/LightX2V/commit/8d0c1a5fa7add4a76a22977675738d784bca7c65)

- **作者**: STwangyingrui
- **时间**: 2026-09-20T14:11:24Z
- **提交信息**: optimize(qwen-image-2.1): add RTX 5090 FP8 inference optimizations (#1543)

Add an optimized Qwen-Image-2.1 inference path for RTX 5090, covering
both text-to-image and image-to-image workloads.

- Add stage-level condition-encoder CPU offload to release GPU memory
before DiT denoising.
- Add FP8 DiT linear inference with both `fp8-sgl` and SM120
FP16-accumulation backends.
- Add a Qwen-Image-2.1 conversion profile using weight qmax 14 and
activation qmax 7 for FP16 accumulation.
- Use dense SageAttention2 in the recommended RTX 5090 configuration.
- Add paired T2I/I2I configs and launch scripts.
- Add optional SageAttention3 and dynamic sparse SLA configs as
aggressive experiments that require manual image-quality review.
- Document model conversion, optimized usage, and measured RTX 5090
performance.

### [4074476](https://github.com/ModelTC/LightX2V/commit/40744764aacc141166d9aa9c9596ba47ab1eab0e)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-20T12:10:56Z
- **提交信息**: feat(minimax_h3_causal): add warmup and compile support, optimize vid… (#1542)

…eo output

### [2773aec](https://github.com/ModelTC/LightX2V/commit/2773aecb5db497091aa304c322c15a1e3bbb0706)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T10:25:52Z
- **提交信息**: Use opencv for qwen-image-2.1 saving result. (#1541)

### [c83f435](https://github.com/ModelTC/LightX2V/commit/c83f43571bb79498be4ff169a96a02ea807e260e)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T10:08:55Z
- **提交信息**: Support warmup for qwen-image-2.1 (#1540)

### [d43f15f](https://github.com/ModelTC/LightX2V/commit/d43f15f769d1d1ba129caa298ca431e0b39af39b)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-20T09:58:36Z
- **提交信息**: feat: support MiniMax-H3 causal streaming RefA2V inference (#1539)

### [a918b2d](https://github.com/ModelTC/LightX2V/commit/a918b2daec3a9e758bd79922f1d382a577e205d2)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T09:17:09Z
- **提交信息**: Align output sizes with diffusers for qwen-image-2.1 (#1538)

### [8b5df72](https://github.com/ModelTC/LightX2V/commit/8b5df725f7e807b3e1123da7ac49bdcbb978183a)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T08:11:21Z
- **提交信息**:  Update qwen-image-2.1 readme. (#1537)

### [2da731b](https://github.com/ModelTC/LightX2V/commit/2da731be7cd912a0fd87b26b92ec2653577da0c5)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T07:57:32Z
- **提交信息**: Update qwen-image-2.1 readme. (#1536)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2254
- **最后更新**: 2026-09-21T05:46:50Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6469
- **最后更新**: 2026-09-21T10:52:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4494
- **最后更新**: 2026-09-21T11:19:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34555
- **最后更新**: 2026-09-21T11:15:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
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


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13152
- **最后更新**: 2026-09-21T09:30:00Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Zhongjie Duan, Hong Zhang

## AI分析总结

基于提供的提交记录与项目背景，现总结如下：

### 1. 主要更新类型
*   **功能增强与集成**：主要提交集中在集成并支持新的图像生成模型 `Qwen-Image-2.1`。
*   **文档与示例更新**：为配合新模型功能，更新了相应的示例代码与README文档。
*   **Bug修复与调整**：包含对调度器(scheduler)、文本编码器(text encoder)的修复及多项微调(minor fix)。
*   **版本发布**：将项目版本号更新至 `2.1.8`。

### 2. 关键变更点及其与项目整体方向的关系
*   **模型ID重命名与调度器复用**：将模型标识统一并复用 `Qwen-Image` 的调度器。这体现了项目在管理**多模型资源**和**代码复用**方面的持续优化，旨在提升开发效率与维护性。
*   **扩展 `lora_target_modules` 与添加兼容性补丁**：这些技术调整旨在确保新模型 `Qwen-Image-2.1` 能无缝集成到现有框架中，特别是与 LoRA 微调工作流兼容。这直接服务于项目**支持多样化扩散模型与高效微调**的核心目标。
*   **全面的示例与文档更新**：确保新功能有据可依、有例可循，符合项目作为**易用、开源工具**的定位。

### 3. 对项目的影响和潜在意义
*   **直接能力扩展**：通过支持更先进的 `Qwen-Image-2.1` 模型，直接提升了工具在**高质量图像生成**方面的输出能力，增强了用户工具箱。
*   **生态系统完善**：持续快速地集成新模型（尤其是来自同生态的模型），巩固了 DiffSynth-Studio 作为**一站式、前沿扩散模型应用平台**的地位。
*   **项目活跃度与成熟度提升**：频繁的更新、修复与版本迭代（至2.1.8）向社区传递了项目**持续维护与积极发展**的信号，有助于吸引和留住用户与贡献者。

### 4. 值得关注的技术点
*   **调度器的复用与修复**：这显示了项目对生成流程核心组件的重视。确保调度器在不同模型下正确工作是获得高质量生成结果的关键。
*   **LoRA目标模块的更新**：这表明项目正在适配新模型的网络结构，以优化其微调效果和效率，是实用性的体现。
*   **向后兼容性**：通过添加“兼容性补丁”，确保新功能不会破坏旧的工作流，体现了良好的软件工程实践。

### 5. 对项目发展的影响
结合README可知，DiffSynth-Studio 致力于提供强大的AI视频/图像生成与创作工具。本次更新：
*   **强化核心竞争力**：通过快速跟进并集成 `Qwen-Image-2.1` 这样的前沿模型，项目**保持了技术先进性**，使其在同类开源项目中更具吸引力。
*   **拓展应用边界**：新模型的加入可能带来新的艺术风格或更高的生成质量，**丰富了创作者的可选工具集**，助力项目的“创意生成”初衷。
*   **巩固平台化趋势**：一系列集成、修复与文档工作，并非针对单一模型，而是为了更好地**支持模型的模块化接入与使用**，这正推动项目从“工具集”向更易扩展的“平台”演进。

## 详细提交记录

### [d2d684a](https://github.com/modelscope/DiffSynth-Studio/commit/d2d684ad1f912949eae08453b9411ae40c5ec0ab)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-20T09:27:36Z
- **提交信息**: update to version 2.1.8 (#1696)

### [982abec](https://github.com/modelscope/DiffSynth-Studio/commit/982abec6856227c287d798b87ed761af94d924e6)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-20T08:57:45Z
- **提交信息**: update Qwen-Image-2.1 examples (#1695)

### [7f31eff](https://github.com/modelscope/DiffSynth-Studio/commit/7f31effabd63310dfd43e57a0a7d08c44a437dc7)

- **作者**: Hong Zhang
- **时间**: 2026-09-20T07:54:01Z
- **提交信息**: update qwen-image-2.1 to latested behavior (#1694)

* support qwen-image2.1

* fix scheduler

* rename model id

* reuse qwen-image scheduler

* update lora_target_modules

* update readme

* add compatible patch to qwenimage2.1

* minor fix

* minor fix for text encoder

---------

Co-authored-by: Artiprocher <wangye87v5@hotmail.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36252
- **最后更新**: 2026-09-21T11:40:41Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 26
- **主要提交者**: JinYan Su, Aurick Qiao, chenyang08056032

## AI分析总结

根据提供的提交记录，结合SGLang作为高性能大语言模型推理框架的项目背景，昨日的提交主要体现了以下发展动向：

### 1. 主要更新类型
*   **重构 (占比最高)**：集中在 `sgl-router` 路由组件，优化代码结构、配置管理和启动逻辑。
*   **性能优化**：涵盖注意力机制融合、内存传输优化（固定内存）、特定模型（如DeepSeek, Kimi）的内存与计算优化。
*   **功能新增与适配**：新增对 `bf16` MoE 路由、`mxfp4` MoE（MiMo V2）、共享 RMSNorm 调度等的支持，以及为多款新模型（Kimi-K3, DeepSeek-V4.1, Qwen4-Exp）提供专项优化。
*   **CI/CD 与测试改进**：包括测试通道隔离、CI权限更新、测试用例修复与框架改进、测试选择流水线等。
*   **Bug修复**：修复TopK回退、CUDA图兼容性、稀疏传输层ID、测试配置等多个影响稳定性与正确性的问题。
*   **文档更新**：主要集中在NPU相关文档的修正与简化。

### 2. 关键变更点与项目方向
*   **路由与调度核心强化**：对 `sgl-router` 的持续重构（BucketResolver、配置、启动逻辑）表明项目在系统架构层面进行优化，旨在提升路由决策的模块化、清晰度和可维护性，以支持更复杂的负载均衡和调度策略。
*   **性能与内存管理精细化**：多处提交（如#39200, #39777, #40217）直接针对计算图融合和内存传输（Pinned Memory），体现了项目对端到端推理延迟和吞吐量的持续追求。对`DeepSeek-V4.1`和`Kimi-K3`的专项优化则显示了其对前沿模型高效部署的支持。
*   **异构计算与生态扩展**：针对 `NPU` 和 `AMD` 平台的提交，以及`Rust-renderer`独立预处理的进展，表明项目在积极拓展硬件支持和优化技术栈。
*   **测试与CI健壮性提升**：大量关于CI流水线、测试修复和框架改进的提交（如#40496, #40288, #40392），反映出项目在基础设施层面投入，以保障快速迭代的质量与稳定性。

### 3. 对项目的影响和潜在意义
*   **架构更稳健**：`sgl-router`的重构为未来更灵活、高效的请求分发奠定了坚实基础。
*   **性能天花板提升**：通过底层内存与计算优化，能为用户带来更佳的吞吐与延迟体验。
*   **支持范围扩大**：对更多模型架构（特别是MoE）、精度（bf16, mxfp4）和硬件（NPU, AMD）的支持，巩固了其作为通用推理框架的竞争力。
*   **开发效率与质量保障**：改进的CI/CD和测试体系，能加速开发流程并减少线上问题。

### 4. 值得关注的技术点
*   **`sgl-router`的“PowerOfTwo”算法**（#40241）：可能是一种新颖或改进的负载均衡策略，值得深入分析其设计。
*   **异步采样元数据的Pinned Memory传输**（#39777）：利用固定内存降低CPU-GPU数据拷贝延迟，是提升流水线并行效率的典型优化。
*   **预填充CUDA图的合约保留**（#35452）：解决了在CUDA Graph模式下，预填充阶段可能破坏模型运行器内部状态一致性的关键问题。
*   **移除swa和mamba radix cache**（#40313）：可能标志着调度或缓存策略的重大简化或演进，影响系统内存占用与调度逻辑。

### 5. 对项目发展的影响
这些提交共同推动SGLang项目向**更高性能、更强兼容性、更稳定可靠**的方向发展。它不仅在持续深化对**核心推理引擎**的优化（内存、调度、计算），也在积极拓展**硬件和模型生态**，并大力加强**工程基础设施**（CI/测试）。这种“核心优化”与“生态拓展”并重的策略，有助于SGLang巩固其在开源LLM推理领域的技术领先地位，并为社区用户提供更强大、易用的工具链。

## 详细提交记录

### [aedda83](https://github.com/sgl-project/sglang/commit/aedda8377e4521ec402192b3f3aaa9534175b544)

- **作者**: Kan Wu
- **时间**: 2026-09-20T23:57:07Z
- **提交信息**: [sgl-router] refactor - layout BucketResolver, Bucket, EngineGroup and implement PowerOfTwo (#40241)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4a9dc5c](https://github.com/sgl-project/sglang/commit/4a9dc5c4af9631b658c6f9d61129f5d2ac32e500)

- **作者**: Kan Wu
- **时间**: 2026-09-20T23:49:23Z
- **提交信息**: [sgl-router] refactor - move policy-required states under src/state (#40272)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [acd20a5](https://github.com/sgl-project/sglang/commit/acd20a516ed2a3274ef574f9506939360de2ba22)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T23:46:53Z
- **提交信息**: [CI] Give the kernel lane a 5090 suite and move kernel-only tests off the general lane (#40496)

### [42875bc](https://github.com/sgl-project/sglang/commit/42875bcd2a7f2d9685eb3dd98fd787b54e3787d1)

- **作者**: Divy
- **时间**: 2026-09-20T23:28:54Z
- **提交信息**: fix(modelopt): dispatch NVFP4 MoE on the cached backend, not the live global (#38932)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [2fa6b94](https://github.com/sgl-project/sglang/commit/2fa6b94e3440d28dab7460246f0b34426a4e4b80)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-20T23:20:37Z
- **提交信息**: [Perf] Fuse the glm5_next mHC attn->MLP boundary (#39200)

Co-authored-by: mmangkad <mohammad.angkad@radixark.ai>

### [983e643](https://github.com/sgl-project/sglang/commit/983e643854f15cf9ef4370a49dfd74b6af54c3e3)

- **作者**: ollybbmonster
- **时间**: 2026-09-20T23:13:59Z
- **提交信息**: [Feature] support bf16 MoE router and mxfp4 MoE for MiMo V2 (#40448)

### [2e2d8a2](https://github.com/sgl-project/sglang/commit/2e2d8a2fda5c3bb9a8f62601679bfc2b18ec67d6)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T22:43:46Z
- **提交信息**: [CI] Drive per-commit stage jobs from a runner table instead of copied job blocks (#40495)

### [d97aed2](https://github.com/sgl-project/sglang/commit/d97aed2c908df22a68bc9b787395f1836970eee3)

- **作者**: luoroger37
- **时间**: 2026-09-20T22:41:41Z
- **提交信息**: Fix TopK v2 fallback when 16-block cluster capacity is zero (#40163)

Co-authored-by: Hank Han <hanhan7630@outlook.com>

### [f31a7bd](https://github.com/sgl-project/sglang/commit/f31a7bd45c6ab86796aa012ebfd2378bc42e1a59)

- **作者**: Yuxuan Zhang
- **时间**: 2026-09-20T22:31:31Z
- **提交信息**: Use pinned memory for asynchronous sampling metadata transfers (#39777)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [95521da](https://github.com/sgl-project/sglang/commit/95521da18df4780e9c63f5e2ddd284ecd9ca9b1c)

- **作者**: Harmya Bhatt
- **时间**: 2026-09-20T21:43:19Z
- **提交信息**: [DeepSeek-V4.1] Bound dense prefill indexer memory (#40217)

### [c2c3629](https://github.com/sgl-project/sglang/commit/c2c3629f2dc0d4fa9386e90ea1a63e6ed5d50580)

- **作者**: JinYan Su
- **时间**: 2026-09-20T21:39:45Z
- **提交信息**: [Kimi-K3] O(1) expert weight lookup in load_weights (#38805)

Signed-off-by: JinYan Su <751080330@qq.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [f6483e4](https://github.com/sgl-project/sglang/commit/f6483e479fc7de2ee67230f6004722966bfe71bf)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T21:36:02Z
- **提交信息**: [Test] Drop cause-less disabled tests, fix XPU lane, demote quality gates off base-c (#40288)

### [d229952](https://github.com/sgl-project/sglang/commit/d229952e25b4df459e7d9bf74336717e3883e906)

- **作者**: Aurick Qiao
- **时间**: 2026-09-20T20:53:14Z
- **提交信息**: [Fix] Preserve model runner contracts in prefill CUDA graphs (#35452)

Co-authored-by: Oasis-Git <ayw.sirius19@gmail.com>
Co-authored-by: Ke Bao <ispobaoke@gmail.com>

### [745de73](https://github.com/sgl-project/sglang/commit/745de73ba3c136b6f99b7a3e2177ed1a8eef4a56)

- **作者**: Shangming Cai
- **时间**: 2026-09-20T17:37:50Z
- **提交信息**: Add CODEOWNERS entry for sglang-renderer (#40483)

### [b3e4d19](https://github.com/sgl-project/sglang/commit/b3e4d198af5e74e5070e541475fd767302342be9)

- **作者**: Khoa Pham
- **时间**: 2026-09-20T17:17:15Z
- **提交信息**: [PD] Bound cached-prefix DCP transfers by pack capacity (#40376)

### [80da443](https://github.com/sgl-project/sglang/commit/80da4432d085ed4d6166ef643d9fd2b829dbb0c5)

- **作者**: Shuwen Wang
- **时间**: 2026-09-20T16:42:55Z
- **提交信息**: [Simulator] Fix meta host memory budgets on constrained runners (#40440)

### [3dbdd70](https://github.com/sgl-project/sglang/commit/3dbdd700e2e99460cb5aa3e1da1b7567b96ef7d7)

- **作者**: WenhaoZhang
- **时间**: 2026-09-20T16:07:37Z
- **提交信息**: [CI] update CI permissions (#40474)

### [e97614d](https://github.com/sgl-project/sglang/commit/e97614d10c8e2c90a72387276086dc33f21bba67)

- **作者**: Jimmy Shong
- **时间**: 2026-09-20T15:28:25Z
- **提交信息**: [Qwen4-Exp] Build the offloaded PLE table on the meta device so --ple-offload-embedding never materialises it on the accelerator (#39928)

Co-authored-by: Yangmin Li <yangminl@nvidia.com>

### [5f017ff](https://github.com/sgl-project/sglang/commit/5f017ffabb6ab8d214f6a4616ee8bd98a376034a)

- **作者**: ZY Y
- **时间**: 2026-09-20T14:42:00Z
- **提交信息**: Update test cases and performance testing framework (#40392)

### [404dee1](https://github.com/sgl-project/sglang/commit/404dee10c040daa6e58d75dba98ae020d5f4acdd)

- **作者**: chenyang08056032
- **时间**: 2026-09-20T14:40:55Z
- **提交信息**: [NPU] add coverage-based precision test selection pipeline (#38339)

### [8923f4d](https://github.com/sgl-project/sglang/commit/8923f4d779b54ff8e0103ea80179311c6a3c3cb3)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-20T14:39:34Z
- **提交信息**: [Test] Fix optimistic prefill disaggregation test after mamba radix cache removal (#40469)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [791c785](https://github.com/sgl-project/sglang/commit/791c7850d0960fd768102f71e7d999b036bb75ba)

- **作者**: faceless void
- **时间**: 2026-09-20T14:08:02Z
- **提交信息**: [Diffusion] Enable shared RMSNorm dispatch for SenseNova-U1 (#39705)

Signed-off-by: syd520zy <529477025@qq.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [7b1c2ed](https://github.com/sgl-project/sglang/commit/7b1c2ed0a423718492069a56db48bd451b5ec994)

- **作者**: Sage
- **时间**: 2026-09-20T14:03:12Z
- **提交信息**: [rust-renderer] Standalone preprocessing (#36718)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>
Co-authored-by: Rain Jiang <96632942+rainj-me@users.noreply.github.com>

### [6880a47](https://github.com/sgl-project/sglang/commit/6880a4795533640f41ebb3db9e4ae0af5a371a1f)

- **作者**: Mick
- **时间**: 2026-09-20T12:39:26Z
- **提交信息**: [diffusion] docs: simplify Qwen-Image 2.1 cookbook (#40455)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [c610c40](https://github.com/sgl-project/sglang/commit/c610c403990255e6ffe41d7314f6fb748a53085f)

- **作者**: Kan Wu
- **时间**: 2026-09-20T11:40:04Z
- **提交信息**: [sgl-router] refactor - config and organize CLI options (#39867)

### [efa7be2](https://github.com/sgl-project/sglang/commit/efa7be2091282e96318f0d9d22d9f78dde099848)

- **作者**: Ruiyan Ma
- **时间**: 2026-09-20T10:00:06Z
- **提交信息**: [Simulator][Compatibility] Adapt to latest KV cache pool interfaces (#40418)

### [0024efa](https://github.com/sgl-project/sglang/commit/0024efa0de38794ee309ba10ab00ebb891a3d050)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T09:01:22Z
- **提交信息**: [CI] Derive registered-test kind from the registry call instead of the path (#40294)

### [671630a](https://github.com/sgl-project/sglang/commit/671630abf1b783cafcfc9277f7afdc3f56abc338)

- **作者**: Kan Wu
- **时间**: 2026-09-20T08:55:34Z
- **提交信息**: [sgl-router] refactor - main startup logic (#39861)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [2a0cb2f](https://github.com/sgl-project/sglang/commit/2a0cb2f04edbd85778f1fb8c26272c7f668d9c34)

- **作者**: HuangJi
- **时间**: 2026-09-20T08:40:28Z
- **提交信息**: [Diffusion][MiniMax-H3] Add SM120 Sage compute for SubBlock sparse attention (#40116)

### [414adef](https://github.com/sgl-project/sglang/commit/414adef060f41977e3a4888cdb35cb0b1f4b8858)

- **作者**: Mick
- **时间**: 2026-09-20T08:33:23Z
- **提交信息**: [CI] skip srt rust extension builds for diffusion-only PRs (#40293)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [dc002c8](https://github.com/sgl-project/sglang/commit/dc002c85fcc94b8b145207d6bfbd57d60a3113f5)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T08:25:34Z
- **提交信息**: [Test] Fix OOT DFlash hook test resolving the draft config over the network (#40427)

### [9f3d275](https://github.com/sgl-project/sglang/commit/9f3d2759407f2e3b9c097b41f90ddac3a499beb5)

- **作者**: Shuwen Wang
- **时间**: 2026-09-20T08:24:24Z
- **提交信息**: [HiCache] Fix sparse hybrid transfer layer IDs (#37870)

Co-authored-by: Seokhoon Kang <sh.kang@postech.ac.kr>

### [e540092](https://github.com/sgl-project/sglang/commit/e54009240a84bf52eb7a21ec532ea49f1b9dd941)

- **作者**: amd-danli103
- **时间**: 2026-09-20T08:16:39Z
- **提交信息**: [AMD][DSV4] feat: enable DSpark with fp8 unified_kv on gfx950 (#38901)

Co-authored-by: HAI <hixiao@gmail.com>

### [a8a4d86](https://github.com/sgl-project/sglang/commit/a8a4d86be9f483fabd097350b06b6ae6e6905874)

- **作者**: Ke Bao
- **时间**: 2026-09-20T08:16:27Z
- **提交信息**: Remove swa and mamba radix cache (#40313)

### [5c69e32](https://github.com/sgl-project/sglang/commit/5c69e32abe013fa1b913022682a3104c79105f37)

- **作者**: amote-i
- **时间**: 2026-09-20T07:15:58Z
- **提交信息**: [NPU] [DOC] fix typos, heading levels and terminology in NPU docs (#40402)

### [f4c2563](https://github.com/sgl-project/sglang/commit/f4c256354cc8a15d18b11f970f01a82d7394a715)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-20T07:15:28Z
- **提交信息**: [kimi k3][pd disagg] support pp prefill + dcp decode with dspark (#40045)

### [22f02cc](https://github.com/sgl-project/sglang/commit/22f02cc3399dcd59380fc546de8d3c89fba6fa3a)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-20T07:08:04Z
- **提交信息**: [Test] Fix scheduler fixtures after prefill burst counting (#40411)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
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


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92320
- **最后更新**: 2026-09-21T12:05:56Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 15
- **主要提交者**: Wentao Ye, Sheral Kumar, YiSheng5

## AI分析总结

基于对 vllm 仓库昨日提交的分析，结合其“提供简单、快速且低成本的 LLM 推理服务”的项目目标，总结如下：

**1. 主要更新类型**
本次提交涵盖了多维度的更新，主要包括：
*   **Bug修复**：修复了 XPU 上进程可见性导致的精度问题、KV缓存相关的索引与偏移错误。
*   **功能新增/集成**：集成了 Humming 特性、为特定模型添加了新的精度格式支持（如 MiMo V2 的 bf16/MXFP4 MoE）、暴露了每请求的 spec decode 指标。
*   **性能优化**：融合了 Triton 内核以提升性能、共享了持久工作空间、采用了 FP8 输出投影以提升效率。
*   **硬件与后端支持**：为 XPU（Intel）、ROCm（AMD）等硬件平台进行了适配、优化和 CI 改进。
*   **代码重构与清理**：移除了无用的内核代码，重命名了相关配置项。

**2. 关键变更点及与项目方向的关系**
*   **深化硬件生态支持**：多个针对 XPU、ROCm 和特定 GLM 模型优化的提交，表明项目正持续投入资源，拓宽对不同 AI 加速器的兼容性与性能表现，这直接服务于“为所有人提供服务”的普惠目标。
*   **强化特定架构模型服务**：对 Mamba/KDA 混合递归状态的传输（MoRIIO）和 GLM-5.3-Flash 模型的深度优化（如 kpool tail 处理），显示项目在积极扩展对 Transformer 之外的新型或特定领域模型架构的高效服务能力。
*   **提升运维与可观测性**：在生成 API 中暴露 spec decode 指标，有助于用户更精细地监控和理解推测解码的性能，提升了生产环境的易用性。

**3. 对项目的影响和潜在意义**
*   **增强系统健壮性**：修复的 Bug 涉及分布式精度、缓存索引和前端输入处理，有助于提升服务在不同部署场景下的稳定性和可靠性。
*   **释放硬件性能潜力**：针对 ROCm 和 GLM 的性能优化（如内核融合、FP8 应用），旨在压低推理成本，直接呼应“低成本”目标。
*   **扩大模型覆盖范围**：对 DeepSeek-V4.1、MiMo V2、VoyageQwen3 等更多模型的支持，增加了框架的通用性，吸引更多用户。

**4. 值得关注的技术点**
*   **非 Transformer 状态管理**：`[KVConnector][MoRIIO]` 提交涉及在 READ 模式下传输 Mamba/KDA 的递归状态，这是高效服务状态空间模型等非 Transformer 架构的关键技术挑战。
*   **模型内核深度优化**：围绕 GLM-5.3-Flash 的多个提交，展示了如何通过融合 Triton 内核、处理索引边界等底层操作，实现对特定模型结构的极限性能挖掘。
*   **CUDA Graph 的广泛应用**：为 DeepSeek 模型的编码器添加 CUDA Graph 支持，是利用静态图优化减少推理开销的典型实践，对提升吞吐量至关重要。

**5. 如何影响项目发展**
这些提交共同推动 vllm 朝着 **更全面、更高效、更专业** 的方向演进。通过持续修复边缘情况下的 Bug，项目的基础可靠性得到夯实；通过深度集成 Humming 等新特性和支持新模型格式，项目的功能边界在不断拓展；而针对特定硬件和模型架构的极致优化，则巩固了其在高性能推理服务领域的技术领先性。整体上，这些活动使 vllm 更接近一个 **通用、高性能且易于部署的 LLM 推理引擎** 的愿景。

## 详细提交记录

### [17e50b9](https://github.com/vllm-project/vllm/commit/17e50b9b761023d5f2499f062507df1ff49092a4)

- **作者**: YiSheng5
- **时间**: 2026-09-20T22:50:25Z
- **提交信息**: [XPU][UT]Bugfix when the process can't see all the world_size meet accuracy issue. (#57779)

Signed-off-by: yisheng <yi.sheng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [9679173](https://github.com/vllm-project/vllm/commit/96791737887224c8bfec0a791517759f62e4d93b)

- **作者**: YukioZzz
- **时间**: 2026-09-20T21:30:34Z
- **提交信息**: [KVConnector][MoRIIO] Transfer hybrid mamba/KDA recurrent state in READ mode (#51052)

Signed-off-by: Yichao Zhu <Yichao.Zhu@amd.com>

### [01f1f58](https://github.com/vllm-project/vllm/commit/01f1f58f10c616850a5f5ade129a7b58d62075fb)

- **作者**: Sheral Kumar
- **时间**: 2026-09-20T20:20:39Z
- **提交信息**: [ROCm][CI] Query HIP device memory for test GPU teardown waits. (#57450)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [4868312](https://github.com/vllm-project/vllm/commit/4868312128172a424a7cf4c90f25c53b49186346)

- **作者**: Wentao Ye
- **时间**: 2026-09-20T17:39:23Z
- **提交信息**: [Refactor] Remove dead kernel code (#57621)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [49ee12d](https://github.com/vllm-project/vllm/commit/49ee12d742b4a5524d2a3a3ee6c3fb77e4913073)

- **作者**: roikoren755
- **时间**: 2026-09-20T16:50:34Z
- **提交信息**: [Misc] Rename --enable-mamba-fine-grained-prefix-cache (#53945 follow-up) (#57382)

Signed-off-by: Roi Koren <roik@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7d99c2c](https://github.com/vllm-project/vllm/commit/7d99c2c4fd61cdeebd29cc7b60584bad10d1ef99)

- **作者**: Jinzhen Lin
- **时间**: 2026-09-20T15:11:01Z
- **提交信息**: [Feature][Humming] Humming feature integration (#56685)

Signed-off-by: jinzhen.ljz <jinzhen.ljz@antgroup.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [27757dd](https://github.com/vllm-project/vllm/commit/27757dde020ecda4f9b0e2c5ca2df1c29badc82f)

- **作者**: Isotr0py
- **时间**: 2026-09-20T13:51:13Z
- **提交信息**: [DSV4.1] Add encoder cuda graph support for deepseek-v4.1-flash (#56625)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [9b2f34c](https://github.com/vllm-project/vllm/commit/9b2f34cad446f73b1699e8236ec0b611a65f48af)

- **作者**: Zyann
- **时间**: 2026-09-20T13:25:56Z
- **提交信息**: [Feature] support bf16 MoE router and mxfp4 MoE for MiMo V2 (#57784)

Signed-off-by: Zyann7 <62597503+Zyann7@users.noreply.github.com>
Co-authored-by: Abatom <182586866+Abatom@users.noreply.github.com>

### [10e6a7f](https://github.com/vllm-project/vllm/commit/10e6a7f21094b76c65efb029b39b3f2227516418)

- **作者**: Hongxin Xu
- **时间**: 2026-09-20T12:21:33Z
- **提交信息**: [Frontend] Expose per-request spec decode metrics in generate API (#43310)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Codex <codex@openai.com>

### [bf01fc4](https://github.com/vllm-project/vllm/commit/bf01fc4a313cc90863c470f37a26e41fd7b16fd1)

- **作者**: Chauncey
- **时间**: 2026-09-20T11:17:59Z
- **提交信息**: [GLM-5.3-Flash] Route kpool indexer top-k through the shared   SparseIndexerTopk dispatcher (#57546)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [f648eed](https://github.com/vllm-project/vllm/commit/f648eed23dc48fcc8ba64be0c4182f8e775b5bfa)

- **作者**: Jared Wen
- **时间**: 2026-09-20T10:58:55Z
- **提交信息**: [Bugfix][KV Offload] Skip non-prefix-cacheable groups in SimpleCPUOffload (GLM-5.3-Flash kpool tail and QSA) (#56810)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Signed-off-by: Jared Wen <w13431838023@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Zhewen Li <zhewenli@inferact.ai>

### [1b9fa3e](https://github.com/vllm-project/vllm/commit/1b9fa3eaa8ff23d1a583f2f77dd2b33c9f896ee8)

- **作者**: Jared Wen
- **时间**: 2026-09-20T10:20:55Z
- **提交信息**: [Perf][GLM] Fuse the kpool tail slot mapping into one Triton kernel (#57534)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [db1bfdd](https://github.com/vllm-project/vllm/commit/db1bfdd4fb0dd7b8226402ee00abc7a987561b7c)

- **作者**: Jared Wen
- **时间**: 2026-09-20T10:15:04Z
- **提交信息**: [Bugfix][GLM-5.3-Flash] Address kpool tail blocks by the padded indexer stride in the NVIDIA prefill seed kernel (#57477)

Signed-off-by: Jared Wen <w13431838023@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0748d3b](https://github.com/vllm-project/vllm/commit/0748d3bd57cb5c4303e58c8465e21f069629480d)

- **作者**: mahird3
- **时间**: 2026-09-20T09:50:00Z
- **提交信息**: [Model][LoRA] Enable LoRA support for VoyageQwen3BidirectionalEmbedModel (#57708)

Signed-off-by: Mahir Dursunoglu <142054011+mahird3@users.noreply.github.com>

### [e5fce7b](https://github.com/vllm-project/vllm/commit/e5fce7b56b07cdf992febd0862bfd599d6dca3fd)

- **作者**: Misha Goin
- **时间**: 2026-09-20T09:28:33Z
- **提交信息**: [Core][Kernel] Share persistent workspaces for Marlin and Humming (#57421)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: ErinYin <liang.yin@daocloud.io>

### [0e110f6](https://github.com/vllm-project/vllm/commit/0e110f696db450f5645ce1daf9945241212d6ef3)

- **作者**: yinfengLiu
- **时间**: 2026-09-20T09:13:55Z
- **提交信息**: [ROCm][DSV4][Perf] Use FP8 WO_A output projection (#54894)

Signed-off-by: Liuyinfeng01 <yinfeliu@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [27b7757](https://github.com/vllm-project/vllm/commit/27b7757f6364be5b0b714793ccdc3e3931443bca)

- **作者**: Dilber
- **时间**: 2026-09-20T08:52:27Z
- **提交信息**: [Bugfix][Frontend] Bound the prompt after multimodal expansion (#57076)

Signed-off-by: Dilber P Shakir <dilbersha@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6958
- **最后更新**: 2026-09-21T11:45:46Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 13
- **主要提交者**: DanaerLee, psv666, jingchengtian

## AI分析总结

基于提供的提交记录和项目背景，对“vllm-project/vllm-omni”仓库昨日提交的分析总结如下：

### 1. 主要更新类型
*   **性能优化**：针对MOSS-TTS模型的流式解码和深度转换器进行了硬件加速与策略优化（提交#1， #9）。
*   **Bug修复**：修复了多个关键模型的运行问题，包括实时播放中断、历史对话、解码器挂起、内存管理以及生成一致性等（提交#4， #6， #7， #8， #12）。
*   **功能新增**：为扩散模型添加了相机交互功能，为MiniMax-H3模型新增了长视频生成能力，并引入了高效的模型间KV缓存传输机制（提交#2， #3， #5）。
*   **代码重构与清理**：重构了扩散模型目录结构以提升可维护性，并移除了不再维护的旧模型支持（提交#10， #13）。
*   **硬件适配与基准测试**：针对昇腾NPU进行了性能优化，并扩展了多模态模型的评估基准（提交#9， #11）。

### 2. 关键变更点及其与项目整体方向的关系
这些提交紧密围绕项目“为每个人提供简单、快速且低成本的全模态模型服务”的核心目标。
*   **性能与成本优化**（#1， #9， #5）：通过NPUGraph、增量KV缓存解码、Mooncake KV传输等技术，直接响应了“快速”和“低成本”的目标，旨在降低推理延迟与资源消耗。
*   **功能与稳定性增强**（#2， #3， #4， #6， #7， #8， #12）：新增的多模态交互与生成能力（相机交互、长视频）巩固了“全模态”定位。一系列关键Bug修复显著提升了生产环境下的可靠性与用户体验，是“简单”可用的基础。
*   **代码质量与演进**（#10， #13）：重构和清理工作维护了代码库的健康发展，移除过时模块有助于项目聚焦，确保长期可维护性，间接支持了项目的可持续发展。

### 3. 对项目的影响和潜在意义
*   **提升了平台成熟度与实用性**：大量Bug修复使得现有功能在实际部署中更加稳定可靠，降低了用户使用门槛。
*   **拓展了模型能力边界**：新增的流式生成、交互和长视频能力，使平台能服务更复杂的AI应用（如交互式世界生成、长内容创作），增强了竞争力。
*   **优化了资源利用率**：性能优化工作有助于降低服务成本，使平台对开发者和企业更具吸引力。
*   **保持了技术先进性**：针对新兴模型（如MOSS-TTS， MiniMax-H3）和硬件（如昇腾NPU）的适配，确保了项目能跟进最新技术趋势。

### 4. 值得关注的技术点
*   **NPUGraph与MOSS-TTS**：利用图优化技术捕获音频编解码器的计算图，可能实现显著的硬件加速，是提升实时音频处理性能的关键。
*   **Mooncake KV传输**（#5）：实现了自回归（AR）模型与扩散模型（DiT）之间高效的键值缓存共享，这对多阶段生成流水线（如文本生成视频）的性能至关重要。
*   **PyAV替代ffmpeg子进程**（#7）：通过使用纯Python解码库，避免了外部进程管理的复杂性和潜在挂起问题，提高了视频处理模块的健壮性。
*   **增量KV缓存解码**（#9）：针对音频模型的深度转换器优化，减少了内存占用和计算量，是针对特定模型结构的精细化性能调优。

### 5. 对项目发展的影响
这些提交标志着项目在从“功能实现”向“工程化成熟与性能优化”阶段迈进。
*   **巩固核心优势**：性能优化与硬件适配进一步夯实了vLLM生态在高效推理方面的基础优势。
*   **构建完善生态**：通过修复边缘情况、新增实用功能，使平台能更好地支撑开发者构建复杂的全模态应用，从而吸引更多用户和贡献者。
*   **明确演进方向**：重构和清理旧模块表明项目正积极管理技术债务，为引入更新、更强大的模型和架构扫清障碍。
总体而言，这批提交使vllm-omni作为一个全模态模型服务平台，变得更加强健、高效和易用，有力地支持了其“服务所有人”的长期愿景。

## 详细提交记录

### [ae3880f](https://github.com/vllm-project/vllm-omni/commit/ae3880f0e39df4ba7376481ae78d9269fc42e09c)

- **作者**: Wallbreazzz
- **时间**: 2026-09-20T22:38:23Z
- **提交信息**: [Performance] Capture MOSS-TTS codec streaming decode with NPUGraph (#7280)

Signed-off-by: Wallbreazzz <110282866+Wallbreazzz@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [e36babd](https://github.com/vllm-project/vllm-omni/commit/e36babd48ff2eee3443c16166b1a6890e62e44e0)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-09-20T16:19:41Z
- **提交信息**: [Core][Diffusion] Camera interaction for diffusion streaming generation (LingBot World 2 as example) (#7198)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>

### [139a47a](https://github.com/vllm-project/vllm-omni/commit/139a47a578e01eb7cd4a0c3d35a02eba4b4ded6a)

- **作者**: 汪志鹏
- **时间**: 2026-09-20T15:44:33Z
- **提交信息**: [Model] Add MiniMax-H3 long-video latent continuation with driving audio (#7838)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [16734bb](https://github.com/vllm-project/vllm-omni/commit/16734bbdf3850bc7407bafb3484de613a73efd84)

- **作者**: DanaerLee
- **时间**: 2026-09-20T15:23:53Z
- **提交信息**: [Bugfix] Route text-only chat as per-request comprehension in HunyuanImage3 AR sampler (#6111)

Signed-off-by: MrlixiangWE <mrdanaer@gmail.com>
Co-authored-by: zijianc2 <157244773+zijianc2@users.noreply.github.com>

### [102ba71](https://github.com/vllm-project/vllm-omni/commit/102ba716bf814cfeb77624157e14ad73f49c658b)

- **作者**: Wu JIAZHEN
- **时间**: 2026-09-20T14:44:55Z
- **提交信息**: [Feat] Add native Mooncake KV transfer from AR to DiT (#7166)

Signed-off-by: asukaqaq-s <1311722138@qq.com>
Signed-off-by: Acerak01-fy <wfy2003324@163.com>
Co-authored-by: Acerak01-fy <wfy2003324@163.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [2d0b03f](https://github.com/vllm-project/vllm-omni/commit/2d0b03f717e96fc8030859dcadbf96e7f8ea8145)

- **作者**: psv666
- **时间**: 2026-09-20T14:42:17Z
- **提交信息**: [Bugfix] Fix Qwen3-Omni realtime playback interruption and conversation history (#7791)

Signed-off-by: psv666 <2693925048@qq.com>

### [d3396fc](https://github.com/vllm-project/vllm-omni/commit/d3396fc5fb16c9b4de6c8fb9ed0f67cc732b7af2)

- **作者**: RyanYun09
- **时间**: 2026-09-20T14:37:09Z
- **提交信息**: # [Bugfix] Replace ffmpeg subprocess with PyAV to avoid HEVC decoder hang (#7364) (#7504)

Signed-off-by: RyanYun09 <318555231+RyanYun09@users.noreply.github.com>

### [4d87778](https://github.com/vllm-project/vllm-omni/commit/4d877780d38cbf93e273aef73e99a100d38e2768)

- **作者**: Canlin Guo
- **时间**: 2026-09-20T12:36:52Z
- **提交信息**: [Bugfix] Avoid waveform-list GC scans and release completed MOSS batches (#7885)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>

### [23f4126](https://github.com/vllm-project/vllm-omni/commit/23f41264456684c793283502f811aab7dcda2c88)

- **作者**: jingchengtian
- **时间**: 2026-09-20T10:34:25Z
- **提交信息**: [Hardware][Ascend] Use incremental KV-cache decode for MOSS-TTS depth transformer (#6967)

Signed-off-by: jingchengtian <tjc1995@126.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [d02681b](https://github.com/vllm-project/vllm-omni/commit/d02681bf01a5d9d1608570aff958dfb15e2bbf8e)

- **作者**: Alicia
- **时间**: 2026-09-20T10:19:24Z
- **提交信息**: [Refactor][Diffusion] Move single-model layers into their model directories (#5908)

Signed-off-by: congw729 <115451386+congw729@users.noreply.github.com>
Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [9f55213](https://github.com/vllm-project/vllm-omni/commit/9f5521351e4471d6538e74ca66cb63cde23b9140)

- **作者**: amy-why-3459
- **时间**: 2026-09-20T09:15:53Z
- **提交信息**: [Benchmark][MiniCPM-o] Port Video-MME dataset support to Omni bench s… (#6987)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [ea62f86](https://github.com/vllm-project/vllm-omni/commit/ea62f86718a4e0e0004a3daf18b033b940c0ada0)

- **作者**: tlysanhuo
- **时间**: 2026-09-20T08:24:38Z
- **提交信息**: [Bugfix] Honor request-level seed in VoxCPM2 CFM noise (#7866)

Signed-off-by: tly <2200895168@qq.com>

### [6a03e45](https://github.com/vllm-project/vllm-omni/commit/6a03e45c340a60553884432ff4fc4a31a6219d55)

- **作者**: wangyu
- **时间**: 2026-09-20T07:28:29Z
- **提交信息**: [Misc] Remove Dynin-Omni and dots.tts support (#7655)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

---
