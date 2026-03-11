# GitHub Stars 合并报告 - 2026-03-10

**合并日期**: 2026-03-11
**监控日期**: 2026-03-10
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


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1714
- **最后更新**: 2026-03-11T10:40:00Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Ting, PQlet, Crystal-jiang

## AI分析总结

根据您提供的README摘要和提交记录，以下是针对VeOmni项目昨日更新的分析总结：

### 1. 主要更新类型
*   **Bug修复**：提交1和提交2均属于此类，分别修复了分布式训练和模型结构中的问题。
*   **功能新增**：提交3为项目增加了对新模型架构的支持。

### 2. 关键变更点及其与项目整体方向的关系
*   **完善分布式训练流程**（提交1）：修复了`build_parallelize_model()`函数中缺失`broadcast_model_weights_from_rank0`选项的问题。这直接服务于项目“**Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo**”的核心目标，确保了大规模多模态模型分布式训练的正确性和稳定性。
*   **修正多模态模型细节**（提交2）：修正了Qwen3-Omni-MoE模型在VLM（视觉语言模型）训练器中的音频投影层。这表明项目正深入支持复杂的**多模态混合专家模型**，确保不同模态（此处为音频）能正确对齐和集成，是构建“全能（Omni）”模型的关键步骤。
*   **扩展模型支持范围**（提交3）：新增对GLM-5模型在GPU上的支持。这体现了项目作为“**分布式配方动物园（Distributed Recipe Zoo）**”的定位，通过持续集成热门或先进的模型架构（如GLM系列），丰富其生态和实用性。

### 3. 对项目的影响和潜在意义
*   **提升稳定性和可靠性**：两项修复增强了框架在关键训练路径上的鲁棒性，降低了用户使用门槛和训练失败风险。
*   **扩大应用场景与用户基础**：支持GLM-5模型能吸引关注该模型的研究者和开发者，提升项目影响力。
*   **强化项目核心价值**：所有更新都紧密围绕“**提供模型中心化的分布式训练配方**”这一使命，使项目工具链更加完善和可用。

### 4. 值得关注的技术点
*   **模型权重的分布式广播**（提交1）：涉及分布式训练中初始化同步的关键机制，对确保训练一致性至关重要。
*   **多模态MoE模型的结构对齐**（提交2）：反映了处理音频等非视觉模态在统一架构中的具体技术挑战。
*   **对新模型系列的快速集成能力**（提交3）：展现了项目框架的**可扩展性**和团队对业界趋势的快速响应。

### 5. 基于项目背景的提交影响分析
VeOmni旨在成为多模态大模型分布式训练的“配方库”和基础设施。昨日的更新共同推动了这一目标：
*   **提交1和2** 属于“**夯实基础**”，通过修复深层次的框架和模型Bug，提升了现有“配方”的**质量和可信度**，这是开源项目获得长期信任的关键。
*   **提交3** 属于“**拓展生态**”，通过增加对新模型的支持，直接扩大了“配方动物园”的**规模和覆盖度**，使项目能服务于更广泛的模型训练需求。
*   **整体来看**，这些提交体现了项目在**纵向（深度、稳定性）** 和**横向（广度、模型支持）** 上的同步发展，符合一个成熟开源基础设施项目的健康发展路径，即不断巩固核心功能的同时，积极拥抱社区和行业的新进展。

## 详细提交记录

### [083873c](https://github.com/ByteDance-Seed/VeOmni/commit/083873cd269d0faf19f189cbb12d2027edf1ba89)

