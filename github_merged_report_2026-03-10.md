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
- **星标数**: 1712
- **最后更新**: 2026-03-10T21:40:56Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Crystal-jiang, PQlet, Ting

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：提交 #548 和 #549 分别解决了分布式训练和音频投影层的具体问题。
- **功能新增**：提交 #541 为 GPU 平台新增了对 GLM-5 模型的支持。

### 2. 关键变更点及其与项目整体方向的关系
- **#548：修复 `broadcast_model_weights_from_rank0` 选项缺失**：确保在构建并行化模型时能正确广播权重，直接服务于项目“模型中心化分布式配方库”的核心目标，保障大规模多模态训练中分布式设置的稳定性和一致性。
- **#549：修正 Qwen3-Omni-MoE 的音频投影层**：针对具体模型（Qwen3-Omni-MoE）在视觉语言模型（VLM）训练器中的音频处理部分进行修复，体现了项目支持“任意模态”模型训练的承诺，确保多模态（此处为音频）组件的正确性。
- **#541：新增 GLM-5 模型对 GPU 的支持**：扩展了项目所支持的模型库，使这个先进的模型能在 GPU 上运行，增强了项目作为“配方动物园”的覆盖范围和实用性。

### 3. 对项目的影响和潜在意义
- **提升稳定性和可靠性**：两项修复有助于减少用户在分布式训练和多模态模型训练中可能遇到的错误，提升框架的健壮性和用户体验。
- **生态扩展**：新增 GLM-5 支持吸引了更多关注或使用该模型的开发者/研究者，扩大了项目的用户基础和适用场景。
- **强化核心价值**：所有更新都紧密围绕项目“规模化训练任意模态模型”和提供“分布式配方”的使命，通过修复和扩展来夯实这一基础。

### 4. 值得关注的技术点
- **分布式训练配置**：`broadcast_model_weights_from_rank0` 选项的修复涉及深度学习分布式训练中关键的权重同步机制。
- **多模态模型架构**：对 Qwen3-Omni-MoE 音频投影层的修正，反映了处理音视频等多模态输入时模型组件的复杂性。
- **模型兼容性扩展**：集成 GLM-5 模型展示了项目快速适配前沿大模型的能力，可能涉及模型加载、并行化策略等适配工作。

### 5. 基于项目背景的提交影响分析
VeOmni 的目标是成为**规模化训练任意模态模型的模型中心化分布式配方库**。昨日的更新对此产生了积极影响：
- **巩固基础设施**：两项 Bug 修复直接提升了分布式训练（#548）和多模态模型训练（#549）这两个核心环节的可靠性，这是实现“规模化”和“任意模态”训练的基础保障。
- **丰富配方动物园**：新增 GLM-5 支持（#541）直接扩展了“配方动物园”的阵容，使项目能服务于更广泛的模型训练需求，增强了其作为一站式解决方案的吸引力。
- **持续迭代与完善**：这些提交表明项目处于积极的开发和维护状态，正在通过解决实践中的具体问题和完善模型支持，来不断逼近其“简化大规模多模态模型训练”的愿景。

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
- **星标数**: 2044
- **最后更新**: 2026-03-10T17:24:00Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: LiangLiu, STwangyingrui

## AI分析总结

根据提供的README摘要和提交记录，以下是对昨日更新的分析总结：

### 1. 主要更新类型
- **性能优化**：支持环形通信和稀疏计算，旨在提升分布式训练/推理效率。
- **功能新增与Bug修复**：为视频生成推理（`rs2v shot infer`）新增流式保存视频、部署工作器支持，并修复了控制器除零错误。

### 2. 关键变更点及其与项目整体方向的关系
- **支持环形FP4通信和SLA稀疏计算**：这与LightX2V作为“轻量级视频生成推理框架”的定位高度一致，通过优化通信和计算模式来降低资源消耗、提升性能，符合其追求高效推理的核心目标。
- **rs2v shot推理功能增强**：新增流式保存视频和支持部署工作器，直接强化了框架的**生产就绪能力**和**用户体验**，使视频生成更流畅、易于集成；修复除零错误则提升了**系统稳定性**，减少运行时崩溃风险。

