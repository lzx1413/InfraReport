# GitHub Stars 合并报告 - 2026-06-27

**合并日期**: 2026-06-28
**监控日期**: 2026-06-27
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


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2046
- **最后更新**: 2026-06-27T03:49:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2447
- **最后更新**: 2026-06-27T11:28:48Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2148
- **最后更新**: 2026-06-26T03:33:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5867
- **最后更新**: 2026-06-27T22:39:20Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Sebastian Huang, Jiayu Chang, kangbintNV

## AI分析总结

### 1. 主要更新类型
- **功能新增**：两条提交（#3708 和 #3375）分别扩展了 MoE 模块的 DeepSeek FP8 + LoRA 路径支持以及 MoE 全到全通信中的每 token LoRA 信息支持。
- **文档更新**：一条提交（#3725）补充了 `gated_delta_rule_mtp` 函数中缺失的 `ssm_state_indices` 参数文档。

### 2. 关键变更点及其与项目整体方向的关系
- **#3708**：允许 `trtllm_fp8_block_scale_routed_moe` 接受 `gemm1_lora_delta` 参数（BiasType::Mn），使 DeepSeek FP8 的 MoE 计算能够结合 LoRA 微调。这与 FlashInfer 长期支持的混合精度、多框架（如 TensorRT-LLM）推理需求一致，尤其是在 MoE 架构广泛使用的 LLM 推理场景中。
- **#3375**：将 MoE 全到全（a2a）通信的 payload 容量从 4 提升到 5，并加入 per-token LoRA adapter ID 的传递。这属于分布式推理中多租户 / 多任务 LoRA 服务的基础设施，与项目中“高效 GPU 内核 + 可扩展分布式推理”的目标紧密相关。
- **#3725**：完善 `gated_delta_rule_mtp`（一种状态空间模型的解码算法）的 API 文档，提升开发者体验和接口可维护性，属于项目长期可持续性的基础工作。

### 3. 对项目的影响和潜在意义
- **MoE 功能增强**：两项 MoE 相关提交共同强化了 FlashInfer 在混合专家模型（如 DeepSeek V2/V3）场景下的灵活性和性能。`per-token LoRA` 支持使得在同一批量中同时服务多个微调版本的模型成为可能（如多用户 LoRA 适配），显著提升推理服务资源利用率。
- **通信优化铺垫**：通过调整 payload 结构，为后续更复杂的分布式 LoRA 调度（如跨节点并行）铺平了路径，对大规模 GPU 集群部署具有实际价值。
- **文档合规性**：修复 API 文档缺失问题，降低了用户误用的风险，也避免了自动化 API diff 工具产生错误警报。

### 4. 值得关注的技术点
- **DP8 与 LoRA 的融合**：DeepSeek FP8（DSFp8）采用块级缩放量化，配合 LoRA delta 路径时需要对 bias 类型 `Mn` 做特殊处理（而非传统的 `Neg` 或 `Zero`），这涉及内核中 scale 和 bias 的重新映射。
- **通信 payload 扩容**：`kMaxPayloads` 从 4 增加到 5，需要同步更新所有相关的 buffer 大小、校验逻辑以及工作区分配，稍有不慎就会导致越界或数据错乱。提交中已有对应测试覆盖。
- **双向互斥约束**：`ssm_state_indices` 与 `intermediate_states_buffer` 互斥，且要求 `disable_state_update=False`，体现了推理内核中精细化的状态管理设计。

### 5. 基于项目背景的综合影响
FlashInfer 定位为“专为推理设计的高性能 GPU 内核库”，其核心优势在于紧耦合最新模型计算模式（如 MoE、状态空间模型）并优化显存和通信。昨日更新体现了两个明确的发展方向：
- **服务化 LoRA 支持**：从内核层（#3708）和分布式通信层（#3375）同时发力，使 FlashInfer 成为支持 **multi‑tenant LoRA serving** 的推理后端，这在 LLM 行业实际落地中需求迫切（如为不同用户提供定制模型）。
- **文档与接口严谨性**：持续完善 API 文档（#3725）有助于吸引社区贡献者，降低集成门槛，符合该库从学术原型转向工业级工具的成熟趋势。

