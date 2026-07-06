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
- **星标数**: 2064
- **最后更新**: 2026-07-06T08:13:09Z

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
- **星标数**: 2466
- **最后更新**: 2026-07-06T11:55:23Z

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
- **星标数**: 2159
- **最后更新**: 2026-07-06T10:20:33Z

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
- **星标数**: 5905
- **最后更新**: 2026-07-06T10:22:04Z

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
- **星标数**: 3802
- **最后更新**: 2026-07-06T13:45:17Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 2
- **主要提交者**: William Lin, Mac Lee

## AI分析总结

基于提交记录和项目背景（FastVideo：高效视频生成工具，强调文档、快速启动和社区协作），现总结昨日更新要点如下：

---

### 1. 主要更新类型
- **CI/测试基础设施优化**（占多数）：CI自动化、测试清理、性能基准增强
- **Bug修复**：修复遗留审查问题、处理架构兼容性问题
- **代码重构/规范化**：删除死代码和重复测试、格式化代码、更新配置
- **性能基准建设**：添加指标特定阈值、归一化组件指标、v2配置字段

### 2. 关键变更点及其与项目方向的关系
| 变更点 | 与项目方向的关系 |
|--------|------------------|
| 删除死代码和重复测试（-489行） | 提升代码可维护性，符合项目“高效”理念 |
| CI自动运行pre-commit（无需手动审批） | 加速外部贡献集成，呼应社区合作（README有Slack/Discussion） |
| 更新reseed-performance-baseline技能（因hf_store迁移） | 及时适配存储层变动，保证性能回归测试准确 |
| 格式化fastvideo/performance至统一yapf风格 | 规范代码风格，便于多人协作 |
| 防止测试目录无CI测试车道收集 | 避免测试遗漏，提高覆盖可靠性 |
| 归一化性能阶段组件指标 | 建立可比对的性能基线，支持项目长期性能跟踪 |
| 添加指标特定性能阈值 | 自动化性能告警，防止回归 |
| 修复#1447遗留审查问题（3个） | 提升代码质量，体现高质量标准 |
| 跳过ThunderKittens内核在aarch64上并文档化构建矩阵 | 解决平台兼容性，明确支持范围 |
| 暴露LoRA提取斜杠命令、添加v2配置字段 | 完善工具链和配置管理，为后续功能扩展铺垫 |

### 3. 对项目的影响和潜在意义
- **短期**：减少无用代码，CI跑得更快更准，贡献者体验提升。
- **长期**：构建了更健壮的性能监控体系（阈值 + 归一化指标），可防止新提交导致性能退化，对项目稳定性至关重要。
- **潜在意义**：随着社区增长（每周开发会议、Slack），这些工程化改进降低了维护成本，为后续功能开发（如更多视频模型支持）扫清障碍。

### 4. 值得关注的技术点
- **性能基准组件指标归一化**：可能统一了不同模型/硬件下的度量方式，是性能对比的基础。
- **指标特定性能阈值**：允许为不同指标（如显存占用、FPS）单独设置阈值，精细化质量门禁。
- **ThunderKittens内核跳过aarch64**：提示该项目对CUDA/Triton等GPU内核有强依赖，未来可能需关注ARM架构下的适配策略。
- **v2性能基准配置身份字段**：可能为多版本基准管理做准备，如区分不同模型、精度或数据并行方案。

### 5. 结合README背景，这些提交如何影响项目发展
FastVideo 以“高效视频生成”为核心，社区导向、快速迭代。这些提交：
- **强化了工程成熟度**：测试清理和CI优化让项目更可靠，符合“Quick Start”中追求的低门槛体验。
- **支持性能可观测性**：阈值和归一化指标为用户/开发者提供透明化的性能表现，增强信任。
- **降低贡献门槛**：CI自动跑pre-commit、格式化配置文件，减少新贡献者的合规摩擦，促进社区活跃（Meeting和Slack已存在）。
- **保障长期演进**：通过修复遗留问题和架构兼容性，项目能更平滑地扩展新功能（如Hunyuan 1.5 chat-list预处理已覆盖）。

**总体**：昨日更新聚焦于“质量与自动化”，是项目从快速原型走向工程化产品的重要一步。

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
- **星标数**: 33993
- **最后更新**: 2026-07-06T14:23:45Z

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
- **星标数**: 12668
- **最后更新**: 2026-07-06T14:08:33Z

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
- **星标数**: 29980
- **最后更新**: 2026-07-06T14:17:54Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 6
- **主要提交者**: Thomas, Cheng Wan, Kevin Flansburg

## AI分析总结

好的，根据你提供的仓库README摘要和昨日提交记录，我对`sgl-project/sglang`的更新进行了深入分析。以下是结合项目背景的要点总结：

---