### 3. 对项目的影响和潜在意义
- **性能提升**：环形通信和稀疏计算可能显著加速大规模视频生成任务，尤其适合多GPU或分布式场景。
- **功能完善**：流式保存和支持部署工作器使框架更贴近实际应用需求，便于在服务器或云环境中部署。
- **稳定性增强**：Bug修复减少了潜在故障点，提高框架可靠性。

### 4. 值得关注的技术点
- **环形FP4通信**：可能涉及低精度（FP4）梯度或参数的高效同步，是分布式训练的前沿优化技术。
- **SLA稀疏计算**：可能指结构化稀疏或激活稀疏，用于减少计算量，是轻量化推理的常见手段。
- **流式保存视频**：暗示框架可能支持实时或渐进式视频生成输出，而非等待全部帧生成完毕，这对长视频生成尤为重要。

### 5. 基于项目背景的提交影响分析
LightX2V旨在提供**高效、轻量的视频生成推理解决方案**。昨日的更新：
- **强化了“轻量”与“高效”特性**：通过通信和计算优化，进一步降低了资源门槛，使视频生成更快、更省资源。
- **提升了实用性和部署便利性**：新增的流式保存和部署工作器支持，使框架更易于集成到实际业务流水线中，加速从原型到生产的转化。
- **体现了框架的持续成熟**：从基础功能向性能优化、稳定性和易用性深化，符合开源项目从可用到好用的发展路径。

**总结**：昨日更新聚焦于**性能优化、功能增强和稳定性提升**，紧密围绕LightX2V作为轻量级视频生成推理框架的核心使命，通过技术进阶和功能完善，推动项目向更高效、更稳定、更易部署的方向发展。

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

### 1. **主要更新类型**
- **Bug修复**：修复了在低版本 `diffusers` 库中出现的“Group Offload”相关错误。

### 2. **关键变更点及其与项目整体方向的关系**
- **关键变更**：提交 `ad72867` 修复了当 `diffusers` 版本较低时，`Group Offload` 功能可能无法正常工作的问题。
- **与项目方向的关系**：该项目（VideoX-Fun）是一个面向AIGC视频生成的应用，依赖于 `diffusers` 等深度学习库。保持与不同版本依赖库的兼容性，有助于扩大用户基础、降低使用门槛，符合项目“易用、可访问”的方向（从README中提供的Hugging Face Spaces链接可看出其注重用户体验和部署便捷性）。

### 3. **对项目的影响和潜在意义**
- **直接影响**：提升了代码的健壮性和向后兼容性，避免低版本 `diffusers` 用户遇到运行时错误。
- **潜在意义**：减少了因环境配置问题导致的用户流失，有助于项目在更广泛的部署环境中稳定运行（例如，用户可能因系统限制无法升级到最新版 `diffusers`）。

### 4. **值得关注的技术点**
- **Group Offload**：可能指一种内存优化技术（例如，在生成视频时分组卸载模型层以减少GPU内存占用），这在资源受限的场景中尤为重要。
- **版本兼容性处理**：修复针对特定依赖库版本，反映了项目对第三方库版本碎片化的关注，可能涉及条件逻辑或API适配代码。

### 5. **基于项目背景的提交影响分析**
- **项目背景**：从README可知，VideoX-Fun 是一个集成了 CogVideoX 和 Wan-Fun 模型的AIGC视频生成工具，旨在通过 Hugging Face Spaces 等平台提供易用的演示和体验。项目强调开放性和多语言支持（中、英、日文文档）。
- **发展影响**：
  - **用户体验**：修复此类Bug能直接改善用户在使用旧版环境时的体验，减少因技术问题导致的交互中断。
  - **项目可靠性**：通过维护版本兼容性，增强了项目在多样化部署环境中的可靠性，支持更广泛的用户群体（如研究人员、开发者或个人爱好者）。
  - **生态适配**：AIGC领域依赖库更新频繁，此类修复有助于项目在快速迭代的生态中保持稳定，为后续功能迭代（如模型升级或性能优化）奠定基础。