整体而言，这些提交表明 FlashInfer 正在从“高效单机内核”向“分布式、多租户推理框架”迈进，巩固其在高性能 LLM 推理生态中的关键地位。

## 详细提交记录

### [c35fb99](https://github.com/flashinfer-ai/flashinfer/commit/c35fb9935cee26d1cc2c374926ae21fc2c33830a)

- **作者**: Sebastian Huang
- **时间**: 2026-06-27T22:39:13Z
- **提交信息**: feat(moe): enable DSFp8 + LoRA delta path (#3708)

## 📌 Description

Enables the DeepSeek FP8 path of `trtllm_fp8_block_scale_routed_moe` to
accept a `gemm1_lora_delta` argument (`BiasType::Mn`).

## 🔍 Related Issues

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

Validated on B200 against the live public cubin mirror.

```
$ pytest tests/moe/test_trtllm_gen_fused_moe.py::test_moe_lora_delta -k "MxFp8 or DSFp8"

test_moe_lora_delta[Swiglu-Shuffled_BlockMajorK-Renorm-MxFp8-1024-1024-8]   SKIPPED   (MxFp8 requires MajorK)
test_moe_lora_delta[Swiglu-Shuffled_BlockMajorK-Renorm-MxFp8-1024-1024-128] SKIPPED   (MxFp8 requires MajorK)
test_moe_lora_delta[Swiglu-Shuffled_BlockMajorK-Renorm-DSFp8-1024-1024-8]   PASSED    (new)
test_moe_lora_delta[Swiglu-Shuffled_BlockMajorK-Renorm-DSFp8-1024-1024-128] PASSED    (new)
test_moe_lora_delta[Swiglu-Shuffled_MajorK-Renorm-MxFp8-1024-1024-8]        PASSED    (baseline)
test_moe_lora_delta[Swiglu-Shuffled_MajorK-Renorm-MxFp8-1024-1024-128]      PASSED    (baseline)
test_moe_lora_delta[Swiglu-Shuffled_MajorK-Renorm-DSFp8-1024-1024-8]        PASSED    (new)
test_moe_lora_delta[Swiglu-Shuffled_MajorK-Renorm-DSFp8-1024-1024-128]      PASSED    (new)

6 passed, 2 skipped, 8 deselected, 2 warnings in 750.74s
```

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

## Release Notes
* **New Features**
* Expanded LoRA-delta support for FP8 Block-Scale MoE, including
DeepSeek FP8 variants, and improved configuration generation for
additional bias cases.
* **Bug Fixes**
  * Corrected DeepSeek FP8 bias/shuffle handling for bias type **Mn**.
* Fixed activation-output selection when returning intermediate
activations for DeepSeek FP8.
* Relaxed prior validation/restrictions so FP8 block-scale MoE accepts
LoRA-delta where applicable.
* **Tests**
* Extended MoE LoRA-delta coverage with verification of a
post-activation FC1 intermediate output.
* **Chores**
  * Updated BMM artifact download path and checksum manifest.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2099bac](https://github.com/flashinfer-ai/flashinfer/commit/2099bac460994d2e6532935f1ad760a79a153f52)

- **作者**: kangbintNV
- **时间**: 2026-06-27T10:02:31Z
- **提交信息**: docs(gdn): document missing ssm_state_indices param in gated_delta_rule_mtp (#3725)

## Summary

- `flashinfer.gdn_decode.gated_delta_rule_mtp` had `ssm_state_indices`
present in the function signature but entirely absent from the
NumPy-style docstring, causing API-diff alerts.
- Add a full parameter entry describing: shape `[B, T]` / dtype `int32`,
per-token pool-scatter semantics (FLA-style speculative decoding), and
constraints (`T >= 2`, `disable_state_update=False`, mutually exclusive
with `intermediate_states_buffer`).
- Cross-link `intermediate_states_buffer` entry to note the mutual
exclusivity.

## Test plan

- [ ] Read the rendered docstring
(`help(flashinfer.gdn_decode.gated_delta_rule_mtp)`) and verify the new
entry appears correctly between `intermediate_states_buffer` and
`disable_state_update`.
- [ ] Run existing GDN decode tests to confirm no regressions: `pytest
tests/gdn/test_decode_delta_rule.py`

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Documentation**
  * Clarified the `gated_delta_rule_mtp` parameter documentation.
* Added detailed guidance for `ssm_state_indices`, including expected
shape (`[B, T]`), dtype (`torch.int32`), default behavior, and key
constraints (e.g., `T >= 2`, `disable_state_update=False`).
* Documented compatibility rules, including mutual exclusivity with
intermediate state buffers.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: cindyz <cindyz@nvidia.com>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [0cb2bc9](https://github.com/flashinfer-ai/flashinfer/commit/0cb2bc9baee7ee3f8a09bafcb940fed1cf2d2bcf)

- **作者**: Jiayu Chang
- **时间**: 2026-06-27T07:11:19Z
- **提交信息**: feat(comm): Support per-token LoRA Info in MoE a2a comm payloads (#3375)

<!-- .github/pull_request_template.md -->

## 📌 Description

- Bump `kMaxPayloads` from 4 → 5 so the dispatch can carry additional
per-token LoRA adapter ID with blocked scale dtypes
  - LoRA support in single node / MNNVL Tests and benchmarks

cc: @djns99 
  
<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues
- implement #3109 
- Umbrella #3107 
- Related #3108 
- Prev. #3153 

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.). **Only tested on single
node multi GPUs**

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Per-token LoRA adapter IDs added to MoE all-to-all dispatch/combine as
an extra int32 payload; payload capacity increased to accommodate them.
* **Documentation**
* Benchmark docs updated with a multi-tenant LoRA launch example and a
new flag to enable LoRA.
* **Tests**
* Unit and integration tests extended and re-parameterized to cover
LoRA-enabled dispatch and combine scenarios.
* **Chores**
* Workspace sizing and communication accounting updated to include the
extra LoRA payload.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3777
- **最后更新**: 2026-06-27T22:39:11Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: William Lin, KyleNeverGivesUp, Satyam Srivastava

## AI分析总结

### 主要更新类型
- **Bug修复**（2项）：包括文档构建失败和VAE编译功能未生效。
- **文档更新**（1项）：重构贡献指南、CI/CD和测试文档结构。

### 关键变更点与项目方向关系
1. **修复 `enable_torch_compile_vae` 实际不生效的问题**  
   - 确保 Wan VAE 能被 `torch.compile` 正确编译，从而加速视频生成/处理中的VAE推理。  
   - 与项目核心目标（高效视频生成）直接相关，属于性能基础设施的修正。

2. **修复文档构建错误**  
   - 保证在线文档的可用性，降低用户和贡献者的使用门槛，有利于社区扩展。

3. **重构贡献/CI/CD/测试文档**  
   - 规范开发流程，统一贡献标准，推动项目从实验阶段向稳定协作迈进。

### 对项目的影响与潜在意义
- **性能提升**：修正VAE编译后，Wan等视频模型在推理阶段的VAE部分可获得PyTorch JIT优化，减少延迟，对大规模视频生成或微调任务影响显著。
- **可维护性**：修复文档构建、重构贡献指南，降低新贡献者学习成本，提升项目长期迭代的可持续性。
- **稳定性**：CI/CD文档的重构可能伴随工作流改进（如自动化测试），减少回归风险。

### 值得关注的技术点
- `torch.compile` 作用于Wan VAE的具体实现方式（如是否使用`torch.compile(model, ...)`，可能涉及动态形状或自定义算子）。
- 修复可能导致之前未生效的编译路径被激活，需要留意内存消耗或图模式下的兼容性（如模型导出、量化）。

### 结合项目背景的发展影响
FastVideo 旨在提供快速、易用的视频生成工具（从README看有文档、快速启动、周会等成熟社区迹象）。昨日的更新：
- **直接推进核心功能**：VAE编译的修补使性能优化落地，更接近“Fast”的目标。
- **强化社区基础**：文档建设表明项目正从代码仓库转向开发者友好平台，符合README中展示的社区协作生态（Slack、周会等），有助于吸引更多贡献者参与Wan等模型的优化。

## 详细提交记录

### [6be280c](https://github.com/hao-ai-lab/FastVideo/commit/6be280c91492c980d63f2a52a4312cc151bba6db)

- **作者**: William Lin
- **时间**: 2026-06-27T20:00:09Z
- **提交信息**: [bugfix]: fix docs build  (#1502)

### [3ccdec9](https://github.com/hao-ai-lab/FastVideo/commit/3ccdec9798a8d8764524d01774019a0127bc4592)

- **作者**: KyleNeverGivesUp
- **时间**: 2026-06-27T19:30:59Z
- **提交信息**: [bugfix] Make enable_torch_compile_vae actually compile the Wan VAE (#1498)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [8658f77](https://github.com/hao-ai-lab/FastVideo/commit/8658f774f30684e87c12859ddc1e18181cc75710)

- **作者**: Satyam Srivastava
- **时间**: 2026-06-27T18:46:18Z
- **提交信息**: [docs] Restructure contributing CI/CD and testing docs (#1501)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33942
- **最后更新**: 2026-06-27T08:50:26Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
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


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12641
- **最后更新**: 2026-06-27T22:15:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29720
- **最后更新**: 2026-06-27T22:47:53Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 9
- **主要提交者**: Aditya Kamat, Brayden Zhong, jonah-berman

## AI分析总结

根据提供的提交记录和项目背景（SGLang 是一个专注于高性能 LLM/Diffusion 模型推理的框架，支持多模型、多硬件），昨日更新的要点总结如下：

---

### 1. 主要更新类型
- **性能优化**（最多）：包括 DSA 索引器 Q/K 路径的 kernel 融合、MLA 下投影的 JIT 融合 GEMM、LTX2.3 CFG 路径优化。
- **功能新增**：支持百度不限量 OCR 模型、原生 Exa 搜索支持、minimax-m3 的 mem-cache/HiCache/稀疏 KV 池、HiSparse 的 NIXL DRAM KV 目标支持。
- **Bug 修复**：修复 DeepSeek V4 PP HiCache 的 SWA 分配和层映射问题。
- **文档更新**：完善扩散模型 cookbook 概述、更新 Ascend NPU 文档、GLM-5.2 NVFP4 调优配方与基准。
- **重构/CI**：扩散模型 CI 重构。

---

### 2. 关键变更点与项目方向的关系
- **Kernel 融合与 JIT GEMM**：针对 DSA V3.2、GLM-5.x、MLA 下投影等核心注意力计算进行极致优化，直接提升推理吞吐与延迟，契合项目“高性能推理”目标。
- **稀疏 KV 缓存扩展（HiCache/NIXL）**：支持 DRAM 作为 KV 缓存目标（NIXL），以及 HiSparse 的稀疏池，为长上下文和异构内存提供新选项，增强可扩展性。
- **新模型与工具集成**：百度 OCR、Exa 搜索、minimax-m3 等扩展了多模态与外部工具能力，符合项目“多模型、多模态”定位。
- **扩散模型优化**：LTX2.3 CFG 路径优化与 CI 重构，持续改进扩散模型推理质量与开发效率。
- **NPU 文档修复**：提升 Ascend NPU 用户的体验，支持更多硬件后端。

---

### 3. 对项目的影响和潜在意义
- **推理效率提升**：DSA/MLA 的 kernel 融合可减少显存访问与 kernel 启动开销，尤其对大规模注意力模型（如 DeepSeek、GLM-5）影响显著。
- **长上下文能力增强**：HiCache 与 NIXL 支持允许更灵活的 KV 缓存管理，有助于处理超长序列。
- **模型生态扩展**：新增 OCR、搜索等工具链，提升 SGLang 作为“模型服务引擎”的实用性。
- **硬件兼容性**：SM120 支持（通过 MLAP JIT）、NPU 文档修复，覆盖更多加速器。
- **代码质量**：CI 重构和文档改进降低了贡献门槛，提升了项目可持续性。

---

### 4. 值得关注的技术点
- **Fused DSA indexer Q/K paths**：将索引器中的 Q/K 路径在单个 kernel 内完成，减少全局内存读写和 kernel 启动次数。
- **JIT fused A GEMM for MLA down projection**：动态生成针对 GLM-5 隐藏尺寸和 SM120 的优化 GEMM，展示了 JIT 编译在适配新硬件/模型时的灵活性。
- **HiSparse + NIXL DRAM KV**：将稀疏 KV 缓存的目标扩展到 DRAM（而不是仅限 HBM），可能利用 CPU 内存或池化内存作为缓存，降低显存压力。
- **NVFP4 配方**：针对 GB300 的 4-bit 浮点量化调优，体现对前沿低

## 详细提交记录

### [073de15](https://github.com/sgl-project/sglang/commit/073de150530ab27e0646492ec00016c727f0d7f7)

- **作者**: Brayden Zhong
- **时间**: 2026-06-27T21:29:56Z
- **提交信息**: Fuse the DSA (V3.2, GLM-5.x) indexer Q/K paths into single kernels (#27705)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>
Co-authored-by: Kaixi <kaiximatteoc@nvidia.com>

### [e4253b3](https://github.com/sgl-project/sglang/commit/e4253b39e22df77d52a9bc87528173e1f2a5bccf)

- **作者**: Brayden Zhong
- **时间**: 2026-06-27T20:32:06Z
- **提交信息**: Support JIT fused A GEMM (MLA down projection) and support GLM-5 hidden size, SM120 (#27397)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [592f6c8](https://github.com/sgl-project/sglang/commit/592f6c849bf972370782d915c7a6528c158c2c80)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-27T16:19:38Z
- **提交信息**: [minimax-m3] Split 2/4: mem-cache / HiCache / sparse KV pool (#28713)

Co-authored-by: hzh0425 <hzh0425@apache.org>

### [cfd911a](https://github.com/sgl-project/sglang/commit/cfd911ad6e7aeef2a6c2d2fdfa9eb40c8612c12b)

- **作者**: Mick
- **时间**: 2026-06-27T16:10:21Z
- **提交信息**: docs: refine diffusion cookbook overview (#29507)

### [1589603](https://github.com/sgl-project/sglang/commit/158960311468342ccc2ab4342a4f53372d042a90)

- **作者**: Aditya Kamat
- **时间**: 2026-06-27T15:36:19Z
- **提交信息**: model: support baidu unlimited-ocr (#29186)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [b030b1a](https://github.com/sgl-project/sglang/commit/b030b1a5f3636ba929f59b74be4261a9c09c6364)

- **作者**: ishandhanani
- **时间**: 2026-06-27T14:32:29Z
- **提交信息**: hisparse: support NIXL DRAM KV destinations for HiSparse (#27563)

Co-authored-by: Zhangheng <hzh0425@apache.org>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [c1b5c7e](https://github.com/sgl-project/sglang/commit/c1b5c7e49959d2259c9fadb6b12c534613343048)

- **作者**: hjzhang
- **时间**: 2026-06-27T14:19:14Z
- **提交信息**: Fix DeepSeek V4 PP HiCache SWA allocation and layer mapping (#29106)

Co-authored-by: hjzhang <zhanghjzzz@qq.com>
Co-authored-by: hzh0425 <hzh0425@apache.org>

### [2f34dbe](https://github.com/sgl-project/sglang/commit/2f34dbe372633a1efcf73b8cb40f95a76e05c2f2)

- **作者**: jonah-berman
- **时间**: 2026-06-27T13:41:09Z
- **提交信息**: Add native Exa-backed web_search support (#29342)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [3306233](https://github.com/sgl-project/sglang/commit/33062339616b1e09b1cf81e015575799dd4246c2)

- **作者**: Mick
- **时间**: 2026-06-27T11:23:14Z
- **提交信息**: [diffusion] optimize: optimize LTX2.3 CFG path (#28624)

### [91f9e73](https://github.com/sgl-project/sglang/commit/91f9e7372db28e791cf9b62f7a7917cf7dd92528)

- **作者**: Mick
- **时间**: 2026-06-27T11:22:27Z
- **提交信息**: [diffusion] CI: refactor CI (#28762)

### [a3c5e28](https://github.com/sgl-project/sglang/commit/a3c5e286f625e993ef6bcf859824fa7fe62b7e5c)

- **作者**: amote-i
- **时间**: 2026-06-27T10:23:11Z
- **提交信息**: [NPU] [DOC] Fix and update Ascend NPU docs (#29501)

### [e0c0c0a](https://github.com/sgl-project/sglang/commit/e0c0c0a45cb1bda90392bfa2bba4184f5b0638a0)

- **作者**: zijiexia
- **时间**: 2026-06-27T08:01:28Z
- **提交信息**: [Cookbook] GLM-5.2: tune GB300 NVFP4 recipes + fill benchmarks (#29486)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1210
- **最后更新**: 2026-06-26T11:07:28Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 84576
- **最后更新**: 2026-06-27T23:07:18Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 9
- **主要提交者**: Fangzhou Ai, xiaolinchen, jj shao

## AI分析总结

### 1. 主要更新类型

- **Bug修复**：5项（#46928, #46782, #46818, #46915, #46927）
- **性能优化**：2项（#46474, #46184），均为 **ROCm/AMD** 专用优化
- **CI/测试调整**：2项（#46928 包含CI测试修复，#46905 队列迁移）
- **推测解码改进**：1项（#46878）

### 2. 关键变更点及其与项目方向的关系

| 提交 | 变更内容 | 与项目目标的关系 |
|------|----------|------------------|
| #46928 | AMD CI：Whisper多LoRA测试改用TRITON_ATTN | 保证AMD硬件上的兼容性，降低用户使用门槛 |
| #46878 | 推测解码使用fp32均匀阈值接受 | 提升推测解码的稳定性/正确性，对**fast**目标有益 |
| #46782 | 修复分块嵌入聚合中的request-id元数据问题 | 确保API元数据正确传递，增强**easy**使用体验 |
| #46818 | 修复Fp8线性方法中层类型注解 | 微小修复，防止运行时类型错误 |
| #46927 | 修复H100冷启动子进程失败断言 | 提高CI可靠性，间接保障**cheap**（减少重复失败） |
| #46915 | 修复sm90上mxfp4 fused MoE测试（权重/缩放交织问题） | 保证新架构测试正确性 |
| #46474 | ROCm：为Minimax M3模型融合共享专家 | 显著提升AMD GPU上MoE推理吞吐，体现**fast & cheap** |
| #

## 详细提交记录

### [9036c89](https://github.com/vllm-project/vllm/commit/9036c89ee410b30913ca8b7d362a7d0805583b51)

- **作者**: Matt
- **时间**: 2026-06-27T22:30:49Z
- **提交信息**: [Hardware][AMD][CI] Patch Whisper multi LoRA test to use TRITON_ATTN for now (#46928)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [b6caeb5](https://github.com/vllm-project/vllm/commit/b6caeb5a0966103c6df22f019270d66233e1b687)

- **作者**: Giancarlo Delfin
- **时间**: 2026-06-27T21:09:25Z
- **提交信息**: [Model Runner V2][Spec Decode] Use fp32 uniform threshold for acceptance (#46878)

### [8bf064f](https://github.com/vllm-project/vllm/commit/8bf064f8d3408ca89cabc2f071adc696314c867e)

- **作者**: Taneem Ibrahim
- **时间**: 2026-06-27T20:57:47Z
- **提交信息**: Fixed chunked embedding aggregation with request-id metadata (#46782)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [ea2ead1](https://github.com/vllm-project/vllm/commit/ea2ead1db33dafb067aa64d4ce7b9c2150c12091)

- **作者**: jj shao
- **时间**: 2026-06-27T20:23:59Z
- **提交信息**: [Misc] Fix incorrect layer type annotation in Fp8LinearMethod (#46818)

Signed-off-by: shaojinjie.sjj <shaojinjiesjj@gmail.com>
Co-authored-by: shaojinjie.sjj <shaojinjiesjj@gmail.com>

### [56aa067](https://github.com/vllm-project/vllm/commit/56aa067bf05a7bc26f0fa017774e8521ccae7144)

- **作者**: Wentao Ye
- **时间**: 2026-06-27T20:17:33Z
- **提交信息**: [CI Bug] Fix h100 `AssertionError: Cold-start child failed` (#46927)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [35e3850](https://github.com/vllm-project/vllm/commit/35e3850fa9499b99f0b32ee8e9d5551a290d9c54)

- **作者**: xiaolinchen
- **时间**: 2026-06-27T18:30:10Z
- **提交信息**: [Bugfix][Test] Fix test_flashinfer_cutlass_mxfp4_fused_moe on sm90 (stale weight/scale interleave) (#46915)

Signed-off-by: wentian-byte <2990624738@qq.com>

### [51a9956](https://github.com/vllm-project/vllm/commit/51a99565c398c8320de8131e07731c75c52eb87c)

- **作者**: Fangzhou Ai
- **时间**: 2026-06-27T12:34:17Z
- **提交信息**: [ROCm][Perf] Fused shared expert for Minimax M3 (#46474)

Signed-off-by: Fangzhou-Ai <fangzhouai@gmail.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [867fd5e](https://github.com/vllm-project/vllm/commit/867fd5e8ed6b0bfcf84b24f82658c9fb698a6d35)

- **作者**: Hongxia Yang
- **时间**: 2026-06-27T10:22:57Z
- **提交信息**: [ROCm][Perf] Use flydsl moe with Minimax-M3 mxfp8 weights on gfx950 and implemented moe-backend selection (#46184)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Tan Pin Siang <tanpinsiang@gmail.com>

### [9fd00ee](https://github.com/vllm-project/vllm/commit/9fd00ee006ccd4996bbc756397b039343d2fde94)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-27T09:08:54Z
- **提交信息**: [ROCm][CI] Move remaining mi250_2 tests out of the MI250 queue (#46905)

Signed-off-by: Codex <codex@example.invalid>
Co-authored-by: Codex <codex@example.invalid>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-28
**监控日期**: 2026-06-27
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5295
- **最后更新**: 2026-06-27T21:52:53Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yueqian Lin

## AI分析总结

好的，以下是对昨日仅有的一个提交的分析总结：

### 1. 主要更新类型
- **Bug修复**：本次提交是一个明确的缺陷修复，无新增功能、性能优化或文档改动。

### 2. 关键变更点及其与项目整体的关系
- **变更点**：修复了 **CosyVoice3** 模型在生成语音时，未能将 `ref_text`（参考文本）正确包裹在指令模板（instruction template）中的问题（对应上游 PR #4644 和 #4756 的向后移植）。
- **与项目关系**：vllm-omni 的目标是“为所有人提供易用、快速、低成本的通用多模态模型服务”，语音（语音合成/语音处理）是其中核心模态之一。CosyVoice3 作为一个语音生成模型，其推理正确性直接影响该项目在多模态服务中的可用性和用户信任度。

### 3. 对项目的影响和潜在意义
- **提升稳定性**：修复了一个潜在的推理错误，避免因 `ref_text` 未按正确格式处理而导致语音输出异常或模型崩溃。
- **增强兼容性**：确保 CosyVoice3 与 vllm-omni 的指令模板机制保持一致，为后续集成更多语音模型扫清障碍。
- **用户侧影响**：使用 CosyVoice3 进行语音合成的用户将获得更可靠的输出结果，无需额外手动处理文本格式。

### 4. 值得关注的技术点
- **指令模板机制**：vllm-omni 可能采用统一的指令模板来规范不同模态模型的输入格式（如文本、音频、图像等），`ref_text` 的封装方式错误会破坏这一抽象，本次修复体现了模板化输入设计的重要性。
- **向后移植**：提交中合并了两个 PR，表明这是来自上游仓库的补丁适配，项目在积极跟进上游修复，保持代码同步。

### 5. 对项目发展的影响（结合 README 背景）
- vllm-omni 强调“全模态”（omni-modality），语音是除文本、图像外的关键能力。本次修复使得 CosyVoice3 这一语音模型在 vllm-omni 中运行更加稳定，直接支持了项目“为所有模态提供易用服务”的核心愿景。
- 单一 Bugfix 虽小，但体现了项目团队对多模态模型的持续维护和精细化打磨，有助于吸引更多语音相关用户和开发者，推动项目成为真正的“一站式”多模态推理平台。

## 详细提交记录

### [92f7208](https://github.com/vllm-project/vllm-omni/commit/92f72085597b26bc6041dc00a98e4f5bcc883bbe)

- **作者**: Yueqian Lin
- **时间**: 2026-06-27T21:38:33Z
- **提交信息**: [Bugfix] CosyVoice3: wrap ref_text in instruction template (#4644) (#4756)

---
