# GitHub Stars 合并报告 - 2026-07-22

**合并日期**: 2026-07-23
**监控日期**: 2026-07-22
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


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2102
- **最后更新**: 2026-07-22T11:24:14Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Bin Jia, 鐘天楽

## AI分析总结

根据提供的仓库 `ByteDance-Seed/VeOmni` 的提交记录和README背景，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：为Muon优化器新增Gram Newton-Schulz后端（#953）
- **Bug修复**：在分布式检查点（DCP）恢复时跳过冗余的Hugging Face权重加载（#955）

### 2. 关键变更点及其与项目整体方向的关系
- **Muon优化器增强**：Muon是一种面向大规模模型训练的优化器（常见于ByteDance相关项目中），新增Gram Newton-Schulz（GNS）后端可提供更稳定的矩阵正交化方法。这与VeOmni“模型中心化分布式训练食谱”的定位一致，旨在丰富训练优化器选项，提升多模态模型训练的收敛效率和稳定性。
- **DCP恢复优化**：跳过冗余的HF权重加载，避免在恢复检查点时重复加载初始化的预训练模型权重。这与项目强调的“高效分布式训练”方向直接相关，减少恢复时间，提升实验迭代速度。

### 3. 对项目的影响和潜在意义
- **提升训练稳定性**：GNS后端的引入可能改善Muon在大规模多模态训练中的数值稳定性，尤其对于需要矩阵正交约束的模块（如注意力机制）。
- **加速实验恢复**：DCP恢复的性能修复可显著缩短断点续训的等待时间，对长期训练任务（如大模型预训练）非常实用，提高GPU利用率。
- **增强框架灵活性**：为Muon提供多种后端实现（类似PyTorch优化器的不同变体），用户可根据模型特性选择最优方案，体现VeOmni的“食谱”理念。

### 4. 值得关注的技术点
- **Gram Newton-Schulz**：一种用于矩阵流形优化的技术，常用于正交约束（如权重归一化）。该后端的实现可能涉及自定义CUDA核或分布式通信原语，值得进一步查看具体代码以评估其效率。
- **DCP（Distributed Checkpoint）与HF权重加载的交互**：修复表明原始实现存在不必要的重复加载，可能源于检查点保存时未正确标记已加载的预训练权重。该修复保证了恢复逻辑的正确性，避免潜在的状态不一致。

### 5. 基于项目背景，这些提交如何影响项目发展
- 根据README，VeOmni旨在“扩展任何模态模型训练”，提供“模型中心化分布式食谱库”。本次更新直接增强了两个关键能力：
  - **优化器食谱扩展**：新增Muon的GNS后端，丰富了优化器选项，帮助用户处理不同模态（文本、图像、视频）模型中的特定数学结构。
  - **训练可靠性提升**：DCP恢复的优化降低了大规模分布式训练中断后重试的成本，使得食谱中涉及长训练周期的方案（如多阶段训练、迭代式微调）更加实用。
- 这些提交体现了项目对**训练效率（性能优化）**和**训练稳定性（功能修复）**的双重关注，符合开源项目持续迭代的典型节奏。未来可能会看到更多优化器后端（如Kronecker分解）和检查点优化（如异步写入）的引入。

## 详细提交记录

### [1f58648](https://github.com/ByteDance-Seed/VeOmni/commit/1f586482f200e444b9b45dd03e91df89685bea21)

