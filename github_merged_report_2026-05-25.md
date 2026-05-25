# GitHub Stars 合并报告 - 2026-05-25

**合并日期**: 2026-05-26
**监控日期**: 2026-05-25
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


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1946
- **最后更新**: 2026-05-25T10:48:29Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bin Jia

## AI分析总结

好的，这是对仓库 `ByteDance-Seed/VeOmni` 昨日提交记录的分析总结。

### 提交分析总结

**提交记录**: `[199e912] [ckpt, lora] feat: Save lora ckpt only and add omni-infer with lora (#785)`

---

#### 1. 主要更新类型

- **功能新增 (Feature)**：本次提交属于功能新增，主要围绕模型微调（LoRA）的实用性和推理部署能力进行增强。

#### 2. 关键变更点及其与项目整体方向的关系

- **变更点 1: 支持仅保存 LoRA 检查点 (Save lora ckpt only)**
  - **关系**: VeOmni 的目标是“扩展任意模态模型训练”。LoRA (Low-Rank Adaptation) 是一种高效的微调技术，常用于大模型。仅保存 LoRA 权重（而非完整模型）可以显著减少存储开销和模型分发的成本。这直接提升了项目在模型微调场景下的实用性和效率。
- **变更点 2: 为 omni-infer 添加 LoRA 支持 (add omni-infer with lora)**
  - **关系**: `omni-infer` 很可能是 VeOmni 提供的推理服务或工具。将 LoRA 权重与推理流程结合，意味着用户微调后的模型可以无缝地用于实际部署和推理。这打通了从“训练/微调”到“推理/应用”的完整链路，是项目走向成熟和可落地的关键一步。

#### 3. 对项目的影响和潜在意义

- **提升微调效率**: 允许仅保存 LoRA 权重，使得用户可以更灵活、更经济地管理和迭代多个微调版本，尤其适合资源受限或需要频繁实验的场景。
- **完善工具链闭环**: 将 LoRA 集成到 `omni-infer` 中，意味着 VeOmni 不再只是一个训练框架，而是一个覆盖“训练-微调-推理”全流程的平台。这极大地增强了项目的吸引力和竞争力。
- **降低使用门槛**: 用户无需保存和加载庞大的完整模型，即可进行高效的微调和部署，降低了使用 VeOmni 进行多模态模型定制化应用的门槛。

#### 4. 值得关注的技术点

- **LoRA 权重的存储与加载**: 如何高效地仅保存和加载 LoRA 权重，并与基础模型权重进行合并或分离，是技术实现的关键。这涉及到对模型结构的深入理解和序列化策略的优化。
- **`omni-infer` 的架构**: 该提交表明 `omni-infer` 是一个可扩展的推理组件，能够动态集成不同的模型适配器（如 LoRA）。其架构设计值得关注，因为它决定了未来支持更多微调技术（如 Adapter, Prefix Tuning）的难易程度。

#### 5. 基于项目背景，这些提交如何影响项目发展

- **强化核心定位**: VeOmni 的定位是“以模型为中心的分布式配方动物园”。本次提交通过支持高效的 LoRA 微调配方，并使其能直接用于推理，丰富了“配方”的实用性和完整性。它证明了 VeOmni 不仅关注从头训练，也关注高效的模型定制化。
- **推动从研究到应用**: 论文和文档是项目的理论基础，而本次提交则是一个重要的工程实践。它表明项目正在从学术研究向工业级应用迈进，致力于解决用户在实际部署中遇到的存储、效率和易用性问题。
- **吸引更广泛的用户群体**: 支持 LoRA 微调和推理，会吸引更多希望基于现有大模型进行快速、低成本定制化开发的开发者和研究者，而不仅仅是进行大规模预训练的研究团队。这有助于扩大项目的社区影响力。

## 详细提交记录

### [199e912](https://github.com/ByteDance-Seed/VeOmni/commit/199e91215fc2e9ef6c50ea8f2c5781d34f35118b)