---
**总结**：本次更新是一个针对依赖库版本兼容性的Bug修复，虽看似微小，但有助于提升项目的稳定性和可访问性，符合其作为开源AIGC应用降低使用门槛、扩大受众的长期目标。

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
- **星标数**: 5115
- **最后更新**: 2026-03-10T23:47:31Z

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
- **星标数**: 3139
- **最后更新**: 2026-03-10T21:17:56Z

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
- **星标数**: 32986
- **最后更新**: 2026-03-10T23:25:46Z

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
- **星标数**: 11957
- **最后更新**: 2026-03-10T22:30:02Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Zhongjie Duan, Hong Zhang, Artiprocher

## AI分析总结

根据提供的README摘要和提交记录，以下是昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：为LTX2模型添加了默认的负面提示词（negative prompt）。
- **功能增强/优化**：合并了与LTX2.3多参考（multiref）相关的功能改进。

### 2. 关键变更点及其与项目整体方向的关系
- **LTX2默认负面提示词**：为LTX2模型增加了默认的负面提示词，这有助于提升生成内容的质量和可控性，减少不良输出。
- **LTX2.3多参考功能**：引入了多参考支持，可能增强了模型在处理复杂或多条件生成任务时的能力。
- **与项目方向的关系**：DiffSynth-Studio作为一个基于扩散模型的合成工具，这些更新直接强化了其核心模型（LTX系列）的功能和用户体验，符合项目持续优化生成效果和扩展应用场景的方向。

### 3. 对项目的影响和潜在意义
- **提升生成质量**：默认负面提示词可标准化生成过程，降低用户使用门槛，同时提高输出内容的可靠性。
- **扩展模型能力**：多参考功能可能使模型能更好地处理多样化的输入条件，增强灵活性和适用性。
- **用户体验改善**：简化了用户配置，使非专业用户也能更容易获得高质量结果。

### 4. 值得关注的技术点
- **负面提示词机制**：在扩散模型中，负面提示词用于引导模型避免生成特定内容，这是控制生成效果的关键技术之一。
- **多参考生成**：可能涉及多条件或多模态输入的处理，反映了模型在复杂场景下的集成能力。

### 5. 基于项目背景的提交影响分析
- **项目背景**：DiffSynth-Studio是一个专注于扩散模型合成的工作室，旨在提供高效的生成工具。README强调其易用性和功能性。
- **影响分析**：
  - 这些提交通过增强LTX模型的功能，直接提升了工具的核心竞争力。
  - 默认负面提示词降低了用户的学习成本，使项目更贴近“开箱即用”的目标。
  - 多参考功能扩展了应用场景，可能吸引更多专业用户，推动项目向更复杂的合成任务发展。
  - 整体上，更新强化了项目的技术前沿性和实用性，有助于在AI生成领域保持竞争力。

**总结**：昨日更新聚焦于LTX模型的优化，通过添加默认负面提示词和引入多参考功能，提升了生成质量、用户体验和模型能力，与项目致力于提供高效、易用的扩散合成工具的方向高度一致。

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
- **星标数**: 24295
- **最后更新**: 2026-03-10T23:12:10Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 15
- **主要提交者**: Lancer, Alison Shao, Xinyuan Tong

## AI分析总结

根据提供的提交记录和README摘要（SGLang项目是一个专注于高效LLM推理的框架），以下是昨日更新的要点总结：

---

### 1. **主要更新类型**
- **Bug修复**：多个提交修复了CI、内存、音频加载、扩散模型（diffusion）和NPU上的问题。
- **性能优化**：集成FlashInfer v0.6.4、优化CUDA图、AMD FP8预填充等，提升推理效率。
- **功能新增**：支持DeepSeek3.2和GlmMoeDsa模型、扩散模型多提示映射、logprob相关参数等。
- **重构与代码清理**：重构jit_kernel、统一rotary embedding入口、清理benchmark命名等。
- **硬件支持扩展**：增强对NPU、AMD、macOS的兼容性。

---

### 2. **关键变更点及其与项目整体方向的关系**
- **性能与效率优化**（如提交4、7、16）：集成FlashInfer的FP8 GEMM和MoE支持，启用CUDA图优化，符合SGLang“高效推理”的核心目标。
- **多硬件与模型扩展**（如提交6、12-14、17）：加强对NPU、AMD、macOS的支持，并新增模型（如DeepSeek3.2），体现项目向多平台、多模型生态发展的方向。
- **稳定性与正确性修复**（如提交1、8、10、19-20）：修复CI、内存重复、扩散模型兼容性等问题，确保框架在复杂场景下的可靠性。
- **代码结构优化**（如提交11、15、21-22）：重构jit_kernel和benchmark工具，提升代码可维护性和测试效率。

