# GitHub Stars 合并报告 - 2026-06-28

**合并日期**: 2026-06-29
**监控日期**: 2026-06-28
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


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2048
- **最后更新**: 2026-06-29T10:04:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2448
- **最后更新**: 2026-06-29T05:30:48Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2150
- **最后更新**: 2026-06-29T08:01:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5875
- **最后更新**: 2026-06-29T09:28:34Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3782
- **最后更新**: 2026-06-29T08:35:45Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Kaiqin Kong, William Lin

## AI分析总结

好的，以下是对昨日提交记录的分析总结：

### 1. 主要更新类型
- **功能新增** (2项)：VSA tile cache可配置化、相对RoPE重新索引
- **文档更新** (1项)：现代化文档构建

### 2. 关键变更点及与项目方向的关系
- **`VSA tile cache` 训练可配置化**：将视频训练中的瓦片缓存行为从硬编码改为可配置参数。这与项目追求高效视频生成的目标一致——允许用户根据硬件资源或任务需求灵活调整缓存策略，提升训练效率和适应性。
- **相对RoPE重新索引（长因果展开）**：针对长序列因果注意力场景，优化了旋转位置编码的索引方式。视频数据常涉及长时序（帧间因果依赖），此改进可提升长视频生成的质量和稳定性，符合FastVideo在视频生成领域的技术深耕方向。
- **文档构建现代化**：更新文档基础设施（可能改用新工具如Sphinx/MkDocs+主题），改善开发者体验和项目可维护性，是项目成熟化的重要一环。

### 3. 对项目的影响和潜在意义
- **训练灵活性提升**：VSA tile cache可配置化降低了不同硬件（如显存大小）和环境下的适配成本，可能加速社区实验和迭代。
- **长视频生成能力增强**：相对RoPE重新索引解决了长因果展开中的位置编码退化问题，为更长的视频序列生成（例如超过1分钟）提供了技术基础，这是视频生成领域的前沿挑战。
- **文档现代化**：提升新用户入门效率和开发者贡献意愿，有助于扩大项目影响力。

### 4. 值得关注的技术点
- **VSA tile cache**：VSA（Variable-Size Attention?）的tile缓存机制，如何与训练结合？可配置化意味着支持不同缓存大小或策略。
- **Relativistic RoPE re-indexing**：将相对RoPE与因果展开结合，可能借鉴了长文本LLM中的位置插值/线性缩放思路，但针对视频的时空维度做了适配。这是视频模型处理长序列的重要创新。

### 5. 对项目整体发展的影响（结合README背景）
- 项目README强调快速入门和每周开发会议，表明其处于活跃迭代期。这两项功能更新直接优化了训练核心（缓存优化）和模型架构（位置编码），说明团队正从**基础可用**向**高性能泛化**迈进。
- 文档现代化则呼应了“文档链接”在README中的突出位置，表明项目注重社区建设与易用性，有助于吸引更多贡献者。
- 总体而言，这些提交使FastVideo在**训练效率**和**长序列建模能力**上更接近工业级视频生成框架的目标。

## 详细提交记录

### [78d606a](https://github.com/hao-ai-lab/FastVideo/commit/78d606a3a7fa0fa9eb82d1f1b2c595e3cb310938)

