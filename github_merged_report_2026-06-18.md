# GitHub Stars 合并报告 - 2026-06-18

**合并日期**: 2026-06-19
**监控日期**: 2026-06-18
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


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2026
- **最后更新**: 2026-06-18T09:08:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2424
- **最后更新**: 2026-06-18T12:01:32Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: Watebear, Yang Yong (雍洋)

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **功能新增**：核心更新类型，新增了对多个模型/功能的支持。
- **脚本/配置更新**：对现有脚本进行了调整。

### 2. 关键变更点及其与项目整体方向的关系
- **支持 HiDream-o1 编辑功能 (`i2i_denoise_strength`)** (#1168, #1167):
    - **变更点**：为 `hidream-o1` 和 `qwen-image-edit` 模型引入了图像到图像（i2i）编辑时的去噪强度控制参数。
    - **项目关系**：直接增强了项目的视频生成和编辑能力。`LightX2V` 作为一个轻量级视频生成推理框架，支持更精细的图像编辑控制（如去噪强度）是提升生成质量和用户控制力的关键，符合“轻量”但“功能强大”的定位。
- **支持 Qwen-Image-T2I 全参数训练** (#1160):
    - **变更点**：为 `qwen-image-t2i` 模型添加了全参数训练（Full Parameters Train）的支持。
    - **项目关系**：这是一个重大的功能扩展。`LightX2V` 不仅是一个推理框架，现在也支持对特定模型进行完整的训练。这标志着项目从单纯的“推理引擎”向“训练+推理”一体化平台演进，极大地提升了项目的灵活性和应用深度。
- **更新脚本** (#1169):
    - **变更点**：对项目中的脚本文件进行了更新。
    - **项目关系**：通常是为了配合上述新功能的集成，确保用户能正确使用新添加的训练或编辑功能。属于常规的维护性更新。

### 3. 对项目的影响和潜在意义
- **提升用户控制力**：`i2i_denoise_strength` 参数的引入，允许用户在编辑视频/图像时精细控制生成结果与原始内容的相似度，这对于需要精确编辑的场景（如视频修复、风格迁移）至关重要。
- **扩展应用边界**：支持 `qwen-image-t2i` 的全参数训练，意味着开发者或研究者可以基于自己的数据集对模型进行微调，从而生成特定风格或内容的视频。这极大地拓宽了 `LightX2V` 的应用场景，从通用生成走向定制化生成。
- **增强模型生态**：对 `HiDream-o1` 和 `Qwen` 系列模型的支持，表明项目正在积极拥抱和集成业界最新的、有影响力的模型，保持技术前沿性。

### 4. 值得关注的技术点
- **`i2i_denoise_strength` 参数**：这是一个在扩散模型中常见的控制参数，用于平衡“保留原始图像结构”和“根据文本提示进行创新”之间的权重。其实现方式值得关注，尤其是在视频生成中如何平滑地应用此参数。
- **全参数训练的实现**：支持全参数训练通常需要处理更大的显存占用、更复杂的优化器配置以及数据加载流程。其实现细节（如是否使用了梯度检查点、混合精度训练等）是技术上的亮点。

### 5. 基于项目背景，这些提交如何影响项目发展
- **从“推理”到“训练”的跨越**：README 中描述 `LightX2V` 为“Light Video Generation Inference Framework”。本次对 `qwen-image-t2i` 全参数训练的支持，是项目发展的重要里程碑。它标志着项目不再局限于推理，而是开始构建完整的模型生命周期管理能力，这对于吸引希望进行模型定制和研究的用户群体至关重要。
- **强化“视频生成”核心能力**：通过支持更精细的编辑控制（`i2i_denoise_strength`），项目在“视频生成”这一核心目标上走得更深。它不再仅仅是“生成”，而是进化到“可控生成”和“精准编辑”，这直接提升了项目的实用价值和竞争力。
- **构建开放的模型生态**：同时支持 `HiDream-o1` 和 `Qwen` 系列模型，体现了项目“框架”而非“单一模型”的定位。这种开放策略有助于吸引不同模型生态的开发者，加速社区建设和项目普及。

## 详细提交记录

### [ee9184c](https://github.com/ModelTC/LightX2V/commit/ee9184cc2b0f685f994bf4b598de197f072fdede)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-06-18T12:00:47Z
- **提交信息**: Update scripts (#1169)

### [4bb486f](https://github.com/ModelTC/LightX2V/commit/4bb486f36d208ad5efbdd7d059ab1724557206f6)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-06-18T10:26:25Z
- **提交信息**: Support hidream-o1 edit i2i_denoise_strength (#1168)

### [3b34b93](https://github.com/ModelTC/LightX2V/commit/3b34b93dd5812b4b114d493eacc389cc3b1246bb)

- **作者**: Watebear
- **时间**: 2026-06-18T10:23:08Z
- **提交信息**: [feat]: support qwen-image-t2i full parameters train (#1160)

Co-authored-by: chendingyu <chendingyu1@sensetime.com>

### [6ffef10](https://github.com/ModelTC/LightX2V/commit/6ffef109a0f6e4b62db7c38274e99b1ca9efd6a3)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-06-18T09:32:15Z
- **提交信息**: Support Qwen-image-edit for i2i_denoise_strength (#1167)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2136
- **最后更新**: 2026-06-17T09:45:54Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5820
- **最后更新**: 2026-06-18T14:23:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3727
- **最后更新**: 2026-06-18T22:55:51Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: alexzms

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 昨日更新要点总结

**1. 主要更新类型**
*   **功能新增 (Feature):** 本次提交属于新功能开发。

**2. 关键变更点及其与项目整体方向的关系**
*   **关键变更点:** 实现了针对FP4（4位浮点数）量化感知训练（QAT）的线性层STE（Straight-Through Estimator，直通估计器）功能。
*   **与项目方向的关系:** FastVideo项目旨在加速视频生成模型的训练与推理。引入FP4 QAT是模型量化领域的前沿技术，旨在通过将模型权重和激活值压缩到4位精度，大幅降低模型的内存占用和计算开销，从而在保持模型质量的同时，显著提升训练和推理速度。这与项目“Fast”（快速）的核心目标高度一致。

**3. 对项目的影响和潜在意义**
*   **性能提升:** 成功实现FP4 QAT后，预计能显著减少模型在GPU上的显存占用，并可能利用硬件对低精度计算的加速支持，从而提升训练和推理的吞吐量。
*   **成本降低:** 更低的内存和计算需求意味着可以在更少的GPU或更经济的硬件上运行大型视频生成模型，降低研究和部署成本。
*   **技术领先性:** 支持FP4量化是业界前沿方向，此更新有助于FastVideo在视频生成加速领域保持技术领先地位。

**4. 值得关注的技术点**
*   **STE (Straight-Through Estimator):** 这是实现QAT的关键技术。由于量化操作（将浮点数映射到离散的4位值）的梯度几乎处处为0，无法直接进行反向传播。STE通过在前向传播时进行量化，但在反向传播时“直通”量化函数的梯度（即假设量化函数的梯度为1），从而使得量化后的模型能够被训练。本次提交专门为线性层实现了这一机制。
*   **FP4精度:** 相比更常见的INT8（8位整数）量化，FP4量化精度更低，挑战更大，但潜在的加速和压缩收益也更高。这表明项目团队正在探索极致的模型压缩技术。

**5. 基于项目背景，这些提交如何影响项目发展**
*   **推动核心目标:** 此更新直接服务于FastVideo“加速视频生成”的核心使命。通过引入更激进的量化技术，为未来支持更大、更复杂的视频生成模型（如长视频、高分辨率视频）的高效训练和部署铺平了道路。
*   **完善技术栈:** 该项目已具备FP8、INT8等量化能力，此次新增FP4 QAT，进一步完善了其低精度训练与推理的技术栈，为用户提供了更多样化的加速选择。
*   **吸引社区关注:** 支持前沿的FP4量化技术，有助于吸引对模型效率有极致追求的研究者和开发者，壮大社区，并可能催生更多基于此技术的创新应用。

## 详细提交记录

### [6da206e](https://github.com/hao-ai-lab/FastVideo/commit/6da206e1967faf9548df012e0a7f0c091da0413b)

- **作者**: alexzms
- **时间**: 2026-06-18T22:55:47Z
- **提交信息**: [feat] QAD 5090: FP4 QAT linear STE for training (13/12) (#1463)

Co-authored-by: William Lin <SolitaryThinker@users.noreply.github.com>
Co-authored-by: Loay Rashid <42599591+loaydatrain@users.noreply.github.com>
Co-authored-by: Kaiqin Kong <k1kong@ucsd.edu>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33881
- **最后更新**: 2026-06-18T22:39:46Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Tarek Ziade, Sayak Paul

## AI分析总结

好的，根据您提供的仓库背景和提交记录，以下是昨日更新的分析总结：

### 1. 主要更新类型

本次更新主要为 **CI/CD（持续集成/持续部署）流程优化**，属于基础设施和开发流程的改进，不涉及模型、API或用户直接使用的功能变更。

### 2. 关键变更点及其与项目整体方向的关系

*   **变更点1: 使用托管运行器 (`b596c83`)**
    *   **内容**: 将CI流程从自建/特定网络环境迁移到HuggingFace的托管运行器。
    *   **与项目方向关系**: `diffusers` 作为一个社区驱动的、快速迭代的开源项目，其CI流程的稳定性和可访问性至关重要。使用托管运行器可以：
        *   **降低维护成本**: 减少维护自建CI基础设施（如Tailscale网络）的负担。
        *   **提升可靠性**: 托管运行器通常更稳定，能减少因网络问题导致的CI失败。
        *   **加速开发**: 更可靠的CI意味着开发者可以更快地获得代码合并的反馈，加速新功能（如新的扩散模型、Pipeline、调度器）的集成。

*   **变更点2: 优化提醒机制 (`9a72cd3`)**
    *   **内容**: 避免在管理员或核心维护者提交的PR上触发不必要的提醒（例如，提醒PR作者关联issue）。
    *   **与项目方向关系**: 这体现了项目对**社区协作效率**的重视。通过减少对核心贡献者的“噪音”提醒，让他们能更专注于代码审查和架构决策，从而推动项目更高效地发展。这符合一个大型开源项目精细化运营的趋势。

### 3. 对项目的影响和潜在意义

*   **直接影响**: 提升了CI流程的稳定性和开发者的体验，减少了因基础设施问题导致的阻塞。
*   **潜在意义**:
    *   **为更大规模协作铺路**: 更健壮的CI是支持更多贡献者、更快迭代速度的基础。
    *   **提升项目专业度**: 从自建网络迁移到托管服务，是项目成熟化和专业化的一个标志。
    *   **减少维护者负担**: 自动化流程的优化（如减少不必要的提醒）直接减轻了核心维护者的工作压力。

### 4. 值得关注的技术点

*   **CI/CD 基础设施迁移**: 从依赖特定网络环境（Tailscale）到使用通用托管运行器，这是一个典型的基础设施现代化操作。对于关注项目运维和贡献流程的开发者来说，这是一个值得注意的变化。
*   **GitHub Actions 工作流优化**: 提交中提到了“hosted runners”和“don't remind on prs from admins”，这涉及到对GitHub Actions工作流配置的精细调整，体现了对自动化流程的深度掌控。

### 5. 结合项目背景，这些提交如何影响项目发展

*   **背景回顾**: `diffusers` 的目标是成为最先进、最易用的扩散模型库，它依赖于社区贡献和快速迭代。
*   **影响分析**:
    *   **加速创新**: 更稳定、更少维护负担的CI，意味着开发者可以更快地将新模型、新Pipeline（如Stable Diffusion 3、Sora等）集成到库中，从而保持`diffusers`在扩散模型领域的领先地位。
    *   **降低贡献门槛**: 对于外部贡献者而言，一个稳定可靠的CI流程意味着他们的PR能更快地被测试和合并，这鼓励了更多社区贡献，形成良性循环。
    *   **聚焦核心价值**: 通过优化CI等“后台”工作，项目团队可以将更多精力投入到核心功能开发、模型支持和文档完善上，直接服务于最终用户。

**总结**: 昨日的更新是典型的“修路”工作，虽然不直接增加用户可见的功能，但通过优化基础设施和开发流程，为`diffusers`项目未来的快速、稳定发展奠定了更坚实的基础。

## 详细提交记录

### [b596c83](https://github.com/huggingface/diffusers/commit/b596c83aef383e23738446ef8a8d873967b5a24c)

- **作者**: Tarek Ziade
- **时间**: 2026-06-18T15:38:04Z
- **提交信息**: ci: use hosted runners (#13987)

hosted runners can now reach Serge directly without creating a tailscale session

### [9a72cd3](https://github.com/huggingface/diffusers/commit/9a72cd3ee9eaefbf5cac47640ba1c3acf082634d)

- **作者**: Sayak Paul
- **时间**: 2026-06-18T08:23:10Z
- **提交信息**: ci: don't remind on prs from admins, etc. (#13965)

* ci: don't remind on prs from admins, etc.

* don't remind model authors about linking issues/.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
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


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12595
- **最后更新**: 2026-06-18T12:28:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29174
- **最后更新**: 2026-06-18T22:50:21Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 22
- **主要提交者**: Baizhou Zhang, Qichao Li, zijiexia

## AI分析总结

好的，作为专业的代码分析助手，以下是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结。

### 1. 主要更新类型

-   **功能新增与硬件支持 (Feature & Hardware Support):** 占比最高，包括对 AMD GPU (gfx950)、NPU (Ascend) 的优化和新模型支持 (DeepSeek-V4, GLM-4.7-Flash)。
-   **性能优化 (Performance Optimization):** 针对特定硬件 (AMD) 和特定场景 (spec decoding, hybrid linear attention) 进行调优。
-   **重构 (Refactoring):** 对 Runner 和 Mamba 等核心模块的代码进行统一和清理，提升可维护性。
-   **Bug 修复 (Bug Fix):** 修复了 spec decoding、Intern-S1 模型、Docker 构建等多个问题。
-   **文档与示例 (Docs & Cookbook):** 更新了 DeepSeek-V4、Laguna-M.1 等模型的 Cookbook 和基准测试结果。

### 2. 关键变更点及其与项目整体方向的关系

-   **硬件生态扩展 (AMD & NPU):**
    -   `[AMD][Perf] Tune extend attention block sizes for gfx950` 和 `[AMD][CI] Use non-gated Qwen3-8B for MI35x disaggregation tests` 表明项目持续投入对 AMD GPU 的深度优化和 CI 测试。
    -   `[NPU] Add head_dim=256 to _can_use_tnd whitelist` 和 `[NPU] Add MTP support for GLM-4.7-Flash` 显示项目正在积极适配国产 NPU (Ascend)，并为其添加新特性支持。
    -   **关系:** 这与项目README中“为各种硬件提供高性能推理”的目标高度一致，旨在打破对单一硬件 (NVIDIA) 的依赖，构建更广泛的硬件生态。

-   **前沿模型支持 (DeepSeek-V4, Laguna-M.1):**
    -   `[DeepSeek-V4] Fuse UE8M0 scale rounding into FP8 group quantization` 和 `[NPU] Add Ascend NPU support for DeepSeek-V4` 表明项目正在快速跟进并优化最新的 DeepSeek-V4 模型。
    -   `Add Laguna-M.1 cookbook` 和 `[Cookbook] Laguna-M.1: enable FP8 on Blackwell` 显示项目在为新模型提供开箱即用的最佳实践和性能数据。
    -   **关系:** 这体现了项目作为“前沿模型推理引擎”的定位，快速集成最新、最强大的模型，并为其提供优化方案，是保持项目竞争力的关键。

-   **核心推理能力增强 (Spec Decoding, Context Parallelism):**
    -   `[3/N][CP] Implement zigzag CP strategy` 引入了新的上下文并行策略，可能用于优化长序列推理。
    -   `[spec decoding] fully overlap spec decoding for hybrid linear attention backend` 和 `Fix spec decoding with grammar in disagg` 持续优化投机解码 (Speculative Decoding) 这一关键加速技术，特别是在混合注意力后端和分离式推理场景下。
    -   **关系:** 这些是提升推理吞吐量和降低延迟的核心技术。持续改进这些特性，直接增强了项目在长文本、高并发场景下的竞争力。

-   **代码质量与可维护性 (Refactoring & Bugfix):**
    -   `refactor(runner): unify eager-forward DP/MLP-sync padding` 和 `refactor(runner): unify pp_proxy_tensors forward kwarg` 等重构工作，旨在统一和简化核心 Runner 模块的代码，降低未来开发和维护的复杂度。
    -   多个 Bug 修复 (如 `Fix Intern-S1 FP8 expert count lookup`, `fix: speculative draft worker clobbering target attention backend`) 提升了系统的稳定性和可靠性。
    -   **关系:** 这是项目健康发展的基石。重构为未来功能迭代铺平道路，而 Bug 修复则直接提升了用户的使用体验。

### 3. 对项目的影响和潜在意义

-   **提升硬件兼容性:** 对 AMD 和 NPU 的持续投入，将吸引更多使用非 NVIDIA 硬件的用户和开发者，扩大项目的用户基础。
-   **巩固前沿模型地位:** 快速适配 DeepSeek-V4 等最新模型，并发布优化后的 Cookbook，有助于项目成为社区中运行这些模型的首选方案。
-   **增强核心竞争力:** 对投机解码和上下文并行等核心技术的优化，将直接转化为性能优势，使项目在处理长序列和高并发推理时更具吸引力。
-   **提高项目成熟度:** 大量的重构和 Bug 修复工作，表明项目正在从快速迭代期向稳定成熟期过渡，这对于企业级用户至关重要。

### 4. 值得关注的技术点

-   **Zigzag CP 策略:** 这是一种新的上下文并行策略，值得关注其具体实现和性能优势，可能对超长序列推理有显著影响。
-   **UE8M0 量化融合:** 将 UE8M0 的 scale rounding 融合到 FP8 量化中，这是一种精细化的量化优化技术，可能在不损失精度的情况下提升性能。
-   **Hybrid Linear Attention 的投机解码重叠:** 通过完全重叠投机解码过程，可以最大化利用硬件资源，是提升推理吞吐量的高级技巧。
-   **NPU 的 MTP (Multi-Token Prediction) 支持:** 为 NPU

## 详细提交记录

### [c1067f8](https://github.com/sgl-project/sglang/commit/c1067f88d6970562525d0385b80c7916aa8ea2a8)

- **作者**: giang_ng_tr
- **时间**: 2026-06-18T22:16:52Z
- **提交信息**: [AMD][Perf] Tune extend attention block sizes for gfx950 (head_dim > 128) (#27793)

### [e3026ef](https://github.com/sgl-project/sglang/commit/e3026ef01622c7b9058bee246012dfbb29b5de4f)

- **作者**: Baizhou Zhang
- **时间**: 2026-06-18T22:10:30Z
- **提交信息**: [3/N][CP] Implement zigzag CP strategy (#28421)

### [9fc9d37](https://github.com/sgl-project/sglang/commit/9fc9d37f6d10eb1fba46d4eaed2abdad5c530807)

- **作者**: Ashish
- **时间**: 2026-06-18T21:58:32Z
- **提交信息**: Fix spec decoding with grammar in disagg (#24082)

Co-authored-by: jimmy.shong <jimmy.shong@radixark.ai>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Codex <codex@example.com>

### [bea282c](https://github.com/sgl-project/sglang/commit/bea282cede6c2eeeb6663d1d73a8357ce1bb2f2f)

- **作者**: Qichao Li
- **时间**: 2026-06-18T21:41:56Z
- **提交信息**: [DeepSeek-V4] Fuse UE8M0 scale rounding into FP8 group quantization (#26766)

Co-authored-by: liqichao <liqichao@baidu.com>
Co-authored-by: yhyang201 <yhyang201@gmail.com>

### [27a374e](https://github.com/sgl-project/sglang/commit/27a374eaefd899a375d4b79ef7f69fa26db5ac9e)

- **作者**: Zhaoyi Li
- **时间**: 2026-06-18T21:29:35Z
- **提交信息**: [AMD][CI] Use non-gated Qwen3-8B for MI35x disaggregation tests (#28678)

### [f83e4d5](https://github.com/sgl-project/sglang/commit/f83e4d59683046afa423c257187967a6edfac8b9)

- **作者**: Cheng Wan
- **时间**: 2026-06-18T20:41:30Z
- **提交信息**: refactor(runner): unify eager-forward DP/MLP-sync padding into one helper (#28383)

### [2411737](https://github.com/sgl-project/sglang/commit/241173724484767d151320485ca74754e36738a6)

- **作者**: Qiaolin Yu
- **时间**: 2026-06-18T20:31:12Z
- **提交信息**: [spec decoding] fully overlap spec decoding for hybrid linear attention backend (#28579)

### [cf0afe3](https://github.com/sgl-project/sglang/commit/cf0afe3223d0e18df33b2fc46c3acf4ab624ba72)

- **作者**: DovLin
- **时间**: 2026-06-18T20:30:20Z
- **提交信息**: [FA]Add lost params in fa varlen func (#28642)

### [66a7fd5](https://github.com/sgl-project/sglang/commit/66a7fd5c0b3efe90afd0759516cd6819d5dec94a)

- **作者**: Yi Zhang
- **时间**: 2026-06-18T20:02:36Z
- **提交信息**: refactor: mamba radix cache server args initialize (#28151)

Co-authored-by: Ke Bao <ispobaoke@gmail.com>

### [8f6d9ef](https://github.com/sgl-project/sglang/commit/8f6d9ef9a55e27f60ce55a3bfa35136370bd252e)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-18T19:51:23Z
- **提交信息**: [misc] Drop redundant req_pool_indices_cpu guards; fold hisparse into GLM-5.1 e2e (#28607)

### [792cb3a](https://github.com/sgl-project/sglang/commit/792cb3a5d069d3ce7b94a4c337a1cab039ebaa6d)

- **作者**: Lawrence Wu
- **时间**: 2026-06-18T19:51:09Z
- **提交信息**: fix: add missing guard for use_jit_ep_activation (#27377)

### [61a8b42](https://github.com/sgl-project/sglang/commit/61a8b42c001442b947f7b114ed232dfd65764e2e)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-18T18:40:56Z
- **提交信息**: docs(minimax-m3): add MMMU-Pro accuracy to B200 benchmark card (#28668)

### [f7632ef](https://github.com/sgl-project/sglang/commit/f7632ef8603bf966cc2062cd45e6fd369ec83931)

- **作者**: Jimmy Shong
- **时间**: 2026-06-18T16:23:53Z
- **提交信息**: [Cookbook] Laguna-M.1: enable FP8 on Blackwell + drop provisional AIME numbers (#28664)

### [0eded9e](https://github.com/sgl-project/sglang/commit/0eded9e208a46bf6a26fda86005ad78c52ae9e44)

- **作者**: Jimmy Shong
- **时间**: 2026-06-18T15:23:53Z
- **提交信息**: Add Laguna-M.1 cookbook (#28661)

### [97e3b89](https://github.com/sgl-project/sglang/commit/97e3b8998dc0f331423438091067ec0201d35e54)

- **作者**: Jimmy Shong
- **时间**: 2026-06-18T12:04:25Z
- **提交信息**: Pass quant_config to attention gate projection (#28649)

### [bb9d31f](https://github.com/sgl-project/sglang/commit/bb9d31f22d8930ddaa909fb9e4cd234358e7e8a8)

- **作者**: syy-hw
- **时间**: 2026-06-18T09:55:50Z
- **提交信息**: [NPU] Add head_dim=256 to _can_use_tnd whitelist (#28635)

### [2a9cce5](https://github.com/sgl-project/sglang/commit/2a9cce5d2757c42bb869b65f9d07807ca9471249)

- **作者**: Estrella-xx
- **时间**: 2026-06-18T09:54:06Z
- **提交信息**: [NPU] Add MTP support for GLM-4.7-Flash (#28516)

### [b7d7dfb](https://github.com/sgl-project/sglang/commit/b7d7dfb4ed5a09efe398eca82c37639935c078ea)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-18T09:49:59Z
- **提交信息**: [Bugfix] Fix Intern-S1 FP8 expert count lookup (#28629)

### [67db2ac](https://github.com/sgl-project/sglang/commit/67db2ac3e74ef9ed9a38dc7e280c2503faf3051c)

- **作者**: Cheng Wan
- **时间**: 2026-06-18T09:23:47Z
- **提交信息**: refactor(runner): unify pp_proxy_tensors forward kwarg into one helper (#28382)

### [105e095](https://github.com/sgl-project/sglang/commit/105e095e005d02a178fb6c5a23bd22ba644c90e4)

- **作者**: Douglas Yang
- **时间**: 2026-06-18T08:51:57Z
- **提交信息**: [Docker] Fix cu12 dev image build: pin torch reinstall + JIT-fallback for missing x86 cubins (#28632)

### [867707f](https://github.com/sgl-project/sglang/commit/867707f1f2dcad5f384dd23e890917ce1f9ab277)

- **作者**: Zhangheng
- **时间**: 2026-06-18T08:39:46Z
- **提交信息**: [UnifiedTree]: move some kl test from base to extra stage (#28627)

Co-authored-by: ispobock <ispobaoke@gmail.com>

### [fa71064](https://github.com/sgl-project/sglang/commit/fa71064147a16b3710755a520f1257323c99b459)

- **作者**: cctry
- **时间**: 2026-06-18T08:21:14Z
- **提交信息**: fix: speculative draft worker clobbering target attention backend (#28559)

### [5900126](https://github.com/sgl-project/sglang/commit/59001267c3c3822598f4ff4903a309ba6543984f)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-18T07:34:00Z
- **提交信息**: Fix bench serving base-url-only runs (#28617)

Co-authored-by: shuwenn <47200617+alphabetc1@users.noreply.github.com>

### [9b10821](https://github.com/sgl-project/sglang/commit/9b10821c8e6eb9f05c357641d28276a2387fa148)

- **作者**: Talantan1102
- **时间**: 2026-06-18T07:30:25Z
- **提交信息**: [NPU] Add Ascend NPU support for DeepSeek-V4 (#25144)

Co-authored-by: khalil2ji3mp6 <khalilzhk@gmail.com>
Co-authored-by: randgun <kelonlu@163.com>
Co-authored-by: t00937989 <tanlei33@huawei.com>

### [3f66873](https://github.com/sgl-project/sglang/commit/3f66873304626d1c3ea87d5b17673e6b6fd6e2ef)

- **作者**: zijiexia
- **时间**: 2026-06-18T07:05:21Z
- **提交信息**: [Docs] DeepSeek-V4 cookbook: drop --disable-flashinfer-autotune from GB300 Flash low-latency (#28590)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
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


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 83278
- **最后更新**: 2026-06-18T23:17:26Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 29
- **主要提交者**: AlexHuang, Tiezhen WANG, stefankoncarevic

## AI分析总结

好的，根据您提供的 `vllm-project/vllm` 仓库的README摘要和昨日提交记录，以下是分析总结：

### 1. 主要更新类型

- **Bug修复 (Bugfix):** 数量最多，覆盖了解析器、KV连接器、量化、内核、工具解析器等多个模块。
- **性能优化 (Perf):** 包括移除未使用的日志器、异步KV查找、优化Gumbel采样精度等。
- **功能新增 (Feature):** 新增了流式解析引擎、`/get_world_size` API路由、模型元数据返回等。
- **重构 (Refactor):** 主要是模型运行器V2的迁移工作。
- **CI/测试 (CI/Tests):** 修复CI问题、新增测试用例、启用特定平台测试。
- **安全更新 (Security):** 升级Starlette依赖以修复CVE漏洞。
- **平台支持 (Platform):** 大量针对ROCm (AMD GPU) 和CPU的修复与优化。
- **模型支持 (Model):** 新增对GLM系列模型的支持，移除了Bamba模型。

### 2. 关键变更点及其与项目整体方向的关系

- **解析器与工具调用增强 (Parser & Tool Calling):**
  - **变更:** 修复了空工具块导致后续内容丢失、Qwen3参数解析错误、非有限数字处理等问题；新增了GLM4.7/5.1/5.2解析器；新增了流式解析引擎；修复了Anthropic API的中间对话系统消息支持。
  - **关系:** 直接服务于项目“Easy”和“cheap”的目标。强大的解析器支持是vLLM作为通用推理引擎的核心，能兼容更多模型和API格式（如OpenAI、Anthropic），降低用户集成成本。

- **KV连接器与Mooncake分布式推理 (KV Connector & Mooncake):**
  - **变更:** 禁用了特定条件下的TP put-striding；实现了异步查找以减少调度开销；跳过了不可达SWA块的KV查找。
  - **关系:** 这是vLLM实现“fast”和可扩展性的关键。Mooncake是一个分布式KV缓存系统，这些优化旨在减少分布式推理中的通信开销和调度延迟，提升大规模部署时的吞吐量和效率。

- **模型运行器V2迁移 (Model Runner V2 - MRV2):**
  - **变更:** 默认支持量化模型；禁用了V2运行器上的并行无关文件系统缓存；优化了FP32 Gumbel采样精度。
  - **关系:** 这是vLLM内部架构的重大重构，旨在提供更统一、更高效的模型执行路径。MRV2的成熟是项目长期发展的基石，能更好地支持新模型、新量化方法和硬件特性。

- **量化与内核优化 (Quantization & Kernel):**
  - **变更:** 修复了FP8 KV缓存与检查点的兼容性、GPTQ/CT MoE的对称量化回归、AWQ在Intel XPU上的反量化问题；为DeepGEMM内核添加了PDL支持；修复了非8倍数头大小的内存对齐崩溃。
  - **关系:** 直接关系到“cheap”和“fast”。量化是降低显存占用和推理成本的核心技术，内核优化则是榨取硬件性能的关键。这些修复确保了量化在各种硬件和模型上的正确性和稳定性。

- **平台支持 (Platform Support):**
  - **变更:** 大量针对ROCm (AMD GPU) 的修复，包括推测解码、MXFP4 LoRA测试、DeepSeek V4功能修复、自定义算子别名等；为CPU平台跳过Triton内核补丁；修复RISC-V向量扩展检测。
  - **关系:** 体现了项目“for everyone”的愿景。通过积极适配AMD、Intel、RISC-V等非NVIDIA硬件，vLLM正在打破硬件垄断，扩大其用户基础。

### 3. 对项目的影响和潜在意义

- **稳定性和兼容性提升:** 大量的Bug修复，特别是解析器和量化方面的修复，将显著提升vLLM在生产环境中的稳定性和与不同模型、API的兼容性。
- **性能与效率优化:** Mooncake的异步查找、Gumbel采样的精度优化、移除未使用日志器等，将在分布式推理和单卡推理场景下带来性能提升。
- **架构演进:** MRV2的持续推进和Rust前端功能的增加，表明vLLM正在向更模块化、高性能的架构演进，为未来支持更复杂的模型和功能打下基础。
- **生态扩展:** 对ROCm、CPU、RISC-V的持续支持，以及对GLM、DeepSeek等新模型的适配，将吸引更多用户和开发者，巩固vLLM作为主流推理框架的地位。

### 4. 值得关注的技术点

- **流式解析引擎 (Streaming Parser Engine):** 这是一个重要的功能，允许模型在生成过程中实时解析结构化输出（如JSON、工具调用），对需要实时响应的应用（如Agent、聊天机器人）至关重要。
- **Mooncake异步KV查找:** 将同步的KV查找操作变为异步，可以有效减少调度器的等待时间，是提升分布式推理系统吞吐量的经典优化手段。
- **DeepGEMM内核的PDL支持:** PDL（可能是某种描述语言或调度策略）的引入，可能意味着vLLM正在探索更灵活、更自动化的内核生成或选择机制，以适配不同硬件。
- **MRV2默认支持量化模型:** 这是MRV2成熟度的重要标志，意味着未来用户可能无需额外配置即可享受量化带来的好处，简化了使用流程。

###

## 详细提交记录

### [7f616c3](https://github.com/vllm-project/vllm/commit/7f616c327d24a259dd81605e513c42ce2b9dc204)

- **作者**: Ben Browning
- **时间**: 2026-06-18T23:17:18Z
- **提交信息**: [Bugfix] [Parser] Fix empty tool block silently dropping subsequent content (#46091)

Signed-off-by: Ben Browning <bbrownin@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [c3c6d72](https://github.com/vllm-project/vllm/commit/c3c6d723fdd1c315322e5d5a51c479eb2bc017a2)

- **作者**: Ivy Xu
- **时间**: 2026-06-18T22:24:29Z
- **提交信息**: [Perf] Remove unused loggers in `reasoning/` (#45988)

Signed-off-by: Ivy <fakeshadow1337@gmail.com>

### [41dcf49](https://github.com/vllm-project/vllm/commit/41dcf49ca52ab25178ca8869298275b1787f328a)

- **作者**: Yifan Qiao
- **时间**: 2026-06-18T22:13:44Z
- **提交信息**: [Bugfix][KV Connector] Disable Mooncake TP put-striding when DCP > 1 (#45371)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Jingyi Yang <girasoleyang@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [35e4dd4](https://github.com/vllm-project/vllm/commit/35e4dd4a69b6b95feb74866341daa46c3836aed0)

- **作者**: Yifan Qiao
- **时间**: 2026-06-18T21:44:02Z
- **提交信息**: [KV Connector][Mooncake] Async lookup to reduce scheduler overhead (#45659)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [4ce2d01](https://github.com/vllm-project/vllm/commit/4ce2d0145312809ef6122ccb7be8ae7cafa462a9)

- **作者**: MrFan
- **时间**: 2026-06-18T20:19:11Z
- **提交信息**: fix(anthropic): auto-detect template support for mid-conversation system messages (#46025)

Signed-off-by: felix0080 <felix0080@users.noreply.github.com>
Signed-off-by: Ben Browning <bbrownin@redhat.com>
Co-authored-by: felix0080 <felix0080@users.noreply.github.com>
Co-authored-by: Ben Browning <bbrownin@redhat.com>

### [16908e1](https://github.com/vllm-project/vllm/commit/16908e132e10f75af93049e865130f8987573f5d)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-18T19:42:09Z
- **提交信息**: [MRV2] Make FP32 Gumbel sampling more accurate (#45996)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [225936a](https://github.com/vllm-project/vllm/commit/225936a1dd10586798c0181696d628e7b609ea90)

- **作者**: Wentao Ye
- **时间**: 2026-06-18T19:37:39Z
- **提交信息**: [CI Bug] Revert #42379 to fix CI `Multi-Modal Models (Extended Generation 1)` (#46070)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [f6ba720](https://github.com/vllm-project/vllm/commit/f6ba7209632936d4908499afc799e96f6eee2725)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-06-18T19:35:13Z
- **提交信息**: (security) Upgrade Starlette to >= 1.0.1 to fix CVE-2026-48710 (#45675)

Signed-off-by: jperezde <jperezde@redhat.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [b53b1c7](https://github.com/vllm-project/vllm/commit/b53b1c7ffe7aebdafd0876350f30e51d1226c92a)

- **作者**: Wentao Ye
- **时间**: 2026-06-18T19:20:44Z
- **提交信息**: [Model Runner V2] Migration to support quantized model by default [5/N] (#44446)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [79ca54d](https://github.com/vllm-project/vllm/commit/79ca54d2215b22d9a4fc17378eb7aa2b2eb9dbd1)

- **作者**: Ting SUN
- **时间**: 2026-06-18T18:18:25Z
- **提交信息**: [Bugfix][Quantization] Don't reject fp8_e5m2 KV cache for non-fp8 quantized checkpoints (#45040)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [09f3cd5](https://github.com/vllm-project/vllm/commit/09f3cd5c1080de42c9001803f638852b7f6a4310)

- **作者**: Ben Browning
- **时间**: 2026-06-18T18:04:06Z
- **提交信息**: [Bugfix] [Parser] Fix Qwen3 latent bug in partial params dropping values containing `<` (#46047)

Signed-off-by: Ben Browning <bbrownin@redhat.com>

### [ea6078f](https://github.com/vllm-project/vllm/commit/ea6078fe6a7242e7a5a89798e617b807d2540466)

- **作者**: Itay Etelis
- **时间**: 2026-06-18T17:43:35Z
- **提交信息**: [KV Connector][Offloading] Disable parallel-agnostic fs-tier cache on V2 model runner (#46044)

Signed-off-by: Itay Etelis <etelis2019@gmail.com>
Co-authored-by: Itay Etelis <etelis2019@gmail.com>

### [a0df04e](https://github.com/vllm-project/vllm/commit/a0df04e4775efbfebd65c997259d63af0ec548ce)

- **作者**: Palaiologos1453
- **时间**: 2026-06-18T17:37:39Z
- **提交信息**: [Tests] Add Qwen3 streaming parser delta boundary cases (#45708)

Signed-off-by: test test <2260891073@qq.com>

### [e2352c2](https://github.com/vllm-project/vllm/commit/e2352c29743aeec4a2dafc66c4fdd0e10b37072e)

- **作者**: stefankoncarevic
- **时间**: 2026-06-18T16:59:37Z
- **提交信息**: [ROCm][Spec Decode] Fix probabilistic draft probs test attention backend (#45706)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [25faa1f](https://github.com/vllm-project/vllm/commit/25faa1f4cc2ec5d0db50b2b2b04c43f58d8a0931)

- **作者**: qli88
- **时间**: 2026-06-18T16:59:09Z
- **提交信息**: [CI]Enable mxfp4 lora test for ROCm platform (#43802)

Signed-off-by: Qiang Li <qiang.li2@amd.com>

### [4583630](https://github.com/vllm-project/vllm/commit/4583630b562124c033551e5630a7ab3d607a6f03)

- **作者**: Humphrey
- **时间**: 2026-06-18T16:58:22Z
- **提交信息**: [Bugfix][Kernel] Check output alignment in vectorize_with_alignment (fixes misaligned-address crash for non-multiple-of-8 head sizes) (#45466)

Signed-off-by: HumphreySun98 <humphreysun98@gmail.com>

### [21da47d](https://github.com/vllm-project/vllm/commit/21da47dabe27559bf46b80ff6caacafd9dde6035)

- **作者**: Divakar Verma
- **时间**: 2026-06-18T16:50:32Z
- **提交信息**: [ROCm][CI] move lora%N test to mi300 and gate (#45970)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [6c379b9](https://github.com/vllm-project/vllm/commit/6c379b9e5439ae305913e4a87ebf2b2e816072b4)

- **作者**: Chauncey
- **时间**: 2026-06-18T16:42:10Z
- **提交信息**: [Frontend] Add Streaming Parser Engine and new GLM4.7/GLM5.1/GLM5.2 Parser (#45915)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5099474](https://github.com/vllm-project/vllm/commit/509947463375cc27e2a60d05ce5463f6dd059171)

- **作者**: Rohan Potdar
- **时间**: 2026-06-18T16:30:21Z
- **提交信息**: [Bugfix][ROCm] Fix rocm_aiter_per_tensor_quant custom op aliasing (#45747)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>

### [058cc0a](https://github.com/vllm-project/vllm/commit/058cc0a8b6e33523b1ed75db933726959df43791)

- **作者**: Yuwen Zhou
- **时间**: 2026-06-18T16:20:29Z
- **提交信息**: [Bugfix] Restore is_sym guard for zp in GPTQ/CT MoE to fix symmetric quant regression (#45656)

Signed-off-by: yuwenzho <yuwen.zhou@intel.com>

### [837db76](https://github.com/vllm-project/vllm/commit/837db7605e240202c43577cfa4da65f3c8f506fb)

- **作者**: Ashish Patel
- **时间**: 2026-06-18T16:00:20Z
- **提交信息**: [Bugfix][Tool Parser] Handle non-finite numbers in coerce_to_schema_type (#43984)

Signed-off-by: ashishpatel26 <shriganesh.patel@gmail.com>
Co-authored-by: Ben Browning <bbrownin@redhat.com>

### [bf2a393](https://github.com/vllm-project/vllm/commit/bf2a3930341695e9b2dad73f2934d5a6d8f564dc)

- **作者**: Mark McLoughlin
- **时间**: 2026-06-18T14:15:43Z
- **提交信息**: Temporarily remove @markmc from CODEOWNERS (#46053)

Signed-off-by: Mark McLoughlin <markmc@redhat.com>

### [d682968](https://github.com/vllm-project/vllm/commit/d682968aa9fcd7e7a78218b548c52fc198a87a6c)

- **作者**: Tiezhen WANG
- **时间**: 2026-06-18T13:51:00Z
- **提交信息**: [Model] Remove BambaForCausalLM (#45990)

Signed-off-by: Xianbao QIAN <xianbao.qian@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [021cdf7](https://github.com/vllm-project/vllm/commit/021cdf72bc2295b5dcb60fcbc4b0dae66831cf77)

- **作者**: lyd1992
- **时间**: 2026-06-18T13:22:35Z
- **提交信息**: Fix _riscv_supports_rvv_vlen128() to detect RVV on hardware without zvl flags (#43179)

Signed-off-by: liuyudong <liuyudong@iscas.ac.cn>
Co-authored-by: YuanSheng <yuansheng@isrc.iscas.ac.cn>

### [4cb5e74](https://github.com/vllm-project/vllm/commit/4cb5e746b63707ed470f952cfb77778a3dd34400)

- **作者**: Ashar
- **时间**: 2026-06-18T13:10:20Z
- **提交信息**: [Rust Frontend]: Add `/get_world_size` route with static parallel size (#44801)

### [22cc891](https://github.com/vllm-project/vllm/commit/22cc891108b1721959a4e346665b4c9cdddd3fb0)

- **作者**: Jee Jee Li
- **时间**: 2026-06-18T12:49:01Z
- **提交信息**: [Kernel] Add PDL support for DeepGEMM kernel (#46006)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [afdcbd5](https://github.com/vllm-project/vllm/commit/afdcbd5d39eaf2b37b616c8ee8aabc51e15e70ef)

- **作者**: Tuukka Sarvi
- **时间**: 2026-06-18T12:21:14Z
- **提交信息**: [ROCm][DSv4] Functional fixes for DeepSeek V4 on MI300X/MI325X (#45681)

Signed-off-by: ganyi <ygan@amd.com>
Signed-off-by: Markus Hartikainen <markus.hartikainen@amd.com>
Signed-off-by: Tuukka Sarvi <tuukka.sarvi@amd.com>
Co-authored-by: ganyi <ygan@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Markus Hartikainen <markus.hartikainen@amd.com>
Co-authored-by: Jin Tao <jintao12@amd.com>

### [8d4f549](https://github.com/vllm-project/vllm/commit/8d4f54966cdb8f1d0768fbe5319e400047877a3d)

- **作者**: AlexHuang
- **时间**: 2026-06-18T12:12:28Z
- **提交信息**: fix(quantization): Fix AWQ dequantize on Intel XPU and refactor AutoAWQ config (#42727)

Signed-off-by: Alex <alex.tech.lab@outlook.com>
Signed-off-by: AlexHuang <jihuihuang@tencent.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [351c72d](https://github.com/vllm-project/vllm/commit/351c72d6e5d43148f16d67b11a613d14dafbf6a4)

- **作者**: Jonathan Mamou
- **时间**: 2026-06-18T10:59:30Z
- **提交信息**: [CPU] Skip Triton kernel monkey-patches when Triton-CPU is available (#44991)

Signed-off-by: jmamou <jonathan.mamou@intel.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [7299e65](https://github.com/vllm-project/vllm/commit/7299e6509ef8b9d27e86c4f2315e1ec5628ca426)

- **作者**: Tahsin Tunan
- **时间**: 2026-06-18T10:29:21Z
- **提交信息**: [Rust Frontend] Return model metadata fields in /v1/models (#45950)

Signed-off-by: Tahsin Tunan <tahsintunan@gmail.com>

### [0898535](https://github.com/vllm-project/vllm/commit/08985351f369d3dd6b80bc54ce143ede268e2846)

- **作者**: littlecircle0730
- **时间**: 2026-06-18T09:32:10Z
- **提交信息**: Fix Stale Encoder Cache After Weight Update (#45093)

Signed-off-by: littlecircle0730 <littlecircle0730@gmail.com>

### [5fd3b27](https://github.com/vllm-project/vllm/commit/5fd3b276f8fa34b70d3c83314700f626c66f9a22)

- **作者**: Wei Zhao
- **时间**: 2026-06-18T09:23:20Z
- **提交信息**: [Mooncake] Skip KV lookup for non-reachable SWA blocks (#45444)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>

### [1e9f04d](https://github.com/vllm-project/vllm/commit/1e9f04da14a6fe349c828928c0f94cf4fcce5363)

- **作者**: MrFan
- **时间**: 2026-06-18T07:58:11Z
- **提交信息**: fix(anthropic): preserve inline system message position for prefix caching (#44602)

Signed-off-by: felix0080 <felix0080@users.noreply.github.com>
Co-authored-by: felix0080 <felix0080@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-19
**监控日期**: 2026-06-18
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5195
- **最后更新**: 2026-06-18T22:42:20Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 9
- **主要提交者**: Zening Chen, Alicia, Honghan Zhu

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对vllm-project/vllm-omni仓库昨日更新的分析总结：

### 1. 主要更新类型

*   **Bug修复**：修复了MOSS-TTS的音频损坏问题，以及DreamZero的TP和交叉注意力缓存问题。
*   **功能新增**：为DreamZero修复了TP和交叉注意力缓存（可视为功能完善），并新增了用于CI对齐测试的vllm-omni-test agent技能。
*   **性能优化**：为Cosmos3 HSDP模块启用了区域编译，以提升性能。
*   **文档更新**：为Voxtral TTS和Qwen3-TTS模型添加了新的硬件配置（如RTX A6000、RTX 4090）和性能基线数据，并修复了文档中的错误链接。
*   **重构**：为DiT（Diffusion Transformer）管道引入了基类，统一了参数声明方式。
*   **清理**：移除了重复的HiDreamI1ImagePipeline代码。
*   **CI/基础设施**：跳过了针对特定Issue的CI检查，并新增了用于测试生成的agent技能。
*   **硬件支持**：为OmniMRotaryEmbedding增加了NPU（神经网络处理器）支持。

### 2. 关键变更点及其与项目整体方向的关系

*   **修复MOSS-TTS音频损坏**：直接解决了多模态服务中文本转语音（TTS）模块的核心质量问题，确保了在批处理场景下音频输出的正确性，这对于提供稳定、可靠的语音服务至关重要。
*   **DreamZero TP & 交叉注意力缓存修复**：修复了图像/视频生成模型（DreamZero）在张量并行（TP）和交叉注意力机制下的缓存问题，这对于支持大规模模型的高效推理和生成质量是必要的。
*   **DiT管道基类重构**：这是对代码架构的深度优化。通过统一参数声明，为未来支持更多基于DiT的图像/视频生成模型（如HiDreamI1、Cosmos等）奠定了更清晰、可扩展的基础，符合项目“易用、快速、廉价”地服务多种模态模型的目标。
*   **新增NPU支持**：扩展了硬件兼容性，使项目能够在除GPU之外的NPU上运行，这有助于降低部署成本并覆盖更广泛的硬件生态，直接呼应了“cheap”和“for everyone”的愿景。
*   **新增CI测试Agent技能**：通过自动化测试生成，提升了代码质量和开发效率，确保新功能或修复不会破坏现有功能，是项目长期健康发展的保障。
*   **文档与性能基线更新**：为Voxtral TTS和Qwen3-TTS提供了具体的硬件配置和性能数据，降低了用户的使用门槛，让用户能快速评估和部署这些模型，体现了项目对“easy”和“fast”的追求。

### 3. 对项目的影响和潜在意义

*   **提升稳定性和可靠性**：MOSS-TTS和DreamZero的Bug修复直接提升了核心模型服务的稳定性，减少了用户在生产环境中遇到问题的概率。
*   **加速模型集成与扩展**：DiT管道的重构是基础设施层面的重要改进，它将显著降低未来集成新图像/视频生成模型（如Stable Diffusion 3、Sora等）的工程成本，加速项目对最新多模态模型的覆盖。
*   **降低部署门槛和成本**：NPU支持使得用户可以利用更便宜的硬件进行推理，而文档中提供的性能基线（如RTX 4090）则为用户提供了明确的硬件选型参考，进一步降低了部署成本。
*   **增强开发者体验**：CI测试Agent和代码清理工作提升了代码库的整洁度和可维护性，为社区贡献者提供了更好的开发环境。

### 4. 值得关注的技术点

*   **区域编译（Regional Compile）**：在Cosmos3 HSDP模块中启用，这是一种针对特定计算区域进行编译优化的技术，可以显著提升模型特定部分的执行效率，是性能优化的高级手段。
*   **DiT管道基类设计**：这是一个典型的设计模式应用。通过抽象基类，定义了统一的接口和参数声明，使得不同DiT模型可以共享核心逻辑，同时允许各自实现特定部分。这是构建可扩展多模态推理引擎的关键。
*   **NPU上的OmniMRotaryEmbedding**：将旋转位置编码（RoPE）适配到NPU架构，表明项目团队正在积极解决不同硬件平台上的算子兼容性问题，这对于实现真正的“多硬件”支持至关重要。

### 5. 结合项目背景，这些提交如何影响项目发展

*   **强化“多模态”核心**：修复TTS和图像生成模型的问题，并重构DiT管道，直接巩固了项目在“omni-modality”（全模态）服务领域的核心能力，确保语音、图像、视频等模态的服务质量。
*   **推动“易用、快速、廉价”目标**：
    *   **易用**：通过文档更新和CI Agent，降低了用户和开发者的使用与贡献门槛。
    *   **快速**：通过性能优化（区域编译）和修复性能相关的Bug（DreamZero缓存），提升了模型推理速度。
    *   **廉价**：通过增加NPU支持，为用户提供了更经济的硬件选择。
*   **构建可持续的工程基础**：代码清理、重构和CI改进是项目长期发展的基石。这些提交表明项目不仅关注功能堆叠，也重视代码质量和架构的健康度，这对于一个快速增长的开源项目至关重要。
*   **扩大硬件生态**：NPU支持是向“for everyone”迈出的重要一步，

## 详细提交记录

### [37a4424](https://github.com/vllm-project/vllm-omni/commit/37a442447ebb474451aa56abd6115d780a38d76e)

- **作者**: yangyonggit
- **时间**: 2026-06-18T22:32:18Z
- **提交信息**: [Cleanup] Remove duplicate HiDreamI1ImagePipeline (fixes #4009) (#4045)

Signed-off-by: leo.yang <leo.yang.engineer@gmail.com>

### [13e9094](https://github.com/vllm-project/vllm-omni/commit/13e9094be092471036a2ef53e20b3b078bdaf60c)

- **作者**: yangyonggit
- **时间**: 2026-06-18T22:27:26Z
- **提交信息**: [Doc] Add 1x RTX A6000 48GB section to Voxtral TTS recipe (#2645) (#4051)

Signed-off-by: leo.yang <leo.yang.engineer@gmail.com>

### [1228a10](https://github.com/vllm-project/vllm-omni/commit/1228a109f09516c4e9323e9d1774b76304a84047)

- **作者**: yangyonggit
- **时间**: 2026-06-18T18:11:51Z
- **提交信息**: [Bugfix] MOSS-TTS: fix cross-request audio corruption under batching (#4415)

Signed-off-by: leo.yang <leo.yang.engineer@gmail.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [8f28b96](https://github.com/vllm-project/vllm-omni/commit/8f28b969e91e00db23ad24e687604f2695a67255)

- **作者**: Honghan Zhu
- **时间**: 2026-06-18T10:57:04Z
- **提交信息**: [Feat] DreamZero fix tp & cross attn cache (#4154)

### [2d22588](https://github.com/vllm-project/vllm-omni/commit/2d2258890b1a3459e1a6b14a0d2255398dac1ae8)

- **作者**: zhumingjue138
- **时间**: 2026-06-18T09:53:34Z
- **提交信息**: [CI] skip ci for issue 4537 (#4538)

Signed-off-by: zhumingjue <zhumingjue@huawei.com>

### [0383fde](https://github.com/vllm-project/vllm-omni/commit/0383fde38a9b2940ade4b479666f84040fcdfe03)

- **作者**: Zening Chen
- **时间**: 2026-06-18T09:31:36Z
- **提交信息**: [Doc] Qwen3-TTS: add 0.6B on 1x RTX 4090 and fix broken links (#4026)

Signed-off-by: Zening Chen <59945561+zeningc@users.noreply.github.com>
Signed-off-by: zeningc <zening.chen@yahoo.com>

### [f75c437](https://github.com/vllm-project/vllm-omni/commit/f75c437a60884691c0da88cbbaec9e1ba27bcec4)

- **作者**: 汪志鹏
- **时间**: 2026-06-18T09:14:18Z
- **提交信息**: [Refactor]Base class for dit pipelines with unified parameter declaration[1/N] (#4225)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [dff8cda](https://github.com/vllm-project/vllm-omni/commit/dff8cda84425cb50cdb2504dc253a960ccbc6317)

- **作者**: wangyu
- **时间**: 2026-06-18T09:01:24Z
- **提交信息**: [SKILLS] Add vllm-omni-test agent skill for CI-aligned test generation (#4434)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <[Your Email]>

### [c782746](https://github.com/vllm-project/vllm-omni/commit/c78274613369a2244c002e8e17c9065e0e60e94e)

- **作者**: Wallbreazzz
- **时间**: 2026-06-18T08:58:40Z
- **提交信息**: Add NPU support for OmniMRotaryEmbedding (#3609)

Signed-off-by: Wallbreazzz <110282866+Wallbreazzz@users.noreply.github.com>

### [db8bc2c](https://github.com/vllm-project/vllm-omni/commit/db8bc2c71d76ddbe475eb291b8bcaab09ca20d02)

- **作者**: Alicia
- **时间**: 2026-06-18T08:56:13Z
- **提交信息**: Update VoxCPM and Qwen3TTS perf baseline. (#4521)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [14d70d9](https://github.com/vllm-project/vllm-omni/commit/14d70d98703f71bcbbc125b3e90a3ad5060c703a)

- **作者**: bjf-frz
- **时间**: 2026-06-18T08:54:05Z
- **提交信息**: [Perf]Enable regional compile for Cosmos3 HSDP blocks (#4485)

Signed-off-by: bjf-frz <frz123db@gmail.com>

---
