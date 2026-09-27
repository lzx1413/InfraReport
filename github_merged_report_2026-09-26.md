# GitHub Stars 合并报告 - 2026-09-26

**合并日期**: 2026-09-27
**监控日期**: 2026-09-26
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


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
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


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2860
- **最后更新**: 2026-09-26T08:09:14Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2259
- **最后更新**: 2026-09-26T17:01:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6506
- **最后更新**: 2026-09-27T00:36:18Z

## 提交统计

- **昨日提交总数**: 15
- **提交者数量**: 1
- **主要提交者**: eigen

## AI分析总结

本次对 FlashInfer 仓库近期更新的综合分析显示，项目核心工作聚焦于 **高性能 GPU 内核的深度优化与自动化生成**，显著强化了对前沿模型与硬件的支撑能力。

**主要更新与关键变更** 更新全面覆盖了性能优化、功能新增与缺陷修复。核心变更集中于三点：一是 **深度适配 NVIDIA 最新 Blackwell 架构 (SM100/SM103)**，为 Kimi-K3、MiniMax-H3 等模型的视觉塔、注意力、MoE 路由等关键模块生成并集成了高度优化的内核后端；二是 **全面支持 FP8/NVFP4 等低精度量化格式**，以突破计算与内存瓶颈；三是 **通过名为 “Cake” 的自动化框架**，实现了从算子描述到跨架构（SM90, SM100/103）优化 CUDA 代码的生成、集成与调试，极大提升了内核开发与迭代效率。此外，优化深入至微架构层面，包括调度策略、指令依赖、共享内存布局与流水线重叠，并修复了部分内核中的性能回归与死锁问题。

**对项目的影响** 这些提交巩固了 FlashInfer 作为连接前沿模型与最新 GPU 硬件的关键桥梁地位。项目不仅为合作模型（如 Kimi-K3）和推理框架（如 vLLM）提供了即用的高性能后端，更通过建立成熟的 **自动化内核开发流水线**，构建了强大的工程护城河。这使其能快速响应新模型与新硬件的迭代需求，正从“提供优化内核”向“**提供生成优化内核的平台**”演进，推动了 Blackwell 架构与量化技术在推理侧的普及。

**值得关注的技术点** 包括：以 Cake 框架为代表的 **生成式内核开发流水线**，它自动化了代码生成、FFI 绑定与性能验证；针对 **微架构的极致性能调优**，涵盖 TMA 描述符预取、寄存器压力分析等底层优化；以及主机端 **基于动态规划的运行时调度**，能够根据输入形状与硬件特性选择最优内核参数与执行策略。这些技术共同构成了一个高效、可复现且持续进化的内核工程体系。

## 详细提交记录

### [e7bf98d](https://github.com/flashinfer-ai/flashinfer/commit/e7bf98dcb8f7c71feec4f3e68526d0af3b6fadee)

