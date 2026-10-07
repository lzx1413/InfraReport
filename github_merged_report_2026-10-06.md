# GitHub Stars 合并报告 - 2026-10-06

**合并日期**: 2026-10-07
**监控日期**: 2026-10-06
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


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2233
- **最后更新**: 2026-10-05T18:27:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2881
- **最后更新**: 2026-10-06T22:28:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2284
- **最后更新**: 2026-10-06T16:59:43Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6552
- **最后更新**: 2026-10-07T01:29:46Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 9
- **主要提交者**: Yanqin Zhai, Vincent, Luke Alonso

## AI分析总结

# FlashInfer 昨日提交综合分析

## 一、主要更新类型

昨日 26 个提交以**性能优化和 Bug 修复**为主导，兼顾功能新增与代码重构。性能优化覆盖 CAKE 团队内核（routing-gate、projection GEMM、MLA decode、varlen attention、MoE finalize allreduce fusion）、Kimi-K3 FP8/NVFP4 投影路径及主机端调度开销；修复类集中在 allreduce 通信正确性与注意力数值稳定性；功能新增包括 Rubin (SM107) 硬件适配、Frost 后端转正、SM100 ReplaySSM 投机解码内核，以及 DeepSeek-V4 NVFP4 稀疏 MLA 解码路径。

## 二、关键变更点

**硬件覆盖扩展**：针对 SM90/SM100/SM103/SM107/SM120 等多代架构持续优化，trtllm-gen BMM 预编译包升级为 Rubin 原生 2xfp8/4xfp4 MMA-K 核，最高带来 1.78x 加速；SM120/SM121 稀疏 MLA 与新增的 NVFP4 路径共享量化缓存 ABI，实现跨架构复用。

**模型专项适配**：Kimi-K3 成为优化主线，FP8/NVFP4 投影 GEMM 与 MLA 解码已超越上游基线（最高 1.268x）；DeepSeek-V4 稀疏 MLA 解码在 Blackwell 上以 `backend="cake"` 显式启用，支持 384 B/token KV 缓存，通过 `trtllm_batch_decode_sparse_mla_dsv4` 公共 API 暴露，保持调用兼容性。

**正确性修复**：修复了 Kimi-K3 MLA FP8 paged attention 中 attention-sink keys 引发的 Inf/NaN 溢出；两阶段 allreduce 的屏障顺序错误导致 token 递增时最多 66% 结果错误，及 fp32 缓冲区按 2 字节元素硬编码的越界写——二者均已修复，前者还因合并 release 指令带来 8–67% 通信提速。稀疏 MLA 的 DSv4 稀疏有效性语义、workspace 契约与 FP8 概率缩放也已对齐。

**自动化与工程化**：`backend="auto"` 在特定条件下自动采用 cuDNN 引擎处理多 token paged-decode；b12x 实验模块整体迁入 `flashinfer.experimental.b12x`；大量 regenerating + sealed export receipts 流程，配合模板化变体索引与统一分派表，形成以生成器为中心的工程化内核开发模式。

## 三、项目影响

**生产可靠性**：修复静默错误（allreduce 结果错误、数值溢出）避免下游 vLLM/sglang 产出不可察觉的错误推理，Kimi-K3 等旗舰模型的稳定性显著提升。

**性能竞争力**：MLA 解码、MoE、投影 GEMM 在生产形状上超越 SOTA 基线；主机端开销大幅下降（KDA prefill 输出别名校验降低约 73%，launch 开销从 ~117µs 降至 ~26µs），CUDA-Graph 兼容的零分配设计强化了部署友好性。

**生态整合**：Frost 转正与 b12x 模块化表明项目正将实验算力资产整合为稳定公共 API，降低外部框架集成成本；NVFP4 稀疏 MLA 为后续多精度混合内核建立可复用的生成与 ABI 模板。

## 四、值得关注的技术点

- **同步原语与性能耦合**：allreduce 屏障修复采用"他槽先写、本槽最后以系统级 release 写"，同时省掉 255 次系统指令。
- **混合精度组合**：NVFP4 块缩放 MMA（E2M1 + 每 16 值一个 E4M3 scale）与 FP8 PV 路径共存，配以 fp32 在线 softmax 保证精度。
- **内核级微优化**：DSM partial exchange 并行发射、FP8 token ring、TwoSum 补偿求和、CTA 本地桶选择、TMA 单次复制、持久化线程划分等技术在精度前提下提升吞吐。
- **寄存器与调度管理**：`__launch_bounds__` 声明寄存器预算，CUDA graph 兼容的 launcher 缓存与一次性计划降低主机开销。
- **投机解码状态重建**：ReplaySSM 以冻结 FP32 checkpoint + 窗口回放 + 单次 commit 替代全量状态存储。
- **质量门槛体系**：位精确验证、compute-sanitizer、GSM8K 一致性测试与导出配对计时构成严谨的发布门禁。

## 五、总结

这批提交推动 FlashInfer 从专注特定计算原语的内核库，向跨架构、跨模型、可验证可维护的高性能推理平台演进：对前沿模型与最新 GPU 的深度优化保持性能领先，正确性修复与工程化体系夯实生产可靠性，cuDNN 集成与实验模块收编降低了集成与维护成本，为其成为推理基础设施的事实标准内核库奠定基础。

## 详细提交记录

### [50a180e](https://github.com/flashinfer-ai/flashinfer/commit/50a180ed0ae1195305a3c17ab1508875796a2ba5)

