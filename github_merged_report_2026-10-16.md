# GitHub Stars 合并报告 - 2026-10-16

**合并日期**: 2026-10-17
**监控日期**: 2026-10-16
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


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2246
- **最后更新**: 2026-10-16T11:52:03Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Coach257

## AI分析总结

## 提交分析总结（VeOmni，2025年）

### 1. 主要更新类型
本次提交包含两类变更：
- **重构**：分布式并行逻辑的内部清理
- **功能新增 / CI 增强**：为 NPU 测试新增 Ascend GatedDeltaNet kernel 的测试覆盖

总体偏向工程质量与平台适配层面的改进，而非新增核心训练能力。

### 2. 关键变更点及与项目方向的关系

**变更一：移除 Ulysses 分组覆盖逻辑**
- Ulysses 是序列并行（Sequence Parallelism）的一种实现方式，常与 DeepSpeed/ZeRO 结合用于长序列训练。
- 此次重构移除了对其自定义分组的覆盖代码，说明项目在简化分布式并行的配置路径，减少特殊分支，使并行策略的管理更统一。
- 这与 VeOmni "Model-Centric Distributed Recipe Zoo" 的定位一致——即通过标准化、可组合的分布式配方来降低多模态大模型训练的配置复杂度。

**变更二：Ascend GatedDeltaNet kernel 覆盖 NPU 测试**
- GatedDeltaNet 是一种基于门控 DeltaNet 的线性注意力/状态空间类架构，属于新兴的高效注意力机制。
- 将其 kernel 纳入 NPU（昇腾）测试体系，表明项目在积极扩展国产 AI 芯片（华为昇腾）的硬件适配，确保关键算子在 NPU 后端的正确性与稳定性。
- 这与 VeOmni 支持多硬件后端（CUDA/NPU 等）的跨平台训练目标直接契合。

### 3. 对项目的影响和潜在意义
- **降低维护成本**：去除 Ulysses 分组的特殊覆盖减少了分布式代码中的隐式行为，使并行配置更可预测，有利于社区贡献者理解和扩展。
- **提升 NPU 后端可信度**：新增 kernel 级测试意味着在昇腾平台上训练含 GatedDeltaNet 模块的模型时，底层算子的正确性有测试保障，为在国产硬件上大规模使用新型注意力架构铺路。
- **体现对新型架构的前瞻布局**：GatedDeltaNet 属于相对前沿的序列建模架构，对其 kernel 的正式测试支持暗示 VeOmni 可能在内部或社区中已有基于该架构的模型训练需求。

### 4. 值得关注的技术点
- **Ulysses 序列并行的抽象层级变化**：移除 override 后，Ulysses 分组应完全交由底层框架（如 DeepSpeed）管理，值得关注这是否会影响某些极端并行配置下的行为。
- **GatedDeltaNet + NPU 的组合**：这是少见的将新型线性注意力 kernel 显式纳入国产芯片测试矩阵的案例，对关注国产硬件生态的用户有参考价值。
- **Co-authored-by Cursor**：本次提交由 AI 编码助手协同完成，反映了该项目已开始将 AI 辅助工具纳入日常开发流程。

### 5. 对项目整体发展的意义
VeOmni 的核心目标是为任意模态模型提供可扩展、标准化的分布式训练方案。本次两笔提交虽小，但方向明确：
- **简化分布式配方**（移除特殊覆盖）使"Recipe Zoo"中的配方更干净、更易组合复用；
- **扩展硬件生态**（NPU kernel 测试）增强了 VeOmni 在多元硬件环境下的可用性，尤其是在国产算力自主可控的背景下具有战略价值。

两者共同强化了项目"工程化、可移植、可维护"的基础设施定位，为后续引入更复杂的多模态模型和更新的注意力架构（如 GatedDeltaNet 类）打下更稳固的基础。总体而言，这是一组典型的"磨刀不误砍柴工"式提交，对项目长期健康发展是积极信号。

## 详细提交记录

### [0c1d908](https://github.com/ByteDance-Seed/VeOmni/commit/0c1d90866612324d11323d578e9bc63520298022)

- **作者**: Coach257
- **时间**: 2026-10-16T11:09:31Z
- **提交信息**: [dist, parallel] refactor: remove the Ulysses group override (#1311)

### [bb41d1a](https://github.com/ByteDance-Seed/VeOmni/commit/bb41d1acfc06a9938513f8a605cf891f4ef5aca6)

- **作者**: Coach257
- **时间**: 2026-10-16T07:50:03Z
- **提交信息**: [ci, ops] feat: cover the Ascend GatedDeltaNet kernels in NPU tests (#1309)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2916
- **最后更新**: 2026-10-17T00:21:24Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: STwangyingrui, Zhuguanyu Wu, Chengtao Lv

## AI分析总结

## LightX2V 昨日提交分析

### 1. 主要更新类型
本次提交涵盖**性能优化**（InfiniteTalk 推理加速）、**功能新增**（强化学习支持）、**工具链迁移**（Codex 技能迁移）以及**文档更新**（Read the Docs 构建镜像、README 链接修复）四类，其中性能优化和功能新增是核心。

### 2. 关键变更点及与项目方向的关系

- **性能优化（#1623）**：针对 InfiniteTalk 模型在 8 张 A800 GPU 上的推理进行了系统级优化，采用 SLA + Triton、DiT 权重常驻内存、完整音频序列并行（Audio SP）、DiT 和 Wan VAE 的动态形状编译等技术。DiT 单步延迟从 4.82s 降至 1.64s（**2.94 倍加速**），分段延迟从 22.42s 降至 9.69s（**2.31 倍加速**）。这与 LightX2V "轻量视频生成推理框架" 的核心定位高度一致——通过工程手段持续降低视频生成的推理成本和延迟。

- **功能新增（#1618）**：引入 `lightx2v_rl` 模块，支持 QwenImage2.1-Turbo 模型的强化学习训练与推理，并集成了 Flow-GRPO、Flow-CPS 和 Geo-FSRL 三种 RL 算法。这表明 LightX2V 正在从纯推理框架向**推理-训练一体化**方向扩展，RL 技术可进一步优化视频/图像生成质量。

- **工具链迁移（#1624）**：将 Codex 相关技能配置迁移并更新仓库指引，属于开发流程层面的整理。

- **文档维护（#1621、#1622）**：更新 Read the Docs 构建镜像、恢复 RealtimeWAN README 链接，保障文档站正常运转。

### 3. 对项目的影响和潜在意义

- **性能优化**使得 InfiniteTalk（长音频驱动的视频生成模型）在生产环境中更具实用价值，近 3 倍的端到端加速意味着相同的硬件资源可以支撑更高的吞吐量或更低成本的部署。
- **RL 模块的加入**拓宽了项目的能力边界。如果 LightX2V 能够在推理框架内支持 RL 微调，用户可以在同一套代码库中完成"训练→推理"闭环，降低使用门槛。
- **文档和工具链维护**体现了项目对工程规范性和可持续发展的重视。

### 4. 值得关注的技术点

- **分阶段性能剖析方法论**：PR #1623 清晰地展示了每一步优化带来的延迟收益（Dense → SLA/Triton → 权重常驻 → Audio SP → 编译），这种渐进式优化的记录方式本身就是很好的工程实践范例。
- **动态形状编译支持**：对 DiT 和 Wan VAE 实现编译并支持动态形状，解决了视频生成中分辨率/长度变化导致的编译失效问题，是框架工程化的重要一步。
- **多种 RL 算法的集成**（Flow-GRPO、Flow-CPS、Geo-FSRL）：在同一框架内支持多种 RL 策略，为后续算法对比和用户选择提供了灵活空间。

### 5. 对项目发展的影响

结合 README 中 LightX2V 定位为"轻量视频生成推理框架"，本次更新在两个维度上推动了项目发展：一是**纵深方向**，通过系统级性能优化将核心推理路径的效率进一步压榨到接近硬件极限；二是**横向方向**，RL 模块的引入让项目从单纯的推理部署工具向更完整的生成式 AI 基础设施演进。两者结合，LightX2V 正在构建一个既快（高效推理）又强（可通过 RL 提升生成质量）的视频生成平台，与其开源、轻量、高性能的项目理念保持一致。

## 详细提交记录

### [9df2311](https://github.com/ModelTC/LightX2V/commit/9df231170eb2a36ee18eb7fab3e8506c87589dd3)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-16T11:43:28Z
- **提交信息**: chore(skills): migrate to Codex and update repository guidance (#1624)

### [ea2c913](https://github.com/ModelTC/LightX2V/commit/ea2c9133cd4d2e357cb505fb3f75a3b338451ba7)

- **作者**: Zhuguanyu Wu
- **时间**: 2026-10-16T11:01:52Z
- **提交信息**: [Feature] add lightx2v_rl (#1618)

- support QwenImage2.1-Turbo RL
- support Flow-GRPO, Flow-CPS and Geo-FSRL

### [b20c66b](https://github.com/ModelTC/LightX2V/commit/b20c66bf91dcd9b071182df858061c41c238c9ed)

- **作者**: STwangyingrui
- **时间**: 2026-10-16T10:16:08Z
- **提交信息**: [Perf] Optimize InfiniteTalk inference on A800 (#1623)

Optimize InfiniteTalk inference on eight A800 GPUs with SLA + Triton at
0.8 sparsity, resident DiT weights, full audio SP, and DiT/native Wan
VAE compilation with dynamic-shape support.
DiT step latency: Dense 4.82s → SLA/Triton 2.78s → resident DiT 2.63s →
full audio SP 1.70s → DiT compile 1.64s: 2.94× speedup.
Segment latency: Dense 22.42s → SLA/Triton 14.42s → resident DiT 13.55s
→ full audio SP 9.65s → DiT and VAE compile 9.69s: 2.31× speedup.

---------

Co-authored-by: Codex <codex@openai.com>

### [c00ab28](https://github.com/ModelTC/LightX2V/commit/c00ab283622baec6600248aa7abccc4a4856ccf1)

- **作者**: Chengtao Lv
- **时间**: 2026-10-16T07:26:49Z
- **提交信息**: recover original realtimewam readme link (#1622)

### [fb291c9](https://github.com/ModelTC/LightX2V/commit/fb291c9b11edd02588a28d0f81f82eeec5c1f056)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-16T07:03:37Z
- **提交信息**: docs: update Read the Docs build image (#1621)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2303
- **最后更新**: 2026-10-16T15:02:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6642
- **最后更新**: 2026-10-16T23:06:14Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 10
- **主要提交者**: Dhiraj Reddy (cuDNN/FlashInfer), Cindy Zhang, eigen

## AI分析总结

# FlashInfer 昨日提交分析（共 16 条）

## 一、主要更新类型

- **性能优化**（8条）：Blackwell MegaMoE 解码流水线、NVFP4 sparse-MLA split-KV 合并、NVLink MoE 通信核升级、SM107 launch 配置调优、autotuner 缓存协调、ICP indexer 几何优化、Muse-Spark 融合核、SSD Combined 融合扫描
- **功能新增**（4条）：NVFP4 LoRA 准备式适配器、topk_varlen 分页输出、GDN host-free prefill、Rubin 内核扩展
- **Bug 修复**（3条）：多流并发 top-k 状态冲突、CuTe-DSL JIT 缓存缺失处理、MoE pack 契约校验与 trace 注册遗漏
- **重构/破坏性变更**（1条）：移除已弃用的 MoeAlltoAll/MnnvlMoe

## 二、关键变更

**硬件前沿覆盖**：#6565 在 4×B300 上为 DeepSeek V4 Pro 稀疏 MegaMoE 解码实现最高 31.6% 延迟降低；#6584 为 MoK 包新增 sm_107a（Rubin）内核；#6580 补充 ICP indexer 多组 exchange-merge 几何配置，覆盖 B200 与 GB300。

**量化推理深化**：#6578 用 CUDA programmatic dependent launch 优化 NVFP4 sparse-MLA split-KV 合并，SASS 仅增 1 条 ACQBULK 指令；#6581 为 NVFP4 LoRA 引入"准备式适配器"，权重折叠一次后运行时复用，附带过期检测；#6544 将 Muse-Spark 的归一化、门控、残差与通信融合为单 kernel。

**MoE 通信重构**：#6047 移除 `MoeAlltoAll`/`MnnvlMoe`，`NVLinkOneSidedAlltoAll` 改为直接使用与 TensorRT-LLM 同步的 NVLink 单边通信核，支持 CFT counted writes 和最多 256 个 EP rank。

**推理解码优化**：#5312 为 topk_varlen 新增融合分页表输出，直接产出物理 KV 槽位索引；GDN host-free prefill 通过 ABI v2 消除每轮 prefill 的 D2H 同步，并修复 identity-key 缓存过期偏移问题。

**工程健壮性**：#3625 修复多 CUDA 流并发时 radix top-k 共享 scratch 导致结果损坏的问题；autotuner 修复分布式 profile 缓存不一致；#6591 修复 CI 失败；#6576 将 Cake 导出包 manifest 化，提升可移植性。

## 三、项目影响

- **推理延迟显著降低**：MegaMoE 在 1-256 token 范围延迟降低 26-32%；SM107 launch 调优在 H≥1024 场景最高加速 2.92 倍。
- **破坏性变更需迁移**：下游依赖旧 MoeAlltoAll API 的代码需转向 `NVLinkOneSidedAlltoAll` 或 `CakeAlltoAll`。
- **生态对齐加强**：与 vLLM（GDN TTFT 回归修复）、SGLang（分页输出）、TensorRT-LLM（NVLink 核同步）深度对接。
- **正确性与生产就绪性提升**：多流并发修复、LoRA staleness 检测（基于 pointer/version/shape 变更判定失效）、CI 恢复全绿。

## 四、值得关注的技术点

- **Programmatic Dependent Launch**：解码内核尾部仍在运行时即调度合并内核，实现流水重叠，是 CUDA 12+ 特性的精妙应用。
- **CFT counted writes**：接收方等待硬件字节计数器而非轮询完成标志，零额外内存分配。
- **PyTorch 流序分配器**：以 `torch.zeros` 替代手动缓存池，自动处理并发隔离与 CUDA 图捕获。
- **Prepared LoRA Adapter 过期检测**："信任但验证"设计，避免逐值比较开销。
- **Autotuner 分布式协调**：确保所有 rank 一致失效/保留缓存，避免 collective 错配挂起。

## 五、综合影响

本批提交体现 FlashInfer 三大发展主线：**深度适配 Blackwell/Rubin 架构**、**针对 MoE/MLA/Mamba/LoRA 等前沿模型架构优化**、**从单一内核向端到端系统级优化演进**。项目与主流推理框架的接口同步演进，量化路径从 GEMM 扩展到全融合算子面。但破坏性 API 移除和多后端分支增多也对版本兼容性与维护性提出更高要求，值得下游用户在升级时留意迁移成本。

## 详细提交记录

### [3c1d1c2](https://github.com/flashinfer-ai/flashinfer/commit/3c1d1c2fff9c26f355c3d18b3b3b15c79003828a)

- **作者**: Yanqin Zhai
- **时间**: 2026-10-16T23:06:08Z
- **提交信息**: add-new-decoding-pipeline-for-blackwell-megamoe (#6565)

<!-- .github/pull_request_template.md -->

## 📌 Description

Optimize sparse Blackwell MegaMoE dispatch and reduction, and add an
opt-in decoding backend with N128 and N64 configurations.

Performance on **4×B300, EP4, unlocked clocks**, using synthetic
DeepSeek V4 Pro shapes, **MXFP8 W8A8 with BF16 output**, and capacity
1024:

| Tokens/rank | Before PR (µs) | GenPhase N64/CGA2 (µs) | Latency
reduction |
|---:|---:|---:|---:|
| 1 | 144\.8 | 107\.2 | 26\.0% |
| 4 | 403\.3 | 286\.2 | 29\.0% |
| 16 | 1034\.6 | 707\.3 | 31\.6% |
| 64 | 1506\.6 | 1047\.1 | 30\.5% |
| 256 | 1546\.6 | 1069\.0 | 30\.9% |
| 1024 | 1576\.1 | 1331\.2 | 15\.5% |

## 🔍 Related Issues

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added opt-in Blackwell GenPhase MegaMoE support for MXFP8 E4M3, with
configurable tile and cluster geometry and separate top-k reduction.
* Exposed GenPhase APIs through the existing MegaMoE package and added
support for preprocessing prequantized weights.
* Added sparse routing for capacities up to 1,024 tokens per rank, with
invalid routes excluded from BF16 reductions.
* **Bug Fixes**
  * Improved sparse dispatch and tail-counter reset synchronization.
* **Documentation**
* Documented GenPhase configuration options, supported inputs, and
limitations.
* **Tests**
* Expanded coverage for CUDA graph replay, multirank routing, workspace
limits, staging, and GenPhase configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [626dc82](https://github.com/flashinfer-ai/flashinfer/commit/626dc820b3bcde86a49368cf641215724363f269)

- **作者**: Sam Mausberg
- **时间**: 2026-10-16T23:01:16Z
- **提交信息**: test(gdn): exercise the slot-slice fallback in fla_scatter_padded_pool (#5382)

<!-- .github/pull_request_template.md -->

## Description

`test_gdn_decode_bf16_state_fla_scatter_padded_pool` builds a padded,
non-contiguous pool but passes `pool_padded.clone()` to the kernel.
`clone()` preserves strides only for dense tensors, so the clone is
contiguous and the test compares the flat scatter path with itself. It
never compiles a `per_token_pool_scatter_flat=False` kernel.

The test now clones the backing allocation and re-slices it, asserts
that the pool under test is non-contiguous, and checks that the per-slot
padding is unchanged after the call (vLLM keeps conv state there).

Test-only. The slot-slice fallback is correct on SM120: it matches the
flat path bit for bit.

## Related Issues

Fixes #5381.

## Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

RTX 5070 Ti (SM120), CUDA 13.2, torch 2.14.0+cu130, nvidia-cutlass-dsl
4.8.0. `pytest tests/gdn/test_decode_delta_rule.py -k
fla_scatter_padded_pool` on a cold cache. Only this test was run; CI has
not run.

| | result | kernels compiled | wall |
| --- | --- | --- | ---: |
| main @ d7a7447c | 6 passed | 6, all flat | 21.9 s |
| this PR | 6 passed | 12: the same 6 plus 6 slot-slice | 41.5 s |

Five further warm-cache runs of the new test: 6 passed each time.

The issue asked whether the fixed test fails once the fallback is
broken. With each of these breaks applied to `gdn_decode_bf16_state.py`,
the test on main still passes 6/6 and the test in this PR fails 6/6:

- the fallback writes slot `pool_slot_t - 1`
- the wrapper drops the stride check, so a padded pool takes the flat
path and `reshape()` copies it
- the wide_vec fallback also stores one row past the slot's `HV` rows,
into the padding (caught by the padding check only)

## Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

- Merges cleanly with #5379. On the merged tree this test is 2 cases and
both pass.
- Every shape here has `B * HV >= 128` and routes to
`gdn_wide_vec_kernel`. The ILP4 kernel has its own copy of the fallback
(`B * HV < 128`), which is still not covered. Checked by hand at `B=1`,
`T=2` and `T=8`: it matches the flat path bit for bit. `batch_size=1`
would cover it; I left it out because it edits the decorator line next
to the one #5379 changes. I can add it here if wanted.

Developed with Claude Fable 5.1.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Tests**
  - Corrected coverage for non-contiguous pooled data handling.
- Added verification that per-slot padding remains unchanged after
processing.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [92f2b13](https://github.com/flashinfer-ai/flashinfer/commit/92f2b13f022ed2080c8ab8b6d29c7ce5536c3021)

- **作者**: eigen
- **时间**: 2026-10-16T22:48:46Z
- **提交信息**: perf(cake_dsv4): launch the NVFP4 sparse-MLA decode split-KV merge with programmatic dependent launch (SM100/SM103) (#6578)

## Summary

Re-exports the SM100 / SM103 DeepSeek-V4 NVFP4 sparse-MLA decode family
(`backend="cake"`, `kv_cache_format="nvfp4"`)
with one change, in the split-KV **merge** kernel and its launcher. The
merge now waits on the decode grid with
`griddepcontrol.wait`. It is launched with programmatic stream
serialization, so it can be scheduled while the decode
grid's tail is still running. The 16 decode kernel variants are
regenerated byte-identically (same generated source as
the previous delivery). The member set, the host route, the loader
registrations and the public API are unchanged.

- **What changes in the kernel.** The merge kernel's first statement is
now
`asm volatile("griddepcontrol.wait;" ::: "memory");`. It runs before the
kernel reads the decode partial outputs
(`partial_O`, `partial_lse`). This line is the only difference in the
merge's generated device source compared with the
previous delivery. SASS on SM100: `ACQBULK` +1, `NOP` -1, 288 -> 288
instructions. The generated binding launches the
merge with `cudaLaunchAttributeProgrammaticStreamSerialization`
(`programmaticStreamSerializationAllowed = 1`), so the
merge grid may be scheduled while the decode grid's tail is still
running. The wait blocks until the whole decode grid
has completed and its memory is visible. The merge reads the two partial
buffers only after the wait. It has no shared
memory, barriers or atomics of its own that could interact with the
decode. A static `pdl_dependency_before_wait`
check on both architectures proves that every access to the two partial
buffers comes after the wait on every
control path. The decode kernels issue no
`griddepcontrol.launch_dependents`; decode grid completion triggers the
dependent launch. A stream-ordered launch without the attribute
therefore behaves exactly as before, because the wait
  returns immediately when no prerequisite grid is in flight.
- **Numerics.** The merge arithmetic (exp2 / rcp split weights, fp32
accumulation in increasing split order, BF16
stores) is byte-identical source, and the decode kernels are regenerated
byte-identically. The outputs are **bitwise
identical** to the previous delivery. Per card (B200 / SM100 and GB300 /
SM103), the checks are:
  - seed gate: 174 / 174 rows bitwise (58 rows x 3 seeds)
- accuracy tables: 417 / 417 records identical (189 family + 228
contract)
- CUDA-graph replay: 84 / 84 (12 hardening rows x 7 members), including
6 graph rows with the PDL edge
  - source/export: bitwise on all 76 exported shapes

compute-sanitizer synccheck and memcheck are clean on both cards. As in
the previous deliveries, racecheck reaches the
  tool limit identically on the previous and the new kernel.
- **Why.** On the 36 split-KV rows per card (the rows that launch the
merge), the GPU span of the decode + merge kernel
pair is 0.767–0.912x of its previous value on B200 (geometric mean
0.834). On GB300 it is 0.762–0.905x (geometric
mean 0.809). Every row on both cards is below 1.0 by more than the 0.030
acceptance band. Single-kernel rows (no
merge launch) run identical decode source and are unaffected by
construction. Their family-table geometric mean
reads 0.991 (B200) / 0.987 (GB300), with same-code A/A 0.9999 / 1.0000.

| Row | B200 pair span, previous → new (us) | B200 ratio | GB300 pair
span, previous → new (us) | GB300 ratio |
|---|---|---|---|---|
| C-h16-k512-t1 | 10.00 → 8.03 | 0.803 | 10.29 → 7.92 | 0.770 |
| C-h16-k512-t8 | 11.81 → 9.06 | 0.767 | 11.33 → 8.64 | 0.763 |
| C-h16-k512-t32 | 13.12 → 11.04 | 0.842 | 12.64 → 10.18 | 0.805 |
| C-h32-k512-t1 | 10.77 → 8.61 | 0.799 | 11.09 → 8.45 | 0.762 |
| C-h32-k512-t8 | 12.10 → 9.82 | 0.812 | 12.13 → 9.34 | 0.770 |
| C-h32-k512-t32 | 14.45 → 12.14 | 0.841 | 14.18 → 11.30 | 0.797 |
| C-h64-k512-t1 | 12.03 → 10.27 | 0.854 | 11.98 → 9.22 | 0.769 |
| C-h64-k512-t8 | 14.08 → 11.52 | 0.818 | 13.06 → 10.59 | 0.811 |
| C-h64-k512-t32 | 16.99 → 14.83 | 0.873 | 16.42 → 13.63 | 0.830 |
| C-h128-k512-t1 | 14.02 → 11.39 | 0.813 | 13.54 → 10.82 | 0.799 |
| C-h128-k512-t8 | 16.35 → 13.73 | 0.840 | 14.66 → 12.22 | 0.834 |
| C-h128-k512-t32 | 20.51 → 18.02 | 0.878 | 19.17 → 16.77 | 0.875 |
| D-h16-m128-e132p2-t8 | 10.38 → 8.48 | 0.817 | 10.72 → 8.35 | 0.779 |
| D-h16-m128-e132p2-t32 | 12.24 → 10.18 | 0.831 | 12.38 → 9.82 | 0.793 |
| D-h128-m128-e132p2-t8 | 16.06 → 13.41 | 0.835 | 14.50 → 11.97 | 0.826
|
| D-h16-m128-e512p64-t8 | 12.32 → 9.60 | 0.779 | 12.08 → 9.28 | 0.768 |
| D-h16-m128-e512p64-t32 | 17.82 → 15.26 | 0.856 | 16.53 → 14.50 | 0.877
|
| D-h128-m128-e512p64-t8 | 16.96 → 14.75 | 0.870 | 16.69 → 13.92 | 0.834
|
| D-h16-m512-e512p64-t8 | 12.62 → 10.27 | 0.814 | 12.61 → 9.76 | 0.774 |
| D-h16-m512-e512p64-t32 | 18.50 → 15.90 | 0.860 | 16.80 → 14.86 | 0.885
|
| D-h128-m512-e512p64-t8 | 16.96 → 14.91 | 0.879 | 16.83 → 14.14 | 0.840
|
| D-h128-m512-e512p64-t32 | 28.64 → 26.11 | 0.912 | 26.91 → 24.35 |
0.905 |
| O-h16-k512-t32 | 12.46 → 10.53 | 0.845 | 12.45 → 9.95 | 0.799 |
| O-h128-k512-t32 | 20.48 → 17.92 | 0.875 | 19.04 → 16.64 | 0.874 |
| M-h16-m128-e512p64-t12 | 12.48 → 10.14 | 0.813 | 12.53 → 9.70 | 0.774
|
| M-h32-m128-e512p64-t12 | 14.37 → 11.58 | 0.806 | 13.28 → 10.88 | 0.819
|
| M-h64-m128-e512p64-t12 | 15.30 → 13.34 | 0.872 | 15.07 → 12.64 | 0.839
|
| M-h128-m128-e512p64-t12 | 17.50 → 15.44 | 0.882 | 17.31 → 14.62 |
0.845 |
| X-h16-k256-t32 | 12.16 → 9.95 | 0.818 | 12.16 → 9.31 | 0.766 |
| X-h16-m128-e512p32-t32 | 17.54 → 15.10 | 0.861 | 16.48 → 14.30 | 0.868
|
| H-02 | 12.10 → 9.66 | 0.799 | 12.03 → 9.25 | 0.769 |
| H-03 | 17.06 → 14.56 | 0.854 | 16.35 → 13.63 | 0.834 |
| H-04 | 12.19 → 10.11 | 0.829 | 12.10 → 9.36 | 0.774 |
| H-06 | 10.24 → 8.32 | 0.812 | 10.37 → 8.00 | 0.772 |
| H-09 | 12.35 → 9.66 | 0.782 | 12.32 → 9.47 | 0.769 |
| H-10 | 13.98 → 11.36 | 0.812 | 13.55 → 10.82 | 0.798 |
| geometric mean over the 36 rows | | 0.834 | | 0.809 |

Ratios below 1.0 are faster. Each ratio divides the pair span with the
launch attribute by the pair span without it. The pair span is the GPU
span of the decode + merge kernel pair, taken as the cold-L2 CUPTI
median and paired ABBA in one process. The span columns read previous →
new in microseconds. The A arm is the previous delivery's kernels
launched on the same native path without the attribute. The B arm is
this delivery. One native host call submits the two launches
back-to-back, with no host work in between. The same-code A/A twin band
is 0.0087 on B200 and 0.0029 on GB300 (acceptance band 0.030). In the
Python-driven host path, the decode -> merge submission gap is itself
host-bound on most rows (36/36 on GB300, 35/36 on B200). The pair-span
gain is therefore realized when the two launches are submitted
back-to-back natively or inside a CUDA graph. The exporter's graph-mode
protocol (Measurement section) recorded a 0.000 us median decode ->
merge gap on all 40 merge-launching rows per card.

## CI coverage note

The PR CI has no SM100 / SM103 runner, so the `backend="cake"` NVFP4
decode tests skip there on the architecture guard;
the route test (`tests/mla/test_cake_dsv4_nvfp4_route.py`, CPU-only)
exercises the plan rows in CI. GPU evidence is the
two-card run below (CUDA 13.4 toolchain). The `cake_dsv4` loader is
JIT-only (not part of the AOT build).

## Proof of identity

The 16 decode kernel variants are regenerated from the same generated
source as the previous delivery. The four member proofs below are the
same as in the previous delivery and have identical receipts on both
export runs.

The split-KV merge kernel was checked on its delivered text for each
architecture:
- Its object, compiled by the FlashInfer JIT with its own flags, maps
`griddepcontrol.wait` to `ACQBULK` at 1 site and contains no
`launch_dependents`.
- The generated binding carries the launch attribute.
- `nvcc -ptx` of the delivered kernel source shows exactly 1
`griddepcontrol.wait`.

None of the 16 delivered decode objects contains `ACQBULK` or `PREEXIT`.

| Export run | Member | sm_100a SASS-equal | sm_103a SASS-equal |
Refinement rounds / widenings | nvcc compiles (prove / probe) |
|---|---|---|---|---|---|
| B200 export | `swap` | 6/6 (alpha 6, sched 6) | 6/6 (alpha 6, sched 6)
| 1 / 1 | 2 / 102 |
| B200 export | `tile` | 3/3 (alpha 3, sched 3) | 3/3 (alpha 3, sched 3)
| 1 / 1 | 2 / 11 |
| B200 export | `tile_h64` | 1/2 (alpha 1, sched 2) [2] | 2/2 (alpha 2,
sched 2) | 0 / 0 | 1 / 0 |
| B200 export | `pv` | 2/2 (alpha 2, sched 2) | 2/2 (alpha 2, sched 2) |
0 / 0 | 1 / 0 |
| GB300 export | `swap` | 6/6 (alpha 6, sched 6) | 6/6 (alpha 6, sched
6) | 1 / 1 | 2 / 102 |
| GB300 export | `tile` | 3/3 (alpha 3, sched 3) | 3/3 (alpha 3, sched
3) | 1 / 1 | 2 / 11 |
| GB300 export | `tile_h64` | 1/2 (alpha 1, sched 2) [2] | 2/2 (alpha 2,
sched 2) | 0 / 0 | 1 / 0 |
| GB300 export | `pv` | 2/2 (alpha 2, sched 2) | 2/2 (alpha 2, sched 2)
| 0 / 0 | 1 / 0 |

[2] The proof accepts an instantiation when its SASS is byte-equal to
the per-knob program's or schedule-equal (the same multiset of
instructions with register numbers erased and the same distinct-register
count; the rule of the previous deliveries). The merge kernel is a
single program and is not one of these member rows. Its delivered object
was proved separately by the `ACQBULK`, launch-attribute and PTX checks
above.

## Measurement (exporter protocol: cold-L2 CUPTI, counterbalanced
interleaved groups, symmetric external CUDA graphs, 76 shapes per card)

Each column is the geometric mean over shapes of Cake source-tree kernel
time over FlashInfer-route time (source / export;
1.0 = parity), all rows and the per-table subsets C / D / M / O / X / H.

| Card | timed rows | correct | rows >= 0.97 (previous delivery in
parentheses) | source/export geomean all / C / D / M / O / X / H |
previous delivery (same geomeans) |
|---|---|---|---|---|---|
| B200 (SM100) | 76 | 76 | 73 (73) | 0.9998 / 0.9999 / 1.0025 / 1.0040 /
0.9990 / 0.9972 / 0.9961 | 0.9985 / 0.9977 / 1.0046 / 0.9981 / 1.0027 /
0.9938 / 0.9963 |
| GB300 (SM103) | 76 | 76 | 69 (68) | 1.0007 / 1.0046 / 1.0062 / 0.9812
/ 0.9992 / 0.9978 / 1.0003 | 0.9968 / 0.9987 / 1.0042 / 0.9784 / 0.9995
/ 0.9996 / 0.9940 |

The per-row source/export floor of 0.97 is informational, not a bar, as
in the previous deliveries. Rows below it are disclosed here.

- **B200 rows below the floor:** C-h32-k128-t1 0.935, C-h64-k512-t8
0.954, X-h128-k256-t72 0.962. The previous delivery listed the same
three rows.
- **GB300 rows below the floor:** C-h64-k512-t8 0.936, C-h64-k512-t32
0.952, O-h128-k512-t32 0.941, M-h64-m128-e512p64-t12 0.944,
M-h128-k128-t12 0.961, M-h128-m128-e512p64-t12 0.944, X-h128-k256-t72
0.968. The previous delivery listed 8 rows; 6 of these 7 were among
them.

Some rows have their exporter measurement marked invalid by the
directional-disagreement check (more than 0.05 between the
counterbalanced groups). Under the previous deliveries' rule they are
disclosed and carry no per-row verdict:
- B200, 3 rows: C-h64-k512-t32, D-h16-m512-e512p64-t32, X-h128-k256-t32.
- GB300, 5 rows: C-h128-k512-t128, D-h16-m128-e512p64-t32,
D-h16-m512-e512p64-t32, D-h128-m512-e512p64-t32, X-h128-k256-t32.

The exporter's per-row gate summary is informational, as in the previous
delivery. All gates passed = false: 70/76 rows on B200 and 64/76 rows on
GB300 pass the per-row floor and validity gates. Correctness and bitwise
identity are 76/76 on both cards.

## Tests

FlashInfer tests on the delivered tree, per card (JIT):
`tests/attention/test_sparse_mla_blackwell_dsv4_nvfp4.py`,
`tests/mla/test_cake_dsv4_nvfp4_route.py` and
`tests/mla/test_cake_dsv4.py`.

- **B200 (SM100): 439 passed, 0 failed, 0 errors**
- **GB300 (SM103): 439 passed, 0 failed, 0 errors**

The bar is >= 435 passed, 0 failed, 0 errors; the previous delivery also
reported 439 passed per card. The exporter's text audit against the
previous delivery reports 0 new findings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Improvements**
* Updated NVFP4 merge processing to coordinate GPU execution. The merge
inputs, outputs, and validation behavior remain unchanged.
* Updated internal kernel identifiers; these changes do not add or
remove user-facing functionality.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6003939](https://github.com/flashinfer-ai/flashinfer/commit/60039395e13e3f663a90c25f08668937a9a0368a)

- **作者**: eigen
- **时间**: 2026-10-16T22:18:54Z
- **提交信息**: fix(moe, trace): validate the pack contract in SM12xNvfp4Runner and register the new comm trace modules (#6591)

## Summary

Since #5863 and #6544 merged to `main`, the `JIT Unittest (H100)` job in
the `PR Test` workflow fails on two CPU-only test nodes. `main`'s own
run of that workflow (run 38930349451 at 19faf79b70) fails on the same
two nodes:

-
`tests/moe/test_unified_moe_pack_contract.py::test_every_pack_inputs_checks_the_contract[SM12xNvfp4Runner]`:
assertion `'self._validate_pack_contract(act)' in ''`
-
`tests/trace/test_template_registry.py::test_registration_module_inventory_is_complete`:
the scan of the source finds three modules that are not in the inventory

This PR fixes both failures.

## Root cause

- `SM12xNvfp4Runner.pack_inputs` was added in #5863 (397b9607c). It is
the only one of the 16 runners in `flashinfer/fused_moe/runners.py` that
never calls the shared `MoERunner._validate_pack_contract`. The test
requires `pack_inputs` to make that call first, either directly or
through a `self._validate_*` helper.
- #6544 (840fb6965) added `flashinfer.comm.mnnvl_cutedsl_ag`,
`flashinfer.comm.mnnvl_cutedsl_moe_finalize` and
`flashinfer.comm.tp_moe_finalize_rmsnorm` with
`@flashinfer_api(trace=...)` decorators. It did not add them to
`_TRACE_REGISTRATION_MODULES` in `tests/trace/template_registry.py`.
That file's docstring requires the inventory to match the set of modules
that use the decorator.

## Changes

2 files, +4/-4.

- `flashinfer/fused_moe/runners.py`: `SM12xNvfp4Runner.pack_inputs` now
calls `self._validate_pack_contract(act)` right after
`self._require_built()`, as its parent
`SM12xNvfp4Bf16Runner.pack_inputs` does. I removed the separate
`NotImplementedError("... supports only PackedPrecomputed routing.")`
branch. The shared check already rejects any `routing_input_mode`
outside `supported_routing_modes`, which is
`(RoutingInputMode.PackedPrecomputed,)` for this runner.
- A pack that is not PackedPrecomputed still raises
`NotImplementedError`, now with the standard message. No test checks the
removed message.
- A pack that carries `per_token_scale` is now rejected by the shared
check (`ValueError`) before it reaches the runner's own `ValueError`.
- The `hidden_states_scale` check and the rest of the method are
unchanged. Kernels and numerics are unchanged.
- `tests/trace/template_registry.py`: adds the three modules to
`_TRACE_REGISTRATION_MODULES`, in alphabetical order within the
`flashinfer.comm.*` block.

## Test plan

- [x] `pre-commit run --files` on both changed files: all hooks pass
(ruff v0.12.8 check and format, mypy, whitespace/EOF hooks).
- [x] CPU-only run (no GPU; torch 2.10.0a0 from the NGC 26.01 container)
of the affected test files on both the base tree (`main` at ed3e64de)
and the fixed tree, to check that the newly registered templates add no
new failures:
- `tests/moe/test_unified_moe_pack_contract.py` (fixed tree): 160
passed, 5 skipped; the `SM12xNvfp4Runner` node passes.
- `tests/trace/test_template_registry.py`: base 1 failed
(`test_registration_module_inventory_is_complete`), 3 passed; fixed tree
4 passed.
- `tests/trace/test_template_init.py` +
`tests/trace/test_fi_trace_template_consistency.py`: base 1453 passed,
246 skipped; fixed tree 1465 passed, 246 skipped. The 12 extra nodes are
the newly registered `flashinfer.comm.*` templates; 0 new failures.
- [ ] CI (`@flashinfer-bot run`)

## References

- #5863: Canonical-layout NVFP4 W4A4 MoE in CuTe DSL on SM12x
- #6544: Support Muse-Spark-Open with fused normalization and TP/EP MoE
optimizations
- Failing `main` run:
https://github.com/flashinfer-ai/flashinfer/actions/runs/38930349451
(commit 19faf79b70)
- Open PRs currently show these two `JIT Unittest (H100)` failures
whatever their content.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1b7a90a](https://github.com/flashinfer-ai/flashinfer/commit/1b7a90a0592a3b46c70c7acbb73b7b647927aeef)

- **作者**: Wei-Cheng (Wayne) Chiu
- **时间**: 2026-10-16T22:16:00Z
- **提交信息**: fix: give concurrent streams disjoint row_states buffers in multi-CTA top-k (#3625)

## Description

Fixes #3618.

The multi-CTA radix top-k kernels keep histograms and inter-CTA barrier
counters in `RadixRowState` scratch. The Python entry points previously
obtained that scratch from device-keyed `_get_cache_buf` entries, so
unsynchronized launches on different CUDA streams could share the same
state and corrupt results or wedge the barrier.

The original PR covered seven producers. Current main subsequently added
two supported `top_k_varlen` producers (`radix` and `radix_cutlass`), so
this rebuild covers all nine current Python call sites.

## Fix

Allocate zero-initialized row-state scratch per call with `torch.zeros`
instead of sharing a device cache entry. PyTorch's stream-ordered
caching allocator gives concurrent live launches disjoint storage,
reuses it after stream work completes, and handles CUDA graph capture
without a custom ring or lifetime registry.

The `top_k_varlen` radix backend preserves its existing SM-count-based
allocation size and `int32` view shape; the other eight paths retain
their existing 1 MiB byte-buffer contract.

## Validation

Rebuilt on `main` at `7b49d8509a4f914856ee71dff3177e7dec6760cb`.
Validated on an RTX PRO 6000 Blackwell, SM120, with Torch 2.13 and CUDA
13:

- A real public-API graph reproduction passes both serial controls on
stock main, then produces incorrect top-k outputs at the first
concurrent replay. With this change, every value and index matches
`torch.topk` across 16 concurrent replays of two independent graphs,
each containing eight calls.
- Native stream, graph, and both variable-length backend regressions: 6
passed.
- Focused public sampling/logits API and operator output tests: 1,032
passed, 126 skipped.
- Existing top-k graph/mode correctness cases on the refreshed base: 56
passed, 6 skipped.
- Ruff 0.12.8 format/check and `git diff --check`: passed.
- Independent outcome verification: confirmed, including all nine
producers and the actual graph regression.

The earlier maintainer-triggered pipeline `57443299` succeeded on the
previous head. These local correctness results apply to the rebuilt
head; no isolated timing or performance result is claimed.

## Disclosure

The correctness checks above ran on real SM120 hardware.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- Improved top-k and variable-length top-k operations during concurrent
CUDA stream execution.
- Prevented overlapping operations from sharing temporary state and
producing incorrect results.
- Preserved synchronization correctness across supported top-k,
page-table, ragged, and radix-based processing modes.
- Improved reliability when multiple sampling and probability-processing
operations run concurrently.

- **Tests**
- Added regression coverage for concurrent top-k and variable-length
top-k operations across multiple CUDA streams.
- Verified results for standard, page-table, ragged, and radix-based
processing paths.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: WEI CHENG CHIU <waynehacking8@gmail.com>

### [6c23f96](https://github.com/flashinfer-ai/flashinfer/commit/6c23f96d2fc75e09d0cdd29e9b1c2877256504db)

- **作者**: eigen
- **时间**: 2026-10-16T20:50:19Z
- **提交信息**: refactor(cake): build.json manifests, shared cake_build loader, header-free bindings; MoK sm_107a BF16/MXFP8 kernels (#6553 steps 2-4) (#6584)

Implements steps 2-4 of #6553, which make the Cake-exported packages
vendorable. Step 1 (#6571, merged) made each package directory
self-contained. This PR does four things:

- Every package now ships a `build.json` manifest.
- All seven packages share one `cake_build.py` loader.
- The bindings include no FlashInfer header.
- The MoK (Mix of Kittens) package gains sm_107a kernels: 8 BF16 kernels
are added and 8 MXFP8 kernels are re-rendered for the sm_107a
shared-memory descriptor encoding. They are compile-checked with nvcc
13.4 (`compute_107`); this PR includes no sm_107a hardware run.
These kernels are the Rubin (`sm_107`) build of the MoK forward /
recompute / backward paths requested in #6165.

As a result, a package can be built and loaded outside FlashInfer.

## What changes

- **`build.json` (schema `cake-build/1`):** one entry per (library,
architecture). Each entry lists its translation units and their sha256,
a per-architecture closure digest, the arches, `min_cuda`, the ffi entry
and the launch plan.
- **`cake_build.py`:** a single loader, byte-identical across the seven
packages. It uses a prebuilt `aot/<name>.so` when a builder has filled
one. Otherwise it falls back to FlashInfer's JIT.
- **Bindings:** they use the shipped `csrc/cake_ffi_checks.h` runtime
instead of FlashInfer headers. Every module exports
`build_cuda_version`.
- **`cake_jit.py`:** the registry literals are reduced to the host-plan
data the loader needs.

## Commit structure

| Commit | Content |
|---|---|
| Scaffold | Host-side edits to the seven packages;
`scripts/check_cake_build_manifests.py` with the in-tree manifest
checks; `aot/` ignored; tests assert the manifest instead of registry
sources; examples and tests call `cake_build.manifest()` |
| Cake exports | Six packages: `rmsnorm_train` backend,
`cake_dsa_train`, `cake_dsa_indexer`, `cake_lm_head_loss`,
`dense_projection_gemm`, `cake_mok_bf16`. Its trailers carry
`Cake-Revision` (both generator revisions), `FI-Pin`, `Packages` and one
`Identity-<package>` line per package with the two identity tree ids |
| MoE | `experimental/cake_moe_grouped_gemm`, produced by the Cake
kitchen writer |

The generators ran against the scaffold pin
`1dd72567fe2cca83fcd92b5a45c3c510d1c3b276`.

## Generator revisions and reproducibility

Each package was exported twice, independently, into two clean worktrees
at the scaffold pin. Both runs used a B200 node with the Cake devel
image and CUDA 13.4.92. For every package, `git add -A && git
write-tree` gave the same tree id for both runs. The committed package
content matches run 1's tree; this was checked per package when the head
was assembled.

| Package | Generator | Identity tree (both runs) |
|---|---|---|
| `rmsnorm_train` | Cake `814f24e44065cce2ae25b694a7a9e6c291f58c7c` |
`1c9dea5e2ff8e885fac57844fede3b60c7695b1f` |
| `cake_dsa_train` | Cake `edd053a14aa1c0b391c85588d7bff0fd2cbaade4` |
`d2f18d38501ccba6ecf692b21cbc02599812e9e2` |
| `cake_dsa_indexer` | Cake `edd053a14aa1c0b391c85588d7bff0fd2cbaade4` |
`6fe1afcd27df8144806dbe0335c407b7a1bd328c` |
| `cake_lm_head_loss` | Cake `814f24e44065cce2ae25b694a7a9e6c291f58c7c`
| `4c6e80f3a382efd833f727110228061e8a7dd399` |
| `dense_projection_gemm` | Cake
`edd053a14aa1c0b391c85588d7bff0fd2cbaade4` |
`e3b2e8048db3984adb00f92cca9822c5c961b88d` |
| `cake_mok_bf16` | Cake `edd053a14aa1c0b391c85588d7bff0fd2cbaade4` |
`33ec253532659612cee024658eb4ff5519b27670` (0-GPU render + assemble) |
| `cake_moe_grouped_gemm` | Cake kitchen writer at kitchen commit
`903b09de00f9948ddc4cf027ba508088166c7392` (the merged tooling), flour
`236ee166` | `25fc23baeb60ad8fa95b1d1628627e52fff0cde2` (two writer
runs) |

Cake `814f24e` differs from `edd053a` in three ways, none of which
touches the other four exporters:

- It formats the lm_head registry block with FlashInfer's pinned ruff.
- It names the public `cake_build.manifest()` accessor in the rmsnorm
test template.
- It updates the MoE export documentation (no code).

The MoE package records its writer commit and flour revision in the
generator block of its `build.json`.

As part of the exporter protocol, these packages also had registered
sm_100a rows measured against the source kernels. The checks covered
correctness, allocation, activity parity, directional agreement and
timing gates. All passed:

- rmsnorm fwd/bwd `h6144_t4096`
- dsa_train `doc_4096` and `masked_4k`
- lm_head `t4096_c4096_ce`
- dense_projection_gemm `indexer_hw_fwd_bf16_t16172`
- dsa_indexer `exact_distinct`

## Device sources relative to the scaffold pin

| Package | Kernel `.cu` files | Device headers re-rendered |
|---|---|---|
| `rmsnorm_train` | 21 renamed only | 2 (shared) |
| `cake_dsa_train` | 8 renamed | 16 |
| `cake_dsa_indexer` | 12 renamed, 31 re-rendered | 1 |
| `cake_lm_head_loss` | 27 renamed | 0 |
| `dense_projection_gemm` | 13 renamed | 0 |

- **`cake_mok_bf16`:**
  - 8 BF16 kernels moved into the per-architecture `csrc/sm_100a/`.
  - 8 sm_107a BF16 kernels added.
- 8 sm_107a MXFP8 kernels re-rendered for the sm_107a shared-memory
descriptor encoding.
- **Bindings:** re-rendered in every package (`cake_ffi_checks` runtime,
`build_cuda_version`).
- **`cake_moe_grouped_gemm`:**
  - The 4 wgrad kernel sources are byte-identical to #6572.
- fwd and dgrad each gain one `tcgen05.fence::before_thread_sync` line.
- tail_reduce sizes its accumulator by the fixed chunk constant (`float
acc[16]`).
- **MoE SASS comparison:** all 26 `build.json` entries of the old
(carried) tree and the new tree were compiled with the manifest's own
flags for sm_100a/sm_103a/sm_107a. Their SASS was compared per kernel
after address normalisation:
  - 20 of 26 are identical: all wgrad and tail-reduce entries.
- fwd and dgrad differ only in NOP alignment padding. dgrad gains 8 NOPs
on sm_100a/sm_103a; fwd and sm_107a dgrad have identical instruction
multisets.
  - No functional instructions changed.

## Validation

All runs used a B200 with CUDA 13.4.92, one GPU per suite, on the
committed package worktrees.

| Check | Result |
|---|---|
| `tests/norm/test_cake_rmsnorm_train.py` | 134 passed, 28 skipped. At
the earlier generator revision: 133 passed, 28 skipped, 1 failed on the
stale `_manifest()` accessor; the rmsnorm re-export fixes this |
| `tests/experimental/test_cake_dsa_train.py` | 103 passed |
| `tests/experimental/test_cake_dsa_indexer.py` | 164 passed |
| `tests/experimental/test_cake_lm_head_loss.py` | 176 passed, 1 skipped
(same at the earlier generator revision) |
| `tests/experimental/test_cake_dense_projection_gemm.py` | 161 passed |
| `test_mok_bf16.py` / `test_mok_bf16_tolerance.py` /
`test_mok_mxfp8.py` | 44 / 10 / 25 passed (distributed mok suite not
run) |
| `tests/experimental/test_cake_moe_grouped_gemm.py` | 40 passed |
| `scripts/check_cake_build_manifests.py --in-tree` (stacked tree) | 7
packages, 0 findings |
| ruff 0.12.8 check + format, every `.py` changed since the scaffold pin
(14 files) | clean |

**MoE vendoring smoke test:** two entries were built with plain nvcc
using only `build.json`. The command combined `common.nvcc_flags`, the
satisfied `nvcc_flags_if`, the entry `nvcc_flags` and gencode, `-I csrc`
plus the tvm_ffi include dirs, and `common.link_flags`. Then `python
-I`, with flashinfer blocked, loaded both through
`cake_build.load_library()` and read `build_cuda_version() == 13040`.

## Limitations

- **Untested architectures:** sm_103a and sm_107a kernels are only
compile-checked (nvcc 13.4, compute_103 / compute_107). This PR includes
no GB300 or Vera Rubin run.
- **MoE sm_107a:** these entries ship the sm_103a kernel text.
Correctness is argued from shared-memory sizes; the sm_107a-specific
mask fold is follow-up work.
- **No license block:** `csrc/cake_ffi_checks.h` has none. Its bytes are
identical in all seven packages.
- **MoE benchmark:** the old-vs-new run
(`benchmarks/bench_cake_moe_grouped_gemm.py`, 4 alternating rounds on an
idle B200) resolves no better than about ±10 % per row. Rows with
byte-identical kernels spread from 0.91 to 1.12. It showed no detectable
difference; the SASS comparison above is the equivalence evidence.
- **MoE generator block refreshed:** the kitchen writer tooling has
landed as a squashed commit, so the MoE `build.json` generator block now
names that commit. Only that metadata changed; writer runs at different
kitchen commits produce the same kernel, binding and loader bytes.

## For reviewers

- Manifest check: `python scripts/check_cake_build_manifests.py
--in-tree`
- One package suite, for example: `pytest
tests/experimental/test_cake_dsa_train.py`
- Please request bot runs for the seven package suites in the Validation
table and for the in-tree manifest check.
- The Cake export commit's trailers carry the two generator revisions
and the per-package identity trees. The MoE commit message and the MoE
`build.json` generator block record the writer commit and flour
revision.
- `aot/` is ignored. With no prebuilt `.so` present, `cake_build.py`
falls back to FlashInfer's JIT, so no extra build step is needed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ea04837](https://github.com/flashinfer-ai/flashinfer/commit/ea04837487e9df91b953b15768838eb1ea8142d2)

- **作者**: eigen
- **时间**: 2026-10-16T20:37:56Z
- **提交信息**: feat(cake_msa_icp_indexer): add world-2 exchange-merge geometries (8,8), (4,8), (2,8), (2,6), (1,6) for sm_100a and sm_103a (#6580)

# feat(cake_msa_icp_indexer): add world-2 exchange-merge geometries
(8,8), (4,8), (2,8), (2,6), (1,6) for sm_100a and sm_103a

Tracker: #4254 (Cake generated-program deliveries). Target:
`origin/main` @ `38e6b8944fe8b6497d793ef21fbaadd797ea39d8` (this PR's
base). The Cake exporter generated the programs at revision
`657092645f7245e100e235f0ac89d258fac8aaf3`. They were measured against
FlashInfer `ac3476396ce741d300ac136df056335c6c6a71a1`, which contains
the sibling delivery #6450. Nine upstream commits sit between that
revision and this base (the Cake package-layout step #6571, `gdn`,
`cake_moe_grouped_gemm`, `norm`, `cake_gdn`, Muse-Spark MoE and CI
changes). None of them touch the ICP paths, so the base version of every
file this PR touches is identical in the measured tree and the published
tree; the delivery itself differs from the measured delivery by one
comment line (see "Tests run on the delivered trees"). This PR changes
23 files and deletes nothing.

## What this PR delivers

The ICP indexer chain picks its exchange-merge geometry (warps `w`,
entries per lane `epl`) from three inputs: the device SM count, the
decode batch and the block-table width. The scorer split is `split =
(SMs * 2) // batch` (two scorer CTAs per SM at page size 128). For a TP2
(world-2) chain with a 2048-column block table (262K-token KV capacity),
it picks these geometries:

- (8,8) for batches 9–11 at 148 SMs / 10–12 at 152 SMs
- (4,8) for batches 18–22 / 18–23
- (2,8) for batches 33–42 / 34–43
- (2,6) for batches 43–59 / 44–60
- (1,6) for batches 75–98 / 77–101

148 SMs (B200) and 152 SMs (GB300) reach the same five geometries; only
the batch bands differ by one or two batches, as listed. #6450
registered only the world-2 merges (1,2), (1,4), (1,8), (4,6), (8,6) and
(8,10). For the batches listed above, `prepare_msa_icp_indexer` raised
`NotImplementedError("... not registered in this checkout")`, so a TP2
vLLM server had to restrict its FULL CUDA-graph capture ladder. This PR
registers the five missing geometries for `sm_100a` and `sm_103a`.

1. **Five world-2 exchange-merge programs**:
- 10 new generated sources, a kernel `.cu` and a binding `.cu` for each
of `cake_msa_icp_indexer_{133176f530b7352070c3, 177f6799f01a652ddd21,
17f1f4efee096a75db68, 9c8c1dc86f1b2c21e293, f76a34922ef374f481e6}`.
- Five new registry records in
`flashinfer/experimental/cake_msa_icp_indexer/cake_jit.py` (+80 lines).
Each record has world 2, one `(warps, entries_per_thread)` pair from
{(8,8), (4,8), (2,8), (2,6), (1,6)}, `late_wait`, `small_fast` and
`reg_tail` set to `True`, and arches `sm_100a` and `sm_103a`.
2. **Shared header and existing kernels (kernel code unchanged)**:
- In `csrc/cake_msa_icp_indexer/cake_msa_icp_indexer_device_common.cuh`,
only a comment changes: the helper-library union grows from 42 to 52
modules.
- Because the shared header's helper union grew, each of nine previously
shipped `*_kernel.cu` files gains a 9-line fallback helper,
`make_warp_uniform`, local to its translation unit. The kernel code in
these files is unchanged.
- The 21 programs registered by #6450 keep their names and registry
records.
3. **Tests**:
- `tests/test_helpers/cake_msa_icp_inputs.py` (+43 lines) adds five
emulated cases, `tp2_q4_b{10,20,40,52,88}_cols2048` (world 2, query_len
4, context 1500, 2048 block-table columns).
- `tests/experimental/test_cake_msa_icp_indexer.py` (+6/−1 lines) adds
the NCCL multi-GPU case `tp2_q4_b52_cols2048` to `MULTI_GPU_CASES`.

## Measurement receipts

The protocol is the same as in #6450:

- Frozen protocol with paired source/export arms. The source arm is the
producer's own chain and the export arm is the FlashInfer-integrated
programs.
- CUPTI timing, cold L2, same-arm preconditioning and fixed sample
counts.
- Gates for each shape: bit-exact outputs, source/export ≥ 0.97,
directional disagreement ≤ 0.12, endpoint drift ≤ 0.08.

The denominator is 66 chain rows × 2 parts = 132 shapes. The 66 rows are
the 61 rows of #6450 plus five new rows,
`chain_tp2_p128_q4_b{10,20,40,52,88}_ctx150k_cap256k_nvfp4`: TP2, page
128, query_len 4, 150K-token contexts, 262K-token capacity (2048
columns).

| part | shapes | result |
|---|---|---|
| ICP indexer sm_100a (B200, 148 SMs) | 66 | 66 / 66 PASS after the one
pre-registered retry round (round 1: 62 / 66, four source/export misses
with bit-exact outputs and valid measurements:
`chain_tp2_p128_q4_b32_ctx100k_cap1m_nvfp4` 0.9598,
`chain_tp4_p128_q4_b8_ctx8k_cap1m_nvfp4` 0.9522,
`correct_tp4_p128_q2_b8_ctx1500_cap12blk_nvfp4` 0.9144,
`correct_tp4_p128_q4_b8_ctx1500_fp8pitch` 0.9695; retry on the same
node: all four pass at 1.0029 / 1.0121 / 0.9870 / 1.0162); final 66
rows: source/export geomean 1.0045, min 0.9741, max 1.0743; directional
disagreement ≤ 0.0433; endpoint drift ≤ 0.0123. New rows: b10 (8,8)
1.0060, b20 (4,8) 1.0056, b40 (2,8) 1.0058, b52 (2,6) 1.0032, b88 (1,6)
1.0057 |
| ICP indexer sm_103a (GB300, 152 SMs) | 66 | 66 / 66 PASS on 4 × GB300
in one round (no retry); source/export geomean 1.0000, min 0.9808, max
1.0292; directional disagreement max 0.0806; endpoint drift max 0.0455.
New rows: b10 (8,8) 0.9963 (export 34.59 µs), b20 (4,8) 1.0000 (47.81
µs), b40 (2,8) 1.0021 (77.50 µs), b52 (2,6) 1.0034 (95.30 µs), b88 (1,6)
1.0057 (147.07 µs) |
| ICP merged complete run (both parts) | 132 | 132 / 132 PASS after the
one pre-registered retry round. The run took the 66 sm_100a rows from
the two closed B200 snapshots (no sm_100a row re-measured) and
re-measured the 66 sm_103a rows (a second GB300 round: geomean 0.9994,
min 0.9770, max 1.0428). Round 1: 131 / 132; the one non-passing row
`correct_tp4_p128_q3_b8_ctx1500_cap12blk_nvfp4` failed the CUPTI
activity-count parity check of the measurement protocol (a
measurement-validity failure: that attempt recorded no timing and no
correctness verdict); the same row passed the standalone GB300 leg
above. Retry round on the same node with the closed round-1 snapshots as
priors: that row 0.9986 (directional 0.0177, drift 0.0096), 131 rows
retained, final 132 / 132 |

<details>
<summary>GB300 per-shape results (sm_103a, 152 SMs, 66 rows)</summary>

GB300 sm_103a @ 152 SMs: rows=66 passed=66; source/export geomean 1.0000
min 0.9808 max 1.0292; directional max 0.0806; drift max 0.0455

| shape (sm_103a, 152 SMs) | source/export | directional | drift |
export us | result |
|---|---|---|---|---|---|
| chain_tp2_p128_q1_b64_ctx150k_cap1m_nvfp4 | 1.0101 | 0.0015 | 0.0025 |
111.07 | PASS |
| chain_tp2_p128_q1_b64_ctx8k_cap1m_nvfp4 | 1.0047 | 0.0001 | 0.0078 |
20.42 | PASS |
| chain_tp2_p128_q1_b8_ctx150k_cap1m_nvfp4 | 0.9978 | 0.0042 | 0.0076 |
29.54 | PASS |
| chain_tp2_p128_q1_b8_ctx8k_cap1m_nvfp4 | 0.9922 | 0.0323 | 0.0219 |
16.42 | PASS |
| chain_tp2_p128_q4_b10_ctx150k_cap256k_nvfp4 | 0.9963 | 0.0055 | 0.0093
| 34.59 | PASS |
| chain_tp2_p128_q4_b16_ctx100k_cap1m_nvfp4 | 1.0031 | 0.0046 | 0.0071 |
35.95 | PASS |
| chain_tp2_p128_q4_b16_ctx150k_cap1m_nvfp4 | 1.0037 | 0.0000 | 0.0124 |
42.98 | PASS |
| chain_tp2_p128_q4_b16_ctx150k_cap1m_nvfp4_shared_prefix | 1.0016 |
0.0018 | 0.0064 | 39.90 | PASS |
| chain_tp2_p128_q4_b16_ctx200k_cap1m_nvfp4 | 1.0000 | 0.0019 | 0.0040 |
51.33 | PASS |
| chain_tp2_p128_q4_b16_ctx8k_cap1m_nvfp4 | 0.9874 | 0.0564 | 0.0296 |
17.73 | PASS |
| chain_tp2_p128_q4_b16_half8k_half200k_cap1m_nvfp4 | 0.9967 | 0.0005 |
0.0105 | 39.38 | PASS |
| chain_tp2_p128_q4_b16_random8k_200k_cap1m_nvfp4 | 0.9992 | 0.0024 |
0.0097 | 42.59 | PASS |
| chain_tp2_p128_q4_b1_ctx100k_cap1m_nvfp4 | 0.9916 | 0.0038 | 0.0305 |
19.01 | PASS |
| chain_tp2_p128_q4_b1_ctx150k_cap1m_nvfp4 | 1.0017 | 0.0385 | 0.0259 |
19.01 | PASS |
| chain_tp2_p128_q4_b1_ctx200k_cap1m_nvfp4 | 0.9902 | 0.0239 | 0.0117 |
19.52 | PASS |
| chain_tp2_p128_q4_b1_ctx8k_cap1m_nvfp4 | 1.0292 | 0.0334 | 0.0056 |
16.45 | PASS |
| chain_tp2_p128_q4_b20_ctx150k_cap256k_nvfp4 | 1.0000 | 0.0008 | 0.0060
| 47.81 | PASS |
| chain_tp2_p128_q4_b32_ctx100k_cap1m_nvfp4 | 1.0057 | 0.0009 | 0.0045 |
50.21 | PASS |
| chain_tp2_p128_q4_b32_ctx150k_cap1m_nvfp4 | 1.0019 | 0.0024 | 0.0052 |
66.98 | PASS |
| chain_tp2_p128_q4_b32_ctx200k_cap1m_nvfp4 | 1.0104 | 0.0021 | 0.0040 |
83.10 | PASS |
| chain_tp2_p128_q4_b32_ctx8k_cap1m_nvfp4 | 1.0000 | 0.0066 | 0.0077 |
20.61 | PASS |
| chain_tp2_p128_q4_b40_ctx150k_cap256k_nvfp4 | 1.0021 | 0.0010 | 0.0029
| 77.50 | PASS |
| chain_tp2_p128_q4_b52_ctx150k_cap256k_nvfp4 | 1.0034 | 0.0005 | 0.0047
| 95.30 | PASS |
| chain_tp2_p128_q4_b64_ctx100k_cap1m_nvfp4 | 1.0075 | 0.0020 | 0.0065 |
80.77 | PASS |
| chain_tp2_p128_q4_b64_ctx150k_cap1m_nvfp4 | 1.0111 | 0.0002 | 0.0025 |
112.03 | PASS |
| chain_tp2_p128_q4_b64_ctx150k_cap256k_nvfp4 | 1.0071 | 0.0020 | 0.0067
| 112.29 | PASS |
| chain_tp2_p128_q4_b64_ctx200k_cap1m_nvfp4 | 1.0083 | 0.0011 | 0.0016 |
142.82 | PASS |
| chain_tp2_p128_q4_b64_ctx8k_cap1m_nvfp4 | 0.9985 | 0.0072 | 0.0211 |
20.99 | PASS |
| chain_tp2_p128_q4_b88_ctx150k_cap256k_nvfp4 | 1.0057 | 0.0017 | 0.0021
| 147.07 | PASS |
| chain_tp2_p128_q4_b8_ctx100k_cap1m_nvfp4 | 0.9928 | 0.0024 | 0.0143 |
26.82 | PASS |
| chain_tp2_p128_q4_b8_ctx150k_cap1m_fp8pitch | 1.0022 | 0.0020 | 0.0128
| 29.76 | PASS |
| chain_tp2_p128_q4_b8_ctx150k_cap1m_nvfp4 | 0.9989 | 0.0026 | 0.0138 |
29.98 | PASS |
| chain_tp2_p128_q4_b8_ctx150k_cap256k_nvfp4 | 0.9968 | 0.0032 | 0.0038
| 29.82 | PASS |
| chain_tp2_p128_q4_b8_ctx200k_cap1m_nvfp4 | 0.9982 | 0.0028 | 0.0092 |
35.14 | PASS |
| chain_tp2_p128_q4_b8_ctx8k_cap1m_nvfp4 | 0.9964 | 0.0441 | 0.0125 |
18.02 | PASS |
| chain_tp2_p256_q4_b64_ctx150k_cap1m_nvfp4 | 1.0015 | 0.0013 | 0.0035 |
110.21 | PASS |
| chain_tp2_p256_q4_b8_ctx150k_cap1m_nvfp4 | 1.0075 | 0.0086 | 0.0239 |
29.86 | PASS |
| chain_tp4_p128_q4_b64_ctx150k_cap1m_nvfp4 | 1.0049 | 0.0022 | 0.0126 |
79.10 | PASS |
| chain_tp4_p128_q4_b64_ctx8k_cap1m_nvfp4 | 1.0155 | 0.0142 | 0.0101 |
31.04 | PASS |
| chain_tp4_p128_q4_b8_ctx150k_cap1m_nvfp4 | 0.9942 | 0.0059 | 0.0123 |
33.31 | PASS |
| chain_tp4_p128_q4_b8_ctx8k_cap1m_nvfp4 | 1.0091 | 0.0047 | 0.0104 |
24.64 | PASS |
| correct_long_tp2_p128_q4_b2_ctx150k_cap1m_nvfp4 | 1.0000 | 0.0045 |
0.0127 | 21.18 | PASS |
| correct_long_tp4_p128_q4_b1_ctx200k_cap1m_nvfp4 | 0.9882 | 0.0049 |
0.0278 | 27.10 | PASS |
| correct_tp2_p128_q1_b8_ctx1500_cap12blk_nvfp4 | 1.0000 | 0.0557 |
0.0175 | 16.58 | PASS |
| correct_tp2_p128_q2_b8_ctx1500_cap12blk_nvfp4 | 0.9922 | 0.0743 |
0.0076 | 16.48 | PASS |
| correct_tp2_p128_q3_b48_split_128_row_window | 1.0056 | 0.0365 |
0.0154 | 17.28 | PASS |
| correct_tp2_p128_q3_b8_ctx1500_cap12blk_nvfp4 | 0.9962 | 0.0524 |
0.0380 | 16.96 | PASS |
| correct_tp2_p128_q4_b64_graph_shrink_reactivate | 0.9808 | 0.0178 |
0.0156 | 18.34 | PASS |
| correct_tp2_p128_q4_b8_ctx1500_cap12blk_nvfp4 | 1.0000 | 0.0503 |
0.0271 | 16.03 | PASS |
| correct_tp2_p128_q4_b8_ctx1500_fp8pitch | 0.9922 | 0.0680 | 0.0145 |
16.45 | PASS |
| correct_tp2_p128_q4_b8_padded_active_rows | 0.9941 | 0.0711 | 0.0173 |
16.38 | PASS |
| correct_tp2_p128_q4_b8_page_table_shared_prefix | 0.9981 | 0.0677 |
0.0304 | 16.48 | PASS |
| correct_tp2_p128_q4_b8_page_table_shuffled | 0.9961 | 0.0626 | 0.0290
| 16.51 | PASS |
| correct_tp2_p128_q4_b8_position_boundary | 0.9882 | 0.0546 | 0.0212 |
16.32 | PASS |
| correct_tp2_p128_q4_b8_position_end | 1.0039 | 0.0507 | 0.0216 | 16.42
| PASS |
| correct_tp2_p128_q4_b8_zero_length_requests | 0.9888 | 0.0685 | 0.0307
| 17.22 | PASS |
| correct_tp2_p128_q4_graph_multi_size_8_16_32_64 | 0.9809 | 0.0290 |
0.0172 | 18.43 | PASS |
| correct_tp2_p128_q8_b8_ctx1500_cap12blk_nvfp4 | 0.9960 | 0.0806 |
0.0178 | 16.03 | PASS |
| correct_tp2_p256_q1_b8_ctx3000_cap24blk_nvfp4 | 1.0117 | 0.0533 |
0.0455 | 16.35 | PASS |
| correct_tp2_p256_q4_b8_ctx3000_cap24blk_nvfp4 | 1.0150 | 0.0796 |
0.0312 | 17.12 | PASS |
| correct_tp4_p128_q1_b8_ctx1500_cap12blk_nvfp4 | 1.0000 | 0.0597 |
0.0167 | 22.21 | PASS |
| correct_tp4_p128_q2_b8_ctx1500_cap12blk_nvfp4 | 1.0042 | 0.0405 |
0.0063 | 22.69 | PASS |
| correct_tp4_p128_q3_b8_ctx1500_cap12blk_nvfp4 | 1.0043 | 0.0135 |
0.0100 | 22.30 | PASS |
| correct_tp4_p128_q4_b8_ctx1500_cap12blk_nvfp4 | 0.9828 | 0.0175 |
0.0217 | 24.13 | PASS |
| correct_tp4_p128_q4_b8_ctx1500_fp8pitch | 1.0088 | 0.0179 | 0.0220 |
21.92 | PASS |
| correct_tp4_p128_q8_b8_ctx1500_cap12blk_nvfp4 | 0.9919 | 0.0430 |
0.0148 | 23.68 | PASS |

</details>

<details>
<summary>B200 (sm_100a, 148 SMs) per-shape receipts, final rows after
the retry round (66)</summary>

| shape (sm_100a, 148 SMs) | source/export | directional | drift |
export us | result |
|---|---|---|---|---|---|
| chain_tp2_p128_q1_b64_ctx150k_cap1m_nvfp4 | 0.9741 | 0.0046 | 0.0015 |
120.00 | PASS |
| chain_tp2_p128_q1_b64_ctx8k_cap1m_nvfp4 | 0.9890 | 0.0064 | 0.0055 |
23.36 | PASS |
| chain_tp2_p128_q1_b8_ctx150k_cap1m_nvfp4 | 1.0069 | 0.0020 | 0.0029 |
32.48 | PASS |
| chain_tp2_p128_q1_b8_ctx8k_cap1m_nvfp4 | 1.0136 | 0.0428 | 0.0077 |
16.45 | PASS |
| chain_tp2_p128_q4_b10_ctx150k_cap256k_nvfp4 | 1.0060 | 0.0051 | 0.0051
| 37.28 | PASS |
| chain_tp2_p128_q4_b16_ctx100k_cap1m_nvfp4 | 1.0058 | 0.0039 | 0.0034 |
38.46 | PASS |
| chain_tp2_p128_q4_b16_ctx150k_cap1m_nvfp4 | 1.0027 | 0.0013 | 0.0024 |
47.42 | PASS |
| chain_tp2_p128_q4_b16_ctx150k_cap1m_nvfp4_shared_prefix | 1.0140 |
0.0129 | 0.0018 | 43.58 | PASS |
| chain_tp2_p128_q4_b16_ctx200k_cap1m_nvfp4 | 0.9953 | 0.0011 | 0.0012 |
54.59 | PASS |
| chain_tp2_p128_q4_b16_ctx8k_cap1m_nvfp4 | 1.0087 | 0.0185 | 0.0069 |
18.40 | PASS |
| chain_tp2_p128_q4_b16_half8k_half200k_cap1m_nvfp4 | 1.0029 | 0.0037 |
0.0022 | 43.10 | PASS |
| chain_tp2_p128_q4_b16_random8k_200k_cap1m_nvfp4 | 0.9911 | 0.0023 |
0.0045 | 46.66 | PASS |
| chain_tp2_p128_q4_b1_ctx100k_cap1m_nvfp4 | 0.9899 | 0.0080 | 0.0034 |
18.94 | PASS |
| chain_tp2_p128_q4_b1_ctx150k_cap1m_nvfp4 | 1.0256 | 0.0104 | 0.0049 |
19.36 | PASS |
| chain_tp2_p128_q4_b1_ctx200k_cap1m_nvfp4 | 0.9891 | 0.0415 | 0.0094 |
20.54 | PASS |
| chain_tp2_p128_q4_b1_ctx8k_cap1m_nvfp4 | 1.0067 | 0.0068 | 0.0022 |
14.43 | PASS |
| chain_tp2_p128_q4_b20_ctx150k_cap256k_nvfp4 | 1.0056 | 0.0018 | 0.0025
| 51.23 | PASS |
| chain_tp2_p128_q4_b32_ctx100k_cap1m_nvfp4 | 1.0029 | 0.0013 | 0.0026 |
54.72 | PASS |
| chain_tp2_p128_q4_b32_ctx150k_cap1m_nvfp4 | 1.0018 | 0.0014 | 0.0009 |
70.91 | PASS |
| chain_tp2_p128_q4_b32_ctx200k_cap1m_nvfp4 | 1.0055 | 0.0026 | 0.0018 |
88.03 | PASS |
| chain_tp2_p128_q4_b32_ctx8k_cap1m_nvfp4 | 1.0255 | 0.0197 | 0.0098 |
22.56 | PASS |
| chain_tp2_p128_q4_b40_ctx150k_cap256k_nvfp4 | 1.0058 | 0.0012 | 0.0019
| 82.56 | PASS |
| chain_tp2_p128_q4_b52_ctx150k_cap256k_nvfp4 | 1.0032 | 0.0006 | 0.0028
| 101.73 | PASS |
| chain_tp2_p128_q4_b64_ctx100k_cap1m_nvfp4 | 0.9963 | 0.0000 | 0.0013 |
87.17 | PASS |
| chain_tp2_p128_q4_b64_ctx150k_cap1m_nvfp4 | 0.9981 | 0.0008 | 0.0008 |
119.71 | PASS |
| chain_tp2_p128_q4_b64_ctx150k_cap256k_nvfp4 | 0.9933 | 0.0032 | 0.0012
| 119.49 | PASS |
| chain_tp2_p128_q4_b64_ctx200k_cap1m_nvfp4 | 1.0017 | 0.0002 | 0.0006 |
151.17 | PASS |
| chain_tp2_p128_q4_b64_ctx8k_cap1m_nvfp4 | 1.0176 | 0.0073 | 0.0068 |
23.65 | PASS |
| chain_tp2_p128_q4_b88_ctx150k_cap256k_nvfp4 | 1.0057 | 0.0012 | 0.0009
| 156.03 | PASS |
| chain_tp2_p128_q4_b8_ctx100k_cap1m_nvfp4 | 0.9956 | 0.0045 | 0.0044 |
28.99 | PASS |
| chain_tp2_p128_q4_b8_ctx150k_cap1m_fp8pitch | 1.0066 | 0.0039 | 0.0057
| 33.82 | PASS |
| chain_tp2_p128_q4_b8_ctx150k_cap1m_nvfp4 | 1.0743 | 0.0148 | 0.0037 |
32.29 | PASS |
| chain_tp2_p128_q4_b8_ctx150k_cap256k_nvfp4 | 1.0000 | 0.0019 | 0.0058
| 33.25 | PASS |
| chain_tp2_p128_q4_b8_ctx200k_cap1m_nvfp4 | 1.0034 | 0.0000 | 0.0034 |
37.38 | PASS |
| chain_tp2_p128_q4_b8_ctx8k_cap1m_nvfp4 | 0.9884 | 0.0039 | 0.0039 |
16.57 | PASS |
| chain_tp2_p256_q4_b64_ctx150k_cap1m_nvfp4 | 0.9967 | 0.0017 | 0.0016 |
116.99 | PASS |
| chain_tp2_p256_q4_b8_ctx150k_cap1m_nvfp4 | 1.0069 | 0.0030 | 0.0039 |
32.70 | PASS |
| chain_tp4_p128_q4_b64_ctx150k_cap1m_nvfp4 | 0.9992 | 0.0028 | 0.0034 |
80.93 | PASS |
| chain_tp4_p128_q4_b64_ctx8k_cap1m_nvfp4 | 1.0032 | 0.0001 | 0.0053 |
30.08 | PASS |
| chain_tp4_p128_q4_b8_ctx150k_cap1m_nvfp4 | 0.9949 | 0.0005 | 0.0051 |
31.33 | PASS |
| chain_tp4_p128_q4_b8_ctx8k_cap1m_nvfp4 | 1.0121 | 0.0101 | 0.0094 |
23.74 | PASS |
| correct_long_tp2_p128_q4_b2_ctx150k_cap1m_nvfp4 | 1.0029 | 0.0018 |
0.0036 | 22.46 | PASS |
| correct_long_tp4_p128_q4_b1_ctx200k_cap1m_nvfp4 | 1.0000 | 0.0166 |
0.0054 | 23.65 | PASS |
| correct_tp2_p128_q1_b8_ctx1500_cap12blk_nvfp4 | 1.0000 | 0.0072 |
0.0071 | 13.38 | PASS |
| correct_tp2_p128_q2_b8_ctx1500_cap12blk_nvfp4 | 0.9862 | 0.0088 |
0.0046 | 13.92 | PASS |
| correct_tp2_p128_q3_b48_split_128_row_window | 1.0743 | 0.0253 |
0.0035 | 18.53 | PASS |
| correct_tp2_p128_q3_b8_ctx1500_cap12blk_nvfp4 | 1.0023 | 0.0002 |
0.0047 | 13.70 | PASS |
| correct_tp2_p128_q4_b64_graph_shrink_reactivate | 0.9752 | 0.0276 |
0.0047 | 20.64 | PASS |
| correct_tp2_p128_q4_b8_ctx1500_cap12blk_nvfp4 | 0.9885 | 0.0099 |
0.0069 | 13.86 | PASS |
| correct_tp2_p128_q4_b8_ctx1500_fp8pitch | 1.0000 | 0.0118 | 0.0071 |
13.57 | PASS |
| correct_tp2_p128_q4_b8_padded_active_rows | 0.9787 | 0.0107 | 0.0106 |
14.94 | PASS |
| correct_tp2_p128_q4_b8_page_table_shared_prefix | 0.9908 | 0.0052 |
0.0048 | 13.76 | PASS |
| correct_tp2_p128_q4_b8_page_table_shuffled | 1.0024 | 0.0003 | 0.0024
| 13.54 | PASS |
| correct_tp2_p128_q4_b8_position_boundary | 1.0243 | 0.0096 | 0.0024 |
13.15 | PASS |
| correct_tp2_p128_q4_b8_position_end | 0.9977 | 0.0068 | 0.0001 | 13.57
| PASS |
| correct_tp2_p128_q4_b8_zero_length_requests | 1.0001 | 0.0083 | 0.0064
| 15.20 | PASS |
| correct_tp2_p128_q4_graph_multi_size_8_16_32_64 | 1.0570 | 0.0103 |
0.0065 | 20.80 | PASS |
| correct_tp2_p128_q8_b8_ctx1500_cap12blk_nvfp4 | 0.9791 | 0.0031 |
0.0023 | 13.79 | PASS |
| correct_tp2_p256_q1_b8_ctx3000_cap24blk_nvfp4 | 0.9933 | 0.0021 |
0.0067 | 14.27 | PASS |
| correct_tp2_p256_q4_b8_ctx3000_cap24blk_nvfp4 | 1.0201 | 0.0070 |
0.0086 | 14.34 | PASS |
| correct_tp4_p128_q1_b8_ctx1500_cap12blk_nvfp4 | 1.0157 | 0.0433 |
0.0103 | 18.34 | PASS |
| correct_tp4_p128_q2_b8_ctx1500_cap12blk_nvfp4 | 0.9870 | 0.0098 |
0.0096 | 19.81 | PASS |
| correct_tp4_p128_q3_b8_ctx1500_cap12blk_nvfp4 | 1.0432 | 0.0133 |
0.0123 | 17.38 | PASS |
| correct_tp4_p128_q4_b8_ctx1500_cap12blk_nvfp4 | 1.0175 | 0.0172 |
0.0096 | 20.06 | PASS |
| correct_tp4_p128_q4_b8_ctx1500_fp8pitch | 1.0162 | 0.0303 | 0.0064 |
19.68 | PASS |
| correct_tp4_p128_q8_b8_ctx1500_cap12blk_nvfp4 | 0.9870 | 0.0131 |
0.0073 | 22.14 | PASS |

</details>

## Tests run on the delivered trees
- GB300 (4 × GB300, applied export worktree):
`tests/experimental/test_cake_msa_icp_indexer.py` → 25 passed (19
existing, 5 new emulated cases and 1 new NCCL case; a first run had one
failure of an existing NCCL case whose spawned workers lost their named
semaphores on the node's shared /dev/shm, and the rerun ran alone with a
private /dev/shm).
- B200 (4 × B200, applied export worktree):
`tests/experimental/test_cake_msa_icp_indexer.py` → 25 passed (19
existing, 5 new emulated cases and 1 new NCCL case).
- The published tree equals the applied export tree except for one
comment line in `tests/test_helpers/cake_msa_icp_inputs.py` (an internal
project reference removed for publication; no behaviour change). The
publication-tree test run below covers the tree exactly as published.
- Publication tree (upstream `main` @ `38e6b894` + this delivery, tree
`09bd84f1`, 4 × GB300):
`tests/experimental/test_cake_msa_icp_indexer.py` → 25 passed.

## Notes
- CUDA-graph capture check: we ran a TP2 MiniMax-M3 vLLM server with
this delivery using Eagle3 k=3 (4 query tokens per request),
FULL_DECODE_ONLY, the default 51-size capture ladder 1..512 and a
2048-column block table. It captured every FULL graph without a geometry
error:
  - 17/17 at `max_num_seqs` 32
- 49/49 at `max_num_seqs` 128 (one graph per distinct decode batch
reached by the ladder at 4 tokens per request: batch 1, every even batch
2..62, then 64..128 in steps of 4; this includes batches 10, 20, 40, 52
and 88)
- 19/19 with speculative decoding off (1 query token, `max_num_seqs`
128)

There were no `NotImplementedError`s and no exchange status errors, and
the server answered a probe request on both ranks (the probe's output
text is not yet valid on this setup because of an NVFP4 main-KV decode
issue outside this PR; this validation checks graph capture, not model
output).
- The `sm_103a` part is exported and measured at 152 SMs (GB300). No
148-SM `sm_103a` part is exported.
- CI runs after each push when triggered by a comment (`@flashinfer-bot
run tests/experimental/test_cake_msa_icp_indexer.py`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for additional two-GPU merge configurations on newer GPU
architectures, covering a wider range of workloads.
* Added coverage for a two-GPU workload with query length 4 and 2,048
score columns.
* **Bug Fixes**
* Improved reliability of CUDA launches by validating inputs and
reporting invalid configurations or launch failures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5c5c44c](https://github.com/flashinfer-ai/flashinfer/commit/5c5c44c314a6dfe7d918bd7e45a90913168e50e5)

- **作者**: eigen
- **时间**: 2026-10-16T20:17:31Z
- **提交信息**: perf(cake_ssd_combined): fused exact-scan programs, host routing, look-back chunk-parallel, exactpre family (SM100 / SM103) (#6582)

## Summary

This PR updates the generated Cake SSDCombined programs for B200
(sm_100a) and GB300 (sm_103a). It also updates the loader
`flashinfer/mamba/cake_ssd_combined.py`. The baseline is the previous
release, FlashInfer `36fd76859292ac2ac5aebd0892fc64715569b9da` (PR #6330
merge). The public API is unchanged.

### Program families

`csrc/cake_mamba_ssd_combined/` now holds 49 device sources and 5 host
templates. The loader table lists 48 programs.

| Family | Device sources | What it is |
|---|---|---|
| `exact_*` | 12 | Previous-release two-kernel exact scan, retained byte
for byte. |
| `exactfused_*` | 12 | Fused single-launch exact scan: preprocess and
scan in one launch. |
| `exactpre_*` | 12 | This release's two-kernel exact scan: standalone
preprocess, then the main kernel. |
| `chunkpar_*` | 6 | Single-pass chunk-parallel scan with decoupled
look-back (fixed Horner fold, range partition). |
| `chunkpar3_*` | 6 | Three-phase chunk-parallel program of the previous
release. Its results are bitwise equal to that release. |
| preprocess | 1 | Metadata preprocess kernel. |

`exact_*` binds the 41 start arguments (`_MAIN_ARGS_START`).
`exactfused_*` and `exactpre_*` bind all 44 (`_MAIN_ARGS`: the 41 plus
`cu_seqlens`, `metadata_from_cu_seqlens`, `preprocess_status`). The
look-back chunk-parallel main kernel takes six more arguments than the
exact scan (`_MAIN_ARGS_CHUNKPAR`, 47) and the three-phase one four more
(`_MAIN_ARGS_CHUNKPAR3`, 45).

The 13 retained files are the 12 `exact_*` device sources and
`host/mamba_ssd_combined_sequence.cpp`. Their SHA-256 digests are pinned
on the Cake side (`_MAMBA_SSD_COMBINED_RETAINED_START_FILES` in the
export module, not in this PR) and checked by the Cake export tool
`tools/export_cake_mamba_ssd_combined.py --check`; the FI test
`test_source_retained_start_programs_are_the_round5_files` carries the
same 13 digests and checks the shipped files against them.

### Host routing

The loader selects one program per call, in this order:

1. The chunk-parallel rule runs first.
`FLASHINFER_CAKE_SSD_CHUNK_PARALLEL` forces or disables it.
2. `fused_selected` mirrors the Cake seed `fused_route`. Calls inside
its window run `exactfused_*`. The window is: batched items <= 1024,
chunks <= 16, (item, chunk) <= 2048; packed varlen items <= 256, (chunk,
head) <= 512.
3. Other calls go to `two_kernel_family`, the mirror of the Cake seed
`two_kernel_route` (`TWO_KERNEL_ROUTE_MIN_CHUNKS = 2`). It counts chunks
per work item: batched `ceil(seqlen/128)`, varlen
`ceil(ceil(packed_tokens/num_sequences)/128)` (num_sequences 0 -> 1). At
>= 2 chunks the call runs `exactpre_*`. At one chunk it runs the
retained `exact_*`.

`exactpre_*` lost the kernel A/B on one-chunk two-kernel calls. Those
calls therefore keep the previous-release program by design.

`_exact_scan_variant` no longer selects the `_noring` twin for
FP32-state varlen calls. In the 93-row gate, only nem_v8x64_float32
changes route.

### Trusted caller cumsum in the triple form (F1b)

- A seq_idx / chunk_indices / chunk_offsets ("triple") call can pass
`seq_chunk_cumsum` with `update_seq_chunk_cumsum=False`. Inside the
fused window, this call now takes the fused program, like the
`cu_seqlens` form.
- On that call the preprocess grid is `(0,1,1)` and
`metadata_from_cu_seqlens=0`. The kernel reads the caller's tables.
- A triple call that derives the table keeps the two-kernel programs.
- `_WorkspaceKey.caller_cumsum` records the case. It is derived from the
call arguments alone.
- `prepare()` reads a given cumsum the way `run()` reads it by default.
In the triple form that is a trusted table. In the `cu_seqlens` form it
is the publishing buffer. `prepare()` and `run()` therefore resolve the
same program.
- A triple-form `run(update_seq_chunk_cumsum=True)` is a different call
shape. It runs the two-kernel program and is captured after one eager
run.

### Launcher, API, branch

- `_load_generated_program` sets
`-DTVM_FFI_CUBIN_LAUNCHER_USE_DRIVER_API=1` (driver-API launcher). Its
bitwise check reads 38/38 on both archs.
- Public API unchanged: `CakeSSDCombined.run/prepare`,
`PreparedSSDCombined`, `SSDCombined(backend="cake")`,
`ssd_combined_fwd`.
- The sglang engine path passes `cu_seqlens` only. F1b does not touch
that path.
- 22 commits on `36fd76859292`: 44 files, +72438 / −327. Changed paths:
`csrc/cake_mamba_ssd_combined/**`,
`flashinfer/mamba/cake_ssd_combined.py`, `tests/mamba/**`.
- Measured head: `31b444fb7fa402582ba60e0dbd694d54ef46e8ca`. PR head:
`63e9d31b255ced943a0eb8ff028f76d29bb504b8`, three commits on top of the
measured head that change comments and docstrings only (51 insertions /
50 deletions across the loader and the two test files; the executable
code is identical: AST with docstrings masked and the comment-free token
stream are equal for all three files, `csrc/` is byte-identical). Every
measurement below was taken on the measured head.

### Labels used below

- **c9**: the same generated kernels with the loader at
`b1cefa5e79f604c460653b3db0273bfcd7bab16f`. This loader predates the
trusted-cumsum route.
- **F1b**: the same generated kernels with this PR's loader (measured at
`31b444fb7fa402582ba60e0dbd694d54ef46e8ca`; the PR head
`63e9d31b255ced943a0eb8ff028f76d29bb504b8` is code-identical, see
above).

## Numerics

- `exact_*` and `chunkpar3_*` are bitwise the previous release.
- `exactfused_*` and `exactpre_*` read a prescaled decay factor table
from shared memory. They update the state with a single-rounding FMA.
The algorithm is the same, but the results are not bitwise the previous
programs.
- `chunkpar_*` differs from the previous programs by the look-back
re-association.

**P6 reading.** It replaces the former bitwise assertions between
program families.

- Oracle: an fp64 token-by-token recurrence. Compared tensors: `out`,
`final_states`, `checkpoint_states`.
- K = 8 fixed seeds per shape. The reference is the previous-release
program on the same inputs.
- Hard clauses, per seed: outlier count (m1) and worst-element ulp
distance (m2) must not exceed the reference.
- Statistical clauses, mean over seeds: p99.9 relative error (m3), RMS
relative error (m4) and max absolute error (m5). Each must stay within
the reference mean plus one seed-to-seed standard deviation.
- Result on the c9 tree: PASS on both archs. GB300: 131 rows plus 20
look-back rows. B200: 141 rows plus 25 look-back rows. F1b changes no
kernel.

**Two packed-varlen metadata forms.** These forms are no longer bitwise
equal in every case.

- A triple call with a trusted caller cumsum runs the same fused program
as the `cu_seqlens` form. The tests assert the two bitwise equal inside
the fused window.
- Consider a triple call that derives the table, with one-chunk items
inside the fused window. It runs the retained `exact_*` two-kernel
program. The `cu_seqlens` form runs `exactfused_*` there. The two differ
only in the last rounding of `final_states`.

Derived triple vs `cu_seqlens` form, 6 cases x 2 repeats:

| Quantity | Result |
|---|---|
| `out` | bitwise equal, 6/6 |
| `final_states`, bf16 state | 0 diff |
| `final_states`, f16 state | <= 1 ulp (1–2 elements) |
| `final_states`, f32 state | max_abs <= 6.0e-8 (max_ulp 26 / 250 /
3217) |
| Error vs fp64 | identical across forms to 4 digits: 2.217e-3 /
3.965e-3 / 2.079e-3 / 2.627e-3 / 3.136e-3 |

Each form passes P6 on its own. The public API and both forms are
unchanged. sglang passes `cu_seqlens` only.

**Determinism.** We ran 7 shapes x 20 launches. Each was repeated under
background-stream load and with the grid knob at {1, 1/2, 1/4}. PASS on
both archs.

## Tests

### GPU module + capture tests

`tests/mamba/test_cake_ssd_combined.py` and
`tests/mamba/test_cake_ssd_combined_capture.py`:

| Loader head | GB300 (sm_103a) | B200 (sm_100a) |
|---|---|---|
| `7fdf10477bdd2680b38d79293e24723daf3b83cc` (comments-only over the
measured head; the PR head `63e9d31b255ced943a0eb8ff028f76d29bb504b8`
differs from it in comments only) | `492 passed, 2 skipped` in 2568.12s
| `492 passed, 2 skipped` in 110.46s |
| `31b444fb7fa402582ba60e0dbd694d54ef46e8ca` (measured head, F1b) | `492
passed, 2 skipped` in 122.90s | `492 passed, 2 skipped` in 125.03s |
| `b1cefa5e79f604c460653b3db0273bfcd7bab16f` (c9) | `490 passed, 2
skipped, 0 failed` | `490 passed, 2 skipped, 0 failed` |

CPU-only subset (`-k "without_gpu or source_"`) at this head: `1 failed,
281 passed, 212 deselected`. Both driver-less environments give the same
counts. The failure is
`test_source_runner_forwards_softplus_and_checkpoint_count`, which needs
a driver.

### New and changed tests

- The bitwise assertions between chunk-parallel and exact-scan programs
are now P6 readings.
- `two_kernel_family` mirrors the Cake seed rule and has cross-check
tests.
- `test_source_retained_start_programs_are_the_round5_files` pins the
SHA-256 of the 13 retained files.
- The `cu_seqlens`-vs-triple test judges the derived triple against the
`cu_seqlens` form under P6 (`_assert_two_forms_p6`). It adds a sanity
check at the state-dtype tolerance. It asserts the trusted-table triple
bitwise equal to the `cu_seqlens` form inside the fused window.
- The out-of-range `seq_idx` test pins one two-kernel family across its
clean / flagged pair. It runs once per family (`exact`, `exactpre`).
-
`test_cake_ssd_combined_chunk_parallel_is_bitwise_the_exact_scan[bf16_triple_*]`
expects `exactfused` for the trusted-cumsum triple inside the fused
window.
- New CPU-only route cases cover four triple variants: derived, trusted,
rewritten buffer, outside the window. A new prepare-vs-run test checks
that both resolve the same workspace key.
- New GPU capture form `triple_cumsum`: prepare -> capture -> three
bitwise replays, with `preprocess_grid == (0,1,1)`.

### Lint and pre-commit

- Pinned ruff 0.12.8 over the loader and both test files: `format
--diff` prints 0 lines, and `check` reports "All checks passed!".
- The repository's pinned pre-commit (16 hooks: 11 ran, including ruff
and mypy; 5 had no matching files) passes on this head with 0 rewrites,
both with the branch config and with the current `main` config. The
branch changes exactly the 44 files listed above and no other file.

## Performance

### Protocol

- 93 rows per arch, timed with CUPTI, cold L2 and 3 interleaved rounds
on an exclusive node.
- The baseline arm is the previous release. Ratio = previous-release
time / candidate time, so > 1 means the candidate is faster.
- Each row has two band readings. The same-run A/A band is max(twin, rr,
0.005). The frozen band was pre-registered before this release's
measurements. A row fails if it falls below 1 − band.
- The verdict pass runs the 7 chunk-parallel rows in their own process.
The disclosure pass runs all rows in the original order.
- CuTe and stock Triton run as reference arms in the same gate.

### GB300 (sm_103a)

| Pass | Tree | Rows | Geomean | Below same-run band | Below frozen band
| Verdict |
|---|---|---|---|---|---|---|
| Verdict pass | c9 | 93 | 1.1568 | 0 | 0 | PASS |
| Disclosure pass (original order) | c9 | 93 | 1.1564 | 0 | 0 | PASS |
| Verdict pass | F1b | 93 | 1.1876 | 0 | 0 | PASS |

All three passes report `fails=0`. The lowest rows all sit inside their
same-run band:

- c9 verdict pass: nem_v160x128_float32 0.9996, nem_v64x128_float32
0.9999 (band 0.005).
- c9 disclosure pass: nem_v64x128_float32 0.9988 (band 0.005).
- F1b verdict pass: nem_v64x128_float32 0.9994, nem_v64x128_bfloat16
0.9998, nem_v160x128_bfloat16 1.0001, nem_v160x128_float32 1.0004 (band
0.005). Also perf_batched_1x64 1.0006 (band 0.0079).

The c9 verdict pass reports `errors=255`. All of them come from the
reference arms:

- 162 x CuTe `state_dtype must be one of [bf16, f16]` on f32-state rows
- 81 x CuTe `seqlen % 128` constraints (9 rows x 3 processes x 3 rounds)
- 12 x a Triton initial-states batch constraint (2 rows x 6)

The candidate and previous-release arms have 0 errors. The F1b verdict
pass also reports `errors=255`.

**Per-class ranges, GB300, c9 tree**

| Class | Rows | Verdict pass | Disclosure pass |
|---|---|---|---|
| Chunk-parallel | 7 | 1.0040–1.0804 | 1.0075–1.0821 |
| Fused single-launch | 27 | 1.0407–2.0529 | 1.0418–2.0574 |
| of which one-chunk batched | 16 | 1.1482–2.0529 | 1.1569–2.0574 |
| Two-kernel, one chunk per item | 31 | 0.9996–1.0639 | 0.9988–1.0701 |
| Two-kernel, >= 2 chunks per item | 28 | 1.0131–1.0684 | 1.0098–1.0551
|

**F1b vs c9 loader, GB300, 7-row A/B**

Both arms use the same Cake head. The run used 3 rounds, CUPTI, cold L2
and `BENCH_MS 300`. Times are the median call in µs. Ratio = c9-loader
time / F1b time, so > 1 means F1b is faster.

| Row | F1b µs | c9 loader µs | Ratio | Kernels F1b / c9 |
|---|---|---|---|---|
| perf_varlen_1x1 | 8.576 | 14.176 | 1.6530 | 1 / 2 |
| perf_varlen_4x1 | 8.704 | 14.592 | 1.6765 | 1 / 2 |
| perf_varlen_8x1 | 9.408 | 15.360 | 1.6327 | 1 / 2 |
| perf_varlen_32x1 | 15.008 | 21.184 | 1.4115 | 1 / 2 |
| perf_varlen_4x8 | 28.320 | 32.960 | 1.1638 | 1 / 2 |
| perf_varlen_8x8 | 29.504 | 33.568 | 1.1377 | 1 / 2 |
| short_varlen_64_60 | 11.520 | 17.344 | 1.5056 | 1 / 2 |

- Geomean 1.4383. 0 rows below either band, `fails=0`, PASS. Same-run
bands are <= 0.0253.
- `errors=9` come from the CuTe arm on short_varlen_64_60: `seqlen (124)
must be divisible by chunk_size (128)`.
- On the c9 loader each row runs the preprocess kernel (3.7–4.1 µs) plus
the main kernel. On F1b each row runs `exactfused_*` alone, with
preprocess grid 0.

**Reference-arm ratios on the same gate, GB300** (reference time /
candidate time)

| Arm | c9 verdict pass | F1b verdict pass |
|---|---|---|
| CuTe | min 2.379, geomean 4.269 | min 2.385, geomean 4.394 |
| stock Triton | min 3.290, geomean 14.616 | min 3.236, geomean 14.931 |

`errors` on reference arms are shape constraints of those arms, not
candidate failures.

### B200 (sm_100a)

Same gate, same 93 rows, exclusive B200 node.

- c9 verdict pass: 93 rows, geomean 1.1052, 0 rows below the same-run
band, 0 below the frozen band, `fails=0`, PASS. Its `errors=801` include
558 import errors of the stock Triton reference arm (a broken reference
checkout on that node; the Triton column for c9 therefore comes from the
supplementary pass below); the remaining 243 are the CuTe shape
constraints. The candidate and previous-release arms have 0 errors.
- c9 disclosure pass (original row order, same tree): geomean 1.1049; 5
of 93 rows fall below the same-run band (short_varlen_1 0.9731,
short_varlen_64_60 0.9846, nem_v4x128_float32 0.9850, perf_batched_1x16
0.9883, nem_v1x128_float32 0.9899), so this pass alone records
`verdict_same_run=FAIL`. These rows are whole-call times of 11.9–32.0
µs; four are cpi=1 two-kernel rows and perf_batched_1x16 is a cpi=16
chunk-parallel look-back row. The preprocess cubins are byte-identical
between the start and final arms, so the preprocess-ratio deviations are
placement and launch-order effects; the same 5 rows sit inside the band
in the verdict pass on the same tree (1.0056 / 1.0000 / 0.9990 / 0.9976
/ 1.0021). The verdict pass governs; the disclosure pass is reported for
completeness.
- F1b verdict pass: 93 rows, geomean 1.1245, 0 rows below the same-run
band, 0 below the frozen band, `fails=0`, PASS. `errors=255` are
reference-arm shape constraints (CuTe 243, Triton 12), not candidate
failures.
- F1b 7-row A/B: geomean 1.2589, 0 rows below either band, `fails=0`,
PASS. `errors=9` are the CuTe arm's chunk-size constraint on
short_varlen_64_60, as on GB300.

**Reference-arm ratios on the same gate, B200** (reference time /
candidate time). The c9 column comes from a supplementary verdict pass
that adds the stock Triton arm (same 93 rows; geomean 1.1052, 0 rows
below either band, PASS); the F1b column is the F1b verdict pass itself.
Rows where an arm does not run are excluded.

| Arm | c9 (rows; min / median / max) | F1b verdict pass (rows; min /
median / max) |
|---|---|---|
| CuTe | 66; 2.103 / 3.141 / 12.855 | 66; 2.100 / 3.253 / 12.835 |
| stock Triton | 91; 2.869 / 9.897 / 49.439 | 91; 2.876 / 9.954 / 49.082
|

### Eager one-wave launch gap

The target is an eager one-wave launch gap of p50 <= 2 µs on the
one-wave rows. Fused rows launch once, so they read 0.00 µs.

- **GB300, c9 tree, shared node:** the fused k=1 rows read 0.00 µs
(5/5), and 7/10 rows are <= 2 µs. The two-launch rows read 2.2–2.9 µs.
The previous-release arm reads 1/10 on the same clause, so we treat this
gap as platform-level.
- **GB300, F1b, exclusive node:** 8/10 rows meet the target, and
perf_varlen_1x1 reads 0.00 µs. Two rows miss it: short_varlen_1 (2.69
µs) and short_varlen_127 (2.54 µs). Both are derived-triple two-kernel
rows, not on the F1b path.
- **GB300, F1b, graph replay:** replay is bitwise 21/21. Four rows show
a replay-span increase of +0.26…+0.42 µs. All four are derived-triple
two-kernel rows.
- **B200, c9 tree, shared node:** 10/10 rows are <= 2 µs (0.00–0.86),
and the two-launch rows read 0.29–0.86 µs. Graph replay is bitwise
21/21.

## Sanitizer

The tool is compute-sanitizer 2026.2.1.0. synccheck and racecheck run as
separate bounded commands. The matrices ran on the c9 tree; they were
not repeated on this PR's head, which changes no kernel source (`csrc/`
is byte-identical between the c9 loader commit and this head; only the
loader and the two test files differ). The Cake sanitizer wrapper now
synchronizes the device before the worker exits. It also requires a
`SANITIZE_DEVICE_SYNC` record, so racecheck records are no longer lost
at exit.

**synccheck: STRICT_PASS.** This holds on both archs, for both the
previous release and this release's Cake head. It covers every executed
form:

- registered CLI `exact_scan` / `chunk_parallel` on 4 shapes
- worker subprocess
- single shape
- custom driver on 4 ring + 4 `_noring` shapes, including the preprocess
kernel
- three-phase entry

**racecheck: INCONCLUSIVE (tool limitation).** INCONCLUSIVE is not a
pass.

- Every call that reuses an aux-ring stage reports WAR records. Counts
on this release's Cake head:
- GB300: `exactpre_*` 5, look-back 9, three-phase 9, and 2 per shape for
the fused program on large shapes.
- B200: `exactpre_*` 5, look-back 9, three-phase 9, and 2/5/2/2 per
shape in the custom driver.
- The fused program on the 3 small registered shapes (<= 2 chunks)
reports 0 records. That is STRICT_PASS on both archs.
- Each record pairs two accesses to the same aux-ring stage
(`smem_delta_all` / `smem_cumsum_all`). One is a loader-warp `STS`. The
other is an `LDS` by pre_inter / pre_intra / epilogue.

Four pieces of evidence point to a tool limitation:

1. Source: the release chain is complete. Reads -> `bar.sync` -> one
elected `mbarrier.arrive.release` -> writer `try_wait.acquire`.
2. Minimal reproducer under the same sanitizer: a race-free ring with an
elected arrive (`elected`) reports 2 WAR. The same ring with per-thread
arrives (`allarrive_both`) reports 0.
3. SASS: every write site is an aux-ring `STS/STS.128`.
4. Addresses: across 40 runs, 30.36 M displayed hazards fall 100 %
inside each program's 2 KiB aux ring, on both archs.

`bar.sync` orders other threads' accesses before the elected arrive.
racecheck 2026.2.1.0 does not count that arrive as releasing them.
compute-sanitizer 2026.3.0.0 gives the same classification on both
archs: the race-free elected-arrive control still reports 2 WAR and the
per-thread-arrive control 0, and the production kernels report the same
record sites (B200: one more record of the same site family on the
three-phase kernel; the B200 `exactpre_*` single-shape run timed out at
1800 s under 2026.3.0.0).

This PR makes no kernel change for this finding. A follow-up evaluates
per-thread `mbarrier.arrive` on the aux-ring empty side. That means
init_count 2/1 -> 256/128, or 384 once pre_intra joins. The change would
touch every program, including the 13 retained files. Its performance
cost is untested.

The sanitizer statements in the PR #6330 description are corrected in a
separate comment.

## End-to-end

We ran Nemotron-H-8B-Reasoning-128K BF16, TP1, through sglang on GB200.
The run used the c9 loader and was not repeated on this PR's loader. The
engine passes `cu_seqlens` only, and the loader change does not touch
that path: with `cu_seqlens` the new fused condition reduces to the c9
condition, and the generated kernels are byte-identical between the two
loaders. A 0-GPU host-route probe confirms it: over 88160 engine call
shapes (128 and 16 heads, 1–64 sequences, 30 fixed packed-token totals
plus 14 per-sequence tiers (30–44 distinct totals per sequence count,
including empty sequences), bf16 and f32 state, with and without z, 4
SM-count / capability settings) both loaders select the same program in
every case. The triple form with a caller cumsum differs in 1680 of 4416
probed shapes (two-kernel -> fused), which is the intended change.

| Arm | GSM8K-200 |
|---|---|
| Baseline | 0.895 |
| Previous release (start) | 0.905 |
| This release (c9) | 0.890 |

- This release − baseline = −0.005 (1 question).
- The previous release saw a band of 0.885–0.890. The baseline and
previous-release arms read 1–3 questions above it.
- We attribute this excursion to batch-composition nondeterminism under
`--parallel 64`. With identical software, stock-vs-stock drifted 0.885
-> 0.895. Single-request probes were byte-identical to an earlier run.
- All arms are NaN-free.
- sglang CPU route tests
(`test/registered/unit/kernels/test_cake_mamba_sp_routes.py`) pass 47/47
on both the unpatched and the patched tree.
- sglang GPU route tests ran at sglang
`328e862122a0f9133620ec7a3ca8b2867ffcbfcd`
(`test/registered/kernels/ops/mamba/test_cake_ssd_combined.py`, 42
tests). The previous-release tree passes 42. The c9 tree gives 38
passed, 4 failed on both archs.
- The 4 failures are the two-form bitwise assertion
`torch.equal(final_cu, final_tr)` in
`test_route_call_cu_seqlens_at_engine_chunk_size_matches_triple_and_stock`.
Routing is unchanged: the two forms run different programs for one-chunk
items under the host route, so they are not bitwise there. The sglang
pin bump carries the test fix (cross-form sanity at the state-dtype
tolerance, each form against the fixed fp64 tolerance, and the bitwise
clause with both forms pinned to the two-kernel family). With that fix
the file passes 42/42 on both GB300 and B200 against this PR's loader
code.

## Cake side

- The Cake-side export tool `tools/export_cake_mamba_ssd_combined.py
--check` (Cake repository, not part of this PR) gives byte-identical
output in the B200 and GB300 environments. It reports 13/13 retained
files, 49 device / 5 host sources and table 12/12/12/6/6.
- Cake GPU tests (the Mamba SSD end-to-end slice of the kernel
generator's GPU test suite): 78 passed on both archs.

## Bot commands and review plan

- At least 1 min after every push, post:
- `@flashinfer-bot run tests/mamba/test_cake_ssd_combined.py
tests/mamba/test_cake_ssd_combined_capture.py`
  - `/bot run`
- Every CodeRabbit thread gets an individual reply, including
outside-diff comments.
- The branch contains only `csrc/cake_mamba_ssd_combined/**`,
`flashinfer/mamba/cake_ssd_combined.py` and `tests/mamba/**`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Added more execution paths for state-space sequence processing, with
automatic selection based on workload characteristics.
* Eligible batched and variable-length workloads can use fused or
chunk-parallel execution.
* **New Features**
* Packed variable-length calls can use caller-provided sequence
metadata; cumulative-length buffers remain available for output.
* Added three-phase chunk-parallel execution alongside existing scan
strategies.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ed3e64d](https://github.com/flashinfer-ai/flashinfer/commit/ed3e64de2438b683e042115d143c07f8557b84aa)

- **作者**: eigen
- **时间**: 2026-10-16T20:14:57Z
- **提交信息**: feat(cake_quant_lora_gemm): prepared NVFP4 LoRA adapter (SVDQuant-equivalent fold) and re-export of the fused quantized-base GEMM + runtime BF16 LoRA kernels (#6581)

Developed by the **CAKE team**. This PR follows up on #6324 (Round 2;
motivation #6303). #6324 added `mm_nvfp4_lora` and `mm_fp8_lora`, which
read the LoRA factors as given at run time. This PR adds an opt-in
**prepared adapter** path for NVFP4. `prepare_nvfp4_lora_adapter(...)`
returns a `PreparedNvFp4LoraAdapter` that folds the LoRA-up weight once:
`B' = bf16_rne(fp32(lora_b) * (lora_scale / alpha))`, with the ratio
computed as a single fp32 round-to-nearest division. `mm_nvfp4_svdquant`
needs this same fold done offline. `mm_nvfp4_lora(...,
lora_adapter=adapter)` then runs the new program `nvfp4_blackwell_svdq`
(SM100, SM103) for every prepared call with K >= 2048; below that K
floor a prepared call raises `ValueError` and the raw path must be used.
The program accumulates base-first and has SVDQuant-equivalent numerics.
If one of the adapter's source tensors (`lora_b`, `lora_scale` or
`alpha`) has moved or been written since the prepare (a change of data
pointer, version counter, shape or device; no value comparison), the
call raises `StaleAdapterError` until the adapter is re-prepared.
Without `lora_adapter`, the NVFP4 path and the FP8 paths keep their
Round-2 semantics: operands consumed as given, fp32 accumulation and one
rounding to bf16.

## What changes

19 files (+3472 / -54), one squashed commit on upstream `main`
`38e6b8944fe8b6497d793ef21fbaadd797ea39d8`.

* **Modified, taken from the export (16).**
* `flashinfer/gemm/cake_quant_lora_gemm.py`: adds
`prepare_nvfp4_lora_adapter` (decorated with `@flashinfer_api` like the
other public entry points), `PreparedNvFp4LoraAdapter`,
`StaleAdapterError` and the `lora_adapter=` route in `mm_nvfp4_lora`.
The unprepared NVFP4 and FP8 paths are unchanged.
* `flashinfer/jit/cake_quant_lora_gemm.py`: adds the
`nvfp4_blackwell_svdq` program record (kernel + binding sources,
dispatch data), an `adapter_states` field on every existing record and,
for the NVFP4 records, a schema-v2 `prepared` dispatch block (K floor
2048) with the `svdq_folded` kernel entry that the raw dispatch rules
never name.
* `flashinfer/__init__.py`: re-exports the three new symbols; its `from
.gemm import` block is re-sorted (six existing lines move, nothing else
is added or removed). `flashinfer/gemm/__init__.py`: three imports and
three `__all__` entries.
* `docs/api/gemm.rst`: extends the existing paragraph with the
prepared-adapter form and adds three autosummary entries
(`prepare_nvfp4_lora_adapter`, `PreparedNvFp4LoraAdapter`,
`StaleAdapterError`).
* `tests/gemm/test_cake_quant_lora_gemm.py`: adds prepared-adapter
equivalence and staleness cases.
`benchmarks/bench_cake_quant_lora_gemm.py`: adds an `--adapter-state
prepared` option (NVFP4 only) that times the prepared path with the
one-time fold outside the timed call.
* `csrc/cake_quant_lora_gemm/cake_quant_lora_gemm_device_common.cuh`:
adds one include (the new `cake_elect_commit_cg2_local` helper) and
reorders two existing includes; its include set is a strict superset of
main's. The shared preamble now serves 18 kernel modules (16 on main;
the svdq program on SM100 and SM103 are the two new ones).
* Eight kernels are re-rendered at their Round-2 program ids:
`nvfp4_blackwell_n192`, `nvfp4_blackwell_n192h`, `nvfp4_blackwell_n256`,
`nvfp4_blackwell_pair`, `fp8_blackwell_n128`, `fp8_blackwell_n256`,
`fp8_blackwell_n256_clc_blocked`, `fp8_blackwell_n256_m256_clc_blocked`.
Each differs from main by the same 9 added lines: one
translation-unit-local fallback definition of `make_warp_uniform`, which
the current exporter emits for a member whose own helper library does
not define that helper while the family's shared preamble carries
another member's definition (an exporter mechanism added in Cake after
the Round-2 export). The kernel bodies are otherwise unchanged.
* **Added (3).**
`csrc/cake_quant_lora_gemm/cake_quant_lora_gemm_140e35bb5ecf92090cf9_kernel.cu`
and `_binding.cu` hold the new program `nvfp4_blackwell_svdq` (NVFP4,
SM100 / SM103).
`csrc/cake_device_helpers/cake_elect_commit_cg2_local_c035d647dc508c30.cuh`
is a `cta_group::2` local elect + commit helper used by the svdq
program.
* **Removed (0).** All ten Round-2 programs keep their ids. The SM90
kernels (`fp8_sm90`, `fp8_sm90_hint`) and all ten Round-2 bindings are
byte-identical to main.
* **Shared device helpers.** Three helpers under
`csrc/cake_device_helpers/` are already on main:
`cake_fma_f32x2_rn_ftz`, `cake_make_sf_cp_desc_lo_sbo128` and
`cake_mbarrier_wait_relaxed_hint`. As in Round 2, they are kept
byte-for-byte. Their code is token-equivalent to this family's
rendering. The renders differ only in comments (the license header
convention and, on two of them, main's DeepGEMM attribution notice) and
whitespace; keeping main's copies preserves those notices.

## Numerics

The prepared path is opt-in and runs only when `lora_adapter` is passed.
Two things move its numerics away from the raw path: the base-first
accumulation order and the bf16 re-rounding of `B'`. Compared with the
raw LoRA-first path:

| metric | prepared (`nvfp4_blackwell_svdq`) | raw LoRA-first |
| --- | ---: | ---: |
| SQNR | 53.8 dB | 55.6 dB |
| max abs error vs fp64 | 0.038 to 0.042 | 0.031 |
| outputs more than 1 bf16 ulp off | 9.3 % | 3e-6 to 5e-6 |

This is the cost of the fold that `mm_nvfp4_svdquant` also requires.
Given the same folded operand, the prepared path's output is bitwise
equal to `mm_nvfp4_svdquant` on all eight checked shapes. Callers who
need the as-given numerics of #6324 can keep calling without
`lora_adapter`. With `lora_scale = 0`, the prepared, raw and no-adapter
calls are bitwise identical on every checked cell. The raw path's
dispatch rules and rule ids are byte-identical to Round 2; the raw
records only gain the prepared-path entries, which the raw path never
reads. The host API docstring carries the SQNR and max-abs-error figures
of this disclosure.

## Export protocol p8 and validation

* **Protocol p8.** 887 rows: SM90 131, SM100 377, SM103 379 (p7 had
663). Every row passes the correctness gate and `source / export >=
0.97`. The gate includes bitwise identity between the loaded program and
the Cake production launcher. As in Round 2, the measurement-stability
metrics `endpoint_drift` and `directional_disagreement` are recorded per
row in the export summaries and do not gate a row.
* **Retention.** The final export revision changed only the test
template. Rows that were not re-measured on it were kept from the
previous revision's sealed passes.
* **FI test module** `tests/gemm/test_cake_quant_lora_gemm.py` on the
export trees: B200 (SM100) 160 passed / 4 skipped; GB300 (SM103) 160
passed / 4 skipped; H100 (SM90) 82 passed / 82 skipped (NVFP4 is
Blackwell-only, so its cases skip on SM90; 4 of the skips are the
torchrun-only TP tests that also skip on B200 / GB300).
* **This PR tree on B200:** 160 passed / 4 skipped on a B200 (revision 2
tree, 58 s)
* **This PR tree, CPU only:** every file in this PR is byte-identical to
the export's output, except `flashinfer/__init__.py` (the merge of
main's import block with the export's three re-export lines) and the
three shared helpers kept at main's copies. A CPU-only step verified the
head and tree hashes, the svdq kernel, the host API and the test module,
and `import flashinfer` with torch 2.13.0+cu130.

## Performance honesty

Timing is kernel-only and paired, on 62 performance rows per
architecture. Ratio = baseline time / prepared time, so a ratio above
1.00 means the prepared path is faster. SM100 numbers are the worse of
two passes on two different nodes. SM103 numbers come from one pass.
Each cell shows three things: the rows at or above 1.00; the ahead / tie
/ behind split, where a tie is a difference inside the row's twin band
(the spread between two repeated measurements of the same arm); and the
median ratio.

| prepared path vs | SM100 (B200) | SM103 (GB300) |
| --- | --- | --- |
| `mm_nvfp4_svdquant` (FlashInfer's fused SVDQuant kernel, autotuned
CUTLASS pick, same fold) | 41 / 62 (38 / 4 / 20), median 1.0106 | 40 /
62 (38 / 3 / 21), median 1.0053 |
| Round-2 production programs on main (raw LoRA-first, #6324) | 61 / 62
(60 / 1 / 1), median 1.0585 | 61 / 62 (61 / 0 / 1), median 1.0598 |
| fastest admitted baseline arm | 38 / 62 (33 / 6 / 23), median 1.0059 |
35 / 62 (33 / 2 / 27), median 1.0029 |

* One row trails the Round-2 production program beyond its twin band:
`perf_h6144_out_m4096_r64` (SM100 ratio 0.9629, prepared 60.35 us). The
same row trails on SM103.
* SM103 routing: the raw path sends the 62 rows to
`nvfp4_blackwell_n256` (29), `nvfp4_blackwell_pair` (24) and
`nvfp4_blackwell_n192` (9). The prepared path sends all 62 to
`nvfp4_blackwell_svdq`.
* SM103 per-GPU clocks were 1926 / 1889 / 1712 MHz. They are disclosed
and were not corrected for.
* No tolerance, denominator or protocol was changed to improve a number.

Cake source revision: 88b28707904d9ffc90f6203a46bc0b8ca8e12ffc (kernels,
bindings and dispatch data exported at
def51f2b2419da477af89676381657551a7d37a1; the host module and
`docs/api/gemm.rst` re-rendered at 88b28707, which adds the
`@flashinfer_api` decorator to `prepare_nvfp4_lora_adapter` and lists
`StaleAdapterError` in the autosummary)

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* NVFP4 LoRA GEMM supports reusable prepared adapters, with public APIs
to prepare and refresh them and detect stale source data.
  * Added a benchmark option to compare raw and prepared adapter paths.
* **Documentation**
* Updated GEMM guidance to cover prepared adapters and their numerical
behavior.
* **Tests**
* Added coverage for prepared-adapter behavior, validation, routing, and
CUDA graph use.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6b88906](https://github.com/flashinfer-ai/flashinfer/commit/6b88906ea97c1e8cd83233f44705f28c6d30be03)

- **作者**: Bo Li
- **时间**: 2026-10-16T20:05:33Z
- **提交信息**: feat(moe_ep)!: sync NVLinkOneSidedAlltoAll with TensorRT-LLM's kernels; remove the deprecated MoeAlltoAll/MnnvlMoe (#6047)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #5532. `flashinfer.moe_ep.NVLinkOneSidedAlltoAll` now runs
its own NVLink one-sided MoE all-to-all kernels, synced with
TensorRT-LLM's (`cpp/tensorrt_llm/kernels/moe/communication/` plus the
later one-sided changes), instead of wrapping the deprecated
`flashinfer.comm.MoeAlltoAll`. The `MoEEpCommunication` interface from
#5532 is unchanged.

It also completes the deprecation started in #5532. No
`MoEEpCommunication` backend builds on `MoeAlltoAll` or `MnnvlMoe` any
more, so both classes are **removed** (breaking; see *Removal and
migration* below). `NVLinkOneSidedAlltoAll` and `CakeAlltoAll` take over
`MoeAlltoAll`'s `checkpoint_prepare` / `checkpoint_restore`.

### What the new kernels bring

- **CFT counted writes.** On Blackwell systems whose driver exports the
CUDA logical-endpoint API, dispatch and combine can push payloads over
the NVLink fabric with `fabric.try_put.counted`. The receiver then waits
on hardware byte counters instead of per-round completion flags, and the
CFT dispatch also fills the padding rows' expert ids itself. The logical
endpoint is bound to the existing MNNVL workspace, so no extra memory is
allocated.
- **Up to 256 EP ranks** (was 64); the active-rank mask grows to four
words.
- **Workspace laid out by phase.** Round state, dispatch control and
payload, and combine control, input and the CFT receive inbox are
separate regions with fixed capacities, which every op validates.
- **Routing and fan-out.**
  - Invalid expert ids are skipped during routing.
- When `top_k > ep_size`, dispatch and combine fan out over a compact
per-rank destination list.
- Receive counters are double-buffered by round parity; the CFT dispatch
publishes them right after routing.
- **Low-precision combine** pairs FP8 conversions.
- **Timeouts** are chosen on the host per launch.

### Python

- `NVLinkOneSidedAlltoAll` drives the new JIT module
(`moe_ep_nvlink_one_sided_alltoall`) directly.
- **Workspace sharing:** instances with the same layout share one
workspace, which is freed when its last instance is destroyed. Instances
on one workspace must run their rounds one after another; a dispatch
while another instance's round awaits its combine raises.
- **CFT setup:** endpoint creation and exchange run over the EP group's
`CommBackend`, so no MPI is involved. Every rank agrees on CFT before
the layout is fixed, and a failure on any rank falls back to the fence
path on all ranks.
- `NVLinkOneSidedConfig` gains:
- `cft`: `None` uses CFT automatically where supported, for steps up to
`cft_max_tokens_for_dispatch` / `cft_max_tokens_for_combine` tokens (128
each); `True` uses it on every supported step; `False` never uses it;
  - `timeout_sec`: the bound on each wait for a peer;
- `enable_pdl`: programmatic dependent launch, `None` enabling it on
SM90+ as before (also on `CakeAlltoAllConfig`).
- `NVLinkOneSidedAlltoAll.active_rank_mask(ranks)` builds the 256-rank
mask, and `cft_enabled` reports whether CFT is available to the
instance.
- **`CakeAlltoAll`** is now a standalone `MoEEpCommunication` (it used
to subclass `NVLinkOneSidedAlltoAll`). The generated Cake kernels
implement the protocol of the functional `moe_a2a_*` ops, which it calls
with `backend="cake"`; those ops are unchanged. `CakeAlltoAll` pins the
combine region at the end of the workspace instead of using the offset
each dispatch returns, which moves with the token count (the race #6376
fixed in `MoeAlltoAll`), and follows the same one-round-per-workspace
rule.
- `benchmarks/moe_ep/core/comm/bench_moe_ep_comm.py` gets `--cft
{auto,on,off}`.
- The module is in the AOT build list for SM90+.

### Checkpointing

`NVLinkOneSidedAlltoAll` and `CakeAlltoAll` gain `checkpoint_prepare()`
and `checkpoint_restore(comm_backend)`, with the semantics `MoeAlltoAll`
had (callers such as vLLM used to reach them through the former
`.alltoall` accessor):

- **Prepare:** releases the physical MNNVL memory and keeps the virtual
addresses reserved.
- **Restore:** remaps the memory over a fresh `CommBackend` and
re-initializes the workspace. CUDA graphs captured before the checkpoint
replay correctly afterwards.
- **Shared rules:** both calls are collective, and repeated calls do
nothing.
- **CFT endpoints:**
- `NVLinkOneSidedAlltoAll` also releases its CFT logical endpoints
before the memory and recreates them afterwards.
- Launches bake the endpoint IDs into their kernel parameters, so the
endpoints keep their ID block reserved across the checkpoint
(`moe_a2a_cft_release_endpoints`) and are recreated under the same IDs.
  - Restore verifies the IDs and raises if they changed.
- **CftLeManager fix:** it now tracks imported peer endpoints
explicitly. It used to treat ID 0 as unset, and ID blocks start at 0, so
the import of rank 0's endpoint was never destroyed. The kernels' copy
in TensorRT-LLM has the same bug.
- The shared MNNVL helpers are `unmap_mnnvl_memory` /
`remap_mnnvl_memory` in `nvlink_common`.

### Removal and migration

`MoeAlltoAll` and `MnnvlMoe` were deprecated in #5532, which ships in a
release before this PR. No backend uses them after this PR:

- `NVLinkOneSidedAlltoAll` runs the new kernels above.
- `CakeAlltoAll` calls the functional `moe_a2a_*` ops with
`backend="cake"`. Instances with the same geometry share a workspace,
which the last one to be destroyed frees, as `NVLinkOneSidedAlltoAll`
does.
- `NVLinkTwoSidedAlltoAll` calls `moe_prepare` / `moe_comm` from
`flashinfer.comm.trtllm_alltoall` directly. Its FIFO positions persist
in the workspace, so, as with `MnnvlMoe`, the workspaces stay with the
process and are shared by every instance of the EP group.

This PR removes both classes, the `flashinfer.comm.MoeAlltoAll` export
and `MoEAlltoallInfo`. The functional ops and their kernels stay.
Migration:

| Removed | Use instead |
|---|---|
| `flashinfer.comm.MoeAlltoAll` |
`flashinfer.moe_ep.NVLinkOneSidedAlltoAll` (newer kernels),
`flashinfer.moe_ep.CakeAlltoAll` for `backend="cake"`, or the
`moe_a2a_*` ops for arbitrary payload lists |
| `MoeAlltoAll.checkpoint_prepare` / `checkpoint_restore` | the methods
of the same names on `NVLinkOneSidedAlltoAll` / `CakeAlltoAll` |
| `flashinfer.comm.trtllm_alltoall.MnnvlMoe` |
`flashinfer.moe_ep.NVLinkTwoSidedAlltoAll`, or `moe_prepare` /
`moe_comm` |

Tests and benchmarks that used the classes now use the replacements:

- Tests that drove the kernels through the classes use the functional
ops, through `tests/comm/moe_a2a_driver.py` where they need per-round
state. Class-only checks (method signatures, the workspace cache) are
dropped.
- The `moe_a2a_dispatch_combine` routine of `flashinfer_benchmark.py`
runs the functional ops.
- `bench_cute_dsl_moe_distributed.py` uses `NVLinkOneSidedAlltoAll`.

### Files

- `csrc/nv_internal/tensorrt_llm/kernels/moe/communication/`: kernels,
CFT logical-endpoint manager, CUDA 13.4 feature gate. The paths mirror
TensorRT-LLM's.
-
`csrc/nv_internal/tensorrt_llm/thop/moe/communication/moeAlltoAllMeta.h`:
workspace layout indices.
- `csrc/moe_ep_nvlink_one_sided_alltoall.cu`: TVM-FFI ops.
- `flashinfer/jit/comm.py`: `gen_moe_ep_nvlink_one_sided_module`.
- `flashinfer/moe_ep/backends/split/comm/{nvlink_one_sided,cake}/`.

## 🔍 Related Issues

Follow-up to #5532 and #4784.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually and fixed any reported issues (run
on the changed files).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated on B300 (CUDA 13.5, driver 620, where CFT counted writes are
available):
- `tests/moe_ep/test_nvlink_one_sided.py` (new; `pytest` spawns one
process per EP rank; also run by `run_tests.sh comm`): 44 passed. Ported
from TensorRT-LLM's `test_nvlink_one_sided.py`: model-shaped round trips
(MXFP8, blockwise FP8, NVFP4 and BF16 dispatch; top_k 3 to 16; EP4 and
EP8; 1, 128 and 1024 tokens), BF16/FP8 combine with external or
workspace input, a 4-rank round sequence with changing and zero token
counts, a delayed rank and the CFT threshold (fence, CFT and automatic;
eager and CUDA graph; PDL on and off), EPLB statistics and the workspace
layout. The round sequence, combine, EPLB and model cases also run on
Cake; with Cake's former moving combine offset the round sequence fails
with mismatched outputs.
- The module also builds for `FLASHINFER_CUDA_ARCH_LIST="9.0a 10.0a
10.3a"`.
- `tests/moe_ep/test_moe_ep_communication_multirank.py` on 4 and 8 GPUs
(`bash tests/moe_ep/run_tests.sh comm`), 18 passed each. The one-sided
cases now run as a fence variant and a CFT variant:
- dispatch/combine against a local reference at top_k 4 and 8
(rank-compact fan-out);
- FP8 combine together with EPLB statistics and an all-active rank mask;
  - split-layer CUDA-graph replay;
  - Cake and two-sided, now off the removed classes, still pass;
- checkpoint/restore around a captured split-layer CUDA graph for the
fence, CFT and Cake paths (4 and 8 GPUs, 3 passed each).
- `tests/moe_ep/test_communication.py` (host-only, stubbed kernels): 31
passed. New cases cover workspace sizing by dispatch format, CFT
selection and probe failures, `enable_pdl`, payload plumbing and
sanitization, the rank mask, config validation, Cake's pinned combine
region, and rejecting interleaved rounds on a shared workspace.
- `bash tests/moe_ep/run_tests.sh unit`: 961 + 1 + 23 passed, 141
skipped.
- The functional ops and their tests in `tests/comm`, now without the
classes:
- `test_trtllm_moe_alltoall.py` and `test_moe_a2a_recv_view_cache.py`:
167 passed;
- `test_mnnvl_moe_alltoall.py` and
`test_mnnvl_moe_alltoall_fused_adapter.py` (`mpirun -np 4`): 41 passed,
1 skipped; the fused adapter's two-rank cycle (`mpirun -np 2`): 24
passed;
  - `test_mnnvl_memory.py` (`mpirun -np 4`): 2 passed.
- `flashinfer_benchmark.py --routine moe_a2a_dispatch_combine
--validate` (plain, `--quant_dtype nvfp4`, `--use_lora`) validates on 4
ranks.
- `bench_cute_dsl_moe_distributed.py --variants w4a16` runs on 8 GPUs.

## Reviewer Notes

- FlashInfer-only features of the old one-sided kernels stay available
through the `moe_a2a_*` ops and are not ported, because
`MoEEpCommunication` does not expose them:
  - combine output quantization (MXFP8/MXFP4/NVFP4);
  - the phased NVFP4 dispatch for hidden ≤ 2048 at EP4/8/16 (#4067).
- **CFT limits:**
- only one workspace per process can bind the logical endpoints; others
use the fence path;
- payload rows must be multiples of 16 bytes, so top_k = 3 or 6 routing
(12- or 24-byte id rows) dispatches over the fence path and only its
combine can use CFT;
- the kernels compile CFT in only with CUDA 13.4+ headers, and the
feature is resolved from the driver at runtime.
- An instance with `enable_rank_mask=True` refuses CUDA-graph capture,
because the mask would be frozen into the graph.

## Follow-ups (separate PRs)

- **Retire the legacy `backend="trtllm"` path of the `moe_a2a_*` ops**
(JIT module `mnnvl_moe_alltoall`, kernels in
`csrc/nv_internal/tensorrt_llm/kernels/communicationKernels/moeAlltoAllKernels.*`).
No `moe_ep` backend uses it after this PR. Deprecate it first, then
remove it together with its tests (`test_trtllm_moe_alltoall.py`,
`test_mnnvl_moe_alltoall.py` / `moe_a2a_driver.py`,
`test_moe_a2a_recv_view_cache.py`; keep the parts that apply to Cake),
and change the `backend` default. The FlashInfer-only features listed
above (combine output quantization, phased NVFP4 dispatch) need a
decision before that: port them or drop them. Until then, note that the
module-level `moe_a2a_dispatch` returns a combine offset that moves with
`runtime_max_tokens_per_rank` and the payload sizes (for both `trtllm`
and `cake`); callers that drive the ops directly must keep the combine
region fixed themselves, as `CakeAlltoAll` does.
- **Retire `benchmarks/routines/moe_comm.py`**
(`moe_a2a_dispatch_combine`), which times the legacy path.
Communication-only cases move to
`benchmarks/moe_ep/core/comm/bench_moe_ep_comm.py`, which needs
`fp8_block_scale` (`DeepSeekFp8`) and an `--extra_payload_bytes` option
(covers `--use_lora`). Dispatch + MoE + combine cases (`--real_math`)
move to `benchmarks/moe_ep/bench_moe_ep.py`, which needs the NVLink
backends (`nvlink_one_sided`, `cake`, `nvlink_two_sided`). Optionally
register `bench_moe_ep_comm.py` as a `flashinfer_benchmark` routine.
- **Move the Cake MoE all-to-all sources out of `nv_internal`** (e.g.
into `csrc/cake_moe_alltoall/`), and remove the per-phase files in
`communicationKernels/` that no JIT spec compiles
(`moeAlltoAllDispatch.cu`, `moeAlltoAllPrepareDispatch.cu`,
`moeAlltoAllStageCombine.cu`, `moeAlltoAllPublishCombine.cu`,
`moeAlltoAllCombine.cu`, `moeAlltoAllQuantizeCombine.cu`,
`moeAlltoAllSanitize.cu`).
- **MNNVL handle selection** (see #5765): pick the handle type from the
first real allocation (create/export, vote, import, vote, then map),
fall back to POSIX on a single host, and share one cached decision
between `MnnvlMemory` and `SymmDeviceMemory`. CFT should then follow the
handle type the workspace actually uses.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added NVLink one-sided expert-parallel communication with optional
counted-write transport, active-rank masking, low-precision combine, and
checkpoint/restore support.
* Cake communication now provides dispatch, combine, workspace
management, and checkpoint/restore.
* Added options for counted-write selection, token limits, and
communication timeouts.
* **Improvements**
* Updated benchmarks and communication paths to use functional dispatch
and combine operations.
  * Added access to distributed allocation handles.
* **API Changes**
  * Removed the legacy `MoeAlltoAll` and `MnnvlMoe` interfaces.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [8dad2ad](https://github.com/flashinfer-ai/flashinfer/commit/8dad2adc7fb11260230ac14795e179350d79a251)

- **作者**: Dhiraj Reddy (cuDNN/FlashInfer)
- **时间**: 2026-10-16T18:29:52Z
- **提交信息**: feat(topk_varlen): gvr_2 decode: fused page-table output (page_table), decode latency floor, K=2048 clustered admission, two-CTA slab for unsplit rows (#5312)

<!-- .github/pull_request_template.md -->

## 📌 Description

Decode-side work on the `top_k_varlen` gvr_2 backend: the fused
page-table output the DeepSeek-V4 decode integration asked for
(`page_table=` / `page_size=`: the selected keys leave the kernel as
physical KV slots), the register-family latency-floor fixes found while
measuring it, the K = 2048 admission to the clustered register family
and the two-CTA-per-SM slab configuration for unsplit rows (the two
decode cell classes that were behind SGLang), programmatic dependent
launch for the slab and cluster families, and a staged coalesced
epilogue for the clustered family's paged output. Rebased on main after
#5304 merged (6e72bc363); the PR is its 14 commits. Consolidates the
former #5315.

**New API** (keyword-only, after `top_k`; decode mode only; the
`top_k_varlen` docstring is the contract: the `page_table` entry states
the tensor, then its effect on the output; the paged engines' limits
live in the gvr_2 entry under `backend`):

- `page_table=` is the request's page map: an `int32` tensor,
contiguous, one row per request, at least `ceil(num_cols / page_size)`
columns. When given, each selected column `c` of request `q` is written
as the physical KV slot `page_table[q, c // page_size] * page_size + c %
page_size` instead of the column; `-1` padding is unchanged. The
`next_n` rows of a request share its table row; columns and `page_size`
are in logits units (compressed units under `compress_ratio=4`). Same
mapping as `top_k_page_table_transform`, fused into the index emit of
all four gvr_2 engine families (register, clustered register, cluster,
streaming slab): one page-table read per selected index, no extra
launch, no extra memory pass.
- `page_size=` is the number of columns per `page_table` entry, a power
of two up to `2**30`. Default `None`, meaning `1` with `page_table`; any
value without `page_table` raises `ValueError`.
- Refused with `ValueError` before any launch, under `auto` and explicit
`gvr_2` alike (the gvr_2 checker admits the call so that `auto` reports
the error instead of "no suitable backend"): `page_table` with
`row_starts` (the paged output frame is decode-only), with `pre_idx`
(the paged compiles carry the table in that ABI slot) or with
`return_values` (the kernels emit indices only); a table that is not a
contiguous 2-D `int32` tensor with one row per request covering the
buffer width; a `page_size` that is not a power of two.
- Only gvr_2 serves paged calls (`auto` never routes them elsewhere; the
other backends' checkers decline). CUDA graphs: `page_size` is part of
the warm-up key, so each paged geometry is warmed up with one eager
paged call on the capturing stream (the host-level `warmup_varlen(...,
page_size=)` compiles the paged set). Compile-time variant per page size
(`paged` + `page_shift` in the compile keys); the default compiles are
byte-identical.
- Parts 2-6 change no API (routing, launch attributes and kernel
epilogues only).

**Breaking since the first push of this PR** (no release carries the old
form): `page_size` defaulted to `1`; it now defaults to `None` (meaning
`1` with `page_table`), and any value passed without `page_table`,
`page_size=1` included, raises `ValueError`.

### Performance summary

fp32, CUDA-graph replay, min of 3 interleaved repetitions, every
comparison on one node in one job; row lengths as stated in each part's
intro (uniform-random in (K, N] for the decode grids). Speedup = the
other kernel's time / ours, or before / after (> 1: this PR is faster).
Every range is the min and max of the corresponding speedup column over
the cells named in the row, read from the collapsed tables below
(nothing excluded unless the cell says so); the per-part prose quotes
rounded ranges that sometimes leave out single noise cells. "n/a" = not
measured on that part.

| Comparison | B200 | B300 | Rubin | B100 / DRIVE P2021 |
|---|---|---|---|---|
| fused `page_table` output vs the window-local kernel + the torch
page-table transform | 2.56-8.24x | 2.49-7.84x | 2.42-7.77x | n/a |
| fused `page_table` output vs FlashInfer's fused
`top_k_page_table_transform` | 1.32-3.04x | 1.35-3.10x | 1.16-2.96x |
n/a |
| fused `page_table` output vs the window-local kernel alone (cost of
the fusion) | 0.90-1.04x | 0.91-1.00x | 0.88-1.00x | n/a |
| fused `page_table` output vs SGLang's fused `topk_transform_512_v2` |
n/a | n/a | 0.82-2.01x | n/a |
| decode floor fixes (PDL, staged emit, early row load), one-wave
register cells, before / after | 0.97-1.26x | 1.00-1.24x | 0.99-1.22x |
n/a |
| K = 2048 clustered register family vs the slab it replaces |
1.25-2.21x | 1.25-2.26x | 1.20-2.80x | n/a |
| two-CTA-per-SM slab configuration vs the one-wave slab (75-148 unsplit
rows, 32K-64K) | 1.10-2.38x | 1.09-2.42x | 1.02-2.14x | 1.27-2.70x |
| PDL on the slab and cluster families, off / on | 1.01-1.05x | n/a |
1.01-1.06x | n/a |
| staged coalesced epilogue of the clustered family's paged output,
before / after | 0.99-1.15x | 0.96-1.16x | 0.98-1.11x | n/a |
| decode grid (N = 32K / 128K) vs SGLang `topk_v2`, after all parts |
1.10-2.66x | n/a | 0.80-2.29x | n/a |

<details>
<summary>Full summary table (per-engine and per-band ranges, control
columns, the other SGLang comparisons)</summary>

| Comparison | B200 | B300 | Rubin | B100 / DRIVE P2021 |
|---|---|---|---|---|
| Part 1: fused `page_table` output vs the window-local gvr_2 kernel +
the torch page-table transform a framework runs today | 2.56-8.24x |
2.49-7.84x | 2.42-7.77x | n/a |
| Part 1: fused `page_table` output vs FlashInfer's fused
`top_k_page_table_transform` (radix / clusters / CUB) | 1.32-3.04x |
1.35-3.10x | 1.16-2.96x | n/a |
| Part 1: fused `page_table` output vs the window-local gvr_2 kernel
alone (cost of the fusion) | 0.902-1.044x | 0.905-1.000x | 0.884-1.000x
| n/a |
| Part 1: fused `page_table` output vs SGLang's fused
`topk_transform_512_v2` | n/a | n/a | 0.82-2.01x (N = 4K: 0.82-1.00x; N
>= 16K: 0.91-2.01x) | n/a |
| Part 2: decode floor (PDL, staged coalesced emit, early row load),
one-wave register cells (rows <= 64, N <= 8K), before / after |
0.968-1.258x | 1.000-1.238x | 0.992-1.215x | n/a |
| Part 2: every other cell of the decode grid, before / after |
0.974-1.083x | 0.975-1.101x | 0.991-1.137x | n/a |
| Part 2: after the floor fixes, vs SGLang `topk_v2` (raw indices), by
engine: register / clustered register / cluster / slab | n/a | n/a |
0.90-1.32x / 1.38-2.24x / 1.74-1.81x / 0.44-1.87x | n/a |
| Part 3: K = 2048 clustered register family vs the slab it replaces
(admitted cells) | 1.25-2.21x | 1.25-2.26x | 1.20-2.80x (1.29-2.80x on
the main grid, 1.20-2.25x in the 37-104-row band above 32K) | n/a |
| Part 3: admitted K = 2048 cells vs SGLang `topk_v2` (raw indices) |
n/a | n/a | 0.74-2.41x (1.03-2.41x outside 1 x 32K and 52 x 20K) | n/a |
| Part 4: two-CTA-per-SM slab configuration vs the one-wave slab, moved
cells (75-148 unsplit rows, 32K-64K) | 1.10-2.38x | 1.09-2.42x |
1.02-2.14x (slab cells; the clustered-register cells of the same grid
0.99-1.01x) | B100 1.32-2.50x, DRIVE P2021 1.27-2.70x |
| Part 4: moved cells vs SGLang `topk_v2` (raw indices) | n/a | n/a |
0.78-1.71x (1.02-1.71x outside K = 2048 at 148 x 32K and 104 x 48K) |
n/a |
| Part 5: PDL on the slab and cluster families, off / on (slab, split
and cluster cells; register-family controls in parentheses) |
1.009-1.049x (controls 1.000-1.032x) | n/a | 1.010-1.057x (controls
1.002-1.056x) | n/a |
| Part 5: the same grid (N = 32K / 128K) vs SGLang `topk_v2` (raw
indices) | 1.10-2.66x | n/a | 0.80-2.29x | n/a |
| Part 6: staged coalesced epilogue for the clustered family's paged
output, staged cells (K <= 1024 at every row count, K = 2048 from 16
rows), before / after (unchanged K = 2048 cells below 16 rows in
parentheses) | 0.986-1.145x (controls 0.979-1.027x) | 0.964-1.158x
(controls 0.984-1.018x) | 0.975-1.112x (controls 0.965-1.000x) | n/a |
| Part 6: clustered paged cells vs SGLang's fused
`topk_transform_512_v2` (page table) | n/a | n/a | 0.74-2.36x
(1.41-2.36x at 1-37 and 64-104 rows except 1024 x 1 x 48K at 0.74x;
1.05-1.31x at 52 rows) | n/a |

</details>

<details>
<summary>Part 1: fused page-table output via page_table / page_size
(prose; B200, B300 and Rubin tables incl. FlashInfer
top_k_page_table_transform and SGLang columns)</summary>

### Part 1: fused page-table output via `page_table` / `page_size`
(commit `feat(topk_varlen): fused page-table output for gvr_2 decode
top-k`)

The DSA **decode** path needs the selected keys as **physical KV
slots**, not as columns of the logits. SGLang's fused decode top-k
(`topk_transform_512_v2`) takes the page table and emits
`page_table[row, c // page_size] * page_size + c % page_size` directly;
a FlashInfer `gvr_2` caller had to run a separate page-table transform
over `num_rows x top_k` indices after every call. This is the output
fusion Akhil asked for in the DeepSeek-V4 sync: it made the end-to-end
comparison unfavourable even where the kernel itself was faster.

This PR adds `top_k_varlen(..., page_table=, page_size=)` (decode mode)
and fuses the transform into the index emit of **all four** gvr_2 engine
families (register, clustered-register, cluster, streaming slab):

- the hint-free compiles never read the `pre_idx` ABI slot, so the paged
compiles carry the page table `[batch, max_pages]` in that slot and
every valid emitted index leaves the kernel as a physical slot: one
page-table read per selected index, no extra launch, no extra memory
pass.
- `-1` pads untouched; the `next_n` rows of a request share the
request's table row; columns and `page_size` are in logits units
(compressed units under `compress_ratio=4`); the table must cover the
logits width.
- compile-time variant per page size (`paged` + `page_shift` in the
compile keys, persist names `..._pg{shift}`): the default compiles are
byte-identical. `warmup_varlen(..., page_size=)` compiles the paged set
for CUDA-graph capture; the `run_varlen` reference engine applies the
same transform.
- not combinable with `return_values` (the raw indices are not kept),
`row_starts` or `pre_idx`; the other backends refuse it (`auto` never
routes it elsewhere).

Same mapping as `top_k_page_table_transform` (radix / clusters / CUB
backends), now available on the gvr_2 engines with `top_k_varlen`'s
`seq_lens` / `next_n` / `compress_ratio` semantics.

#### Perf

Fused paged output vs the window-local kernel alone, and vs the un-fused
alternative a framework must run today (window-local kernel + a
page-table transform pass); SGLang's fused `topk_transform_512_v2` where
importable. fp32, CUDA graph, 3 interleaved reps, min; same node, one
job. Speedups > 1 favour the fused variant.

**B200 (computelab, 148 SMs)** (us; `local` = window-local indices,
`fused` = `page_table=` output, `local+xf` = window-local kernel
followed by the torch page-table transform a framework runs today,
`fi_pt` = FlashInfer's existing fused `top_k_page_table_transform`;
page_size 64)

| K | rows | N | engine | local | fused | local+xf | fi_pt | local/fused
| (local+xf)/fused | fi_pt/fused |
|---|---|---|---|---|---|---|---|---|---|---|
| 512 | 1 | 4096 | register | 3.2 | 3.4 | 28.0 | 7.7 | 0.941x | 8.24x |
2.26x |
| 512 | 1 | 16384 | register | 5.3 | 5.7 | 33.1 | 11.0 | 0.930x | 5.81x
| 1.93x |
| 512 | 1 | 65536 | clustered register | 6.3 | 6.5 | 33.5 | 11.2 |
0.969x | 5.15x | 1.72x |
| 512 | 16 | 4096 | register | 4.0 | 4.0 | 31.3 | 8.8 | 1.000x | 7.83x |
2.20x |
| 512 | 16 | 16384 | register | 5.7 | 6.1 | 33.4 | 12.0 | 0.934x | 5.48x
| 1.97x |
| 512 | 16 | 65536 | clustered register | 7.3 | 7.7 | 32.7 | 14.9 |
0.948x | 4.25x | 1.94x |
| 512 | 64 | 4096 | register | 4.0 | 4.3 | 32.7 | 9.0 | 0.930x | 7.60x |
2.09x |
| 512 | 64 | 16384 | register | 5.7 | 6.1 | 34.2 | 12.0 | 0.934x | 5.61x
| 1.97x |
| 512 | 64 | 65536 | cluster | 8.3 | 8.6 | 34.6 | 24.1 | 0.965x | 4.02x
| 2.80x |
| 512 | 256 | 4096 | register | 4.7 | 5.1 | 31.1 | 15.5 | 0.922x | 6.10x
| 3.04x |
| 512 | 256 | 16384 | slab | 8.1 | 8.6 | 34.8 | 22.5 | 0.942x | 4.05x |
2.62x |
| 512 | 256 | 65536 | slab | 14.7 | 15.3 | 42.3 | 44.0 | 0.961x | 2.76x
| 2.88x |
| 2048 | 1 | 4096 | register | 4.7 | 4.5 | 27.8 | 7.1 | 1.044x | 6.18x |
1.58x |
| 2048 | 1 | 16384 | register | 5.5 | 5.9 | 29.0 | 11.4 | 0.932x | 4.92x
| 1.93x |
| 2048 | 1 | 65536 | slab | 8.6 | 8.8 | 32.7 | 11.6 | 0.977x | 3.72x |
1.32x |
| 2048 | 16 | 4096 | register | 4.7 | 4.7 | 30.5 | 8.6 | 1.000x | 6.49x
| 1.83x |
| 2048 | 16 | 16384 | register | 5.9 | 6.5 | 31.9 | 13.7 | 0.908x |
4.91x | 2.11x |
| 2048 | 16 | 65536 | slab | 9.8 | 9.8 | 35.6 | 17.0 | 1.000x | 3.63x |
1.73x |
| 2048 | 64 | 4096 | register | 4.7 | 4.7 | 31.1 | 8.8 | 1.000x | 6.62x
| 1.87x |
| 2048 | 64 | 16384 | register | 5.9 | 6.5 | 32.3 | 14.1 | 0.908x |
4.97x | 2.17x |
| 2048 | 64 | 65536 | slab | 15.9 | 16.5 | 43.0 | 25.9 | 0.964x | 2.61x
| 1.57x |
| 2048 | 256 | 4096 | register | 6.1 | 6.1 | 37.4 | 15.9 | 1.000x |
6.13x | 2.61x |
| 2048 | 256 | 16384 | slab | 11.0 | 12.2 | 42.5 | 24.8 | 0.902x | 3.48x
| 2.03x |
| 2048 | 256 | 65536 | slab | 19.2 | 20.0 | 51.1 | 52.0 | 0.960x | 2.56x
| 2.60x |

**B300 (computelab, 148 SMs)** (us; `local` = window-local indices,
`fused` = `page_table=` output, `local+xf` = window-local kernel
followed by the torch page-table transform a framework runs today,
`fi_pt` = FlashInfer's existing fused `top_k_page_table_transform`;
page_size 64)

| K | rows | N | engine | local | fused | local+xf | fi_pt | local/fused
| (local+xf)/fused | fi_pt/fused |
|---|---|---|---|---|---|---|---|---|---|---|
| 512 | 1 | 4096 | register | 3.2 | 3.2 | 25.1 | 7.3 | 1.000x | 7.84x |
2.28x |
| 512 | 1 | 16384 | register | 5.0 | 5.4 | 30.2 | 10.6 | 0.926x | 5.59x
| 1.96x |
| 512 | 1 | 65536 | clustered register | 6.1 | 6.3 | 30.8 | 10.8 |
0.968x | 4.89x | 1.71x |
| 512 | 16 | 4096 | register | 3.8 | 4.0 | 26.3 | 8.3 | 0.950x | 6.58x |
2.08x |
| 512 | 16 | 16384 | register | 5.4 | 5.9 | 31.2 | 11.6 | 0.915x | 5.29x
| 1.97x |
| 512 | 16 | 65536 | clustered register | 7.1 | 7.3 | 30.4 | 14.5 |
0.973x | 4.16x | 1.99x |
| 512 | 64 | 4096 | register | 3.8 | 4.0 | 30.4 | 8.5 | 0.950x | 7.60x |
2.12x |
| 512 | 64 | 16384 | register | 5.4 | 5.7 | 31.7 | 11.6 | 0.947x | 5.56x
| 2.04x |
| 512 | 64 | 65536 | cluster | 7.9 | 8.3 | 32.1 | 23.3 | 0.952x | 3.87x
| 2.81x |
| 512 | 256 | 4096 | register | 4.4 | 4.8 | 28.6 | 14.9 | 0.917x | 5.96x
| 3.10x |
| 512 | 256 | 16384 | slab | 7.9 | 8.3 | 32.5 | 21.8 | 0.952x | 3.92x |
2.63x |
| 512 | 256 | 65536 | slab | 14.3 | 14.9 | 40.1 | 42.5 | 0.960x | 2.69x
| 2.85x |
| 2048 | 1 | 4096 | register | 4.2 | 4.2 | 25.1 | 6.7 | 1.000x | 5.98x |
1.60x |
| 2048 | 1 | 16384 | register | 5.2 | 5.7 | 26.3 | 11.0 | 0.912x | 4.61x
| 1.93x |
| 2048 | 1 | 65536 | slab | 8.3 | 8.3 | 30.0 | 11.2 | 1.000x | 3.61x |
1.35x |
| 2048 | 16 | 4096 | register | 4.4 | 4.4 | 28.2 | 8.1 | 1.000x | 6.41x
| 1.84x |
| 2048 | 16 | 16384 | register | 5.7 | 6.3 | 29.4 | 13.2 | 0.905x |
4.67x | 2.10x |
| 2048 | 16 | 65536 | slab | 9.3 | 9.5 | 33.1 | 16.5 | 0.979x | 3.48x |
1.74x |
| 2048 | 64 | 4096 | register | 4.4 | 4.4 | 28.6 | 8.3 | 1.000x | 6.50x
| 1.89x |
| 2048 | 64 | 16384 | register | 5.7 | 6.3 | 30.0 | 13.4 | 0.905x |
4.76x | 2.13x |
| 2048 | 64 | 65536 | slab | 15.5 | 16.1 | 40.3 | 24.9 | 0.963x | 2.50x
| 1.55x |
| 2048 | 256 | 4096 | register | 5.9 | 5.9 | 34.7 | 15.3 | 1.000x |
5.88x | 2.59x |
| 2048 | 256 | 16384 | slab | 10.8 | 11.8 | 40.1 | 24.1 | 0.915x | 3.40x
| 2.04x |
| 2048 | 256 | 65536 | slab | 18.6 | 19.4 | 48.3 | 50.2 | 0.959x | 2.49x
| 2.59x |

**Rubin GR100 (208 SMs)** (us; `local` = window-local indices, `fused` =
`page_table=` output, `local+xf` = window-local kernel followed by the
torch page-table transform a framework runs today, `fi_pt` =
FlashInfer's existing fused `top_k_page_table_transform`, `sgl` =
SGLang's fused `topk_transform_512_v2`; page_size 64)

| K | rows | N | engine | local | fused | local+xf | fi_pt | local/fused
| (local+xf)/fused | fi_pt/fused | sgl | sgl/fused |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 512 | 1 | 4096 | register | 2.3 | 2.6 | 20.2 | 6.0 | 0.885x | 7.77x |
2.31x | 2.6 | 1.00x |
| 512 | 1 | 16384 | register | 3.8 | 4.3 | 22.1 | 8.6 | 0.884x | 5.14x |
2.00x | 3.9 | 0.91x |
| 512 | 1 | 65536 | clustered register | 4.8 | 5.0 | 23.1 | 8.7 | 0.960x
| 4.62x | 1.74x | 7.2 | 1.44x |
| 512 | 16 | 4096 | register | 2.9 | 3.1 | 24.0 | 7.1 | 0.935x | 7.74x |
2.29x | 2.9 | 0.94x |
| 512 | 16 | 16384 | register | 4.4 | 4.8 | 25.7 | 9.5 | 0.917x | 5.35x
| 1.98x | 4.9 | 1.02x |
| 512 | 16 | 65536 | clustered register | 5.5 | 6.1 | 27.6 | 10.0 |
0.902x | 4.52x | 1.64x | 11.2 | 1.84x |
| 512 | 64 | 4096 | register | 2.8 | 3.1 | 23.3 | 7.1 | 0.903x | 7.52x |
2.29x | 3.0 | 0.97x |
| 512 | 64 | 16384 | register | 4.4 | 4.9 | 24.8 | 9.9 | 0.898x | 5.06x
| 2.02x | 4.9 | 1.00x |
| 512 | 64 | 65536 | cluster | 6.6 | 6.7 | 27.9 | 15.5 | 0.985x | 4.16x
| 2.31x | 12.1 | 1.81x |
| 512 | 256 | 4096 | register | 4.9 | 5.5 | 28.0 | 11.9 | 0.891x | 5.09x
| 2.16x | 5.1 | 0.93x |
| 512 | 256 | 16384 | slab | 6.5 | 6.8 | 29.3 | 16.1 | 0.956x | 4.31x |
2.37x | 7.8 | 1.15x |
| 512 | 256 | 65536 | slab | 9.9 | 10.5 | 33.5 | 31.1 | 0.943x | 3.19x |
2.96x | 16.8 | 1.60x |
| 2048 | 1 | 4096 | register | 3.1 | 3.4 | 20.5 | 5.5 | 0.912x | 6.03x |
1.62x | 2.8 | 0.82x |
| 2048 | 1 | 16384 | register | 4.2 | 4.4 | 21.9 | 9.1 | 0.955x | 4.98x
| 2.07x | 4.4 | 1.00x |
| 2048 | 1 | 65536 | slab | 6.8 | 7.0 | 25.6 | 9.4 | 0.971x | 3.66x |
1.34x | 7.7 | 1.10x |
| 2048 | 16 | 4096 | register | 3.3 | 3.6 | 23.6 | 7.1 | 0.917x | 6.56x
| 1.97x | 3.1 | 0.86x |
| 2048 | 16 | 16384 | register | 4.6 | 5.0 | 25.0 | 11.0 | 0.920x |
5.00x | 2.20x | 5.7 | 1.14x |
| 2048 | 16 | 65536 | slab | 7.8 | 7.8 | 28.5 | 12.7 | 1.000x | 3.65x |
1.63x | 15.7 | 2.01x |
| 2048 | 64 | 4096 | register | 3.5 | 3.6 | 26.4 | 7.0 | 0.972x | 7.33x
| 1.94x | 3.2 | 0.89x |
| 2048 | 64 | 16384 | register | 4.8 | 5.2 | 27.8 | 12.0 | 0.923x |
5.35x | 2.31x | 5.7 | 1.10x |
| 2048 | 64 | 65536 | slab | 14.6 | 15.2 | 37.9 | 17.7 | 0.961x | 2.49x
| 1.16x | 15.2 | 1.00x |
| 2048 | 256 | 4096 | register | 5.7 | 6.1 | 31.7 | 12.0 | 0.934x |
5.20x | 1.97x | 5.4 | 0.89x |
| 2048 | 256 | 16384 | slab | 8.0 | 8.6 | 34.1 | 18.1 | 0.930x | 3.97x |
2.10x | 9.0 | 1.05x |
| 2048 | 256 | 65536 | slab | 17.3 | 18.3 | 44.2 | 34.3 | 0.945x | 2.42x
| 1.87x | 20.0 | 1.09x |

The fused paged output is within 5% of the window-local kernel on most
cells and at most 12% slower (the register rungs at N=16K, where the
emit is the largest share of a 5 us kernel); it is 2.4-8.2x faster than
the window-local kernel followed by a page-table transform pass, and
1.2-3.1x faster than FlashInfer's existing fused
`top_k_page_table_transform` (radix / clusters / CUB) on every cell.
Against SGLang's fused `topk_transform_512_v2` (importable on the Rubin
box only) it is 1.0-2.0x faster from N=16K up and 0.82-0.96x at N=4096,
where the un-fused gvr_2 kernel already trails SGLang's by the same
margin (a launch-floor item of the decode kernel, not of the fusion).

</details>

<details>
<summary>Part 2: decode latency floor, PDL + staged coalesced emit +
early row load (prose; before/after tables for B200, B300 and Rubin
incl. SGLang column)</summary>

### Part 2: decode latency floor: PDL launch, staged coalesced emit,
early row load (commit `perf(topk_varlen): gvr_2 decode floor`)

Small-N decode top-k (rows ≤ 64, N ≤ 8K: the DSA decode shape) runs at a
launch-and-latency floor of 3-5 us, and there SGLang's `topk_v2` was
5-27% faster than `gvr_2` (worst: K=2048, N=4096 at 0.73x). Profiling
with Nsight Compute and CUPTI split that gap into two parts: about 0.4
us of launch overlap (SGLang launches with programmatic dependent
launch, so consecutive kernels overlap in a graph) and a kernel-body gap
dominated by scoreboard stalls. Three changes to the **register family**
close it:

1. **Programmatic dependent launch** for the decode register families
(`_DECODE_PDL`). The kernels already `griddepcontrol.wait` before their
first read; passing the launch attribute lets the next kernel's launch
processing overlap this kernel's tail, in a CUDA graph and in a serving
stream alike. ~0.4 us on every decode cell.
2. **Staged coalesced output.** The per-bin-cursor emit writes each
index to a position scattered across the row within a warp, so every
emitted index cost one L1 store sector (5x the sectors of a coalesced
write, ~1 us at k=2048). The k outputs are now staged in a k-word
shared-memory region at the tail of the register kernel's dynamic window
(all emit paths write raw indices there; unwritten slots surface as -1)
and written to global in one coalesced pass after a barrier, which also
applies the prefill / paged output transform. The host enables it for
one-wave launches only (rows ≤ SM count, the latency-bound regime):
several waves deep, the extra barrier + copy measured 3-4% slower than
the scattered stores, so multi-wave launches and the prefill slabs keep
the direct emit (compile-time `stage_out`). The existing warp-ballot
emit arm was measured as the alternative and is slower on every cell.
3. **Early envelope-bounded row load** (decode). The float4 register
batch is loaded at kernel start bounded by the launch envelope (≤ the
row width, memory-safe) instead of after the per-row `kv_lens` read, so
the two global latencies overlap; lanes beyond the row's own length are
-inf-filled in the body. Prefill keeps its in-body load (its base
depends on the `row_starts` read).

No API change. The register families' compile keys gain the `pdl` and
`stage_out` flags; launch shared memory grows by `4 * k` bytes for the
staging region on one-wave launches only.

#### Perf

`top_k_varlen` gvr_2 (hint-free) before vs after on the decode grid, and
vs SGLang's `topk_transform_512_v2` (raw-index mode) where importable.
fp32, uniform-random lengths in `(K, N]`, CUDA graph, 3 interleaved
reps, min; same node, one job. Speedups > 1 favour the new tree.

**B200 (computelab, 148 SMs)** (us; `before` = tree after Part 1,
`after` = tree after Part 2)

| K | rows | N | engine | before | after | before/after |
|---|---|---|---|---|---|---|
| 512 | 1 | 4096 | register | 3.05 | 3.15 | 0.968x |
| 512 | 1 | 8192 | register | 3.56 | 3.46 | 1.029x |
| 512 | 1 | 16384 | register | 4.99 | 4.99 | 1.000x |
| 512 | 1 | 32768 | clustered register | 5.20 | 5.09 | 1.022x |
| 512 | 1 | 65536 | clustered register | 6.12 | 6.01 | 1.018x |
| 512 | 16 | 4096 | register | 3.76 | 3.46 | 1.087x |
| 512 | 16 | 8192 | register | 4.07 | 3.86 | 1.054x |
| 512 | 16 | 16384 | register | 5.10 | 5.19 | 0.983x |
| 512 | 16 | 32768 | clustered register | 5.51 | 5.50 | 1.002x |
| 512 | 16 | 65536 | clustered register | 7.04 | 7.04 | 1.000x |
| 512 | 64 | 4096 | register | 3.76 | 3.46 | 1.087x |
| 512 | 64 | 8192 | register | 4.07 | 3.87 | 1.052x |
| 512 | 64 | 16384 | register | 5.40 | 5.40 | 1.000x |
| 512 | 64 | 32768 | clustered register | 6.73 | 6.84 | 0.984x |
| 512 | 64 | 65536 | cluster | 8.47 | 8.47 | 1.000x |
| 512 | 256 | 4096 | register | 4.48 | 4.28 | 1.047x |
| 512 | 256 | 8192 | register | 5.51 | 5.20 | 1.060x |
| 512 | 256 | 16384 | slab | 7.86 | 8.07 | 0.974x |
| 512 | 256 | 32768 | slab | 11.03 | 10.93 | 1.009x |
| 512 | 256 | 65536 | slab | 14.42 | 14.57 | 0.990x |
| 1024 | 1 | 4096 | register | 3.66 | 3.46 | 1.058x |
| 1024 | 1 | 8192 | register | 3.66 | 3.45 | 1.061x |
| 1024 | 1 | 16384 | register | 4.79 | 4.69 | 1.021x |
| 1024 | 1 | 32768 | clustered register | 5.61 | 5.50 | 1.020x |
| 1024 | 1 | 65536 | clustered register | 6.02 | 6.02 | 1.000x |
| 1024 | 16 | 4096 | register | 3.77 | 3.46 | 1.090x |
| 1024 | 16 | 8192 | register | 4.17 | 3.97 | 1.050x |
| 1024 | 16 | 16384 | register | 5.71 | 5.51 | 1.036x |
| 1024 | 16 | 32768 | clustered register | 5.81 | 5.71 | 1.018x |
| 1024 | 16 | 65536 | clustered register | 7.45 | 7.35 | 1.014x |
| 1024 | 64 | 4096 | register | 3.97 | 3.66 | 1.085x |
| 1024 | 64 | 8192 | register | 4.28 | 4.06 | 1.054x |
| 1024 | 64 | 16384 | register | 5.81 | 5.71 | 1.018x |
| 1024 | 64 | 32768 | clustered register | 7.18 | 6.93 | 1.036x |
| 1024 | 64 | 65536 | cluster | 8.99 | 8.78 | 1.024x |
| 1024 | 256 | 4096 | register | 4.69 | 4.33 | 1.083x |
| 1024 | 256 | 8192 | register | 5.61 | 5.30 | 1.058x |
| 1024 | 256 | 16384 | slab | 8.78 | 8.58 | 1.023x |
| 1024 | 256 | 32768 | slab | 9.70 | 9.50 | 1.021x |
| 1024 | 256 | 65536 | slab | 12.67 | 12.37 | 1.024x |
| 2048 | 1 | 4096 | register | 4.48 | 3.56 | 1.258x |
| 2048 | 1 | 8192 | register | 4.68 | 4.18 | 1.120x |
| 2048 | 1 | 16384 | register | 5.30 | 5.30 | 1.000x |
| 2048 | 1 | 32768 | slab | 9.50 | 9.50 | 1.000x |
| 2048 | 1 | 65536 | slab | 8.47 | 8.47 | 1.000x |
| 2048 | 16 | 4096 | register | 4.37 | 3.55 | 1.231x |
| 2048 | 16 | 8192 | register | 4.58 | 4.27 | 1.073x |
| 2048 | 16 | 16384 | register | 5.60 | 5.60 | 1.000x |
| 2048 | 16 | 32768 | slab | 9.49 | 9.49 | 1.000x |
| 2048 | 16 | 65536 | slab | 9.40 | 9.39 | 1.001x |
| 2048 | 64 | 4096 | register | 4.38 | 3.66 | 1.197x |
| 2048 | 64 | 8192 | register | 4.69 | 4.27 | 1.098x |
| 2048 | 64 | 16384 | register | 5.71 | 5.70 | 1.002x |
| 2048 | 64 | 32768 | slab | 16.46 | 16.46 | 1.000x |
| 2048 | 64 | 65536 | slab | 15.54 | 15.53 | 1.001x |
| 2048 | 256 | 4096 | register | 5.71 | 5.40 | 1.057x |
| 2048 | 256 | 8192 | register | 6.43 | 6.12 | 1.051x |
| 2048 | 256 | 16384 | slab | 11.34 | 11.44 | 0.991x |
| 2048 | 256 | 32768 | slab | 13.08 | 13.07 | 1.001x |
| 2048 | 256 | 65536 | slab | 18.91 | 18.91 | 1.000x |

**B300 (computelab, 148 SMs)** (us; `before` = tree after Part 1,
`after` = tree after Part 2)

| K | rows | N | engine | before | after | before/after |
|---|---|---|---|---|---|---|
| 512 | 1 | 4096 | register | 2.83 | 2.83 | 1.000x |
| 512 | 1 | 8192 | register | 3.45 | 3.24 | 1.065x |
| 512 | 1 | 16384 | register | 4.78 | 4.78 | 1.000x |
| 512 | 1 | 32768 | clustered register | 4.98 | 4.88 | 1.020x |
| 512 | 1 | 65536 | clustered register | 5.90 | 5.80 | 1.017x |
| 512 | 16 | 4096 | register | 3.55 | 3.34 | 1.063x |
| 512 | 16 | 8192 | register | 3.85 | 3.65 | 1.055x |
| 512 | 16 | 16384 | register | 5.19 | 5.08 | 1.022x |
| 512 | 16 | 32768 | clustered register | 5.29 | 5.29 | 1.000x |
| 512 | 16 | 65536 | clustered register | 6.62 | 6.73 | 0.984x |
| 512 | 64 | 4096 | register | 3.65 | 3.34 | 1.093x |
| 512 | 64 | 8192 | register | 3.86 | 3.65 | 1.058x |
| 512 | 64 | 16384 | register | 5.29 | 5.19 | 1.019x |
| 512 | 64 | 32768 | clustered register | 6.62 | 6.52 | 1.015x |
| 512 | 64 | 65536 | cluster | 7.95 | 7.95 | 1.000x |
| 512 | 256 | 4096 | register | 4.47 | 4.06 | 1.101x |
| 512 | 256 | 8192 | register | 5.19 | 5.08 | 1.022x |
| 512 | 256 | 16384 | slab | 7.75 | 7.95 | 0.975x |
| 512 | 256 | 32768 | slab | 10.72 | 10.72 | 1.000x |
| 512 | 256 | 65536 | slab | 14.20 | 14.30 | 0.993x |
| 1024 | 1 | 4096 | register | 3.65 | 3.24 | 1.127x |
| 1024 | 1 | 8192 | register | 3.44 | 3.24 | 1.062x |
| 1024 | 1 | 16384 | register | 4.57 | 4.57 | 1.000x |
| 1024 | 1 | 32768 | clustered register | 5.39 | 5.29 | 1.019x |
| 1024 | 1 | 65536 | clustered register | 5.90 | 5.80 | 1.017x |
| 1024 | 16 | 4096 | register | 3.55 | 3.34 | 1.063x |
| 1024 | 16 | 8192 | register | 4.06 | 3.85 | 1.055x |
| 1024 | 16 | 16384 | register | 5.60 | 5.39 | 1.039x |
| 1024 | 16 | 32768 | clustered register | 5.49 | 5.49 | 1.000x |
| 1024 | 16 | 65536 | clustered register | 7.13 | 7.13 | 1.000x |
| 1024 | 64 | 4096 | register | 3.75 | 3.45 | 1.087x |
| 1024 | 64 | 8192 | register | 4.06 | 3.85 | 1.055x |
| 1024 | 64 | 16384 | register | 5.60 | 5.49 | 1.020x |
| 1024 | 64 | 32768 | clustered register | 6.93 | 6.72 | 1.031x |
| 1024 | 64 | 65536 | cluster | 8.77 | 8.56 | 1.025x |
| 1024 | 256 | 4096 | register | 4.57 | 4.16 | 1.099x |
| 1024 | 256 | 8192 | register | 5.39 | 5.08 | 1.061x |
| 1024 | 256 | 16384 | slab | 8.46 | 8.26 | 1.024x |
| 1024 | 256 | 32768 | slab | 9.18 | 9.28 | 0.989x |
| 1024 | 256 | 65536 | slab | 11.95 | 11.94 | 1.001x |
| 2048 | 1 | 4096 | register | 4.06 | 3.34 | 1.216x |
| 2048 | 1 | 8192 | register | 4.37 | 3.96 | 1.104x |
| 2048 | 1 | 16384 | register | 5.08 | 5.08 | 1.000x |
| 2048 | 1 | 32768 | slab | 9.18 | 9.18 | 1.000x |
| 2048 | 1 | 65536 | slab | 8.16 | 8.16 | 1.000x |
| 2048 | 16 | 4096 | register | 4.17 | 3.44 | 1.212x |
| 2048 | 16 | 8192 | register | 4.37 | 3.96 | 1.104x |
| 2048 | 16 | 16384 | register | 5.39 | 5.39 | 1.000x |
| 2048 | 16 | 32768 | slab | 9.18 | 9.18 | 1.000x |
| 2048 | 16 | 65536 | slab | 9.08 | 9.08 | 1.000x |
| 2048 | 64 | 4096 | register | 4.26 | 3.44 | 1.238x |
| 2048 | 64 | 8192 | register | 4.47 | 4.06 | 1.101x |
| 2048 | 64 | 16384 | register | 5.59 | 5.49 | 1.018x |
| 2048 | 64 | 32768 | slab | 16.04 | 16.04 | 1.000x |
| 2048 | 64 | 65536 | slab | 15.27 | 15.31 | 0.997x |
| 2048 | 256 | 4096 | register | 5.49 | 5.19 | 1.058x |
| 2048 | 256 | 8192 | register | 6.21 | 6.00 | 1.035x |
| 2048 | 256 | 16384 | slab | 11.13 | 11.23 | 0.991x |
| 2048 | 256 | 32768 | slab | 12.76 | 12.82 | 0.995x |
| 2048 | 256 | 65536 | slab | 18.55 | 18.50 | 1.003x |

**Rubin GR100 (208 SMs)** (us; `before` = tree after Part 1, `after` =
tree after Part 2, `sgl` = SGLang `topk_transform_512_v2` raw-index
mode)

| K | rows | N | engine | before | after | before/after | sgl |
sgl/after |
|---|---|---|---|---|---|---|---|---|
| 512 | 1 | 4096 | register | 2.35 | 2.13 | 1.103x | 2.25 | 1.06x |
| 512 | 1 | 8192 | register | 2.80 | 2.66 | 1.053x | 3.07 | 1.15x |
| 512 | 1 | 16384 | register | 3.92 | 3.78 | 1.037x | 3.72 | 0.98x |
| 512 | 1 | 32768 | clustered register | 3.99 | 3.93 | 1.015x | 6.27 |
1.60x |
| 512 | 1 | 65536 | clustered register | 4.78 | 4.72 | 1.013x | 6.65 |
1.41x |
| 512 | 16 | 4096 | register | 2.91 | 2.62 | 1.111x | 2.80 | 1.07x |
| 512 | 16 | 8192 | register | 3.19 | 2.99 | 1.067x | 3.31 | 1.11x |
| 512 | 16 | 16384 | register | 4.43 | 4.15 | 1.067x | 4.68 | 1.13x |
| 512 | 16 | 32768 | clustered register | 4.43 | 4.41 | 1.005x | 7.44 |
1.69x |
| 512 | 16 | 65536 | clustered register | 5.72 | 5.60 | 1.021x | 10.64 |
1.90x |
| 512 | 64 | 4096 | register | 2.89 | 2.59 | 1.116x | 2.82 | 1.09x |
| 512 | 64 | 8192 | register | 3.13 | 3.01 | 1.040x | 3.42 | 1.14x |
| 512 | 64 | 16384 | register | 4.43 | 4.25 | 1.042x | 4.67 | 1.10x |
| 512 | 64 | 32768 | clustered register | 5.62 | 5.60 | 1.004x | 7.73 |
1.38x |
| 512 | 64 | 65536 | cluster | 6.66 | 6.61 | 1.008x | 11.52 | 1.74x |
| 512 | 256 | 4096 | register | 4.91 | 4.32 | 1.137x | 4.78 | 1.11x |
| 512 | 256 | 8192 | register | 4.42 | 4.27 | 1.035x | 5.64 | 1.32x |
| 512 | 256 | 16384 | slab | 6.33 | 6.33 | 1.000x | 7.29 | 1.15x |
| 512 | 256 | 32768 | slab | 8.03 | 8.02 | 1.001x | 10.82 | 1.35x |
| 512 | 256 | 65536 | slab | 9.92 | 9.86 | 1.006x | 15.94 | 1.62x |
| 1024 | 1 | 4096 | register | 2.53 | 2.45 | 1.033x | 2.57 | 1.05x |
| 1024 | 1 | 8192 | register | 2.56 | 2.58 | 0.992x | 2.32 | 0.90x |
| 1024 | 1 | 16384 | register | 3.56 | 3.56 | 1.000x | 3.42 | 0.96x |
| 1024 | 1 | 32768 | clustered register | 4.38 | 4.30 | 1.019x | 6.77 |
1.57x |
| 1024 | 1 | 65536 | clustered register | 4.56 | 4.49 | 1.016x | 6.88 |
1.53x |
| 1024 | 16 | 4096 | register | 2.82 | 2.76 | 1.022x | 2.90 | 1.05x |
| 1024 | 16 | 8192 | register | 3.17 | 3.08 | 1.029x | 3.40 | 1.10x |
| 1024 | 16 | 16384 | register | 4.38 | 4.18 | 1.048x | 4.83 | 1.16x |
| 1024 | 16 | 32768 | clustered register | 4.52 | 4.46 | 1.013x | 8.02 |
1.80x |
| 1024 | 16 | 65536 | clustered register | 5.75 | 5.68 | 1.012x | 12.71
| 2.24x |
| 1024 | 64 | 4096 | register | 2.85 | 2.73 | 1.044x | 2.85 | 1.04x |
| 1024 | 64 | 8192 | register | 3.25 | 3.17 | 1.025x | 3.68 | 1.16x |
| 1024 | 64 | 16384 | register | 4.52 | 4.29 | 1.054x | 5.07 | 1.18x |
| 1024 | 64 | 32768 | clustered register | 5.73 | 5.68 | 1.009x | 8.14 |
1.43x |
| 1024 | 64 | 65536 | cluster | 7.16 | 7.16 | 1.000x | 12.93 | 1.81x |
| 1024 | 256 | 4096 | register | 4.97 | 4.45 | 1.117x | 4.76 | 1.07x |
| 1024 | 256 | 8192 | register | 4.54 | 4.36 | 1.041x | 5.73 | 1.31x |
| 1024 | 256 | 16384 | slab | 6.69 | 6.69 | 1.000x | 7.58 | 1.13x |
| 1024 | 256 | 32768 | slab | 7.54 | 7.50 | 1.005x | 11.95 | 1.59x |
| 1024 | 256 | 65536 | slab | 12.44 | 12.43 | 1.001x | 16.50 | 1.33x |
| 2048 | 1 | 4096 | register | 3.01 | 2.57 | 1.171x | 2.58 | 1.00x |
| 2048 | 1 | 8192 | register | 3.40 | 3.12 | 1.090x | 3.26 | 1.04x |
| 2048 | 1 | 16384 | register | 4.09 | 3.93 | 1.041x | 4.01 | 1.02x |
| 2048 | 1 | 32768 | slab | 7.77 | 7.76 | 1.001x | 3.38 | 0.44x |
| 2048 | 1 | 65536 | slab | 6.76 | 6.71 | 1.007x | 7.05 | 1.05x |
| 2048 | 16 | 4096 | register | 3.22 | 2.75 | 1.171x | 2.75 | 1.00x |
| 2048 | 16 | 8192 | register | 3.51 | 3.24 | 1.083x | 3.38 | 1.04x |
| 2048 | 16 | 16384 | register | 4.51 | 4.34 | 1.039x | 5.12 | 1.18x |
| 2048 | 16 | 32768 | slab | 7.65 | 7.67 | 0.997x | 8.97 | 1.17x |
| 2048 | 16 | 65536 | slab | 7.68 | 7.68 | 1.000x | 14.33 | 1.87x |
| 2048 | 64 | 4096 | register | 3.39 | 2.79 | 1.215x | 2.97 | 1.06x |
| 2048 | 64 | 8192 | register | 3.64 | 3.30 | 1.103x | 3.52 | 1.07x |
| 2048 | 64 | 16384 | register | 4.65 | 4.48 | 1.038x | 5.30 | 1.18x |
| 2048 | 64 | 32768 | slab | 14.32 | 14.33 | 0.999x | 9.03 | 0.63x |
| 2048 | 64 | 65536 | slab | 14.37 | 14.36 | 1.001x | 13.93 | 0.97x |
| 2048 | 256 | 4096 | register | 5.53 | 5.04 | 1.097x | 4.84 | 0.96x |
| 2048 | 256 | 8192 | register | 5.01 | 4.91 | 1.020x | 5.82 | 1.19x |
| 2048 | 256 | 16384 | slab | 7.85 | 7.81 | 1.005x | 8.26 | 1.06x |
| 2048 | 256 | 32768 | slab | 13.42 | 13.54 | 0.991x | 12.55 | 0.93x |
| 2048 | 256 | 65536 | slab | 17.24 | 17.23 | 1.001x | 18.35 | 1.07x |

On the register family's one-wave cells (rows <= 64, N <= 8K) the new
tree is 1.05-1.26x faster on B200, 1.05-1.24x on B300 and 1.05-1.22x on
Rubin, with the largest gains at K=2048, N=4096 (the cell that was 0.73x
SGLang: now 0.94-0.97x on B200, at parity on Rubin). Every other cell is
within noise (worst 0.968x on one 3 us B200 cell that reads 1.000x on
B300; 0.975x on untouched slab cells). Against SGLang's `topk_v2` on
Rubin the register family is now at or above parity on every cell but
one (K=1024, rows=1, N=8192 at 0.90x); the remaining losses are the
few-row K=2048 cells at N >= 32K, which the router sends to the
streaming slab (0.44-0.63x) - a routing/coverage item, not touched here.

</details>

<details>
<summary>Part 3: K = 2048 admitted to the clustered register family
(prose; B200, B300 and two Rubin tables; tests)</summary>

### Part 3: K = 2048 admitted to the clustered register family (commit
`perf(topk_varlen): admit K=2048 to the gvr_2 clustered register
family`)

Few-row decode top-k at K = 2048 and N in (16K, 64K] ran on the
streaming slab: the clustered register-resident family (2-8 CTAs of 1024
threads holding the row in registers, one DSMEM histogram merge) was
gated at `k <= 1024` like upstream. The gate exists because the family's
hint sample is one word per thread; every selection stage after it
(merged scan, cursor emit, crossing-bin tie select over the striped
DSMEM slabs, key-space fallback) is k-generic. This was the last decode
cell class clearly behind SGLang's `topk_v2` (0.44-0.63x on Rubin at
1-64 rows, N = 32K, in the Part 2 tables).

- `route()`: the clustered family admits `k <= 2 * BLKC`. For K > BLKC
the bracket comes from the first BLKC row values instead of the first k
(a looser bracket, the same exact result). Above 32K the K > BLKC
admission also requires the cluster grid to fit one GPC wave, `b * cs <=
7/8 of the SM count`: on B200/B300 (148 SMs) 32 rows x 4-CTA clusters
are admitted and 37 x 4 are not (that band spills into a second wave,
0.89x of the slab at 37 x 48K); on Rubin (208 SMs) 37-44 x 4 are
admitted (2.1-2.3x vs the slab) and 52 x 4 are not (1.2-1.35x there,
left on the slab).
- `GvrRegClusKernel`: the short-row identity write (rows with n <= k)
strides over k instead of assuming k <= BLK. No other kernel change.

#### Perf

Same process, old admission gate vs new (the route patched in-process,
everything else identical), random lengths in (K, N], fp32, CUDA graph,
3 interleaved reps, min; same node, one job. Speedups > 1 favour the new
routing.

**B200 (computelab), 148 SMs** (us; `before` = slab routing (k <= 1024
gate), `after` = this commit)

| K | rows | N | before (engine) | after (engine) | before/after |
|---|---|---|---|---|---|
| 2048 | 1 | 20480 | 8.74 (slab) | 5.66 (clustered register) | 1.54x |
| 2048 | 1 | 32768 | 9.76 (slab) | 5.87 (clustered register) | 1.66x |
| 2048 | 1 | 49152 | 8.63 (slab) | 6.38 (clustered register) | 1.35x |
| 2048 | 1 | 65536 | 8.43 (slab) | 6.17 (clustered register) | 1.37x |
| 2048 | 8 | 20480 | 9.35 (slab) | 6.28 (clustered register) | 1.49x |
| 2048 | 8 | 32768 | 9.76 (slab) | 6.28 (clustered register) | 1.55x |
| 2048 | 8 | 49152 | 9.25 (slab) | 6.79 (clustered register) | 1.36x |
| 2048 | 8 | 65536 | 8.84 (slab) | 6.17 (clustered register) | 1.43x |
| 2048 | 16 | 20480 | 9.25 (slab) | 6.07 (clustered register) | 1.52x |
| 2048 | 16 | 32768 | 9.76 (slab) | 6.07 (clustered register) | 1.61x |
| 2048 | 16 | 49152 | 9.86 (slab) | 7.71 (clustered register) | 1.28x |
| 2048 | 16 | 65536 | 9.35 (slab) | 7.51 (clustered register) | 1.25x |
| 2048 | 32 | 20480 | 10.07 (slab) | 6.08 (clustered register) | 1.66x |
| 2048 | 32 | 32768 | 9.96 (slab) | 6.17 (clustered register) | 1.61x |
| 2048 | 32 | 49152 | 10.16 (slab) | 7.61 (clustered register) | 1.34x |
| 2048 | 32 | 65536 | 9.96 (slab) | 7.61 (clustered register) | 1.31x |
| 2048 | 37 | 20480 | 16.41 (slab) | 10.78 (clustered register) | 1.52x
|
| 2048 | 37 | 32768 | 16.52 (slab) | 10.78 (clustered register) | 1.53x
|
| 2048 | 37 | 49152 | 12.11 (slab) | 12.11 (slab) | 1.00x |
| 2048 | 37 | 65536 | 14.16 (slab) | 14.16 (slab) | 1.00x |
| 2048 | 64 | 20480 | 16.00 (slab) | 7.40 (clustered register) | 2.16x |
| 2048 | 64 | 32768 | 16.62 (slab) | 7.51 (clustered register) | 2.21x |
| 2048 | 64 | 49152 | 15.80 (slab) | 15.85 (slab) | 1.00x |
| 2048 | 64 | 65536 | 15.60 (slab) | 15.60 (slab) | 1.00x |
| 2048 | 148 | 20480 | 17.13 (slab) | 17.13 (slab) | 1.00x |
| 2048 | 148 | 32768 | 17.34 (slab) | 17.33 (slab) | 1.00x |
| 2048 | 148 | 49152 | 16.93 (slab) | 16.93 (slab) | 1.00x |
| 2048 | 148 | 65536 | 17.54 (slab) | 17.54 (slab) | 1.00x |

**B300 (computelab), 148 SMs** (us; `before` = slab routing (k <= 1024
gate), `after` = this commit)

| K | rows | N | before (engine) | after (engine) | before/after |
|---|---|---|---|---|---|
| 2048 | 1 | 20480 | 7.95 (slab) | 5.49 (clustered register) | 1.45x |
| 2048 | 1 | 32768 | 8.66 (slab) | 5.38 (clustered register) | 1.61x |
| 2048 | 1 | 49152 | 7.43 (slab) | 5.69 (clustered register) | 1.31x |
| 2048 | 1 | 65536 | 8.14 (slab) | 5.64 (clustered register) | 1.44x |
| 2048 | 8 | 20480 | 9.48 (slab) | 6.00 (clustered register) | 1.58x |
| 2048 | 8 | 32768 | 8.76 (slab) | 5.99 (clustered register) | 1.46x |
| 2048 | 8 | 49152 | 8.66 (slab) | 6.51 (clustered register) | 1.33x |
| 2048 | 8 | 65536 | 8.55 (slab) | 5.99 (clustered register) | 1.43x |
| 2048 | 16 | 20480 | 9.37 (slab) | 5.59 (clustered register) | 1.68x |
| 2048 | 16 | 32768 | 8.96 (slab) | 5.79 (clustered register) | 1.55x |
| 2048 | 16 | 49152 | 9.58 (slab) | 7.43 (clustered register) | 1.29x |
| 2048 | 16 | 65536 | 9.17 (slab) | 7.32 (clustered register) | 1.25x |
| 2048 | 32 | 20480 | 9.79 (slab) | 5.69 (clustered register) | 1.72x |
| 2048 | 32 | 32768 | 9.79 (slab) | 6.00 (clustered register) | 1.63x |
| 2048 | 32 | 49152 | 9.88 (slab) | 7.53 (clustered register) | 1.31x |
| 2048 | 32 | 65536 | 9.48 (slab) | 7.32 (clustered register) | 1.30x |
| 2048 | 37 | 20480 | 15.63 (slab) | 10.30 (clustered register) | 1.52x
|
| 2048 | 37 | 32768 | 16.04 (slab) | 10.51 (clustered register) | 1.53x
|
| 2048 | 37 | 49152 | 11.83 (slab) | 11.83 (slab) | 1.00x |
| 2048 | 37 | 65536 | 13.57 (slab) | 13.57 (slab) | 1.00x |
| 2048 | 64 | 20480 | 15.52 (slab) | 7.13 (clustered register) | 2.18x |
| 2048 | 64 | 32768 | 16.14 (slab) | 7.13 (clustered register) | 2.26x |
| 2048 | 64 | 49152 | 15.52 (slab) | 15.52 (slab) | 1.00x |
| 2048 | 64 | 65536 | 15.11 (slab) | 15.11 (slab) | 1.00x |
| 2048 | 148 | 20480 | 16.44 (slab) | 16.44 (slab) | 1.00x |
| 2048 | 148 | 32768 | 16.75 (slab) | 16.65 (slab) | 1.01x |
| 2048 | 148 | 49152 | 16.33 (slab) | 16.33 (slab) | 1.00x |
| 2048 | 148 | 65536 | 17.05 (slab) | 17.05 (slab) | 1.00x |

**Rubin GR100, 208 SMs** (us; `before` = slab routing (k <= 1024 gate),
`after` = this commit, `sgl` = SGLang `topk_transform_512_v2` raw-index
mode)

| K | rows | N | before (engine) | after (engine) | before/after | sgl |
sgl/after |
|---|---|---|---|---|---|---|---|
| 2048 | 1 | 20480 | 7.07 (slab) | 4.62 (clustered register) | 1.53x |
4.89 | 1.06x |
| 2048 | 1 | 32768 | 7.97 (slab) | 4.56 (clustered register) | 1.75x |
3.37 | 0.74x |
| 2048 | 1 | 49152 | 6.76 (slab) | 4.91 (clustered register) | 1.38x |
6.97 | 1.42x |
| 2048 | 1 | 65536 | 6.69 (slab) | 4.70 (clustered register) | 1.42x |
7.05 | 1.50x |
| 2048 | 8 | 20480 | 7.59 (slab) | 5.09 (clustered register) | 1.49x |
6.44 | 1.27x |
| 2048 | 8 | 32768 | 7.78 (slab) | 5.10 (clustered register) | 1.53x |
8.95 | 1.75x |
| 2048 | 8 | 49152 | 7.29 (slab) | 5.13 (clustered register) | 1.42x |
7.96 | 1.55x |
| 2048 | 8 | 65536 | 7.25 (slab) | 5.09 (clustered register) | 1.42x |
7.24 | 1.42x |
| 2048 | 16 | 20480 | 7.88 (slab) | 4.80 (clustered register) | 1.64x |
6.48 | 1.35x |
| 2048 | 16 | 32768 | 7.68 (slab) | 4.74 (clustered register) | 1.62x |
8.96 | 1.89x |
| 2048 | 16 | 49152 | 7.85 (slab) | 6.00 (clustered register) | 1.31x |
11.10 | 1.85x |
| 2048 | 16 | 65536 | 7.66 (slab) | 5.96 (clustered register) | 1.29x |
14.34 | 2.41x |
| 2048 | 32 | 20480 | 8.01 (slab) | 5.07 (clustered register) | 1.58x |
6.79 | 1.34x |
| 2048 | 32 | 32768 | 8.19 (slab) | 4.75 (clustered register) | 1.72x |
8.86 | 1.87x |
| 2048 | 32 | 49152 | 7.96 (slab) | 6.05 (clustered register) | 1.32x |
11.17 | 1.85x |
| 2048 | 32 | 65536 | 7.80 (slab) | 6.05 (clustered register) | 1.29x |
13.76 | 2.27x |
| 2048 | 37 | 20480 | 13.48 (slab) | 5.00 (clustered register) | 2.70x |
6.86 | 1.37x |
| 2048 | 37 | 32768 | 13.50 (slab) | 4.82 (clustered register) | 2.80x |
8.74 | 1.81x |
| 2048 | 37 | 49152 | 12.75 (slab) | 12.76 (slab) | 1.00x | 11.70 |
0.92x |
| 2048 | 37 | 65536 | 10.10 (slab) | 10.10 (slab) | 1.00x | 14.10 |
1.40x |
| 2048 | 52 | 20480 | 12.96 (slab) | 8.66 (clustered register) | 1.50x |
6.57 | 0.76x |
| 2048 | 52 | 32768 | 13.52 (slab) | 8.44 (clustered register) | 1.60x |
9.26 | 1.10x |
| 2048 | 52 | 49152 | 12.83 (slab) | 12.83 (slab) | 1.00x | 11.79 |
0.92x |
| 2048 | 52 | 65536 | 12.57 (slab) | 12.57 (slab) | 1.00x | 13.72 |
1.09x |
| 2048 | 64 | 20480 | 12.90 (slab) | 6.06 (clustered register) | 2.13x |
6.89 | 1.14x |
| 2048 | 64 | 32768 | 14.34 (slab) | 5.86 (clustered register) | 2.45x |
9.01 | 1.54x |
| 2048 | 64 | 49152 | 13.91 (slab) | 13.91 (slab) | 1.00x | 11.58 |
0.83x |
| 2048 | 64 | 65536 | 14.37 (slab) | 14.37 (slab) | 1.00x | 13.92 |
0.97x |
| 2048 | 104 | 20480 | 13.70 (slab) | 5.93 (clustered register) | 2.31x
| 6.88 | 1.16x |
| 2048 | 104 | 32768 | 13.46 (slab) | 5.96 (clustered register) | 2.26x
| 9.03 | 1.52x |
| 2048 | 104 | 49152 | 13.51 (slab) | 13.51 (slab) | 1.00x | 11.72 |
0.87x |
| 2048 | 104 | 65536 | 14.22 (slab) | 14.23 (slab) | 1.00x | 14.18 |
1.00x |
| 2048 | 148 | 20480 | 13.99 (slab) | 13.97 (slab) | 1.00x | 6.94 |
0.50x |
| 2048 | 148 | 32768 | 13.79 (slab) | 13.80 (slab) | 1.00x | 9.22 |
0.67x |
| 2048 | 148 | 49152 | 14.02 (slab) | 14.01 (slab) | 1.00x | 11.84 |
0.85x |
| 2048 | 148 | 65536 | 14.04 (slab) | 14.05 (slab) | 1.00x | 14.25 |
1.01x |

**Rubin GR100, rows 37-104 above 32K, 208 SMs** (us; `before` = one-wave
gate at the B200 constant (these rows stay on the slab), `after` = this
commit, `sgl` = SGLang `topk_transform_512_v2` raw-index mode)

| K | rows | N | before (engine) | after (engine) | before/after | sgl |
sgl/after |
|---|---|---|---|---|---|---|---|
| 2048 | 37 | 40960 | 13.92 (slab) | 6.19 (clustered register) | 2.25x |
10.27 | 1.66x |
| 2048 | 37 | 49152 | 12.93 (slab) | 6.32 (clustered register) | 2.05x |
11.81 | 1.87x |
| 2048 | 37 | 65536 | 10.04 (slab) | 6.10 (clustered register) | 1.65x |
14.10 | 2.31x |
| 2048 | 44 | 40960 | 13.81 (slab) | 6.16 (clustered register) | 2.24x |
10.48 | 1.70x |
| 2048 | 44 | 49152 | 12.84 (slab) | 6.04 (clustered register) | 2.13x |
11.73 | 1.94x |
| 2048 | 44 | 65536 | 10.60 (slab) | 6.02 (clustered register) | 1.76x |
13.82 | 2.30x |
| 2048 | 52 | 40960 | 13.80 (slab) | 10.24 (clustered register) | 1.35x
| 10.52 | 1.03x |
| 2048 | 52 | 49152 | 12.99 (slab) | 10.54 (clustered register) | 1.23x
| 11.88 | 1.13x |
| 2048 | 52 | 65536 | 12.59 (slab) | 10.47 (clustered register) | 1.20x
| 13.79 | 1.32x |
| 2048 | 64 | 40960 | 14.15 (slab) | 14.09 (slab) | 1.00x | 10.22 |
0.73x |
| 2048 | 64 | 49152 | 14.13 (slab) | 14.10 (slab) | 1.00x | 11.65 |
0.83x |
| 2048 | 64 | 65536 | 14.39 (slab) | 14.39 (slab) | 1.00x | 13.89 |
0.97x |
| 2048 | 80 | 40960 | 14.38 (slab) | 14.35 (slab) | 1.00x | 10.20 |
0.71x |
| 2048 | 80 | 49152 | 13.37 (slab) | 13.39 (slab) | 1.00x | 11.76 |
0.88x |
| 2048 | 80 | 65536 | 14.01 (slab) | 14.00 (slab) | 1.00x | 13.82 |
0.99x |
| 2048 | 104 | 40960 | 14.00 (slab) | 13.98 (slab) | 1.00x | 10.41 |
0.74x |
| 2048 | 104 | 49152 | 13.50 (slab) | 13.50 (slab) | 1.00x | 11.80 |
0.87x |
| 2048 | 104 | 65536 | 14.22 (slab) | 14.22 (slab) | 1.00x | 14.19 |
1.00x |

On every admitted K = 2048 cell the clustered family is 1.3-2.3x faster
than the slab it replaces on B200 and B300 and 1.5-2.9x on Rubin (208
SMs, where the SM-scaled one-wave gate also admits the 37-44 row band
above 32K at 2.1-2.3x); cells the gate leaves on the slab are unchanged
(identical launches). Against SGLang's topk_v2 on Rubin the admitted K =
2048 cells are now 1.06-2.4x ahead, with two exceptions: 1 x 32K (0.74x,
SGLang's one-CTA 32K path at 3.4 us) and 52 x 20K (0.76x, a 208-CTA
cluster grid). The cells the gate leaves on the slab are unchanged and
remain behind SGLang where they were: 148 rows at 20K-32K (0.50-0.67x)
and 52-104 rows at 48K (0.83-0.92x); both are the slab's per-row cost at
one CTA per row, the next item.

#### Tests

`test_topk_varlen_gvr2.py`: K = 2048 clustered cells in the family
parity/oracle grid (CS = 2 and CS = 4, `next_n` rows), a hint-free
exactness case with short rows through the strided identity write, a
pure `route()` pin of the admission and its one-wave gate; the paged
suite's (8, 32768) x K = 2048 shape now runs the clustered paged engine.

</details>

<details>
<summary>Part 4: unsplit slab rows at 75-148 take the two-CTA-per-SM
configuration (prose; B200, B300, Rubin, B100 and DRIVE P2021 tables;
tests)</summary>

### Part 4: unsplit slab rows at 75-148 take the two-CTA-per-SM
configuration (commit `perf(topk_varlen): gvr_2 unsplit slab rows at
75-148 take the two-CTA-per-SM configuration`)

The streaming slab has two configurations: the "big" one for grids that
fit one wave (`b * R <= 148`: 1024-thread CTAs, one per SM, sample caps
SCAP 16384 / CMP 4096) and the b > 148 one ((512, U 8, MINB 2): 512
threads, two CTAs per SM, the smaller caps). Upstream picks by the wave
test alone. For an unsplit row (R = 1, one CTA per row) in the 75-148
row band that is the wrong choice: at 32K-64K columns the 1024-thread
slab costs 15-19 us on B200 for K in {512, 1024, 2048} while the same
rows at b = 256, already on the b > 148 configuration, cost 7-14 us.
Forcing the U = 8 unroll on the 1024-thread kernel changed nothing and
the 512-thread shape ran the same with either set of host sample
constants, so it is the CTA shape with its BLK-derived caps.

- `_big_regime(b, R, n4)`, one helper for `route` / `route_dynamic` /
`route_streaming` / the varlen launcher: upstream's `b * R <= 148`,
except unsplit rows with 75 <= b <= 148 and n <= 64K, which take the b >
148 configuration. The bounds are measured: 33-74 unsplit rows (only K =
2048 reaches the slab there, above 32K) lose at 64K (0.75x at 37 rows)
and rows above 64K are mixed to bad (0.5x at 75-148 rows x 256K), so
both keep upstream's regime, as do the split slab (R > 1) and b > 148.
`route_dynamic` reads the regime off the static plan (1024-thread CTAs
<=> big): the 64K bound is a band boundary of the static plan, not a
per-row quantity.
- Affected cells: K <= 1024 at 75-148 rows, 32K-64K (below 75 rows the
clustered register family takes them); K = 2048 at 75-148 rows, 20K-64K
where Part 3's one-wave gate leaves them on the slab. Everything else is
an identical launch.

#### Perf

Same process, upstream regime selector vs this commit (patched
in-process, everything else identical), random lengths in (K, N], fp32,
CUDA graph, 3 interleaved reps, min; same node, one job. Speedups > 1
favour the new routing. Only the moved cells are shown (75-148 rows, <=
64K); the B100 / DRIVE runs used the wider first-cut rule, identical on
these cells.

**B200 (computelab), 148 SMs** (us; `before` = upstream regime selector
(`b * R <= 148`), `after` = this commit)

| K | rows | N | before (engine, CTA) | after (engine, CTA) |
before/after |
|---|---|---|---|---|---|
| 512 | 75 | 32768 | 14.44 (slab) | 7.54 (slab) | 1.92x |
| 512 | 75 | 49152 | 17.06 (slab) | 10.20 (slab) | 1.67x |
| 512 | 75 | 65536 | 16.04 (slab) | 8.66 (slab) | 1.85x |
| 512 | 104 | 32768 | 16.55 (slab) | 9.38 (slab) | 1.76x |
| 512 | 104 | 49152 | 16.44 (slab) | 7.74 (slab) | 2.12x |
| 512 | 104 | 65536 | 15.73 (slab) | 13.49 (slab) | 1.17x |
| 512 | 148 | 32768 | 16.09 (slab) | 8.88 (slab) | 1.81x |
| 512 | 148 | 49152 | 16.34 (slab) | 11.43 (slab) | 1.43x |
| 512 | 148 | 65536 | 15.52 (slab) | 9.69 (slab) | 1.60x |
| 1024 | 75 | 32768 | 16.96 (slab) | 7.13 (slab) | 2.38x |
| 1024 | 75 | 49152 | 17.01 (slab) | 8.15 (slab) | 2.09x |
| 1024 | 75 | 65536 | 16.75 (slab) | 9.48 (slab) | 1.77x |
| 1024 | 104 | 32768 | 16.96 (slab) | 7.17 (slab) | 2.37x |
| 1024 | 104 | 49152 | 16.65 (slab) | 8.15 (slab) | 2.04x |
| 1024 | 104 | 65536 | 15.11 (slab) | 9.48 (slab) | 1.59x |
| 1024 | 148 | 32768 | 17.21 (slab) | 8.25 (slab) | 2.09x |
| 1024 | 148 | 49152 | 16.14 (slab) | 8.35 (slab) | 1.93x |
| 1024 | 148 | 65536 | 14.90 (slab) | 9.17 (slab) | 1.62x |
| 2048 | 75 | 32768 | 18.09 (slab) | 8.97 (slab) | 2.02x |
| 2048 | 75 | 49152 | 17.57 (slab) | 16.04 (slab) | 1.10x |
| 2048 | 75 | 65536 | 17.27 (slab) | 11.44 (slab) | 1.51x |
| 2048 | 104 | 32768 | 18.09 (slab) | 9.58 (slab) | 1.89x |
| 2048 | 104 | 49152 | 16.25 (slab) | 10.21 (slab) | 1.59x |
| 2048 | 104 | 65536 | 16.76 (slab) | 11.64 (slab) | 1.44x |
| 2048 | 148 | 32768 | 16.96 (slab) | 9.29 (slab) | 1.83x |
| 2048 | 148 | 49152 | 16.97 (slab) | 10.32 (slab) | 1.64x |
| 2048 | 148 | 65536 | 17.88 (slab) | 13.99 (slab) | 1.28x |

**B300 (computelab), 148 SMs** (us; `before` = upstream regime selector
(`b * R <= 148`), `after` = this commit)

| K | rows | N | before (engine, CTA) | after (engine, CTA) |
before/after |
|---|---|---|---|---|---|
| 512 | 75 | 32768 | 13.79 (slab) | 7.23 (slab) | 1.91x |
| 512 | 75 | 49152 | 16.44 (slab) | 9.79 (slab) | 1.68x |
| 512 | 75 | 65536 | 15.32 (slab) | 8.26 (slab) | 1.85x |
| 512 | 104 | 32768 | 15.83 (slab) | 8.97 (slab) | 1.76x |
| 512 | 104 | 49152 | 15.73 (slab) | 7.44 (slab) | 2.11x |
| 512 | 104 | 65536 | 15.12 (slab) | 12.66 (slab) | 1.19x |
| 512 | 148 | 32768 | 15.42 (slab) | 8.46 (slab) | 1.82x |
| 512 | 148 | 49152 | 15.73 (slab) | 11.12 (slab) | 1.41x |
| 512 | 148 | 65536 | 14.91 (slab) | 9.38 (slab) | 1.59x |
| 1024 | 75 | 32768 | 16.04 (slab) | 6.63 (slab) | 2.42x |
| 1024 | 75 | 49152 | 16.46 (slab) | 8.06 (slab) | 2.04x |
| 1024 | 75 | 65536 | 16.24 (slab) | 9.18 (slab) | 1.77x |
| 1024 | 104 | 32768 | 16.25 (slab) | 6.82 (slab) | 2.38x |
| 1024 | 104 | 49152 | 16.14 (slab) | 8.05 (slab) | 2.00x |
| 1024 | 104 | 65536 | 14.60 (slab) | 9.08 (slab) | 1.61x |
| 1024 | 148 | 32768 | 16.54 (slab) | 7.85 (slab) | 2.11x |
| 1024 | 148 | 49152 | 15.64 (slab) | 8.15 (slab) | 1.92x |
| 1024 | 148 | 65536 | 14.45 (slab) | 8.98 (slab) | 1.61x |
| 2048 | 75 | 32768 | 17.37 (slab) | 8.57 (slab) | 2.03x |
| 2048 | 75 | 49152 | 16.86 (slab) | 15.43 (slab) | 1.09x |
| 2048 | 75 | 65536 | 16.65 (slab) | 10.92 (slab) | 1.52x |
| 2048 | 104 | 32768 | 17.37 (slab) | 9.28 (slab) | 1.87x |
| 2048 | 104 | 49152 | 15.68 (slab) | 9.89 (slab) | 1.59x |
| 2048 | 104 | 65536 | 16.19 (slab) | 11.02 (slab) | 1.47x |
| 2048 | 148 | 32768 | 16.34 (slab) | 8.97 (slab) | 1.82x |
| 2048 | 148 | 49152 | 16.34 (slab) | 10.00 (slab) | 1.63x |
| 2048 | 148 | 65536 | 17.16 (slab) | 13.37 (slab) | 1.28x |

**Rubin GR100, 208 SMs** (us; `before` = upstream regime selector (`b *
R <= 148`), `after` = this commit, `sgl` = SGLang
`topk_transform_512_v2` raw-index mode)

| K | rows | N | before (engine, CTA) | after (engine, CTA) |
before/after | sgl | sgl/after |
|---|---|---|---|---|---|---|---|
| 512 | 75 | 32768 | 5.59 (clustered register) | 5.56 (clustered
register) | 1.01x | 7.60 | 1.37x |
| 512 | 75 | 49152 | 13.28 (slab) | 7.53 (slab) | 1.76x | 9.56 | 1.27x |
| 512 | 75 | 65536 | 12.90 (slab) | 7.26 (slab) | 1.78x | 11.47 | 1.58x
|
| 512 | 104 | 32768 | 5.70 (clustered register) | 5.76 (clustered
register) | 0.99x | 7.74 | 1.34x |
| 512 | 104 | 49152 | 13.19 (slab) | 7.63 (slab) | 1.73x | 9.63 | 1.26x
|
| 512 | 104 | 65536 | 13.37 (slab) | 7.94 (slab) | 1.68x | 11.66 | 1.47x
|
| 512 | 148 | 32768 | 12.56 (slab) | 6.08 (slab) | 2.07x | 7.72 | 1.27x
|
| 512 | 148 | 49152 | 13.07 (slab) | 7.32 (slab) | 1.79x | 9.62 | 1.31x
|
| 512 | 148 | 65536 | 13.46 (slab) | 7.32 (slab) | 1.84x | 11.67 | 1.59x
|
| 1024 | 75 | 32768 | 5.64 (clustered register) | 5.62 (clustered
register) | 1.00x | 8.25 | 1.47x |
| 1024 | 75 | 49152 | 13.98 (slab) | 6.52 (slab) | 2.14x | 10.64 | 1.63x
|
| 1024 | 75 | 65536 | 13.36 (slab) | 7.63 (slab) | 1.75x | 12.77 | 1.67x
|
| 1024 | 104 | 32768 | 5.80 (clustered register) | 5.72 (clustered
register) | 1.01x | 8.19 | 1.43x |
| 1024 | 104 | 49152 | 13.79 (slab) | 6.85 (slab) | 2.01x | 10.58 |
1.54x |
| 1024 | 104 | 65536 | 12.15 (slab) | 7.59 (slab) | 1.60x | 13.00 |
1.71x |
| 1024 | 148 | 32768 | 13.88 (slab) | 8.27 (slab) | 1.68x | 8.43 | 1.02x
|
| 1024 | 148 | 49152 | 13.59 (slab) | 6.83 (slab) | 1.99x | 10.74 |
1.57x |
| 1024 | 148 | 65536 | 13.21 (slab) | 10.55 (slab) | 1.25x | 12.94 |
1.23x |
| 2048 | 75 | 32768 | 5.84 (clustered register) | 5.90 (clustered
register) | 0.99x | 9.02 | 1.53x |
| 2048 | 75 | 49152 | 13.20 (slab) | 8.97 (slab) | 1.47x | 11.75 | 1.31x
|
| 2048 | 75 | 65536 | 13.19 (slab) | 9.33 (slab) | 1.41x | 13.78 | 1.48x
|
| 2048 | 104 | 32768 | 5.95 (clustered register) | 5.96 (clustered
register) | 1.00x | 8.97 | 1.51x |
| 2048 | 104 | 49152 | 13.50 (slab) | 13.22 (slab) | 1.02x | 11.76 |
0.89x |
| 2048 | 104 | 65536 | 14.20 (slab) | 9.71 (slab) | 1.46x | 14.14 |
1.46x |
| 2048 | 148 | 32768 | 13.80 (slab) | 11.65 (slab) | 1.18x | 9.13 |
0.78x |
| 2048 | 148 | 49152 | 13.97 (slab) | 8.85 (slab) | 1.58x | 11.87 |
1.34x |
| 2048 | 148 | 65536 | 14.02 (slab) | 12.88 (slab) | 1.09x | 14.23 |
1.10x |

**B100, 148 SMs** (us; `before` = upstream regime selector (`b * R <=
148`), `after` = this commit)

| K | rows | N | before (engine, CTA) | after (engine, CTA) |
before/after |
|---|---|---|---|---|---|
| 512 | 75 | 32768 | 13.96 (slab) | 6.49 (slab) | 2.15x |
| 512 | 75 | 65536 | 15.70 (slab) | 8.38 (slab) | 1.87x |
| 512 | 104 | 32768 | 16.22 (slab) | 6.49 (slab) | 2.50x |
| 512 | 104 | 65536 | 15.60 (slab) | 8.74 (slab) | 1.78x |
| 512 | 148 | 32768 | 15.81 (slab) | 6.49 (slab) | 2.44x |
| 512 | 148 | 65536 | 15.30 (slab) | 8.74 (slab) | 1.75x |
| 1024 | 75 | 32768 | 16.73 (slab) | 7.10 (slab) | 2.36x |
| 1024 | 75 | 65536 | 16.73 (slab) | 9.87 (slab) | 1.70x |
| 1024 | 104 | 32768 | 16.73 (slab) | 7.11 (slab) | 2.35x |
| 1024 | 104 | 65536 | 14.89 (slab) | 9.77 (slab) | 1.52x |
| 1024 | 148 | 32768 | 16.93 (slab) | 7.21 (slab) | 2.35x |
| 1024 | 148 | 65536 | 14.78 (slab) | 9.77 (slab) | 1.51x |
| 2048 | 75 | 32768 | 17.76 (slab) | 10.89 (slab) | 1.63x |
| 2048 | 75 | 65536 | 17.24 (slab) | 13.04 (slab) | 1.32x |
| 2048 | 104 | 32768 | 17.86 (slab) | 11.00 (slab) | 1.62x |
| 2048 | 104 | 65536 | 16.83 (slab) | 12.02 (slab) | 1.40x |
| 2048 | 148 | 32768 | 17.04 (slab) | 10.48 (slab) | 1.63x |
| 2048 | 148 | 65536 | 17.65 (slab) | 12.22 (slab) | 1.44x |

**DRIVE P2021, 68 SMs** (us; `before` = upstream regime selector (`b * R
<= 148`), `after` = this commit)

| K | rows | N | before (engine, CTA) | after (engine, CTA) |
before/after |
|---|---|---|---|---|---|
| 512 | 75 | 32768 | 17.88 (slab) | 8.97 (slab) | 1.99x |
| 512 | 75 | 65536 | 26.59 (slab) | 11.84 (slab) | 2.25x |
| 512 | 104 | 32768 | 26.48 (slab) | 9.79 (slab) | 2.70x |
| 512 | 104 | 65536 | 20.24 (slab) | 13.07 (slab) | 1.55x |
| 512 | 148 | 32768 | 32.72 (slab) | 14.29 (slab) | 2.29x |
| 512 | 148 | 65536 | 34.16 (slab) | 17.47 (slab) | 1.96x |
| 1024 | 75 | 32768 | 21.56 (slab) | 11.12 (slab) | 1.94x |
| 1024 | 75 | 65536 | 25.45 (slab) | 13.07 (slab) | 1.95x |
| 1024 | 104 | 32768 | 24.84 (slab) | 11.53 (slab) | 2.15x |
| 1024 | 104 | 65536 | 23.51 (slab) | 15.01 (slab) | 1.57x |
| 1024 | 148 | 32768 | 28.73 (slab) | 15.83 (slab) | 1.81x |
| 1024 | 148 | 65536 | 30.78 (slab) | 19.52 (slab) | 1.58x |
| 2048 | 75 | 32768 | 27.25 (slab) | 17.57 (slab) | 1.55x |
| 2048 | 75 | 65536 | 23.41 (slab) | 18.49 (slab) | 1.27x |
| 2048 | 104 | 32768 | 29.55 (slab) | 16.24 (slab) | 1.82x |
| 2048 | 104 | 65536 | 26.07 (slab) | 19.52 (slab) | 1.34x |
| 2048 | 148 | 32768 | 37.54 (slab) | 22.38 (slab) | 1.68x |
| 2048 | 148 | 65536 | 34.36 (slab) | 25.25 (slab) | 1.36x |

On the moved cells (75-148 rows, 32K-64K) the two-CTA configuration is
1.5-2.5x faster than the one-wave slab on B200 and B300 for K <= 1024
and 1.1-2.0x for K = 2048, 1.5-2.6x on B100 and DRIVE P2021 (68 SMs),
and 1.2-2.1x on Rubin; no moved cell is slower on any part. Against
SGLang's topk_v2 on Rubin these cells go from 0.55-0.9x to 1.0-1.6x, the
two exceptions being K = 2048 at 148 x 32K (0.78x) and 104 x 48K
(0.89x).

#### Tests

`test_topk_varlen_gvr2.py`: the regime pinned for K in {512, 1024, 2048}
at 75-148 rows and 32K/48K/64K ((512, 8, 2) with the b > 148 sample
caps), 1024 threads again just above 64K, at 37 rows, for the split slab
and for b > 148, the helper's boundaries; two family parity/oracle cells
run the moved configuration (100 x 64K at K = 512, 148 x 32K at K =
2048).

</details>

<details>
<summary>Part 5: programmatic dependent launch for the slab and cluster
families (prose; B200 and Rubin tables incl. SGLang columns)</summary>

### Part 5: programmatic dependent launch for the slab and cluster
families (commit `perf(topk_varlen): programmatic dependent launch for
the gvr_2 slab and cluster families`)

Part 2 gave the register families a programmatic dependent launch
(`griddepcontrol.wait` as the first instruction, the launch attribute on
the kernel) so a following kernel's launch processing overlaps the tail
of the previous one; the streaming slab (`GvrMainKernel`) and the
cluster split (`GvrClusKernel`) still launched without it. This adds the
same `pdl` compile flag (part of the compile key and persist name,
default off) to both and passes it from the varlen launcher, so every
decode engine launches the same way. The wait precedes every global read
(including the split slab's workspace) and no kernel triggers early, so
ordering is exactly the stream order; only the launch latency overlaps.
Prefill launches are unchanged.

#### Perf

Same process, PDL off on every family vs on (this commit), random
lengths in (K, N], fp32, CUDA graph, 3 interleaved reps, min; same node,
one job. The register-family rows are controls (they had PDL since Part
2; `off` turns it off there too).

**B200 (local), 148 SMs** (us; `off` = no programmatic dependent launch
on any family, `on` = this commit, `sgl` = SGLang
`topk_transform_512_v2` raw-index mode)

| K | rows | N | engine | off | on | off/on | sgl | sgl/on |
|---|---|---|---|---|---|---|---|---|
| 512 | 16 | 32768 | clustered register | 5.67 | 5.57 | 1.018x | 9.16 |
1.64x |
| 512 | 16 | 131072 | slab | 10.08 | 9.72 | 1.037x | 14.02 | 1.44x |
| 512 | 64 | 32768 | clustered register | 7.00 | 6.90 | 1.014x | 9.46 |
1.37x |
| 512 | 64 | 131072 | cluster | 10.80 | 10.49 | 1.030x | 27.89 | 2.66x |
| 512 | 148 | 32768 | slab | 9.16 | 8.85 | 1.035x | 9.77 | 1.10x |
| 512 | 148 | 131072 | slab | 18.17 | 17.76 | 1.023x | 33.53 | 1.89x |
| 512 | 256 | 32768 | slab | 11.61 | 11.31 | 1.027x | 14.89 | 1.32x |
| 512 | 256 | 131072 | slab | 18.12 | 17.34 | 1.045x | 37.88 | 2.18x |
| 1024 | 16 | 32768 | clustered register | 6.08 | 5.98 | 1.017x | 9.87 |
1.65x |
| 1024 | 16 | 131072 | slab | 11.92 | 11.66 | 1.022x | 15.71 | 1.35x |
| 1024 | 64 | 32768 | clustered register | 7.41 | 7.41 | 1.000x | 10.29
| 1.39x |
| 1024 | 64 | 131072 | cluster | 11.00 | 10.90 | 1.009x | 28.51 | 2.62x
|
| 1024 | 148 | 32768 | slab | 8.54 | 8.23 | 1.038x | 10.38 | 1.26x |
| 1024 | 148 | 131072 | slab | 17.86 | 17.45 | 1.023x | 40.64 | 2.33x |
| 1024 | 256 | 32768 | slab | 10.08 | 9.77 | 1.032x | 16.63 | 1.70x |
| 1024 | 256 | 131072 | slab | 19.50 | 19.19 | 1.016x | 43.36 | 2.26x |
| 2048 | 16 | 32768 | clustered register | 6.39 | 6.19 | 1.032x | 11.92
| 1.93x |
| 2048 | 16 | 131072 | slab | 10.39 | 9.98 | 1.041x | 17.76 | 1.78x |
| 2048 | 64 | 32768 | clustered register | 7.72 | 7.62 | 1.013x | 11.92
| 1.56x |
| 2048 | 64 | 131072 | slab | 16.53 | 16.22 | 1.019x | 29.28 | 1.81x |
| 2048 | 148 | 32768 | slab | 9.83 | 9.37 | 1.049x | 12.02 | 1.28x |
| 2048 | 148 | 131072 | slab | 16.99 | 16.73 | 1.016x | 42.13 | 2.52x |
| 2048 | 256 | 32768 | slab | 14.06 | 13.76 | 1.022x | 18.68 | 1.36x |
| 2048 | 256 | 131072 | slab | 21.86 | 21.64 | 1.010x | 51.29 | 2.37x |

**Rubin GR100, 208 SMs** (us; `off` = no programmatic dependent launch
on any family, `on` = this commit, `sgl` = SGLang
`topk_transform_512_v2` raw-index mode)

| K | rows | N | engine | off | on | off/on | sgl | sgl/on |
|---|---|---|---|---|---|---|---|---|
| 512 | 16 | 32768 | clustered register | 4.70 | 4.45 | 1.056x | 7.35 |
1.65x |
| 512 | 16 | 131072 | slab | 7.79 | 7.37 | 1.057x | 10.40 | 1.41x |
| 512 | 148 | 32768 | slab | 6.09 | 5.76 | 1.057x | 7.72 | 1.34x |
| 512 | 148 | 131072 | slab | 11.88 | 11.56 | 1.028x | 26.45 | 2.29x |
| 512 | 256 | 32768 | slab | 8.20 | 7.91 | 1.037x | 10.77 | 1.36x |
| 512 | 256 | 131072 | slab | 18.67 | 18.36 | 1.017x | 24.18 | 1.32x |
| 2048 | 16 | 32768 | clustered register | 4.99 | 4.98 | 1.002x | 9.10 |
1.83x |
| 2048 | 16 | 131072 | slab | 8.31 | 7.94 | 1.047x | 13.13 | 1.65x |
| 2048 | 148 | 32768 | slab | 11.68 | 11.49 | 1.017x | 9.19 | 0.80x |
| 2048 | 148 | 131072 | slab | 14.80 | 14.41 | 1.027x | 31.46 | 2.18x |
| 2048 | 256 | 32768 | slab | 13.53 | 13.26 | 1.020x | 12.55 | 0.95x |
| 2048 | 256 | 131072 | slab | 16.58 | 16.41 | 1.010x | 33.15 | 2.02x |

Every slab, split and cluster cell gains 0.1-0.45 us per launch (1-4%)
on B200 and 0.2-0.4 us on Rubin; no cell is slower.

#### Tests

Existing suites (hint-free, family parity, paged, CUDA-graph replay,
split) cover both families.

</details>

<details>
<summary>Part 6: staged coalesced epilogue for the clustered family's
paged output (prose; B200, B300 and Rubin tables incl. SGLang column;
tests)</summary>

### Part 6: staged coalesced epilogue for the clustered family's paged
output (commit `perf(topk_varlen): staged coalesced epilogue for the
gvr_2 clustered family's paged output`)

The clustered register family still emitted its paged output the way the
register family did before Part 2: every winner as one scattered global
store with the page-table transform inline (one L1 store sector per
index, the table read on the emit path), 0.3-0.8 us over the unpaged
kernel on the clustered cells.

- `stage_out` for `GvrRegClusKernel`: every rank writes its winners into
a k-word staging region at the tail of rank 0's dynamic window (DSMEM
stores through mapa; rank 0 clears it before the first cluster
rendezvous), and after the final rendezvous rank 0 alone writes the row
in one coalesced pass, applying the page transform there. The staged
variant reads the page table from global in that epilogue instead of
staging the table row in the prologue: concentrated at the tail the
reads hit L2 and the prologue stage is pure overhead (0.1-0.3 us better
than the smem row on every clustered cell).
- Host rule, measured on B200: paged output only, K <= 1024 at every row
count and K = 2048 from 16 rows up. K = 2048 below 16 rows keeps the
scattered emit (the two-pass epilogue over 2048 words costs more than it
saves, -0.3 us at 1 x 32K); the unpaged output keeps it too (funnelling
every rank's winners through rank 0 lost 0.3-0.8 us at 16-64 rows
without a transform to amortise). Compile key and persist name gain
`stage_out`; launch smem grows by 4k when staged.

#### Perf

Same process, before (scattered emit, smem-staged table row) vs this
commit, random lengths in (K, N], fp32, page size 64, CUDA graph, 3
interleaved reps, min; same node, one job. Only clustered cells are
shown; K = 2048 rows below 16 are the unchanged control.

**B200 (computelab), 148 SMs** (us, paged output, clustered register
family; `before` =…

### [19faf79](https://github.com/flashinfer-ai/flashinfer/commit/19faf79b70cdbe2127530784016a73c9e015e0f1)

- **作者**: Yang Xu
- **时间**: 2026-10-16T16:14:14Z
- **提交信息**: fix(autotuner): coordinate cache hits before distributed profiling (#6185)

Coordinate profile-cache hit decisions before distributed autotuning. If any
rank misses, all ranks invalidate old candidates and profile together, avoiding
collective mismatches after partial caches or concurrent publication.

Coordinate nested tactic-ranking caches and clear ephemeral shortlists during
managed reload. Serving remains collective-free; frameworks must still provide
matching operation, profile, and candidate order.

Validation: current-head H100 autotuner scope (351 passed, 18 skipped), six AOT
build/import jobs, and the two-B200 cache-recovery/replay reproducer. Reviewed
and approved by Albert Cheng. AI-assisted implementation and validation.

Co-authored-by: Codex <noreply@openai.com>
Signed-off-by: Yang Xu <yanxu@nvidia.com>

### [38e6b89](https://github.com/flashinfer-ai/flashinfer/commit/38e6b8944fe8b6497d793ef21fbaadd797ea39d8)

- **作者**: Cindy Zhang
- **时间**: 2026-10-16T10:08:39Z
- **提交信息**: fix(ci): handle CuTe-DSL JIT cache misses (#6492)

MissingJITCacheError reporting assumed every spec exposed NVCC-only
fields. Preserve the existing NVCC report and use the common artifact
path for other JIT backends so CuTe-DSL cache misses are skipped and
reported as intended.\n\nAdd a GPU-independent regression test that
drives the pytest hook with a JitSpecCuteDsl.

<!-- .github/pull_request_template.md -->

## 📌 Description

Handle `MissingJITCacheError` reports for `JitSpecCuteDsl` without
assuming NVCC-only fields such as `sources` and `aot_path`. NVCC reports
retain their existing metadata, while other JIT backends report their
common artifact path.
Add a GPU-independent regression test that drives the pytest hook with a
`JitSpecCuteDsl` cache miss and verifies that the test is skipped and
recorded instead of failing with a secondary `AttributeError`.

## 🔍 Related Issues

Fix https://github.com/flashinfer-ai/flashinfer/issues/6490

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
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes
The primary CuTe-DSL cache miss is expected while CuTe-DSL artifacts are
not integrated with `flashinfer-jit-cache` AOT packaging. This PR fixes
only the secondary reporting failure; it does not change cache coverage
or kernel behavior.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Missing JIT cache reports now show information appropriate to the
artifact being checked, improving clarity across build configurations.
* **Tests**
* Added coverage for missing CuTe DSL JIT cache reporting, including the
resulting test skip and cache record.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [840fb69](https://github.com/flashinfer-ai/flashinfer/commit/840fb69656b336da91f0a8131c2e61b907bbc2cf)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-10-16T09:57:51Z
- **提交信息**: [Feat] Support Muse-Spark-Open with fused normalization and TP/EP MoE optimizations (#6544)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add fused normalization and TP/EP MoE kernels for Muse Spark that
combine normalization, gating, residual operations, and communication to
reduce intermediate tensors, kernel launches, and data movement.

- **Gated residual RMSNorm fusion:** Fuse RMSNorm, gating, and residual
combination into one kernel while preserving the FP32 residual stream.
- **RMSNorm + sigmoid gate fusion:** Fuse per-head RMSNorm and sigmoid
gating with runtime-token kernel reuse, full-tile specialization, and
PDL support.
- **Gated residual dual norm fusion:** Fuse branch normalization, gated
residual combination, and next-layer RMSNorm with optional input scales,
scalar gates, FP32 router output, and PDL support.
- **TP MoE finalize fusion:** Fuse TP reduction, per-expert RMSNorm, and
weighted expert accumulation directly from permuted GEMM2 rows, with
token-owner paths for medium and large token counts.
- **All-gather + gated residual dual norm fusion:** Fuse column
all-gather with gated residual dual normalization.
- **All-gather + RMSNorm + NVFP4 quantization fusion:** Fuse column
all-gather, RMSNorm, and NVFP4 quantization.
- **MoE finalize + RMSNorm + all-reduce fusion:** Fuse per-expert
RMSNorm into the all-reduce/finalize path while skipping normalization
for nonlocal experts.

The fused normalization and TP MoE finalize paths support SM100, SM103,
and SM107.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> `git diff --check` and pre-commit passed on all 30 changed files,
including mypy and Ruff.

## 🧪 Tests

- Pre-commit on all 30 files changed against upstream `main` at
`7b2438ec309a9b1b244dbef8a1260073e59a913a`: passed, including mypy and
Ruff.

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).


## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

The LL collective pairs an early relaxed cluster arrival with a wait
before the first peer shared-memory store; existing post-store barriers
remain in place, and the startup synchronization is enabled only when
normalized output is requested.

AI assistance was used for integration, rebasing, and validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added fused normalization operations for gated residual updates,
sequential RMSNorm, and RMSNorm with sigmoid gating.
* Added tensor-parallel operations that combine all-gather with gated
residual normalization, RMSNorm and NVFP4 quantization, or MoE
finalization with RMSNorm and all-reduce.
  * Added tensor-parallel MoE finalization with per-expert RMSNorm.
* Added support checks and trace coverage for the new normalization and
communication operations.
* **Bug Fixes**
  * MoE finalization treats invalid row indices as zero-valued inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: jiahanc <173873397+jiahanc@users.noreply.github.com>
Signed-off-by: Cyrus Chang <jiahanc@nvidia.com>
Signed-off-by: Jiahan Chang (Cyrus) <173873397+jiahanc@users.noreply.github.com>
Signed-off-by: Cyrus Chang <173873397+jiahanc@users.noreply.github.com>
Co-authored-by: Duncan Moss <6038874+djmmoss@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Duncan Moss <djm.moss@gmail.com>

### [41f2ba1](https://github.com/flashinfer-ai/flashinfer/commit/41f2ba10503fd324fc253d8a8cabc9eb240a9c14)

- **作者**: eigen
- **时间**: 2026-10-16T08:29:55Z
- **提交信息**: feat(cake_gdn): host-free non-CP prefill launch -- optional cu_seqlens_cpu, no device-to-host sync, launch ABI v2 (#6519)

## 📌 Description

### Motivation

`chunk_gated_delta_rule(..., backend="cake_gdn")` without CP resolved
its per-sequence lengths on the
host: `_run_cake_gdn_prefill -> _cake_gdn_prefill_seq_lens ->
_cake_gdn_host_ints` ran
`cu_seqlens.detach().cpu().tolist()` (one full device-to-host
synchronization) and cached the result
under an identity key `(device, data_ptr, version or None, numel)` that
also required the weak-referenced
tensor to be the *same object*. A second identity-keyed cache
(`_cake_gdn_i32`) held int32 copies of
int64 metadata. Consequences:

- vLLM pays one synchronization per prefill step (the engine passes a
fresh int32
`prefill_query_start_loc` every step; 36 layers share one resolution),
and CUDA Graph capture needed one
eager pre-resolution or raised `CakeGDNUnsupportedError("... requires
one eager cu_seqlens resolution
  before CUDA Graph capture")`.
- The default SM100 GDN prefill (`backend="auto"`, CuTe-DSL
`chunk_gated_delta_rule_sm100`) has no host
synchronization, so under concurrency the Cake route lost step overlap.
In an internal vLLM measurement
(two B300 node pairs, concurrency 32), median TTFT was +14.3 % / +9.7 %
versus the default route, while
single-stream TTFT was 4-5 % *lower* (the kernel itself is not slower).
A concurrency-32 TTFT re-test with this PR (vLLM, Qwen3.5-35B-A3B, 1x
B300, baseline vs Cake route on the same node) does not gate this PR;
its result is appended as a PR comment.
- The identity-keyed host-int cache could return stale offsets when an
engine rewrites a persistent
`cu_seqlens` buffer in place (inference-mode tensors carry no version
counter).

### What changed

**Public API** (`flashinfer/gdn_prefill.py`)

- `chunk_gated_delta_rule(..., *, cu_seqlens_cpu: Optional[Sequence[int]
| torch.Tensor] = None)`:
keyword-only host copy of `cu_seqlens`, either a one-dimensional
int32/int64 CPU tensor or a sequence of
Python ints of length `num_seqs + 1` with the same values (vLLM
`query_start_loc_cpu`, the prefix
sums of SGLang `extend_seq_lens_cpu`). Only `backend="cake_gdn"` without
CP uses it; every other route
ignores it. When it is passed, the route checks the offsets on the host
before any launch (non-decreasing,
first `0`, last `total_seq_len`; a `max_seqlen` smaller than the exact
maximum is rejected; a CUDA
tensor is refused, not copied). It then uses the exact longest sequence
as the bound for variant selection
  and the persistent grid, and checks the checkpoint count exactly.
- Without it the route still reads nothing back from the device:
`num_seqs` and the token count are
shapes, the bound is the existing `max_seqlen` hint (else
`total_seq_len`), and the kernel resolves
  `cu_seqlens` on the device at every launch.
- Removed: `_cake_gdn_host_ints`, `_CAKE_GDN_HOST_INTS`,
`_cake_gdn_prefill_seq_lens`, `_cake_gdn_i32`,
`_CAKE_GDN_I32_COPIES`, the capture-time "requires one eager ...
resolution" error and the
`checkpoint_cu_starts` content verification (the public docstring
already declared it a caller
precondition; the kernel guards it on the device). Int32 `cu_seqlens` /
`state_indices` /
`checkpoint_cu_starts` reach the kernel as is; int64 metadata is cast on
the caller's stream at every
call (`_cake_gdn_prefill_i32`, no cache). Nothing is cached by tensor
identity.
- Routes without `g` / `beta`: the FP32 unit gates that the selected
variant reads now come from a bounded
per-device cache keyed by `[tokens, heads]` (8 entries,
`_cake_gdn_unit_gates`) instead of a fresh
`torch.ones` per call. A tensor first built under CUDA Graph capture is
handed to the capture uncached.
  A warm call allocates and frees no device memory (new GPU test

`test_public_cake_gdn_prefill_repeated_calls_allocate_no_device_memory`).
- Grid: one host-known rule `_cake_gdn_prefill_grid_x(total_tiles,
sm_count, dvsplit, bound_tokens)`,
mirrored byte-for-byte from the Cake program's
`_select_persistent_grid_ctas`.
Rule: DV-split or `total_tiles <= 128` -> `min(sm_count, total_tiles)`;
otherwise `G = argmin_{G in {128, sm_count}} ceil(total_tiles / G)`,
ties kept at 128. This is rule v3, adopted after the two-architecture
paired A/B because a smaller per-CTA tile quantum wins (e.g. 384 tiles
on 212 SMs -> 212). The caller validates the bound, but the bound does
not change the grid.
- Docstrings (`backend`, `max_seqlen`, `cu_seqlens_cpu`) and
`docs/api/gdn_prefill.rst` document the
contract; `csrc/gdn/cake/README.md` gains "Non-CP prefill: host-free
launch".

**Variant selection** (`flashinfer/jit/cake_gdn.py`)

- `select_cake_gdn_prefill_variant` loses the `seq_lens` keyword;
`max_seq_len` is an upper bound
(exact with `cu_seqlens_cpu`, else the `max_seqlen` hint, else
`total_seq_len`). `single_chunk` keeps
its rule on that bound (<= 64 tokens, no initial/final state, no
checkpoints). The SGLang TP4 BF16
indexed checkpoint route is admitted on structural conditions alone
(dtypes, heads (4, 4, 8),
  interval 64, indexed state, DV-split).
- Twin selection follows the manifest. The `_gatestream_full` twin is
selected only where the manifest
ships it for the key; every other key runs its base record, and a
missing base record still fails
closed. The twins were exported only for the geometries that the
representative rows reach. The
FP32-state TP geometries added in #6478 keep their base body, so
requesting the twin unconditionally
would make their many-short-sequence full-DV calls fail closed. A new
test pins the fallback.
`cake_gdn_prefill_geometries` passes the three twin flags explicitly
(`False`), so it enumerates the
  base templates' contract geometries.

**Exported kernels** (`csrc/gdn/cake/`, launch ABI v2)

- Every shipped non-CP prefill variant is re-exported from Cake with one
new i32 scalar `total_tokens`
right after `num_seqs` (kernel formals and TVM-FFI shim entry; the shim
checks
`total_tokens == Q.size(0)` and `0 < grid_x <= total_tiles`). Per work
tile, the kernel clamps
`begin = min(max(cu_seqlens[b], 0), total_tokens)` and `end =
min(max(cu_seqlens[b+1], begin), total_tokens)`.
Offsets past the token count are therefore clamped, and a non-monotonic
pair becomes an empty
sequence. That case is a documented no-op (output rows untouched, state
slot keeps the initial state),
  never an out-of-bounds access and never a trap.
- Tile schedule: every exported body uses the strided schedule (tile `t`
-> CTA `t mod grid_x`, natural order). The wave schedule (single
remainder wave, `G < T <= 2G`) stays an opt-in Cake-side knob that is
not exported (every exported body uses the strided schedule): it helps
skewed batches (8-12 %) but costs 1-4 % on the uniform and short rows
that dominate the representative set.
- Manifest: 190 -> 227 variants, 0 records removed.
- Prefill goes from 106 to 143 records under ABI v2. All 106 shipped
records are re-delivered. They include the 11 FP32-state TP records from
#6478: 4 are reached by the R3 engine rows and the other 7 by 7 new
export coverage rows.
  - 37 prefill records are new:
- 27 sm_100a `state_inp_late` twins, 9 each over the `dvsplit`,
`dvsplit_initial` and `dvsplit_initial_bf16state` bases.
    - 8 `_gatestream_full` (5 bf16-state, 3 fp32-state).
    - 1 `fullgrid_vhold`.
    - 1 sm_103a `role_rebalanced`.
- No shipped prefill record is retired. The runtime-head plain stateful
fp16 record
`prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_f16io_2897cee67e22`
is reached by the ungated route (`g` or `beta` absent) and re-delivered
under ABI v2.
- Decode: 84/84 records are byte-identical to `main`, and no decode file
changed.

**Tests** (`tests/gdn/`)

- New CPU-only `tests/gdn/test_cake_gdn_prefill.py`: host-offset
validation (tensor and int-sequence
forms, fail-closed cases), grid rule == launch contract (table + bounds
sweep, the only grid text in
the route), int32 pass-through / int64 per-call cast, no cache symbols,
public forwarding of
`cu_seqlens_cpu` and the bound, keyword-only signature, resolver without
device-derived lengths.
- `tests/gdn/test_cake_gdn_prefill_gpu.py`:
- `cu_seqlens_cpu` is rejected on the host before any launch, and every
host-copy form matches the device metadata.
- Zero-sync proof: 36 calls under
`torch.cuda.set_sync_debug_mode("error")` plus a profiler window with a
positive control; with and without the host copy, int32 and int64.
- Cold CUDA Graph capture after only the one-time variant load; in-place
rewrite + replay vs reference and eager.
- Chunked state carry k in {2, 4, 8} (fp32 and bf16 state, one sequence
and an unequal batch).
  - Malformed device metadata degrades to the clamped no-op.
- int64 metadata matches int32 bitwise, including after in-place
rewrites and graph replay.
- `tests/gdn/test_cake_gdn_decode.py`: resolver tests without
`seq_lens`, bound-only TP4 resolution,
`single_chunk` bound test. The `fake_variant_for` helper now takes
`arch`. The sm_107a twin-rule probe
now uses H16/HV32, because the FP32-state TP record it used to probe
ships only for sm_100a / sm_103a.
`tests/gdn/test_cake_gdn_decode_gpu.py`: raw prefill launch passes
`total_tokens`.


### Behaviour and compatibility notes

- No change for `backend="auto"`, `"flashinfer"`, `"cudnn"` and
`backend="cake_gdn", use_cp=True`.
- `cu_seqlens_cpu` is optional; existing `backend="cake_gdn"` callers
keep working and simply stop
synchronizing. CUDA Graph capture no longer needs an eager warm-up call
for the same metadata; the
one-time `nvcc` compile and TVM-FFI load of a kernel variant is the only
eager step.
- **Stateless single-chunk batches now need the bound.** Previously, a
stateless batch (no initial/final
state, no checkpoints) whose sequences were all <= 64 tokens resolved
the single-chunk kernel from the
  host-read lengths. That decision now follows the bound:
- With `max_seqlen=64` or `cu_seqlens_cpu`, it resolves exactly as
before.
- With neither, a packed length above 64 tokens resolves the general
stateless specialization. The
manifest ships that specialization only where listed. For the one
single-chunk head split
(H4/HV8, BF16 I/O, FP32 state) it is unshipped, and the call fails
closed with
`CakeGDNUnsupportedError: no exact frozen Cake GDN variant for
flashinfer.cake_gdn.generated.prefill:flashinfer_blackwell_gdn_prefill_dvsplit
with {...}`.

Pass `max_seqlen` or `cu_seqlens_cpu` (pinned by
`test_prefill_resolver_single_chunk_follows_the_host_bound`).
- `checkpoint_cu_starts` contents are no longer verified on the host
(they never could be without the
synchronization this PR removes); the kernel clamps them like
`cu_seqlens`. The exact
  `state_checkpoints.shape[0]` check runs only with `cu_seqlens_cpu`.
- Malformed device metadata (non-monotonic, last offset != total tokens)
is a documented no-op for the
affected sequence instead of an out-of-bounds write; with
`cu_seqlens_cpu` the host raises before
  the launch.

### Measurements

Protocol: same-process paired CUPTI timing (`bench_gpu_time`, cold L2,
20 warm-up launches, 101
samples, symmetric ABAB order with 4 measurements per arm), Cake tool
`tools/gdn-prefill-paired-ab`.

- **Denominator**: the faster of FlashInfer `backend="auto"` exact /
prepared on the base. The baseline
kernel actually dispatched is recorded per row:
`GatedDeltaNetChunkedKernel` of the CuTe-DSL
`chunk_gated_delta_rule_sm100` path (CUPTI activity
`kernel_cutlass_kernel_flashinfergdn_kernelsblackwellgated_delta_net_chunkedGatedDeltaNetChunkedKernel_object_at__TiledMMA_...`)
on all 82 rows of both architectures. The `exact` arm was the faster
denominator on all but one row
  per architecture.
- **Incumbent**: `backend="cake_gdn"` on the base (previous kernels +
previous host path).
- **Row sets**:
  - R1 = 16 frozen perf rows (fp16 I/O, fp32 state).
  - R2 = 30 Qwen3.5 bf16-I/O / bf16-state rows.
- R3 = 36 engine chunked-prefill rows (bf16 I/O, fp32 or bf16 state,
8x1024 / unequal 8 / 32x256 / 2x8192 / 8192+7x1024 / 16x512 for
H16/HV32, H8/HV16, H4/HV8).
- **Error**: the max-abs error of every arm against the fp32 reference
is recorded ("error parity" = Cake error / FI auto error).

The base for this revision is `fb83b0ee9d41df4e24fb0b2ce1e671accadcef85`
(`main` after #6478).

- **Re-run on `fb83b0ee`**: export/source parity, the strict
`backend="auto"` gate and host overhead.
- **Measured on the previous pin, before the rebase**: the two 82-row
paired tables, the zero-sync,
chunked-carry and numerics results, and the sanitizer runs. The Cake
kernel sources have not changed
  since then.

**B200 (sm_100a)**: one B200 node (exclusive lease), container
`sglang-2607` (torch 2.13.0a0+nv26.07, CUDA 13.x), Cake tree
`m36-c4718a5b` (kernel byte-identical to the delivered head), measured
before the rebase

| rows | n | geomean vs FI auto | min vs FI auto (row) | rows in (1.00,
1.02] | geomean vs incumbent | min vs incumbent (row) | error parity max
|
|---|---|---|---|---|---|---|---|
| R1 | 16 | 1.1668 | 1.0496 (`perf_hq16_hv16_8192x8`) | 0 | 1.0223 |
1.0105 (`perf_hq16_hv16_1024_7168`) | 1.000 |
| R2 | 30 | 1.1319 | 1.0395
(`prefill_bf16state_397b_tp2_hq8_hv32_4x2048`) | 0 | 1.0586 | 1.0123
(`prefill_bf16state_397b_tp8_hq2_hv8_16x512`) | 1.000 |
| R3 | 36 | 1.1731 | 1.0146
(`engine_chunked_h8_hv16_bf16state_1x8192_7x1024`) | 2 | 1.0646 (n = 24;
the 12 fp32-state H16/HV32 rows have no shipped incumbent variant) |
1.0083 (`engine_chunked_h16_hv32_fp32state_1x8192_7x1024`) | 1.000 |
| all | 82 | 1.1567 | 1.0146
(`engine_chunked_h8_hv16_bf16state_1x8192_7x1024`) | 2 | 1.0522 (n = 70)
| 1.0083 | 1.000 |

**GB300 (sm_103a)**: one GB300 node (exclusive lease), container
`sglang-2607` (torch 2.13.0a0+nv26.07, CUDA 13.x), Cake tree
`m36-c4718a5b` (kernel byte-identical to the delivered head), measured
before the rebase

| rows | n | geomean vs FI auto | min vs FI auto (row) | rows in (1.00,
1.02] | geomean vs incumbent | min vs incumbent (row) | error parity max
|
|---|---|---|---|---|---|---|---|
| R1 | 16 | 1.1916 | 1.0571 (`perf_hq16_hv16_8192x8`) | 0 | 1.0447 |
1.0186 (`perf_hq16_hv16_8192x8`) | 1.000 |
| R2 | 30 | 1.1256 | 1.0442
(`prefill_bf16state_397b_tp2_hq8_hv32_4x2048`) | 0 | 1.0505 | 1.0050
(`prefill_bf16state_35b_tp4_hq4_hv8_16x512`) | 1.000 |
| R3 | 36 | 1.1780 | 1.0214
(`engine_chunked_h8_hv16_bf16state_1x8192_7x1024`) | 0 | 1.0684 (n = 24)
| 1.0056 (`engine_chunked_h4_hv8_bf16state_16x512`) | 1.000 |
| all | 82 | 1.1612 | 1.0214
(`engine_chunked_h8_hv16_bf16state_1x8192_7x1024`) | 0 | 1.0553 (n = 70)
| 1.0050 | 1.000 |

Rows in the watch band (1.00, 1.02] were re-measured twice in another
time window:

- B200: `engine_chunked_h16_hv32_bf16state_1x8192_7x1024` 1.0150 /
1.0150 / 1.0154 and `engine_chunked_h8_hv16_bf16state_1x8192_7x1024`
1.0146 / 1.0148 / 1.0154.
- GB300: none.

The B200 row `perf_hq16_hv16_8192x32` (±5 % run-to-run noise) measured
1.0136 / 0.9982 / 1.0205 vs the incumbent on the final kernel (gate >=
0.98).
Rows below 1.00 after the lever rounds: none.

**Strict gate vs the CuTe-DSL `backend="auto"` kernel, re-run on
`fb83b0ee`** (66 rows, delivered kernels, same-process paired ABAB
timing in the export runs):

- B200: min 1.0134, geomean 1.1555, max 1.5559, 0 rows <= 1.00. Three
rows fall in (1.00, 1.02]:
`engine_chunked_h8_hv16_bf16state_1x8192_7x1024` 1.0134,
`engine_chunked_h16_hv32_bf16state_uneq8_4096to32` 1.0173 and
`engine_chunked_h8_hv16_bf16state_uneq8_4096to32` 1.0173. Each was
measured in three independent ABAB groups in early and late windows, all
> 1.00 (1.0125-1.0189).
- GB300: min 1.0306 (`engine_chunked_h8_hv16_bf16state_1x8192_7x1024`),
geomean 1.1618, max 1.6210, 0 rows <= 1.00, 0 rows in (1.00, 1.02].

**Exported vs source kernel paired ratio on `fb83b0ee`** (export gate >=
0.97; 248 shapes per architecture = 82 perf + 88 coverage + 78 decode;
the coverage rows grew from 81 to 88 to reach the 7 #6478 records that
no perf or engine row reaches). All 248 rows are correct on both
architectures.

- GB300: geomean 1.0010, min 0.9762; 248/248 rows >= 0.97.
- B200: geomean 1.00003, min 0.9667; 247/248 rows >= 0.97.

The only row below the gate on either architecture is the 8-µs B200
decode row `bf16_t1_397b_tp2_h8_hv32_b16`. On the full export run it
read 0.9667 (source 8.352 µs / export 8.640 µs), so the B200 export gate
reports it as fail-closed. On an independent build of the same bytes it
reads 0.9813 (8.384 / 8.544 µs). The decode records are byte-identical
to `main` (84/84), so this is not a kernel change. The same row reads
0.9808 on GB300, and its ratio vs the FlashInfer decode baseline is
1.078 (full run) / 1.0861 (independent build).

The three short coverage rows that read below the gate on the previous
export build now pass:

- `export_cov_dvsplit_single_chunk_hq4_hv8_s_4x64`: 0.9779 (GB300) /
1.0000 (B200).
- `export_cov_dvsplit_f16io_hq1_hv2_f_4x256`: 0.9899 (GB300).

**Host overhead on `fb83b0ee`** (CPU time per call, median of 36 calls,
same process; acceptance: <= incumbent cache hit + 10 µs):

| | incumbent cache hit (miss) | this PR, no `cu_seqlens_cpu` |
`cu_seqlens_cpu` CPU tensor | `cu_seqlens_cpu` int list | fresh host
tensor per call | gate |
|---|---|---|---|---|---|---|
| GB300 | 52.6 µs (125.6 µs) | 46.8 µs | 53.4 µs | 53.6 µs | 57.1 µs |
<= 62.6 µs |
| B200 | 43.7 µs (121.5 µs) | 38.9 µs | 48.7 µs | 48.6 µs | 45.1 µs | <=
53.7 µs |

Every form passes on both architectures.

- Without `cu_seqlens_cpu`, a call costs 5.8 µs (GB300) / 4.8 µs (B200)
less than the incumbent's cache hit.
- With it, a call costs at most 4.5 µs / 5.0 µs more.
- The incumbent's cache miss is paid once per step when the engine
passes fresh metadata, and it includes the device-to-host
synchronization that this PR removes.

**Zero-sync proof**: 36 consecutive `backend="cake_gdn"` calls under
`torch.cuda.set_sync_debug_mode("error")` raise nothing. The profiler
window shows 0 `cudaMemcpy*`
D2H and 0 `cudaStreamSynchronize` / `cudaDeviceSynchronize` /
`cudaEventSynchronize`, with and
without `cu_seqlens_cpu`, int32 and int64. Both architectures pass:

- Cake-side no-synchronization assertion check (the generator's launch
path under a sync-error mode): 2/2 per architecture.
- FI
`test_public_cake_gdn_prefill_performs_no_device_to_host_sync[{i32,i64}-{device_metadata,cu_seqlens_cpu}]`:
4/4 passed per architecture, on both the exported tree and the previous
PR-head tree.

The test is also part of the `tests/gdn` run below.

**Chunked state carry** (k in {2, 4, 8} calls with `output_state ->
initial_state`, 36 R3 rows): all
results are within tolerance of the single call and of the reference.
36/36 rows are correct at every k on
both architectures. The max chunked-vs-single difference is 6.1e-05 for
the output and 9.8e-04 for the
final state (k = 8), identical for the Cake route and the FI `auto`
kernel.

**Numerics**: the max-abs error against the fp32 reference is <= 1.05 x
the FI `auto` kernel's error on every
row. It is identical to the error of the incumbent `cake_gdn` kernel and
of the FI `auto` kernel on every
row (error parity 1.000 on both architectures). The host-free launch
does not touch the arithmetic. Every
adopted lever (register-sliced DV-split epilogue, earlier
`state_inp_ready` release with the sm_100a late
twin, the `_gatestream_full` twin, grid rule v3) was measured
bit-identical to its off control.

### Documentation

- `docs/api/gdn_prefill.rst`: new section "Cake GDN non-CP backend:
host-free launch".
- `csrc/gdn/cake/README.md`: "Non-CP prefill: host-free launch" contract
section.
- Docstrings of `chunk_gated_delta_rule` (`backend`, `max_seqlen`,
`cu_seqlens_cpu`),
  `select_cake_gdn_prefill_variant`, `_run_cake_gdn_prefill`.

## 🔍 Related Issues

- Cake kernel tracker: #4254 (registration comment:
https://github.com/flashinfer-ai/flashinfer/issues/4254).
- Base: #6478 (FP32-state TP records). This PR re-delivers its 11
records under launch ABI v2.
- `backend="auto"` promotion of the Cake route is tracked separately and
is out of scope here.
- Engine follow-ups (comments only, no engine code in this PR):
- vLLM can pass `cu_seqlens_cpu=query_start_loc_cpu` /
`prefill_query_start_loc_cpu`.
  - SGLang can pass the prefix sums of `extend_seq_lens_cpu`.
- No vLLM or SGLang PR comment has been posted yet: the vLLM route is a
branch without an open PR, and no SGLang route PR exists. Both engines
already hold the host prefix sums that this parameter accepts.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.
(`pre-commit run --from-ref fb83b0ee9d41df4e24fb0b2ce1e671accadcef85
--to-ref HEAD` on this head's tree: all hooks passed (mypy, ruff check,
ruff format and 8 more Passed; 5 hooks skipped for lack of matching
files))

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing.

Results below are for `tests/gdn` on the PR-head tree
`47fac131a8a748672ec6acaa61bb61d21373cda4` (base `fb83b0ee` + this PR),
one run per architecture. The run includes:

- the new CPU-only `test_cake_gdn_prefill.py`
- `test_cake_gdn_prefill_gpu.py`
- `test_cake_gdn_decode.py`, including the manifest consistency tests
`test_manifest_lists_loadable_source_only_variants` and
`test_compile_cubin_adds_manifest_header_include_paths`
- `test_cake_gdn_decode_gpu.py`
- `test_prefill_state_indices.py`
- `test_prefill_delta_rule.py`
- `test_prefill_auto_backend.py`

| architecture | `tests/gdn` |
|---|---|
| B200 (sm_100a) | 4107 tests: 3240 passed / 867 skipped / 0 failed
(1009 s) |
| GB300 (sm_103a) | 4107 tests: 3240 passed / 867 skipped / 0 failed
(896 s) |

compute-sanitizer `synccheck` + `memcheck` (`ERROR SUMMARY: 0 errors`)
covered at least one DV-split row,
one full-DV row and one unequal-length R3 row per architecture. These
runs were measured before the rebase; the kernel sources are unchanged
since.

- GB300 (sanitizer 13.4.92):
- 12 base rows (DV-split, full-DV, `uneq8` unequal-length R3,
`_gatestream_full` twins): `ERROR SUMMARY: 0 errors` x 24.
  - 4 multi-tile rows (stateless x2, initial/no-final x2): 0 errors x 8.
- B200: the same 12 + 4 rows, 0 errors x 24 / x 8.

Unchanged variants: every `csrc/gdn/cake` file that is not re-exported
under ABI v2 is byte-identical to
`main` (`fb83b0ee`). The decode records are byte-identical (84/84), and
no decode file changed. Keys without a
shipped twin resolve to their base record, as on `main`.

## Reviewer Notes

- Base: `fb83b0ee9d41df4e24fb0b2ce1e671accadcef85` (`main` after #6478).
- The Cake kernel sources are generated; the review surface is
`flashinfer/gdn_prefill.py`,
`flashinfer/jit/cake_gdn.py`, the tests and the docs.
`csrc/gdn/cake/manifest.json` and the
re-exported bodies/shims come from the Cake exporter
(`exports/gdn/export.py`, pinned to `fb83b0ee`).
- CI: `/bot run`
- Targeted: `@flashinfer-bot run tests/gdn/test_cake_gdn_prefill.py
tests/gdn/test_cake_gdn_prefill_gpu.py tests/gdn/test_cake_gdn_decode.py
tests/gdn/test_cake_gdn_decode_gpu.py
tests/gdn/test_prefill_state_indices.py
tests/gdn/test_prefill_delta_rule.py
tests/gdn/test_prefill_auto_backend.py`
- Registered in the Cake kernel tracker #4254
(https://github.com/flashinfer-ai/flashinfer/issues/4254).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6eb3221](https://github.com/flashinfer-ai/flashinfer/commit/6eb3221c969fc681f64bf5b04a34e534abd427e9)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-16T07:58:11Z
- **提交信息**: perf(norm): SM107 launch config for add_rmsnorm_fp4quant (#6133)

<!-- .github/pull_request_template.md -->

## 📌 Description

On SM107, `add_rmsnorm_fp4quant` (CuTe-DSL) does not get the measured
SM100/SM103 config. It falls back to the generic launch heuristic in
`_compute_launch_config`. This PR adds an SM107 branch,
`_compute_sm107_launch_config`, next to the SM100/SM103 one.

**Why.** Every thread stages `num_vec_blocks` 16-byte vectors of each of
input, residual and weight with `cp.async` before the first
`cp_async_wait_group`. For H >= 1024 the generic heuristic gives 4-8
vectors per tensor, so each thread has 12-24 copies in flight. On SM107
that config keeps the kernel far below memory bandwidth at every M
measured. It is slower than the same kernel on SM103 and slower than the
unfused path.

**What.** Cap staging at two vectors per tensor:
- Widen `threads_per_row` to `ceil(H / (2 * vec_size))`, rounded up to a
whole warp and capped at 1024.
- Use one row per CTA when `threads_per_row` >= 128. Smaller rows still
pack to 128 threads per CTA.
- When the generic config already has <= 2 vectors per thread (H <=
512), keep it unchanged.

This was the fastest config measured on SM107 for H in 1024..16384 and M
in 1..16384. Two rows per CTA, or one vector per tensor, were slower.
The SM100/SM103-tuned config (`256, 256` at H >= 8192) was no better
than the generic fallback on SM107, so routing SM107 through the
existing tuned path would not help.

SM100/SM103 and all other architectures are unchanged.

## 📊 Speedup

Speedup multipliers only. Baseline (`main`) and this PR ran in the same
job on the same node, interleaved per case, using CUDA graphs with
cold-L2 rotating buffers. Each value is the best of 3 passes. The shapes
are every `add_rmsnorm_fp4quant` line in the benchmark testlists
(`--backends cute-dsl`).

| shape (BF16 in) | SM107: PR vs `main` | SM107 vs GB300, before | SM107
vs GB300, after |
|---|---:|---:|---:|
| NVFP4 M2048 H4096 | 2.92x | 0.44x | 1.31x |
| NVFP4 M16384 H4096 | 4.36x | 0.32x | 1.43x |
| NVFP4 M2048 H8192 | 3.23x | 0.39x | 1.31x |
| NVFP4 M16384 H8192 | 4.16x | 0.32x | 1.34x |
| MXFP4 M2048 H4096 | 2.80x | 0.50x | 1.40x |
| MXFP4 M16384 H4096 | 3.96x | 0.37x | 1.50x |
| MXFP4 M2048 H8192 | 2.97x | 0.43x | 1.32x |
| MXFP4 M16384 H8192 | 3.66x | 0.36x | 1.36x |
| NVFP4 M2048 H4096, global scale + swizzled SF | 3.07x | — | — |
| NVFP4 M16384 H4096, global scale + swizzled SF | 3.79x | — | — |
| NVFP4 M2048 H4096, global scale + both SF layouts | 3.07x | — | — |
| NVFP4 M32 H4096 | 1.56x | — | — |
| NVFP4 M32 H4096, both SF layouts | 1.54x | — | — |
| NVFP4 M32 H4096, global scale + both SF layouts | 1.74x | — | — |
| NVFP4 M32 H4096, global scale | 1.74x | — | — |
| NVFP4 M32 H4096, swizzled SF | 1.55x | — | — |
| NVFP4 M32 H128 (3D, 32 heads) | 1.00x | — | — |
| NVFP4 M64 H8192 | 1.37x | — | — |
| NVFP4 M64 H8192, both SF layouts | 1.40x | — | — |
| MXFP4 M32 H4096 | 1.60x | — | — |
| MXFP4 M32 H4096, both SF layouts | 1.61x | — | — |

- The two "SM107 vs GB300" columns compare the chips running the same
code: both on `main`, then both on this PR.
  - These columns are given for the 8 shapes benchmarked on both.
- The GB300 code path is unchanged by this PR, because the new branch is
taken only on SM107.
- No shape regressed on SM107.
- NVFP4 M32 H128 (3D, 32 heads) is the control. H ≤ 512 keeps the
generic config by design.

## 🔍 Related Issues

Internal: IKL-536.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Tests run on GR100:

| suite | result |
|---|---|
| `tests/norm/test_add_rmsnorm_fp4_quant_cute_dsl.py` (full file) | 1225
passed, both with and without this change |

The change only affects launch-config selection, so the existing
coverage applies.
- FP4 output bytes can differ in the last bit across launch configs,
because the row-sum reduction order changes. The tests compare against
references with tolerance.
- The residual write-back is bit-identical.

## Reviewer Notes

- `cluster_n > 1` (H >= 32768): the config is computed on `H_per_cta`
and capped at 1024 threads. The tests cover H 16384/32768 and pass, but
these shapes were not timed.
- Possible follow-ups, not included here:
  - Switch input/residual to `cp.async.cg` on SM107.
- Check whether SM100/SM103 also benefits from the "<= 2 vectors per
thread" rule. Its tuned `(256, 256)` config at H 8192 uses 4 vectors per
thread.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved launch configuration for FP4 quantization with RMSNorm on
SM107 GPUs, while leaving other architectures unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4612
- **最后更新**: 2026-10-17T00:26:56Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

## FastVideo 昨日提交分析（批次 1/1）

### 1. 主要更新类型
**文档更新/基础设施迁移**。本次提交（`6212e72`）不涉及核心功能代码、性能优化或 Bug 修复，而是将项目的 **Documentation** 与 **Cookbook** 两大文档板块整体迁移至 **Blume** 平台（推测为 Hao AI Lab 统一使用的文档/知识库系统）。

### 2. 关键变更点及与项目整体方向的关系
- README 中原本列有独立入口：`hao-ai-lab.github.io/FastVideo`（文档站）与 `haoailab.com/FastVideo/cookbook/`（实践教程），迁移后这两类内容的托管与渲染方式发生统一。
- FastVideo 是面向视频生成模型的高吞吐训练/推理框架，其用户群体高度依赖 **Quick Start**、**Cookbook**（典型场景配方）来快速上手不同模型（如 Wan、HunyuanVideo 等）与蒸馏/服务化流程。文档的组织质量直接影响框架的采用率。
- 本次迁移反映了项目在"功能迭代之外"同步推进**开发者体验（DX）统一化**的方向，将分散在不同域名/系统的文档资源整合到单一平台，降低维护成本与用户查找成本。

### 3. 对项目的影响和潜在影响
- **正面**：文档入口与风格趋于一致，便于长期维护（一次迁移替代多处手工同步）；未来新增 Cookbook 条目、版本化文档（如随模型版本演进的推理指南）更易管理。
- **风险/注意点**：文档 URL 变更可能导致**外部链接失效**（博客、论文引用、Issue 中的旧链接），若未做重定向会影响既有用户与搜索引擎收录；README 中的链接若未同步更新，会造成入口不一致。
- 对核心功能无直接影响，属于低风险、高长期收益的整理性工作。

### 4. 值得关注的技术点
- **Blume 平台的角色**：值得关注它是否提供版本化文档、交互式示例（notebook 渲染）或与 CI 联动的能力——若支持，未来 FastVideo 的 Cookbook 可能向"可直接运行的配方"演进。
- **协作模式**：提交带有 `Co-authored-by: Aryan Kumar`，且 README 中有 Weekly Dev Meeting 与 Slack 社区入口，说明文档迁移是社区协作产出，体现项目有意识地将外部贡献纳入基础设施。
- 建议后续关注是否配套**链接重定向**或**归档旧文档站**的补充提交，这是评估迁移完整性的关键信号。

### 5. 结合项目背景对发展的影响
从 README 看，FastVideo 正在构建**文档 + Cookbook + 社区（周会/Slack）**三位一体的开发者生态，目标是让研究者与工程师能快速复现和部署视频生成工作流。此次迁移表明项目进入**生态巩固期**：核心能力趋于稳定后，重点转向降低使用门槛、统一知识沉淀。这有利于吸引更多用户采用其推理/蒸馏方案，形成"高质量框架 + 高质量文档"的正向循环，是项目从"工具"走向"平台"的重要一步。若后续能保持文档与代码版本同步更新，将显著提升项目的长期可维护性与社区活跃度。

（综上，本次提交虽小，但体现了 FastVideo 在工程化与社区运营上的成熟度提升，建议关注后续文档链接的连贯性与 Blume 平台的内容更新节奏。）

## 详细提交记录

### [6212e72](https://github.com/hao-ai-lab/FastVideo/commit/6212e7262ecb7d4f38eb0eb3201d296a3ca80fba)

- **作者**: Aryan Kumar
- **时间**: 2026-10-16T23:09:04Z
- **提交信息**: [docs] Migrate documentation and cookbook to Blume (#1969)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34736
- **最后更新**: 2026-10-16T23:34:40Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: YiYi Xu

## AI分析总结

## huggingface/diffusers 昨日提交分析

### 1. 主要更新类型

本次提交属于**纯文档更新**，不涉及任何代码逻辑变更。它专门针对 **FLUX.3 模块化（modular）文档体系**进行了多次迭代优化，最终合并为一次 PR。

---

### 2. 关键变更点及其与项目整体方向的关系

- **新增"Coming from DiffusionPipeline"迁移指南页面**：帮助用户从传统的 `DiffusionPipeline` 全流程调用方式迁移到模块化 API。这直接对应 diffusers 近期大力推动的**模块化架构方向**——将各组件（unet、vae、scheduler、guider 等）的加载与组合拆分为独立步骤，提供更高的灵活性和可组合性。

- **强化 lazy loading、输出格式、guider、offloading、可编辑 block 等差异说明**：通过 tips callout 清晰列出模块化 API 与 `DiffusionPipeline` 的核心差异，降低学习门槛。

- **新增/重构 per-step callbacks 文档**：在模块化模式下展示了如何使用 `callback_on_step_end` 进行逐步骤回调，并且该回调能正确遍历所有去噪循环（FLUX.3 包含多个去噪阶段）。这部分内容先是放在 quickstart 中，后被独立到专门的 callbacks 指南中。

- **文档结构多次调整**：将提示词建议移入 upsampling 章节（附带 "pop-the-step" 示例）、展示上采样后的 caption 效果、澄清 index 说明等，体现了对用户体验的持续打磨。

---

### 3. 对项目的影响和潜在意义

- **降低模块化 API 使用门槛**：FLUX.3 是 diffusers 中首个大规模采用模块化架构的模型，其文档质量直接影响用户能否顺利采用新范式。本次更新通过迁移指南、差异说明和回调示例，显著改善了上手体验。
- **文档质量提升**：经过 5 次迭代修订（从提交信息可见多次调整结构和内容位置），说明团队对文档的信息架构和用户阅读路径非常重视，力求让用户在正确的位置找到正确的信息。
- **推动社区采纳**：清晰的迁移路径有助于减少用户从旧 API 转向新 API 时的阻力，加速模块化架构的社区渗透。

---

### 4. 值得关注的技术点

- **多去噪循环的 callbacks 机制**：FLUX.3 的模块化流程涉及多个去噪循环（如 upsampling 阶段），回调需要正确遍历所有循环，这是模块化架构中一个容易被忽视的技术细节，文档对其做了专门说明。
- **lazy loading 模式**：模块化 API 采用惰性加载策略，仅在需要时才加载对应组件，这在内存管理上更灵活，但与 `DiffusionPipeline` 的 eager 加载行为有本质差异，文档中做了显式对比。
- **可编辑 block（editing blocks）**：模块化 API 支持在推理过程中替换或修改特定计算 block，这是 `DiffusionPipeline` 无法做到的高级能力，也是模块化架构的核心卖点之一。
- **Co-Authored-By 使用 AI 辅助**：提交信息中多次标注了 AI co-author，反映了 HuggingFace 团队在文档撰写中对 AI 工具链的实际采用。

---

### 5. 对项目整体发展的影响

基于 diffusers 的项目背景——作为 HuggingFace 生态中最核心的扩散模型推理库，正处于从"单一 pipeline 调用"向"模块化、可组合、可编辑"架构范式转型的关键时期——本次提交虽然是纯文档更新，但其意义不可小觑：

- 它直接服务于 **FLUX.3 模块化 API 的推广**，帮助社区用户完成认知迁移。
- 文档的完善程度是新架构能否被广泛采纳的重要非技术因素，本次迭代式的精细化打磨表明团队对这一转型的重视。
- 从长期来看，随着更多模型支持模块化调用方式，本次建立的"Coming from DiffusionPipeline"迁移指南模式可以被复用到其他模型的文档中，形成可扩展的文档范式。

综上，这是一次虽然规模不大但战略意义明确的文档更新，有力支撑了 diffusers 向模块化架构演进的整体方向。

## 详细提交记录

### [b800f82](https://github.com/huggingface/diffusers/commit/b800f828f3951c4d206e154411bcbfa693cd322e)

- **作者**: YiYi Xu
- **时间**: 2026-10-16T23:34:11Z
- **提交信息**: [docs] FLUX.3: modular-only notes, lazy loading, callbacks (#15069)

* [docs] FLUX.3: modular-only notes, lazy loading, callbacks

Add a tips callout on what differs from DiffusionPipeline (lazy loading,
outputs, guider, offloading, editing blocks), move the prompting advice
into the upsampling section with the pop-the-step example, and add a
per-step callbacks section with a block that takes callback_on_step_end.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* [docs] FLUX.3: callback block walks all denoising loops

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* [docs] modular: add "Coming from DiffusionPipeline" to the quickstart and move per-step callbacks to the callbacks guide

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* [docs] FLUX.3: show the upsampled caption; clarify the index note in the quickstart

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* [docs] modular: make "Coming from DiffusionPipeline" its own page

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 433
- **最后更新**: 2026-09-26T17:57:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13253
- **最后更新**: 2026-10-17T00:21:00Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

# DiffSynth-Studio 昨日提交分析（commit 4e34969）

## 1. 主要更新类型

本次提交以 **功能新增** 为主，同时附带 **文档更新** 和 **训练脚本扩展**。核心工作是为项目接入了 Flux 3 Image Klein 模型的支持，并补充了配套的训练资源。

## 2. 关键变更点及与项目整体方向的关系

- **新增 Flux 3 Image Klein 模型支持**：Klein 通常是 Flux 系列中的轻量/精简变体，这一接入延续了 DiffSynth-Studio"广泛支持前沿扩散模型"的核心定位，进一步丰富了图像生成模型矩阵。
- **新增 Entropack 训练脚本**：Entropack 可能指向基于熵压缩/打包思想的训练方法（如潜空间压缩或参数高效训练方向），这表明项目不仅关注推理侧的模型覆盖，也在持续强化**训练侧的工具链供给**。
- **文档同步更新**：确保新模型和新脚本对用户可见、可用，符合该项目一贯重视开发者上手体验的做法。

## 3. 对项目的影响和潜在意义

- **扩大用户可用的模型选择**：Klein 这类轻量化模型对显存有限的用户和生产部署场景更友好，有助于降低扩散模型的使用门槛。
- **强化训练能力**：提供开箱即用的训练脚本，使研究者和工程师可以基于新模型进行微调和二次开发，而不仅局限于推理演示。
- **巩固生态位**：DiffSynth-Studio 已在 Trendshift 等榜单上获得关注，持续快速跟进新模型是保持社区活跃度和项目影响力的关键策略。

## 4. 值得关注的技术点

- **Flux 家族的扩展方式**：如何将 Klein 变体高效整合进现有的 Flux 推理管线，值得研究其代码复用和适配模式。
- **Entropack 方法的落地**：如果这是较新的训练压缩技术，其实现在 DiffSynth 框架中的具体形式（是量化感知训练、潜空间压缩还是参数打包）值得关注，可能为后续论文复现和方法对比提供参考。
- **推理与训练的统一架构**：项目同时维护多模型推理和多模型训练两套能力，其抽象层设计值得借鉴。

## 5. 对项目发展方向的影响

结合 README 所展示的定位——DiffSynth-Studio 是 ModelScope 生态下专注于扩散模型合成（图像、视频多模态生成）的综合工作室——本次提交体现了项目发展的两条清晰主线：

其一，**横向扩展模型覆盖面**，从 Hunyuan Video、Flux 到各种变体模型，确保项目始终站在生成模型技术前沿；其二，**纵向深化工具链**，从纯推理框架逐步补齐训练、压缩、微调等环节，向"一站式扩散模型研发平台"演进。

这类提交虽然单次改动看似常规，但累积效应显著：每一次新模型和新脚本的加入都在降低用户的使用成本，同时增强项目在开源社区中的不可替代性，为后续吸引更多贡献者和研究合作奠定基础。总体而言，此次提交是 DiffSynth-Studio 保持技术迭代节奏、巩固其在扩散模型工具链领域领先地位的又一次稳步推进。

## 详细提交记录

### [4e34969](https://github.com/modelscope/DiffSynth-Studio/commit/4e3496991455b300fd60ab023113422cd16899f5)

- **作者**: Hong Zhang
- **时间**: 2026-10-16T10:15:39Z
- **提交信息**: Support Flux 3 image klein (#1759)

* support flux-3-image-klein

* minor fix

* update docs

* add entropack training scripts

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37226
- **最后更新**: 2026-10-17T00:24:08Z

## 提交统计

- **昨日提交总数**: 52
- **提交者数量**: 26
- **主要提交者**: Kan Wu, metamergebot, Benjamin Truong

## AI分析总结

# SGLang 昨日提交分析总结（共52条）

## 1. 主要更新类型分布

- **性能优化（Perf）**：18条，占比最高，聚焦 AMD DSv4 系列、dp-attention、unified-memory 等
- **功能新增（Feat）**：12条，涵盖 Rust 前端、gRPC、新算子、KV 传输等
- **Bug 修复（Fix）**：12条，涉及 hicache、rust-server、DSA、deepseek-v4.1 等
- **文档更新（Doc）**：7条，以 cookbook 部署指南为主
- **CI/测试改进**：8条，提升测试稳定性和效率

## 2. 关键变更点与项目方向的关系

- **AMD 生态大举推进**：约 14 条提交集中在 AMD/ROCm 上，完成了一个完整的 DSv4 优化系列（8 个阶段），从 GEMM 调优、FP4/FP8 索引器、MoE 排序到 Docker 镜像集成 aiter，形成系统性的 AMD 硬件支持。这与项目"快速推理"的核心目标高度一致——多硬件覆盖是其竞争力关键。
- **DeepSeek V4.1 (dsv4/dsv4.1) 深度适配**：多条提交围绕 DSpark draft SWA、MegaMoE、SWA 环形缓冲区展开，显示项目正紧密跟随前沿模型架构（滑动窗口注意力+MTP 投机解码）进行推理优化。
- **Rust 服务器成熟化**：`/v1/loads` 接口、gRPC 推理 RPC 补全、cache_salt 修复，表明 Rust 前端正逐步替代 Python 路由层，提升多机路由性能。
- **分离式推理（PD disagg）**：KV 传输校验跳过、解码端 KV 预分配优化等提交，继续强化大规模分布式部署能力。

## 3. 对项目的影响与潜在意义

- **硬件多元化**：AMD、Intel XPU、NPU、FlashInfer NVFP4 多路并行，降低对单一硬件的依赖，扩大用户群。
- **推理性能持续压榨**：如 2shot all-reduce、gloo gather+broadcast 同步、fp8 统一 KV 解码等，直接提升吞吐和降低延迟，巩固 SGLang 作为高性能 LLM 推理引擎的定位。
- **企业级可用性提升**：多 worker ASGI 路径可配置、prefetch 超时控制、CI 自动 PR 评论等，改善运维和开发体验。

## 4. 值得关注的技术点

- **Unified memory / compaction**：预热压缩移动、按页 ID 整体拷贝，优化内存碎片化场景。
- **MegaMoE 与 NVFP4 W4A16**：Meta、NVIDIA、AMD 多方合作的 MoE 专用算子链（muse spark 算子 2/5 系列），暗示大规模 MoE 推理的硬件级加速正在成型。
- **Claude AI 参与开发**：多条提交 co-author 为 Claude（Anthropic），反映 AI 辅助编码已进入核心基础设施项目。
- **投机解码 + SWA 组合优化**：DSpark draft SWA 从 radix tree 隔离、窗口提交跳过废弃 KV 行等细节，体现对复杂注意力机制推理路径的精细打磨。

## 5. 对项目整体发展的影响

结合 README 定位（"Fast inference for LLMs and multimodal models"），这些提交表明 SGLang 正从"通用推理引擎"向"多硬件、多模型架构深度优化的生产级平台"演进：AMD 系列优化使其在非 NVIDIA 平台具备竞争力；Rust 路由层和 PD 分离强化大规模部署能力；MegaMoE/FlashInfer 集成则卡位下一代 MoE 模型推理市场。项目正处于快速扩张功能边界与硬件覆盖面的阶段，同时通过 CI 和测试改进保障工程质量，整体发展势头强劲。

## 详细提交记录

### [d8dd49d](https://github.com/sgl-project/sglang/commit/d8dd49d21d56ea4cbe9b1ae98f4be37fdc412de7)

- **作者**: metamergebot
- **时间**: 2026-10-16T23:55:54Z
- **提交信息**: [Fix] srt: Apply --gc-threshold in every server process and freeze every tokenizer worker (#44785)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: joshuadeng <joshuadeng@users.noreply.github.com>

### [d230f2c](https://github.com/sgl-project/sglang/commit/d230f2c35b82aa3c0b2eb11da97538ba455af745)

- **作者**: metamergebot
- **时间**: 2026-10-16T23:51:20Z
- **提交信息**: [Feat] profiler: Add the forward pass id to detailed step span labels (#44775)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: charlotte12l <charlotte12l@users.noreply.github.com>

### [36cf028](https://github.com/sgl-project/sglang/commit/36cf0283460cda42fcb054a1d2b7b604a82f8c73)

- **作者**: metamergebot
- **时间**: 2026-10-16T23:47:50Z
- **提交信息**: [Perf] unified-memory: Prewarm the compaction move at startup and copy whole page envelopes by page id (#44592)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [aaf5f39](https://github.com/sgl-project/sglang/commit/aaf5f397a5a6565ad2cbcfe64bab56bdebbe4b75)

- **作者**: Khoa Pham
- **时间**: 2026-10-16T22:38:33Z
- **提交信息**: [Feat] dsv4.1: Support encoder SWA bounded replay with CUDA DP attention (#43813)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8e3f11b](https://github.com/sgl-project/sglang/commit/8e3f11b2193d18a62e9480c29e1e0514e9192094)

- **作者**: Yuwei An
- **时间**: 2026-10-16T22:05:45Z
- **提交信息**: [Perf] DSv4.1: Skip discarded KV rows during window commit (#44783)

### [a46fe83](https://github.com/sgl-project/sglang/commit/a46fe83c70d9e3085f6409e636e5029756fce409)

- **作者**: metamergebot
- **时间**: 2026-10-16T21:53:21Z
- **提交信息**: [CI] tests: Fork the gloo exchange test's ranks from a preloaded forkserver (#44679)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: fei-xx <fei-xx@users.noreply.github.com>

### [d5d8789](https://github.com/sgl-project/sglang/commit/d5d87899f9a84b8940854340d387db4304facac5)

- **作者**: Aarav
- **时间**: 2026-10-16T21:35:23Z
- **提交信息**: [Fix] DSA: skip-topk pipeline handoff for owed outputs (#43832)

Co-authored-by: Aarav <211792885+AaravMehta-07@users.noreply.github.com>

### [71b60fa](https://github.com/sgl-project/sglang/commit/71b60fa46c9da596f29c6182cdae8201c8c1596e)

- **作者**: Khoa Pham
- **时间**: 2026-10-16T21:29:05Z
- **提交信息**: [Fix] engram: Avoid blocking history copies during PD admission (#44787)

Co-authored-by: Trevor Morris <tmorris@nvidia.com>

### [2948662](https://github.com/sgl-project/sglang/commit/2948662026a8addefdba7697060aa109d821ec23)

- **作者**: metamergebot
- **时间**: 2026-10-16T20:53:41Z
- **提交信息**: [Perf] dp-attention: Exchange the scheduler's MLP sync rows with gather + broadcast on gloo (#44622)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: hanming-lu <hanming-lu@users.noreply.github.com>

### [f39c269](https://github.com/sgl-project/sglang/commit/f39c2693aa896de3fca9936645791cea634816ea)

- **作者**: metamergebot
- **时间**: 2026-10-16T20:47:52Z
- **提交信息**: [CI] rust-server: Raise the ChunkEvent frame-size cap to 152 bytes (#44773)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>

### [07950be](https://github.com/sgl-project/sglang/commit/07950be745136dc90de8a6f7f61d6fc734ae1858)

- **作者**: Chunan Zeng
- **时间**: 2026-10-16T20:43:18Z
- **提交信息**: [Perf] [NVIDIA] custom-all-reduce: Add 2shot_push all-reduce and retune SM100 TP4/TP8 (#42811)

### [21791e7](https://github.com/sgl-project/sglang/commit/21791e7023a31028a68dce04a9a0bd78faadd96f)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-16T20:40:03Z
- **提交信息**: [CI] [NVIDIA] DSv4.1-Flash: Split GB300 accuracy test into one file per config (#44696)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [a31a8c2](https://github.com/sgl-project/sglang/commit/a31a8c2bbd11983299fc7ea6e68565c0bb876639)

- **作者**: metamergebot
- **时间**: 2026-10-16T20:38:39Z
- **提交信息**: [CI] tests: Let test_hicache_storage size its host cache to the runner (#44729)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>

### [a18a908](https://github.com/sgl-project/sglang/commit/a18a908066dec07e93295e7da589c1c5bbbe5fa4)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-16T19:41:39Z
- **提交信息**: [Test] mem_cache: Free SWA peers below the eviction floor in the SWA repair test (#44777)

### [456231e](https://github.com/sgl-project/sglang/commit/456231e2517dd29e78c77d20126c893b3f1a6675)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-16T17:49:35Z
- **提交信息**: [Feat] kernels: Add muse spark operators and collective GEMM (2/5) (#44665)

Co-authored-by: 1am9trash <1am9trash@gmail.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>
Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Ethan Che <eche@meta.com>
Co-authored-by: HAI <hixiao@gmail.com>
Co-authored-by: Jiajun Li <guapisolo@gmail.com>
Co-authored-by: Jiajun Li <jiajun.li@radixark.ai>
Co-authored-by: Jimmy Shiu <jimmysh341@gmail.com>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>
Co-authored-by: Liangsheng Yin <lsyincs@gmail.com>
Co-authored-by: Wookje Han <52435620+wookjeHan@users.noreply.github.com>
Co-authored-by: Wookje Han <wookjeh@nvl72d079-T17.cm.cluster>
Co-authored-by: Wookje Han <wookjeh@nvl72d094-T17.cm.cluster>
Co-authored-by: Wookje Han <wookjeh@nvl72d157-T16.cm.cluster>
Co-authored-by: Wookje Han <wookjeh@nvl72d170-T04.cm.cluster>
Co-authored-by: Wookje Han <wookjeh@nvl72d214-T17.cm.cluster>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Yuhao Yang <yhyang201@users.noreply.github.com>
Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>
Co-authored-by: ethche <ethche@gmail.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>
Co-authored-by: jianan-gu <jianan.gu@intel.com>

### [80c54e6](https://github.com/sgl-project/sglang/commit/80c54e6ac52c769cb66c4bda53942898965e9bc3)

- **作者**: ormandj
- **时间**: 2026-10-16T17:45:16Z
- **提交信息**: [Fix] [AMD] hicache: Serve encoder-replay prefix hits with a paged DSpark draft SWA (#42716)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [553068a](https://github.com/sgl-project/sglang/commit/553068af25b040b291ae863c8aebfbda9e3d3392)

- **作者**: metamergebot
- **时间**: 2026-10-16T17:38:09Z
- **提交信息**: [Fix] rust-server: Honour cache_salt and require_reasoning on /generate (#44533)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [453b251](https://github.com/sgl-project/sglang/commit/453b251dbd0f9ca6e3de2ddec99a4ce7fe723e0f)

- **作者**: metamergebot
- **时间**: 2026-10-16T17:37:11Z
- **提交信息**: [Fix] hicache: Bound the storage prefetch timeout from the first blocked admission poll (#44614)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [989ccf4](https://github.com/sgl-project/sglang/commit/989ccf4863c6f9aa2ed68ffd32abbaacbc755a06)

- **作者**: metamergebot
- **时间**: 2026-10-16T17:36:46Z
- **提交信息**: [Feat] disaggregation: Let a KV transfer backend skip the checksum for an incomparable peer (#44605)

Co-authored-by: jiayisuse <jiayisuse@users.noreply.github.com>

### [63a9b7a](https://github.com/sgl-project/sglang/commit/63a9b7a71341ec286b39333936469144ef3968ab)

- **作者**: metamergebot
- **时间**: 2026-10-16T17:36:35Z
- **提交信息**: [Feat] http_server: Make the multi-worker ASGI app path configurable (#44583)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: joshuadeng <joshuadeng@users.noreply.github.com>

### [26a2f18](https://github.com/sgl-project/sglang/commit/26a2f18c0258b93edd315e03cb6f6d9a81881d63)

- **作者**: metamergebot
- **时间**: 2026-10-16T17:35:37Z
- **提交信息**: [Feat] sglang-server: serve /v1/loads from the Rust frontend (#44532)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [a038a0d](https://github.com/sgl-project/sglang/commit/a038a0dca05cefca1e0edc4ac43e3bfbec2e064c)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-16T15:39:50Z
- **提交信息**: [Fix] dsv41: Preserve tool-result image order and current-turn thinking (#44751)

### [ed2ebad](https://github.com/sgl-project/sglang/commit/ed2ebad342ddd774daf320b982987bb2c7f34492)

- **作者**: Duyi-Wang
- **时间**: 2026-10-16T15:34:01Z
- **提交信息**: [Doc] [AMD] cookbook: Refresh DeepSeek V4 AgentX PD recipe optimizations (#44454)

### [2c2986b](https://github.com/sgl-project/sglang/commit/2c2986be2b05525e3501a566aaf8ec2afcc87add)

- **作者**: Jimmy Shong
- **时间**: 2026-10-16T13:29:14Z
- **提交信息**: docs: add Beam 1.0 deployment cookbook (#44694)

Co-authored-by: Jimmy Shong <jimmy.shong@mac.attlocal.net>

### [7c99ace](https://github.com/sgl-project/sglang/commit/7c99ace127526c2a7b21e5474a2981e4789b367c)

- **作者**: Benjamin Truong
- **时间**: 2026-10-16T11:37:41Z
- **提交信息**: [Fix] dsa: Fix ragged seed indices before MTP draft decode (#42565)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5e240a2](https://github.com/sgl-project/sglang/commit/5e240a200dd04060e4d47bf967c409611949b82f)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-16T11:31:08Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches for Qwen3.5 and DeepSeek-V4.1-Flash GB300 (#44712)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4afae55](https://github.com/sgl-project/sglang/commit/4afae5568bdc72487db44f40f619780b1ba0efee)

- **作者**: Xinyi Song
- **时间**: 2026-10-16T10:11:02Z
- **提交信息**: [Perf] [AMD] dsv4: Add a separate MegaMoE decode instance (#44657)

Co-authored-by: HAI <hixiao@gmail.com>

### [2adc76a](https://github.com/sgl-project/sglang/commit/2adc76ad61a9c036304716a4548093b1b27b10fb)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-16T09:55:25Z
- **提交信息**: [Perf] [AMD] dsv4: reuse the q_lora fp8 quant for the C4 indexer wq_b (4/8) (#41903)

Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>
Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [9246acd](https://github.com/sgl-project/sglang/commit/9246acd462e8b5f7ccf139adca82795dcc44069f)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-10-16T09:50:20Z
- **提交信息**: [CI] [AMD] aiter: pin aiter commit to 2bb549 for rocm10.1 gfx1250 (#44620)

### [baf451f](https://github.com/sgl-project/sglang/commit/baf451fcd6f54962c7db7dc30c636cb534ba1f2a)

- **作者**: kk
- **时间**: 2026-10-16T09:47:41Z
- **提交信息**: [Perf] [AMD] dsv4: carry aiter DSv4 GEMM tuned rows and mHC tile_m=16 until aiter ships them (7/8) (#44008)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [f05da43](https://github.com/sgl-project/sglang/commit/f05da43d44067e4e4f95302b6d3bd40f7deb3b1d)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-16T09:39:27Z
- **提交信息**: [Feat] [AMD] disagg: Support DSV4 decode radix cache on ROCm unified KV (bf16/fp8, DSpark) (#30929)

Co-authored-by: HAI <hixiao@gmail.com>
Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [42eb556](https://github.com/sgl-project/sglang/commit/42eb556e66f1d5f288ee8b232a8a545431a25226)

- **作者**: kk
- **时间**: 2026-10-16T09:28:31Z
- **提交信息**: [Perf] [AMD] dsv4: optional e8m0 mxscale GEMM for dense 128x128 fp8 linears (6/8) (#44007)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [8d229d9](https://github.com/sgl-project/sglang/commit/8d229d96e00b3c02641fc12b7ee441c4f355bd25)

- **作者**: caihuali95
- **时间**: 2026-10-16T09:24:06Z
- **提交信息**: [Fix] unified-memory: enabling trtllm_mha with decode graphs and speculative decoding (#42930)

### [6efc96a](https://github.com/sgl-project/sglang/commit/6efc96abf975cb0a2658f7cdfa164c3e5ab5eb95)

- **作者**: kk
- **时间**: 2026-10-16T09:16:06Z
- **提交信息**: [Perf] [AMD] dsv4: FP4 indexer on aiter's row-group kernel for decode and target-verify (5/8) (#44006)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [9fde8bc](https://github.com/sgl-project/sglang/commit/9fde8bcc466f5f8b5c8222d266feff95551c71da)

- **作者**: kk
- **时间**: 2026-10-16T09:09:32Z
- **提交信息**: [Perf] [AMD] moe: small-batch sort with histogram + bitonic sort for 32 < P <= 256 (3/8) (#44004)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [f0ff183](https://github.com/sgl-project/sglang/commit/f0ff18353d2c6bd8d0c1896563e197d3f4fcfa2b)

- **作者**: kk
- **时间**: 2026-10-16T08:58:00Z
- **提交信息**: [Perf] [AMD] dsv4: fp8 verify writes the SWA ring in the fused norm/rope kernel (2/8) (#44003)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [56a3c4f](https://github.com/sgl-project/sglang/commit/56a3c4fa16765f591c9eb5dbf10761f31111dfa2)

- **作者**: Mingyi
- **时间**: 2026-10-16T08:55:41Z
- **提交信息**: [Doc] cookbook: Add RTX Spark Qwen3.6 NVFP4 recipe (#44707)

Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>

### [81c9d80](https://github.com/sgl-project/sglang/commit/81c9d804b033325cc3c407af5b58ce6c0771c843)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-16T08:54:38Z
- **提交信息**: [CI] pr-check-comment: Comment on PRs when lint or title check fails (#44708)

### [ab5858a](https://github.com/sgl-project/sglang/commit/ab5858ac8a8f2eb4dac3835e22e1a3f1cf9f1504)

- **作者**: kk
- **时间**: 2026-10-16T08:50:16Z
- **提交信息**: [Perf] [AMD] dsv4: fp8 unified_kv decode/verify on FlyDSL v4 nm decode with a latency-model split plan (1/8) (#44016)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [9baace8](https://github.com/sgl-project/sglang/commit/9baace84567d5ad23206eeaf716edf94e182fd2a)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-16T08:48:25Z
- **提交信息**: [Doc] cookbook: refresh MiniCPM-V 4.7 DSPARK benchmarks at the final model PR head (#44310)

Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [3d61bdd](https://github.com/sgl-project/sglang/commit/3d61bdd2c9db507e0b299488d1218b596364f42c)

- **作者**: Kan Wu
- **时间**: 2026-10-16T08:23:17Z
- **提交信息**: [Feat] sgl-router: Serve the remaining native gRPC inference RPCs (#42681)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [536cdb4](https://github.com/sgl-project/sglang/commit/536cdb4b04ba0323fa5ba6ead9b5702685c07a3e)

- **作者**: kk
- **时间**: 2026-10-16T08:20:40Z
- **提交信息**: [Feat] [AMD] docker: Install the sgl-amd-mono monokernel plugin in the ROCm image (#44621)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [fad7d95](https://github.com/sgl-project/sglang/commit/fad7d95a7f1a942e039f74eb2d319da29311b8cb)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-16T08:18:58Z
- **提交信息**: [Fix] deepseek-v4.1: Keep the DSpark draft SWA out of the radix tree (#44673)

### [06b81b1](https://github.com/sgl-project/sglang/commit/06b81b120e07c08becad03c91900f47a7f133dd6)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-16T08:14:54Z
- **提交信息**: [CI] deepgemm: Increase B200 release test timeout to 180 minutes (#44706)

### [bdc4ec1](https://github.com/sgl-project/sglang/commit/bdc4ec15ce4fbe2a05c43b3d6b79d2d657232863)

- **作者**: kk
- **时间**: 2026-10-16T08:13:37Z
- **提交信息**: [Perf] [AMD] dspark: No per-step host sync in decode (1/4) (#44405)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [5dd37af](https://github.com/sgl-project/sglang/commit/5dd37af412b32b65af938f1e730141ce93e28967)

- **作者**: Ziru
- **时间**: 2026-10-16T08:13:24Z
- **提交信息**: [Doc] [XPU] Cookbook: Update the XPU Docker version to 0.5.22 (#44647)

Co-authored-by: Niu Ziru <niuziru@gnr799217.jf.intel.com>

### [a448fdf](https://github.com/sgl-project/sglang/commit/a448fdf3161a10c059921ee1fba3c6b23b1792af)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-10-16T07:51:55Z
- **提交信息**: [Perf] [AMD] qwen3: Fuse QK-norm + RoPE + KV cache write for dense Qwen3 decode (#44267)

### [9d394df](https://github.com/sgl-project/sglang/commit/9d394dfbd755759d3add89cfd0bc86d59b31f78c)

- **作者**: amote-i
- **时间**: 2026-10-16T07:48:37Z
- **提交信息**: [Doc] [NPU] docs: refresh associated dependency  versions in npu docs (#44695)

### [7098ec3](https://github.com/sgl-project/sglang/commit/7098ec387c9f9d9f85a0c2c16bc1233f40f1d407)

- **作者**: Ziang Li
- **时间**: 2026-10-16T07:38:50Z
- **提交信息**: [Feat] FlashInfer: Add NVFP4 W4A16 and SiTU support to MegaMoE (#44036)

### [3a5d46e](https://github.com/sgl-project/sglang/commit/3a5d46e946fa496e447d5c806ac837a6d6786183)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-16T07:34:56Z
- **提交信息**: [Perf] pd: Stage decode-side KV preallocation lengths through pinned memory (#38955)

Co-authored-by: Jingshu Chen <96519051+elmo2019@users.noreply.github.com>

### [51faf52](https://github.com/sgl-project/sglang/commit/51faf523059d8f03b9efcdec6152d613a9e8ef65)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-16T07:06:14Z
- **提交信息**: [Fix] monokernels: Honor resolved CUDA graph configuration (#44630)

### [dfc8958](https://github.com/sgl-project/sglang/commit/dfc89580f1225d2806f7d60ed105761cc5aff067)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-16T07:00:12Z
- **提交信息**: [Doc] cookbook: Add Muse Spark Open SWA ratio calculator (#44687)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1291
- **最后更新**: 2026-10-16T11:34:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93946
- **最后更新**: 2026-10-17T00:24:59Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 26
- **主要提交者**: Oxana Korzh, bnellnm, cjackal

## AI分析总结

## vLLM 昨日提交分析（共30条）

### 1. 主要更新类型分布
- **功能新增/特性**：约 8 条（可插拔 KV 缓存配置、Beam 推理解析器、DP 引擎唤醒机制、Mamba2 变长解码等）
- **Bug 修复**：约 9 条（LoRA SM90 数值异常、解析器工具调用 ID、多模态 PNG 透明度、Mooncake 多连接器统计等）
- **性能优化**：约 5 条（FP4 DeepGEMM 跳过填充、投机解码短草稿跳过、Triton JIT 预热共享、MiniMax M2 流式工具参数解析等）
- **CI/构建/治理**：约 6 条（MI300→MI355 测试迁移、B200 NVSHMEM 挂起修复、移除无用脚本、CODEOWNERS 更新）
- **重构清理**：1 条（死代码移除）

### 2. 关键变更点与项目方向的关系
- **架构可扩展性**：`Pluggable KVCacheConfigBuilder`（#53558）将 KV 缓存规划抽象为平台/模型可插插拔的构建器，是核心基础设施的模块化改进，契合 vLLM 支持多样硬件与模型生态的目标。
- **分布式与调度**：DP 引擎自主管理唤醒、移除前端 `FIRST_REQ`（#59559），简化了分布式调度路径的职责边界。
- **投机解码（Spec Decode）持续推进**：Mamba2 变长解码、短草稿跳过 bonus-logit 归约、DSpark 自适应验证等多条提交，说明投机解码仍是性能主线之一。
- **新模型与新前端支持**：Beam 推理/工具解析器、Kimi-K3、GLM-5.2、MiniMax M2、Inkling MTP 等，体现 vLLM 快速跟进最新模型生态。
- **多硬件平台深化**：AMD ROCm（ITER 融合、KDA prefill、MI355 CI 迁移）和 Intel XPU（MXFP4 线性后端）投入显著，符合"人人可用"的普惠定位。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：LoRA SM90 fp32 展开输出修复、编译缓存键排除 Ray 环境变量等修复，直接减少生产环境中的隐蔽错误。
- **延迟与吞吐改善**：MiniMax M2 工具参数流式解析将 16KB 调用从 5.9 秒降到 26 毫秒，是工具调用场景的量级级提升；DeepGEMM/投机解码优化直接作用于 MoE 与解码阶段吞吐。
- **CI 资源布局优化**：大批测试迁往 MI355、修复 NVSHMEM 挂起，提高多硬件回归测试的覆盖面和可靠性。
- **维护健康度**：移除无用安装脚本、清理死代码，降低长期维护成本。

### 4. 值得关注的技术点
- **AI 代理协同开发常态化**：绝大多数提交含 Claude/Codex/Cursor 等 AI 代理作为共同作者，反映 vLLM 已深度采用 AI 辅助开发流程。
- **量化路径精细化**：SM90 LoRA fp32 陷阱、SM100 FP4 padding 跳过、XPU MXFP4 后端、per-tensor 量化+RMSNorm 融合，量化相关的数值正确性与性能打磨非常密集。
- **解析器/前端鲁棒性**：工具调用 ID、推理块闭合、logprobs 流式路径、离线评分聊天模板等多条修复，说明 serving 前端的边界情况仍是易错区，也是生产用户高频触碰的路径。

### 5. 对项目发展的总体影响
结合 README "简单、快速、廉价的 LLM 服务"这一目标，昨日提交呈现三条清晰主线：一是**核心架构的可扩展性**（可插拔 KV 缓存、DP 调度解耦），为未来更多平台和模型铺路；二是**全栈性能打磨**（内核、量化、投机解码、工具调用解析），持续兑现"快速"承诺；三是**多硬件与 CI 基建**（ROCm/XPU/MI355 迁移），支撑"人人可用"的普惠定位。这些提交共同强化了 vLLM 作为生产级 LLM 推理引擎的稳定性与生态覆盖，短期提升用户可感知的延迟与正确性，长期降低新硬件/新模型的接入门槛，对项目保持领先的推理框架地位具有积极意义。

## 详细提交记录

### [523d74e](https://github.com/vllm-project/vllm/commit/523d74e2ac78867aa35d535835e14f78fb7433af)

- **作者**: Beichen Huang
- **时间**: 2026-10-16T23:42:30Z
- **提交信息**: [Bugfix][LoRA] Fix garbage/NaN lora_expand output on SM90 with fp32 i… (#61906)

Signed-off-by: BeichenHuang <polarishuang0.0@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [a94c315](https://github.com/vllm-project/vllm/commit/a94c3157119e52adacb4d580d4e950983d14e353)

- **作者**: aoshen02
- **时间**: 2026-10-16T23:41:54Z
- **提交信息**: [DP] Engines own wave wake-ups; drop the front-end FIRST_REQ (#59559)

Signed-off-by: fh3 <a@b>
Co-authored-by: fh3 <a@b>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b544587](https://github.com/vllm-project/vllm/commit/b5445874080ce85c575f2bcb847852235f1af7bc)

- **作者**: wangxiyuan
- **时间**: 2026-10-16T23:16:47Z
- **提交信息**: [Core][Feat] Pluggable KVCacheConfigBuilder for platform/model-specific KV cache planning (#53558)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [2268d83](https://github.com/vllm-project/vllm/commit/2268d83bd9eb9a60138b3591ad9ec8c170b093df)

- **作者**: alp
- **时间**: 2026-10-16T23:09:12Z
- **提交信息**: [Bugfix][Multimodal] Honor RGB PNG transparency when loading images (#61986)

Signed-off-by: mottopanikeiku <176798723+mottopanikeiku@users.noreply.github.com>
Co-authored-by: mottopanikeiku <176798723+mottopanikeiku@users.noreply.github.com>

### [28e92ee](https://github.com/vllm-project/vllm/commit/28e92eeff25f96c1b78a2f7552f6747c9073798e)

- **作者**: Omar Muhammad
- **时间**: 2026-10-16T22:58:56Z
- **提交信息**: [ROCm][Perf][Kimi-K3] Use AITER Gluon chunk_kda for KDA prefill (#59552)

Signed-off-by: Omar Muhammad <omar.muhammad@amd.com>
Signed-off-by: Nicholas Susanto <nicholas.susanto@amd.com>
Co-authored-by: Nicholas Susanto <nicholas.susanto@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [b088eba](https://github.com/vllm-project/vllm/commit/b088eba94431b711ffaa2f356e33361cf38b8fc5)

- **作者**: Afonso Ribeiro
- **时间**: 2026-10-16T22:46:02Z
- **提交信息**: [Perf][Parser] Stream MiniMax M2 tool argument values incrementally (16 KB call: 5.9 s to 26 ms) (#62035)

Signed-off-by: Afonso Ribeiro <afonso.diamantino2@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [596e530](https://github.com/vllm-project/vllm/commit/596e53067548fab65de6fc3abdcd020f752e7ae7)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-16T22:39:46Z
- **提交信息**: [Kernel] Add router GEMM kernels for (5120, 256) and BF16 output to ll_bf16_gemm (#62042)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Lain <fusiyuan2000@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [153a171](https://github.com/vllm-project/vllm/commit/153a17166e5d07bc38184dedeea542d2e8885e55)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-16T21:08:29Z
- **提交信息**: [Frontend] Add the Beam reasoning and tool parsers (#62052)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Yoni Gozlan <74535834+yonigozlan@users.noreply.github.com>
Co-authored-by: neilkg <33635204+neilkg@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9731f30](https://github.com/vllm-project/vllm/commit/9731f30a030c545e7f29a8a4ed96b8562be12c88)

- **作者**: Dan Blanaru
- **时间**: 2026-10-16T20:59:48Z
- **提交信息**: [Bugfix] Keep VLLM_RAY_BUNDLE_INDICES out of the compile cache key (#61211)

Signed-off-by: DanBlanaru <48605845+DanBlanaru@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [68ebea7](https://github.com/vllm-project/vllm/commit/68ebea789a4652a6b16665d50d79805866b933ec)

- **作者**: Tyler Michael Smith
- **时间**: 2026-10-16T20:20:52Z
- **提交信息**: [Perf][MoE] Skip padded work in SM100 FP4 DeepGEMM experts (#59044)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [cc2e4fe](https://github.com/vllm-project/vllm/commit/cc2e4fecf2fca603939445faccf20dd466f1502e)

- **作者**: afriedri
- **时间**: 2026-10-16T20:19:07Z
- **提交信息**: [ROCm] [fusion] support ROCm aiter fusion of per tensor quant + rmsnorm (#52831)

Signed-off-by: Andy Friedrich <afriedri@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9eb7fb9](https://github.com/vllm-project/vllm/commit/9eb7fb9157f622bb2c87839788bbec1d5ef51ad2)

- **作者**: Tyler Michael Smith
- **时间**: 2026-10-16T19:57:49Z
- **提交信息**: [Build] Remove unused `tools/install_deepgemm.sh` (#61265)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [663e535](https://github.com/vllm-project/vllm/commit/663e5356404332d6c764180aef41cc07015cd34a)

- **作者**: cjackal
- **时间**: 2026-10-16T19:42:48Z
- **提交信息**: [Perf][Spec Decode] Skip bonus-logit reduction for short drafts in rejection sampling (#61451)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [5bf3d9f](https://github.com/vllm-project/vllm/commit/5bf3d9f6653e53485f0ca74149f958dc6cbd3b82)

- **作者**: Oxana Korzh
- **时间**: 2026-10-16T18:53:49Z
- **提交信息**: [ROCm][Kimi-K3] Support DSpark adaptive verification on MI355X (#59824)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [307c584](https://github.com/vllm-project/vllm/commit/307c5844ad2d3003154f3a768540e686e37dddec)

- **作者**: djramic
- **时间**: 2026-10-16T18:36:14Z
- **提交信息**: [ROCm][CI] Enable batch invariance for the ngram scheduling accuracy test (#62048)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [3dc6def](https://github.com/vllm-project/vllm/commit/3dc6def36088a4139182e1a79cfe9b4e5953aa8b)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-10-16T18:23:59Z
- **提交信息**: [Attention][Spec Decode] Enable varlen Mamba2 decode for adaptive verification (#53036)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e7a5bdb](https://github.com/vllm-project/vllm/commit/e7a5bdb4542ca13e70a1ef0a1d9fb628b632c691)

- **作者**: djramic
- **时间**: 2026-10-16T18:22:38Z
- **提交信息**: [ROCm][CI] Move Spec Decode Speculators + MTP to MI355 (#62053)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [ae8f412](https://github.com/vllm-project/vllm/commit/ae8f41238cc7316781ef4359890940749735b209)

- **作者**: alberto
- **时间**: 2026-10-16T16:54:42Z
- **提交信息**: [Bugfix][Parser] Honor a prompt-closed reasoning block in non-streaming parse and reasoning token counts (#61857)

Signed-off-by: Alberto Perdomo <aperdomo@redhat.com>

### [cffc0cf](https://github.com/vllm-project/vllm/commit/cffc0cfa311f4997be58cfe8f5f6473ab4898269)

- **作者**: Misha Goin
- **时间**: 2026-10-16T16:00:12Z
- **提交信息**: [CI] Fix B200 FusedMoE Layer Kernels hang on NVSHMEM IB setup (#61695)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [706791d](https://github.com/vllm-project/vllm/commit/706791d5162355dfe2a924dd0257770fc529ec10)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-16T15:58:59Z
- **提交信息**: [CI][AMD] Move 17 test groups from MI300 to MI355 and test large DeepSeek/Nemotron evals on AITER (#61955)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [76081b9](https://github.com/vllm-project/vllm/commit/76081b9ee4bfc73fc307505d633ada5bce079880)

- **作者**: Sawyer Bowerman
- **时间**: 2026-10-16T15:49:26Z
- **提交信息**: [Bugfix][Model] Honor quantization config in Inkling MTP (#61921)

Signed-off-by: Sawyer Bowerman <sbowerma@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [1a5b187](https://github.com/vllm-project/vllm/commit/1a5b187066c918b2e23184560d703174dd542828)

- **作者**: bnellnm
- **时间**: 2026-10-16T15:16:03Z
- **提交信息**: Add @bnellnm to CODEOWNERS (#62025)

Signed-off-by: Bill Nell <bnell@redhat.com>

### [8e25bbc](https://github.com/vllm-project/vllm/commit/8e25bbca19f0605b347e103dde4bf5355d049e72)

- **作者**: Wentao Ye
- **时间**: 2026-10-16T15:01:07Z
- **提交信息**: [Refactor] Remove dead code multiple places (#61843)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [8a6c044](https://github.com/vllm-project/vllm/commit/8a6c0449b36e7aba29c2a6b1720ca3c08cfafa32)

- **作者**: Avinash Paul
- **时间**: 2026-10-16T13:38:55Z
- **提交信息**: [Bugfix][ROCm][GLM-5.2] Stop forcing skip_final_all_reduce on AMD DSA model path (#58589)

Signed-off-by: avininjamay8 <Avinash.Paul@amd.com>
Signed-off-by: avininjamay8 <avpaul@amd.com>
Co-authored-by: avininjamay8 <avpaul@amd.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [de7eeaa](https://github.com/vllm-project/vllm/commit/de7eeaa87bc19ecf088472d5f4471cdc9a5ab995)

- **作者**: Ayushman Singh
- **时间**: 2026-10-16T12:59:42Z
- **提交信息**: [Perf] Share Triton JIT warmup compilation pool across registered kernels (#61422)

### [64175d3](https://github.com/vllm-project/vllm/commit/64175d38277f3731069cabaa9cb88983ee314f85)

- **作者**: Martin Hickey
- **时间**: 2026-10-16T10:27:17Z
- **提交信息**: [Bugfix][Frontend] Keep the parser's tool call IDs in batch derender (#61852)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [4ab99ff](https://github.com/vllm-project/vllm/commit/4ab99ff1364735de12ac804ff4a15958001bbe06)

- **作者**: alp
- **时间**: 2026-10-16T10:20:46Z
- **提交信息**: [Bugfix][Frontend] Honor the constructor chat template in offline scoring (#61990)

Signed-off-by: mottopanikeiku <176798723+mottopanikeiku@users.noreply.github.com>
Co-authored-by: mottopanikeiku <176798723+mottopanikeiku@users.noreply.github.com>

### [024c518](https://github.com/vllm-project/vllm/commit/024c5188bf5a8a464124b36519c1e7de76648625)

- **作者**: Shimi Bandiel
- **时间**: 2026-10-16T10:04:15Z
- **提交信息**: [Frontend] Resolve logprobs on the parsed streaming derender path (#60437)

Signed-off-by: Shimi Bandiel <shimib@google.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: wang.yuqi <yuqi.wang@daocloud.io>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [9a16d43](https://github.com/vllm-project/vllm/commit/9a16d43ef0413b0a2a222e7f5baa4498c291ae5b)

- **作者**: Hexiang Wang
- **时间**: 2026-10-16T09:54:48Z
- **提交信息**: [Bugfix][Mooncake] Fix MultiConnector stats and proxy SSE responses (#61218)

Signed-off-by: whx-sjtu <xiaowang990929@gmail.com>
Signed-off-by: Nicolò Lucchesi <nicolo.lucchesi@gmail.com>

### [07f3857](https://github.com/vllm-project/vllm/commit/07f3857fb93772fed64e06642cdb0b8c03e0b249)

- **作者**: zofia
- **时间**: 2026-10-16T09:07:05Z
- **提交信息**: [XPU][Linear][MXFP4] enable torch as mxfp4 linear backend on xpu (#51965)

Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>
Signed-off-by: zofia <110436990+zufangzhu@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-17
**监控日期**: 2026-10-16
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7214
- **最后更新**: 2026-10-16T23:32:51Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 6
- **主要提交者**: NATURE, psv666, Canlin Guo

## AI分析总结

## vllm-omni 昨日提交分析（共10条）

### 1. 主要更新类型

- **ROCm 平台适配与 CI 增强**：3条（#9032、#9031、#8994），占比最高
- **Bug 修复**：3条（#9031、#9019、#9001）
- **模型性能优化**：3条（#8990、#9016、#8989），全部围绕 MOSS Local 模型
- **测试基础设施**：2条（#8026、#8613）中涉及 CI fixture 与基准测试支持

整体以 **ROCm 硬件生态拓展** 和 **MOSS Local 模型推理优化** 为主线，辅以测试稳定性修复。

### 2. 关键变更点及与项目方向的关系

- **ROCm/HIP 平台深度适配**（#9032、#9031、#8994）：为 HunyuanVideo-1.5 在 MI300 上添加 nightly 冒烟测试，修复 CUDA-only Triton 启动选项在 HIP 下的兼容问题，并使 OOM 注入测试可在 HIP 环境运行。这直接服务于项目"easy, fast, cheap serving for everyone"的普惠目标——通过支持 AMD ROCm 硬件，降低多模态模型服务的硬件门槛。

- **MOSS Local 两阶段推理引擎优化**（#8990、#9016、#8989）：将 codec chunks 打包进现有 Stage1 引擎、用显式融合 kernel 替换 Inductor 自动编译、优化两阶段 kernel 和 host 输出。这是一条连贯的性能优化链，表明团队正在将 MOSS Local 从"可用"推向"高效"。

- **CI 与测试基础设施**（#8026、#9019）：新增共享 AsyncOmni pytest fixture（含残留 worker 清理）、修复 MiniCPM duplex 响应测试，提升测试可靠性和可维护性。

- **基准测试扩展**（#8613）：支持 Qwen3-Omni duplex 数据集基准测试，扩展了多模态双工场景的评测能力。

- **流式服务健壮性**（#9001）：修复 ASGI 取消场景下视频流清理问题，保障生产环境长连接稳定性。

### 3. 对项目的影响和潜在意义

- **硬件多元化**：ROCm 的持续投入使 vllm-omni 在 AMD 数据中心 GPU 上逐步具备生产可用性，扩大了用户群体和部署场景。
- **MOSS Local 推理效率提升**：显式融合 kernel 取代 Inductor 编译意味着更可预测的延迟和更小的运行时开销，对实时多模态服务意义重大。
- **工程成熟度提高**：共享 fixture、残留清理、ASGI 取消保护等细节修复，体现项目正从功能扩展期过渡到生产就绪期。
- **双工场景覆盖完善**：duplex 基准测试和 MiniCPM duplex 测试修复，强化了实时语音/视频交互这一核心场景。

### 4. 值得关注的技术点

- **显式融合 kernel vs Inductor 自动编译**：#9016 选择手动 kernel 而非 torch.compile 自动路径，反映在多模态场景下自动编译的不确定性（编译时间、kernel 质量）仍是瓶颈，手动优化仍是高性能推理的重要手段。
- **ASGI 取消保护模式**（#9001）：在异步 web 框架中保护流式清理不受任务取消影响，是 Python 异步流式服务的常见难题，值得其他项目借鉴。
- **共享测试 fixture 中的残留 worker 清理**（#8026）：暗示此前多模态推理测试中 worker 泄漏是已知痛点，此类基础设施投入对大型 CI 矩阵（尤其 HIP/CUDA 双平台）的稳定性至关重要。
- **多个提交使用 AI 辅助工具**（Cursor、Claude、Codex）共同署名，体现了该社区对 AI 辅助开发的开放态度。

### 5. 对项目发展的整体影响

从 README 定位来看，vllm-omni 致力于提供"人人可用"的全模态模型服务。本批提交中 ROCm 适配拓宽了硬件生态，MOSS Local 优化提升了核心推理路径性能，测试与 CI 加固增强了多平台持续交付能力。三者共同推动项目从"支持多模态推理"向"在异构硬件上稳定高效地服务全模态模型"演进，是项目走向生产级多模态服务引擎的关键一步。

## 详细提交记录

### [7a28b6b](https://github.com/vllm-project/vllm-omni/commit/7a28b6b2f9329a0adff9c274a28e24046d05de0c)

- **作者**: haic0
- **时间**: 2026-10-16T23:32:45Z
- **提交信息**: [CI/Build][ROCm] Add HunyuanVideo-1.5 MI300 nightly smoke (#9032)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [e1d77a3](https://github.com/vllm-project/vllm-omni/commit/e1d77a38a7d645283e660b6add4dfb2439732d15)

- **作者**: haic0
- **时间**: 2026-10-16T19:52:26Z
- **提交信息**: [Bugfix][ROCm] Omit CUDA-only Triton launch options on HIP (#9031)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Codex <noreply@openai.com>

### [6613d77](https://github.com/vllm-project/vllm-omni/commit/6613d77bf1c5ed27f5bc68787aeb4b988914dfce)

- **作者**: haic0
- **时间**: 2026-10-16T15:55:50Z
- **提交信息**: [CI/Build][ROCm] Make weekly OOM injection ready on HIP (#8994)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [6d29fde](https://github.com/vllm-project/vllm-omni/commit/6d29fde51c08b2512eafa8778315c2eda745bebe)

- **作者**: Armaan Amatya
- **时间**: 2026-10-16T14:53:19Z
- **提交信息**: [CI] Add shared AsyncOmni pytest fixtures with leftover-worker cleanup (#8026)

Signed-off-by: Armaan Amatya <armaanamatya2014@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [f6a0b5f](https://github.com/vllm-project/vllm-omni/commit/f6a0b5f99634ca9b1eecc6bed10328eac4d28b11)

- **作者**: NATURE
- **时间**: 2026-10-16T11:42:15Z
- **提交信息**: [Bugfix] Fix MiniCPM duplex response-required CI test (#9019)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [aa9c9a2](https://github.com/vllm-project/vllm-omni/commit/aa9c9a2d2ce3ff8640f1b4ab8937a6194b0ead4d)

- **作者**: Canlin Guo
- **时间**: 2026-10-16T11:24:14Z
- **提交信息**: [Model] Pack MOSS Local codec chunks in the existing Stage1 engine (#8990)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>
Co-authored-by: Sy03 <1370724210@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9bbfb61](https://github.com/vllm-project/vllm-omni/commit/9bbfb61d50fcd489c6e964db90abef0ecc233070)

- **作者**: Canlin Guo
- **时间**: 2026-10-16T10:09:51Z
- **提交信息**: [Model] Replace MOSS Local Inductor compilation with explicit fused kernels (#9016)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>
Co-authored-by: Sy03 <1370724210@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [303b8df](https://github.com/vllm-project/vllm-omni/commit/303b8df6531fc37d2d0da7b73c318324a0daa4b4)

- **作者**: psv666
- **时间**: 2026-10-16T09:00:43Z
- **提交信息**: [Frontend][Benchmark] Support Qwen3-Omni duplex dataset benchmarks (#8613)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: NATURE <wzliu@connect.hku.hk>

### [082eaf2](https://github.com/vllm-project/vllm-omni/commit/082eaf235cfc373322bc5f8a1a3398915446a82d)

- **作者**: amy-why-3459
- **时间**: 2026-10-16T08:40:17Z
- **提交信息**: [Bugfix] Shield video stream cleanup from ASGI cancellation (#9001)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [c8ccb8a](https://github.com/vllm-project/vllm-omni/commit/c8ccb8aed59e1db273d9dce6ee91b4f09d30db18)

- **作者**: Canlin Guo
- **时间**: 2026-10-16T07:32:16Z
- **提交信息**: [Model] Optimize MOSS Local two-stage kernels and host outputs (#8989)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>
Co-authored-by: Sy03 <1370724210@qq.com>

---
