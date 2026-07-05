# GitHub Stars 合并报告 - 2026-07-05

**合并日期**: 2026-07-06
**监控日期**: 2026-07-05
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


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2063
- **最后更新**: 2026-07-04T15:32:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2464
- **最后更新**: 2026-07-04T10:15:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2157
- **最后更新**: 2026-07-03T15:39:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5898
- **最后更新**: 2026-07-05T18:34:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3800
- **最后更新**: 2026-07-05T22:53:44Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 2
- **主要提交者**: Mac Lee, William Lin

## AI分析总结

根据昨日提交记录（共12个），主要更新集中在**CI优化、测试清理、性能基准增强和Bug修复**，未涉及新功能或大规模重构。以下是具体分析：

### 1. 主要更新类型
| 类型 | 提交数 | 关键提交 |
|------|--------|----------|
| CI/自动化改进 | 6 | `#1555`、`#1552`、`#1550`、`#1545`、`#1542`、`#1544` |
| 测试维护 | 2 | `#1556`（删除死代码和重复测试-489行）、`#1552`（防止CI遗漏测试目录） |
| 性能基准工具完善 | 3 | `#1553`（更新reseed脚本适配hf_store迁移）、`#1554`（格式化性能代码）、`#1518`（覆盖Hunyuan 1.5 chat-list预处理） |
| Bug修复 | 2 | `#1549`（修复#1447的3个遗留问题）、`#1548`（aarch64跳过ThunderKittens内核+文档） |

### 2. 关键变更点与项目方向关联
- **CI流水线增强**：  
  - 允许fork PR自动运行pre-commit（`#1555`），降低社区贡献门槛。  
  - 添加**指标级性能阈值**（`#1545`）和**v2基准配置标识**（`#1544`），确保性能退化可被自动检测。  
  - 暴露LoRA提取Slash命令（`#1542`），与项目可能支持的LoRA微调/推理工作流衔接。  
- **测试清理**：删除489行死代码和重复测试（`#1556`），提升CI执行效率与可维护性。  
- **性能基准工具优化**：  
  - 调整reseed脚本适配`hf_store`迁移（`#1553`），反映项目对HuggingFace模型存储的依赖变化。  
  - 覆盖Hunyuan 1.5 chat-list文本预处理（`#1518`），该项目可能集成该视频/多模态模型。  
- **Bug修复**：  
  - 修复#1447的3个review问题（`#1549`），提高代码质量。  
  - 跳过aarch64平台的ThunderKittens内核（`#1548`），并补充构建矩阵文档，增强跨平台兼容性（尤其是Apple Silicon）。

### 3. 对项目的影响与潜在意义
- **稳定性和可维护性提升**：清理测试、格式化性能代码、修复bug减少技术债，利于长期迭代。  
- **CI质量门禁加强**：性能阈值和指标归一化（`#1475`）使性能回归能自动告警，避免因代码变更导致推理/训练效率下降。  
- **社区协作优化**：fork PR自动CI检查+pre-commit，吸引外部贡献者，符合开源项目“Weekly Dev Meeting”的社区驱动风格。  
- **模型支持扩展**：针对Hunyuan 1.5的预处理覆盖，暗示项目可能正在集成该视频生成模型，与README中介绍的FastVideo定位（视频快速生成/处理）一致。

### 4. 值得关注的技术点
- **性能基准指标归一化**（`#1475`的后续）：统一不同组件（如GPU、异构加速）的计量方式，对精准评估很有价值。  
- **ThunderKittens内核架构支持**：明确构建矩阵（aarch64跳过），表明项目依赖了手写CUDA/Triton内核，且需考虑多平台。  
- **LoRA提取

## 详细提交记录

### [9d909f5](https://github.com/hao-ai-lab/FastVideo/commit/9d909f5f0457ac91f489d5fc8000931f042b72ce)