### 1. 主要更新类型
- **Bug修复**：3个（#30053 Bootstrap-queue资源释放， #30154 遗留getter基线修复， #29926 Diffusion生成管线修复）
- **重构**：3个（#30151 ServerArgs顺序优化， #30137 配置解析管线全栈审查， #30152 虽然未列出但提及10-PR系列）
- **功能新增**：1个（#23049 Diffusion模型支持log-requests）
- **代码清理与维护**：3个（#30153 移除格式化注释， #30159 扩散模型重复定义清理， #30149 删除占位文件）

---

### 2. 关键变更点及与项目方向的关系
- **ServerArgs顺序优化**（#30151）：将公共参数提前，同时内联特定架构元组（LLAMA4/MIMO_V2）。这体现了项目**对多架构支持的持续改进**，便于用户和开发者统一管理配置，符合README中“支持多种模型”的定位。
- **HiCache预取资源释放**（#30053）：修复在disaggregated-prefetch场景下Bootstrap队列异常中止时的资源泄漏。**直接提升系统稳定性**，尤其对长序列或高并发推理场景至关重要。
- **Diffusion模型功能拓展**（#23049、#29926）：新增log-requests功能，修复生成管线。表明项目正**积极扩展Diffusion模型的多模态服务能力**，与README中可能提及的“支持文本生成与扩散模型”方向一致。
- **配置解析管线重构**（#30137）：进行全栈审查（10个PR的系列），这是**底层基础设施的深度优化**，将影响所有模型启动、参数合并、优先级解析等流程，长期会降低维护成本、提高新特性集成效率。

---

### 3. 对项目的影响和潜在意义
- **稳定性提升**：资源泄漏修复和getter基线冲突解决，减少了生产环境中的偶发崩溃和配置解析错误，尤其对部署高可用服务有直接价值。
- **维护性改善**：代码清理（移除`# fmt: off`、删除占位文件、重复定义清理）降低了技术债务，使后续贡献者更容易理解和修改代码。
- **多模态能力增强**：Diffusion模块的功能完善（log-requests）是迈向生产级多模态服务的重要一步，可能吸引更多图像/视频生成场景的用户。
- **架构演进铺垫**：ServerArgs和配置管线的重构，为未来支持新硬件、新分布式策略（如disaggregated serving）奠定了更清晰的抽象层。

---

### 4. 值得关注的技术点
- **Disaggregated serving中的资源管理**：Bootstrap-queue中止时的资源释放机制（#30053），反映了项目在**细粒度资源生命周期控制**上的投入，是高性能推理系统的关键设计。
- **配置解析的“全栈审查”**（#30137）：10个PR的系列审查表明项目采用**渐进式重构策略**，关注点包括配置优先级、覆盖逻辑、类型安全等，对理解整个系统的启动流程有重要参考价值。
- **内联架构元组**（#30151）：将LLAMA4/MIMO_V2的架构信息直接嵌入ServerArgs，而非通过外部映射，减少了运行时查找开销，体现**对性能极致的追求**。
- **Diffusion生成管线**（#29926）：修复了ground truth（GT）生成管线，这说明项目在**为Diffusion模型提供量化、评估等高级功能**做准备。

---

### 5. 这些提交如何影响项目发展（结合README背景）
- **方向一：多模型统一推理

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
- **星标数**: 1220
- **最后更新**: 2026-07-06T13:24:34Z

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
- **星标数**: 85484
- **最后更新**: 2026-07-06T14:29:39Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: Spandan Tiwari, Ting SUN, Isotr0py

## AI分析总结

根据提交记录和项目背景，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：MRV2 启用前缀双向注意力支持、序列并行（无数据并行）特性。
- **Bug 修复**：Voxtral Realtime 超时挂起、Mamba/Mamba2 检查点加载崩溃、TurboQuant KV 缓存数据类型不一致。
- **性能优化**：序列并行带来 1.9%～5.0% 端到端吞吐量提升。
- **测试/兼容性改进**：修复 ROCm (AMD GPU) 上 FP8 量化测试容差问题。