- **作者**: PQlet
- **时间**: 2026-03-10T21:40:50Z
- **提交信息**: [ckpt] fix: Add missing broadcast_model_weights_from_rank0 option for build_parallelize_model() (#548)

### [01be667](https://github.com/ByteDance-Seed/VeOmni/commit/01be6671300bd88818beb9a812c8fb23d302422c)

- **作者**: Ting
- **时间**: 2026-03-10T13:39:32Z
- **提交信息**: [model] fix: correct audio projection layer for Qwen3-Omni-MoE in VLM trainer (#549)

### [37cf43a](https://github.com/ByteDance-Seed/VeOmni/commit/37cf43ae9084c805b698d836c2939cc89763ed95)

- **作者**: Crystal-jiang
- **时间**: 2026-03-10T09:35:51Z
- **提交信息**: [model] feat: Add glm-5 model support for GPU (#541)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2049
- **最后更新**: 2026-03-11T12:02:26Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: STwangyingrui, LiangLiu

## AI分析总结

根据提供的README摘要和提交记录，以下是对昨日更新的分析总结：

### 1. 主要更新类型
*   **性能优化**：支持环形通信和稀疏计算，旨在提升分布式训练或推理的效率。
*   **功能新增与优化**：为`rs2v shot infer`（推测为视频生成的一个特定模式或模型）增加了流式保存视频、支持部署工作节点的新功能。
*   **Bug修复**：修复了`va_controller`中除零错误，提升了系统稳定性。

### 2. 关键变更点及其与项目整体方向的关系
*   **支持Ring FP4通信和SLA稀疏计算**：这与项目“**Light**X2V”（轻量级视频生成推理框架）的核心目标“**高效、轻量**”高度一致。通过引入低精度通信（FP4）和稀疏计算，直接减少了内存占用和通信开销，是向高性能、低成本推理迈进的关键技术步骤。
*   **`rs2v shot infer`功能增强**：
    *   **流式保存视频**：优化了用户体验和系统资源管理，使视频生成过程更流畅，符合生产环境部署的需求。
    *   **支持部署工作节点**：增强了框架的**可扩展性和部署灵活性**，使其更容易集成到实际的服务器或云服务环境中，与项目作为“推理框架”的定位相符。
    *   **修复除零错误**：提高了框架的**鲁棒性和可靠性**，这是任何成熟框架必须关注的基础。

### 3. 对项目的影响和潜在意义
*   **正向影响**：
    *   **性能提升**：低精度与稀疏化技术有望显著降低推理延迟和硬件成本，拓宽了框架在资源受限场景下的应用潜力。
    *   **功能完善**：流式处理和部署支持的增强，使框架更贴近实际应用场景，降低了用户的使用门槛。
    *   **稳定性增强**：Bug修复提升了框架的健壮性。
*   **潜在意义**：这些更新表明项目正从**基础模型实现**向**高性能、工业化部署的成熟推理框架**深化，关注点从“能否生成”转向“如何更快、更稳、更省地生成”。

### 4. 值得关注的技术点
*   **Ring FP4通信**：在分布式训练/推理中，如何高效组织低精度（4位浮点）数据的环形通信，以平衡通信带宽和计算精度。
*   **SLA稀疏计算**：具体指何种稀疏模式（如结构化稀疏、激活稀疏）及其在视频生成模型中的实现方式，这对保持生成质量的同时提升速度至关重要。
*   **流式视频保存与部署工作节点**：反映了框架在**工程化**和**易用性**方面的设计思路，如何将大模型推理无缝融入现有工作流。

### 5. 基于项目背景的提交影响分析
LightX2V的目标是成为一个**轻量、高效的视频生成推理框架**。昨日的更新完美地服务于这一目标：
*   **强化“轻量”与“高效”**：`Ring FP4`和`SLA稀疏`是直接针对计算和通信瓶颈的“硬核”优化技术，直指降低资源消耗的核心诉求。
*   **完善“推理框架”属性**：`部署工作节点支持`和`流式保存`功能，不再是单纯的模型代码，而是提供了完整的、面向服务的推理解决方案，使框架更“可用”和“易用”。
*   **提升成熟度**：修复`div 0`这类基础错误，表明团队在追求前沿性能的同时，也注重代码的稳定性和产品质量，这对于框架的长期发展和用户信任至关重要。

**总结**：昨日的更新是一次**兼具深度与广度**的迭代。深度上，通过底层通信和计算优化，夯实了框架“高效”的技术根基；广度上，通过增强部署和用户体验功能，拓展了框架作为“产品”的实用性。这标志着LightX2V正朝着一个**技术领先、易于部署、稳定可靠**的工业级视频生成推理框架稳步迈进。

## 详细提交记录

### [b845787](https://github.com/ModelTC/LightX2V/commit/b845787da4857d705718ee7c29b2b124c81fed7c)

- **作者**: STwangyingrui
- **时间**: 2026-03-10T08:34:42Z
- **提交信息**: support ring fp4 comm and sla sparse (#933)

Co-authored-by: wangshankun <wangshankun2011@hotmail.com>

### [08f1f3c](https://github.com/ModelTC/LightX2V/commit/08f1f3c845ddd152afad7f1a8e00e436459d0ebb)

- **作者**: LiangLiu
- **时间**: 2026-03-10T08:34:12Z
- **提交信息**: rs2v shot infer: stream save video, support deploy worker, va_control… (#934)

rs2v shot infer:
1. stream save video
2. support deploy worker
3. va_controller fix div 0 error

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1955
- **最后更新**: 2026-03-10T14:14:46Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

根据提供的仓库信息和提交记录，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了在低版本 `diffusers` 库中出现的“Group Offload”相关错误。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：提交 `ad72867` 解决了当 `diffusers` 版本较低时，`Group Offload` 功能可能无法正常工作的问题。
- **与项目方向的关系**：该项目（VideoX-Fun）是一个面向AIGC视频生成和图像处理的应用集合（如CogVideoX-Fun和Wan-Fun），旨在提供易用、高效的生成式AI体验。修复底层依赖库的兼容性问题，有助于确保应用在不同环境下的稳定运行，符合项目追求**可靠性和用户体验**的整体方向。

### 3. 对项目的影响和潜在意义
- **直接影响**：提升了代码的健壮性，避免因依赖版本不匹配导致的功能失效，特别是对于使用较旧版本 `diffusers` 的用户或部署环境。
- **潜在意义**：减少了用户使用门槛和技术支持负担，有助于扩大项目的适用性和用户基础。

### 4. 值得关注的技术点
- **Group Offload**：这可能是一种内存优化技术，用于在资源受限的设备上高效管理模型加载与计算，常见于大规模生成式模型推理。
- **diffusers 版本兼容性**：突出了对关键依赖库版本的管理，反映了项目对**向后兼容性**的重视，这在开源项目中尤为重要。

### 5. 基于README了解的项目背景，这些提交如何影响项目发展
- **项目背景**：VideoX-Fun 提供基于 Hugging Face Spaces 的在线演示，目标用户可能包括开发者、研究人员及普通爱好者，强调易用性和快速体验。
- **对发展的影响**：
  - **稳定性提升**：通过修复此类底层Bug，增强了项目的可靠性，有利于维护用户信任和口碑。
  - **生态适配**：确保与 `diffusers` 库的广泛版本兼容，使项目能更好地融入现有AI工具链，促进更广泛的采用和集成。
  - **持续维护信号**：即使是小规模修复，也表明项目处于积极维护状态，这对吸引贡献者和用户有正面作用。

**总结**：本次更新虽是一个具体的Bug修复，但通过确保核心功能在多种环境下的稳定性，间接支持了项目的长期目标——提供稳定、易用的AIGC应用体验。

## 详细提交记录

### [ad72867](https://github.com/aigc-apps/VideoX-Fun/commit/ad72867c0f5fef880bcdbc85d5bfdeb2af65965b)

- **作者**: Bubbliiiing
- **时间**: 2026-03-10T07:02:16Z
- **提交信息**: Fix Bug in Group Offload when diffusers version is low. (#474)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5120
- **最后更新**: 2026-03-11T12:07:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
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


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 32995
- **最后更新**: 2026-03-11T11:12:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
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


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 11963
- **最后更新**: 2026-03-11T09:40:58Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Artiprocher, Zhongjie Duan, Hong Zhang

## AI分析总结

根据提供的README摘要和提交记录，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：为LTX2模型添加了默认的负面提示词（negative prompt）。
- **功能增强/优化**：合并了与LTX2.3多参考（multiref）相关的功能改进。

### 2. 关键变更点及其与项目整体方向的关系
- **添加LTX2默认负面提示词**：通过设置默认负面提示词，可以更稳定地引导模型生成高质量内容，减少不良输出。这与项目（DiffSynth-Studio）作为**基于扩散模型的视频/图像合成工具**的定位一致，旨在提升用户体验和生成结果的可靠性。
- **LTX2.3多参考功能合并**：增强了模型在处理多参考输入时的能力，可能支持更复杂的视频合成或编辑任务。这符合项目向**多功能、高性能合成平台**发展的方向，扩展了模型的应用场景。

### 3. 对项目的影响和潜在意义
- **提升易用性和稳定性**：默认负面提示词的加入降低了用户的使用门槛，无需手动配置即可获得更优结果，有助于吸引更广泛的用户群体。
- **增强模型能力**：多参考功能的引入可能提升视频合成的连贯性和多样性，为复杂创意任务（如多视角视频生成）提供支持，增强项目在AI生成内容领域的竞争力。

### 4. 值得关注的技术点
- **负面提示词优化**：在扩散模型中，负面提示词用于抑制不希望的生成内容，其默认设置直接影响生成质量。这一变更反映了对模型提示工程（prompt engineering）的持续优化。
- **多参考（multiref）技术**：可能涉及多输入源（如多段视频或图像）的融合处理，是视频合成领域的前沿方向，值得关注其具体实现（如注意力机制或特征对齐技术）。

### 5. 基于项目背景的提交影响分析
- 项目背景（从README推断）：DiffSynth-Studio是一个专注于**扩散模型合成技术**的开源工具，可能用于视频生成、编辑或风格化。其目标是提供高效、易用的AI创作解决方案。
- **提交如何影响发展**：
  - **功能完善**：这些更新细化了LTX2模型的功能，体现了项目在**模型迭代和用户体验**上的持续投入，有助于巩固其作为专业合成工具的地位。
  - **技术前沿跟进**：多参考功能的加入显示项目正探索**更复杂的合成任务**，与AI生成内容的行业趋势（如长视频生成、交互式编辑）同步，可能为未来功能（如动态场景合成）奠定基础。

---

**总结**：昨日更新以功能优化为主，通过添加默认负面提示词和增强多参考能力，提升了DiffSynth-Studio的实用性和技术深度。这些变更符合项目作为扩散模型合成平台的发展方向，既改善了基础体验，也为高级应用场景做了铺垫。

## 详细提交记录

### [c927062](https://github.com/modelscope/DiffSynth-Studio/commit/c927062546de3e628576ef0676b80e1a332713cf)

- **作者**: Hong Zhang
- **时间**: 2026-03-10T09:31:05Z
- **提交信息**: Merge pull request #1343 from mi804/ltx2.3_multiref

Ltx2.3 multiref

### [f3ebd6f](https://github.com/modelscope/DiffSynth-Studio/commit/f3ebd6f714be8a59fac2f438eb7ccade964b89bc)

- **作者**: Zhongjie Duan
- **时间**: 2026-03-10T07:10:51Z
- **提交信息**: Merge pull request #1342 from modelscope/ltx2-default-prompt

add default negative prompt of ltx2

### [959471f](https://github.com/modelscope/DiffSynth-Studio/commit/959471f0830b1bd4a0db2ae4c1a5de3aafb64f63)

- **作者**: Artiprocher
- **时间**: 2026-03-10T07:10:03Z
- **提交信息**: add default negative prompt of ltx2

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24323
- **最后更新**: 2026-03-11T11:44:40Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 15
- **主要提交者**: Yuan Luo, Ziang Li, Qiaolin Yu

## AI分析总结

根据提供的提交记录和README摘要（SGLang项目是一个用于高效运行大型语言模型的框架），以下是昨日更新的要点总结：

---

### 1. **主要更新类型**
- **Bug修复**：多个提交修复了CI/CD、NPU、扩散模型、内存重复等具体问题。
- **性能优化**：集成FlashInfer v0.6.4、优化CUDA图、AMD FP8预填充等，提升推理效率。
- **功能新增**：支持DeepSeek 3.2和GlmMoeDsa模型、音频解码器替换、扩散模型多提示映射等。
- **重构/代码整理**：重构JIT内核（如旋转嵌入、缓存使用），统一入口点，清理基准测试命名。
- **硬件支持扩展**：增强对NPU、AMD、macOS等平台的支持和兼容性修复。

---

### 2. **关键变更点及其与项目整体方向的关系**
- **性能与效率提升**（如提交4、7、16）：集成FlashInfer的FP8 GEMM和MoE优化，启用分段CUDA图，符合SGLang作为**高效LLM推理框架**的核心目标，旨在降低延迟、提高吞吐量。
- **多硬件平台支持**（如提交6、12-14、16）：修复NPU、AMD和macOS的兼容性问题，体现项目向**异构计算生态扩展**的趋势，增强框架的普适性和部署灵活性。
- **模型与功能扩展**（如提交3、9、17、19）：新增对DeepSeek 3.2等模型的支持、改进扩散模型的多提示处理、替换音频解码器，显示项目在**多模态和模型覆盖**上的持续拓展。
- **代码健康度与维护**（如提交1、11、15、21-22）：修复CI/CD问题、重构内核代码、统一接口，有助于**提升开发效率和代码可维护性**，支撑长期迭代。

---

### 3. **对项目的影响和潜在意义**
- **用户体验**：Bug修复（如NPU精度、扩散模型LoRA）直接提升稳定性和功能可靠性；性能优化可能带来更快的推理速度。
- **开发者体验**：代码重构和CI修复使贡献和测试更顺畅；统一内核接口降低了开发复杂度。
- **生态扩展**：新增模型支持和多硬件优化有助于吸引更广泛的用户和社区参与者。
- **技术债务**：重构和清理有助于减少长期维护成本，但需注意变更可能引入短期兼容性风险（如提交18的还原操作）。

---

### 4. **值得关注的技术点**
- **FlashInfer v0.6.4集成**（提交4）：引入FP8 GEMM和路由MoE，可能显著提升高精度计算和MoE模型的推理性能。
- **NPU自定义内核与优化**（提交12-14）：针对华为昇腾等NPU的定制化优化，反映对国产硬件的重点支持。
- **重叠安全的logprob返回**（提交3）：在spec v2中支持安全的重叠logprob计算，提升采样和调试能力。
- **JIT内核重构系列**（提交11、15、21-22）：系统性重构内核代码，可能为未来性能优化和功能扩展奠定基础。
- **扩散模型多提示修复**（提交19）：改进多提示到图像的映射，增强多模态生成任务的准确性。

---

### 5. **基于项目背景的提交影响分析**
SGLang旨在成为**高效、可扩展的LLM服务框架**。昨日更新整体强化了这一方向：
- **性能优先**：通过FlashInfer、CUDA图、FP8集成等优化，直接支撑**低延迟、高吞吐**的核心竞争力。
- **扩展性与兼容性**：支持新模型（如DeepSeek 3.2）、多硬件（NPU/AMD/macOS）和多模态（扩散模型、音频），帮助项目**覆盖更广泛的应用场景和部署环境**。
- **代码质量与维护**：重构和CI修复确保项目在快速迭代中保持**稳定和可维护性**，这对开源项目的长期健康至关重要。
- **社区与生态**：修复用户-facing问题（如扩散模型LoRA、多提示映射）和增加模型支持，有助于**提升用户满意度和社区活跃度**。

---

**总结**：昨日更新以**性能优化、多平台兼容性提升和代码重构**为主，紧密围绕SGLang作为高效LLM推理框架的定位，同时扩展模型和硬件支持以增强生态竞争力。这些变更既解决了即时问题，也为长期发展奠定了技术基础。

## 详细提交记录

### [eea7f8d](https://github.com/sgl-project/sglang/commit/eea7f8de41c574f757f48489b725604f7fad75ec)

- **作者**: Alison Shao
- **时间**: 2026-03-10T23:00:31Z
- **提交信息**: [CI] Fix B200 runner label for scheduled runs (#20297)

Co-authored-by: Alison Shao <alisonshao@Mac.attlocal.net>

### [f32882c](https://github.com/sgl-project/sglang/commit/f32882cee5b3b46bbe70a5fc5b5b3f797dd9d287)

- **作者**: Alison Shao
- **时间**: 2026-03-10T22:40:52Z
- **提交信息**: [CI] Relax Eagle infer_b spec accept length threshold (#20300)

Co-authored-by: Alison Shao <alisonshao@Mac.attlocal.net>

### [09a118f](https://github.com/sgl-project/sglang/commit/09a118fafed0577756413018cd4a3cbee342a1e3)

- **作者**: Qiaolin Yu
- **时间**: 2026-03-10T22:38:27Z
- **提交信息**: Support return_logprob for spec v2 (overlap safe) (#19801)

Co-authored-by: Ratish1 <ratish1501@gmail.com>
Co-authored-by: Ratish1 <formula733@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [76ee4bb](https://github.com/sgl-project/sglang/commit/76ee4bb98c64e9dc95ceb330bb12fd1cda405e17)

- **作者**: Ziang Li
- **时间**: 2026-03-10T22:37:57Z
- **提交信息**: [FlashInfer v0.6.4] [RL] Integrate FlashInfer mxfp8 gemm, MoE, and routed MoE (#19537)

### [bd460e9](https://github.com/sgl-project/sglang/commit/bd460e9565c984bc7b95de1126171c939dbb4933)

- **作者**: Qiaolin Yu
- **时间**: 2026-03-10T22:04:57Z
- **提交信息**: add logprob related params in bench_serving (#20218)

### [db97f19](https://github.com/sgl-project/sglang/commit/db97f193b7212cdcc2b462416f82a80e3d8fe579)

- **作者**: R0CKSTAR
- **时间**: 2026-03-10T20:11:07Z
- **提交信息**: [diffusion][llm] macOS support (#19549)

Signed-off-by: Xiaodong Ye <yeahdongcn@gmail.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [a3d88a2](https://github.com/sgl-project/sglang/commit/a3d88a247b1744ff85cb92aa61150318d22e268d)

- **作者**: Qiaolin Yu
- **时间**: 2026-03-10T19:50:57Z
- **提交信息**: Enable piecewise-cuda-graph when logprob_start_len = -1 (#19453)

### [031d0a2](https://github.com/sgl-project/sglang/commit/031d0a2aad444b61c3bbe04e67dda84677b2289d)

- **作者**: fxmarty-amd
- **时间**: 2026-03-10T17:34:56Z
- **提交信息**: [Qwen-MOE] Fix memory duplication issues in case layers weights are re-assigned during weight loading (#18255)

### [11d9c36](https://github.com/sgl-project/sglang/commit/11d9c36c2ffc4ba4117bb250ebb5009ed6786247)

- **作者**: Xinyuan Tong
- **时间**: 2026-03-10T17:26:29Z
- **提交信息**: Replace soundfile+torchaudio with torchcodec AudioDecoder in load_audio (#20190)

### [e1f0b31](https://github.com/sgl-project/sglang/commit/e1f0b3181a2e73f090b1a3900f7692a0b6bcef18)

- **作者**: Mick
- **时间**: 2026-03-10T17:21:54Z
- **提交信息**: [diffusion] fix: adjust convert_hf_to_fp8 to be compatible with more dits (#20281)

### [60cc062](https://github.com/sgl-project/sglang/commit/60cc06297ef72c9db013c02177a85df75626f054)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-10T13:37:41Z
- **提交信息**: [4/n jit_kernel restruct] speed up CI tests and add benchmark workflow (#20268)

### [5a7c1b8](https://github.com/sgl-project/sglang/commit/5a7c1b8ec632a12f8984a3df1ef75c38e2174c13)

- **作者**: JiaruiChang5268
- **时间**: 2026-03-10T13:08:37Z
- **提交信息**: [NPU] replace swiglu with custom kernel

### [9884957](https://github.com/sgl-project/sglang/commit/9884957c07ce0a98fad34ea0055803594c459cb1)

- **作者**: Hexq0210
- **时间**: 2026-03-10T12:03:26Z
- **提交信息**: [NPU] Bugfix  for qwen35 on NPU (#19756)

### [6ed996b](https://github.com/sgl-project/sglang/commit/6ed996bf65b2e29d871e7dd306d9670197ecbb82)

- **作者**: heziiop
- **时间**: 2026-03-10T11:26:46Z
- **提交信息**: [bugfix] disable share input buffer feature on npu due to accuracy issue (#19507)

### [51d9d34](https://github.com/sgl-project/sglang/commit/51d9d34977582dc565c784e4435cf23cf3ea0640)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-10T09:49:57Z
- **提交信息**: [2/n jit_kernel restruct] unify rotary embedding entrypoints under rope.py (#20247)

### [6407891](https://github.com/sgl-project/sglang/commit/6407891b4fefc819fd2af1f2db098c6b25f4420b)

- **作者**: Thomas Wang
- **时间**: 2026-03-10T09:49:47Z
- **提交信息**: [AMD] Fp8 prefill integration with radix cache path for dpsk models (#20187)

### [751c454](https://github.com/sgl-project/sglang/commit/751c4540990152bc045d44859ca1498d34337750)

- **作者**: Yuan Luo
- **时间**: 2026-03-10T09:12:58Z
- **提交信息**: Add DeepSeek3.2 and GlmMoeDsa into moe tune (#18876)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [ac07a6d](https://github.com/sgl-project/sglang/commit/ac07a6d43980ab310ebd2b86fe005033ade64da3)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-10T08:58:48Z
- **提交信息**: Revert "[Scheduler] Decouple `maybe_send_health_check_signal` from `process_batch_result`" (#20259)

### [8cd1de3](https://github.com/sgl-project/sglang/commit/8cd1de3354d032bb1527c0db7b2a944e838fc368)

- **作者**: Lancer
- **时间**: 2026-03-10T08:58:21Z
- **提交信息**: [diffusion] fix: map each prompt to corresponding image in multi-prompt scenario (#20081)

Signed-off-by: Lancer <maruixiang6688@gmail.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [2c20031](https://github.com/sgl-project/sglang/commit/2c2003158f484728c34d6bad737733df903f0d03)

- **作者**: Lancer
- **时间**: 2026-03-10T08:57:01Z
- **提交信息**: [diffusion] fix: fix flux2 lora (#20200)

Signed-off-by: Lancer <maruixiang6688@gmail.com>

### [8517da5](https://github.com/sgl-project/sglang/commit/8517da5d087049bb60d5f3e9e3e3ff5392c723e8)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-10T08:39:03Z
- **提交信息**: [3/n jit_kernel restruct] Clean up benchmark naming and benchmarking helpers (#20250)

### [c812504](https://github.com/sgl-project/sglang/commit/c812504b928252c7933fed602ceaa40042eac7a9)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-10T07:53:43Z
- **提交信息**: [1/n jit_kernel restruct] unify cache usage and clean up naming in ngram_embedding (#20244)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1080
- **最后更新**: 2026-03-11T11:40:17Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据提供的README摘要和提交记录，以下是针对 `vipshop/cache-dit` 仓库昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增对 FireRed-Image-Edit-1.1 模型的支持。
- **文档更新**：修复了注意力机制（attn）和额外并行（extra parallel）相关的文档。
- **重构/API变更**：弃用 `parallel_kwargs` 参数，可能涉及内部API清理或优化。

### 2. 关键变更点及其与项目整体方向的关系
- **支持 FireRed-Image-Edit-1.1**：该项目作为PyTorch原生推理引擎，专注于加速DiTs（Diffusion Transformers）。新增对特定模型的支持，直接符合其“混合缓存加速与大规模并行”的目标，扩展了引擎的适用性和实用性。
- **弃用 `parallel_kwargs`**：这可能意味着项目在并行化接口上进行了简化或标准化，以提升易用性和维护性，与“大规模并行”的核心方向一致。
- **文档修复**：更新了注意力机制和并行相关的文档，有助于用户更好地理解和使用这些高级功能，降低学习成本。

### 3. 对项目的影响和潜在意义
- **模型生态扩展**：支持 FireRed-Image-Edit-1.1 增强了项目的模型兼容性，可能吸引更多用户或贡献者。
- **API 演进**：弃用 `parallel_kwargs` 可能带来短期适配成本，但长期看有助于代码库的清晰度和稳定性。
- **用户体验提升**：文档修复减少了使用障碍，特别是对于并行化等复杂特性。

### 4. 值得关注的技术点
- **FireRed-Image-Edit-1.1 集成**：可能涉及模型架构适配、缓存策略优化或并行计算调整，具体实现细节未在提交中说明，但值得后续关注。
- **并行化改进**：弃用 `parallel_kwargs` 可能暗示并行配置方式的变更，例如转向更统一的参数传递机制。

### 5. 基于项目背景的提交影响分析
- **项目背景**：Cache-DiT 是一个专注于 DiTs 推理加速的 PyTorch 引擎，通过混合缓存和大规模并行提升性能。
- **发展影响**：
  - **功能增强**：新增模型支持直接服务于项目目标，即提供高效、通用的 DiT 推理方案，可能提升其在图像编辑等场景的竞争力。
  - **代码质量**：API 清理和文档更新有助于项目成熟度提升，促进社区协作和长期维护。
  - **生态建设**：持续集成新模型和优化用户体验，有助于扩大项目影响力和采用率。

**总结**：昨日更新以功能扩展和代码维护为主，既强化了项目的实用性（支持新模型），又优化了开发体验（文档和API清理），整体上推动了项目向更稳定、易用和功能丰富的方向发展。

## 详细提交记录

### [b4ee4e6](https://github.com/vipshop/cache-dit/commit/b4ee4e6d4fb9a287b8fe4da459cd5c5afa317579)

- **作者**: DefTruth
- **时间**: 2026-03-10T13:14:33Z
- **提交信息**: feat: support FireRed-Image-Edit-1.1 (#854)

### [2e638a3](https://github.com/vipshop/cache-dit/commit/2e638a3eda87835ac23d8a9a7b836a02ff95737d)

- **作者**: DefTruth
- **时间**: 2026-03-10T12:44:51Z
- **提交信息**: feat: support FireRed-Image-Edit-1.1 (#853)

* chore: fix attn & extra parallel docs

* chore: fix attn & extra parallel docs

* feat: support FireRed-Image-Edit-1.1

* feat: support FireRed-Image-Edit-1.1

* feat: support FireRed-Image-Edit-1.1

### [9e0cf1c](https://github.com/vipshop/cache-dit/commit/9e0cf1c6bdee4703b4dd379244e401dc51940247)

- **作者**: DefTruth
- **时间**: 2026-03-10T12:13:09Z
- **提交信息**: chore: fix attn & extra parallel docs (#852)

* chore: fix attn & extra parallel docs

* chore: fix attn & extra parallel docs

### [ea4399a](https://github.com/vipshop/cache-dit/commit/ea4399a330ee6a788bb00212a6abbcaeebb03923)

- **作者**: DefTruth
- **时间**: 2026-03-10T10:25:46Z
- **提交信息**: chore: update README (#851)

### [ca87950](https://github.com/vipshop/cache-dit/commit/ca879503323bfa76cba721a7fe8ed4a07cf2c0b0)

- **作者**: DefTruth
- **时间**: 2026-03-10T10:10:33Z
- **提交信息**: chore: fix context parallel docs (#850)

### [3c25ad2](https://github.com/vipshop/cache-dit/commit/3c25ad201e675a5d3e3b2492e82b51bc0e0a761e)

- **作者**: DefTruth
- **时间**: 2026-03-10T09:58:06Z
- **提交信息**: feat: deprecated parallel_kwargs (#849)

* feat: deprecated parallel_kwargs

* feat: deprecated parallel_kwargs

* feat: deprecated parallel_kwargs

* feat: deprecated parallel_kwargs

* feat: deprecated parallel_kwargs

* feat: deprecated parallel_kwargs

* feat: deprecated parallel_kwargs

* feat: deprecated parallel_kwargs

* feat: deprecated parallel_kwargs

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 72829
- **最后更新**: 2026-03-11T12:11:55Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 18
- **主要提交者**: SoluMilken, Mark McLoughlin, Srinivasoo7

## AI分析总结

根据提供的提交记录和项目README背景（vLLM是一个致力于“简单、快速、经济的LLM服务”的项目），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及多个核心组件（如KV缓存、模型支持、异步调度、HTTP请求等）。
- **性能优化**：主要集中在ROCm平台和稀疏注意力（Sparse MLA）的CUDA图支持。
- **功能新增/增强**：包括KV卸载策略、gRPC服务分离、模型Runner V2的测试与修复。
- **CI/测试改进**：新增测试、调整测试策略、更新工具版本。
- **代码质量/重构**：简化核心逻辑、修复拼写错误、改进错误信息。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向（易用、快速、经济）的关系 |
| :--- | :--- |
| **ROCm性能优化**（#35719, #34304） | 提升AMD硬件上的推理速度（**快速**），扩大硬件支持范围（**经济**）。 |
| **KV缓存与卸载优化**（#36521, #35342） | 优化内存管理，提升吞吐量并降低延迟（**快速、经济**）。 |
| **Model Runner V2 多项修复**（#36041, #36588, #36580等） | 完善新一代推理引擎，为未来更高性能与灵活性打下基础（**快速、易用**）。 |
| **多模型/后端Bug修复**（TRT-LLM, FunASR, Qwen2.5-VL, Mamba等） | 增强框架的稳定性和模型兼容性（**易用**）。 |
| **gRPC服务分离**（#36169） | 改善服务部署的模块化和可维护性（**易用**）。 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：大量Bug修复直接提高了生产环境的可靠性。
- **性能边界拓展**：对ROCm和稀疏注意力的优化，意味着vLLM在更多硬件和复杂模型上能保持高性能。
- **架构演进**：Model Runner V2的持续投入和gRPC的重构，表明项目正在为更复杂、更高效的推理场景做准备。
- **社区与协作**：提交来自AMD、Meta、IBM、阿里、Hugging Face等多方贡献者，显示生态活跃。

### 4. 值得关注的技术点
- **稀疏注意力（Sparse MLA）的CUDA图支持**（#35719, #36519）：这是实现长上下文、高性能推理的关键技术。
- **KV卸载策略A**（#35342）：通过智能管理CPU/GPU内存交换，可能显著降低大模型服务的内存成本。
- **Model Runner V2的细节**：如使用未填充的token数计算注意力元数据（#36626），体现了对性能极致的追求。
- **编译与functorch配置**（#36582）：涉及PyTorch编译栈的深度集成，影响部署效率。

### 5. 基于项目背景的提交影响分析
vLLM的核心目标是**降低LLM服务的门槛和成本**。昨日的更新紧密围绕这一目标：
- **追求“快速”**：通过ROCm优化、KV缓存逻辑简化、Sparse MLA支持等，持续压榨硬件性能。
- **保障“易用”**：修复众多模型和前端（如HTTP状态检查、处理器签名）的Bug，减少用户踩坑。
- **实现“经济”**：KV卸载策略和更高效的内存管理，直接指向降低运营所需的GPU内存和成本。
- **夯实基础**：大量的CI测试和代码质量改进，确保了项目在快速迭代中的健康度，这是大规模服务框架长期发展的关键。

**总结**：昨日更新是一次以**修复和优化**为主的常规推进，重点在于**巩固核心性能、扩大硬件支持、完善新架构（Model Runner V2）**，这些工作都在稳步推动vLLM向着更稳定、更高效、更通用的生产级LLM推理引擎迈进。

## 详细提交记录

### [81939e7](https://github.com/vllm-project/vllm/commit/81939e7733642f583d1731e5c9ef69dcd457b5e5)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-10T23:45:27Z
- **提交信息**: [ROCm][CI] Making some tests optional to reduce workload (#36090)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [195d1ca](https://github.com/vllm-project/vllm/commit/195d1ca3e8b1662e5df88b159a4306c48e1b0b5c)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-10T22:38:45Z
- **提交信息**: [Minor] Enhance error message for TRTLLM decode uniformity check (#36609)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [8d983d7](https://github.com/vllm-project/vllm/commit/8d983d7cd661aae1ac8781f67fbbff017db4d0af)

- **作者**: Nick Hill
- **时间**: 2026-03-10T21:55:21Z
- **提交信息**: [Model Runner V2] Add initial CI tests (#36041)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [65b2f40](https://github.com/vllm-project/vllm/commit/65b2f405dca824adad17a42a71c908c6ebbcfd9a)

- **作者**: Nick Hill
- **时间**: 2026-03-10T20:20:02Z
- **提交信息**: [Core] Simplify core kv-cache blocks initialization logic (#36521)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [2a68464](https://github.com/vllm-project/vllm/commit/2a68464c5bf1a26821afe76cf49dc53f75b87e98)

- **作者**: Nick Hill
- **时间**: 2026-03-10T18:17:26Z
- **提交信息**: [Test] `test_async_scheduling.py` improvements (#36340)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [bdd8981](https://github.com/vllm-project/vllm/commit/bdd8981dab8d8c6ae88a3f605d04ec5243088e5a)

- **作者**: Zhengxu Chen
- **时间**: 2026-03-10T16:34:35Z
- **提交信息**: [compile] Apply stored functorch config while finalizing loaded artifacts. (#36582)

Signed-off-by: zhxchen17 <zhxchen17@fb.com>

### [f088a83](https://github.com/vllm-project/vllm/commit/f088a831dd6c35d995c4232cc2462c024c61925b)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-10T16:30:56Z
- **提交信息**: [Model Runner V2] Use unpadded num_tokens for PW CUDA graph attn metadata (#36626)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [f83b933](https://github.com/vllm-project/vllm/commit/f83b933b84b85ee54121575fc347881b35090616)

- **作者**: Harry Mellor
- **时间**: 2026-03-10T16:18:28Z
- **提交信息**: [CI] Bump `mypy` version to 1.19.1 (#36104)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [82f3f30](https://github.com/vllm-project/vllm/commit/82f3f30e266e24b26c46916a8c9daaea7d5e32bd)

- **作者**: Pleaplusone
- **时间**: 2026-03-10T16:14:35Z
- **提交信息**: [ROCm][Perf] Enable `sparse_mla`'s cudagraph on ROCm platform (#35719)

Signed-off-by: ganyi <ygan@amd.com>

### [9095cbb](https://github.com/vllm-project/vllm/commit/9095cbbfb6f68f3f7abc7f55c74768e9f7b1d0a7)

- **作者**: Matthew Bonanni
- **时间**: 2026-03-10T16:14:31Z
- **提交信息**: [Bugfix][Sparse MLA] report indexer CG support properly (#36519)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [721ae79](https://github.com/vllm-project/vllm/commit/721ae79f50c5f85b301d05f1db71372b1ca85dd6)

- **作者**: Hashem Hashemi
- **时间**: 2026-03-10T16:14:27Z
- **提交信息**: Improvements to wvSplitKrc skinny GEMM solution (#34304)

Signed-off-by: Hashem Hashemi <hashem.hashemi@amd.com>

### [aefc59f](https://github.com/vllm-project/vllm/commit/aefc59f088665b23c0285c7f77c32b365efaa5dc)

- **作者**: AllenDou
- **时间**: 2026-03-10T15:14:21Z
- **提交信息**: FunASR model bugfix (#36633)

Signed-off-by: zixiao <shunli.dsl@alibaba-inc.com>
Co-authored-by: zixiao <shunli.dsl@alibaba-inc.com>

### [d88f28d](https://github.com/vllm-project/vllm/commit/d88f28da05b12bc7d63ebe3dcedf445ecb274343)

- **作者**: Harry Mellor
- **时间**: 2026-03-10T15:03:18Z
- **提交信息**: Fix `hf_override_fn` when it modifies `model_type` (#35200)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [106ff69](https://github.com/vllm-project/vllm/commit/106ff69c4eb4921d33341a96b9c3d6db9d12ba76)

- **作者**: Srinivasoo7
- **时间**: 2026-03-10T14:43:40Z
- **提交信息**: feat(kv-offload): Strategy A — StoreReusedOffloadingManager gates CPU stores on reuse frequency (#35342)

Signed-off-by: srinivas_oo7 <Sriusa4414@gmail.com>
Signed-off-by: Sriusa4414@gmail.com
Signed-off-by: Srinivasoo7 <158864704+Srinivasoo7@users.noreply.github.com>
Co-authored-by: srinivas_oo7 <sklinkedin0120@gmail.com>
Co-authored-by: Srinivasoo7 <158864704+Srinivasoo7@users.noreply.github.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [ca5fb4b](https://github.com/vllm-project/vllm/commit/ca5fb4bbd85244fafba72fb91523c657025998a3)

- **作者**: Jiangyun Zhu
- **时间**: 2026-03-10T14:39:01Z
- **提交信息**: [Bugfix] Avoid merging empty-only partitions into splitting-op subgraphs (#36595)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [cf88b23](https://github.com/vllm-project/vllm/commit/cf88b23749187b9a31406925d3f9e966fc4c566b)

- **作者**: Alvin Tang
- **时间**: 2026-03-10T14:22:40Z
- **提交信息**: fix: check HTTP status in batch read_file to prevent silent failures (#36397)

Signed-off-by: gambletan <ethanchang32@gmail.com>
Co-authored-by: gambletan <ethanchang32@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [a3189a0](https://github.com/vllm-project/vllm/commit/a3189a08b0d3de44dd6d49c5d883abf29ac1e6fa)

- **作者**: wang.yuqi
- **时间**: 2026-03-10T13:32:25Z
- **提交信息**: [Model] Consolidate score logic by introduce score_type (#36479)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [409c4e6](https://github.com/vllm-project/vllm/commit/409c4e632d58acc7f2a2f66e7554776c78bb65ad)

- **作者**: SoluMilken
- **时间**: 2026-03-10T13:25:37Z
- **提交信息**: [Misc] fix typo: homogenous-> homogeneous (2 lines change) (#36508)

Signed-off-by: SoluMilken <ypiheyn.imm02g@g2.nctu.edu.tw>

### [8850738](https://github.com/vllm-project/vllm/commit/8850738b700cca34448fbafbc8ac41bcad5a2e17)

- **作者**: Raushan Turganbay
- **时间**: 2026-03-10T13:20:47Z
- **提交信息**: [Bugfix] Fix processor signature (#36630)

Signed-off-by: raushan <raushan@huggingface.co>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [2348603](https://github.com/vllm-project/vllm/commit/234860399b9d390bf59bfe1f19c2e2304ac5c806)

- **作者**: Mark McLoughlin
- **时间**: 2026-03-10T13:20:41Z
- **提交信息**: [Frontend][Core] Revert "Add shutdown timeout" (#34730 and #36270) (#36628)

Signed-off-by: Mark McLoughlin <markmc@redhat.com>

### [c885100](https://github.com/vllm-project/vllm/commit/c88510083b8d6b4fa7a42ae29bc27ff6adc181ee)

- **作者**: Harry Mellor
- **时间**: 2026-03-10T12:05:34Z
- **提交信息**: Fix Qwen2.5-VL test for Transformers v5 (#36532)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [4ff8c3c](https://github.com/vllm-project/vllm/commit/4ff8c3c8f9ece010a1d0e376f5cc1b468b95f366)

- **作者**: Vadim Gimpelson
- **时间**: 2026-03-10T10:32:20Z
- **提交信息**: [BUGFIX][Mamba][Qwen3.5] Zero freed SSM cache blocks on GPU (#35219)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>

### [507ddbe](https://github.com/vllm-project/vllm/commit/507ddbe9927f421a1d574b283d1611044859a30d)

- **作者**: Chang Su
- **时间**: 2026-03-10T10:29:59Z
- **提交信息**: feat(grpc): extract gRPC servicer into smg-grpc-servicer package, add --grpc flag to vllm serve (#36169)

Signed-off-by: Chang Su <chang.s.su@oracle.com>
Co-authored-by: Nick Hill <nhill@redhat.com>

### [ddbb0d2](https://github.com/vllm-project/vllm/commit/ddbb0d230a3592106ac9f5f7f4e9a861863fcbee)

- **作者**: Nick Hill
- **时间**: 2026-03-10T07:24:58Z
- **提交信息**: [Model Runner V2] Fix mm input embeddings lookup (#36588)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [9efc3bd](https://github.com/vllm-project/vllm/commit/9efc3bdcd6749f6d0ba26b12aee27cc8829c6f93)

- **作者**: Nick Hill
- **时间**: 2026-03-10T07:23:42Z
- **提交信息**: [Model Runner V2] Fix `_compute_slot_mappings_kernel` for chunked prefill (#36580)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-11
**监控日期**: 2026-03-10
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 3011
- **最后更新**: 2026-03-11T12:07:38Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Daniel Huang, Juan Pablo Zuluaga, Zhou Taichang

## AI分析总结

根据 `vllm-omni` 仓库的 README 摘要（“Easy, fast, and cheap omni-modality model serving for everyone”）和昨日提交记录，分析总结如下：

### 1. 主要更新类型
- **性能优化**：针对 Qwen3-omni 模型的核心推理路径进行了重构和优化。
- **功能新增**：为 Qwen3TTS 模型增加了动态 TTFA（Time To First Audio）功能。
- **Bug修复**：修复了与 vLLM 0.17.0 的兼容性问题。
- **文档更新**：更新了安装说明。
- **CI/CD 与测试增强**：增加了测试标记和服务器启动检查。
- **功能回退**：回退了 Stable Audio Diffusion 的在线服务及相关端点。

### 2. 关键变更点及其与项目整体方向的关系
- **Qwen3-omni 性能优化**：通过重构代码预测器、引入重预填充（re-prefill）和 SDPA（Scaled Dot-Product Attention），并消除解码热路径中的 CPU 往返，**直接提升了推理速度和效率**，紧扣项目“fast”和“cheap”的目标。
- **Qwen3TTS 动态 TTFA**：基于 Code2Wav 负载实现，**旨在改善语音合成的首次响应时间**，提升用户体验，符合“easy”和“omni-modality”的服务宗旨。
- **vLLM 兼容性修复**：确保音频多模态（mimo-audio）功能在最新 vLLM 版本上稳定运行，**维护了项目核心依赖的生态兼容性**。
- **Stable Audio Diffusion 回退**：可能由于稳定性、性能或架构问题暂时撤下该功能，**体现了对生产环境稳定性的谨慎态度**。
- **文档与测试更新**：**降低了用户和开发者的使用与贡献门槛**，支持项目“for everyone”的愿景。

### 3. 对项目的影响和潜在意义
- **正面影响**：
    - **显著提升 Qwen 系列模型的推理性能**，降低服务延迟与成本。
    - **增强语音合成的响应速度**，改善多模态交互体验。
    - **保持与上游 vLLM 的同步**，避免技术债务。
    - **完善项目基础设施**，提高代码质量和开发效率。
- **潜在风险**：
    - Stable Audio Diffusion 功能的回退可能影响部分用户，需关注后续重新引入的计划。

### 4. 值得关注的技术点
- **“重预填充 + SDPA”优化**：可能针对长序列或特定注意力模式进行了深度优化，是提升大模型推理性能的关键技术。
- **消除解码热路径的 CPU 往返**：通过减少 CPU-GPU 通信开销来提升吞吐量，是高性能推理服务的常见优化手段。
- **基于负载的动态 TTFA**：体现了对服务质量和资源利用率的精细化控制。
- **与 vLLM 0.17.0 的兼容性适配**：反映了项目紧密跟随核心引擎迭代，并及时整合变化。

### 5. 基于项目背景的提交影响分析
`vllm-omni` 旨在为所有人提供**简单、快速、经济的全模态模型服务**。昨日的提交整体上**强力推进了这一目标**：
- **性能优化与功能新增** 直接使服务更“快”和“易用”，并覆盖了视觉-语言（Qwen3-omni）和语音（Qwen3TTS）模态，强化了“全模态”能力。
- **Bug修复与兼容性维护** 确保了服务的稳定性和可靠性，这是“为所有人服务”的基础。
- **文档与测试改进** 降低了使用和参与门槛，促进了社区发展。
- **功能回退** 虽然短期收缩，但体现了对生产质量的重视，长期有利于建立可信赖的服务生态。

**总结**：昨日更新以**性能优化和体验增强**为核心，同时夯实了项目的基础设施与兼容性，是朝着“高效、易用、稳定的全模态服务平台”目标的一次扎实迭代。

## 详细提交记录

### [2ee4a07](https://github.com/vllm-project/vllm-omni/commit/2ee4a07adb836a32bdba33376957b579e0871e94)

- **作者**: Junhong Liu
- **时间**: 2026-03-10T23:52:21Z
- **提交信息**: [Refactor][Perf] Qwen3-omni: code predictor with re-prefill + SDPA and eliminate decode hot-path CPU round-trips (#1758)

Signed-off-by: Junhong Liu <98734602+LJH-LBJ@users.noreply.github.com>

### [1d0a97f](https://github.com/vllm-project/vllm-omni/commit/1d0a97f0d1c6e84b97e21796cbd1fee2d7be8640)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-03-10T21:02:33Z
- **提交信息**: [feat][Qwen3TTS] Simple dynamic TTFA based on Code2Wav load (#1714)

Signed-off-by: pablo <pablo@agigo.ai>
Co-authored-by: pablo <pablo@agigo.ai>

### [2fdc647](https://github.com/vllm-project/vllm-omni/commit/2fdc647ed759bbadfa1dbb6912fda079844918a6)

- **作者**: Baoyuan Qi
- **时间**: 2026-03-10T20:57:26Z
- **提交信息**: [BUGFIX] Add compatibility for mimo-audio with vLLM 0.17.0 (#1752)

Signed-off-by: Baoyuan Qi <qibaoyuan@xiaomi.com>

### [4027534](https://github.com/vllm-project/vllm-omni/commit/4027534dbf1fde8f4dcd6b0526c71e068aa66360)

- **作者**: Hongsheng Liu
- **时间**: 2026-03-10T14:40:48Z
- **提交信息**: Revert "Add online serving to Stable Audio Diffusion and introduce `v1/audio/generate` endpoint" (#1789)

### [e449cc4](https://github.com/vllm-project/vllm-omni/commit/e449cc411ef0e047f23a2b4b82f742cc100af57b)

- **作者**: Zhou Taichang
- **时间**: 2026-03-10T14:29:16Z
- **提交信息**: [Doc][skip-ci] Update installation instructions (#1762)

Signed-off-by: Taichang Zhou <tzhouam@connect.ust.hk>
Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: Zhou Taichang <tzhouam@connect.ust.hk>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>

### [5d62fcd](https://github.com/vllm-project/vllm-omni/commit/5d62fcd7171f1d0588045fcf77ea6e8d4c8ecedf)

- **作者**: zhumingjue138
- **时间**: 2026-03-10T09:39:37Z
- **提交信息**: [CI]: Add core_model and cpu markers for L1 use case. (#1709)

Signed-off-by: zhumingjue <zhumingjue@huawei.com>

### [745ef31](https://github.com/vllm-project/vllm-omni/commit/745ef312a73ac7cab594df120ca3b4614f68fe4f)

- **作者**: Daniel Huang
- **时间**: 2026-03-10T07:44:54Z
- **提交信息**: [Enhancement][pytest] Check for process running during start server (#1559)

Signed-off-by: Daniel Huang <daniel1.huang@intel.com>

---