- **作者**: Bin Jia
- **时间**: 2026-07-22T11:23:07Z
- **提交信息**: [optim, trainer, config, docs, ci] feat: add Gram Newton-Schulz backends for Muon (#953)

### [6f3b474](https://github.com/ByteDance-Seed/VeOmni/commit/6f3b474690c2e5260b03b3b415df2d70dbf2b909)

- **作者**: 鐘天楽
- **时间**: 2026-07-22T07:42:46Z
- **提交信息**: [dist, trainer, ckpt] fix: skip redundant HF weight loading on DCP resume (#955)

Co-authored-by: jiabin.00 <jiabin.00@bytedance.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2517
- **最后更新**: 2026-07-22T13:13:38Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Watebear, Bilang ZHANG, Yang Yong (雍洋)

## AI分析总结

### 昨日（根据提交日期）更新分析总结

#### 1. 主要更新类型
- **功能新增**：编译支持（`compile`）为Wan模型系列添加CPU卸载、延迟加载和序列并行（sp）特性。
- **性能优化**：消除RoPE（旋转位置编码）和位置编码中的冗余计算。
- **文档更新**：更新了ROS（Read the Docs）页面。

#### 2. 关键变更点及与项目方向的关系
- **`[compile] wan2.1,2.2 moe,2.2 dense for cpu_offload and lazy_load and sp`**  
  为Wan模型（视频生成主流架构）的多个变体（MoE、Dense）集成三种推理优化机制：
  - **CPU offload**：将部分张量卸载到CPU，减少GPU显存占用，支持更大模型推理。
  - **lazy_load**：按需加载模型权重，减少初始化内存峰值。
  - **sp**（序列并行）：可能指序列并行（Sequence Parallelism），用于分布式推理中分割长序列，降低单卡计算负载。  
  **与项目方向**：LightX2V定位为“轻量视频生成推理框架”，这些特性直接提升其在有限硬件资源上的部署能力，扩大适用场景。

- **`[fix] Eliminate redundant computation of RoPE and position`**  
  优化Transformer中位置编码（RoPE）的重复计算，消除不必要的浮点运算。  
  **与项目方向**：推理性能优化是轻量级框架的核心，减少计算冗余可降低延迟，提升吞吐量，尤其对高分辨率长视频生成场景意义重大。

- **`update ros page`**  
  文档页面更新（可能包括新特性说明、使用指南等），保持文档与代码功能同步，提升开发者体验。

#### 3. 对项目的影响和潜在意义
- **硬件适配性增强**：CPU offload和lazy load允许在GPU显存受限（如消费级显卡）或大模型场景下运行Wan系列模型，降低部署门槛。
- **推理可扩展性**：SP支持使模型能够通过多卡并行加速长视频生成，适应更大分辨率或更长时间的视频任务。
- **计算效率提升**：RoPE冗余消除为所有使用该位置编码的模型（不仅是Wan）带来通用性能收益，属于低风险高回报的优化。
- **项目成熟度提升**：文档更新表明项目注重用户引导，有利于吸引更多开发者使用和贡献。

#### 4. 值得关注的技术点
- **CPU offload + lazy load组合**：推理时先初始化关键权重到GPU，非关键路径张量按需从CPU加载，平衡显存与速度。需留意数据传输开销的优化策略。
- **SP实现细节**：序列并行在视频生成中可能涉及时空维度的切分，如何与视频特有的帧间依赖相结合是技术难点。
- **RoPE计算消除**：具体是通过缓存中间结果、调整计算顺序还是算子融合实现，可参考提交代码（推测是类似`precompute`缓存或算子融合）。

#### 5. 对项目发展的推动
根据README，项目是“轻量视频生成推理框架”，这些提交直接增强了其核心竞争力：
- **模型生态兼容**：集中支持Wan系列（当前主流开源视频模型），确保框架能快速适配最新模型变体（MoE、Dense）。
- **性能标杆**：通过消除冗余计算和引入高级推理策略，巩固“轻量快速”的定位，与同类框架（如Hugging Face Diffusers）形成差异化。
- **实用化方向**：CPU offload和SP解决了实际部署中的显存和计算瓶颈，推动视频生成从学术演示走向可落

## 详细提交记录

### [814c493](https://github.com/ModelTC/LightX2V/commit/814c4935260403fc3849653a9c571c088ed257ac)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-07-22T13:07:27Z
- **提交信息**: update ros page (#1278)

### [2c9daa2](https://github.com/ModelTC/LightX2V/commit/2c9daa20b7192cb3bece1935075e57f52af6bcea)

- **作者**: Bilang ZHANG
- **时间**: 2026-07-22T11:43:02Z
- **提交信息**: compile: wan2.1,2.2 moe,2.2 dense for cpu_offload and lazy_load and sp (#1276)

### [a43da09](https://github.com/ModelTC/LightX2V/commit/a43da09397cdcf5c26893b1e74432e11e6adcb5f)

- **作者**: Watebear
- **时间**: 2026-07-22T09:24:14Z
- **提交信息**: [fix]: Eliminate redundant computation of RoPE and position (#1274)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2178
- **最后更新**: 2026-07-22T09:38:31Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: hkz

## AI分析总结

### 分析总结

- **主要更新类型**：功能新增  
- **关键变更点**：为 Wan2.1 模型添加了 Causal-Focing（因果强制）机制。  
- **与项目整体方向的关系**：VideoX-Fun 的核心是提供灵活、可控的视频生成工具（如 CogVideoX-Fun 和 Wan-Fun）。Causal-Focing 是视频生成中常用的技术，用于加强帧间因果约束，提升生成视频的时序一致性和可控性；这与项目“让视频生成更简单、更强大”的目标高度吻合。  
- **对项目的影响和潜在意义**：  
  - **增强 Wan2.1 模型能力**：允许用户在生成时强制指定因果依赖关系，可能用于保持物体运动连贯性或处理更长序列。  
  - **扩大适用场景**：例如在文本生视频、图像生视频等任务中，因果强制可提高结果稳定性，降低“闪烁”等伪影。  
  - **为后续多模型统一支持铺路**：若该机制验证有效，未来可能移植到 CogVideoX-Fun 等其他模型上。  
- **值得关注的技术点**：Causal-Focing 的具体实现方式（例如是否通过修改注意力掩码、损失函数或采样策略），以及它对生成速度和内存的潜在影响。后续可关注是否加入用户可调节参数。  
- **基于项目背景的发展影响**：  
  - 补齐了 Wan2.1 在时序控制方面的短板，使其更像一个可用于专业创作的“功能型”工具（区别于仅演示 demo）。  
  - 提升项目在社区中的竞争力，尤其是与同类开源视频生成框架（如 VideoLDM、Modelscope）对比时，更强调可定制性。  
  - 为未来引入其他高级特性（如运动叠加、关键帧控制）奠定了基础。

## 详细提交记录

### [248ab0a](https://github.com/aigc-apps/VideoX-Fun/commit/248ab0ac0ebc48f0b4ae43ceb2d7ded24cc907bb)

- **作者**: hkz
- **时间**: 2026-07-22T09:37:05Z
- **提交信息**: Add Causal-Focing for Wan2.1 (#500)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6002
- **最后更新**: 2026-07-22T21:31:22Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Daniel Stokes, Yang Xu, YAMY

## AI分析总结

以下是针对 `flashinfer-ai/flashinfer` 仓库昨日（基于提交时间）更新内容的分析总结：

---

## 1. 主要更新类型

| 类型 | 数量 | 对应提交 |
|------|------|----------|
| **功能新增 (feat)** | 4 | nixl_ep 传输补全、GDN Blackwell 状态池索引、collect-env 工具、caller-owned MoE workspace |
| **性能优化 (perf/part of fix)** | 1 | fused_moe runner 缓存 |
| **Bug 修复 (fix)** | 1 | NVFP4 bias 测试缩放 |
| **工具 / 文档 / 模板** | 1 | collect-env 工具 + issue 模板 |
| **测试改进** | 分散

## 详细提交记录

### [56d538e](https://github.com/flashinfer-ai/flashinfer/commit/56d538ed7ca36ae2b1f60e9865134bf6fa7f5106)

- **作者**: Anerudhan Gopal
- **时间**: 2026-07-22T21:31:05Z
- **提交信息**: feat(moe_ep): close the nixl_ep transport gaps blocking the vLLM Fleet/Handle adapters (#4075)

## 📌 Description

Brings the NIXL-EP split transport up to the same `DispatchOutput` /
`BootstrapConfig` contract the `nccl_ep` backend serves, so vLLM's
in-tree `nixl_ep` all2all backend can be folded into the
`flashinfer_ep_low_latency` backend of vllm-project/vllm#47948 via
`create_fleet(..., backend="nixl_ep")` — same manager, same LL adapter,
transport selected per backend.

### Gap closures

- **Recv counts surfaced** — `NixlEpHandle.dispatch` previously
discarded the `recv_count` returned by `Buffer.low_latency_dispatch`; it
is now returned as `DispatchOutput.expert_counts` (the vLLM LL adapter
builds `ExpertTokensMetadata` from it — this was the hard blocker).
- **Process-group-only bootstrap** — when `BootstrapConfig.tcp_store` is
unset, the fleet derives a namespaced `PrefixStore` from
torch.distributed's default store (the NIXL analogue of `nccl_ep`'s
`_resolve_comm` GAP-1 path). vLLM's manager passes only `process_group`;
no sibling-port TCPStore needed. Prefix is namespaced by the EP group's
global ranks + a per-process generation counter so disjoint subgroups /
re-created fleets never collide on store keys. Explicit `tcp_store`
still wins.
- **FP8 scales surfaced** — with `FleetAlgoKnobQuantization`, the
library returns `(fp8_data, scales)`; the scales were dropped. New
optional `DispatchOutput.expert_scales` carries them.
- **`HandleAlgoKnobUserStream` honored** — the NIXL `Buffer` API takes
no stream argument, so dispatch/combine/complete now run under the bound
stream via `torch.cuda.stream(ExternalStream(...))` (previously the knob
was silently ignored; vLLM passes the current stream every forward).
- **`num_tokens` semantics fixed** — was `num_local × max_tokens ×
world`; now the per-expert row count of the recv buffer, matching
`nccl_ep` LL `EXPERT_MAJOR` (read off the returned tensor, with a
capacity-based fallback). No in-tree consumer read it yet.
- `split_layer` init requirement relaxed accordingly (store **or**
initialized torch.distributed).

### Still open for full parity with vLLM's in-tree nixl_ep (follow-ups)

Async recv hooks through the Handle API (DBO overlap),
`FleetAlgoKnobAllocator` (NIXL's `Buffer` owns its RDMA arena outside
torch's pool), elastic-EP fault tolerance (mask query, staged commit).
LL/`EXPERT_MAJOR` remains the only nixl_ep algorithm — matching vLLM's
`nixl_ep`, which is batched/LL-only.

## 🧪 Tests

- `tests/moe_ep/nixl_ep/test_fleet_mock.py` extended:
counts/`num_tokens` contract, fp8 scale surfacing, user-stream redirect,
derived-store path (1-rank gloo), missing-store error. The fake `Buffer`
now returns shape-faithful `[num_local, max_tokens×ranks, hidden]` recv
tensors and the fp8 `(data, scales)` tuple.
- All 8 mock tests collect cleanly; the new code paths were additionally
exercised end-to-end with the mocked Buffer on CPU (this dev box has a
cu126 torch, so the CUDA-13 guard skips the suite — needs a run in the
EP container per `docs/design_docs/moe_ep_runbook.md`, plus the 4-GPU
`smoke_nixl_ep.py` / `run_tests.sh multirank` on cluster).
- `pre-commit` (mypy, ruff, format) passes on the touched files.

Docs: NIXL-EP parity section added to
`docs/design_docs/vllm_moe_ep_integration.md`. Related: #4074 (runbook
NIXL-EP test instructions).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* NIXL-EP fleets can use a default rendezvous store when distributed
communication is initialized.
* Dispatch now returns per-expert token counts and, when enabled, FP8
dequantization scales.
  * NIXL-EP operations can run on a user-selected CUDA stream.
  * Exposes fleet capacity for sizing/configuration.
* **Bug Fixes**
* Improved low-latency dispatch/receive semantics, including corrected
token-count behavior.
  * More reliable loading of the vendored NIXL-EP extension.
* **Documentation**
* Expanded NIXL-EP transport parity details and added NIXL-EP run/test
guidance.
* **Build & Packaging**
* Updated NIXL-EP GPU builds (sm_90/sm_100/sm_103) and raised the
minimum `nixl-cu13` requirement.
  * Added an option to build NIXL-EP only.
* **Tests**
* Expanded host-mock coverage for dispatch, FP8, stream, and
rendezvous-store behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [9481099](https://github.com/flashinfer-ai/flashinfer/commit/94810993a7e23126cbacc49fdf19be6acca0fa99)

- **作者**: YAMY
- **时间**: 2026-07-22T21:19:19Z
- **提交信息**: fix(fused_moe): avoid repeated runner setup in host dispatch (#4045)

## Description

The fused MoE launch path constructs a `MoE::Runner` for every
invocation. Runner construction filters the global GEMM config table and
builds the Cartesian GEMM1/GEMM2 tactic set. After a tactic is selected,
the launcher also materializes and scans the complete valid-tactic list
to validate that single index.

This work remains on the warmed CPU launch path. The artifact update in
#3973 increased the global config set from 1,696 to 2,516 entries and
the tile-128 joint tactic set from 16 to 64, making the existing
per-call work visible in serving throughput.

This change:

- caches constructor-derived `MoE::Runner` instances per host thread,
keyed by the current constructor options, SM version, and CUDA device;
- establishes a CUDA device guard before Runner lookup, construction,
validation, and launch;
- adds `Runner::isValidConfigIndex()` to validate only the selected
GEMM1/GEMM2 pair instead of enumerating the complete valid set.

Runtime tensors, workspaces, streams, and shapes are not cached. Default
tactic selection continues to use `getDefaultValidConfigIndex()`,
followed by the same O(1) selected-pair validation used for explicit
tactics. The BMM artifact, tactic selection policy, selected kernels,
and 2CTA behavior are unchanged.

## Validation

### Same-dispatch GB300 microbenchmark

A same-GPU `stock / fixed / fixed / stock` ABBA comparison used the same
artifact, default tactic path, and identical GEMM1/GEMM2 kernel symbols
in both arms.

| Token bucket | Total latency, fixed - stock | Non-CUDA residual, fixed
- stock | Captured CUDA, fixed - stock |
|---:|---:|---:|---:|
| 8K | -0.430 ms | -0.441 ms | +0.010 ms |
| 32K | -0.416 ms | -0.416 ms | -0.0002 ms |

The non-CUDA residual is total operator latency minus captured CUDA
kernel time. The improvement is isolated to host dispatch; dispatched
kernels and their measured CUDA time remain unchanged within the
benchmark threshold.

### End-to-end serving

The end-to-end comparison used Qwen3.5-397B-A17B-NVFP4 on GB300 with
disaggregated TP4 prefill and TP4 decode, prefill concurrency 96, and
two 900-second measurements per arm in `R-B-H-H-B-R` order. All
measurement windows completed with zero request errors.

- **R:** v0.6.12 compatibility baseline
- **B:** v0.6.15 stock
- **H:** v0.6.15 with this change

| Geometric-mean comparison | Result |
|---|---:|
| B vs. R | -6.090% |
| H vs. B | +6.118% |
| H vs. R | -0.344% |

The v0.6.12 arm includes only an API compatibility backport required by
the newer serving stack; it does not modify the fused MoE artifact,
tuning path, or runtime dispatch.

## Checks

- repository pre-commit checks for the modified files;
- GB300 JIT compilation of the cache and selected-pair path on v0.6.15;
- artifact, tactic, and kernel-symbol parity in the same-dispatch
microbenchmark;
- two-repeat GB300 TP4 end-to-end validation on v0.6.15.

The branch is rebased onto current `main`. Additional constructor-path,
multi-thread, and multi-device tests remain to be added before marking
the PR ready for review.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- Improved mixture-of-experts configuration validation by using a direct
validity check for selected tactics, rejecting invalid configurations
reliably.
- Ensured MoE execution runs on the correct CUDA device across fused MoE
execution paths.

- **Performance**
- Added per-thread caching of compatible MoE runner instances to reduce
repeated setup overhead during repeated executions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [771b7d4](https://github.com/flashinfer-ai/flashinfer/commit/771b7d47aeba365492a7518e02eef7ea9fb64762)

- **作者**: Guoming Zhang
- **时间**: 2026-07-22T13:37:02Z
- **提交信息**: feat(gdn): index GDN prefill state pool via state_indices (SM100/SM103) (#4084)

<!-- .github/pull_request_template.md -->

## 📌 Description
Add an optional state_indices argument to chunk_gated_delta_rule. On the
SM100/SM103 Blackwell kernel, when provided, initial_state and
output_state are treated as a state pool whose first dimension is
indexed by these slot ids: sequence i reads its initial state from row
state_indices[i] and writes its final state back to the same row (in
place when output_state is initial_state). The pool may be non-compact
(padded first-dimension stride). This lets callers with a paged/indexed
state pool skip gathering the active rows into a packed buffer and
scattering the result back; state_indices=None keeps the packed,
sequence-ordered layout unchanged.
<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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
* Added optional indexed recurrent-state pooling for Gated Delta Net
prefill on Blackwell-class hardware (SM100/SM103), using a per-sequence
`state_indices` tensor.
  * Behavior is unchanged when `state_indices` is omitted.
* **Bug Fixes**
* Improved correctness and safety for pooled-state execution:
unsupported dispatch paths now error, and pooled output-final-state
requires an explicit `output_state`.
* **Tests**
* Added GPU-gated coverage validating pooled vs packed outputs/final
states, input/output-state requirements, and default behavior when
`state_indices=None`.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Guoming Zhang <137257613+nv-guomingz@users.noreply.github.com>

### [9dd5f75](https://github.com/flashinfer-ai/flashinfer/commit/9dd5f75d156174453353b67fd3292fdd7d6d4f0b)

- **作者**: Yang Xu
- **时间**: 2026-07-22T13:32:37Z
- **提交信息**: feat: add collect-env environment report tool + issue templates (bug, feature request) (#4007)

## 📌 Description

Issue reporters often can't state their environment precisely, and the
most common unreproducible-issue root cause is version confusion —
multiple copies of cuDNN/cuBLAS/CUDA runtime installed where the
**loaded** one is not the one the user assumes.

This PR adds an environment-forensics tool and wires it into a new
(first) GitHub issue template:

```bash
python -m flashinfer.collect_env        # or: flashinfer collect-env [--json]
```

**What the report covers**

- flashinfer / flashinfer-cubin / flashinfer-jit-cache versions (with
explicit mismatch flag), JIT cache + local cubin store stats, resolved
target CUDA archs
- GPU/driver properties in **CUDA enumeration order** (nvidia-smi order
as no-torch fallback), CUDA toolkit **as resolved by flashinfer's JIT**
vs `CUDA_HOME`
- **Loaded vs installed GPU libraries**: force-loads the libs torch
actually uses, parses `/proc/self/maps` for what is truly mapped, scans
`LD_LIBRARY_PATH` / site-packages / `CUDA_HOME` / ldconfig for other
on-disk installs; aggregated per directory with pip provenance, ⚠ on
real conflicts
- torch build info, cuDNN frontend + loaded backend version, relevant
packages (incl. vLLM/SGLang and their declared flashinfer pins, stated
factually), `FLASHINFER_*`/`CUDA*`/… env vars, GPU topology

**Design constraints** (documented in the module docstring)

- stdlib-only at module level and every probe individually guarded →
still produces a report when `import flashinfer` or torch is broken; the
file can be `curl`-ed and run standalone with bare Python
- strictly offline/read-only (no downloads, unlike `show-config`'s
artifact status), ~7 s wall clock

Example of the headline section on a box with a pip-wheel CUDA stack
plus a local toolkit:

```text
==== GPU Libraries: loaded vs on disk ====
libcublas  ⚠ other installs on disk (check which one you expect):
    LOADED   .../.venv/lib/python3.12/site-packages/nvidia/cu13/lib/  [pip nvidia-cublas==13.0.0.19]
    on disk  /usr/local/cuda-13.2/targets/x86_64-linux/lib/  [v13.3.0.5]
```

## 🔍 Related Issues

Improves triage for env-dependent reports in general (e.g. the recurring
"works on my machine" class).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`tests/utils/test_collect_env.py` asserts the core contract (collection
never raises, sections present, JSON-serializable) and runs GPU-less.
Manually verified on a multi-arch box (A100/L40S/H100/B200-class, driver
595.71.05): full run in a venv, standalone run with bare
`/usr/bin/python3` (no torch/flashinfer — degrades gracefully), `--json`
parses.

## Reviewer Notes

- `/proc/self/maps` is Linux-only; on other platforms that section
degrades to the on-disk scan.
- AI-assisted (Claude Code).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a `collect-env` CLI command to generate detailed environment
reports (runtime, CUDA/GPU details, loaded libraries, and version info).
  * Supports formatted text or pretty-printed JSON output.
* Added GitHub issue forms for bug reports and feature requests with
prompts for reproducible steps and environment output.

* **Documentation**
* Updated quick-reference materials with environment-report commands,
including an optional `--json` mode.

* **Tests**
* Added tests covering report section presence/structure,
FlashInfer↔flashinfer version consistency, text formatting, and
JSON-serializability.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

**Update (2026-07-17):** also adds `🚀 Kernel / Feature Request`
(`feature_request.yml`), a slimmed revision of the template draft
circulated on Slack, incorporating the thread feedback (thanks
@Kaustubh, Brian, Jingfan):

- Two clean templates with an explicit routing rule in each description:
*broken / wrong / slower than before* → Bug Report; *new capability /
speedup* → Feature Request
- Required fields: 4 (+ a "searched existing issues" checkbox on both
templates); the remaining fields are grouped under a visible "everything
below is optional" divider
- Hardware dropdown gains Ampere/Ada; inference engine is multi-select;
Evidence dropdown folded into the Problem field; Impact
label/multi-select contradiction fixed
- Both templates reference the same environment tool: `python -m
flashinfer.collect_env`; bug-template reproducer guidance now asks for a
short standalone script rather than a full `vllm serve` run

---------

Co-authored-by: Yang Xu <yanxu@nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [d25d2d6](https://github.com/flashinfer-ai/flashinfer/commit/d25d2d64f03fe00bcded80d0d1fe663e71d2cc63)

- **作者**: feih-nv
- **时间**: 2026-07-22T11:55:31Z
- **提交信息**: feat(moe): support caller-owned CUTLASS MoE workspace (#4057)

## 📌 Description

Addresses the workspace-allocation portion of #3364.

`cutlass_fused_moe` previously allocated its scratch workspace
internally on every invocation. For large token batches, this workspace
can consume multiple GiB and cause allocator churn, transient memory
spikes, CUDA graph pool duplication, and poor visibility for
serving-engine memory planning.

This PR adds caller-owned workspace support to the CUTLASS fused MoE
API:

- `cutlass_fused_moe_workspace_size(...)` queries the required workspace
size.
- `workspace_buffer=` allows callers to reuse pre-allocated workspace.
- Runtime validation checks workspace size, dtype, dimensionality,
contiguity, alignment, and device.
- Architecture selection, new runner initialization, execution,
profiling, and fallback allocation use the input device.
- Packed weights use an explicit logical intermediate size.
- Expert parallelism uses an explicit global expert count.

Calls that omit `workspace_buffer` retain the existing
internal-allocation behavior. This change affects workspace ownership
and reuse, not the algorithmic workspace requirement.

### Usage

Query and allocate the workspace during model initialization:

```python
workspace_bytes = flashinfer.fused_moe.cutlass_fused_moe_workspace_size(
    max_num_tokens,
    hidden_size,
    intermediate_size,  # logical, unpacked intermediate size
    num_experts_total,  # global expert count across EP ranks
    top_k,
    x_dtype=input.dtype,
    weight_dtype=fc1_expert_weights.dtype,
    output_dtype=output_dtype,
    ep_size=ep_size,
    ep_rank=ep_rank,
    use_fused_finalize=use_fused_finalize,
    use_packed_weights=use_packed_weights,
    device=input.device,
)

workspace = torch.empty(
    workspace_bytes,
    dtype=torch.uint8,
    device=input.device,
)
```

Reuse the workspace during execution:

```python
outputs = flashinfer.fused_moe.cutlass_fused_moe(
    ...,
    ep_size=ep_size,
    ep_rank=ep_rank,
    use_fused_finalize=use_fused_finalize,
    use_packed_weights=use_packed_weights,
    workspace_buffer=workspace,
)
output = outputs[0]
```

The workspace must be:

- A contiguous, one-dimensional `torch.uint8` or `torch.int8` CUDA
tensor.
- Allocated on the same device as `input`.
- At least the size returned by `cutlass_fused_moe_workspace_size`.
- 128-byte aligned.

A separate workspace is required for each concurrently executing CUDA
stream. A workspace sized for the maximum token count can be reused for
smaller calls with the same model and kernel configuration.

### Device Handling

Module selection, runner initialization, execution, profiling, and
fallback
workspace allocation now consistently use `input.device`.

The workspace-size query accepts an explicit `device`, and
caller-provided
workspaces are rejected if they are on a different device from the
input. This
fixes multi-GPU cases where the current CUDA device differs from the
input
device.

### Sizing Semantics

For packed weights, `intermediate_size` is the logical unpacked
dimension, not the packed storage dimension.

Under expert parallelism, `num_experts_total` is the global expert
count:

```python
num_experts_total = fc2_expert_weights.shape[0] * ep_size
```

The sizing API validates parallel ranks and expert-count divisibility
before entering the kernel.

## 🧪 Tests

Added coverage for:

- Positive and monotonic workspace sizing.
- Buffered and unbuffered numerical equivalence.
- Exact-size and undersized buffers.
- Invalid dtype, device, dimensionality, and layout.
- Packed-weight workspace sizing.
- Expert-parallel workspace sizing.
- Avoiding internal workspace allocation.
- CUDA graph capture and replay.
- Execution when the current CUDA device differs from the input device.

Local results on B100:

```bash
pytest -v tests/moe/test_trtllm_cutlass_fused_moe.py -k workspace
```

```text
12 passed, 2 skipped, 130 deselected, 2 warnings in 3908.20s
```

Expected skips:

- SM90 packed-weight test on the SM100 host.
- Two-GPU device test on the single-GPU host.

```bash
pytest -v tests/trace/
```

```text
955 passed, 172 skipped, 36 warnings in 1110.29s
```

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [x] I have installed the hooks.
- [x] I have run `pre-commit run --all-files` and fixed reported issues.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary of release changes

* **New Features**
* Added support for caller-provided workspace buffers for CUTLASS fused
MoE, enabling reuse.
* Added `cutlass_fused_moe_workspace_size(...)` to compute exact
required buffer size.
* Extended fused MoE runner and scripting interfaces to accept
`base_activation_type` and optional `workspace_buffer`.

* **Bug Fixes**
* Improved device handling so workspace/context selection follows the
input tensor’s device.

* **Tests**
* Added comprehensive workspace-buffer coverage (exact sizing
acceptance, validation failures, and CUDA graph replay).
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d0889c7](https://github.com/flashinfer-ai/flashinfer/commit/d0889c7c95619d48a957353c379cb724ec8e3fb5)

- **作者**: Daniel Stokes
- **时间**: 2026-07-22T08:45:54Z
- **提交信息**: fix: Fix the MOE tests to properly scale NVFP4 bias (#3755)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved FP4 bias handling for MoE operations, fixing a
quantization-specific issue so results are adjusted correctly across
supported FP4 modes.
* **Tests**
* Expanded MoE coverage to validate the bias path under multiple FP4
quantization variants instead of a single configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [06a2088](https://github.com/flashinfer-ai/flashinfer/commit/06a2088ddc2350d8923afc8ce4ed6dfd838cc776)

- **作者**: RuQing Xu
- **时间**: 2026-07-22T08:39:34Z
- **提交信息**: [feat] Add TRTLLM/SageAttention quantization routine (#3982)

<!-- .github/pull_request_template.md -->

## 📌 Description

#2711 added SageAttention kernels for Blackwell SM100, but didn't
provide a corresponding quantization routine. We expected users to
create their own quantization kernel according to the examples in
tests/, but absence of a directly importable GPU quantization routine
still causes much inconvenience.

This PR tries to add quantization routine for TRTLLM SageAttention as a
direct importable module of flashinfer. Please let me know if the added
API is appropriate (naming, file location, ...)

- `sageQuant.cu` imported from
[TRTLLM/cpp/...](https://github.com/NVIDIA/TensorRT-LLM/blob/main/cpp/tensorrt_llm/common/sageQuant.cu)
- Routine is specific to TRTLLM's SageAttention for Blackwell SM100
- Must be used with trtllm_ragged_attention_deepseek
- See added tests for use example

## 🔍 Related Issues

<!-- Link any related issues here -->
N/A

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added TensorRT-LLM SageAttention quantization for **Q/K** (INT8 or FP8
E4M3) and **V** (FP8 E4M3).
* Introduced `trtllm_sage_attention_quantize` to produce quantized Q/K/V
tensors and the required SageAttention scale tensors.
* Re-exported `trtllm_sage_attention_quantize` at the package top level
for easier access.
* **Documentation**
* Clarified `sage_attn_sfs` usage and wiring for the SageAttention
quantization outputs in ragged attention.
* **Tests**
* Updated DiT ragged-attention coverage to use the new SageAttention
quantization workflow.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3869
- **最后更新**: 2026-07-22T12:47:51Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: pkisfaludi-nv

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **Bug修复 / 兼容性修复**：修复了 LTX-2 模型中 RMSNorm 层因 in-place 操作导致 `torch_tensorrt` 和 Ulysses SP（序列并行）无法编译的问题。
- **性能优化前置准备**：将 RMSNorm 改为 out-of-place，为后续利用 TensorRT 推理优化和 Ulysses 序列并行铺平道路。

#### 2. 关键变更点及其与项目方向的关系
- **变更点**：将 LTX-2 中的 RMSNorm 实现从 in-place 改为 out-of-place（即返回新张量而非原地修改）。
- **与项目方向关系**：FastVideo 旨在提供**高效视频生成/处理**，涉及大规模模型训练与部署。本次修改直接打通了与 **NVIDIA TensorRT**（推理加速）和 **Ulysses SP**（序列级并行，常用于长视频 / 高分辨率场景）的编译器兼容性，契合项目“快速”（Fast）的核心目标。

#### 3. 对项目的影响和潜在意义
- **编译疏通**：消除了 `torch_tensorrt` 和 Ulysses SP 在 LTX-2 模型上的编译障碍，使模型能够顺利导出为优化后的推理引擎。
- **性能提升潜力**：TensorRT 通常能带来 2~5 倍的推理加速；Ulysses SP 可支持更长的序列长度训练/推理（如长视频生成），从而扩大模型的应用场景。
- **可维护性**：out-of-place 操作更符合现代编译器与并行框架的期望，减少潜在的梯度计算或内存别名问题。

#### 4. 值得关注的技术点
- **in-place vs out-of-place 的编译器影响**：in-place 操作会引入张量别名，导致 `torch_tensorrt` 等静态编译器难以进行内存分析和算子融合；改为 out-of-place 后编译器可安全优化。
- **Ulysses SP 的依赖**：序列并行往往需要在不同设备间通信，out-of-place 设计可避免通信过程中意外修改原始数据。
- **LTX-2 模型定位**：推测 LTX-2 是 FastVideo 中核心的**视频生成/处理 Transformer 模型**，其 RMSNorm 的改动可能对应模型中的一个关键层（例如 QKV 归一化或 FFN 前的归一化）。

#### 5. 对项目发展的影响（结合项目背景）
- **加速模型部署**：FastVideo 的 README 强调“快速上手”和“文档”，说明项目重视易用性与实际落地。本次提交让用户能更顺畅地使用 TensorRT 进行推理加速，提升了实用性。
- **支持长序列训练**：Ulysses SP 的兼容性意味着项目正朝着**长视频 / 高分辨率生成**方向演进，这与社区对高质量视频模型的需求一致。
- **社区协作特征**：提交备注中出现 AI 辅助署名（Claude

## 详细提交记录

### [9fb74b9](https://github.com/hao-ai-lab/FastVideo/commit/9fb74b97329b9838e33d4f9598d298d1c34fa0df)

- **作者**: pkisfaludi-nv
- **时间**: 2026-07-22T11:32:04Z
- **提交信息**: Make LTX-2 RMSNorm out-of-place so torch_tensorrt + Ulysses SP compiles (#1623)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34133
- **最后更新**: 2026-07-22T19:07:44Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: YiYi Xu, Dhruv Nair

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **CI/质量保障增强**：自动化文档字符串（auto docstrings）的陈旧性检测机制得到完善。
- **功能更新与工具改进**：`diffusers-cli` 命令行工具进行了大量更新，以支持更灵活的“代理式”（agentic）使用场景。

#### 2. 关键变更点与项目方向的关系
- **提交 4d89a88**：  
  * 重新生成了当前所有模块化管道的自动文档字符串，确保与源码块声明一致。  
  * **改进 CI 检查**：原先只检查文档字符串是否存在，现在会对比实际生成的内容与仓库中的内容，若不一致则报告过时的类。  
  * 此举将 `check_auto_docs` CI 任务迁移至 torch 容器（与测试任务共享依赖），避免依赖不一致导致误报。  
  * **关系**：项目倡导“模块化”（modular）设计，自动文档字符串是连接模板、规范和具体声明的关键。该提交提升了文档的准确性，降低了因跨文件变更导致文档漂移的风险，与项目长期追求的“模块化可维护性”方向一致。

- **提交 6afdfd9**：  
  * 对 `diffusers-cli` 进行了数十次增量更新（具体变更未详细说明，但从描述“for agentic use”推断）。  
  * **关系**：`diffusers-cli` 是用户与库交互的命令行入口。强化其“代理式”能力意味着用户可以通过更灵活的组合、脚本化调用来使用扩散模型（如自动化推理、管线编排），这符合 HuggingFace 推动的“工具化+代理”生态趋势（如 `smolagents`、`transformers.agents`）。更新为未来集成 LLM 智能代理或更复杂的自动化工作流铺平了道路。

#### 3. 对项目的影响与潜在意义
- **质量影响**：  
  * 文档的自动验证从“存在性检查”升级为“内容一致性检查”，能早期发现因模板或块声明变更导致的文档过期问题，提升开发者体验和文档可靠性。  
  * CI 流程的调整（依赖到 torch 容器）确保了检查环境与实际运行环境一致，减少误判。
- **生态影响**：  
  * `diffusers-cli` 的代理化使用扩展了库的应用场景：从单纯的一个命令跑 pipeline 到更复杂的任务链、循环、条件触发等，有助于吸引更多自动化/编排型用户（如 MLOps、研究人员）。

#### 4. 值得关注的技术点
- **自动文档字符串的生成机制**：`modular_auto_docstring.py` 脚本通过解析模块声明、模板和规格来生成文档。提交中增加了 `--fix_and_overwrite` 模式，且检查模式在其临时副本上执行完整 regenerate → format → compare 流程，类似于 `check_copies` 的工作方式。
- **CI 依赖管理**：由于检查需要导入 diffusers 内部模块（如 `diffusers.utils.doc_properties`），所以将任务移至带有 torch 依赖的容器，避免因缺少 GPU 依赖或 torch 版本不匹配导致的 import 错误。
- **Agentic CLI 的演进**：虽未公开具体 API 变动，但“代理式”可能涉及：支持管道间组合、状态保存/恢复、外部工具调用（如搜索、代码执行）等。值得关注后续文档或 example 更新。

#### 5. 结合项目背景，这些提交如何影响项目发展
- **巩固模块化基础**：Diffusers 的成功部分源于其模块化设计（管道、调度器、模型可互换）。确保模块文档与声明同步，降低了维护多文件带来的耦合风险，使得社区贡献者更容易添加新模块而不破坏文档。
- **提升自动化/低级使用体验**：命令行

## 详细提交记录

### [4d89a88](https://github.com/huggingface/diffusers/commit/4d89a88748e851bac1c30f32b7d8af7707bbf0a4)

- **作者**: YiYi Xu
- **时间**: 2026-07-22T19:05:54Z
- **提交信息**: [modular] detect stale auto docstrings in CI + regenerate current ones (#14241)

* Regenerate stale modular auto docstrings

Mechanical output of `python utils/modular_auto_docstring.py
src/diffusers/modular_pipelines --fix_and_overwrite` on current main.
These docstrings drifted because the CI check only verifies a docstring
exists, not that its content matches the current block declarations.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* Make auto docstring check detect stale content, not just missing docstrings

Check mode now regenerates each # auto_docstring docstring the same way
--fix_and_overwrite does (generate -> insert -> ruff/doc-builder format,
on a temp copy) and compares with the checked-in file, reporting the
stale classes. Works like check_copies: forgetting to run the fixer now
fails CI on the PR that caused the drift, including when the causing
change is in another file (leaf block declarations, templates, specs).

The check now imports diffusers to evaluate doc properties, so the
check_auto_docs CI job moves to the torch container with the test job's
dependency install.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [6afdfd9](https://github.com/huggingface/diffusers/commit/6afdfd9f4e2e2381c5d5cced0dc4262e9e4267bd)

- **作者**: Dhruv Nair
- **时间**: 2026-07-22T11:32:44Z
- **提交信息**: Update `diffusers-cli` for agentic use (#13966)

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* pdate

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

* update

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 426
- **最后更新**: 2026-07-21T12:34:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12738
- **最后更新**: 2026-07-22T22:24:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30641
- **最后更新**: 2026-07-22T22:10:01Z

## 提交统计

- **昨日提交总数**: 36
- **提交者数量**: 18
- **主要提交者**: Fan Kun, Xiaoyu Zhang, Cheng Wan

## AI分析总结

分析生成失败

## 详细提交记录

### [24da0e5](https://github.com/sgl-project/sglang/commit/24da0e51b67ae56ac95a1df96d6286c7dd91eb07)

- **作者**: danielafrimi
- **时间**: 2026-07-22T22:09:53Z
- **提交信息**: Warn on small Mamba chunked prefill size (#30938)

Co-authored-by: Daniel Afrimi <dafrimi@aws-dfw-cs-001-login-01.cm.cluster>

### [0c29c8f](https://github.com/sgl-project/sglang/commit/0c29c8fecee11f6e9cbe6a69142ceeb44fc41645)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-22T21:21:59Z
- **提交信息**: Bump FlashInfer to 0.6.15.post1 (#31927)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [c20c48b](https://github.com/sgl-project/sglang/commit/c20c48b8fd94c5553452988edda6b3832166e5dc)

- **作者**: ilyasher-harmonic
- **时间**: 2026-07-22T21:14:47Z
- **提交信息**: Add 'anyOf' schema support for qwen3_coder tool call parser (#30832)


Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [e751114](https://github.com/sgl-project/sglang/commit/e7511141ea396bb22d35e5af51edfa4f2a0e49a7)

- **作者**: Brayden Zhong
- **时间**: 2026-07-22T21:13:12Z
- **提交信息**: Support CuteDSL GEMM BF16 on SM100 on by default when allowed by heuristic (#30567)

### [98cc8d9](https://github.com/sgl-project/sglang/commit/98cc8d91cf78f7ce8d41d3e80f407e715ff23e34)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-22T19:41:06Z
- **提交信息**: [Fix] Evict only the KV shortfall in evict_from_tree_cache (#32016)

### [5c6a29b](https://github.com/sgl-project/sglang/commit/5c6a29b3c389100e1cda820150cb338d7a178a8e)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-22T19:29:34Z
- **提交信息**: [Fix] Unify pinned host pool release on graceful shutdown (#32029)

### [f5dcbe8](https://github.com/sgl-project/sglang/commit/f5dcbe8f142f0f15a861271717c5dc000b89952b)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T18:52:41Z
- **提交信息**: Revert RuntimeContext config-namespace reads/roles (#31813–#31817) (#32100)

### [0bdd473](https://github.com/sgl-project/sglang/commit/0bdd4730af8c215545821049ea9f794519c13fa8)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-22T16:11:25Z
- **提交信息**: [CI] Fix failures on main (#32091)

### [40ac197](https://github.com/sgl-project/sglang/commit/40ac197fb2379d86f9032b43d0173d1b9a619a80)

- **作者**: Ke Bao
- **时间**: 2026-07-22T16:09:25Z
- **提交信息**: Fix get_server_args import lint error (#32096)

### [e81b326](https://github.com/sgl-project/sglang/commit/e81b326e7231fb4e140c63b6379eb04d2c698f62)

- **作者**: Ke Bao
- **时间**: 2026-07-22T15:56:18Z
- **提交信息**: Add Inkling per-commit server test (#32095)

### [4eaa5ca](https://github.com/sgl-project/sglang/commit/4eaa5ca6510622cb0006bcfee5947b17859ac8c7)

- **作者**: Raghavendra Vedula
- **时间**: 2026-07-22T15:25:25Z
- **提交信息**: Treat partial_json_parser AssertionError as incomplete JSON (#31975)

### [a9497e8](https://github.com/sgl-project/sglang/commit/a9497e8d7378262d0673b37a1599633baa9e8f1a)

- **作者**: Raghavendra Vedula
- **时间**: 2026-07-22T15:24:25Z
- **提交信息**: Guard min_new_tokens penalizer against None eos_token_id (#31973)

### [40b2119](https://github.com/sgl-project/sglang/commit/40b2119b23e49be767da1f9f73746ac8e158dae5)

- **作者**: Chengze Fan
- **时间**: 2026-07-22T14:50:23Z
- **提交信息**: [AMD] Cache AITER expert mask across decode (#31889)

### [e8e765b](https://github.com/sgl-project/sglang/commit/e8e765b9d6577a53b7186f068728ca04c7d06036)

- **作者**: Hubert Lu
- **时间**: 2026-07-22T14:33:03Z
- **提交信息**: [AMD] Add fused all-reduce RMSNorm per-group quant for Qwen3.5 FP8 (#24651)

Co-authored-by: jacky.cheng <yichiche@amd.com>
Co-authored-by: yctseng0211 <yctseng@amd.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [b855efd](https://github.com/sgl-project/sglang/commit/b855efd9e66a19cbe54b118fee675f9ac1e8546c)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-22T14:09:01Z
- **提交信息**: Fix Inkling kernel imports after migration (#32076)

### [0a6d193](https://github.com/sgl-project/sglang/commit/0a6d1930c36079dc08aeee6df41be5ebef195f39)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-22T14:06:22Z
- **提交信息**: [Attention Backend] Add HPC-Ops attention backend (#30540)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Halcyon <56064364+VAthree@users.noreply.github.com>

### [004df6b](https://github.com/sgl-project/sglang/commit/004df6b520825f8fa3ac463a896e091b3fcc9c06)

- **作者**: Fan Kun
- **时间**: 2026-07-22T14:01:29Z
- **提交信息**: [FIX] Prevent Lightning Attention extra-buffer mamba state corruption (#29973)

Co-authored-by: 范坤 <fankun@U-Q0542J2D-0225.local>

### [21065bc](https://github.com/sgl-project/sglang/commit/21065bc86290efd3279cd2f2b873710ba47f3d9c)

- **作者**: ishandhanani
- **时间**: 2026-07-22T13:39:08Z
- **提交信息**: feat: add native gRPC sidecar module launcher (#31076)

Signed-off-by: Ishan Dhanani <ishandhanani@gmail.com>
Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Co-authored-by: Connor Carpenter <connorc@nvidia.com>

### [74338e9](https://github.com/sgl-project/sglang/commit/74338e94f10ec1f2cc9f3f1b5060612082f45c3d)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-22T13:15:03Z
- **提交信息**: [Kernel] Phase 4 batch-3: migrate tangled JIT subsystems + new groups into kernels.ops (RFC #29630) (#32045)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [71fe649](https://github.com/sgl-project/sglang/commit/71fe649d68878f28e9e49e8a134f0f37c93dc67d)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-22T13:14:21Z
- **提交信息**: [AMD] Register the Helios release workflow on main (#32069)

Co-authored-by: bingxche <bingxche@amd.com>

### [b13abfd](https://github.com/sgl-project/sglang/commit/b13abfdedfc6eb5556e0a04e9714ebd91b323c1d)

- **作者**: 王鹤男
- **时间**: 2026-07-22T12:24:21Z
- **提交信息**: Fix LongCat n-gram token-table crashes on padded batches (#31312)

Co-authored-by: whn09 <whn09@users.noreply.github.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [d6690de](https://github.com/sgl-project/sglang/commit/d6690de96171a677f9d2d4e66ad3f8262bb8ba8e)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-22T12:16:43Z
- **提交信息**: [CI] Fix Marlin MoE test ServerArgs initialization (#32049)

### [4f88206](https://github.com/sgl-project/sglang/commit/4f88206393b620f5a856c8719289cf845a72b4fb)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-22T11:45:29Z
- **提交信息**: [CI] Fix stale per-token group quant callers (#32047)

### [977ea33](https://github.com/sgl-project/sglang/commit/977ea336cd3e960141c4c6e746b4efc24fdf312e)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-22T09:49:51Z
- **提交信息**: [Kernel] Phase 4 batch-2: migrate JIT operator groups into kernels.ops (no shims) (RFC #29630) (#32015)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [9456cef](https://github.com/sgl-project/sglang/commit/9456cef279ea42f032431600e88e5c2d2752bb86)

- **作者**: McZyWu
- **时间**: 2026-07-22T08:34:59Z
- **提交信息**: [NPU]fix rl update weights 'Parameter' object has no attribute 'weight_LOADER' (#31796)

### [2e43b4d](https://github.com/sgl-project/sglang/commit/2e43b4de5244930201b1bfdefc3b9d04df764bb8)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T08:19:13Z
- **提交信息**: test: publish resolved config in unit fixtures for the namespace API (#31817)

### [745b2ca](https://github.com/sgl-project/sglang/commit/745b2ca45c7fc552b43707e95a65058815861b87)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T08:18:50Z
- **提交信息**: config: read parallel config leaves via get_parallel() (#31816)

### [602b546](https://github.com/sgl-project/sglang/commit/602b546a4e8f4f8528c3264689cd55c825ae9cb8)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T08:18:31Z
- **提交信息**: config: load-time declarations write the config bags (#31815)

### [11a4c2d](https://github.com/sgl-project/sglang/commit/11a4c2d05771303f02dc28c28af5e710ea3f5e1f)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T08:18:05Z
- **提交信息**: config: read resolved config via namespace accessors (#31814)

### [1d0a6ee](https://github.com/sgl-project/sglang/commit/1d0a6ee1781351c3819f64101dbe6ce2a62ed5ac)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T08:17:42Z
- **提交信息**: runtime_context: record the publishing process role (#31813)

### [e1479cc](https://github.com/sgl-project/sglang/commit/e1479cc9661a2c66df52025f6bf9c089370cccce)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T08:17:22Z
- **提交信息**: config: route runtime config adjustments through the namespace bags (#31812)

### [97e2c0c](https://github.com/sgl-project/sglang/commit/97e2c0c4eee25369155da1daaae11fe7fcaaa1f9)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T08:16:55Z
- **提交信息**: config: make ServerArgs read-only with a single audited mutation entry (#31811)

### [09688d5](https://github.com/sgl-project/sglang/commit/09688d58bc7d1c0d54da5924543509ea09409f1c)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T08:16:24Z
- **提交信息**: runtime_context: add resolved-config namespace bags and accessors (#31810)

### [1a19f2b](https://github.com/sgl-project/sglang/commit/1a19f2b50f5005fe2d9dd9de8769d0962578b692)

- **作者**: Cheng Wan
- **时间**: 2026-07-22T08:15:11Z
- **提交信息**: config: annotate ServerArgs fields with their runtime-config namespace (#31809)

### [ae2bc33](https://github.com/sgl-project/sglang/commit/ae2bc3321e3e54dae532d4caadc505612358b37e)

- **作者**: Yuan Luo
- **时间**: 2026-07-22T08:03:29Z
- **提交信息**: [KDA] Fix mixed exponent bases in Triton chunk prefill (#31904)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [7dcf3f7](https://github.com/sgl-project/sglang/commit/7dcf3f7cbfc1e2ed9e367a60ab68968255fefd42)

- **作者**: axx-ty911
- **时间**: 2026-07-22T07:09:05Z
- **提交信息**: [Doc] Rename A5 product name (#31998)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1234
- **最后更新**: 2026-07-20T09:15:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 86898
- **最后更新**: 2026-07-22T22:17:14Z

## 提交统计

- **昨日提交总数**: 18
- **提交者数量**: 16
- **主要提交者**: Teresa Chen, Nick Hill, wang.yuqi

## AI分析总结

以下是结合项目背景（vLLM：为所有人提供易用、快速、低成本的LLM推理服务）对昨日提交记录的分析总结：

---

### 1. 主要更新类型

| 类型 | 提交数量 | 代表提交 |
|------|----------|----------|
| **Bug修复** | 4 | #49427（越界访问修复）、#48748（特殊token泄漏）、#49400（视觉UUID重建）、#49297（MLA+mamba异构TP） |
| **CI/测试稳定性** | 5 | #49423、#49388、#49450、#49374、#49350（超时调整、测试修复、跳过不稳定测试） |
| **性能优化** | 1 | #48957（跳过空c128内核启动，性能提升约2x） |
| **构建/依赖升级** | 3 | #48914（Flashinfer 0.6.15）、#49326（vllm-flash-attn C++20兼容）、#49431（

## 详细提交记录

### [910cc85](https://github.com/vllm-project/vllm/commit/910cc8543a6907c9cc87c417f8f2420969278bf5)

- **作者**: Nick Hill
- **时间**: 2026-07-22T20:47:37Z
- **提交信息**: [Bugfix] Restore `gather_and_maybe_dequant_cache` OOB guard (#49427)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [4319345](https://github.com/vllm-project/vllm/commit/431934522b65f126c43f74b19cdd8f3bf63f9747)

- **作者**: Nick Hill
- **时间**: 2026-07-22T20:43:07Z
- **提交信息**: [CI] Fix stale/fragile untethered kernels-root tests (#49423)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [61a0953](https://github.com/vllm-project/vllm/commit/61a09532f23a24915dc6f0aaf8991405a92c8c7d)

- **作者**: Wei Zhao
- **时间**: 2026-07-22T20:32:05Z
- **提交信息**: Bump Flashinfer version to 0.6.15 (#48914)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Signed-off-by: Wei Zhao <weizha@oci-aga-slurm-1-vscode-02.cm.cluster>
Co-authored-by: Wei Zhao <weizha@oci-aga-slurm-1-vscode-02.cm.cluster>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [3de4b2b](https://github.com/vllm-project/vllm/commit/3de4b2bf3c477513afff4a58680eb00d557bb53a)

- **作者**: Ben Browning
- **时间**: 2026-07-22T20:10:55Z
- **提交信息**: [Bugfix][Parser] Fix special tokens (EOS/BOS) leaking into reasoning content (#48748)

Signed-off-by: Ben Browning <56071+bbrowning@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b44311b](https://github.com/vllm-project/vllm/commit/b44311b6ef9232d1f345f4b55adef7abc223f0e7)

- **作者**: Thien Tran
- **时间**: 2026-07-22T16:03:46Z
- **提交信息**: [CI] stabilize GDN prefill CuTeDSL test (#49388)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Codex <noreply@openai.com>

### [b0d7875](https://github.com/vllm-project/vllm/commit/b0d7875180047470a877e4e4f0d930b56ed111fc)

- **作者**: Nick Hill
- **时间**: 2026-07-22T15:39:09Z
- **提交信息**: [CI] Increase timeout of pytorch-compilation-unit-tests (#49450)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [53c2f20](https://github.com/vllm-project/vllm/commit/53c2f20dd9f1ead9c4a086e5103af7f8a74681a2)

- **作者**: Divakar Verma
- **时间**: 2026-07-22T15:18:01Z
- **提交信息**: [ROCm][CI] skip moe weight padding for eplb (#49350)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [37e370f](https://github.com/vllm-project/vllm/commit/37e370fe936fbee062b7a4bd502375794d859b5f)

- **作者**: Wentao Ye
- **时间**: 2026-07-22T14:55:20Z
- **提交信息**: [DSv4 Perf] Skip empty c128 kernel launch, around 2x kernel performance improvement. (#48957)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [2dc5a72](https://github.com/vllm-project/vllm/commit/2dc5a72e7e4e012653a0effda493222c85836bc6)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-07-22T14:11:24Z
- **提交信息**: [Bugfix][Renderer] Rebuild vision chunk UUIDs in async render path (#49400)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>

### [c79ff5f](https://github.com/vllm-project/vllm/commit/c79ff5f91854b54a8e0cf225980b7b8ca4c52c3a)

- **作者**: Andrey Talman
- **时间**: 2026-07-22T13:51:59Z
- **提交信息**: [Build] Bump vllm-flash-attn to C++20-compatible commit for torch-nightly (#49326)

Signed-off-by: Andrey Talman <atalman@fb.com>

### [1a659a0](https://github.com/vllm-project/vllm/commit/1a659a0c370942bae3c8567902e38bddbbae95f3)

- **作者**: Teresa Chen
- **时间**: 2026-07-22T11:52:56Z
- **提交信息**: Upgrade tpu-inference to v0.25.0 (#49431)

### [0f6cf7f](https://github.com/vllm-project/vllm/commit/0f6cf7f628de8f09f35bc871f28b28a5ecdf563b)

- **作者**: Sage
- **时间**: 2026-07-22T11:31:36Z
- **提交信息**: [Rust Frontend] Extract request preparation from the inference path (#49045)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [c79ad3a](https://github.com/vllm-project/vllm/commit/c79ad3ae213249760bc360b50eb733af1bf1f715)

- **作者**: Connor Carpenter
- **时间**: 2026-07-22T11:31:01Z
- **提交信息**: [Rust Frontend][gRPC] Add abort control RPC (#49255)

Co-authored-by: OpenAI Codex <codex@openai.com>
Signed-off-by: Connor Carpenter <connorc@nvidia.com>

### [61c9ef9](https://github.com/vllm-project/vllm/commit/61c9ef986a807aa3b9c6ccd25bb223b8f4116ac7)

- **作者**: wang.yuqi
- **时间**: 2026-07-22T10:56:23Z
- **提交信息**: [Frontend] Parallelize preprocessing within the same request for pooling models online serving. (#49153)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [d6dbdb9](https://github.com/vllm-project/vllm/commit/d6dbdb9b0d6e77b9ac4ef9b298d6dfd8f308b583)

- **作者**: Liangqiusong
- **时间**: 2026-07-22T08:16:13Z
- **提交信息**: [XPU] WA of topk_softplus_sqrt arg mismatch on XPU (#49408)

Signed-off-by: xiaolong <xiaolong.guo@intel.com>

### [06da482](https://github.com/vllm-project/vllm/commit/06da482fb43209978a42262597f9d3107e7302e4)

- **作者**: liuzhenwei
- **时间**: 2026-07-22T08:05:01Z
- **提交信息**: [XPU] WA of topk_softmax arg mismatch on XPU (#49395)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [2f75e7f](https://github.com/vllm-project/vllm/commit/2f75e7f712fb2a013ce05ff357d94135231c8ae2)

- **作者**: Kevin H. Luu
- **时间**: 2026-07-22T07:16:16Z
- **提交信息**: [CI] Increase timeouts for jobs exceeding current limits (#49374)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [7c21548](https://github.com/vllm-project/vllm/commit/7c21548ce38ffe691026edac4eac5a731757283b)

- **作者**: Ziming Huang
- **时间**: 2026-07-22T07:11:39Z
- **提交信息**: [PD][Bugfix] Fix NIXL hybrid MLA+mamba heterogeneous TP (#49297)

Signed-off-by: ZeldaHuang <zelda.huanghuang@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-23
**监控日期**: 2026-07-22
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5654
- **最后更新**: 2026-07-22T22:09:50Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 10
- **主要提交者**: Zeyu Huang | 黃澤宇, wangyu, vOv

## AI分析总结

### 1. 主要更新类型

- **Bug修复**（4个）：主要涉及多模态推理的稳定性、异步执行时的挂死、错误模态处理的返回、CI测试跳过问题。
- **重构/代码清理**（5个）：移除过时示例、清理冗余配置、淘汰死代码、迁移测试配置、统一Diffusion模型接口。
- **模型优化**（1个）：MiniCPM-o 4.5的SigLIP位置ID优化。
- **测试基础设施**（1个）：引入配置驱动的微小模型构建器。
- **CI/测试修复**（1个）：移除模态依赖跳过的逻辑。

### 2. 关键变更点与项目整体方向的关系

| 变更 | 与项目方向（多模态模型服务）的关系 |
|------|-----------------------------------|
| 修复Omni stage runners中的非positive token span | 直接保障多模态流水线切割的正确性，避免推理异常 |
| 修复NPU环境下full-payload异步请求的挂死 | 消除硬件（NPU）特异性阻塞问题，提升异构部署可靠性 |
| 返回明确错误而非空结果 | 改善用户对未支持模态的调试体验，符合“Easy”原则 |
| MiniCPM-o位置ID优化 | 提升具体多模态模型（视觉+文本联合编码）的推理性能与精度 |
| 清理Scheduler死代码 | 为后续多模态调度策略迭代腾出干净基础 |
| 清理Diffusion Model Runner/Worker接口 | 标准化扩散模型（如图像/视频生成）的服务化接口，便于扩展新模态 |
| 迁移Step-Audio2测试至deploy config | 测试配置统一，降低多模态模型上线门槛 |
| 移除sensenova示例 | 聚焦核心功能，减少维护负担 |
| 配置驱动tiny model builder | 简化微模型测试，加速多模态回归验证 |

### 3. 对项目的影响和潜在意义

- **稳定性提升**：修复了多模态同步/异步模式下、跨硬件（NPU）的挂死问题，对生产环境部署至关重要。
- **开发体验改善**：清理代码、统一接口、移除无效模块，降低新贡献者参与不同模态（文本、图像、音频、视频）开发的复杂度。
- **对上游vLLM的兼容性**：这次提交包含了对NPU runner的port（#5234→#5290），表明项目正积极跟进vLLM主线的硬件抽象结构。
- **模型支持深化**：对MiniCPM-o的优化表明项目不仅追求广度（多模态），也开始在单一模型上微调推理效率。
- **测试现代化**：Config-driven builder和deploy config迁移，使CI对多模态模型更敏捷、更可配置。

### 4. 值得关注的技术点

- **Omni stage runners**：是vLLM-Omni特有的流水线切割机制，修复非正跨度bug暗示其调度逻辑复杂度。
- **async_chunk=false**：在NPU runner上的挂死问题涉及推理预填充与解码的同步性，值得其他硬件使用者关注。
- **SigLIP位置ID优化**：在MiniCPM-o中可能通过更合理的position embedding对齐视觉和语言token，提升长文本/多图场景效率。
- **Diffusion Runner接口清理**：为将来集成更多生成模型（如Stable Diffusion、Flux等）提供了可扩展的基类。
- **[0/N] 系列重构**：Scheduler清理是系列重构的开端，暗示后续可能对多模态优先级、抢占等策略重做。

### 5. 对项目发展的影响（从背景出发）

> “Easy, fast, and

## 详细提交记录

### [f10320f](https://github.com/vllm-project/vllm-omni/commit/f10320f53fbe9290e4155f8e878febd9c18be71c)

- **作者**: Nick Cao
- **时间**: 2026-07-22T17:11:53Z
- **提交信息**: [Tests] Config driven tiny model builder (#5090)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [cc19391](https://github.com/vllm-project/vllm-omni/commit/cc1939120f3dc06c9456aa1165833545feccab5d)

- **作者**: vOv
- **时间**: 2026-07-22T16:01:45Z
- **提交信息**: [Bugfix] Skip non-positive scheduled token spans in omni stage runners (#5269)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [f44649f](https://github.com/vllm-project/vllm-omni/commit/f44649ffd0d84dcec228a615b9ccff8000894115)

- **作者**: 汪志鹏
- **时间**: 2026-07-22T15:36:00Z
- **提交信息**: [Refactor]: Remove sensenova examples (#5201)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [8219c01](https://github.com/vllm-project/vllm-omni/commit/8219c01b57ce41a5c15fa8af5a780f9d7899e0a3)

- **作者**: Weiming Liao
- **时间**: 2026-07-22T13:53:04Z
- **提交信息**: [Bugfix][NPU] Port OmniConnectorModelRunnerMixin to NPU runners to fix async_chunk=false full-payload hang (#5234) (#5290)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [23d0ee5](https://github.com/vllm-project/vllm-omni/commit/23d0ee5c0cfdadcd8b413f2de1625d26a54611e4)

- **作者**: Ricardo Noriega
- **时间**: 2026-07-22T11:00:01Z
- **提交信息**: [Bugfix] Return error for unsupported output modalities instead of empty choices (#4720)

Signed-off-by: Ricardo Noriega De Soto <rnoriega@redhat.com>

### [fb4dd41](https://github.com/vllm-project/vllm-omni/commit/fb4dd41d793da4c1f1e0383b1e7557ae7bab5cf7)

- **作者**: 汪志鹏
- **时间**: 2026-07-22T10:48:05Z
- **提交信息**: [Refactor]: Remove unnecessary config getattr (#5199)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [68ee52f](https://github.com/vllm-project/vllm-omni/commit/68ee52f4e739e31ff9fcab3f3a76aafde5614429)

- **作者**: Fyrgo
- **时间**: 2026-07-22T10:35:37Z
- **提交信息**: [Model] MiniCPM-o 4.5: optimize SigLIP position IDs (#5130)

Signed-off-by: 道路自信 <182356120+daoluzixin@users.noreply.github.com>
Co-authored-by: 道路自信 <182356120+daoluzixin@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [1984346](https://github.com/vllm-project/vllm-omni/commit/1984346bc7e53100f751fcf749d967306105fbf5)

- **作者**: rein yang
- **时间**: 2026-07-22T09:59:44Z
- **提交信息**: [Refactor] [0/N] Scheduler clean dead code (#5312)

Signed-off-by: R2-Y <ruiruyang2@gmail.com>

### [633ebbd](https://github.com/vllm-project/vllm-omni/commit/633ebbd8a41c149b673eb06ec461bae5294fc071)

- **作者**: Yukim1
- **时间**: 2026-07-22T09:44:27Z
- **提交信息**: [Refactor] Migrate Step-Audio2 online test to deploy config (#5309)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>

### [8fc9df4](https://github.com/vllm-project/vllm-omni/commit/8fc9df4331eea40bc1741a34e5cb61a1af3d04b0)

- **作者**: wangyu
- **时间**: 2026-07-22T09:29:59Z
- **提交信息**: [CI][Bugfix] remove module-level skip_if_gated_repo_inaccessible in flux kontext e2e (#5250) (#5297)

Signed-off-by: wangyu <410167048@qq.com>

### [9479720](https://github.com/vllm-project/vllm-omni/commit/9479720f81bc931bfc53e601ec619713e87b281c)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-07-22T09:07:36Z
- **提交信息**: [Refactor]: clean up diffusion model runner surface (#5218)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [f43d761](https://github.com/vllm-project/vllm-omni/commit/f43d761c26ed2e7031ebb43c4b83429526d76efb)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-07-22T09:07:09Z
- **提交信息**: [Refactor]: clean up diffusion worker interfaces (#5217)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