### 2. 关键变更点与项目方向的关系
- **序列并行 (#47070)**：直接提升吞吐量，对应项目“fast”和“cheap”目标，降低推理成本。
- **MRV2 前缀双向注意力 (#46942)**：增强长上下文推理或复杂提示处理能力，扩展服务场景。
- **Mamba/Mamba2 加载修复 (#46037)**：确保新模型架构的兼容性，扩大模型支持范围。
- **Voxtral Realtime 超时修复 (#44461)**：针对实时语音/流式服务的稳定性改进，提升可用性。
- **ROCm FP8 测试 (#46944)**：适配 AMD GPU 的硬件特性（1-ULP 舍入），完善跨平台支持。
- **TurboQuant KV 缓存修复 (#47609)**：修复量化部署中可能导致内存损坏的 bug，保障低精度推理的可靠性。

### 3. 对项目的影响和潜在意义
- **性能提升**：序列并行无需数据并行即可生效，降低了部署复杂度，单节点/小规模集群受益明显。
- **稳定性增强**：多个 Bug 修复解决了实际部署中的挂起、崩溃问题，提升生产环境可靠性。
- **模型兼容性**：Mamba 加载修复与 Voxtral 修复表明项目正向更多架构（如状态空间模型、实时语音模型）扩展。
- **硬件生态**：AMD GPU 测试改进有助于吸引更多硬件平台用户，符合开源社区多元化趋势。

### 4. 值得关注的技术点
- **序列并行实现**：无需 DP 的序列并行方案可能利用了张量并行中的序列分片，减少了跨节点通信开销。
- **MRV2 双向注意力前缀**：可能是对 Multi-Reference Variant 2 架构的优化，支持前缀缓存中的双向注意力，有利于高效处理多轮对话或长文档。
- **FP8 测试的 ULP 调整**：针对 gfx950 芯片的 1-ULP 浮点舍入行为，体现了对具体硬件细粒度适配的工程实践。

### 5. 对项目发展的影响（结合 README）
- **“Easy, fast, and cheap”**：序列并行降低了 DP 依赖和通信开销，使低成本部署更易实现；Mamba 等模型支持降低了用户切换模型的门槛；Bug 修复提升了开箱即用的体验。
- **社区活跃度**：修复来自多位贡献者（AMD、学术机构），显示项目吸引了跨领域开发者，有助于生态壮大。
- **技术演进方向**：从单纯的 Transformer 加速扩展到 Mamba 等非 Transformer 架构，以及实时

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
- **星标数**: 5456
- **最后更新**: 2026-07-06T13:59:40Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: TaffyOfficial, Renzheng Wang, 汪志鹏

## AI分析总结

根据您提供的6条提交记录（均为Bug修复）与仓库README背景（旨在提供“易用、快速、低成本的全模态模型服务”），以下是昨日更新的要点分析：

---

### 1. 主要更新类型
- **全部为 Bug 修复**（BugFix / Bugfix），无功能新增、性能优化或文档更新。

---

### 2. 关键变更点及与项目方向的关系
| 提交 | 修复内容 | 与项目方向的关系 |
|------|----------|----------------|
| `#4877` | 修复 `#3236` 号 issue 中的 Bug（具体细节未展开） | 提升通用稳定性 |
| `#4900` | 在**进程外 CFG（分类器自由引导）并行**中保留扩散模型的 `extra_body` 参数 | 保障扩散模型（图像生成）与并行推理机制的兼容性 |
| `#4893` | 修复 HunyuanImage3 在 **vLLM 0.24** 版本下的 MoE（混合专家）分组问题 | 适配最新 vLLM 版本，保证**图像模态推理**的正确性 |
| `#4834` | **休眠模式**（sleep mode）：防止生成任务在部分唤醒时被提前执行，并确保唤醒操作的幂等性 | 优化**资源管理**，避免因状态混乱导致的推理错误 |
| `#4889` | 保持 **Qwen3-TTS（文本转语音）** 的有种子残差 MTP（多 token 预测）采样批量化 | 增强**语音模态**的采样一致性，支持批量推理 |
| `#4892` | 移除 HunyuanImage3 扩散加载器中已被删除的 `get_cache_scale` 调用 | 消除加载错误，保持**图像扩散模型**与代码库的同步 |

所有修复均直接服务于**多模态（图像、语音）模型的稳定推理**，符合项目“全模态服务”定位。

---

### 3. 对项目的影响和潜在意义
- **提升可靠性**：修复了多个边缘场景（部分唤醒、参数丢失、版本兼容等），减少生产环境中的意外中断。
- **增强兼容性**：主动适配 vLLM 0.24 等上游版本，降低用户升级时的阻塞风险。
- **完善多模态覆盖**：HunyuanImage3（图像扩散）和 Qwen3-TTS（语音）的特定修复，表明项目正持续深耕热门多模态模型。
- **优化资源管理**：休眠模式相关修复有助于节省 GPU 资源（在闲置时保持低功耗），对低成本服务目标有直接贡献。

---

### 4. 值得关注的技术点
- **CFG 并行中的 extra_body 保留**：扩散模型常通过 `extra_body` 传递控制参数（如引导尺度、负提示），进程外并行容易丢失这些参数，修复此问题保障了**高级生成控制**的有效性。
- **MoE 分组与 vLLM 版本兼容**：HunyuanImage3 使用混合专家层，vLLM 0.24 可能改变了专家分组逻辑，需同步调整。
- **MTP 采样批量化**：Qwen3-TTS 的“有种子残差 MTP”是一种提升语音生成质量和多样性的技术，保持其批量化有助于**提高吞吐**。
- **休眠模式的幂等性**：确保唤醒操作只生效一次，避免重复初始化导致的状态冲突，这是分布式推理中常见但容易被忽略的细节。

---

### 5. 对

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