---

### 3. **对项目的影响和潜在意义**
- **提升推理性能**：FP8和CUDA图优化可能显著降低延迟与内存占用，适合高吞吐场景。
- **扩大应用范围**：增强对扩散模型和多硬件的支持，使SGLang能覆盖更广泛的AI任务（如文生图）和部署环境。
- **提高开发体验**：CI修复和代码重构有助于加速迭代，降低贡献者门槛。
- **风险提示**：NPU共享输入缓冲区因精度问题被禁用（提交14），需注意硬件特定限制。

---

### 4. **值得关注的技术点**
- **FlashInfer v0.6.4集成**：支持FP8 GEMM和路由MoE，可能大幅提升Attention和MoE模型效率。
- **CUDA图优化**（提交7）：通过分段CUDA图优化logprob计算，减少内核启动开销。
- **多硬件适配**：NPU自定义内核（提交12）、AMD FP8支持（提交16）显示项目正深入硬件层优化。
- **扩散模型增强**：多提示映射（提交19）和LoRA修复（提交20）改善文生图任务的实用性。

---

### 5. **基于项目背景的提交影响分析**
SGLang旨在提供“高效、灵活的LLM推理框架”。昨日更新紧密围绕这一目标：
- **强化高效推理**：通过FlashInfer、CUDA图、FP8等优化，直接提升推理性能，符合项目对低延迟、高吞吐的追求。
- **扩展灵活性**：新增模型支持（如DeepSeek3.2）、多硬件兼容（NPU/AMD/macOS）和扩散模型修复，使框架能适应更多模型类型和部署环境。
- **提升稳健性**：修复内存、音频加载、CI等问题，增强生产环境可靠性。
- **生态建设**：代码重构和benchmark工具改进为长期维护和社区贡献奠定基础。

---

**总结**：昨日更新以**性能优化、多硬件支持、Bug修复**为主，全面强化了SGLang作为高效LLM推理框架的核心能力，同时向多模态（扩散模型）和跨平台生态扩展，符合项目“高效、灵活”的长期发展方向。

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

- **描述**: 🤗 A PyTorch-native and Flexible Inference Engine with Hybrid Cache Acceleration and Parallelism for DiTs.
- **语言**: Python
- **星标数**: 1078
- **最后更新**: 2026-03-10T13:14:38Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据仓库README摘要和提交记录分析，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：支持FireRed-Image-Edit-1.1模型（#854、#853）
- **文档更新**：修复注意力机制和并行化相关文档（#852、#850）
- **重构/API变更**：弃用`parallel_kwargs`参数（#849）
- **项目维护**：更新README文档（#851）

### 2. 关键变更点及其与项目方向的关系
- **模型扩展**：新增对FireRed-Image-Edit-1.1的支持，符合项目作为"PyTorch-native and Flexible Inference Engine"的定位，持续扩展支持的模型生态
- **API简化**：弃用`parallel_kwargs`参数，表明项目在优化API设计，减少冗余配置，提升易用性
- **文档完善**：多次修复并行化相关文档，强化项目"Hybrid Cache Acceleration and Parallelism"核心特性的文档支持

### 3. 对项目的影响和潜在意义
- **用户价值**：FireRed-Image-Edit模型的加入扩展了图像编辑应用场景
- **开发者体验**：API简化降低了使用门槛，文档完善减少了学习成本
- **技术债务**：主动弃用旧参数有利于长期代码维护

### 4. 值得关注的技术点
- **模型适配**：FireRed-Image-Edit作为图像编辑模型，其集成可能涉及特殊的缓存和并行化策略
- **并行化演进**：从`parallel_kwargs`的弃用可以看出并行化配置正在向更简洁的接口演进
- **文档一致性**：多次提交修复同一类文档问题，反映项目对文档质量的重视

