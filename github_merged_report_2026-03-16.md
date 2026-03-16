# GitHub Stars 合并报告 - 2026-03-16

**合并日期**: 2026-03-17
**监控日期**: 2026-03-16
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


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1732
- **最后更新**: 2026-03-16T16:38:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2070
- **最后更新**: 2026-03-16T16:27:21Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Chengtao Lv

## AI分析总结

根据提供的仓库README摘要和提交记录，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **性能优化**：支持自回归（AR）KV缓存量化，并优化了自回归窗口大小。

### 2. 关键变更点及其与项目整体方向的关系
- **支持AR KV缓存量化**：通过量化键值（KV）缓存来减少内存占用，提升推理效率。
- **优化AR窗口大小**：调整自回归生成过程中的窗口大小，可能旨在平衡生成质量与计算开销。
- **与项目方向的关系**：LightX2V定位为“轻量级视频生成推理框架”，核心目标是高效、快速的视频生成。本次更新直接针对推理阶段的**内存优化和计算效率**，与项目追求的“轻量”和“高性能”方向高度一致。

### 3. 对项目的影响和潜在意义
- **降低内存需求**：KV缓存量化可显著减少大模型推理时的显存占用，使框架更易在资源受限的设备上部署。
- **提升推理速度**：优化窗口大小可能减少了不必要的计算，加快了自回归生成步骤。
- **增强框架竞争力**：这些优化使LightX2V在保持生成质量的同时，进一步突出了其“轻量高效”的优势，可能吸引更多注重性能的用户。

### 4. 值得关注的技术点
- **KV缓存量化技术**：这是大语言模型（LLM）推理中常见的内存优化手段，现在被应用于视频生成模型。具体量化方法（如INT8、INT4）和其对生成质量的影响值得关注。
- **自回归窗口优化**：窗口大小的调整策略（例如，基于内容动态调整还是固定优化）可能涉及对视频时序依赖性的深入理解。

### 5. 基于项目背景的提交影响分析
- **巩固核心优势**：README强调框架的“轻量”和“快速”。本次提交通过内存和计算优化，直接强化了这两个核心卖点。
- **推动实际部署**：降低资源消耗使LightX2V更适用于**边缘计算、实时应用或成本敏感**的场景，拓宽了其应用潜力。
- **技术栈演进**：引入量化支持表明项目正在积极集成业界成熟的模型压缩与加速技术，以保持其技术前沿性。

**总结**：昨日更新是一次针对推理性能的精准优化，通过量化技术和参数调优，进一步夯实了LightX2V作为高效视频生成推理框架的定位，有助于其在实际应用中的推广和部署。

## 详细提交记录

### [8d96337](https://github.com/ModelTC/LightX2V/commit/8d963373660d004c4643afebd27bd07df938996c)