- **作者**: William Lin
- **时间**: 2026-06-28T09:18:31Z
- **提交信息**: [feat]: make VSA tile cache configurable for training (#1444)

### [c4e108d](https://github.com/hao-ai-lab/FastVideo/commit/c4e108de7810b7258c91dbb8fe7a59bc162d95ea)

- **作者**: William Lin
- **时间**: 2026-06-28T09:02:09Z
- **提交信息**: [docs]: modernize documentation build (#1503)

### [16bf2ea](https://github.com/hao-ai-lab/FastVideo/commit/16bf2eaf77112af12c82efad059bb92a51460411)

- **作者**: Kaiqin Kong
- **时间**: 2026-06-28T08:43:00Z
- **提交信息**: [feat] Relativistic RoPE re-indexing for long causal rollouts (#1454)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33952
- **最后更新**: 2026-06-29T08:46:10Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: dxqb

## AI分析总结

好的，以下是对 `huggingface/diffusers` 仓库提交 `ea80295` 的要点总结：

---

### 1. 主要更新类型
- **Bug 修复** – 修复 Kohya 格式 UNet LoRA 权重加载时的键映射错误，属于功能兼容性修复。

### 2. 关键变更点及其与项目方向的关系
- **修复了 `_convert_unet_lora_key()` 函数**：为 `conv_in`、`conv_out`、`time_embedding` 三个顶层子模块添加了缺失的键映射规则，使 Kohya 格式的 LoRA 权重（如 `lora_unet_conv_in`、`lora_unet_time_embed_0/2`）能正确转换为 Diffusers 内部的模块名（`conv_in`、`conv_out`、`time_embedding.linear_1/2`）。
- **同时支持 SGM 与 Diffusers 两种命名风格**：原先只处理了 Diffusers 的拼写（`conv.in`/`conv.out`）和 SGM 的 `time_embed` 拼写，现在补全了 SGM 的 `conv_in/conv_out`（即 `input_blocks.0.0`/`out.2`）以及 Diffusers 的 `time_embedding.linear_1/2`，确保 SD1.x 和 SDXL 均能覆盖。
- **处理 SDXL SGM UNet 的顶层模块穿透**：`_maybe_map_sgm_blocks_to_diffusers()` 函数之前会错误地将所有非文本键视为下/中/上块，导致 `time_embed`、`label_emb`、`out`（即 `conv_out`）和 `input_blocks.0.0`（即 `conv_in`）触发 `"layer not supported"` 异常。本次改为让这些顶层模块直接透传，交由 `_convert_unet_lora_key()` 映射。
- **新增 `label_emb` 映射**：将 SGM 的 `label_emb.0.0/0.2`（SDXL 附加条件 MLP）映射到 Diffusers 的 `add_embedding.linear_1/2`，映射优先于 SDXL 索引精简启发式规则。

这些变更直接提升了 **Diffusers 与 Kohya 生态的互操作性**，符合项目“支持主流社区工具格式、降低用户迁移成本”的发展方向。

### 3. 对项目的影响和潜在意义
- **影响**：修复后，用户可以直接加载来自 Kohya_ss 训练的 SD1.x 和 SDXL 的 UNet LoRA 权重，不再出现 `unexpected keys` 错误，端到端加载后可正常使用。
- **潜在意义**：加强了 Diffusers 作为通用扩散模型加载/微调 / 推理框架的地位，吸引更多 Kohya 用户迁入。同时也为后续支持更多 SGM / Kohya 格式的组件（如 Text Encoder LoRA、ControlNet）打下基础。

### 4. 值得关注的技术点
- **键映射逻辑的对称性**：S

## 详细提交记录

### [ea80295](https://github.com/huggingface/diffusers/commit/ea802951f5fb235b6af8fe9247f56187d49748b2)

- **作者**: dxqb
- **时间**: 2026-06-28T15:54:42Z
- **提交信息**: Fix Kohya UNet LoRA key conversion for conv_in/conv_out/time_embedding (#14006)

* Fix Kohya UNet LoRA key conversion for conv_in/conv_out/time_embedding

_convert_unet_lora_key() had no mapping for these three top-level UNet
submodules, so Kohya-format keys touching them (e.g. lora_unet_conv_in,
lora_unet_time_embed_0/2) came out as conv.in/conv.out/time.embed.0/2
instead of conv_in/conv_out/time_embedding.linear_1/2, and were
reported as unexpected keys instead of being applied.

* Handle both sgm and diffusers spellings for conv/time_embedding keys

The initial fix mapped conv_in/conv_out in the diffusers spelling (conv.in/
conv.out) and time_embedding in the sgm spelling (time_embed.0/.2), so neither
SD1.x nor SDXL was fully covered. Add the missing spellings:

- sgm conv_in/conv_out: input_blocks.0.0 / out.2 (kohya-ss SDXL sgm UNet),
  mapped before the block renames so input_blocks.0.0 does not become
  down_blocks.0.0.
- diffusers time_embedding: time_embedding.linear_1/2 (kohya-ss trains SD1.x on
  the diffusers UNet).

Verified against kohya-ss source (sdxl_original_unet.py, networks/lora.py) and
the diffusers UNet module names; regression set unchanged.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Map SDXL sgm label_emb LoRA keys and pass UNet top-level modules through

The conv_in/conv_out/time_embedding fix only reached _convert_unet_lora_key;
for the SDXL sgm UNet those keys never got there, because
_maybe_map_sgm_blocks_to_diffusers treats every non-text key as a down/mid/up
block. The top-level modules that live outside that block structure
(time_embed, label_emb, out = conv_out, and input_blocks.0.0 = conv_in) hit the
"layer not supported" raise, or crashed the inner block-index int() parse.

- Pass those top-level modules through unchanged so _convert_unet_lora_key maps
  them, instead of block-remapping or raising.
- Map the sgm label_emb (SDXL added-conditioning MLP) to diffusers add_embedding:
  label_emb.0.0/0.2 -> add_embedding.linear_1/2, before the SDXL index-strip
  heuristic that would otherwise collapse the layer index.

All additions follow the kohya/sgm naming pattern and are no-ops on real
kohya-ss files (which contain none of these top-level UNet LoRA keys); verified
end-to-end loading a full SDXL sgm UNet LoRA into the diffusers pipeline with no
unexpected/missing adapter keys.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 419
- **最后更新**: 2026-06-26T21:01:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12645
- **最后更新**: 2026-06-29T05:06:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29784
- **最后更新**: 2026-06-29T11:17:15Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 8
- **主要提交者**: Liangsheng Yin, Brayden Zhong, Mick

## AI分析总结

### 1. 主要更新类型

- **Bug修复**（3项）：DSA indexer融合导致内存消耗过大、张量子类虚拟权重初始化、FlashInfer A2A调度器在CUDA图捕获时的分发问题。
- **功能新增**（2项）：调度器指标报告初始化钩子、SGLang中一级会话身份（session identity）。
- **重构/优化**（2项）：dflash移除verify_done屏障并依赖调度器WAR回退、规格解码中用capabilities替换特殊案例。
- **测试/CI改进**（1项）：扩散模型测试健壮性（应对CDN瞬态失败）。
- **构建/依赖更新**（1项）：升级sgl-deep-gemm的apache-tvm-ffi依赖版本。

### 2. 关键变更点及其与项目整体方向的关系

- **DSA indexer融合Bug修复**（#29576）：直接影响了内存占用，与项目追求的“高性能推理”中内存效率目标一致。
- **调度器metrics reporter init hook**（#29535）：增强可观测性，为后续监控、性能调优和运营奠定基础，符合生产级系统需求。
- **会话身份一级支持**（#29436）：为多会话、多用户隔离或状态管理提供基础能力，对应框架的扩展性和企业级特性。
- **FlashInfer CUDA图捕获修复**（#29461）：保证CUDA图优化路径的正确性，是维持高推理吞吐的关键底层修复。
- **dflash重构与capabilities模型**（#29556, #29232）：将特例逻辑抽象为通用能力（WAR barrier + seq_lens_cpu），简化代码架构，推动框架向更灵活、可扩展的规格解码（speculative decoding）演进。
- **依赖升级**（#28481）：保持与上游TVM生态的兼容性，减少构建风险。

### 3. 对项目的影响和潜在意义

- **稳定性提升**：多个Bug修复直接降低了内存爆炸、初始化失败和CUDA执行异常的概率，提升用户信任度。
- **可观测性增强**：调度器指标hook让开发者/运维能实时监控调度性能，便于定位瓶颈和容量规划。
- **

## 详细提交记录

### [b9b8606](https://github.com/sgl-project/sglang/commit/b9b860652e36e2ab70f776bd851b933dbb9b502b)

- **作者**: Brayden Zhong
- **时间**: 2026-06-28T21:11:07Z
- **提交信息**: Fix DSA indexer fusion bug causing excessive memory consumption. (#29576)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [ad30a99](https://github.com/sgl-project/sglang/commit/ad30a9958e1398d53d1a56f4b82d7ae9996769be)

- **作者**: Aurick Qiao
- **时间**: 2026-06-28T17:17:00Z
- **提交信息**: Fix dummy weight init for tensor subclasses (#29229)

### [c5b9388](https://github.com/sgl-project/sglang/commit/c5b93887219b0f6dc46e3884afbef6b63650b8af)

- **作者**: Yinghai Lu
- **时间**: 2026-06-28T16:59:34Z
- **提交信息**: [scheduler] Add scheduler metrics reporter init hook (#29535)

### [aaa31eb](https://github.com/sgl-project/sglang/commit/aaa31eb0a11e09f9511bade5e815907ec0b91fa0)

- **作者**: ishandhanani
- **时间**: 2026-06-28T14:16:38Z
- **提交信息**: feat: first-class session identity in SGLang (#29436)

### [828411e](https://github.com/sgl-project/sglang/commit/828411e6f1adba2a6f8885119f4228439469951f)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-28T09:21:26Z
- **提交信息**: Fix FlashInfer A2A dispatcher during CUDA graph capture (#29461)

### [4cb6d81](https://github.com/sgl-project/sglang/commit/4cb6d81bda4898825a1e5fee957a2cef90c60e7b)

- **作者**: Mick
- **时间**: 2026-06-28T09:13:53Z
- **提交信息**: [diffusion] CI: make consistency GT probe robust to transient CDN failures (#29545)

### [6582fc1](https://github.com/sgl-project/sglang/commit/6582fc1e5d71396e233cad695ff3ed19723e509a)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-28T08:47:17Z
- **提交信息**: dflash: drop verify_done barrier; rely on scheduler WAR fallback (#29556)

### [b1da208](https://github.com/sgl-project/sglang/commit/b1da2082ca89d69e81c0d813a4552d16da68ecaf)

- **作者**: Martin Hua
- **时间**: 2026-06-28T07:26:24Z
- **提交信息**: chore: bump sgl-deep-gemm build-time apache-tvm-ffi 0.1.9 -> 0.1.11 (#28481)

### [593f5ba](https://github.com/sgl-project/sglang/commit/593f5ba68f4c27d5ea5644cd46c938644b5ef61a)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-28T07:02:32Z
- **提交信息**: [Spec] Replace shared-infra dflash special-cases with capabilities (WAR barrier + seq_lens_cpu) (#29232)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1211
- **最后更新**: 2026-06-29T07:39:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 84775
- **最后更新**: 2026-06-29T11:27:03Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 13
- **主要提交者**: Matt, Wei Zhao, xaguilar-amd

## AI分析总结

好的，以下是对 `vllm-project/vllm` 仓库昨日提交记录的分析总结。

---

### 1. 主要更新类型

- **性能优化**：聚焦 MOE 算子优化（reduce-scatter、Fused Shared Expert）、FlashAttention 新后端、算子融合。
- **Bug 修复**：修复 Mooncake 前缀查找、M-RoPE 的重计算、DSv3.2 权重跳过、多模态 ViT CUDA graph 等问题。
- **功能新增**：新增 OpenAI `privacy-filter` 模型支持、Render 端点增加 training data 生成能力。
- **硬件支持 / CI**：强化 AMD ROCm 平台（新 MLA 后端、FSE 支持、CI 示例修复、测试调整）。

---

### 2. 关键变更点与项目方向关系

| 变更 | 与项目目标（Easy, Fast, Cheap）的关系 |
|------|--------------------------------------|
| **添加 `openai/privacy-filter`** | 扩展模型生态，让更多用户能直接使用 vLLM 部署 (Easy) |
| **MOE all-reduce → reduce-scatter (GLM5.2)** | 端到端吞吐提升 ~3.2%，直接降低推理成本 (Fast, Cheap) |
| **AITER FlashAttention MLA 后端 (ROCm)** | 为 AMD 硬件提供高性能注意力实现，填补 AMD 生态短板 (Fast, Cheap) |
| **Fused Shared Expert (GLM4.5/6/7)** | 在 ROCm 上融合专家计算，减少显存带宽占用，提升吞吐 (Fast) |
| **Render endpoint `return_loss_mask`** | 支持训练数据生成，扩展 vLLM 到训练/RLHF 场景，增加用途 (Easy) |
| **Bugfixes (Mooncake, M-RoPE, DSv3.2, ViT...)** | 提升稳定性，降低用户使用门槛 (Easy, Reliable) |

---

### 3. 对项目的影响与潜在意义

- **AMD 平台成熟度提升**：多个 ROCm 专用优化（MLA FA、FSE）表明 vLLM 正积极打造 AMD 作为 NVIDIA 之外的主力推理方案，有助于降低总拥有成本。
- **GLM/DSv3 系列性能飞跃**：针对这些模型的通信和

## 详细提交记录

### [4dfbf15](https://github.com/vllm-project/vllm/commit/4dfbf1503b4bae722743c483a0079ce2f0633f4c)

- **作者**: Fabian Joswig
- **时间**: 2026-06-28T23:18:22Z
- **提交信息**: [Model] Add support for openai/privacy-filter (#41026)

Signed-off-by: Fabian Joswig <fjosw@users.noreply.github.com>
Co-authored-by: wang.yuqi <yuqi.wang@daocloud.io>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [9552852](https://github.com/vllm-project/vllm/commit/95528527eab9077aa4eb1d21ccdc20ef18eb5c95)

- **作者**: Wei Zhao
- **时间**: 2026-06-28T21:36:23Z
- **提交信息**: [Bugfix][Mooncake] Fix Mooncake lookup prefixes with DCP > 1 (#46855)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>

### [c2127a2](https://github.com/vllm-project/vllm/commit/c2127a25c787492fea657b867a6c668a317166fb)

- **作者**: Micah Williamson
- **时间**: 2026-06-28T17:50:30Z
- **提交信息**: [ROCm][CI] Fix `rlhf_async_new_apis` Example On ROCm (#46895)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [03c6d01](https://github.com/vllm-project/vllm/commit/03c6d01c3028cd567ddddc54e1d8414a24dbe501)

- **作者**: fxmarty-amd
- **时间**: 2026-06-28T17:43:19Z
- **提交信息**: [OCP MX ] Add back emulation to available OCP MX backends list (#46629)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [4b643c4](https://github.com/vllm-project/vllm/commit/4b643c463e31e0513c4b722c8c0754685159c6fa)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-28T15:37:00Z
- **提交信息**: [GLM5] Fix minor typo (#46961)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [7544286](https://github.com/vllm-project/vllm/commit/7544286b04a860fcfb98725345f2b43a5023b844)

- **作者**: Gonzague de Carpentier
- **时间**: 2026-06-28T15:19:28Z
- **提交信息**: [Bugfix] Transformers backend: recompute `mm_token_type_ids` per request for M-RoPE (#46552)

Signed-off-by: Gonzague de Carpentier <decarpentierg@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [89876b0](https://github.com/vllm-project/vllm/commit/89876b0c548afdd932d41d5ef81b14347edb9ff7)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-28T15:17:39Z
- **提交信息**: [GLM5] Implement op fusion for GLM5/DSV3.2 (#46876)

### [5c91039](https://github.com/vllm-project/vllm/commit/5c91039c41bc0b6a4a4ab2dc5f62115946e38a30)

- **作者**: Wentao Ye
- **时间**: 2026-06-28T14:55:54Z
- **提交信息**: [GLM5.2 Perf] Replace MOE all-reduce with reduce-scatter, 3.1%~3.2 E2E Throughput improvement (#46635)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [5ecae32](https://github.com/vllm-project/vllm/commit/5ecae3266cd5e6b814e14368d615957ffe85fdef)

- **作者**: xaguilar-amd
- **时间**: 2026-06-28T14:52:00Z
- **提交信息**: [ROCm][Perf][MLA] Add AITER FlashAttention MLA prefill backend (`ROCM_AITER_FA`) (#45033)

Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Signed-off-by: Xavier Aguilar <Xavier.AguilarFruto@amd.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [6eb63a1](https://github.com/vllm-project/vllm/commit/6eb63a1da6996abad00323dc7e845dc868996524)

- **作者**: frida-andersson
- **时间**: 2026-06-28T08:37:44Z
- **提交信息**: [Bugfix][DSv3.2] Skip indexer weights for index-cache-skipped layers (#46600)

Signed-off-by: Frida Andersson <fanderss@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [09841ae](https://github.com/vllm-project/vllm/commit/09841ae705ce73967b3303cdda5c7046d7710f5f)

- **作者**: Ranran
- **时间**: 2026-06-28T07:07:33Z
- **提交信息**: [Render][Speculator] Add return_loss_mask to render endpoint for training data generation (#46846)

Signed-off-by: Ranran Haoran Zhang <ranzhang@redhat.com>
Co-authored-by: Benjamin Chislett <chislett.ben@gmail.com>

### [a2a92cb](https://github.com/vllm-project/vllm/commit/a2a92cbbaac1175de96fc6f4712b4bba789a0c02)

- **作者**: Matt
- **时间**: 2026-06-28T07:07:14Z
- **提交信息**: [Hardware][AMD][CI] Tweak mirrored tests; improve CI base dependency change detection (#46930)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [35e6c86](https://github.com/vllm-project/vllm/commit/35e6c86caaaced4fd1398739fb04140b65d6ca89)

- **作者**: Shanshan Shen
- **时间**: 2026-06-28T07:06:43Z
- **提交信息**: [Bugfix][MM][CG] Enable dual-path ViT CUDA graph for Step3-VL (#46034)

Signed-off-by: shen-shanshan <467638484@qq.com>
Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [c7ca0bc](https://github.com/vllm-project/vllm/commit/c7ca0bccae667934c29c654544131cdab046adfd)

- **作者**: Olga Miroshnichenko
- **时间**: 2026-06-28T07:04:08Z
- **提交信息**: [ROCm][Perf] Add Fused Shared Expert (FSE) support for GLM-4.5/6/7 (#44313)

Signed-off-by: Olga Miroshnichenko <olga.miroshnichenko@amd.com>
Signed-off-by: Mehdi Ghanimifard <mehdi.ghanimifard@amd.com>
Co-authored-by: Mehdi Ghanimifard <mghanimi@amd.com>
Co-authored-by: Mehdi Ghanimifard <mehdi.ghanimifard@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-29
**监控日期**: 2026-06-28
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5344
- **最后更新**: 2026-06-29T10:46:40Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: SuyanLi

## AI分析总结

### 昨日更新要点分析

#### 1. 主要更新类型
- **重构（Refactor）**：核心操作是代码重构，涉及复用已有的 `CFGParallelMixin`。

#### 2. 关键变更点及其与项目整体方向的关系
- **变更内容**：在 `Bagel`（可能是某个模型或模块）中，用 `CFGParallelMixin` 替代原有的独立实现，以实现 CFG（Classifier-Free Guidance，无分类器引导）并行去噪。
- **与项目方向的关系**：
  - 项目目标强调 **“fast”（快速）** 和 **“cheap”（低成本）** 的多模态模型服务。CFG 是扩散模型生成中常用的技术（如文本到图像、音频生成），并行去噪可以显著加速推理，降低延迟。
  - `Bagel` 可能是项目支持的某个多模态模型或特定组件，这一重构让代码更统一、易维护，符合 **“easy”（易用）** 目标。

#### 3. 对项目的影响和潜在意义
- **性能提升**：通过复用成熟的并行 mixin，避免重复实现带来的低效或错误风险，可能进一步提升 CFG 并行处理的稳定性和速度。
- **代码可维护性**：减少重复代码，降低未来扩展新模型时的工作量，加速项目迭代。
- **社区贡献**：来自外部开发者（bytedance），表明项目吸引了更多贡献者，生态在成长。

#### 4. 值得关注的技术点
- **`CFGParallelMixin`**：这是一个用于并行执行无分类器引导的混入类（Mixin），体现了对现代扩散模型推理优化的重视。
- **“Bagel”**：可能指代论文或模型名称（如 Bagel 多模态模型），需要关注其在 vllm-omni 中的实际角色。
- **去噪（Denoising）**：扩散模型的核心步骤，并行化是提升吞吐的关键。

#### 5. 结合项目背景，对项目发展的影响
- **对齐“全模态”愿景**：CFG 并行优化不止适用于图像，也可用于音频、视频等生成任务，助力实现真正的 omni-modality 服务。
- **底层基础设施夯实**：重构是成熟项目的标志，表明 vllm-omni 在从“可用”走向“高效”和“可扩展”，为支持更多模型类型（如文本、图像、语音的混合生成）打下基础。
- **方向性**：持续优化推理效率，降低用户成本，正是项目口号中“cheap”与“fast”的直接体现。

## 详细提交记录

### [1b318d1](https://github.com/vllm-project/vllm-omni/commit/1b318d11d17804c54c6ffa482efdd7abcb03657c)

- **作者**: SuyanLi
- **时间**: 2026-06-28T07:16:10Z
- **提交信息**: [Refactor] Reuse CFGParallelMixin in Bagel for CFG-parallel denoising (#4768)

Signed-off-by: suyan.li <suyan.li@bytedance.com>
Co-authored-by: suyan.li <suyan.li@bytedance.com>

---