### 5. 基于项目背景的提交影响分析
从README可知项目是**专注于DiTs的混合缓存加速推理引擎**，昨日提交：
- **强化核心优势**：通过完善并行化文档和简化API，进一步突出"Parallelism"和"Flexible"特性
- **生态扩展**：支持新模型符合"for 🤗DiTs"的生态建设目标
- **用户体验优化**：文档更新和API简化降低了用户采用门槛，有助于提升项目采用率（与README中的下载量徽章目标一致）
- **技术前瞻性**：弃用旧参数显示项目在积极优化架构，为未来功能扩展做准备

**总体评价**：昨日更新体现了项目在功能扩展、用户体验和技术优化三个维度的平衡发展，既增加了对新模型的支持，又通过文档和API改进降低了使用门槛，符合项目作为专业推理引擎的定位。

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
- **星标数**: 72753
- **最后更新**: 2026-03-10T23:45:33Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 18
- **主要提交者**: Zhengxu Chen, Pleaplusone, Vadim Gimpelson

## AI分析总结

根据提供的提交记录和项目README背景（vLLM是一个致力于“简单、快速、经济的LLM服务”的项目），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及多个核心组件（如KV缓存、模型推理、HTTP请求、处理器签名等）。
- **性能优化**：主要集中在ROCm平台和稀疏注意力（Sparse MLA）的CUDA图支持。
- **功能新增/增强**：包括KV卸载策略、gRPC服务分离、模型Runner V2的测试与修复、错误信息增强等。
- **CI/测试改进**：涉及测试优化、CI工作负载调整和类型检查工具升级。
- **重构/代码简化**：如核心KV缓存初始化逻辑简化。
- **模型支持修复**：针对特定模型（如FunASR、Qwen2.5-VL、Mamba/Qwen3.5）的bug修复。

### 2. 关键变更点及其与项目整体方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **性能优化（ROCm/CUDA图）** | 直接支持“快速”目标，提升AMD平台和稀疏注意力的推理效率。 |
| **KV卸载策略（Strategy A）** | 支持“经济”目标，通过智能管理CPU内存降低部署成本。 |
| **Model Runner V2 多项修复** | 增强新一代推理引擎的稳定性，是架构演进的关键。 |
| **核心KV缓存初始化简化** | 提升代码可维护性和执行效率，支持“简单”和“快速”。 |
| **gRPC服务分离** | 改善服务部署的模块化和灵活性，支持生产化需求。 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：大量Bug修复（尤其是核心组件和模型支持）直接增强了生产环境的可靠性。
- **性能与成本优化**：针对ROCm和KV卸载的改进，有助于在更多硬件上实现高性能、低成本的推理。
- **架构演进**：Model Runner V2的持续测试和修复，表明项目正在积极向更先进的推理架构过渡。
- **开发者体验**：CI测试优化和错误信息增强，改善了开发与测试效率。

### 4. 值得关注的技术点
- **稀疏注意力（Sparse MLA）的CUDA图支持扩展至ROCm**：标志着对AMD GPU生态的性能优化进入更深层次。
- **KV卸载的“重用频率门控”策略**：一种新的内存管理策略，可能对长序列或高并发场景的成本控制有重要意义。
- **Model Runner V2对分块预填充（chunked prefill）的处理修复**：这是处理长上下文输入的关键技术。
- **FunASR模型bug修复**：表明vLLM在持续扩展其支持的模型家族，不限于纯文本LLM。

### 5. 基于项目背景的提交影响分析
vLLM的目标是“为所有人提供简单、快速、经济的LLM服务”。昨日的提交从多个维度推动这一目标：
- **快速**：通过ROCm性能优化、稀疏MLA CUDA图支持、核心逻辑简化，持续压榨硬件性能。
- **经济**：引入KV卸载新策略，优化内存使用，直接降低部署的硬件成本。
- **简单**：通过修复各类Bug（模型、处理器、HTTP请求）、增强错误信息，减少用户和开发者的使用与调试复杂度。
- **为所有人**：修复特定模型（如Qwen、FunASR）的问题，并改进AMD平台支持，体现了对多样化模型和硬件生态的包容性。

**总体而言**，这是一次以**稳定性修复和性能优化**为主的常规迭代，同时稳步推进**新架构（Model Runner V2）** 和**新功能（gRPC、KV卸载）**，完全符合vLLM作为一个成熟、高性能推理引擎的持续演进路径。

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
- **星标数**: 2984
- **最后更新**: 2026-03-10T23:52:25Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Baoyuan Qi, Junhong Liu, Zhou Taichang

