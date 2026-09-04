# GitHub Stars 合并报告 - 2026-09-03

**合并日期**: 2026-09-04
**监控日期**: 2026-09-03
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


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2188
- **最后更新**: 2026-09-03T20:21:35Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Wenzhe Wang

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交属于**文档更新与CI（持续集成）修复**的混合类型，核心目标是确保文档构建过程无警告（warning-free），属于工程化质量改进。

**2. 关键变更点与项目方向的关系**  
- 变更聚焦于文档构建流程的严格性，要求所有文档构建必须零警告通过。  
- 这与VeOmni作为“模型中心化分布式训练配方库”的定位高度一致：项目强调可复现性和易用性，而文档是用户上手和社区协作的关键入口。零警告构建能减少用户因文档错误产生的困惑，提升项目专业性和可信度。  
- 同时，将CI与文档质量绑定，体现了项目对工程规范的重视，符合其作为开源基础设施项目的长期维护需求。

**3. 对项目的影响和潜在意义**  
- **直接影响**：减少文档中的潜在错误（如格式问题、无效链接、API引用错误），避免用户因文档缺陷而误用或放弃使用。  
- **间接影响**：通过CI强制约束，降低后续贡献者引入文档问题的概率，提升社区协作效率。  
- **潜在意义**：为未来扩展更多模态（如音频、视频）的训练文档奠定可靠基础，避免因文档质量瓶颈拖累新功能发布节奏。

**4. 值得关注的技术点**  
- 采用“零警告”作为CI门禁标准，而非简单检查构建是否成功，体现了对文档质量的精细化控制。  
- 该做法通常涉及对文档工具链（如Sphinx、MkDocs）的严格配置，可能包括对弃用API、未定义引用、代码块语法等问题的静态检查，值得其他文档密集型项目借鉴。

**5. 对项目发展的影响**  
- 结合README背景，VeOmni的目标是“扩展任意模态模型训练”，其核心价值在于提供多样化的分布式训练配方。清晰的文档是用户选择和使用这些配方的第一道门槛，本次提交直接强化了这一入口的可靠性。  
- 从长期看，零警告构建策略有助于项目在快速迭代（如新增训练策略、支持新硬件）时保持文档同步质量，避免技术债累积，为社区生态的健康发展提供保障。  
- 此外，该提交虽不直接涉及功能代码，但通过提升工程严谨性，间接增强了项目作为“配方动物园”的可信度，有利于吸引更多研究者贡献新模态的训练方案。

**总结**  
本次提交是一次典型的“基础设施加固”操作，虽无用户可见的功能变化，但通过强化文档质量门禁，为VeOmni的规模化扩展和社区协作奠定了更稳固的工程基础，体现了项目对长期可持续性的重视。

## 详细提交记录

### [2449609](https://github.com/ByteDance-Seed/VeOmni/commit/2449609f5e20b4c83c03c69c6496fc22b1a147ac)