- **作者**: Bin Jia
- **时间**: 2026-05-25T09:32:41Z
- **提交信息**: [ckpt, lora] feat: Save lora ckpt only and add omni-infer with lora (#785)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2292
- **最后更新**: 2026-05-25T13:46:17Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Yang Yong (雍洋), Shiqiao Gu (谷石桥)

## AI分析总结

好的，这是对仓库 `ModelTC/LightX2V` 昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增**：支持 `Seko AR` 模型推理、支持 `drop_tail_invalid_frames` 预处理。
- **性能优化**：KV Cache 环形布局、Triton 算子优化（RoPE、KIVI 反量化）、异步解码、NVFP4 量化。
- **重构**：KV Offload 单缓冲预取设计。

### 2. 关键变更点及其与项目整体方向的关系

- **`[557eb4d]` 支持动画模型预处理丢弃无效帧**:
  - **变更点**: 为动画模型的数据预处理阶段增加 `drop_tail_invalid_frames` 功能，用于丢弃尾部无效帧。
  - **与项目方向关系**: 这是一个针对特定模型（动画类）的实用功能增强，提升了数据处理的灵活性和鲁棒性，符合项目作为通用视频生成推理框架的定位。

- **`[4721f77]` 支持并优化 Seko AR 模型**:
  - **变更点**: 这是本次更新的核心。它完整地引入了对 `Seko` 自回归（AR）模型的支持，并进行了深度优化。
  - **与项目方向关系**: 直接契合项目“轻量级视频生成推理框架”的目标。通过一系列优化，使得原本需要 8x80GB 高端 GPU 的模型，能够在消费级 GPU 上运行，极大地降低了使用门槛，扩展了框架的适用模型生态。

### 3. 对项目的影响和潜在意义

- **降低硬件门槛**: 这是最直接的影响。`Seko AR` 模型的优化使得普通用户和开发者也能在单卡或低显存环境下尝试和部署先进的视频生成模型，有望吸引更广泛的用户群体。
- **提升推理效率**: 环形 KV Cache、Triton 算子、异步解码等优化不仅针对 `Seko`，其设计思路和代码实现（如 KV Cache 管理、算子优化）可以复用到框架内其他模型，提升整体推理性能。
- **增强框架竞争力**: 支持并高效运行 `Seko` 这样的前沿模型，使 `LightX2V` 在视频生成推理框架中更具竞争力，尤其是在消费级硬件部署场景下。

### 4. 值得关注的技术点

- **环形 KV Cache (Ring Layout)**: 这是一种巧妙的内存管理技巧。在滚动窗口更新时，通过逻辑重映射而非物理拷贝数据，显著减少了显存带宽消耗和延迟，是高性能推理的关键。
- **Triton 算子融合**: 将 `RoPE` 位置编码和 `KIVI` 反量化（`unpack + dequant`）等操作编写为 Triton 内核，实现了算子融合，减少了 kernel launch 开销和中间显存读写。
- **异步自回归解码**: 通过重叠计算和通信/内存操作，隐藏了解码过程中的延迟，提高了 GPU 利用率。
- **NVFP4 量化支持**: 引入了 `LongLive2` 的 NVFP4 量化方案，这是一种更激进的低精度量化（4-bit），能大幅降低显存占用，同时通过并行反量化来缓解精度损失带来的性能问题。

### 5. 基于项目背景，这些提交如何影响项目发展

- **从“可用”到“好用”**: 项目 README 强调“轻量级”和“推理框架”。之前的版本可能更侧重于支持多种模型。本次更新，特别是 `Seko AR` 的优化，标志着项目重心从“支持模型”转向“优化模型以使其在有限资源下高效运行”，这是从“可用”迈向“好用”的关键一步。
- **巩固技术壁垒**: 通过实现环形 KV Cache、Triton 算子等底层优化，`LightX2V` 在推理引擎的核心技术上建立了自己的优势，而不仅仅是模型加载器。这有助于形成技术壁垒，区别于其他仅做模型集成的项目。
- **吸引社区贡献**: 成功将高端模型“平民化”是一个很好的宣传点。这能吸引更多对视频生成感兴趣但受限于硬件的开发者加入社区，贡献代码、反馈问题，形成良性循环，加速项目发展。

## 详细提交记录

### [557eb4d](https://github.com/ModelTC/LightX2V/commit/557eb4d72b6747e4cd39ea76c3e3723160ae97bb)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-05-25T08:39:57Z
- **提交信息**: Support drop_tail_invalid_frames for animate model preprocess (#1092)

### [4721f77](https://github.com/ModelTC/LightX2V/commit/4721f77b174ed8ba55f8f5e3fff6bc409956b0eb)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-05-25T08:26:35Z
- **提交信息**: Add support and optimizations for Seko AR model (#1091)

## Summary

This PR adds and optimizes KV cache support for Seko autoregressive
inference, with a focus on making the Seko AR model practical on
consumer GPUs.

Key changes include:

- Add support for Seko autoregressive model inference, mainly through
the step-aware KV cache architecture.
- Support sequence-parallel inference for the Seko AR path, including
SP-aware cache indexing and RoPE position handling.
- Refactor KV cache storage into a ring layout to avoid unnecessary
copies during rolling-window updates. Instead of physically shifting
`[sink | chunk1 | chunk2 | chunk3]` into `[sink | chunk2 | chunk3 |
chunk4]`, the cache can now keep a ring layout such as `[sink | chunk4 |
chunk2 | chunk3]`, reducing memory movement.
- Optimize RoPE in the Seko AR path with a Triton kernel, including
support for cache-range RoPE and sequence-parallel spatial position
mapping.
- Optimize KIVI KV cache dequantization by fusing unpack and dequant
into a Triton kernel.
- Add asynchronous autoregressive decode support to overlap and hide
decode latency.
- Add LongLive2 NVFP4 KV cache quantization support, including parallel
dequantization across multiple chunks.
- Refactor KV offload with a simpler single-buffer prefetch design,
improving readability and inference speed.
- Together, these optimizations make Seko AR inference practical on
consumer-grade GPUs, while the original reference setup typically
targets an 8-GPU environment with 80 GB of memory per GPU.

---------

Co-authored-by: root <root@pt-d7801c16d4cc44d2a1a4303af37df0d5-worker-0.pt-d7801c16d4cc44d2a1a4303af37df0d5.ns-devsft-3460edd0.svc.cluster.local>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2092
- **最后更新**: 2026-05-25T09:39:23Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 昨日更新要点分析

**提交记录:** `[2b5596b] Update Self-Forcing and Ernie Image (#490)`

---

#### 1. 主要更新类型
- **功能新增/增强**：本次提交主要涉及对现有功能的更新和增强，具体是“Self-Forcing”和“Ernie Image”两个模块。

#### 2. 关键变更点及其与项目整体方向的关系
- **更新 Self-Forcing**：Self-Forcing 是一种视频生成技术，用于提升生成视频的时序一致性和质量。此更新可能涉及算法优化、参数调整或支持新的模型架构。
- **更新 Ernie Image**：Ernie Image 可能指的是与百度文心（ERNIE）大模型相关的图像生成或理解能力。此更新可能增强了项目与文心模型的集成，或优化了图像到视频的生成流程。
- **与项目方向的关系**：VideoX-Fun 的核心目标是提供高质量、易用的视频生成工具。这两个更新直接服务于这一目标：
    - **Self-Forcing** 的优化直接提升了视频生成的**核心质量**（如连贯性、流畅度）。
    - **Ernie Image** 的更新则扩展了项目的**多模态能力**，特别是与中文大模型生态的融合，增强了从图像生成视频（Image-to-Video）的灵活性和效果。

#### 3. 对项目的影响和潜在意义
- **提升生成质量**：Self-Forcing 的改进将直接使用户生成的视频在时序上更稳定、更自然，减少闪烁和抖动。
- **增强生态兼容性**：更新 Ernie Image 表明项目正在积极拥抱国内主流AI生态（如百度文心），这有助于吸引更广泛的用户群体，并可能解锁更多基于文心模型的创意工作流。
- **保持技术领先**：持续优化核心算法和集成前沿模型，有助于 VideoX-Fun 在快速发展的AI视频生成领域保持竞争力。

#### 4. 值得关注的技术点
- **Self-Forcing 机制**：这是一种在扩散模型或自回归模型中用于改善长视频生成一致性的技术。本次更新可能涉及新的实现方式或超参数调优。
- **Ernie 模型集成**：需要关注更新后，项目如何调用文心模型（API或本地部署），以及是否支持文心模型特有的功能（如中文理解、风格控制等）。

#### 5. 基于项目背景，这些提交如何影响项目发展
- **巩固核心优势**：VideoX-Fun 定位为“Fun”（有趣、易用）的视频生成工具。通过优化 Self-Forcing，项目在**生成质量**这一核心维度上持续进步，这是吸引和留住用户的基础。
- **拓展应用场景**：与 Ernie Image 的深度结合，使得项目能更好地服务于中文用户，并可能衍生出更多结合文心大模型能力的特色功能（例如，根据中文描述生成视频，或对视频内容进行中文语义理解）。
- **强化社区与生态**：README 中提供了 Hugging Face 空间和多种语言文档，表明项目注重社区和国际化。本次更新进一步强化了与国内AI生态的连接，有助于构建一个更开放、多元的开发者社区。

**总结：** 本次提交是一次**功能增强型**更新，通过优化核心算法（Self-Forcing）和集成前沿模型（Ernie Image），在提升视频生成质量的同时，拓展了项目与国内AI生态的兼容性，对项目的长期发展和用户吸引力具有积极意义。

## 详细提交记录

### [2b5596b](https://github.com/aigc-apps/VideoX-Fun/commit/2b5596b8e68ba920091c13990aa620b8fb77c82d)

- **作者**: Bubbliiiing
- **时间**: 2026-05-25T09:39:17Z
- **提交信息**: Update Self-Forcing and Ernie Image (#490)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5674
- **最后更新**: 2026-05-25T19:17:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3512
- **最后更新**: 2026-05-25T08:52:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33697
- **最后更新**: 2026-05-25T18:49:37Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 405
- **最后更新**: 2026-05-25T05:11:57Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12471
- **最后更新**: 2026-05-25T20:31:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 28242
- **最后更新**: 2026-05-25T22:07:13Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 14
- **主要提交者**: Makcum888e, Ziang Li, Xiaoyu Zhang

## AI分析总结

好的，以下是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结：

### 1. 主要更新类型

-   **功能新增**：新增了 `--dsa-topk-backend` 参数、FlashInfer 与 PyTorch topk 集成、扩散模型的 CFG 门控、NPU 平台的扩散模型分阶段支持、实验性 Rust HTTP 路由器。
-   **性能优化**：EAGLE 推测解码跳过全词汇 softmax、Qwen3.5 模型 topkGating 内核优化、在 CUDA Graph 填充中清零 `req_pool_indices` 以减少填充开销。
-   **重构**：HiCache 栈调度重构为策略模式、推测命名从“始终开启规则”改为“按技能懒加载”。
-   **文档更新**：HiSparse 用户指南更新、MXFP4 量化文档新增。
-   **Bug 修复**：修复了 Blackwell 架构上 FlashInfer allreduce 融合未生效的问题。
-   **CI/DevOps**：启用了 EPD 架构的 CI、对齐了 dsv4 分解测试的分数阈值、为实验性 sgl-router 添加了夜间 Docker 构建工作流、修复了 Docker 构建中 Cargo.lock 生成问题。
-   **依赖/版本更新**：Mooncake 版本升级至 0.3.11.post1、为 NPU 平台添加了 torchaudio 依赖。

### 2. 关键变更点及其与项目整体方向的关系

-   **强化 RL 与推理后端灵活性**：`--dsa-topk-backend` 的引入允许用户选择 FlashInfer 或 PyTorch 的 topk 实现，这与项目支持多种推理后端（如 FlashInfer, TRTLLM）和强化学习（RL）场景的目标一致。
-   **推进扩散模型支持**：多项提交（CFG 门控、FP32 LayerNorm 缓存、NPU 分阶段支持、默认 NVFP4 后端）表明项目正在系统性地增强对扩散模型（如 Stable Diffusion）的支持，覆盖了精度、性能、硬件适配等多个维度。
-   **优化推测解码性能**：跳过全词汇 softmax 的优化直接提升了 EAGLE 等推测解码技术的效率，这是提升 LLM 推理吞吐量的关键路径。
-   **架构重构与模块化**：HiCache 调度策略化、推测命名懒加载等重构，体现了项目在代码架构上追求更好的可扩展性和可维护性，为未来更复杂的调度和功能组合打下基础。
-   **引入实验性 Rust 路由器**：`sgl-router` 的引入是一个重大架构变化，旨在用高性能的 Rust 实现替代现有路由组件，以支持更大的工作池和更复杂的负载均衡，这直接服务于项目作为高性能推理系统的核心定位。

### 3. 对项目的影响和潜在意义

-   **提升推理性能与效率**：多项性能优化（推测解码、内核优化、填充减少）将直接降低延迟、提高吞吐量，使 SGLang 在处理高并发请求时更具竞争力。
-   **扩展模型与硬件支持**：对扩散模型和 NPU 硬件的持续投入，拓宽了项目的应用场景，使其不仅能服务于 LLM，也能服务于多模态生成任务，并适配更多国产化硬件。
-   **增强系统鲁棒性与可扩展性**：重构和模块化工作降低了未来功能迭代的复杂性。实验性 Rust 路由器的引入，为构建更大规模、更稳定的推理集群提供了技术储备。
-   **改善开发者与用户体验**：新增的文档（HiSparse, MXFP4）和 CI 改进（EPD CI, 夜间构建）降低了新用户的入门门槛，并提高了开发流程的可靠性。

### 4. 值得关注的技术点

-   **`--dsa-topk-backend` 参数**：这是一个重要的抽象层，允许用户在不同硬件或精度需求下，灵活切换 topk 计算后端，体现了“可插拔”的设计思想。
-   **扩散模型的 CFG 门控**：这是一种在去噪过程中动态控制条件信号强度的技术，对于提升生成质量和多样性至关重要。
-   **EAGLE 推测解码的 softmax 跳过**：当 `topk==1` 时，无需计算完整的 softmax，这是一个非常巧妙且有效的性能优化技巧。
-   **HiCache 策略模式重构**：将调度逻辑从“栈”抽象为“策略”，为未来实现更复杂的缓存替换算法（如 LRU, LFU 或基于学习的策略）提供了清晰的接口。
-   **实验性 Rust HTTP 路由器**：使用 Rust 重写关键网络组件，是追求极致性能和稳定性的典型做法，值得关注其后续的集成效果和性能对比。

### 5. 基于项目背景，这些提交如何影响项目发展

结合 README 中 SGLang 作为“快速、高效、灵活的 LLM 推理和服务框架”的定位，昨日的更新清晰地展示了项目在以下三个核心方向上的持续演进：

1.  **追求极致性能**：通过优化推测解码、内核和内存管理，SGLang 正在不断巩固其在高性能推理领域的领先地位。
2.  **扩展能力边界**：通过强化对扩散模型、NPU 等新模型和硬件的支持，SGLang 正从一个纯粹的 LLM 推理框架，向一个更通用的多模态、多硬件推理平台演进。
3.  **提升系统成熟度**：通过架构重构、引入 Rust 组件、改进 CI/CD 流程和文档

## 详细提交记录

### [2b9dd9c](https://github.com/sgl-project/sglang/commit/2b9dd9c8b339bb397a3bbb56ff4bc330627d1033)

- **作者**: Ziang Li
- **时间**: 2026-05-25T20:08:03Z
- **提交信息**: [FlashInfer v0.6.10] [RL] [DSv32] [GLM-5] Add `--dsa-topk-backend` and integrate FlashInfer and pytorch topk (#22851)

### [b13d3d1](https://github.com/sgl-project/sglang/commit/b13d3d18c68c5da56936b1b9aee9dcf467b65b91)

- **作者**: Ke Bao
- **时间**: 2026-05-25T16:06:17Z
- **提交信息**: Refactor HiCache stack dispatch into strategies (#26295)

### [2aa6995](https://github.com/sgl-project/sglang/commit/2aa69953085de5963a9542ec7561b6f835402b8e)

- **作者**: Shangming Cai
- **时间**: 2026-05-25T15:52:58Z
- **提交信息**: [CI] Enable EPD CI for EPD architecture enhancements (#26281)

### [121cc09](https://github.com/sgl-project/sglang/commit/121cc094054f2fae39ca8c22e267c2edb63904d6)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-25T14:57:09Z
- **提交信息**: [diffusion] Add CFG gating for denoising (#25848)

Co-authored-by: BBuf <bbuf@example.com>

### [85f9522](https://github.com/sgl-project/sglang/commit/85f9522e364bc543fa29c9b81cb006a476c98144)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-25T14:56:39Z
- **提交信息**: [diffusion] Cache fp32 layernorm params (#25847)

Co-authored-by: BBuf <bbuf@example.com>

### [0801cc0](https://github.com/sgl-project/sglang/commit/0801cc05ed202544e2e5c67d6b0a1d454de54fca)

- **作者**: Makcum888e
- **时间**: 2026-05-25T10:51:25Z
- **提交信息**: [Diffusion][NPU] Disaggregation diffusion stages support for NPU (#25895)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [3e67398](https://github.com/sgl-project/sglang/commit/3e67398a96b341402eea7845de9a6221b6af5ca7)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-25T10:29:05Z
- **提交信息**: Zero `req_pool_indices` padding in cuda-graph populate (#26292)

### [533ef41](https://github.com/sgl-project/sglang/commit/533ef4111283f191b6eee1ccd1539ce4d939f2a8)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-25T10:14:06Z
- **提交信息**: [Diffusion] Default NVFP4 backend to FlashInfer TRTLLM (#25523)

### [c05756d](https://github.com/sgl-project/sglang/commit/c05756da7a07c99d34aee64a189e461193b91a9e)

- **作者**: Mick
- **时间**: 2026-05-25T10:07:15Z
- **提交信息**: [SRT] fix flashInfer allreduce fusion not used on blackwell (#26197)

### [a4db563](https://github.com/sgl-project/sglang/commit/a4db563c87d7a0c95c50290433ad8493b3a8fb97)

- **作者**: Zhangheng
- **时间**: 2026-05-25T09:54:55Z
- **提交信息**: [hisparse]: update user guide (#26249)

Co-authored-by: 晟海 <huangtingwei.htw@antgroup.com>

### [bc8d64b](https://github.com/sgl-project/sglang/commit/bc8d64bf36c687580ea9d4dc17fed8bcd8e62395)

- **作者**: Shangming Cai
- **时间**: 2026-05-25T09:48:45Z
- **提交信息**: [CI] Align score threshold in dsv4 disaggregation test (#26268)

### [a77449f](https://github.com/sgl-project/sglang/commit/a77449f86d56f7c4b3420d4392e123286b1179bd)

- **作者**: Qiaolin Yu
- **时间**: 2026-05-25T09:06:48Z
- **提交信息**: [perf][spec decoding] Skip full-vocab softmax in EAGLE draft when topk == 1 (#26235)

### [7c04b9e](https://github.com/sgl-project/sglang/commit/7c04b9e9427aa584ae460d4487dcc775d20e89e9)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-25T08:54:47Z
- **提交信息**: fix(docker): generate Cargo.lock in chef stage for sgl-router build (#26279)

Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>

### [7f2829a](https://github.com/sgl-project/sglang/commit/7f2829af39357d317036e9576697a6367a827699)

- **作者**: Shangming Cai
- **时间**: 2026-05-25T08:51:03Z
- **提交信息**: chore: bump mooncake version to 0.3.11.post1 (#25989)

### [0942011](https://github.com/sgl-project/sglang/commit/0942011665e003f954d85bbafa354b2470f64af2)

- **作者**: xdtbynd
- **时间**: 2026-05-25T08:30:12Z
- **提交信息**: [NPU] Add torchaudio dependency for NPU platform (#26267)

### [81704ad](https://github.com/sgl-project/sglang/commit/81704ad602855ebf5b317b41b221f29e3bec496e)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-25T08:19:07Z
- **提交信息**: ci: add nightly Docker workflow for experimental sgl-router (#26273)

Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>

### [e27d4fb](https://github.com/sgl-project/sglang/commit/e27d4fb70f33d6a86533a5dc3e14114c480b4d2f)

- **作者**: Jincong Chen
- **时间**: 2026-05-25T08:08:21Z
- **提交信息**: [Perf][Qwen3.5] Add case 512 to topkGatingSoftmaxKernelLauncher, (#25775)

### [b0cf01e](https://github.com/sgl-project/sglang/commit/b0cf01eb85c41dd1c14a1a1973a6ae575852bf98)

- **作者**: fzyzcjy
- **时间**: 2026-05-25T07:58:29Z
- **提交信息**: Lazy-load speculative-naming via skill instead of always-on rule (#26270)

### [6e8fe17](https://github.com/sgl-project/sglang/commit/6e8fe176be9cc0dbbebee3e87a841359f4fa5daa)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-25T07:34:05Z
- **提交信息**: sgl-router: experimental Rust HTTP router for SGLang worker pools (#25851)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [aae04b1](https://github.com/sgl-project/sglang/commit/aae04b12416443822722840067a4c74db40e692c)

- **作者**: Junlin Wu
- **时间**: 2026-05-25T07:24:30Z
- **提交信息**: :memo: docs(diffusion): add MXFP4 quantization docs (#25904)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1181
- **最后更新**: 2026-05-25T15:30:45Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，这是对 `vipshop/cache-dit` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **重构 (Refactoring)**: 两项提交均属于代码重构。
*   **功能废弃 (Deprecation)**: 明确标记并移除了一个旧的后端支持。

### 2. 关键变更点及其与项目整体方向的关系

*   **`parallel: deprecated native diffusers backend`**:
    *   **变更**: 废弃并移除了 `Native_Diffusers` 后端。
    *   **关系**: 项目目标是构建一个“PyTorch原生”的推理引擎，专注于缓存、并行化和量化。`Native_Diffusers` 可能是一个早期或外部集成的后端，其实现方式与项目“原生”和“高性能”的核心理念不符。移除它意味着项目正在精简架构，聚焦于自己更高效、更可控的实现。

*   **`ray: refactor ray wrapper impl`**:
    *   **变更**: 重构了与 `Ray` 框架集成的包装器实现。
    *   **关系**: `Ray` 是一个流行的分布式计算框架，常用于大规模并行推理。重构 `Ray` 包装器，表明项目正在优化其并行化能力，使其能更好地与 `Ray` 集成，从而支持更大规模的模型部署和更高效的资源利用。这与项目“并行化”的核心目标高度一致。

### 3. 对项目的影响和潜在意义

*   **影响**:
    *   **向后兼容性**: 废弃 `Native_Diffusers` 后端是一个破坏性变更，依赖此后端的用户需要迁移到新的后端。
    *   **代码质量**: 重构 `Ray` 包装器通常会带来更清晰、更健壮、更易于维护的代码。
    *   **性能**: 移除冗余后端和优化 `Ray` 集成，有望提升整体并行推理的性能和稳定性。

*   **潜在意义**:
    *   **技术债务清理**: 主动废弃旧后端是清理技术债务的积极信号，表明项目正朝着更统一、更高效的技术栈演进。
    *   **生态聚焦**: 项目正在明确其技术生态，选择与 `Ray` 等主流框架深度集成，而不是维护多个可能功能重叠的后端。

### 4. 值得关注的技术点

*   **后端策略**: 项目如何定义和管理其“后端”架构。从“原生”到“废弃”，体现了项目对技术路线的取舍。
*   **`Ray` 集成深度**: 重构后的 `Ray` 包装器具体优化了什么？是资源调度、任务分发还是容错机制？这直接关系到项目在分布式环境下的实际表现。
*   **并行化实现**: 项目内部是如何实现并行化的？是模型并行、数据并行还是流水线并行？`Ray` 的集成方式能揭示其并行策略。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **强化“PyTorch原生”定位**: 废弃 `Native_Diffusers` 后端，虽然名字带有“Native”，但很可能其实现并非完全基于PyTorch的优化路径。移除它，有助于项目团队将所有精力集中在基于PyTorch的高效实现上，强化其“PyTorch-native”的品牌承诺。
*   **加速“并行化”能力建设**: 重构 `Ray` 包装器是项目在“并行化”这一核心能力上的重要投入。这表明项目不仅仅满足于单卡推理，而是致力于解决大规模、分布式场景下的Diffusion Transformer推理问题，这与项目README中强调的“Parallelism”完全吻合。
*   **走向成熟**: 主动进行代码重构和功能废弃，是项目从快速原型阶段走向成熟、稳定阶段的标志。这有助于提升代码的可维护性、可扩展性和长期可靠性，对吸引更多生产环境用户至关重要。

**总结**: 昨日的更新是一次“瘦身”和“强基”操作。项目通过废弃旧后端来精简架构，同时通过重构核心并行化组件来夯实基础。这清晰地表明 `cache-dit` 正在朝着一个更专注、更高效、更易于大规模部署的PyTorch原生推理引擎方向演进。

## 详细提交记录

### [bcbaa7b](https://github.com/vipshop/cache-dit/commit/bcbaa7b336b920ce91d7573f975d52267dd6f2b8)

- **作者**: DefTruth
- **时间**: 2026-05-25T13:06:46Z
- **提交信息**: parallel: deprecated native diffusers backend (#1017)

* parallel: deprecated Native_Diffusers backend

* parallel: deprecated Native_Diffusers backend

### [1e22079](https://github.com/vipshop/cache-dit/commit/1e22079fbff51ef5d930bcfe353d4d75f3060863)

- **作者**: DefTruth
- **时间**: 2026-05-25T12:19:47Z
- **提交信息**: ray: refactor ray wrapper impl (#1016)

* ray: refactor ray wrapper impl

* ray: refactor ray wrapper impl

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 80991
- **最后更新**: 2026-05-25T21:11:46Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Zhewen Li, Jee Jee Li, Nicolò Lucchesi

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 昨日更新要点分析

1.  **主要更新类型**
    *   **代码重构/清理**：移除了一个旧的、不再需要的 Kernel（`NormGateLinear`）。
    *   **测试/调试改进**：优化了 PD（推测解码）测试的日志输出，使其在成功时也打印精度值。
    *   **Bug 修复**：修复了 Mooncake KV Connector 在处理抢占后完成请求时的一个问题。

2.  **关键变更点及其与项目整体方向的关系**
    *   **移除 `NormGateLinear` Kernel**：这是一个代码清理操作，移除了一个可能已被新实现取代或不再使用的内核。这符合项目“易用、快速、廉价”的目标，通过精简代码库来降低维护成本和潜在的复杂性。
    *   **改进 PD 测试日志**：在成功时也打印精度值，可以更早地发现精度退化问题，有助于提升模型服务的**质量**和**可靠性**，这与提供“廉价且快速”但同样准确的 LLM 服务目标一致。
    *   **修复 Mooncake KV Connector 抢占后处理**：Mooncake 是一个分布式 KV 缓存管理框架，用于跨多个 GPU 节点共享 KV 缓存，以提升推理效率。修复抢占后的完成逻辑，确保了在资源竞争（抢占）场景下，分布式推理的**正确性**和**稳定性**，这对于实现“快速”和“廉价”（通过高效利用资源）至关重要。

3.  **对项目的影响和潜在意义**
    *   **代码库健康度**：移除旧代码是保持项目长期健康发展的必要步骤，减少了技术债务。
    *   **测试质量**：改进的测试日志有助于开发者更快地定位精度问题，提升开发效率和模型质量。
    *   **分布式推理稳定性**：修复 Mooncake 的 Bug 直接提升了 vLLM 在分布式、多租户环境下的鲁棒性。这对于 vLLM 作为生产级推理引擎至关重要，尤其是在需要处理高并发和资源动态调度的场景下。

4.  **值得关注的技术点**
    *   **`NormGateLinear` Kernel**：这个 Kernel 的具体作用值得关注。它的移除可能意味着 vLLM 在 MoE（混合专家）模型的实现上有了更优的替代方案，或者该 Kernel 的功能已被合并到其他更通用的实现中。
    *   **Mooncake KV Connector**：这是一个关键组件，用于实现跨节点的 KV 缓存共享。这次修复表明 vLLM 正在积极完善其分布式推理能力，特别是针对复杂的调度和抢占场景。这是实现大规模、低成本 LLM 服务的关键技术。

5.  **基于项目背景，这些提交如何影响项目发展**
    *   **“Easy”**：代码清理和测试改进间接降低了新贡献者理解和贡献代码的门槛。
    *   **“Fast”**：修复 Mooncake 的 Bug 确保了在分布式环境下，因抢占导致的性能下降或错误能被正确处理，从而维持了推理速度。移除旧 Kernel 也可能为未来更快的实现铺平道路。
    *   **“Cheap”**：Mooncake 的修复直接关系到资源利用效率。在抢占场景下正确完成请求，意味着宝贵的 GPU 资源没有被浪费，从而降低了每 token 的服务成本。测试改进则有助于防止因精度问题导致的模型退化，避免了潜在的重新训练或调试成本。

**总结：** 昨日的更新侧重于**内部质量**和**分布式稳定性**。虽然看起来是小改动，但修复 Mooncake 的 Bug 和清理旧代码，对于 vLLM 实现其“为所有人提供易用、快速、廉价的 LLM 服务”的愿景，尤其是在大规模生产环境中，具有重要的实际意义。

## 详细提交记录

### [d400445](https://github.com/vllm-project/vllm/commit/d4004455d2357985830af10e432709b42c820455)

- **作者**: Jee Jee Li
- **时间**: 2026-05-25T09:49:19Z
- **提交信息**: [Kernel] Remove NormGateLinear (#43554)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [716d529](https://github.com/vllm-project/vllm/commit/716d5294e6db16fe1d8afb09a061694cf4602d7e)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-05-25T09:10:01Z
- **提交信息**: [Misc] Print accuracy value for PD tests even on success  (#43583)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [873758c](https://github.com/vllm-project/vllm/commit/873758c13a64742e2a0247e0f2c62cadf027dd2b)

- **作者**: Zhewen Li
- **时间**: 2026-05-25T08:58:38Z
- **提交信息**: [KV Connector] Handle Mooncake finish after preemption (#43281)

Signed-off-by: Zhewen Li <zhewenli@inferact.ai>
Co-authored-by: Zhewen Li <zhewenli@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-26
**监控日期**: 2026-05-25
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4886
- **最后更新**: 2026-05-25T19:37:58Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: rongfu.leng, Yueqian Lin, Yuekai Zhang

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **功能新增**：1项（支持新的TTS模型）
- **Bug修复**：2项（修复扩散模型休眠阶段问题、Qwen3-TTS前缀缓存正确性问题）
- **用户体验/重构**：1项（重命名默认配置文件）

### 2. 关键变更点及其与项目整体方向的关系
- **`[Higgs-Audio] bosonai/higgs-audio-v2-generation-3B-base TTS模型支持`**：这是最核心的更新。项目目标是“为所有人提供简单、快速、廉价的**全模态**模型服务”。新增TTS（文本转语音）模型支持，直接扩展了项目的**音频生成**模态能力，与“全模态”愿景高度契合。
- **`[UX] 重命名默认配置为 hunyuan_image_3_moe`**：这是一个用户体验优化。将默认配置重命名为一个更具描述性的名称（指向一个具体的图像MoE模型），有助于用户更快理解和使用，体现了项目对易用性的关注。
- **`[Bugfix] 修复扩散模型未设置 sleeping_stages 的问题`** 和 **`[Bugfix] 修复 Qwen3-TTS Stage 0 前缀缓存正确性`**：这两项修复分别针对**图像生成（扩散模型）** 和**音频生成（TTS）** 的核心功能。修复这些bug能提升模型的稳定性和推理效率，是项目走向成熟和可靠的必要步骤。

### 3. 对项目的影响和潜在意义
- **模态能力增强**：新增Higgs-Audio TTS模型，使项目在音频模态上从“仅支持语音识别/理解”向“支持语音生成”迈出了重要一步，丰富了应用场景（如语音助手、有声内容生成）。
- **稳定性与可靠性提升**：两个Bug修复直接解决了模型在特定场景下的运行错误和结果正确性问题。这对于一个旨在“服务所有人”的开源项目至关重要，能增强用户信任，降低使用门槛。
- **用户体验改善**：重命名默认配置是一个小但友好的改动，降低了新用户的认知负担，体现了项目团队对细节和易用性的重视。

### 4. 值得关注的技术点
- **TTS模型支持**：`bosonai/higgs-audio-v2-generation-3B-base` 是一个3B参数规模的TTS模型。支持它意味着项目后端需要处理文本编码、声学模型、声码器等一系列复杂流程，这展示了项目在多模态模型集成方面的技术深度。
- **前缀缓存（Prefix Caching）**：修复Qwen3-TTS的前缀缓存正确性问题。前缀缓存是提升LLM推理效率的关键技术，将其应用于TTS模型，表明项目在优化多模态模型推理性能方面有深入探索。
- **扩散模型控制**：`sleeping_stages` 参数可能用于控制扩散模型在推理过程中的阶段（如跳过某些去噪步骤以加速）。修复此问题确保了模型行为的可预测性和正确性。

### 5. 这些提交如何影响项目发展
- **加速“全模态”愿景实现**：新增TTS模型是补齐“音频生成”短板的关键一步。结合README中“全模态”的定位，项目正从支持图像、文本、音频理解，向**理解与生成并重**的完整多模态平台演进。
- **提升项目成熟度**：从“新增功能”到“修复Bug”再到“优化体验”，这些提交覆盖了项目发展的不同阶段。这表明vllm-omni不仅追求功能广度，也开始注重**深度打磨**，这对于吸引更多生产环境用户至关重要。
- **构建模型生态**：支持来自不同厂商（如Boson AI）的模型，有助于构建一个开放的模型生态，吸引更多社区贡献者，使项目成为多模态模型服务的首选平台。

## 详细提交记录

### [52020c7](https://github.com/vllm-project/vllm-omni/commit/52020c7af781850f6689c49fdf372251c2b66776)

- **作者**: Canlin Guo
- **时间**: 2026-05-25T17:41:15Z
- **提交信息**: [UX] Rename default config to hunyuan_image_3_moe (#3835)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [8f45e68](https://github.com/vllm-project/vllm-omni/commit/8f45e68bcd4b5beb44c45ddbb576e59ea9c7a741)

- **作者**: Yuekai Zhang
- **时间**: 2026-05-25T15:16:07Z
- **提交信息**: [Higgs-Audio] bosonai/higgs-audio-v2-generation-3B-base TTS model support  (#3762)

Signed-off-by: Yuekai Zhang <zhangyuekai@foxmail.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [80dea88](https://github.com/vllm-project/vllm-omni/commit/80dea88007fdf3370d3e7266c31b703b3491decd)

- **作者**: rongfu.leng
- **时间**: 2026-05-25T15:13:38Z
- **提交信息**: [Bugfix] fix when diffusion model not set sleeping_stages (#3023)

Signed-off-by: rongfu.leng <lenronfu@gmail.com>

thanks

### [e996723](https://github.com/vllm-project/vllm-omni/commit/e996723bc9357409a287df6a495d72ff5e677504)

- **作者**: Yueqian Lin
- **时间**: 2026-05-25T15:09:38Z
- **提交信息**: [Bugfix] Fix Qwen3-TTS Stage 0 prefix-caching correctness (#3665)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Signed-off-by: Rein Yang <ruiruyang2@gmail.com>
Co-authored-by: Rein Yang <ruiruyang2@gmail.com>

the ci failure case is irrelavent to this PR and occurs rarely

---
