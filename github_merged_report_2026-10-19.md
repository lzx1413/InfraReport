# GitHub Stars 合并报告 - 2026-10-19

**合并日期**: 2026-10-20
**监控日期**: 2026-10-19
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


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2249
- **最后更新**: 2026-10-19T11:34:01Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: LeoCristallo

## AI分析总结

## 提交概要分析

### 1. 主要更新类型
- **性能优化 + 重构**：提交标签 `[ops, perf]` 和 `refactor` 表明这是一次以性能和代码结构为目标的改动，而非新增功能或修复 Bug。

### 2. 关键变更点及与项目方向的关系
- **核心变更**：优化了合并式（merged）MoE（Mixture-of-Experts）算子的反向传播过程中激活值（activation）的存活时间（lifetime），即让中间激活在反向计算中尽早释放，减少显存峰值占用。
- **与项目方向的关系**：VeOmni 的核心定位是 "Model-Centric Distributed Recipe Zoo"，旨在高效扩展多模态模型的分布式训练。MoE 是大规模模型训练中的关键组件，而显存瓶颈是扩展 MoE 规模的主要障碍之一。该提交直接服务于项目"扩展（Scaling）"这一主线目标。

### 3. 对项目的影响和潜在意义
- **显存效率提升**：缩短激活存活时间意味着训练时峰值显存下降，用户可在相同硬件上训练更大规模的 MoE 模型，或用更小的 micro-batch 保持吞吐。
- **对多模态训练的间接支持**：多模态训练本身显存需求高（不同模态的编码器 + MoE 路由），显存优化对 VeOmni 的典型场景（如 Omni 模型）尤其有价值。
- **维护性改善**：重构通常伴随代码结构梳理，可能使 merged MoE 算子更容易扩展到新的并行策略或精度模式。

### 4. 值得关注的技术点
- **"Merged MoE" 设计**：将多专家计算合并处理的算子形式，是融合 kernel 的常见优化路径，需关注其实现是否兼容序列并行/专家并行等分布式策略。
- **反向激活生命周期管理**：涉及 autograd 图中 tensor 的释放时机，可能借助了 `torch.utils.checkpoint`、自定义 autograd Function 或显式 `del` 等手段，这类技巧在大规模训练框架中是精细调优的重点。
- **与 FSDP/Megatron 类并行方案的兼容性**：VeOmni 支持多种分布式配方，此类底层算子优化需保证在不同并行模式下行为一致，值得验证。

### 5. 对项目发展的影响（结合 README 背景）
VeOmni 论文目标是通过统一的分布式配方让任意模态模型都能高效训练，项目已覆盖稠密模型、MoE、视频/音频等多种场景。此次提交体现了项目在**工程落地层面的持续打磨**——在已有功能完备的 MoE 支持基础上，进一步挖掘显存与性能潜力，属于典型的"成熟度提升"型提交。这类改动虽不显眼，但对希望基于 VeOmni 进行实际大规模训练的用户而言，直接降低了使用门槛（更少显存、更稳定）。它也表明社区/团队正积极回应大规模训练中真实的资源瓶颈问题，有利于提升项目在生产环境中的可信度和采用率。

**总结**：这是一次聚焦 MoE 反向传播显存优化的重构型提交，精准契合 VeOmni "高效扩展多模态训练" 的核心使命，对项目的性能基线和生产可用性都有积极意义。

## 详细提交记录

### [8a15e45](https://github.com/ByteDance-Seed/VeOmni/commit/8a15e4552cde4f8847612b572134b94968f2d8f9)

- **作者**: LeoCristallo
- **时间**: 2026-10-19T11:23:41Z
- **提交信息**: [ops, perf] refactor: reduce merged MoE backward activation lifetime (#1306)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2927
- **最后更新**: 2026-10-19T18:49:00Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Tingting-Y, Yang Yong (雍洋), Bilang ZHANG

## AI分析总结

## LightX2V 昨日提交分析

### 1. 主要更新类型

本次 5 笔提交涵盖：**性能优化**（CPU offload 静态常驻块、VAE 内存优化）、**重构**（kernel 后端组织、HTTP 参数解析统一）和**文档更新**。

### 2. 关键变更点与项目方向的关系

**静态常驻块 Offload（#1629）是本次最核心的变更。** CPU offload 场景下权重传输可能比块计算更慢，导致去噪停顿。该提交在 Wan 2.1、Qwen Image、Qwen Image 2.1 Turbo 和 MiniMax-H3 四个模型中引入静态均匀分布的常驻块机制：离线测量计算与传输时间后确定常驻块数，推理时保留这些块在设备端，其余块通过事件驱动的双缓冲流式传输。这直接服务于 LightX2V 的核心目标——轻量高效视频生成推理。

**Kernel 后端重构（#1632）** 将 NVIDIA 相关包重命名并保留旧命名的兼容支持，属于架构层面的整理，为后续多后端扩展奠定基础。

**HTTP 参数解析统一（#1630）** 消除了接口层的分散逻辑，提升服务化部署的可维护性。

### 3. 对项目的影响

- **性能与稳定性的双重提升**：静态常驻块方案避免了在线搜索的额外开销，同时显著减少 offload 引起的计算停顿；Qwen Image 2.1 VAE 内存优化进一步降低显存压力。
- **配置体系更加清晰**：移除冗余的 `use_event_offload` 开关，将 `cpu_offload_layout` 替换为布尔型 `cpu_offload_block_contiguous`，非法值给出明确错误提示，提升了用户体验。
- **模型覆盖面扩展**：常驻块机制同时覆盖文生图和图像编辑任务，MiniMax-H3 也纳入支持范围。

### 4. 值得关注的技术点

- **事件管理的双缓冲传输**：用两个 CUDA event 管理的 buffer 实现计算与传输的流水线化，去噪步骤结束后释放常驻权重，失败时也保证资源回收。
- **离线估算而非在线搜索**：用一个代表性 DiT 块实测时间后直接推算常驻块数，避免了运行时反复校准的复杂性，在实际部署中更可预测。
- **Agent Skills 集成**：新增 `.agents` 结构下的静态块驻留技能，并更新连续 offload 指南，反映了项目对 AI 辅助开发流程的重视。
- **多后端基线**：同时提供 CUDA 和 NPU 的基线、估算器和常驻块启动器，体现了跨硬件平台的适配思路。
- **139 项针对性测试在 H200 上通过**，合并上游 main 后验证，质量把控严格。

### 5. 对项目发展的意义

LightX2V 定位为轻量视频生成推理框架，这些提交在三个维度推动了项目发展：**推理效率**方面，静态常驻块和 VAE 优化直接降低端到端延迟和显存占用，使框架在消费级和云端部署场景都更具竞争力；**架构健壮性**方面，kernel 后端重构和 HTTP 层统一为未来多硬件支持和更复杂的服务化场景做好铺垫；**生态建设**方面，中英文文档同步、配置项的清晰化和 Agent Skills 的引入降低了开发者上手门槛。整体来看，这些变更体现了项目从功能覆盖向工程成熟度和部署可用性深化的趋势。

## 详细提交记录

### [34e7a44](https://github.com/ModelTC/LightX2V/commit/34e7a447bf1261b5e81e8bd52ea9a6c276707254)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-19T16:40:06Z
- **提交信息**: refactor(kernel): organize backends and rename NVIDIA package with le… (#1632)

…gacy support

### [540102c](https://github.com/ModelTC/LightX2V/commit/540102c31eae93ed4ada01647144de9d9045fde3)

- **作者**: Chernobyllight
- **时间**: 2026-10-19T12:29:22Z
- **提交信息**: feat(offload): add static block residency across Wan, Qwen Image, and MiniMax-H3 (#1629)

## Summary

CPU block offload can stall denoising when weight transfers take longer
than block computation. This change adds static, uniformly distributed
resident blocks for Wan 2.1, Qwen Image, Qwen Image 2.1 Turbo, and
MiniMax-H3 while keeping residency estimation outside inference.

- Measure computation and transfer time using a representative real DiT
block, directly estimate the resident count, and write a config for
inference. There is no online search or overlap calibration.
- Keep the selected blocks on the device across denoising steps, stream
the remaining blocks through two event-managed buffers, and release
resident weights before decoding and on failure.
- Provide CUDA/NPU baseline, estimation, and residency launchers with
concise English and Chinese documentation. Qwen Image 2.1 covers
text-to-image and image editing.

## Configuration

- `offload_resident_blocks: 0` selects event-based double buffering with
no extra resident blocks. Positive values distribute that many resident
blocks uniformly. Omitting the field preserves the legacy offload path.
- Remove the redundant `use_event_offload` switch from these four model
integrations; the separate Flux2 implementation retains its existing
switch.
- Replace `cpu_offload_layout` with `cpu_offload_block_contiguous:
true/false`, defaulting to `false`. The boolean selects contiguous block
storage independently of residency. Invalid types and the obsolete
layout field fail with a clear error.
- Update baseline and contiguous configs, the standalone estimator, and
bilingual guides together.

## Agent skills

Add a static block residency skill under upstream’s `.agents` structure
and update contiguous-offload guidance for the boolean layout option.

## Validation

- 139 targeted checks passed on NVIDIA H200 after merging upstream main
at `2918a3d6`, covering configuration validation, tracked-config
migration, model dispatch, numerical correctness, transfer counts, and
resident-weight release/rebuild behavior, including warmup and decoding
boundaries.
- Real Qwen Image 2.1 DiT checks exercised all 32 blocks with small
inputs, both layouts, T2I/I2I, and resident counts of 0, 1, 16, 31, and
32. Repeated requests and denoising steps matched the reference bitwise;
cross-layout denoising outputs also matched bitwise.
- The Qwen Image 2.1 estimation launcher completed for both layouts at
2048 × 2048 and produced the expected boolean config and matching layout
report.
- Python lint/format checks, JSON migration checks, shell syntax, skill
validation, and documentation links passed.
- NPU changes received static checks only; no NPU device run was
performed for this update. Small-input DiT checks are not a full
image-generation pipeline test.

### [f70bb06](https://github.com/ModelTC/LightX2V/commit/f70bb063463bfb890533d9c552c0fd65e90398cd)

- **作者**: Tingting-Y
- **时间**: 2026-10-19T12:12:21Z
- **提交信息**: docs: update README documentation (#1631)

Updated the LightX2V Studio descriptions in the English and Chinese
README files.

### [ec13e35](https://github.com/ModelTC/LightX2V/commit/ec13e3592ba95ecb1e9fd739b4beafe00de0f346)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-19T11:21:00Z
- **提交信息**: refactor: unify HTTP request parameter parsing and forwarding (#1630)

### [2918a3d](https://github.com/ModelTC/LightX2V/commit/2918a3d641cd7c63b1c095ca9c8f248e1ffa0f7e)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-19T08:54:17Z
- **提交信息**: optimize qwen-image-2.1 vae mem (#1627)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2306
- **最后更新**: 2026-10-19T19:53:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6709
- **最后更新**: 2026-10-20T01:02:26Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 12
- **主要提交者**: eigen, 0z5a, Jimmy Zhou

## AI分析总结

# FlashInfer 昨日提交总结（37 个提交）

## 一、主要更新

昨日更新以**性能优化**为绝对主线（约占半数），辅以**功能新增**、**Bug 修复**、**测试加固**与**大规模重构**。核心方向可归纳为三条：Rubin（SM107）原生适配、NVFP4 低精度端到端栈构建、Kimi-K3 MoE 与前沿模型深度调优。

## 二、关键变更

**Rubin 架构适配成为主线**：约 5 项以上提交面向 SM107/R200，涵盖 blockwise FP8 GEMM 新后端、MLA decode 利用率修复、GDN 分块预填充、FP8/FP4 GEMM 选择、MegaMoE 优化及 H1536/H4096 RMSNorm 训练内核。SM107 正从借用 SM100 代码走向原生支持。

**NVFP4 低精度通信栈成型**：新增 Cake NVFP4 all-reduce 内核（8 种变体），在 NVLink 上按序传输 E2M1 值、E4M3 块缩放与 FP32 行缩放，实现量化感知通信；同时提供 FP8 逐行 GEMM+All-Reduce 融合内核，消除独立集合通信调用。NVFP4 all-reduce 在 GB200/GB300/SM107 上几何平均加速 7.5–8.6%。

**Kimi-K3 MoE 深度优化**：通过 `evict_first` 缓存提示减少权重重读对激活/路由表的驱逐；将量化与路由表重置融合进单个内核，采用 512 对/CTA 路由粒度；all-gather matmul 在 SM103a 上通过 SM push 路由带与 `cta_group::2` CTA 配对内核，部分形状加速 5.8–11.5%。MegaMoE 工作负载每解码步 MoE 时间降低约 10 倍。

**训练场景扩展**：新增 cake_kda（GLM-5.3-Flash）、cake_causal_conv1d（Flash-linear-attention）训练内核，均提供前向+反向完整支持，反向加速最高 4–8 倍，标志项目从纯推理向训练/微调延伸。

**大规模代码去重**：CAKE DSA indexer 净减约 38,000 行，Kimi-K3 FP8 投影源文件净删 74,227 行，均通过掩码指令地址与 SASS 位级一致验证保证行为不变。

**Bug 修复**：修复 JIT 并发下载重复工作、SM107 trace gates 派生不一致、topk_clusters_exact 跨集群共享内存竞态、Blackwell 平台 ragged Q 张量 TMA 加载问题（运行时按 SM100/SM103 能力条件清除描述符 bit 85）。

**测试加固**：参数化测试重构（660 用例缩减为 69 个常规用例）、采样 fuzz 测试、RMSNorm 输出契约覆盖。

## 三、项目影响

FlashInfer 正从"单一内核库"向"跨架构、跨后端、训练推理兼备的内核平台"加速演进。硬件覆盖面从 Hopper/Blackwell 主力向 Rubin 全面扩展；技术栈从自研 CUDA 向 CuTe-DSL/Cake/trtllm-gen 多后端统一，layernorm_quant 完成 CuTe-DSL 迁移；NVFP4 计算与通信端到端贯通，对 Blackwell 大模型推理吞吐意义显著。SM100/103/107/110+ 各自独立的路由与修复策略，标志项目进入逐架构逐形状调优的成熟阶段。多个新功能以 opt-in 或 `backend="auto"` 接入，用户迁移成本低，默认行为不变。

## 四、值得关注的技术点

- **自适应 KV split 调度**：按 SM 数动态调整 split 上限 [48,128]，小 batch MLA decode 提升 1.25x。
- **split-K 不改内核**：通过 strided view 复用 CUTLASS batch 模式实现 K 维切分，手法优雅。
- **mbarrier phase 复用与双 lane Sinkhorn**：LayerNorm 双重归约配合 cluster barrier；Sinkhorn 改为 2 lane 寄存器操作，提升 2–5%。
- **L2 缓存感知优化**：LoRA GEMM 条带光栅化配合 TMA evict 策略；SM107 GDN 改用 EVICT_NORMAL 利用更大 L1。
- **条件式 TMA 描述符修正**：运行时按 OOB 阈值判断是否清除特定 bit，细节精致且范围受控。
- **位级可复现性**：多处内核采用固定顺序规约保证 bit-identical；PDL 链式通信流水化 MoE 路由内核。
- **测量方法严谨**：A/B/B/A 交错测量、CUDA graph、逐形状逐 run 报告，为性能声明提供可信度。

## 详细提交记录

### [7385b0d](https://github.com/flashinfer-ai/flashinfer/commit/7385b0d1e12a5683ed1edd68f15f3e1a652408cf)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-19T23:59:59Z
- **提交信息**: perf(cute_dsl_mla): let small CuTe-DSL MLA decode launches use more KV splits (#6710)

<!-- .github/pull_request_template.md -->

## 📌 Description

**perf(cute_dsl_mla): let small CuTe-DSL MLA decode launches use more KV
splits.**

The CuTe-DSL MLA decode kernel splits each request's KV cache across
CTAs and merges the partial results in a separate reducer kernel. The
number of splits (`split_kv`) was capped at a static 48. That is plenty
once a few work units (requests x 128-row query tiles) share the GPU,
but a single long request launches only 2 x 48 = 96 CTAs and leaves more
than half of a 208-SM GPU idle (about a third of a 148-SM one).

This change raises the cap only when the launch has too few work units
to fill the GPU at 48 splits, which in practice means one or two query
tiles: the cap becomes the number of resident 2-CTA clusters divided by
the work-unit count, bounded to [48, 128]. On a 208-SM part that is 104
splits for one unit and 52 for two; on a 148-SM part it is 74 for one
unit and 48 otherwise. Launches with three or more units on today's
parts are unchanged.

The reducer is sized to the launch as before. For `split_kv <= 48` the
capacity rule is byte-identical to the old one (same kernels, same
register budget); above 48 it grows to the covering power of two, up to
128. The reducer already accepts up to 256 splits, so no new kernels are
needed. The rule is not gated on SM107 on purpose: the under-fill is
arch-independent, Rubin just has more SMs to leave idle.

**Measured (same-node A/B, 3 interleaved rounds, `cute-dsl` backend,
kv_lora_rank 512, batch 1, 8 query tokens, 12 heads, 128K context):**

| row | GR100 (208 SMs) | B200 (148 SMs) |
|---|---|---|
| 128K ctx, bf16 KV | 1.25x | 1.09x |
| 128K ctx, fp8 KV | 1.07x | 1.07x |
| 64K ctx, batch 2, 16 heads (cap 48 -> 52) | n/a | 1.00x (neutral) |

Outputs match the `trtllm-gen` MLA backend under the benchmark refcheck
on all three rows. The fp8 128K row gains less because it is L2-resident
and latency-bound rather than bandwidth-bound.

Why the cap is 128 and not higher: on the 208-SM part, 1024 KV tiles /
104 splits normalises to 103 nonempty splits, so cap 104 and cap 128
produce the identical launch; 128 is just the headroom for larger parts.
Experiments that split the reducer's output dimension across more CTAs
instead (1, 2, or 4 bands on top of the raised cap) were neutral to
negative, so the reducer grid policy is left alone.

## 🔍 Related Issues

Follow-up to the MLA decode attainment gap on SM107 (internal Rubin perf
tracking).

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
- [x] All tests are passing (`unittest`, etc.).

`tests/attention/test_cute_dsl_mla_decode.py::test_mla_split_kv_cap` is
updated for the new expected split counts (106 / 74 / 128 for one unit
at 212 / 148 / 1024 active blocks, 53 for two units at 212, 48 for three
units at 288, 26 for four units at 212 unchanged) and asserts the
reducer capacity above 48 (53 -> 64, 104 -> 128, 128 -> 128).

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

The only behaviour change is for launches whose work-unit count is at
most `clusters / 48` (one or two units on 148- to 208-SM parts). The
persistent and variable-split (`is_var_split_kv`) paths pick their own
split counts and are not touched. The modular CuTe-DSL MLA wrapper
(`flashinfer/cute_dsl/attention/wrappers/batch_mla.py`) has its own
sizer and is intentionally left as is.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Large attention workloads can now use split counts of up to 128,
beyond the previous limit of 48.
* Split capacity adjusts to the amount of available work, allowing some
workloads to use more splits while retaining the 48-split cap when there
are three work units. This expands the range of workload configurations
supported by split-KV processing.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a2c583d](https://github.com/flashinfer-ai/flashinfer/commit/a2c583d6bc572e5f17db367e03c8a70e8bf61ad8)

- **作者**: eigen
- **时间**: 2026-10-19T23:32:38Z
- **提交信息**: deslop(cake_dsa_indexer): fold kernel twins, share launcher bindings, drop dead registry glue (#6802)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR removes duplicated and dead code from the experimental
Cake-generated DSA indexer top-k in
`flashinfer/experimental/cake_dsa_indexer/`. The family serves
`flashinfer.dsa_indexer.dsa_indexer_topk(..., backend="cake")`, JIT
only, on sm_100a, sm_103a and sm_107a. The PR does three things:
- It deletes 29 kernel translation units and 57 TVM-FFI bindings. Their
build entries now compile a kept sibling source with their own `-D`
flags.
- It drops the test-only lever table and unused registry glue.
- It caches the validated dispatch policy per architecture.

The diff against the base is 122 files, +2,829 / -41,042 (net -38,213),
all inside the family. Every program keeps its kernel symbol, host-shim
namespace, library name, dispatch keys, launch geometry and arguments.
Program selection, launch arguments and results are unchanged for every
input.

**Behaviour changes** (all deliberate):
- **Stale JIT workspaces.** 113 of the 133 `build.json` entries now
build a sibling program's kernel source, binding source, or both, with
their own `-D` flags. Library names and closure digests are unchanged.
So a JIT build directory from before this change holds objects built
from the deleted sources. Those objects have the same kernel symbol, and
the gate below checks that their SASS is identical after masking
instruction addresses and encodings. When upgrading, start from a fresh
JIT workspace for this family's modules. The validation below uses a
fresh workspace per tree.
- **Host-check backtraces.** `TVM_FFI_CHECK` / `TVM_FFI_THROW`
backtraces in the bindings now name the shared binding file and its line
numbers instead of the program's own binding. For the hoisted TMA
encoders they name the host header. Message texts are unchanged.
Conditions that name the kernel symbol are pre-expanded, so the text
still shows the symbol, not the macro.
- **Removed Python surface.** None of these names has an in-tree reader
outside the family, but an out-of-tree reader would break.
- `cake_jit.py`: the loader helpers `registered_archs`,
`program_available`, `select_program` and `specs_for_arch`.
- `cake_jit.py`: the `launch` field of the 68 `PROGRAMS` records.
Records now carry `arches`, `library` and `role`. The bindings set
block, cluster and dynamic shared memory themselves.
- The test-only lever table
`tests/test_helpers/cake_dsa_indexer_program_levers.py` (1,173 lines),
with its import and asserts. The runtime never read it.
- **Policy caching.** `cake_backend.policy_for` is memoised per
architecture with `functools.cache`. `DispatchPolicy.from_record` now
validates once per process and architecture instead of twice per eager
call. An unregistered architecture still raises `NotImplementedError`
with the same message on every call.
- **Tests.**
- Three new CPU tests:
`test_shared_kernel_sources_keep_distinct_symbols`,
`test_shared_binding_sources_keep_distinct_namespaces` and
`test_policy_is_validated_once_per_architecture`.
  - The lever-table and `launch` asserts are removed.
- Collected ids go from 164 to 167 (42 -> 45 functions), and none are
removed. GPU gating is unchanged.
- **Docs.**
- The README Layout section, the registry header and the `csrc/` host
header each state once that the kernel and launcher sources, the
registry and `build.json` are exporter output. They are hand-folded here
into shared translation units selected by per-entry `-D` flags, pending
exporter support.
- The README's `cake_jit.py` bullet describes the trimmed record, and
the lever-table mention is gone.

## Changes

Footprint against the base:

| | Base | Head |
|---|---:|---:|
| `csrc/cake_dsa_indexer_topk/` `.cu` files | 136 | 50 |
| `cake_dsa_indexer_topk_host_common.cuh` (lines) | 52 | 487 |
| `cake_jit.py` (lines) | 899 | 802 |
| `cake_backend.py` (lines) | 1,064 | 1,067 |
| Test file (lines) | 2,173 | 2,334 |
| README (lines) | 248 | 267 |
| `build.json` (lines) | 2,695 | 3,494 |

**Sources.** At the base, the 136 `.cu` files were 68 kernel translation
units and 68 TVM-FFI bindings:
- Each kernel translation unit had one `extern "C"` kernel symbol,
`kernel_cake_dsa_indexer_topk_<hash20>`.
- Each binding had one host-shim namespace, `cake_host_shim_<16hex>`.

87 files are deleted: 29 kernel translation units, 57 bindings and the
lever table. What stays:
- **39 kernels.** 21 are byte-identical to the base. The other 18 change
only in `#ifndef` defaults, `#if` / `#elif` lever arms and the
`CAKE_PROGRAM_KERNEL(` definition line.
- **11 bindings**, parameterised the same way. They use
`CAKE_PROGRAM_KERNEL` / `CAKE_PROGRAM_SHIM` with `#ifndef` defaults
equal to the program each was exported for, plus the finalize launch
constants.
- **The host header** grows from 52 to 487 lines. It now holds the
hoisted TMA descriptor encoders, selected by `CAKE_HOST_COMMON_PART`,
and two small helper macros.

**`build.json`.** It still has 133 entries, one per (program,
architecture): 40 sm_100a, 40 sm_103a and 53 sm_107a.
- Every entry keeps its name, architecture, entry point, gencode,
minimum CUDA, conditional flags, path and closure digest.
- 113 entries now list a sibling's kernel or binding source and carry
per-entry `-D` flags:
- all 113 get `-DCAKE_PROGRAM_KERNEL=<own symbol>` and
`-DCAKE_PROGRAM_SHIM=<own namespace>`;
- entries also get the lever, window and thread constants where the kept
source's defaults differ.
- Every entry's per-source sha256 map is updated, because every binding
changed.

**Registry and unchanged files.**
- `PROGRAMS` still has 68 records, one per program. The 68 kernel
symbols stay distinct, and so do the 68 host-shim namespaces.
- `PROGRAM_KEYS` (40 / 40 / 53 keys per architecture) and `POLICY` are
unchanged.
- The shared loader `cake_build.py`, `cake_policy.py`, the device
preamble and the device helpers are unchanged.

### 1. Drop the test-only lever table and dead registry glue
(`22a43bda3`; 4 files, +16 / -1,309)
- Deletes `tests/test_helpers/cake_dsa_indexer_program_levers.py` (1,173
lines). Only one import and the key-set / record-shape asserts of the
registry test read it.
- In `cake_jit.py`, drops the four loader helpers that nothing calls:
`registered_archs`, `program_available`, `select_program` and
`specs_for_arch`. The backend dispatches through its own `program_for`
and `cake_policy.select_program`.
- Drops the `launch` field of the 68 `PROGRAMS` records, which no host
code reads.
- The test drops the matching import and asserts. The README and the
registry header describe the trimmed record.
- No kernel, binding, manifest entry, dispatch key or policy value
changes.
- Covers step 1 as a hand edit of the exported registry. The exporter's
registry template is not changed.

### 2. Fold 9 scan lever twins into their sibling kernels (`77a2d9983`;
21 files, +377 / -20,526)
- Nine scan programs were lever twins of a sibling:
  - four differ only in the tile-unroll literal (`TILE_UNROLL` 2 vs 1);
- three add the snake-order blocks, one of them also with the
tile-unroll value;
- two add the snake-order blocks plus the register-split operands of the
wide kind, one of them also with the tile-unroll value.
- Their nine kernel translation units (20,468 lines) are deleted. Their
11 `build.json` entries (one per architecture) build the sibling's
kernel with:
  - `-DTILE_UNROLL=<n>` / `-DCAKE_LEVER_SNAKE=<n>`;
- `-DCAKE_PROGRAM_KERNEL=<own symbol>` / `-DCAKE_PROGRAM_SHIM=<own
namespace>`.
- The eight kept kernels gain `#ifndef` defaults equal to their own
values and `#if` / `#elif` arms for the twins' lever text. They name
their symbol through `CAKE_PROGRAM_KERNEL`.
- Proof: rendering each kept source with each twin's defines reproduces
the deleted kernel line for line. This covers 9 fold renders and 8
identity renders: 1,070 checks, 0 differing lines.
- `test_shared_kernel_sources_keep_distinct_symbols` pins one distinct
symbol per entry.
- Covers step 2 (the four `TILE_UNROLL` pairs) and the mechanical part
of step 6. Scan kernel translation units go from 37 to 28. The
sample-fit twins and the cross-architecture pairs stay (see Not in this
PR).

### 3. Fold finalize kernel clones into per-form sources (`f0e4f65de`;
34 files, +1,171 / -5,754)
- The 25 rank-finalize kernel sources fall into 9 window groups. Members
of a group differ only in the kernel symbol and ten `#define` values:
the `SMEM_S_*` window constants, `SMEM_TOTAL` and `RANK_XCH_PAD`.
- The 5 CUB finalize sources differ only in four values:
`SMEM_SCRATCH_*`, `SMEM_TOTAL` and `THREADS`.
- One source per group stays, 10 in total (9 + 1). Each has `#ifndef`
defaults equal to its own values and names its symbol through
`CAKE_PROGRAM_KERNEL`.
- The other 20 sources (5,515 lines) are deleted. Their 54 `build.json`
entries (20 programs across the three architectures) build the kept
source with their own constants and the `-DCAKE_PROGRAM_KERNEL` /
`-DCAKE_PROGRAM_SHIM` pair. Every library keeps its distinct kernel
symbol.
- Proof: 54 fold renders and 10 identity renders: 2,457 checks, 0
differing lines. The CPU symbol test also covers the finalize groups.
- Covers step 3 except the `constexpr` derivation of the shared-memory
constants. They stay `-D` values with `#ifndef` defaults (see Not in
this PR).

### 4. Cache the validated dispatch policy per architecture
(`90297e288`; 2 files, +24 / -1)
- `policy_for` re-ran `DispatchPolicy.from_record` (about sixty field
checks) on every call. The eager path calls it twice per call: once to
prepare, once to plan.
- The registry record is immutable for the life of the process. So the
function is now memoised per architecture with `functools.cache`, like
the program loader.
- `test_policy_is_validated_once_per_architecture` checks two things:
the same object is returned, and the unregistered-architecture error
still raises on every call.
- Covers step 5.

### 5. Share binding bodies, hoist common scan launcher text
(`a646474d5`; 73 files, +1,335 / -13,546)
- With the kernel symbol, the host-shim namespace and the finalize
launch constants masked, the 68 exported TVM-FFI bindings were 11
distinct texts.
- One binding per text stays: 11 files, 100-201 lines each. They are
parameterised through:
- `CAKE_PROGRAM_KERNEL` / `CAKE_PROGRAM_SHIM`, defaulting to the program
each was exported for;
- for the finalize launchers, the `THREADS` / `SMEM_TOTAL` constants
their entries already pass to the kernel.
- The other 57 bindings are deleted. Their entries build the shared
source with their own `-D` values.
- Every scan binding carried its own TMA descriptor encoders
(`EncodeTma_Q` / `EncodeTma_K` / `EncodeTma_W`). They now live once in
the shared host header, as one verbatim part per box shape (whole
functions only), selected by `CAKE_HOST_COMMON_PART`. The opening of
each binding's `Run` stays in the binding.
- The exporter's per-file comment in the kept bindings is replaced by
one neutral two-line note.
- Proof: rendering each shared source with each entry's defines
reproduces that entry's base binding line for line: 133 entries, 68
programs, 0 differing lines. Of 384 check conditions scanned, none
stringises a macro name.
- `test_shared_binding_sources_keep_distinct_namespaces` pins one
distinct namespace per entry.
- Covers the mechanical part of step 4: whole-body sharing and the
hoisted encoders. The role-level launcher template is not included (see
Not in this PR).

## Validation

Base `e623eac470` (upstream main) against head
`a646474d539896b8d694864f959833cc0fbf4ed4`.

**SM107 evidence is compile-only.** The SM107 SASS and host rows were
produced with a CUDA 13.4 toolchain on a GB300 host. No CC 10.7 GPU ran
the tests or the load-all check in this PR.

- **Device SASS gate.** There is one row per build entry:

  | Arch | Rows | Fold | Identity |
  |---|---:|---:|---:|
  | SM100 | 40 | 20 | 20 |
  | SM103 | 40 | 20 | 20 |
  | SM107 | 53 | 25 | 28 |

- Fold rows cover the entries that now build another program's kernel.
Base: the entry's own deleted kernel with the base flags. Head: the kept
kernel with the entry's exact flags, including its `-D` set.
- Identity rows cover the entries that keep their own kernel: the same
source built with the base recipe and with the head recipe.
- Each build is dumped with `cuobjdump`, instruction addresses and
encodings are masked, and the instruction text is compared per kernel.
- Each build must contain exactly one kernel, named by the entry's own
symbol and never by the kept source's default. The required result is
identical after masking instruction addresses and encodings.
- SM100 (40 rows, built and compared on B200): 40 / 40 identical (20
fold rows + 20 identity rows; exactly one kernel per build, named by the
entry's own symbol)
- SM103 (40 rows, built and compared on GB300): 40 / 40 identical (20
fold rows + 20 identity rows; exactly one kernel per build, named by the
entry's own symbol)
- SM107 (53 rows, compile-only with a CUDA 13.4 toolchain on a GB300
host; no CC 10.7 GPU in this PR): 53 / 53 identical (25 fold rows + 28
identity rows; exactly one kernel per build, named by the entry's own
symbol; compile-only, no CC 10.7 GPU)
- **Host gate.** There is one row per build entry:

  | Arch | Rows | Own-binding | Shared-binding |
  |---|---:|---:|---:|
  | SM100 | 40 | 5 | 35 |
  | SM103 | 40 | 6 | 34 |
  | SM107 | 53 | 9 | 44 |

Each row compares the entry's own base binding with the binding source
it builds at the head with its `-D` flags, plus the hoisted host header.
Both must:
  - compile;
  - contain no device functions;
- have identical preprocessed text after the documented normalisations:
line markers, blank lines, unsigned-literal suffixes, adjacent string
literals, and the `__FILE__` / `__LINE__` arguments of the check macros'
backtrace;
- export the FFI entries and the shim's `Run` with no foreign namespace.
- SM100: 40 / 40 passed (all compiled, no device code, preprocessed text
identical after normalisation, the FFI entries and the shim's Run
exported, no foreign namespace)
  - SM103: 40 / 40 passed (same checks)
- SM107 (compile-only, as above): 53 / 53 passed (same checks;
compile-only)
- **Planner proof.** This runs on CPU with the real loader, in each
architecture's environment.
- The host dispatch policy is enumerated on base and head over a dense
grid of public-API geometries. The grid covers all three architectures
and SM counts 148 / 152 / 160 / 192 / 208 / 212 / 216 / 256, and
includes the partition-knob rows.
  - The registry view and the full selection streams must be identical.
- Every point must produce a program on both sides. A stream of
identical exceptions fails.
- Result: identical on both architectures' environments (B200 and GB300
runs): the base and head registry views and the full selection streams,
including the partition-knob rows, agree over 1,331,856 enumerated
points (every geometry, architecture and SM count), 0 points raised on
either side, and the only differing informational lines are the loader
names and record fields this PR removes
- **CPU checks on the head tree.**
  - ruff / `py_compile` on the changed Python files.
- Stale-reference counts for the 87 deleted files, the removed loader
helpers, the lever table and the `launch` field.
- `csrc/` tree shape: 39 kernel and 11 binding translation units; 21
kept kernels byte-identical to the base and 18 parameterised; 0 literal
symbols or namespaces in the bindings.
  - The text proofs above, re-run from clean snapshots.
- The registry invariant: 68 distinct symbols and 68 distinct
namespaces. The 40 / 40 / 53 keys reach exactly the programs of each
architecture.
  - `build.json` canonical form, with every per-source sha256 verified.
- The repository's manifest checker,
`scripts/check_cake_build_manifests.py --in-tree`.
  - Collected ids: 164 -> 167.
- The CPU test subset with CUDA hidden on the head (static inventory:
head 72 passed / 95 skipped, base 69 / 95).
- Result: all passed on the head tree, run on both environments: ruff
check / format clean and py_compile ok on the 3 changed Python files (a
stand-alone import-order lint reports 0 findings on base and head);
stale-reference counts at 0 for the 87 deleted files (repo-wide), the
per-digest source names in Python / tests / docs, the lever table, the
removed loader helpers and the launch field (68 records with role, 0
with launch); csrc shape as stated (39 kernel + 11 binding translation
units, 21 kept kernels byte-identical to the base, the 18 changed
kernels exactly the parameterised set, 29 + 29 CAKE_PROGRAM_KERNEL
guards and defaults, 11 bindings through the two macros, 0 literal
binding declarations or namespaces, 0 check conditions naming a program
macro); the text proofs re-run from clean snapshots (scan fold 1,070
checks / 0 differing lines, finalize fold 2,457 / 0, binding render 133
entries and 68 programs / 0 differing lines with 384 conditions scanned
and none stringising a macro; the gate tables regenerate identically
from the tree); registry invariant 68 distinct symbols and namespaces,
40 / 40 / 53 keys reaching exactly the programs of each architecture;
build.json canonical with 133 / 133 per-source digests verified; the
repository's manifest checker clean for all 7 packages and for this
package; collected ids 164 -> 167 (the three new CPU tests, nothing
removed; GPU ids unchanged); CPU test subset with CUDA hidden 72 passed
/ 95 skipped; commit messages clean with the trailer on all 5
- **GPU tests.**
- Full pytest of `tests/experimental/test_cake_dsa_indexer.py` and
`tests/experimental/test_cake_dsa_indexer_api.py` on the head and on the
unchanged base. Each runs on one GPU with a fresh JIT workspace per
tree.
- The static inventory expects head 167 passed / 0 skipped and base 164
/ 0. Every GPU test requires a registered program for the device, so any
skip would be a regression.
- An all-programs load check: every build entry of the GPU's
architecture is built and loaded into one process through the real
loader. That is 40 libraries on SM100 and 40 on SM103.
- Each library must export exactly its own kernel symbol, its shim `Run`
and the two FFI entries, and `run` and `build_cuda_version` must
resolve.
- B200: head 167 passed, 0 skipped (2 min 36 s); unchanged base 164
passed, 0 skipped (2 min 29 s); all 40 sm_100a build entries built and
loaded into one process (40 distinct kernel symbols and 40 distinct shim
namespaces over the 40 programs of the architecture; run and
build_cuda_version resolvable on every module)
- GB300: head 167 passed, 0 skipped (2 min 8 s); unchanged base 164
passed, 0 skipped (2 min 2 s); all 40 sm_103a build entries built and
loaded into one process (40 distinct kernel symbols and 40 distinct shim
namespaces over the 40 programs of the architecture; run and
build_cuda_version resolvable on every module)
- R200 (SM107): not run in this PR. The only SM107 evidence is the
compile-only rows above.

## Not in this PR

- **Exporter changes (steps 1-4).** The issue words steps 1-4 as
exporter changes, but no exporter change lands here.
- The registry, `build.json`, the shared kernel / binding sources and
the hoisted host header are hand edits of exporter output. This is
disclosed in the README Layout section, the registry header and the
`csrc/` host header.
  - Regeneration by the exporter is a follow-up.
- The closure digests were not recomputed and library names are
unchanged; see the fresh-workspace note in Summary.
- **Step 4, role-level launcher template.** The template with
`EncodeTma_{Q,K,W}` parameterised by box dims is not done.
  - The bindings are shared by whole text: 11 sources for 68 programs.
  - The encoders are hoisted as verbatim per-box-shape parts.
  - As a result the bindings are 100-201 lines, not ~20-line stubs.
- **Step 3, `constexpr` shared-memory constants.** Not done. The window
and scratch constants stay `-D` values with `#ifndef` defaults and no
`#error` guards.
- **Step 6, remaining scan twins.**
- The sample-fit (`f0` / `f1`) pairs differ by 48-57 lines. This round
cannot reproduce them with `-D` flags and `#if` arms.
  - The two cross-architecture pairs stay separate sources.
- Scan kernel translation units go from 37 to 28, not to the issue's
~14.
- **Step 6, benchmark.** The "within noise" check for rows P1, P2,
S1-S8, C1-C3 and V1-V3 was not run. This PR relies on the per-entry SASS
gate and unchanged launch paths, not on a measured benchmark.
- **Step 7 and the dead `POLICY` values.** Neither is done, and `POLICY`
is untouched.
- Manifest slimming: per-entry `gencode`, constant `entry` /
`nvcc_flags_if` and derivable `path`. This needs the loader's owner.
- The optional dead `POLICY` values: `rank_window_variants` 131072 /
262144 / 524288, `rank_window_variants_seg_only`, two-level 1048576 and
`rank_rule[1]`.
- **Step 8, `candidate_multiplier` knob hole.** Not confirmed on a GPU
and not clamped. The policy enumeration records the knob rows of base
and head and requires them to be identical; it does nothing more.
- **Step 9, narrow-snake sm_107a programs.** The conditional deletion of
the two programs is not done. This PR retires no program: every removed
source is a line-identical fold with its own SASS row.
- **SM107 hardware.** The sm_107a tests and the load-all check did not
run on a CC 10.7 GPU. All 106 SM107 rows (53 SASS + 53 host) are
compile-only.
- **Other deferred items.**
- The cross-package copies of `cake_build.py`, `cake_ffi_checks.h` and
the device helpers.
  - The `flashinfer/aot.py` entries.

```experimental-tests
tests/experimental/test_cake_dsa_indexer.py
tests/experimental/test_cake_dsa_indexer_api.py
```

Part of #6656

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
* Consolidated Cake DSA indexer launchers and shared descriptor helpers
while preserving program-specific kernel and launch configurations.
* Removed several specialized indexer implementations and their
associated entry points.
  * Cached validated dispatch policies for each architecture.

* **Documentation**
* Updated package guidance to explain shared sources, per-program build
settings, and binding-specific launch geometry.

* **Tests**
* Added checks for distinct kernel symbols and host bindings across
programs, and for one-time policy validation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1b04b2d](https://github.com/flashinfer-ai/flashinfer/commit/1b04b2df2d2c6fff6897af8c77ce3d82f1897229)

- **作者**: eigen
- **时间**: 2026-10-19T23:26:26Z
- **提交信息**: feat(cake_rmsnorm_train): add H1536 / H4096 forward and backward routes (SM100 / SM103 / SM107) (#6792)

`cake_rmsnorm_train` (`flashinfer.cake_rmsnorm_train`) is Cake's family
of RMSNorm training kernels in FlashInfer. All of them use one data
type: BF16 activations and weight, FP32 statistics (`rstd`) and an FP32
weight gradient from a deterministic (fixed-order, atomic-free)
reduction. Cake ships four variants: the plain forward (`y`, `rstd`),
the plain backward (`dx`, `dweight`), and the residual-fused forward and
backward. This PR adds the plain forward and backward at two new hidden
sizes, H=1536 and H=4096, on sm_100a (GB200/B200), sm_103a (GB300) and
sm_107a (R200). That is 16 new programs and 32 new build entries, and
each architecture has its own tuned program table. The residual-fused
variants still reject these two widths. Every previously shipped program
is byte-for-byte unchanged.

No earlier Cake version covers these widths, so each row's baseline is
the fastest of five non-Cake implementations, measured in the same
process on the same GPU with PyTorch 2.14.1+cu130, Triton 3.8.0,
liger-kernel 0.8.4 and FlashInfer 0.7.2 (main): `torch.compile`
(inductor) RMSNorm forward/backward, eager FP32 autograd,
`torch.nn.functional.rms_norm` autograd (`F.rms_norm`), Liger-Kernel
RMSNorm (Liger) and `flashinfer.norm.rmsnorm` (forward rows only), with
the Fastest baseline column naming the winner. Latency is CUPTI
kernel-active time for a T × H input with a cold L2 before every launch,
taken as the median of 3 counterbalanced paired groups; `step` is
forward + backward, and Speedup is baseline latency / Cake latency, so a
value above 1.000x means Cake is faster.

At H=1536, T=256 the forward on GB200 (0.974x) and R200 (0.986x) is at
the kernel-launch latency floor and ties Liger. At H=4096, T=65536 the
forward on GB300 (0.998x) is at the DRAM bandwidth roofline and ties
`torch.compile`.

### NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.0 (Cake kernels compiled
with NVRTC 13.0; baselines run on the PyTorch CUDA 13.0 build)

| H | T | Pass | Cake (µs) | Fastest baseline | Baseline (µs) | Speedup
|
|---:|---:|---|---:|---|---:|---:|
| 1536 | 256 | fwd | 2.43 | Liger | 2.37 | 0.974x |
| 1536 | 256 | bwd | 5.57 | F.rms_norm | 9.76 | 1.753x |
| 1536 | 256 | step | 7.87 | F.rms_norm | 13.57 | 1.724x |
| 1536 | 1024 | fwd | 3.10 | Liger | 3.36 | 1.082x |
| 1536 | 1024 | bwd | 7.52 | F.rms_norm | 12.80 | 1.702x |
| 1536 | 1024 | step | 10.43 | torch.compile | 16.13 | 1.546x |
| 1536 | 4096 | fwd | 6.14 | flashinfer.norm.rmsnorm | 6.66 | 1.083x |
| 1536 | 4096 | bwd | 13.09 | torch.compile | 22.11 | 1.689x |
| 1536 | 4096 | step | 19.33 | torch.compile | 29.79 | 1.541x |
| 1536 | 14928 | fwd | 15.46 | flashinfer.norm.rmsnorm | 16.96 | 1.097x
|
| 1536 | 14928 | bwd | 30.40 | torch.compile | 59.49 | 1.957x |
| 1536 | 14928 | step | 45.66 | torch.compile | 78.75 | 1.725x |
| 1536 | 15288 | fwd | 15.87 | flashinfer.norm.rmsnorm | 16.93 | 1.067x
|
| 1536 | 15288 | bwd | 31.01 | torch.compile | 61.50 | 1.983x |
| 1536 | 15288 | step | 46.72 | torch.compile | 81.15 | 1.737x |
| 1536 | 15566 | fwd | 16.45 | flashinfer.norm.rmsnorm | 18.14 | 1.103x
|
| 1536 | 15566 | bwd | 31.39 | torch.compile | 62.37 | 1.987x |
| 1536 | 15566 | step | 47.33 | torch.compile | 82.27 | 1.738x |
| 1536 | 15590 | fwd | 15.84 | flashinfer.norm.rmsnorm | 17.60 | 1.111x
|
| 1536 | 15590 | bwd | 31.81 | torch.compile | 61.66 | 1.939x |
| 1536 | 15590 | step | 47.42 | torch.compile | 82.05 | 1.730x |
| 1536 | 16114 | fwd | 16.54 | flashinfer.norm.rmsnorm | 17.95 | 1.085x
|
| 1536 | 16114 | bwd | 32.06 | torch.compile | 62.18 | 1.939x |
| 1536 | 16114 | step | 48.35 | torch.compile | 82.94 | 1.715x |
| 1536 | 16132 | fwd | 16.38 | flashinfer.norm.rmsnorm | 18.18 | 1.109x
|
| 1536 | 16132 | bwd | 32.10 | torch.compile | 63.74 | 1.986x |
| 1536 | 16132 | step | 48.26 | torch.compile | 85.02 | 1.762x |
| 1536 | 16164 | fwd | 16.74 | flashinfer.norm.rmsnorm | 18.08 | 1.080x
|
| 1536 | 16164 | bwd | 32.03 | torch.compile | 63.84 | 1.993x |
| 1536 | 16164 | step | 48.51 | torch.compile | 87.07 | 1.795x |
| 1536 | 16263 | fwd | 16.51 | flashinfer.norm.rmsnorm | 18.24 | 1.105x
|
| 1536 | 16263 | bwd | 32.22 | torch.compile | 68.51 | 2.126x |
| 1536 | 16263 | step | 48.48 | torch.compile | 90.08 | 1.858x |
| 1536 | 32768 | fwd | 30.82 | flashinfer.norm.rmsnorm | 32.35 | 1.050x
|
| 1536 | 32768 | bwd | 56.90 | torch.compile | 84.22 | 1.480x |
| 1536 | 32768 | step | 87.17 | torch.compile | 123.84 | 1.421x |
| 1536 | 65536 | fwd | 58.48 | flashinfer.norm.rmsnorm | 60.35 | 1.032x
|
| 1536 | 65536 | bwd | 105.09 | torch.compile | 209.70 | 1.995x |
| 1536 | 65536 | step | 163.20 | torch.compile | 285.66 | 1.750x |
| 4096 | 256 | fwd | 2.82 | Liger | 2.94 | 1.045x |
| 4096 | 256 | bwd | 6.98 | torch.compile | 12.70 | 1.821x |
| 4096 | 256 | step | 9.50 | torch.compile | 15.23 | 1.603x |
| 4096 | 1024 | fwd | 4.86 | flashinfer.norm.rmsnorm | 5.57 | 1.145x |
| 4096 | 1024 | bwd | 11.81 | torch.compile | 18.40 | 1.558x |
| 4096 | 1024 | step | 15.71 | torch.compile | 22.53 | 1.434x |
| 4096 | 4096 | fwd | 11.94 | flashinfer.norm.rmsnorm | 14.05 | 1.177x |
| 4096 | 4096 | bwd | 24.51 | torch.compile | 48.96 | 1.997x |
| 4096 | 4096 | step | 36.38 | torch.compile | 60.96 | 1.675x |
| 4096 | 14928 | fwd | 38.05 | flashinfer.norm.rmsnorm | 38.69 | 1.017x
|
| 4096 | 14928 | bwd | 71.65 | torch.compile | 118.21 | 1.650x |
| 4096 | 14928 | step | 107.33 | torch.compile | 157.60 | 1.468x |
| 4096 | 15288 | fwd | 38.50 | flashinfer.norm.rmsnorm | 39.58 | 1.028x
|
| 4096 | 15288 | bwd | 73.02 | torch.compile | 116.83 | 1.600x |
| 4096 | 15288 | step | 109.44 | torch.compile | 157.09 | 1.435x |
| 4096 | 15566 | fwd | 39.39 | flashinfer.norm.rmsnorm | 40.42 | 1.026x
|
| 4096 | 15566 | bwd | 74.46 | torch.compile | 119.71 | 1.608x |
| 4096 | 15566 | step | 111.58 | torch.compile | 160.51 | 1.438x |
| 4096 | 15590 | fwd | 39.30 | flashinfer.norm.rmsnorm | 40.26 | 1.024x
|
| 4096 | 15590 | bwd | 74.14 | torch.compile | 119.74 | 1.615x |
| 4096 | 15590 | step | 111.36 | torch.compile | 160.77 | 1.444x |
| 4096 | 16114 | fwd | 40.77 | flashinfer.norm.rmsnorm | 41.47 | 1.017x
|
| 4096 | 16114 | bwd | 76.58 | torch.compile | 122.43 | 1.599x |
| 4096 | 16114 | step | 114.82 | torch.compile | 164.32 | 1.431x |
| 4096 | 16132 | fwd | 40.03 | flashinfer.norm.rmsnorm | 41.34 | 1.033x
|
| 4096 | 16132 | bwd | 76.93 | torch.compile | 121.18 | 1.575x |
| 4096 | 16132 | step | 115.10 | torch.compile | 163.33 | 1.419x |
| 4096 | 16164 | fwd | 40.22 | flashinfer.norm.rmsnorm | 41.63 | 1.035x
|
| 4096 | 16164 | bwd | 76.51 | torch.compile | 120.93 | 1.581x |
| 4096 | 16164 | step | 114.69 | torch.compile | 163.13 | 1.422x |
| 4096 | 16263 | fwd | 40.35 | flashinfer.norm.rmsnorm | 41.70 | 1.033x
|
| 4096 | 16263 | bwd | 76.74 | torch.compile | 121.41 | 1.582x |
| 4096 | 16263 | step | 115.07 | torch.compile | 163.74 | 1.423x |
| 4096 | 32768 | fwd | 77.54 | flashinfer.norm.rmsnorm | 79.36 | 1.024x
|
| 4096 | 32768 | bwd | 145.98 | torch.compile | 172.77 | 1.183x |
| 4096 | 32768 | step | 221.76 | torch.compile | 251.90 | 1.136x |
| 4096 | 65536 | fwd | 150.75 | torch.compile | 152.99 | 1.015x |
| 4096 | 65536 | bwd | 283.52 | torch.compile | 319.30 | 1.126x |
| 4096 | 65536 | step | 432.73 | torch.compile | 470.53 | 1.087x |

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4 (Cake kernels compiled
with NVRTC 13.4; baselines run on the PyTorch CUDA 13.0 build)

| H | T | Pass | Cake (µs) | Fastest baseline | Baseline (µs) | Speedup
|
|---:|---:|---|---:|---|---:|---:|
| 1536 | 256 | fwd | 2.34 | Liger | 2.34 | 1.000x |
| 1536 | 256 | bwd | 5.47 | F.rms_norm | 9.66 | 1.766x |
| 1536 | 256 | step | 7.68 | F.rms_norm | 13.44 | 1.750x |
| 1536 | 1024 | fwd | 3.01 | Liger | 3.20 | 1.064x |
| 1536 | 1024 | bwd | 7.20 | F.rms_norm | 12.54 | 1.742x |
| 1536 | 1024 | step | 10.11 | torch.compile | 15.65 | 1.547x |
| 1536 | 4096 | fwd | 5.95 | flashinfer.norm.rmsnorm | 6.40 | 1.075x |
| 1536 | 4096 | bwd | 12.80 | torch.compile | 21.41 | 1.672x |
| 1536 | 4096 | step | 19.01 | torch.compile | 28.83 | 1.517x |
| 1536 | 14928 | fwd | 15.55 | flashinfer.norm.rmsnorm | 16.83 | 1.082x
|
| 1536 | 14928 | bwd | 30.30 | torch.compile | 57.47 | 1.897x |
| 1536 | 14928 | step | 45.66 | torch.compile | 75.84 | 1.661x |
| 1536 | 15288 | fwd | 15.62 | flashinfer.norm.rmsnorm | 16.83 | 1.078x
|
| 1536 | 15288 | bwd | 31.20 | torch.compile | 59.55 | 1.909x |
| 1536 | 15288 | step | 46.72 | torch.compile | 78.82 | 1.687x |
| 1536 | 15566 | fwd | 16.64 | flashinfer.norm.rmsnorm | 17.70 | 1.063x
|
| 1536 | 15566 | bwd | 32.00 | torch.compile | 59.46 | 1.858x |
| 1536 | 15566 | step | 48.22 | torch.compile | 78.98 | 1.638x |
| 1536 | 15590 | fwd | 16.06 | flashinfer.norm.rmsnorm | 17.41 | 1.084x
|
| 1536 | 15590 | bwd | 31.20 | torch.compile | 61.53 | 1.972x |
| 1536 | 15590 | step | 47.10 | torch.compile | 81.95 | 1.740x |
| 1536 | 16114 | fwd | 16.26 | flashinfer.norm.rmsnorm | 17.38 | 1.069x
|
| 1536 | 16114 | bwd | 31.81 | torch.compile | 74.56 | 2.344x |
| 1536 | 16114 | step | 48.00 | torch.compile | 96.03 | 2.001x |
| 1536 | 16132 | fwd | 16.67 | flashinfer.norm.rmsnorm | 17.47 | 1.048x
|
| 1536 | 16132 | bwd | 32.00 | torch.compile | 62.85 | 1.964x |
| 1536 | 16132 | step | 48.45 | torch.compile | 84.32 | 1.740x |
| 1536 | 16164 | fwd | 17.18 | flashinfer.norm.rmsnorm | 18.34 | 1.067x
|
| 1536 | 16164 | bwd | 31.94 | torch.compile | 60.32 | 1.889x |
| 1536 | 16164 | step | 48.80 | torch.compile | 83.04 | 1.702x |
| 1536 | 16263 | fwd | 16.64 | flashinfer.norm.rmsnorm | 17.89 | 1.075x
|
| 1536 | 16263 | bwd | 32.06 | torch.compile | 60.99 | 1.902x |
| 1536 | 16263 | step | 48.54 | torch.compile | 83.90 | 1.728x |
| 1536 | 32768 | fwd | 30.85 | flashinfer.norm.rmsnorm | 32.45 | 1.052x
|
| 1536 | 32768 | bwd | 57.50 | torch.compile | 80.64 | 1.402x |
| 1536 | 32768 | step | 88.19 | torch.compile | 118.48 | 1.343x |
| 1536 | 65536 | fwd | 59.30 | flashinfer.norm.rmsnorm | 60.61 | 1.022x
|
| 1536 | 65536 | bwd | 107.07 | torch.compile | 202.69 | 1.893x |
| 1536 | 65536 | step | 166.30 | torch.compile | 273.54 | 1.645x |
| 4096 | 256 | fwd | 2.82 | Liger | 2.94 | 1.045x |
| 4096 | 256 | bwd | 6.82 | torch.compile | 12.42 | 1.822x |
| 4096 | 256 | step | 9.31 | torch.compile | 14.85 | 1.595x |
| 4096 | 1024 | fwd | 4.80 | flashinfer.norm.rmsnorm | 5.44 | 1.133x |
| 4096 | 1024 | bwd | 11.42 | torch.compile | 17.76 | 1.555x |
| 4096 | 1024 | step | 15.17 | torch.compile | 21.62 | 1.425x |
| 4096 | 4096 | fwd | 12.10 | Liger | 13.73 | 1.135x |
| 4096 | 4096 | bwd | 24.10 | torch.compile | 47.84 | 1.985x |
| 4096 | 4096 | step | 36.06 | torch.compile | 58.94 | 1.634x |
| 4096 | 14928 | fwd | 37.55 | flashinfer.norm.rmsnorm | 38.72 | 1.031x
|
| 4096 | 14928 | bwd | 67.52 | torch.compile | 114.75 | 1.700x |
| 4096 | 14928 | step | 103.26 | torch.compile | 153.38 | 1.485x |
| 4096 | 15288 | fwd | 38.46 | flashinfer.norm.rmsnorm | 39.33 | 1.022x
|
| 4096 | 15288 | bwd | 68.99 | torch.compile | 113.09 | 1.639x |
| 4096 | 15288 | step | 105.22 | torch.compile | 152.19 | 1.446x |
| 4096 | 15566 | fwd | 39.10 | flashinfer.norm.rmsnorm | 40.00 | 1.023x
|
| 4096 | 15566 | bwd | 69.95 | torch.compile | 116.32 | 1.663x |
| 4096 | 15566 | step | 107.04 | torch.compile | 156.16 | 1.459x |
| 4096 | 15590 | fwd | 39.49 | flashinfer.norm.rmsnorm | 40.26 | 1.019x
|
| 4096 | 15590 | bwd | 69.86 | torch.compile | 116.19 | 1.663x |
| 4096 | 15590 | step | 107.07 | torch.compile | 155.94 | 1.456x |
| 4096 | 16114 | fwd | 40.29 | flashinfer.norm.rmsnorm | 41.50 | 1.030x
|
| 4096 | 16114 | bwd | 72.10 | torch.compile | 117.98 | 1.636x |
| 4096 | 16114 | step | 110.37 | torch.compile | 159.17 | 1.442x |
| 4096 | 16132 | fwd | 39.94 | flashinfer.norm.rmsnorm | 41.34 | 1.035x
|
| 4096 | 16132 | bwd | 72.99 | torch.compile | 118.02 | 1.617x |
| 4096 | 16132 | step | 111.17 | torch.compile | 159.14 | 1.431x |
| 4096 | 16164 | fwd | 40.16 | flashinfer.norm.rmsnorm | 41.82 | 1.041x
|
| 4096 | 16164 | bwd | 71.46 | torch.compile | 117.73 | 1.648x |
| 4096 | 16164 | step | 109.66 | torch.compile | 158.82 | 1.448x |
| 4096 | 16263 | fwd | 40.26 | flashinfer.norm.rmsnorm | 41.60 | 1.033x
|
| 4096 | 16263 | bwd | 72.29 | torch.compile | 118.46 | 1.639x |
| 4096 | 16263 | step | 110.85 | torch.compile | 159.87 | 1.442x |
| 4096 | 32768 | fwd | 77.66 | torch.compile | 78.85 | 1.015x |
| 4096 | 32768 | bwd | 136.06 | torch.compile | 168.64 | 1.239x |
| 4096 | 32768 | step | 212.22 | torch.compile | 247.04 | 1.164x |
| 4096 | 65536 | fwd | 152.45 | torch.compile | 152.16 | 0.998x |
| 4096 | 65536 | bwd | 262.11 | torch.compile | 311.49 | 1.188x |
| 4096 | 65536 | step | 413.06 | torch.compile | 462.91 | 1.121x |

### NVIDIA R200 (sm_107a, 212 SMs), CUDA 13.4 (Cake kernels compiled
with NVRTC 13.4; baselines run on the PyTorch CUDA 13.0 build)

| H | T | Pass | Cake (µs) | Fastest baseline | Baseline (µs) | Speedup
|
|---:|---:|---|---:|---|---:|---:|
| 1536 | 256 | fwd | 2.34 | Liger | 2.30 | 0.986x |
| 1536 | 256 | bwd | 5.22 | F.rms_norm | 9.06 | 1.736x |
| 1536 | 256 | step | 7.52 | torch.compile | 12.96 | 1.724x |
| 1536 | 1024 | fwd | 2.72 | flashinfer.norm.rmsnorm | 3.23 | 1.188x |
| 1536 | 1024 | bwd | 6.02 | F.rms_norm | 11.94 | 1.984x |
| 1536 | 1024 | step | 8.83 | torch.compile | 14.08 | 1.594x |
| 1536 | 4096 | fwd | 4.32 | torch.compile | 7.04 | 1.630x |
| 1536 | 4096 | bwd | 9.50 | F.rms_norm | 25.66 | 2.700x |
| 1536 | 4096 | step | 13.67 | F.rms_norm | 35.23 | 2.578x |
| 1536 | 14928 | fwd | 10.18 | torch.compile | 17.57 | 1.726x |
| 1536 | 14928 | bwd | 20.61 | torch.compile | 59.27 | 2.876x |
| 1536 | 14928 | step | 29.41 | torch.compile | 76.48 | 2.601x |
| 1536 | 15288 | fwd | 10.43 | torch.compile | 17.89 | 1.715x |
| 1536 | 15288 | bwd | 20.83 | torch.compile | 60.48 | 2.903x |
| 1536 | 15288 | step | 29.95 | torch.compile | 78.21 | 2.611x |
| 1536 | 15566 | fwd | 10.50 | torch.compile | 18.18 | 1.732x |
| 1536 | 15566 | bwd | 20.99 | torch.compile | 61.31 | 2.921x |
| 1536 | 15566 | step | 30.21 | torch.compile | 79.20 | 2.622x |
| 1536 | 15590 | fwd | 10.53 | torch.compile | 18.21 | 1.729x |
| 1536 | 15590 | bwd | 21.02 | Liger | 85.22 | 4.053x |
| 1536 | 15590 | step | 30.24 | torch.compile | 103.52 | 3.423x |
| 1536 | 16114 | fwd | 10.82 | torch.compile | 18.72 | 1.731x |
| 1536 | 16114 | bwd | 21.60 | torch.compile | 62.77 | 2.906x |
| 1536 | 16114 | step | 31.01 | torch.compile | 80.23 | 2.587x |
| 1536 | 16132 | fwd | 10.79 | torch.compile | 18.75 | 1.739x |
| 1536 | 16132 | bwd | 21.57 | torch.compile | 87.36 | 4.050x |
| 1536 | 16132 | step | 30.98 | torch.compile | 106.31 | 3.432x |
| 1536 | 16164 | fwd | 10.78 | torch.compile | 18.75 | 1.739x |
| 1536 | 16164 | bwd | 21.50 | Liger | 87.68 | 4.077x |
| 1536 | 16164 | step | 30.95 | torch.compile | 106.94 | 3.456x |
| 1536 | 16263 | fwd | 10.91 | torch.compile | 18.88 | 1.730x |
| 1536 | 16263 | bwd | 21.66 | torch.compile | 63.78 | 2.944x |
| 1536 | 16263 | step | 31.17 | torch.compile | 81.82 | 2.625x |
| 1536 | 32768 | fwd | 19.17 | torch.compile | 34.62 | 1.806x |
| 1536 | 32768 | bwd | 36.38 | torch.compile | 137.76 | 3.786x |
| 1536 | 32768 | step | 54.75 | torch.compile | 172.52 | 3.151x |
| 1536 | 65536 | fwd | 35.30 | torch.compile | 65.89 | 1.867x |
| 1536 | 65536 | bwd | 65.57 | torch.compile | 265.99 | 4.057x |
| 1536 | 65536 | step | 100.23 | torch.compile | 331.94 | 3.312x |
| 4096 | 256 | fwd | 2.69 | Liger | 2.75 | 1.024x |
| 4096 | 256 | bwd | 6.30 | torch.compile | 11.62 | 1.843x |
| 4096 | 256 | step | 9.15 | torch.compile | 13.41 | 1.465x |
| 4096 | 1024 | fwd | 3.71 | Liger | 4.90 | 1.319x |
| 4096 | 1024 | bwd | 8.58 | F.rms_norm | 16.10 | 1.877x |
| 4096 | 1024 | step | 12.00 | F.rms_norm | 21.86 | 1.821x |
| 4096 | 4096 | fwd | 8.29 | Liger | 11.04 | 1.332x |
| 4096 | 4096 | bwd | 16.71 | Liger | 41.86 | 2.506x |
| 4096 | 4096 | step | 25.47 | Liger | 52.93 | 2.078x |
| 4096 | 14928 | fwd | 22.66 | Liger | 32.29 | 1.425x |
| 4096 | 14928 | bwd | 45.12 | torch.compile | 108.42 | 2.403x |
| 4096 | 14928 | step | 67.14 | torch.compile | 141.28 | 2.104x |
| 4096 | 15288 | fwd | 22.78 | Liger | 32.74 | 1.437x |
| 4096 | 15288 | bwd | 45.19 | torch.compile | 110.40 | 2.443x |
| 4096 | 15288 | step | 67.68 | torch.compile | 143.75 | 2.124x |
| 4096 | 15566 | fwd | 23.14 | Liger | 33.28 | 1.438x |
| 4096 | 15566 | bwd | 47.11 | torch.compile | 112.23 | 2.382x |
| 4096 | 15566 | step | 69.44 | torch.compile | 146.02 | 2.103x |
| 4096 | 15590 | fwd | 23.26 | Liger | 33.15 | 1.425x |
| 4096 | 15590 | bwd | 47.55 | torch.compile | 112.23 | 2.360x |
| 4096 | 15590 | step | 70.34 | torch.compile | 146.24 | 2.079x |
| 4096 | 16114 | fwd | 23.84 | Liger | 34.34 | 1.440x |
| 4096 | 16114 | bwd | 47.36 | torch.compile | 113.63 | 2.399x |
| 4096 | 16114 | step | 70.72 | torch.compile | 148.55 | 2.100x |
| 4096 | 16132 | fwd | 23.81 | Liger | 34.37 | 1.443x |
| 4096 | 16132 | bwd | 47.68 | torch.compile | 114.72 | 2.406x |
| 4096 | 16132 | step | 71.20 | torch.compile | 149.44 | 2.099x |
| 4096 | 16164 | fwd | 23.90 | Liger | 34.34 | 1.436x |
| 4096 | 16164 | bwd | 47.43 | torch.compile | 114.88 | 2.422x |
| 4096 | 16164 | step | 71.27 | torch.compile | 149.60 | 2.099x |
| 4096 | 16263 | fwd | 24.06 | Liger | 34.53 | 1.435x |
| 4096 | 16263 | bwd | 47.62 | torch.compile | 115.33 | 2.422x |
| 4096 | 16263 | step | 71.36 | torch.compile | 150.56 | 2.110x |
| 4096 | 32768 | fwd | 44.26 | torch.compile | 64.64 | 1.461x |
| 4096 | 32768 | bwd | 87.30 | Liger | 218.98 | 2.508x |
| 4096 | 32768 | step | 130.85 | Liger | 285.12 | 2.179x |
| 4096 | 65536 | fwd | 85.89 | torch.compile | 124.45 | 1.449x |
| 4096 | 65536 | bwd | 182.21 | torch.compile | 328.26 | 1.802x |
| 4096 | 65536 | step | 267.83 | torch.compile | 453.42 | 1.693x |

The other Cake variants of this kernel are the residual-fused forward
and backward (H=6144) and the plain forward and backward at H=512, 2048
and 6144; the family ships on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added Cake RMSNorm training support for hidden sizes 1536 and 4096,
including forward and backward operations.
  * Added kernel coverage for SM100a, SM103a, and SM107a architectures.
* **Tests**
* Expanded validation across additional hidden sizes, epsilon settings,
row counts, and input scales.
* Added checks for weight alignment behavior in forward and backward
operations.
* **Benchmarks**
* Added the new hidden sizes and epsilon settings to the training
benchmark configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1c26cfa](https://github.com/flashinfer-ai/flashinfer/commit/1c26cfadba2cf6cf4af91bdc2e08f6dc4f9c5a9b)

- **作者**: eigen
- **时间**: 2026-10-19T23:22:54Z
- **提交信息**: perf(cake_all_gather_matmul): SM103a spill-split pair twins for gate/up (#6624)

This is a regenerated export of the Cake all-gather matmul backend. On
SM103a (B300), it routes two bf16 K-major gate/up shapes with 512 padded
rows to `cg2s2`, a spill-split variant of the CTA-pair twin, and adds
the two programs for them. It also replaces the positional CTA-pair flag
of the host ABI with a form code. SM100a (B200) routes and programs are
unchanged.

This PR builds on the previous PR of this series (SM103a 16-CTA push and
world-size-2 CTA-pair points). That PR builds on the SM100a CTA-pair
points PR. Neither of the two is merged yet. The branch
`cake-agmm-sm103a-spill-split-pairs-push-rows` was created from the
previous PR's branch `cake-agmm-sm103a-push-rows-ws2-pairs`, and the PR
targets `main` so that CI runs. Until the earlier PRs merge, the GitHub
diff also contains their commits. This PR's own change consists of:

- the spill-point tables in the loader;
- the form code in the host ABI;
- the two `cg2s2` programs;
- the regenerated host sequences;
- the tests.

Please merge it after the previous PR.

The change has two parts:

1. **SM103a spill points.** A new per-architecture table lists (world
size, dtype, layout, padded rows, N, form) points. SM103a lists two
points, both bf16 K-major and both of form `cg2s2`: TP4 gate/up at M=512
(world size 4, N=14336) and TP8 gate/up at M=512 (world size 8, N=7168).
SM100a lists none. Two SM103a programs are added,
`main_bfloat16_ws4_k_major_cg2s2` and `main_bfloat16_ws8_k_major_cg2s2`,
so the kernel set grows from 26 to 28 programs.
2. **Form code in the host ABI.** The positional `main_cg2` flag becomes
the form code `main_form` on both host entries: 0 one-CTA, 1 pair, 2
`cg2s1`, 3 `cg2s2`. The shared sequence template changes with it, so all
24 generated host sequences change text.

The timings come from paired runs on two 8×B300 nodes. Each ratio is the
comparison arm's time divided by the candidate's time, so a value above
1 means the candidate is faster. The same-code control arm runs the
CTA-pair twin on these shapes. Against it, the two-tile form `cg2s2`
read +2.3 % / +2.3 % on TP4 gate/up and +3.8 % / +3.7 % on TP8 gate/up
(node 1 / node 2). Against the reference program, the ratios are 1.0954
/ 1.1044 and 1.0883 / 1.0837. On every rank, outputs are bitwise
identical to the reference program. The TP4 gain is at the edge of the
combined noise, and the gain is adopted as measured. A third candidate
point is not adopted: TP4 QKV at 1024 padded rows × 2560 read +3.9 % on
node 1 and −0.1 % on node 2. *Disclosures* covers four items:

- the TP4 gain at the noise edge;
- the suspended third point;
- the control arm's offset against the reference program;
- a repeated export step.

## Routing and kernel changes

### SM103a spill points

The backend's kernel module gains a frozen per-architecture table,
`CG2_SPILL_POINTS_BY_ARCH`. Each point has this form:

`(world_size, dtype, layout, padded_rows, n, form)`

Padded rows is the row count rounded up to a multiple of 128. The table
refines the existing CTA-pair rule. A call runs the form of a point only
if both of these hold:

- the call qualifies for the CTA-pair twin under the region rule;
- its world size, dtype, layout, padded rows and N match the point.

Every point is checked at import. It must belong to a K-major class, lie
on the 128 / 256 grid, name a spill form, lie inside a pair rectangle of
its class, and appear only once. The kernel module looks points up with
`cg2_spill_point_form` and `cg2_spill_points`.

| architecture | points |
|---|---|
| SM100a (B200) | none |
| SM103a (B300) | `(4, bfloat16, k_major, 512, 14336, cg2s2)`, `(8,
bfloat16, k_major, 512, 7168, cg2s2)` |

The two spill forms:

- `cg2s2` is the spill-wave N-split variant of the CTA-pair twin, with
two 256×128 spill tiles. Both points use it.
- `cg2s1` is the variant with four 256×64 spill tiles. It was measured
and is not adopted (see *Measurement*). It stays defined in the kernel
module, but no `cg2s1` program is delivered on any architecture.

The export delivers a spill twin only for a (class, form) pair that has
a point. Every point needs a routed inventory shape and a delivered pair
twin of its class. Today that means the world-size-4 and world-size-8
bf16 K-major `cg2s2` main programs on SM103a.

Two inventory shapes change program on SM103a. Both stay on the
copy-engine route:

| shape (per rank) | inventory label | program after this PR |
|---|---|---|
| TP4 gate/up: world size 4, bf16, K-major, M=512, N=14336 |
`llama_tp4_gate_up_bf16_m512_kmajor` | `main_bfloat16_ws4_k_major_cg2s2`
(was the CTA-pair twin) |
| TP8 gate/up: world size 8, bf16, K-major, M=512, N=7168 |
`llama_tp8_gate_up_bf16_m512_kmajor` | `main_bfloat16_ws8_k_major_cg2s2`
(was the CTA-pair twin) |

For a matching call, a point changes only three things: the route's
form, the sequence's compiled stage list and the launched symbol. The
launch configuration of both shapes is unchanged.

Each point is a single (padded rows, N) pair. The table uses padded
rows, so row counts that pad onto a point also select it. At N=14336
(world size 4) and N=7168 (world size 8), any M from 385 to 512 rows per
rank now selects the `cg2s2` twin. M=513 (padded to 640) and M ≤ 384 do
not. The adoption checks cover these neighbouring row counts for routing
and bitwise identity, not timing.

### Form code in the host ABI

- The host ABI's positional `main_cg2` flag becomes the form code
`main_form` on both host entries: 0 one-CTA, 1 pair, 2 `cg2s1`, 3
`cg2s2`. The loader computes it with `main_form_code`.
- The shared sequence template admits a spill code only when the class
ships that program. It launches every pair form with the CTA-pair twin's
cluster attribute.
- All 24 generated host sequences change text: form-code checks, spill
stand-in namespaces, `kMainFormCg*` constants and two extra
`TensorMapCache` slots.
- The SM103a bf16 K-major sequences at world sizes 4 and 8 also compile
the `cg2s2` twin.

### Shapes that keep their program

- Every SM100a call. SM100a lists no spill point.
- TP4 QKV at M=1024 (N=2560) on SM103a, the suspended third point. It
stays on the CTA-pair twin; see *Disclosures*.
- bf16 K-major calls at these N whose padded rows are not 512. For
example, 513 rows at world sizes 4 and 8 stay on the one-CTA K-major
program.
- Classes without a point, such as bf16 N-major 512 × 14336 at world
size 4 and fp16 K-major 512 × 7168 at world size 8.
- Every other SM103a inventory shape. The resolve table differs on
exactly the two gate/up shapes; see *This export*.

## Kernel set and loader surface

- **Kernels.** Two programs are added for SM103a:
`main_bfloat16_ws4_k_major_cg2s2` (world size 4, bf16, K-major) and
`main_bfloat16_ws8_k_major_cg2s2` (world size 8, bf16, K-major). These
are the `cg2s2` spill twins of the delivered CTA-pair twins of those
classes. The kernel set goes from 26 to 28 programs. No `cg2s1` program
is delivered.
- **Loader** (`flashinfer/jit/cake_all_gather_matmul.py`):
- new tables `CG2_SPILL_POINTS`, `CG2S_CLASSES`, `MAIN_FORMS` and
`PAIR_FORMS`, plus `main_form_code`. The export's route contract checks
them together with `main_form_code`;
  - `PUSH_LAUNCH_ROWS_BY_ARCH` is unchanged from the previous PR.
- **Host launch sources.** In the generated `csrc/.../*_sequence_*.cu`
sources, all 24 sequences change text as described above. The SM103a
bf16 K-major sequences at world sizes 4 and 8 also compile the `cg2s2`
twin.
- **Tests** (`tests/comm/test_all_gather_matmul_cake.py`):
- pins for the two points, the spill classes, the delivered route keys,
the loader tables and the form codes;
- a new
`test_cg2_spill_point_table_lists_the_measured_points_per_architecture`;
- the launch-ABI parametrization derives each point's form code from the
pinned point table `_CG2_SPILL_POINTS`.
`test_launch_passes_the_loader_tile_width_and_form_after_grid_z_on_both_routes`
covers the form code on both routes;
  - comments on the frozen region table are reworded (comments only).
- **File signature vs the base branch:** 2 added / 28 modified / 0
deleted, 5330 insertions and 1014 deletions, no stray files (signature
check `added=2 modified=28 deleted=0 other=0 stray=0 ok=1`). Added:
`csrc/cake_all_gather_matmul/cake_all_gather_matmul_b9a6204da826be87d972_kernel.cu`
(`main_bfloat16_ws4_k_major_cg2s2`) and
`…_9d5d20282a6a1082a079_kernel.cu` (`main_bfloat16_ws8_k_major_cg2s2`):
the SM103a spill-wave N-split CTA-pair main kernels of the bf16 K-major
world-size-4 and world-size-8 classes, 971 lines each. Modified: all 24
host sequence files — the two SM103a bf16 K-major classes that ship the
new twins +284/−39 each (they carry the twin's tensor-map encoders and
launch path), the other 22 +109/−39 each (form-code wording and the
spill-twin encoder stand-ins, which throw when a class ships no such
program); `…_device_common.cuh` (1 line); the loader
`flashinfer/jit/cake_all_gather_matmul.py` (+148/−23: the
per-architecture spill-point table, the form codes and the two kernel
entries); `flashinfer/comm/all_gather_matmul/cake_all_gather_matmul.py`
(+7/−6); `tests/comm/test_all_gather_matmul_cake.py` (+266/−48). ruff
0.12.8 check + format --check pass on the three python files
(verification only).

## Measurement

The A/B runs used two 8×B300 (SM103a) nodes, node 1 and node 2, with the
same protocol as the previous PR. The spill forms ran from a per-call
selection on the generator tree of this series. This PR expresses the
adopted form as the point table. The identity check under *This export*
compares the two.

A single-GPU entry probe ran before the two-node runs. It found
bitwise-identical outputs (12/12) and no new floating-point opcodes.

Timing protocol:

- interleaved paired A/B: 9 groups × 2 passes per arm, pooled to 18
groups, 200 ms per arm per group;
- CUPTI timing with a cold L2, the slowest rank per iteration, and SM
clocks recorded;
- a same-code control arm, which runs the CTA-pair twin on the three
candidate points;
- the control shapes of the previous PR.

Each ratio is the comparison arm's time divided by the candidate's time.
The noise bound is 2.8·sd(control)/√G with G = 18 pooled groups.

### Spill-split twins at the three candidate points

All three points are bf16 K-major. Values are node 1 / node 2.

| point (per rank) | inventory label | control arm vs reference |
four-tile vs control | two-tile vs control | two-tile vs reference |
outcome |
|---|---|---:|---:|---:|---:|---|
| world size 4, 512 × 14336 (TP4 gate/up) |
`llama_tp4_gate_up_bf16_m512_kmajor` | 1.0711 / 1.0794 | 1.011 / 1.016 |
1.023 / 1.023 | 1.0954 / 1.1044 | adopted (`cg2s2`) |
| world size 8, 512 × 7168 (TP8 gate/up) |
`llama_tp8_gate_up_bf16_m512_kmajor` | 1.0487 / 1.0453 | 1.028 / 1.038 |
1.038 / 1.037 | 1.0883 / 1.0837 | adopted (`cg2s2`) |
| world size 4, 1024 × 2560 (TP4 QKV) |
`llama_tp4_qkv_bf16_m1024_kmajor` | 1.0548 / 1.0980 | 0.919 / 0.880 |
1.039 / 0.999 | above 1 on both nodes | suspended; stays on the CTA-pair
twin |

- **Adoption rule against the reference program.**
- The two-tile arm passes. All three changed points read above 1 and
beyond the noise bound on both nodes.
  - The four-tile arm fails. TP4 QKV M=1024 read 0.9694 / 0.9658.
- **Judged against the control arm.** On these shapes, the control arm
differs from the reference program (see *Disclosures*), so the arms were
also judged against the control arm:
- TP8 gate/up: |ln| 0.036–0.037, well above the combined noise of about
0.019 in log ratio.
- TP4 gate/up: +2.3 % on both nodes. This is at the edge of the combined
noise, and the gain is adopted as measured.
- TP4 QKV M=1024: +3.9 % / −0.1 %. The two nodes disagree in sign, so
the point is suspended.
- **Noise bound** (log ratio): two-tile arm 0.0116 / 0.0155, four-tile
arm 0.0146 / 0.0181, control arm 0.0188 / 0.0135.
- **Four-tile variant (`cg2s1`).** Against the control arm, it read
0.919 / 0.880 (−8 % / −12 %) on TP4 QKV M=1024. On the two gate/up
points it read 1.011 / 1.016 and 1.028 / 1.038, against 1.023 / 1.023
and 1.038 / 1.037 for the two-tile form. It is not adopted, and no
four-tile program is delivered.
- **Per-call times.** These come from the all-shape pass; the two-tile
form is compared with the reference program:
  - TP4 gate/up: 376.4 / 371.1 µs vs 413.2 / 409.4 µs;
  - TP8 gate/up: 383.3 / 385.3 µs vs 416.2 / 418.5 µs.
- **No-regression check.** The check covers 45 timed shapes and requires
candidate ≥ exp(−bound). It found 0 failing shapes on both nodes, for
every arm.
- **Push launch-row candidate.** A world-size-8 launch row at 128 padded
rows was measured on two other 8×B300 nodes. It used 16 or 8 push CTAs
per peer with the wide push program. On TP8 gate/up M=125, it was slower
than the control arm on both nodes: 0.957 / 0.946 with 16 CTAs and 0.933
/ 0.923 with 8 CTAs. It is not adopted, so `PUSH_LAUNCH_ROWS_BY_ARCH` is
unchanged.

## Correctness

Measured tree, with the spill form selected per call:

- **Exactness.** On node 1, 18 launches over 102 rows had 0 failing:
outputs were bitwise identical to the reference program on every rank.
Routing and push launch were checked on all 102 rows, with 0 mismatches.
On both nodes, the bitwise check inside the timing runs passed 3/3,
outputs were deterministic, and routing had 0 mismatches for every arm.
- **Ad-hoc shapes.** 6/6 on node 1, with 0 mismatches.
- **compute-sanitizer.** synccheck and racecheck were run separately
with compute-sanitizer 13.4.92. Both had zero errors on 7/7 rows per arm
(node 1).
- **End-to-end.** The end-to-end test passed for each arm (node 1).

Adoption tree (the generator code behind this export):

- **Exactness and determinism.** Compared with an independent checkout
of the reference program `8b96a056`: pass: 6 launches (world sizes 2 / 4
/ 8, two independent torchrun runs each) over 34 rows, the bitwise-check
inventory rows and the controls of the three world sizes: 0 failing, 0
compare failures; routing checked on 34/34 rows with 0 mismatches; every
(row, rank) output SHA-256 equal to the reference program and equal
across the two runs (adoption check on an 8×B300 node,
2026-10-17T03:23–03:33Z, generator tree `e63e8de0`, reference program
built from an independent checkout of `8b96a056`). The two changed
shapes are not in that inventory list. Their programs are covered three
ways: by the ad-hoc rows 500 × 14336 (world size 4) and 500 × 7168
(world size 8) below, which pad onto the two points and run the `cg2s2`
programs bitwise against the reference; by the bitwise checks inside the
two-node timing runs on the exact shapes (3/3 on both nodes); and by the
identity check, which shows the table-selected programs are
byte-identical to the measured per-call selection.
- **Shapes around the points.** These are the identity check's ad-hoc
shapes on SM103a.
  - World size 4, bf16:
    - 500 × 14336 K-major, which pads onto the TP4 point;
    - 513 × 14336 K-major (padded to 640);
    - 512 × 14336 N-major;
    - 1000, 1025 and 125 × 2560 K-major.
  - World size 8:
    - 500 × 7168 K-major bf16, which pads onto the TP8 point;
    - 513 × 7168 K-major bf16;
    - 512 × 7168 K-major fp16;
    - 100 and 129 × 1280 K-major bf16;
    - 128 × 2048 N-major bf16.

Routing and bitwise identity: pass: 14 ad-hoc rows at world sizes 8 and
4, one anchor row each (TP8 QKV M=1025 K-major, TP4 QKV M=2048 K-major):
world size 8 bf16 K-major 100, 129, 500 and 513 × 1280 / 7168 (100 and
129 at N=1280; 500 and 513 at N=7168), 128 × 2048 N-major bf16, 512 ×
7168 K-major fp16; world size 4 bf16 K-major 1000, 1025 and 125 × 2560
and 500 and 513 × 14336, 512 × 14336 N-major bf16. 0 failing, routing
14/14 against the pinned expected kernel symbols (500 × 7168 and 500 ×
14336 resolve to the `cg2s2` twins; 513 rows to the one-CTA K-major
program; 1000 and 1025 × 2560 to the CTA-pair twin; 100, 125 and 128
rows to the 128-wide twins), outputs bitwise-identical to the reference
program and across replays on every row (same node,
2026-10-17T03:33–03:37Z)
- **compute-sanitizer.** synccheck and racecheck were run separately on
the four registered rows and the two gate/up shapes: pass:
compute-sanitizer synccheck and racecheck, run as separate processes
(never memcheck) with compute-sanitizer 13.4.92, on 6 rows: the four
registered rows (world size 2 1024×2048 N-major bf16, world size 4
512×2560 K-major bf16, world size 8 125×2048 N-major bf16 and 2048×1280
K-major bf16) plus the two changed shapes (world size 4 512×14336
K-major bf16, world size 8 512×7168 K-major bf16). synccheck: 6/6 rows 0
errors on every rank, plus the registered world-size-2 target once;
racecheck: 6/6 rows 0 hazards and 0 internal errors on every rank (same
node, 2026-10-17T03:37–03:47Z). The racecheck wrapper returned exit
status 1 although every row was clean; this is a known quirk of the
wrapper, which counts `ERROR SUMMARY` lines that racecheck does not
print, and the per-row logs are the evidence
- **End-to-end** (2 GPUs): pass: the generator's end-to-end
`all_gather_matmul` test with exactly 2 visible GPUs: 1 passed, 0
skipped, 27.6 s (same node, 2026-10-17T03:47Z)

## Disclosures

- **Same-code control arm vs the reference program.** On the three
candidate points, the same-code control arm read 1.0711 / 1.0794 (TP4
gate/up), 1.0487 / 1.0453 (TP8 gate/up) and 1.0548 / 1.0980 (TP4 QKV
M=1024) against the reference program. Outputs were bitwise identical,
but these offsets were flagged as significant. The current tree already
runs the CTA-pair twin on these shapes (adopted earlier in this series),
while the reference program runs the one-CTA program. This is not a
same-program comparison. The arms were therefore judged against the
same-code control arm as well as against the reference program.
- **TP4 gate/up gain at the noise edge.** Against the control arm, the
TP8 gate/up gain (|ln| 0.036–0.037) is well above the combined noise of
about 0.019 in log ratio. The TP4 gate/up gain is +2.3 % on both nodes,
which is at the edge of the combined noise. That gain is adopted as
measured.
- **Suspended third point.** The same runs measured a third bf16 K-major
point at world size 4: TP4 QKV with 1024 padded rows × N=2560
(`llama_tp4_qkv_bf16_m1024_kmajor`). Against the same-code control arm,
the two-tile form read +3.9 % on node 1 and −0.1 % on node 2. The sign
disagreement is unexplained. The point is not adopted: the shape stays
on the CTA-pair twin, and the tests assert that the table does not list
it. It remains a candidate for a later re-measurement.
- **Padded rows vs measured rows.** The two points were measured at
exactly M=512. The table selects by padded rows, so at N=14336 (world
size 4) and N=7168 (world size 8), any M from 385 to 512 selects the
`cg2s2` twin. The adoption checks cover such neighbours (500 rows at
both world sizes) for routing and bitwise identity, not timing.
- **Export step repeated.** The first attempt of the export step on the
adoption tree hit a storage-quota failure while it checked out the
FlashInfer target tree, before the export ran. The export step was
repeated after the quota was cleared. The earlier correctness steps on
the adoption tree (exactness, ad-hoc shapes, compute-sanitizer,
end-to-end) were not repeated.
- **Racecheck wrapper exit status.** On the adoption tree, the racecheck
wrapper returned exit status 1 even though all 6 rows reported zero
hazards and zero errors. This is a known quirk in how the wrapper counts
the tool's `ERROR SUMMARY` lines, and the run is classified as zero
errors.

## This export

- **SM100a (B200).** `CG2_SPILL_POINTS_BY_ARCH` has no SM100a point, and
no SM100a program is added. SM100a routes and programs are unchanged.
- **Generator identity check.** This compares the export's generator
tree with the generator tree the measurements ran on:
- the SM103a resolve table differs on exactly the two gate/up shapes:
pair form → `cg2s2`, with the launch unchanged. SM100a has no changed
shape;
- of the ad-hoc shapes, exactly the two that pad onto a point change, to
the `cg2s2` twin: 500 × 14336 at world size 4 and 500 × 7168 at world
size 8, both bf16 K-major. The other ten SM103a shapes and the four
SM100a shapes resolve as before;
- the table path selects the same program as the per-call selection used
in the measurements, and the push launch surface is identical.
- **Generator source vs this export.** The export gate (floor 0.95,
bitwise-identical outputs) compares the generator source with this
export on the two changed shapes at world sizes 4 and 8: pass: 2/2
changed SM103a shapes (8×B300, 2026-10-17T05:25–05:38Z; clang-format
19.1.1 ok), ratio = generator-source time / export time with a floor of
0.95 and bitwise-identical outputs on both: world size 4 TP4 gate/up
bf16 M=512 K-major 0.9922 (0.3568 / 0.3596 ms, route
`ws4_bfloat16_k_major_ce_cg2s2`); world size 8 TP8 gate/up bf16 M=512
K-major 1.0023 (0.3628 / 0.3619 ms, route
`ws8_bfloat16_k_major_ce_cg2s2`). The exporter's summary reads
`all_passed=False complete=False` only because the two changed shapes,
not the whole catalog, were selected
- **FlashInfer tests.** Against the exported tree: pass on the exported
tree: FlashInfer CPU tests 359 passed / 0 failed / 0 errors / 0 skipped
(3.4 s); end-to-end `all_gather_matmul` tests 3 passed at 8 visible GPUs
(72 s), 3 passed at 4 (43 s) and 3 passed at 2 (29 s) (8×B300,
2026-10-17T05:38–05:40Z). On the PR head
(`691b263da50e64a31a1d2e33a1a61244472ce200`): pass
(2026-10-17T07:51–08:03Z on an 8×B300 node): CPU suite 359 passed / 0
failed / 0 errors / 0 skipped; e2e `-k all_gather_matmul` 3 passed (116
s) with 8 visible GPUs, 3 passed (84 s) with 4 and 3 passed (71 s) with
2 (`FIPR_TESTS_DONE rc=0`, head `691b263d`). The PR-head tests ran once,
on the first node, with no retry.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added selectable matrix-multiplication execution options for supported
hardware and input shapes, including paired-CTA variants.
* Expanded SM-push routing to support additional architecture- and
shape-specific cases, including certain larger padded-row workloads.
* Launch selection now adapts to the device architecture and workload
shape, while retaining existing fallback routes when specialized options
are unavailable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e41b069](https://github.com/flashinfer-ai/flashinfer/commit/e41b069bab32e659cda5f3ac9c00ac8f3cbacb7d)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-19T23:12:49Z
- **提交信息**: feat(gemm): SM107 CuTe-DSL blockwise FP8 GEMM backend for gemm_fp8_nt_groupwise (#6508)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds an SM107 (Rubin) backend for `gemm_fp8_nt_groupwise`, the FP8 GEMM
with 1x128 activation scales and 128x128 weight scales. It is built on
the public CUTLASS 4.8 CuTe-DSL `SM107BlockwiseGemmKernel`. **No default
changes:** the new `backend="cute-dsl"` and `backend="auto"` are opt-in,
and the default stays `"cutlass"`.

**Problem.** On Rubin the only backend for this API is CUTLASS, built
for `sm_100f` rather than natively for SM107. Its kernel uses fixed
128x128 output tiles and never splits K. For large weights, the tile
count fills Rubin's SMs badly: either most SMs sit idle, or a mostly
empty last wave costs a full K loop.

**What this adds.**
- `flashinfer/gemm/kernels/blockwise_gemm_rubin.py` and
`blockwise_gemm_blackwell.py`: the vendored public CUTLASS 4.8 kernel
classes (NVIDIA/cutlass@0b55a2f6,
`examples/python/CuTeDSL/cute/{rubin,blackwell}/kernel/blockwise_gemm/blockwise_gemm.py`).
The Rubin class subclasses the Blackwell one. The example's tensor
setup, command-line and benchmark code was removed; kernel logic is
unchanged.
- `flashinfer/gemm/kernels/gemm_fp8_groupwise_sm107.py`, the launcher:
- **split-K** without touching the kernel: K is cut into `S` slices,
each passed as one entry of the kernel's batch mode through strided
views (no copies), and the FP32 partial results are summed;
- a small relative **wave-cost model** that picks the split factor and
the 1-CTA or 2-CTA tile;
  - input checks;
- one cached TVM-FFI compile per tile configuration, with symbolic
M/N/K.
- `gemm_fp8_nt_groupwise(backend="cute-dsl")`, SM107 only. It needs CuTe
DSL ≥ 4.8 and takes MN-major scales only, `(1, 128, 128)` granularity,
e4m3 inputs, N and K multiples of 128, and M a multiple of 4.
- `gemm_fp8_nt_groupwise(backend="auto")`, for callers whose M varies
per call (e.g. serving):
- On SM107 it runs `cute-dsl` for M > 32, which was faster on every
measured shape.
- For M ≤ 32 it runs `cute-dsl` only when N ≤ 8192 and K is short, long,
or split at least 4 ways. Everywhere else CUTLASS's small-M swap-AB
kernel is faster, so CUTLASS keeps those shapes.
- Off SM107, and whenever a `cute-dsl` requirement fails, it runs
`cutlass`.
  - Callers with a fixed M > 32 can simply pass `backend="cute-dsl"`.
- `flashinfer_benchmark.py` accepts `cute-dsl` / `auto` for
`gemm_fp8_nt_groupwise`.
- Tests: every `cute-dsl` tactic on large-K shapes, and `auto`
correctness plus the chosen backend for both scale layouts.

### Performance

Rubin (SM107), measured with `flashinfer_benchmark.py` (CUDA events,
CUDA graphs, cold L2), taking the faster of two passes. "main" is
`backend="cutlass"` (the default) and "PR" is `backend="auto"`. The
GB300 column uses the same benchmark command; GB300 runs `cutlass` in
both cases.

| Shape (M × N × K) | PR vs main on Rubin | Rubin vs GB300, main | Rubin
vs GB300, PR |
|---|---:|---:|---:|
| 512 × 8192 × 28672 | **1.37x** | 1.15x | **1.58x** |
| 32 × 8192 × 28672 | **1.15x** | 1.23x | **1.41x** |
| 48 × 9216 × 7168 | **1.16x** | — | — |
| 4 × 1024 × 7168 | **1.27x** | 1.28x | **1.63x** |
| 16 × 9216 × 7168 (`auto` keeps CUTLASS) | 0.97x | 1.31x | 1.28x |

The 0.97x row is the host-side cost of the `auto` heuristic on a shape
where it keeps CUTLASS; the kernel itself is unchanged.

| Sweep (same process) | Shapes | PR vs main | Slower shapes |
|---|---:|---:|---|
| `auto` vs `cutlass`, model-traced shapes | 86 | 1.15x geomean (within
0.5% of always picking the faster backend) | none |
| same rule, 28 shapes not used to fit it | 28 | 1.11x geomean | none |
| `cute-dsl` vs `cutlass`, M > 32 | 46 | 1.03–1.69x | none |

### Not addressed here

| Area | Status | What is left |
|---|---|---|
| M > 32 | Improved | Still below the expected Rubin scaling at large K;
further gains need kernel-side work in the CuTe-DSL blockwise kernel's
main loop. |
| M ≤ 32 | Mostly unchanged (`auto` keeps CUTLASS) | Needs a small-M
swap-AB variant of the Rubin blockwise kernel. |
| K-major scales | Unchanged (CUTLASS) | `cute-dsl` supports MN-major
scales only. |
| `group_gemm_fp8_nt_groupwise` | Unchanged | Needs split-K across
groups (new kernel or scheduler work). Running this kernel with one
batch entry per group gives 1.1–1.6x on smaller-K shapes, but the API
would need per-group M on the host. |

## 🔍 Related Issues

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually (`pre-commit run --files` on every
changed file) and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

On Rubin, before the rebase onto current main:
`test_groupwise_scaled_gemm_fp8.py -k 'auto or cute-dsl or
cute_dsl_sm107 or blockscale'` gave 391 passed, 125 skipped (K-major
`cute-dsl` cases). `--refcheck` passed on every benchmark row above, and
every sweep output matched the FP32 reference. CI is requested below for
this branch. Off SM107 nothing changes unless a caller opts in.

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

- **Vendored kernel.** `blockwise_gemm_rubin.py` /
`blockwise_gemm_blackwell.py` are the public CUTLASS 4.8 example kernels
with the harness removed, plus three `type: ignore` lines for mypy. They
need CuTe DSL ≥ 4.8 and use
`cutlass.utils.StaticPersistentTileScheduler`, which the DSL warns may
move in a future release.
- **The `auto` rule for M ≤ 32** was fitted on a single system. The
split-K model uses the live SM count, but its constants were fitted on
one SKU.
- **Known issue on main, not touched here:** CUTLASS
`gemm_fp8_nt_groupwise` with K-major scales returns wrong results at M ∈
{28, 32} for N 1024–8192. `auto` sends K-major scales to CUTLASS, as the
default does.
- The `mm_fp8` / `bmm_fp8` / `mm_fp4` selection changes moved to #6521,
which is independent of this PR.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for additional backends and automatic backend selection
for FP8 GEMM operations.
* Added a CuTe DSL backend for groupwise FP8 GEMM on SM107 hardware,
including support for split-K tactics.
  * Expanded autotuning options for FP8 matrix multiplication.
* **Bug Fixes**
* Improved backend selection to account for weight layout and hardware
support.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8a9cc3a](https://github.com/flashinfer-ai/flashinfer/commit/8a9cc3a0128cace7b7ce2c569b0c8b75da7f7c1a)

- **作者**: Hao Wang
- **时间**: 2026-10-19T23:09:31Z
- **提交信息**: fix(jit): reuse artifacts downloaded by concurrent workers (#6461)

<!-- .github/pull_request_template.md -->

## 📌 Description

When concurrent workers miss the same artifact cache entry, each
currently queues a download and atomically replaces the destination,
even after another worker has populated it. Recheck the requested
checksum under the existing download lock so waiting workers reuse that
artifact and preserve its file identity.

`get_artifact()` passes its checksum through a new optional keyword-only
`expected_sha256` argument to `download_file()`. Calls without that
argument retain unconditional download/copy behavior. Missing or
mismatched artifacts are still downloaded, and the warm-cache fast path
is unchanged.

## 🔍 Related Issues

Fixes #3507.

Related to #2987, specifically download coordination (item 2). This is a
narrow correction to the existing per-file lock, not the broader
sentinel redesign.

Duplicate-work check: #3368 addresses symlink creation; #5343 addresses
versioned include paths and explicitly excludes downloader rework. This
change addresses neither of those scopes. #4925 handles download
failures and native error propagation, rather than duplicate downloads.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

| Check | Result |
| --- | --- |
| Four simultaneous misses, absent or stale entry, before patch | Both
cases fail: 4 HTTP downloads instead of 1 |
| Same cases after patch | Pass: 1 download; all 4 readers receive
expected bytes |
| Entire `tests/test_artifacts.py` | 21 passed, 0 skipped |
| Pre-commit on both changed files | Passed, including mypy and Ruff |

Normal repository test command: `pytest tests/test_artifacts.py -q`.

Local validation used the exact checkout versions of `artifacts.py`,
`jit/cubin_loader.py`, and the full test file loaded into an existing
FlashInfer 0.6.18 / PyTorch 2.13.0+cu130 ARM64 environment. An isolated
pytest runner excluded the unrelated parent repository's test-skipping
configuration. The unmodified loader and patched loader were tested with
the same regression tests. These are CPU/filesystem tests with mocked
HTTP; no GPU kernels or full repository test suite were run.

The all-files checklist boxes are intentionally left unchecked:
validation ran `pre-commit run --files flashinfer/jit/cubin_loader.py
tests/test_artifacts.py` and the focused artifact suite.

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

The checksum recheck uses the existing `load_cubin()` policy, including
`FLASHINFER_CUBIN_CHECKSUM_DISABLED`. Atomic replacement remains in
place for artifacts that need downloading. Existing nonpositive-retry
behavior is preserved by explicitly returning `None` on the previous
fall-through path.

This fixes redundant replacement after concurrent misses. It does not
claim to resolve a particular NVCC duplicate-definition failure:
replacement was observed during TP4 startup, but replacement during the
compiler's header reads has not been established. No model, kernel, or
numerical changes are included.

AI assistance was used to implement, test, and review this change.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Artifact retrieval now reuses cached files that match the expected
checksum, avoiding unnecessary downloads.
* Simultaneous requests for the same uncached artifact now share a
single download, including when the cache is empty or outdated.
  * Valid zero-byte artifacts are reused from the cache.
  * Failed artifact loads are handled without returning invalid data.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [35a1056](https://github.com/flashinfer-ai/flashinfer/commit/35a10560da05517ceb5472ba90c88d53f9129a40)

- **作者**: Lee Yong Jun
- **时间**: 2026-10-19T22:44:26Z
- **提交信息**: feat: add CuTe-DSL backend for layernorm_quant (#4335)

## 📌 Description

`layernorm_quant` is the only norm quant routine still running on the
first-generation CUDA kernel only; `rmsnorm_quant` and
`fused_add_rmsnorm_quant` already default to CuTe-DSL kernels. This PR
ports `layernorm_quant` to CuTe-DSL and wires it as the default backend,
with the CUDA kernel kept as the `FLASHINFER_USE_CUDA_NORM` fallback.

The new `LayerNormQuantKernel` derives from `RMSNormQuantKernel`
(multi-row tiles, cluster reduction, cp.async staging, vectorized fp8
stores for both e4m3 and e5m2), with three deltas:

- LayerNorm needs two reductions (mean, then variance). The cluster path
reuses a single mbarrier by waiting on phase 0 and then phase 1, with a
cluster barrier in between; `cluster_reduce_multirow` and
`row_reduce_sum_multirow` gain an optional `phase` parameter (additive,
existing callers unchanged).
- gamma/beta are float32 while the input tile is fp16/bf16, so they are
loaded through a dedicated tiled copy whose value mode is split into
128-bit pieces, keeping the fragment flat order aligned with the input
fragment. Per-element scalar loads would serialize on L2 latency and
dominate the kernel time (0.63 TB/s at batch 1024, H=8192, versus 1.48
TB/s with a constant-gamma control). Partial (non power of two) tiles
keep predicated scalar loads.
- Tile tail columns are masked out of both reductions; cp.async does not
zero-fill predicated-off columns, and `diff = -mean` at padded positions
would otherwise leak `mean^2` into the variance.

The kernel also switches to 256 threads from H_per_cta >= 8192, one step
earlier than RMSNormQuantKernel: with one row per CTA, the two
reductions plus the gamma/beta loads leave too little parallelism to
hide latency, and the wider block lifts batch 1024, H=8192 from 0.88
TB/s to 1.24 TB/s.

API and test changes:

- `layernorm_quant` gains `enable_pdl` (honored by the CuTe-DSL backend;
the CUDA kernel does not support PDL) and dispatches like the other norm
quant routines. Input validation on the CuTe-DSL path mirrors the CUDA
error messages.
- One semantic difference: the CUDA kernel rounds the normalized value
to the input dtype before scaling, the CuTe-DSL kernel stays in fp32
until the fp8 cast. The fp32 behavior matches the trace reference; tests
and the benchmark compare each backend against its own reference.
- `test_layernorm_quant` and `test_layernorm_quant_invalid_inputs` are
parametrized over both backends (672 cases total, including
non-power-of-two H = 111 and 500 that exercise the tail masking).
- The benchmark routine times both backends in one process.

Measured on RTX 5090 (bf16 input, e4m3 output, CUPTI timing):

| batch | hidden | cuda | cute-dsl | speedup |
|---|---|---|---|---|
| 256 | 4096 | 0.40 TB/s | 0.55 TB/s | 1.38x |
| 1024 | 4096 | 0.58 TB/s | 1.16 TB/s | 1.99x |
| 4096 | 4096 | 0.67 TB/s | 1.44 TB/s | 2.14x |
| 256 | 8192 | 0.56 TB/s | 0.76 TB/s | 1.35x |
| 1024 | 8192 | 0.96 TB/s | 1.24 TB/s | 1.30x |
| 4096 | 8192 | 1.18 TB/s | 1.50 TB/s | 1.27x |
| 256 | 16384 | 0.67 TB/s | 0.81 TB/s | 1.20x |
| 1024 | 16384 | 1.09 TB/s | 1.23 TB/s | 1.14x |
| 4096 | 16384 | 1.33 TB/s | 1.50 TB/s | 1.13x |
| 1024 | 65536 | error | 1.47 TB/s | n/a |

At H=65536 the CUDA kernel fails with "invalid argument" at launch
(pre-existing block size limit); the CuTe-DSL kernel handles it through
cluster_n=2.

Also verified on RTX 5090: the software fp8 conversion path (force
compiled with use_hw_fp8=False) and the symbolic-stride compile variant
used when M*H exceeds INT32_MAX are bit-exact against the torch
reference, and the rmsnorm/fused_add_rmsnorm quant suites pass unchanged
with the reduction signature extension.

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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added CuTe DSL support for LayerNorm quantization alongside CUDA.
  * Added backend-aware execution with optional PDL support.
* Added FP8 quantization handling across supported compute capabilities.

* **Bug Fixes**
  * Improved backend-specific rounding and reference output handling.
* Added validation for required inputs and output properties when using
CuTe DSL.

* **Tests**
  * Expanded LayerNorm quantization coverage across CUDA and CuTe DSL.
  * Added handling for environments where CuTe DSL is unavailable.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Brian K. Ryu <bryu@nvidia.com>
Co-authored-by: Ka-Hyun Nam <knam@nvidia.com>

### [f442588](https://github.com/flashinfer-ai/flashinfer/commit/f4425885eddb6410557308d1b35a01c1a3fadd9b)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-10-19T22:39:01Z
- **提交信息**: fix(trace): derive mm_bf16_fp4 cute-dsl trace gates from the library predicate (#6270)

## 📌 Description

On SM107 (Rubin) the two `cute-dsl` cases of
`tests/trace/test_mm_bf16_fp4_reference_correctness.py` fail with
`AssertionError: assert <TraceTemplate> is <TraceTemplate>` at `assert
mm_bf16_fp4_trace_dispatch(**inputs) is tpl` (v0.7.2rc1 QA,
`unit_test_vr200 [0, cu134]`). #5308 admitted SM107 to the SM100-family
`cute-dsl` layout in `_prepare_cute_dsl`, `_compute_cute_dsl` and
`_cute_dsl_bf16_fp4_requirement`, but three trace-side gates kept the
older `((10, 0), (10, 3))` tuple: the template selection in the test and
the admission checks in `_mm_bf16_fp4_cute_dsl_init` and
`_mm_bf16_fp4_cute_dsl_sm100_init`. On CC 10.7 the test therefore
selects the SM12x template, whose init happily prepares weights,
`prepare_bf16_fp4_weights` returns the SM100 layout (uint8 weight, 6-D
scale view), and the layout-keyed dispatch correctly answers with the
SM100 template. The dispatch is right; the reference-side gating is
stale.

The fix adds one predicate, `_cute_dsl_uses_sm100_layout(major, minor)`
in `flashinfer/gemm/gemm_bf16_fp4.py`, and routes all six sites through
it: the three library copies of the tuple and the three trace-side
gates. The trace reference and the dispatch now derive from the same
predicate, so admitting the next architecture to the SM100 layout is a
one-line change that cannot leave the trace reference behind. No kernel
or dispatch behaviour changes. `gemm_bf16_fp4_blackwell.py` keeps its
own `((10, 0), (10, 3))`: that is the
`blackwell-native`/`blackwell-tiled` backend, declared for SM100/103
only, and unrelated to this issue.

## 🔍 Related Issues

Fixes #6232 (v0.7.2rc1 QA, VR200 / SM107 / cu134). The three stale gates
are the ones the issue points at; the PR fixes them through the shared
predicate rather than editing each tuple. Follow-up to #5308.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> `pre-commit run ruff-check` and `ruff-format` were run on the four
changed files inside the cu130 CI container and pass; the full
`--all-files` run was not executed.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Verified on a B200 (CC 10.0, cu130 CI container), base `f8935b997` vs
this branch; the fix changes no outcome on SM100. No SM107 device run
was possible (no Rubin GPU reachable), so the SM107 claim rests on the
issue's job log plus the capability-mock runs below, which reproduce the
exact assertion on base and clear it on the fix.

| check | base | fix |
|---|---|---|
| `tests/trace/test_mm_bf16_fp4_reference_correctness.py` (real CC 10.0)
| 7 passed / 12 skipped | 7 passed / 12 skipped, identical ids |
| same file, `cute-dsl` cases, compute capability mocked to (10, 7) at
the gate sites only | **2 failed**, the issue's `AssertionError: assert
<TraceTemplate> is <TraceTemplate>` | **2 passed** |
| same, mocked (10, 3) / (12, 0) / (9, 0) | 2 passed / 2 passed / 2
skipped | 2 passed / 2 passed / 2 skipped |
| gate-agreement script: `_prepare_cute_dsl` layout ->
`mm_bf16_fp4_trace_dispatch` vs which cute-dsl template init admits the
CC, over (9,0) (10,0) (10,3) (10,7) (12,0) (12,1) | 1 mismatch, at (10,
7) | all six agree |
| `tests/trace/test_template_init.py`, `test_template_registry.py`,
`test_fi_trace_template_consistency.py` | 454/235 skipped, 4, 902/2
skipped | identical |

The mock patches `torch.cuda.get_device_capability` and the
`gemm_bf16_fp4*` module bindings of `get_compute_capability`, so kernels
still compile for the real device; the (12, 0) rows exercised the SM12x
prepare path and kernel on the B200. `tests/gemm/test_mm_bf16_fp4.py`
was not re-run: the library change replaces three identical tuple
literals with a function returning the same values. The commit
cherry-picks cleanly onto `release-v0.7.2`.

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

`gemm_bf16_fp4_blackwell.py` still carries `((10, 0), (10, 3))`; that is
the `blackwell-native`/`blackwell-tiled` backend declared for SM100/103
only, so it was deliberately left alone. The mock plugin and
gate-agreement script are kept out of the tree (`tests/trace` has no
capability-mocking precedent); they can be promoted to a test if
reviewers want a permanent guard. A `/bot run
tests/trace/test_mm_bf16_fp4_reference_correctness.py` on the VR200 lane
is the real SM107 confirmation.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added consistent support for BF16×FP4 CuTe DSL layouts on SM100-family
GPUs, including compute capabilities 10.0, 10.3, and 10.7.
* **Bug Fixes**
* Corrected weight-format selection for these GPUs; other supported
architectures continue to use their existing format.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [bdcfa39](https://github.com/flashinfer-ai/flashinfer/commit/bdcfa394e51ad95e0e6daaccf2c7f3084bf319d5)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-19T22:34:32Z
- **提交信息**: perf(gdn): Rubin (SM107) chunked-prefill kernel subclass and SM107 fp32 decode launch config (#6507)

<!-- .github/pull_request_template.md -->

## 📌 Description

GDN (gated delta rule) chunked prefill and fp32 decode on SM107 (Rubin)
ran the Blackwell code paths unchanged and trailed the expected
Rubin-vs-GB300 speedup. This PR adds two SM107-only changes. SM100/SM103
code generation and launch configs are unchanged.

### 1. Rubin subclass of the chunked GDN prefill kernel

`RubinGatedDeltaNetChunkedKernel` is a thin subclass: the kernel body is
inherited from `GatedDeltaNetChunkedKernel`, and only the following are
specialized:

- **Arch tag** `sm_107`.
- **Initial-state load L1 policy: `EVICT_NORMAL`.** The Blackwell class
uses `NO_ALLOCATE`, which avoids polluting SM100's small effective L1.
SM107 has more L1 headroom, so neighbouring loads reuse sectors of the
same lines.
- **Register split without an initial state: 208 / 256 / 40** (compute
group 0 / compute group 1 / lightweight warps), up from 216 / 256 / 32.
This relieves spills in the lightweight warps; compute group 0 is
relieved by the packed math below. The total must stay at or below 504:
at 512 the register reallocation can never succeed and the CTA hangs on
SM107, so the constructor asserts it.
- **Packed f32x2 multiplies** for the `W * T * scale` epilogues
(`_scale_convert_shared_acc_fragment`).
- **A mixed bf16x2/f16x2 → f32x2 FMA** that fuses the inverse fragment's
up-convert with the per-column beta multiply
(`_apply_beta_upconvert_ainv`). It is one FMA-pipe instruction with RN
rounding.
- **TMEM stays at 512 columns.** SM107 allows 576, but deeper
accumulator rings measured neutral to negative.

f16 and bf16 both use the packed f32x2 multiply followed by a
round-to-nearest convert. A fused f16 multiply+convert+pack would round
toward zero and is not available in the current CuTe-DSL release, so it
is not used.

The base class gains the two hooks above and a class attribute
`state_load_l1c_evict_priority`. Its default keeps the existing code, so
SM100/SM103 output is unchanged. `gdn_prefill.py` picks the class per
device. The kernel variant is part of the in-process cache key and of
the on-disk specialization name; the `sm100` variant adds no suffix, so
existing artifact names do not change.
`FLASHINFER_GDN_SM107_PREFILL_KERNEL=sm100` forces the Blackwell class
on SM107 for A/B runs and bisection (documented in `CLAUDE.md`).

### 2. SM107 launch config for the fp32 pretranspose decode kernel

The pipelined pretranspose decode kernel splits each (batch, head) state
across 8 CTAs. Each CTA streams two 8-row V tiles with one tile in
flight. On SM107 a large grid of these CTAs keeps too few bytes in
flight per SM to saturate HBM. The stage count and CTAs-per-state are
now Constexpr kernel parameters, chosen per call by
`_decode_launch_config`:

| SM107 states (`B * HV`) | CTAs per state | stages | why |
|---|---:|---:|---|
| < 256 | 8 | 2 (default) | 4 CTAs per state under-fills the GPU |
| 256 – 3071 | 4 | 3 | neutral or faster at every swept size |
| ≥ 3072 | 4 | 5 (every V tile in flight) | faster at every swept size |

- The thresholds come from a GR100 sweep over `B` in [1, 512] × `HV` in
{32, 64}.
- Outputs and final states are bit-identical across all launch configs.
- Other architectures keep the default. GB300 was swept too: (3 stages,
4 CTAs) also helps there at 256–1024 states, but it is left for a
follow-up that validates B200.
- The default config adds nothing to the specialization name, so
existing artifacts keep their names.

### Performance

Measured with `benchmarks/flashinfer_benchmark.py` on the Qwen3-Next /
Qwen3.5 GDN shapes (head size 128, 16 Q/K heads, bf16 I/O, fp32 state).
Timing uses CUDA events with CUDA graphs and takes the minimum over 2
pass medians.

The main-vs-PR comparison ran against current `main` on GR100 (212 SMs).
Main and the PR alternated on the same GPU, 3 rounds each, and the whole
sequence was repeated independently on a second GPU of the same node.
Repeats agree to within run-to-run noise. The table shows the median
over both GPUs.

GB300 runs the unchanged SM100/SM103 path, so the GR100 vs GB300 column
moves only through the GR100 speedup. That cross-arch column depends on
which GR100 node is used; the PR-vs-`main` column does not.

| API | B | seq len | V heads | PR vs `main` (GR100) | GR100 vs GB300,
`main` | GR100 vs GB300, this PR |
|---|---:|---:|---:|---:|---:|---:|
| decode (T=1) | 128 | 1 | 32 | **1.13x** | 1.47x | 1.65x |
| MTP (T=4) | 128 | 4 | 32 | 1.00x | 1.49x | 1.49x |
| chunk prefill | 4 | 2048 | 32 | **1.15x** | 1.15x | 1.33x |
| chunk prefill | 1 | 2048 | 128 | **1.16x** | 1.13x | 1.31x |
| chunk prefill | 4 | 2048 | 128 | **1.19x** | 1.40x | 1.66x |
| chunk prefill | 8 | 2048 | 128 | **1.20x** | 1.42x | 1.71x |
| chunk prefill | 1 | 2200 | 128 | **1.16x** | 1.14x | 1.32x |
| chunk prefill | 4 | 2200 | 128 | **1.19x** | 1.39x | 1.66x |
| chunk prefill | 1 | 9216 | 128 | **1.13–1.18x** | 1.17x | 1.35x |

The last row's range comes from the two GPUs: the PR's result matches on
both, while `main` differs between them.

MTP is unchanged: this PR does not touch its kernel, which is limited by
the serial T=4 state update rather than by memory traffic.

## 🔍 Related Issues

Internal Rubin performance ticket IKL-544.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran `pre-commit run --files` on the
changed files: all hooks pass.)

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`tests/gdn/test_cute_dsl_kernel_cache.py` now covers the prefill kernel
variant and the decode launch config in the specialization names.
`tests/gdn/test_multistream_overlap.py` passes the new cache-key
argument.

Passed on GR100 (SM107):

- `test_prefill_delta_rule.py`, `test_prefill_state_indices.py`,
`test_prefill_qk_normalization.py`, `test_prefill_auto_backend.py`
- `test_decode_delta_rule.py`,
`test_decode_pretranspose_noncontiguous_pool.py`,
`test_decode_pretranspose_bf16_padded_pool.py`, `test_fused_decode.py`,
`test_decode_ucache.py`
- `test_cute_dsl_kernel_cache.py`, `test_multistream_overlap.py`,
`test_gdn_device_target.py`

The benchmark `--refcheck` rows pass on every shape.

After rebasing onto current `main`, I re-ran
`test_cute_dsl_kernel_cache.py`, `test_multistream_overlap.py`,
`test_gdn_device_target.py`, `test_decode_delta_rule.py`,
`test_prefill_auto_backend.py` and `test_prefill_state_indices.py` on
GR100: 499 passed. The 29 failures are all Cake GDN backend cases
(`backend="cake_gdn"`, or `auto` with a pooled state routed to Cake).
They fail with `nvcc fatal: Unsupported gpu architecture 'sm_107a'`
while compiling Cake `.cu` sources in my local container, so they are a
toolkit/image issue unrelated to this change.

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

- **SM100/SM103 are unaffected by construction.** The base-class hooks
contain the old loop bodies verbatim, the default L1 policy is the old
constant, and the decode config returns the old constants off SM107.
- **Single-sequence long prefill still has headroom.** The kernel runs
one persistent CTA per (sequence, value head), so 128 work items occupy
only 128 of Rubin's SMs. Rubin's gain on those rows is mostly the
SM-clock ratio. Closing that gap needs more CTAs per sequence (for
example, a V-split across a 2-CTA cluster); that is new kernel work, not
part of this PR.
- **Decode with an indexed state pool.** On `main`, `backend="auto"`
tries the Cake GDN decode first when the state is pooled. The new launch
config therefore applies to the non-pool path, and to the pool path
whenever Cake does not take the call.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a049856](https://github.com/flashinfer-ai/flashinfer/commit/a049856962945d33bc5c2c2af1c25a89de1edb33)

- **作者**: eigen
- **时间**: 2026-10-19T21:26:07Z
- **提交信息**: perf(cake_all_gather_matmul): SM103a 16-CTA push and ws2 CTA-pair points (#6606)

This is a regenerated export of the Cake all-gather matmul backend. It
changes the SM103a (B300) push launch for one world-size-4 row point and
adds SM103a CTA-pair points for four world-size-2 shapes. No kernel
program changes, and SM100a (B200) routes and programs are unchanged.

This PR builds on the previous PR of this series (SM100a CTA-pair
points). That PR builds on the SM103a gate/up PR and the SM103a
route-band PR. None of the three is merged yet. The branch was created
from the previous PR's branch `cake-agmm-sm100a-cg2-points`, and the PR
targets `main` so that CI runs. Until the earlier PRs merge, the GitHub
diff also contains their commits. This PR's own change consists of the
SM103a launch-row table, the three SM103a region points with their two
pair twins, and the regenerated host launch sources and tests. Please
merge it after the previous PR.

The change has two parts:

1. **SM103a push launch rows.** A new per-architecture table,
`PUSH_LAUNCH_ROWS_BY_ARCH`, sets the push launch for listed (world size,
padded rows) points. SM103a has one entry: at world size 4 with 512
padded rows, a call launches 16 push CTAs per peer instead of 8, using
the wide push program. SM100a has no entry. Only the push launch grid
changes.
2. **SM103a CTA-pair points for four world-size-2 shapes.**
`CG2_REGIONS["sm_103a"]` gains three single-point entries at 1024 padded
rows and N=2048: bf16 N-major, bf16 K-major and fp16 K-major. The
world-size-2 bf16 K-major and fp16 K-major pair twins are added for
SM103a, so the kernel set grows from 24 to 26 programs. The selection
rule and the pair program are unchanged.

The speedups come from paired runs on two 8×B300 nodes, where speedup =
reference time / candidate time. The three shapes with the new launch
row read 1.0852–1.1009, and the four world-size-2 shapes read
1.0100–1.0424. All seven are beyond the noise bound on both nodes. On
every rank, outputs are bitwise identical to the reference program. On
the four world-size-2 shapes, the same-code control arm drifted by about
as much as the two smaller effects, so read those two effects with that
drift in mind. A cluster preemption cut short node 1's run for those
four shapes, so node 1's dataset for them was re-measured completely on
a replacement 8×B300 node. *Disclosures* covers both points.

## Routing and kernel changes

### SM103a push launch rows

The new table is in the loader,
`flashinfer/jit/cake_all_gather_matmul.py`. Each
`PUSH_LAUNCH_ROWS_BY_ARCH` entry has this form:

`[world_size, padded_rows, ctas_per_peer, unroll]`

A call on the SM push route whose world size and padded rows match an
entry launches `ctas_per_peer` push CTAs per peer, using the push
program of that `unroll`. Unroll 8 is the wide push program, which is
already delivered. Padded rows is the row count rounded up to a multiple
of 128. Every other call keeps the payload rule:

- at least 4 MiB per peer: 8 CTAs with the wide program;
- otherwise: 32 CTAs with the narrow program.

| architecture | entries |
|---|---|
| SM100a (B200) | none |
| SM103a (B300) | `[4, 512, 16, 8]` |

On SM103a, world-size-4 calls on the SM push route with exactly 512
padded rows (385–512 rows per rank) now launch 16 push CTAs per peer.
That is 48 push CTAs over the 3 peers instead of 24. Only the push
launch grid changes: `push_ctas_per_peer` in the route metadata goes
from 8 to 16, and no kernel program changes. The generated host-side
launch sources (`csrc/.../*_sequence_*.cu`) carry the table as
`constexpr` arrays (`kPushLaunchRow*`) and `push_launch_row()`.

Three world-size-4 inventory shapes change their launch on SM103a:

| shape (per rank) | inventory label | timed shape |
|---|---|---|
| TP4 QKV, bf16, K-major, M=512, N=2560 |
`llama_tp4_qkv_bf16_m512_kmajor` | yes |
| fp16, K-major, 512×2560 | `kmajor_ws4_fp16_m512_n2560` | yes |
| bf16, N-major, 512×2560 | `ws4_packed_qkv_bf16_m512_n2560` | no |

A fourth world-size-4 shape also has 512 padded rows: TP4 gate/up at
M=512 (N=14336). It uses the copy-engine route, so the table has no
effect on it.

### SM103a CTA-pair points

`CG2_REGIONS["sm_103a"]` gains three entries in the existing schema:

`[world_size, dtype, b_layout, min_padded_rows, max_padded_rows,
min_cols, max_cols]`

The rule is unchanged. A call runs the CTA-pair twin only if some
rectangle of its class satisfies both of these conditions:

- `min_padded_rows ≤ ceil128(rows) ≤ max_padded_rows`;
- `min_cols ≤ N ≤ max_cols`.

The new SM103a entries:

| world size | dtype | B layout | padded rows | N | entry |
|---|---|---|---|---|---|
| 2 | bf16 | N-major | 1024 | 2048 | `[2, "bfloat16", "n_major", 1024,
1024, 2048, 2048]` |
| 2 | bf16 | K-major | 1024 | 2048 | `[2, "bfloat16", "k_major", 1024,
1024, 2048, 2048]` |
| 2 | fp16 | K-major | 1024 | 2048 | `[2, "float16", "k_major", 1024,
1024, 2048, 2048]` |

`CG2_CLASSES["sm_103a"]` gains the world-size-2 bf16 K-major and fp16
K-major classes. Their pair twins are now delivered for SM103a; see
*Kernel set and loader surface*.

Four inventory shapes move from the single-CTA main kernel to the
CTA-pair main kernel on SM103a:

- `perf_bf16_m1024`: bf16, N-major, 1024×2048;
- `tail_ws2_bf16_m1000_n2048`: M=1000, which pads to 1024;
- `kmajor_ws2_bf16_m1024_n2048`;
- `kmajor_ws2_fp16_m1024_n2048`.

SM103a now routes 10 inventory shapes to the CTA-pair kernel: 4 + 2 from
the earlier PRs, plus these 4. SM100a keeps its nine.

Each rectangle is a single point. The rule uses padded rows, so row
counts that pad onto a point also select it. At world size 2 and N=2048,
any M from 897 to 1024 rows per rank (padded rows 1024) now selects the
pair twin in these three classes. M=1025 (padded to 1152) and M ≤ 896 do
not. The adoption checks cover these neighbouring row counts for routing
and bitwise identity, not timing.

### Shapes that keep their launch

- every SM100a call: the SM100a launch-row table is empty, and the
SM100a region tables are unchanged;
- TP4 gate/up at M=512 on SM103a, which uses the copy-engine route;
- world-size-2 calls at N=2048 in these three classes with M=1025 or M ≤
896;
- every other SM103a inventory shape. The resolve table differs on
exactly the seven shapes above; see *This export*.

The push programs and the pair program are unchanged. On SM103a, this PR
changes only the push launch grid at one (world size, padded rows) point
and which calls select the pair twins.

## Kernel set and loader surface

- **Kernels.** No kernel program changes. Two CTA-pair twins are added
for SM103a: `main_bfloat16_ws2_k_major_cg2` (world size 2, bf16,
K-major) and `main_float16_ws2_k_major_cg2` (world size 2, fp16,
K-major). The kernel set goes from 24 to 26 programs, and the pair
program itself is unchanged.
- **Loader** (`flashinfer/jit/cake_all_gather_matmul.py`):
- new `PUSH_LAUNCH_ROWS_BY_ARCH`, with `push_launch_rows(arch)` and
`push_launch(padded_rows, dtype_bytes, *, world_size, arch)`;
  - `CG2_REGIONS["sm_103a"]` gains the three points;
- `CG2_CLASSES["sm_103a"]` gains the world-size-2 bf16 K-major and fp16
K-major classes;
  - `_cg2_regions` and `main_form` are unchanged.
- **Host launch sources.** The generated `csrc/.../*_sequence_*.cu`
sources carry the launch-row table as `constexpr` arrays
(`kPushLaunchRow*`) and `push_launch_row()`.
- **Tests** (`tests/comm/test_all_gather_matmul_cake.py`):
  - pins for the launch-row table and both SM103a tables;
- the inventory gains `tail_ws2_bf16_m1000_n2048` and
`kmajor_ws2_bf16_m1024_n2048`;
- the pair-rule test covers the world-size-2 classes. For N-major,
897…1024 select the pair twin, and 1025, 1152 and 1920 select the
one-CTA program. K-major is tested at the 1024 point;
  - the launch-row rule is tested on the three 512-row shapes.
- **Public API.** Unchanged.
- **File signature vs the base branch:** 2 added / 27 modified / 0
deleted, 2854 insertions and 391 deletions, no stray files. Added:
`csrc/cake_all_gather_matmul/cake_all_gather_matmul_d0fc2abec5d93b9a81ec_kernel.cu`
and `…_aa1b0acc28e1e23913d9_kernel.cu` (the SM103a world-size-2 K-major
CTA-pair main kernels, bf16 and fp16, 722 lines each). Modified:
`…_sequence_bfloat16_ws2_k_major_sm_103a.cu` and
`…_sequence_float16_ws2_k_major_sm_103a.cu` (+213/−18 each: the
pair-kernel program — kernel declaration, `kHasMainCg2`, cluster-of-2
launch attributes, 197632 B dynamic shared memory — for the new K-major
pair points); the other 22 sequences (+34/−14 each: the per-architecture
SM push launch-row table `kPushLaunchRow*` and the row-first launch
selection; the table lists exactly one row — 512 padded rows → 16 CTAs
per peer of the wide push program — in the four SM103a world-size-4
sequences and is empty in the other 20, whose launches are therefore
unchanged); `…_device_common.cuh` (+1/−1, helper-library count in a
comment, 46 → 48); `flashinfer/jit/cake_all_gather_matmul.py` (+77/−10:
`PUSH_LAUNCH_ROWS_BY_ARCH = {"sm_103a": [[4, 512, 16, 8]]}` with
`push_launch_rows()` / `push_launch()` mirroring the generated host
selection, the two new pair-kernel names, and the three world-size-2
points (bf16 N-major, bf16 K-major, fp16 K-major; padded rows 1024, N
2048) in the SM103a CTA-pair table);
`tests/comm/test_all_gather_matmul_cake.py` (+158/−36: launch-row and
pair-point expectations, incl.
`test_push_launch_rows_give_the_sm_103a_four_rank_512_row_calls_sixteen_wide_ctas`).
Three shared device helpers differed from the base only in their
copyright line and were left as on the base branch.

## Measurement

The A/B runs used two 8×B300 (SM103a) nodes, node 1 and node 2. For the
16-CTA arm, node 1 is the original node. For the world-size-2 region
points, node 1 is a replacement node, on which the complete node-1
dataset was re-measured with the same protocol and the same reference
program (see *Disclosures*). Both changes were measured on the generator
tree of the SM103a gate/up PR, whose SM103a programs are the ones this
PR exports:

- the 16-CTA arm ran from a per-call environment knob on that tree;
- the ws2 region points ran from an exact-M allow-list knob on that
tree.

This PR expresses both changes as tables: the launch-row table and the
padded-row region points. The generator identity check under *This
export* shows that, compared with the generator tree of the previous PR,
the adoption tree changes exactly these seven shapes on SM103a and
nothing on SM100a.

Timing protocol:

- interleaved paired A/B: 9 groups × 2 passes per arm, 200 ms per arm
per group;
- CUPTI timing with a cold L2, the slowest rank per iteration, and SM
clocks recorded;
- a same-code control arm;
- control shapes (`perf_bf16_m8192`, `perf_bf16_m65536` and their
world-size-4 counterparts), which stayed inside the 0.958–1.030 band on
every node: 0.9941–1.0090 in the 16-CTA runs, 0.9963–1.0034 in the
original ws2-point runs, and inside the band on the replacement node as
well.

The speedup is the reference time divided by the candidate time, so a
value above 1 means the candidate is faster. The noise bound is
2.8·sd(control)/√G. Under the adoption rule, every changed shape must
read ≥ 1 on both nodes and be significant on both.

### SM103a push launch rows (16 push CTAs per peer)

| shape (per rank, world size 4) | node 1 speedup | node 2 speedup |
beyond the noise bound |
|---|---:|---:|---|
| `llama_tp4_qkv_bf16_m512_kmajor` | 1.0991 | 1.1009 | both nodes |
| `kmajor_ws4_fp16_m512_n2560` | 1.1007 | 1.0856 | both nodes |
| `ws4_packed_qkv_bf16_m512_n2560` | 1.0852 | 1.0905 | both nodes |

- **Per-call times.** On the two timed shapes, candidate vs reference:
115.1 µs vs 125.2 µs and 115.1 µs vs 126.6 µs on node 1, and 117.2 vs
123.8 µs and 115.7 vs 126.9 µs on node 2.
- **Timeline attribution.** The gain is in the push span: 52.9–54.1 µs,
against 70.4–71.8 µs before.
- **32-CTA variant.** The same runs measured a 32-CTA variant, `[4, 512,
32, 8]`. It read 1.0714 / 1.0673 and 1.0894 / 1.0850 on the two timed
shapes. It was not better than 16 CTAs on either node, so it is not
adopted.
- **Same-code control.** On these three shapes, the same-code control
arm read +1.9 … +5.7 % against the reference program; see *Disclosures*.

### SM103a CTA-pair points (world size 2, N=2048)

| shape (per rank) | node 1 speedup | node 2 speedup | per-call time,
node 2 (µs, candidate vs reference) | beyond the noise bound |
|---|---:|---:|---:|---|
| `tail_ws2_bf16_m1000_n2048` | 1.0200 | 1.0239 | 89.0 vs 90.9 | both
nodes |
| `kmajor_ws2_bf16_m1024_n2048` | 1.0302 | 1.0368 | 90.4 vs 92.9 | both
nodes |
| `kmajor_ws2_fp16_m1024_n2048` | 1.0424 | 1.0247 | 90.8 vs 92.8 | both
nodes |
| `perf_bf16_m1024` | 1.0216 | 1.0100 | 91.2 vs 92.1 | both nodes |

Node 1 for these four shapes is the replacement node. The noise bound
was 0.0032–0.0039 in log ratio. On these four shapes, the same-code
control arm read −1.5 % … +1.2 %, which is of the same order as the two
smaller effects; see *Disclosures*.

### Both changes

- **Adoption rule.** Both changes pass. All seven changed shapes read
above 1 and are beyond the noise bound on both nodes.
- **No-regression check.** The check covers 45 timed shapes and requires
candidate ≥ exp(−bound). Identical-program shapes are exempt when
bitwise output, replay and kernel names match.
- 16-CTA arm: both nodes pass 45/45 after the exemption. One
identical-program shape, bf16 world size 2 at M=1024, missed by 0.001 on
both nodes and is exempt.
- ws2 region points: node 2 passes 45/45 after the exemption, with one
identical-program shape at margin −0.0000 that is exempt. On node 1 (the
replacement node), every world-size-2 and world-size-4 shape passes. Its
13 world-size-8 shapes were voided by that run's own same-code control;
under this change they are identical programs, and they pass on node 2.
No shape fails on both nodes. See *Disclosures*.

## Correctness

Measured trees, both changes, on the original node 1 and node 2:

- **Exactness.** For every changed shape, outputs are bitwise identical
to the reference program on every rank. Routing was checked and matched.
Outputs are deterministic across two independent launches. In the
bitwise run of each change, 32 of 32 launches were clean.
- **compute-sanitizer.** synccheck and racecheck were run separately.
Both report 0 errors on the registered rows and the changed rows, 6/6
rows per change per tool. One synccheck row of the ws2 region points did
not start on its first attempt, and its same-host re-run was clean on
6/6 rows; see *Disclosures*.
- **Skew pressure.** 0 failures on the two 16-CTA timed shapes.
- **End-to-end.** The end-to-end test passes.

Adoption tree (the generator code behind this export):

- **Exactness and determinism.** Compared with an independent checkout
of the reference program `8b96a056`: pass: 6 launches (world sizes
2/4/8, two independent torchrun runs each) over 34 rows (the seven
changed SM103a rows, the bitwise-check inventory rows and the controls),
0 failing, 0 compare failures; routing checked on 34/34 rows with 0
mismatches (adoption check on an 8×B300 node, 2026-10-16T16:31–16:40Z,
generator tree `653e21af`, reference program built from an independent
checkout of `8b96a056`; every (row, rank) output SHA-256 equal to the
reference and equal across the two runs)
- **Shapes around the points.** Ad-hoc shapes. World size 4: 500 and 513
rows × 2560 (K-major bf16), 512 × 4096 (K-major bf16), 512 × 2560
(N-major bf16) and 500 × 2560 (K-major fp16). World size 2: 896, 897,
1023 and 1025 rows × 2048 (N-major bf16); 1000 and 1025 × 2048 (K-major
bf16); 897 and 1025 × 2048 (K-major fp16); 125 × 2048 (N-major bf16);
and the N-neighbours of the three new points, 1024 × 1792 (N-major bf16)
and 1024 × 2304 (N-major bf16, K-major bf16 and K-major fp16), which
route to the non-pair programs. Routing and bitwise identity: pass: 16
ad-hoc rows at world sizes 4 and 2 (the shapes listed above, with one
anchor row each) — 0 failing, routing 16/16 against the pinned expected
kernel symbols, outputs bitwise-identical to the reference and across
replays (adoption check on an 8×B300 node, 2026-10-16T16:39–16:41Z). A
planned 1024 × 2176 N-major bf16 spec is not admissible to the harness
(N must be a multiple of 256) and did not launch; a supplementary check
on the same node (17:31–17:32Z) covered the N-neighbours of the three
new world-size-2 points instead — 1024 × 1792 N-major bf16 and 1024 ×
2304 N-major bf16 / K-major bf16 / K-major fp16, all routed to the
non-pair programs as expected — 5 rows, 0 failing, routing 5/5, bitwise
- **Skew pressure.** On the two 16-CTA shapes: pass: skew pressure on
the two changed world-size-4 timed shapes
(`llama_tp4_qkv_bf16_m512_kmajor`, `kmajor_ws4_fp16_m512_n2560`) — eager
and CUDA-graph-captured paths, 10000 iterations each, all ranks passed
with 0 mismatching iterations
- **compute-sanitizer.** synccheck and racecheck: pass:
compute-sanitizer synccheck and racecheck, run as separate processes
(never memcheck), on 8 rows: the four registered rows (world size 2
1024×2048 N-major bf16, world size 4 512×2560 K-major bf16, world size 8
125×2048 N-major bf16 and 2048×1280 K-major bf16) plus world size 4
512×2560 K-major fp16 and N-major bf16 and world size 2 1024×2048
K-major bf16 and fp16. synccheck: 8/8 rows 0 errors on every rank, plus
the registered world-size-2 target (2026-10-16T16:42–16:56Z). racecheck:
the first attempt (16:56–17:10Z) failed inside the tool — an older
compute-sanitizer build aborted on every rank with `Internal Sanitizer
Error: The Sanitizer failed to handle a hardware exception`, so it
produced no hazard verdict; the re-run with the current 13.4.92
sanitizer on the same node (17:42–17:47Z) is clean: 8/8 rows, 0 hazards
and 0 internal errors on every rank
- **End-to-end.** pass: the generator's end-to-end `all_gather_matmul`
test with exactly 2 visible GPUs: 1 passed, 0 skipped (same node,
2026-10-16T17:14Z)
- **Benchmark regression.** The registered bench-regression gates
(world-size-2 focus suite and the TP8 suite) pass against the live
cuTile reference, 1.465× and 1.283× with a floor of 1.0.

## Disclosures

- **Same-code control drift on the world-size-2 shapes.** The same-code
control arm runs identical programs in both arms. On the four
world-size-2 shapes, it read −1.5 % … +1.2 %. Two shapes read negative
on both nodes, one read positive on both, and one was split. This drift
is of the same order as the two smaller effects:
`tail_ws2_bf16_m1000_n2048` (+2.0 / +2.4 %) and `perf_bf16_m1024` (+2.2
/ +1.0 %). The two K-major effects exceed it: +3.0 / +3.7 % for bf16 and
+4.2 / +2.5 % for fp16. The adoption rule is met on both nodes, but the
two smaller effects should be read with that control drift in mind.
- **Same-code control on the three 512-row shapes.** On these shapes,
the same-code control arm read +1.9 … +5.7 % against the reference
program. That control compares the current tree with the older reference
program, which predates the wide push program delivered earlier in this
series, so its push program for these shapes differs. This is not a
same-program comparison, and it does not change the verdict.
- **Node-1 run cut short (ws2 region points).** On node 1, the run for
the ws2 region points was cut short by a cluster preemption 27 s into
the all-shape no-regression check. The node's allocation was preempted
after 5 h 04 min, and a first same-host repeat was preempted again after
4.5 min. A pinned allocation on the same host never started. The first
replacement node was unhealthy (NCCL initialization hung) and produced
no measurement. The node-1 dataset for the ws2 region points was
therefore re-measured completely on a different 8×B300 node, with the
same protocol and the same reference program. The re-measurement covered
the timing runs with the same-code control arm (both passes) and the
all-shape no-regression check. The node-1 numbers reported for those
four shapes come from that node. The earlier node's results for those
shapes agree in sign (1.0167–1.0613) and are supplementary. Completion
on the replacement node: complete on a replacement 8×B300 node (same
protocol, same reference program, 63.5 min). Two-node no-regression
check on the 45 timed shapes: 0 shapes fail on both nodes (strict or
after the identical-program exemption); the only strict one-node failure
is the node-2 shape `tp8_perf_bf16_m4096` at 0.9935 (identical program,
exempt); 13 world-size-8 shapes of the node-1 check were voided by their
own same-code control and are identical programs under this change, all
passing on node 2. The four changed world-size-2 shapes pass on both
nodes with margins of +2.2 % to +5.3 % above the significance floor.
- **Sanitizer row that did not start.** For the ws2 region points, the
synccheck row `ws2_1024_2048_k_major_bfloat16` did not start on its
first attempt because the torchrun rendezvous port was taken, so no
kernel ran. The same-host re-run was clean on 6/6 rows.
- **Racecheck tool failure on the adoption tree.** The first racecheck
run on the adoption tree failed inside the tool: an older
compute-sanitizer build aborted on every rank with `Internal Sanitizer
Error`, so it gave no hazard verdict. The re-run with the 13.4.92
sanitizer on the same node is clean on 8/8 rows.
- **Padded rows vs measured rows.** The ws2 region points were measured
with an exact-M allow-list. The region table selects by padded rows
instead, so at world size 2 and N=2048 any M from 897 to 1024 selects
the pair twin in these three classes. Likewise, on the SM push route,
385–512 rows per rank at world size 4 select the 16-CTA launch. The
adoption checks cover these neighbouring row counts for routing and
bitwise identity, not timing.

## This export

- **SM100a (B200).** `PUSH_LAUNCH_ROWS_BY_ARCH` has no SM100a entry, and
the SM100a entries of `CG2_REGIONS` and `CG2_CLASSES` are unchanged.
SM100a routes and programs are unchanged.
- **Generator identity check.** Against the previous PR's generator
tree:
- the resolve table differs on exactly the seven SM103a shapes: four by
pair form and three by `push_ctas_per_peer` 8 → 16. SM100a resolves
identically;
- the harness kernels (23 per architecture), their receipts and the 52
extra renders are byte-identical.
- **Generator source vs this export.** The export gate (floor 0.95,
bitwise-identical outputs) compares the generator source with this
export on the changed shapes at world sizes 4 and 2: pass: 7/7 changed
SM103a shapes, ratio = generator-source time / export time with a floor
of 0.95 and bitwise-identical outputs on every row (8×B300,
2026-10-16T17:14–17:29Z) — world size 4: TP4 QKV bf16 M=512 K-major
1.0051 (0.1146 / 0.1141 ms), fp16 M=512 K-major 0.9994 (0.1144 / 0.1144
ms), bf16 M=512 N-major (correctness row) 1.0013 (0.1118 / 0.1117 ms);
world size 2: bf16 M=1024 N-major 1.0000 (0.0894 / 0.0894 ms), bf16
M=1000 N-major 1.0053 (0.0888 / 0.0884 ms), bf16 M=1024 K-major 1.0000
(0.0896 / 0.0896 ms), fp16 M=1024 K-major 1.0011 (0.0899 / 0.0898 ms)
- **FlashInfer tests.** Against the exported tree: pass on the exported
tree: FlashInfer CPU tests 358 passed / 0 failed / 0 errors / 0 skipped;
end-to-end `all_gather_matmul` tests 3 passed at 8 visible GPUs and 3
passed at 2 visible GPUs, while at 4 visible GPUs one of three tests did
not start (torchrun rendezvous port collision on the node, no kernel
ran) — the complete 8/4/2 set is re-run on the PR head below. On the PR
head (`6c5ad929cde32295e80319fe7bddb72aae62986a`): pass
(2026-10-16T21:19–21:30Z on an 8×B300 node): CPU suite 358 passed / 0
failed / 0 errors / 0 skipped; e2e `-k all_gather_matmul` 3 passed with
8 visible GPUs (115 s), 3 passed with 4 (83 s) and 3 passed with 2 (70
s). A first attempt on a different node of the same pool stalled inside
NCCL communicator initialisation before any test body ran (no Cake code
executed, GPUs idle) and was cancelled after 20 minutes; the re-run
above on another node completed the full 8/4/2 set.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added an optional two-CTA main-kernel mode for supported all-gather
matrix multiplication workloads.
* Added architecture-specific routing for main-kernel selection and
SM-push eligibility, with tuned launch settings for selected workload
shapes.
* Expanded support for both bfloat16 and float16 workloads across
supported GPU architectures.
* **Tests**
* Added coverage for kernel routing, launch sizing, and
architecture-specific SM-push behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [65dde40](https://github.com/flashinfer-ai/flashinfer/commit/65dde4062100e77aca1b1ef5d83b2cc605b05d0f)

- **作者**: Mingyuan Ma
- **时间**: 2026-10-19T21:15:24Z
- **提交信息**: CuteDSL MegaMoe Optimization for DSV41 (#6499)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

This achieved about 10x less MoE time per decode step than FlashInfer
main for dsv4.1-flash workload.

## Commits

| # | commit | what it does | gate |
|---|---|---|---|
| 1 | fix(moe_ep/sm107): phase-interleave FC12 scheduler keeps
cluster-uniform state (EP deadlock) | Stops two CTAs of one cluster from
disagreeing on `fc1_exhausted`. Without it, the shared-expert overlap
with the phase-interleave schedule hung 3 of 3 vLLM boots during
adaptive-verification profiling. | always (phase-interleave schedule) |
| 2 | perf(moe_ep/sm107): an SM budget launches the MegaMoE as a uniform
cluster grid | `max_sm_count` now builds a workspace instead of raising,
so a side-stream shared-expert MLP can run next to the megakernel. |
only when `max_sm_count` is set |
| 5 | feat(quantization): nvfp4_quantize_cute_dsl can write into
caller-provided buffers (out=) | Adds an `out=` argument; the quantizer
itself is unchanged. | caller opt-in |
| 7 | perf(moe_ep/sm107): bind the per-call NVFP4 epilogue scalars as
launch arguments | Binds fc1/fc2 alpha and the fc1 norm constant as
launch arguments, removing 3 device copies per layer. | always (NVFP4) |
| 8 | perf(moe_ep/sm107): fold the caller's padding mask into the
one-launch route staging | Adds `MoEEpTensors.route_padding_mask`, so
callers drop their own masking kernel. | only when the caller sets the
field |

14 files, +726 / -56, on `main` 289557772.

The steps are cumulative from `main` (top) to this series plus the
companion vLLM change (bottom). Rows marked
*[vLLM]* belong to the companion vLLM change and are shown because the
steps were measured together. Columns are
tokens per rank @ workspace capacity.


| step | 1260 @ 3072 (µs) | 2046 @ 2048 (µs) | 2304 @ 3072 (µs) | 4608 @
6144 (µs) | MoE per step (ms) | output vs previous step |
|---|---|---|---|---|---|---|
| `main` (start) | 1892.8 | 2782.5 | 3098.0 | 5992.8 | 94.40 | – |
| #1 scheduler fix + #2 SM-budget launch (+ *[vLLM]* SM107 enablement) |
+0.2 | -0.2 | +1.0 | +0.1 | -0.001 | bit-identical |
| #7 bound epilogue scalars | -6.7 | -7.0 | -8.7 | -4.2 | -0.274 |
bit-identical |
| #8 padding-mask fold (+ *[vLLM]* hand-off), no padding rows | -0.2 |
-0.2 | 0.0 | -0.6 | -0.007 | bit-identical |
| **this series + vLLM change (end)** | **232.5** | **257.2** |
**265.8** | **438.4** | **9.82** | |




## 🔍 Related Issues

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
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
* Added faster staging for supported SM107 MoE routes and NVFP4 inputs,
with fallback handling for unsupported inputs.
* Added an optimized BF16 inference reduction path that masks invalid
routes without first clearing their combine slots.
* NVFP4 quantization can now write into caller-provided output buffers.
* Per-call scalar tensors can be passed directly to supported launches.

* **Bug Fixes**
* Improved reliability of SM107 work scheduling to prevent CTAs from
disagreeing about which work phase is active.
  * Preserved route validation for inputs that use fallback staging.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fef5862](https://github.com/flashinfer-ai/flashinfer/commit/fef5862926900c82249a0d6b8a64985a8c25c735)

- **作者**: eigen
- **时间**: 2026-10-19T21:10:54Z
- **提交信息**: feat(cake_w8a8_megamoe_ep16): regenerate the six device kernels from their Cake sources (#6796)

`sm103_mxfp8_mxfp8_bf16_cake` is the experimental Cake backend of
FlashInfer's `moe_ep` MegaMoE EP16 kernel family (`MoEEpMegaLayer` API).
It takes MXFP8 E4M3 activations and MXFP8 E4M3 weights with E8M0
block-32 scales and produces BF16 output. It runs EP16 over NVSHMEM
symmetric memory with hidden 3072, intermediate 5120, 512 experts (32
per rank), top-8 and at most 64 tokens per rank. The other variants of
this MXFP8 × MXFP8 → BF16 configuration are the CuTe-DSL
`sm100_mxfp8_mxfp8_bf16_cutedsl` backend in its legacy inference form
and in its GenPhase form (`knobs=None` heuristic, `knobs="auto"`
autotune). This PR regenerates the Cake backend's six device kernels
(publish_push, local_pack, fc1, fc2, combine, quantize_weights) from
their Cake sources and replaces the version shipped by PR #6759.
Bindings, host path and tests are unchanged. Compared with the previous
Cake kernels from PR #6759, measured on the same 16 GPUs in the same
session, the speedup ranges from 0.997x to 1.005x across the six shapes
below. T is the global token count, and hot-set routing sends 50% of
tokens to a hot expert set.

*16x NVIDIA GB300 (4 nodes, one NVL72 block), sm_103a, CUDA 13.3
(PyTorch 2.13 container), FlashInfer dad76de78 with this PR's kernels
and manifest in place of the shipped ones; both sides measured by
CUDA-graph replay, max rank-local CUPTI median over 3 counterbalanced
rounds, cold L2; per-forward latency of the full EP16 layer on 16
ranks.*

| Shape | Previous Cake kernels (PR #6759), µs | This PR, µs | Speedup
(previous / this PR) |
|---|---:|---:|---:|
| T=256 (16 per rank), balanced | 266.1 | 264.8 | 1.005x |
| T=256 (16 per rank), hot-set | 264.9 | 265.2 | 0.999x |
| T=512 (32 per rank), balanced | 268.8 | 267.7 | 1.004x |
| T=512 (32 per rank), hot-set | 266.2 | 267.0 | 0.997x |
| T=1024 (64 per rank), balanced | 272.4 | 272.6 | 0.999x |
| T=1024 (64 per rank), hot-set | 272.2 | 272.8 | 0.998x |

Cake also ships the BF16-activation × MXFP8-weight variant of this EP16
MegaMoE in FlashInfer
(`flashinfer/experimental/cake_mxfp8_megamoe_ep16`, CUDA and CuTe-DSL
backends) on sm_100a and sm_103a; this W8A8 (MXFP8 × MXFP8) family ships
on sm_103a only.

```experimental-tests
tests/experimental/test_cake_w8a8_megamoe_ep16.py
```


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
* Updated internal GPU processing and synchronization details. These
changes do not alter user-facing functionality.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [41788aa](https://github.com/flashinfer-ai/flashinfer/commit/41788aab9faba7d6798cbbfc904505471f0fd212)

- **作者**: Jeonghwan Park
- **时间**: 2026-10-19T21:02:58Z
- **提交信息**: fix(topk): order the cached-count reset after the previous round's read in topk_clusters_exact (#6400)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes #6399. `topk_clusters_exact` (what `top_k(...,
deterministic=False)` uses on SM100/SM103) sometimes returns a wrong
top-k when a row is split across more than one cluster.

The race: at the start of each round, thread 0 resets
`shared_num_cached_count[phase]`. The previous round read that same slot
(as `[phase ^ 1]`) after its last `__syncthreads`, and only the cluster
arrive/wait sits in between. Arrive comes before the read, so a slow
warp can read 0 and drop its candidates. This adds a `__syncthreads()`
at the top of the round loop.

Measured on B300, fp32 `randn * 3` `[rows, 248320]`, k=20,
`deterministic=False`, 500 calls per row:

| rows (clusters per row) | before: wrong / garbage ids | after | kernel
time before → after |
|---|---|---|---|
| 160 (2) | 3 / 0 | 0 / 0 | 94.5 → 95.0 µs |
| 200 (2) | 18 / 7 | 0 / 0 | 96.6 → 97.2 µs |
| 240 (2) | 26 / 4 | 0 / 0 | 117.5 → 118.2 µs |
| 252 (2) | 14 / 8 | 0 / 0 | 120.2 → 120.9 µs |
| 255 (2) | 17 / 3 | 0 / 0 | 121.1 → 121.2 µs |
| 252 (4, forced) | 23 / 10 | 0 / 0 | 127.3 → 128.5 µs |
| 64 (4), 512 (1), 252 with k=2048 | 0 / 0 | 0 / 0 | within ±1 µs |

## 🔍 Related Issues

#6399

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
- [x] All tests are passing (`unittest`, etc.).

Added `test_topk_clusters_exact_two_clusters_repeated` (batch 200 and
252, vocab 248320, k=20, 200 calls each, exact comparison against
`torch.topk`). Existing cases use batch 1/16/64, which never select 2
clusters. On B300 the new test failed 5 of 5 runs without the fix and
passed 5 of 5 with it (~7 s). `pytest tests/utils/test_topk.py -k
clusters`: 458 passed with the fix.

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

- Tested on B300 (SM103) only.
- The page-table / ragged transforms use the same device function, so
they get the fix too. Only the existing `-k clusters` tests cover them.
- Same kind of fix as #3529.
- Moving the read above `cluster.barrier_arrive()` also fixes it (0 /
3,500, no extra barrier), but leaves the `NClusters == 1` path
unordered, so I went with the barrier.
- AI-assisted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved the reliability of exact clustered top-k results across
repeated runs, including large inputs with two clusters.
* Added synchronization between processing phases to help ensure results
are consistent.
* **Tests**
* Added repeated-run coverage that checks returned indices, values, and
top-k results against expected outputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [3e5a826](https://github.com/flashinfer-ai/flashinfer/commit/3e5a82608543be804a753f95c785c06a7f8414d9)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-19T20:17:46Z
- **提交信息**: perf(gemm): SM107 FP8/FP4 GEMM selection: mm_fp8 cuBLAS route, bmm_fp8 runner order, mm_fp4 split-K picks (#6521)

<!-- .github/pull_request_template.md -->

## 📌 Description

On Rubin (SM107), three FP8/FP4 GEMM APIs either can't reach their
fastest existing kernel or pick a slower one by default. This PR only
changes kernel selection; no new kernels are added. **No default
changes:** the new `mm_fp8` backends are opt-in.

**1. `mm_fp8`: new opt-in `cublas` / `cudnn` / `cutlass` / `auto`
backends. The default stays `"trtllm_low_latency"`.**
- Problem: `mm_fp8` could only run the trtllm-gen low-latency kernels.
Those are tuned for Blackwell and were never the fastest backend on any
of 96 measured Rubin shapes. The per-tensor-scaled FP8 GEMMs behind
`bmm_fp8` (cuBLAS, cuDNN, CUTLASS) do the same math but were unreachable
from `mm_fp8`.
- Fix: pass the unprocessed `(n, k)` weight with `backend="cublas"` (or
`"auto"`) to run the `bmm_fp8` runners with batch 1, sharing their
autotuner cache. `auto` follows the weight layout: a weight prepared by
`prepare_low_latency_gemm_weights` still runs `trtllm_low_latency`.
`trtllm_low_latency` now rejects a 2-D weight with a clear error instead
of misreading it.

**2. `bmm_fp8` / `fp8_gemm_sm100`: the untuned runner now follows the
heuristic order.**
- Problem: `fp8_gemm_sm100` built its runner list in a fixed cutlass →
cublas → cudnn order. Untuned, and on a cache miss, the autotuner runs
the first runner, so `bmm_fp8(backend="auto")` always ran CUTLASS
whatever the heuristic said.
- Fix: build the runners in the caller's order, and put cuBLAS first on
SM107, where it is the faster untuned choice. Autotuning still tries
every candidate, and the order on other architectures is unchanged. This
affects only explicit `bmm_fp8(backend="auto")` on SM107; the `bmm_fp8`
default (`"cublas"`) is unchanged.

**3. `mm_fp4(backend="cute-dsl")`: the SM107 untuned path now considers
split-K.**
- Problem: on SM107 the untuned path went straight to the SM107 tile
picker and never consulted the cluster split-K picker that SM100/SM103
have used since #5609. Low-M, large-weight shapes therefore ran one
block (CTA) per weight tile and left most SMs idle.
- Fix: take the split-K picker's choice when it selects the split-K
kernel, an `sm_100f` build that already runs on Rubin. Otherwise the
SM107 picker decides, as before.

**Benchmarks and tests**
- `flashinfer_benchmark.py` accepts `cublas` / `cudnn` / `cutlass` /
`auto` / `cutedsl_low_latency` for `mm_fp8`. Only `trtllm_low_latency`
is given the prepared weight.
- New tests: `mm_fp8` on every new backend and with `auto` on both
weight layouts; `auto` routing; `trtllm_low_latency` rejecting an
unprocessed weight.

### Performance

Rubin (SM107), measured with `flashinfer_benchmark.py` (CUDA events,
CUDA graphs, cold L2), taking the faster of two passes. For `mm_fp8`,
"main" is the default (`trtllm_low_latency`) and "PR" is
`backend="auto"` with the unprocessed weight. For `mm_fp4`, both sides
are untuned `cute-dsl` in the same process, with the old and new tactic
picker. The GB300 column uses the same benchmark command; this PR does
not change what GB300 runs for any row here.

| API | Shape (M × N × K) | PR vs main on Rubin | Rubin vs GB300, main |
Rubin vs GB300, PR |
|---|---|---:|---:|---:|
| `mm_fp8` | 16 × 5120 × 16384 | **1.71x** | 1.16x | **1.97x** |
| `mm_fp8` | 1 × 5120 × 8192 | **1.55x** | 1.14x | **1.76x** |
| `mm_fp4` | 8 × 8192 × 28672 | **1.16x** | 1.39x | **1.63x** |
| `mm_fp4` | 1 / 32 × 8192 × 28672 | **1.17x / 1.11x** | — | — |
| `mm_fp4` | 8 × 5120 × 16384 | **1.57x** | — | — |

| Sweep (same process) | Shapes | PR vs main | Slower shapes |
|---|---:|---:|---|
| `mm_fp8` untuned cuBLAS vs `trtllm_low_latency`, M 1–128 × 12 (N, K) |
96 | 1.55x geomean | 4 (M 1–8 × 8192 × 4096: 0.80–0.94x untuned;
autotuned cuBLAS wins there too) |
| `mm_fp8` best autotuned of cuBLAS/cuDNN/CUTLASS vs autotuned
`trtllm_low_latency` | 96 | 1.35x geomean (1.11–1.83x) | none |

### Not addressed here

| Area | Status | What is left |
|---|---|---|
| `mm_fp8`, prepared weight | Unchanged | Callers that pre-shuffle the
weight for `trtllm_low_latency` keep that path until they pass the
unprocessed weight. |
| `mm_fp4`, small M | Improved where split-K is chosen | Some
kernel-side headroom remains. Shapes where no split is chosen (e.g.
N7168 K4608) are unchanged. |

## 🔍 Related Issues

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually (`pre-commit run --files` on every
changed file) and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

On Rubin, before the rebase onto current main: `test_mm_fp8.py` gave 211
passed, 6 skipped; `test_bmm_fp8.py` + `test_autotuner_bmm_fp8.py` gave
22 passed. `mm_fp4` split-K outputs were bit-identical to cuDNN. CI is
requested below for this branch. Not yet run on B200/GB300; nothing
changes there unless a caller opts into the new `mm_fp8` backends.

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

- **No default changes.** `mm_fp8`, `bmm_fp8` and `mm_fp4` keep their
defaults; only the `mm_fp8` `Literal` backend list grows. The one
behaviour change on an existing path is untuned
`bmm_fp8(backend="auto")` on SM107, which now starts with cuBLAS instead
of CUTLASS.
- Split out of #6508, which now carries only the SM107 CuTe-DSL
blockwise backend for `gemm_fp8_nt_groupwise`. The two PRs are
independent.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* FP8 matrix multiplication now supports cuBLAS, cuDNN, and CUTLASS,
alongside existing low-latency options.
* Automatic backend selection is available and adapts to whether weights
are prepared and which backends are supported.
* **Improvements**
* FP8 batch matrix multiplication now prioritizes cuBLAS on SM107 when
available.
* NVFP4 matrix multiplication can try an additional split-K option
before falling back to an SM107 tactic.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b89aa0e](https://github.com/flashinfer-ai/flashinfer/commit/b89aa0efdd422f979e4fcca2788c9a81357fd219)

- **作者**: Vincent
- **时间**: 2026-10-19T20:11:37Z
- **提交信息**: perf(moe): split the topK reduction in small-batch trtllm-gen MoE finalize (#6546)

<!-- .github/pull_request_template.md -->

## 📌 Description

At decode batch sizes the trtllm-gen MoE finalize step (`finalize::run`,
non-DeepSeek path) uses `finalizeKernel`, where each thread reads one
scalar element per expert and walks the topK dependent index/data loads
serially. For high top-k models this is a large share of a MoE call's
fixed cost at one token.

This adds `finalizeKernelSmallBatch` for the same regime
(`ceil(hidden/256) * numTokens < 1184`, 128-bit aligned hidden, `4 <
topK <= 64`):
- one CTA per (token, hidden slice), 128-bit loads;
- the topK reduction is split across `blockDim.y` thread groups so each
thread issues at most four independent loads, and partial sums are
combined through shared memory;
- the routing permutation and expert weights are read before
`cudaGridDependencySynchronize()` (they come from routing, which has
completed before the GEMMs this kernel depends on can start, as
`finalizeKernelVecLoad` already assumes); only the GEMM output is read
after the wait;
- programmatic launch completion is triggered at kernel start, so the
next kernel can launch while finalize runs.

For `topK <= 4` the whole topK fits in one thread group, the
shared-memory reduction costs more than it saves, and the previous
kernel is kept. The large-batch `finalizeKernelVecLoad` path and
`finalizeDeepSeekKernel` are unchanged. The new kernel is arch-generic.

### Performance

**Finalize only** (`trtllm_moe_run_finalize`, PDL on, CUDA graph, median
of 3 interleaved rounds), new vs previous kernel over hidden {1024,
2048, 2880, 3584, 4096, 5120, 6144, 7168} x every small-batch token
count x bf16/fp32 expert weights. Median speedup per topK (min in
parentheses):

| topK | SM107 (Rubin) | SM103 (GB300) | SM100 (GB200) |
|---|---|---|---|
| 1, 4 | kept on previous kernel (would be 0.97-1.00x, min 0.85x) | | |
| 6  | 1.26x (1.17) | 1.29x (1.17) | 1.29x (1.15) |
| 8  | 1.13x (1.06) | 1.13x (1.06) | 1.14x (1.06) |
| 10 | 1.40x (1.36) | 1.41x (1.36) | 1.42x (1.35) |
| 16 | 1.40x (1.36) | 1.42x (1.34) | 1.44x (1.37) |
| 22 | 1.78x (1.65) | 1.79x (1.62) | 1.81x (1.64) |
| 32 | 1.97x (1.75) | 1.94x (1.75) | 1.99x (1.77) |

topK 2 is also faster with the new kernel (~1.06-1.10x median) but is
kept on the previous kernel so the rule stays "more than one topK
group". Shapes outside the small-batch regime run the unchanged kernel
and move within noise (0.98-1.02x).

**Whole-op** `trtllm_fp4_block_scale_moe` (NVFP4, PDL on, default
tactic, CUDA graph, median of 3 interleaved rounds), H6144/E256/top-8,
H2048/E512/top-22 (ReLU2), H3584/E896/top-16:

| tokens | top-8 Rubin | top-8 GB300 | top-8 GB200 | top-22 Rubin |
top-22 GB300 | top-22 GB200 | top-16 Rubin | top-16 GB300 | top-16 GB200
|
|---|---|---|---|---|---|---|---|---|---|
| 1 | 1.018x | 1.015x | 1.014x | 1.076x | 1.084x | 1.085x | 1.047x |
1.062x | 1.060x |
| 8 | 1.004x | 1.007x | 1.009x | 1.053x | 1.038x | 1.041x | 1.029x |
1.022x | 1.026x |
| 16 | 1.009x | 1.004x | 1.006x | 1.039x | 1.028x | 1.030x | 1.032x |
1.026x | 1.026x |
| 32 | 1.009x | 1.000x | 1.000x | 1.022x | 1.017x | 1.018x | 1.016x |
1.013x | 1.012x |
| 64 | (unchanged path) | 0.997x | 0.996x | 1.021x | 1.014x | 1.015x |
1.025x | 1.008x | 1.009x |
| 128 | — | 1.004x | 1.004x | 1.033x | 1.024x | 1.027x | — | 1.000x |
1.001x |

Rubin whole-op runs were on a clock-capped board; compare ratios, not
absolute times.

### PDL ordering (last three commits)

Three ordering-only changes that shorten the decode-time critical path;
the arithmetic is unchanged:
1. small-batch finalize reads the routing permutation and expert weights
before its grid-dependency wait;
2. small-batch finalize triggers its dependents at kernel start;
3. `routingIndicesBlockKernel` / `routingIndicesDynBlockKernel` trigger
their dependents right after their own grid-dependency wait instead of
after all writes. The batched GEMMs that follow guard every
routing-dependent load with a grid dependency
(`gridWaitForPrimaryRouting`), so they launch and run their prologue
while routing computes. On its own this is neutral; it helps once (2)
lets the routing kernel itself launch early.

Whole-op `trtllm_fp4_block_scale_moe` (NVFP4, PDL on, best of default /
autotuned tactic), this head vs the previous head of this PR:

| shape | tokens | SM107 (Rubin), `flashinfer_benchmark`, 3 GPUs x 3
interleaved rounds | SM103 (GB300), CUDA graph | SM100 (GB200), CUDA
graph |
|---|---|---|---|---|
| H6144/I512/E256/top-8 | 1 | 1.038x | 1.014x | 1.013x |
| H6144/I512/E256/top-8 | 8 | 1.035x | 1.021x | 1.033x |
| H2048/I1280/E512/top-22 | 1 | 1.058x | | |
| H2048/I1280/E512/top-22 | 8 | 1.025x | | |

On SM103 / SM100 the top-8 shape improves 1.008-1.055x across 1-16
tokens, with no regression.

Correctness: with PDL on, outputs are bitwise equal to PDL off over 900
routings (1-16 tokens, top-8) on each architecture, and the small-token
MoE tests pass (SM107: 211 passed, 0 failed of the 504 selected; SM103 /
SM100: 76 passed, 0 failed of a 152-test NvFP4 / MxFP4 subset; the rest
skipped by the tests' own filters).

## 🔍 Related Issues

Follow-up to #6271 (small-batch MoE latency on SM107).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (clang-format 19.1.1 on the changed file)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (Covered by existing
reference-checked MoE tests.)
- [x] All tests are passing (`unittest`, etc.).
- Every test in `tests/moe/test_trtllm_gen_fused_moe.py` and
`tests/moe/test_prims_ts_fp8_block_scale_moe.py` with <= 128 tokens
(3264 collected), on SM107 / SM103 / SM100: 463 / 457 / 467 passed, 0
failed (rest skipped by the tests' own compatibility filters). Passes
include FP8 block-scale 155, NvFP4 142, MxFP4 85-95, BF16 28, FP8
per-tensor 9, MxInt4 8, Prims-TS staged finalize 1-5 (29 more Prims-TS
tests passed on SM100/SM103 in an earlier run).
- The finalize-only sweep checks every config against a torch reference:
max error 3.7e-3 relative to peak (bf16 rounding).

🤖 Generated with [Claude Code](https://claude.com/claude-code)




<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved processing efficiency for eligible small-batch workloads with
higher top-K values.
* Updated routing and finalization coordination to support more
efficient execution.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [feb2095](https://github.com/flashinfer-ai/flashinfer/commit/feb20959a8619a5a8adfe24c298960d9c1028275)

- **作者**: eigen
- **时间**: 2026-10-19T19:34:39Z
- **提交信息**: perf(cake_all_gather_matmul): SM100a CTA-pair main kernel for nine measured shapes (#6586)

This is a regenerated export of the Cake all-gather matmul backend. It
changes which calls run the CTA-pair main kernel on SM100a (B200). No
kernel program changes, and SM103a is unchanged.

This PR builds on #6566 (SM103a CTA-pair main kernel for two gate/up
shapes), which in turn builds on #6501. Neither is merged yet. The
branch was created from #6566's branch
`cake-agmm-sm103a-cg2-gate-up-regions`, and the PR targets `main` so
that CI runs. Until #6566 merges, the GitHub diff also contains the
#6501 and #6566 commits; this PR's own change is one commit: the SM100a
region points, the world-size-8 pair twin now delivered for SM100a, and
the regenerated tests. Please merge it after #6566.

The change has two parts:

1. **Nine SM100a region points.** Before this PR, SM100a had no CTA-pair
regions, so every SM100a call ran the single-CTA main kernel. The SM100a
table now has nine entries in the schema from #6566. Each entry is a
single point: one padded row count and one N, both taken from a measured
inventory shape. The selection rule is unchanged.
2. **World-size-8 pair twin on SM100a.** Two of the nine shapes have
world size 8 (bf16, K-major). The world-size-8 bf16 K-major pair twin,
which #6566 delivered for SM103a, is now also delivered for SM100a. The
kernel set stays at 24 programs.

The speedups come from paired runs on two 8×B200 nodes. Seven of the
nine shapes ran 4.1–10.1 % faster, beyond the noise bound on both nodes.
The other two (TP4 and TP8 gate/up, M=1024 per rank) ran 2.0–4.1 %
faster, but not beyond the noise bound on at least one node. They are
routed as measured, and no gain is claimed for them. No shape was slower
on either node. Outputs are bitwise identical to the reference program
on every rank. Some node-1 checks were re-run on the same host; see
*Disclosures*.

## Routing and kernel changes

### SM100a region points

The schema and the rule are the ones from #6566. Each `CG2_REGIONS`
entry in `flashinfer/jit/cake_all_gather_matmul.py` has this form:

`[world_size, dtype, b_layout, min_padded_rows, max_padded_rows,
min_cols, max_cols]`

A call with 256-column tiles runs the CTA-pair twin only if one
rectangle of its class, on the device architecture, satisfies both of
these conditions:

- `min_padded_rows ≤ padded rows ≤ max_padded_rows`, where padded rows
is the row count rounded up to a multiple of 128;
- `min_cols ≤ N ≤ max_cols`.

Every other call keeps its current main kernel.

The new SM100a entries:

| world size | dtype | B layout | padded rows | N | measured shape (per
rank) | inventory label |
|---|---|---|---|---|---|---|
| 2 | bf16 | N-major | 2048 | 2048 | M=2048 | `perf_bf16_m2048` |
| 2 | bf16 | N-major | 4096 | 2048 | M=4096 | `perf_bf16_m4096` |
| 4 | bf16 | K-major | 1024 | 2560 | TP4 QKV, M=1024 |
`llama_tp4_qkv_bf16_m1024_kmajor` |
| 4 | bf16 | K-major | 1152 | 2560 | TP4 QKV, M=1025 |
`llama_tp4_qkv_bf16_m1025_kmajor` |
| 4 | bf16 | K-major | 2048 | 2560 | TP4 QKV, M=2048 |
`llama_tp4_qkv_bf16_m2048_kmajor` |
| 4 | bf16 | K-major | 512 | 14336 | TP4 gate/up, M=512 |
`llama_tp4_gate_up_bf16_m512_kmajor` |
| 4 | bf16 | K-major | 1024 | 14336 | TP4 gate/up, M=1024 |
`llama_tp4_gate_up_bf16_m1024_kmajor` |
| 8 | bf16 | K-major | 512 | 7168 | TP8 gate/up, M=512 |
`llama_tp8_gate_up_bf16_m512_kmajor` |
| 8 | bf16 | K-major | 1024 | 7168 | TP8 gate/up, M=1024 |
`llama_tp8_gate_up_bf16_m1024_kmajor` |

On SM100a, these nine shapes move from the single-CTA main kernel to the
CTA-pair main kernel (`_cg2`). The SM103a entries from #6501 and #6566
are unchanged, so SM103a routing does not change.

Each rectangle is a single point. Calls with a different padded row
count or a different N keep the single-CTA kernel. Because the rule uses
padded rows, row counts that pad onto a point also select it. For
example, at world size 4 and N=14336, 385–512 rows select the 512 point
and 897–1024 rows select the 1024 point. 513 rows (padded to 640) and
1025 rows (padded to 1152) select neither. N=14080, one 256-column tile
below the point, does not select it either. The TP4 QKV point at 1152
padded rows is the M=1025 inventory shape. The gate/up classes have no
1152 point, so the TP4 and TP8 gate/up shapes at M=1025 keep the
single-CTA kernel.

### Shapes that keep their programs on SM100a

- the TP4 and TP8 gate/up shapes at M=1025 (padded to 1152) and at
M=2048;
- the TP4 QKV shape at M=512 (N=2560);
- every fp16 shape;
- every other shape, including every call with 128-column tiles.

The CTA-pair programs are the ones already delivered. This PR changes
only which calls select them on SM100a. Nothing is approximated, and
accumulation precision is unchanged.

## Kernel set and loader surface

- **Kernels.** No kernel program changes, and no kernel module is added.
The set stays at 24 programs: 21 plus 3 CTA-pair twins. The world-size-8
bf16 K-major twin, `main_bfloat16_ws8_k_major_cg2` (kernel symbol
`kernel_cake_all_gather_matmul_main_bfloat16_8_k_major_cg2`), was
delivered for SM103a only. Its architecture list is now `["sm_100a",
"sm_103a"]`. Route keys are unchanged.
- **Loader** (`flashinfer/jit/cake_all_gather_matmul.py`):
  - `CG2_REGIONS["sm_100a"]` gains the nine points;
- `CG2_CLASSES["sm_100a"]` lists the three classes that have points:
world size 2 bf16 N-major, world size 4 bf16 K-major and world size 8
bf16 K-major;
  - `_cg2_regions` and `main_form` are unchanged.
- **Tests** (`tests/comm/test_all_gather_matmul_cake.py`):
  - the SM100a pins for both tables are updated;
  - the nine shapes are expected on the pair kernel on SM100a;
- the inventory gains the TP4 and TP8 gate/up shapes at M=1024 and
M=1025, so the new points and their M=1025 neighbours are exercised;
- on SM100a, the pair-rule test covers world size 8 and the world-size-4
gate/up points, with row neighbours inside and outside each point and
the adjacent N values;
- the launch-entry table expects the pair kernel for 512×14336 (world
size 4) and 512×7168 (world size 8) on SM100a, and adds 500-, 513-,
1000-, 1024-, 1025- and 2048-row entries for both classes;
- the architecture check for the world-size-8 twin no longer assumes
SM103a only.
- **Public API.** The `all_gather_matmul` / `prepare_all_gather_matmul`
entry points are unchanged.
- **File signature vs #6566's branch:** 0 added / 6 modified / 0
deleted, 804 insertions and 46 deletions, no stray files:
`csrc/cake_all_gather_matmul/cake_all_gather_matmul_sequence_bfloat16_ws2_n_major_sm_100a.cu`,
`…_sequence_bfloat16_ws4_k_major_sm_100a.cu`,
`…_sequence_bfloat16_ws8_k_major_sm_100a.cu` (each gains the pair-kernel
launch path: declaration, TMA encoders and dispatch for its class),
`flashinfer/jit/cake_all_gather_matmul.py` (the nine region points and
the three classes), `tests/comm/test_all_gather_matmul_cake.py`, and
`csrc/cake_all_gather_matmul/cake_all_gather_matmul_device_common.cuh`
(two generated lines: the helper-union count in the header comment, 43 →
46, and the position of one `#include` in the helper list; no include
added or removed). No kernel `.cu` file is added, modified or deleted:
the pair programs the nine points route to were already delivered by
#6566, under the same content-hashed file names, and the 24 delivered
kernel files are byte-identical to the base branch

## Measurement

The A/B runs used two 8×B200 (SM100a) nodes. The measured tree was the
generator code behind #6566. Its SM100a programs are byte-identical to
Cake `main` at `20912c24` (≡ `8b96a056`). The candidate arm was the same
tree with a row allow-list, `CAKE_AGMM_CG2_ROWS`, that forces the
CTA-pair kernel on exactly these nine calls. Through the region table,
this PR selects the same kernel for the same nine calls. The generator
identity check under *This export* confirms this.

The same runs also measured two nested subsets of the nine shapes: the
five world-size-2 and QKV shapes, and those five plus the two M=512
gate/up shapes. This PR routes the full nine-shape set.

Timing protocol:

- CUPTI timing with a cold L2;
- nine counterbalanced ABBA groups per arm on each node;
- a same-code control arm.

A value above 1 means the CTA-pair kernel is faster. The speedup is the
pooled median of the per-group ratios t_base / t_cake. A shape counts as
faster on a node when |ln speedup| exceeds that node's noise bound
(delta_res).

| shape (per rank) | node 1 speedup | node 2 speedup | beyond the noise
bound |
|---|---:|---:|---|
| world size 2, M=2048, N=2048, bf16, N-major | 1.0453 | 1.0482 | both
nodes |
| world size 2, M=4096, N=2048, bf16, N-major | 1.0750 | 1.0887 | both
nodes |
| TP4 QKV, M=1024, N=2560 | 1.0737 | 1.0702 | both nodes |
| TP4 QKV, M=1025, N=2560 | 1.0411 | 1.0407 | both nodes |
| TP4 QKV, M=2048, N=2560 | 1.0468 | 1.0491 | both nodes |
| TP4 gate/up, M=512, N=14336 | 1.1009 | 1.0941 | both nodes |
| TP4 gate/up, M=1024, N=14336 | 1.0260 | 1.0410 | node 2 only (node 1
delta_res 0.0362) |
| TP8 gate/up, M=512, N=7168 | 1.0588 | 1.0658 | both nodes |
| TP8 gate/up, M=1024, N=7168 | 1.0220 | 1.0202 | neither (delta_res
0.0270 / 0.0357) |

The TP4 and TP8 shapes are bf16, K-major.

- **Adoption rule.** The nine-shape set passes: seven shapes are faster
beyond the noise bound on both nodes, and no shape is slower on either
node. The two M=1024 gate/up shapes read above 1 on both nodes. They are
routed as measured, and no gain is claimed for them.
- **Timeline attribution.** The main kernel span is shorter on every
changed shape on both nodes.
- **No-regression check.** Every changed shape is ≥ exp(−delta_res) on
both nodes. The check also covers all 45 perf rows, with
identical-program rows exempted. Under the nine-shape arm, both nodes
pass 45/45. Node 1's result comes from the same-host completion of its
run; see *Disclosures*. On node 1, one row misses the strict check:
`tail_ws2_bf16_m1000_n2048`, at 0.9948. Its program is byte-identical to
the baseline, so it is exempt. On node 2, four identical-program
world-size-2 rows (0.9897–0.9966) miss the strict check and are exempt
the same way.

## Correctness

Measured tree with the allow-list (node 1):

- **Exactness.** On every rank, outputs are bitwise identical to the
reference program. The run covered 128 rows in 24 launches, with 0
failures. The route of all 128 rows was checked and matched the expected
kernel.
- **compute-sanitizer.** synccheck: clean. racecheck: 0 hazards on the 4
registered rows under both the five-shape and the nine-shape arms. Under
the nine-shape arm, the first run was clean on 7 of 8 rows, and the
eighth produced incomplete tool output. A same-host re-run was clean on
all 8 rows; see *Disclosures*.
- **End-to-end.** The end-to-end test passes.

Adoption tree (the generator code behind this export, Cake `4c86f7b6`;
its only changes over the tree the adoption checks ran on, `32e46040`,
are two edits of the test template that touch no program, table or
assertion: a formatting-only re-layout so this export's test file is a
ruff 0.12.8 fixed point, and a rewording of eight comment and docstring
lines):

- **Exactness and determinism.** Compared with an independent checkout
of `8b96a056`, two independent launches: pass: 6 launches over 32 rows
(the inventory rows at world sizes 8, 4 and 2, plus controls), 0
failing, 0 compare failures; routing checked on 32/32 rows with 0
mismatches. Every (row, rank) output SHA-256 equals the reference
program's output and is equal across two independent launches; the
reference `8b96a056` was built from an independent checkout (adoption
step, 2026-10-16T09:56–10:06Z)
- **Shapes around the points.** 24 ad-hoc shapes: 511, 512, 513, 500,
1023, 1024, 1025 and 1000 rows at N=14336 (world size 4) and at N=7168
(world size 8); 512×14080 (world size 4); 512×6912 (world size 8); 1000,
1153 and 1025 × 2560 (world size 4); 2000 and 3000 × 2048, and 4096×2560
(world size 2). Routing and bitwise identity: pass: 27 ad-hoc rows
(shapes outside the measured inventory: the 24 shapes listed above plus
3 anchors), 0 failing; routing checked on 27/27 rows with 0 mismatches
against the expected kernel symbols (same step, 10:06–10:11Z)
- **compute-sanitizer.** synccheck and racecheck on the registered rows
and the nine changed rows: pass: compute-sanitizer synccheck and
racecheck, run as separate processes (never memcheck), on 13 rows: the
four registered rows (world size 2 1024×2048 N-major, world size 4
512×2560, world size 8 125×2048 N-major and 2048×1280) plus the nine
changed rows (world size 2 2048×2048 and 4096×2048 N-major; world size 4
1024, 1025 and 2048 × 2560 and 512 and 1024 × 14336; world size 8 512
and 1024 × 7168; all bf16). synccheck: 13/13 rows with `ERROR SUMMARY: 0
errors` on every rank. racecheck: 13/13 rows with 0 hazards and 0
internal errors on every rank. The registry launcher check passed (same
step, 10:11–10:28Z)
- **End-to-end.** pass: the generator's end-to-end `all_gather_matmul`
test with exactly 2 visible GPUs: 1 passed, 0 skipped (same step,
10:28–10:29Z)

## Disclosures

- **Two shapes without a claimed gain.** TP4 gate/up M=1024 is not
significant on node 1 (1.0260, delta_res 0.0362). TP8 gate/up M=1024 is
not significant on either node (1.0220 / 1.0202, delta_res 0.0270 /
0.0357). Both read ≥ 1 on both nodes and are routed as measured.
- **Node-1 run cut short and completed.** Node 1's measurement step was
killed by an external SIGTERM at exactly 4 h 00 min. The cause is
unknown; it was not a cluster time limit. At that point, the all-perf
no-regression check under the nine-shape arm covered only 33 of 45 rows
on node 1. The 12 world-size-8 rows were missing, and the control arm's
first-pass world-size-4 launch was void. A one-hour follow-up on the
same host completed the evidence. It repeated the void control launch
and the whole nine-shape all-perf pass at world sizes 8, 4 and 2, with
no void rows. It also measured node 1's fixed per-call overhead for the
hardware bound and re-ran racecheck. Node 1 now passes 45/45 after the
identical-program exemption. Its control rows are no longer void. The
five-shape and nine-shape arms both still pass the adoption rule.
Completion details: completed on node 1's own host
(2026-10-16T09:19–10:20Z, one 8-GPU allocation of 1.0 h). The follow-up
repeated the voided control-arm first-pass world-size-4 launch and the
whole nine-shape all-perf pass at world sizes 8, 4 and 2 with no void
rows; measured node 1's fixed per-call overhead for the hardware bound
(29.248 µs, 9 groups); and re-ran racecheck on the nine-shape arm (8/8
rows clean). Read-out after completion: node 1 passes the all-perf
no-regression check 45/45 after the identical-program exemption, the
two-node check has 45 common rows with 0 failures after exemption, the
control arm is no longer void, and the adoption verdicts are unchanged
for both the five-shape and the nine-shape arms. Hardware-bound read
with the measured overhead on both nodes: node 1 has 9 of 45 rows at or
under the bound (the 7 rows already there in the baseline round, plus
`perf_bf16_m2048` 118.1 ≤ 120.9 µs and `perf_bf16_m4096` 217.8 ≤ 222.2
µs); node 2 (overhead 30.432 µs) has 10 of 45, adding TP4 gate/up M=1024
at 787.8 ≤ 810.0 µs
- **Export re-run on another node.** The adoption step ran on one 8×B200
node. Its exactness, ad-hoc shape, sanitizer and end-to-end checks
passed. They do not depend on clocks, so they stand. The export phase
then failed because that node was throttled. The first world-size-8
shape, `llama_tp8_gate_up_bf16_m512_kmajor`, passed at ratio 0.9987.
Next, the exporter's loaded-SM-clock floor aborted
`llama_tp8_gate_up_bf16_m1024_kmajor`. The clock read 1140 of 1965 MHz,
below the 0.60 fraction gate. The world-size-4 run hit the floor twice
more at 1020 MHz and then hung for 23 min. The step was cancelled. A
second step on a different 8×B200 node re-ran only the export and the
FlashInfer tests. All nine changed shapes passed the 0.95 floor with
bitwise-identical outputs, and the FlashInfer tests passed. Two later
exports from the same kernel sources, made after the two template-only
edits, reproduced this; the last of them is the export of record under
*This export*.
- **Incomplete racecheck output.** On one row,
`ws4_1024_14336_k_major_bfloat16`, the first racecheck run printed no
RACECHECK SUMMARY. This was incomplete tool output, not a reported
hazard. A re-run on the same host covered all 8 rows run under the
nine-shape arm. It was clean on 8 of 8 rows, including this one, with 0
hazards and 0 internal errors on every rank. Re-run: clean. The re-run
on node 1 (2026-10-16T10:13–10:19Z) covered the 8 rows run under the
nine-shape arm (world size 2 1024×2048 N-major; world size 4 512×2560,
512×14336, 1024×14336; world size 8 125×2048 N-major, 2048×1280,
512×7168, 1024×7168; all bf16): 0 hazards and 0 internal errors on every
rank. synccheck and racecheck ran as separate processes; memcheck was
never used
- **Same-code control offset.** On world size 2, M=2048, the same-code
control arm read +0.8 to +1.1 % on both nodes. This is inside the
0.958–1.030 control band. The candidate's effect on that shape (+4.5 to
+4.8 %) exceeds the control offset by at least 3.4 %.
- **Voided launches.**
- On node 1, the control arm's first-pass world-size-4 launch was
voided: its control spread was 0.0912, above the 0.08 limit. Its second
pass was valid. The launch was also repeated on the same host, with no
void rows.
- On node 2, the world-size-4 subset of the all-perf check under the
nine-shape arm was voided. It was repeated on the same host, with no
void rows.
- On node 2, the seven-shape intermediate arm's first-pass world-size-8
launch was voided. The nine-shape arm supersedes this arm and is valid
on both nodes.
  - After the repeats, no row is void on either node.
- **Padded rows vs measured rows.** The allow-list in the measurement
names exact row counts. The region table selects by padded rows, so row
counts that pad onto a point (for example, 385–511 rows at the 512
points) also run the CTA-pair kernel. Only the inventory row counts were
timed. The adoption checks above cover such shapes for routing and
bitwise identity, but not for timing.

## This export

- **SM103a (B300).** The SM103a entries of `CG2_REGIONS` and
`CG2_CLASSES` are unchanged. Every SM103a call launches the same program
as before.
- **Generator identity check.** Pass. Against the generator tree behind
#6566:
- the resolve table differs on exactly the nine SM100a shapes, and
SM103a resolves identically;
- the 23 harness kernels per architecture, their receipts and 52 extra
renders are byte-identical;
  - pytest: 297 + 266 passed.
- **Generator source vs this export.** The export check compares the
generator source with this export, with a floor of 0.95 per changed
shape at world sizes 8, 4 and 2: pass: 9/9 changed shapes, ratio =
generator-source time / export time with a floor of 0.95 and
bitwise-identical outputs on every row — world size 8: TP8 gate/up
M=1024 1.0004 (0.7653 / 0.7650 ms), M=512 0.9996 (0.3994 / 0.3995 ms);
world size 4: TP4 gate/up M=1024 0.9984, M=512 0.9977, TP4 QKV M=1024
0.9969, M=1025 0.9996, M=2048 0.9981; world size 2: M=2048 1.0049
(0.1193 / 0.1188 ms), M=4096 0.9965 (0.2102 / 0.2109 ms); geometric mean
0.9991. Two earlier exports of the byte-identical kernel sources
measured the same shapes at 0.9960–1.0049 (gpu-157) and 0.9974–1.0029
(gpu-65).
- **FlashInfer tests.** Against the exported tree: pass: FlashInfer CPU
tests 345 passed / 0 failed / 0 errors / 0 skipped on the exported tree;
end-to-end `all_gather_matmul` tests 3 passed at 8 visible GPUs there,
while at 4 and 2 visible GPUs one of three tests did not start (torchrun
rendezvous port collision on the node, no kernel ran); the complete
8/4/2 set passed on the PR head (next item) and on the first export of
the byte-identical kernel sources (3 passed at each of 8, 4 and 2
visible GPUs); the second earlier export passed 3 at 8 and 3 at 2
visible GPUs, and at 4 visible GPUs one of three tests did not start for
the same port-collision reason. On the PR head
(`35a639d21dfc112cf7b7c85ac1d1485c9d1fc57b`): pass
(2026-10-16T14:46–14:59Z on gpu-193, B200): CPU suite 345 passed / 0
failed / 0 errors / 0 skipped; e2e `-k all_gather_matmul` 3 passed (137
s) with 8 visible GPUs, 3 passed (113 s) with 4 and 3 passed (97 s) with
2 — the full 8/4/2 set that the export step's rendezvous port collisions
had interrupted (all suites passed; the runner's own exit code was 1
only because its tally expected two device sets and three were run).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added an optional CTA-pair kernel path for eligible BF16 and FP16
all-gather matrix multiplications. Selection depends on the supported
hardware, workload shape, and tile width; other calls retain existing
kernel paths.
- Expanded architecture-specific SM-push routing, including an
additional eligible workload range for eight-rank operations.
- **Bug Fixes**
- Improved validation of kernel selection and launch configurations,
including grid dimensions and SM-push eligibility.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [284e970](https://github.com/flashinfer-ai/flashinfer/commit/284e970771b6f02a6315ac08a876cf460b9ce27d)

- **作者**: eigen
- **时间**: 2026-10-19T19:13:09Z
- **提交信息**: feat(cake_causal_conv1d): packed causal conv + SiLU kernels for sm_100a, sm_103a and sm_107a with grad (#6782)

Cake's `causal_conv1d` training kernel family has two programs, and this
PR delivers both. The forward program maps BF16 `x` to BF16 `y` with
fused SiLU. The backward program produces BF16 `dx` and FP32 `dweight`
using a fixed-order, bitwise-reproducible reduction. Both work on packed
sequences (device-side `cu_seqlens`, zero history at the beginning of
each document) with width 4, BF16 activations in [S, C] layout (S packed
tokens, C channels) and FP32 weights [C, 4]. No other data type, layout
or fused form is shipped. No previous Cake version of this kernel
exists, so the baseline is the flash-linear-attention (FLA) 0.5.2 Triton
`causal_conv1d`: its forward kernel for forward, and its `dx` and
`dweight` kernels for backward. FLA and Cake were measured interleaved
on the same inputs (median kernel time, cold L2). Across the 14 shapes
below, the speedup over FLA is 1.476x–1.918x forward and 4.082x–4.864x
backward on GB300, 1.406x–1.842x forward and 4.036x–4.494x backward on
B200, and 1.414x–1.986x forward and 3.563x–3.933x backward on R200.

**NVIDIA GB300 (sm_103a).** Driver 580.159.03, CUDA 13.0 runtime (torch
2.14.1+cu130).

| S | C | FLA fwd (µs) | Cake fwd (µs) | Fwd speedup | FLA bwd (µs) |
Cake bwd (µs) | Bwd speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 239718 | 512 | 148.1 | 83.4 | 1.776x | 841.5 | 206.0 | 4.084x |
| 245028 | 512 | 150.8 | 86.3 | 1.748x | 861.8 | 210.3 | 4.098x |
| 249866 | 512 | 153.7 | 86.9 | 1.768x | 876.0 | 214.6 | 4.082x |
| 250340 | 512 | 154.1 | 87.0 | 1.772x | 893.6 | 214.7 | 4.161x |
| 258574 | 512 | 158.8 | 89.5 | 1.774x | 907.1 | 221.9 | 4.089x |
| 259042 | 512 | 159.2 | 89.6 | 1.778x | 915.6 | 223.3 | 4.100x |
| 259584 | 512 | 159.3 | 89.7 | 1.776x | 915.2 | 223.1 | 4.103x |
| 261393 | 512 | 160.8 | 90.7 | 1.774x | 918.7 | 223.8 | 4.106x |
| 250340 | 128 | 41.8 | 28.3 | 1.476x | 309.6 | 63.7 | 4.864x |
| 250340 | 256 | 78.8 | 47.3 | 1.667x | 490.5 | 113.0 | 4.341x |
| 250340 | 1024 | 304.6 | 171.2 | 1.779x | 1768.5 | 410.4 | 4.309x |
| 250340 | 2048 | 607.5 | 323.6 | 1.877x | 3443.4 | 805.4 | 4.275x |
| 250340 | 4096 | 1211.2 | 636.3 | 1.903x | 6852.3 | 1594.7 | 4.297x |
| 250340 | 8192 | 2421.6 | 1262.3 | 1.918x | 13977.8 | 3169.7 | 4.410x |

**NVIDIA B200 (sm_100a).** Driver 580.82.07, CUDA 13.0 runtime (torch
2.14.1+cu130).

| S | C | FLA fwd (µs) | Cake fwd (µs) | Fwd speedup | FLA bwd (µs) |
Cake bwd (µs) | Bwd speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 239718 | 512 | 157.2 | 92.4 | 1.701x | 887.0 | 218.6 | 4.057x |
| 245028 | 512 | 160.4 | 93.9 | 1.707x | 907.5 | 223.3 | 4.064x |
| 249866 | 512 | 163.6 | 96.2 | 1.702x | 920.7 | 228.1 | 4.036x |
| 250340 | 512 | 163.9 | 96.4 | 1.701x | 926.6 | 228.0 | 4.064x |
| 258574 | 512 | 168.9 | 99.4 | 1.699x | 954.4 | 234.9 | 4.064x |
| 259042 | 512 | 169.0 | 99.1 | 1.705x | 958.3 | 235.1 | 4.076x |
| 259584 | 512 | 169.8 | 99.5 | 1.707x | 958.1 | 235.6 | 4.067x |
| 261393 | 512 | 171.4 | 100.2 | 1.711x | 962.7 | 237.5 | 4.053x |
| 250340 | 128 | 44.6 | 31.7 | 1.406x | 302.4 | 67.3 | 4.494x |
| 250340 | 256 | 83.6 | 54.4 | 1.536x | 510.0 | 119.7 | 4.260x |
| 250340 | 1024 | 325.1 | 182.5 | 1.782x | 1827.5 | 437.7 | 4.175x |
| 250340 | 2048 | 650.2 | 356.9 | 1.822x | 3591.2 | 861.7 | 4.168x |
| 250340 | 4096 | 1294.9 | 705.7 | 1.835x | 7251.6 | 1702.9 | 4.258x |
| 250340 | 8192 | 2584.1 | 1402.6 | 1.842x | 14737.9 | 3376.5 | 4.365x |

**R200 (sm_107a).** Pre-production Rubin board with 212 SMs, reported by
the driver as `NVIDIA Graphics Device`. Driver 620.62, CUDA 13.0 runtime
(torch 2.14.1+cu130). FLA's Triton kernels were compiled with a CUDA
13.5 ptxas because Triton's bundled ptxas does not know sm_107a. The
C=128 backward row comes from a single re-run because the first run
showed a -3.72% timing drift on the baseline side.

| S | C | FLA fwd (µs) | Cake fwd (µs) | Fwd speedup | FLA bwd (µs) |
Cake bwd (µs) | Bwd speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 239718 | 512 | 91.3 | 50.3 | 1.813x | 453.4 | 127.2 | 3.563x |
| 245028 | 512 | 93.2 | 51.6 | 1.807x | 464.0 | 129.2 | 3.591x |
| 249866 | 512 | 94.6 | 52.1 | 1.817x | 472.9 | 132.0 | 3.581x |
| 250340 | 512 | 95.2 | 52.3 | 1.822x | 475.3 | 131.8 | 3.605x |
| 258574 | 512 | 98.2 | 54.2 | 1.811x | 489.2 | 135.5 | 3.611x |
| 259042 | 512 | 98.5 | 54.2 | 1.817x | 491.0 | 136.3 | 3.602x |
| 259584 | 512 | 98.4 | 54.5 | 1.805x | 490.7 | 136.6 | 3.591x |
| 261393 | 512 | 99.4 | 54.7 | 1.817x | 492.7 | 137.2 | 3.591x |
| 250340 | 128 | 26.4 | 18.7 | 1.414x | 159.2 | 40.5 | 3.933x |
| 250340 | 256 | 49.5 | 30.5 | 1.622x | 255.4 | 70.9 | 3.601x |
| 250340 | 1024 | 185.7 | 97.8 | 1.899x | 917.8 | 246.0 | 3.731x |
| 250340 | 2048 | 368.3 | 189.3 | 1.946x | 1814.4 | 476.6 | 3.807x |
| 250340 | 4096 | 734.4 | 372.4 | 1.972x | 3575.6 | 939.4 | 3.806x |
| 250340 | 8192 | 1466.5 | 738.4 | 1.986x | 7206.2 | 1863.0 | 3.868x |

There are no other Cake variants of this kernel; this one covers
sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a training API for packed, width-4 depthwise causal convolution
with SiLU, including forward, backward, and autograd support.
* Supports BF16 activations and gradients with FP32 weights on SM100,
SM103, and SM107 GPUs. Packed documents are processed independently
using their provided boundaries.
* Added workspace helpers and options for preallocated outputs and
backward workspace. The API is also available through FlashInfer’s
top-level exports.
* **Documentation**
* Added API documentation covering supported inputs, outputs, and
training behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c59a76c](https://github.com/flashinfer-ai/flashinfer/commit/c59a76ccd6f8442cff4ffe555f55dc8c8d6a97c3)

- **作者**: eigen
- **时间**: 2026-10-19T18:56:33Z
- **提交信息**: perf(cake_comm): QkvNormRopeExchangeOverlap enables words_capacity_small_m=4096 on SM90 by default (#6717)

## 📌 Description

Stacked on #6620 (merge that first); the diff against #6620's head is
this change.

This PR turns on the small-row readiness-word gate by default on SM90
(Hopper) for `flashinfer.comm.QkvNormRopeExchangeOverlap`. That is the
fused QKV projection + per-head QK RMSNorm + RoPE + Ulysses exchange
session. The change is rendered from the Cake generator at ddb1ce74.

What changes:

* **SM90 shape-gate default.** The SM90 row of
`SHAPE_GATE_DEFAULT_BY_ARCH`
(`flashinfer/comm/cake_qkv_exchange_plan.py`) sets
`words_capacity_small_m` from 0 (off) to 4096.
* **Resulting behavior.** On SM90, a call with at most 4096 rows per
rank now publishes one readiness word per destination
(`words_capacity_per_dest = 1`). SM100 and SM103 already do this.
* **Host plan only.** The only runtime change is the number of readiness
words that the host plan uses for small rows. No kernels change.

SM90 shape gates after this PR:

| Gate | SM90 default |
|---|---|
| Small-row readiness words (`words_capacity_small_m`) | 4096 (was 0,
off) |
| Large-row gate (`reserved_sms_large_m`) | 16384 (unchanged) |
| Per-destination launch gate | off (unchanged) |

Unchanged:

* **Other architectures.** The SM100, SM103 and SM107 rows.
* **Programs.** The 84 generated `.cu` files, the loader and the
benchmark. The 15 generated programs compile to byte-identical cubins on
sm_90a, sm_100a and sm_103a (15 of 15, checked on the Cake side).
* **Larger rows.** The gate does not fire for a call with more than 4096
rows per rank, so that call takes the same plan as before.

Why: after the round-1 measurement on Hopper, this gate was left off on
SM90. In round 4 the Cake side measured it again on 8 × H100, using
OFF/ON A/B/B/A pairs within the same node allocation. The gate was
faster at every group size: +1.19 %, +0.40 % and +0.42 % for groups of
8, 4 and 2 ranks (see Speedup). Following the user decision of round 4,
this PR flips only this gate, and only on SM90.

Opt-out: `FLASHINFER_QKV_EXCHANGE_SHAPE_GATES=words_capacity_small_m=0`
restores the previous SM90 plan for a session, rank-uniformly.

Numerics: the compiled programs do not change, so the arithmetic does
not change. The round-4 performance run did not record output digests
for this change on SM90. The GPU verification in the Test plan compares
the outputs bitwise against the gate-off plan, and its result is
reported there.

### Files

Compared with the head of #6620 (290d89db): 4 files modified, none added
or deleted.

| Path | Change |
|---|---|
| `flashinfer/comm/cake_qkv_exchange_plan.py` | SM90 row of
`SHAPE_GATE_DEFAULT_BY_ARCH` and its comment (8 lines) |
| `tests/comm/test_qkv_norm_rope_exchange_overlap.py` | Shape-gate
default-table test: the SM90 entry of the whole-table assertion and its
docstring; on SM90, 128 and 4096 rows per rank now fire the small-row
gate, 16383 does not, and 16384 and above fire the large-row gate as
before (12 insertions, 7 deletions) |
| `flashinfer/comm/qkv_norm_rope_exchange_overlap.py` | API docstring (5
lines) |
| `docs/api/comm.rst` | API documentation (7 lines) |

The five rendered template files are byte-identical to the Cake
generator's templates at ddb1ce74.

## 🔍 Related Issues

- #4254: the parent tracking issue.
- Stacked on #6620 (merge that first). #6620 adds SM107 (Rubin), and the
diff against its head is this change.
- #6613: the previous PR in this series. #6620 stacks on it.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

The CPU precheck runs pre-commit on the changed files and mypy at this
head (`0f545cc8`) on a CPU-only machine. The result is in the Test plan.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing. CPU precheck at this head: PASS at
0f545cc8: 5 templates byte-identical; 35 passed, 3 deselected; boundary
lint clean; pre-commit (ruff 0.12.8 included) passed with no file
modifications; mypy passed.. CI: requested after this PR opened (two bot
comments); see the PR checks..

This head is rendered from the Cake generator at ddb1ce74. The GPU
checks below ran on the Cake side at 20e74fe1 on one 8 × H100 node;
ddb1ce74 differs from 20e74fe1 only in the test template that renders
into this PR's test file, which the CPU precheck covers.

### Test plan

- [x] `tests/comm/test_qkv_norm_rope_exchange_overlap.py`: the
shape-gate default-table test checks the new SM90 verdicts (see Files).
- [ ] CPU precheck at head 0f545cc8 on a CPU-only machine:
- The five templates are byte-identical to the Cake generator's at
ddb1ce74.
- CPU tests of `tests/comm/test_qkv_norm_rope_exchange_overlap.py` with
`-k "not multi_gpu"`.
  - Pre-commit on the changed files, and mypy.
- Result: PASS at 0f545cc8: 5 templates byte-identical; 35 passed, 3
deselected; boundary lint clean; pre-commit (ruff 0.12.8 included)
passed with no file modifications; mypy passed.
- [ ] CI: `@flashinfer-bot run
tests/comm/test_qkv_norm_rope_exchange_overlap.py` and a scoped internal
CI run, requested after this PR opens. Status: requested after this PR
opened (two bot comments); see the PR checks.
- [ ] GPU verification on the Cake side at 20e74fe1 (8 × H100; see the
note above on ddb1ce74):
- Correctness rows for groups of 8, 4 and 2 ranks at the new default.
Per-rank output digests are compared bitwise with gate-off runs: W = 8
and W = 2 against the round-4 gate-off arm, and W = 4 against the
round-3 final gate-off arm.
  - CUDA-graph replay: at least 3 replays, which must be bit-identical.
- Two-communicator concurrency, end to end through torchrun at W = 8, 4
and 2.
  - Smoke overlap timeline.
- compute-sanitizer synccheck, memcheck and racecheck, which must report
0 errors.
- Result: PASS. Output digests of the W = 8 / 2 / 4 correctness rows are
bitwise identical to the gate-off runs (2 rows / 36 arms, 3 rows / 66
arms, 4 rows / 76 arms; 0 differ). CUDA-graph replay passed on both rows
(guard bit-identical on every rank and tensor, no
replay_not_reproduced). Two-communicator torchrun e2e passed at W = 8, 4
and 2. Smoke timeline passed. synccheck, memcheck and racecheck each
reported 0 errors on 8 of 8 ranks, with 48 of 48 shape-gate records as
expected. Note: two result readers embedded in the gate script had
porting defects (an assertion on a replay-count field the receipts never
fill; rows counted per row:layout), so the step itself exited FAIL;
re-reading the same receipts and logs with the round-3 acceptance
readers gives PASS everywhere, and no GPU observation failed. 8 × H100,
2026-10-18 02:11–02:43 UTC.
- [x] Program identity: no generated `.cu` file changes against #6620.
On the Cake side, the 15 generated programs compile to byte-identical
cubins on sm_90a, sm_100a and sm_103a (15 of 15).
- [x] Performance on 8 × H100 (see Speedup).

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

- Stacked on #6620 (merge that first); the diff against #6620's head is
this change. This PR's own change is one commit, 0f545cc8, on top of the
#6620 head 290d89db. Until #6620 merges, this PR also shows #6620's
commit. The base is upstream main 5e454aa7.
- Only the SM90 default changes. The SM100, SM103 and SM107 rows, the
programs, the loader and the benchmark are unchanged.
- Calls with more than 4096 rows per rank were not measured again for
this change. The gate does not fire for them, so they take the same plan
as before.
- This PR does not claim bitwise output identity from the performance
run, because that run recorded no output digests for this change on
SM90. The evidence is the GPU verification in the Test plan.
- Opt-out:
`FLASHINFER_QKV_EXCHANGE_SHAPE_GATES=words_capacity_small_m=0` restores
the previous SM90 plan for a session, rank-uniformly.

## Speedup

### Hopper (H100 80 GB, 8 GPUs per node)

* Setup: a single node with an NVLink mesh. Groups of 8, 4 and 2 ranks.
* Protocol: OFF/ON A/B/B/A pairs. Each group size ran within one node
allocation: W = 8 on one allocation, W = 4 and W = 2 on another. CUPTI
kernel spans with a cold L2. Medians over 5 A/B/B/A rounds. The A/A
control is at most 1 %.
* Metric: the median exchange-window time in ms.

Rows are given as hidden × S_global. M is the number of rows per rank.

| W | row | M | OFF ms | ON ms | gain | A/A (OFF / ON) |
|---|---|---|---|---|---|---|
| 8 | 3072 × 4096 | 512 | 0.091775 | 0.090687 | +1.19 % | 0.10 % / 0.48
% |
| 4 | 4096 × 4096 | 1024 | 0.186766 | 0.186014 | +0.40 % | 0.07 % / 0.07
% |
| 2 | 3072 × 8192 | 4096 | 0.415388 | 0.413660 | +0.42 % | 0.02 % / 0.04
% |

* The Cake side applies two adoption readings: a strict reading and a
second reading from its design note. Both adopt the gate at every group
size.
* The round-1 Hopper measurement had left this gate off on SM90. This
measurement and the user decision of round 4 reverse that outcome.
* Rows with M above 4096 take the same plan with or without this change,
so they were not measured again.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added architecture-aware defaults and configuration options for QKV
exchange launch paths, producer variants, grouped scaling, and row-count
gates.
  * Extended Cake backend support to SM107 for groups of 2 or 4 ranks.
* Added benchmark options for backend and launch-path selection, with
expanded correctness and timing results.
* **Documentation**
* Documented the new configuration settings, supported architectures,
and benchmark behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6338871](https://github.com/flashinfer-ai/flashinfer/commit/6338871aba046b523265c70c02de167dbbeeb075)

- **作者**: Vincent
- **时间**: 2026-10-19T18:52:09Z
- **提交信息**: perf(moe): retune the routingCustom split-topK dispatch rule (#6555)

<!-- .github/pull_request_template.md -->

## 📌 Description

`routingCustom::run` takes the split topK path (block-per-token scores
kernel + post-topK pipeline, PDL-chained) instead of the fused
single-cluster kernel whenever `numExperts >= 160` in the single-cluster
batch range. A routing-only sweep on current kernels shows that rule is
wrong in both directions:

- **Non-sigmoid-bias policies with E >= 160:** the fused single-cluster
kernel is faster up to 64 tokens (the scores kernel + PDL handoff cost
more than the cluster kernel's idle warps). Exception: E >= 512 with 10
<= K <= 16 from 32 tokens.
- **E < 160:** splitting is up to 2.4x faster once K >= 8 and tokens * K
>= 1536. Today this range never splits.
- **Sigmoid+bias policies (DeepSeekV3 nGroup=1, MiniMax2) with E >=
160:** splitting stays best, so they keep the current behavior.

This PR replaces the `numExperts >= 160` condition with that rule. The
`FLASHINFER_ROUTING_FORCE_BLOCK_PER_TOKEN` override, the static-block
boundary, and all kernels are unchanged.

### Sweep

`trtllm_moe_run_routing` timed alone (routing kernels only, CUDA graph
over 16 routings, median of 20 replays) for every routingCustom policy
(Default, Renormalize, RenormalizeNaive, TopK, Sigmoid, SigmoidRenorm,
TopKSigmoid, DeepSeekV3 nGroup=1, MiniMax2), over E ∈ {128, 160, 256,
384, 512, 896, 1024}, K ∈ {4, 6, 8, 10, 16, 22} and tokens ∈ {1, 4, 8,
16, 17, 24, 32, 48, 64, 96, 128, 192, 256}, using the env override to
force each path. That is 2769 supported shapes on SM100 (GB200), SM103
(GB300) and SM107 (Rubin).

The rule was derived from that sweep, then validated by an A/B of the
actual code (both legs `auto`, 2 interleaved rounds). Results on the 736
shapes where the decision changes:

| | SM107 | SM103 | SM100 |
|---|---|---|---|
| geomean speedup | 1.106x | 1.080x | 1.078x |
| range | 0.95-1.92x | 0.96-2.43x | 0.96-2.39x |
| same-path noise (p1-p99 of unchanged shapes) | 0.94-1.10 | 0.95-1.06 |
0.94-1.05 |

Per policy (geomean on changed shapes, SM107 / SM103 / SM100):
- DeepSeekV3 nGroup=1: 1.58 / 1.88 / 1.86x
- MiniMax2: 1.57 / 1.88 / 1.86x
- Renormalize: 1.09 / 1.06 / 1.06x
- RenormalizeNaive: 1.10 / 1.06 / 1.06x
- Default: 1.11 / 1.07 / 1.06x
- TopK: 1.12 / 1.08 / 1.08x
- TopKSigmoid: 1.10 / 1.04 / 1.03x
- Sigmoid: 1.06 / 1.06 / 1.05x
- SigmoidRenorm: 1.06 / 1.05 / 1.05x

No changed shape is slower beyond the same-path noise band.

## 🔍 Related Issues

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (clang-format 19.1.1 on the changed file)

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- `tests/moe/test_trtllm_gen_routing.py` +
`tests/moe/test_trtllm_gen_fused_moe_routing_renormalize_fp4.py`: SM103
710 passed / 10 xfailed, SM100 720 passed, 0 failed.
- SM107: the standalone `trtllm_gen_routing` API (and so
`test_trtllm_gen_routing.py`) is not enabled on SM107, so SM107 was
validated through the fused MoE path instead. 288 randomly selected
cases with 17-256 tokens (where the decision changes) from
`test_trtllm_gen_fused_moe.py` and the three
`test_trtllm_gen_fused_moe_routing_renormalize_*` files: 169 passed, 0
failed, 119 skipped by the tests' own incompatibility filters.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Refined when split-TopK routing is selected for eligible workloads,
using expert count, topK, token count, and preprocessing type. This
adjusts routing behavior across a broader range of input sizes and
configurations, with potential performance improvements for qualifying
workloads.
* **Documentation**
* Updated descriptions of the routing criteria and related measurements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ee84ecd](https://github.com/flashinfer-ai/flashinfer/commit/ee84ecd2bc767013418950ea7ce46847ddfb05b0)

- **作者**: eigen
- **时间**: 2026-10-19T18:12:26Z
- **提交信息**: feat(cake_fp8_rowwise_gemm_allreduce): fused row-wise FP8 GEMM + all-reduce backend (SM100, four ranks) (#6583)

Cake's fused row-wise FP8 GEMM + all-reduce works on per-rank operands
A_r [M, K_l] and W_r [N, K_l] in FP8 e4m3, with an fp32 row scale per M
row, an fp32 column scale per N column and fp32 accumulation. It sums
the scaled partial products across ranks and gives every rank the bf16
[M, N] result, all in one fused kernel with no separate all-reduce
collective per call. Cake has one data-type variant of this kernel (FP8
e4m3 in, fp32 scales, bf16 out) and three fused forms that differ by
communication carrier: a GEMM-only form, a peer-to-peer carrier for
world sizes 2 and 4, and an NVLink-multicast (NVLS) carrier for world
size 8. This PR delivers the sm_100a, world-size-4, peer-to-peer variant
as `flashinfer.comm.fp8_rowwise_gemm_allreduce` /
`prepare_fp8_rowwise_gemm_allreduce` with `backend="cake"`, as requested
in #6302. Cake has not shipped an earlier version of this kernel, so the
baseline is `torch._scaled_mm` row-wise FP8 (cuBLASLt) followed by
`torch.distributed.all_reduce` in bf16 (NCCL 2.29.7). The new kernel is
faster on 10 of the 48 shapes: all six MLP shapes with N = 8192
(1.062x–1.454x) and the four MLP shapes with N = 6144 and M ≥ 16384
(1.059x–1.131x). It is slower on the other 38 shapes (0.488x–0.992x),
and the geometric mean over all 48 shapes is 0.827x.

### Speedup

Setup: four NVIDIA B200 GPUs (sm_100a) in one node, CUDA 13.0 runtime,
driver 580.82.07, PyTorch 2.13.0+cu130 and NCCL 2.29.7. The baseline is
`torch._scaled_mm` row-wise FP8 (cuBLASLt, bf16 output) followed by
`torch.distributed.all_reduce` in bf16. Times are CUPTI GPU kernel spans
(rank maximum of per-rank medians), measured in one session with ABBA
interleaving. Speedup = baseline / this PR, so values above 1 mean this
PR is faster. The measured program is the kernel's evaluation launcher,
and the exported FlashInfer entry point reproduces it within 2 % on
every row. M is rows, N is output columns and K per rank = K_l (total K
= 4·K_l). MLP rows have K_l = N and O-proj rows have K_l = N/4.

| Shape group | M | N | K per rank | This PR, ms | Baseline, ms |
Speedup |
|---|--:|--:|--:|--:|--:|--:|
| MLP (K = 4N) | 4096 | 3072 | 3072 | 0.1806 | 0.1702 | 0.943x |
| MLP (K = 4N) | 8192 | 3072 | 3072 | 0.3144 | 0.2311 | 0.735x |
| MLP (K = 4N) | 16384 | 3072 | 3072 | 0.6096 | 0.3988 | 0.654x |
| MLP (K = 4N) | 32768 | 3072 | 3072 | 1.1779 | 0.7661 | 0.650x |
| MLP (K = 4N) | 65536 | 3072 | 3072 | 2.2914 | 1.4754 | 0.644x |
| MLP (K = 4N) | 131072 | 3072 | 3072 | 4.6107 | 2.9003 | 0.629x |
| MLP (K = 4N) | 4096 | 4096 | 4096 | 0.2012 | 0.1903 | 0.946x |
| MLP (K = 4N) | 8192 | 4096 | 4096 | 0.3548 | 0.3051 | 0.860x |
| MLP (K = 4N) | 16384 | 4096 | 4096 | 0.6685 | 0.5739 | 0.858x |
| MLP (K = 4N) | 32768 | 4096 | 4096 | 1.2804 | 1.1275 | 0.881x |
| MLP (K = 4N) | 65536 | 4096 | 4096 | 2.5062 | 2.2137 | 0.883x |
| MLP (K = 4N) | 131072 | 4096 | 4096 | 4.9547 | 4.4227 | 0.893x |
| MLP (K = 4N) | 4096 | 6144 | 6144 | 0.3058 | 0.2818 | 0.921x |
| MLP (K = 4N) | 8192 | 6144 | 6144 | 0.5164 | 0.5123 | 0.992x |
| MLP (K = 4N) | 16384 | 6144 | 6144 | 0.9493 | 1.0049 | 1.059x |
| MLP (K = 4N) | 32768 | 6144 | 6144 | 1.8208 | 1.9901 | 1.093x |
| MLP (K = 4N) | 65536 | 6144 | 6144 | 3.5251 | 3.9752 | 1.128x |
| MLP (K = 4N) | 131072 | 6144 | 6144 | 7.0329 | 7.9529 | 1.131x |
| MLP (K = 4N) | 4096 | 8192 | 8192 | 0.3803 | 0.4037 | 1.062x |
| MLP (K = 4N) | 8192 | 8192 | 8192 | 0.6411 | 0.7886 | 1.230x |
| MLP (K = 4N) | 16384 | 8192 | 8192 | 1.1725 | 1.5913 | 1.357x |
| MLP (K = 4N) | 32768 | 8192 | 8192 | 2.2583 | 3.1882 | 1.412x |
| MLP (K = 4N) | 65536 | 8192 | 8192 | 4.4170 | 6.3837 | 1.445x |
| MLP (K = 4N) | 131072 | 8192 | 8192 | 9.0047 | 13.0915 | 1.454x |
| O-proj (K = N) | 4096 | 3072 | 768 | 0.1745 | 0.1674 | 0.959x |
| O-proj (K = N) | 8192 | 3072 | 768 | 0.3046 | 0.2122 | 0.697x |
| O-proj (K = N) | 16384 | 3072 | 768 | 0.6208 | 0.3488 | 0.562x |
| O-proj (K = N) | 32768 | 3072 | 768 | 1.1841 | 0.6144 | 0.519x |
| O-proj (K = N) | 65536 | 3072 | 768 | 2.3252 | 1.1711 | 0.504x |
| O-proj (K = N) | 131072 | 3072 | 768 | 4.6412 | 2.2646 | 0.488x |
| O-proj (K = N) | 4096 | 4096 | 1024 | 0.1909 | 0.1814 | 0.950x |
| O-proj (K = N) | 8192 | 4096 | 1024 | 0.3440 | 0.2456 | 0.714x |
| O-proj (K = N) | 16384 | 4096 | 1024 | 0.6591 | 0.4437 | 0.673x |
| O-proj (K = N) | 32768 | 4096 | 1024 | 1.2887 | 0.8542 | 0.663x |
| O-proj (K = N) | 65536 | 4096 | 1024 | 2.5287 | 1.6302 | 0.645x |
| O-proj (K = N) | 131072 | 4096 | 1024 | 5.0778 | 3.1791 | 0.626x |
| O-proj (K = N) | 4096 | 6144 | 1536 | 0.2829 | 0.2219 | 0.784x |
| O-proj (K = N) | 8192 | 6144 | 1536 | 0.4878 | 0.3504 | 0.718x |
| O-proj (K = N) | 16384 | 6144 | 1536 | 0.9161 | 0.6741 | 0.736x |
| O-proj (K = N) | 32768 | 6144 | 1536 | 1.7986 | 1.2832 | 0.713x |
| O-proj (K = N) | 65536 | 6144 | 1536 | 3.5564 | 2.5093 | 0.706x |
| O-proj (K = N) | 131072 | 6144 | 1536 | 7.0422 | 4.9572 | 0.704x |
| O-proj (K = N) | 4096 | 8192 | 2048 | 0.3277 | 0.2604 | 0.794x |
| O-proj (K = N) | 8192 | 8192 | 2048 | 0.5803 | 0.4787 | 0.825x |
| O-proj (K = N) | 16384 | 8192 | 2048 | 1.1041 | 0.9235 | 0.836x |
| O-proj (K = N) | 32768 | 8192 | 2048 | 2.1590 | 1.7816 | 0.825x |
| O-proj (K = N) | 65536 | 8192 | 2048 | 4.2493 | 3.5101 | 0.826x |
| O-proj (K = N) | 131072 | 8192 | 2048 | 8.4387 | 6.9457 | 0.823x |

Besides this variant, Cake has a GEMM-only form, a world-size-2
peer-to-peer form and a world-size-8 NVLS form, and the world-size-2 and
world-size-8 forms are not part of this PR; this PR ships the family on
sm_100a, the sm_103a build has been measured but is not exported yet,
and an sm_90a implementation is in development.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [51a2fde](https://github.com/flashinfer-ai/flashinfer/commit/51a2fde6c9925293e0fcfd66178151e91aaa5a64)

- **作者**: eigen
- **时间**: 2026-10-19T17:43:22Z
- **提交信息**: feat(cake_kda): packed KDA chunked training kernels (forward and backward) for GLM-5.3-Flash grad (#6787)

This PR adds `flashinfer.experimental.cake_kda_train`: forward,
first-order backward and checkpoint replay (backward without saved
activations) for packed variable-length KDA (Kimi Delta Attention)
chunked training in the GLM-5.3-Flash geometry. That geometry uses head
dimension 128 for q, k, v and the gate, chunk length 64, a zero initial
state per document, 1 to 64 heads per call and one packed batch
described by `cu_seqlens`. This operator has a single Cake variant (BF16
q, k, v, out, dq, dk, dv and dbeta; FP32 gate g, dg and recurrent state;
packed `[1, S, H, 128]` layout), and this PR delivers it with both save
modes: `light` (the default, measured below) and `tape` (keeps the state
tape for a faster backward). No previous Cake version of this kernel is
shipped, so the baseline is the Triton `chunk_kda` from FLA 0.6.0
(commit ce50999e), with the same L2 normalization, gate pre-activation
and sigmoid(beta) applied outside both implementations. Times are kernel
times from CUPTI with a cold L2 cache (median of three interleaved
groups of 64 iterations); bwd is the backward from saved activations
including its recomputation, ckpt is forward + replay + backward, P1–P8
are packs of 3–4 documents at H=4, and P9–P14 vary H at S=261393.
Speedups are 1.60×–6.12× on GB300, 1.66×–6.05× on B200 and 1.55×–8.75×
on R200, lowest at P12 bwd (P14 bwd on R200) and highest at P9 fwd.

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4**

| Shape (H, S) | fwd Cake / FLA ms | fwd speedup | bwd Cake / FLA ms |
bwd speedup | ckpt fwd+bwd Cake / FLA ms | ckpt speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 2.057 / 10.594 | 5.15× | 5.049 / 20.487 | 4.06× |
9.116 / 41.656 | 4.57× |
| P2 (H=4, S=245028) | 2.018 / 6.936 | 3.44× | 4.997 / 13.356 | 2.67× |
8.978 / 27.219 | 3.03× |
| P3 (H=4, S=249866) | 2.092 / 8.205 | 3.92× | 5.191 / 15.811 | 3.05× |
9.322 / 32.210 | 3.46× |
| P4 (H=4, S=250340) | 2.078 / 7.193 | 3.46× | 5.140 / 13.847 | 2.69× |
9.237 / 28.222 | 3.06× |
| P5 (H=4, S=258574) | 2.089 / 8.703 | 4.17× | 5.208 / 16.781 | 3.22× |
9.334 / 34.183 | 3.66× |
| P6 (H=4, S=259042) | 2.091 / 6.752 | 3.23× | 5.172 / 12.978 | 2.51× |
9.297 / 26.458 | 2.85× |
| P7 (H=4, S=259584) | 2.156 / 8.193 | 3.80× | 5.353 / 15.788 | 2.95× |
9.596 / 32.151 | 3.35× |
| P8 (H=4, S=261393) | 2.036 / 7.259 | 3.57× | 5.105 / 13.978 | 2.74× |
9.115 / 28.488 | 3.13× |
| P9 (H=1, S=261393) | 0.784 / 4.802 | 6.12× | 1.756 / 9.387 | 5.35× |
3.290 / 18.853 | 5.73× |
| P10 (H=2, S=261393) | 1.189 / 5.104 | 4.29× | 2.856 / 10.711 | 3.75× |
5.197 / 20.820 | 4.01× |
| P11 (H=8, S=261393) | 3.823 / 8.280 | 2.17× | 9.876 / 20.201 | 2.05× |
17.459 / 36.756 | 2.11× |
| P12 (H=16, S=261393) | 7.922 / 12.768 | 1.61× | 21.016 / 33.695 |
1.60× | 36.838 / 59.215 | 1.61× |
| P13 (H=32, S=261393) | 13.837 / 22.747 | 1.64× | 38.522 / 61.868 |
1.61× | 66.165 / 107.396 | 1.62× |
| P14 (H=64, S=261393) | 26.481 / 47.207 | 1.78× | 75.844 / 121.970 |
1.61× | 128.807 / 216.380 | 1.68× |

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4**

| Shape (H, S) | fwd Cake / FLA ms | fwd speedup | bwd Cake / FLA ms |
bwd speedup | ckpt fwd+bwd Cake / FLA ms | ckpt speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 2.179 / 10.645 | 4.88× | 5.513 / 23.095 | 4.19× |
9.864 / 44.378 | 4.50× |
| P2 (H=4, S=245028) | 2.133 / 6.793 | 3.18× | 5.465 / 15.605 | 2.86× |
9.738 / 29.182 | 3.00× |
| P3 (H=4, S=249866) | 2.225 / 8.119 | 3.65× | 5.684 / 18.222 | 3.21× |
10.130 / 34.443 | 3.40× |
| P4 (H=4, S=250340) | 2.206 / 7.065 | 3.20× | 5.604 / 16.182 | 2.89× |
10.013 / 30.304 | 3.03× |
| P5 (H=4, S=258574) | 2.204 / 8.642 | 3.92× | 5.684 / 19.325 | 3.40× |
10.123 / 36.602 | 3.62× |
| P6 (H=4, S=259042) | 2.200 / 6.584 | 2.99× | 5.633 / 15.327 | 2.72× |
10.056 / 28.482 | 2.83× |
| P7 (H=4, S=259584) | 2.265 / 8.087 | 3.57× | 5.835 / 18.270 | 3.13× |
10.379 / 34.427 | 3.32× |
| P8 (H=4, S=261393) | 2.144 / 7.115 | 3.32× | 5.559 / 16.377 | 2.95× |
9.891 / 30.606 | 3.09× |
| P9 (H=1, S=261393) | 0.794 / 4.807 | 6.05× | 1.868 / 9.622 | 5.15× |
3.474 / 19.252 | 5.54× |
| P10 (H=2, S=261393) | 1.229 / 6.127 | 4.98× | 3.070 / 11.876 | 3.87× |
5.546 / 24.158 | 4.36× |
| P11 (H=8, S=261393) | 4.301 / 12.194 | 2.83× | 11.445 / 24.335 | 2.13×
| 20.212 / 48.719 | 2.41× |
| P12 (H=16, S=261393) | 8.417 / 17.341 | 2.06× | 23.099 / 38.413 |
1.66× | 39.976 / 73.125 | 1.83× |
| P13 (H=32, S=261393) | 15.333 / 30.955 | 2.02× | 42.805 / 78.079 |
1.82× | 73.895 / 140.061 | 1.90× |
| P14 (H=64, S=261393) | 29.842 / 59.184 | 1.98× | 85.068 / 151.546 |
1.78× | 145.254 / 269.905 | 1.86× |

**NVIDIA R200 (sm_107a, 212 SMs), CUDA 13.5**

| Shape (H, S) | fwd Cake / FLA ms | fwd speedup | bwd Cake / FLA ms |
bwd speedup | ckpt fwd+bwd Cake / FLA ms | ckpt speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 1.257 / 8.617 | 6.86× | 3.133 / 16.637 | 5.31× |
5.654 / 33.877 | 5.99× |
| P2 (H=4, S=245028) | 1.203 / 4.977 | 4.14× | 3.048 / 10.152 | 3.33× |
5.492 / 20.212 | 3.68× |
| P3 (H=4, S=249866) | 1.244 / 6.228 | 5.01× | 3.139 / 12.365 | 3.94× |
5.632 / 24.825 | 4.41× |
| P4 (H=4, S=250340) | 1.203 / 5.205 | 4.33× | 3.086 / 10.580 | 3.43× |
5.511 / 20.987 | 3.81× |
| P5 (H=4, S=258574) | 1.271 / 6.390 | 5.03× | 3.203 / 12.812 | 4.00× |
5.722 / 25.587 | 4.47× |
| P6 (H=4, S=259042) | 1.242 / 4.528 | 3.65× | 3.157 / 9.481 | 3.00× |
5.664 / 18.536 | 3.27× |
| P7 (H=4, S=259584) | 1.306 / 6.140 | 4.70× | 3.318 / 12.281 | 3.70× |
5.933 / 24.573 | 4.14× |
| P8 (H=4, S=261393) | 1.210 / 5.211 | 4.31× | 3.107 / 10.636 | 3.42× |
5.533 / 21.056 | 3.81× |
| P9 (H=1, S=261393) | 0.482 / 4.222 | 8.75× | 1.127 / 7.700 | 6.83× |
2.096 / 16.136 | 7.70× |
| P10 (H=2, S=261393) | 0.744 / 4.332 | 5.82× | 1.792 / 8.470 | 4.73× |
3.299 / 17.158 | 5.20× |
| P11 (H=8, S=261393) | 2.328 / 6.440 | 2.77× | 6.182 / 14.334 | 2.32× |
10.880 / 27.211 | 2.50× |
| P12 (H=16, S=261393) | 4.838 / 9.019 | 1.86× | 13.505 / 21.849 | 1.62×
| 23.158 / 39.923 | 1.72× |
| P13 (H=32, S=261393) | 8.133 / 14.449 | 1.78× | 23.525 / 37.772 |
1.61× | 39.749 / 66.664 | 1.68× |
| P14 (H=64, S=261393) | 15.332 / 25.280 | 1.65× | 46.262 / 71.624 |
1.55× | 76.936 / 122.170 | 1.59× |

Cake ships no other data-type or layout variant of this training
operator (Cake's KDA decode and prefill kernels are separate operators),
and this kernel family builds for sm_100a (B200), sm_103a (GB300) and
sm_107a (R200).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added experimental packed KDA chunked-training support, including
forward, backward, autograd, and workspace APIs for supported GPU
architectures.
* Added options to save intermediate state or use checkpoint replay,
along with workspace and saved-memory sizing queries.
* Added a benchmark for training boundaries, with optional comparison
against an external implementation.

* **Documentation**
* Added guidance on API usage, supported inputs, memory requirements,
and device support.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [eca987e](https://github.com/flashinfer-ai/flashinfer/commit/eca987e198e06d3d6691ba9f09d5bdba58c78416)

- **作者**: eigen
- **时间**: 2026-10-19T17:42:35Z
- **提交信息**: deslop(cake_kimi_k3_fp8_projection): share kernel/launcher sources, slim MODULES, drop dead host code (#6780)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR removes duplicated code from the experimental Cake-generated FP8
projection GEMM for the Kimi-K3 KDA / MLA projections, following #6653.
The family lives in `flashinfer/experimental/kimi_k3_fp8_projection/`.
It is exposed as
`flashinfer.gemm.{prepare_kimi_k3_fp8_projection_weights,
prepare_kimi_k3_fp8_projection, kimi_k3_fp8_projection,
kimi_k3_fp8_projection_launcher}` with `backend="cake"`, JIT only, on
sm_100a and sm_103a.
- 32 lever-twin kernel sources and 53 launcher-twin bindings are
deleted. Their records now build a shared source with their own `-D`
flags.
- `MODULES` becomes per-program rows plus five argument plans.
- The dispatch table drops 108 default-valued or unread keys.
- Dead and test-only host code is removed.
- Wheels now ship the family's `csrc/` tree.

Diff against the base: 171 files, +3,862 / -78,089 (net -74,227).

Every one of the 107 records keeps its name, JIT spec name
(`<name>_<arch>[_defines]_<closure20>`), kernel symbol, host-shim
namespace, `arches` and argument plan. `KERNELS` is unchanged: 109 keys
onto the 107 records, with 81 records building for sm_100a and 82 for
sm_103a. Program selection, launch arguments and results are unchanged
for every input.

**Behaviour changes** (all deliberate):
- **Stale JIT workspaces.** 32 records now build a sibling's kernel
source and 53 records build a sibling's launcher source. Each passes its
own `-D` flags: `-DCAKE_PROGRAM_KERNEL=<symbol>`,
`-DCAKE_PROGRAM_SHIM=<namespace>`, plus a lever define for the folded
kernels. Because spec names are unchanged, a JIT build directory from
before this change holds objects built from the deleted sources. Start
from a fresh JIT workspace for this family's modules when upgrading. The
validation below uses a fresh workspace per tree.
- **Host-check backtraces.** `TVM_FFI_CHECK` / `TVM_FFI_THROW`
backtraces in the bindings now name the shared launcher file and its
line numbers, not the record's own binding. For the hoisted receipt /
chain text they name the host preamble instead. Message texts are
unchanged. Conditions that name the kernel symbol are pre-expanded, so
the message still shows the symbol, not the macro.
- **Removed Python surface.** None of these names has an in-tree reader
outside the family, but an out-of-tree reader would break.
- `cake_backend.py`: `generated_program_available`, `unswizzle_sf_128x4`
and `n_padded_128` (moved into the test / benchmark that used them);
`gemm_cs_k_ranges`; `gemm_cs_suffix`.
- `cake_backend.py`, ordered stream-K host path: `StreamKPlan`,
`gemm_stream_k*`, `ProjectionPlan.gemm_sk`, the `GEMM_SK_*` constants,
and the `_sk` / `_sks` / `_skf4` / `_skf8` branches of
`required_kernel_keys` and `route_plan`.
- `cake_jit.py`: the `MODULES[*]` keys `role` and `ffi_entry`. `MODULES`
is now expanded at import from `_PROGRAMS` rows and `ARG_PLANS`, which
are new public names.
- **Dispatch table.** `decode_table.py` loses 108 default-valued or
unread keys. `decode_config` returns the same configuration for every
cell.
- **Wheels.** A non-editable install now ships the family's `csrc/` tree
(156 files: 129 `.cu`, 26 `.cuh`, the README). Before this, the first
JIT build of any record failed on a missing source; now it succeeds. The
issue asked for this fix as a separate small PR. It lands here as its
own commit (5) so that the shipped tree is the deduplicated one.
- **Tests.** Two new CPU tests:
`test_shared_kernel_sources_keep_distinct_symbols` and
`test_shared_launcher_sources_keep_distinct_namespaces`. One new
registry assertion: `MODULES[name]["arg_plan"] in ARG_PLANS`. The
stream-K test pieces and the literal keys of never-built programs are
updated. Collected ids go from 81 to 83 and none are removed.
- **Docs.**
- The README's generated-sources paragraph now describes the shared
sources. It also discloses that the registry rows, the table edit and
the shared kernel / launcher sources are a hand fold of the exported
files, pending regeneration by the exporter.
- The README's benchmark paragraph is corrected to 132 rows and M in {1,
8, 64, 256, 4096, 16384}. It previously said 198 rows and nine M values.
- `csrc/README.md` now describes the flat layout; the `<arch>/`
subdirectories it documented no longer exist. It no longer says the
files must not be edited by hand.

## Changes

Footprint against the base:

| | Base | Head |
|---|---:|---:|
| `csrc/` `.cu` files | 214 | 129 |
| `cake_kimi_k3_fp8_projection_host_common.cuh` (lines) | 52 | 182 |
| `cake_jit.py` (lines) | 4,657 | 1,816 |
| `cake_backend.py` (lines) | 4,520 | 4,287 |
| `decode_table.py` (lines) | 1,363 | 1,252 |
| `test_cake_kimi_k3_fp8_projection.py` (lines) | 2,745 | 2,766 |

At the base, the 214 `.cu` files were 107 kernel translation units and
107 TVM-FFI bindings. 85 are deleted: 32 kernels and 53 bindings.
- 75 kernels are kept. 52 are byte-identical to the base. The other 23
change only in `#ifndef` defaults, `#if` / `#elif` lever arms and the
`CAKE_PROGRAM_KERNEL(` definition line.
- 54 launcher bindings are kept, parameterised the same way.

### 1. Fold 32 lever-twin kernel sources into 23 (`8371f1f28`; 58 files,
+1,117 / -20,986)
- 55 kernel sources fall into clusters whose members differ only by a
lever literal (`GROUP_M`, a prefetch distance, a stage or slot count) or
by a lever-guarded block.
- One kernel per cluster stays (23 files). Each kept kernel has `#ifndef
CAKE_LEVER_<X>` / `#ifndef GROUP_M` defaults equal to its own values (26
+ 2 guards) and `#if` / `#elif CAKE_LEVER_<X>` arms (34 in total) for
its siblings' variants. It names its symbol through
`CAKE_PROGRAM_KERNEL`, with an `#ifndef` default.
- The other 32 kernel files (20,886 lines) are deleted. Their records
build the kept source with `-DCAKE_LEVER_<X>=<n>` or `-DGROUP_M=64`,
plus `-DCAKE_PROGRAM_KERNEL=<own symbol>` / `-DCAKE_PROGRAM_SHIM=<own
namespace>`.
- The 14 cluster members that cannot be reproduced by define
substitution and `#if` arms stay as their own sources.
- Proof: rendering each kept source with each removed record's defines
reproduces the removed kernel line for line. This covers 32 fold renders
and 23 identity renders: 630 checks, 0 differing lines.
- `test_shared_kernel_sources_keep_distinct_symbols` pins distinct
per-record symbols. Covers step 2.

### 2. Drop default-valued dispatch-table keys (`ebcde26e3`; 1 file, +1
/ -112)
- Removes 108 keys from `decode_table.py`: `resident: False` x103, `pf:
0` x2, `gemm_sk: 0`, `tstore: False`, and the unconsumed
`gemm_sk_ksplit: 28`.
- `persist: False` (x25) stays because it is not the default. `fused`
stays because it is required.
- Proof: re-expanding the trimmed table with `decode_config`'s defaults
gives the base table cell by cell (218 cells, 0 differences). The 68
per-arch overrides stay distinct.
- Covers step 4 as a hand edit of the exported table; the exporter is
not changed.

### 3. Drop dead and test-only host helpers (`22407b2e4`; 5 files, +45 /
-73)
- Deletes `gemm_cs_k_ranges` and `gemm_cs_suffix`, which have no
callers.
- Moves `generated_program_available`, `unswizzle_sf_128x4` and
`n_padded_128` into the test and benchmark, their only users.
- Rewrites `csrc/README.md` for the flat layout and fixes the package
README's benchmark paragraph. Covers step 5.

### 4. Remove the dead ordered stream-K host path (`93240293a`; 2 files,
+90 / -367)
- The stream-K host code never ran: `gemm_sk` / `gemm_sks` appear in no
table cell, and no `_sk`, `_sks<n>`, `_skf4` / `_skf8` or `_cs3` program
is registered.
- Removes `StreamKPlan`, `gemm_stream_k*`, `ProjectionPlan.gemm_sk`, the
`GEMM_SK_*` constants, the stream-K branches of `required_kernel_keys`
and the `_sk` candidates of `route_plan`.
- Keeps the code that is still live: `gemm_cs_row_form`,
`GEMM_CS_FORMS`, and the fractional-wave fix-up levers `gemm_skf` and
`_skp`.
- The test drops its stream-K pieces and the literal keys of never-built
programs. It now asserts that no table cell asks for `gemm_sk`, and that
`required_kernel_keys` names no `_sk` / `_sks<n>` / `_skf4` / `_skf8`
program on either architecture. Covers step 6.

### 5. Ship the generated `csrc/` tree in wheels (`fc05255a0`; 1 file,
+2 / -0)
- Adds the missing `[tool.setuptools.package-data]` entry
`"flashinfer.experimental.kimi_k3_fp8_projection" = ["csrc/**"]`.
- `pyproject.toml` sets `include-package-data = false`, so a package's
`csrc/` reaches a wheel only when it is listed there. The loader
resolves every source relative to its own module file, so this one entry
is the whole fix.
- Covers the packaging step. It lands in this PR rather than a separate
one; see Summary.

### 6. Slim `MODULES` to rows and five argument plans (`9ff3658dd`; 4
files, +555 / -3,721)
- The 107-record `MODULES` literal (3,939 lines) repeated five argument
plans 107 times and carried two constant fields, `role` and `ffi_entry`.
- It is replaced by `ARG_PLANS` and `_PROGRAMS`:
- `ARG_PLANS` holds the five plans by name: `decode` (51 records),
`decode_tso` (16), `gemm` (38), `gemm_skp` (1) and `quant` (1).
- `_PROGRAMS` has one row per program with `arches`, `arg_plan` and the
closure digest. Where they differ from the family default, a row also
carries `compile_flags`, the sibling whose `kernel` or `binding` source
it builds, or an explicit `sources` list.
- A 12-line builder expands `MODULES` from the rows at import. The
planner reads the plan through `ARG_PLANS`.
- Proof: the expanded registry equals the previous literal record by
record (107 / 107 records, 2,476 field checks, 0 differences).
- Covers the registry half of step 3 as a hand fold; the exporter is not
changed.

### 7. Share launcher twins and hoist the receipt text (`8da0b3fba`; 112
files, +2,162 / -52,940)
- With the program hash and the host-shim hash normalised, the 107
bindings had 54 distinct bodies.
- One binding per body stays (54 files). It names its kernel symbol and
namespace through `CAKE_PROGRAM_KERNEL` / `CAKE_PROGRAM_SHIM`, with
`#ifndef` defaults.
- The other 53 bindings (46,791 lines) are deleted. Their records build
the shared body with their own `-D` pair.
- Every binding repeated the receipt-chain prefix and ABI, the receipt
header and the chain entry. These move into the host preamble as three
include parts.
- `TVM_FFI_CHECK` conditions that mention the kernel symbol go through a
pre-expanding macro, so their message text keeps the symbol.
- The exporter's per-file comment in the kept bindings is replaced by
one neutral line.
- Proof: rendering the shared body with each record's defines reproduces
that record's base binding line for line (107 / 107, 0 differing lines).
Of 11,122 check conditions scanned, none stringises a macro name.
- `test_shared_launcher_sources_keep_distinct_namespaces` pins distinct
per-record namespaces. Covers step 1 except the templated TMA encoders
(see Not in this PR).

## Validation

Base `3e95a1fba9` (upstream main) against head
`8da0b3fba403f3aee29fb58c894087e4ca5200f1`.

- **Device SASS gate.** There is one row per record and architecture it
lists. SM100 has 81 rows (20 fold + 61 identity); SM103 has 82 rows (25
fold + 57 identity).
- Fold rows cover the records that now build another program's kernel.
Base: the record's own deleted kernel with the base flags. Head: the
kept kernel with the record's exact flags, including its `-D` set.
- Identity rows cover the other records: the same source built with the
base recipe and with the head recipe.
- Each build is dumped with `cuobjdump`, with instruction addresses and
encodings masked, and the instruction text is compared per kernel. Each
build must contain exactly one kernel, named by the record's symbol. The
required result is identical after masking instruction addresses and
encodings.
- SM100 (81 rows, B200): 81 / 81 rows accepted: 79 identical after
masking; the other 2 identity rows (unchanged source, byte-identical
translation unit on both sides) compile to SASS that differs only in
register numbering between any two compilations of the same file,
including two compilations of the unchanged base, with the instruction
skeleton identical; which 2 rows differ changes from run to run, so this
is compiler nondeterminism, not a source difference
- SM103 (82 rows, GB300): 82 / 82 identical (25 fold rows + 57 identity
rows; exactly one kernel per build, named by the record's symbol)
- **Host gate.** There is one row per record and architecture (SM100 81,
SM103 82). Each row compares the record's own base binding with the
launcher source it builds at the head with its `-D` flags. Both must:
  - compile;
  - contain no device functions;
- have identical preprocessed text after the documented normalisations:
line markers, blank lines, unsigned-literal suffixes, adjacent string
literals, and the `__FILE__` / `__LINE__` arguments of the check macros'
backtrace;
- export the FFI entries and the shim's `Run` with no foreign namespace.
- SM100: 81 / 81 passed (all compiled, no device code, preprocessed text
identical after normalisation, the FFI entries and the shim's Run
exported, no foreign namespace)
  - SM103: 82 / 82 passed (same checks)
- **Planner proof.** This runs on CPU with the real loader, in each
architecture's environment.
- `decode_config`, `required_kernel_keys` and `route_plan` are
enumerated on base and head over every table cell, every bucket edge
+-1, every projection family and output view, both architectures, and SM
counts 148 / 152 / 160.
- The three streams must be identical: the full configuration dict, the
full key tuple and the full plan.
- The comparison fails if any `route_plan` call raised or if a record
kind is missing.
- Result: identical on both architectures' environments: the base and
head streams of decode_config, required_kernel_keys and route_plan agree
over every cell, bucket edge, family and output view at SM counts 148 /
152 / 160; every route_plan call returned a plan (no error entries,
every record kind present), and the test file's registry assertions hold
on both sides with 83 / 84 required = registered keys
- **CPU checks on the head tree.**
  - ruff / `py_compile` on the changed Python files.
- Stale-reference counts for the 85 deleted sources, the removed planner
names and the dropped keys.
- `csrc/` tree shape: 52 kept kernels byte-identical, 23 parameterised,
54 launchers, 0 literal symbols or namespaces.
  - The text proofs above, re-run.
- The registry invariant: 107 distinct symbols and namespaces, 109 keys.
- Package data: base and head wheels are built and installed into fresh
environments. The head wheel must carry the 156 `csrc/` files and the
base wheel none.
  - Collected ids: 81 -> 83.
  - The CPU test subset with CUDA hidden (head 26 passed / 57 skipped).
  - The benchmark's `--help` with CUDA hidden.
- Result: all passed on the head tree: ruff check / format clean with
the repo's configuration and py_compile ok on the changed Python files
(a stand-alone import-order lint outside that configuration reports one
finding on the test file, present identically on the base);
stale-reference counts at 0 for the 85 deleted sources, the removed
planner names and the dropped keys; csrc shape as stated (85 deleted =
32 kernels + 53 launchers, 79 modified, 52 kept kernels byte-identical,
the 23 changed kernels exactly the parameterised set, 54 launchers
through the two macros, 0 literal symbols or namespaces); the text
proofs re-run (kernel fold 630 checks / 0 differing lines, table 218
cells / 0 differences, registry 107 records / 2,476 field checks / 0
differences, launcher render 107 / 107 with 11,122 check conditions and
none stringising a macro; the gate tables regenerate identically from
the tree); registry invariant 107 distinct symbols and namespaces, 109
keys, import view equal to the text expansion; package data: setuptools
discovers the 156 csrc files on the head and none on the base, wheels of
both trees built and installed into fresh environments, the head wheel
resolving every registered source and the base wheel none; collected ids
81 -> 83 (the two new CPU tests, nothing removed); CPU test subset with
CUDA hidden 26 passed / 57 skipped; benchmark --help ok (132 rows);
commit messages clean with the trailer on all 7
- **GPU tests.**
- Full pytest of
`tests/experimental/test_cake_kimi_k3_fp8_projection.py` on the head and
on the unchanged base, on one GPU, with a fresh JIT workspace per tree.
The static inventory expects head 83 passed / 0 skipped and base 81 / 0.
Every GPU test requires the registry and a supported device, so any skip
would be a regression.
- An all-programs load check: every `KERNELS` key of the GPU's
architecture is built and loaded into one process. That is 83 libraries
over 81 records on SM100, and 84 over 82 on SM103. Each library must
export exactly its own kernel symbol, its shim `Run` and the four FFI
entries.
- B200: head 83 passed, 0 skipped (7 min 1 s); unchanged base 81 passed,
0 skipped (6 min 58 s); all 83 sm_100a kernel keys built and loaded into
one process (81 distinct kernel symbols and 81 distinct shim namespaces
over the 81 records of the architecture; run, run_plan, run_launch and
run_chain resolvable on every module)
- GB300: head 83 passed, 0 skipped (8 min 40 s); unchanged base 81
passed, 0 skipped (8 min 18 s); all 84 sm_103a kernel keys built and
loaded into one process (82 distinct kernel symbols and 82 distinct shim
namespaces over the 82 records of the architecture; run, run_plan,
run_launch and run_chain resolvable on every module)

## Not in this PR

- **Step 1, templated TMA-encoder helper.** The per-binding
`EncodeTma_*` encoders (25,301 lines) and the per-plan `Run` / `Plan` /
`Launch` bodies are shared by body, not templated. The next step, if
wanted, is one binding per argument plan, as the sibling
attention-residual family did. That would take the 54 sources down to
about 5.
- **Step 1, cluster-size attribute set once per kernel.** The 5
cluster-14 launchers still call
`cudaFuncSetAttribute(...NonPortableClusterSizeAllowed)` on every
launch; this PR does not touch the launch path. The `--cupti`
launch-overhead comparison was not run. No launch path or attribute call
changes, so this PR claims no launch-overhead change.
- **Step 2, templates for twins that are not preprocessor-equivalent.**
The 14 cluster members that cannot be reproduced by define substitution
and `#if` arms stay as their own kernel sources.
- **Steps 3 and 4, exporter changes.**
- No exporter change lands. The registry rows, the table edit and the
shared sources are hand edits of exporter output, disclosed as such in
the registry header, the package README and `csrc/README.md`.
Regeneration by the exporter is a follow-up.
- The planner's slot-form parsing for `_sks` / `_skf4` / `_skf8` names
stays; only `required_kernel_keys` lost the branches.
- **Steps 7 and 8.**
- Step 7 (accept a row stride for `x`, strided `GPU_ROWS` case) is not
landed.
- Step 8 (benchmark-gated retirement of the single-cell twins `_dpf`,
`_pw2`, `_px1`, `_pf1` / `_pf2`, `_g64`, `_pdlb`, `_st`, `_cs2`,
`_skp4`, `_n384`) is not landed.
- This PR retires no program. Every removed source is a line-identical
fold with its own row in the SASS gate.
- **Packaging follow-ups.**
- The GPU check of an installed wheel (one `GPU_ROWS` case) was not run.
The wheel's content and its clean-environment install are part of the
CPU checks above.
- 14 of the 24 `flashinfer/experimental/*` packages with a `csrc/`
directory have no package-data entry. That is a separate change.
- **README counts.** The README sentence "(54 launcher sources for the
107 programs)" contains counts that will go stale on regeneration. It is
kept as written.

```experimental-tests
tests/experimental/test_cake_kimi_k3_fp8_projection.py
```

Part of #6653

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
  * Updated FP8 projection prefetch tuning across supported GPU routes.
* **Compatibility**
* Stream-K routing now uses prefetched or fix-up plans; ordered stream-K
plans and row-oriented cluster split-K requests are no longer supported.
* **Documentation**
* Expanded benchmark and generated-source documentation, including the
benchmark’s revised workload coverage.
* **Packaging**
  * Included generated projection sources in packaged distributions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d853ff3](https://github.com/flashinfer-ai/flashinfer/commit/d853ff30e10ae1787067ec5d61c3154f7e517d14)

- **作者**: eigen
- **时间**: 2026-10-19T17:26:18Z
- **提交信息**: perf(cake_deepgemm_mega_mhc): two-lane Sinkhorn normalization chain on the 40- and 27-split mHC programs (SM100a, SM103a) (#6202)

This PR speeds up the Cake fused manifold hyper-connection (mHC) kernel
(`flashinfer.experimental.deepgemm_mega_mhc`, public API
`flashinfer.mega_mhc.prepare_mega_mhc`). It is one persistent kernel
that fuses the mHC residual-stream mixing of DeepSeek V4.1 Flash at
hidden size 5120. That covers the FP8-normalized comb/post/pre mixing
GEMV work, a 4 x 4 Sinkhorn normalization (20 iterations) of the mixing
matrix, the residual update, and the BF16 / FP8 outputs with their scale
factors. The exported family has 4 routes: col and extra layouts, each
in plain and shifted form. The token range is split into 4 split-count
classes chosen at generation time: 40 splits for T <= 192, 27 for 193 <=
T <= 320, 20 for 321 <= T <= 448 and 16 for T >= 449. That gives one
compiled program per route and split class, and one source per program
serves both architectures. This PR delivers the 40- and 27-split
programs (T <= 320). In these programs the Mix role now runs the 4 x 4
Sinkhorn chain on two lanes, with in-register row sums and one xor-1
shuffle per iteration. Before, it ran on 16 lanes with shuffle-reduced
row and column sums. Each element goes through the same operations on
the same values in the same order, so outputs are bit-identical. Inputs,
outputs, quantization formats, scale layouts and the `prepare_mega_mhc`
signature are unchanged. The baseline is the previous Cake version of
this family on FlashInfer main. Most of the gain is at T = 200, the
27-split class, at 1.022-1.050x on both architectures. The GB300 T =
64/65 rows gain 1.005-1.026x. On B200 the T = 64/65 rows are mixed
(0.987-1.015x). The T = 1 rows show no consistent gain (0.966-1.024x),
and the lowest is GB300 extra plain at 0.966x. So the two-lane chain
mainly helps the 27-split programs.

Timings are CUPTI kernel-time medians of the whole call, not CUDA
events. Each row is one launch, with L2 flushed before every launch.
Each cell is the median of 12 readings per architecture. On B200 these
came from eight distinct GPUs over two allocations of the same node
class. On GB300 they came from four distinct GPUs of one node, each read
three times. All shapes use hidden size 5120 with the listed token count
T, and route = layout (col / extra) x form (plain / shifted). Speedup =
previous / this PR. Rows with T <= 320 run the changed program. Rows
with T >= 1025 run byte-identical programs on both sides, measured in
separate passes, so their ratios show measurement spread: 0.999-1.003x
on B200 and 1.003-1.013x on GB300.

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.3

| tokens (T) | route | program | previous, µs | this PR, µs | speedup |
|---:|---|---|---:|---:|---:|
| 1 | col plain | changed | 10.832 | 10.576 | 1.024 |
| 1 | col shifted | changed | 11.104 | 11.072 | 1.003 |
| 1 | extra plain | changed | 10.880 | 10.928 | 0.996 |
| 1 | extra shifted | changed | 11.168 | 11.024 | 1.013 |
| 64 | col plain | changed | 12.671 | 12.480 | 1.015 |
| 64 | col shifted | changed | 12.528 | 12.544 | 0.999 |
| 64 | extra plain | changed | 12.640 | 12.576 | 1.005 |
| 64 | extra shifted | changed | 12.592 | 12.400 | 1.015 |
| 65 | col plain | changed | 12.320 | 12.480 | 0.987 |
| 65 | col shifted | changed | 12.416 | 12.544 | 0.990 |
| 65 | extra plain | changed | 12.800 | 12.768 | 1.003 |
| 65 | extra shifted | changed | 12.448 | 12.560 | 0.991 |
| 200 | col plain | changed | 15.808 | 15.312 | 1.032 |
| 200 | col shifted | changed | 15.808 | 15.457 | 1.023 |
| 200 | extra plain | changed | 15.808 | 15.248 | 1.037 |
| 200 | extra shifted | changed | 15.888 | 15.184 | 1.046 |
| 1025 | col plain | unchanged | 32.144 | 32.111 | 1.001 |
| 1025 | col shifted | unchanged | 35.343 | 35.359 | 1.000 |
| 1025 | extra plain | unchanged | 32.192 | 32.224 | 0.999 |
| 1025 | extra shifted | unchanged | 35.392 | 35.312 | 1.002 |
| 4096 | col plain | unchanged | 108.047 | 108.208 | 0.999 |
| 4096 | col shifted | unchanged | 92.864 | 92.800 | 1.001 |
| 4096 | extra plain | unchanged | 110.399 | 110.256 | 1.001 |
| 4096 | extra shifted | unchanged | 93.712 | 93.456 | 1.003 |

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.3

| tokens (T) | route | program | previous, µs | this PR, µs | speedup |
|---:|---|---|---:|---:|---:|
| 1 | col plain | changed | 9.872 | 9.904 | 0.997 |
| 1 | col shifted | changed | 10.624 | 10.720 | 0.991 |
| 1 | extra plain | changed | 9.920 | 10.272 | 0.966 |
| 1 | extra shifted | changed | 10.640 | 10.688 | 0.996 |
| 64 | col plain | changed | 12.032 | 11.856 | 1.015 |
| 64 | col shifted | changed | 12.272 | 12.064 | 1.017 |
| 64 | extra plain | changed | 12.064 | 11.936 | 1.011 |
| 64 | extra shifted | changed | 12.272 | 12.032 | 1.020 |
| 65 | col plain | changed | 12.096 | 11.792 | 1.026 |
| 65 | col shifted | changed | 12.432 | 12.160 | 1.022 |
| 65 | extra plain | changed | 12.352 | 12.288 | 1.005 |
| 65 | extra shifted | changed | 12.352 | 12.064 | 1.024 |
| 200 | col plain | changed | 14.832 | 14.432 | 1.028 |
| 200 | col shifted | changed | 14.976 | 14.656 | 1.022 |
| 200 | extra plain | changed | 14.784 | 14.368 | 1.029 |
| 200 | extra shifted | changed | 15.088 | 14.368 | 1.050 |
| 1025 | col plain | unchanged | 30.896 | 30.640 | 1.008 |
| 1025 | col shifted | unchanged | 33.936 | 33.760 | 1.005 |
| 1025 | extra plain | unchanged | 31.200 | 30.800 | 1.013 |
| 1025 | extra shifted | unchanged | 33.872 | 33.728 | 1.004 |
| 4096 | col plain | unchanged | 102.704 | 102.024 | 1.007 |
| 4096 | col shifted | unchanged | 87.616 | 87.368 | 1.003 |
| 4096 | extra plain | unchanged | 104.528 | 103.728 | 1.008 |
| 4096 | extra shifted | unchanged | 88.432 | 88.096 | 1.004 |

The kernel's other Cake variants are the 20- and 16-split programs (T >=
321), which keep the previous Sinkhorn chain, and the family ships on
sm_100a (B200) and sm_103a (GB300).

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [ce0de7f](https://github.com/flashinfer-ai/flashinfer/commit/ce0de7f4c61264fca1e75ec3bf2c275c8fa1e74c)

- **作者**: eigen
- **时间**: 2026-10-19T17:25:04Z
- **提交信息**: feat(cake_comm): QkvNormRopeExchangeOverlap adds the SM107 (Rubin) producer programs (#6620)

## 📌 Description

Stacked on #6613 (merge that first); the diff against #6613's head is
this change.

This PR adds compute capability 10.7 (SM107, Rubin R200) as a target of
`flashinfer.comm.QkvNormRopeExchangeOverlap`. That is the fused QKV
projection + per-head QK RMSNorm + RoPE + Ulysses exchange session. The
generated files are rendered from the upstream generator at 196f4cf2.

What SM107 adds:

* **SM107 producer programs.** The SM107 tcgen05 producer programs have
wider SMEM-descriptor address masks. They are therefore delivered as
their own content-hashed programs. Three programs are new.
* **Shared programs.** If a stage's SM107 text is identical to an
existing program, that program only adds `sm_107a` to its architectures.
* **Tables.** The program and architecture tables have SM107 entries.
The plan and world-size tables have SM107 rows.
* **Unsupported devices.** A device whose capability has no program
table still raises the explicit error. It never runs another
architecture's program.

Defaults on SM107:

| Setting | SM107 default |
|---|---|
| World sizes | 2 and 4 (SM107 nodes carry four GPUs) |
| Folded rendezvous producer (`fold_barrier`) | on, as on the other
architectures |
| Producer build | shipped |
| `group_m_scale` | 1 |
| Shape gates | none |

* The benchmark's per-operator baseline communicators default to NCCL on
SM107, because the NVLink Ulysses kernels are unverified there. The
fused session itself runs its NVLink path.
* The opt-out switches keep their meaning on SM107.

Unchanged on SM90, SM100 and SM103:

* **Programs.** The compiled programs match those of #6613: 15 of 15
default programs, 4 of 4 fold programs and 36 of 36 variant builds.
* **Templates.** The five FlashInfer templates are identical.
* **Defaults.** The per-(architecture, world size) defaults of #6613 do
not change.
* **Numerics.** The programs do not change, so the outputs do not
change.
* **Validation protocol.** No change for these architectures.

Numerics on SM107: the BF16 Q/K/V outputs of this build are bitwise
identical to the generator's earlier SM107 builds. Per-element checks
against the fp32 reference are within the documented tolerance class
(see Tests).

### Files

Compared with the head of #6613 (9b8f2c93):

| Path | Change |
|---|---|
| `csrc/cake_qkv_norm_rope_exchange_overlap/` | Generated translation
units: 42 programs × {binding, kernel} = 84 `.cu` files (#6613: 39
programs, 78 files). The three new programs are the SM107 producer
programs `27a9e2ff563af5644d27`, `6cea4b1cead955382caa` and
`f86aebd1e176ce36e6d2`. |
| Table, plan and session modules (`flashinfer/jit/`,
`flashinfer/comm/`) | SM107 entries in the program and architecture
tables; SM107 rows in the plan and world-size tables; the SM107 defaults
|
| `tests/comm/test_qkv_norm_rope_exchange_overlap.py` | SM107 rows in
the default-table tests, for example the SM107 row of
`test_producer_variant_default_table` |
| Documentation | SM107 entries |

## 🔍 Related Issues

- Stacked on #6613 (merge that first); the diff against #6613's head is
this change.
- #6537 and #6516: earlier PRs in this series. #6613 stacks on #6537,
and #6516 was the first PR.
- #6304: the feature request behind `QkvNormRopeExchangeOverlap`.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

Pre-commit was run at this head (`290d89db`) on a CPU-only machine. The
run exited 0, the mypy check returned 0, and the working tree was clean
afterwards.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing. The CPU tests pass at this head (35 passed,
3 deselected). This PR does not record a run of the whole test file on a
GPU node at this head. CI is pending.

This head is rendered from the upstream generator at 196f4cf2. The SM107
GPU checks below ran at 196f4cf2 on one 4-GPU R200 node, using the
kernel generator's acceptance harness. They used the defaults (fold on)
at W = 2 and W = 4.

### Test plan

- [x] CPU tests at head 290d89db on a CPU-only machine: 35 passed, 3
deselected. These include `test_producer_variant_default_table` with its
SM107 row.
- [x] Pre-commit at head 290d89db on a CPU-only machine: exit 0, mypy
check 0, no post-hook diff.
- [x] Bitwise output identity on SM107 (4 × R200, W = 2 and W = 4):
- This build's per-rank BF16 Q/K/V output digests were compared with
three earlier SM107 runs of the generator: the previous acceptance run,
and an earlier build with the fold on and with it off. Each comparison:
1724 of 1724 identical, 0 different.
  - The reference digests were identical as well (0 different).
- The earlier builds had matched the revision that first admitted SM107:
200 groups at W = 2 and 320 groups at W = 4, with 0 differences.
- [x] Per-element checks against the fp32 reference are within the
documented tolerance class.
- [x] SM107 compile: all 15 SM107 cubins match the two earlier SM107
builds (15/15). They are stable across two compiles (15/15).
- [x] compute-sanitizer on 4 ranks with the defaults (fold on):
  - synccheck, full scope: passed with 0 errors.
- racecheck, full scope: passed with 0 hazards and 0 deadlock warnings.
- [x] Dual-communicator concurrency test: 14 passed at W = 4 and 14
passed at W = 2.
- [x] Host path: 2 launches per call with the folded rendezvous on all
24 perf rows at each world size. Overlap timelines were recorded with 3
samples per row on 4 rows.
- [x] Performance on SM107 (see Speedup).
- [ ] CI: pending.
- [ ] Whole test file on a 4-GPU SM107 node at this head: not recorded
here.

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

- Stacked on #6613 (merge that first); the diff against #6613's head is
this change. That change is one commit, 290d89db, on top of the #6613
head 9b8f2c93. Until #6613 and the PRs below it are merged, the diff
against upstream main 5e454aa7 also shows their changes.
- SM107 defaults: world sizes 2 and 4, the folded rendezvous producer
on, and the shipped producer build with `group_m_scale` 1 and no shape
gates.
- On SM107 the benchmark's baseline communicators default to NCCL,
because the NVLink Ulysses kernels are unverified there. The fused
session runs its NVLink path.
- W = 8 is not measured on SM107. The nodes carry four GPUs, so W = 8
would need two nodes. The SM107 world-size table lists 2 and 4.
- A device whose capability has no program table raises the explicit
error. It never falls back to another architecture's program.
- The kernel generator renders the generated files. This head's tree
equals the render at 196f4cf2. There are 84 generated `.cu` files (42
programs × binding + kernel).
- Environment: the SM107 acceptance and export runs used apache-tvm-ffi
0.1.13.dev57. The previous SM107 acceptance run used 0.1.12. Only the
host binding layer differs, and the SM107 cubins are identical.

## Speedup

### Rubin (R200, 4 GPUs/node)

The benchmark ran at 196f4cf2 with the defaults (fold on) on one 4-GPU
R200 node, using the kernel generator's acceptance harness:

* Protocol: 5 × 10 A/B/B/A over the NVLink exchange, with an in-session
A/A arm against the B1 baseline.
* Speedup: the fused arm's speedup over the fastest runnable baseline
arm.
* Void rows: a row is void when its A/A deviation exceeds 1 %. A void
row is reported but not counted.

Rows are given as hidden × S_global.

| W | rows measured | geomean | min (row) | max | rows below 1.00 | void
|
|---|---|---|---|---|---|---|
| 2 | 24 of 24 | 2.533 | 1.826 (8192 × 131072) | 3.246 | 0 | 0 |
| 4 | 21 of 24 | 2.378 | 1.915 (8192 × 65536) | 2.840 | 0 | 3 |

* **W = 4 void rows** (A/A deviation, point estimate): 3072 × 4096 (1.12
%, 2.499), 6144 × 4096 (1.55 %, 2.137) and 8192 × 4096 (1.18 %, 2.180).
* **Re-measure.** These three rows were re-measured right afterwards on
a second R200 node with the same scripts and environment:
  * 3072 × 4096: 2.547 (A/A 0.97 %).
  * 6144 × 4096: 2.190 (A/A 0.33 %).
  * 8192 × 4096: 2.109 (A/A 0.91 %).
* None is void, and all are above 1.00. Two of the three A/A deviations
(0.97 % and 0.91 %) are within 0.1 percentage point of the 1 % limit.
* Every W = 4 row therefore has a measured speedup above 1.00. The W = 4
geomean of 2.378 covers only the 21 rows from the first node. The three
re-measured rows come from another node and are reported separately.
* **Baseline arms.** On the six W = 4 rows with hidden 3072, the B3
head-chunk baseline has only one schedule (six local heads). These rows
therefore have 10 of 12 baseline arms. In the previous SM107 acceptance
run no baseline arm failed.
* **Previous SM107 acceptance run.** On other nodes it read 2.649 at W =
2 (24 rows) and 2.485 at W = 4 (23 rows, one void). Because the nodes
and sessions differ, this comparison is informational only.

### Export-protocol validation (per-row receipts)

SM107 is measured over the export protocol at W = 2 and W = 4 (48 perf
rows and 9 correctness rows). The runs used the defaults on three 4-GPU
R200 nodes. Validity gates are never relaxed.

* **Generator revision.** The receipts were produced at generator
revision d0c1b0a1, and this head is rendered from 196f4cf2. The two
revisions differ by one test row (the SM107 row of
`test_producer_variant_default_table`). They compile to identical SM107
cubins (15 of 15).
* **Exception row.** `perf_w2_h8192_s131072` did not pass. It failed the
baseline directional-disagreement gates of `b2_whole_qkv` and
`b3_head_chunk` on both ranks (raw speedup 1.706, not valid). The row is
disclosed and not counted. In #6613 the SM100 and SM103 rows of this
shape failed in the same class.
* **Retries on small-M shapes.** Some shapes with M ≤ 2048 needed a
retry:
* Cause: the timing harness's CUPTI attribution sometimes counted
kernels from a neighbouring CUDA-graph replay into the open measurement
window. That attempt then failed its activity-count check.
* A shape whose receipt passed has exact per-sample parity, so passing
receipts are unaffected.
  * One W = 2 row (6144 × 4096) passed on its fifth attempt.

Export-protocol receipts on SM107 (R200, 4 GPUs per node; world sizes 2
and 4; default settings; speedup = fastest baseline arm / fused session,
per-row protocol gates applied; a valid row passes every gate and is >
1.00):

| World size | perf rows | passed (all > 1.00) | geomean | min (hidden,
S) | max (hidden, S) | not passed |
|---|---|---|---|---|---|---|
| 4 | 24 | 24 | 1.954 | 1.640 (8192, 131072) | 2.281 (4096, 65536) | 0 |
| 2 | 24 | 23 | 2.147 | 1.526 (8192, 65536) | 2.807 (4096, 16384) | 1:
hidden 8192, S 131072 — the two-node baseline gates
`directional_disagreement` fired on both ranks (same exception class as
the SM100/SM103 rows of that shape in the previous round); disclosed,
not counted |

Overall: 47/48 perf rows passed, geomean 2.046, min 1.526; correctness
rows 9/9. Receipts were produced by the generator at d0c1b0a1, which
differs from the delivered 196f4cf2 only by one test row and compiles to
identical SM107 binaries (15/15).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added SM107 support for the Cake communication backend, with supported
group sizes of 2 or 4 ranks.
* Added options to configure barrier handling, producer variants, group
scaling, and row-count-based launch behavior. Session details now report
the resolved settings and plans.
* **Improvements**
* Benchmark results now include output checks and launch configuration
details, with backend defaults selected by GPU architecture.
* **Documentation**
* Expanded configuration guidance, supported-architecture details, and
alignment requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8bef84c](https://github.com/flashinfer-ai/flashinfer/commit/8bef84ca44f7746d5b6b04afe8e273777fb673ae)

- **作者**: Adrian
- **时间**: 2026-10-19T16:12:08Z
- **提交信息**: test: use parametrize_product for block_sparse_cutile (#6380)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adopt `parametrize_product` in
`tests/attention/test_block_sparse_cutile.py` using deterministic
pairwise regular cases and preserving the original parameter assignments
under `pytest --full`. Preserve coupled configurations, test bodies, and
other markers.

Collection for this file: **660 original/full cases → 69 regular
cases**.

## 🔍 Related Issues

Follows the regular/full parameterization approach in #5313 and #5413.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- Regular collection passed: 69 cases.
- Full collection passed: 660 cases; all six converted files together
retain the original 1,606 full cases.
- Parameter-matrix equivalence, pairwise coverage, unique IDs, Python
compilation, and diff checks passed.
- Pre-commit hooks passed for the changed files.
- A GPU test execution attempt stopped with `RuntimeError: No CUDA GPUs
are available`; GPU correctness must be validated in CI.

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

Converted functions:
- `test_block_sparse_cutile`

Full parameter assignments were checked against the original decorators,
including grouped axes. Regular subsets retain every axis value and
every pair of axis values. Test bodies and other decorators are
unchanged. Source-defined configuration/backend inventories remain
unchanged; metadata checks used symbolic representatives for those
inventories. GPU runtime was not benchmarked. The `(R, M)`, `(C, N)`,
and head-count pairs remain coupled to preserve exactly 660 valid full
cases. Rebased onto current main, preserving the upstream single-config
autotuning fixture from #6110 and the removal of the solo marker from
#6438. `_CUTILE_CASES` is removed; parameter groups are defined directly
in `@parametrize_product`. Post-rebase verification preserves exact
parameter metadata (values, ordering and IDs): 69 regular cases and 660
full cases. Both pytest collection modes and changed-file pre-commit
hooks pass.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Updated cuTile block-sparse test coverage to group related block-size,
sequence-length, head-count, and head-dimension combinations. The suite
retains its full set of 660 test cases; no user-facing behavior changes
are included.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f64b4ba](https://github.com/flashinfer-ai/flashinfer/commit/f64b4ba8762ded12a4f4b9a2092974c9a395e7ca)

- **作者**: eigen
- **时间**: 2026-10-19T10:50:33Z
- **提交信息**: perf(cake_all_gather_matmul): SM103a CTA-pair main kernel for two measured gate/up shapes (region table with column ranges) (#6566)

This is a regenerated export of the Cake all-gather matmul backend. It
changes which calls run the CTA-pair main kernel on SM103a. No existing
kernel program changes, and SM100a is unchanged.

This PR builds on #6501 (SM103a SM push route band and CTA-pair main
kernel), which is not merged yet. It targets `main` so that CI can run.
Until #6501 merges, the diff also contains #6501's commit (`c8917fee`);
only the last commit (`d8e69c67`) belongs to this PR: the region-table
change and the new world-size-8 pair twin. Please merge it after #6501.

The change has two parts:

1. **Region table with column ranges.** Each entry in the loader's
CTA-pair region table now has a minimum N as well as a maximum N. A
class can also list several rectangles. With these two changes, the
table can select single measured shapes.
2. **Two more shapes on the CTA-pair main kernel.** Two gate/up
projection shapes at M=512 per rank (TP4 and TP8; bf16, K-major, K=8192)
now run the CTA-pair twin. They run 5.2–6.9 % faster. The TP8 shape
needs the world-size-8 bf16 K-major twin, which this PR adds to the
delivered kernel set.

The speedups come from paired runs on two 8×B300 nodes. On both nodes,
every changed shape is faster by more than its noise bound, and its
outputs are bitwise identical. SM100a has no regions, so its programs
are unchanged.

## Narrowed scope and export-gate incident

The measurement covered four gate/up shapes: M=512 and M=2048 per rank,
for TP4 (N=14336) and TP8 (N=7168). All four met the adoption rule on
both nodes. This PR routes only the two M=512 shapes. The two M=2048
shapes keep the single-CTA kernel.

- **Why the M=2048 shapes are not included.** The export check compares
the generator source with this export (see *This export* below). It uses
a frozen timing protocol that rejects a run if any rank's loaded SM
clock falls below 0.60 of the 2032 MHz maximum during the timing
session. The M=2048 shapes take about 1.45 ms, are compute-bound, and
run power-throttled under that load (1100 W limit). On the export node,
two attempts saw 1 and 3 of 8 ranks at 1162 / 1177 / 1200 MHz
(0.572–0.591 of the maximum), and the timing raised
`InterleavedTimingError`. When idle, the GPUs return to 2032 MHz. In the
A/B runs, the same shapes ran at median clocks of 0.616–0.640 of the
reference clock, which is also close to the floor. So the export check
cannot be evaluated for these shapes. The 0.60 floor, the protocol and
the acceptance thresholds were not relaxed. The M=2048 results stay on
record for a later decision.
- **Export-engine hang (disclosed, not fixed here).** In the first
attempt, one rank raised inside the distributed timing. Its
`dist.destroy_process_group()` call never returned while the other ranks
waited in a collective. Because `mp.spawn(join=True)` has no join
timeout, the run produced no output for 80 min, until the job's progress
timeout killed it. The second attempt ran under a watchdog that kills a
run whose log has been silent for 480 s or more. The defect is in the
export engine that produces and checks this export. This change does not
fix it.
- **Superseded result.** In the first attempt, the TP8 M=512 export
check passed (export 0.3808 ms vs source 0.3801 ms). That attempt is
superseded. The export figures in this PR come from a fresh run on the
final tree.

## Routing and kernel changes

### Region table with column ranges

Before this PR, each entry of `CG2_REGIONS` in
`flashinfer/jit/cake_all_gather_matmul.py` had the form `[world_size,
dtype, b_layout, min_padded_rows, max_padded_rows, max_cols]`. A class
could have at most one region.

Each entry now has this form:

`[world_size, dtype, b_layout, min_padded_rows, max_padded_rows,
min_cols, max_cols]`

Table rules:

- a class `(world_size, dtype, b_layout)` may list several rectangles;
- the rectangles of one class must be pairwise disjoint. The generator
rejects overlapping rectangles and never merges them;
- row bounds are positive multiples of 128, with `min_padded_rows ≤
max_padded_rows`. Column bounds are positive, with `min_cols ≤
max_cols`.

A call with 256-column tiles runs the CTA-pair twin only if one
rectangle of its class, on the device architecture, satisfies both of
these conditions:

- `min_padded_rows ≤ padded rows ≤ max_padded_rows`;
- `min_cols ≤ N ≤ max_cols`.

Every other call keeps its current main kernel.

Loader details:

- `_cg2_region` returned one region or `None`. It is replaced by
`_cg2_regions`, which returns every rectangle of the class, or an empty
list if the class has none.
- `main_form` applies the any-rectangle rule.
- On SM103a, `CG2_CLASSES` gains `[8, "bfloat16", "k_major"]`. SM100a
still lists no class and gets no twin.

| architecture | world size | dtype | B layout | padded rows | N |
origin |
|---|---|---|---|---|---|---|
| SM103a | 2 | bf16 | N-major | 2048–5760 | 1–2048 | #6501, unchanged |
| SM103a | 4 | bf16 | K-major | 1024–1536 | 1–6058 | #6501, unchanged |
| SM103a | 4 | bf16 | K-major | 512 | 14336 | new: TP4 gate/up, M=512 |
| SM103a | 8 | bf16 | K-major | 512 | 7168 | new: TP8 gate/up, M=512 |
| SM100a | no regions | | | | | |

The two rectangles from #6501 keep their bounds. Their `min_cols` is 1,
so every call they routed before is still routed.

Each new rectangle is a single point: one padded row count and one N,
both taken from a measured inventory shape. Calls with a different
padded row count or a different N keep the single-CTA kernel. The rule
uses padded rows. So on world size 4 at N=14336, 511 rows (padded to
512) select the pair kernel, and 513 rows (padded to 640) do not.
N=14335 and N=14337 do not select it either. The table has no M=2048
points for these classes, so the M=2048 gate/up calls keep the
single-CTA kernel.

### Shapes whose launch changes

| shape | SM103a before | SM103a after | SM100a |
|---|---|---|---|
| TP4 gate/up projection, M=512 per rank, N=14336, K=8192, bf16, K-major
| single-CTA main | CTA-pair main (`_cg2`) | unchanged |
| TP8 gate/up projection, M=512 per rank, N=7168, K=8192, bf16, K-major
| single-CTA main | CTA-pair main (`_cg2`, new world-size-8 twin) |
unchanged |
| every other inventory shape | unchanged | unchanged | unchanged |

These shapes keep their programs:

- the TP4 and TP8 gate/up shapes at M=2048. They were measured but are
not routed; see *Narrowed scope* above;
- the TP4 QKV shapes at M=512 and M=2048 (N=2560);
- every other TP8 shape;
- every fp16 shape;
- every N-major shape outside the existing world-size-2 rectangle.

The CTA-pair kernel is the program from #6501. This PR changes only
which calls select it. Nothing is approximated, and accumulation
precision is unchanged.

## Kernel set and loader surface

- **Kernels.** This PR adds one kernel module in
`csrc/cake_all_gather_matmul`: the CTA-pair `_cg2` main of the
world-size-8 bf16 K-major class (SM103a). It is the same pair-twin
program, generated for that class. It was not delivered before because
no shape selected it. Kernel modules go from 23 to 24. SM100a gets no
new kernel.
- **Loader** (`flashinfer/jit/cake_all_gather_matmul.py`):
  - `CG2_REGIONS` entries gain `min_cols`;
  - `_cg2_region` is replaced by `_cg2_regions`;
  - `main_form` applies the any-rectangle rule;
  - on SM103a, `CG2_CLASSES` gains the world-size-8 bf16 K-major class.
- **Tests** (`tests/comm/test_all_gather_matmul_cake.py`):
  - updated pins for both tables;
  - the two shapes are expected on the pair kernel;
  - edge cases around each new point (row and N neighbours);
  - cases for the world-size-8 class.
- **Public API.** The `all_gather_matmul` / `prepare_all_gather_matmul`
entry points are unchanged.
- **File signature vs #6501's branch:** 1 added / 4 modified / 0
deleted, 0 stray (assembly step `d2439d19abd71e6e53c93ea3` from the
rerun export, delivered set 64 = 24 kernels + 24 sequences + 10 helpers
+ 4 python, `FIPR_DERIVED ok` with the dispatcher byte-identical,
applied-sha256 digest 6bd6d696288b6018): added
`csrc/cake_all_gather_matmul/cake_all_gather_matmul_17f60837feb11a634b34_kernel.cu`
(the ws8 bf16 k_major `_cg2` twin); modified
`csrc/cake_all_gather_matmul/cake_all_gather_matmul_device_common.cuh`,
`csrc/cake_all_gather_matmul/cake_all_gather_matmul_sequence_bfloat16_ws8_k_major_sm_103a.cu`,
`flashinfer/jit/cake_all_gather_matmul.py` (`CG2_REGIONS` table) and
`tests/comm/test_all_gather_matmul_cake.py`; the three shared device
helper headers that differ only in their copyright line are kept at the
base's version.

## Validation

The A/B and exactness runs used two 8×B300 (SM103a) nodes, with the
generator code behind #6501. A row override forced the CTA-pair kernel
on four shapes, in two configurations:

- the two M=512 shapes together. These are the shapes this PR changes;
- the two M=2048 shapes together. This PR does not route them.

Each configuration was paired against an independent reference build.
That build runs these shapes on the single-CTA kernel. Through the
region table, this PR selects the same kernel for the two M=512 shapes.
A change is adopted only if every shape it changes is significantly
faster on both nodes.

Timing protocol (the same as for #6501):

- CUPTI timing with a cold L2;
- nine counterbalanced ABBA groups and two passes, which gives 18 group
ratios per shape;
- a same-code control arm.

### CTA-pair main kernel on the gate/up shapes

- **Exactness.** On every rank, outputs are bitwise identical to the
reference (int16-view SHA-256 per rank). The exactness run covered 102
rows in 18 launches: the two configurations plus the unchanged code, at
world sizes 2, 4 and 8. It had 0 failures, and the route of all 102 rows
was checked. This run was on node 1.
- **Determinism.** Two independent launches produced identical outputs
for every configuration and world size (node 1).
- **compute-sanitizer.** synccheck: 0 errors. racecheck: 6 rows in each
of the two configurations, with 0 errors and 0 hazards.
- **End-to-end.** The 2-GPU end-to-end test passes.
- **Paired A/B on the two changed shapes.** A value above 1 means the
CTA-pair kernel is faster. The µs columns give each arm's median over
all samples. The speedup is the median of the 18 per-group
reference/CTA-pair ratios, so the columns need not multiply out exactly.
Both shapes are significantly faster on both nodes.

| shape | node 1 reference µs | node 1 CTA-pair µs | node 1 speedup |
node 2 speedup |
  |---|---:|---:|---:|---:|
| TP4 gate/up, M=512 per rank, N=14336 | 416.4 | 390.6 | 1.0649 | 1.0687
|
| TP8 gate/up, M=512 per rank, N=7168 | 423.0 | 402.8 | 1.0529 | 1.0515
|

Node 2 medians and the per-shape noise bounds (delta_res, node 1 / node
2):

| shape | node 2 reference µs | node 2 CTA-pair µs | delta_res node 1 /
node 2 |
  |---|---:|---:|---|
| TP4 gate/up, M=512 per rank, N=14336 | 415.8 | 389.0 | 0.0341 / 0.0478
|
| TP8 gate/up, M=512 per rank, N=7168 | 422.4 | 399.8 | 0.0404 / 0.0322
|

The margin is |ln speedup| / delta_res. It is 1.28–1.85 for the two
changed shapes.

The same runs measured the M=2048 configuration. It was also
significantly faster on both nodes. Speedups were 1.0251 / 1.0303 for
TP4 (N=14336) and 1.0432 / 1.0427 for TP8 (N=7168), on node 1 / node 2,
with margins of 3.6–12.7. This PR does not route those shapes; see
*Narrowed scope* above.

Timeline attribution points the same way on both nodes. The main kernel
span is shorter on every measured shape. The reference/CTA-pair span
ratio is 1.057–1.080 on the two changed shapes and 1.033–1.045 on the
M=2048 shapes. These shapes use the copy-engine push, so no push kernel
is involved.

Same-code control arm: the same code without the override, so all four
measured shapes run the single-CTA kernel. Ratios are 0.9955–1.0070 over
the four shapes and two nodes. One value falls outside its noise bound
and is disclosed here: TP8 M=2048 on node 1 reads 0.9955 (|ln| 0.0045 vs
bound 0.0039). The A/A read-out passes.

Two launches were repeated on the same hosts because their control
groups were voided. After the repeats, no group in the data is voided.

SM clocks were 0.79–0.83 of the reference clock on the two changed
shapes. The M=2048 shapes take over 1 ms and run power-throttled. In
these runs, their median clocks were 0.616–0.640, above 0.60, the level
below which a run is voided. During the export check, some ranks fell
below that level; see *Narrowed scope* above.

- **No-regression check.** Every changed shape is ≥ exp(−delta_res) on
both nodes. The check also covers all 45 perf rows, with
identical-program rows exempted. It passes for the M=2048 configuration
on both nodes and for the M=512 configuration on node 1.

On node 2, the M=512 configuration has one strict miss: world size 4,
M=512, N=2560, fp16, K-major, at 0.9354 (bound 0.0444). This PR does not
change that shape's program. The shape runs the wide SM push kernel
(`peer_push_wide`) in every configuration, including the control. The
reference build does not contain that kernel, so the kernel-name
exemption does not apply. The same shape reads 1.0314 and 1.0199 in the
M=2048 configuration, and 1.0490 on node 1 in the M=512 configuration.

### This export

- **SM100a (B200).** For SM100a, the region table is empty and
`CG2_CLASSES` lists nothing. Every call launches the same programs as
before. All measurements in this PR are from SM103a.
- **Generator identity check.** This check confirms two things: the
kernel programs are identical to the measured code, and the launch
changes on exactly the two shapes. Result: pass — generator render of
the 23 kernel programs per architecture plus the 12 `_cg2` twins and
`peer_push_wide` is byte-identical to the measured tree (`c1384r2e`),
and the resolve table differs on exactly the two M=512 gate/up shapes of
SM103a (which gain stages `main_cg2`, cluster dims [2,1,1]); SM100a
resolves identically.
- **Generator source vs this export.** Route-scoped export of the two
changed shapes, with a floor of 0.95 per shape, from a fresh run on the
final tree: pass 2/2 (export rerun step `f0614b027f5290ce9c273988`,
pool0-0242, 2026-10-15T21:13Z, tree `c1384r3c`): ws8
`llama_tp8_gate_up_bf16_m512_kmajor` source/export = 0.9988 (0.3799 →
0.3803 ms; loaded SM clock 0.985 / 0.997 / 0.974 of max over the 3
groups), ws4 `llama_tp4_gate_up_bf16_m512_kmajor` 0.9909 (0.3751 →
0.3785 ms; clocks 0.974 / 0.812 / 0.989); both correctness-passed on the
`_cg2` route, exporter stability gates passed, delivery check ok. The
first export step `5a829dda498de602be8a9acc` (pool0-0356, tree
`c1384r3b`, byte-identical kernels) read 1.0041 and 1.0006 (ws8 clocks
0.985–0.993, ws4 0.808–0.956); the informational source_over_export ≥
1.0 note is therefore host/run dependent at the ±1 % level while the ≥
0.95 gate holds on both runs.
- **FlashInfer tests.** Against the exported tree: 307 passed / 0 failed
/ 0 errors (CPU suite) and 3/3 e2e passed at world sizes 8, 4 and 2
(export rerun step `f0614b027f5290ce9c273988`, pool0-0242,
2026-10-15T21:13Z, tree `c1384r3c`; the first export step
`5a829dda498de602be8a9acc` on `c1384r3b` / pool0-0356 gave the same 307
/ 3-3-3 read-out). On the PR head
(`d8e69c67bc81ca3d3a451f5e38c5155430b01245`): CPU suite 307 passed / 0
failed / 0 errors; e2e 3/3 passed with 8 visible GPUs and 3/3 with 4
visible GPUs (step `e6adb517dbf3c0ca1de96a92`, pool0-0242, B300,
2026-10-15T21:33Z, `FIPR_TESTS_DONE rc=0`). The superseded first head
4964b066 (same code, test-file comments with tracker ids) had the
identical read-out in step `08ef57e8a48d6f7f310781ba`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added an optional paired-CTA main-kernel path for supported workloads,
with automatic selection based on hardware, data type, and workload
shape.
* Expanded SM-push routing to support architecture-specific workload
ranges, including an additional route for certain eight-rank
configurations.
* Updated launch configuration to support paired kernels in both
copy-engine and SM-push execution paths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [816db66](https://github.com/flashinfer-ai/flashinfer/commit/816db6625da0e3bc9de9f91c023131a553a35c11)

- **作者**: eigen
- **时间**: 2026-10-19T10:50:16Z
- **提交信息**: perf(cake_ssd_combined): SM107 varlen exact-scan geometry through the aux stage and full-grid tail-pair routing (#6775)

The Cake backend of FlashInfer's Mamba2 SSD combined chunk-scan prefill,
`SSDCombined(backend="cake")`, ships three state data types (bf16, f16,
f32) x two sequence layouts (batched, varlen) x these program forms:
exact-scan (fused one-launch, preprocess+main two-launch, metadata+main
two-launch, in-kernel-table one-launch, tail-wave pair, plus the no-ring
exact-scan forms a route can select), look-back chunk-parallel and
three-phase chunk-parallel. Since #6739 removed unreachable programs,
the loader has 56 program entries, and the 45 entries on `sm_107a` are
backed by 40 generated device sources. This PR re-exports the 13
`sm_107a` varlen exact-scan device sources (fused, two-launch ring and
no-ring, one-launch; bf16/f16/f32). In the new sources, the X/dt loader
passes each chunk's segment bounds through the input stage, so the three
consumer roles read those bounds instead of loading the chunk table
again. On capability (10, 7), the loader also sends full-grid two-launch
calls to the tail-wave pair program when the saved wave beats the pair
render's measured penalty (chunk floor: batched 16, varlen 8). It also
raises the chunk-parallel workspace cap to 512 MiB (256 MiB elsewhere),
so 1 x 1024-chunk and 4 x 256-chunk 8-head calls take the chunk-parallel
family, which is 2-7x faster than the exact scan on those shapes. The
baseline is the previous Cake version of this kernel on the same GPU:
FlashInfer main after #6746, which shipped the previous `sm_107a`
programs. Across the 73 performance shapes in the table below (perf_*
and nem_* rows), this PR has a geomean speedup of 1.0105x (1.0082x over
all 93 measured rows), with the largest gains on long varlen calls
(perf_varlen_32x32 1.101x, 0.1709 -> 0.1553 ms; perf_varlen_128x32
1.100x, 0.4746 -> 0.4315 ms), while six varlen rows of 128-1024 tokens
are slower at 0.954x-0.988x (worst nem_v4x128_float32, 0.0218 -> 0.0228
ms; perf_varlen_1x1 0.974x, 0.0072 -> 0.0074 ms) and every other row is
at or above 0.994x.

Measured on NVIDIA Rubin R200 (sm_107a, 212 SMs), CUDA 13.5 image /
NVRTC 13.4; CUPTI kernel time, cold L2, median of 3 rounds; both sides
in the same process on the same GPU.

| shape | mode | seqlen x batch (varlen: tokens / sequences) | heads |
state dtype | previous Cake ms | Cake (this PR) ms | speedup |
|---|---|---|---|---|---|---|---|
| nem_b1x1000_bfloat16 | batched | 1000 x 1 | 128 | bfloat16 | 0.0267 |
0.0267 | 1.001x |
| nem_b1x1000_float32 | batched | 1000 x 1 | 128 | float32 | 0.0264 |
0.0264 | 0.999x |
| nem_b1x1024_bfloat16 | batched | 1024 x 1 | 128 | bfloat16 | 0.0269 |
0.0268 | 1.002x |
| nem_b1x1024_float32 | batched | 1024 x 1 | 128 | float32 | 0.0268 |
0.0268 | 1.000x |
| nem_b1x2048_bfloat16 | batched | 2048 x 1 | 128 | bfloat16 | 0.0473 |
0.0473 | 1.000x |
| nem_b1x2048_float32 | batched | 2048 x 1 | 128 | float32 | 0.0476 |
0.0476 | 1.000x |
| nem_v1000_bfloat16 | varlen | 1000 tok / 1 seq | 128 | bfloat16 |
0.0323 | 0.0318 | 1.014x |
| nem_v1000_float32 | varlen | 1000 tok / 1 seq | 128 | float32 | 0.0324
| 0.0328 | 0.988x |
| nem_v1024_bfloat16 | varlen | 1024 tok / 1 seq | 128 | bfloat16 |
0.0324 | 0.0318 | 1.017x |
| nem_v1024_float32 | varlen | 1024 tok / 1 seq | 128 | float32 | 0.0326
| 0.0332 | 0.981x |
| nem_v1024p100_bfloat16 | varlen | 1124 tok / 2 seq | 128 | bfloat16 |
0.0385 | 0.0370 | 1.041x |
| nem_v1024p100_float32 | varlen | 1124 tok / 2 seq | 128 | float32 |
0.0384 | 0.0378 | 1.017x |
| nem_v1024x2_bfloat16 | varlen | 2048 tok / 2 seq | 128 | bfloat16 |
0.0589 | 0.0549 | 1.073x |
| nem_v1024x2_float32 | varlen | 2048 tok / 2 seq | 128 | float32 |
0.0587 | 0.0543 | 1.081x |
| nem_v128p896_bfloat16 | varlen | 1024 tok / 2 seq | 128 | bfloat16 |
0.0357 | 0.0340 | 1.052x |
| nem_v128p896_float32 | varlen | 1024 tok / 2 seq | 128 | float32 |
0.0367 | 0.0365 | 1.007x |
| nem_v160x128_bfloat16 | varlen | 20480 tok / 160 seq | 128 | bfloat16
| 0.5058 | 0.5058 | 1.000x |
| nem_v160x128_float32 | varlen | 20480 tok / 160 seq | 128 | float32 |
0.5075 | 0.5076 | 1.000x |
| nem_v16x128_bfloat16 | varlen | 2048 tok / 16 seq | 128 | bfloat16 |
0.0567 | 0.0567 | 0.999x |
| nem_v16x128_float32 | varlen | 2048 tok / 16 seq | 128 | float32 |
0.0554 | 0.0551 | 1.006x |
| nem_v1x128_bfloat16 | varlen | 128 tok / 1 seq | 128 | bfloat16 |
0.0103 | 0.0102 | 1.012x |
| nem_v1x128_float32 | varlen | 128 tok / 1 seq | 128 | float32 | 0.0105
| 0.0104 | 1.009x |
| nem_v2048_bfloat16 | varlen | 2048 tok / 1 seq | 128 | bfloat16 |
0.0545 | 0.0534 | 1.020x |
| nem_v2048_float32 | varlen | 2048 tok / 1 seq | 128 | float32 | 0.0548
| 0.0538 | 1.018x |
| nem_v4x128_bfloat16 | varlen | 512 tok / 4 seq | 128 | bfloat16 |
0.0214 | 0.0213 | 1.002x |
| nem_v4x128_float32 | varlen | 512 tok / 4 seq | 128 | float32 | 0.0218
| 0.0228 | 0.954x |
| nem_v64_64_bfloat16 | varlen | 128 tok / 2 seq | 128 | bfloat16 |
0.0209 | 0.0209 | 0.998x |
| nem_v64_64_float32 | varlen | 128 tok / 2 seq | 128 | float32 | 0.0219
| 0.0220 | 0.994x |
| nem_v64x128_bfloat16 | varlen | 8192 tok / 64 seq | 128 | bfloat16 |
0.2052 | 0.2051 | 1.000x |
| nem_v64x128_float32 | varlen | 8192 tok / 64 seq | 128 | float32 |
0.2048 | 0.2047 | 1.001x |
| nem_v8x64_bfloat16 | varlen | 512 tok / 8 seq | 128 | bfloat16 |
0.0465 | 0.0466 | 0.999x |
| nem_v8x64_float32 | varlen | 512 tok / 8 seq | 128 | float32 | 0.0468
| 0.0471 | 0.994x |
| nem_v96p160_bfloat16 | varlen | 256 tok / 2 seq | 128 | bfloat16 |
0.0240 | 0.0238 | 1.009x |
| nem_v96p160_float32 | varlen | 256 tok / 2 seq | 128 | float32 |
0.0252 | 0.0250 | 1.008x |
| perf_batched_128x1 | batched | 128 x 128 | 8 | bfloat16 | 0.0233 |
0.0232 | 1.003x |
| perf_batched_128x16 | batched | 2048 x 128 | 8 | bfloat16 | 0.1719 |
0.1719 | 1.000x |
| perf_batched_128x4 | batched | 512 x 128 | 8 | bfloat16 | 0.0548 |
0.0548 | 1.000x |
| perf_batched_16x1 | batched | 128 x 16 | 8 | bfloat16 | 0.0075 |
0.0075 | 1.000x |
| perf_batched_16x16 | batched | 2048 x 16 | 8 | bfloat16 | 0.0394 |
0.0394 | 1.000x |
| perf_batched_16x4 | batched | 512 x 16 | 8 | bfloat16 | 0.0137 |
0.0137 | 1.000x |
| perf_batched_1x1 | batched | 128 x 1 | 8 | bfloat16 | 0.0062 | 0.0061
| 1.005x |
| perf_batched_1x16 | batched | 2048 x 1 | 8 | bfloat16 | 0.0210 |
0.0210 | 1.000x |
| perf_batched_1x256 | batched | 32768 x 1 | 8 | bfloat16 | 0.0839 |
0.0838 | 1.000x |
| perf_batched_1x4 | batched | 512 x 1 | 8 | bfloat16 | 0.0109 | 0.0109
| 1.000x |
| perf_batched_1x64 | batched | 8192 x 1 | 8 | bfloat16 | 0.0346 |
0.0346 | 1.000x |
| perf_batched_256x1 | batched | 128 x 256 | 8 | bfloat16 | 0.0418 |
0.0418 | 1.000x |
| perf_batched_256x16 | batched | 2048 x 256 | 8 | bfloat16 | 0.3305 |
0.3306 | 1.000x |
| perf_batched_256x4 | batched | 512 x 256 | 8 | bfloat16 | 0.0995 |
0.0995 | 1.000x |
| perf_batched_4x1 | batched | 128 x 4 | 8 | bfloat16 | 0.0063 | 0.0063
| 1.000x |
| perf_batched_4x16 | batched | 2048 x 4 | 8 | bfloat16 | 0.0328 |
0.0328 | 1.000x |
| perf_batched_4x4 | batched | 512 x 4 | 8 | bfloat16 | 0.0112 | 0.0112
| 1.000x |
| perf_batched_4x64 | batched | 8192 x 4 | 8 | bfloat16 | 0.0742 |
0.0742 | 1.000x |
| perf_batched_512x2 | batched | 256 x 512 | 8 | bfloat16 | 0.1106 |
0.1106 | 1.000x |
| perf_batched_64x1 | batched | 128 x 64 | 8 | bfloat16 | 0.0141 |
0.0140 | 1.005x |
| perf_batched_64x16 | batched | 2048 x 64 | 8 | bfloat16 | 0.1052 |
0.0989 | 1.063x |
| perf_batched_64x4 | batched | 512 x 64 | 8 | bfloat16 | 0.0373 |
0.0373 | 1.000x |
| perf_nemotron_h_8b_c128_projection_batched_b1x1 | batched | 128 x 1 |
128 | bfloat16 | 0.0083 | 0.0083 | 1.000x |
| perf_nemotron_h_8b_c128_projection_varlen_4x1 | varlen | 512 tok / 4
seq | 128 | bfloat16 | 0.0212 | 0.0212 | 1.002x |
| perf_varlen_128x1 | varlen | 16384 tok / 128 seq | 8 | bfloat16 |
0.0321 | 0.0321 | 1.000x |
| perf_varlen_128x32 | varlen | 524288 tok / 128 seq | 8 | bfloat16 |
0.4746 | 0.4315 | 1.100x |
| perf_varlen_16x8 | varlen | 16384 tok / 16 seq | 8 | bfloat16 | 0.0282
| 0.0278 | 1.016x |
| perf_varlen_1x1 | varlen | 128 tok / 1 seq | 8 | bfloat16 | 0.0072 |
0.0074 | 0.974x |
| perf_varlen_256x1 | varlen | 32768 tok / 256 seq | 8 | bfloat16 |
0.0573 | 0.0573 | 1.000x |
| perf_varlen_32x1 | varlen | 4096 tok / 32 seq | 8 | bfloat16 | 0.0137
| 0.0134 | 1.019x |
| perf_varlen_32x32 | varlen | 131072 tok / 32 seq | 8 | bfloat16 |
0.1709 | 0.1553 | 1.101x |
| perf_varlen_32x8 | varlen | 32768 tok / 32 seq | 8 | bfloat16 | 0.0526
| 0.0507 | 1.037x |
| perf_varlen_4x1 | varlen | 512 tok / 4 seq | 8 | bfloat16 | 0.0076 |
0.0077 | 0.983x |
| perf_varlen_4x8 | varlen | 4096 tok / 4 seq | 8 | bfloat16 | 0.0229 |
0.0221 | 1.036x |
| perf_varlen_64x1 | varlen | 8192 tok / 64 seq | 8 | bfloat16 | 0.0215
| 0.0215 | 1.000x |
| perf_varlen_64x32 | varlen | 262144 tok / 64 seq | 8 | bfloat16 |
0.2661 | 0.2469 | 1.078x |
| perf_varlen_64x8 | varlen | 65536 tok / 64 seq | 8 | bfloat16 | 0.0778
| 0.0740 | 1.051x |
| perf_varlen_8x1 | varlen | 1024 tok / 8 seq | 8 | bfloat16 | 0.0078 |
0.0080 | 0.984x |
| perf_varlen_8x8 | varlen | 8192 tok / 8 seq | 8 | bfloat16 | 0.0241 |
0.0232 | 1.036x |

The same Cake family (all three state dtypes, both layouts and all
program forms) also ships on Blackwell `sm_100a` (B200) and `sm_103a`
(GB300); this PR changes only the `sm_107a` programs and the (10, 7)
routing and leaves the `sm_100a`/`sm_103a` programs byte-identical.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated workload selection for supported GPUs, allowing more batched
and variable-length workloads to use full-grid processing when its
estimated runtime is favorable.
* Increased the available workspace limit for supported GPUs, enabling
automatic selection to account for larger workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e623eac](https://github.com/flashinfer-ai/flashinfer/commit/e623eac470363f7bf529c44e857731f49c011af7)

- **作者**: eigen
- **时间**: 2026-10-19T10:13:08Z
- **提交信息**: perf(cake_quant_lora_gemm): W-resident strip raster for the SM90 FP8 LoRA GEMM hint program (#6769)

`cake_quant_lora_gemm` fuses a quantized GEMM (FP8 E4M3 or NVFP4) with a
runtime BF16 low-rank LoRA term and BF16 output. The family ships 11
program variants: 6 FP8 and 5 NVFP4. This PR updates one SM90 FP8
variant, `fp8_sm90_hint` (form `acc2_hint`), with a weight-resident
strip raster. The persistent tile walk now visits strips of 5 weight
n-tiles across all activation m-tile pairs (n-tile fastest, serpentine
between strips). A strip's weight tiles stay in L2 while the activation
streams once per strip, and the TMA L2 cache policies follow that order
(weights evict_last, activations evict_first). Only the tile order
changes, and the output is bit-identical to the previous version. The
baseline is the previous Cake version of the same program, already
shipped in FlashInfer. The gain is small and limited to one row. The one
shape that dispatches to `fp8_sm90_hint` (131072 x 8192 x 32768, rank
64) reads 56.54 vs 57.06 ms back to back (new / previous 0.9937;
per-round range 0.9785 to 1.0214) and 50.23 vs 51.00 ms cooled (0.9848;
per-round range 0.9743 to 1.0000). The other 59 of 60 shapes dispatch to
the unchanged `fp8_sm90` program (form `acc2`) and are listed with the
same measurement on both sides (1.0000).

| Program | Shape (M x N x K, rank) | Back to back: previous (ms) | new
(ms) | new / previous | Cooled: previous (ms) | new (ms) | new /
previous |
|---|---|---:|---:|---:|---:|---:|---:|
| `fp8_sm90` | 4096 x 9216 x 3072, 64 | 0.191 | 0.191 | 1.0000 | 0.182 |
0.182 | 1.0000 |
| `fp8_sm90` | 32768 x 9216 x 3072, 64 | 1.600 | 1.600 | 1.0000 | 1.382
| 1.382 | 1.0000 |
| `fp8_sm90` | 131072 x 9216 x 3072, 64 | 6.540 | 6.540 | 1.0000 | 5.617
| 5.617 | 1.0000 |
| `fp8_sm90` | 4096 x 3072 x 3072, 64 | 0.062 | 0.062 | 1.0000 | 0.062 |
0.062 | 1.0000 |
| `fp8_sm90` | 32768 x 3072 x 3072, 64 | 0.531 | 0.531 | 1.0000 | 0.468
| 0.468 | 1.0000 |
| `fp8_sm90` | 131072 x 3072 x 3072, 64 | 2.146 | 2.146 | 1.0000 | 1.846
| 1.846 | 1.0000 |
| `fp8_sm90` | 4096 x 12288 x 3072, 64 | 0.260 | 0.260 | 1.0000 | 0.239
| 0.239 | 1.0000 |
| `fp8_sm90` | 32768 x 12288 x 3072, 64 | 2.144 | 2.144 | 1.0000 | 1.845
| 1.845 | 1.0000 |
| `fp8_sm90` | 131072 x 12288 x 3072, 64 | 8.769 | 8.769 | 1.0000 |
7.564 | 7.564 | 1.0000 |
| `fp8_sm90` | 4096 x 3072 x 12288, 64 | 0.234 | 0.234 | 1.0000 | 0.213
| 0.213 | 1.0000 |
| `fp8_sm90` | 32768 x 3072 x 12288, 64 | 1.989 | 1.989 | 1.0000 | 1.704
| 1.704 | 1.0000 |
| `fp8_sm90` | 131072 x 3072 x 12288, 64 | 7.923 | 7.923 | 1.0000 |
7.093 | 7.093 | 1.0000 |
| `fp8_sm90` | 4096 x 12288 x 4096, 64 | 0.341 | 0.341 | 1.0000 | 0.304
| 0.304 | 1.0000 |
| `fp8_sm90` | 32768 x 12288 x 4096, 64 | 2.746 | 2.746 | 1.0000 | 2.387
| 2.387 | 1.0000 |
| `fp8_sm90` | 131072 x 12288 x 4096, 64 | 11.19 | 11.19 | 1.0000 |
9.957 | 9.957 | 1.0000 |
| `fp8_sm90` | 4096 x 4096 x 4096, 64 | 0.120 | 0.120 | 1.0000 | 0.119 |
0.119 | 1.0000 |
| `fp8_sm90` | 32768 x 4096 x 4096, 64 | 0.936 | 0.936 | 1.0000 | 0.817
| 0.817 | 1.0000 |
| `fp8_sm90` | 131072 x 4096 x 4096, 64 | 3.820 | 3.820 | 1.0000 | 3.265
| 3.265 | 1.0000 |
| `fp8_sm90` | 4096 x 16384 x 4096, 64 | 0.448 | 0.448 | 1.0000 | 0.396
| 0.396 | 1.0000 |
| `fp8_sm90` | 32768 x 16384 x 4096, 64 | 3.733 | 3.733 | 1.0000 | 3.205
| 3.205 | 1.0000 |
| `fp8_sm90` | 131072 x 16384 x 4096, 64 | 15.32 | 15.32 | 1.0000 |
13.45 | 13.45 | 1.0000 |
| `fp8_sm90` | 4096 x 4096 x 16384, 64 | 0.457 | 0.457 | 1.0000 | 0.407
| 0.407 | 1.0000 |
| `fp8_sm90` | 32768 x 4096 x 16384, 64 | 3.514 | 3.514 | 1.0000 | 3.095
| 3.095 | 1.0000 |
| `fp8_sm90` | 131072 x 4096 x 16384, 64 | 14.44 | 14.44 | 1.0000 |
13.64 | 13.64 | 1.0000 |
| `fp8_sm90` | 4096 x 18432 x 6144, 64 | 0.764 | 0.764 | 1.0000 | 0.658
| 0.658 | 1.0000 |
| `fp8_sm90` | 32768 x 18432 x 6144, 64 | 6.017 | 6.017 | 1.0000 | 5.315
| 5.315 | 1.0000 |
| `fp8_sm90` | 131072 x 18432 x 6144, 64 | 24.86 | 24.86 | 1.0000 |
22.15 | 22.15 | 1.0000 |
| `fp8_sm90` | 4096 x 6144 x 6144, 64 | 0.246 | 0.246 | 1.0000 | 0.223 |
0.223 | 1.0000 |
| `fp8_sm90` | 32768 x 6144 x 6144, 64 | 2.025 | 2.025 | 1.0000 | 1.738
| 1.738 | 1.0000 |
| `fp8_sm90` | 131072 x 6144 x 6144, 64 | 8.061 | 8.061 | 1.0000 | 7.224
| 7.224 | 1.0000 |
| `fp8_sm90` | 4096 x 24576 x 6144, 64 | 1.004 | 1.004 | 1.0000 | 0.872
| 0.872 | 1.0000 |
| `fp8_sm90` | 32768 x 24576 x 6144, 64 | 7.986 | 7.986 | 1.0000 | 7.102
| 7.102 | 1.0000 |
| `fp8_sm90` | 131072 x 24576 x 6144, 64 | 33.26 | 33.26 | 1.0000 |
29.44 | 29.44 | 1.0000 |
| `fp8_sm90` | 4096 x 6144 x 24576, 64 | 0.946 | 0.946 | 1.0000 | 0.819
| 0.819 | 1.0000 |
| `fp8_sm90` | 32768 x 6144 x 24576, 64 | 7.824 | 7.824 | 1.0000 | 7.132
| 7.132 | 1.0000 |
| `fp8_sm90` | 131072 x 6144 x 24576, 64 | 32.87 | 32.87 | 1.0000 |
29.72 | 29.72 | 1.0000 |
| `fp8_sm90` | 4096 x 24576 x 8192, 64 | 1.325 | 1.325 | 1.0000 | 1.147
| 1.147 | 1.0000 |
| `fp8_sm90` | 32768 x 24576 x 8192, 64 | 10.67 | 10.67 | 1.0000 | 9.417
| 9.417 | 1.0000 |
| `fp8_sm90` | 131072 x 24576 x 8192, 64 | 43.14 | 43.14 | 1.0000 |
39.06 | 39.06 | 1.0000 |
| `fp8_sm90` | 4096 x 8192 x 8192, 64 | 0.449 | 0.449 | 1.0000 | 0.393 |
0.393 | 1.0000 |
| `fp8_sm90` | 32768 x 8192 x 8192, 64 | 3.537 | 3.537 | 1.0000 | 3.084
| 3.084 | 1.0000 |
| `fp8_sm90` | 131072 x 8192 x 8192, 64 | 14.37 | 14.37 | 1.0000 | 12.87
| 12.87 | 1.0000 |
| `fp8_sm90` | 4096 x 32768 x 8192, 64 | 1.755 | 1.755 | 1.0000 | 1.512
| 1.512 | 1.0000 |
| `fp8_sm90` | 32768 x 32768 x 8192, 64 | 14.14 | 14.14 | 1.0000 | 12.68
| 12.68 | 1.0000 |
| `fp8_sm90` | 131072 x 32768 x 8192, 64 | 58.12 | 58.12 | 1.0000 |
52.58 | 52.58 | 1.0000 |
| `fp8_sm90` | 4096 x 8192 x 32768, 64 | 1.716 | 1.716 | 1.0000 | 1.486
| 1.486 | 1.0000 |
| `fp8_sm90` | 32768 x 8192 x 32768, 64 | 14.02 | 14.02 | 1.0000 | 13.02
| 13.02 | 1.0000 |
| `fp8_sm90_hint` | 131072 x 8192 x 32768, 64 | 57.06 | 56.54 | 0.9937 |
51.00 | 50.23 | 0.9848 |
| `fp8_sm90` | 32768 x 3072 x 3072, 32 | 0.527 | 0.527 | 1.0000 | 0.465
| 0.465 | 1.0000 |
| `fp8_sm90` | 32768 x 3072 x 3072, 128 | 0.555 | 0.555 | 1.0000 | 0.487
| 0.487 | 1.0000 |
| `fp8_sm90` | 32768 x 12288 x 3072, 32 | 2.114 | 2.114 | 1.0000 | 1.832
| 1.832 | 1.0000 |
| `fp8_sm90` | 32768 x 12288 x 3072, 128 | 2.220 | 2.220 | 1.0000 |
1.919 | 1.919 | 1.0000 |
| `fp8_sm90` | 32768 x 8192 x 8192, 32 | 3.562 | 3.562 | 1.0000 | 3.084
| 3.084 | 1.0000 |
| `fp8_sm90` | 32768 x 8192 x 8192, 128 | 3.636 | 3.636 | 1.0000 | 3.148
| 3.148 | 1.0000 |
| `fp8_sm90` | 32768 x 32768 x 8192, 32 | 14.39 | 14.39 | 1.0000 | 12.77
| 12.77 | 1.0000 |
| `fp8_sm90` | 32768 x 32768 x 8192, 128 | 14.63 | 14.63 | 1.0000 |
12.98 | 12.98 | 1.0000 |
| `fp8_sm90` | 32768 x 16384 x 8192, 64 | 7.131 | 7.131 | 1.0000 | 6.267
| 6.267 | 1.0000 |
| `fp8_sm90` | 32768 x 8192 x 16384, 64 | 6.864 | 6.864 | 1.0000 | 6.275
| 6.275 | 1.0000 |
| `fp8_sm90` | 32768 x 4096 x 8192, 64 | 1.819 | 1.819 | 1.0000 | 1.552
| 1.552 | 1.0000 |
| `fp8_sm90` | 32768 x 8192 x 4096, 64 | 1.861 | 1.861 | 1.0000 | 1.598
| 1.598 | 1.0000 |

NVIDIA H100 80GB HBM3 (SXM, 700 W), sm_90a, CUDA 13 (kernels compiled
with NVRTC 13.4, PyTorch cu130 runtime). CUPTI kernel time, cold L2. The
`fp8_sm90_hint` row uses 6 back-to-back rounds and 3 cooled rounds, each
round timing the previous program and then the new one. Previous and new
are each program's median over the rounds. new / previous is the median
of the per-round paired ratios, not the quotient of the two medians. The
`fp8_sm90` rows measure the unchanged program once over 3 back-to-back
and 2 cooled rounds, and its median is shown as both previous and new.
Each shape runs the program FlashInfer dispatches for it
(`fp8_sm90_hint` only for 131072 x 8192 x 32768). Back to back: GPU
power-throttled. Cooled: a GPU delay of about one kernel time before
every timed launch. Rank is the LoRA rank; bias off.

Cake also ships this family as FP8 across sm_100a / sm_103a (four
Blackwell programs) and as NVFP4 across sm_100a / sm_103a (five
programs), and the sm_90a coverage is the two FP8 programs, of which
this PR changes `fp8_sm90_hint`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated tile scheduling and coordinated data loading for supported
quantized LoRA matrix operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b74f34d](https://github.com/flashinfer-ai/flashinfer/commit/b74f34de71747d392aa6716c14c0bfc42101f9dd)

- **作者**: eigen
- **时间**: 2026-10-19T10:09:55Z
- **提交信息**: perf(cake_deepgemm_mega_gate): deterministic small-M route on a cta_group::2 split-1 template -- one exported template for M <= 16 deterministic calls (SM100a, SM103a) (#6427)

The Cake fused MoE routing gate
(`flashinfer.experimental.deepgemm_mega_gate`, public API
`flashinfer.mega_gate.prepare_mega_gate`) is one persistent BF16 kernel.
It computes the router GEMM `x[M,K] @ weight[E,K]^T` with FP32
accumulation and applies `sqrtsoftplus` scoring with an FP32 expert
bias. It then selects the top-6 of E = 384 experts (K = 5120),
normalizes and scales the unbiased weights, and returns int64 physical
expert indices `[M, topk(+shared)]` with FP32 weights. The kernel source
exports 16 schedule templates, each compiled as one program. They differ
in block tokens, MMA CTA pairing (single CTA or a `cta_group::2` pair),
split-K count, expert groups, pipeline stages, gate warpgroups and
K-block merge. The templates cover the single-token 16-way cluster
split-K route, the 2..4-token cluster route, exact-shape programs for
the production token counts 1, 3, 16, 128 and 512 and for the
2..16-token logical-output route, runtime programs for every other token
count, and the deterministic (split-K-free) routes.

This PR adds one deterministic template for calls of at most 16 tokens.
It is a paired-CTA (`cta_group::2`) split-1 template with:
- one 32-token block (rows 16..31 are zero-filled and never ranked)
- three expert groups with two MMA CTAs each
- 22 pipeline stages merged into eleven 128-wide K blocks
- a 3 x 2 CTA launch grid

Deterministic calls of at most 16 tokens on the 128-expert group
partition now use this template instead of the single-CTA split-1
template. The output bits match the previous program because the
per-expert, per-token FP32 accumulation order is the same and split
stays 1. Deterministic calls above 16 tokens, all non-deterministic
routes, and the `prepare_mega_gate` entry point and arguments are
unchanged.

The baseline is the previous Cake version of this family on FlashInfer
main. Against it, the deterministic 16-token call drops from 14.368 to
11.360 µs on B200 (1.265x) and from 13.664 to 10.528 µs on GB300
(1.298x).

Timing uses CUPTI kernel-time medians of the whole call (one launch per
row), not CUDA events, with L2 flushed before every launch. Each row has
12 readings. On B200 that is one reading per shard on eight distinct
GPUs over two allocations of the same node class. On GB300 it is four
distinct GPUs of one node, each read three times. Each table cell is the
median of its readings. Shapes: K = 5120, E = 384, top-k 6, token count
M as listed. Only the deterministic 16-token row runs a different
program. Every other row runs a byte-identical program on both sides,
but its two columns come from separate measurement passes, so its ratio
shows measurement spread, not a change.

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.3

| tokens (M) | route | previous, µs | this PR, µs | speedup |
|---:|---|---:|---:|---:|
| 1 | physical map | 7.360 | 7.136 | 1.031 |
| 3 | physical map | 8.576 | 8.512 | 1.008 |
| 16 | physical map | 8.640 | 8.864 | 0.975 |
| 16 | deterministic, paired-CTA split-1 (this PR) | 14.368 | 11.360 |
1.265 |
| 16 | logical output | 8.448 | 8.576 | 0.985 |
| 128 | physical map | 9.440 | 9.664 | 0.977 |
| 512 | physical map | 11.488 | 11.488 | 1.000 |
| 1024 | physical map | 12.880 | 13.024 | 0.989 |
| 2048 | physical map | 16.656 | 16.640 | 1.001 |
| 4096 | physical map | 24.640 | 24.656 | 0.999 |
| 8192 | physical map | 37.696 | 37.632 | 1.002 |

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.3

| tokens (M) | route | previous, µs | this PR, µs | speedup |
|---:|---|---:|---:|---:|
| 1 | physical map | 6.880 | 6.896 | 0.998 |
| 3 | physical map | 8.352 | 8.336 | 1.002 |
| 16 | physical map | 8.448 | 8.416 | 1.004 |
| 16 | deterministic, paired-CTA split-1 (this PR) | 13.664 | 10.528 |
1.298 |
| 16 | logical output | 8.288 | 8.208 | 1.010 |
| 128 | physical map | 9.408 | 9.376 | 1.003 |
| 512 | physical map | 11.264 | 11.152 | 1.010 |
| 1024 | physical map | 12.704 | 12.752 | 0.996 |
| 2048 | physical map | 16.224 | 16.288 | 0.996 |
| 4096 | physical map | 23.568 | 23.616 | 0.998 |
| 8192 | physical map | 35.360 | 35.328 | 1.001 |

The family's other Cake variants (other scoring functions, image bias,
token masks and fixed/random routing) are part of the kernel ABI but
have no exported program; the family ships on sm_100a (B200) and sm_103a
(GB300), with one source per program serving both architectures.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [2844806](https://github.com/flashinfer-ai/flashinfer/commit/2844806b5f3732029d1f4baacf77577d4c887cbc)

- **作者**: eigen
- **时间**: 2026-10-19T10:08:52Z
- **提交信息**: feat(cake_comm): QkvNormRopeExchangeOverlap per-world-size producer variants and plan defaults on sm_100a / sm_103a / sm_90a (#6613)

## 📌 Description

Stacked on #6537 (merge that first); the diff against #6537's head is
this round's change.

#6537 turned on two host-side shape gates by default on SM100 and SM103.
This PR does three things:

* It picks the producer build and the plan's group scaling of
`flashinfer.comm.QkvNormRopeExchangeOverlap` per (architecture, world
size), using the settings that measured faster on each.
* On SM90 it rebuilds the bn128 producer with a six-stage TMA ring.
* On SM90 it turns on a third shape gate, `reserved_sms_large_m`.

Below, W is the world size and M is the number of token rows each rank
projects (batch × local sequence length). K is the hidden size.

Defaults per (architecture, world size):

| Architecture | W | Producer build | `group_m_scale` |
`reserved_sms_large_m` |
|---|---|---|---|---|
| SM100 (B200) | 8 | `bulk_ow256` (`operand_load_width=256`,
`store_path=bulk`) | 1 | 0 (off) |
| SM100 (B200) | 4 | `ow256` (`operand_load_width=256`) | 2 | 0 |
| SM100 (B200) | 2 | shipped (as in #6537) | 2 | 0 |
| SM103 (B300) | 8 | `ow256` | 2 | 0 |
| SM103 (B300) | 4 | `ow256` | 2 | 0 |
| SM103 (B300) | 2 | shipped | 2 | 0 |
| SM90 (H100) | 8 / 4 / 2 | shipped; the bn128 producer now uses a
six-stage TMA ring (bn256 unchanged) | 1 | 16384 |

* **`group_m_scale = 2`** applies only to grouped-order rows with K ≥
6144. On those rows it scales group_m, for example from 8 to 16 on the W
= 2, 8192 × 131072 row. All other rows keep the #6537 plan.
* **`reserved_sms_large_m = 16384`** (SM90): for calls with M ≥ 16384
the host plan reserves no SMs. On H100 the grid goes from 130 to 132.
* **New programs**: the `ow256` and `bulk_ow256` builds ship as separate
tcgen05 programs next to the shipped ones. Routes are keyed by the build
variant.
* **Opt-outs**: each environment variable restores the #6537 behavior
for its part.
* `FLASHINFER_QKV_EXCHANGE_PRODUCER_VARIANT=shipped` restores the
shipped producer build.
* `FLASHINFER_QKV_EXCHANGE_GROUP_M_SCALE=1` restores the #6537 group_m.
* `FLASHINFER_QKV_EXCHANGE_SHAPE_GATES=reserved_sms_large_m=0` restores
the #6537 SM90 host path.

The SM90 six-stage bn128 producer is a rebuilt program, not a setting.
The four-stage program is no longer shipped. Its outputs are bitwise
identical (see Tests).
* **Unchanged**:
* The public interface. There is no new keyword argument. The new inputs
are the two environment variables above and the third gate name in
`FLASHINFER_QKV_EXCHANGE_SHAPE_GATES`.
* The numerics. BF16 Q/K/V outputs are bitwise identical on every
compared arm pair, #6537 behavior (control run or opt-out) against the
new default (see Tests).
* The validation protocol. The export-protocol validation uses the same
rows and per-row receipt gates as #6537. One H100 perf row is excluded;
see Reviewer Notes.
* **Plan record**: the plan records the selected producer build, the
group_m scale and the shape gates, so the record of a run shows which
plan was chosen.

Measured effect of the new defaults (OFF → default, per-call GPU time of
the fused arm; details in Speedup):

* B200:
* W = 8: +4.34 % and +4.27 % on 3072 × 32768, and +1.20 % and +1.05 % on
8192 × 131072, over two runs. On 3072 × 4096 the two runs read −0.51 %
(beyond A/A) and −0.43 % (within A/A). The default is kept; see the note
in Speedup.
  * W = 4: +0.64 % and +1.98 %.
* W = 2: +4.53 % on 8192 × 131072. The 3072 × 8192 row is a control
(+0.03 %).
* B300:
  * W = 8: +0.44 %, +3.05 % and +0.19 %.
* W = 4: +1.62 % and +1.71 % on 6144 × 32768 (two runs). 4096 × 4096 is
void in both runs.
  * W = 2: +4.24 % on 8192 × 131072.
* H100:
* W = 8: +3.54 % on 3072 × 4096 (the six-stage producer). 8192 × 131072
is within A/A (+0.20 %).
  * W = 2: +0.70 % on 8192 × 65536. 3072 × 8192 is within A/A (−0.03 %).
* The `reserved_sms_large_m` gate alone, measured against its opt-out:
+0.62 % (W = 8) and +1.14 % (W = 2) on the large rows.

The export protocol is re-measured per row on all three architectures;
see Speedup.

### Files

Compared with the head of #6537 (8be70df7):

| Path | Change |
|---|---|
| `csrc/cake_qkv_norm_rope_exchange_overlap/` | Generated translation
units: 39 programs × {binding, kernel} = 78 `.cu` files (#6537 had 21
programs). 18 programs are new tcgen05 variants: nine `bulk_ow256`
programs (SM100) and nine `ow256` programs (six SM103 bn128 builds and
three bn256 pair builds routed on both SM100 and SM103). The three SM90
bn128 producer programs (main, fold0, fold1) are replaced by the
six-stage rebuild, so their ids change. |
| `flashinfer/comm/cake_qkv_exchange_plan.py`,
`flashinfer/comm/cake_qkv_norm_rope_exchange_overlap.py`,
`flashinfer/comm/qkv_norm_rope_exchange_overlap.py` | Per-(architecture,
world size) `group_m_scale` defaults and the K ≥ 6144 rule; the third
shape gate `reserved_sms_large_m` (the reserved-SM count moves into the
plan module); the producer build, group scale and shape gates in the
plan record; the two new opt-out variables |
| `flashinfer/jit/cake_qkv_norm_rope_exchange_overlap.py` |
Per-(architecture, world size) producer-variant defaults; routes keyed
by build variant; the new variant programs and the renamed SM90 bn128
ids |
| `benchmarks/comm/bench_qkv_norm_rope_exchange_overlap.py` | Records
the fused arm's producer variant and group_m scale in its output |
| `tests/comm/test_qkv_norm_rope_exchange_overlap.py` | 37 tests (#6537:
32): five new host-only tests, covering the two default tables, the two
environment resolutions and the producer-key grammar |
| `CLAUDE.md` | four rows added after the
`FLASHINFER_SM90_CAKE_BF16_COMBINE_WIRE` row |
| API documentation | the new defaults, and the H100 80 GB limit for W =
2, 8192 × 131072 |

## 🔍 Related Issues

- Stacked on #6537 (merge that first); the diff against #6537's head is
this round's change.
- #6516: the earlier PR in this series, which #6537 follows up.
- #6304: the feature request behind `QkvNormRopeExchangeOverlap`.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

Pre-commit has been run at this head (`9b8f2c93`) on a CPU-only node:
every hook passed on the files changed against the upstream base,
`pre-commit run mypy --all-files` exited 0, and the working tree was
clean afterwards. The hooks are run as for #6537: `pre-commit run
--show-diff-on-failure --files <the files changed against the upstream
base 5e454aa7>`, plus `pre-commit run mypy --all-files`.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing. The whole test file passed on 8-GPU B200
and H100 nodes (37 passed on each) and on an 8-GPU B300 node. It ran on
a tree identical to this head (see the test plan). A CPU-only run at
this head is not recorded here.

This head is rendered from the upstream generator at 9ca399c5. The OFF →
default pairs in Speedup were measured at the generator's previous
revision 7b2cc583. 9ca399c5 changes only the generator's export-protocol
adapter and the formatting of that adapter's test, not a kernel, the
host plan or a rendered file, so those pairs were not re-measured. The
acceptance checks below (bitwise identity, compute-sanitizer, CUDA-graph
replay, dual-communicator, overlap, GPU tests) were re-run at 9ca399c5:
GPU acceptance subset re-run at the code-final tip `9ca399c5` on all
three architectures (B200 / B300 / H100): output digests identical to
the OFF arm and to the round-2 control (48/48, 50/50, 70/70 arms; H100
two-tree 72/76/110), acceptance I and H PASS, exchange-overlap E reading
unchanged, `compute-sanitizer` synccheck / memcheck / racecheck 8/8
ranks 0 errors (B200 for both the `bulk_ow256` default set and the
`ow256` W4 set), FlashInfer `pytest` 37/37 and the bench guard RC_ALL=0
on the rendered tree `781424c8` for each architecture. The checks used
the kernel generator's acceptance harness on 8-GPU B200, B300 and H100
nodes. The FlashInfer tests ran on a render whose tree hash equals this
head's tree.

### Test plan

- [ ] `pytest tests/comm/test_qkv_norm_rope_exchange_overlap.py -q -k
"not multi_gpu"` on a CPU-only runner at this head: not yet recorded.
- [x] `pre-commit run --show-diff-on-failure --files <changed files>`
and `pre-commit run mypy --all-files` at head 9b8f2c93 on a CPU-only
node: all hooks passed, mypy exit 0, no post-hook diff.
- [x] Bitwise output identity with the new defaults:
  - B200 and B300:
- W = 8: per-rank Q/K/V digests were identical (48/48) to the control
run recorded for #6537. No opted-out W = 8 run was made at this
revision.
- W = 4 and W = 2: the default and opted-out runs were identical, 50/50
and 70/70.
    - The fp32 reference digests were the same.
- Every digest record carried the expected build and scale for its tier.
On B200 these are `bulk_ow256` / 1 at W = 8, `ow256` / 2 at W = 4 and
shipped / 2 at W = 2. On B300 they are `ow256` / 2 at W = 8 and W = 4,
and shipped / 2 at W = 2.
  - H100:
- Against the generator's final round-2 revision, whose programs are the
#6537 programs (two build trees on one node): W = 8 72/72, W = 4 76/76
and W = 2 110/110 identical.
- Against the `reserved_sms_large_m=0` opt-out: W = 8 72/72 and W = 2
110/110 identical.
    - The reference digests were the same.
- [x] compute-sanitizer synccheck, memcheck and racecheck with the
defaults on B200, B300 and H100:
- Rows: `corr_w8_min`, `sanitize_w8_bn256` and
`sanitize_w8_bn128_m16384`, each in the `bshd_three` and `fused_payload`
layouts, on 8 ranks. The recorded shape-gate decisions matched the
expected ones on 48/48 in every run.
- B200: each tool ran twice, once on the W = 8 default (`bulk_ow256`)
and once on the `ow256` build (the W = 4 default). In all six runs
synccheck and memcheck reported `ERROR SUMMARY: 0 errors` on 8/8 ranks,
racecheck reported 8/8 summaries at 0, and the expected variant appeared
on 48/48.
- B300 (`ow256`): synccheck and memcheck reported 0 errors on 8/8 ranks,
and racecheck reported 8/8 summaries at 0. The M = 16384 row uses
per-destination launches.
- H100: synccheck and memcheck reported 0 errors on 8/8 ranks, and
racecheck passed. `sanitize_w8_bn128_m16384` fires
`reserved_sms_large_m`.
- Coverage: the sanitizer rows are W = 8. On B200 and B300 the W = 2
tier runs the shipped programs. Their compiled hashes are unchanged, so
the #6537 sanitizer runs still apply to them.
- [x] CUDA-graph replay with the defaults:
- B200 W = 8 passed: 12 arms on the two smaller rows and 14 on 8192 ×
131072, replayed fused-arm outputs bitwise identical on all ranks and
tensors, and no replay mismatch. B200 W = 4 also passed.
  - B300 W = 8 and W = 4 passed.
  - H100 W = 8 passed.
- [x] Dual-communicator concurrency test with the defaults: passed on
B200 and H100. On B300 the test ran with the rest of the B300 set, but
its individual verdict is not quoted in the record.
- [x] Overlap measurement on the W = 8, 3072 × 4096 row (fused arm):
- B200: the ratio was min 0.1429 / median 0.2857 both with the #6537
defaults and with the new defaults, so the new default leaves overlap
unchanged on this row.
  - H100: passed.
  - B300: not quoted in the record.
- [x] OFF → default performance comparison on all three architectures
(see Speedup).
- [x] GPU tests on 8-GPU nodes. These run the whole
`tests/comm/test_qkv_norm_rope_exchange_overlap.py` with 37 tests
expected, including `multi_gpu[2|4|8]` and the default-vs-opted-out
bitwise comparison. They also run the benchmark on representative rows.
- B200: 37 passed / 0 failed / 0 skipped; `multi_gpu[8]` took 114.4 s.
The benchmark guard ran 4 rows each at W = 2 / 4 / 8 (hidden 4096 / 8192
× S 16384 / 65536). On every row:
    - 2 calls per iteration with the L2 flush;
    - max |diff| 0.0625 (gate: at most 0.0625);
    - V bitwise zero-diff;
    - the b2 / b3 / b4 baseline arms bitwise identical to the b1 arm.

The shape gates reported `source: default` with `words_capacity_small_m
= 4096`, `reserved_sms_large_m = 0` and `per_dest_large_m = 16384`.
- H100: 37 passed; `multi_gpu[4]` took 19.1 s and `multi_gpu[8]` 49.4 s.
The benchmark guard ran 4 rows at W = 8 and passed the same checks. The
shape gates reported `source: default` with `reserved_sms_large_m =
16384`.
- B300: the tests and the benchmark guard passed. The counts are not
quoted in the record.

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

- Stacked on #6537 (merge that first); the diff against #6537's head is
this round's change. That change is one commit, 9b8f2c93, on top of the
#6537 head 8be70df7. Until #6537 and the PRs below it are merged, the
diff against upstream main 5e454aa7 also shows their changes.
- The defaults are explicit and reversible through the three environment
variables in the Description. The one exception is the SM90 bn128
rebuild, which is a new program with bitwise-identical outputs.
- Because the defaults are tiered by world size, the B200 W = 8 path now
uses the bulk-store build (`bulk_ow256`). W = 4 uses the `ow256` build
and W = 2 the #6537 programs. On B200, group_m_scale stays 1 at W = 8.
- The B200 W = 8, 3072 × 4096 row read slightly negative in the eager
pairs and faster under graph replay. The default is kept; the details
are in Speedup.
- H100 `reserved_sms_large_m`: the W = 2 reading depends on the rule
(see Speedup). The strict reading rejects it, because a control row
drifted. The pre-registered reading adopts it. The gate is on for every
world size, and the split is disclosed rather than hidden.
- On H100 80 GB the W = 2, 8192 × 131072 shape needs 71.4 GB, but 67.4
GB is available. It is not measurable, so it is excluded and H100 has 71
perf rows. The API documentation states this limit. On H100, 8192 ×
65536 is used as the W = 2 large row.
- The generator's static analyzer does not classify the 32-byte operand
reads in the `ow256` epilogue, so its five passes do not cover the
`ow256` and `bulk_ow256` builds. Their correctness evidence is the GPU
checks above: bitwise identity, compute-sanitizer and the tests.
- The kernel generator renders the generated files. This head's tree
equals the render on which the GPU tests ran. There are 78 generated
`.cu` files (39 programs × binding + kernel). A count of 79 tracked
files in that directory includes its `.clang-format`.

## Speedup

### Effect of the new defaults (OFF -> default)

All pairs used the kernel generator's acceptance harness on 8-GPU nodes:

* On B200 and B300 the OFF run is the #6537 behavior, selected through
the opt-outs: the shipped producer build with group_m_scale 1. The
default run sets no variable.
* On H100 the OFF run is the generator's final round-2 revision, whose
programs are the #6537 programs, built as a second tree on the same
node. A second OFF arm, "gate opt-out", is this revision with
`reserved_sms_large_m=0`; it isolates that gate.

Each pair is an A/B/B/A comparison on one node within one allocation,
with an in-session A/A control per arm. The metric is the per-call GPU
time of the fused arm, and gain = (t_OFF − t_default) / t_OFF. The
verdicts mean:

- **improves**: the gain exceeds the A/A control.
- **within A/A**: the gain or loss does not exceed the A/A control.
- **regresses**: the loss exceeds the A/A control.
- **void**: the in-session A/A of at least one arm exceeded 1 %. A void
row is reported but not counted.
- **control**: the default does not change this row's plan or program,
so the difference only measures session drift. The verdict is "control
ok" if the difference stays within A/A and "control drift" if it does
not.

Two readings are reported where they differ. The strict reading counts
control drift against the default. The pre-registered reading treats
control drift as session noise.

Rows are given as hidden × S_global.

**B200 (SM100).** W = 8 was measured in two runs in separate
allocations. W = 4 and W = 2 come from run 1.

| W | row | run | OFF → default (ms) | gain | A/A (OFF / default) |
verdict |
|---|---|---|---|---|---|---|
| 8 | 3072 × 4096 (M = 512) | 1 | 0.053472 → 0.053744 | −0.51 % | 0.10 %
/ 0.05 % | regresses |
| 8 | 3072 × 4096 (M = 512) | 2 | 0.052416 → 0.052640 | −0.43 % | 0.60 %
/ 0.03 % | within A/A |
| 8 | 3072 × 32768 (M = 4096) | 1 | 0.214160 → 0.204864 | +4.34 % | 0.17
% / 0.23 % | improves |
| 8 | 3072 × 32768 (M = 4096) | 2 | 0.214543 → 0.205375 | +4.27 % | 0.13
% / 0.09 % | improves |
| 8 | 8192 × 131072 (M = 16384) | 1 | 4.790910 → 4.733278 | +1.20 % |
0.05 % / 0.03 % | improves |
| 8 | 8192 × 131072 (M = 16384) | 2 | 4.794195 → 4.743666 | +1.05 % |
0.00 % / 0.04 % | improves |
| 4 | 4096 × 4096 (M = 1024) | 1 | 0.099488 → 0.098848 | +0.64 % | 0.26
% / 0.18 % | improves |
| 4 | 6144 × 32768 (M = 8192) | 1 | 1.321455 → 1.295295 | +1.98 % | 0.10
% / 0.13 % | improves |
| 2 | 3072 × 8192 (M = 4096) | 1 | 0.173744 → 0.173696 | +0.03 % | 0.10
% / 0.21 % | control ok |
| 2 | 8192 × 131072 (M = 65536; group_m 8 → 16) | 1 | 22.626456 →
21.601472 | +4.53 % | 0.61 % / 0.34 % | improves |

**B300 (SM103).** Run 1 covered all rows. Run 2 re-measured W = 4 in a
second allocation.

| W | row | run | OFF → default (ms) | gain | A/A (OFF / default) |
verdict |
|---|---|---|---|---|---|---|
| 8 | 3072 × 4096 (M = 512) | 1 | 0.055089 → 0.054848 | +0.44 % | 0.10 %
/ 0.20 % | improves |
| 8 | 3072 × 32768 (M = 4096) | 1 | 0.214818 → 0.208258 | +3.05 % | 0.57
% / 0.41 % | improves |
| 8 | 8192 × 131072 (M = 16384) | 1 | 4.204138 → 4.196090 | +0.19 % |
0.09 % / 0.02 % | improves |
| 4 | 4096 × 4096 (M = 1024) | 1 | 0.096321 → 0.095232 | +1.13 % | 1.10
% / 1.07 % | void |
| 4 | 4096 × 4096 (M = 1024) | 2 | 0.096353 → 0.095249 | +1.15 % | 2.09
% / 2.39 % | void |
| 4 | 6144 × 32768 (M = 8192) | 1 | 1.138218 → 1.119786 | +1.62 % | 0.13
% / 0.14 % | improves |
| 4 | 6144 × 32768 (M = 8192) | 2 | 1.164297 → 1.144445 | +1.71 % | 0.09
% / 0.09 % | improves |
| 2 | 3072 × 8192 (M = 4096) | 1 | 0.161010 → 0.160656 | +0.22 % | 0.12
% / 0.27 % | control ok |
| 2 | 8192 × 131072 (M = 65536) | 1 | 20.938933 → 20.051026 | +4.24 % |
0.41 % / 0.20 % | improves |

**H100 (SM90).** All pairs ran in one allocation. W = 4 pairs are not
reported here.

| W | row | OFF arm | OFF → default (ms) | gain | A/A (OFF / default) |
verdict |
|---|---|---|---|---|---|---|
| 8 | 3072 × 4096 (M = 512; six-stage bn128 producer) | previous
revision | 0.094879 → 0.091520 | +3.54 % | 0.07 % / 0.52 % | improves |
| 8 | 8192 × 131072 (M = 16384; gate fires, grid 130 → 132) | previous
revision | 10.681358 → 10.659993 | +0.20 % | 0.22 % / 0.12 % | within
A/A |
| 2 | 3072 × 8192 (M = 4096) | previous revision | 0.414622 → 0.414736 |
−0.03 % | 0.01 % / 0.06 % | within A/A |
| 2 | 8192 × 65536 (M = 32768; gate fires) | previous revision |
21.106589 → 20.958400 | +0.70 % | 0.20 % / 0.48 % | improves |
| 8 | 3072 × 4096 (M = 512) | gate opt-out | 0.091567 → 0.091520 | +0.05
% | 0.16 % / 0.52 % | control ok |
| 8 | 8192 × 131072 (M = 16384) | gate opt-out | 10.725976 → 10.659993 |
+0.62 % | 0.38 % / 0.12 % | improves |
| 2 | 3072 × 8192 (M = 4096) | gate opt-out | 0.414351 → 0.414736 |
−0.09 % | 0.08 % / 0.06 % | control drift |
| 2 | 8192 × 65536 (M = 32768) | gate opt-out | 21.201067 → 20.958400 |
+1.14 % | 0.01 % / 0.48 % | improves |

Notes:

- **B200 W = 8, 3072 × 4096 (M = 512).** This row takes about 53 µs of
GPU time per call against about 122 µs of host enqueue.
- The two eager pairs read −0.51 % and −0.43 %. The first is beyond the
OFF arm's A/A of 0.10 %; the second is within A/A.
- In run 1, host enqueue in the default arm was 2.2–3.1 % slower on all
three W = 8 rows. In run 2 it was unchanged.
- A host profile of one call shows the same call graph for the #6537
build and the new build: 157 calls and 2 kernel launches.
- Under CUDA-graph replay, which excludes host enqueue, the new build
reads +4.71 % on this row (51.68 → 49.25 µs). The pair is void because
the OFF arm's A/A was 1.01 %. The two larger W = 8 rows read +4.43 % and
+1.24 % (improves).
  - The bulk-store setting alone read +0.85 % on this row (improves).
- The same default program, selected through the environment instead of
the per-world-size table, read −0.68 %. Its records differ only in the
two source labels.
- The torch baseline drifted by up to −1.22 % between consecutive runs
on one node within 20 minutes. That is more than this row's A/A.
- When the defaults were selected, this row read +2.46 %
(`operand_load_width=256` alone), +1.96 % (`store_path=bulk` alone) and
+2.80 % (both).
- We read the eager result as within the session noise of this
host-bound row, and keep the default.
- **Host enqueue on B300.** In the B300 W = 8 pairs, host enqueue in the
default arm was 1.5–1.8 % slower. The GPU time of 3072 × 4096 still
improved (+0.44 %).
- **B300 W = 4, 4096 × 4096.** This row was void in both runs (A/A 1.10
% / 1.07 % and 2.09 % / 2.39 %; point estimates +1.13 % and +1.15 %). It
was also void in three earlier measurements. It is reported but not
counted. The B300 W = 4 default rests on the 6144 × 32768 row.
- **B300 W = 8, 3072 × 32768.** This is the first same-node measurement
of the `ow256` build with the new group scaling. The row has K = 3072,
so the scaling does not apply, and the +3.05 % comes from the `ow256`
build. An earlier measurement of `ow256` alone read +3.64 %.
- **H100 `reserved_sms_large_m`.**
- Measured alone (default vs. gate opt-out), the gate improves both
large rows: +0.62 % at W = 8 and +1.14 % at W = 2. The W = 2 control row
moved −0.09 %, beyond its A/A.
- The strict reading therefore rejects the gate, and the pre-registered
reading adopts it.
- The measurement that selected the default split the same way: +1.66 %
on the W = 2 large row, and −0.23 % on the W = 2 small row, beyond its
A/A.
- That measurement read +1.70 % on the W = 8 large row. The combined
pair here does not reproduce it: +0.20 %, within A/A.
- No selected H100 row regresses beyond its A/A; the only loss beyond
A/A is the W = 2 control row (−0.09 %, control drift).
- **H100 W = 8, 3072 × 4096.** The six-stage producer reads +3.54 %.
Three earlier measurements read +3.01 %, +3.44 % and +3.19 %.
- **H100 W = 2 large row.** H100 uses 8192 × 65536 as its W = 2 large
row, because 8192 × 131072 does not fit in 80 GB.

### Export-protocol validation (per-row receipts)

The new defaults change the delivered programs on all three
architectures: there are new variant programs on SM100 and SM103, and
the rebuilt bn128 producer on SM90. They also change the plan metadata
of the export protocol. All three architectures are therefore
re-measured over the export protocol of the upstream generator at
9ca399c5.

* B200 and B300 receipts are compared row by row with the sealed
receipts of #6537.
* H100 is re-measured for the first time since #6516. The #6516 H100
receipts are recorded alongside but are not compared on the node. H100
has 71 perf rows, because the W = 2, 8192 × 131072 row does not fit in
80 GB.
* Validity gates are never relaxed.

**B200 (SM100): final.**

| | this PR | #6537 |
|---|---|---|
| valid perf rows | 71 of 72 (all 71 above 1.00) | 71 of 72 |
| geomean (W = 8 / W = 4 / W = 2) | 1.792 (1.678 / 1.823 / 1.886) |
1.758 (1.634 / 1.786 / 1.867) |
| minimum | 1.404 (W = 8, 8192 × 4096) | 1.399 (W = 8, 3072 × 4096) |
| perf exceptions | 1 (it was an exception in #6537 and #6516) | 1 |

Correctness rows: 13 of 13 have a passing receipt. `corr_w2_max`, which
had none in #6537, passes here.

The receipts come from four sealed snapshots on four B200 nodes. All
four nodes ran the same GPU model, driver and PyTorch build:

- snapshot 1 (first node): all 24 W = 2 perf rows and 5 correctness
rows; 29 receipts, 26 passed (22 perf, 4 correctness)
- snapshot 2 (second node): all 24 W = 4 perf rows and 4 correctness
rows; 28 receipts, 28 passed
- snapshot 3 (third node): all 24 W = 8 perf rows and 4 correctness
rows; 28 receipts, 28 passed
- snapshot 4 (fourth node): the 3 W = 2 rows without a passing receipt
in snapshot 1, re-measured with the receipts of snapshots 1 to 3 as
priors; 3 receipts, 2 passed

When a row has more than one receipt, its passing receipt is the row of
record.

The one row without a valid receipt on B200:

- `perf_w2_h8192_s131072` (perf): invalid on two nodes.
- Snapshot-1 node: b1/b2/b3 directional disagreement (raw speedup 1.421,
loaded clock 0.752).
- Snapshot-4 node: b2 directional disagreement (raw speedup 1.388,
loaded clock 0.992).
  - Correctness of the row passed on both nodes.
- The same failure class as in #6537 (raw speedup 1.317 there) and
#6516. No further attempt was made.

Rows whose status changed relative to #6537:

- `corr_w2_max`: no passing receipt in #6537 (the loaded SM clock was
below the 0.50 gate on both nodes). It passes here (snapshot-4 node,
loaded clock 0.546). Its snapshot-1 receipt records no measurement: the
rank set aborted (SIGABRT) because the loaded SM clock was below the
0.50 gate (937 of 1965 MHz). That receipt is disclosed here.

Re-measured row whose status did not change:

- `perf_w2_h6144_s131072`: valid in #6537 and valid here (1.651,
snapshot-4 node, loaded clock 0.828). Its snapshot-1 receipt records no
measurement (the rank set aborted, SIGABRT) and is disclosed here.

A row-by-row comparison with the #6537 B200 receipts covered the 71 rows
that are valid in both. The runs used different nodes and sessions, so
the comparison is informational only:

- median +1.89 %
- range from −1.64 % (`perf_w2_h4096_s131072`) to +9.98 %
(`perf_w8_h3072_s8192`)
- 60 rows faster, 11 slower; 17 rows moved by more than 3 % (17 up, 0
down)
- the largest gains are W = 8 and W = 4 rows with hidden size 3072 or
4096, where this PR's producer-build and `group_m` defaults apply

The delivered SM100 sources are the programs the per-(architecture,
world size) defaults route to. The export table measures the defaults
against the four baselines, not against the opted-out plan. The
same-node, same-process OFF → default pairs above are the evidence for
the defaults.

#### sm_100a: export receipts per row

| W | hidden | S_global | export ms | fastest baseline (ms) | speedup |
B1 | B2 | B3 | B4 | source/export | status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 8 | 3072 | 4096 | 0.0530 | b2_whole_qkv (0.0783) | **1.477** | 1.928 |
1.477 | 2.060 | 2.252 | 1.027 | passed |
| 8 | 3072 | 8192 | 0.0736 | b2_whole_qkv (0.1192) | **1.618** | 1.920 |
1.618 | 2.020 | 2.823 | 1.012 | passed |
| 8 | 3072 | 16384 | 0.1274 | b2_whole_qkv (0.2114) | **1.659** | 1.697
| 1.659 | 1.784 | 2.352 | 1.015 | passed |
| 8 | 3072 | 32768 | 0.2029 | b3_head_chunk (0.3987) | **1.965** | 2.036
| 2.003 | 1.965 | 2.927 | 1.001 | passed |
| 8 | 3072 | 65536 | 0.4927 | b1_ordinary (0.7950) | **1.613** | 1.613 |
1.646 | 1.653 | 2.262 | 1.006 | passed |
| 8 | 3072 | 131072 | 0.9436 | b1_ordinary (1.5577) | **1.651** | 1.651
| 1.700 | 1.721 | 2.263 | 0.998 | passed |
| 8 | 4096 | 4096 | 0.0737 | b2_whole_qkv (0.1085) | **1.472** | 1.773 |
1.472 | 1.901 | 2.126 | 1.018 | passed |
| 8 | 4096 | 8192 | 0.0953 | b2_whole_qkv (0.1627) | **1.708** | 1.918 |
1.708 | 2.053 | 2.541 | 1.016 | passed |
| 8 | 4096 | 16384 | 0.1500 | b2_whole_qkv (0.3109) | **2.073** | 2.099
| 2.073 | 2.152 | 2.969 | 1.003 | passed |
| 8 | 4096 | 32768 | 0.2691 | b1_ordinary (0.5812) | **2.160** | 2.160 |
2.190 | 2.222 | 3.009 | 0.994 | passed |
| 8 | 4096 | 65536 | 0.5653 | b1_ordinary (1.1504) | **2.035** | 2.035 |
2.091 | 2.136 | 2.824 | 0.997 | passed |
| 8 | 4096 | 131072 | 1.2527 | b1_ordinary (2.2733) | **1.815** | 1.815
| 1.884 | 1.926 | 2.536 | 0.996 | passed |
| 8 | 6144 | 4096 | 0.1009 | b2_whole_qkv (0.1539) | **1.524** | 1.739 |
1.524 | 1.841 | 2.153 | 1.015 | passed |
| 8 | 6144 | 8192 | 0.1603 | b2_whole_qkv (0.2764) | **1.724** | 1.780 |
1.724 | 1.850 | 2.265 | 1.000 | passed |
| 8 | 6144 | 16384 | 0.2935 | b2_whole_qkv (0.5383) | **1.834** | 1.851
| 1.834 | 1.891 | 2.455 | 0.999 | passed |
| 8 | 6144 | 32768 | 0.6082 | b1_ordinary (1.0984) | **1.806** | 1.806 |
1.825 | 1.843 | 2.370 | 1.002 | passed |
| 8 | 6144 | 65536 | 1.2922 | b1_ordinary (2.2395) | **1.733** | 1.733 |
1.780 | 1.808 | 2.298 | 1.003 | passed |
| 8 | 6144 | 131072 | 2.5670 | b1_ordinary (4.2713) | **1.664** | 1.664
| 1.715 | 1.742 | 2.220 | 1.005 | passed |
| 8 | 8192 | 4096 | 0.1637 | b2_whole_qkv (0.2298) | **1.404** | 1.527 |
1.404 | 1.605 | 1.872 | 1.009 | passed |
| 8 | 8192 | 8192 | 0.2916 | b2_whole_qkv (0.4424) | **1.517** | 1.531 |
1.517 | 1.564 | 2.010 | 0.998 | passed |
| 8 | 8192 | 16384 | 0.5485 | b1_ordinary (0.8656) | **1.578** | 1.578 |
1.596 | 1.602 | 2.016 | 0.998 | passed |
| 8 | 8192 | 32768 | 1.1352 | b1_ordinary (1.7323) | **1.526** | 1.526 |
1.552 | 1.570 | 1.969 | 1.003 | passed |
| 8 | 8192 | 65536 | 2.3306 | b1_ordinary (3.4320) | **1.473** | 1.473 |
1.518 | 1.533 | 1.920 | 1.000 | passed |
| 8 | 8192 | 131072 | 4.6414 | b1_ordinary (7.0317) | **1.515** | 1.515
| 1.565 | 1.565 | 1.958 | 0.990 | passed |
| 4 | 3072 | 4096 | 0.0646 | b2_whole_qkv (0.1043) | **1.614** | 1.982 |
1.614 | 2.067 | 2.630 | 1.009 | passed |
| 4 | 3072 | 8192 | 0.0949 | b2_whole_qkv (0.2008) | **2.115** | 2.230 |
2.115 | 2.291 | 3.175 | 1.002 | passed |
| 4 | 3072 | 16384 | 0.1592 | b2_whole_qkv (0.3942) | **2.476** | 2.509
| 2.476 | 2.527 | 3.449 | 1.020 | passed |
| 4 | 3072 | 32768 | 0.3520 | b1_ordinary (0.7709) | **2.190** | 2.190 |
2.235 | 2.207 | 3.115 | 0.990 | passed |
| 4 | 3072 | 65536 | 0.6737 | b1_ordinary (1.5245) | **2.263** | 2.263 |
2.328 | 2.392 | 3.126 | 0.989 | passed |
| 4 | 3072 | 131072 | 1.3133 | b1_ordinary (2.9980) | **2.283** | 2.283
| 2.382 | 2.434 | 3.154 | 0.997 | passed |
| 4 | 4096 | 4096 | 0.0942 | b2_whole_qkv (0.1531) | **1.625** | 1.807 |
1.625 | 1.905 | 2.402 | 0.996 | passed |
| 4 | 4096 | 8192 | 0.1521 | b3_head_chunk (0.3026) | **1.990** | 2.040
| 2.034 | 1.990 | 2.680 | 0.996 | passed |
| 4 | 4096 | 16384 | 0.2779 | b3_head_chunk (0.5724) | **2.060** | 2.095
| 2.124 | 2.060 | 2.842 | 0.999 | passed |
| 4 | 4096 | 32768 | 0.5545 | b1_ordinary (1.1523) | **2.078** | 2.078 |
2.137 | 2.173 | 2.830 | 1.002 | passed |
| 4 | 4096 | 65536 | 1.1452 | b1_ordinary (2.2904) | **2.000** | 2.000 |
2.072 | 2.103 | 2.722 | 0.997 | passed |
| 4 | 4096 | 131072 | 2.2590 | b1_ordinary (4.5656) | **2.021** | 2.021
| 2.125 | 2.131 | 2.757 | 0.999 | passed |
| 4 | 6144 | 4096 | 0.1568 | b2_whole_qkv (0.2639) | **1.684** | 1.779 |
1.684 | 1.785 | 2.245 | 0.996 | passed |
| 4 | 6144 | 8192 | 0.3003 | b3_head_chunk (0.5237) | **1.744** | 1.800
| 1.783 | 1.744 | 2.317 | 0.998 | passed |
| 4 | 6144 | 16384 | 0.6228 | b1_ordinary (1.0984) | **1.764** | 1.764 |
1.781 | 1.784 | 2.271 | 1.002 | passed |
| 4 | 6144 | 32768 | 1.2947 | b1_ordinary (2.2647) | **1.749** | 1.749 |
1.793 | 1.828 | 2.270 | 0.997 | passed |
| 4 | 6144 | 65536 | 2.5495 | b1_ordinary (4.2986) | **1.686** | 1.686 |
1.748 | 1.791 | 2.208 | 0.998 | passed |
| 4 | 6144 | 131072 | 5.1500 | b1_ordinary (8.7914) | **1.707** | 1.707
| 1.787 | 1.783 | 2.215 | 0.995 | passed |
| 4 | 8192 | 4096 | 0.2949 | b3_head_chunk (0.4344) | **1.473** | 1.507
| 1.501 | 1.473 | 1.846 | 0.996 | passed |
| 4 | 8192 | 8192 | 0.5526 | b3_head_chunk (0.8636) | **1.563** | 1.576
| 1.594 | 1.563 | 2.016 | 1.002 | passed |
| 4 | 8192 | 16384 | 1.1529 | b1_ordinary (1.7360) | **1.506** | 1.506 |
1.536 | 1.557 | 1.914 | 1.000 | passed |
| 4 | 8192 | 32768 | 2.3460 | b1_ordinary (3.4903) | **1.488** | 1.488 |
1.537 | 1.564 | 1.915 | 1.005 | passed |
| 4 | 8192 | 65536 | 4.6001 | b1_ordinary (7.2670) | **1.580** | 1.580 |
1.603 | 1.591 | 1.994 | 1.002 | passed |
| 4 | 8192 | 131072 | 9.2354 | b1_ordinary (14.6709) | **1.589** | 1.589
| 1.624 | 1.623 | 1.922 | 1.000 | passed |
| 2 | 3072 | 4096 | 0.0983 | b2_whole_qkv (0.1924) | **1.958** | 2.055 |
1.958 | 2.074 | 3.058 | 1.006 | passed |
| 2 | 3072 | 8192 | 0.1660 | b3_head_chunk (0.3790) | **2.284** | 2.390
| 2.367 | 2.284 | 3.246 | 1.003 | passed |
| 2 | 3072 | 16384 | 0.3289 | b1_ordinary (0.7638) | **2.322** | 2.322 |
2.367 | 2.389 | 3.246 | 0.995 | passed |
| 2 | 3072 | 32768 | 0.6396 | b1_ordinary (1.5068) | **2.356** | 2.356 |
2.427 | 2.504 | 3.271 | 0.993 | passed |
| 2 | 3072 | 65536 | 1.2637 | b1_ordinary (2.9859) | **2.363** | 2.363 |
2.458 | 2.526 | 3.149 | 0.998 | passed |
| 2 | 3072 | 131072 | 2.5640 | b1_ordinary (5.9681) | **2.328** | 2.328
| 2.445 | 2.488 | 3.126 | 0.999 | passed |
| 2 | 4096 | 4096 | 0.1485 | b3_head_chunk (0.2961) | **1.994** | 2.053
| 2.029 | 1.994 | 2.719 | 1.000 | passed |
| 2 | 4096 | 8192 | 0.2753 | b3_head_chunk (0.5689) | **2.066** | 2.083
| 2.120 | 2.066 | 2.859 | 1.007 | passed |
| 2 | 4096 | 16384 | 0.5513 | b1_ordinary (1.1324) | **2.054** | 2.054 |
2.116 | 2.151 | 2.805 | 0.999 | passed |
| 2 | 4096 | 32768 | 1.1155 | b1_ordinary (2.2607) | **2.027** | 2.027 |
2.102 | 2.141 | 2.760 | 0.999 | passed |
| 2 | 4096 | 65536 | 2.2375 | b1_ordinary (4.5504) | **2.034** | 2.034 |
2.105 | 2.138 | 2.666 | 0.999 | passed |
| 2 | 4096 | 131072 | 4.5370 | b1_ordinary (9.0590) | **1.997** | 1.997
| 2.122 | 2.115 | 2.661 | 0.999 | passed |
| 2 | 6144 | 4096 | 0.2919 | b3_head_chunk (0.5134) | **1.759** | 1.826
| 1.816 | 1.759 | 2.314 | 0.998 | passed |
| 2 | 6144 | 8192 | 0.6030 | b1_ordinary (1.0791) | **1.790** | 1.790 |
1.813 | 1.811 | 2.303 | 0.997 | passed |
| 2 | 6144 | 16384 | 1.2508 | b1_ordinary (2.2278) | **1.781** | 1.781 |
1.817 | 1.840 | 2.298 | 1.000 | passed |
| 2 | 6144 | 32768 | 2.4612 | b1_ordinary (4.2688) | **1.734** | 1.734 |
1.783 | 1.801 | 2.188 | 1.000 | passed |
| 2 | 6144 | 65536 | 5.0507 | b1_ordinary (8.5890) | **1.701** | 1.701 |
1.787 | 1.786 | 2.145 | 0.996 | passed |
| 2 | 6144 | 131072 | 10.4604 | b1_ordinary (17.2672) | **1.651** |
1.651 | 1.688 | 1.719 | 2.057 | 0.990 | passed |
| 2 | 8192 | 4096 | 0.5472 | b3_head_chunk (0.8480) | **1.550** | 1.562
| 1.579 | 1.550 | 1.960 | 0.996 | passed |
| 2 | 8192 | 8192 | 1.1175 | b1_ordinary (1.7186) | **1.538** | 1.538 |
1.571 | 1.587 | 1.949 | 1.000 | passed |
| 2 | 8192 | 16384 | 2.2372 | b1_ordinary (3.4245) | **1.531** | 1.531 |
1.570 | 1.596 | 1.964 | 0.999 | passed |
| 2 | 8192 | 32768 | 4.4647 | b1_ordinary (6.9554) | **1.558** | 1.558 |
1.593 | 1.625 | 1.939 | 0.995 | passed |
| 2 | 8192 | 65536 | 9.2393 | b1_ordinary (13.9043) | **1.505** | 1.505
| 1.579 | 1.622 | 1.878 | 0.998 | passed |
| 2 | 8192 | 131072 | 19.8677 | — | 1.388 (invalid) | 1.388 | 1.421 |
1.419 | 1.686 | — | NOT PASSED (2 attempt(s)):
b2_whole_qkv.directional_disagreement;
b2_whole_qkv.directional_disagreement |

**B300 (SM103): final.**

| | this PR | #6537 |
|---|---|---|
| valid perf rows | 70 of 72 (all 70 above 1.00) | 69 of 72 |
| geomean (W = 8 / W = 4 / W = 2) | 1.777 (1.608 / 1.824 / 1.926) |
1.765 (1.607 / 1.808 / 1.905) |
| minimum | 1.354 (W = 8, 4096 × 4096) | 1.354 (W = 8, 3072 × 4096) |
| perf exceptions | 2 (both were exceptions in #6537 and #6516) | 3 |

Correctness rows: 13 of 13 have a passing receipt. `corr_w2_max`, which
had none in #6537, passes here.

The receipts come from two sealed snapshots on two B300 nodes:

- snapshot 1 (first node): all 85 rows measured; 85 receipts, 82 passed
- snapshot 2 (second node): the 3 perf rows without a passing receipt in
snapshot 1, re-measured with the snapshot-1 receipts as priors; 3
receipts, 1 passed

When a row has more than one receipt, its passing receipt is the row of
record.

Rows without a valid receipt on B300:

- `perf_w2_h6144_s131072` (perf): invalid on two nodes.
- Snapshot-1 node: b2 directional disagreement (raw speedup 1.702,
loaded clock 0.779).
- Snapshot-2 node: b2 directional disagreement (raw speedup 1.786,
loaded clock 0.738).
- The same failure class as in #6537 and #6516. No further attempt was
made.
- `perf_w2_h8192_s131072` (perf): invalid on two nodes.
- Snapshot-1 node: row-level and b2/b3 directional disagreement (raw
speedup 1.499, loaded clock 0.805).
- Snapshot-2 node: row-level and b2/b3 directional disagreement (raw
speedup 1.557, loaded clock 0.642).
- The same failure class as in #6537 and #6516. No further attempt was
made.

Rows whose status changed relative to #6537:

- `perf_w4_h8192_s131072`: invalid in #6537, valid here (1.523,
snapshot-2 node). Its snapshot-1 receipt did not pass (b1 directional
disagreement, raw speedup 1.545, loaded clock 0.613) and is disclosed
here.
- `corr_w2_max`: no passing receipt in #6537 (the loaded SM clock was
below the 0.50 gate on both nodes), passes here.

A row-by-row comparison with the #6537 B300 receipts covered the 69 rows
that are valid in both. The runs used different nodes and sessions, so
the comparison is informational only:

- median +0.60 %
- range from −3.0 % (`perf_w8_h3072_s16384`) to +6.9 %
(`perf_w4_h3072_s4096`)
- 47 rows faster, 22 slower; 13 rows moved by more than 3 % (12 up, 1
down)

The delivered SM103 sources now hold 78 translation units (42 in #6537;
the 36 new ones are the variant programs). The export table measures the
defaults against the four baselines, not against the opted-out plan. The
same-node, same-process OFF → default pairs above are the evidence for
the defaults.

#### sm_103a: export receipts per row

| W | hidden | S_global | export ms | fastest baseline (ms) | speedup |
B1 | B2 | B3 | B4 | source/export | status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 8 | 3072 | 4096 | 0.0548 | b2_whole_qkv (0.0771) | **1.407** | 1.847 |
1.407 | 1.926 | 2.626 | 1.009 | passed |
| 8 | 3072 | 8192 | 0.0805 | b2_whole_qkv (0.1125) | **1.398** | 1.638 |
1.398 | 1.772 | 2.436 | 0.967 | passed |
| 8 | 3072 | 16384 | 0.1306 | b2_whole_qkv (0.2032) | **1.556** | 1.609
| 1.556 | 1.662 | 2.184 | 1.013 | passed |
| 8 | 3072 | 32768 | 0.2077 | b3_head_chunk (0.3847) | **1.853** | 1.888
| 1.870 | 1.853 | 2.723 | 1.003 | passed |
| 8 | 3072 | 65536 | 0.4897 | b1_ordinary (0.7506) | **1.533** | 1.533 |
1.562 | 1.587 | 2.151 | 1.004 | passed |
| 8 | 3072 | 131072 | 0.9334 | b1_ordinary (1.4632) | **1.568** | 1.568
| 1.624 | 1.634 | 2.176 | 0.995 | passed |
| 8 | 4096 | 4096 | 0.0764 | b2_whole_qkv (0.1034) | **1.354** | 1.656 |
1.354 | 1.767 | 2.301 | 1.010 | passed |
| 8 | 4096 | 8192 | 0.0973 | b2_whole_qkv (0.1589) | **1.633** | 1.816 |
1.633 | 1.957 | 2.770 | 1.006 | passed |
| 8 | 4096 | 16384 | 0.1501 | b2_whole_qkv (0.2962) | **1.974** | 1.992
| 1.974 | 2.045 | 2.707 | 1.003 | passed |
| 8 | 4096 | 32768 | 0.2626 | b1_ordinary (0.5501) | **2.095** | 2.095 |
2.123 | 2.165 | 2.925 | 1.003 | passed |
| 8 | 4096 | 65536 | 0.5316 | b1_ordinary (1.0699) | **2.013** | 2.013 |
2.070 | 2.128 | 2.804 | 1.004 | passed |
| 8 | 4096 | 131072 | 1.2471 | b1_ordinary (2.1127) | **1.694** | 1.694
| 1.759 | 1.796 | 2.361 | 0.972 | passed |
| 8 | 6144 | 4096 | 0.1040 | b2_whole_qkv (0.1508) | **1.450** | 1.614 |
1.450 | 1.752 | 2.045 | 1.002 | passed |
| 8 | 6144 | 8192 | 0.1606 | b2_whole_qkv (0.2690) | **1.674** | 1.727 |
1.674 | 1.803 | 2.462 | 1.001 | passed |
| 8 | 6144 | 16384 | 0.2857 | b2_whole_qkv (0.5035) | **1.762** | 1.779
| 1.762 | 1.837 | 2.418 | 0.996 | passed |
| 8 | 6144 | 32768 | 0.5848 | b1_ordinary (1.0169) | **1.739** | 1.739 |
1.758 | 1.777 | 2.269 | 1.001 | passed |
| 8 | 6144 | 65536 | 1.1923 | b1_ordinary (2.0150) | **1.690** | 1.690 |
1.737 | 1.756 | 2.278 | 0.999 | passed |
| 8 | 6144 | 131072 | 2.5867 | b1_ordinary (4.0127) | **1.551** | 1.551
| 1.594 | 1.642 | 2.125 | 0.992 | passed |
| 8 | 8192 | 4096 | 0.1600 | b2_whole_qkv (0.2190) | **1.369** | 1.479 |
1.369 | 1.556 | 1.925 | 0.995 | passed |
| 8 | 8192 | 8192 | 0.2816 | b1_ordinary (0.4186) | **1.487** | 1.487 |
1.487 | 1.522 | 1.872 | 0.994 | passed |
| 8 | 8192 | 16384 | 0.5217 | b1_ordinary (0.8115) | **1.555** | 1.555 |
1.570 | 1.579 | 1.971 | 1.001 | passed |
| 8 | 8192 | 32768 | 1.0612 | b1_ordinary (1.6270) | **1.533** | 1.533 |
1.565 | 1.589 | 2.004 | 1.002 | passed |
| 8 | 8192 | 65536 | 2.1338 | b1_ordinary (3.2717) | **1.533** | 1.533 |
1.602 | 1.585 | 2.102 | 1.003 | passed |
| 8 | 8192 | 131072 | 4.4942 | b1_ordinary (6.5455) | **1.456** | 1.456
| 1.502 | 1.538 | 1.981 | 0.990 | passed |
| 4 | 3072 | 4096 | 0.0625 | b2_whole_qkv (0.1032) | **1.651** | 2.015 |
1.651 | 2.135 | 2.649 | 1.014 | passed |
| 4 | 3072 | 8192 | 0.0979 | b2_whole_qkv (0.1930) | **1.972** | 2.115 |
1.972 | 2.127 | 3.295 | 1.009 | passed |
| 4 | 3072 | 16384 | 0.1581 | b2_whole_qkv (0.3838) | **2.428** | 2.461
| 2.428 | 2.508 | 3.362 | 1.008 | passed |
| 4 | 3072 | 32768 | 0.3457 | b1_ordinary (0.7429) | **2.149** | 2.149 |
2.182 | 2.170 | 2.981 | 1.001 | passed |
| 4 | 3072 | 65536 | 0.6498 | b1_ordinary (1.4519) | **2.235** | 2.235 |
2.302 | 2.362 | 3.095 | 0.990 | passed |
| 4 | 3072 | 131072 | 1.2447 | b1_ordinary (2.8625) | **2.300** | 2.300
| 2.391 | 2.446 | 3.171 | 0.994 | passed |
| 4 | 4096 | 4096 | 0.0935 | b2_whole_qkv (0.1466) | **1.568** | 1.780 |
1.568 | 1.898 | 2.367 | 0.999 | passed |
| 4 | 4096 | 8192 | 0.1487 | b3_head_chunk (0.2919) | **1.962** | 2.004
| 1.988 | 1.962 | 2.655 | 0.998 | passed |
| 4 | 4096 | 16384 | 0.2655 | b3_head_chunk (0.5553) | **2.092** | 2.104
| 2.141 | 2.092 | 2.858 | 0.998 | passed |
| 4 | 4096 | 32768 | 0.5099 | b1_ordinary (1.0895) | **2.137** | 2.137 |
2.195 | 2.242 | 2.917 | 1.002 | passed |
| 4 | 4096 | 65536 | 1.0766 | b1_ordinary (2.1625) | **2.009** | 2.009 |
2.083 | 2.112 | 2.731 | 0.989 | passed |
| 4 | 4096 | 131072 | 2.1058 | b1_ordinary (4.3467) | **2.064** | 2.064
| 2.136 | 2.165 | 2.786 | 0.996 | passed |
| 4 | 6144 | 4096 | 0.1532 | b2_whole_qkv (0.2551) | **1.665** | 1.757 |
1.665 | 1.768 | 2.226 | 0.999 | passed |
| 4 | 6144 | 8192 | 0.2858 | b3_head_chunk (0.5053) | **1.768** | 1.827
| 1.803 | 1.768 | 2.419 | 1.000 | passed |
| 4 | 6144 | 16384 | 0.5854 | b1_ordinary (1.0314) | **1.762** | 1.762 |
1.778 | 1.785 | 2.305 | 0.997 | passed |
| 4 | 6144 | 32768 | 1.1723 | b1_ordinary (2.0479) | **1.747** | 1.747 |
1.789 | 1.832 | 2.285 | 1.002 | passed |
| 4 | 6144 | 65536 | 2.4195 | b1_ordinary (4.1076) | **1.698** | 1.698 |
1.745 | 1.781 | 2.272 | 0.994 | passed |
| 4 | 6144 | 131072 | 4.7502 | b1_ordinary (8.2540) | **1.738** | 1.738
| 1.783 | 1.804 | 2.219 | 1.000 | passed |
| 4 | 8192 | 4096 | 0.2783 | b3_head_chunk (0.4127) | **1.483** | 1.509
| 1.498 | 1.483 | 1.851 | 0.996 | passed |
| 4 | 8192 | 8192 | 0.5229 | b3_head_chunk (0.8119) | **1.553** | 1.563
| 1.585 | 1.553 | 1.947 | 0.999 | passed |
| 4 | 8192 | 16384 | 1.0505 | b1_ordinary (1.6499) | **1.571** | 1.571 |
1.603 | 1.626 | 2.009 | 1.002 | passed |
| 4 | 8192 | 32768 | 2.0984 | b1_ordinary (3.3384) | **1.591** | 1.591 |
1.627 | 1.639 | 2.104 | 1.001 | passed |
| 4 | 8192 | 65536 | 4.2911 | b1_ordinary (6.7772) | **1.579** | 1.579 |
1.646 | 1.644 | 2.038 | 0.997 | passed |
| 4 | 8192 | 131072 | 8.6932 | b1_ordinary (13.2428) | **1.523** | 1.523
| 1.573 | 1.557 | 1.955 | 1.007 | passed |
| 2 | 3072 | 4096 | 0.0967 | b2_whole_qkv (0.1869) | **1.934** | 2.089 |
1.934 | 2.077 | 2.893 | 1.011 | passed |
| 2 | 3072 | 8192 | 0.1611 | b3_head_chunk (0.3646) | **2.263** | 2.365
| 2.340 | 2.263 | 3.204 | 0.992 | passed |
| 2 | 3072 | 16384 | 0.3166 | b1_ordinary (0.7318) | **2.312** | 2.312 |
2.348 | 2.362 | 3.227 | 0.995 | passed |
| 2 | 3072 | 32768 | 0.5981 | b1_ordinary (1.4294) | **2.390** | 2.390 |
2.458 | 2.539 | 3.329 | 0.986 | passed |
| 2 | 3072 | 65536 | 1.1529 | b1_ordinary (2.8307) | **2.455** | 2.455 |
2.551 | 2.616 | 3.274 | 0.996 | passed |
| 2 | 3072 | 131072 | 2.3088 | b1_ordinary (5.6412) | **2.443** | 2.443
| 2.588 | 2.635 | 3.321 | 0.997 | passed |
| 2 | 4096 | 4096 | 0.1427 | b3_head_chunk (0.2827) | **1.982** | 2.047
| 2.024 | 1.982 | 2.685 | 1.002 | passed |
| 2 | 4096 | 8192 | 0.2619 | b3_head_chunk (0.5413) | **2.067** | 2.097
| 2.128 | 2.067 | 2.861 | 0.999 | passed |
| 2 | 4096 | 16384 | 0.5069 | b1_ordinary (1.0679) | **2.107** | 2.107 |
2.172 | 2.204 | 2.864 | 0.998 | passed |
| 2 | 4096 | 32768 | 1.0264 | b1_ordinary (2.1198) | **2.065** | 2.065 |
2.148 | 2.184 | 2.817 | 0.996 | passed |
| 2 | 4096 | 65536 | 2.0520 | b1_ordinary (4.2868) | **2.089** | 2.089 |
2.164 | 2.203 | 2.754 | 0.996 | passed |
| 2 | 4096 | 131072 | 4.0855 | b1_ordinary (8.5864) | **2.102** | 2.102
| 2.201 | 2.221 | 2.807 | 0.998 | passed |
| 2 | 6144 | 4096 | 0.2770 | b3_head_chunk (0.4851) | **1.751** | 1.814
| 1.801 | 1.751 | 2.314 | 0.998 | passed |
| 2 | 6144 | 8192 | 0.5625 | b1_ordinary (1.0065) | **1.789** | 1.789 |
1.807 | 1.809 | 2.298 | 0.999 | passed |
| 2 | 6144 | 16384 | 1.1403 | b1_ordinary (2.0090) | **1.762** | 1.762 |
1.792 | 1.821 | 2.295 | 1.003 | passed |
| 2 | 6144 | 32768 | 2.2879 | b1_ordinary (4.0004) | **1.749** | 1.749 |
1.816 | 1.849 | 2.255 | 0.994 | passed |
| 2 | 6144 | 65536 | 4.6460 | b1_ordinary (8.0294) | **1.728** | 1.728 |
1.796 | 1.797 | 2.281 | 0.999 | passed |
| 2 | 6144 | 131072 | 9.1684 | — | 1.786 (invalid) | 1.850 | 1.807 |
1.786 | 2.224 | — | NOT PASSED (2 attempt(s)):
b2_whole_qkv.directional_disagreement;
b2_whole_qkv.directional_disagreement |
| 2 | 8192 | 4096 | 0.5100 | b3_head_chunk (0.7946) | **1.558** | 1.572
| 1.586 | 1.558 | 1.956 | 0.999 | passed |
| 2 | 8192 | 8192 | 1.0357 | b1_ordinary (1.6147) | **1.559** | 1.559 |
1.593 | 1.612 | 1.997 | 1.000 | passed |
| 2 | 8192 | 16384 | 2.0531 | b1_ordinary (3.2427) | **1.579** | 1.579 |
1.622 | 1.652 | 2.078 | 1.002 | passed |
| 2 | 8192 | 32768 | 4.1375 | b1_ordinary (6.5602) | **1.586** | 1.586 |
1.645 | 1.659 | 2.030 | 0.995 | passed |
| 2 | 8192 | 65536 | 8.4833 | b1_ordinary (13.4177) | **1.582** | 1.582
| 1.619 | 1.677 | 2.073 | 1.006 | passed |
| 2 | 8192 | 131072 | 16.7115 | — | 1.557 (invalid) | 1.557 | 1.654 |
1.685 | 1.999 | — | NOT PASSED (2 attempt(s)): directional_disagreement;
b2_whole_qkv.directional_disagreement;
b3_head_chunk.directional_disagreement;
b2_whole_qkv.directional_disagreement;
b3_head_chunk.directional_disagreement |

**H100 (SM90): final.**

| | this PR | #6516 (the H100 receipts kept by #6537) |
|---|---|---|
| valid perf rows | 70 of 71 measurable (all 70 above 1.00) | 70 of 71 |
| geomean (W = 8 / W = 4 / W = 2) | 1.388 (1.372 / 1.410 / 1.382) |
1.387 (1.366 / 1.404 / 1.393) |
| minimum | 1.147 (W = 4, 8192 × 131072) | 1.152 (W = 4, 8192 × 131072)
|
| perf exceptions | 1 | 1 |

The protocol lists 72 perf rows per architecture. On H100 the W = 2,
8192 × 131072 row needs 71.4 GB per rank and does not fit in the 66.4 GB
available on an 80 GB H100. It is recorded as not measurable and is not
counted, as in #6516.

Correctness rows: 13 of 13 have a passing receipt.

The receipts come from three sealed snapshots on three H100 nodes:

- snapshot 1 (first node): all 28 W = 2 rows, 20 of the 28 W = 4 rows
and 13 of the 28 W = 8 rows; 61 receipts, 61 passed
- snapshot 2 (second node): the remaining 8 W = 4 and 15 W = 8 rows,
measured with the snapshot-1 receipts as priors; 23 receipts, 22 passed
- snapshot 3 (third node): the one row without a passing receipt,
re-measured with the snapshot-1 and snapshot-2 receipts as priors; 1
receipt, 0 passed

When a row has more than one receipt, its passing receipt is the row of
record.

Rows without a valid receipt on H100:

- `perf_w8_h8192_s131072` (perf): invalid on two nodes.
- Snapshot-2 node: b2 directional disagreement (raw speedup 1.248,
loaded clock 0.894).
- Snapshot-3 node: b2 directional disagreement (raw speedup 1.243,
loaded clock 0.924).
- The same failure class on two nodes; no further attempt was made. In
#6516 this row was valid (1.228).
- `perf_w2_h8192_s131072` (perf): not measurable on 80 GB (above); no
receipt, as in #6516.

Rows whose status changed relative to #6516:

- `perf_w2_h8192_s65536`: invalid in #6516, valid here (1.181).
- `perf_w8_h8192_s131072`: valid in #6516 (1.228), invalid here (above).

A row-by-row comparison with the #6516 H100 receipts covered the 69 rows
that are valid in both. The runs used different nodes and sessions, and
the #6516 receipts were not re-run on this node, so the comparison is
informational only:

- median +0.20 %
- range from −9.6 % (`perf_w8_h3072_s131072`) to +15.2 %
(`perf_w8_h3072_s4096`)
- 43 rows faster, 26 slower

The export table measures the defaults against the four baselines, not
against the opted-out plan. The same-node, same-process OFF → default
pairs above are the evidence for the defaults.

#### sm_90a: export receipts per row

| W | hidden | S_global | export ms | fastest baseline (ms) | speedup |
B1 | B2 | B3 | B4 | source/export | status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 8 | 3072 | 4096 | 0.0933 | b2_whole_qkv (0.1379) | **1.478** | 1.977 |
1.478 | 1.879 | 1.698 | 1.000 | passed |
| 8 | 3072 | 8192 | 0.1498 | b2_whole_qkv (0.2099) | **1.401** | 1.744 |
1.401 | 1.623 | 1.671 | 0.991 | passed |
| 8 | 3072 | 16384 | 0.2625 | b2_whole_qkv (0.3780) | **1.440** | 1.763
| 1.440 | 1.610 | 1.785 | 1.003 | passed |
| 8 | 3072 | 32768 | 0.5110 | b2_whole_qkv (0.7311) | **1.431** | 1.704
| 1.431 | 1.561 | 1.775 | 0.999 | passed |
| 8 | 3072 | 65536 | 1.1002 | b2_whole_qkv (1.4291) | **1.299** | 1.481
| 1.299 | 1.353 | 1.611 | 1.000 | passed |
| 8 | 3072 | 131072 | 2.3857 | b2_whole_qkv (2.8253) | **1.184** | 1.326
| 1.184 | 1.208 | 1.470 | 0.996 | passed |
| 8 | 4096 | 4096 | 0.1321 | b2_whole_qkv (0.1656) | **1.254** | 1.607 |
1.254 | 1.521 | 1.452 | 1.005 | passed |
| 8 | 4096 | 8192 | 0.2001 | b2_whole_qkv (0.3067) | **1.532** | 1.897 |
1.532 | 1.772 | 1.821 | 1.003 | passed |
| 8 | 4096 | 16384 | 0.3697 | b2_whole_qkv (0.5700) | **1.542** | 1.845
| 1.542 | 1.698 | 1.865 | 1.004 | passed |
| 8 | 4096 | 32768 | 0.7111 | b2_whole_qkv (1.0980) | **1.544** | 1.768
| 1.544 | 1.626 | 1.874 | 0.999 | passed |
| 8 | 4096 | 65536 | 1.4108 | b2_whole_qkv (2.1663) | **1.536** | 1.706
| 1.536 | 1.570 | 1.867 | 0.998 | passed |
| 8 | 4096 | 131072 | 2.7934 | b2_whole_qkv (4.2863) | **1.534** | 1.705
| 1.534 | 1.558 | 1.881 | 0.999 | passed |
| 8 | 6144 | 4096 | 0.2471 | b2_whole_qkv (0.2891) | **1.170** | 1.377 |
1.170 | 1.313 | 1.333 | 1.001 | passed |
| 8 | 6144 | 8192 | 0.4049 | b2_whole_qkv (0.5334) | **1.318** | 1.527 |
1.318 | 1.437 | 1.541 | 1.001 | passed |
| 8 | 6144 | 16384 | 0.7304 | b2_whole_qkv (1.0396) | **1.423** | 1.606
| 1.423 | 1.500 | 1.667 | 0.999 | passed |
| 8 | 6144 | 32768 | 1.5016 | b2_whole_qkv (2.0575) | **1.370** | 1.508
| 1.370 | 1.407 | 1.624 | 0.996 | passed |
| 8 | 6144 | 65536 | 3.0582 | b2_whole_qkv (4.0899) | **1.337** | 1.477
| 1.337 | 1.368 | 1.617 | 0.999 | passed |
| 8 | 6144 | 131072 | 6.0603 | b2_whole_qkv (8.4173) | **1.389** | 1.494
| 1.389 | 1.419 | 1.622 | 1.000 | passed |
| 8 | 8192 | 4096 | 0.3332 | b2_whole_qkv (0.4303) | **1.292** | 1.479 |
1.292 | 1.412 | 1.466 | 1.005 | passed |
| 8 | 8192 | 8192 | 0.6396 | b2_whole_qkv (0.8284) | **1.295** | 1.472 |
1.295 | 1.382 | 1.493 | 1.000 | passed |
| 8 | 8192 | 16384 | 1.2753 | b2_whole_qkv (1.6613) | **1.303** | 1.433
| 1.303 | 1.348 | 1.499 | 1.004 | passed |
| 8 | 8192 | 32768 | 2.6143 | b2_whole_qkv (3.3751) | **1.291** | 1.413
| 1.291 | 1.331 | 1.497 | 1.001 | passed |
| 8 | 8192 | 65536 | 5.2409 | b2_whole_qkv (6.8203) | **1.301** | 1.385
| 1.301 | 1.306 | 1.492 | 1.000 | passed |
| 8 | 8192 | 131072 | 10.4852 | — | 1.243 (invalid) | 1.375 | 1.243 |
1.354 | 1.526 | — | NOT PASSED (2 attempt(s)):
b2_whole_qkv.directional_disagreement;
b2_whole_qkv.directional_disagreement |
| 4 | 3072 | 4096 | 0.1455 | b2_whole_qkv (0.2018) | **1.387** | 1.743 |
1.387 | 1.627 | 1.657 | 1.002 | passed |
| 4 | 3072 | 8192 | 0.2368 | b2_whole_qkv (0.3740) | **1.579** | 1.963 |
1.579 | 1.798 | 1.966 | 1.014 | passed |
| 4 | 3072 | 16384 | 0.4382 | b2_whole_qkv (0.6957) | **1.587** | 1.901
| 1.587 | 1.719 | 1.989 | 1.001 | passed |
| 4 | 3072 | 32768 | 0.8566 | b2_whole_qkv (1.3635) | **1.592** | 1.840
| 1.592 | 1.665 | 1.996 | 1.000 | passed |
| 4 | 3072 | 65536 | 1.6385 | b2_whole_qkv (2.6903) | **1.642** | 1.864
| 1.642 | 1.688 | 2.071 | 0.999 | passed |
| 4 | 3072 | 131072 | 3.2463 | b2_whole_qkv (5.2450) | **1.616** | 1.842
| 1.616 | 1.655 | 2.065 | 1.003 | passed |
| 4 | 4096 | 4096 | 0.1865 | b2_whole_qkv (0.2851) | **1.529** | 1.874 |
1.529 | 1.751 | 1.838 | 1.001 | passed |
| 4 | 4096 | 8192 | 0.3557 | b2_whole_qkv (0.5418) | **1.523** | 1.850 |
1.523 | 1.690 | 1.857 | 1.001 | passed |
| 4 | 4096 | 16384 | 0.7017 | b2_whole_qkv (1.0503) | **1.497** | 1.734
| 1.497 | 1.589 | 1.834 | 0.999 | passed |
| 4 | 4096 | 32768 | 1.3800 | b2_whole_qkv (2.0685) | **1.499** | 1.697
| 1.499 | 1.553 | 1.842 | 1.003 | passed |
| 4 | 4096 | 65536 | 2.7165 | b2_whole_qkv (4.0992) | **1.509** | 1.691
| 1.509 | 1.545 | 1.861 | 0.999 | passed |
| 4 | 4096 | 131072 | 5.4554 | b2_whole_qkv (8.0964) | **1.484** | 1.682
| 1.484 | 1.525 | 1.880 | 0.999 | passed |
| 4 | 6144 | 4096 | 0.3898 | b2_whole_qkv (0.5297) | **1.359** | 1.597 |
1.359 | 1.498 | 1.595 | 1.002 | passed |
| 4 | 6144 | 8192 | 0.7305 | b2_whole_qkv (1.0016) | **1.371** | 1.567 |
1.371 | 1.473 | 1.623 | 0.999 | passed |
| 4 | 6144 | 16384 | 1.4498 | b2_whole_qkv (1.9875) | **1.371** | 1.529
| 1.371 | 1.422 | 1.623 | 1.000 | passed |
| 4 | 6144 | 32768 | 2.8979 | b2_whole_qkv (3.9512) | **1.363** | 1.510
| 1.363 | 1.399 | 1.623 | 1.004 | passed |
| 4 | 6144 | 65536 | 5.7126 | b2_whole_qkv (8.0290) | **1.405** | 1.545
| 1.405 | 1.443 | 1.684 | 1.004 | passed |
| 4 | 6144 | 131072 | 12.4498 | b2_whole_qkv (15.5355) | **1.248** |
1.354 | 1.248 | 1.271 | 1.477 | 0.994 | passed |
| 4 | 8192 | 4096 | 0.6347 | b2_whole_qkv (0.8120) | **1.279** | 1.458 |
1.279 | 1.362 | 1.475 | 0.997 | passed |
| 4 | 8192 | 8192 | 1.2598 | b2_whole_qkv (1.6016) | **1.271** | 1.412 |
1.271 | 1.325 | 1.472 | 0.997 | passed |
| 4 | 8192 | 16384 | 2.5499 | b2_whole_qkv (3.2604) | **1.279** | 1.422
| 1.279 | 1.337 | 1.487 | 0.999 | passed |
| 4 | 8192 | 32768 | 5.1004 | b2_whole_qkv (6.6148) | **1.297** | 1.401
| 1.297 | 1.317 | 1.503 | 1.005 | passed |
| 4 | 8192 | 65536 | 10.7802 | b2_whole_qkv (12.7660) | **1.184** |
1.276 | 1.184 | 1.209 | 1.387 | 0.993 | passed |
| 4 | 8192 | 131072 | 22.4824 | b2_whole_qkv (25.7869) | **1.147** |
1.275 | 1.147 | 1.159 | 1.339 | 0.974 | passed |
| 2 | 3072 | 4096 | 0.2278 | b2_whole_qkv (0.3315) | **1.455** | 1.853 |
1.455 | 1.676 | 1.852 | 1.002 | passed |
| 2 | 3072 | 8192 | 0.4194 | b2_whole_qkv (0.6423) | **1.532** | 1.837 |
1.532 | 1.671 | 1.948 | 0.998 | passed |
| 2 | 3072 | 16384 | 0.8216 | b2_whole_qkv (1.2629) | **1.537** | 1.778
| 1.537 | 1.610 | 1.959 | 0.999 | passed |
| 2 | 3072 | 32768 | 1.6064 | b2_whole_qkv (2.5087) | **1.562** | 1.791
| 1.562 | 1.607 | 2.004 | 1.001 | passed |
| 2 | 3072 | 65536 | 3.1929 | b2_whole_qkv (4.8122) | **1.507** | 1.767
| 1.507 | 1.585 | 1.960 | 1.002 | passed |
| 2 | 3072 | 131072 | 6.4054 | b2_whole_qkv (9.6060) | **1.500** | 1.756
| 1.500 | 1.553 | 1.967 | 1.002 | passed |
| 2 | 4096 | 4096 | 0.3408 | b2_whole_qkv (0.4953) | **1.453** | 1.783 |
1.453 | 1.601 | 1.805 | 0.999 | passed |
| 2 | 4096 | 8192 | 0.6749 | b2_whole_qkv (0.9833) | **1.457** | 1.676 |
1.457 | 1.533 | 1.803 | 1.000 | passed |
| 2 | 4096 | 16384 | 1.3490 | b2_whole_qkv (1.9428) | **1.440** | 1.640
| 1.440 | 1.496 | 1.797 | 1.001 | passed |
| 2 | 4096 | 32768 | 2.6418 | b2_whole_qkv (3.8867) | **1.471** | 1.654
| 1.471 | 1.504 | 1.841 | 1.002 | passed |
| 2 | 4096 | 65536 | 5.2645 | b2_whole_qkv (7.6549) | **1.454** | 1.648
| 1.454 | 1.522 | 1.804 | 1.000 | passed |
| 2 | 4096 | 131072 | 10.5467 | b3_head_chunk (15.4342) | **1.463** |
1.702 | 1.491 | 1.463 | 1.842 | 1.006 | passed |
| 2 | 6144 | 4096 | 0.7290 | b2_whole_qkv (0.9459) | **1.297** | 1.477 |
1.297 | 1.381 | 1.549 | 0.998 | passed |
| 2 | 6144 | 8192 | 1.4714 | b2_whole_qkv (1.8952) | **1.288** | 1.437 |
1.288 | 1.328 | 1.542 | 0.997 | passed |
| 2 | 6144 | 16384 | 2.9214 | b2_whole_qkv (3.8628) | **1.322** | 1.432
| 1.322 | 1.349 | 1.567 | 1.004 | passed |
| 2 | 6144 | 32768 | 5.6981 | b2_whole_qkv (7.8316) | **1.374** | 1.556
| 1.374 | 1.397 | 1.606 | 0.999 | passed |
| 2 | 6144 | 65536 | 11.4624 | b3_head_chunk (14.9578) | **1.305** |
1.517 | 1.393 | 1.305 | 1.574 | 1.004 | passed |
| 2 | 6144 | 131072 | 24.1508 | b2_whole_qkv (29.9326) | **1.239** |
1.366 | 1.239 | 1.281 | 1.464 | 1.007 | passed |
| 2 | 8192 | 4096 | 1.2445 | b2_whole_qkv (1.5433) | **1.240** | 1.374 |
1.240 | 1.287 | 1.443 | 1.000 | passed |
| 2 | 8192 | 8192 | 2.5120 | b2_whole_qkv (3.1892) | **1.270** | 1.389 |
1.270 | 1.291 | 1.483 | 1.001 | passed |
| 2 | 8192 | 16384 | 5.0104 | b2_whole_qkv (6.3981) | **1.277** | 1.381
| 1.277 | 1.302 | 1.491 | 0.998 | passed |
| 2 | 8192 | 32768 | 9.7752 | b2_whole_qkv (12.4075) | **1.269** | 1.479
| 1.269 | 1.331 | 1.520 | 1.025 | passed |
| 2 | 8192 | 65536 | 21.4285 | b3_head_chunk (25.3121) | **1.181** |
1.263 | 1.185 | 1.181 | 1.361 | 0.991 | passed |
| 2 | 8192 | 131072 | — | — | — | — | — | — | — | — | NOT PASSED (0
attempt(s)): no receipt |

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added configurable folded-barrier launches, producer variants, group
scaling, and row-count gates for QKV exchange sessions, with
architecture- and world-size-based defaults.
* Session descriptions now report resolved settings, launch sequences,
and prepared row plans.
* Added support for additional optimized QKV normalization and
rotary-embedding exchange paths across GPU architectures.
* **Documentation**
* Documented the new session options, defaults, constraints, and
benchmark behavior.
* **Benchmarking**
* Improved timing and per-tensor correctness reporting for exchange
comparisons.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9bd7f7e](https://github.com/flashinfer-ai/flashinfer/commit/9bd7f7e4271e7d2d98c7e750f39f23778c4fa014)

- **作者**: Julian
- **时间**: 2026-10-19T10:04:28Z
- **提交信息**: test(sampling): add seeded correctness fuzz coverage (#5341)

## 📌 Description

Add seeded correctness tests for probability sampling, top-k, top-p and
both combined filtering orders. Cases cover scalar/per-request
thresholds, int32/int64 indices, row remapping and RNG replay. No kernel
or API changes.

An independent float64 reference checks legal support, including ties
and top-p rounding boundaries. Frozen distributions also check
probability mass with a chi-square and effect-size gate. CPU tests cover
the reference, case generator and statistics.

Replay a failure with `FLASHINFER_SAMPLING_FUZZ_ONLY_SEED`; adjust
coverage with `FLASHINFER_SAMPLING_FUZZ_NUM_CASES` and
`FLASHINFER_SAMPLING_FUZZ_SEED`. The suite is registered in the JIT
sampling test task.

## 🔍 Related Issues

Part of #3605. Depends on #5348: the int64 cases expose #5347 without
that fix. #5340 is already merged; the remaining order is **#5348 → this
PR**.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

GPU validation on October 6 (RTX 4090 D, CUDA 12.8, torch 2.9.1):

- With #5348 applied: 455 passed, no xfails.
- Without #5348: the row-remapping probe passes for int32 and fails for
int64.

The October 13 cleanup changes comments/docstrings only; executable AST
is unchanged. CPU checks: 62 passed, 393 CUDA skips. Ruff and `git diff
--check` passed. GPU tests were not rerun for this cleanup.

## Reviewer Notes

The top-k tie semantics and top-p float32 allowance are the main
reference choices to review.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Expanded sampling coverage across probability sampling, top-k, top-p,
and combined filtering.
* Added seeded fuzz tests for reproducibility, generator replay,
supported results, and output validity across index types and
per-request thresholds.
* Added independent reference checks for filtering boundaries and top-k
ties.
* Added statistical distribution checks, including safeguards for
invalid inputs and insufficient expected counts.
* CPU tests cover reference behavior and validation; CUDA-specific
sampling checks remain conditional.
* Included the expanded sampling tests in the relevant test execution
workflow.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: JulianZJN <148066842+JulianZJN@users.noreply.github.com>
Co-authored-by: Yang Xu <38851819+YangXu1990uiuc@users.noreply.github.com>

### [261e2f9](https://github.com/flashinfer-ai/flashinfer/commit/261e2f9c60cad967001a355f493b8311e12a59d3)

- **作者**: 0z5a
- **时间**: 2026-10-19T10:04:24Z
- **提交信息**: test: cover RMSNorm caller-owned output contracts (#4994)

**Incremental review:** [Files
changed](https://github.com/flashinfer-ai/flashinfer/pull/4994/files)
against `main`.

<!-- .github/pull_request_template.md -->

## Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Add 80 parameterized RMSNorm output-buffer contract cases to the
existing `tests/utils/test_norm.py` CI entry point.

The tests cover FP16/BF16, 2D/3D shapes, dense/padded row storage, and
zero/tiny/sparse/alternating/large finite inputs. They check
caller-supplied output identity, complete overwrite of NaN and finite
poison, input/weight preservation, output-padding guards, finite outputs
and agreement with the existing FP32 reference after synchronization.

This is test-only correctness coverage. No production kernel, dispatch,
dependency or tolerance is changed, and no existing kernel defect or
performance improvement is claimed.

## Related Issues

<!-- Link any related issues here -->

Related to #3605. @YangXu1990uiuc [confirmed the bounded RMSNorm slice
was
available](https://github.com/flashinfer-ai/flashinfer/issues/3605#issuecomment-5564614029)
and [recorded the Norm/RoPE stream
direction](https://github.com/flashinfer-ai/flashinfer/issues/3605#issuecomment-5564708820).
This PR is only the first, 80-case RMSNorm output-contract slice; it
does not close the whole quality RFC or add RoPE/quantized-norm
coverage. GPU evidence is in the [updated collaboration
comment](https://github.com/flashinfer-ai/flashinfer/issues/3605#issuecomment-5561845889).

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

Full-repository hooks passed, including mypy, Ruff, clang-format and the
experimental-scope self-test. The hook-installation checkbox is left
unchecked because only the manual full run is verified here. `git diff
--check` also passed.

## Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

The new 80-case selection passed on an NVIDIA L20 (SM 8.9) through
**each actual dispatch path**, CuTe and forced CUDA: 80 passed, zero
failures/errors/skips per run. These are 80 distinct cases exercised
twice, not 160 different contracts. The entire library test suite was
not run, so the broad all-tests checkbox remains unchecked.

```sh
FLASHINFER_USE_CUDA_NORM=0 python -m pytest tests/utils/test_norm.py -k test_rmsnorm_output_contract -q
FLASHINFER_USE_CUDA_NORM=1 python -m pytest tests/utils/test_norm.py -k test_rmsnorm_output_contract -q
```

Base: `6c14bbd5ff34210404d5d4b5f6ff3b4b2527f59f`; tested patch:
`92da53c4c4b9a2a5d261650b401dd891904ba0b5`.
Environment: Torch 2.13.0+cu130, CUDA 13.0, CUTLASS DSL 4.6.2, TVM FFI
0.1.11, pytest 9.1.1. Before both runs, all 6,991 source/header manifest
entries were checked and the actual backend selection was asserted.
Results and boundaries are summarized in the linked issue comment.

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
# tests/experimental/test_my_backend.py
# tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->

Please focus on the public output/storage contract and whether the
finite edge-input patterns add useful coverage to the existing norm
suite. Validation covers one GPU architecture; no PDL or performance
conclusion is intended.

AI-assisted test implementation, disclosed in the commit. Upstream
maintainer review/CI remains pending.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Tests**
- Added checks that RMS normalization produces repeatable, finite
results across edge-value inputs and padded storage layouts, while
preserving inputs, padding sentinels, and output-buffer behavior.
- Fused normalization tests now skip cases when the device’s per-block
shared-memory limit is insufficient, improving compatibility with
devices that have lower limits.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: 0z5a <0z5a@users.noreply.github.com>
Signed-off-by: 0z5a <dezhen.lu@student.uni-tuebingen.de>
Co-authored-by: 0z5a <0z5a@users.noreply.github.com>

### [5ed7fd1](https://github.com/flashinfer-ai/flashinfer/commit/5ed7fd1c2d82a5eee703b521047135d145caafdb)

- **作者**: eigen
- **时间**: 2026-10-19T09:26:26Z
- **提交信息**: feat(cake_comm): NVFP4-transport tensor-parallel all-reduce (TP2 one-shot, TP4 two-shot) with a fused residual + RMSNorm epilogue (SM100 / SM103 / SM107) (#6500)

This PR delivers the Cake kernels for all eight variants of the
NVFP4-transport tensor-parallel all-reduce in
`flashinfer.comm.cake_fp4_allreduce` (`cake_fp4_allreduce`,
`cake_fp4_allreduce_nvfp4`, `cake_fp4_allreduce_rmsnorm`,
`cake_fp4_allreduce_rmsnorm_nvfp4`, workspace
`CakeFp4AllReduceWorkspace`) for hidden size 6144 and 1024–16384 rows:
TP2 one-shot and TP4 two-shot all-reduce, each with BF16 or
pre-quantised NVFP4 input and BF16 output, and TP2 all-reduce + residual
+ Gemma RMSNorm as BF16→BF16, NVFP4→BF16, BF16→NVFP4 and BF16→MXFP8
(swizzled `fp4_quantize` and `mxfp8_quantize` layouts). Ranks exchange
rows over NVLink as NVFP4 records (E2M1 values, E4M3 block scales, one
FP32 row scale), decoded in rank order. As this is the family's first
Cake version, the baseline is Fan Shi's reference implementation,
https://github.com/fans-nv/fp4-all-reduce at commit 2878bf5 (its own
kernels built from that commit), which writes the quantised RMSNorm
outputs in a linear rather than swizzled layout. Latencies are per-call
GPU time in µs for CUDA graphs of 10 back-to-back calls (CUPTI kernel
spans, maximum over ranks, median of three interleaved A/B/B/A blocks)
in two independent runs, both implementations on the same GPUs of one
node; lower is better, and speedup = baseline time / Cake time.
Averaging each shape's two runs, the geometric-mean speedup over the 40
shapes is 1.079 on GB200, 1.075 on GB300 and 1.086 on SM107; every shape
is faster in both runs on GB200 and GB300, and 38 of the 40 on SM107,
where the TP4 two-shot all-reduce with NVFP4 in / BF16 out at 8192 rows
(0.986) and the fused RMSNorm with NVFP4 in / BF16 out at 2048 rows
(0.999) are not. The smallest speedups among the faster shapes are 1.004
(GB200, TP2 one-shot all-reduce, NVFP4 in / BF16 out, 16384 rows), 1.008
(GB300, fused RMSNorm, BF16 in / BF16 out, 1024 rows) and 1.008 (SM107,
TP2 one-shot all-reduce, BF16 in / BF16 out, 8192 rows); the largest
1.283 (GB200, fused RMSNorm, NVFP4 in / BF16 out, 1024 rows), 1.277
(GB300, fused RMSNorm, NVFP4 in / BF16 out, 1024 rows) and 1.271 (SM107,
fused RMSNorm, BF16 in / MXFP8 out, 8192 rows).

### `sm_100a`

**`sm_100a`: NVIDIA GB200 (sm_100a, 152 SMs; NVL72 node nvl72139-T18; 2
GPUs for world size 2, 4 GPUs for world size 4), CUDA 13.4**

| Shape (hidden 6144) | Baseline µs (run 1 / run 2) | Cake µs (run 1 /
run 2) | Speedup = baseline / Cake (run 1 / run 2) |
|---|---|---|---|
| TP2 one-shot all-reduce, BF16 in / BF16 out, 1024 rows | 13.63 / 13.64
| 13.03 / 13.04 | 1.046 / 1.046 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 2048 rows | 20.00 / 20.04
| 18.87 / 18.90 | 1.060 / 1.060 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 4096 rows | 33.55 / 33.58
| 32.00 / 32.00 | 1.049 / 1.049 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 8192 rows | 57.56 / 57.48
| 57.29 / 57.15 | 1.005 / 1.006 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 16384 rows | 105.05 /
105.14 | 102.01 / 101.87 | 1.030 / 1.032 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 1024 rows | 10.97 /
10.98 | 10.82 / 10.83 | 1.013 / 1.014 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 2048 rows | 16.25 /
16.22 | 15.98 / 16.00 | 1.017 / 1.014 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 4096 rows | 27.79 /
27.78 | 27.47 / 27.45 | 1.012 / 1.012 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 8192 rows | 51.74 /
51.67 | 50.89 / 50.86 | 1.017 / 1.016 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 16384 rows | 94.33 /
94.46 | 93.98 / 94.00 | 1.004 / 1.005 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 1024 rows | 22.87 / 22.87
| 21.05 / 21.06 | 1.087 / 1.086 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 2048 rows | 32.39 / 32.39
| 29.64 / 29.65 | 1.093 / 1.093 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 4096 rows | 52.46 / 52.43
| 48.73 / 48.79 | 1.076 / 1.075 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 8192 rows | 94.43 / 94.46
| 86.85 / 86.87 | 1.087 / 1.087 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 16384 rows | 169.76 /
169.72 | 163.74 / 163.84 | 1.037 / 1.036 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 1024 rows | 19.06 /
19.06 | 18.86 / 18.84 | 1.011 / 1.012 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 2048 rows | 27.70 /
27.71 | 25.81 / 25.83 | 1.073 / 1.073 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 4096 rows | 46.24 /
46.23 | 44.23 / 44.22 | 1.045 / 1.045 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 8192 rows | 88.23 /
88.32 | 84.29 / 84.26 | 1.047 / 1.048 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 16384 rows | 157.30 /
157.36 | 154.27 / 154.34 | 1.020 / 1.020 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 1024 rows |
19.98 / 19.99 | 19.06 / 19.07 | 1.049 / 1.048 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 2048 rows |
31.51 / 31.54 | 30.30 / 30.28 | 1.040 / 1.042 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 4096 rows |
54.08 / 54.10 | 50.84 / 50.82 | 1.064 / 1.065 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 8192 rows |
101.64 / 101.78 | 91.42 / 91.38 | 1.112 / 1.114 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 16384 rows |
187.68 / 187.68 | 169.34 / 169.30 | 1.108 / 1.109 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 1024 rows |
21.52 / 21.52 | 16.77 / 16.81 | 1.283 / 1.280 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 2048 rows |
31.84 / 31.83 | 29.76 / 29.71 | 1.070 / 1.071 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 4096 rows |
47.77 / 47.74 | 46.38 / 46.41 | 1.030 / 1.029 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 8192 rows |
82.82 / 82.76 | 76.88 / 76.90 | 1.077 / 1.076 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 16384 rows |
157.81 / 157.87 | 142.21 / 142.16 | 1.110 / 1.110 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 1024 rows |
21.17 / 21.15 | 19.42 / 19.43 | 1.091 / 1.089 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 2048 rows |
33.60 / 33.62 | 31.38 / 31.38 | 1.071 / 1.071 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 4096 rows |
60.57 / 60.57 | 51.90 / 51.94 | 1.167 / 1.166 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 8192 rows |
112.56 / 112.69 | 95.79 / 95.81 | 1.175 / 1.176 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 16384 rows |
210.72 / 210.74 | 178.80 / 178.84 | 1.178 / 1.178 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 1024 rows |
21.07 / 21.12 | 19.32 / 19.32 | 1.090 / 1.093 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 2048 rows |
34.51 / 34.51 | 31.32 / 31.36 | 1.102 / 1.100 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 4096 rows |
60.60 / 60.59 | 51.62 / 51.65 | 1.174 / 1.173 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 8192 rows |
114.04 / 114.21 | 94.94 / 94.87 | 1.201 / 1.204 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 16384 rows |
213.32 / 213.51 | 177.13 / 177.31 | 1.204 / 1.204 |

Geometric-mean speedup over the 40 rows: 1.079 (run 1) / 1.079 (run 2);
rows faster than the baseline in both runs: 40 of 40.

### `sm_103a`

**`sm_103a`: NVIDIA GB300 (NVL72 node; 2 GPUs for world size 2, 4 GPUs
for world size 4), CUDA 13.4**

| Shape (hidden 6144) | Baseline µs (run 1 / run 2) | Cake µs (run 1 /
run 2) | Speedup = baseline / Cake (run 1 / run 2) |
|---|---|---|---|
| TP2 one-shot all-reduce, BF16 in / BF16 out, 1024 rows | 13.46 / 13.46
| 12.99 / 12.99 | 1.036 / 1.036 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 2048 rows | 19.72 / 19.78
| 18.74 / 18.77 | 1.053 / 1.054 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 4096 rows | 33.92 / 33.90
| 32.16 / 32.21 | 1.054 / 1.052 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 8192 rows | 58.60 / 58.60
| 57.40 / 57.38 | 1.021 / 1.021 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 16384 rows | 107.09 /
107.36 | 103.92 / 103.87 | 1.030 / 1.034 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 1024 rows | 10.84 /
10.81 | 10.68 / 10.67 | 1.015 / 1.013 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 2048 rows | 16.10 /
16.10 | 15.80 / 15.80 | 1.019 / 1.019 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 4096 rows | 27.61 /
27.62 | 27.23 / 27.18 | 1.014 / 1.016 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 8192 rows | 50.51 /
50.47 | 49.46 / 49.41 | 1.021 / 1.021 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 16384 rows | 96.50 /
96.48 | 95.50 / 95.62 | 1.010 / 1.009 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 1024 rows | 22.58 / 22.57
| 20.89 / 20.89 | 1.081 / 1.081 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 2048 rows | 32.12 / 32.09
| 29.51 / 29.52 | 1.089 / 1.087 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 4096 rows | 51.97 / 52.00
| 48.43 / 48.31 | 1.073 / 1.076 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 8192 rows | 93.74 / 93.84
| 86.54 / 86.47 | 1.083 / 1.085 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 16384 rows | 167.89 /
167.90 | 163.79 / 163.84 | 1.025 / 1.025 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 1024 rows | 18.83 /
18.84 | 18.64 / 18.64 | 1.010 / 1.011 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 2048 rows | 27.42 /
27.44 | 25.90 / 25.89 | 1.059 / 1.060 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 4096 rows | 45.73 /
45.72 | 44.06 / 44.07 | 1.038 / 1.037 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 8192 rows | 87.41 /
87.48 | 83.05 / 83.08 | 1.053 / 1.053 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 16384 rows | 155.80 /
155.81 | 153.56 / 153.61 | 1.015 / 1.014 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 1024 rows |
19.49 / 19.52 | 19.31 / 19.37 | 1.009 / 1.008 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 2048 rows |
31.28 / 31.29 | 30.40 / 30.38 | 1.029 / 1.030 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 4096 rows |
53.61 / 53.60 | 50.62 / 50.65 | 1.059 / 1.058 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 8192 rows |
100.88 / 100.94 | 90.20 / 90.29 | 1.118 / 1.118 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 16384 rows |
187.02 / 187.18 | 166.55 / 166.66 | 1.123 / 1.123 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 1024 rows |
21.12 / 21.12 | 16.53 / 16.54 | 1.277 / 1.277 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 2048 rows |
31.38 / 31.35 | 29.29 / 29.21 | 1.071 / 1.073 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 4096 rows |
46.84 / 46.86 | 45.71 / 45.76 | 1.025 / 1.024 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 8192 rows |
81.32 / 81.25 | 76.71 / 76.75 | 1.060 / 1.059 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 16384 rows |
154.43 / 154.53 | 140.50 / 140.47 | 1.099 / 1.100 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 1024 rows |
20.72 / 20.73 | 19.38 / 19.39 | 1.069 / 1.069 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 2048 rows |
33.15 / 33.13 | 31.32 / 31.34 | 1.059 / 1.057 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 4096 rows |
60.44 / 60.33 | 52.15 / 52.19 | 1.159 / 1.156 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 8192 rows |
112.24 / 112.38 | 94.90 / 94.94 | 1.183 / 1.184 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 16384 rows |
209.11 / 208.99 | 176.51 / 176.48 | 1.185 / 1.184 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 1024 rows |
20.69 / 20.69 | 19.35 / 19.32 | 1.069 / 1.071 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 2048 rows |
33.87 / 33.90 | 31.00 / 31.06 | 1.092 / 1.091 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 4096 rows |
60.08 / 60.10 | 51.52 / 51.51 | 1.166 / 1.167 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 8192 rows |
112.99 / 113.01 | 93.71 / 93.62 | 1.206 / 1.207 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 16384 rows |
210.88 / 210.80 | 173.95 / 174.02 | 1.212 / 1.211 |

Geometric-mean speedup over the 40 rows: 1.075 (run 1) / 1.075 (run 2);
rows faster than the baseline in both runs: 40 of 40.

### `sm_107a`

**`sm_107a`: SM107 (212 SMs; 2 GPUs for world size 2, 4 GPUs for world
size 4), CUDA 13.5**

| Shape (hidden 6144) | Baseline µs (run 1 / run 2) | Cake µs (run 1 /
run 2) | Speedup = baseline / Cake (run 1 / run 2) |
|---|---|---|---|
| TP2 one-shot all-reduce, BF16 in / BF16 out, 1024 rows | 10.49 / 10.49
| 9.73 / 9.73 | 1.078 / 1.078 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 2048 rows | 14.98 / 15.01
| 13.85 / 13.86 | 1.082 / 1.083 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 4096 rows | 21.93 / 21.97
| 20.28 / 20.28 | 1.081 / 1.083 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 8192 rows | 34.48 / 34.43
| 34.21 / 34.15 | 1.008 / 1.008 |
| TP2 one-shot all-reduce, BF16 in / BF16 out, 16384 rows | 61.10 /
61.04 | 60.10 / 60.04 | 1.017 / 1.017 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 1024 rows | 8.56 / 8.56
| 8.34 / 8.33 | 1.026 / 1.028 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 2048 rows | 11.77 /
11.78 | 11.23 / 11.23 | 1.048 / 1.049 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 4096 rows | 18.36 /
18.35 | 17.78 / 17.78 | 1.033 / 1.032 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 8192 rows | 30.99 /
30.98 | 30.31 / 30.31 | 1.022 / 1.022 |
| TP2 one-shot all-reduce, NVFP4 in / BF16 out, 16384 rows | 55.48 /
55.48 | 54.58 / 54.60 | 1.016 / 1.016 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 1024 rows | 19.90 / 19.91
| 17.79 / 17.79 | 1.119 / 1.119 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 2048 rows | 26.27 / 26.28
| 22.48 / 22.48 | 1.169 / 1.169 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 4096 rows | 36.24 / 36.28
| 30.71 / 30.71 | 1.180 / 1.181 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 8192 rows | 56.27 / 56.32
| 54.52 / 54.53 | 1.032 / 1.033 |
| TP4 two-shot all-reduce, BF16 in / BF16 out, 16384 rows | 104.55 /
104.47 | 101.02 / 101.04 | 1.035 / 1.034 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 1024 rows | 16.30 /
16.31 | 15.57 / 15.58 | 1.047 / 1.047 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 2048 rows | 21.06 /
21.06 | 19.49 / 19.48 | 1.081 / 1.081 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 4096 rows | 30.54 /
30.52 | 28.99 / 29.00 | 1.053 / 1.052 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 8192 rows | 50.34 /
50.29 | 51.01 / 51.05 | 0.987 / 0.985 |
| TP4 two-shot all-reduce, NVFP4 in / BF16 out, 16384 rows | 99.24 /
99.17 | 94.18 / 94.18 | 1.054 / 1.053 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 1024 rows |
16.34 / 16.35 | 15.36 / 15.35 | 1.064 / 1.065 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 2048 rows |
22.75 / 22.74 | 20.90 / 20.90 | 1.089 / 1.088 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 4096 rows |
34.70 / 34.70 | 33.27 / 33.31 | 1.043 / 1.042 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 8192 rows |
61.31 / 61.28 | 56.57 / 56.56 | 1.084 / 1.083 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / BF16 out, 16384 rows |
112.73 / 112.69 | 102.62 / 102.65 | 1.099 / 1.098 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 1024 rows |
13.85 / 13.83 | 13.34 / 13.34 | 1.038 / 1.037 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 2048 rows |
21.74 / 21.73 | 21.77 / 21.76 | 0.999 / 0.999 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 4096 rows |
34.63 / 34.71 | 32.66 / 32.63 | 1.060 / 1.064 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 8192 rows |
54.63 / 54.67 | 49.75 / 49.74 | 1.098 / 1.099 |
| TP2 all-reduce + residual + RMSNorm, NVFP4 in / BF16 out, 16384 rows |
96.19 / 96.23 | 88.85 / 88.92 | 1.083 / 1.082 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 1024 rows |
18.08 / 18.11 | 15.78 / 15.77 | 1.146 / 1.148 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 2048 rows |
24.20 / 24.18 | 20.62 / 20.60 | 1.174 / 1.174 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 4096 rows |
37.40 / 37.37 | 34.22 / 34.22 | 1.093 / 1.092 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 8192 rows |
74.59 / 74.46 | 58.58 / 58.65 | 1.273 / 1.270 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / MXFP8 out, 16384 rows |
130.92 / 131.19 | 107.17 / 107.20 | 1.222 / 1.224 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 1024 rows |
17.54 / 17.55 | 15.92 / 15.90 | 1.102 / 1.104 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 2048 rows |
23.95 / 23.96 | 20.59 / 20.58 | 1.163 / 1.164 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 4096 rows |
36.98 / 37.01 | 34.44 / 34.34 | 1.074 / 1.078 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 8192 rows |
73.85 / 73.65 | 59.86 / 59.78 | 1.234 / 1.232 |
| TP2 all-reduce + residual + RMSNorm, BF16 in / NVFP4 out, 16384 rows |
131.36 / 131.66 | 109.15 / 109.15 | 1.203 / 1.206 |

Geometric-mean speedup over the 40 rows: 1.086 (run 1) / 1.086 (run 2);
rows faster than the baseline in both runs: 38 of 40. The two rows that
are not faster are TP4 two-shot all-reduce with NVFP4 in / BF16 out at
8192 rows (0.987 / 0.985) and TP2 all-reduce + residual + RMSNorm with
NVFP4 in / BF16 out at 2048 rows (0.999 / 0.999, within run-to-run
noise).

Cake has no other variant of this family beyond these eight, and the
family ships on `sm_100a`, `sm_103a` and `sm_107a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added two- and four-rank NVFP4-transport all-reduce, with fused
residual and RMSNorm options for two-rank use. Supports BF16 or NVFP4
inputs and BF16, NVFP4, or MXFP8 fused outputs.
- Added workspace planning and management, public communication APIs,
and support for SM100a and SM103a targets.
- **Documentation**
- Documented supported inputs, rank counts, workspace needs, CUDA graph
constraints, architecture targets, and fused output formats.
- **Tests**
- Added correctness coverage for distributed operations, output formats,
workspace behavior, and CUDA graph capture and replay.
- **Chores**
  - Updated pre-commit exclusions for matching CUDA kernel files.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Zihao Ye <zihaoy@nvidia.com>

### [d8e13c0](https://github.com/flashinfer-ai/flashinfer/commit/d8e13c06d575cd6ce0746d835b6f7fc42abe46ab)

- **作者**: eigen
- **时间**: 2026-10-19T08:51:10Z
- **提交信息**: perf(cake_fused_moe): Kimi-K3 NVFP4 SiTU experts SM100 8- and 16-token rows with evict-first weight-stream loads (#6628)

## Kimi-K3 NVFP4 SiTU experts: SM100 8- and 16-token rows with
evict-first weight-stream loads

On SM100 (B200), the 8-token row now runs `n8_feature_ef_f2e` and the
16-token row now runs `n8_w2a_m16_ef_f2e`. Each new route keeps the four
launches of the previous route. Only the FC1 and FC2 programs change.
The new programs put an `evict_first` cache hint on their weight-stream
TMA loads, which are A (the weights) and SFA (the weight scale factors).
A row reads the weights and their scale factors once, so they should not
displace the activations and routing tables that are read again. SM103
(B300) is unchanged. The single-token rows of both architectures are
also unchanged.

| tokens | SM100 (B200), previous route | SM100 (B200), this PR | SM103
(B300) |
|---|---|---|---|
| 8 | `n8_feature`: `quant_route:s2b`, `fc1:n8_s3b`, `fc2:n8_workfeed`,
`finalize:feature` | **`n8_feature_ef_f2e`**: `quant_route:s2b`,
`fc1:n8_persistent_ef`, `fc2:n8_workfeed_f2e`, `finalize:feature` |
`n8_feature` (unchanged) |
| 16 | `n8_w2a_m16`: `quant_route:s2b`, `fc1:n8_s3b`, `fc2:n8_w2a_s4`,
`finalize:feature` | **`n8_w2a_m16_ef_f2e`**: `quant_route:s2b`,
`fc1:n8_persistent_ef`, `fc2:n8_w2a_s4_f2e`, `finalize:feature` |
`n8_w2a_m16` (unchanged) |

The three new programs are SM100-only records. Each one is named after
its kernel and has one kernel translation unit and one binding
translation unit. `fc1:n8_persistent_ef`
(`cake_kimi_k3_nvfp4_situ_routed_moe_ffc17ea7b5160932a22c`) is the
persistent tile-N8 FC1. Both routes share this one record.
`fc2:n8_workfeed_f2e` (`..._d879256424e97e4fe373`) is the tile-N8
device-workfeed FC2 of the 8-token row. `fc2:n8_w2a_s4_f2e`
(`..._5f1134ff62964abafd6b`) is the two-CTA-per-SM FC2 of the 16-token
row. Each new program keeps the shared-memory layout, barriers, MMA
order and launch ABI of the program it replaces. The cache hint is the
only change. The FC1 and FC2 variants ship as a pair. The programs these
rows used before (`fc1:n8_s3b`, `fc2:n8_workfeed`, `fc2:n8_w2a_s4`) are
unchanged and remain the SM103 programs. SM100 no longer launches them,
so their registry records now list SM103 only.

The SM100 branch of the runtime's `_selector` now returns the two new
selectors. In `flashinfer/jit/cake_kimi_k3_situ.py`,
`KERNELS["sm_100a"]` replaces the three previous keys with the three new
ones, and `KERNELS["sm_103a"]` is unchanged. The launch arguments,
device-workfeed pools, host workspace layout and public workspace-size
query have not changed.

On the four measured rows (8 and 16 tokens, uniform and skewed routing),
the whole call takes 7.4-12.1 % less time than with the previous route
(1.08-1.14x its speed), runs at 1.18-1.25x the speed of the FlashInfer
trtllm-gen baseline, and has bitwise identical outputs to the previous
route.

This PR is stacked on #6622 (the SM100 8192-token row). Until that PR
merges, the diff against `main` also shows its changes. Only the six
added translation units (three kernel, three binding) and the three
modified host files listed below belong to this PR.

Rows changed by this PR: M = 8, uniform; M = 8, skewed; M = 16, uniform;
M = 16, skewed on B200 (SM100); every other row of the 52-row table is
unchanged.

Protocol, tolerances and the FlashInfer baseline (revision
`ac7bce13ea0ff76392fd17aa696b096e191d0825`, fresh autotune) are
unchanged: symmetric external CUDA graphs, CUPTI activity timing with
cold L2, five arms per row interleaved in one sealed timer, five rounds,
allocation-free submission, all-element BF16 atol 1.0 / rtol 0.1 with
exact intermediates, independent CPU re-derivation of every raw record,
compute-sanitizer synccheck and racecheck (memcheck not run).

| row | hardware | this export (us) | source build (us) | FlashInfer
trtllm-gen baseline (us) | previous export (us) | baseline / export |
source / export | previous / export | timer physical s | GPU-reportable
s (export / source / baseline / previous) | floor (us) | gap to the
ceiling model | stage times (us) | convergence |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|---|---|
| M = 8, uniform | B200 (SM100) | 64.959 | 64.992 | 77.952 | 71.776 |
1.2000x | 1.0005x | 1.1049x | 2587.2 | 3.747 / 3.751 / 4.500 / 4.143 |
50.0 | 1.300x | fc1 38.6 (floor 26.8) / fc2 26.2 (floor 13.5) / finalize
2.7 (floor 0.1) | open (gap tracked, not declared closed) |
| M = 8, skewed | B200 (SM100) | 42.400 | 42.464 | 52.768 | 47.232 |
1.2445x | 1.0015x | 1.1140x | 3171.6 | 3.799 / 3.801 / 4.727 / 4.231 |
29.9 | 1.420x | fc1 23.5 (floor 13.4) / fc2 17.0 (floor 6.8) / finalize
2.7 (floor 0.1) | open (gap tracked, not declared closed) |
| M = 16, uniform | B200 (SM100) | 107.264 | 107.040 | 126.432 | 115.807
| 1.1787x | 0.9979x | 1.0796x | 2424.2 | 3.762 / 3.755 / 4.435 / 4.061 |
90.4 | 1.186x | fc1 68.5 (floor 53.6) / fc2 38.6 (floor 27.0) / finalize
2.8 (floor 0.3) | open (gap tracked, not declared closed) |
| M = 16, skewed | B200 (SM100) | 53.152 | 52.895 | 66.368 | 60.448 |
1.2486x | 0.9952x | 1.1373x | 2837.4 | 3.752 / 3.733 / 4.684 / 4.269 |
40.2 | 1.322x | fc1 32.1 (floor 20.2) / fc2 16.9 (floor 10.3) / finalize
2.8 (floor 0.3) | open (gap tracked, not declared closed) |

Whole-call medians in microseconds; "previous export" is the route these
rows shipped before this PR, re-measured in the same timer; "source
build" is an in-session build of the same programs from source; the
floor is the row's roofline + measured fixed-overhead ceiling model (HBM
bytes, FC1/FC2 tensor-core FLOPs, launch / route / finalize overhead)
and the gap is the whole-call time over that floor. Geomean over the
rows above: baseline / export 1.2176x, previous / export 1.1088x.

**Correctness**: Rows M = 8, uniform; M = 8, skewed; M = 16, uniform; M
= 16, skewed: the exported kernels are bitwise identical to the previous
export on every timer round (BF16 output compared exactly; intermediates
exact). compute-sanitizer synccheck and racecheck ran clean on the
exported route of every row.

**Files** (one commit on top of `5012cb593a61` (the head of #6622)): +6
translation units under `csrc/fused_moe/cake_kimi_k3_situ/`;
`flashinfer/fused_moe/cake_kimi_k3_situ.py`,
`flashinfer/jit/cake_kimi_k3_situ.py`,
`tests/moe/test_cake_kimi_k3_situ.py`.

**Tests**: tests/moe/test_cake_kimi_k3_situ.py on B200 (sm_100a, 1 GPU,
FlashInfer head e1c8aba6858a): 31 passed / 0 failed, 37 warnings, 881.89
s.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added optimized routed Mixture-of-Experts execution for supported
NVIDIA SM100a GPUs, including routes for 8- and 16-token inputs.
* Added an 8,192-token route that combines quantization with
routing-table reset and processes routed inputs in larger groups.
* Added NVFP4 routed computation and support for preparing and
submitting routed execution in stages.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [579dc85](https://github.com/flashinfer-ai/flashinfer/commit/579dc85897be8c46fa03e74fb0efc1dc874fe524)

- **作者**: eigen
- **时间**: 2026-10-19T08:50:53Z
- **提交信息**: perf(cake_fused_moe): Kimi-K3 NVFP4 SiTU experts SM100 8192-token row: fused quantization + reset and 512-pair routing CTAs (#6622)

### Kimi-K3 NVFP4 SiTU experts: SM100 8192-token row with fused
quantization + reset and 512-pair routing CTAs

On SM100 (B200), the 8192-token row of the Kimi-K3 NVFP4 SiTU experts
now runs `large_q8i_p512fh2qr` instead of `large_q8i`, which #6341
shipped for the SM100 large rows. The new route launches seven kernels
instead of eight. One kernel now does both the activation quantization
and the routing-table reset. The routing histogram and scatter are
replaced by variants that handle 512 routed (token, expert-slot) pairs
per CTA. FC1, FC2 and the finalize are unchanged. SM103 (B300) is
unchanged, and the SM100 16384-token row keeps `large_q8i_p1024`
(#6442).

On the skewed 8192-token row, this change is 2.6 % faster than the
previously shipped SM100 route of this row: 845.953 us against 868.6725
us, or 22.7 us less. On the uniform row it is 890.657 us against 891.553
us: 0.896 us (0.1005 %) less, inside the measurement noise, so no gain
is claimed for the uniform row. The margin over FlashInfer trtllm-gen
(1.43x uniform, 1.95x skew) comes from the route and is inherited from
the previously shipped route. This change keeps it.

**Route by token count.** At 8192 tokens, SM100 runs
`large_q8i_p512fh2qr` (new) and SM103 is unchanged. At 16384 tokens,
SM100 runs `large_q8i_p1024` (#6442, unchanged) and SM103 is unchanged.
On SM100, no token count runs `large_q8i` itself any more. Each SM100
large row runs one of the two routes derived from it.

**Launch sequence of the new route.**

1. `quant_reset` (new): the static-qX activation quantization and the
routing-table reset in one kernel. Grid: num_tokens + ceil(max(E,
max_tiles*128+1) / 256) CTAs, which is 9149 CTAs at 8192 tokens.
2. `route_histogram` (new variant): each CTA builds a private expert
histogram in shared memory, with a first-toucher flush to global memory.
512 pairs per CTA, 3584 B shared memory.
3. `route_prefix`: unchanged.
4. `route_scatter` (new variant): a block-reserved scatter. Each CTA
reserves one block of rows per expert with a single global atomic and
places each pair at its in-CTA rank. Both tail loads are hoisted. 512
pairs per CTA, 7168 B shared memory.
5. `fc1:n128`: the unchanged tile-128 FC1.
6. `fc2:n128_q8i`: the unchanged FC2 with an INT8 per-tile partial.
7. `finalize:n128_q8i`: the unchanged finalize.

At 8192 tokens, the histogram and the scatter each launch 256 CTAs for
the row's 131,072 routed pairs. The production routing kernels launch
one pair per thread. Expert counts, tile tables and the set of rows for
every expert match the production routing's. The order of rows inside an
expert's tiles is a permutation of the production order, as in #6442.

**Programs and registry records.** The three new kernels are SM100-only
programs named after their kernel (one architecture, no fold):

- `quant_reset:n128_p512fh2qr` ->
`cake_kimi_k3_nvfp4_situ_routed_moe_2edb34923b075b7ab878` (kernel
translation unit sha256
`1389aea30d8f2b7d01709f9074a7c881e18de1ac38d3979ea71e8508ef0e83d5`,
26072 bytes; binding sha256
`efd4f2327347d91a379e4acb54e1ae19f7a2b558267012c58c4e90e4d0a8a18a`)
- `route_histogram:n128_p512f` ->
`cake_kimi_k3_nvfp4_situ_routed_moe_194f5c89b6e5659e023f` (kernel sha256
`f1531dc1a0ef8369491442ad69a33a35e86228d922b8e0a96df6170b2a680164`, 4259
bytes; binding sha256
`9bac311d084b2c2d956429be6e366d91d3f24ee644b35f7f6c9fdadaabe5cb2c`)
- `route_scatter:n128_p512fh2` ->
`cake_kimi_k3_nvfp4_situ_routed_moe_98eeb51d40321f05a2e9` (kernel sha256
`e9ecf4ffd314faa5e58a6fa7cc7ffc9daffbde24b002ff2a80e8436687badc78`, 6864
bytes; binding sha256
`fbe9b699df8f87e67093452c8b78a16c5e86cca03ba7d35c22e86bd5b697157f`)

Each program ships as `<program>_kernel.cu` and `<program>_binding.cu`
under `csrc/fused_moe/cake_kimi_k3_situ/`. Six translation units are
added, and none is removed or changed. The three kernel texts are
byte-identical to the kernels that were measured. The registry
`flashinfer/jit/cake_kimi_k3_situ.py` gains the three records in
`KERNELS["sm_100a"]` (37 -> 40 records; no existing record changes).
`KERNELS["sm_103a"]` is unchanged.

The three binding files are the exporter's prepared-stage host shims.
This is the form in which #6135 regenerated this backend. Each shim is
composed from a per-stage binding. The measured runs did not use the
delivered shims. They launched each kernel through a per-kernel staging
launcher, with those per-stage `run` bindings. A device-independent text
comparison of each per-stage binding with its delivered binding found
the launch equivalent for all three programs. The two bindings share:

- the entry signature
- the grid, `dim3((uint32_t)grid_x, (uint32_t)grid_y,
(uint32_t)grid_z)`, with the same grid > 0 guard
- block `(256u, 1u, 1u)`
- dynamic shared memory of 0 / 3584 / 7168 B (quant_reset / histogram /
scatter)
- the absence of launch attributes: no cluster, PDL or cooperative
launch in either binding
- the kernel symbol in `cudaLaunchKernelExC`
- the kernel-argument order and scalar casts
- the pointer sources (`arg.data_ptr()`) and the stream
(`TVMFFIEnvGetStream(dev.device_type, dev.device_id)`)
- the argument guards

One difference is outside the launch. The delivered `Run` and the route
submitter bind a `tvm::ffi::CUDADeviceGuard` on the first tensor's
device before they prepare and submit. The per-stage binding has no
guard and relies on its `CheckCurrentCudaDevice` check. Only the error
path for a non-current device differs. The other differences are style:
the per-stage binding keeps typed pointers
(`static_cast<T*>(arg.data_ptr())`) where the delivered shim stores
`void*` members assigned from the same `arg.data_ptr()`; the delivered
shim keeps a TensorView retention vector for its prepared path; the
delivered shim splits `Run` into Prepare and Submit and exports
`prepare_entry` / `submit_entry`; and the two host-shim namespace hashes
differ.

**Host.** In `flashinfer/fused_moe/cake_kimi_k3_situ.py`, the SM100
8192-token selector returns `large_q8i_p512fh2qr`
(`_LARGE_P512FH2QR_ARCHES = ("sm_100a",)`, `_LARGE_P512FH2QR_TOKENS =
(8192,)`). The fused `quant_reset` stage binds the quantization
constants and the reset constants in one Prepare. Each selector now gets
its own routing grid: `_ROUTE_PAIRS_PER_CTA = {"large_q8i_p1024": 1024,
"large_q8i_p512fh2qr": 512}`, and 256 pairs per CTA for all other
selectors. The workspace layout and the public workspace size query are
unchanged, because the new selector reads the same layout as
`large_q8i`.

**Tests.** In `tests/moe/test_cake_kimi_k3_situ.py`, the every-route
case asserts the 256-CTA routing grid at 8192 tokens on SM100. The new
test
`test_cake_situ_fused_quant_reset_routing_matches_the_production_routing`
runs the production routing kernels (route reset, quantization,
histogram, scatter) on the same workspace, inputs and stage bindings. It
compares the fused route with them in pair order, through the
token-to-row map. The following must be bitwise identical: expert
counts, tile tables, the rows of every expert, the route map, and the
FC1 output of every routed pair. Each call's output must also stay
within the test's published tolerance (`atol=1.0, rtol=0.1`). The test
does not compare the two outputs with each other. The INT8 per-tile FC2
partial is summed in an order that depends on tile membership, and tile
membership differs between the two routings. The test skips on
architectures that route 8192 tokens elsewhere (SM103). This change is
based on `main`, which contains #6442.

The full file `tests/moe/test_cake_kimi_k3_situ.py` passed on this
branch's head `5012cb593a61ef0b04072e4bbda6c508d9c63aee` on one NVIDIA
B200 (SM100): 31 passed, 0 failed, 37 warnings, 963.64 s (16:03). The
run used the delivered binding shims. It ran in the container
`nvcr.io#nvidia/sglang:26.07-py3` (CUDA 13.3.1, nvcc 13.3.73, torch
2.13.0a0+9186a08b2c.nv26.07, Python 3.12.3). FlashInfer was imported
from the checkout: flashinfer 0.7.2 resolved from the checkout, and the
JIT sources came from the checkout's `csrc`. The tree's pinned
dependencies were installed into a private directory placed first on
`PYTHONPATH`: apache-tvm-ffi 0.1.14.post1, nvidia-cutlass-dsl 4.7.1 with
its libs, pytest 9.1.1 and pytest-timeout 2.4.0. The image's own
flashinfer 0.6.14, flashinfer_jit_cache, flashinfer_cubin and cutlass
4.5.2 packages were not used. `FLASHINFER_CUDA_ARCH_LIST=10.0a` was set,
the JIT caches were private to the run, and cubins were read from a
private `FLASHINFER_CUBIN_DIR`. A build-generated, gitignored
`flashinfer/_build_meta.py` gave the checkout its version 0.7.2, so the
tree's own version checks ran. That file is not part of this PR. The
earlier gate for this backend ran in a project virtual environment; this
run did not.

**How it was measured.** The measurements were taken on SM100 (B200)
with the frozen protocol: symmetric external CUDA graphs, CUPTI cold-L2
timing, and a FlashInfer trtllm-gen baseline with fresh autotune. Each
row has five arms interleaved in one timer:

- this change
- an in-session source build of the same programs
- FlashInfer trtllm-gen
- the previously shipped SM100 route of this row (`large_q8i`, #6341)
- the route before that (`large_c7`, the pre-shuffled scale-factor route
of #5942)

compute-sanitizer synccheck (`ERROR SUMMARY: 0 errors`) and racecheck
(`RACECHECK SUMMARY: 0 hazards`) are clean on both rows. memcheck was
not run. Independent CPU checks of every tensor passed: 310 tensor
checks, 8 FlashInfer canonical checks and 360 routing checks.

Per-stage times (uniform / skew, us):

- fused quantization + reset: 15.872 / 15.520
- histogram + prefix + scatter: 9.311 / 9.119
- FC1: 369.3285 / 370.849
- FC2: 378.4485 / 336.4645
- finalize: 116.929 / 111.776

The ceiling-attribution floor is 489.08 us for both rows. This change
measures 1.82x the floor on the uniform row and 1.73x on the skew row.
These ratios are for information only.

**Numerics.** The output is not bitwise equal to the previously shipped
route's output, for the tile-membership reason given under Tests.
Routing tables, pair order and FC1 output were bitwise equal in every
numerics round. The tolerance gates passed with 0 mismatches. The max
abs diff to the reference was 0.9414 (uniform) and 0.8364 (skew). This
error band lies within the previously shipped route's own spread.

Rows changed by this PR: M = 8192, uniform; M = 8192, skewed on B200
(SM100); every other row of the 52-row table is unchanged.

Protocol, tolerances and the FlashInfer baseline (revision
`ac7bce13ea0ff76392fd17aa696b096e191d0825`, fresh autotune) are
unchanged: symmetric external CUDA graphs, CUPTI activity timing with
cold L2, five arms per row interleaved in one sealed timer, five rounds,
allocation-free submission, all-element BF16 atol 1.0 / rtol 0.1 with
exact intermediates, independent CPU re-derivation of every raw record,
compute-sanitizer synccheck and racecheck (memcheck not run).

| row | hardware | this export (us) | source build (us) | FlashInfer
trtllm-gen baseline (us) | previous export (us) | baseline / export |
source / export | previous / export | timer physical s | GPU-reportable
s (export / source / baseline / previous) | floor (us) | gap to the
ceiling model | stage times (us) | convergence |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|---|---|
| M = 8192, uniform | B200 (SM100) | 890.657 | 890.785 | 1275.858 |
891.553 | 1.4325x | 1.0001x | 1.0010x | 3370.0 | 3.931 / 3.931 / 5.621 /
3.936 | 489.1 | 1.821x | fc1 369.3 (floor 227.0) / fc2 378.4 (floor
161.1) / finalize 116.9 (floor 71.5) | open (gap tracked, not declared
closed) |
| M = 8192, skewed | B200 (SM100) | 845.953 | 846.369 | 1650.673 |
868.673 | 1.9513x | 1.0005x | 1.0269x | 3257.5 | 3.792 / 3.794 / 7.405 /
3.894 | 489.1 | 1.730x | fc1 370.8 (floor 227.0) / fc2 336.5 (floor
161.1) / finalize 111.8 (floor 71.5) | open (gap tracked, not declared
closed) |

Whole-call medians in microseconds; "previous export" is the route these
rows shipped before this PR, re-measured in the same timer; "source
build" is an in-session build of the same programs from source; the
floor is the row's roofline + measured fixed-overhead ceiling model (HBM
bytes, FC1/FC2 tensor-core FLOPs, launch / route / finalize overhead)
and the gap is the whole-call time over that floor. Geomean over the
rows above: baseline / export 1.6719x, previous / export 1.0138x.

**Correctness**: Rows M = 8192, uniform; M = 8192, skewed: data types
and quantization points are unchanged and only the floating-point
reduction order changed; the all-element BF16 gate (atol 1.0 / rtol 0.1
with exact intermediates) and the independent CPU audit pass, and the
error against the audit reference stays inside the previous export's own
round-to-round spread. compute-sanitizer synccheck and racecheck ran
clean on the exported route of every row.

**Files** (one commit on `main` `a9dae2503f37`): +6 translation units
under `csrc/fused_moe/cake_kimi_k3_situ/`;
`flashinfer/fused_moe/cake_kimi_k3_situ.py`,
`flashinfer/jit/cake_kimi_k3_situ.py`,
`tests/moe/test_cake_kimi_k3_situ.py`.

**Tests**: tests/moe/test_cake_kimi_k3_situ.py (the full file) on the
delivered head 5012cb593a61ef0b04072e4bbda6c508d9c63aee on one NVIDIA
B200 (SM100): 31 passed, 0 failed, 37 warnings, 963.64 s. Environment:
container nvcr.io#nvidia/sglang:26.07-py3 (CUDA 13.3.1, nvcc 13.3.73,
torch 2.13.0a0+9186a08b2c.nv26.07, Python 3.12.3); FlashInfer imported
from the checkout (0.7.2, JIT sources from the checkout's csrc) with the
tree's pinned dependencies (apache-tvm-ffi 0.1.14.post1,
nvidia-cutlass-dsl 4.7.1 and its libs, pytest 9.1.1, pytest-timeout
2.4.0) installed into a private directory placed first on PYTHONPATH;
the image's own flashinfer / cutlass packages were not used;
FLASHINFER_CUDA_ARCH_LIST=10.0a, private JIT caches and cubin directory.
The gate ran the delivered binding shims, whose launch is text-proven
equivalent to the measured per-stage bindings (see the binding paragraph
above).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added an `sm_100a` routing option for 8,192-token inputs. It combines
activation quantization with routing-table reset and processes up to 512
routed pairs per block during routing.
* The new option integrates with the existing quantized
expert-processing pipeline and is checked against the production route
for routing data, intermediate results, and output accuracy.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f57c58b](https://github.com/flashinfer-ai/flashinfer/commit/f57c58b898cc0f96ddea03066a3fd66ad201337a)

- **作者**: Yuxian Qiu
- **时间**: 2026-10-19T08:33:50Z
- **提交信息**: [NVBUG-6791733][fix] Guard ragged Q tensor maps on Blackwell (#6482)

<!-- .github/pull_request_template.md -->

## 📌 Description

Repeated Prims-TS context launches can fail in the packed-Q TMA load on
Blackwell. Preserve the original five-dimensional ragged Q descriptor,
loads, and request-local masking, and apply NVIDIA's documented OOB
address-generation correction only when needed by the real Q layout.

The context builder gates the correction on the tensor's actual device
capability, SM100 or SM103. After descriptor encoding, clear descriptor
bit 85 when a contiguous 128 KiB prefix cannot be established from the
real compact Q tensor. For compact `(T,H,D)` inputs, compare runtime `T`
against `ceil(131072 / (H*D*element_bytes))`; unknown/noncompact layouts
conservatively receive the correction. This avoids runtime byte-count
multiplication overflow and uses actual D192 FP8 storage rather than its
padded staging width.

The SM100/SM103 gate describes this backend's scope, not an exhaustive
list of affected GPUs. Prims-TS context accepts SM100, SM103, and SM107;
its SM107 support can use a `sm_100f` compiler fallback, so the compiler
target alone must not enable a Blackwell-specific descriptor edit.
SM110/SM120/SM121 are rejected by this context path. NVIDIA's driver
notice says Blackwell generally and does not provide a per-SM
affected/unaffected matrix; this PR does not establish whether those
other Blackwell devices encounter the same issue. The descriptor edit
must not be generalized to other architectures without confirming their
layout and applicability.

Large compact Q tensors retain the original descriptor. Fixed-Q, K/V/O
descriptors, GPU scheduling, and public APIs retain their existing
behavior. The correction adds no GPU kernel, workspace, or host-device
synchronization.

The driver issue is consistent with allocation-placement-dependent
failures involving overlapping tensor descriptions. Synthetic descriptor
dimensions cannot establish the actual mapped prefix. The targeted
correction strongly supports this diagnosis; it does not establish the
driver's internal address-translation sequence.

Retain the four packed-tail regression tests covering contiguous/paged
KV, causal/sliding-window attention, and replay after changing Q.

## 🔍 Related Issues

- [NVIDIA driver 615.71.09 known
issues](https://docs.nvidia.com/datacenter/tesla/tesla-release-notes-615-71-09/index.html#known-issues):
Blackwell tensor-map failures and the descriptor correction.
- [CUTLASS contiguous-prefix
criterion](https://github.com/NVIDIA/cutlass/blob/main/include/cute/arch/copy_sm90_desc.hpp#L443).
- [Related TensorRT-LLM draft
PR](https://github.com/NVIDIA/TensorRT-LLM/pull/20298), which currently
contains the earlier native-Q approach.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

All applicable hooks passed for the affected files using `pre-commit run
--files ...`, including mypy, Ruff lint, and formatting. Repository-wide
hooks were not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

GPU validation used the guarded-candidate source in
`a9883a5e8ada0d25754ecb31ae7eb83109c403cc`, based on main
`2895577720741ddfedff118202c89584996b8875`. The subsequent
copyright-header cleanup changes no executable Python code (AST equality
checked); applicable pre-commit hooks pass. GPU tests were not repeated
for that comment-only cleanup:

- **B200: 80 ordered graph/tail tests passed**: four packed-tail cases
followed by four BF16 packed/paged D128/D256 live-offset graph cases,
repeated in session order ten times.
- **B200: five supplemental boundary/view oracle cases passed**, each
checking eager execution, captured replay, and replay after changing Q:
BF16 H8/D128 at 63 and 64 rows; FP8 H8/QK192/V128 at 85 and 86 rows; and
a contiguous 64-row BF16 view with a nonzero storage offset.
- **The guarded candidate passed 54 independent FP32-reference checks in
18 benchmark processes** across B200/B300, covering eager execution,
graph replay, and changed-Q replay. Across all comparison variants
(baseline, native-Q, unconditional correction, and guarded correction),
40 processes passed 120 checks. Source and harness hashes matched the
frozen validation snapshots.
- Runtime: PyTorch `2.14.0a0+b2c75dd062.nv26.09`, CUDA 13.4, CUTLASS DSL
`4.8.0.dev0`, reported driver `615.71.09`.

Reproduce the ordered selection in one process (requires pytest-repeat):

```bash
python -m pytest -p no:xdist -v \
  tests/attention/test_attention_ts_context.py::test_attention_ts_context_packed_query_tails \
  tests/attention/test_attention_ts_context.py::test_attention_ts_context_live_q_offsets_expand_causal_domain_on_graph_replay \
  -k 'packed_query_tails or bf16' --count=10 --repeat-scope=session
```

The full 322-case context suite and the full FlashInfer suite have not
been run on this guarded candidate.

### Performance

Paired measurements use the original main source as baseline, two
fresh-process rounds with reversed variant order, 50 eager and 10 graph
warmups, and 31 CUDA-event samples per process. Each timed graph
contains 256 wrapper calls with preallocated outputs. Every paired
process-median delta across five B200 and two B300 configurations was
within **±0.02%**. All samples were retained, including one B300
baseline timing outlier; this is a median-latency result, not a
tail-latency guarantee.

All configurations below use Hq/Hkv=8/2 and BF16 output. Times are
medians of the two process medians.

| GPU | Configuration | Baseline µs | Guarded correction µs |
| --- | --- | ---: | ---: |
| B200 | Paged BF16 D256, many short requests | 61.710 | 61.710 |
| B200 | Packed BF16 D256, many short requests | 49.754 | 49.758 |
| B200 | Packed BF16 D128, tails | 9.361 | 9.361 |
| B200 | Fixed BF16 D256 | 47.318 | 47.316 |
| B200 | Packed FP8 D256, long aligned requests | 178.111 | 178.097 |
| B300 | Paged BF16 D256, many short requests | 59.017 | 59.010 |
| B300 | Fixed BF16 D256 | 42.226 | 42.232 |

Problem sizes: many-short Q=`(1,3,17,65)` ×32, KV=`(33,33,65,129)` ×32,
causal window 31, with nonidentity 32-token pages for paged KV; tails
Q=`(3,130,1)`, KV=`(33,160,17)`, causal; fixed 256 requests with
Q=1/KV=33, causal; long FP8 two Q=KV=4096 requests, dense.

For small packed causal inputs Q=`(3,2)`, KV=`(33,64)`, B200 measured
**9.199 → 9.193 µs** for BF16 D128 and **9.892 → 9.809 µs** for FP8
QK192/V128, comparing the earlier native-Q fix with this guarded
correction. No uncorrected small-Q baseline was run.

These measurements cover warmed CUDA-graph GPU execution. Planning, JIT,
capture, host overhead, cold-cache behavior, and end-to-end serving
throughput are outside the measurement scope.

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

Please review the real-Q prefix proof, actual-device architecture gate,
and host descriptor update. Generated host IR confirms the runtime
row-count guard modifies the descriptor later passed to launch. The
writable host `TensorMap` alias works in the tested DSL runtime;
cross-version support or an encoder-side helper needs DSL-owner review.

This revision replaces the earlier native-Q implementation, which passed
broad correctness checks but increased measured graph-operation latency
by up to 3.43% in a separate B300 comparison. A separately frozen
unconditional descriptor-correction port passed the original 37-case
TensorRT-LLM sequence ten times (370 passes), supporting the diagnosis;
those results are not validation of this exact guarded source.

Keep the workaround scoped to documented Blackwell descriptor layouts
and revisit it when a driver fix or supported encoder helper is
available.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved attention correctness on supported Blackwell GPUs when
processing partial query tiles in contiguous and paged attention.
* Verified correct results with causal masking, both unwindowed and
sliding-window attention, and captured graph replay after query data
changes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>

### [8f5d65d](https://github.com/flashinfer-ai/flashinfer/commit/8f5d65d6037cc5c171cabacce3fc9d1b8f9d96dc)

- **作者**: eigen
- **时间**: 2026-10-19T08:02:45Z
- **提交信息**: perf(cake_all_gather_matmul): SM103a SM push route band and cta_group::2 pair main kernel for measured regions (#6501)

Regenerated export of the Cake all-gather matmul backend from the same
generator as #6440, rebased on `main`. This export makes two changes.
Both apply to SM103a only:

1. **SM push route band.** A world-size-8 call takes the SM push instead
of the copy-engine push when its rows pad to 1024 and its N is at most
1619. In the shape inventory this moves one shape: TP8, M=1024 per rank,
N=1280, K=8192, bf16, K-major weight. That shape runs 8.1–8.3 % faster.
This change does not touch any kernel.
2. **CTA-pair main kernel for measured regions.** The persistent main
GEMM kernel with 256-column tiles gets a CTA-pair twin that runs
`tcgen05.mma.cta_group::2` over a cluster of two CTAs. A
per-architecture region table decides which calls use it. In the shape
inventory this moves four shapes: two world-size-2 bf16 N-major shapes
and two TP4 bf16 K-major QKV shapes. These four run 5.8–11.5 % faster.

The speedups come from paired runs on two 8×B300 nodes. Every changed
shape is faster on both nodes, and its outputs are bitwise identical.
SM100a has an empty band and no regions, so its routes and programs are
unchanged.

## Routing and kernel changes

### SM push route band

Until now, the SM push required all three of these conditions:

- world size 4 or 8;
- rows rounded up to a multiple of 128 ("padded rows") of at most 512;
- N ≤ 12288 − 16 × padded rows.

Every other call used the copy-engine push.

`flashinfer/jit/cake_all_gather_matmul.py` now has a band table per
architecture:

`SM_PUSH_BANDS_BY_ARCH = {"sm_100a": [], "sm_103a": [[8, 1024, 1619]]}`

Each band is `[world_size, padded_rows, max_cols]`. A call takes the SM
push in either of two cases:

- the existing rule holds;
- a band for its architecture matches: the same world size, exactly the
same padded row count, and N ≤ `max_cols`.

Details:

- `uses_sm_push(*, rows, world_size, cols, arch)` and
`sm_push_reachable(*, world_size, cols, arch)` now take `arch`. The new
helper `sm_push_bands(arch)` returns the bands for an architecture. An
architecture missing from the table raises an error; it never falls back
to an empty band.
- The ws8 SM103a host sequences compile the band into a constexpr route
guard. Every other sequence has an empty band.
- 1619 is the geometric midpoint of two values at 1024 padded rows: N =
1280, where the SM push is faster, and N = 2048, where the copy-engine
push is faster.
- The banded inventory shape uses the existing wide push program,
`peer_push_wide` (8 CTAs per peer, unroll 8).

| shape | SM103a before | SM103a after | SM100a |
|---|---|---|---|
| TP8, M=1024 per rank, N=1280, K=8192, bf16, K-major | copy-engine push
| SM push (`peer_push_wide`) | unchanged (copy-engine push) |
| every other inventory shape | unchanged | unchanged | unchanged |

### CTA-pair main kernel

The persistent main kernel with 256-column tiles now has a CTA-pair
twin:

- it issues `tcgen05.mma.cta_group::2` over a cluster of two CTAs
(cluster dims `(2, 1, 1)`);
- each CTA holds its own 128 A rows and 128 B columns per stage;
- its kernel symbols end in `_cg2`;
- it launches on an even grid of `2 * min(pair_tiles, SMs / 2)` CTAs.

The loader's `main_form` picks the twin with a fixed rule. A call runs
the twin only when both of these hold:

- its `(world_size, dtype, b_layout)` class has a measured region for
the device architecture;
- `min_padded_rows ≤ padded rows ≤ max_padded_rows`, and N ≤ `max_cols`.

Every other call keeps its current main kernel.

The loader holds the regions in `CG2_REGIONS`. Each entry is
`[world_size, dtype, b_layout, min_padded_rows, max_padded_rows,
max_cols]`:

| architecture | world size | dtype | B layout | padded rows | max N |
|---|---|---|---|---|---:|
| SM103a | 2 | bf16 | N-major | 2048–5760 | 2048 |
| SM103a | 4 | bf16 | K-major | 1024–1536 | 6058 |
| SM100a | no regions | | | | |

An architecture gets the twin only for classes that route at least one
inventory shape on it. `CG2_CLASSES` lists those classes and matches the
region classes. On SM103a they are world size 2 bf16 N-major and world
size 4 bf16 K-major. SM100a has none. The host sequences receive the
selected form as a positional `main_cg2` flag after `block_n`.

| shape | SM103a before | SM103a after | SM100a |
|---|---|---|---|
| world size 2, M=2048 per rank, bf16, N-major | single-CTA main |
CTA-pair main (`_cg2`) | unchanged |
| world size 2, M=4096 per rank, bf16, N-major | single-CTA main |
CTA-pair main (`_cg2`) | unchanged |
| TP4 QKV projection, M=1024 per rank, bf16, K-major | single-CTA main |
CTA-pair main (`_cg2`) | unchanged |
| TP4 QKV projection, M=1025 per rank (pads to 1152), bf16, K-major |
single-CTA main | CTA-pair main (`_cg2`) | unchanged |
| every other inventory shape | unchanged | unchanged | unchanged |

Nothing is approximated, and accumulation precision is unchanged.

## Kernel set and loader surface

- **Kernels.** The route band adds no kernel. The CTA-pair change adds
the `_cg2` twins for the two SM103a classes. SM100a gets no new kernel.
Kernel-set growth in `csrc/cake_all_gather_matmul`: 2 new kernel modules
(the CTA-pair `_cg2` main of the world-size-2 bf16 N-major class and of
the world-size-4 bf16 K-major class, SM103a). The 24 host sequences are
regenerated (every sequence passes the form as the positional `main_cg2`
flag; the SM103a world-size-8 sequences also carry the band). The shared
device header includes the two helper libraries of the pair twin
(`cake_elect_commit_cg2_multicast`, `cake_tma_3d_gmem2smem_cta2`), and
four existing kernel modules (`barrier_p0`, `barrier_p1`, `peer_push`,
`peer_push_wide`) gain a translation-unit-local `make_warp_uniform(int)`
fallback overload for that header; their kernel bodies are unchanged.
- **New loader constants** (`flashinfer/jit/cake_all_gather_matmul.py`):
`SM_PUSH_BANDS_BY_ARCH`, `CG2_CLASSES`, `CG2_REGIONS`, plus the new
helper `sm_push_bands(arch)`. `uses_sm_push` and `sm_push_reachable`
gain a keyword-only `arch` argument. `main_form` applies the region
rule.
- **Host sequences** (`csrc/cake_all_gather_matmul`): re-rendered with
the shared band guard and the `main_cg2` flag. Only the ws8 SM103a
sequences carry a non-empty band.
- **Backend module**
(`flashinfer/comm/all_gather_matmul/cake_all_gather_matmul.py`): passes
the device architecture to both route helpers, and passes the form
chosen by `main_form` to the host sequence.
- **Tests** (`tests/comm/test_all_gather_matmul_cake.py`): updated for
the band rule and the region rule.
- **Public API.** The `all_gather_matmul` / `prepare_all_gather_matmul`
entry points are unchanged.
- **File signature vs `main`:** added 2, modified 32, deleted 0 (63
delivered files: 23 kernel modules, 24 host sequences, 10 device
helpers, 4 Python files).

## Validation

All GPU runs used two 8×B300 (SM103a) nodes. Each change was measured
separately against an independent build of the generator's `main`. The
export gate and FlashInfer tests at the end of this section cover the
combined export. A change is adopted only if every shape it changes is
significantly faster on both nodes.

Timing protocol, the same for both changes:

- CUDA-graph replay with a cold L2;
- CUPTI GPU span, taking the slowest rank in each iteration;
- 200 ms per group, nine counterbalanced ABBA groups, two passes;
- a same-code control arm.

### SM push route band

- **Exactness.** On every rank, outputs are bitwise identical to the
base (int16-view SHA-256 per rank, both arms). The dedicated exactness
run covered 68 rows with 0 failures and 0 route mismatches. The rows of
the paired run had 0 failures. All 62 inventory rows are covered.
- **Determinism.** Two independent `torchrun` launches produced
identical outputs on both arms and both nodes.
- **Skew stress.** 2 rows × {this routing, forced copy-engine push}, ≥
1e4 iterations per path, bitwise check on every iteration: 0 failures.
- **compute-sanitizer 13.4.92.** synccheck: 0 errors on 5/5 rows.
racecheck: 0 hazards on 5/5 rows. The two tools ran separately. memcheck
was not run.
- **Paired A/B on the changed shape** (> 1 means this PR is faster). The
µs columns are each arm's median over all samples. The speedup is the
median, over the nine groups, of the per-group base/PR ratio, so the
columns need not multiply exactly.

| node | base µs | this PR µs | speedup | noise bound (delta_res) |
read-out |
  |---|---:|---:|---:|---:|---|
  | node 1 | 342.3 | 314.2 | 1.0832 | 0.0089 | significantly faster |
  | node 2 | 342.1 | 314.5 | 1.0811 | 0.0117 | significantly faster |

Timeline attribution points the same way on both nodes. The main kernel
span is 4.0 % / 4.9 % shorter and starts earlier. The SM push kernel
spans 208 / 212 µs. The copy-engine route has no push kernel.

Same-code control arm (this code forced to the copy-engine push, which
is `main`'s route for this shape):

  | node | ratio | read-out |
  |---|---:|---|
  | node 1 | 1.0097 | marginal: \|ln\| 0.0096 vs bound 0.0094 |
  | node 2 | 1.0051 | not significant |

  The A/A read-out passes.

  Identical-program control rows:

  | control row | median ratios |
  |---|---|
| TP8 M=512 gate/up projection, bf16, K-major (sub-millisecond) |
0.9973–1.0099 |
  | TP8 M=65536 bf16 (≥ 1 ms) | 0.9986–1.0031 |

  Control standard deviation was ≤ 0.0185, with 0 voided groups.

No-regression check: every one of the 45 perf rows must be ≥
exp(−delta_res) in the paired run. The check passes on both nodes once
rows whose programs are identical to `main` are exempted (bitwise-equal
outputs, identical kernel names). Before the exemption, only
identical-program rows missed:

  - four ws2 rows at 0.989–0.997 on both nodes;
  - TP8 M=125 gate/up projection on one node (0.9550, bound 0.0132);
  - TP8 M=4096 bf16 on the other node (0.9891, bound 0.0041).

- **Route rescan.** All 45 perf rows were compared under both forced
push routes on one 8×B300 node (world sizes 8/4/2, 9 groups). The
shipped route (existing rule + band) is the faster route on every row,
with 0 drift.

### CTA-pair main kernel

- **Exactness.** On every rank and every row, outputs are bitwise
identical to the reference program. The test tolerance is unchanged
(bf16, atol = rtol = 1e-2 against an fp32 reference), and there are zero
mismatches.
- **Determinism.** Replays are deterministic.
- **compute-sanitizer.** synccheck and racecheck: 0 errors.
- **End-to-end.** The 2-GPU end-to-end test passes.
- **Paired A/B on the four changed shapes** (> 1 means this PR is
faster; same conventions as above). All four are significantly faster on
both nodes.

| shape | node 1 base µs | node 1 this PR µs | node 1 speedup | node 2
speedup |
  |---|---:|---:|---:|---:|
| world size 2, M=2048 per rank, bf16, N-major | 121.8 | 114.0 | 1.0650
| 1.0583 |
| world size 2, M=4096 per rank, bf16, N-major | 216.7 | 203.9 | 1.0637
| 1.0596 |
| TP4 QKV, M=1024 per rank, bf16, K-major | 189.3 | 170.1 | 1.1152 |
1.0707 |
| TP4 QKV, M=1025 per rank, bf16, K-major | 187.4 | 170.6 | 1.0914 |
1.0613 |

Node 2 medians and the per-row noise bounds (delta_res, node 1 / node
2):

| shape | node 2 base µs | node 2 this PR µs | delta_res node 1 / node 2
|
  |---|---:|---:|---|
| world size 2, M=2048 per rank, bf16, N-major | 120.6 | 113.9 | 0.0011
/ 0.0011 |
| world size 2, M=4096 per rank, bf16, N-major | 216.3 | 204.2 | 0.0011
/ 0.0011 |
| TP4 QKV, M=1024 per rank, bf16, K-major | 181.6 | 171.7 | 0.0408 /
0.0350 |
| TP4 QKV, M=1025 per rank, bf16, K-major | 185.2 | 176.2 | 0.0408 /
0.0350 |

Same-code control arm (this code forced to the single-CTA main kernel):
+0.3 %. The A/A read-out flags this as significant, so it is disclosed
here. It is smaller than the smallest per-node speedup of the change
(5.8 %).

### Combined export

- **SM100a (B200).** The band table and the region table are both empty
for SM100a. Every call therefore takes the same route and launches the
same programs as on `main`. All measurements in this PR are from SM103a.
- **Generator source vs this export.** Route-scoped export of the five
changed shapes, world sizes 8/4/2:

| shape | route / main kernel | source ms | export ms | source / export
|
  |---|---|---:|---:|---:|
| TP8 1024×1280 K-major bf16 (SM103a) | SM push (`peer_push_wide`) |
0.302690 | 0.304212 | 0.9950 |
| world size 2, M=2048, bf16, N-major (SM103a) | CTA-pair main |
0.114273 | 0.114689 | 0.9964 |
| world size 2, M=4096, bf16, N-major (SM103a) | CTA-pair main |
0.197986 | 0.198146 | 0.9992 |
| TP4 QKV M=1024, bf16, K-major (SM103a) | CTA-pair main | 0.167714 |
0.167938 | 0.9987 |
| TP4 QKV M=1025, bf16, K-major (SM103a) | CTA-pair main | 0.168899 |
0.169794 | 0.9947 |

Each change's own export also passed this gate. For the route band
shape, that run measured generator source 0.302659 ms vs FlashInfer
export 0.302339 ms, ratio 1.0011 (3 counterbalanced groups, floor 0.95).
- **FlashInfer tests.** Against the exported tree:
`tests/comm/test_all_gather_matmul_cake.py` 291 passed, 0 failed;
`tests/comm/test_all_gather_matmul_cake_e2e.py` 3 passed with 8, 4 and 2
GPUs visible (SM103a, 8×B300). On the PR head (`c8917fee`):
`tests/comm/test_all_gather_matmul_cake.py` 291 passed, 0 failed;
`tests/comm/test_all_gather_matmul_cake_e2e.py` 3 passed with 8 GPUs
visible and 3 passed with 4 GPUs visible (SM103a, 8×B300). Each change's
own export passed the FlashInfer tests. For the route band export,
`tests/comm/test_all_gather_matmul_cake.py` had 268 passed and e2e 3/3
passed (world sizes 8, 4, 2).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4626
- **最后更新**: 2026-10-19T21:57:42Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

## 提交分析总结（hao-ai-lab/FastVideo，2 条提交）

### 1. 主要更新类型
两条提交均属于**功能新增（feat）**，分别聚焦于：
- 新模型/新推理模式在消费级硬件上的落地支持
- 社区微调模型（LoRA）的加载能力与显存优化

没有涉及 Bug 修复或文档更新，属于纯粹的能力扩展。

### 2. 关键变更点及与项目方向的关系
- **FastH3 OmniRef 推理支持（#1980）**：新增对 OmniRef（参考驱动的视频生成）推理模式的支持，并明确列出了目标硬件——RTX 5090、PRO 6000、DGX Spark、4090 等消费级/桌面级设备。这直接呼应 FastVideo 的核心定位：**让高质量视频生成在非数据中心环境下也能高效运行**。
- **MiniMax-H3 LoRA 加载 + 量化 side branch（#1973）**：支持社区基于 MiniMax-H3 的 LoRA 微调权重加载，并引入量化（quantization）技术处理 side branch（旁路分支），在保留主干精度的同时降低显存占用。

两者结合，体现了项目在"**模型多样性 + 硬件亲民化**"两条线上的同步推进。

### 3. 对项目的影响和潜在意义
- **降低使用门槛**：消费级显卡（4090/5090）用户此前可能无法运行 OmniRef 类推理，现在可以直接上手，扩大了用户基数和社区生态。
- **增强生态兼容性**：LoRA 加载支持意味着社区创作的微调模型可以无缝进入 FastVideo 推理管线，鼓励社区贡献，形成"训练在别处、加速在 FastVideo"的协作模式。
- **量化技术的引入**为后续在更小显存设备（如 DGX Spark、笔记本级 GPU）上部署更大模型铺平了道路，是性能优化路线的重要一步。

### 4. 值得关注的技术点
- **量化 side branch 设计**：将 LoRA 旁路分支量化而非全模型量化，是一种精度-显存的折中策略，值得观察其在实际生成质量上的表现。
- **硬件适配广度**：同时覆盖 Ada（4090）、Blackwell（5090/PRO 6000）和 GB10（DGX Spark）架构，说明底层 kernel/调度层做了跨架构适配，工程复杂度不低。
- **AI 辅助开发痕迹**：#1980 出现 Claude Opus 5.5 作为共同作者，反映了项目在采用 AI 辅助编码工作流上的探索。

### 5. 对项目发展的意义（结合 README 背景）
FastVideo 定位为高效的视频生成/训练框架，配套文档、Cookbook、Quick Start 和每周开发会议，说明它正从研究项目走向**活跃的开源产品化阶段**。这两条提交表明团队当前战略重点是：
1. **横向扩展模型覆盖面**（H3 系、MiniMax-H3 等新模型快速接入）
2. **纵向深化硬件可及性**（消费级设备全系支持）

这种"新模型快速跟进 + 低门槛部署"的组合，有助于在竞争激烈的视频生成加速赛道（如与 SVD 加速、Distill 方案等对比）中建立差异化优势，吸引社区开发者围绕其生态进行微调与应用开发。

总体而言，这两条提交强化了 FastVideo 作为"**消费级硬件上的视频生成加速枢纽**"的角色，对项目社区增长和生态成熟具有积极而直接的推动作用。

## 详细提交记录

### [376e445](https://github.com/hao-ai-lab/FastVideo/commit/376e445f0e8d192c2d9a5f28010a6b3a7012667e)

- **作者**: Aryan Kumar
- **时间**: 2026-10-19T21:57:36Z
- **提交信息**: [feat]: FastH3 OmniRef inference on consumer devices (RTX 5090 / PRO 6000 / DGX Spark / 4090) (#1980)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2099dd5](https://github.com/hao-ai-lab/FastVideo/commit/2099dd55337e4da7a69d8e18def7d0382f775d13)

- **作者**: Aryan Kumar
- **时间**: 2026-10-19T21:29:23Z
- **提交信息**: [feat]: Community MiniMax-H3 LoRA loading with quantized side branch (#1973)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34762
- **最后更新**: 2026-10-19T17:56:42Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, YiYi Xu

## AI分析总结

## huggingface/diffusers 昨日提交分析

### 1. 主要更新类型
- **发布流程维护**：post-release 0.41.0，版本发布后的例行收尾
- **功能修正/对齐**：FLUX.3 模型的参考图像尺寸处理与 BFL 官方发布版本保持一致

### 2. 关键变更点与项目方向的关系
- **版本发布收尾（#15062）**：在 0.41.0 版本发布后，对仓库进行版本号重置、开发分支恢复等常规操作，属于 HuggingFace diffusers 项目的标准发布周期管理，确保主分支继续用于下一版本（如 0.42.0 dev）的开发。
- **FLUX.3 图像尺寸对齐（#15073）**：调整了 FLUX.3 模型对参考图像的预处理逻辑，具体包括：单张参考图整体保留，缩放至填充画布低于 4MP，按 FLUX.3 图像处理器的 `resize_mode="fill"` 策略进行反射填充（reflect padding）以匹配 token 网格，输出时裁剪回原始比例；多张参考图则各自控制在 1MP 以下；默认输出尺寸跟随第一张参考图。这一变更使开源实现与 BFL（Black Forest Labs）官方发布的参考图行为完全对齐。

### 3. 对项目的影响和潜在意义
- **版本稳定性**：post-release 提交保证了开源版本迭代的规范性，为社区开发者提供清晰的版本基线。
- **跨实现一致性**：FLUX.3 对齐 BFL 参考实现，意味着用户使用 diffusers 复现 FLUX.3 官方示例或对比效果时将获得更一致的输出，减少因预处理差异导致的结果偏差。这对采用 Apache 2.0 许可、定位为开放扩散模型库的 diffusers 来说，是维持其"参考级"实现地位的重要举措。
- **对多图参考任务的影响**：明确了单图与多图参考的不同预算策略（4MP vs 1MP），对实际应用中图像参考工作流（如图像编辑、风格迁移）的显存与质量平衡有指导意义。

### 4. 值得关注的技术点
- **反射填充（reflect padding）与 token 网格对齐**：扩散模型（尤其 DiT 架构如 FLUX）要求输入分辨率是特定 patch/token 网格的整数倍，采用反射填充而非简单黑边填充可避免引入边缘伪影。
- **`resize_mode="fill"` 语义**：保持纵横比并填充到目标画布，而非强制拉伸，有利于保持参考图内容完整性。
- **AI 辅助开发痕迹**：第二条提交的共同作者为 "Claude Fable 5.1"（Anthropic），体现了前沿开源项目中 AI 协作工具参与代码贡献的趋势，值得关注其对代码质量和审阅流程的影响。

### 5. 基于项目背景的综合影响
README 显示 diffusers 是 HuggingFace 维护的 Apache 2.0 许可开源项目，核心使命是提供标准化、高质量的扩散模型实现。这两条提交虽规模不大，但分别对应项目的两大支柱：**规范的版本发布流程**保障社区对稳定版本的依赖；**与 BFL 官方参考实现的精确对齐**则强化了 diffusers 作为 FLUX 系列模型权威开源实现的地位，降低用户从官方闭源/参考环境迁移到开源生态的门槛，有助于巩固其在生成式 AI 基础设施中的核心角色。

## 详细提交记录

### [e04f0c5](https://github.com/huggingface/diffusers/commit/e04f0c5f24392fcd34b32d18d0ce03668f9bcd50)

- **作者**: Sayak Paul
- **时间**: 2026-10-19T10:31:56Z
- **提交信息**: post-release 0.41.0 (#15062)

* post-release 0.41.0

* up

### [4df4a5b](https://github.com/huggingface/diffusers/commit/4df4a5b35748bab1d967c0ff49ad1a144d094322)

- **作者**: YiYi Xu
- **时间**: 2026-10-19T07:28:26Z
- **提交信息**: FLUX.3: match the released BFL reference image sizing (#15073)

* FLUX.3: match the released BFL reference image sizing

A single reference is kept whole: downscaled so its padded canvas fits under 4 MP, reflect-padded to the token grid (`resize_mode="fill"` of the FLUX.3 image processor), and cropped back on output. Several references are fitted under 1 MP each. The default output size follows the first reference.

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-10-19T05:38:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13268
- **最后更新**: 2026-10-19T21:10:17Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Hong Zhang, Jinyan Ye

## AI分析总结

## 一、主要更新类型
本次提交以**功能新增**为核心，辅以**文档更新**。主要体现在两方面：一是新增对 Moss-Image 模型的支持，二是为该模型追加低显存（lowvram）推理能力与 entropack 优化。其中 entropack 具体技术细节需结合代码进一步确认，但可推断为一种面向内存/效率的压缩或打包机制。

## 二、关键变更点与项目方向的关系
- **扩展模型生态**：DiffSynth-Studio 作为扩散模型合成工作台，其核心竞争力在于广泛兼容各类图像/视频生成模型。新增 Moss-Image 支持，延续了项目"一站式集成多模型"的主线方向，进一步丰富可选模型矩阵。
- **降低部署门槛**：lowvram 推理与 entropack 属于典型的"易用性工程"，旨在让资源受限用户（如消费级显卡）也能运行新模型。这与开源生成式 AI 工具追求"普惠化"的趋势一致。
- **配套文档同步**：两个提交均包含 README/docs 更新，说明项目在扩展功能的同时注重使用引导，有利于新模型的快速落地。

## 三、对项目的影响和潜在意义
- **扩大用户覆盖面**：低显存支持可显著降低尝试 Moss-Image 的硬件门槛，有助于吸引更多中小团队与个人开发者。
- **增强模型一致性**：将 lowvram/entropack 抽象为可复用能力（而非仅针对 Moss-Image），未来有望推广到其他模型，形成统一的资源优化层。
- **社区活跃度信号**：连续两个相邻 PR 从"基础支持"到"性能/易用性增强"的递进，反映出贡献者对模型集成质量的持续打磨。

## 四、值得关注的技术点
1. **lowvram 推理实现**：通常涉及权重分片、激活值 offload、混合精度等手段的组合，值得考察其在 Moss-Image 上的具体策略及显存占用改善幅度。
2. **entropack 机制**：命名上类似"entropy packing"，可能与潜在空间压缩或模型权重编码相关，若能有效降低模型体积或传输开销，对边缘部署场景具有参考价值。
3. **模型接入的工程范式**：如何将新模型以最小侵入方式纳入 DiffSynth 现有抽象（pipeline、调度器、VAE 等组件），可作为后续接入其他模型的参考模板。

## 五、结合项目背景的影响判断
DiffSynth-Studio 具有 PyPI 包分发与 Trendshift 收录，属于社区关注度较高的活跃开源项目。本次提交通过"新增模型 + 资源优化"双管齐下，既巩固了其模型支持广度这一核心卖点，又通过易用性改进扩大了潜在用户基数。尤其是将 lowvram 能力作为模型支持的一部分同步交付，体现了项目对"可运行性"的重视，而非仅停留在"能加载"。长期看，这种将模型接入与资源优化绑定的模式，有助于 DiffSynth-Studio 在同类扩散模型工具中形成"开箱即用、门槛友好"的差异化定位。

整体而言，这两组提交是项目生态扩展与工程化打磨的正常演进，虽无颠覆性技术突破，但对维持社区贡献节奏、提升模型覆盖质量具有积极意义。

## 详细提交记录

### [681c456](https://github.com/modelscope/DiffSynth-Studio/commit/681c456a3e8cf9e17cf2cb9a35297718ed4270ca)

- **作者**: Hong Zhang
- **时间**: 2026-10-19T12:30:51Z
- **提交信息**: support lowvram inference and entropack for moss-image (#1764)

* support lowvram inference and entropack for moss

* update readme

### [dcb6d0b](https://github.com/modelscope/DiffSynth-Studio/commit/dcb6d0b011742d3afe916773bdc26d8ab27cd966)

- **作者**: Jinyan Ye
- **时间**: 2026-10-19T08:53:23Z
- **提交信息**: support Moss-Image (#1763)

* support moss_image

* update docs

* fix

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37447
- **最后更新**: 2026-10-20T00:48:06Z

## 提交统计

- **昨日提交总数**: 47
- **提交者数量**: 33
- **主要提交者**: jacky.cheng, Shangming Cai, Liu Ke

## AI分析总结

# SGLang 昨日提交分析（第 1/1 批，共 47 条）

## 1. 主要更新类型分布

- **Bug 修复**：约 20 条，占最大比重
- **性能优化**：约 10 条，集中于 DeepSeek-v4/v4.1、AMD、diffusion 等路径
- **功能新增**：约 8 条，聚焦路由（sgl-router）、NVIDIA megakernel、MoE 分页专家
- **CI/测试**：约 7 条，涉及 Python 3.10 迁移、NPU 精确测试选择等
- **文档更新**：约 4 条，主要是 cookbook 和 TPU 指南
- **重构**：1 组（MoE shared-expert 配置作用域化）

## 2. 关键变更点及与项目方向的关系

SGLang 的核心目标是**大模型与多模态模型的高性能推理**，本批提交高度契合这一方向：

- **MoE 推理正确性与可维护性**：连续 4 条重构/修复将 shared-expert 配置按模型隔离、拆分 `num_fused_shared_experts` 的双重语义、修正每 rank shared-slot 路由的重归一化与 `routed_scaling_factor` 的重复计数问题。这是对 MoE 这一热点模型架构的深度治理，为后续支持更多 MoE 模型（如 DeepSeek 系列）扫清技术债务。
- **DeepSeek-v4.1 性能攻坚**：多条优化提交移除请求窗口（request-window）标签重置和 SWA 历史检查中的 host sync、按 GPU 尺寸调整 masked silu-mul-quant 网格、在任意上下文长度回放可断开的 prefill CUDA graph、解码尾图在 DP attention 下运行。这表明项目正在针对旗舰模型做端到端的延迟与吞吐优化，减少 CPU-GPU 同步是关键手段。
- **PD 分离（Prefill-Decode 分离）生态完善**：sgl-router 新增 `--decode-dispatch-limit` 与 `--pd-stream-after-prefill`，配合模型网关根据 KV 到达位置选择解码 worker，并修复被取消前缀查询突发时 kv-indexer 连接保持问题。这强化了 SGLang 在大规模分布式推理场景下的调度能力。
- **新硬件与新执行路径**：NVIDIA megakernel 插件层、分页专家（paged-experts）支持 VRAM 装不下的 MoE 权重、TPU 指南引入 SGLang-TorchTPU、AMD ROCm/gfx1250/UMB P HiCache 相关修复、NPU 精确测试选择。体现项目"多后端"战略的持续推进。

## 3. 对项目的影响和潜在意义

- MoE 修复消除潜在的数值错误与配置歧义，**直接提升模型输出正确性**，降低下游用户踩坑概率。
- DeepSeek-v4.1 系列优化减少同步开销，**对实际部署的延迟尾部（P99）和吞吐有实质收益**。
- paged-experts 让超大 MoE 模型可在有限 VRAM 上服务，**扩展了 SGLang 的可服务模型规模边界**。
- PD 调度增强使多租户/长上下文场景下的资源利用率更高，**巩固 SGLang 在生产级推理服务中的竞争力**。
- 一批 int32 溢出、CUDA graph、VAE 等修复表明项目在处理极端规模（如 37,451 tokens）和多模态（diffusion）路径上的**成熟度稳步提升**。

## 4. 值得关注的技术点

- **host sync 消除范式**：多条提交一致地用"无 host sync"方式重置/检查请求窗口状态，是 GPU 异步化编程的典型案例，值得作为性能优化模板。
- **分页专家（paged-experts）**：将 KV cache 的分页思想推广到专家权重，是 MoE 推理领域的重要方向。
- **int32 溢出边界**：attn_residual 与 Qwen-Image VAE 的溢出修复说明高 token 数场景正成为常态，需要全链路审视数据类型。
- **AI 协作痕迹**：多个提交由 Claude Opus/Cursor 等 AI 代理共同完成，反映该项目已深度采用 AI 辅助开发流程。

## 5. 对项目整体发展的意义

基于 README，SGLang 定位为快速推理引擎。本批提交显示项目正处于**"横向扩后端（NPU/AMD/TPU/NVIDIA megakernel）+ 纵向榨性能（DeepSeek-v4.1）+ 打磨生产可靠性（PD 调度、MoE 正确性、极端规模溢出）"三线并进**的阶段。MoE 治理与分页专家为下一个模型浪潮做准备，PD 分离调度强化其在数据中心级部署的护城河，而大量修复与 CI 收紧则在为更大规模的社区协作和长期演进夯实基础。这些工作共同支撑项目在推理性能与功能覆盖上继续保持第一梯队的位置。

## 详细提交记录

### [6b90e57](https://github.com/sgl-project/sglang/commit/6b90e5716d4246d2a772bef06c7ddecceb6ac6ed)

- **作者**: Cheng Wan
- **时间**: 2026-10-19T23:59:37Z
- **提交信息**: [Refactor] moe: Scope shared-expert configuration to each model (#44913)

### [964ab2b](https://github.com/sgl-project/sglang/commit/964ab2b280ee59995bd21f8514d1ee6a2b517a1f)

- **作者**: Cheng Wan
- **时间**: 2026-10-19T23:57:15Z
- **提交信息**: [Refactor] moe: Split the two meanings of num_fused_shared_experts (#44912)

### [48ea486](https://github.com/sgl-project/sglang/commit/48ea4869280dfaace60840b5c967ee00a5598968)

- **作者**: Cheng Wan
- **时间**: 2026-10-19T23:56:21Z
- **提交信息**: [Fix] moe: Renormalize per-rank shared-slot routing over routed experts only (#44904)

### [3a059de](https://github.com/sgl-project/sglang/commit/3a059de94c1642b35441cb16cd365b07fbae6990)

- **作者**: Cheng Wan
- **时间**: 2026-10-19T23:54:27Z
- **提交信息**: [Fix] moe: Count routed_scaling_factor once when top-k folds it (#44901)

### [28448a8](https://github.com/sgl-project/sglang/commit/28448a86d47eb49a3c8e47dca52fe25cc95425d8)

- **作者**: Qiaolin Yu
- **时间**: 2026-10-19T22:57:22Z
- **提交信息**: [Doc] cookbook: Default Qwen3.8-Flash-Next datacenter recipes to FP8 KV cache and QSA indexer (#45245)

Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [1238edd](https://github.com/sgl-project/sglang/commit/1238edd954b7f255e7e8e53246b8493bcacef2c6)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-19T22:45:17Z
- **提交信息**: [Perf] deepseek-v4.1: Reset request-window tags without a host sync (#45247)

### [9a94940](https://github.com/sgl-project/sglang/commit/9a949403f12af57d8a0a5823ee51ace23d923171)

- **作者**: Mingyi
- **时间**: 2026-10-19T22:34:47Z
- **提交信息**: [Doc] tpu: Introduce SGLang-TorchTPU in README and TPU guide (#45246)

### [ab258b6](https://github.com/sgl-project/sglang/commit/ab258b6453a256b1eab5a7e16b1ad5d6e38a197c)

- **作者**: Liu Ke
- **时间**: 2026-10-19T22:29:35Z
- **提交信息**: [Fix] symm-mem: Name the window registration in the scheduler watchdog dump (#44681)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [05d7f7a](https://github.com/sgl-project/sglang/commit/05d7f7a166e2b4dd5a9e0445fd5993ea1a60d6ba)

- **作者**: Gabriel Wu
- **时间**: 2026-10-19T22:27:52Z
- **提交信息**: [Fix] attention: Honor selected FlashAttention implementation (#33007)

### [49766a7](https://github.com/sgl-project/sglang/commit/49766a74f9de2b5cdd3c11269671329f3d716ac2)

- **作者**: Jiuqiang Tang
- **时间**: 2026-10-19T22:12:12Z
- **提交信息**: [Fix] attn_residual: int64 program ids in the score/combine kernels (int32 overflow at 37,451 tokens) (#43438)

### [80ea5ee](https://github.com/sgl-project/sglang/commit/80ea5ee638489834af51684622d3625bcf9e8cdf)

- **作者**: 0z5a
- **时间**: 2026-10-19T21:48:37Z
- **提交信息**: [Fix] dLLM: Preserve prompt tails and literal mask tokens across prefix reuse (#39592)

Signed-off-by: 0z5a <dezhen.lu@student.uni-tuebingen.de>
Co-authored-by: Richard Wang <wangrichard08@gmail.com>

### [fdc2dd0](https://github.com/sgl-project/sglang/commit/fdc2dd0d05df2b18040b09c442c5c44af7b25dad)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-19T21:44:01Z
- **提交信息**: [Perf] dspark: Make the prefill SWA valid-from update sync-free (#45234)

### [81ac153](https://github.com/sgl-project/sglang/commit/81ac15391ca6010f6d686333c850cc361e0bf123)

- **作者**: Liu Ke
- **时间**: 2026-10-19T21:36:16Z
- **提交信息**: [Fix] metrics: record HTTP request metrics in tokenizer workers (#44663)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [7656ea0](https://github.com/sgl-project/sglang/commit/7656ea0e7487a3b828b81f21f88e9ee4ed55f6d0)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-19T21:29:00Z
- **提交信息**: [CI] python: Move the remaining CUDA build paths off Python 3.10 (#44393)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [b20cb36](https://github.com/sgl-project/sglang/commit/b20cb3665d5bccc2f6a988f09701bf29a3d79b82)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-19T21:20:32Z
- **提交信息**: [CI] radix-cache: Drop redundant unified radix cache unit tests (#45232)

### [642a671](https://github.com/sgl-project/sglang/commit/642a671c300babc061b0200c69b1c9882465696d)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-19T20:40:02Z
- **提交信息**: [CI] tests: Re-enable muse spark B300 PD coverage (#44975)

### [8b1d1e0](https://github.com/sgl-project/sglang/commit/8b1d1e0d74d2531141fb18db460b87852569b365)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-19T20:34:52Z
- **提交信息**: [Perf] deepseek-v4.1: Check request-window SWA history without per-layer host syncs (#45223)

### [aaa9388](https://github.com/sgl-project/sglang/commit/aaa9388c91128156a57f4f7ba6abe7457ad62518)

- **作者**: Rain Jiang
- **时间**: 2026-10-19T20:16:54Z
- **提交信息**: [Fix] kda: Keep FlashInfer prefill off its grouped kernel's bf16/flat-dt_bias contract (#45018)

### [f1a2ee7](https://github.com/sgl-project/sglang/commit/f1a2ee763d57d2066f7adde3dcbcb7fefe936326)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-19T20:02:07Z
- **提交信息**: [Perf] deepseek-v4.1: Run decoder replay tail graphs in prefill-graph steps and under DP attention (#45107)

### [5385866](https://github.com/sgl-project/sglang/commit/5385866108b86712e2114d1f06b559d550900ebd)

- **作者**: Qiaolin Yu
- **时间**: 2026-10-19T19:52:36Z
- **提交信息**: [Fix] moe: gated NVFP4 MoE intermediate alignment for FlashInfer TRTLLM (#44138)

### [9ab74b8](https://github.com/sgl-project/sglang/commit/9ab74b85179464277b5015a54c4a494ece24bcfe)

- **作者**: Qiaolin Yu
- **时间**: 2026-10-19T19:41:39Z
- **提交信息**: [Fix] Qwen3.8next: Stop retaining per-size PLE outputs in breakable prefill CUDA graphs (#44150)

### [0ce41c5](https://github.com/sgl-project/sglang/commit/0ce41c5a06f829bb74e3d582c82d8d51837742df)

- **作者**: Jooman
- **时间**: 2026-10-19T18:55:04Z
- **提交信息**: [Fix] PD: retraction restores racing the in-flight decode forward (#42702)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Zhiqiang Xie <xiezhq@stanford.edu>

### [722669e](https://github.com/sgl-project/sglang/commit/722669e6066fec2266e8a7e2f6bb738709a2f53f)

- **作者**: YAMY
- **时间**: 2026-10-19T18:54:44Z
- **提交信息**: [Feat] [NVIDIA] megakernels: Add --enable-nvidia-megakernel and a layer for NVIDIA megakernel plugins (#44945)

### [678913a](https://github.com/sgl-project/sglang/commit/678913a0f029394ad1f4ee64d1439421e9ea56ef)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-19T18:16:21Z
- **提交信息**: [Feat] sgl-model-gateway: Add --decode-dispatch-limit to pick PD decode workers near KV arrival (#44689)

### [80b86db](https://github.com/sgl-project/sglang/commit/80b86dbecb0831d4088dc79eb5e1421ff1d06412)

- **作者**: jacky.cheng
- **时间**: 2026-10-19T18:07:37Z
- **提交信息**: [Fix] [AMD] diffusion: Accept residual and skip_bias in the ROCm Conv3d-to-Conv2d VAE patch (#44672)

### [5ed306b](https://github.com/sgl-project/sglang/commit/5ed306bd69be18ce97f8e9d57721da7e05bd2f9f)

- **作者**: jacky.cheng
- **时间**: 2026-10-19T17:36:28Z
- **提交信息**: [Fix] [AMD] diffusion: Keep gfx1250 FlyDSL BF16 attention out of torch.compile (#44671)

### [4ef9765](https://github.com/sgl-project/sglang/commit/4ef9765e76be4952d25f6b8ed160600aefc0757f)

- **作者**: lixiufei-leo
- **时间**: 2026-10-19T17:13:25Z
- **提交信息**: [Feat] sgl-router: Add --pd-stream-after-prefill (#45102)

Co-authored-by: Xiufei Li <294029388+lixiufei-leo@users.noreply.github.com>

### [716c915](https://github.com/sgl-project/sglang/commit/716c9151f217a640affac40d015c9749a7f2c79a)

- **作者**: chenyang08056032
- **时间**: 2026-10-19T16:57:27Z
- **提交信息**: [CI] [NPU] npu-coverage: run only coverage-recommended tests on PRs (precise test selection) (#44019)

### [8e7601a](https://github.com/sgl-project/sglang/commit/8e7601ae4a48c1127afd1bcdccf0a0ad61dbf043)

- **作者**: Jan Schalkamp
- **时间**: 2026-10-19T15:10:04Z
- **提交信息**: [Feat] paged-experts: Serve MoE models whose weights do not fit VRAM (#42557)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [806e742](https://github.com/sgl-project/sglang/commit/806e7423af8c2ab3dd364f1501b5d3f69e1d83d5)

- **作者**: Monishver
- **时间**: 2026-10-19T15:07:12Z
- **提交信息**: [Perf] deepseek_v4: size the masked silu-mul-quant grid to the GPU, not the padded capacity (#44618)

Signed-off-by: Monishver Chandrasekaran <monishverchandrasekaran@gmail.com>

### [c04f9a6](https://github.com/sgl-project/sglang/commit/c04f9a61f03f60a5b49bbd6985463859a2a43b56)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-19T15:04:26Z
- **提交信息**: [Fix] diffusion: Fix VMoBA chunk selection bugs (#44286)

### [7c4cc5a](https://github.com/sgl-project/sglang/commit/7c4cc5a51c8f4b5ec8549b8dcb1ee69e92102f1a)

- **作者**: Siliang Chen
- **时间**: 2026-10-19T15:03:27Z
- **提交信息**: [Perf] [AMD] attention: Spread uneven Triton decode batches across XCDs (#41229)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [96ba108](https://github.com/sgl-project/sglang/commit/96ba1080728f7f9f08a1054d8278a0de63bd6c75)

- **作者**: Sam Shleifer
- **时间**: 2026-10-19T14:54:08Z
- **提交信息**: [Fix] dsa-eagle-topk: Copy token keys and scales when relocating index cache (#44564)

### [4176065](https://github.com/sgl-project/sglang/commit/417606527d0059fbbb5f87b6eb2b8508f5647433)

- **作者**: Sam Shleifer
- **时间**: 2026-10-19T14:41:53Z
- **提交信息**: [Fix] nvfp4: Own streamed tensors while waiting for paired weights (#44500)

### [8c4680c](https://github.com/sgl-project/sglang/commit/8c4680cb65fdcf57f6b9052c909918e2d015be04)

- **作者**: pllimax
- **时间**: 2026-10-19T14:29:30Z
- **提交信息**: [CI] npu: Move llada2-mini FDFO test to full test (#45153)

### [62cee1b](https://github.com/sgl-project/sglang/commit/62cee1b15c22350b17a9256fc6ad5777feb2ec70)

- **作者**: lixiufei-leo
- **时间**: 2026-10-19T13:41:03Z
- **提交信息**: [Fix] sgl-router: Keep the kv-indexer connection through bursts of cancelled prefix queries (#45100)

Co-authored-by: Xiufei Li <294029388+lixiufei-leo@users.noreply.github.com>

### [ed0b8f4](https://github.com/sgl-project/sglang/commit/ed0b8f433f887995b1ce361b15aaf9f6ca93483f)

- **作者**: zhaozx-cn
- **时间**: 2026-10-19T11:30:41Z
- **提交信息**: [Fix] [NPU] kimi-k3: skip fused gmm1 for situ activation in Ascend runner (#43837)

### [0025f93](https://github.com/sgl-project/sglang/commit/0025f9394421451aa09ec192a4a6e7928e14736b)

- **作者**: Shangming Cai
- **时间**: 2026-10-19T10:24:17Z
- **提交信息**: [Fix] sgl-router: Refuse prefill workers that cannot compute before bootstrap under --decode-dispatch-limit (#45120)

### [e45cbce](https://github.com/sgl-project/sglang/commit/e45cbce599b56fecab14b6d36fe2c1191e13a523)

- **作者**: Quanli Li
- **时间**: 2026-10-19T10:01:02Z
- **提交信息**: [Fix] diffusion: Prevent int32 overflow in Qwen-Image-2.1-Turbo VAE RMSNorm (#45118)

Co-authored-by: 全力 <liquanli.lql@antgroup.com>

### [a90e9c5](https://github.com/sgl-project/sglang/commit/a90e9c5dd8973cdb84af4ff6154c7b4958083b31)

- **作者**: Niko Ma
- **时间**: 2026-10-19T08:37:50Z
- **提交信息**: [Fix] [AMD] mhc: Bound the Triton fused post+pre buffer cache (#44443)

Co-authored-by: inkcherry <mingzhi.liu@amd.com>

### [8111841](https://github.com/sgl-project/sglang/commit/8111841103ca44bec779289c1da8d29cec55cc0a)

- **作者**: Yizheng Jiao
- **时间**: 2026-10-19T08:29:14Z
- **提交信息**: [Perf] deepseek-v4.1: Replay the breakable prefill CUDA graph at any context length (#43733)

Co-authored-by: Oasis-Git <ayw.sirius19@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [33dd8f6](https://github.com/sgl-project/sglang/commit/33dd8f6a2eee41d4ad44fb397cf9b794df07aa54)

- **作者**: elvischenv
- **时间**: 2026-10-19T08:24:41Z
- **提交信息**: [Fix] hybrid-SSM: DP attention failures at low concurrency (#34535)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [5d9c956](https://github.com/sgl-project/sglang/commit/5d9c956f8e309a2f60bfd4472bb25447e9b63129)

- **作者**: Thomas Wang
- **时间**: 2026-10-19T08:11:11Z
- **提交信息**: [Doc] [AMD] dsv4: Update amd cookbook 1016 (#45070)

### [af9bb2a](https://github.com/sgl-project/sglang/commit/af9bb2a32d4a313d20a629ac1b2cb8e6ef245b95)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-19T07:24:08Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches with twelve open InferenceX PRs (#45111)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3d58877](https://github.com/sgl-project/sglang/commit/3d588779e1c8001c1596c1662af785ead61d355c)

- **作者**: Bingxu Chen
- **时间**: 2026-10-19T07:23:52Z
- **提交信息**: [CI] [AMD] test: Run UMBP HiCache E2E through standalone DRAM server (#40674)

### [f86a04a](https://github.com/sgl-project/sglang/commit/f86a04a3314c673e3a9025451d5a6467213ff353)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-19T07:11:40Z
- **提交信息**: [Feat] sgl-router: Add --decode-dispatch-limit to pick decode DP ranks near KV arrival (#44402)

### [a5117be](https://github.com/sgl-project/sglang/commit/a5117beb11c5e3f825992524bfbc75f50f93ec65)

- **作者**: leonardHONG
- **时间**: 2026-10-19T07:07:13Z
- **提交信息**: [Perf] mhc: Parallelize small-batch post across hidden tiles (#44906)

Co-authored-by: leonardHONG <178642616+leonardHONG@users.noreply.github.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1290
- **最后更新**: 2026-10-19T06:50:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 94158
- **最后更新**: 2026-10-20T01:04:43Z

## 提交统计

- **昨日提交总数**: 48
- **提交者数量**: 43
- **主要提交者**: Isotr0py, Rohit Nagraj, Niansia

## AI分析总结

## vLLM 昨日提交总结（共48条）

### 1. 主要更新类型
- **Bug修复最多**（约20条）：涵盖调度器、采样器、工具解析、KV缓存、前端等领域
- **CI/测试优化**（约10条）：AMD镜像调整、Blackwell/Rubin适配、pre-commit检查
- **性能优化**（约6条）：MoE、SPLADE、注意力内核等
- **文档更新**（约6条）：新模型部署指南、验证模型清单
- **新功能支持**：Step-5 Preview模型、MOSS-Transcribe-Diarize热词、NIXL sleep模式

### 2. 关键变更点
- **DeepSeek-V4.1 持续打磨**：修复encoder/renderer与参考编码对齐、MegaAttn优化、Engram注入、MegaMoE MXFP4显式启用——显示该模型是当前重点支持对象
- **硬件平台扩展**：新增SM107a（DeepEP）、Blackwell/Rubin的MoE单测适配、ROCm 10镜像升级至torch 2.13，以及多条AMD/ITER内核优化，体现对NVIDIA新卡和AMD生态的双线投入
- **CI分流**：最重的4xL4测试改为仅nightly运行但保留AMD镜像在PR上，平衡PR速度与覆盖度
- **安全加固**：新增pre-commit检查，禁止硬编码 `trust_remote_code=True`
- **投机解码**：FLy（熵门控延迟验证）、EAGLE+SWA尾部保留修复，持续完善spec decode

### 3. 对项目的影响
- 大量边界情况修复（split top-p大logits、多行JSON工具参数、调度优先级、auto截断等）提升生产环境可靠性
- 权重缓存修复（RoPE参数入IPC键、DP守护进程键对齐）改善多进程部署正确性
- 性能小步快跑：SPLADE提升3.6–7.8%、MoE top-k门控启用PDL、辅助输出避免重复扫描

### 4. 值得关注的技术点
- **cudnn-frontend>=1.31.0强制升级**：修复CUDA graph重放未加载内核的隐患，可能影响用户依赖版本
- **persistent_topk float4尾部lane修复**：内核级精度边界问题
- **NIXL pull connector支持sleep mode**：服务成本优化（KV offload场景）相关
- **systemone混合模型共享前缀预填充**：与项目"降低LLM服务成本"的使命直接呼应

### 5. 对项目发展方向的影响
README强调"Easy, fast, and cheap LLM serving"。本次提交印证三大方向：(1) **Fast**——持续的内核级与调度级优化；(2) **Cheap**——sleep mode、KV offload、投机解码提升吞吐降低成本；(3) **Easy**——完善文档（DeepSeek/Kimi/Step-5部署指南）与多硬件支持，降低用户接入门槛。同时，AI辅助开发（Claude/Codex/各类agent署名）在提交中占比极高，预示vLLM社区工作流已深度拥抱AI协作。

## 详细提交记录

### [53172fa](https://github.com/vllm-project/vllm/commit/53172fa72ef8c775cd294273b2e7b0c7c21240f2)

- **作者**: Harry Mellor
- **时间**: 2026-10-19T23:40:45Z
- **提交信息**: [CI] Bump Transformers version to 5.20.0 (#61983)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8c60cf0](https://github.com/vllm-project/vllm/commit/8c60cf07b3df3b289c310fbd45a382a10709d9ab)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-19T22:19:33Z
- **提交信息**: [CI] Keep the AMD mirrors of the nightly-only 4xL4 steps on PRs (#62567)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0b7ae8f](https://github.com/vllm-project/vllm/commit/0b7ae8f53204efb9c1c873d0da2ee06b03faf51c)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-19T22:14:49Z
- **提交信息**: [CI] Run the heaviest 4xL4 steps nightly only (#62564)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5fd6268](https://github.com/vllm-project/vllm/commit/5fd62688ffe995c0c11c8708fe51dbff53235b74)

- **作者**: yuvalluria
- **时间**: 2026-10-19T21:37:31Z
- **提交信息**: [Docs] Add Gemma-2, Granite SWA, Qwen3-0.6B to batch invariance validated models (#61254)

Signed-off-by: Yuval Luria <yluria@redhat.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5f446bf](https://github.com/vllm-project/vllm/commit/5f446bfb84b8cbc6a8a04f4be11d24b12a2dddba)

- **作者**: Yuchen Wang
- **时间**: 2026-10-19T21:32:22Z
- **提交信息**: docs: explain parser boundary tokens in custom grammars (#58219)

Signed-off-by: Yuchen Wang <93700456+yuchenwang3@users.noreply.github.com>

### [04631c4](https://github.com/vllm-project/vllm/commit/04631c4915d6c14ea17bbf77d9dbaccbe8a8788f)

- **作者**: Mritunjay Kumar Sharma
- **时间**: 2026-10-19T21:19:35Z
- **提交信息**: [Security][CI/Build] Add pre-commit check for hardcoded trust_remote_code=True (#62547)

Signed-off-by: Mritunjay Sharma <mritunjaysharma394@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3ff10dd](https://github.com/vllm-project/vllm/commit/3ff10ddeb0b77c469c62d9988742d2faa8e4c1f5)

- **作者**: Rohit Nagraj
- **时间**: 2026-10-19T20:35:47Z
- **提交信息**: [Doc] Document DeepSeek-V4.1-Flash Dynamo sidecar serving / 记录 DeepSeek-V4.1-Flash Dynamo sidecar 部署 (#62534)

Signed-off-by: Rohit Pujar Nagraj <rpujarnagraj@nvidia.com>
Signed-off-by: Rohit Nagraj <rohitnagraj.99@gmail.com>
Co-authored-by: Ankur Singh <as.ankursingh3.1@gmail.com>

### [e1f3141](https://github.com/vllm-project/vllm/commit/e1f3141647b93f12ac2ffa95f0cf7699fcaca21f)

- **作者**: Stu Cao
- **时间**: 2026-10-19T20:25:36Z
- **提交信息**: [Bugfix][V1] Null sliding-window block-table entries below the window (#60767)

Signed-off-by: Stu Cao <stu@primeintellect.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: Giancarlo Delfin <32987265+TheEpicDolphin@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b7701fc](https://github.com/vllm-project/vllm/commit/b7701fc3e4b8616353e06b27c95a33463f1f9aa7)

- **作者**: x41lakazam
- **时间**: 2026-10-19T20:21:43Z
- **提交信息**: [Bugfix][Test] Synchronise ranks before the profiled call in profile_… (#57001)

Signed-off-by: Eyal Chocron <x41lakazam@gmail.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: bnellnm <49004751+bnellnm@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8a1c02e](https://github.com/vllm-project/vllm/commit/8a1c02efca9bb0660f70b404e1ac4cb0629144ae)

- **作者**: Yicong Wang
- **时间**: 2026-10-19T19:49:32Z
- **提交信息**: [Bugfix][DeepSeek V4.1] Inject Engram at pipeline stage entry (#62208)

Signed-off-by: wangyicong <wangyicong@bytedance.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b9df898](https://github.com/vllm-project/vllm/commit/b9df8980fb7b117405fb198ffb869ad82cf44ca3)

- **作者**: John Calderon
- **时间**: 2026-10-19T19:46:34Z
- **提交信息**: [CI][Tests] Add SM107a to DeepEP build (#61442)

Signed-off-by: John Calderon <jcalderon@nvidia.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [b188771](https://github.com/vllm-project/vllm/commit/b188771f98dc56bb021a39714fcdc27f88e0e2f9)

- **作者**: Ankur Singh
- **时间**: 2026-10-19T19:40:28Z
- **提交信息**: [Doc] Document Kimi-K3 GB300 disaggregated AgentX profile (#62528)

Signed-off-by: Ankur Singh <ankusingh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [fdb9533](https://github.com/vllm-project/vllm/commit/fdb953365c589b61abfc59ca4f657efa25e03c73)

- **作者**: John Calderon
- **时间**: 2026-10-19T19:35:17Z
- **提交信息**: [CI][Unit Test] Patch MoE layer unit tests for Blackwell and Rubin (#62090)

Signed-off-by: John Calderon <jcalderon@nvidia.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [3c9beb8](https://github.com/vllm-project/vllm/commit/3c9beb82d1a92eb5a84cca4408a0a1b479d4dd03)

- **作者**: Hanlin Bi
- **时间**: 2026-10-19T19:17:28Z
- **提交信息**: [Perf] Enable PDL for fused MoE top-k gating (#59737)

Signed-off-by: Hanlin Bi <hanlinb@nvidia.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [b439421](https://github.com/vllm-project/vllm/commit/b439421f11912305559235937134682a28eb47bc)

- **作者**: Aarushi Jain
- **时间**: 2026-10-19T18:51:06Z
- **提交信息**: [CI][ROCm] Raise data_parallel_offline.py --timeout in AMD Torchrun + Examples (#62520)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>

### [c8fbb79](https://github.com/vllm-project/vllm/commit/c8fbb79406c85fb6d8b439b38105706cc93e05ce)

- **作者**: Divakar Verma
- **时间**: 2026-10-19T18:49:51Z
- **提交信息**: [ROCm][MoE] Add AITER MXFP4 W4A16/W4A4 modular-kernel test coverage (#60886)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3b05805](https://github.com/vllm-project/vllm/commit/3b05805d475b22ed4be38bbce883e667156bdd23)

- **作者**: Isotr0py
- **时间**: 2026-10-19T18:45:37Z
- **提交信息**: [Misc] Fix failing weight cache RoPE test on main (#62508)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [aa3564c](https://github.com/vllm-project/vllm/commit/aa3564ceefbd605f1d28238fa0fbbb964201c6b8)

- **作者**: stefankoncarevic
- **时间**: 2026-10-19T17:00:21Z
- **提交信息**: [Bugfix][Test] Stop requesting capfd in the subprocess weight cache test (#62461)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [bde4d00](https://github.com/vllm-project/vllm/commit/bde4d001130e5112d984ba99f0546e22c09e1a89)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-19T16:13:55Z
- **提交信息**: [Bugfix][Kernel] persistent_topk: don't select float4 tail lanes past the row length (#62467)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a9104fd](https://github.com/vllm-project/vllm/commit/a9104fd3db6f9aebbd3687b4055fef0f3e5de30d)

- **作者**: Taneem Ibrahim
- **时间**: 2026-10-19T16:08:36Z
- **提交信息**: [Pooling] Improve SPLADE throughput 3.6% to 7.8%  (#62250)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [e347836](https://github.com/vllm-project/vllm/commit/e347836d68befbb77e94a1e9d36ae338613149fa)

- **作者**: Niansia
- **时间**: 2026-10-19T16:07:16Z
- **提交信息**: [Bugfix][Tool Parser] Parse multi-line JSON arguments in the DeepSeek V3 and V3.1 parsers (#60362)

Signed-off-by: niansia <niansia930202@gmail.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [5caabdb](https://github.com/vllm-project/vllm/commit/5caabdbb65d61222354501edbe76294dfe7e1eb5)

- **作者**: wang.yuqi
- **时间**: 2026-10-19T16:00:10Z
- **提交信息**: [Frontend] Consolidate startup utils. (#62390)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [a3cee21](https://github.com/vllm-project/vllm/commit/a3cee21d0bf986b519b48f13a3e7fa3814cbabca)

- **作者**: Anton Peganov
- **时间**: 2026-10-19T15:48:13Z
- **提交信息**: [Bugfix] Require cudnn-frontend >=1.31.0: cuDNN could replay an unloaded kernel from a CUDA graph (#61465)

Signed-off-by: Anton Peganov <apeganov@nvidia.com>

### [afe2183](https://github.com/vllm-project/vllm/commit/afe2183f2bab35988de0e6a506a5694b3cc1ef34)

- **作者**: aoshen02
- **时间**: 2026-10-19T15:44:34Z
- **提交信息**: [KV Connector] Support sleep mode with the NIXL pull connector (#59635)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: Dakai An <77474977+andakai@users.noreply.github.com>

### [3aad539](https://github.com/vllm-project/vllm/commit/3aad5392abe2cb7268538e287a953c618e5a76d2)

- **作者**: WaylonLiu
- **时间**: 2026-10-19T15:29:20Z
- **提交信息**: [Model] Support hotwords for MOSS-Transcribe-Diarize (#62329)

Signed-off-by: WaylonLiu <221707432+lzwwaylon@users.noreply.github.com>

### [ddefe40](https://github.com/vllm-project/vllm/commit/ddefe40e16dda6cd3a0ba1b5c83e1ee9f18187fc)

- **作者**: Robert Shaw
- **时间**: 2026-10-19T15:08:41Z
- **提交信息**: [Bugfix][Frontend] Match DeepSeek-V4.1 encoder to the 1017 reference encoding (#62199)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b048630](https://github.com/vllm-project/vllm/commit/b048630a195d8469b37c2897f646aeaf8d6ef91a)

- **作者**: Chi McIsaac
- **时间**: 2026-10-19T15:08:25Z
- **提交信息**: [Bugfix] Size the HiSparse hot buffer from the rounded sparse top-k width (#60805)

Signed-off-by: Chi McIsaac <chi@primeintellect.ai>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [b29be52](https://github.com/vllm-project/vllm/commit/b29be5235725efa78412d33a12baf91b75bc0085)

- **作者**: aoshen02
- **时间**: 2026-10-19T14:59:50Z
- **提交信息**: [Perf][AuxOutput] Do not rescan referenced keys in the routed-experts store (#62392)

Signed-off-by: faresobeid <111092724+faresobeid@users.noreply.github.com>
Signed-off-by: Ao Shen <aoshen@inferact.ai>
Co-authored-by: faresobeid <111092724+faresobeid@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2cea893](https://github.com/vllm-project/vllm/commit/2cea893821861c1007b3c7f1da44f9774bb0c18c)

- **作者**: Robert Shaw
- **时间**: 2026-10-19T14:57:03Z
- **提交信息**: [Bugfix][Rust Frontend] Match DeepSeek-V4.1 renderer to the 1017 reference encoding (#62200)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4bd75e9](https://github.com/vllm-project/vllm/commit/4bd75e952a9f423742223c97c8cc9fc6db362950)

- **作者**: liranschour
- **时间**: 2026-10-19T14:31:50Z
- **提交信息**: [Bugfix][KV Offload][P2P] Report NIXL submission failures and escalate persistent faults to session teardown (#60374)

Signed-off-by: Liran Schour <lirans@il.ibm.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [973dbf8](https://github.com/vllm-project/vllm/commit/973dbf8071f8bdd6dd7eb2d6ee0da7cbe6a93670)

- **作者**: Chun Fang
- **时间**: 2026-10-19T14:18:01Z
- **提交信息**: [Doc][ROCm] Align Kimi-K3 MI355X recipe with InferenceX #4215 (#62273)

Signed-off-by: Chun Fang <chun.fang@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>

### [2aa5080](https://github.com/vllm-project/vllm/commit/2aa5080fa0454b0f7bf107c85ffb149c5ecbcb83)

- **作者**: bzsuni
- **时间**: 2026-10-19T14:07:39Z
- **提交信息**: [Bugfix][Weight Cache] Include RoPE parameters in IPC cache key (#60994)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [81f7c69](https://github.com/vllm-project/vllm/commit/81f7c69577433b938ee16539020792dae37c7d0c)

- **作者**: Lucky S Lodhi
- **时间**: 2026-10-19T13:25:33Z
- **提交信息**: [Bugfix][Tool Calling] Tool parser non-streaming parse drops post-tool-call text that streaming returns (#56270)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [a608b6e](https://github.com/vllm-project/vllm/commit/a608b6e6e05f4b309f77981f010e93c2caa1c677)

- **作者**: Jared Wen
- **时间**: 2026-10-19T12:38:18Z
- **提交信息**: [Bugfix][Core] Keep the EAGLE-reachable SWA tail at a shared-prefix junction (#62206)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ffa18e5](https://github.com/vllm-project/vllm/commit/ffa18e55a466d7f04a20ea5c4f458ace3b1688c8)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-19T12:31:00Z
- **提交信息**: [ROCm][DSv4] Require explicit MXFP4 opt-in for MegaMoE shared-expert fusion (#61345)

Signed-off-by: Yanfei Wang <yanfei.wang@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [283d48f](https://github.com/vllm-project/vllm/commit/283d48f4ebb404b00e76264ad8f759d7e9a05dfd)

- **作者**: dskwe
- **时间**: 2026-10-19T12:16:12Z
- **提交信息**: [Bugfix][Frontend] Preserve scheduling priority for online and offline beam search (#62253)

Signed-off-by: Yuan Li <dskwelmcy@163.com>
Co-authored-by: Hermes Agent <hermes@nousresearch.com>
Co-authored-by: Hermes Agent <noreply@nousresearch.com>

### [3e96f9c](https://github.com/vllm-project/vllm/commit/3e96f9cf63dae9b0949ce6888b6c0c59587acb6c)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-19T11:55:02Z
- **提交信息**: [ROCm][CI] Bump the ROCm 10 image to torch 2.13 (#62276)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dde9aca](https://github.com/vllm-project/vllm/commit/dde9aca41cd3ccceb1ffa902933b6678a09c83ce)

- **作者**: Jee Jee Li
- **时间**: 2026-10-19T10:35:32Z
- **提交信息**: Add Step-5 Preview support (#61727)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Signed-off-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: chensiyu <chensiyu@stepfun.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Isotr0py <mozf@inferact.ai>
Co-authored-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Dakai An <77474977+andakai@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ee22f68](https://github.com/vllm-project/vllm/commit/ee22f682ab0d2139ae69e3cdbb762a565a166813)

- **作者**: SCcagg5
- **时间**: 2026-10-19T10:13:33Z
- **提交信息**: [Frontend] systemone: prefill the shared prefix once before the reads on hybrid models (#61192)

Signed-off-by: SCcagg5 <sccagg5@gmail.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [5bc2671](https://github.com/vllm-project/vllm/commit/5bc26717ddf415267511bfcf7facf45108735bd3)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-19T10:07:01Z
- **提交信息**: [ROCm][Qwen4Exp] Remove the Qwen3.8-Flash-Next TEP8 MXFP4 emulation guard (#60816)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>

### [fb61ac0](https://github.com/vllm-project/vllm/commit/fb61ac07bd1d5b8b9722c80085b99ef770efb265)

- **作者**: Hexiang Wang
- **时间**: 2026-10-19T09:45:06Z
- **提交信息**: [ROCm][Perf] Use AITER top-k for the DeepSeek-V3.2/GLM-5 sparse indexer (#61943)

Signed-off-by: whx-sjtu <56632993+whx-sjtu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1641765](https://github.com/vllm-project/vllm/commit/1641765ffb53cb10f2753ece0efb41399f7381d3)

- **作者**: Tianyu Guo
- **时间**: 2026-10-19T09:38:24Z
- **提交信息**: [Bugfix][Scheduler] Fix encoder cache deadlock with drafter look-ahead (#60553)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d46cb9a](https://github.com/vllm-project/vllm/commit/d46cb9a6d40414fef1f27f0937a97796c351a216)

- **作者**: nien-hui
- **时间**: 2026-10-19T09:31:22Z
- **提交信息**: [Bugfix][Weight Cache] Key non-MoE DP daemons as DP=1 like the engine (#60179)

Signed-off-by: paul <paulqwer.cs13@nycu.edu.tw>

### [852989f](https://github.com/vllm-project/vllm/commit/852989f580820849113d67d13fd8053e279d0444)

- **作者**: Gilad Zamoscinski
- **时间**: 2026-10-19T07:51:50Z
- **提交信息**: [Bugfix][Sampler] Fix split top-p masking every token for huge logits (thinking_token_budget + spec decode emits token 0) (#58231)

Signed-off-by: Gilad Zamoscinski <gilad.z@taboola.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: tomeras91 <57313761+tomeras91@users.noreply.github.com>

### [bbf59fb](https://github.com/vllm-project/vllm/commit/bbf59fbad49243d12dc966f13b037ffee39f7317)

- **作者**: jackLei
- **时间**: 2026-10-19T07:40:40Z
- **提交信息**: [Kernel] Reject unsupported layouts in CUTLASS 3.x scaled_mm (#55537)

Signed-off-by: jackLei0901 <42642542+jackLei0901@users.noreply.github.com>

### [018f5ff](https://github.com/vllm-project/vllm/commit/018f5ff71aa9cf7138d562dade7e8f1caebfa7cc)

- **作者**: Juntian Liu
- **时间**: 2026-10-19T07:39:31Z
- **提交信息**: [Perf][DSv4.1] MegaAttn: wo_a writes wo_b's MXFP8 input (#60118)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c1dc2e9](https://github.com/vllm-project/vllm/commit/c1dc2e9cf992995953548c392f8c67db7283495b)

- **作者**: Yudong Pan
- **时间**: 2026-10-19T07:30:09Z
- **提交信息**: [Spec Decode][ROCm] Add FLy: entropy-gated deferred verification for draft-model speculative decoding (#53987)

Signed-off-by: eecspan <yudongpyd@163.com>
Signed-off-by: yudong <yudong@minimax.com>
Co-authored-by: yudong <yudong@minimax.com>

### [10e8e92](https://github.com/vllm-project/vllm/commit/10e8e921b8e3115e9e7fc5ab3bac7c5c5844c02f)

- **作者**: bzsuni
- **时间**: 2026-10-19T07:20:29Z
- **提交信息**: [Bugfix][Frontend] Fix auto truncation without an output token limit (#62010)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-20
**监控日期**: 2026-10-19
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7258
- **最后更新**: 2026-10-19T19:24:43Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 10
- **主要提交者**: wangqiankun13, wangyu, zzh

## AI分析总结

# vllm-omni 昨日提交分析（共 10 条）

## 1. 主要更新类型
- **Bug 修复**（4 条）：占比较大，涉及分布式传输、扩散模型、缓存解释。
- **功能新增**（3 条）：语音 VAD、扩散模型 LoRA 桥接、硬件辅助契约校验。
- **CI/流程建设**（2 条）：发布分支 CI 规则、性能测试技能。
- **版本对齐/重构**（1 条）：与上游 vLLM v0.32.0 对齐。

## 2. 关键变更点与项目方向的关系
- **vLLM v0.32.0 对齐（#9066）**：作为 vLLM 生态的全模态扩展，持续跟进上游是项目的核心维护策略，确保 API 兼容与能力同步。
- **Smart Turn 语义 VAD（#8895）**：面向双工（duplex）语音会话的语义语音活动检测，直接服务于 README 中"全模态模型服务"的目标，提升实时语音交互体验。
- **Mooncake 传输引擎修复（#4270）**：修复分布式 KV 缓存传输中缺失的 stage_id，关系到大规模部署下的内存/数据正确性。
- **扩散模型相关修复与增强（#9100、#8521、#8326、#9022）**：涵盖 FA（FlashAttention）变长注意力版本传递、TeaCache 校准说明、MoE+LoRA 桥接、性能测试技能，表明项目正积极拓展扩散模型的服务能力边界。
- **CI 强化（#8380、#9083、#8985）**：降低语音克隆测试的 HNR 门槛说明测试稳定性在持续调优；发布分支上运行 merge/nightly/weekly CI 表明项目开始为版本发布做流程准备。

## 3. 对项目的影响和潜在意义
- 稳定性提升：多个 Bug 修复减少分布式推理与扩散推理中的运行时错误。
- 功能深化：语义 VAD 使双工语音对话更自然，是全模态交互体验的关键一环。
- 工程成熟度：CI 覆盖扩展到发布分支、增加硬件契约前置校验，为长期维护和版本化发布奠定基础。
- 生态兼容：上游对齐降低用户从标准 vLLM 迁移的摩擦。

## 4. 值得关注的技术点
- **语义 VAD 融入双工会话**：超越传统声学 VAD，用语义判断说话人意图，是语音大模型服务的前沿方向。
- **Mooncake stage_id**：分布式 KV 传输引擎的正确性细节，影响多阶段流水线。
- **FlashAttention 变长注意力版本解析**：多后端环境下注意力 kernel 选择的边界问题。
- **MoE + LoRA 桥接**：为扩散大模型的高效微调/适配提供服务端支持。
- 多位贡献者使用 AI 编码助手（Cursor、Claude）协同署名，反映开发流程的新形态。

## 5. 对项目整体发展的意义
结合 README 定位"人人可用的快速、低成本全模态模型服务"，本批提交体现了三条主线：**服务体验**（语音 VAD）、**模态广度**（扩散模型能力与测试）、**工程可靠性**（上游对齐、CI 与发布流程）。这些工作共同推动项目从功能搭建期向生产就绪期过渡，既夯实了与 vLLM 主干的兼容性，又在多模态语音与图像生成服务上持续扩展，符合其全模态推理服务的长期愿景。

## 详细提交记录

### [da572cd](https://github.com/vllm-project/vllm-omni/commit/da572cddb38383deae9caef33b8d490e292ef071)

- **作者**: Nick Cao
- **时间**: 2026-10-19T15:24:05Z
- **提交信息**: [BugFix] Add missing stage_id to MooncakeTransferEngineConnector (#4270)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [6839c4d](https://github.com/vllm-project/vllm-omni/commit/6839c4d162f4bf6cb7f8ccf3ae7d6f3f40e51d6b)

- **作者**: Sheng
- **时间**: 2026-10-19T15:22:42Z
- **提交信息**: [Bugfix][Diffusion] Pass the resolved FA version into dense varlen attention (#9100)

Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [c319a81](https://github.com/vllm-project/vllm-omni/commit/c319a81e46495801e78058376807cbdf5cc8b9ef)

- **作者**: chickeyton
- **时间**: 2026-10-19T14:30:47Z
- **提交信息**: [Core] Add Smart Turn semantic VAD to duplex sessions (RFC #7478) (#8895)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Signed-off-by: psv666 <2693925048@qq.com>
Signed-off-by: LHXuuu <xulianhao.xlh@antgroup.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: psv666 <2693925048@qq.com>
Co-authored-by: LHXuuu <xulianhao.xlh@antgroup.com>
Co-authored-by: psv666 <150513104+psv666@users.noreply.github.com>

### [44a10dc](https://github.com/vllm-project/vllm-omni/commit/44a10dc1e3f9b11b789a6e1d3fe1ebe9c9c1458f)

- **作者**: cheater6666
- **时间**: 2026-10-19T14:21:17Z
- **提交信息**: [Bugfix] Explain uncalibrated MingZImage TeaCache (#8521)

Signed-off-by: cheater6666 <2936663834@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [69789f2](https://github.com/vllm-project/vllm-omni/commit/69789f2af8f6458b4d1c2f9d06402426e5d16040)

- **作者**: andyluo7
- **时间**: 2026-10-19T14:13:19Z
- **提交信息**: ci: validate hardware helper contracts before test collection (#8380)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [f297f33](https://github.com/vllm-project/vllm-omni/commit/f297f33edc19439239d5637816c6e29d848a6ee9)

- **作者**: Yueqian Lin
- **时间**: 2026-10-19T13:31:11Z
- **提交信息**: [CI] Drama 3: lower the PCM HNR floor for the streaming voice-clone test (#9083)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [db23219](https://github.com/vllm-project/vllm-omni/commit/db23219c005ecfb20b1912ff3ea686f9f4e96b4e)

- **作者**: wangqiankun13
- **时间**: 2026-10-19T13:15:02Z
- **提交信息**: [Diffusion][CI] Add performance test skill for diffusion model (#9022)

Signed-off-by: wangqiankun13 <wangqiankun13@huawei.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [d9636de](https://github.com/vllm-project/vllm-omni/commit/d9636de5c46d4e4b4d1ff0198aa9a5115183fc09)

- **作者**: wangyu
- **时间**: 2026-10-19T13:01:03Z
- **提交信息**: [CI/Build] Run merge, nightly, and weekly CI on release/vX.Y.Z branches (#8985)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>

### [f7f4006](https://github.com/vllm-project/vllm-omni/commit/f7f40063db85c481b9dfa46e00a43b0a7efecfb6)

- **作者**: Zhou Taichang
- **时间**: 2026-10-19T12:41:51Z
- **提交信息**: [Core] Align vLLM-Omni with vLLM v0.32.0 (#9066)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [03c3348](https://github.com/vllm-project/vllm-omni/commit/03c334818305d3b1666da01cd0f67d48a4f3e7a2)

- **作者**: zzh
- **时间**: 2026-10-19T09:14:39Z
- **提交信息**: diffusion moe lora bridge (#8326)

Signed-off-by: zzh <943967662@qq.com>

---