- **作者**: eigen
- **时间**: 2026-10-06T22:48:12Z
- **提交信息**: fix(cake_kimi_k3_mla): bound the lazy E4M3 reference drop on the row-tile kernels (Inf/NaN rows with attention-sink keys); regenerate SM100 / SM103 (#6126)

Developed by the **CAKE team**.

## Summary

Fixes an Inf/NaN defect in the `backend="cake"` Kimi-K3 MLA FP8 paged
attention decode route (#5552, #5602, #5871) and regenerates the
programs of both architectures from the fixed producer. The host side
(`flashinfer/mla/cake_kimi_k3_mla.py`, planner, grids, kernel arguments)
is unchanged; this PR moves only the generated program sources, the jit
registry and the test file.

**Defect.** Serving Kimi-K3 with FP8 KV cache produced rows of `inf` /
`nan` output for some requests in a batch while the same requests alone,
or with a different batch composition, were fine. Real Kimi-K3 KV caches
contain an attention-sink key (token 0) whose score sits ~115-125
octaves above every other key for most heads. The swapped-AB row-tile
kernels (RT 16/32/48/64/96, the H12 decode and MTP routes) keep one lazy
E4M3 reference per softmax warpgroup and re-reference every column of
the warpgroup to the exceeding column's own tile maximum. A column
without a sink (a head whose query does not attend the sink, or a
padding column that reads the next request's query rows inside the
batch) exceeds on a later tile, the whole warpgroup moves its reference
down by ~118 octaves, the FP32 rescale `alpha = 2^118` overflows the
running sum and the O^T accumulator, and the merged row becomes Inf/NaN.
This is why the failure depended on the batch and reproduced with
`num_split=1`.

**Fix (kernel only).** Each softmax column keeps its running maximum in
SMEM (the slot previously used for a dead column-sum write, so the SMEM
carve-up and ring depths are unchanged) and the reference may never drop
more than 32 octaves below the column's running maximum. Moves below 32
octaves are bit-identical to the previous programs; a sink column
therefore keeps its reference near the sink and the non-sink columns of
its warpgroup are only clamped where their mass is already below 2^-32
of the row. The wide two-CTA route (H96 decode, prefill) uses a monotone
running maximum and is not affected; its programs are regenerated from
the same producer and are byte-identical apart from the shared headers.

## Tests

- New `test_decode_sink_key_rows` in
`tests/mla/test_cake_kimi_k3_mla.py`: sink key (+2.0 on all 576 channels
at token 0) with sink-attending query heads at +1.25 (~150 octaves above
the random keys), H12 batch 1 and the 8-request 11-14-page band that
reproduced the failure, H96 two-request and long-request cases, checked
against an FP32 reference at FP8-class tolerance (atol/rtol 0.1) plus
relative L2 <= 0.05. The previous programs fail these cases with Inf/NaN
rows; the regenerated programs pass.
- `tests/mla/test_cake_kimi_k3_mla.py`: 38 passed (34 existing + the 4
new sink cases) on B200, 38 passed on B300 on the generated programs of
this PR.
- `tests/attention/test_trtllm_gen_mla.py -k trtllm_mla_blackwell`
(dispatch regression): 27 passed on B200; 27 passed on B300.
- Export receipts (source-vs-generated host-plan and bitwise output
parity plus ABBA CUPTI timing gates; 27 perf rows + 2 coverage rows per
architecture): 27 / 29 rows pass after a closed-prior retry round
(source/export geomean 0.9997; 28 timed-correct) on B200; 28 / 29 rows
pass (source/export geomean 1.0020) on B300. The refusals are
measurement-validity gates, not parity or correctness failures:
`prefill_h96_b1_q2048_kv131072` on both GPUs is the exporter's
loaded-SM-clock gate under the sustained power cap (1245 / 1965 MHz on
B200, 1170 / 2032 MHz on B300, below the 0.70 fraction; the same row and
gate as every previous head of this family), reproduced by a
closed-prior retry round on B300 (1192 / 2032 MHz) and on B200 (1207 /
1965 MHz); on B200 `mirror_h96_b1_q1_kv76800` (the shortest wide row,
~24 us) fails the paired ABBA `directional_disagreement` gate in both
the first run and the closed-prior retry while bitwise parity holds
(source/export 1.0053, then 0.9816 with the sign flipped), the
arm-position offset of the paired harness on short rows already
disclosed for this row in #5602; `mirror_h96_b2_q1_kv77699` hit the same
gate in the first run (1.0096) and passed in the retry. The B200 and
B300 exporter runs delivered byte-identical files (the two delivered
patches have the same SHA-256; 21 program sources + README + jit
registry). The wide decode kernel's two architecture lowerings now fold
into one source under `__CUDA_ARCH__` guards like every other kind, so
the registry carries one `main_wide` program instead of two.
- Producer-side evidence for the fix: the 8 layer-91 decode reproducer
dumps (batch 64, H12) are finite with the fix and match an FP32
reference at FP8-class tolerance (previously 2 of 8 had Inf/NaN rows);
the 10 pre-existing contract correctness rows are unchanged (6 bitwise
identical, 4 peaked rows differ only in elements below 1.3e-17); paired
perf A/B on the fixed vs previous kernel over the H12 decode / MTP rows:
geomean 1.0005 (within noise).

## Performance

No host or schedule change; the bound costs one `max`, one compare and
one select per column per tile on the softmax warps and never fires on
the benchmark rows. Export receipts above show source and generated
programs within 0.2 % on every measured row.

## Unsupported (rejected explicitly)

Unchanged from #5552 / #5602.

<details><summary>Export receipts (29 rows per architecture, source vs
generated: same-session ABBA CUPTI cold-L2 medians, CUDA-graph replay;
B200 column from the closed-prior retry round, B300 column from the
first run whose single refusal the retry reproduced)</summary>

| row | route | sm_100a source us | sm_100a export us | sm_100a src/exp
| sm_100a verdict | sm_103a source us | sm_103a export us | sm_103a
src/exp | sm_103a verdict |
|---|---|---:|---:|---:|---|---:|---:|---:|---|
| mtp_h12_fixed_q5 | main_rt64_reduce_w2 | 271.0 | 270.6 | 1.0014 | PASS
| 262.7 | 262.7 | 1.0001 | PASS |
| mtp_h96_fixed_q8_kv8000 | main_rt96_reduce_w1 | 141.8 | 141.9 | 0.9995
| PASS | 125.6 | 125.1 | 1.0038 | PASS |
| trace_h12_b1_q1_kv76800 | main_rt16_reduce_cta | 22.0 | 21.3 | 1.0285
| PASS | 21.8 | 20.8 | 1.0476 | PASS |
| trace_h12_b2_q1_kv77699 | main_rt16_reduce_cta | 29.3 | 29.3 | 1.0000
| PASS | 29.0 | 29.0 | 1.0022 | PASS |
| trace_h12_b3_q1_kv261120 | main_rt16_reduce_cta | 89.9 | 90.0 | 0.9993
| PASS | 90.7 | 90.8 | 0.9989 | PASS |
| trace_h12_b4_q1_kv268800 | main_rt16_reduce_cta | 111.8 | 111.7 |
1.0006 | PASS | 113.3 | 113.2 | 1.0011 | PASS |
| trace_h12_b5_q1_kv276480 | main_rt16_reduce_w4 | 137.5 | 137.8 |
0.9977 | PASS | 139.9 | 140.2 | 0.9977 | PASS |
| trace_h12_b6_q1_kv467751 | main_rt16_reduce_w4 | 249.8 | 249.9 |
0.9997 | PASS | 256.1 | 255.7 | 1.0013 | PASS |
| trace_h12_b7_q1_kv299613 | main_rt16_reduce_w4 | 194.4 | 194.1 |
1.0013 | PASS | 197.4 | 197.2 | 1.0015 | PASS |
| trace_h12_b8_q1_kv342305 | main_rt16_reduce_w4 | 244.7 | 244.9 |
0.9995 | PASS | 250.6 | 250.7 | 0.9996 | PASS |
| trace_h12_b9_q1_kv348705 | main_rt16_reduce_w4 | 274.4 | 274.8 |
0.9986 | PASS | 279.9 | 280.2 | 0.9989 | PASS |
| trace_h12_b10_q1_kv474166 | main_rt16_reduce_w4 | 405.0 | 405.0 |
1.0001 | PASS | 413.8 | 413.7 | 1.0003 | PASS |
| trace_h12_b11_q1_kv474405 | main_rt16_reduce_w4 | 439.6 | 439.5 |
1.0001 | PASS | 449.8 | 449.7 | 1.0001 | PASS |
| mirror_h96_b1_q1_kv76800 | main_wide_reduce_cta | — | — | — | FAIL:
failed gates: directional_disagreement | 23.0 | 22.9 | 1.0028 | PASS |
| mirror_h96_b2_q1_kv77699 | main_wide_reduce_cta | 33.0 | 33.6 | 0.9819
| PASS | 33.3 | 33.0 | 1.0087 | PASS |
| mirror_h96_b6_q1_kv467751 | main_wide_reduce_w2 | 290.3 | 290.0 |
1.0011 | PASS | 285.0 | 285.2 | 0.9992 | PASS |
| mirror_h96_b7_q1_kv299613 | main_wide_reduce_w2 | 220.2 | 220.0 |
1.0012 | PASS | 218.4 | 218.7 | 0.9984 | PASS |
| mirror_h96_b8_q1_kv342305 | main_wide_reduce_w2 | 281.4 | 281.2 |
1.0010 | PASS | 277.8 | 278.1 | 0.9991 | PASS |
| mtp_h12_b8_q2_kv342305 | main_rt32_reduce_w4 | 249.3 | 249.6 | 0.9987
| PASS | 252.5 | 252.8 | 0.9991 | PASS |
| mtp_h12_b8_q4_kv342305 | main_rt48_reduce_w2 | 262.0 | 262.1 | 0.9995
| PASS | 259.1 | 259.2 | 0.9996 | PASS |
| mtp_h12_b8_q8_kv342305 | main_wide_reduce_w2 | 282.3 | 282.0 | 1.0008
| PASS | 277.3 | 277.7 | 0.9986 | PASS |
| mtp_h96_b8_q2_kv342305 | main_wide_reduce_w1 | 549.6 | 549.3 | 1.0006
| PASS | 507.0 | 506.9 | 1.0003 | PASS |
| mtp_h96_b8_q4_kv342305 | main_wide_reduce_w1 | 833.4 | 833.0 | 1.0005
| PASS | 769.3 | 769.3 | 1.0000 | PASS |
| mtp_h96_b8_q8_kv342305 | main_wide_reduce_w1 | 1613.4 | 1612.8 |
1.0003 | PASS | 1593.6 | 1593.8 | 0.9999 | PASS |
| prefill_h12_b1_q2048_kv131072 | main_wide_reduce_w1 | 2378.9 | 2378.9
| 1.0000 | PASS | 2351.6 | 2351.7 | 1.0000 | PASS |
| prefill_h12_b2_q512_kv32768 | main_wide_reduce_w1 | 300.5 | 300.9 |
0.9988 | PASS | 278.8 | 279.3 | 0.9980 | PASS |
| prefill_h12_b4_q1024_kv8192 | main_wide_reduce_w1 | 309.2 | 308.8 |
1.0013 | PASS | 285.2 | 285.2 | 1.0001 | PASS |
| prefill_h96_b1_q2048_kv131072 | main_wide_reduce_w1 | — | — | — |
FAIL: InterleavedTimingError: reportable loaded SM clock 1207/1965 MHz
is below the 0.700000 fraction gate | — | — | — | FAIL:
InterleavedTimingError: reportable loaded SM clock 1192/2032 MHz is
below the 0.700000 fraction gate |
| prefill_h96_b2_q512_kv32768 | main_wide_reduce_w1 | 2402.8 | 2402.7 |
1.0000 | PASS | 2380.4 | 2379.8 | 1.0002 | PASS |

</details>

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Improvements**
* Improved numerical stability for FP8 paged attention, including cases
with dominant sink scores.
* Reduced repeated CUDA device setup during kernel execution and updated
launch handling.
  * Unified wide-kernel selection across SM100 and SM103 architectures.

* **Tests**
* Added decode coverage across multiple head counts and KV lengths, with
checks against an FP32 reference.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0feacf4](https://github.com/flashinfer-ai/flashinfer/commit/0feacf4c22f74c0385f958254d8d03c3b4776669)

- **作者**: Vedaanta Agarwalla
- **时间**: 2026-10-06T22:30:54Z
- **提交信息**: feat(cudnn): backend="auto" takes cuDNN for the multi-token paged-decode rows its default FROST engine serves faster (cudnn-frontend 1.30+) (#5508)

<!-- .github/pull_request_template.md -->

## 📌 Description

`BatchDecodeWithPagedKVCacheWrapper(backend="auto")` takes cuDNN for the
multi-token decode rows (speculative / MTP verification, `2 <=
q_len_per_req <= 4`) of fp16 / bf16 head_dim-128 GQA models on SM100 /
SM103 when cudnn-frontend 1.30+ is installed, inside the envelope where
cuDNN's FROST decode tile measured at 0.35-0.95x fa2's tensor-core
decode on B200. Everything else `auto` did before is unchanged. No new
environment variable is needed: the frontend's SM100 engine that serves
these rows is one of its default engines.

### How cuDNN serves FlashInfer's decode graphs on cudnn-frontend 1.30
(no flags)

cudnn-frontend 1.30.0 ranks its default SM100 f16/bf16 CuTe-DSL
("FROST") SDPA engine against the classic backend engine per shape. For
the paged-decode graphs this wrapper builds, measured through the
wrapper (B200, cuDNN 9.26, bf16, page 16, CUDA-graph replay, kernel
time):

- multi-token rows (`q_len_per_req` 2..4): the FROST decode tile, one
128-row CTA per (batch, KV head) unit packing the GQA group's rows; the
backend engine has no decode-class path for them (its prefill-class
engine is ~8x slower than fa2);
- an attention sink at `q_len_per_req == 1` (gpt-oss decode): the
backend engine declines at plan time and the frontend falls through to
the FROST row, so sinks just work on 1.30+ (verified:
`test_cudnn_wrapper_sinks_match_reference` passes on the 1.30 wheel with
nothing set; on 1.29 it still skips with the backend's decline);
- single-token d128 decode: the backend decode engine, which the
frontend ranks ahead of the FROST tile there.

### The `auto` rule (`_auto_decode_prefers_cudnn`, a pure predicate over
plan() arguments)

- SM100 / SM103, cudnn-frontend >= 1.30.0 importable, fp16 / bf16 with
uniform q / kv / o dtype, `head_dim` 128, a GQA group that divides 128,
`page_size` a multiple of 8 that divides 128 or is a multiple of it, no
RoPE / soft-cap / sliding window;
- `2 <= q_len_per_req <= 4` with `q_len_per_req * group` in [32, 128]
rows per CTA and `batch_size * num_kv_heads >= 64` CTAs.

Why those two bounds, from the matrix below: with 16 rows per CTA (64/8
at two rows) the tile loses 1.0-1.7x at every batch from 8 and every
cache; with 32 CTAs (64/4 at b=8) it loses 1.2x at a 1k cache and only
wins from 4k; at b=1 it is about 2x slower. Single-token decode stays on
fa2 because the engine that would serve it (the backend decode engine)
is mixed against fa2: 0.7-1.1x at b=32 but 1.3-1.8x at b=128 for 64/4.
d256 (Qwen3.5 32/2) stays on fa2: 0.65-1.1x at b=32, 1.2-3x below.
GLM-4.5's 96/8 (group 12, partial packing) is 1.1-1.9x slower.

`FLASHINFER_DECODE_AUTO_CUDNN` overrides the choice: `0` never resolves
to cudnn, `1` applies the rule on an older frontend too (benchmarking /
bisection). `wrapper.resolved_backend` reports the choice (the benchmark
harness prints `auto(cudnn)`).

Under CUDA graphs `auto` takes cuDNN only when `plan()` receives a
caller-owned `block_tables` (the auto-built table is captured at its
first width and `_plan_cudnn` raises when a later plan crosses the
declared-length bucket, while fa2 replans inside its preallocated
buffers) or when fa2 cannot serve the rows (multi-token without tensor
cores); the resolution is then part of the frozen graph shape and a
later `plan()` that would flip it raises instead of replaying stale
metadata. `fast_decode_plan` applies the same selector on its plan's
geometry before trusting the cached FA2 module.

Also in this PR: the declared KV length the cudnn path buckets to is now
2048 tokens instead of 1024. cudnn-frontend 1.30's placement ranks the
FROST decode tile ahead of the backend for multi-token rows only from a
declared 2048-token cache, so a 1024 bucket would have sent short caches
to the backend's prefill-class engine (409 us vs 24 us for 64/4 at b=32
with 1000 live tokens). The frontend-side fix (FROST first at every
cache length for multi-token rows) is NVIDIA/cudnn-frontend#1420.

Plumbing from earlier revisions: `_requested_backend` / `_cudnn_auto` /
`_uses_cudnn` / `resolved_backend`, lazy `_kv_lens_buffer`, dtype
canonicalization ahead of the `q_len_per_req` check, the shared selector
for `plan()` / `workspace_size()` / `fast_decode_plan` (follow-up
commits by @YangXu1990uiuc also bind a strided single-token Q as a
zero-copy BHSD view, fixing packed-QKV queries on the 1.30 wheel).
`cudnn_frontend_version()` and `cudnn_frontend_serves_frost_decode()`
live in `flashinfer/cudnn/utils.py`.

### Numbers

B200 (148 SMs), cudnn-frontend 1.30.0 wheel + cuDNN 9.26, nothing set in
the environment, bf16, page 16, HND, through the wrapper with
`bench_gpu_time` (CUDA-graph replay, 20 timed iterations, median, kernel
time). `cudnn` is `backend="cudnn"` (what `auto` resolves to inside the
envelope); `fa2` is the tensor-core decode `auto` resolved to before.
Ratios are cudnn / fa2; bold rows are inside the new `auto` envelope.

| shape, rows | b | 1k cache | 4k cache | 16k cache |
|---|---|---|---|---|
| 64/4 d128, 2 rows | 8 | 24 / 20 (1.23) | 35 / 40 (0.88) | 78 / 153
(0.51) |
| 64/4 d128, 2 rows | 32 | **24 / 50 (0.48)** | **65 / 139 (0.47)** |
**480 / 533 (0.90)** |
| 64/4 d128, 2 rows | 128 | **82 / 126 (0.65)** | **482 / 530 (0.91)** |
**1878 / 2046 (0.92)** |
| 64/4 d128, 4 rows | 8 | 29 / 23 (1.25) | 41 / 43 (0.94) | 83 / 133
(0.62) |
| 64/4 d128, 4 rows | 32 | **24 / 65 (0.37)** | **65 / 184 (0.35)** |
**220 / 529 (0.42)** |
| 64/4 d128, 4 rows | 128 | **82 / 156 (0.53)** | **504 / 546 (0.92)** |
**1928 / 2067 (0.93)** |
| 64/8 d128, 2 rows | 8 | 23 / 21 (1.10) | 47 / 45 (1.04) | 234 / 192
(1.21) |
| 64/8 d128, 2 rows | 32 | 45 / 36 (1.24) | 126 / 105 (1.20) | 906 / 713
(1.27) |
| 64/8 d128, 2 rows | 128 | 228 / 137 (1.66) | 929 / 663 (1.40) | 3764 /
3614 (1.04) |
| 64/8 d128, 4 rows | 8 | **26 / 29 (0.88)** | **47 / 69 (0.68)** |
**217 / 251 (0.87)** |
| 64/8 d128, 4 rows | 32 | **44 / 60 (0.74)** | **182 / 247 (0.74)** |
**949 / 1027 (0.92)** |
| 64/8 d128, 4 rows | 128 | **140 / 260 (0.54)** | **946 / 1025 (0.92)**
| **3833 / 4127 (0.93)** |

Cells are cuDNN / fa2 in microseconds (ratio). The 1k cache is 1000 live
tokens with 2048 declared.

Full matrix (all batches 1-128, three cache lengths, 64/4, 64/8,
32/2-d256 and 96/8, one, two and four rows) is in the collapsed section.

<details><summary>Full matrix</summary>

| shape, rows | b | 1k cache | 4k cache | 16k cache |
|---|---|---|---|---|
| 64/4 d128, 2 rows | 1 | 24 / 13 (1.85) | 32 / 15 (2.15) | 51 / 27
(1.89) |
| 64/4 d128, 2 rows | 4 | 26 / 15 (1.71) | 31 / 26 (1.19) | 54 / 67
(0.80) |
| 64/4 d128, 2 rows | 8 | 24 / 20 (1.23) | 35 / 40 (0.88) | 78 / 153
(0.51) |
| 64/4 d128, 2 rows | 32 | **24 / 50 (0.48)** | **65 / 139 (0.47)** |
**480 / 533 (0.90)** |
| 64/4 d128, 2 rows | 128 | **82 / 126 (0.65)** | **482 / 530 (0.91)** |
**1878 / 2046 (0.92)** |
| 64/4 d128, 4 rows | 1 | 26 / 13 (2.03) | 35 / 14 (2.45) | 54 / 27
(2.01) |
| 64/4 d128, 4 rows | 4 | 25 / 16 (1.59) | 35 / 27 (1.27) | 58 / 68
(0.85) |
| 64/4 d128, 4 rows | 8 | 29 / 23 (1.25) | 41 / 43 (0.94) | 83 / 133
(0.62) |
| 64/4 d128, 4 rows | 32 | **24 / 65 (0.37)** | **65 / 184 (0.35)** |
**220 / 529 (0.42)** |
| 64/4 d128, 4 rows | 128 | **82 / 156 (0.53)** | **504 / 546 (0.92)** |
**1928 / 2067 (0.93)** |
| 64/4 d128, 1 row | 1 | 13 / 12 (1.14) | 16 / 14 (1.17) | 25 / 21
(1.17) |
| 64/4 d128, 1 row | 4 | 15 / 13 (1.17) | 24 / 20 (1.19) | 59 / 42
(1.41) |
| 64/4 d128, 1 row | 8 | 18 / 17 (1.08) | 36 / 25 (1.43) | 105 / 62
(1.68) |
| 64/4 d128, 1 row | 32 | 20 / 29 (0.69) | 53 / 69 (0.77) | 339 / 318
(1.07) |
| 64/4 d128, 1 row | 128 | 133 / 74 (1.80) | 333 / 259 (1.29) | 1426 /
1623 (0.88) |
| 64/8 d128, 2 rows | 1 | 21 / 12 (1.70) | 30 / 18 (1.65) | 41 / 26
(1.57) |
| 64/8 d128, 2 rows | 4 | 22 / 17 (1.29) | 33 / 26 (1.27) | 75 / 102
(0.74) |
| 64/8 d128, 2 rows | 8 | 23 / 21 (1.10) | 47 / 45 (1.04) | 234 / 192
(1.21) |
| 64/8 d128, 2 rows | 32 | 45 / 36 (1.24) | 126 / 105 (1.20) | 906 / 713
(1.27) |
| 64/8 d128, 2 rows | 128 | 228 / 137 (1.66) | 929 / 663 (1.40) | 3764 /
3614 (1.04) |
| 64/8 d128, 4 rows | 1 | 29 / 13 (2.20) | 41 / 18 (2.30) | 44 / 37
(1.17) |
| 64/8 d128, 4 rows | 4 | 23 / 19 (1.18) | 33 / 39 (0.86) | 74 / 110
(0.67) |
| 64/8 d128, 4 rows | 8 | **26 / 29 (0.88)** | **47 / 69 (0.68)** |
**217 / 251 (0.87)** |
| 64/8 d128, 4 rows | 32 | **44 / 60 (0.74)** | **182 / 247 (0.74)** |
**949 / 1027 (0.92)** |
| 64/8 d128, 4 rows | 128 | **140 / 260 (0.54)** | **946 / 1025 (0.92)**
| **3833 / 4127 (0.93)** |
| 64/8 d128, 1 row | 1 | 12 / 12 (1.00) | 15 / 17 (0.90) | 26 / 25
(1.06) |
| 64/8 d128, 1 row | 4 | 15 / 16 (0.90) | 27 / 24 (1.11) | 78 / 66
(1.19) |
| 64/8 d128, 1 row | 8 | 14 / 20 (0.74) | 40 / 42 (0.96) | 175 / 186
(0.94) |
| 64/8 d128, 1 row | 32 | 46 / 35 (1.30) | 104 / 163 (0.64) | 604 / 687
(0.88) |
| 64/8 d128, 1 row | 128 | 112 / 123 (0.91) | 557 / 646 (0.86) | 3484 /
3769 (0.92) |
| 32/2 d256, 2 rows | 1 | 32 / 15 (2.07) | 45 / 17 (2.67) | 71 / 28
(2.52) |
| 32/2 d256, 2 rows | 4 | 34 / 16 (2.09) | 40 / 23 (1.74) | 69 / 56
(1.23) |
| 32/2 d256, 2 rows | 8 | 31 / 17 (1.84) | 44 / 36 (1.22) | 126 / 127
(0.99) |
| 32/2 d256, 2 rows | 32 | 32 / 38 (0.83) | 91 / 140 (0.65) | 546 / 506
(1.08) |
| 32/2 d256, 2 rows | 128 | 108 / 125 (0.86) | 530 / 502 (1.06) | 2276 /
2085 (1.09) |
| 32/2 d256, 4 rows | 1 | 39 / 16 (2.51) | 53 / 17 (3.06) | 82 / 29
(2.83) |
| 32/2 d256, 4 rows | 4 | 41 / 17 (2.44) | 48 / 25 (1.95) | 77 / 62
(1.23) |
| 32/2 d256, 4 rows | 8 | 39 / 18 (2.12) | 52 / 38 (1.35) | 108 / 142
(0.76) |
| 32/2 d256, 4 rows | 32 | 31 / 44 (0.70) | 87 / 133 (0.65) | 565 / 550
(1.03) |
| 32/2 d256, 4 rows | 128 | 119 / 127 (0.94) | 619 / 554 (1.12) | 2349 /
2133 (1.10) |
| 32/2 d256, 1 row | 1 | 15 / 16 (0.97) | 18 / 17 (1.04) | 29 / 30
(0.97) |
| 32/2 d256, 1 row | 4 | 17 / 16 (1.06) | 28 / 25 (1.14) | 56 / 45
(1.23) |
| 32/2 d256, 1 row | 8 | 23 / 17 (1.37) | 37 / 30 (1.21) | 67 / 67
(1.00) |
| 32/2 d256, 1 row | 32 | 27 / 30 (0.89) | 87 / 73 (1.20) | 263 / 339
(0.78) |
| 32/2 d256, 1 row | 128 | 60 / 97 (0.62) | 340 / 355 (0.96) | 1732 /
1652 (1.05) |
| 96/8 d128, 2 rows | 1 | 20 / 13 (1.52) | 30 / 18 (1.71) | - |
| 96/8 d128, 2 rows | 4 | 22 / 19 (1.21) | 63 / 39 (1.61) | - |
| 96/8 d128, 2 rows | 8 | 42 / 28 (1.49) | 122 / 68 (1.78) | - |
| 96/8 d128, 2 rows | 32 | 111 / 60 (1.86) | 454 / 274 (1.65) | - |
| 96/8 d128, 4 rows | 1 | 21 / 13 (1.57) | 31 / 18 (1.71) | - |
| 96/8 d128, 4 rows | 4 | 23 / 22 (1.05) | 63 / 42 (1.51) | - |
| 96/8 d128, 4 rows | 8 | 42 / 33 (1.26) | 122 / 74 (1.66) | - |
| 96/8 d128, 4 rows | 32 | 112 / 61 (1.84) | 470 / 274 (1.71) | - |
| 96/8 d128, 1 row | 1 | 14 / 12 (1.14) | 18 / 17 (1.09) | - |
| 96/8 d128, 1 row | 4 | 18 / 17 (1.07) | 35 / 24 (1.44) | - |
| 96/8 d128, 1 row | 8 | 19 / 20 (0.92) | 51 / 42 (1.22) | - |
| 96/8 d128, 1 row | 32 | 69 / 35 (1.96) | 206 / 214 (0.96) | - |

Single-row (`1 row`) cells are served by the backend engine (`eng10`),
d256 single-row at small batches by the backend's prefill-class engine
(`eng8`), everything else by the FROST row.

</details>

## 🔍 Related Issues

- Follows #4625 (cudnn decode backend on the wrapper) and #5327
(multi-token rows, sliding window, sinks).
- cudnn-frontend: the SM100 FROST row became a default, per-shape-ranked
engine in NVIDIA/cudnn-frontend#1152 (1.30.0);
NVIDIA/cudnn-frontend#1420 ranks it first for multi-token rows at every
cache length.

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

- `tests/utils/test_cudnn_decode_auto_rule.py` (new, CPU only, 74
cases): cudnn-frontend version parsing (`1.31.0.dev123`, `+cu13`,
`1.30`), the 1.30 / SM100 gate, and a positive / negative table for
`_auto_decode_prefers_cudnn` (every clause has a negative: one row, 16
rows per CTA, 32 CTAs, 256 rows, group 12 / 5 / 6, d64 / d192 / d256 /
d512, fp8, page 24, window, soft-cap, RoPE, overrides).
- `tests/attention/test_cudnn_decode.py` (+10 `auto` tests): fa2 on an
older frontend; `FLASHINFER_DECODE_AUTO_CUDNN=0`; `=1` forces cudnn on
SM100 for 64/8 x 4 rows and 64/4 x 2 rows (HND / NHD, without tensor
cores) and matches fa2; one wrapper going cudnn -> fa2 -> cudnn across
`q_len_per_req` with the KV-length storage following the batch up and
down; the shape gate (one row, two rows at 64/8, eight rows, b=4, group
12, d64, d256, page 24, window, 256 rows); the no-flag positive
(cudnn-frontend 1.30+ on SM100 resolves cudnn for 64/8 x 4, 64/4 x 2 / 3
/ 4 rows and matches fa2; skips on 1.29); CUDA-graph capture +
`fast_decode_plan` replan with changed lengths (caller-owned table / no
table x tensor cores on / off x 1 / 2 / 4 rows); `workspace_size`
agreeing with `plan()`; CUDA-graph `auto` without a table staying on fa2
and replaying correctly after the cache grows past the bucket; the
frozen-resolution error; `fast_decode_plan` moving fa2 -> cudnn -> fa2
-> cudnn across `q_len_per_req`.

Run on B200:

| stack | files | result |
|---|---|---|
| pip: cudnn-frontend 1.29 + cuDNN 9.26 (classic backend engine) |
`tests/attention/test_cudnn_decode.py`,
`tests/utils/test_cudnn_decode_auto_rule.py`,
`tests/attention/test_cudnn_wrapper_regressions.py`,
`tests/attention/test_cudnn_prepared_graph.py`,
`tests/attention/test_cudnn_prepared_contract.py` | 290 passed, 9
skipped (the sink-at-one-row cases the backend engine declines by name,
and the no-flag `auto` positives that need 1.30+) |
| cudnn-frontend 1.30.0 wheel + cuDNN 9.26, nothing set in the
environment | same files | 298 passed, 1 skipped: every sink,
multi-token, window, packed-Q and `auto` case, including the no-flag
positives |
| pip stack, `tests/attention/test_batch_decode_kernels.py` CUDA-graph /
tensor-core / fast-plan subset | | 1171 passed |

`ruff format` / `ruff check` (0.12.8) and `mypy` 1.17.1 (`--config-file
pyproject.toml`) clean on the changed files; pre-commit's whitespace /
EOF / tab hooks checked by hand (the hook install cannot reach the
network from this box).


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

- **Default behavior changes only on SM100 / SM103 with cudnn-frontend
>= 1.30.0 installed, and only for multi-token decode plans inside the
envelope above.** CI without a 1.30 frontend exercises the `auto -> fa2`
paths and the forced-override tests; the no-flag positive test skips
there with a message saying what it needs.
- Earlier revisions of this PR added a `FLASHINFER_CUDNN_FROST_ENGINES`
switch that forwarded cudnn-frontend's
`CUDNN_FRONTEND_ENABLE_FROST_ENGINES` opt-in. That was unnecessary (the
SM100 row is a default engine; the flag only makes FROST lead
everywhere, including shapes where it loses) and is gone; FlashInfer
sets no cuDNN environment variables.
- The rule is a plain predicate over plan-time arguments, unit-tested on
CPU, so widening it later (single-token decode once the frontend's d128
tile or backend ranking warrants it, d256, smaller CTA counts once the
tile splits KV at short caches) is a one-line change with a test row.
The gaps are measured in the matrix and reported to the cudnn-frontend
side.
- Serving loops that capture CUDA graphs with CSR metadata only keep fa2
under `auto` until they pass a dense `block_tables`; sizing the
auto-built table from the wrapper's fixed buffers is a possible
follow-up once its effect on the FROST split heuristic is measured.
- The fa2 wrapper without the attention-sink JIT variant ignores `sinks`
silently (the sink tests compare against a torch reference for that
reason, since #5327). Pre-existing; worth its own issue.

AI-assisted (Claude Code); reviewed and validated by the author on B200.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Yang Xu <yanxu@nvidia.com>

### [8565c83](https://github.com/flashinfer-ai/flashinfer/commit/8565c8358e7bc3048c7411f566173a562f15d2a0)

- **作者**: eigen
- **时间**: 2026-10-06T22:13:24Z
- **提交信息**: perf(cake_deepgemm_mega_gate): 16-way split-K cluster reduction with a compensated token-parallel combine on the small-M routing-gate routes (SM100a, SM103a) (#6129)

## Summary

Regenerates the fused routing-gate family
`flashinfer.experimental.deepgemm_mega_gate` (public API
`flashinfer.mega_gate.prepare_mega_gate`)
for SM100a (B200) and SM103a (GB300) at FlashInfer `d4a3ad6c1`. Two
scheduling changes on the single-tile small-M routes, everything
else keeps its program:

- The M = 1 route (both architectures) splits K = 5120 sixteen ways
instead of eight (48 CTAs x 5 k-blocks of 64) and reduces the partial
scores through a 16-CTA non-portable cluster (distributed shared memory,
same per-group leader pre-ranking as the previous revision).
- On SM100a the 1 < M <= 4 route takes the same 16-split cluster
reduction: a new runtime template (`cluster_tokens = 4`) and its
exact-shape specialization (static 4 tokens, physical map); the group
leader distributes the tokens over its gate warp groups
(token-parallel combine). SM103a keeps the 8-split scratch route for 1 <
M <= 4 (measured neutral there).

Expert selection is identical to native DeepGEMM `39d8c4ca` on every
shape. The normalized weights of the changed routes are computed from
the same FP32 partial sums combined in a different order with an
error-free compensated (TwoSum) pairwise summation, so they are not
bit-identical to native there; against an FP64 reference computed from
the identical inputs their error is at or below native's on every
seed (table below), bit-identical run to run, no NaN/Inf, top-k sets and
tie handling match the reference. No fast-math, no reduced
accumulation precision, no sampling or early exit.

## What changed in the generated package

- `csrc/experimental/deepgemm_mega_gate/generated/`: the M = 1 cluster
split-K program (both archs) and the SM100a `cluster_tokens = 4`
runtime program plus its static-4 specialization are new schedules.
Every program of the family is regenerated at this producer, so
the unchanged routes' files change too (new module ids and
generator-side text of the one-program-per-template model); their
schedules are the previous revision's, and the per-shape table below
measures the regenerated programs.
- `flashinfer/experimental/deepgemm_mega_gate/mega_gate.py` (and the
package README): the schedule-template table gains the
`cluster_tokens` axis and the new routes; `flashinfer/mega_gate.py` and
the public signature of `prepare_mega_gate` are unchanged.
- `tests/experimental/test_mega_gate_generated.py`: covers the new
routes (M = 1..4 on SM100a, M = 1 on SM103a) and the static set.

## Per-shape speedup (native DeepGEMM / this revision), cohort gate rows

CUPTI medians, cold L2, paired ABBA against native DeepGEMM `39d8c4ca`
in one process, 12 readings over 4 GPUs per row. "previous" = the
programs FlashInfer main carries (#5766 / #5961), measured the same way
in their round.


### SM100a (B200, 148 SMs)

| row (K = 5120, E = 384, top-6, sqrtsoftplus, FP32 bias) | native us |
source us (this revision) | native/source | source us (previous) |
native/source (previous) | program |
|---|---:|---:|---:|---:|---:|---|
| model-gate-m1 | 8.896 | 7.360 | 1.2099 | 7.872 | 1.1545 | changed |
| model-gate-m3 | 8.848 | 8.576 | 1.0335 | 8.576 | 1.0485 | changed |
| model-gate-m16 | 9.040 | 8.640 | 1.0474 | 8.768 | 1.0584 | unchanged |
| model-gate-m128 | 9.808 | 9.440 | 1.0407 | 9.600 | 1.0383 | unchanged
|
| model-gate-m512 | 11.888 | 11.488 | 1.0333 | 11.456 | 1.0363 |
unchanged |
| model-gate-m1024 | 13.568 | 12.880 | 1.0521 | 12.992 | 1.0468 |
unchanged |
| model-gate-m2048 | 17.376 | 16.656 | 1.0441 | 16.800 | 1.0323 |
unchanged |
| model-gate-m4096 | 25.776 | 24.640 | 1.0474 | 24.608 | 1.0338 |
unchanged |
| model-gate-m8192 | 40.064 | 37.696 | 1.0629 | 38.496 | 1.0216 |
unchanged |
| model-gate-m16-deterministic | 15.104 | 14.368 | 1.0522 | 14.592 |
1.0569 | unchanged |
| model-gate-m16-logical | 8.784 | 8.448 | 1.0377 | 8.544 | 1.0337 |
unchanged |

Gate-family rows all above 1.0 on this arch; the 118-row cohort geomean
of native/source at this revision is 1.2497.
The 16-CTA cluster routes (M = 1, M = 3) carry a +-0.35 us per-prepare
placement term (where the allocator places the 128 B score-barrier block
relative to the FP32 scratch block decides it); the readings above are
single draws, a previous measurement of the same schedules read 7.04 /
8.29 us.

### SM103a (GB300, 152 SMs)

| row (K = 5120, E = 384, top-6, sqrtsoftplus, FP32 bias) | native us |
source us (this revision) | native/source | source us (previous) |
native/source (previous) | program |
|---|---:|---:|---:|---:|---:|---|
| model-gate-m1 | 8.608 | 6.880 | 1.2512 | 7.264 | 1.1769 | changed |
| model-gate-m3 | 8.736 | 8.352 | 1.0421 | 8.192 | 1.0430 | unchanged |
| model-gate-m16 | 8.928 | 8.448 | 1.0526 | 8.224 | 1.0506 | unchanged |
| model-gate-m128 | 9.792 | 9.408 | 1.0409 | 9.184 | 1.0523 | unchanged
|
| model-gate-m512 | 11.616 | 11.264 | 1.0282 | 10.800 | 1.0178 |
unchanged |
| model-gate-m1024 | 13.152 | 12.704 | 1.0316 | 12.288 | 1.0365 |
unchanged |
| model-gate-m2048 | 17.152 | 16.224 | 1.0613 | 15.616 | 1.0430 |
unchanged |
| model-gate-m4096 | 24.528 | 23.568 | 1.0399 | 23.008 | 1.0382 |
unchanged |
| model-gate-m8192 | 37.184 | 35.360 | 1.0485 | 35.679 | 1.0188 |
unchanged |
| model-gate-m16-deterministic | 14.432 | 13.664 | 1.0584 | 13.568 |
1.0637 | unchanged |
| model-gate-m16-logical | 8.544 | 8.288 | 1.0331 | 8.160 | 1.0198 |
unchanged |

Gate-family rows all above 1.0 on this arch; the 118-row cohort geomean
of native/source at this revision is 1.2535.

## Correctness of the changed routes (FP64 reference from the identical
inputs, seeds 1-3)

| arch | row | seed | max abs (this / native) | max rel (this / native)
| weights beyond 1 ulp (this / native) | run-to-run | verdict |
|---|---|---|---:|---:|---:|---|---|
| B200 | model-gate-m1 | seed1 | 3.22e-08 / 6.2e-08 | 1.29e-07 /
3.45e-07 | 0.167 / 0.500 | identical | PASS abcde |
| B200 | model-gate-m1 | seed2 | 4.03e-08 / 5.75e-08 | 1.24e-07 /
2.17e-07 | 0.000 / 0.333 | identical | PASS abcde |
| B200 | model-gate-m1 | seed3 | 5.15e-08 / 5.15e-08 | 2.64e-07 /
2.64e-07 | 0.167 / 0.333 | identical | PASS abcde |
| B200 | model-gate-m3 | seed1 | 3.67e-08 / 6.65e-08 | 1.99e-07 /
3.61e-07 | 0.111 / 0.333 | identical | PASS abcde |
| B200 | model-gate-m3 | seed2 | 4.81e-08 / 6.01e-08 | 2.39e-07 /
4.74e-07 | 0.167 / 0.333 | identical | PASS abcde |
| B200 | model-gate-m3 | seed3 | 5.73e-08 / 1.18e-07 | 2.64e-07 /
3.31e-07 | 0.222 / 0.500 | identical | PASS abcde |
| GB300 | model-gate-m1 | seed1 | 2.59e-08 / 5.57e-08 | 1.47e-07 /
3.16e-07 | 0.167 / 0.167 | identical | PASS abcde |
| GB300 | model-gate-m1 | seed2 | 3.6e-08 / 9.74e-08 | 2.24e-07 /
2.67e-07 | 0.500 / 0.500 | identical | PASS abcde |
| GB300 | model-gate-m1 | seed3 | 2.36e-08 / 7.13e-08 | 1.31e-07 /
3.42e-07 | 0.167 / 0.333 | identical | PASS abcde |

Every other gate row (and the other 107 cohort rows of the DeepGEMM
family) passes the same criteria with an unchanged rounding path.
Criteria: no NaN/Inf mismatch; max abs / max rel error at most 1.05x
native's and the fraction of elements beyond 1 ulp at most native's +
0.1 pp on the same inputs; absolute caps never exceeded; bit-identical
output over 3 runs on both archs; expert sets and weights match the
reference except at ties within the reference tolerance.

## Validation

- `tests/experimental/test_mega_gate_generated.py` and the exporter's
unit tests pass on both archs; the DeepGEMM-family e2e slice at this
revision fails exactly the same pre-existing ids as the unmodified base
on both archs (0 regressions).
- The generated sources are committed byte-exact as sealed by the export
run (their SHA-256 digests are in the run manifest), like the previous
revision's generated files; the host files pass ruff and mypy.
- compute-sanitizer synccheck and memcheck: `ERROR SUMMARY: 0 errors` on
the gate rows M = 1 / 3 / 16 / 16-logical / 128 / 512 (12 runs per tool
per arch), both archs.
- Export gate (below): source program vs delivered program on one
workspace, 4 counterbalanced groups per shape, same-arm preconditioning,
SM clock >= 0.85 of the maximum, endpoint drift <= 2 %, direction
agreement <= 5 %, source/export >= 0.97.

## Generated-program export evidence

Baseline: **Cake production dispatcher** at Cake revision
`0c1128fbc818252dff863859c532858590aca4f3`.

## Hardware stages

- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-6bc5a7f5-5eef-5e21-9afa-7dc3106b0241`; 5
shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-24f29dbc-8d51-2c98-e791-ae203199a8e8`; 5
shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-86bec76a-9b78-4790-0a85-ccdcfc8793d4`; 5
shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-2bee3d64-dde0-cd64-6e01-9a32d717e0a0`; 5
shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.167.08`, UUIDs `GPU-cc730467-77fa-997b-0003-130f5e558b96`;
5 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.167.08`, UUIDs `GPU-b46339d8-036c-8884-f475-116e4ecd2e74`;
5 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.167.08`, UUIDs `GPU-0fa8ac69-dca2-e900-f0a1-5627d4b2786b`;
5 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.167.08`, UUIDs `GPU-b8a61286-075f-a882-f5dd-60c851acf0dc`;
5 shapes (named in the per-shape tables below).

Target revision: `d4a3ad6c1cd42c9f9f995c625ec7819eb7104af6`.

Benchmark execution: `direct`; 4 counterbalanced groups, 20.000 ms
warmup and 250.000 ms reportable budget per arm/group.
Latency metric: CUPTI GPU span per sample, first compute-kernel start to
last compute-kernel end of one arm call (every kernel the call launches,
asynchronous copies excluded), after a cold-L2 flush before each
measured sample; the reported value is the per-arm median. Each row's
``sm_clock_mhz_range`` in the summary JSON is the SM clock range
observed while the row was timed (group-boundary probes and, in the
symmetric graph mode, every sampled warmup/measurement phase).
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
|m1__sm_100a|G2|R15|0.007360|0.007392|0.9957x|—|—|—|pass|
|m3__sm_100a|G3|R27|0.008288|0.008288|1.0000x|—|—|—|pass|
|m16__sm_100a|G1|R11|0.008736|0.008704|1.0037x|—|—|—|pass|
|m128__sm_100a|G0|R5|0.009727|0.009696|1.0032x|—|—|—|pass|
|m512__sm_100a|G2|R33|0.011616|0.011520|1.0083x|—|—|—|pass|
|m1024__sm_100a|G3|R3|0.012993|0.012992|1.0001x|—|—|—|pass|
|m2048__sm_100a|G1|R17|0.016480|0.016448|1.0019x|—|—|—|pass|
|m4096__sm_100a|G0|R31|0.024671|0.024704|0.9987x|—|—|—|pass|
|m8192__sm_100a|G2|R39|0.038144|0.038240|0.9975x|—|—|—|pass|
|m16_deterministic__sm_100a|G3|R7|0.014720|0.014720|1.0000x|—|—|—|pass|
|m16_logical__sm_100a|G1|R9|0.008480|0.008448|1.0038x|—|—|—|pass|
|m1_logical__sm_100a|G0|R13|0.007520|0.007520|1.0000x|—|—|—|pass|
|m7__sm_100a|G2|R37|0.008736|0.008672|1.0074x|—|—|—|pass|
|m400__sm_100a|G3|R29|0.011776|0.011744|1.0027x|—|—|—|pass|
|m33_deterministic__sm_100a|G1|R23|0.014560|0.014559|1.0001x|—|—|—|pass|
|m100_logical__sm_100a|G0|R1|0.009376|0.009440|0.9932x|—|—|—|pass|
|m24_logical__sm_100a|G2|R19|0.008736|0.008736|1.0000x|—|—|—|pass|
|m3_logical__sm_100a|G3|R25|0.008449|0.008480|0.9963x|—|—|—|pass|
|m777__sm_100a|G1|R35|0.012576|0.012607|0.9975x|—|—|—|pass|
|m3000__sm_100a|G0|R21|0.023680|0.023680|1.0000x|—|—|—|pass|
|m1__sm_103a|G6|R16|0.006688|0.006688|1.0000x|—|—|—|pass|
|m3__sm_103a|G7|R28|0.007776|0.007936|0.9798x|—|—|—|pass|
|m16__sm_103a|G5|R12|0.008320|0.008480|0.9811x|—|—|—|pass|
|m128__sm_103a|G4|R6|0.009120|0.009120|1.0000x|—|—|—|pass|
|m512__sm_103a|G6|R34|0.010912|0.010816|1.0089x|—|—|—|pass|
|m1024__sm_103a|G7|R4|0.012256|0.012256|1.0000x|—|—|—|pass|
|m2048__sm_103a|G5|R18|0.015648|0.015648|1.0000x|—|—|—|pass|
|m4096__sm_103a|G4|R32|0.022784|0.022848|0.9972x|—|—|—|pass|
|m8192__sm_103a|G6|R40|0.035072|0.035008|1.0018x|—|—|—|pass|
|m16_deterministic__sm_103a|G7|R8|0.013920|0.013920|1.0000x|—|—|—|pass|
|m16_logical__sm_103a|G5|R10|0.008064|0.008096|0.9960x|—|—|—|pass|
|m1_logical__sm_103a|G4|R14|0.006592|0.006592|1.0000x|—|—|—|pass|
|m7__sm_103a|G6|R38|0.008256|0.008224|1.0039x|—|—|—|pass|
|m400__sm_103a|G7|R30|0.011232|0.011232|1.0000x|—|—|—|pass|
|m33_deterministic__sm_103a|G5|R24|0.013600|0.013568|1.0024x|—|—|—|pass|
|m100_logical__sm_103a|G4|R2|0.009024|0.009024|1.0000x|—|—|—|pass|
|m24_logical__sm_103a|G6|R20|0.008224|0.008224|1.0000x|—|—|—|pass|
|m3_logical__sm_103a|G7|R26|0.007904|0.007968|0.9920x|—|—|—|pass|
|m777__sm_103a|G5|R36|0.011904|0.011904|1.0000x|—|—|—|pass|
|m3000__sm_103a|G4|R22|0.022240|0.022240|1.0000x|—|—|—|pass|

## Route legend

|Key|Route|
|---|---|
|R1|deepgemm_mega_gate_m100_logical_sm_100a|
|R2|deepgemm_mega_gate_m100_logical_sm_103a|
|R3|deepgemm_mega_gate_m1024_sm_100a|
|R4|deepgemm_mega_gate_m1024_sm_103a|
|R5|deepgemm_mega_gate_m128_sm_100a|
|R6|deepgemm_mega_gate_m128_sm_103a|
|R7|deepgemm_mega_gate_m16_deterministic_sm_100a|
|R8|deepgemm_mega_gate_m16_deterministic_sm_103a|
|R9|deepgemm_mega_gate_m16_logical_sm_100a|
|R10|deepgemm_mega_gate_m16_logical_sm_103a|
|R11|deepgemm_mega_gate_m16_sm_100a|
|R12|deepgemm_mega_gate_m16_sm_103a|
|R13|deepgemm_mega_gate_m1_logical_sm_100a|
|R14|deepgemm_mega_gate_m1_logical_sm_103a|
|R15|deepgemm_mega_gate_m1_sm_100a|
|R16|deepgemm_mega_gate_m1_sm_103a|
|R17|deepgemm_mega_gate_m2048_sm_100a|
|R18|deepgemm_mega_gate_m2048_sm_103a|
|R19|deepgemm_mega_gate_m24_logical_sm_100a|
|R20|deepgemm_mega_gate_m24_logical_sm_103a|
|R21|deepgemm_mega_gate_m3000_sm_100a|
|R22|deepgemm_mega_gate_m3000_sm_103a|
|R23|deepgemm_mega_gate_m33_deterministic_sm_100a|
|R24|deepgemm_mega_gate_m33_deterministic_sm_103a|
|R25|deepgemm_mega_gate_m3_logical_sm_100a|
|R26|deepgemm_mega_gate_m3_logical_sm_103a|
|R27|deepgemm_mega_gate_m3_sm_100a|
|R28|deepgemm_mega_gate_m3_sm_103a|
|R29|deepgemm_mega_gate_m400_sm_100a|
|R30|deepgemm_mega_gate_m400_sm_103a|
|R31|deepgemm_mega_gate_m4096_sm_100a|
|R32|deepgemm_mega_gate_m4096_sm_103a|
|R33|deepgemm_mega_gate_m512_sm_100a|
|R34|deepgemm_mega_gate_m512_sm_103a|
|R35|deepgemm_mega_gate_m777_sm_100a|
|R36|deepgemm_mega_gate_m777_sm_103a|
|R37|deepgemm_mega_gate_m7_sm_100a|
|R38|deepgemm_mega_gate_m7_sm_103a|
|R39|deepgemm_mega_gate_m8192_sm_100a|
|R40|deepgemm_mega_gate_m8192_sm_103a|

## Baseline legend

Each shape row above inlines its applicable external baselines (paired
export ms is the shape's Export ms column); keys resolve here.

|Key|Baseline|Label|Rows|Gate|
|---|---|---|---:|---|

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|40|40|0.011566|0.011573|0.999316x|
|holdout|18|18|0.010629|0.010631|0.999744x|
|production|22|22|0.012393|0.012406|0.998967x|

|tpl_gate_bt16_c1_g3_st12_gw2_cluster4tok_touch|1|1|0.008449|0.008480|0.996344x|

|tpl_gate_bt16_c1_g3_st12_gw2_cluster4tok_touch_m4_r1_w3|1|1|0.008288|0.008288|1.000000x|

|tpl_gate_bt16_c1_g3_st12_gw2_cluster_touch|2|2|0.007041|0.007041|1.000000x|

|tpl_gate_bt16_c1_g3_st12_gw2_cluster_touch_m1_r1_w3|2|2|0.007016|0.007031|0.997833x|
|tpl_gate_bt16_c1_g3_st12_gw2_touch|6|6|0.011952|0.011947|1.000404x|

|tpl_gate_bt16_c1_g3_st12_gw2_touch_m16_r1_w6|5|5|0.008357|0.008398|0.995110x|

|tpl_gate_bt16_c1_g3_st12_gw2_touch_m16_r2_w6|3|3|0.008146|0.008168|0.997256x|
|tpl_gate_bt176_c2_g3_st11_gw6|6|6|0.013535|0.013536|0.999926x|
|tpl_gate_bt176_c2_g3_st11_gw7|4|4|0.028972|0.028977|0.999828x|
|tpl_gate_bt176_c2_g3_st11_gw7_bk128|2|2|0.023709|0.023758|0.997931x|
|tpl_gate_bt32_c1_g3_st11_gw4|2|2|0.009198|0.009230|0.996604x|

|tpl_gate_bt32_c1_g3_st11_gw4_m128_r1_w6|2|2|0.009419|0.009404|1.001597x|
|tpl_gate_bt96_c1_g3_st7_gw6|2|2|0.011501|0.011485|1.001361x|
|tpl_gate_bt96_c1_g3_st7_gw6_m512_r1_w6|2|2|0.011258|0.011162|1.008605x|

Complete denominator: **true** (40/40).

All gates passed: **true** (40/40).

## Baselines and their source PRs

- #5523 - the DeepGEMM-family generated package (origin of this family).
- #5739, #5754 - the routing-gate revisions that preceded #5766.
- #5766 - per-group leader pre-ranking on the M = 1 cluster split-K
route (the previous revision of the changed programs).
- #5961 - runtime token count with one program per schedule template
(the host/template model this revision extends).
- Native baseline: DeepGEMM `39d8c4ca`.

Producer: Cake revision `0c1128fbc818252dff863859c532858590aca4f3`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added an optimized execution route for workloads processing 2–4 tokens
on supported SM100a hardware.
* Expanded single-tile execution options for workloads processing 1–4
tokens, including improved handling of partial results.
* Configuration and schedule selection now account for hardware
architecture and cluster-based execution requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [26fe42d](https://github.com/flashinfer-ai/flashinfer/commit/26fe42d91acc1d56bd27560f64e9bf727d623cca)

- **作者**: eigen
- **时间**: 2026-10-06T22:07:53Z
- **提交信息**: perf(cake_fp8_projection): Kimi-K3 KDA/MLA projection GEMM round 7 (FP8 token ring on the M=256 cluster split-K cell, parallel-issue DSM partial exchange), shared-source export (SM100a, SM103a) (#6146)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise (see
Baselines).

## Summary

Round 7 of the experimental generated-program backend for the serialized
`FP8_PB_WO` KDA / MLA projection GEMMs of `nvidia/Kimi-K3-NVFP4` on
`sm_100a` (B200) and `sm_103a` (B300 / GB300):
`flashinfer/experimental/kimi_k3_fp8_projection` (shared-source layout,
one `_kernel.cu` / `_binding.cu` pair per program). Built on upstream
main `ea8135c0b` (#6096).

### What round 7 adds
- **FP8 token ring on the M = 256 narrow-N cluster rows** (`xq_stages`,
key field `_x<N>`; table cells `1,28,256` = `b_proj` / `f_a` at M = 256,
both architectures): the BF16 ring (4 slots) and the FP8 token ring (4
slots) run next to the 4-stage weight ring of the 4-CTA cluster split-K
instance (`decode:t16_p4_fused_r4_x4_cs4`); 1.015-1.022x on both GPUs
(7-round paired A/B), bit-exact.
- **Parallel-issue DSM exchange** (`xp`, `_xp`) on the 14-CTA cluster
split-K cells `1,28,1` / `1,28,8` / `1,28,64` / `5,28,1` / `5,28,64`
(`b_proj` M = 1 / 8 / 64, `f_a` M = 8 / 64, `kv_a` M = 1 / 64; 14-CTA
cells plus the 8-CTA t32 `kv_a` M = 64 cell): the cluster partial
exchange issues its DSM bulk copies from one lane per peer instead of
one thread serially; 1.005-1.014x on both GPUs (7-10 paired rounds,
every round a win); bit-exact.
- Host package: `cake_backend.py` gains the FP8-ring sizing rule
(`decode_config` / `_decode_stage_geometry`, mirror of the Cake rule)
and the `xp` key; `decode_table.py` carries the two adopted cells;
`cake_jit.py` registry regenerated.

### Evidence
- Export protocol (Cake `tools/export-generated-programs`, CUPTI graph
replay, source program vs exported program per contract row, zero-budget
correctness + bitwise fused/unfused parity): arch-neutral exporter,
TARGET_REVISION FlashInfer main `ea8135c0b`, producer `r7fin3`
`e061ebab951b`: GB300 (sm_103a, 152 SMs) 352/352 sealed (349 in round e3
+ 3 in no-touch retry round 1); B200 (sm_100a) 349/352 sealed (338 + 11
across no-touch retries) with root cause for the 3 unsealed rows
`tp8_f_a_m512`, `tp8_b_proj_m512`, `tp1_b_proj_m512` -- only
`directional_disagreement` fails (0.081-0.086 vs 0.08;
source_over_export 0.957, drift < 0.01, correctness True): a
deterministic launch-order artifact of the ~17 us M=512 GEMM rows
(export arm 8 % slower only in export-first paired blocks, 4 attempts +
2 nodes), programs identical to main; delivery render byte-identical on
both GPUs (78 files, sha256 without index lines `97df3e22c9015dbf`).
- Package tests
`tests/experimental/test_cake_kimi_k3_fp8_projection.py`: 51 passed on
the delivered tree on both GPUs (B200 step `e0444d8e`, GB300 step
`f777cfc9`), host-rule pre-test 17 passed before the first export
measurement.
- Exported programs vs the fastest existing FlashInfer / DeepGEMM chain
(`benchmarks/bench_cake_kimi_k3_fp8_projection.py --cupti`, 132 perf
rows): exported programs vs the fastest FlashInfer / DeepGEMM chain, 132
rows each: B200 132/132 > 1 (min 1.022, gm 2.033), GB300 132/132 > 1
(min 1.013, gm 2.014).

### Baselines
The comparison set of `benchmarks/bench_cake_kimi_k3_fp8_projection.py
--cupti` is the fastest *complete* existing chain per row (quantization
+ GEMM where the chain needs a separate FP8 quantization pass), measured
on the same GPU in the same process (CUDA-graph replay, cold L2,
alternating rounds), with the per-row winner recorded in the receipts:
- `bf16_cublas` -- BF16 cuBLAS GEMM on the unquantized activations (the
fastest chain on most decode-size rows and on the narrow-N prefill
rows);
- `deepgemm_pack` -- DeepGEMM `fp8_gemm_nt` (per-token x per-block FP8,
UE8M0) with its packed-scale activation quantization (the fastest chain
on the wide-N prefill rows and the tp1 M <= 64 rows of the wide
families);
- `fi_trtllm` -- FlashInfer trtllm-gen FP8 block-scale GEMM
(`gemm_fp8_nt_blockscaled` path) (fastest on several tp1 M <= 8 rows);
- `fi_cutlass_*` / `fi_cutile` -- FlashInfer CUTLASS and cuTile FP8
block-scale GEMMs (fastest on a few tp1 rows).
Round 7 changes two dispatch cells; every other exported program is
cubin-identical to the previous head, so the per-row results of the
previous rounds carry over (geomean 2.04x B200 / 2.03x B300 vs these
chains at round 6).

### Test plan
- `pytest tests/experimental/test_cake_kimi_k3_fp8_projection.py` on
B200 and B300 (run on both).
- `python benchmarks/bench_cake_kimi_k3_fp8_projection.py --cupti` on
B200 and B300 (run on both).

Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Expanded Kimi K3 FP8 projection decode configurations with an
independent FP8 token ring and parallel cluster exchange options,
including automatic ring sizing within shared-memory limits.
- Added kernel variants to support the updated decode configurations and
quantization paths.
- **Bug Fixes**
  - Improved cluster reduction coordination for projection workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8f4ee77](https://github.com/flashinfer-ai/flashinfer/commit/8f4ee770e49fdfb084408d50f5f0dc823d1ecfc9)

- **作者**: eigen
- **时间**: 2026-10-06T21:45:16Z
- **提交信息**: refactor(cake_kimi_k3_situ): regenerate the SiTU MoE backend from its producer, drop dead bindings and sequences, fold per-arch copies (#6135)

Closes #5800 (mechanical and regenerated steps; the remaining structural
steps are recorded on the issue as follow-ups).

- Delete the per-stage bindings no module ever compiled, the sequences
no route selector reaches (and the kernels only
they used), the `m256_c12` alias sequence and every per-route
prepared-sequence binding (17 per architecture, each
repeating its stages' host shims): every kernel module now carries its
own stage shim (`PreparedLaunch` / `Prepare` /
`Submit`, a single-call `run`, and two-phase entry points), and one
host-only route submitter prepares every stage of
a call from a plan the host flattens once per (workspace, token count)
before it launches the first — the shipped
sequence timeline (prepare all, then launch back to back) without a
sequence TU per route.
- Regenerate the quant, routing, FC1/FC2 and finalize modules of the
generic tile 8/16/32 routes from the producer as
architecture-neutral sources (one source per module, the sm_100a/sm_103a
smem-base line behind `__CUDA_ARCH__`); carry
every other kernel unchanged (same bodies, per-symbol SASS proof; its
stage shim is the one the shipped sequence
bindings embed for it) with the same one-line arch fold where the pair
differed only there — the small-row, `claim8`
and single-token kernels have no producer, and the tile-128 FC1/FC2
kernels keep the shipped bodies because their
regenerated versions measured 2-4 % slower on the 2048..16384-token
rows.
- Tests cover every routed selector per architecture (1, 8, 16, 32..256,
512/1024, 2048/4096, 8192/16384 tokens) and
the generic tile buckets (2, 200, 300, 3000), eager and CUDA-graph
replay, prepared-plan facts (stages, modules, FC2 pool
rows), workspace-size monotonicity and the unsupported-dispatch
rejections; the SFB layout, two-CTA footprint and
  cluster-router facts are asserted behaviourally.

Net: 194 files / 207,891 lines -> 75 files / 64,762 lines (202 files
changed with renames, +7,643 / -150,772; family csrc 191 -> 72 files,
jit module 6,549 -> 1,496 lines).

Validation: per-symbol SASS equivalence of every routed kernel against
main `f8d3729e9c85` on sm_100a and sm_103a
(per-symbol SASS body hashes of the carried kernels are identical to the
shipped bodies on both architectures: 22/22 carried programs matched,
and the 6 regenerated programs whose bodies did not change also matched
byte-for-byte; only the 7 regenerated generic tile 8/16/32 FC1/FC2/quant
bodies are new, replacing 6 shipped bodies at those stages);
`tests/moe/test_cake_kimi_k3_situ.py` on B200 and B300 (30/30 passed on
both, every selector, eager and graph); paired A/B (base and
candidate in one process pair on the same GPU, interleaved rounds, CUPTI
timing) over the 26 routed rows (13 token counts x
uniform/skew) plus the 4 generic rows. Because this is a host-path
change, eager rows are scored end-to-end (host call to
completion) and graph rows by GPU span, with the eager GPU span reported
alongside: B200 geomean 1.0396 (min row
0.9919, m16384 skew graph), B300 geomean 1.0396 (min row 0.9950, m16
uniform graph). Scored by eager GPU span alone, the large-token eager
rows read 1-2.5% lower on B200 (B300 within 1.2%) while every graph row
and the SASS are identical: the faster host raises
the GPU duty cycle and lowers the power-capped SM clock (clock-sampled;
padding the host by 60 us closes the gap on
every such row and changes nothing on the m64 control), so that reading
measures the clock, not the kernels.

Follow-ups recorded on #5800: FC1/FC2 as templates over tile-N and
pipeline depth (the affine literals in the shared-memory
and TMEM offsets need a generator extension), descriptor caching at
prepare time for the by-value tensor-map ABI, and
regeneration of the carried kernels (small-row / claim8 / single-token,
and the tile-128 FC1/FC2 once the producer
matches the shipped schedule).

<!-- CI: /bot run tests/moe/test_cake_kimi_k3_situ.py ; @flashinfer-bot
run tests/moe/test_cake_kimi_k3_situ.py -->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added staged execution for routed MoE operations, allowing launch
preparation and submission to be coordinated across multiple stages.
* Expanded token-count-based routing options, including additional tile
selections and large-token workspace handling.
* Added architecture-specific handling for shared-memory access across
GPU targets.
* **Bug Fixes**
* Improved tensor-map dimension checks and validation of inputs and
launch settings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8d04a12](https://github.com/flashinfer-ai/flashinfer/commit/8d04a12ed32d73877447cff5bd6b33c2cad2e7dc)

- **作者**: eigen
- **时间**: 2026-10-06T21:35:59Z
- **提交信息**: perf(cake_nvfp4_mla_decode): pin the decode kernel's launch bounds so its register budgets apply (SM100a 1.6-2 % faster) (#6127)

## Summary

Regenerates the `cake_nvfp4_mla_decode` programs (DeepSeek-V4 NVFP4 MLA
decode, D=512 latent + 64 rope, split-KV combine) from the latest Cake
kernel tree.

Kernel change carried by the generated decode program: the kernel now
declares `__launch_bounds__(512, 1)`. Without the minimum-blocks
argument ptxas cannot determine the entry register count, drops every
`setmaxnreg` and allocates all warps under the 128-register
launch-bounds share; with it the kernel's per-role register budgets
(softmax warps 160, transform / load / MMA warps 96) take effect. The IR
is unchanged, so the numerics are bit-identical to the programs
currently in `main`; the combine program is regenerated unchanged apart
from the current rendering of the bf16-pair unpack (plain C++ shifts
instead of inline PTX, same bits). Precision points and test tolerances
are unchanged (NVFP4 QK, fp32 softmax, E4M3 P x 2^8, on-chip V
requantisation to E4M3, fp32 combine).

## Speedup

Kernel-only CUPTI GPU span of every launch (decode + combine; FP8
CuTe-DSL likewise), cold L2, arms interleaved per row, 2 reps, same GPU
and process; bs32 / q6 / H64 / sink / page 64.

Against the programs currently in `main` (ratio = new / current time):

| KV length | GB300 (SM103a) | B200 node 1 (SM100a) | B200 node 2
(SM100a) |
|---|---|---|---|
| 8K | 1.002 | **0.980** | **0.980** |
| 16K | 1.000 | **0.983** | **0.978** |
| 32K | 0.999 | **0.982** | **0.980** |
| 64K | 1.000 | **0.982** | **0.985** |
| 128K | 0.999 | **0.984** | **0.988** |

Against `trtllm_batch_decode_with_kv_cache_mla(backend="cute-dsl")` with
an FP8 KV cache (FP8 time / new time):

| KV length | GB300 (SM103a) | B200 node 1 (SM100a) | B200 node 2
(SM100a) |
|---|---|---|---|
| 8K | **1.054x** | **1.060x** | **1.024x** |
| 16K | **1.132x** | **1.093x** | **1.048x** |
| 32K | **1.178x** | **1.142x** | **1.085x** |
| 64K | **1.226x** | **1.175x** | **1.128x** |
| 128K | **1.255x** | **1.204x** | **1.175x** |

## Export protocol

Sealed generated-program export, 16/16 rows (8 shapes x 2
architectures), source/export 0.9925-1.0452 with the directional, drift
and SM-clock gates passed on B200 and GB300; two-architecture merge
through a closed read-only prior. Target revision e07685c59.

| row | SM100a source / export ms | SM103a source / export ms |
|---|---|---|
| smoke | 0.013632 / 0.013536 | 0.012768 / 0.012864 |
| partial_pages_h8 | 0.023679 / 0.022656 | 0.022768 / 0.022208 |
| no_sink_q1 | 0.039936 / 0.039680 | 0.036224 / 0.036416 |
| bs32_q6_kv8k | 0.115200 / 0.114624 | 0.094240 / 0.094944 |
| bs32_q6_kv16k | 0.206015 / 0.206240 | 0.163648 / 0.163632 |
| bs32_q6_kv32k | 0.382847 / 0.382335 | 0.298880 / 0.299232 |
| bs32_q6_kv64k | 0.738463 / 0.737919 | 0.568992 / 0.569072 |
| bs32_q6_kv128k | 1.449599 / 1.449086 | 1.099648 / 1.100064 |

## Tests

- `tests/experimental/test_cake_nvfp4_mla_decode.py`: 51 passed, 1
skipped on B200, 51 passed, 1 skipped on GB300.
- `benchmarks/bench_cake_nvfp4_mla_decode.py` (batch 32, q 6, 64 heads;
host path included): B200 0.1081 / 0.1920 / 0.3663 / 0.7926 / 1.5557 ms,
GB300 0.0937 / 0.1647 / 0.3004 / 0.5718 / 1.1398 ms at 8K / 16K / 32K /
64K / 128K.

Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
* Updated the internal execution path for NVFP4 MLA decoding. Existing
inputs, outputs, validation, and launch behavior remain unchanged; no
user-facing behavior changes are noted.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [203ecad](https://github.com/flashinfer-ai/flashinfer/commit/203ecadcf2d8e0bea0ea75b66c7cf9f403a7fa87)

- **作者**: eigen
- **时间**: 2026-10-06T21:31:56Z
- **提交信息**: perf(cake_nvfp4_attn): block-relative P codes and a selector upper bound for the MiniMax-H3 SM120 NVFP4 varlen attention (#6068)

## perf(cake_nvfp4_attn): block-relative P codes and a selector upper
bound for the MiniMax-H3 SM120 NVFP4 varlen attention

Regenerated
`csrc/cake_minimax_h3_sm120_nvfp4_varlen_attention_sm120a.cu` from the
Cake tree 970db970ee9. Both host entries
(`minimax_h3_sm120_varlen_attention_nvfp4`, `_nodelta`) keep their
signatures and contracts.

**What changes**
- All four device kernels (compensated / uncompensated x base /
warp-specialised) produce the E2M1 P codes block-relative straight
from the exponential (`exp2((s - blockmax) * c + log2 6)`, rounded to
E2M1) and accumulate the row sum per 16-key block. Same FP32
operations re-associated -- no reduced precision, no approximation; the
UE4M3 block scales are byte-identical to #6060. Outputs are
not bit-identical to #6060: per-row max-abs error vs an FP32 reference
is identical and rel-L2 agrees within 4e-6 (identical to 6-7 significant
digits; mixed sign at the last bit, max-abs identical in all 234 cells)
relative on
all 13 contract shapes x 3 seeds on RTX 5090 and RTX PRO 6000 Blackwell
(tables in the Cake design doc).
- Host selector (compensated entry): the warp-specialised kernel is
launched for `1536 <= tokens / segments < 16384` on >= 188-SM
parts (`kWsMaxMeanSegment`); longer calls return to the base kernel,
which is now the faster one there. The uncompensated entry
keeps the #6060 selection (`kWsMaxMeanSegmentNodelta = 0`): both of its
kernels tie on long calls.

**Measured (paired ABAB CUPTI cold-L2, complete operator, 56 heads x
128; this TU vs #6060 forms)**
**RTX 5090 (node 2u1g-b650-1923, step daf420fd)** (compensated entry
`minimax_h3_sm120_varlen_attention_nvfp4` / uncompensated `_nodelta`;
base = the #6060 kernel the entry ran for that shape)

| Shape (cu_seqlens) | #6060 op ms | this PR op ms | operator speedup
(min paired group) | uncompensated entry speedup (min group) |
|---|---|---|---|---|
| center_4s (0,33472) | 39.050 | 36.860 | **1.0595** (1.0514) | 1.0413
(1.0411) |
| center_5s (0,38592) | 52.330 | 49.220 | **1.0626** (1.0545) | 1.0404
(1.0379) |
| center_6s (0,48768) | 83.190 | 78.670 | **1.0575** (1.0513) | 1.0393
(1.0372) |
| center_8s (0,58944) | 121.800 | 116.300 | **1.0510** (1.0474) | 1.0385
(1.0380) |
| center_10s (0,74240) | 195.700 | 186.500 | **1.0488** (1.0486) |
1.0404 (1.0390) |
| center_15s (0,109952) | 435.000 | 416.500 | **1.0449** (1.0445) |
1.0411 (1.0397) |
| tail_5s_a (0,38531) | 54.730 | 52.310 | **1.0463** (1.0399) | 1.0399
(1.0393) |
| tail_5s_b (0,38629) | 54.620 | 52.030 | **1.0451** (1.0402) | 1.0387
(1.0373) |
| pad_15s (0,109901,109952) | 439.000 | 419.400 | **1.0476** (1.0465) |
1.0414 (1.0412) |
| seg4 (0,8368,16736,25104,33472) | 12.010 | 11.350 | **1.0577**
(1.0452) | 1.0301 (1.0292) |
| seg3_ragged (0,257,4567,4824) | 0.930 | 0.891 | **1.0433** (1.0426) |
1.0280 (1.0278) |
| seg_empty (0,0,129,129,500) | 0.042 | 0.041 | **1.0125** (1.0121) |
1.0085 (1.0081) |
| single_4096 (0,4096) | 0.782 | 0.747 | **1.0459** (1.0457) | 1.0274
(1.0271) |

**RTX PRO 6000 Blackwell Server Edition (node 2u2g-emr-0472, step
006e6f64)** (compensated entry `minimax_h3_sm120_varlen_attention_nvfp4`
/ uncompensated `_nodelta`; base = the #6060 kernel the entry ran for
that shape)

| Shape (cu_seqlens) | #6060 op ms | this PR op ms | operator speedup
(min paired group) | uncompensated entry speedup (min group) |
|---|---|---|---|---|
| center_4s (0,33472) | 36.760 | 35.540 | **1.0334** (1.0296) | 1.0168
(1.0116) |
| center_5s (0,38592) | 48.480 | 46.820 | **1.0343** (1.0284) | 1.0147
(1.0127) |
| center_6s (0,48768) | 76.870 | 74.760 | **1.0314** (1.0282) | 1.0163
(1.0142) |
| center_8s (0,58944) | 112.200 | 108.200 | **1.0339** (1.0329) | 1.0141
(1.0114) |
| center_10s (0,74240) | 177.600 | 171.100 | **1.0372** (1.0332) |
1.0150 (1.0149) |
| center_15s (0,109952) | 388.600 | 373.200 | **1.0387** (1.0386) |
1.0171 (1.0163) |
| tail_5s_a (0,38531) | 48.970 | 47.530 | **1.0319** (1.0301) | 1.0146
(1.0140) |
| tail_5s_b (0,38629) | 48.890 | 47.460 | **1.0298** (1.0294) | 1.0134
(1.0108) |
| pad_15s (0,109901,109952) | 387.100 | 372.500 | **1.0390** (1.0386) |
1.0157 (1.0145) |
| seg4 (0,8368,16736,25104,33472) | 11.200 | 11.030 | **1.0141**
(1.0122) | 1.0085 (1.0081) |
| seg3_ragged (0,257,4567,4824) | 0.879 | 0.868 | **1.0119** (1.0119) |
1.0099 (1.0096) |
| seg_empty (0,0,129,129,500) | 0.056 | 0.055 | **1.0185** (1.0179) |
1.0136 (1.0133) |
| single_4096 (0,4096) | 0.749 | 0.741 | **1.0111** (1.0107) | 1.0087
(1.0086) |

All 13 shapes >= 1.00 on both parts and both entries; outputs finite,
idempotent, within the FP4 tolerance; the 5090 gains reproduced on a
second board (node 2u1g-b650-1927). Cake kernel tree 970db970ee9
(2026-10-05).

Baselines carried from #6060 on #5660 / #5629 / #5595 / #5583 / #5545
(all-shape tables in the Cake design doc; ragged
SageAttention3 d1a57a546c3 + CUTLASS 0b55a2f6 same-session comparison:
RTX PRO 6000 1.24-1.39x on the single-segment shapes 33472..109952,
1.83x / 2.75x / 1.82x on the 4-segment, 3-segment ragged and 4096
shapes; RTX 5090 1.03-1.26x and 1.67x / 2.45x / 1.64x).

Tracker: #4254. Tests:
`tests/diffusion_ops/test_minimax_h3_sm120_nvfp4_varlen_attention.py`
and `..._nodelta.py` (unchanged) --
17 passed + 2 skipped / 17 passed on RTX PRO 6000 (ws kernels exercised)
and on RTX 5090, FlashInfer 188bdd769db with this TU.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a9d3d64](https://github.com/flashinfer-ai/flashinfer/commit/a9d3d64fee145fa2be06e08063de7d6ca1c45095)

- **作者**: eigen
- **时间**: 2026-10-06T21:04:10Z
- **提交信息**: perf(cake_moe_finalize_allreduce_fusion): poll the owner segment at world size 8 too (#6128)

## Summary

Second performance round for `cake_moe_finalize_allreduce_fusion`
(indexed MoE finalize + Lamport all-reduce +
residual/RMSNorm + optional NVFP4 epilogue, SM100/SM103), on top of
#6057. No API, workspace-ABI, binding-table or
numerics change: the same twelve kernels, the same workspace layout, and
every output stays bit-identical to the current
kernel on the full test matrix (fp16/bf16 × tokens 1/16/128/2048 × top-k
4/8 × PDL × output profile × shared expert,
TP2/TP4/TP8).

One change (regenerated templated TU
`csrc/cake_moe_finalize_allreduce_fusion/cake_moe_finalize_kernels.cu`):

**World size 8 polls the owner segment too.** #6057 switched world sizes
2 and 4 to poll the owner segment of the local
Lamport buffer and kept the remote-diagonal poll at world size 8 because
an earlier measurement had the owner poll
losing 4 % at tokens = 1 there. That measurement was an artefact of how
the ws8 kernels were generated for it (the
per-peer poll loads had been rolled into a loop; the kernels were not
the straight-line form being compared). With the
straight-line form the ws8 owner poll is 16 SASS instructions shorter
than the diagonal poll and faster on every row,
so all three world sizes now poll the same way. Same published bytes
either way; the ws2/ws4 kernels are unchanged
(three convert statements of the NVFP4 scale path are now plain instead
of volatile asm; the SASS of all twelve
kernels is unchanged by that, verified per kernel).

## Benchmarks

`benchmarks/comm/bench_cake_moe_finalize_allreduce.py`, CUPTI, paired
in-process A/B against the current kernel (arms
interleaved per row, 10 counterbalanced passes for tokens ≤ 16 and 4
passes at tokens 128, geomean of the per-row
rank-min ratio current/new over fp16/bf16 × top-k 4/8 × PDL × profile ×
shared expert = 32 rows per tokens value).
TP2/TP4 are unchanged by construction (identical SASS); measured as
controls in the same runs: B200 TP2 0.999 / 0.999 / 1.000 and TP4 1.002
/ 0.999 / 1.000 at tokens 1 / 16 / 128,
TP2 tokens 2048 1.000; B300 class A TP2 0.999 / 1.000 / 0.998 and TP4
1.007 / 1.002 / 1.001, TP2 tokens 2048 0.999.

| GPU | TP8 tokens 1 | 2 | 4 | 8 | 16 | 128 | rows faster |
|---|---|---|---|---|---|---|---|
| B200 | 1.097 | 1.105 | 1.098 | 1.182 | 1.292 | 2.048 | 192 / 192 |
| B300 (node class A) | 1.070 | 1.067 | 1.084 | 1.122 | 1.248 | 1.990 |
192 / 192 |
| B300 (node class B) | 1.183 | 1.219 | 1.158 | 1.191 | 1.1836 | 1.18328
| 192 / 192 |

Combined with #6057, vs the kernel before that PR: B200 TP8 tokens 1 /
16 / 128 ≈ 1.23 / 1.39 / 2.22, B300 ≈ 1.25 /
1.35 / 2.06; TP2 / TP4 as reported there.

## Tests

- `tests/comm/test_cake_moe_finalize_dispatch.py`,
`tests/comm/test_cake_moe_finalize_allreduce.py`,
`tests/comm/test_allreduce_fusion_moe_unified_api.py` at ws2/4/8, fp16 +
bf16, on B200 and B300.
- Every A/B row bit-identical to the current kernel (B200 and B300);
outputs identical on all ranks.
- compute-sanitizer synccheck (0 errors) and memcheck (no device-side
error; the reported entries are host
`cuMemCreate` capability probes in torch's symmetric-memory allocator,
identical on the current kernel) on the ws8 path.

Related to #5771.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
* Streamlined the underlying all-reduce and FP8 quantization
implementation. Conversion behavior remains unchanged, and no
user-facing features or capabilities were added or removed. This update
does not change how users interact with the product or the results they
should expect.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [58a603e](https://github.com/flashinfer-ai/flashinfer/commit/58a603e500baf9bbcab6110afd37263e934d1864)

- **作者**: Vincent
- **时间**: 2026-10-06T20:11:32Z
- **提交信息**: chore(artifacts): bump trtllm-gen BMM cubins for SM107 2x/4x MMA-K MoE kernels (#6090)

## 📌 Description

Bump `ArtifactPath.TRTLLM_GEN_BMM` / `CheckSumHash.TRTLLM_GEN_BMM` to a
trtllm-gen batched-GEMM (MoE) pack that adds the Rubin (SM107) 2xfp8 /
4xfp4 MMA-K kernels.

The current pack built its `sm_107a` MoE kernels with the Blackwell
MMA-K (fp8/mxfp8 K=32, nvfp4 K=64), so Rubin never got its native 2x/4x
MMA. The new pack ([cubin_publishing
!201](https://gitlab-master.nvidia.com/dl/flashinfer/cubin_publishing/-/merge_requests/201))
pairs MMA-K with the target arch:

| `sm_107a` kernel family | before | after |
|---|---|---|
| nvfp4 x nvfp4 | K=64 | **K=128 (4xfp4)** |
| mxfp8 x mxfp8 | K=32 | **K=64 (2xfp8)** |
| mxfp4 weights x mxfp8 activations | K=32 | **K=64 (2xfp8)** |
| mxfp4 x fp8, fp8 per-tensor / per-channel | K=32 | **K=64 (2xfp8)** |
| fp8 DeepSeek block-scale | K=32 | K=32 (unchanged; 2x MMA-K needs mmaM
% 128 == 0) |

The `sm_100f` / `sm_103a` configuration set is unchanged.

New pack:
`35cb99413a3ebce2e87a03fc04196e528e22c8d5/batched_gemm-fdba669-7e3d0a6/`,
6,984 files, `checksums.txt` sha256 `66b467a0…971f`. It is published on
the public Artifactory (verified via edge.urm).

## 🔍 Related Issues

Requested by vLLM for Rubin MoE (mxfp8 x mxfp8, mxfp8 x mxfp4, nvfp4).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran `pre-commit run --files
flashinfer/artifacts.py`; all hooks pass.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (Artifact bump only.)
- [x] All tests are passing (`unittest`, etc.).

Ran on a Rubin GR100 (SM107) with
`tests/moe/test_trtllm_gen_fused_moe.py` plus the
`routing_renormalize_{fp4,fp8}` files, selecting the nvfp4 / mxfp4xmxfp8
/ mxfp8 / fp8 cases. Same selection before and after the bump:

- Previous pack (validated earlier on an internal build of the same
config): 699 passed, 0 failed. FlashInfer loaded 1,393 `sm_107a` cubins,
all at Blackwell MMA-K.
- New pack (an MR build of the same config + trtllm-gen fdba6697): 699
passed, 0 failed. The same 1,393 kernels load at the new MMA-K: E2m1
K=128 (362), MxE4m3 x {MxE2m1, MxE4m3} K=64 (412 / 414), E4m3 per-tensor
K=64 (83), E4m3 DeepSeek K=32 (122).
- This PR branch with the **published** pack, downloaded from the public
Artifactory: 699 passed, 0 failed, 1,393 `sm_107a` cubins with the same
MMA-K breakdown as above.

Blackwell (SM100/103) is not tested locally; please rely on this PR's CI
for the rebuilt `sm_100f` / `sm_103a` cubins.

## Reviewer Notes

Pure artifact bump: two lines in `flashinfer/artifacts.py`. Performance
comparison on Rubin will follow separately.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>

### [601cb12](https://github.com/flashinfer-ai/flashinfer/commit/601cb12713fd73f1744b15fdea6f9ddaaf2b4ec3)

- **作者**: Alex Yang
- **时间**: 2026-10-06T20:01:29Z
- **提交信息**: style(experimental): make the b12x tree pass pre-commit

#5767 landed b12x without passing pre-commit, and pre-commit runs on
all files, so every PR has been red since.

- Format the b12x trees (end-of-file-fixer, clang-format, ruff format).
  No behavior change.
- Fix undefined names (F821): add the missing imports (os, dataclass,
  torch.multiprocessing as mp, TYPE_CHECKING imports in engram/_disk.py).
  Where the real value is unknown, add None placeholders (mhc
  *_4096_K_SPLITS, test_ep_moe_api swizzle_block_scale) or noqa
  (startup/attention.py declaration, test_gdn_decode recurrent_state).
  Those paths still fail at runtime, as before; b12x owners must supply
  the real values.
- Waive b12x's remaining ruff style debt via per-file-ignores (F821
  stays enforced) and exclude b12x from mypy. Ruff's autofixes were not
  applied because F401 fixes strip re-exports from b12x's api.py modules.

AI-assisted.

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

### [fc8fdc1](https://github.com/flashinfer-ai/flashinfer/commit/fc8fdc17f702371302a0ea780c604b099b927196)

- **作者**: Luke Alonso
- **时间**: 2026-10-06T19:46:21Z
- **提交信息**: feat(experimental): migrate b12x to experimental submodule (#5767)

<!-- .github/pull_request_template.md -->

## 📌 Description

Embed b12x 1.5.0 kernels and shared preparation, autotuning,
compilation,
workspace, and checkpoint-loading infrastructure under
`flashinfer.experimental.b12x`, with corresponding tests and benchmarks.

Preserve `import b12x` through a compatibility package shipped by
`flashinfer-python`, with dependencies in the `b12x` extra. The
framework-independent
`b12x.loader` API exposes checkpoint sessions, shared reads, and
progress;
vLLM owns its model-loader adapter and registration.

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

- MLA and Trellis changes: 77 tests passed on SM120, covering FP32
partials,
allocation-stable CUDA graph replay, full-codeword decode, selection
rules,
  and prepared route-pack ownership across live row counts.

- Targeted SM120 checks: 82 passed, 8 skipped, and 15 subtests passed
across
cache integrity, tuning-key schemas, packaging, direct checkpoint
loading,
shared-read planning, and progress. The skips require four assigned
GPUs.
- All 6,536 embedded b12x tests collect successfully.
- Targeted composed suites on RTX PRO 6000 Blackwell Max-Q (SM120),
CUTLASS
  DSL 4.7.1: 215 MXFP4-CSF/selection tests, 177 MXFP8/selection tests,
126 stage-scale tests, 92 expansion tests, 55 block-sparse attention
tests,
  and 107 scale-decoder tests pass in FlashInfer. These suites overlap.
- On GPUs 8–11, four-rank DCP all-to-all and exact top-k exchange pass
in both
b12x and FlashInfer, including mixed-grid and skewed queued graph
replay.
The separate four-rank FP8 two-shot script passes reduce-scatter, exact
all-gather, and slot-parity checks. Two hardware-fault tests remain
gated off.
- Targeted b12x Compute Sanitizer checks pass for block-sparse
attention,
compressed-scale decoding, compact W4A8 graph replay, and MXFP8
execution.
Host backtrace reporting was disabled for runs where sanitizer reporting
  itself stalled; race checking retained hazard reporting.
- Physical RoCE, collectives requiring 8–16 GPUs, SM121, and full-model
serving
  were not qualified in this pass. The installed vLLM lacks
`B12xPreparationUnit`; its FP6 setup test fails identically on the
task-start
  b12x base and the MXFP8 branch.
- The unchanged-stat corruption regression fails on the original
implementation
  and passes with byte revalidation.
- The vLLM-owned loader suite passed all 24 tests in the
`local-inference-lab/vllm`
`dev/karmic-kraken` checkout with this FlashInfer change, using SM120
and disk-backed checkpoint fixtures.
- GDS tests require a supported disk filesystem. Fixtures under this
host's
`/tmp` (tmpfs) fail cuFile handle registration; disk-backed fixtures
pass.
- The full imported test suite is not passing; these results cover the
targeted
  checks above.

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: not yet assigned.
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
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
tests/experimental/b12x/
```

## Reviewer Notes

Uninstall the standalone `b12x` distribution (`pip uninstall b12x`)
before
installing `flashinfer-python[b12x]`. FlashInfer owns the top-level
`b12x` package;
co-installing both distributions can overwrite or remove each other's
files.

---------

Co-authored-by: Martin Vit <martin@voipmonitor.org>
Co-authored-by: derek <derek.yates@live.com>
Co-authored-by: Jason Cook <jasonc@maxlyn.com>
Co-authored-by: MadeBy561 <madeby561@gmail.com>
Co-authored-by: Brandon Music <brandon.m.music@gmail.com>

### [1ce02e5](https://github.com/flashinfer-ai/flashinfer/commit/1ce02e5774605399a8ddb8f47ea22749afb4c93f)

- **作者**: Zixin Huang
- **时间**: 2026-10-06T19:36:00Z
- **提交信息**: fix(comm): order the two-shot allreduce barrier so a growing grid cannot pass it early (#6091)

## 📌 Description

**Impact**
- **Correctness:** fixes silently wrong two-shot allreduce results. When
back-to-back calls grow the token count, up to **66% of output
elements** were wrong on B200, with no error raised.
- **Performance:** the two-shot path is also **8-67% faster** (up to
**3.0x** at ws=8, T=64: 75.5 -> 25.0 us per call), because each barrier
now does one system-scope release instead of up to 256.

**Details**

`Barrier::sync` in `include/flashinfer/comm/trtllm_allreduce_fusion.cuh`
(used by the two-shot path of `trtllm_allreduce_fusion`) writes the new
flag to all 256 slots, including the slots of CTAs that are not
launched, to avoid ABA. But it wrote the block's **own** slot first, and
a peer only waits on that slot. Seeing the own slot updated did not
imply the other slots were updated yet.

The flag cycles through 3 values. When the next two-shot call launches a
**larger grid**, a new block `j >= previous gridDim.x` can read a slot
that still holds the flag from two barriers ago. That value also differs
from `prev_flag`, so the barrier passes before the peer has written its
comm buffer, and the block reduces stale data. No extra synchronization
is needed to trigger it: back-to-back calls with a growing token count
are enough.

**Repro on 4x B200** (bf16, H=4096, `use_oneshot=False`, no host sync
between calls), calls T=5 -> 64 -> 64, repeated:
- on `main`, every T=5 -> 64 transition returns 2-11 wrong rows out of
64 (max abs error 4-13);
- the following T=64 -> 64 call is correct.

**Fix**
- Write the other slots first and the own slot last.
- The own-slot store is `st.release.sys` from the same thread, so a peer
that observes it also observes the other slots.
- The other stores can therefore be `st.relaxed.sys`. That leaves one
system-scope release per barrier instead of `256 / gridDim.x` of them.

The fix also makes the two-shot path faster. B200, bf16, 100 calls
captured in a CUDA graph, median per call, measured A/B/A:

| ws | T | H | main | this PR |
|---|---|---|---|---|
| 8 | 64 | 7168 | 75.5 us | 25.0 us |
| 8 | 1024 | 7168 | 75.5 us | 69.5 us |
| 4 | 256 | 4096 | 25.0 us | 20.3 us |
| 2 | 1024 | 4096 | 34.8 us | 31.0 us |

## 🔍 Related Issues

None filed. The same barrier code exists in TensorRT-LLM
(`allReduceFusionKernels.cu`).

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

New test: `test_trtllm_allreduce_fusion_twoshot_growing_grid`.
- It alternates T = world_size + 1 -> 256 -> 256 two-shot calls back to
back, for ws 2/4/8 and H 4096/7168.
- On 8x B200 it fails on `main` (28-66% of elements wrong on the first
large call) and passes with this PR.

Also on 8x B200 with this PR:
- `test_trtllm_allreduce_fusion.py` (H=4096 subset for ws 2/4/8, both
APIs, plus `gpu_offset`): passing.
- `test_trtllm_allreduce_fusion_pdl.py` and
`test_trtllm_allreduce_fusion_subgroup.py`: passing.
- Stress check: the growing-grid sequences (ws 2/4/8, T up to 1000) stay
correct with a 200 us `__nanosleep` inserted on one rank between the
relaxed stores and the own-slot release.

## Reviewer Notes

The ordering argument is the usual release/acquire one. All flag stores
to a given peer come from the same thread (`threadIdx.x ==
target_rank`), so the final release store orders the earlier relaxed
ones.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability of distributed all-reduce operations when
consecutive calls process different input sizes without host
synchronization, including transitions from smaller to larger workloads.
* **Tests**
* Added coverage for varied input sizes across multiple distributed
configurations to verify that consecutive all-reduce results remain
correct.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1390ea1](https://github.com/flashinfer-ai/flashinfer/commit/1390ea1006a9db12c9d06453686401d5e813c9d1)

- **作者**: Zixin Huang
- **时间**: 2026-10-06T19:35:33Z
- **提交信息**: fix(comm): size the allreduce fusion two-shot buffer by the element size (#6092)

## 📌 Description

**Impact**
- **Correctness:** fixes an out-of-bounds write in fp32 two-shot
allreduce at world size 2 when `token_num > max_token_num / 2`. On B200
one rank returned garbage (max error ~4.5e33) and the other **hung**,
although `is_buffer_size_sufficient` accepted the shape.
- **Cost:** no kernel change. Only the two-shot buffer of fp32
workspaces grows (2x), to the size the kernel actually writes.

**Details**

`trtllm_create_ipc_workspace_for_all_reduce_fusion` sizes the two-shot
comm buffer as `tp_size * max_token_num * hidden_dim * 2` bytes, which
hard-codes a 2-byte element. The two-shot kernel writes `2 * token_num *
hidden_dim` elements of the input dtype into each rank's buffer: the
scattered input plus the reduced shard. So with **fp32 and world size
2**, any call with `token_num > max_token_num / 2` writes past the end
of the buffer, even though `is_buffer_size_sufficient` accepts the
shape.

**Repro on 2x B200**: fp32, `max_token_num=1024`, T=1024, H=4096,
`use_oneshot=False`. On `main`, rank 1 returns garbage (max error
~4.5e33) and rank 0 hangs. T=512 is correct.

**Fix:** use 4 bytes per element when `use_fp32_lamport` is set, as the
lamport buffer already does. `is_buffer_size_sufficient` needs no
change, because the workspace metadata check already requires
`use_fp32_lamport` to match the input dtype.

## 🔍 Related Issues

None filed.

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

New test: `test_trtllm_allreduce_fusion_fp32_twoshot_max_tokens`, an
fp32 two-shot call at `max_token_num` for ws 2 and 4.
- On B200 the ws=2 case hangs on `main`; with this PR both cases pass.
- With this PR, T in {513, 700, 1024} is also correct.
- The existing `test_trtllm_allreduce_fusion.py` subset still passes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected workspace sizing for FP32 Lamport all-reduce so the
communication buffer can accommodate FP32 elements. This helps avoid
insufficient workspace allocation when using this mode.
* Added validation for FP32 two-shot all-reduce at the maximum supported
token count, including checks that results match the sum of inputs
across participating ranks.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [67c190f](https://github.com/flashinfer-ai/flashinfer/commit/67c190f7dc0c10d99e00401f20b4d0fdced007a0)

- **作者**: eigen
- **时间**: 2026-10-06T18:50:48Z
- **提交信息**: fix(cake_sparse_mla): trtllm-gen sparse-validity semantics, workspace contract and FP8 probability scale for the SM100/SM103 DSv4 sparse-MLA Cake programs (#6066)

## Summary

`backend="cake"` DSv4 sparse-MLA (SM100 / SM103): the Cake programs now
reproduce trtllm-gen's sparse validity
semantics on every production route, and the host binds the full query
layout and an exact workspace contract.

Combined column `c` of metadata row `t` is attended iff `c <
clamp(sparse_topk_lens[t] + offset, 0, sparse_topk)`,
the staged index is not `-1`, and (`c >= 128` or `c < visible(t)`) with
`visible(t) = clamp(seq_lens[b] - (q_len_b - 1 - q_off), 0, 128)`. A
`-1` inside the active length is masked
(excluded from numerator and denominator); a row without an attendable
column writes the zero result.

Fixes the correctness regression tracked as CAKE-944 (sliding-window
`seq_lens` not applied; `-1` inside the SWA tile /
the compressed active length attended on several routes; poisoned tail
leaking through the FP8 H32 topk4x split path)
and the host contract tracked as CAKE-939 (workspace sizing, counter
reset inside the launch contract, no raise under
CUDA-graph capture).

## Host changes (`flashinfer/mla/cake_dsv4.py`,
`flashinfer/mla/_core.py`)
- Every variant binds the five query-layout parameters (`seq_lens`,
`cum_seq_lens_q`, `ragged_query`, `max_q_len`,
`batch_size`); dense rows pass `seq_lens` for the unread
`cum_seq_lens_q`.
- `cake_dsv4_workspace_requirement()` returns the exact per-route
requirement; the row-tiled host path keeps sglang's
fixed 128 MiB buffer usable for any row count on the routes that support
tiling (documented exceptions).
- Counter reset is part of the launch contract; preconditions documented
(`sparse_topk_lens[t] + offset >= 1`,
  `seq_lens[b] >= q_len_b`).
- 1-D int32 vectors are bound as the caller's object (boundary-beacon
tests).

## Regenerated programs
- `csrc/cake_dsv4/{common,sm_103a,sm_100a}/*` and the `_PLAN_*_QLAYOUT`
constants / per-arch registries in
`flashinfer/jit/cake_dsv4.py`: exported from Cake b6677263b63 (the Cake
MR tip) with the Cake export protocol
(197 shapes per arch = 94 canonical + 103 hardening; correctness +
source/export timing parity gates, every
canonical row faster than trtllm-gen). The exporter folds the variants
both architectures compile from
identical source into `common/` (thirteen after round 2: the two FP8 H64
m64 variants joined them once both
arches carried the sink fix; the stale pre-round `common/` m64 copies,
referenced by neither registry, are replaced)
and keeps the rest per architecture. Round-2 release commit:
`d07e7383bbba2aa3f01b64ffedf311bfcfa1a745`; round-4 release commit of
this branch: `e136478a02b3a052c1556334fcaefeb0318abede` (sm_103a
`f92e3bd20`, sm_100a `e136478a0`); round-5 release commit of this
branch: `64cedcfeda28d02d645051cf999ae2cb178e1503` (sm_103a `9a0a59bab`,
sm_100a `64cedcfed`); round-6 release commit of this branch:
`80063ebea7dc2816fe1ef5701d36bf45daf038cb` (sm_103a `ee83b72c3`, sm_100a
`80063ebea`); merge-with-main release commit of this branch:
`332ef122b60b88c92ad2d0d7f84d63da5a871965` (sm_103a `e8f544925a5`,
sm_100a `332ef122b60`).
- Round 2 of the export carries the FP8 attention-sink fix found by this
suite (CAKE-989): the five FP8
programs had seeded the online softmax with the sink in both key-half
warps (exp(sink) counted twice) and
quantised P against the sink; with `sinks=None` they already matched
trtllm-gen to four digits.

- Round 4 (CAKE-992) carries the FP8 probability scale: the FP8 programs
form `P' = 2^8 * P = exp2(fma(s, scale_log2, 8 - max * scale_log2))`
before the e4m3 conversion (row sum, sink fold and the stored partial
LSE carry the same factor), so many-column rows are
quantised in e4m3's normal range instead of its subnormals. Measured on
the hardening suite and the Cake probe rows the scale changes
nothing at four-digit resolution on either arch (the test rows are
near-uniform, every P rounds to one e4m3 code at any scale), so
it is kept as hygiene and does not close CAKE-992. Exported from Cake
`617752955bd` (kernel commits `4340605d465` +
`89d0ccf739d`); the BF16 programs render byte-identically, host files
unchanged. The precision level is unchanged (contract
  tolerances kept; bits differ).

- Round 5 (performance only, no semantic change): the three FP8 families
that read 2-7 % slower than the round-18 programs in the
round-4 paired ABBA (single-CTA FP8 low-head, FP8 H64 source-exact, and
the persistent FP8 H64 m64 body on sm_103a) are
re-scheduled with bit-identical output: the trtllm-gen SWA window is
resolved off the softmax critical path (taken after the
TMEM seeding / first-tile gathers / `q_full` wait in the single-CTA
body; published by the index warp through a two-slot SMEM
ring in the sm_103a m64 body; computed from the body's own request range
with the next tile's `-1` quad prefetched in the
source-exact body). Exported from Cake `a315fb4adbe`; the six affected
programs change per arch (`fp8_lowhead_prefill`,
`fp8_h64_source_exact` on both; the m64 pair on sm_103a only), every
other program and the host files render byte-identically
to the round-4 release. Release commit of this round: `64cedcfed`
(sm_103a `9a0a59bab`, sm_100a `64cedcfed`).
- Round 6 (performance only, no semantic change): the request table of
the trtllm-gen SWA window scan is staged in registers at
role entry (`WINDOW_STAGED_REQUESTS`): each lane of the resolving warp
loads one `cum_seq_lens_q` entry and one `seq_lens` entry
for request chunks 0/1 (batch <= 64; larger batches keep the chunk
loop), so per work item the request index is two ballots
and the window bounds six warp shuffles instead of two dependent global
round trips on the softmax critical path. Output bits
are identical to the round-5 programs. Exported from Cake `2e17a6a8648`;
the whole-tile FP8 H64 program changes on both arches
and the FP8 H64 m64 pair on sm_100a only (the sm_103a m64 pair keeps the
round-5 index-warp ring, which measured as fast; the
FP8 H128 v76 pair is unchanged on both arches because the lever measured
neutral there); every other program and the host
files render byte-identically to the round-5 release. Release commit of
this round: `80063ebea` (sm_103a `ee83b72c3`,
  sm_100a `80063ebea`).
- Merge with main (no semantic change): the branch was merged with Cake
main (DSv4 round 20, native NVFP4 families, exporter
changes) and this PR was merged with upstream FlashInfer main (b4470edcc
resolves the host-file conflict with #6103 by
keeping both workspace additions). Every DSv4 sparse-MLA program was
re-exported from the merged Cake tree `b9595e806ef`
against b4470edcc on both architectures: 23 of 27 registered programs
per architecture have unit bodies byte-identical
to the round-6 release (kernel-symbol / host-shim-namespace tokens
aside); the four bf16 reducers
(`bf16_h128_split5_reduce`, `bf16_h32_topk128x_early_v47`,
`bf16_h64_compressed_reduce`, `split_reduce`) carry main's
bf16-pair unpack lowering (inline asm replaced by shift/mask C++; nvcc
13.3 sm_103a emits byte-identical `.text` for
the compressed reducer). Architecture-neutral programs ship one
`common/` text for both architectures
(`fp8_h64_source_exact` and `fp8_lowhead_h64` join them with the text of
their round-6 sm_100a units; the three reducers
that now render per architecture move to `sm_100a/` + `sm_103a/`); the
NVFP4 DSv4 decode registrations of #6103 are
untouched. Release commits of this round: sm_103a
`e8f544925a5a4bb7386a0709d25e1ebcd72ead3e`, sm_100a
`332ef122b60b88c92ad2d0d7f84d63da5a871965` (= PR head).

## Tests
- `tests/mla/test_cake_dsv4.py`,
`tests/mla/test_cake_dsv4_hardening.py`: poisoned tail, `-1` inside
lens, unaligned
lens, short `seq_lens` window, sglang conventions (dense `[B,1,H,512]`,
MTP `[B,4,H,512]`, varlen prefill),
workspace cap and capture tests. Each case checks (a) elementwise
closeness at the contract tolerances
(bf16 atol = rtol = 1e-2, fp8 1e-1), (b) a per-(row, head) relative L2
error normalised by the attended-mass
scale `sqrt(sum_c p_c ||v_c||^2) x sink factor` (bf16 0.02 / fp8 0.1) --
normalising by `||expected||`
instead is ill-conditioned on rows whose SWA (-0.2) and compressed
(+0.25) value pools cancel and turned FP8
P precision into spurious validity failures -- and (c) bit-identity
under a poisoned page / `-1` slots.
The message of a relative failure names the worst row's active / visible
counts and trtllm-gen's own
  relative error on the same inputs.

## Evidence (full acceptance table in [Cake
!1211](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1211))
Merge-with-main round (Cake b9595e806ef / fb0bfbe5965, FlashInfer
332ef122b60b88c92ad2d0d7f84d63da5a871965), both architectures; step ids
in the Cake acceptance table:
- Cake `check_rows` all mutation axes 839/839 (both); GPU e2e dsv4 slice
37 passed / 1 pre-existing unrelated failure (both);
CPU rule tests 928 passed / 6 skipped (one test rewritten for main's
fixed-Q route retirement); render diff vs the
round-6 tree: exactly the four (sm_103a) / five (sm_100a) bf16 reducer
programs differ, v76 and every staged-window FP8
  program identical.
- compute-sanitizer synccheck + memcheck on the changed-program rows:
GB300 6/6 + 6/6, B200 6/6 + 6/6; 0 errors.
- Export r957n (197 shapes per arch): sm_103a 196/197 --
hardening-000105 (`bf16_h64_compressed`, 10 us) passes correctness
and fails only the directional-disagreement measurement gate
(source/export 0.990; export-first 1.026 / source-first
0.962) with the reducer's machine code byte-identical to round 6
(accepted 2026-10-06 as a measurement-protocol artifact); sm_100a
195/197 -- hardening-000016 / hardening-000036 (bf16_h64_prefill, 44 us)
pass correctness and fail only the directional-disagreement measurement
gate in every measurement (disagreement 0.050-0.067 vs 0.05,
source/export 0.986-1.005; the program is byte-identical to round 6,
where 000016 failed the same gate), presented for acceptance.
A later closed-prior re-measure on a node not used before on each
cluster (GB300 nvl72d396-T12, B200 gpu-96) reproduced the same gate
signature on exactly these rows (0.061 / 0.069 / 0.056 vs the 0.05
threshold) while the control rows pass, so the failure is a systematic
arm-order effect of the measurement protocol on these 10-44 us rows (the
second-measured arm runs 3-4 % faster), not a kernel difference;
correctness passes on every measurement.
- FlashInfer GPU tests on a fresh clone of
332ef122b60b88c92ad2d0d7f84d63da5a871965: GB300 519 passed / 4 skipped
(2e5859fd, fresh clone at 332ef122b60, 167 s); B200 519 passed / 4
skipped (85c1fa30, fresh clone at 332ef122b60, 212 s).
- Paired CUPTI ABBA vs the round-18 units transfers from round 6: all
nine FP8 ABBA programs have byte-identical unit
bodies, no FP8 row routes through a changed reducer. GB300 geomean
0.9961 [0.968-1.035] (1 row > 1.02: hardening-000032
1.035); B200 B/A geomean 1.0007 [0.958-1.029] over the 66 paired rows
(legs A1 B1 from r957m2 steps on 2153493/2154xxx, B2 A2 from r957m4
shards 0339ac37 / 19c207c2 / 50627f45 / 893a1b26 on 2156459): 2 rows >
1.02 = hardening-000017 1.029, hardening-000011 1.028; 0 rows < 1.0 vs
trtllm-gen (min trtllm-gen/cake 1.203). Rows above 1.02 vs round 18
after paired re-measure (disclosed for acceptance, nothing
assumed accepted): GB300 hardening-000032 1.035; B200 hardening-000017
1.029, hardening-000011 1.028.

Round 6 (Cake 2e17a6a8648, FlashInfer
80063ebea7dc2816fe1ef5701d36bf45daf038cb), both architectures unless
noted; step ids in the Cake acceptance table:
- Cake validity rows `checksel` 11/11 PASS on the affected rows (both),
output bits identical to the round-5 tree a315fb4adbe;
`check_rows` all mutation axes 839/839 (both); render diff vs
a315fb4adbe: exactly the re-scheduled programs differ (sm_103a 1,
sm_100a 3).
- GPU e2e dsv4 slice 33 passed / 1 pre-existing unrelated failure
(both); CPU rule tests 884 passed / 6 skipped (all 74 `test_dsv4_*.py`,
both).
- compute-sanitizer synccheck + memcheck on the changed-program rows
(decode-000008 / decode-000011 whole-tile, hardening-000022 /
hardening-000028 m64,
plus the v76 rows hardening-000011 / decode-000030 as controls): GB300
6/6 + 6/6; B200 4/4 + 4/4 (whole-tile and m64 rows; the v76 program is
unchanged on B200); 0 errors.
- Export r957m (197 shapes per arch, correctness + source/export
timing-parity gates): sm_103a 197/197 (full run 91a7924e + same-identity
retry 9e5993cc of four sub-10-us timing-parity rows); sm_100a 196/197
(full run 6810edbd + same-identity retries 3483eaa3 / b5496786; the one
open row, hardening-000016 on the unchanged BF16 H64 prefill program,
fails only the directional-disagreement gate with identical values in
both retries: export-first 1.037 / source-first 0.968, symmetric 1.0036,
correctness pass).
- FlashInfer GPU tests on a fresh clone of 80063ebea: GB300 519 passed /
4 skipped (b60e39e3, fresh clone at 80063ebea, 162 s); B200 519 passed /
4 skipped (ed58cbe1, fresh clone at 80063ebea, 205 s).
- Paired CUPTI ABBA vs the round-18 units on the 66 FP8 rows (A1 B1 B2
A2): GB300 B/A geomean 0.9961 [0.968-1.035] over the 66 paired rows (4
legs A1 B1 B2 A2, shards 03b32239 / 927f56a0 / 9324c82e / a04b4b07 on
844048): 1 row > 1.02 = hardening-000032 1.035 (both pairs 1.035; M64
index-warp ring row, unchanged by this round's lever, same value as
round 5), 0 rows < 1.0 vs trtllm-gen (min trtllm-gen/cake 1.223);
whole-tile decode rows 0.968-1.000, M64 rows 0.993-1.035, v76 rows
1.002-1.018; B200 B/A geomean 1.0007 [0.958-1.029] over the 66 paired
rows (legs A1 B1 from r957m2 steps on 2153493/2154xxx, B2 A2 from r957m4
shards 0339ac37 / 19c207c2 / 50627f45 / 893a1b26 on 2156459): 2 rows >
1.02 = hardening-000017 1.029, hardening-000011 1.028; 0 rows < 1.0 vs
trtllm-gen (min trtllm-gen/cake 1.203).
Remaining rows above 1.02 vs round 18 after the paired re-measure
(disclosed for acceptance; accepted 2026-10-06 at the measured level):
GB300 hardening-000032 1.035; B200 hardening-000017 1.029,
hardening-000011 1.028.

Round 5 (Cake a315fb4adbe, FlashInfer
64cedcfeda28d02d645051cf999ae2cb178e1503), both architectures unless
noted; step ids in the Cake acceptance table:
- Cake validity rows `checksel` 129/129 PASS on the changed-program rows
(both), output bits identical to the round-4 tree 617752955bd;
`check_rows` all mutation axes 839/839 (both); render diff vs
617752955bd: exactly the six re-scheduled programs differ per arch.
- GPU e2e dsv4 slice 33 passed / 1 pre-existing unrelated failure
(both); CPU rule tests 884 passed / 6 skipped (all 74 `test_dsv4_*.py`,
both).
- compute-sanitizer synccheck + memcheck on the changed-program rows:
GB300 7/7 + 7/7 rows 0 errors; B200 3/3 + 3/3 rows 0 errors (single-CTA
decode-000006 / hardening-000020, source-exact prefill-style-000087; the
v76 and m64 programs are the round-4 programs sanitized in round 4).
- Export r957k (197 shapes per arch, correctness + source/export
timing-parity gates): sm_103a 197/197 passed (round-1 run on da240432f9d
whose sm_103a programs are byte-identical to a315fb4adbe, provenance
re-run on a315fb4adbe retained all 197 receipts; trtllm-gen/export
geomean 1.511), sm_100a 197/197 passed on a315fb4adbe (195 + 2
timing-parity rows re-measured in the same-identity retry;
trtllm-gen/export geomean 1.453).
- FlashInfer GPU tests on a fresh clone of 64cedcfed: GB300 519 passed /
0 failed / 4 skipped (293df1f5, fresh clone of 64cedcfed, clean, 165 s);
B200 519 passed / 0 failed / 4 skipped on a second fresh clone
(8d6f6294, 208 s); the first fresh clone (2cb713bf) read 518 passed / 1
failed: test_cuda_graph_replay_matches_eager[h32-bf16-q1] tripped its
exact-equality "eager call allocated" pre-check because allocated memory
DROPPED 1.07 GB -> 175 MB during the call (Python GC releasing earlier
tests' tensors), i.e. not a kernel allocation.
- Paired CUPTI ABBA vs the round-18 units on the 66 FP8 rows (A1 B1 B2
A2): GB300 66 rows, B/A geomean 0.997 (0.960-1.032), every row >= 1.387x
trtllm-gen; 3 rows > 1.02 (hardening-000032 1.032, decode-000011 1.031,
decode-000008 1.028), paired re-measure 1.035 / 1.031 / 1.003; B200 66
rows, geomean 1.0015 (0.951-1.040), every row >= 1.212x trtllm-gen, 0
correctness failures; 5 rows > 1.02 in the sweep (hardening-000034
1.040, hardening-000017 1.030, hardening-000028 1.028, hardening-000011
1.025, hardening-000032 1.024) plus decode-000008 / decode-000011 (sweep
1.019 / 1.020) that re-measure above 1.02; paired re-measure (pairs
equal to 3 digits): hardening-000034 1.034, hardening-000028 1.026,
hardening-000032 1.018, hardening-000017 1.030, hardening-000011 1.029,
decode-000008 1.025, decode-000011 1.022.
Remaining rows above 1.02 vs round 18 after the paired re-measure
(disclosed for acceptance; accepted 2026-10-06 at the measured level):
GB300 hardening-000032 1.035 (m64 persistent body with the sm_103a
index-warp ring), decode-000011 1.031 and decode-000008 1.003
(whole-tile FP8 H64 body, one-wave ~10 us rows); B200 hardening-000034
1.034 and hardening-000028 1.026 (m64 persistent body, unchanged on
sm_100a), hardening-000017 1.030 and hardening-000011 1.029 (v76
persistent body, unchanged on both arches), decode-000008 1.025 and
decode-000011 1.022 (whole-tile FP8 H64 body, unchanged),
hardening-000032 1.018 (m64; 1.024 in the sweep). Every row keeps >=
1.21x trtllm-gen.

Round 4 (Cake 617752955bd, FlashInfer e136478a0), both architectures
unless noted; step ids in the Cake MR table:
- Cake validity rows `checksel` 203/203 PASS (GB300 + B200), per-row
output bits identical to the kernel tree 4340605d465;
`check_rows` all mutation axes 839/839 (both); diag3 109 hardening rows
x base/neg_swa/neg_comp: 0 Cake ZERO cells, 0 Cake errors (both).
- GPU e2e dsv4 slice 33 passed / 1 pre-existing unrelated failure
(both); render diff vs 4340605d465 byte-identical on 28/29 + 29/30
programs, the remaining one identical after canonical temporary
renumbering; CPU rule tests 159 passed (both).
- compute-sanitizer synccheck + memcheck on the 10 changed-program rows:
GB300 10/10 + 10/10 rows 0 errors; B200 synccheck 10/10 + memcheck 10/10
rows 0 errors.
- compute-sanitizer on the e2e-only cluster-2 unsplit FP8 trace (not a
production route): synccheck 0 errors on both arches (GB300 3238 s and
B200 4168 s, each `1 passed` + `ERROR SUMMARY: 0 errors`); memcheck
exceeded the 90-min per-tool cap on GB300 (residual).
- Export r957j (197 shapes per arch, correctness + source/export
timing-parity gates): sm_103a 197/197 (two timing-parity rows
re-measured
  in a retry on the sealed prior), sm_100a 197/197 first run.
- FlashInfer GPU tests on a fresh clone of e136478a0: GB300 519 passed /
0 failed / 4 skipped (`tests/mla/test_cake_dsv4*.py`, fresh clone, 164
s); B200 519 passed / 0 failed / 4 skipped (229 s).
- Paired CUPTI ABBA vs d07e7383 (134 rows x A1 B1 B2 A2): GB300: geomean
1.003 vs round 18, every row >= 1.10x trtllm-gen, 11/134 rows 2.9-6.9 %
slower than round 18 on paired re-measure (FP8 low-head decode x10 + one
FP8 H64 source-exact row; attribution ABBA shows the round-4 FP8
probability scale costs 0.0000 -- the residual is the corrected validity
semantics; listed for acceptance in the Cake MR); B200: B200: geomean
1.005 vs round 18, every row >= 1.137x trtllm-gen, 19/134 rows 2.2-11.0
% slower than round 18 on paired re-measure (FP8 low-head decode x15 at
2.2-6.6 %, FP8 H64 source-exact prefill-style-000087/000091 at 11.0 %,
FP8 H128 persistent runtime hardening-000017/000011 at 3.2/2.5 %;
attribution round-3e vs round-4 export: geomean 0.998 (0.995-1.002), 0
rows > 1.02 -- the round-4 FP8 P scale is perf-neutral on B200 as well
(the two v76 lazy-threshold rows hardening-000017/000011 at 1.00x), so
the residual is the round-3 validity semantics (the window resolution on
the critical path of fp8_lowhead_decode, fp8_h64_source_exact and the
v76 body)).
- e2e DeepSeek-V4-Flash FP8 TP4 GSM8K (dlcluster GB200, sm_100a
programs): baseline 0.960 / Cake route 0.970 (100 q, 0 invalid, route
taken on every rank, decode throughput identical; FP8 bits differ, max
|delta logprob| 0.28 on 8 greedy prompts); 200-q confirmation: Cake
0.975 vs baseline 0.965, prefill/decode throughput equal in both arms;
the sglang EAGLE/MTP arms could not start on this engine build
(branch-side worker bug, identical for stock).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for dense and ragged query layouts across CAKE attention
variants, with sequence-aware sliding-window visibility.
* Added per-route workspace estimates and row-tiled execution when
available workspace cannot fit all rows.
* Exposed query-layout metadata and workspace requirements through the
MLA interface.
* **Bug Fixes**
* Improved handling of invalid attention indices and zero-active-top-k
cases.
* Improved split-merge counter initialization during regular execution
and CUDA Graph capture.
* **Documentation**
* Clarified workspace sizing, row tiling, query-layout metadata, and
sequence-length behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c4931aa](https://github.com/flashinfer-ai/flashinfer/commit/c4931aa59339e6d9ec02a5d702eb03c3c0886cbe)

- **作者**: Yanqin Zhai
- **时间**: 2026-10-06T18:46:44Z
- **提交信息**: Yanqinz/move frost out from experiment (#6035)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adding Frost to MoELayer's backend pool delivers up to 1.78x speedup,
with the largest gains in MXFP8 at larger token counts.

Compared the existing backend pool against the same pool plus Frost on
the same PR checkout, with each pool independently autotuned.
Benchmarked 576 cases on SM107 with unlocked clocks: 8 model shapes, 4
dtypes, 9 token counts (1-16,384), and uniform/skew routing.
Measurements cover synthetic single-layer MoELayer GPU latency using
warm CUDA Graph replay, EP=1; input quantization, weight preparation,
and autotuning are excluded.

MXFP8 speedups by model and token count (before/after latency; geometric
mean across the two routing distributions):

| Model shape | 1,024 tokens | 4,096 tokens | 8,192 tokens | 16,384
tokens |
| --- | ---: | ---: | ---: | ---: |
| DeepSeek V2 Lite | 1.16x | 1.58x | 1.75x | 1.76x |
| Mixtral 8x7B | 1.37x | 1.63x | 1.58x | 1.59x |
| DeepSeek V4 Flash | 1.04x | 1.16x | 1.45x | 1.57x |
| DeepSeek V4 Pro | 1.03x | 1.12x | 1.31x | 1.54x |
| MiniMax M2.5 | 1.08x | 1.30x | 1.55x | 1.70x |
| MiniMax M1 | 1.12x | 1.38x | 1.44x | 1.45x |
| Qwen3-235B | 1.08x | 1.39x | 1.51x | 1.66x |
| Kimi K2 | 1.05x | 1.14x | 1.37x | 1.49x |

- MXFP8: 1.155x geometric mean across all cases; 1.464x at T >= 4,096.
Peak: DeepSeek V2 Lite, T=16,384, uniform routing, 1060.78 -> 596.13 us
(1.779x).
- MXFP4 weights / MXFP8 activations: 1.052x overall; 1.125x at T >=
4,096, peaking at 1.463x on Mixtral 8x7B at T=16,384.
- BF16 and NVFP4 are broadly unchanged overall (1.002x / 1.008x), with
individual DeepSeek V2 Lite T=1 cases reaching 1.13x / 1.41x.
Small-token workloads (T <= 64) are broadly unchanged on average across
all four dtypes.

One MiniMax M2.5 W4A8 case at T=4,096 showed 7.3% higher latency; a
fresh autotune run was at parity. The original regression remains in the
statistics. One Kimi K2 NVFP4 baseline numerical mismatch did not recur
in either the single-case or original-order rerun; its root cause
remains unresolved.


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

### [09fdb12](https://github.com/flashinfer-ai/flashinfer/commit/09fdb12e9ae6e155bbc22c4c76d45a656a39cf82)

- **作者**: Tian Zheng
- **时间**: 2026-10-06T18:03:27Z
- **提交信息**: feat: Add SM100 cuteDSL ReplaySSM GDN MTP decode kernels (#5314)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Add SM100-family ReplaySSM verification and accepted-prefix commit to
FlashInfer GDN MTP. Speculative verification normally stores a full FP32
recurrent state after each token so an accepted prefix can be committed.
This PR keeps the checkpoint frozen during verify and saves only raw
K/V, log-decay and sigmoid-beta windows, then reconstructs the accepted
state in one all-layer commit launch.

- Extend `flashinfer.gdn_decode.gated_delta_rule_mtp` with opt-in
`cache_replayssm` and four caller-owned window buffers.
- Add `flashinfer.gdn_decode.gated_delta_rule_replayssm_commit`. Verify
writes the windows by pool slot; commit consumes the accepted prefix
exactly once before the next verify overwrites it.
- On SM100/SM103, use TMA and tcgen05 TF32 contractions for frozen FP32
128x128 checkpoints, normalized Q/K, T=4..8, B=1..256, BF16 output,
int32 indices and an even value-head/key-head ratio. Other supported
SM100 inputs use the FP32 MTP fallback.
- For normalized K without tracking, commit auto selects tcgen05 for
T=8, or T=6/7 when B>1 and `layers * B * HV >= 256`; otherwise it uses
SIMT. Explicit tcgen05 supports T=4..8. `backend="simt"` retains FP32
contractions, and optional tracked checkpoints use the SIMT path. TF32
outputs/checkpoints are not bitwise identical to FP32 recurrence.
- Preserve upstream device-specific compile targets and persistent
CuTe-DSL caches, including layout-sensitive cache identities; add API
docs, trace templates and trace examples.

ReplaySSM is restricted to FP32 checkpoints, K=V=128 and SM100/SM103.
FP16 inputs follow the existing MTP BF16 conversion convention. Live
source slots must be unique and in range; optional track destinations
must be disjoint from all live source and track slots. Zero acceptance
and reserved slots are no-ops. These device-side index contracts are
documented without introducing host synchronization.

Dispatch uses tcgen05 for eligible T=4–8 verification and, with
normalized K and no tracking, for T=8 commit or T=6/7 commit when B>1
and `layers * B * HV >= 256`; other cases use the generic verify or SIMT
commit path.

### Performance

All values are microseconds. Verify columns are per layer; commit and
total columns cover four layers. Full acceptance (4/4 or 8/8):

| B | T | Upstream verify + snapshots | ReplaySSM verify | Upstream
total | ReplaySSM total | Speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 4 | 5.50 | 4.17 | 27.82 | 22.90 | 1.21x |
| 8 | 4 | 19.27 | 5.14 | 122.23 | 49.53 | 2.47x |
| 16 | 4 | 38.09 | 11.67 | 240.71 | 112.50 | 2.14x |
| 32 | 4 | 80.80 | 18.35 | 497.68 | 214.75 | 2.32x |
| 64 | 4 | 156.67 | 30.89 | 972.86 | 418.47 | 2.32x |
| 128 | 4 | 319.87 | 61.74 | 1971.26 | 843.94 | 2.34x |
| 256 | 4 | 652.36 | 126.54 | 3992.64 | 1730.32 | 2.31x |
| 1 | 8 | 8.83 | 4.53 | 40.92 | 26.18 | 1.56x |
| 8 | 8 | 35.87 | 6.47 | 188.43 | 54.64 | 3.45x |
| 16 | 8 | 77.78 | 11.92 | 399.56 | 113.32 | 3.53x |
| 32 | 8 | 156.49 | 19.30 | 800.22 | 220.33 | 3.63x |
| 64 | 8 | 297.30 | 34.96 | 1537.35 | 436.24 | 3.52x |
| 128 | 8 | 605.23 | 71.27 | 3116.81 | 891.46 | 3.50x |
| 256 | 8 | 1246.78 | 147.81 | 6378.51 | 1845.57 | 3.46x |

The full-acceptance total improves **1.21–3.63x**. Ordinary MTP without
ReplaySSM stays within 0.1% of the baseline at the slowest observed
point; small-batch calls benefit from removing the unused-buffer memset.

## 🔍 Related Issues

<!-- Link any related issues here -->
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

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

- ReplaySSM tests including T=3 lifecycle coverage: **198 passed, 16
skipped** (unsupported tcgen05 combinations).
- T=3-focused racecheck: **11 passed, 6 skipped; 0 hazards, 0 errors, 0
warnings**.
- Prior T=4..8 cycle/single-request/CUDA-graph racecheck: **67 passed,
10 skipped; 0 hazards, 0 errors, 0 warnings**.
- Final MTP regression selection: **86 passed**.
- Prior cache naming and device-target checks: **88 passed, 2 skipped**
(requires a second GPU).
- Prior GDN trace and template consistency: **24 passed**.
- Memcheck including T=3 lifecycle coverage: **198 passed, 16 skipped; 0
errors**.
- All pre-commit hooks passed on the modified source, tests, docs and
generated JSON.

The 198 ReplaySSM tests cover the final native-window implementation and
dispatch policy, including the T=3 lifecycle additions. The 86 selected
MTP regressions passed on the same unchanged kernel implementation.
Cache/device-target and trace results above are from earlier validation.
An earlier broad decode/MTP pass completed with 474 passed and 5
skipped; it is not counted as a full-suite run of the final candidate.

The independent oracle evaluates the sequential GDN recurrence in FP64,
including Q/K normalization with epsilon 1e-6, then compares verify
outputs and committed states. Test tolerances are output `atol=1e-4,
rtol=1e-2`, SIMT checkpoint `atol=2e-6, rtol=1e-5`, and TF32 checkpoint
`atol=1e-4, rtol=1e-3`. Frozen checkpoints, raw BF16 caches, padding
outputs and unused cache slots are checked exactly; gate windows use
`atol=rtol=2e-6`.

Unit tests in `tests/gdn/test_replayssm_spec_fold.py` cover the T=3
fallback lifecycle, native T=4..8 paths and dispatch policy directly:

| Test | Coverage |
|---|---|
| `test_replayssm_verify` | T=3 at B=2 and B=17 (inline and
warp-specialized fallback), plus T=5/6/7 at B=1 and B=17, against the
FP64 oracle; additional short-window cases cover all-padding rows,
inner-strided Q/K/V and strided gate parameters. Frozen checkpoints, raw
windows and untouched slots are checked. |
| `test_replayssm_verify_commit_cycles` | Each T=3..8, every accepted
length from 0 through T, two layers and two verify/commit rounds. Covers
explicit SIMT/tcgen05 where supported, normalized/unnormalized SIMT,
intermediate/final accepted-step tracking (including T=3), null and
zero-accept rows. Rejected cache suffixes are filled with NaNs. |
| `test_replayssm_single_request_commit` | B=1 for each T=3..8,
accepting 1, T-1 or T tokens, with auto/SIMT and tcgen05 where supported
(T=4..8). Checks output and committed state, rejected-tail NaNs, and
valid aligned storage-offset views. |
| `test_replayssm_commit_dispatch` | T=3/4/5 auto stays on SIMT; T=6/7
tests both sides of the grid threshold (224 versus 256 layer/batch/head
work units), equivalent multi-layer shapes, and B=1 exclusion even at
256. Also covers explicit backend overrides, T=8 auto and T=9 fallback.
These are routing assertions; numerical correctness is checked by the
tests above. |

Additional coverage includes explicit tcgen05 rejection for T=3, T=16
fallback, B=256/257 and head-pair boundaries, FP16/BF16 inputs,
FP32/BF16 outputs, int32/int64 indices, noncontiguous state fallback,
zero Q/K, extreme gates, 16-byte base-alignment validation, argument
errors and CUDA graph capture. Memcheck was rerun on the full ReplaySSM
test file. Focused T=3 racecheck covers both verify fallback kernels and
the T=3 lifecycle; earlier racecheck covers the T=4..8 cycles,
single-request commit and CUDA graph cases.

The 109 benchmark points additionally check output, raw-window and
checkpoint equivalence before timing. They are external performance
evidence; the full benchmark shape matrix is not duplicated in the unit
tests.

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

### How to review

Follow one request through the code: verify reads a frozen checkpoint
and writes raw K/V plus gate windows by **state-pool slot**; commit
replays only the accepted prefix into that checkpoint across all layers.
Start with the API and SIMT commit to establish the state semantics,
then compare the tensor-core implementations against the same
recurrence.

| File (suggested reading order) | What changed and why | Review focus |
|---|---|---|
| `flashinfer/gdn_decode.py` | Adds opt-in ReplaySSM buffers to
`gated_delta_rule_mtp` and the public
`gated_delta_rule_replayssm_commit` entry point. Validates metadata and
16-byte base alignment before launching kernels. Reuses an existing
tensor for the unused intermediate-state argument to avoid a per-call
memset. | Frozen checkpoint semantics; pool-slot versus batch indexing;
buffer ownership; shape/dtype/alignment checks. Index values and
non-aliasing remain documented caller contracts, avoiding host
synchronization. |
| `docs/api/gdn_decode.rst` | Documents the verify → accept → commit
lifecycle, public commit API, supported shapes, dispatch and TF32
precision tradeoff. | Confirm callers can allocate the windows, select a
backend and reuse the checkpoint without depending on internal kernel
details. |
| `flashinfer/gdn_kernels/gdn_replayssm_spec_fold.py` | Adds shared
commit validation/dispatch and the SIMT implementation. A warp keeps a
stripe of FP32 state in registers and applies accepted updates
sequentially; optional tracking writes an intermediate accepted state.
This is the direct recurrence against which to read the tensor-core
path. | Zero acceptance and reserved slots must not write; tracking is
zero-based and restricted to the accepted prefix. Check the auto
threshold independently of explicit backend support. |
| `flashinfer/gdn_kernels/gdn_decode_mtp.py` | Extends both existing MTP
kernels to capture raw windows while computing verify outputs, providing
the fallback outside tcgen eligibility. Fuses cache writes with
input/gate preparation, adds the tcgen dispatcher, and distinguishes
ReplaySSM/layout variants in compilation caches. Also fixes strided Q/K
loads and overflowing softplus evaluation. | The `cache_replayssm=False`
path should retain ordinary MTP behavior. Check unique ownership of
raw-cache writes, padding preservation, FP16/output staging and cache
keys for stride-sensitive CuTe layouts. |
| `flashinfer/gdn_kernels/gdn_decode_mtp_replayssm_tcgen.py` | Adds the
T=4..8 verify specialization. TMA streams the checkpoint; tcgen05
computes checkpoint–K/Q products, and a small Gram matrix drives the
low-rank recurrence without materializing per-token state snapshots. B=1
uses one value head per CTA; larger batches pair adjacent heads to share
Q/K work. | Compare outputs/raw windows with the generic path. For
T=5/6/7, unused MMA columns are zeroed while logical IO retains the
actual T. Check SMEM publication, head sharing and frozen-state
behavior. |
| `flashinfer/gdn_kernels/gdn_replayssm_spec_fold_tcgen.py` | Adds
normalized T=4..8 commit using an eight-column MMA tile, an
accepted-prefix coefficient recurrence, and a final low-rank state
update. The logical cache length is distinct from the padded MMA width
and is part of the compile key. | No reads beyond the logical window;
rejected keys are zeroed before normalization so rejected-tail NaNs
cannot enter the update. Check Gram-row synchronization and both B=1 and
packed update paths. |
| `tests/gdn/test_replayssm_spec_fold.py` | Adds an independent FP64
recurrence oracle and lifecycle tests for T=3..8, including every
accepted length, repeated rounds, tracking, padding, strides,
aligned/unaligned views and rejected-tail NaNs. Separate tests assert
the dispatch boundary. | Use `_reference` to check the mathematical
contract, then `test_replayssm_verify_commit_cycles` for state
ownership/lifetime. Routing tests deliberately check selection
separately from numerical correctness. |
| `tests/gdn/test_cute_dsl_kernel_cache.py` | Adds `cache_replayssm` to
the MTP cache-name baseline and parameter-variation test. | Verify
normal MTP and ReplaySSM cannot reuse a compiled artifact with a
different signature. |
| `flashinfer/trace/templates/gdn.py` | Extends the MTP schema/reference
with raw-window outputs and adds a commit schema, initializer and
sequential reference. Aligns the MTP reference with normalization,
frozen-state behavior and batch-indexed snapshots. | In-place
cache/checkpoint outputs must be represented in traces; reference state
updates and accepted-prefix behavior should match the public API. |
| `tests/trace/test_fi_trace.py` | Adds CPU-side schema checks for
ReplaySSM verify and commit. | These validate trace axes, dtypes and
in-place output shapes; GPU numerical correctness is covered by the GDN
tests above. |
| `tests/trace/example.py` | Adds a commit example guarded by
SM100-family capability. | Unsupported GPUs should skip the example; the
example should use the public API. |
| `tests/trace/fi_trace_out/gdn_mtp_qk4_v8_d128.json` | Regenerates the
MTP trace example with the updated schema/reference. | Treat as
generated output; compare against the template rather than reviewing it
as a separate implementation. |
| `tests/trace/fi_trace_out/gdn_replayssm_commit_k2_v8_d128.json` | Adds
the generated commit trace example. | Check consistency with the new
template and example. |

The main correctness invariants are: verify leaves the external
checkpoint unchanged; commit consumes only accepted tokens; inactive
slots and tracking destinations outside the accepted prefix stay
untouched. The tcgen paths trade FP32 contractions for TF32, so compare
against the documented tolerances rather than bitwise equality.

Validation used SM100 hardware; SM103 and long-horizon TF32 state drift
remain unverified. The performance table measures candidate `8e03d01d`
against upstream `c0392885` on a GPU reported as `NVIDIA Graphics
Device` (SM100, 148 SMs), using PyTorch 2.14 / CUDA 13.4 / CuTe DSL
4.8.0.dev0. Exact commands, source hashes, later dispatch measurements
and final-test logs are retained in the external `sm100-gdn-validation/`
evidence bundle; attach it when publishing. The Tes

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added ReplaySSM speculative verification and accepted-prefix commit
support for gated delta-rule decoding on SM100/SM103 GPUs.
- Added optional caching of ReplaySSM intermediate values during MTP
verification.
- Added trace support and examples for ReplaySSM verification and commit
workflows.

- **Documentation**
- Documented ReplaySSM verification, commit behavior, backend selection,
supported configurations, and hardware requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [417065d](https://github.com/flashinfer-ai/flashinfer/commit/417065d70b91a4ebeb3e3c74949a098bc835ae0c)

- **作者**: Anerudhan Gopal
- **时间**: 2026-10-06T17:26:37Z
- **提交信息**: perf: reduce KDA prefill output-overlap validation overhead (#6073)

<!-- .github/pull_request_template.md -->

## 📌 Description

KDA prefill output-alias validation recomputes the output byte range for
every input and walks dimensions even for contiguous tensors. Compute
the output range once per call, use `nbytes` for contiguous ranges,
share the interval predicate, and skip alias checks when the output was
freshly allocated internally. Caller-provided outputs retain the
conservative strided-range check. Buffer pointers and metadata are still
observed on every invocation; there is no cross-call cache.

At the originally measured patch `5ec9190`, on GB200/GB300, the
six-input overlap helper drops from approximately 15.8 µs to 4.3 µs of
active CPU time. A paired vLLM adapter experiment over nine shapes per
GPU measures mean active CPU reductions of 7.89%/8.03% and
completed-call reductions of 5.87%/6.01%. These are adapter
microbenchmarks, not model-serving speedups.

Original `cab5c617` → `5ec9190` results for 8,192 tokens, one sequence,
128-dimensional heads, BF16 inputs/state (µs, lower is better):

| GPU | Heads | Helper CPU before → after | Adapter CPU before → after |
Completed adapter before → after | Profiled GPU kernel sum before →
after |
|---|---:|---:|---:|---:|---:|
| GB200 | 6 | 15.72 → 4.30 | 216.90 → 200.61 | 392.38 → 376.06 | 199.12
→ 199.16 |
| GB200 | 12 | 15.77 → 4.32 | 220.42 → 204.88 | 407.55 → 391.94 | 212.65
→ 213.17 |
| GB200 | 16 | 15.79 → 4.29 | 218.91 → 201.55 | 414.14 → 397.90 | 220.37
→ 220.74 |
| GB300 | 6 | 15.82 → 4.32 | 222.64 → 206.11 | 397.07 → 381.04 | 197.76
→ 198.66 |
| GB300 | 12 | 15.78 → 4.33 | 222.99 → 206.96 | 409.35 → 392.80 | 209.60
→ 210.16 |
| GB300 | 16 | 15.81 → 4.36 | 222.82 → 206.48 | 414.19 → 398.34 | 216.41
→ 216.95 |

No device-kernel change is intended or measured. The GPU column is a
separate three-call CUPTI profile; kernel names match. It is not added
to host time. Completed adapter time includes a final device
synchronization.

Base: `cab5c6172454484701dfda0e6fa4fd639909b0b4`; patch:
`5ec9190fad9a24215ec13c20786c22804201406d`. Runtime: ARM64 Grace hosts,
Torch 2.13.0+cu132, CUDA 13.2. Adapter: [`flashinfer_kda_prefill` at
vLLM
b163158](https://github.com/Anerudhan/vllm/blob/b163158f82b7503f12b3000ded0d49a9f574ac8f/vllm/model_executor/layers/mamba/ops/flashinfer_kda.py),
backend `auto`, safe gate −5, strided beta. H6/H12/H16 × (T1024/N1,
T8192/N1, T8192/N8). Only the changed Python validation functions were
swapped between exact base and patch sources in one process, keeping
compiled kernels and caches fixed. Six alternating ABBA/BAAB rounds × 50
samples per block = 600 samples per variant per shape; table values are
pooled medians. Correctness uses reset input/state and requires bitwise
equality of output and final state.

<details>
<summary>Reproduce the host helper measurement</summary>

Save as `/tmp/bench_kda_overlap.py`, then run it with the base and
patched FlashInfer installations. The helper launches no GPU work;
`thread_time_ns` measures active host CPU time. Both installations
should use the same Python/Torch/CUDA environment and GPU.

```python
import statistics
import time
import torch
from flashinfer.kda_prefill import _check_output_does_not_overlap_inputs

for heads in (6, 12, 16):
    tensors = [torch.empty(1, 8192, heads, 128, device="cuda",
                           dtype=torch.bfloat16) for _ in range(5)]
    q, k, v, g, out = tensors
    carrier = torch.empty(8192, heads + 8, device="cuda", dtype=torch.bfloat16)
    beta = carrier[:, :heads].unsqueeze(0)
    state = torch.empty(1, heads, 128, 128, device="cuda", dtype=torch.bfloat16)
    def call():
        _check_output_does_not_overlap_inputs(
            out, q=q, k=k, v=v, g=g, beta=beta, initial_state=state)
    for _ in range(100):
        call()
    samples = []
    for _ in range(20):
        start = time.thread_time_ns()
        for _ in range(100):
            call()
        samples.append((time.thread_time_ns() - start) / 100_000)
    print(torch.cuda.get_device_name(), heads, statistics.median(samples), "CPU us")
```

```sh
python /tmp/bench_kda_overlap.py
pytest -q tests/kda/test_recurrent_kda_prefill.py \
  -k 'output_overlap or frozen_route_passes_nondefault_stream'
```
</details>

## Revised FlashInfer helper: absolute CPU time

At `44411d30`, caller-provided outputs retain per-call overlap
validation; internally allocated outputs skip it. **This table measures
only the helper, including Python dispatch—not allocation, adapter
execution, GPU kernels or serving.** Times are active CPU µs per call;
lower is better.

| GPU | Heads | Caller output: base → previous → revised | Internal
output: previous → revised |
|---|---:|---:|---:|
| GB200 | 6 | 15.577 → 4.307 → 4.036 | 4.287 → 0.235 |
| GB200 | 12 | 15.359 → 4.220 → 3.944 | 4.292 → 0.232 |
| GB200 | 16 | 15.414 → 4.276 → 4.004 | 4.252 → 0.232 |
| GB300 | 6 | 15.676 → 4.362 → 4.082 | 4.331 → 0.235 |
| GB300 | 12 | 15.571 → 4.234 → 3.985 | 4.242 → 0.233 |
| GB300 | 16 | 15.502 → 4.251 → 3.988 | 4.214 → 0.233 |

Exact helpers from `cab5c617` / `5ec9190` / `44411d30` ran in one
process on each GPU host. T8192/N1/D128, BF16, strided beta; four
alternating ABC-CBA/CBA-ABC rounds, 160 samples per revision/case and
100 calls per sample. Every case first rejected a real output alias.
Buffer allocation and GPU operations stayed outside timing.

Full KDA-prefill tests at `44411d30`: GB200 **308 passed, 1 skipped**;
GB300 **309 passed**. Initial cold-JIT timeouts remain archived; the
same-source retries completed successfully. This validates the revised
heads without upgrading earlier adapter measurements to those heads.

## 🔍 Related Issues

None.

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

At `5ec9190`, 26 focused tests passed on each of GB200 and GB300,
including contiguous, transposed, gapped and expanded views; adjacent
disjoint slices; partial byte aliases; rebound buffers; empty tensors;
and the existing nondefault-stream test. All 18 shape/GPU numerical
comparisons passed exact output/state equality. The full repository
suite was not run.

Review revision `44411d30` passes the full KDA-prefill test file: GB200
308 passed/1 skipped; GB300 309 passed. The revised helper measurements
above followed those gates. Changed-file pre-commit checks and 24 CPU
storage probes pass; a forced contiguous-span mutant fails 12 probes.
New-head adapter and model-serving timings have not been measured.
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

Touched-file pre-commit hooks passed (including mypy and Ruff). The
`--all-files` and full-suite boxes remain unchecked because those
commands were not run.

The strided check intentionally preserves conservative address bounds,
including holes. Caller-provided output validation, public APIs and
backend selection are preserved; storage pointers are not cached. The
measured gain does not close the full host-overhead gap with FlashKDA;
workspace/metadata setup and adapter copies remain.

### [ea8135c](https://github.com/flashinfer-ai/flashinfer/commit/ea8135c0bdf641f54214e9ae777d5b75b5133079)

- **作者**: eigen
- **时间**: 2026-10-06T10:04:38Z
- **提交信息**: feat(cake_kimi_k3_fp8_projection): mid-M dispatch buckets, per-weight cached launcher, SM103 152-SM plan (round 7) (#6096)

## Summary

Round 7 of the Cake `kimi_k3_fp8_projection` generated-program export (FP8 block-scaled projection GEMMs of the Kimi-K3 MLA / fused-QKV / in-proj families, SM100 + SM103):

- **Mid-M dispatch buckets 512 / 1024 / 2048**: the measured table now covers every production cell up to M = 2048 explicitly (decode route = swap-AB split-K for the K = 7168 narrow-N rows, measured 20-112 % faster than the plain GEMM there; GEMM lever cells elsewhere; untabulated buckets fall back to the plain GEMM). Shared table + per-architecture overrides (`decode_table(arch)`).
- **Per-weight cached launcher** (`kimi_k3_fp8_projection_launcher`): route plan and argument templates resolved once per (M, row stride, output address class), per-M workspace LRU, a call binds only `x` / `out`. Host cost at M = 1024 drops from 87-117 us to 26-33 us per call on GB300 (67-86 to 15-19 us on B200). Bit-exact with the prepare path; CUDA-graph capturable; a workspace used inside a capture is pinned (also when it was resolved eagerly before the capture).
- **Stream-K slot forms** (`_skf4` / `_skf8`) and the SM103 plan at the measured 152 SMs (every SM-count-dependent production rule matches the device).
- Regenerated kernel / binding sources, `cake_jit.py` registry (union of the per-architecture key maps), target test module updated to the round-7 rules.

## Validation

- Sealed export receipts (paired same-GPU source-vs-export CUPTI timing, cold L2, 3 counterbalanced groups, bitwise parity + zero-budget correctness on every row): SM103 352/352 rows sealed (source/export geomean 0.994); SM100 342/352 rows sealed, the 10 remaining rows were refused by the harness's environment-validity gates only (order-dependent sampling on two-kernel rows, within-window level switches), never by correctness; all 704 rows passed correctness and bitwise parity.
- `tests/experimental/test_cake_kimi_k3_fp8_projection.py` against this package: 51 passed on B200, 50/51 on GB300 before the last test-rule fix in this PR.
- Paired no-regression check vs the previous kernel of record on both GPUs: 132 rows each, geomean 0.9996 (GB300) / 1.0001 (B200).
- Follow-up commit: typing-only fix for the pre-commit mypy failure (`_WorkspaceState.bindings` is keyed by the plan's tuple of kernel keys). The sealed receipts above attest the previous render of `cake_backend.py`; the shipped file differs from it by that one annotation only.
- Merge note: after this branch was cut, the Cake generator changed how a bf16 pair is unpacked in the vector-load path (inline PTX `shl`/`and` → plain C++ bit casts; identical bits, no scheduling barrier). Re-exporting from the current generator therefore renders the activation-quant program and four fused decode variants with different source hashes. The package in this PR is the render the sealed receipts attest; a paired same-GPU A/B of the two renders on 132 production rows (GB300, 3 alternating rounds, per-kernel isolation on the only row below 0.98) is performance-neutral (geomean 1.0008, isolated worst case 0.5 %), so the shipped package was kept rather than re-measured.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

### [e835a97](https://github.com/flashinfer-ai/flashinfer/commit/e835a9742ce4c999b211211cd9c70c75d32b2df2)

- **作者**: eigen
- **时间**: 2026-10-06T09:43:25Z
- **提交信息**: perf(cake_sampling): round 10 -- CTA-local select twins, integer-tested whole-CTA tail, R200 one-wave re-pick (SM90, SM100a, SM103a, SM107a) (#6105)

## cake_sampling round 10 -- exact levers to the hardware floor

Follow-up of #5439, #5553, #5664, #5771, #5873, #5950, #6065 (rounds
3-9). Round 10 keeps the correctness contract
unchanged (exact top-k set and tie rule, eps-exact top-p cut,
deterministic sampling per (input, seed, offset), fp32 keys,
no reduced-precision paths, no approximate algorithms) and ships three
exact levers plus the measured hard-floor model:

- **L1 CTA-local bucket select** (`_cs_lp_l1` / `_sp_lp_l1` twins,
launch flag bit 10): each CTA picks its filter bucket
from its own sample, so the coarse-histogram DSM round and its barrier
disappear and the leader push is the only cluster
round. Served per compute capability (`top_k_max` <= 10 on 9.0, 20 on
10.0, 32 on 10.3; off on 10.7 / 12.x) and, on
10.0 / 10.3, reaching the two-chunk ept-32 rows the round-9 chunk rule
excluded.
- **L3-T integer tail tests** (`_bt_tia`, launch flag bit 11): the
stage-2/3 integer tests inside the fused whole-CTA tail
on 10.3, where the FP64 rate is reduced (0.92-0.96 of the FP64 tail on
the served k = 1000 route).
- **L6 one-wave re-pick on the 212-SM table** (R200): a small-k one-wave
ept-32 stream pick becomes the cluster-8 ept-16
stream when both grids fit one wave (8-15 % faster at batch <= 16;
multi-wave grids, large k and the other tables keep
  the ranked pick). Host-only; no kernel change.

Bundle: 126 kernels (106 round-9 + 20 new), the 106 round-9 kernels
byte-identical (`.text`) on sm_90a / sm_100a /
sm_103a / sm_107a. `cake_sampling` tests green on B200, GB300, H100,
R200 (261 passed / 18 skipped each); compute-sanitizer
synccheck + memcheck 0 errors on the new kernels (B200, R200); sglang
GSM8K parity on B200.

### Speedup vs `top_k_first` (192-cell matrix per device: k 10 / 50 /
1000 x eager / graph x 8 batches x 4 vocabularies; min / median / max
over the 32 cells of each row)

| device | k | mode | speedup | cells |
|---|---|---|---|---|
| gb300 | 10 | eager | 4.74x / 11.04x / 18.74x | 32 |
| gb300 | 10 | graph | 3.84x / 5.66x / 7.81x | 32 |
| gb300 | 50 | eager | 4.78x / 10.78x / 16.89x | 32 |
| gb300 | 50 | graph | 3.87x / 5.76x / 7.38x | 32 |
| b200 | 10 | eager | 3.07x / 6.64x / 10.36x | 32 |
| b200 | 10 | graph | 3.62x / 5.82x / 8.67x | 32 |
| b200 | 50 | eager | 3.11x / 6.65x / 9.54x | 32 |
| b200 | 50 | graph | 3.74x / 5.91x / 7.81x | 32 |
| b200 | 1000 | eager | 2.93x / 4.54x / 7.89x | 32 |
| b200 | 1000 | graph | 2.96x / 5.22x / 8.17x | 32 |
| h100 | 10 | eager | 2.43x / 6.26x / 11.25x | 32 |
| h100 | 10 | graph | 2.71x / 5.22x / 8.50x | 32 |
| h100 | 50 | eager | 2.49x / 5.91x / 10.65x | 32 |
| h100 | 50 | graph | 2.70x / 5.23x / 7.79x | 32 |
| h100 | 1000 | eager | 2.49x / 4.36x / 6.66x | 32 |
| h100 | 1000 | graph | 2.75x / 4.98x / 7.84x | 32 |
| r200 | 10 | eager | 3.19x / 5.11x / 7.07x | 32 |
| r200 | 10 | graph | 3.29x / 5.34x / 7.04x | 32 |
| r200 | 50 | eager | 3.25x / 5.12x / 7.03x | 32 |
| r200 | 50 | graph | 3.67x / 5.40x / 7.07x | 32 |
| r200 | 1000 | eager | 2.40x / 4.40x / 7.66x | 32 |
| r200 | 1000 | graph | 2.71x / 4.90x / 7.91x | 32 |
| gb300 | 1000 | eager | 3.51x / 5.32x / 7.82x | 32 |
| gb300 | 1000 | graph | 2.83x / 5.23x / 9.02x | 32 |

Every one of the 192 cells is faster than `top_k_first` on every device.
Regressions vs round 9 by the perturbed-process
protocol: GB300 0, R200 0, B200 0, H100 1 (V262144 batch 2 k 10 eager:
+0.1-0.2 us on a route L1 now serves;
the lever is 1.3-5.5 % faster on every other 9.0 cell it serves).

RTX PRO 6000 (sm_120, real hardware): 253 passed / 26 skipped. Design
doc (Cake MR !1251, internal): hard-floor tables per class and device,
roofline, evidence manifest, convergence statement.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved top-k sampling launch selection for eligible workloads,
including small top-k batches and certain two-chunk rows.
* Added support for additional sampling variants on compatible hardware,
including compute capability 10.3.
* **Documentation**
* Expanded guidance on build-selection options, supported launch
configurations, and selection behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f8d3729](https://github.com/flashinfer-ai/flashinfer/commit/f8d3729e9c85d20afdf4a1e672771cdb157e0e33)

- **作者**: eigen
- **时间**: 2026-10-06T09:26:18Z
- **提交信息**: perf(cake_fused_moe): pre-shuffled scale-factor route with a register-only writer kernel for the 8192- and 16384-token Kimi-K3 NVFP4 SiTU rows (SM100/SM103) (#5942)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Routes the 8192- and 16384-token shapes of the Cake Kimi-K3 NVFP4 SiTU
experts (`cutlass_fused_moe(..., activation_type=ActivationType.Situ,
tp_size=8, backend="cake")`) on SM100 (B200) and SM103 (B300) through a
nine-stage sequence that pre-shuffles the FC1 block-scale factors with a
register-only writer kernel. Shipped for both architectures.

- **Pre-shuffled scale-factor route.** The tile-N128 FC1 program of
these shapes consumes K in steps of 512 elements and, per (N-tile,
K-step), needs a 4096-byte image of routed scale factors (128 rows x 32
bytes, one byte per 16-element group) in a fixed shared-memory layout.
The previous route gathered and shuffled that image inside FC1 with 32 x
`cp.async.4` per load thread. The new route writes every image once into
the `sfb_shuffled` workspace field (one 4096-byte image per real routed
tile and K-step, padded rows zero) and the FC1 program of this route
loads each image with a single TMA copy; the routed B loads of that
program use the `.cg` cache operator. MMA operands, layouts, epilogue
and outputs are unchanged.
- **Writer kernel (`kimi_k3_nvfp4_situ_sfb_shuffle_n128_r4p_nc`).** One
warp per tile (grid `(max_tiles, 1, 1)`, 32 threads, no shared memory,
no CTA barrier). Lane q owns rows q, q+32, q+64 and q+96 of the tile:
the four 32-byte scale rows it gathers per K-step (eight 16-byte loads
through the read-only cache path; padded rows stay zero) are already the
eight 16-byte output words of the image, stored directly from registers
so that every warp store covers four full 128-byte lines. The gathers of
the next K-step are issued before the stores of the current one (two
register buffers). Every byte written is a copy of a byte read, so the
images are bitwise the image the FC1 program built itself; the whole
call stays bitwise identical to the previous route on every row and
round.

The `(arch, large_c7)` routes point at a new prepared launch sequence
per architecture (routing kernels, quantization, scale-factor writer,
FC1, FC2, finalize; the routing, quantization, FC2 and finalize programs
are the existing records). Ten generated translation units are added
under `csrc/fused_moe/cake_kimi_k3_situ/{sm_100a,sm_103a}` (writer
kernel + binding, FC1 kernel + binding and the sequence binding per
architecture); the six sources of the superseded tile-N128 FC1 program
and sequence, which no shape selects any more, are removed (150 -> 154
translation units). `flashinfer/jit/cake_kimi_k3_situ.py` gains three
program records per architecture, drops the two superseded ones per
architecture, adds the two routes and removes the two `(arch, 128)`
routes, and carries a static per-program facts table (`PROGRAM_FLAGS`:
the selectors bound to each program, its stage names, route flags and
exported token counts) next to the selector function the runtime now
shares with the sequence lookup.
`flashinfer/fused_moe/cake_kimi_k3_situ.py` adds the `sfb_shuffled`
workspace field and the `sfb_shuffle` launch stage for both token
counts, extends the workspace size query to the pre-shuffled layouts at
or below `max_num_tokens` (a buffer sized for 8193 to 8647 tokens grows
to the 8192-token layout, 1,880,977,664 bytes), and checks every
prepared selection against the static facts and a device-free static
selection (`_route_flags`). The public API, every other program record
and generated source, and the tutorial are unchanged. Generated CUDA
sources are emitted verbatim by the exporter and are not hand-formatted,
as in the previous revisions.

**Behaviour outside the measured shapes.** The `(arch, 128)` routes stay
registered and keep serving every token count from 1025 to 16384 that no
other route covers (all counts except 2048, 4096, 8192 and 16384),
exactly as before this change; the pre-shuffled route is bound only to
the 8192- and 16384-token shapes, and the shipped shapes are the
exported token counts 1, 8, 16, 32, 64, 128, 256, 512, 1024, 2048, 4096,
8192 and 16384 per architecture. The workspace size query covers the
pre-shuffled layouts at or below `max_num_tokens`, so it grows by about
55 MB for `max_num_tokens` between 8193 and 8647 (the first 16384-token
layout becomes reachable there).

## Baseline / source PRs

- #5183 (the Cake Kimi-K3 NVFP4 SiTU experts; merged as 88c241d4) -- the
routes, programs and runtime this change extends; its merged 8192- and
16384-token route (the tile-N128 FC1 program that gathers the scale
factors itself) is the "previous export" arm of the 8192-token rows
below.
- #5755 (open; 16384 tokens) ships the same FC1 program with a
128-thread shared-memory writer for the 16384-token shape only; its
measured route is the "previous export" arm of the 16384-token rows
below. This PR supersedes that route (the records #5755 adds are the
ones this change replaces); whichever merges later rebases onto the
other.
- #5736 (open; small token counts) and #5895 (open; 512/1024 tokens)
edit the same registration and runtime modules with disjoint program
records and routes; whichever merges later rebases onto the others.
- FlashInfer comparison baseline for the measurements:
`trtllm_fp4_block_scale_routed_moe` at
`ac7bce13ea0ff76392fd17aa696b096e191d0825`, including input quantization
and finalization for the same complete-call boundary.

## Performance

Eight physical rows: B200 and B300 at M = 8192 and M = 16384 with
uniform and skewed routing, each measured in one isolated step per row
with five arms under the frozen protocol of #5183 (symmetric external
CUDA graphs, CUPTI activity timing with cold L2, three counterbalanced
groups, 100 ms warmup and 1000 ms reportable budget per arm/group,
minimum 1900 MHz SM clock): the current source implementation, this
export, the FlashInfer baseline, the previous export of the row (see
above) and the export before that one. Qualification requires
source/export >= 0.97, directional disagreement <= 2%, sustained
endpoint drift <= 2%, activity parity, allocation-free submission and no
regression against either earlier export. Correctness (every BF16
element at `atol=1.0, rtol=0.1`, exact intermediate arrays, exact
routing tables) runs before and after each measurement; each row
additionally passes compute-sanitizer synccheck, racecheck and memcheck
on the source and the realized export before it is timed, and an
independent CPU audit re-derives every number from the raw samples.

`FlashInfer / Export` compares the FlashInfer baseline with this export
(values above 1 favor the export). `Source / Export` measures retention
of the source implementation's performance. `Previous export / Export`
compares the row's previous export with this one (values above 1 mean
this revision is faster). `Export / roofline` is the export latency over
the row's roofline (max of the memory-traffic floor at peak bandwidth
and the compute floor), with the remaining gap in microseconds.

| Row | Export us | FlashInfer / Export | Source / Export | Previous
export / Export | Export / roofline (gap) |
|---|---:|---:|---:|---:|---:|
| B300 (sm_103a) M8192 uniform | 858.683 | 1.4277x | 0.9998x | 1.0053x |
1.85x (+395.3 us) |
| B300 (sm_103a) M8192 skew | 860.076 | 1.8618x | 1.0000x | 1.0212x |
1.86x (+396.7 us)* |
| B300 (sm_103a) M16384 uniform | 1369.363 | 1.5960x | 1.0007x | 1.0147x
| 2.12x (+723.9 us) |
| B300 (sm_103a) M16384 skew | 1377.075 | 1.4739x | 0.9994x | 1.0118x |
2.13x (+731.6 us)* |
| B200 (sm_100a) M8192 uniform | 931.197 | 1.4472x | 0.9997x | 1.0175x |
2.01x (+467.8 us) |
| B200 (sm_100a) M8192 skew | 901.900 | 1.9217x | 1.0000x | 1.0346x |
1.95x (+438.5 us)* |
| B200 (sm_100a) M16384 uniform | 1507.851 | 1.6003x | 0.9999x | 1.0157x
| 2.34x (+862.4 us) |
| B200 (sm_100a) M16384 skew | 1473.611 | 1.5211x | 0.9990x | 1.0112x |
2.28x (+828.1 us)* |

\* Skewed-routing floors use the uniform expert-occupancy count, so the
floor is an upper bound and the gap a lower bound.

Geomeans over the eight rows: FlashInfer / Export 1.5971x, Previous
export / Export 1.0165x (1.0196x over the 8192-token rows, 1.0133x over
the 16384-token rows); Source / Export between 0.9990x and 1.0007x.
Final outputs and exact intermediates are bitwise identical to the
source and to both earlier exports on every row and every round. Largest
sustained endpoint drift 0.93%, largest directional disagreement 0.25%
(gate 2%).

## Absolute timings (previous route vs this route)

Complete-call medians from the same five-arm step per row (CUPTI
activity timing, cold L2, three counterbalanced groups, same inputs and
workspace). The 8192-token rows compare against the eight-kernel route
without the writer (the FC1 program gathers the scale factors itself);
the 16384-token rows compare against the nine-kernel route with the
previous 128-thread shared-memory writer. Every other stage is the same
program on the same inputs.

| GPU | Tokens | Routing | Previous export | This export | Difference |
|---|---:|---|---:|---:|---:|
| B300 (sm_103a) | 8192 | uniform | 863.2 us (route without the writer)
| 858.7 us | -4.6 us (1.0053x) |
| B300 (sm_103a) | 8192 | skewed | 878.3 us (route without the writer) |
860.1 us | -18.3 us (1.0212x) |
| B300 (sm_103a) | 16384 | uniform | 1389.4 us (previous writer) |
1369.4 us | -20.1 us (1.0147x) |
| B300 (sm_103a) | 16384 | skewed | 1393.3 us (previous writer) | 1377.1
us | -16.3 us (1.0118x) |
| B200 (sm_100a) | 8192 | uniform | 947.5 us (route without the writer)
| 931.2 us | -16.3 us (1.0175x) |
| B200 (sm_100a) | 8192 | skewed | 933.1 us (route without the writer) |
901.9 us | -31.2 us (1.0346x) |
| B200 (sm_100a) | 16384 | uniform | 1531.5 us (previous writer) |
1507.9 us | -23.7 us (1.0157x) |
| B200 (sm_100a) | 16384 | skewed | 1490.1 us (previous writer) | 1473.6
us | -16.5 us (1.0112x) |

## Generated sources

The ten `.cu` files and the six program records are emitted by the Loom
kernel exporter (`python -m loom.export.generated_programs`: `protocol`
freezes the export protocol, `run` generates the sources into a clean
FlashInfer worktree; the Kimi-K3 SiTU operator adapter supplies the
shapes and callbacks). Each record's `closure_sha256` is computed over
the record identity and the SHA-256 of every listed source, and
`cache_name` carries its prefix, so the committed sources are checked
against the records on every export. The generated files are not
hand-edited. The writer kernel's compiled image is identical on both
architectures' measurement runs to the one profiled during development;
the FC1 program's compiled image is identical to the one measured for
#5755.

## Evidence

The measurement receipts (five-arm timer results, independent raw CPU
audits, sanitizer records, prepare realizations) are archived on the
measurement clusters; the accompanying evidence manifest lists every
artifact as host / absolute path / size / SHA-256. No artifacts are
attached to this PR.

## Test plan

- `tests/moe/test_cake_kimi_k3_situ.py` (SM100a / SM103a) via the CI
bots: workspace-size query, prepared-workspace binding, complete-call
correctness against the reference and graph capture/replay; the
complete-call test now also runs the 8192- and 16384-token shapes, and
the writer-image test launches the writer alone on both shapes (uniform
and skewed routing) and compares its images with a Python shuffle,
including the sentinel check of unwritten padding tiles.
- Added GPU-free tests: every route binds a program whose static facts
name that selector and architecture, the static selection resolves every
exported token count to its program, and only the 8192- and 16384-token
rows route to the nine-stage sequence; the workspace size query covers
the pre-shuffled layouts at or below `max_num_tokens` and stays
monotonic; the 8192- and 16384-token layouts append `sfb_shuffled` as
their last field.
- `python -m py_compile` on `flashinfer/jit/cake_kimi_k3_situ.py` and
`flashinfer/fused_moe/cake_kimi_k3_situ.py`; `ruff format --check` and
`ruff check` (0.12.8) on the three Python files.

Related:
[4254](https://github.com/flashinfer-ai/flashinfer/issues/4254).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added large-token routing for Cake SiTU at 8,192 and 16,384 tokens on
supported GPU architectures.
* Added a scale-factor shuffle stage to prepare data for the routed MoE
sequence, with updated workspace sizing and route selection.
* **Bug Fixes**
* Added validation for incompatible route settings, tensor inputs, and
launch parameters, with errors reported when configurations are invalid.
* **Tests**
* Expanded coverage for large-token routes, workspace layouts, output
correctness, and scale-factor shuffle behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e07685c](https://github.com/flashinfer-ai/flashinfer/commit/e07685c59186e60f1e94bcc82f947b7941685504)

- **作者**: eigen
- **时间**: 2026-10-06T09:08:52Z
- **提交信息**: perf(cake_nvfp4_mla_decode): faster than the FP8 CuTe-DSL MLA decode on every shipped shape (SM100a, SM103a) (#6107)

## Summary

Regenerates the `cake_nvfp4_mla_decode` programs (DeepSeek-V4 NVFP4 MLA
decode, D=512 latent + 64 rope, split-KV combine) from the latest Cake
kernel tree. The generated programs are now faster than
`trtllm_batch_decode_with_kv_cache_mla(backend="cute-dsl")` with an FP8
KV cache on every shipped shape, on both SM100a (B200) and SM103a
(GB300), and no row regresses against the programs currently in `main`.

Kernel changes carried by the generated programs:
- **Cost-balanced persistent unit partition** in the host plan: units
equalise `tiles + 2.5 x (pieces - 1)` instead of tiles, because every
extra piece (item boundary) costs the softmax warps an epilogue plus a
pipeline refill. `cake_backend.py` ports the same partition so the host
plan matches the kernel's source of truth; the plan tests assert cost
balance instead of an equal-tiles spread.
- **Decode epilogue**: one staging tile per round and bulk tensor stores
batched two 32-column rounds per 4 KB SW128 tile (4 stores per epilogue
instead of 8).
- **Split-KV combine**: one wave (two heads per warp), every two-split
load issued at kernel entry, scalar two-split LSE; output bit-identical
to the general path.

Precision points are unchanged (NVFP4 QK, E4M3 P x 2^8, on-chip V
requantisation to E4M3, fp32 softmax); test tolerances are unchanged.

## Speedup vs FlashInfer FP8 CuTe-DSL MLA decode

Kernel-only CUPTI GPU span of every launch (decode + combine; FP8
CuTe-DSL likewise), cold L2, FP8 first then the arms interleaved, 3
reps, same GPU and process; bs32 / q6 / H64 / sink / page 64.

| KV length | GB300 (SM103a) | B200 node 1 (SM100a) | B200 node 2
(SM100a) |
|---|---|---|---|
| 8K | **1.081x** | **1.021x** | **1.013x** |
| 16K | **1.148x** | **1.039x** | **1.041x** |
| 32K | **1.183x** | **1.086x** | **1.072x** |
| 64K | **1.235x** | **1.135x** | **1.116x** |
| 128K | **1.268x** | **1.174x** | **1.160x** |

Against the programs currently in `main` (same measurement): 0.975 /
0.978 / 0.992 / 0.997 / 0.999 of their time on GB300 and 0.970-0.972 /
0.977-0.981 / 0.988-0.991 / 0.996-0.998 / 0.997-0.998 on B200.

## Export protocol

Sealed generated-program export, 16/16 rows (8 shapes x 2
architectures), source/export 0.9899-1.0489 with the directional, drift
and SM-clock gates passed on B200 and GB300; two-architecture merge
through a closed read-only prior. Target revision d4b19b87d.

| row | SM100a source / export ms | SM103a source / export ms |
|---|---|---|
| smoke | 0.013280 / 0.013184 | 0.012576 / 0.012704 |
| partial_pages_h8 | 0.024032 / 0.022912 | 0.023008 / 0.022368 |
| no_sink_q1 | 0.040800 / 0.040576 | 0.037184 / 0.037217 |
| bs32_q6_kv8k | 0.114560 / 0.114400 | 0.094016 / 0.094752 |
| bs32_q6_kv16k | 0.206112 / 0.206016 | 0.162977 / 0.162944 |
| bs32_q6_kv32k | 0.383137 / 0.382625 | 0.300705 / 0.300929 |
| bs32_q6_kv64k | 0.733217 / 0.732834 | 0.568385 / 0.568706 |
| bs32_q6_kv128k | 1.441028 / 1.440739 | 1.102626 / 1.103235 |

## Tests

- `tests/experimental/test_cake_nvfp4_mla_decode.py`: 51 passed, 1
skipped on B200 and on GB300.
- `benchmarks/bench_cake_nvfp4_mla_decode.py` (batch 32, q 6, 64 heads;
host path included): B200 0.1089 / 0.1938 / 0.3666 / 0.7347 / 1.5754 ms,
GB300 0.0932 / 0.1641 / 0.2992 / 0.5692 / 1.1310 ms at 8K / 16K / 32K /
64K / 128K.

Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* NVFP4 MLA decode work is balanced by estimated processing cost,
accounting for the overhead of splitting sequences into pieces.
* Updated decode processing and partial-result combination support
workloads with multiple partial outputs.
* Adjusted processing for supported GPU architectures and head groups,
including updated output handling.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d894051](https://github.com/flashinfer-ai/flashinfer/commit/d8940515fa976ab547e107224f3baef64a67327f)

- **作者**: eigen
- **时间**: 2026-10-06T08:27:01Z
- **提交信息**: perf(cake_all_gather_matmul): one native host sequence per route (SM100a, SM103a) (#6099)

## Summary

Cake all-gather matmul (`flashinfer.comm.all_gather_matmul`, Blackwell
SM100 / SM103 TP2/TP4/TP8): the per-call
host work moves from Python orchestration into one native call per
route.

The first delivery issued, per call, three tvm-ffi launches with
per-call tensor-map encodes, six `copy_` /
`stream_write_value32_` operators for the peer pushes, and the torch
stream plumbing around them: ~117 µs of
host issue time (37 to 114 aten ops) per call versus ~31 µs for the
previous launcher. Under a cold-L2 CUPTI
single-call measurement the sub-millisecond SM103 rows (N=1280 TP8,
N=2560 TP4) read 10 to 60 % slower than
with the previous launcher although the kernels were unchanged.

This PR renders one **host sequence** per (dtype, world size, weight
layout, architecture) and compiles it
with the route's device units into one module:

* `run`: barrier(phase), bridge event to the communication stream,
`(world_size - 1) x chunks` of
`cudaMemcpyAsync` + `cuStreamWriteValue32`, main kernel on the caller's
stream, bridge event back.
* `run_fused` (SM103 TP8 bf16 routes): barrier, fused SM copy kernel,
join, second barrier, main kernel.
* Tensor maps are cached on (address, extents, strides); weight and
scratch hit on every call.
* The Python backend keeps validation, epoch/phase bookkeeping and the
cross-stream tail join, and passes
  prebuilt peer address tables from the workspace.

Device code is unchanged: every kernel `.cu` unit is byte-identical to
the previous delivery. The generated
per-program bindings are replaced by the sequence modules.

## Measurements

#### Export gate (Cake direct launcher vs FlashInfer backend, cold-L2
CUPTI rank-max, 3 counterbalanced groups)

sm_103a: 60 rows, all correct and passing the gate, direct/backend
0.9893 to 1.0226, geomean 1.0002.

<details><summary>sm_103a rows (8xB300)</summary>

| ws | N | M | dtype | weight | entry | Cake direct ms | FlashInfer
backend ms | direct / backend |
|---:|---:|---:|---|---|---|---:|---:|---:|
| 2 | 2048 | 1000 | bfloat16 | n_major | one_shot | 0.0662 | 0.0665 |
0.9945 |
| 2 | 2048 | 1024 | bfloat16 | k_major | one_shot | 0.0683 | 0.0687 |
0.9944 |
| 2 | 2048 | 1024 | bfloat16 | n_major | one_shot | 0.0666 | 0.0669 |
0.9943 |
| 2 | 2048 | 1024 | float16 | k_major | one_shot | 0.0690 | 0.0693 |
0.9954 |
| 2 | 2048 | 2048 | bfloat16 | n_major | one_shot | 0.1177 | 0.1178 |
0.9992 |
| 2 | 2048 | 4096 | bfloat16 | n_major | one_shot | 0.2112 | 0.2114 |
0.9989 |
| 2 | 2048 | 8192 | bfloat16 | n_major | one_shot | 0.4419 | 0.4429 |
0.9976 |
| 2 | 2048 | 16384 | bfloat16 | n_major | one_shot | 1.1091 | 1.1088 |
1.0003 |
| 2 | 2048 | 16384 | float16 | n_major | one_shot | 1.1381 | 1.1376 |
1.0004 |
| 2 | 2048 | 19456 | bfloat16 | n_major | one_shot | 1.4335 | 1.4331 |
1.0002 |
| 2 | 2048 | 32768 | bfloat16 | n_major | one_shot | 2.3954 | 2.3944 |
1.0004 |
| 2 | 2048 | 65536 | bfloat16 | n_major | one_shot | 4.9062 | 4.9163 |
0.9980 |
| 4 | 2048 | 1024 | bfloat16 | n_major | one_shot | 0.1210 | 0.1211 |
0.9995 |
| 4 | 2048 | 1025 | float16 | n_major | one_shot | 0.1250 | 0.1250 |
1.0004 |
| 4 | 2048 | 2048 | bfloat16 | n_major | one_shot | 0.2225 | 0.2225 |
1.0001 |
| 4 | 2048 | 4096 | bfloat16 | n_major | one_shot | 0.4206 | 0.4203 |
1.0008 |
| 4 | 2048 | 8192 | bfloat16 | n_major | one_shot | 0.9265 | 0.9269 |
0.9996 |
| 4 | 2048 | 16384 | bfloat16 | n_major | one_shot | 2.3251 | 2.3222 |
1.0013 |
| 4 | 2048 | 16384 | float16 | n_major | one_shot | 2.4083 | 2.4091 |
0.9997 |
| 4 | 2048 | 19456 | bfloat16 | n_major | one_shot | 2.9711 | 2.9715 |
0.9999 |
| 4 | 2048 | 32768 | bfloat16 | n_major | one_shot | 5.1421 | 5.1453 |
0.9994 |
| 4 | 2048 | 65536 | bfloat16 | n_major | one_shot | 10.3450 | 10.3828 |
0.9964 |
| 4 | 2560 | 125 | bfloat16 | k_major | prepared | 0.0741 | 0.0735 |
1.0078 |
| 4 | 2560 | 512 | bfloat16 | k_major | prepared | 0.1887 | 0.1898 |
0.9944 |
| 4 | 2560 | 512 | bfloat16 | n_major | prepared | 0.1843 | 0.1850 |
0.9964 |
| 4 | 2560 | 512 | float16 | k_major | prepared | 0.1852 | 0.1855 |
0.9986 |
| 4 | 2560 | 1024 | bfloat16 | k_major | prepared | 0.2020 | 0.2041 |
0.9893 |
| 4 | 2560 | 1025 | bfloat16 | k_major | prepared | 0.2014 | 0.2033 |
0.9906 |
| 4 | 2560 | 2048 | bfloat16 | k_major | prepared | 0.3886 | 0.3886 |
0.9999 |
| 4 | 2560 | 4096 | bfloat16 | k_major | prepared | 0.6020 | 0.6024 |
0.9993 |
| 4 | 14336 | 125 | bfloat16 | k_major | prepared | 0.1508 | 0.1508 |
0.9998 |
| 4 | 14336 | 512 | bfloat16 | k_major | prepared | 0.4230 | 0.4226 |
1.0011 |
| 4 | 14336 | 1024 | bfloat16 | k_major | prepared | 0.7826 | 0.7832 |
0.9993 |
| 4 | 14336 | 1025 | bfloat16 | k_major | prepared | 0.7805 | 0.7806 |
0.9999 |
| 4 | 14336 | 2048 | bfloat16 | k_major | prepared | 1.4372 | 1.4388 |
0.9989 |
| 4 | 14336 | 4096 | bfloat16 | k_major | prepared | 2.9123 | 2.9105 |
1.0006 |
| 8 | 1280 | 125 | bfloat16 | k_major | prepared | 0.0900 | 0.0887 |
1.0144 |
| 8 | 1280 | 512 | bfloat16 | k_major | prepared | 0.2326 | 0.2313 |
1.0055 |
| 8 | 1280 | 512 | bfloat16 | n_major | prepared | 0.2384 | 0.2383 |
1.0007 |
| 8 | 1280 | 512 | float16 | k_major | prepared | 0.1463 | 0.1455 |
1.0053 |
| 8 | 1280 | 1024 | bfloat16 | k_major | prepared | 0.2035 | 0.2033 |
1.0009 |
| 8 | 1280 | 1025 | bfloat16 | k_major | prepared | 0.2050 | 0.2057 |
0.9969 |
| 8 | 1280 | 2048 | bfloat16 | k_major | prepared | 0.3178 | 0.3128 |
1.0160 |
| 8 | 1280 | 4096 | bfloat16 | k_major | prepared | 0.6199 | 0.6109 |
1.0147 |
| 8 | 2048 | 125 | bfloat16 | n_major | one_shot | 0.0780 | 0.0783 |
0.9955 |
| 8 | 2048 | 1024 | bfloat16 | n_major | one_shot | 0.2415 | 0.2422 |
0.9971 |
| 8 | 2048 | 2048 | bfloat16 | n_major | one_shot | 0.4139 | 0.4047 |
1.0226 |
| 8 | 2048 | 4096 | bfloat16 | n_major | one_shot | 0.8524 | 0.8549 |
0.9971 |
| 8 | 2048 | 8192 | bfloat16 | n_major | one_shot | 1.8058 | 1.8016 |
1.0023 |
| 8 | 2048 | 16384 | bfloat16 | n_major | one_shot | 4.8691 | 4.8668 |
1.0005 |
| 8 | 2048 | 16384 | float16 | n_major | one_shot | 5.0466 | 5.0385 |
1.0016 |
| 8 | 2048 | 19456 | bfloat16 | n_major | one_shot | 6.1800 | 6.1808 |
0.9999 |
| 8 | 2048 | 32768 | bfloat16 | n_major | one_shot | 10.7824 | 10.8387 |
0.9948 |
| 8 | 2048 | 65536 | bfloat16 | n_major | one_shot | 22.0823 | 22.0431 |
1.0018 |
| 8 | 7168 | 125 | bfloat16 | k_major | prepared | 0.1625 | 0.1628 |
0.9982 |
| 8 | 7168 | 512 | bfloat16 | k_major | prepared | 0.4354 | 0.4353 |
1.0003 |
| 8 | 7168 | 1024 | bfloat16 | k_major | prepared | 0.7940 | 0.7938 |
1.0002 |
| 8 | 7168 | 1025 | bfloat16 | k_major | prepared | 0.7968 | 0.7969 |
0.9998 |
| 8 | 7168 | 2048 | bfloat16 | k_major | prepared | 1.5658 | 1.5665 |
0.9995 |
| 8 | 7168 | 4096 | bfloat16 | k_major | prepared | 3.0648 | 3.0701 |
0.9983 |

</details>

sm_100a: 59 rows, all correct and passing the gate, direct/backend
0.9695 to 1.0080, geomean 0.9987.

<details><summary>sm_100a rows (8xB200)</summary>

| ws | N | M | dtype | weight | entry | Cake direct ms | FlashInfer
backend ms | direct / backend |
|---:|---:|---:|---|---|---|---:|---:|---:|
| 2 | 2048 | 1000 | bfloat16 | n_major | one_shot | 0.0662 | 0.0671 |
0.9866 |
| 2 | 2048 | 1024 | bfloat16 | k_major | one_shot | 0.0704 | 0.0701 |
1.0041 |
| 2 | 2048 | 1024 | bfloat16 | n_major | one_shot | 0.0671 | 0.0673 |
0.9976 |
| 2 | 2048 | 1024 | float16 | k_major | one_shot | 0.0705 | 0.0703 |
1.0027 |
| 2 | 2048 | 2048 | bfloat16 | n_major | one_shot | 0.1208 | 0.1209 |
0.9997 |
| 2 | 2048 | 4096 | bfloat16 | n_major | one_shot | 0.2208 | 0.2221 |
0.9942 |
| 2 | 2048 | 8192 | bfloat16 | n_major | one_shot | 0.4742 | 0.4751 |
0.9981 |
| 2 | 2048 | 16384 | bfloat16 | n_major | one_shot | 1.1940 | 1.1927 |
1.0011 |
| 2 | 2048 | 16384 | float16 | n_major | one_shot | 1.2227 | 1.2224 |
1.0002 |
| 2 | 2048 | 19456 | bfloat16 | n_major | one_shot | 1.5403 | 1.5412 |
0.9995 |
| 2 | 2048 | 32768 | bfloat16 | n_major | one_shot | 2.5799 | 2.5809 |
0.9996 |
| 2 | 2048 | 65536 | bfloat16 | n_major | one_shot | 5.3000 | 5.2994 |
1.0001 |
| 4 | 2048 | 1024 | bfloat16 | n_major | one_shot | 0.1229 | 0.1235 |
0.9953 |
| 4 | 2048 | 1025 | float16 | n_major | one_shot | 0.1247 | 0.1249 |
0.9978 |
| 4 | 2048 | 2048 | bfloat16 | n_major | one_shot | 0.2326 | 0.2333 |
0.9971 |
| 4 | 2048 | 4096 | bfloat16 | n_major | one_shot | 0.4529 | 0.4534 |
0.9989 |
| 4 | 2048 | 8192 | bfloat16 | n_major | one_shot | 1.0211 | 1.0219 |
0.9992 |
| 4 | 2048 | 16384 | bfloat16 | n_major | one_shot | 2.5505 | 2.5493 |
1.0005 |
| 4 | 2048 | 16384 | float16 | n_major | one_shot | 2.6542 | 2.6478 |
1.0024 |
| 4 | 2048 | 19456 | bfloat16 | n_major | one_shot | 3.2655 | 3.2645 |
1.0003 |
| 4 | 2048 | 32768 | bfloat16 | n_major | one_shot | 5.6315 | 5.6325 |
0.9998 |
| 4 | 2048 | 65536 | bfloat16 | n_major | one_shot | 11.5813 | 11.5956 |
0.9988 |
| 4 | 2560 | 125 | bfloat16 | k_major | prepared | 0.0740 | 0.0741 |
0.9981 |
| 4 | 2560 | 512 | bfloat16 | k_major | prepared | 0.1943 | 0.1940 |
1.0016 |
| 4 | 2560 | 512 | float16 | k_major | prepared | 0.1957 | 0.1962 |
0.9979 |
| 4 | 2560 | 1024 | bfloat16 | k_major | prepared | 0.2117 | 0.2125 |
0.9962 |
| 4 | 2560 | 1025 | bfloat16 | k_major | prepared | 0.2117 | 0.2122 |
0.9977 |
| 4 | 2560 | 2048 | bfloat16 | k_major | prepared | 0.4043 | 0.4044 |
0.9996 |
| 4 | 2560 | 4096 | bfloat16 | k_major | prepared | 0.6515 | 0.6516 |
0.9997 |
| 4 | 14336 | 125 | bfloat16 | k_major | prepared | 0.1524 | 0.1531 |
0.9956 |
| 4 | 14336 | 512 | bfloat16 | k_major | prepared | 0.4457 | 0.4457 |
0.9999 |
| 4 | 14336 | 1024 | bfloat16 | k_major | prepared | 0.8547 | 0.8551 |
0.9995 |
| 4 | 14336 | 1025 | bfloat16 | k_major | prepared | 0.8600 | 0.8613 |
0.9985 |
| 4 | 14336 | 2048 | bfloat16 | k_major | prepared | 1.5612 | 1.5647 |
0.9977 |
| 4 | 14336 | 4096 | bfloat16 | k_major | prepared | 3.0942 | 3.0972 |
0.9990 |
| 8 | 1280 | 125 | bfloat16 | k_major | prepared | 0.0809 | 0.0807 |
1.0024 |
| 8 | 1280 | 512 | bfloat16 | k_major | prepared | 0.1371 | 0.1367 |
1.0026 |
| 8 | 1280 | 512 | bfloat16 | n_major | prepared | 0.1438 | 0.1435 |
1.0025 |
| 8 | 1280 | 512 | float16 | k_major | prepared | 0.1459 | 0.1448 |
1.0080 |
| 8 | 1280 | 1024 | bfloat16 | k_major | prepared | 0.2056 | 0.2060 |
0.9977 |
| 8 | 1280 | 1025 | bfloat16 | k_major | prepared | 0.2060 | 0.2063 |
0.9988 |
| 8 | 1280 | 2048 | bfloat16 | k_major | prepared | 0.3285 | 0.3281 |
1.0012 |
| 8 | 1280 | 4096 | bfloat16 | k_major | prepared | 0.6536 | 0.6578 |
0.9937 |
| 8 | 2048 | 125 | bfloat16 | n_major | one_shot | 0.0834 | 0.0860 |
0.9695 |
| 8 | 2048 | 1024 | bfloat16 | n_major | one_shot | 0.2532 | 0.2521 |
1.0044 |
| 8 | 2048 | 2048 | bfloat16 | n_major | one_shot | 0.4271 | 0.4322 |
0.9881 |
| 8 | 2048 | 4096 | bfloat16 | n_major | one_shot | 0.9158 | 0.9193 |
0.9962 |
| 8 | 2048 | 8192 | bfloat16 | n_major | one_shot | 1.9753 | 1.9791 |
0.9981 |
| 8 | 2048 | 16384 | bfloat16 | n_major | one_shot | 5.4196 | 5.4152 |
1.0008 |
| 8 | 2048 | 16384 | float16 | n_major | one_shot | 5.5943 | 5.5893 |
1.0009 |
| 8 | 2048 | 19456 | bfloat16 | n_major | one_shot | 6.8941 | 6.8884 |
1.0008 |
| 8 | 2048 | 32768 | bfloat16 | n_major | one_shot | 11.9580 | 11.9742 |
0.9986 |
| 8 | 2048 | 65536 | bfloat16 | n_major | one_shot | 24.7563 | 24.6327 |
1.0050 |
| 8 | 7168 | 125 | bfloat16 | k_major | prepared | 0.1450 | 0.1446 |
1.0027 |
| 8 | 7168 | 512 | bfloat16 | k_major | prepared | 0.4532 | 0.4528 |
1.0008 |
| 8 | 7168 | 1024 | bfloat16 | k_major | prepared | 0.8519 | 0.8523 |
0.9994 |
| 8 | 7168 | 1025 | bfloat16 | k_major | prepared | 0.8640 | 0.8633 |
1.0009 |
| 8 | 7168 | 2048 | bfloat16 | k_major | prepared | 1.7123 | 1.7133 |
0.9994 |
| 8 | 7168 | 4096 | bfloat16 | k_major | prepared | 3.2312 | 3.2327 |
0.9995 |

</details>

#### Previous launcher (FlashInfer 0.7.0.post1) vs this delivery,
8xB300, cold-L2 CUPTI single-call spans, prepared launcher, matched
arms, pooled over passes

TP4, N=2560, bf16 (main kernel enqueued before the pushes) (3 new + 3
old passes):

| M | N | samples/arm | new median ms | new q25 | new min | old median
ms | old q25 | old min | old/new median | old/new q25 | old/new min |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 128 | 2560 | 54 | 0.1943 | 0.1600 | 0.1180 | 0.4143 | 0.2865 | 0.2276
| 2.133 | 1.791 | 1.929 |
| 512 | 2560 | 54 | 0.2902 | 0.2371 | 0.2076 | 0.3946 | 0.2806 | 0.2308
| 1.360 | 1.183 | 1.112 |
| 1024 | 2560 | 54 | 0.3050 | 0.2479 | 0.2115 | 0.3428 | 0.2906 | 0.2183
| 1.124 | 1.172 | 1.032 |
| 2048 | 2560 | 54 | 0.5105 | 0.4679 | 0.4333 | 0.5255 | 0.4632 | 0.4158
| 1.029 | 0.990 | 0.960 |
| 4096 | 2560 | 54 | 0.7706 | 0.6612 | 0.6160 | 0.7406 | 0.6509 | 0.6179
| 0.961 | 0.984 | 1.003 |

TP8, N=1280, bf16 (pushes first) (5 new + 5 old passes):

| M | N | samples/arm | new median ms | new q25 | new min | old median
ms | old q25 | old min | old/new median | old/new q25 | old/new min |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 128 | 1280 | 90 | 0.5784 | 0.4133 | 0.2205 | 0.7566 | 0.6086 | 0.4496
| 1.308 | 1.473 | 2.039 |
| 512 | 1280 | 90 | 0.6142 | 0.4685 | 0.2794 | 0.7724 | 0.6314 | 0.4679
| 1.258 | 1.348 | 1.675 |
| 1024 | 1280 | 90 | 0.7013 | 0.5626 | 0.3686 | 0.8051 | 0.7062 | 0.4857
| 1.148 | 1.255 | 1.318 |
| 2048 | 1280 | 90 | 0.9124 | 0.7589 | 0.5678 | 0.9066 | 0.7736 | 0.6089
| 0.994 | 1.019 | 1.072 |
| 4096 | 1280 | 90 | 1.3065 | 1.1749 | 0.9590 | 1.3487 | 1.2202 | 1.0255
| 1.032 | 1.039 | 1.069 |

TP4 4096x2560 reads 0.96 at the median with a higher slow-mode share in
the new arm (35 % vs 26 %), q25 0.98 and an
equal fast mode (min 1.00); every other row is at or above 0.98 on
median, q25 and min. Samples are bimodal on both
arms (rank skew absorbed by the barrier), so q25 and min are the stable
statistics. The export gate was re-measured on
the final commit; the comparison against the previous launcher was
measured before the review follow-ups, which add
host-side checks and a module name only.

Host issue time per call (cProfile, 200 calls, 8xB300): TP4 512x2560 24
us (previous launcher 30 us, first delivery
117 us); TP8 2048x1280 300 us (previous launcher 323 us).


## Tests

* `tests/comm/test_all_gather_matmul_cake*.py`: 148 CPU tests passed on
8xB200 and 8xB300; the multi-GPU e2e test (2 cases) passed on both.
* `pre-commit` clean (generated `csrc/cake_all_gather_matmul/` excluded
as before).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7a14082](https://github.com/flashinfer-ai/flashinfer/commit/7a1408216cf6141f5f6b586ba9dc805e119c8768)

- **作者**: eigen
- **时间**: 2026-10-06T08:10:48Z
- **提交信息**: feat(cake_dsv4_sparse_mla): variant-indexed generated family for the SM120 DSv4.1 mixed-cache sparse-MLA decode (#6071)

## Summary

Regenerated SM120 / SM121 DeepSeek-V4.1 mixed-cache sparse-MLA decode
family (`csrc/cake_dsv4/sm_120a/cake_sparse_mla_dsv41_mixed_*`) from the
Cake R2 round (kernel module commit `cf9aa7cac36` (device code unchanged
since `8affb681437`; the last module change only sets the pre-13.2
toolchain fallback form), dispatch tables v9.13, export identity
`7c7caa2c3571` (exporter tree `c854788fb8d`)), plus the host-side
exact-variant dispatch mirror in
`flashinfer/mla/_sparse_mla_sm120/cake_dsv41_mixed.py`. The last commit
(Zihao Ye) is the export-review follow-up: the split-merge bodies folded
into two template units, an index-based binding ABI, a trimmed manifest
and a host that validates and plans once per call; the decode device
code is byte-identical to the previous export (`d12d3804aa0e`).

Follow-up to #5983 (R1 family, one decode body per head count). R2 adds
trace-time exact variants of the same kernel (`sa` SMEM address slot
table, `pw` pow2 page resolve, `lq` decoupled prologue, `ip` hoisted
index-table fill, `el` evict-last partials, `tl` runtime stage loop,
`t1` one 16-head tile per CTA, `e2m1_nomul` single-instruction E2M1
convert, `ew` / `ra` IO arrival / resolve-ahead, `mo2` merge load hoist,
`e2f` pre-13.2 2^112 fold) and a per-card dispatch (170-SM RTX 5090,
188-SM RTX PRO 6000 Blackwell SE, 48-SM GB10) over cache layout x head
count x token bucket x ragged x toolchain, carried in the manifest and
evaluated by the host
(`cake_sparse_mla_sm120_dsv41_mixed_plan_variant`). Numerics are
unchanged (BF16 Q, exact dequant, BF16 QK MMA, fp32 softmax / accumulate
/ merge, BF16 output); the `t1` bodies re-associate the fp32
accumulation across head tiles only.

Paired against the R1 family on the same cards (Cake `bench_gpu_time`,
CUPTI, cold L2): geomean decode time 0.909x (RTX PRO 6000), 0.908x (RTX
5090) and 0.954x (GB10) of the R1 family over the 44 measured rows, no
row slower beyond its A/A band; see the Cake design notes for the
per-row tables.

## Contents

- `csrc/cake_dsv4/sm_120a/`: 47 kernel translation units for 97 decode
bodies + 14 merge bodies. Exact twins of one decode body (its
power-of-two-page twin, its `e2m1_nomul` twin, head counts of one
structural class) share a folded unit: one `template <int kHeads, bool
kPow2Pages, bool kNoMul>` `__global__` kernel per fold grid (31 units,
83 bodies) with one explicit instantiation per body; the other 14 decode
bodies are single units; the split-merge bodies of one merge variant
differ only in the head count and are two `template <int kHeads>` units
(`default`: 9 head counts, `mo2`: 5). Every body keeps its own
`h<N>::decode[_dual]_<variant>::launch()` /
`h<N>::merge_<variant>::launch()` namespace. Every instantiation was
proven SASS-identical (`nvcc -cubin -arch=sm_120a` + `cuobjdump -sass`,
addresses/encodings/symbols masked) to the body's standalone render
before the unit was written: 33/33 fold groups, 97/97 kernels on CUDA
13.3; the 31 decode groups (83 kernels) were also re-proven with the
CUDA 13.0 and 12.9 compilers of the gate images on the previous export,
whose decode device text this one repeats.
- Binding `cake_sparse_mla_dsv41_mixed_binding.cu` (296 lines): a
launcher. The host passes the decode and merge body as indices into the
manifest's `decode_kernels` / `merge_kernels`, `chunks_per_block` and
the grid order (`hb_major`); the binding checks that both bodies serve
the call's head count and cache layout, derives the split count, and
launches. No variant / precision scalars or tables, no per-call
device-attribute query, no mutex or cache; each decode body opts into
its dynamic shared memory once through a function-local static.
- Host: `CakeDsv41MixedDispatch` / `dispatch_from_manifest()` /
`plan_variant` mirror (v8 full-grid split refit, v9 quarter-to-half-SM
rules, ragged hint, `pw` stripped on non-power-of-two pages, pre-13.2
toolchain fallback form on the two-tile dual renders of every card incl.
GB10); `variant=` pins a label. One validation and plan per call
(`wrapper_run` / `functional_run` no longer plan twice), device facts
(SM count, GB10, opt-in shared memory, CC 12.x) cached per device, body
indices taken from the manifest, `compute_precision="fp8"` rejected when
the wrapper is built (no FP8 route is exported).
- Tests `tests/mla/test_cake_dsv41_mixed.py`: synthetic-manifest
dispatch rules, manifest / host consistency, planner parity tables,
public-API gates, and a GPU sweep of every exported variant for every
head count and both cache layouts, through the direct epilogue and the
split merge, at power-of-two and 61-row pages, against the fp32
exact-dequant reference.

## Validation (Cake compute steps)

This head (identity `7c7caa2c3571`, family files taken from the PR
commit) gated on three cards x three images (CI-equivalent `nvcc
-gencode=arch=compute_120f,code=sm_120f` of every TU, JIT build through
the JitSpec, `tests/mla/test_cake_dsv41_mixed.py`, the FP8-writer and
NVFP4 regression selections, paired P/S/O smoke benchmark):

| image | RTX 5090 | RTX PRO 6000 | GB10 (SM121, aarch64) |
|---|---|---|---|
| `nvcr.io/nvidia/pytorch:26.07-py3` (CUDA 13.3) | compile 48/48, JIT
ok, 117 passed / 1 skipped, 26, 12, bench 51 rows | same | same |
| `nvcr.io/nvidia/pytorch:25.08-py3` (CUDA 13.0) | 48/48 (nvcc 13.0),
JIT ok, 117 / 1, 26, 12, 51 | same | same |
| `nvcr.io/nvidia/pytorch:25.06-py3` (CUDA 12.9) | 48/48 (nvcc 12.9),
JIT ok, 117 / 1, 26, 12, 51 | same | same |

The previous export (`d12d3804aa0e`, 59 units: the same decode device
text with 14 single merge units and the earlier binding) passed the same
nine gates (compile 60/60, 102 passed / 1 skipped, 26, 12, 51 rows on
every image x card).

The three toolchains run the tests, not only the compile: the 13.2+
images take the direct E2M1 `cvt` unpack, the 13.0 / 12.9 images the
F16-route fallback bodies (`tl+ip+e2f` form), all against the fp32
exact-dequant reference.

CUDA 12.9 note: the sibling NVFP4 Cake family's regression slice passes
12 / 12 on the 12.9 image in this round (this branch's base includes
#6027, which regenerated that family's SM120 decode kernels for 12.9
ptxas); the 3 / 12 failures noted in the earlier version of this
description were measured against an older base.

Size against `main`: 61 files, +527,990 / -192,192 lines (the family
directory itself: 50 files, 40.5 MB).

Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Zihao Ye <expye@outlook.com>

### [67b5462](https://github.com/flashinfer-ai/flashinfer/commit/67b54628b821a65f67f8fa16685852e48ba32913)

- **作者**: eigen
- **时间**: 2026-10-06T08:09:09Z
- **提交信息**: perf(cake_fp8_projection): Kimi-K3 KDA/MLA projection GEMM round 6 (L2 prefetch, weight multicast, TMA-store epilogue, cluster split-K, 192-wide / stream-K GEMM, PDL), shared-source export (SM100a, SM103a) (#5672)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Round 6 of the experimental generated-program backend for the serialized
`FP8_PB_WO` KDA / MLA projection GEMMs of `nvidia/Kimi-K3-NVFP4` on
`sm_100a` (B200) and `sm_103a` (B300 / GB300):
`flashinfer/experimental/kimi_k3_fp8_projection`. Rounds 1-5: #5572,
#5590, #5611, #5635, #5654.

This head is the **re-export of the round-6 programs in the
shared-source layout** that #5888 introduced for this package (one
`_kernel.cu` / `_binding.cu` pair per program with `__CUDA_ARCH__`
guards, shared `_device_common.cuh` / `_host_common.cuh`, `MODULES` one
record per program with its architectures, `KERNELS` with compile-line
defines). It replaces the previous per-architecture head (186 generated
files) and rebases the host package onto the current `main`
(`DeviceFacts`, `decode_table(arch)`, `kernel_program`).

### What round 6 adds on top of round 5 (both architectures)

Decode programs (table-driven, `decode_table.py`):
- **TMA-store epilogue** (`tstore`, key field `_tso`): the epilogue
warps stage the BF16 tile in SMEM and one elected thread issues
`cp.async.bulk.tensor` stores; 16-byte-aligned output views only, host
rule `route_plan(decode_tma_store=...)`.
- **Weight-stream L2 prefetch** (`pf`, `_pf<D>`), **BF16 token-tile L2
prefetch** (`pfx`, `_px<D>`) and **cross-item prefetch by the load
warp** (`pfi`, `_pi<n>`).
- **2-CTA weight multicast** (`mc`, `_mc<C>`): the m tiles of one N tile
run as a cluster and share each weight stage through TMA multicast.
- **Non-portable cluster split-K up to 16 CTAs** (`csplit` 2..16,
`_cs<C>[a]`) with the tabulated co-resident cluster capacities
(`DECODE_MAX_ACTIVE_CLUSTERS` 2..16; identical on B200 and B300).
- **5-stage t32 ring** (`stages`, `epi_chunk` 16, `_c16`), **16
quantizing warps** (`qwarps`, `_w16`), **half-slot BF16 ring** (`xbh`,
`_xh`) and **early half-slot release** (`qer`, `_qe`) on the fused
16384-row bucket.

GEMM programs (persistent 2-CTA GEMM, M > 256):
- **Weight prefetch** `gemm_tstore_pf<D>` (`gemm_pf`), **192-wide N
tile** `gemm_*_n192` (`gemm_bn`) for the N = 576 `kv_a` family.
- **Ordered stream-K** `gemm_tstore[_n192]_sk` (`gemm_sk`,
`gemm_sk_ksplit`) on the wave-quantized rows: FP32 partials handed off
in ordinal order through a hand-off area behind the activation scale
tiles (bit-exact with the data-parallel program).
- **Fix-up stream-K** `gemm_tstore[_n192]_skf` (`gemm_skf`) on three
rows with a fractional last wave (`384,28,256`, `386,28,256`,
`5,28,16384`): the FP32 partials of the split tiles are added in ordinal
order before the BF16 rounding. This is the one lever that changes the
reduction order: declared max_abs_err 0.03125 vs the data-parallel
program, < 0.01 % of the elements differ by one BF16 ulp; package
tolerance unchanged (atol = rtol = 1e-2).
- **Programmatic dependent launch** on every stage (quantization pass
included).

Host package: `cake_backend.py` carries the Cake dispatch rules as host
mirrors (`DecodeConfig` fields, `decode_cluster_capacity`,
`gemm_prefetch_distance`, `gemm_block_n`, `gemm_stream_k_plan` /
`StreamKPlan`, `gemm_stream_k_fixup_plan` / `StreamKFixupPlan`,
`required_kernel_keys`, `route_plan`); `cake_jit.py` carries the round-6
kernel-key fields and `gemm_kernel_key`; `decode_table.py` is rendered
from the measured Cake table (shared cells + per-architecture
overrides); the package test pins every rule.

### Evidence

- Export protocol (Cake `tools/export-generated-programs`, CUPTI graph
replay, source program vs exported program per contract row): **220 /
220 rows sealed on B200 and on B300**; `delivery.patch` byte-identical
from both architectures (SHA-256
`b9c0bca771576674267b8448713dac0ed64e6653131e7210fcdd5c794b4c0b1b`).
- Package tests
`tests/experimental/test_cake_kimi_k3_fp8_projection.py`: 48 / 48 passed
on B200, 48 / 48 passed on B300.
- Exported programs vs the fastest existing FlashInfer / DeepGEMM chain
(`benchmarks/bench_cake_kimi_k3_fp8_projection.py --cupti`, 132 perf
rows): B200 132 / 132 rows faster, geomean 2.040x, min 1.030x
(`tp1_fused_qkvg_m8`); B300 132 / 132 rows faster, geomean 2.026x, min
1.040x (`tp1_fused_qkvg_m1`).
- Round-6 development evidence (own-process paired A/B per lever,
per-row floors, convergence verdict per row) is in the Cake design
document of the round; the previous head's description holds the
per-continuation history.

### Test plan

- `pytest tests/experimental/test_cake_kimi_k3_fp8_projection.py` on
B200 and B300 (run on both).
- `python benchmarks/bench_cake_kimi_k3_fp8_projection.py --cupti` on
B200 and B300 (run on both).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ee4e148](https://github.com/flashinfer-ai/flashinfer/commit/ee4e148e3c5785a02b62b308e9556a621c5f3c43)

- **作者**: eigen
- **时间**: 2026-10-06T08:07:20Z
- **提交信息**: perf(cake_fused_moe): thread-block-cluster routing kernel for the 512- and 1024-token Kimi-K3 NVFP4 SiTU rows (SM100/SM103) (#5895)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Replaces the routing kernel of the 512- and 1024-token routes of the
Cake Kimi-K3 NVFP4 SiTU experts (`cutlass_fused_moe(...,
activation_type=ActivationType.Situ, tp_size=8, backend="cake")`) on
SM100 (B200) and SM103 (B300) with a kernel that runs as one
thread-block cluster, and moves those routes to a seven-row FC2 work
pool. Shipped for both architectures.

- **Cluster routing kernel (`kimi_k3_route_cluster_workfeed_v16_mc8`).**
The previous routing kernel ran as a single CTA of 512 threads and spent
its time in latency-bound serial loops on one SM (route reset,
per-expert histogram, tile prefix scan, scatter). The new kernel is
launched as one cluster of eight CTAs (`__cluster_dims__(8,1,1)`, 512
threads each, 16512 bytes of shared memory). Every CTA resets an
interleaved share of the route rows and builds the histogram of an
interleaved share of the (token, expert) pairs in its own shared memory;
after a cluster barrier every CTA reads every peer's histogram through
distributed shared memory, so all CTAs hold the identical per-expert
totals and a rank-exclusive base per expert; the tile prefix is computed
redundantly from the totals and CTA 0 publishes the expert tables,
`total_tiles` and the FC2 work counter; after a second cluster barrier
every CTA scatters its own pairs into the rows `[base, base +
local_count)` of each expert span and writes the tile tables for the
tiles that start inside its range. Expert counts, tile offsets, tile
tables, `total_tiles` and the FC2 work counter are the same values as
before; the row order inside an expert span is assigned by atomics, as
before. The kernel count per call stays at five; the launch uses the
cluster attribute and is graph-capturable.
- **Seven-row FC2 work pool.** The 512- and 1024-token routes now
prepare `fc2_grid_n = min(max_tiles, 7)` (7 * 28 = 196 FC2 CTAs on the
148-SM B200 and B300) instead of `sm_count // 28` = 5 rows; the routing
kernel initializes the work counter with the pool size, as before. Host
launch parameters only; the FC2 program is unchanged.

The `(arch, n32_claim8)` routes point at a new prepared launch sequence
per architecture (quantization, cluster routing kernel, FC1, FC2,
finalize; the four shared stage programs are the existing records). Six
generated translation units are added under
`csrc/fused_moe/cake_kimi_k3_situ/{sm_100a,sm_103a}` (routing kernel +
binding and the sequence binding per architecture) and the six sources
of the superseded single-CTA routing kernel and sequences are removed
(150 -> 150 translation units). `flashinfer/jit/cake_kimi_k3_situ.py`
gains the four program records, drops the four superseded ones and
repoints the two routes; `flashinfer/fused_moe/cake_kimi_k3_situ.py`
launches the routing stage of these routes on a grid of eight CTAs and
prepares their seven-row pool (additive hunks only). The public API,
every other program record and generated source, the workspace layout
and the tutorial are unchanged. Generated CUDA sources are emitted
verbatim by the exporter and are not hand-formatted, as in the previous
revisions.

## Baseline / source PRs

- #5183 (the Cake Kimi-K3 NVFP4 SiTU experts; merged as 88c241d4) -- the
routes, programs and runtime this change extends; its merged
512/1024-token route (single-CTA routing kernel, five-row pool) is the
"previous export" arm below.
- #5736 (open; small token counts) and #5755 (open; 16384 tokens) edit
the same registration and runtime modules with disjoint program records
and routes; whichever merges later rebases onto the others.
- FlashInfer comparison baseline for the measurements:
`trtllm_fp4_block_scale_routed_moe` at
`ac7bce13ea0ff76392fd17aa696b096e191d0825`, including input quantization
and finalization for the same complete-call boundary.

## Performance

Eight physical rows: B200 and B300 at M = 512 and M = 1024 with uniform
and skewed routing, each measured in one isolated step per row with five
arms under the frozen protocol of #5183 (symmetric external CUDA graphs,
CUPTI activity timing with cold L2, three counterbalanced groups, 100 ms
warmup and 1000 ms reportable budget per arm/group, minimum 1900 MHz SM
clock): the current source implementation, this export, the FlashInfer
baseline, the previous export (#5183 as merged, measured twice under two
namespaces -- the second measurement agrees with the first within
0.09%). Qualification requires source/export >= 0.97, directional
disagreement <= 2%, sustained endpoint drift <= 2%, activity parity,
allocation-free submission and no regression against the previous
export. Correctness (every BF16 element at `atol=1.0, rtol=0.1`, exact
intermediate arrays, exact routing tables, per-expert row sets of the
permutation with its exact inverse map) runs before and after each
measurement; each row additionally passes compute-sanitizer synccheck,
racecheck and memcheck on the source and the realized export before it
is timed, and an independent CPU audit re-derives every number from the
raw samples.

`FlashInfer / Export` compares the FlashInfer baseline with this export
(values above 1 favor the export). `Source / Export` measures retention
of the source implementation's performance. `Previous export / Export`
compares the export merged in #5183 with this one (values above 1 mean
this revision is faster). `Export / roofline` is the export latency over
the row's roofline (max of the memory-traffic floor at peak bandwidth
and the compute floor), with the remaining gap in microseconds.

| Row | Export us | FlashInfer / Export | Source / Export | Previous
export / Export | Export / roofline (gap) |
|---|---:|---:|---:|---:|---:|
| B300 (sm_103a) M512 uniform | 349.826 | 1.0553x | 1.0001x | 1.0125x |
1.20x (+57.2 us) |
| B300 (sm_103a) M512 skew | 376.163 | 1.0458x | 0.9996x | 1.0097x |
1.29x (+83.6 us)* |
| B300 (sm_103a) M1024 uniform | 375.202 | 1.0551x | 0.9996x | 1.0284x |
1.23x (+71.2 us) |
| B300 (sm_103a) M1024 skew | 432.515 | 1.0565x | 0.9995x | 1.0235x |
1.42x (+128.5 us)* |
| B200 (sm_100a) M512 uniform | 347.200 | 1.0449x | 0.9991x | 1.0135x |
1.19x (+54.6 us) |
| B200 (sm_100a) M512 skew | 374.337 | 1.0350x | 0.9996x | 1.0107x |
1.28x (+81.7 us)* |
| B200 (sm_100a) M1024 uniform | 370.239 | 1.0481x | 1.0002x | 1.0324x |
1.22x (+66.2 us) |
| B200 (sm_100a) M1024 skew | 434.111 | 1.0423x | 0.9996x | 1.0245x |
1.43x (+130.1 us)* |

\* Skewed-routing floors use the uniform expert-occupancy count, so the
floor is an upper bound and the gap a lower bound.

Geomeans over the eight rows: FlashInfer / Export 1.0478x, Previous
export / Export 1.0194x; Source / Export between 0.9991x and 1.0002x.
Final outputs and exact intermediates are bitwise identical to the
source and to the previous export on every row and every round; the
routing tables (expert counts, tile offsets, tile tables, `total_tiles`,
work counter) are bitwise identical to the previous export's, and the
per-expert row sets of the permutation are equal with the exact inverse
map (the previous kernel also assigns the in-span order by atomics and
is not run-to-run bitwise there). Largest sustained endpoint drift
0.23%, largest directional disagreement 0.04% (gate 2%).

## Absolute timings (previous route vs this route)

Complete-call medians from the same five-arm step per row (CUPTI
activity timing, cold L2, three counterbalanced groups, same inputs and
workspace). Both arms run five kernels per call; the difference is the
cluster routing kernel plus the seven-row pool against the single-CTA
routing kernel plus the five-row pool, every other stage being the same
program on the same inputs.

| GPU | Tokens | Routing | Previous export (single-CTA router, five-row
pool) | This export (cluster router, seven-row pool) | Difference |
|---|---:|---|---:|---:|---:|
| B300 (sm_103a) | 512 | uniform | 354.2 us | 349.8 us | -4.4 us
(1.0125x) |
| B300 (sm_103a) | 512 | skewed | 379.8 us | 376.2 us | -3.6 us
(1.0097x) |
| B300 (sm_103a) | 1024 | uniform | 385.9 us | 375.2 us | -10.7 us
(1.0284x) |
| B300 (sm_103a) | 1024 | skewed | 442.7 us | 432.5 us | -10.1 us
(1.0235x) |
| B200 (sm_100a) | 512 | uniform | 351.9 us | 347.2 us | -4.7 us
(1.0135x) |
| B200 (sm_100a) | 512 | skewed | 378.3 us | 374.3 us | -4.0 us
(1.0107x) |
| B200 (sm_100a) | 1024 | uniform | 382.2 us | 370.2 us | -12.0 us
(1.0324x) |
| B200 (sm_100a) | 1024 | skewed | 444.7 us | 434.1 us | -10.6 us
(1.0245x) |

## Generated sources

The six `.cu` files and the four program records are emitted by the Loom
kernel exporter (`python -m loom.export.generated_programs`: `protocol`
freezes the export protocol, `run` generates the sources into a clean
FlashInfer worktree; the Kimi-K3 SiTU operator adapter supplies the
shapes and callbacks). Each record's `closure_sha256` is computed over
the record identity and the SHA-256 of every listed source, and
`cache_name` carries its prefix, so the committed sources are checked
against the records on every export. The generated files are not
hand-edited. The routing kernel's compiled image is identical on both
architectures' measurement runs to the one profiled during development
(32 registers, 16512 bytes of shared memory, cluster (8,1,1)).

## Evidence

The measurement receipts (five-arm timer results, independent raw CPU
audits, sanitizer records, prepare realizations) are archived on the
measurement clusters; the accompanying evidence manifest lists every
artifact as host / absolute path / size / SHA-256. No artifacts are
attached to this PR.

## Notes from review

- The DSMEM reduction is fully unrolled by the generator: each thread
owns two experts and reads the eight peers' counts for both in a fixed
rank order (16 independent `mapa` + `ld.shared::cluster` scalar loads
per thread). The fixed order is what makes the totals and the
rank-exclusive bases identical in every CTA; the loads are the whole
reduction phase and are not batched, because batching would need the
peer histograms laid out per thread rather than per expert, which would
change the production scatter formulas kept byte-identical here.
- `flashinfer/jit/cake_kimi_k3_situ.py` is generator output. Program
records are keyed by the content hash of their sources, so replacing the
four 512/1024-token records and repointing the two `(arch, n32_claim8)`
routes renames the affected keys; every other record is unchanged.
- The FC2 pool-row selection in `cake_fused_moe_prepare_workspace` is
one if/elif chain keyed on the route flags (follow-up commit).

## Test plan

- `tests/moe/test_cake_kimi_k3_situ.py` (SM100a / SM103a) via the CI
bots: workspace-size query, prepared-workspace binding, complete-call
correctness against the reference and graph capture/replay; the
512-token case of the complete-call test now runs the cluster routing
kernel and asserts the prepared shape (route flag, seven-row pool, 196
work-pool CTAs).
- Added: two skewed-routing cases of the complete-call test (512 and
1024 tokens; every token picks one of four disjoint 16-expert groups, so
64 experts each own several 32-row tiles and the cluster kernel's
rank-exclusive scatter ranges cover multi-tile expert spans). The
1024-token route is thereby exercised end to end as well.
- Added: a GPU-free test that each architecture's 512/1024-token
sequence lists exactly one routing kernel source and that it declares
the eight-CTA cluster the runtime launches.
- `python -m py_compile` on `flashinfer/jit/cake_kimi_k3_situ.py` and
`flashinfer/fused_moe/cake_kimi_k3_situ.py`; `ruff format --check` and
`ruff check` (0.12.8) on the three Python files.

Related:
[4254](https://github.com/flashinfer-ai/flashinfer/issues/4254).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Updated routed MoE execution for 512- and 1024-token workloads with
clustered routing and a capped FC2 work pool. Routing behavior for other
token counts remains unchanged.
* Updated kernel selection for 32-token workloads on SM100 and SM103;
both architectures use the `n32_claim8` route.
* **Bug Fixes**
* Added coverage for skewed routing workloads and prepared-workspace
behavior to help verify routing and FC2 execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [16f0f22](https://github.com/flashinfer-ai/flashinfer/commit/16f0f22c805af7897ec5c7e1af65e52fa44b6066)

- **作者**: eigen
- **时间**: 2026-10-06T07:25:54Z
- **提交信息**: feat(cake_dsv4): NVFP4 DeepSeek-V4 sparse-MLA decode on SM100/SM103 (backend="cake") (#6103)

## Summary

Adds the DeepSeek-V4 NVFP4 (384 B/token) sparse-MLA decode for SM100 /
SM103 (B200 / GB300) behind the existing public entry:

```python
trtllm_batch_decode_sparse_mla_dsv4(..., kv_cache_format="nvfp4", backend="cake")
```

The cache ABI is the one already consumed by `backend="sparse"` on SM120
/ SM121 (448 NoPE values as E2M1 with one E4M3 scale per 16 values, 64
BF16 RoPE values; `page_size * 352` data bytes followed by `page_size *
32` scale bytes per page). The generated decode kernel family
(`csrc/cake_dsv4/sm_100a/`, `csrc/cake_dsv4/sm_103a/`: persistent, 2-CTA
cluster, 64-head tile, persistent SwapsAB, one-tile SwapsAB and one-tile
members with their `tile_n` / `o_chunks` variants, plus a split merge)
reads the quantized cache directly: tcgen05 block-scaled MMA for QK^T,
FP8 MMA for PV, fp32 online softmax, BF16 output.

- Two independent selection tables (`sparse_indices` over
`swa_kv_cache`, `extra_sparse_indices` over `compressed_kv_cache`) with
their own `*_topk_lens`, `-1` masking, `sinks`, caller-owned
`workspace_buffer`
(`flashinfer.mla.cake_dsv4.get_cake_dsv4_workspace_bytes`), CUDA-Graph
safe, no device allocation.
- `nvfp4_quantize_pack_sparse_mla_cache` /
`nvfp4_quantize_append_sparse_mla_cache` now build and run on SM100 /
SM103 (same implementation and bytes as on SM120 / SM121).
- `backend="auto"` on SM100 / SM103 is unchanged (TRTLLM-GEN); the NVFP4
route is opt-in via `backend="cake"`.

## Generated sources and registry

`csrc/cake_dsv4/common/` gains 14 NVFP4 decode programs
(`nvfp4_decode_<member>[_n<tile_n>][_oc<o_chunks>]`: persistent,
cluster, t64, pv x2, swap x6, tile x3) and the split merge as
`cake_dsv4_nvfp4_<variant>_{kernel,binding}.cu`, one source per program
compiled for both architectures (the sm_100a and sm_103a renders are
byte-identical modulo the generated names, so nothing is kept per
architecture); `flashinfer/jit/cake_dsv4.py` registers them per
architecture with four shared argument plans (`_PLAN_NVFP4_DECODE`,
`_PLAN_NVFP4_TILE`, `_PLAN_NVFP4_G4`, `_PLAN_NVFP4_MERGE`), following
the data-only registry of #5920. The host plan (`_nvfp4_plan`) mirrors
the Cake planner: member and knobs from the SM count, token count, head
count and candidate tiles; the merge launch takes `heads_per_cta` (the
smallest power of two keeping at most one merge CTA per SM). The route
prepares the decode and the merge launches first and issues both through
`run_sequence`. The NVFP4 bindings do not use the SM103 descriptor slab
(descriptors are passed by value on both architectures).

## Measurement notes

The device kernels are the ones measured in the Cake source tree.
Through the FlashInfer JIT the E2M1 x E4M3 scale multiply compiles from
public PTX (an 8-byte magnitude table per 16-value block selected with
`prmt`, bit-identical to the fused form); the source-tree build patches
the fused form into the cubin. Across the 76 exported shapes per
architecture the source-tree latency is 0.957x (B200) / 0.953x (GB300)
of the FlashInfer-route latency (geomean; the public-PTX multiply costs
4-5 % on these 6-50 us kernels), with identical outputs on every shape.
The benchmark below reports the FlashInfer-route numbers.

## Tests

- `tests/mla/test_cake_dsv4_nvfp4_route.py`: host plan against the Cake
planner's plan table (128 entries on 148 / 152 SMs), member selection
and rejection paths (CPU); `tests/mla/test_cake_dsv4.py` registry checks
cover the new variants.
- `tests/attention/test_sparse_mla_blackwell_dsv4_nvfp4.py`: cache
pack/append byte checks and decode through the public entry against the
dequantized-cache reference (single and dual cache, extra page sizes 2 /
64, top-k lengths 0 / 1 / 63 / 65 / full with `-1` entries and sinks,
all-masked rows, NHD layout, CUDA-graph replay bitwise x3, LSE read back
from the workspace). The three test files pass on B200 and GB300 (428
tests).

## Benchmark

`benchmarks/bench_cake_dsv4_nvfp4_decode.py` times the public entry on
representative decode rows (cold-L2 CUPTI, 1 Mi-token HBM pools, random
selections without replacement) with an informational TRTLLM-GEN FP8
column.

## Docs

`docs/api/attention.rst` documents the NVFP4 format and the
`backend="cake"` route.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added Cake backend support for NVFP4 DeepSeek-V4 sparse attention on
SM100 and SM103, including cache packing, appending, and decoding with
separate main and compressed index tables.
* Added NVFP4 workspace sizing options and documented supported backend
and architecture combinations.
* Added a benchmark for NVFP4 sparse decode, with optional FP8
comparison and JSON output.
* **Tests**
* Added coverage for cache operations, decoding, planning, workspace
sizing, and CUDA Graph replay.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4555
- **最后更新**: 2026-10-07T00:09:58Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 2
- **主要提交者**: William Lin, Aryan Kumar

## AI分析总结

# FastVideo 仓库昨日提交分析

## 1. 主要更新类型

本次 5 条提交呈现**功能新增为主、文档更新为辅**的格局，核心主题聚焦于 **FastH3**（可能是视频扩散模型推理加速相关组件）的多硬件平台支持，以及 **Kandinsky-6.0**（新视频生成/编辑模型）的 pipeline 接入。涉及功能开发、模型集成、文档同步三类变更，未见明显的 Bug 修复或性能调优类提交。

## 2. 关键变更点与项目方向的关系

- **FastH3 的跨平台部署**（提交 #1919、#1920）：FastH3 继续在不同硬件上扩展——先支持单张 RTX GPU（面向消费级 NVIDIA 显卡），再进一步覆盖 DGX Spark（企业级推理平台）和 Apple Silicon（Mac 生态）。这一演进方向与 README 中体现的项目愿景高度一致：FastVideo 本身强调快速推理与易用性（文档、Cookbook、Quick Start、Slack 社区齐备），快速将新架构推向消费级与移动端硬件，正符合其降低视频生成门槛的定位。
- **FastH3 Trim 的文档公告**（提交 #1923）：配合硬件适配工作，文档层面同步宣布 FastH3 在消费级硬件上的能力及"Trim"特性（推测是模型裁剪/压缩版本），说明团队在功能落地的同时重视用户可发现性和使用引导。
- **Kandinsky-6.0 集成**（提交 #1924、#1925）：引入 TI2VA（文本/图像到视频动画）和 VSR（视频超分辨率）两条 pipeline，并在 README 新闻区公告。这表明项目持续扩充支持的模型阵容，从单一代理解码/生成架构向**多样化视频生成与增强工作流**拓展。

## 3. 对项目的影响和潜在意义

- **可及性显著提升**：FastH3 从单卡 RTX 一路适配到 Apple Silicon，意味着开发者无需企业级 GPU 即可运行该架构，有助于社区规模扩大和开发者采用率提高。
- **生态完整性增强**：Kandinsky-6.0 的 TI2VA 与 VSR pipeline 使 FastVideo 覆盖了更完整的视频生成/增强链路（生成 → 超分），提升了平台作为"一站式视频推理框架"的竞争力。
- **发布节奏与社区协作**：多条提交由外部贡献者（Aryan Kumar 等）与 AI 助手共同协作完成，且有文档与功能配套推送（#1923、#1925 紧跟其后），体现了成熟、规范的贡献者协作流程。

## 4. 值得关注的技术点

- **跨架构部署一致性**：DGX Spark、单卡 RTX、Apple Silicon 属于差异巨大的硬件栈（x86+专用加速 vs 消费级 CUDA vs ARM/Metal），FastH3 在三者上的同时支持暗示了背后有统一的硬件抽象层或大量针对 Metal/CUDA 的后端实现，值得深入代码关注。
- **FastH3 与"Trim"机制**：Trim 可能涉及模型量化、通道裁剪或推理路径优化，这是在消费级硬件上获得实用吞吐量的关键，是值得进一步技术拆解的点。
- **VSR pipeline 的工程化**：视频超分对显存与内存带宽要求高，能在消费级设备落地说明团队在内存管理/分块推理上可能有工程创新。
- **AI 辅助开发模式**：多条提交的 Co-author 列表中出现 Claude Opus 5.5，反映出该项目已将 AI 编程工具深度纳入开发流程，可作为协作效率的观察样本。

## 5. 对项目发展的整体影响

结合 README 可知，FastVideo 定位为快速、易用的视频生成/推理平台，配套完善的文档体系、Cookbook 教程、周例会和 Slack 社区。本次提交延续了该定位：

- **FastH3 硬件矩阵的完善**直接呼应了"Quick Start"与"Cookbook"的易用性承诺——用户在更广泛的硬件上能跑起来，平台的实际可访问性和用户粘性将得到切实提升。
- **Kandinsky-6.0 的接入**扩充了模型库，使 FastVideo 不再只是单一架构的加速器，而是向"支持多模型、多任务的视频推理枢纽"演进，这为其在开源视频 AI 生态中确立长期地位奠定基础。
- **文档与功能的同步节奏**（新闻条目与 pipeline 提交配对出现）表明项目处于活跃、健康的迭代周期，对外释放了"持续供给新能力"的积极信号。

综合来看，昨日提交的核心价值在于：通过 **FastH3 的消费级硬件普及**与 **Kandinsky-6.0 的多任务集成**，双线推进 FastVideo 在"低门槛"与"多功能"两个维度上的发展，进一步巩固其作为开源视频推理快速上手框架的定位。

## 详细提交记录

### [02a027c](https://github.com/hao-ai-lab/FastVideo/commit/02a027c49f3fa099f1a0eb1305a6646415406d87)

- **作者**: Aryan Kumar
- **时间**: 2026-10-06T19:17:11Z
- **提交信息**: [feat]: FastH3 on DGX Spark and Apple Silicon (#1920)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>
Co-authored-by: Aryan Kumar <aryank@Aryans-Mac-Studio.local>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e235b6a](https://github.com/hao-ai-lab/FastVideo/commit/e235b6a332a2c7a855556cee89edab2b3af997f5)

- **作者**: Aryan Kumar
- **时间**: 2026-10-06T18:39:24Z
- **提交信息**: [docs] Announce FastH3 on consumer hardware and FastH3 Trim (#1923)

### [8b51380](https://github.com/hao-ai-lab/FastVideo/commit/8b51380466a963692a8c0afa254417bfcc2ba8bc)

- **作者**: Aryan Kumar
- **时间**: 2026-10-06T18:37:01Z
- **提交信息**: [feat]: FastH3 on single RTX GPUs (#1919)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>
Co-authored-by: Aryan Kumar <aryank@Aryans-Mac-Studio.local>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [527a316](https://github.com/hao-ai-lab/FastVideo/commit/527a3165b9af3ab2a48a622c3de8e0b5e5828121)

- **作者**: William Lin
- **时间**: 2026-10-06T18:05:40Z
- **提交信息**: [docs]: add Kandinsky 6 to the README news (#1925)

### [f06d824](https://github.com/hao-ai-lab/FastVideo/commit/f06d824054034e6b8d54a69286b16ee6b28c94c0)

- **作者**: William Lin
- **时间**: 2026-10-06T17:50:17Z
- **提交信息**: [feat]: add Kandinsky-6.0 TI2VA and VSR pipelines (#1924)

Co-authored-by: leffff <levnovitskiy@gmail.com>
Co-authored-by: Kirill <kykozlov@gmail.com>
Co-authored-by: shaoxiongduan <shaoxiongduan@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34673
- **最后更新**: 2026-10-06T19:12:23Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Sayak Paul, YiYi Xu, Pauline Bailly-Masson

## AI分析总结

# diffusers 昨日提交分析总结

## 1. 主要更新类型
- **功能新增**：Kandinsky 6 模型集成（占主导，PR #14949），新增音频-视频扩散管线（TI2VA 和 SR 管线）。
- **Bug修复**：FlowMatchEulerDiscreteScheduler 的 timestep 处理修复（PR #14956）。
- **文档更新**：Jobs 指南文档（PR #14926）和 Kandinsky 6 文档（部分在 #14949）。
- **依赖/维护更新**：doc-builder 工作流 pin 版本升级（PR #14957），涉及 CI/CD 工作流。

## 2. 关键变更点及其与项目整体方向的关系
- **Kandinsky 6 集成**：这是核心功能扩展，实现了多模态（文本到视频/音频）扩散模型。这与 diffusers 项目目标一致——为 Hugging Face 生态提供先进扩散模型的标准化加载和使用 API（README 中强调的“统一模型加载库”）。它补充了现有管线（如文本到视频、超分辨率），提升库的多模态能力。
- **调度器修复**：改进 FlowMatchEulerDiscreteScheduler 对显式 timestep 的处理（包括无 sigma 时的警告），确保与项目中其他调度器的兼容性。这支持了模型微调和推理的稳定 API，维护库的模块化设计。
- **文档和 CI 更新**：Jobs 指南简化了训练/微调工作流，而 doc-builder pin 升级确保文档构建工具链的稳定性。这些变更反映了项目对开发者体验和社区贡献的重视（README 提到 Apache 许可和协作开发）。
- **重构细节**（Kandinsky 6 内）：移除冗余代码、统一注意力处理器、优化依赖（移除 einops/pydantic，改为 lazy imports）。这强化了项目的性能导向和最小依赖原则，符合开源库的可维护性目标。

## 3. 对项目的影响和潜在意义
- **正面影响**：扩展了 diffusers 的模型覆盖范围，特别是音频/视频生成领域，潜在推动了社区在创意 AI 工具（如视频编辑、音频合成）中的应用。这提升了库的竞争力，与 Hugging Face 作为 AI 平台的整体愿景对齐。
- **潜在风险**：Kandinsky 6 的引入涉及大量代码变更（多次重命名和修复），可能带来初始兼容性挑战（如 checkpoint 名称不匹配，已在提交中解决）。但最终通过验证 checkpoint 一致性确保了稳定性。
- **整体意义**：这些提交增强了项目的健壮性和文档支持，减少了用户门槛，促进更多开发者采用和贡献。这有助于 diffusers 作为开源扩散模型库的领导地位，支持从研究到生产的全流程。

## 4. 值得关注的技术点
- **多模态管线架构**：Kandinsky 6 使用 PiflowScheduler 和 MMAudioVAE 实现音频-视频融合，体现了扩散模型在模态间的灵活扩展；注意力处理器移到 transformer 文件中，优化了模块化。
- **依赖管理**：修复 unguarded 依赖问题（移除不必要的模块），通过 lazy imports（如 torchvision、av）减少安装负担，这在库开发中是最佳实践。
- **调度器鲁棒性**：显式 timestep 处理 + 警告机制，展示了对边缘情况的细致处理，避免用户在微调时出错。
- **CI/CD 维护**：工作流 pin 升级确保工具链一致，避免文档构建失败——这对高频更新的开源项目至关重要。
- **重构深度**：Kandinsky 6 提交包含数十次迭代（从实现到 review 反馈），突显了 diffusers 社区的协作文化和高质量标准。

## 5. 基于项目背景的项目发展影响
结合 README 中的核心目标——“统一扩散模型加载和使用”，这些提交推动了项目从单一模型支持向多模态生态的转型。Kandinsky 6 的加入直接响应了行业对音频/视频生成的需求，增强了 diffusers 作为 Hugging Face 模型 hub 的桥梁作用（README 许可声明强调的开放协作）。文档和修复提交则维护了库的可靠性和易用性，确保项目可持续发展。总体而言，这些变更将加速 AI 创意工具的普及，支持研究者和开发者快速集成先进模型，同时强化了 diffusers 在扩散模型领域的核心地位，为未来的版本（如 v1.0）奠定坚实基础。这些提交共同体现了项目对创新与质量的平衡追求。

## 详细提交记录

### [c6df88a](https://github.com/huggingface/diffusers/commit/c6df88a511a98740646ee55577b590c9852650ce)

- **作者**: Steven Liu
- **时间**: 2026-10-06T19:04:08Z
- **提交信息**: [docs] Jobs guide (#14926)

hf jobs

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [71774d9](https://github.com/huggingface/diffusers/commit/71774d9bc84600eb4c60522dbf85c4b8cc317e20)

- **作者**: Pauline Bailly-Masson
- **时间**: 2026-10-06T14:21:32Z
- **提交信息**: Bump doc-builder workflow pin (#14957)

* Bump doc-builder pin to 9fc8a41 in build_documentation.yml

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Bump doc-builder pin to 9fc8a41 in build_pr_documentation.yml

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Bump doc-builder pin to 9fc8a41 in upload_pr_documentation.yml

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [bc5e3bd](https://github.com/huggingface/diffusers/commit/bc5e3bd9c55412cb74b6ac5e4c690fc7030461aa)

- **作者**: Sayak Paul
- **时间**: 2026-10-06T12:04:58Z
- **提交信息**: Kandinsky6 (#14949)

* implement Kandinsky 6
 - add TI2VA and SR pipelines
 - additonally implement PiflowScheduler and MMAudioVAE

* update docs for Kandinsky 6

* remove redundant bigvgan code and manual checkpoint loading inside model
code

* add missing _no_split_modules

* use attention processor in SR

* fix unguarded dependencies
 - removed: einops, pydantic
 - lazy: torchvision, av, librosa

* remove dead manual weight loading code; flattent MMAudioVAE structure

* move attention processors to transformer files

* remove duplicate code in K6 latent_upscaler

* address 1st batch of comments

* patch transformer k6

* patch SR

* patch pipeline style

* replace TimestepEmbedding and fix batching

* refactor ti2va dit and pipeline

* refactor piflow scheduler

* refactor SR

* patch sr transformer autocast

* major refactor

* untrack notebooks directory

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* patch mmaudio VAE

* patch mmaudio VAE

* fix inits

* fix flex attn

* refactoring

* remove __all__

* separate MMAudio VAE and Vocoder

* fix naming

* refactor checkpointing, magcache, transformer, sr vae for K6

* refactor

* address apply_scale_shift_norm problem

* update docs

* apply style chanes

* address review feedback on transformer, SR VAE, and flex attention

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* address comments

* fix critical bugs

* Revert checkpoint-breaking module renames from 28c5326da

Commit 28c5326da (today, 14:03 +0300) renamed Kandinsky6FusedTransformerDecoderBlock's
videoT/audioT submodules to video_dec_block/audio_dec_block, and replaced both
Kandinsky6TimeEmbeddings and Kandinsky6SRTimeEmbeddings's hand-rolled in_layer/out_layer
with diffusers' Timesteps/TimestepEmbedding, purely for naming clarity. No checkpoint
conversion was re-run to match, so every published K6 checkpoint (unchanged since Sep 27,
confirmed via identical blob SHA256 across recent Hub commits) still ships the old names.

Verified against kandinskylab/Kandinsky-6.0-Pro-distill-5s-Diffusers and
kandinskylab/Kandinsky-6.0-VSR-5s-Diffusers: this was silently dropping ~65% of the main
transformer's weights (every visual_transformer_blocks.*.{video,audio}T.* parameter) and
the SR transformer's time embeddings, then crashing with "Cannot copy out of meta tensor"
on enable_model_cpu_offload(). After this revert, all checkpoint keys match exactly
(4471/4471 for the main transformer, 459/459 for the SR transformer).

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* Revert checkpoint-breaking latent-upscaler renames from 372f29088

Same class of regression as 9ae71f0d0, this time in Kandinsky6SRLatentUpscalerX2Branch
and Kandinsky6SRLatentUpscalerOutputHead: today's "address comments" commit (18:48 +0300)
dropped the private_ prefix from private_mid_blocks/private_upsample/private_blocks/
private_output_proj, and converted OutputHead from nn.Sequential to a plain nn.Module with
named norm/activation/conv submodules, again without a matching checkpoint re-conversion.

Verified against kandinskylab/Kandinsky-6.0-VSR-5s-Diffusers's latent_upscaler: this left
every Kandinsky6SRLatentUpscalerX2Branch parameter (and the OutputHead-based output_proj
used standalone by the x2/x4 branches) unfilled on the meta device, crashing
enable_model_cpu_offload() the same way as the main transformer did before 9ae71f0d0.

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* move vocoder and LU

* add coppied from resolve i2v cond mode

* rename variables

* fix lu rename bug

* Update src/diffusers/pipelines/kandinsky6/pipeline_kandinsky6_ti2va.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/models/transformers/transformer_kandinsky6.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* address yiyixuxu's comments

* fix audio channels bug

* fix tests

* Fix CI failures on the Kandinsky6 PR

- tests/others/test_utils.py: assert the caller file path without assuming the checkout directory is named `diffusers`.
- .github/workflows/pr_tests.yml: raise PYTEST_TIMEOUT to 300 s for the example and pipeline CPU steps. Both run several workers with four threads each on an 8-vCPU runner, and the checkpointing example tests run several training subprocesses in sequence.

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* Avoid staging LFS dedup race in the org push test

The second push in TestModelPushToHub.test_push_to_hub_in_organization sent the same model bytes as the first push. The staging server can deduplicate those bytes against the first push's LFS object and then reject the commit with "LFS pointer pointed to a file that does not exist". Change the weights before the second push so its bytes differ.

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* Revert "Avoid staging LFS dedup race in the org push test"

This reverts commit 35e6cc4ef.

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* Revert "Fix CI failures on the Kandinsky6 PR"

This reverts commit 60cad4341.

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* Apply suggestion from @yiyixuxu

* Apply suggestion from @yiyixuxu

* Apply batched suggestions from code review

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* remove review-only files from the Kandinsky6 PR

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* Apply suggestion from @yiyixuxu

* restore .gitignore to match main

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* simplify the mono audio handling in _write_audio

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* remove the no-op set_attention_backend calls from the Kandinsky6 docs

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* give the Kandinsky6 transformer its own output class instead of reusing LTX-2's

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* fix the stale pipeline exports and add return annotations for the Kandinsky6 pipelines

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* address feedback from @leffff

---------

Co-authored-by: Denis Koposov <denis.koposov@phystech.edu>
Co-authored-by: leffff <levnovitskiy@gmail.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Lev Novitskiy <57654885+leffff@users.noreply.github.com>
Co-authored-by: YiYi Xu <yixu310@gmail.com>

### [36438e2](https://github.com/huggingface/diffusers/commit/36438e2ee44a7b8939a06e9c635085d96ae83a3e)

- **作者**: YiYi Xu
- **时间**: 2026-10-06T08:42:25Z
- **提交信息**: fix https://github.com/huggingface/diffusers/issues/14461 (#14956)

* keep explicit timesteps in FlowMatchEulerDiscreteScheduler.set_timesteps and warn when they come without sigmas

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
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


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13202
- **最后更新**: 2026-10-07T00:15:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36825
- **最后更新**: 2026-10-07T01:27:34Z

## 提交统计

- **昨日提交总数**: 42
- **提交者数量**: 26
- **主要提交者**: Hongsheng Jin, DarkSharpness, Shangming Cai

## AI分析总结

## SGLang 昨日提交分析（42 条）

### 1. 主要更新类型
- **功能新增**：约 15 条，集中在 diffusion 扩散模型支持（Kandinsky 6、Qwen-Image-2.1 GGUF、LoRA）、AMD 硬件（MI355X DeepSeek-V4 Pro PD recipes、MXFP4/MXFP8 测试）、gRPC 元数据暴露、sgl-router 重试机制等。
- **Bug 修复**：约 12 条，涵盖 PD 分离崩溃、diffusion 请求参数丢失、mimo-vl 多模态特征、DeepEP 导入问题等。
- **性能/正确性优化**：约 8 条，包括 MLA KV 准备的 FP8 原生转换、mem_cache 前缀管理修复、DSA CUDA graph 回放修复等。
- **重构/工程化**：约 7 条，包括 rust-processor 拆分模块、Docker 镜像改用 uv 管理、HiCache buffer 模式管理等。

### 2. 关键变更点与项目方向的关系
SGLang 的核心目标是**大模型与多模态模型的高效推理**，本批提交充分体现了这一方向：

- **多模态扩散模型持续扩展**：多个 diffusion 提交（Kandinsky、Ideogram、Qwen-Image）表明项目正将推理框架覆盖到图像/视频生成场景。
- **硬件生态多元化**：AMD（MI30X/MI355X）、NVIDIA（Thor SM110、CUDA 134 nightly）持续投入，巩固多硬件后端支持。
- **PD 分离与推理调度优化**：sgl-router 重试机制系列（retry 1/5~5/5 共 5 条）与 PD 相关修复，说明分布式推理的鲁棒性是当前重点攻坚方向。
- **显存与缓存管理**：HiCache、mem_cache、DFlash draft KV pool 等多项修复，针对长上下文和 KV 缓存的正确性与效率。

### 3. 对项目的影响和潜在意义
- **可靠性显著提升**：sgl-router 的渐进式重试策略（跳过失败 worker、退避重试、超时约束）使分布式路由更具容错能力，对生产环境部署至关重要。
- **硬件适配面拓宽**：AMD MI355X 的 PD 配方与 MXFP4/MXFP8 测试表明项目在积极响应新一代 AMD GPU，有利于生态扩展。
- **架构更清晰**：rust-processor 拆分为 tokenizer/render/parser 三个 crate，提升代码模块化与维护性。
- **安全性加固**：diffusion 的 ZMQ ingress 限制为 loopback、文件名处理加固，对多租户部署有保护意义。

### 4. 值得关注的技术点
- **sgl-router 重试序列**：一条请求可被多次派发且跳过已失败 worker——这是路由层容错设计的重要演进。
- **MLA 的 SATFINITE FP8 原生转换**：直接在 KV/Q 准备阶段利用硬件能力，减少转换开销。
- **DeepSeek-V4.1 mHC 状态机统一**：简化了状态管理，删除了中等批次融合变体，属于化繁为简的架构收敛。
- **gRPC follower 元数据暴露**：为分布式部署提供节点级 KV 来源信息，有利于 RDMA/Mooncake 类传输方案。

### 5. 对项目整体发展的影响
结合 README 中"fast inference for LLMs and multimodal models"的定位，本批提交表明项目正朝三个维度深化：**推理性能持续压榨**（FP8、CUDA graph、prefix cache）、**多模态推理场景扩展**（diffusion 与 VL 模型修复）、**生产级可靠性建设**（路由重试、缓存一致性、PD 正确性）。大量 NVIDIA/AMD 社区与 Anthropic 协作者的参与，也显示出该项目正吸引更广泛的工业界与 AI 实验室贡献，生态活跃度持续走高。

## 详细提交记录

### [66dd4e1](https://github.com/sgl-project/sglang/commit/66dd4e15b9aaca870260258fd221bdf6205b65c4)

- **作者**: Duyi-Wang
- **时间**: 2026-10-06T23:58:40Z
- **提交信息**: [AMD][Docs] Add MI355X DeepSeek-V4 Pro PD recipes (#42757)

### [08aad0c](https://github.com/sgl-project/sglang/commit/08aad0c19646165387b75783fe1d30a9a84eb3f7)

- **作者**: metamergebot
- **时间**: 2026-10-06T23:45:05Z
- **提交信息**: [HiCache] Manage buffer-mode backups per storage pool (#42633)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [fd62ee8](https://github.com/sgl-project/sglang/commit/fd62ee84f71fcea88a35bd507236b8fc5a108696)

- **作者**: jain-ria
- **时间**: 2026-10-06T23:39:01Z
- **提交信息**: feat(grpc): expose follower metadata and node-local KV sources (#39659)

Signed-off-by: jain-ria <riajain@NVIDIA.com>
Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [90aa1cb](https://github.com/sgl-project/sglang/commit/90aa1cb0fbc0b99ba74a18a0df44151da40a59d5)

- **作者**: Chunan Zeng
- **时间**: 2026-10-06T23:15:34Z
- **提交信息**: [Scheduler] Gather prefill-delayer queue timeout across ranks (#42625)

Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>

### [0a0fe00](https://github.com/sgl-project/sglang/commit/0a0fe001f1d033c030b6f24e4eff52f0b3d0dad1)

- **作者**: Jan Bernlöhr
- **时间**: 2026-10-06T23:02:45Z
- **提交信息**: fix: route Thor SM110 FP8 and ModelOpt NVFP4 auto backends (#41765)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [6b737fd](https://github.com/sgl-project/sglang/commit/6b737fd4c675c65d6544bb7013d017688bb6f7c8)

- **作者**: metamergebot
- **时间**: 2026-10-06T22:50:59Z
- **提交信息**: Bind the MessageQueue remote socket atomically (#42695)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: charlotte12l <charlotte12l@users.noreply.github.com>

### [44a2558](https://github.com/sgl-project/sglang/commit/44a2558d4005d33571d348b13b29f62aff9acf0b)

- **作者**: Trevor Morris
- **时间**: 2026-10-06T21:52:42Z
- **提交信息**: [NVIDIA] Fix nightly-cu134 build and update (#42661)

### [264d1c2](https://github.com/sgl-project/sglang/commit/264d1c20153cadc921670b982e6531d9800353e6)

- **作者**: metamergebot
- **时间**: 2026-10-06T21:23:18Z
- **提交信息**: Back the DFlash-family draft KV pool to the post-capture token count (#42651)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: 842974287 <842974287@users.noreply.github.com>

### [4506927](https://github.com/sgl-project/sglang/commit/4506927635cc920c79bf19c79ea376d442e68b28)

- **作者**: metamergebot
- **时间**: 2026-10-06T21:20:41Z
- **提交信息**: [Metrics] Add per-rank DP attention imbalance metrics (#42755)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: hanming-lu <hanming-lu@users.noreply.github.com>

### [38bdf25](https://github.com/sgl-project/sglang/commit/38bdf25f8d34cf87f1151030ee89b012a9d85bfa)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-06T21:10:09Z
- **提交信息**: [Docker] Use uv-managed Python 3.12 and uv for all installs in the CUDA image (#42612)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [3eec178](https://github.com/sgl-project/sglang/commit/3eec178e480494355b16f20308e5a9a05cce54a6)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-06T21:09:57Z
- **提交信息**: [Spec][MegaMoE] Let the speculative draft choose its own W4A4 MXFP4 MegaMoE MMA type (#42022)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1200404](https://github.com/sgl-project/sglang/commit/12004043b8bd900d0b6eea9b64b5d9d09cddd337)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-06T20:11:29Z
- **提交信息**: [Metrics] Read scheduled prefill KV tokens from batch `prefix_lens` (#42797)

### [a34cba3](https://github.com/sgl-project/sglang/commit/a34cba3c62ff9c0a3e89df9bb25943844804c6ba)

- **作者**: metamergebot
- **时间**: 2026-10-06T18:02:23Z
- **提交信息**: [HiCache] Resolve write_back to write_through under buffer_only host memory (#42754)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [0f57a39](https://github.com/sgl-project/sglang/commit/0f57a391521a4e741e2446c9f2c3762c40098c44)

- **作者**: Kan Wu
- **时间**: 2026-10-06T17:58:38Z
- **提交信息**: [rust-processor] Gate render, tokenizer and parser behind cargo features (#42663)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [abed685](https://github.com/sgl-project/sglang/commit/abed685de1e59e8ca8d82a34c99c6332ce59d556)

- **作者**: Byron Hsu
- **时间**: 2026-10-06T16:36:31Z
- **提交信息**: [PD] Fix crash for allocation when mamba + pd + decode radix cache (#41927)

### [209e190](https://github.com/sgl-project/sglang/commit/209e190ee568d346abb50b5d4bd0cb0d2192a73d)

- **作者**: Michael
- **时间**: 2026-10-06T16:00:11Z
- **提交信息**: [AMD] ci: build the miles ROCm 10 MI30X image nightly (#41605)

Co-authored-by: Claude <noreply@anthropic.com>

### [e179358](https://github.com/sgl-project/sglang/commit/e17935820a47b69a6fc2fd2bd2f8ec388897f1cc)

- **作者**: Emil Bogomolov
- **时间**: 2026-10-06T15:31:31Z
- **提交信息**: [diffusion] fix: fix width/height silently dropped on multipart /v1/videos requests (#35108)

Co-authored-by: Emil Bogomolov <zetyquickly@googlemail.com>

### [2579875](https://github.com/sgl-project/sglang/commit/2579875b5d0dc59cf6bbf90d6ebc750d25148d3d)

- **作者**: WenhaoZhang
- **时间**: 2026-10-06T15:30:48Z
- **提交信息**: [diffusion] feat: support loading community ComfyUI-GGUF Qwen-Image-2.1 transformers (#42556)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [49bafb5](https://github.com/sgl-project/sglang/commit/49bafb58cd6eb3a4feff035ce33dd72bb73addfd)

- **作者**: Chunan Zeng
- **时间**: 2026-10-06T14:47:47Z
- **提交信息**: perf(mla): use native SATFINITE FP8 conversion in MLA KV/Q preparation (#42659)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [679d285](https://github.com/sgl-project/sglang/commit/679d2851ba28a1c5d85efa116faab9f0087bd4d8)

- **作者**: Xiaoshuai Zhang
- **时间**: 2026-10-06T14:15:14Z
- **提交信息**: fix(mimo-vl): keep multimodal features when capturing aux hidden states and correct vision preprocessing (#40888)

Co-authored-by: jet <dev@jetd.one>

### [16a23a6](https://github.com/sgl-project/sglang/commit/16a23a672b0688c415fa81b056e24bf7b7db320d)

- **作者**: Mick
- **时间**: 2026-10-06T14:13:29Z
- **提交信息**: [diffusion] model: support Kandinsky 6 (#42743)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Lev Novitskiy <57654885+leffff@users.noreply.github.com>
Co-authored-by: Kirill <kykozlov@gmail.com>
Co-authored-by: Artem Borisov <divotionchannel@gmail.com>

### [730f1f3](https://github.com/sgl-project/sglang/commit/730f1f3e5be9c781f523f856fc39c18c2ad266d6)

- **作者**: DarkSharpness
- **时间**: 2026-10-06T13:01:42Z
- **提交信息**: [DeepSeek-V4.1] Unify mHC into one state machine and drop medium-batch fusion variants (#42245)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: BBuf <1182563586@qq.com>

### [2a5f45d](https://github.com/sgl-project/sglang/commit/2a5f45d3d47879f5524194789fe0db61fe206671)

- **作者**: WenhaoZhang
- **时间**: 2026-10-06T12:43:08Z
- **提交信息**: [diffusion] fix: skip zero blocks when hashing large conditioning inputs (#42748)

### [ba94488](https://github.com/sgl-project/sglang/commit/ba94488b42a75898605eccc9da3131e56122d3c1)

- **作者**: WMC
- **时间**: 2026-10-06T12:20:58Z
- **提交信息**: [diffusion] feat: default Qwen-Image 2.1 to VAE tiling on gfx1151 (#41655)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [1291f31](https://github.com/sgl-project/sglang/commit/1291f3175d3b7614821884e9653985fcd3c3dae8)

- **作者**: Shangming Cai
- **时间**: 2026-10-06T11:10:26Z
- **提交信息**: [rust-processor] Fix chat-template precedence wording in the processor README (#42756)

### [28525b4](https://github.com/sgl-project/sglang/commit/28525b43c4af99c3d0223ba95b8165e73834ca16)

- **作者**: Shangming Cai
- **时间**: 2026-10-06T11:07:37Z
- **提交信息**: [sgl-router] Document and reject a zero request timeout (#42751)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [cf19ae6](https://github.com/sgl-project/sglang/commit/cf19ae6d041eb37d6d52c24b651c8569f56e70f0)

- **作者**: Kan Wu
- **时间**: 2026-10-06T10:59:02Z
- **提交信息**: [rust-processor] Split sglang-processor into tokenizer, render and parser (#42662)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [45db430](https://github.com/sgl-project/sglang/commit/45db4305303a106988a65a1855a5183054c3837d)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-06T10:57:52Z
- **提交信息**: [DSA] Fix pooled page table refresh for target verify CUDA graph replay (#42750)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [2167cf9](https://github.com/sgl-project/sglang/commit/2167cf90c3263d1fd0d32a7b44c1aee8f85a5dbe)

- **作者**: Kan Wu
- **时间**: 2026-10-06T10:35:11Z
- **提交信息**: [sgl-router] Bound streaming time-to-headers by --request-timeout-secs (retry 5/5) (#42632)

Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f3b5a28](https://github.com/sgl-project/sglang/commit/f3b5a28f4315767261d439baf4705f2049d8871f)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-10-06T09:22:53Z
- **提交信息**: [AMD] M3-mxfp8 Nightly Test Update (#42605)

### [542adda](https://github.com/sgl-project/sglang/commit/542addad32e39d07605c81b3a650f58f26c62f02)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-10-06T09:22:01Z
- **提交信息**: [AMD] M3-MXFP4 Nightly Test (#42602)

### [662879e](https://github.com/sgl-project/sglang/commit/662879e4952190b8649196615e26741448102337)

- **作者**: Kan Wu
- **时间**: 2026-10-06T09:06:45Z
- **提交信息**: [sgl-router] Back off between retry attempts (retry 4/5) (#42631)

Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [b563bbd](https://github.com/sgl-project/sglang/commit/b563bbd59784a660f3de9a3cadd6f0e1bd24af35)

- **作者**: Gawr Gura 0721
- **时间**: 2026-10-06T08:58:02Z
- **提交信息**: [Fix] Don't let a failed deep_ep import-time check kill servers that never use DeepEP (#40671)

### [e49e971](https://github.com/sgl-project/sglang/commit/e49e9711317618218289e479660e28cbef555514)

- **作者**: Hongsheng Jin
- **时间**: 2026-10-06T08:40:35Z
- **提交信息**: [mem_cache] Keep prefix_indices current for chunked requests kept out of the tree (#42467)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [bb4d0a1](https://github.com/sgl-project/sglang/commit/bb4d0a13c128400fcbed97096e3d823f33563084)

- **作者**: Kan Wu
- **时间**: 2026-10-06T08:28:52Z
- **提交信息**: [sgl-router] Retry failed dispatches on another worker (retry 3/5) (#42630)

Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kan Wu <kan.wu@radixark.ai>

### [1be3013](https://github.com/sgl-project/sglang/commit/1be30131184a797ff433d07ba4a44441bb06d32f)

- **作者**: Jzz1943
- **时间**: 2026-10-06T08:15:21Z
- **提交信息**: [diffusion] feat: support Ideogram TurboTime LoRA (#30487)

### [0134519](https://github.com/sgl-project/sglang/commit/01345197afcaf83f7faf2db9969672f92f128c3a)

- **作者**: Max Kong
- **时间**: 2026-10-06T08:14:39Z
- **提交信息**: [diffusion] chore: harden OpenAI upload filename handling (#17270)

=

### [d0494af](https://github.com/sgl-project/sglang/commit/d0494af08bdb63c46755d62ee8df35b9d78e807c)

- **作者**: Jinbao Chen
- **时间**: 2026-10-06T08:05:17Z
- **提交信息**: [diffusion] security: pin multimodal-gen ZMQ scheduler ingress to loopback on wildcard --host (#36854)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [c7f3ae1](https://github.com/sgl-project/sglang/commit/c7f3ae1dd598600a28e21d973242601826e5dc0f)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-06T07:59:38Z
- **提交信息**: [mem_cache] Hold a request's tree lock as one `TreeLock` (#42686)

### [05340e9](https://github.com/sgl-project/sglang/commit/05340e9ecb965921ac9112ba2223c78a6e6de685)

- **作者**: Kan Wu
- **时间**: 2026-10-06T07:24:02Z
- **提交信息**: [sgl-router] Make one request dispatchable more than once (retry 2/5) (#42629)

Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c683190](https://github.com/sgl-project/sglang/commit/c683190b40f137f91f8d82fdf7df64ea028f888b)

- **作者**: Sasha Sidorov
- **时间**: 2026-10-06T07:17:12Z
- **提交信息**: [PD] Wait for prefill completion before Mooncake early KV transfer (#41395)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [8c273d6](https://github.com/sgl-project/sglang/commit/8c273d68139a1230909bc3ff636740e6e21bb425)

- **作者**: Kan Wu
- **时间**: 2026-10-06T07:10:51Z
- **提交信息**: [sgl-router] Let selection skip workers a request already failed on (retry 1/5) (#42628)

Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1289
- **最后更新**: 2026-10-07T00:36:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93294
- **最后更新**: 2026-10-07T01:35:22Z

## 提交统计

- **昨日提交总数**: 43
- **提交者数量**: 41
- **主要提交者**: eky-amd, roikoren755, Jiangyun Zhu

## AI分析总结

# vLLM 仓库近期提交总结（43 条）

## 1. 主要更新类型分布

- **性能优化**（约 35%）：MoE、KV 缓存、量化、稀疏注意力
- **Bug 修复**（约 30%）：投机解码、前端 API、KV 卸载等
- **功能新增**（约 15%）：新模型架构、新 KV 缓存后端、评测工具
- **CI/构建**（约 12%）：依赖升级、构建迁移、CI 稳定性
- **文档/杂项**（约 8%）：安全说明、贡献指南、代码风格

## 2. 关键变更点与项目方向的关系

项目核心目标是"为所有人提供简单、快速、低成本的 LLM 服务"，本次提交主要围绕以下方向展开：

- **推理性能持续压榨**：DeepGEMM FP8 MoE 跳过填充计算、NCCL 对称 reduce-scatter 消除暂存、HiSparse 按请求缓存驻留信息、MTP 投机解码去除冗余元数据重建、flashMLA 稀疏注意力的 Q 头填充优化。这些直接提升吞吐量和延迟表现。
- **量化与 KV 缓存多样化**：新增 UltraQuant 4-bit KV 缓存（AMD 平台）、GLM 默认切换 FP8 KV 缓存（E2E 吞吐提升 2.3%~5.5%）、MXFP8→FP8 PTPC 在线层重量化 API、Humming 量化后端优先于 Marlin（SM90）。
- **投机解码链路完善**（Model Runner V2）：Ngram GPU 投机解码器实现及 Bug 修复、异构词表草稿模型回退 V1、缓存可预测性修复。
- **多硬件生态**：ROCm 方向大量投入——MLA dual RMSNorm + FP8 分组量化融合（DeepSeek-R1）、RDNA3/3.5/4 上的分段注意力后端、gfx11 W4A16 步长填充优化。
- **模型架构扩展**：EmbeddingGemma2 多模态池化架构、LongCat-Flash MLA 归一化加载、Mamba2 内部预填充检查点、DiffusionGemma 修复。

## 3. 对项目的影响与潜在意义

- **吞吐与成本**：多条性能提交直接服务于"低成本"目标，尤其是 MoE、KV 缓存和量化路径的优化，对大规模部署的 TCO 有明显影响。
- **平台覆盖扩展**：AMD（ROCm）和 CPU 平台的持续投入，强化了 vLLM 的多硬件异构服务能力。
- **稳定性与正确性**：FlashInfer 自动调优缓存死锁修复、投机解码相关 Bug 修复，提升了生产环境可靠性。
- **开发者体验**：gsm8k 评测 CLI、vllm-bench Mooncake 风格时间序列回放、Rust 前端工具函数透传，完善了评测和调试生态。
- **安全与合规**：文档明确声明多租户共享同一服务器不提供隔离，为部署方提供了重要的安全边界认知。

## 4. 值得关注的技术点

- **DeepGEMM 构建迁移**：从 pybind 迁移到 TORCH_LIBRARY (abi3)，简化依赖链并提升跨版本兼容性。
- **FlashInfer 调优缓存按 rank 持久化**：解决 rank-0-only 命中导致的分布式死锁，是典型的分布式缓存一致性问题修复。
- **FlashMLA 稀疏注意力的 Q 头填充策略调整**（128→64）：对特定硬件内存布局的精细优化。
- **多条提交出现 AI 辅助开发署名**（Claude、Codex、Kimi 等），反映 AI 编码已深度融入 vLLM 的日常开发流程。

## 5. 对项目发展的整体影响

这些提交表明 vLLM 正处于**性能深挖、量化普及、硬件多元化和工程成熟化**的加速阶段。MoE 与量化路径的持续优化巩固了其在主流 LLM 服务场景中的性能优势；ROCm、CPU、Rust 前端等多线并进降低了单一硬件依赖；投机解码 V1/V2 双线演进和评测工具链的完善，为后续更激进的架构革新奠定了基础。整体而言，这批提交在不偏离"人人可用的高效 LLM 服务"核心愿景的前提下，系统性地提升了性能上限、生态广度和工程可靠性。

## 详细提交记录

### [5ab4e44](https://github.com/vllm-project/vllm/commit/5ab4e4445bcbe2bf07351b82d1af160234c32273)

- **作者**: Tyler Michael Smith
- **时间**: 2026-10-06T23:49:57Z
- **提交信息**: [Perf][MoE] Skip padded work in block-FP8 DeepGEMM experts (#59128)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b6d8e8a](https://github.com/vllm-project/vllm/commit/b6d8e8afd985f5711eee68e343d2ce908d166488)

- **作者**: Cheese Cake
- **时间**: 2026-10-06T22:02:04Z
- **提交信息**: [Bugfix][MRV2][Spec Decode] Accept num_speculative_tokens in NgramGPUSpeculator.propose (#60300)

Signed-off-by: cheesecake <farzanaman99@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ae19af8](https://github.com/vllm-project/vllm/commit/ae19af883a3ab7baa8a42ba0a6ef0752e4120b33)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-06T21:50:10Z
- **提交信息**: [CI] Require transformers 5.19 for the EmbeddingGemma2 registry test (#60295)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [385d86a](https://github.com/vllm-project/vllm/commit/385d86a6cf6f05051899b53d83ec55c63cccb379)

- **作者**: aditi-amd
- **时间**: 2026-10-06T20:42:52Z
- **提交信息**: [Attention] Add UltraQuant 4-bit KV cache backend (FlyDSL D=256) (#57057)

Signed-off-by: Aditi Rana <aditi.rana@amd.com>

### [819852d](https://github.com/vllm-project/vllm/commit/819852df6bffb873304c421f7091b7f8133fa87b)

- **作者**: PatchyTIS
- **时间**: 2026-10-06T20:32:59Z
- **提交信息**: [ModelRunner V2] Speculative Decoding NGram GPU Implementations (#40704)

Signed-off-by: PatchouliTaisa <patchychen@tencent.com>
Signed-off-by: PatchouliTaisa <pyramkar@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Signed-off-by: Xuanan Chen <xuananchenc@nvidia.com>
Co-authored-by: PatchouliTaisa <patchychen@tencent.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Xuanan Chen <xuananchenc@nvidia.com>
Co-authored-by: Giancarlo Delfin <32987265+TheEpicDolphin@users.noreply.github.com>

### [dac35c5](https://github.com/vllm-project/vllm/commit/dac35c5b66efb0ddabb6f67af5d1817b2c74edc0)

- **作者**: Benjamin Chislett
- **时间**: 2026-10-06T20:13:44Z
- **提交信息**: [Misc] Add chat-completion options to gsm8k_eval.py CLI (#60114)

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e43db1f](https://github.com/vllm-project/vllm/commit/e43db1f5e2eb7ca16fc284a810c548a0d3d44b14)

- **作者**: PatrykSaffer
- **时间**: 2026-10-06T20:03:05Z
- **提交信息**: Pad to 64 not 128 Q heads in flashMLA sparse (#60029)

Signed-off-by: Patryk Saffer <patryk.saffer@mistral.ai>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [d1f3d8b](https://github.com/vllm-project/vllm/commit/d1f3d8b87083a95f914c674c477796950e2ba5fe)

- **作者**: Jinzhen Lin
- **时间**: 2026-10-06T19:31:35Z
- **提交信息**: [Quantization] Prefer Humming before Marlin backends on SM90 (#56997)

Signed-off-by: jinzhen.ljz <jinzhen.ljz@antgroup.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bb87d22](https://github.com/vllm-project/vllm/commit/bb87d227d4b964abb2a966cdf9194f3d376d9bbe)

- **作者**: Roger Wang
- **时间**: 2026-10-06T19:10:00Z
- **提交信息**: [Bugfix][Model] Fix mypy safe-super error in EmbeddingGemma2Model (#60280)

Signed-off-by: Roger Wang <hey@rogerw.io>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [e37e51d](https://github.com/vllm-project/vllm/commit/e37e51dd246cf421c554e7d6f53e178e3fd29085)

- **作者**: Cameron Quilici
- **时间**: 2026-10-06T18:52:05Z
- **提交信息**: [Metrics] Expose cached prompt tokens by cache tier (#56318)

Signed-off-by: Cam Quilici <cjquilici@gmail.com>
Signed-off-by: Cam Quilici <cameron@semianalysis.com>
Co-authored-by: Cam Quilici <cameron@semianalysis.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [ad0f67a](https://github.com/vllm-project/vllm/commit/ad0f67a7ec8f0393c8b4ae50a2a0e66672db372f)

- **作者**: Nishant Revur
- **时间**: 2026-10-06T18:03:44Z
- **提交信息**: [Bugfix][Spec Decode] Keep heterogeneous-vocab draft models on Model Runner V1 (#59541)

Signed-off-by: Nishant Revur <kumrfni@amazon.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3403e0f](https://github.com/vllm-project/vllm/commit/3403e0f176efb90b0d92cc0ff1d350f092ed9e9f)

- **作者**: Madhav Jivrajani
- **时间**: 2026-10-06T17:51:01Z
- **提交信息**: [Bugfix] Persist FlashInfer autotune cache per rank to fix the rank-0-only cache-hit deadlock (#57635)

Signed-off-by: Madhav Jivrajani <madhav.jiv@gmail.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [02b8391](https://github.com/vllm-project/vllm/commit/02b83919aa2eece2fd7efb8d8c906e4db9a02ff4)

- **作者**: Luciano Martins
- **时间**: 2026-10-06T17:43:38Z
- **提交信息**: [Model] Support EmbeddingGemma2 multimodal pooling architecture (#60254)

Signed-off-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Luciano Martins <lucianommartins@users.noreply.github.com>

### [7b665f7](https://github.com/vllm-project/vllm/commit/7b665f7a581b8cfb33974675174a9b0f29ec57e2)

- **作者**: Yin Li
- **时间**: 2026-10-06T17:22:47Z
- **提交信息**: [Frontend] Integer token IDs for generate output logprobs (GenerateLogProbs) (#58181)

Signed-off-by: Yin Li <kevinli.ai.work@gmail.com>
Co-authored-by: Yin Li <kevinli.ai.work@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e82b800](https://github.com/vllm-project/vllm/commit/e82b80099acba001693af29361a0255a7b171b8a)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-06T17:04:55Z
- **提交信息**: [Perf][HiSparse] Cache per-request residency instead of rescanning every page each step (#60083)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fba31f3](https://github.com/vllm-project/vllm/commit/fba31f31a9d14a8fbe52e4246ba5b3fcd1a9ba63)

- **作者**: Wentao Ye
- **时间**: 2026-10-06T16:54:20Z
- **提交信息**: [GLM5.3 Perf] Switch to fp8 kv cache by default for GLM, 2.3%~5.5% E2E Throughput Improvement (#60140)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [f8d92ca](https://github.com/vllm-project/vllm/commit/f8d92cae410a56822bc5a89ccb96012b44bea222)

- **作者**: fxmarty-amd
- **时间**: 2026-10-06T16:38:18Z
- **提交信息**: [Quantization] Layer re-quantization for linear layers through online quantization API (MXFP8 -> FP8 PTPC showcase) (#55684)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Signed-off-by: Tan Pin Siang <tanpinsiang@gmail.com>
Co-authored-by: vllmellm <vllm.ellm@embeddedllm.com>
Co-authored-by: Tan Pin Siang <tanpinsiang@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [29f955c](https://github.com/vllm-project/vllm/commit/29f955cce0e8713e22d50d521dc0589f2c4bd319)

- **作者**: eky-amd
- **时间**: 2026-10-06T16:26:38Z
- **提交信息**: [ROCm] Fuse MLA dual RMSNorm + FP8 group quant for DeepSeek-R1 (#54857)

Signed-off-by: Ethan Ky <ethan.ky@amd.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [4516896](https://github.com/vllm-project/vllm/commit/451689662688bfb3152f5c2218b70c24b12c5852)

- **作者**: stefankoncarevic
- **时间**: 2026-10-06T16:23:37Z
- **提交信息**: [CI/Build] Warm the DP engines before measuring load balance in test_load (#60241)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [fcf53d2](https://github.com/vllm-project/vllm/commit/fcf53d240c73d44bd9e3fe62996f8a2f1169fee9)

- **作者**: Giancarlo Delfin
- **时间**: 2026-10-06T16:17:30Z
- **提交信息**: [Spec Decode] Remove eager metadata rebuild during MTP fused multi-step decode (#58463)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [4ea0c28](https://github.com/vllm-project/vllm/commit/4ea0c28bc4ba28968b8386728ed64235fbe1ac79)

- **作者**: SeongJun Lee
- **时间**: 2026-10-06T15:55:27Z
- **提交信息**: [Bugfix] Warn only on per-request do_normalize/do_rescale overrides (#60240)

Signed-off-by: lesj0610 <lesj0610@gmail.com>

### [aad4579](https://github.com/vllm-project/vllm/commit/aad4579bbe56ce87a7799d31df57a19756d6f549)

- **作者**: Jeff-Tseng-dev
- **时间**: 2026-10-06T15:44:56Z
- **提交信息**: Upgrade tpu-inference to v0.31.0 (#60190)

### [cc73cca](https://github.com/vllm-project/vllm/commit/cc73cca9c88bc19a368a910a630e9c5caec61ac3)

- **作者**: Chris Leonard
- **时间**: 2026-10-06T15:39:04Z
- **提交信息**: [Build] Migrate vendored DeepGEMM from pybind to TORCH_LIBRARY (abi3) (#48962)

Signed-off-by: Chris Leonard <chleonar@redhat.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [cbe1f97](https://github.com/vllm-project/vllm/commit/cbe1f9740d0ae7f6eb82bd752a984c7db8ab85fe)

- **作者**: ovidiusm
- **时间**: 2026-10-06T14:55:03Z
- **提交信息**: [NIXL] Bump NIXL version to 1.5.0 (#56907)

Signed-off-by: Ovidiu Mara <ovidium@nvidia.com>

### [0719975](https://github.com/vllm-project/vllm/commit/0719975ceeeab568cbd3a3e88a5c790a91b56709)

- **作者**: Bugen Zhao
- **时间**: 2026-10-06T14:53:17Z
- **提交信息**: [CI][Rust Frontend] Pass `--locked` to cargo binstall (#60182)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8bd7737](https://github.com/vllm-project/vllm/commit/8bd7737a03bfcd4a1bca008f9f0e94729f8d67dc)

- **作者**: Sunny Rangnani
- **时间**: 2026-10-06T14:39:59Z
- **提交信息**: [Docs] Clarify that vLLM does not isolate tenants sharing a server (#59811)

Signed-off-by: SunnyR <sunny.rangnani@chainguard.dev>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Juan Pérez de Algaba <124347725+jperezdealgaba@users.noreply.github.com>

### [4a99ca4](https://github.com/vllm-project/vllm/commit/4a99ca40d647a0b5618315fe44fcb85554ddcb53)

- **作者**: Samuel Nordmann
- **时间**: 2026-10-06T14:37:01Z
- **提交信息**: [Perf][MoE] Eliminate staging from NCCL symmetric reduce-scatter (#49194)

Signed-off-by: samnordmann <snordmann@nvidia.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [bf049dd](https://github.com/vllm-project/vllm/commit/bf049ddb8f4f305cdb01be63f89743f83b397228)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-06T14:12:18Z
- **提交信息**: [Docs] Run pr-checklist before opening a PR (#60235)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b267fe4](https://github.com/vllm-project/vllm/commit/b267fe488102eb26555d553a005127b4a523ff4b)

- **作者**: Matthias Gehre
- **时间**: 2026-10-06T13:22:33Z
- **提交信息**: [ROCm][Perf] W4A16: pad gfx11 weight and activation strides (#56301)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>

### [049507a](https://github.com/vllm-project/vllm/commit/049507aa76200090f8bc6ca4e48ab0e09f2f0d29)

- **作者**: Artem Perevedentsev
- **时间**: 2026-10-06T13:01:04Z
- **提交信息**: [Bugfix][Structured Output] Flag multi-branch allOf as unsupported for xgrammar (#59061)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Shashank Varma <324153016+shashankvarma499@users.noreply.github.com>

### [1a86733](https://github.com/vllm-project/vllm/commit/1a86733c7b02f1cd5b035e64b9af5ce23e726484)

- **作者**: Roy Wang
- **时间**: 2026-10-06T12:40:10Z
- **提交信息**: [Docs] Add model recipes skill (#57786)

### [3faf214](https://github.com/vllm-project/vllm/commit/3faf2140516d52dbaf143ab82402bf4681abc7c3)

- **作者**: Rodrigo Garcia
- **时间**: 2026-10-06T12:39:35Z
- **提交信息**: [vllm-bench, feature] Added support for Mooncake-style, timed-traces replay. (#55937)

### [2538510](https://github.com/vllm-project/vllm/commit/25385102fe99708f831eedafeb1b03f51287c95a)

- **作者**: Sherif Waly
- **时间**: 2026-10-06T12:25:08Z
- **提交信息**: [Bugfix][KV Offload] Honor speculative cacheability in SimpleCPU (#60071)

Signed-off-by: Sherif Waly <sherif.waly@mistral.ai>

### [3e18218](https://github.com/vllm-project/vllm/commit/3e182185aa5d143b0e69c44607f58a0cc55f3971)

- **作者**: Wentao Ye
- **时间**: 2026-10-06T12:15:12Z
- **提交信息**: [Deprecation] Deprecate sonet dataset as scheduled (#60129)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [3313825](https://github.com/vllm-project/vllm/commit/3313825983dad6fd4291986e7f9ba647c059d1ff)

- **作者**: Mia Ojeda
- **时间**: 2026-10-06T11:25:51Z
- **提交信息**: [Bugfix][DiffusionGemma] Read the causal mask as int32 and compile the sample step (#59992)

Signed-off-by: ojeda-e <eojeda@league.com>

### [09e0ce3](https://github.com/vllm-project/vllm/commit/09e0ce3d82f404e842fdfc9ab34ba27e76f95a16)

- **作者**: Shimi Bandiel
- **时间**: 2026-10-06T10:46:24Z
- **提交信息**: [Bugfix][Frontend] Apply model-default reasoning parser in GPU-less render server (#54835)

Signed-off-by: Shimi Bandiel <shimib@google.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [68088ed](https://github.com/vllm-project/vllm/commit/68088ed3927e91bce8918db78f2efd9e644a4134)

- **作者**: zhangchengzhucufe-dev
- **时间**: 2026-10-06T10:19:54Z
- **提交信息**: Fix grammar in `BlockPool.reset_prefix_cache` docstring: "to invalid" → "to invalidate" (#59886)

Signed-off-by: zhangchengzhucufe-dev <zhangchengzhucufe@gmail.com>

### [888074b](https://github.com/vllm-project/vllm/commit/888074b42ded93c0d3aac083bbf281daeec963e4)

- **作者**: Louie Tsai
- **时间**: 2026-10-06T10:15:40Z
- **提交信息**: [CPU][Recipes] Detect model head constraints for automatic tensor parallel selection in vLLM Recipes Tool (#60170)

Signed-off-by: louie-tsai <louie.tsai@intel.com>

### [6bbad6a](https://github.com/vllm-project/vllm/commit/6bbad6acdffd58b63037829f9fe27b92c6650071)

- **作者**: Bugen Zhao
- **时间**: 2026-10-06T10:00:15Z
- **提交信息**: [Rust Frontend] Pass tool defer_loading through to chat templates (#60203)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [31e2443](https://github.com/vllm-project/vllm/commit/31e2443c90542a33a4a4a293ea7186fba2796c67)

- **作者**: aoshen02
- **时间**: 2026-10-06T08:47:02Z
- **提交信息**: [Model] LongCat-Flash: scale MLA norms while loading and drop the post-load sweep (#60080)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e11962f](https://github.com/vllm-project/vllm/commit/e11962fc1ce542c725dacda6f641daed8d54337f)

- **作者**: roikoren755
- **时间**: 2026-10-06T07:53:51Z
- **提交信息**: [Feat][Mamba2] Enable internal prefill checkpoints (#57329)

Signed-off-by: Roi Koren <roik@nvidia.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

### [edfccc9](https://github.com/vllm-project/vllm/commit/edfccc946925a8439e27abd76da8d1a640d1a1b7)

- **作者**: big_yellow_duck
- **时间**: 2026-10-06T07:53:47Z
- **提交信息**: [ROCM][Perf] Add ROCM_SEGMENTED_ATTN attention-backend works across RDNA3/3.5/4 (#59132)

Signed-off-by: root <jeffaw99@hotmail.com>
Signed-off-by: big-yellow-duck <jeffaw99@hotmail.com>
Co-authored-by: Tan Pin Siang <1716735+tanpinsiang@users.noreply.github.com>
Co-authored-by: vllmellm <190700713+vllmellm@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [15c1cc1](https://github.com/vllm-project/vllm/commit/15c1cc12ac50c1fb36fd92978c14ad2e2f865055)

- **作者**: LostFox11
- **时间**: 2026-10-06T07:44:57Z
- **提交信息**: [Bugfix][EPLB] Use group-local ranks for torch P2P transfers (#55804)

Signed-off-by: LostFox11 <wangziyue17@huawei.com>
Co-authored-by: LostFox11 <wangziyue17@huawei.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: YangShuai52 <178856220+YangShuai52@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-07
**监控日期**: 2026-10-06
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7060
- **最后更新**: 2026-10-07T01:30:05Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 7
- **主要提交者**: Dong1017, BeatSeat, Sy03

## AI分析总结

## 提交分析总结（vllm-omni，共 11 条）

### 1. 主要更新类型
本次提交以**性能优化**与**模型扩展**为主，辅以 CI/测试基础设施建设、Bug 修复和前端功能增强：
- 性能优化：2 条
- 模型/功能新增：3 条（MOSS、MiniMax-H3、Kandinsky6）
- Core API 扩展：1 条（实时会话接口）
- 前端（ComfyUI）：1 条
- Bug 修复：1 条
- CI/Build（ROCm 覆盖率）：3 条

### 2. 关键变更点与项目方向的关系
- **[Core] 泛化的基于轮次的 /v1/realtime 实现**：这是核心 API 层的重构性增强，将实时多模态交互（音频/视频流）抽象为更通用的会话模型，直接服务项目"omni-modality serving"的核心定位，是本轮提交中最具战略意义的一条。
- **[Perf] MiniCPM-o Stage 0 流式编码器 CUDA Graph 化 + 候选采样**：针对音频/视觉编码器启用 CUDA Graph，减少流式推理中的内核启动开销，契合项目"fast"的目标。
- **[Perf] AdaLayerNorm Triton 融合**：将 CUDA eager 路径中的归一化操作融合为 Triton kernel，降低内存带宽消耗，属于典型推理热路径优化。
- **[Model] 新增 Kandinsky6、MOSS 默认切至自适应 CUDA MRV2 + MPS**：扩展可服务模型矩阵，体现"easy and cheap"——通过 MPS（多处理流）等机制提升单卡并发。
- **MiniMax-H3 相关（ComfyUI latent-mask 编辑、服务端解析原始视频 mask）**：在前端与服务端两端打通 mask 编辑工作流，说明项目正在把 omni 模型能力向实际创作场景（ComfyUI 生态）延伸。
- **[CI][ROCm] 三处覆盖率提升（Pi0.5、HunyuanImage3、Cosmos3）**：将更多 omni 模型（含音频/图像模型）纳入 AMD ROCm 夜间测试，说明项目对多后端（NVIDIA/AMD）兼容性的承诺在持续兑现。

### 3. 对项目的影响和潜在意义
- **稳定性与可维护性提升**：Bug 修复（弃用 Config 类迁移）和 CI 覆盖面扩大，降低了回归风险。
- **多模态推理链路整体提速**：编码器 CUDA Graph + Triton 融合叠加，有望显著改善流式音频/视觉场景的端到端延迟。
- **生态位扩展**：ComfyUI 扩展和更多模型支持，使 vllm-omni 从纯推理引擎向"可接入创作/推理工作流"演进。
- **硬件包容性**：ROCm 夜测覆盖是面向 AMD 用户的重要信任信号，降低供应商锁定。

### 4. 值得关注的技术点
- `/v1/realtime` 接口设计如何抽象多轮 omni 会话（值得跟踪后续迭代）。
- MiniCPM-o 流式编码器中 CUDA Graph 与动态输入长度的调和方式。
- AdaLayerNorm 在 Triton 中的数值稳定性与精度验证。
- MOSS 自适应 MRV2 + MPS 的调度策略（何时切换、收益边界）。
- MiniMax-H3 服务端 mask 网格解析是否成为 omni 模型的标准 mask 约定。

### 5. 对项目发展的整体影响
结合 README"Easy, fast, and cheap omni-modality model serving for everyone"的愿景，这批提交从三个维度推进目标：**fast**（CUDA Graph、Triton 融合）、**easy**（realtime 接口标准化、ComfyUI 扩展、新模型开箱可用）与 **everyone**（ROCm/AMD 覆盖、MPS 并发降本）。项目正从"支持多模态模型推理"走向"提供标准化、低延迟、多硬件可用的 omni 服务层"，核心 API 的泛化与生态接入（ComfyUI）是关键拐点，后续值得关注的是这些能力在文档与示例中的沉淀，以及实际部署场景下的性能基准数据。

## 详细提交记录

### [e61cd42](https://github.com/vllm-project/vllm-omni/commit/e61cd4290f3b139298d9a5153e5d729239217461)

- **作者**: haic0
- **时间**: 2026-10-06T18:05:14Z
- **提交信息**: [CI/Build][ROCm] Move Pi0.5 CPU coverage to AMD nightly (#8559)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [a0d9152](https://github.com/vllm-project/vllm-omni/commit/a0d915254b4815b085d6d713de73e3ea6c76a0be)

- **作者**: haic0
- **时间**: 2026-10-06T16:54:27Z
- **提交信息**: [CI][ROCm] Add and stabilize HunyuanImage3 nightly coverage (#7934)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: akshatvishu <akshatnayak197@gmail.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: akshatvishu <akshatnayak197@gmail.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [bad88bc](https://github.com/vllm-project/vllm-omni/commit/bad88bca2559e8a54cca09f94e75aa07d69461bb)

- **作者**: chen hongwei
- **时间**: 2026-10-06T16:32:40Z
- **提交信息**: [Frontend] MiniMax-H3: Add latent-mask editing to the ComfyUI extension (#7575)

Signed-off-by: chen hongwei <1792043268@qq.com>
Signed-off-by: Wang Zhipeng <wangzhipeng628@gmail.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Wang Zhipeng <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7be49aa](https://github.com/vllm-project/vllm-omni/commit/7be49aa0ce95810a3b78fd6317f3c374bdd4422d)

- **作者**: Sy03
- **时间**: 2026-10-06T15:20:46Z
- **提交信息**: [Model] Default MOSS Local 1.5 to adaptive CUDA MRV2 with MPS (#8438)

Signed-off-by: Sy03 <1370724210@qq.com>

### [ee9ab9e](https://github.com/vllm-project/vllm-omni/commit/ee9ab9ea88a180455e089afff1febd136c1cce14)

- **作者**: Dong1017
- **时间**: 2026-10-06T15:11:45Z
- **提交信息**: [Perf] Fuse AdaLayerNorm CUDA eager path with Triton (#8231)

Signed-off-by: GUOGUO <xwdong1998@163.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [182b77d](https://github.com/vllm-project/vllm-omni/commit/182b77da4cf0a3d76b7638ccc22754d82222a9d3)

- **作者**: BeatSeat
- **时间**: 2026-10-06T14:53:03Z
- **提交信息**: [Perf][MiniCPM-o] Stage 0 streaming audio/vision encoder CUDA graphs and candidate sampling (#8430)

Signed-off-by: BeatSeat <wendavid552@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [65699fe](https://github.com/vllm-project/vllm-omni/commit/65699fe94c355e235f1acabddd866bce0bba1c02)

- **作者**: Nick Cao
- **时间**: 2026-10-06T14:07:31Z
- **提交信息**: [Core] Generalized turn-based /v1/realtime implementation (#8339)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [25fb257](https://github.com/vllm-project/vllm-omni/commit/25fb257667abb397eab10b71ec7de7b35b42e3a3)

- **作者**: chen hongwei
- **时间**: 2026-10-06T12:46:35Z
- **提交信息**: [Model] MiniMax-H3: accept raw video masks and resolve the latent grid server-side (#7947)

Signed-off-by: chen hongwei <1792043268@qq.com>
Signed-off-by: Wang Zhipeng <wangzhipeng628@gmail.com>
Co-authored-by: Wang Zhipeng <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0677064](https://github.com/vllm-project/vllm-omni/commit/0677064b87aeb7a92fb855a8515e978eb419342e)

- **作者**: Nick Cao
- **时间**: 2026-10-06T12:42:09Z
- **提交信息**: [Bugfix] Migrate CreateAudio from deprecated class Config to ConfigDict (#5245)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [5f95115](https://github.com/vllm-project/vllm-omni/commit/5f95115e703ffe51e03e40ae23c78ff841c3335e)

- **作者**: Nikita Osterov
- **时间**: 2026-10-06T07:55:15Z
- **提交信息**: Kandinsky6 (#8537)

Signed-off-by: leffff <levnovitskiy@gmail.com>
Signed-off-by: Artem Borisov <divotionchannel@gmail.com>
Co-authored-by: leffff <levnovitskiy@gmail.com>
Co-authored-by: Artem Borisov <divotionchannel@gmail.com>

### [1f63e97](https://github.com/vllm-project/vllm-omni/commit/1f63e97a40505cecd7a532e4b789daa9d5e58e26)

- **作者**: haic0
- **时间**: 2026-10-06T07:18:44Z
- **提交信息**: [CI][ROCm] Add Cosmos3 nightly coverage (#7933)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

---