- **作者**: Wenzhe Wang
- **时间**: 2026-09-03T07:28:50Z
- **提交信息**: [docs, ci] fix: enforce warning-free documentation builds (#1123)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2777
- **最后更新**: 2026-09-03T18:10:49Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yang Yong (雍洋)

## AI分析总结

### 主要更新类型
- **功能新增**：为训练和验证流程引入数据缓存支持。

### 关键变更点及与项目方向的关系
- 提交 `[Train]: Support cache data for train and val` 在训练与验证阶段增加了数据缓存机制。LightX2V 定位为轻量级视频生成推理框架，核心目标是降低视频生成的计算与存储开销。该变更直接服务于训练效率优化，通过缓存预处理后的数据，减少重复的数据加载与转换操作，从而加速训练迭代，与项目“轻量”和“高效”的核心理念一致。

### 对项目的影响和潜在意义
- **训练效率提升**：缓存机制可显著减少数据管道的I/O瓶颈，尤其对大规模视频数据集，能缩短每个epoch的训练时间，提升实验迭代速度。
- **资源利用率优化**：通过复用缓存数据，降低CPU/GPU空闲等待时间，提高整体硬件利用率，有助于在有限资源下进行更复杂的模型实验。
- **为后续扩展奠基**：该功能为未来支持更大规模数据集或更复杂的训练策略（如动态采样）提供了基础设施。

### 值得关注的技术点
- **缓存策略设计**：需关注缓存的数据格式（如内存映射、磁盘序列化）及缓存失效/更新机制，确保训练与验证阶段数据一致性。
- **内存与磁盘权衡**：缓存可能占用大量内存或磁盘空间，需考虑可配置的缓存大小与清理策略，避免影响系统稳定性。

### 对项目发展的影响
- 该提交强化了LightX2V作为“训练友好”框架的定位，不仅限于推理场景，还兼顾了模型开发阶段的效率需求。这有助于吸引更多研究者和开发者使用该框架进行视频生成模型的快速迭代，推动项目从单一推理工具向全流程开发平台演进。长期来看，数据缓存机制是构建可扩展训练流水线的基础模块，为后续支持分布式训练、数据增强等高级特性铺平道路。

## 详细提交记录

### [d067db3](https://github.com/ModelTC/LightX2V/commit/d067db3a24c21382bfb0f56c7f9485beec9f1122)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-03T17:26:49Z
- **提交信息**: [Train]: Support cache data for train and val (#1475)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2231
- **最后更新**: 2026-09-03T07:02:50Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6326
- **最后更新**: 2026-09-03T23:39:23Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 9
- **主要提交者**: Vincent, Alex Yang, Jonathan Dierksen

## AI分析总结

# FlashInfer 昨日提交综合分析

## 主要更新类型

昨日共10个提交，涵盖**功能新增**、**重构优化**、**Bug修复**及**CI/基础设施改进**。核心亮点包括：ReplaySSM自动调优、输出专用KDA解码、TP8全聚合矩阵乘法、SM103 NVFP4 warp解码，以及为Blackwell架构（SM100/SM103）引入全新的低延迟块缩放GEMM内核。

## 关键变更点与项目方向

- **ReplaySSM自动调优**：为SSM检查点推理引入框架无关的运行时自动调优，缓存最优策略，与FlashInfer“高性能推理内核”定位一致。
- **SM120稀疏MLA重构**：合并解码与预填充路径，用解析模型替代逐形状自动调优，消除硬编码T≤64限制，新增GLM53_NOPE和DOTS3_SWA模型支持。
- **KDA输出专用解码**：为vLLM Kimi K3循环验证提供即插即用替代，扩展对新兴模型架构的覆盖。
- **低延迟块缩放GEMM内核**：基于CuTe-DSL实现，支持FP4、FP8及混合FP8×FP4格式，以“cutedsl_low_latency”后端集成至mm_fp4、mm_fp8、mm_mxfp8 API，并扩展tgv_gemm_sm100实现稠密与块缩放格式的自动调度。支持可选偏置、FP32累加、split-K执行，生成所有策略组合并按布局/TMEM/SMEM约束过滤。
- **TP8扩展与NVFP4后端**：延续Blackwell优化路线，分别提升张量并行扩展性和低精度推理能力。

## 项目影响与意义

- 性能提升显著：SM120解码T=1延迟降低24%，TP8路由最高提速1.79倍。
- 架构覆盖扩大：SM107（Rubin）纳入FlashKDA运行时守卫，SM103获得NVFP4后端及低延迟GEMM支持。
- 生态集成深化：KDA内核与vLLM精确签名对齐，降低下游框架接入成本。
- 工程成熟度提升：CI引入CUDA 13.4缓存支持，测试摘要区分真实失败与超时。
- 代码量净增约3,470行，主要来自新内核及正确性测试，属较大规模功能扩展。

## 值得关注的技术点

- 自动调优采用冷L2和CUDA图分析，暴露scratch分配器保证图稳定性。
- 连续覆盖范围设计：解码支持任意head数，预填充支持任意T和topk%64==0宽度。
- 非2的幂次启动配置（如heads_per_group=14）通过验证，突破传统约束。
- 输出专用内核不写状态池，通过WY并行张量核路径实现1-16 token/序列处理。
- 低延迟GEMM后端要求SM100/SM103且M≤8，针对小批量推理优化；NVFP4要求K被64整除，MXFP4/MXFP8/静态FP8要求K被128整除；支持静态FP8使现有alpha参数可被块缩放内核应用。
- 正确性测试覆盖每个生成策略、边界情况、alpha、偏置、PDL及混合操作数格式，并对GPT-OSS-120B和DeepSeek-V3等真实模型形状进行验证。

## 对项目发展的影响

这批提交表明FlashInfer正从单一注意力内核库向**多架构、多模型格式的通用推理加速层**演进：通过自动调优框架降低手动调参成本，通过模型特定内核（KDA、MLA变体）紧跟前沿架构需求，同时以CI和代码所有权改进保障长期可维护性。对M≤8小形状的专门优化瞄准LLM解码阶段实际需求，SM107/SM103支持显示其硬件适配节奏与NVIDIA产品路线同步，为下一代GPU提前布局，有助于巩固其在生成式推理领域的竞争优势。

## 详细提交记录

### [b255f54](https://github.com/flashinfer-ai/flashinfer/commit/b255f54480b7754ea094a43575d0c2cfbd0bff18)

- **作者**: Andrii Skliar
- **时间**: 2026-09-03T23:39:10Z
- **提交信息**: Add ReplaySSM autotuning (#4545)

## Summary

Adds framework-agnostic runtime autotuning for ReplaySSM checkpointing
SSU. For eligible dense decode workloads, FlashInfer profiles supported
monolithic and two-kernel launches and caches the fastest tactic for
reuse.

## What changes

- Exposes main-kernel pipeline stages and CTAs per SM as runtime launch
controls, alongside the existing precompute heads-per-CTA control.
- Adds a `CheckpointingSSURunner` that tunes the algorithm, `d_split`,
main launch geometry, and precompute grouping through FlashInfer's
generic autotuner.
- Buckets the active batch dimension while profiling compact private
state/ring buffers, preserving the production `dt` broadcast layout and
representative replay history.
- Uses cold-L2 and CUDA-graph profiling, and exposes a scratch allocator
so inference frameworks can provide graph-stable two-kernel workspace.
- Keeps explicit algorithm/launch overrides and unsupported
configurations on the normal fallback path.

## Scope

Generic autotuning is enabled only for dense calls (`cu_seqlens is
None`) with the two-kernel scratch buffers present and launch controls
left on automatic selection. The implementation contains no
vLLM-specific policy or state.

## Validation

- Base-head H100 focused suite: 7 passed, covering scratch allocation,
dynamic profiles, cache keys, tactic generation, `d_split`, autotune
cache reuse, and monolithic/two-kernel parity.
- Review-followup H100 checks: 3 focused tests passed, and the newly
admitted non-power-of-two launch (`heads_per_group=14`,
`heads_per_cta=3`) compiled and executed successfully.
- H100 `autotune(True)` wall clock at `max_batch=1024`: **63.856
seconds** with a warm JIT module and empty autotuner cache. This used
dense `T=4`, BF16 inputs, FP32 state, and Nemotron TP8 geometry
(`nheads=16`, `ngroups=1`, `head_dim=64`, `d_state=128`); all 12 batch
buckets were saved (3,574 distinct tactic profiles after launch
deduplication).
- Pre-commit and public API/documentation checks pass. The full
repository test matrix is pending maintainer CI authorization.

---------

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Albert Cheng <albecheng@nvidia.com>

### [453aa7c](https://github.com/flashinfer-ai/flashinfer/commit/453aa7c7296e9ec711fd4c1f3aa6ee061a6b69dc)

- **作者**: Gabriel Wu
- **时间**: 2026-09-03T22:50:33Z
- **提交信息**: Refactor Sparse MLA SM120 (#4802)

## Summary

Consolidated SM120 sparse-MLA rework, decode + prefill. All numbers on
RTX PRO 6000 (SM120).

- **Faster decode, small T**: T=1 14.9 → **11.3µs** (−24%, graph replay,
dual-cache 18K context); bitwise-identical outputs.
- **Calibrated dispatch**: an analytical `chunks_per_block` model +
measured decode/prefill crossover replace the per-shape autotune sweep
and the hard `T ≤ 64` cutoff (up to −61% on rerouted configs; tables
below).
- **Continuous envelopes**: decode serves any `num_heads ∈ [1,128]` and
any `topk ≥ min_topk`; prefill serves any `T ≥ 1` and any `topk % 64 ==
0` width. Runtime-topk prefill drops instantiations **75 → 55**.
- **swapAB prefill** carried from #4751 behind a per-call `prefill_impl`
override; independently re-benched at **1.12–2.37×** over MG.
- **Two new model types**: `GLM53_NOPE` (carried from #4791) and
`DOTS3_SWA` (sliding-window MLA, d_qk=1088, d_v=1024, 1160 B/token
footer-scale, padded-row KV support) — the latter also fixing five
latent bugs along the way (rope writeback overrun at D_V==D_NOPE,
flat-vs-paged addressing keyed on the wrong trait, a Python chunk-width
hardcode, an undersized amax scratch at 4 math warps, a vestigial SG
register array).
- **Public runner**: `flashinfer.mla.SparseMLASm120Wrapper` — one
persistent instance, memoized dispatch, CUDA-graph-safe (decode scratch
is routing-aware and instance-owned).
- Merged current main, incl. the #4732 SM121 prefill-hang fix.
- Also: row-strided `indices` (unblocks vllm-project/vllm#53574's
persistent-buffer narrowing) and row-strided `out_lse`; T=0 decode
returns empty instead of aborting; decode bindings now validate
`out_lse`/index dtypes/dim0.

Carries (authorship preserved): #4461 zero-token decode (rewritten;
XingSong), #4551 dispatch diagnostics +
`supported_sparse_mla_sm120_configs()` (Sam Mausberg), #4751 swapAB
(Lemon7-UP), #4791 GLM53_NOPE (lucamotz; extended with H=64/TP1 decode,
swapAB@2176, calibration coverage). Supersedes #4683: its per-shape
sweep profiles L2-resident synthetic indices, which distorts cpb when
production caches are DRAM-resident (observed on 5070 Ti) — this PR
removes the sweep instead (thanks Sam for the original analysis).

## Performance vs main (adc49a85)

Same GPU, fixed-seed identical inputs, CUDA-graph replay GPU-only, both
sides out-of-box (no tactic cache / no calibrated constants). Only
surfaces present on both sides listed.

| shape | main | PR | speedup |
|---|---|---|---|
| dsv4-dual-h64 (topk 128+512), T=1 | 14.80µs | 11.40µs | 1.30x |
| dsv4-dual-h64 (topk 128+512), T=8 | 19.80µs | 16.14µs | 1.23x |
| dsv4-dual-h64 (topk 128+512), T=16 | 36.66µs | 29.46µs | 1.24x |
| dsv4-dual-h64 (topk 128+512), T=64 | 97.19µs | 89.79µs | 1.08x |
| dsv4-h128 (topk 1024), T=1 | 14.70µs | 11.44µs | 1.29x |
| dsv4-h128 (topk 1024), T=64 | 231.60µs | 219.79µs | 1.05x |
| dsv3_2-h64 (topk 2048), T=1 | 14.08µs | 10.68µs | 1.32x |
| dsv3_2-h64 (topk 2048), T=64 | 216.78µs | 220.23µs | 0.98x |
| dsv3_2-h128 (topk 2048), T=1 | 16.57µs | 14.08µs | 1.18x |
| dsv3_2-h128 (topk 2048), T=64 | 324.19µs | 323.53µs | 1.00x |
| dsv4-prefill-h128 (topk 1024), T=128 | 293.82µs | 266.49µs | 1.10x |
| dsv4-prefill-h128 (topk 1024), T=2048 | 4486.89µs | 3928.68µs | 1.14x
|
| dsv4-prefill-dual-h64 (topk 128+512), T=128 | 124.66µs | 124.64µs |
1.00x |
| dsv4-prefill-dual-h64 (topk 128+512), T=2048 | 1559.56µs | 1559.35µs |
1.00x |

Decode gains concentrate at small T (launch-bound); the two decode
commits behind them: `quantize_q_to_smem` rewritten as a vectorized
single pass (3 `bar.sync` → 1), and the decode-dsv4 IO gather reads each
candidate's index once instead of twice. T=64 decode and dual-cache
prefill are unchanged within noise.

## swapAB prefill (#4751)

Re-benched on the PRO 6000 (#4751's table was measured on a PRO 5000),
same grid, MG↔swapAB cross-checked at 5e-2 on identical inputs, `auto`
bitwise-identical to forced swapAB:

| shape | MG | swapAB | speedup |
|---|---|---|---|
| H=64, T=128 | 250.8µs | 159.7µs | 1.57× |
| H=64, T=512 | 798.7µs | 565.6µs | 1.41× |
| H=64, T=2048 | 2948.1µs | 2158.6µs | 1.37× |
| H=64, T=8192 | 11673.6µs | 8607.7µs | 1.36× |
| H=128, T=128 | 349.6µs | 267.9µs | 1.30× |
| H=128, T=512 | 1348.2µs | 840.0µs | 1.60× |
| H=128, T=2048 | 5330.9µs | 3011.6µs | 1.77× |
| H=128, T=8192 | 21156.9µs | 11847.7µs | 1.79× |

Wins everywhere; the H=64 large-T plateau (~1.4×, one CTA per token
saturates ~1280 GB/s vs ~1860 at H=128) is a flat asymptote out to
T=32768, so no dispatch range limit. KV layout and all parameters
unchanged; both scale formats, sinks, and variable `topk_length`
supported. `prefill_impl`: `"auto"` (default) / `"swapab"` / `"mg"`;
forcing swapab at an ineligible shape raises.

## Dispatch: cpb model + crossover

**cpb model** — analytical pick over gather bandwidth/latency, per-block
overhead, and the exact list-scheduling makespan of the split grid, with
an L2-footprint guard rail (at topk=1024+2176 dual the heuristic picks a
single 50-chunk block at 2.7× L2 — ncu: L2 hit 69.7% vs 86.8%, costing
33%; the guard recovers it to 1.02×). Calibrated once per device inside
`autotune()` tuning mode (6 fixed measurements over a ~2 GiB pool, timed
as queued batches over rotating fresh index sets — launch latency
overlaps execution, and the batch length keeps each set's reuse distance
past an L2 turnover; small numpy LM fit; any failure = silent fallback
to the C++ heuristic, so the new path can't be worse than status quo).
Offline pick error vs exhaustive sweep (DRAM-cold protocol): **mean
1.011× / max 1.061×**; beats the heuristic by up to **1.37×** at mid
shapes. A GPU accuracy-guard test fails loudly if a future kernel change
breaks the model's assumptions, measured with the same protocol the
calibration runs. Host cost ~8µs/call, memoized; zero per-replay under
CUDA graphs.

**Per-shape refinement** — the model's residual pick error concentrates
at mid-T wave-quantization shapes (measured up to **1.35×**, e.g.
DOTS3_SWA T=32: 78.0µs → 57.8µs). tuning-mode decode-form calls time the
model pick ±6 candidates with the calibration protocol and persist the
measured best as a per-shape override in the same tuning cache;
`_resolve_cpb` consults overrides first, then the model. Across 12
production bucket shapes (T=16..64, three families, two-pass re-timing):
**never worse than the model (12/12), closes every pocket to ≤1.03×**.
Shapes never warmed (off-graph calls, arbitrary T, dual-cache) stay on
the model. Capture-time calls only read the table/model and freeze — no
measurement ever runs under graph capture or in serving.

**Crossover** — per-config `decode_max_tokens` measured during the same
tuning pass (probe T ∈ {4..64}, both paths, DRAM-faithful fresh indices;
decode wins iff ≤ 0.95× prefill). Uncalibrated behavior is unchanged.
Measured examples:

| config | `decode_max_tokens` | Σ T∈{24,32,48,64}: old policy →
calibrated |
|---|---|---|
| DSv3.2 H=128 topk=2048 (swapAB side) | 8 | 1271.4 → 494.0 µs (−61%) |
| DSv4 H=64 topk=512 | 24 | 292.3 → 216.7 µs (−26%) |
| DSv4 H=64 topk=128 | 16 | 132.3 → 96.7 µs (−27%) |
| DSv4 H=8 topk=1024 | 64 (decode dominates) | no rerouting |

Full per-probe data for all 71 calibrated configs: kernel-bench
`crossover-v5` baseline. A public `calibrate_sparse_mla_sm120(device,
heads=, topks=, families=, force=)` makes any envelope shape tunable
outside tuning mode (idempotent skip-existing; `force=True`
re-measures).

## Runtime envelopes (head counts and topk widths)

- **Decode**: any H ∈ [1,128] — dedicated instantiations on the
production grid (0.9–2.5% faster), one runtime-H instance otherwise,
**40/40 bitwise-identical** between the two. Any `topk ≥ min_topk` (1;
513 for DOTS3_SWA so the window fits). The `_DECODE_*_DISPATCH` objects
vLLM probes are membership predicates with exactly this meaning;
`supported_sparse_mla_sm120_configs()` exposes the envelopes for
init-time validation. Off-grid example: H=80 T=16 is 1.14× faster than
the pad-to-128 workaround callers needed before.
- **Prefill**: same topk rule across SG / MG / dual / swapAB. One
deliberate residual asymmetry: **decode serves ragged widths (partial
tail chunk, tested at topk=500); prefill requires whole 64-wide index
tiles** — all production topk widths qualify, tail support needs
predicated gathers + tail masking across the IO and math paths, and is
deferred until a model needs it. This is safe at the routing layer: a
ragged decode-form call has no prefill envelope and simply stays on
decode (no crossover), and a ragged T>64 call fails loudly at the
binding. 50-config parity vs the pinned build: worst **+0.94%**. One
variant needed kernel-side help: DOTS3_SWA SG's BI=32 tiles are too
short to cover the index→rope address-chain latency once the
compile-time trip count disappeared (+24% `long_scoreboard` in NCU). The
SG loop now stages the three per-tile index reads one tile ahead in
registers, `if constexpr`-scoped to short tiles (unconditional staging
taxed BI=64 SG +2.3%). Net: **374.6µs vs the pinned build's 380.7µs** at
H=64/T=256, registers flat, `long_scoreboard` back to parity.

## Plan layer

All dispatch policy lives in one memoized Python planner
(`_sparse_mla_sm120_plan.py`): each variant declares its envelope once,
`plan()` picks by envelope + crossover + `prefill_impl`. The C++ side is
a policy-free launcher registry (the old `dispatch_v32` chain is
deleted). Single-sourcing surfaced two latent upstream bugs, fixed here:
prefill launchers never checked `page_block_size` against the compiled
64 (silent wrong-stride launch), and dual-cache decode-form
DSv3.2-family calls silently ignored the secondary cache.

## Runner and CUDA graphs

`SparseMLASm120Wrapper` holds buffers persistently: LSE pre-sized at
construction, decode split-K scratch allocated only when the call
actually routes to decode and cached for the instance's lifetime (a
per-call temporary's freed block can be recycled into a later capture
while an older graph replays into it). Capture contract: construct and
warm up every captured shape before capture (or pass `out_lse`/scratch
explicitly); replay is pure graph replay with zero Python. Both routing
variants are correct for any T, so a crossover inside a padding bucket
is at worst suboptimal, never wrong. GPU tests pin capture/replay for
crossover dispatch and for runner-internal scratch.

## Compatibility

Public Python API: unchanged except additive kwargs; `flashinfer.mla`
exports purely additive; no-constants path behaves exactly as today.
Deliberate behavior changes:

- Per-shape tactic caches (`sparse_mla_sm120_decode_dsv{4,3_2}.json`)
are ignored; the new calibration file is schema-versioned (v1),
unrecognized versions treated as absent and recalibrated.
- `autotune(True)` runs a one-time-per-device calibration (~2 GiB
transient pool) instead of profiling each new shape; honors
`skip_ops={"sparse_mla_sm120"}`; refuses to run under CUDA graph
capture; cache writes serialized with a FileLock.
- With calibration present, decode-form calls beyond the measured
crossover route to prefill (the point of the feature).
- T ≤ 64 shapes outside the old fixed grid now take the runtime decode
instantiation instead of raising.
- Prefill serves any `topk % 64 == 0` (≥ 513 for DOTS3_SWA); ragged
widths fail at the binding.
- Inline-scale (DSv3.2/GLM) KV caches must be contiguous through the
paged entry (prefill flat-addresses the cache and crossover makes
routing dynamic); contiguous padded-row caches remain decode-served and
fail loudly only if prefill-routed.
- `indices`/`out_lse` may be row-strided views (widening); the decode
binding previously corrupted a strided `out_lse` silently.
- C++ launcher entries gained row-stride parameters — internal to the
JIT module, no stable ABI consumers.

Out of scope (tracked follow-ups): H=64 swapAB bandwidth at large T; a
pinned-topk fast path à la decode-H for DOTS3_SWA SG (locked clocks show
~2% there, boost clocks show nothing — not worth the instantiation axis
on current evidence).

## Test plan

All on RTX PRO 6000: **658 passed** across
`test_sparse_mla_sm120{,_dispatch,_cpb_model}.py` and
`test_autotuner_core.py`, pre-commit clean — including the 68-config
small-T prefill matrix vs the reference (T ∈ {1..64} × SG/MG/swapAB/dual
× sink/truncation), 27 C++⟺Python envelope-consistency probes,
runtime-H/topk parity gates (bitwise where required), crossover routing
+ CUDA-graph capture/replay tests, runner scratch routing/lifetime
tests, and the review-round regression tests (row-strided `out_lse`, cpb
save/publish/FileLock, grid-completeness gating, padded-cache rejection,
skip_ops/capture guards).

This PR was prepared with AI assistance; all changes reviewed and tested
locally by the submitter.

---------

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: XingSong <sunwenhan@xfusion.com>
Co-authored-by: Sam Mausberg <samuelmausberg@gmail.com>
Co-authored-by: Lemon7-UP <fearless192@163.com>
Co-authored-by: Luca Motz <321921718+lucamotz@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Brian K. Ryu <bryu@nvidia.com>

### [5377916](https://github.com/flashinfer-ai/flashinfer/commit/53779166d09ada303ecdd8043277d1a8b88020fb)

- **作者**: ameynaik-hub
- **时间**: 2026-09-03T22:12:40Z
- **提交信息**: feat(kda): output-only KDA decode + drop-in for vLLM Kimi K3 recurren… (#4709)

# Output-only KDA decode + drop-in for vLLM Kimi K3 recurrent verify

An output-only (frozen-state) Kimi Delta Attention decode kernel — the
KDA
analog of the GDN WY output-only kernel (flashinfer #3908) — and a
verified
drop-in replacement for the recurrent speculative-verify kernel from
[vLLM PR #52993](https://github.com/vllm-project/vllm/pull/52993).

## Files

| File | Role |
|---|---|
| `flashinfer/kda_kernels/kda_decode_wy_output_only.py` | kernel
(self-contained; reuses PTX helpers from
`gdn_decode_bf16_wy_output_only` and gate helpers from
`kda_kernels/recurrent_kda`) |
| `flashinfer/kda_decode.py` | public API + docstrings |
| `flashinfer/__init__.py` | exports |
| `flashinfer/trace/templates/kda.py` | trace template |
| `docs/api/kda_decode.rst` | docs |
| `tests/kda/test_kda_output_only.py` | 39 tests |
| `benchmarks/bench_kda_output_only.py` | benchmark |

## API

1. `flashinfer.kda_output_only_decode(q, k, v, g, beta, state_pool,
   state_indices, ..., emit_corrections=False, backend="auto")`

Computes outputs for 1..16 tokens/seq from a read-only state pool; never
   writes state. Backends: `"wy"` (WY-parallel tensor-core kernel:
per-K-channel decay folded into `k*exp(±cumsum g)` / `q*exp(cumsum g)`
   operand tiles, T×T triangular inverse via register-resident block
   forward-substitution, TMA-streamed state GEMMs) and `"recurrent"` (a
   grouped register recurrence for tiny batches); `"auto"` dispatches by
   measured crossover. `emit_corrections=True` additionally returns
   corrections `U_t = sigmoid(beta_t) * (v_t - u_t)` and a kg cache.

2. `flashinfer.kda_recoverssm_verify(q, k, v, raw_g, raw_beta, A_log,
   dt_bias, lower_bound, checkpoint_state, correction_cache, kg_cache,
   query_start_loc, state_indices, spec_query_len, out=None)`

   Exact signature and contract of
`vllm/models/kimi_k3/nvidia/ops/recoverssm.py::kda_recoverssm_verify`:
varlen-packed inputs with runtime per-sequence lengths and token
strides,
   null-slot semantics (`state_indices <= 0` → zero outputs, no cache
writes), slot-indexed caches with rows past `query_len` left untouched.

## Precision

| | |
|---|---|
| inputs | `q/k/v/raw_g/raw_beta` bf16; `A_log/dt_bias` fp32;
`checkpoint_state` pool bf16 (the vLLM default:
`mamba_cache_dtype="auto"` → model dtype) |
| compute | bf16 tensor-core MMAs with fp32 accumulation; in-kernel L2
norm (eps 1e-6), gate transforms and beta sigmoid in fp32 |
| outputs | attention out bf16 `[1, total_tokens, H, 128]`;
`correction_cache` fp32 `[blocks, H, spec_len, 128]` (stored from fp32
MMA fragments, no bf16 rounding on the store); `kg_cache` bf16 `[blocks,
H, spec_len, 256]` = raw k \| raw g, bit-exact vs the vLLM kernel |
| accuracy | vs fp32 reference: outputs ~2e-4; vs vLLM's Triton kernel
on identical inputs: outputs ≤ 4.9e-4 (bf16 rounding, summation order),
corrections ≤ 1.6e-2 (their all-fp32 math vs bf16 MMA), kg bit-exact,
untouched cache bytes identical |

## Benchmark

**Baseline:** the recurrent verify kernel
(`_kda_recoverssm_verify_kernel`, a
serial token-by-token Triton recurrence) from vLLM PR #52993 — the
optimized
"New" version fetched from the PR head (`pull/52993/head`; vLLM main
predates the PR's verify tuning: batch-sensitive BV, `num_warps=1`,
eviction hints).

**Config:** 1× B200 (SM100); Kimi K3 TP=8 shard = 96 total KDA heads / 8
→
H = HV = 12 heads/GPU, K = V = 128; T = 8 tokens/seq (uniform);
`lower_bound = -5` gate with `dt_bias`; beta logits; bf16 state pool;
batch B = 1..512; both kernels fed byte-identical tensors and producing
the
full verify contract (out + fp32 corrections + kg).

**Method:** `flashinfer.testing.bench_gpu_time(fn, enable_cupti=True,
dry_run_iters=10, repeat_iters=50)` — per-iteration CUPTI GPU kernel
time
with L2 flushed before every iteration (cold cache); median of 50. All
three output artifacts refchecked between the two kernels at every point
before timing. Harness anchored externally: it reproduces the GDN WY
PR #3908 endpoint (132.2 vs 129.7 µs published) and, under hot L2, the
vLLM PR #52993 published B300 verify table within ~4–8%.

| B | flashinfer (µs) | vLLM PR recurrent (µs) | speedup (cold L2) |
|---|---|---|---|
| 1 | 6.94 | 10.46 | 1.51× |
| 2 | 6.96 | 11.07 | 1.59× |
| 4 | 7.25 | 12.05 | 1.66× |
| 8 | 7.39 | 15.52 | 2.10× |
| 16 | 8.42 | 20.03 | 2.38× |
| 32 | 9.63 | 37.12 | 3.85× |
| 64 | 17.63 | 69.30 | 3.93× |
| 128 | 27.14 | 123.07 | 4.54× |
| 256 | 48.11 | 257.86 | 5.36× |
| 512 | 91.74 | 537.95 | 5.86× |

Hot-L2 speedups match (1.40×–5.96×).

### DP / lower-TP configurations

Same setup at larger per-GPU head counts (DP = no TP sharding = all 96
KDA
heads on one GPU), refchecked per point:

| H (TP) | B=1 | B=8 | B=32 | B=128 | B=256 |
|---|---|---|---|---|---|
| 24 (TP=4) | 1.58× | 3.36× | 3.90× | 5.38× | 5.91× |
| 48 (TP=2) | 1.59× | 4.45× | 4.65× | 5.96× | 6.10× |
| 96 (DP) | 2.19× | 4.45× | 5.51× | 6.23× | 6.15× |

(e.g. H=96, B=128: 178.9 µs vs 1114.9 µs.)

## Correctness checking

`pytest tests/kda/test_kda_output_only.py` (39 tests): fp32 recurrent
reference across gate modes / GQA / ragged T / odd batches; RecoverSSM
contract tests (ragged lengths, null and negative slots, fp32
corrections,
raw-k|raw-g kg, checkpoint-pool immutability); cross-check vs
`flashinfer.recurrent_kda`; preallocated-output paths.

For the direct diff against vLLM's Triton kernel, fetch
`vllm/models/kimi_k3/nvidia/ops/recoverssm.py` from `pull/52993/head`
and
run it standalone next to `kda_recoverssm_verify` on identical inputs (a
local harness exists but is intentionally not committed, as it depends
on
the vLLM source file).

**Limits** (clear errors, no silent fallback): K = V = 128,
`spec_query_len <= 16`, bf16 checkpoint pool, SM90+ (validated on SM100a
/ B200).
Checkpoint blocks must be dense `[H, V, K]`, but the pool's block stride
may
be padded (16 B-aligned) — the stride is a runtime kernel argument, so
one
compiled kernel serves any padding (validated vs the vLLM Triton kernel
with
128/256/1024-element paddings, padding bytes verified untouched).



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

- **New Features**
- Added output-only KDA decoding for speculative verification using
read-only committed state.
  - Added automatic, WY, and recurrent backend selection.
  - Added optional correction and key/gate cache outputs.
  - Added a RecoverSSM verification API with top-level package access.
- Added trace support for sequences of up to 16 tokens on supported
hardware.

- **Documentation**
- Documented supported inputs, constraints, backend behavior, usage, and
tuning options.

- **Tests**
- Added coverage for accuracy, backends, ragged sequences, output
buffers, optional outputs, and state immutability.

- **Benchmarks**
  - Added configurable GPU latency and dispatch speedup benchmarks.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [7a3c04f](https://github.com/flashinfer-ai/flashinfer/commit/7a3c04f0156f1a1913d3f1a2928372c214322316)

- **作者**: Alex Yang
- **时间**: 2026-09-03T20:24:38Z
- **提交信息**: Modify CODEOWNERS - Anik (#4937)

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

* **Chores**
* Updated code ownership assignments for the MOE_EP source and test
areas.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2c9e6b1](https://github.com/flashinfer-ai/flashinfer/commit/2c9e6b1350f1f816a25ca19c767ad268c6df3eac)

- **作者**: Jonathan Dierksen
- **时间**: 2026-09-03T19:47:18Z
- **提交信息**: ci: enable patched sccache for CUDA 13.4 (#4808)

## 📌 Description

Enable NVCC caching for CUDA 13.4 by building sccache from pinned
upstream merge commit `e9b15a35f7240a7edd1b9644583edb388c6cb5f9`, which
contains the CUDA 13.3+ dry-run parser fix.

- Build the checksum-verified source natively in the existing x86_64 and
aarch64 manylinux builders.
- Keep CUDA 12.9 and 13.0 on the official sccache v0.17.0 binaries.
- Build only the S3-enabled sccache feature set with the locked
dependency graph and its supported vendored OpenSSL option.
- Remove AWS cache credentials from the Cargo build environment.
- Default the Release workflow to the public sccache bucket and region
when fork PR variables are unavailable, enabling anonymous read-only
caching and exercising the patched build in PR CI.
- Re-enable `FLASHINFER_NVCC_LAUNCHER=sccache` for CUDA 13.4.
- Build cu134 sccache in a dedicated `Build patched sccache (<arch>)`
Actions step in both Release and Nightly Release, preserving elapsed
timing even when the step fails.
- Pass the resulting native binary into the subsequent wheel-build
container through the shared CI cache mount.
- Cancel superseded Release dry-runs per PR while keeping real release
dispatches independent.
- Default the workflow token to contents: read, with actions: read and
contents: write granted only to create-release.
- Record the sccache install source and exact revision in the existing
stats artifact.

This is intended as a temporary bridge until an official sccache release
contains the upstream parser fix.

## 🔍 Related Issues

- https://github.com/mozilla/sccache/pull/2722

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

Validation completed locally:

- `pre-commit run --all-files`
- `bash -n scripts/build_patched_sccache.sh
scripts/jit_cache_build_common.sh
scripts/build_flashinfer_jit_cache_whl.sh
scripts/task_test_jit_cache_package_build_import.sh`
- `shellcheck scripts/build_patched_sccache.sh
scripts/jit_cache_build_common.sh
scripts/build_flashinfer_jit_cache_whl.sh`
- YAML parsing for both Release workflows
- Mocked routing checks for CUDA 13.4 on x86_64 and aarch64 and
unchanged release routing for CUDA 12.9/13.0
- Mocked launcher check confirming cu134 enables both C++ and NVCC
sccache launchers
- Reverified the pinned GitHub source archive SHA256
- Verified the pinned Cargo lockfile contains the vendored OpenSSL
dependency
- Rebased onto current `main` and reran the changed-file validations

Native Linux builds remain for the PR release workflow matrix, which
covers both x86_64 and aarch64.

## Reviewer Notes

Please compare the dedicated patched-sccache Actions step duration and
the resulting NVCC cache statistics for both cu134 architectures. The
source build intentionally remains scoped to cu134; other CUDA variants
continue using the published v0.17.0 artifacts.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
  * Improved build-cache reliability for CUDA 13.4 environments.
  * Ensured the CUDA compiler consistently uses the configured cache.
* Added build metadata identifying the cache implementation and
revision.

* **Chores**
  * Added validated, reproducible cache builds for CUDA 13.4.
  * Added support for released or pinned cache binaries.
  * Added automated verification for patched cache binaries.
  * Improved release workflow handling and pull request checks.
* Added fallback cache storage settings when release configuration is
unavailable.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [03d8b2c](https://github.com/flashinfer-ai/flashinfer/commit/03d8b2cd33459b5dc66c6187a2b47e02f83a2fe3)

- **作者**: Vincent
- **时间**: 2026-09-03T17:17:17Z
- **提交信息**: fix(kda): accept SM107 (Rubin) in the FlashKDA family guards (#4710)

## Summary

Accept SM107 (Rubin) in the FlashKDA runtime guards, and refresh the JIT
cache
keys that the guard edit invalidates.

> **Scope note (updated).** This PR originally also carried
`topk_varlen`,
> `routergemm`/tinygemm2 and MoE test changes. Those are gone:
> `top_k_varlen` SM107 support landed on `main` independently via #4621,
> tinygemm2 SM107 support via #4849, and the MoE test-classification
hook was
> reverted within this branch (`2a376e647`). What remains is FlashKDA
only.
> Earlier review comments referencing tinygemm2 or `routergemm` no
longer apply
> to the diff.

### 1. `fix(kda)` — FlashKDA family guard

The family build is compiled for `sm_100f`, a family-conditional target
valid
across the whole SM100 line including 10.7, but the runtime
`TVM_FFI_ICHECK`
admitted only 10.0/10.3. The check was stricter than the binary it
guards.
Widened at all four binding sites:

* `csrc/kda/flashkda_binding_common.cuh`
* `csrc/kda/flashkda_decode_binding_common.cuh`
* `csrc/kda/cake_kda_packed_t1_binding.cuh`
* `csrc/kda/cake_flashkda_packed_t1_binding.cuh`

The exact-target branch (`FLASHINFER_FLASH_KDA_TARGET_MINOR`, `sm100a`
builds)
is deliberately untouched — an `sm_100a` cubin genuinely is not runnable
on 10.7.

This widens the C++ guard only; the Python entry points still restrict
KDA to
10.0/10.3, so enabling KDA on Rubin end-to-end remains separate work.

### 2. `fix(jit)` — refresh the FlashKDA cache keys

`_FLASH_KDA_MODULE_IDENTS` and `_FLASH_KDA_TRAINING_MODULE_IDENT` are
SHA-256
digests over each variant's sources **plus the shared binding header**,
so
editing `flashkda_binding_common.cuh` invalidates them by construction.
Eleven
of the eighteen variant keys change here, along with the training key
(`118da6c1ae`) and the three `tests/jit/test_flash_kda_*` assertions
that pin
them.

**This is the trap in this PR.** The keys went stale twice during review
—
once when the guard was first widened, and again when a `main` merge
pulled in
#4675, which also edits that header. Both times CI failed identically:

```
assert 'flash_kda_training_<old>_sm100a' == 'flash_kda_training_<new>_sm100a'
```

Anyone rebasing or merging `main` into this branch must recompute the
digests
afterwards, not just resolve the textual conflict. `tests/jit/`
recomputes them
from the files, so a green `test_flash_kda_*_jit` run is the check.

## Validation

| Change | Before | After |
|---|---|---|
| kda guard | guard rejects 10.7 | freshly JIT-compiled `sm_100f` module
builds and loads on 10.7 |
| cache keys | `test_flash_kda_training_jit` 18 failures across
B300/GB200/GB300/H100/RTX Pro 6000 | digests recomputed; both targets
`118da6c1ae` |

No behaviour change on any non-107 device: every edit either adds 107 to
a
predicate that previously excluded it, or refreshes a cache key.

## Notes

* `main` has been merged in twice (`f4b79869d`, `0e4ed81a3`). The second
  resolution took `main`'s side wholesale on `csrc/tinygemm2_sm100.cu`,
  `flashinfer/jit/tinygemm2.py`, `flashinfer/gemm/routergemm.py` and
`flashinfer/topk_varlen/topk_varlen.py`, since #4849/#4621 rewrote them
— in
particular `main`'s tinygemm2 gate is a superset of what this branch
had.
* A `tests/model_optimizations/test_tinygemm2_sm100.py` capability-gate
fix was
dropped from this PR (`1921d560c`) as out of scope. It belongs with
#4849,
which enabled tinygemm2 on SM107 but shipped only three files and left
the
test's gate (`is_sm100a_supported`, i.e. `major == 10`) looser than the
  kernel's. **Still unlanded** — needs a follow-up PR.
* One unrelated CI failure is outstanding:
`tests.gemm.test_groupwise_scaled_gemm_fp8`,
1 failure on GB200 / CUDA 12.9. This PR touches no groupwise or
scaled-GEMM code.

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [1dff49b](https://github.com/flashinfer-ai/flashinfer/commit/1dff49bcb36299546e81bd12c6e967e2b0e3578c)

- **作者**: Adrian
- **时间**: 2026-09-03T14:56:17Z
- **提交信息**: ci: Improvement in test runner summary output (#4895)

## 📌 Description

Improve the test runner summary and allow verifying repo state with
SOURCE_GIT_SHA

The test runner summary will now (1) print the versions of dependent
libraries (2) separate failed test nodes due to timeouts from actual
failures (3) when printing the test files with failures, also print the
count of failed nodes.

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

Supersedes https://github.com/flashinfer-ai/flashinfer/pull/4552


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Terminal summaries now report Python, CUDA, PyTorch, and related
package versions.
- Test results distinguish genuine test failures from synthetic timeout
failures, with separate file lists and node counts.
  - Failure diagnostics and log paths are presented more clearly.

- **Bug Fixes**
- Resuming a test plan is no longer affected by changes to timing
estimate inputs.
- Test-start output has been simplified for clearer progress reporting.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [87ad818](https://github.com/flashinfer-ai/flashinfer/commit/87ad818ab2ea6869582920014dff111498c51158)

- **作者**: eigen
- **时间**: 2026-09-03T14:11:02Z
- **提交信息**: feat(cake_comm): extend Blackwell all-gather matmul to TP8 (#4822)

## Summary

Extends the Blackwell all-gather matmul implementation added in #4722 to
tensor-parallel world size 8 while preserving the existing TP2/TP4
paths.

- Adds eight-rank barrier and main-kernel routes.
- Supports the TP8 BF16/FP16 `N=2048` path.
- Supports the prepared packed-QKV TP8 route with local `N=1280`.
- Preserves fail-closed dispatch, reusable prepared launchers, and
fresh-output semantics.

Exact candidate:

- Commit: `3e764f6f3d93dfb4c2b279109f7a7296ad492361`
- Tree: `b08941f224dbba153bc07f8a11a9f630c643d113`
- Wheel: `flashinfer_python-0.6.18-py3-none-any.whl`
- Wheel SHA256:
`c6a2b5d6a8d65929c2b1df722ad81da2803a3c1e41fd1d48c8d06e93d75db13b`
- Backend source SHA256:
`f5a9b0db76fd0dbf9708731a91d7e5dc651fe2c1be236d1583aabd4653dc7a3c`
- Generated CUDA SHA256:
`6ba37efcba102135f0155ef5e162143ad71bc27e52699c9aae05b9d9ace99433`

## Validation method

The reportable TP8 GPU runs used one server with 8x NVIDIA B300 SXM6 AC
GPUs (SM103, CUDA 13.0), NCCL world size 8, full peer access, and remote
transport disabled. Timing used CUPTI activity tracing with cold-L2
flushing, a fresh eight-rank process per shape, distributed
candidate/baseline/baseline/candidate interleaving, 100 ms warmup, 1000
ms measured per arm, and the maximum participating-rank median as the
collective latency.

## TP8 route performance

The exact pre-export source kernel passed 10/10 correctness rows on all
eight ranks. All 7/7 timed BF16 `N=2048` rows were strictly faster than
the legacy public TP8 route under the identical schedule.

| BF16 `M` | New route (ms) | Legacy route (ms) | Speedup |
| ---: | ---: | ---: | ---: |
| 65,536 | 25.529275 | 31.134333 | 1.219554x |
| 32,768 | 12.969359 | 16.053747 | 1.237821x |
| 16,384 | 6.168790 | 8.215163 | 1.331730x |
| 8,192 | 3.198872 | 4.815536 | 1.505385x |
| 4,096 | 1.439967 | 2.576280 | 1.789124x |
| 2,048 | 0.866409 | 1.025912 | 1.184097x |
| 1,024 | 0.721816 | 1.010102 | 1.399390x |

Geometric-mean speedup is **1.368129x**, with range
**1.184097-1.789124x**. The measured benchmark runtime was **530.052 s**
and physical turnaround was **1133.017 s**.

## Export fidelity and public-API no-regression gate

The exact wheel was installed into an isolated target and selected
through the explicit public backend. All 9/9 exported-versus-source
comparison rows passed correctness on all eight ranks. All 7/7 timed
rows met the strict no-regression floor; the exported path was slightly
faster at every measured shape.

| BF16 `M` | Exported/public (ms) | Pre-export source (ms) |
Source/export ratio |
| ---: | ---: | ---: | ---: |
| 65,536 | 25.620375 | 25.698412 | 1.003046x |
| 32,768 | 12.942687 | 12.999199 | 1.004366x |
| 16,384 | 6.106822 | 6.144005 | 1.006089x |
| 8,192 | 3.156719 | 3.188720 | 1.010137x |
| 4,096 | 1.399640 | 1.474970 | 1.053820x |
| 2,048 | 0.724200 | 0.760216 | 1.049732x |
| 1,024 | 0.668230 | 0.704822 | 1.054760x |

The geometric-mean source/export ratio is **1.025729x**, with range
**1.003046-1.054760x**. The CUPTI measurement window was **519.799 s**
and physical turnaround was **524.616 s**. The sealed comparison
contains 112 raw CUPTI files (8 ranks x 2 arms x 7 timed shapes), with
no timing fallback.

## Promotion and safety gates

Completed on the exact candidate:

- Full pre-commit suite and 65 focused host tests.
- Wheel build and installed-wheel source/hash isolation.
- TP8 direct correctness: 10/10 rows on all eight ranks.
- TP8 installed-wheel packed-QKV correctness: BF16 and FP16 `M=512,
K=8192, N=1280`, max absolute error 0 on all eight ranks, fresh output
storage, and first-output preservation.
- Fresh JIT for SM100a and SM103a.
- Manifest-driven SM100a and SM103a SASS, with all 12 expected
TP2/TP4/TP8 symbols on each architecture.
- Eight-rank synccheck and memcheck, both with `ERROR SUMMARY: 0 errors`
on every rank. Sanitizer physical turnaround was **3013.153 s**.
- Fresh exact-head GitHub CI: 14/14 jobs succeeded in [PR Test run
33288915646](https://github.com/flashinfer-ai/flashinfer/actions/runs/33288915646).

Terminal receipt SHA256 values:

- TP8 source-vs-legacy comparison:
`2ef6376131b83db564a774a638259d542ca1459c1976b08af0824a0edf30ac17`
- TP8 export-vs-source comparison:
`21bf63d68ea2f933804d4831b54710ced51662d4b92122cc90ebf61a0a54734f`
- Eight-rank sanitizer:
`7ea44d96370fb1c32ba63f6c46aa0fb7f38600ec85520919f12c2fd3d20ee69c`
- Dual-architecture SASS:
`7455997b636b0493778057fe3901e9e581bb746c17986206f7c4b8606eea5865`

Strict downstream TP8 real-model validation is tracked separately and is
not represented by the existing TP4 result. It remains pending until a
compatible single-host eight-device GB300 test target is available.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added Blackwell all-gather matrix multiplication support for
eight-device configurations.
- Added world-size-specific tensor dimensions for standard and
packed-QKV workloads.
- Expanded prepared packed-QKV execution with additional peer routing
and repeated-launch support.
  - Added configurable readiness tracking for launches.

- **Bug Fixes**
- Improved synchronization and signal handling for more reliable
multi-device execution.

- **Tests**
- Added coverage for eight-device BF16 execution, packed-QKV workloads,
repeated launches, buffer reuse, and numerical correctness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [b418184](https://github.com/flashinfer-ai/flashinfer/commit/b4181843891fd33decb091520c1e6b8d01179786)

- **作者**: eigen
- **时间**: 2026-09-03T12:38:01Z
- **提交信息**: feat(cake_warp_decode): add SM103 NVFP4 warp-decode backend (#4855)

## Description

Adds an opt-in SM103 NVFP4 warp-decode backend for two calibrated
fused-MoE
geometries:

- H=2048, I=512, E=512, top-k=10, T=1–32
- H=2048, I=1536, E=60, top-k=4, T=1–32

The change includes generated CUDA kernels and their manifest, JIT and
AOT
registration, public runner and layer integration, caller-owned output
and
workspace handling, current-stream execution, and CUDA Graph
capture/replay
support. The backend requires exact compute capability 10.3 and is not
included
in the default backend selection.

## Dispatch

The generated bundle contains 15 specialized kernels.

For E512 / I512 / top-k 10:

- T=1: static direct path
- T=2–22: persistent direct path
- T=23–32: persistent GPU-packed path

For E60 / I1536 / top-k 4:

- T=1–7: persistent direct path
- T=8–10: persistent direct padded-SFB path
- T=11: GPU-packed scan-1 path
- T=12–16: GPU-packed scan-2 path
- T=17–32: persistent GPU-packed path

The E512 T23 boundary was confirmed on one discovery route seed and two
held-out route seeds: packed execution beats direct execution by
1.0375x,
1.0196x, and 1.0239x. The production shuffled NVFP4 ABI, MajorK weight
layout,
R128c4 scales, and fail-closed shape contract are unchanged.

## Validation

Hardware: NVIDIA B300 SXM6 AC, SM103, driver 580.126.09, x86_64.

All output comparisons use the independent row-wise physical FP4 oracle
with
`atol=1.0` and `rtol=0.1`.

- All 64 supported rows across both geometries and T=1–32 pass before
and
  after timing and remain bitwise equal across arms.
- T22 selects the E512 direct route and T23 selects the GPU-packed
route.
- Selector-boundary CUDA Graph capture, replay, and mutation pass.
- Same-address receipt generations, asynchronous workspace retirement,
public
  layer capture/replay, and cross-stream preparation/execution pass.
- Stale, released, repeated-release, non-positive, and invalid receipts
are
  rejected.
- 35 targeted public tests pass on the final public revision.
- Generated CUDA and the C++ manifest are byte-identical to the
validated
  production bundle.
- Representative Compute Sanitizer synccheck and memcheck have zero
reported
errors. The T23 crossover update changes selector metadata only and does
not
  change kernel memory access, synchronization, or cross-warp dataflow.

## Performance methodology

The comparison ran at public commit
`782437fc368284de17ac2e7f04a04c3859f8dd44` in
`nvcr.io/nvidia/pytorch:26.07-py3`, using PyTorch
2.13.0a0+9186a08b2c.nv26.07, FlashInfer 0.6.16, CUDA CUPTI 13.3.75, and
CUPTI Python 13.0.1.

Each geometry reused one extent-32 physical checkpoint; the E512 and E60
sweeps used seeds 28301 and 28201 respectively. The official comparison
consumed unpacked precomputed routes with `Renormalize` and
`tune_max_num_tokens=T`. Both arms replayed complete CUDA Graphs.

Cold-L2 CUPTI timing used three counterbalanced paired groups, 50 ms
warmup
and 500 ms reportable time per arm and group, and the pooled unrounded
reportable-sample median. Quantization, compilation, workspace
preparation,
and Graph capture were outside the measured region. Delta is exported
minus
official, so a negative value is faster. Lower latency is better.

## Complete performance results

All 64 exported rows beat official TRT-LLM. E512 geometric-mean speedup
is
**1.0592x** (range **1.0198x–1.1261x**); E60 is **1.1757x**
(**1.1487x–1.3102x**); the combined equal-row geometric mean is
**1.1160x**.
Exported replay has three GPU activities before the packing boundary and
four
afterward; official replay has four throughout.

### E512 / I512 / top-k 10 (seed 28301)

| T | Exported (us) | Official (us) | Delta (us) | Speedup | Improvement
| Activities |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 15.616 | 17.184 | -1.568 | 1.1004x | +9.12% | 3/4 |
| 2 | 19.040 | 21.440 | -2.400 | 1.1261x | +11.19% | 3/4 |
| 3 | 22.817 | 25.344 | -2.527 | 1.1108x | +9.97% | 3/4 |
| 4 | 27.105 | 28.576 | -1.471 | 1.0543x | +5.15% | 3/4 |
| 5 | 30.176 | 32.481 | -2.305 | 1.0764x | +7.10% | 3/4 |
| 6 | 33.824 | 35.936 | -2.112 | 1.0624x | +5.88% | 3/4 |
| 7 | 36.161 | 38.400 | -2.239 | 1.0619x | +5.83% | 3/4 |
| 8 | 38.752 | 41.088 | -2.336 | 1.0603x | +5.69% | 3/4 |
| 9 | 41.664 | 44.000 | -2.336 | 1.0561x | +5.31% | 3/4 |
| 10 | 44.768 | 47.201 | -2.433 | 1.0543x | +5.15% | 3/4 |
| 11 | 46.944 | 48.992 | -2.048 | 1.0436x | +4.18% | 3/4 |
| 12 | 49.472 | 50.816 | -1.344 | 1.0272x | +2.64% | 3/4 |
| 13 | 51.712 | 53.121 | -1.409 | 1.0272x | +2.65% | 3/4 |
| 14 | 54.337 | 55.872 | -1.535 | 1.0282x | +2.75% | 3/4 |
| 15 | 57.312 | 58.721 | -1.409 | 1.0246x | +2.40% | 3/4 |
| 16 | 59.873 | 61.057 | -1.184 | 1.0198x | +1.94% | 3/4 |
| 17 | 61.953 | 65.792 | -3.839 | 1.0620x | +5.84% | 3/4 |
| 18 | 64.385 | 68.737 | -4.352 | 1.0676x | +6.33% | 3/4 |
| 19 | 66.465 | 70.817 | -4.352 | 1.0655x | +6.15% | 3/4 |
| 20 | 68.641 | 72.704 | -4.063 | 1.0592x | +5.59% | 3/4 |
| 21 | 70.817 | 74.305 | -3.488 | 1.0493x | +4.69% | 3/4 |
| 22 | 72.961 | 75.681 | -2.720 | 1.0373x | +3.59% | 3/4 |
| 23 | 72.897 | 77.536 | -4.639 | 1.0636x | +5.98% | 4/4 |
| 24 | 74.337 | 79.233 | -4.896 | 1.0659x | +6.18% | 4/4 |
| 25 | 75.873 | 80.960 | -5.087 | 1.0670x | +6.28% | 4/4 |
| 26 | 76.929 | 82.849 | -5.920 | 1.0770x | +7.15% | 4/4 |
| 27 | 78.688 | 83.680 | -4.992 | 1.0634x | +5.97% | 4/4 |
| 28 | 79.233 | 84.449 | -5.216 | 1.0658x | +6.18% | 4/4 |
| 29 | 81.633 | 86.913 | -5.280 | 1.0647x | +6.08% | 4/4 |
| 30 | 82.977 | 87.585 | -4.608 | 1.0555x | +5.26% | 4/4 |
| 31 | 84.033 | 89.345 | -5.312 | 1.0632x | +5.95% | 4/4 |
| 32 | 85.281 | 88.832 | -3.551 | 1.0416x | +4.00% | 4/4 |

### E60 / I1536 / top-k 4 (seed 28201)

| T | Exported (us) | Official (us) | Delta (us) | Speedup | Improvement
| Activities |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 13.632 | 16.000 | -2.368 | 1.1737x | +14.80% | 3/4 |
| 2 | 16.673 | 19.552 | -2.879 | 1.1727x | +14.72% | 3/4 |
| 3 | 22.176 | 29.056 | -6.880 | 1.3102x | +23.68% | 3/4 |
| 4 | 25.729 | 33.536 | -7.807 | 1.3034x | +23.28% | 3/4 |
| 5 | 29.952 | 36.737 | -6.785 | 1.2265x | +18.47% | 3/4 |
| 6 | 32.864 | 39.713 | -6.849 | 1.2084x | +17.25% | 3/4 |
| 7 | 35.168 | 41.793 | -6.625 | 1.1884x | +15.85% | 3/4 |
| 8 | 37.953 | 46.273 | -8.320 | 1.2192x | +17.98% | 3/4 |
| 9 | 42.273 | 50.528 | -8.255 | 1.1953x | +16.34% | 3/4 |
| 10 | 46.113 | 54.465 | -8.352 | 1.1811x | +15.33% | 3/4 |
| 11 | 48.065 | 56.224 | -8.159 | 1.1697x | +14.51% | 4/4 |
| 12 | 49.088 | 57.281 | -8.193 | 1.1669x | +14.30% | 4/4 |
| 13 | 52.737 | 61.313 | -8.576 | 1.1626x | +13.99% | 4/4 |
| 14 | 55.584 | 64.641 | -9.057 | 1.1629x | +14.01% | 4/4 |
| 15 | 57.665 | 66.240 | -8.575 | 1.1487x | +12.95% | 4/4 |
| 16 | 57.089 | 66.752 | -9.663 | 1.1693x | +14.48% | 4/4 |
| 17 | 57.537 | 66.337 | -8.800 | 1.1529x | +13.27% | 4/4 |
| 18 | 57.761 | 66.433 | -8.672 | 1.1501x | +13.05% | 4/4 |
| 19 | 58.465 | 67.520 | -9.055 | 1.1549x | +13.41% | 4/4 |
| 20 | 60.353 | 69.568 | -9.215 | 1.1527x | +13.25% | 4/4 |
| 21 | 61.185 | 70.465 | -9.280 | 1.1517x | +13.17% | 4/4 |
| 22 | 61.953 | 71.617 | -9.664 | 1.1560x | +13.49% | 4/4 |
| 23 | 62.849 | 72.737 | -9.888 | 1.1573x | +13.59% | 4/4 |
| 24 | 63.041 | 72.641 | -9.600 | 1.1523x | +13.22% | 4/4 |
| 25 | 62.945 | 72.929 | -9.984 | 1.1586x | +13.69% | 4/4 |
| 26 | 64.001 | 73.633 | -9.632 | 1.1505x | +13.08% | 4/4 |
| 27 | 64.129 | 73.761 | -9.632 | 1.1502x | +13.06% | 4/4 |
| 28 | 64.705 | 75.073 | -10.368 | 1.1602x | +13.81% | 4/4 |
| 29 | 64.801 | 74.689 | -9.888 | 1.1526x | +13.24% | 4/4 |
| 30 | 66.497 | 76.993 | -10.496 | 1.1578x | +13.63% | 4/4 |
| 31 | 66.177 | 77.153 | -10.976 | 1.1659x | +14.23% | 4/4 |
| 32 | 66.304 | 76.961 | -10.657 | 1.1607x | +13.85% | 4/4 |

## Generated evidence

- Raw CUDA SHA-256:
  `844e7eb08a7c2250dce5e2eea93a9c726be9be114365fbb5f4a50862b3f62703`
- Combined CUDA SHA-256:
  `9985afbe38c240b10a0e60280dabd6bc45483db3a28e0ae94fd48bc9428a2daf`
- C++ manifest SHA-256:
  `a57df0b76fb80bddb648481493ae7746a87f6b9c0a2f5c2c0617d2986bcb506c`
- Dispatch manifest SHA-256:
  `b042f71428c33322df806e79b4e940229797beb3441d2bd172f9e1bbe3cde031`

The two geometry benchmark phases took 3084 s and 3287 s; the complete
scripts
took 3316 s and 3515 s. They ran concurrently, with 3577.1 s managed
end-to-end turnaround for the complete matrix.

## Related issues

None.

## Pull request checklist

- [x] Tests have been added or updated as needed.
- [x] Generated CUDA and manifest pass exact export checks.
- [x] Relevant CPU/JIT and package-content checks pass.
- [x] B300 correctness and CUDA Graph checks pass.
- [x] Complete T=1–32 cold-L2 CUPTI results are included for both
geometries.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added the Cake NVFP4 warp-decode MoE backend for supported SM103 GPUs.
- Added public configuration and runner APIs with workspace management
and CUDA Graph-compatible execution.
  - Added cuTile BF16 and NVFP4 backend configurations.
  - Expanded unified MoE backend dispatch and autotuning support.
  - Added JIT and AOT support for Cake warp-decode modules.

- **Documentation**
- Documented supported configurations, runtime requirements, workspace
handling, validation, and benchmarking.

- **Tests**
- Added coverage for validation, stream and graph behavior, caching,
error handling, and backend registration.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [fbad18c](https://github.com/flashinfer-ai/flashinfer/commit/fbad18cb42d201c6a5943919a17ed79e86f6acec)

- **作者**: Peterson Guo
- **时间**: 2026-09-03T09:34:06Z
- **提交信息**: Add CuteDSL Low Latency GEMM tactic to mm_fp4, mm_fp8, mm_mxfp8, tgv_gemm_sm100 backends (SM100/SM103) (#4685)

## 📌 Description

Adds the CuTe-DSL low-latency block-scaled GEMM kernel and integrates it
behind existing FlashInfer GEMM APIs.

- Adds the low-latency Blackwell block-scaled GEMM kernel with FP4, FP8,
and mixed FP8 × FP4 support.
- Exposes the kernel as the "cutedsl_low_latency" backend for mm_fp4,
mm_mxfp8, and mm_fp8.
- Extends tgv_gemm_sm100 with automatic dispatch between dense BF16/FP16
GEMM and block-scaled FP4/FP8 GEMM.
- Supports optional bias and an FP32 output scale applied in accumulator
precision before bias and output conversion.
- Supports scale and bias correctly for both regular and split-K
execution.
- Generates all supported CTA-K, pipeline-stage, and split-K tactics,
filtered by layout, TMEM, and SMEM constraints.
- Adds static FP8 support using unit E8M0 block scales, allowing the
existing alpha argument to be applied by the block-scaled kernel.
- Preserves existing backend heuristics and adds "cutedsl_low_latency"
as the final eligible automatic-dispatch candidate.
  - Keeps existing dense TGV behavior and weight preparation unchanged.
- Documents backend layout, dtype, architecture, shape, and alignment
requirements through the public API docstrings.
- Adds correctness coverage for every generated tactic, GPT-OSS-120B and
DeepSeek-V3 shapes, edge cases, alpha, bias, PDL, and mixed operand
formats.

The low-latency backend requires SM100 or SM103 and currently supports
public GEMM shapes with M <= 8. NVFP4 requires K divisible by 64; MXFP4,
MXFP8, and static FP8 require K divisible by 128.

Overall diff versus main: approximately 3,470 net lines added, primarily
from the new kernel and its correctness coverage.

  ## 🔍 Related Issues

  N/A

  ## 🚀 Pull Request Checklist

  ✅ Pre-commit Checks

  - Pre-commit checks were run against the changed files.
- Mypy, Ruff checks, Ruff formatting, Python compilation, and repository
hygiene checks pass.

  ## 🧪 Tests

  - Low-latency kernel tactic correctness: 17 passed.
  - Public FP4 and MXFP8 low-latency dispatch coverage: 19 passed.
- FP8 backend coverage: 54 passed, 6 expected skips for unsupported
shapes.
  - Quantized tgv_gemm_sm100 coverage: 4 passed.
  - Every generated tactic is checked with alpha and bias.
- Coverage includes NVFP4, MXFP4, MXFP8, FP8 × FP8, mixed FP8 × FP4,
split-K, PDL, GPT-OSS-120B shapes, DeepSeek-V3 shapes, and edge-case
dimensions.

## Reviewer Notes
Closes #3141 as this builds on top.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added low-latency block-scaled GEMM support for FP8, MXFP8, and FP4
workloads on supported Blackwell GPUs.
- Added CuTe-DSL access, automatic tactic tuning, optional bias and
output scaling, and split-K execution.
- Added block-scaled input support to TGV GEMM, including scaling
factors and bias.
  - Added support for model-shaped workloads.

- **Bug Fixes**
- Improved validation for unsupported layouts and misaligned matrix
dimensions.

- **Tests**
- Expanded coverage across formats, architectures, backends, workloads,
edge cases, and correctness checks.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Sinestro38 <pavanjayasinha@gmail.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4317
- **最后更新**: 2026-09-03T22:00:49Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: SYLAR

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交为**功能新增**，核心是添加对 NVIDIA SM103a 架构（即 Blackwell Ultra 系列 GPU）的原生 VSA（Video Super-Resolution Accelerator，视频超分加速器）支持。

**2. 关键变更点与项目方向**  
FastVideo 是一个面向视频生成与处理的高性能框架，强调对最新硬件架构的快速适配。SM103a 是 NVIDIA 新一代数据中心 GPU，原生支持意味着框架无需依赖通用 CUDA 回退路径，可直接调用硬件级视频超分指令，显著提升推理效率。这与项目“极致性能优化”的定位高度一致。

**3. 对项目的影响与潜在意义**  
- **性能跃升**：原生 VSA 支持可让视频超分任务在 SM103a 上获得数倍于通用路径的吞吐量，降低延迟。  
- **生态前瞻性**：在 Blackwell Ultra 尚未大规模普及前完成适配，使 FastVideo 成为首批支持该架构的开源视频工具，吸引早期高端用户。  
- **硬件差异化**：为后续针对 SM103a 的专属优化（如算子融合、显存调度）奠定基础，形成竞争壁垒。

**4. 值得关注的技术点**  
- **VSA 硬件单元**：SM103a 集成的专用视频加速模块，需通过特定指令集或驱动 API 访问，提交中必然包含底层封装与调度逻辑。  
- **条件编译与回退**：需确保在非 SM103a 设备上自动降级至通用实现，避免破坏现有兼容性，这通常涉及架构检测与代码分支管理。  
- **性能验证**：新增功能大概率附带基准测试或示例脚本，用于量化原生路径与回退路径的差异。

**5. 对项目发展的影响**  
结合 README 中“快速上手”与“Cookbook”的定位，此次提交直接强化了 FastVideo 在**高端视频生成/处理工作流**中的竞争力。它使依赖最新 GPU 的研究团队或企业用户能即刻获得硬件红利，无需等待第三方适配。同时，该功能可能吸引更多开发者围绕 SM103a 贡献专属优化，形成正向社区循环。长远看，这标志着项目从“通用框架”向“硬件感知的深度优化平台”演进，有助于在 AI 视频工具链中巩固领先地位。

## 详细提交记录

### [7bb76b5](https://github.com/hao-ai-lab/FastVideo/commit/7bb76b5ec99807a66aa3047b901f15019abe0f00)

- **作者**: SYLAR
- **时间**: 2026-09-03T22:00:28Z
- **提交信息**: [feat] Add native SM103a VSA support (#1812)

Signed-off-by: lishunyang12 <lishunyang12@163.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34440
- **最后更新**: 2026-09-03T23:51:24Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: dg845, YiYi Xu, Zhiqi Zhang

## AI分析总结

### 提交分析总结

#### 1. 主要更新类型
本次提交包含 **Bug修复** 和 **功能优化** 两类核心变更，辅以文档更新。其中两项为功能性调整（默认参数变更、调度器修复），一项为针对特定模型的设备管理Bug修复。

#### 2. 关键变更点与项目方向关系
- **`save_pretrained` 默认行为变更**：将 `overwrite_modular_index` 默认值改为 `True`，简化模块化管线的保存流程，减少用户手动覆盖索引的步骤。这与项目推动的 **模块化管线（ModularPipeline）** 设计理念一致，旨在提升易用性和开发效率。
- **分布式训练调度器修复**：修正 `train_text_to_image_decoder.py` 中学习率调度器在分布式环境下的计算逻辑，确保传入 `num_train_epochs` 时调度器正确工作。这直接支撑了项目在 **大规模分布式训练** 场景下的可靠性，符合社区对稳定训练流程的需求。
- **PriorTransformer 组卸载Bug修复**：解决 `PriorTransformer` 在组卸载（group offloading）时参数设备不一致的问题，并顺带修复了 Kandinsky 系列管线的同类故障。这强化了 **Stable unCLIP 和 Kandinsky 管线** 在显存受限环境下的可用性，是项目对 **内存优化与多管线兼容性** 的持续投入。

#### 3. 项目影响与潜在意义
- **提升模块化管线的用户友好度**：默认覆盖索引降低了新手使用门槛，可能吸引更多开发者尝试模块化设计，加速其生态成熟。
- **增强分布式训练稳定性**：修复调度器问题可减少多卡训练中的隐性错误，提升大规模实验的可复现性，对研究社区有直接价值。
- **扩大模型部署场景**：组卸载修复使高端模型（如 unCLIP、Kandinsky）能在更低显存设备上运行，拓宽了项目的硬件适用范围，有利于社区参与和实际应用落地。

#### 4. 值得关注的技术点
- **模块化索引的默认策略**：`overwrite_modular_index=True` 意味着保存时自动覆盖索引，需注意在版本控制或协作场景下可能引发的文件冲突，未来或需引入更细粒度的控制选项。
- **分布式调度器与epoch的交互**：修复涉及 `num_train_epochs` 在分布式环境下的传递逻辑，提示开发者需关注训练参数在不同并行策略下的语义一致性。
- **模型级参数与子模块卸载的差异**：`PriorTransformer` 将 `clip_mean`/`clip_std` 作为顶层参数而非子模块，导致组卸载钩子无法覆盖后处理阶段。这一案例揭示了 **模型参数组织方式对内存管理机制的影响**，为后续设计提供参考。

#### 5. 对项目发展的影响
结合README中强调的 **多模态生成模型库** 定位，这些提交体现了项目在三个维度的演进：
- **易用性**：模块化管线的默认行为优化，降低了自定义管线的复杂度，有助于吸引更多非专业用户。
- **健壮性**：分布式训练和内存卸载的修复，巩固了项目作为 **生产级工具** 的可靠性，支撑从研究到部署的平滑过渡。
- **生态扩展**：对 Kandinsky 等多样管线的兼容性修复，表明项目正积极维护多模型家族，避免因基础设施缺陷阻碍新模型集成。

整体而言，本次提交虽规模不大，但精准解决了用户实际使用中的痛点，体现了项目在 **细节打磨** 与 **长期可维护性** 上的投入，为后续功能迭代奠定了更稳定的基础。

## 详细提交记录

### [7643c48](https://github.com/huggingface/diffusers/commit/7643c4826609c47755e3da0e5b768e8070468f49)

- **作者**: YiYi Xu
- **时间**: 2026-09-03T23:50:58Z
- **提交信息**: ModularPipeline.save_pretrained: change the default  `overwrite_modular_index` to be True (#14659)

* flipt default for save_pretrained overwrite_modular_index to be True

* update doc

* make style

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* Update docs/source/en/modular_diffusers/modular_pipeline.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/modular_diffusers/modular_pipeline.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/modular_diffusers/modular_pipeline.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/modular_diffusers/modular_pipeline.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* address review comments

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

### [09e4f5e](https://github.com/huggingface/diffusers/commit/09e4f5e4950c4eb156c8b9e5486176c431d53be5)

- **作者**: Zhiqi Zhang
- **时间**: 2026-09-03T08:27:19Z
- **提交信息**: [train_text_to_image_decoder.py] Fix the LR scheduler when num_train_epochs is passed in a distributed training env (#14542)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [937bf6e](https://github.com/huggingface/diffusers/commit/937bf6e046def4b1364728ba739e70c5b4b01ff0)

- **作者**: dg845
- **时间**: 2026-09-03T08:02:32Z
- **提交信息**: Fix PriorTransformer Group Offloading Bug (#14695)

[Stable unCLIP] Fix Stable unCLIP group offloading tests

`PriorTransformer` holds `clip_mean` / `clip_std` as parameters of the model
itself rather than of a submodule, so group offloading gathers them into the
"unmatched group" whose hook wraps the top-level `forward`. They are therefore
onloaded only for the duration of `forward`, while `post_process_latents` runs
after the denoising loop and saw them back on the offload device:

    RuntimeError: Expected all tensors to be on the same device, but found at
    least two devices, cuda:0 and cpu!

Move them to the latents' device explicitly.

This also fixes the same failure in the three Kandinsky prior pipelines, whose
strict xfail markers now XPASS, so remove them along with the overrides that
existed only to carry them. Their `PIPELINE_GROUP_OFFLOAD_XFAIL_REASON` was a
misdiagnosis: the model-level parameters are onloaded for `forward`, and the
pipeline-level test was failing on `post_process_latents` like the others.

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-08-31T08:28:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13047
- **最后更新**: 2026-09-03T20:41:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 34074
- **最后更新**: 2026-09-03T23:23:05Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 27
- **主要提交者**: Baizhou Zhang, Jimmy Shong, Duyi-Wang

## AI分析总结

# SGLang 仓库提交分析报告

## 一、主要更新类型

本次提交涵盖**功能新增**（如UNO原生服务、IFM K2 Horizon支持、统一SWA内存推测解码）、**性能优化**（Kimi-K3 MoE优化、缓存管理改进）、**Bug修复**（FP4索引越界、DSv4压缩路径问题）、**CI/CD改进**（Lark通知、NPU/AMD测试修复）、**文档更新**（NPU支持模型刷新、AMD cookbook）及**代码重构**（量化重构、统一缓存集成）六大类。

## 二、关键变更点与项目方向

1. **统一缓存架构持续推进**：多个提交围绕Unified Cache/HiCache展开，包括外部链接器模式端到端集成、L3存储预取生命周期指标、缓冲模式锚定锁存预取等，体现项目向**分层统一缓存管理**演进的核心方向。

2. **多硬件平台适配深化**：AMD MI355X、NPU、SM120等平台的支持与修复密集出现，配合CI测试矩阵扩展，显示项目正从NVIDIA独占向**多厂商硬件生态**扩展。

3. **模型服务能力扩展**：新增UNO、IFM K2 Horizon、MiniMax-H3等模型的原生支持，以及Kimi-K3的MoE优化，反映项目持续跟进前沿模型架构。

4. **推测解码与内存管理创新**：统一SWA内存推测解码、解码上下文并行等特性，指向**更高效的内存复用与计算并行**方向。

## 三、项目影响与潜在意义

- **缓存系统精细化**：通过mmap+cudaHostRegister固定主机缓存大小、页面对齐要求等改进，提升缓存管理确定性，对长序列和高并发场景意义重大。
- **CI基础设施升级**：结构化Lark通知、CUDA CI状态监控、队列时间追踪，将提升开发协作效率与问题响应速度。
- **量化重构启动**：FP4 Marlin辅助代码去重是量化重构的第一步，预示后续将有系统性的量化框架优化。
- **测试稳定性增强**：允许top-k截断并列、修复UT因重构失败等问题，提高测试套件可靠性。

## 四、值得关注的技术点

1. **cudaHostRegister精确固定主机缓存**：通过mmap+注册机制实现确定性缓存大小，是缓存管理的重要底层优化。
2. **块级缩放swizzling设备放置修复**：涉及底层内存布局与设备间数据分布的精细调优。
3. **快速前缀匹配能力的前向传递**：可能显著加速多轮对话与共享前缀场景。
4. **可组合评分与资格策略**：路由器的策略抽象设计，增强系统灵活性与可扩展性。
5. **Kimi-K3跳过思考修复改为opt-in**：以流式覆盖方式处理非空内容，兼顾功能与兼容性。

## 五、对项目发展的整体影响

SGLang正从单一GPU推理引擎向**多硬件、多模型、统一内存管理**的综合服务平台演进。缓存系统的层级化与精细化、路由策略的可组合化、量化框架的重构，共同构建更健壮的架构基础。对AMD/NPU等平台的持续投入，配合CI基础设施完善，表明项目正积极拓展企业级市场。推测解码、上下文并行等高级特性与前沿模型（Kimi-K3、DeepSeek-V4）的快速适配，巩固其在**高性能推理框架**领域的领先地位。整体来看，项目处于架构升级与生态扩展并行的关键阶段，技术深度与广度同步提升。

## 详细提交记录

### [66d6043](https://github.com/sgl-project/sglang/commit/66d60433c17b98867ea8b8a70b88d1deeb05b6ed)

- **作者**: Yueming Yuan
- **时间**: 2026-09-03T23:20:59Z
- **提交信息**: state_capturer: pin the exact host-cache size via mmap + cudaHostRegister (#37285)

### [8b05013](https://github.com/sgl-project/sglang/commit/8b0501399ecc5945c80fa1388c5c13c6dd48008b)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-03T23:18:56Z
- **提交信息**: [CI] Improve Lark CI cards: structured layout, PDT timestamps, slow-only queue digest (#37884)

### [b444963](https://github.com/sgl-project/sglang/commit/b44496389c4487488b1fe6694ea83b3faaeeecb2)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-03T23:08:50Z
- **提交信息**: [HiCache] Count hit allocations and in-flight backups in the buffer pipeline idle check (#37883)

### [a480f38](https://github.com/sgl-project/sglang/commit/a480f388b2acbeead991936213b8dfb82c053d66)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-03T23:00:04Z
- **提交信息**: [HiCache] L3 storage prefetch lifecycle metrics and cross-tier attribution fixes (#37503)

### [0610a65](https://github.com/sgl-project/sglang/commit/0610a6539d4da26100fd471ba125a85c26b98807)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-03T22:46:33Z
- **提交信息**: [CI] Add Lark notifications for CUDA CI status, runner health, and queue time (#37881)

### [4dc9cda](https://github.com/sgl-project/sglang/commit/4dc9cda5f977e7cf86e980f9cb2f8f456b584fbb)

- **作者**: Yonghao Zhuang
- **时间**: 2026-09-03T22:42:21Z
- **提交信息**: [PD] Gate deferred decode KV release on backend capability (#37454)

Co-authored-by: yhzhuang <yhzhuang@fb.com>

### [fd70325](https://github.com/sgl-project/sglang/commit/fd70325c108c17b635e7caaa57fc7ab4e6e63ad9)

- **作者**: Baizhou Zhang
- **时间**: 2026-09-03T21:26:25Z
- **提交信息**: [CI] Add dspark + dsv4 e2e test (#37665)

### [4372b8e](https://github.com/sgl-project/sglang/commit/4372b8efa7966d1813f56c481abffb2ba673a214)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-03T21:22:31Z
- **提交信息**: [1/N] Quantization Refactor: remove dead code and dedup the FP4 marlin helpers (#37552)

### [0e5414f](https://github.com/sgl-project/sglang/commit/0e5414fd2f109a02151a87b437afe6ba82d49839)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-03T21:13:26Z
- **提交信息**: [Test] Allow top-k cutoff ties in `test_sampling_mask_matches_topk_logprobs` (#37873)

### [05dbe64](https://github.com/sgl-project/sglang/commit/05dbe64dffab51af8f4b21063cd6a616b16cf6b5)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-03T20:56:12Z
- **提交信息**: Fix buffer-mode idle tracking and VLM memory sizing (#37567)

### [2a980cb](https://github.com/sgl-project/sglang/commit/2a980cbf10db36c6052042cc3f92b4a80c4047b6)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-03T20:28:33Z
- **提交信息**: [mem_cache] Require page-aligned starts in `free_segment` and drop the boundary trim (#37729)

### [3ffacf9](https://github.com/sgl-project/sglang/commit/3ffacf949b9275abdb1fcd3ad2c4871f95adf31c)

- **作者**: Martin Hickey
- **时间**: 2026-09-03T20:17:33Z
- **提交信息**: [Docs] [BugFix] Sync --tool-call-parser and --reasoning-parser lists with the code (#37788)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [d0c95f6](https://github.com/sgl-project/sglang/commit/d0c95f6c911addde7d21a62df5f8ad06709d9ae8)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-03T19:08:22Z
- **提交信息**: [HiCache] buffer mode: anchor-lock staged prefetches by default (#37464)

### [68978f8](https://github.com/sgl-project/sglang/commit/68978f8d52547f83af76b62e5020e4dbfe0edf13)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-03T19:08:17Z
- **提交信息**: [Scheduler] Count the parked chunked-prefill request in the busy mem check (#37502)

### [2da5802](https://github.com/sgl-project/sglang/commit/2da5802bfaf499aef0742a59a8d2ddbec2191c21)

- **作者**: Jimmy Shong
- **时间**: 2026-09-03T18:43:01Z
- **提交信息**: [Cookbook] DeepSeek-V4 DGX Spark: v2 image + Flash Official NVFP4 and Flash Vision FP4 cells (#37737)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [abed680](https://github.com/sgl-project/sglang/commit/abed680320502c8db04cc1560b907e6ff0f5ee12)

- **作者**: Zhangheng
- **时间**: 2026-09-03T18:02:58Z
- **提交信息**: [Unified Cache][5/N]: Integrate external linker mode end to end (#37381)

Co-authored-by: 晟海 <huangtingwei.htw@antgroup.com>

### [619ab2b](https://github.com/sgl-project/sglang/commit/619ab2bccecf6d075c0cf198a62aec407ff8f187)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-03T17:47:04Z
- **提交信息**: Fix block-scale swizzling device placement (#37849)

### [23ab10a](https://github.com/sgl-project/sglang/commit/23ab10a63e5e8008c2ab8c7165f7486cdd9be25e)

- **作者**: Yonghao Zhuang
- **时间**: 2026-09-03T17:44:57Z
- **提交信息**: Support speculative decoding with unified SWA memory (#36403)

Co-authored-by: yhzhuang <yhzhuang@fb.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [33a22b1](https://github.com/sgl-project/sglang/commit/33a22b1b083a5e3ece8c425cdc80095d1d947189)

- **作者**: cctry
- **时间**: 2026-09-03T17:33:30Z
- **提交信息**: [Cache] Forward fast prefix matching capability (#37844)

### [54cadad](https://github.com/sgl-project/sglang/commit/54cadad151e55c7cfef357da77061812eb893b96)

- **作者**: Vincent Gao
- **时间**: 2026-09-03T16:01:41Z
- **提交信息**: [Router] Add composable scoring and eligibility policies (#37731)

Co-authored-by: inkcherry <mingzhi.liu@amd.com>

### [392841f](https://github.com/sgl-project/sglang/commit/392841f47cb7ef214601eeb528906a0abba02471)

- **作者**: Yash Akhauri
- **时间**: 2026-09-03T15:53:16Z
- **提交信息**: [Bugfix] Support K2 Horizon MoE without MoVA (#37825)

Co-authored-by: BBuf <1182563586@qq.com>

### [bf71035](https://github.com/sgl-project/sglang/commit/bf71035d39d57a5b39cf3f72ae0134eaa5fff305)

- **作者**: triple-mu
- **时间**: 2026-09-03T14:09:21Z
- **提交信息**: [diffusion] MiniMax-H3: tiered AdaLN plan cache (pinned-host tier + per-plan LRU) (#37266)

Co-authored-by: mickqian <mickqian@users.noreply.github.com>

### [4e37882](https://github.com/sgl-project/sglang/commit/4e37882a9374b9ed4cd15d30186ffeddfe7e988a)

- **作者**: Quanli Li
- **时间**: 2026-09-03T14:05:22Z
- **提交信息**: [Diffusion][minimax-h3] Add SM120 support for SubBlock sparse attention (#37332)

Co-authored-by: 全力 <liquanli.lql@antgroup.com>

### [3239bae](https://github.com/sgl-project/sglang/commit/3239baef255d09decc753674a16012d102c947da)

- **作者**: pllimax
- **时间**: 2026-09-03T13:57:14Z
- **提交信息**: [CI][NPU] Fix kimi_k2_6 16p in64k perf test and dsv4-flash testcases (#37760)

### [9cb38a3](https://github.com/sgl-project/sglang/commit/9cb38a3d5750fa9fd1232ecdedefe714948c8fe7)

- **作者**: dujifeng
- **时间**: 2026-09-03T13:54:11Z
- **提交信息**: [diffusion] feat: filter duplicate precision variants across custom loaders (#37616)

Co-authored-by: mickqian <mickqian@users.noreply.github.com>

### [f5bed25](https://github.com/sgl-project/sglang/commit/f5bed255c0d855a1ab98bd3a7df7297a33dca5e3)

- **作者**: Yihao Wang
- **时间**: 2026-09-03T12:13:33Z
- **提交信息**: [diffusion] feat: support key masks on USPAttention's replicated-prefix path (#36735)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [14444c6](https://github.com/sgl-project/sglang/commit/14444c6a04212b3e5b0c5a6d21090227129be245)

- **作者**: Yihao Wang
- **时间**: 2026-09-03T12:12:54Z
- **提交信息**: [diffusion] feat: add maybe_record_function profiler spans for request phases (#35922)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [2bb25dc](https://github.com/sgl-project/sglang/commit/2bb25dc18bc27321fb116bbefcaddaf13c1c1754)

- **作者**: Yash Akhauri
- **时间**: 2026-09-03T12:08:41Z
- **提交信息**: [Speculative Decoding] Add native UNO serving support (#37667)

Co-authored-by: drproduck <drproduck@MacBook-Air-2.local>
Co-authored-by: BBuf <1182563586@qq.com>

### [354ed6d](https://github.com/sgl-project/sglang/commit/354ed6d66b767e06d1305fd0cebc7c70da1e0584)

- **作者**: amote-i
- **时间**: 2026-09-03T11:53:39Z
- **提交信息**: [NPU] [DOC] Refresh supported models and features on NPU (#37799)

### [dd091f4](https://github.com/sgl-project/sglang/commit/dd091f43cdcfd08568c26287c90994cc8e6228fd)

- **作者**: kk
- **时间**: 2026-09-03T10:44:39Z
- **提交信息**: [AMD] Update kimi-k3 amd cookbook 0903 (#37781)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [a11dba1](https://github.com/sgl-project/sglang/commit/a11dba1a01ec553b01c76858ae53a2e04a056fca)

- **作者**: Cheng Wan
- **时间**: 2026-09-03T10:37:12Z
- **提交信息**: [Feature] Unified memory: support decode context parallelism for the trtllm_mla family (#37693)

### [f59a484](https://github.com/sgl-project/sglang/commit/f59a4840c508766d13ed982272bdf68a974a462f)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-09-03T10:32:44Z
- **提交信息**: [AMD][CI] Correct MI355X Slurm exclude node (#37779)

Co-authored-by: Chen <bingxche@amd.com>

### [429ac2d](https://github.com/sgl-project/sglang/commit/429ac2d82ccc931712a866e6e0991cf0413e82d4)

- **作者**: Duyi-Wang
- **时间**: 2026-09-03T09:46:49Z
- **提交信息**: [AMD] Fix DSv4 draft extend taking the target compression path during prefill (#37713)

### [27b7a2d](https://github.com/sgl-project/sglang/commit/27b7a2dc3baf6b93736540e35c1847efdfb56436)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-03T09:37:28Z
- **提交信息**: [Kimi K3] Rework skipped-think fix as opt-in force_nonempty_content with streaming coverage (#34187)

Co-authored-by: yhyang201 <yhyang201@gmail.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>

### [a600147](https://github.com/sgl-project/sglang/commit/a6001478f4300941f514b1f7b5544d13f8f0caae)

- **作者**: kk
- **时间**: 2026-09-03T09:28:28Z
- **提交信息**: [AMD] Perf Kimi-K3 MoE optimization (#33838)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [397aeca](https://github.com/sgl-project/sglang/commit/397aeca3762478161c2e11021e89d535f1fb6ae6)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-03T09:21:42Z
- **提交信息**: fix(benchmark): support Glm4MoeLite in fused MoE tuner (#37623)

### [7ed29eb](https://github.com/sgl-project/sglang/commit/7ed29eba80b5dd04b81b55bbc59a1dbf807b3c97)

- **作者**: Xinyi Song
- **时间**: 2026-09-03T08:49:46Z
- **提交信息**: [AMD] Fix FP4 indexer OOR (#37660)

Co-authored-by: Thomas Wang <1am9trash@gmail.com>

### [e59a576](https://github.com/sgl-project/sglang/commit/e59a576f0301829ae15fd8c65b25ef819c335df6)

- **作者**: Polisetty V R K Jyothendra Varma
- **时间**: 2026-09-03T08:48:55Z
- **提交信息**: fix test/manual/test_forward_split_prefill.py UT due to many refactors and design changes (#36617)

Signed-off-by: P V R K Jyothendra Varma <polisetty.v.r.k.jyothendra.varma@intel.com>

### [3bac084](https://github.com/sgl-project/sglang/commit/3bac084d4e498fd6f87bc93a3ee72bd724342583)

- **作者**: Yash Akhauri
- **时间**: 2026-09-03T08:39:43Z
- **提交信息**: [Model] Add native IFM K2 Horizon serving support (#37654)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1270
- **最后更新**: 2026-09-03T16:29:21Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 90913
- **最后更新**: 2026-09-04T00:06:13Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 31
- **主要提交者**: Taneem Ibrahim, Will Eaton, Wen Zhou

## AI分析总结

# vLLM 仓库提交分析总结

## 一、主要更新类型

本批次37个提交涵盖四大类别：**性能优化**（约10个）、**Bug修复**（约10个）、**Rust前端功能开发**（5个）、**新模型支持与CI改进**（其余）。整体呈现“性能驱动+功能扩展”双轮推进态势。

## 二、关键变更点与项目方向

1. **Rust前端加速推进**：多个提交围绕Rust前端展开，包括推理token报告、TLS支持、LoRA静态加载、token属性文本解析等。这表明vLLM正加速将核心服务层迁移至Rust，提升性能与安全性，与“easy, fast, cheap”目标一致。

2. **AMD/ROCm生态强化**：AITER版本升级、MiniMax-M3优化、gfx950低精度GEMM、Zen5 CI镜像等，显示vLLM正系统性增强AMD GPU支持，扩大硬件覆盖范围。

3. **新模型适配**：新增GLM-5.3-Flash、K2-Horizon、DeepSeek V4 FlashMLA KV缓存修复，体现紧跟前沿模型迭代的承诺。

4. **MLA架构深度优化**：Kimi-K3 MLA解码延迟削减、SiTU内核启用，针对MLA（Multi-Latent Attention）这一热门架构做专项优化。

## 三、项目影响与潜在意义

- **性能提升**：PDL等待前权重预取、Conformer注意力baddbmm累积、Triton top-p掩码内核等优化，将直接降低推理延迟，提升吞吐量。
- **稳定性增强**：多节点world size校验、PP张量发送同步、KV offload边界修复等，解决分布式推理中的关键一致性问题。
- **生态扩展**：GLM、K2-Horizon等新模型支持，配合Rust前端架构演进，巩固vLLM作为“一站式LLM服务”平台的定位。

## 四、值得关注的技术点

1. **Rust前端与Python后端的混合架构**演进路径值得关注，涉及推理token报告、TLS等生产级特性。
2. **CuteDSL MoE后端**与SM107低延迟GEMM计划的结合，代表NVIDIA GPU上MoE推理的新方向。
3. **KV Cache offload与多节点一致性**的系列修复，反映大规模部署中内存管理的复杂性。
4. **ActivationQuantFusionPass**手动融合pass的初步应用，预示量化与融合优化的新阶段。

## 五、对项目发展的影响

vLLM正从“高性能推理引擎”向“全栈AI服务平台”演进：Rust前端提供生产级服务能力，ROCm支持扩大硬件生态，新模型快速适配保持前沿性，而持续的性能优化巩固其速度优势。这些提交共同推动vLLM在“易用、快速、经济”三个维度上持续深化，巩固其作为LLM服务领域领先开源项目的地位。

## 详细提交记录

### [d6bce42](https://github.com/vllm-project/vllm/commit/d6bce42983bc0b2095ad6422dbf1399e219ae572)

- **作者**: Bugen Zhao
- **时间**: 2026-09-03T23:47:24Z
- **提交信息**: [Rust Frontend] Report reasoning tokens in chat completion usage (#54883)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [579aef4](https://github.com/vllm-project/vllm/commit/579aef4e8dfa2c9d498a702dd04c5ec5db333266)

- **作者**: Rohan Potdar
- **时间**: 2026-09-03T23:28:40Z
- **提交信息**: [ROCm] Bump AITER to 0.1.21.post1 (#52826)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Signed-off-by: Rohan Potdar <rohan.potdar@amd.com>
Signed-off-by: fai <fangzhouai@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: fai <fangzhouai@gmail.com>

### [bc2ee48](https://github.com/vllm-project/vllm/commit/bc2ee480738d7dcc558262a0c6d81956b515b050)

- **作者**: Yongye Zhu
- **时间**: 2026-09-03T22:40:16Z
- **提交信息**: [Perf] Prefetch the weight before the PDL wait in fused_q_kv_rmsnorm (#55020)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [9509fc8](https://github.com/vllm-project/vllm/commit/9509fc8ae61a8eb871a984e759a6d228c930df80)

- **作者**: Yongye Zhu
- **时间**: 2026-09-03T22:39:58Z
- **提交信息**: [Perf][Kimi-K3] Cut MLA decode concat/cache epilogue latency (#54896)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [c7e6e36](https://github.com/vllm-project/vllm/commit/c7e6e36fa93a5b8cb95b74fa96e4abdf2f0be51d)

- **作者**: Wen Zhou
- **时间**: 2026-09-03T21:56:44Z
- **提交信息**: [Rust Frontend] Add support for TLS in render server (#54999)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Richard <noreply@moonshot.cn>
Signed-off-by: Wen Zhou <wenzhou@redhat.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [6fdee17](https://github.com/vllm-project/vllm/commit/6fdee17f849b1aad5b4d88ff13b475d2e73d8c1a)

- **作者**: Andy Linfoot
- **时间**: 2026-09-03T21:34:35Z
- **提交信息**: [CI] Zen5 image build (#50314)

Signed-off-by: Chinmay Kulkarni <Chinmay.Kulkarni@amd.com>
Signed-off-by: andy-neuma <alinfoot@redhat.com>
Co-authored-by: Chinmay Kulkarni <Chinmay.Kulkarni@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [e410111](https://github.com/vllm-project/vllm/commit/e41011129bd54c9e8e12b645ea9b964027d2363f)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-03T21:00:29Z
- **提交信息**: [CI] Avoid logging test server environment values (#54379)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [cee0f92](https://github.com/vllm-project/vllm/commit/cee0f92c02112ace7120da45896d27e0fe95ea1e)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-03T20:20:18Z
- **提交信息**: [ROCm][Perf] Optimize MiniMax-M3 decode indexer and top-k (#54682)

Signed-off-by: fai <fangzhouai@gmail.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [2a336d8](https://github.com/vllm-project/vllm/commit/2a336d8239d00565a99752cfa248f2326e2ac8aa)

- **作者**: Ning Xie
- **时间**: 2026-09-03T19:44:21Z
- **提交信息**: [warmup] overlap renderer warmup and engine core initialization (#54557)

Signed-off-by: Andy Xie <andy.xning@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [fc8f107](https://github.com/vllm-project/vllm/commit/fc8f10792c59011447b56b41d4c8b1048673e939)

- **作者**: elehayym
- **时间**: 2026-09-03T19:29:14Z
- **提交信息**: Fix DeepSeek V4 FlashMLA auto KV cache dtype (#45091)

Signed-off-by: elehayym <huangxh1618@gmail.com>
Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: elehayym <huangxh1618@gmail.com>
Co-authored-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [2db1c4d](https://github.com/vllm-project/vllm/commit/2db1c4dc31c58bc4fd1f5fc48dbfceebc598e502)

- **作者**: Will Eaton
- **时间**: 2026-09-03T19:12:45Z
- **提交信息**: [Rust Frontend] Support `--lora-modules` for static adapter loading (#54837)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Will Eaton <weaton@redhat.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [21a2211](https://github.com/vllm-project/vllm/commit/21a22110404d98dcab5f51cd90e9acb0acc15e47)

- **作者**: Bugen Zhao
- **时间**: 2026-09-03T18:05:05Z
- **提交信息**: [Rust Frontend] Use token-attributed text in reasoning and unified parsers (#54884)

Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [8bf3963](https://github.com/vllm-project/vllm/commit/8bf39632b86df21fa9bfbb470ce8305bf67a5838)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-03T17:42:25Z
- **提交信息**: [ROCm][Perf] Add low-M FP32 router GEMM for gfx950 (#54845)

### [b762406](https://github.com/vllm-project/vllm/commit/b7624069ff023043b39ba4ea67ae5f6045556819)

- **作者**: Misha Goin
- **时间**: 2026-09-03T17:37:31Z
- **提交信息**: [Fusion] Manual `ActivationQuantFusionPass` initial application (#51415)

Signed-off-by: mgoin <mgoin64@gmail.com>
Signed-off-by: ElizaWszola <ewszola@redhat.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: ElizaWszola <ewszola@redhat.com>

### [d4d703c](https://github.com/vllm-project/vllm/commit/d4d703caf908786416585ceb1f369e2e0363358b)

- **作者**: sychen52
- **时间**: 2026-09-03T17:09:39Z
- **提交信息**: [Bugfix][Model] Fix FP8 PLE loading in mixed ModelOpt checkpoints (#54882)

Signed-off-by: Shiyang Chen <shiychen@nvidia.com>
Co-authored-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>

### [d410fc1](https://github.com/vllm-project/vllm/commit/d410fc12f30b4224fca71a2faca75dcd4a5c3557)

- **作者**: Bolin Sun
- **时间**: 2026-09-03T16:49:31Z
- **提交信息**: [Kernel] Enable Kimi-K3 SiTU on the CuteDSL MoE backend and the SM107 low-latency GEMM plan (#54606)

Signed-off-by: Bolin Sun <bolins@nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [98ed085](https://github.com/vllm-project/vllm/commit/98ed0856f31fa3aaf5e27464e2b4ef5a8ee6b2f5)

- **作者**: Jiangyun Zhu
- **时间**: 2026-09-03T16:40:35Z
- **提交信息**: [Model] add GLM-5.3-Flash support (#53906)

### [da8ec28](https://github.com/vllm-project/vllm/commit/da8ec2826898d47bd2fb424bc607052a6dc515c1)

- **作者**: Yifan Jiang
- **时间**: 2026-09-03T16:08:46Z
- **提交信息**: [Bugfix][KV Offload] Do not let a recurrent group's unhashed block truncate the load boundary (#52807)

Signed-off-by: Yifan Jiang <19356972+yifjiang@users.noreply.github.com>

### [4ae6228](https://github.com/vllm-project/vllm/commit/4ae6228284c4e9776f62d0867f543e621864176c)

- **作者**: mevince
- **时间**: 2026-09-03T15:58:07Z
- **提交信息**: [Bugfix][KV Connector] Populate SimpleCPUOffload BlockStored metadata (#54325)

### [e55b93f](https://github.com/vllm-project/vllm/commit/e55b93f2969d76b854eae158b6d17baea757d3e8)

- **作者**: Nick Hill
- **时间**: 2026-09-03T15:56:59Z
- **提交信息**: [Core] Deprecate "all" mamba cache mode (#55041)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [31e9c13](https://github.com/vllm-project/vllm/commit/31e9c13685b484d4ba67dc4e73019b23402609c7)

- **作者**: Jeff (Junze) Ma
- **时间**: 2026-09-03T15:16:22Z
- **提交信息**: [Bugfix][KV Connector] Safely fill circular buffers in DecodeBench (#54879)

Signed-off-by: Jeff Ma <jeffjma@umich.edu>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [edc0fb7](https://github.com/vllm-project/vllm/commit/edc0fb7e03b43fc17265c117f92021813711c6d8)

- **作者**: bhsueh_NV
- **时间**: 2026-09-03T15:02:59Z
- **提交信息**: Optimize PLE MTP metadata transfers (#55054)

### [bf95f58](https://github.com/vllm-project/vllm/commit/bf95f58d10891293aa6fde4e21f184d12ec0ba34)

- **作者**: Nick Hill
- **时间**: 2026-09-03T14:52:47Z
- **提交信息**: [Core] Triton kernel for small-batch top-p only masking (#54651)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [bb363db](https://github.com/vllm-project/vllm/commit/bb363db9a5ec2edc7b39e99b00af363a89d1fb81)

- **作者**: JasonCohere
- **时间**: 2026-09-03T12:02:49Z
- **提交信息**: feat: Add support for reasoning_token_count to reasoning parser (#54982)

Signed-off-by: Jason Ozuzu <jasonozuzu@cohere.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [848ab13](https://github.com/vllm-project/vllm/commit/848ab131bcdb5264bcff0d802f47f7d4adb0f548)

- **作者**: Sun
- **时间**: 2026-09-03T11:17:52Z
- **提交信息**: [Perf] Accumulate Conformer attention scores with baddbmm (#55062)

Signed-off-by: levius <2114377220@qq.com>
Co-authored-by: Codex <codex@openai.com>

### [758c79e](https://github.com/vllm-project/vllm/commit/758c79e1c5fc228a78d154f59dc0521e063e7a93)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-03T11:17:38Z
- **提交信息**: [Bugfix] Retain vocab embeddings during replacement (#55083)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [ee0a4c4](https://github.com/vllm-project/vllm/commit/ee0a4c46ae771af034ae676d44e932469586e7be)

- **作者**: Simon
- **时间**: 2026-09-03T10:52:42Z
- **提交信息**: [Bugfix] Account for PCP in multi-node world size validation (#55111)

Signed-off-by: DebugSy <532151398@qq.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [facd9a7](https://github.com/vllm-project/vllm/commit/facd9a74a1cd1b9fed324cdc2cceb8d54fdad3d0)

- **作者**: Giancarlo Delfin
- **时间**: 2026-09-03T10:32:33Z
- **提交信息**: [Model Runner V2][Spec Decode] Skip DP sync for all speculator uniform decodes (#54856)

### [0d3ede3](https://github.com/vllm-project/vllm/commit/0d3ede3e3bd62cae2fc5c465b9bc2e62028b1e71)

- **作者**: djramic
- **时间**: 2026-09-03T10:21:54Z
- **提交信息**: [Bugfix][Model] Enable torch.compile for StableLM (#54969)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [c21751c](https://github.com/vllm-project/vllm/commit/c21751c90b1b1d4cfd8fd6e951feaeb539171cfc)

- **作者**: Zupeng Wang
- **时间**: 2026-09-03T10:19:48Z
- **提交信息**: [Kernel] Warm up Qwen GDN gated RMSNorm (#54251)

Signed-off-by: Zupeng Wang <71580390+zupengwang@users.noreply.github.com>
Co-authored-by: OpenAI <support@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4cc0cb6](https://github.com/vllm-project/vllm/commit/4cc0cb6f76a608622a29d9ea8f4d415697e21364)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-03T09:55:10Z
- **提交信息**: [CI][AMD] Avoid expandable segments in LoRA TP tests (#55094)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [e6eb907](https://github.com/vllm-project/vllm/commit/e6eb9074e9f1fce6115dc036b40d07ebaa926979)

- **作者**: Harry Mellor
- **时间**: 2026-09-03T09:12:43Z
- **提交信息**: [CI] Bump Transformers version to 5.16.1 (#53905)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [096d8e8](https://github.com/vllm-project/vllm/commit/096d8e8ce61f43a7e142fba4b8ccb845d793c737)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-03T09:07:59Z
- **提交信息**: [ROCm][CI] Add MiniMax reduce RMS kernel coverage (#55057)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [1f76efa](https://github.com/vllm-project/vllm/commit/1f76efaa2195485b92cb04215aba6fb8f5fe523d)

- **作者**: Bowen Tan
- **时间**: 2026-09-03T08:17:08Z
- **提交信息**: [Model] Add K2-Horizon model support (#55063)

### [092334c](https://github.com/vllm-project/vllm/commit/092334c828e1114d6d8fb5828f7b0580e57e4a56)

- **作者**: chuanzhisongshu
- **时间**: 2026-09-03T08:07:35Z
- **提交信息**: [Bugfix] Wait for offload keys before storing chunks (#52923)

Signed-off-by: chuanzhisongshu <49055103+982945902@users.noreply.github.com>
Co-authored-by: lishuo121 <lishuo121@jd.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [859dd39](https://github.com/vllm-project/vllm/commit/859dd395128adbce604039f2d725be1067fdf9a3)

- **作者**: Derek Weitzel
- **时间**: 2026-09-03T08:01:36Z
- **提交信息**: [Bugfix][Core] Wait for the previous PP tensor sends before the next forward pass (#54962)

Signed-off-by: Derek Weitzel <djw8605@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ee17d0d](https://github.com/vllm-project/vllm/commit/ee17d0d869203ef9a35ad73358a4987bba14b1fc)

- **作者**: Clinton Thomas
- **时间**: 2026-09-03T07:15:58Z
- **提交信息**: Use server-generated keys for late-interaction query caches (#51445)

Co-authored-by: Lucas Bourtoule <35483370+dhalf@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-04
**监控日期**: 2026-09-03
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6632
- **最后更新**: 2026-09-03T23:08:51Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Eugene Zhao, Mu GuanLin, WeiQing Chen

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批提交以 **Bug修复** 为主（3项），辅以 **文档更新**（1项），无新增功能或性能优化。

### 2. 关键变更点与项目方向的关系
- **MiniMax-H3 模型精度修复**：修复融合调制过程中BF16残差语义丢失问题，直接保障模型推理数值正确性，属于核心推理路径的稳定性维护。
- **LTX视频模型蒸馏服务恢复**：修复两阶段视频服务回归，确保蒸馏模型在视频生成场景下的可用性，支撑多模态视频能力。
- **Omni健康路由归属修复**：恢复健康检查路由的正确所有权，涉及服务治理与可观测性，对生产环境运维至关重要。
- **生产扩散模型技能文档**：新增面向生产环境的扩散模型部署指南，填补了实操文档空白，降低用户上手门槛。

### 3. 对项目的影响与潜在意义
- 三项Bugfix均针对**已发布功能的回归或精度缺陷**，修复后能显著提升模型服务稳定性与输出质量，尤其对依赖精确数值计算的科研与生产用户价值明显。
- 文档补充完善了“从模型到生产”的闭环，配合Bugfix共同提升项目成熟度，增强社区信任感。

### 4. 值得关注的技术点
- **BF16残差语义**：涉及混合精度训练/推理中的数值稳定性，修复方式可能影响后续算子融合策略。
- **蒸馏两阶段服务架构**：LTX的修复暗示其服务层存在复杂的状态管理，值得关注其设计模式。
- **路由所有权**：健康路由归属问题反映服务组件边界划分，对微服务架构设计有参考意义。

### 5. 对项目发展的影响
vllm-omni定位为“人人可用的多模态模型服务”，本批提交虽无新功能，但通过**修复精度缺陷、恢复视频能力、完善运维与文档**，夯实了项目作为生产级基础设施的可靠性基础。特别是MiniMax-H3与LTX的修复，直接保障了前沿模型在统一框架下的可用性，符合项目“易用、快速、低成本”的愿景。文档更新则有助于吸引更广泛的用户群体，推动社区生态扩展。整体上，这批提交体现了项目在**稳定性和易用性**上的持续投入，为后续多模态能力扩展奠定坚实基础。

## 详细提交记录

### [fda3af8](https://github.com/vllm-project/vllm-omni/commit/fda3af8bbcdcdd822139e139955970157ab44f69)

- **作者**: Bo Li
- **时间**: 2026-09-03T18:01:34Z
- **提交信息**: [Bugfix] Preserve BF16 residual semantics in fused MiniMax-H3 modulation (#6878)

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [dff28e6](https://github.com/vllm-project/vllm-omni/commit/dff28e686711add0e929ce0c5660b09ef26c8c88)

- **作者**: WeiQing Chen
- **时间**: 2026-09-03T12:09:28Z
- **提交信息**: [Doc] Add production diffusion model skill (#6097)

Signed-off-by: David Chen <530634352@qq.com>

### [1dae537](https://github.com/vllm-project/vllm-omni/commit/1dae53731389cce1d2f99697c920a4c159196548)

- **作者**: Mu GuanLin
- **时间**: 2026-09-03T10:48:43Z
- **提交信息**: [Bugfix][LTX] Restore distilled two-stage video serving (#6847)

Signed-off-by: mglyn <1203789601@qq.com>

### [ec22c7a](https://github.com/vllm-project/vllm-omni/commit/ec22c7ac06ad1d344dbfcf6aaf8b641113bf87a5)

- **作者**: Eugene Zhao
- **时间**: 2026-09-03T07:54:36Z
- **提交信息**: [Bugfix] Restore Omni health route ownership (#6723)

Signed-off-by: qujing226 <qujing226@gmail.com>
Signed-off-by: Eugene Zhao <113281545+qujing226@users.noreply.github.com>

---
