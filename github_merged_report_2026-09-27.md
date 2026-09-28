# GitHub Stars 合并报告 - 2026-09-27

**合并日期**: 2026-09-28
**监控日期**: 2026-09-27
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


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2225
- **最后更新**: 2026-09-24T05:19:34Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2861
- **最后更新**: 2026-09-27T21:17:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2260
- **最后更新**: 2026-09-27T14:02:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6510
- **最后更新**: 2026-09-28T00:08:17Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 1
- **主要提交者**: eigen

## AI分析总结

本次提交汇总了仓库近期（共16个提交）的集中更新，核心是为DeepSeek-V4、Kimi-K3等前沿大模型及最新NVIDIA GPU（如Blackwell/Thor）提供极致性能优化，并增强算子生态支持。

**主要更新**
本次更新以**性能深度优化**为绝对主导，全面覆盖大模型推理的核心计算环节：包括针对DeepSeek-V4稀疏MLA、Kimi-K3 MLA注意力的解码与预填充优化，FP8/MXFP4/NVFP4等低精度投影GEMM，以及MoE路由、权重加载和融合算子。此外，项目扩展了功能支持（如Blackwell AlphaMoE NVFP4算子、更多All-Reduce世界规模）并进行了内核生成工具链与算子后端的重构与加固。

**关键变更**
所有优化均紧密围绕硬件与模型协同展开。一方面，**深度适配最新GPU架构**，充分利用SM100/103（Blackwell）的H128 TMA、WGMMA、L2缓存提示及Thor的MNNVL多播内存等新特性，进行硬件感知的参数调优。另一方面，**针对关键模型算子进行微架构级重构**，例如为MLA注意力重构softmax与PV计算的流水线以减少停顿，为MoE算子实现多路径分发策略，并为采样流程引入基于寄存器的位onic排序以降低固定开销。

**项目影响**
这些变更带来了显著的**直接性能收益**，在目标硬件和模型上可实现10%-30%的延迟降低，有效降低了推理成本。同时，**硬件支持广度得到延伸**，覆盖了从H100到最新GB300及Thor等多种GPU，确保了项目的长期竞争力。通过对MoE等复杂算子的全面优化，项目正从提供独立内核向构建**完整、高效推理流水线**演进，巩固了其作为高性能AI推理基础设施的技术地位。

**技术关注点**
值得关注的技术点包括：**Warp-uniform TMA Gather**，通过坐标广播解决了FP8 MLA中的指令序列化瓶颈；**延迟隐藏与融合**，在Kimi-K3 LatentMoE尾部将多步骤计算与通信融合并利用CUDA Graph执行；**寄存器级优化**，如在NVFP4内核中将量化数据驻留于寄存器以减少内存访问；以及**硬件满载调度**，为不同SM数量的GPU（如R200）重新校准参数，实现高效并行执行。这些技术共同体现了对GPU计算潜力的极致挖掘。

## 详细提交记录

### [4b8167e](https://github.com/flashinfer-ai/flashinfer/commit/4b8167eabfc61647f6a7fc8023355ea59147a918)

- **作者**: eigen
- **时间**: 2026-09-27T23:54:48Z
- **提交信息**: perf(cake_sparse_mla): warp-uniform FP8/H128 TMA gathers and 32-byte epilogue stores in the DSv4 sparse-MLA Cake programs (SM100/SM103) (#5610)

## Summary

Round-2 performance of the `backend="cake"` DeepSeek-V4 sparse-MLA
decode path of `trtllm_batch_decode_sparse_mla_dsv4`
(SM100a / SM103a), regenerated from the same producer pipeline as #5591:

- **FP8/H128 persistent prefill program (prefill-style rows with 128+
query tokens, batch 2-48 items x 16 KV tiles):** the two K and
two V loader warps issued their TMA `gather4` with lane-divergent
coordinates, so ptxas serialised every gather into a 32-iteration
per-lane loop and the loaders spent ~1.0 us of every 1.12-us KV tile
issuing. They now issue from one elected lane with warp-uniform
coordinates (`shfl.sync` broadcast, one unrolled 16-quartet site per
warp with the KV descriptor selected per tile), the same form the
default trtllm-gen kernels use. Same barriers, pipeline depth and data
movement; only the issuing lane changes. The loop is now paced by
the tensor pipe (16 QK + 8 PV MMAs per tile, ~0.8 us).
prefill-style-000089 / 000093: GB300 1.02x / 1.01x -> **1.24x / 1.21x**,
B200 1.05x / 1.06x -> **1.19x / 1.18x** vs the default path. The
persistent seed compiles with `-Xptxas=--register-usage-level=10`
so the exported build keeps the softmax schedule of the source build
(without it ptxas re-orders the exp2/convert chains across
  the P-publication fence: 3-5 % slower on these rows).
- **BF16/H128 K-reuse (snake) prefill program
(`bf16_h128_prefill_v42_snake`, hardening rows 27 / 37):** the epilogue
drains O with
32-byte stores like the striped program already did. hardening-000037:
GB300 1.016x -> **1.107x**, B200 1.028x -> **1.100x**;
  hardening-000027: 1.175x -> 1.190x, 1.172x -> 1.173x.
- Every other program is a byte-identical regeneration (renamed for the
new producer revision).
- New CPU test: registered programs build with public nvcc/ptxas options
only, and the FP8/H128 persistent variants pin the
  register-usage level.

The one-KV-tile SWA-only work items of the BF16/H128 persistent prefill
body (hardening rows 23 / 29 / 35) were re-attributed and
left unchanged: the item is a per-SM chain bound by the SM's L2<->SM
port (256 KB per CTA per item at the measured ~66 GB/s = the
measured 3.9 / 4.1 us period); the byte levers (K-reuse body, four
issuing warps, DSM exchange of the V halves) measured negative
or closed by arithmetic. Those rows stay at 1.03-1.16x.

## Validation

Export r11 (Cake `db0609184cd`, this branch at 8589d49b0 + the
regenerated programs), same-session paired CUPTI (active-union
median, 500 warmup / 3000 calls per arm, cold L2) against the default
trtllm-gen path at the same revision:

| | GB300 (sm_103a) | B200 (sm_100a) |
|---|---|---|
| 94 canonical + 40 hardening shapes correct (BF16 atol=rtol=1e-2, FP8
0.1; padded / separate-table / offset axes) | 134/134 | 134/134 |
| **94 canonical rows faster than the default path** | **94/94, geomean
1.243x, min 1.054x** (#5591: 1.237x, min 1.006x) | **94/94, geomean
1.232x, min 1.041x** (#5591: 1.226x, min 1.013x) |
| 40 hardening rows faster than the default path | **40/40, geomean
1.30x, min 1.058x** (#5591: 1.28x, min 1.016x) | **40/40, geomean 1.25x,
min 1.037x** (#5591: 1.25x, min 1.029x) |
| exported program vs Cake source build (agreement gate, 134 rows) |
geomean 1.002x, every row within 3 % | geomean 1.004x, every row within
3 % |
| compute-sanitizer synccheck + memcheck on the two changed kernels | 0
errors | 0 errors |
| `tests/mla/test_cake_dsv4*.py` (GPU, on the exported programs) | 292
passed | 292 passed |
| `tests/mla/test_cake_dsv4*.py` (CPU, this host) | 210 passed | 210
passed |

## Baselines and their source PRs

- **trtllm-gen default path** =
`trtllm_batch_decode_sparse_mla_dsv4(...)` without `backend="cake"` (the
TRTLLM-GEN DSv4
sparse-MLA kernels plus the framework launches it needs for equal
semantics: padded-Q masking, separate-table merge,
workspace/counter handling). Origin PRs: #3269 (9c76c994b, 2026-05-21,
`flashinfer/decode.py`, `flashinfer/mla/_core.py`,
DSv4 TRTLLM-GEN kernels); SM120 kernels #3395 (f95469478, 2026-06-15);
DSv4.1 unification #5197 (eb5f05be1, 2026-09-18).
- **Cake backend under test** = `backend="cake"` from #4573 (13db2cfd5,
2026-09-16) as hardened and regenerated by #5591
  (8589d49b0, 2026-09-27), regenerated again by this PR.
- **Test oracle** = the PyTorch reference of
`tests/mla/test_cake_dsv4.py` / `test_cake_dsv4_hardening.py` (DSv4
RopeQuant
  exposure #4918, 27d5b0298, 2026-09-07).
- **Branch base** = upstream `main` 8589d49b0 (the #5591 merge); no
upstream commits in between.

## CI

`tests/mla/test_cake_dsv4.py` and
`tests/mla/test_cake_dsv4_hardening.py` (CPU and GPU parametrizations).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved correctness of CAKE DSV4 attention kernels by refining
shared-memory synchronization, sparse gather operations, and pipeline
phase handling.
- Updated output processing to use more efficient vectorized stores in
selected kernels.
- Corrected kernel registration and dispatch across supported GPU
architectures, including updates to available variants and compile
settings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [698a961](https://github.com/flashinfer-ai/flashinfer/commit/698a96197f52759f79256e212d291653d1c9ce40)

- **作者**: eigen
- **时间**: 2026-09-27T23:35:43Z
- **提交信息**: perf(cake_mla): kimi_k3 shape, regenerate both architectures for the r52 kernel (deferred O rescale, wider long-request threshold) (#5602)

## Summary

Regenerates the Cake-generated `backend="cake"` Kimi-K3 MLA FP8 paged
attention route (#5552; v9, r50 and r51 programs in the previous heads
of this PR) for the **r52 kernel** on SM100 (B200) and SM103 (B300 /
GB300). The host side is unchanged from the r51 head (same planner,
grids and kernel arguments), so this head only moves the generated
programs of both architectures; every file is written by the exporter
from the same producer tree.

What r52 changes against the r51 programs (`33b85998c`):

- **Deferred O rescale (wide kernel).** When a row's lazy E4M3 reference
moves at tile t, the softmax warps used to wait for PV(t-1) to retire
and rescale their O lanes in TMEM (four 64-column `tcgen05.ld` /
`tcgen05.st` round trips per warp) *before* storing P(t), so every move
stalled the P publish by 3-4 us and, with the latent K stages held until
PV(t), the load ring behind it. The warps now store P(t) and arrive
`p_full` first, then wait for PV(t-1), rescale and arrive a new
`o_ready` mbarrier (tile parity, 4 warps x 2 CTAs, arrived every tile);
the MMA warp waits `o_ready(t)` with `p_full(t)` before PV(t). Outputs
are unchanged (same FP32-reference max_abs on every checked row).
- **Wider long-request threshold.** Requests with at least 32768 cached
tokens publish their reference 4 (was 2) octaves above the running max,
so a move needs a 6-octave (was 4) jump. On the contract inputs (peaked
profile, one dominant key per row) this cuts the reference moves from
12.65 to 4.1 per mtp_h96_b8_q4 cluster lifetime (8.1 -> 1.5 on the H96
batch-8 decode rows) for the same speed a 7-octave threshold gives on
that row. FP32-reference max_abs over all 25 contract rows stays inside
0.01 / 0.02 with zero mismatches (prefill_h96_b1_q2048_kv131072 0.0029
-> 0.0059 over 100.7 M elements, prefill_h96_b2 0.0068 -> 0.0088,
mtp_h96_b8_q4 0.0012 -> 0.0020); a 7-octave threshold failed that first
row (57 mismatches) and was rejected. Short-KV rows are unchanged.
- Both levers measured on B300 against the r51 tree (main kernel, 3
alternating rounds, CUDA-graph cold-L2): mirror_h96_b8 0.994,
mtp_h96_b8_q2 0.987, mtp_h96_b8_q4 0.985, prefill_h96_b2 0.981 (removing
the rescale path entirely: 0.987 / 0.982 / 0.986 / 0.978).

## Performance (same-session CUPTI cold-L2, CUDA-graph replay, 3
alternating rounds; Cake vs the fastest existing FlashInfer route)

| row | route | B200 Cake us (median of 3) | B200 vs best FI | B300 Cake
us (median of 3) | B300 vs best FI |
|---|---|---:|---:|---:|---:|
| trace_h12_b1_q1_kv76800 | row tiles | 21.1 | **1.173x** | 20.8 |
**1.132x** |
| trace_h12_b2_q1_kv77699 | row tiles | 29.2 | **1.060x** | 29.1 |
**1.052x** |
| trace_h12_b3_q1_kv261120 | row tiles | 89.7 | **1.043x** | 90.6 |
**1.026x** |
| trace_h12_b4_q1_kv268800 | row tiles | 112.8 | **1.096x** | 113.5 |
**1.058x** |
| trace_h12_b5_q1_kv276480 | row tiles | 138.4 | **1.075x** | 139.9 |
**1.070x** |
| trace_h12_b6_q1_kv467751 | row tiles | 254.3 | **1.073x** | 256.5 |
**1.067x** |
| trace_h12_b7_q1_kv299613 | row tiles | 195.5 | **1.068x** | 197.8 |
**1.066x** |
| trace_h12_b8_q1_kv342305 | row tiles | 246.8 | **1.078x** | 248.5 |
**1.073x** |
| trace_h12_b9_q1_kv348705 | row tiles | 279.2 | **1.075x** | 280.3 |
**1.070x** |
| trace_h12_b10_q1_kv474166 | row tiles | 412.8 | **1.088x** | 411.8 |
**1.075x** |
| trace_h12_b11_q1_kv474405 | row tiles | 453.3 | **1.076x** | 450.6 |
**1.069x** |
| mirror_h96_b1_q1_kv76800 | wide | 23.7 | **1.159x** | 23.1 |
**1.130x** |
| mirror_h96_b2_q1_kv77699 | wide | 33.3 | **1.022x** | 33.1 |
**1.021x** |
| mirror_h96_b6_q1_kv467751 | wide | 331.2 | **1.033x** | 320.4 |
**1.063x** |
| mirror_h96_b7_q1_kv299613 | wide | 247.3 | **1.043x** | 239.6 |
**1.049x** |
| mirror_h96_b8_q1_kv342305 | wide | 318.3 | **1.052x** | 309.5 |
**1.058x** |
| mtp_h12_b8_q2_kv342305 | row tiles | 256.7 | **1.227x** | 253.0 |
**1.220x** |
| mtp_h12_b8_q4_kv342305 | row tiles | 278.4 | **1.148x** | 263.6 |
**1.190x** |
| mtp_h12_b8_q8_kv342305 | wide | 321.2 | **1.047x** | 313.3 |
**1.049x** |
| mtp_h96_b8_q2_kv342305 | wide | 616.2 | **1.126x** | 607.5 |
**1.038x** |
| mtp_h96_b8_q4_kv342305 | wide | 946.2 | **1.046x** | 902.6 |
**1.027x** |
| mtp_h96_b8_q8_kv342305 | wide | 1782.4 | **1.223x** | 1776.7 |
**1.131x** |
| prefill_h12_b1_q2048_kv131072 | wide | 2531.1 | **1.070x** | 2534.7 |
**1.033x** |
| prefill_h12_b2_q512_kv32768 | wide | 327.5 | **1.200x** | 327.9 |
**1.135x** |
| prefill_h12_b4_q1024_kv8192 | wide | 331.6 | **1.091x** | 321.2 |
**1.120x** |
| prefill_h96_b1_q2048_kv131072 | wide | 20226.7 | **1.042x** | 20314.9
| **1.028x** |
| prefill_h96_b2_q512_kv32768 | wide | 2560.0 | **1.039x** | 2490.9 |
**1.051x** |

`vs best FI` = median over the 3 rounds of (fastest of `auto` /
`trtllm-gen` / `cute-dsl` divided by Cake) in that round (>1 = Cake
faster); `Cake us` = median of the 3 rounds; same session and GPU (B200
`nsc-svg-slurm-1-gpu-157`, 148 SMs, allocation 2076841, step `eb75a751`;
B300 `pool0-0048 (B300 SXM6 AC)`, 148 SMs, allocation 583080, step
`2ed26b9c`). `route` is the schedule the planner selects for the row.
**The route is faster than every existing FlashInfer backend on all 27
rows on both GPUs: the user's rule (every shape > 1 vs every baseline)
is met on B200 and on B300.** There are no misses. The closest rows are
mirror_h96_b2 (1.022x on B200, 1.021x on B300) and, on B300,
trace_h12_b3 (1.026x) and the previous round's miss mtp_h96_b8_q4
(1.027x `auto` / 1.029x `cute-dsl`; 1.046x on B200). Against the r51
head of this PR, the r52 tree is 0.969x time (gpu-157 vs the r51d gate
on the same node) (B200) / 0.987x time (pool0-0048 vs the r51d gate node
pool0-0275) (B300) of the r51d gate time over the 27 rows (geomean;
Against the r51d gate benches the H96 wide rows take 0.92-0.98x of their
previous time on B200 (mirror_h96_b8 0.919x, mtp_h96_b8_q2 0.930x,
mtp_h96_b8_q4 0.953x, prefill_h96_b2 0.964x) and 0.94-0.99x on B300
(mtp_h96_b8_q4 0.939x, prefill_h96_b2 0.955x, mtp_h96_b8_q8 0.957x,
mirror_h96_b8 0.975x); the H12 rows are unchanged within noise (same
kernels). The B200 comparison is same-node, different session; the
same-node paired A/B behind the design numbers is on B300 pool0-0143
(section r52).).

## Baselines and their source PRs

The `vs best FI` column compares against the two existing FlashInfer
routes of the same public entry points, resolved at this branch's
upstream merge-base `7b8f6129c` (2026-09-27, #5585):

- **trtllm-gen** (`backend="trtllm-gen"`, also what `backend="auto"`
selects for H12): `trtllm_batch_decode_with_kv_cache_mla` /
`trtllm_prefill_with_kv_cache_mla` in `flashinfer/mla/_core.py`
launching the prebuilt TRT-LLM-gen FMHA cubins pinned in
`flashinfer/artifacts.py` (`TRTLLM_GEN_FMHA =
2d6a5a02…/fmha/trtllm-gen/`; pin set by #4654 `857bc3a11`, 2026-08-26).
Test oracle: `tests/attention/test_trtllm_gen_mla.py`.
- **cute-dsl** (`backend="cute-dsl"`, what `auto` selects for H96): the
CuTe-DSL MLA decode family under `flashinfer/cute_dsl/attention/` —
`mla_decode_fp8.py`, `mla_config.py`, `wrappers/batch_mla.py` (#2805,
`00ac5053d`, 2026-04-13; H64/H96 configs #3235 `2d0e0efac` 2026-05-11;
SM107 reland #4280 `5b1af9724` 2026-07-30), `mla_dispatch.py` +
`monolithic/mla_decode.py` (#3296 `e91ac8f15` 2026-05-21; LSE base
semantics #4650 `d7a7447cb` 2026-09-21), reached through
`flashinfer/mla/_core.py` (cute-dsl MLA op #2743 `31b63bc3d`
2026-03-27). Test oracle: `tests/attention/test_trtllm_gen_mla.py` / the
CuTe-DSL MLA tests of those PRs.

Since the previous merge-base `bf82326b0` (the #5552 comparison) no
upstream commit touched the `cute-dsl` MLA kernels (`git log
bf82326b0..7b8f6129c -- flashinfer/cute_dsl/attention` is empty), the
`TRTLLM_GEN_FMHA` pin is unchanged (#5149 `e34a1735a` moved only the
`batched_gemm` artifact in `flashinfer/artifacts.py`), and
`flashinfer/mla/_core.py` changed only by the `backend="cake"` dispatch
additions of #5552, #5577 and #5588. The Cake route in this PR is
compared against exactly those implementations.

## Unsupported (rejected explicitly)

Unchanged from #5552: sparse top-k MLA, attention sinks, LSE output,
DCP, skip-softmax, FP16 softmax, PDL as a caller option (`enable_pdl`:
the attention kernel is an ordinary launch on the caller's stream;
internally the route launches its split-KV merge as a programmatic
dependent of the attention kernel), NVFP4 / uint8 caches,
`multi_ctas_kv_counter_buffer`. Requests with > 64 packed rows whose
longest KV is below 8192 tokens run the 96-row tiles (the wide kernel's
lazy-E4M3 reference needs atol 0.012 at KV 4096 against the 0.01 gate).

## Tests

- `tests/mla/test_cake_kimi_k3_mla.py` (30 cases: decode H12/H96 incl.
the long-KV wide-route set, MTP variable-Q (incl. the 60-row RT=64 case
and a wide-route H96 case), incremental prefill with prefix reuse and
the wide-route prefill at 0.01 / 0.02, route selection with the 8192
threshold, CUDA-graph replay with a changed page table on both routes,
unsupported-option rejection, nine host-only wide-split-planner cases
and the three tail-plan cases): **30 passed on B200, 30 passed on B300**
on the generated programs of this PR head. Upstream pre-commit hooks
(mypy, ruff check, ruff format) pass on the hand-written files (the only
hook output is the `ruff format` re-wrap already applied as
`43cb25a50`).
- `tests/attention/test_trtllm_gen_mla.py -k trtllm_mla_blackwell`
(dispatch regression for the #4557 route): 18 passed on B200; 12 passed,
6 skipped on B300.
- Export receipts (source-vs-generated host-plan + bitwise output parity
and ABBA CUPTI timing gates; denominator = 27 perf rows + the two
coverage rows, per arch): B200 27 / 29 rows pass (25 perf + 2 coverage
rows; source/export geomean 1.0010, perf rows 1.0012); B300 27 / 29 rows
pass (25 perf + 2 coverage rows; source/export geomean 1.0013, perf rows
1.0015). Two rows per GPU are refused, both by measurement-validity
gates rather than by parity or correctness:
`prefill_h96_b1_q2048_kv131072`, the exporter's loaded-SM-clock gate
(1312 / 1965 MHz on B200, 1185 / 2032 MHz on B300, below the 0.70
fraction under the sustained power cap; the same row and gate as r50 and
r51), and `mirror_h96_b1_q1_kv76800`, whose paired ABBA timing shows a
~1.3 % first-arm advantage on both GPUs (`directional_disagreement`
0.0263 / 0.0204 against a 0.02 limit; source and generated program are
the same kernel, bitwise parity holds, source/export 1.0026 / 1.0097). A
closed-prior retry round re-measured only these two rows and reproduced
both refusals (0.0253 / 0.0218), so they are disclosed rather than
re-rolled; the row's speed against the baselines is the gate bench's
1.159x / 1.130x. the B200 and B300 exporter runs generated
byte-identical program files (42 files under
`csrc/cake_kimi_k3_mla/{sm_100a,sm_103a}` + README + jit registry,
per-file SHA-256 equal; the two tarballs differ only in archive
metadata).

<details><summary>Export receipts (29 rows per architecture, source vs
generated: same-session ABBA CUPTI cold-L2 medians, CUDA-graph
replay)</summary>

| row | route | sm_100a source us | sm_100a export us | sm_100a src/exp
| sm_100a verdict | sm_103a source us | sm_103a export us | sm_103a
src/exp | sm_103a verdict |
|---|---|---:|---:|---:|---|---:|---:|---:|---|
| mtp_h12_fixed_q5 | rt64_reduce_w2_sm_100a | 300.6 | 300.5 | 1.0001 |
PASS | 268.5 | 268.5 | 1.0001 | PASS |
| mtp_h96_fixed_q8_kv8000 | rt96_reduce_w1_sm_100a | 139.6 | 139.8 |
0.9982 | PASS | 125.3 | 125.7 | 0.9967 | PASS |
| trace_h12_b1_q1_kv76800 | rt16_reduce_cta_sm_100a | 21.5 | 21.2 |
1.0151 | PASS | 21.2 | 20.9 | 1.0138 | PASS |
| trace_h12_b2_q1_kv77699 | rt16_reduce_cta_sm_100a | 29.3 | 29.4 |
0.9967 | PASS | 28.9 | 29.1 | 0.9945 | PASS |
| trace_h12_b3_q1_kv261120 | rt16_reduce_cta_sm_100a | 89.6 | 89.7 |
0.9986 | PASS | 90.2 | 90.5 | 0.9968 | PASS |
| trace_h12_b4_q1_kv268800 | rt16_reduce_cta_sm_100a | 112.8 | 112.7 |
1.0009 | PASS | 114.0 | 113.9 | 1.0011 | PASS |
| trace_h12_b5_q1_kv276480 | rt16_reduce_w4_sm_100a | 138.9 | 139.2 |
0.9975 | PASS | 139.8 | 140.2 | 0.9973 | PASS |
| trace_h12_b6_q1_kv467751 | rt16_reduce_w4_sm_100a | 253.5 | 253.7 |
0.9994 | PASS | 253.6 | 253.7 | 0.9995 | PASS |
| trace_h12_b7_q1_kv299613 | rt16_reduce_w4_sm_100a | 196.1 | 195.8 |
1.0011 | PASS | 197.3 | 197.3 | 1.0002 | PASS |
| trace_h12_b8_q1_kv342305 | rt16_reduce_w4_sm_100a | 249.0 | 249.0 |
0.9999 | PASS | 248.5 | 248.5 | 1.0001 | PASS |
| trace_h12_b9_q1_kv348705 | rt16_reduce_w4_sm_100a | 280.9 | 281.2 |
0.9986 | PASS | 279.7 | 280.0 | 0.9990 | PASS |
| trace_h12_b10_q1_kv474166 | rt16_reduce_w4_sm_100a | 421.9 | 422.2 |
0.9991 | PASS | 412.5 | 412.8 | 0.9994 | PASS |
| trace_h12_b11_q1_kv474405 | rt16_reduce_w4_sm_100a | 463.8 | 463.9 |
0.9997 | PASS | 448.5 | 448.5 | 0.9999 | PASS |
| mirror_h96_b1_q1_kv76800 | wide_reduce_cta_sm_100a | — | — | — | FAIL:
failed gates: directional_disagreement | — | — | — | FAIL: failed gates:
directional_disagreement |
| mirror_h96_b2_q1_kv77699 | wide_reduce_cta_sm_100a | 33.3 | 32.9 |
1.0126 | PASS | 33.6 | 32.9 | 1.0194 | PASS |
| mirror_h96_b6_q1_kv467751 | wide_reduce_w2_sm_100a | 341.9 | 341.4 |
1.0015 | PASS | 328.5 | 327.9 | 1.0017 | PASS |
| mirror_h96_b7_q1_kv299613 | wide_reduce_w2_sm_100a | 257.9 | 257.6 |
1.0014 | PASS | 242.0 | 241.7 | 1.0012 | PASS |
| mirror_h96_b8_q1_kv342305 | wide_reduce_w2_sm_100a | 334.0 | 333.6 |
1.0011 | PASS | 320.7 | 320.3 | 1.0014 | PASS |
| mtp_h12_b8_q2_kv342305 | rt32_reduce_w4_sm_100a | 261.4 | 261.7 |
0.9987 | PASS | 253.4 | 253.7 | 0.9990 | PASS |
| mtp_h12_b8_q4_kv342305 | rt48_reduce_w2_sm_100a | 287.6 | 287.8 |
0.9993 | PASS | 263.9 | 264.1 | 0.9995 | PASS |
| mtp_h12_b8_q8_kv342305 | wide_reduce_w2_sm_100a | 334.0 | 333.7 |
1.0009 | PASS | 320.5 | 320.0 | 1.0014 | PASS |
| mtp_h96_b8_q2_kv342305 | wide_reduce_w1_sm_100a | 641.3 | 640.7 |
1.0009 | PASS | 619.6 | 619.1 | 1.0008 | PASS |
| mtp_h96_b8_q4_kv342305 | wide_reduce_w1_sm_100a | 954.5 | 953.5 |
1.0010 | PASS | 923.8 | 923.2 | 1.0006 | PASS |
| mtp_h96_b8_q8_kv342305 | wide_reduce_w1_sm_100a | 1838.8 | 1838.3 |
1.0003 | PASS | 1802.6 | 1802.2 | 1.0002 | PASS |
| prefill_h12_b1_q2048_kv131072 | wide_reduce_w1_sm_100a | 2576.4 |
2576.0 | 1.0001 | PASS | 2526.6 | 2525.9 | 1.0003 | PASS |
| prefill_h12_b2_q512_kv32768 | wide_reduce_w1_sm_100a | 332.6 | 332.0 |
1.0017 | PASS | 327.7 | 327.3 | 1.0014 | PASS |
| prefill_h12_b4_q1024_kv8192 | wide_reduce_w1_sm_100a | 335.8 | 335.1 |
1.0021 | PASS | 316.4 | 315.8 | 1.0020 | PASS |
| prefill_h96_b1_q2048_kv131072 | wide_reduce_w1_sm_100a | — | — | — |
FAIL: InterleavedTimingError: reportable loaded SM clock 1297/1965 MHz
is below the 0.700000 fraction | — | — | — | FAIL:
InterleavedTimingError: reportable loaded SM clock 1177/2032 MHz is
below the 0.700000 fraction |
| prefill_h96_b2_q512_kv32768 | wide_reduce_w1_sm_100a | 2570.3 | 2569.7
| 1.0003 | PASS | 2529.9 | 2529.2 | 1.0003 | PASS |

</details>

## Baselines-free numerics evidence carried over from the kernel rounds

Every route was measured against the FP32 reference: the routed kernel
passes all functional rows at 0.01 / 0.02 on both GPUs (forced-wide,
routed and forced-tail plans, 8 rows each); the 20 unchecked perf rows
pass on both (20 / 20 (max_abs 0.00586, prefill_h96_b1; 0 mismatches)
B200, 20 / 20 (max_abs 0.00586, prefill_h96_b1; 0 mismatches) B300). The
deferred rescale gives bitwise the same numerics as r51; the wider
threshold raises max_abs on the long rows as stated above and leaves the
short rows unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated paged-attention planning for long sequences, including more
selective splitting of final partial waves.
* Optimized attention output reduction and row scheduling to better
handle full and partial work tiles.

* **Reliability**
* Improved synchronization across attention tiles to ensure completion
is observed consistently during processing.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [22d2d07](https://github.com/flashinfer-ai/flashinfer/commit/22d2d0798667f55c97d48b53718f0bfe08b07f59)

- **作者**: eigen
- **时间**: 2026-09-27T23:23:16Z
- **提交信息**: feat(cake_alpha_moe): add Blackwell AlphaMoE NVFP4 expert up/down compute (#4340)

## 📌 Description

Add SM100a/SM103a **AlphaMoE NVFP4** expert compute (fused gate/up
projection + SwiGLU + intermediate requantization, down projection,
route alignment and BF16 finalize) as a routed-MoE operator that
consumes the same prequantized activations, NVFP4 weights with E4M3
block scales and supplied route ids/weights as
`trtllm_fp4_block_scale_routed_moe`, and produces the same BF16 output.

This head supersedes the earlier head of this PR (`c691f3b5`), whose six
measured shapes were all below 1x (0.08x to 0.31x). The kernels were
re-derived shape by shape; the current package selects one of 17
host-side routes from `(M, N, K, block_m, prepared-weight inputs)`:

- **Decode (M = 1 / 8 .. 16)**: one-token GEMV chain with bitmask-rank
alignment fused into the up kernel, persistent split-K down, deferred
finalize with a caller-supplied BF16 seed.
- **Batched (M = 128 / 512)**: BM16/BM8 whole-owner up kernels with L2
`evict_last` W1 streaming, and down kernels that stream **prepared W2
panels** with `evict_first` so the row buffers of the following finalize
stay L2-resident.
- **Large batches (M > 512)**: a grouped-GEMM shaped token-tile route:
cooperative 128-row per-expert tile alignment, tile-ordered activation
scale-factor panels, a persistent 128-token-tile up GEMM over the
prepared W1 panels, a dynamic-scheduled down GEMM over **K-256 W2
panels** and a pair-to-row BF16 finalize. Each expert's W1/W2 is
streamed once per 128-token tile instead of once per 8 rows.
- **General path** for every other shape (BM8 whole-owner up/down,
alignment, row-buffer finalize).

Every route is bitwise identical to the general path on its shape; the
GLM-geometry shapes are bitwise identical to the Stock operator.

**This head (`19056357`) fixes the CUDA 12.9 build** that failed the
cu129 CI job on the previous head (`24a4f9db`, tests
`test_alphamoe_nvfp4_token_tile_route_matches_general[m1000|m4096]`). In
the two BM8 down kernels that own 32 / 16 / 8 live sub-tiles per stage,
the second-K-half `tcgen05.mma` was issued from three sibling branches
(one per N variant); ptxas 12.9 sank the branches' shared shared-memory
descriptor computation into the N=32 branch, so the N=16 / N=8 branches
read an uninitialised descriptor (compute-sanitizer: out-of-range shared
address in the MMA warp). CUDA 13.x keeps the descriptor in uniform
registers per branch, which is why only the cu129 job failed. The fix
regenerates those two kernels with a single MMA issue site per stage
whose instruction descriptor carries the live N at run time
(`nvfp4_s14_c302n_down`, `nvfp4_s14_c358n_down`; same shared-memory
layout, thread count and instruction shapes). csrc only: the Python API,
routes and tests are unchanged.

### Public API

```python
from flashinfer.fused_moe import (
    alphamoe_nvfp4_routed_moe, alphamoe_nvfp4_routed_moe_deferred, alphamoe_nvfp4_aligned_moe,
    prepare_nvfp4_w1_scales, prepare_nvfp4_w2_scales, prepare_nvfp4_w1_data,
    prepare_nvfp4_w1_gate_up_data, prepare_nvfp4_w1_gate_up_scales, prepare_nvfp4_w2_data,
    prepare_nvfp4_w2_data_k256, prepare_nvfp4_w2_scales_k256,
)
```

The `prepare_*` helpers are one-time model-load layout permutations
(exact byte permutations, no arithmetic). `prepare_nvfp4_w2_data(w2)`
turns the contiguous uint8 W2 `[E, K, N/4]` into `[E*(K/128)*(N/256),
128, 64]` panels so each expert / 128-row output tile / 128-wide
intermediate block is one contiguous 8 KB TMA box. The M = 128 and M =
512 fast routes require both `w1_data_prepared` and `w2_data_prepared`;
without them the selector keeps the general routes. All optional inputs
default to `None`, so existing callers are unaffected.

`prepare_nvfp4_w2_data_k256(w2)` /
`prepare_nvfp4_w2_scales_k256(w2_scale)` (new in this head) build
128-byte-row, 256-K-element W2 panels and the matching block-scale
panels for the large-batch route; `alphamoe_nvfp4_routed_moe` selects
that route only when the caller passes both (plus `w1_data_prepared`),
otherwise batches above 512 tokens keep the general path.

### GPU performance (NVIDIA GB300, sm_103a)

Boundary: complete routed operator, prequantized activations + route
ids/weights in, BF16 out, for both arms. Stock =
`trtllm_fp4_block_scale_routed_moe` (permutation, both GEMMs,
intermediate quantization and finalization; autotuned once, untimed).
Candidate = route alignment + the AlphaMoE kernels + finalize. Metric =
sum of correlated GPU kernel durations from strict CUPTI activity
tracing with a cold L2 before every sample, 5 paired rounds x 30
samples, medians of the paired ratios. Speedup = Stock / candidate.

| Shape | Route | Stock GPU sum (us) | AlphaMoE GPU sum (us) | Speedup
(Stock / AlphaMoE) | max abs diff vs Stock |
|---|---:|---:|---:|---:|---:|
| M=8, H=7168, I=128, E=256, top-k=8, BM=8 | 0 | 42.66 | 38.50 |
**1.1090x** | 1 |
| M=128, H=7168, I=128, E=256, top-k=8, BM=16 | 0 (aligned entry; BM16
has no routed companion) | 116.00 | 101.70 | **1.1411x** | 2 |
| M=1, H=6144, I=512, E=256, top-k=8, BM=8 | 1 | 25.60 | 19.42 |
**1.3185x** | 0 |
| M=8, H=6144, I=512, E=256, top-k=8, BM=8 | 9 | 74.59 | 71.33 |
**1.0453x** | 0 |
| M=128, H=6144, I=512, E=256, top-k=8, BM=8 | 10 | 224.00 | 216.13 |
**1.0364x** | 0 |
| M=512, H=6144, I=512, E=256, top-k=8, BM=8 | 12 | 241.95 | 240.42 |
**1.0064x** | 0 |

GPU: NVIDIA GB300; 5 paired rounds; 6/6 rows above 1x (re-measured on
this head; the M = 512 route now runs the regenerated `c358n` down
kernel, the other five routes' kernels are unchanged from the previous
head).

The GLM M = 512 row is the tightest margin (1.5 us); its per-round
ratios were 1.0059, 1.0068, 1.0059, 1.0064, 1.0064.

Deterministic fixtures with unit expert global scales; seeds 28104/28105
(H=7168 rows) and 28110..28113 (GLM rows). Measured on the exact commit
of this PR head with the current `main` merged in.

**Large batches (same metric, PDL-enabled Stock, 5 paired rounds;
re-measured on this head):**

| Shape | Route | Stock GPU sum (us) | AlphaMoE GPU sum (us) | Speedup
(Stock / AlphaMoE) | max abs diff vs Stock |
|---|---:|---:|---:|---:|---:|
| M=1000, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 265.15 | 260.58 |
**1.0176x** | 0 |
| M=2048, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 299.71 | 291.14 |
**1.0296x** | 0 |
| M=4096, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 391.65 | 382.96 |
**1.0229x** | 0 |
| M=8192, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 606.87 | 580.74 |
**1.0449x** | 0 |

Outputs are bitwise equal to Stock at all four token counts. The
previous head ran these shapes on the general path at 0.80x / 0.65x /
0.53x / 0.46x. Both arms now stream the weights at the HBM ceiling; the
remaining margins come from alignment, finalize and L2 policy.

### Real-model evidence (GLM-5.2-NVFP4, TP4, GB300, SGLang
`flashinfer_alphamoe` MoE backend vs `flashinfer_trtllm`)

Measured on the previous head of this PR (`24a4f9db`, 2026-09-27); the
numbers in parentheses are from the head before that (`d62684bc`). This
head changes only the two down kernels named above; the GLM-geometry
shapes stay bitwise equal to Stock (six-shape table above) and the
package tests that compare the routes still pass, so the real-model
evidence carries over. Batches above 512 tokens (decode batches of ~1000
tokens, prefill chunks of 6k..16k tokens) take the new large-batch route
once the serving integration passes the two prepared W2 sidecars to the
routed call; the first re-run on this head still ran the general path
there because the integration's quant-info object did not carry the
sidecars (an integration-side fix, not part of this PR's library or
API), and reproduced the previous numbers; the re-run below has the
large-batch route live.

- GSM8K 1314-question accuracy: **1257 / 1314 correct vs Stock 1264**
(threshold 1258): below the threshold by 1 (previous head 1260; the
first re-run on this head scored 1260). Stock has 27
thinking-budget-exhausted answers, this run 33; 13 of the 17 questions
lost against Stock are such empties, and the two re-runs lose and win
different question sets. The large-batch route's outputs are bitwise
equal to Stock at every prefill shape this workload used, and earlier
revisions scored 1253 / 1257 / 1259 / 1260 with kernels identical on
every route it exercises, so the protocol's run-to-run spread is at
least +-4 and the result is not attributable to kernel numerics. Not
re-run to fish for a pass.
- Paired clean serving throughput at concurrency 1 / 8 / 16 (5 seeds
each, same node class, same seeds both arms, 8192-token prompts / 512
output tokens): **0.973x / 0.962x / 0.977x of Stock, 0 wins out of 15**
(previous head 0.967x / 0.914x / 0.906x, 0 of 15).
- Instrumented layer capture at M = 2 / M = 4 (TP4 layer 3): PASS,
bitwise against the reference replay.

The serving integration loads the prepared W1 / W2 layouts once at model
load through a small weight-carrier helper; the kernels and library are
the ones validated below.

### Validation on this head

- Native gate: PASS (20 package tests; SASS compared kernel by kernel
against the previous head's validated library: 97 kernels bit-identical,
1 register-renaming-only difference, the 2 regenerated down kernels
added and their predecessors removed)
- compute-sanitizer memcheck / synccheck / racecheck on the
prepared-weight routes (M = 128 / 512) and the large-batch route (M =
1000 / 4096; seeded == direct == general-path bitwise): 0 errors / 0
errors / 0 hazards
- CUDA 12.9 build (the failing CI configuration): the package built and
passed all 20 tests in the FlashInfer CI image (cuda_12.9, torch
2.13.0+cu129); compute-sanitizer memcheck on the two previously failing
cases reports 0 errors
- Pre-commit hooks (ruff check + format, mypy, clang-format with the
AlphaMoE csrc units excluded): clean

### Baselines and their source PRs

| baseline | origin | files | used for |
|---|---|---|---|
| `trtllm_fp4_block_scale_routed_moe` (trtllm-gen NVFP4 fused MoE,
artifacts `4e73ccb7.../batched_gemm-b738138-6923fec`) |
flashinfer-ai/flashinfer `main` @ `e34a1735` (2026-09-25, PR #5149
bumped the BMM artifact set) | `flashinfer/fused_moe/core.py`,
`csrc/trtllm_fused_moe_runner.cu`,
`csrc/trtllm_fused_moe_kernel_launcher.cu`,
`csrc/trtllm_fused_moe_routing_binding.cu` | GPU six-shape and
large-batch rows above (Stock arm) |
| SGLang `flashinfer_trtllm` MoE runner backend | sglang `5407ec1a`
(unchanged from the earlier head of this PR) |
`python/sglang/srt/layers/moe/...` | real-model accuracy / serving Stock
arm |

## 🔍 Related Issues

Supersedes the measurements posted earlier in this PR.

## 🚀 Pull Request Checklist

- [x] I have read the [contributing
guidelines](https://github.com/flashinfer-ai/flashinfer/blob/main/CONTRIBUTING.md)
- [x] Pre-commit hooks pass on the changed files
- [x] Tests added: `tests/moe/test_alphamoe_nvfp4_sm100.py` (20 cases:
routed / aligned / deferred paths, prepared-weight layouts, W1/W2 panel
permutations, large-batch route vs general path at 1000 / 4096 tokens)
- [x] Documentation: `docs/api/fused_moe.rst`,
`examples/pytorch/alphamoe_nvfp4_aligned_moe.py`

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [166aabc](https://github.com/flashinfer-ai/flashinfer/commit/166aabc7c8638b762a35fb62e30dc91602d99bf5)

- **作者**: eigen
- **时间**: 2026-09-27T23:03:26Z
- **提交信息**: perf(cake_fp8_projection): Kimi-K3 KDA/MLA projection GEMM (per-token FP8 activations x per-block FP8 weights, SM100/SM103) round 3: narrow quantization units and a decoupled BF16 token ring in the fused-quant decode kernel (#5604)

## Summary

Round 3 of the experimental generated-program backend for the serialized
`FP8_PB_WO` KDA / MLA projection GEMMs of `nvidia/Kimi-K3-NVFP4` on
`sm_100a` (B200) and `sm_103a` (B300/GB300),
`flashinfer/experimental/kimi_k3_fp8_projection` (round 1: #5572, round
2: #5590; this PR is stacked on the round-2 branch and contains its
commits until #5590 merges).

- **Narrow quantization units in the fused decode programs**: the in-CTA
per-token 1x128 quantization of the BF16 activations is done by 4-lane
(or 8-lane) units per (token, 128-K block) instead of half-warp units,
which removes most of the per-unit overhead that sat on the pipeline's
critical path. Quantized operands and outputs are unchanged (bit-exact
against the exact quantized-operand emulation and against the unfused
route).
- **Decoupled BF16 token ring**: a dedicated TMA warp streams the token
tiles through their own SMEM ring (`xb_full` / `xb_empty`), so the
activation fetch latency no longer sits inside the weight-stage slot.
- **Dispatch table**: the N = 128 buckets `256` / `4096` / `16384`
select the new instances on both architectures
(`decode:t16_p4_fused_q8`, `decode:t32_p3_fused_r5_q4`,
`decode:t64_p2_fused_r3_q4`); every other bucket is unchanged.
- Host: `cake_backend.py` (`decode_config` ring split and unit-width
rule, `decode_module_stages`, `DecodeConfig.xb_stages` / `qlanes`),
`cake_jit.py` (`decode_kernel_key` `_r<xb>` / `_q<lanes>` suffixes,
regenerated registries), `decode_table.py` (three entries per
architecture), `csrc/cake_kimi_k3_fp8_projection/{sm_100a,sm_103a}/*`
(regenerated programs), tests for the new rules.

Same-GPU paired A/B of the new instances against the round-2 programs (3
alternating rounds, CUDA-graph replay, CUPTI, cold L2): `f_a M=4096`
**1.342x** (B200) / **1.291x** (B300), `f_a M=16384` **1.426x** /
**1.421x**, the 256-row `f_a` / `b_proj` rows 1.02-1.05x, the M <= 8
fused rows unchanged within +-2 %.

## Evidence (export protocol, producer `2488c8be3ed`, target
`334099c70`)

Every contract row (22 families x `M in {1, 8, 64, 256, 4096, 16384}` =
132 perf rows, plus 88 correctness-only rows with `M in {3, 129, 1000,
4097}` and padded output strides) is measured on the source launcher and
on the exported programs in counterbalanced pairs (CUDA-graph replay,
CUPTI, cold L2) and sealed only when bitwise identical and inside the
timing gates.

| arch | GPU | rows measured | correct (bitwise source == export) |
sealed (all timing gates) | source / export (min .. max, geomean) |
|---|---|---|---|---|---|
| sm_100a | B200 | 220 | 220 | 218 | 0.9552 .. 1.0504, 0.9995 |
| sm_103a | B300 | 220 | 220 | 220 | 0.9504 .. 1.0445, 0.9960 |

Rounds, all disclosed: B300 sealed every row in the first round. B200
sealed 216 rows in the first round; a retry round (the first round
closed as a read-only prior, only the four failed rows re-measured)
sealed `tp1 f_b M=64` (1.017x) and `tp8 in_proj_qkvgfab M=16384`
(0.9986x); the two `kv_a M=64` rows fail the arm-order disagreement gate
again (source / export 0.984x / 0.974x, same generated kernel,
bitwise-identical output) — the same pair-order effect of the shortest
persistent decode call disclosed in #5590. Delivery is byte-identical
from both GPUs (`delivery.patch` SHA-256
`6c787e53d885a0675d57cfe732dc18ffda5995541e76bbbe326303aaeb2b27a5`).

Exported programs vs the fastest existing FP8 chain per row, same
process, CUDA-graph replay, CUPTI, cold L2
(`benchmarks/bench_cake_kimi_k3_fp8_projection.py --cupti`; chains:
`per_token_group_quant_8bit` + `gemm_fp8_nt_groupwise` with `cutlass`
mma_sm 1 / 2, `trtllm`, `cutile`; every chain available on every row):

| GPU | rows faster than the best chain | min | geomean (#5590) | max |
`f_a M=4096` / `M=16384` | best chain census |
|---|---|---|---|---|---|---|
| B200 | **132 / 132** | 1.041x (`tp1 fused_qkvg M=1`) | 1.888x (1.839x)
| 8.490x | 6.76x / 8.49x | trtllm 60, cutile 40, cutlass sm2 26, cutlass
sm1 6 |
| B300 | **132 / 132** | 1.049x (`tp1 in_proj_qkvgfab M=8`) | 1.872x
(1.836x) | 8.481x | 6.72x / 8.45x | trtllm 60, cutile 41, cutlass sm2
20, cutlass sm1 11 |

`tests/experimental/test_cake_kimi_k3_fp8_projection.py`: 35 passed on
B200 and on B300 against this tree (two new tests cover the ring /
narrow-unit dispatch rules).

## Baselines and their source PRs

The comparison arms are upstream FlashInfer entry points at
`9b727df8af4858db231f7f3a436a8a87fe54e563` (this branch's upstream
merge-base). No upstream kernel is modified.

- `per_token_group_quant_8bit`
(`flashinfer/quantization/fp8_quantization.py`, cuTile kernel
`flashinfer/quantization/kernels/cutile/per_token_group_quant_8bit_cutile.py`):
#4019 (`c517c07bd`, 2026-08-13).
- `gemm_fp8_nt_groupwise` `backend="cutlass"` (`mma_sm` 1 and 2;
`csrc/gemm_groupwise_sm100.cu`,
`csrc/gemm_groupwise_sm100_kernel_inst.jinja`,
`flashinfer/gemm/gemm_base.py`): #1045 (`71002782f`, 2025-05-04).
- `gemm_fp8_nt_groupwise` `backend="trtllm"`
(`csrc/trtllm_gemm_runner.cu`): #1320 (`67e77fd5a`, 2025-07-28); last
change #4280 (`5b1af9724`, 2026-07-30).
- `gemm_fp8_nt_groupwise` `backend="cutile"`
(`flashinfer/gemm/kernels/cutile/gemm_fp8_nt_groupwise_cutile.py`):
#3426 (`992848ad3`, 2026-06-12); last change #4459 (`d70a043f5`,
2026-09-12).
- DeepGEMM `fp8_gemm_nt` with `per_token_group_quant_8bit(...,
scale_ue8m0=True)` packing: deepseek-ai/DeepGEMM
`78b69000794d0937b47ae3387eff7663410264d1` (external).
- Round-1 (#5572) and round-2 (#5590) programs of this backend are the
previous states of the same entry points; the speedups above are against
the existing FP8 chains, not against the earlier rounds, except where a
same-GPU A/B against the round-2 programs is stated explicitly.
- BF16 cuBLAS (`torch.matmul` on the dequantized weight) is reported as
an informational reference only.

Test oracle: the exact quantized-operand emulation in
`tests/experimental/test_cake_kimi_k3_fp8_projection.py`.

## Test

```
pytest tests/experimental/test_cake_kimi_k3_fp8_projection.py
python benchmarks/bench_cake_kimi_k3_fp8_projection.py --cupti
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expanded Kimi K3 FP8 projection support for additional NVIDIA GPU
architectures.
* Improved fused decode flexibility with independently configurable
token buffering and quantization widths, including automatic pipeline
tuning for selected routes.
* **Performance**
* Updated projection processing to use dedicated token loading and
quantization pipelines, with revised resource allocation for selected
configurations.
* **Tests**
* Added coverage for decode pipeline settings and their corresponding
kernel selections.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8d75938](https://github.com/flashinfer-ai/flashinfer/commit/8d75938865ac4dd2bf28271a7ef378ceffc38b95)

- **作者**: eigen
- **时间**: 2026-09-27T22:50:56Z
- **提交信息**: feat(cake_comm): extend the MoE all-reduce fusion union export to world sizes 2, 4 and 8 on SM100 and SM103 (#5599)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extend the Cake-generated **TRT-LLM MoE all-reduce fusion union**
(#5514) from SM100 world size 4 to **world sizes 2, 4 and 8
on SM100 (B200) and SM103 (B300)**. `trtllm_moe_allreduce_fusion(...,
backend="cake")` now routes every SM100 or SM103 call
with an `moe_allreduce_out` tensor and `world_size in (2, 4, 8)` to the
verified union export of that architecture; calls
without the all-reduce output (and every other architecture) keep the
isolated source bundle from #4730 unchanged. The
change is additive for the public API.

### Speedup vs baselines (CUPTI paired timing, maximum per-rank median)

| SM100 (8xB200): world size | Rows correct | Speedup vs upstream
`trtllm_moe_allreduce_fusion(backend="trtllm")`: geomean | min | max |
rows >= 1.0x | Speedup vs shipped standalone cake programs
(`cake_trtllm_moe_allreduce_fusion` generic / `sm100_ws8_mid`): geomean
| min | rows >= 1.0x | Source / export timing parity: geomean |
|---|---|---:|---:|---:|---|---:|---:|---|---:|
| 2 | 10/10 | **1.2572x** | 1.0881x | 1.3375x | 10/10 | **1.0757x** |
1.0000x | 10/10 | 0.9950x |
| 4 (units byte-identical to the shipped ws4 export; re-measured) |
10/10 | **1.1313x** | 0.9789x | 1.5968x | 9/10 | **0.9595x** | 0.7966x |
1/10 | 1.0034x |
| 8 | 10/10 | **1.1105x** | 1.0409x | 1.1439x | 10/10 | **1.0107x** |
0.9999x | 9/10 | 0.9837x |
| all 30 rows | 30/30 | **1.1646x** | | | | **1.0142x** | | | 0.9940x |

| SM103 (8xB300): world size | Rows correct | Speedup vs upstream
`trtllm_moe_allreduce_fusion(backend="trtllm")`: geomean | min | max |
rows >= 1.0x | Speedup vs shipped standalone SM103 cake programs
(`cake_trtllm_moe_allreduce_fusion` generic / `sm103_t1`): geomean | min
| rows >= 1.0x | Source / export timing parity: geomean |
|---|---|---:|---:|---:|---|---:|---:|---|---:|
| 2 | 10/10 | **1.2337x** | 1.0549x | 1.3152x | 10/10 | **1.0092x** |
0.9972x | 8/10 | 1.0010x |
| 4 | 10/10 | **1.2301x** | 1.0361x | 2.0212x | 10/10 | **1.0616x** |
0.9983x | 9/10 | 1.0009x |
| 8 | 10/10 | **1.1019x** | 1.0351x | 1.1307x | 10/10 | **1.0130x** |
0.9965x | 7/10 | 1.0011x |
| all 30 rows | 30/30 | **1.1869x** | | | | **1.0277x** | | | 1.0010x |

Speedup = baseline time / union-export time, both arms measured in the
same process with CUPTI activity tracing, interleaved in three
counterbalanced groups, maximum per-rank median per sample; per-row
values are in the per-architecture tables below. The SM100 ws4 rows
below 1.0x vs the shipped standalone programs (and
`ws4_bf16_t1_e8_nopdl` at 0.9789x vs upstream) are the pre-existing ws4
profile of the merged export; those units are byte-identical to it and
are only re-measured under the shared protocol. On SM103 six rows
measure 0.1-0.35 % below the shipped standalone SM103 programs
(0.9965x-0.9990x: `sm103_ws2_fp16_t2048_e8_nopdl`,
`sm103_ws2_fp16_t2048_e16_pdl`, `sm103_ws4_fp16_t2048_e8_nopdl`,
`sm103_ws8_fp16_t64_e12_nopdl`, `sm103_ws8_fp16_t2048_e8_nopdl`,
`sm103_ws8_fp16_t2048_e16_pdl`); these union programs are the same
physical schedule as the standalone ones (the union adds the
`moe_allreduce_out` store), the differences are inside the per-group
noise of the protocol, and every one of them is 1.03x-1.36x faster than
upstream.

### What is exported

* `csrc/cake_trtllm_moe_allreduce_union/sm_100a/*_{kernel,binding}.cu`
(unchanged by the SM103 commit): the physical builds
selected for the ten ratified shapes at each world size on SM100,
de-duplicated to 100 modules: 8 (ws2) + 28 (ws4) + 64
(ws8). Reviewed shape specializations: the three ws4 specializations
from #5514 plus `sm100_ws8_mid` at world size 8 for
  T in {64, 128} (measured against the generic schedule).
* `csrc/cake_trtllm_moe_allreduce_union/sm_103a/*_{kernel,binding}.cu`:
the physical builds selected for the same ten shapes
at each world size on SM103 (modules 78 routes 17 reviewed 5 by ws {2:
5, 4: 7, 8: 5}). Reviewed specializations on SM103: the
`sm103_t1` schedule variant at T=1 on every world size (composing with
the ws4 serial clear), the ws4 resident /
owner-forwarding shapes; On B300 the eight-rank mid schedule
(`sm103_ws8_mid`, the `sm100_ws8_mid` publication schedule compiled for
`sm_103a`) is not faster than `generic` on any of the four T64/T128 rows
(generic / mid 0.9984–1.0022), so the production rule keeps `generic`
for SM103 eight ranks; `sm103_ws8_mid` stays a probe-only variant.
* `flashinfer/jit/cake_trtllm_moe_allreduce_union.py`: manifest-verified
module inventory (per-file SHA-256, module `arch`),
route table keyed by `(arch, world_size, dtype, launch_with_pdl,
specialization)`, `ARCH_BY_CAPABILITY` =
{(10, 0): "sm_100a", (10, 3): "sm_103a"} with the exact per-architecture
nvcc flags, `route_applies` owning exactly the
exported (architecture, world size) scopes,
`route_module_names(arch=..., world_size=...)`, and
`run_cake_moe_allreduce_union` binding `3 * world_size + 1`
pointer-table entries (control + per-rank payloads).
* `flashinfer/comm/trtllm_ar.py`: the route scope names SM100 and SM103;
the `moe_allreduce_out is None` check still
  precedes the capability probe.
* `tests/comm/test_cake_moe_allreduce_union.py`: CPU inventory, route
and dispatch tests for both architectures and all
three world sizes; the existing
`tests/comm/test_cake_moe_allreduce_distributed.py` `tp2`/`tp4`/`tp8`
cases exercise the
  union route on both architectures.

### Binding contract

Unchanged from #5514: the kernel derives every device address from the
workspace pointer table in-kernel; the typed
`workspace_control` / `workspace_payload_<rank>` parameters are bound as
raw `int64_t` device addresses registered per
workspace tensor at creation time. The launchers keep the current-device
guard the merged ws4 launchers carry.

### World-size-8 schedule variant

SM100 (8xB200, generic vs `sm100_ws8_mid`):

| Row | generic us | `sm100_ws8_mid` us | generic / mid | Rule |
Decision |
|---|---:|---:|---:|---|---|
| ws8 bfloat16 T128 E16 nopdl | 62.51 | 63.23 | 0.9886 | `sm100_ws8_mid`
| generic faster by 0.0115 |
| ws8 bfloat16 T64 E8 pdl | 63.66 | 63.86 | 0.9970 | `sm100_ws8_mid` |
within noise band 0.010; production rule kept |
| ws8 float16 T128 E16 pdl | 77.00 | 67.95 | 1.1331 | `sm100_ws8_mid` |
sm100_ws8_mid faster by 0.1175 |
| ws8 float16 T64 E12 nopdl | 44.71 | 44.82 | 0.9977 | `sm100_ws8_mid` |
within noise band 0.010; production rule kept |

3 interleaved A B B A groups, 200 ms per arm and group, CUPTI, maximum
per-rank median, noise band 1%; correctness of both arms vs the contract
reference at atol = rtol = 1e-2 on every rank.

SM103 (8xB300, generic vs `sm103_ws8_mid`): On B300 the eight-rank mid
schedule (`sm103_ws8_mid`, the `sm100_ws8_mid` publication schedule
compiled for `sm_103a`) is not faster than `generic` on any of the four
T64/T128 rows (generic / mid 0.9984–1.0022), so the production rule
keeps `generic` for SM103 eight ranks; `sm103_ws8_mid` stays a
probe-only variant.

| Row | generic us | `sm103_ws8_mid` us | generic / mid | Rule |
Decision |
|---|---:|---:|---:|---|---|
| ws8 bfloat16 T128 E16 nopdl | 48.26 | 48.34 | 0.9984 | `generic` |
within noise band 0.010; production rule kept |
| ws8 bfloat16 T64 E8 pdl | 28.29 | 28.27 | 1.0006 | `generic` | within
noise band 0.010; production rule kept |
| ws8 float16 T128 E16 pdl | 47.74 | 47.81 | 0.9987 | `generic` | within
noise band 0.010; production rule kept |
| ws8 float16 T64 E12 nopdl | 28.82 | 28.75 | 1.0022 | `generic` |
within noise band 0.010; production rule kept |

3 interleaved A B B A groups, 200 ms per arm and group, CUPTI, maximum
per-rank median, noise band 1%; correctness of both arms vs the contract
reference at atol = rtol = 1e-2 on every rank.

**Four-rank T=1 physical build (B300).** The SM103 four-rank
BF16/T1/E8/no-PDL row is the only SM103 row at parity with upstream
(0.9852x in the final measurement, 1.0021x in the first). Before
changing anything, the production build (SM103 T=1 schedule with the
reviewed four-rank serial clear), the serial-clear toggle, and the
generic schedule with and without the serial clear were timed against
upstream `backend="trtllm"` in one four-rank session under the same
CUDA-graph replay protocol as the export (three counterbalanced groups,
600/6000 samples per arm and group, cold L2, CUPTI, maximum per-rank
sample): production 15.776 us, best candidate 15.648 us, upstream 15.744
us — all five arms within 1.5 % of each other, below the 1 % decision
band, so the production build is kept and no program changes. This shape
is a structural parity row (same one-shot Lamport algorithm and launch
geometry as upstream), reported and not dropped.

| Row | Physical build | Rank-max median (us) | upstream
`backend="trtllm"` / build | production / build | Correct |
|---|---|---:|---:|---:|---|
| ws4 bfloat16 T1 E8 nopdl | `sm103_t1+serial_clear` (production) |
15.776 (groups 15.90, 15.81, 15.58) | 0.9980 | 1.0000 | True |
| ws4 bfloat16 T1 E8 nopdl | `sm103_t1` | 15.648 (groups 15.95, 15.46,
15.62) | 1.0061 | 1.0082 | True |
| ws4 bfloat16 T1 E8 nopdl | `generic+serial_clear` | 15.872 (groups
16.13, 15.58, 15.92) | 0.9919 | 0.9940 | True |
| ws4 bfloat16 T1 E8 nopdl | `generic` | 15.680 (groups 16.29, 15.33,
15.52) | 1.0041 | 1.0061 | True |
| ws4 bfloat16 T1 E8 nopdl | upstream `backend="trtllm"` | 15.744
(groups 16.27, 15.58, 15.42) | 1.0000 | 1.0020 | True |

Decision for this row: `sm103_t1+serial_clear` ->
`sm103_t1+serial_clear` (no candidate beats the production build
(sm103_t1+serial_clear) by more than 0.010; production selection kept).

Same timing protocol as the export tables: every arm captured into a
CUDA graph and replayed, 3 counterbalanced groups, 600/6000
warm-up/measured samples per arm and group, same-arm preconditioning,
cold L2, CUPTI, maximum per-rank sample; noise band 1%; every arm
checked against the reference at atol = rtol = 1e-2 on all four ranks.

**Four-rank T=1 row, kernel-level fix (B300).** The previous revision
measured the SM103 four-rank BF16/T1/E8/no-PDL row at parity with
upstream (0.9852x). This revision changes the SM103 T=1 schedule body
(all three SM103 T=1 programs): the fused epilogue's residual/gamma
loads are issued before the Lamport poll, and the RMS block partials are
exchanged push-style behind a single cluster barrier (every thread sums
the local copies in fixed CTA order). Values, rounding points and store
order are unchanged; the outputs bit-match upstream. Both changes were
measured in the export's timing regime before promotion (tables below:
probe 1 = hoisted loads only, probe 2 = hoisted loads + single-barrier
exchange as `sm103_t1_push`, which is now the `sm103_t1` body); the
SM103 tables above were re-measured in full with the new programs. The
revision of this PR's branch that carries the change regenerates the
shipped program set byte-for-byte (module fingerprints equal
one-to-one).

| Row | Physical build | Rank-max median (us) | upstream
`backend="trtllm"` / build | production / build | Correct |
|---|---|---:|---:|---:|---|
| ws4 bfloat16 T1 E8 nopdl | `sm103_t1+serial_clear` (production) |
18.272 (groups 18.11, 18.24, 18.43) | 1.0385 | 1.0000 | True |
| ws4 bfloat16 T1 E8 nopdl | `sm103_t1` | 18.336 (groups 18.50, 17.98,
18.50) | 1.0349 | 0.9965 | True |
| ws4 bfloat16 T1 E8 nopdl | `generic+serial_clear` | 19.424 (groups
19.52, 19.07, 19.71) | 0.9769 | 0.9407 | True |
| ws4 bfloat16 T1 E8 nopdl | `generic` | 19.264 (groups 19.74, 18.79,
19.20) | 0.9850 | 0.9485 | True |
| ws4 bfloat16 T1 E8 nopdl | upstream `backend="trtllm"` | 18.976
(groups 19.26, 18.88, 18.72) | 1.0000 | 0.9629 | True |

Decision for this row: `sm103_t1+serial_clear` ->
`sm103_t1+serial_clear` (no candidate beats the production build
(sm103_t1+serial_clear) by more than 0.010; production selection kept).

Same timing protocol as the export tables: every arm captured into a
CUDA graph and replayed, 3 counterbalanced groups, 600/6000
warm-up/measured samples per arm and group, same-arm preconditioning,
cold L2, CUPTI, maximum per-rank sample; noise band 1%; every arm
checked against the reference at atol = rtol = 1e-2 on all four ranks.

| Row | Physical build | Rank-max median (us) | upstream
`backend="trtllm"` / build | production / build | Correct |
|---|---|---:|---:|---:|---|
| ws4 bfloat16 T1 E8 nopdl | `sm103_t1+serial_clear` (production) |
18.624 (groups 18.78, 18.72, 18.40) | 1.0258 | 1.0000 | True |
| ws4 bfloat16 T1 E8 nopdl | `sm103_t1` | 18.400 (groups 18.30, 18.56,
18.34) | 1.0383 | 1.0122 | True |
| ws4 bfloat16 T1 E8 nopdl | `generic+serial_clear` | 19.489 (groups
19.17, 19.71, 19.68) | 0.9802 | 0.9556 | True |
| ws4 bfloat16 T1 E8 nopdl | `generic` | 19.457 (groups 19.58, 19.49,
19.36) | 0.9819 | 0.9572 | True |
| ws4 bfloat16 T1 E8 nopdl | `sm103_t1_push+serial_clear` (fastest
candidate) | 18.048 (groups 17.95, 18.18, 18.02) | 1.0585 | 1.0319 |
True |
| ws4 bfloat16 T1 E8 nopdl | upstream `backend="trtllm"` | 19.104
(groups 18.91, 18.98, 19.39) | 1.0000 | 0.9749 | True |

Decision for this row: `sm103_t1+serial_clear` ->
`sm103_t1_push+serial_clear` (sm103_t1_push+serial_clear faster than the
production build (sm103_t1+serial_clear) by 0.0309).

Same timing protocol as the export tables: every arm captured into a
CUDA graph and replayed, 3 counterbalanced groups, 600/6000
warm-up/measured samples per arm and group, same-arm preconditioning,
cold L2, CUPTI, maximum per-rank sample; noise band 1%; every arm
checked against the reference at atol = rtol = 1e-2 on all four ranks.

### Evidence — SM100 (8xB200, NVIDIA B200 CC 10.0, driver 580.82.07,
torch 2.13.0+cu130)

Protocol: one NCCL rank set per shape (2, 4 or 8 ranks on one node),
every sample the per-rank maximum across ranks;
symmetric external CUDA-graph arms; 3 counterbalanced groups, 600
warm-up and 6000 reportable samples per arm and
group; same-arm preconditioning; cold L2; CUPTI. Arms: `source` = the
Cake union launcher on the same workspace,
`exported` = this PR's `backend="cake"` route (bitwise-identical outputs
to `source`), `trtllm` = `backend="trtllm"`
on its own workspace, `cake_legacy` = the isolated source bundle (#4730)
that served these calls before this PR.
Correctness for every arm vs the rank-summed reference at atol = rtol =
1e-2 on the three outputs.

SM100 world size 2: 10/10 correct, 10/10 sealed, trtllm / export geomean
1.2572x (min 1.0881x, 10/10 rows >= 1.0x), shipped cake / export geomean
1.0757x (min 1.0000x, 10/10 rows >= 1.0x), source / export 0.9950x;
SM100 world size 4: 10/10 correct, 10/10 sealed, trtllm / export geomean
1.1313x (min 0.9789x, 9/10 rows >= 1.0x), shipped cake / export geomean
0.9595x (min 0.7966x, 1/10 rows >= 1.0x), source / export 1.0034x; SM100
world size 8: 10/10 correct, 9/10 sealed, trtllm / export geomean
1.1105x (min 1.0409x, 10/10 rows >= 1.0x), shipped cake / export geomean
1.0107x (min 0.9999x, 9/10 rows >= 1.0x), source / export 0.9837x.

`ws8_fp16_t2048_e8_nopdl` (SM100) is measured and correct on every rank
(incl. bitwise source/export equality) (1.1203x vs `backend="trtllm"`,
1.0118x vs the isolated bundle) but is **not sealed**: it misses the
exporter's gate(s) `source_over_export` = 0.9688 (`PERFORMANCE
min_source_over_export` = 0.97: the FlashInfer route must run within 3 %
of the in-tree Cake launcher of the identical program). This is a
launch-route timing statistic, not a numerical one: correctness passes
including bitwise source/export equality (`source_export_bitwise`), and
both ratified baselines are beaten. Left unsealed rather than loosening
the floor; reported for the owner's decision.

### World size 2 (10 rows)

| Shape | dtype | T | experts | PDL | Specialization | Source ms |
Export ms | Source / Export | trtllm ms | trtllm / Export | legacy cake
ms | legacy / Export | Correctness | Verdict |
|---|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---|---|
| ws2_bf16_t1_e8_nopdl | bfloat16 | 1 | 8 | off | generic | 0.012256 |
0.012352 | 0.9922x | 0.013440 | 1.0881x | 0.012832 | 1.0389x | pass |
pass |
| ws2_bf16_t64_e8_pdl | bfloat16 | 64 | 8 | on | generic | 0.017952 |
0.017857 | 1.0053x | 0.021920 | 1.2275x | 0.019648 | 1.1003x | pass |
pass |
| ws2_fp16_t64_e12_nopdl | float16 | 64 | 12 | off | generic | 0.020672
| 0.020640 | 1.0016x | 0.025696 | 1.2450x | 0.020640 | 1.0000x | pass |
pass |
| ws2_bf16_t128_e16_nopdl | bfloat16 | 128 | 16 | off | generic |
0.041151 | 0.041407 | 0.9938x | 0.053120 | 1.2829x | 0.047712 | 1.1523x
| pass | pass |
| ws2_fp16_t128_e16_pdl | float16 | 128 | 16 | on | generic | 0.039392 |
0.039680 | 0.9927x | 0.051776 | 1.3048x | 0.039777 | 1.0024x | pass |
pass |
| ws2_bf16_t256_e8_nopdl | bfloat16 | 256 | 8 | off | generic | 0.047296
| 0.047392 | 0.9980x | 0.059551 | 1.2566x | 0.053152 | 1.1215x | pass |
pass |
| ws2_bf16_t256_e12_pdl | bfloat16 | 256 | 12 | on | generic | 0.056416
| 0.056575 | 0.9972x | 0.072128 | 1.2749x | 0.064833 | 1.1460x | pass |
pass |
| ws2_fp16_t2048_e8_nopdl | float16 | 2048 | 8 | off | generic |
0.340160 | 0.343776 | 0.9895x | 0.437406 | 1.2724x | 0.352286 | 1.0248x
| pass | pass |
| ws2_bf16_t2048_e12_pdl | bfloat16 | 2048 | 12 | on | generic |
0.399294 | 0.403455 | 0.9897x | 0.524352 | 1.2997x | 0.473281 | 1.1731x
| pass | pass |
| ws2_fp16_t2048_e16_pdl | float16 | 2048 | 16 | on | generic | 0.463456
| 0.467873 | 0.9906x | 0.625758 | 1.3375x | 0.475647 | 1.0166x | pass |
pass |

World size 2: 10/10 correct, 10/10 sealed; trtllm / export geomean
1.2572x (min 1.0881x, max 1.3375x, 10/10 rows >= 1.0x); legacy cake /
export geomean 1.0757x (min 1.0000x, 10/10 rows >= 1.0x); source /
export geomean 0.9950x.

### World size 4 (10 rows)

| Shape | dtype | T | experts | PDL | Specialization | Source ms |
Export ms | Source / Export | trtllm ms | trtllm / Export | legacy cake
ms | legacy / Export | Correctness | Verdict |
|---|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---|---|
| ws4_bf16_t1_e8_nopdl | bfloat16 | 1 | 8 | off |
clearserial_t1_e8_serial_clear | 0.013760 | 0.013664 | 1.0070x |
0.013376 | 0.9789x | 0.012864 | 0.9415x | pass | pass |
| ws4_bf16_t64_e8_pdl | bfloat16 | 64 | 8 | on | generic | 0.019360 |
0.019264 | 1.0050x | 0.021472 | 1.1146x | 0.018720 | 0.9718x | pass |
pass |
| ws4_fp16_t64_e12_nopdl | float16 | 64 | 12 | off | t64_e12_resident |
0.019616 | 0.019520 | 1.0049x | 0.023584 | 1.2082x | 0.019296 | 0.9885x
| pass | pass |
| ws4_bf16_t128_e16_nopdl | bfloat16 | 128 | 16 | off | generic |
0.041888 | 0.041760 | 1.0031x | 0.045119 | 1.0804x | 0.040032 | 0.9586x
| pass | pass |
| ws4_fp16_t128_e16_pdl | float16 | 128 | 16 | on |
t128_e16_owner_forward | 0.027936 | 0.027776 | 1.0058x | 0.044352 |
1.5968x | 0.034464 | 1.2408x | pass | pass |
| ws4_bf16_t256_e8_nopdl | bfloat16 | 256 | 8 | off | generic | 0.051808
| 0.051648 | 1.0031x | 0.057152 | 1.1066x | 0.050496 | 0.9777x | pass |
pass |
| ws4_bf16_t256_e12_pdl | bfloat16 | 256 | 12 | on | generic | 0.062592
| 0.062272 | 1.0051x | 0.068368 | 1.0979x | 0.060289 | 0.9681x | pass |
pass |
| ws4_fp16_t2048_e8_nopdl | float16 | 2048 | 8 | off | generic |
0.400574 | 0.400352 | 1.0006x | 0.430016 | 1.0741x | 0.348128 | 0.8696x
| pass | pass |
| ws4_bf16_t2048_e12_pdl | bfloat16 | 2048 | 12 | on | generic |
0.456640 | 0.456641 | 1.0000x | 0.499809 | 1.0945x | 0.428350 | 0.9380x
| pass | pass |
| ws4_fp16_t2048_e16_pdl | float16 | 2048 | 16 | on | generic | 0.523937
| 0.523968 | 0.9999x | 0.554112 | 1.0575x | 0.417375 | 0.7966x | pass |
pass |

World size 4: 10/10 correct, 10/10 sealed; trtllm / export geomean
1.1313x (min 0.9789x, max 1.5968x, 9/10 rows >= 1.0x); legacy cake /
export geomean 0.9595x (min 0.7966x, 1/10 rows >= 1.0x); source / export
geomean 1.0034x.

### World size 8 (10 rows)

| Shape | dtype | T | experts | PDL | Specialization | Source ms |
Export ms | Source / Export | trtllm ms | trtllm / Export | legacy cake
ms | legacy / Export | Correctness | Verdict |
|---|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---|---|
| ws8_bf16_t1_e8_nopdl | bfloat16 | 1 | 8 | off | generic | 0.016320 |
0.016257 | 1.0039x | 0.017311 | 1.0648x | 0.016256 | 0.9999x | pass |
pass |
| ws8_bf16_t64_e8_pdl | bfloat16 | 64 | 8 | on | sm100_ws8_mid |
0.029600 | 0.030015 | 0.9862x | 0.033792 | 1.1258x | 0.030528 | 1.0171x
| pass | pass |
| ws8_fp16_t64_e12_nopdl | float16 | 64 | 12 | off | sm100_ws8_mid |
0.030688 | 0.030912 | 0.9928x | 0.034016 | 1.1004x | 0.031040 | 1.0041x
| pass | pass |
| ws8_bf16_t128_e16_nopdl | bfloat16 | 128 | 16 | off | sm100_ws8_mid |
0.050304 | 0.050688 | 0.9924x | 0.057984 | 1.1439x | 0.051680 | 1.0196x
| pass | pass |
| ws8_fp16_t128_e16_pdl | float16 | 128 | 16 | on | sm100_ws8_mid |
0.049504 | 0.050016 | 0.9898x | 0.056512 | 1.1299x | 0.050656 | 1.0128x
| pass | pass |
| ws8_bf16_t256_e8_nopdl | bfloat16 | 256 | 8 | off | generic | 0.083648
| 0.084960 | 0.9846x | 0.096127 | 1.1314x | 0.085665 | 1.0083x | pass |
pass |
| ws8_bf16_t256_e12_pdl | bfloat16 | 256 | 12 | on | generic | 0.087584
| 0.089696 | 0.9765x | 0.100032 | 1.1152x | 0.090208 | 1.0057x | pass |
pass |
| ws8_fp16_t2048_e8_nopdl | float16 | 2048 | 8 | off | generic |
0.615552 | 0.635390 | 0.9688x | 0.711809 | 1.1203x | 0.642913 | 1.0118x
| pass | FAIL |
| ws8_bf16_t2048_e12_pdl | bfloat16 | 2048 | 12 | on | generic |
0.640448 | 0.659233 | 0.9715x | 0.749441 | 1.1368x | 0.671009 | 1.0179x
| pass | pass |
| ws8_fp16_t2048_e16_pdl | float16 | 2048 | 16 | on | generic | 0.648960
| 0.668225 | 0.9712x | 0.695584 | 1.0409x | 0.675134 | 1.0103x | pass |
pass |

World size 8: 10/10 correct, 9/10 sealed; trtllm / export geomean
1.1105x (min 1.0409x, max 1.1439x, 10/10 rows >= 1.0x); legacy cake /
export geomean 1.0107x (min 0.9999x, 9/10 rows >= 1.0x); source / export
geomean 0.9837x.



### Evidence — SM103 (8xB300, NVIDIA B300 SXM6 AC CC 10.3, driver
580.126.09, torch 2.10.0a0+a36e1d39eb.nv26.01.42222806)

Same protocol on one B300 node (ws2/ws4 rank sets on device ordinals 0-1
/ 0-3, ws8 on all eight GPUs); `cake_legacy` is
the isolated source bundle's SM103 program set (`generic` / `sm103_t1`).
This revision's SM103 rows were re-measured in full on a fresh B300 node
with the new T=1 programs.

SM103 world size 2: 10/10 correct, 10/10 sealed, trtllm / export geomean
1.2337x (min 1.0549x, 10/10 rows >= 1.0x), shipped cake / export geomean
1.0092x (min 0.9972x, 8/10 rows >= 1.0x), source / export 1.0010x; SM103
world size 4: 10/10 correct, 10/10 sealed, trtllm / export geomean
1.2301x (min 1.0361x, 10/10 rows >= 1.0x), shipped cake / export geomean
1.0616x (min 0.9983x, 9/10 rows >= 1.0x), source / export 1.0009x; SM103
world size 8: 10/10 correct, 10/10 sealed, trtllm / export geomean
1.1019x (min 1.0351x, 10/10 rows >= 1.0x), shipped cake / export geomean
1.0130x (min 0.9965x, 7/10 rows >= 1.0x), source / export 1.0011x.

SM103: all thirty rows are sealed by the exporter's protocol gates.

SM103: every row measures >= 1.0x vs `backend="trtllm"`.

### SM103 (8xB300) World size 2 (10 rows)

| Shape | dtype | T | experts | PDL | Specialization | Source ms |
Export ms | Source / Export | trtllm ms | trtllm / Export | legacy cake
ms | legacy / Export | Correctness | Verdict |
|---|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---|---|
| sm103_ws2_bf16_t1_e8_nopdl | bfloat16 | 1 | 8 | off | sm103_t1 |
0.017376 | 0.017473 | 0.9944x | 0.018432 | 1.0549x | 0.018176 | 1.0402x
| pass | pass |
| sm103_ws2_bf16_t64_e8_pdl | bfloat16 | 64 | 8 | on | generic |
0.018657 | 0.018592 | 1.0035x | 0.022497 | 1.2100x | 0.018624 | 1.0017x
| pass | pass |
| sm103_ws2_fp16_t64_e12_nopdl | float16 | 64 | 12 | off | generic |
0.024960 | 0.024768 | 1.0078x | 0.029856 | 1.2054x | 0.025024 | 1.0103x
| pass | pass |
| sm103_ws2_bf16_t128_e16_nopdl | bfloat16 | 128 | 16 | off | generic |
0.042880 | 0.042816 | 1.0015x | 0.054464 | 1.2720x | 0.042944 | 1.0030x
| pass | pass |
| sm103_ws2_fp16_t128_e16_pdl | float16 | 128 | 16 | on | generic |
0.039328 | 0.039329 | 1.0000x | 0.050785 | 1.2913x | 0.039488 | 1.0040x
| pass | pass |
| sm103_ws2_bf16_t256_e8_nopdl | bfloat16 | 256 | 8 | off | generic |
0.047872 | 0.047904 | 0.9993x | 0.059232 | 1.2365x | 0.048768 | 1.0180x
| pass | pass |
| sm103_ws2_bf16_t256_e12_pdl | bfloat16 | 256 | 12 | on | generic |
0.056641 | 0.056512 | 1.0023x | 0.070785 | 1.2526x | 0.057280 | 1.0136x
| pass | pass |
| sm103_ws2_fp16_t2048_e8_nopdl | float16 | 2048 | 8 | off | generic |
0.342081 | 0.341988 | 1.0003x | 0.424097 | 1.2401x | 0.341025 | 0.9972x
| pass | pass |
| sm103_ws2_bf16_t2048_e12_pdl | bfloat16 | 2048 | 12 | on | generic |
0.400420 | 0.400258 | 1.0004x | 0.512261 | 1.2798x | 0.402948 | 1.0067x
| pass | pass |
| sm103_ws2_fp16_t2048_e16_pdl | float16 | 2048 | 16 | on | generic |
0.462498 | 0.462402 | 1.0002x | 0.608134 | 1.3152x | 0.461413 | 0.9979x
| pass | pass |

World size 2: 10/10 correct, 10/10 sealed; trtllm / export geomean
1.2337x (min 1.0549x, max 1.3152x, 10/10 rows >= 1.0x); legacy cake /
export geomean 1.0092x (min 0.9972x, 8/10 rows >= 1.0x); source / export
geomean 1.0010x (min 0.9944x, max 1.0078x).

### SM103 (8xB300) World size 4 (10 rows)

| Shape | dtype | T | experts | PDL | Specialization | Source ms |
Export ms | Source / Export | trtllm ms | trtllm / Export | legacy cake
ms | legacy / Export | Correctness | Verdict |
|---|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---|---|
| sm103_ws4_bf16_t1_e8_nopdl | bfloat16 | 1 | 8 | off |
clearserial_sm103_t1_t1_e8_serial_clear | 0.019232 | 0.019488 | 0.9869x
| 0.020192 | 1.0361x | 0.020736 | 1.0640x | pass | pass |
| sm103_ws4_bf16_t64_e8_pdl | bfloat16 | 64 | 8 | on | generic |
0.023232 | 0.022976 | 1.0111x | 0.024608 | 1.0710x | 0.023104 | 1.0056x
| pass | pass |
| sm103_ws4_fp16_t64_e12_nopdl | float16 | 64 | 12 | off |
t64_e12_resident | 0.024736 | 0.024608 | 1.0052x | 0.034368 | 1.3966x |
0.027040 | 1.0988x | pass | pass |
| sm103_ws4_bf16_t128_e16_nopdl | bfloat16 | 128 | 16 | off | generic |
0.045632 | 0.045633 | 1.0000x | 0.048192 | 1.0561x | 0.046593 | 1.0210x
| pass | pass |
| sm103_ws4_fp16_t128_e16_pdl | float16 | 128 | 16 | on |
t128_e16_owner_forward | 0.030816 | 0.030849 | 0.9989x | 0.062352 |
2.0212x | 0.046080 | 1.4937x | pass | pass |
| sm103_ws4_bf16_t256_e8_nopdl | bfloat16 | 256 | 8 | off | generic |
0.054272 | 0.053984 | 1.0053x | 0.058401 | 1.0818x | 0.054112 | 1.0024x
| pass | pass |
| sm103_ws4_bf16_t256_e12_pdl | bfloat16 | 256 | 12 | on | generic |
0.066464 | 0.066337 | 1.0019x | 0.071553 | 1.0786x | 0.066656 | 1.0048x
| pass | pass |
| sm103_ws4_fp16_t2048_e8_nopdl | float16 | 2048 | 8 | off | generic |
0.395044 | 0.395171 | 0.9997x | 0.527364 | 1.3345x | 0.394500 | 0.9983x
| pass | pass |
| sm103_ws4_bf16_t2048_e12_pdl | bfloat16 | 2048 | 12 | on | generic |
0.450627 | 0.450501 | 1.0003x | 0.485861 | 1.0785x | 0.454309 | 1.0085x
| pass | pass |
| sm103_ws4_fp16_t2048_e16_pdl | float16 | 2048 | 16 | on | generic |
0.516518 | 0.516581 | 0.9999x | 0.737640 | 1.4279x | 0.516710 | 1.0002x
| pass | pass |

World size 4: 10/10 correct, 10/10 sealed; trtllm / export geomean
1.2301x (min 1.0361x, max 2.0212x, 10/10 rows >= 1.0x); legacy cake /
export geomean 1.0616x (min 0.9983x, 9/10 rows >= 1.0x); source / export
geomean 1.0009x (min 0.9869x, max 1.0111x).

### SM103 (8xB300) World size 8 (10 rows)

| Shape | dtype | T | experts | PDL | Specialization | Source ms |
Export ms | Source / Export | trtllm ms | trtllm / Export | legacy cake
ms | legacy / Export | Correctness | Verdict |
|---|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---|---|
| sm103_ws8_bf16_t1_e8_nopdl | bfloat16 | 1 | 8 | off | sm103_t1 |
0.020128 | 0.020001 | 1.0063x | 0.020704 | 1.0351x | 0.020416 | 1.0207x
| pass | pass |
| sm103_ws8_bf16_t64_e8_pdl | bfloat16 | 64 | 8 | on | generic |
0.032224 | 0.032128 | 1.0030x | 0.035073 | 1.0917x | 0.032640 | 1.0159x
| pass | pass |
| sm103_ws8_fp16_t64_e12_nopdl | float16 | 64 | 12 | off | generic |
0.033440 | 0.033377 | 1.0019x | 0.035648 | 1.0680x | 0.033344 | 0.9990x
| pass | pass |
| sm103_ws8_bf16_t128_e16_nopdl | bfloat16 | 128 | 16 | off | generic |
0.051841 | 0.051905 | 0.9988x | 0.057633 | 1.1104x | 0.052897 | 1.0191x
| pass | pass |
| sm103_ws8_fp16_t128_e16_pdl | float16 | 128 | 16 | on | generic |
0.051393 | 0.051329 | 1.0012x | 0.056449 | 1.0997x | 0.051360 | 1.0006x
| pass | pass |
| sm103_ws8_bf16_t256_e8_nopdl | bfloat16 | 256 | 8 | off | generic |
0.084480 | 0.084608 | 0.9985x | 0.095041 | 1.1233x | 0.086401 | 1.0212x
| pass | pass |
| sm103_ws8_bf16_t256_e12_pdl | bfloat16 | 256 | 12 | on | generic |
0.087553 | 0.087457 | 1.0011x | 0.098177 | 1.1226x | 0.089217 | 1.0201x
| pass | pass |
| sm103_ws8_fp16_t2048_e8_nopdl | float16 | 2048 | 8 | off | generic |
0.606279 | 0.606181 | 1.0002x | 0.679558 | 1.1210x | 0.605027 | 0.9981x
| pass | pass |
| sm103_ws8_bf16_t2048_e12_pdl | bfloat16 | 2048 | 12 | on | generic |
0.626886 | 0.626983 | 0.9998x | 0.708936 | 1.1307x | 0.651623 | 1.0393x
| pass | pass |
| sm103_ws8_fp16_t2048_e16_pdl | float16 | 2048 | 16 | on | generic |
0.638375 | 0.638311 | 1.0001x | 0.714758 | 1.1198x | 0.636068 | 0.9965x
| pass | pass |

World size 8: 10/10 correct, 10/10 sealed; trtllm / export geomean
1.1019x (min 1.0351x, max 1.1307x, 10/10 rows >= 1.0x); legacy cake /
export geomean 1.0130x (min 0.9965x, 7/10 rows >= 1.0x); source / export
geomean 1.0011x (min 0.9985x, max 1.0063x).



### Baselines and their source PRs

- `trtllm_moe_allreduce_fusion(backend="trtllm")`: upstream main at
`78c6e1fbfcb` (this PR's base), on SM100 and SM103.
- `backend="cake"` isolated source bundle
(`csrc/cake_trtllm_moe_allreduce_fusion`, SM100 `generic` /
`sm100_ws8_mid` and
  SM103 `generic` / `sm103_t1` program sets): #4730, at `78c6e1fbfcb`.
- World-size-4 SM100 union export: #5514 (merged as `b6d920aad`).

## 🔍 Related Issues

- #5514 (world-size-4 union export this PR extends)
- #4730 (isolated bundle; remains the path for calls without the
all-reduce output and for other architectures)
- Tracker: #4254

## 🚀 Pull Request Checklist

- [x] Pre-commit hooks pass on the changed hand-written files (the
generated directory is excluded as a byte-faithful export).
- [x] Tests: `tests/comm/test_cake_moe_allreduce_union.py`,
`tests/comm/test_cake_moe_allreduce_api.py`,
      `tests/comm/test_cake_trtllm_moe_allreduce_source.py` (CPU) and
`tests/comm/test_cake_moe_allreduce_distributed.py -k "tp2 or tp4 or
tp8"` (eight B200 GPUs and eight B300 GPUs).
- [x] Public API behaviour for `backend="trtllm"` and for calls without
`moe_allreduce_out` is unchanged; the SM100 program
      set is byte-identical to the previous revision of this PR.

## Reviewer Notes

The export receipts (correctness against the contract reference, bitwise
source/export parity, allocation probe,
no-fallback route check, per-rank timing with the maximum across ranks
per sample) were produced by the Cake
generated-program exporter on one B200 node (SM100) and one B300 node
(SM103); the tables above list every row of the
frozen thirty-row denominator per architecture. The evaluation binds
PyTorch's NVSHMEM symmetric-memory backend for the
process group before the workspaces are allocated (both arms share the
provider), as in #5514. `compute-sanitizer` is
not available in those environments; the generated device code is the
validated Cake source and only host-side binding
and routing are new.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b9fe0f4](https://github.com/flashinfer-ai/flashinfer/commit/b9fe0f453a4aef5db1d0a8adff4e41141b6c97df)

- **作者**: eigen
- **时间**: 2026-09-27T21:34:03Z
- **提交信息**: perf(cake_fp8_projection): Kimi-K3 KDA/MLA projection GEMM (per-token FP8 activations x per-block FP8 weights, SM100/SM103) round 2: TMA-store epilogue and fused-quant decode route for large-M single-N-tile layers (#5590)

## Summary

Round 2 of the experimental generated-program backend for the serialized
`FP8_PB_WO` KDA / MLA projection GEMMs of `nvidia/Kimi-K3-NVFP4` on
`sm_100a` (B200) and `sm_103a` (B300/GB300),
`flashinfer/experimental/kimi_k3_fp8_projection` (round 1: #5572). The
operator, entry points and numerics are unchanged (per-token 1x128 E4M3
quantization with UE8M0 scales, bit-exact with DeepGEMM
`per_token_cast_to_fp8(use_ue8m0=True)`; block-scaled tcgen05 GEMM into
an arbitrary-even-stride BF16 view; padding never written). What changes
is the program set and the dispatch:

- **TMA-store GEMM epilogue** (`gemm_tstore` program): each epilogue
warp group stages 128 x 32 BF16 columns in a 64-byte-swizzled SMEM tile
and issues `cp.async.bulk.tensor` stores; selected when the output view
has a 16-byte base, a row stride that is a multiple of 8 elements **and
a valid width that is a multiple of 8 elements** (the TMA unit
bounds-checks the inner axis of a store at 16-byte granularity; any
other view keeps the predicated register epilogue). 1-3 % on the large-M
GEMM rows.
- **Table-driven decode route above 256 rows** for the single-N-tile
families (`f_a`, `b_proj`): the measured dispatch table gains the `4096`
/ `16384` buckets, so those rows take the fused decode kernel (1.47x at
M = 4096) instead of the GEMM.
- Host: `cake_backend.py` (route plan, `gemm_tma_store_eligible`,
large-M buckets), `decode_table.py` (regenerated per architecture),
`cake_jit.py` registries (regenerated, 12 programs per arch),
`csrc/cake_kimi_k3_fp8_projection/{sm_100a,sm_103a}/*` (regenerated),
tests (+1 padded row), benchmark.

## Evidence (export protocol, producer `67dbe6d9360`, target
`bde7f3617b1`)

Every contract row (22 families x `M in {1, 8, 64, 256, 4096, 16384}` =
132 perf rows, plus 88 correctness-only rows with `M in {3, 129, 1000,
4097}` and padded output strides) is measured on the source launcher and
on the exported programs in counterbalanced pairs (CUPTI, cold L2,
CUDA-graph replay, SM-clock floor 0.55 of rated max; observed 1965 MHz
on B200 and 2032 MHz on B300 throughout).

| arch | GPU | rows measured | correct (bitwise source == export) |
sealed (all timing gates) | source / export (min .. max, geomean) |
|---|---|---|---|---|---|
| sm_100a | B200 | 220 | 220 | 218 | 0.9419 .. 1.0645, 0.9977 |
| sm_103a | B300 | 220 | 220 | 218 | 0.9431 .. 1.0800, 1.0002 |

Rounds, all disclosed: the first run was aborted after it exposed a
padded-stride bug in the TMA-store dispatch (fixed in this PR's host
code before any receipt was consumed); the full run then sealed 217 rows
per GPU; a retry round (the full run closed as a read-only prior
snapshot, only the failed rows re-measured) sealed one more row per GPU.
The two rows still unsealed on each GPU are the same pair:

| GPU | row | source us | export us | source / export | gate (round 1 /
retry) |
|---|---|---:|---:|---:|---|
| B200 | `tp1 kv_a M=64` | 11.90 | 11.84 | 1.005x | directional
disagreement 0.100 / 0.111 (limit 0.08) |
| B200 | `tp8 kv_a M=64` | 11.87 | 11.90 | 0.997x | directional
disagreement 0.126 / 0.080 |
| B300 | `tp1 kv_a M=64` | 12.51 | 11.59 | 1.080x | directional
disagreement 0.136 / 0.191 |
| B300 | `tp8 kv_a M=64` | 11.65 | 11.65 | 1.000x | directional
disagreement 0.148 / 0.161 |

Source and export are the same generated kernel (bitwise-identical
output, byte-identical delivery on both GPUs) and the pooled ratio is at
parity; the two arm orders of the counterbalanced pairs disagree by 8-19
% only on this row family (the shortest persistent decode call, whose
first arm after the cold-L2 flush pays the weight re-warm). The same
pair failed the same gate in round 1 (#5572) on both GPUs; it is
disclosed rather than re-rolled. The rows disclosed in #5572 below the
0.94 speed floor (B300 `tp1 b_proj M=1` 0.937, `tp8 f_b M=3` 0.932)
measure 1.004 and 0.944 on this delivery.

Exported programs vs the fastest existing FP8 chain per row, same
process, CUDA-graph replay, CUPTI, cold L2
(`benchmarks/bench_cake_kimi_k3_fp8_projection.py --cupti`; chains:
`per_token_group_quant_8bit` + `gemm_fp8_nt_groupwise` with `cutlass`
mma_sm1 / mma_sm2, `trtllm` and `cutile`; `trtllm` rejects K = 128 and N
< 256 (`a.shape[1] must be >= 256`) so those 7 rows compare against the
other three chains):

| GPU | rows faster than the best chain | min | geomean | max | `tp1
kv_b M=256` | best chain census |
|---|---|---|---|---|---|---|
| B200 | **132 / 132** | 1.042x (`tp1 fused_qkvg M=1`) | 1.839x | 5.730x
| 1.269x | trtllm 60, cutile 43, cutlass sm2 22, cutlass sm1 7 |
| B300 | **132 / 132** | 1.045x (`tp1 fused_qkvg M=1`) | 1.836x | 5.965x
| 1.246x | trtllm 60, cutile 42, cutlass sm2 21, cutlass sm1 9 |

`tests/experimental/test_cake_kimi_k3_fp8_projection.py`: 33 passed on
B200 and on B300 against this tree. Delivery is byte-identical from both
GPUs (`delivery.patch` SHA-256
`a18e6290d5b2c7123ea106d83358dd58563ee19e1b9cb91d72ac5a002e4b5879`).

## Baselines and their source PRs

The comparison arms are upstream FlashInfer entry points at
`9b727df8af4858db231f7f3a436a8a87fe54e563` (this branch's upstream
merge-base). No upstream kernel is modified.

- `per_token_group_quant_8bit`
(`flashinfer/quantization/fp8_quantization.py`, cuTile kernel
`flashinfer/quantization/kernels/cutile/per_token_group_quant_8bit_cutile.py`):
#4019 (`c517c07bd`, 2026-08-13).
- `gemm_fp8_nt_groupwise` `backend="cutlass"` (`mma_sm` 1 and 2;
`csrc/gemm_groupwise_sm100.cu`,
`csrc/gemm_groupwise_sm100_kernel_inst.jinja`,
`flashinfer/gemm/gemm_base.py`): #1045 (`71002782f`, 2025-05-04).
- `gemm_fp8_nt_groupwise` `backend="trtllm"`
(`csrc/trtllm_gemm_runner.cu`): #1320 (`67e77fd5a`, 2025-07-28); last
change #4280 (`5b1af9724`, 2026-07-30).
- `gemm_fp8_nt_groupwise` `backend="cutile"`
(`flashinfer/gemm/kernels/cutile/gemm_fp8_nt_groupwise_cutile.py`):
#3426 (`992848ad3`, 2026-06-12); last change #4459 (`d70a043f5`,
2026-09-12).
- DeepGEMM `fp8_gemm_nt` with `per_token_group_quant_8bit(...,
scale_ue8m0=True)` packing: deepseek-ai/DeepGEMM
`78b69000794d0937b47ae3387eff7663410264d1` (external).
- Round-1 programs of this backend (#5572) are the previous state of the
same entry points; the speedups above are against the existing FP8
chains, not against round 1.
- BF16 cuBLAS (`torch.matmul` on the dequantized weight) is reported as
an informational reference only.

Test oracle: the exact quantized-operand emulation in
`tests/experimental/test_cake_kimi_k3_fp8_projection.py`.

## Test

```
pytest tests/experimental/test_cake_kimi_k3_fp8_projection.py
python benchmarks/bench_cake_kimi_k3_fp8_projection.py --cupti
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Expanded Kimi K3 FP8 projection routing with measured decode options
for selected large workloads.
* Added a TMA-store GEMM path for eligible output layouts, with the
existing GEMM path retained for other layouts.
  * Added projection kernel support for additional GPU architectures.
* **Bug Fixes**
* Improved kernel synchronization handling and added validation for
projection inputs and launch configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [05ebb2d](https://github.com/flashinfer-ai/flashinfer/commit/05ebb2d7976e9389ea63bbd03a9a5cc8c0dbb525)

- **作者**: eigen
- **时间**: 2026-09-27T20:35:10Z
- **提交信息**: feat(cake_fused_moe): add Kimi-K3 W4A8 MXFP4 SiTU routed MoE for SM100/SM103 (#5430)

Adds a source-visible CuTe DSL **W4A8 MXFP4 SiTU routed MoE** runner for
Kimi K3 on
NVIDIA B300 (SM103) and B200 (SM100), as requested in #5156.

### Speedup vs TensorRT-LLM Gen (`trtllm_fp4_block_scale_routed_moe`,
SiTU) on B300

Same GPU, one process, CUPTI kernel timing with an L2 flush before every
sample, 30 paired repeats per row, medians;
ratios are **trtllm-gen ÷ candidate** (above 1.0 = candidate faster).
GPU span = first kernel start to last kernel end of one
graph replay. Every required row (`T = 1..4096`, both layouts, every
routing) is above 1.0; the 45-row contract run at the pinned
revision is 45/45 above 1.0 (geomean 1.240, min 1.039). Method and the
eager / kernel-sum / deferred tables are in the
performance section below; per-row floors are in the docs roofline
section.

| layout | mode / metric | rows | geomean | min | rows ≤ 1.0 |
|---|---|---:|---:|---|---:|
| EP=8 (rank 3, 112 local experts) | graph, GPU span | 44 | 1.387 |
1.039 (T=128 remote-dominated) | 0 |
| EP=8 (rank 3, 112 local experts) | graph, kernel sum | 44 | 1.113 |
0.815 (T=1 balanced) | 13 |
| EP=8 (rank 3, 112 local experts) | eager, kernel sum | 44 | 1.298 |
1.004 (T=128 balanced) | 0 |
| TP=8 (rank 0, I_shard=384) | graph, GPU span | 33 | 1.406 | 1.076
(T=2048 hot) | 0 |
| TP=8 (rank 0, I_shard=384) | graph, kernel sum | 33 | 1.189 | 0.851
(T=1 balanced) | 5 |
| TP=8 (rank 0, I_shard=384) | eager, kernel sum | 33 | 1.328 | 1.034
(T=2048 hot) | 0 |

Per-`T` GPU-span ratios, graph mode, EP=8 (rank 3, 112 local experts):

| T | balanced cand ms | balanced TRT ms | balanced ratio | hot ratio |
empty ratio | remote-dom. ratio | balanced e2e ratio |
|---|---:|---:|---:|---:|---:|---:|---:|
| 1 | 0.0249 | 0.0334 | 1.341 | 1.447 | 1.453 | 1.428 | 1.233 |
| 2 | 0.0361 | 0.0511 | 1.416 | 1.440 | 1.449 | 1.337 | 1.317 |
| 4 | 0.0577 | 0.0782 | 1.354 | 1.399 | 1.420 | 1.417 | 1.299 |
| 8 | 0.0989 | 0.1251 | 1.265 | 1.773 | 1.774 | 1.404 | 1.245 |
| 16 | 0.1795 | 0.2034 | 1.133 | 1.543 | 1.760 | 1.266 | 1.127 |
| 128 | 0.5922 | 0.6151 | 1.039 | 1.045 | 1.635 | 1.039 | 1.035 |
| 256 | 0.6066 | 0.6438 | 1.061 | 1.057 | 1.470 | 1.058 | 1.063 |
| 512 | 0.6103 | 0.7003 | 1.147 | 1.078 | 1.702 | 1.165 | 1.147 |
| 1024 | 0.6196 | 0.7627 | 1.231 | 1.115 | 1.860 | 1.242 | 1.225 |
| 2048 | 0.8050 | 1.2345 | 1.534 | 1.473 | 1.971 | 1.565 | 1.523 |
| 4096 | 0.8348 | 1.2330 | 1.477 | 1.421 | 2.348 | 1.551 | 1.465 |

ep8 graph: 44 rows, geomean 1.387, min 1.039 (T=128 remote-dom.), rows
<= 1.0: 0; e2e min 1.028, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.380, min 1.038 (T=128 balanced), rows <=
1.0: 0; e2e min 1.039, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.387, min 1.036 (T=128 remote-dom.), rows
<= 1.0: 0; e2e min 1.037, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.377, min 1.029 (T=128 remote-dom.), rows
<= 1.0: 0; e2e min 1.031, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.370, min 1.031 (T=128 remote-dom.), rows
<= 1.0: 0; e2e min 1.032, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.376, min 1.033 (T=128 remote-dom.), rows
<= 1.0: 0; e2e min 1.035, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.368, min 1.018 (T=128 remote-dom.), rows
<= 1.0: 0; e2e min 1.021, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.376, min 1.033 (T=128 remote-dom.), rows
<= 1.0: 0; e2e min 1.035, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.373, min 1.031 (T=128 balanced), rows <=
1.0: 0; e2e min 1.032, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.340, min 1.022 (T=128 balanced), rows <=
1.0: 0; e2e min 1.022, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.331, min 1.030 (T=128 balanced), rows <=
1.0: 0; e2e min 1.031, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.212, min 1.004 (T=128 balanced), rows <=
1.0: 0; e2e min 1.017, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.215, min 1.029 (T=128 remote-dom.), rows
<= 1.0: 0; e2e min 1.039, e2e rows <= 1.0: 0

ep8 graph: 44 rows, geomean 1.206, min 1.003 (T=128 balanced), rows <=
1.0: 0; e2e min 1.014, e2e rows <= 1.0: 0



Per-`T` GPU-span ratios, graph mode, TP=8 (rank 0, I_shard=384):

| T | balanced cand ms | balanced TRT ms | balanced ratio | hot ratio |
empty ratio | balanced e2e ratio |
|---|---:|---:|---:|---:|---:|---:|
| 1 | 0.0251 | 0.0350 | 1.394 | 1.418 | 1.413 | 1.260 |
| 2 | 0.0374 | 0.0526 | 1.408 | 1.426 | 1.479 | 1.343 |
| 4 | 0.0602 | 0.0752 | 1.250 | 1.324 | 1.399 | 1.215 |
| 8 | 0.1045 | 0.1318 | 1.262 | 1.290 | 1.627 | 1.245 |
| 16 | 0.1821 | 0.2193 | 1.204 | 1.225 | 1.757 | 1.195 |
| 128 | 0.6140 | 0.6770 | 1.103 | 1.102 | 3.919 | 1.097 |
| 256 | 0.6319 | 0.6922 | 1.095 | 1.093 | 2.867 | 1.089 |
| 512 | 0.6584 | 0.7161 | 1.088 | 1.098 | 3.317 | 1.082 |
| 1024 | 0.7138 | 0.7826 | 1.096 | 1.083 | 2.491 | 1.093 |
| 2048 | 0.8058 | 0.8820 | 1.094 | 1.076 | 1.464 | 1.093 |
| 4096 | 0.9142 | 1.0981 | 1.201 | 1.186 | 1.243 | 1.197 |

tp8 graph: 33 rows, geomean 1.406, min 1.076 (T=2048 hot), rows <= 1.0:
0; e2e min 1.075, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.408, min 1.078 (T=2048 hot), rows <= 1.0:
0; e2e min 1.076, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.398, min 1.073 (T=2048 hot), rows <= 1.0:
0; e2e min 1.071, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.401, min 1.075 (T=2048 hot), rows <= 1.0:
0; e2e min 1.075, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.399, min 1.077 (T=2048 hot), rows <= 1.0:
0; e2e min 1.076, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.396, min 1.073 (T=2048 hot), rows <= 1.0:
0; e2e min 1.071, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.400, min 1.076 (T=2048 hot), rows <= 1.0:
0; e2e min 1.075, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.399, min 1.077 (T=2048 hot), rows <= 1.0:
0; e2e min 1.074, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.397, min 1.074 (T=2048 hot), rows <= 1.0:
0; e2e min 1.072, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.403, min 1.076 (T=2048 hot), rows <= 1.0:
0; e2e min 1.074, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.396, min 1.073 (T=2048 hot), rows <= 1.0:
0; e2e min 1.070, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.283, min 1.027 (T=2048 hot), rows <= 1.0:
0; e2e min 1.070, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.290, min 1.027 (T=2048 hot), rows <= 1.0:
0; e2e min 1.067, e2e rows <= 1.0: 0

tp8 graph: 33 rows, geomean 1.248, min 1.028 (T=2048 hot), rows <= 1.0:
0; e2e min 1.068, e2e rows <= 1.0: 0



Optional long rows (`T = 8192..32768`, dense grouped-GEMM path, GPU
span, graph): EP=8 geomean 1.445 over 12 rows, TP=8 1.104 over 9;
six rows sit below 1.0 (EP=8 `T = 8192` balanced / hot 0.956 / 0.986 and
`T = 16384` balanced / hot 0.987 / 0.961; TP=8 `T = 8192`
balanced / hot 0.975 / 0.962), the dense-path node band documented in
the roofline section; the `T = 32768` rows run under the
board power cap (round 25).

EP=8 (rank 3):

| T | balanced cand ms | balanced TRT ms | balanced ratio | hot ratio |
empty ratio | remote-dom. ratio | balanced e2e ratio |
|---|---:|---:|---:|---:|---:|---:|---:|
| 8192 | 1.2169 | 1.1628 | 0.956 | 0.986 | 2.527 | 1.499 | 0.955 |
| 16384 | 2.3183 | 2.2888 | 0.987 | 0.961 | 3.411 | 1.055 | 0.987 |
| 32768 | 4.2625 | 4.7724 | 1.120 | 1.074 | 3.858 | 1.393 | 1.116 |

ep8 graph: 12 rows, geomean 1.439, min 0.956 (T=8192 balanced), rows <=
1.0: 4; e2e min 0.955, e2e rows <= 1.0: 4

ep8 graph: 12 rows, geomean 1.443, min 0.944 (T=8192 balanced), rows <=
1.0: 2; e2e min 0.944, e2e rows <= 1.0: 2

ep8 graph: 12 rows, geomean 1.444, min 0.968 (T=8192 balanced), rows <=
1.0: 3; e2e min 0.968, e2e rows <= 1.0: 2

ep8 graph: 12 rows, geomean 1.467, min 0.971 (T=8192 balanced), rows <=
1.0: 1; e2e min 0.973, e2e rows <= 1.0: 1

ep8 graph: 12 rows, geomean 1.448, min 0.954 (T=8192 balanced), rows <=
1.0: 4; e2e min 0.951, e2e rows <= 1.0: 4

ep8 graph: 12 rows, geomean 1.449, min 0.954 (T=8192 balanced), rows <=
1.0: 3; e2e min 0.954, e2e rows <= 1.0: 3

ep8 graph: 12 rows, geomean 1.455, min 0.954 (T=8192 balanced), rows <=
1.0: 2; e2e min 0.953, e2e rows <= 1.0: 2

ep8 graph: 12 rows, geomean 1.464, min 0.944 (T=8192 balanced), rows <=
1.0: 2; e2e min 0.944, e2e rows <= 1.0: 2

ep8 graph: 12 rows, geomean 1.384, min 0.790 (T=8192 balanced), rows <=
1.0: 3; e2e min 0.794, e2e rows <= 1.0: 3

ep8 graph: 12 rows, geomean 1.387, min 0.801 (T=8192 balanced), rows <=
1.0: 3; e2e min 0.804, e2e rows <= 1.0: 3

ep8 graph: 12 rows, geomean 1.391, min 0.792 (T=8192 balanced), rows <=
1.0: 5; e2e min 0.795, e2e rows <= 1.0: 5

ep8 graph: 12 rows, geomean 1.385, min 0.785 (T=8192 balanced), rows <=
1.0: 4; e2e min 0.786, e2e rows <= 1.0: 4

ep8 graph: 12 rows, geomean 1.398, min 0.797 (T=8192 balanced), rows <=
1.0: 3; e2e min 0.801, e2e rows <= 1.0: 3

ep8 graph: 12 rows, geomean 1.402, min 0.802 (T=8192 balanced), rows <=
1.0: 4; e2e min 0.806, e2e rows <= 1.0: 4


TP=8 (rank 0):

| T | balanced cand ms | balanced TRT ms | balanced ratio | hot ratio |
empty ratio | balanced e2e ratio |
|---|---:|---:|---:|---:|---:|---:|
| 8192 | 1.6680 | 1.6270 | 0.975 | 0.962 | 1.196 | 0.977 |
| 16384 | 3.1275 | 3.3078 | 1.058 | 1.132 | 1.181 | 1.057 |
| 32768 | 5.6043 | 6.6201 | 1.181 | 1.192 | 1.091 | 1.179 |

tp8 graph: 9 rows, geomean 1.104, min 0.962 (T=8192 hot), rows <= 1.0:
2; e2e min 0.962, e2e rows <= 1.0: 2

tp8 graph: 9 rows, geomean 1.107, min 0.967 (T=8192 balanced), rows <=
1.0: 2; e2e min 0.966, e2e rows <= 1.0: 2

tp8 graph: 9 rows, geomean 1.107, min 0.981 (T=8192 hot), rows <= 1.0:
2; e2e min 0.980, e2e rows <= 1.0: 2

tp8 graph: 9 rows, geomean 1.124, min 0.993 (T=8192 hot), rows <= 1.0:
2; e2e min 0.991, e2e rows <= 1.0: 2

tp8 graph: 9 rows, geomean 1.122, min 0.973 (T=8192 balanced), rows <=
1.0: 2; e2e min 0.973, e2e rows <= 1.0: 2

tp8 graph: 9 rows, geomean 1.111, min 0.968 (T=8192 hot), rows <= 1.0:
2; e2e min 0.967, e2e rows <= 1.0: 2

tp8 graph: 9 rows, geomean 1.095, min 0.972 (T=8192 hot), rows <= 1.0:
2; e2e min 0.970, e2e rows <= 1.0: 2

tp8 graph: 9 rows, geomean 1.068, min 0.963 (T=32768 empty), rows <=
1.0: 3; e2e min 0.963, e2e rows <= 1.0: 3

tp8 graph: 9 rows, geomean 1.078, min 0.984 (T=8192 hot), rows <= 1.0:
2; e2e min 0.983, e2e rows <= 1.0: 2

tp8 graph: 9 rows, geomean 1.041, min 0.976 (T=8192 balanced), rows <=
1.0: 3; e2e min 0.973, e2e rows <= 1.0: 3

tp8 graph: 9 rows, geomean 1.062, min 0.971 (T=8192 balanced), rows <=
1.0: 3; e2e min 0.969, e2e rows <= 1.0: 3

tp8 graph: 9 rows, geomean 1.077, min 0.964 (T=8192 hot), rows <= 1.0:
2; e2e min 0.961, e2e rows <= 1.0: 2

tp8 graph: 9 rows, geomean 1.052, min 0.966 (T=32768 empty), rows <=
1.0: 5; e2e min 0.965, e2e rows <= 1.0: 5

tp8 graph: 9 rows, geomean 1.071, min 0.969 (T=8192 hot), rows <= 1.0:
3; e2e min 0.967, e2e rows <= 1.0: 3


`flashinfer.fused_moe.cute_dsl.CuteDslMxfp4MoEWrapper` consumes native
packed E2M1
weights with UE8M0 group-32 scales, FP8 E4M3 activations with linear
UE8M0 scales,
precomputed **global** top-k expert ids and router weights, and writes a
combined
rank-local BF16 output. Key properties:

- **SiTU** (`ActivationType.Situ`): `gate_out = beta * tanh(gate/beta) *
sigmoid(gate)`,
`up_out = linear_beta * tanh(up/linear_beta)` (or `up` when
`linear_beta` is absent).
`beta` and optional `linear_beta` are **runtime** FP32 device tensors
(one value or one
per local expert); they are read at execution, never specialized into
compiled constants.
- **Explicit parallel layouts** selected from metadata, not tensor
shapes: expert parallel
(EP=8: 112 local experts per rank, global ids, non-local routes ignored)
and MoE tensor
parallel (TP=8: all 896 experts, a 384-wide intermediate shard per rank,
partial output
for a caller-managed all-reduce). Hybrid EP×TP is rejected with a clear
error.
- **Capability query** `mxfp4_moe_capability(...)` covering arch,
quantization, activation,
  dimensions, top-k, expert/parallel metadata and CUDA Graph support.
- **Caller-owned output and workspace**; `get_workspace_size(T)` needs
no CUDA allocation;
  workspace stays bounded for large prefill.
- `plan(...)` compiles, binds addresses and warms up **before** serving;
`run()` enqueues on
the caller's current stream with no host synchronization, device-to-host
metadata read,
allocation, JIT compilation or autotuning, and is CUDA-Graph capturable
for every
  integer `T` (validated for `T = 1..16` in both layouts).
- Decode/prefill variant selection is internal. Token counts up to 1024
in both layouts run
  **swap-AB grouped GEMMs**

(`flashinfer/fused_moe/cute_dsl/blackwell/blockscaled_swapab_grouped_gemm.py`:
expert
weights as the MMA-M operand, 8/16/32-row groups of routed rows as MMA-N
chosen per layout
and token count, in-kernel row gather by configurable cp.async gather
warps, tile-major weight
streaming, SiTU + MXFP8 requantization epilogue for GEMM1 and a
barrier-free
`red.global.add.bf16x2` finalize epilogue for GEMM2, or a two-stage
finalize on the 384-wide
shard). From T=1025 to T=2048 the MoE-TP shard runs a **hybrid form**:
`moe_sort` groups the
permuted rows in 128-row tiles, a single-block dispatch kernel
(`csrc/moe_swapab_dispatch.cu`,
~3 µs, graph-capturable, PDL-aware) lists the occupied 64-row halves,
the swap-AB GEMM1 runs only
those halves and writes its MXFP8 scales directly in the tcgen05
block-scaled layout, and GEMM2 is
the dense contiguous grouped GEMM with the bulk-reduce finalize into the
zero-filled output (no
permuted partial rows, no finalize gather). The hybrid form's GEMM1
tiles are **mixed per sort group**
(`SWAPAB_HYBRID_DENSE_MIN_ROWS`, default 64): the dispatch kernel lists
the 128-row groups with more than 64
valid rows separately and the dense gather GEMM1 runs exactly those
groups through a compacted work list
(`tile_idx_to_row_group`: scheduler slot → sort group; expert, row
limit, gathered rows, output rows and
block-scaled output scales follow the group), while the swap-AB GEMM1
keeps the sub-tiles of the partially
filled groups; both write one MXFP8 row layout and GEMM2 is unchanged. A
full group streams its expert's
weight tile once instead of once per 64-row half and pads nothing.
Same-GPU B300 medians, MoE-TP rank 0:
`empty` routing T=2048 414 → 295 µs (GEMM1 249 → 127 µs dense + 4 µs for
the empty swap list), T=1536
326 → 222 µs; `hot` 850 → 816 µs and 816 → 787 µs; `balanced` (36 rows
per expert, no full group) 828 → 820 µs
and 792 → 795 µs, within the run-to-run band: it pays only the
dense-GEMM1 launch that finds an empty list, 3 µs.
From `T = 16` up the swap-AB GEMM2 of the MoE-TP shard (K = 384) runs
**two weight M-tiles per work item** with
128-wide (4 K-block) stages (`SWAPAB_TP_MGROUP2` /
`SWAPAB_TP_MGROUP2_MIN_TOKENS`, defaults 2 / 16): the token stage
is fetched once for both tiles and the short K loop keeps two tiles in
flight. Same-GPU B300 medians against one tile
per item: every MoE-TP row from `T = 16` up is faster (balanced/hot
−0.7..−6.6 %, `empty` −2..−7.3 %: T=16 balanced
199 → 186 µs, T=512 empty 211 → 199 µs, T=1024 empty 388 → 360 µs);
below `T = 16` the one-expert `empty` rows would
lose 0.2–0.8 µs (56 weight tiles become 28 items, halving the CTAs that
stream them) and the 3072-wide expert-parallel
shard loses 7–11 % on its 24–40 µs rows, so both keep one tile per item.
The mixed schedule is also available **below
the hybrid cap as an opt-in** (`SWAPAB_MIXED=1`: 128-row sort groups, a
third dispatch list of every occupied sub-tile
for the swap-AB GEMM2, which then reads the block-scaled scale layout
the dense tiles write, and a device-side
wide-fraction rule `SWAPAB_MIXED_WIDE_PERMILLE` so only concentrated
routings take dense tiles): MoE-TP `empty` rows
T=128/256/512/1024 run 145 → 94, 171 → 103, 211 → 152, 388 → 247 µs
(0.60–0.72×), but balanced/hot rows pay 1–2 % for
the dense-GEMM1 launch that finds an empty list and the 128-row GEMM2
groups (the fused routing kernel emits the lists
itself, so no dispatch launch remains), so it is off by default. Larger
token counts (and the expert-parallel rank above
T=1024) use the dense grouped GEMMs; their tcgen05 tile, cluster shape
and GEMM2 N-width come from per-shard, B300-measured
tactic tables keyed by token count (`B300_SITU_DENSE_TACTIC_TABLE_WIDE`
for the 3072-wide expert-parallel intermediate,
`..._NARROW` for the 384-wide MoE-TP shard: a cluster-2 256-wide GEMM2
for `T` in (4096, 7168], the two-CTA
(`cta_group::2`) M256 GEMM1 with the two-CTA 256-wide GEMM2 for `T` in
(7168, 14336], the 192-wide GEMM2 elsewhere).
Above `T = 7168` the MoE-TP shard chooses its dense M tile **on the
device** (`MXFP4_DENSE_DUAL_TILE`, default on for shards
up to 512 columns): the routing kernel pads every local expert to the
128- and to the 256-row tile, takes the two-CTA M256
tile when its padded total is within 1.10× of the M128 one (measured
break-even between 1.0 and 1.137), writes the
128-granularity tile list, which is always valid, plus the
256-granularity list and one active tile count per variant, and
both grouped GEMMs are launched once per variant on the same permuted
rows and output; the variant the routing did not
choose reads a zero count and exits (2.6–3.9 µs per launch). The choice
replays inside a captured graph. On the
expert-parallel rank the rule is opt-in (`dense_dual_tile=True`): its
two unchosen launches (≈8 µs with gaps) are 1–4 % of
that rank's 86–160 µs `empty` rows, which must not lose to the
single-tile plan; where enabled it takes EP=8 `T = 8192`
balanced/hot down 17/14 % and `T = 16384` remote-dominated down 16 %
(same GPU, interleaved arms).
  Every streamed weight load carries an L2 `EVICT_FIRST` TMA hint
where it measured faster (dense GEMMs always; swap-AB GEMMs for decode,
the MoE-TP shard and
EP ranks from T=256). A fused routing kernel (histogram, permutation,
scale, output clear)
serves `T * top_k <= 4096`; above that one conversion + output-clear
kernel precedes the
  native `moe_sort`.
- **Deferred finalize** (`plan(..., do_finalize=False)`): the deferred
output form from the
issue — rank-local GEMM2 rows in permuted order, the router weights and
the
assignment-to-row map (`plan.expanded_idx_to_permuted_idx`, `-1` for
non-local routes),
mirroring `trtllm_fp4_block_scale_routed_moe(do_finalize=False)`.
`get_deferred_output_rows(T)`
sizes the caller-owned row buffer, `get_workspace_size(T,
do_finalize=False)` the workspace,
and `mxfp4_moe_capability(..., do_finalize=False).deferred_output`
reports support.
- Weights are rearranged losslessly at load time
(`prepare_cute_dsl_mxfp4_weights`) and
are never converted to NVFP4; EP/TP slicing helpers produce rank shards.

Layouts, scale encoding, workspace and persistent memory, prefill
slicing, the
compiled/executed kernel counts, and a B300 roofline section (measured
HBM / tcgen05 / launch-gap floors per row,
the weight-streaming ramp, and which gaps are structural) are documented
in `docs/mxfp4_situ_moe.rst`.

<details>
<summary><b>Optimization rounds 6–25 on B300 (measured history; kernels
unchanged since round 22)</b></summary>

### Round 6: programmatic dependent launch on the swap-AB kernel chain

The fused routing kernel triggers its dependents at entry and every
swap-AB GEMM executes
`griddepcontrol.wait` after its prologue (TMEM allocation, barrier
initialisation, descriptor
prefetch) and before its first read of a routing output, so each GEMM's
launch latency and
prologue overlap the previous kernel. The swap plan launches its chain
with the PDL attribute
regardless of the caller's `enable_pdl` (`SWAPAB_PDL=0` restores plain
launches); the first
launch of the op is unchanged, and SiTU decode with `enable_pdl=True`
now takes the swap-AB
path. Output is bitwise identical (same relative-L2 error per row).

Why this and not more CTAs per tile: per-CTA `%globaltimer` stamps
inside the swap GEMMs show
all 148 CTAs starting within 0.2 us, a 1.2-1.5 us prologue, a K loop at
0.25 us per K=256 stage
(the MMA warp's issue rate: 8 `kind::f8f6f4` MMAs + 2 `tcgen05.cp` +
commit per stage; removing
the token-row loads, the TMEM epilogue traffic, or doubling the stages
in flight changes it by
<1 us), and ~3 us of each kernel outside any CTA (launch latency +
drain). Split-K over the
weight tiles (two implementations) was measured slower or equal; PDL
removes the part that is
launch latency.

Decode rows, graph mode, B300 (GPU span, since summed kernel durations
double-count the overlap):

EP=8 rank 3 (GPU-span ratios trtllm-gen ÷ candidate, graph mode;
balanced candidate/TRT in ms):

| T | balanced cand ms | balanced TRT ms | balanced ratio | hot ratio |
empty ratio | remote-dom. ratio | balanced e2e ratio |
|---|---:|---:|---:|---:|---:|---:|---:|
| 1 | 0.0250 | 0.0339 | 1.355 | 1.232 | 1.226 | 1.232 | 1.281 |
| 2 | 0.0399 | 0.0518 | 1.299 | 1.224 | 1.225 | 1.340 | 1.243 |
| 4 | 0.0591 | 0.0740 | 1.254 | 1.236 | 1.247 | 1.314 | 1.216 |
| 8 | 0.1026 | 0.1242 | 1.210 | 1.510 | 1.526 | 1.363 | 1.201 |
| 16 | 0.1829 | 0.2040 | 1.115 | 1.499 | 1.497 | 1.220 | 1.118 |

TP=8 rank 0 (GPU-span ratios trtllm-gen ÷ candidate, graph mode;
balanced candidate/TRT in ms):

| T | balanced cand ms | balanced TRT ms | balanced ratio | hot ratio |
empty ratio | balanced e2e ratio |
|---|---:|---:|---:|---:|---:|---:|
| 1 | 0.0253 | 0.0346 | 1.365 | 1.380 | 1.365 | 1.266 |
| 2 | 0.0399 | 0.0519 | 1.302 | 1.329 | 1.522 | 1.268 |
| 4 | 0.0606 | 0.0760 | 1.254 | 1.283 | 1.401 | 1.223 |
| 8 | 0.1065 | 0.1324 | 1.243 | 1.303 | 1.676 | 1.233 |
| 16 | 0.1846 | 0.2182 | 1.182 | 1.220 | 1.605 | 1.173 |


Full tables (both metrics, both layouts) and the roofline subsection are
in `docs/mxfp4_situ_moe.rst`.

### Round 7: split form for concentrated routings, fused routing to
16384 routes

Swap-AB path of the MoE-TP shard, T = 128..1024: the fused routing
kernel lays the local experts holding
more than 64 rows out in 128-row groups behind the policy-tile groups of
the other experts, but only when
those experts together hold at least 25 % of the local rows
(`SWAPAB_SPLIT_MIN_ROWS`,
`SWAPAB_SPLIT_MIN_PERMILLE`), so balanced and hot routings keep the
default layout. The wide groups run
first in the PDL chain on the dense gather GEMM1 (128x128 tile up to
T=512 — at these row counts the
narrower N tile fills more SMs, T=128 empty 56.9 vs 63.6 us — and
128x256 at T=1024; block-scaled output
scales) and on the swap GEMM2 at `n_tile = 128` reading those blocked
scales into the two-stage finalize;
both wide kernels signal their programmatic dependents at entry, so
without wide experts they cost the two
dependency hops (~2 us each) and nothing else. The swap GEMM1 at `n_tile
= 128` measured 2.3x slower than
the dense tile on the same groups (65 vs 28 us at T=128: one 128-row
activation gather per K stage against
the dense kernel's TMA-fed pipeline) and is not used. Expert-parallel
ranks keep the default form
(`SWAPAB_SPLIT_EP=1` opts in): there the two extra launches cost the
decode-class `empty` rows 21-27 %
(27 -> 34 us) for one 2.9 % gain (hot T=512), measured.

Fused routing kernel: 8192 routes on any rank (T <= 512 for top-16),
16384 on ranks with at most 128
local experts and on the shard where the split form runs. The histogram
issues eight routes per thread
before ranking any of them (one block's 32 warps are latency-bound
otherwise; the plain loop stays for up
to one route per thread), the per-route scratch is int16, and in the
16384-route variant layouts above
8192 rows stage the inverse permutation in shared memory and copy it out
coalesced: scattered 4-byte
stores cost one L1 sector each (13.6 -> 8.7 us of the T=1024 kernel on
the shard, per-phase `%globaltimer`
stamps). Output bitwise identical (same relative-L2 per row).

MoE-TP rank 0, graph mode, GPU span, B300 (same node for the three
candidate columns' floors; 3a0b1340 =
phase-2 baseline, round 6 = previous revision):

| T | routing | 3a0b1340 us | round 6 us | round 7 us | r7/3a0b |
trtllm-gen us | trtllm/r7 |
|---:|---|---:|---:|---:|---:|---:|---:|
| 128 | balanced | 618.2 | 612.2 | 617.0 | 0.998 | 681.0 | 1.104 |
| 128 | hot | 621.1 | 613.7 | 618.1 | 0.995 | 685.0 | 1.108 |
| 128 | empty | 146.0 | 140.4 | 56.7 | 0.388 | 183.6 | 3.238 |
| 256 | balanced | 640.4 | 632.2 | 638.2 | 0.997 | 697.4 | 1.093 |
| 256 | hot | 643.0 | 632.8 | 639.1 | 0.994 | 699.7 | 1.095 |
| 256 | empty | 172.6 | 165.8 | 82.4 | 0.478 | 194.1 | 2.354 |
| 512 | balanced | 671.0 | 658.0 | 662.6 | 0.987 | 722.5 | 1.090 |
| 512 | hot | 670.8 | 660.8 | 664.8 | 0.991 | 728.3 | 1.096 |
| 512 | empty | 213.8 | 198.7 | 134.3 | 0.628 | 322.8 | 2.403 |
| 1024 | balanced | 722.5 | 714.9 | 723.5 | 1.001 | 786.3 | 1.087 |
| 1024 | hot | 731.1 | 723.4 | 732.7 | 1.002 | 787.6 | 1.075 |
| 1024 | empty | 391.1 | 360.6 | 235.9 | 0.603 | 401.1 | 1.701 |

EP=8 rank 3 (fused routing to 16384 routes; the split form is off
there):

| T | routing | 3a0b1340 us | round 6 us | round 7 us | r7/3a0b |
trtllm/r7 |
|---:|---|---:|---:|---:|---:|---:|
| 512 | balanced | 620.1 | 619.2 | 615.4 | 0.992 | 1.135 |
| 512 | hot | 681.5 | 682.3 | 676.1 | 0.992 | 1.075 |
| 512 | empty | 37.2 | 38.5 | 32.8 | 0.882 | 1.480 |
| 512 | remote_dominated | 617.7 | 615.6 | 611.3 | 0.990 | 1.154 |
| 1024 | balanced | 629.8 | 628.0 | 627.5 | 0.996 | 1.219 |
| 1024 | hot | 753.5 | 753.0 | 752.4 | 0.999 | 1.112 |
| 1024 | empty | 38.7 | 40.3 | 38.7 | 1.001 | 1.408 |
| 1024 | remote_dominated | 622.5 | 623.4 | 621.8 | 0.999 | 1.235 |

Closed by measurement this round: swap GEMM1 at `n_tile = 128` (2.3x
slower than the dense tile);
the split form on expert-parallel ranks (+21-27 % on the decode-class
rows); the 16384-route fused
routing on the shard outside the split form (15 us vs 16 us for the
conversion kernel plus `moe_sort`,
within noise, so the sort path stays); early PDL trigger / launch order
of the wide kernels (each extra
kernel in the chain costs ~2-2.5 us regardless of trigger placement).
Remaining structure of the shard's
`empty` rows at T=128 (57 us against an 11 us floor): routing 6.4 us,
dense GEMM1 23.9 us (16 experts x
56 M-tiles = 896 work items of K=7168 on 148 SMs, 6 waves at ~4 us),
wide GEMM2 35.9 us (896 items of
K=384 at `n_tile = 128`, bound by the per-item activation gather and
epilogue; the dense finalize-fusion
GEMM2 runs the same rows in 15.9 us but writes token rows, so the
two-stage finalize would have to
accumulate — the next lever, worth ~20 us), two empty narrow launches
(5.7 + 3.1 us) and the finalize
(7.2 us). Full tables (both metrics, both layouts) and the roofline
subsection are in
`docs/mxfp4_situ_moe.rst`.

### Round 8: dense finalize-fusion GEMM2 for the split form's wide
groups, reachable floors per row

Split form of the MoE-TP shard (T = 128..1024): the wide 128-row groups'
GEMM2 now runs on the dense
finalize-fusion kernel
(`Sm100BlockScaledContiguousGroupedGemmFinalizeFusionKernel`), which
reduce-adds the
route-weighted rows into the zero-filled output (one 128 x N tile per
weight tile, TMA-fed), instead of the
swap GEMM2 at `n_tile = 128` that was bound by its per-item 128-row
activation gather. The kernel gets an
optional compacted work list (`tile_idx_to_row_group`: scheduler slot i
runs the 128-row group list[i], whose
expert and row limit are read at that group index) and
`pdl_trigger_early`. The two-stage finalize then adds
the narrow groups' rows on top: it reads the output row first (only when
the routing produced wide groups,
a device-side count), skips the slots whose permuted row lies in the
wide region (the first 128-multiple past
the narrow groups, from the device-side group count) and exits at once
when there is no narrow group, so a
captured graph follows the routing. `SWAPAB_SPLIT_DENSE_GEMM2=0`
restores the swap wide GEMM2. The 16 wide
routes of a token are summed by the kernel's BF16 reduce-adds (the class
the default fused finalize uses below
T=17): relative L2 error of the `empty` rows 2.4e-3 -> 5.3e-3 against
the FP64 reference, inside the unchanged
tolerances.

Same-GPU interleaved A/B (B300, TP8 rank 0, graph, GPU span; swap wide
GEMM2 -> dense): `empty` T=128 57.5 ->
47.4 us, T=256 83.1 -> 68.6, T=512 134.8 -> 100.2, T=1024 236.4 -> 169.1
(0.82 / 0.83 / 0.74 / 0.72x); `balanced`
and `hot` 0.996-1.003x (the routing kernel's output clear). GEMM2 N tile
128 / 192 / 256 within 1.6 % (tactic
default kept).

MoE-TP rank 0, graph mode, GPU span, B300 (same node for the candidate
columns' floors; 3a0b1340 = phase-2
baseline, round 7 = previous revision):

| T | routing | 3a0b1340 us | round 7 us | round 8 us | r8/3a0b |
trtllm-gen us | trtllm/r8 |
|---:|---|---:|---:|---:|---:|---:|---:|
| 128 | balanced | 618.2 | 617.0 | 611.5 | 0.989 | 676.7 | 1.107 |
| 128 | hot | 621.1 | 618.1 | 614.4 | 0.989 | 678.7 | 1.105 |
| 128 | empty | 146.0 | 56.7 | 47.7 | 0.326 | 196.0 | 4.111 |
| 256 | balanced | 640.4 | 638.2 | 629.7 | 0.983 | 697.7 | 1.108 |
| 256 | hot | 643.0 | 639.1 | 629.5 | 0.979 | 699.0 | 1.110 |
| 256 | empty | 172.6 | 82.4 | 68.5 | 0.397 | 193.7 | 2.827 |
| 512 | balanced | 671.0 | 662.6 | 662.7 | 0.988 | 723.0 | 1.091 |
| 512 | hot | 670.8 | 664.8 | 662.0 | 0.987 | 726.3 | 1.097 |
| 512 | empty | 213.8 | 134.3 | 100.2 | 0.469 | 320.1 | 3.193 |
| 1024 | balanced | 722.5 | 723.5 | 719.5 | 0.996 | 788.6 | 1.096 |
| 1024 | hot | 731.1 | 732.7 | 728.0 | 0.996 | 787.0 | 1.081 |
| 1024 | empty | 391.1 | 235.9 | 169.5 | 0.433 | 403.0 | 2.377 |

EP=8 rank 3 (the split form stays off there; the dense wide GEMM2 also
applies when `SWAPAB_SPLIT_EP=1`; the 3a0b1340 and
round-7 columns come from other nodes of the same pool, so the per-row
invariant against 3a0b1340 is settled by the
same-GPU pairs listed under the validation section, not by this table):

| T | routing | 3a0b1340 us | round 7 us | round 8 us | r8/3a0b |
trtllm/r8 |
|---:|---|---:|---:|---:|---:|---:|
| 128 | balanced | 611.4 | 609.0 | 593.3 | 0.970 | 1.037 |
| 128 | hot | 623.4 | 620.6 | 609.3 | 0.977 | 1.045 |
| 128 | empty | 29.0 | 27.5 | 27.6 | 0.950 | 1.383 |
| 128 | remote_dominated | 605.0 | 601.2 | 588.8 | 0.973 | 1.037 |
| 512 | balanced | 620.1 | 615.4 | 613.2 | 0.989 | 1.139 |
| 512 | hot | 681.5 | 676.1 | 676.3 | 0.992 | 1.076 |
| 512 | empty | 37.2 | 32.8 | 32.8 | 0.882 | 1.494 |
| 512 | remote_dominated | 617.7 | 611.3 | 609.4 | 0.987 | 1.155 |
| 1024 | balanced | 629.8 | 627.5 | 627.2 | 0.996 | 1.217 |
| 1024 | hot | 753.5 | 752.4 | 750.6 | 0.996 | 1.118 |
| 1024 | empty | 38.7 | 38.7 | 38.6 | 0.997 | 1.431 |
| 1024 | remote_dominated | 622.5 | 621.8 | 620.8 | 0.997 | 1.230 |

Closed by measurement this round: the wide chain on a second stream
(`SWAPAB_SPLIT_SIDE_STREAM=1`, fork after
the routing kernel, join before the finalize): shard `empty` rows -3..-7
%, but `balanced`/`hot` T=512/1024
+1.0..1.4 % (the wide kernels' persistent CTAs contend with the narrow
GEMM1's start) -> stays opt-in. The
split form on the expert-parallel rank with the dense wide GEMM2 and the
side stream (`SWAPAB_SPLIT_EP=1`):
`hot` T=128/256/512/1024 610 -> 597, 628 -> 609, 677 -> 637, 753 -> 673
us (-2..-11 %) but `balanced`
+0.6..1.9 % and `empty` 27 -> 37, 30 -> 46, 33 -> 47, 39 -> 53 us
(+13..37 %: the empty wide kernels still pay
their launches, prologues and dependency hops) -> stays opt-in; the
lever it leaves is a cheap no-work exit
for the wide kernels. GEMM2 N tile of the wide groups (128/192/256,
within 1.6 %).

Remaining structure of the shard's `empty` row at T=128 (47 us against
an 11 us floor, 29 us reachable):
routing 6.6 us, dense GEMM1 22.9 us (96 items of 128 x 128 x K=7168 on
96 SMs: 10 us of MMA issue at N=128 plus
a 0.9 MB activation gather and 458 KB of weights per item that the
kernel does not fully overlap), and 17.9 us
of span for the dense GEMM2 plus the tail (two empty narrow launches and
the finalize exit; the GEMM2's own
31.9 us of duration overlaps the GEMM1 under the early trigger).

Reachable floor per row: the roofline subsection of
`docs/mxfp4_situ_moe.rst` now carries, next to the Goal
floor of every row, the reachable floor of the best kernel form from the
same node's constants (streaming ramp
2.4 us + bytes / 5.2 TB/s up to 70 MB and the 6.92 TB/s HBM rate beyond;
padded FLOPs at the shape-specific
tcgen05 peak; reduce-add bytes at 3.4 TB/s; per-SM MMA issue at max(64,
0.695 N) cycles per 128 x N x 32 MMA
plus prologue and epilogue; L2 re-read at 8.9 TB/s for further swap row
groups; one launch gap per dependent
kernel), minimized over the swap, dense 128 x 256, dense 128 x 128 and
dense 256 x 256 forms. Against the Goal floor (max of bytes, FLOPs and
launch terms) 10 of the 56 EP=8 rows and 2 of the 42 MoE-TP rows sit
within 1.10x (geomean candidate/floor 2.08 and 1.88); against the
reachable floor 29 of 56 and 21 of 42 rows (geomean 1.20 and 1.15). The
rows still above 1.10x of their reachable floor: on the expert-parallel
rank `hot` T=16, `empty` T=128..2048 (routing kernel 4.4 -> 12.7 us from
T=128 to 4096 on a 27-50 us chain), every routing at T=2048/4096 and
every long row T>=8192; on the shard `balanced` T=2, `empty` T=16..2048,
`balanced`/`hot` T=512..2048 and every long row. Each is listed with its
binding term in the docs tables.

### Round 9: where the dense-path rows stop, measured (no kernel change)

FlashInfer docs commit follows the round-8 code (`8433ea47`, unchanged,
still the pinned revision). This round measures
why the dense gather GEMM1 / finalize GEMM2 rows (EP=8 `T >= 2048`, both
layouts' long rows) sit 1.4-2.8x above the
Goal floor, closes the remaining levers by same-GPU paired measurement
(FP64-checked, relative L2 unchanged), and adds
the resulting structural term to the reachable-floor model in
`docs/mxfp4_situ_moe.rst`.

Utilisation (Nsight Compute, real clocks, cache flushed, EP=8 `T = 2048`
balanced): dense GEMM1 491 us at 70 % of the
DRAM peak (5.39 TB/s), dense GEMM2 272 us at 67 %; the 32-row swap GEMM1
/ GEMM2 on the same 2.6 / 1.3 GB of weights
(`T = 512`) reach 87 % / 81 % (393 / 213 us). No other unit is saturated
(SM 47-75 %, L2 44-58 %, 2-2.7 active warps
per scheduler, one CTA per SM, long-scoreboard stalls dominant). The
dense kernels are latency-bound on their operand
ring: both run 4 A/B stages (GEMM1 50688 B per stage = 16 KB
LDGSTS-gathered FP8 A + 32 KB TMA FP4 B in 8-bit
containers + scales; GEMM2 42496 B), and capping the ring at 3 and 2
stages gives GEMM1 509 / 572 / 747 us and GEMM2
274 / 314 / 436 us at 4 / 3 / 2 stages: `a + L / S` with `L = 0.93 us`
per K-stage round trip in both kernels and a
fill term `a` of 0.27 / 0.16 us per stage. The same `L` with the swap
kernels' own fill terms (0.19 / 0.12 us, 5 / 11
stages) reproduces their `T = 512` times within 3 %. The DRAM-bandwidth
time of a dense stage is 0.36 us and would need
about ten stages in flight.

Closed by measurement (B300, same GPU, paired):

* a fifth stage: a single-stage epilogue frees 8 KB and GEMM1 stays at 4
stages (`(232448 - 1024 - 8192) / 50688 = 4.4`);
the 128 x 128 GEMM1 tile keeps the bytes in flight (5 x 34 KB) and is
1-4 % slower on every `T = 2048` / `4096` row
(GEMM1 510 -> 524 balanced, 547 -> 580 hot); the 192-wide GEMM2 tile is
already the default;
* software L2 prefetch of the operand rows ahead of the ring: per-line
`prefetch.global.L2` issued by the TMA warp 4 / 8
stages ahead makes GEMM1 +6-8 % and GEMM2 +11-13 % slower on every row
(EP=8 `T = 2048` 510 -> 550 / 541 us, 275 ->
304 / 311; `T = 8192` 904 -> 990 / 981, 540 -> 580 / 572); bulk
`cp.async.bulk.prefetch.L2` of eight stages per row
roughly doubles both kernels (510 -> 1030 us, 275 -> 733 us), because it
moves the same bytes through the same
  per-SM async-copy unit whose fill the `a` term measures;
* the two-stage token-major finalize (`MXFP4_DENSE_TWO_STAGE=1`) on
every long row of both layouts: EP=8 `T = 8192` /
`16384` 1487 -> 1653 and 2210 -> 2555 us, MoE-TP 1710 -> 1908 and 3075
-> 3496 us; on the shard the plain-store GEMM2
alone costs 765 of the fused 879 us, so the reduce-add is 13 % of that
kernel and the rest is the per-tile ring of a
  K = 384 GEMM with three K-stages per tile;
* the reduce path on its own (16 x T expanded rows into T token rows,
7168 BF16 columns): the epilogue's
`cp.reduce.async.bulk` of scattered 384 / 512 B row segments runs at
2.6-2.7 TB/s of payload at `T = 8192` and 2.4
TB/s at `T = 16384`, within 3-10 % of a plain scattered bulk store of
the same segments; token-sorted rows 3.3 TB/s;
a token-major reduction reads at 4.6 TB/s but needs the expanded rows
written first (the two-stage form above);
* the host tile policy at EP=8 `T = 2048`: the 64-row hybrid form wins
balanced / remote-dominated by 5 / 7.5 % and
ties hot but loses `empty` by 15 % (72 vs 63 us: routing 20 vs 16 us and
both GEMM1 kernels run); the 32-row swap form
wins `empty` / remote-dominated by 30 / 21 % but loses balanced / hot by
24 / 42 %. No per-T policy keeps every
  routing within 1 % of the previous revision, so the dense form stays;
* the shard's hybrid GEMM1 is not slower than the dense one at `T =
2048` (478 vs 492 us, 72 vs 70 % DRAM); at
  `T = 4096` the hybrid form has no narrow group and is the dense pair.

Reachable floors with the load-ring term (`prologue 2.2 us + ceil(tiles
/ 148) x (K / K_stage) x (fill + 0.93 us / S)`,
tables in the docs): 45 of the 56 EP=8 rows and 34 of the 42 MoE-TP rows
sit within 1.10x of their reachable floor
(geometric mean candidate / reachable 1.04 on both layouts, was 1.20 /
1.15 without the term; against the Goal floor
unchanged: 10 / 56 and 2 / 42, geomean 2.08 / 1.88). Rows still above
1.10x of the reachable floor, each listed with its
binding term in the docs: EP=8 `empty` from `T = 256` (30-132 us chains
bound by the routing kernel and the swap GEMM1's
per-tile latency), EP=8 `T = 2048` remote-dominated (1.31, the policy
conflict above), `T = 4096` balanced (1.13),
`T = 8192` remote-dominated (1.14), `T = 32768` balanced (1.15); MoE-TP
`T = 256` empty (1.29), `T = 1024` / `2048`
balanced and hot (1.16-1.34: 32-row swap groups re-read each expert's
weights from L2 once per group), `T = 16384`
balanced (1.12), `T = 32768` balanced / empty (1.23 / 1.18).

Kernel and bench tables are unchanged from round 8 (no code change); the
contract stays pinned to `8433ea47`.

### Round 10: one fill-rate constant for every kernel form, chains of
the open rows (no kernel change)

FlashInfer docs commit follows the round-9 docs on the unchanged code
(`8433ea47`, still the pinned revision). The swap
kernels now print their operand rings instead of being fitted: GEMM1
with the (128, 32, 128) tiler runs 9 stages of
21504 B (12 would fit; the kernel caps at 9), the 64-row tiler 8 stages
of 25600 B, the split form's GEMM1 5 of 38400 B,
the swap GEMM2 3 stages of 64512 B (K = 384 per stage). Capping them on
the same GPU (paired, FP64-checked): 32-row GEMM1
402 / 675 / 943 us at 9 / 3 / 2 stages (EP=8 `T = 512`), 404 / 683 / 953
on the shard at `T = 1024`, 64-row GEMM1 475 /
725 / 1008 at 8 / 3 / 2 (shard `T = 2048`). At shallow depth the swap
kernels follow the dense kernels' latency line
(`a + 0.93 us / S`), but at their printed depth they sit above it (the
fit predicts 323 / 371 us), so a second bound binds:
stage bytes per kernel time is 101 / 108 GB/s per SM for the dense GEMM1
/ GEMM2 and 111 / 112 / 106 GB/s for the
32-row swap GEMM1, the 64-row one and the swap GEMM2. Every form fills
its shared memory at about 110 GB/s per SM (16 TB/s
over 148 SMs), and a kernel's DRAM utilisation is its DRAM bytes over
its shared-memory bytes at that rate (87 % for the
32-row swap GEMM1, 70 / 67 % for the dense kernels whose FP4 operand
sits in 8-bit containers). The shard's dense finalize
GEMM2 (K = 384, 6 stages of 34304 B) is insensitive to depth (320 / 320
/ 386 us at 6 / 3 / 2 stages, `T = 2048`): per-tile
bound, 97 tiles per CTA x 3.3 us = 0.94 us of fill + ~2.4 us of
scattered 32 KB reduce epilogue.

The reachable-floor model replaces its four fitted fill terms by that
one constant with the printed stage sizes
(`prologue 2.2 us + ceil(tiles / 148) x (K / K_stage) x stage bytes /
(110 GB/s x 148 / min(tiles, 148)) + epilogue`):
38 of the 56 EP=8 rows and 36 of the 42 MoE-TP rows sit within 1.10x of
their reachable floor (geometric mean candidate /
reachable 1.09 / 1.03; the earlier fit over-credited the swap rows).
Against the bytes / FLOPs / launch floor unchanged: 10 / 56 and 2 / 42.

Rows above 1.10x of the reachable floor, measured kernel by kernel
(standalone launches, same GPU, FP64-checked):

* EP=8 `T = 2048` `empty` (one local expert, 42 rows): dense chain 54.4
us = routing 5.3 + `moe_sort` 10.4 + GEMM1 25.9 +
GEMM2 11.6 (+ hops); 64-row hybrid chain 70.1 us = 5.4 + 11.5 + dispatch
4.2 + swap GEMM1 23.5 + wide GEMM1 no-work exit
2.9 + GEMM2 13.4. The swap GEMM1 is no slower than the dense one on a
single 48-tile group (a 56-stage chain either way);
the hybrid costs its two extra launches and hops, so no form choice
keeps this row and its balanced routing both within
1 %. The same rule keeps EP=8 `T = 2048` / `4096` remote-dominated on
the dense form (hybrid measured 741 vs 798 and
  765 vs 816 us).
* MoE-TP `T = 256` `empty`: 67.6 us = routing 7.5 + dense wide GEMM1
33.6 (32 wide groups x 6 N tiles = 192 items on 148
SMs: two 56-stage chains) + dense wide GEMM2 34.9 (1792 items, 12 per
CTA x 3 stages + reduce epilogue) + narrow exits
6.7 + 2.9 + 2.2; `T = 512` `empty` 98.8 = 9.8 + 43.2 + 51.6 + 7.0 + 2.9
+ 3.2.
* Long rows: the first kernel (route conversion + output zero-fill)
takes 33.6-38.3 us at `T = 16384` and 64.9-86.8 us at
`T = 32768` on both layouts = `T x 7168 x 2 B` at 6.9-7.2 TB/s on the
`empty` rows (5.4-6.2 on the others) against the
6.91 TB/s measured fill bandwidth: at the DRAM bound. The fused
finalize's reduce-add needs the zero base (the
token-major alternative was measured slower in round 9). It is 41-49 %
of the EP=8 `empty` rows at `T = 16384` / `32768`
  and 1.3-3.2 % of the other routings.
* Decode-class rows: the fused routing kernel is a single CTA: 4.6 / 5.2
/ 7.0 / 12.7 us at EP=8 `T = 128` / `256` / `512`
/ `1024` (1024-8192 routes), 6.5-7.0 / 7.6-8.4 / 9.9-12.9 / 16.0-17.6 us
on the shard; 17-33 % of the EP=8 `empty` rows
(27.6-38.6 us), 9-14 % of the shard's (47.7-169.5 us), <= 2 % elsewhere.
Its `%globaltimer` phases at `T = 1024` put
5.3 us in the histogram (one CTA's shared-memory atomics over 8192
routes). A multi-CTA routing kernel is the open
lever for these rows; every other term of the `empty` chains is a
launch, a dependency hop or one 56-stage GEMM1 chain.

Kernel and bench tables are unchanged from round 8 (no code change); the
contract stays pinned to `8433ea47`.

### Round 11: thread-block cluster for the fused routing kernel

FlashInfer code commit `6224e108` (the new pinned revision); the
previous rows and forms are unchanged, only the fused
routing kernel (`T x top_k <= 8192 / 16384` routes: T <= 512 / 1024)
changes. Above one route per thread it now runs as a
cluster of `ceil(T x top_k / 1024)` CTAs (at most 8,
`MXFP4_FUSED_ROUTE_CLUSTER`): each CTA converts, histograms
(shared-memory atomics) and scatters its own chunk of routes; the
per-CTA expert counts are exchanged through the
`out_expert_counts` scratch (unused on this path) at one
`barrier.cluster` release / acquire; every CTA derives the same
group bases from the totals and CTA 0 alone writes the group tables,
work lists and totals (row = expert base + that
expert's rows in the lower-ranked chunks + rank in the own chunk). The
output zero-fill moves to a grid-stride loop of
16-byte stores on the CTAs after the sort cluster
(`MXFP4_FUSED_ROUTE_CLEAR_CTAS` = 120): clusters are scheduled as units,
so the one-word-per-thread grid of the single block cost 4-5 us in
cluster waves, and 4-byte stores from a 4-byte-aligned
pointer type another 6 us (both measured with `%globaltimer` phase
stamps before the final form). Decode rows (one route
per thread) keep the single block.

Measured (B300, same GPU, r34 vs previous revision alternating, 20
repeats, FP64-checked, identical relative L2):

* routing kernel EP=8 `T = 128 / 256 / 512 / 1024`: 4.5-4.8 / 4.8-5.0 /
5.3-5.4 / 6.3-6.8 us (was 4.6-4.9 / 4.9-5.4 / 7.0 /
12.8); MoE-TP shard: 6.1-6.6 / 6.5-6.8 / 6.8-7.5 / 8.4-9.2 us (was
6.6-7.1 / 7.6-8.5 / 9.9-12.3 / 16.1-17.6);
* rows (GPU span): EP=8 `empty` `T = 512 / 1024` 1.101x / 1.239x, shard
`empty` 1.034x / 1.049x, every other
`T = 128..1024` row 0.999-1.015x, decode rows `T = 1..16` 0.989-1.002x
(0.1 us less routing);
* phases at EP=8 `T = 1024` (stamps): histogram 1.8 us, count exchange
1.4, group bases 0.55, scatter 0.3, sort end 4.6-4.9
us, clear end 3.4-4.0 us; on the shard the group-table phase over 896
experts takes 1.9 us and the sort ends at 6.6-7.4
us. The kernel is now bound by its launch plus the histogram / exchange
/ group-table chain, not by the route count.

Bench (tree r34 = `6224e108`, B300, graph, GPU span, 30 paired CUPTI
repeats): EP=8 44/44 rows > 1 vs TRT-LLM Gen (geomean
1.304, min 1.013 at `T = 128` balanced), long rows 12 (geomean 1.382,
the pre-existing sub-1 dense rows `T = 8192`
balanced / hot and `T = 16384` remote-dominated); MoE-TP 33/33 > 1
(geomean 1.388, min 1.072 at `T = 2048` hot), long rows 9 (geomean
1.077; the pre-existing sub-1 `T = 8192` balanced / hot).
Rows of the bench that read more than 1 % slower than the previous
revision's bench (a different node) are the untouched
dense long rows and the `T = 1..256` rows whose kernels did not change;
their same-GPU pairs read 0.990-1.015x for the small rows; the dense
long rows pair 0.997-1.028x on the rank and 0.999-1.017x on the shard,
with `T = 32768` hot 0.981 in that four-arm pair and 1.015 (mean) /
1.045 (median) in a six-arm pair of 20 repeats, so inside the row's
run-to-run band.

Validation: small-geometry suite 200 passed, selection slice 175 passed,
deferred finalize 69 passed, all-local (896 local experts) 2 passed,
EP=8 rank sum 4 passed, TP=8 shard sum 3 passed + 1 OOM skip (hot `T =
512`, as in every round), TP=8 paired FP64 18 passed, TP=8 graph replay
`T = 1..16` 16 passed; compute-sanitizer synccheck + memcheck on the
36-row list of the previous rounds: 142 summaries, every one `ERROR
SUMMARY: 0 errors`.

Contract: the 45-row timed contract (EP=8 rank 3 and MoE-TP rank 0, T =
1..2048, uniform / spread / hot routings, graph-replay CUPTI medians,
isolated B300 node, 07:46-08:13 UTC) at `6224e108`: 91/91 shapes
correct, 45/45 timed rows > 1.0 vs trtllm-gen, geomean 1.2264, min
1.0107 (EP=8 T=128 uniform_spread); previous pin `8433ea47` 1.2214 / min
1.0111.

### Round 12: dependent-side weight prefetch in the swap-AB GEMM2

FlashInfer code commit `023e5080` (the new pinned revision); only the
plain routing -> GEMM1 -> GEMM2 chain changes
(decode rows and the expert-parallel rank's `T <= 1024` rows; split,
hybrid and mixed launches are untouched). GEMM1 now
triggers its programmatic dependent right after its own
`griddepcontrol.wait` -- the routing grid is complete by then --
and GEMM2 executes `griddepcontrol.wait` only in the warps that load its
row operand (GEMM1's output: the gather warps, plus
the TMA warp when the row tile is TMA-fed). Its scheduler reads the
routing tables and its TMA warp streams the weight
stages at once, so GEMM2's tile CTAs take the SMs that GEMM1's tile-less
CTAs leave and hold their weights before GEMM1
ends; the decode-class GEMM2 (short 4-block stages) takes 8-block stages
when the stage ring then covers the whole K
(K = 3072: 12 stages of 256), so the whole tile is resident. Every other
input of GEMM2 (tables, finalize metadata, the
routing kernel's output clear) was written by grids that completed
before GEMM1 started, which is what makes the partial
wait sound. `SWAPAB_DEP_PREFETCH=0` restores the previous chain.

Measured (B300, same GPU, r35 vs previous revision alternating, 20
repeats, FP64-checked, identical relative L2):

* EP=8 decode rows `T = 1..16`: hot / empty / remote-dominated
1.033-1.055x (22.4-23.3 -> 21.6-22.9 us), balanced
1.010-1.032x; MoE-TP decode 0.996-1.026x (its GEMM2 K = 384 already fits
one stage; only the early residency applies);
EP=8 `empty` `T = 128` 1.03x, `T = 256..1024` 1.01x; every other `T =
128..1024` row 0.997-1.007x; the shard's
  `T = 128..1024` rows run the split form and read 0.997-1.003x (noise).
* Per-kernel CUPTI start / end offsets of one graph replay (EP=8 `T = 1`
hot): before, routing 0-2.4 us, GEMM1 1.0-14.9,
GEMM2 13.5-22.3 (GEMM2 starts 1.4 us before GEMM1 ends, tail after GEMM1
7.4 us); after, GEMM2 starts at 3.8 us, GEMM1
ends 0.2 us later (15.1, the shared HBM stream) and GEMM2's tail is 6.8
us with half the tile in 128-wide stages and
~6 us with the whole tile resident. An 11 us head start on the weight
stream removes 1-1.4 us: what remains after GEMM1
is the row gather from GEMM1's output, the MMA-issue-bound loop (96
`kind::f8f6f4` MMAs of K = 32 at ~64 issue cycles,
~3.1 us; N = 8 leaves the tensor pipe idle), the epilogue and the drain.
GEMM1's own stream cannot start before the
routing kernel publishes the expert ids, so the same prefetch does not
apply to it.

Bench (tree r35 = `023e5080`, B300, graph, GPU span, 30 paired CUPTI
repeats): EP=8 44/44 rows > 1 vs TRT-LLM Gen by GPU span (geomean 1.331,
min 1.030 at `T = 128` balanced; previous revision 1.304 / 1.013), long
rows 12 (geomean 1.394; the pre-existing sub-1 dense rows `T = 8192`
balanced / hot and `T = 16384` balanced / hot / remote-dominated, which
pair 0.967-1.027x against the previous revision on the same GPU); MoE-TP
33/33 > 1 (geomean 1.396, min 1.073 at `T = 2048` hot; previous 1.388 /
1.072), long rows 9 (geomean 1.063; `T = 8192` balanced / hot and `T =
16384` balanced below one, dense path, pairs 0.993-1.005x); deferred
form EP=8 1.174 / MoE-TP 1.152 (previous 1.155 / 1.145). The summed
kernel durations of the plain chain now include GEMM2's wait (see the
note under the summary table): 18 EP=8 and 5 MoE-TP graph rows and the
three EP=8 eager `T = 128` rows read below one on that column while
every span and end-to-end ratio is above one.

Validation: small-geometry suite 200 passed, routing / split / decode
selection slice 175 passed, deferred finalize 69 passed, all-local (896
local experts) 2 passed, EP=8 rank sum 4 passed, TP=8 shard sum 3 passed
+ 1 skipped (hot T=512, fixture OOM, as in every round), TP=8 paired
FP64 18 passed, TP=8 graph replay `T = 1..16` 16 passed;
compute-sanitizer synccheck + memcheck on the same 36-row list, now with
the partial-wait GEMM2 and the trigger-after-wait GEMM1 under both
tools: 72 runs, 142 summaries, every one `ERROR SUMMARY: 0 errors`.

Contract: the 45-row timed contract (EP=8 rank 3 and MoE-TP rank 0, T =
1..2048, uniform / spread / hot routings, graph-replay CUPTI medians of
the replay time, isolated B300 node, 09:29-09:56 UTC) at `023e5080`:
91/91 shapes correct, 45/45 timed rows > 1.0 vs trtllm-gen, geomean
1.2308, min 1.0180 (EP=8 T=128 uniform_spread); previous pin `6224e108`
1.2264 / min 1.0107.

### Round 13: device-side adaptive split-K for the plain-chain finalize
GEMM2

FlashInfer code commit `4f037b34` (the new pinned revision); again only
the plain routing -> GEMM1 -> GEMM2 chain changes
(the finalize GEMM2 of the decode rows and of the expert-parallel rank's
`T <= 1024` rows; split, hybrid, mixed and deferred
launches are untouched). Round 12 left the decode chain's GEMM2 with its
whole weight tile resident before GEMM1 ends, and
measured what remains after GEMM1 as the MMA-issue-bound loop over that
resident tile (96 `kind::f8f6f4` MMAs of K = 32,
~3.1 us) plus the row gather, epilogue and drain. Its finalize epilogue
accumulates into the output with `red.global.add`,
so partial K sums are additive with no cross-CTA reduction, partial
buffer or counter: GEMM2's persistent scheduler now
publishes a K range with every work item (7-field tile info: K begin /
count added) and, when the valid work of the launch
fits in half the SMs (`num_groups x m_chunks <= max_active_clusters //
2`, 74 items on B300), it hands out `(m_chunk, split)`
items with S = 2 halves of the K loop, so two CTAs stream and issue each
output tile's halves concurrently. When the launch
does not qualify, the items are remapped onto the original raster
exactly (no skipped items, no idle CTAs; the first form of
the patch skipped the unsplit items and idled the odd CTAs, which cost
the multi-expert decode rows 9-12 % and was fixed
before adoption). Shard rows (K = 384, one stage) keep S = 1, the
deferred form keeps S = 1, and any K not divisible by S falls
back to S = 1. `SWAPAB_GEMM2_SPLIT_K=1` restores the previous chain.

Measured (B300, same GPU, r36 vs the round-12 revision alternating, 20
repeats, FP64-checked):

* EP=8 single-expert decode rows (hot / empty / remote-dominated `T =
1..8`, empty `T = 16`): 1.028-1.038x (21.9-22.2 ->
21.1-21.6 us); multi-expert decode rows (balanced, remote-dominated `T
>= 2`, hot `T = 16`) 0.997-1.004x (unsplit path,
same raster as before); the shard's decode rows 0.992-1.008x (S = 1
there). EP=8 `empty` `T = 128..1024` 1.023-1.036x
(26.1 -> 25.6, 28.8 -> 27.8, 28.9 -> 28.0, 31.0 -> 30.1 us); every other
`T = 128..1024` row 0.996-1.001x.
* Split factor sweep on the single-expert rows: S = 2 +3.3-3.8 %, S = 3
-2 %, S = 4 -11 % (each split re-runs the 2.6 us
prologue and halves the per-CTA stage depth), so S = 2 is the only
adopted value.
* Per-kernel CUPTI start / end offsets of one graph replay (EP=8 `T = 1`
hot, same run for both trees): routing 0-2.8 us,
GEMM1 1.1-15.5 for both; GEMM2 4.1-21.9 before and 4.1-21.2 after, i.e.
the tail after GEMM1 goes 6.3 -> 5.5 us. What
remains is the row gather from GEMM1's output, six K stages per CTA
(~1.6 us of issue), the finalize epilogue and the
drain; the decode rows are now 21.1-21.6 us against the 5 us bytes floor
and the 9-10 us three-launch floor.
* Numerics: the two K partials each round through the BF16 `red.add`, so
the EP=8 decode rows' relative L2 error against
the FP64 reference moves from 0.00167 to 0.00247 (still the 1e-2 class;
all tolerances unchanged); every other row is
  bit-identical to the previous revision.

Bench (tree r36 = `4f037b34`, B300, graph, GPU span, 30 paired CUPTI
repeats): EP=8 44/44 rows > 1 vs TRT-LLM Gen by GPU span (geomean 1.340,
min 1.022 at `T = 128` balanced; previous revision 1.331 / 1.030), long
rows 12 (geomean 1.387; the pre-existing sub-1 dense rows `T = 8192`
balanced / hot 0.801 / 0.835 and `T = 16384` remote-dominated 0.857,
dense path unchanged, same-GPU pairs against the previous revision
0.999-1.006x); MoE-TP 33/33 > 1 (geomean 1.403, min 1.076 at `T = 2048`
hot; previous 1.396 / 1.073), long rows 9 (geomean 1.041; `T = 8192`
balanced / hot 0.976 / 0.980 and `T = 16384` empty 0.978 below one,
dense path unchanged, pairs 1.000-1.004x and 1.055x median / 1.037x mean
for `T = 32768` hot in a six-arm pair of 20 repeats); deferred form EP=8
1.178 / MoE-TP 1.149 (previous 1.174 / 1.152). Against the previous
revision on the bench node every required row reads 0.947-1.015x (EP=8;
the two balanced decode rows above 1.01 pair 0.997-0.998x on the same
GPU) and 0.976-1.006x (MoE-TP). The kernel-sum columns keep the round-12
wait artifact (18 EP=8 and 5 MoE-TP graph rows and the three EP=8 eager
`T = 128` rows below one on that column while every span and end-to-end
ratio is above one).

Validation: small-geometry suite 200 passed, routing / split / decode
selection slice 175 passed, deferred finalize 69 passed, all-local (896
local experts) 2 passed, EP=8 rank sum 4 passed (+4 shard-sum OOM skips,
as in every round), TP=8 shard sum 3 passed + 1 skipped (hot T=512,
fixture OOM, as in every round), TP=8 paired FP64 18 passed, TP=8 graph
replay `T = 1..16` 16 passed; compute-sanitizer synccheck + memcheck on
the same 36-row list, now with the split scheduler and the K-range tile
info of the finalize GEMM2 under both tools: 72 runs, 142 summaries,
every one `ERROR SUMMARY: 0 errors`.

Contract: the 45-row timed contract (EP=8 rank 3 and MoE-TP rank 0, T =
1..2048, uniform / spread / hot routings, graph-replay CUPTI medians of
the replay time, isolated B300 node, 11:38-12:04 UTC) at `4f037b34`:
91/91 shapes correct, 45/45 timed rows > 1.0 vs trtllm-gen, geomean
1.2329, min 1.0184 (EP=8 T=128 uniform_spread); previous pin `023e5080`
1.2308 / min 1.0180.

### Round 14: 2-CTA cluster split-K for the plain-chain SiTU GEMM1

FlashInfer code commit `822d86fe` (the new pinned revision); again only
the plain routing -> GEMM1 -> GEMM2 chain changes, and
only on expert-parallel ranks (the host enables the cluster form when
`num_local_experts < num_experts`, the tile is
`n_tile <= 16` tokens, the K-tile count is even and each CTA owns one M
chunk; the shard, the split / hybrid / mixed / deferred
launches and every `n_tile > 16` launch keep the round-13 kernel). After
round 13 the single-expert decode rows spent 12.5 of
their 21 us in GEMM1's 56-stage K chain on one expert: 32 work items on
148 SMs, each CTA streaming and issuing the whole K range
alone. The swap GEMM1 now launches as a `(1, 1, 2)` cluster along its
persistent grid; every TMA and pipeline coordinate keeps the
single-CTA layout and the cluster exists only for the exchange. Both
CTAs of a pair take the same `(m_chunk, row_group)` item
and split its K range (the round-13 rule, grid-uniform and device-side:
only while the valid items fit half the CTA budget).
The peer scales its 128 x `n_tile` FP32 accumulator by alpha and ships
it with `st.async` into the leader's shared memory,
completing the leader's `red_full` mbarrier by transaction count; the
leader adds it to its own accumulator before the SiTU +
MXFP8 requant epilogue and frees the slot with a remote
`mbarrier.arrive.release.cluster` on the peer's `red_empty`. Unsplit
launches take neither cluster barrier and never touch the peer.
`SWAPAB_GEMM1_CLUSTER_SPLIT=0` restores the round-13 chain.

Measured (B300, same GPU, r37 vs the round-13 revision alternating, 20
repeats, FP64-checked):

* EP=8 single-expert decode rows (hot / empty / remote-dominated `T =
1..16`): 1.081-1.087x (20.9-21.7 -> 19.2-20.0 us);
EP=8 `empty` `T = 128` 1.104x and `T = 1024` 1.010x; the multi-expert
decode rows (three active local experts,
96 items, unsplit) 0.988-1.001x; the shard's decode rows 0.996-1.006x
(the cluster form is never launched there); every
  other `T = 128..1024` row 0.995-1.011x.
* The 1-1.2 % on the unsplit rank rows is neither the cluster launch nor
the shared memory: the same kernel without the cluster
launch and never splitting measures 0.984-0.999x, and the round-13
kernel with only the 8 KB exchange buffer added to its
shared memory 0.993-1.001x; it is the split-capable code path itself
(K-range tile info and the exchange branches in the
epilogue) and stays the next lever. Against the phase-2 baseline those
rows pair 1.026-1.109x on the same GPU (`T = 1..16`
balanced / remote-dominated on the rank) and the single-expert rows
1.28-1.30x.
* Per-kernel CUPTI start / end offsets of one graph replay (EP=8 `T = 1`
hot, same run for both trees): routing 0-2.5 us for
both; GEMM1 1.0-15.4 -> 1.1-13.6 us, GEMM2 3.9-20.9 -> 4.3-19.3 us.
Splitting the 56-stage chain in two removed ~1.8 us of GEMM1's ~14.4 us:
each CTA still runs the 2.6 us prologue, 28 stages, the exchange round
trip and the epilogue, and
GEMM2's tail after GEMM1 moves 5.5 -> 5.7 us; the decode rows now stand
at 19.2-20.0 us against the 5 us bytes floor and
  the 9-10 us three-launch floor.
* Numerics: the peer's FP32 partial is added before the requant, so
every row whose launch does not split is bit-identical to
the previous revision and the split rows stay in the same 1e-2 class
(EP=8 decode relative L2 error against FP64 0.00247 ->
  0.00247); all tolerances unchanged.

Bench (tree r37 = `822d86fe`, B300, graph, GPU span, 30 paired CUPTI
repeats): EP=8 44/44 rows > 1 vs TRT-LLM Gen by GPU span (geomean 1.373,
min 1.031 at `T = 128` balanced; previous revision 1.340 / 1.022), long
rows 12 (geomean 1.384; the pre-existing sub-1 dense rows `T = 8192`
balanced / hot 0.790 / 0.831 and `T = 16384` remote-dominated 0.877,
dense path unchanged, same-GPU pairs against the previous revision
0.998-1.005x); MoE-TP 33/33 > 1 (geomean 1.397, min 1.074 at `T = 2048`
hot; previous 1.403 / 1.076; the shard never launches the cluster form
and no row moves outside 0.99-1.03x of the previous bench), long rows 9
(geomean 1.079; `T = 8192` balanced / hot 0.998 / 0.984 below one, every
long row 1.007-1.031x of the previous bench on this node); deferred form
EP=8 1.200 / MoE-TP 1.155 (previous 1.178 / 1.149). Against the previous
revision on the bench node every required row reads 0.982-1.105x (EP=8;
the rows below 0.99 pair 0.991-1.000x on the same GPU: `T = 2` balanced
0.997, `T = 16` hot 0.991, `T = 256` / `T = 512` empty 0.995 / 1.011, `T
= 4096` empty 1.000) and 0.99-1.03x (MoE-TP). The kernel-sum columns
keep the round-12 wait artifact (14 EP=8 and 5 MoE-TP graph rows and the
three EP=8 eager `T = 128` rows below one on that column while every
span and end-to-end ratio is above one).

Validation: small-geometry suite 200 passed, routing / split / decode
selection slice 175 passed, deferred finalize 69 passed, all-local (896
local experts) 2 passed, EP=8 rank sum 4 passed (+4 shard-sum OOM skips,
as in every round), TP=8 shard sum 3 passed + 1 skipped (hot T=512,
fixture OOM, as in every round), TP=8 paired FP64 18 passed, TP=8 graph
replay `T = 1..16` 16 passed; compute-sanitizer synccheck + memcheck on
the same 36-row list, now with the cluster launch, the DSMEM exchange
and its two mbarriers of the SiTU GEMM1 under both tools: 72 runs, 142
summaries, every one `ERROR SUMMARY: 0 errors`.

Contract: the 45-row timed contract (EP=8 rank 3 and MoE-TP rank 0, T =
1..2048, uniform / spread / hot routings, graph-replay CUPTI medians of
the replay time, private isolated B300 node, 14:30-14:57 UTC) at
`822d86fe`: 91/91 shapes correct, 45/45 timed rows > 1.0 vs trtllm-gen,
geomean 1.2370, min 1.0294 (EP=8 T=128 uniform_spread); previous pin
`4f037b34` 1.2329 / min 1.0184.

### Round 15: measured structural terms of the open rows, three
host-level levers (no kernel change)

FlashInfer code commits `49b5f191` + `d1604402` (the new pinned revision
is `d1604402`; `mxfp4.py` and the routing dispatcher only, no CuTe DSL
kernel changes). Round 14 left 21 rows above 1.10x of the reachable
floor. Before touching them the floor's terms were re-measured
against launches of a known item count (synthetic routings giving `e`
local experts exactly 128 or 32 rows each, per-kernel CUPTI
medians) and against per-kernel timelines from `T = 128` to `32768` on
both layouts, all on one B300. Three terms are structural to
the kernels and now sit in the floor; three were schedule choices on the
host and are changed in this revision.

Structural (documented in the roofline subsection):

* A kernel with fewer items than SMs is bound by its single-item chain,
not by a share of the chip's fill rate: a lone dense
128 x 256 gather tile at `K = 7168` takes 23.7 us (56 stages, 0.42 us
per stage, 120 GB/s through one SM) whether the launch has
24 or 144 tiles; a lone 128 x 128 tile 15.8 us; a 16- / 32-row swap
group 11.0 / 16.5 us after its routing dependency. At full
occupancy a wave of 148 dense tiles costs 27.9 us (106 GB/s per SM, 15.7
TB/s aggregate) and a wave of 148 swap groups 11.1 us.
* The finalize tile's reduce-add does not overlap the next tile's fill
(EP=8 GEMM2 9.3 us per wave = 7.3 fill + 2.0 reduce;
  the shard's `K = 384` tile 1.57 us = 0.86 + 0.82).
* The route bookkeeping before the first GEMM grows with `T`
independently of the routing: the fused routing kernel scans the
routes in 4.2 us + 2.2 us per 1000 tokens; the dense form's route
conversion, weight copy and sort cost 7.6 us + 0.27 us per
1000 tokens plus five launch gaps of 0.34 us. An `empty` row pays the
same bookkeeping as a balanced one.

Changed (measured B300, same GPU, alternating against the round-14
revision, 10 repeats, FP64-checked; `--check` relative L2
against FP64 identical to five digits on every row):

* **Dense output zero-fill on an auxiliary stream (expert-parallel
ranks).** The dense form zeroed the `T x H` BF16 output between GEMM1
and GEMM2 in stream order: 5.6 / 10.5 / 19.8 / 37.9 / 74.7 us at `T =
2048 / 4096 / 8192 / 16384 / 32768` (half of the EP=8 `T = 32768`
`empty` row, 1-3 % of the long balanced rows). On expert-parallel ranks
the plan now records an event after the routing sort, launches the
fill on an auxiliary stream and joins it before GEMM2 (graph capture
turns the fork/join into edges; `MXFP4_DENSE_ASYNC_MEMSET` = `ep`
by default, `1` for every layout, `0` for the in-order launch
everywhere). EP=8 `empty` `T = 2048 / 4096 / 8192 / 16384 / 32768`:
0.913 /
0.892 / 0.868 / 0.907 / 0.986 of the previous time; balanced
0.970-0.992, remote-dominated 0.984-0.992. Hidden behind GEMM1 the fill
shares HBM with it (it stretches to 97 us at `T = 32768` and GEMM1 slows
by about the hidden bytes), so the long rows keep a 1-3 % gain
and the `T = 32768` `empty` row stays fill-bound. The MoE-TP shard keeps
the in-order launch: paired on one GPU (20 repeats, both arms on
the same routing path) its dense rows read 0.969-1.005x with the overlap
(`T = 8192` hot 0.973, `T = 32768` hot / `empty` 0.969 / 0.981),
because the finalize GEMM2 ran 2-4 % slower without the zero-fill right
before it (the z…

### [69ead1d](https://github.com/flashinfer-ai/flashinfer/commit/69ead1ded5ff834a05f6460d7eabd878f1dc1455)

- **作者**: eigen
- **时间**: 2026-09-27T19:47:04Z
- **提交信息**: perf(cake_sampling): round-3 kernels (candidate-list stage 1, composite bitonic stage 2/3) and re-fitted dispatch (#5607)

## Summary

Round 3 of the radix top-k -> sparse top-p -> sampling pipeline
(`flashinfer.cake_sampling`): a new frozen kernel bundle that attacks
the fixed cost of both stages, plus re-fitted dispatch constants.

- **Stage 2/3**: the slab is sorted once as 64-bit composites `(key <<
32) | ~idx` by a bitonic network in registers / warp shuffles / one
ping-pong smem buffer, replacing two CUB radix sorts. Stage alone
1.75-2.5x (B200: k <= 64 8.29 -> 3.30 us, k = 1000 14.02 -> 8.00 us);
bit-identical samples, sorted slab and renormalised output.
- **Stage 1**: one cluster-wide radix pass, then each CTA appends its
selected-bucket elements to a replicated candidate list (<= 2048); after
a single cluster barrier the remaining passes run locally on the
gathered candidates. Falls back to the exact multi-pass path when the
bucket is larger (adversarial rows). Stage alone 1.12-1.45x on B200 and
GB300; the selected set is identical to the previous kernel, so pipeline
outputs are unchanged.
- **Dispatch**: cost constants re-fitted to the new kernels (resident
2.0 + 0.1/entry us, streaming 6.0 + 0.4/chunk us); 0 % regret against
per-variant sweeps on all four GPUs; V = 151936, B <= 8 now takes the
(8,48) resident variant.
- **Bundle**: `csrc/cake_sampling/generated/` regenerated from the
single Cake generator source (21 kernels, source sha256 `120fc309…`),
manifest updated.
- `benchmarks/bench_cake_sampling.py`: `--skip-joint` (the joint
rejection-sampler arm takes minutes per cell at k = 10, large V) and
line-buffered rows.

## Measured (192 cells per GPU: B 1-128 x V 32K/128K/152K/256K x k
10/50/1000, eager + CUDA graph, CUPTI, same node/run for both bundles)

| arch | cells | worst new/base | B<=16 gain vs base min / median / max
| B>16 gain min / median | vs top_k_first min / median / max |
|---|---|---|---|---|---|
| H100 sm_90a | 192 | 0.972 | 1.03 / 1.26 / 1.75 | 1.05 / 1.16 | 1.24 /
2.66 / 7.31 |
| B200 sm_100a | 192 | 0.948 | 1.07 / 1.32 / 1.71 | 1.05 / 1.21 | 1.36 /
2.98 / 9.56 |
| GB300 sm_103a | 192 | 0.944 | 1.07 / 1.25 / 1.42 | 1.06 / 1.17 | 1.17
/ 3.02 / 9.86 |
| R200 sm_107a | 192 | 0.937 | 1.12 / 1.38 / 1.71 | 1.07 / 1.18 | 1.54 /
2.89 / 5.42 |

- No cell is slower than the previous bundle by more than the 2 % noise
band; every cell beats the default `top_k_first` route.
- Cells that gain less than 15 % over the previous bundle are those
whose stage 1 runs the unchanged streaming template (V = 262144; B = 16
at V = 128K/152K on H100 and GB300) and k = 1000 at V = 151936, B <= 8
on H100.
- Full per-cell tables: `docs/api/cake_sampling.rst`.

## Tests

- `tests/utils/test_cake_sampling.py` +
`tests/utils/test_cake_sampling_upstream.py`: 246 passed / 18 skipped on
H100, B200, GB300, R200 and RTX PRO 6000 (sm_120 route/fallback
semantics unchanged).
- compute-sanitizer synccheck + memcheck on the 8 registered pipeline
cells: 0 errors on B200 and R200.
- Outputs are bit-identical to the previous bundle (selection is exact;
the sample is determined by the Philox seed/offset).

## Baselines and source PRs

- Baseline for every comparison: the merged bundle from #5585 (this
branch's base commit 7b8f6129ce) and FlashInfer's `top_k_first` route
measured in the same run.
- Source PRs of this module: #5439 (introduction), #5482 (SM90 / SM107
dispatch), #5585 (R200 single-wave capacity table), this PR (round-3
kernels).
- Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated sampling route selection to improve performance across
supported hardware and workload sizes.
* **Documentation**
* Expanded sampling documentation with selection-method details and
refreshed benchmark results across additional hardware, batch sizes, and
vocabulary sizes.
* **Benchmarking**
* Added an option to skip joint-route measurements. Benchmark output now
appears as it is produced.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [97b3bd8](https://github.com/flashinfer-ai/flashinfer/commit/97b3bd80f0b9869b591a6732d871e6d09549388c)

- **作者**: eigen
- **时间**: 2026-09-27T19:17:08Z
- **提交信息**: perf(cake_mm_fp4): faster NVFP4 per-token path (register-resident per-token quantize, per-tile alpha epilogue, low-M split-K, L2 eviction policies) (#5609)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #5504 (per-token alpha for NVFP4 `mm_fp4` + `out_scale`
fold in per-token `nvfp4_quantize`). Four kernel-level changes on the
CuTe-DSL SM100 path, measured on B200 and GB300:

1. **Per-token quantize kernel** (`nvfp4_quantize.py`,
`NVFP4QuantizePerTokenKernel`): the row stays register-resident (one
global read instead of two passes), the CTA width is chosen from K and M
(128..512 threads; wide CTAs only while M <= 4096, the narrowest
register-resident width above), padding-row zeroing folded,
`griddepcontrol.launch_dependents` right after the row reduction. Output
(fp4 words, E4M3 SF, per-token scale, padding SF) is bitwise identical
to #5504 on every measured row.
2. **Per-token alpha epilogue** (`dense_blockscaled_gemm_sm100.py`): the
t2r fragment's token coordinates are resolved statically from the
partitioned identity layout, so alpha is loaded once per tile ("m"
orientation, 32dp32b) or once per distinct token per subtile ("n"
orientation under swap_ab) instead of once per element with a
per-element clamp. Same multiply, same accumulation order: outputs are
bitwise identical to #5504.
3. **Low-M cluster split-K for NVFP4, with narrow token tiles over
several N tiles** (`dense_blockscaled_gemm_sm100_splitk.py`, the #3847
MXFP8 kernel, plus `dense_blockscaled_gemm_sm100.py`): the MXFP8-only
guards are relaxed (sf_vec_size 16, 4-bit A/B) and the epilogue applies
the per-token alpha after the FP32 cluster reduction. Both kernels now
address the 128-token SFB tile per sub-tile when the N tile is narrower
than 64 (TMA slice `coord // (128/tile_n)`, one TMEM column per 32
tokens, the smem->TMEM scale-factor copy starts at the remaining token
row), so an 8/16-wide token tile can cover M up to 32 with
ceil(M/tile_n) N tiles; `can_implement` accepts `n > tile_n` for those
tiles. The untuned `mm_fp4(backend="cute-dsl")` path picks split-K for M
<= 32 where it wins: <= 20 weight tiles with M <= 16 -> 8/16-wide tile,
4 K slices; <= 20 weight tiles with 17 <= M <= 32 -> 8-wide tile over
ceil(M/8) N tiles, 2 K slices; otherwise <= sm_count/2 tiles with K >=
16384 -> 2 slices. The split-K tactics (every supported tile no wider
than the covering tile) are also enumerated for the autotuner (kernel
type `sm100sk`, the `use_tma_store` slot carries the slice count). Two
further untuned rules from round 7: with >= 128 weight tiles and K % 512
== 0 the persistent kernel runs with 8 MMA K instructions per stage (K
tile 512, `mma_inst_tile_k=8`, carried in the `use_tma_store` slot of an
`sm100` tactic and enumerated for the autotuner; same instruction order,
so outputs stay bitwise identical); on SM103 only, shapes with <=
sm_count/2 weight tiles and 8192 <= K < 16384 run the persistent kernel
with TMA prefetch for 17 <= M <= 32 (a two-slice split-K for M <= 16 on
the same shapes was measured and dropped).

4. **L2 eviction policies on the operand TMA streams**
(`dense_blockscaled_gemm_sm100.py`, `gemm_mm_fp4_cute_dsl.py`,
`gemm_base.py`): the persistent kernel streams the weight matrix once
per token tile while every CTA of a column re-reads the same token tile
and scale factors; with the default policy the 32-117 MB weight stream
flushes them from L2. The TMA producer now creates runtime L2 policies
(`createpolicy.fractional.L2::evict_first|evict_last`) and passes them
as `cache_policy` to the operand TMA loads. `mm_fp4_l2_policy()` picks
the policy per shape: with at most two token tiles (`ceil(M /
token_tile) <= 2`) the weight operand (A under swap_ab, else B) loads
`evict_first`; with more token tiles the no-swap kernel loads both
operands `evict_last` (the weights are then re-read by every M tile and
each token tile by every N tile). Cache hints only, outputs bitwise
unchanged; the policy is part of the compile cache key and the on-disk
kernel name, and the autotuner precompile worker builds the same kernel
(the worker also now honours the K-tile-512 slot). `evict_first` on the
weights moves the 64-224-weight-tile small-M rows (8192x8192,
7168x18432, 8192x28672, 18432x7168, 16384x7168, 28672x8192 at M <= 32)
from 0.99-1.02 to 1.04-1.20 and the M = 130-512 rows to 1.08-1.24 on
both GPUs; `evict_last` on both operands adds 0.1-10 % on the M = 2048 /
8192 rows (`evict_last` on either operand alone was mixed or left rows
at 0.999).

## Baselines and their source PRs

- #5504 `7d967939` (merged 2026-09-27, author @aleozlx): per-token alpha
epilogue + per-token quantize `out_scale` fold. Files:
`flashinfer/gemm/kernels/dense_blockscaled_gemm_sm100.py`,
`flashinfer/gemm/gemm_base.py`,
`flashinfer/gemm/gemm_mm_fp4_cute_dsl.py`,
`flashinfer/quantization/kernels/nvfp4_quantize.py`, tests. This is the
baseline arm of every table below.
- #4441 (closed, superseded by #5504): original per-token quantization
proposal for NVFP4 `mm_fp4`; not merged, no code measured.
- #3847 `e7f305e6` (merged 2026-07-08): SM100 CuTe-DSL MXFP8 split-K
kernel that change 3 generalises.
- Merge base of this branch with `main`: `7d967939` (= #5504 merge).
Verified 2026-09-27: no upstream commit after `7d967939` touches the
files changed here (`git log 7d967939..origin/main -- <files>` is empty;
`origin/main` = `d97b1801`).

## Methodology

Same container (`sglang:26.07-py3` + `nvidia-cutlass-dsl 4.7.0`), same
GPU, both trees on `PYTHONPATH` in separate processes,
`flashinfer.testing.bench_gpu_time(enable_cupti=True,
cold_l2_cache=True)`, 100 iterations per row, 6 rounds with the arm
order alternated each round; each cell is the min over rounds of the
per-round median. Shapes: (K, N) in {(7168,2112), (7168,1536),
(16384,7168), (7168,18432), (18432,7168), (8192,8192), (8192,28672),
(28672,8192)} x M in {1, 8, 17, 32, 128, 130, 257, 512, 2048, 8192},
128x4 SF, bf16 and fp16 outputs. Weights statically quantised
(`nvfp4_quantize`, cuda backend), activations through the per-token
cute-dsl quantize with the weight scale folded (`out_scale`).

## Results (speedup = #5504 time / this PR time; each cell is the min
over 6 rounds of the per-round median of 100 CUPTI-timed iterations,
cold L2)

Per GPU: the three delivery tables (quantize kernel, GEMM with per-token
alpha, fused quantize + GEMM under a CUDA Graph with PDL) plus the
scalar-alpha GEMM A/A check. Rows marked `(<=1)` are within measurement
noise of 1.00 and run the same persistent kernel code as #5504 (the
split-K rule does not fire for them); see the summary line of each
table.


### B200 (sm_100a)

<details><summary><b>Per-token quantize kernel</b> - geomean bf16 1.5659
/ fp16 1.5678; rows <= 1.00: bf16 0/80, fp16 0/80; min bf16 1.0854, fp16
1.0518</summary>

| K | N | M | bf16 base / cand us | bf16 speedup | fp16 base / cand us |
fp16 speedup |
|---|---|---|---|---|---|---|
| 7168 | 1536 | 1 | 4.70 / 2.94 | 1.598 | 4.70 / 2.98 | 1.581 |
| 7168 | 1536 | 8 | 4.45 / 2.85 | 1.562 | 4.42 / 2.85 | 1.551 |
| 7168 | 1536 | 17 | 4.51 / 2.85 | 1.584 | 4.48 / 2.88 | 1.556 |
| 7168 | 1536 | 32 | 4.56 / 2.78 | 1.638 | 4.53 / 2.82 | 1.608 |
| 7168 | 1536 | 128 | 4.93 / 3.14 | 1.571 | 4.93 / 3.14 | 1.571 |
| 7168 | 1536 | 130 | 4.99 / 3.17 | 1.576 | 4.96 / 3.17 | 1.566 |
| 7168 | 1536 | 257 | 5.31 / 3.74 | 1.419 | 5.28 / 3.78 | 1.398 |
| 7168 | 1536 | 512 | 6.02 / 4.80 | 1.253 | 6.02 / 4.83 | 1.245 |
| 7168 | 1536 | 2048 | 13.34 / 12.02 | 1.111 | 13.22 / 12.00 | 1.101 |
| 7168 | 1536 | 8192 | 35.23 / 29.20 | 1.207 | 34.88 / 29.01 | 1.202 |
| 7168 | 2112 | 1 | 4.58 / 2.82 | 1.625 | 4.54 / 2.82 | 1.614 |
| 7168 | 2112 | 8 | 4.45 / 2.85 | 1.562 | 4.42 / 2.85 | 1.551 |
| 7168 | 2112 | 17 | 4.51 / 2.75 | 1.640 | 4.51 / 2.75 | 1.639 |
| 7168 | 2112 | 32 | 4.54 / 2.85 | 1.596 | 4.51 / 2.86 | 1.575 |
| 7168 | 2112 | 128 | 4.93 / 3.14 | 1.571 | 4.93 / 3.17 | 1.556 |
| 7168 | 2112 | 130 | 5.02 / 3.23 | 1.554 | 4.99 / 3.20 | 1.560 |
| 7168 | 2112 | 257 | 5.31 / 3.78 | 1.407 | 5.30 / 3.81 | 1.391 |
| 7168 | 2112 | 512 | 6.03 / 4.83 | 1.248 | 6.02 / 4.86 | 1.237 |
| 7168 | 2112 | 2048 | 13.22 / 12.18 | 1.085 | 13.12 / 12.16 | 1.079 |
| 7168 | 2112 | 8192 | 34.98 / 28.74 | 1.217 | 34.69 / 28.51 | 1.217 |
| 7168 | 18432 | 1 | 4.58 / 2.75 | 1.663 | 4.54 / 2.78 | 1.632 |
| 7168 | 18432 | 8 | 4.45 / 2.69 | 1.655 | 4.45 / 2.69 | 1.655 |
| 7168 | 18432 | 17 | 4.51 / 2.72 | 1.659 | 4.51 / 2.75 | 1.639 |
| 7168 | 18432 | 32 | 4.58 / 2.78 | 1.644 | 4.54 / 2.82 | 1.614 |
| 7168 | 18432 | 128 | 4.93 / 3.14 | 1.572 | 4.96 / 3.14 | 1.581 |
| 7168 | 18432 | 130 | 5.02 / 3.20 | 1.570 | 5.09 / 3.20 | 1.590 |
| 7168 | 18432 | 257 | 5.28 / 3.74 | 1.410 | 5.34 / 3.84 | 1.392 |
| 7168 | 18432 | 512 | 6.02 / 4.80 | 1.253 | 6.02 / 4.83 | 1.245 |
| 7168 | 18432 | 2048 | 13.28 / 12.13 | 1.095 | 13.15 / 12.00 | 1.096 |
| 7168 | 18432 | 8192 | 35.04 / 28.80 | 1.217 | 34.61 / 28.37 | 1.220 |
| 8192 | 8192 | 1 | 4.80 / 3.01 | 1.596 | 4.80 / 3.04 | 1.579 |
| 8192 | 8192 | 8 | 4.51 / 2.88 | 1.567 | 4.50 / 2.91 | 1.544 |
| 8192 | 8192 | 17 | 4.51 / 2.75 | 1.639 | 4.50 / 2.78 | 1.615 |
| 8192 | 8192 | 32 | 4.54 / 2.94 | 1.543 | 4.53 / 2.96 | 1.530 |
| 8192 | 8192 | 128 | 4.93 / 3.23 | 1.525 | 4.93 / 3.23 | 1.524 |
| 8192 | 8192 | 130 | 4.99 / 3.30 | 1.514 | 4.99 / 3.33 | 1.500 |
| 8192 | 8192 | 257 | 5.41 / 3.94 | 1.374 | 5.38 / 3.90 | 1.377 |
| 8192 | 8192 | 512 | 6.51 / 5.15 | 1.264 | 6.46 / 5.09 | 1.270 |
| 8192 | 8192 | 2048 | 14.83 / 12.58 | 1.179 | 14.77 / 12.35 | 1.196 |
| 8192 | 8192 | 8192 | 39.44 / 31.63 | 1.247 | 39.10 / 31.57 | 1.239 |
| 8192 | 28672 | 1 | 4.80 / 3.04 | 1.579 | 4.77 / 3.04 | 1.568 |
| 8192 | 28672 | 8 | 4.50 / 2.91 | 1.544 | 4.48 / 2.90 | 1.547 |
| 8192 | 28672 | 17 | 4.51 / 2.78 | 1.621 | 4.48 / 2.80 | 1.600 |
| 8192 | 28672 | 32 | 4.54 / 2.94 | 1.543 | 4.54 / 2.98 | 1.527 |
| 8192 | 28672 | 128 | 4.93 / 3.23 | 1.525 | 4.93 / 3.23 | 1.525 |
| 8192 | 28672 | 130 | 5.02 / 3.33 | 1.510 | 4.99 / 3.33 | 1.500 |
| 8192 | 28672 | 257 | 5.41 / 3.90 | 1.385 | 5.38 / 3.90 | 1.377 |
| 8192 | 28672 | 512 | 6.53 / 5.15 | 1.267 | 6.50 / 5.12 | 1.269 |
| 8192 | 28672 | 2048 | 14.82 / 12.48 | 1.187 | 14.72 / 12.29 | 1.198 |
| 8192 | 28672 | 8192 | 39.63 / 31.74 | 1.248 | 39.20 / 31.62 | 1.240 |
| 16384 | 7168 | 1 | 7.34 / 3.49 | 2.105 | 7.33 / 3.49 | 2.101 |
| 16384 | 7168 | 8 | 7.02 / 3.36 | 2.090 | 6.98 / 3.36 | 2.076 |
| 16384 | 7168 | 17 | 7.17 / 3.26 | 2.196 | 7.12 / 3.26 | 2.181 |
| 16384 | 7168 | 32 | 7.26 / 3.52 | 2.064 | 7.23 / 3.49 | 2.073 |
| 16384 | 7168 | 128 | 7.90 / 4.10 | 1.930 | 7.84 / 4.10 | 1.914 |
| 16384 | 7168 | 130 | 7.90 / 4.35 | 1.816 | 7.97 / 4.38 | 1.818 |
| 16384 | 7168 | 257 | 8.56 / 5.47 | 1.564 | 8.51 / 5.38 | 1.583 |
| 16384 | 7168 | 512 | 10.50 / 8.57 | 1.224 | 10.43 / 8.51 | 1.226 |
| 16384 | 7168 | 2048 | 26.62 / 24.51 | 1.086 | 26.51 / 23.90 | 1.109 |
| 16384 | 7168 | 8192 | 78.49 / 71.94 | 1.091 | 78.89 / 75.01 | 1.052 |
| 18432 | 7168 | 1 | 7.97 / 3.55 | 2.243 | 7.89 / 3.46 | 2.283 |
| 18432 | 7168 | 8 | 7.81 / 3.42 | 2.280 | 7.76 / 3.36 | 2.309 |
| 18432 | 7168 | 17 | 7.87 / 3.65 | 2.158 | 7.86 / 3.58 | 2.192 |
| 18432 | 7168 | 32 | 7.90 / 3.62 | 2.186 | 8.00 / 3.49 | 2.294 |
| 18432 | 7168 | 128 | 8.51 / 4.42 | 1.928 | 8.58 / 4.35 | 1.971 |
| 18432 | 7168 | 130 | 8.61 / 4.74 | 1.818 | 8.70 / 4.67 | 1.863 |
| 18432 | 7168 | 257 | 9.41 / 5.92 | 1.589 | 9.38 / 5.79 | 1.619 |
| 18432 | 7168 | 512 | 11.36 / 9.25 | 1.228 | 11.30 / 9.12 | 1.239 |
| 18432 | 7168 | 2048 | 29.79 / 27.01 | 1.103 | 29.73 / 26.34 | 1.129 |
| 18432 | 7168 | 8192 | 94.27 / 64.67 | 1.458 | 94.05 / 64.45 | 1.459 |
| 28672 | 8192 | 1 | 11.17 / 4.32 | 2.585 | 11.14 / 4.21 | 2.647 |
| 28672 | 8192 | 8 | 10.94 / 4.10 | 2.672 | 10.88 / 3.97 | 2.742 |
| 28672 | 8192 | 17 | 11.10 / 4.10 | 2.711 | 11.07 / 4.00 | 2.768 |
| 28672 | 8192 | 32 | 11.23 / 4.29 | 2.619 | 11.14 / 4.19 | 2.656 |
| 28672 | 8192 | 128 | 11.84 / 5.34 | 2.216 | 11.78 / 5.22 | 2.258 |
| 28672 | 8192 | 130 | 11.97 / 5.76 | 2.078 | 11.87 / 5.63 | 2.108 |
| 28672 | 8192 | 257 | 13.57 / 7.49 | 1.812 | 13.54 / 7.25 | 1.867 |
| 28672 | 8192 | 512 | 16.42 / 12.38 | 1.326 | 16.27 / 11.81 | 1.378 |
| 28672 | 8192 | 2048 | 45.39 / 35.44 | 1.281 | 45.30 / 34.06 | 1.330 |
| 28672 | 8192 | 8192 | 161.47 / 105.63 | 1.529 | 161.36 / 106.93 |
1.509 |

</details>

<details><summary><b>GEMM, per-token alpha</b> - geomean bf16 1.1012 /
fp16 1.1011; rows <= 1.00: bf16 0/80, fp16 0/80; min bf16 1.0028, fp16
1.0043</summary>

| K | N | M | bf16 base / cand us | bf16 speedup | fp16 base / cand us |
fp16 speedup |
|---|---|---|---|---|---|---|
| 7168 | 1536 | 1 | 6.94 / 5.73 | 1.212 | 6.94 / 5.71 | 1.216 |
| 7168 | 1536 | 8 | 7.04 / 5.73 | 1.229 | 7.04 / 5.73 | 1.229 |
| 7168 | 1536 | 17 | 7.58 / 6.14 | 1.234 | 7.58 / 6.14 | 1.234 |
| 7168 | 1536 | 32 | 7.55 / 6.26 | 1.207 | 7.55 / 6.24 | 1.210 |
| 7168 | 1536 | 128 | 8.42 / 8.13 | 1.035 | 8.42 / 8.13 | 1.035 |
| 7168 | 1536 | 130 | 8.35 / 8.10 | 1.032 | 8.35 / 8.10 | 1.032 |
| 7168 | 1536 | 257 | 8.54 / 8.32 | 1.027 | 8.54 / 8.32 | 1.027 |
| 7168 | 1536 | 512 | 8.77 / 8.51 | 1.030 | 8.77 / 8.51 | 1.030 |
| 7168 | 1536 | 2048 | 12.83 / 12.10 | 1.061 | 12.83 / 12.10 | 1.061 |
| 7168 | 1536 | 8192 | 38.72 / 37.18 | 1.041 | 38.72 / 37.18 | 1.041 |
| 7168 | 2112 | 1 | 7.20 / 6.11 | 1.178 | 7.23 / 6.11 | 1.183 |
| 7168 | 2112 | 8 | 7.30 / 6.11 | 1.194 | 7.30 / 6.08 | 1.200 |
| 7168 | 2112 | 17 | 7.84 / 6.94 | 1.129 | 7.84 / 6.91 | 1.134 |
| 7168 | 2112 | 32 | 7.87 / 6.67 | 1.180 | 7.87 / 6.69 | 1.177 |
| 7168 | 2112 | 128 | 8.86 / 8.61 | 1.030 | 8.86 / 8.64 | 1.026 |
| 7168 | 2112 | 130 | 8.86 / 8.74 | 1.015 | 8.80 / 8.70 | 1.011 |
| 7168 | 2112 | 257 | 9.12 / 8.80 | 1.036 | 9.09 / 8.80 | 1.033 |
| 7168 | 2112 | 512 | 9.34 / 9.06 | 1.032 | 9.31 / 9.06 | 1.028 |
| 7168 | 2112 | 2048 | 15.52 / 14.94 | 1.039 | 15.52 / 14.94 | 1.039 |
| 7168 | 2112 | 8192 | 46.58 / 45.76 | 1.018 | 46.56 / 45.70 | 1.019 |
| 7168 | 18432 | 1 | 19.10 / 17.12 | 1.116 | 19.17 / 17.18 | 1.115 |
| 7168 | 18432 | 8 | 19.17 / 17.30 | 1.108 | 19.34 / 17.38 | 1.113 |
| 7168 | 18432 | 17 | 19.14 / 17.06 | 1.122 | 19.33 / 17.06 | 1.133 |
| 7168 | 18432 | 32 | 19.07 / 16.99 | 1.122 | 19.23 / 17.09 | 1.126 |
| 7168 | 18432 | 128 | 20.35 / 17.70 | 1.150 | 20.19 / 17.70 | 1.141 |
| 7168 | 18432 | 130 | 22.18 / 19.34 | 1.146 | 22.11 / 19.36 | 1.142 |
| 7168 | 18432 | 257 | 31.84 / 26.78 | 1.189 | 31.90 / 26.85 | 1.188 |
| 7168 | 18432 | 512 | 32.22 / 27.84 | 1.158 | 32.22 / 27.87 | 1.156 |
| 7168 | 18432 | 2048 | 89.02 / 88.25 | 1.009 | 89.07 / 88.35 | 1.008 |
| 7168 | 18432 | 8192 | 343.63 / 339.97 | 1.011 | 343.97 / 340.38 |
1.011 |
| 8192 | 8192 | 1 | 11.06 / 10.43 | 1.060 | 11.14 / 10.46 | 1.064 |
| 8192 | 8192 | 8 | 11.17 / 10.50 | 1.064 | 11.25 / 10.56 | 1.065 |
| 8192 | 8192 | 17 | 11.52 / 10.82 | 1.065 | 11.62 / 10.85 | 1.071 |
| 8192 | 8192 | 32 | 11.54 / 10.86 | 1.062 | 11.65 / 10.91 | 1.067 |
| 8192 | 8192 | 128 | 12.58 / 11.58 | 1.086 | 12.64 / 11.58 | 1.091 |
| 8192 | 8192 | 130 | 13.57 / 12.70 | 1.068 | 13.63 / 12.69 | 1.074 |
| 8192 | 8192 | 257 | 19.01 / 16.99 | 1.119 | 19.04 / 17.02 | 1.118 |
| 8192 | 8192 | 512 | 19.30 / 17.28 | 1.117 | 19.33 / 17.25 | 1.121 |
| 8192 | 8192 | 2048 | 52.64 / 51.81 | 1.016 | 52.64 / 51.81 | 1.016 |
| 8192 | 8192 | 8192 | 172.58 / 169.46 | 1.018 | 172.91 / 169.37 | 1.021
|
| 8192 | 28672 | 1 | 31.10 / 25.86 | 1.203 | 30.98 / 25.68 | 1.206 |
| 8192 | 28672 | 8 | 31.12 / 26.02 | 1.196 | 30.98 / 25.82 | 1.200 |
| 8192 | 28672 | 17 | 31.52 / 26.18 | 1.204 | 31.45 / 26.05 | 1.208 |
| 8192 | 28672 | 32 | 31.55 / 26.29 | 1.200 | 31.55 / 26.18 | 1.205 |
| 8192 | 28672 | 128 | 35.38 / 29.14 | 1.214 | 35.38 / 29.18 | 1.212 |
| 8192 | 28672 | 130 | 39.36 / 33.39 | 1.179 | 39.25 / 33.15 | 1.184 |
| 8192 | 28672 | 257 | 57.73 / 50.90 | 1.134 | 56.69 / 50.61 | 1.120 |
| 8192 | 28672 | 512 | 58.85 / 53.52 | 1.100 | 58.19 / 53.38 | 1.090 |
| 8192 | 28672 | 2048 | 154.88 / 154.45 | 1.003 | 154.77 / 154.03 |
1.005 |
| 8192 | 28672 | 8192 | 621.13 / 608.19 | 1.021 | 615.50 / 608.99 |
1.011 |
| 16384 | 7168 | 1 | 18.11 / 17.25 | 1.050 | 18.24 / 17.25 | 1.058 |
| 16384 | 7168 | 8 | 18.14 / 17.28 | 1.050 | 18.34 / 17.28 | 1.061 |
| 16384 | 7168 | 17 | 19.49 / 18.22 | 1.069 | 19.49 / 18.24 | 1.068 |
| 16384 | 7168 | 32 | 19.65 / 18.53 | 1.060 | 19.71 / 18.50 | 1.066 |
| 16384 | 7168 | 128 | 21.66 / 18.16 | 1.193 | 21.66 / 18.24 | 1.188 |
| 16384 | 7168 | 130 | 23.02 / 19.65 | 1.172 | 23.01 / 19.65 | 1.171 |
| 16384 | 7168 | 257 | 32.77 / 27.22 | 1.204 | 32.70 / 27.23 | 1.201 |
| 16384 | 7168 | 512 | 33.47 / 27.97 | 1.197 | 33.65 / 28.19 | 1.194 |
| 16384 | 7168 | 2048 | 93.14 / 92.61 | 1.006 | 93.14 / 92.69 | 1.005 |
| 16384 | 7168 | 8192 | 333.81 / 329.45 | 1.013 | 335.47 / 330.48 |
1.015 |
| 18432 | 7168 | 1 | 20.32 / 19.52 | 1.041 | 20.35 / 19.54 | 1.042 |
| 18432 | 7168 | 8 | 20.42 / 19.54 | 1.045 | 20.48 / 19.57 | 1.047 |
| 18432 | 7168 | 17 | 21.82 / 20.86 | 1.046 | 21.95 / 20.80 | 1.055 |
| 18432 | 7168 | 32 | 21.92 / 20.83 | 1.052 | 22.02 / 20.80 | 1.058 |
| 18432 | 7168 | 128 | 23.97 / 20.21 | 1.186 | 23.98 / 20.22 | 1.186 |
| 18432 | 7168 | 130 | 25.54 / 21.82 | 1.170 | 25.66 / 21.95 | 1.169 |
| 18432 | 7168 | 257 | 36.26 / 30.18 | 1.201 | 36.26 / 30.24 | 1.199 |
| 18432 | 7168 | 512 | 36.64 / 30.85 | 1.188 | 36.51 / 30.91 | 1.181 |
| 18432 | 7168 | 2048 | 104.18 / 103.45 | 1.007 | 104.35 / 103.49 |
1.008 |
| 18432 | 7168 | 8192 | 380.96 / 376.84 | 1.011 | 380.96 / 377.89 |
1.008 |
| 28672 | 8192 | 1 | 31.87 / 30.62 | 1.041 | 31.70 / 30.62 | 1.035 |
| 28672 | 8192 | 8 | 31.97 / 30.66 | 1.043 | 31.81 / 30.75 | 1.034 |
| 28672 | 8192 | 17 | 34.34 / 31.71 | 1.083 | 34.21 / 31.74 | 1.078 |
| 28672 | 8192 | 32 | 34.37 / 31.63 | 1.086 | 34.16 / 31.74 | 1.076 |
| 28672 | 8192 | 128 | 37.05 / 29.63 | 1.251 | 36.70 / 29.68 | 1.237 |
| 28672 | 8192 | 130 | 38.94 / 31.76 | 1.226 | 38.72 / 31.78 | 1.219 |
| 28672 | 8192 | 257 | 53.52 / 44.32 | 1.208 | 53.10 / 44.27 | 1.199 |
| 28672 | 8192 | 512 | 53.85 / 45.76 | 1.177 | 53.95 / 45.79 | 1.178 |
| 28672 | 8192 | 2048 | 161.47 / 160.77 | 1.004 | 161.38 / 160.69 |
1.004 |
| 28672 | 8192 | 8192 | 663.55 / 658.73 | 1.007 | 662.01 / 658.25 |
1.006 |

</details>

<details><summary><b>Fused quantize + GEMM (CUDA Graph, PDL)</b> -
geomean bf16 1.2142 / fp16 1.2170; rows <= 1.00: bf16 0/80, fp16 0/80;
min bf16 1.0165, fp16 1.0070</summary>

| K | N | M | bf16 base / cand us | bf16 speedup | fp16 base / cand us |
fp16 speedup |
|---|---|---|---|---|---|---|
| 7168 | 1536 | 1 | 11.92 / 8.38 | 1.422 | 11.90 / 8.38 | 1.420 |
| 7168 | 1536 | 8 | 11.65 / 8.22 | 1.416 | 11.63 / 8.22 | 1.414 |
| 7168 | 1536 | 17 | 12.51 / 8.96 | 1.396 | 12.46 / 8.98 | 1.389 |
| 7168 | 1536 | 32 | 11.82 / 8.74 | 1.354 | 12.10 / 8.73 | 1.385 |
| 7168 | 1536 | 128 | 13.50 / 11.17 | 1.209 | 13.44 / 11.20 | 1.200 |
| 7168 | 1536 | 130 | 12.99 / 11.01 | 1.180 | 13.25 / 10.98 | 1.207 |
| 7168 | 1536 | 257 | 13.60 / 11.79 | 1.153 | 13.54 / 11.73 | 1.154 |
| 7168 | 1536 | 512 | 14.82 / 13.09 | 1.132 | 14.82 / 13.14 | 1.128 |
| 7168 | 1536 | 2048 | 25.65 / 23.36 | 1.098 | 25.50 / 23.34 | 1.092 |
| 7168 | 1536 | 8192 | 69.44 / 62.03 | 1.119 | 69.22 / 61.95 | 1.117 |
| 7168 | 2112 | 1 | 11.49 / 8.11 | 1.416 | 11.42 / 8.13 | 1.406 |
| 7168 | 2112 | 8 | 11.94 / 8.64 | 1.381 | 11.94 / 8.64 | 1.382 |
| 7168 | 2112 | 17 | 12.70 / 9.79 | 1.297 | 12.70 / 9.76 | 1.302 |
| 7168 | 2112 | 32 | 12.13 / 9.22 | 1.316 | 12.42 / 9.22 | 1.347 |
| 7168 | 2112 | 128 | 13.76 / 11.49 | 1.198 | 13.73 / 11.10 | 1.236 |
| 7168 | 2112 | 130 | 13.84 / 11.71 | 1.182 | 13.82 / 11.71 | 1.180 |
| 7168 | 2112 | 257 | 14.18 / 12.26 | 1.157 | 14.18 / 12.16 | 1.166 |
| 7168 | 2112 | 512 | 14.93 / 13.12 | 1.138 | 14.94 / 13.12 | 1.139 |
| 7168 | 2112 | 2048 | 28.80 / 26.29 | 1.096 | 28.72 / 26.37 | 1.089 |
| 7168 | 2112 | 8192 | 77.47 / 70.56 | 1.098 | 77.26 / 69.94 | 1.105 |
| 7168 | 18432 | 1 | 24.10 / 19.82 | 1.216 | 24.32 / 20.00 | 1.216 |
| 7168 | 18432 | 8 | 23.46 / 19.39 | 1.210 | 23.58 / 19.33 | 1.220 |
| 7168 | 18432 | 17 | 23.42 / 19.46 | 1.204 | 23.87 / 19.65 | 1.215 |
| 7168 | 18432 | 32 | 23.74 / 19.46 | 1.220 | 23.82 / 19.62 | 1.214 |
| 7168 | 18432 | 128 | 24.80 / 20.03 | 1.238 | 24.74 / 20.03 | 1.235 |
| 7168 | 18432 | 130 | 27.01 / 21.98 | 1.228 | 27.14 / 21.86 | 1.242 |
| 7168 | 18432 | 257 | 37.09 / 30.43 | 1.219 | 37.12 / 29.87 | 1.243 |
| 7168 | 18432 | 512 | 37.57 / 31.78 | 1.182 | 38.02 / 32.16 | 1.182 |
| 7168 | 18432 | 2048 | 99.98 / 97.95 | 1.021 | 100.26 / 98.48 | 1.018 |
| 7168 | 18432 | 8192 | 373.28 / 363.28 | 1.028 | 374.22 / 365.15 |
1.025 |
| 8192 | 8192 | 1 | 16.06 / 12.74 | 1.261 | 16.03 / 12.74 | 1.259 |
| 8192 | 8192 | 8 | 16.22 / 13.25 | 1.225 | 16.16 / 13.25 | 1.220 |
| 8192 | 8192 | 17 | 16.35 / 13.21 | 1.237 | 16.37 / 13.22 | 1.238 |
| 8192 | 8192 | 32 | 16.35 / 13.28 | 1.231 | 16.38 / 13.31 | 1.231 |
| 8192 | 8192 | 128 | 17.52 / 14.34 | 1.222 | 17.54 / 14.30 | 1.226 |
| 8192 | 8192 | 130 | 18.69 / 15.49 | 1.207 | 18.66 / 15.49 | 1.204 |
| 8192 | 8192 | 257 | 24.50 / 20.45 | 1.198 | 24.41 / 20.58 | 1.187 |
| 8192 | 8192 | 512 | 25.79 / 21.57 | 1.196 | 25.63 / 21.52 | 1.191 |
| 8192 | 8192 | 2048 | 66.18 / 62.85 | 1.053 | 66.16 / 62.64 | 1.056 |
| 8192 | 8192 | 8192 | 206.61 / 194.75 | 1.061 | 207.09 / 194.81 | 1.063
|
| 8192 | 28672 | 1 | 36.38 / 28.86 | 1.261 | 36.27 / 28.21 | 1.286 |
| 8192 | 28672 | 8 | 35.87 / 28.80 | 1.246 | 36.10 / 28.67 | 1.259 |
| 8192 | 28672 | 17 | 35.90 / 28.22 | 1.272 | 35.97 / 28.43 | 1.265 |
| 8192 | 28672 | 32 | 36.05 / 28.70 | 1.256 | 36.16 / 28.77 | 1.257 |
| 8192 | 28672 | 128 | 40.03 / 31.65 | 1.265 | 39.90 / 31.77 | 1.256 |
| 8192 | 28672 | 130 | 44.24 / 35.94 | 1.231 | 43.81 / 35.68 | 1.228 |
| 8192 | 28672 | 257 | 62.27 / 54.05 | 1.152 | 61.09 / 53.71 | 1.137 |
| 8192 | 28672 | 512 | 64.18 / 57.47 | 1.117 | 63.65 / 57.41 | 1.109 |
| 8192 | 28672 | 2048 | 167.71 / 163.97 | 1.023 | 167.81 / 163.85 |
1.024 |
| 8192 | 28672 | 8192 | 649.40 / 637.82 | 1.018 | 656.64 / 639.21 |
1.027 |
| 16384 | 7168 | 1 | 25.60 / 19.84 | 1.290 | 25.78 / 19.82 | 1.300 |
| 16384 | 7168 | 8 | 25.47 / 20.00 | 1.274 | 25.55 / 19.97 | 1.280 |
| 16384 | 7168 | 17 | 27.23 / 21.22 | 1.284 | 27.17 / 21.25 | 1.279 |
| 16384 | 7168 | 32 | 27.42 / 21.70 | 1.264 | 27.54 / 21.71 | 1.268 |
| 16384 | 7168 | 128 | 29.60 / 21.50 | 1.376 | 29.63 / 21.63 | 1.370 |
| 16384 | 7168 | 130 | 30.59 / 23.01 | 1.330 | 30.78 / 23.01 | 1.338 |
| 16384 | 7168 | 257 | 40.90 / 31.63 | 1.293 | 40.83 / 31.49 | 1.297 |
| 16384 | 7168 | 512 | 43.65 / 35.52 | 1.229 | 43.71 / 35.62 | 1.227 |
| 16384 | 7168 | 2048 | 117.15 / 114.34 | 1.025 | 117.15 / 113.79 |
1.030 |
| 16384 | 7168 | 8192 | 409.53 / 402.88 | 1.017 | 408.16 / 405.31 |
1.007 |
| 18432 | 7168 | 1 | 28.80 / 22.62 | 1.273 | 28.88 / 22.35 | 1.292 |
| 18432 | 7168 | 8 | 28.74 / 22.72 | 1.265 | 28.80 / 22.62 | 1.273 |
| 18432 | 7168 | 17 | 30.34 / 23.94 | 1.267 | 30.40 / 23.94 | 1.270 |
| 18432 | 7168 | 32 | 29.87 / 23.74 | 1.258 | 30.22 / 23.78 | 1.271 |
| 18432 | 7168 | 128 | 32.21 / 23.74 | 1.356 | 32.58 / 23.68 | 1.376 |
| 18432 | 7168 | 130 | 34.11 / 25.47 | 1.339 | 34.21 / 25.38 | 1.348 |
| 18432 | 7168 | 257 | 45.02 / 35.01 | 1.286 | 45.06 / 34.93 | 1.290 |
| 18432 | 7168 | 512 | 47.30 / 39.30 | 1.204 | 47.52 / 39.02 | 1.218 |
| 18432 | 7168 | 2048 | 130.22 / 126.51 | 1.029 | 129.98 / 125.98 |
1.032 |
| 18432 | 7168 | 8192 | 472.38 / 438.89 | 1.076 | 472.20 / 438.33 |
1.077 |
| 28672 | 8192 | 1 | 43.09 / 34.11 | 1.263 | 42.75 / 34.03 | 1.256 |
| 28672 | 8192 | 8 | 42.72 / 33.92 | 1.259 | 42.78 / 34.00 | 1.258 |
| 28672 | 8192 | 17 | 45.23 / 35.17 | 1.286 | 45.28 / 35.23 | 1.285 |
| 28672 | 8192 | 32 | 45.50 / 35.52 | 1.281 | 45.02 / 35.17 | 1.280 |
| 28672 | 8192 | 128 | 48.29 / 33.82 | 1.428 | 47.90 / 33.86 | 1.415 |
| 28672 | 8192 | 130 | 50.30 / 36.19 | 1.390 | 49.89 / 35.97 | 1.387 |
| 28672 | 8192 | 257 | 65.81 / 51.01 | 1.290 | 65.31 / 50.58 | 1.291 |
| 28672 | 8192 | 512 | 68.06 / 57.18 | 1.190 | 68.32 / 57.02 | 1.198 |
| 28672 | 8192 | 2048 | 201.55 / 189.82 | 1.062 | 201.05 / 188.17 |
1.068 |
| 28672 | 8192 | 8192 | 834.55 / 779.59 | 1.070 | 831.10 / 776.17 |
1.071 |

</details>

<details><summary><b>GEMM, scalar alpha (A/A no-regression check; low-M
rows now take split-K)</b> - geomean bf16 1.0919 / fp16 1.0919; rows <=
1.00: bf16 9/80, fp16 9/80; min bf16 0.9855, fp16 0.9891</summary>

| K | N | M | bf16 base / cand us | bf16 speedup | fp16 base / cand us |
fp16 speedup |
|---|---|---|---|---|---|---|
| 7168 | 1536 | 1 | 6.93 / 5.73 | 1.210 | 6.94 / 5.73 | 1.212 |
| 7168 | 1536 | 8 | 6.94 / 5.76 | 1.206 | 6.91 / 5.76 | 1.200 |
| 7168 | 1536 | 17 | 7.49 / 6.11 | 1.225 | 7.49 / 6.11 | 1.225 |
| 7168 | 1536 | 32 | 7.46 / 6.18 | 1.207 | 7.46 / 6.18 | 1.207 |
| 7168 | 1536 | 128 | 8.22 / 8.19 | 1.004 | 8.19 / 8.19 | 1.000 (<=1) |
| 7168 | 1536 | 130 | 8.16 / 8.16 | 1.000 (<=1) | 8.19 / 8.14 | 1.006 |
| 7168 | 1536 | 257 | 8.38 / 8.34 | 1.006 | 8.35 / 8.34 | 1.002 |
| 7168 | 1536 | 512 | 8.58 / 8.58 | 1.000 (<=1) | 8.58 / 8.58 | 1.000 |
| 7168 | 1536 | 2048 | 12.61 / 12.13 | 1.040 | 12.61 / 12.13 | 1.040 |
| 7168 | 1536 | 8192 | 37.84 / 37.20 | 1.017 | 37.87 / 37.18 | 1.019 |
| 7168 | 2112 | 1 | 7.17 / 6.10 | 1.176 | 7.18 / 6.11 | 1.175 |
| 7168 | 2112 | 8 | 7.20 / 6.11 | 1.178 | 7.20 / 6.11 | 1.178 |
| 7168 | 2112 | 17 | 7.74 / 6.90 | 1.123 | 7.74 / 6.88 | 1.126 |
| 7168 | 2112 | 32 | 7.78 / 6.66 | 1.168 | 7.78 / 6.62 | 1.174 |
| 7168 | 2112 | 128 | 8.67 / 8.64 | 1.004 | 8.66 / 8.67 | 0.998 (<=1) |
| 7168 | 2112 | 130 | 8.67 / 8.80 | 0.985 (<=1) | 8.67 / 8.77 | 0.989
(<=1) |
| 7168 | 2112 | 257 | 8.93 / 8.86 | 1.007 | 8.93 / 8.86 | 1.007 |
| 7168 | 2112 | 512 | 9.15 / 9.09 | 1.007 | 9.14 / 9.09 | 1.005 |
| 7168 | 2112 | 2048 | 15.20 / 14.98 | 1.015 | 15.20 / 14.98 | 1.015 |
| 7168 | 2112 | 8192 | 46.34 / 45.73 | 1.013 | 46.46 / 45.70 | 1.017 |
| 7168 | 18432 | 1 | 19.04 / 17.09 | 1.114 | 19.14 / 17.23 | 1.111 |
| 7168 | 18432 | 8 | 19.09 / 17.18 | 1.111 | 19.25 / 17.28 | 1.114 |
| 7168 | 18432 | 17 | 19.04 / 16.90 | 1.127 | 19.17 / 16.96 | 1.130 |
| 7168 | 18432 | 32 | 19.01 / 16.86 | 1.127 | 19.10 / 16.90 | 1.131 |
| 7168 | 18432 | 128 | 20.19 / 17.66 | 1.143 | 20.19 / 17.68 | 1.142 |
| 7168 | 18432 | 130 | 21.95 / 19.39 | 1.132 | 21.89 / 19.42 | 1.127 |
| 7168 | 18432 | 257 | 31.58 / 26.85 | 1.176 | 31.62 / 26.94 | 1.173 |
| 7168 | 18432 | 512 | 31.98 / 27.87 | 1.148 | 32.03 / 27.90 | 1.148 |
| 7168 | 18432 | 2048 | 88.38 / 88.29 | 1.001 | 88.41 / 88.41 | 1.000
(<=1) |
| 7168 | 18432 | 8192 | 340.40 / 339.89 | 1.002 | 340.81 / 340.40 |
1.001 |
| 8192 | 8192 | 1 | 11.04 / 10.43 | 1.058 | 11.20 / 10.43 | 1.074 |
| 8192 | 8192 | 8 | 11.10 / 10.40 | 1.068 | 11.17 / 10.43 | 1.071 |
| 8192 | 8192 | 17 | 11.42 / 10.75 | 1.062 | 11.50 / 10.75 | 1.070 |
| 8192 | 8192 | 32 | 11.46 / 10.72 | 1.069 | 11.58 / 10.78 | 1.074 |
| 8192 | 8192 | 128 | 12.35 / 11.62 | 1.063 | 12.45 / 11.58 | 1.075 |
| 8192 | 8192 | 130 | 13.44 / 12.69 | 1.059 | 13.50 / 12.70 | 1.063 |
| 8192 | 8192 | 257 | 18.77 / 17.02 | 1.102 | 18.75 / 17.05 | 1.100 |
| 8192 | 8192 | 512 | 19.07 / 17.34 | 1.100 | 19.04 / 17.34 | 1.098 |
| 8192 | 8192 | 2048 | 51.89 / 51.81 | 1.002 | 52.00 / 51.87 | 1.002 |
| 8192 | 8192 | 8192 | 169.20 / 169.38 | 0.999 (<=1) | 169.76 / 169.36 |
1.002 |
| 8192 | 28672 | 1 | 31.10 / 25.90 | 1.201 | 30.96 / 25.70 | 1.205 |
| 8192 | 28672 | 8 | 31.10 / 26.08 | 1.193 | 30.98 / 25.89 | 1.197 |
| 8192 | 28672 | 17 | 31.47 / 26.13 | 1.205 | 31.42 / 25.97 | 1.210 |
| 8192 | 28672 | 32 | 31.62 / 26.24 | 1.205 | 31.55 / 26.18 | 1.205 |
| 8192 | 28672 | 128 | 35.23 / 29.22 | 1.206 | 35.18 / 29.25 | 1.203 |
| 8192 | 28672 | 130 | 39.23 / 33.41 | 1.174 | 39.10 / 33.15 | 1.180 |
| 8192 | 28672 | 257 | 57.38 / 50.88 | 1.128 | 56.45 / 50.66 | 1.114 |
| 8192 | 28672 | 512 | 58.69 / 53.55 | 1.096 | 58.08 / 53.44 | 1.087 |
| 8192 | 28672 | 2048 | 154.11 / 154.46 | 0.998 (<=1) | 154.08 / 154.02
| 1.000 |
| 8192 | 28672 | 8192 | 616.62 / 614.27 | 1.004 | 611.16 / 611.56 |
0.999 (<=1) |
| 16384 | 7168 | 1 | 18.06 / 17.25 | 1.047 | 18.24 / 17.22 | 1.059 |
| 16384 | 7168 | 8 | 18.10 / 17.22 | 1.051 | 18.27 / 17.25 | 1.059 |
| 16384 | 7168 | 17 | 19.41 / 18.18 | 1.068 | 19.39 / 18.22 | 1.064 |
| 16384 | 7168 | 32 | 19.58 / 18.51 | 1.058 | 19.63 / 18.50 | 1.061 |
| 16384 | 7168 | 128 | 21.50 / 18.24 | 1.179 | 21.50 / 18.21 | 1.181 |
| 16384 | 7168 | 130 | 22.86 / 19.65 | 1.164 | 22.88 / 19.68 | 1.163 |
| 16384 | 7168 | 257 | 32.50 / 27.26 | 1.192 | 32.45 / 27.29 | 1.189 |
| 16384 | 7168 | 512 | 33.25 / 27.98 | 1.188 | 33.44 / 28.26 | 1.183 |
| 16384 | 7168 | 2048 | 92.58 / 92.67 | 0.999 (<=1) | 92.54 / 92.66 |
0.999 (<=1) |
| 16384 | 7168 | 8192 | 329.42 / 329.49 | 1.000 (<=1) | 330.38 / 330.43
| 1.000 (<=1) |
| 18432 | 7168 | 1 | 20.29 / 19.46 | 1.043 | 20.37 / 19.55 | 1.042 |
| 18432 | 7168 | 8 | 20.30 / 19.50 | 1.041 | 20.35 / 19.52 | 1.043 |
| 18432 | 7168 | 17 | 21.76 / 20.80 | 1.046 | 21.86 / 20.77 | 1.052 |
| 18432 | 7168 | 32 | 21.82 / 20.80 | 1.049 | 21.94 / 20.77 | 1.056 |
| 18432 | 7168 | 128 | 23.81 / 20.24 | 1.176 | 23.81 / 20.29 | 1.174 |
| 18432 | 7168 | 130 | 25.44 / 21.89 | 1.162 | 25.54 / 21.95 | 1.163 |
| 18432 | 7168 | 257 | 36.05 / 30.27 | 1.191 | 36.00 / 30.24 | 1.190 |
| 18432 | 7168 | 512 | 36.38 / 30.94 | 1.176 | 36.24 / 30.94 | 1.171 |
| 18432 | 7168 | 2048 | 103.49 / 103.46 | 1.000 | 103.47 / 103.45 |
1.000 |
| 18432 | 7168 | 8192 | 376.53 / 376.54 | 1.000 (<=1) | 377.12 / 379.50
| 0.994 (<=1) |
| 28672 | 8192 | 1 | 31.84 / 30.64 | 1.039 | 31.71 / 30.62 | 1.035 |
| 28672 | 8192 | 8 | 31.87 / 30.66 | 1.040 | 31.74 / 30.59 | 1.038 |
| 28672 | 8192 | 17 | 34.27 / 31.65 | 1.083 | 34.14 / 31.66 | 1.078 |
| 28672 | 8192 | 32 | 34.30 / 31.63 | 1.084 | 34.08 / 31.76 | 1.073 |
| 28672 | 8192 | 128 | 36.85 / 29.66 | 1.242 | 36.48 / 29.74 | 1.226 |
| 28672 | 8192 | 130 | 38.78 / 31.76 | 1.221 | 38.58 / 31.79 | 1.213 |
| 28672 | 8192 | 257 | 53.25 / 44.29 | 1.202 | 52.85 / 44.29 | 1.193 |
| 28672 | 8192 | 512 | 53.60 / 45.81 | 1.170 | 53.66 / 45.86 | 1.170 |
| 28672 | 8192 | 2048 | 160.53 / 160.73 | 0.999 (<=1) | 160.57 / 160.67
| 0.999 (<=1) |
| 28672 | 8192 | 8192 | 660.33 / 658.54 | 1.003 | 662.71 / 661.64 |
1.002 |

</details>


### GB300 (sm_103a)

<details><summary><b>Per-token quantize kernel</b> - geomean bf16 1.5738
/ fp16 1.5845; rows <= 1.00: bf16 0/80, fp16 0/80; min bf16 1.1063, fp16
1.0615</summary>

| K | N | M | bf16 base / cand us | bf16 speedup | fp16 base / cand us |
fp16 speedup |
|---|---|---|---|---|---|---|
| 7168 | 1536 | 1 | 4.64 / 2.88 | 1.611 | 4.61 / 2.88 | 1.600 |
| 7168 | 1536 | 8 | 4.34 / 2.77 | 1.566 | 4.32 / 2.69 | 1.607 |
| 7168 | 1536 | 17 | 4.38 / 2.78 | 1.575 | 4.38 / 2.75 | 1.593 |
| 7168 | 1536 | 32 | 4.45 / 2.69 | 1.655 | 4.42 / 2.66 | 1.663 |
| 7168 | 1536 | 128 | 4.77 / 3.01 | 1.585 | 4.80 / 3.01 | 1.596 |
| 7168 | 1536 | 130 | 4.86 / 3.07 | 1.583 | 4.83 / 3.07 | 1.573 |
| 7168 | 1536 | 257 | 5.18 / 3.65 | 1.421 | 5.15 / 3.62 | 1.425 |
| 7168 | 1536 | 512 | 5.84 / 4.74 | 1.233 | 5.82 / 4.66 | 1.251 |
| 7168 | 1536 | 2048 | 12.83 / 11.17 | 1.149 | 12.74 / 11.01 | 1.157 |
| 7168 | 1536 | 8192 | 33.76 / 28.90 | 1.168 | 33.47 / 28.56 | 1.172 |
| 7168 | 2112 | 1 | 4.46 / 2.72 | 1.641 | 4.45 / 2.69 | 1.655 |
| 7168 | 2112 | 8 | 4.35 / 2.78 | 1.563 | 4.35 / 2.78 | 1.563 |
| 7168 | 2112 | 17 | 4.38 / 2.62 | 1.671 | 4.38 / 2.62 | 1.671 |
| 7168 | 2112 | 32 | 4.45 / 2.82 | 1.580 | 4.45 / 2.78 | 1.598 |
| 7168 | 2112 | 128 | 4.77 / 3.04 | 1.568 | 4.77 / 3.01 | 1.585 |
| 7168 | 2112 | 130 | 4.86 / 3.14 | 1.551 | 4.86 / 3.10 | 1.567 |
| 7168 | 2112 | 257 | 5.12 / 3.65 | 1.404 | 5.12 / 3.62 | 1.416 |
| 7168 | 2112 | 512 | 5.86 / 4.74 | 1.236 | 5.86 / 4.67 | 1.253 |
| 7168 | 2112 | 2048 | 12.80 / 11.22 | 1.141 | 12.70 / 11.04 | 1.151 |
| 7168 | 2112 | 8192 | 33.73 / 28.16 | 1.198 | 33.44 / 28.00 | 1.194 |
| 7168 | 18432 | 1 | 4.48 / 2.72 | 1.647 | 4.45 / 2.69 | 1.655 |
| 7168 | 18432 | 8 | 4.35 / 2.59 | 1.679 | 4.35 / 2.59 | 1.679 |
| 7168 | 18432 | 17 | 4.38 / 2.62 | 1.671 | 4.37 / 2.62 | 1.665 |
| 7168 | 18432 | 32 | 4.42 / 2.72 | 1.624 | 4.42 / 2.69 | 1.643 |
| 7168 | 18432 | 128 | 4.77 / 3.04 | 1.568 | 4.74 / 3.04 | 1.558 |
| 7168 | 18432 | 130 | 4.80 / 3.09 | 1.554 | 4.80 / 3.07 | 1.562 |
| 7168 | 18432 | 257 | 5.10 / 3.65 | 1.399 | 5.09 / 3.60 | 1.413 |
| 7168 | 18432 | 512 | 5.92 / 4.74 | 1.250 | 5.89 / 4.67 | 1.260 |
| 7168 | 18432 | 2048 | 12.83 / 11.34 | 1.131 | 12.70 / 11.17 | 1.138 |
| 7168 | 18432 | 8192 | 33.66 / 28.48 | 1.182 | 33.28 / 28.26 | 1.178 |
| 8192 | 8192 | 1 | 4.74 / 2.98 | 1.591 | 4.70 / 2.98 | 1.581 |
| 8192 | 8192 | 8 | 4.42 / 2.85 | 1.551 | 4.42 / 2.85 | 1.551 |
| 8192 | 8192 | 17 | 4.42 / 2.69 | 1.643 | 4.38 / 2.67 | 1.641 |
| 8192 | 8192 | 32 | 4.46 / 2.85 | 1.567 | 4.45 / 2.85 | 1.562 |
| 8192 | 8192 | 128 | 4.86 / 3.14 | 1.551 | 4.83 / 3.14 | 1.541 |
| 8192 | 8192 | 130 | 4.93 / 3.20 | 1.540 | 4.93 / 3.20 | 1.540 |
| 8192 | 8192 | 257 | 5.28 / 3.84 | 1.375 | 5.26 / 3.84 | 1.371 |
| 8192 | 8192 | 512 | 6.11 / 4.96 | 1.232 | 6.08 / 4.96 | 1.226 |
| 8192 | 8192 | 2048 | 14.27 / 11.86 | 1.204 | 14.18 / 11.86 | 1.196 |
| 8192 | 8192 | 8192 | 37.86 / 31.26 | 1.211 | 37.46 / 31.17 | 1.202 |
| 8192 | 28672 | 1 | 4.70 / 2.94 | 1.598 | 4.70 / 2.94 | 1.598 |
| 8192 | 28672 | 8 | 4.42 / 2.82 | 1.568 | 4.42 / 2.85 | 1.551 |
| 8192 | 28672 | 17 | 4.42 / 2.69 | 1.643 | 4.42 / 2.72 | 1.624 |
| 8192 | 28672 | 32 | 4.45 / 2.85 | 1.562 | 4.45 / 2.85 | 1.562 |
| 8192 | 28672 | 128 | 4.86 / 3.14 | 1.551 | 4.83 / 3.14 | 1.541 |
| 8192 | 28672 | 130 | 4.93 / 3.20 | 1.540 | 4.90 / 3.20 | 1.530 |
| 8192 | 28672 | 257 | 5.25 / 3.81 | 1.378 | 5.22 / 3.81 | 1.370 |
| 8192 | 28672 | 512 | 6.08 / 4.99 | 1.218 | 6.06 / 4.96 | 1.223 |
| 8192 | 28672 | 2048 | 14.27 / 12.00 | 1.189 | 14.14 / 11.95 | 1.183 |
| 8192 | 28672 | 8192 | 37.70 / 31.04 | 1.214 | 37.41 / 30.93 | 1.210 |
| 16384 | 7168 | 1 | 7.23 / 3.39 | 2.132 | 7.17 / 3.36 | 2.133 |
| 16384 | 7168 | 8 | 6.94 / 3.30 | 2.107 | 6.94 / 3.26 | 2.127 |
| 16384 | 7168 | 17 | 6.94 / 3.18 | 2.181 | 6.94 / 3.14 | 2.214 |
| 16384 | 7168 | 32 | 7.10 / 3.36 | 2.114 | 7.07 / 3.33 | 2.125 |
| 16384 | 7168 | 128 | 7.62 / 3.97 | 1.919 | 7.58 / 3.90 | 1.943 |
| 16384 | 7168 | 130 | 7.71 / 4.08 | 1.890 | 7.68 / 4.03 | 1.905 |
| 16384 | 7168 | 257 | 8.26 / 5.28 | 1.564 | 8.22 / 5.15 | 1.596 |
| 16384 | 7168 | 512 | 10.24 / 8.22 | 1.245 | 10.18 / 8.05 | 1.264 |
| 16384 | 7168 | 2048 | 25.81 / 22.85 | 1.130 | 25.73 / 22.40 | 1.149 |
| 16384 | 7168 | 8192 | 75.62 / 68.35 | 1.106 | 75.94 / 71.54 | 1.062 |
| 18432 | 7168 | 1 | 7.78 / 3.42 | 2.271 | 7.81 / 3.38 | 2.313 |
| 18432 | 7168 | 8 | 7.65 / 3.33 | 2.298 | 7.62 / 3.26 | 2.333 |
| 18432 | 7168 | 17 | 7.66 / 3.49 | 2.197 | 7.65 / 3.42 | 2.234 |
| 18432 | 7168 | 32 | 7.73 / 3.42 | 2.257 | 7.71 / 3.39 | 2.274 |
| 18432 | 7168 | 128 | 8.29 / 4.26 | 1.947 | 8.26 / 4.19 | 1.969 |
| 18432 | 7168 | 130 | 8.42 / 4.35 | 1.934 | 8.42 / 4.29 | 1.963 |
| 18432 | 7168 | 257 | 9.04 / 5.66 | 1.596 | 9.02 / 5.54 | 1.630 |
| 18432 | 7168 | 512 | 10.98 / 8.98 | 1.223 | 10.91 / 8.78 | 1.242 |
| 18432 | 7168 | 2048 | 28.86 / 25.54 | 1.130 | 28.77 / 24.74 | 1.163 |
| 18432 | 7168 | 8192 | 90.24 / 63.65 | 1.418 | 90.10 / 63.33 | 1.423 |
| 28672 | 8192 | 1 | 11.01 / 4.22 | 2.606 | 10.93 / 4.06 | 2.689 |
| 28672 | 8192 | 8 | 10.69 / 3.95 | 2.704 | 10.62 / 3.84 | 2.767 |
| 28672 | 8192 | 17 | 10.78 / 4.00 | 2.696 | 10.69 / 3.84 | 2.783 |
| 28672 | 8192 | 32 | 10.98 / 4.19 | 2.618 | 10.91 / 4.03 | 2.706 |
| 28672 | 8192 | 128 | 11.68 / 5.22 | 2.239 | 11.63 / 5.06 | 2.301 |
| 28672 | 8192 | 130 | 11.78 / 5.41 | 2.178 | 11.71 / 5.28 | 2.218 |
| 28672 | 8192 | 257 | 13.18 / 7.26 | 1.815 | 13.15 / 7.01 | 1.877 |
| 28672 | 8192 | 512 | 15.90 / 12.03 | 1.322 | 15.74 / 11.60 | 1.357 |
| 28672 | 8192 | 2048 | 43.78 / 34.53 | 1.268 | 43.68 / 33.09 | 1.320 |
| 28672 | 8192 | 8192 | 155.90 / 102.05 | 1.528 | 155.76 / 102.80 |
1.515 |

</details>

<details><summary><b>GEMM, per-token alpha</b> - geomean bf16 1.1096 /
fp16 1.1097; rows <= 1.00: bf16 0/80, fp16 0/80; min bf16 1.0011, fp16
1.0028</summary>

| K | N | M | bf16 base / cand us | bf16 speedup | fp16 base / cand us |
fp16 speedup |
|---|---|---|---|---|---|---|
| 7168 | 1536 | 1 | 6.77 / 5.57 | 1.216 | 6.75 / 5.55 | 1.216 |
| 7168 | 1536 | 8 | 6.85 / 5.57 | 1.230 | 6.85 / 5.57 | 1.230 |
| 7168 | 1536 | 17 | 7.39 / 5.98 | 1.235 | 7.38 / 5.98 | 1.233 |
| 7168 | 1536 | 32 | 7.36 / 6.02 | 1.223 | 7.36 / 6.02 | 1.223 |
| 7168 | 1536 | 128 | 8.22 / 8.00 | 1.028 | 8.21 / 8.02 | 1.024 |
| 7168 | 1536 | 130 | 8.10 / 7.90 | 1.024 | 8.10 / 7.90 | 1.024 |
| 7168 | 1536 | 257 | 8.10 / 7.87 | 1.028 | 8.10 / 7.90 | 1.024 |
| 7168 | 1536 | 512 | 8.29 / 8.06 | 1.028 | 8.29 / 8.06 | 1.028 |
| 7168 | 1536 | 2048 | 11.78 / 10.53 | 1.119 | 11.78 / 10.53 | 1.119 |
| 7168 | 1536 | 8192 | 34.59 / 32.94 | 1.050 | 34.53 / 32.96 | 1.048 |
| 7168 | 2112 | 1 | 7.07 / 5.95 | 1.188 | 7.06 / 5.95 | 1.185 |
| 7168 | 2112 | 8 | 7.17 / 5.92 | 1.211 | 7.17 / 5.92 | 1.211 |
| 7168 | 2112 | 17 | 7.70 / 6.69 | 1.151 | 7.68 / 6.72 | 1.143 |
| 7168 | 2112 | 32 | 7.65 / 6.40 | 1.195 | 7.65 / 6.40 | 1.195 |
| 7168 | 2112 | 128 | 8.34 / 8.13 | 1.026 | 8.35 / 8.13 | 1.028 |
| 7168 | 2112 | 130 | 8.29 / 8.22 | 1.008 | 8.29 / 8.24 | 1.006 |
| 7168 | 2112 | 257 | 8.45 / 8.22 | 1.027 | 8.45 / 8.22 | 1.027 |
| 7168 | 2112 | 512 | 8.61 / 8.37 | 1.029 | 8.64 / 8.35 | 1.034 |
| 7168 | 2112 | 2048 | 13.98 / 13.14 | 1.065 | 13.98 / 13.12 | 1.066 |
| 7168 | 2112 | 8192 | 41.39 / 40.40 | 1.025 | 41.46 / 40.38 | 1.027 |
| 7168 | 18432 | 1 | 18.18 / 16.10 | 1.129 | 18.18 / 16.10 | 1.129 |
| 7168 | 18432 | 8 | 18.30 / 16.19 | 1.130 | 18.27 / 16.22 | 1.126 |
| 7168 | 18432 | 17 | 18.24 / 16.14 | 1.130 | 18.21 / 16.16 | 1.127 |
| 7168 | 18432 | 32 | 18.18 / 16.03 | 1.134 | 18.11 / 16.03 | 1.130 |
| 7168 | 18432 | 128 | 19.36 / 16.77 | 1.155 | 19.33 / 16.77 | 1.153 |
| 7168 | 18432 | 130 | 21.02 / 18.24 | 1.153 | 21.09 / 18.26 | 1.155 |
| 7168 | 18432 | 257 | 29.98 / 24.78 | 1.210 | 30.05 / 24.83 | 1.210 |
| 7168 | 18432 | 512 | 30.51 / 25.79 | 1.183 | 30.62 / 25.79 | 1.187 |
| 7168 | 18432 | 2048 | 80.59 / 79.95 | 1.008 | 80.46 / 80.06 | 1.005 |
| 7168 | 18432 | 8192 | 293.44 / 290.14 | 1.011 | 293.54 / 290.61 |
1.010 |
| 8192 | 8192 | 1 | 10.72 / 10.18 | 1.053 | 10.72 / 10.14 | 1.057 |
| 8192 | 8192 | 8 | 10.80 / 10.24 | 1.055 | 10.78 / 10.26 | 1.051 |
| 8192 | 8192 | 17 | 11.33 / 10.86 | 1.043 | 11.34 / 10.88 | 1.043 |
| 8192 | 8192 | 32 | 11.33 / 10.78 | 1.050 | 11.34 / 10.75 | 1.055 |
| 8192 | 8192 | 128 | 12.35 / 11.23 | 1.100 | 12.29 / 11.26 | 1.091 |
| 8192 | 8192 | 130 | 13.22 / 12.22 | 1.081 | 13.18 / 12.22 | 1.079 |
| 8192 | 8192 | 257 | 17.73 / 15.65 | 1.133 | 17.76 / 15.65 | 1.135 |
| 8192 | 8192 | 512 | 18.11 / 16.03 | 1.130 | 18.16 / 16.03 | 1.133 |
| 8192 | 8192 | 2048 | 47.26 / 46.59 | 1.014 | 47.36 / 46.59 | 1.016 |
| 8192 | 8192 | 8192 | 153.23 / 151.46 | 1.012 | 153.54 / 151.70 | 1.012
|
| 8192 | 28672 | 1 | 29.60 / 24.83 | 1.192 | 29.73 / 24.98 | 1.190 |
| 8192 | 28672 | 8 | 29.54 / 25.02 | 1.180 | 29.66 / 25.06 | 1.184 |
| 8192 | 28672 | 17 | 30.27 / 25.22 | 1.200 | 30.27 / 25.22 | 1.200 |
| 8192 | 28672 | 32 | 30.18 / 25.34 | 1.191 | 30.16 / 25.31 | 1.192 |
| 8192 | 28672 | 128 | 32.69 / 27.73 | 1.179 | 32.61 / 27.71 | 1.177 |
| 8192 | 28672 | 130 | 33.41 / 27.86 | 1.199 | 33.34 / 27.87 | 1.196 |
| 8192 | 28672 | 257 | 45.84 / 38.59 | 1.188 | 46.02 / 38.61 | 1.192 |
| 8192 | 28672 | 512 | 46.69 / 40.66 | 1.148 | 46.82 / 40.75 | 1.149 |
| 8192 | 28672 | 2048 | 133.86 / 133.31 | 1.004 | 134.08 / 133.42 |
1.005 |
| 8192 | 28672 | 8192 | 512.82 / 511.30 | 1.003 | 515.62 / 512.50 |
1.006 |
| 16384 | 7168 | 1 | 17.57 / 16.67 | 1.054 | 17.57 / 16.67 | 1.054 |
| 16384 | 7168 | 8 | 17.63 / 16.74 | 1.054 | 17.66 / 16.77 | 1.053 |
| 16384 | 7168 | 17 | 19.20 / 17.84 | 1.076 | 19.20 / 17.86 | 1.075 |
| 16384 | 7168 | 32 | 19.20 / 17.89 | 1.073 | 19.23 / 17.89 | 1.075 |
| 16384 | 7168 | 128 | 20.99 / 17.41 | 1.206 | 20.99 / 17.41 | 1.206 |
| 16384 | 7168 | 130 | 22.27 / 18.78 | 1.186 | 22.27 / 18.74 | 1.189 |
| 16384 | 7168 | 257 | 27.07 / 21.71 | 1.247 | 27.10 / 21.66 | 1.251 |
| 16384 | 7168 | 512 | 27.81 / 22.21 | 1.252 | 27.81 / 22.21 | 1.252 |
| 16384 | 7168 | 2048 | 66.93 / 66.51 | 1.006 | 66.98 / 66.46 | 1.008 |
| 16384 | 7168 | 8192 | 280.14 / 278.03 | 1.008 | 280.35 / 278.35 |
1.007 |
| 18432 | 7168 | 1 | 19.47 / 18.46 | 1.055 | 19.52 / 18.46 | 1.057 |
| 18432 | 7168 | 8 | 19.58 / 18.56 | 1.055 | 19.62 / 18.54 | 1.058 |
| 18432 | 7168 | 17 | 21.12 / 19.68 | 1.073 | 21.18 / 19.68 | 1.076 |
| 18432 | 7168 | 32 | 21.25 / 19.68 | 1.080 | 21.25 / 19.71 | 1.078 |
| 18432 | 7168 | 128 | 23.14 / 19.09 | 1.212 | 23.10 / 19.07 | 1.211 |
| 18432 | 7168 | 130 | 24.46 / 20.64 | 1.185 | 24.58 / 20.59 | 1.193 |
| 18432 | 7168 | 257 | 29.87 / 23.97 | 1.246 | 29.94 / 24.03 | 1.246 |
| 18432 | 7168 | 512 | 30.46 / 24.51 | 1.243 | 30.43 / 24.51 | 1.242 |
| 18432 | 7168 | 2048 | 74.58 / 73.90 | 1.009 | 74.51 / 74.05 | 1.006 |
| 18432 | 7168 | 8192 | 319.78 / 317.58 | 1.007 | 320.37 / 317.54 |
1.009 |
| 28672 | 8192 | 1 | 31.49 / 29.78 | 1.058 | 31.42 / 29.73 | 1.057 |
| 28672 | 8192 | 8 | 31.58 / 29.86 | 1.058 | 31.52 / 29.76 | 1.059 |
| 28672 | 8192 | 17 | 33.68 / 30.94 | 1.088 | 33.63 / 30.94 | 1.087 |
| 28672 | 8192 | 32 | 33.63 / 30.98 | 1.086 | 33.70 / 30.98 | 1.088 |
| 28672 | 8192 | 128 | 35.98 / 28.83 | 1.248 | 35.98 / 28.86 | 1.247 |
| 28672 | 8192 | 130 | 37.81 / 30.45 | 1.242 | 37.81 / 30.53 | 1.238 |
| 28672 | 8192 | 257 | 49.42 / 40.90 | 1.209 | 49.34 / 40.83 | 1.208 |
| 28672 | 8192 | 512 | 50.08 / 42.18 | 1.187 | 50.34 / 42.13 | 1.195 |
| 28672 | 8192 | 2048 | 147.06 / 146.90 | 1.001 | 147.26 / 146.85 |
1.003 |
| 28672 | 8192 | 8192 | 568.30 / 566.82 | 1.003 | 570.69 / 567.76 |
1.005 |

</details>

<details><summary><b>Fused quantize + GEMM (CUDA Graph, PDL)</b> -
geomean bf16 1.2240 / fp16 1.2244; rows <= 1.00: bf16 0/80, fp16 0/80;
min bf16 1.0139, fp16 1.0012</summary>

| K | N | M | bf16 base / cand us | bf16 speedup | fp16 base / cand us |
fp16 speedup |
|---|---|---|---|---|---|---|
| 7168 | 1536 | 1 | 11.39 / 7.94 | 1.435 | 11.36 / 7.90 | 1.437 |
| 7168 | 1536 | 8 | 11.62 / 8.42 | 1.380 | 11.57 / 8.38 | 1.380 |
| 7168 | 1536 | 17 | 11.84 / 8.45 | 1.402 | 11.81 / 8.48 | 1.392 |
| 7168 | 1536 | 32 | 12.13 / 8.86 | 1.368 | 12.10 / 8.85 | 1.367 |
| 7168 | 1536 | 128 | 12.91 / 10.66 | 1.212 | 12.86 / 10.66 | 1.207 |
| 7168 | 1536 | 130 | 13.18 / 10.91 | 1.208 | 13.18 / 10.94 | 1.205 |
| 7168 | 1536 | 257 | 13.28 / 11.39 | 1.166 | 13.25 / 11.36 | 1.166 |
| 7168 | 1536 | 512 | 13.66 / 12.10 | 1.130 | 13.63 / 12.08 | 1.128 |
| 7168 | 1536 | 2048 | 24.32 / 21.65 | 1.123 | 24.27 / 21.63 | 1.122 |
| 7168 | 1536 | 8192 | 65.15 / 58.40 | 1.116 | 64.80 / 58.02 | 1.117 |
| 7168 | 2112 | 1 | 11.49 / 8.19 | 1.402 | 11.46 / 8.22 | 1.393 |
| 7168 | 2112 | 8 | 11.97 / 8.74 | 1.370 | 11.97 / 8.74 | 1.370 |
| 7168 | 2112 | 17 | 12.19 / 9.15 | 1.332 | 12.19 / 9.15 | 1.332 |
| 7168 | 2112 | 32 | 12.42 / 9.17 | 1.354 | 12.42 / 9.15 | 1.357 |
| 7168 | 2112 | 128 | 12.93 / 10.69 | 1.210 | 12.93 / 10.66 | 1.213 |
| 7168 | 2112 | 130 | 12.99 / 10.91 | 1.191 | 12.98 / 10.91 | 1.189 |
| 7168 | 2112 | 257 | 13.26 / 11.39 | 1.164 | 13.28 / 11.36 | 1.169 |
| 7168 | 2112 | 512 | 14.18 / 12.51 | 1.133 | 14.14 / 12.51 | 1.130 |
| 7168 | 2112 | 2048 | 26.70 / 24.11 | 1.107 | 26.62 / 23.98 | 1.110 |
| 7168 | 2112 | 8192 | 71.52 / 65.15 | 1.098 | 71.31 / 64.61 | 1.104 |
| 7168 | 18432 | 1 | 22.66 / 18.66 | 1.214 | 22.69 / 18.67 | 1.215 |
| 7168 | 18432 | 8 | 22.54 / 18.53 | 1.217 | 22.54 / 18.59 | 1.213 |
| 7168 | 18432 | 17 | 22.98 / 18.72 | 1.227 | 22.91 / 18.72 | 1.224 |
| 7168 | 18432 | 32 | 23.01 / 18.72 | 1.229 | 22.99 / 18.72 | 1.228 |
| 7168 | 18432 | 128 | 23.84 / 19.14 | 1.246 | 23.78 / 19.18 | 1.239 |
| 7168 | 18432 | 130 | 26.00 / 21.09 | 1.233 | 25.97 / 21.09 | 1.231 |
| 7168 | 18432 | 257 | 34.54 / 28.03 | 1.232 | 34.75 / 28.02 | 1.240 |
| 7168 | 18432 | 512 | 35.63 / 29.87 | 1.193 | 35.79 / 29.82 | 1.200 |
| 7168 | 18432 | 2048 | 92.48 / 90.47 | 1.022 | 92.38 / 90.32 | 1.023 |
| 7168 | 18432 | 8192 | 323.66 / 316.05 | 1.024 | 323.65 / 316.37 |
1.023 |
| 8192 | 8192 | 1 | 16.06 / 12.83 | 1.252 | 16.08 / 12.80 | 1.256 |
| 8192 | 8192 | 8 | 15.49 / 12.70 | 1.219 | 15.47 / 12.64 | 1.224 |
| 8192 | 8192 | 17 | 16.29 / 13.39 | 1.216 | 16.26 / 13.38 | 1.215 |
| 8192 | 8192 | 32 | 16.38 / 13.50 | 1.213 | 16.29 / 13.47 | 1.209 |
| 8192 | 8192 | 128 | 17.58 / 14.30 | 1.229 | 17.49 / 14.30 | 1.223 |
| 8192 | 8192 | 130 | 18.53 / 15.38 | 1.205 | 18.50 / 15.34 | 1.205 |
| 8192 | 8192 | 257 | 23.33 / 19.30 | 1.209 | 23.23 / 19.36 | 1.200 |
| 8192 | 8192 | 512 | 24.70 / 20.62 | 1.198 | 24.66 / 20.61 | 1.196 |
| 8192 | 8192 | 2048 | 60.61 / 57.70 | 1.050 | 60.69 / 57.66 | 1.052 |
| 8192 | 8192 | 8192 | 187.91 / 178.67 | 1.052 | 188.29 / 178.86 | 1.053
|
| 8192 | 28672 | 1 | 34.50 / 27.36 | 1.261 | 34.62 / 27.39 | 1.264 |
| 8192 | 28672 | 8 | 34.19 / 27.26 | 1.254 | 34.29 / 27.25 | 1.258 |
| 8192 | 28672 | 17 | 34.46 / 27.30 | 1.263 | 34.46 / 27.30 | 1.263 |
| 8192 | 28672 | 32 | 35.07 / 28.03 | 1.251 | 35.10 / 28.03 | 1.252 |
| 8192 | 28672 | 128 | 37.12 / 30.14 | 1.231 | 37.09 / 30.18 | 1.229 |
| 8192 | 28672 | 130 | 38.10 / 30.59 | 1.245 | 38.08 / 30.53 | 1.247 |
| 8192 | 28672 | 257 | 50.58 / 41.87 | 1.208 | 50.69 / 41.86 | 1.211 |
| 8192 | 28672 | 512 | 51.74 / 44.62 | 1.160 | 51.84 / 44.80 | 1.157 |
| 8192 | 28672 | 2048 | 147.44 / 143.97 | 1.024 | 147.57 / 144.67 |
1.020 |
| 8192 | 28672 | 8192 | 547.26 / 539.71 | 1.014 | 551.01 / 541.70 |
1.017 |
| 16384 | 7168 | 1 | 25.33 / 19.41 | 1.305 | 25.30 / 19.39 | 1.304 |
| 16384 | 7168 | 8 | 25.09 / 19.55 | 1.283 | 25.10 / 19.52 | 1.286 |
| 16384 | 7168 | 17 | 26.45 / 20.48 | 1.291 | 26.43 / 20.45 | 1.293 |
| 16384 | 7168 | 32 | 26.56 / 20.64 | 1.287 | 26.48 / 20.64 | 1.283 |
| 16384 | 7168 | 128 | 28.70 / 20.77 | 1.382 | 28.64 / 20.80 | 1.377 |
| 16384 | 7168 | 130 | 30.26 / 22.72 | 1.332 | 30.16 / 22.69 | 1.329 |
| 16384 | 7168 | 257 | 35.62 / 26.40 | 1.349 | 35.58 / 26.30 | 1.353 |
| 16384 | 7168 | 512 | 38.11 / 30.02 | 1.270 | 38.13 / 29.89 | 1.276 |
| 16384 | 7168 | 2048 | 89.95 / 86.35 | 1.042 | 89.95 / 86.30 | 1.042 |
| 16384 | 7168 | 8192 | 351.01 / 346.21 | 1.014 | 350.64 / 350.21 |
1.001 |
| 18432 | 7168 | 1 | 27.52 / 21.09 | 1.305 | 27.47 / 21.06 | 1.305 |
| 18432 | 7168 | 8 | 27.46 / 21.09 | 1.302 | 27.41 / 21.12 | 1.298 |
| 18432 | 7168 | 17 | 29.12 / 22.37 | 1.302 | 29.09 / 22.37 | 1.300 |
| 18432 | 7168 | 32 | 29.52 / 22.85 | 1.292 | 29.47 / 22.85 | 1.290 |
| 18432 | 7168 | 128 | 31.26 / 22.53 | 1.388 | 31.22 / 22.51 | 1.387 |
| 18432 | 7168 | 130 | 33.07 / 24.59 | 1.345 | 32.93 / 24.50 | 1.344 |
| 18432 | 7168 | 257 | 38.69 / 28.80 | 1.343 | 38.85 / 28.80 | 1.349 |
| 18432 | 7168 | 512 | 40.96 / 32.45 | 1.262 | 40.77 / 32.29 | 1.263 |
| 18432 | 7168 | 2048 | 100.16 / 96.48 | 1.038 | 100.31 / 95.95 | 1.045
|
| 18432 | 7168 | 8192 | 404.06 / 376.02 | 1.075 | 404.82 / 375.30 |
1.079 |
| 28672 | 8192 | 1 | 42.54 / 33.20 | 1.281 | 42.40 / 32.99 | 1.285 |
| 28672 | 8192 | 8 | 42.13 / 32.88 | 1.281 | 42.08 / 32.77 | 1.284 |
| 28672 | 8192 | 17 | 44.32 / 34.14 | 1.298 | 44.26 / 33.95 | 1.304 |
| 28672 | 8192 | 32 | 44.56 / 34.53 | 1.291 | 44.56 / 34.34 | 1.298 |
| 28672 | 8192 | 128 | 46.90 / 32.99 | 1.421 | 46.86 / 32.82 | 1.428 |
| 28672 | 8192 | 130 | 48.67 / 34.98 | 1.392 | 48.64 / 34.85 | 1.396 |
| 28672 | 8192 | 257 | 61.73 / 47.33 | 1.304 | 61.65 / 47.12 | 1.308 |
| 28672 | 8192 | 512 | 64.16 / 53.39 | 1.202 | 64.42 / 53.02 | 1.215 |
| 28672 | 8192 | 2048 | 187.15 / 176.64 | 1.060 | 187.50 / 175.30 |
1.070 |
| 28672 | 8192 | 8192 | 724.70 / 670.59 | 1.081 | 723.60 / 674.66 |
1.073 |

</details>

<details><summary><b>GEMM, scalar alpha (A/A no-regression check; low-M
rows now take split-K)</b> - geomean bf16 1.1010 / fp16 1.1008; rows <=
1.00: bf16 13/80, fp16 14/80; min bf16 0.9826, fp16 0.9845</summary>

| K | N | M | bf16 base / cand us | bf16 speedup | fp16 base / cand us |
fp16 speedup |
|---|---|---|---|---|---|---|
| 7168 | 1536 | 1 | 6.75 / 5.57 | 1.213 | 6.75 / 5.57 | 1.213 |
| 7168 | 1536 | 8 | 6.75 / 5.57 | 1.213 | 6.72 / 5.54 | 1.214 |
| 7168 | 1536 | 17 | 7.28 / 5.95 | 1.223 | 7.30 / 5.95 | 1.226 |
| 7168 | 1536 | 32 | 7.26 / 5.98 | 1.214 | 7.26 / 5.98 | 1.214 |
| 7168 | 1536 | 128 | 8.03 / 8.03 | 1.000 (<=1) | 8.03 / 8.03 | 1.000
(<=1) |
| 7168 | 1536 | 130 | 7.94 / 7.94 | 1.000 (<=1) | 7.94 / 7.94 | 1.000
(<=1) |
| 7168 | 1536 | 257 | 7.94 / 7.95 | 0.998 (<=1) | 7.92 / 7.94 | 0.998
(<=1) |
| 7168 | 1536 | 512 | 8.10 / 8.10 | 1.000 (<=1) | 8.10 / 8.10 | 1.000
(<=1) |
| 7168 | 1536 | 2048 | 11.39 / 10.56 | 1.079 | 11.39 / 10.56 | 1.079 |
| 7168 | 1536 | 8192 | 33.70 / 32.98 | 1.022 | 33.74 / 32.99 | 1.023 |
| 7168 | 2112 | 1 | 7.07 / 5.95 | 1.188 | 7.07 / 5.95 | 1.188 |
| 7168 | 2112 | 8 | 7.07 / 5.92 | 1.195 | 7.04 / 5.95 | 1.183 |
| 7168 | 2112 | 17 | 7.58 / 6.66 | 1.139 | 7.58 / 6.66 | 1.139 |
| 7168 | 2112 | 32 | 7.58 / 6.34 | 1.197 | 7.55 / 6.34 | 1.192 |
| 7168 | 2112 | 128 | 8.16 / 8.16 | 1.000 (<=1) | 8.16 / 8.16 | 1.000
(<=1) |
| 7168 | 2112 | 130 | 8.13 / 8.27 | 0.983 (<=1) | 8.13 / 8.26 | 0.984
(<=1) |
| 7168 | 2112 | 257 | 8.29 / 8.29 | 1.000 (<=1) | 8.29 / 8.29 | 1.000
(<=1) |
| 7168 | 2112 | 512 | 8.42 / 8.42 | 1.000 (<=1) | 8.38 / 8.40 | 0.998
(<=1) |
| 7168 | 2112 | 2048 | 13.60 / 13.15 | 1.034 | 13.60 / 13.15 | 1.034 |
| 7168 | 2112 | 8192 | 41.28 / 40.38 | 1.022 | 41.31 / 40.35 | 1.024 |
| 7168 | 18432 | 1 | 18.18 / 16.06 | 1.131 | 18.11 / 16.10 | 1.125 |
| 7168 | 18432 | 8 | 18.24 / 16.10 | 1.133 | 18.18 / 16.13 | 1.127 |
| 7168 | 18432 | 17 | 18.14 / 16.06 | 1.129 | 18.14 / 16.06 | 1.129 |
| 7168 | 18432 | 32 | 18.06 / 15.94 | 1.134 | 18.02 / 15.97 | 1.128 |
| 7168 | 18432 | 128 | 19.41 / 16.77 | 1.157 | 19.28 / 16.74 | 1.152 |
| 7168 | 18432 | 130 | 20.77 / 18.26 | 1.138 | 20.83 / 18.24 | 1.142 |
| 7168 | 18432 | 257 | 29.66 / 24.86 | 1.193 | 29.76 / 24.90 | 1.195 |
| 7168 | 18432 | 512 | 30.27 / 25.79 | 1.174 | 30.26 / 25.82 | 1.172 |
| 7168 | 18432 | 2048 | 80.27 / 79.95 | 1.004 | 80.22 / 80.05 | 1.002 |
| 7168 | 18432 | 8192 | 290.45 / 290.02 | 1.001 | 291.31 / 290.46 |
1.003 |
| 8192 | 8192 | 1 | 10.75 / 10.18 | 1.057 | 10.69 / 10.16 | 1.052 |
| 8192 | 8192 | 8 | 10.72 / 10.14 | 1.057 | 10.72 / 10.14 | 1.057 |
| 8192 | 8192 | 17 | 11.23 / 10.72 | 1.048 | 11.26 / 10.75 | 1.048 |
| 8192 | 8192 | 32 | 11.23 / 10.66 | 1.054 | 11.23 / 10.66 | 1.054 |
| 8192 | 8192 | 128 | 12.16 / 11.26 | 1.080 | 12.13 / 11.30 | 1.074 |
| 8192 | 8192 | 130 | 13.09 / 12.22 | 1.071 | 13.09 / 12.21 | 1.072 |
| 8192 | 8192 | 257 | 17.50 / 15.71 | 1.114 | 17.50 / 15.74 | 1.112 |
| 8192 | 8192 | 512 | 17.89 / 16.06 | 1.114 | 17.92 / 16.06 | 1.116 |
| 8192 | 8192 | 2048 | 46.96 / 46.59 | 1.008 | 46.99 / 46.62 | 1.008 |
| 8192 | 8192 | 8192 | 151.79 / 151.41 | 1.003 | 152.02 / 151.68 | 1.002
|
| 8192 | 28672 | 1 | 29.57 / 24.93 | 1.186 | 29.70 / 24.91 | 1.192 |
| 8192 | 28672 | 8 | 29.57 / 25.06 | 1.180 | 29.71 / 25.06 | 1.186 |
| 8192 | 28672 | 17 | 30.19 / 25.15 | 1.200 | 30.29 / 25.20 | 1.202 |
| 8192 | 28672 | 32 | 30.24 / 25.28 | 1.196 | 30.18 / 25.30 | 1.193 |
| 8192 | 28672 | 128 | 32.51 / 27.76 | 1.171 | 32.38 / 27.74 | 1.167 |
| 8192 | 28672 | 130 | 33.42 / 27.94 | 1.196 | 33.38 / 27.84 | 1.199 |
| 8192 | 28672 | 257 | 45.63 / 38.62 | 1.181 | 45.78 / 38.69 | 1.183 |
| 8192 | 28672 | 512 | 46.59 / 40.77 | 1.143 | 46.72 / 40.77 | 1.146 |
| 8192 | 28672 | 2048 | 133.60 / 133.41 | 1.001 | 133.70 / 133.70 |
1.000 (<=1) |
| 8192 | 28672 | 8192 | 511.55 / 512.14 | 0.999 (<=1) | 513.62 / 513.20
| 1.001 |
| 16384 | 7168 | 1 | 17.57 / 16.69 | 1.053 | 17.57 / 16.67 | 1.054 |
| 16384 | 7168 | 8 | 17.55 / 16.70 | 1.051 | 17.55 / 16.69 | 1.052 |
| 16384 | 7168 | 17 | 19.04 / 17.84 | 1.067 | 19.10 / 17.82 | 1.072 |
| 16384 | 7168 | 32 | 19.14 / 17.86 | 1.072 | 19.14 / 17.89 | 1.070 |
| 16384 | 7168 | 128 | 20.85 / 17.44 | 1.195 | 20.83 / 17.47 | 1.192 |
| 16384 | 7168 | 130 | 22.16 / 18.78 | 1.180 | 22.18 / 18.78 | 1.181 |
| 16384 | 7168 | 257 | 27.01 / 21.73 | 1.243 | 27.04 / 21.79 | 1.241 |
| 16384 | 7168 | 512 | 27.70 / 22.21 | 1.247 | 27.71 / 22.24 | 1.246 |
| 16384 | 7168 | 2048 | 66.66 / 66.46 | 1.003 | 66.54 / 66.56 | 1.000
(<=1) |
| 16384 | 7168 | 8192 | 277.36 / 277.65 | 0.999 (<=1) | 278.34 / 277.30
| 1.004 |
| 18432 | 7168 | 1 | 19.46 / 18.46 | 1.054 | 19.52 / 18.45 | 1.058 |
| 18432 | 7168 | 8 | 19.49 / 18.46 | 1.055 | 19.49 / 18.48 | 1.055 |
| 18432 | 7168 | 17 | 21.12 / 19.68 | 1.073 | 21.12 / 19.65 | 1.075 |
| 18432 | 7168 | 32 | 21.15 / 19.68 | 1.075 | 21.17 / 19.68 | 1.076 |
| 18432 | 7168 | 128 | 22.94 / 19.14 | 1.199 | 22.93 / 19.17 | 1.196 |
| 18432 | 7168 | 130 | 24.32 / 20.61 | 1.180 | 24.38 / 20.64 | 1.181 |
| 18432 | 7168 | 257 | 29.76 / 24.03 | 1.238 | 29.79 / 24.05 | 1.239 |
| 18432 | 7168 | 512 | 30.37 / 24.58 | 1.236 | 30.37 / 24.51 | 1.239 |
| 18432 | 7168 | 2048 | 74.03 / 73.95 | 1.001 | 74.06 / 74.19 | 0.998
(<=1) |
| 18432 | 7168 | 8192 | 316.31 / 317.07 | 0.998 (<=1) | 316.98 / 317.10
| 1.000 (<=1) |
| 28672 | 8192 | 1 | 31.49 / 29.78 | 1.057 | 31.39 / 29.79 | 1.054 |
| 28672 | 8192 | 8 | 31.54 / 29.76 | 1.060 | 31.42 / 29.76 | 1.056 |
| 28672 | 8192 | 17 | 33.57 / 30.88 | 1.087 | 33.57 / 30.88 | 1.087 |
| 28672 | 8192 | 32 | 33.60 / 30.96 | 1.085 | 33.63 / 30.98 | 1.086 |
| 28672 | 8192 | 128 | 35.78 / 28.86 | 1.239 | 35.78 / 28.90 | 1.238 |
| 28672 | 8192 | 130 | 37.66 / 30.53 | 1.234 | 37.74 / 30.53 | 1.236 |
| 28672 | 8192 | 257 | 49.15 / 40.93 | 1.201 | 49.06 / 40.93 | 1.199 |
| 28672 | 8192 | 512 | 49.89 / 42.21 | 1.182 | 50.13 / 42.14 | 1.189 |
| 28672 | 8192 | 2048 | 146.93 / 146.96 | 1.000 (<=1) | 146.82 / 147.02
| 0.999 (<=1) |
| 28672 | 8192 | 8192 | 567.01 / 567.02 | 1.000 (<=1) | 567.55 / 568.00
| 0.999 (<=1) |

</details>

## Correctness

- Quantize: fp4 / SF / per-token scale bitwise identical to #5504 on all
rows, both GPUs, both input dtypes
(`tests/utils/test_fp4_quantize.py::test_nvfp4_quantize_per_token_cute_dsl_wide_rows`
adds K in {1536..69632}, M in {1, 17, 130}, all SF layouts).
- GEMM: outputs bitwise identical to #5504 on all 80 rows per GPU and
dtype (the K tile 512 variant keeps the MMA instruction order; the
split-K rows were observed bitwise identical on every measured row and
are required to match within bf16/fp16 atol=rtol=1e-2). New
`tests/gemm/test_mm_fp4.py::test_mm_fp4_per_token_alpha_splitk` (incl.
the 8-wide token tile over several N tiles),
`::test_mm_fp4_per_token_alpha_deep_k` and
`::test_mm_fp4_per_token_alpha_low_m_untuned` check the per-token row
scaling, the sum against the cutlass backend and the tactic the untuned
path selects; `::test_mm_fp4_weight_l2_policy_rule` pins the L2-policy
rule and `tests/jit/test_cute_dsl_cache.py` checks the policy is part of
the on-disk kernel name.
- Scalar-alpha path: same kernel binaries as the per-token path minus
the per-token epilogue (the L2 policies and the untuned low-M split-K /
K-tile rules apply to both), re-measured on both GPUs (scalar A/A tables
above): geomean 1.09-1.10, low-M rows 1.03-1.24; the ~8 us
7168x{1536,2112} rows sit at 0.985-1.00 within run noise (7168x2112 M =
130 read 0.983-0.989 in the 6-round finals and 1.000 in a stand-alone
6-round re-measurement of the same kernel).
- compute-sanitizer memcheck (pytorch:26.07, B200 and GB300): 0 errors
on eight public-API cases (quantize with and without `out_scale`,
persistent per-token GEMM in both orientations, the K tile 512 variant,
split-K incl. the 8-wide token tile, tails M = 17/130/257, bf16 and fp16
outputs). synccheck reports the `Divergent thread(s) in block` class and
stops the target with a launch failure on every CuTe-DSL tcgen05 GEMM
kernel of the unchanged #5504 tree as well (persistent per-token kernel,
upstream MXFP8 split-K kernel), so that report is pre-existing tool
behaviour, not introduced here; the quantize kernel is synccheck-clean.

## 🧪 Tests

- [x] `tests/gemm/test_mm_fp4.py`, `tests/utils/test_fp4_quantize.py`,
`tests/jit/test_cute_dsl_cache.py` on B200 and GB300
- [x] pre-commit hooks

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved NVFP4 quantization performance across a wider range of row
sizes.
* Added optimized FP4 matrix multiplication paths for workloads with
small output dimensions or large reduction dimensions.
* **New Features**
* Expanded per-token scaling support for FP4 matrix multiplication,
including split-K workloads.
* Added support for additional tile configurations to handle narrower
output dimensions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1157cf9](https://github.com/flashinfer-ai/flashinfer/commit/1157cf9259b70765562057a75b9e45497775a108)

- **作者**: eigen
- **时间**: 2026-09-27T19:08:14Z
- **提交信息**: feat(cake_latent_moe): Kimi-K3 TP12 fused LatentMoE tail for GB200 / GB300 NVL72, kimi_k3_tp12_tail) (#5603)

## Summary

Adds `flashinfer.kimi_k3_tp12_tail` (`backend="cake"`): the fused
Kimi-K3 TP12 LatentMoE communication tail for
three-tray GB200 / GB300 NVL72 tensor-parallel groups (twelve ranks, one
NVLink domain), requested in #4542.

The operator: `latent = KimiRMSNorm(sum_r routed_partial_r)` (`[M,
3584]`), then
`out = BF16(latent @ up_weight.T + sum_r shared_partial_r)` (`[M,
7168]`), bitwise identical on every rank.
The stock chain issues two NCCL all-reduces, `flashinfer.norm.rmsnorm`,
the replicated cuBLAS up-projection and an
add. The fused tail launches three kernels per rank on the current
stream (CUDA-Graph capturable, no allocation):

- **K1** twelve-rank Lamport all-reduce + RMSNorm over multicast
symmetric memory (one-shot per-rank variant for
`M <= 16`, token-sliced two-shot owner reduce + multicast broadcast
above), producing the normalised latent on
  every rank;
- **K2** cuBLAS `torch.mm` on the rank's contiguous slice of the
up-projection weight (`7168 = 8 x 640 + 4 x 512`
  output columns; no weight replication of work);
- **K3** column reduce-scatter of the shared-expert partials + add of
the GEMM slice + one BF16 rounding + multicast
  all-gather of the twelve column slices (grid `(M, 2) x 448`).

All three workspaces reuse `MNNVLAllReduceFusionWorkspace` (FlashInfer's
MNNVL multicast allocator, negative-zero
Lamport initialisation, nine-word flags). Programmatic dependent launch
is on for every kernel.

## Files

- `flashinfer/kimi_k3_tp12_tail.py` — public entry points
(`create_kimi_k3_tp12_tail_workspace`,
  `prepare_kimi_k3_tp12_tail`, `kimi_k3_tp12_tail`; experimental API).
- `flashinfer/experimental/kimi_k3_tp12_tail/cake_backend.py`,
`cake_jit.py`, `csrc/` — host runtime, JIT specs and
the generated CUDA programs (16 per architecture: 12 rank-specialised
one-shot K1, two-shot K1 and K3 in the
  grouped and pinned poll schedules; `sm_100a`, `sm_103a`).
- `tests/experimental/test_cake_kimi_k3_tp12_tail.py` — CPU tests
(partition, routing, sizing, validation, generated
module inventory) and the twelve-rank GPU test (reference at `atol =
rtol = 1e-2`, rank invariance, idempotence,
  CUDA-graph replay, capacity error).
- `benchmarks/bench_cake_kimi_k3_tp12_tail.py` — twelve-rank torchrun
benchmark, stock chain versus fused (CUPTI,
  rank-max medians, counterbalanced groups).

## Results

Rank-max median GPU time per call (CUPTI, cold L2, CUDA graphs, twelve
ranks on three trays of one NVLink domain).
Stock = NCCL all-reduce -> `flashinfer.norm.rmsnorm` -> cuBLAS
`torch.mm` (replicated up-projection) -> NCCL
all-reduce -> `torch.add`, captured in one CUDA graph (the fastest stock
route of every stage on both racks).

### GB300 NVL72 (sm_103a)

| M | stock chain us | fused (this PR) us | speedup | source/export
parity |
|---|---|---|---|---|
| 1 | 114.9 | 25.8 | 4.45x | 1.0279 |
| 8 | 118.1 | 25.0 | 4.72x | 1.0064 |
| 32 | 119.7 | 27.4 | 4.38x | 1.0047 |
| 64 | 120.1 | 28.3 | 4.25x | 0.9978 |
| 128 | 135.8 | 31.5 | 4.31x | 1.0005 |
| 256 | 144.2 | 42.3 | 3.41x | 1.0031 |
| 512 | 178.9 | 64.9 | 2.76x | 0.9970 |
| 1024 | 254.1 | 104.1 | 2.44x | 1.0000 |
| 2048 | 367.7 | 186.8 | 1.97x | 1.0009 |
| 4096 | 591.8 | 353.3 | 1.67x | 0.9997 |

### GB200 NVL72 (sm_100a)

| M | stock chain us | fused (this PR) us | speedup | source/export
parity |
|---|---|---|---|---|
| 1 | 118.7 | 25.4 | 4.66x | 0.9963 |
| 8 | 119.7 | 25.5 | 4.69x | 0.9937 |
| 32 | 121.8 | 27.9 | 4.37x | 1.0006 |
| 64 | 122.1 | 29.1 | 4.20x | 0.9989 |
| 128 | 137.8 | 31.6 | 4.36x | 1.0015 |
| 256 | 148.0 | 43.5 | 3.41x | 0.9919 |
| 512 | 183.3 | 65.7 | 2.79x | 0.9985 |
| 1024 | 259.8 | 104.1 | 2.50x | 1.0015 |
| 2048 | 406.0 | 189.7 | 2.14x | 0.9991 |
| 4096 | 629.9 | 355.4 | 1.77x | 1.0009 |

Correctness (both racks, every row plus `M in {2, 3, 4, 16, 8192}`): 0
violations at `atol = rtol = 1e-2` against an
fp32 reference, finite, bitwise identical across the twelve ranks,
idempotent (Lamport buffers rotate and clear
themselves), CUDA-graph replay bitwise identical to the eager launch;
the FlashInfer runtime and the Cake source
runtime produce bitwise identical outputs on every rank.
compute-sanitizer: memcheck at M = 1, 8, 32, 512 and synccheck at M = 1,
8: 12/12 ranks `ERROR SUMMARY: 0 errors` (GB300, twelve ranks,
`nvcr.io/nvidia/pytorch:26.07-py3`); synccheck at M = 32, 512 filtered
to the Cake kernels (`--kernel-regex kns=kimi_k3_tp12`): 12/12 ranks 0
errors — the unfiltered run at those rows reports only "Divergent
thread(s) in block" inside NCCL `AllGather_RING_SIMPLE` / `RING_LL`
launched by the test harness's own `all_gather` (reference /
rank-invariance gathers), not by any kernel of this PR.

### FlashInfer-side test and benchmark on the delivered tree

FlashInfer-side validation on the delivered tree (same trays,
`nvcr.io/nvidia/sglang:26.07-py3`): the CPU inventory tests (5 passed)
and the twelve-rank GPU test
`tests/experimental/test_cake_kimi_k3_tp12_tail.py -k twelve_ranks`
(rows M = 1, 8, 16, 32, 128, 300: reference at 1e-2, rank invariance,
idempotence, CUDA-graph replay, `max_tokens` guard) pass on GB300 and
GB200; `benchmarks/bench_cake_kimi_k3_tp12_tail.py` (`--M 1 .. 4096`, 50
warmup + 200 iterations x 3 counterbalanced groups,
`bench_gpu_time_with_cupti`; every iteration's span is gathered from all
ranks and the row time is the median over iterations of the maximum over
ranks) reports every row faster than the stock chain (the max abs
difference against the stock chain's own output is one BF16 ulp of the
stock chain's ring-rounded result):

| M | GB200 stock us | GB200 fused us | speedup | GB300 stock us | GB300
fused us | speedup | max abs diff vs stock |
|---|---|---|---|---|---|---|---|
| 1 | 116.1 | 24.8 | 4.67 | 111.4 | 24.8 | 4.49 | 0.0156 |
| 8 | 125.3 | 24.5 | 5.11 | 121.7 | 24.0 | 5.08 | 0.0312 |
| 32 | 126.8 | 26.8 | 4.72 | 123.0 | 25.6 | 4.81 | 0.0312 |
| 64 | 127.0 | 27.6 | 4.61 | 124.4 | 27.4 | 4.54 | 0.0312 |
| 128 | 139.9 | 31.1 | 4.50 | 137.3 | 29.7 | 4.62 | 0.0312 |
| 256 | 152.4 | 44.6 | 3.41 | 149.3 | 41.7 | 3.58 | 0.0312 |
| 512 | 186.6 | 64.1 | 2.91 | 182.5 | 63.1 | 2.89 | 0.0312 |
| 1024 | 259.2 | 103.7 | 2.50 | 251.3 | 102.4 | 2.45 | 0.0312 |
| 2048 | 418.7 | 188.2 | 2.22 | 376.7 | 186.8 | 2.02 | 0.0312 |
| 4096 | 645.3 | 353.9 | 1.82 | 604.5 | 352.3 | 1.72 | 0.0312 |

The benchmark's teardown aborts the NCCL process group after the final
barrier instead of calling `destroy_process_group()`: the NCCL
collectives captured into the stock-chain CUDA graphs leave their work
objects pending in the process group, and the destroy call then waits
without end (torch 2.13 / CUDA 13.3; every rank was stuck in
`destroy_process_group` on both racks under `faulthandler`).

The benchmark's `per_rank_us` / `rank_spread_us` fields hold every
rank's own CUPTI median: `bench_gpu_time_with_cupti` aggregates the
per-iteration spans across the initialised process group itself
(elementwise max by default, which made a first version report twelve
identical "per-rank" medians), so the benchmark passes an `aggregate_op`
that keeps each rank's span and takes the rank maximum per iteration
itself. Verified on GB200 (twelve ranks, rc = 0 on all three trays,
10/10 rows faster, 4.90x at M = 1 to 1.81x at M = 4096; per-rank medians
spread 3.5-6.2 us on the stock chain and 3.8-5.8 us on the fused path,
each rank's own median below the rank-max row time).

## Baselines and their source PRs

- `flashinfer.norm.rmsnorm` (stock-chain normalisation): introduced in
#207 (`3e515a475`, 2024-04-21; kernel
`include/flashinfer/norm.cuh`, binding `csrc/norm.cu`), Python module
layout from #643 (`8e3d25874`, 2024-12-10).
- NCCL all-reduce via
`torch.distributed._functional_collectives.all_reduce` and cuBLAS
`torch.mm` / `torch.add`:
PyTorch 2.13.0a0+9186a08b2c.nv26.07 (CUDA 13.3) (container
`nvcr.io/nvidia/sglang:26.07-py3`), NCCL 2.30.7.
- Reused FlashInfer infrastructure (not a baseline):
`MNNVLAllReduceFusionWorkspace` from #2130 (`fd0c2f124`,
2025-12-17) on the MNNVL all-reduce allocator of #1213 (`a03c2909d`,
2025-07-10), two-shot workspace stages per
  #4473 (`b8c21928b`, 2026-08-13).
- Branch merge-base with `main`: `d97b1801c` (#5455, 2026-09-26). No
upstream commit after the merge-base touches
`flashinfer/norm.py`, `csrc/norm.cu`, `include/flashinfer/norm.cuh`,
`flashinfer/comm/trtllm_mnnvl_ar.py`,
`include/flashinfer/comm/trtllm_mnnvl_allreduce.cuh`,
`csrc/trtllm_mnnvl_allreduce.cu` or `flashinfer/comm/mnnvl.py`
(`git log d97b1801c..origin/main -- <files>` is empty as of 8589d49b0).

## Evidence

Every measurement above comes from the generated-program export protocol
of the Cake repository (frozen protocol
`kimi_k3_tp12_tail_perf_10x2`: twenty shapes, arms `source` / `exported`
/ `stock`, 3 groups x 300 warmup + 600
samples per arm, source/export parity gate `>= 0.97`). Receipts stay on
the measuring clusters; the manifest (host,
path, size, SHA-256) is kept with the internal export receipts.

Delivered-tree archives and protocol summaries (the GB200 and GB300 runs
delivered byte-identical trees; `applied.json`
lists the 65 delivered files with their SHA-256):

| artifact | bytes | sha256 |
|---|---|---|
| sm_100a `delivered_sm_100a.tar.gz` | 251857 |
`1ecd3a30dac1d5fdc9de5b0c13d6becde5066dcc7b5561ca91e63205b1c950f9` |
| sm_100a `applied.json` | 13594 |
`d2fddc49cdb91d5c6c1422f22adb64e9ecb9ac31f3f5a11ad080738dada3cba5` |
| sm_100a `summary.json` | 111030 |
`83686240a9facd619a7949fcd5751b353b16935df847777c7d3815623b2f39b9` |
| sm_100a `summary.md` | 6306 |
`71f37434a167c9c460daea5530fbab3d09e4d9831518314c43eee467ddea05ee` |
| sm_103a `delivered_sm_103a.tar.gz` | 252572 |
`62db692f798b60a315d12a7b4141cebca9c93e060c33f65a0d006774c5317eed` |
| sm_103a `applied.json` | 13594 |
`d2fddc49cdb91d5c6c1422f22adb64e9ecb9ac31f3f5a11ad080738dada3cba5` |
| sm_103a `summary.json` | 111160 |
`6ac6ad54a0304db6999c03673345a86a4519a274470c35669e46993d92225f53` |
| sm_103a `summary.md` | 6306 |
`cdf069927edfd270c9b0fe614a6f8168f4334c1bb62a9a446bf416117aaa0fb8` |

## Limits

Twelve ranks in one NVLink domain with CUDA fabric symmetric memory and
multicast only; `sm_100a` / `sm_103a`; BF16
model-layout weights; `M <= max_tokens` of the workspace (default 4096);
every rank launches the same `M`.

Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added experimental Kimi-K3 TP12 tail processing for 12-rank
distributed workloads, with reusable workspaces and options to prepare
or directly run the operation.
- Added a benchmark comparing the fused operation with a standard
processing chain, including timings, speedup, and output differences.
- **Documentation**
  - Documented the experimental operation and generated-kernel setup.
- **Tests**
- Added coverage for routing, workspace validation, and distributed GPU
outputs, including repeated runs and CUDA graph replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3e69d57](https://github.com/flashinfer-ai/flashinfer/commit/3e69d57cd1f8725e895a00bba041c0b0358df522)

- **作者**: eigen
- **时间**: 2026-09-27T18:15:06Z
- **提交信息**: perf(cake_kda): shorter unbounded prepare chain for the BF16 prefill programs (sm_100a, sm_103a), correction buffer only on the chain route (#5598)

Follow-up to #5573 (kernel round 2, merged as 9b727df8a); this branch is
based on that merge and carries the regenerated programs of the
`cake_kda_bf16` BF16 prefill family (sm_100a and sm_103a) plus one host
commit. The generated kernel is the round-2 kernel with a shorter
prepare chain on the unbounded gate; the bounded-gate programs are
regenerated from the same source revision and are unchanged in
behaviour.

### 1. Kernel: the unbounded body's prepare chain

The unbounded (softplus, no lower bound) body pays for a tile-anchored
decay: per chunk the prepare warps scan the gate prefix, derive two
per-column tile anchors and restore the Q/K operands by exp2 of
anchor-relative prefixes. Three changes shorten that chain, all
bit-identical to the round-2 programs on synthetic and Kimi-profile
inputs (out, final state and checkpoint rows hashed on both GPUs):

- the scan thread publishes its column's two tile anchors once (signed
16-bit halves packed into one word, 512 B per pipeline stage); the Qd /
Kd passes read eight packed words with two 128-bit shared loads and
decode with ALU ops only;
- one shared restore code path for the three unbounded owner warps
(runtime row block / tile / pass count, branchless anchor-field select);
code size 83.2 → 74.9 KiB;
- the restore duty is re-cut along tile boundaries across all four
prepare warps (3/5/4/4 row pairs instead of 4/4/8; the warp that was
idle until the diagonal inverse restores first).

Forced-sequential body cost (one sequence, GPU-time slope between 8192
and 16384 tokens, rows every 64 / no rows): B200 2.914 / 2.727 → 2.713 /
2.517 us per chunk, GB300 2.712 / 2.516 → 2.533 / 2.346 (−7 %); at
one-wave occupancy (nine sequences, 144 CTAs) the no-rows body goes 3.27
→ 2.58 us (B200) and 3.04 → 2.41 us (GB300), −20 %. Five further
candidates (tail vote, later export release, three-segment restore,
anchor-relative prefix rows, register-buffered scan) were measured A B A
B on both GPUs and dropped; the last of them is 5–8 % faster on a single
CTA but 4–11 % slower at one-wave occupancy, where the period is bound
by the pipeline recycle loop rather than by the prepare work.

### 2. Host

- `cake_kda_tf32_runtime.py`: the affine composite no longer allocates
the BF16 correction output buffer on the apply route (the apply kernel
reduce-adds its correction into the output tail and never touches it);
−T_tail × H × D × 2 B per cached plan (67 MB at 2×8192 H16). The fused
epilogue receives the output tail as a stand-in tensor on that route,
where it reads zero tail elements. No kernel or numerics change.

### 3. Validation

- 359 export rows per architecture: output, final state and checkpoint
rows bitwise equal between the source dispatcher and the exported API
after identical resets (B200 and GB300); the chain-route coverage pass
(`CAKE_KDA_AFFINE_APPLY=0`) resolves 351/359 rows and adds no program
(every chain-route program is already published by the base passes).
- `tests/kda/test_kda_prefill_plan_cache.py`,
`tests/kda/test_bf16_one_wave_route.py`,
`tests/kda/test_tf32_prefill.py`: 76 passed on B200 and on GB300
(per-architecture trees, again after the chain pass) and 76 passed on
the combined tree of this PR on B200 and on GB300.
- compute-sanitizer synccheck + memcheck on the seven registered KDA
launchers of the source tree: 0 errors on both architectures.
- rel L2 vs the Triton reference (out / state) unchanged on all 56 bench
rows on both architectures; the source tree's GPU e2e slice reproduces
exactly the failure set of the same-node main control on both
architectures.

### Speedup vs Triton (bench_tb, same GPU, same inputs, FP32 state, rows
every 64)

Same harness as #5452 / #5543 / #5565 / #5573 (serving-adapter layer
call of the prepared export vs the Triton `chunk_kda` path, fresh
identically seeded inputs per arm, FP32 state pool, checkpoint rows
every 64 tokens; GPU time = profiler CUDA time of the call, event time =
CUDA events around the call incl. host; one lane per GPU). Unbounded H16
layer rows, GPU-time speedup:

| case | B200 #5565 → #5573 → this PR | GB300 #5565 → #5573 → this PR |
|---|---:|---:|
| 8192 | 1.47 → 1.78 → **1.92** | 1.51 → 1.84 → **1.96** |
| 16384 | 1.65 → 2.02 → **2.19** | 1.71 → 2.06 → **2.24** |
| 2x8192 | 1.18 → 1.49 → **1.63** | 1.24 → 1.51 → **1.65** |
| 3000+13384 | 1.46 → 1.81 → **1.98** | 1.54 → 1.84 → **2.01** |
| 4x4096 | 2.00 → 1.99 → **2.20** | 2.05 → 2.02 → **2.26** |
| 2x(8128+64) | 1.18 → 1.46 → **1.57** | 1.20 → 1.44 → **1.59** |
| 8x(1024+64) | 3.06 → 3.11 → **3.50** | 3.18 → 3.20 → **3.85** |
| 32768 | 1.74 → 2.13 → **2.33** | 1.81 → 2.15 → **2.38** |

Every one of the 56 rows beats Triton on GPU and on event time on both
GPUs; no row is more than 2 % slower than #5573 on GPU time; the bounded
rows are within ±1 % of #5573. On GB300 the two smallest wrapper rows
(BS4×T64, H16) read 0.96–0.98× on event time in the recorded run at
identical GPU time; a same-node A B A B against the #5573 tree shows
that row's host time to be bimodal (0.26 / 0.32 ms) for both trees, with
this PR's tree 0–10 % faster on GPU time on every lane.

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5573 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2537 | 2.36x | 0.4656 | 1.57x | 2.38x → 2.36x | 0.0052/0.0036
|
| 16384 | 0.4146 | 2.74x | 0.6892 | 1.84x | 2.79x → 2.74x |
0.0052/0.0041 |
| 2x8192 | 0.4625 | 1.81x | 0.7019 | 1.37x | 1.83x → 1.81x |
0.0052/0.0042 |
| 3000+13384 | 0.4379 | 2.35x | 0.7096 | 1.64x | 2.39x → 2.35x |
0.0052/0.0041 |
| 4x4096 | 0.2418 | 2.87x | 0.4842 | 1.69x | 2.90x → 2.87x |
0.0052/0.0039 |
| 2x(8128+64) | 0.4604 | 1.82x | 0.7024 | 1.37x | 1.84x → 1.82x |
0.0052/0.0042 |
| 8x(1024+64) | 0.1199 | 3.10x | 0.3120 | 1.64x | 3.11x → 3.10x |
0.0041/0.0017 |
| 32768 | 0.7191 | 3.12x | 1.1226 | 2.12x | 3.15x → 3.12x |
0.0052/0.0043 |

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5573 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.3112 | 2.05x | 0.5400 | 1.43x | 2.07x → 2.05x | 0.0052/0.0038
|
| 16384 | 0.5135 | 2.42x | 0.8315 | 1.65x | 2.45x → 2.42x |
0.0052/0.0040 |
| 2x8192 | 0.4639 | 2.05x | 0.7509 | 1.42x | 2.07x → 2.05x |
0.0052/0.0039 |
| 3000+13384 | 0.5271 | 2.17x | 0.8500 | 1.49x | 2.19x → 2.17x |
0.0052/0.0038 |
| 4x4096 | 0.2472 | 3.27x | 0.5309 | 1.76x | 3.32x → 3.27x |
0.0052/0.0040 |
| 2x(8128+64) | 0.4646 | 2.06x | 0.7498 | 1.44x | 2.08x → 2.06x |
0.0052/0.0039 |
| 8x(1024+64) | 0.0980 | 4.53x | 0.3136 | 1.86x | 4.52x → 4.53x |
0.0052/0.0040 |
| 32768 | 0.9183 | 2.64x | 1.4038 | 1.82x | 2.66x → 2.64x |
0.0052/0.0041 |

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5573 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0140 | 3.87x | 0.1572 | 1.60x | 3.81x → 3.87x |
0.0053/0.0039 |
| BS16 x T64 | 0.0333 | 2.40x | 0.1689 | 1.67x | 2.35x → 2.40x |
0.0040/0.0017 |
| BS64 x T64 | 0.0997 | 2.09x | 0.2636 | 1.54x | 2.05x → 2.09x |
0.0040/0.0017 |
| BS16 x T128 | 0.0438 | 2.61x | 0.1845 | 2.00x | 2.56x → 2.61x |
0.0053/0.0040 |
| BS16 x T256 | 0.0632 | 2.97x | 0.2152 | 1.77x | 2.95x → 2.97x |
0.0052/0.0039 |
| BS16 x T(17..255) | 0.0352 | 3.32x | 0.1773 | 2.12x | 3.22x → 3.32x |
0.0052/0.0040 |

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5573 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0144 | 3.74x | 0.1491 | 1.65x | 3.69x → 3.74x |
0.0053/0.0040 |
| BS16 x T64 | 0.0315 | 2.74x | 0.1678 | 1.68x | 2.72x → 2.74x |
0.0053/0.0040 |
| BS64 x T64 | 0.1128 | 2.17x | 0.2880 | 1.45x | 2.16x → 2.17x |
0.0052/0.0040 |
| BS16 x T128 | 0.0456 | 2.88x | 0.1885 | 1.90x | 2.86x → 2.88x |
0.0052/0.0040 |
| BS16 x T256 | 0.0648 | 3.40x | 0.2315 | 1.68x | 3.43x → 3.40x |
0.0052/0.0040 |
| BS16 x T(17..255) | 0.0460 | 2.88x | 0.1944 | 1.93x | 2.89x → 2.88x |
0.0052/0.0040 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5573
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2731 | 2.22x | 0.4389 | 1.67x | 2.09x → 2.22x | 0.0040/0.0022
|
| 16384 | 0.4611 | 2.48x | 0.6254 | 2.02x | 2.31x → 2.48x |
0.0040/0.0019 |
| 2x8192 | 0.4597 | 1.85x | 0.6195 | 1.56x | 1.74x → 1.85x |
0.0040/0.0019 |
| 3000+13384 | 0.4838 | 2.15x | 0.6521 | 1.78x | 2.00x → 2.15x |
0.0040/0.0024 |
| 4x4096 | 0.3707 | 1.90x | 0.4952 | 1.67x | 1.77x → 1.90x |
0.0040/0.0020 |
| 2x(8128+64) | 0.4672 | 1.82x | 0.6332 | 1.53x | 1.70x → 1.82x |
0.0040/0.0020 |
| 8x(1024+64) | 0.1199 | 3.14x | 0.2453 | 2.10x | 2.63x → 3.14x |
0.0039/0.0020 |
| 32768 | 0.8226 | 2.75x | 0.9894 | 2.42x | 2.54x → 2.75x |
0.0040/0.0021 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5573
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.3374 | 1.92x | 0.5080 | 1.50x | 1.78x → 1.92x | 0.0040/0.0020
|
| 16384 | 0.5757 | 2.19x | 0.7435 | 1.87x | 2.02x → 2.19x |
0.0040/0.0021 |
| 2x8192 | 0.5918 | 1.63x | 0.7634 | 1.42x | 1.49x → 1.63x |
0.0040/0.0021 |
| 3000+13384 | 0.5869 | 1.98x | 0.7491 | 1.71x | 1.81x → 1.98x |
0.0040/0.0025 |
| 4x4096 | 0.3733 | 2.20x | 0.5007 | 1.89x | 1.99x → 2.20x |
0.0040/0.0022 |
| 2x(8128+64) | 0.6186 | 1.57x | 0.7882 | 1.39x | 1.46x → 1.57x |
0.0040/0.0021 |
| 8x(1024+64) | 0.1290 | 3.50x | 0.2562 | 2.26x | 3.11x → 3.50x |
0.0040/0.0021 |
| 32768 | 1.0527 | 2.33x | 1.2194 | 2.13x | 2.13x → 2.33x |
0.0040/0.0021 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5573 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0214 | 2.54x | 0.1561 | 1.58x | 2.42x → 2.54x |
0.0040/0.0021 |
| BS16 x T64 | 0.0390 | 2.08x | 0.1623 | 1.72x | 1.98x → 2.08x |
0.0039/0.0020 |
| BS64 x T64 | 0.1150 | 1.84x | 0.2480 | 1.63x | 1.76x → 1.84x |
0.0039/0.0020 |
| BS16 x T128 | 0.0520 | 2.24x | 0.1759 | 2.10x | 2.12x → 2.24x |
0.0040/0.0021 |
| BS16 x T256 | 0.0772 | 2.48x | 0.2018 | 1.94x | 2.30x → 2.48x |
0.0039/0.0020 |
| BS16 x T(17..255) | 0.0428 | 2.77x | 0.1640 | 2.26x | 2.60x → 2.77x |
0.0040/0.0023 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5573 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0216 | 2.52x | 0.1566 | 1.61x | 2.40x → 2.52x |
0.0040/0.0021 |
| BS16 x T64 | 0.0393 | 2.27x | 0.1668 | 1.69x | 2.09x → 2.27x |
0.0040/0.0020 |
| BS64 x T64 | 0.1393 | 1.82x | 0.2704 | 1.55x | 1.70x → 1.82x |
0.0040/0.0021 |
| BS16 x T128 | 0.0529 | 2.56x | 0.1795 | 2.07x | 2.36x → 2.56x |
0.0039/0.0021 |
| BS16 x T256 | 0.0802 | 2.87x | 0.2041 | 1.98x | 2.61x → 2.87x |
0.0040/0.0021 |
| BS16 x T(17..255) | 0.0559 | 2.47x | 0.1803 | 2.04x | 2.24x → 2.47x |
0.0039/0.0023 |

HEADLINE_H16_UNB 8192: 1.78 → 1.92; 16384: 2.02 → 2.19; 2x8192: 1.49 →
1.63; 3000+13384: 1.81 → 1.98; 4x4096: 1.99 → 2.20; 2x(8128+64): 1.46 →
1.57; 8x(1024+64): 3.11 → 3.50; 32768: 2.13 → 2.33
**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5573 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2362 | 2.38x | 0.5325 | 1.41x | 2.37x → 2.38x | 0.0052/0.0041
|
| 16384 | 0.3856 | 2.74x | 0.7309 | 1.72x | 2.74x → 2.74x |
0.0052/0.0037 |
| 2x8192 | 0.3846 | 2.00x | 0.7240 | 1.34x | 2.01x → 2.00x |
0.0052/0.0039 |
| 3000+13384 | 0.4064 | 2.35x | 0.7508 | 1.55x | 2.35x → 2.35x |
0.0052/0.0039 |
| 4x4096 | 0.2254 | 2.82x | 0.5340 | 1.58x | 2.82x → 2.82x |
0.0052/0.0039 |
| 2x(8128+64) | 0.3850 | 2.00x | 0.7244 | 1.34x | 2.00x → 2.00x |
0.0052/0.0039 |
| 8x(1024+64) | 0.1093 | 3.09x | 0.3773 | 1.46x | 3.08x → 3.09x |
0.0040/0.0016 |
| 32768 | 0.6721 | 3.10x | 1.1363 | 2.00x | 3.10x → 3.10x |
0.0052/0.0034 |

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5573 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2868 | 2.13x | 0.6092 | 1.27x | 2.12x → 2.13x | 0.0052/0.0040
|
| 16384 | 0.4769 | 2.49x | 0.8610 | 1.61x | 2.48x → 2.49x |
0.0052/0.0040 |
| 2x8192 | 0.4374 | 2.06x | 0.7885 | 1.38x | 2.06x → 2.06x |
0.0052/0.0041 |
| 3000+13384 | 0.4867 | 2.24x | 0.8669 | 1.48x | 2.24x → 2.24x |
0.0052/0.0038 |
| 4x4096 | 0.2258 | 3.38x | 0.5648 | 1.68x | 3.37x → 3.38x |
0.0052/0.0040 |
| 2x(8128+64) | 0.4352 | 2.08x | 0.7744 | 1.42x | 2.09x → 2.08x |
0.0052/0.0040 |
| 8x(1024+64) | 0.0883 | 4.71x | 0.3768 | 1.66x | 4.70x → 4.71x |
0.0052/0.0040 |
| 32768 | 0.8540 | 2.71x | 1.3978 | 1.78x | 2.71x → 2.71x |
0.0052/0.0042 |

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5573 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0132 | 3.83x | 0.2678 | 1.16x | 3.85x → 3.83x |
0.0053/0.0040 |
| BS16 x T64 | 0.0307 | 2.39x | 0.2730 | 1.47x | 2.39x → 2.39x |
0.0041/0.0017 |
| BS64 x T64 | 0.0921 | 2.04x | 0.3682 | 1.80x | 2.07x → 2.04x |
0.0041/0.0017 |
| BS16 x T128 | 0.0397 | 2.61x | 0.3057 | 1.88x | 2.65x → 2.61x |
0.0053/0.0040 |
| BS16 x T256 | 0.0577 | 2.91x | 0.3043 | 1.79x | 2.95x → 2.91x |
0.0052/0.0040 |
| BS16 x T(17..255) | 0.0318 | 3.31x | 0.2859 | 1.84x | 3.33x → 3.31x |
0.0052/0.0041 |

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5573 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0133 | 3.96x | 0.3223 | 0.96x | 3.90x → 3.96x |
0.0053/0.0040 |
| BS16 x T64 | 0.0292 | 2.54x | 0.2852 | 1.51x | 2.52x → 2.54x |
0.0053/0.0040 |
| BS64 x T64 | 0.1040 | 2.21x | 0.3818 | 1.46x | 2.21x → 2.21x |
0.0052/0.0040 |
| BS16 x T128 | 0.0410 | 3.01x | 0.2838 | 1.84x | 3.03x → 3.01x |
0.0052/0.0040 |
| BS16 x T256 | 0.0596 | 3.50x | 0.2989 | 1.67x | 3.51x → 3.50x |
0.0052/0.0039 |
| BS16 x T(17..255) | 0.0418 | 2.98x | 0.2850 | 1.80x | 2.95x → 2.98x |
0.0052/0.0040 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5573
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2582 | 2.19x | 0.5182 | 1.45x | 2.09x → 2.19x | 0.0040/0.0020
|
| 16384 | 0.4281 | 2.49x | 0.6725 | 1.88x | 2.28x → 2.49x |
0.0040/0.0020 |
| 2x8192 | 0.4305 | 1.82x | 0.6695 | 1.45x | 1.68x → 1.82x |
0.0040/0.0019 |
| 3000+13384 | 0.4530 | 2.13x | 0.6866 | 1.68x | 1.96x → 2.13x |
0.0040/0.0024 |
| 4x4096 | 0.3439 | 1.88x | 0.5504 | 1.51x | 1.75x → 1.88x |
0.0040/0.0021 |
| 2x(8128+64) | 0.4394 | 1.78x | 0.6843 | 1.42x | 1.64x → 1.78x |
0.0040/0.0020 |
| 8x(1024+64) | 0.1099 | 3.12x | 0.3086 | 1.76x | 2.60x → 3.12x |
0.0040/0.0020 |
| 32768 | 0.7693 | 2.73x | 1.0084 | 2.26x | 2.50x → 2.73x |
0.0040/0.0022 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5573
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.3161 | 1.96x | 0.5526 | 1.40x | 1.83x → 1.96x | 0.0040/0.0021
|
| 16384 | 0.5365 | 2.24x | 0.7719 | 1.79x | 2.06x → 2.24x |
0.0040/0.0020 |
| 2x8192 | 0.5551 | 1.65x | 0.7990 | 1.37x | 1.51x → 1.65x |
0.0040/0.0021 |
| 3000+13384 | 0.5485 | 2.01x | 0.7807 | 1.65x | 1.84x → 2.01x |
0.0039/0.0022 |
| 4x4096 | 0.3447 | 2.25x | 0.5401 | 1.76x | 2.02x → 2.25x |
0.0040/0.0021 |
| 2x(8128+64) | 0.5804 | 1.59x | 0.8274 | 1.33x | 1.44x → 1.59x |
0.0040/0.0021 |
| 8x(1024+64) | 0.1106 | 3.85x | 0.3194 | 1.96x | 3.20x → 3.85x |
0.0040/0.0021 |
| 32768 | 0.9851 | 2.38x | 1.2315 | 2.05x | 2.15x → 2.38x |
0.0040/0.0023 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5573 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0200 | 2.55x | 0.2682 | 1.36x | 2.44x → 2.55x |
0.0039/0.0020 |
| BS16 x T64 | 0.0359 | 2.06x | 0.2450 | 1.67x | 1.98x → 2.06x |
0.0040/0.0020 |
| BS64 x T64 | 0.1059 | 1.78x | 0.3197 | 1.67x | 1.74x → 1.78x |
0.0039/0.0020 |
| BS16 x T128 | 0.0479 | 2.21x | 0.2468 | 2.09x | 2.15x → 2.21x |
0.0040/0.0021 |
| BS16 x T256 | 0.0715 | 2.41x | 0.2671 | 1.90x | 2.33x → 2.41x |
0.0039/0.0020 |
| BS16 x T(17..255) | 0.0394 | 2.72x | 0.2463 | 2.00x | 2.64x → 2.72x |
0.0040/0.0023 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5573 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5573 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0201 | 2.64x | 0.3057 | 0.98x | 2.55x → 2.64x |
0.0040/0.0021 |
| BS16 x T64 | 0.0366 | 2.11x | 0.2509 | 1.74x | 1.97x → 2.11x |
0.0040/0.0020 |
| BS64 x T64 | 0.1289 | 1.84x | 0.3430 | 1.59x | 1.73x → 1.84x |
0.0039/0.0021 |
| BS16 x T128 | 0.0490 | 2.59x | 0.2479 | 2.06x | 2.44x → 2.59x |
0.0040/0.0020 |
| BS16 x T256 | 0.0732 | 2.95x | 0.2746 | 1.82x | 2.69x → 2.95x |
0.0040/0.0021 |
| BS16 x T(17..255) | 0.0509 | 2.53x | 0.2450 | 2.05x | 2.32x → 2.53x |
0.0040/0.0022 |

HEADLINE_H16_UNB 8192: 1.83 → 1.96; 16384: 2.06 → 2.24; 2x8192: 1.51 →
1.65; 3000+13384: 1.84 → 2.01; 4x4096: 2.02 → 2.25; 2x(8128+64): 1.44 →
1.59; 8x(1024+64): 3.20 → 3.85; 32768: 2.15 → 2.38

### Baselines and their source PRs

- Triton reference: SGLang FLA `chunk_kda` at the pinned checkout
24c9251ac52ada1660f372922c72c1d3af722247 (same harness as the previous
PRs).
- #5573 — kernel round 2 (fused apply route, operator export, pair-map
prefix; merged as 9b727df8a): the "previous export" column of every
table and the regression baseline (no row may be > 2 % slower on GPU
time).
- #5565 — kernel round 1 (checkpoint rows leave the compute warps;
merged as b7d82df5a).
- #5543 — dense-beta unbounded coverage, measured affine break-even,
sm_103a constants (merged as 797872eac).
- #5452 — prepared BF16 prefill plan cache, FP32 intermediate states,
cached affine split (merged as 71f724405).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Optimized BF16 KDA state restoration and anchor processing on
supported CUDA kernels.
* Reduced temporary output-buffer allocation in the TF32 affine
split-launch path when correction is not needed.
* **Reliability**
* Added input and workspace validation for BF16 KDA launches, with
clearer error reporting.
* **New Features**
* Added options to prepare launch descriptors separately or run with
previously prepared descriptors.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [8589d49](https://github.com/flashinfer-ai/flashinfer/commit/8589d49b097601e18cc6e322da5db9c3a1bbc021)

- **作者**: eigen
- **时间**: 2026-09-27T08:31:05Z
- **提交信息**: fix(cake_sparse_mla): harden the DSv4 sparse-MLA Cake backend for #4671 (padded Q, separate SWA/compressed tables, caller-owned workspace, length offsets) and regenerate the SM100/SM103 programs (#5591)

## Summary

Hardens the `backend="cake"` DeepSeek-V4 sparse-MLA decode path of
`trtllm_batch_decode_sparse_mla_dsv4`
(SM100a / SM103a) for the asks in #4671 and re-exports the generated
programs:

- padded query rows beyond the metadata token count are ignored (no
metadata read past `num_tokens`, `-1` never
  dereferenced, padded output rows untouched);
- separate SWA and compressed index tables (`extra_sparse_indices`,
`extra_sparse_topk_lens`) are consumed in-kernel,
  the combined table keeps working;
- caller-owned workspace: `get_cake_dsv4_workspace_bytes(...)`, no
device allocation on any call path (MTP, CUDA graph
  capture), split counters self-reset;
- raw lengths plus `sparse_topk_lens_offset`;
- many-token (MTP) rows route to the bodies that beat trtllm-gen (16-512
tokens): BF16/H128 SWA and SWA+topk4x
rows use the persistent prefill body from 64 tokens
(`_BF16_H128_PREFILL_MIN_TOKENS`), BF16/H128 topk128x width
260/388 rows above 16 tokens use the row-first single-owner program
(`_BF16_TOPK128X_SPLIT_MAX_TOKENS`);
FP8/H64 rows admitted to the persistent body with >= 128 tokens use the
H64-specific single-CTA M64 program
(`fp8_h64_prefill_source_persistent_m64`, `_FP8_H64_M64_MIN_TOKENS`);
BF16/H32 topk4x rows share the retained-KV
topk128x program (`bf16_h32_topk128x_early_v47`, last-arriver split
merge);
- BF16/H128 SWA+topk4x rows whose persistent-grid tail clusters are the
majority launch the boustrophedon work-feed program
of the prefill body (`bf16_h128_prefill_v42_snake`,
`_bf16_h128_prefill_uses_snake_feed`);
- the boustrophedon program `bf16_h128_prefill_v42_snake` is regenerated
from a K-reuse body (the PV operand is served from the
gathered K tile, 25 % fewer L2 bytes per KV tile); the striped program
is byte-identical to the previous export;
- the FP8/H128 persistent programs rescale the O accumulator lazily (the
running max only advances when a tile raises it by more
than 8 in the exp2 domain, so most tiles skip the TMEM rescale on the
serial PV chain; P stays inside e4m3, O / sum unchanged);
- the BF16/H128 persistent prefill program drains O with 32-byte stores
(half the LSU instruction count of the epilogue tail);
- FP8 H8/H16 canonical 12-token rows (batch 3, ragged q_len 5, widths
192/256 topk4x or 260 topk128x) use the FP8 port of the
1-CTA SwapsAb body (`fp8_h8_h16_source_exact`, heads on the MMA N side),
1.24-1.49x vs the default path on both arches;
- 12-token decode routing follows the Cake seeds: FP8 low-head widths up
to 384 -> one-partition producer,
FP8/H64 rows with >= 3 complete sparse tiles -> the persistent FP8 body,
BF16/H128 topk128x width 260/388 -> the
  two-stage split3/split4 programs on both targets.

Also hardens the default trtllm-gen host path (#4671 P1/P4, see
`flashinfer/mla/_core.py`).

## Validation

Export r9 (Cake 421f1a5671a, this branch at f63041ced + the regenerated
programs), same-session paired CUPTI (active-union
median, 500 warmup / 3000 calls per arm, cold L2) against the default
trtllm-gen path at the same revision:

| | GB300 (sm_103a) | B200 (sm_100a) |
|---|---|---|
| 94 canonical + 40 hardening shapes correct (BF16 atol=rtol=1e-2, FP8
0.1; padded / separate-table / offset axes) | 134/134 | 134/134 |
| **94 canonical rows faster than the default path** | **94/94, geomean
1.24x, min 1.006x** | **94/94, geomean 1.23x, min 1.013x** |
| 40 hardening rows faster than the default path | **40/40, geomean
1.28x, min 1.016x** | **40/40, geomean 1.25x, min 1.029x** |
| compute-sanitizer synccheck + memcheck on the changed kernels | 0
errors | 0 errors |
| `tests/mla/test_cake_dsv4*.py` (GPU, on the exported programs) | 292
passed | 292 passed |
| `tests/mla/test_cake_dsv4*.py` (CPU, this host) | 208 passed | 208
passed |

The default trtllm-gen path itself is hardened for #4671 P1/P4 in
`flashinfer/mla/_core.py`.

## Baselines and their source PRs

- **trtllm-gen default path** =
`trtllm_batch_decode_sparse_mla_dsv4(...)` without `backend="cake"` (the
TRTLLM-GEN DSv4
sparse-MLA kernels plus the framework launches it needs for equal
semantics: padded-Q masking, separate-table merge,
workspace/counter handling). Origin PRs: #3269 (9c76c994b, 2026-05-21,
`flashinfer/decode.py`, `flashinfer/mla/_core.py`,
DSv4 TRTLLM-GEN kernels); SM120 kernels #3395 (f95469478, 2026-06-15);
DSv4.1 unification #5197 (eb5f05be1, 2026-09-18).
- **Cake backend under test** = `backend="cake"` from #4573 (13db2cfd5,
2026-09-16, `flashinfer/mla/cake_dsv4.py`,
`flashinfer/jit/cake_dsv4.py`, `csrc/cake_dsv4/`), regenerated by this
PR.
- **Test oracle** = the PyTorch reference of
`tests/mla/test_cake_dsv4.py` / `test_cake_dsv4_hardening.py` (DSv4
RopeQuant
  exposure #4918, 27d5b0298, 2026-09-07).
- **Branch merge-base** with upstream `main` at measurement:
d3af75ac7bef. The branch has since merged upstream `main`
c0ea2a1c2; of the upstream commits in between, the only ones touching
`flashinfer/mla/_core.py` (#4557, #5552, #5577) change
`_trtllm_batch_decode_with_kv_cache_mla_impl` (other `backend="cake"`
MLA decode paths) and leave the DSv4 default path and
`trtllm_batch_decode_sparse_mla_dsv4` unchanged, so the comparison above
still describes the merged head.

## CI

`tests/mla/test_cake_dsv4.py` and
`tests/mla/test_cake_dsv4_hardening.py` (CPU and GPU parametrizations).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7b8f612](https://github.com/flashinfer-ai/flashinfer/commit/7b8f6129ce978b2933c724aa5ce46c0a57a09389)

- **作者**: eigen
- **时间**: 2026-09-27T08:12:24Z
- **提交信息**: perf(cake_sampling): Rubin R200 (212 SM) single-wave capacity table and re-qualification (#5585)

## Summary

Re-qualifies `flashinfer.cake_sampling` (#5439, #5482) on Rubin R200
(compute capability 10.7, 212 SMs) and gives the dispatcher a measured
single-wave capacity table for that SM count.

#5482 measured R200 with the nearest existing table (B200, 148 SMs: `{1:
148, 2: 144, 4: 128, 8: 64}`). On a VR200 NVL72 node (driver 620.43,
internal CUDA 13.5 toolkit with `compute_107`, triton 3.7.0) this round
measured the device itself:

- `cuOccupancyMaxActiveClusters` for every frozen stage-1 variant (one
512-thread CTA per SM): 106 two-CTA, 46 four-CTA and 22 eight-CTA
clusters; the streaming `(c, 16)` variants step from one wave to two
between 212 and 216 CTAs (clusters of 1-2) and between 176 and 192 CTAs
(clusters of 4-8). Register-light variants (`ept <= 16`) fit two CTAs
per SM (212 two-CTA / 92 four-CTA clusters).
- Every frozen stage-1 variant that can serve a cell was timed (CUPTI, k
= 50 for B = 1..128 and k = 1000 for B = 1, 8..128; V = 32768 / 128256 /
151936 / 262144, 56 cells). With the inherited B200 table the pick
trailed the fastest frozen variant by more than 3 % in two cells (V =
128256, B = 16: streamed `(4, 16)` 16.6 / 16.9 µs vs register-resident
`(8, 32)` 15.8 / 16.0 µs at k = 50 / 1000), because 128 cluster-8 CTAs
are two waves under that table but one wave on R200.
- New table `_WAVE_CTAS_BY_SM_COUNT[212] = {1: 212, 2: 212, 4: 184, 8:
176}`: every pick is within 3 % of the fastest frozen variant (summed
relative regret 0.14 over the 56 cells, worst cell 2.9 %). The cost
constants stay the B200 fit (a Rubin-only refit reaches 0 regret there
but the constants are shared with H100 / B200, where no single set fits
every cell). Devices whose SM count is nearer 212 than 148 now use this
table.

The generated source (`csrc/cake_sampling/generated/`) is unchanged;
this is a host-side dispatch change plus tests and docs.

## Tests

- `tests/utils/test_cake_sampling.py`: 39 passed on R200 (the dispatch
test now pins the 212-SM picks: `(16, 128256) -> (8, 32)`, `(32, 128256)
-> (4, 16, stream)`, `(32, 32768) -> (4, 16)`, `(64, 32768) -> (2, 32)`,
`(128, 32768) -> (1, 16, stream)`, and nearest-table selection for 200
SMs).
- `tests/utils/test_cake_sampling_upstream.py`: 207 passed / 18 skipped
on R200 (skips = `k >= vocab`, as upstream).
- Generator-side gates on the same node: adversarial suite (CUDA graph
capture/replay, three concurrent streams, NaN / Inf / negative /
denormal rows, ties at the k and p boundaries, per-request tensors,
bitwise identity across every variant and launch mode) (38 passed / 1
skipped); compute-sanitizer synccheck + memcheck `ERROR SUMMARY: 0
errors` on four cells; eight registered regression cells re-measured.
- `pre-commit run --files` (mypy, ruff check, ruff format): passed
locally on the changed files.
- 12.x devices (RTX PRO 6000 / RTX 5090, 99 KB dynamic-smem opt-in): the
145 KB streaming stage-1 variants are not candidates there, so a
262144-entry vocabulary takes the documented `fallback:vocab_too_large`
route to `top_k_first` (already asserted by
`test_stage1_variants_respect_the_device_smem_limit`). Two tests
hard-coded the 227 KB behaviour and failed on the RTX PRO 6000 CI
runners; they now check the fallback result against the reference
`top_k_first` path and pin the dispatcher picks with an explicit 227 KB
`smem_limit`. Re-run on an RTX PRO 6000 Blackwell Server Edition (188
SMs, opt-in 101376 B, CUDA 13.3 container): both files 246 passed / 18
skipped.

## Performance

`python benchmarks/bench_cake_sampling.py --cupti --batches
1,2,4,8,16,32,64,128 --vocabs 32768,128256,151936,262144` with `--top-k
50` / `--top-k 1000`, stream launch and `--cuda-graph`
(`flashinfer.testing.bench_gpu_time`, CUPTI kernel time, p = 0.9, median
µs). Each cell is `top_k_first → cake_sampling (speedup)`.

### Rubin R200 (sm_107a, 212 SMs, internal CUDA 13.5 toolkit), this PR's
dispatch

| V | B | k=50 | k=1000 | k=50, CUDA graph | k=1000, CUDA graph |
|---|---|---|---|---|---|
| 32768 | 1 | 30.0 → 15.8 (1.89x) | 30.0 → 21.1 (1.43x) | 36.8 → 24.7
(1.49x) | 32.5 → 29.9 (1.09x) |
| 32768 | 2 | 31.1 → 16.3 (1.91x) | 31.5 → 21.6 (1.46x) | 37.9 → 25.0
(1.52x) | 36.7 → 30.1 (1.22x) |
| 32768 | 4 | 32.4 → 17.2 (1.88x) | 32.5 → 22.0 (1.48x) | 37.5 → 26.5
(1.41x) | 37.6 → 31.6 (1.19x) |
| 32768 | 8 | 33.4 → 17.2 (1.94x) | 33.5 → 22.2 (1.51x) | 41.0 → 25.4
(1.62x) | 39.0 → 30.8 (1.27x) |
| 32768 | 16 | 35.6 → 17.2 (2.08x) | 35.9 → 22.4 (1.61x) | 40.4 → 26.1
(1.55x) | 45.6 → 31.2 (1.46x) |
| 32768 | 32 | 37.2 → 17.7 (2.10x) | 38.1 → 22.8 (1.67x) | 41.8 → 26.8
(1.56x) | 42.5 → 32.0 (1.33x) |
| 32768 | 64 | 38.4 → 18.9 (2.03x) | 38.6 → 24.4 (1.58x) | 44.0 → 27.2
(1.61x) | 50.5 → 33.1 (1.53x) |
| 32768 | 128 | 39.1 → 19.9 (1.96x) | 39.6 → 31.8 (1.25x) | 44.5 → 28.9
(1.54x) | 48.3 → 41.0 (1.18x) |
| 128256 | 1 | 70.8 → 22.1 (3.19x) | 57.1 → 27.2 (2.10x) | 69.6 → 31.7
(2.19x) | 54.0 → 36.7 (1.47x) |
| 128256 | 2 | 71.3 → 22.8 (3.13x) | 62.2 → 27.8 (2.23x) | 70.4 → 31.8
(2.21x) | 69.6 → 36.7 (1.90x) |
| 128256 | 4 | 71.3 → 23.6 (3.01x) | 65.9 → 28.5 (2.31x) | 73.4 → 32.2
(2.28x) | 75.7 → 37.2 (2.03x) |
| 128256 | 8 | 71.4 → 23.8 (3.00x) | 68.2 → 28.6 (2.38x) | 69.1 → 32.2
(2.15x) | 73.7 → 37.3 (1.98x) |
| 128256 | 16 | 71.1 → 24.2 (2.94x) | 75.7 → 29.1 (2.60x) | 71.4 → 33.0
(2.16x) | 90.7 → 38.5 (2.35x) |
| 128256 | 32 | 73.5 → 25.7 (2.86x) | 84.0 → 30.9 (2.72x) | 74.6 → 34.4
(2.17x) | 101.3 → 39.6 (2.56x) |
| 128256 | 64 | 73.8 → 29.8 (2.48x) | 93.1 → 35.3 (2.64x) | 77.2 → 38.5
(2.00x) | 99.0 → 44.0 (2.25x) |
| 128256 | 128 | 73.7 → 38.1 (1.93x) | 138.1 → 50.4 (2.74x) | 81.2 →
47.1 (1.72x) | 150.2 → 59.4 (2.53x) |
| 151936 | 1 | 70.9 → 24.2 (2.93x) | 64.4 → 29.4 (2.19x) | 75.2 → 33.3
(2.26x) | 59.4 → 38.4 (1.55x) |
| 151936 | 2 | 71.6 → 24.9 (2.87x) | 70.2 → 30.1 (2.33x) | 76.4 → 34.5
(2.21x) | 76.1 → 38.8 (1.96x) |
| 151936 | 4 | 71.1 → 25.9 (2.75x) | 75.5 → 30.7 (2.46x) | 76.4 → 34.9
(2.19x) | 85.3 → 40.4 (2.11x) |
| 151936 | 8 | 71.0 → 26.1 (2.72x) | 77.4 → 30.8 (2.51x) | 76.0 → 35.2
(2.16x) | 100.1 → 39.5 (2.54x) |
| 151936 | 16 | 71.2 → 26.4 (2.70x) | 87.1 → 31.4 (2.77x) | 79.0 → 35.1
(2.25x) | 109.8 → 40.0 (2.74x) |
| 151936 | 32 | 72.1 → 27.1 (2.66x) | 97.1 → 32.2 (3.01x) | 75.7 → 36.3
(2.09x) | 95.3 → 41.1 (2.32x) |
| 151936 | 64 | 73.1 → 32.6 (2.24x) | 106.8 → 38.1 (2.80x) | 77.8 → 41.6
(1.87x) | 100.5 → 47.3 (2.12x) |
| 151936 | 128 | 73.7 → 42.9 (1.72x) | 160.8 → 54.9 (2.93x) | 85.2 →
51.8 (1.64x) | 174.8 → 63.7 (2.74x) |
| 262144 | 1 | 70.2 → 28.1 (2.50x) | 81.1 → 33.4 (2.43x) | 73.2 → 37.1
(1.97x) | 66.4 → 42.2 (1.58x) |
| 262144 | 2 | 71.1 → 28.6 (2.49x) | 92.1 → 33.8 (2.73x) | 72.8 → 37.4
(1.94x) | 130.7 → 42.3 (3.09x) |
| 262144 | 4 | 71.5 → 29.5 (2.43x) | 99.5 → 34.3 (2.90x) | 74.2 → 38.3
(1.94x) | 111.2 → 43.9 (2.53x) |
| 262144 | 8 | 70.7 → 29.8 (2.37x) | 102.4 → 34.6 (2.96x) | 74.6 → 38.6
(1.93x) | 123.8 → 43.3 (2.86x) |
| 262144 | 16 | 70.7 → 30.4 (2.33x) | 117.2 → 35.4 (3.31x) | 75.8 → 39.1
(1.94x) | 264.6 → 44.2 (5.98x) |
| 262144 | 32 | 71.0 → 31.4 (2.26x) | 134.7 → 36.5 (3.69x) | 77.8 → 40.5
(1.92x) | 154.8 → 45.4 (3.41x) |
| 262144 | 64 | 87.7 → 41.2 (2.13x) | 196.9 → 46.8 (4.21x) | 103.9 →
50.4 (2.06x) | 180.5 → 56.0 (3.23x) |
| 262144 | 128 | 107.7 → 60.7 (1.77x) | 292.0 → 72.8 (4.01x) | 119.3 →
70.2 (1.70x) | 307.6 → 82.1 (3.75x) |

All 128 cells are faster than `top_k_first` (1.09x-5.98x; the worst cell
is V = 32768, B = 1, k = 1000 under CUDA-graph replay). The only pick
that changed from #5482 is V = 128256, B = 16, now register-resident
`(8, 32)`: 24.2 µs vs 25.0 µs (k = 50) and 29.1 vs 30.0 µs (k = 1000)
with the inherited table on the same node. `joint` stays faster than the
pipeline only at V = 32768, k = 1000, B <= 4, as on B200 and H100.

### Comparison with the other routes and vLLM on R200 (stream launch, k
= 50, p = 0.9, µs)

`bench-radix-sampling-baseline`-style harness (CUPTI, cold L2, median):
FlashInfer `joint` (rejection kernel), `top_k_first` (default route),
explicit `top_k_renorm_probs` -> AIR `top_p_renorm_probs` ->
`sampling_from_probs`, vLLM's Triton `apply_top_k_top_p_triton` +
`random_sample` (vLLM main `c723a831`, triton 3.7.0 on sm_107a), PyTorch
sort + `random_sample`, and `cake_sampling`. Every arm's draws were
checked against the exact `top_k_first` support (fraction 1.000 for all
arms except `joint`, whose rejection sampler admits tokens outside that
support by design).

| V | B | `top_k_first` | `joint` | explicit (top-k renorm → AIR top-p →
sample) | vLLM Triton | torch sort | `cake_sampling` | vs `top_k_first`
| vs vLLM |
|---|---|---|---|---|---|---|---|---|---|
| 32768 | 1 | 28.7 | 33.0 | 64.5 | 146.2 | 212.7 | 21.5 | 1.33x | 6.80x
|
| 32768 | 2 | 29.7 | 39.0 | 67.6 | 146.1 | 237.6 | 21.3 | 1.39x | 6.84x
|
| 32768 | 4 | 31.0 | 45.2 | 68.3 | 145.7 | 242.0 | 21.3 | 1.45x | 6.83x
|
| 32768 | 8 | 31.7 | 52.0 | 72.1 | 146.1 | 243.7 | 21.7 | 1.46x | 6.73x
|
| 32768 | 16 | 34.1 | 57.9 | 69.6 | 145.4 | 242.0 | 22.1 | 1.54x | 6.57x
|
| 32768 | 32 | 35.6 | 63.0 | 77.5 | 144.7 | 244.9 | 21.9 | 1.63x | 6.62x
|
| 32768 | 64 | 36.8 | 67.0 | 85.3 | 147.3 | 290.7 | 22.0 | 1.67x | 6.70x
|
| 32768 | 128 | 37.8 | 71.5 | 106.2 | 72.7 | 527.1 | 22.0 | 1.72x |
3.31x |
| 128256 | 1 | 75.8 | 123.1 | 118.6 | 194.1 | 331.3 | 22.2 | 3.42x |
8.75x |
| 128256 | 2 | 76.0 | 150.5 | 125.2 | 194.2 | 426.8 | 22.8 | 3.33x |
8.53x |
| 128256 | 4 | 76.4 | 180.4 | 132.2 | 194.2 | 430.5 | 23.1 | 3.31x |
8.40x |
| 128256 | 8 | 76.2 | 193.6 | 141.9 | 193.2 | 435.7 | 23.4 | 3.25x |
8.25x |
| 128256 | 16 | 76.6 | 217.4 | 150.4 | 195.9 | 481.3 | 24.7 | 3.10x |
7.94x |
| 128256 | 32 | 81.8 | 236.1 | 169.3 | 201.4 | 598.7 | 25.8 | 3.17x |
7.82x |
| 128256 | 64 | 82.4 | 255.0 | 214.3 | 209.4 | 842.0 | 30.1 | 2.74x |
6.96x |
| 128256 | 128 | 81.9 | 266.0 | 375.4 | 233.9 | 2113.2 | 38.4 | 2.13x |
6.09x |
| 151936 | 1 | 77.1 | 152.5 | 134.7 | 187.4 | 266.0 | 24.3 | 3.18x |
7.73x |
| 151936 | 2 | 76.7 | 178.8 | 140.2 | 195.6 | 453.8 | 25.2 | 3.05x |
7.78x |
| 151936 | 4 | 77.2 | 211.3 | 149.4 | 191.1 | 459.9 | 25.5 | 3.03x |
7.50x |
| 151936 | 8 | 76.8 | 232.4 | 159.3 | 190.6 | 467.3 | 25.7 | 2.98x |
7.41x |
| 151936 | 16 | 76.5 | 263.3 | 166.6 | 193.9 | 528.4 | 26.8 | 2.85x |
7.22x |
| 151936 | 32 | 77.1 | 275.8 | 193.1 | 207.9 | 666.5 | 27.1 | 2.84x |
7.66x |
| 151936 | 64 | 81.2 | 301.8 | 249.6 | 222.6 | 970.7 | 33.1 | 2.46x |
6.73x |
| 151936 | 128 | 83.4 | 323.2 | 450.2 | 275.1 | 2507.8 | 43.2 | 1.93x |
6.36x |
| 262144 | 1 | 76.1 | 256.2 | 175.6 | 254.9 | 341.7 | 28.1 | 2.71x |
9.08x |
| 262144 | 2 | 75.8 | 320.4 | 192.7 | 258.8 | 669.7 | 28.7 | 2.65x |
9.03x |
| 262144 | 4 | 75.9 | 361.8 | 205.2 | 261.7 | 650.4 | 29.1 | 2.61x |
9.00x |
| 262144 | 8 | 75.6 | 415.2 | 216.8 | 265.8 | 698.4 | 29.4 | 2.57x |
9.05x |
| 262144 | 16 | 77.4 | 449.5 | 243.5 | 270.4 | 819.4 | 30.8 | 2.51x |
8.78x |
| 262144 | 32 | 78.4 | 488.5 | 274.9 | 285.9 | 1082.7 | 31.5 | 2.49x |
9.07x |
| 262144 | 64 | 88.7 | 531.4 | 511.4 | 337.8 | 1722.9 | 41.7 | 2.13x |
8.10x |
| 262144 | 128 | 107.7 | 609.4 | 803.5 | 466.8 | 4325.8 | 61.3 | 1.76x |
7.61x |

Over the round-6 matrix (96 cells: B 1-128 x 4 vocabularies x k 10 / 50
/ 1000, p = 0.9, stream + CUDA graph, plus a per-request-tensor subset)
every cell beats `top_k_first`: worst 1.10x (V = 32768, B = 1, k =
1000), 1.58x (worst CUDA-graph cell), 1.10x (worst per-request cell);
vLLM Triton is 3.3x-9.4x slower than `cake_sampling`.

Across the full round-5 matrix (B 1-128 x 4 vocabularies x k 10 / 50 /
1000 x p 0.5 / 0.9 / 1.0, stream and CUDA graph, 288 cells, plus a
per-request-tensor subset) every cell is faster than `top_k_first`:
worst 1.09x (V = 32768, B = 1, k = 1000, p = 1.0, stream), 1.41x (worst
CUDA-graph cell), 1.12x (worst per-request cell); vs vLLM Triton
2.2x-9.9x. As on B200 and H100, `joint` remains the fastest route only
at V = 32768, k = 1000, B <= 4.

## Baselines and their source PRs

- `top_k_top_p_sampling_from_probs(filter_apply_order="top_k_first")`
(the default route and the speedup denominator): radix
`flashinfer.topk.top_k` fast path + `top_p_sampling_from_probs` on the
gathered `[B, k]` rows from #3461 (2026-06-09), seed/offset arguments
from #2132; multi-CTA radix top-k in `include/flashinfer/topk.cuh`
(#3615 fixed its SM120 hangs), deterministic renorm mode from #4831
(`f2f2279`, 2026-09-23, the last upstream commit touching
`flashinfer/sampling.py`).
- `filter_apply_order="joint"`: `TopKTopPSamplingFromProbKernel` in
`include/flashinfer/sampling.cuh` (same files, same last commit).
- Explicit route: `top_k_renorm_probs` (`topk.cuh`) ->
`top_p_renorm_probs` (AIR, `include/flashinfer/air_top_p.cuh`, #2752
`b418bc3`, 2026-03-16) -> `sampling_from_probs`.
- vLLM: `vllm/v1/sample/ops/topk_topp_triton.py` + `random_sample` at
vLLM main `c723a831a81cb4ff89ea6d61b2d15109306ed1bc` (2026-09-21),
vendored unmodified for the harness.
- Test oracle: `tests/utils/test_cake_sampling_upstream.py` (from #5439)
compares against the `top_k_first` route on identical seeds.
- Branch merge-base: upstream `main` `6dd6218` (2026-09-26). No upstream
commit after the merge-base touches `flashinfer/sampling.py`,
`flashinfer/topk.py`, `include/flashinfer/sampling.cuh`,
`include/flashinfer/topk.cuh`, `include/flashinfer/air_top_p.cuh` or
`csrc/sampling.cu` (verified with `git log 6dd6218..origin/main --
<files>` at publication time: 2026-09-27 UTC, merge-base 6dd6218, 0
commits).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Updates**
* Added Rubin R200 performance data and stage-1 capacity coverage across
additional batch sizes and vocabulary sizes.
* Updated measured timings and selection guidance, including the limited
cases where the joint route is fastest.
* Clarified how capacity tables are selected for unlisted device sizes
and documented the corrected variant choice for a specific workload.
* Expanded validation of sampling behavior and device-specific variant
selection.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6f13ec1](https://github.com/flashinfer-ai/flashinfer/commit/6f13ec1e7c942112d14a97dd4a7ca888ea34ac20)

- **作者**: eigen
- **时间**: 2026-09-27T08:09:09Z
- **提交信息**: perf(cake_vsa_sm90): two-warpgroup small kernels, deferred cluster rendezvous, persistent first-tile header (#5586)

## Summary

Round 4 of the Hopper `backend="cake"` variable block-sparse attention
route: per-shape ceiling work on the small-selection kernels, driven by
a measured latency model, plus the FP32-partial / deterministic-test
revision that fixed the internal CI of #5582.

Kernel changes (`csrc/cake_vsa_sm90`, re-rendered from the Cake library
export):

- **Two consumer warpgroups per small CTA** (KMAX 3/4/6 and every
cluster variant): block `s` runs on warpgroup `s & 1`; warpgroup 1 hands
its FP32 partial (accumulator through its last K/V stage, running
max/sum per row) to warpgroup 0 through one CTA-wide named barrier. The
dependent QK -> softmax -> PV chain per warpgroup halves; the handoff
costs 0.35-0.46 us (a 32 KB shared-memory round trip). Occupancy for
KMAX 2/3 drops to one CTA per SM (256 threads).
- **Cluster kernels: deferred prologue rendezvous, no exit rendezvous.**
The post-initialization `barrier.cluster` wait now sits immediately
before the `st.async` push (the only cross-CTA traffic), so the whole
K/V block chain overlaps the peers' initialization, and the kernel exits
without a final cluster barrier (every owner waits for all pushed bytes
on its receive mbarrier; peers never read another CTA's shared memory).
Attributed cost of the two rendezvous: 0.57 us + 0.5-0.76 us per launch.
- **FP32 partials on both merge paths** (split workspace and the
push-form DSM merge), `k6c3` dropped (receive buffers exceed 227 KB),
tests seeded with an FP32 reference (revision 2 of #5582, unchanged
tolerances).

Planner (`flashinfer/cake_vsa_sm90.py`): the sliced-route cost model
uses the two-warpgroup chain (`ceil(blocks / 2)`), `SPLIT_MERGE_COST
0.3`, `SPLIT_FIXED_COST 2.0`; consequences on the benchmark matrix:
h1-m1024-k16 routes to the 4 x 4 cluster (was 3 x 6), the ragged 8-block
row to the 4 x 2 cluster (was split-KV 3).

## Results (H100 SXM, cold L2, CUPTI, 6 pairs, three arms in one
process)

| case | `vsa_sm90_blk64` (us) | `cake` #5582 (us) | `cake` this PR (us)
| vs blk64 | vs #5582 | warm vs #5582 |
|---|---|---|---|---|---|---|
| h1-m64-n64-k1-ragged0-scale0 | 3.360 | 2.944 | 2.944 | **1.141** |
**1.000** | 1.000 |
| h4-m256-n256-k1-ragged0-scale0 | 3.728 | 3.360 | 3.360 | **1.110** |
**1.000** | 1.000 |
| h8-m256-n256-k3-ragged0-scale0 | 5.792 | 5.120 | 5.024 | **1.153** |
**1.019** | 1.023 |
| h8-m1024-n1024-k4-ragged0-scale0 | 8.576 | 7.584 | 7.384 | **1.161** |
**1.027** | 1.023 |
| h8-m1024-n1024-k12-ragged0-scale0 | 13.120 | 11.200 | 11.008 |
**1.192** | **1.017** | 1.003 |
| h8-m2048-n2048-k8-ragged0-scale0 | 16.032 | 15.296 | 14.720 |
**1.089** | **1.039** | 1.056 |
| h8-m2048-n2048-k16-ragged0-scale0 | 23.655 | 22.464 | 22.064 |
**1.072** | **1.018** | 1.007 |
| h8-m4096-n4096-k16-ragged0-scale0 | 44.119 | 39.799 | 39.296 |
**1.123** | **1.013** | 1.015 |
| h8-m4096-n4096-k32-ragged0-scale0 | 75.471 | 66.623 | 65.919 |
**1.145** | **1.011** | 1.007 |
| h4-m512-n1024-k4-ragged0-scale0 | 6.624 | 6.192 | 5.960 | **1.111** |
**1.039** | 1.037 |
| h4-m1024-n512-k4-ragged1-scale0 | 7.808 | 6.176 | 5.952 | **1.312** |
**1.038** | 1.033 |
| h4-m1024-n1024-k8-ragged1-scale0 | 10.111 | 8.576 | 7.168 | **1.411**
| **1.196** | 1.184 |
| h7-m4096-n4096-k16-ragged1-scale0 | 29.904 | 24.959 | 24.016 |
**1.245** | **1.039** | 1.010 |
| h4-m512-n512-k4-ragged0-scale1 | 6.520 | 5.952 | 5.759 | **1.132** |
**1.034** | 1.030 |
| h1-m1024-n1024-k16-ragged0-scale0 | 13.504 | 7.328 | 6.577 | **2.053**
| **1.114** | 1.145 |
| h7-m16384-n16384-k32-ragged0-scale0 | 261.086 | 236.118 | 234.934 |
**1.111** | **1.005** | 1.004 |
| h7-m32768-n32768-k64-ragged0-scale0 | 984.049 | 944.185 | 942.857 |
**1.044** | **1.001** | 1.005 |
| h7-m65536-n65536-k64-ragged0-scale0 | 2065.187 | 2027.731 | 2022.092 |
**1.021** | **1.003** | 1.004 |
| h7-m109632-n109632-k64-ragged0-scale0 | 3833.870 | 3576.752 | 3565.336
| **1.075** | **1.003** | 1.012 |
| h7-m109632-n109632-k64-ragged1-scale0 | 1850.640 | 1793.073 | 1788.193
| **1.035** | **1.003** | 0.992 |

- Cold (6 pairs): every row >= #5582 (min 1.000, no row below 0.99),
every row > `vsa_sm90_blk64` (min 1.021); geomean 1.030 vs #5582, 1.172
vs blk64. Largest gains: h4-m1024-k8-ragged 1.196x (4 x 2 cluster
route), h1-m1024-k16 1.114x (4 x 4 cluster), the four-block rows
1.03-1.04x, h8-m2048-k8 / h7-m4096-k16-ragged 1.039x.
- Warm L2 (separate, 3 pairs): geomean 1.028 vs #5582; the one warm row
below 1 (h7-m109632-k64-ragged 0.992) is inside its 2-3 % spread.
- The nine small rows and the eleven persistent rows were measured in
two consecutive runs of the same process layout (the small kernels are
identical in both); per-row spreads 0.3-3.6 %.

## Baselines and their source PRs

- `vsa_sm90_blk64`: PR #5470 (CuTe DSL Hopper VSA kernels), head
`9f35c6acfda7`.
- `cake` round 3: PR #5582 head `f0be507` (cluster-merge small route) —
the kernel of record this round is measured against.
- `cake` round 2: PR #5581; round 1: PR #5561.

## Validation

- `pytest tests/experimental/test_cake_vsa_sm90.py`: 89 passed (the two
route-expectation tests now assert the refit routes).
- PR #5470's `tests/experimental/test_vsa_sm90.py` on `backend="cake"`:
16 passed (dispatch/metadata tests specific to the blk64 backend
deselected).
- compute-sanitizer racecheck + synccheck, unfiltered, on every cluster
variant, the split variants and the persistent kernel: 0 hazards in the
exported kernels (the FP32 reference GEMM's cuBLAS kernel reports its
known internal races).
- Split and cluster routes: two-run and CUDA-graph replay bit-exact.

Commands:

```
python benchmarks/bench_vsa_sm90.py --backends vsa_sm90_blk64,cake --pairs 6
pytest tests/experimental/test_cake_vsa_sm90.py
```


🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added cluster-based routing options for SM90a attention workloads,
including support for ragged workloads and replayable cluster plans.
* Attention planning now supports additional execution routes alongside
persistent and split-KV execution.

* **Improvements**
* Updated SM90a attention execution and work distribution across
supported routes. Some routes now combine partial results within the
kernel rather than relying on separate output workspaces.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [2469eeb](https://github.com/flashinfer-ai/flashinfer/commit/2469eeb4eadacf4b09b882ab625bb99417cbbba2)

- **作者**: eigen
- **时间**: 2026-09-27T07:51:42Z
- **提交信息**: perf(cake_xqa): add the split-KV register-MMA FP16 page128 route to experimental SM110 XQA (#5597)

## Summary

Adds the round-6 `register_mma_split` route to the experimental SM110
XQA package: the D512 tree attention kernel
split over the two halves of the KV sequence by two eight-warp groups
with an in-CTA merge, frozen for FP16 page128
KV (the one cache mode where it is faster than the `register_mma` route
on both validated Thor nodes), plus
`kernel="register_mma_auto"` which selects it for FP16 page128 KV and
the `register_mma` route elsewhere.

-
`csrc/sm110_xqa/sm_110a/sm110_xqa_tree_fp16_paged_mma_split_{kernel,binding}.cu`:
generated sm_110a source of the
Cake split kernel (`edge_xqa_tree_split`), same ABI, thread block (512
threads) and grid as `tree_fp16_paged_mma`;
manifest route `tree_fp16_paged_mma_split` (kernel family
`register_mma_split`, geometry `groups=2, group_warps=8,
  kv_split=2`, in-CTA shared-memory merge, KV L2 prefetch).
- `jit.py`: third tree kernel family with its own route suffix and
geometry contract; eleven base routes.
- `backend.py`: `kernel="register_mma_split"` (FP16 page128 only,
`ValueError` otherwise) and `kernel="register_mma_auto"`.
- Tests: FP16 page128 cache cases for both new kernel arguments, auto
fallback to `register_mma` on the other three
cache modes, rejection of `register_mma_split` off its frozen mode, JIT
fixture for the new family.

No existing route, source file or manifest entry changes; the `tcgen05`
and `register_mma` routes are untouched.

## Speedup vs baselines (shipped `register_mma_auto` route, cold-L2
CUPTI medians, two Thor nodes)

| mode | route chosen | vs `register_mma` (A, PR #5293) node 1 / node 2
| vs upstream TensorRT Edge XQA source (B) node 1 / node 2 |
|---|---|---|---|
| FP16 page128 | `register_mma_split` (new) | **1.062x / 1.082x** cold,
1.046x / 1.039x warm | **1.497x / 1.556x** |
| FP8 page128 | `register_mma` (unchanged) | 1.000x | 1.179x / 1.156x |
| FP8 contiguous | `register_mma` (unchanged) | 1.000x | 1.238x / 1.242x
|
| FP16 contiguous | `register_mma` (unchanged) | 1.000x | 1.332x /
1.319x |

Every row is >= the previous route by construction (the new kernel is
only selected where it wins on both nodes) and > 1 vs the upstream
source. In this repository's own ledger benchmark (one process, 12 rows)
the new route is 1.099x faster than `tree_fp16_paged_mma` and 1.734x
faster than the `tcgen05` `tree_fp16_paged` row.

## Measurements (Thor, sm_110a, CUDA 13.4, strict cold-L2 CUPTI paired
timing, four pairs per row)

Two Thor nodes, one process per row timing the pinned upstream TensorRT
Edge XQA source (B), the `register_mma`
route kernel (A, PR #5293) and the new split kernel in alternating
order. FP16 page128 is the shipped mode.

| mode | node | A cold | B cold | split cold | split/A | split/B | A
warm | B warm | split warm | split/A |
|---|---|---|---|---|---|---|---|---|---|---|
| FP16 page128 | node 1 | 35.58 | 50.14 | 33.50 | 1.062 | 1.497 | 22.59
| 27.73 | 21.60 | 1.046 |
| FP16 page128 | node 2 | 36.88 | 53.06 | 34.10 | 1.082 | 1.556 | 22.56
| 27.73 | 21.71 | 1.039 |
| FP8 page128 | node 1 | 25.70 | 30.30 | 28.51 | 0.901 | 1.063 | 19.39 |
19.70 | 21.28 | 0.911 |
| FP8 page128 | node 2 | 26.21 | 30.30 | 28.72 | 0.912 | 1.055 | 19.36 |
19.47 | 21.25 | 0.911 |
| FP8 contiguous | node 1 | 25.42 | 31.47 | 28.77 | 0.884 | 1.094 |
21.95 | 19.50 | 20.90 | 1.050 |
| FP8 contiguous | node 2 | 25.55 | 31.74 | 29.96 | 0.853 | 1.060 |
19.58 | 19.49 | 20.62 | 0.950 |
| FP16 contiguous | node 1 | 31.78 | 42.34 | 36.61 | 0.868 | 1.157 |
19.26 | 21.54 | 21.33 | 0.903 |
| FP16 contiguous | node 2 | 33.18 | 43.76 | 38.00 | 0.873 | 1.152 |
18.69 | 21.15 | 21.09 | 0.886 |

(us; the split kernel is exported for FP16 page128 only;
`register_mma_auto` keeps A on the other three modes.)

Correctness: seven qualification rows (three D128 decode rows, four D512
modes) pass at the package tolerances
(FP16 `atol=rtol=1e-2`, FP8 `atol=rtol=0.1`) on both nodes; the in-CTA
merge is bit-deterministic across two direct
launches and across two CUDA-graph replays. compute-sanitizer: synccheck
0 errors on all four D512 cache modes on both nodes; racecheck timed out
at the 20 s deadline on all modes (skipped by protocol, no result);
memcheck not run. The seven qualification rows and the e2e slice (68
tests) pass on both nodes.

## FlashInfer-side validation (Thor node 2, one container session;
recorded in `RESULTS.md` / `validation.json`)

- Artifact parity (frozen split schedule launcher vs the TVM-FFI export,
six alternating pairs, CUPTI cold-L2): 34.160 vs 34.328 us,
export/schedule 1.0049 (gate 3%), pass.
- Public ledger benchmark (`benchmarks/bench_sm110_xqa.py`, 12 rows in
one process): `tree_fp16_paged_mma_split` 40.897 us vs
`tree_fp16_paged_mma` 44.928 us and `tree_fp16_paged` (tcgen05) 70.928
us.
- compute-sanitizer on the exported route: synccheck 0 errors; racecheck
completed in 19 s with 53 warnings / 0 errors (asynchronous staging
writes and fragment reads ordered by mbarrier phases the tool does not
model, the same classes as the `register_mma` routes).
- Tests in the container: JIT metadata suite 35 passed; GPU suite 109
passed; pre-commit clean.

## Baselines and their source PRs

- `register_mma` route (A): PR #5293 (merged d7e03f5e, 2026-09-27),
files

`flashinfer/experimental/sm110_xqa/csrc/sm110_xqa/sm_110a/sm110_xqa_tree_*_mma_{kernel,binding}.cu`,
`backend.py`,
`jit.py`; tests `tests/experimental/sm110_xqa/test_sm110_xqa.py` (oracle
`_oracle`, same PR).
- `tcgen05` routes: PR #5293 (same merge), untouched here.
- Upstream TensorRT Edge XQA source (B): pinned revision e8b29522 of the
TensorRT Edge-LLM XQA kernel, built and
timed in the same process by the Cake benchmark harness; not part of
this repository.
- Branch merge-base: upstream `main` at d97b1801; no upstream commit
after the merge-base touches the files above
(`git log d97b1801..origin/main -- flashinfer/experimental/sm110_xqa
tests/experimental/sm110_xqa` is empty at
  publication time).

## Test plan

- [ ] `pytest tests/experimental/sm110_xqa/test_sm110_xqa_jit.py` (CPU)
- [ ] `pytest tests/experimental/sm110_xqa/test_sm110_xqa.py` on Thor
(CUDA 13.x, compute capability 11.0)
- [ ] pre-commit (ruff, mypy, end-of-file-fixer) clean

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [d61fa5e](https://github.com/flashinfer-ai/flashinfer/commit/d61fa5e03174f1b0e7b9cc8cedb8538e45a9b69c)

- **作者**: eigen
- **时间**: 2026-09-27T07:18:44Z
- **提交信息**: perf(cake_warp_decode): evict-first weight streams for the sm_103a Qwen3-30B-A3B fused route-pack rows (num_tokens 8-32) (#5593)

## NVFP4 warp-decode: evict-first weight streams for the SM103
Qwen3-30B-A3B fused route-pack rows

Update of the public-model NVFP4 warp-decode portfolio (SM100 / SM103,
num_tokens 1–32). The seven SM103 fused route-pack modules that serve
**Qwen3-30B-A3B (2048, 768, 128 experts, top-8) at num_tokens 8–32** now
issue their expert-weight and weight-scale TMA loads with an L2
evict-first cache hint (`cp.async.bulk.tensor ... .L2::cache_hint`).
Warp roles, barriers, pipeline depth, tile shapes, epilogues, routes,
boundaries and the physical contract are unchanged; every changed
module's output is bitwise identical to its predecessor. Streaming
weights this way avoids paying, inside the kernel, for the write-back of
dirty L2 lines left by whatever ran before it (in the benchmark
protocol, the cold-L2 flush); both arms below run under the same
protocol and the trtllm-gen baseline cubins use no L2 policy.

Files:
`csrc/fused_moe/warp_decode/generated/cake_warp_decode_generated_manifest.cuh`,
`generated/cake_warp_decode_inventory.json` (program `1958b9aa` ->
`39f3d098`), seven re-identified SM103 module pairs (`*_kernel.cu` +
`*_binding.cu`) and their seven sequence bindings under
`generated/sm_103a/`; the 59 retained modules and
`cake_warp_decode_contract.cuh` are byte-identical to the merged export.

### Speedup vs baseline (SM103, Qwen3-30B-A3B; CUPTI GPU time, cold L2,
same paired protocol as #5574 and #5134)

**Speedup vs baseline** = baseline latency B (FlashInfer trtllm-gen
NVFP4 fused-MoE path) divided by this export's latency E_o in the same
paired population (B/E_o); > 1.00x means this PR is faster than the
baseline. For num_tokens 8–32 the value is the median of the two
independent B300 allocations (both listed); for num_tokens 1–7 it is the
median of three measurements. "Previous PR" is the merged export before
this PR (#5574).

**Compared with the previous PR, this PR speeds up the 25 shapes
num_tokens 8–32 (bold rows): speedup vs baseline goes from 1.00–1.03x to
1.12–1.16x, geometric mean 1.13x (session 1) / 1.14x (session 2) vs
about 1.015x before, and the export latency drops by 3.5–6.7 µs per call
(3.5 µs at num_tokens 8, 6.7 µs at num_tokens 31, 6.6 µs at num_tokens
32). num_tokens 1–7 use unchanged modules and are re-measured for
non-regression only.**

| num_tokens | baseline µs (trtllm-gen) | this PR µs | **speedup vs
baseline** | per allocation (session 1 / session 2) | previous PR
speedup vs baseline | previous PR µs | latency saved vs previous PR µs |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 16.704 | 15.761 | 1.056x | median of 3 measurements | 1.052x |
15.888 | +0.13 (unchanged module) |
| 2 | 21.569 | 19.680 | 1.096x | median of 3 measurements | 1.088x |
19.729 | +0.05 (unchanged module) |
| 3 | 25.680 | 23.992 | 1.071x | median of 3 measurements | 1.057x |
23.968 | -0.02 (unchanged module) |
| 4 | 28.905 | 27.313 | 1.050x | median of 3 measurements | 1.055x |
27.361 | +0.05 (unchanged module) |
| 5 | 31.088 | 30.608 | 1.016x | median of 3 measurements | 1.009x |
30.576 | -0.03 (unchanged module) |
| 6 | 33.977 | 33.633 | 1.007x | median of 3 measurements | 1.011x |
33.600 | -0.03 (unchanged module) |
| 7 | 37.536 | 37.193 | 1.010x | median of 3 measurements | 1.008x |
37.153 | -0.04 (unchanged module) |
| **8** | **39.536** | **35.105** | **1.126x** | **1.1232 / 1.1293** |
**1.021x** | **38.624** | **3.52** |
| **9** | **41.776** | **37.120** | **1.125x** | **1.1199 / 1.1309** |
**1.002x** | **41.281** | **4.16** |
| **10** | **43.105** | **38.321** | **1.125x** | **1.1230 / 1.1266** |
**1.007x** | **42.561** | **4.24** |
| **11** | **44.480** | **39.504** | **1.126x** | **1.1224 / 1.1296** |
**1.009x** | **43.841** | **4.34** |
| **12** | **45.840** | **40.800** | **1.124x** | **1.1191 / 1.1280** |
**1.010x** | **45.249** | **4.45** |
| **13** | **47.969** | **42.240** | **1.136x** | **1.1333 / 1.1380** |
**1.014x** | **47.105** | **4.86** |
| **14** | **48.624** | **42.768** | **1.137x** | **1.1346 / 1.1392** |
**1.011x** | **47.809** | **5.04** |
| **15** | **50.544** | **44.337** | **1.140x** | **1.1364 / 1.1436** |
**1.019x** | **49.345** | **5.01** |
| **16** | **51.553** | **45.120** | **1.143x** | **1.1389 / 1.1462** |
**1.020x** | **50.305** | **5.18** |
| **17** | **53.473** | **46.304** | **1.155x** | **1.1462 / 1.1635** |
**1.033x** | **51.616** | **5.31** |
| **18** | **54.848** | **47.536** | **1.154x** | **1.1458 / 1.1618** |
**1.022x** | **53.345** | **5.81** |
| **19** | **55.184** | **47.856** | **1.153x** | **1.1436 / 1.1626** |
**1.024x** | **53.633** | **5.78** |
| **20** | **55.648** | **49.008** | **1.135x** | **1.1278 / 1.1432** |
**1.013x** | **54.689** | **5.68** |
| **21** | **56.737** | **50.064** | **1.133x** | **1.1262 / 1.1404** |
**1.010x** | **56.000** | **5.94** |
| **22** | **57.825** | **51.169** | **1.130x** | **1.1230 / 1.1372** |
**1.012x** | **57.089** | **5.92** |
| **23** | **57.888** | **50.881** | **1.138x** | **1.1305 / 1.1450** |
**1.016x** | **56.865** | **5.98** |
| **24** | **58.368** | **51.232** | **1.139x** | **1.1349 / 1.1437** |
**1.016x** | **57.345** | **6.11** |
| **25** | **60.112** | **52.880** | **1.137x** | **1.1335 / 1.1401** |
**1.010x** | **59.329** | **6.45** |
| **26** | **61.888** | **54.729** | **1.131x** | **1.1262 / 1.1354** |
**1.006x** | **61.313** | **6.58** |
| **27** | **62.416** | **55.185** | **1.131x** | **1.1274 / 1.1347** |
**1.011x** | **61.600** | **6.41** |
| **28** | **62.945** | **55.616** | **1.132x** | **1.1282 / 1.1354** |
**1.006x** | **62.112** | **6.50** |
| **29** | **63.952** | **56.416** | **1.134x** | **1.1276 / 1.1395** |
**1.015x** | **62.912** | **6.50** |
| **30** | **64.385** | **56.848** | **1.133x** | **1.1271 / 1.1380** |
**1.015x** | **63.361** | **6.51** |
| **31** | **65.424** | **57.600** | **1.136x** | **1.1316 / 1.1401** |
**1.013x** | **64.320** | **6.72** |
| **32** | **65.424** | **57.600** | **1.136x** | **1.1322 / 1.1395** |
**1.015x** | **64.225** | **6.63** |

### Gates (same protocol as the previous updates)

Two gates per row, measured with symmetric repeated paired measurement
(CUPTI activity timing, cold L2, symmetric external CUDA Graph
population, 6 creation orders × 6 instances per arm, same-instance
prime, 3 counterbalanced groups, seed 28301, FP4 atol 1 / rtol 0.1, SM
clock ≥ 1900 MHz):

- **Baseline speedup gate**: official FlashInfer baseline latency B over
the export latency E_o in the same paired population; passes when B/E_o
> 1.
- **Export no-regression gate**: source latency S over the export
latency E_s in its own paired population; passes when S/E_s ≥ 0.97
(strict S/E_s ≥ 1 reported alongside).

Previous status of these rows: B/E_o 1.002–1.033 (all > 1, 1–3 % ahead
of the baseline).

### What changed (SM103 Qwen3-30B-A3B, 32 rows re-measured across five
independent B300 allocations; the full num_tokens 8–32 set in two of
them, num_tokens 9–32 in a third, num_tokens 1–8 in the other two)

Independent B300 session 1 (rows t08, t09-t16, t17-t24, t25-t32):

| num_tokens | baseline µs | export µs (E_o) | B/E_o | source µs |
export µs (E_s) | S/E_s | S/E_s ≥ 1 |
|---:|---:|---:|---:|---:|---:|---:|:-:|
| 8 | 39.392 | 35.072 | 1.1232 | 34.976 | 35.008 | 0.9991 | no |
| 9 | 41.536 | 37.089 | 1.1199 | 37.120 | 37.088 | 1.0009 | yes |
| 10 | 42.945 | 38.241 | 1.1230 | 38.368 | 38.272 | 1.0025 | yes |
| 11 | 44.320 | 39.488 | 1.1224 | 39.489 | 39.488 | 1.0000 | yes |
| 12 | 45.729 | 40.864 | 1.1191 | 40.864 | 40.864 | 1.0000 | yes |
| 13 | 47.905 | 42.272 | 1.1333 | 42.209 | 42.273 | 0.9985 | no |
| 14 | 48.544 | 42.785 | 1.1346 | 42.752 | 42.784 | 0.9993 | no |
| 15 | 50.400 | 44.352 | 1.1364 | 44.480 | 44.321 | 1.0036 | yes |
| 16 | 51.425 | 45.153 | 1.1389 | 45.216 | 45.153 | 1.0014 | yes |
| 17 | 53.185 | 46.400 | 1.1462 | 46.497 | 46.401 | 1.0021 | yes |
| 18 | 54.560 | 47.616 | 1.1458 | 47.681 | 47.616 | 1.0014 | yes |
| 19 | 54.785 | 47.904 | 1.1436 | 47.968 | 47.905 | 1.0013 | yes |
| 20 | 55.361 | 49.088 | 1.1278 | 49.281 | 49.056 | 1.0046 | yes |
| 21 | 56.545 | 50.209 | 1.1262 | 50.241 | 50.209 | 1.0006 | yes |
| 22 | 57.537 | 51.233 | 1.1230 | 51.297 | 51.200 | 1.0019 | yes |
| 23 | 57.664 | 51.009 | 1.1305 | 50.944 | 51.040 | 0.9981 | no |
| 24 | 58.144 | 51.232 | 1.1349 | 51.265 | 51.232 | 1.0006 | yes |
| 25 | 60.064 | 52.992 | 1.1335 | 52.961 | 52.992 | 0.9994 | no |
| 26 | 61.664 | 54.753 | 1.1262 | 54.880 | 54.753 | 1.0023 | yes |
| 27 | 62.305 | 55.265 | 1.1274 | 55.232 | 55.264 | 0.9994 | no |
| 28 | 62.817 | 55.680 | 1.1282 | 55.616 | 55.649 | 0.9994 | no |
| 29 | 63.616 | 56.417 | 1.1276 | 56.481 | 56.448 | 1.0006 | yes |
| 30 | 64.129 | 56.896 | 1.1271 | 56.993 | 56.865 | 1.0023 | yes |
| 31 | 65.217 | 57.632 | 1.1316 | 57.793 | 57.632 | 1.0028 | yes |
| 32 | 65.249 | 57.632 | 1.1322 | 57.793 | 57.633 | 1.0028 | yes |

Independent B300 session 2 (rows t08, t09-t16, t17-t24, t25-t32):

| num_tokens | baseline µs | export µs (E_o) | B/E_o | source µs |
export µs (E_s) | S/E_s | S/E_s ≥ 1 |
|---:|---:|---:|---:|---:|---:|---:|:-:|
| 8 | 39.680 | 35.137 | 1.1293 | 35.104 | 35.136 | 0.9991 | no |
| 9 | 42.016 | 37.152 | 1.1309 | 37.120 | 37.184 | 0.9983 | no |
| 10 | 43.264 | 38.401 | 1.1266 | 38.368 | 38.400 | 0.9992 | no |
| 11 | 44.641 | 39.520 | 1.1296 | 39.552 | 39.553 | 1.0000 | no |
| 12 | 45.952 | 40.736 | 1.1280 | 40.832 | 40.737 | 1.0023 | yes |
| 13 | 48.033 | 42.209 | 1.1380 | 42.113 | 42.240 | 0.9970 | no |
| 14 | 48.704 | 42.752 | 1.1392 | 42.688 | 42.753 | 0.9985 | no |
| 15 | 50.687 | 44.321 | 1.1436 | 44.512 | 44.320 | 1.0043 | yes |
| 16 | 51.681 | 45.088 | 1.1462 | 45.089 | 45.120 | 0.9993 | no |
| 17 | 53.761 | 46.208 | 1.1635 | 46.368 | 46.241 | 1.0027 | yes |
| 18 | 55.136 | 47.456 | 1.1618 | 47.552 | 47.488 | 1.0013 | yes |
| 19 | 55.584 | 47.809 | 1.1626 | 47.873 | 47.808 | 1.0014 | yes |
| 20 | 55.936 | 48.929 | 1.1432 | 49.025 | 48.929 | 1.0020 | yes |
| 21 | 56.929 | 49.920 | 1.1404 | 50.048 | 49.920 | 1.0026 | yes |
| 22 | 58.113 | 51.104 | 1.1372 | 51.200 | 51.104 | 1.0019 | yes |
| 23 | 58.112 | 50.753 | 1.1450 | 50.880 | 50.784 | 1.0019 | yes |
| 24 | 58.593 | 51.232 | 1.1437 | 51.104 | 51.232 | 0.9975 | no |
| 25 | 60.161 | 52.768 | 1.1401 | 52.769 | 52.769 | 1.0000 | yes |
| 26 | 62.112 | 54.705 | 1.1354 | 54.784 | 54.688 | 1.0018 | yes |
| 27 | 62.528 | 55.105 | 1.1347 | 55.072 | 55.104 | 0.9994 | no |
| 28 | 63.072 | 55.552 | 1.1354 | 55.584 | 55.553 | 1.0006 | yes |
| 29 | 64.288 | 56.416 | 1.1395 | 56.448 | 56.385 | 1.0011 | yes |
| 30 | 64.640 | 56.800 | 1.1380 | 56.928 | 56.800 | 1.0023 | yes |
| 31 | 65.632 | 57.568 | 1.1401 | 57.665 | 57.585 | 1.0014 | yes |
| 32 | 65.600 | 57.568 | 1.1395 | 57.697 | 57.569 | 1.0022 | yes |

Independent B300 session 3 (rows t09-t16, t17-t24, t25-t32):

| num_tokens | baseline µs | export µs (E_o) | B/E_o | source µs |
export µs (E_s) | S/E_s | S/E_s ≥ 1 |
|---:|---:|---:|---:|---:|---:|---:|:-:|
| 9 | 41.888 | 37.185 | 1.1265 | 37.184 | 37.184 | 1.0000 | yes |
| 10 | 43.200 | 38.433 | 1.1240 | 38.432 | 38.401 | 1.0008 | yes |
| 11 | 44.704 | 39.456 | 1.1330 | 39.521 | 39.488 | 1.0008 | yes |
| 12 | 46.017 | 40.737 | 1.1296 | 40.833 | 40.768 | 1.0016 | yes |
| 13 | 48.128 | 42.305 | 1.1376 | 42.272 | 42.337 | 0.9985 | no |
| 14 | 48.768 | 42.816 | 1.1390 | 42.817 | 42.848 | 0.9993 | no |
| 15 | 50.689 | 44.321 | 1.1437 | 44.449 | 44.321 | 1.0029 | yes |
| 16 | 51.713 | 45.056 | 1.1477 | 45.088 | 45.056 | 1.0007 | yes |
| 17 | 53.569 | 46.272 | 1.1577 | 46.369 | 46.304 | 1.0014 | yes |
| 18 | 54.848 | 47.457 | 1.1557 | 47.552 | 47.457 | 1.0020 | yes |
| 19 | 55.296 | 47.840 | 1.1559 | 47.872 | 47.840 | 1.0007 | yes |
| 20 | 55.584 | 48.960 | 1.1353 | 49.024 | 48.960 | 1.0013 | yes |
| 21 | 56.800 | 49.921 | 1.1378 | 50.016 | 49.952 | 1.0013 | yes |
| 22 | 57.761 | 51.104 | 1.1303 | 51.137 | 51.104 | 1.0006 | yes |
| 23 | 57.825 | 50.784 | 1.1386 | 50.848 | 50.753 | 1.0019 | yes |
| 24 | 58.272 | 51.200 | 1.1381 | 51.073 | 51.200 | 0.9975 | no |
| 25 | 60.289 | 52.768 | 1.1425 | 52.768 | 52.768 | 1.0000 | yes |
| 26 | 62.241 | 54.688 | 1.1381 | 54.753 | 54.688 | 1.0012 | yes |
| 27 | 62.625 | 55.137 | 1.1358 | 55.041 | 55.136 | 0.9983 | no |
| 28 | 62.753 | 55.521 | 1.1303 | 55.553 | 55.552 | 1.0000 | yes |
| 29 | 64.032 | 56.416 | 1.1350 | 56.449 | 56.416 | 1.0006 | yes |
| 30 | 64.481 | 56.768 | 1.1359 | 56.896 | 56.737 | 1.0028 | yes |
| 31 | 65.409 | 57.537 | 1.1368 | 57.664 | 57.536 | 1.0022 | yes |
| 32 | 65.633 | 57.568 | 1.1401 | 57.697 | 57.569 | 1.0022 | yes |

Independent B300 session 4 (rows t01-t08, t01_02_03_04_05_06_07):

| num_tokens | baseline µs | export µs (E_o) | B/E_o | source µs |
export µs (E_s) | S/E_s | S/E_s ≥ 1 |
|---:|---:|---:|---:|---:|---:|---:|:-:|
| 1 | 16.800 | 15.904 | 1.0563 | 15.760 | 15.825 | 0.9959 | no |
| 2 | 21.569 | 19.680 | 1.0960 | 19.904 | 19.680 | 1.0114 | yes |
| 3 | 25.633 | 23.953 | 1.0701 | 23.969 | 23.968 | 1.0000 | yes |
| 4 | 28.657 | 27.296 | 1.0498 | 27.296 | 27.264 | 1.0012 | yes |
| 5 | 31.040 | 30.560 | 1.0157 | 30.688 | 30.560 | 1.0042 | yes |
| 6 | 33.777 | 33.569 | 1.0062 | 33.424 | 33.584 | 0.9953 | no |
| 7 | 37.377 | 37.136 | 1.0065 | 36.817 | 37.136 | 0.9914 | no |
| 8 | 39.584 | 34.976 | 1.1317 | 35.040 | 35.040 | 1.0000 | yes |

Independent B300 session 5 (rows t01-t08):

| num_tokens | baseline µs | export µs (E_o) | B/E_o | source µs |
export µs (E_s) | S/E_s | S/E_s ≥ 1 |
|---:|---:|---:|---:|---:|---:|---:|:-:|
| 1 | 16.608 | 15.617 | 1.0635 | 15.744 | 15.552 | 1.0123 | yes |
| 2 | 21.568 | 19.680 | 1.0959 | 20.064 | 19.648 | 1.0212 | yes |
| 3 | 25.728 | 24.032 | 1.0706 | 24.001 | 24.000 | 1.0000 | yes |
| 4 | 29.153 | 27.329 | 1.0667 | 27.360 | 27.360 | 1.0000 | yes |
| 5 | 31.136 | 30.657 | 1.0156 | 30.688 | 30.656 | 1.0010 | yes |
| 6 | 34.176 | 33.697 | 1.0142 | 33.440 | 33.696 | 0.9924 | no |
| 7 | 37.696 | 37.249 | 1.0120 | 36.864 | 37.249 | 0.9897 | no |
| 8 | 39.809 | 35.008 | 1.1371 | 35.040 | 35.009 | 1.0009 | yes |

### Validation

- Correctness on SM103 for every exported Qwen3-30B-A3B route (FP4
tolerance atol 1.0 / rtol 0.1 against the PyTorch reference) plus the
export pipeline's source/export/build/runtime/manifest/route checks; the
changed modules additionally reproduce their predecessors' outputs bit
for bit on the pinned inputs; the 59 retained modules are byte-identical
to the merged export and keep their previous validation.
- compute-sanitizer synccheck and racecheck (run separately; memcheck
not run) on the seven changed SM103 modules: 2/2 PASS (synccheck and
racecheck, 0 errors, 0 hazards) over the num_tokens
1/2/8/9/10/11/12/17/20/21 routes.
- Nsight Compute (informational): the changed FC1 kernels sustain 55–63
% of DRAM peak at num_tokens 9–16, the same as before under ncu's own
clean cache flush.

### Baselines and their source PRs

- Baseline arm (B): the FlashInfer trtllm-gen NVFP4 fused-MoE path
(`flashinfer.fused_moe` trtllm-gen batched-GEMM cubins, the same cubin
set the previous updates were measured against), invoked through the
same pre-routed physical contract as before. Implementation files:
`flashinfer/fused_moe/core.py`,
`csrc/trtllm_fused_moe_kernel_launcher.cu`,
`csrc/trtllm_fused_moe_runner.cu`,
`csrc/trtllm_fused_moe_routing_binding.cu`,
`include/flashinfer/trtllm/fused_moe/`. Most recent upstream changes to
these files before this branch's merge-base: #5149 (`e34a1735a`,
2026-09-25), #5281 (`476f7bbdd`, 2026-09-17), #5207 (`7281e687a`,
2026-09-16), #4894 (`7554a6ed0`, 2026-09-16). This branch's merge-base
with `flashinfer-ai/flashinfer` main is `9b727df8a`; `git log
9b727df8a..upstream/main -- <baseline files>` was empty when the PR was
opened, so the comparison arm did not move between measurement and
publication.
- Source arm (S): the reference implementation the export is generated
from (Cake NVFP4 warp-decode schedules, same revision as this export).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4509
- **最后更新**: 2026-09-27T21:53:30Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Max LI

## AI分析总结

**1. 主要更新类型**
*   **Bug修复**：修复了代码中的一个缺陷。

**2. 关键变更点及其与项目整体方向的关系**
*   **修复对象**：专门修复了在`MLX`（苹果针对其芯片优化的机器学习框架）后端下，“提示词增强采样器”组件存在的兼容性问题。
*   **与项目方向的关系**：FastVideo致力于在多种硬件（包括苹果芯片设备）上提供高效、易用的视频生成与处理能力。此修复确保了核心功能（提示词增强）在目标平台（Apple Silicon）上的正常运行，维护了项目“跨平台高性能”的关键承诺。

**3. 对项目的影响和潜在意义**
*   **直接影响**：提升了使用苹果设备（如Mac）的用户的稳定性与体验，解决了可能阻碍他们正常使用的具体问题。
*   **间接影响**：体现了项目对跨平台兼容性的持续维护，有助于保持社区的活跃度和用户信任度，特别是在庞大的苹果用户群体中。
*   **潜在意义**：为在MLX后端上集成或开发更复杂的功能奠定了更稳固的基础。

**4. 值得关注的技术点**
*   此修复可能涉及对`MLX`框架API或其与项目自定义采样器逻辑交互方式的适配与调试。
*   它表明项目的模块化设计允许针对特定后端（如MLX）进行独立修复，而无需重构整个系统。

**5. 基于README了解的项目背景分析**
*   README显示项目强调易用性（有快速入门指南）和社区协作。本次对“提示词增强”这一常用功能组件的修复，直接保障了新用户通过快速入门文档尝试时的顺畅度。
*   项目提供多种硬件后端支持，此次修复巩固了其在苹果生态中的可用性，这与其作为一站式视频处理工具的定位相符。
*   它间接支持了项目文档的准确性：确保用户按照文档操作时，功能在所有支持的后端上都能如预期工作，避免了因平台特定bug导致的困惑。

## 详细提交记录

### [dd35763](https://github.com/hao-ai-lab/FastVideo/commit/dd35763ad6ba8db441fdccbe05f66fba797b8931)

- **作者**: Max LI
- **时间**: 2026-09-27T21:53:25Z
- **提交信息**: [bugfix] Fix MLX prompt enhancement sampler compatibility (#1891)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34621
- **最后更新**: 2026-09-28T00:29:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
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


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13186
- **最后更新**: 2026-09-27T15:12:54Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36490
- **最后更新**: 2026-09-28T00:33:41Z

## 提交统计

- **昨日提交总数**: 45
- **提交者数量**: 17
- **主要提交者**: mrusanovsky, Nguyễn Văn Cao Nguyên, WenhaoZhang

## AI分析总结

基于提供的提交记录，对 **sgl-project/sglang** 昨日（一批）提交的分析总结如下：

### 1. 主要更新类型
本次提交以**大规模架构重构**为主导，辅以**功能增强**、**Bug修复**和**性能优化**。
*   **重构（占主导）**：超过半数的提交（尤其是 #1-27）聚焦于核心计算图和并行策略的架构重构。
*   **功能增强与新特性**：包括新的推理算法、模型架构支持、基准测试工具等。
*   **Bug修复**：修正了分布式计算、内核掩码、兼容性等方面的关键问题。
*   **性能优化**：针对特定模型（如SANA-Video）和硬件（AMD）进行加速与适配。

### 2. 关键变更点及其与项目整体方向的关系
本次提交的核心是围绕**计算边界（Boundaries）** 和**层（Layer）定义方式**的彻底重构。
*   **引入声明式边界**：通过 `LayerFacts` 和边界声明，替代了原先的 `ScatterMode` 和 `LayerScatterModes`（#1, #6）。这使得模型的并行策略（如数据并行DP、张量并行TP、上下文并行CP）的配置更直观、灵活。
*   **简化层结构**：将CUDA内核在层构造时注入而非通过子类（#2），并统一了阶段（Stage）的边界构建和残差读写方式（#3, #4, #15）。这降低了自定义层的复杂度。
*   **增强MoE与混合架构支持**：重构了密集MLP和MoE层（特别是Falcon-H1、Nemotron-H）的并行计算路径，使其更统一地从声明中派生（#7, #9, #10, #14, #27）。这体现了项目对**混合专家模型（MoE）** 和**非Transformer架构（如Mamba）** 的持续投入。

### 3. 对项目的影响和潜在意义
*   **大幅提升代码可维护性与可扩展性**：声明式边界和统一的层构造方式，使得添加新的并行策略或模型架构变得更加清晰和安全，减少了样板代码和潜在错误。
*   **奠定下一代高效并行推理的基础**：重构清晰地定义了“边界”，为实现更复杂、更灵活的流水线并行（Pipeline Parallelism）、专家并行（Expert Parallelism）以及多维并行组合铺平了道路。
*   **提升推理框架的健壮性**：多个Bug修复（如DP/CP交互时的梯度计算、掩码问题）直接提升了复杂分布式场景下的计算正确性和系统稳定性。

### 4. 值得关注的技术点
*   **CuTe DSL 的深度集成**：将基于Cute的DSL内核直接注入层构造，标志着项目对**高性能、可组合的CUDA内核开发**的深度整合，旨在实现更极致的算子融合。
*   **显式边界与入口点**：`BoundarySteps`、`FFN-exit` 等概念的引入，将隐式的计算流程显式化、数据流化，是构建可预测、可优化计算图的关键一步。
*   **针对特定架构的深度优化**：如对 `Falcon-H1`（混合Transformer-Mamba）和 `LongCat-Flash` 等模型进行特定的通信与计算优化，展示了框架对前沿模型架构的快速适配能力。

### 5. 基于项目背景的影响总结
SGLang 定位为高性能大语言模型推理与服务框架。此次提交通过**彻底的架构重构**，显著增强了其作为核心引擎的 **“可配置性”** 与 **“可编程性”**。
*   **技术债务清理与架构升级**：重构解决了历史设计中边界模糊、子类耦合过重的问题，使框架更易于维护和演进。
*   **面向未来的可扩展性**：新架构能更好地容纳未来出现的混合专家模型、多模态模型以及更复杂的分布式并行策略，支持项目持续追求**高吞吐、低延迟**的目标。
*   **社区贡献整合**：本次提交包含多个来自外部合作的贡献（如AMD适配、新模型支持），重构后的清晰架构有助于更顺畅地集成这些贡献，推动生态发展。

综上，这批提交标志着 SGLang 在其内部计算核心实现了一次重要的**现代化升级**，为其应对日益复杂的大模型推理需求打下了坚实的基础。

## 详细提交记录

### [81f27fb](https://github.com/sgl-project/sglang/commit/81f27fb3a71d3504eab821a9d39352c924c730cf)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:56:11Z
- **提交信息**: [Refactor] Replace LayerScatterModes with LayerFacts and remove ScatterMode (#41443)

### [06d012e](https://github.com/sgl-project/sglang/commit/06d012eacad7f0a79c8bf4467159af4fc6fcbc44)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:55:47Z
- **提交信息**: [Refactor] Give a layer its CuTe DSL kernels at construction instead of a subclass (#41442)

### [341d527](https://github.com/sgl-project/sglang/commit/341d5273bd3ff840f16ce10428d08a3092b1d583)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:55:25Z
- **提交信息**: [Refactor] Build the boundary into any stage with one construction (#41441)

### [644014b](https://github.com/sgl-project/sglang/commit/644014bc981bbf5156cb6b6431f600160c74dbbf)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:55:04Z
- **提交信息**: [Refactor] Declare each stage's residual read and update, and give each stage its own entry (#41440)

### [0e907b7](https://github.com/sgl-project/sglang/commit/0e907b755d73da127d04708a0cd91436b1d12ff8)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:54:41Z
- **提交信息**: [Refactor] Split the layer communicator into a package (move only) (#41439)

### [427c9e0](https://github.com/sgl-project/sglang/commit/427c9e05c165befa2997a080c4ef0274dbce1f5a)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:54:18Z
- **提交信息**: [Refactor] Choose every layer's boundaries from declarations and remove the scatter-mode selection (#41438)

### [55d2ee5](https://github.com/sgl-project/sglang/commit/55d2ee554635b8ac5db58b30ae828a83bd0cf27b)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:53:57Z
- **提交信息**: [Refactor] Step-3.5: complete the dense MLP's sum through ffn_exit (#41437)

### [0971450](https://github.com/sgl-project/sglang/commit/0971450c168f14fd28055ec32f4eb5a6b50f1799)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:53:36Z
- **提交信息**: [Fix] LongCat-Flash under attention DP: branch and merge the dense FFNs through the communicators (#41436)

### [4fac02f](https://github.com/sgl-project/sglang/commit/4fac02fe5dad6002453620743be523c4835242d3)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:53:15Z
- **提交信息**: [Refactor] Choose MoE layers' boundaries from declarations when moe_dp_size equals attn_cp_size (#41435)

### [ecb8e9f](https://github.com/sgl-project/sglang/commit/ecb8e9fc8f753c4b2544df2d9d1d6695fc02992f)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:52:53Z
- **提交信息**: [Refactor] Falcon-H1: complete the FFN's sum through ffn_exit (#41434)

### [19eb56f](https://github.com/sgl-project/sglang/commit/19eb56fa57c5aec984dc6c4b084d5750d3952e51)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:52:31Z
- **提交信息**: [Fix] Falcon-H1: count the Mamba mixer's output once under tensor parallelism (#41433)

### [31329c2](https://github.com/sgl-project/sglang/commit/31329c222cb0e4e172fcc4c9a31b12c906b43654)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:52:10Z
- **提交信息**: [Fix] Run MoE layers under attention DP and GQA prefill CP on the declared DP × CP gather (#41432)

### [f0ecf15](https://github.com/sgl-project/sglang/commit/f0ecf15c84d2b58d1726c2a1e87809ba0d71948f)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:51:48Z
- **提交信息**: [Refactor] Move CuTe DSL-fused layers onto the declared boundaries and FFN-exit kernel entries (#41431)

### [8c43c66](https://github.com/sgl-project/sglang/commit/8c43c667cbb462b2d90016ad03ba39f9e581a75e)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:51:27Z
- **提交信息**: [Refactor] Nemotron-H: build each layer's boundaries from its stage and the previous one (#41430)

### [6f370c3](https://github.com/sgl-project/sglang/commit/6f370c3bcd6a65b10960b47909e7781d92ebeae3)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:51:05Z
- **提交信息**: [Refactor] Build each decoder boundary from the declarations of its two sides (#41429)

### [2e7f0bb](https://github.com/sgl-project/sglang/commit/2e7f0bb28c4826755e30c574b1cb1ab6b782d591)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:50:43Z
- **提交信息**: [Refactor] Publish the LoRA token layout from the batch's FFN input rows (#41428)

### [c289656](https://github.com/sgl-project/sglang/commit/c28965643489701cc561bd0b724c3b354dd6c3cb)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:50:23Z
- **提交信息**: [Refactor] Let the MoE declare whether its skipped reduction is one TP all-reduce (#41427)

### [deaa7f1](https://github.com/sgl-project/sglang/commit/deaa7f14634e66800ae6949acd46a3c51415918f)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:50:03Z
- **提交信息**: [Refactor] Run two-batch-overlap layers on the declared boundaries (#41426)

### [6f2d243](https://github.com/sgl-project/sglang/commit/6f2d2437b63f1d5fa8efeb9a1e744df581a20693)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:49:42Z
- **提交信息**: [Refactor] Run MHC layers on the shared boundary steps with MHC's residual operations (#41425)

### [f5ae989](https://github.com/sgl-project/sglang/commit/f5ae989a0e945135b672049e03f647a9798fcc41)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:49:21Z
- **提交信息**: [Refactor] Choose fully-DP dense and DSA / MLA prefill CP layers' steps from declarations (#41424)

### [cad9eaf](https://github.com/sgl-project/sglang/commit/cad9eaf27d7468c07cd5e61b8c347e7881a3895a)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:48:59Z
- **提交信息**: [Fix] Gather a dense FFN's input across attention DP and CP in one DP sum (#41423)

### [1c919e4](https://github.com/sgl-project/sglang/commit/1c919e401de427e23cf8aa0573ed380aa99d537f)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:48:39Z
- **提交信息**: [Fix] Keep one copy of CP-replicated rows in the DP gather (#41422)

### [7a833ad](https://github.com/sgl-project/sglang/commit/7a833ad0a2a0367f544d7957ef23ebf5037765f3)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:48:17Z
- **提交信息**: [Refactor] Choose a GQA prefill CP extend's steps from declarations (#41421)

### [380a4d0](https://github.com/sgl-project/sglang/commit/380a4d03329f2dca0b35a4fc2ad906e2053e70cf)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:47:55Z
- **提交信息**: [Refactor] Run every batch of a layer from one BoundarySteps (#41420)

### [9f87d28](https://github.com/sgl-project/sglang/commit/9f87d28db6fcda194cf04bc0522928aecd339b39)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:47:32Z
- **提交信息**: [Refactor] Choose the LayerNorm SP region's and input-scattered batches' steps from declarations (#41419)

### [846181f](https://github.com/sgl-project/sglang/commit/846181f1c40884cbdee81c8c6a5935f4defba047)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:47:11Z
- **提交信息**: [Refactor] Give the fused prepare_mlp kernels an explicit contract (#41418)

### [446d181](https://github.com/sgl-project/sglang/commit/446d181e23d05554cfd5534469bbdfbe56d4f673)

- **作者**: Cheng Wan
- **时间**: 2026-09-27T23:46:50Z
- **提交信息**: [Refactor] Choose the boundaries of plain-TP dense layers and MoE layers from declarations (#41417)

### [583fada](https://github.com/sgl-project/sglang/commit/583fada954a8a7f2cb2b8e07735a336f2e20f6cf)

- **作者**: Yoni Gozlan
- **时间**: 2026-09-27T23:14:24Z
- **提交信息**: Port chat_parsing core (#40477)

Co-authored-by: Yoni Gozlan <yonigozlan@users.noreply.github.com>

### [78eee88](https://github.com/sgl-project/sglang/commit/78eee88113510d6b0d70f6978739d0845e2fff0f)

- **作者**: mrusanovsky
- **时间**: 2026-09-27T22:36:48Z
- **提交信息**: [Spec] Add LiLiCorr: a candidate-lattice reranker for DFlash drafts (#37462)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [14ab74e](https://github.com/sgl-project/sglang/commit/14ab74ef951e837da9d8a1dc5cb98292a21cd727)

- **作者**: Shangming Cai
- **时间**: 2026-09-27T21:16:23Z
- **提交信息**: [PD] Fan drain abort ACKs out to every decode peer of the room (#41402)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [b252ace](https://github.com/sgl-project/sglang/commit/b252aceffecd1e313cb5a03d3cbf56c99fc8c9ce)

- **作者**: Thomas Wang
- **时间**: 2026-09-27T17:53:21Z
- **提交信息**: [AMD] Update v4 cookbook for megamoe, fp8 kv attn, BCG (#41458)

### [e581520](https://github.com/sgl-project/sglang/commit/e581520c67a921feda4433bc4e4d41f3514a9d06)

- **作者**: Shunkangz
- **时间**: 2026-09-27T17:45:02Z
- **提交信息**: [HiCache] Add the page-unified KV load-back JIT kernel  (#39726)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: huangtingwei <141888744+huangtingwei9988@users.noreply.github.com>
Co-authored-by: Zhangheng <hzh0425@apache.org>

### [d10a09e](https://github.com/sgl-project/sglang/commit/d10a09ecf3310423ad01191bd9b1421f5436a23f)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-27T17:33:27Z
- **提交信息**: Add MiniMax arch fallback to auto parser resolution (#40930)

### [b280046](https://github.com/sgl-project/sglang/commit/b2800461e5bd5967f4aa00cbc8ab7337757f1867)

- **作者**: CuzMi
- **时间**: 2026-09-27T15:57:43Z
- **提交信息**: [Diffusion] Reuse bit-exact packed SwiGLU for Ming-Image (#41266)

### [1ba84a4](https://github.com/sgl-project/sglang/commit/1ba84a4b59e6aee78f90a41ac49a3df6d1778c8e)

- **作者**: Nguyễn Văn Cao Nguyên
- **时间**: 2026-09-27T15:57:18Z
- **提交信息**: [bench] Take each request's prompt length from the server (#39889)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [c311bc9](https://github.com/sgl-project/sglang/commit/c311bc961164be098bb281b743fdbb59ad35b1ba)

- **作者**: Yuan Luo
- **时间**: 2026-09-27T15:04:21Z
- **提交信息**: [VLM] Introduce FA4 into ViT for SM100/SM103 (#41344)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [588049f](https://github.com/sgl-project/sglang/commit/588049fe2eaad4bd41bf052a84b2110f52a1c331)

- **作者**: Mick
- **时间**: 2026-09-27T14:54:46Z
- **提交信息**: [diffusion] fix: run an all-valid attention mask on the backend's unmasked kernel (#41309)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [84622ce](https://github.com/sgl-project/sglang/commit/84622ce9d50cf9c606a976289e9f651493ce526c)

- **作者**: Kangrui Du
- **时间**: 2026-09-27T14:54:10Z
- **提交信息**: [diffusion] fix: lora-wrapped linears crash qwen-image and minimax-h3 inference (#41272)

Signed-off-by: rockdu <kangrdu@gmail.com>

### [a0ba196](https://github.com/sgl-project/sglang/commit/a0ba1968b161f1d2989aaacfdbd88a7e522d59a1)

- **作者**: Jianghai
- **时间**: 2026-09-27T10:32:20Z
- **提交信息**: [Diffusion] Apply latent-ids and packing to caller-provided initial latents (#34418)

Co-authored-by: aimicahchen <aimicahchen@tencent.com>
Co-authored-by: WenhaoZhang <42087078+niehen6174@users.noreply.github.com>

### [f1e62e3](https://github.com/sgl-project/sglang/commit/f1e62e3a2effef2cbddd02e24479f7069b06718a)

- **作者**: WenhaoZhang
- **时间**: 2026-09-27T09:58:54Z
- **提交信息**: [diffusion] feat: add MiniMax-H3 to ComfyUI integrated mode (#35990)

### [ae47bcd](https://github.com/sgl-project/sglang/commit/ae47bcd4da527933ae599a8e95d7058c26999d32)

- **作者**: WenhaoZhang
- **时间**: 2026-09-27T09:56:13Z
- **提交信息**: [diffusion] feat: minimax-h3 spectrum skip-step + fused RMSNorm/AdaLN (#35684)

### [2a14f65](https://github.com/sgl-project/sglang/commit/2a14f65fd7a1b00ec45711103f0e3f46bec5803e)

- **作者**: WenhaoZhang
- **时间**: 2026-09-27T09:54:40Z
- **提交信息**: [diffusion] feat: support in-place lora merge/unmerge under layerwise offload (#36192)

### [37556c1](https://github.com/sgl-project/sglang/commit/37556c1b91494db583b01791720d49f275cae3bb)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-27T09:53:16Z
- **提交信息**: [mem_cache] Replace `cache_finished_req` with `insert_req`; `release_kv_cache` frees and unpins (#41281)

### [0bc074d](https://github.com/sgl-project/sglang/commit/0bc074db83286449b96198eb340dacdf89041650)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-27T08:57:12Z
- **提交信息**: [KDA+Kimi K3] Speed up SANA-Video residual gate add on H200 (#41305)

Co-authored-by: kernel-design-agents <334018530+kernel-design-agents@users.noreply.github.com>

### [aa7a976](https://github.com/sgl-project/sglang/commit/aa7a976807ea71320027713a8b90cf91cc1503c4)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-27T08:27:56Z
- **提交信息**: [qwen 3.8 next] Fuse small CUDA graph input buffer copies (#41166)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1286
- **最后更新**: 2026-09-27T05:52:14Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92804
- **最后更新**: 2026-09-28T00:43:14Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 11
- **主要提交者**: Rakul-Chauhan, Fangzhou Ai, Xun Sun

## AI分析总结

根据提交记录，对vllm-project/vllm仓库昨日提交的总结如下：

1.  **主要更新类型**
    *   **性能优化**：占主导，涉及MoE模型路由、注意力计算、池化操作、多流重叠等核心环节。
    *   **Bug修复**：修复了KV连接器注册超时、特定API格式支持、ROCm硬件兼容性及异步调度下的同步问题。
    *   **功能新增**：为快速启动功能（Fast Start）添加了健康检查端点。
    *   **重构/依赖更新**：切换前端依赖以使用开源版本。
    *   **开发流程优化**：调整了CI测试任务的配置。

2.  **关键变更点及其与项目整体方向的关系**
    *   **深度性能挖掘**：多项优化（如MiniMax2路由、避免阻塞复制、SM90稀疏MLA去同步、zentorch SDPA）直接服务于项目“快速、低成本”的核心目标，通过更精细的硬件利用和算法优化来降低延迟与提高吞吐。
    *   **增强稳定性与兼容性**：修复Mooncake注册超时、ROCm上CPU张量回退等问题，提升了框架在复杂分布式环境和多硬件平台下的鲁棒性，符合“简单、可靠”的易用性目标。
    *   **提升开发与部署体验**：添加`/health`端点便于监控，优化CI任务提高开发效率，均旨在让整个系统的使用和维护更加便捷。

3.  **对项目的影响和潜在意义**
    *   **性能提升**：一系列优化有望在特定模型和场景下（如MoE模型、DeepSeek系列、CPU MLA预填充）带来显著的推理速度提升和成本降低，增强项目竞争力。
    *   **生态与可靠性增强**：修复关键Bug和改善硬件支持，能吸引更多企业用户和开发者，巩固项目作为生产级LLM服务框架的地位。
    *   **基础设施完善**：前端依赖切换、健康检查端点等改进，使项目的构建、部署和监控体系更加健壮。

4.  **值得关注的技术点**
    *   **MiniMax2路由集成**：在非单位路由缩放（non-unit routed scaling）场景下使用融合的MiniMax2路由，是提升MoE模型效率的针对性优化。
    *   **避免GPU-CPU同步阻塞**：在FlashInfer元数据构建中避免池化的`seq_lens`复制操作，是消除异构计算中常见性能瓶颈的典型实践。
    *   **ROCm多流重叠**：为特定模型启用的CSA2多流重叠技术，展示了对AMD GPU并行计算能力的深度挖掘。
    *   **zentorch SDPA**：在CPU MLA预填充中使用zentorch的Scaled Dot-Product Attention，是利用专用算子库优化特定硬件上关键操作的范例。

5.  **基于项目背景的发展影响**
    这些提交全面响应了vLLM项目“易用、快速、低成本”的定位。性能优化直接追求“快速”与“低成本”；Bug修复和依赖管理提升了“易用性”与可靠性；CI和监控改进则优化了项目自身的开发与部署效率，使其能更快速、稳定地迭代，从而更好地服务社区和用户，巩固其在开源LLM服务领域的领先地位。

## 详细提交记录

### [73859fe](https://github.com/vllm-project/vllm/commit/73859fec5865700c5b2021b22890cb3b2005f66e)

- **作者**: Anton Peganov
- **时间**: 2026-09-27T20:43:56Z
- **提交信息**: [Frontend] Switch Python Harmony dependency to oss-harmony (#55128)

Signed-off-by: Anton Peganov <apeganov@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [386ac25](https://github.com/vllm-project/vllm/commit/386ac2573e334a670a0406c9a2bca3a9981ac63d)

- **作者**: Chao Lei
- **时间**: 2026-09-27T19:47:36Z
- **提交信息**: [Bugfix][KV Connector] Retry Mooncake bootstrap registration on timeout (reopens #55763) (#58919)

### [187c81b](https://github.com/vllm-project/vllm/commit/187c81b32d2233b8caccc0eabc2519301e99e955)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-27T19:47:07Z
- **提交信息**: [ROCm][Bugfix] Fall back to default GEMM for CPU tensors on ROCm builds (#58923)

Signed-off-by: fai <fangzhouai@gmail.com>

### [231fdb8](https://github.com/vllm-project/vllm/commit/231fdb83cccf18b0c96ab874fe210820025b3857)

- **作者**: Jiangyun Zhu
- **时间**: 2026-09-27T19:37:33Z
- **提交信息**: [Perf][MoE] Use fused MiniMax2 routing with non-unit routed scaling (#58880)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [e790015](https://github.com/vllm-project/vllm/commit/e7900156e130c9880eb03b7c1f2df32820e7a2be)

- **作者**: Xun Sun
- **时间**: 2026-09-27T17:48:54Z
- **提交信息**: [Fast Start] Add `/health` endpoint for the weight cache daemon (#58552)

Signed-off-by: Xun Sun <UNIDY2002@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [2b9b55c](https://github.com/vllm-project/vllm/commit/2b9b55c7f1bd344d07ca5545cd31735e580b2d1a)

- **作者**: Artem Perevedentsev
- **时间**: 2026-09-27T17:17:34Z
- **提交信息**: [Bugfix] Support repsonse_format + tool_choice=auto (#56086)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>
Co-authored-by: pablopupo <145598901+pablopupo@users.noreply.github.com>
Co-authored-by: hubunt <150658615+hubunt@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [0376f81](https://github.com/vllm-project/vllm/commit/0376f81530336d90b3bba85cdea3284ff2ebde64)

- **作者**: Frank Wang
- **时间**: 2026-09-27T16:06:38Z
- **提交信息**: [Perf][Pooling] Avoid blocking seq_lens GPU-to-CPU copy for pooling in FlashInfer metadata builder (#57214)

Signed-off-by: frankwang28 <frank.wbb@hotmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>

### [44af287](https://github.com/vllm-project/vllm/commit/44af287ebe38d6dc4e102948025f5e3e175aefd6)

- **作者**: Shanshan Shen
- **时间**: 2026-09-27T15:48:01Z
- **提交信息**: [ROCm][Perf] Enable layer-aware CSA2 multi-stream overlap for DeepSeek-V4.1-Flash (#57407)

Signed-off-by: Shanshan Shen <87969357+shen-shanshan@users.noreply.github.com>

### [924707f](https://github.com/vllm-project/vllm/commit/924707f1bf94ff583d89bff7522ee12ff032c286)

- **作者**: Thang Nguyen
- **时间**: 2026-09-27T12:01:31Z
- **提交信息**: [CI] Split (H200 MIG 35GB) Spec Decode Speculators + MTP into 4 named jobs (#57237)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Thang Nguyen <thang.nguyen@inferact.ai>
Co-authored-by: Kimi Code <noreply@moonshot.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c8d7a7d](https://github.com/vllm-project/vllm/commit/c8d7a7dd13e2b40c013fb6d46be800937e4335fb)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-27T11:06:23Z
- **提交信息**: [Perf][Attention] Remove D2H sync from FlashInfer SM90 sparse MLA plan under async scheduling (#58684)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [24c9772](https://github.com/vllm-project/vllm/commit/24c9772d19251dbbf70fef75119546827c540c63)

- **作者**: Rakul-Chauhan
- **时间**: 2026-09-27T08:30:55Z
- **提交信息**: [Attention][CPU] Use zentorch SDPA for CPU MLA prefill (#54967)

Signed-off-by: Rakul Chauhan <rakul.chauhan@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-28
**监控日期**: 2026-09-27
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7090
- **最后更新**: 2026-09-28T00:47:45Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Ding Zuhao, kinnara

## AI分析总结

1. **主要更新类型**：均为功能新增。
2. **关键变更点及与项目方向的关系**：
   * **硬件支持扩展**：为华为昇腾NPU添加了MiniMax-H3模型的FastH3四步部署方案。这直接增强了项目在多样化硬件环境下的服务能力。
   * **模型支持扩展**：新增了对SenseNova-U1-A3B-MoT（一种混合专家模型）的支持。这丰富了项目可服务的模型生态。
   * **与项目方向的关系**：两项更新都紧密围绕项目“易用、快速、低成本地服务全模态模型”的核心目标。新增硬件支持旨在降低部署门槛与成本，新模型支持旨在拓宽服务范围，共同推动“全模态”（Omni-modality）愿景的实现。
3. **对项目的影响和潜在意义**：
   * **直接影响**：项目现可支持在昇腾NPU上部署特定H3模型，并能够服务SenseNova系列的MoE模型，拓宽了其应用边界。
   * **潜在意义**：增强了项目在国产AI芯片生态中的实用性，可能吸引更多相关开发者。同时，持续的模型支持扩充巩固了其作为通用多模态服务平台的定位。
4. **值得关注的技术点**：
   * Ascend NPU的部署采用了“FastH3四步部署”这一特定流程，这可能涉及针对该硬件与模型的组合优化。
   * 对SenseNova-U1-A3B-MoT（MoE）模型的支持，意味着项目需要有效处理混合专家模型的动态路由与推理调度，这是对服务框架灵活性的一个考验。
5. **基于项目背景的总结**：这些提交是项目践行“Easy, fast, and cheap”服务承诺的具体步骤。通过**持续扩展硬件兼容性（特别是国产芯片）和模型库**，项目正在积极构建更广泛、更易接入的推理服务生态，这有助于其从vLLM主分支独立出来后，形成更独特的差异化优势，并最终达成让“所有人”都能便捷使用多模态模型服务的最终目标。

## 详细提交记录

### [817f5d0](https://github.com/vllm-project/vllm-omni/commit/817f5d0e4d12751020a2ed8d7886b821eb605467)

- **作者**: kinnara
- **时间**: 2026-09-27T17:34:59Z
- **提交信息**: [Hardware][Ascend] Add FastH3 four-step deployment to MiniMax-H3 NPU … (#7149)

Signed-off-by: kinnara <kinnara1989@gmail.com>

### [1b97ff1](https://github.com/vllm-project/vllm-omni/commit/1b97ff11881173d9926c67cb9ace9457f5e57954)

- **作者**: Ding Zuhao
- **时间**: 2026-09-27T08:48:08Z
- **提交信息**: [Model] Support SenseNova-U1-A3B-MoT (MoE) (#8172)

Signed-off-by: Ding Zuhao <e1583181@u.nus.edu>

---