- **作者**: eigen
- **时间**: 2026-09-26T23:50:13Z
- **提交信息**: feat(cake_kimi_k3_mla): Cake-generated Kimi-K3 MLA FP8 paged attention backend for SM100/SM103 (backend="cake") (#5552)

## Summary

Adds a Cake-generated `backend="cake"` route for Kimi-K3 MLA attention
on Blackwell SM100 (B200) and SM103 (B300/GB300):

- BF16 I/O, FP8 E4M3 paged latent KV cache (page 64, latent 512 + 64
extra QK channels), FP8 query, TP8-local H12 and global H96.
- Two generated schedules cover low-head paged decode (`q_len = 1`),
packed variable-query / MTP batches (`q_len <= 8`, `cum_seq_lens_q`) and
incremental prefill against the paged cache (ragged KV, prefix-cache
reuse, changing page tables): swapped-AB row tiles 16/32/48/64/96
(packed (token, head) rows per CTA) for requests with at most 64 packed
rows or a longest KV below 16384 tokens, and a two-CTA wide kernel (128
packed rows per cluster, K tokens split across the pair, cluster launch
(2, 1, 1); two softmax warp-groups alternating KV tiles, three unpadded
36 KB tile-granular K stages next to two full V tiles (the rope chunks
under a 64 B swizzle behind their own tensor maps), V loaded by its own
TMA warp) for the H96 decode, MTP-H96 and long-KV prefill shapes; both
share the warp-per-row / CTA split-KV merge kernels. The host planner
(`flashinfer/mla/cake_kimi_k3_mla.py`) reproduces the Cake route choice
and both split planners, including the wide planner's per-wave cost term
(`WIDE_WAVE_COST_TILES = 8`: long KV streams take the largest split
count that still fits one wave of SM pairs).
- Reached through `trtllm_batch_decode_with_kv_cache_mla(...,
backend="cake")` (and the packed variable-Q form); direct API
`flashinfer.mla.KimiK3MlaFp8PagedAttention` /
`run_cake_kimi_k3_mla_fp8_paged_attention`. Caller-owned output, current
stream, CUDA-Graph replayable.
- Generated sources under `csrc/cake_kimi_k3_mla/{sm_100a,sm_103a}`
(Cake `loom/examples/weave/kimi_k3_mla_fp8_paged_attention.py` +
`kimi_k3_mla_wide.py`, producer revision
`9e6cb6587629044ff48fe799dc9a059a5b34244d` (kernel of record v8
`416871f4d` plus the exporter change `9e6cb658762`; both architectures
regenerated); internal design doc
`CAKE645_KIMI_K3_MLA_FP8_PAGED_ATTENTION.md`); registry filled by the
Cake generated-program exporter (`flashinfer/jit/cake_kimi_k3_mla.py`).
Tracker: #4254, request #4568, Linear CAKE-645.

- `backend="cake"` is shared with the Cake trtllm-MLA family (#4557).
`flashinfer/mla/_core.py` dispatches between the two by dimension tuple:
`cake_trtllm_mla_blackwell.supports_dimension_tuple(...)` (the tuples
that family generates, a named set) takes precedence, and everything
else with `backend="cake"` falls through to this route, which then
applies its own contract checks. Before this split the Kimi-K3 route was
unreachable through the public entry point (the #4557 block raised on
the (512, 64, H12/H96) tuples).

## Performance (same-session CUPTI cold-L2, CUDA-graph replay; Cake vs
the fastest existing FlashInfer route)

| row | route | B200 Cake us | B200 vs best FI | B300 Cake us | B300 vs
best FI |
|---|---|---:|---:|---:|---:|
| trace_h12_b1_q1_kv76800 | row tiles | 21.2 | **1.17x** | 20.4 |
**1.16x** |
| trace_h12_b2_q1_kv77699 | row tiles | 29.6 | **1.05x** | 29.6 |
**1.03x** |
| trace_h12_b3_q1_kv261120 | row tiles | 90.2 | **1.03x** | 91.1 |
**1.02x** |
| trace_h12_b4_q1_kv268800 | row tiles | 113.3 | **1.09x** | 114.0 |
**1.05x** |
| trace_h12_b5_q1_kv276480 | row tiles | 138.7 | **1.07x** | 140.1 |
**1.07x** |
| trace_h12_b6_q1_kv467751 | row tiles | 254.0 | **1.07x** | 256.3 |
**1.07x** |
| trace_h12_b7_q1_kv299613 | row tiles | 195.4 | **1.07x** | 197.7 |
**1.07x** |
| trace_h12_b8_q1_kv342305 | row tiles | 246.3 | **1.08x** | 248.6 |
**1.07x** |
| trace_h12_b9_q1_kv348705 | row tiles | 278.9 | **1.08x** | 280.2 |
**1.07x** |
| trace_h12_b10_q1_kv474166 | row tiles | 412.5 | **1.08x** | 411.7 |
**1.07x** |
| trace_h12_b11_q1_kv474405 | row tiles | 452.0 | **1.08x** | 450.6 |
**1.07x** |
| mirror_h96_b1_q1_kv76800 | wide | 25.0 | **1.10x** | 24.5 | **1.07x**
|
| mirror_h96_b2_q1_kv77699 | wide | 33.9 | **1.00x** | 34.4 | 0.98x |
| mirror_h96_b6_q1_kv467751 | wide | 345.7 | 0.99x | 347.3 | 0.97x |
| mirror_h96_b7_q1_kv299613 | wide | 259.5 | 0.99x | 254.2 | 0.98x |
| mirror_h96_b8_q1_kv342305 | wide | 337.9 | 1.00x | 333.3 | 0.97x |
| mtp_h12_b8_q2_kv342305 | row tiles | 257.4 | **1.22x** | 252.9 |
**1.21x** |
| mtp_h12_b8_q4_kv342305 | row tiles | 277.1 | **1.15x** | 263.7 |
**1.19x** |
| mtp_h12_b8_q8_kv342305 | wide | 338.8 | 0.99x | 331.4 | 0.98x |
| mtp_h96_b8_q2_kv342305 | wide | 651.4 | **1.09x** | 642.9 | 0.99x |
| mtp_h96_b8_q4_kv342305 | wide | 970.8 | **1.02x** | 930.9 | 0.99x |
| mtp_h96_b8_q8_kv342305 | wide | 1859.6 | **1.14x** | 1846.7 |
**1.08x** |
| prefill_h12_b1_q2048_kv131072 | wide | 2775.7 | 1.00x | 2728.1 | 0.97x
|
| prefill_h12_b2_q512_kv32768 | wide | 345.5 | **1.14x** | 342.1 |
**1.08x** |
| prefill_h12_b4_q1024_kv8192 | row tiles | 521.5 | 0.70x | 473.7 |
0.75x |
| prefill_h96_b1_q2048_kv131072 | wide | 21019.1 | **1.01x** | 21477.2 |
0.98x |
| prefill_h96_b2_q512_kv32768 | wide | 2737.0 | 0.97x | 2705.6 | 0.96x |

`vs best FI` = fastest of `auto` / `trtllm-gen` / `cute-dsl` divided by
Cake (>1 = Cake faster); CUPTI cold-L2 medians under CUDA-graph replay,
same session (B200 `nsc-svg-slurm-1-gpu-157`, B300 `pool0-0048`; Cake
kernel of record v8 `416871f4d` on both GPUs, gate steps `8708227f` /
`f9bc9e96`). `route` is the schedule the planner selects for the row.

The route is faster than every existing FlashInfer backend on all 11
serving-trace H12 decode rows, the MTP-H12 q2/q4 rows, the H96 b1 decode
row, the MTP-H96 q8 row and the H12 b2 prefill row on both GPUs, plus
the H96 b2 decode row, MTP-H96 q2/q4 and the H96 b1 prefill row on B200
(20/27 rows on B200, 16/27 on B300). It remains **slower** than
`cute-dsl` on B200 on the H96 b6 decode row (0.99x), MTP-H12 q8 (0.99x)
and the long H12 b1 prefill row (0.995x), and sits at the single-session
noise floor on the H96 b7/b8 decode rows and the H96 b2 prefill row
(0.97-1.00x against `auto`, 0.99-1.01x against `cute-dsl`, which is the
same kernel on the H96 rows); on B300 it is slower on the long H96
decode rows (0.97-0.98x), MTP-H96 q2/q4 (0.99x), MTP-H12 q8 (0.98x) and
the long prefill rows (0.96-0.98x); `prefill_h12_b4` (KV 8192) stays on
the row tiles for numerical reasons at 0.70-0.75x. The v8 change
launches the split-KV merge as a programmatic dependent launch of the
attention kernel (the attention kernel signals
`griddepcontrol.launch_dependents` once a CTA's work is done; the merge
kernel carries the programmatic-stream-serialization launch attribute
and waits on `griddepcontrol.wait` before its first partial read): a
deterministic 0.5-0.8 us per split row on both GPUs (same-node paired
A/B against the previous programs: H96 b1 0.97x, b2 0.98x, H12 b1 0.98x,
b2 0.99x; long split rows within noise; split-1 rows unchanged). It came
out of an item-by-item structural comparison with the `cute-dsl` FP8 MLA
kernel: the other differences that keep this route's numerics (two MMA
issue warps, `cute-dsl`'s split heuristic, a direct-store epilogue)
measured neutral to slower on both GPUs and were not adopted.

## Baselines and their source PRs

The `vs best FI` column above compares against the two existing
FlashInfer routes of the same public entry points, resolved at this
branch's upstream merge-base `bf82326b0` (2026-09-25, #4557):

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

No upstream commit after the merge-base touched these files (`git log
bf82326b0..origin/main -- flashinfer/mla/_core.py
flashinfer/cute_dsl/attention/{mla_decode_fp8,mla_config,mla_dispatch}.py
flashinfer/cute_dsl/attention/monolithic
flashinfer/cute_dsl/attention/wrappers/batch_mla.py
flashinfer/artifacts.py` is empty at `origin/main` = `a3701b2ee`,
2026-09-25). The Cake route in this PR is compared against exactly those
implementations; the numbers in the internal design doc
`CAKE645_KIMI_K3_MLA_FP8_PAGED_ATTENTION.md` use the same pinned
FlashInfer revision.

## Unsupported (rejected explicitly)

sparse top-k MLA, attention sinks, LSE output, DCP, skip-softmax, FP16
softmax, PDL as a caller option (`enable_pdl`: the attention kernel is
an ordinary launch on the caller's stream; internally the route launches
its split-KV merge as a programmatic dependent of the attention kernel),
NVFP4 / uint8 caches, `multi_ctas_kv_counter_buffer`.

## Tests

- `tests/mla/test_cake_kimi_k3_mla.py` (22 cases): decode H12/H96 incl.
the long-KV wide-route set, MTP variable-Q (incl. the 60-row RT=64 case
and a wide-route H96 case), incremental prefill with prefix reuse,
wide-route prefill, route selection, CUDA-graph replay with a changed
page table on both routes, unsupported-option rejection, and six
host-only wide-split-planner cases (B200 / B300 SM counts); run on B200
(sm_100a, `nsc-svg-slurm-1-gpu-157`) and B300 (sm_103a, `pool0-0048`),
v8 programs on the generated programs of this PR head: **22 passed on
each GPU**. Upstream pre-commit hooks (mypy, ruff check, ruff format)
pass on the hand-written files.
- `tests/attention/test_trtllm_gen_mla.py -k trtllm_mla_blackwell`
(dispatch regression for the #4557 route): 18/18 pass on B200
(`nsc-svg-slurm-1-gpu-62`); on the B300 node (`pool0-0052`, B300 SXM6
AC, the 148-SM class) 12/18 pass and the same six `bf16_dispatch` cases
fail as for the previous heads (that family ships an `sm_103a_152`
program only — `TRT-LLM MLA target 'sm_103a_148' is absent from the
generated-source catalog` on 148-SM B300 nodes — reproduced at the
upstream baseline `bf82326b0` with no Kimi code present on the same node
class, i.e. a pre-existing, node-specific gap unrelated to this change).
- Export receipts (source-vs-generated host-plan + bitwise output parity
and ABBA CUPTI timing gates; denominator = 27 perf rows + the
64-row-tile coverage row, per arch): B200 27/28 rows pass every gate
(perf source/export geomean 0.9999 over 26 timed rows, per-row
0.997-1.002; correctness row 1.0015); B300 27/28 (perf geomean 0.9994,
per-row 0.987-1.004; correctness row 1.0013); host plans and outputs
bitwise identical on every timed row on both GPUs. The one failing row
on each GPU is `prefill_h96_b1` (a 21-22 ms tensor-bound kernel that
runs at the board power cap: the timing-quality gate rejects the SM
clock below 70 % of nominal -- 1260/1965 MHz on B200, 1140/2032 MHz on
B300; the plan and bitwise gates pass on it), reported as-is.

### Maintenance 2026-09-26 (head `538d3f442`)

- Branch rebuilt as `f0605ba0d` → `093143a91` → `538d3f442`: the shared
`.pre-commit-config.yaml` is no longer edited (the receipt-bound sources
under `csrc/cake_kimi_k3_mla/` opt out of clang-format through a
per-directory `.clang-format`), the dimension-tuple key in
`cake_trtllm_mla_blackwell.supports_dimension_tuple` is ruff-formatted,
and `tests/mla/test_cake_kimi_k3_mla.py` skips on SM100-family parts
without generated programs (the CI's VR200 / sm_107a node raised `no
generated route 'main_rt16'`).
- Generated programs and the source registry are byte-identical to the
previous head `ebdf30250` (`git diff ebdf30250 538d3f442` touches only
the four hand-written files), so the export receipts above still apply.

### Regeneration 2026-09-26 (head `1a94521a7`)

- Generated programs regenerated from Cake
`696fb0470029e2ce3ac6e31c2099937b731a8e50` (kernel of record
`f44f288ccbf`: the wide route's three unpadded 36 KB K stages next to
two full V tiles, rope tensor maps) on top of the scaffold `093143a91`;
hand-written files unchanged. Only the wide program (kernel + binding
pair per arch) and its registry entries differ from `538d3f442`: `git
diff --stat 538d3f442 1a94521a7` = 5 files, +560 / -310 (two
`*_kernel.cu` + two `*_binding.cu` under new content hashes, and the
registry).
- Performance table, tests and export receipts above refreshed for this
head.

### Regeneration 2026-09-26 (head `b4c8032c8`)

- Generated programs regenerated from Cake
`9794b1a3287262681d05498be7ba66d0d2afa437` (kernel of record v6:
coalesced re-referencing of the wide route's lazy E4M3 reference) on top
of the scaffold `093143a91`; hand-written files unchanged. Only the wide
program (kernel + binding pair per arch) and its registry entries differ
from `1a94521a7`: `git diff --stat 1a94521a7 b4c8032c8` = 5 files, +157
/ -107 (two `*_kernel.cu` + two `*_binding.cu` under new content hashes,
registry entries).
- Performance table, tests and export receipts above refreshed for this
head (B200 `nsc-svg-slurm-1-gpu-119` step `07861d3d`: the clock-gated
row reports reportable loaded SM clock 1200/1965 MHz is below the
0.700000 fraction gate; B300 `pool0-0048` step `80e919d7`: reportable
loaded SM clock 1170/2032 MHz is below the 0.700000 fraction gate).
FlashInfer tests on the regenerated tree: 22 passed (B200) / 22 passed
(B300); dispatch regression `tests/attention/test_trtllm_gen_mla.py -k
trtllm_mla_blackwell`: 18/18 passed (B200) / 12/18 (six `bf16_dispatch`
cases fail as for every previous head) (B300, the documented
`sm_103a_148` gap); upstream pre-commit hooks clean.


### Regeneration 2026-09-26 (head
`75e5b5633e4db8574d09b0235adeddc310a67896`)

- sm_100a programs regenerated from Cake
`ccf4f66da17be937f355c84d780ae7e0ae5448b4` (kernel of record v7: the
SM100 specialization of the wide route drops packed f32x2 math and the
FMA exp2 emulation, which cost ~2 % of SM clock at the board power cap
for no cycle gain; a two-entry specialization change, forced-wide
correctness 8/8); the sm_103a programs are unchanged (v7 does not touch
the sm_103a IR). Hand-written files unchanged. `git diff --stat
b4c8032c8b17525d0b9c7e7981cd16cac45afa11
75e5b5633e4db8574d09b0235adeddc310a67896` = 3 files changed, 114
insertions(+), 144 deletions(-).
- B200 performance table, tests and export receipts above refreshed for
this head (B200 export on `nsc-svg-slurm-1-gpu-78`, allocation 2066038);
B300 values are those of `b4c8032c8b17525d0b9c7e7981cd16cac45afa11`.
FlashInfer tests on the regenerated tree: 22 passed (B200); dispatch
regression `tests/attention/test_trtllm_gen_mla.py -k
trtllm_mla_blackwell`: 18/18 pass (B200); upstream pre-commit hooks
clean.


### Regeneration 2026-09-26 (head
`b9a186f8a26c8212db125c5c59fcc5166afa450e`)

- sm_100a and sm_103a programs regenerated from Cake
`9e6cb6587629044ff48fe799dc9a059a5b34244d` (kernel of record v8
`416871f4d`: the split-KV merge is a programmatic dependent launch of
the attention kernel -- `griddepcontrol.launch_dependents` from the
attention kernel once a CTA is done, `griddepcontrol.wait` + the launch
attribute on both merge kernels; the exporter builds the merge stage
with PDL on and the attention stage as an ordinary launch). Hand-written
files unchanged. `git diff --stat
75e5b5633e4db8574d09b0235adeddc310a67896
b9a186f8a26c8212db125c5c59fcc5166afa450e` = 23 files changed, 729
insertions(+), 655 deletions(-).
- Performance table, tests and export receipts above refreshed for this
head on both GPUs (B200 export on `nsc-svg-slurm-1-gpu-157`, allocation
2068996; B300 export on `pool0-0048`, allocation 568175). FlashInfer
tests on the regenerated trees: 22 passed (B200) / 22 passed (B300);
dispatch regression `tests/attention/test_trtllm_gen_mla.py -k
trtllm_mla_blackwell`: 18/18 pass (B200) / 12/18 (the same six
`bf16_dispatch` cases as for every previous head on the 148-SM B300 node
class, the documented `sm_103a_148` gap of the #4557 family) (B300);
upstream pre-commit hooks clean on both.


🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a2f59b8](https://github.com/flashinfer-ai/flashinfer/commit/a2f59b8be39a8f763bb1fd2a60ca9c2ad23f916b)

- **作者**: eigen
- **时间**: 2026-09-26T23:44:50Z
- **提交信息**: feat(cake_backend): NVFP4 paged-KV MSA decode program for SM100/SM103 + layout contract (#5402)

<!-- .github/pull_request_template.md -->

## 📌 Description

Two things for the NVFP4 paged-KV MiniMax Sparse Attention (MSA) decode
on compute capability
10.0/10.3:

1. **The layout contract**
(`docs/design_docs/nvfp4_msa_paged_kv_layout.md`): the canonical planar
page map (K data, linear K scales, V data, swizzled V scales;
`page_layout(num_kv_heads)`), the
E2M1/E4M3 encoding, the four strided views the route verifies, and how
the vLLM producer, the
`flashinfer.msa_ops` reader and the MiniMax `nv_dev` kernels spell the
same bytes.

2. **A second reader of that contract, an experimental Cake-generated
decode program**
(`flashinfer.msa_ops.prepare_msa_nvfp4_sparse_decode(...,
backend="cake")`, backend under
`flashinfer/experimental/msa_nvfp4_decode/`): one persistent kernel per
decode step, plus a
second, non-persistent program that the host selects when every work
item of the step spans at
most four pages (the 257-token tail row): one eight-CTA thread-block
cluster per work item, two
CTAs per selected page, register `mma.sync` with the query heads as the
MMA rows, and a
distributed-shared-memory push merge in which each rank owns two of the
sixteen heads; the CTAs
retire as soon as their own stores and pushes are issued (no cluster
barrier at kernel exit: the
owning rank's transaction barrier already orders every peer push before
the owner stores). In the
   persistent kernel each work
item is one `(query token, KV head)` pair with its sixteen selected
128-token pages; a producer warp streams the packed pages and block
scales with two TMA requests per page side, which carry
the L2 evict-first cache-policy operand because every page is streamed
exactly once (the once-read lines
no longer displace the re-read query tiles and the pages of the other
CTAs in flight; the split-KV
programs keep the default policy, where the hint measured a 0.4 % loss
on B300) (each
item's first K tiles are requested before the next item's pages are
resolved, and its query
tile between the first and the second page pair's K tiles, so it is in
flight ahead of the
   first QK^T MMA), two
transform warpgroups dequantize them to BF16 in shared memory, the K
tiles stay resident in
tensor memory, and both MMAs run in the swapped `S^T` / `O^T`
orientation so the sixteen query
heads of a KV head form the MMA N dimension. Small batches split the
page pairs of every item
across 2, 4 or 8 CTAs that launch as one thread-block cluster (one rank
per split): each rank
owns 16/splits of the sixteen heads and receives the other ranks' FP32
partial slices for those
heads directly in its own shared memory (asynchronous
distributed-shared-memory stores that
complete transaction bytes on one barrier, landing in the query buffers
that are dead once the
item's last QK^T MMA has retired), then merges them locally in the same
summation order as a single CTA, so the output is bitwise
identical to the unsplit path (the (origin, sum) statistics of every
split travel on their own
transaction barrier, so the merge weights are computed before the slices
arrive; in the two-way case
each rank merges and pushes the peer-owned half of its partial first,
merges its own half while the
push is in flight, and writes that half into its own landing zone with
plain shared stores instead
of an asynchronous self-push); within a cluster only the
warps that address a peer CTA wait for the whole cluster's prologue, and
every CTA releases
its tensor memory from an idle warp as soon as its last accumulator has
been read; the
caller-owned workspace is unchanged, so a prepared runner still launches
with no allocation
   and is CUDA-Graph capturable. `seqlen_q` in `[1, 32]` query tokens
per request attend causally (right-aligned). `k_global_scale` is folded
into the softmax scale
and `v_global_scale` applied in the epilogue, exactly as the contract
states.

Host side: `cake_jit.MODULES` registers one generated module per
architecture and split factor
(`sm_100a`, `sm_103a`; splits 1/2/4/8) and one short-item module per
architecture
(`cake_msa_nvfp4_decode_<arch>_short`; `max_pages` 4, `cluster` 4);
`cake_backend` validates the
four views against the contract, selects the short-item program from the
page count the planner
already knows, otherwise mirrors the split rule on the device's
resident-CTA count and carves the
   workspace;
nothing reads tensor contents on the host. `msa_sparse_decode_attention`
is unchanged and keeps
   serving its route; the new entry point is an explicit opt-in.

Correctness: `tests/experimental/test_cake_msa_nvfp4_decode.py` checks
the program against the
FP32 oracle of the existing route (`atol = rtol = 1e-2` on the BF16
output) on tail, uniform,
ragged, tensor-parallel (64/4, 32/2, 16/1, 8/1 heads) and multi-token
(`seqlen_q` 2, 4, 8) rows,
against the existing route on the same pages (the route at its own peer
criterion, whole-output
cosine >= 0.99 and relative Frobenius error <= 0.06, since it
accumulates at lower precision than
the oracle on the 32/2, 16/1 and multi-token geometries), on the 8/1
geometry the route's
allowlist declines, on the tail and the four-page
eight-heads-per-KV-head rows with the short-item
program (including CUDA-Graph replay across new selections), and after
CUDA-Graph replay with new
queries and selections written in place;
it also checks that launching allocates nothing and that the registered
argument plans match the
host binding.

Performance: the generated program was measured on B200 (sm_100a, 148
SMs) and B300 (sm_103a,
148 SMs) with the generated-program export runner, which times every row
three ways on the same
tensors and the same GPU with counterbalanced cold-L2 CUPTI graph
replays: the Cake production
source (parity), the exported program, and `msa_sparse_decode_attention`
(this repository's
packed-NVFP4 route, on the 30 rows whose head geometry its allowlist
serves; it declines the 8/1
row). The complete per-row tables are below. In short: the generated
program is 1.369-1.405x faster than the route on the batch-128
tensor-parallel rows
(32/2 and 16/1 heads) and 1.552-1.718x faster on every multi-token row
(`seqlen_q` 2, 4, 8), where the route also runs at its lower-precision
accumulation (relative Frobenius error 0.048-0.050 against the FP32
oracle, versus 0.001 for the
generated program); it is 1.069-1.097x faster on the batch-32 64K rows,
and now clearly ahead on the batch-128 64/4 row
(1.080x on B200, 1.100x on B300, from 1.036x / 1.032x in the previous
delivery: the evict-first
policy on the streamed pages takes the row from 47.55 to 45.50 us on
B200 and from 46.91 to 44.10 us
on B300 against the route's 49.15 and 48.51 us), on the single-item 1M
row (1.28x on B200, 1.28x on
B300), on the batch-1 and batch-8 long-KV rows that split one item
across CTAs (1.017-1.023x), on
the 257-token tail (1.066x on B200 and 1.062x on B300 with the
short-item program of the delivery
before the previous one, which executes no thread-block-cluster barrier
before its CTAs retire), and
on the batch-16 2-way row (1.018x on B200, 1.005x on B300 with the
split-2 program of the previous
delivery, whose two-way merge hides its local work, merge weights and
own-half write behind the
distributed-shared-memory flight; 12.16 and 11.87 us against the route's
12.38 and 11.94 us). Geometric mean over the 15 timed rows: 1.281 on
B200 and 1.272 on B300 (previous delivery of this
PR: 1.270 and 1.265; 15 of 15 rows above 1 on B200 and 15 of 15 on B300,
from 15 and 15). The split-KV programs (batch-16 2-way, batch-8 100K
4-way, batch-1 200K 8-way, single-item 1M 8-way)
are byte-identical to the previous delivery and their export times read
within 1 % of it (12.16 /
9.79 / 7.42 / 6.98 us on B200 against 12.16 / 9.82 / 7.42 / 7.01 us, and
11.87 / 9.54 / 7.23 / 6.85
us on B300 against 11.84 / 9.54 / 7.23 / 6.78 us; worst: the 1M row on
B300, 0.96 % slower); every
persistent-program row is faster than or within 1 % of its previous
export on both parts (the
batch-128 row 4.3 % / 6.0 % faster, the multi-token rows 0-1.5 %
faster), so no row is more than 1 %
slower than its previous export on either part. The same-GPU alternating
A/B of this delivery's persistent program against the previous one on
all
sixteen rows (six passes of 150 cold-L2 iterations, outputs bitwise
identical on every row) measured
the batch-128 row at 1.047x on B200 and 1.068x on B300, the multi-token
rows at 1.006-1.018x, and
every other row within 1 %; the split-KV programs are byte-identical to
the previous delivery. No row is a diagnostic row on this revision:
every row's source/export parity reads 0.972-1.002 on
B200 and 0.972-1.005 on B300 (gate 0.97). The single-item 1M row's first
measurement read 0.968 /
0.967 and failed that gate on both parts, so it was re-measured alone in
a second runner invocation
on the same GPU at the same producer and target revisions (its receipt
of record: 0.9725 / 0.9718,
1.26x / 1.28x faster than the route; the regenerated package of the
second invocation is
byte-identical to the first); the other 15 receipts per part are from
the first invocation.
`benchmarks/bench_cake_msa_nvfp4_decode.py` reproduces the comparison
with
`bench_gpu_time_with_cupti`.

Baselines and their source PRs: the **route** arm of every table is
`msa_sparse_decode_attention`
on its packed-NVFP4 paged-KV path (`packed_nvfp4_paged_kv_cc10`), run
from this branch's own
checkout (upstream merge-base `bf82326b0`, 2026-09-25, at measurement
time; the branch was then
rebased onto `main` `b6d920aad` for mergeability, which leaves the
package and the files below
untouched); no upstream commit after `bf82326b0` up to `b6d920aad`
touches the files below.
- #4982 (`ed3abc178`, 2026-09-17) — the route itself:
`csrc/msa_decode_nvfp4_specialized.cu`,
  `flashinfer/msa_ops/_nvfp4_decode_sm100.py`,
  `flashinfer/msa_ops/cute_dsl/sparse_decode_nvfp4_sm100.py` and
`flashinfer/msa_ops/msa_decode_nvfp4_specialized_workloads.json` (the
frozen export protocol
records the SHA-256 of each of these four files under
`benchmark_identity`), plus the FP32
reference in `tests/msa_ops/test_msa_nvfp4_decode_sm100.py` that the
correctness gates use as
  the oracle.
- #3655 (`868005910`, 2026-07-15) — the `msa_sparse_decode_attention`
entry point and the
`flashinfer/msa_ops/sparse_decode.py` dispatch that the route arm goes
through; amended before
the merge-base by #4039 (K/V views split from a packed paged KV cache),
#4058 (docs), #4324
(decode path improvements), #4355 (Blackwell minimal sparse attention
source kernels) and #4982.
- The **source** arm is not a FlashInfer baseline: it is the Cake
production dispatcher launching
the same generated kernel at the producer revision named under *Hardware
and protocol* (parity
check only). "Previous delivery of this PR" refers to the receipts of
the earlier regenerations
  on this PR (their target revisions are listed there as well).

Hardware utilization: both parts have 8 TB/s of HBM3e. Counting only the
packed KV bytes a row
touches (16 selected pages x 128 tokens x (64 B data + 8 B block scales)
x K and V per query token
and KV head), the generated program streams 3.32-3.42 TB/s on the
batch-128 row (41-43 % of peak), 4.07-4.27 TB/s
on the largest multi-token row (`seqlen_q` 8, 302 MB; 51-53 %) and
2.38-2.42 TB/s on the batch-32
64K rows (30-30 %); the existing route spans 1.5-3.1 TB/s on the same
rows. Those numbers
were compared against a same-GPU measured ceiling rather than the
datasheet: a streaming-only TMA
replay of the kernel's own page lists on its own grid saturates at
4.2-4.5 TB/s on B200 and 4.2 TB/s
on B300 (52-56 % of peak) for this sixteen-pages-per-item pattern with
the default L2 policy,
independent of ring depth, box shape, issuing-CTA count or L2 prefetch;
the L2 eviction policy does
move it: with the evict-first policy the same replay reaches 4.96 TB/s
on B200 and 4.95 TB/s on B300
(62 % of peak; 30.44 and 30.50 us on the batch-128 row against 36.32 and
36.31 us with the default
policy, measured on the export GPUs of this delivery), and a
register-load path streams the same
pages at 4.9-5.2 TB/s, so the bandwidth-bound rows run at 1.25-1.35x of
the default-policy TMA floor on B200 (the batch-128
row moved from 1.30x to 1.25x with the evict-first policy on its
once-streamed pages) and at 1.49x /
1.43x (batch-128) and 1.42x / 1.41x (batch-32 64K) of the evict-first
floor on B200 / B300; the
remaining gap is the software E2M1 -> BF16 dequantization stage (150 ns
per K tile, 245 ns per
shared-memory-bandwidth-bound V tile; a raw-CUDA probe that adds only
the kernel's per-chunk convert
to a rolling register-load stream drops it from 4.86 to 3.8 TB/s on the
batch-128 row). The rows below 10 MB of KV (batch 1-8, the
257-token tail, the single-item 1M row) are latency-bound: the streaming
floor on their pages is
4.1-4.4 us, the exported program takes 5.7-9.8 us and the existing route
6.1-10.0 us; the
backend runs a second, non-persistent program for decode steps whose
work items span at most
four pages (the 257-token tail row): one eight-CTA thread-block cluster
per work item, two CTAs per
selected page with four warps of sixteen tokens each, the E2M1 pages
dequantized to BF16 in shared
memory and consumed by register `mma.sync` with the query heads as the
MMA rows, and a
distributed-shared-memory push merge in which each rank owns two heads
(7 KiB received per rank).
The previous delivery's eight-CTA form (four CTAs per item before it)
took the tail from 6.78 to
6.37 us on B200 and from 6.72 to 6.24 us on B300, 0.13 us behind the
route's single 4-warp
`mma.sync` kernel on both parts. The previous delivery removed the
thread-block-cluster barrier that the program executed before its CTAs
retired: it followed the owning rank's output stores and the
peers' asynchronous partial-slice pushes and drained them onto the
critical path, while the
owner's transaction barrier already orders every push before the owner
stores and no CTA reads
another CTA's shared memory. Without an exit cluster barrier the tail
runs in 5.82 us on B200 and 5.70 us on B300 in this
delivery's receipts (5.82 and 5.73 us in the previous ones; same-GPU
alternating A/B against the
persistent program 1.277x and 1.279x), 0.35-0.42 us ahead of the route;
a plain-launch skeleton of the same eight-CTA program
measures about 1.5 us, and the remaining time is the per-item metadata
chain, the dequantization,
the MMA and the merge. The previous delivery's persistent program
changed only the split merge: the (origin, sum) statistics of
every split travel on their own transaction barrier so the owners
compute the merge weights before
the slices arrive, and in the two-way exchange each rank merges and
pushes the peer-owned half of
its FP32 partial first, merges its own half while the push is in flight
(0.46-0.50 us of
distributed-shared-memory flight and barrier wake-up per item, measured
with a timestamp after the
last asynchronous store) and writes that half into its own landing zone
with plain shared stores,
halving the transaction bytes the owner waits for; same shared-memory
layout and summation order, so
the outputs are bitwise identical to the previous program on every row.
In the same-GPU alternating
A/B that took the batch-16 2-way row from 12.03 to 11.75 us on B200 and
from 11.66 to 11.39 us on
B300 (1.024x on both parts) and left the other fifteen rows within 1 %;
in this delivery's receipts
the row reads 12.16 us on B200 and 11.87 us on B300 against the route's
12.38 and 11.94 us (the
split-KV programs are byte-identical to the previous delivery). This
delivery's persistent
single-split program adds the L2 evict-first cache-policy operand to its
raw page loads: every page
is streamed exactly once, so with the default policy the once-read lines
displaced the re-read query
tiles and the pages of the other CTAs in flight. Same shared-memory
layout and summation order,
outputs bitwise identical on every row; in the same-GPU alternating A/B
the batch-128 row goes from
47.39 to 45.27 us on B200 (1.047x) and from 46.46 to 43.49 us on B300
(1.068x), the multi-token rows
gain 0.6-1.8 % and every other row stays within 1 %. On the split-KV
programs the same hint measured
a 0.4 % loss on B300 and a wash on B200 (pass ranges disjoint in both
cases), so those programs keep
the default policy. The persistent program of the delivery before the
previous one was
byte-identical to the one before it, which had requested each item's
query tile between the first and the second page
pair's K tiles instead of after all four of the item's first K tiles,
which moved the B300 rows
0.4-2.0 % and left B200 within 1 % either way, and the revisions before
it had moved the
batch-1 8-way split rows 1.7-3.2 % and the batch-8 4-way row 0.6-1.6 %
by requesting the query
tile after the item's first K tiles instead of before its page slots are
resolved, the batch-1
8-way split rows 4-5 %, the 4-way row 2-3 %, the 2-way row 1-2 % and the
257-token tail 6-7 % by
letting the producer, transform and PV warps of every CTA start the
first item as soon as their own
CTA's barriers and tensor memory are published (only the softmax warps,
which receive the partial
slices, and the QK^T MMA warp, which releases the landing zones, wait
for the whole cluster) and by
releasing the 256 tensor-memory columns from the otherwise idle warp as
soon as the softmax warps
have read their last accumulator (which also moved the 128-item
bandwidth rows 0.5-2 %), the batch-1 8-way rows 7 % and the 4-way row
4-5 % by having the QK^T MMA warp release
each rank's Q^T landing zone with one cluster-multicast
`tcgen05.commit`, deciding the exponent
origins of all sixteen heads with one warp-uniform test and reducing the
epilogue's head sums
with a transpose-reduce, the split rows 8-15 % by merging through a
thread-block cluster instead
of global memory, another 1-8 % by pushing each rank's partial slice
straight into the owning
rank's shared memory without a merge-completion handshake, and 5-7 % by
issuing each item's
first K tiles before the next item's page gather and reading the
received partial slices at
most 2-way bank-conflicted. A self-loading register-load transform
design is the recorded next
step for the bandwidth rows; the per-row `Export KV GB/s` column in the
per-shape summary below
is the number to compare against.

## 🔍 Related Issues

The MSA NVFP4 paged-KV decode route and its layout, and the MiniMax
`nv_dev` reference kernels.

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

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: this PR (the layout contract document is the tracking
artifact until a dedicated issue is opened).
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

```experimental-tests
tests/experimental/test_cake_msa_nvfp4_decode.py
```

## Reviewer Notes

The generated `csrc/cake_msa_nvfp4_decode/sm_10xa/*.cu` files are
emitted by the export and are
excluded from formatting hooks; review the host layer
(`cake_backend.py`, `cake_jit.py`, the
`msa_ops` entry point), the tests and the tables. Measurements below are
from the export runner's
receipts (per-row absolute latencies, ratios, correctness and drift
gates).

## Generated-program export evidence

Three arms on the same tensors and the same GPU, in counterbalanced
groups of cold-L2 CUPTI graph replays: **source** = the Cake production
dispatcher launching the same generated kernel (parity), **export** =
the exported TVM-FFI entry loaded through the FlashInfer JIT
registration in `cake_jit.py`, and **route** =
`flashinfer.msa_ops.msa_sparse_decode_attention`, this repository's
packed-NVFP4 paged-KV decode route at the same revision, timed on the
rows whose head geometry its allowlist serves (it declines 8 query heads
per KV head). Every arm's output is checked against the FP32 oracle of
that route before and after timing: source and export at `atol = rtol =
1e-2` on the BF16 output, the route at its own peer criterion
(whole-output cosine >= 0.99 and relative Frobenius error <= 0.06, the
acceptance of its tests; it accumulates at lower precision than the
oracle on the 32/2, 16/1 and multi-token geometries). Source and export
outputs are compared bitwise; the export submit path is verified to
allocate nothing.

### Hardware and protocol

- `sm_100a`: NVIDIA B200, driver 580.82.07, PyTorch
2.13.0a0+9186a08b2c.nv26.07, CUDA 13.3.
- `sm_103a`: NVIDIA B300 SXM6 AC, driver 580.126.09, PyTorch
2.13.0a0+9186a08b2c.nv26.07, CUDA 13.3.
- CUPTI GPU-span timing, cold L2 before every sample,
`symmetric_external_cuda_graph` for all arms, 3 counterbalanced groups,
200 ms warmup and 100 ms reportable budget per arm and group; gates:
source/export >= 0.97, directional disagreement <= 0.05, endpoint drift
<= 0.02, SM clock >= 0.85 of the observed maximum in every
warmup/measurement phase.
- Target revision `2cb298ce2243d1609117919c25bf72a665839a89` (the PR
head after the previous delivery; producer Cake revision
`5b8027577c19eed8d7f99f49ae2fb3438d199331`); the generated sources carry
the module hashes recorded in `cake_jit.py`.
- Every row is re-measured in full for each delivery. On this revision
only the persistent single-split program changes (its raw page loads
carry the L2 evict-first cache-policy operand; the short-item and
split-KV programs are byte-identical to the previous delivery), and that
change was measured by same-GPU alternating A/B of the new program
against the previous one on all 16 rows on both parts before the export.
- Route baseline provenance: FlashInfer #4982 (route implementation and
FP32 oracle) on the #3655 entry point, run from this branch's checkout
(merge-base `bf82326b0`); the four implementation files and their
SHA-256 are recorded in the frozen protocol's `benchmark_identity`. Full
list under *Baselines and their source PRs* in the description.

### Per-shape results

| Shape | Geometry | Arch | Splits | Source us | Export us | Source /
Export | Route us | Route / Export | Route vs FP32 (cosine / rel Fro) |
Export KV GB/s | Export max abs err vs FP32 | Export max row rel L2 | SM
clock MHz (phase min-max) | Verdict |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---|
| tp1_b128_kv8k_q1 | B128 Hq64/Hkv4 KV 8192 | sm_100a | 1 | 45.44 |
45.50 | 0.9986 | 49.15 | 1.080 | 1.0000 / 0.001 | 3318 | 0.0010 | 0.0040
| 1965-1965 | pass |
| tp1_b32_kv64k_q1 | B32 Hq64/Hkv4 KV 65536 | sm_100a | 1 | 15.78 |
15.81 | 0.9980 | 17.34 | 1.097 | 1.0000 / 0.001 | 2388 | 0.0010 | 0.0038
| 1965-1965 | pass |
| tp1_b32_kv64k_q1_ragged | B32 Hq64/Hkv4 KV 50283..80789 | sm_100a | 1
| 15.90 | 15.94 | 0.9980 | 17.34 | 1.088 | 1.0000 / 0.001 | 2369 |
0.0010 | 0.0039 | 1965-1965 | pass |
| tp1_b8_kv100k_q1 | B8 Hq64/Hkv4 KV 100000 | sm_100a | 4 | 9.79 | 9.79
| 1.0000 | 10.02 | 1.023 | 1.0000 / 0.001 | 964 | 0.0010 | 0.0036 |
1965-1965 | pass |
| tp1_b1_kv200k_q1 | B1 Hq64/Hkv4 KV 200000 | sm_100a | 8 | 7.29 | 7.42
| 0.9826 | 7.58 | 1.022 | 1.0000 / 0.001 | 159 | 0.0005 | 0.0035 |
1965-1965 | pass |
| tp2_b64_kv16k_q1 | B64 Hq32/Hkv2 KV 16384 | sm_100a | 1 | 15.84 |
15.84 | 1.0000 | 22.27 | 1.406 | 0.9988 / 0.050 | 2383 | 0.0010 | 0.0038
| 1965-1965 | pass |
| tp4_b128_kv8k_q1 | B128 Hq16/Hkv1 KV 8192 | sm_100a | 1 | 15.84 |
15.87 | 0.9980 | 22.30 | 1.405 | 0.9988 / 0.050 | 2378 | 0.0010 | 0.0039
| 1965-1965 | pass |
| tp4_b1_kv1m_q1 | B1 Hq16/Hkv1 KV 1048576 | sm_100a | 8 | 6.78 | 6.98 |
0.9725 | 8.93 | 1.280 | 0.9989 / 0.048 | 42 | 0.0005 | 0.0026 |
1965-1965 | pass |
| tp8_b128_kv64k_q1 | B128 Hq8/Hkv1 KV 65536 | sm_100a | 1 | 15.74 |
15.71 | 1.0020 | declined | — | — | 2403 | 0.0010 | 0.0038 | 1965-1965 |
pass |
| tp1_b2_kv257_q1_tail | B2 Hq64/Hkv4 KV 257 | sm_100a | 1 | 5.82 | 5.82
| 1.0000 | 6.21 | 1.066 | 1.0000 / 0.001 | 76 | 0.0020 | 0.0030 |
1965-1965 | pass |
| tp1_b32_kv8k_q2 | B32 Hq64/Hkv4 q2 KV 8192 | sm_100a | 1 | 25.66 |
25.82 | 0.9938 | 40.48 | 1.568 | 0.9987 / 0.050 | 2924 | 0.0010 | 0.0041
| 1965-1965 | pass |
| tp1_b32_kv8k_q4 | B32 Hq64/Hkv4 q4 KV 8192 | sm_100a | 1 | 44.80 |
44.96 | 0.9964 | 75.07 | 1.670 | 0.9987 / 0.050 | 3358 | 0.0010 | 0.0041
| 1965-1965 | pass |
| tp1_b32_kv8k_q8 | B32 Hq64/Hkv4 q8 KV 8192 | sm_100a | 1 | 74.11 |
74.24 | 0.9983 | 126.53 | 1.704 | 0.9987 / 0.050 | 4068 | 0.0010 |
0.0041 | 1965-1965 | pass |
| tp4_b32_kv64k_q8 | B32 Hq16/Hkv1 q8 KV 65536 | sm_100a | 1 | 25.92 |
26.05 | 0.9951 | 40.93 | 1.571 | 0.9987 / 0.050 | 2898 | 0.0010 | 0.0039
| 1965-1965 | pass |
| tp1_b8_kv100k_q8 | B8 Hq64/Hkv4 q8 KV 100000 | sm_100a | 1 | 25.76 |
25.86 | 0.9963 | 41.02 | 1.587 | 0.9987 / 0.050 | 2920 | 0.0010 | 0.0040
| 1965-1965 | pass |
| tp1_b16_kv64k_q1 | B16 Hq64/Hkv4 KV 65536 | sm_100a | 2 | 12.10 |
12.16 | 0.9947 | 12.38 | 1.018 | 1.0000 / 0.001 | 1552 | 0.0010 | 0.0037
| 1965-1965 | pass |
| tp1_b128_kv8k_q1 | B128 Hq64/Hkv4 KV 8192 | sm_103a | 1 | 44.06 |
44.10 | 0.9993 | 48.51 | 1.100 | 1.0000 / 0.001 | 3424 | 0.0010 | 0.0040
| 2032-2032 | pass |
| tp1_b32_kv64k_q1 | B32 Hq64/Hkv4 KV 65536 | sm_103a | 1 | 15.55 |
15.55 | 1.0000 | 16.86 | 1.084 | 1.0000 / 0.001 | 2427 | 0.0010 | 0.0038
| 2032-2032 | pass |
| tp1_b32_kv64k_q1_ragged | B32 Hq64/Hkv4 KV 50283..80789 | sm_103a | 1
| 15.78 | 15.78 | 1.0000 | 16.86 | 1.069 | 1.0000 / 0.001 | 2393 |
0.0010 | 0.0039 | 2032-2032 | pass |
| tp1_b8_kv100k_q1 | B8 Hq64/Hkv4 KV 100000 | sm_103a | 4 | 9.47 | 9.54
| 0.9933 | 9.70 | 1.017 | 1.0000 / 0.001 | 990 | 0.0010 | 0.0036 |
2032-2032 | pass |
| tp1_b1_kv200k_q1 | B1 Hq64/Hkv4 KV 200000 | sm_103a | 8 | 7.10 | 7.23
| 0.9823 | 7.36 | 1.018 | 1.0000 / 0.001 | 163 | 0.0005 | 0.0035 |
2032-2032 | pass |
| tp2_b64_kv16k_q1 | B64 Hq32/Hkv2 KV 16384 | sm_103a | 1 | 15.68 |
15.65 | 1.0020 | 21.54 | 1.376 | 0.9988 / 0.050 | 2412 | 0.0010 | 0.0038
| 2032-2032 | pass |
| tp4_b128_kv8k_q1 | B128 Hq16/Hkv1 KV 8192 | sm_103a | 1 | 15.74 |
15.71 | 1.0020 | 21.50 | 1.369 | 0.9988 / 0.050 | 2403 | 0.0010 | 0.0039
| 2032-2032 | pass |
| tp4_b1_kv1m_q1 | B1 Hq16/Hkv1 KV 1048576 | sm_103a | 8 | 6.66 | 6.85 |
0.9718 | 8.77 | 1.280 | 0.9989 / 0.048 | 43 | 0.0005 | 0.0026 |
2032-2032 | pass |
| tp8_b128_kv64k_q1 | B128 Hq8/Hkv1 KV 65536 | sm_103a | 1 | 15.55 |
15.52 | 1.0021 | declined | — | — | 2432 | 0.0010 | 0.0038 | 2032-2032 |
pass |
| tp1_b2_kv257_q1_tail | B2 Hq64/Hkv4 KV 257 | sm_103a | 1 | 5.73 | 5.70
| 1.0054 | 6.05 | 1.062 | 1.0000 / 0.001 | 78 | 0.0020 | 0.0030 |
2032-2032 | pass |
| tp1_b32_kv8k_q2 | B32 Hq64/Hkv4 q2 KV 8192 | sm_103a | 1 | 24.96 |
24.99 | 0.9987 | 38.78 | 1.552 | 0.9987 / 0.050 | 3021 | 0.0010 | 0.0041
| 2032-2032 | pass |
| tp1_b32_kv8k_q4 | B32 Hq64/Hkv4 q4 KV 8192 | sm_103a | 1 | 42.98 |
43.01 | 0.9993 | 72.19 | 1.679 | 0.9987 / 0.050 | 3511 | 0.0010 | 0.0041
| 2032-2032 | pass |
| tp1_b32_kv8k_q8 | B32 Hq64/Hkv4 q8 KV 8192 | sm_103a | 1 | 70.78 |
70.75 | 1.0005 | 121.57 | 1.718 | 0.9987 / 0.050 | 4268 | 0.0010 |
0.0041 | 2032-2032 | pass |
| tp4_b32_kv64k_q8 | B32 Hq16/Hkv1 q8 KV 65536 | sm_103a | 1 | 25.12 |
25.18 | 0.9974 | 39.23 | 1.558 | 0.9987 / 0.050 | 2998 | 0.0010 | 0.0039
| 2032-2032 | pass |
| tp1_b8_kv100k_q8 | B8 Hq64/Hkv4 q8 KV 100000 | sm_103a | 1 | 25.12 |
25.18 | 0.9975 | 39.39 | 1.564 | 0.9987 / 0.050 | 2998 | 0.0010 | 0.0040
| 2032-2032 | pass |
| tp1_b16_kv64k_q1 | B16 Hq64/Hkv4 KV 65536 | sm_103a | 2 | 11.78 |
11.87 | 0.9920 | 11.94 | 1.005 | 1.0000 / 0.001 | 1590 | 0.0010 | 0.0037
| 2032-2032 | pass |

### Geometric means (rows with a timed route comparison)

| Arch | Rows | Route / Export geomean | Rows with Route / Export > 1 |
Source / Export geomean |
|---|---:|---:|---:|---:|
| sm_100a | 15 | 1.281 | 15/15 | 0.9948 |
| sm_103a | 15 | 1.272 | 15/15 | 0.9961 |

### Hardware stages

- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-22b65d55-561a-775f-12d6-f89fd42616bd`;
shapes `tp1_b128_kv8k_q1__sm_100a, tp1_b32_kv64k_q1__sm_100a,
tp1_b32_kv64k_q1_ragged__sm_100a, tp1_b8_kv100k_q1__sm_100a,
tp1_b1_kv200k_q1__sm_100a, tp2_b64_kv16k_q1__sm_100a,
tp4_b128_kv8k_q1__sm_100a, tp4_b1_kv1m_q1__sm_100a,
tp8_b128_kv64k_q1__sm_100a, tp1_b2_kv257_q1_tail__sm_100a,
tp1_b32_kv8k_q2__sm_100a, tp1_b32_kv8k_q4__sm_100a,
tp1_b32_kv8k_q8__sm_100a, tp4_b32_kv64k_q8__sm_100a,
tp1_b8_kv100k_q8__sm_100a, tp1_b16_kv64k_q1__sm_100a`.
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-d50f1d54-e7d5-408d-ae9d-9f14e2ce2f7c`; shapes
`tp1_b128_kv8k_q1__sm_103a, tp1_b32_kv64k_q1__sm_103a,
tp1_b32_kv64k_q1_ragged__sm_103a, tp1_b8_kv100k_q1__sm_103a,
tp1_b1_kv200k_q1__sm_103a, tp2_b64_kv16k_q1__sm_103a,
tp4_b128_kv8k_q1__sm_103a, tp4_b1_kv1m_q1__sm_103a,
tp8_b128_kv64k_q1__sm_103a, tp1_b2_kv257_q1_tail__sm_103a,
tp1_b32_kv8k_q2__sm_103a, tp1_b32_kv8k_q4__sm_103a,
tp1_b32_kv8k_q8__sm_103a, tp4_b32_kv64k_q8__sm_103a,
tp1_b8_kv100k_q8__sm_103a, tp1_b16_kv64k_q1__sm_103a`.

Target revision: `2cb298ce2243d1609117919c25bf72a665839a89`.

Benchmark execution: `symmetric_external_cuda_graph`; 3 counterbalanced
groups, 200.000 ms warmup and 100.000 ms reportable budget per
arm/group.

The complete semantic arguments and machine-readable receipts remain in
`summary.json`; the tables below retain every registered shape without
repeating those arguments.

### Per-shape results

| Shape | GPU | Route | Source ms | Export ms | Source / Export |
Correctness | Verdict |
|---|---|---|---:|---:|---:|---|---|
| tp1_b128_kv8k_q1__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.045440 | 0.045503 | 0.998615x | pass | pass |
| tp1_b32_kv64k_q1__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.015776 | 0.015808 | 0.997976x | pass | pass |
| tp1_b32_kv64k_q1_ragged__sm_100a | G0 |
msa_nvfp4_decode_sm_100a_split1 | 0.015904 | 0.015936 | 0.997992x | pass
| pass |
| tp1_b8_kv100k_q1__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split4 |
0.009792 | 0.009792 | 1.000000x | pass | pass |
| tp1_b1_kv200k_q1__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split8 |
0.007295 | 0.007424 | 0.982624x | pass | pass |
| tp2_b64_kv16k_q1__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.015840 | 0.015840 | 1.000000x | pass | pass |
| tp4_b128_kv8k_q1__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.015840 | 0.015872 | 0.997984x | pass | pass |
| tp4_b1_kv1m_q1__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split8 |
0.006784 | 0.006976 | 0.972477x | pass | pass |
| tp8_b128_kv64k_q1__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.015744 | 0.015712 | 1.002037x | pass | pass |
| tp1_b2_kv257_q1_tail__sm_100a | G0 | msa_nvfp4_decode_sm_100a_short |
0.005824 | 0.005824 | 1.000000x | pass | pass |
| tp1_b32_kv8k_q2__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.025664 | 0.025824 | 0.993804x | pass | pass |
| tp1_b32_kv8k_q4__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.044800 | 0.044960 | 0.996441x | pass | pass |
| tp1_b32_kv8k_q8__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.074113 | 0.074240 | 0.998289x | pass | pass |
| tp4_b32_kv64k_q8__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.025920 | 0.026048 | 0.995086x | pass | pass |
| tp1_b8_kv100k_q8__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split1 |
0.025760 | 0.025856 | 0.996287x | pass | pass |
| tp1_b16_kv64k_q1__sm_100a | G0 | msa_nvfp4_decode_sm_100a_split2 |
0.012096 | 0.012160 | 0.994737x | pass | pass |
| tp1_b128_kv8k_q1__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.044064 | 0.044096 | 0.999274x | pass | pass |
| tp1_b32_kv64k_q1__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.015552 | 0.015552 | 1.000000x | pass | pass |
| tp1_b32_kv64k_q1_ragged__sm_103a | G1 |
msa_nvfp4_decode_sm_103a_split1 | 0.015776 | 0.015776 | 1.000000x | pass
| pass |
| tp1_b8_kv100k_q1__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split4 |
0.009472 | 0.009536 | 0.993289x | pass | pass |
| tp1_b1_kv200k_q1__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split8 |
0.007104 | 0.007232 | 0.982301x | pass | pass |
| tp2_b64_kv16k_q1__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.015680 | 0.015648 | 1.002013x | pass | pass |
| tp4_b128_kv8k_q1__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.015744 | 0.015712 | 1.002037x | pass | pass |
| tp4_b1_kv1m_q1__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split8 |
0.006656 | 0.006849 | 0.971821x | pass | pass |
| tp8_b128_kv64k_q1__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.015552 | 0.015520 | 1.002062x | pass | pass |
| tp1_b2_kv257_q1_tail__sm_103a | G1 | msa_nvfp4_decode_sm_103a_short |
0.005728 | 0.005697 | 1.005441x | pass | pass |
| tp1_b32_kv8k_q2__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.024960 | 0.024992 | 0.998720x | pass | pass |
| tp1_b32_kv8k_q4__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.042976 | 0.043008 | 0.999256x | pass | pass |
| tp1_b32_kv8k_q8__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.070785 | 0.070753 | 1.000452x | pass | pass |
| tp4_b32_kv64k_q8__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.025120 | 0.025185 | 0.997419x | pass | pass |
| tp1_b8_kv100k_q8__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split1 |
0.025120 | 0.025184 | 0.997459x | pass | pass |
| tp1_b16_kv64k_q1__sm_103a | G1 | msa_nvfp4_decode_sm_103a_split2 |
0.011777 | 0.011872 | 0.991998x | pass | pass |

### Per-shape comparison: FlashInfer msa_sparse_decode_attention
packed-NVFP4 paged-KV route

| Shape | Baseline ms | Paired export ms | Baseline / Export |
|---|---:|---:|---:|
| tp1_b128_kv8k_q1__sm_100a | 0.049152 | 0.045503 | 1.080193x |
| tp1_b32_kv64k_q1__sm_100a | 0.017344 | 0.015808 | 1.097166x |
| tp1_b32_kv64k_q1_ragged__sm_100a | 0.017344 | 0.015936 | 1.088353x |
| tp1_b8_kv100k_q1__sm_100a | 0.010016 | 0.009792 | 1.022876x |
| tp1_b1_kv200k_q1__sm_100a | 0.007584 | 0.007424 | 1.021552x |
| tp2_b64_kv16k_q1__sm_100a | 0.022272 | 0.015840 | 1.406061x |
| tp4_b128_kv8k_q1__sm_100a | 0.022303 | 0.015872 | 1.405179x |
| tp4_b1_kv1m_q1__sm_100a | 0.008928 | 0.006976 | 1.279817x |
| tp1_b2_kv257_q1_tail__sm_100a | 0.006208 | 0.005824 | 1.065934x |
| tp1_b32_kv8k_q2__sm_100a | 0.040480 | 0.025824 | 1.567534x |
| tp1_b32_kv8k_q4__sm_100a | 0.075071 | 0.044960 | 1.669729x |
| tp1_b32_kv8k_q8__sm_100a | 0.126528 | 0.074240 | 1.704310x |
| tp4_b32_kv64k_q8__sm_100a | 0.040927 | 0.026048 | 1.571215x |
| tp1_b8_kv100k_q8__sm_100a | 0.041024 | 0.025856 | 1.586634x |
| tp1_b16_kv64k_q1__sm_100a | 0.012384 | 0.012160 | 1.018421x |
| tp1_b128_kv8k_q1__sm_103a | 0.048512 | 0.044096 | 1.100145x |
| tp1_b32_kv64k_q1__sm_103a | 0.016864 | 0.015552 | 1.084362x |
| tp1_b32_kv64k_q1_ragged__sm_103a | 0.016864 | 0.015776 | 1.068966x |
| tp1_b8_kv100k_q1__sm_103a | 0.009696 | 0.009536 | 1.016779x |
| tp1_b1_kv200k_q1__sm_103a | 0.007360 | 0.007232 | 1.017699x |
| tp2_b64_kv16k_q1__sm_103a | 0.021536 | 0.015648 | 1.376234x |
| tp4_b128_kv8k_q1__sm_103a | 0.021504 | 0.015712 | 1.368635x |
| tp4_b1_kv1m_q1__sm_103a | 0.008768 | 0.006849 | 1.280187x |
| tp1_b2_kv257_q1_tail__sm_103a | 0.006048 | 0.005697 | 1.061611x |
| tp1_b32_kv8k_q2__sm_103a | 0.038785 | 0.024992 | 1.551897x |
| tp1_b32_kv8k_q4__sm_103a | 0.072193 | 0.043008 | 1.678595x |
| tp1_b32_kv8k_q8__sm_103a | 0.121569 | 0.070753 | 1.718217x |
| tp4_b32_kv64k_q8__sm_103a | 0.039233 | 0.025185 | 1.557792x |
| tp1_b8_kv100k_q8__sm_103a | 0.039392 | 0.025184 | 1.564168x |
| tp1_b16_kv64k_q1__sm_103a | 0.011936 | 0.011872 | 1.005391x |

### Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

| Shape tag | Timed rows | Denominator | Source ms | Export ms | Source
/ Export |
|---|---:|---:|---:|---:|---:|
| all | 32 | 32 | 0.017429 | 0.017502 | 0.995841x |
| coverage | 2 | 2 | 0.011935 | 0.012015 | 0.993366x |
| fi_route | 30 | 30 | 0.017555 | 0.017635 | 0.995429x |
| perf | 30 | 30 | 0.017874 | 0.017946 | 0.996006x |

### Geomeans: FlashInfer msa_sparse_decode_attention packed-NVFP4
paged-KV route

| Shape tag | Timed rows | Denominator | Baseline ms | Paired export ms
| Baseline / Export |
|---|---:|---:|---:|---:|---:|
| all | 30 | 30 | 0.022515 | 0.017635 | 1.276729x |
| coverage | 2 | 2 | 0.012158 | 0.012015 | 1.011885x |
| fi_route | 30 | 30 | 0.022515 | 0.017635 | 1.276729x |
| perf | 28 | 28 | 0.023529 | 0.018125 | 1.298107x |

Complete denominator: **true** (32/32).

All gates passed: **true** (32/32).

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [b42f4ee](https://github.com/flashinfer-ai/flashinfer/commit/b42f4ee5123452d533746613f941e69d6813a25c)

- **作者**: eigen
- **时间**: 2026-09-26T23:26:36Z
- **提交信息**: feat(cake_backend): Kimi-K3 Stable LatentMoE front/tail projections (SM100a/SM103a) with generated programs (#5575)

## Summary

Generated-program export of the Cake Kimi-K3 Stable LatentMoE front /
tail projection kernels for `sm_100a` (B200) and `sm_103a` (B300 /
GB300) into `flashinfer/experimental/kimi_k3_latent_moe` (#4568, tracker
#4254), with the public experimental entry points
`flashinfer.kimi_k3_latent_moe.{prepare_,}kimi_k3_latent_moe_{front,tail}`
(`backend="cake"`).

Per rank and layer, around the routed experts of `nvidia/Kimi-K3-NVFP4`
(`KimiSparseMoeBlock`, latent width 3584):

```
front:  logits     = FP32(x @ gate_weight.T)                        [T, 896]      router logits
        latent     = BF16(x @ down_weight.T)                        [T, 3584]     routed-expert input
        shared_act = SiTU(x @ shared_gate.T, x @ shared_up.T)       [T, 6144/TP]  shared-expert intermediate
tail:   y   = KimiRMSNorm(sum of the P routed partials)             [T, 3584]     (eps 1e-5; caller-owned workspace)
        out = BF16(y[:, cols] @ up_weight[:, cols].T + shared_act @ shared_down.T)   [T, 7168]  (rank's latent slice; all-reduce outside)
```

- `cake_backend.py`: host planner mirroring the Cake production launcher
(`T <= 128`: one weight-streaming swapped-AB tcgen05 launch per stage,
the tail's KimiRMSNorm fused into it; `T > 128`: persistent 2-CTA
tcgen05 GEMM, the tail preceded by a one-pass RMSNorm kernel and
launched programmatic-dependent with trailing-wave stream-K), operand
validation, launch binding, CUDA-Graph-safe runners. Weights are the
checkpoint's `nn.Linear` BF16 tensors in the serving layout (`gate` /
`down` / `norm` / `up` replicated, shared experts `MergedColumnParallel`
+ `RowParallel`); nothing is copied or re-packed.
- `cake_jit.py`: the `MODULES` / `KERNELS` registries populated by the
Cake export protocol (56 exact-architecture programs: 28 per arch = 20
decode instances + 2 prefill front GEMMs + 2 RMSNorm trigger variants +
4 prefill tail GEMMs — per TP degree one default variant and one that
loads the weight boxes with the `evict_first` L2 policy, selected by the
planner for single-wave grids, T = 256 / 512). Both literals are
generated; do not edit by hand.
-
`csrc/cake_kimi_k3_latent_moe/{sm_100a,sm_103a}/*_{kernel,binding}.cu`:
112 generated sources (identities receipt-bound; a per-directory
`csrc/.clang-format` with `DisableFormat: true` keeps clang-format off
them, the shared `.pre-commit-config.yaml` is untouched).
- Limits: TP 1 and TP 8 only (no EP); TP 12 is out of scope (#4542);
SM100 / SM103 only.

## Evidence (Cake export protocol, producer
`04a8bdd762d5b36490e550810c8c05703d0d0ce0`, target
`3844dff5aed72bd807450cec1f1b00b1e8cc27d8`)

Every row runs the source (Cake production launcher `launch_for_eval`)
and the exported programs in counterbalanced CUDA-graph groups;
correctness = both arms against the FP32/BF16 torch reference (the Cake
reference module `kimi_k3_latent_moe_ref`; BF16 outputs `atol = rtol =
1e-2`, FP32 logits `1e-3`) plus bitwise `source == export` on every
output, and per-row plan parity (FlashInfer planner kernel keys / grids
/ stream-K plan == production plan on the device). Gates: source /
export `>= 0.94`, directional disagreement `<= 0.08`, endpoint drift `<=
0.02`, loaded SM clock `>= 0.85 x max` (measurement validity).

| arch | GPU | rows sealed | clock-unqualified (disclosed) | correct
(bitwise source == export) | source/export | steps |
|---|---|---|---|---|---|---|
| sm_100a | B200 | 49 / 60 | 9 clock-unqualified + 2 endpoint-drift | 51
/ 51 | 0.9997 - 1.0433 | `4bef4c9427386ba1e3f37889` (5 batches),
`5d5dc944f405b815b7da1ddc` (retry round + FlashInfer tests) |
| sm_103a | B300 | 49 / 60 | 9 clock-unqualified + 2 endpoint-drift | 51
/ 51 | 0.9973 - 1.0315 | `ca762d0829376b89e5a6b69d` (5 batches),
`4f2d6f1fec18159425f5b0aa` (retry round + FlashInfer tests) |

Clock-unqualified rows: the sustained dense tcgen05 GEMM rows run at the
power cap and the interleaved timing session sampled the loaded SM clock
below 0.85 x max after two bounded rounds (sampled / max MHz): sm_100a:
`front_tp1_m16384` 1342 / 1965 MHz (0.683), `front_tp1_m2048` 1612 /
1965 MHz (0.820), `front_tp1_m4096` 1342 / 1965 MHz (0.683),
`front_tp1_m8192` 1417 / 1965 MHz (0.721), `front_tp8_m16384` 1402 /
1965 MHz (0.713), `front_tp8_m8192` 1515 / 1965 MHz (0.771),
`tail_tp1_m16384` 1372 / 1965 MHz (0.698), `tail_tp1_m4096` 1545 / 1965
MHz (0.786), `tail_tp1_m8192` 1455 / 1965 MHz (0.740); sm_103a:
`front_tp1_m16384` 1470 / 2032 MHz (0.723), `front_tp1_m2048` 1627 /
2032 MHz (0.801), `front_tp1_m4096` 1447 / 2032 MHz (0.712),
`front_tp1_m8192` 1282 / 2032 MHz (0.631), `front_tp8_m16384` 1312 /
2032 MHz (0.646), `front_tp8_m8192` 1425 / 2032 MHz (0.701),
`tail_tp1_m16384` 1260 / 2032 MHz (0.620), `tail_tp1_m4096` 1470 / 2032
MHz (0.723), `tail_tp1_m8192` 1312 / 2032 MHz (0.646). Endpoint-drift
gate rows (completed measurement, correct + bitwise source == export,
ratio ~1.00; the `<= 0.02` drift gate guards clock movement across the
session and is sealed after one completed measurement): sm_100a:
`tail_tp1_m2048` ratio 0.9997, `tail_tp8_m16384` ratio 1.0003; sm_103a:
`front_tp8_m4096` ratio 1.0010, `tail_tp1_m2048` ratio 1.0002. Both arms
run the same byte-identical program (receipt `source_export_bitwise` on
every completed row), so no timing claim is made for the unqualified
rows; their configurations are correctness-covered by the FlashInfer
test below.

`pytest tests/experimental/test_cake_kimi_k3_latent_moe.py` (5 host-plan
tests incl. the weight-eviction plan field + GPU correctness for both
stages x TP {1, 8} x `T in {1, 8, 16, 128, 256, 4096, 8192, 16384}`,
bit-identical re-launch and CUDA-graph replay, `y` byte-exact on the
decode route, BF16 tolerance for the prefill one-pass RMSNorm which
lands within one BF16 ulp exactly as the production kernel does in the
Cake receipts) on the round-4 delivery: B200 39 passed, 24 warnings
(step `5d5dc944f405b815b7da1ddc`, nsc-svg-slurm-1-gpu-108), B300 39
passed, 24 warnings (step `4f2d6f1fec18159425f5b0aa`, pool0-0048).
Pre-commit (ruff, mypy, clang-format with the per-directory opt-out for
the generated `csrc/`) clean on every changed file.

<details><summary>sm_100a per-row receipts</summary>

| row (B200, sm_100a) | route | source | export | source / export |
correctness (both arms) | bitwise src == exp | verdict |
|---|---|---|---|---:|---|---|---|
| front_tp1_m1 | decode | 51.20 us | 50.98 us | 1.0044 | pass | yes |
sealed |
| front_tp1_m2 | decode | 51.52 us | 51.17 us | 1.0069 | pass | yes |
sealed |
| front_tp1_m4 | decode | 51.36 us | 50.91 us | 1.0088 | pass | yes |
sealed |
| front_tp1_m8 | decode | 51.49 us | 51.07 us | 1.0082 | pass | yes |
sealed |
| front_tp1_m16 | decode | 51.58 us | 51.13 us | 1.0088 | pass | yes |
sealed |
| front_tp1_m32 | decode | 53.21 us | 53.09 us | 1.0024 | pass | yes |
sealed |
| front_tp1_m64 | decode | 54.82 us | 54.37 us | 1.0082 | pass | yes |
sealed |
| front_tp1_m128 | decode | 59.58 us | 58.94 us | 1.0109 | pass | yes |
sealed |
| front_tp1_m256 | prefill | 60.99 us | 60.86 us | 1.0021 | pass | yes |
sealed |
| front_tp1_m512 | prefill | 87.84 us | 85.82 us | 1.0235 | pass | yes |
sealed |
| front_tp1_m1024 | prefill | 166.30 us | 166.06 us | 1.0014 | pass |
yes | sealed |
| front_tp1_m2048 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1612/1965 MHz) |
| front_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1342/1965 MHz) |
| front_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1417/1965 MHz) |
| front_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1342/1965 MHz) |
| front_tp8_m1 | decode | 22.34 us | 21.82 us | 1.0235 | pass | yes |
sealed |
| front_tp8_m2 | decode | 22.40 us | 21.86 us | 1.0249 | pass | yes |
sealed |
| front_tp8_m4 | decode | 22.30 us | 21.82 us | 1.0220 | pass | yes |
sealed |
| front_tp8_m8 | decode | 22.56 us | 21.97 us | 1.0270 | pass | yes |
sealed |
| front_tp8_m16 | decode | 22.72 us | 22.21 us | 1.0231 | pass | yes |
sealed |
| front_tp8_m32 | decode | 23.81 us | 23.39 us | 1.0178 | pass | yes |
sealed |
| front_tp8_m64 | decode | 26.34 us | 25.82 us | 1.0198 | pass | yes |
sealed |
| front_tp8_m128 | decode | 33.95 us | 33.54 us | 1.0124 | pass | yes |
sealed |
| front_tp8_m256 | prefill | 44.99 us | 44.67 us | 1.0072 | pass | yes |
sealed |
| front_tp8_m512 | prefill | 47.55 us | 47.10 us | 1.0095 | pass | yes |
sealed |
| front_tp8_m1024 | prefill | 82.81 us | 81.18 us | 1.0201 | pass | yes
| sealed |
| front_tp8_m2048 | prefill | 117.02 us | 116.67 us | 1.0030 | pass |
yes | sealed |
| front_tp8_m4096 | prefill | 243.52 us | 243.10 us | 1.0017 | pass |
yes | sealed |
| front_tp8_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1515/1965 MHz) |
| front_tp8_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1402/1965 MHz) |
| tail_tp1_m1 | decode | 33.09 us | 32.42 us | 1.0207 | pass | yes |
sealed |
| tail_tp1_m2 | decode | 33.09 us | 32.45 us | 1.0197 | pass | yes |
sealed |
| tail_tp1_m4 | decode | 33.12 us | 32.54 us | 1.0177 | pass | yes |
sealed |
| tail_tp1_m8 | decode | 33.18 us | 32.61 us | 1.0177 | pass | yes |
sealed |
| tail_tp1_m16 | decode | 34.43 us | 33.95 us | 1.0141 | pass | yes |
sealed |
| tail_tp1_m32 | decode | 34.91 us | 34.40 us | 1.0149 | pass | yes |
sealed |
| tail_tp1_m64 | decode | 36.80 us | 36.48 us | 1.0088 | pass | yes |
sealed |
| tail_tp1_m128 | decode | 43.39 us | 43.07 us | 1.0074 | pass | yes |
sealed |
| tail_tp1_m256 | prefill | 48.73 us | 48.38 us | 1.0073 | pass | yes |
sealed |
| tail_tp1_m512 | prefill | 61.98 us | 61.60 us | 1.0063 | pass | yes |
sealed |
| tail_tp1_m1024 | prefill | 111.62 us | 110.56 us | 1.0096 | pass | yes
| sealed |
| tail_tp1_m2048 | prefill | 202.75 us | 202.81 us | 0.9997 | pass | yes
| disclosed: endpoint-drift gate (correct + bitwise, ratio 0.9997) |
| tail_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1545/1965 MHz) |
| tail_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1455/1965 MHz) |
| tail_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1372/1965 MHz) |
| tail_tp8_m1 | decode | 8.29 us | 8.06 us | 1.0278 | pass | yes |
sealed |
| tail_tp8_m2 | decode | 8.32 us | 8.16 us | 1.0197 | pass | yes |
sealed |
| tail_tp8_m4 | decode | 8.42 us | 8.19 us | 1.0273 | pass | yes |
sealed |
| tail_tp8_m8 | decode | 8.54 us | 8.22 us | 1.0389 | pass | yes |
sealed |
| tail_tp8_m16 | decode | 11.71 us | 11.52 us | 1.0167 | pass | yes |
sealed |
| tail_tp8_m32 | decode | 12.38 us | 12.10 us | 1.0238 | pass | yes |
sealed |
| tail_tp8_m64 | decode | 13.31 us | 13.12 us | 1.0146 | pass | yes |
sealed |
| tail_tp8_m128 | decode | 15.62 us | 15.52 us | 1.0063 | pass | yes |
sealed |
| tail_tp8_m256 | prefill | 16.19 us | 15.52 us | 1.0433 | pass | yes |
sealed |
| tail_tp8_m512 | prefill | 20.54 us | 20.19 us | 1.0175 | pass | yes |
sealed |
| tail_tp8_m1024 | prefill | 26.81 us | 26.50 us | 1.0120 | pass | yes |
sealed |
| tail_tp8_m2048 | prefill | 40.51 us | 40.29 us | 1.0055 | pass | yes |
sealed |
| tail_tp8_m4096 | prefill | 66.72 us | 66.17 us | 1.0082 | pass | yes |
sealed |
| tail_tp8_m8192 | prefill | 116.51 us | 116.00 us | 1.0044 | pass | yes
| sealed |
| tail_tp8_m16384 | prefill | 228.35 us | 228.29 us | 1.0003 | pass |
yes | disclosed: endpoint-drift gate (correct + bitwise, ratio 1.0003) |

</details>

<details><summary>sm_103a per-row receipts</summary>

| row (B300, sm_103a) | route | source | export | source / export |
correctness (both arms) | bitwise src == exp | verdict |
|---|---|---|---|---:|---|---|---|
| front_tp1_m1 | decode | 51.42 us | 50.62 us | 1.0158 | pass | yes |
sealed |
| front_tp1_m2 | decode | 51.27 us | 50.88 us | 1.0075 | pass | yes |
sealed |
| front_tp1_m4 | decode | 51.55 us | 50.91 us | 1.0126 | pass | yes |
sealed |
| front_tp1_m8 | decode | 51.62 us | 51.07 us | 1.0106 | pass | yes |
sealed |
| front_tp1_m16 | decode | 51.65 us | 51.14 us | 1.0100 | pass | yes |
sealed |
| front_tp1_m32 | decode | 53.41 us | 52.90 us | 1.0097 | pass | yes |
sealed |
| front_tp1_m64 | decode | 54.66 us | 54.08 us | 1.0107 | pass | yes |
sealed |
| front_tp1_m128 | decode | 59.71 us | 59.62 us | 1.0016 | pass | yes |
sealed |
| front_tp1_m256 | prefill | 61.03 us | 60.80 us | 1.0037 | pass | yes |
sealed |
| front_tp1_m512 | prefill | 83.01 us | 83.23 us | 0.9973 | pass | yes |
sealed |
| front_tp1_m1024 | prefill | 154.47 us | 154.11 us | 1.0023 | pass |
yes | sealed |
| front_tp1_m2048 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1627/2032 MHz) |
| front_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1447/2032 MHz) |
| front_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1282/2032 MHz) |
| front_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1470/2032 MHz) |
| front_tp8_m1 | decode | 22.21 us | 21.82 us | 1.0176 | pass | yes |
sealed |
| front_tp8_m2 | decode | 22.34 us | 22.02 us | 1.0145 | pass | yes |
sealed |
| front_tp8_m4 | decode | 22.24 us | 21.89 us | 1.0161 | pass | yes |
sealed |
| front_tp8_m8 | decode | 22.56 us | 21.98 us | 1.0262 | pass | yes |
sealed |
| front_tp8_m16 | decode | 22.79 us | 22.27 us | 1.0230 | pass | yes |
sealed |
| front_tp8_m32 | decode | 23.87 us | 23.39 us | 1.0205 | pass | yes |
sealed |
| front_tp8_m64 | decode | 26.30 us | 25.82 us | 1.0186 | pass | yes |
sealed |
| front_tp8_m128 | decode | 33.95 us | 33.57 us | 1.0114 | pass | yes |
sealed |
| front_tp8_m256 | prefill | 42.50 us | 42.05 us | 1.0107 | pass | yes |
sealed |
| front_tp8_m512 | prefill | 45.15 us | 44.77 us | 1.0086 | pass | yes |
sealed |
| front_tp8_m1024 | prefill | 77.66 us | 76.64 us | 1.0134 | pass | yes
| sealed |
| front_tp8_m2048 | prefill | 111.62 us | 111.20 us | 1.0037 | pass |
yes | sealed |
| front_tp8_m4096 | prefill | 230.53 us | 230.31 us | 1.0010 | pass |
yes | disclosed: endpoint-drift gate (correct + bitwise, ratio 1.0010) |
| front_tp8_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1425/2032 MHz) |
| front_tp8_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1312/2032 MHz) |
| tail_tp1_m1 | decode | 32.77 us | 32.22 us | 1.0169 | pass | yes |
sealed |
| tail_tp1_m2 | decode | 32.80 us | 32.29 us | 1.0159 | pass | yes |
sealed |
| tail_tp1_m4 | decode | 32.74 us | 32.16 us | 1.0179 | pass | yes |
sealed |
| tail_tp1_m8 | decode | 32.86 us | 32.43 us | 1.0133 | pass | yes |
sealed |
| tail_tp1_m16 | decode | 34.53 us | 34.18 us | 1.0103 | pass | yes |
sealed |
| tail_tp1_m32 | decode | 35.01 us | 34.62 us | 1.0111 | pass | yes |
sealed |
| tail_tp1_m64 | decode | 37.02 us | 36.67 us | 1.0096 | pass | yes |
sealed |
| tail_tp1_m128 | decode | 43.04 us | 42.69 us | 1.0082 | pass | yes |
sealed |
| tail_tp1_m256 | prefill | 48.70 us | 48.42 us | 1.0060 | pass | yes |
sealed |
| tail_tp1_m512 | prefill | 58.78 us | 58.50 us | 1.0049 | pass | yes |
sealed |
| tail_tp1_m1024 | prefill | 104.80 us | 104.80 us | 1.0000 | pass | yes
| sealed |
| tail_tp1_m2048 | prefill | 190.91 us | 190.88 us | 1.0002 | pass | yes
| disclosed: endpoint-drift gate (correct + bitwise, ratio 1.0002) |
| tail_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1470/2032 MHz) |
| tail_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1312/2032 MHz) |
| tail_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1260/2032 MHz) |
| tail_tp8_m1 | decode | 8.06 us | 7.97 us | 1.0120 | pass | yes |
sealed |
| tail_tp8_m2 | decode | 8.16 us | 8.03 us | 1.0159 | pass | yes |
sealed |
| tail_tp8_m4 | decode | 8.16 us | 8.06 us | 1.0120 | pass | yes |
sealed |
| tail_tp8_m8 | decode | 8.38 us | 8.13 us | 1.0315 | pass | yes |
sealed |
| tail_tp8_m16 | decode | 11.46 us | 11.33 us | 1.0113 | pass | yes |
sealed |
| tail_tp8_m32 | decode | 12.03 us | 12.00 us | 1.0027 | pass | yes |
sealed |
| tail_tp8_m64 | decode | 12.86 us | 12.90 us | 0.9975 | pass | yes |
sealed |
| tail_tp8_m128 | decode | 15.20 us | 15.14 us | 1.0042 | pass | yes |
sealed |
| tail_tp8_m256 | prefill | 15.55 us | 15.17 us | 1.0254 | pass | yes |
sealed |
| tail_tp8_m512 | prefill | 19.43 us | 19.07 us | 1.0185 | pass | yes |
sealed |
| tail_tp8_m1024 | prefill | 25.12 us | 24.99 us | 1.0051 | pass | yes |
sealed |
| tail_tp8_m2048 | prefill | 38.43 us | 38.43 us | 1.0000 | pass | yes |
sealed |
| tail_tp8_m4096 | prefill | 63.22 us | 62.91 us | 1.0048 | pass | yes |
sealed |
| tail_tp8_m8192 | prefill | 112.03 us | 111.55 us | 1.0043 | pass | yes
| sealed |
| tail_tp8_m16384 | prefill | 209.89 us | 209.55 us | 1.0016 | pass |
yes | sealed |

</details>
### Measured speedups (Cake contract, paired cold-L2 CUPTI graph timing
vs the fastest stock chain of each row; from
`design_doc/active/CAKE_621_KIMI_K3_LATENT_MOE.md`)

Decode tail, fused one-launch kernel (model-layout weights):

| row | B200 | B300 |
|---|---|---|
| tail_tp1 m1 / m2 / m4 / m8 | 1.071 / 1.085 / 1.076 / 1.056 | 1.081 /
1.091 / 1.086 / 1.069 |
| tail_tp1 m16 / m32 / m64 / m128 | 1.031 / 1.133 / 1.086 / 1.010 |
1.034 / 1.134 / 1.096 / 1.021 |
| tail_tp8 m1 / m2 / m4 / m8 | 1.806 / 1.984 / 1.977 / 1.958 | 1.772 /
1.980 / 1.737 / 1.947 |
| tail_tp8 m16 / m32 / m64 / m128 | 1.409 / 1.400 / 1.352 / 1.251 |
1.436 / 1.421 / 1.375 / 1.258 |

Absolute (B200 / B300): TP1 T1-T8 32.9-33.0 / 32.5-32.7 us (stock best
34.0-35.7), TP8 T1-T8 8.3-8.5 / 8.2-8.4 us (stock 14.6-16.6). Decode
front (16 rows per arch, all correct): TP1 1.41-1.68x, TP8 1.84-2.42x.
Prefill (persistent 2-CTA GEMMs + remainder-wave split-K / trailing-wave
stream-K + PDL; the tail GEMM streams its weight boxes `evict_first` on
single-wave grids): front 14/14 rows > 1 (TP1 1.75-1.92x, TP8
1.28-1.70x); tail TP8 7/7 (B200 1.27-1.54x, B300 1.29-1.56x); tail TP1
m256 / m512 / m1024 / m2048 / m4096 / m8192 / m16384 1.014 / 1.165 /
1.105 / 1.031 / 1.018 / 1.061 / 1.139 (B200) and 1.017 / 1.178 / 1.086 /
1.019 / 1.043 / 1.072 / 1.041 (B300). All 60 perf rows beat the fastest
stock chain on each GPU (the m256 tail row by a thin 1.4-1.7 %; the cold
weight stream at ~3.2 TB/s plus the norm launch hand-off are the
documented remaining gap).

### Baselines and their source PRs

- **Stock chain (Cake contract denominator, per row the fastest of):**
torch / cuBLAS `torch.mm` / `torch.addmm` (FP32-upcast or
`out_dtype=float32` router GEMM, BF16 latent / shared GEMMs, `addmm` for
the tail sum) and every FlashInfer `mm_bf16` backend that computes the
product (`auto`, `cudnn`, `cublaslt`, `tgv`, `tinygemm`, `cutlass`,
`cute-dsl`), `flashinfer.rmsnorm` for the tail norm, torch SiTU; eager
and CUDA-graph twins, the candidate timed in the winning form.
FlashInfer `mm_bf16`: `flashinfer/gemm/gemm_base.py`, origin #2070
(2062decf4, 2026-01-09, "BF16 GEMM for SM100, including CUTLASS, TGV
backends"), last touched by #5222 (2b16e3c76, 2026-09-16, cute-dsl
backend on SM107). FlashInfer `rmsnorm`: `flashinfer/norm/__init__.py`,
cute-dsl port #2428 (8bf921a7a, 2026-03-12), last touched by #4753
(5a8e62ac5, 2026-08-31). Torch: the `nvcr.io/nvidia/pytorch:26.01-py3`
container of the measurement steps.
- **Operator semantics reference:** `nvidia/Kimi-K3-NVFP4`
`modeling_kimi_linear.py` (`KimiSparseMoeBlock`, `KimiMLP`,
`KimiRMSNorm`, `SituAndMul`, `KimiMoEGate`; `text_config`: hidden 7168,
latent 3584, 896 experts, shared intermediate 6144, `rms_norm_eps` 1e-5,
SiTU beta 4 / linear beta 25); serving layout from vLLM
`models/kimi_k3/nvidia/{model.py, latent_moe_runner.py,
low_latency_gemm.py}` and SGLang `srt/models/kimi_k3.py` (main,
2026-09-26).
- **Test oracle:** the torch reference in
`tests/experimental/test_cake_kimi_k3_latent_moe.py` (this PR;
transcribed from the Cake reference module `kimi_k3_latent_moe_ref.py`).
- **Merge-base:** upstream `main` 78c6e1fbf (= #5564's merge commit); no
upstream commit after the merge-base touches the new files.

## Test

```
pytest tests/experimental/test_cake_kimi_k3_latent_moe.py
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9b727df](https://github.com/flashinfer-ai/flashinfer/commit/9b727df8af4858db231f7f3a436a8a87fe54e563)

- **作者**: eigen
- **时间**: 2026-09-26T22:09:57Z
- **提交信息**: perf(cake_kda): fused apply route for the unbounded affine BF16 prefill composite (operator export, pair-map prefix, fused apply kernel), H12 beta export fix (#5573)

Follow-up to #5565 (kernel round 1, merged as b7d82df5a); this branch is
rebased onto that merge and carries only the round-2 host commits and
the regenerated programs. The exported programs of the `cake_kda_bf16`
BF16 prefill family are regenerated from a new kernel revision on both
architectures, and the host runtime gains one schedule: the unbounded
affine composite's correction chain is replaced by an operator export
from the main pass, a pair-map prefix kernel and one fused apply kernel.
No API change; plan-cache keys of the unbounded affine composite change
(new schedule), everything else is untouched.

### 1. Composite schedule (unbounded gate only)

Sequences longer than the affine split run as windows: a main pass over
every window from a zero state, then the true state is carried through
the windows and applied. Until now the carry was applied by two further
chain passes over the whole sequence (correction + map), so the
composite cost three near-equal chains. The main pass now exports, per
32-token chunk and head, the chunk's linear operators (Qd/Kd/Kr, MQK,
the per-column decay, the restore scalar and the 32 sigmoid(beta) words,
one 292-word vector per chunk); a pair-map producer and a prefix kernel
(`M_{p+1} = M_p ⊙ D_p + bf16(M_p)·R_p`) turn them into per-window state
maps; the existing carry scan runs on those maps; and one fused apply
kernel (two independent block pipelines per CTA) applies the carried
state to the output tiles with `cp.reduce.async.bulk.tensor` straight
into the caller's output. The correction chain is still available behind
`CAKE_KDA_AFFINE_APPLY=0` and its programs stay exported.

Composite cost on GB300 (`bench_gpu_time`, cold L2, paired A B A B in
one process, FP32 pool, rows every 64 tokens): 2×8192 H16 chain 740.8 /
742.2 / 739.1 us vs apply route 629.1 / 632.7 / 629.0 us (1.174×); 8192
H16 396.7 → 356.1 us; 8224 H4 BF16 pool 166.4 → 144.8 us. Per-kernel
profile of the 2×8192 H16 apply route: main with export 269.9, apply
146.5, pair-map 101.5, prefix 55.0, scan 28.4 us (chain: three
main-sized passes 666.8 + scan 28.1 + `add_` 27.8).

Precision (FP32 token recurrence as reference, slow-decay inputs): apply
route vs chain differ by at most one BF16 ulp on `out`, ≤ 3.1e-4 on the
final state (values ≈ 1.5) and ≤ 2.4e-3 on window-boundary checkpoint
rows; rel L2 vs the reference changes in the fourth digit (e.g. 2×8192
H16 out 5.3545e-3 → 5.3550e-3).

### 2. Host

- `kda_prefill.py` / `cake_kda_tf32_runtime.py`: apply-route schedule
for the prepared BF16 affine composite (a9a5df80b): operator-export main
pass, pair-map + prefix + scan (hi/lo carry pair), fused apply kernel
reduce-adding into the output tail; the correction-chain schedule
remains behind `CAKE_KDA_AFFINE_APPLY=0`.
- Route restricted to the unbounded gate (`lower_bound is None`) and the
scan variant keyed on the route only (fbb8c2c00).

### 3. Defects found by the export validation (both fixed in the
regenerated programs)

- **Bounded gate on the apply route.** The exported operators are the
unbounded body's images and overflow FP32 under a lower bound (restore
factor ≈ 9e33 → NaN maps). The apply route is selected only for the
unbounded gate; the bounded composite keeps the #5565 correction chain
(its programs are unchanged).
- **H12 beta words at the wrong shared-memory offset.** The kernel
stages the prepared sigmoid(beta) above the restore factors by the raw
beta TMA box (516 B for the strided beta box, 816 B for the dense-H12
pair-packed (24, 17) box); the export copied a fixed block and so
published raw beta logits as sigmoid(beta) on H12. Source and export
agreed bitwise (same kernel) but the apply route diverged from the chain
by up to 0.10 on H12 outputs. The MMA warp now stores the beta words per
lane from the typed slot; verified apply-vs-chain within one BF16 ulp on
4096 / 8192 H12 and H16.

### 4. Validation

- 359 export rows per architecture: output, final state and checkpoint
rows bitwise equal between the source dispatcher and the exported API
after identical resets; exported/source GPU-time median 0.998 (max
1.029) on B200 and 0.999 on GB300; Triton/export min 1.16, median 3.64.
- `tests/kda/test_kda_prefill_plan_cache.py`,
`tests/kda/test_bf16_one_wave_route.py`,
`tests/kda/test_tf32_prefill.py`: 76 passed on B200 and on GB300
(per-architecture trees) and 76 passed on the combined tree of this PR
on B200 and on GB300. (The suite grows 71 → 76 with the apply-route
cases; the `CAKE_KDA_AFFINE_APPLY=0` fallback is covered, which is why
the correction-chain programs stay exported.)
- compute-sanitizer synccheck + memcheck on the seven registered KDA
launchers of the source tree: 0 errors on both architectures.
- rel L2 vs the Triton reference (out / state) unchanged on all 56 bench
rows on both architectures.

### Speedup vs Triton (bench_tb, same GPU, same inputs, FP32 state, rows
every 64)

Same harness as #5452 / #5543 / #5565 (serving-adapter layer call of the
prepared export vs the Triton `chunk_kda` path, fresh identically seeded
inputs per arm, FP32 state pool, checkpoint rows every 64 tokens; GPU
time = profiler CUDA time, event time = CUDA events around the call; one
lane per GPU). **All 56 rows beat Triton on GPU time and on event time
on both architectures**, and GPU time is 15–21 % below #5565 on the
unbounded composite rows the round changes while every other row stays
within −2.8 … +2.0 % of #5565 (within +1.0 % of #5543) on GPU time, i.e.
measurement noise on the bounded and short-sequence rows it does not
touch. Unbounded H16 layer rows (Kimi-Linear shape), GPU-time speedup vs
Triton:

| case | B200 #5543 → #5565 → this PR | GB300 #5543 → #5565 → this PR |
|---|---:|---:|
| 8192 | 1.32 → 1.47 → **1.78** | 1.39 → 1.51 → **1.84** |
| 16384 | 1.48 → 1.65 → **2.02** | 1.55 → 1.71 → **2.06** |
| 2x8192 | 1.05 → 1.18 → **1.49** | 1.11 → 1.24 → **1.51** |
| 3000+13384 | 1.33 → 1.46 → **1.82** | 1.40 → 1.54 → **1.84** |
| 4x4096 | 1.45 → 2.00 → 1.99 | 1.54 → 2.05 → 2.02 |
| 2x(8128+64) | 1.05 → 1.18 → **1.46** | 1.10 → 1.20 → **1.44** |
| 8x(1024+64) | 2.68 → 3.06 → 3.11 | 2.81 → 3.18 → 3.20 |
| 32768 | 1.57 → 1.74 → **2.13** | 1.65 → 1.81 → **2.15** |

(4×4096 and 8×(1024+64) run the sequential body below the affine split
and are unchanged by design.) On GB300 the 18 rows whose event time sits
more than 2 % above the #5543 recording are all faster than #5543 on GPU
time; that run shared its node with a concurrent pytest gate.
Re-measured three times on the quiet node against the #5543 tree
measured twice on the same node, this branch is below the #5543 tree on
GPU time in every arm and at or below it on event time on 17 of the 18
rows (the exception is the 13 us `k3_wrapper_h16 BS4×T64` row,
0.249–0.256 vs 0.242–0.249 ms), and the #5543 tree itself reproduces the
shift against its own recording (e.g. `k3_layer_h12 8192` event 0.649 /
0.637 ms vs the recorded 0.510 at identical GPU time), so the deficit is
the measuring node's host time, as in #5565; both trees beat Triton on
event time in every one of the 160 measurements (min 1.10x / 1.15x).

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5565 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2545 | 2.38x | 0.4610 | 1.59x | 2.36x → 2.38x | 0.0052/0.0036
|
| 16384 | 0.4137 | 2.79x | 0.6903 | 1.85x | 2.76x → 2.79x |
0.0052/0.0041 |
| 2x8192 | 0.4639 | 1.83x | 0.7018 | 1.39x | 1.81x → 1.83x |
0.0052/0.0042 |
| 3000+13384 | 0.4371 | 2.39x | 0.7084 | 1.65x | 2.37x → 2.39x |
0.0052/0.0041 |
| 4x4096 | 0.2421 | 2.90x | 0.4834 | 1.71x | 2.88x → 2.90x |
0.0052/0.0039 |
| 2x(8128+64) | 0.4615 | 1.84x | 0.7031 | 1.38x | 1.82x → 1.84x |
0.0052/0.0042 |
| 8x(1024+64) | 0.1205 | 3.11x | 0.3103 | 1.66x | 3.10x → 3.11x |
0.0041/0.0017 |
| 32768 | 0.7202 | 3.15x | 1.1258 | 2.13x | 3.12x → 3.15x |
0.0052/0.0043 |

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5565 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.3115 | 2.07x | 0.5411 | 1.43x | 2.06x → 2.07x | 0.0052/0.0038
|
| 16384 | 0.5139 | 2.45x | 0.8348 | 1.65x | 2.44x → 2.45x |
0.0052/0.0040 |
| 2x8192 | 0.4631 | 2.07x | 0.7519 | 1.44x | 2.05x → 2.07x |
0.0052/0.0039 |
| 3000+13384 | 0.5278 | 2.19x | 0.8470 | 1.51x | 2.18x → 2.19x |
0.0052/0.0038 |
| 4x4096 | 0.2454 | 3.32x | 0.5349 | 1.75x | 3.32x → 3.32x |
0.0052/0.0040 |
| 2x(8128+64) | 0.4657 | 2.07x | 0.7516 | 1.44x | 2.07x → 2.07x |
0.0052/0.0039 |
| 8x(1024+64) | 0.0986 | 4.52x | 0.3166 | 1.85x | 4.47x → 4.52x |
0.0052/0.0040 |
| 32768 | 0.9207 | 2.66x | 1.4197 | 1.82x | 2.64x → 2.66x |
0.0052/0.0041 |

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5565 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0142 | 3.81x | 0.1511 | 1.64x | 3.78x → 3.81x |
0.0053/0.0039 |
| BS16 x T64 | 0.0335 | 2.35x | 0.1696 | 1.67x | 2.36x → 2.35x |
0.0040/0.0017 |
| BS64 x T64 | 0.1006 | 2.05x | 0.2685 | 1.63x | 2.05x → 2.05x |
0.0040/0.0017 |
| BS16 x T128 | 0.0441 | 2.56x | 0.1825 | 2.07x | 2.56x → 2.56x |
0.0053/0.0040 |
| BS16 x T256 | 0.0632 | 2.95x | 0.2140 | 1.83x | 2.96x → 2.95x |
0.0052/0.0039 |
| BS16 x T(17..255) | 0.0356 | 3.22x | 0.1775 | 2.10x | 3.21x → 3.22x |
0.0052/0.0040 |

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5565 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0146 | 3.69x | 0.1500 | 1.64x | 3.71x → 3.69x |
0.0053/0.0040 |
| BS16 x T64 | 0.0317 | 2.72x | 0.1651 | 1.65x | 2.72x → 2.72x |
0.0053/0.0040 |
| BS64 x T64 | 0.1138 | 2.16x | 0.2899 | 1.45x | 2.16x → 2.16x |
0.0052/0.0040 |
| BS16 x T128 | 0.0461 | 2.86x | 0.1892 | 1.93x | 2.86x → 2.86x |
0.0052/0.0040 |
| BS16 x T256 | 0.0649 | 3.43x | 0.2307 | 1.71x | 3.39x → 3.43x |
0.0052/0.0040 |
| BS16 x T(17..255) | 0.0459 | 2.89x | 0.1957 | 1.91x | 2.87x → 2.89x |
0.0052/0.0040 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5565
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2937 | 2.09x | 0.4560 | 1.62x | 1.73x → 2.09x | 0.0040/0.0022
|
| 16384 | 0.5022 | 2.31x | 0.6644 | 1.93x | 1.88x → 2.31x |
0.0040/0.0019 |
| 2x8192 | 0.4944 | 1.74x | 0.6592 | 1.48x | 1.38x → 1.74x |
0.0040/0.0019 |
| 3000+13384 | 0.5283 | 2.00x | 0.6926 | 1.70x | 1.57x → 2.00x |
0.0040/0.0024 |
| 4x4096 | 0.4031 | 1.77x | 0.5281 | 1.58x | 1.76x → 1.77x |
0.0040/0.0020 |
| 2x(8128+64) | 0.5061 | 1.69x | 0.6741 | 1.46x | 1.36x → 1.69x |
0.0040/0.0020 |
| 8x(1024+64) | 0.1445 | 2.63x | 0.2708 | 1.96x | 2.60x → 2.63x |
0.0039/0.0020 |
| 32768 | 0.9014 | 2.54x | 1.0738 | 2.26x | 2.05x → 2.54x |
0.0040/0.0021 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5565
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.3664 | 1.78x | 0.5313 | 1.46x | 1.48x → 1.78x | 0.0040/0.0020
|
| 16384 | 0.6307 | 2.02x | 0.7956 | 1.76x | 1.63x → 2.02x |
0.0040/0.0021 |
| 2x8192 | 0.6528 | 1.49x | 0.8092 | 1.36x | 1.17x → 1.49x |
0.0040/0.0021 |
| 3000+13384 | 0.6451 | 1.82x | 0.8045 | 1.61x | 1.46x → 1.82x |
0.0040/0.0025 |
| 4x4096 | 0.4172 | 1.99x | 0.5335 | 1.78x | 2.01x → 1.99x |
0.0040/0.0022 |
| 2x(8128+64) | 0.6711 | 1.46x | 0.8370 | 1.32x | 1.19x → 1.46x |
0.0040/0.0021 |
| 8x(1024+64) | 0.1463 | 3.11x | 0.2757 | 2.12x | 3.00x → 3.11x |
0.0040/0.0021 |
| 32768 | 1.1607 | 2.13x | 1.3271 | 1.97x | 1.73x → 2.13x |
0.0040/0.0021 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5565 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0226 | 2.42x | 0.1556 | 1.61x | 2.40x → 2.42x |
0.0040/0.0021 |
| BS16 x T64 | 0.0412 | 1.98x | 0.1663 | 1.70x | 1.97x → 1.98x |
0.0039/0.0020 |
| BS64 x T64 | 0.1216 | 1.76x | 0.2536 | 1.60x | 1.75x → 1.76x |
0.0039/0.0020 |
| BS16 x T128 | 0.0551 | 2.12x | 0.1809 | 2.08x | 2.11x → 2.12x |
0.0040/0.0021 |
| BS16 x T256 | 0.0835 | 2.30x | 0.2080 | 1.89x | 2.28x → 2.30x |
0.0039/0.0020 |
| BS16 x T(17..255) | 0.0457 | 2.60x | 0.1679 | 2.22x | 2.56x → 2.60x |
0.0040/0.0023 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5565 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0227 | 2.40x | 0.1603 | 1.55x | 2.39x → 2.40x |
0.0040/0.0021 |
| BS16 x T64 | 0.0421 | 2.09x | 0.1667 | 1.65x | 2.12x → 2.09x |
0.0040/0.0020 |
| BS64 x T64 | 0.1474 | 1.70x | 0.2784 | 1.50x | 1.73x → 1.70x |
0.0040/0.0021 |
| BS16 x T128 | 0.0564 | 2.36x | 0.1785 | 2.10x | 2.40x → 2.36x |
0.0039/0.0021 |
| BS16 x T256 | 0.0870 | 2.61x | 0.2109 | 1.86x | 2.65x → 2.61x |
0.0040/0.0021 |
| BS16 x T(17..255) | 0.0601 | 2.24x | 0.1845 | 2.03x | 2.29x → 2.24x |
0.0039/0.0023 |

B200 (SM100, 148 SMs): 56/56 rows > 1 on both metrics; GPU time at or
below #5565 on 27/56 rows.

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5565 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2372 | 2.37x | 0.5239 | 1.38x | 2.37x → 2.37x | 0.0052/0.0041
|
| 16384 | 0.3852 | 2.74x | 0.7216 | 1.74x | 2.76x → 2.74x |
0.0052/0.0037 |
| 2x8192 | 0.3833 | 2.01x | 0.7135 | 1.34x | 2.02x → 2.01x |
0.0052/0.0039 |
| 3000+13384 | 0.4064 | 2.35x | 0.7367 | 1.55x | 2.35x → 2.35x |
0.0052/0.0039 |
| 4x4096 | 0.2255 | 2.82x | 0.5182 | 1.59x | 2.82x → 2.82x |
0.0052/0.0039 |
| 2x(8128+64) | 0.3853 | 2.00x | 0.7166 | 1.34x | 2.00x → 2.00x |
0.0052/0.0039 |
| 8x(1024+64) | 0.1094 | 3.08x | 0.3661 | 1.49x | 3.08x → 3.08x |
0.0040/0.0016 |
| 32768 | 0.6732 | 3.10x | 1.1254 | 2.01x | 3.11x → 3.10x |
0.0052/0.0034 |

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5565 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2875 | 2.12x | 0.5960 | 1.29x | 2.13x → 2.12x | 0.0052/0.0040
|
| 16384 | 0.4777 | 2.48x | 0.8506 | 1.62x | 2.49x → 2.48x |
0.0052/0.0040 |
| 2x8192 | 0.4373 | 2.06x | 0.7749 | 1.40x | 2.06x → 2.06x |
0.0052/0.0041 |
| 3000+13384 | 0.4863 | 2.24x | 0.8648 | 1.48x | 2.23x → 2.24x |
0.0052/0.0038 |
| 4x4096 | 0.2262 | 3.37x | 0.5578 | 1.70x | 3.37x → 3.37x |
0.0052/0.0040 |
| 2x(8128+64) | 0.4345 | 2.09x | 0.7687 | 1.42x | 2.09x → 2.09x |
0.0052/0.0040 |
| 8x(1024+64) | 0.0885 | 4.70x | 0.3676 | 1.66x | 4.72x → 4.70x |
0.0052/0.0040 |
| 32768 | 0.8536 | 2.71x | 1.3858 | 1.80x | 2.71x → 2.71x |
0.0052/0.0042 |

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5565 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0132 | 3.85x | 0.2439 | 1.21x | 3.85x → 3.85x |
0.0053/0.0040 |
| BS16 x T64 | 0.0309 | 2.39x | 0.2524 | 1.51x | 2.39x → 2.39x |
0.0041/0.0017 |
| BS64 x T64 | 0.0919 | 2.07x | 0.3580 | 1.86x | 2.10x → 2.07x |
0.0041/0.0017 |
| BS16 x T128 | 0.0399 | 2.65x | 0.2814 | 2.00x | 2.68x → 2.65x |
0.0053/0.0040 |
| BS16 x T256 | 0.0577 | 2.95x | 0.2822 | 1.88x | 2.98x → 2.95x |
0.0052/0.0040 |
| BS16 x T(17..255) | 0.0321 | 3.33x | 0.2645 | 1.90x | 3.36x → 3.33x |
0.0052/0.0041 |

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5565 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0134 | 3.90x | 0.2485 | 1.22x | 3.95x → 3.90x |
0.0053/0.0040 |
| BS16 x T64 | 0.0291 | 2.52x | 0.2831 | 1.36x | 2.53x → 2.52x |
0.0053/0.0040 |
| BS64 x T64 | 0.1038 | 2.21x | 0.3744 | 1.40x | 2.22x → 2.21x |
0.0052/0.0040 |
| BS16 x T128 | 0.0408 | 3.03x | 0.2751 | 1.76x | 3.01x → 3.03x |
0.0052/0.0040 |
| BS16 x T256 | 0.0593 | 3.51x | 0.2862 | 1.69x | 3.52x → 3.51x |
0.0052/0.0039 |
| BS16 x T(17..255) | 0.0419 | 2.95x | 0.2788 | 1.75x | 2.95x → 2.95x |
0.0052/0.0040 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5565
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2719 | 2.09x | 0.5254 | 1.37x | 1.75x → 2.09x | 0.0040/0.0020
|
| 16384 | 0.4671 | 2.28x | 0.6983 | 1.80x | 1.92x → 2.28x |
0.0040/0.0020 |
| 2x8192 | 0.4660 | 1.68x | 0.7077 | 1.36x | 1.39x → 1.68x |
0.0040/0.0019 |
| 3000+13384 | 0.4926 | 1.96x | 0.7255 | 1.57x | 1.61x → 1.96x |
0.0040/0.0024 |
| 4x4096 | 0.3691 | 1.75x | 0.5654 | 1.45x | 1.74x → 1.75x |
0.0040/0.0021 |
| 2x(8128+64) | 0.4762 | 1.64x | 0.7103 | 1.36x | 1.35x → 1.64x |
0.0040/0.0020 |
| 8x(1024+64) | 0.1324 | 2.59x | 0.3277 | 1.67x | 2.62x → 2.59x |
0.0040/0.0020 |
| 32768 | 0.8423 | 2.50x | 1.0756 | 2.11x | 2.07x → 2.50x |
0.0040/0.0022 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5565
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.3369 | 1.83x | 0.5838 | 1.32x | 1.52x → 1.83x | 0.0040/0.0021
|
| 16384 | 0.5834 | 2.06x | 0.8233 | 1.66x | 1.71x → 2.06x |
0.0040/0.0020 |
| 2x8192 | 0.6076 | 1.51x | 0.8477 | 1.29x | 1.22x → 1.51x |
0.0040/0.0021 |
| 3000+13384 | 0.5989 | 1.84x | 0.8382 | 1.52x | 1.53x → 1.84x |
0.0039/0.0022 |
| 4x4096 | 0.3844 | 2.02x | 0.5782 | 1.63x | 2.03x → 2.02x |
0.0040/0.0021 |
| 2x(8128+64) | 0.6389 | 1.44x | 0.8637 | 1.27x | 1.20x → 1.44x |
0.0040/0.0021 |
| 8x(1024+64) | 0.1328 | 3.20x | 0.3262 | 1.89x | 3.17x → 3.20x |
0.0040/0.0021 |
| 32768 | 1.0887 | 2.15x | 1.3129 | 1.91x | 1.82x → 2.15x |
0.0040/0.0023 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5565 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0208 | 2.44x | 0.2560 | 1.16x | 2.44x → 2.44x |
0.0039/0.0020 |
| BS16 x T64 | 0.0378 | 1.98x | 0.2363 | 1.55x | 1.96x → 1.98x |
0.0040/0.0020 |
| BS64 x T64 | 0.1109 | 1.74x | 0.3834 | 1.26x | 1.71x → 1.74x |
0.0039/0.0020 |
| BS16 x T128 | 0.0500 | 2.15x | 0.2780 | 2.33x | 2.11x → 2.15x |
0.0040/0.0021 |
| BS16 x T256 | 0.0760 | 2.33x | 0.2882 | 1.87x | 2.28x → 2.33x |
0.0039/0.0020 |
| BS16 x T(17..255) | 0.0415 | 2.64x | 0.2380 | 2.11x | 2.59x → 2.64x |
0.0040/0.0023 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5565 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5565 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0208 | 2.55x | 0.2610 | 1.15x | 2.52x → 2.55x |
0.0040/0.0021 |
| BS16 x T64 | 0.0385 | 1.97x | 0.2363 | 1.60x | 2.01x → 1.97x |
0.0040/0.0020 |
| BS64 x T64 | 0.1342 | 1.73x | 0.3358 | 1.54x | 1.77x → 1.73x |
0.0039/0.0021 |
| BS16 x T128 | 0.0512 | 2.44x | 0.2427 | 1.96x | 2.50x → 2.44x |
0.0040/0.0020 |
| BS16 x T256 | 0.0783 | 2.69x | 0.2668 | 1.79x | 2.76x → 2.69x |
0.0040/0.0021 |
| BS16 x T(17..255) | 0.0546 | 2.32x | 0.2387 | 2.01x | 2.38x → 2.32x |
0.0040/0.0022 |

GB300 (SM103, 152 SMs): 56/56 rows > 1 on both metrics; GPU time at or
below #5565 on 24/56 rows.

### Baselines and their source PRs

- **Triton reference**: SGLang's `chunk_kda` FLA path at the pinned
SGLang checkout 24c9251ac52ada1660f372922c72c1d3af722247 (same pin as
#5452 / #5543 / #5565), invoked as in `tests/kda` (sigmoid of logit beta
on the host, FP32 pool with state indices, intermediate states on).
- **Previous exported programs**: #5565 (f810de30c, 2026-09-26, the
"#5565" columns above); earlier #5543 (797872eac), #5452 (71f724405) and
#5440 (d3af75ac7). Files:
`csrc/kda/bf16/cake_kda_bf16_*_{kernel,binding}.cu`,
`flashinfer/jit/cake_kda_tf32.py`,
`flashinfer/cake_kda_tf32_runtime.py`, `flashinfer/kda_prefill.py`,
`tests/kda/`.
- Branch merge-base with `main`: b7d82df5a (the #5565 squash merge).
Since 797872eac the KDA prefill files (`csrc/kda/bf16`,
`flashinfer/jit/cake_kda_tf32.py`,
`flashinfer/cake_kda_tf32_runtime.py`, `flashinfer/kda_prefill.py`, the
three prefill test files) changed on `main` only through #5565; #5551
(37a53f374) touches only the fused-decode files and tests. The
regenerated programs and host files in this PR are byte-identical to the
tree validated on B200 and GB300 before the rebase.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [02ac572](https://github.com/flashinfer-ai/flashinfer/commit/02ac572bbd94423e4a4e511cd87b2e7b708d4f3a)

- **作者**: eigen
- **时间**: 2026-09-26T21:54:50Z
- **提交信息**: chore(cake_kernel): regenerate the epilogue-fused NVFP4 QKV GEMM export for MiniMax-H3 pre-attention (SM100a/SM103a) (#5566)

## Summary

Regenerated export of the epilogue-fused NVFP4 QKV GEMM for MiniMax-H3
pre-attention (`cake_minimax_h3_nvfp4_pre_attention`, SM100a / SM103a)
from the current producer tree.

This round of the optimise-to-ceiling work opened the three remaining
structural levers of the fused program (weight-tile multicast across two
CTA pairs, an epilogue instruction-stream diet, a CTA-specialised /
two-kernel epilogue) with paired cold-L2 CUPTI probes on B200 and B300
and closed all of them: the best bit-identical lever moves the kernel by
less than 1 % geomean on both parts, so **the kernels of record are
unchanged**. The generated CUDA of every production program in this PR
is byte-identical to the shipped #5563 programs; only the
producer-derived identity hashes change (file names, host-shim symbol
names, the `source_identity` / `closure_sha256` / per-file `sha256`
digests inside the route tables). The diff is therefore a pure rename of
the eight csrc files plus the two route tables (38 lines changed, no
kernel text change).

Opened as a draft so the package can either be merged to keep the
shipped identity hashes in step with the producer, or closed as a no-op;
there is no performance or numerics change to take.

## What changed

- `csrc/cake_minimax_h3_nvfp4_pre_attention/sm_100a/` and `sm_103a/`:
the four `_binding.cu` / `_kernel.cu` pairs renamed to the new identity
hashes (`4d04d24e…`, `8df3ceff…`, `37198195…`, `77d2620e…`); after
normalising the hash tokens every renamed file is line-identical to its
predecessor.
- `flashinfer/jit/cake_minimax_h3_nvfp4_pre_attention_sm100a.py` /
`_sm103a.py`: route tables regenerated; after normalising the hash
tokens the only differences are the identity and digest fields.
- No Python API, test, or documentation change.

## Validation

- Both export legs (B200 and B300) regenerated from the same producer
tree and delivered byte-identical `delivery.patch` files (sha256
`d10835f7bfb03634…`, 450106 bytes); the patch content equals the #5563
delivery after normalising the identity hashes.
- 44/44 contract rows byte-exact against the segmented reference chain
on B200 and B300 (packed NVFP4 outputs and E4M3 scales), on the same
producer tree.
- Paired 24-row production table of the exported program vs the #5563
program (same binary, same node, cold-L2 CUPTI): B200 1.0016x / B300
0.9996x geomean, 24/24 rows byte-equal on both parts, as expected for an
identical kernel.
- compute-sanitizer synccheck + memcheck clean on both architectures.
- `tests/test_minimax_h3_nvfp4.py`: 19 passed on B200 and 19 passed on
B300 against the delivered package; pre-commit clean on both legs and on
this branch.
- Paired source-vs-export timing (same program in both arms,
sampled-clock qualification): B200 42/44 selected shapes sealed at
0.999x-1.001x after one bounded retry (`center_p4_6s_m12192`,
`center_p4_15s_m27488` failed only the 70 % SM-clock floor of the
measurement window and are disclosed, not rescored); B300 43/44 sealed
(`center_p2_15s_m54976` disclosed for the same reason).

## Baselines and their source PRs

- Segmented reference chain: `cake_minimax_h3_nvfp4_pre_attention`
staged programs as shipped in #5496 / #5529 (main `a3701b2ee`,
2026-09-26); no later change to
`csrc/cake_minimax_h3_nvfp4_pre_attention/` or
`flashinfer/jit/cake_minimax_h3_nvfp4_pre_attention_sm10{0,3}a.py`
between #5563 and this PR's merge-base (`78c6e1fbf`).
- Previously shipped fused programs (the programs this PR renames):
#5563 (main `d1821bbac`, branch head `1ada9df51`, 2026-09-26), itself on
top of #5529 (`a3701b2ee`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Maintenance**
* Updated MiniMax-H3 NVFP4 pre-attention kernel references for supported
GPU architectures and partition counts. Kernel behavior and launch
settings are unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d67061a](https://github.com/flashinfer-ai/flashinfer/commit/d67061a80dbcb81bd421cef681b93169bb619587)

- **作者**: eigen
- **时间**: 2026-09-26T21:53:17Z
- **提交信息**: perf(cake_backend): split cooperative joins and a warp-level round-0 shortcut for the mid and large Kimi-K3 fused router batches (SM100/SM103) (#5568)

## Kimi-K3 fused MoE router: split cooperative joins and a warp-level
round-0 shortcut for the mid and large batches (SM100 / SM103)

Follow-up to #5531 / #5548 / #5564 (same source family; regenerated
programs only, no host change). Same K3 semantics (sigmoid gate, top-16
on `sigmoid(logit) + bias`, renormalized unbiased weights, lower expert
id on ties) and the same expert-aligned route plan for `block_m` 8/16;
the public entries `flashinfer.fused_moe.kimi_k3_fused_router` /
`prepare_kimi_k3_fused_router`, the route table and the arm set are
unchanged. The exporter regenerates all 14 programs per arch; for the 8
small-batch programs (`L`, `LC2`, `LC4`, `LC8` x `block_m` 8/16) the
kernel and binding sources are identical to #5564 up to the module
identifier (the module name is a content fingerprint that also covers
exporter-side build metadata), so only the 6 mid/large programs per arch
carry code changes.

### What changed
The 12 routed shapes with `num_tokens` 256 … 8192 (`block_m` 8/16) get
new kernel code (arms `M`, `Q4S`, `GW`); the 16 small-batch shapes keep
their kernel code.

- **Split cooperative join in the mid-batch arms (`M`, `Q4S`;
`num_tokens` 256 … 2048).** The single grid-wide join between expert
selection and route-plan build becomes an arrive / wait pair
(`cooperative_groups::grid_group::barrier_arrive` / `barrier_wait`):
every CTA arrives right after its last selection row, only the CTAs that
own plan-build work wait, the others retire instead of spinning in
`this_grid().sync()`.
- **Split first join in the large-batch arm (`GW`; `num_tokens` 4096 /
8192).** The join that publishes the zeroed expert counts is split into
an arrive after the grid-strided clear and one wait between a CTA's
first-row selection and its first ticket atomic, so the slowest CTA's
clear overlaps one row of selection. Every CTA arrives and waits exactly
once per round (a CTA without rows waits once after its empty loop).
- **Fence-free barrier sites in `GW`.** The three per-thread
device-scope fences in front of the GW grid barriers are dropped:
`__syncthreads()` followed by the barrier's own device-scope release
already orders the preceding stores (the same reasoning as #5548,
previously applied only to the mid-batch arms).
- **Round-0 max-bin shortcut in the `GW` radix selection.** The top byte
of the ordered key is sign + 7 exponent bits, so a row's 896 keys
concentrate in one or two round-0 histogram bins and the 28 conditional
shared-memory atomics per lane serialized on one address. Round 0 now
takes the maximum top byte and its population from two warp reductions
(`redux.sync`); when that bin holds at least 16 keys it is exactly the
bin the histogram round selects (nothing lies above it) and the state
update is identical, otherwise the unchanged histogram round runs.
Rounds 1-3 are unchanged, so the selected experts and their order are
bit-identical.

Source-side paired cold-L2 CUPTI A/B against the #5564 programs (same
session, same node, two runs per arch on different GPUs; `previous /
new` kernel time):

| row | B200 run 1 / run 2 | GB300 run 1 / run 2 |
|---|---|---|
| m256 bm8 / bm16 | 1.027 / 1.028, 1.027 / 1.036 | 1.016 / 1.021, 1.012
/ 1.034 |
| m512 bm8 / bm16 | 1.057 / 1.057, 1.075 / 1.051 | 1.075 / 1.079, 1.071
/ 1.074 |
| m1024 bm8 / bm16 | 1.067 / 1.062, 1.041 / 1.058 | 1.050 / 1.058, 1.047
/ 1.057 |
| m2048 bm8 / bm16 | 1.028 / 1.023, 1.011 / 1.026 | 1.035 / 1.056, 1.039
/ 1.058 |
| m4096 bm8 / bm16 | 1.093 / 1.091, 1.092 / 1.082 | 1.088 / 1.092, 1.087
/ 1.094 |
| m8192 bm8 / bm16 | 1.093 / 1.092, 1.094 / 1.090 | 1.083 / 1.077, 1.083
/ 1.079 |
| geomean (12 rows) | 1.060, 1.057 | 1.060, 1.061 |

Every changed row is faster than #5564 in every run on both
architectures.

### Exactness
Source-side gates on both arches: exact43 43/43, affected slice +
registered e2e, compute-sanitizer synccheck and racecheck (separate
runs, 8 frozen shapes + all 28 routed rows): `ERROR SUMMARY: 0 errors` /
`RACECHECK SUMMARY: 0 hazards` on every run. Export receipts (source <->
export bitwise parity on all 28 shapes per arch, generated grid ==
source grid): B200 (sm_100a) 28/28 rows correct, GB300 (sm_103a) 28/28
rows correct; the delivered patch produced from the two architectures is
byte-identical (SHA-256
`eb051e8e130f00c2dffa69f1095fdcc6fdb70a97c55f9d5425e49cda65fe4c22`).
`tests/experimental/test_cake_kimi_k3_fused_router.py`: 44 passed on
both arches. Pre-commit (ruff, mypy, clang-format opt-out for the
generated `csrc/`) clean.

### Benchmark
`benchmarks/bench_cake_kimi_k3_fused_router.py --cupti --rounds 5`
(interleaved A/B rounds, CUPTI kernel time with a cold L2) against
SGLang `route_radix` + `moe_align_block_size` (pinned SGLang revision
83bd2c47, kernel-only):

| row | arm (B200 / GB300) | B200 fused us | B200 SGLang us | B200
speedup | GB300 fused us | GB300 SGLang us | GB300 speedup |
|---|---|---:|---:|---:|---:|---:|---:|
| m1_bm8 | L / L | 5.79 | 9.31 | **1.608** | 5.54 | 12.64 | **2.283** |
| m2_bm8 | LC / LC | 5.28 | 9.63 | **1.825** | 5.22 | 12.64 | **2.423**
|
| m4_bm8 | LC / LC | 5.92 | 9.50 | **1.606** | 5.60 | 12.58 | **2.246**
|
| m8_bm8 | LC / LC | 5.95 | 9.73 | **1.635** | 5.76 | 12.45 | **2.161**
|
| m16_bm8 | L / L | 6.14 | 9.57 | **1.557** | 6.08 | 12.83 | **2.111** |
| m32_bm8 | L / L | 6.27 | 9.79 | **1.561** | 6.21 | 12.93 | **2.082** |
| m64_bm8 | L / L | 7.01 | 10.02 | **1.429** | 6.66 | 12.99 | **1.952**
|
| m128_bm8 | L / L | 8.06 | 10.40 | **1.290** | 7.68 | 13.18 | **1.717**
|
| m256_bm8 | M / M | 8.16 | 10.94 | **1.341** | 7.97 | 14.14 | **1.775**
|
| m512_bm8 | Q4S / Q4S | 9.89 | 12.96 | **1.311** | 9.47 | 15.33 |
**1.618** |
| m1024_bm8 | Q4S / Q4S | 13.70 | 18.34 | **1.339** | 12.80 | 18.53 |
**1.447** |
| m2048_bm8 | Q4S / Q4S | 20.74 | 28.19 | **1.360** | 19.20 | 26.78 |
**1.395** |
| m4096_bm8 | GW / GW | 28.35 | 47.52 | **1.676** | 26.75 | 45.25 |
**1.691** |
| m8192_bm8 | GW / GW | 43.33 | 87.20 | **2.013** | 40.90 | 82.08 |
**2.007** |
| m1_bm16 | L / L | 6.46 | 9.85 | **1.525** | 6.05 | 12.51 | **2.069** |
| m2_bm16 | LC / LC | 5.79 | 9.50 | **1.641** | 5.54 | 12.70 | **2.295**
|
| m4_bm16 | LC / LC | 5.60 | 9.89 | **1.766** | 5.50 | 12.74 | **2.314**
|
| m8_bm16 | LC / LC | 5.70 | 9.79 | **1.719** | 5.79 | 13.12 | **2.265**
|
| m16_bm16 | L / L | 5.86 | 9.98 | **1.705** | 6.05 | 12.93 | **2.138**
|
| m32_bm16 | L / L | 6.43 | 9.95 | **1.547** | 6.11 | 13.18 | **2.157**
|
| m64_bm16 | L / L | 7.14 | 10.05 | **1.408** | 6.91 | 13.09 | **1.894**
|
| m128_bm16 | L / L | 8.26 | 10.40 | **1.260** | 7.81 | 13.60 |
**1.742** |
| m256_bm16 | M / M | 8.22 | 11.33 | **1.377** | 7.97 | 13.89 |
**1.743** |
| m512_bm16 | Q4S / Q4S | 9.95 | 12.54 | **1.260** | 9.34 | 15.46 |
**1.654** |
| m1024_bm16 | Q4S / Q4S | 13.38 | 17.76 | **1.328** | 12.80 | 18.53 |
**1.447** |
| m2048_bm16 | Q4S / Q4S | 20.70 | 26.66 | **1.287** | 19.14 | 25.82 |
**1.349** |
| m4096_bm16 | GW / GW | 28.74 | 44.89 | **1.562** | 27.46 | 43.20 |
**1.573** |
| m8192_bm16 | GW / GW | 43.45 | 81.60 | **1.878** | 41.63 | 77.79 |
**1.869** |

Geomean speedup vs SGLang: **NVIDIA B200 1.516** (min `1.260`, `28`/28
rows > 1.0), **NVIDIA GB300 1.882** (min `1.349`, `28`/28 rows > 1.0).
#5564 on the same benchmark: B200 1.492 (min 1.220), GB300 1.873 (min
1.319).

### Baselines and their source PRs
- **Previous programs (A/B "previous" arm and the geomean reference):**
#5564 (merge 78c6e1fbf, 2026-09-26), on top of #5548 (c89471142,
2026-09-25) and #5531 (afad7014a, 2026-09-25). Files:
`flashinfer/experimental/kimi_k3_fused_router/{cake_backend.py,
cake_jit.py, csrc/cake_kimi_k3_fused_router/sm_10{0,3}a/*}`,
`flashinfer/fused_moe/kimi_k3_fused_router.py`,
`benchmarks/bench_cake_kimi_k3_fused_router.py`,
`tests/experimental/test_cake_kimi_k3_fused_router.py`. This branch's
merge-base with `main` is 78c6e1fbf (= #5564's merge commit); `git log
78c6e1fbf..origin/main -- <those files>` is empty, so no upstream commit
after the merge-base touched them.
- **SGLang reference (benchmark denominator and the test oracle's
semantics):** `sglang.kernels.ops.moe.moe_route_radix.route_radix` +
`sglang.kernels.ops.moe.moe_align.moe_align_block_size` at the pinned
SGLang revision 83bd2c473f173404216f6d9851ad7a95c1e3c565, imported
kernel-only (no SGLang runtime); `moe_route_radix.py` last changed by
sgl-project/sglang#32890 (fb207b72b, 2026-08-01, "port standalone Kimi
K3 kernels") and `moe_align.py` by sgl-project/sglang#32045 (74338e94f,
2026-07-22), both before the pinned revision; the pin is unchanged since
#5531.
- **Test oracle:** the PyTorch reference in
`tests/experimental/test_cake_kimi_k3_fused_router.py` from #5531
(unchanged since).

### Notes
- No change to `cake_backend.py`; `cake_jit.py` only changes the 14
module records per arch (module names follow the generated program
fingerprint). Same-session controls on the 16 unchanged small rows:
geomean 0.994 (B200) / 1.006 (GB300) with both arms loading the same
module, so the small rows are unchanged within noise.
- Shapes outside the routed set still raise `NotImplementedError`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved fused routing efficiency across supported GPU architectures
and workloads, including faster top-k selection and more targeted
synchronization.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [68cd7f2](https://github.com/flashinfer-ai/flashinfer/commit/68cd7f2245a2ebbbf2bef7bc52fedad99f220e3e)

- **作者**: eigen
- **时间**: 2026-09-26T21:50:23Z
- **提交信息**: feat(cake_fused_norm_combine): add SM103 (B300) eight-peer fused norm-combine beside SM100 and a pipelined persistent owner reduce for 1024+ tokens (#5540)

## Summary

Follow-up to #5528 (SM100 only): the Cake eight-peer fused residual-add
+ two-track RMSNorm + BF16 combine now also ships for **SM103 (B300)**.

* `csrc/cake_fused_norm_combine/sm_103a/*.cu` — generated device +
binding translation units for the two dispatch variants
(`parallel_lamport` below 256 tokens, `owner_lamport` at and above), the
same schedules as SM100 built for `sm_103a`.
* `flashinfer/jit/cake_fused_norm_combine.py` — `MODULES` records carry
`arch`; `ROUTES` is keyed by architecture then variant;
`ARCH_BY_CAPABILITY` / `arch_for_capability` resolve the module from the
device capability (10.0 → `sm_100a`, 10.3 → `sm_103a`); each module
compiles with exactly its own `-gencode` (`sm100a_nvcc_flags` /
`sm103a_nvcc_flags`).
* `flashinfer/comm/cake_fused_norm_combine.py` — API unchanged; the
route scope now accepts uniform eight-GPU SM100 or SM103 nodes.
* `tests/comm/test_cake_fused_norm_combine.py` — inventory / dispatch /
scope tests cover both architectures; the eight-GPU distributed test
runs on a uniform SM100 or SM103 node.

No behaviour change on SM100: the `sm_100a` translation units are
byte-identical to #5528 (the module SHA-256 pins in the loader are
unchanged).

### Third dispatch band: pipelined persistent owner reduce for T >= 1024
(SM100 + SM103)

The one-CTA-per-token owner reduce runs 3-7 waves deep at 1024-2048
tokens and every wave serialises both cross-GPU latency rounds. The new
`owner_lamport_pipelined` module keeps the same arithmetic, workspace
layout, three-slot Lamport rotation and PDL, but each CTA of a
co-resident odd grid walks tokens `b, b+G, ...`: per step it publishes
token `k` while reducing and broadcasting its owned token of step `k-2`,
so the two latency rounds overlap with the publish stream. Outputs are
bitwise identical to the existing kernels.

* `csrc/cake_fused_norm_combine/{sm_100a,sm_103a}/*.cu` — one new
generated device + binding pair per architecture (the binding bakes the
cooperative-grid launch attribute); the existing units are unchanged.
* `flashinfer/jit/cake_fused_norm_combine.py` — `ROUTES[arch]` gains
`owner_lamport_pipelined`; `WIDE_MIN_TOKENS = 1024`; each module record
carries a `grid_rule` (`per_token`, or `co_resident_odd` with the
measured `ctas_per_sm` / `sm_count`); `persistent_grid` launches
`tokens` CTAs when they fit, else the largest odd grid not above the
co-resident capacity; on a device whose SM count differs from the
verified receipt the loader falls back to the one-CTA-per-token
`owner_lamport` module; `WIDE_COOPERATIVE` records the launch attribute.
* `flashinfer/comm/cake_fused_norm_combine.py` — API unchanged;
re-exports `WIDE_MIN_TOKENS`.
* `tests/comm/test_cake_fused_norm_combine.py` — three-band inventory /
dispatch tests, the `persistent_grid` formula and the grid-rule
fallback; the eight-GPU distributed test exercises all three bands (T1
... T2048).

Measured co-resident capacity of the pipelined kernel: 4 CTAs/SM on 148
SMs (592 CTAs) on both B200 and B300; T1024 and T2048 launch 591 CTAs
(odd, so the token-to-owner assignment rotates across CTAs).

Paired receipts of the new wide route against the previous
`owner_lamport` route on the same GPUs (10000 warmup / 100000 CUPTI
samples per rank, max-rank medians): **8x B200** T1024 35.49 -> 31.87 us
(1.113x), T2048 57.60 -> 49.50 us (1.164x); **8x B300** T1024 34.43 ->
30.98 us (1.112x), T2048 56.00 -> 49.15 us (1.139x). Rows below 1024
keep their previous modules.

## Validation (8x B300 SXM6, driver 615.71.09, torch 2.13 / CUDA 13.3)

Every row is run with all eight ranks live (world size 8, hidden 2560,
two RMSNorm tracks, epsilon 1e-6). Correctness compares the exported
program bitwise against the generating Cake source kernel and against a
PyTorch reference of the fused op on every rank; timing is CUPTI kernel
time per rank with a cold L2 before every sample, counterbalanced
source/export arms, 200 ms of samples per arm and group, three groups.

| tokens | variant | source us | export us | source / export | customer
fused kernel us | customer / export |
|---:|---|---:|---:|---:|---:|---:|
| 1 | parallel_lamport | 18.37 | 18.24 | 1.007x | 19.33 | 1.060x |
| 8 | parallel_lamport | 19.14 | 18.94 | 1.010x | 20.93 | 1.105x |
| 64 | parallel_lamport | 19.46 | 19.39 | 1.003x | 22.14 | 1.142x |
| 256 | owner_lamport | 22.27 | 22.08 | 1.009x | 33.98 | 1.539x |
| 1024 | owner_lamport | 36.93 | 36.80 | 1.003x | n/a | — |
| 2048 | owner_lamport | 58.21 | 57.66 | 1.009x | n/a | — |

All six rows pass correctness and every timing gate (source/export
agreement, directional agreement between counterbalanced groups,
endpoint drift). The customer's own fused one-shot kernel (the workload
this replaces) only resolves up to 256 tokens; the geometric mean over
those four rows is 1.198x in favour of the exported program.

`pytest tests/comm/test_cake_fused_norm_combine.py` on the same node: 17
passed (CPU inventory / dispatch / scope tests plus the eight-GPU
distributed test).

## Validation (8x B200, driver 615.71.09, torch 2.13 / CUDA 13.3)

Same protocol on eight B200 GPUs. The `sm_100a` units and loader pins
are unchanged from #5528; this run regresses the two-architecture loader
and tests on SM100.

| tokens | variant | source us | export us | source / export | customer
fused kernel us | customer / export |
|---:|---|---:|---:|---:|---:|---:|
| 1 | parallel_lamport | 18.59 | 18.30 | 1.016x | 19.97 | 1.091x |
| 8 | parallel_lamport | 18.94 | 18.66 | 1.015x | 20.77 | 1.113x |
| 64 | parallel_lamport | 18.91 | 18.72 | 1.010x | 21.54 | 1.151x |
| 256 | owner_lamport | 21.98 | 21.82 | 1.007x | 33.54 | 1.537x |
| 1024 | owner_lamport | 38.24 | 37.86 | 1.010x | n/a | — |
| 2048 | owner_lamport | 58.46 | 58.35 | 1.002x | n/a | — |

All six rows pass correctness and every timing gate; customer geometric
mean 1.210x over the four resolvable rows. `pytest
tests/comm/test_cake_fused_norm_combine.py`: 17 passed. The B200 export
regenerated this PR's files independently and produced byte-identical
`sm_103a` units and Python modules.

## Validation of the third band (export run at the three-band loader)

### 8x B300 SXM6 (driver 615.71.09, torch 2.13 / CUDA 13.3)

Same protocol as above (world size 8, hidden 2560, two tracks, epsilon
1e-6; bitwise correctness of the exported program against the generating
Cake source kernel and a PyTorch reference on every rank; CUPTI kernel
time per rank with a cold L2 before every sample, counterbalanced
source/export arms, 200 ms of samples per arm and group, three groups).
The 1024- and 2048-token rows now resolve to the new
`owner_lamport_pipelined` module (591-CTA cooperative grid).

| tokens | route | source us | export us | source / export | customer
fused kernel us | customer / export |
|---:|---|---:|---:|---:|---:|---:|
| 1 | parallel_lamport | 17.25 | 17.28 | 0.998x | 18.62 | 1.078x |
| 8 | parallel_lamport | 17.57 | 17.47 | 1.005x | 19.42 | 1.112x |
| 64 | parallel_lamport | 20.10 | 19.90 | 1.010x | 22.46 | 1.129x |
| 256 | owner_lamport | 23.04 | 22.82 | 1.010x | 34.98 | 1.533x |
| 1024 | owner_lamport_pipelined | 34.72 | 34.69 | 1.001x | n/a | — |
| 2048 | owner_lamport_pipelined | 51.87 | 51.94 | 0.999x | n/a | — |

All six rows pass correctness and every timing gate; source/export
geometric mean 1.004x; customer geometric mean 1.200x over the four rows
the customer kernel resolves. `pytest
tests/comm/test_cake_fused_norm_combine.py` on the same node: 25 passed
(three-band inventory / dispatch / grid-rule tests plus the eight-GPU
distributed test).

### 8x B200 (driver 615.71.09, torch 2.13 / CUDA 13.3)

Same protocol on eight B200 GPUs; the B200 export regenerated the
delivery independently and produced byte-identical generated units and
Python modules to the B300 run.

| tokens | route | source us | export us | source / export | customer
fused kernel us | customer / export |
|---:|---|---:|---:|---:|---:|---:|
| 1 | parallel_lamport | 17.38 | 17.28 | 1.005x | 18.66 | 1.080x |
| 8 | parallel_lamport | 17.54 | 17.47 | 1.004x | 19.81 | 1.134x |
| 64 | parallel_lamport | 19.23 | 18.91 | 1.017x | 21.82 | 1.154x |
| 256 | owner_lamport | 21.86 | 21.41 | 1.021x | 33.38 | 1.559x |
| 1024 | owner_lamport_pipelined | 33.95 | 33.95 | 1.000x | n/a | — |
| 2048 | owner_lamport_pipelined | 50.53 | 50.72 | 0.996x | n/a | — |

All six rows pass correctness and every timing gate; source/export
geometric mean 1.007x; customer geometric mean 1.218x over the four rows
the customer kernel resolves. `pytest
tests/comm/test_cake_fused_norm_combine.py` on the same node: 25 passed.

The published Python modules are the exported modules after the upstream
`ruff-format` hook (two line wraps); their ASTs are identical to the
measured modules. The generated CUDA units are byte-identical to the
measured ones.

## Test plan

- [x] `pytest tests/comm/test_cake_fused_norm_combine.py` on 8x B300
(CPU tests + distributed test) — 17 passed
- [x] export gates on 8x B300: 6/6 rows correct, source/export within
1.0-1.1 %
- [x] `pytest tests/comm/test_cake_fused_norm_combine.py` on 8x B200
(CPU tests + distributed test) — 17 passed
- [x] export gates on 8x B200: 6/6 rows correct, source/export within
0.2-1.6 %
- [x] three-band export gates on 8x B300: 6/6 rows correct,
source/export within 0.2-1.0 %; `pytest
tests/comm/test_cake_fused_norm_combine.py` 25 passed
- [x] three-band export gates on 8x B200: 6/6 rows correct,
source/export within 0.4-2.1 %; `pytest
tests/comm/test_cake_fused_norm_combine.py` 25 passed
- [x] `pre-commit run --files` on the three Python modules (upstream
hook versions)

🤖 Generated with [Claude Code](https://claude.com/claude-code)



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for fused bfloat16 normalization and combine operations
on SM103 GPUs, alongside existing SM100 support.
* Added a pipelined processing option for workloads with 1,024 or more
tokens on supported architectures. Other workload sizes continue to use
existing processing routes.
* Added architecture and launch configuration information to the public
JIT interface.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e7f65f7](https://github.com/flashinfer-ai/flashinfer/commit/e7f65f783eb409c7ec3b3f9bfa3d552281f8f8a5)

- **作者**: eigen
- **时间**: 2026-09-26T21:47:08Z
- **提交信息**: feat(cake_backend): Kimi-K3 FP8_PB_WO KDA/MLA projection GEMMs (SM100/SM103) (#5572)

## Summary

Experimental generated-program backend for the serialized `FP8_PB_WO`
KDA / MLA projection GEMMs of `nvidia/Kimi-K3-NVFP4` on `sm_100a` (B200)
and `sm_103a` (B300/GB300),
`flashinfer/experimental/kimi_k3_fp8_projection` (#4568, tracker #4254).

BF16 activations `x[M, K]` are quantized per token in 1x128 blocks to
E4M3 with power-of-two (UE8M0) scales (DeepGEMM
`per_token_cast_to_fp8(use_ue8m0=True)`, bit-exact) and multiplied with
the serialized weight (E4M3 `[N_pad128, K]` + ModelOpt 128x128 FP32
`weight_scale`, requantized once to UE8M0 scales with vLLM
`requant_weight_ue8m0` semantics) through block-scaled tcgen05 MMA into
BF16 `out[M, n_valid]` with an arbitrary even row stride (fused
projections are split by views, no pad / slice kernels).

- `flashinfer/gemm/kimi_k3_fp8_projection.py`: thin experimental entry
points `prepare_kimi_k3_fp8_projection_weights`,
`allocate_kimi_k3_fp8_projection_workspace`,
`prepare_kimi_k3_fp8_projection` (allocation-free, CUDA-graph capturable
runner) and `kimi_k3_fp8_projection`.
- `flashinfer/experimental/kimi_k3_fp8_projection/cake_backend.py`:
weight preparation (UE8M0 requantization, 256-row padding, 128x128 tile
order the TMA streams, swizzled scale tiles), workspaces, the measured
per-architecture dispatch table (`decode_table.py`: `(N, K)` family x
`M` bucket -> quantization launch + persistent 2-CTA GEMM / quantization
launch + swap-AB split-K decode / fused decode incl. resident token
tiles) and the binding to the generated argument plans.
- `cake_jit.py`: `MODULES` / `KERNELS` registries populated by the
export protocol (11 exact-architecture programs per arch:
`quant:u1/u2/u4`, `gemm`, 7 decode instances). Both literals are
generated; do not edit by hand.
-
`csrc/cake_kimi_k3_fp8_projection/{sm_100a,sm_103a}/*_{kernel,binding}.cu`:
44 generated sources (formatting disabled by the directory
`.clang-format`; identities are receipt-bound).
- `tests/experimental/test_cake_kimi_k3_fp8_projection.py`,
`benchmarks/bench_cake_kimi_k3_fp8_projection.py`.

The first commit is the backend scaffold (host code, entry points,
tests, benchmark); the second adds the generated programs only.

## Evidence (export protocol, producer `e27cc1b1eb4`, target
`9390fbac3701`)

Every contract row (22 families x `M in {1, 8, 64, 256, 4096, 16384}` =
132 perf rows, plus 88 correctness-only rows with `M in {3, 129, 1000,
4097}` and padded output strides) is measured on the source launcher and
the exported programs in 3 counterbalanced CUDA-graph groups (fixed
sample counts: 200 warmup / 2000 reportable calls per arm and group for
the microsecond rows, ~2.5 s of warmup for the rows above 100 us; one
unmeasured same-arm launch and a fresh cold-L2 flush precede every
reportable sample; SM clock floor 0.55 of the rated maximum for the
power-capped millisecond GEMM rows). Gates: `source_ms / export_ms >=
0.94`, directional disagreement `<= 0.08`, endpoint drift `<= 0.02`;
correctness = bitwise `source == export` plus the contract's zero-budget
rule `|out - ref| <= 1e-2 + 1e-2 |ref| + 2 bf16 ulp` against the exact
quantized-operand emulation, the DeepGEMM `calc_diff < 1e-3` gate
against the BF16 dequantized-weight chain, and untouched output padding;
no device allocation in the export submit.

| arch | GPU | rows measured | correct (bitwise source == export) |
sealed (all timing gates) | source / export (min .. max, geomean) |
|---|---|---|---|---|---|
| sm_100a | B200 | 220 | 220 | 216 | 0.942 .. 1.079, 0.9965 |
| sm_103a | B300 | 220 | 220 | 217 | 0.932 .. 1.051, 0.9942 |

Two complete independent rounds per architecture (the first round is
closed as a read-only prior snapshot); the round-2 medians reproduce
round 1 to within one 32 ns CUPTI quantum on nearly every row, and the
seven rows below fail the same measurement-qualification gates in both
rounds, so they are disclosed rather than retried further. All seven are
bitwise-correct.

| GPU | row | source us | export us | source / export | gate |
|---|---|---|---|---|---|
| B200 | `tp8 kv_a M=64` | 12.54 | 12.32 | 1.018x | directional
disagreement > 0.08 |
| B200 | `tp1 f_b M=64` | 6.08 | 5.66 | 1.073x | directional
disagreement > 0.08 |
| B200 | `tp1 kv_a M=64` | 11.65 | 12.13 | 0.960x | directional
disagreement > 0.08 |
| B200 | `tp1 o_proj M=4096` | 300.7 | 301.1 | 0.999x | endpoint drift >
0.02 |
| B300 | `tp1 b_proj M=1` | 7.58 | 8.10 | 0.937x | speed floor 0.94 |
| B300 | `tp1 kv_a M=64` | 11.65 | 11.84 | 0.984x | directional
disagreement > 0.08 |
| B300 | `tp8 f_b M=3` (correctness row) | 3.97 | 4.26 | 0.932x | speed
floor 0.94 |

The two B300 rows below the 0.94 floor are the smallest kernels of the
set (4 to 8 us, one or two waves); the exported programs are the same
generated sources compiled by nvcc instead of the source's NVRTC path,
and the 0.3 to 0.5 us deficit reproduces exactly across rounds. `tp1
b_proj M=1` on B300 remains 1.5x faster than the fastest existing chain
(DeepGEMM pack + GEMM, 12.7 us). The `kv_a` / `f_b` `M=64` rows read a
reproducible order effect inside the paired blocks with the ratio itself
near 1.

Speed vs the fastest existing FP8 chain per row
(`per_token_group_quant_8bit` + `gemm_fp8_nt_groupwise` with the
`cutlass` sm1 / sm2, `trtllm` and `cutile` backends, and DeepGEMM
`fp8_gemm_nt` with UE8M0 packing; CUDA-graph replay, cold L2, same
weights), 132 perf rows per GPU: B200 131/132 rows faster, geomean
1.639x (min 0.976x on `tp1 kv_b M=256`, K = 512); B300 132/132 rows
faster, geomean 1.626x (min 1.014x).

`tests/experimental/test_cake_kimi_k3_fp8_projection.py`: 30 passed on
B200 and on B300 against this tree. Delivery is byte-identical from all
four runs (delivery.patch SHA-256
`49ac7e7e9f6c5943777decf6d74b4f457f12939455247149f7ceedb5d5e5f21d`).
Receipts, raw timings and state copies stay on the clusters (host / path
/ size / SHA-256 recorded in the source repository's design record).

## Baselines and their source PRs

The comparison arms are upstream FlashInfer entry points at
`e34a1735aecae0819be9c7a44f2e7c8e0d023aff` (2026-09-25; this branch's
upstream merge-base is `78c6e1fbfcb65043cdee92506c077259e7e878b7`,
2026-09-26). No upstream commit between the survey revision and the
merge-base, nor after the merge-base, touched the files below (`git log
e34a1735a..78c6e1fbf -- <files>` and `git log 78c6e1fbf..origin/main --
<files>` are empty).

- `per_token_group_quant_8bit`
(`flashinfer/quantization/fp8_quantization.py`, cuTile kernel
`flashinfer/quantization/kernels/cutile/per_token_group_quant_8bit_cutile.py`):
#4019 (`c517c07bd`, 2026-08-13).
- `gemm_fp8_nt_groupwise` `backend="cutlass"` (`mma_sm` 1 and 2;
`csrc/gemm_groupwise_sm100.cu`,
`csrc/gemm_groupwise_sm100_kernel_inst.jinja`,
`flashinfer/gemm/gemm_base.py`): #1045 (`71002782f`, 2025-05-04); last
kernel change #2327 (`2bf87713d`, 2026-01-13).
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
- BF16 cuBLAS (`torch.matmul` on the dequantized weight) is reported as
an informational reference only.

Test oracle: the exact quantized-operand emulation in
`tests/experimental/test_cake_kimi_k3_fp8_projection.py` (this PR).

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
* Added experimental Kimi-K3 FP8 projection support for SM100 and SM103,
including weight preparation, reusable runners, and optional workspace
and output allocation.
* Added route selection for decode and GEMM workloads, with support for
fused activation quantization on applicable routes.
* **Documentation**
* Documented supported hardware, usage, input requirements, and
benchmarking.
* **Tests**
* Added coverage for projection correctness, dispatch, graph replay,
allocation behavior, and input validation.
* **Benchmarks**
* Added comparisons against available quantization and GEMM
alternatives, including timing and speedup reporting.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b6e4ebf](https://github.com/flashinfer-ai/flashinfer/commit/b6e4ebfdd36f683b751e13e627f55d76ca2601d4)

- **作者**: eigen
- **时间**: 2026-09-26T21:36:37Z
- **提交信息**: perf(cake_vision_backend): Kimi-K3 vision tower Cake backend round 2 (SM100a/SM103a): packed epilogues, f16x2 RoPE table, PDL (#5570)

## Summary

Round 2 of the generated-program export of the Cake Kimi-K3 vision tower
(MoonViT-3D encoder, 27 layers, + PatchMergerV2) for `sm_100a` (B200)
and `sm_103a` (B300/GB300) into
`flashinfer/experimental/kimi_k3_vision_tower` (#4568, tracker #4254;
round 1 = #5554).

- The first commit (`fd757bf11`) mirrors the round-2 Cake host policy in
the scaffold: `TileConfig` carries the tail / packed / prefetch /
RoPE-table fields and the full Cake tile catalogue (packed
residual-epilogue twins `*_p` / `*_pf`, packed f16x2 RoPE-table twins
`*_cs`, opt-in tail twins `*_t` the policy never selects);
`select_tile_config` reproduces the production selection for every
variant and token count; the GEMM launches bind the kernels' new
parameters (`CS`, `WS`, `FLAGS`, `full_tiles`, `tail_split`); the plan
derives the packed `[T, 64]` u32 f16x2 (cos, sin) table next to the FP32
tables. The exported bindings own the programmatic-stream-serialization
launch attribute (Cake PDL default is on for every stage of the tower).
- The second commit is the generated delivery only: `cake_jit.py`
`MODULES` / `KERNELS` registries (54 exact-architecture programs: 27 per
arch = 23 tile-config GEMM programs + 2 attention layouts +
final-norm/merge + rmsnorm-apply) and
`csrc/cake_kimi_k3_vision_tower/{sm_100a,sm_103a}/*_{kernel,binding}.cu`
(108 generated sources, replacing the round-1 set; excluded from the
formatting hooks via `csrc/.clang-format`; identities are
receipt-bound). Both literals are generated; do not edit by hand.

Kernel changes behind the regenerated programs (Cake CAKE-663): packed
bf16x2 residual epilogues (no register spills), residual-row /
norm-weight prefetch before the mainloop wait, packed f16x2 RoPE table,
TMA-descriptor prefetch in the attention loader, and programmatic
dependent launch across every launch of the tower.

## Evidence (Cake export protocol, producer `5964871e82a`, target
`fd757bf11f`)

Every contract row is measured on the source (Cake production launcher)
and the exported programs in counterbalanced groups; `source_ms /
export_ms >= 0.97`, directional disagreement `<= 0.02`, endpoint drift
`<= 0.02`, correctness = bitwise `source == export` plus the contract's
FP32-oracle fairness gate against the fastest FlashInfer
ragged-attention chain (`fa2` / `cudnn` / `cutlass` / `cute-dsl`, chosen
by timing per row; rows with < 64 output tokens pool 8 pixel seeds). One
uninterrupted single-cache round per architecture (fresh exporter state,
all 22 rows, 4 GPUs).

| arch | GPU | rows measured | passed | source/export (min .. max) |
directional disagreement | endpoint drift |
|---|---|---|---|---|---|---|
| sm_100a | B200 (4 GPUs, one build session) | 22 | 22 | 0.9747 ..
1.0079 (geomean 0.9983) | <= 0.0038 | <= 0.0171 |
| sm_103a | B300 (4 GPUs, one build session) | 22 | 22 | 0.9706 ..
1.0057 (geomean 0.9983) | <= 0.0007 | <= 0.0160 |

Pooled smoke rows (8 seeds, candidate/reference-chain mean-error ratio):
B200 `smoke_2x2` 0.9993 / `smoke_ragged` 1.0011 / `smoke_t3` 0.9977;
B300 `smoke_2x2` 0.9993 / `smoke_ragged` 1.0001 / `smoke_t3` 0.9993
(violation ratios 0.9949-1.0070; all pass). Delivery is byte-identical
from both rounds (delivery.patch SHA-256
`cf982040c1c9a069c8d91d827374b57afb9ef0b3551864475a11118e1f5676ec`).

Speed vs the round-1 programs and vs the FlashInfer chain: see the Cake
MR (CAKE-663) design doc; the export protocol measures source == export
parity, not speed vs peers.

Receipts, raw timings and state copies stay on the cluster (host / path
/ size / SHA-256 recorded in the Cake MR's design doc and
`exports/kimi_k3_vision_tower/README.md`).

## Baselines and their source PRs

The export's correctness gate compares both arms against the FP32 tower
oracle relative to the HF BF16 chain whose attention is the fastest
FlashInfer ragged BF16 route of this checkout
(`BatchPrefillWithRaggedKVCacheWrapper(kv_layout="NHD", backend=...)`,
chosen by timing per row). Branch upstream merge-base: `e34a1735a`
(2026-09-25, "feat(moe): wire dynamic FP8 FC2 quantization for
per-channel MoE (#5149)").

- `fa2` route: `flashinfer/prefill.py` (last upstream change #5350
`7685a893e`, 2026-09-24), `csrc/batch_prefill.cu` (#5176 `e0a18900c`,
2026-09-21), `include/flashinfer/attention/prefill.cuh` (#5239
`b8107c7fd`, 2026-09-17).
- `cudnn` route: `flashinfer/cudnn/prefill.py` (#5350 `7685a893e`,
2026-09-24).
- `cutlass` route: `csrc/fmha_cutlass_sm100.cu` (#3064 `1aa32d03e`,
2026-05-08), `csrc/fmha_cutlass_sm100_binding.cu` (#2047 `db2aacbd3`,
2025-12-17).
- `cute-dsl` route: `flashinfer/cute_dsl/attention/fmha/` (#4859
`f17b77260`, 2026-09-18; cubin refresh #4997 `75038cdf6`, 2026-09-10).
- Chain RMSNorm: `flashinfer/norm/` (#5305 `012542c85`, 2026-09-18).
- Previous programs (replaced by this PR): round-1 delivery from #5554
(`6dd3104a7`, 2026-09-25); the package tests / FP32-oracle stage tests
of that PR (`tests/experimental/test_cake_kimi_k3_vision_tower.py`) are
the test oracle, extended in `fd757bf11` for the round-2 tile policy.

No upstream commit after the merge-base touched any of these files (`git
log e34a1735a..origin/main -- <files>` is empty at `78c6e1fbf`, the two
later commits are #5564 and #5530).

## Test

```
pytest tests/experimental/test_cake_kimi_k3_vision_tower.py
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Optimized Kimi K3 vision-tower processing with packed RoPE data and
more efficient residual, normalization, and output handling.
* Added programmatic coordination between GPU workloads, including
support for CUDA graph capture.
* **Compatibility**
* Updated kernel selection across supported GPU architectures;
production tile selection avoids tail-split configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c0aca1f](https://github.com/flashinfer-ai/flashinfer/commit/c0aca1fa944cd5efd0e7bf5c003dd77e35d341d1)

- **作者**: eigen
- **时间**: 2026-09-26T21:05:58Z
- **提交信息**: feat(cake_vsa_sm90): SM90 BF16 variable block-sparse attention backend for VariableBlockSparseAttentionWrapper (#5569)

## Summary

Adds `backend="cake"` to `VariableBlockSparseAttentionWrapper` on Hopper
(compute capability 9.0): generated Cake kernels for BF16 variable
block-sparse attention with 64-token blocks, behind the wrapper's
unchanged `plan()` / `run()` contract. Two kernels share one planner: a
persistent-CTA kernel (pair/split tiles, shared ring positions) and a
small-selection kernel (at most 6 selected KV blocks per query block on
one-wave grids: one CTA per query block, plan passed in the
kernel-parameter constant bank).

**Supported scope** (explicit): BF16 HND `q/k/v` of shape `(H, S, 128)`;
`head_dim == 128`; `num_qo_heads == num_kv_heads`; noncausal; uniform
64-token query and KV blocks (`block_row_sz == block_col_sz == 64`);
boolean `block_mask_map` of shape `(H, MB, NB)` with 1..64 selected KV
blocks per query block (ragged counts allowed, empty rows rejected);
custom finite `sm_scale` (including 0 and negative); `out` in the
wrapper's DPS ABI `[H*M, 1, 128]` (contiguous, must not overlap
`q/k/v`), return value HND `[H, M, 128]`; offset (16-byte misaligned)
views are copied on the current stream; reusable uploaded plan,
cross-stream readiness (event wait on the plan upload), replanning,
fixed-plan CUDA-graph replay (a preallocated `out` is required inside
capture; a captured plan cannot be replaced).

**Unsupported** (raise `ValueError`): GQA/MQA, causal,
`return_lse`/`lse`, PDL, positional encodings, `logits_soft_cap`, FP16
QK reduction, FP16 inputs, `head_dim != 128`, non-64 block sizes, more
than 64 selected KV blocks per query block. Automatic backend selection
never picks `cake`.

## Kernel

`csrc/cake_vsa_sm90/` is a source-only export (`cake.library_export.v4`
manifest, device `.cu` + tvm-ffi binding; TMA descriptors in the
`grid_constant` ABI are encoded from the tensors on every call, so a
fixed plan replays under CUDA graphs without descriptor storage).
Persistent CTAs (`grid = min(tiles, SMs)`), one producer warpgroup (K
loader, V^T loader, two plan stagers that also arm Q), two consumer
warpgroups doing m64n128k128 QK + PV per ring position (two 64-token KV
blocks per position) in FA3 order; the host planner
(`flashinfer/cake_vsa_sm90.py`, no Cake dependency) emits per-CTA tile
lists in *split* mode (both warpgroups alternate over one query block's
positions and merge FP32 partials in SMEM) or *pair* mode (two query
blocks of one head share the KV ring, shared blocks loaded once),
whichever has the smaller modelled makespan.

## Files

- `csrc/cake_vsa_sm90/{sm_90a/*_kernel.cu, sm_90a/*_binding.cu,
cake_vsa_sm90_manifest.json}` — generated (Cake `python -m
loom.export.flashinfer_sm90_vsa render`), do not edit by hand
- `flashinfer/jit/cake_vsa_sm90.py` — manifest-checked JIT loader
(`sm90a_nvcc_flags`), one module per stage (`attention`,
`small_k1/k3/k4/k6`)
- `flashinfer/cake_vsa_sm90.py` — planner (dependency-free port of the
Cake planner: pair/split selection, LPT tile order for ragged plans that
fit L2, small-route rule) + plan object
- `flashinfer/sparse.py` — `backend="cake"` dispatch in
`VariableBlockSparseAttentionWrapper.__init__/plan/run`
- `tests/experimental/test_cake_vsa_sm90.py` — planner invariants (CPU),
FA3 cross-check on the PR #5470 schedule matrix, FP32-reference held-out
shapes (boundary/tail, full 64-block capacity, unequal Q/KV lengths,
ragged, custom scales), replanning, padding math, signed/tiny scales,
offset views + alias rejection, stream/graph lifetime, unsupported
options
- `benchmarks/bench_cake_vsa_sm90.py` — 20-case paired alternating-order
CUPTI comparison (cold L2 default, `--warm-l2` separately) vs `fa3`
(main) or `vsa_sm90_blk64` (PR #5470 checkout)

## Tests

```
pytest tests/experimental/test_cake_vsa_sm90.py -v          # H100 (GPU tests skip elsewhere)
python benchmarks/bench_cake_vsa_sm90.py --output /tmp/vsa-sm90-cake.json            # vs fa3
python benchmarks/bench_cake_vsa_sm90.py --output /tmp/vsa-sm90-cake-pr5470.json --baseline vsa_sm90_blk64   # inside a #5470 checkout
```

## Results (H100 SXM 80GB, driver 535.216.03, node pool0-01853, run
`fi_combo_r45b`)

`benchmarks/bench_cake_vsa_sm90.py --baseline vsa_sm90_blk64 --pairs 6`
inside a #5470 checkout with this branch applied: both backends through
`VariableBlockSparseAttentionWrapper` in one process, 6
alternating-order A/B pairs per case, cold L2 (CUPTI kernel time), both
validated against the FP32 reference in the same run. Warm L2
(`--warm-l2 --pairs 3`) is a separate run, reported separately.

| case | vsa_sm90_blk64 us | cake us | cake/blk64 (cold) | warm ratio
(separate) |
|---|---|---|---|---|
| h1-m64-n64-k1-ragged0-scale0 | 3.368 | 2.952 | **1.141** | 1.123 |
| h4-m256-n256-k1-ragged0-scale0 | 3.712 | 3.360 | **1.105** | 1.091 |
| h8-m256-n256-k3-ragged0-scale0 | 5.632 | 5.183 | **1.087** | 1.153 |
| h8-m1024-n1024-k4-ragged0-scale0 | 8.655 | 7.744 | **1.118** | 1.231 |
| h8-m1024-n1024-k12-ragged0-scale0 | 13.216 | 11.200 | **1.180** |
1.239 |
| h8-m2048-n2048-k8-ragged0-scale0 | 16.080 | 15.495 | **1.038** | 0.930
|
| h8-m2048-n2048-k16-ragged0-scale0 | 23.696 | 22.560 | **1.050** |
1.086 |
| h8-m4096-n4096-k16-ragged0-scale0 | 44.192 | 40.104 | **1.102** |
1.157 |
| h8-m4096-n4096-k32-ragged0-scale0 | 77.192 | 66.376 | **1.163** |
1.143 |
| h4-m512-n1024-k4-ragged0-scale0 | 6.688 | 6.496 | **1.030** | 1.173 |
| h4-m1024-n512-k4-ragged1-scale0 | 7.744 | 6.368 | **1.216** | 1.404 |
| h4-m1024-n1024-k8-ragged1-scale0 | 9.888 | 8.640 | **1.144** | 1.217 |
| h7-m4096-n4096-k16-ragged1-scale0 | 29.272 | 24.848 | **1.178** |
1.216 |
| h4-m512-n512-k4-ragged0-scale1 | 6.528 | 6.048 | **1.079** | 1.190 |
| h1-m1024-n1024-k16-ragged0-scale0 | 13.296 | 11.552 | **1.151** |
1.227 |
| h7-m16384-n16384-k32-ragged0-scale0 | 259.335 | 234.967 | **1.104** |
1.111 |
| h7-m32768-n32768-k64-ragged0-scale0 | 963.492 | 899.317 | **1.071** |
1.075 |
| h7-m65536-n65536-k64-ragged0-scale0 | 1990.153 | 1954.202 | **1.018**
| 1.019 |
| h7-m109632-n109632-k64-ragged0-scale0 | 3735.438 | 3491.166 |
**1.070** | 1.070 |
| h7-m109632-n109632-k64-ragged1-scale0 | 1794.013 | 1691.677 |
**1.060** | 1.048 |

Cold geomean **1.1039**, min 1.018, **20/20 cases faster**. Warm geomean
1.1410, min 0.930 (h8-m2048-k8). Against the `fa3` backend on main
(separate, 2 pairs): geomean 1.814x, min 1.418x.

Routing per case: capacity <= 6 on a one-wave grid (k1 x2, k3, the k4
cases) uses the small-selection kernel; everything else the persistent
kernel.

Tests on H100: `tests/experimental/test_cake_vsa_sm90.py` 64 passed;
#5470's own `tests/experimental/test_vsa_sm90.py` GPU tests with
`backend="cake"` 16 passed (27 CPU tests bound to #5470's metadata
module deselected; control on the original route 43 passed).
compute-sanitizer synccheck 0 errors / racecheck 0 kernel hazards on the
small kernel (k1/k3/k4/k6, ragged, scales 0/-0.125/1) and the persistent
plans (see the Cake design doc).

## Baselines and their source PRs

- `vsa_sm90_blk64` — flashinfer-ai/flashinfer PR #5470 (`feat(sparse):
add experimental Hopper CuTe DSL VSA backend`), head
`9f35c6acfda7a2cd5719835dce7291d4b5da816e` (open at the time of writing;
rerun on the same H100 in the same process as the candidate; files
`flashinfer/experimental/vsa_sm90/*`,
`tests/experimental/test_vsa_sm90.py`, `benchmarks/bench_vsa_sm90.py`);
its 20-case matrix and `make_inputs` are reproduced verbatim in
`benchmarks/bench_cake_vsa_sm90.py`.
- `fa3` — the wrapper's existing FA3 backend on `main`
(`e34a1735aecae0819be9c7a44f2e7c8e0d023aff`), used as the numerical
cross-reference in the tests, as in #5470.

## Provenance

Cake MR:
[averyh/r94494673bb0150eeffa896f7!925](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/925)
(NVIDIA GitLab; design doc `design_doc/active/CAKE_659_SM90_VSA.md` with
the full comparison table, roofline fractions and evidence manifest).
Linear CAKE-659.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added Cake variable block-sparse attention for compatible SM90 GPUs,
with automatic planning and kernel selection.
* Added support for using the Cake backend through the sparse attention
wrapper.
* **Bug Fixes**
* Added input and execution checks to report unsupported configurations
and invalid data clearly.
* **Tests**
* Added planner tests and SM90 GPU checks for output accuracy,
scheduling, and supported execution scenarios.
* **Documentation**
  * Documented Cake backend constraints and routing behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [316a705](https://github.com/flashinfer-ai/flashinfer/commit/316a70578a90749113ab375e9fa88b323034f9a0)

- **作者**: eigen
- **时间**: 2026-09-26T21:00:47Z
- **提交信息**: perf(cake_warp_decode): route the SM103 Qwen3-30B-A3B num_tokens=8 warp-decode row onto the fused route-pack K256 path (#5574)

## NVFP4 warp-decode: sm_103a Qwen3-30B-A3B num_tokens 8 joins the fused
route-pack rows

Policy-only update of the public-model NVFP4 warp-decode portfolio
(SM100 / SM103, num_tokens 1–32). One row changes: **SM103 Qwen3-30B-A3B
(2048, 768, 128, 8) at num_tokens 8** moves from the direct route to the
fused route-pack schedule that already serves num_tokens 9–19 on SM103
(persistent FC1 that derives the packed route table in its prologue,
route-parallel K256 FC2 with workfeed prefetch, fixed top-8 packed
finalizer; three launches per row). No kernel source or schedule
changes; 0 new modules; the two direct-route modules that only served
this row retire (SM103 36 -> 34 modules); the other 66 modules are
byte-identical to the previous export (program hash `d0025e1d…` ->
`1958b9aa…`). SM100 is untouched.

Files: `csrc/fused_moe/warp_decode/cake_warp_decode_contract.cuh`
(boundary table: num_tokens 8 joins the fused K256 rows for this model
on SM103), `generated/cake_warp_decode_generated_manifest.cuh`,
`generated/cake_warp_decode_inventory.json`, the SM103 sequence binding
for the changed route table (`seq_fa182508…` -> `seq_16455d3e…`), and
the four retired module files.

### Gates (same protocol as the previous update)

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

Previous status of this row: B/E_o 0.9976 (direct route, the only row of
448 that missed the baseline gate).

### What changed (SM103 Qwen3-30B-A3B, 32 rows re-measured across three
independent B300 allocations; num_tokens 8 in two of them)

Independent B300 session 1 (rows t01-t08):

| num_tokens | baseline µs | export µs (E_o) | B/E_o | source µs |
export µs (E_s) | S/E_s | S/E_s ≥ 1 |
|---:|---:|---:|---:|---:|---:|---:|:-:|
| 1 | 16.736 | 15.840 | 1.0566 | 15.488 | 15.424 | 1.0041 | yes |
| 2 | 21.568 | 19.681 | 1.0959 | 19.936 | 19.712 | 1.0114 | yes |
| 3 | 25.344 | 23.968 | 1.0574 | 23.968 | 23.936 | 1.0013 | yes |
| 4 | 28.960 | 27.328 | 1.0597 | 27.329 | 27.360 | 0.9989 | no |
| 5 | 30.753 | 30.560 | 1.0063 | 30.689 | 30.560 | 1.0042 | yes |
| 6 | 33.984 | 33.600 | 1.0114 | 33.409 | 33.600 | 0.9943 | no |
| 7 | 37.440 | 37.153 | 1.0077 | 36.864 | 37.121 | 0.9931 | no |
| 8 | 39.440 | 38.624 | 1.0211 | 38.784 | 38.592 | 1.0050 | yes |

Independent B300 session 2 (rows t01-t08, t09-t16):

| num_tokens | baseline µs | export µs (E_o) | B/E_o | source µs |
export µs (E_s) | S/E_s | S/E_s ≥ 1 |
|---:|---:|---:|---:|---:|---:|---:|:-:|
| 1 | 16.704 | 15.936 | 1.0482 | 15.617 | 15.616 | 1.0001 | yes |
| 2 | 21.344 | 19.777 | 1.0792 | 20.097 | 19.776 | 1.0162 | yes |
| 3 | 25.344 | 23.968 | 1.0574 | 24.033 | 23.937 | 1.0040 | yes |
| 4 | 28.769 | 27.393 | 1.0502 | 27.392 | 27.392 | 1.0000 | yes |
| 5 | 30.977 | 30.592 | 1.0126 | 30.689 | 30.560 | 1.0042 | yes |
| 6 | 33.985 | 33.601 | 1.0114 | 33.440 | 33.632 | 0.9943 | no |
| 7 | 37.440 | 37.152 | 1.0078 | 36.896 | 37.153 | 0.9931 | no |
| 8 | 39.457 | 38.624 | 1.0216 | 38.785 | 38.625 | 1.0041 | yes |
| 9 | 41.377 | 41.281 | 1.0023 | 41.280 | 41.281 | 1.0000 | no |
| 10 | 42.880 | 42.561 | 1.0075 | 42.721 | 42.592 | 1.0030 | yes |
| 11 | 44.224 | 43.841 | 1.0087 | 43.777 | 43.745 | 1.0007 | yes |
| 12 | 45.696 | 45.249 | 1.0099 | 45.280 | 45.249 | 1.0007 | yes |
| 13 | 47.744 | 47.105 | 1.0136 | 47.073 | 47.136 | 0.9987 | no |
| 14 | 48.352 | 47.809 | 1.0114 | 47.681 | 47.776 | 0.9980 | no |
| 15 | 50.304 | 49.345 | 1.0194 | 49.504 | 49.344 | 1.0032 | yes |
| 16 | 51.328 | 50.305 | 1.0203 | 50.497 | 50.305 | 1.0038 | yes |

Independent B300 session 3 (rows t17-t24, t25-t32):

| num_tokens | baseline µs | export µs (E_o) | B/E_o | source µs |
export µs (E_s) | S/E_s | S/E_s ≥ 1 |
|---:|---:|---:|---:|---:|---:|---:|:-:|
| 17 | 53.312 | 51.616 | 1.0329 | 51.904 | 51.616 | 1.0056 | yes |
| 18 | 54.496 | 53.345 | 1.0216 | 53.280 | 53.345 | 0.9988 | no |
| 19 | 54.944 | 53.633 | 1.0244 | 53.793 | 53.760 | 1.0006 | yes |
| 20 | 55.425 | 54.689 | 1.0135 | 54.816 | 54.817 | 1.0000 | no |
| 21 | 56.545 | 56.000 | 1.0097 | 56.097 | 55.936 | 1.0029 | yes |
| 22 | 57.760 | 57.089 | 1.0118 | 57.184 | 57.088 | 1.0017 | yes |
| 23 | 57.793 | 56.865 | 1.0163 | 56.928 | 56.865 | 1.0011 | yes |
| 24 | 58.273 | 57.345 | 1.0162 | 57.536 | 57.473 | 1.0011 | yes |
| 25 | 59.904 | 59.329 | 1.0097 | 59.297 | 59.233 | 1.0011 | yes |
| 26 | 61.697 | 61.313 | 1.0063 | 61.281 | 61.184 | 1.0016 | yes |
| 27 | 62.304 | 61.600 | 1.0114 | 61.760 | 61.633 | 1.0021 | yes |
| 28 | 62.496 | 62.112 | 1.0062 | 62.240 | 62.081 | 1.0026 | yes |
| 29 | 63.872 | 62.912 | 1.0153 | 63.008 | 62.849 | 1.0025 | yes |
| 30 | 64.288 | 63.361 | 1.0146 | 63.424 | 63.329 | 1.0015 | yes |
| 31 | 65.153 | 64.320 | 1.0130 | 64.352 | 64.321 | 1.0005 | yes |
| 32 | 65.185 | 64.225 | 1.0149 | 64.352 | 64.257 | 1.0015 | yes |

### Validation

- Correctness on SM103 for every exported Qwen3-30B-A3B route (FP4
tolerance atol 1.0 / rtol 0.1 against the PyTorch reference) plus the
export pipeline's source/export/build/runtime/manifest/route checks; the
66 retained modules are byte-identical to the merged export and keep
their previous validation.
- compute-sanitizer synccheck and racecheck (run separately; memcheck
not run) on the SM103 num_tokens 8 module set: 2/2 PASS (synccheck and
racecheck, 0 errors, 0 hazards) on SM103 for the num_tokens 8 route.

### Baselines and their source PRs

- Baseline arm (B): the FlashInfer trtllm-gen NVFP4 fused-MoE path
(`flashinfer.fused_moe` trtllm-gen batched-GEMM cubins
`batched_gemm-09795a1-31ee4e5`, the cubin set the previous update was
measured against), invoked through the same pre-routed physical contract
as before. Implementation files: `flashinfer/fused_moe/core.py`,
`csrc/trtllm_fused_moe_kernel_launcher.cu`,
`csrc/trtllm_fused_moe_runner.cu`,
`csrc/trtllm_fused_moe_routing_binding.cu`,
`include/flashinfer/trtllm/fused_moe/`. Most recent upstream changes to
these files before this branch's merge-base: #5149 (`e34a1735a`,
2026-09-25), #5281 (`476f7bbdd`, 2026-09-17), #5207 (`7281e687a`,
2026-09-16), #4894 (`7554a6ed0`, 2026-09-16). This branch's merge-base
with `flashinfer-ai/flashinfer` main is `78c6e1fbf` (the upstream head
at branch time); `git log 78c6e1fbf..upstream/main -- <baseline files>`
was empty when the PR was opened, so the baseline sources listed above
are exactly the ones in the merge-base and the comparison arm did not
move between measurement and publication.
- Source arm (S): the reference implementation the export is generated
from (Cake NVFP4 warp-decode schedules, same revision as the merged
export).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved execution efficiency for Qwen3-30B workloads with 8 tokens on
supported SM103a GPUs.
  * Kept the existing 10-token threshold for supported SM100a GPUs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5bb9498](https://github.com/flashinfer-ai/flashinfer/commit/5bb9498d1c5643a9dc9cfcf771a3f471b990fa27)

- **作者**: eigen
- **时间**: 2026-09-26T20:55:15Z
- **提交信息**: perf(cake_minimax_h3): fp8-PV split-program schedule fix and sm_103a split-cost recalibration (SM100/SM103) (#5571)

## 📌 Description

Follow-up to #5499 / #5530
(`flashinfer.experimental.minimax_h3_varlen_attention`, MiniMax-H3
packed-varlen attention,
SM100/SM103). One kernel-side change and one planner recalibration, both
for the **NVFP4 fp8-PV route**; the BF16 and
fp4-PV programs are byte-identical to the merged package.

**sm_103a fp8-PV split program at parity with the dense program.** The
split-capable fp8-PV program (bound when the host
planner K/V-splits partial-wave units) cost 1.21x the dense program per
unit on B300, so the planner carried a 1.35 program
cost and B300 fp8-PV partial-wave rows rarely split. Per-instruction
stall sampling plus a decode of the SASS dependency
scoreboards found the cause: in the split program the compiler placed
the result of the "P buffer free" mbarrier
`try_wait` and an `ex2` result on the same scoreboard, so the first E4M3
pack of every K/V block waited for the previous
stage's PV drain instead of overlapping it (one instruction carried 10 %
of all stall samples, all long-scoreboard). The fp8
softmax body now does its register-only work (scale, `exp2`, first E4M3
pack) first and waits for the free buffer right
before the first TMEM store. Paired program cost on the same unsplit
plan (same node, CUPTI, cold L2):

| Row | B300 before (split / dense ms) | B300 after | B200 after |
|---|---:|---:|---:|
| center_4s_p1_m33472 | 15.05 / 12.42 (1.21x) | 12.335 / 12.330 (1.00x)
| 16.94 / 17.00 (1.00x) |
| center_4s_p4_m8368 | 0.3257 / 0.2511 (1.30x) | 0.2509 / 0.2493 (1.01x)
| 0.3661 / 0.3657 (1.00x) |
| center_6s_p8_m6096 | 0.1238 / 0.0974 (1.27x) | 0.0989 / 0.0982 (1.01x)
| 0.1403 / 0.1404 (1.00x) |

`SPLIT_PROGRAM_COST[("fp8", "sm_103a")]` in `cake_backend.py` drops from
1.35 to 1.01 (paired measurement), so the B300
planner now splits e.g. `center_4s_p4_m8368` 4-way (0.213 vs 0.249 ms
complete attention + combine) and
`center_6s_p8_m6096` 7-way (0.068 vs 0.099 ms).

**Not changed:** a two-stage TMA-staged quantizer was built and measured
(bit-identical output) and does not pay: a plain
same-size device copy only reaches 4.3-4.8 TB/s at the 29-44 MB sizes of
the single-wave rows, the current quantizer is at
71-78 % of that copy roofline, and the staged form is 0.85-1.02x on
those rows; it is not part of this PR.

Regenerated programs (both architectures): `nvfp4_fp8pv` `attention` and
`attention_split`. Unchanged and byte-identical
to #5530: every `bf16` and `nvfp4_fp4pv` program, `quantize`, `amax`,
`combine`.

## Paired evidence on this delivery (same node, merged package vs this
PR, complete call, four arms old/new/old/new)

### fp8-PV: the eight targeted B300 partial-wave rows plus the other
sub-3.6-wave rows (11 rows, both architectures)

| Row (fp8pv) | B200 merged ms | B200 PR ms | B200 ratio | B200 PR vs
cutlass | B300 merged ms | B300 PR ms | B300 ratio | B300 PR vs cutlass
|
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| center_6s_p8_m6096 (listed) | 0.1056 | 0.1046 | 1.0096x | 1.978x |
0.0949 | 0.0805 | **1.1789x** | 2.009x |
| center_8s_p8_m7368 (listed) | 0.1484 | 0.1471 | 1.0092x | 1.692x |
0.1305 | 0.1103 | **1.1837x** | 1.735x |
| center_4s_p4_m8368 (listed) | 0.3386 | 0.3353 | 1.0098x | 1.629x |
0.2835 | 0.2455 | **1.1550x** | 1.737x |
| center_15s_p8_m13744 (listed) | 0.4236 | 0.4202 | 1.0082x | 1.583x |
0.3312 | 0.3095 | **1.0701x** | 1.666x |
| center_5s_p4_m9648 (listed) | 0.4395 | 0.4363 | 1.0073x | 1.477x |
0.3326 | 0.3236 | 1.0275x | 1.540x |
| tail_5s_p4_m9587 (listed) | 0.4385 | 0.4347 | 1.0087x | 1.475x |
0.3305 | 0.3212 | 1.0290x | 1.536x |
| tail_5s_p4_m9685 (listed) | 0.4409 | 0.4380 | 1.0066x | 1.478x |
0.3346 | 0.3250 | 1.0295x | 1.538x |
| center_10s_p8_m9280 (listed) | 0.2240 | 0.2251 | 0.9953x | 1.367x |
0.1604 | 0.1602 | 1.0012x | 1.468x |
| center_10s_p4_m18560 | 1.5350 | 1.5362 | 0.9992x | 1.446x | 1.1182 |
1.1126 | 1.0050x | 1.553x |
| center_4s_p8_m4184 | 0.0646 | 0.0648 | 0.9969x | 1.249x | 0.0503 |
0.0502 | 1.0030x | 1.260x |
| center_5s_p8_m4824 | 0.0723 | 0.0726 | 0.9966x | 1.258x | 0.0556 |
0.0554 | 1.0027x | 1.288x |
| **geomean / min** | | | **1.0043x / 0.9953x** | 1.500x / 1.249x | | |
**1.0601x / 1.0012x** | 1.563x / 1.260x |

Ratio = mean of the two merged arms / mean of the two PR arms (complete
call, CUPTI cold L2, 5 paired groups x 200 ms
per arm); "vs cutlass" = the PR arms' speedup over the FlashInfer SM100
CUTLASS FMHA route measured in the same arm. 44
arm-rows per arch, 0 correctness failures; one B200 and one B300 node,
both arms of a row on the same node.

Why the listed rows land where they do (host planner replayed offline
for B300, 74 clusters; predicted = simulated
dense makespan / split makespan at program cost 1.01, including the
combine):

| Row | units / waves | plan at cost 1.35 (before) | plan at cost 1.01
(this PR) | predicted | measured B300 |
|---|---:|---|---|---:|---:|
| center_6s_p8_m6096 | 84 / 1.14 | split 7-way x 10 tail units | same |
1.563x | 1.179x |
| center_8s_p8_m7368 | 105 / 1.42 | dense | split 2-way x 31 tail units
| 1.248x | 1.184x |
| center_4s_p4_m8368 | 238 / 3.22 | dense | split 4-way x 16 tail units
| 1.185x | 1.155x |
| center_15s_p8_m13744 | 189 / 2.55 | dense | split 5-way x 41 tail
units | 1.096x | 1.070x |
| center_5s_p4 / tail_5s_p4 (x3) | 266 / 3.59 | dense | split 5-way x 44
tail units | 1.053x | 1.028-1.030x |
| center_10s_p8_m9280 | 133 / 1.80 | dense | dense (no candidate beats
the dense makespan by 3 % at any cost: 8-block units, 2-block per-chunk
overhead) | 1.000x | 1.001x |
| pad_5s_p4 | - | not an NVFP4 contract row (BF16 only) | - | - | - |

center_6s_p8 was already split before; its gain is the split program
running at dense cost (1.27x -> 1.01x per unit).
The three 3.59-wave rows now split but gain 2.8-3.0 % (model 5.3 %):
each of the 220 chunks pays the 2-block unit
overhead and the combine, which the makespan model under-weights at k=5;
they stay below the 1.05x bar and are recorded
as the lever's residual. center_10s_p8 cannot be helped by a K/V split
at all (structural). sm_100a fp8pv rows move
0.995-1.010x (>= 0.99x clause met); the fp4pv and bf16 programs are
cubin-identical.

### fp8-PV: the remaining 23 contract rows (>= 0.99x clause), both
architectures

| Row (fp8pv) | B200 merged ms | B200 PR ms | B200 ratio | B200 PR vs
cutlass | B300 merged ms | B300 PR ms | B300 ratio | B300 PR vs cutlass
|
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| center_10s_p1_m74240 | 88.1822 | 88.3171 | 0.9985x | 1.652x | 64.4468
| 64.0867 | 1.0056x | 1.858x |
| center_10s_p2_m37120 | 11.9512 | 11.9519 | 0.9999x | 1.491x | 9.1626 |
9.1158 | 1.0051x | 1.565x |
| center_15s_p1_m109952 | 187.7432 | 187.4384 | 1.0016x | 1.737x |
135.0514 | 134.2743 | 1.0058x | 2.002x |
| center_15s_p2_m54976 | 26.9830 | 27.0774 | 0.9965x | 1.427x | 20.4635
| 20.3272 | 1.0067x | 1.520x |
| center_15s_p4_m27488 | 3.4458 | 3.4386 | 1.0021x | 1.474x | 2.5199 |
2.5102 | 1.0039x | 1.599x |
| center_4s_p1_m33472 | 19.9770 | 20.0029 | 0.9987x | 1.451x | 15.2195 |
15.1517 | 1.0045x | 1.518x |
| center_4s_p2_m16736 | 2.5843 | 2.5881 | 0.9985x | 1.446x | 1.8951 |
1.8851 | 1.0053x | 1.565x |
| center_5s_p1_m38592 | 27.1774 | 27.1233 | 1.0020x | 1.408x | 20.5018 |
20.4147 | 1.0043x | 1.502x |
| center_5s_p2_m19296 | 3.4062 | 3.4085 | 0.9993x | 1.458x | 2.5186 |
2.5086 | 1.0040x | 1.573x |
| center_6s_p1_m48768 | 41.3946 | 41.4304 | 0.9991x | 1.490x | 31.1974 |
31.0624 | 1.0043x | 1.597x |
| center_6s_p2_m24384 | 5.3982 | 5.4054 | 0.9987x | 1.465x | 3.9306 |
3.9130 | 1.0045x | 1.585x |
| center_6s_p4_m12192 | 0.7118 | 0.7123 | 0.9994x | 1.431x | 0.5177 |
0.5158 | 1.0038x | 1.545x |
| center_8s_p1_m58944 | 58.0581 | 58.0080 | 1.0009x | 1.587x | 43.2605 |
42.9757 | 1.0066x | 1.732x |
| center_8s_p2_m29472 | 7.6090 | 7.6135 | 0.9994x | 1.472x | 5.6886 |
5.6472 | 1.0073x | 1.611x |
| center_8s_p4_m14736 | 1.0317 | 1.0327 | 0.9991x | 1.440x | 0.7483 |
0.7455 | 1.0038x | 1.559x |
| seg3_5s_p8_m4824 | 0.0673 | 0.0675 | 0.9970x | 1.213x | 0.0522 |
0.0520 | 1.0029x | 1.224x |
| seg4_6s_p2_m24384 | 2.8352 | 2.8274 | 1.0027x | 1.407x | 2.1018 |
2.1020 | 0.9999x | 1.530x |
| tail_5s_p1_m38531 | 27.1126 | 27.1314 | 0.9993x | 1.406x | 20.5251 |
20.3486 | 1.0087x | 1.501x |
| tail_5s_p1_m38629 | 27.1097 | 27.0615 | 1.0018x | 1.409x | 20.5684 |
20.4575 | 1.0054x | 1.502x |
| tail_5s_p2_m19235 | 3.4024 | 3.4006 | 1.0005x | 1.457x | 2.5257 |
2.5113 | 1.0057x | 1.576x |
| tail_5s_p2_m19333 | 3.4253 | 3.4238 | 1.0004x | 1.456x | 2.5318 |
2.5226 | 1.0036x | 1.578x |
| tail_5s_p8_m4763 | 0.0721 | 0.0723 | 0.9972x | 1.262x | 0.0557 |
0.0555 | 1.0036x | 1.289x |
| tail_5s_p8_m4861 | 0.0723 | 0.0725 | 0.9979x | 1.256x | 0.0558 |
0.0556 | 1.0036x | 1.292x |
| **geomean / min** | | | **0.9996x / 0.9965x** | 1.443x / 1.213x | | |
**1.0047x / 0.9999x** | 1.549x / 1.224x |

Four arms old/new/old/new, 3 paired groups x 200 ms per arm, complete
call only (no stage breakdown), 92 arm-rows per
arch, 0 correctness failures. B200: one step. B300:
the first step was SIGTERM-cancelled by the control plane at the start
of arm 3 after arms 1-2 had completed and been
written, so arms 3-4 ran as a second step on the same node with the same
two trees 20 minutes later (per-row ratio still
= mean of the two merged arms / mean of the two PR arms). Every row >=
0.99x vs merged on both arches (worst 0.9965x,
center_15s_p2 on B200, within the arm-to-arm spread) and >= 1.21x vs the
cutlass route.

## Baselines and their source PRs

The "vs this PR's predecessor" columns compare against the merged
package at `f7f1577ae` (#5530, 2026-09-26; introduced by
#5499 `e550d6a04`, 2026-09-23); the "vs cutlass" columns compare against
the **fastest upstream ragged noncausal BF16 prefill
route per row** (`BatchPrefillWithRaggedKVCacheWrapper`,
`kv_layout="NHD"`, planned once per shape outside the timed
region, `run()` timed with CUPTI, cold L2) — the `cutlass` route (SM100
CUTLASS FMHA) on every row. Baseline revision: this
branch's upstream merge-base `78c6e1fbf` (2026-09-26).

| Route / component | Implementation files | Introduced | Last change at
the merge-base |
|---|---|---|---|
| this package (predecessor) |
`flashinfer/experimental/minimax_h3_varlen_attention/` | #5499
(`e550d6a04`, 2026-09-23) | #5530 (`f7f1577ae`, 2026-09-26) |
| `cutlass` (SM100 CUTLASS FMHA, the winning upstream route) |
`csrc/fmha_cutlass_sm100.cu`, `csrc/fmha_cutlass_sm100_binding.cu`,
`include/flashinfer/attention/blackwell/` | #1039 (`9a05c92ad`,
2025-05-12) | #3064 (`1aa32d03e`, 2026-05-08) |
| `cute-dsl` (DSL FMHA cubins) | `flashinfer/attention/cute_dsl/fmha.py`
| #3039 (`bb873d207`, 2026-04-24) | #4997 (`75038cdf6`, 2026-09-10) |
| `cudnn` | `flashinfer/cudnn/prefill.py` | #1187 (`ece99ccce`,
2025-06-30) | #5350 (`7685a893e`, 2026-09-24) |
| `fa2` | `csrc/batch_prefill.cu`, `csrc/batch_prefill_jit_binding.cu`,
`include/flashinfer/attention/prefill.cuh` | #643 / #143 | #5176
(`e0a18900c`, 2026-09-21) |
| wrapper (`flashinfer/prefill.py`, route dispatch) |
`flashinfer/prefill.py` | #643 | #5350 (`7685a893e`, 2026-09-24) |

No commit on `origin/main` after the merge-base (`git log
78c6e1fbf..origin/main -- <files>` at `78c6e1fbf`, fetched 2026-09-26;
origin/main is the merge-base itself) touches any of
these files. The correctness oracle is the package's own FP32 reference
(`_reference` in the test file; tolerances BF16
`atol=rtol=1e-2`, NVFP4 `atol=1.0 / rtol=0.1`, unchanged), not an
upstream kernel.

## 🔍 Related Issues

#4254 (tracker), #5499, #5530.

## Export evidence (generated programs vs the source launcher, both
architectures)

Programs re-exported from the same source at the revision this PR
targets; the exporter measures every generated program
against its source launcher on the same GPU (symmetric external
CUDA-graph timing, 3 counterbalanced groups, 20 warmup +
100 reportable calls per arm/group) and seals a row only when the
exported program is correct and within the timing gate.

| | B200 (`sm_100a`) | B300 (`sm_103a`) |
|---|---|---|
| Selected rows sealed | 120 / 120 | 118 / 120 |
| Unsealed rows | none | `bf16 center_6s_p1_m48768`, `bf16
pad_15s_p1_used109901_total109952`: the exporter's loaded-SM-clock
validity gate tripped (reportable clock 1290-1342 MHz, below 70 % of the
2032 MHz max, on an air-cooled B300 across three attempts). The BF16
program is byte-identical to the one merged in #5530, where both rows
sealed. |
| Generated-program patch | SHA-256 `7f1d2205fcf5…` (170673 B),
byte-identical from both architectures | same |
| Package tests | 625 passed | 625 passed |


## 🚀 Pull Request Checklist

- [x] I have read the
[CONTRIBUTING.md](https://github.com/flashinfer-ai/flashinfer/blob/main/CONTRIBUTING.md)
- [x] Pre-commit hooks run on the changed files (ruff, mypy,
clang-format opt-out per directory)
- [x] Tests:
`tests/experimental/test_cake_minimax_h3_varlen_attention.py` passes on
B200 and B300 (625 passed on each)

## 🧪 Tests

`pytest tests/experimental/test_cake_minimax_h3_varlen_attention.py` on
B200 (`sm_100a`) and B300 (`sm_103a`): 625 passed on each.
Benchmark: `benchmarks/bench_cake_minimax_h3_varlen_attention.py`.

## 🔬 Experimental Track

Same experimental package and API as #5499/#5530
(`flashinfer.experimental.minimax_h3_varlen_attention`); no public API
change.

## Reviewer Notes

The kernel change is one statement reorder inside the fp8-PV softmax
body of the generated programs (the free-buffer wait
moved behind the exp2/pack block); `cake_jit.py` carries the regenerated
`nvfp4_fp8pv` programs and `cake_backend.py` the
planner cost. Everything else is unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b7d82df](https://github.com/flashinfer-ai/flashinfer/commit/b7d82df5aecb830d4e2ee54bf8faacbcff28791d)

- **作者**: eigen
- **时间**: 2026-09-26T20:44:00Z
- **提交信息**: perf(cake_kda): faster fused M128 BF16 prefill body (checkpoint rows off the chain, packed gate scan), page64 phase fix (#5565)

Follow-up to #5543 (merged as 797872eac). The exported programs of the
`cake_kda_bf16` BF16 prefill family are regenerated from a new kernel
body on both architectures; the host runtime changes in one place (the
checkpoint panel descriptor is typed like the FP32 carrier rows). No
API, plan-cache or route-selection change.

### 1. Kernel body

Per 32-token chunk on the unbounded softplus gate with FP32 checkpoint
rows every 64 tokens (forced-sequential probe, one sequence, H16, slope
between 4096 / 8192 / 16384 tokens, cold-L2 CUPTI):

| body | B200 before | B200 after | GB300 before | GB300 after |
|---|---:|---:|---:|---:|
| unbounded softplus, FP32 rows | 3.95 us | 2.92 us (−26 %) | 3.58 us |
2.71 us (−24 %) |
| unbounded softplus, no rows | 2.87 us | 2.72 us | 2.67 us | 2.52 us |

- **Checkpoint rows leave the compute warps.** The FP32 rows were stored
from the compute warps' registers after the TMEM load and held the
release ordering of the following barriers until L2 acknowledged 64 KiB
per head per boundary. The rows are now written by the epilogue warps
from their own TMEM snapshot through an asynchronous path, off the
recurrence chain. Row cost 0.91 → 0.20 us per chunk (B200).
- **Straight-line softplus.** The three-regime gate scan is `selp` code
instead of branches (bitwise identical).
- **One restore tile per owner warp.** The 128-row FP32 state restore is
spread over the four prep warps of an instance instead of two.
- **Token-0 gate evaluated once**, and the 32-token scan runs on packed
`f32x2` pairs (RN, FTZ; row 0 and the last row stay scalar).
- **Page64 phase fix.** The two page cursors of the `page64_n32x2`
bodies (bounded gate, FP32 pool, checkpoint rows, ≤ 256-token sequences)
each flip their own software phase bits; the second cursor previously
relied on the first one's advance and deadlocked on its second ring wrap
(every sequence longer than 128 tokens on that route). The upstream
programs of that route were regenerated from the fixed body.
- **Rank-3 TMA reduce-add guard.** The arch guard around the rank-3
`cp.reduce.async.bulk.tensor` emitted `#error` in nvcc's host pass
(where `__CUDA_ARCH__` is undefined); every exported program that
accumulates FP32 rows through it failed to JIT. The guard now fires only
on a defined, too-old device pass; device code unchanged.

### 2. Host

`prepare_descriptors` types the checkpoint panel descriptor (rank 3)
like the FP32 carrier rows for every fused M128 program (888d03d).
Programs published before this change that carried the old rank-4 BF16
dummy and can still be selected were regenerated (staged-window slab
consumer; sequential body with BF16 rows on the FP32 pool).

### 3. Validation

- 359 export rows per architecture: output, final state and checkpoint
rows bitwise equal between the source dispatcher and the exported API
after identical resets; exported/source GPU-time median 0.999 (max 1.053
B200, 1.026 GB300).
- `tests/kda/test_kda_prefill_plan_cache.py`,
`tests/kda/test_bf16_one_wave_route.py`,
`tests/kda/test_tf32_prefill.py`: 71 passed on B200 and on GB300
(per-architecture trees) and 71 passed on the combined tree of this PR
(B200).
- compute-sanitizer synccheck + memcheck on the seven registered KDA
launchers of the source tree: 0 errors on both architectures.
- rel L2 vs the Triton reference (out / state) unchanged on all 56 bench
rows.

### Speedup vs Triton (bench_tb, same GPU, same inputs, FP32 state, rows
every 64)

Same harness as #5452 / #5543 (serving-adapter layer call of the
prepared export vs the Triton `chunk_kda` path, fresh identically seeded
inputs per arm, FP32 state pool, checkpoint rows every 64 tokens; GPU
time = profiler CUDA time, event time = CUDA events around the call; one
lane per GPU). GPU time: every one of the 56 rows beats Triton on both
architectures and none is slower than #5543 beyond measurement noise
(three bounded composite rows are within +0.2 %; all other rows are 1–27
% faster). CUDA-event time: 56/56 rows > 1 on B200 in three runs; on
GB300 the 32 layer rows are all > 1 and the T64 wrapper rows (13–40 us
of GPU time behind 0.22–0.31 ms of host time) carry event times above
the #5543 recording while Triton's event time in the same runs did not
move — the v8 FlashInfer tree re-measured on the same GB300 node shows
the same shift on every row at identical GPU time (event +20–40 %, e.g.
k3 H12 8192 GPU 0.2551 vs 0.2561 ms, event 0.652 vs 0.510), so the
deficit is host time on the measuring node, not the new programs. A
paired A B A B of the four wrapper lanes (this branch vs the #5543 tree,
same node) has this branch at or below the #5543 tree on GPU time in
every arm; its event ratio vs Triton is ≥ 1 in 6 of 8 measurements (8 of
8 for the #5543 tree), and the two misses are single-arm 0.32–0.34 ms
host outliers that the repeat arm does not reproduce (0.250–0.259 ms,
below both #5543 arms at 0.275–0.308 ms). The T64 wrapper rows are 13–40
us of GPU work; their event time is the host path, unchanged by this PR.


**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5543 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2536 | 2.36x | 0.4611 | 1.58x | 2.17x → 2.36x | 0.0052/0.0036
|
| 16384 | 0.4122 | 2.76x | 0.6896 | 1.83x | 2.48x → 2.76x |
0.0052/0.0041 |
| 2x8192 | 0.4617 | 1.81x | 0.7037 | 1.38x | 1.81x → 1.81x |
0.0052/0.0042 |
| 3000+13384 | 0.4354 | 2.37x | 0.6995 | 1.66x | 2.14x → 2.37x |
0.0052/0.0041 |
| 4x4096 | 0.2413 | 2.88x | 0.4834 | 1.70x | 2.86x → 2.88x |
0.0052/0.0039 |
| 2x(8128+64) | 0.4586 | 1.82x | 0.6967 | 1.38x | 1.83x → 1.82x |
0.0052/0.0042 |
| 8x(1024+64) | 0.1195 | 3.10x | 0.3102 | 1.66x | 3.03x → 3.10x |
0.0041/0.0017 |
| 32768 | 0.7170 | 3.12x | 1.1147 | 2.12x | 2.78x → 3.12x |
0.0052/0.0043 |

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5543 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.3095 | 2.06x | 0.5470 | 1.42x | 1.89x → 2.06x | 0.0052/0.0038
|
| 16384 | 0.5113 | 2.44x | 0.8425 | 1.63x | 2.19x → 2.44x |
0.0052/0.0040 |
| 2x8192 | 0.4630 | 2.05x | 0.7602 | 1.42x | 2.04x → 2.05x |
0.0052/0.0039 |
| 3000+13384 | 0.5247 | 2.18x | 0.8550 | 1.50x | 1.96x → 2.18x |
0.0052/0.0038 |
| 4x4096 | 0.2438 | 3.32x | 0.5364 | 1.76x | 3.30x → 3.32x |
0.0052/0.0040 |
| 2x(8128+64) | 0.4611 | 2.07x | 0.7582 | 1.44x | 2.07x → 2.07x |
0.0052/0.0039 |
| 8x(1024+64) | 0.0991 | 4.47x | 0.3192 | 1.86x | 3.99x → 4.47x |
0.0052/0.0040 |
| 32768 | 0.9158 | 2.64x | 1.4227 | 1.81x | 2.35x → 2.64x |
0.0052/0.0041 |

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5543 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0142 | 3.78x | 0.1576 | 1.64x | 3.64x → 3.78x |
0.0053/0.0039 |
| BS16 x T64 | 0.0336 | 2.36x | 0.1722 | 1.69x | 2.30x → 2.36x |
0.0040/0.0017 |
| BS64 x T64 | 0.1000 | 2.05x | 0.2689 | 1.54x | 2.06x → 2.05x |
0.0040/0.0017 |
| BS16 x T128 | 0.0439 | 2.56x | 0.1882 | 2.02x | 2.58x → 2.56x |
0.0053/0.0040 |
| BS16 x T256 | 0.0624 | 2.96x | 0.2159 | 1.88x | 2.76x → 2.96x |
0.0052/0.0039 |
| BS16 x T(17..255) | 0.0355 | 3.21x | 0.1804 | 2.14x | 3.20x → 3.21x |
0.0052/0.0040 |

**B200 (SM100, 148 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5543 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0146 | 3.71x | 0.1564 | 1.64x | 3.56x → 3.71x |
0.0053/0.0040 |
| BS16 x T64 | 0.0318 | 2.71x | 0.1699 | 1.68x | 2.63x → 2.71x |
0.0053/0.0040 |
| BS64 x T64 | 0.1135 | 2.16x | 0.2883 | 1.45x | 2.15x → 2.16x |
0.0052/0.0040 |
| BS16 x T128 | 0.0460 | 2.86x | 0.1878 | 1.97x | 2.78x → 2.86x |
0.0052/0.0040 |
| BS16 x T256 | 0.0651 | 3.39x | 0.2287 | 1.74x | 3.12x → 3.39x |
0.0052/0.0040 |
| BS16 x T(17..255) | 0.0462 | 2.88x | 0.1908 | 1.96x | 2.66x → 2.88x |
0.0052/0.0040 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5543
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.3503 | 1.73x | 0.4999 | 1.46x | 1.56x → 1.73x | 0.0040/0.0022
|
| 16384 | 0.6075 | 1.88x | 0.7581 | 1.67x | 1.70x → 1.88x |
0.0040/0.0019 |
| 2x8192 | 0.6149 | 1.38x | 0.7548 | 1.28x | 1.26x → 1.38x |
0.0040/0.0019 |
| 3000+13384 | 0.6599 | 1.57x | 0.8056 | 1.44x | 1.43x → 1.57x |
0.0040/0.0024 |
| 4x4096 | 0.3993 | 1.76x | 0.5273 | 1.56x | 1.28x → 1.76x |
0.0040/0.0020 |
| 2x(8128+64) | 0.6223 | 1.36x | 0.7763 | 1.25x | 1.24x → 1.36x |
0.0040/0.0020 |
| 8x(1024+64) | 0.1453 | 2.60x | 0.2704 | 1.90x | 2.28x → 2.60x |
0.0039/0.0020 |
| 32768 | 1.1024 | 2.05x | 1.2396 | 1.93x | 1.84x → 2.05x |
0.0040/0.0021 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5543
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.4388 | 1.48x | 0.5868 | 1.31x | 1.32x → 1.48x | 0.0040/0.0020
|
| 16384 | 0.7726 | 1.63x | 0.9251 | 1.50x | 1.48x → 1.63x |
0.0040/0.0021 |
| 2x8192 | 0.8239 | 1.17x | 0.9644 | 1.14x | 1.05x → 1.17x |
0.0040/0.0021 |
| 3000+13384 | 0.7960 | 1.46x | 0.9368 | 1.38x | 1.33x → 1.46x |
0.0040/0.0025 |
| 4x4096 | 0.4090 | 2.01x | 0.5338 | 1.77x | 1.45x → 2.01x |
0.0040/0.0022 |
| 2x(8128+64) | 0.8175 | 1.19x | 0.9705 | 1.13x | 1.04x → 1.19x |
0.0040/0.0021 |
| 8x(1024+64) | 0.1505 | 3.00x | 0.2751 | 2.12x | 2.68x → 3.00x |
0.0040/0.0021 |
| 32768 | 1.4177 | 1.73x | 1.5631 | 1.66x | 1.57x → 1.73x |
0.0040/0.0021 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5543 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0226 | 2.40x | 0.1665 | 1.49x | 2.23x → 2.40x |
0.0040/0.0021 |
| BS16 x T64 | 0.0413 | 1.97x | 0.1728 | 1.61x | 1.86x → 1.97x |
0.0039/0.0020 |
| BS64 x T64 | 0.1210 | 1.75x | 0.2562 | 1.63x | 1.66x → 1.75x |
0.0039/0.0020 |
| BS16 x T128 | 0.0550 | 2.11x | 0.1845 | 2.09x | 1.97x → 2.11x |
0.0040/0.0021 |
| BS16 x T256 | 0.0837 | 2.28x | 0.2113 | 1.87x | 1.99x → 2.28x |
0.0039/0.0020 |
| BS16 x T(17..255) | 0.0459 | 2.56x | 0.1718 | 2.27x | 2.31x → 2.56x |
0.0040/0.0023 |

**B200 (SM100, 148 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5543 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0227 | 2.39x | 0.1589 | 1.56x | 2.23x → 2.39x |
0.0040/0.0021 |
| BS16 x T64 | 0.0421 | 2.12x | 0.1664 | 1.65x | 1.99x → 2.12x |
0.0040/0.0020 |
| BS64 x T64 | 0.1469 | 1.73x | 0.2746 | 1.54x | 1.65x → 1.73x |
0.0040/0.0021 |
| BS16 x T128 | 0.0565 | 2.40x | 0.1818 | 2.06x | 2.23x → 2.40x |
0.0039/0.0021 |
| BS16 x T256 | 0.0870 | 2.65x | 0.2118 | 1.87x | 2.30x → 2.65x |
0.0040/0.0021 |
| BS16 x T(17..255) | 0.0602 | 2.29x | 0.1839 | 2.01x | 2.08x → 2.29x |
0.0039/0.0023 |

B200 (SM100, 148 SMs): 56/56 rows > 1 on both metrics; GPU time at or
below #5543 on 55/56 rows.


**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5543 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2359 | 2.37x | 0.5339 | 1.35x | 2.19x → 2.37x | 0.0052/0.0041
|
| 16384 | 0.3841 | 2.76x | 0.7531 | 1.66x | 2.48x → 2.76x |
0.0052/0.0037 |
| 2x8192 | 0.3829 | 2.02x | 0.7480 | 1.30x | 1.82x → 2.02x |
0.0052/0.0039 |
| 3000+13384 | 0.4065 | 2.35x | 0.7601 | 1.51x | 2.12x → 2.35x |
0.0052/0.0039 |
| 4x4096 | 0.2255 | 2.82x | 0.5134 | 1.60x | 2.82x → 2.82x |
0.0052/0.0039 |
| 2x(8128+64) | 0.3852 | 2.00x | 0.7422 | 1.29x | 1.81x → 2.00x |
0.0052/0.0039 |
| 8x(1024+64) | 0.1095 | 3.08x | 0.3739 | 1.44x | 3.06x → 3.08x |
0.0040/0.0016 |
| 32768 | 0.6724 | 3.10x | 1.1531 | 1.96x | 2.77x → 3.10x |
0.0052/0.0034 |

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5543 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.2863 | 2.13x | 0.6454 | 1.19x | 1.95x → 2.13x | 0.0052/0.0040
|
| 16384 | 0.4767 | 2.49x | 0.8804 | 1.58x | 2.24x → 2.49x |
0.0052/0.0040 |
| 2x8192 | 0.4366 | 2.06x | 0.7800 | 1.40x | 2.06x → 2.06x |
0.0052/0.0041 |
| 3000+13384 | 0.4866 | 2.23x | 0.8842 | 1.45x | 2.00x → 2.23x |
0.0052/0.0038 |
| 4x4096 | 0.2266 | 3.37x | 0.5621 | 1.69x | 3.38x → 3.37x |
0.0052/0.0040 |
| 2x(8128+64) | 0.4348 | 2.08x | 0.7682 | 1.42x | 2.08x → 2.08x |
0.0052/0.0040 |
| 8x(1024+64) | 0.0884 | 4.72x | 0.3832 | 1.60x | 4.51x → 4.72x |
0.0052/0.0040 |
| 32768 | 0.8540 | 2.71x | 1.4095 | 1.77x | 2.41x → 2.71x |
0.0052/0.0042 |

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H12, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5543 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0130 | 3.85x | 0.2573 | 1.31x | 3.81x → 3.85x |
0.0053/0.0040 |
| BS16 x T64 | 0.0307 | 2.40x | 0.2621 | 1.48x | 2.38x → 2.40x |
0.0041/0.0017 |
| BS64 x T64 | 0.0912 | 2.10x | 0.3263 | 1.59x | 2.05x → 2.10x |
0.0041/0.0017 |
| BS16 x T128 | 0.0395 | 2.68x | 0.2770 | 1.81x | 2.64x → 2.68x |
0.0053/0.0040 |
| BS16 x T256 | 0.0573 | 2.98x | 0.2830 | 1.72x | 2.74x → 2.98x |
0.0052/0.0040 |
| BS16 x T(17..255) | 0.0318 | 3.36x | 0.2571 | 1.88x | 3.29x → 3.36x |
0.0052/0.0041 |

**GB300 (SM103, 152 SMs), one lane per GPU — K3 shape, bounded lb=-5,
H16, wrapper** (prepared ms; speedup = Triton ÷ prepared; #5543 column =
the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0132 | 3.95x | 0.3031 | 0.97x | 3.94x → 3.95x |
0.0053/0.0040 |
| BS16 x T64 | 0.0291 | 2.53x | 0.2802 | 1.50x | 2.56x → 2.53x |
0.0053/0.0040 |
| BS64 x T64 | 0.1036 | 2.22x | 0.3693 | 1.43x | 2.24x → 2.22x |
0.0052/0.0040 |
| BS16 x T128 | 0.0410 | 3.01x | 0.2718 | 1.78x | 2.97x → 3.01x |
0.0052/0.0040 |
| BS16 x T256 | 0.0592 | 3.52x | 0.2925 | 1.63x | 3.30x → 3.52x |
0.0052/0.0039 |
| BS16 x T(17..255) | 0.0419 | 2.95x | 0.2683 | 1.82x | 2.87x → 2.95x |
0.0052/0.0040 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, layer** (prepared ms; speedup = Triton ÷ prepared; #5543
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.3236 | 1.75x | 0.5524 | 1.30x | 1.61x → 1.75x | 0.0040/0.0020
|
| 16384 | 0.5579 | 1.92x | 0.7791 | 1.60x | 1.74x → 1.92x |
0.0040/0.0020 |
| 2x8192 | 0.5617 | 1.39x | 0.7748 | 1.23x | 1.28x → 1.39x |
0.0040/0.0019 |
| 3000+13384 | 0.6004 | 1.61x | 0.8143 | 1.42x | 1.47x → 1.61x |
0.0040/0.0024 |
| 4x4096 | 0.3708 | 1.74x | 0.5655 | 1.46x | 1.32x → 1.74x |
0.0040/0.0021 |
| 2x(8128+64) | 0.5792 | 1.35x | 0.7925 | 1.22x | 1.25x → 1.35x |
0.0040/0.0020 |
| 8x(1024+64) | 0.1311 | 2.62x | 0.3233 | 1.67x | 2.31x → 2.62x |
0.0040/0.0020 |
| 32768 | 1.0174 | 2.07x | 1.2334 | 1.84x | 1.90x → 2.07x |
0.0040/0.0022 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, layer** (prepared ms; speedup = Triton ÷ prepared; #5543
column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| 8192 | 0.4062 | 1.52x | 0.7060 | 1.09x | 1.39x → 1.52x | 0.0040/0.0021
|
| 16384 | 0.7051 | 1.71x | 0.9348 | 1.49x | 1.55x → 1.71x |
0.0040/0.0020 |
| 2x8192 | 0.7491 | 1.22x | 0.9715 | 1.13x | 1.11x → 1.22x |
0.0040/0.0021 |
| 3000+13384 | 0.7182 | 1.53x | 0.9367 | 1.36x | 1.40x → 1.53x |
0.0039/0.0022 |
| 4x4096 | 0.3818 | 2.03x | 0.5841 | 1.63x | 1.54x → 2.03x |
0.0040/0.0021 |
| 2x(8128+64) | 0.7668 | 1.20x | 0.9845 | 1.11x | 1.10x → 1.20x |
0.0040/0.0021 |
| 8x(1024+64) | 0.1340 | 3.17x | 0.3327 | 1.86x | 2.81x → 3.17x |
0.0040/0.0021 |
| 32768 | 1.2861 | 1.82x | 1.5120 | 1.66x | 1.65x → 1.82x |
0.0040/0.0023 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H12, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5543 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0207 | 2.44x | 0.2579 | 1.17x | 2.36x → 2.44x |
0.0039/0.0020 |
| BS16 x T64 | 0.0376 | 1.96x | 0.2357 | 1.65x | 1.91x → 1.96x |
0.0040/0.0020 |
| BS64 x T64 | 0.1102 | 1.71x | 0.3226 | 1.58x | 1.68x → 1.71x |
0.0039/0.0020 |
| BS16 x T128 | 0.0496 | 2.11x | 0.2858 | 2.41x | 2.02x → 2.11x |
0.0040/0.0021 |
| BS16 x T256 | 0.0760 | 2.28x | 0.2853 | 1.99x | 2.04x → 2.28x |
0.0039/0.0020 |
| BS16 x T(17..255) | 0.0414 | 2.59x | 0.2458 | 2.08x | 2.39x → 2.59x |
0.0040/0.0023 |

**GB300 (SM103, 152 SMs), one lane per GPU — Kimi-Linear shape,
unbounded, H16, wrapper** (prepared ms; speedup = Triton ÷ prepared;
#5543 column = the previous export on the same harness)

| case | GPU prepared | GPU x | event prepared | event x | GPU x #5543 →
this PR | out / state relL2 |
|---|---:|---:|---:|---:|---:|---|
| BS4 x T64 | 0.0208 | 2.52x | 0.3113 | 0.96x | 2.46x → 2.52x |
0.0040/0.0021 |
| BS16 x T64 | 0.0382 | 2.01x | 0.2456 | 1.70x | 1.90x → 2.01x |
0.0040/0.0020 |
| BS64 x T64 | 0.1339 | 1.77x | 0.3392 | 1.56x | 1.67x → 1.77x |
0.0039/0.0021 |
| BS16 x T128 | 0.0508 | 2.50x | 0.2489 | 1.95x | 2.31x → 2.50x |
0.0040/0.0020 |
| BS16 x T256 | 0.0780 | 2.77x | 0.2718 | 1.75x | 2.36x → 2.77x |
0.0040/0.0021 |
| BS16 x T(17..255) | 0.0540 | 2.38x | 0.2461 | 1.96x | 2.16x → 2.38x |
0.0040/0.0022 |

GB300 (SM103, 152 SMs): 54/56 rows > 1 on both metrics; GPU time at or
below #5543 on 54/56 rows.


### Baselines and their source PRs

- **Triton reference**: SGLang's `chunk_kda` FLA path at the pinned
SGLang checkout 24c9251ac52ada1660f372922c72c1d3af722247 (same pin as
#5452 / #5543), invoked as in `tests/kda` (sigmoid of logit beta on the
host, FP32 pool with state indices, intermediate states on).
- **Previous exported programs**: #5543 (797872eac, 2026-09-25); earlier
#5452 (71f724405) and #5440 (d3af75ac7). Files:
`csrc/kda/bf16/cake_kda_bf16_*_{kernel,binding}.cu`,
`flashinfer/jit/cake_kda_tf32.py`,
`flashinfer/cake_kda_tf32_runtime.py`, `flashinfer/kda_prefill.py`,
`tests/kda/`.
- Branch merge-base with `main`: 797872eac. Upstream `main` has since
gained #5551 (37a53f374), which touches only
`csrc/kda/cake_fused_kda_decode_*` and
`tests/kda/test_cake_fused_kda_decode_*`; `git log
797872eac..upstream/main -- csrc/kda/bf16
flashinfer/jit/cake_kda_tf32.py flashinfer/cake_kda_tf32_runtime.py
flashinfer/kda_prefill.py tests/kda/test_kda_prefill_plan_cache.py
tests/kda/test_bf16_one_wave_route.py tests/kda/test_tf32_prefill.py` is
empty (checked at 289ac7803).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for saving intermediate KDA state checkpoints at chunk
boundaries, including when using FP32 checkpoint storage.
* Added descriptor preparation and prepared-run options for compatible
BF16 KDA kernels.
* **Improvements**
* Expanded checkpoint tensor layout support to cover tensors with two or
more dimensions.
* Improved handling of sequence-end boundaries during gate calculations
and checkpoint writes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [78c6e1f](https://github.com/flashinfer-ai/flashinfer/commit/78c6e1fbfcb65043cdee92506c077259e7e878b7)

- **作者**: eigen
- **时间**: 2026-09-26T07:05:27Z
- **提交信息**: perf(cake_backend): warp-per-row selection arm for the largest Kimi-K3 fused router batches (SM100/SM103) (#5564)

## Kimi-K3 fused MoE router: warp-per-row two-join arm for the largest
batches (SM100 / SM103)

Follow-up to #5531 / #5548 (same source family; one new dispatch arm).
Same K3 semantics (sigmoid gate, top-16 on `sigmoid(logit) + bias`,
renormalized unbiased weights, lower expert id on ties) and the same
expert-aligned route plan for `block_m` 8/16; the public entries
`flashinfer.fused_moe.kimi_k3_fused_router` /
`prepare_kimi_k3_fused_router` are unchanged.

### What changed
The four largest routed shapes (`num_tokens` 4096 and 8192 x `block_m`
8/16) move from the previous two-join arm (`G`: thread-per-expert
selection, four CTAs per SM on CC 10.0 and six on CC 10.3) to a new arm
`GW`:

- **Warp-per-row selection.** Each warp owns one token row and selects
its 16 experts with a packed-key radix pass over the 896 biased scores
(key = biased score bits | expert id, so ties resolve to the lower
expert id exactly as before), instead of the thread-per-expert selection
of arm `G`.
- **Dual-expert sort phase.** With four CTAs per SM the segment-sort
phase hands two of the 896 expert segments to about half of the CTAs;
arm `GW` processes a CTA's two segments together through two
shared-memory pools (clear, scatter, prefix and gather of both segments
between the same barriers), so the phase costs one latency round instead
of two. The per-segment ordering is unchanged.
- **Launch bounds** `__launch_bounds__(224, 4)` on both architectures;
persistent grid `min(num_tokens, 4 x SM count)` (`ARM_GW_CTAS_PER_SM`),
so the CC 10.3 grid for these rows changes from six to four CTAs per SM.

`cake_backend.py`: route table `G -> GW` for the four shapes,
`ARM_G_CTAS_PER_SM -> ARM_GW_CTAS_PER_SM = {(10, 0): 4, (10, 3): 4}`,
`launch_grid("GW", ...)`. `cake_jit.py` MODULES: the four `G` records
are replaced by four `GW` records per arch
(`cake_kimi_k3_fused_router_gw_bm{8,16}_sm_10{0,3}a`); the 24 other
programs per arch are byte-identical to #5548 (their generated sources
and module names are unchanged). Tests: the route-table and launch-grid
assertions follow the new arm.

Source-side paired cold-L2 CUPTI A/B against the #5548 programs (same
session, same node; `previous / new` kernel time): B200 `m4096_bm8`
**1.230**, `m4096_bm16` **1.206**, `m8192_bm8` **1.319**, `m8192_bm16`
**1.312** (geomean 1.266); GB300 **1.144** / **1.145** / **1.179** /
**1.186** (geomean 1.163). Rows of the other arms are unchanged code
(same-session interleaved controls on the 24 unchanged rows,
previous/new kernel time on byte-identical binaries: B200 mid rows
geomean 1.004, GB300 mid rows 1.000 and small rows 1.005 / 0.994 over
two runs; B200 small rows 0.994; per-row spread is within the +-3-7 %
cohort noise of these 5-20 us kernels).

### Exactness
Source-side gates on both arches: exact43 43/43, affected slice +
registered e2e, compute-sanitizer synccheck and racecheck (separate
runs): all green on both architectures (sanitizers on the 8 frozen
shapes plus the four large rows). Export receipts (source <-> export
bitwise parity on all 28 shapes per arch, generated grid == source
grid): B200 (sm_100a) 28/28 rows correct, source/export time ratio
`0.95-1.04`; GB300 (sm_103a) 28/28 rows correct, ratio `0.97-1.02`.
`tests/experimental/test_cake_kimi_k3_fused_router.py`: B200 `44/44`
passed, GB300 `44/44` passed.

### Benchmark
`benchmarks/bench_cake_kimi_k3_fused_router.py --cupti --rounds 5`
(interleaved A/B rounds, CUPTI kernel time with a cold L2) against
SGLang `route_radix` + `moe_align_block_size` (pinned SGLang revision
83bd2c47, kernel-only):

| row | arm (B200 / GB300) | B200 fused us | B200 SGLang us | B200
speedup | GB300 fused us | GB300 SGLang us | GB300 speedup |
|---|---|---:|---:|---:|---:|---:|---:|
| m1_bm8 | L / L | 5.79 | 9.44 | **1.630** | 5.89 | 13.34 | **2.266** |
| m2_bm8 | LC / LC | 5.44 | 9.70 | **1.782** | 5.44 | 13.02 | **2.394**
|
| m4_bm8 | LC / LC | 5.92 | 9.66 | **1.633** | 5.70 | 13.02 | **2.287**
|
| m8_bm8 | LC / LC | 5.89 | 9.76 | **1.658** | 5.79 | 12.64 | **2.182**
|
| m16_bm8 | L / L | 6.14 | 9.76 | **1.589** | 6.18 | 13.41 | **2.171** |
| m32_bm8 | L / L | 6.27 | 9.89 | **1.577** | 6.14 | 13.25 | **2.156** |
| m64_bm8 | L / L | 7.04 | 10.14 | **1.441** | 6.91 | 13.57 | **1.963**
|
| m128_bm8 | L / L | 8.03 | 10.50 | **1.307** | 7.65 | 13.60 | **1.778**
|
| m256_bm8 | M / M | 8.51 | 10.98 | **1.289** | 8.13 | 14.56 | **1.791**
|
| m512_bm8 | Q4S / Q4S | 10.53 | 13.09 | **1.243** | 10.21 | 15.78 |
**1.545** |
| m1024_bm8 | Q4S / Q4S | 14.34 | 18.59 | **1.297** | 13.79 | 18.98 |
**1.376** |
| m2048_bm8 | Q4S / Q4S | 20.99 | 28.64 | **1.364** | 20.00 | 27.30 |
**1.365** |
| m4096_bm8 | GW / GW | 30.91 | 48.19 | **1.559** | 29.25 | 46.08 |
**1.575** |
| m8192_bm8 | GW / GW | 47.17 | 88.54 | **1.877** | 45.02 | 83.74 |
**1.860** |
| m1_bm16 | L / L | 6.46 | 9.76 | **1.510** | 6.05 | 13.18 | **2.180** |
| m2_bm16 | LC / LC | 5.95 | 9.60 | **1.613** | 5.73 | 13.25 | **2.313**
|
| m4_bm16 | LC / LC | 5.57 | 9.79 | **1.759** | 5.57 | 13.25 | **2.379**
|
| m8_bm16 | LC / LC | 5.70 | 10.05 | **1.764** | 5.86 | 13.54 |
**2.311** |
| m16_bm16 | L / L | 6.02 | 10.11 | **1.681** | 5.98 | 13.34 | **2.230**
|
| m32_bm16 | L / L | 6.43 | 9.89 | **1.537** | 6.14 | 13.76 | **2.240**
|
| m64_bm16 | L / L | 7.14 | 10.05 | **1.408** | 6.91 | 13.54 | **1.958**
|
| m128_bm16 | L / L | 8.19 | 10.30 | **1.258** | 7.87 | 13.89 |
**1.764** |
| m256_bm16 | M / M | 8.32 | 11.10 | **1.335** | 8.29 | 14.34 |
**1.730** |
| m512_bm16 | Q4S / Q4S | 10.50 | 12.80 | **1.220** | 10.05 | 15.87 |
**1.580** |
| m1024_bm16 | Q4S / Q4S | 14.02 | 18.02 | **1.285** | 13.66 | 19.23 |
**1.407** |
| m2048_bm16 | Q4S / Q4S | 20.99 | 27.04 | **1.288** | 19.94 | 26.30 |
**1.319** |
| m4096_bm16 | GW / GW | 31.26 | 45.70 | **1.462** | 30.05 | 44.26 |
**1.473** |
| m8192_bm16 | GW / GW | 47.61 | 83.01 | **1.743** | 44.80 | 79.46 |
**1.774** |

Geomean speedup vs SGLang: **NVIDIA B200 1.492** (min `1.220`, `28`/28
rows > 1.0), **NVIDIA GB300 1.873** (min `1.319`, `28`/28 rows > 1.0).
#5548 on the same benchmark: B200 1.447 (min 1.211), GB300 1.837 (min
1.287).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved large-batch routing across supported GPU architectures by
optimizing token selection and processing pairs of experts in parallel.
* Standardized the large-batch launch limit to four blocks per SM on
both supported architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f7f1577](https://github.com/flashinfer-ai/flashinfer/commit/f7f1577aee02422630da7ad2a0226551437ed2b0)

- **作者**: eigen
- **时间**: 2026-09-26T07:03:24Z
- **提交信息**: perf(cake_minimax_h3): K/V-split the partial-wave units of the packed-varlen attention (SM100/SM103) (#5530)

<!-- .github/pull_request_template.md -->

## 📌 Description

Second performance round of the experimental **MiniMax-H3 packed-varlen
attention** (#4532 candidates 3A/3C, SM100/SM103),
on top of the merged first delivery (#5499).

**Problem.** The short packed rows (Ulysses P=8 / P=4, 4k-14k tokens)
ran at 57-85 % of the large-row throughput. The
cause is wave quantization of the persistent grid, not tail padding:
`cu_seqlens=[0, 6096]` x 7 heads is `U = 84`
equal-cost units on `G = 74` clusters (1.14 waves), so the kernel takes
two full unit times.

**Change.** Both program families split the units of a partial wave over
their K/V range (flash-decoding style) and merge
the partials with a small `combine` stage:

* Host planner `choose_kv_splits` (shared by `build_bf16_segment_plan`
and `build_tile_tables`): for plans below four
waves, simulate the longest-processing-time-first slot assignment for
splitting the `U mod G` most expensive units
(fallback: every unit) `k = 2..8` ways into near-equal K/V block ranges,
add a combine cost, and keep the best
candidate only above a 3 % predicted gain (2-6 ms per new `cu_seqlens`).
* The BF16 `unit_table` carries four int32 per slot (segment, `head <<
16 | cluster`, `kv_block_begin << 16 | kv_blocks`,
partial slot or -1); the NVFP4 tile tables gain `cl_kv_begin` /
`cl_kv_blocks` / `cl_ws_slot` and are now placed LPT
like the BF16 plan. Unsplit units are bitwise identical to the previous
kernels.
* Split units write rows normalized by their own softmax sum as FP16
plus FP32 `(scaled log2 max, sum)` into a per-plan
partial workspace (`512 x 128` FP16 + `512 x 2` FP32 per slot, owned by
the plan / tile tables, allocation-free at
launch); the generated `combine` kernel (one warp per output row, 128
CTAs per split unit, all split loads of a row in
flight) applies the exact merge `O = sum_i 2^(m_i - m) l_i O_i / sum_i
2^(m_i - m) l_i` in FP32 with one BF16
rounding. The runners launch it after the attention kernel only when a
plan has split units (ordinary serial launch on
the same stream; the quantizer -> attention PDL handshake is unchanged).
* The NVFP4 routes register two attention programs per architecture,
traced from one kernel body: the dense program
(the merged kernel with its 17-parameter signature: no K/V-split code
and no split parameters) for plans without split
units and the split program (six more parameters: K/V range, partial
slots, partial workspace, unit count) for plans
with partial slots. The runner binds exactly one at preparation with
that program's own parameter set
(`runner.attention_stage`, `route_metadata["attention_variant"]`,
`NVFP4_ATTENTION_*_KWARGS` vs
`NVFP4_ATTENTION_SPLIT_*_KWARGS`); stage lists are `(quantize,
attention, attention_split, combine)`. Keeping the
  dense program free of the split epilogue keeps the
softmax block loop of unsplit units at the schedule of the merged
kernel: with the split epilogue present, ptxas
reschedules the loop's exp2/pack region (MUFU clustering, +32 %
`mio_throttle` stalls) and every long unsplit
fp4pv/fp8pv row measured 1-2 % slower, and a dense program that differed
from the merged kernel only in the
constant-bank layout of six extra parameters still measured 0.982-0.993x
on the 55-75 us `U < G` fp4pv rows. The dense
programs are SASS-identical to the merged kernels (register-normalized,
constant bank included).
The split program runs at a measured per-unit cost relative to the dense
program (`SPLIT_PROGRAM_COST[(pv_mode, arch)]`:
sm_103a fp8pv 1.21x, whose softmax block loop is rescheduled at its
register budget; sm_100a fp4pv 1.03x; parity
otherwise), and the planner scales a split plan's makespan by it, so a
row splits only when the wave-quantization gain
exceeds the program cost (sm_103a fp8pv splits its 1.14-wave rows, not
its 3.2-wave rows).
* Public API, semantics and tolerances are unchanged. `route_metadata`
reports `kv_split_units` / `max_kv_splits` /
  `attention_variant`.

**Paired result** (same node, old kernels vs this PR, complete call
incl. quantize + combine for NVFP4):

| Row (`cu_seqlens` x heads) | Units / waves | BF16 B200 | BF16 B300 |
NVFP4 fp4 B200 | NVFP4 fp4 B300 |
|---|---|---:|---:|---:|---:|
| [0, 6096] x 7 | 84 / 1.14 | 0.1585 -> 0.1105 ms (**1.43x**) | 0.1277
-> 0.0872 (**1.46x**) | 0.1524 -> 0.1062 (**1.44x**) | 0.1129 -> 0.0830
(**1.36x**) |
| [0, 7368] x 7 | 105 / 1.42 | 1.21x | 1.21x | 1.21x | 1.16x |
| [0, 8368] x 14 | 238 / 3.2 | 1.16x | 1.15x | 1.17x | 1.14x |
| [0, 13744] x 7 | 189 / 2.55 | 1.08x | 1.07x | 1.09x | 1.05x |
| [0, 9648] x 14 | 266 / 3.6 | 1.05x | 1.03x | 1.05x | 1.02x |
| [0, 4184] x 7 (U < G) | 63 / 0.85 | 1.00x | 1.00x | 0.99x | 0.97x |
| [0, 33472] x 56 | 3696 / 50 | 1.00x | 1.00x | 1.00x | 0.99x |

Against FlashInfer's fastest BF16 ragged prefill route the [0, 6096] x 7
row goes from 1.26x to 1.85x (BF16) /
1.97x (NVFP4 fp4) on B200 and to 1.85x / 1.94x on B300. Rows with `U <
G` cannot gain from a K/V split (the kernel
already finishes in one unit time).

## Paired evidence on this delivery (same node, old kernels vs this PR,
complete call)

A 44-row arm of the contract harness runs longer than two hours per
kernel (the FP32 oracle of the 110k-token rows dominates), so the
same-node pairs are bounded to two row sets per family and architecture,
run as one step each (old arm, then new arm, on one GPU):

* **large unsplit rows** (dense program; representative of every row at
or above four waves): `[0, 33472] x 56`,
`[0, 24384] x 28`, and the four-segment `[0, 6096, 12192, 18288, 24384]
x 28`;
* **split-affected rows** (every P=8 / P=4 center row, the P=4 / P=8
tail rows, the padded P=4 row, the three-segment P=8 row and
  the four smoke rows).

Every row is measured with five interleaved candidate/baseline groups
(CUPTI, cold L2) at a 150 ms budget per arm; the
old kernels are the merged #5499 programs, the new kernels this PR's
programs; all 22 rows pass correctness in every arm
(the four `smoke_*` rows are correctness-only). Ratios are old / new
(above 1 = this PR is faster). The B300 fp8pv column
was measured at the final programs; the other five columns at the first
export of this PR, whose split programs are
identical to the final ones and whose dense programs differ only by the
fold verified in the four-arm table below.

**Split-affected and partial-wave rows (S1, 18 timed rows)** (old kernel
ms -> this PR ms, ratio; same node, one old arm then one new arm per
step)

| Row | units / waves | bf16 B200 | fp4 B200 | fp8 B200 | bf16 B300 |
fp4 B300 | fp8 B300 |
|---|---|---:|---:|---:|---:|---:|---:|
| center_10s_p4_m18560 | 518 / 7.0 | 1.7910 -> 1.7887 1.001x | 1.4763 ->
1.4599 1.011x | 1.5357 -> 1.5462 0.993x | 1.5443 -> 1.5441 1.000x |
1.0790 -> 1.0832 0.996x | 1.1263 -> 1.1291 0.998x |
| center_10s_p8_m9280 | 133 / 1.80 | 0.2395 -> 0.2391 1.002x | 0.2197 ->
0.2182 1.007x | 0.2341 -> 0.2353 0.995x | 0.1968 -> 0.1967 1.001x |
0.1585 -> 0.1595 0.994x | 0.1741 -> 0.1746 0.997x |
| center_15s_p4_m27488 | 756 / 10.2 | 4.0772 -> 4.0287 1.012x | 3.3221
-> 3.2816 1.012x | 3.4396 -> 3.4592 0.994x | 3.4689 -> 3.4664 1.001x |
2.4122 -> 2.4175 0.998x | 2.4937 -> 2.4960 0.999x |
| center_15s_p8_m13744 | 189 / 2.55 | 0.5313 -> 0.4970 **1.069x** |
0.4579 -> 0.4223 **1.084x** | 0.4674 -> 0.4351 **1.074x** | 0.4354 ->
0.4045 **1.076x** | 0.3235 -> 0.3041 **1.064x** | 0.3438 -> 0.3444
0.998x |
| center_4s_p4_m8368 | 238 / 3.2 | 0.4302 -> 0.3728 **1.154x** | 0.3935
-> 0.3383 **1.163x** | 0.4081 -> 0.3510 **1.163x** | 0.3463 -> 0.3026
**1.144x** | 0.2816 -> 0.2438 **1.155x** | 0.2949 -> 0.2949 1.000x |
| center_4s_p8_m4184 | 63 / 0.85 (U<G) | 0.0650 -> 0.0648 1.003x |
0.0667 -> 0.0671 0.994x | 0.0875 -> 0.0876 0.999x | 0.0516 -> 0.0515
1.002x | 0.0548 -> 0.0556 0.986x | 0.0722 -> 0.0724 0.997x |
| center_5s_p4_m9648 | 266 / 3.6 | 0.5178 -> 0.4965 **1.043x** | 0.4452
-> 0.4269 **1.043x** | 0.4619 -> 0.4458 **1.036x** | 0.4227 -> 0.4092
**1.033x** | 0.3216 -> 0.3171 1.014x | 0.3420 -> 0.3423 0.999x |
| center_5s_p8_m4824 | 70 / 0.95 (U<G) | 0.0744 -> 0.0742 1.003x |
0.0736 -> 0.0743 0.991x | 0.0965 -> 0.0971 0.994x | 0.0586 -> 0.0585
1.002x | 0.0591 -> 0.0603 0.980x | 0.0785 -> 0.0787 0.997x |
| center_6s_p4_m12192 | 336 / 4.5 | 0.8226 -> 0.8216 1.001x | 0.6815 ->
0.6736 1.012x | 0.7169 -> 0.7192 0.997x | 0.6771 -> 0.6795 0.996x |
0.5040 -> 0.5040 1.000x | 0.5226 -> 0.5257 0.994x |
| center_6s_p8_m6096 | 84 / 1.14 | 0.1593 -> 0.1097 **1.452x** | 0.1524
-> 0.1064 **1.432x** | 0.1811 -> 0.1361 **1.331x** | 0.1287 -> 0.0874
**1.473x** | 0.1133 -> 0.0831 **1.363x** | 0.1385 -> 0.1223 **1.132x** |
| center_8s_p4_m14736 | 406 / 5.5 | 1.2058 -> 1.2045 1.001x | 0.9840 ->
0.9752 1.009x | 1.0306 -> 1.0349 0.996x | 0.9886 -> 0.9889 1.000x |
0.7239 -> 0.7256 0.998x | 0.7498 -> 0.7502 0.999x |
| center_8s_p8_m7368 | 105 / 1.42 | 0.1884 -> 0.1564 **1.205x** | 0.1797
-> 0.1503 **1.196x** | 0.2131 -> 0.1834 **1.162x** | 0.1500 -> 0.1254
**1.196x** | 0.1308 -> 0.1119 **1.169x** | 0.1615 -> 0.1615 1.000x |
| pad_5s_p4_used9611_total9664 | 266 / 3.6 | 0.5259 -> 0.5119 1.027x |
0.4445 -> 0.4393 1.012x | 0.4629 -> 0.4496 1.030x | 0.4240 -> 0.4145
1.023x | 0.3213 -> 0.3196 1.005x | 0.3447 -> 0.3439 1.002x |
| seg3_5s_p8_m4824 | 77 / 1.04 (U<G) | 0.0672 -> 0.0672 1.000x | 0.0762
-> 0.0688 **1.108x** | 0.0999 -> 0.0918 **1.088x** | 0.0537 -> 0.0537
1.000x | 0.0624 -> 0.0566 **1.102x** | 0.0828 -> 0.0755 **1.097x** |
| tail_5s_p4_m9587 | 266 / 3.6 | 0.5105 -> 0.4894 **1.043x** | 0.4391 ->
0.4252 **1.033x** | 0.4560 -> 0.4431 1.029x | 0.4164 -> 0.4065 1.024x |
0.3205 -> 0.3137 1.022x | 0.3413 -> 0.3414 1.000x |
| tail_5s_p4_m9685 | 266 / 3.6 | 0.5170 -> 0.4956 **1.043x** | 0.4450 ->
0.4276 **1.041x** | 0.4645 -> 0.4475 **1.038x** | 0.4241 -> 0.4104
**1.033x** | 0.3267 -> 0.3173 1.030x | 0.3454 -> 0.3456 0.999x |
| tail_5s_p8_m4763 | 70 / 0.95 (U<G) | 0.0745 -> 0.0742 1.004x | 0.0733
-> 0.0739 0.992x | 0.0972 -> 0.0975 0.997x | 0.0582 -> 0.0582 1.000x |
0.0591 -> 0.0598 0.988x | 0.0788 -> 0.0789 0.999x |
| tail_5s_p8_m4861 | 70 / 0.95 (U<G) | 0.0747 -> 0.0745 1.003x | 0.0735
-> 0.0742 0.991x | 0.0969 -> 0.0980 0.989x | 0.0587 -> 0.0587 1.000x |
0.0591 -> 0.0600 0.985x | 0.0789 -> 0.0794 0.994x |

* bf16 B200: 18 rows, geomean 1.054x, 7 rows > 3 %, worst 1.000x
(seg3_5s_p8_m4824), geomean vs FlashInfer cutlass route (new) 1.365x
* fp4 B200: 18 rows, geomean 1.058x, 8 rows > 3 %, worst 0.991x
(tail_5s_p8_m4861), geomean vs FlashInfer cutlass route (new) 1.444x
* fp8 B200: 18 rows, geomean 1.047x, 7 rows > 3 %, worst 0.989x
(tail_5s_p8_m4861), geomean vs FlashInfer cutlass route (new) 1.276x
* bf16 B300: 18 rows, geomean 1.051x, 6 rows > 3 %, worst 0.996x
(center_6s_p4_m12192), geomean vs FlashInfer cutlass route (new) 1.330x
* fp4 B300: 18 rows, geomean 1.043x, 5 rows > 3 %, worst 0.980x
(center_5s_p8_m4824), geomean vs FlashInfer cutlass route (new) 1.473x
* fp8 B300: 18 rows, geomean 1.011x, 2 rows > 3 %, worst 0.994x
(tail_5s_p8_m4861), geomean vs FlashInfer cutlass route (new) 1.257x

**Large unsplit rows (S2)** (old kernel ms -> this PR ms, ratio; same
node, one old arm then one new arm per step)

| Row | units / waves | bf16 B200 | fp4 B200 | fp8 B200 | bf16 B300 |
fp4 B300 | fp8 B300 |
|---|---|---:|---:|---:|---:|---:|---:|
| center_4s_p1_m33472 | 3696 / 50 | 22.4635 -> 22.5107 0.998x | 20.0311
-> 19.7575 1.014x | 19.9382 -> 20.0152 0.996x | 19.9889 -> 20.0211
0.998x | 14.7083 -> 14.7743 0.996x | 15.3521 -> 15.3765 0.998x |
| center_6s_p2_m24384 | 1344 / 18 | 6.2397 -> 6.2246 1.002x | 5.2292 ->
5.1982 1.006x | 5.3803 -> 5.4052 0.995x | 5.5128 -> 5.5022 1.002x |
3.7783 -> 3.7921 0.996x | 3.9696 -> 3.9424 1.007x |
| seg4_6s_p2_m24384 | 1344 / 18 | 3.1626 -> 3.1675 0.998x | 2.7135 ->
2.7010 1.005x | 2.8429 -> 2.8563 0.995x | 2.7748 -> 2.7755 1.000x |
1.9981 -> 2.0032 0.997x | 2.1286 -> 2.1261 1.001x |

* bf16 B200: 3 rows, geomean 1.000x, 0 rows > 3 %, worst 0.998x
(center_4s_p1_m33472), geomean vs FlashInfer cutlass route (new) 1.408x
* fp4 B200: 3 rows, geomean 1.008x, 0 rows > 3 %, worst 1.005x
(seg4_6s_p2_m24384), geomean vs FlashInfer cutlass route (new) 1.435x
* fp8 B200: 3 rows, geomean 0.996x, 0 rows > 3 %, worst 0.995x
(seg4_6s_p2_m24384), geomean vs FlashInfer cutlass route (new) 1.426x
* bf16 B300: 3 rows, geomean 1.000x, 0 rows > 3 %, worst 0.998x
(center_4s_p1_m33472), geomean vs FlashInfer cutlass route (new) 1.322x
* fp4 B300: 3 rows, geomean 0.996x, 0 rows > 3 %, worst 0.996x
(center_4s_p1_m33472), geomean vs FlashInfer cutlass route (new) 1.518x
* fp8 B300: 3 rows, geomean 1.002x, 0 rows > 3 %, worst 0.998x
(center_4s_p1_m33472), geomean vs FlashInfer cutlass route (new) 1.537x

**Program-cost calibration (B300 fp8pv).** With the 1.21 cost measured
on a 33k-token plan, the planner split the 1.42-wave
row `center_8s_p8` 31x2 and it measured 0.977x, and the 1.14-wave row
gained 1.132x against a modelled 1.32x: the split
program's fixed per-unit cost is a larger share of the 48-58 block units
of the partial-wave rows (effective 1.30-1.42x).
`SPLIT_PROGRAM_COST[("fp8", "sm_103a")] = 1.35` keeps the 1.42-wave row
dense (re-paired 1.000x) and still splits the
1.14-wave row (1.132x); the planner test pins both decisions.

**Shortest NVFP4 fp4pv rows (`U < G`, 55-75 us).** Before the signature
alignment these rows (`center_4s_p8`,
`center_5s_p8`, `tail_5s_p8_*`) measured 0.982-0.993x in four-arm
same-node A/Bs on both architectures (old arms repeat
within 0.3 %) on a dense program whose SASS equalled the merged kernel
up to the constant-bank offsets of six added
kernel parameters. With the dense program declared with the merged
kernel's signature (SASS identical, constant bank
included), the four-arm A/B (fp4pv, old / new / old / new; ratio = mean
old / mean new) reads:

**Root cause and fix.** With the dense program's SASS identical to the
merged kernel the four-arm A/B still read 0.984-0.997x on these rows,
and the per-kernel stage times of both trees were equal (quantize
11.1-11.2 us, attention 44.5-44.6 us on B300); the whole difference sat
in the span between the two kernels. Two experiments located it on the
host: a bit-exact quantizer that is 0.9 us faster (this PR's regenerated
`minimax_h3_varlen_nvfp4_quantize_*` programs: one 8-byte store per
packed 16-vector and quad-shuffled 4-byte UE4M3 scale words instead of
scattered byte stores; quantize-only 11.2 -> 10.2 us, 10.0 -> 9.4 us,
17.9 -> 16.6 us on B200) left the complete-call span of these rows
unchanged on both architectures while the 10s_p8 row gained the full
1.0-1.1 %, and a host probe measured 16.7 us of host time per complete
call in the source launcher (the attention shim re-encoded its seven
tensor maps on every call). The benchmark synchronizes before every
call, so on these 55-75 us rows the attention launch reached the GPU
only after the 10-11 us quantizer had finished: the span was host-bound
and the PDL prologue overlap never happened. The source launcher now
marshals every stage once and issues the complete call from one native
launch sequence (`cuLaunchKernelEx` with the cluster and
programmatic-stream-serialization attributes; host time 16.7 -> 10.7 us
per call), which made the inter-kernel gap negative on both
architectures and exposed the quantizer gain. The FlashInfer runner in
this PR is unchanged: it launches the generated programs through their
host bindings (tensor maps encoded at preparation and passed by value)
and leaves CUDA-graph capture to the caller. The quantizer also signals
its dependent grid at the start of its body instead of the end (no
measurable change alone; the attention program still waits on
`griddepcontrol.wait` before its first packed-operand read).

Four-arm same-node A/B of the source launcher (old arm / new arm / old
arm / new arm in one step; ratio = mean old / mean new; old arms repeat
within 0.5 %; 0 correctness failures):

| Row (fp4pv, U < G unless noted) | B200 old -> new | B200 ratio | B300
old -> new | B300 ratio |
|---|---:|---:|---:|---:|
| center_4s_p8_m4184 | 66.2 -> 61.9 us | **1.069x** | 54.2 -> 47.6 us |
**1.140x** |
| center_5s_p8_m4824 | 73.1 -> 69.4 us | **1.053x** | 58.9 -> 52.8 us |
**1.115x** |
| tail_5s_p8_m4763 | 73.0 -> 69.5 us | **1.050x** | 58.6 -> 52.8 us |
**1.109x** |
| tail_5s_p8_m4861 | 73.0 -> 69.5 us | **1.050x** | 58.9 -> 53.1 us |
**1.109x** |
| center_10s_p8_m9280 (1.8 waves, control) | 219.9 -> 217.3 us | 1.012x
| 158.6 -> 155.9 us | 1.017x |


Same four-arm A/B for fp8pv at `5f07bd32832` (ratio = mean old / mean
new; 0 correctness failures). The fp8 quantize stage (V amax reduction +
quantizer, 31-35 us) already outlasted the host launch path, so these
rows gain only the quantizer's coalesced stores and the overlapped
attention prologue:

| Row (fp8pv, U < G) | B200 old -> new | B200 ratio | B300 old -> new |
B300 ratio |
|---|---:|---:|---:|---:|
| center_4s_p8_m4184 | 86.5 -> 84.5 us | 1.023x | 71.9 -> 70.2 us |
1.024x |
| center_5s_p8_m4824 | 96.4 -> 94.6 us | 1.019x | 78.8 -> 77.3 us |
1.019x |
| tail_5s_p8_m4763 | 96.4 -> 94.5 us | 1.020x | 79.0 -> 77.5 us | 1.019x
|
| tail_5s_p8_m4861 | 97.2 -> 94.7 us | 1.026x | 79.5 -> 77.7 us | 1.024x
|


Four-arm verification at the final programs (fp4pv, old / new / old /
new arms; ratio = mean old / mean new):

| Row | B200 | B300 |
|---|---:|---:|
| center_4s_p4_m8368 (3.2 waves, split) | 1.160x | 1.155x |
| center_6s_p8_m6096 (1.14 waves, split) | 1.438x | 1.364x |
| seg3_5s_p8_m4824 (LPT placement) | 1.100x | 1.113x |
| center_10s_p8_m9280 (1.8 waves, dense) | 1.003x | 0.996x |
| center_4s_p8_m4184 (U < G, dense) | 0.989x | 0.987x |
| center_5s_p8_m4824 (U < G, dense) | 0.987x | 0.982x |
| tail_5s_p8_m4763 (U < G, dense) | 0.987x | 0.988x |
| tail_5s_p8_m4861 (U < G, dense) | 0.992x | 0.988x |


Rows with `U < G` run the dense program in both arms (the planner never
splits them); `seg3` gains 1.09-1.11x on NVFP4
from the longest-processing-time-first placement of its unequal units
(BF16 was already placed that way: 1.000x). Rows at or
above four waves bind the dense program (SASS-identical to the merged
fp4pv kernel) and are covered by the S2 pairs and the
120-row export seal per architecture.

### Round 2: device `amax(V)` stage for the fp8-PV route

The fp8pv `U < G` rows (`center_4s_p8`, `center_5s_p8`, `tail_5s_p8_*`,
50-95 us) were the last rows below the FlashInfer
cutlass ragged route (0.955-0.975x on B200, 0.912-0.938x on B300): their
quantize step spent 31-35 us, of which ~20 us
were two `torch.linalg.vector_norm(ord=inf)` launches computing the
per-tensor `amax(V)` for the E4M3 scale.

* New generated stage **`amax`** (`minimax_h3_varlen_v_amax_partial`): a
fixed grid of 512 CTAs strides over the BF16 V
tensor in 32-byte vectors and writes one partial `max|V|` each
(`v_amax_partial[512]`, `AMAX_KWARGS`).
* The fp8 quantizer is that kernel's **programmatic dependent launch**:
its generated binding carries the PDL attribute,
its Q/K/V loads overlap the amax tail, and only the fold of the 512
partials waits (`griddepcontrol.wait`); CTA 0
publishes `v_amax[0]` for the attention kernel. The maximum is order
independent, so every packed operand and the
output are bit-identical to the torch path (identical error metrics in
every A/B arm).
* Host: `reduce_v_amax` is gone; `nvfp4_fp8pv` stages are `(amax,
quantize, attention, attention_split, combine)`,
`runner.quantize()` submits amax + quantizer, `runner.attention()` the
rest; `nvfp4_workspace_shapes` has
`v_amax_partial = (512,)`. fp4pv and bf16 programs are byte-identical to
the previous delivery (per-stage cubin hashes
checked on both architectures); only the fp8 quantizer cubin changes and
the amax program is added.

Four-arm same-node A/B vs the previous delivery (old/new/old/new,
`--bench-ms 150 --groups 5`, ratio = mean old / mean new,
old arms repeat within 0.1 %, new within 0.2 %, 0 correctness failures):

| Row (fp8pv) | B200 old -> new | B200 ratio | B200 vs cutlass | B300
old -> new | B300 ratio | B300 vs cutlass |
|---|---:|---:|---:|---:|---:|---:|
| center_4s_p8_m4184 | 85.2 -> 64.5 us | **1.321x** | 0.955 ->
**1.254x** | 70.0 -> 50.7 us | **1.382x** | 0.912 -> **1.258x** |
| center_5s_p8_m4824 | 94.7 -> 71.9 us | **1.317x** | 0.974 ->
**1.275x** | 77.2 -> 55.5 us | **1.391x** | 0.937 -> **1.300x** |
| tail_5s_p8_m4763 | 94.7 -> 71.9 us | **1.316x** | 0.975 -> **1.277x**
| 77.2 -> 55.4 us | **1.394x** | 0.935 -> **1.296x** |
| tail_5s_p8_m4861 | 94.8 -> 72.0 us | **1.316x** | 0.975 -> **1.274x**
| 77.5 -> 55.7 us | **1.390x** | 0.935 -> **1.294x** |
| center_10s_p8_m9280 (1.8 waves, control) | 235.6 -> 223.5 us | 1.054x
| 1.311 -> 1.379x | 176.6 -> 161.0 us | 1.097x | 1.340 -> 1.467x |

<!-- FP8_REST_TABLE_START -->
| Row (fp8pv) | B200 old -> new | B200 ratio | B200 vs cutlass | B300
old -> new | B300 ratio | B300 vs cutlass |
|---|---:|---:|---:|---:|---:|---:|
| center_4s_p1_m33472 | 20.00 ms -> 19.99 ms | **1.000x** | 1.436 ->
**1.437x** | 14.95 ms -> 15.02 ms | 0.995x | 1.507 -> **1.500x** |
| center_4s_p2_m16736 | 2587.2 us -> 2577.6 us | **1.004x** | 1.448 ->
**1.453x** | 1858.6 us -> 1860.8 us | 0.999x | 1.550 -> **1.548x** |
| center_4s_p4_m8368 | 350.0 us -> 340.9 us | **1.027x** | 1.565 ->
**1.607x** | 296.0 us -> 283.2 us | **1.045x** | 1.435 -> **1.501x** |
| center_5s_p1_m38592 | 27.04 ms -> 27.04 ms | **1.000x** | 1.385 ->
**1.385x** | 20.11 ms -> 20.07 ms | **1.002x** | 1.489 -> **1.492x** |
| center_5s_p2_m19296 | 3404.9 us -> 3426.4 us | 0.994x | 1.460 ->
**1.451x** | 2481.1 us -> 2474.4 us | **1.003x** | 1.561 -> **1.566x** |
| center_5s_p4_m9648 | 449.8 us -> 441.9 us | **1.018x** | 1.434 ->
**1.460x** | 345.7 us -> 335.9 us | **1.029x** | 1.448 -> **1.491x** |
| center_6s_p1_m48768 | 41.86 ms -> 41.75 ms | **1.003x** | 1.468 ->
**1.471x** | 30.64 ms -> 30.70 ms | 0.998x | 1.595 -> **1.592x** |
| center_6s_p2_m24384 | 5403.4 us -> 5393.0 us | **1.002x** | 1.467 ->
**1.470x** | 3824.8 us -> 3824.1 us | **1.000x** | 1.574 -> **1.574x** |
| center_6s_p4_m12192 | 721.3 us -> 713.5 us | **1.011x** | 1.414 ->
**1.429x** | 528.2 us -> 519.8 us | **1.016x** | 1.501 -> **1.525x** |
| center_6s_p8_m6096 | 132.4 us -> 106.1 us | **1.248x** | 1.567 ->
**1.956x** | 120.7 us -> 95.3 us | **1.266x** | 1.337 -> **1.693x** |
| center_8s_p1_m58944 | 57.64 ms -> 57.83 ms | 0.997x | 1.600 ->
**1.595x** | 42.64 ms -> 42.79 ms | 0.996x | 1.712 -> **1.706x** |
| center_8s_p2_m29472 | 7579.1 us -> 7596.4 us | 0.998x | 1.483 ->
**1.480x** | 5584.9 us -> 5579.2 us | **1.001x** | 1.593 -> **1.595x** |
| center_8s_p4_m14736 | 1037.1 us -> 1030.5 us | **1.006x** | 1.436 ->
**1.445x** | 755.4 us -> 749.1 us | **1.008x** | 1.526 -> **1.539x** |
| center_8s_p8_m7368 | 180.9 us -> 149.4 us | **1.211x** | 1.376 ->
**1.666x** | 159.7 us -> 129.9 us | **1.229x** | 1.196 -> **1.470x** |
| center_10s_p1_m74240 | 88.55 ms -> 88.66 ms | 0.999x | 1.640 ->
**1.638x** | 64.11 ms -> 64.30 ms | 0.997x | 1.828 -> **1.823x** |
| center_10s_p2_m37120 | 11.95 ms -> 11.96 ms | 0.999x | 1.485 ->
**1.484x** | 9020.8 us -> 9022.6 us | 1.000x | 1.550 -> **1.549x** |
| center_10s_p4_m18560 | 1551.6 us -> 1550.4 us | **1.001x** | 1.445 ->
**1.446x** | 1123.0 us -> 1115.7 us | **1.007x** | 1.533 -> **1.543x** |
| center_15s_p1_m109952 | 187.09 ms -> 187.09 ms | **1.000x** | 1.740 ->
**1.740x** | 134.21 ms -> 134.70 ms | 0.996x | 1.977 -> **1.969x** |
| center_15s_p2_m54976 | 26.90 ms -> 26.88 ms | **1.001x** | 1.416 ->
**1.417x** | 20.14 ms -> 20.19 ms | 0.998x | 1.501 -> **1.497x** |
| center_15s_p4_m27488 | 3441.0 us -> 3440.2 us | **1.000x** | 1.480 ->
**1.480x** | 2481.2 us -> 2481.6 us | 1.000x | 1.585 -> **1.584x** |
| center_15s_p8_m13744 | 437.8 us -> 428.1 us | **1.023x** | 1.525 ->
**1.560x** | 347.9 us -> 332.7 us | **1.046x** | 1.481 -> **1.549x** |
| tail_5s_p1_m38531 | 26.98 ms -> 27.04 ms | 0.998x | 1.386 ->
**1.383x** | 20.07 ms -> 20.07 ms | **1.000x** | 1.486 -> **1.487x** |
| tail_5s_p1_m38629 | 27.03 ms -> 27.16 ms | 0.995x | 1.392 ->
**1.385x** | 20.09 ms -> 20.16 ms | 0.997x | 1.488 -> **1.483x** |
| tail_5s_p2_m19235 | 3403.4 us -> 3413.1 us | 0.997x | 1.459 ->
**1.455x** | 2478.1 us -> 2477.8 us | **1.000x** | 1.565 -> **1.565x** |
| tail_5s_p2_m19333 | 3419.2 us -> 3412.1 us | **1.002x** | 1.457 ->
**1.460x** | 2486.6 us -> 2484.3 us | **1.001x** | 1.566 -> **1.567x** |
| tail_5s_p4_m9587 | 444.8 us -> 437.3 us | **1.017x** | 1.434 ->
**1.459x** | 342.1 us -> 331.9 us | **1.031x** | 1.444 -> **1.488x** |
| tail_5s_p4_m9685 | 449.5 us -> 441.0 us | **1.019x** | 1.433 ->
**1.460x** | 345.0 us -> 335.7 us | **1.028x** | 1.447 -> **1.487x** |
| pad_5s_p4_used9611_total9664 | 452.1 us -> 444.6 us | **1.017x** |
1.423 -> **1.447x** | 345.5 us -> 335.3 us | **1.031x** | 1.439 ->
**1.483x** |
| pad_15s_p1_used109901_total109952 | 187.27 ms -> 187.19 ms |
**1.000x** | 1.739 -> **1.739x** | 134.60 ms -> 134.69 ms | 0.999x |
1.980 -> **1.978x** |

Four arms (old/new/old/new) on both architectures: B200
nsc-svg-slurm-1-gpu-139, step `96386dda` (the first B200 run `7de52d22`
on gpu-62 hit the 3 h managed-step timeout in arm 4 after three complete
arms; its old/new/old ratios agree with this table to within 0.3 %);
B300 pool0-0001, step `bd257e09`. 0 correctness failures, error metrics
identical to the printed digits in every arm. Every row on both
architectures is faster than the FlashInfer cutlass route (B200 min
1.383x, B300 min 1.470x). Every row is within -0.7 % of the delivered
kernel: the rows below 1.00x are the >= 1.8-wave rows where the amax
pass adds one full read of V and the quantizer's PDL overlap does not
pay back (worst 0.9937x B200 center_5s_p2, 0.9953x B300 center_4s_p1);
their old-arm and new-arm repeats spread by 0.1-0.5 % on both arches, so
these deficits are at the resolution of the protocol, and none is below
the 0.99x bar.

```
B200: 29 rows, ratio geomean 1.0188 min 0.9937 (center_5s_p2_m19296) max 1.2484; vs cutlass geomean 1.5075 min 1.3833 (tail_5s_p1_m38531); rows <1.00x vs old: 8 [('center_5s_p2_m19296', 0.9937), ('center_8s_p1_m58944', 0.9967), ('center_8s_p2_m29472', 0.9977), ('center_10s_p1_m74240', 0.9987), ('center_10s_p2_m37120', 0.9992), ('tail_5s_p1_m38531', 0.9978), ('tail_5s_p1_m38629', 0.9954), ('tail_5s_p2_m19235', 0.9972)]; rows <0.99x: []; arms old/new per row: 2/2

B300: 29 rows, ratio geomean 1.0230 min 0.9953 (center_4s_p1_m33472) max 1.2659; vs cutlass geomean 1.5759 min 1.4698 (center_8s_p8_m7368); rows <1.00x vs old: 11 [('center_4s_p1_m33472', 0.9953), ('center_4s_p2_m16736', 0.9988), ('center_6s_p1_m48768', 0.998), ('center_8s_p1_m58944', 0.9964), ('center_10s_p1_m74240', 0.9972), ('center_10s_p2_m37120', 0.9998), ('center_15s_p1_m109952', 0.9963), ('center_15s_p2_m54976', 0.9975), ('center_15s_p4_m27488', 0.9998), ('tail_5s_p1_m38629', 0.9965), ('pad_15s_p1_used109901_total109952', 0.9993)]; rows <0.99x: []; arms old/new per row: 2/2

correctness failures: B200 0, B300 0
```
<!-- FP8_REST_TABLE_END -->

Gates at the producer revision on both architectures: e2e slice 20
passed, benchmark-regression ALL PASS, compute-sanitizer
synccheck + memcheck 6/6 `ERROR SUMMARY: 0 errors`.

## Baselines and their source PRs

Every "vs FlashInfer" number in this PR compares against the **fastest
upstream ragged noncausal BF16 prefill route per row**
(`BatchPrefillWithRaggedKVCacheWrapper`, `kv_layout="NHD"`, planned once
per shape outside the timed region, `run()` timed
with CUPTI, cold L2). All four routes (`fa2`, `cudnn`, `cutlass`,
`cute-dsl`) are timed for every row and the fastest is the
denominator; on every row of the tables above that was the **`cutlass`**
route (SM100 CUTLASS FMHA). Baseline revision:
this branch's upstream merge-base `28ae778e4` (2026-09-24). Origin PRs
of the baseline implementations at that revision:

| Route | Implementation files | Introduced | Last change at the
merge-base |
|---|---|---|---|
| `cutlass` (SM100 CUTLASS FMHA, the winning route) |
`csrc/fmha_cutlass_sm100.cu`, `csrc/fmha_cutlass_sm100_binding.cu`,
`include/flashinfer/attention/blackwell/` | #1039 (`9a05c92ad`,
2025-05-12) | #3064 (`1aa32d03e`, 2026-05-08), #2047 (`db2aacbd3`,
2025-12-17), #3888 (`a6c626819`, 2026-07-09) |
| `cute-dsl` (DSL FMHA cubins) | `flashinfer/attention/cute_dsl/fmha.py`
| #3039 (`bb873d207`, 2026-04-24) | #4997 (`75038cdf6`, 2026-09-10) |
| `cudnn` | `flashinfer/cudnn/prefill.py` | #1187 (`ece99ccce`,
2025-06-30) | #5350 (`7685a893e`, 2026-09-24) |
| `fa2` | `csrc/batch_prefill.cu`, `csrc/batch_prefill_jit_binding.cu`,
`include/flashinfer/attention/prefill.cuh` | #643 / #143 | #5176
(`e0a18900c`, 2026-09-21), #3871, #5239 (`b8107c7fd`, 2026-09-17) |
| wrapper (`flashinfer/prefill.py`, route dispatch) |
`flashinfer/prefill.py` | #643 | #5350 (`7685a893e`, 2026-09-24) |

No commit on `origin/main` after the merge-base (`git log
28ae778e4..origin/main -- <files>` at `a3701b2ee`, 2026-09-25) touches
any of these files, so the comparison is against the current upstream
baselines. The correctness oracle is the package's own
FP32 reference (`_reference` in the test file: explicit FP32
`softmax(QK^T * scale) V` per packed segment and head; tolerances BF16
`atol=rtol=1e-2`, NVFP4 `atol=1.0 / rtol=0.1`),
not an upstream kernel.

## 🔍 Related Issues

#4532 (candidates 3A / 3C), tracker #4254. Follow-up to #5499.

## Export evidence (generated programs vs the source launcher, both
architectures)

**sm_100a (NVIDIA B200, driver 580.82.07, torch
2.13.0a0+9186a08b2c.nv26.07 / CUDA 13.3;
`symmetric_external_cuda_graph`, 3 counterbalanced groups x 100
calls)**: 120/120 rows sealed (correctness on both arms, timing gates),
producer `0f23b223a01`, target scaffold `500861494`.

| Family | rows | source ms (geomean) | export ms (geomean) | source /
export |
|---|---:|---:|---:|---:|
| all | 120 | 1.3560 | 1.3500 | 1.0044x |
| bf16 | 40 | 1.5484 | 1.5487 | 0.9999x |
| nvfp4_fp8pv | 40 | 1.2839 | 1.2760 | 1.0062x |
| nvfp4_fp4pv | 40 | 1.2540 | 1.2452 | 1.0071x |

**sm_103a (NVIDIA B300 SXM6 AC, driver 580.126.09, torch
2.13.0a0+9186a08b2c.nv26.07 / CUDA 13.3;
`symmetric_external_cuda_graph`, 3 counterbalanced groups x 100
calls)**: 119/120 rows sealed (correctness on both arms, timing gates),
producer `0f23b223a01`, target scaffold `500861494`.

| Family | rows | source ms (geomean) | export ms (geomean) | source /
export |
|---|---:|---:|---:|---:|
| all | 119 | 1.0380 | 1.0299 | 1.0078x |
| bf16 | 39 | 1.2842 | 1.2818 | 1.0019x |
| nvfp4_fp8pv | 40 | 0.9752 | 0.9613 | 1.0145x |
| nvfp4_fp4pv | 40 | 0.8977 | 0.8915 | 1.0069x |

Packages from either architecture carry both `sm_100a` and `sm_103a`
csrc directories and the `delivery.patch` is byte-identical across the
two exports (sha256
`54ab25e6f1ce40707c58f1c24b6e38bfb1db6c3080c4f3ec04413a722fe902c6`,
90,583 B on both hosts) and identical to the FlashInfer regeneration
commit `9d46c1625` of this delivery (PR head `3605574e4` adds only two
mypy type annotations in the host file) (`git diff` of the integrated
worktree differs only in index-hash width). The FlashInfer package tests
(`tests/experimental/test_cake_minimax_h3_varlen_attention.py`) pass on
both nodes (625 passed on B200 nsc-svg-slurm-1-gpu-20 and 625 passed on
B300 pool0-0068 and again on pool0-0056). FlashInfer bench geomeans vs
the ragged BF16 route: B200 bf16 1.013x / fp8pv 1.242x / fp4pv 1.266x;
B300 bf16 1.037x / fp8pv 1.446x / fp4pv 1.544x (pool0-0068; pool0-0056:
1.086x / 1.493x / 1.607x). Measurement-validity retries: B200
re-measured `bf16 center_15s_p8_m13744` and `bf16 tail_5s_p4_m9587` in
place after an `endpoint_drift` gate (sealed 120/120). B300 re-measured
five `endpoint_drift` BF16 rows in place (sealed) and **one row stays
unsealed: `bf16__seg4_6s_p2_m24384__sm_103a`** — its receipt
(`receipts/bf16__seg4_6s_p2_m24384__sm_103a.json`, sha256
`61e68000de8e…`) records `InterleavedTimingError: reportable loaded SM
clock 1372/2032 MHz is below the 0.700000 fraction gate`; the same clock
gate tripped on four attempts across two nodes (pool0-0068:
1402/1395/1395 MHz, pool0-0056: 1372 MHz), i.e. this BF16 four-segment
24k-token row sustains only 67-69 % of the max SM clock on the
air-cooled B300 SXM6 nodes we were allocated, so the exporter refuses to
attest its timing. The BF16 program is byte-identical to the previous
delivery (cubin identity table above), where this row sealed on B300 at
2.883 ms source / 2.879 ms export (1.0013x), and its correctness passed
in every attempt; the row is also measured in the same-node paired A/B
of the first delivery (bf16 `seg4_6s_p2` 1.10-1.11x vs the FlashInfer
route on both arches).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed (round 2:
`v_amax_partial` workspace shape, per-PV-mode stage lists,
`AMAX_KWARGS`/grid; round 1: plan invariants for the four-word unit
table, K/V-split coverage,
forced splits, combine-table consistency; runner stage list incl.
`attention_split` / `combine`; the dense program is
bound for plans without split units and the split program for a
1.14-wave plan).
- [x] All tests are passing
(`tests/experimental/test_cake_minimax_h3_varlen_attention.py`: 625
passed on B200 (nsc-svg-slurm-1-gpu-20) and 625 passed on B300
(pool0-0068) with the delivered package, both after the round-2 export).

## 🔬 Experimental Track

- [x] This PR is **experimental**: it changes code under
`flashinfer/experimental/` and the two
`@flashinfer_experimental_api` entry points keep their signatures.
Tracking issue: #4532
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`.

- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets.

```experimental-tests
tests/experimental/test_cake_minimax_h3_varlen_attention.py
```

## Reviewer Notes

* The generated sources under
`flashinfer/experimental/minimax_h3_varlen_attention/csrc/` are
receipt-bound export artifacts (excluded from clang-format like the
other generated packages); they are regenerated (two NVFP4 attention
programs
per PV mode and arch, the BF16 attention kernels, the `combine` kernel,
and in this round the fp8 `amax` program and the PDL-dependent fp8
quantizer); `cake_jit.py` registry literals are populated verbatim by
the generator.
* The planner constants (combine cost 3.0 blocks + 0.02 per slot, 3 %
minimum gain, at most 8 splits, no split at or
above four waves) were calibrated on B200 and B300; they only decide
*whether* to split, correctness does not depend
  on them (forced splits are covered by the tests).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* BF16 and NVFP4 attention planning can split K/V blocks across multiple
units when the plan is expected to run faster, then combine partial
results.
* NVFP4 selects between dense and split attention programs based on the
plan.
* FP8-PV processing calculates the maximum value on the GPU before
quantization, avoiding a host-side reduction.
* Added support for these attention workflows on supported GPU
architectures.
* **Documentation**
* Updated planning and execution guidance for split attention and FP8-PV
processing.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4504
- **最后更新**: 2026-09-26T23:24:32Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34611
- **最后更新**: 2026-09-26T21:07:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
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


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13183
- **最后更新**: 2026-09-26T07:24:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36457
- **最后更新**: 2026-09-27T00:18:14Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 10
- **主要提交者**: yuyu5333, Cheng Wan, Thomas Wang

## AI分析总结

以下是对 `sgl-project/sglang` 昨日提交记录的分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了内存缓存（MemCache）组件的游标和后端选择问题，以及AMD ROCm环境下JIT编译的异常。
- **性能优化**：优化了Mamba2模型在特定硬件上的执行效率，提升了约7.5%的推理性能。
- **重构**：对Dense层边界选择、批量重叠布局、LayerNorm边界处理、FFN退出逻辑等多个内部组件进行了重构，旨在优化计算图与通信流程。
- **功能新增**：新增了DeepSelect JIT内核以支持DeepSeek V4.1模型架构；增强了滑动窗口缓存与投机批处理填充的扩展性。
- **CI/测试改进**：调整了夜间测试集、修复了测试文件入口点，并重组了部分测试模块以解决命名空间冲突。

### 2. 关键变更点及其与项目整体方向的关系
- **内存缓存修复**：确保了缓存系统在多后端选择下的稳定性，这对维持大模型推理的高性能和内存效率至关重要，符合项目对高效推理的追求。
- **AMD ROCm支持修复**：提升了框架对非NVIDIA硬件的兼容性，有助于扩大项目在多元硬件生态中的适用性。
- **性能与架构优化**：对Mamba2的优化直接提升了在特定硬件上的服务吞吐量；多项重构则旨在优化模型并行策略与通信开销，为更复杂模型和更大规模部署奠定基础。
- **DeepSelect与新模型支持**：新增的JIT内核和滑动窗口扩展性工作，直接支持了如DeepSeek V4.1等新架构的集成与高效运行，体现了框架对前沿模型架构的快速跟进能力。

### 3. 对项目的影响和潜在意义
- **提升稳定性与可靠性**：关键Bug的修复直接改善了现有功能的可靠性，特别是缓存和硬件支持方面。
- **增强性能与可扩展性**：性能优化和架构重构预计将提升框架的整体推理效率与资源利用率，并为未来支持更复杂的并行策略（如更灵活的张量/流水线并行）铺平道路。
- **扩大硬件与模型覆盖面**：改进AMD支持与新增模型内核，有助于吸引更广泛的用户群体，并巩固项目在多样化部署环境下的竞争力。

### 4. 值得关注的技术点
- **缓存后端选择与游标管理**：涉及多后端内存缓存系统的细节，是高效管理大模型KV缓存的关键技术。
- **JIT编译的硬件适配**：确保JIT编译器在不同硬件平台（NVIDIA/AMD）上的正确性与性能。
- **并行策略的重构**：涉及Dense层边界选择、批量重叠分割布局等，展示了框架在精细控制模型并行计算图方面的深入优化。
- **Mamba2状态更新优化**：通过调整CUDA内核启动配置（8x1 launch config）在特定硬件上实现了显著加速，是针对状态空间模型的重要优化案例。

### 5. 基于项目背景的影响分析
SGLang作为一个专注于高效大模型推理与服务的框架，其核心目标是提供高性能、易扩展且兼容多硬件的解决方案。本次提交：
- **强化了核心性能与稳定性**：通过修复和优化，确保了现有功能在主流硬件上的高效稳定运行。
- **拓展了模型与硬件边界**：新内核与硬件支持工作，使框架能更快适配前沿模型（如DeepSeek V4.1）和新兴硬件（如AMD），增强了生态吸引力。
- **夯实了架构扩展基础**：内部重构优化了计算与通信流程，为未来支持更复杂的并行策略和模型架构提供了更灵活、更高效的内部结构。
- 总体而言，这批提交从**稳定性、性能、扩展性**多方面推动了项目，使其在快速发展的生成式AI推理框架领域中保持技术先进性与实用性。

## 详细提交记录

### [fc9e1c8](https://github.com/sgl-project/sglang/commit/fc9e1c8d296216ff1e216dfbe7286ef392448d28)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-26T18:24:39Z
- **提交信息**: [MemCache] Fix LMCache component cursors and per-cache backend selection (#41328)

Co-authored-by: Lu Fang <30275821+houseroad@users.noreply.github.com>

### [c10fa03](https://github.com/sgl-project/sglang/commit/c10fa03fc43180fcae072c6535f6c6d9c33c3ef1)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-26T18:24:02Z
- **提交信息**: Make sliding-window caching and speculative batch padding extensible (#41325)

Co-authored-by: Lu Fang <30275821+houseroad@users.noreply.github.com>
Co-authored-by: jasonjk-park <jasonjk@fb.com>

### [c73f707](https://github.com/sgl-project/sglang/commit/c73f7077eb051ceeaadfa8819b20ed6d4912e8de)

- **作者**: Thomas Wang
- **时间**: 2026-09-26T16:59:59Z
- **提交信息**: [AMD] Fix jit broken on rocm env (#41356)

### [7bdd8fe](https://github.com/sgl-project/sglang/commit/7bdd8fe6ec2a94d6a0d11b885ca9fe6a9f610d53)

- **作者**: Khoa Pham
- **时间**: 2026-09-26T16:48:00Z
- **提交信息**: [CI] Merge the Kimi-Linear PD DCP4 nightly tests and drop exact-token parity (#41321)

### [e1e97e8](https://github.com/sgl-project/sglang/commit/e1e97e8b4949bd9ec4b3b459b2e631f2410c4bc8)

- **作者**: Ariel
- **时间**: 2026-09-26T16:43:25Z
- **提交信息**: Pin triton_kernels num_warps for MXFP4 MoE below Hopper (6x gpt-oss decode on RTX 4090) (#41292)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [cdbea5d](https://github.com/sgl-project/sglang/commit/cdbea5dccf0a8085200abad617910c9688e932fe)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-26T13:39:00Z
- **提交信息**: [CI] Move DeepSelect into the attention kernel group to fix the namespace test (#41349)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [710a41b](https://github.com/sgl-project/sglang/commit/710a41ba570abdb3aa127916088ca62a9b665ca4)

- **作者**: Shangming Cai
- **时间**: 2026-09-26T11:39:01Z
- **提交信息**: [sgl-router] Book the input_ids forwarding outcome only for built bodies (#41342)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [a947b56](https://github.com/sgl-project/sglang/commit/a947b56bc7cb135a47911bbf49e83011497a434c)

- **作者**: DarkSharpness
- **时间**: 2026-09-26T10:12:41Z
- **提交信息**: [CI] Add __main__ entry to test_deep_select.py (#41341)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [bd37e7f](https://github.com/sgl-project/sglang/commit/bd37e7f513b67701afe27a93e1dc45320d724eeb)

- **作者**: Cheng Wan
- **时间**: 2026-09-26T09:41:43Z
- **提交信息**: [Refactor] Choose a dense layer's boundaries under attention DP from both sides' declarations (#41257)

### [9cd6616](https://github.com/sgl-project/sglang/commit/9cd6616c24c41a6e7b28d1d50be7363a5b0b330f)

- **作者**: Cheng Wan
- **时间**: 2026-09-26T09:41:09Z
- **提交信息**: [Refactor] Pick the two-batch-overlap split's layout moves once and remove execute (#41256)

### [d3fcf89](https://github.com/sgl-project/sglang/commit/d3fcf8997cf2fc7ea51cdd7a852dc57306cb0a5a)

- **作者**: Cheng Wan
- **时间**: 2026-09-26T09:40:34Z
- **提交信息**: [Refactor] Run the LayerNorm SP region's boundary steps in the communicator itself (#41255)

### [35b369e](https://github.com/sgl-project/sglang/commit/35b369ebba2c8a05a0b76373dedd834e605483a9)

- **作者**: Cheng Wan
- **时间**: 2026-09-26T09:39:58Z
- **提交信息**: [Refactor] Declare at construction the layers whose FFN completes its own reduction (#41254)

### [c081d4a](https://github.com/sgl-project/sglang/commit/c081d4aacc439fed6aacbb96ed16fe4d0d5ec94e)

- **作者**: Cheng Wan
- **时间**: 2026-09-26T09:39:25Z
- **提交信息**: [Refactor] Drive an FFN exit's flags and its completion from one selection (#41253)

### [8fc3ce4](https://github.com/sgl-project/sglang/commit/8fc3ce48da1c296d195f5a48981e3988608d5f63)

- **作者**: Cheng Wan
- **时间**: 2026-09-26T09:38:03Z
- **提交信息**: [Refactor] Choose prepare_attn / prepare_mlp steps and fused kernels at construction (#41252)

### [7bc9884](https://github.com/sgl-project/sglang/commit/7bc988446d54490f771b9ee7e8c63e449b77c417)

- **作者**: yuyu5333
- **时间**: 2026-09-26T09:36:48Z
- **提交信息**: [DeepSeek V4.1] Add DeepSelect JIT kernel. (#40556)

Co-authored-by: DarkSharpness <2040703891@qq.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [a5c8afa](https://github.com/sgl-project/sglang/commit/a5c8afab48a3ee850d05e7fba6fc8d1e0dc0dae9)

- **作者**: Hexu Zhao
- **时间**: 2026-09-26T09:27:01Z
- **提交信息**: [Perf] Mamba2 selective_state_update up to 2x faster on B200 via 8x1 launch config for dstate 128 (+7.5% Nemotron-3-Super serving) (#41223)

Co-authored-by: hexu.zhao <zhaohexu2001@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1286
- **最后更新**: 2026-09-24T16:23:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92728
- **最后更新**: 2026-09-27T00:33:39Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 15
- **主要提交者**: simon-veitner-redhat, Kevin H. Luu, Lucas Wilkinson

## AI分析总结

根据提供的提交记录，结合项目目标，分析如下：

### 1. 主要更新类型
本次更新涵盖了多个方面：**性能优化**、**Bug修复**、**安全加固**、**CI/测试稳定性提升**、**架构支持演进**以及**代码质量与重构**。其中，性能优化和Bug修复占据了较大比重。

### 2. 关键变更点及其与项目整体方向的关系
*   **性能与内核优化**：提交（如#58846, #58586, #58720）聚焦于算子融合、减少内存拷贝与同步开销、优化MoE（专家混合模型）加载。这直接服务于项目“**Fast**”的核心目标，通过底层内核的持续优化来提升推理速度和吞吐量。
*   **硬件与模型支持演进**：提交（如#56723, #58473, #57263）涉及对新硬件架构（如DCP、弹性EP）的支持以及为新模型（如Gemma4）添加特性。这体现了项目积极跟进硬件发展与模型迭代，旨在扩大适用场景，是项目保持竞争力的关键。
*   **可靠性与安全性强化**：多个Bug修复（如#58594, #58754, #58786）针对具体模型（GLM、Anthropic）的特定功能（稀疏注意力、系统消息处理）进行修正。安全提交（#58832, #58830）加固了输入处理。这些变更是实现“**Easy**”和稳定服务的基础，确保用户能可靠地部署各种模型。
*   **工程效率与代码健康**：CI优化（#58810, #58749, #58609）旨在提升测试效率与稳定性，为快速迭代提供保障。重构（#58803）与类型修复（#58046）则维护了代码库的清晰度与可维护性，支持项目的长期健康发展。

### 3. 对项目的影响和潜在意义
这些提交共同强化了vLLM作为高性能、高可靠性LLM推理引擎的地位。性能优化直接提升了用户体验；Bug修复和安全加固增强了生产环境下的可信度；对新硬件和模型的支持拓宽了项目边界；工程层面的改进则保障了项目自身的可持续迭代能力。

### 4. 值得关注的技术点
*   **内核级融合**：将MoE的finalize操作融合到Tensor Parallel的all-reduce操作中，是追求极致性能的体现。
*   **精度与状态管理**：将FlashAttention的循环状态保持为fp32，这是在性能与数值稳定性之间做出的重要权衡。
*   **前端复杂逻辑处理**：针对Anthropic模型系统消息合并与思考模式的多次修复，显示了在前端消息处理逻辑上的复杂性和持续完善。
*   **弹性伸缩**：修复EPLB的负载统计问题，对实现生产级的大规模弹性部署至关重要。

### 5. 基于项目背景的影响总结
vLLM的目标是提供“易用、快速、便宜”的LLM服务。此次提交集中体现了这一追求：通过**内核优化和架构支持**持续攻克性能瓶颈；通过**广泛而深入的Bug修复与安全加固**提升服务的稳定性和安全性，降低用户的使用门槛；通过**CI和重构**夯实工程基础。这些看似分散的变更，共同推动了vLLM在**性能、兼容性、可靠性和可维护性**上的全面演进，使其能更好地服务于日益增长的LLM部署需求。来自Red Hat、NVIDIA等核心贡献者的参与也表明，项目正得到产业界的强力支持，发展方向与生产环境的需求紧密结合。

## 详细提交记录

### [4be061c](https://github.com/vllm-project/vllm/commit/4be061c5afab75d8f36f83db48097776eb936a34)

- **作者**: simon-veitner-redhat
- **时间**: 2026-09-26T22:20:44Z
- **提交信息**: [Kernel] Bump FlashKDA to keep the recurrent state in fp32 (#58846)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [927c87b](https://github.com/vllm-project/vllm/commit/927c87b3472a39da79a95a8df12d0a2b21e2d32e)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-26T22:12:35Z
- **提交信息**: [PCP][DCP] Support DCP target model with non-DCP Dspark (#56723)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>

### [7787112](https://github.com/vllm-project/vllm/commit/77871126f9b69cff9feffff390d1171a60dbd7e2)

- **作者**: Yongye Zhu
- **时间**: 2026-09-26T19:08:36Z
- **提交信息**: [Kernel][DSV4.1] Fuse MoE finalize into the TP all-reduce + mHC boundary (#58586)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [379e9a1](https://github.com/vllm-project/vllm/commit/379e9a1ea8a5995464d9bf775bcd36bb03a0995f)

- **作者**: Cyrus Leung
- **时间**: 2026-09-26T16:28:32Z
- **提交信息**: [Security] Harden message sanitization (#58832)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [7d8c5fe](https://github.com/vllm-project/vllm/commit/7d8c5fe9a95dd7a9734f05fdbad57c1ad61f77fe)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-26T15:37:36Z
- **提交信息**: [Bugfix][DSV4.1] Avoid host sync in ViT CUDA graph replay metadata (#58499)

### [0239bd2](https://github.com/vllm-project/vllm/commit/0239bd2549224a4bc4245ba5a70e7acb120cbeb7)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-26T15:35:56Z
- **提交信息**: [CI] Stabilize batch submission in full CUDA graph tests (#58810)

### [3576691](https://github.com/vllm-project/vllm/commit/3576691c426ea7565789da98b8440600f8ca488e)

- **作者**: Wentao Ye
- **时间**: 2026-09-26T15:35:28Z
- **提交信息**: [GLM5.3 Bug] Fix sparse indexer attn topk backend selection (#58594)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [79ac28c](https://github.com/vllm-project/vllm/commit/79ac28c5bd363d243ff2dea39306b568f59d4153)

- **作者**: Misha Goin
- **时间**: 2026-09-26T15:22:33Z
- **提交信息**: [CI] Reduce CUDA graph mode test overhead (#58749)

### [5113cf9](https://github.com/vllm-project/vllm/commit/5113cf9d168cf71b1573c69500f884b0bccbad89)

- **作者**: Ashraf Bhuiyan
- **时间**: 2026-09-26T14:31:51Z
- **提交信息**: [Mypy] Fix mypy typing for Qwen and Qianfan models (#58046)

Signed-off-by: Ashraf Bhuiyan <mbhuiyan@redhat.com>

### [dfab504](https://github.com/vllm-project/vllm/commit/dfab5043336cfae4739d3d0ae54047463e26f17d)

- **作者**: Robert Shaw
- **时间**: 2026-09-26T14:00:56Z
- **提交信息**: [Bugfix][Frontend] Detect Anthropic inline-system merge against the resolved chat template (#58754)

Signed-off-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>

### [d64f277](https://github.com/vllm-project/vllm/commit/d64f277c54d444284bdbcd16e7fd1073b0a3b50e)

- **作者**: Robert Shaw
- **时间**: 2026-09-26T13:50:57Z
- **提交信息**: [Bugfix] Fix Anthropic Thinking Disabled with P/D (#58786)

Signed-off-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>

### [ad6817b](https://github.com/vllm-project/vllm/commit/ad6817b68d9b1d138eca2033cf90233bd0100bf3)

- **作者**: Willian Z
- **时间**: 2026-09-26T13:48:24Z
- **提交信息**: [Perf][MoE] Index expert mapping lookups in RoutedExperts.load_weights (#58720)

Signed-off-by: Willian <willian@willian.email>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [bf93e1f](https://github.com/vllm-project/vllm/commit/bf93e1f92c40673454c938b277a0a99d49662657)

- **作者**: Wentao Ye
- **时间**: 2026-09-26T13:16:53Z
- **提交信息**: [Refactor] Remove dead tests utils (#58803)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [2bb7605](https://github.com/vllm-project/vllm/commit/2bb7605ae197d54fdf04f4364cddfc97962b7fcd)

- **作者**: Itay Alroy
- **时间**: 2026-09-26T12:05:37Z
- **提交信息**: [Elastic EP] Fix EPLB load statistics during scaling (#58473)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [31f2e70](https://github.com/vllm-project/vllm/commit/31f2e70cd3e403aaa471fb7fe3d33a7207aaf3cc)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-09-26T11:10:35Z
- **提交信息**: [Security] Gate per-request multimodal processor kwargs (#58830)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [2f41e00](https://github.com/vllm-project/vllm/commit/2f41e002351188284885282a374a16e6c0136d4d)

- **作者**: Thang Nguyen
- **时间**: 2026-09-26T11:10:14Z
- **提交信息**: [CI] Split (B200) Miscellaneous Kernels into mHC, FLA Ops and Misc named jobs (#58609)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [a4eb3f2](https://github.com/vllm-project/vllm/commit/a4eb3f25d6f9b3cad7ecf5390423d853935fcaeb)

- **作者**: qizixi
- **时间**: 2026-09-26T09:01:17Z
- **提交信息**: [Spec Decode] Enable Gemma4 DSpark adaptive verification with FlashInfer (#57263)

Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-27
**监控日期**: 2026-09-26
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7074
- **最后更新**: 2026-09-26T22:33:17Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 5
- **主要提交者**: Tianyao Wu, R0CKSTAR, Sy03

## AI分析总结

### 1. 主要更新类型
本次提交以**功能增强**和**性能优化**为主，同时包含**代码重构**和**维护性清理**。没有明确的Bug修复或文档更新。

### 2. 关键变更点及其与项目整体方向的关系
*   **性能与吞吐量优化**：
    *   为扩散模型（如Boogu-Image）启用了**请求级批处理**，直接提升了多模态生成任务的吞吐效率。
    *   针对**Qwen3-TTS模型**的流式处理进行了优化，旨在降低首字节音频延迟并提升整体吞吐。这些变更直接服务于项目“快速、便宜”的服务目标。
*   **可控性与可扩展性增强**：
    *   允许通过**环境变量配置Torch Dynamo的重编译限制**，为开发者提供了更精细的性能调试与优化控制手段。
    *   在扩散模型的**块传输中加入字节背压机制**，增强了系统在异步和分布式场景下的稳定性和资源管理能力。
*   **架构清晰化与维护**：
    *   重构了扩散模型中**卸载策略的读取位置**，将其从配置层外移，使架构层次更清晰，便于维护和扩展。
    *   移除了一个过时的离线示例代码，属于常规的项目维护。

### 3. 对项目的影响和潜在意义
这些提交显著增强了`vllm-omni`在**多模态模型服务**场景下的核心能力。通过批处理、流式优化和传输机制改进，项目在处理图像生成、语音合成等复杂任务时，有望实现更低的延迟和更高的资源利用率。架构上的优化也为未来接入更多模态和模型奠定了更清晰的基础。整体上，这些变更推动项目朝着**更高效、更稳定、更易于调优**的方向发展，巩固了其作为通用多模态服务引擎的定位。

### 4. 值得关注的技术点
*   **请求级批处理**：将同一请求内的多个生成任务进行批处理，是提升扩散模型服务效率的关键技术。
*   **字节背压机制**：在网络或组件速度不匹配时进行流量控制，是保障分布式系统稳定的重要设计。
*   **Torch Dynamo配置外部化**：将PyTorch编译器的关键参数暴露给用户，体现了对性能敏感场景的深度支持。

### 5. 基于README的项目背景与发展影响
`vllm-omni`的目标是实现“简单、快速、便宜”的**全模态模型服务**。此次提交中，对扩散模型和TTS模型的专门优化，直接回应了项目处理**多模态生成与理解**的核心任务。性能优化和架构重构使得服务核心引擎更加健壮和高效，降低了单次请求的资源消耗和成本。可控性增强则让高级用户能根据硬件和负载情况灵活调整，更好地实现了“为每个人服务”的易用性与适用性目标。这些改进共同增强了项目在多模态AI应用落场景中的竞争力。

## 详细提交记录

### [6715c57](https://github.com/vllm-project/vllm-omni/commit/6715c57b2dffbf4623c0acb7a72862ddb9e54cb7)

- **作者**: R0CKSTAR
- **时间**: 2026-09-26T14:54:47Z
- **提交信息**: feat: configure Torch Dynamo recompile limit from environment (#7243)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [d418004](https://github.com/vllm-project/vllm-omni/commit/d418004b6ba6391a354cf910c98b739ed38f0dea)

- **作者**: Tianyao Wu
- **时间**: 2026-09-26T14:54:06Z
- **提交信息**: [Misc] Remove stale offline word_timestamps example resurrected by #5146 (#7233)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>

### [eb67caa](https://github.com/vllm-project/vllm-omni/commit/eb67caaaa973cd8d84dcdc7d2fdd23e6dd3ea006)

- **作者**: Shenglei Fu
- **时间**: 2026-09-26T14:53:35Z
- **提交信息**: [Diffusion] Enable request-level batching for Boogu-Image (TI2I) (#7227)

Signed-off-by: Shenglei Fu <sfu@confluent.io>
Signed-off-by: Shenglei Fu <117230642+ShengleiFu@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e75278d](https://github.com/vllm-project/vllm-omni/commit/e75278dccc36ae894159d519f18c3b3db578a8bd)

- **作者**: R0CKSTAR
- **时间**: 2026-09-26T14:53:04Z
- **提交信息**: feat(magi2): add fused SwiGLU7 activation (#7252)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [e1303e5](https://github.com/vllm-project/vllm-omni/commit/e1303e5067bb5617eb12d4cb291aef6eb8b42634)

- **作者**: Sy03
- **时间**: 2026-09-26T14:51:04Z
- **提交信息**: [Model] Optimize Qwen3-TTS streaming throughput and first audio on CUDA (#8163)

Signed-off-by: Sy03 <1370724210@qq.com>

### [8a49c65](https://github.com/vllm-project/vllm-omni/commit/8a49c65bf9e477338173339540186577086d1cf4)

- **作者**: Anjie Hou
- **时间**: 2026-09-26T09:48:32Z
- **提交信息**: [Core][Diffusion] Add byte backpressure to chunk transfers (#7916)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [acf6620](https://github.com/vllm-project/vllm-omni/commit/acf66202333ff837c058a0957c778ca14a1460da)

- **作者**: Anjie Hou
- **时间**: 2026-09-26T09:45:20Z
- **提交信息**: [Refactor][Diffusion] Read the resolved offload policy outside the config layer (#7327)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