- **作者**: Chengtao Lv
- **时间**: 2026-03-16T10:49:26Z
- **提交信息**: support ar kv cache quant and optimize ar window size (#950)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1963
- **最后更新**: 2026-03-15T20:23:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: 无法获取仓库信息

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3190
- **最后更新**: 2026-03-16T13:27:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33060
- **最后更新**: 2026-03-16T23:08:57Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Steven Liu

## AI分析总结

### 1. 主要更新类型
- **文档更新**：本次提交主要涉及文档的修复和内容更新。

### 2. 关键变更点及其与项目整体方向的关系
- **修复文档链接和内容**：修正了文档中的链接错误，并更新了中文（zh）文档部分。
- **与项目方向的关系**：Diffusers 项目致力于提供易用、可扩展的扩散模型库，清晰的文档对降低用户使用门槛、促进社区协作至关重要。本次更新直接支持了项目的易用性和国际化目标。

### 3. 对项目的影响和潜在意义
- **提升用户体验**：修复链接和更新内容有助于用户更顺畅地查阅文档，减少困惑。
- **增强国际化支持**：更新中文文档部分，有助于扩大项目在中文开发者社区的影响力和可及性。
- **维护项目质量**：持续改进文档是维护开源项目专业性和可靠性的重要一环。

### 4. 值得关注的技术点
- 无明显代码或架构层面的技术变更；本次为纯文档更新。

### 5. 基于README了解的项目背景，这些提交如何影响项目发展
- README 强调 Diffusers 是一个用于扩散模型的模块化工具箱，旨在平衡**易用性、灵活性和高性能**。清晰的文档是“易用性”的核心支撑。
- 本次提交通过修复文档问题，直接强化了项目的**易用性和可访问性**，尤其通过更新中文内容，支持了更广泛的全球开发者社区，这与项目追求开放、协作的发展方向一致。持续维护多语言文档有助于降低技术传播壁垒，促进项目生态的健康发展。

## 详细提交记录

### [ed31974](https://github.com/huggingface/diffusers/commit/ed31974c3e7c7459db066687c7e98a29f0b7769f)

- **作者**: Steven Liu
- **时间**: 2026-03-16T20:24:57Z
- **提交信息**: [docs] updates (#13248)

* fixes

* few more links

* update zh

* fix

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 382
- **最后更新**: 2026-03-16T13:39:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12007
- **最后更新**: 2026-03-16T06:33:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24642
- **最后更新**: 2026-03-16T22:42:20Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 12
- **主要提交者**: Bruce Wu, Shangming Cai, Sugar920

## AI分析总结

根据提供的提交记录和README摘要（SGLang项目是一个专注于高效LLM推理的框架），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占主导，涉及依赖、推理解析、采样参数、并行计算、图编译等多个方面。
- **性能优化**：包括注意力机制和专家并行通信的优化。
- **功能增强/测试**：为NPU添加基础功能测试，并重新启用CI测试。
- **发布与依赖**：发布了`sglang kernel 0.4.0`版本。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **修复sglang-kernel CI依赖** (#20715) | 确保核心组件在CI环境中的稳定构建与测试，维护项目基础可靠性。 |
| **修复多种并行计算场景** (#19548, #20686) | 直接支持**大规模、高性能分布式推理**，是项目处理长上下文、高吞吐的核心。 |
| **优化DP Attention和Elastic EP通信** (#20406, #12068) | 提升**计算效率和资源利用率**，对降低延迟、提高吞吐量有直接贡献。 |
| **发布sglang kernel 0.4.0** (#20440) | 标志核心推理引擎的迭代更新，可能包含性能提升和新特性。 |
| **新增NPU基础测试** (#19382) | 拓展对**异构硬件（如华为昇腾）** 的支持生态，符合项目追求广泛部署的目标。 |
| **修复Diffusion相关图编译与参数问题** (#20699, #20630, #20681) | 完善**多模态（文生图）推理**能力，是项目向超越纯文本生成发展的重要部分。 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：大量Bug修复增强了框架在复杂并行配置和边缘情况下的鲁棒性。
- **性能与扩展性**：通信和计算优化有助于进一步提升推理速度，支持更大模型和更复杂部署。
- **生态与兼容性**：支持NPU和修复各类并行问题，降低了用户在不同硬件和集群配置上的使用门槛。
- **功能完整性**：对Diffusion模块的修复确保了多模态推理路径的可用性。

### 4. 值得关注的技术点
- **复杂并行支持**：PP2+CP8+TP8等混合并行模式的修复，体现了对**极致分布式推理**的深入支持。
- **硬件异构化**：主动添加NPU测试，表明项目正积极拥抱**国产AI芯片等多样化算力**。
- **图编译优化**：关注`torch.compile`在图生图任务中的图融合问题，涉及**底层计算图优化**的前沿实践。
- **动态负载均衡**：Elastic EP中使用GPU P2P通信交换专家权重，是**MoE模型高效推理**的关键技术。

### 5. 基于项目背景的提交影响分析
SGLang旨在成为**高效、可扩展的LLM服务引擎**。昨日的更新紧密围绕这一核心目标：
- **强化核心优势**：通过修复并行计算Bug和进行通信优化，直接巩固了其**高吞吐、低延迟分布式推理**的立身之本。
- **拓展能力边界**：完善Diffusion模块，是在其**高效文本推理**的基础上，向**多模态推理**能力拓展的重要步骤。
- **扩大应用生态**：修复CI、发布新内核、增加NPU支持，这些工作提升了项目的**成熟度、可靠性和硬件普适性**，有助于吸引更广泛的开发者和企业用户，促进社区和生态增长。

**总结**：昨日更新是一次以**修复和优化**为主的迭代，重点在于夯实基础、提升性能、扩大兼容性。这符合一个处于快速发展期项目的典型特征：在积极添加新功能（如多模态、多硬件支持）的同时，不断回头打磨核心推理引擎的稳定性和效率，为项目长期发展奠定坚实基础。

## 详细提交记录

### [826eb21](https://github.com/sgl-project/sglang/commit/826eb21bca8b0fd73682f95f472793f8cc1ae668)

- **作者**: Baizhou Zhang
- **时间**: 2026-03-16T22:23:01Z
- **提交信息**: Fix sglang-kernel dependency on CI runners (#20715)

### [5ef5806](https://github.com/sgl-project/sglang/commit/5ef58061609ab7a73cd75a7ac1fe63ea4ef63f43)

- **作者**: roikoren755
- **时间**: 2026-03-16T20:29:40Z
- **提交信息**: [Nemotron] Small reasoning parser fix (#20284)

### [70a6fb5](https://github.com/sgl-project/sglang/commit/70a6fb53af1ec80dd5cc57d485dbbb664db0ea19)

- **作者**: Bruce Wu
- **时间**: 2026-03-16T18:37:58Z
- **提交信息**: Enable embedding lookup/lora_a logic for chunked backend (#17692)

Co-authored-by: Bruce Wu <mogicianwu@fb.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: Ethan (Yusheng) Su <yushengsu.thu@gmail.com>

### [061ec58](https://github.com/sgl-project/sglang/commit/061ec582bfb2d4c075520d04685eb828db2ec7eb)

- **作者**: Douglas Yang
- **时间**: 2026-03-16T18:27:06Z
- **提交信息**: fix: adding teacache.params back to sampling params as intended (#20665)

### [a4528a5](https://github.com/sgl-project/sglang/commit/a4528a5737b841bf17ef49c010f564fe5a06d454)

- **作者**: Shangming Cai
- **时间**: 2026-03-16T17:04:21Z
- **提交信息**: [CI] Bring back CI test for Mamba PD Disaggregation (#20675)

### [289cbcf](https://github.com/sgl-project/sglang/commit/289cbcf482f3704bc48975e8627646da566cc423)

- **作者**: ybyang
- **时间**: 2026-03-16T16:51:47Z
- **提交信息**: fix: support PP2+CP8+TP8 (PP with context parallelism) (#19548)

### [6489f77](https://github.com/sgl-project/sglang/commit/6489f77733816fcc1a70e75d09c14e12cb8a299b)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-16T15:14:27Z
- **提交信息**: [Diffusion] Fix compile graph broken by flashinfer rope (#20699)

### [d3c0f43](https://github.com/sgl-project/sglang/commit/d3c0f4376a12e3c51836902f7fed02be60e1bf90)

- **作者**: Du Bin
- **时间**: 2026-03-16T14:38:59Z
- **提交信息**: Fix AssertionError crash in disagg prefill inflight queue with PP (#20686)

### [15097c5](https://github.com/sgl-project/sglang/commit/15097c5c3b528d9165ddc935d99c5fadef8cdcb5)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-16T12:34:58Z
- **提交信息**: Release sglang kernel 0.4.0 (#20440)

Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [3d58cd1](https://github.com/sgl-project/sglang/commit/3d58cd16d940e2437e58e146d780f54e1112e2b9)

- **作者**: sky
- **时间**: 2026-03-16T10:44:42Z
- **提交信息**: [DP Attention] Optimize dp_padding_mode selection for dp_size=1 in extend mode (#20406)

Signed-off-by: wangfakang <fakangwang@gmail.com>

### [549fbcc](https://github.com/sgl-project/sglang/commit/549fbcc864c24bc7d98b6ac33981967b79a67c3c)

- **作者**: Xun Sun
- **时间**: 2026-03-16T10:40:58Z
- **提交信息**: [5/N] (Elastic EP) Use GPU P2P to exchange expert weights during EPLB as much as possible (#12068)

Co-authored-by: Hank Han <hanhan.hank@bytedance.com>
Co-authored-by: Hank Han <hanhan7630@outlook.com>

### [3055b69](https://github.com/sgl-project/sglang/commit/3055b6906d5f64d8aeb810bbda96d3f9a8c67170)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-16T09:41:40Z
- **提交信息**: [Diffusion] Document torch.compile graph-break checks in diffusion benchmark skills (#20681)

### [485597e](https://github.com/sgl-project/sglang/commit/485597e651d38398b9b24fa08c48263509d22300)

- **作者**: Mick
- **时间**: 2026-03-16T08:55:30Z
- **提交信息**: [diffusion] fix: fix some sampling args passed via cli are omitted (#20630)

### [895e560](https://github.com/sgl-project/sglang/commit/895e56097cc25f762373f462fd027bc39163eb0c)

- **作者**: Sugar920
- **时间**: 2026-03-16T07:09:56Z
- **提交信息**: Add NPU basic function testcases (#19382)

Co-authored-by: cy <chenyang08056032@163.com>
Co-authored-by: Cherry_ming <136634645@qq.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1090
- **最后更新**: 2026-03-16T15:37:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 73321
- **最后更新**: 2026-03-16T23:15:22Z

## 提交统计

- **昨日提交总数**: 50
- **提交者数量**: 39
- **主要提交者**: Harry Mellor, Artem Perevedentsev, Roy Wang

## AI分析总结

根据您提供的 vLLM 仓库昨日提交记录，结合其“易用、快速、经济的LLM服务”的项目目标，现总结分析如下：

### 1. 主要更新类型
昨日提交以 **Bug修复** 和 **性能优化** 为主，辅以功能增强、文档更新和CI/基础设施改进。
*   **Bug修复 (约20项)**：涉及模型支持（如EagleMistral、Mamba、Qwen系列）、注意力机制、量化、编译、多模态、工具调用等多个核心模块的稳定性问题。
*   **性能优化 (约8项)**：包括缓存预取、内存管理、注意力后端优化、模型加载加速等。
*   **功能新增/增强 (约6项)**：支持新的量化格式（MXFP8）、新的模型架构（混合SSM-FA）、新的工具解析器（Granite4）等。
*   **文档/代码质量 (约5项)**：澄清文档、更新工作流、重构测试、移除无用代码。
*   **CI/构建/基础设施 (约5项)**：稳定测试、修复构建问题、硬件支持（ROCm/AMD）优化。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向（易用、快速、经济）的关系 |
| :--- | :--- |
| **支持在线MXFP8量化 (#35448)** | **经济性**：为MoE和稠密模型新增更高效的8位量化支持，可降低部署成本。 |
| **多项性能优化（缓存预取#36012、内存API替换#37031等）** | **快速性**：直接提升服务吞吐量和响应速度，优化资源利用率。 |
| **广泛修复模型兼容性Bug（Qwen, Mamba, EagleMistral等）** | **易用性**：扩大vLLM可稳定支持的模型范围，降低用户使用新模型的门槛。 |
| **增强多模态/多连接器支持 (#36549, #37057, #37147)** | **易用性 & 快速性**：提升对复杂输入（视频、音频）和部署架构（流水线并行）的支持能力。 |
| **ROCm/AMD硬件支持优化 (#36845, #36442等)** | **经济性 & 易用性**：改善对AMD硬件的支持，为用户提供更多硬件选择，可能降低成本。 |
| **工具调用与解析器修复/增强 (#36827, #36774, #36992)** | **易用性**：提升与Agent、RAG等应用场景的集成流畅度。 |

### 3. 对项目的影响和潜在意义
*   **稳定性与可靠性提升**：大量Bug修复直接增强了生产环境的稳定性，特别是对量化、新模型和边缘用例的支持。
*   **性能基准持续提高**：通过内存、缓存、加载等底层优化，巩固了vLLM在高性能LLM推理领域的领先地位。
*   **生态扩展**：对新模型架构（SSM）、新硬件（AMD）、新格式（MXFP8）的支持，持续扩大vLLM的适用生态。
*   **开发者体验改善**：文档澄清、编译警告修复、测试稳定化等工作，有助于降低贡献者门槛和内部开发效率。

### 4. 值得关注的技术点
1.  **MXFP8在线量化 (#35448)**：一种新的8位浮点量化格式，旨在为MoE等模型提供更优的精度-效率权衡。
2.  **混合SSM-FA模型支持 (#36687)**：将状态空间模型（SSM）与注意力机制结合，是架构探索的前沿。
3.  **“延迟KV连接器清理”用于推测解码 (#37013)**：优化推测解码这一关键性能特性，可能减少内存操作开销。
4.  **针对Blackwell架构的FlashInfer回滚 (#36987)**：显示了对最新GPU硬件的快速适配和调优。
5.  **ROCm注意力后端自动选择 (#36845)**：提升在AMD GPU上的开箱即用性能和兼容性。

### 5. 基于项目背景的提交影响分析
vLLM的核心目标是降低**高质量LLM服务的获取门槛**。昨日的提交集合紧密围绕这一目标：
*   **迈向“易用”**：通过修复众多模型（尤其是国产Qwen系列和Mistral系列）和功能（工具调用、多模态）的Bug，**让更多模型和复杂用例能“开箱即用”**，减少了用户的调试成本。
*   **夯实“快速”**：不仅修复了影响性能的Bug（如注意力崩溃#34871），还主动引入缓存预取等优化，**持续压榨硬件潜力，保持推理速度的竞争优势**。
*   **拓展“经济”**：新增**MXFP8量化支持**和**强化AMD ROCm支持**是两大亮点。前者为用户提供了可能**更低精度损失或更高效率的量化选项**以节省成本；后者则**打破了英伟达的硬件垄断**，为用户提供了更具成本效益的硬件选择方案，直接服务于“cheap for everyone”的愿景。

**总结**：昨日的更新是一次典型的“巩固与拓展”并重的迭代。在**夯实核心推理引擎稳定性与性能**的同时，积极**拓展支持的模型边界、硬件平台和优化技术**，全方位推动项目向更易用、更快速、更经济的LLM服务平**台演进。

## 详细提交记录

### [3e6a1e1](https://github.com/vllm-project/vllm/commit/3e6a1e1686958dcd7eff1438bc5418b8d56daa30)

- **作者**: Terry Gao
- **时间**: 2026-03-16T22:51:46Z
- **提交信息**: [Custom Ops] Add functional + out variant for scaled_fp4_quant (#34389)

Signed-off-by: tianrengao <terrygao87@gmail.com>

### [7961486](https://github.com/vllm-project/vllm/commit/7961486a9b749b1b60d8b6fd5fb7d61596a9b041)

- **作者**: Julien Denize
- **时间**: 2026-03-16T22:41:00Z
- **提交信息**: Fix EagleMistralLarge3Model initialization (#37232)

Signed-off-by: juliendenize <julien.denize@mistral.ai>

### [4f9b14c](https://github.com/vllm-project/vllm/commit/4f9b14c21cd4eb4b56c972b3280be41d341056d1)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-16T22:40:23Z
- **提交信息**: [CI] Stabilize multinode DP internal LB completion tests (#36356)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [31a458c](https://github.com/vllm-project/vllm/commit/31a458c0913e2c498da004e16ba2ac922bcebe96)

- **作者**: Yuchen Fama
- **时间**: 2026-03-16T22:27:42Z
- **提交信息**: [Doc] Clarify schema enforcement behavior for tool_choice modes (#37064)

Signed-off-by: yfama <yuchengu@gmail.com>

### [a3a51d2](https://github.com/vllm-project/vllm/commit/a3a51d20e7d040542118f04f5089c57a27bc7aca)

- **作者**: Wei Zhao
- **时间**: 2026-03-16T22:22:40Z
- **提交信息**: [Benchmark] Improvements to attention benchmark script (#37115)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>

### [e5b8076](https://github.com/vllm-project/vllm/commit/e5b807607c8493155e6eccd665772d4c19b2114e)

- **作者**: EdalatiAli
- **时间**: 2026-03-16T22:07:39Z
- **提交信息**: [Quant][Feature] Support online MXFP8 quantization for MoE and dense models (#35448)

Signed-off-by: EdalatiAli <aliedalati@cohere.com>

### [fd4d963](https://github.com/vllm-project/vllm/commit/fd4d96302a2999a8d773b1b331951d232e3f5e05)

- **作者**: Elvir Crnčević
- **时间**: 2026-03-16T22:03:54Z
- **提交信息**: Fix eplb nvfp4 experts hook (#37217)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>
Signed-off-by: Elvir Crncevic <elvir@anthropic.com>
Co-authored-by: Tyler Michael Smith <tyler@neuralmagic.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [c0f0119](https://github.com/vllm-project/vllm/commit/c0f011918da543f1323833c8ee2bfcac99e0452a)

- **作者**: Krish Gupta
- **时间**: 2026-03-16T21:11:33Z
- **提交信息**: [Bugfix] opcheck false mutation error in rms_norm_per_block_quant (#36688) (#36779)

Signed-off-by: Krish Gupta <krishom70@gmail.com>

### [e6ae4b1](https://github.com/vllm-project/vllm/commit/e6ae4b1be1c3dca1c25d7a12058dbb1fd900caa2)

- **作者**: Zhengxu Chen
- **时间**: 2026-03-16T21:05:51Z
- **提交信息**: [compile] Enable mega aot artifact for torch 2.12+. (#37198)

Signed-off-by: zhxchen17 <zhxchen17@fb.com>

### [2dccb38](https://github.com/vllm-project/vllm/commit/2dccb38f73fa79bc629b8b215b8066e61ce4a211)

- **作者**: zhanqiuhu
- **时间**: 2026-03-16T20:51:04Z
- **提交信息**: [Bugfix][MultiConnector] Fix MultiConnector for SupportsHMA sub-connectors (#36549)

### [d157216](https://github.com/vllm-project/vllm/commit/d157216093ac50603bab5c2236437cdc68512f6d)

- **作者**: Kunshang Ji
- **时间**: 2026-03-16T20:39:56Z
- **提交信息**: [BUGFIX][Mamba] Use uint64 for address in KVBlockZeroer (#37197)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [93f3c8e](https://github.com/vllm-project/vllm/commit/93f3c8e53157f55b45cb902bb12ba68bb69e062c)

- **作者**: Matthew Bonanni
- **时间**: 2026-03-16T20:24:48Z
- **提交信息**: [Misc] Add `float16` to `CacheDType` (#37199)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [2cc26c3](https://github.com/vllm-project/vllm/commit/2cc26c3a9973257d5fcc582f063915d52dded86f)

- **作者**: rasmith
- **时间**: 2026-03-16T20:22:57Z
- **提交信息**: [CI][BugFix][MORI][AMD] Add transfer_id to kv transfer params for test (#37213)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>

### [dfa8852](https://github.com/vllm-project/vllm/commit/dfa8852db20a75374e5451789fbee1c535f62315)

- **作者**: Flora Feng
- **时间**: 2026-03-16T19:53:07Z
- **提交信息**: [Refactor] Consolidate GPT-OSS reasoning parser tests (#36915)

Signed-off-by: sfeng33 <4florafeng@gmail.com>
Signed-off-by: Flora Feng <4florafeng@gmail.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [714c6e0](https://github.com/vllm-project/vllm/commit/714c6e0eab76a4fb1394089d848ecfe46408b9c9)

- **作者**: Lucas Kabela
- **时间**: 2026-03-16T19:42:34Z
- **提交信息**: [torch.compile][BE] Modify cudagraph callable to check for is_forward_context_set (#36288)

Signed-off-by: Lucas Kabela <lucaskabela@meta.com>

### [0fefd00](https://github.com/vllm-project/vllm/commit/0fefd00e6ccf6670686eb2cc0a5eda57f56e625a)

- **作者**: Sage
- **时间**: 2026-03-16T18:59:01Z
- **提交信息**: [Bugfix] Fix render server crash for quantized models on CPU-only hosts (#37215)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [f5c081d](https://github.com/vllm-project/vllm/commit/f5c081d4325536975f79720125af48f200bcac75)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-03-16T18:58:06Z
- **提交信息**: [PD][Nixl] Add support for hybrid SSM-FA models (#36687)

### [c88ea83](https://github.com/vllm-project/vllm/commit/c88ea8338b9ad2f01bfb24c7bbf8ae6140866afd)

- **作者**: Matthew Bonanni
- **时间**: 2026-03-16T17:51:21Z
- **提交信息**: [MTP][Sparse MLA] Take advantage of native MTP support in indexer when possible (#36982)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [9f9ecff](https://github.com/vllm-project/vllm/commit/9f9ecff4cdff5b8847f541b896c0ca081397cc51)

- **作者**: Max de Bayser
- **时间**: 2026-03-16T17:49:09Z
- **提交信息**: Add simple granite4 tool parser (#36827)

Signed-off-by: Max de Bayser <maxdebayser@gmail.com>
Signed-off-by: Max de Bayser <mbayser@br.ibm.com>

### [ca1954d](https://github.com/vllm-project/vllm/commit/ca1954d58c49e3a3209ec86d743a99f3a605028b)

- **作者**: haosdent
- **时间**: 2026-03-16T17:03:10Z
- **提交信息**: [Bugfix] Disable cross-layer KV cache for MLA attention backends (#37090)

Signed-off-by: haosdent <haosdent@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [55e6d3d](https://github.com/vllm-project/vllm/commit/55e6d3d5c035b4c0035108b3a51f7a474cae379b)

- **作者**: Raushan Turganbay
- **时间**: 2026-03-16T16:48:18Z
- **提交信息**: [Bugfix] Make siglip/clip compatible with transformers v5  (#37200)

Signed-off-by: raushan <raushan@huggingface.co>

### [6682c23](https://github.com/vllm-project/vllm/commit/6682c231fa97f33d3b3f4d788da4e14959989a67)

- **作者**: Chauncey
- **时间**: 2026-03-16T16:27:47Z
- **提交信息**: [Bugfix] Add error handling for FINISHED_ERROR in OpenAIServing (#37148)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [5ae685c](https://github.com/vllm-project/vllm/commit/5ae685c1c85bb659476a21ce7a2457eb6cccc4bb)

- **作者**: Itay Etelis
- **时间**: 2026-03-16T15:20:51Z
- **提交信息**: [Bugfix] Relax TRTLLM KV cache contiguity assertion for cross-layer layout (#34158)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>

### [ce8cf91](https://github.com/vllm-project/vllm/commit/ce8cf9161d2228745aa40135f6e427b603572597)

- **作者**: Wentao Ye
- **时间**: 2026-03-16T15:12:15Z
- **提交信息**: [Compile] Fix compile warning `st256_cs` in `cuda_vec_utils.cuh` (#36693)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [18be11f](https://github.com/vllm-project/vllm/commit/18be11fd59cd3bf1082170ca638ebdfa384e7ed6)

- **作者**: xjx
- **时间**: 2026-03-16T15:10:42Z
- **提交信息**: [BUGFIX]fix CUDA OOM ERROR : invalid argument at cumem_allocator.cpp:119 (#35594)

Signed-off-by: xjx <493337577@qq.com>

### [8d8855f](https://github.com/vllm-project/vllm/commit/8d8855fdae00830221025e4a8ba8267596372056)

- **作者**: Yuanheng Zhao
- **时间**: 2026-03-16T14:27:29Z
- **提交信息**: [Bugfix] Add safety check and fallback for null scaling factor (#36106)

Signed-off-by: Yuanheng Zhao <jonathan.zhaoyh@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [e855d38](https://github.com/vllm-project/vllm/commit/e855d380fa59614167362a94e87a21a91f3ab470)

- **作者**: Wentao Ye
- **时间**: 2026-03-16T14:16:14Z
- **提交信息**: [Compile] Fix compile warning in `moe_permute` (#36529)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [0e5a938](https://github.com/vllm-project/vllm/commit/0e5a9382af6a48c8edc0efaa25a01156fdd3738e)

- **作者**: Benjamin Bartels
- **时间**: 2026-03-16T14:01:57Z
- **提交信息**: [Bugfix] accept redacted thinking blocks in Anthropic messages (#36992)

Signed-off-by: Benjamin Bartels <benjaminba@tiglab-ubuntu.ilab.local>
Signed-off-by: bbartels <benjamin@bartels.dev>
Co-authored-by: Benjamin Bartels <benjaminba@tiglab-ubuntu.ilab.local>

### [04bf5a3](https://github.com/vllm-project/vllm/commit/04bf5a35fa2692aa75e0442791849dd976014ce8)

- **作者**: Fynn Schmitt-Ulms
- **时间**: 2026-03-16T13:53:45Z
- **提交信息**: [Spec Decode] Update extract_hidden_states to use deferred kv_connector clear (#37013)

### [43a73f8](https://github.com/vllm-project/vllm/commit/43a73f853bac76e6c95c629e4aaa0858f610eb11)

- **作者**: Tianyu Guo
- **时间**: 2026-03-16T13:09:09Z
- **提交信息**: Remove unused EVS functions in qwen3_vl.py (#37183)

Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>

### [ffbc2e5](https://github.com/vllm-project/vllm/commit/ffbc2e5bdbfb7e4caae9c671696ca92fc9836101)

- **作者**: Julien Denize
- **时间**: 2026-03-16T12:22:18Z
- **提交信息**: Patch Mistral config (#37104)

Signed-off-by: juliendenize <julien.denize@mistral.ai>

### [f9e6db3](https://github.com/vllm-project/vllm/commit/f9e6db30349d7ec70410981b1f634a1e661e61e1)

- **作者**: Lukas Geiger
- **时间**: 2026-03-16T12:11:59Z
- **提交信息**: [Models][Qwen3 ViT] Keep `max_seqlen` on CPU to prevent D2H sync (#37139)

Signed-off-by: Lukas Geiger <lukas.geiger94@gmail.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [d61d2b0](https://github.com/vllm-project/vllm/commit/d61d2b08e99e311976d6622a991de7603034b174)

- **作者**: elvischenv
- **时间**: 2026-03-16T12:09:27Z
- **提交信息**: [Build] Fix API rate limit exceeded when using `VLLM_USE_PRECOMPILED=1` (#36229)

Signed-off-by: elvischenv <219235043+elvischenv@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [f5e59ee](https://github.com/vllm-project/vllm/commit/f5e59ee7a6c3a07aad8f814b261bc0a1db2dcaf1)

- **作者**: Artem Perevedentsev
- **时间**: 2026-03-16T11:32:02Z
- **提交信息**: [Performance] Add prefetch for checkpoints to OS page cache (#36012)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [9b005ed](https://github.com/vllm-project/vllm/commit/9b005edc48d105e9a9ced0ac44b5292a647c2b05)

- **作者**: Harry Mellor
- **时间**: 2026-03-16T11:12:58Z
- **提交信息**: [Docs] Make the link to hardware plugins clearer (#37174)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [bf9a185](https://github.com/vllm-project/vllm/commit/bf9a1853958584fe039d33242a43c91cf8786d61)

- **作者**: Robin Nabel
- **时间**: 2026-03-16T10:48:52Z
- **提交信息**: GLM4 tool parser: fix streaming mode (#35208)

Signed-off-by: Robin Nabel <opensource@nabel.co>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [ad041c7](https://github.com/vllm-project/vllm/commit/ad041c79db4a6e99b28c9ba78cce02435b35fd2d)

- **作者**: Harry Mellor
- **时间**: 2026-03-16T10:31:16Z
- **提交信息**: Fix text only inputs for MRoPE models with the Transformers modelling backend (#37055)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [747b068](https://github.com/vllm-project/vllm/commit/747b0681364aa53235b71a30488f450652cc316a)

- **作者**: Kunshang Ji
- **时间**: 2026-03-16T10:24:48Z
- **提交信息**: [Hardware] Replace memory related torch.cuda APIs  (#37031)

Signed-off-by: Kunshang Ji <jikunshang95@gmail.com>

### [122f75d](https://github.com/vllm-project/vllm/commit/122f75d9393883d64935706ad381beda85bc3112)

- **作者**: Harry Mellor
- **时间**: 2026-03-16T10:20:37Z
- **提交信息**: Fix pipeline parallel with multimodal models with the Transformers modelling backend (#37057)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [d8f8a7a](https://github.com/vllm-project/vllm/commit/d8f8a7aad2223f5892e966bf22df832130afe26b)

- **作者**: SoluMilken
- **时间**: 2026-03-16T10:03:21Z
- **提交信息**: [Misc] Sync pre-commit to 4.5.1 in workflows and docs (#36675)

Signed-off-by: SoluMilken <ypiheyn.imm02g@g2.nctu.edu.tw>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [0115e95](https://github.com/vllm-project/vllm/commit/0115e957d46002ca0c6823e66ef5856fbcef65be)

- **作者**: Roy Wang
- **时间**: 2026-03-16T09:46:28Z
- **提交信息**: [Frontend][Misc] Remove unused log in `/is_sleeping` (#37093)

Signed-off-by: esmeetu <jasonailu87@gmail.com>

### [116ed13](https://github.com/vllm-project/vllm/commit/116ed130f4d323cb0fb088490b52197683e875a8)

- **作者**: haosdent
- **时间**: 2026-03-16T09:30:23Z
- **提交信息**: [Bugfix] Fix GDN attention crash with mixed decode/spec-decode batches (#34871)

Signed-off-by: haosdent <haosdent@gmail.com>

### [8374387](https://github.com/vllm-project/vllm/commit/8374387bd8ef747ea331d84e911cdaaed4eb7124)

- **作者**: Vadim Gimpelson
- **时间**: 2026-03-16T09:04:29Z
- **提交信息**: [FlashInfer] Revert block_size 16 + head_size 256 workaround on Blackwell (#36987)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>

### [912fbe9](https://github.com/vllm-project/vllm/commit/912fbe9555f9f2b5f402ba1a60e3d17828bc76b0)

- **作者**: Isotr0py
- **时间**: 2026-03-16T08:56:06Z
- **提交信息**: [Bugfix] Fix Qwen2.5-Omni/Qwen3-Omni use_audio_in_video with multi-video inputs (#37147)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [52131f8](https://github.com/vllm-project/vllm/commit/52131f88d9f8d3257530ac492d9db40ca81b4872)

- **作者**: Laith Sakka
- **时间**: 2026-03-16T08:52:31Z
- **提交信息**: use skip_all_guards_unsafe to drop global_state and torch_function_mode_stack guards instead of previous hacks (#36204)

Signed-off-by: Laith Sakka <lsakka@meta.com>

### [821eb80](https://github.com/vllm-project/vllm/commit/821eb80c0d9c3eec0201fda21dbeead83b6ac1fc)

- **作者**: Roy Wang
- **时间**: 2026-03-16T08:33:36Z
- **提交信息**: [Performance][Model Loader] Skip non-local expert weights during EP model loading (#37136)

Signed-off-by: esmeetu <jasonailu87@gmail.com>

### [a2956a0](https://github.com/vllm-project/vllm/commit/a2956a0f8e8f44cc79c14a9d3b45167631b7c249)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-16T08:08:51Z
- **提交信息**: [ROCm][CI] Retrying in case of batch variance effects and reducing flakiness (#36442)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [911355e](https://github.com/vllm-project/vllm/commit/911355e216d34d08ae6fec11be118d5817c4e5fd)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-16T08:07:27Z
- **提交信息**: [ROCm] Fix KV copy methods and auto-select attention backend for ROCm (#36845)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [8d3f8f4](https://github.com/vllm-project/vllm/commit/8d3f8f485efc0b812f91ecf19a3a12232587550c)

- **作者**: Chauncey
- **时间**: 2026-03-16T07:38:42Z
- **提交信息**: [Bugfix] fix Qwen3.5 tool calling bug (#36774)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [96efb91](https://github.com/vllm-project/vllm/commit/96efb91480cd973dbcffab25ccb4b3a119b9929e)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-16T07:35:49Z
- **提交信息**: [Model Runner V2] Fix processed logits in sample() (#37144)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-17
**监控日期**: 2026-03-16
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 3199
- **最后更新**: 2026-03-16T19:23:15Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Juan Pablo Zuluaga, rongfu.leng

## AI分析总结

根据提供的README摘要和提交记录，以下是针对 `vllm-project/vllm-omni` 仓库昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了Qwen3TTS模型在流式处理中的动态初始块问题。
- **代码清理/维护**：移除了过时的Qwen3TTS相关文件。

### 2. 关键变更点及其与项目整体方向的关系
- **修复流式处理逻辑**：提交 `cf328eb` 移除了动态初始块的计算，仅在初始请求时计算，这有助于提高流式响应的稳定性和一致性。
- **清理冗余代码**：提交 `4036cd5` 删除了过时的 `qwen3_tts.py` 文件，保持代码库的整洁和可维护性。
- **与项目方向的关系**：vLLM-Omni 旨在提供“简单、快速、经济的全模态模型服务”，这些更新直接支持了项目的**稳定性**和**代码质量**目标，确保多模态（尤其是语音合成）服务的高效可靠运行。

### 3. 对项目的影响和潜在意义
- **提升流式体验**：修复可能避免流式输出中的卡顿或错误，改善用户在使用TTS（文本转语音）功能时的体验。
- **减少技术债务**：移除过时代码降低了维护成本，使开发者能更专注于核心功能的迭代。
- **增强可靠性**：针对边缘场景（如流式请求初始化）的修复有助于减少生产环境中的意外故障。

### 4. 值得关注的技术点
- **流式处理优化**：动态初始块的移除可能涉及音频流生成的时序逻辑调整，反映了对实时性要求的深入处理。
- **代码版本管理**：直接删除文件而非保留废弃代码，说明项目注重架构清晰，可能采用模块化设计，便于替换升级。

### 5. 基于项目背景的提交影响分析
- vLLM-Omni 专注于全模态（文本、图像、音频等）模型服务，**TTS是音频模态的关键组件**。这些提交：
  - **强化音频流水线**：确保语音合成在流式场景下稳定工作，支持项目“快速、便宜”服务的目标。
  - **维护开发者友好性**：清理代码有助于新贡献者快速上手，促进生态协作。
  - **体现迭代成熟度**：项目从功能扩展阶段进入优化维护阶段，注重细节打磨以提升生产就绪度。

**总结**：昨日更新虽未增加新功能，但通过修复和清理巩固了音频模态（尤其是Qwen3TTS）的流式处理基础，符合项目向稳定、高效的全模态服务平台演进的趋势。

## 详细提交记录

### [cf328eb](https://github.com/vllm-project/vllm-omni/commit/cf328eb8e8ebd913d889a9f1142ee2cb801e77d2)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-03-16T19:23:09Z
- **提交信息**: [Bug][Qwen3TTS][Streaming] remove dynamic initial chunk and only compute on initial request (#1930)

Signed-off-by: JuanPZuluaga <juanz9312@gmail.com>

### [4036cd5](https://github.com/vllm-project/vllm-omni/commit/4036cd547c7552fd9329a87f38b9d6c484f3f14b)

- **作者**: rongfu.leng
- **时间**: 2026-03-16T17:09:04Z
- **提交信息**: [Misc] removed qwen3_tts.py as it is out-dated (#1926)

Signed-off-by: rongfu.leng <lenronfu@gmail.com>

---