## AI分析总结

根据 `vllm-omni` 仓库的 README 摘要（“为所有人提供简单、快速、经济的全模态模型服务”）和昨日的提交记录，以下是分析总结：

### 1. 主要更新类型
- **性能优化**：针对 Qwen3-omni 模型的核心推理路径进行了重构和优化。
- **功能新增**：为 Qwen3TTS 模型增加了动态 TTFA 功能。
- **Bug修复**：修复了与 vLLM 0.17.0 的兼容性问题。
- **功能回退**：回退了 Stable Audio Diffusion 的在线服务及相关端点。
- **文档更新**：更新了安装说明。
- **CI/CD 增强**：增加了测试标记以支持特定用例。
- **测试增强**：改进了服务器启动时的进程检查。

### 2. 关键变更点及其与项目整体方向的关系
- **Qwen3-omni 性能优化**：通过重构代码预测器、引入重预填充和 SDPA，并消除解码热路径的 CPU 往返，**直接提升了推理速度和效率**，这与项目“快速”和“经济”的核心目标高度一致。
- **Qwen3TTS 动态 TTFA**：基于 Code2Wav 负载实现动态首次音频时间，**增强了音频生成的响应性和用户体验**，支持了“全模态”和“易用”的目标。
- **vLLM 兼容性修复**：确保与上游 vLLM 框架新版本的兼容性，**维护了项目的稳定性和可维护性**，是生态集成的重要一环。
- **Stable Audio Diffusion 回退**：可能由于稳定性、架构冲突或优先级调整，**暂时收缩了功能范围以保障核心服务稳定**，体现了对生产就绪性的谨慎态度。
- **安装文档更新**：**降低了新用户的入门门槛**，支持“为所有人服务”的易用性目标。

### 3. 对项目的影响和潜在意义
- **正面影响**：
    - **显著提升 Qwen3-omni 性能**：可能降低推理延迟和成本，增强该模型在服务场景的竞争力。
    - **改善音频模型体验**：动态 TTFA 使 TTS 服务更智能、响应更快。
    - **加强项目健壮性**：兼容性修复和测试增强减少了潜在故障点。
- **潜在风险/关注点**：
    - **功能回退**：可能影响依赖该音频生成端口的用户，需关注后续替代方案或重新引入计划。
    - **复杂度管理**：性能优化可能增加了代码复杂度，需要确保可维护性。

### 4. 值得关注的技术点
- **“重预填充 + SDPA”优化**：这可能是针对注意力机制和预填充阶段的重要性能优化技术，值得关注其具体实现和性能收益。
- **消除解码热路径 CPU 往返**：这是典型的低延迟优化手段，通过减少 CPU-GPU 通信来提升吞吐量。
- **动态 TTFA 基于 Code2Wav 负载**：体现了根据模型内部状态动态调整服务行为的智能调度思路。
- **与 vLLM 0.17.0 的兼容性**：反映了项目紧密跟随上游核心框架演进，需要持续关注集成策略。

### 5. 基于项目背景的提交影响分析
`vllm-omni` 旨在成为**全模态、高性能、低成本的模型服务引擎**。昨日的提交整体上**强力推进了这一愿景**：
- **强化核心性能**：对 Qwen3-omni（作为重要的全模态模型）的优化直接提升了服务的“快速”和“便宜”属性。
- **拓展模态体验**：在音频模态（TTS）上引入更智能的动态特性，丰富了“全模态”服务的细腻度。
- **巩固基础架构**：通过兼容性修复、文档更新和测试增强，**提升了项目的整体成熟度和用户友好度**，使“为每个人服务”更可持续。
- **战略聚焦**：回退可能不成熟或不核心的功能，**有助于集中资源打磨关键路径**，符合快速发展项目中常见的优先级调整策略。

**总结**：昨日更新是一次以**性能优化和体验增强为核心**的迭代，紧密结合项目目标，在提升核心模型效率、完善音频模态支持的同时，夯实了项目基础，展现了在追求全模态服务过程中对性能、稳定性和用户体验的平衡考量。

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