- **作者**: William Lin
- **时间**: 2026-07-05T22:53:40Z
- **提交信息**: [test]: remove dead and duplicate tests (-489 lines) (#1556)

### [76b0550](https://github.com/hao-ai-lab/FastVideo/commit/76b0550c1515469d02d70cccf59c3e1ec0750d88)

- **作者**: William Lin
- **时间**: 2026-07-05T21:18:16Z
- **提交信息**: [ci]: run pre-commit on fork PRs without manual approval (#1555)

### [384c1e9](https://github.com/hao-ai-lab/FastVideo/commit/384c1e9493fb59f9f45c21ea6c19f29f0ebdba30)

- **作者**: William Lin
- **时间**: 2026-07-05T21:16:55Z
- **提交信息**: [misc]: update reseed-performance-baseline skill for the hf_store move (#1545 follow-up) (#1553)

### [b1dbcc9](https://github.com/hao-ai-lab/FastVideo/commit/b1dbcc93f6a27f468f5344bf27a44a0c88a85746)

- **作者**: William Lin
- **时间**: 2026-07-05T21:16:20Z
- **提交信息**: [misc]: reformat fastvideo/performance to the repo yapf config (#1554)

### [b938337](https://github.com/hao-ai-lab/FastVideo/commit/b93833772e7a78eef71806b5516ca85d33f0ce39)

- **作者**: William Lin
- **时间**: 2026-07-05T21:07:38Z
- **提交信息**: [ci]: guard against test directories no CI lane collects (#1552)

### [30b523e](https://github.com/hao-ai-lab/FastVideo/commit/30b523edd69843a269c15597b1bb3090d75e21c6)

- **作者**: Mac Lee
- **时间**: 2026-07-05T21:05:26Z
- **提交信息**: [ci] Normalize performance stage component metrics (#1475) (#1550)

### [6aab7f3](https://github.com/hao-ai-lab/FastVideo/commit/6aab7f3832e9ffb8c0011bc22e4c688272bf9b9c)

- **作者**: Mac Lee
- **时间**: 2026-07-05T19:05:25Z
- **提交信息**: [ci] cover Hunyuan 1.5 chat-list text preprocessing (#1518)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [9cd53fe](https://github.com/hao-ai-lab/FastVideo/commit/9cd53fe5f8af8158cb268c2a25b92e403a6d715c)

- **作者**: Mac Lee
- **时间**: 2026-07-05T19:04:33Z
- **提交信息**: [ci] Add metric-specific performance thresholds (#1545)

### [6a32cf3](https://github.com/hao-ai-lab/FastVideo/commit/6a32cf3a5e7c35a6663b1ae6f247a4a64a7b499d)

- **作者**: Mac Lee
- **时间**: 2026-07-05T13:45:31Z
- **提交信息**: [ci]: expose LoRA extraction slash command (#1542)

### [98be9b3](https://github.com/hao-ai-lab/FastVideo/commit/98be9b3da2cabaf3cdc2871e5a244a94ab8d4fd1)

- **作者**: William Lin
- **时间**: 2026-07-05T13:43:27Z
- **提交信息**: [bugfix]: address the three remaining #1447 review findings (#1549)

### [c53e85b](https://github.com/hao-ai-lab/FastVideo/commit/c53e85b76745603dad7ed687f22cd83eef7b98d2)

- **作者**: Mac Lee
- **时间**: 2026-07-05T13:18:15Z
- **提交信息**: [ci] Add v2 performance benchmark config identity fields (#1544)

### [40a8bd2](https://github.com/hao-ai-lab/FastVideo/commit/40a8bd2d3b6d21ea01f89c143cb7f75a7e695266)

- **作者**: William Lin
- **时间**: 2026-07-05T13:13:11Z
- **提交信息**: [bugfix]: skip ThunderKittens kernels on aarch64 and document the kernel build matrix (#1548)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33987
- **最后更新**: 2026-07-05T15:57:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 423
- **最后更新**: 2026-07-03T19:24:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12663
- **最后更新**: 2026-07-05T02:36:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29942
- **最后更新**: 2026-07-05T22:34:37Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 6
- **主要提交者**: Kevin Flansburg, Thomas, Elizaveta Martirosian

## AI分析总结

根据提交记录和项目背景（SGLang 是一个高性能大语言模型服务框架，支持多模态模型如扩散模型），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **重构与代码清理**：占主导（4项：`#1`、`#2`、`#5`、`#6`），包括移除废弃格式化指令、调整参数顺序、删除重复定义和占位文件。
- **Bug 修复**：3项（`#3`、`#4`、`#8`），涉及资源泄漏、竞态条件及扩散模型生成管线问题。
- **功能增强**：1项（`#7`），为扩散模型添加 `log-requests` 支持。
- **配置/审查**：1项（`#9`），全栈配置解析流水线代码审查（仅审查，未合入代码改动）。

### 2. 关键变更点与项目方向的关系
- **参数结构调整（`#2`）**：将 `ServerArgs` 的公共参数置于特定参数之前，提升代码可读性和易用性，符合“快速服务框架”对配置清晰的需求。
- **HiCache 资源释放修复（`#3`）**：修复分离预填充（disagg-prefill）模式下引导队列中止时的预取资源泄漏，直接提升分布式推理的稳定性（SGLang 的核心特性之一）。
- **扩散模型管线修复与日志支持（`#7`、`#8`）**：修复 GT 生成管线并增加请求日志，表明项目正积极扩展对扩散模型的支持（从 README 可知 SGLang 已支持 Stable Diffusion 等多模态模型），完善其可观测性。
- **清理技术债务（`#1`、`#5`、`#6`）**：移除过时代码和占位符，减少维护负担，为后续功能迭代腾出空间。

### 3. 对项目的影响与潜在意义
- **稳定性提升**：修复资源泄漏和竞态条件（`#3`、`#4`），降低生产环境中异常崩溃和内存泄漏的风险，提升服务可靠性。
- **多模态支持强化**：扩散模型相关修复和日志功能使 SGLang 在多模态推理场景下更健壮，有助于吸引更多用户（如图像生成业务）。
- **可维护性改善**：参数重排、代码清理和配置管道审查为未来规模化开发打下基础，减少新手理解成本。

### 4. 值得关注的技术点
- **分离预填充（disagg-prefill）的资源管理**：`HiCache` 在引导队列中的预取机制，是 SGLang 实现低延迟预填充与高吞吐解码分离的关键技术，本次修复涉及边界情况处理。
- **扩散模型与 LLM 的架构融合**：`#7` 和 `#8` 表明 SGLang 的扩散模型分支已逐渐成熟，其请求日志系统如何兼容不同模型类型（text/image）值得关注。
- **配置解析流水线（`#9`）**：虽本次仅为审查，但“全栈配置解析”暗示项目可能重构配置加载机制，长远看可提升灵活性和错误提示质量。

### 5. 基于项目背景的总结性影响
SGLang 正从“专注 LLM 服务”向“统一多模态推理框架”演进：
- 昨日更新在保持 LLM 核心稳定的同时，显著加固了扩散模型分支，并清理了历史遗留代码。
- 修复的资源泄漏和竞态问题体现了对生产环境稳定性的重视。
- 参数顺序调整和占位符清理代表项目进入“架构优化”阶段，为后续大规模功能扩展（如更长上下文、更多硬件支持）做准备。
- 整体上，这些提交有助于提升框架的成熟度，增强社区信任，并

## 详细提交记录

### [8673e85](https://github.com/sgl-project/sglang/commit/8673e85e6c312f4f7c618a5f05c0a9eef4dd6886)

- **作者**: Lianmin Zheng
- **时间**: 2026-07-05T19:45:24Z
- **提交信息**: Remove `# fmt: off` from environ.py Envs class (#30153)

### [92a1f6e](https://github.com/sgl-project/sglang/commit/92a1f6e06c5f72582e56bfe48f8faf14472e1405)

- **作者**: Lianmin Zheng
- **时间**: 2026-07-05T19:17:24Z
- **提交信息**: [refactor] Reorder ServerArgs sections common-first; inline LLAMA4/MIMO_V2 arch tuples (#30151)

### [48ba79c](https://github.com/sgl-project/sglang/commit/48ba79c11e1f01cbd933929a83589a1906925a8d)

- **作者**: Kevin Flansburg
- **时间**: 2026-07-05T16:06:59Z
- **提交信息**: [BugFix] Release HiCache prefetch resources on disagg-prefill bootstrap-queue abort (#30053)

### [602c861](https://github.com/sgl-project/sglang/commit/602c8615a1afbb2ad13b80334643c64970884bac)

- **作者**: Cheng Wan
- **时间**: 2026-07-05T14:06:07Z
- **提交信息**: [fix] Reconcile the legacy-getter ratchet baseline after racing merges (#30154)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [931b00f](https://github.com/sgl-project/sglang/commit/931b00f1b0a9398744be596d5cdba526fdb67949)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-05T14:05:11Z
- **提交信息**: [diffusion] Clean up duplicate helper definitions (#30159)

### [3ea875f](https://github.com/sgl-project/sglang/commit/3ea875fef48f6f01fa3bddd9e2197ad190cef29d)

- **作者**: Cheng Wan
- **时间**: 2026-07-05T09:39:45Z
- **提交信息**: [chore] Remove the stack-review placeholder file (#30149)

### [addffd7](https://github.com/sgl-project/sglang/commit/addffd7489835b796d5cf8065cd12ae065697cb4)

- **作者**: Thomas
- **时间**: 2026-07-05T09:01:26Z
- **提交信息**: [Diffusion] Diffusion model support log-requests (#23049)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [b070cb2](https://github.com/sgl-project/sglang/commit/b070cb2ae05f3b28a4e0f3ca7734403bed717b4c)

- **作者**: Elizaveta Martirosian
- **时间**: 2026-07-05T08:43:50Z
- **提交信息**: Fix Diffusion GT generation pipelines (#29926)

Co-authored-by: Elizaveta Martirosian <elizaveta.martirosian@gmail.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [8fb99bb](https://github.com/sgl-project/sglang/commit/8fb99bbaf8dc3421cdc8188fddcb0082c3c0c5e7)

- **作者**: Cheng Wan
- **时间**: 2026-07-05T07:00:07Z
- **提交信息**: [refactor] Config resolution pipeline: full-stack review (10-PR series, review only) (#30137)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1216
- **最后更新**: 2026-07-03T19:34:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 85436
- **最后更新**: 2026-07-05T23:02:37Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: Lucas Wilkinson, Isotr0py, Spandan Tiwari

## AI分析总结

根据仓库 `vllm-project/vllm` 的昨日提交记录，结合其“Easy, fast, and cheap LLM serving”的定位，分析如下：

### 1. 主要更新类型
- **Bug修复**：4项（FP8测试容差、Voxtral超时挂起、Mamba模型加载崩溃、TurboQuant KV缓存数据类型）
- **功能新增**：1项（MRV2前缀双向注意力支持）
- **性能优化**：1项（序列并行无需数据并行，吞吐量提升1.9%~5%）

### 2. 关键变更点与项目方向的关系
- **序列并行优化**（`[Feature] Support sequence parallel without DP`）：  
  直接提升端到端吞吐量，符合“fast”与“cheap”（通过减少DP需求降低显存开销）的目标。这是对大规模部署场景的核心改进。
- **MRV2模型支持**：  
  扩展了模型兼容性（可能指Mamba-2或类似变体），使vLLM能服务于更多新型架构，推进“everyone”的普及目标。
- **Mamba/Mamba2加载修复**：  
  修复缺少`architectures`字段的检查点崩溃，增强了对Hugging Face生态的兼容性，降低用户使用门槛。
- **Voxtral Realtime超时修复**：  
  解决静默挂起问题，提升实时推理的可靠性，呼应“easy”与稳定服务。
- **ROCm FP8测试容差**：  
  针对AMD GPU（gfx950）的FP8精度调整，表明项目在跨平台支持上的持续投入，拓宽低成本硬件选择。
- **TurboQuant KV缓存类型修复**：  
  确保量化推理时KV缓存数据类型一致，避免精度错误，保障“cheap”（低精度量化）的有效性。

### 3. 对项目的影响和潜在意义
- **性能提升**：序列并行优化直接降低延迟/提高吞吐，尤其对大模型服务影响显著。
- **稳定性增强**：多个bug修复（特别是Mamba和Voxtral）减少用户遇到的崩溃和挂起，提升生产环境信任度。
- **硬件生态扩展**：ROCm相关的测试修复有利于AMD GPU用户，降低对NVIDIA的依赖，符合“cheap”目标。
- **模型生态丰富**：支持MRV2和Mamba系列，吸引更多研究者和开发者使用vLLM部署非Transformer模型（如状态空间模型）。

### 4. 值得关注的技术点
- **序列并行 vs 数据并行**：PR #47070 提出的序列并行无需DP，可能通过将序列维度分片来减少通信开销，是分布式推理中的创新方法。
- **MRV2的“prefix bidi attention”**：这可能是一种双向注意力机制，用于前缀编码（如prompt caching），需要在MRV2特定架构中实现，技术细节值得后续关注。
- **TurboQuant的KV缓存dtype保持**：量化推理中KV缓存的数据

## 详细提交记录

### [b712181](https://github.com/vllm-project/vllm/commit/b71218107fac12bdbbffed3aa597b508347365b9)

- **作者**: Spandan Tiwari
- **时间**: 2026-07-05T23:02:30Z
- **提交信息**: [ROCm][Test] Fix test_per_token_group_quant_fp8 tolerance for 1-ULP FP8 rounding on gfx950 (#46944)

Signed-off-by: Spandan Tiwari <sptiwari@amd.com>

### [cc1d020](https://github.com/vllm-project/vllm/commit/cc1d020d01949d11b7ef70dabb0eb196b3f39f53)

- **作者**: Isotr0py
- **时间**: 2026-07-05T14:45:29Z
- **提交信息**: [MRV2] Enable mm prefix bidi attention support on MRV2 (#46942)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Signed-off-by: Isotr0py <2037008807@qq.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [8974ed8](https://github.com/vllm-project/vllm/commit/8974ed89cd0b17615ae48cf09ef824cd8e3ec521)

- **作者**: Ting SUN
- **时间**: 2026-07-05T12:42:36Z
- **提交信息**: [Bugfix][Voxtral Realtime] Fix token feedback timeout silent hang (#44461)

Signed-off-by: Ting Sun <suntcrick@gmail.com>

### [fb2face](https://github.com/vllm-project/vllm/commit/fb2faceacd7af2ea6aa51eed90f295c421c00ec5)

- **作者**: Ting SUN
- **时间**: 2026-07-05T12:42:32Z
- **提交信息**: [Bugfix][Model] Fix crash loading Mamba/Mamba2 checkpoints without an `architectures` field (#46037)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Signed-off-by: Ting SUN <suntcrick@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b6cc46e](https://github.com/vllm-project/vllm/commit/b6cc46ec3b903c71405f4355c1e9ecb47ae54bb2)

- **作者**: Wentao Ye
- **时间**: 2026-07-05T12:41:30Z
- **提交信息**: [Feature] Support sequence parallel without the need for DP, 1.9%~5.0% E2E Throughput Improvement (#47070)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: gcanlin <canlinguosdu@gmail.com>
Co-authored-by: Canlin Guo <canlinguosdu@gmail.com>

### [fa4321d](https://github.com/vllm-project/vllm/commit/fa4321de3d894c50c5ca0766dffa352d3fb07423)

- **作者**: Lucas Wilkinson
- **时间**: 2026-07-05T08:20:48Z
- **提交信息**: [Bugfix][TurboQuant] Preserve KV cache dtype in backend shape (#47609)

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-06
**监控日期**: 2026-07-05
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5440
- **最后更新**: 2026-07-05T22:26:29Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: 汪志鹏, TaffyOfficial, Yueqian Lin

## AI分析总结

以下是昨日（基于提供的提交记录日期推断）对 `vllm-project/vllm-omni` 仓库更新的分析：

### 1. 主要更新类型
- **全部为 Bug 修复**（6 个提交均标注 `[BugFix]` 或 `[Bugfix]`），无功能新增、性能优化或文档变更。

### 2. 关键变更点及其与项目方向的关系
| 提交 | 关键变更 | 与项目方向的关系 |
|------|----------|------------------|
| `#4877` | 修复 issue #3236（具体内容未公开） | 解决用户报告的基础问题，提升通用稳定性 |
| `#4900` | 保留扩散模型 `extra_body` 参数，支持外部进程 CFG 并行 | 改进多模态图像生成（扩散模型）的分布式推理兼容性 |
| `#4893` | 修复 HunyuanImage3 的 MoE 分组逻辑，适配 vLLM 0.24 | 确保与最新 vLLM 框架的兼容性，继续支持图像生成模态 |
| `#4834` | 修复睡眠模式（sleep mode）：部分唤醒时保护生成，并保证唤醒操作幂等性 | 优化资源管理，避免唤醒竞争，提升服务高可用性 |
| `#4889` | 修复 Qwen3-TTS 中带种子的残差 MTP 采样批处理问题 | 保证语音合成（TTS）模态的确定性、批处理正确性 |
| `#4892` | 移除已删除的 `get_cache_scale` 调用（HunyuanImage3 加载器） | 清理过时代码，避免潜在的加载失败 |

**项目方向**：`vllm-omni` 旨在“easy, fast, cheap”地服务全模态模型（文本、图像、语音等）。以上修复直接确保了多种模型（HunyuanImage3 图像生成、Qwen3-TTS 语音合成）和关键功能（分布式并行、睡眠模式、版本兼容）的正确运行。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：修复了多个可能导致推理出错或资源竞争的场景，为用户提供更可靠的 serving 体验。
- **多模态覆盖增强**：针对图像生成（扩散模型）和语音合成（TTS）的特定 bug 修复，表明项目仍在积极扩展或维护这些模态支持。
- **兼容性保障**：适配 vLLM 0.24 的改动可防止因框架版本升级导致的功能倒退。
- **生产环境友好**：睡眠模式幂等性修复对长期运行、弹性伸缩的部署场景至关重要，减少运维风险。

### 4. 值得关注的技术点
- **扩散模型外部进程 CFG 并行**（`#4900`）：涉及多进程间 `extra_body` 参数传递，是分布式扩散推理的常见痛点。
- **MoE 分组与 vLLM 版本耦合**（`#4893`）：HunyuanImage3 的 Mo

## 详细提交记录

### [14fad98](https://github.com/vllm-project/vllm-omni/commit/14fad9835d6a5a8f1c01bc620ec5917bfef8bd53)

- **作者**: 汪志鹏
- **时间**: 2026-07-05T17:26:09Z
- **提交信息**: [BugFix]: fix #3236 bug (#4877)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [862e0a2](https://github.com/vllm-project/vllm-omni/commit/862e0a2b27a92638fd2e31b30f4f9293a73f7c08)

- **作者**: 汪志鹏
- **时间**: 2026-07-05T17:06:30Z
- **提交信息**: [BugFix] Preserve diffusion extra_body params for out-of-process CFG Parallel (#4900)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [66ec3a2](https://github.com/vllm-project/vllm-omni/commit/66ec3a2aff983d8017e9069fbc78adc6f70a08a2)

- **作者**: TaffyOfficial
- **时间**: 2026-07-05T15:37:42Z
- **提交信息**: [Bugfix] Fix HunyuanImage3 MoE groups for vLLM 0.24 (#4893)

Signed-off-by: zuiho <2324465096@qq.com>
Co-authored-by: zuiho <2324465096@qq.com>

### [ddba6de](https://github.com/vllm-project/vllm-omni/commit/ddba6de2ab658a0fdb6f3f72cac9d2c3e2c19aea)

- **作者**: Vensen
- **时间**: 2026-07-05T14:50:08Z
- **提交信息**: [Bugfix][sleep mode]: guard generation on partial wake and ensure wake idempotency (#4834)

Signed-off-by: vensen <vensenmu@gmail.com>

### [d7b365d](https://github.com/vllm-project/vllm-omni/commit/d7b365df64075f8784109f5b7ee9596a274075e5)

- **作者**: Yueqian Lin
- **时间**: 2026-07-05T13:47:06Z
- **提交信息**: [Bugfix][Qwen3-TTS] Keep seeded residual MTP sampling batched (#4889)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [02d6547](https://github.com/vllm-project/vllm-omni/commit/02d654760fd7116554b8cb6cf3ec0c2569330928)

- **作者**: Renzheng Wang
- **时间**: 2026-07-05T09:50:43Z
- **提交信息**: [BugFix] Drop removed get_cache_scale call in HunyuanImage3 diffusion loader (#4892)

Signed-off-by: wangrzneu <wangrzneu@gmail.com>

---
