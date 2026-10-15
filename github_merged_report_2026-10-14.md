# GitHub Stars 合并报告 - 2026-10-14

**合并日期**: 2026-10-15
**监控日期**: 2026-10-14
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


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2240
- **最后更新**: 2026-10-14T21:19:31Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: zangyu

## AI分析总结

## 提交记录分析：ByteDance-Seed/VeOmni（2c07c48）

### 1. 主要更新类型
**功能新增**。这次提交为模型（model）和训练器（trainer）模块增加了对**选择性重计算（selective recomputation）**的支持。

### 2. 关键变更点及其与项目整体方向的关系
- **核心功能**：选择性重计算（通常与 gradient checkpointing 相关）是一种经典的显存-计算权衡技术：通过在反向传播时只保留部分中间激活、重新计算其余部分，从而显著降低训练时的显存占用。
- **与项目方向的关系**：VeOmni 的定位是"以模型为中心的分布式训练配方库"，目标是支撑大规模多模态模型训练。选择性重计算正是大规模分布式训练中"省显存、扩规模"的关键基础设施之一，与项目的"Scaling"核心目标高度一致。

### 3. 对项目的影响和潜在意义
- **降低训练门槛**：使用户能在相同硬件条件下训练更大模型或使用更大 batch size，提升训练资源利用率。
- **增强分布式训练能力**：与项目已有的分布式策略（如并行、通信优化）叠加，为更极致的扩展性提供新维度。
- **完善训练配方库**：作为"recipe zoo"的一块拼图，丰富了用户可选的显存优化手段组合。

### 4. 值得关注的技术点
- **"selective" 的粒度与策略**：选择性重计算区别于全局重计算的关键在于"选择"——如何判断哪些层/算子值得重计算、哪些直接保留，这直接影响显存节省幅度与额外计算开销的平衡。
- **model 与 trainer 双模块改动**：说明该特性需要模型侧（定义 checkpoint 边界）与训练侧（调度重计算逻辑）协同设计，体现了框架层面的深度集成。
- **性能-显存权衡的可配置性**：需关注是否提供细粒度开关（如按层配置），这对实际生产调优非常重要。

### 5. 基于项目背景对发展的影响
VeOmni 面向"任何模态的模型训练"，多模态模型（尤其含视觉、语音、长序列文本）训练时显存压力巨大，激活值常成为瓶颈。本次提交补强了显存扩展这一基础能力，使项目在与同类大模型训练框架竞争时，在"大规模可训性"上更完整。它与项目既有的分布式配方协同，有助于兑现"Scaling Any Modality Model Training"的愿景，是推向生产级大规模训练的重要一步。

---
**总结**：本次提交是一次与项目战略定位高度契合的功能增强，通过引入选择性重计算机制，强化了 VeOmni 在大规模多模态训练场景下的显存优化与扩展能力，值得关注其具体的选择策略设计与配置灵活性。

## 详细提交记录

### [2c07c48](https://github.com/ByteDance-Seed/VeOmni/commit/2c07c4831773cc5ead42f6317685be3dafb9faeb)

- **作者**: zangyu
- **时间**: 2026-10-14T12:22:40Z
- **提交信息**: [model, trainer] feat: support selective recomputation (#1166)

Co-authored-by: vvyuervv <2794113628@qq.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2907
- **最后更新**: 2026-10-14T23:21:24Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2298
- **最后更新**: 2026-10-14T16:38:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6619
- **最后更新**: 2026-10-14T23:58:13Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 10
- **主要提交者**: Adrian, Ziang Li, Yang Xu

## AI分析总结

# FlashInfer 昨日提交综合分析（共 20 条提交）

## 主要更新类型
昨日提交以**性能优化**为绝对主导（约 14 条），其余为功能新增（3 条）、Bug 修复（2 条）、CI 重构（1 条）与文档治理（2 条），无大规模重构。

## 关键变更点
- **MoE 解码全面深挖**：SM107 稀疏 MegaMoE 解码优化（跳过无效槽位、减少尾部同步、新增 GenPhase 配置）；小 token 批次新增 N32 W4A16 MegaMoE 路径与 16 个自动调优候选；Kimi-K3 NVFP4 MoE 在 SM100 16384-token 行引入 per-CTA 私有化路由，CTA 启动从 1024 降至 256；MegaMoE 工作区支持按 capacity 定制固定 knobs。构成"优化-扩容-灵活性"的完整推进。
- **CAKE 团队持续交付**：为 MiniMax 稀疏注意力（MSA）家族在 SM100/SM103 重新生成 prefill 与 Top-K 路由内核——调度级优化（union-route 选择、两阶段折叠 GQA、消除共享内存 bank 冲突）使 paged first_topk 提速 1.8–2.7×、Top-K 流式选择提速约 1.4×；NVFP4 稀疏 MLA 解码利用 TMEM 存 Q 码腾出空间实现 V 双缓冲无损提速；另新增融合 NVFP4/FP8 GEMM 加 BF16 LoRA 修正的 kernel 及 Qwen3-Next/3.5 多几何形状的 CP-prefill 交付。
- **GEMM 后端智能化**：`mm_bf16(backend="auto")` 在有自动调优时纳入 CuTe DSL 后端，小 M 场景 SM107 提速 1.26×，最差形状差距从 2.11× 收敛至 1.03×。
- **解码路径调优与指令优化**：修复 trtllm-gen 分页解码中 >16 KV 分片被强制切到 GMEM 归约的问题，明确"每 CTA ≤ 4096 KV token 时 CGA 更优"的边界；MiniMax-H3 FC1+SwiGLU 与 norm/AdaLN 分别通过设备名分派（GeForce 专属单位标度 mxf8f6f4）和指令打包优化，SASS 指令数降低 19–32% 且逐位一致。
- **Bug 修复与基础设施**：修复 dummy warmup 后 CUDA graph 签名污染、W4A16 图测试 int64/int32 路由 ID 不匹配、SM120 W4A8 在 CuTe DSL 4.9 下编译失败等问题；CI 将隔离标记拆分为三级（node/gpu/memory）并支持 `--workers-per-gpu` 并发；文档审计修复 193 个问题覆盖 411 页站点，补齐 docstring 与环境变量文档。

## 对项目的影响
项目正沿三条主线纵深推进：**一是**面向 Blackwell（SM100/103/107）与 GeForce（SM120）的宽硬件谱系，同时覆盖注意力（MSA）与 MoE 两大核心算子，并下放至消费级 GPU；**二是**通过更智能的自动调优降低用户门槛，可靠性大幅提升；**三是**与 CAKE 管线深度协同，对接 MiniMax、Kimi-K3、Qwen、GLM5、DeepSeek 等前沿模型，形成"生成器→bitwise 验证→板卡实测→receipts"的成熟交付闭环。国产大模型在 B200/GB300 上的高效推理由此获得关键基础设施支撑。

## 值得关注的技术点
- **TMEM 高级编程**：将 Q 的 E2M1 码写入空闲 TMEM，让 tensor core 直接取 A 操作数，共享内存让位 V 双缓冲。
- **内存一致性把控**：共享内存重写后需 fence 推入 async proxy 才能 TMA 发布，CTA barrier 不够。
- **CUDA graph 签名陷阱**：dummy warmup 的内部 dtype 会污染稳态签名，对推理框架集成方有警示价值。
- **per-CTA 私有化路由**：以全局原子操作换共享内存局部性，是大规模 MoE dispatch 的新范式。
- **数值不变性纪律**：性能优化普遍保证 bitwise identical，纯调度/形态改动获取"免费"性能是团队一贯手法。
- **按架构 fail-closed 的 resolver**：未导出记录的架构抛显式错误，避免静默回退。

总体而言，FlashInfer 已进入"特定模型 × 特定硬件 × 特定批形状"的深度优化阶段，在自动化内核管线、数值验证纪律与 CI 基础设施三者协同下，持续强化其作为推理框架底层算子枢纽的地位。

## 详细提交记录

### [0a0cecb](https://github.com/flashinfer-ai/flashinfer/commit/0a0cecb50b1250f0b609a9c51f1b25816ba073b8)

- **作者**: Yang Xu
- **时间**: 2026-10-14T23:58:06Z
- **提交信息**: perf(moe): optimize sparse SM107 MegaMoE decode (#6447)

<!-- .github/pull_request_template.md -->

## 📌 Description

Sparse decode often reserves a large token capacity while only a few
routes are live. This optimizes the existing SM107 Generic and GenPhase
MegaMoE paths by avoiding invalid-slot work, shortening sparse metadata
handling and reducing tail synchronization overhead.

- Mask invalid payloads and scores in the separate BF16 reducer,
allowing the matching pre-launch combine clear to be omitted. Quantized
combine and in-kernel reduction keep their clearing rules.
- Skip invalid histogram/scatter work. Fence rewritten shared-memory
data into the async proxy before TMA publication; a CTA barrier alone is
insufficient. GenPhase publishes the last valid route extent, transfers
its aligned metadata prefix and uses a bounded shorter sort path,
preserving holes and route IDs.
- Reuse the existing padded scale-factor prefix for refinement
scheduling.
- Admit GenPhase `(256,64,128)` for the qualified MXFP8 E4M3 and mixed
MXFP4/MXFP8 paths, with matching SFB/TMEM indexing, gather participation
and live-row Gather4 transaction counts. Add the configurations to the
offline tuning menu.
- Use counted non-aligned barriers in warp-role branches and preserve a
two-dimensional gather descriptor at capacity one.
- Let CTA0 clear small tail-reset prefixes after the required drains,
removing the post-reset local grid join. Generic keeps both peer
barriers; GenPhase keeps its single peer barrier. EP1, prefixes above 16
KiB and NCU mode retain distributed reset.
- Explicitly drain the preceding GenPhase router and join every
main-kernel warp role before reset. Empty work cannot use epilogue
completion as proof that all consumers have acquired ready flags or that
refinement has stopped updating its counter.

- Reject multirank GenPhase N64 phase-interleave during host
configuration, before allocation or compilation; `is_valid_sm107`
applies the same boundary to tuning candidates. Grouped N64, EP1
phase-interleave and inherited N128/N256 admission remain.

Public call signatures and default-family selection are unchanged.
Existing `inference` callers receive eligible internal improvements;
using the separate GenPhase/N64 path still requires selecting that
family and retuning. This extends the original implementation and does
not introduce a FROST backend.

## 🔍 Related Issues

Follow-up optimization of the existing SM107 MegaMoE implementation; no
separate tracking issue.

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

- [x] Tests have been added or updated as needed.
- [ ] All repository tests are passing (`unittest`, etc.).

Current head `fff72c2` adds a host-only scheduling admission guard.
**All 41 exported device files and the other unchanged runtime
dependencies are byte-identical to `3cc30cd`.** Of 554 MoE runtime
Python files, only `shim/block_scaled.py` changes, to reject multirank
N64 phase-interleave. The retained grouped path computes the same
descriptors and launches the same device implementation.

New guard qualification on native SM107:

- **48 host runtime-option tests pass**, including 15 schedule-boundary
cases. The same new detector against the preceding shim gives the
expected nine rejection failures and six retained-boundary passes.
- **102 selected single-GPU tests pass**, plus **32 separate live-row/SF
boundary cases** covering retained EP1 N64 phase-interleave, grouped
controls and N128 across E4M3/mixed formats. The original single-suite
filter does not select those 32 cases; they were run explicitly.
- **Eight changing-route cases pass on every rank at both EP4 and EP2**,
with grouped N64, C2 and mixed-format cases, early/late weights,
seven-pusher stress, NaN-poisoned combine storage, exact-zero inactive
rows and first/65th captured replays.
- Changed-file pre-commit checks pass. At current head `fff72c2c`, the
[targeted H100 CI
job](https://github.com/flashinfer-ai/flashinfer/actions/runs/38551390140/job/115810256269)
passed **177 tests**, with **188 architecture skips** and zero failures.
All six x64/arm64 × CUDA 12.9/13.0/13.4 AOT build/import jobs and the
[targeted CI
workflow](https://github.com/flashinfer-ai/flashinfer/actions/runs/38551390140)
have passed. H100 architecture skips are not native SM107 execution
evidence; native results are listed separately above.

The unchanged device implementation was additionally qualified at
`3cc30cd`: all 71 registered multirank tests per rank at EP2 and EP4
passed without skips, and all-kernel synccheck/memcheck each passed
eight GenPhase changing-route cases on all four ranks, with four
zero-error summaries and no tool warnings. These are explicitly reused
device-source results, not newly executed broad suites on the guarded
head. Sanitizers complement source review and do not prove every
cross-GPU memory-model relation.

The new boundary addresses a concrete qualification gap: current-source
N64 phase-interleave passed the EP4 changing-route suite but stalled in
its first EP2 case and hit the 600-second qualifier timeout. The exact
warmup/replay invocation was not isolated. A separate ready-dispatch
prototype also timed out at its EP4 native gate and was not admitted to
performance testing or this PR. Grouped performance results below do not
qualify phase-interleave.

Reproduce the bounded checks on native SM107 with a supported CuTe DSL
runtime:

```bash
CUTE_DSL_ARCH=sm_107a python tests/moe_ep/qualify_sm107.py --suite host --filter runtime_options --output-dir /tmp/sm107-admission-host
CUTE_DSL_ARCH=sm_107a python tests/moe_ep/qualify_sm107.py --suite multi --world-size 4 --filter 'sparse_to_dense and genphase' --output-dir /tmp/sm107-routing-ep4
CUTE_DSL_ARCH=sm_107a python tests/moe_ep/qualify_sm107.py --suite multi --world-size 2 --filter 'sparse_to_dense and genphase' --output-dir /tmp/sm107-routing-ep2
CUTE_DSL_ARCH=sm_107a python tests/moe_ep/qualify_sm107.py --suite single --filter 'routing_graph or masked_combine or genphase_cga2 or runtime_options or qualification or block_scaled_contracts or test_sm107_combine or genphase_repeated_launches' --output-dir /tmp/sm107-sparse-single
CUTE_DSL_ARCH=sm_107a python tests/moe_ep/qualify_sm107.py --suite single --filter genphase_live_rows_and_sf_tile_boundaries --output-dir /tmp/sm107-ep1-boundaries
```

These are bounded native gates, not the entire repository matrix.
`VENDOR.md` inventories local device changes and the supported subset;
`SKILL.md` records publication/reset contracts and EP-specific schedule
qualification; `TUNING.md` documents the restriction and retuning path.
An initial admission-detector invocation selected the wrong suite and
collected no tests; the strict runner rejected it, and the corrected
host-suite red/green records are retained with identical source/tests.

## Kernel GPU-time comparison

**Direct comparison of the complete current PR against the best measured
original FlashInfer finalist, on the same SM107 hardware with matched
shape, EP, inputs and cache protocol. Model-shaped kernel tests are not
model-throughput tests.**

Synthetic Qwen-shaped routed MoE: H=2560, I=640, E=512, top-k=10,
capacity 1024 per rank; MXFP8 E4M3, SwiGLU, late routing weights and
separate BF16 combine. Four physical SM107 GPUs over NVLink, EP4/TP1. T
counts live input tokens per rank; N is the token-axis tile width.

| Workload/cache | Best original main (µs) | Current PR main (µs) |
Combined speedup | GPU time saved |
|---|---|---|---|---|
| T1 warm | 42.29–42.30 | 24.49 | **1.73×** | 42.1% |
| T1 cold | 42.61–42.63 | 28.28–28.33 | **1.50–1.51×** | 33.5–33.7% |
| T64 warm | 86.36–86.43 | 78.29–78.30 | **1.103–1.104×** | 9.3–9.4% |
| T64 cold | 87.45 | 82.63–82.70 | **1.057–1.058×** | 5.4–5.5% |
| T1024 warm | 104.58–104.60 | 100.90–101.03 | **1.035–1.037×** |
3.4–3.5% |

Original source is `53e3168`; current PR source is **`fff72c2`**. Each
row measures the complete combination directly. Incremental ablation
gains are not multiplied into these results. Ranges span two execution
orders, not confidence intervals.

| Workload | Winning original | Winning current PR |
|---|---|---|
| T1 warm/cold | Generic c19 | GenPhase N64/C4, grouped |
| T64 warm/cold | Generic c03, N64/C2, phase-interleave | Same Generic
c03 |
| T1024 warm | GenPhase c06, N128/C4, phase-interleave | Same GenPhase
c06 |

The T1 comparison includes newly supported GenPhase geometry and
configuration selection as well as source improvements. The T64/prefill
winners retain the same configurations on both sides. Both kernel
families use Tensor Core GEMMs. The multirank N64 phase-interleave guard
applies to GenPhase, not the Generic T64 winner.

The original screen covers 32 menu entries, resolving to **31 distinct
configurations**, for each listed workload/cache condition. T1
confirmation compares five original Generic/GenPhase finalists with the
current candidate; T64/prefill confirmation selects original and current
top-two finalists independently. The screens use seed 5678 and three
routes. Confirmation uses held-out seed 9187, six routes and both
execution orders on the same four GPUs and allocation, with T129/T1024
full-row reference/graph gates. T1 has 24 timing runs and ten dense
gates; T64/prefill has 30 timing runs (including one separately tracked
mapper candidate) and three common-harness bridge checks. All 96 T1
timing rank records and 132 T64/prefill timing/bridge rank records were
independently audited. This is a finite-menu result, not an exhaustive
optimum. The two cold T1 Generic leaders are within 0.01 µs.

<details>
<summary>Reproducible winning configuration overrides</summary>

All use separate BF16 reduction, bulk FC2 stores, epilogue flag batches
`(1,4)` and the common shape/math above. Overrides below distinguish the
winners; full resolved configurations are retained with the benchmark
records.

| Configuration | MMA tile (M,N,K) | Cluster / fallback | Schedule |
Work IDs | FC2 TMA stages |
|---|---|---|---|---|---|
| Original Generic c19 | (256,128,128) | (4,1) / (2,1) | grouped |
grid_stride | 2 |
| Current GenPhase T1 | (256,64,128) | (4,1) / none | grouped |
atomic_counter | 1 |
| Original/current Generic c03 | (256,64,128) | (2,1) / none |
phase_interleave, hint 4 | atomic_counter | 1 |
| Original/current GenPhase c06 | (256,128,128) | (4,1) / none |
phase_interleave, hint 4 | atomic_counter | 2 |

</details>

CUPTI records main-kernel GPU duration from eight native launches per
CUDA Graph, with 16 profiled replays after two warmup replays. Each
invocation takes the maximum across four ranks; the result is the median
across 128 samples and then the mean across six routes. Warm reuses
buffers; cold flushes 512 MiB before each invocation, outside the
component timing. Runtime: PyTorch 2.13 + CUDA 13.0 and CuTe DSL
4.8.0a0. Inputs and the specified mathematics match across providers;
all active output rows and columns are checked before/after graph replay
and profiling, with finite/exact-zero inactive rows. Input fingerprints
sample 4096 bytes plus deterministic generation, not full tensor hashes.

The metric includes waits inside the main kernel. It excludes separate
router/reducer/clear kernels, gate projection/top-k selection, CPU/API
overhead and serving latency. Kernel partitioning differs between
families and PDL allows overlap; component durations must not be added
to infer end-to-end performance.

### Final scope and deferred work

This PR is ready for review at `fff72c2`; the optimization scope is
closed for this revision. Further scheduler/mapper/prefetch prototypes
remain outside the diff. The strongest recent mapper follow-up adds only
about 1.8% at T64 warm and 1.4–1.5% cold against current PR, while
regressing N128 prefill by about 0.7%; it has not earned general
adoption. Fixed grouped-control gains do not establish wins over
independently selected workload baselines.

Earlier GLM-, DeepSeek- and Kimi-shaped measurements support specific
component/eligible-path behavior; they are not current-head,
best-original totals. The separately tuned FE/FI compatible-contract
campaign remains incomplete. No additional FE, full-model throughput or
Blackwell performance claim is made.

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

Review findings have been addressed in the current diff: the Generic
shared-to-async publication now fences every writer before the TMA
issuer's CTA join, and changing-route sparse-to-dense replay regressions
cover the failure. The three new single-GPU test files are registered in
both `qualify_sm107.py` and `tests/moe_ep/run_tests.sh`. `VENDOR.md`
records local exported-code exceptions and admitted C2/N64 geometry. The
sort wrapper passes its acquired route extent into `_run_sort_impl`,
removing the duplicate wait/load while retaining the
histogram-initialization barrier. These source fixes and qualifications
do not substitute for maintainer review.

Please focus on shared-to-async publication, the sparse ready-flag and
reset lifetime contracts, all-role participation before reset, two-CTA
SFB parity, Gather4 transaction accounting and named-barrier participant
counts. No new EP8, Blackwell or NCU performance claim is made.

The all-files hook checkbox remains unchecked: hooks were run on changed
files to avoid unrelated formatting churn.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added GenPhase tuning candidates for supported N64 MXFP8 E4M3 and
mixed MXFP4/MXFP8 configurations. These candidates do not change the
default inference configuration.
* BF16 combine can skip invalid routes during separate top-k reduction,
avoiding a preliminary clear of the combine buffer. Quantized combine
retains its existing clearing behavior.
* Routing exchanges adapt to active routes, including empty and
partially filled route sets.

* **Bug Fixes**
* Improved handling of partially filled tiles, invalid routes, and
routing changes during CUDA Graph replay.
* Expanded SM107 qualification coverage for supported configurations and
routing scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c5877ff](https://github.com/flashinfer-ai/flashinfer/commit/c5877ff2a56f8eb96218556261f0d97644bb1796)

- **作者**: Vincent
- **时间**: 2026-10-14T23:32:39Z
- **提交信息**: gemm: let mm_bf16 auto consider the CuTe DSL backend (#6392)

## 📌 Description

**`mm_bf16(backend="auto")` now considers the CuTe DSL backend.** `auto`
never included `"cute-dsl"` among its candidates, although it is the
fastest `mm_bf16` backend at low M on SM100/SM103/SM107. With this
change, autotuning can select it.

Without autotuning, `auto` behaves exactly as before. The cute-dsl
runners are appended after the existing ones, so the no-autotune
fallback (`runners[0]`) is still the first of cuDNN, cuBLASLt and
CUTLASS. I also tried making cute-dsl the no-autotune default for M <=
32 and dropped it: cute-dsl's untuned tactic choice regresses some
shapes by up to 2x on both SM100 and SM107 (wide N, or shallow K with
wide N).

The change is confined to `_heuristic_func_mm_bf16` in
`flashinfer/gemm/gemm_base.py`.

## 📊 Performance

`mm_bf16`, `backend="auto"` with autotuning, before vs after, 35 shapes
(M 1-8192; N, K in 256-24576). Both sides were measured with each
backend autotuned in isolation (the benchmark change in #6147); without
it, `auto` can reuse another backend's tuned runner and the numbers are
not meaningful.

| | M <= 32 | M > 32 | `auto` vs fastest single backend, worst shape |
|---|---|---|---|
| SM107 | **1.26x** | ~1.0x (within noise) | 2.11x -> **1.03x** |
| SM100 (GB200)* | **1.18x** | ~1.0x (within noise) | 1.96x -> **1.08x**
|

Without autotuning `auto` is unchanged (SM107, M <= 32: 1.00x, worst
shape 0.99x).

\* Measured on an earlier revision that additionally changed the
no-autotune default; the autotuned path is identical (same candidate
set; the winner is chosen by profiling).

The BF16 GEMM rows of our performance regression suite (`mm_bf16`,
`bmm_bf16` and `tinygemm_bf16`, explicit backends) show no change on
GB300, GB200 or SM107: 52 rows, A/B'd on the same GPU over three
alternating rounds (on the earlier revision), all within run-to-run
noise. Those rows name explicit backends, so neither revision's `auto`
change is reachable from them.

## 🧪 Tests

- `tests/gemm/test_mm_bf16.py` on SM107: 27 passed, 1 skipped (TinyGEMM
is not enabled on SM107). On SM100 (GB200) the earlier revision passed
in full.
- `--refcheck` on every benchmarked shape and backend: no mismatches.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] `ruff check` / `ruff format --check` (v0.12.8) pass on the changed
files.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>

### [0cf804f](https://github.com/flashinfer-ai/flashinfer/commit/0cf804f0602bbb7332996495a32160dba67111d0)

- **作者**: nvamyt
- **时间**: 2026-10-14T22:41:31Z
- **提交信息**: fix(moe_ep): defer steady-state signature after dummy warmup (#6349)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Fix MegaMoE CUDA graph tests failing after a dummy warmup() with:
MegaMoE steady-state input signature changed
warmup() creates dummy routing IDs with the default torch.arange dtype
(int64). The dummy forward then stores that dtype in the workspace’s
steady-state input signature.
The SM100 W4A16 MegaMoE backend supports both int32 and int64 routing
IDs, and its warmup prepares staging variants for both. However, when
the first real batch uses int32 routing IDs, the cached dummy signature
incorrectly rejects it as a signature change.
This change removes the signature established by an internally generated
dummy batch after warmup completes. The first real batch can then
establish the steady-state signature. Explicit warmup(t) calls are
unchanged and continue to use the caller-provided input as the
steady-state signature.
## 🔍 Related Issues
#6347 
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

* **Bug Fixes**
* Dummy-input warmup no longer leaves a cached forward signature that
can affect the first real batch. Warmup with a supplied batch continues
to retain its signature.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ceb589c](https://github.com/flashinfer-ai/flashinfer/commit/ceb589ce3e28bebcbb3b6628b5d4fcb5c2c2eceb)

- **作者**: Ziang Li
- **时间**: 2026-10-14T21:52:14Z
- **提交信息**: Add small-shape W4A16 MegaMoE tactics and model benchmarks (#6277)

## 📌 Description

@humansand

Small token batches previously used N64/N128 tiles. Add N32 W4A16
MegaMoE paths and autotune candidates, plus model presets for
reproducing small-shape workloads.

- **N32 implementation:** FC1 executes one 32-token epilogue half; FC2
uses the corresponding compact accumulator load, conversion, transpose
and store. M128 uses one-CTA MMA and M256 uses two-CTA MMA, both with
K256 and cluster `(2,1,1)`.
- **Autotuning:** four tiles, `((128,32,256), (256,32,256),
(256,64,256), (256,128,256))`, × group hints 512/1024 ×
epilogue/dispatch return modes give **16 default tactics**. M128 is
limited to N32; larger tiles remain available for dense workloads.
- **Contracts:** retain the existing activation math, bit-exact
reference, scheduler, two weight-decode warp groups, weight layout and
fused deterministic combine. N64/N128 retain their existing epilogue
paths.
- **Benchmark support:** add the presets below while preserving the
`deepseek-v3` default, and normalize fixed JSON tactic tuples. Reported
measurements use `--precomputed-routing` to exclude routing preparation
from timing.

| Added preset | Hidden D | Intermediate E | Experts N | Top-K |
Activation |
|---|---:|---:|---:|---:|---|
| `kimi-k3` | 3584 | 3072 | 896 | 16 | SiTU(4,25) |
| `deepseek-v41-flash` | 5120 | 2304 | 384 | 6 | SwiGLU, clamp 10 |
| `glm5` | 6144 | 2048 | 256 | 8 | SwiGLU |

### Performance

**GLM5, one routed-expert layer, EP8 on 8× B300 SXM6 AC.** Baseline:
`a7103ae2a97f38f4dbbf410c32acc7c6fe99cab1` with the same model benchmark
driver and AUTO8. Final: unmodified
`866c80d0c70a90624b4c2056d12d1543d709609e`, AUTO16.

- **Timing:** one fresh process group per arm; 3 warmups and 100
untrimmed cold-L2 CUPTI CUDA-graph samples per point. Latency is the
median of per-iteration rank-MAX GPU activity spans. The saved baseline
is reused; samples are not pooled across arms.
- **Workload:** global token counts, D6144/E2048/N256/K8, SwiGLU,
grouped routing (8 groups/top4, scale 2.5). Timing includes staging,
dispatch, FC1/activation/FC2, return and deterministic combine. Routing
preparation, autotuning, graph capture and L2 flushing are excluded, as
are attention and shared experts.
- **Controls:** PDL enabled; fused TMA/FC2 reduction disabled; fused
deterministic combine enabled; `apply_topk_in_fc1=False`.

| Global tokens | BEFORE AUTO8 µs | Final AUTO16 µs | Speedup | Final
tactic M/N/G/return |
|---|---:|---:|---:|---|
| 1* | 64.4810 | 65.8080 | 0.97984× | 128/32/512/epi |
| 2* | 84.8325 | 82.4325 | 1.02911× | 256/64/1024/epi |
| 4 | 92.4970 | 91.6010 | 1.00978× | 256/32/512/epi |
| 8 | 113.4085 | 112.0650 | 1.01199× | 128/32/512/epi |
| 16 | 124.5285 | 123.4570 | 1.00868× | 256/32/512/epi |
| 32 | 142.4010 | 140.4815 | 1.01366× | 256/32/1024/epi |
| 64 | 156.8810 | 169.6655 | 0.92465× | 128/32/512/epi |
| 128 | 165.6645 | 160.4810 | 1.03230× | 256/32/1024/epi |
| 256 | 169.7610 | 164.6895 | 1.03079× | 256/32/1024/epi |
| 512 | 172.8170 | 166.9935 | 1.03487× | 256/32/1024/epi |
| 4096 | 396.4350 | 393.0275 | 1.00867× | 256/128/1024/dispatch |
| 8192 | 662.8690 | 667.2550 | 0.99343× | 256/128/1024/dispatch |
| 16384 | 1232.4130 | 1244.3505 | 0.99041× | 256/128/512/dispatch |

`epi` = `epi_warps`; `dispatch` = `reuse_dispatch_warps`. All selected
tactics use K256, cluster `(2,1,1)`, scheduler depth 2 and flag batch 4.
*T1/T2 are reported but excluded from the geometric means and retention
decision.*

Geometric-mean speedup is **1.00495×** across T4–16384: **1.00777×** for
decode T4–512 and **0.99747×** for prefill. Results are mixed: T128–512
improve, T64 regresses, and prefill is approximately flat. This is one
sweep against a saved baseline, not a paired statistical study or an
end-to-end speedup claim. Current BEFORE-versus-final performance
evidence here is limited to GLM5.

Raw samples and selected tactics: [final GLM5, all 1,300
samples](https://gist.githubusercontent.com/zianglih/de71cbb5abd9811563eb81af200425e3/raw/afa72c28f2505ca467edc837efc619c535a4af1b/public-raw-samples-glm5-866c-fresh-v1.json);
[baseline
archive](https://gist.githubusercontent.com/zianglih/b0fab803ada6848668bf441c8c7a542c/raw/03a14d0feb2240a126fef159c3f05f4e2494850e/public-raw-samples-clean-48fce-all-models-v1.json),
using only its `glm5-before-v1` arm for this comparison.

<details>
<summary>Environment, setup and benchmark command</summary>

- **Image:** `nvcr.io/nvidia/pytorch:26.05-py3`; CUDA 13.2.1; host
driver `590.48.01`; Python 3.12.3.
- **Runtime:** container Torch `2.12.0a0+5aff3928d8.nv26.5.50603568`;
CuTe DSL 4.7.1; CUDA Python/bindings 13.2.0; CUPTI Python 13.2.0 / CUPTI
13.2.86; NVSHMEM 3.6.5 / nvshmem4py 0.3.1. Container Torch is retained.

In a dedicated checkout, set `K3_ROOT` to its parent directory:

```bash
export K3_ROOT=/data/home/ziangli/flashinfer-k3-w4a16-megamoe-opt
cd "$K3_ROOT/flashinfer"
git fetch origin pull/6277/head
git switch --detach 866c80d0c70a90624b4c2056d12d1543d709609e
git submodule update --init 3rdparty/cccl 3rdparty/cutlass 3rdparty/nixl 3rdparty/spdlog
export BUILD_NVEP=0 BUILD_NIXL_EP=0 BUILD_NCCL_EP=0
export FLASHINFER_BUILD_NO_PIP=1 MAX_JOBS=8
unset PIP_CONSTRAINT
cat > "$K3_ROOT/pr-validation-constraints.txt" <<'EOF'
torch==2.12.0a0+5aff3928d8.nv26.5.50603568
nvidia-cutlass-dsl==4.7.1
cuda-python==13.2.0
cuda-bindings==13.2.0
cupti-python==13.2.0
nvidia-cuda-cupti==13.2.86
nvshmem4py-cu13==0.3.1
nvidia-nvshmem-cu13==3.6.5
EOF
python3 -m pip install --disable-pip-version-check \
  --upgrade-strategy only-if-needed -c "$K3_ROOT/pr-validation-constraints.txt" \
  'nvidia-cutlass-dsl[cu13]==4.7.1' 'cuda-python==13.2.0' \
  'cuda-bindings==13.2.0' 'cupti-python==13.2.0' \
  'nvidia-cuda-cupti==13.2.86' 'nvshmem4py-cu13==0.3.1' \
  'nvidia-nvshmem-cu13==3.6.5' 'setuptools>=77' 'packaging>=24' \
  'apache-tvm-ffi>=0.1.11,<0.2'
python3 -m pip install --disable-pip-version-check \
  --upgrade-strategy only-if-needed -c "$K3_ROOT/pr-validation-constraints.txt" \
  --no-build-isolation -e '.[cu13]'
python3 -m pip install 'pytest==8.4.2'
python3 -m pip install --no-deps \
  'apache-tvm-ffi==0.1.14.post1' 'cuda-core==1.2.1' 'cuda-pathfinder==1.5.4'
```

```bash
export PYTHONPATH="$K3_ROOT/flashinfer" PYTHONUNBUFFERED=1
export CUDA_VISIBLE_DEVICES=0,1,2,3,4,5,6,7
export CUDA_HOME=/usr/local/cuda CUDA_MODULE_LOADING=LAZY
export FLASHINFER_WORKSPACE_BASE="$K3_ROOT/compile-cache/c2-sm103/flashinfer"
export CUTE_DSL_CACHE_DIR="$K3_ROOT/compile-cache/c2-sm103/cute-dsl"
export CUDA_CACHE_PATH="$K3_ROOT/compile-cache/c2-sm103/cuda-driver"
export TRITON_CACHE_DIR="$K3_ROOT/compile-cache/c2-sm103/triton"
export CUTE_DSL_NO_CACHE=0 FLASHINFER_CUTE_DSL_DISABLE_CACHE=0 CUDA_CACHE_DISABLE=0
export FLASHINFER_DIST_AWARE_AUTOTUNE=0
export FLASHINFER_NVFP4_4OVER6=1 FLASHINFER_NVFP4_4OVER6_E4M3_USE_256=1
export FLASHINFER_NVFP4_4OVER6_ERR_MODE=MSE
export FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH=1
export FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=1
export PYTHONWARNINGS='error:CUPTI is not installed:UserWarning'
unset FLASHINFER_DISABLE_JIT FLASHINFER_DISABLE_VERSION_CHECK
unset CUTE_DSL_DISABLE_FILE_CACHING MEGA_NO_DIST MEGA_USE_NCU CUTE_DSL_KEEP
mkdir -p "$FLASHINFER_WORKSPACE_BASE" "$CUTE_DSL_CACHE_DIR" \
  "$CUDA_CACHE_PATH" "$TRITON_CACHE_DIR"

torchrun --master-addr=127.0.0.1 --master-port=29671 --nproc-per-node=8 \
  benchmarks/bench_cute_dsl_moe_distributed.py \
  --model glm5 --mode benchmark --parallel-modes ep --num-gpus 8 \
  --variants w4a16_megamoe \
  --num-tokens 1,2,4,8,16,32,64,128,256,512,4096,8192,16384 \
  --timing cupti --cuda-graph --precomputed-routing --no-fused-finalize \
  --warmup 3 --iters 100 --log-timing-samples --megamoe-knobs auto
```

To reproduce BEFORE, use a separate checkout and cache directory, keep
this benchmark driver, restore the baseline library, then run the same
GLM5 command:

```bash
git switch --detach 866c80d0c70a90624b4c2056d12d1543d709609e
git restore --source=a7103ae2a97f38f4dbbf410c32acc7c6fe99cab1 -- flashinfer
```

The main command benchmarks the final source. `--model kimi-k3` and
`--model deepseek-v41-flash` select the other added synthetic NVFP4
fixtures. Their outer model projections and router computation are
outside this benchmark. `--no-fused-finalize` controls split
finalization; MegaMoE sets `enable_in_kernel_fc2_reduce=False` and
retains deterministic combine.

</details>

## 🔍 Related Issues

- Tracked in
[#4561](https://github.com/flashinfer-ai/flashinfer/issues/4561).
- Benchmark methodology follows
[#5019](https://github.com/flashinfer-ai/flashinfer/pull/5019).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

- **Bit-exact validation at `866c80d0`:** 17 logical cases / 52
rank-local passes, zero failures, errors or skips. The original
reference and `rtol=atol=0` are preserved.
- **N32 coverage:** eight EP2 cases cover M128/M256, static/atomic
scheduling, SwiGLU/epilogue return and SiTU/dispatch return, D288/E448
feature tails, routed counts 15/16/17, 31/32/33 and 63/64/65,
empty/refill and graph replay. Nine EP4 cases check existing activation,
scaling, routing and normalization contracts.
- **Additional model-sized exact validation:** a standalone port of this
kernel passed **104 logical cases / 624 rank-local passes**, with zero
failures, errors or skips, in **316.477s total**. GLM5/SwiGLU and Kimi
K3/SiTU(4,25), EP4/EP8, random/skewed routing, T1..4096 (all 13 powers
of two), all 16 tactics, O3/eager and FC1 top-k False. Each case
computes one finite independent reference; both launches of every tactic
match its BF16 bits exactly, including signed zero. Upstream source
remains `866c80d0c70a90624b4c2056d12d1543d709609e`.
- **Harness scope:** reuse weights, compiled code and runtime
initialization across cases. Cached compilation exposed a first-use
workspace initialization race; the harness now collectively synchronizes
after workspace zeroing, before first launch. This run qualifies the
prepared execution path, not unsynchronized first-use allocation. PDL
and deterministic combine are enabled; fused TMA/in-kernel FC2 reduction
is disabled.
- **Compute Sanitizer:** synchronized W4A16 kernels pass memcheck,
synccheck and racecheck on B300 EP4/EP8 across all 16 tactics (eight
N32), both random/skewed routing patterns, with **36 clean rank logs and
zero selected pytest skips**. Memcheck/synccheck cover T1/T128/T1024;
racecheck covers **T1 only**. The existing memcheck `--check-tensor-ops
no` exclusion remains for the 2026.3 legal two-CTA TMA false positive.
This earlier sanitizer qualification is separate from the new
numerical-harness run.
- **Static validation:** focused pre-commit, commit hooks, Python syntax
compilation and `git diff --check` passed. The full repository suite and
all-files pre-commit were not run. Kernel validation does not establish
full-model checkpoint accuracy.

<details>
<summary>Bit-exact test commands and complete rank summaries</summary>

Use the pinned source and runtime above. The groups run serially; each
rank writes its own JUnit report.

```bash
set -euo pipefail
export PYTHONPATH="$PWD" PYTHONDONTWRITEBYTECODE=1 PYTHONNOUSERSITE=1
export PYTHONUNBUFFERED=1 PYTEST_DISABLE_PLUGIN_AUTOLOAD=1 PYTEST_ADDOPTS=''
export OMP_NUM_THREADS=1 CUDA_VISIBLE_DEVICES=0,1,2,3,4,5,6,7
unset RANK WORLD_SIZE LOCAL_RANK LOCAL_WORLD_SIZE GROUP_RANK ROLE_RANK
unset MASTER_ADDR MASTER_PORT MEGA_NO_DIST MEGA_SINGLE_GPU_GLOO MEGA_USE_NCU
unset CUTE_DSL_DUMP_DIR CUTE_DSL_KEEP_PTX CUTE_DSL_KEEP_CUBIN
export FLASHINFER_DIST_AWARE_AUTOTUNE=0
export FLASHINFER_NVFP4_4OVER6=1 FLASHINFER_NVFP4_4OVER6_E4M3_USE_256=1
export FLASHINFER_NVFP4_4OVER6_ERR_MODE=MSE
export FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH=1
export FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=1
export CUDA_CACHE_DISABLE=0 CUTE_DSL_NO_CACHE=0 FLASHINFER_CUTE_DSL_DISABLE_CACHE=0
export N32_EXACT_OUT="$K3_ROOT/exact-866c-results"
mkdir "$N32_EXACT_OUT"
export FLASHINFER_WORKSPACE_BASE="$N32_EXACT_OUT/cache/flashinfer"
export CUTE_DSL_CACHE_DIR="$N32_EXACT_OUT/cache/cute"
export CUDA_CACHE_PATH="$N32_EXACT_OUT/cache/cuda"
export TRITON_CACHE_DIR="$N32_EXACT_OUT/cache/triton"
mkdir -p "$FLASHINFER_WORKSPACE_BASE" "$CUTE_DSL_CACHE_DIR" \
  "$CUDA_CACHE_PATH" "$TRITON_CACHE_DIR"
export N32_TEST=tests/moe_ep/test_moe_ep_nvfp4_cutedsl_mega_multirank.py
run_exact() {
  local label="$1" ep="$2" port="$3"
  export N32_NODE="$4" N32_SELECT="$5" N32_CASE_OUT="$N32_EXACT_OUT/$label"
  mkdir "$N32_CASE_OUT"
  python3 -m torch.distributed.run --nnodes=1 --nproc-per-node="$ep" \
    --master-addr=127.0.0.1 --master-port="$port" --max-restarts=0 \
    --no-python bash -c '
      exec python3 -m pytest "$N32_NODE" -k "$N32_SELECT" \
        -q -ra -x -p no:cacheprovider --confcutdir=tests/moe_ep \
        --junitxml="$N32_CASE_OUT/rank-$RANK.xml"
    ' 2>&1 | tee "$N32_CASE_OUT/launcher.log"
}
run_exact ep2-n32 2 29711 \
  "$N32_TEST::test_nvfp4_mega_uneven_sources_and_empty_refill" n32
run_exact ep4-epilogue 4 29712 \
  "$N32_TEST::test_nvfp4_w4a16_epilogue_contract" 'not n32'
```

```text
EP2 N32 — two ranks:
8 passed, 14 deselected, 705 warnings in 212.28s (0:03:32)
8 passed, 14 deselected, 705 warnings in 212.28s (0:03:32)
EP4 original epilogue contract — four ranks:
9 passed, 789 warnings in 171.66s (0:02:51)
9 passed, 789 warnings in 171.69s (0:02:51)
9 passed, 789 warnings in 171.69s (0:02:51)
9 passed, 789 warnings in 171.77s (0:02:51)
```

All six JUnit reports were independently checked for the expected case
sets and zero failures, errors or skips. Rank-local passes are
cooperating participants, not additional independent logical tests.

</details>

<details>
<summary>Supplemental model-sized exact suite: complete rank
summaries</summary>

Eight B300 SXM6 AC GPUs, serial EP4/EP8 groups,
`nvcr.io/nvidia/pytorch:26.05-py3`, CUDA 13.2.1, driver `590.48.01`,
Python 3.12.3, PyTorch `2.12.0a0+5aff3928d8.nv26.5.50603568`, CuTe DSL
4.7.1, NVSHMEM 3.6.5 / nvshmem4py 0.3.1 and pytest 8.4.2. GLM5
`(D,E,N,K)=(6144,2048,256,8)`; Kimi K3 routed latent shape
`(3584,3072,896,16)`. Fixed capacity is 1,024 tokens/rank at EP4 and 512
at EP8. These are supplemental standalone checks, separate from the
upstream pytest cases above.

```text
EP4 rank 0: 52 passed, 692 warnings in 132.49s (0:02:12)
EP4 rank 1: 52 passed, 692 warnings in 132.53s (0:02:12)
EP4 rank 2: 52 passed, 692 warnings in 132.49s (0:02:12)
EP4 rank 3: 52 passed, 692 warnings in 132.49s (0:02:12)
EP8 rank 0: 52 passed, 692 warnings in 149.25s (0:02:29)
EP8 rank 1: 52 passed, 692 warnings in 149.32s (0:02:29)
EP8 rank 2: 52 passed, 692 warnings in 149.38s (0:02:29)
EP8 rank 3: 52 passed, 692 warnings in 149.34s (0:02:29)
EP8 rank 4: 52 passed, 692 warnings in 149.30s (0:02:29)
EP8 rank 5: 52 passed, 692 warnings in 149.28s (0:02:29)
EP8 rank 6: 52 passed, 692 warnings in 149.09s (0:02:29)
EP8 rank 7: 52 passed, 692 warnings in 149.29s (0:02:29)

Independent audit: PASS
104 unique logical cases; 624 rank-local passes; 0 failures/errors/skips
16 tactics/case; 3,328 logical reference-bit comparisons
12 rank-local JUnit files; 0 duplicate cases; no earlier results counted
Sealed standalone source and runtime verified before/after execution
EP4 pytest max: 132.53s; EP8 pytest max: 149.38s
Total supervisor wall time: 316.477s (startup, collection and teardown included)
```

Every selected case passed on every participating rank; rank-local
passes are cooperating participants, not additional independent logical
cases. No partial result from earlier stopped runs is included. This is
kernel numerical coverage, not a full-model accuracy claim.

</details>

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

The change extends tile geometry and autotuning without changing
activation numerics. The table includes all measured token counts and
regressions; no K3/DeepSeek BEFORE-versus-final speedup is claimed.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Expanded routed MoE benchmark options to cover additional model
configurations and routing behaviors.
* Added support for 32-token tiles in BF16/NVFP4 MegaMoE processing,
including additional tile configurations.
* **Bug Fixes**
* Improved handling of routing boundaries, input scaling, and varied
tile configurations in multi-rank tests.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [649eb10](https://github.com/flashinfer-ai/flashinfer/commit/649eb1060905ff26e0b9446420435c632c1aa735)

- **作者**: eigen
- **时间**: 2026-10-14T21:42:56Z
- **提交信息**: feat(cake_quant_lora_gemm): fused NVFP4 / FP8 GEMM with a runtime BF16 LoRA correction (mm_nvfp4_lora, mm_fp8_lora) (#6324)

Developed by the **CAKE team**. FlashInfer's existing fused low-rank
path, `mm_nvfp4_svdquant`, computes `alpha * (A @ W^T + D @ l1^T) +
bias` and needs the LoRA-up weight pre-divided by `alpha` offline (a
fold that re-rounds it to bf16); it has no SM90 or FP8 variant. This PR
adds a sibling, not a replacement: the adapter is read as given at run
time with its own `lora_scale`, for NVFP4 and FP8 bases. The per-shape
tables below compare the generated programs loaded through FlashInfer
against the Cake production launcher of the same kernels (the export's
source arm) on real devices; they are not a comparison against other
libraries.

## Update 2026-10-12 — R2-opt re-export (Cake
`6808d3494681c5bd2d373af6301fd01c54ed9dfb`, export protocol p7)

This revision re-exports the family from Cake
`6808d3494681c5bd2d373af6301fd01c54ed9dfb` after an optimization round
on every performance row whose
fastest-baseline / candidate ratio was below 1.00, and rebases the
branch onto upstream `main`
(`f63b2e7cbfb9a008a3880ebf00f2bbf3721176fe`).
Everything is schedule-only: the kernel math, tolerances, fp32
accumulation and the per-row denominator are unchanged.

* **New programs.** NVFP4: a 256 x 192 pair tile
(`nvfp4_blackwell_n192`) and its L2-hinted variant
(`nvfp4_blackwell_n192h`),
selected per problem by the ported shape rule (`PROGRAMS` /
`select_template`), plus a drain-compacted pair epilogue.
FP8 Blackwell: a CLC dynamic-tile-scheduler + 2-D blocked-raster program
(`fp8_blackwell_n256_clc_blocked`, SM100/SM103,
selected for tiles >= 10 and K >= 16384) and, on SM103 only, its
256-row-tile composition
(`fp8_blackwell_n256_m256_clc_blocked`, bound to the same gated point).
SM90: the raster-group-4 + TMA-cache-hint form
  (`fp8_sm90_hint`) for the M = 131072 down projections.
* **Shared device helpers.** `csrc/cake_device_helpers/` files already
present on `main` (delivered by the Cake DeepGEMM
family) are kept byte-for-byte; the exporter's retention rule requires
token-equivalence with this family's rendering,
which was verified on the final tree (6 retained helpers, all equal).
Six helpers are new.
* **Export protocol p7.** 663 routes (SM90 131, SM100 265, SM103 267).
The two measurement-stability metrics
(`endpoint_drift`, `directional_disagreement`) are disclosed per row
below instead of gating a row (the loaded SM clock
under the power cap wanders between the two endpoints of a timed
window); correctness gates and
  `source / export >= 0.97` are unchanged and every row passes them.
* **Final-tree validation.** Rebased tree: pre-commit (clang-format,
mypy, ruff) clean, `tests/gemm/test_cake_quant_lora_gemm.py`
collected (125 tests); the record passes below ran the same module on
each device (FI tests: SM90 116 passed / 4 skipped, SM100 121 / 4, SM103
121 / 4).
  Branch head `e7e6b7d0b1fce80d8dfaad0c63437a8879f0a4e0`.
* **Performance honesty (kernel-only, same-session paired timing against
the fastest admitted baseline arm, 62
performance rows per family and architecture, judged on the worse of two
B200 nodes or RUN + same-node RERUN).**
Rows above 1.00: NVFP4 SM100 17, FP8 SM100 38, FP8 SM103 47, NVFP4 SM103
11,
FP8 SM90 37 of 62. The residual rows split into a power-cap class
(equal-clock ratio above 1, the
candidate arm runs 60-420 MHz below the baseline arm) and a cycle-bound
class (FP8 down projections with large K on
SM90 and the small-M FP8 down rows on SM103; most NVFP4 SM100 rows
against `mm_nvfp4_svdquant`'s CUTLASS kernel).
  No tolerance, denominator or protocol was changed to improve a number.

## Summary

This PR adds a fused **quantized-base GEMM with a runtime BF16 LoRA
correction** as Cake-generated programs:

```
out = alpha * (dequant(a) @ dequant(b)^T) + lora_scale * (d @ lora_b^T) [+ bias]      (bf16 out)
```

| operator | base operands | architectures |
| --- | --- | --- |
| `flashinfer.mm_nvfp4_lora(a, b, a_sf, b_sf, alpha, d, lora_b,
lora_scale, *, bias=None, out=None, backend="cake")` | NVFP4: E2M1 codes
packed two per byte, UE4M3 block scales (16 along K) in the 128x4
swizzled layout of `fp4_quantize` / `mm_fp4`; `alpha` = fp32 device
scalar `alpha_base / (a_global * b_global)` | SM100 (B200), SM103 (B300)
|
| `flashinfer.mm_fp8_lora(a, b, a_scale, b_scale, d, lora_b, lora_scale,
*, bias=None, out=None, backend="cake")` | FP8 E4M3 `[M, K]` / `[N, K]`
with per-tensor fp32 scales | SM90 (H100), SM100, SM103 |

The LoRA factors are consumed **as given**: `d` (the LoRA-down output `x
@ A^T`, `bf16 [M, r]`) and `lora_b` (the
LoRA-up weight, `bf16 [N, r]`) are never re-rounded, pre-scaled or
folded into the base weights; the correction is
accumulated in fp32 inside the same kernel and the result is rounded
once to bf16. `alpha` and `lora_scale` are
independent fp32 device scalars, so adapters and scales can change per
call without touching the quantized weights.

Motivation: #6303 (serving quantized base weights with per-request LoRA
adapters). The unfused chain -- base GEMM
(`mm_fp4` / cuBLASLt FP8), a BF16 `addmm_` for the correction and a bias
add -- costs an extra pass over the
`[M, N]` output and a second kernel per layer; this fuses it into the
base GEMM's epilogue.

## Semantics and limits

* Ranks: `r = d.shape[1] = lora_b.shape[1]` in `{32, 64, 128}`; other
ranks raise `ValueError`.
* Shape rules (violations raise `ValueError` naming the requirement):
NVFP4 `M >= 1`, `N >= 1`, `K % 256 == 0`;
FP8 on SM100/SM103 `N % 8 == 0`, `K % 128 == 0`; FP8 on SM90 `N % 8 ==
0`, `K % 16 == 0`, `M * N <= 2**32`.
* `lora_scale` is a one-element fp32 device tensor. `0` and `None` both
take the zero-adapter fast path (no LoRA
work, bitwise identical to each other and to a call without adapter).
**`lora_scale=None` disables the adapter
even if `d` / `lora_b` are passed; pass a device scalar to apply it.**
`d` and `lora_b` must be given together
  or both be `None`.
* `lora_scale` must be a normal fp32 value or `±0` (`-0.0` takes the
zero-adapter fast path, bitwise identical to
`0`); denormal (subnormal) scales are out of contract and unsupported
(the scale lives on the device, so this is
  documented, not checked at call time).
* `bias` (`bf16 [N]`) is added in fp32 before the single rounding. `out`
is caller-owned bf16 `[M, N]` or allocated.
* Only `out_dtype=torch.bfloat16`; the programs are built with
programmatic dependent launch (`enable_pdl` `None` /
`True`). `backend` accepts `"cake"` (default) or `"auto"`; the generated
programs are the only implementation.
  SM120 / SM121 are not supported (tcgen05 / TMEM programs).
* Tensor parallelism (host contract): column-parallel (`N`-sharded)
ranks each hold their `N` shard of
`b` / scales / `lora_b` / `bias` and the full `d`, and each adds its own
correction; row-parallel (`K`-sharded)
ranks hold their `K` shard of `a` / `b`, the full `d` and the full
`lora_b`, and only the owner rank passes
`lora_scale` / `bias` (the others pass `lora_scale = 0`, `bias = None`)
so the correction is counted exactly once
  before the all-reduce of the base partials.
* CUDA graphs: a captured call keeps the adapter *pointers*; swap
adapters by `copy_` into the captured tensors.

## Mixed-precision implementation (the issue's "explain any
alternative")

Tensor-core MMAs carry no per-instruction fp32 scale, so `alpha` and
`lora_scale` need one of three forms:

| form | mechanism | precision | cost | shipped |
| --- | --- | --- | --- | --- |
| (i) second accumulator | base MMA into `acc1`, LoRA MMA into `acc2`,
epilogue `alpha * acc1 + lora_scale * acc2 (+ bias)` in fp32 | exact:
two fp32 products and one fp32 add | a second accumulator: the shipped
2-CTA 256 x 128 pair program uses all 512 TMEM columns (the 1-CTA 128 x
128 variant 416 of 512); it does not fit the 256 x 256 pair tile;
register accumulators on SM90 | NVFP4 256 x 128 pair program; FP8 SM90 |
| (ii) same accumulator, in-place rescale | after the base K loop the
fp32 accumulator is multiplied by `alpha / lora_scale`, the LoRA MMA
accumulates into it, the epilogue multiplies by `lora_scale` |
fp32-only, no operand re-rounding; one extra fp32 rounding of the ratio
and of the rescaled partial; requires `lora_scale` normal or +-0 (see
limits) | one TMEM / register round trip over the tile (TMEM 288 of 512
columns) | NVFP4 256 x 256 program; FP8 SM100 / SM103 (256- and 128-wide
N tiles) |
| (iii) pre-scaled operands | fold `lora_scale / alpha` into `d` or
`lora_b` before the MMA | re-rounds an operand to bf16 | - | rejected
(analysis only) |

Both (i) and (ii) were implemented from one template per kernel
(identical base path) and compared on the same rows: SQNR against the
fp32 product of the dequantized operands agrees to 0.01 dB (about 55.6
dB on the evaluation rows), the fraction of outputs more than one bf16
ulp from `bf16(ref)` is at most 6.0e-6 (NVFP4) and 5.0e-5 (FP8, measured
on SM100) for both, and `lora_scale = 0` is bitwise equal to the
no-adapter call under both. The faster form that meets the tolerances
ships per program: for NVFP4 the host chooses between the pair program
(form (i)) and the 256-wide program (form (ii), the only form that fits
its accumulator in TMEM) by shape (`K < 8192` or `M <= 4096 and N <=
4096 and K >= 16384` -> pair, otherwise 256-wide); FP8 on SM100 / SM103
ships form (ii), which was never slower and faster on the long rows in
paired timing; FP8 on SM90 ships form (i). The SM90 FP8 program keeps
the Hopper WGMMA accumulator and promotes it to fp32 every four K blocks
(128 x 192 x 128 tile, 5 stages). The NVFP4 programs are compiled with
`--use_fast_math` (the project default): their outputs were bitwise
identical with and without the flag on every frozen test cell; its
remaining effect is flush-to-zero on denormal `lora_scale` values, which
the contract excludes.

## What is generated

One program family `csrc/cake_quant_lora_gemm` with ten `template <int
RANK>` programs: NVFP4 on `cta_group::2` pair
tiles of 256 x 128 (`nvfp4_blackwell_pair`), 256 x 192
(`nvfp4_blackwell_n192`, and `nvfp4_blackwell_n192h` with L2
cache hints) and 256 x 256 (`nvfp4_blackwell_n256`), chosen per problem
by the shape rule ported into the host; FP8
Blackwell with 128-wide (`fp8_blackwell_n128`) and 256-wide
(`fp8_blackwell_n256`) N tiles, the CLC-scheduled blocked-raster
program (`fp8_blackwell_n256_clc_blocked`) and, on SM103, its 256-row
composition (`fp8_blackwell_n256_m256_clc_blocked`);
and two runtime-rank SM90 programs (`fp8_sm90`, `fp8_sm90_hint`);
`flashinfer/jit/cake_quant_lora_gemm.py` (JIT loader and
the `PROGRAMS` catalog), `flashinfer/gemm/cake_quant_lora_gemm.py` (host
API, shape and dispatch rules, launch),
`tests/gemm/test_cake_quant_lora_gemm.py`,
`benchmarks/bench_cake_quant_lora_gemm.py`, `docs/api/gemm.rst`, and the
content-addressed shared device helpers under
`csrc/cake_device_helpers/`. The delivered Python files are formatted
with
the ruff version pinned by this repository's pre-commit configuration;
the generated CUDA sources carry a `.clang-format`
opt-out so their receipt-bound text is never reformatted.

## Validation

Every registered shape below was run on real devices (NVIDIA H100 80GB
HBM3 (SM90, compute capability 9.0, driver 535.216.03); NVIDIA B200
(SM100, compute capability 10.0, driver 580.82.07); NVIDIA GB300 (SM103,
compute capability 10.3, driver 580.159.03)) through the generated
programs **and** the Cake
production launcher on the same tensors, with: finite outputs; per-row
SQNR against the fp32 product of the
dequantized operands at or above the contract floor for that device
(minimum 40 dB); `max|out - ref| / max|ref| < 1 %`;
bitwise identity between the generated program and the production
launcher; LoRA-isolation rows (zero base weights)
elementwise within `atol = rtol = 1e-2` of the bf16 reference;
zero-adapter fast-path bitwise checks and base-weight
checksums; adapter-switch and CUDA-graph pointer semantics;
tensor-parallel shard simulation against the full
reference. Performance rows report the CUPTI-timed generated program
against the production launcher
(source / export >= 0.97 on every row; geometric mean source / export
over all timed rows: 0.9995 on NVIDIA H100 80GB HBM3 (131 rows), 0.9993
on NVIDIA B200 (265 rows), 1.0000 on NVIDIA GB300 (267 rows)). The FP8
`coverage` rows (M = 129, reaching the 128-wide tile at every rank, and
the SM103 composition's
coverage rows) are timed like every row but are not performance rows and
carry no performance claim.

The evidence tables that follow are generated from the sealed run
summaries.

## Evidence per architecture (sealed export passes, protocol p7)

Source = the kernel module's production `launch`; Export =
`mm_nvfp4_lora` / `mm_fp8_lora`. Source / Export above 1 on NVFP4
performance rows comes from the host-side per-shape dispatch rule
carried in `PROGRAMS`, which the single-form production launch does not
apply.

### SM90 — NVIDIA H100 80GB HBM3 (CC 9.0, driver 535.216.03, UUID
`GPU-2632f9c3-b016-b5ab-d589-d1e8c894abf6`)

131 registered shapes for `sm_90a` (denominator 663 routes across the
three architectures); every row passed correctness and the export
protocol (verdict `pass`).

Geometric means over all timed rows (Source = Cake production launcher,
Export = loaded generated program):

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|131|663|0.904127|0.904583|0.999496x|
|fp8_adapter_switch|12|36|0.175197|0.175352|0.999117x|
|fp8_correctness|16|48|0.443238|0.443533|0.999335x|
|fp8_coverage|3|17|0.021258|0.021268|0.999521x|
|fp8_lora_isolation|16|48|0.410378|0.410515|0.999666x|
|fp8_perf|62|186|2.854557|2.855611|0.999631x|
|fp8_tp_sim|6|18|0.427761|0.428022|0.999391x|
|fp8_zero_adapter|16|48|0.432353|0.432664|0.999282x|

Loaded SM clock disclosure (disclosed, not gated;
`min_sm_clock_fraction` = None in p7): median loaded SM clock fraction
0.992 of the rated maximum over 131 timed rows; power-cap events not
recorded in the p7 receipts (no power / throttle key in
`clock_evidence`).

Window-stability disclosure (per row, not gated; p7 limits 0.99):
endpoint drift p50 0.0033 / p90 0.0247 / max 0.0530; directional
disagreement max 0.0210; 19 of 131 rows exceed the former 0.02 limit on
at least one metric (19 drift, 1 directional); source / export minimum
0.9971.

|shape|endpoint drift|directional disagreement|source / export|
|---|---:|---:|---:|

|fp8_correctness_h6144_down_m4097_r64_b1_a0p37_s2p5_seed0|0.0247|0.0009|0.9997|

|fp8_correctness_h8192_down_m4097_r64_b1_a0p37_s2p5_seed0|0.0265|0.0006|0.9995|

|fp8_correctness_h8192_qkv_m4097_r64_b1_a0p37_s2p5_seed0|0.0327|0.0007|1.0005|
|fp8_perf_h3072_out_m131072_r64|0.0292|0.0003|0.9996|
|fp8_perf_h3072_qkv_m131072_r64|0.0273|0.0003|0.9998|
|fp8_perf_h3072_up_m131072_r64|0.0288|0.0001|0.9991|
|fp8_perf_h3072_up_m32768_r64|0.0366|0.0003|0.9997|
|fp8_perf_h4096_out_m131072_r64|0.0263|0.0003|0.9996|
|fp8_perf_h4096_qkv_m32768_r64|0.0218|0.0002|0.9994|
|fp8_perf_h4096_up_m32768_r64|0.0247|0.0001|1.0000|
|fp8_perf_h6144_down_m131072_r64|0.0530|0.0210|0.9980|
|fp8_perf_h6144_out_m32768_r64|0.0259|0.0003|0.9971|
|fp8_perf_h6144_up_m32768_r64|0.0225|0.0003|0.9999|
|fp8_perf_h8192_down_m4096_r64|0.0255|0.0006|0.9990|
|fp8_perf_h8192_qkv_m4096_r64|0.0217|0.0006|0.9997|
|fp8_perf_h8192_up_m32768_r64_tp4c|0.0224|0.0006|1.0002|
|fp8_perf_h8192_up_m32768_r64_tp8c|0.0259|0.0004|0.9996|
|fp8_perf_h8192_up_m4096_r64|0.0398|0.0004|0.9989|

|fp8_zero_adapter_h8192_down_m4097_r64_b1_a0p37_s2p5_seed0|0.0221|0.0004|1.0007|

Non-performance rows (69: correctness, LoRA-isolation, adapter-switch
and coverage tags) all pass and are summarized by the geomeans table
above; their per-row values are in the sealed summary (sha256 in the
Cake record).

<details><summary>Performance rows (62 of 131 registered shapes; names
omit `__sm_90a`; ms rounded to 5 decimals)</summary>

|shape|src ms|exp ms|src/exp|
|---|---:|---:|---:|
|fp8_perf_h3072_qkv_m4096_r64|0.18448|0.18474|0.9986|
|fp8_perf_h3072_qkv_m32768_r64|1.56298|1.56347|0.9997|
|fp8_perf_h3072_qkv_m131072_r64|6.55773|6.55923|0.9998|
|fp8_perf_h3072_out_m4096_r64|0.06352|0.06362|0.9985|
|fp8_perf_h3072_out_m32768_r64|0.47706|0.47750|0.9991|
|fp8_perf_h3072_out_m131072_r64|2.11413|2.11501|0.9996|
|fp8_perf_h3072_up_m4096_r64|0.24352|0.24374|0.9991|
|fp8_perf_h3072_up_m32768_r64|2.10320|2.10378|0.9997|
|fp8_perf_h3072_up_m131072_r64|8.91108|8.91916|0.9991|
|fp8_perf_h3072_down_m4096_r64|0.21494|0.21530|0.9984|
|fp8_perf_h3072_down_m32768_r64|1.96107|1.96128|0.9999|
|fp8_perf_h3072_down_m131072_r64|8.00548|8.00474|1.0001|
|fp8_perf_h4096_qkv_m4096_r64|0.31037|0.31056|0.9994|
|fp8_perf_h4096_qkv_m32768_r64|2.76407|2.76576|0.9994|
|fp8_perf_h4096_qkv_m131072_r64|11.38214|11.38472|0.9998|
|fp8_perf_h4096_out_m4096_r64|0.12134|0.12150|0.9987|
|fp8_perf_h4096_out_m32768_r64|0.87855|0.87958|0.9988|
|fp8_perf_h4096_out_m131072_r64|3.81498|3.81650|0.9996|
|fp8_perf_h4096_up_m4096_r64|0.40803|0.40829|0.9994|
|fp8_perf_h4096_up_m32768_r64|3.71889|3.71904|1.0000|
|fp8_perf_h4096_up_m131072_r64|15.34850|15.34951|0.9999|
|fp8_perf_h4096_down_m4096_r64|0.42048|0.42067|0.9995|
|fp8_perf_h4096_down_m32768_r64|3.54391|3.54436|0.9999|
|fp8_perf_h4096_down_m131072_r64|14.43567|14.43674|0.9999|
|fp8_perf_h6144_qkv_m4096_r64|0.68701|0.68771|0.9990|
|fp8_perf_h6144_qkv_m32768_r64|6.11201|6.11210|1.0000|
|fp8_perf_h6144_qkv_m131072_r64|25.06373|25.02110|1.0017|
|fp8_perf_h6144_out_m4096_r64|0.22518|0.22551|0.9986|
|fp8_perf_h6144_out_m32768_r64|1.99735|2.00323|0.9971|
|fp8_perf_h6144_out_m131072_r64|8.23751|8.23785|1.0000|
|fp8_perf_h6144_up_m4096_r64|0.93415|0.93482|0.9993|
|fp8_perf_h6144_up_m32768_r64|8.15635|8.15719|0.9999|
|fp8_perf_h6144_up_m131072_r64|33.63929|33.64436|0.9998|
|fp8_perf_h6144_down_m4096_r64|0.89499|0.89621|0.9986|
|fp8_perf_h6144_down_m32768_r64|7.81027|7.81063|1.0000|
|fp8_perf_h6144_down_m131072_r64|38.25518|38.33340|0.9980|
|fp8_perf_h8192_qkv_m4096_r64|1.27141|1.27174|0.9997|
|fp8_perf_h8192_qkv_m32768_r64|10.79383|10.79668|0.9997|
|fp8_perf_h8192_qkv_m131072_r64|44.32953|44.43957|0.9975|
|fp8_perf_h8192_out_m4096_r64|0.40243|0.40256|0.9997|
|fp8_perf_h8192_out_m32768_r64|3.56802|3.56727|1.0002|
|fp8_perf_h8192_out_m131072_r64|14.56423|14.55540|1.0006|
|fp8_perf_h8192_up_m4096_r64|1.74975|1.75170|0.9989|
|fp8_perf_h8192_up_m32768_r64|14.40642|14.39613|1.0007|
|fp8_perf_h8192_up_m131072_r64|59.55179|59.59689|0.9992|
|fp8_perf_h8192_down_m4096_r64|1.71488|1.71659|0.9990|
|fp8_perf_h8192_down_m32768_r64|13.94684|13.94613|1.0001|
|fp8_perf_h8192_down_m131072_r64|64.81789|64.67521|1.0022|
|fp8_perf_h3072_out_m32768_r32|0.47101|0.47123|0.9995|
|fp8_perf_h3072_out_m32768_r128|0.49325|0.49363|0.9992|
|fp8_perf_h3072_up_m32768_r32|2.07555|2.07050|1.0024|
|fp8_perf_h3072_up_m32768_r128|2.17424|2.17219|1.0009|
|fp8_perf_h8192_out_m32768_r32|3.55552|3.55599|0.9999|
|fp8_perf_h8192_out_m32768_r128|3.62639|3.62703|0.9998|
|fp8_perf_h8192_up_m32768_r32|14.36936|14.36968|1.0000|
|fp8_perf_h8192_up_m32768_r128|14.80517|14.80253|1.0002|
|fp8_perf_h8192_up_m32768_r64_tp2c|7.17804|7.17990|0.9997|
|fp8_perf_h8192_down_m32768_r64_tp2r|6.99502|6.99217|1.0004|
|fp8_perf_h8192_up_m32768_r64_tp4c|3.57252|3.57170|1.0002|
|fp8_perf_h8192_down_m32768_r64_tp4r|3.56535|3.56445|1.0003|
|fp8_perf_h8192_up_m32768_r64_tp8c|1.79874|1.79952|0.9996|
|fp8_perf_h8192_down_m32768_r64_tp8r|1.80267|1.80298|0.9998|

</details>

### SM100 — NVIDIA B200 (CC 10.0, driver 580.82.07, UUID
`GPU-cbb12a7b-7da6-476d-4fec-c64a0f8e3442`)

265 registered shapes for `sm_100a` (denominator 663 routes across the
three architectures); every row passed correctness and the export
protocol (verdict `pass`).

Geometric means over all timed rows (Source = Cake production launcher,
Export = loaded generated program):

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|265|663|0.298311|0.298513|0.999326x|
|fp8_adapter_switch|12|36|0.076214|0.076215|0.999999x|
|fp8_correctness|16|48|0.189528|0.189574|0.999760x|
|fp8_coverage|6|17|0.089247|0.089333|0.999040x|
|fp8_lora_isolation|16|48|0.161889|0.161982|0.999426x|
|fp8_perf|62|186|1.218358|1.219131|0.999366x|
|fp8_tp_sim|6|18|0.186623|0.186641|0.999905x|
|fp8_zero_adapter|16|48|0.184320|0.184368|0.999739x|
|nvfp4_adapter_switch|12|24|0.049095|0.049122|0.999457x|
|nvfp4_correctness|16|32|0.109555|0.109612|0.999480x|
|nvfp4_coverage|3|6|0.018129|0.018134|0.999765x|
|nvfp4_lora_isolation|16|32|0.102621|0.102712|0.999116x|
|nvfp4_perf|62|124|0.668645|0.669429|0.998829x|
|nvfp4_tp_sim|6|12|0.105922|0.106003|0.999237x|
|nvfp4_zero_adapter|16|32|0.104752|0.104811|0.999441x|

Loaded SM clock disclosure (disclosed, not gated;
`min_sm_clock_fraction` = None in p7): median loaded SM clock fraction
1.000 of the rated maximum over 265 timed rows; power-cap events not
recorded in the p7 receipts (no power / throttle key in
`clock_evidence`).

Window-stability disclosure (per row, not gated; p7 limits 0.99):
endpoint drift p50 0.0009 / p90 0.0133 / max 0.0356; directional
disagreement max 0.0285; 19 of 265 rows exceed the former 0.02 limit on
at least one metric (16 drift, 3 directional); source / export minimum
0.9928.

|shape|endpoint drift|directional disagreement|source / export|
|---|---:|---:|---:|

|fp8_coverage_h3072_out_m129_r128_b1_a0p37_s2p5_seed0|0.0001|0.0285|0.9999|

|fp8_coverage_h3072_out_m129_r32_b1_a0p37_s2p5_seed0|0.0000|0.0234|0.9967|
|fp8_perf_h4096_down_m131072_r64|0.0239|0.0004|0.9996|
|fp8_perf_h4096_up_m131072_r64|0.0216|0.0000|1.0072|
|fp8_perf_h6144_up_m32768_r64|0.0356|0.0008|0.9989|
|fp8_perf_h8192_down_m32768_r64_tp2r|0.0355|0.0006|0.9991|
|fp8_perf_h8192_down_m32768_r64_tp4r|0.0203|0.0009|0.9990|
|fp8_perf_h8192_out_m32768_r64|0.0274|0.0009|0.9991|
|fp8_perf_h8192_up_m32768_r128|0.0246|0.0004|0.9979|
|fp8_perf_h8192_up_m32768_r32|0.0264|0.0002|0.9931|
|nvfp4_perf_h6144_down_m32768_r64|0.0300|0.0015|0.9928|
|nvfp4_perf_h6144_qkv_m32768_r64|0.0235|0.0008|0.9977|
|nvfp4_perf_h6144_up_m32768_r64|0.0236|0.0009|0.9953|
|nvfp4_perf_h8192_down_m32768_r64|0.0355|0.0012|0.9953|
|nvfp4_perf_h8192_qkv_m32768_r64|0.0266|0.0006|0.9979|
|nvfp4_perf_h8192_up_m32768_r128|0.0272|0.0004|0.9984|
|nvfp4_perf_h8192_up_m32768_r32|0.0283|0.0003|0.9986|
|nvfp4_perf_h8192_up_m32768_r64_tp2c|0.0355|0.0011|0.9973|

|nvfp4_zero_adapter_h3072_out_m4097_r64_b1_a0p37_s2p5_seed0|0.0008|0.0224|1.0000|

Non-performance rows (141: correctness, LoRA-isolation, adapter-switch
and coverage tags) all pass and are summarized by the geomeans table
above; their per-row values are in the sealed summary (sha256 in the
Cake record).

<details><summary>Performance rows (124 of 265 registered shapes; names
omit `__sm_100a`; ms rounded to 5 decimals)</summary>

|shape|src ms|exp ms|src/exp|
|---|---:|---:|---:|
|nvfp4_perf_h3072_qkv_m4096_r64|0.05248|0.05251|0.9994|
|nvfp4_perf_h3072_qkv_m32768_r64|0.36931|0.36957|0.9993|
|nvfp4_perf_h3072_qkv_m131072_r64|1.55258|1.55348|0.9994|
|nvfp4_perf_h3072_out_m4096_r64|0.02173|0.02176|0.9985|
|nvfp4_perf_h3072_out_m32768_r64|0.11846|0.11856|0.9992|
|nvfp4_perf_h3072_out_m131072_r64|0.50352|0.50379|0.9995|
|nvfp4_perf_h3072_up_m4096_r64|0.06656|0.06659|0.9995|
|nvfp4_perf_h3072_up_m32768_r64|0.51763|0.51779|0.9997|
|nvfp4_perf_h3072_up_m131072_r64|2.13282|2.13473|0.9991|
|nvfp4_perf_h3072_down_m4096_r64|0.06038|0.06042|0.9995|
|nvfp4_perf_h3072_down_m32768_r64|0.41280|0.41309|0.9993|
|nvfp4_perf_h3072_down_m131072_r64|1.75879|1.76556|0.9962|
|nvfp4_perf_h4096_qkv_m4096_r64|0.08493|0.08502|0.9989|
|nvfp4_perf_h4096_qkv_m32768_r64|0.66499|0.66547|0.9993|
|nvfp4_perf_h4096_qkv_m131072_r64|2.74500|2.74506|1.0000|
|nvfp4_perf_h4096_out_m4096_r64|0.03235|0.03235|1.0000|
|nvfp4_perf_h4096_out_m32768_r64|0.20720|0.20733|0.9994|
|nvfp4_perf_h4096_out_m131072_r64|0.87901|0.87972|0.9992|
|nvfp4_perf_h4096_up_m4096_r64|0.11235|0.11245|0.9991|
|nvfp4_perf_h4096_up_m32768_r64|0.88263|0.88327|0.9993|
|nvfp4_perf_h4096_up_m131072_r64|3.63800|3.63860|0.9998|
|nvfp4_perf_h4096_down_m4096_r64|0.09834|0.09846|0.9987|
|nvfp4_perf_h4096_down_m32768_r64|0.74579|0.74701|0.9984|
|nvfp4_perf_h4096_down_m131072_r64|3.22574|3.23183|0.9981|
|nvfp4_perf_h6144_qkv_m4096_r64|0.16186|0.16192|0.9996|
|nvfp4_perf_h6144_qkv_m32768_r64|1.41961|1.42288|0.9977|
|nvfp4_perf_h6144_qkv_m131072_r64|5.82213|5.82429|0.9996|
|nvfp4_perf_h6144_out_m4096_r64|0.05853|0.05856|0.9995|
|nvfp4_perf_h6144_out_m32768_r64|0.44813|0.44827|0.9997|
|nvfp4_perf_h6144_out_m131072_r64|1.88321|1.88666|0.9982|
|nvfp4_perf_h6144_up_m4096_r64|0.21591|0.21603|0.9994|
|nvfp4_perf_h6144_up_m32768_r64|1.89127|1.90029|0.9953|
|nvfp4_perf_h6144_up_m131072_r64|7.71801|7.72025|0.9997|
|nvfp4_perf_h6144_down_m4096_r64|0.21226|0.21222|1.0002|
|nvfp4_perf_h6144_down_m32768_r64|1.72348|1.73596|0.9928|
|nvfp4_perf_h6144_down_m131072_r64|7.38905|7.39561|0.9991|
|nvfp4_perf_h8192_qkv_m4096_r64|0.27450|0.27466|0.9994|
|nvfp4_perf_h8192_qkv_m32768_r64|2.45956|2.46478|0.9979|
|nvfp4_perf_h8192_qkv_m131072_r64|10.15909|10.16045|0.9999|
|nvfp4_perf_h8192_out_m4096_r64|0.09456|0.09469|0.9986|
|nvfp4_perf_h8192_out_m32768_r64|0.77671|0.77767|0.9988|
|nvfp4_perf_h8192_out_m131072_r64|3.31385|3.31828|0.9987|
|nvfp4_perf_h8192_up_m4096_r64|0.37255|0.37283|0.9992|
|nvfp4_perf_h8192_up_m32768_r64|3.30636|3.31051|0.9987|
|nvfp4_perf_h8192_up_m131072_r64|13.50676|13.50819|0.9999|
|nvfp4_perf_h8192_down_m4096_r64|0.35226|0.35277|0.9986|
|nvfp4_perf_h8192_down_m32768_r64|3.10622|3.12083|0.9953|
|nvfp4_perf_h8192_down_m131072_r64|13.35232|13.37332|0.9984|
|nvfp4_perf_h3072_out_m32768_r32|0.11693|0.11699|0.9995|
|nvfp4_perf_h3072_out_m32768_r128|0.12579|0.12586|0.9995|
|nvfp4_perf_h3072_up_m32768_r32|0.51171|0.51191|0.9996|
|nvfp4_perf_h3072_up_m32768_r128|0.54576|0.54589|0.9998|
|nvfp4_perf_h8192_out_m32768_r32|0.76463|0.76527|0.9992|
|nvfp4_perf_h8192_out_m32768_r128|0.79536|0.79603|0.9992|
|nvfp4_perf_h8192_up_m32768_r32|3.26639|3.27092|0.9986|
|nvfp4_perf_h8192_up_m32768_r128|3.39311|3.39846|0.9984|
|nvfp4_perf_h8192_up_m32768_r64_tp2c|1.60087|1.60520|0.9973|
|nvfp4_perf_h8192_down_m32768_r64_tp2r|1.52042|1.52580|0.9965|
|nvfp4_perf_h8192_up_m32768_r64_tp4c|0.77757|0.77834|0.9990|
|nvfp4_perf_h8192_down_m32768_r64_tp4r|0.77767|0.77858|0.9988|
|nvfp4_perf_h8192_up_m32768_r64_tp8c|0.37651|0.37680|0.9992|
|nvfp4_perf_h8192_down_m32768_r64_tp8r|0.42314|0.42311|1.0001|
|fp8_perf_h3072_qkv_m4096_r64|0.07635|0.07635|1.0000|
|fp8_perf_h3072_qkv_m32768_r64|0.62653|0.62663|0.9998|
|fp8_perf_h3072_qkv_m131072_r64|2.61911|2.62103|0.9993|
|fp8_perf_h3072_out_m4096_r64|0.03261|0.03264|0.9990|
|fp8_perf_h3072_out_m32768_r64|0.19178|0.19184|0.9997|
|fp8_perf_h3072_out_m131072_r64|0.84157|0.84203|0.9994|
|fp8_perf_h3072_up_m4096_r64|0.10070|0.10074|0.9997|
|fp8_perf_h3072_up_m32768_r64|0.83930|0.83962|0.9996|
|fp8_perf_h3072_up_m131072_r64|3.53795|3.54051|0.9993|
|fp8_perf_h3072_down_m4096_r64|0.10358|0.10362|0.9997|
|fp8_perf_h3072_down_m32768_r64|0.83701|0.83820|0.9986|
|fp8_perf_h3072_down_m131072_r64|3.93675|3.94099|0.9989|
|fp8_perf_h4096_qkv_m4096_r64|0.12967|0.12973|0.9995|
|fp8_perf_h4096_qkv_m32768_r64|1.10421|1.10492|0.9994|
|fp8_perf_h4096_qkv_m131072_r64|4.85269|4.85541|0.9994|
|fp8_perf_h4096_out_m4096_r64|0.05130|0.05133|0.9994|
|fp8_perf_h4096_out_m32768_r64|0.35027|0.35040|0.9996|
|fp8_perf_h4096_out_m131072_r64|1.49047|1.49212|0.9989|
|fp8_perf_h4096_up_m4096_r64|0.16605|0.16608|0.9998|
|fp8_perf_h4096_up_m32768_r64|1.48588|1.48698|0.9993|
|fp8_perf_h4096_up_m131072_r64|6.54166|6.49502|1.0072|
|fp8_perf_h4096_down_m4096_r64|0.18112|0.18112|1.0000|
|fp8_perf_h4096_down_m32768_r64|1.44167|1.44200|0.9998|
|fp8_perf_h4096_down_m131072_r64|6.42572|6.42850|0.9996|
|fp8_perf_h6144_qkv_m4096_r64|0.28528|0.28535|0.9998|
|fp8_perf_h6144_qkv_m32768_r64|2.57001|2.57523|0.9980|
|fp8_perf_h6144_qkv_m131072_r64|11.30795|11.31670|0.9992|
|fp8_perf_h6144_out_m4096_r64|0.10416|0.10419|0.9997|
|fp8_perf_h6144_out_m32768_r64|0.81383|0.81416|0.9996|
|fp8_perf_h6144_out_m131072_r64|3.59435|3.59800|0.9990|
|fp8_perf_h6144_up_m4096_r64|0.38419|0.38438|0.9995|
|fp8_perf_h6144_up_m32768_r64|3.59190|3.59600|0.9989|
|fp8_perf_h6144_up_m131072_r64|14.98805|14.98722|1.0001|
|fp8_perf_h6144_down_m4096_r64|0.43882|0.43882|1.0000|
|fp8_perf_h6144_down_m32768_r64|3.60699|3.60969|0.9993|
|fp8_perf_h6144_down_m131072_r64|15.12343|15.15281|0.9981|
|fp8_perf_h8192_qkv_m4096_r64|0.51984|0.52010|0.9995|
|fp8_perf_h8192_qkv_m32768_r64|4.91155|4.91466|0.9994|
|fp8_perf_h8192_qkv_m131072_r64|21.44609|21.45995|0.9994|
|fp8_perf_h8192_out_m4096_r64|0.16224|0.16227|0.9998|
|fp8_perf_h8192_out_m32768_r64|1.46479|1.46613|0.9991|
|fp8_perf_h8192_out_m131072_r64|7.00409|7.00851|0.9994|
|fp8_perf_h8192_up_m4096_r64|0.70797|0.70835|0.9995|
|fp8_perf_h8192_up_m32768_r64|6.66570|6.66980|0.9994|
|fp8_perf_h8192_up_m131072_r64|28.36089|28.44849|0.9969|
|fp8_perf_h8192_down_m4096_r64|0.71909|0.71955|0.9994|
|fp8_perf_h8192_down_m32768_r64|6.69673|6.70620|0.9986|
|fp8_perf_h8192_down_m131072_r64|27.95950|27.95401|1.0002|
|fp8_perf_h3072_out_m32768_r32|0.18813|0.18816|0.9998|
|fp8_perf_h3072_out_m32768_r128|0.19847|0.19850|0.9998|
|fp8_perf_h3072_up_m32768_r32|0.82592|0.82618|0.9997|
|fp8_perf_h3072_up_m32768_r128|0.87098|0.87117|0.9998|
|fp8_perf_h8192_out_m32768_r32|1.45810|1.45858|0.9997|
|fp8_perf_h8192_out_m32768_r128|1.48367|1.48517|0.9990|
|fp8_perf_h8192_up_m32768_r32|6.68647|6.73315|0.9931|
|fp8_perf_h8192_up_m32768_r128|6.94169|6.95606|0.9979|
|fp8_perf_h8192_up_m32768_r64_tp2c|3.15448|3.15958|0.9984|
|fp8_perf_h8192_down_m32768_r64_tp2r|3.10324|3.10608|0.9991|
|fp8_perf_h8192_up_m32768_r64_tp4c|1.46256|1.46321|0.9996|
|fp8_perf_h8192_down_m32768_r64_tp4r|1.46337|1.46477|0.9990|
|fp8_perf_h8192_up_m32768_r64_tp8c|0.72375|0.72391|0.9998|
|fp8_perf_h8192_down_m32768_r64_tp8r|0.73013|0.73021|0.9999|

</details>

### SM103 — NVIDIA GB300 (CC 10.3, driver 580.159.03, UUID
`GPU-aaf51a09-a5d5-0c0b-8837-4ee22b2f3948`)

267 registered shapes for `sm_103a` (denominator 663 routes across the
three architectures); every row passed correctness and the export
protocol (verdict `pass`).

Geometric means over all timed rows (Source = Cake production launcher,
Export = loaded generated program):

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|267|663|0.266042|0.266050|0.999972x|
|fp8_adapter_switch|12|36|0.068936|0.068923|1.000187x|
|fp8_correctness|16|48|0.168915|0.168935|0.999882x|
|fp8_coverage|8|17|0.214685|0.214881|0.999089x|
|fp8_lora_isolation|16|48|0.147629|0.147652|0.999848x|
|fp8_perf|62|186|1.032039|1.032269|0.999776x|
|fp8_tp_sim|6|18|0.170704|0.170652|1.000306x|
|fp8_zero_adapter|16|48|0.164497|0.164489|1.000046x|
|nvfp4_adapter_switch|12|24|0.044460|0.044496|0.999191x|
|nvfp4_correctness|16|32|0.097980|0.097969|1.000113x|
|nvfp4_coverage|3|6|0.016709|0.016690|1.001176x|
|nvfp4_lora_isolation|16|32|0.094224|0.094253|0.999687x|
|nvfp4_perf|62|124|0.558533|0.558373|1.000286x|
|nvfp4_tp_sim|6|12|0.095539|0.095540|0.999984x|
|nvfp4_zero_adapter|16|32|0.094515|0.094486|1.000308x|

Loaded SM clock disclosure (disclosed, not gated;
`min_sm_clock_fraction` = None in p7): median loaded SM clock fraction
1.000 of the rated maximum over 267 timed rows; power-cap events not
recorded in the p7 receipts (no power / throttle key in
`clock_evidence`).

Window-stability disclosure (per row, not gated; p7 limits 0.99):
endpoint drift p50 0.0013 / p90 0.0039 / max 0.0156; directional
disagreement max 0.0333; 4 of 267 rows exceed the former 0.02 limit on
at least one metric (0 drift, 4 directional); source / export minimum
0.9965.

|shape|endpoint drift|directional disagreement|source / export|
|---|---:|---:|---:|

|fp8_coverage_h3072_out_m129_r128_b1_a0p37_s2p5_seed0|0.0033|0.0259|0.9967|

|fp8_coverage_h3072_out_m129_r32_b1_a0p37_s2p5_seed0|0.0000|0.0313|0.9965|

|fp8_coverage_h3072_out_m129_r64_b1_a0p37_s2p5_seed0|0.0033|0.0333|1.0000|

|nvfp4_coverage_h4096_out_m129_r32_b1_a0p37_s2p5_seed0|0.0018|0.0218|1.0000|

Non-performance rows (143: correctness, LoRA-isolation, adapter-switch
and coverage tags) all pass and are summarized by the geomeans table
above; their per-row values are in the sealed summary (sha256 in the
Cake record).

<details><summary>Performance rows (124 of 267 registered shapes; names
omit `__sm_103a`; ms rounded to 5 decimals)</summary>

|shape|src ms|exp ms|src/exp|
|---|---:|---:|---:|
|nvfp4_perf_h3072_qkv_m4096_r64|0.04554|0.04554|1.0000|
|nvfp4_perf_h3072_qkv_m32768_r64|0.32291|0.32262|1.0009|
|nvfp4_perf_h3072_qkv_m131072_r64|1.29581|1.29514|1.0005|
|nvfp4_perf_h3072_out_m4096_r64|0.02051|0.02054|0.9984|
|nvfp4_perf_h3072_out_m32768_r64|0.11405|0.11405|1.0000|
|nvfp4_perf_h3072_out_m131072_r64|0.44048|0.44019|1.0007|
|nvfp4_perf_h3072_up_m4096_r64|0.05952|0.05952|1.0000|
|nvfp4_perf_h3072_up_m32768_r64|0.43197|0.43168|1.0007|
|nvfp4_perf_h3072_up_m131072_r64|1.73577|1.73537|1.0002|
|nvfp4_perf_h3072_down_m4096_r64|0.05466|0.05469|0.9994|
|nvfp4_perf_h3072_down_m32768_r64|0.34663|0.34598|1.0018|
|nvfp4_perf_h3072_down_m131072_r64|1.36327|1.36312|1.0001|
|nvfp4_perf_h4096_qkv_m4096_r64|0.07443|0.07446|0.9996|
|nvfp4_perf_h4096_qkv_m32768_r64|0.54960|0.54919|1.0008|
|nvfp4_perf_h4096_qkv_m131072_r64|2.21709|2.21685|1.0001|
|nvfp4_perf_h4096_out_m4096_r64|0.02902|0.02906|0.9989|
|nvfp4_perf_h4096_out_m32768_r64|0.18502|0.18483|1.0010|
|nvfp4_perf_h4096_out_m131072_r64|0.73363|0.73309|1.0007|
|nvfp4_perf_h4096_up_m4096_r64|0.09869|0.09885|0.9984|
|nvfp4_perf_h4096_up_m32768_r64|0.74708|0.74659|1.0006|
|nvfp4_perf_h4096_up_m131072_r64|3.00449|3.00369|1.0003|
|nvfp4_perf_h4096_down_m4096_r64|0.08925|0.08938|0.9986|
|nvfp4_perf_h4096_down_m32768_r64|0.60218|0.60135|1.0014|
|nvfp4_perf_h4096_down_m131072_r64|2.46997|2.47135|0.9994|
|nvfp4_perf_h6144_qkv_m4096_r64|0.14656|0.14643|1.0009|
|nvfp4_perf_h6144_qkv_m32768_r64|1.11949|1.11877|1.0006|
|nvfp4_perf_h6144_qkv_m131072_r64|4.56473|4.56369|1.0002|
|nvfp4_perf_h6144_out_m4096_r64|0.05341|0.05341|1.0000|
|nvfp4_perf_h6144_out_m32768_r64|0.37219|0.37178|1.0011|
|nvfp4_perf_h6144_out_m131072_r64|1.48912|1.48810|1.0007|
|nvfp4_perf_h6144_up_m4096_r64|0.18941|0.18915|1.0013|
|nvfp4_perf_h6144_up_m32768_r64|1.49156|1.49092|1.0004|
|nvfp4_perf_h6144_up_m131072_r64|6.08795|6.08850|0.9999|
|nvfp4_perf_h6144_down_m4096_r64|0.19206|0.19174|1.0017|
|nvfp4_perf_h6144_down_m32768_r64|1.34504|1.34434|1.0005|
|nvfp4_perf_h6144_down_m131072_r64|5.75786|5.76150|0.9994|
|nvfp4_perf_h8192_qkv_m4096_r64|0.24256|0.24237|1.0008|
|nvfp4_perf_h8192_qkv_m32768_r64|1.88233|1.88231|1.0000|
|nvfp4_perf_h8192_qkv_m131072_r64|7.78535|7.78641|0.9999|
|nvfp4_perf_h8192_out_m4096_r64|0.08493|0.08502|0.9989|
|nvfp4_perf_h8192_out_m32768_r64|0.63136|0.63095|1.0007|
|nvfp4_perf_h8192_out_m131072_r64|2.53937|2.53998|0.9998|
|nvfp4_perf_h8192_up_m4096_r64|0.31674|0.31648|1.0008|
|nvfp4_perf_h8192_up_m32768_r64|2.52282|2.52273|1.0000|
|nvfp4_perf_h8192_up_m131072_r64|10.36824|10.36430|1.0004|
|nvfp4_perf_h8192_down_m4096_r64|0.30163|0.30122|1.0014|
|nvfp4_perf_h8192_down_m32768_r64|2.48882|2.48718|1.0007|
|nvfp4_perf_h8192_down_m131072_r64|10.53987|10.56555|0.9976|
|nvfp4_perf_h3072_out_m32768_r32|0.11587|0.11584|1.0003|
|nvfp4_perf_h3072_out_m32768_r128|0.11782|0.11782|1.0000|
|nvfp4_perf_h3072_up_m32768_r32|0.43661|0.43639|1.0005|
|nvfp4_perf_h3072_up_m32768_r128|0.45136|0.45101|1.0008|
|nvfp4_perf_h8192_out_m32768_r32|0.62394|0.62355|1.0006|
|nvfp4_perf_h8192_out_m32768_r128|0.64762|0.64714|1.0007|
|nvfp4_perf_h8192_up_m32768_r32|2.49538|2.49564|0.9999|
|nvfp4_perf_h8192_up_m32768_r128|2.58676|2.58710|0.9999|
|nvfp4_perf_h8192_up_m32768_r64_tp2c|1.25559|1.25520|1.0003|
|nvfp4_perf_h8192_down_m32768_r64_tp2r|1.18637|1.18522|1.0010|
|nvfp4_perf_h8192_up_m32768_r64_tp4c|0.63146|0.63107|1.0006|
|nvfp4_perf_h8192_down_m32768_r64_tp4r|0.63136|0.63098|1.0006|
|nvfp4_perf_h8192_up_m32768_r64_tp8c|0.31891|0.31846|1.0014|
|nvfp4_perf_h8192_down_m32768_r64_tp8r|0.36486|0.36451|1.0010|
|fp8_perf_h3072_qkv_m4096_r64|0.06845|0.06842|1.0005|
|fp8_perf_h3072_qkv_m32768_r64|0.53290|0.53267|1.0004|
|fp8_perf_h3072_qkv_m131072_r64|2.19762|2.19783|0.9999|
|fp8_perf_h3072_out_m4096_r64|0.02886|0.02886|1.0000|
|fp8_perf_h3072_out_m32768_r64|0.18048|0.18029|1.0011|
|fp8_perf_h3072_out_m131072_r64|0.71424|0.71437|0.9998|
|fp8_perf_h3072_up_m4096_r64|0.09194|0.09205|0.9988|
|fp8_perf_h3072_up_m32768_r64|0.71168|0.71168|1.0000|
|fp8_perf_h3072_up_m131072_r64|2.95265|2.95175|1.0003|
|fp8_perf_h3072_down_m4096_r64|0.09469|0.09485|0.9983|
|fp8_perf_h3072_down_m32768_r64|0.71802|0.71802|1.0000|
|fp8_perf_h3072_down_m131072_r64|3.03345|3.03484|0.9995|
|fp8_perf_h4096_qkv_m4096_r64|0.12045|0.12064|0.9984|
|fp8_perf_h4096_qkv_m32768_r64|0.93469|0.93472|1.0000|
|fp8_perf_h4096_qkv_m131072_r64|3.93148|3.93160|1.0000|
|fp8_perf_h4096_out_m4096_r64|0.04566|0.04573|0.9986|
|fp8_perf_h4096_out_m32768_r64|0.31021|0.31008|1.0004|
|fp8_perf_h4096_out_m131072_r64|1.25460|1.25463|1.0000|
|fp8_perf_h4096_up_m4096_r64|0.15543|0.15533|1.0006|
|fp8_perf_h4096_up_m32768_r64|1.25005|1.25023|0.9999|
|fp8_perf_h4096_up_m131072_r64|5.27616|5.27349|1.0005|
|fp8_perf_h4096_down_m4096_r64|0.17050|0.17051|0.9999|
|fp8_perf_h4096_down_m32768_r64|1.21517|1.21511|1.0001|
|fp8_perf_h4096_down_m131072_r64|5.20306|5.20237|1.0001|
|fp8_perf_h6144_qkv_m4096_r64|0.26109|0.26099|1.0004|
|fp8_perf_h6144_qkv_m32768_r64|2.13613|2.13817|0.9990|
|fp8_perf_h6144_qkv_m131072_r64|9.10552|9.10281|1.0003|
|fp8_perf_h6144_out_m4096_r64|0.09440|0.09443|0.9997|
|fp8_perf_h6144_out_m32768_r64|0.69133|0.69130|1.0000|
|fp8_perf_h6144_out_m131072_r64|2.91310|2.91364|0.9998|
|fp8_perf_h6144_up_m4096_r64|0.34573|0.34563|1.0003|
|fp8_perf_h6144_up_m32768_r64|2.86780|2.86900|0.9996|
|fp8_perf_h6144_up_m131072_r64|12.20022|12.21772|0.9986|
|fp8_perf_h6144_down_m4096_r64|0.37991|0.37974|1.0004|
|fp8_perf_h6144_down_m32768_r64|2.88710|2.88943|0.9992|
|fp8_perf_h6144_down_m131072_r64|12.22513|12.24174|0.9986|
|fp8_perf_h8192_qkv_m4096_r64|0.45555|0.45543|1.0003|
|fp8_perf_h8192_qkv_m32768_r64|3.95517|3.95641|0.9997|
|fp8_perf_h8192_qkv_m131072_r64|16.69849|16.71748|0.9989|
|fp8_perf_h8192_out_m4096_r64|0.15074|0.15082|0.9995|
|fp8_perf_h8192_out_m32768_r64|1.23002|1.23082|0.9993|
|fp8_perf_h8192_out_m131072_r64|5.41488|5.41547|0.9999|
|fp8_perf_h8192_up_m4096_r64|0.59405|0.59395|1.0002|
|fp8_perf_h8192_up_m32768_r64|5.33544|5.33045|1.0009|
|fp8_perf_h8192_up_m131072_r64|22.12714|22.19706|0.9969|
|fp8_perf_h8192_down_m4096_r64|0.61879|0.61887|0.9999|
|fp8_perf_h8192_down_m32768_r64|5.30551|5.30867|0.9994|
|fp8_perf_h8192_down_m131072_r64|22.78241|22.77846|1.0002|
|fp8_perf_h3072_out_m32768_r32|0.17757|0.17731|1.0014|
|fp8_perf_h3072_out_m32768_r128|0.18682|0.18675|1.0003|
|fp8_perf_h3072_up_m32768_r32|0.70131|0.70135|1.0000|
|fp8_perf_h3072_up_m32768_r128|0.73847|0.73847|1.0000|
|fp8_perf_h8192_out_m32768_r32|1.22295|1.22368|0.9994|
|fp8_perf_h8192_out_m32768_r128|1.25056|1.25104|0.9996|
|fp8_perf_h8192_up_m32768_r32|5.31417|5.31776|0.9993|
|fp8_perf_h8192_up_m32768_r128|5.43853|5.44032|0.9997|
|fp8_perf_h8192_up_m32768_r64_tp2c|2.54308|2.54537|0.9991|
|fp8_perf_h8192_down_m32768_r64_tp2r|2.50007|2.49993|1.0001|
|fp8_perf_h8192_up_m32768_r64_tp4c|1.23277|1.23330|0.9996|
|fp8_perf_h8192_down_m32768_r64_tp4r|1.23183|1.23248|0.9995|
|fp8_perf_h8192_up_m32768_r64_tp8c|0.60845|0.60842|1.0001|
|fp8_perf_h8192_down_m32768_r64_tp8r|0.61799|0.61779|1.0003|

</details>

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added NVFP4 and FP8 matrix multiplication with optional BF16 LoRA
adapters and bias, supporting adapter ranks of 32, 64, and 128 on
compatible NVIDIA GPUs.
* Exported both operations through the main package API and added usage
guidance.
* Added a command-line benchmark comparing fused operations with
reference implementations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [fd14b30](https://github.com/flashinfer-ai/flashinfer/commit/fd14b3056d0c1aa72c80fc9c35c8493f38c5a9a5)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-14T21:18:10Z
- **提交信息**: perf(trtllm-gen decode): keep CGA reduction for small-batch long-KV decode; fuse v_scale in the decode wrapper (#6267)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR makes three changes to trtllm-gen paged decode, one per commit.
Commit 3 extends commit 1 to multi-token (spec-decode) queries.

### 1. `perf(trtllm-gen decode)`: clamp >16 KV splits to the CGA
reduction limit

`computeCtaAndClusterConfig` sets the KV split count to `min(maxSplits,
SMs / (batch × headsKv × …))`. KV splits are reduced in one of two ways:

- **`CgaSmemReduction`:** the split CTAs form one cluster and reduce
through distributed shared memory. A cluster holds at most 16 CTAs.
- **`GmemReduction`:** the fallback. It reduces through global memory
with an atomic counter.

When there are few (batch × headKv) CTAs and the KV is long, the
SM-filling split goes past 16, and the launch ends up on the GMEM path.
Batch-1 decode with 8 KV heads at KV ≥ 9216, or headKv = 1 models up to
batch 8, are typical cases. More SMs push more shapes past 16. On a
212-SM part, `min(32, 212 / 8) = 26`.

A forced-split sweep showed that the GMEM path costs more than the extra
splits buy. 16 splits on the CGA path beat 17-32 splits on the GMEM path
whenever each CTA walks ≤ 4096 KV tokens. Past that, for example batch 1
at KV 128K, the extra splits win again. The clamp therefore applies only
when all of the following hold:

- one query token per request (`mMaxSeqLenQ == 1`), which is the
measured case;
- a SwapsMmaAb GQA generation kernel (`headDimV < 512`, so MLA is
excluded) and not DSv3 min-latency mode;
- a CGA-reduction cubin is registered for the shape
(`hasCgaSmemReductionKernel`), so the clamp never selects a missing
kernel;
- `mForceGmemReduction` is not set;
- `ceil(maxAttentionWindow / 16) <= 4096`.

`run()` already checks cluster occupancy, and that check is unchanged.
If 16-CTA clusters cannot co-reside, it still falls back to the GMEM
path with the original split. That is what happens on GB300 for 8 KV
heads × 16 splits, so those shapes stay unchanged there.

### 2. `perf(decode)`: fuse `v_scale` into the trtllm-gen paged decode
wrapper

`BatchDecodeWithPagedKVCacheWrapper(backend="trtllm-gen")` passed a
hard-coded bmm2 scale of `1.0` to the kernel, then applied `v_scale` in
torch after the kernel:

- **FP8 output:** `out = (out.to(fp32) * v_scale).to(out.dtype)`, three
elementwise launches.
- **BF16 / FP16 output:** `out *= v_scale`, one launch.

At decode sizes these launches are pure overhead.
`trtllm_batch_decode_with_kv_cache` runs the same cubin with `v_scale`
as its bmm2 scale and has no such tail. The wrapper now forwards
`v_scale` to the kernel as its bmm2 scale (through the `scale_v` slot of
`paged_run`) and skips the post-pass. This applies when `v_scale` is a
python float, or a 1-element fp32 tensor on q's device. Any other form,
and the JIT-variant path, keep the old post-pass.

This also fixes two correctness side effects of the old tail:

- FP8 output is no longer rounded twice.
- A caller-provided FP8 `out=` buffer now receives the scaled result.
Before, the post-pass rebound `out` to a new tensor and left the
caller's buffer unscaled.

The same fusion was done for the prefill wrapper earlier.

### 3. `perf(trtllm-gen decode)`: extend the >16 KV split clamp to
multi-token decode

With spec decode (MTP / Eagle, `q_len_per_req` > 1), the GQA generation
path groups the draft tokens and the head group into one SwapsMmaAb CTA
whenever `q_len × (headsQ / headsKv)` fits in the Q tile (≤ 32 rows).
The base grid is then the same `batch × headsKv` as one-token decode, so
the SM-filling split overshoots 16 in exactly the same cases and lands
on the GMEM path.

Commit 1 gated the clamp to `mMaxSeqLenQ == 1` only because one-token
decode was the only case measured. This commit drops that restriction,
with one exception: head dim 256 keeps the old behavior when `q_len >
1`. That shape family (4/1 heads, D256, bf16, batch 1) measured
0.97-0.98x with the clamp on both SM107 and B200, while every other
affected shape gained. All other conditions from commit 1 are unchanged,
including the occupancy fallback.

Shapes with more than 32 grouped rows (e.g. 8 q-heads per kv-head at
`q_len` 8) select KeepsMmaAb kernels, which have no CGA-reduction
variant, so they are not affected.

## 📊 Speedup vs current `main`

Baseline is `main` at `87422668f`; the candidate is the same tree with
this PR's three commits applied. Speedup multipliers only (`main` time ÷
PR time; above 1 means the PR is faster). Both trees ran in the same job
on the same node, interleaved, with CUDA graphs and cold-L2 rotating
buffers; each number is the min of 2 rounds of medians.

- **SM107:** a GR100 (Rubin) development node with 208 SMs. The
production cluster was unavailable, so treat these as same-node ratios.
- **B200:** run to check for regressions on Blackwell. On B200, shapes
whose launch configuration is identical in both trees scatter by
0.99-1.02x, which is the noise floor of that node.

### Commit 1: split clamp (`trtllm_batch_decode_with_kv_cache`, one
query token)

| shape (batch, KV length, q-heads/kv-heads, head dim, dtype) | q_len |
SM107: PR vs `main` | B200: PR vs `main` |
|---|---:|---:|---:|
| B1, KV 9216, 64/8, D64, fp8 | 1 | 1.12x | 0.99x |
| B1, KV 16384, 64/8, D64, fp8 | 1 | 1.29x | 1.00x |
| B1, KV 16384, 64/8, D128, fp8 | 1 | 1.26x | 1.01x |
| B1, KV 16384, 64/8, D128, bf16 | 1 | 1.29x | 1.00x |
| B1, KV 32768, 64/8, D64, fp8 | 1 | 1.14x | 1.01x |
| B1, KV 65536, 64/8, D64, fp8 | 1 | 1.01x | 1.00x |
| B1, KV 16384, 8/1, D128, fp8 | 1 | 1.13x | 1.19x |
| B4, KV 32768, 8/1, D128, fp8 | 1 | 1.23x | 1.29x |
| B8, KV 16384, 8/1, D128, fp8 | 1 | 1.23x | 1.00x |
| B1, KV 65536, 8/1, D128, fp8 | 1 | 1.33x | 1.38x |
| B1, KV 9216, 4/1, D256, bf16 | 1 | 0.98x | 1.00x |
| *unchanged:* B2, KV 16384, 64/8, D64, fp8 | 1 | 1.00x | 1.00x |
| *unchanged (4096-token guard):* B1, KV 131072, 8/1, D128, fp8 | 1 |
1.01x | 0.99x |
| *unchanged:* B16, KV 16384, 64/8, D64, fp8 | 1 | 1.00x | 1.00x |
| *unchanged:* MLA B128, KV 4096, 16 heads, fp8 | 1 | 1.00x | 1.00x |

- On B200, eight 16-CTA clusters cannot run at once, so 8-KV-head
batch-1 shapes fall back to the original split and are unchanged; the
1-KV-head shapes gain 1.19-1.38x.
- SM107 B1, KV 9216, 4/1, D256, bf16 measured 0.98x here; the earlier
production-cluster run measured 1.05x for the same shape, so this one is
within this node's noise or marginal.

### Commit 2: `v_scale` fusion (`BatchDecodeWithPagedKVCacheWrapper`,
fp8 KV)

`trtllm-gen` is the backend this commit changes; `trtllm-native` is the
control. On SM107 the two batch-1 rows also include commit 1, which is
why `trtllm-native` moves on the KV 16384 row.

| shape | backend | SM107: PR vs `main` | B200: PR vs `main` |
|---|---|---:|---:|
| B16, KV 16384, 64/8, D64, out fp8 | `trtllm-gen` | 1.31x | 1.11x |
| B16, KV 16384, 64/8, D64, out fp8 | `trtllm-native` | 1.00x | 1.00x |
| B16, KV 8192, 64/8, D64, out fp8 | `trtllm-gen` | 1.52x | 1.21x |
| B16, KV 8192, 64/8, D64, out fp8 | `trtllm-native` | 1.00x | 1.00x |
| B16, KV 8192, 64/8, D128, out fp8 | `trtllm-gen` | 1.22x | 1.16x |
| B16, KV 8192, 64/8, D128, out fp8 | `trtllm-native` | 1.00x | 1.00x |
| B1, KV 8192, 64/8, D128, out fp8 | `trtllm-gen` | 1.50x | 1.55x |
| B1, KV 8192, 64/8, D128, out fp8 | `trtllm-native` | 1.00x | 1.00x |
| B1, KV 16384, 64/8, D64, out fp8 | `trtllm-gen` | 1.85x | 1.48x |
| B1, KV 16384, 64/8, D64, out fp8 | `trtllm-native` | 1.39x | 1.00x |
| B256, KV 9216, 8/1, D128, out bfloat16 | `trtllm-gen` | 1.03x | 1.02x
|
| B256, KV 9216, 8/1, D128, out bfloat16 | `trtllm-native` | 1.00x |
1.00x |
| B256, KV 2048, 8/1, D128, out bfloat16 | `trtllm-gen` | 1.10x | 1.04x
|
| B256, KV 2048, 8/1, D128, out bfloat16 | `trtllm-native` | 1.00x |
1.02x |

- After this PR, `trtllm-gen` matches `trtllm-native` on every row on
both GPUs. `trtllm-native` itself is unchanged except where commit 1
applies.

### Commit 3: clamp for multi-token decode
(`trtllm_batch_decode_with_kv_cache`, `q_len_per_req` > 1)

| shape | q_len | SM107: PR vs `main` | B200: PR vs `main` |
|---|---:|---:|---:|
| B1, KV 16384, 64/8, D64, fp8 | 2 | 1.29x | 1.01x |
| B1, KV 16384, 64/8, D64, fp8 | 3 | 1.31x | 0.99x |
| B1, KV 16384, 64/8, D64, fp8 | 4 | 1.29x | 1.00x |
| B1, KV 16384, 64/8, D64, bf16 | 2 | 1.29x | 1.00x |
| B1, KV 16384, 64/8, D64, bf16 | 4 | 1.27x | 0.99x |
| B1, KV 16384, 64/8, D128, fp8 | 2 | 1.31x | 1.00x |
| B1, KV 16384, 64/8, D128, fp8 | 4 | 1.29x | 1.00x |
| B1, KV 16384, 64/8, D128, bf16 | 2 | 1.31x | 1.00x |
| B1, KV 16384, 64/8, D128, bf16 | 4 | 1.32x | 1.00x |
| B1, KV 32768, 64/8, D64, fp8 | 2 | 1.15x | 1.00x |
| B1, KV 32768, 64/8, D64, fp8 | 4 | 1.13x | 1.00x |
| B1, KV 16384, 8/1, D128, fp8 | 2 | 1.13x | 1.19x |
| B1, KV 16384, 8/1, D128, fp8 | 4 | 1.15x | 1.23x |
| B4, KV 16384, 8/1, D128, fp8 | 2 | 1.24x | 0.99x |
| B4, KV 16384, 8/1, D128, fp8 | 4 | 1.00x | 1.00x |
| B8, KV 16384, 8/1, D128, fp8 | 2 | 1.26x | 1.00x |
| B8, KV 16384, 8/1, D128, fp8 | 4 | 1.25x | 1.01x |
| *excluded (head dim 256):* B1, KV 16384, 4/1, D256, bf16 | 2 | 1.00x |
0.99x |
| *excluded (head dim 256):* B1, KV 16384, 4/1, D256, bf16 | 4 | 1.00x |
1.00x |
| *unchanged (4096-token guard):* B1, KV 131072, 64/8, D64, fp8 | 2 |
1.00x | 1.00x |

- B200 changes only the 1-KV-head batch-1 rows (1.19-1.23x); every other
B200 row keeps its launch configuration and is within noise.

<details>
<summary>Earlier measurements: SM107 vs GB300 on the production
clusters, older base</summary>

These were measured before the rebase onto current `main`, against the
base the PR was originally written on. They add the SM107-vs-GB300
comparison that the table above does not have.

Speedup multipliers only:

- **PR vs `main`:** baseline and this PR ran in the same job on the same
node, using CUDA graphs with cold-L2 rotating buffers, min of 2
interleaved rounds.
- **SM107 vs GB300, before / after:** both chips running `main`, then
both running this PR.

Shapes are given as batch / KV length / q-heads/kv-heads / head dim /
dtype.

#### Commit 1: split clamp (`trtllm-native` /
`trtllm_batch_decode_with_kv_cache`)

| shape | SM107: PR vs `main` | GB300: PR vs `main` | SM107 vs GB300,
before | SM107 vs GB300, after |
|---|---:|---:|---:|---:|
| B1, KV 9216, 64/8, D64, fp8 | 1.28x | 1.03x | 1.09x | 1.36x |
| B1, KV 16384, 64/8, D64, fp8 | 1.38x | 1.00x | 1.02x | 1.41x |
| B1, KV 16384, 64/8, D128, fp8 | 1.33x | 1.00x | 1.10x | 1.45x |
| B1, KV 16384, 64/8, D128, bf16 | 1.20x | 1.01x | 1.19x | 1.41x |
| B1, KV 32768, 64/8, D64, fp8 | 1.21x | 1.00x | 1.09x | 1.32x |
| B1, KV 65536, 64/8, D64, fp8 | 1.06x | 1.00x | 1.21x | 1.29x |
| B1, KV 16384, 8/1, D128, fp8 | 1.32x | 1.23x | 1.08x | 1.15x |
| B4, KV 32768, 8/1, D128, fp8 | 1.48x | 1.31x | 1.03x | 1.18x |
| B8, KV 16384, 8/1, D128, fp8 | 1.32x | 1.00x | 1.09x | 1.43x |
| B1, KV 65536, 8/1, D128, fp8 | 1.60x | 1.56x | 1.10x | 1.13x |
| B1, KV 9216, 4/1, D256, bf16 | 1.05x | 0.98x | 1.03x | 1.10x |
| *unchanged:* B2, KV 16384, 64/8, D64, fp8 | 1.00x | 1.00x | 1.17x |
1.17x |
| *unchanged (guard):* B1, KV 131072, 8/1, D128, fp8 | 1.00x | 1.00x |
0.92x | 0.92x |
| *unchanged:* B16, KV 16384, 64/8, D64, fp8 | 1.00x | 1.00x | 1.24x |
1.24x |
| *unchanged:* MLA B128, KV 4096, 16 heads, fp8 | 1.00x | 1.00x | 1.28x
| 1.28x |

The full sweep was 62 shapes:

- **SM107:** 35 shapes changed, all faster (1.04x-1.60x). The other 27
are within ±0.3%.
- **GB300:** the headKv = 1 shapes gain 1.06x-1.56x. Shapes with 8 KV
heads at batch 1 are unchanged, because of the occupancy fallback.
- **One regression on GB300:** B1, KV 9216, 4/1, D256, bf16, at 0.98x
(shown in the table).

#### Commit 2: `v_scale` fusion (`BatchDecodeWithPagedKVCacheWrapper`,
`backend="trtllm-gen"`, fp8 KV)

| shape | SM107: PR vs `main` | GB300: PR vs `main` | SM107 vs GB300,
before | SM107 vs GB300, after |
|---|---:|---:|---:|---:|
| B16, KV 16384, 64/8, D64, fp8 out | 1.15x | 1.13x | 1.22x | 1.24x |
| B16, KV 8192, 64/8, D64, fp8 out | 1.26x | 1.24x | 1.19x | 1.21x |
| B16, KV 8192, 64/8, D128, fp8 out | 1.20x | 1.16x | 1.29x | 1.33x |
| B1, KV 8192, 64/8, D128, fp8 out | 1.65x | 1.58x | 1.34x | 1.39x |
| B1, KV 16384, 64/8, D64, fp8 out | 1.52x | 1.52x | 1.01x | 1.02x |
| B256, KV 9216, 8/1, D128, bf16 out | 1.02x | 1.02x | 1.34x | 1.34x |
| B256, KV 2048, 8/1, D128, bf16 out | 1.07x | 1.05x | 1.29x | 1.32x |

- With this change, the `trtllm-gen` wrapper backend matches
`trtllm-native` to within 0.3% on every row, on both chips.
- `trtllm-native` itself does not change (≤ 0.2%), which serves as the
control.
- The commit-2 rows were measured without commit 1. That is why the B1
KV 16384 row shows no cross-arch change.

#### Commit 3: clamp for multi-token decode
(`trtllm_batch_decode_with_kv_cache`, `q_len_per_req` > 1)

Measured on a GR100 (SM107) development node and a B200, baseline =
commit 1 alone, same timing method as above. GB300 was not available for
this commit, so there is no cross-arch column. B200, like GB300, cannot
co-schedule eight 16-CTA clusters, so the 8-KV-head rows fall back to
the original GMEM split there.

| shape | q_len | SM107: PR vs before | B200: PR vs before |
|---|---:|---:|---:|
| B1, KV 16384, 64/8, D64, fp8 | 2 | 1.27x | 1.02x |
| B1, KV 16384, 64/8, D64, fp8 | 3 | 1.29x | 1.00x |
| B1, KV 16384, 64/8, D64, fp8 | 4 | 1.29x | 1.01x |
| B1, KV 16384, 64/8, D64, bf16 | 2 | 1.27x | 1.00x |
| B1, KV 16384, 64/8, D64, bf16 | 4 | 1.27x | 1.00x |
| B1, KV 16384, 64/8, D128, fp8 | 2 | 1.32x | 1.01x |
| B1, KV 16384, 64/8, D128, fp8 | 4 | 1.28x | 1.00x |
| B1, KV 16384, 64/8, D128, bf16 | 2 | 1.30x | 1.00x |
| B1, KV 16384, 64/8, D128, bf16 | 4 | 1.30x | 1.00x |
| B1, KV 32768, 64/8, D64, fp8 | 2 | 1.15x | 1.00x |
| B1, KV 32768, 64/8, D64, fp8 | 4 | 1.14x | 1.00x |
| B1, KV 16384, 8/1, D128, fp8 | 2 | 1.10x | 1.19x |
| B1, KV 16384, 8/1, D128, fp8 | 4 | 1.16x | 1.26x |
| B4, KV 16384, 8/1, D128, fp8 | 2 | 1.23x | 1.00x |
| B4, KV 16384, 8/1, D128, fp8 | 4 | 1.00x | 1.01x |
| B8, KV 16384, 8/1, D128, fp8 | 2 | 1.25x | 1.01x |
| B8, KV 16384, 8/1, D128, fp8 | 4 | 1.24x | 1.00x |
| *unchanged (guard):* B1, KV 131072, 64/8, D64, fp8 | 2 | 1.00x | 1.00x
|
| *unchanged:* any shape with `q_len` 1 | 1 | 1.00x | 1.00x |
| *excluded (head dim 256):* B1, KV 16384, 4/1, D256, bf16 | 2-4 | 1.00x
| 1.00x |

- Without the head-dim-256 exclusion, the last row measured 1.00x /
0.97x (q_len 2 / 4) on SM107 and 0.98x / 0.98x on B200. With it, those
shapes run the unchanged path.
- Outputs match the baseline to within 1-2 ULP of the output dtype on
every row (reduction-order differences only).

</details>

## 🔍 Related Issues

Rubin decode perf: small-batch long-KV paged decode falls short of the
modelled speedup over GB300.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (clang-format, ruff, mypy and the
whitespace hooks were run on the diff at commit time.)

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

The `trtllm-gen` wrapper check in `_test_trtllm_batch_decode` now also
runs the wrapper with `out=`. It asserts that the returned tensor shares
storage with the caller's buffer and holds the scaled result.

Tests on `main` `87422668f` + this PR (current head):

| GPU | suite | result |
|---|---|---|
| SM107 | `tests/attention/test_trtllm_gen_attention_decode.py --full -k
"long_sequence_length or reduction_indexing or dynamic_page_size or
same_dtype_gqa_grouping or head_dim_256 or batch_decode_bs1 or
gpt_oss_counter_reuse"` | 788 passed, 32 skipped, 0 failed |
| B200 | same command | 788 passed, 32 skipped, 0 failed |
| SM107 | same file, default (sampled) matrix, `-k "<same> or
(test_trtllm_batch_decode and HND and fp8-fp8)"` | 151 passed, 8
skipped, 0 failed |

Earlier runs on the original base (GR100 / SM107):

| suite | result |
|---|---|
| `tests/attention/test_trtllm_gen_attention_decode.py -k
test_trtllm_batch_decode` (both commits) | 63836 passed, 33376 skipped,
0 failed |
| `tests/attention/test_trtllm_gen_attention_decode.py -k
"long_sequence_length or batch_decode_bs1 or gpt_oss_counter_reuse"`
(commit 1) | 369 passed |
| `tests/attention/test_trtllm_gen_attention_decode.py -k
"long_sequence_length or reduction_indexing or dynamic_page_size or
same_dtype_gqa_grouping or head_dim_256 or batch_decode_bs1 or
gpt_oss_counter_reuse"` (commit 3, without the head-dim-256 exclusion) |
756 passed, 64 skipped, 0 failed |

The commit-3 run includes `long_sequence_length` cases at batch 1 with
`q_len` 3 and 4 up to KV 131072, which take the extended clamp.

Benchmark `--refcheck` against `fa2` found no output mismatches on
either chip, for both commits.

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

- **Speedups and tests above are on current `main` (`87422668f`) plus
this PR's head (`53088d9ac`).** The SM107 numbers come from a
development node because the production Rubin cluster was unavailable;
the ratios are same-node, same-job measurements.
- **The thresholds are empirical.** The 4096-tokens-per-CTA guard comes
from the sweep (KV 128K regresses without it), and the head-dim-256
exclusion for `q_len` > 1 comes from the commit-3 measurements; neither
is a cost model.
- **Commit 3 is measured as committed**, including the head-dim-256
exclusion (those rows show 1.00x).
- **Not measured:**
  - page sizes other than 16 and 64, NVFP4 KV, sliding window, and fp16;
- B300 and GB300 against current `main`. B200 was measured for all three
commits and shows no regression beyond its ±2% noise floor. The clamp is
arch-generic, but the occupancy fallback leaves shapes unchanged
wherever 16-CTA clusters don't fit.
- **One small GB300 regression** (0.98x, B1 KV 9216, 4/1, D256, bf16).
It is within noise of the 2% bar, but it is consistent across rounds.
- The tensor form of `v_scale` (1-element fp32 device tensor) uses the
same launcher path as `trtllm_batch_decode_with_kv_cache`, but no test
or benchmark exercises it through the wrapper.
- `single_decode_with_kv_cache` and the non-trtllm-gen wrapper backends
(fa2, cudnn) still post-multiply `v_scale`. They are out of scope here.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Paged decode can apply supported value scaling directly within the
kernel; unsupported values continue to use output-side scaling.
* Eligible decode configurations cap key-value partitions at 16 when the
sequence length per partition is within the supported limit.
* **Bug Fixes**
* Supplying an output buffer during decode now returns that buffer with
results matching the standard output.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fd1178e](https://github.com/flashinfer-ai/flashinfer/commit/fd1178e9a777ebfe42b89841ce25c856de41cd71)

- **作者**: eigen
- **时间**: 2026-10-14T20:49:23Z
- **提交信息**: feat(cake_gdn): FP32-state initial prefill records for the Qwen3-Next / Qwen3.5 TP2/TP4/TP8 geometries and the re-delivered Cake CP-prefill programs (sm_100a, sm_103a) (#6478)

## Summary

`chunk_gated_delta_rule(backend="cake_gdn")` gains the eleven frozen
BF16-I/O, FP32-state `initial`+final prefill records that the vLLM
TP2/TP4/TP8 per-rank geometries of Qwen3-Next-80B / Qwen3.5 (35B, 397B)
were missing — (HEAD_GROUP_LOG2, IS_GQA, NUM_O_HEADS_LOG2) = (1,0,4)
H8/HV16, (1,0,3) H4/HV8, (2,0,5) H8/HV32, (2,0,4) H4/HV16, (2,0,3)
H2/HV8 in both physical schedules (DV-split and full-DV) and (1,0,2)
H2/HV4 in the full-DV schedule — together with a re-delivery of the Cake
CP-prefill programs (`csrc/gdn/gdn_cp`) that `use_cp="auto"` now reaches
on SM100/SM103 for long few-sequence rows.

- **Manifest + records**: eleven records = two generated bodies under
`csrc/gdn/cake` (`cake_gdn_e1e2550ac8ccd62ae772_730343990bdc.cu`
DV-split, `cake_gdn_c2cc4dde363f0f11c73d_7772d559e3af.cu` full-DV) with
eleven, host shims derived from the shipped Hq16/Hv32 records; the
resolver (`flashinfer/jit/cake_gdn.py`) fails closed per architecture
(`CakeGDNUnsupportedError` for an architecture a record was not exported
for) and `chunk_gated_delta_rule`'s docstring lists the covered geometry
set.
- **CP band** (`flashinfer/gdn_prefill.py`): with `use_cp="auto"`, BF16
I/O, FP32 initial+final state, gates, no checkpoints/indices,
`4·num_seqs·Hv < SM count` and `max_seqlen >= 4096` on compute
capability 10.0/10.3 the call runs the Cake four-stage CP programs (CUDA
graph); the same rule lives in the Cake dispatcher and the exporter
plan.
- **CP programs** (`csrc/gdn/gdn_cp`, commit bc8569708): plain-BF16
Stage-2 MN precompute, native BF16 kernels on 10.0/10.3 (no token-serial
FP32 state-repair recurrences; `_NATIVE_BF16_ARCHES`), one-wave
chunk-overflow rule on every SM count; sm_107a programs carried over
unchanged. Round 4 adds an int32 `cu_seqlens` Stage-1 variant
(`t_precompute_cu32`, `t_precompute_bf16_cu32`): it reads the caller's
int32 prefix sums and publishes the int64 copy the later stages read, so
the eager int32 call no longer starts with a host-issued int32->int64
staging copy (the first GPU activity of every call) and int64 inputs are
bound by address with no copy; `has_gdn_cp_kernel` gates the selection
per architecture ahead of the GB300 Hv48 alias, sm_107a and all-empty
batches keep the host cast; `launch_with_bindings` validates the rebound
prefix (dtype, shape, contiguity, device).
- **Tests**: `tests/gdn/test_cake_gdn_cp_backend.py` covers both prefix
dtypes (plans, direct launches, frozen graphs, checkpoint oracle, kernel
count) and pins the host one-wave chunk-overflow rule;
`tests/gdn/test_cake_gdn_prefill_gpu.py` covers the six geometries × two
schedules (output and FP32 final state vs the FP32 reference recurrence
at atol=rtol=1e-2, state-carry two-segment calls, CUDA-graph
capture/replay); `tests/gdn/test_cake_gdn_prefill_band.py` pins the band
rule.

## Performance (paired cold-L2 CUPTI, 3 counterbalanced groups, per row
vs `chunk_gated_delta_rule(backend="auto")` on the same inputs)

| geometry | sm_100a (B200) speedup min / geomean / max over 11 rows |
sm_103a (GB300) speedup min / geomean / max | slowest-gain row |
|---|---|---|---|
| G1 (1,0,4) Hq8/Hv16 — Qwen3-Next-80B / Qwen3.5-35B TP2 | 1.036 / 1.231
/ 1.626 | 1.051 / 1.346 / 2.372 | `35b_tp2_hq8_hv16_1x16384` 1.036
(sm_100a) |
| G2 (1,0,3) Hq4/Hv8 — TP4 | 1.025 / 1.451 / 4.338 | 1.025 / 1.752 /
6.758 | `35b_tp4_hq4_hv8_mixed16` 1.025 (sm_103a) |
| G3 (1,0,2) Hq2/Hv4 — TP8 (full-DV record + the shipped DV-split
record) | 1.076 / 1.613 / 4.328 | 1.069 / 2.020 / 6.654 |
`35b_tp8_hq2_hv4_mixed16` 1.069 (sm_103a) |
| G4 (2,0,5) Hq8/Hv32 — Qwen3.5-397B TP2 | 1.033 / 1.195 / 1.653 | 1.030
/ 1.282 / 2.440 | `397b_tp2_hq8_hv32_1x16384` 1.030 (sm_103a) |
| G5 (2,0,4) Hq4/Hv16 — TP4 | 1.029 / 1.226 / 1.613 | 1.041 / 1.346 /
2.380 | `397b_tp4_hq4_hv16_2x8192` 1.029 (sm_100a) |
| G6 (2,0,3) Hq2/Hv8 — TP8 | 1.020 / 1.454 / 4.338 | 1.023 / 1.760 /
6.818 | `397b_tp8_hq2_hv8_mixed16` 1.020 (sm_100a) |
| **all 66 rows, sm_100a** | 1.020 / 1.353 / 4.338 | | 0 rows <= 1.00;
source/export min 0.971 / geomean 1.040 |
| **all 66 rows, sm_103a** | | 1.023 / 1.561 / 6.818 | 0 rows <= 1.00;
source/export min 0.976 / geomean 1.095 |

Rows: 1x16384, 1x4096, 2x8192, 4x2048, 8x1024, 16x512, 32x512, 64x256,
mixed16 (8192 … 1), 1x2048, 4x512 per geometry; BF16 I/O, FP32 initial +
final state, gates and betas, caller-normalized Q/K, `scale="auto"`,
int32 `cu_seqlens`, `use_cp="auto"`. Every row is strictly faster than
`backend="auto"` on both architectures; the full per-row receipts are in
the runner section below.

## Validation

- **Correctness**: every exported row (66 per architecture) checks the
BF16 output and the FP32 final state against the FP32 reference
recurrence at `atol = rtol = 1e-2` before and after timing, and the
source-vs-export output-identity gate (the Cake-side launch and the
delivered FlashInfer launch produce the same bytes on one shared
fixture). `tests/gdn/test_cake_gdn_prefill_gpu.py` adds state-carry
two-segment calls and CUDA-graph capture/replay per geometry.
- **Export protocol**: paired cold-L2 CUPTI timing of the Cake source
launch and the delivered FlashInfer launch, three counterbalanced
groups, gates `source/export >= 0.97`, `directional disagreement <=
0.05`, `endpoint drift <= 0.02`, plus the external baseline
`chunk_gated_delta_rule(backend="auto")` (strict `> 1.00` on every row).
The merged seal of the 66 x 2 rows is complete (`complete=True`,
`all_passed=True`); the CP-program re-delivery carries its own merged
seal of 322 shapes (161 per architecture, `complete=True`,
`all_passed=True`).
- **Tests on this tree** (`tests/gdn/test_cake_gdn_*`; run on commit
`b83d18c05`, whose tree is identical to the PR head): sm_103a GPU 726
passed / 3 skipped, sm_100a GPU 718 passed / 11 skipped, CPU 560 passed
/ 169 skipped (GPU tests skip). Full-DAG and per-stage
`compute-sanitizer` synccheck/memcheck runs on the CP programs report 0
errors on both architectures.
- **No regression**: the existing `cake_gdn` routes (Qwen3.5 BF16
records, decode) resolve unchanged; the int64 `cu_seqlens` CP programs
are byte-identical to the previous delivery (only the two `*_cu32`
Stage-1 programs are new).

## Architectures

Delivered and measured on sm_100a (B200) and sm_103a (GB300). The new
records have no sm_107a view: the resolver raises
`CakeGDNUnsupportedError` for them on sm_107a (the sm_107a leg is
tracked separately and will follow as its own PR once measured).

---

## Generated-program export evidence

Baseline: **Cake GDN non-CP decode/prefill dispatchers** at Cake
revision `7b22b3d4090a77827ec1360d74230455ff66efc7`.

## Hardware stages

- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-dfea784a-ee44-6e56-65c1-112782e1de65`;
18 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-e3cb08ec-b0a7-2db6-880a-762db4ab0e1d`;
17 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-90f6c74a-5c18-d77d-5dce-f31533fe8ce2`;
15 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-54ecc425-5858-fdc4-7451-6ca1e9de3ca2`;
16 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-5d603b55-6d0a-9f8c-7835-88bc8ce573e6`;
17 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-f68d5db7-d8d1-b832-625f-4e0363035c35`;
17 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-8701bd88-0d51-644e-e9c8-c9806e5d1339`;
16 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-1bf8659d-992d-24be-0d1c-ab79bf77a829`;
16 shapes (named in the per-shape tables below).

Target revision: `bc856970852dc23c08326945031f9d36e4f85940`.

Benchmark execution: `direct`; 3 counterbalanced groups, 50.000 ms
warmup and 100.000 ms reportable budget per arm/group.
Latency metric: CUPTI GPU span per sample, first compute-kernel start to
last compute-kernel end of one arm call (every kernel the call launches,
asynchronous copies excluded), after a cold-L2 flush before each
measured sample, with the SM clock held at or above 1900 MHz; the
reported value is the per-arm median. Each row's ``sm_clock_mhz_range``
in the summary JSON is the SM clock range observed while the row was
timed (group-boundary probes and, in the symmetric graph mode, every
sampled warmup/measurement phase).
Each sample follows one unmeasured same-arm launch, state restoration,
and a fresh cold-L2 flush.

The complete semantic arguments and machine-readable receipts remain in
`summary.json`; the table below retains every registered shape without
repeating those arguments, keys routes and external baselines against
the legends that follow it, and inlines each shape's external
comparison.

## Per-shape results

|Shape|GPU|Route|Source ms|Export ms|Source / Export|Baseline|Baseline
ms|Baseline / Export|Verdict|
|---|---|---|---:|---:|---:|---|---:|---:|---|

|prefill_fp32state_35b_tp2_hq8_hv16_1x16384__sm_100a|G0|R1|0.187773|0.188030|0.9986x|B1|0.194781|1.0359x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_1x16384__sm_103a|G4|R2|0.187073|0.172352|1.0854x|B1|0.194561|1.1289x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_1x4096__sm_100a|G1|R3|0.111424|0.083776|1.3300x|B1|0.113727|1.3575x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_1x4096__sm_103a|G5|R4|0.139680|0.079904|1.7481x|B1|0.147104|1.8410x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_2x8192__sm_100a|G2|R5|0.178878|0.178942|0.9996x|B1|0.185981|1.0393x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_2x8192__sm_103a|G6|R6|0.183712|0.167361|1.0977x|B1|0.187680|1.1214x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_4x2048__sm_100a|G3|R43|0.067327|0.067391|0.9991x|B1|0.077119|1.1444x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_4x2048__sm_103a|G7|R44|0.060928|0.060896|1.0005x|B1|0.072832|1.1960x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_8x1024__sm_100a|G0|R55|0.044544|0.044608|0.9986x|B1|0.051360|1.1514x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_8x1024__sm_103a|G4|R56|0.041088|0.041056|1.0008x|B1|0.047168|1.1489x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_16x512__sm_100a|G1|R55|0.053376|0.053552|0.9967x|B1|0.068032|1.2704x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_16x512__sm_103a|G5|R56|0.048832|0.048736|1.0020x|B1|0.063585|1.3047x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_32x512__sm_100a|G2|R55|0.101663|0.101343|1.0032x|B1|0.133566|1.3180x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_32x512__sm_103a|G6|R56|0.093696|0.093632|1.0007x|B1|0.126368|1.3496x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_64x256__sm_100a|G3|R55|0.133182|0.133215|0.9998x|B1|0.171934|1.2907x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_64x256__sm_103a|G7|R56|0.126528|0.126496|1.0003x|B1|0.166240|1.3142x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_mixed16__sm_100a|G0|R55|0.256957|0.256669|1.0011x|B1|0.270205|1.0527x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_mixed16__sm_103a|G4|R56|0.241952|0.242081|0.9995x|B1|0.254528|1.0514x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_1x2048__sm_100a|G1|R43|0.063264|0.063360|0.9985x|B1|0.103008|1.6258x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_1x2048__sm_103a|G5|R44|0.059360|0.059360|1.0000x|B1|0.140800|2.3720x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_4x512__sm_100a|G2|R43|0.023552|0.023424|1.0055x|B1|0.032384|1.3825x|pass|

|prefill_fp32state_35b_tp2_hq8_hv16_4x512__sm_103a|G6|R44|0.021696|0.021696|1.0000x|B1|0.030784|1.4189x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_1x16384__sm_100a|G3|R7|0.144862|0.130878|1.1068x|B1|0.144766|1.1061x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_1x16384__sm_103a|G7|R8|0.164289|0.122689|1.3391x|B1|0.165568|1.3495x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_1x4096__sm_100a|G0|R9|0.105279|0.072735|1.4474x|B1|0.105599|1.4518x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_1x4096__sm_103a|G4|R10|0.139104|0.073632|1.8892x|B1|0.145888|1.9813x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_2x8192__sm_100a|G1|R11|0.131232|0.118656|1.1060x|B1|0.135647|1.1432x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_2x8192__sm_103a|G5|R12|0.154912|0.110080|1.4073x|B1|0.161297|1.4653x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_4x2048__sm_100a|G2|R45|0.064288|0.064735|0.9931x|B1|0.108382|1.6742x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_4x2048__sm_103a|G6|R46|0.059712|0.059584|1.0021x|B1|0.145760|2.4463x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_8x1024__sm_100a|G3|R45|0.038143|0.038144|1.0000x|B1|0.047456|1.2441x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_8x1024__sm_103a|G7|R46|0.034880|0.034848|1.0009x|B1|0.045312|1.3003x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_16x512__sm_100a|G0|R49|0.028608|0.028672|0.9978x|B1|0.035103|1.2243x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_16x512__sm_103a|G4|R50|0.026528|0.026592|0.9976x|B1|0.032992|1.2407x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_32x512__sm_100a|G1|R49|0.052960|0.053152|0.9964x|B1|0.068128|1.2818x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_32x512__sm_103a|G5|R50|0.048864|0.048800|1.0013x|B1|0.063072|1.2925x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_64x256__sm_100a|G2|R49|0.069695|0.069695|1.0000x|B1|0.097727|1.4022x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_64x256__sm_103a|G6|R50|0.065408|0.065344|1.0010x|B1|0.094304|1.4432x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_mixed16__sm_100a|G3|R49|0.245437|0.245406|1.0001x|B1|0.251661|1.0255x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_mixed16__sm_103a|G7|R50|0.230625|0.230528|1.0004x|B1|0.236225|1.0247x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_1x2048__sm_100a|G0|R45|0.062591|0.062687|0.9985x|B1|0.100351|1.6008x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_1x2048__sm_103a|G4|R46|0.058976|0.058944|1.0005x|B1|0.141265|2.3966x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_4x512__sm_100a|G1|R45|0.022111|0.022145|0.9985x|B1|0.096065|4.3380x|pass|

|prefill_fp32state_35b_tp4_hq4_hv8_4x512__sm_103a|G5|R46|0.020544|0.020640|0.9953x|B1|0.139489|6.7582x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_1x16384__sm_100a|G2|R13|0.146126|0.116831|1.2508x|B1|0.149982|1.2838x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_1x16384__sm_103a|G6|R14|0.172224|0.112832|1.5264x|B1|0.175600|1.5563x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_1x4096__sm_100a|G3|R15|0.104159|0.066591|1.5642x|B1|0.107775|1.6185x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_1x4096__sm_103a|G7|R16|0.137792|0.070048|1.9671x|B1|0.151392|2.1613x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_2x8192__sm_100a|G0|R17|0.122975|0.095359|1.2896x|B1|0.122718|1.2869x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_2x8192__sm_103a|G4|R18|0.151712|0.091456|1.6589x|B1|0.152064|1.6627x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_4x2048__sm_100a|G1|R39|0.063232|0.064895|0.9744x|B1|0.102432|1.5784x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_4x2048__sm_103a|G5|R40|0.059328|0.060416|0.9820x|B1|0.141873|2.3483x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_8x1024__sm_100a|G2|R39|0.036448|0.037343|0.9760x|B1|0.099423|2.6624x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_8x1024__sm_103a|G6|R40|0.033824|0.034400|0.9833x|B1|0.139008|4.0409x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_16x512__sm_100a|G3|R39|0.023296|0.023904|0.9746x|B1|0.032320|1.3521x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_16x512__sm_103a|G7|R40|0.021664|0.022208|0.9755x|B1|0.031360|1.4121x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_32x512__sm_100a|G0|R53|0.028575|0.028607|0.9989x|B1|0.035296|1.2338x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_32x512__sm_103a|G4|R54|0.026528|0.026432|1.0036x|B1|0.033024|1.2494x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_64x256__sm_100a|G1|R53|0.037152|0.037312|0.9957x|B1|0.051360|1.3765x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_64x256__sm_103a|G5|R54|0.034432|0.034432|1.0000x|B1|0.048801|1.4173x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_mixed16__sm_100a|G0|R39|0.230109|0.232700|0.9889x|B1|0.250461|1.0763x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_mixed16__sm_103a|G6|R40|0.213920|0.218241|0.9802x|B1|0.233217|1.0686x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_1x2048__sm_100a|G3|R39|0.062719|0.063423|0.9889x|B1|0.101343|1.5979x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_1x2048__sm_103a|G7|R40|0.058912|0.060128|0.9798x|B1|0.145984|2.4279x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_4x512__sm_100a|G0|R39|0.021344|0.021983|0.9709x|B1|0.095135|4.3277x|pass|

|prefill_fp32state_35b_tp8_hq2_hv4_4x512__sm_103a|G4|R40|0.020256|0.020736|0.9769x|B1|0.137984|6.6543x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_1x16384__sm_100a|G1|R19|0.317343|0.318208|0.9973x|B1|0.328639|1.0328x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_1x16384__sm_103a|G5|R20|0.292592|0.292257|1.0011x|B1|0.301089|1.0302x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_1x4096__sm_100a|G2|R21|0.124511|0.110975|1.1220x|B1|0.127551|1.1494x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_1x4096__sm_103a|G6|R22|0.155968|0.102368|1.5236x|B1|0.161088|1.5736x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_2x8192__sm_100a|G3|R41|0.240701|0.240861|0.9993x|B1|0.254493|1.0566x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_2x8192__sm_103a|G7|R42|0.218881|0.218912|0.9999x|B1|0.238272|1.0884x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_4x2048__sm_100a|G0|R47|0.075583|0.075806|0.9971x|B1|0.083231|1.0979x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_4x2048__sm_103a|G4|R48|0.068704|0.068672|1.0005x|B1|0.075008|1.0923x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_8x1024__sm_100a|G1|R47|0.084607|0.084736|0.9985x|B1|0.101024|1.1922x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_8x1024__sm_103a|G5|R48|0.076704|0.077920|0.9844x|B1|0.091616|1.1758x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_16x512__sm_100a|G2|R47|0.101695|0.101631|1.0006x|B1|0.132702|1.3057x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_16x512__sm_103a|G6|R48|0.094144|0.094048|1.0010x|B1|0.124544|1.3243x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_32x512__sm_100a|G3|R47|0.196509|0.196605|0.9995x|B1|0.234077|1.1906x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_32x512__sm_103a|G7|R48|0.183552|0.183681|0.9993x|B1|0.224096|1.2200x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_64x256__sm_100a|G0|R47|0.263421|0.263388|1.0001x|B1|0.333051|1.2645x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_64x256__sm_103a|G4|R48|0.249344|0.249697|0.9986x|B1|0.317057|1.2698x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_mixed16__sm_100a|G1|R47|0.299647|0.298271|1.0046x|B1|0.316448|1.0609x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_mixed16__sm_103a|G5|R48|0.275648|0.274464|1.0043x|B1|0.294721|1.0738x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_1x2048__sm_100a|G2|R41|0.065087|0.065280|0.9970x|B1|0.107935|1.6534x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_1x2048__sm_103a|G6|R42|0.060352|0.060288|1.0011x|B1|0.147073|2.4395x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_4x512__sm_100a|G3|R47|0.028320|0.028288|1.0011x|B1|0.035391|1.2511x|pass|

|prefill_fp32state_397b_tp2_hq8_hv32_4x512__sm_103a|G7|R48|0.026304|0.026304|1.0000x|B1|0.033248|1.2640x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_1x16384__sm_100a|G0|R23|0.187165|0.187358|0.9990x|B1|0.194174|1.0364x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_1x16384__sm_103a|G4|R24|0.186016|0.169921|1.0947x|B1|0.194976|1.1475x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_1x4096__sm_100a|G1|R25|0.111552|0.083167|1.3413x|B1|0.113504|1.3648x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_1x4096__sm_103a|G5|R26|0.140737|0.080064|1.7578x|B1|0.147360|1.8405x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_2x8192__sm_100a|G2|R27|0.178046|0.179678|0.9909x|B1|0.184927|1.0292x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_2x8192__sm_103a|G6|R28|0.183360|0.165824|1.1058x|B1|0.188352|1.1359x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_4x2048__sm_100a|G3|R35|0.067552|0.067519|1.0005x|B1|0.076894|1.1388x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_4x2048__sm_103a|G7|R36|0.060736|0.060928|0.9968x|B1|0.071776|1.1780x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_8x1024__sm_100a|G0|R57|0.043903|0.043967|0.9985x|B1|0.051295|1.1667x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_8x1024__sm_103a|G4|R58|0.040032|0.040032|1.0000x|B1|0.047008|1.1743x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_16x512__sm_100a|G1|R57|0.053056|0.053056|1.0000x|B1|0.067680|1.2756x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_16x512__sm_103a|G5|R58|0.048256|0.048224|1.0007x|B1|0.062496|1.2960x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_32x512__sm_100a|G2|R57|0.101216|0.101471|0.9975x|B1|0.132271|1.3035x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_32x512__sm_103a|G6|R58|0.093280|0.093088|1.0021x|B1|0.125024|1.3431x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_64x256__sm_100a|G3|R57|0.132926|0.132927|1.0000x|B1|0.169214|1.2730x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_64x256__sm_103a|G7|R58|0.125792|0.125664|1.0010x|B1|0.163808|1.3035x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_mixed16__sm_100a|G0|R57|0.258045|0.258365|0.9988x|B1|0.269468|1.0430x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_mixed16__sm_103a|G4|R58|0.242496|0.243072|0.9976x|B1|0.253152|1.0415x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_1x2048__sm_100a|G1|R35|0.063520|0.063649|0.9980x|B1|0.102688|1.6133x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_1x2048__sm_103a|G5|R36|0.059584|0.059488|1.0016x|B1|0.141568|2.3798x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_4x512__sm_100a|G2|R35|0.023391|0.023647|0.9892x|B1|0.032160|1.3600x|pass|

|prefill_fp32state_397b_tp4_hq4_hv16_4x512__sm_103a|G6|R36|0.021696|0.021536|1.0074x|B1|0.030304|1.4071x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_1x16384__sm_100a|G3|R29|0.144415|0.129918|1.1116x|B1|0.144494|1.1122x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_1x16384__sm_103a|G7|R30|0.163680|0.121409|1.3482x|B1|0.166177|1.3687x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_1x4096__sm_100a|G0|R31|0.104703|0.071679|1.4607x|B1|0.105438|1.4710x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_1x4096__sm_103a|G4|R32|0.140304|0.073696|1.9038x|B1|0.147488|2.0013x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_2x8192__sm_100a|G1|R33|0.131263|0.118016|1.1122x|B1|0.134816|1.1424x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_2x8192__sm_103a|G5|R34|0.155040|0.108736|1.4258x|B1|0.161521|1.4854x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_4x2048__sm_100a|G2|R37|0.064416|0.064671|0.9961x|B1|0.107135|1.6566x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_4x2048__sm_103a|G6|R38|0.059872|0.059744|1.0021x|B1|0.145473|2.4349x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_8x1024__sm_100a|G3|R37|0.038207|0.038079|1.0034x|B1|0.047680|1.2521x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_8x1024__sm_103a|G7|R38|0.034816|0.034752|1.0018x|B1|0.044000|1.2661x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_16x512__sm_100a|G0|R51|0.028128|0.028096|1.0011x|B1|0.035263|1.2551x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_16x512__sm_103a|G4|R52|0.025792|0.025824|0.9988x|B1|0.032608|1.2627x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_32x512__sm_100a|G1|R51|0.052736|0.053024|0.9946x|B1|0.068160|1.2855x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_32x512__sm_103a|G5|R52|0.048192|0.048161|1.0006x|B1|0.062688|1.3016x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_64x256__sm_100a|G2|R51|0.069279|0.069407|0.9982x|B1|0.097374|1.4029x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_64x256__sm_103a|G6|R52|0.065120|0.065152|0.9995x|B1|0.093696|1.4381x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_mixed16__sm_100a|G3|R51|0.246205|0.246013|1.0008x|B1|0.250877|1.0198x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_mixed16__sm_103a|G7|R52|0.230368|0.229888|1.0021x|B1|0.235073|1.0226x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_1x2048__sm_100a|G0|R37|0.062655|0.062720|0.9990x|B1|0.099103|1.5801x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_1x2048__sm_103a|G4|R38|0.059104|0.059008|1.0016x|B1|0.143520|2.4322x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_4x512__sm_100a|G1|R37|0.022016|0.022080|0.9971x|B1|0.095776|4.3377x|pass|

|prefill_fp32state_397b_tp8_hq2_hv8_4x512__sm_103a|G5|R38|0.020640|0.020608|1.0016x|B1|0.140512|6.8183x|pass|

## Route legend

|Key|Route|
|---|---|
|R1|cp_band_prefill_fp32state_35b_tp2_hq8_hv16_1x16384__sm_100a|
|R2|cp_band_prefill_fp32state_35b_tp2_hq8_hv16_1x16384__sm_103a|
|R3|cp_band_prefill_fp32state_35b_tp2_hq8_hv16_1x4096__sm_100a|
|R4|cp_band_prefill_fp32state_35b_tp2_hq8_hv16_1x4096__sm_103a|
|R5|cp_band_prefill_fp32state_35b_tp2_hq8_hv16_2x8192__sm_100a|
|R6|cp_band_prefill_fp32state_35b_tp2_hq8_hv16_2x8192__sm_103a|
|R7|cp_band_prefill_fp32state_35b_tp4_hq4_hv8_1x16384__sm_100a|
|R8|cp_band_prefill_fp32state_35b_tp4_hq4_hv8_1x16384__sm_103a|
|R9|cp_band_prefill_fp32state_35b_tp4_hq4_hv8_1x4096__sm_100a|
|R10|cp_band_prefill_fp32state_35b_tp4_hq4_hv8_1x4096__sm_103a|
|R11|cp_band_prefill_fp32state_35b_tp4_hq4_hv8_2x8192__sm_100a|
|R12|cp_band_prefill_fp32state_35b_tp4_hq4_hv8_2x8192__sm_103a|
|R13|cp_band_prefill_fp32state_35b_tp8_hq2_hv4_1x16384__sm_100a|
|R14|cp_band_prefill_fp32state_35b_tp8_hq2_hv4_1x16384__sm_103a|
|R15|cp_band_prefill_fp32state_35b_tp8_hq2_hv4_1x4096__sm_100a|
|R16|cp_band_prefill_fp32state_35b_tp8_hq2_hv4_1x4096__sm_103a|
|R17|cp_band_prefill_fp32state_35b_tp8_hq2_hv4_2x8192__sm_100a|
|R18|cp_band_prefill_fp32state_35b_tp8_hq2_hv4_2x8192__sm_103a|
|R19|cp_band_prefill_fp32state_397b_tp2_hq8_hv32_1x16384__sm_100a|
|R20|cp_band_prefill_fp32state_397b_tp2_hq8_hv32_1x16384__sm_103a|
|R21|cp_band_prefill_fp32state_397b_tp2_hq8_hv32_1x4096__sm_100a|
|R22|cp_band_prefill_fp32state_397b_tp2_hq8_hv32_1x4096__sm_103a|
|R23|cp_band_prefill_fp32state_397b_tp4_hq4_hv16_1x16384__sm_100a|
|R24|cp_band_prefill_fp32state_397b_tp4_hq4_hv16_1x16384__sm_103a|
|R25|cp_band_prefill_fp32state_397b_tp4_hq4_hv16_1x4096__sm_100a|
|R26|cp_band_prefill_fp32state_397b_tp4_hq4_hv16_1x4096__sm_103a|
|R27|cp_band_prefill_fp32state_397b_tp4_hq4_hv16_2x8192__sm_100a|
|R28|cp_band_prefill_fp32state_397b_tp4_hq4_hv16_2x8192__sm_103a|
|R29|cp_band_prefill_fp32state_397b_tp8_hq2_hv8_1x16384__sm_100a|
|R30|cp_band_prefill_fp32state_397b_tp8_hq2_hv8_1x16384__sm_103a|
|R31|cp_band_prefill_fp32state_397b_tp8_hq2_hv8_1x4096__sm_100a|
|R32|cp_band_prefill_fp32state_397b_tp8_hq2_hv8_1x4096__sm_103a|
|R33|cp_band_prefill_fp32state_397b_tp8_hq2_hv8_2x8192__sm_100a|
|R34|cp_band_prefill_fp32state_397b_tp8_hq2_hv8_2x8192__sm_103a|

|R35|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_02758b28da17__sm_100a|

|R36|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_02758b28da17__sm_103a|

|R37|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_133e26131d0c__sm_100a|

|R38|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_133e26131d0c__sm_103a|

|R39|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_300ad6039f75__sm_100a|

|R40|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_300ad6039f75__sm_103a|

|R41|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_7d2cfe13cdc6__sm_100a|

|R42|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_7d2cfe13cdc6__sm_103a|

|R43|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_8571bbd41c3e__sm_100a|

|R44|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_8571bbd41c3e__sm_103a|

|R45|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_d5abb5418532__sm_100a|

|R46|prefill_flashinfer_blackwell_gdn_prefill_dvsplit_initial_d5abb5418532__sm_103a|

|R47|prefill_flashinfer_blackwell_gdn_prefill_initial_2c61b8ed0d75__sm_100a|

|R48|prefill_flashinfer_blackwell_gdn_prefill_initial_2c61b8ed0d75__sm_103a|

|R49|prefill_flashinfer_blackwell_gdn_prefill_initial_5d5f08a3c151__sm_100a|

|R50|prefill_flashinfer_blackwell_gdn_prefill_initial_5d5f08a3c151__sm_103a|

|R51|prefill_flashinfer_blackwell_gdn_prefill_initial_667f95e65ccc__sm_100a|

|R52|prefill_flashinfer_blackwell_gdn_prefill_initial_667f95e65ccc__sm_103a|

|R53|prefill_flashinfer_blackwell_gdn_prefill_initial_752a4089b99c__sm_100a|

|R54|prefill_flashinfer_blackwell_gdn_prefill_initial_752a4089b99c__sm_103a|

|R55|prefill_flashinfer_blackwell_gdn_prefill_initial_b7c6fbbafa43__sm_100a|

|R56|prefill_flashinfer_blackwell_gdn_prefill_initial_b7c6fbbafa43__sm_103a|

|R57|prefill_flashinfer_blackwell_gdn_prefill_initial_caf801606f9b__sm_100a|

|R58|prefill_flashinfer_blackwell_gdn_prefill_initial_caf801606f9b__sm_103a|

## Baseline legend

Each shape row above inlines its applicable external baselines (paired
export ms is the shape's Export ms column); keys resolve here.

|Key|Baseline|Label|Rows|Gate|
|---|---|---|---:|---|
|B1|flashinfer_auto|FlashInfer GDN prefill automatic route (backend
auto, use_cp auto)|132|Baseline / Export > 1.0|

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|132|132|0.080964|0.075879|1.067016x|
|flashinfer_auto|132|132|0.080964|0.075879|1.067016x|
|perf|132|132|0.080964|0.075879|1.067016x|
|prefill|132|132|0.080964|0.075879|1.067016x|

### Geomeans: FlashInfer GDN prefill automatic route (backend auto,
use_cp auto)

|Shape tag|Timed rows|Denominator|Baseline ms|Paired export ms|Baseline
/ Export|
|---|---:|---:|---:|---:|---:|
|all|132|132|0.110274|0.075879|1.453291x|
|flashinfer_auto|132|132|0.110274|0.075879|1.453291x|
|perf|132|132|0.110274|0.075879|1.453291x|
|prefill|132|132|0.110274|0.075879|1.453291x|

Complete denominator: **true** (132/132).

All gates passed: **true** (132/132).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Expanded GDN prefill support for Qwen3-Next and Qwen3.5 head
configurations, including DV-split and full-DV layouts on supported
Blackwell GPUs.
* Added automatic context-parallel routing for eligible long-sequence
prefill requests with FP32 states.
* Added context-parallel GDN processing support and broader handling of
sequence metadata in supported workflows.
  * Added an API for listing available GDN prefill head geometries.

* **Documentation**
* Clarified automatic and explicit Cake GDN prefill routing
requirements, including sequence-length guidance for multi-sequence
batches.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [387eefd](https://github.com/flashinfer-ai/flashinfer/commit/387eefd3854e1e88e2ff6294f170dce9f6e0d9a8)

- **作者**: kangbintNV
- **时间**: 2026-10-14T20:26:47Z
- **提交信息**: docs: fix live documentation audit findings (#5494)

## 📌 Description

Fix all actionable findings from an LLM Doc Check audit of the live
https://docs.flashinfer.ai/ site (193 unique findings across a 411-page
crawl).

This PR:

- corrects API-contract and factual issues, including
speculative-sampling
return types, POD indptr names, sparse-attention mask/output
descriptions,
grouped GEMM arguments, cascade cache naming, and the current KDA
kernel-body
  count;
- fixes malformed RST, typos, grammar, and ambiguous wording across API
docs,
  tutorials, and generated API docstrings;
- updates stale descriptions to match the current implementation,
including
  grouped-MM backends and autotuning cache behavior.

Findings that were already absent from `main` (live-site deployment lag)
or
were generated by inherited standard-library documentation were verified
and
left unchanged rather than introducing incorrect source edits.

## 🔍 Related Issues

#6409

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

All hooks pass for the 47 changed files. The full-repository form was
not used
to avoid rewriting unrelated pre-existing files.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Documentation-only validation performed:

- `python3 -m compileall -q flashinfer docs/tutorials/jax_tvm_ffi`
- `git diff --check`
- `pre-commit run --files <all changed files>`
- Sphinx HTML build (with Linux-only CUTLASS imports mocked on macOS)
- `python3 scripts/check_pr_document.py --base origin/main --head HEAD
--strict`
  (0 new findings)

GPU unit tests were not run because this PR changes documentation,
docstrings,
comments, and a corrected return type annotation only. The
`chain_speculative_sampling` implementation already returned three
tensors;
the annotation correction does not change its call arguments or runtime
behavior.

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

The live docs were audited at depth 1 because every crawled page exposed
the
global navigation; the completed crawl reached 411 same-domain pages
with no
HTTP failures. Please focus review on source-grounded contract
corrections.
After the PR synchronized with newer `main`, the KDA decode portfolio
changed
from 27 to 21 frozen bodies, matching 17 `FLASH_KDA_DECODE_VARIANTS`
plus 4
`CAKE_KDA_DECODE_VARIANTS`; the documentation now reflects the current
source.

Changes are kept narrow; unrelated stylistic rewrites and prose reflow
are
intentionally excluded.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Clarified supported hardware and qualification status for experimental
attention features.
* Updated guidance on backend selection, prefill behavior, autotuning
caches, tracing setup, and supported limits.
* Corrected and clarified API descriptions, parameter details, tensor
shapes, and terminology across tutorials and reference material.
* Fixed grammar, typos, capitalization, and other wording throughout the
documentation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [18f5f1b](https://github.com/flashinfer-ai/flashinfer/commit/18f5f1b009b2d8c8d5a345256fef9b5606cc5302)

- **作者**: kangbintNV
- **时间**: 2026-10-14T20:23:57Z
- **提交信息**: docs: complete MiniMax H3 FC2 weight helper docstrings (#6396)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add NumPy-style `Parameters` and `Returns` sections to the two
MiniMax-H3 FC2 weight preparation APIs. These public functions were
introduced in #6169 with prose-only docstrings, which fails the
Docstring Completeness check. This changes documentation only.

## 🔍 Related Issues

Follow-up to #6169; splits the docstring fix from the MegaMoE
environment-variable documentation change.

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

- `pre-commit run --files
flashinfer/diffusion_ops/cake_minimax_h3_sm120_quant_mlp.py` — passed.
- Project Docstring Completeness and Args Consistency checks for both
APIs — passed.
- GPU tests were not run; this PR changes docstrings only.

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

The existing return-value prose is preserved in structured `Returns`
sections. No signatures or runtime code changed.

### [95b3153](https://github.com/flashinfer-ai/flashinfer/commit/95b315312486d9b1830d89bf76e963c9ad7d9031)

- **作者**: kangbintNV
- **时间**: 2026-10-14T20:23:21Z
- **提交信息**: docs: document MegaMoE compile diagnostics flag (#6412)

<!-- .github/pull_request_template.md -->

## 📌 Description

Document `FLASHINFER_MEGAMOE_LOG_COMPILE_SPEC` in `CLAUDE.md` quick
reference and full environment-variable table. The MegaMoE backend
introduced this read in #4632, and the variable is currently missing
from the documentation consistency check. This changes documentation
only.

## 🔍 Related Issues

Follow-up to #4632; splits this environment-variable documentation fix
from #6396.

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

- `pre-commit run --files CLAUDE.md` — passed.
- Project Env Vars Consistency check for
`FLASHINFER_MEGAMOE_LOG_COMPILE_SPEC` — passed.
- GPU tests were not run; this PR changes documentation only.

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

The runtime enables these diagnostics only when the value is exactly
`1`; no runtime code changed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Documented the `FLASHINFER_MEGAMOE_LOG_COMPILE_SPEC` setting, which
enables compile-choice, workspace-memory, and timing diagnostics when
set to `1`. Other values leave diagnostics disabled.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [fa69943](https://github.com/flashinfer-ai/flashinfer/commit/fa6994348d63b9a13661f104f54ac5b49081d062)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-14T19:37:40Z
- **提交信息**: feat(moe_ep): accept fixed knobs when creating MegaMoE workspaces (#6416)

<!-- .github/pull_request_template.md -->

## 📌 Description

Allow `layer.create_workspace(capacity, knobs=selected_knobs)` to use a
different fixed configuration for each capacity while sharing the
layer's transformed weights. Copy the dictionary and use that
workspace's backend for staging, execution and teardown.

Omitting `knobs` keeps the existing behavior. An override for the
default capacity must be supplied before that workspace is allocated.
The owning layer must use fixed knobs.

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

The workspace tests passed: 49 cases on the host, with the three cases
that query CUDA device properties also passing on GPU. Two GPU-only pool
cases were skipped in the host run. The new cases cover dictionary
copies, pooling, backend selection, live-token profiles, teardown and
the default-workspace guard.

The NVFP4 test passed on two B200 GPUs with two capacities and different
explicit knob dictionaries, including graph replay after changing the
inputs. `pre-commit run --all-files` passed on this branch.

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
* Workspaces can now use their own fixed kernel settings. If settings
are omitted, the workspace inherits the layer’s configuration.
* Multiple workspaces can coexist for the same capacity when their
live-token counts differ. Each workspace retains its configuration for
operations and cleanup.
* Configure the default-capacity workspace before allocating it to use
an override. Create and destroy workspaces collectively, in the same
order, with matching capacities and settings.
* **Documentation**
* Clarified workspace configuration, inheritance, and lifecycle
requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [527df05](https://github.com/flashinfer-ai/flashinfer/commit/527df05b5095c5c9ac9929563dd3bcbe38cfc25a)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-14T19:20:19Z
- **提交信息**: fix(moe_ep): correct graph warmup and non-root test setup (#6379)

<!-- .github/pull_request_template.md -->

## 📌 Description

Warm the W4A16 graph tests with their actual input tensors. Default
warmup uses int64 routing IDs, while these tests use int32 IDs, causing
the first forward to fail the steady-state signature check.

Allow EP dependency setup to run without root by skipping system linker
configuration. Export the NCCL wheel library path from the test launcher
so its workers load the required library; root image builds retain the
persistent linker setup.

## 🔍 Related Issues

<!-- Link any related issues here -->

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

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Installation**
* Non-root installations provide guidance for setting `LD_LIBRARY_PATH`
so launched applications can find NCCL libraries.
  * Root installations configure the NCCL library path for the system.

* **Bug Fixes**
* Improved reliability of CUDA 13+ MoE test runs by making NCCL
libraries available to test processes while preserving existing library
paths.
* Updated graph-capture warmup behavior for the `w4a16` backend,
including tests with different input sizes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ba87b19](https://github.com/flashinfer-ai/flashinfer/commit/ba87b199601858ce18ba919369cbedad7d917708)

- **作者**: eigen
- **时间**: 2026-10-14T19:19:41Z
- **提交信息**: perf(cake_dsv4): overlap the next tile's V transform with PV in the NVFP4 sparse-MLA decode persistent member (SM100/SM103) (#6357)

## Summary

Re-exports the SM100 / SM103 DeepSeek-V4 NVFP4 sparse-MLA decode family
(`backend="cake"`, `kv_cache_format="nvfp4"`)
with one kernel change in the **persistent member**
(`nvfp4_decode_persistent`, the member that serves the 128-head
throughput rows): the next tile's V transform now runs under the current
tile's PV MMAs. The member set, the host route,
the loader registrations and the public API are unchanged; the other
members' generated sources are regenerated from the
same exporter and are byte-identical to the previous delivery except for
the regenerated receipts.

- **What changes in the kernel.** The persistent member's shared memory
was full (230944 B of 232448 B), so the compute
warps could not start transforming the next tile's V (E2M1 x E4M3 ->
E4M3, MN-major) until the MMA warp had finished
reading the single V buffer; the transform sat exposed between PV(t) and
QK(t+1) on every tile. The Q NoPE E2M1 tile is
written once and read by every tile, and the tensor core can take it
from TMEM: the kernel now stores the Q codes into
64 free TMEM columns and issues QK as `tcgen05.mma.kind::mxf4nvf4` with
the A operand from TMEM (same K-set order, same
scale operands; the instruction descriptor bytes are identical, checked
by the proof step). The 32 KiB this frees is a
second V buffer for the odd tiles, so PV stages 2 / 3 are
double-buffered and V(t) is formed while PV(t - 1) runs; the PV
issue order becomes (PSUM, 2, 0, 1, 3) with stage 2 landing in the S
columns that two compute groups drain. Every new
  compute -> MMA hand-off is `tcgen05.fence::before_thread_sync`-fenced.
- **Numerics.** Scheduling and operand placement only: the same MMAs on
the same operands in the same order, so the
outputs are **bitwise identical** to the previous delivery on every
validated shape and seed (seed gate 96 rows x 3
seeds per card, accuracy tables 189 + 228 records per card, CUDA-graph
replay x 3, source/export bitwise on all 76
exported shapes per card); compute-sanitizer synccheck is clean on both
cards (racecheck reaches the tool limit
  identically on the previous and the new kernel).
- **Why.** Measured with the same cold-L2 CUPTI paired protocol as the
previous deliveries, the six 128-head rows that
route to the persistent member run 0.96–0.98x of their previous time on
B200 (0.962–0.975, geometric mean 0.969) and
0.95–0.99x on GB300 (0.946–0.990, geometric mean 0.967); the eight
reference rows on other members read 0.99–1.01 on
both cards, matching their same-code A/A twins. Register pressure rose
slightly (ptxas spill 564 -> 612 B on sm_100a,
540 -> 564 B on sm_103a at 128 registers) while the SASS shrank by about
450 instructions; this is disclosed because the
pre-registered spill rule read "increase" and was relaxed for this
candidate on review.

| Row (member) | B200 new / previous (us) | B200 same-code A/A | GB300
new / previous (us) | GB300 same-code A/A |
|---|---|---|---|---|
| C-h128-k512-t128 (persistent, re-measured) | 0.965 (33.54 → 32.35) |
0.997 | 0.964 (30.14 → 29.07) | 0.993 |
| D-h128-m512-e512p64-t32 (persistent, re-measured) | 0.974 (27.01 →
26.30) | 1.001 | 0.960 (25.38 → 24.37) | 0.999 |
| H-11 (persistent, re-measured) | 0.964 (50.80 → 48.99) | 0.997 | 0.977
(45.07 → 44.02) | 1.003 |
| C-h128-k512-t128 — contract twin (persistent, re-measured) | 0.974
(33.44 → 32.56) | 0.994 | 0.990 (30.14 → 29.86) | 1.010 |
| D-h128-m512-e512p64-t32 — contract twin (persistent, re-measured) |
0.975 (26.99 → 26.30) | 0.999 | 0.946 (25.60 → 24.21) | 1.002 |
| H-11-num128-top512-ext512 (persistent, re-measured) | 0.962 (51.28 →
49.34) | 0.998 | 0.967 (45.52 → 44.00) | 0.999 |
| C-h32-k128-t32 (route unchanged, reference) | 1.000 (8.00 → 8.00) |
1.000 | 0.991 (7.39 → 7.33) | 0.991 |
| C-h64-k128-t8 (route unchanged, reference) | 1.008 (8.19 → 8.26) |
1.008 | 1.000 (7.46 → 7.46) | 0.985 |
| C-h64-k512-t128 (route unchanged, reference) | 0.994 (24.96 → 24.82) |
1.000 | 0.990 (23.18 → 22.94) | 1.006 |
| C-h128-k128-t32 (route unchanged, reference) | 1.004 (11.31 → 11.36) |
1.003 | 1.009 (10.56 → 10.66) | 1.009 |
| C-h128-k128-t128 (route unchanged, reference) | 1.006 (16.22 → 16.32)
| 1.008 | 1.011 (14.72 → 14.88) | 1.011 |
| D-h128-m128-e132p2-t32 (route unchanged, reference) | 0.996 (18.91 →
18.83) | 1.003 | 1.002 (17.60 → 17.63) | 0.994 |
| D-h128-m128-e512p64-t32 (route unchanged, reference) | 1.008 (24.45 →
24.64) | 0.999 | 0.992 (23.22 → 23.04) | 0.999 |
| X-h128-k256-t32 (route unchanged, reference) | 1.001 (16.77 → 16.78) |
1.008 | 0.993 (16.13 → 16.02) | 1.002 |

Ratios below 1.0 are faster. Each cell is the ratio of cold-L2 CUPTI
medians of the Cake `sparse_mla_decode` entry with the new
persistent-member schedule over the same entry with the previous one,
five counterbalanced ABBA rounds in one process; the same-code A/A
column repeats the measurement with two copies of the previous program
and bounds the noise band (0.030 floor). Bit-identity on every row: seed
gate 96 / 96 rows x 3 seeds and A/B 14 / 14 per card.

## CI coverage note

The PR CI has no SM100 / SM103 runner, so the `backend="cake"` NVFP4
decode tests skip there on the architecture guard;
the route test (`tests/mla/test_cake_dsv4_nvfp4_route.py`, CPU-only)
exercises the plan rows in CI. GPU evidence is the
two-card run below (CUDA 13.4 toolchain). The `cake_dsv4` loader is
JIT-only (not part of the AOT build).

## Proof of identity

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
count; the rule of the previous deliveries). The persistent member is a
single program (no template knob) and is covered by the source/export
bitwise check on all of its rows.

## Measurement (same protocol as the previous deliveries: cold-L2 CUPTI,
counterbalanced interleaved groups, 76 shapes per card)

Each column is the geometric mean over shapes of Cake source-tree kernel
time over FlashInfer-route time (source / export;
1.0 = parity), all rows and the per-table subsets C / D / M / O / X / H.

| Card | timed rows | correct | rows >= 0.97 (previous delivery in
parentheses) | source/export geomean all / C / D / M / O / X / H |
previous delivery (same geomeans) |
|---|---|---|---|---|---|
| B200 (sm_100a) | 76 | 76 | 73 (74) | 0.999 / 0.998 / 1.005 / 0.998 /
1.003 / 0.994 / 0.996 | 1.000 / 1.002 / 1.001 / 0.998 / 0.998 / 0.994 /
0.997 |
| GB300 (sm_103a) | 76 | 76 | 68 (71) | 0.997 / 0.999 / 1.004 / 0.978 /
1.000 / 1.000 / 0.994 | 1.001 / 1.005 / 1.009 / 0.985 / 1.007 / 0.996 /
0.999 |

Disclosed (the per-row source/export floor 0.97 is informational, same
acceptance as the previous deliveries; the previous-delivery column is
that export's own compare receipt): B200 rows below the floor:
C-h32-k128-t1 0.939, C-h64-k512-t8 0.923, X-h128-k256-t72 0.964 (the
previous delivery listed C-h64-k512-t8 0.940 and X-h128-k256-t72 0.963).
Four B200 rows (C-h64-k512-t32 1.024, D-h16-m128-e512p64-t32 1.014,
D-h16-m512-e512p64-t32 0.991, X-h128-k256-t32 1.005) failed the
exporter's A/B-order validity gate (directional disagreement 0.052–0.077
against 0.050) under the same four-shapes-at-a-time condition; included
in the geomeans, no per-row verdict. GB300 rows below the floor:
C-h32-k128-t1 0.914, C-h64-k512-t8 0.908, C-h64-k512-t32 0.964,
O-h128-k512-t32 0.942, M-h64-m128-e512p64-t12 0.937, M-h128-k128-t12
0.958, M-h128-m128-e512p64-t12 0.943, H-10-num128-top512-pag32 0.964
(the previous delivery's GB300 list had 5 rows; the same portable-QMUL4
rows recur). Five GB300 rows (C-h128-k512-t128 0.992,
D-h128-m128-e132p2-t32 1.008, D-h16-m512-e512p64-t32 1.002,
D-h128-m512-e512p64-t32 1.002, X-h128-k256-t32 1.009) failed the
exporter's A/B-order validity gate (directional disagreement 0.052–0.094
against 0.050) while four shapes were measured concurrently on
independent GPUs; their ratios are included in the geomeans but carry no
per-row verdict. Against the stored previous-export geomeans the
family-level bars hold on both cards (all rows within 0.01, every table
within 0.02).

## Tests

FlashInfer tests on the delivered tree, per card (CUDA 13.4 toolchain,
JIT): `tests/attention/test_sparse_mla_blackwell_dsv4_nvfp4.py`,
`tests/mla/test_cake_dsv4_nvfp4_route.py` and
`tests/mla/test_cake_dsv4.py` -- **B200: 439 passed, 0 failed; GB300:
439 passed, 0 failed** (no test patch: the allowlist changes of the
previous deliveries are already in `main`). Source side: the e2e compile
/ analysis / GPU correctness slice, the planner tests and the
benchmark-regression floors pass on both cards at the delivered
revision; compute-sanitizer synccheck clean on both cards; CUDA-graph
replay x 3 bitwise.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Updated NVFP4 descriptor dimensions for query buffers and corrected
descriptor-encoding error messages.
  * Updated the NVFP4 kernel selection for the generated launcher.

* **Chores**
* Refreshed generated build identities for supported NVFP4 variants.
Other changes are formatting and attribution updates with no stated
behavior changes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5ee9bd4](https://github.com/flashinfer-ai/flashinfer/commit/5ee9bd4f8edb9e2d764f4a508ef24c36caf7bf38)

- **作者**: Adrian
- **时间**: 2026-10-14T18:56:52Z
- **提交信息**: ci(tests): separate node, GPU, and host-heavy isolation (#6438)

<!-- .github/pull_request_template.md -->

## 📌 Description

Concurrent test workers can stall behind files waiting for host or GPU
isolation, while the `solo` marker conflates allocation-wide isolation
with memory pressure. This change separates those requirements and
leaves blocked units queued so workers can dispatch runnable work.

- Replace `solo` with `node_exclusive` for files that must run alone
across the allocation. Remove unnecessary isolation from low-RAM cuTile
and routed MoE files.
- Add `gpu_exclusive` and `host_memory_heavy` for narrower isolation.
Reserve both atomically, allow work stealing, and drain one GPU for
pending exclusive work without blocking other GPUs.
- Support GPU sharing through `--workers-per-gpu` or `--workers`. Full
and targeted H100 PR CI explicitly use two workers per GPU; other lanes
retain the default.
- Run attention sink in the parallel phase with host-heavy and
GPU-exclusive limits so other GPUs can continue working.
- Isolate scheduling logic in `scheduling.py`, handle exiting processes
during telemetry scans, and include host-heavy serialization in capacity
estimates.
- Use schema 5 for the marker contract. Historical plans retain their
isolation classification when read for reports; incompatible resume is
refused.

## 🔍 Related Issues

Related work: #6263 and #6388.
Merging this #6438 obsoletes both #6263 and #6388.

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

Changed-file hooks passed, including at commit time. `pre-commit run
--all-files` was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Coordinator validation before the workflow integration: **179 passed**.
The H100 follow-up passed **seven focused coordinator tests** and **six
workflow argument-routing cases**, covering H100/non-H100 lanes with and
without scoped paths. Workflow YAML and Bash syntax checks also passed.

```bash
FLASHINFER_WORKSPACE_BASE=/tmp/flashinfer-scheduling-validation \
python -m pytest --confcutdir=tests/test_sharding tests/test_sharding -q
```

Coverage focuses on concurrent resource isolation, GPU drainage and
stealing, reservation cleanup, shutdown wakeups, historical manifests,
and serial-capacity estimates. Basic parser/order-only tests and
duplicate coverage were omitted. Fault injection confirmed that a
missing shutdown notification is detected without hanging the test.

Model/scheduler type checks and Bash syntax checks passed. GPU tests and
performance measurements were not run because the local NVIDIA driver is
unavailable.

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

The markers enforce overlap rules rather than measured memory limits.
Existing peak-memory comments describe CI observations and can vary with
cold JIT compilation, cache-wheel availability, and hardware. Capacity
estimates account for host-heavy serialization but remain optimistic
about GPU contention because the estimator does not receive GPU
topology.

Standards and behavior reviews found no remaining actionable findings
after correcting the capacity estimate and shutdown-test cleanup
ordering. No end-to-end CI speedup is claimed for this implementation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Test runs now default to a worker pool sized for the visible GPUs,
with options to set a total worker count or workers per GPU.
* Resource-aware scheduling coordinates GPU-intensive,
host-memory-intensive, and exclusive tests while allowing compatible
work to run concurrently.
* Workers can cycle across visible GPU slots when the configured worker
count exceeds the number of GPUs.
* Scheduling reports resource wait times and includes exclusive work in
capacity estimates.
* **Documentation**
* Added guidance on scheduling behavior, resource limits,
capacity-estimate caveats, and running coordinator tests. H100 pull
request checks now use two workers per GPU.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7d3a7da](https://github.com/flashinfer-ai/flashinfer/commit/7d3a7dafa907ba32039582adddcb43c89dbd3557)

- **作者**: eigen
- **时间**: 2026-10-14T18:51:39Z
- **提交信息**: perf(cake_diffusion): MiniMax-H3 SM120 FC1+SwiGLU — FP8 mxf8f6f4 unit-scale form on GeForce, raster group 64, NVFP4 producer-warpgroup form (#6475)

## 📌 Description

Regenerates `csrc/cake_minimax_h3_sm120_quant_fc1_swiglu_sm120a.cu`
(introduced in #5521, last regenerated in #5905) from the upstream
generator at `e5342d3a10d` with the three production forms that the
fused SM120 MLP operator already uses:

- **FP8, GeForce boards (RTX 5090 / GB202):** `kind::mxf8f6f4` MMA with
a unit UE8M0 scale instead of the legacy plain-e4m3
`mma.sync.aligned.m16n8k32.row.col.f32.e4m3.e4m3.f32` form — 2048 vs
1024 FLOP/clk/SM issue limit on GeForce. The host tail selects the FP8
form per device at the first call (`cudaDeviceProp::name` containing
"GeForce" selects the `mxf8f6f4` form; every other GB202 board gets the
legacy form; cached per device); RTX PRO 6000 keeps the legacy form,
which issues at 2048 on that board and measured faster there.
- **FP8, both boards:** raster group 64 (was 16).
- **NVFP4, both boards:** producer-warpgroup form (384 threads: 8
`mma.sync` warps + a dedicated TMA producer warpgroup) instead of the
folded producer.

**Numerics.** All forms are bitwise identical to the previous generated
kernel on the full validation grid (`torch.equal`, 14 rows per variant
per board, incl. M = 1 / 127 / 128 / 129 and the ±1 / ±64 tails): the
`mxf8f6f4` unit-scale form reproduces the legacy FP8 form bit-for-bit,
and the raster / producer changes do not touch the per-tile K order. The
fused SM120 MLP operator
(`csrc/cake_minimax_h3_sm120_quant_mlp_sm120a.cu`), which shares the
mainloop helpers, is not touched by this PR: its generated kernel CUDA
is byte-identical before and after this change and its tests
(`test_minimax_h3_sm120_quant_mlp.py`, 22 passed) pass unchanged on both
boards in the same session.

**Performance** (sustained protocol: >= 2 s CUDA-graph replay at the
board's power limit, operator = norm/AdaLN+quantize kernel + GEMM, 6
timed production shapes, two rounds; geometric mean [min, max]):

| board | variant | vs previous kernel | vs fastest same-session
segmented chain (torch norm/AdaLN -> quantize -> fastest quantized GEMM
-> silu_and_mul) |
|---|---|---|---|
| RTX 5090 | FP8 | 1.320 [1.300, 1.360] / 1.309 [1.303, 1.321] | 1.775 /
1.761 (3 shapes; the 3 largest OOM on the 32 GB board for the chain) |
| RTX 5090 | NVFP4 | 1.031 [1.006, 1.060] / 1.028 [1.009, 1.047] | 1.519
/ 1.513 (4 shapes) |
| RTX PRO 6000 Blackwell Server Edition | FP8 (legacy + group 64) |
1.032 [1.028, 1.043] / 1.031 [1.029, 1.040] | 2.062 [2.044, 2.077] /
2.060 [2.044, 2.068] (6 shapes) |
| RTX PRO 6000 Blackwell Server Edition | NVFP4 | 1.062 [1.055, 1.080] /
1.061 [1.056, 1.076] | 1.701 [1.684, 1.710] / 1.700 [1.678, 1.710] (6
shapes) |

Achieved MMA issue rate at the in-kernel sustained clock: RTX 5090 FP8
0.93 / 0.92 of the 2048 FLOP/clk/SM limit at M = 38592 / 109952
(previous kernel 0.98 / 0.98 of 1024), NVFP4 0.96 / 0.92 of 4096
(previous 0.88 / 0.87). RTX PRO 6000: FP8 0.93 / 0.93 of 2048 (previous
0.92 / 0.92), NVFP4 0.92 / 0.93 of 4096 (previous 0.84 / 0.84), both
bitwise-identical to the previous kernel in the same runs.

## 🔍 Related Issues

#5905, #4254 (FC1 + SwiGLU section)

## 🚀 Pull Request Checklist

- [x] Pre-commit checks pass.
- [x] Tests:
`tests/diffusion_ops/test_minimax_h3_sm120_quant_fc1_swiglu.py` (and
`test_minimax_h3_sm120_quant_mlp.py`, unchanged mainloop) on RTX 5090
and RTX PRO 6000: 17 + 22 passed on each board, identical result with
the previous source in the same session.
- [x] Generated source only; no Python API change (the commit touches
`csrc/cake_minimax_h3_sm120_quant_fc1_swiglu_sm120a.cu` only).

## Reviewer Notes

Generated file; the generator diff is in the upstream repository.
sha256:
`0133fda3b61e5cd1678115f74f79384323c9c3b1e01d7cc4a44d7eb610ead051` (7504
lines).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b50f11d](https://github.com/flashinfer-ai/flashinfer/commit/b50f11ded2e4439ab6afe09d7bec6be299a5358e)

- **作者**: eigen
- **时间**: 2026-10-14T18:50:12Z
- **提交信息**: perf(cake_diffusion): bitwise norm/AdaLN prologue rewrite for MiniMax-H3 FC1+SwiGLU and fused MLP (SM100/SM103) (#6474)

## 📌 Description

Regenerates the SM100/SM103 CUDA sources of the MiniMax-H3 fused RMSNorm
+ AdaLN + FC1 + SwiGLU operator (#6039) and of the fused MLP operator
that shares its norm/AdaLN kernels, from the upstream generator at
`83264f1c122`:

- `csrc/cake_minimax_h3_fc1_swiglu_sm100a.cu`,
`csrc/cake_minimax_h3_fc1_swiglu_sm103a.cu`
- `csrc/cake_minimax_h3_mlp_sm100a.cu`,
`csrc/cake_minimax_h3_mlp_sm103a.cu`

**What changed in the kernels.** Functionally, only the
norm/AdaLN(+quantize) prologue kernels: the BF16 round points use the
packed `__float22bfloat162_rn` intrinsic (one `cvt.rn.bf16x2.f32`) each,
the RMSNorm sum of squares is accumulated with `fma.rn.f32.bf16`
directly from the packed BF16 words (same sequential FP32 FMA chain),
and `BF16(scale + 1)` is one `add.rn.bf16x2`. Instruction-form only:
every output is **bitwise identical** to the previous generated kernels
on the full validation grid of all three variants (BF16 / MXFP8 / NVFP4)
on both architectures (verified with `torch.equal`, 56 rows per variant
per architecture per round, two rounds, incl. M = 1, unaligned tails and
out-of-range AdaLN indices). The GEMM kernels are functionally
unchanged: the MLP GEMM kernels are byte-identical to the previous
sources, and in the two FC1 files the only change inside the GEMM
kernels is that the newer generator spells the shared-memory buffer
offsets through the existing `SMEM_*_OFF` constants instead of literals
(identical values; the kernel text is identical after macro
substitution). Static SASS instruction count of the prologue kernels
(`cuobjdump` of the sm_103a cubin; 168 elements per lane): BF16 3152 ->
2056 (18.8 -> 12.2 per element), MXFP8 4240 -> 3320 (25.2 -> 19.8),
NVFP4 3992 -> 3072 (23.8 -> 18.3), counted on the development build of
the same kernels, whose generated CUDA differs from the delivered
sources only in the spelling of the three BF16 round sites (same
`F2FP.BF16.F32.PACK_AB` SASS class); the delivered cubins were not
re-counted and sm_100a was not counted.

**Hygiene.** The previous `cake_minimax_h3_fc1_swiglu_sm10{0,3}a.cu` in
`main` predate the generator fix for the MXFP8 norm kernel's guard-row
literal-zero word (CUDA 12.9 ptxas constant-pack hazard); the
regenerated sources carry that fix. They also predate three cosmetic
generator changes that the fused-MLP sources in `main` already carry, so
these appear in the FC1 diff only: the norm kernels spell their block
size as `__launch_bounds__(THREADS)` (with `#define THREADS 128`
directly before each kernel), the BF16 -> FP32 widening of `x`,
`x_norm_weight` and `adaln_shift` uses plain C++ shifts/masks instead of
inline `asm volatile`, and the GEMM kernels' shared-memory pointer setup
refers to the file's existing `SMEM_*_OFF` macros instead of repeating
their literal values (same offsets). None of these changes kernel
semantics; all are covered by the bitwise comparison above.

**Performance** (sustained protocol: >= 2 s CUDA-graph replay at the
power wall, exclusive node, operator = norm/AdaLN kernel + GEMM,
geometric mean over the 40 timed shapes (the 24 production centres plus
tail/odd-M rows), two rounds; bracketed = [min, max] over the 40 rows of
both rounds):

| arch | variant | vs previous kernels (sustained) | vs fastest
segmented baseline chain (FlashInfer rmsnorm -> torch modulate ->
[FlashInfer quantize] -> fastest available GEMM (FlashInfer / cuBLAS) ->
FlashInfer silu_and_mul) |
|---|---|---|---|
| sm_103a (B300) | NVFP4 | 1.023 / 1.025 [1.012, 1.039] | 1.988 / 1.992
(min 1.763) |
| sm_103a | MXFP8 | 1.012 / 1.011 [1.002, 1.026] | 1.468 / 1.466 (min
1.294) |
| sm_103a | BF16 | 1.006 / 1.006 [0.994, 1.013] | 1.093 / 1.093 (min
1.077) |
| sm_100a (B200) | NVFP4 | 1.027 / 1.029 [1.013, 1.043] | 1.519 / 1.521
(min 1.466) |
| sm_100a | MXFP8 | 1.015 / 1.012 [0.996, 1.028] | 1.525 / 1.522 (min
1.316) |
| sm_100a | BF16 | 1.006 / 1.004 [0.990, 1.025] | 1.111 / 1.109 (min
1.091) |

Standalone norm/AdaLN prologue kernels (sm_103a only, not measured on
sm_100a; a separate, smaller measurement on the development build of the
same kernels: four shapes M = 4824 / 9648 / 38592 / 109952, three
sustained rounds, geometric mean vs the previous prologue kernels,
shared node): 1.18-1.19x BF16 / 1.26x MXFP8 / 1.29x NVFP4.

## 🔍 Related Issues

#6039, #4254 (FC1 + SwiGLU section). FC1 source history: #5491
(introduced), #5506 / #5513 (GEMM tile changes), #6039 (last
regenerated).

## 🚀 Pull Request Checklist

- [x] Pre-commit checks pass.
- [x] Tests: `tests/diffusion_ops/test_minimax_h3_fc1_swiglu.py`,
`tests/diffusion_ops/test_minimax_h3_mlp.py` JIT-built from the
regenerated sources: sm_103a 20 passed / 26 passed (0 failed; identical
counts with the previous sources in the same step); sm_100a 20 passed /
26 passed (0 failed; identical counts with the previous sources in the
same step).
- [x] Generated sources only; no Python API change.

## Reviewer Notes

The csrc files are generated; the generator diff is in the upstream
repository. sha256 of the four files:
`cake_minimax_h3_fc1_swiglu_sm100a.cu`
`bf6f49b01d159d67c2676f56a389a7a7f7d241343a846ad041dd380aa8110c5b`,
`cake_minimax_h3_fc1_swiglu_sm103a.cu`
`a27cc398c13271bc76a802eff8c25e63e3a41660b413163c835ee5339c3fc10a`,
`cake_minimax_h3_mlp_sm100a.cu`
`062f4f4856c35da50b4bd54972db1c8714a0de76d661ccd98728959b03bbbde0`,
`cake_minimax_h3_mlp_sm103a.cu`
`50346495af3f579b985a637378ace81d6700745dac2caadc2cf7982515428b7c`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Improvements**
* Updated normalization and activation processing for BF16, MXFP8, and
NVFP4 across supported hardware.
* BF16 rounding is now applied at specific points in AdaLN modulation
and quantization, which may result in small numerical differences.
  * Invalid MXFP8 inputs continue to produce zeroed activations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [2895577](https://github.com/flashinfer-ai/flashinfer/commit/2895577720741ddfedff118202c89584996b8875)

- **作者**: Hong Wang
- **时间**: 2026-10-14T13:04:29Z
- **提交信息**: Fix SM120 W4A8 scalar-scale MMA on CuTe DSL 4.9 (#6417)

## 📌 Description

Fix SM120 W4A8 MegaMoE compilation with CuTe DSL 4.9. FlashInfer
supplies scalar 8-bit E8M0 scale factors on this MMA path, but also
passed byte selectors intended for packed 32-bit scale factors. **CuTe
DSL 4.9** rejects that combination during IR verification.

Remove the byte selectors from this scalar-scale path. The packed-scale
path is unchanged.

This change affects only the internal SM120 W4A8 MMA helper; it does not
change FlashInfer’s public API, kernel inputs or outputs, or data
layout.

### CuTe DSL 4.8 compatibility

Validated this change on an RTX 5080 (SM120) using this flashinfer
branch commit `49eb03f1` and CuTe DSL `4.8.0` (all five DSL packages at
the same version). The single-GPU tests in
`tests/moe_ep/test_moe_ep_sm120_w4a8_cutedsl_mega.py` completed with
**30 passed, 12 deselected, 0 failed**.

This confirms that the change does not break the tested W4A8 MegaMoE
path on CuTe DSL 4.8.0. Versions earlier than 4.8.0 were not tested.

## 🔍 Related Issues


## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Existing tests cover the affected path; no new test was needed.
- [x] On RTX 5080 (SM120), with the DSL 4.9 wheel from the bug report:
all 7 previously failing cases passed; the full single-GPU test
selection passed (30 passed, 12 deselected).

## Reviewer Notes

Validation used FlashInfer commit `ae312f7c` plus this change and DSL
wheel `4.9.0a0+20261010230000.b110033`. The 4-GPU cases were outside the
single-GPU test selection.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
* Updated internal matrix-multiplication handling to use thread-based
selectors without byte-based selectors for packed scale data. This
changes how the operation is configured internally; no changes to
user-facing functionality or public interfaces are indicated.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [87ef739](https://github.com/flashinfer-ai/flashinfer/commit/87ef73934ef61e4d85444b91aeaa8e0df667f6ae)

- **作者**: eigen
- **时间**: 2026-10-14T08:35:40Z
- **提交信息**: perf(cake_msa): faster Blackwell MSA prefill programs — union-route selection census, Q-resident long-route order, two-stage folded-GQA rings, shared-TMEM QK/PV issue order, tile interleave, host-side cu_seqlens_k removal (rounds 4–9 levers) (#6463)

> Developed by the **CAKE team**, this PR regenerates the **prefill**
routes of the Cake-generated MiniMax Sparse Attention family for
> SM100 / SM103 with every prefill lever the CAKE-1183 ceiling round
accepted since the family's last prefill delivery (#6397): the paged
> `first_topk` rows run **1.8–2.7× faster** (2.0–2.7× on 8 of the 10
rows; B200 128K 1.76×, GB300 64K 1.94×; e.g. paged b1 q8192: 965 → 411
µs on B200, 885 → 332 µs on GB300; round-9 merged-head
> acceptance, medians of the two interleaved passes), the flat GQA-16
q4096 row **1.18× / 1.11×**, the long flat rows 1.01–1.04× on the
round-9 rows (the q8192 row PARITY) and
> 1.02–1.08× on the WIN rows of the rounds-4–8 head (the remaining long
flat rows PARITY), with **0 LOSS** on the 10 round-9 rows per
architecture
> and on the 18 (GB300) / 17 measured (B200, 1 GAP: baseline arm
OOM-infeasible) rounds-4–8 rows. Every lever is a schedule,
pipeline-depth, work-list, tile-order, host-plan or
> host-launch change; outputs are bitwise identical to the replaced
programs except on the four paged 16K–128K `first_topk` rows that move
> onto the selection-union route (closer to the FP32 reference than
before, see "Precision"). Based on `main` `ba4defb9`
> (#6459, #6443, #6397 and #6410 are merged).

## Summary

Regenerates the prefill routes of the Cake-generated MiniMax Sparse
Attention family for SM100 / SM103 (`csrc/blackwell_msa/`,
`flashinfer/jit/blackwell_msa.py`,
`flashinfer/msa_ops/_blackwell_sm100.py`) from the Cake generator at
`6941a6ee67a980d01c85547b7d1b6b42119b9643` (CAKE-1183 MSA ceiling round;
= the FlashInfer-export integration head `803d25e1` — the
Top-K round-9 producer `5dbd76a3` of #6459 merged with the prefill
round-9 MR head `ee3544b3` — plus one host-mirror-only commit
that makes the regenerated `_blackwell_sm100.py` ruff-clean: a format
re-wrap and explicit `strict=` on three `zip` calls; see "Provenance")
onto
`7cd20a82caeceb1e4b4a925ac13ddc3458474e94` (= main after #6315), **on
`main` `ba4defb9`** (which contains the squash-merged #6459 and #6443
`d0546b42`): this PR's
commit carries only the prefill delta on top of `main`; the
7cd20a82-based stacked tree is byte-identical to the export's delivery
(asserted by the commit step) and was moved object-level onto the
rebased chain with the delta unchanged (see "Stacking"). Same
per-program layout as #5893 / #6315 / #6397 / #6410.

The prefill routes were last delivered by #6397 (Cake producer
`37d6d177`), so this delta carries every prefill lever accepted since,
by
Cake MR:

| Cake MR (head) | round | levers | what |
|---|---|---|---|
| !1403 (`c12393f7`) | 4–8 | P2, PNV-A1, P-H1, P-H1b, PNV-A2 / P-U1,
P1b, P9b | long-route LPT tail-wave split and Q-resident work order;
two-stage folded-GQA K/V rings; load-warp union block list on the paged
GQA-16 `causal_mask64` program; `cu_seqlens_k` built as one int32 scan
at launch (superseded by P-H1d below); NVFP4 second raw TMA slot (NVFP4
prefill is not shipped by this family) |
| !1409 (`ad2c9390`) | 8 | P10, P-X2b′ | paged prefill routes by an
exact selection-union census with a list-position mask; the four BF16
GQA-16 union retraces share one TMEM score region and issue QK(b+1)
ahead of PV(b) |
| !1416 (`ee3544b3`) | 9 | P-H1d, P-U4b (tree B) | paged prefill binds
an all-zero `cu_seqlens_k` carrier, the scan kernels are gone
(host-only, CUDA identical); the flat GQA-16 causal program interleaves
heavy / light Q tiles and rotates the KV head across consecutive CTAs |

No dtype, tolerance, public signature, CUDA-graph workspace key or test
change: the host mirror keeps the `prefill_cu_seqlens_k`
workspace key and its `(batch + 1,)` int32 extent; the buffer is now
zero-filled once when the warmed workspace creates it
(`_paged_prefill_cu_seqlens_k`) instead of being refilled per call by
`cu_k[0].zero_()` + `torch.cumsum` (`_cumulative_kv_lengths`, removed;
Cake's intermediate P-H1 / P-H1b cub-scan path
`_cumulative_kv_lengths_{buffer,scan}` / `_launch_route(before_launch=)`
was never shipped to FlashInfer). No file under `tests/` or
`csrc/cake_device_helpers/` changes.

## What changed

Device code vs #6459: 18 new program files (9 modules: `249de815`,
`d24af147`, `c3da0a78`, `044ebdf2`, `0e42bddc`, `e9c87303`,
`39657d21`, `9c2eacf9`, `04f607ba`), 20 removed (10 modules: `9b8df5a0`,
`67f613e9`, `70a89c8d`, `1e1433e9`, `ca3cbae6`, `dfcd2b63`,
`943f0e35`, `d7a39c2b`, `a1682947`, `b2b929b1`; the paged GQA-16 long
route and its sm100a-only `direct_group` variant now share
`d24af147`), `flashinfer/jit/blackwell_msa.py` (+322 / −384: 10
`MODULES` records replaced by 9, 19 `ROUTES` entries re-pointed = 10
route
keys on both arches, `direct_group` being sm100a-only),
`flashinfer/msa_ops/_blackwell_sm100.py` (+447 / −38) and one comment
line in
`csrc/blackwell_msa/cake_blackwell_msa_device_common.cuh`
(helper-library count 61 → 60): 23 files, +2431 / −3876 (stack-commit
step
`027693cd`, `fi_commit.json`; git records the 18 new files as renames of
the replaced ones). Every decode and Top-K module,
`tests/msa_ops/test_blackwell_msa_routes.py` (unchanged),
`tests/jit/test_blackwell_msa_jit.py` and `csrc/cake_device_helpers/`
are byte-identical to #6459 (the export
regenerates the whole family; the Cake render census of the integration
head against each of its parents differs in exactly the prefill
keys vs the Top-K producer and exactly the decode / NVFP4 /
streaming-Top-K keys vs the prefill head, with no key in both sets).

| route(s) | module on #6459 (= #6397 for prefill) | module in this PR |
levers | mechanism |
|---|---|---|---|---|
| `long_bf16_reverse:{flat:gqa16, paged:gqa16, paged:gqa8}:main` and the
sm100a-only `long_bf16_reverse:paged:gqa16:direct_group:main` |
`9b8df5a0` / `70a89c8d` / `1e1433e9`; direct_group `67f613e9` |
`249de815` / `d24af147` / `c3da0a78`; direct_group `d24af147` (same
module as `paged:gqa16:main`) | P1b | forward producers retraced with
the group count derived from the item's `q_count`; the host orders the
long work-list items with at least `fill_groups` groups by `(head, first
query token // 1024, group_count desc, kv_block, q_begin)` and appends
the smaller items in group-count-descending order, so consecutive CTAs
of one head share the Q slab in L2. The `:reduce` (long combine) modules
are unchanged (`2722338b` for the GQA-16 routes, `711d5eee` for paged
GQA-8; no `reduce` route line changes in
`flashinfer/jit/blackwell_msa.py`) |
| `prefill_union:bfloat16:bfloat16:flat:gqa16:any:main` | `ca3cbae6` |
`044ebdf2` | PNV-A2, P-X2b′, P-U4b | two-stage folded-GQA K/V rings
(`GQA_FOLDED_KV_STAGES` 1 → 2, +65,536 B dynamic SMEM); shared
128-column TMEM score region with P in its own 64 + 64 columns,
`s_empty` / `o_full` hand-offs, MMA issue order QK0(b+1), PV0(b),
QK1(b+1), PV1(b); heavy / light Q-tile interleave within a request +
round-robin KV-head rotation across consecutive CTAs (two u32 index maps
under constant guards; 128 registers / 0 spill, hot-loop opcodes
unchanged) |
| `prefill_union:bfloat16:bfloat16:{flat:gqa8:any, paged:gqa16:any,
paged:gqa8:any}:main` | `dfcd2b63` / `943f0e35` / `b2b929b1` |
`0e42bddc` / `e9c87303` / `04f607ba` | PNV-A2 (+ P-X2b′ on the GQA-16
retrace) | two-stage rings (+65,536 B dynamic SMEM); on the GQA-16
retrace also the shared-TMEM issue order |
| `prefill_union:bfloat16:bfloat16:paged:gqa16:causal_large:main` |
`d7a39c2b` | `39657d21` | PNV-A2, P10, P-X2b′ | two-stage rings (+65,536
B); load-warp union block list with a list-position selection mask
(`UNION_LIST + UNION_POS_MASK`, +9,216 B SMEM) — the >64-page program
the P10 selection-union census routes the paged 16K–128K `first_topk`
rows onto; shared-TMEM issue order |
| `prefill_union:bfloat16:bfloat16:paged:gqa16:causal_mask64:main` |
`a1682947` | `9c2eacf9` | PNV-A2, P9b, P-X2b′ | two-stage rings (+65,536
B); load-warp union block list (`UNION_LIST`, +9,216 B SMEM; a fully
masked block is an exact identity of the online softmax); shared-TMEM
issue order |
| host plan / launch (`flashinfer/msa_ops/_blackwell_sm100.py`, byte
mirror of Cake's `exports/blackwell_msa/backend_sm100.py`) | — | +447 /
−38 lines vs #6459 (includes the ruff-format re-wrap of the mirror, Cake
6941a6ee) | P2, P1b, P10, P-H1d | LPT split of the long-route tail wave;
Q-resident long-route order; union-census route selection for paged
prefill; paged prefill binds the all-zero `cu_seqlens_k` carrier
(`_paged_prefill_cu_seqlens_k()` zero-fills on creation;
`_cumulative_kv_lengths` (per-call zero + `torch.cumsum`) removed; the
kernels never read the offsets under `INPUT_PAGED`: `token_base = 0`) |

Unchanged (byte-identical to #6459): the gqa0 (general three-stage) BF16
/ FP16 / FP8 `prefill_union` programs (none of them is in the
commit's 23-file list), every `decode_*` program, every Top-K program.

## Precision

All levers are bitwise by construction except P10's route change, and
the Cake A/B records confirm it: output SHA-256 equal in both
arms on every measured prefill row of every A/B and knock-out run —
rounds 4–8 integration head `21f89241`: 18 / 18 (GB300) and 17 / 17
(B200, +1 row whose baseline arm is OOM-infeasible on B200); P-X2b′ 7 /
7 per arch; round-9 per-lever knock-outs P-H1d 9 / 9 and P-U4b
7 / 7 per arch; round-9 merged head knock-out vs H9 10 / 10 per arch.
The round-9 merged-head acceptance vs the frozen baseline reads
`bitwise 6 / diff 4` per arch: the 4 differing rows are the paged
16K–128K `first_topk` rows that P10 moves from the long route onto the
selection-union program (a different program with a different reduction
order); the Cake ledger records their error against the FP32
reference at **0.36–0.39× (rel-L2) and 0.44–0.59× (max-abs) of the
frozen baseline's** — closer to the reference, not further. The export
protocol's correctness check (FP32 attention reference, exact LSE)
passes on every shipped prefill shape (table below). No tolerance was
changed anywhere.

## Performance

Cake `tools/msa_rebench` acceptance protocol (frozen-baseline arm
`08e48b26` = the generator state of #6315 = the programs on `main`, vs
candidate arm in the same run, CUPTI cold-L2 timing, two interleaved A/B
passes, 11 samples after 5 warm-up launches per arm and pass, band auto
with floor 0.02; ratio =
baseline median / candidate median).

**Round-9 merged head `f18fe94b`** (program text = this delivery; 10
prefill rows per architecture; acceptance steps 8b43b4aa → absum
224e3f23 (NSC) / abab7ce6 → d5de25ad (JHB); knock-out vs H9 `5412122c`
f61ddfd5 → 4ddbbcc4 / bdf94b14 → 7bad0a3d):

| row | B200 acc (µs base → now) ; KO vs H9 | GB300 acc ; KO vs H9 |
|---|---|---|
| flat b1 q4096 (union GQA-16) | **1.1762** (282.2 → 239.9) ; **1.0400**
| **1.1111** (213.4 → 192.0) ; **1.0454** |
| paged b1 q8192 first_topk | **2.3439** (964.5 → 411.5) ; **1.0497** |
**2.6650** ; **1.1036** |
| paged b1 q16384 first_topk | **2.1245** ; **1.0215** | **2.2426** ;
**1.0524** |
| paged b1 q32768 first_topk | **2.0018** ; 1.0096 PARITY | **2.0052** ;
**1.0238** |
| paged b1 q65536 first_topk | **2.0208** ; **1.0744** | **1.9429** ;
1.0141 PARITY |
| paged b1 q131072 first_topk | **1.7572** ; 1.0316 PARITY (band 0.035)
| **2.0080** ; 0.9838 PARITY |
| nvfp4 paged b1 q8192 (Cake-dispatcher-only route, not shipped) |
**1.6684** ; **1.0743** | **2.0203** ; **1.1282** |
| flat b1 q8192 / q16384 / q32768 (long route) | 1.0063 / 1.0104 /
**1.0214** ; PARITY / PARITY / **1.0385** | 1.0059 / **1.0201** /
**1.0419** ; PARITY ×3 |
| verdict | **WIN 8 / PARITY 2 / LOSS 0** ; KO WIN 6 / PARITY 4 / LOSS
0, bitwise 10 / 10 | **WIN 9 / PARITY 1 / LOSS 0** ; KO WIN 5 / PARITY 5
/ LOSS 0, bitwise 10 / 10 |

Per-lever knock-out shares (candidate vs the same tree without the
lever; the Cake ledger rows):

| lever | B200 | GB300 |
|---|---|---|
| P9b (round 7): union block list on the paged GQA-16 `causal_mask64`
program | paged 8K first_topk 876.3 → 477.1 µs **1.8367** | 737.6 →
401.0 µs **1.8393** |
| P10 (round 8): selection-union census route, paged 16K / 32K / 64K /
128K first_topk (vs the long route) | **1.586 / 1.620 / 1.556 / 1.586**
| **1.616 / 1.635 / 1.622 / 1.566** |
| P-X2b′ (round 8): shared-TMEM QK/PV issue order | flat q4096 285.3 →
248.8 µs **1.1466**, paged 8K first_topk 478.7 → 431.7 µs **1.1089** |
**1.0520** / **1.0483** |
| PNV-A2 (round 7): two-stage folded-GQA rings | BF16 rows PARITY (the
gain is on the unshipped NVFP4 rows) | paged 8K first_topk **1.1018** |
| P1b (round 7): Q-resident long-route order | long rows WIN 6 / PARITY
9 (flat 64K 1.0856, paged 32K ft 1.1011) | WIN 13 / PARITY 3 (paged 128K
ft 1.1816, flat 256K 1.0786) |
| P-H1d (round 9): all-zero `cu_seqlens_k` carrier, host-only | paged 8K
/ 16K first_topk **1.0497 / 1.0249**, nvfp4 **1.0753**; others PARITY |
**1.1100 / 1.0554**, 32K **1.0269**, nvfp4 **1.1433** |
| P-U4b tree B (round 9): tile interleave + KV-head rotation | flat
q4096 **1.0354** (0.2485 → 0.2402 ms) | **1.0463** (0.2020 → 0.1929 ms)
|

Rounds 4–8 integration head `21f89241` vs the frozen baseline, 18 rows
per arch: GB300 WIN 15 / PARITY 3 / LOSS 0 (absum 91edca89), B200
WIN 12 / PARITY 4 / LOSS 1 / GAP 1 as recorded by absum ef2e7b34 (17
measured rows + 1 OOM-infeasible GAP); the LOSS row `flat_b2_q32768`
(0.9292, band 0.044, two interleaved passes) was re-measured on a
dedicated GPU at 1.1166 WIN (absum ebf9e36c) and bracketed by an A/A
(absum 08044b3e) whose two-pass band 0.1056 exceeds the 0.071 deviation
→ 0 LOSS after re-measurement.

## Export protocol on the delivery

`loom.export.generated_programs`, same protocol as #6459, frozen on the
integration head `803d25e1` and reused unchanged for the `6941a6ee`
export (the host-mirror-only commit changes no route entry; structured
diff vs the Top-K
round-9 protocol: 12 changed route entries, all prefill — the six
`prefill_union:bfloat16:bfloat16:*` routes (`flat:gqa16:any`,
`flat:gqa8:any`, `paged:gqa16:any`, `paged:gqa16:causal_large`,
`paged:gqa16:causal_mask64`, `paged:gqa8:any`) on both arches, each with
exactly one changed leaf
`stages[0].source_build.launch.dynamic_smem_bytes` (the two-stage K/V
rings); the 45 other route keys (18 decode, 8 Top-K, 7
`long_bf16_reverse`, 12 unchanged `prefill_union` GQA-0 BF16 / FP8 /
FP16 routes) identical; at shape granularity 18 of the 175 route entries
changed (9 prefill shapes × 2 arches), 157 identical (decode 100 /
prefill 41 / Top-K 16); same 57 route keys and 175 shapes; sha256 old
`861294e3…` → new `6dfc9928…`).

| | B200 (sm_100a; NSC step 70568b34, job 2243845) | GB300 (sm_103a; JHB
step e909dba4, job 992972) |
|---|---|---|
| shapes completed / timed-correct / all gates passed / `correctness ==
false` | 87 / 87 / 77 / 0 | 88 / 88 / 78 / 0 |
| all timing gates passed | no — 10 rows fail timing-validity gates only
(listed below) | no — 10 rows fail timing-validity gates only (listed
below) |
| source / export time geomean, all shapes | 0.9989 (87 shapes) | 0.9995
(88 shapes) |
| prefill shapes (29 on B200, 30 on GB300) | 22 / 29 timing-passed,
geomean 0.9966 | 24 / 30 timing-passed, geomean 0.9989 |

Non-passing rows (all `correctness: true`, `measurement_valid: false`
only; the runner exits 1 on them by design):
- B200 (10): `topk_small_forced_clamped`, `topk_tied_threshold_forced`,
`topk_nvp_le16_t5_h2_k64_nvp9_fb2_fe1` (directional_disagreement +
endpoint_drift); `prefill_flat_bf16_gqa16_folded_tail`,
`prefill_flat_bf16_gqa16_ragged_batch`, `prefill_fully_masked_row`,
`serving_m3_prefill_tp8_correctness_q17_kv257_h8_hkv1_k16_paged_bf16`,
`coverage_prefill_mixed_fp8_b2_q64_kv512_h8_hkv2_k16_flat`,
`coverage_prefill_bf16_b2_q64_kv512_h16_hkv1_k16_paged_noncausal`
(directional_disagreement);
`perf_prefill_bf16_b1_q16384_kv16384_h64_hkv4_k16_flat_varlen`
(endpoint_drift).
- GB300 (10): `topk_small_forced_clamped`, `topk_tied_threshold_forced`,
`topk_nvp_le16_t5_h2_k64_nvp9_fb2_fe1`,
`prefill_flat_bf16_gqa16_folded_tail`,
`prefill_flat_bf16_gqa16_ragged_batch` (directional_disagreement +
endpoint_drift); `topk_large_radix_domain`,
`serving_m3_prefill_tp8_correctness_q17_kv257_h8_hkv1_k16_paged_bf16`,
`coverage_prefill_mixed_fp8_b2_q64_kv512_h8_hkv2_k16_flat`,
`coverage_prefill_bf16_b2_q64_kv512_h16_hkv1_k16_paged_noncausal`
(directional_disagreement);
`perf_prefill_bf16_b2_q262144_kv262144_h64_hkv4_k16_flat_varlen`
(endpoint_drift).

## Tests

- **Repository tests** on both clusters, `pytest tests/msa_ops
tests/jit/test_blackwell_msa_jit.py` on the dev worktree (7cd20a82 +
this
delivery): 394 passed / 155 skipped / 0 failed (NSC step f106a740, 284
s); 394 passed / 155 skipped / 0 failed (JHB step 419059d4, 340 s).
(#6397 / #6410 / #6443 / #6459 read 394 passed / 155 skipped / 0
failed.)
- **Cake-side gates on the delivered program text** (every gate step
exits `GATE_RC=1` only because of items pre-existing on its base tree;
attributed PASS per !1416 / !1409): round 9 — P-H1d full gates B200
`2aac3905` / GB300 `ec1dd229` (unit 1349 / 0; e2e_cpu 80 / 68 failed =
the frozen mrpint-cpu control set, NEW 0 / FIXED 0; GPU e2e 76 passed /
0 failed / 1 xfailed and 70 passed / 0 failed / 6 skipped / 1 xfailed;
`tools/bench-regression` 31 pass / 0 regress / 3 non-comparable / 1
crash of 35, the crash `prefill_m64_bf16` and the non-comparable entries
pre-existing on the base; host-only, no sanitizer phase); P-U4b tree B
full gates B200 `57e0476a` / GB300 `5e3b15d4` (same counts;
compute-sanitizer synccheck + memcheck on
the 5 registered prefill entries `ERROR SUMMARY: 0 errors` per
architecture). Rounds 4–8: integration head `21f89241` gates B200
`8ad974ed` / GB300 `a772a083` (unit 1119 / 0, GPU e2e 73 / 67 passed, 0
failed, bench 0 regressions, sanitizer 4 entries × 2 tools
  0 errors); P10 / P-X2b′ family-head gates as recorded in !1409.
- **PAIR_IDENTICAL**: the B200 and GB300 export runs deliver
byte-identical files (100 / 100 delivered files identical, 0 differing,
removed-file sets equal, target revision `7cd20a82` on both;
`export_pair_compare msa-rebench-expr9pfx2-b200
msa-rebench-expr9pfx2-gb300`).

## Pre-commit

`pre-commit run --all-files` with the repository configuration
(pre-commit 4.7.0, ruff 0.12.8), NSC step `e0f7157b` on the delivery
worktree: exit 0, 15 hooks Passed (added large files, case conflicts,
merge conflicts, EOF, line endings, requirements, whitespace, tabs,
CRLF,
clang-format, mypy, ruff check, ruff check SM12x import order, ruff
format, experimental test scope selftest), `check for broken symlinks`
Skipped (no files to check); no hook modified a delivered file
(`hook_modified=0`). This PR
changes no Python besides the generated
`flashinfer/jit/blackwell_msa.py` registry and the generated host mirror
`flashinfer/msa_ops/_blackwell_sm100.py`.

## Reproduction

- Export: Cake `exports/blackwell_msa` from Cake
`6941a6ee67a980d01c85547b7d1b6b42119b9643` into a fresh FlashInfer
worktree at
`7cd20a82caeceb1e4b4a925ac13ddc3458474e94`, shape arch `sm_100a` (B200,
2 GPUs, step 70568b34) / `sm_103a` (GB300, 1 GPU, step e909dba4);
protocol frozen on the integration head `803d25e1`
(`provenance.producer_revision`, sha256 `6dfc9928…`; 6941a6ee changes
only the host
mirror, so the protocol is unchanged); expected exit 1 on the
timing-only flags above with `correctness_false == 0`.
- Pair compare: `export_pair_compare` of the two runs →
`PAIR_IDENTICAL`.
- Stack: the delivery's delta was committed on the 7cd20a82-based Top-K
round-9 commit `e6659626` (stack-commit step 027693cd, branch
`cake/blackwell-msa-prefill-r9-cake1183-20261013`, commit `e26f0e02`;
the step asserts the stacked tree equals the delivery tree), then
rebased object-level onto the Top-K PR head at that time, `d4647c8e` (on
#6443 `e3122c1f`, on `main` `13149016`) as `833a6f52` — same file
set and `git patch-id`, no conflicts. After #6443 merged (`d0546b42`,
2026-10-14T05:16Z) and #6459 was re-stacked onto `main` `e403d307` as
`b68ae569`, this commit was re-stacked the same way onto `b68ae569` as
`b2773704` (same file set and `git patch-id`, no conflicts; `833a6f52`
retained as branch
`cake/blackwell-msa-prefill-r9-cake1183-20261013-on-d4647c8e`). After
#6459 merged (`ba4defb9`, 2026-10-14T07:27Z) it was
re-stacked onto `main` `ba4defb9` as `fdb82c4c`
(`--merge-base=b68ae569`, same checks; `b2773704` retained as branch
`…-on-b68ae569`).

## Stacking

Based directly on `main` `ba4defb942f35ecc3320f81803188a59f89e4f92`
(which contains the squash-merged Top-K round-9 PR #6459 and the decode
round-8 PR #6443): this commit
`fdb82c4c406ed6c6f5c2282ec140455e65cfdec1` is the only commit of the PR;
the prefill delta is
`git diff ba4defb9 fdb82c4c` (23 files, +2431 / −3876: the 9 regenerated
prefill modules as 18 renamed program files, the 2 files of the removed
`direct_group` module `67f613e9`, `flashinfer/jit/blackwell_msa.py` +322
/ −384, `flashinfer/msa_ops/_blackwell_sm100.py` +447 / −38, one comment
line of `cake_blackwell_msa_device_common.cuh`). The delta was produced
by the stack-commit step 027693cd on the 7cd20a82-based Top-K commit
`e665962645521bac3b957a7e9c18a92bc5ee5ca8` (commit
`e26f0e020eed1993be4c8dff01391187730cd16f`, tree byte-identical to the
regenerated delivery),
then moved object-level (`git merge-tree --write-tree`, no conflicts,
identical file set and `git patch-id --stable` `ac0aac51` at every step)
onto
`d4647c8e` as `833a6f52`, onto `b68ae569` as `b2773704`, and onto `main`
`ba4defb9` as `fdb82c4c`; the earlier commits are kept as branches

`cake/blackwell-msa-prefill-r9-cake1183-20261013-on-{7cd20a82,d4647c8e,b68ae569}`
in the export clone. If `main` moves again, the commit is
re-stacked the same way and the PR force-updated.

## Provenance

- Cake producer `6941a6ee67a980d01c85547b7d1b6b42119b9643` = the pushed
integration head `803d25e1496fa679f7b4e7100a1d7c762bc7c928`
  (branch `averyh/msa-ceiling-fi-int-r9pfx`) + one commit touching only
`exports/blackwell_msa/backend_sm100.py` (ruff-format re-wrap,
`strict=False` on three `zip` calls; no kernel or route change — the
regenerated device programs and route tables are identical to an export
from `803d25e1`; the commit itself is on no pushed Cake branch — it
reached both clusters as the bundle
`stage/cake-1183-6941a6ee67a9.bundle`; a follow-up Cake MR onto `main`
carries it). The integration head is the merge of the Top-K
round-9 integration head `5dbd76a393015a3827f8354f9e73e6c4187206d4`
(producer of #6459) and the prefill round-9 MR head
`ee3544b312be5ba49d501d4910caf696359de170` (!1416, stacked on !1409
`ad2c9390` → !1403 `c12393f7`); merge base
`918858462ccc`. No kernel text is authored in the merge: every
merge-touched source path equals one of the two parents, and the three
files both sides touch (`exports/blackwell_msa/backend_sm100.py`,
`loom/examples/weave/minimax_sparse_attention_sm100.py`,
`tactics/README.md`) are exact hunk unions (verified by line-multiset
comparison); the only conflict was the Goal changelog. Cake render
census of the integration head: vs `5dbd76a3` exactly the prefill keys
differ (24 per arch + the P1b `u8partial_direct_group` keys new to
the prefill side), vs `ee3544b3` exactly the decode / NVFP4 /
streaming-Top-K keys (22 / 24), no key in both sets.
- Cake MRs: prefill !1403 (`c12393f7`), !1409 (`ad2c9390`), round 9
!1416 (`ee3544b3`); Top-K / decode as in
  #6459 / #6443.
- Linear: CAKE-1183.


🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Updated Blackwell MSA execution paths with revised work scheduling and
multi-stage data processing. Some long-prefill workloads can now avoid
processing unselected blocks when conditions allow.
* Improved handling of paged prefill inputs and query-group sizing
across supported routes.
* **Compatibility**
* Updated kernel dispatch and launch requirements for the revised
Blackwell MSA variants.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [55087f5](https://github.com/flashinfer-ai/flashinfer/commit/55087f53e75238dc38d5a926442c6fe3e42ee961)

- **作者**: eigen
- **时间**: 2026-10-14T07:39:45Z
- **提交信息**: perf(cake_fused_moe): Kimi-K3 NVFP4 SiTU experts SM100 16384-token row with per-CTA privatized routing (#6442)

## Kimi-K3 NVFP4 SiTU experts: SM100 16384-token row with per-CTA
privatized routing

On SM100 (B200) the 16384-token row now runs `large_q8i_p1024`: the
eight stages of the `large_q8i` route that #6341 introduced for the
SM100 large rows (tile-128 FC1, the FC2 that stores a signed INT8
partial with one FP32 scale per 128×128 tile, the stream-ordered
finalize), with the routing histogram and the routing scatter replaced
by two kernels that handle 1024 routed (token, expert-slot) pairs per
CTA. The histogram accumulates its CTA's expert counts in shared memory
and adds each non-zero count to global memory once; the scatter ranks
its CTA's pairs per expert in shared memory, reserves one block of rows
per expert per CTA with a single global atomic and places each pair at
its rank inside that block. The route therefore launches 256 CTAs for
the 262,144 pairs of the row where the production routing kernels launch
1024 CTAs of one pair per thread. Expert counts, tile tables and the set
of rows of every expert equal the production routing's; the order of
rows inside an expert's tiles is a permutation of it, so the 8-bit
per-tile FC2 partial and its per-tile scales round differently: the
whole-call output of this route is not bitwise equal to the #6341
route's output, and the two outputs are not gated against each other;
each is gated against the reference at the published tolerance
(`atol=1.0, rtol=0.1`), see Tests. The 8192-token row keeps `large_q8i`
on SM100; every SM103 row is unchanged. This change is stacked on #6341
and, through it, on #6340, #6329, #6248 and #6194; the PR diff therefore
includes those commits until they merge.

| token count | SM100 (B200) route | SM103 (B300) route |
|---|---|---|
| 8192 | `large_q8i` (unchanged) | `large_q8i` (unchanged) |
| 16384 | **`large_q8i_p1024`**: `large_q8i` stages with the per-CTA
privatized routing histogram / scatter, 256 routing CTAs | `large_q8i`
(unchanged; 1024 routing CTAs) |

The two kernels are SM100-only programs named after their kernel (like
the SM100 single-token FC1 of #6340, carried for one architecture, no
fold): the histogram `route_histogram:n128_p1024` is
`..._bf03708b8a006adcd5e1` (kernel translation unit sha256
`87f05b26a4e0850553386f587fbf3e642d0885862b69d0f671ce165f4adc5597`) and
the scatter `route_scatter:n128_p1024` is `..._5237090cc1d6ad6ce001`
(sha256
`e62f1feb1eb3ed7536af6dc1650b234503ef822938f4fcfeb843ebffec8e0322`);
both kernel texts are the measured delivery byte for byte. Four
translation units are added under `csrc/fused_moe/cake_kimi_k3_situ/`;
no unit is removed or changed. The program registry
`flashinfer/jit/cake_kimi_k3_situ.py` gains the two records (35 -> 37;
`KERNELS["sm_100a"]` gains the two routing keys, `KERNELS["sm_103a"]` is
unchanged; `CARRIED_PROGRAMS`). The runtime's per-architecture selector
(`flashinfer/fused_moe/cake_kimi_k3_situ.py`) returns `large_q8i_p1024`
for 16384 tokens on SM100 and derives the routing grid per selector
(`_ROUTE_PAIRS_PER_CTA`: 1024 pairs per CTA for the new route, 256
otherwise: 256 CTAs at (SM100, 16384), 512 CTAs at 8192 tokens on both
architectures, 1024 CTAs at (SM103, 16384)); the workspace layout and
the public workspace size query are unchanged, as the new selector reads
the same eight-stage layout as `large_q8i`. The behavioural tests
(`tests/moe/test_cake_kimi_k3_situ.py`) assert the 256-CTA routing grid
in the 16384-token every-route case on SM100, and a new test
(`test_cake_situ_per_cta_privatized_routing_matches_the_production_routing`,
uniform and skewed routing) runs the production routing kernels on the
same workspace, inputs and stage bindings and compares the two routings
in pair order through the token-to-row map: expert counts, tile tables,
the rows of every expert, the route map and the FC1 output of every
routed pair must be identical, and the outputs of both calls stay within
the reference tolerance; it skips where an architecture routes 16384
tokens elsewhere (SM103).

**Files** (this change is the one commit on the #6341 head ea330f20a6f7:
7 files, +1060/-3): `flashinfer/jit/cake_kimi_k3_situ.py` (two records
added, 35 -> 37), `flashinfer/fused_moe/cake_kimi_k3_situ.py` (the SM100
16384-token selector and the per-selector routing grid),
`tests/moe/test_cake_kimi_k3_situ.py` (the grid assertion and the
pair-ordered routing comparison with the production routing kernels),
`csrc/fused_moe/cake_kimi_k3_situ/` (+4 translation units). Against
`main` (upstream head 84eb132c81cd at the pre-check) the PR diff also
carries the stacked #6194 + #6248 + #6329 + #6340 + #6341 commits: 18
files, +8916/-4730 in total (23 files, +12109/-7923 without rename
detection).

**Measurement, SM100 (B200)** (frozen protocol: symmetric external CUDA
graphs, CUPTI cold-L2 timing, FlashInfer trtllm-gen baseline with fresh
autotune, five arms per row interleaved in one timer; compute-sanitizer
synccheck and racecheck clean on the source-build and delivered arms,
memcheck not run; the delivered programs are the measured delivery
exactly; the timer held its own GPU, the node was shared with other GPU
jobs):

| B200 row | this PR us | source build us | FlashInfer trtllm-gen us |
#6341 route us (same session) | #6329 route us (same session) |
FlashInfer trtllm-gen / this PR | #6341 route / this PR | #6329 route /
this PR | source build / this PR | tolerance gate (worst gate-normalized
margin / mismatches / max abs diff) | bitwise vs source build (recorded)
| gap to the upper-bound model |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---|---|
| M16384 uniform | 1466.966 | 1467.862 | 2357.648 | 1469.254 | 1480.822
| 1.6072 | 1.0016 | 1.0094 | 1.0006 | 0.830 / 0 / 0.9219 | False |
1.607x over the 912.8 us floor |
| M16384 skew | 1382.150 | 1382.310 | 2210.336 | 1429.350 | 1460.517 |
1.5992 | 1.0341 | 1.0567 | 1.0001 | 0.823 / 0 / 0.9375 | False | 1.514x
over the 912.8 us floor |

"#6341 route" is the previously shipped SM100 route of this row
(`large_q8i` with the production routing kernels) and "#6329 route" the
one before it (pre-shuffled scale factors, BF16 expert output), both
re-measured in the same timer as arms; "source build" is an in-session
build of the same programs from source; "gap to the upper-bound model"
is the measured time of the row over its floor, the roofline + measured
fixed-overhead upper-bound model of the row (HBM bytes + FC1/FC2
tensor-core FLOP + measured launch/route/finalize overhead), so the gap
is a lower bound on the remaining headroom. **Trade-off**: the gain over
the #6341 route is 1.0341× on the skewed row (the row the change
targets: under skewed routing the production scatter's
one-atomic-per-pair contention on the busy experts is what the block
reservation removes) and 1.0016× on the uniform row, which is inside the
±0.5 % run-to-run band of this protocol -- no gain beyond noise is
claimed for the uniform row; the route is adopted for the 16384-token
row as a whole because neither row regresses. As in #6341, run-to-run
bitwise reproducibility of the output is lost on this row (tile
membership, hence each tile's INT8 scale and rounding, depends on the
row assignment of the call); this PR changes the row order inside an
expert's tiles, so its output is not bitwise equal to the #6341 route's
and the two outputs are not gated against each other: over the timer's 5
rounds per row the largest gate-normalized difference between the two
routes' outputs on identical inputs was 0.422 / 0.393 (|diff| / (1.0 +
0.1·|#6341 route output|); max abs diff 0.4375 on both rows), while on
the unit test's inputs one element of 58,720,256 differed by 1.09 to
1.12 (see Tests); per-tile scales within [0.540, 1.181] / [0.593, 1.200]
with no zero or non-finite scale over 10 records per row; the output was
not bitwise equal to the source build on either row (recorded, not
gated), while every round of both rows stays within the reference
tolerance (0 mismatches at `atol=1.0, rtol=0.1`; packed inputs, block
scales and the pair-ordered intermediates bitwise equal in every round);
the dirty-workspace arm (every workspace buffer pre-filled with 0xA5,
seeded random and zeros before the reference comparison) passed on both
rows.

Measurement cost per row (seconds; the five-arm timer step and the
GPU-reportable time per arm):

| B200 row | timer physical s | timer driver s | benchmark s | autotune
s | GPU-reportable s (this PR / source build / FlashInfer trtllm-gen /
#6341 route / #6329 route) |
|---|---:|---:|---:|---:|---|
| M16384 uniform | 575.7 | 470.4 | 86.0 | 152.7 | 4.090 / 4.093 / 6.560
/ 4.096 / 4.137 |
| M16384 skew | 550.7 | 453.6 | 86.9 | 138.4 | 4.034 / 4.031 / 6.460 /
4.172 / 4.264 |

**Tests**: `tests/moe/test_cake_kimi_k3_situ.py` on B200 (SM100): 29
collected / 29 passed / 0 skipped / 0 failed in 888.02 s (29 cases: the
27 cases of #6341 plus the two pair-ordered routing cases). The
pair-ordered test runs the production routing kernels on the same
workspace, inputs and stage bindings: the two routings produce
bitwise-identical pair-ordered routing tables (expert counts, tile
tables, the rows of every expert, the route map and the FC1 output of
every routed pair), and each call's BF16 output matches the reference
within the published tolerance (atol 1.0 / rtol 0.1). The two outputs
are not compared with each other: they are not bitwise identical,
because the accumulation order of the INT8 per-tile FC2 partial depends
on tile membership, which differs between the two routings; the test
records their largest absolute difference instead. Because the commit
changes the shared host module, the shared test module and the registry,
the same file was run on B300 (SM103) at this head: 27 passed / 2
skipped / 0 failed in 663.90 s (the two new cases skip on SM103, which
routes 16384 tokens to `large_q8i`). An additional run of the SM100
16384-token cases
(`test_cake_situ_every_route_eager_and_external_graph[large_m16384]` and
the two pair-ordered routing cases) with every live workspace view
pre-filled with the byte 0xA5 immediately before each call (test-side
pytest plugin wrapping the submit entry; delivered kernels, bindings and
runtime unchanged; tracked files unchanged after the run): 3 passed, 0
failed in 16.14 s (7 poisoned submits, 91 view fills). The pair-ordered
test prints the largest absolute difference between the two routings'
BF16 outputs instead of asserting on it (pytest captured that output in
these passing runs, so the gate logs do not show the value); in the run
of the earlier form of the test on the same kernels, inputs and seeds,
that difference was 1.09 to 1.12 at one element of 58,720,256 while both
outputs stayed within the published tolerance of the reference. The
branch has a clean `git merge-tree --write-tree` against upstream `main`
at 84eb132c81cd (fetched at the pre-check).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an optimized routing path for 16,384-token workloads on select
hardware.
* Extended the large Q8I routing path to an additional supported
architecture.
* **Refactor**
* Updated routing and expert-processing paths for supported workloads,
replacing some previous scale-factor handling.
* **Tests**
* Added routing comparisons and updated route-selection and workspace
checks for the revised paths.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ba4defb](https://github.com/flashinfer-ai/flashinfer/commit/ba4defb942f35ecc3320f81803188a59f89e4f92)

- **作者**: eigen
- **时间**: 2026-10-14T07:27:04Z
- **提交信息**: perf(cake_msa): Blackwell MSA Top-K streaming select 1.39-1.41x faster (bank-conflict-free candidate dump, one barrier per argmax round); small-grid stage-only plan rule (bit-identical selections) (#6459)

> Developed by the **CAKE team**, this PR regenerates the Top-K select
routes of the Cake-generated MiniMax Sparse Attention family for
> SM100 / SM103 with three Cake levers: (1) the one-CTA-per-row
**streaming Top-K16 program** dumps and reads its candidates rank-major,
so
> the 24 % of its cycles that went to shared-memory bank conflicts
vanish (lever C2-S); (2) every argmax round of that program keeps **one
CTA
> barrier instead of two** (lever C1-S); (3) the **host plan** sends
16-query grids of at most 32 (query, head) rows (at most 27 head ×
query-tile groups, so the
> `S = 16` grid fits one wave) over 513..1024 valid pages to the
stage-only `S = 16` split of the existing `topk_select` program instead
of the streaming program (lever T11b-2, host rule
> only). On the frozen Top-K rows the streaming t64 rows run **1.395 /
1.395× (B200) and 1.401 / 1.408× (GB300)** faster and the small-grid
> t8 rows **1.11 / 1.11× (B200) and 1.13 / 1.12× (GB300)** (1.11 / 1.10×
and 1.12 / 1.12× against the plan of #6410), every other row PARITY, 0
LOSS, with **bit-identical selected indices**. Based on
> `main` `e403d307` (#6443, #6397 and #6410 are merged).

## Summary

Regenerates the Top-K select routes of the Cake-generated MiniMax Sparse
Attention family for SM100 / SM103 (`csrc/blackwell_msa/`,
`flashinfer/jit/blackwell_msa.py`,
`flashinfer/msa_ops/_blackwell_sm100.py`) from the Cake generator at
`5dbd76a393015a3827f8354f9e73e6c4187206d4` (CAKE-1183 MSA ceiling round;
the FlashInfer-export integration head = the decode round-8
producer `845ed0b4` of #6443 merged with the Top-K round-9 MR head
`fed26a8f` — see "Provenance") onto
`7cd20a82caeceb1e4b4a925ac13ddc3458474e94` (= main after #6315), **on
top of the decode round-8 delivery #6443** (merged; this PR's commit
`b68ae569` sits on `main`
`e403d307`): this PR carries only the Top-K delta; the 7cd20a82-based
stacked tree
(`e6659626` on `bb84f85b`) is byte-identical to the export's delivery
(asserted by the commit step) and was moved object-level first onto
#6443's head `e3122c1f` (`d4647c8e`) and, after #6443 merged, onto
`main` `e403d307` (`b68ae569`) with the delta unchanged (see
"Stacking"). Same per-program layout as #5893 / #6315 / #6397 / #6410.

All three changes are layout / schedule / host-plan changes: the
selected Top-K indices are **bitwise identical** to the replaced
programs
(output SHA-256 equal in both arms on every measured Top-K row of both
architectures in every A/B and knock-out: 8 / 8 rows × 3 runs per
architecture for the streaming levers, 10 / 10 rows × 2 runs per
architecture for the plan rule; 98 / 98 exact `topk_v2_check` cases per
architecture at the plan-rule head). No dtype, tolerance, public
signature, CUDA-graph workspace or test change.

## What changed

Device code vs `main` (`e403d307`, which contains #6443): 2 program
files — the `_kernel.cu` + `_binding.cu` pair of the regenerated
streaming module
`cake_blackwell_msa_090fde3ccd83ac99e97d` replacing the pair of
`cake_blackwell_msa_9b2a4e4b7dfc96f12c9a` (git renames, 83 / 16 changed
lines); `flashinfer/jit/blackwell_msa.py` (+35 / −35: 1 `MODULES` record
replaced — `dynamic_smem_bytes` 32,896 → 33,024, new
`closure_sha256` — and the two `topk_select_streaming:main` `ROUTES`
entries re-pointed under `sm100a` and `sm103a`; 32 modules / 64 route
entries before and after); `flashinfer/msa_ops/_blackwell_sm100.py` (+26
/ −2: the small-grid plan rule, its two constants and the
`_topk_grid_plan` / `_topk_route` docstrings).
4 files, +110 / −87 (`git diff e403d307 b68ae569`; identical to `git
diff e3122c1f d4647c8e`, `git patch-id --stable` `1dd186a4`).
`tests/msa_ops/test_blackwell_msa_routes.py`,
`tests/jit/test_blackwell_msa_jit.py`, every decode / prefill program
and `csrc/cake_device_helpers/` are byte-identical to `main` / #6443
(the export regenerates the whole family; the Cake render census of
the integration head against each of its parents differs in exactly the
two streaming keys vs the decode producer and exactly the
decode / NVFP4 keys vs the Top-K head, with no key in both sets).

| route key | module on `main` (#6443) | module in this PR | arches |
change |
|---|---|---|---|---|
| `topk_select_streaming:main` |
`cake_blackwell_msa_9b2a4e4b7dfc96f12c9a` (= main / #6410) |
`cake_blackwell_msa_090fde3ccd83ac99e97d`
(`flashinfer/jit/blackwell_msa.py` L1806 / L1839, both arches) |
sm_100a, sm_103a | C2-S rank-major candidate dump / round reads + C1-S
one CTA barrier per argmax round; dynamic SMEM 32,896 → 33,024 B (+128 B
after alignment; declared pool +64 B), block 256, 80 registers / 0 spill
unchanged |
| `topk_select:main`, `topk_select_keq:main`, `topk_select_q32:main` |
`4a11da13` / `0301f8d4` / `fd97fbe1` | unchanged | sm_100a, sm_103a |
program text byte-identical |
| host plan `_topk_grid_plan` (`flashinfer/msa_ops/_blackwell_sm100.py`,
byte mirror of Cake's `exports/blackwell_msa/backend_sm100.py`) |
cost-minimal `S` over `(1, 2, 4, 8, 16)` | + one rule after the
minimiser (T11b-2): `qpack == 1 and rows <= _TOPK_SMALL_GRID_MAX_ROWS
(32) and num_valid_pages <= 1024 and ceil(nvp / S_min) > _TOPK_CAND_CAP
(64) and groups * 16 <= wave CTAs (444)` → `S = _TOPK_SMALL_GRID_SLICES
(16)` | — | the planned slice (33..64) is within the candidate cap, so
`_topk_route` — logic unchanged, only its docstring gained a T11b note
(+3 / −1) — no longer sends these grids to the streaming program; they
run the 16-query `topk_select` instance, one stage-only CTA per slice.
Fires only for 513..1024 valid pages at ≤ 32 rows whose `S = 16` grid
fits one wave (`groups * 16 <= 444`, i.e. at most 27 head ×
16-query-tile groups; 1-query grids with 28..32 heads keep the streaming
plan); every other shape keeps its plan and route |

### Streaming program: C2-S rank-major candidate dump + C1-S one barrier
per round

The streaming program (`topk_select_streaming`: one 256-thread CTA per
(query, head) row, every thread scans its share of the up-to-1024
valid pages and keeps its local top-16, the CTA then performs 16 argmax
rounds over the 4096 dumped candidates and a final bitonic
ordering) is the route of the tied-threshold rows with more than 32 rows
per grid (e.g. the frozen `t64` rows: 64 queries × 4 heads,
782 pages, 8 K blocks).

- **C2-S.** The candidate dump wrote `cand[tid * 16 + rank]` and each
round read `cand[tid * 16 + local_rank]`: with 32 four-byte banks,
`(tid * 16 + rank) mod 32 = 16 * (tid & 1) + rank`, so a warp touched 2
banks per access (dump: 4-way, per-round reads: up to 16-way
conflicts). An ncu bank probe on the replaced program (locked base
clock) attributes **23.98 % / 23.86 % (B200 / GB300)** of
`sm__cycles_elapsed` to non-atomic shared-memory conflict wavefronts,
all of them at these two sites. The regenerated program indexes
rank-major (`rank * 256 + tid`, `local_rank * 256 + tid`): lane `tid`
always lands in bank `tid mod 32`; the probe on the new program reads
**0.0000–0.0003 %**. SASS: 80 registers / 0 spill unchanged; STS 15 → 39
(8 `STS.128` → 32 `STS.32`, the same number of wavefronts), LDS
unchanged in count, same instruction count in the round body. Bitwise:
the re-indexing is a bijection of the 4096 candidate slots; the
  (score, index) pairs dumped and read are the same.
- **C1-S.** Each argmax round used two CTA barriers: warp winners →
barrier A → warp 0 reduces and writes `selected[round]` → barrier B →
every thread reads it to advance its cursor. Now the per-warp winners
are double-buffered by round parity
(`warp_{scores,indices}[(round & 1) * 8 + warp]`, +64 B of the declared
pool: 32,896 → 32,960 B; dynamic SMEM 33,024 B after 128-B
alignment), **every warp performs the second-level reduction itself** on
the same 8 inputs with the same f32 max butterfly and the same
`redux.sync` index minimum (hence the same `best_index` the former warp
0 produced), clamps and advances its cursor from registers; thread
0 still writes `selected[round]` for the final stage, barrier B is gone,
and one barrier after the loop guards the bitonic stage's read of
`selected[]`. WAR safety: round s + 2 writes buffer `s & 1` only after
barrier A of round s + 1, and every thread had finished its round-s
reads before arriving there; the producer can lead the slowest consumer
by at most one round (one full-CTA `bar.sync 0` per round, no
mbarrier). SASS: static barriers 6 → 5, round body 129 → 121
instructions with 2 (was 4) `BAR`, kernel-wide LDS 11 → 9.

Measurements (Cake `tools/msa_rebench` acceptance protocol:
frozen-baseline arm `08e48b26` = the generator state of #6315 = the
programs
on `main` at `7cd20a82`, before #6397 / #6410 (the streaming program
`9b2a4e4b` is unchanged on `main` `13149016`), vs candidate arm in the
same run, CUPTI cold-L2 timing, two interleaved A/B passes, 11 CUPTI
samples after 5 warm-up launches per arm and pass, auto band with
floor 0.02 (every row at the floor except one B200 knock-out-2 control
row at 0.0227); output SHA-256
equal on every row; measured on the lane head `ca24c86c`, whose
streaming program text is byte-identical to this delivery; 8 rows per
architecture = the two streaming `t64` tied rows + 6 16-query control
rows):

| rows | B200 (sm_100a; steps 1d034b86 → absum 068a073b) | GB300
(sm_103a; steps 4ac6730f → 2f7520e7) |
|---|---|---|
| `topk_hkt_tied_threshold_t64_h4_k8192_nvp782` (streaming) | **1.3953**
(14.272 → 10.272 µs) | **1.4009** (13.695 → 9.792 µs) |
| `topk_thk_tied_threshold_t64_h4_k8192_nvp782` (streaming) | **1.3947**
(14.337 → 10.240 µs) | **1.4078** (13.696 → 9.728 µs) |
| 6 control rows (t8 × 2 on the small-grid plan, t256 × 2, t3, k16384) |
WIN on the levers already in #6410 / this PR's plan rule (1.10–2.28),
`t3` PARITY 0.9966; **0 LOSS** | same (1.08–2.26), `t3` PARITY 0.9873;
**0 LOSS** |
| verdict | **WIN 7 / PARITY 1 / LOSS 0**, bitwise 8 / 8 | **WIN 7 /
PARITY 1 / LOSS 0**, bitwise 8 / 8 |
| knock-out 1 = C2-S alone (`568f7ef8` vs `809c79b5`; steps b92d9bf0 →
826e15af / d12ac552 → 398b9058) | t64 **1.3540 / 1.3515** (14.400 →
10.592, 14.368 → 10.591 µs); 6 controls PARITY; bitwise 8 / 8 | t64
**1.3497 / 1.3545** (13.633 → 10.144 / 10.080, 13.728 → 10.048 / 10.176
µs); bitwise 8 / 8 |
| knock-out 2 = C1-S alone (`ca24c86c` vs `568f7ef8`; steps d580b0dd →
dc25fa1d / fb787b56 → f657fae4) | t64 **1.0328 / 1.0360** (10.560 /
10.592 → 10.240, 10.656 / 10.528 → 10.208 / 10.240 µs); bitwise 8 / 8 |
t64 **1.0361 / 1.0377** (10.112 → 9.760, 10.176 / 10.112 → 9.728 / 9.824
µs); bitwise 8 / 8 |

C2-S × C1-S (1.354 × 1.033 ≈ 1.398 on B200, 1.350 × 1.036 ≈ 1.398 on
GB300) reproduces the acceptance ratio.

### Host plan: T11b-2 small-grid stage-only rule

For grids of at most 32 (query, head) rows over 513..1024 valid pages
whose cost-minimal 16-query plan would stream (slice > 64), the plan
takes the stage-only `S = 16` split: 16 single-pass CTAs per 16-query
group, each over a slice of 33..64 blocks, on the existing
`topk_select` program. No program text changes; the selected indices are
identical (plan only). Derivation: the round-6 row-count sweep
found the `S = 16` radix split faster than the streaming program at 32
rows (tied t8 at 782 pages 9.73 / 9.38 µs vs 10.94 / 10.50 µs on
B200 / GB300), parity at 48 rows, streaming faster from 64 rows — hence
the 32-row bound.

| row (frozen manifest, 10 Top-K rows per architecture; lever head
`b5731b4d`) | B200 (sm_100a) | GB300 (sm_103a) |
|---|---|---|
| `topk_hkt_tied_threshold_t8_h4_k8192_nvp782` / `topk_thk_…` vs the
frozen baseline (A/B 333e39a4 → 3d5cf9ca / b696b27e → af1d5361) |
**1.1068 / 1.1086** | **1.1314 / 1.1221** |
| the same two rows, knock-out vs the plan of #6410 (`444aa6e0`;
96b56f51 → 3d2183e6 / e30bb65a → 4c92fcfc) | **1.1099 / 1.1029** (10.976
→ 9.920 µs, 10.944 → 10.047 µs) | **1.1158 / 1.1172** (10.464 → 9.376
µs, 10.560 → 9.375 µs) |
| the other 8 rows (t1024 × 2, k16384, t256 × 2, t3, t64 × 2), knock-out
| PARITY 0.9965–1.0033 | PARITY 0.9974–1.0052 |
| verdict vs the frozen baseline | **WIN 7 / PARITY 3 / LOSS 0**,
bitwise 10 / 10 | **WIN 7 / PARITY 3 / LOSS 0**, bitwise 10 / 10 |

## Export protocol on the delivery

`loom.export.generated_programs`: Cake production dispatcher = *source*
arm vs this PR's module through the FlashInfer JIT = *export*
arm, same GPU, one worker process per shape, CUPTI timing with L2
flushed between calls, 3 counterbalanced groups of 200 ms warm-up +
100 ms timed per arm; gates `source_over_export >= 0.97`,
`directional_disagreement <= 0.05`, `endpoint_drift <= 0.02`. The
protocol was
re-frozen on the integration head (the Top-K protocol reused by #6443 no
longer matched: its structured diff against the new
freeze shows exactly two changed route entries —
`topk_tied_route_t64_h4_k8192_nvp782` on both arches,
`dynamic_smem_bytes` 32896 →
33024 — and 173 identical entries, same 175 shapes, same policy; sha256
`043fe244…` → `861294e3…`).

| | B200 (sm_100a; NSC step 60c67547, job 2243845) | GB300 (sm_103a; JHB
step 56ebbb0d, job 990528, nvl72d425-T03) |
|---|---|---|
| shapes completed / `correctness == true` / all timing gates passed /
`correctness == false` | 87 / 87 / 75 / 0 | 88 / 88 / 82 / 0 |
| all timing gates passed | no — 12 rows fail timing-validity gates only
(listed below) | no — 6 rows fail timing-validity gates only (listed
below) |
| source / export time geomean, all shapes | 0.9986 (87 shapes) | 1.0009
(88 shapes) |
| Top-K shapes (8 per arch, tag `topk`) | 5 / 8 timing-passed, geomean
0.9947 | 4 / 8 timing-passed, geomean 1.0099 |

Non-passing rows (all `correctness: true`, `measurement_valid: false`
only; the runner exits 1 on them by design):
- B200 (12): `topk_small_forced_clamped` (source_over_export,
directional_disagreement, endpoint_drift), `topk_tied_threshold_forced`
(directional_disagreement, endpoint_drift),
`topk_nvp_le16_t5_h2_k64_nvp9_fb2_fe1`, `prefill_fully_masked_row`,
`serving_m3_prefill_tp4_correctness_q17_kv257_h16_hkv1_k16_paged_bf16`,
`coverage_prefill_mixed_fp8_b2_q64_kv512_h8_hkv2_k16_flat`
(directional_disagreement);
`perf_prefill_bf16_b1_q8192_kv8192_h64_hkv4_k16_flat_varlen`,
`…_b1_q32768_kv32768…`, `…_b1_q65536_kv65536…`,
`…_b1_q262144_kv262144…`, `…_b2_q32768_kv32768…`,
`…_b2_q262144_kv262144…` (endpoint_drift).
- GB300 (6): `topk_small_forced_clamped` (source_over_export,
directional_disagreement, endpoint_drift), `topk_tied_threshold_forced`
(directional_disagreement, endpoint_drift), `topk_large_radix_domain`,
`topk_nvp_le16_t5_h2_k64_nvp9_fb2_fe1`, `prefill_fully_masked_row`,
`coverage_prefill_mixed_fp8_b2_q64_kv512_h8_hkv2_k16_flat`
(directional_disagreement).

## Tests

- **Repository tests** on both clusters, `pytest tests/msa_ops
tests/jit/test_blackwell_msa_jit.py` on the dev worktree (7cd20a82 +
this
delivery): 394 passed / 155 skipped / 0 failed (NSC step e197d48a, 279
s); 394 passed / 155 skipped / 0 failed (JHB step ba1409cb, 337 s).
(#6397, #6410 and
#6443 read 394 passed / 155 skipped / 0 failed on both; the 155 skips
are the SM120 / SM121-only cases.) The Top-K routes
changed here are exercised by `test_blackwell_msa_routes.py`; the
bitwise evidence is the Cake-side output SHA-256 equality above and the
  export protocol's `correctness: true` on every shape.
- **Cake-side gates on the delivered program text** (every gate step
exits `GATE_RC=1` only because of rows pre-existing on its base
tree; attributed PASS): streaming levers — full gates on `ca24c86c`
(B200 step `7d7bd603`: unit 1351 passed / 0 failed; e2e_cpu slice
80 failed = the frozen control set (NEW 0 / GONE 0); GPU e2e 76 passed /
1 xfailed / 0 failed; `tools/bench-regression` 31 pass /
0 regress / 1 non-comparable / 1 crash of 33, both pre-existing on
`main`; synccheck + memcheck `ERROR SUMMARY: 0 errors` on the
registered Top-K entry; GB300 step `c629f6ea`: unit 1351 / 0, e2e_cpu 68
failed = control set (NEW 0 / GONE 0), e2e 70 passed / 6
skipped / 1 xfailed / 0 failed, bench 31 pass / 0 regress / 1
non-comparable / 1 crash of 33 (inherited), sanitizer 0 errors;
racecheck
4 / 4 probes `0 hazards` on the candidate and the base per
architecture); plan rule — full gates on `cc2ec8ba` (B200 `5426c958`:
unit
1308 / 0, e2e_cpu 78 failed = the pre-existing failure set of its base
tree (attributed in !1404), GPU e2e 75 passed / 1 xfailed /
0 failed, bench 31 pass / 0 regress / 1 non-comparable / 1 crash of 33
(inherited); GB300 `c8a781fe`: unit 1308 / 0, e2e_cpu 66 failed
(same basis), e2e 69 passed / 6 skipped / 1 xfailed, bench 31 / 0
regress / 1 / 1 of 33; no sanitizer phase — host rule only, launched
  programs unchanged).
- **PAIR_IDENTICAL**: the B200 and GB300 export runs deliver
byte-identical files (102 / 102 delivered files identical, 0 differing,
removed-file sets equal, target revision `7cd20a82` on both;
`export_pair_compare msa-rebench-expr9topk-b200
msa-rebench-expr9topk-gb300`).

## Pre-commit

`pre-commit run --all-files` with the repository configuration
(pre-commit 4.7.0, ruff 0.12.8), NSC step `b6ae1dea` on the delivery
worktree: exit 0, 15 hooks Passed (added large files, case conflicts,
merge conflicts, EOF, line endings, requirements, whitespace, tabs,
CRLF, clang-format, mypy, ruff check, ruff check SM12x import order,
ruff format, experimental test scope selftest), `check for broken
symlinks` Skipped (no files to check); no hook modified a delivered file
(`hook_modified=0`). This PR changes no Python besides the generated
`flashinfer/jit/blackwell_msa.py`
registry and the generated host mirror
`flashinfer/msa_ops/_blackwell_sm100.py`.

## Reproduction

- Export: Cake `exports/blackwell_msa`
(`loom.export.generated_programs`) from Cake
`5dbd76a393015a3827f8354f9e73e6c4187206d4` into a
fresh FlashInfer worktree at `7cd20a82caeceb1e4b4a925ac13ddc3458474e94`,
shape arch `sm_100a` (B200) / `sm_103a` (GB300), 2 GPUs per
cluster, protocol re-frozen on this head (`blackwell_msa.protocol.json`,
175 shapes, 87 / 88 selected per architecture); expected exit 1
  on the timing-only flags above with `correctness_false == 0`.
- Pair compare: `export_pair_compare` of the two runs →
`PAIR_IDENTICAL`.
- Stack: the delivery's delta was committed on the 7cd20a82-based decode
round-8 head `bb84f85b` (stack-commit step 2585318f, branch
`cake/blackwell-msa-topk-r9-cake1183-20261013`, commit `e6659626`; the
step asserts the stacked tree equals the delivery tree), then rebased
object-level onto #6443's head `e3122c1f` (on `main` `13149016`) as
`d4647c8e` and, after #6443 merged, onto `main` `e403d307` as `b68ae569`
— same file set and `git patch-id` at each step, no conflicts.

## Stacking

#6443 (`e3122c1fd5dfee2efbf2ad6eab1d4a01dfd0dc95`, decode round 8) is
merged, so this PR now sits directly on `main`
`e403d30785ea9ece65a88b3337db86dcac19fef5`: base `main` + this commit
`b68ae5696ecce008aa1feb6640022468c4085755`. The Top-K round-9 delta is
`git diff e403d307 b68ae569` (4 files, +110 / −87: the streaming module
`090fde3c` replacing `9b2a4e4b` as two renamed program files,
`flashinfer/jit/blackwell_msa.py` +35 / −35,
`flashinfer/msa_ops/_blackwell_sm100.py` +26 / −2). The delta was
produced by the stack-commit step
2585318f on the 7cd20a82-based head `bb84f85b` (commit
`e665962645521bac3b957a7e9c18a92bc5ee5ca8`, tree byte-identical to the
regenerated delivery),
moved object-level onto #6443's head `e3122c1f` as `d4647c8e` (`git
merge-tree --write-tree --merge-base=bb84f85b`, no conflicts) and, once
#6443
merged, onto `main` `e403d307` as `b68ae569` (`--merge-base=e3122c1f`,
no conflicts); every step keeps the identical file set and
`git patch-id --stable` (`1dd186a4`). The earlier commits are kept as
fork branches `cake/blackwell-msa-topk-r9-cake1183-20261013-on-7cd20a82`
(`e6659626`) and `…-on-e3122c1f` (`d4647c8e`) for traceability. The bot
CI (`tests/msa_ops tests/jit/test_blackwell_msa_jit.py`) passed on
`d4647c8e` and is re-run on `b68ae569`.

## Provenance

- Cake integration head `5dbd76a393015a3827f8354f9e73e6c4187206d4`
(branch `averyh/msa-ceiling-fi-int-r9topk`) = merge of the decode
round-8 stack head `845ed0b41d3c232624505f3d2eccc0a17c2c473c` (producer
of #6443) and the Top-K round-9 MR head
`fed26a8f97f245a4ef6eb1ff36d945d963fd1fdb` (!1415, stacked on !1404
`809c79b5` = lever T11b-2); merge base `918858462ccc`.
The FlashInfer PR chain is linear while the Cake family branches fork,
and the export regenerates the whole family, so each stacked
commit's producer must contain the previous producer's programs: no
kernel text is authored in the merge (every merge-touched source path
equals one of the two parents; the only conflict was the Goal
changelog). Cake render census of the integration head: vs `845ed0b4`
exactly the two streaming keys differ (B200 168 keys / GB300 167 keys, 0
others), vs `fed26a8f` exactly the 20 / 22 decode-NVFP4-FP8
keys of the decode round-8 levers, no key in both sets; the streaming CU
of the integration head is byte-identical to `fed26a8f`'s.
- Cake MRs: Top-K T11b-2 follow-up !1404 (`809c79b5`); Top-K round-9
follow-up !1415 (`fed26a8f`); decode round 8 as in
  #6443.
- Linear: CAKE-1183.


🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved planning for certain small top-k workloads, keeping candidate
slices within limits and using a stage-only plan when conditions allow.
* Updated Blackwell MSA kernel variants and synchronization behavior
across supported GPU architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4602
- **最后更新**: 2026-10-14T16:11:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34720
- **最后更新**: 2026-10-14T23:03:45Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: Wang, Yi, Vinh H. Pham, Dhruv Nair

## AI分析总结

## huggingface/diffusers 昨日提交分析总结

### 1. 主要更新类型
本次提交以 **CI/基础设施加固** 与 **推理功能扩展** 为主，辅以测试代码重构，无核心训练算法变更。

### 2. 关键变更点及与项目方向的关系
- **CI 环境升级至 Python 3.11**（#15030）：同步更新 `setup.py` 与相关配置，保持项目依赖生态与主流 Python 版本对齐。
- **GitHub Actions 全面固定为 commit SHA**（#15028、#15030 衍生修复）：将工作流中可变的 tag/分支引用替换为不可变 SHA，并保留原始版本注释。这是典型的供应链安全加固，响应了安全机器人的扫描告警。
- **`test_modeling_common.py` 清理**（#14988）：精简共享建模测试代码，提升测试可维护性。
- **MagCache 支持 Flux2**（#14756）：核心功能更新，将 `Flux2TransformerBlock` 与 `Flux2SingleTransformerBlock` 注册进 `TransformerBlockRegistry`，并修复单流块尾部缓存的张量形状错配问题。
- **FlashAttention Hub 集成更新 + CUDA-only 测试加守卫**（#15024）：由 Intel 贡献，确保在无 GPU 环境下 CI 不会误报失败。

### 3. 对项目的影响和潜在意义
安全层面，SHA 固定显著降低了 CI 被恶意 action 篡改的风险，对一个广泛被下游引用的基础库尤为重要。功能层面，MagCache 对 Flux2/Flux2 Klein 的支持扩展了记忆化缓存（cache）加速技术的覆盖范围，让 Flux2 用户可用更低开销获得近似精度。CI 清理与 Python 版本升级则降低长期维护成本。

### 4. 值得关注的技术点
- **MagCache 尾部钩子的形状对齐**：Flux2 在单流块前会拼接文本与图像流，导致尾部输出为融合序列 `[text; image]`。最终方案是在已有的"序列长度不匹配"分支中，仅取尾部图像 token 计算残差，与参考实现 MagCache4FLUX 保持一致，并移除了原本会错误相减的死代码分支——这是一种"最小侵入式"修复思路。
- **同一 PR 多次被安全机器人要求补 SHA 固定**，说明安全检查已深度嵌入其 CI 流程。
- 贡献者中出现 Claude/GPT 类 AI 署名与 Intel 工程师，反映该项目 AI 辅助开发与跨厂商协作的趋势。

### 5. 对项目整体发展的影响
结合 README（Apache 2.0 许可的 HuggingFace Diffusers 库），这些提交虽非新模型发布，却巩固了项目作为**生产级、安全可信的扩散模型基础设施**的定位：既保证 CI 供应链可信，又持续把前沿加速技术（MagCache、FlashAttention）适配到最新模型（Flux2）。这种"基础稳固 + 推理加速"并重的节奏，有助于吸引更多模型作者在该框架上发布权重，巩固生态中心地位。

总之，本批次提交以稳健的基础设施强化为主，并通过 MagCache 支持 Flux2 带来了实质性的推理性能收益，为后续的缓存技术扩展（如 FirstBlockCache 修复）铺平了道路。

## 详细提交记录

### [efe46a5](https://github.com/huggingface/diffusers/commit/efe46a5b177af67c64b3666da8ddddac7ee12163)

- **作者**: Sayak Paul
- **时间**: 2026-10-14T14:41:45Z
- **提交信息**: ci: move to python 3.11. (#15030)

* move to python 3.11.

* update setup.py along with others.

* fix(ci): pin GitHub Actions to commit SHAs (#15030) (#15033)

fix(ci): pin actions in workflows flagged on #15030

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

* up

* fix(ci): pin GitHub Actions to commit SHAs (#15030) (#15036)

fix(ci): pin actions in workflows flagged on #15030

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

* up

---------

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

### [ea981b8](https://github.com/huggingface/diffusers/commit/ea981b8b7d80f10deaff369bcda8cbf2c90428dd)

- **作者**: Dhruv Nair
- **时间**: 2026-10-14T11:18:28Z
- **提交信息**: [CI] Clean up `test_modeling_common.py` (#14988)

clean up

### [40f6369](https://github.com/huggingface/diffusers/commit/40f63690da440e8c382ab53e67508835deb1ed2f)

- **作者**: Pauline Bailly-Masson
- **时间**: 2026-10-14T10:55:44Z
- **提交信息**: 🔒 Pin GitHub Actions to commit SHAs (#15028)

Pin GitHub Actions to commit SHAs

Replace mutable tags and branch refs in workflow files with full commit SHAs,
keeping the original version as a trailing comment.

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [7c6eb78](https://github.com/huggingface/diffusers/commit/7c6eb783060f82cd912fb5f51eb204810cf71f66)

- **作者**: Vinh H. Pham
- **时间**: 2026-10-14T09:51:38Z
- **提交信息**: [hooks] Support Flux2 in MagCache (#14756)

* [hooks] Support Flux2 in MagCache

MagCache could not be enabled on `Flux2Transformer2DModel` (Flux2 and Flux2 Klein):

1. `Flux2TransformerBlock` and `Flux2SingleTransformerBlock` were not registered in
   `TransformerBlockRegistry`, so `apply_mag_cache` raised `ValueError: Model class ... not registered`.
2. Once registered, the tail hook raised a shape error. The head hook records the image-only input of
   `transformer_blocks[0]`, but the Flux2 model concatenates the text and image streams before the
   single-stream blocks and calls them with `encoder_hidden_states=None`, so the last single block returns
   the fused `[text; image]` sequence. The residual `tail_output - head_input` could not be formed.

Register the two Flux2 blocks (the single block with `return_encoder_hidden_states_index=None`, matching
how the model calls it) and add `_align_to_hidden_states`, which keeps only the trailing image tokens of
the fused tensor when computing the residual. The cached residual is therefore image-only, which is what
the reference MagCache4FLUX implementation does, and it matches the head input on skipped steps. This also replaces
a dead "fallback" branch in the tail hook that subtracted mismatched shapes anyway.

Tests: `MagCacheTesterMixin` for `Flux2Transformer2DModel`, `Flux2Pipeline` and `Flux2KleinPipeline`.

FirstBlockCache has the same head/tail structure and still fails on Flux2; left for a follow-up.

* [hooks] Slice the fused tail output in the existing mismatch branch

Implement the Flux2 residual fix inside the tail hook's sequence-length mismatch branch instead of a
separate `_align_to_hidden_states` helper. The surrounding structure stays as it was: the `diff == 0`
case still covers a batch-size mismatch via broadcasting, and only the mismatched-length case changes
to subtract the trailing image tokens.

---------

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

### [839af3a](https://github.com/huggingface/diffusers/commit/839af3a04357551ee5a4db84985a0dbb04dbe6d5)

- **作者**: Wang, Yi
- **时间**: 2026-10-14T08:35:19Z
- **提交信息**: Update FlashAttention Hub integration and guard CUDA-only tests (#15024)

* Update FlashAttention Hub integration and guard CUDA-only tests

Signed-off-by: Wang, Yi <yi.a.wang@intel.com>

* fmt

Signed-off-by: Wang, Yi <yi.a.wang@intel.com>

---------

Signed-off-by: Wang, Yi <yi.a.wang@intel.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
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


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13242
- **最后更新**: 2026-10-14T19:47:03Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

## 分析说明

以下分析基于提交标题 `[208d3ab] Fix LTX-2.5 split training, add FL2AV training and INT8 ConvRot scripts (#1752)` 及其提交信息（修复 LTX2.5 训练、新增 INT8-ConvRot 脚本、修复文档），并结合 DiffSynth-Studio 作为扩散模型训练/推理统一框架的项目定位推断得出。由于无法实时访问仓库逐行核对 diff，涉及具体实现细节的部分为合理推断，请以实际代码为准。

## 1. 主要更新类型

这是一次**混合型提交**，同时包含三类变更：Bug 修复（LTX-2.5 split 训练）、功能新增（FL2AV 训练支持、INT8 ConvRot 脚本）、文档更新（配套说明修正）。整体以"让新模型可训练、可落地"为核心诉求，属于功能完善与稳定性加固并重的迭代。

## 2. 关键变更点及与项目方向的关系

- **修复 LTX-2.5 分块（split）训练**：LTX 系列是近期热门的长视频/高分辨率扩散模型，分块训练是让模型在有限显存下处理长序列的关键路径。修复该问题意味着框架对最新视频生成模型的支持从"能跑"提升到"能可靠地训练"。
- **新增 FL2AV 训练支持**：从命名看指向音频-视觉（Audio-Visual）方向的生成任务，说明项目正在从纯视觉扩散向多模态生成扩展，契合 DiffSynth-Studio 一贯的"多模型、多模态全覆盖"战略。
- **新增 INT8 ConvRot 量化脚本**：ConvRot（卷积旋转量化）是针对扩散模型卷积结构的低比特量化技术，表明项目在"训练之后"的部署侧持续投入，推动模型在消费级显卡上低成本推理。
- **文档同步修复**：保证新增训练流程的可复现性，降低社区用户上手门槛。

## 3. 对项目的影响和潜在意义

短期内，用户在 LTX-2.5 上进行分块训练时的失败率和调试成本将显著下降，FL2AV 为音视频生成研究者提供了开箱即用的训练入口，INT8 脚本则让显存受限的用户也能部署大模型。长期看，这类提交强化了 DiffSynth-Studio"训练—量化—推理"全链路闭环的护城河，提升项目在开源扩散框架竞争中的实用价值和用户粘性。

## 4. 值得关注的技术点

- split training 修复中涉及的**长序列分块边界处理与梯度累积一致性**问题，是视频扩散训练的常见坑点，修复思路值得参考。
- **ConvRot 与 INT8 结合**的量化方案：扩散模型的激活分布动态且接近高斯，旋转正交变换（类似 QuaRot/SpinQuant 思路）可有效降低量化误差，如何迁移到卷积结构是技术亮点。
- 音视频联合训练的数据管线与损失配比设计，反映了多模态扩散的工程复杂度。

## 5. 对项目发展的整体影响

结合 README 所述的项目背景，DiffSynth-Studio 的核心价值在于快速跟进前沿扩散模型并提供完整工具链。本次提交精准命中两条主线：一是**前沿模型的及时适配与修复**（LTX-2.5），保证框架"永远支持最新模型"的时效性口碑；二是**低比特量化部署**（INT8 ConvRot），呼应其在消费级硬件上运行大模型的普惠定位。同时 FL2AV 的引入预示项目正积极布局多模态生成赛道，为后续更多音视频模型接入奠定基础。

综上，这次提交虽然规模不大，但同时夯实了训练稳定性、扩展了任务类型、强化了部署效率，是推动项目向"全链路、多模态、低门槛"目标前进的一次典型增量迭代，对社区用户和研究者均有直接的实用价值。

## 详细提交记录

### [208d3ab](https://github.com/modelscope/DiffSynth-Studio/commit/208d3abad800f09bd0acd18a134013e2ebd22c17)

- **作者**: Hong Zhang
- **时间**: 2026-10-14T08:58:27Z
- **提交信息**: Fix LTX-2.5 split training, add FL2AV training and INT8 ConvRot scripts (#1752)

* fix ltx2.5 training & add int8-convrot scripts

* fix docs

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37147
- **最后更新**: 2026-10-15T00:27:13Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 18
- **主要提交者**: Liu Ke, FREETRUMP, Junnan Li

## AI分析总结

## sglang 昨日提交总结（30条）

### 1. 主要更新类型

- **性能优化（约10条）**：占比最高，涵盖批处理拆分缓存、多模态token计数缓存、CPU绑定NUMA节点、MXFP4路由、diffusion解码优化等
- **Bug修复（约12条）**：涉及多tokenizer输出重打包、缓存所有权、Attention后端、GLM5.2/DeepSeek-V4.1模型对齐等
- **功能新增（约4条）**：sgl-router的LoRA块ID分离、Qwen3.8模型渲染、elastic-ep扩展
- **Rust前端建设（约3条）**：metrics服务、weights_checker、移除旧crate
- **文档/测试/CI（约4条）**

### 2. 关键变更点及与项目方向的关系

- **Rust前端持续完善**：新增metrics和weights_checker端点，同时清理旧crate，表明项目正将生产级可观测性和接口从Python逐步迁移到Rust高性能前端，强化部署能力和低延迟目标。
- **HiCache多层缓存演进**：引入Buffer-only L3辅助SWA窗口缓存，仅回填缺失行，体现了项目在分层KV缓存（多级内存）方向的深入优化，直接服务大规模推理成本控制。
- **PD分离架构修复**：修复decode radix cache所有权问题并支持EAGLE/EAGLE3投机解码，这是Prefill-Decode分离部署这一核心架构的关键稳定性保障。
- **弹性扩展（elastic-ep）**：按DP-attention副本粒度扩展，推进多卡大规模部署的弹性伸缩能力，契合生产环境需求。

### 3. 对项目的影响和潜在意义

- **稳定性提升**：大量模型特定修复（GLM5.2、DeepSeek-V4.1、Qwen-Image 2.1、MiMo）表明项目正加速支持最新模型，每个修复减少特定配置下的运行风险，扩大兼容性覆盖。
- **生产就绪性增强**：Rust前端metrics、NUMA感知的CPU绑定、IPC发送分组等提交明显面向生产运维场景，降低部署调优门槛。
- **多模态和会话优化**：多模态prompt token计数缓存、OpenAI接口层同步修复，提升Agent/会话式使用场景的性能与一致性。
- **sgl-router生态扩展**：cache-aware路由修复混合Mamba/KDA模型、LoRA块ID分离，巩固路由器在动态LoRA和多变体模型场景下的核心路由能力。

### 4. 值得关注的技术点

- **AI辅助开发趋势**：多个提交（#44288、#44252、#43520等）出现Claude Opus系列作为co-author，AI编程助手已深度参与核心推理系统的开发。
- **投机解码（speculative decoding）**：EAGLE/EAGLE3与radix cache的结合、DFLASH verify mask策略修复，反映投机解码已从实验特性走向稳定支持。
- **CuTeDSL/MXFP4**：为MiMo启用native MXFP4路由和CuTeDSL融合，体现对新一代低精度格式和NVIDIA底层DSL的前沿利用。
- **FA4 paged-KV SM90零页表寄存器修复**：涉及FlashAttention4在Hopper架构上的寄存器使用细节，属于深度GPU kernel级优化。

### 5. 对项目发展的影响

结合README所述的"快速LLM与多模态推理"定位，这批提交清晰展现了sglang从功能丰富期向**生产成熟期**的演进：性能提交聚焦真实工作负载的微小开销消除（缓存、IPC、NUMA），架构提交强化PD分离和分层缓存等核心差异化特性，模型覆盖持续跟进业界最新大模型。Rust前端与Python的分工日益清晰，弹性扩展和可观测性的推进意味着项目正对标企业级推理服务平台，而非单纯的推理引擎。这些变更共同巩固sglang在高吞吐、低延迟推理领域的竞争优势。

## 详细提交记录

### [0f36c80](https://github.com/sgl-project/sglang/commit/0f36c8015c3fd250ac52261e61ad56a8131025f1)

- **作者**: Junnan Li
- **时间**: 2026-10-14T23:56:56Z
- **提交信息**: [Bug] Fix multi-tokenizer BatchEmbeddingOutput repack dropping fields (#31892)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [209f822](https://github.com/sgl-project/sglang/commit/209f8220d6f0dacbd7ba2ea6a82ea9adca9bd077)

- **作者**: metamergebot
- **时间**: 2026-10-14T23:44:31Z
- **提交信息**: [Fix] sglang-server: Honour extra_key on the Rust frontend's /generate (#44207)

Co-authored-by: fei-xx <fei-xx@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [e7d6a88](https://github.com/sgl-project/sglang/commit/e7d6a88bfce232fb3441baff1293e9bedeeb37ef)

- **作者**: metamergebot
- **时间**: 2026-10-14T23:43:24Z
- **提交信息**: [HiCache] Buffer-only L3 for an auxiliary SWA window; load back only missing window rows (#43932)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: houseroad <houseroad@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [aa8793f](https://github.com/sgl-project/sglang/commit/aa8793f33b37ce1d8e4265555a06ad83f484601c)

- **作者**: metamergebot
- **时间**: 2026-10-14T23:43:06Z
- **提交信息**: [Rust] Serve scheduler metrics on the Rust frontend's /metrics (#43942)

Co-authored-by: hanminglu <hanminglu@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [2a9f6a2](https://github.com/sgl-project/sglang/commit/2a9f6a25a7394f4fef43d1e18ee04c50bc51b2d8)

- **作者**: metamergebot
- **时间**: 2026-10-14T23:42:30Z
- **提交信息**: [Core] Add subclass hooks for the generation request class and optimistic prefill eligibility (#44113)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: CuiCoco <CuiCoco@users.noreply.github.com>

### [5f2861b](https://github.com/sgl-project/sglang/commit/5f2861bf599767c1d174b434333bd4b97ee57b4a)

- **作者**: metamergebot
- **时间**: 2026-10-14T23:41:34Z
- **提交信息**: [Perf] session: Cache multimodal prompt token counts across turns (#44112)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: joshuadeng <joshuadeng@users.noreply.github.com>

### [9732188](https://github.com/sgl-project/sglang/commit/9732188a58be589673fceca0b654e2c3c78f92d7)

- **作者**: metamergebot
- **时间**: 2026-10-14T23:41:10Z
- **提交信息**: [Rust] Serve /weights_checker from the Rust frontend (#43926)

Co-authored-by: hanminglu <hanminglu@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [97d3150](https://github.com/sgl-project/sglang/commit/97d3150a6a3c412f9445d33c7a91238e590f8b10)

- **作者**: FREETRUMP
- **时间**: 2026-10-14T21:51:26Z
- **提交信息**: [Perf] Cache msgspec struct fields in the batch splitter (#43520)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [4273814](https://github.com/sgl-project/sglang/commit/427381477133c7da86c69fa0e180a7013a71ed1d)

- **作者**: Liu Ke
- **时间**: 2026-10-14T21:26:51Z
- **提交信息**: [Perf] detokenizer: Group return IPC sends by tokenizer worker (#44288)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [d3dc14e](https://github.com/sgl-project/sglang/commit/d3dc14eb3869adcf2291b40c6903a40a77fc6f76)

- **作者**: Charles Chen
- **时间**: 2026-10-14T21:19:51Z
- **提交信息**: [mem_cache][PD] Fix decode radix cache ownership and allow EAGLE/EAGLE3 with decode radix cache (#40857)

Co-authored-by: alphabetc1 <2508695655@qq.com>

### [12dc623](https://github.com/sgl-project/sglang/commit/12dc62310288926b0f38e33ff2d466dee2bf6bb9)

- **作者**: Rain Jiang
- **时间**: 2026-10-14T18:43:37Z
- **提交信息**: [Chore] rust: Remove the sglang-renderer crate (#43451)

### [b677851](https://github.com/sgl-project/sglang/commit/b67785153a5578c8e7114952911773f245838f83)

- **作者**: Shuwen Wang
- **时间**: 2026-10-14T17:28:03Z
- **提交信息**: [Fix] glm5.2: Align HiSparse warmup backends and move test to nightly (#44303)

### [87ed1b9](https://github.com/sgl-project/sglang/commit/87ed1b95266c4ccff9a9e5b0e2fb6143f6ecb7f8)

- **作者**: Yoray Zack
- **时间**: 2026-10-14T17:17:01Z
- **提交信息**: [4/N] elastic-ep: Scale at DP-attention replica granularity (#33728)

### [c964d9b](https://github.com/sgl-project/sglang/commit/c964d9ba207d1f86d2b6ef156efc1525124b9ac7)

- **作者**: Kan Wu
- **时间**: 2026-10-14T16:50:19Z
- **提交信息**: [Feat] sgl-router: Separate LoRA block IDs from prompt lookup keys (#42818)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [3a9cae2](https://github.com/sgl-project/sglang/commit/3a9cae27edec392ff8cc9f09d1164f557c653f42)

- **作者**: amote-i
- **时间**: 2026-10-14T16:27:18Z
- **提交信息**: [Doc] [NPU] docs: Update NPU CANN version to 9.1.0 (#44177)

### [1737251](https://github.com/sgl-project/sglang/commit/1737251730ff00d05e636c5eafcd7067393e4a44)

- **作者**: Michael
- **时间**: 2026-10-14T15:04:23Z
- **提交信息**: [Test] [AMD] diffusion: Run the IPC all-to-all transport tests only on CUDA (#44096)

### [010776e](https://github.com/sgl-project/sglang/commit/010776e94f31a94106fdeeb723fcdd951cb6c4ee)

- **作者**: Kan Wu
- **时间**: 2026-10-14T14:56:28Z
- **提交信息**: [KV events] Publish opaque LoRA block IDs and adapter names (#42817)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [ed40c7f](https://github.com/sgl-project/sglang/commit/ed40c7fc66e74095d215c690c2ff59564a415bc0)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-14T14:40:01Z
- **提交信息**: [Doc] cookbook: add Ling-3.1-flash (#44301)

### [d2a4364](https://github.com/sgl-project/sglang/commit/d2a436446cca3d955358e7b4a5bf6881ea8591cd)

- **作者**: Kan Wu
- **时间**: 2026-10-14T13:21:01Z
- **提交信息**: [Feat] sgl-router: Fix cache-aware routing for MTP/EAGLE on hybrid (Mamba/KDA) models (#44252)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [204644c](https://github.com/sgl-project/sglang/commit/204644c2dc0e65ada5f93c5742e7a47388771fd6)

- **作者**: Kan Wu
- **时间**: 2026-10-14T13:06:13Z
- **提交信息**: [Fix] sglang-processor: Follow Python's OpenAI layer through #43027, #37577, #43006, #43026, #43005 (#44243)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [5e90312](https://github.com/sgl-project/sglang/commit/5e90312eb1e123e3d7f05e009fc1c2e3811a5e2e)

- **作者**: triple-mu
- **时间**: 2026-10-14T12:47:46Z
- **提交信息**: [diffusion] perf: support bit-exact norm/bias fusions and channels_last decode for Qwen-Image 2.1(#41340)

### [7b53a13](https://github.com/sgl-project/sglang/commit/7b53a134016c23f554647534a3b4f78d4ea055e1)

- **作者**: Shuwen Wang
- **时间**: 2026-10-14T12:40:28Z
- **提交信息**: [Fix] glm5.2: Align PD HiSparse prefill KV layout (#44256)

### [bab9c81](https://github.com/sgl-project/sglang/commit/bab9c81fea62c2d20b646736c918c88fea54b7a2)

- **作者**: razorback16
- **时间**: 2026-10-14T11:10:15Z
- **提交信息**: fix: FA4 paged-KV zero-size page-table registers on SM90 (#35757)

Co-authored-by: razorback16 <razorback16@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: BBuf <1182563586@qq.com>

### [3b72b70](https://github.com/sgl-project/sglang/commit/3b72b70ef4afb3b2fd670b34f93b189000ad28bb)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-14T09:50:18Z
- **提交信息**: [CI] vlm: Pin baidu/Unlimited-OCR revision in test_unlimited_ocr_server (#44235)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c82e8bd](https://github.com/sgl-project/sglang/commit/c82e8bd5fe9cad787c2cd3ccf067a1ba5b95e0c4)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-14T09:31:19Z
- **提交信息**: [Fix] DeepSeek-V4.1: Align paged indexer score rows for DeepSelect decode (#44210)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [df1a089](https://github.com/sgl-project/sglang/commit/df1a089cd39e02ad56eb5dfe5e561a77cfb93cbe)

- **作者**: elvischenv
- **时间**: 2026-10-14T09:15:36Z
- **提交信息**: [Spec] Fix DFLASH verify mask policy for wrapped attention backends (#43054)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [817781b](https://github.com/sgl-project/sglang/commit/817781b8285ef4ac39ef4abf415b02241c8fc82e)

- **作者**: Kan Wu
- **时间**: 2026-10-14T09:09:35Z
- **提交信息**: [Feat] sgl-router: Render Qwen3.8 (Max, 27B, Flash-Next) through sglang-processor (#43689)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [72730d6](https://github.com/sgl-project/sglang/commit/72730d6360a5894b167500d5d1ad82c34c6bb116)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-14T08:07:40Z
- **提交信息**: [Doc] cookbook: Mirror SA cluster NCCL_CUMEM_ENABLE in AgentX launches, fix GPU counts (#44228)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c54ba66](https://github.com/sgl-project/sglang/commit/c54ba66cd40f32a6a663b537d390570ce2e9fc4e)

- **作者**: leonardHONG
- **时间**: 2026-10-14T07:39:44Z
- **提交信息**: [Perf] Enable native MXFP4 routing and CuTeDSL fusion for MiMo (#43639)

Co-authored-by: lianghougong <lianghouhong@xiaohongshu.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [6daae9c](https://github.com/sgl-project/sglang/commit/6daae9c98eca1ab6704c8fe71a72665fece93da9)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-14T07:01:32Z
- **提交信息**: [Perf] Bind scheduler CPUs to the GPU's NUMA node when memory policy is not permitted (#44023)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1292
- **最后更新**: 2026-10-14T08:56:22Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## cache-dit 仓库昨日提交分析（1批，共2条）

### 1. 主要更新类型
- **功能新增（核心）**：FFPA attention 后端的功能增强，包括支持 `attn_mask` 和扩大硬件兼容范围（sm_89）。
- **文档更新**：README 同步更新，保持与代码功能一致。

### 2. 关键变更点及与项目方向的关系
- **Attention Mask 支持**：FFPA 后端现在接受 1-D 到 4-D 的 `attn_mask`（1-D/2-D 自动扩展为 `[B,1,1,Nkv]`，3-D/4-D 直接透传）；含 mask 的调用强制走 HND 路由。这直接服务于 DiT 推理中常见的条件控制、序列掩码等场景，是推理引擎完备性的重要一环。
- **硬件覆盖扩大**：fp16/fp8 路径新增 sm_89（Ada Lovelace 架构，如 RTX 40 系列）支持；fp4 和 NHD 快速路径仍保持 sm_120 专属。这降低了用户硬件门槛，扩大了可部署设备范围。
- **测试保障**：新增 70 个测试用例，覆盖 mask 与 SDPA 的数值一致性对比及架构矩阵测试，体现了对多硬件正确性的重视。
- **README 更新**：文档随功能同步，确保用户了解最新的能力边界。

### 3. 对项目的影响和潜在意义
- **功能完备性提升**：mask 支持使 FFPA 后端能够处理更复杂的推理任务（如分块生成、条件注入），减少了用户回退到非优化后端的需要，有利于保持全链路的加速收益。
- **生态扩展**：sm_89 支持意味着大量消费级和工作站级 GPU 用户可以直接使用 fp16/fp8 加速路径，对开源推理引擎的社区采用率有积极推动。
- **质量信号**：大量测试用例和架构矩阵的引入，向潜在用户传递了稳定性与可信度信号，对项目口碑有利。

### 4. 值得关注的技术点
- **掩码的维度自适应策略**：低维 mask 自动广播为 `[B,1,1,Nkv]` 形状，平衡了接口易用性与底层性能要求。
- **HND/NHD 路由选择**：含 mask 时强制 HND 路径，说明 NHD 快速路径对 mask 的支持尚不完善，这是后续优化的潜在方向。
- **架构分层支持**：fp4 与 NHD fast path 仅限 sm_120（Blackwell），反映出对最新硬件特性的前瞻布局，同时以条件编译/分支方式保证旧硬件兼容。
- **与 SDPA 的 parity 测试**：以 PyTorch 原生实现为基准做数值一致性验证，是自定义 kernel 开发的最佳实践。

### 5. 对项目整体发展的贡献
结合 README，cache-dit 是一个专注 DiT 推理的 PyTorch 原生引擎，核心卖点是 Cache、并行、量化和 CPU Offload。本次提交在 **量化（fp16/fp8）** 和 **attention 内核** 两个核心方向上均有推进：mask 支持补全了 FFPA 作为主力 attention 后端的能力缺口，sm_89 扩容则把量化加速带给更广泛的用户群体。两者共同强化了项目"在多样硬件上提供高效 DiT 推理"的定位，为后续支持更复杂生成场景（如视频 DiT 的长序列分块推理）奠定了基础。下一步值得关注的是 NHD 路径的 mask 支持以及 fp4 在更多架构上的可用性。

## 详细提交记录

### [3b205e9](https://github.com/vipshop/cache-dit/commit/3b205e902f651a502af2fa819777136ce3449b60)

- **作者**: DefTruth
- **时间**: 2026-10-14T08:56:16Z
- **提交信息**: Update README.md

### [01d5218](https://github.com/vipshop/cache-dit/commit/01d521817e1cc0e36efa000f13f2be0bc8433ada)

- **作者**: DefTruth
- **时间**: 2026-10-14T07:27:01Z
- **提交信息**: feat(attention): support attn_mask and sm_89 on the FFPA backend (#1119)

ffpa: accept attn_mask (1-D/2-D expand to [B,1,1,Nkv], 3-D/4-D pass through; masked calls force the HND route) and admit sm_89 for fp16/fp8 (fp4 and the NHD fast path stay sm_120-only). Tests: 70 cases incl. mask parity vs SDPA and the arch matrix; docs synced.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93801
- **最后更新**: 2026-10-15T00:33:52Z

## 提交统计

- **昨日提交总数**: 74
- **提交者数量**: 65
- **主要提交者**: Zheng Gong, Stefano Castagnetta, xuebwang

## AI分析总结

# vLLM 昨日 74 条提交综合分析

## 一、主要更新类型分布

- **性能优化**：约13条，聚焦投机解码（MRV2 / EAGLE3 / DFlash）、CUDA Graph 捕获与解码索引器优化。
- **Bug 修复**：约30条，占比最大，涵盖 KV Offload、量化精度、注意力后端、多模态模型与工具调用解析。
- **硬件生态**：AMD ROCm 与 Intel XPU 合计约15条，是单一主题中数量最多的。
- **量化与依赖升级**：MXFP4/FP8 量化、在线量化扩展至 MoE，AITER、FlashInfer、DeepGEMM 及 PyTorch 2.14 / Triton 3.8 版本迭代。
- **功能新增**：Decision 3.0、LightOnOCR、GraniteMoe EAGLE3 等新模型支持，Rust 前端增强，`vllm bench forward` 基准工具。
- **CI / 安全 / 文档**：含 stale PR 自动同步主分支、日志测试修复与一次安全加固。

## 二、关键变更与项目方向

这些提交从三个维度支撑 README 中"Easy, fast, and cheap"的定位：

1. **Fast——推理性能持续压榨**：DSv4.1 解码索引器引入长度感知候选块选择；DFlash 将 context combine 与 anchor 捕获进草稿 CUDA Graph；MRV2 跳过空草稿重置并预热 top-k/top-p 与贪心拒绝核；GPT-OSS 启用批量分片采样；Nemotron-Parse 图像预处理迁至 GPU；PaddleOCR-VL 视觉编码器批处理；GDN prefill 跳过冗余元数据，均在降低每 token 延迟与 CPU 开销。
2. **Cheap & Easy——硬件与量化普惠**：ROCm 大量投入（AITER 升级至 v0.1.25、gfx942/gfx950 上 FlyDSL GDN prefill 默认开启、gfx90a 的 rms_norm 兼容修复、FP8 查询 Triton 注意力、MLA prefill unpad 修复）；Intel XPU 启用 torch 作为 MXFP8 linear 后端；MXFP4 MoE 配 FP8 激活、FP8 scale 在 UE8M0 舍入前钳制、在线量化 API 泛化到任意在线 MoE 方法（NVFP4 / ModelOpt / Quark），显著降低低比特部署门槛。
3. **稳定性与分层卸载**：NIXL 1.5 分层描述符准备、KV Offload 通用配置指标与多条计数时序修复（pin 保留、比例丢弃、超时任务回收），表明分层卸载正从实验特性走向稳定。

## 三、值得关注的技术点

- **投机解码栈快速成熟**：MRV2、EAGLE3、DFlash 多路径并行优化，预示其将成为默认推荐路径。
- **Rust 前端持续落地**：修复 `vllm-rs` 环境变量注入问题、ServerInfo 上报 proto schema 版本，服务入口向 Rust 迁移的方向明确。
- **PCP-aware 本地 GPU 索引共享**：跨模块统一 NUMA 绑定逻辑，对多机多卡部署的性能可预测性有实际意义。
- **后端 kernel 组合复杂度上升**：FlashInfer GDN prefill 与 FLA chunk metadata 的互斥处理，需要精细的条件分支管理。
- **可观测性与体验**：缓存盐与 tracing 进入 OpenAI 兼容层决策路径，便于排查高并发缓存与路由问题；`--reasoning-parser none` 成为默认值，改善 reasoning 模型配置一致性。
- **安全与依赖纪律**：拒绝 Speculators 元数据中的本地验证器引用，收紧元数据可信边界；deep_gemm locality_domain 回退后重新提交，体现依赖升级的谨慎。
- **AI 协作常态化**：大量提交由 Codex、Cursor、Claude、Gemini、Kimi 等 AI 助手共同署名，贡献吞吐显著提升。

## 四、对项目发展的整体影响

模型兼容性维护密集（DeepSeek V4.1、MiniMax-M3、GLM-5.3-Flash、Kimi-K3、Gemma4、Qwen3 工具调用、Cohere v2 JSON schema、GB10 平台 NVML 回退等），大量边界场景 bug 被清理，同时移除临时工具、修复 fork PR CI 合并报告，工程健康度改善。总体而言，vLLM 正从"支持尽可能多的模型"转向"在每条路径上做深性能与稳定性"：AMD 平台从能用走向好用，投机解码与量化从实验走向默认，Rust 前端与 PyTorch 2.14 升级为后续调度与 kernel 优化铺路，持续巩固其在开源 LLM 服务领域的事实标准地位。

## 详细提交记录

### [273a049](https://github.com/vllm-project/vllm/commit/273a04964ed9d1e389c4a7cb9d660e8294782f8d)

- **作者**: josh-schell-amd
- **时间**: 2026-10-14T23:50:24Z
- **提交信息**: [ROCm] Bump AITER to v0.1.25 and relax the DSv4.1 mono MoE tolerance (#61697)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [7840bed](https://github.com/vllm-project/vllm/commit/7840bede989adc226d35e893f29deec1814734f7)

- **作者**: Aarushi Jain
- **时间**: 2026-10-14T23:00:44Z
- **提交信息**: [ROCm][CI] Add AMD jobs for test groups that only exist in tes… (#59678)

Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [4b61f30](https://github.com/vllm-project/vllm/commit/4b61f300c04ddfed4d2188b06b273085518a1960)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-14T22:26:15Z
- **提交信息**: [CI] Fix /ci run reporting a failed merge on fork PRs (#61684)

Signed-off-by: khluu <khluu000@gmail.com>

### [a4d553a](https://github.com/vllm-project/vllm/commit/a4d553a46ac112d43d6cf90735a363ee5549a394)

- **作者**: Micah Williamson
- **时间**: 2026-10-14T21:57:44Z
- **提交信息**: Revert "[Build] Update deep_gemm git tag for locality_domain update" (#61703)

### [9a648b4](https://github.com/vllm-project/vllm/commit/9a648b4649de263e5b19d9e2a50d56693380a416)

- **作者**: Rohan Potdar
- **时间**: 2026-10-14T21:44:55Z
- **提交信息**: [ROCm][Kimi-K3] Don't read W_UK_T before weight loading in the MLA wrapper (#61654)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4c5ea86](https://github.com/vllm-project/vllm/commit/4c5ea86f53a2a9cc8930a25057e2c5551d3651db)

- **作者**: Ben Browning
- **时间**: 2026-10-14T21:25:41Z
- **提交信息**: [Bugfix][Parser] Stream Gemma4 string tool arguments incrementally (#61494)

Signed-off-by: Ben Browning <56071+bbrowning@users.noreply.github.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [984c242](https://github.com/vllm-project/vllm/commit/984c242ede0beaf1c3ba9eb4c01b98bed8973eac)

- **作者**: Misha Goin
- **时间**: 2026-10-14T20:33:35Z
- **提交信息**: [Quantization] Support compressed-tensors MXFP4 MoE with FP8 activations via Mxfp4MoEMethod (#59815)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [fe98d90](https://github.com/vllm-project/vllm/commit/fe98d90a9d0288307afc557e298c6c71947e4045)

- **作者**: Jinzhen Lin
- **时间**: 2026-10-14T20:32:36Z
- **提交信息**: [Dependency] Update Humming and remove NVFP4 scale workaround (#61556)

Signed-off-by: jinzhen.ljz <jinzhen.ljz@antgroup.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [2e8a593](https://github.com/vllm-project/vllm/commit/2e8a5930f603d62cdd371385adb7eeaf55919365)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-14T20:30:18Z
- **提交信息**: [Benchmark] Remove the temporary bench forward dummy loader (#61676)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7c3f7e5](https://github.com/vllm-project/vllm/commit/7c3f7e5500c85aacb72aab50bd1ce05485b1d73a)

- **作者**: Juntian Liu
- **时间**: 2026-10-14T20:15:58Z
- **提交信息**: [Perf][DSv4.1] Length-aware candidate block selection in the decode indexer (#61039)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>

### [2622ee2](https://github.com/vllm-project/vllm/commit/2622ee21aa4a9428aa0fc9a854c8aaacb5174643)

- **作者**: rasmith
- **时间**: 2026-10-14T19:48:37Z
- **提交信息**: [ROCm][BugFix] Don't use AITER rms_norm as an IR OP on gfx90a when AITER always on. (#59290)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e73fa00](https://github.com/vllm-project/vllm/commit/e73fa00981f0e30fc2cc0d77013160b705077106)

- **作者**: alp
- **时间**: 2026-10-14T19:42:20Z
- **提交信息**: [Bugfix][Frontend] Apply the JSON schema in Cohere Chat v2 response_format (#60586)

Signed-off-by: mottopanikeiku <176798723+mottopanikeiku@users.noreply.github.com>
Co-authored-by: mottopanikeiku <176798723+mottopanikeiku@users.noreply.github.com>

### [ded7ae3](https://github.com/vllm-project/vllm/commit/ded7ae35e56f8304f8232fadd890804929527247)

- **作者**: Chris Leonard
- **时间**: 2026-10-14T19:41:16Z
- **提交信息**: [Build] Update deep_gemm git tag for locality_domain update (#61491)

Signed-off-by: Chris Leonard <chleonar@redhat.com>
Signed-off-by: Shengqi Chen <harry-chen@outlook.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [388a610](https://github.com/vllm-project/vllm/commit/388a610dfb5f462261cc1ec27bc2e3bebc0249ca)

- **作者**: Juntian Liu
- **时间**: 2026-10-14T19:40:52Z
- **提交信息**: [Perf][DFlash] Capture context combine and anchor in the draft CUDA graph (#59511)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [4975fda](https://github.com/vllm-project/vllm/commit/4975fda88247eae37c665deb4fb106e1790548c2)

- **作者**: Wei Zhao
- **时间**: 2026-10-14T19:31:08Z
- **提交信息**: [Dependency] Upgrade FlashInfer to 0.7.1 (#60948)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [9b5c670](https://github.com/vllm-project/vllm/commit/9b5c6707a3064db25e1045c1c47674b1885da54c)

- **作者**: Ayushman Singh
- **时间**: 2026-10-14T19:20:48Z
- **提交信息**: [Bugfix][MRV2] Capture DCP FULL cudagraphs with KV context (#61496)

Signed-off-by: Ayushman Singh <40520701+ayush1399@users.noreply.github.com>

### [222e00f](https://github.com/vllm-project/vllm/commit/222e00fc4450ee1fc2fa7cd408a486a05f7243ab)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-14T19:17:59Z
- **提交信息**: [CI/Build] Fix test_deepseek_v41_mxfp8_scale_loading after #57797 (#61678)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [e96c822](https://github.com/vllm-project/vllm/commit/e96c822660df434bd2868ab08667892eb5633be9)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-14T19:13:48Z
- **提交信息**: [Bugfix][ROCm][MiniMax-M3] Reject unbuilt index-head counts in the AITER indexer (#60990)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [21e207e](https://github.com/vllm-project/vllm/commit/21e207efa11c2645d232d700cc6da97bd59d195d)

- **作者**: Sandeep Agrawal
- **时间**: 2026-10-14T19:09:06Z
- **提交信息**: [Bugfix][MRV2][Spec Decode] Honor EAGLE3 single-state draft configuration (#61563)

Signed-off-by: Sandeep Agrawal <sandeepa@nvidia.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [06265be](https://github.com/vllm-project/vllm/commit/06265beb259fa2216d0f99b2dee2285c7cef8ef6)

- **作者**: amd-xavierwang
- **时间**: 2026-10-14T19:03:20Z
- **提交信息**: [ROCm] Enable fp8 query for Triton attention (#60296)

Signed-off-by: xawang <xawang@amd.com>
Co-authored-by: JartX <sagformas@epdcenter.es>

### [857ddac](https://github.com/vllm-project/vllm/commit/857ddac4e535fd93b0dd56e72916c2870ea2d50c)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-10-14T19:01:01Z
- **提交信息**: [Perf][MRV2] Skip empty draft-token resets on request admission (#61640)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [c1407a7](https://github.com/vllm-project/vllm/commit/c1407a7e86a8666cb9223e8e2b818ef4b81e53c0)

- **作者**: qizixi
- **时间**: 2026-10-14T18:59:21Z
- **提交信息**: [Spec Decode][MRV2] Warm up top-k/top-p and greedy rejection kernels for speculative decoding (#59260)

Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [ae94e9c](https://github.com/vllm-project/vllm/commit/ae94e9c9e8e30723dbefb5993c3157ccfb4e0797)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-14T18:58:35Z
- **提交信息**: [Bugfix] Don't crash DeepGEMM MegaMoE warmup when get_bf16_mega_gate_config is missing (#61657)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3f729da](https://github.com/vllm-project/vllm/commit/3f729dafcc5a2ce1bc252734cee3828c6a0678c5)

- **作者**: Simon Danielsson
- **时间**: 2026-10-14T18:48:56Z
- **提交信息**: [Perf][ROCm][GLM-5.3-Flash] AITER prefill indexer topk (#60753)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>

### [e534024](https://github.com/vllm-project/vllm/commit/e534024e490a32cc500555973e2291cb9de9b38f)

- **作者**: lucas-santos-amd
- **时间**: 2026-10-14T18:34:28Z
- **提交信息**: [ROCm][Bugfix][MLA] Fix FP8 MLA prefill unpad for interleave-padded heads (#60907)

Signed-off-by: Lucas Santos <Lucas.Santos@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [d1d8e6c](https://github.com/vllm-project/vllm/commit/d1d8e6c096b628ecdbc19066ec99241340d3d5b3)

- **作者**: Hangrui Cao
- **时间**: 2026-10-14T18:33:22Z
- **提交信息**: [Perf][Nemotron-Parse] Do image rescale/normalize on the device (#60500)

Signed-off-by: DiegoCao <DiegoCao@users.noreply.github.com>
Co-authored-by: DiegoCao <DiegoCao@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0b6d07c](https://github.com/vllm-project/vllm/commit/0b6d07cbe2b607f12d330cff4afccd3d2483c1a8)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-14T18:29:12Z
- **提交信息**: [CI/Build] Use FileStore for DeepEP test rendezvous (#56595)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [d3f6b2a](https://github.com/vllm-project/vllm/commit/d3f6b2a7b3c7c8dbec869b05eafa478601b4a27a)

- **作者**: Robert Shaw
- **时间**: 2026-10-14T18:27:58Z
- **提交信息**: [Frontend] Clean Client Facing 500 Report (#58043)

Co-authored-by: Claude <noreply@anthropic.com>

### [47232f3](https://github.com/vllm-project/vllm/commit/47232f3c7faf616a725ad62efe38e47f6df930a5)

- **作者**: Ganesh R
- **时间**: 2026-10-14T18:14:58Z
- **提交信息**: [Bugfix][CI] Fix renderers tests broken by tool name removal from warn logs (#61652)

Signed-off-by: Ganesh R <ganesh.r@amd.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [52a8cc5](https://github.com/vllm-project/vllm/commit/52a8cc53161103bbda2351d6ec1ed6f7279eb0d8)

- **作者**: Rohan Potdar
- **时间**: 2026-10-14T18:04:14Z
- **提交信息**: [ROCm][CI] Add dtype to the KDA metadata test's fake model config (#61650)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9d3dfa2](https://github.com/vllm-project/vllm/commit/9d3dfa2886ae0b3b248f563c678ff3616658c5f6)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-14T17:52:26Z
- **提交信息**: [Benchmark] Add vllm bench forward: exact-shape forward timing (#61339)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2c74fd1](https://github.com/vllm-project/vllm/commit/2c74fd1873e36a1ee76d6b9dc8ef3c5e5ef80092)

- **作者**: Taimys
- **时间**: 2026-10-14T17:11:11Z
- **提交信息**: [Model Runner V2] Enable batch-sharded sampling for GPT-OSS (#61257)

Co-authored-by: OpenAI Codex <codex@openai.com>

### [89cab55](https://github.com/vllm-project/vllm/commit/89cab550862e4b7f08d70c19682121362d7dd0c5)

- **作者**: Xunzhuo
- **时间**: 2026-10-14T17:10:55Z
- **提交信息**: [Model] Support Decision 3.0 decision models (vllm-sr/d3) (#61565)

Signed-off-by: Xunzhuo Liu <xunzhuo.liu@amd.com>

### [3895a8b](https://github.com/vllm-project/vllm/commit/3895a8babee2aed49c203f4214c119c393a867c0)

- **作者**: zexplorerhj
- **时间**: 2026-10-14T17:09:23Z
- **提交信息**: [Bugfix] Fix TP loading of small block-FP8 MLA gates in BailingMoeV3 (#61642)

Signed-off-by: zexplorerhj <zhjoneson@163.com>
Co-authored-by: Codex <noreply@openai.com>

### [e2e3e2b](https://github.com/vllm-project/vllm/commit/e2e3e2b8340b014a597ffa7368a7f22d250041a2)

- **作者**: SeongJun Lee
- **时间**: 2026-10-14T17:04:07Z
- **提交信息**: [CI] Use an ungated model in the DGX Spark XQA test (#61416)

Signed-off-by: lesj0610 <lesj0610@gmail.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [3e851a7](https://github.com/vllm-project/vllm/commit/3e851a7803c98491cdcbf8f1dec0fcf992948b6d)

- **作者**: Harry Mellor
- **时间**: 2026-10-14T16:38:52Z
- **提交信息**: [Bugfix][Attention] Make the query contiguous for TRTLLM ragged MLA prefill (#61634)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [355553a](https://github.com/vllm-project/vllm/commit/355553ac22dca4080929ea8f88a446f15df1f3ba)

- **作者**: Zheng Gong
- **时间**: 2026-10-14T16:15:51Z
- **提交信息**: [ROCm][Perf] Drop two dead per-step ops from the AITER sparse MLA metadata build (#58354)

Signed-off-by: ZhengGong-amd <zgong@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [13dbf96](https://github.com/vllm-project/vllm/commit/13dbf96093cbae69692a72717933a68691aea9cf)

- **作者**: Itay Etelis
- **时间**: 2026-10-14T16:10:10Z
- **提交信息**: [Model Loader] Apply EP weight filtering in InstantTensor (#61167)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [eaf25f6](https://github.com/vllm-project/vllm/commit/eaf25f675a4eee6a256cc984f37014db109ba39b)

- **作者**: Nick Hill
- **时间**: 2026-10-14T16:07:24Z
- **提交信息**: [NIXL] Prepare KV transfer descriptors as NIXL 1.5 strided lists (#61032)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Ilia Yastrebov <iyastrebov@nvidia.com>

### [9e2b579](https://github.com/vllm-project/vllm/commit/9e2b579aabe9f289791867de539f999c188b63cd)

- **作者**: Nan Zhang
- **时间**: 2026-10-14T16:01:14Z
- **提交信息**: [Model] Support EAGLE3/DFlash aux hidden states for GraniteMoe and GraniteMoeShared (#61110)

Signed-off-by: ZN1010 <neilzhang1010@126.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [e2aabc8](https://github.com/vllm-project/vllm/commit/e2aabc8b1521aad382b439e6be4e740d8e8211eb)

- **作者**: dingdangmao
- **时间**: 2026-10-14T15:31:31Z
- **提交信息**: [Bugfix][KV Offload][P2P] Keep store pins and AbortAck until NIXL transfers stop (#59790)

Signed-off-by: apex-mochen <2756823972@qq.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [5d88c03](https://github.com/vllm-project/vllm/commit/5d88c034f605fa10f4620f0c9c1322bfce9615ab)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-10-14T15:30:20Z
- **提交信息**: [Security] Reject local verifier references in Speculators metadata (#61587)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [bf6c80c](https://github.com/vllm-project/vllm/commit/bf6c80c7e80c2c88547a5caca3a3f9b1ea321f0b)

- **作者**: sfbemerk
- **时间**: 2026-10-14T15:03:11Z
- **提交信息**: [Misc] Remove tool name from warn logs (#59294)

Signed-off-by: Benjamin Merkel <benjamin.merkel@tngtech.com>
Co-authored-by: Benjamin Merkel <benjamin.merkel@tngtech.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [efad400](https://github.com/vllm-project/vllm/commit/efad400092bac444608ffdac937431239696a06f)

- **作者**: Itay Etelis
- **时间**: 2026-10-14T14:28:26Z
- **提交信息**: [HiSparse] Prefault the shared host pool in parallel (#60869)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [02653fa](https://github.com/vllm-project/vllm/commit/02653fa22cd1232cd252165b901091bd4a96f04f)

- **作者**: Thuongvu Ho
- **时间**: 2026-10-14T14:05:21Z
- **提交信息**: [Bugfix][KV Offload] Fix inaccurate proportional store dropping (#59140)

Signed-off-by: Thuongvu Ho <thuongvuho@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [b4b7eca](https://github.com/vllm-project/vllm/commit/b4b7eca0ef35cfcbec85170f894bb4ef1537e3bc)

- **作者**: Ashish Rao
- **时间**: 2026-10-14T13:56:42Z
- **提交信息**: [Bugfix][Quantization] Clamp FP8 scales before UE8M0 rounding (#58032)

Signed-off-by: Ashish Rao <asrao@nvidia.com>
Co-authored-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>

### [7115b70](https://github.com/vllm-project/vllm/commit/7115b70c0170797cb3f0ed98b7ae761f6fe9bcb3)

- **作者**: Sohom chakraborty
- **时间**: 2026-10-14T13:22:28Z
- **提交信息**: [Bugfix][KV Offload][P2P] Drop a timed-out store job's blocks from the round's parked supply (#59329)

Signed-off-by: Sohom Chakraborty <16609933+sohom-cs@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [2d09fdc](https://github.com/vllm-project/vllm/commit/2d09fdcdc213eaf9087766bd6f7b7c055bb346e3)

- **作者**: Luca Motz
- **时间**: 2026-10-14T12:59:50Z
- **提交信息**: [Quantization] Auto-disable DeepGEMM for Kolibri 1 on SM12x (#61274)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3723a1e](https://github.com/vllm-project/vllm/commit/3723a1ea96df967f7cef21ef6ea5b4af6c529807)

- **作者**: Frank
- **时间**: 2026-10-14T12:56:54Z
- **提交信息**: [Bugfix][Transformers backend] Fix CUDA graph capture for dynamic-rope models (#58064)

Signed-off-by: YongfengX <erkang040804@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [2631afd](https://github.com/vllm-project/vllm/commit/2631afd3fe33f02d186b983131fcc7b48b20e5c0)

- **作者**: hcl
- **时间**: 2026-10-14T12:45:29Z
- **提交信息**: [Bugfix][Platform] Fall back to torch when device-level NVML memory is unsupported (GB10) (#57378)

Signed-off-by: hclsys <chenglunhu@gmail.com>
Signed-off-by: Chenglun Hu <chenglunhu@gmail.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [a68dbba](https://github.com/vllm-project/vllm/commit/a68dbbad0524a776b171860cef819ce9251c3b63)

- **作者**: Kapil Arya
- **时间**: 2026-10-14T12:43:04Z
- **提交信息**: [Bugfix][KV Offload] Retain offload mappings after unsafe KVCR startup failure (#57500)

Signed-off-by: Kapil Arya <kapila@nvidia.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [775fefa](https://github.com/vllm-project/vllm/commit/775fefa804cafce395c3bb7497c003f04e534616)

- **作者**: Amir Friedman
- **时间**: 2026-10-14T12:34:37Z
- **提交信息**: [Metrics][KV Offload] Add vllm:kv_offload_config_info - generic info metrics for offloading the offloading connector (#56867)

Signed-off-by: Amir Friedman <Amir.Friedman1@ibm.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [3a5a6b1](https://github.com/vllm-project/vllm/commit/3a5a6b11a3d70707ea6615e2dbc2a0780dca2e4c)

- **作者**: ssingh231219
- **时间**: 2026-10-14T11:59:44Z
- **提交信息**: [Perf][Model] Batch PaddleOCR-VL vision encoder and projector (#61458)

Signed-off-by: ssingh231219 <simran.singh@artificialy.com>

### [d39c2fb](https://github.com/vllm-project/vllm/commit/d39c2fb05a6cfba7d4be48e17cca71ec114257f3)

- **作者**: sudhanshu shukla
- **时间**: 2026-10-14T11:27:44Z
- **提交信息**: [Bugfix][Gemma4] Quantize audio towers independently (#59935)

Signed-off-by: sudhanshu shukla <sudhanshu112233shukla@users.noreply.github.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: sudhanshu shukla <sudhanshu112233shukla@users.noreply.github.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [23fbc2e](https://github.com/vllm-project/vllm/commit/23fbc2ec2f7219888bfc76cf987381f501151971)

- **作者**: Lazurite
- **时间**: 2026-10-14T10:54:09Z
- **提交信息**: [Model] Support precomputed image embeddings for LightOnOCR (#61585)

Signed-off-by: Rapisurazurite <43494437+Rapisurazurite@users.noreply.github.com>

### [8150355](https://github.com/vllm-project/vllm/commit/81503550f379b5a83bc091073bc2a2f2ebe67ff5)

- **作者**: xuebwang
- **时间**: 2026-10-14T10:46:02Z
- **提交信息**: [ROCm] Disable AITER FP8/FP4 BMM for MLA by default (#53123)

Signed-off-by: xuebwang-amd <xuebwang@amd.com>

### [c67c69e](https://github.com/vllm-project/vllm/commit/c67c69e657254dace058ed5250a29f884cf4a19b)

- **作者**: linshi wang
- **时间**: 2026-10-14T10:34:10Z
- **提交信息**: [Bugfix][KV Offload] Track allocated block IDs when num_external_tokens is 0 (#47046)

Signed-off-by: linshi-w <linshiw.edu@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [6ecb39e](https://github.com/vllm-project/vllm/commit/6ecb39eaa7c55b26afd39b76a87b44f33053bdff)

- **作者**: wang.yuqi
- **时间**: 2026-10-14T10:28:22Z
- **提交信息**: [Docs] Update structured decisions docs. (#61588)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [19aba3e](https://github.com/vllm-project/vllm/commit/19aba3e4d59baf0bc1c1433cea3ccb3065ed00c9)

- **作者**: Ronald
- **时间**: 2026-10-14T10:17:58Z
- **提交信息**: [Bugfix][RL] Load attention sinks through weight_loader for layerwise reload (#57797)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [f9b65c3](https://github.com/vllm-project/vllm/commit/f9b65c30c7b518600b622d4b683c9f2f1eb04370)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-14T10:11:57Z
- **提交信息**: [ROCm][Perf] Make AITER FlyDSL GDN prefill default on gfx942/gfx950 (#60645)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [3f466c8](https://github.com/vllm-project/vllm/commit/3f466c852cfd3882820af8dd7963ac775174bce4)

- **作者**: Abhay Joshi
- **时间**: 2026-10-14T10:01:25Z
- **提交信息**: [Bugfix][Parser] Recover genuine tool calls after unclosed Qwen3 <function= opener in prose (#59928)

Signed-off-by: Abhay Joshi <105213625+abhayjoshi201@users.noreply.github.com>
Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Gemini <noreply@google.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [8a8e2ba](https://github.com/vllm-project/vllm/commit/8a8e2baa02cdd3d98ee99dbead0a8c9943a97410)

- **作者**: Isotr0py
- **时间**: 2026-10-14T09:09:08Z
- **提交信息**: [Bugfix][Rust Frontend] Inject VLLM_USE_RUST_FRONTEND=1 into `vllm-rs` managed engine envs  (#61586)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [be4ce2e](https://github.com/vllm-project/vllm/commit/be4ce2e50545c6c1bf13f224022aeb2bcf0c0070)

- **作者**: Sherif Waly
- **时间**: 2026-10-14T08:54:03Z
- **提交信息**: [Bugfix] Share PCP-aware local GPU indexing for NUMA binding (#61237)

### [937d6c1](https://github.com/vllm-project/vllm/commit/937d6c19dfec2f928b5c75562c932de2070a40a7)

- **作者**: Thien Tran
- **时间**: 2026-10-14T08:46:54Z
- **提交信息**: [Perf][GDN] Skip FLA chunk metadata when FlashInfer GDN prefill is active (#61569)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [d36158f](https://github.com/vllm-project/vllm/commit/d36158f9193bc635f16952d401f577bf5e1f3052)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-14T08:43:03Z
- **提交信息**: [CI] Merge the target branch into stale PRs on /ci run (#61592)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [bb1438a](https://github.com/vllm-project/vllm/commit/bb1438a93f8873c30176d93267d0647f8e4c7b83)

- **作者**: Artem Perevedentsev
- **时间**: 2026-10-14T08:24:24Z
- **提交信息**: [CI] Fix Unlimited-OCR loading after upstream `model_type` rename (#61590)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [467b024](https://github.com/vllm-project/vllm/commit/467b024f21b055839ef396def9b08d9c64208932)

- **作者**: Alec
- **时间**: 2026-10-14T08:21:48Z
- **提交信息**: [Rust Frontend] Report vllm-proto schema version in ServerInfo (#61533)

Signed-off-by: Alec Flowers <aflowers@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [aa0c433](https://github.com/vllm-project/vllm/commit/aa0c433a3e5ee65641b7996e56c018ce91f9273d)

- **作者**: Alec
- **时间**: 2026-10-14T07:50:35Z
- **提交信息**: [Frontend] Accept `--reasoning-parser none` as the unset default (#61525)

Signed-off-by: Alec Flowers <aflowers@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [c9bfa57](https://github.com/vllm-project/vllm/commit/c9bfa574ce690e45d1da5d506d17ed1586dcf9dd)

- **作者**: fxmarty-amd
- **时间**: 2026-10-14T07:49:37Z
- **提交信息**: [Online quantization] Extend re-quantization API to MOE (showcase `NVFP4 modelopt/CT/quark` to any online MOE method) (#60276)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Signed-off-by: Tan Pin Siang <tanpinsiang@gmail.com>
Co-authored-by: vllmellm <vllm.ellm@embeddedllm.com>
Co-authored-by: Tan Pin Siang <tanpinsiang@gmail.com>

### [e1726d9](https://github.com/vllm-project/vllm/commit/e1726d9142b1d32ebba18b15b20c8157609a0aa5)

- **作者**: Chauncey
- **时间**: 2026-10-14T07:48:44Z
- **提交信息**: [Frontend] Add cache salt and tracing to openai decisions (#61550)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [4dc5add](https://github.com/vllm-project/vllm/commit/4dc5add6ea71427c7bad707ee1b1c88891142e5f)

- **作者**: zofia
- **时间**: 2026-10-14T07:48:38Z
- **提交信息**: [XPU] [Linear] [MXFP8] enable torch as mxfp8 linear backend (#51933)

Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>
Signed-off-by: zofia <110436990+zufangzhu@users.noreply.github.com>

### [ec8a372](https://github.com/vllm-project/vllm/commit/ec8a3725668418b156fe2fd5c85ae3b1b9e37ad9)

- **作者**: Ronald
- **时间**: 2026-10-14T07:19:38Z
- **提交信息**: [ROCm][Bugfix] Pin AITER back to v0.1.24.post1 for DSv4.1 mono decode numerics (#61559)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>

### [30e79c3](https://github.com/vllm-project/vllm/commit/30e79c3a766c628fa005146d713ae72530be2b76)

- **作者**: Andrey Talman
- **时间**: 2026-10-14T07:17:59Z
- **提交信息**: [Core] Update PyTorch to 2.14.0, torchvision to 0.29.0, triton to 3.8.0 (release channel) (#52183)

Signed-off-by: Andrey Talman <atalman@users.noreply.github.com>
Signed-off-by: Andrey Talman <atalman@fb.com>
Co-authored-by: Andrey Talman <atalman@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ec317a4](https://github.com/vllm-project/vllm/commit/ec317a4618c60c1a6edaa3ac8b9758d18ca0244c)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-14T07:10:35Z
- **提交信息**: [CI] Keep vLLM log propagation on through the first LLM init in caplog_vllm (#61535)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-15
**监控日期**: 2026-10-14
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7171
- **最后更新**: 2026-10-14T23:40:43Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 14
- **主要提交者**: Joshna-Medisetty, luca huang, Hongsheng Liu

## AI分析总结

## vllm-omni 昨日提交分析（共20条）

### 1. 主要更新类型分布
- **性能优化**（约6条）：Drama 3 性能优化、Ascend 端 MOSS-Audio-Tokenizer 解码融合、VoxCPM2 批处理 FSQ 融合、Qwen-Image-2.1 Turbo BF16 内核优化等。
- **Bug 修复**（约6条）：Intel Covo/LingBot-Video、MiniMax H3 帧数限制、Drama 3 单帧请求卡死、Diffusion 队列释放等。
- **CI/构建**（3条）：ROCm 测试可靠性标记、BF16 AITER 模块恢复、Omni-DuplexEval 夜间评测。
- **功能新增/模型支持**（3条）：JoyAI 统一全双工文本/视频会话、Wan EG/EGD 分离架构、realtime 接口支持图像输入。
- **文档**（2条）：贡献者预检流程、审查与问题经验沉淀。

### 2. 关键变更与项目方向的关系
项目定位是"人人可用的全模态模型服务"，本次提交集中体现了三条主线：

- **多硬件后端成熟化**：ROCm（AMD）、XPU/Intel Gaudi、Ascend（华为）三大非 NVIDIA 后端均有修复与优化，说明项目正从"以 CUDA 为中心"转向真正的异构多平台支持，尤其 Ascend 的 RoPE 缓存跨层复用和算子融合体现了深度工程优化。
- **全双工/实时多模态能力**：JoyAI duplex、/v1/realtime 图像输入、DuplexEval 夜间评测，强化了低延迟交互场景（语音+视觉）的可用性和质量保障。
- **视频/扩散模型体验**：Drama 3 的性能优化与单帧卡死修复、MiniMax H3 帧数网格对齐、Wan EG/EGD 分离架构（Intel），改善长视频生成的稳定性与吞吐。

### 3. 对项目的影响
- 异构硬件覆盖面扩大，可服务更广泛的企业级部署场景（国产芯片、AMD 数据中心卡）。
- 实时交互路径获得功能扩展与自动化回归保护，降低全双工场景的线上故障率。
- 多个扩散/视频模型的性能与内存观测改进（GiB 日志标注、队列释放修复），提升长会话内存稳定性和可观测性。
- 文档类提交沉淀"设计契约"与审查经验，利于大规模社区协作的一致性。

### 4. 值得关注的技术点
- Ascend 端 **mask sharing + addcmul 融合** 解码优化与 **跨层 RoPE cos/sin 缓存**，是硬件特化优化的典型手法。
- Drama 3 **codec handoff 单帧挂起**修复与默认启用批处理 FSQ 融合，直接关系到低延迟音频编解码的用户体验。
- **EG/EGD 分离架构**（编码/生成解耦）对分布式推理扩展性意义重大。
- 多条提交出现 **AI 编码助手（Cursor、Claude、Codex、opencode）** 作为共同作者，反映社区在用 AI 工具加速多硬件适配。
- MiniMax H3 **17n+5 对齐帧网格**上限，是模型结构约束与服务端参数管理的精细处理。

### 5. 对项目发展的意义
结合 README"easy, fast, cheap omni-modality serving"的愿景，这批提交显示项目正从核心推理能力迈向**生产就绪**：多后端一致性、实时全双工的评测闭环、长视频/扩散场景的资源治理都在补强。ROCm、Intel、Ascend 的持续投入意味着 vllm-omni 有望成为横跨主流与国产加速卡的统一全模态服务栈，配合文档化的协作流程，将有助于吸引芯片厂商和模型团队共建生态，降低全模态应用的部署门槛。

## 详细提交记录

### [d6ed4f4](https://github.com/vllm-project/vllm-omni/commit/d6ed4f4844fbc41573ffc03247e5b2ff0a38d322)

- **作者**: haic0
- **时间**: 2026-10-14T23:40:37Z
- **提交信息**: [CI/Build][ROCm] Mark reliability fault tests for AMD GPU (#8944)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [cb3c189](https://github.com/vllm-project/vllm-omni/commit/cb3c189d9c8973a6a3d376b8264d1c388faf2009)

- **作者**: haic0
- **时间**: 2026-10-14T20:43:57Z
- **提交信息**: [CI/Build][ROCm] Restore the BF16 AITER module in READY consumers (#8939)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [48d9785](https://github.com/vllm-project/vllm-omni/commit/48d9785fd66c5df4a7cc5628494b9ef66c6a542b)

- **作者**: Joshna-Medisetty
- **时间**: 2026-10-14T20:35:30Z
- **提交信息**: [XPU][GR00T] Select the pipeline device from the current platform (#8653)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>

### [d315557](https://github.com/vllm-project/vllm-omni/commit/d3155575df980469fdcaf411c80bfcd3e0135139)

- **作者**: Joshna-Medisetty
- **时间**: 2026-10-14T20:24:46Z
- **提交信息**: [Bugfix][Hardware][Intel] Covo: keep token2wav attention off CUDA-only APIs (#8656)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>

### [db8c982](https://github.com/vllm-project/vllm-omni/commit/db8c9827f9112e7dfac0d41a5e9bdd3fee7d62d8)

- **作者**: Yueqian Lin
- **时间**: 2026-10-14T19:34:07Z
- **提交信息**: [Bugfix] Drama 3: one-frame requests no longer hang in the codec handoff (#8938)

Signed-off-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [c4871a0](https://github.com/vllm-project/vllm-omni/commit/c4871a09b006507ed38e3f4eb2e5db81d18f1191)

- **作者**: Sy03
- **时间**: 2026-10-14T16:41:00Z
- **提交信息**: [Perf][Drama 3] Optimization of Drama3 performance (#8933)

Signed-off-by: Sy03 <1370724210@qq.com>

### [fd6c69d](https://github.com/vllm-project/vllm-omni/commit/fd6c69d32457d40cc736957648b6cf174847d55f)

- **作者**: luca huang
- **时间**: 2026-10-14T14:53:54Z
- **提交信息**: [Misc] Label diffusion runner peak memory log in GiB (#8865)

Signed-off-by: luca-888 <55954511+luca-888@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [910b8f0](https://github.com/vllm-project/vllm-omni/commit/910b8f07d23c7f387729173333c9d5f927dc6c4f)

- **作者**: WeiQing Chen
- **时间**: 2026-10-14T14:29:45Z
- **提交信息**: [Kernel][Model] Optimize Qwen-Image-2.1 Turbo BF16 inference on B300 (#8739)

Signed-off-by: david6666666 <530634352@qq.com>

### [5b46a01](https://github.com/vllm-project/vllm-omni/commit/5b46a01283c58d270af58b111aca03ae3b821758)

- **作者**: jingchengtian
- **时间**: 2026-10-14T14:27:30Z
- **提交信息**: [Hardware][Ascend] Optimize MOSS-Audio-Tokenizer codec decode with mask sharing and addcmul fusion (#8002)

Signed-off-by: jingchengtian <tjc1995@126.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [1b6c6c5](https://github.com/vllm-project/vllm-omni/commit/1b6c6c50cf7aaaff82d579e41072a2fe0057d212)

- **作者**: jingchengtian
- **时间**: 2026-10-14T12:17:48Z
- **提交信息**: [Hardware][Ascend] Cache codec RoPE cos/sin tables across all transformer layers (#7967)

Signed-off-by: jingchengtian <tjc1995@126.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [d8a59b0](https://github.com/vllm-project/vllm-omni/commit/d8a59b0410f57c1398e988cc06d78c1028ac6d7c)

- **作者**: Lingwei1943
- **时间**: 2026-10-14T12:16:02Z
- **提交信息**: [perf][VoxCPM2]: enable batched FSQ fusion and prefill tail by default (#8311)

Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: opencode <opencode@ai>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [5c4eb75](https://github.com/vllm-project/vllm-omni/commit/5c4eb75d40a02abe18f209286aab684daf90ad3a)

- **作者**: Joshna-Medisetty
- **时间**: 2026-10-14T11:28:28Z
- **提交信息**: [Bugfix][Hardware][Intel] LingBot-Video: drive autocast from the tensor device (#8651)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>

### [caaa4cc](https://github.com/vllm-project/vllm-omni/commit/caaa4cc32dbaf943c7c1d0ea7a624bbcd04d091d)

- **作者**: Iryna Boiko
- **时间**: 2026-10-14T11:28:11Z
- **提交信息**: [Bugfix] MiniMax H3: cap num_frames on aligned 17n+5 grid for max duration (#8696)

Signed-off-by: Iryna Boiko <iboiko@habana.ai>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [b124514](https://github.com/vllm-project/vllm-omni/commit/b124514e46901c72b0f143aa8891d568fdf1dae8)

- **作者**: Hongsheng Liu
- **时间**: 2026-10-14T10:33:26Z
- **提交信息**: [Doc] Connect contributor precheck to existing design contracts (#8918)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [1f53c7f](https://github.com/vllm-project/vllm-omni/commit/1f53c7f94d2711416dcdc0efee2e8a6abb363bd7)

- **作者**: NATURE
- **时间**: 2026-10-14T10:29:12Z
- **提交信息**: [Model] Add JoyAI unified duplex text/video sessions (#8823)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [c2ba8e7](https://github.com/vllm-project/vllm-omni/commit/c2ba8e715518d8d8c32f6dfb8f047524fd4681c1)

- **作者**: Nick Cao
- **时间**: 2026-10-14T09:32:22Z
- **提交信息**: [Frontend] Accept image input on /v1/realtime?duplex=0 (#8896)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [858cde6](https://github.com/vllm-project/vllm-omni/commit/858cde64c364182e2c25fe009b2812e435f86297)

- **作者**: Hongsheng Liu
- **时间**: 2026-10-14T09:00:17Z
- **提交信息**: [Doc] Add concise review and issue lessons (#8917)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [9b300b9](https://github.com/vllm-project/vllm-omni/commit/9b300b98338daf1ce3366b6598b870248b5c32f3)

- **作者**: NATURE
- **时间**: 2026-10-14T08:34:49Z
- **提交信息**: [CI/Build] Run Omni-DuplexEval nightly through bench serve (#8871)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [41ed44c](https://github.com/vllm-project/vllm-omni/commit/41ed44cc014dfe0a46499ffd63473addf05777f5)

- **作者**: Rahul Steiger
- **时间**: 2026-10-14T08:14:42Z
- **提交信息**: [Bugfix][Diffusion] Release queues when output streams close before iteration (#8513)

Signed-off-by: Rahul Steiger <rsteiger@nvidia.com>

### [e7c007c](https://github.com/vllm-project/vllm-omni/commit/e7c007cc3fa697e88c866863fdd7602ba0e5afb4)

- **作者**: Yuan Wu
- **时间**: 2026-10-14T07:49:12Z
- **提交信息**: Feat/wan EG/EGD disagg (#6285)

Signed-off-by: yuanwu <yuan.wu@intel.com>
Signed-off-by: N <matrix.yao@intel.com>
Signed-off-by: Yuan Wu <yuan.wu@intel.com>
Co-authored-by: N <matrix.yao@intel.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
