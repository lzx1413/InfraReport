# GitHub Stars 合并报告 - 2026-10-04

**合并日期**: 2026-10-05
**监控日期**: 2026-10-04
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


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2232
- **最后更新**: 2026-10-04T09:21:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2877
- **最后更新**: 2026-10-04T02:27:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2282
- **最后更新**: 2026-10-04T18:25:32Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6545
- **最后更新**: 2026-10-04T23:56:54Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 2
- **主要提交者**: Akaash Parthasarathy, eigen

## AI分析总结

# FlashInfer 昨日提交综合分析

## 主要更新

昨日共 9 个提交，整体围绕 **CAKE 生成式 kernel 后端**的扩张与整合展开。一类为功能新增与性能优化，覆盖 MoE 算子（masked grouped FP8 DeepGEMM、MoE finalize allreduce fusion 重构、Rubin GenPhase 与量化 combine）、注意力与解码层（NVFP4 sparse MLA decode、selective state update headdim-64 推广、Kimi-K3 AttnRes mid-M 路由、MiniMax-H3 diffusion stage operators），以及 SM120 DeepSeek-V4 NVFP4 融合 RoPE+量化+分页插入的 cache 写入器。另一类为大型累积提交，将 DeepSeek-V4 稀疏 MLA Cake 后端在 SM100/SM103 上第 7–17 轮优化以单一提交落到主线 #5920 布局路径，取代此前分散的 stacked PR 与 fork 分支。

## 关键变更

- **内核源码再生成**：以 Cake round-17 内核树经导出器 #5920 布局路径整体重新生成 `cake_dsv4` 源码（覆盖 sm_100a 与 sm_103a），替换旧源；host 侧按主线重新表达，测试移植到合并结构。
- **单轮微优化示例**：FP8/H64 SWA 单遍 softmax 与 TMEM-alias 正确性修复（每行 -0.7~0.85µs）、cluster/宽分区 V4 gather 拥有权按 128-key tile 整块并在 DSMEM 上 f32 终端合并（-0.13~0.70µs）、loader warp 跳过填充 gather 行（最多 -1.6µs）。
- **量化全链路打通**：NVFP4/MXFP8/UE8M0 从 cache 写入、MoE GEMM 计算到 RoPE+量化融合实现闭环。
- **严格数值纪律**：所有轮次保证无精度级变化，以 NaN 污染位比对做全族 bit 级回归验证；#5970 明确给出相对误差上界（≤3.5e-3）。

## 项目影响

**性能层面**：多个算子在冷 L2 基准下超越或追平 SOTA baseline（Geomean ratio 0.853~0.867），cache 写入快 2–4 倍，直接提升 DeepSeek-V4、Kimi-K3、MiniMax-H3 等模型在 Blackwell 与 RTX 5090 上的解码吞吐。

**工程层面**：单一累积提交大幅减少维护面，统一代码路径、布局与测试结构，标志 Cake 后端从快速试错进入**主线收敛与稳定阶段**。生成代码 + 手写 dispatch binding、协议锁保证 ABI 稳定、per-(arch, cluster) JIT 注册表支持自适应编译，为复用奠定基础。

**生态层面**：API 采用 `backend="cake"` 显式切换、默认路径不变，向后兼容降低迁移风险；项目定位从"个别优化算子"向"完整推理算子后端矩阵"演进，同时频繁引用 vLLM issue 表明目标直指实际推理系统瓶颈。

## 技术关注点

- **SASS identity 验证**：#5870 重构时用 `cuobjdump -sass` 逐指令比对，确保 12 个 kernel 合并后二进制完全一致，是安全重构生成代码的标杆做法。
- **冷 L2 基准方法论**：CUPTI + L2 flush + 交错采样的严格设计，可复现性强。
- **Blackwell 特性利用**：TMEM 别名正确性、DSMEM 上 f32 终端合并、warp 级调度策略体现对架构延迟的深度理解。
- **代码生成管线**：外部内核 DSL/生成器（Cake exporter）与推理内核库（JIT 编译 + ABI 契约）的集成模式，可能是未来 kernel 开发的主流形态。

**潜在风险**：生成式 kernel 数量快速膨胀带来测试与维护成本上升，且对 driver 580.x 等硬件驱动版本强依赖，部署门槛有所提高。

## 详细提交记录

### [c11f8ba](https://github.com/flashinfer-ai/flashinfer/commit/c11f8ba94ecf4c5bcd764f73824b87dd4c4fa08d)

- **作者**: eigen
- **时间**: 2026-10-04T23:56:49Z
- **提交信息**: feat(cake_backend): generated backend="cake" for nvfp4_sparse_mla_decode on SM100 / SM103 (#5970)

## Summary

Adds `backend="cake"` to `flashinfer.mla.nvfp4_sparse_mla_decode`: a
generated-program implementation of the
same operator and tensor ABI as the hand-written `backend="cuda"` kernel
(#5717) for SM100 (B200 / GB200) and
SM103 (B300 / GB300). The default backend is unchanged.

- `flashinfer/experimental/nvfp4_sparse_mla_decode/cake_backend.py`:
planner-driven dispatcher (one thread-block
cluster of `C` CTAs per query token, `C` in {1, 2, 3, 4, 5, 6, 8},
planned from the device's one-wave cluster
capacity; `num_ctas_per_token` overrides), input checks shared with the
cuda backend.
- `flashinfer/experimental/nvfp4_sparse_mla_decode/cake_jit.py`:
per-(arch, cluster) JIT module registry for the
generated `sm_100a` / `sm_103a` sources under
`csrc/cake_nvfp4_sparse_mla_decode/`.
- `flashinfer/mla/_core.py`: `backend="cake"` dispatch; unknown backends
still raise.
- Tests parametrized over both backends (forced cluster sizes
{1,2,3,4,5,6,8}; 7 rejected); benchmark gains a
cake arm and `--cold-l2`; README documents the backend with the cold-L2
table below.

Numerics: exact on-chip E2M1 x E4M3 dequantization to f16, fp32
accumulation and softmax, f16 P; relative error
vs an fp32 reference <= 3.5e-3 on every tested row (max 3.46e-3 on
GB300, 3.31e-3 on B200; the cuda backend
reaches the same maxima on the same rows).

## Cold-L2 timing vs `backend="cuda"` (CUPTI, paired interleaved median,
same card)

Eager launches timed from CUPTI activity records with the L2 flushed
before every launch (100 ms warm-up and 1,000 ms per slot, six
interleaved slots per arm, pooled median), request-shaped indices, 16
heads. B200 (148 SMs): driver 580.82.07; GB300 (152 SMs): driver
580.159.03; torch 2.13.0a0 (CUDA 13.3) on both. Ratio = cake / cuda; `-`
marks a wave-boundary row that exists only on the other card's planner
table. Geomean ratio B200 0.853 (39 rows), GB300 0.867 (40 rows); worst
0.930 (B200, the P row T = 5 K = 1024) / 0.933 (GB300, the P row T = 5 K
= 1024); every gate row faster on both cards: True.

| row | T | topk | padding | B200 cuda us | B200 cake us | B200 ratio |
GB300 cuda us | GB300 cake us | GB300 ratio |
|---|---|---|---|---|---|---|---|---|---|
| P | 5 | 2048 | none | 13.34 | 12.26 | 0.918 | 12.70 | 11.55 | 0.909 |
| P | 10 | 2048 | none | 13.82 | 12.67 | 0.917 | 12.96 | 11.78 | 0.909 |
| P+W | 15 | 2048 | none | 14.43 | 13.18 | 0.914 | 13.34 | 12.16 | 0.911
|
| P | 20 | 2048 | none | 17.41 | 15.74 | 0.904 | 16.13 | 14.59 | 0.905 |
| P | 25 | 2048 | none | 19.78 | 17.73 | 0.896 | 18.11 | 16.29 | 0.899 |
| P | 30 | 2048 | none | 22.62 | 20.35 | 0.900 | 20.77 | 18.66 | 0.898 |
| P | 35 | 2048 | none | 28.64 | 24.22 | 0.846 | 20.99 | 18.88 | 0.899 |
| P | 40 | 2048 | none | 28.99 | 24.54 | 0.847 | 26.66 | 23.55 | 0.884 |
| P | 45 | 2048 | none | 29.34 | 24.83 | 0.846 | 26.78 | 23.71 | 0.885 |
| P | 5 | 1024 | none | 9.54 | 8.86 | 0.930 | 9.06 | 8.45 | 0.933 |
| P | 10 | 1024 | none | 9.98 | 9.22 | 0.923 | 9.38 | 8.67 | 0.925 |
| P | 15 | 1024 | none | 10.37 | 9.60 | 0.926 | 9.79 | 9.02 | 0.922 |
| P | 20 | 1024 | none | 12.42 | 11.26 | 0.907 | 11.62 | 10.59 | 0.912 |
| P | 25 | 1024 | none | 13.82 | 12.32 | 0.891 | 12.77 | 11.42 | 0.895 |
| P | 30 | 1024 | none | 14.78 | 13.22 | 0.894 | 13.70 | 12.26 | 0.895 |
| P | 35 | 1024 | none | 17.70 | 15.10 | 0.854 | 13.89 | 12.45 | 0.896 |
| P | 40 | 1024 | none | 18.02 | 15.36 | 0.853 | 16.64 | 14.72 | 0.885 |
| P | 45 | 1024 | none | 18.21 | 15.52 | 0.852 | 16.80 | 14.85 | 0.884 |
| P | 5 | 512 | none | 9.60 | 7.20 | 0.750 | 9.06 | 6.88 | 0.760 |
| P | 10 | 512 | none | 9.79 | 7.52 | 0.768 | 9.31 | 7.04 | 0.756 |
| P | 15 | 512 | none | 10.11 | 7.74 | 0.766 | 9.50 | 7.33 | 0.771 |
| P | 20 | 512 | none | 10.34 | 8.58 | 0.830 | 9.79 | 8.16 | 0.833 |
| P | 25 | 512 | none | 10.69 | 9.41 | 0.880 | 10.02 | 8.90 | 0.888 |
| P | 30 | 512 | none | 10.75 | 9.63 | 0.896 | 10.11 | 9.12 | 0.902 |
| P | 35 | 512 | none | 12.74 | 10.91 | 0.857 | 10.30 | 9.25 | 0.898 |
| P | 40 | 512 | none | 13.02 | 11.10 | 0.853 | 12.16 | 10.72 | 0.882 |
| P | 45 | 512 | none | 13.18 | 11.23 | 0.852 | 12.29 | 10.85 | 0.883 |
| W | 16 | 2048 | none | 17.15 | 15.39 | 0.897 | 15.94 | 14.40 | 0.904 |
| W | 22 | 2048 | none | 17.73 | 16.00 | 0.903 | - | - | - |
| W | 23 | 2048 | none | 19.55 | 17.57 | 0.899 | 16.32 | 14.82 | 0.908 |
| W | 24 | 2048 | none | - | - | - | 18.08 | 16.26 | 0.899 |
| W | 26 | 2048 | none | 19.94 | 17.89 | 0.897 | - | - | - |
| W | 27 | 2048 | none | 22.30 | 20.10 | 0.901 | - | - | - |
| W | 28 | 2048 | none | - | - | - | 18.30 | 16.48 | 0.900 |
| W | 29 | 2048 | none | - | - | - | 20.70 | 18.66 | 0.901 |
| W | 33 | 2048 | none | 22.97 | 20.67 | 0.900 | - | - | - |
| W | 34 | 2048 | none | 28.61 | 24.19 | 0.846 | - | - | - |
| W | 36 | 2048 | none | - | - | - | 20.99 | 18.91 | 0.901 |
| W | 37 | 2048 | none | - | - | - | 26.56 | 23.46 | 0.883 |
| W | 46 | 2048 | none | 54.24 | 32.35 | 0.596 | 26.85 | 23.74 | 0.884 |
| W | 47 | 2048 | none | - | - | - | 50.53 | 31.17 | 0.617 |
| W | 64 | 2048 | none | 55.39 | 33.02 | 0.596 | 51.42 | 31.62 | 0.615 |
| W | 128 | 2048 | none | 83.36 | 64.29 | 0.771 | 77.06 | 61.70 | 0.801
|
| S | 20 | 2048 | suffix | 17.38 | 15.74 | 0.906 | 16.10 | 14.59 | 0.907
|
| S | 45 | 2048 | suffix | 29.38 | 24.80 | 0.844 | 26.98 | 23.68 | 0.878
|

rows: union 45 (B200 39, GB300 40); worst ratio B200 0.930, GB300 0.933;
geomean ratio B200 0.853, GB300 0.867

rows: union 45 (B200 39, GB300 40); worst ratio B200 0.929, GB300 0.929;
geomean ratio B200 0.851, GB300 0.864

## Validation

- `tests/experimental/test_nvfp4_sparse_mla_decode.py` on B200 and GB300
against the delivered sources: 220 passed, 0 failed
on each card (124 `backend="cake"` cases, 77 `backend="cuda"` cases, 19
planner cases).
- Hardening rows on both cards with the `cake` and `cuda` backends: all
`-1` indices (T = 3 / 20), T = 3 / 47 / 128,
first / last pool rows, inputs on `cuda:1` with `cuda:0` current,
mismatched devices rejected, eager vs 3x CUDA-graph
replay bitwise, forced `num_ctas_per_token` 1..8 (7 rejected): all PASS.
- Exporter seal over all 64 export rows (32 per architecture): the
generated program is bitwise equal to its source launcher
  on every row; source / export time 1.0004x.
- compute-sanitizer synccheck and memcheck on the kernel family: 0
errors on 9 rows per card (negative controls detected).
- The clustered programs end with a CTA-exit handshake (one 4-byte
`st.async` flag per peer after the receive barrier,
waited on a dedicated mbarrier as the last statement), so a CTA never
retires while a peer-bound
`cp.async.bulk.shared::cluster` chunk may still read its shared memory;
it costs 2-3 % of kernel time on the
  P / W / S rows and is included in the tables above.
- Toolkits: the clustered programs declare `__launch_bounds__(448, 1)
__cluster_dims__(1,C,1)` (an earlier revision also
carried the third `__launch_bounds__` operand, which ptxas of CUDA 12.9
/ 13.0 rejects next to a static cluster entry).
The FP4 dequantisation extracts the `.b8` operand of
`cvt.rn.f16x2.e2m1x2` with the 32-bit unpack `mov.b32 {b, _, _, _}`
(the idiom of `vec_cast<half, __nv_fp4x2_e2m1>` in
`include/flashinfer/vec_dtypes.cuh`); an earlier revision used the
16-bit `mov.b16 {b, _}`, which ptxas 12.9 mis-assembles (wrong byte
widened: finite, plausible, wrong output on every
cake test node of the cu129 jobs, while 13.0 / 13.4 were correct). The
delivered sources compile with CUDA 12.9, 13.0
and 13.3 nvcc (CI toolkit images), and the cubins built by 12.9 and 13.0
match the FP32 reference on every cluster size.
- Layout: the sm_100a and sm_103a programs of a cluster size render to
the same text, so each ships once under
`csrc/cake_nvfp4_sparse_mla_decode/` and is compiled per architecture (7
kernel + 7 binding sources).

Tracking: flashinfer-ai/flashinfer#5716 (DSA NVFP4 sparse MLA decode),
tracker #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Stu Cao <stu@primeintellect.ai>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [613d12e](https://github.com/flashinfer-ai/flashinfer/commit/613d12e08d3230f79e5d9e57a676164508525486)

- **作者**: eigen
- **时间**: 2026-10-04T23:52:46Z
- **提交信息**: refactor(cake_moe_finalize_allreduce_fusion): regenerate the 12 kernels as one templated source (#5870)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Phase 2 of #5771 for `cake_moe_finalize_allreduce_fusion`: the twelve
generated device files

`csrc/cake_moe_finalize_allreduce_fusion/sm_100a/kernel_cake_trtllm_moe_finalize_{float16,bfloat16}_ws{2,4,8}_o{110,111}_device.cu`
(8,476 lines) are replaced by **one regenerated translation unit**,
`csrc/cake_moe_finalize_allreduce_fusion/cake_moe_finalize_kernels.cu`
(672 lines).

- The unit holds one templated body,
`cake_trtllm_moe_finalize::finalize_body<T, WS, QUANT>` (state dtype,
world size, NVFP4 quantisation profile), and twelve explicit `extern "C"
__global__` instantiations under the **unchanged kernel symbols**.
State-dtype differences go through a small `dtype_traits<T>` layer
(`__nv_bfloat16` / `__half`), world-size differences are `#pragma
unroll` loops over `WS`, and the quantisation epilogue is an `if
constexpr (QUANT)` region.
- The unit is emitted by the Cake exporter from the same programs that
produced the per-kernel files; nothing in it is hand-written. The
hand-written dispatch binding
(`cake_moe_finalize_allreduce_fusion_binding.cu`) and its kernel table
are untouched.
- `flashinfer/jit/cake_moe_finalize_comm.py` compiles the one unit plus
the binding per architecture (same module names and flags as before).

No behaviour or performance change is intended.

## Evidence

**SASS identity (24/24).** Every instantiation compiles to the same SASS
as the file it replaces, on `sm_100a` and `sm_103a`
(nvcc `-cubin -arch=<arch> --use_fast_math -std=c++17`, `cuobjdump
-sass`, addresses/encodings stripped, symbol masked):

| kernel | instructions (unit / previous) | sm_100a | sm_103a |
|---|---|---|---|
| `*_ws2_o110` (fp16, bf16) | 697 / 697 | identical | identical |
| `*_ws2_o111` (fp16, bf16) | 777 / 777 | identical | identical |
| `*_ws4_o110` (fp16, bf16) | 785 / 785 | identical | identical |
| `*_ws4_o111` (fp16, bf16) | 865 / 865 | identical | identical |
| `*_ws8_o110` (fp16, bf16) | 993 / 993 | identical | identical |
| `*_ws8_o111` (fp16, bf16) | 1065 / 1065 | identical | identical |

**Device source lines:** 8,476 → 672.

**GPU gates** (B200 and B300;
`tests/comm/test_cake_moe_finalize_dispatch.py`,
`tests/comm/test_cake_moe_finalize_allreduce.py` at ws 2/4/8 for fp16
and bf16, `tests/comm/test_allreduce_fusion_moe_unified_api.py`; paired
CUPTI benchmark `benchmarks/comm/bench_cake_moe_finalize_allreduce.py`
main vs this PR on the same GPUs) are posted as comments below as they
complete.

Related to #5771.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* MoE finalization and all-reduce now support both bfloat16 and float16
across workspace sizes 2, 4, and 8.
* Quantized and non-quantized output modes are available, with residual
addition and RMS normalization handled in the fused operation.
* **Refactor**
* Consolidated the supported MoE finalization kernels into a shared
implementation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3256c44](https://github.com/flashinfer-ai/flashinfer/commit/3256c444a4f74f5d6b50a1d2cdf2d7bf57990070)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-04T21:02:27Z
- **提交信息**: feat(moe_ep): add Rubin GenPhase and quantized combine options (#5991)

<!-- .github/pull_request_template.md -->

## 📌 Description

Expose GenPhase and NVFP4/MXFP8 FC2 return formats through the Rubin
MegaMoE backends. Add configuration validation, workspace and
scale-buffer handling, separate cache identities, and offline tuner
support.

GenPhase supports up to 1024 tokens per rank with BF16 combine.
Quantized combine uses the standard kernel with separate top-k
reduction. The final output remains BF16.

## 🔍 Related Issues

Builds on #5662 and #5699.

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

Changed-file pre-commit checks pass, including lint and type checks.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validation covers host contracts, native single-GPU correctness, and
EP2/4/8 graph replay and workspace reuse with NVFP4 and MXFP4/MXFP8
inputs.

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

The vendored device source is unchanged. Review the workspace layouts
and masked-route resets, cache isolation, and validation of unsupported
combinations. The default remains the standard kernel with BF16 combine.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added an optional GenPhase kernel variant for SM107, with
configuration requirements including a 1,024-token-per-rank limit.
* Added NVFP4 and MXFP8 formats for the FC2 combine payload; BF16
remains the default output format.
  * Added kernel-variant and combine-format options to tuning.
* **Documentation**
* Expanded guidance on supported formats, configuration constraints, and
tuning options.
* **Tests**
* Added coverage for GenPhase, quantized combine formats, runtime
options, and tuning dispatch.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [dfca689](https://github.com/flashinfer-ai/flashinfer/commit/dfca6891312cff277971d2d7d9b2b43532cae504)

- **作者**: eigen
- **时间**: 2026-10-04T20:25:17Z
- **提交信息**: feat(cake_dsv4): SM120 DeepSeek-V4 NVFP4 fused GPT-J RoPE + quantize + paged-insert writers (#6033)

## 📌 Description

SM120/SM121 DeepSeek-V4(.1) NVFP4 sparse-MLA cache writers, fused:
`cake_dsv4_nvfp4_rope_quantize_insert` (sliding-window pool:
GPT-J RoPE of Q with head padding or in place, GPT-J RoPE + BF16
rounding + NVFP4 quantize + paged insert of the latent KV) and
`cake_dsv4_nvfp4_kv_rope_quantize_insert` (compressed pool
`compress_ratio` 1|2, speculative-context writes). Records are
byte-identical to `nvfp4_quantize_append_sparse_mla_cache` applied to
the BF16-rounded roped rows, so the existing Cake decode /
prefill kernels read them unchanged. Generated sources under
`csrc/cake_dsv4/sm_120a/` (34 kernel variants, TVM-FFI binding,
manifest) come from the Cake exporter (Cake MR
https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1195,
kernel commit 67117e3900a, identity 1da663e2b218); JIT module
`flashinfer/jit/cake_dsv4_nvfp4_rope_insert.py`.

Motivation: vllm-project/vllm#59725 (SM120 DSv4 NVFP4 E2E regression) --
the NVFP4 path wrote the cache with torch RoPE + the
append kernel (hundreds of us per layer per step) while the FP8 path had
a fused writer.

Measured (CUPTI, cold L2): RTX PRO 6000 / RTX 5090, CUPTI cold-L2
medians: SWA-pool decode N=8 **2.24 / 1.86 us** vs 339 / 512 us for the
pre-fix torch RoPE + append path and 26.8 / 27.4 us for the in-place
RoPE kernel + append (vLLM FP8 fused op 3.01 / 2.53); in-place prefill
N=4096 **13.3 / 10.8 us** (pre-fix 402 / 552, unfused 36.9 / 38.1, FP8
op 53.2 / 51.7; 1.19x / 1.01x of the copy-bandwidth floor); N=16384 43.7
/ 41.5 us (1.03x / 1.02x of the floor); compressed-pool ratio-1 N=8
**2.02 / 1.76 us** (FP8 Triton writer 2.37 / 2.02), ratio-2 N=4096 6.6 /
4.3 us (FP8 7.7 / 6.3); DSpark context N=1024 3.8 / 3.3 us (FP8 4.4 /
3.6). Every one of 68 gated rows beats both unfused sequences on both
SKUs; 67 of 68 also beat the FP8 fused op (the head-padding copy row
N=4096 H=8->16 ties it on the 5090, 76.1 vs 75.5 us, both copy-bound).

## 🔍 Related Issues

vllm-project/vllm#59725; FlashInfer SM120 DSv4 tracker #4254.

## 🚀 Pull Request Checklist

- [x] Pre-commit checks (`pre-commit run --all-files` on the touched
files)
- [x] Tests: `tests/attention/test_cake_dsv4_nvfp4_rope_insert.py` (25)
on RTX PRO 6000 and RTX 5090
- [x] Benchmarks: `benchmarks/bench_cake_dsv4_nvfp4_rope_insert.py`
- [x] Documentation: `docs/api/attention.rst`,
`csrc/cake_dsv4/README.md`

## Reviewer Notes

- The generated `csrc/cake_dsv4/sm_120a/*` files are exporter output (do
not hand-edit); the manifest records the Cake kernel commit and the
source identity, and the binding checks `total_slots <= INT32_MAX`
(32-bit page math in the kernel).
- Launch geometry: one warp per (token, head slot), 256-thread CTAs;
copy form `q_head_padded + 1` warps per token, in-place form
`q_head_padded / 8` (the slot-0 warp also inserts the KV row), kv entry
one warp per token.
- Numerics: cache bytes are identical to
`nvfp4_quantize_append_sparse_mla_cache` on the BF16-rounded roped row
for every row of
the test matrix (byte-exact oracle on the FlashInfer side too); the
read-back test runs the Cake decode route on the written
pages in the decode tests' input regime (`kv, q ~ N(0, 1)`), because the
decode kernel's P/V operands are E4M3-bounded.
- `q_inplace=True` requires `q.shape[1] == q_head_padded` and
`apply_q_rope=True` (checked); it rewrites only the 64 rope dims of `q`.
- JIT build of the module takes ~6 s on SM120; tests: 25 cases on RTX
PRO 6000 and RTX 5090.

## Serving E2E

8x RTX PRO 6000 Blackwell Server Edition, TP8, DeepSeek-V4.1-Flash, vLLM
nightly `1a001d584` + the vLLM-side patch
(fork branch `cake-945-sm120-dsv4-nvfp4-cake-writers`), `vllm bench
serve` random 1024 in / 256 out. Output tok/s:

| c | FP8 | NVFP4 pre-fix | NVFP4 fixed (this PR) | fixed/FP8 |
fixed/pre-fix | with DSpark k=5: fixed/FP8 | fixed/pre-fix |
|---|---|---|---|---|---|---|---|
| 1 | 94.1 | 87.2 | **96.7** | 1.028 | 1.109 | 1.010 | 1.112 |
| 4 | 300.5 | 278.9 | **310.2** | 1.032 | 1.112 | 0.998 | 1.037 |
| 16 | 649.7 | 625.7 | **675.5** | 1.040 | 1.080 | 1.024 | 1.037 |
| 64 | 1125.2 | 1117.8 | **1152.5** | 1.024 | 1.031 | 1.012 | 1.012 |

KV capacity +38.9 % vs FP8 (1,548,577 vs 1,114,975 tokens at
max-model-len 16384). Objective QA (16 questions, thinking off, greedy,
asked twice per server): all six arms 16/16 correct and 16/16
self-consistent.
Profiler at c=16: KV write path 21.6 ms / 5,940 launches for FP8, ~263
ms / ~154,700 launches for the pre-fix NVFP4 path, 13.3 ms / 5,940
launches with this PR's writers.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added fused NVFP4 RoPE and cache-insertion APIs for supported
SM120/SM121 devices. They support query rotation with padded or in-place
output, plus KV-only insertion with compression ratios of 1 or 2.
* Added build-time module generation for the new cache writers when
supported.
* **Documentation**
* Added API guidance and examples describing supported cache-writing
modes and output compatibility.
* **Benchmarks**
* Added timing comparisons between fused cache writers and an unfused
PyTorch path.
* **Tests**
* Added coverage for cache contents, query outputs, input validation,
empty batches, and CUDA graph replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4b6d64b](https://github.com/flashinfer-ai/flashinfer/commit/4b6d64be9f519218190ae80134b328f2d137eb77)

- **作者**: eigen
- **时间**: 2026-10-04T19:46:08Z
- **提交信息**: feat(cake_selective_state_update): promote the headdim-64 / dstate-128 single-token decode row (Nemotron-H, granite-4.0-h) (#6040)

## Summary

Promote the headdim-64 / dstate-128 single-token
`selective_state_update` decode row (Nemotron-H, granite-4.0-h; BF16 and
FP32 state) to the Cake backend, on the raw SGLang decode ABI (BF16
`dt`/`D`/`dt_bias` broadcasts, int32 slot tables, padded
fused-projection views, `pad_slot_id` rows) as well as the canonical
ABI.

Generated by the Cake export adapter `exports/selective_state_update` at
Cake revision `ad10c97638e7ab0f643f4d1b09208c54ae111bae` (protocol lock
producer `ad10c97638e7ab0f643f4d1b09208c54ae111bae`, target revision
`6dec771b1fb7980dad595fb59a9d490294592081`); Cake MR
https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1202.

- New programs under `csrc/cake_selective_state_update/{cuda,host}/`:
`cake_selective_state_update_stp_paired_rows` /
`..._stp_paired_rows_mb4` (two adjacent 64-row heads form one 128-row
program head streamed through row-major 32-row TMA stages; B/C
coefficients resident in registers; direct grid; the `_mb4` source is
the four-CTA launch-bounds schedule B200 selects between 6 and 16
program heads per SM), `..._stp_hd64_rows_bf16`,
`..._stp_hd64_rows_fp32` (row-owner tiles for under-saturated grids, odd
head pairings and FP32 state; one source per state dtype, instantiated
per plan through the `PREFETCH_ROWS` / `DIM_TILES` defines).
- The five shipped BF16 128×128 STP programs stay byte-identical; every
previously served row keeps its program and defines.
- Loader `flashinfer/jit/mamba/cake_selective_state_update.py`:
`plan_route` admits the 3-D `(64, 128)` call (`_plan_stp_hd64`),
`_plan_stp_batch(paired=…)` with `_paired_rows_program` /
`_paired_heads_per_cta`, `hd64_rows_plan` → `(dim_tiles, prefetch_rows)`
→ `rows_defines(dt, idx, prefetch_rows, dim_tiles)`, `pad_slot_id`
forwarded, raw-address slot tables and runtime batch strides for the
padded projection views.
- Tests `tests/mamba/test_cake_selective_state_update.py`: raw decode
layout vs the FlashInfer kernel, pad rows (zero-state output, untouched
pool), CUDA-graph capture, non-dense-row / odd-pairing fallbacks, define
selection, plan rules.

## Speedup summary

Baseline = `selective_state_update(backend="flashinfer",
algorithm="auto")` on identical inputs; incumbent = previous Cake
backend (no hd64 row: `backend="cake"` fell back to the FlashInfer
kernel, ratio 1.00 by construction, shipped 128×128 rows unchanged and
byte-identical). CUPTI kernel time (`loom.bench`, cold L2), 5
interleaved rounds × 40 iterations. Ratio = baseline / Cake (> 1 = Cake
faster).

| shape (raw SGLang ABI) | B200 FI µs | B200 Cake µs | B200 FI/Cake |
GB300 FI µs | GB300 Cake µs | GB300 FI/Cake |
|---|---|---|---|---|---|---|
| Nemotron-H TP1 H128 G8 b1 BF16 | 5.02 | 3.81 | **1.319** | 4.58 | 4.22
| **1.083** |
| Nemotron-H TP1 H128 G8 b2 BF16 | 7.65 | 4.99 | **1.532** | 7.60 | 5.15
| **1.475** |
| Nemotron-H TP1 H128 G8 b4 BF16 | 7.14 | 6.45 | **1.107** | 7.20 | 6.66
| **1.082** |
| Nemotron-H TP1 H128 G8 b8 BF16 | 10.02 | 9.46 | **1.059** | 10.18 |
9.28 | **1.097** |
| Nemotron-H TP1 H128 G8 b16 BF16 | 17.02 | 14.42 | **1.181** | 15.87 |
15.01 | **1.058** |
| Nemotron-H TP1 H128 G8 b32 BF16 | 27.94 | 25.34 | **1.102** | 27.10 |
25.31 | **1.071** |
| Nemotron-H TP1 H128 G8 b64 BF16 | 48.67 | 44.96 | **1.083** | 46.13 |
44.00 | **1.048** |
| Nemotron-H TP1 H128 G8 b128 BF16 | 91.68 | 86.81 | **1.056** | 85.70 |
84.16 | **1.018** |
| Nemotron-H TP1 H128 G8 b256 BF16 | 176.49 | 166.85 | **1.058** |
165.60 | 161.12 | **1.028** |
| Nemotron-H TP1 H128 G8 b1 FP32 | 4.93 | 4.29 | **1.149** | 5.30 | 4.99
| **1.061** |
| Nemotron-H TP1 H128 G8 b8 FP32 | 14.61 | 14.05 | **1.040** | 15.47 |
14.08 | **1.099** |
| Nemotron-H TP1 H128 G8 b64 FP32 | 86.25 | 83.53 | **1.033** | 84.53 |
83.54 | **1.012** |
| Nemotron-H TP1 H128 G8 b256 FP32 | 325.37 | 317.48 | **1.025** |
315.15 | 313.71 | **1.005** |
| Nemotron-H TP2 H64 G4 b1 BF16 | 3.63 | 3.36 | **1.081** | 4.22 | 4.16
| **1.015** |
| Nemotron-H TP2 H64 G4 b64 BF16 | 27.58 | 25.29 | **1.090** | 26.46 |
25.17 | **1.052** |
| Nemotron-H TP2 H64 G4 b256 BF16 | 92.32 | 86.88 | **1.063** | 85.18 |
84.10 | **1.013** |
| Nemotron-H TP4 H32 G2 b1 BF16 | 3.33 | 3.06 | **1.089** | 3.84 | 3.74
| **1.026** |
| Nemotron-H TP4 H32 G2 b64 BF16 | 16.74 | 14.34 | **1.167** | 15.65 |
14.88 | **1.052** |
| Nemotron-H TP4 H32 G2 b256 BF16 | 48.94 | 45.01 | **1.087** | 45.97 |
44.03 | **1.044** |
| granite-small H128 G1 b1 BF16 | 4.96 | 3.87 | **1.281** | 4.61 | 4.19
| **1.099** |
| granite-small H128 G1 b8 BF16 | FI n/a (dispatchRatio) | 9.60 | — | FI
n/a (dispatchRatio) | 9.33 | — |
| granite-small H128 G1 b64 BF16 | FI n/a (dispatchRatio) | 45.05 | — |
FI n/a (dispatchRatio) | 43.97 | — |
| granite-small H128 G1 b256 BF16 | FI n/a (dispatchRatio) | 167.18 | —
| FI n/a (dispatchRatio) | 160.96 | — |
| granite-tiny H48 G1 b1 BF16 | 3.58 | 3.23 | **1.109** | 4.32 | 4.03 |
**1.071** |
| granite-tiny H48 G1 b64 BF16 | FI n/a (dispatchRatio) | 21.28 | — | FI
n/a (dispatchRatio) | 21.23 | — |

B200: 42/42 representative rows >= 1.00 vs FI; below: []
GB300: 42/42 representative rows >= 1.00 vs FI; below: []

Floor distance (`floor` arm = `torch.add(src, 0, out=dst)` over the
state bytes, same run): every b64+ row is within 2-6 % of the floor; the
b1/b2 rows sit at floor x1.3-1.7 (one dependent slot-table round trip
plus the per-head scalar chain that the memcpy-like floor does not pay;
the FI stock kernel sits in the same latency class). max cake/floor B200
1.458 (nemh_tp2_H64_G4_bflo_raw_b1); max cake/floor GB300 1.681
(band_tp2_H64_G4_bflo_raw_b2).

Canonical-ABI rows (FP32 coefficients, int64 tables) and the band points
are in the Cake MR table. granite rows with `nheads / ngroups` ∈ {48,
128} have no FlashInfer baseline (the stock kernel's `dispatchRatio`
rejects the ratio); Cake serves them.

## Verification

Cake revision `ad10c97638e7ab0f643f4d1b09208c54ae111bae` (branch
`averyh/cake-935-ssu-hd64-decode`); protocol lock producer = the same
revision; FlashInfer target revision
`6dec771b1fb7980dad595fb59a9d490294592081`.

| check | GB300 (JHB `nvl72d401-T18`, sglang:26.07, step
`14e75379143a7a7d3fc78406`) | B200 (NSC `nsc-svg-slurm-1-gpu-108`,
sglang:26.07, step `d4e97114544c960e48bd0379`) |
|---|---|---|
| `tools/export-generated-programs run` (64 shapes per arch,
Source/Export ratio, slop audit) | RUN_EXIT=0, 64/64 shapes |
RUN_EXIT=0, 64/64 shapes |
| `pytest tests/mamba/test_cake_selective_state_update.py` on the
exported worktree | 58 passed (rc 0) | 58 passed (rc 0) |
| sglang adapter route tests (CPU, `test_cake_mamba_sp_routes.py -k
ssu`) | 11 passed (rc 0) | 11 passed (rc 0) |
| sglang adapter kernel tests (GPU,
`ops/mamba/test_cake_selective_state_update.py -k hd64`) | 9 passed (rc
0) | 9 passed (rc 0) |
| `compute-sanitizer --tool synccheck` and `--tool memcheck` over the
hd64 correctness rows (`--rounds 0`) | synccheck rc 0, memcheck rc 0, 4
runs, 0 errors | not run on this arch (GB300 covers it) |

Logs stay on the clusters (export run logs and `results/gate/*` under
the session workspace); the local manifest records host, path, size and
SHA-256 of the pulled summaries. compute-sanitizer ran on GB300
(sglang:26.07 provides no sanitizer on the B200 image route; the kernels
are architecture-neutral sources).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added optimized execution paths for eligible single-token workloads
with head dimension 64, including paired-head and row-based processing.
* Expanded support for different state precisions, index widths, and
batch layouts, including padded state slots.
  * Added CUDA graph coverage for the new execution paths.
* **Bug Fixes**
* Improved handling of padded state slots so outputs can be computed
without updating padded state.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7aa42e2](https://github.com/flashinfer-ai/flashinfer/commit/7aa42e2dc147b34987358af0bc03af0383b8ff5f)

- **作者**: eigen
- **时间**: 2026-10-04T17:50:31Z
- **提交信息**: feat(cake_kimi_k3_attn_res): mid-M routing of the small-M Kimi-K3 AttnRes programs for SM100 / SM103 (#6036)

## Generated-program export evidence

Baseline: **Cake production AttnRes launcher (launch_for_eval)** at Cake
revision `dfa1b856faf83a9cdc29e290e7e4062e569a8f26`.

## Hardware stages

- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-77ce95d1-a793-ea91-f29e-f6251c4197ae`;
100 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-a735906c-d8b3-8029-3cab-d52df0be8326`;
50 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-57cc9f03-562b-f2a8-ac59-55679531bb8f`; 50 shapes (named in the
per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-b8f7f32b-e144-d7e2-f26e-23eeafd17c67`; 50 shapes (named in the
per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-323f05d3-4909-0c21-9aa2-923539b95eb0`; 50 shapes (named in the
per-shape tables below).

Target revision: `7f0c200b55eb022ed0e0057804e8ca4bc05c0499` (the
measured scaffold `49ca49a216f55b946dc7688c96bcf683a89e6927` rebased
onto upstream main; scaffold file contents unchanged).

Benchmark execution: `symmetric_external_cuda_graph` with 8
independently captured graph instances per arm, replayed round-robin; 3
counterbalanced groups, 100 warmup calls and 1000 reportable calls per
arm/group (fixed counts; no sizing pilot).
Each sample follows one unmeasured same-arm launch, state restoration,
and a fresh cold-L2 flush.

The complete semantic arguments and machine-readable receipts remain in
`summary.json`; the tables below retain every registered shape without
repeating those arguments.

## Per-shape results

|Shape|GPU|Route|Source ms|Export ms|Source /
Export|Correctness|Verdict|
|---|---|---|---:|---:|---:|---|---|

|primary_m1_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1_k0_sm_100a_pdl0|0.002720|0.002720|1.000000x|pass|pass|

|primary_m1_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1_k1_sm_100a_pdl0|0.003520|0.003520|1.000000x|pass|pass|

|primary_m1_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1_k4_sm_100a_pdl0|0.004385|0.004416|0.992980x|pass|pass|

|primary_m1_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1_k8_sm_100a_pdl0|0.005536|0.005536|1.000000x|pass|pass|

|primary_m2_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2_k0_sm_100a_pdl0|0.002784|0.002784|1.000000x|pass|pass|

|primary_m2_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2_k1_sm_100a_pdl0|0.003360|0.003360|1.000000x|pass|pass|

|primary_m2_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2_k4_sm_100a_pdl0|0.004416|0.004416|1.000000x|pass|pass|

|primary_m2_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2_k8_sm_100a_pdl0|0.005407|0.005409|0.999630x|pass|pass|

|primary_m4_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4_k0_sm_100a_pdl0|0.002688|0.002688|1.000000x|pass|pass|

|primary_m4_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4_k1_sm_100a_pdl0|0.003424|0.003424|1.000000x|pass|pass|

|primary_m4_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m4_k4_sm_100a_pdl0|0.004511|0.004480|1.006920x|pass|pass|

|primary_m4_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4_k8_sm_100a_pdl0|0.005632|0.005633|0.999822x|pass|pass|

|primary_m8_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8_k0_sm_100a_pdl0|0.002849|0.002880|0.989236x|pass|pass|

|primary_m8_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8_k1_sm_100a_pdl0|0.003584|0.003584|1.000000x|pass|pass|

|primary_m8_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8_k4_sm_100a_pdl0|0.004576|0.004607|0.993271x|pass|pass|

|primary_m8_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8_k8_sm_100a_pdl0|0.005728|0.005727|1.000175x|pass|pass|

|primary_m16_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16_k0_sm_100a_pdl0|0.002911|0.002912|0.999657x|pass|pass|

|primary_m16_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16_k1_sm_100a_pdl0|0.003616|0.003616|1.000000x|pass|pass|

|primary_m16_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16_k4_sm_100a_pdl0|0.004736|0.004736|1.000000x|pass|pass|

|primary_m16_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16_k8_sm_100a_pdl0|0.005920|0.005952|0.994624x|pass|pass|

|primary_m32_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m32_k0_sm_100a_pdl0|0.002976|0.002977|0.999664x|pass|pass|

|primary_m32_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m32_k1_sm_100a_pdl0|0.003776|0.003776|1.000000x|pass|pass|

|primary_m32_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m32_k4_sm_100a_pdl0|0.004960|0.004960|1.000000x|pass|pass|

|primary_m32_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m32_k8_sm_100a_pdl0|0.006496|0.006528|0.995098x|pass|pass|

|primary_m64_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m64_k0_sm_100a_pdl0|0.003232|0.003232|1.000000x|pass|pass|

|primary_m64_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m64_k1_sm_100a_pdl0|0.004160|0.004160|1.000000x|pass|pass|

|primary_m64_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m64_k4_sm_100a_pdl0|0.005600|0.005600|1.000000x|pass|pass|

|primary_m64_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m64_k8_sm_100a_pdl0|0.007327|0.007424|0.986934x|pass|pass|

|primary_m128_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m128_k0_sm_100a_pdl0|0.003712|0.003743|0.991718x|pass|pass|

|primary_m128_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m128_k1_sm_100a_pdl0|0.004736|0.004736|1.000000x|pass|pass|

|primary_m128_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m128_k4_sm_100a_pdl0|0.006592|0.006592|1.000000x|pass|pass|

|primary_m128_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m128_k8_sm_100a_pdl0|0.008608|0.008608|1.000000x|pass|pass|

|primary_m256_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m256_k0_sm_100a_pdl0|0.004832|0.004832|1.000000x|pass|pass|

|primary_m256_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m256_k1_sm_100a_pdl0|0.006464|0.006464|1.000000x|pass|pass|

|primary_m256_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m256_k4_sm_100a_pdl0|0.009984|0.009920|1.006452x|pass|pass|

|primary_m256_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m256_k8_sm_100a_pdl0|0.012417|0.012448|0.997510x|pass|pass|

|primary_m512_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m512_k0_sm_100a_pdl0|0.007648|0.007648|1.000000x|pass|pass|

|primary_m512_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m512_k1_sm_100a_pdl0|0.010145|0.010144|1.000099x|pass|pass|

|primary_m512_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m512_k4_sm_100a_pdl0|0.015008|0.015008|1.000000x|pass|pass|

|primary_m512_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m512_k8_sm_100a_pdl0|0.021088|0.021024|1.003044x|pass|pass|

|primary_m1024_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1024_k0_sm_100a_pdl0|0.011488|0.011457|1.002706x|pass|pass|

|primary_m1024_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1024_k1_sm_100a_pdl0|0.015328|0.015360|0.997917x|pass|pass|

|primary_m1024_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1024_k4_sm_100a_pdl0|0.023328|0.023329|0.999957x|pass|pass|

|primary_m1024_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1024_k8_sm_100a_pdl0|0.033696|0.033728|0.999051x|pass|pass|

|primary_m2048_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2048_k0_sm_100a_pdl0|0.021376|0.021407|0.998552x|pass|pass|

|primary_m2048_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2048_k1_sm_100a_pdl0|0.026688|0.026656|1.001200x|pass|pass|

|primary_m2048_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2048_k4_sm_100a_pdl0|0.040576|0.040640|0.998425x|pass|pass|

|primary_m2048_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2048_k8_sm_100a_pdl0|0.061568|0.061536|1.000520x|pass|pass|

|primary_m4096_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4096_k0_sm_100a_pdl0|0.039104|0.039167|0.998392x|pass|pass|

|primary_m4096_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m4096_k1_sm_100a_pdl0|0.048927|0.048960|0.999326x|pass|pass|

|primary_m4096_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4096_k4_sm_100a_pdl0|0.076384|0.076352|1.000419x|pass|pass|

|primary_m4096_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4096_k8_sm_100a_pdl0|0.115072|0.115008|1.000556x|pass|pass|

|primary_m8192_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8192_k0_sm_100a_pdl0|0.074112|0.074144|0.999568x|pass|pass|

|primary_m8192_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8192_k1_sm_100a_pdl0|0.092480|0.092512|0.999654x|pass|pass|

|primary_m8192_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8192_k4_sm_100a_pdl0|0.143520|0.143584|0.999554x|pass|pass|

|primary_m8192_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8192_k8_sm_100a_pdl0|0.213920|0.213887|1.000154x|pass|pass|

|primary_m16384_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16384_k0_sm_100a_pdl0|0.144415|0.144384|1.000215x|pass|pass|

|primary_m16384_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16384_k1_sm_100a_pdl0|0.178720|0.178719|1.000006x|pass|pass|

|primary_m16384_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16384_k4_sm_100a_pdl0|0.274016|0.274079|0.999770x|pass|pass|

|primary_m16384_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16384_k8_sm_100a_pdl0|0.413695|0.413631|1.000156x|pass|pass|

|k_sweep_m1_k2__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m1_k2_sm_100a_pdl0|0.003584|0.003584|1.000000x|pass|pass|

|k_sweep_m1_k3__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m1_k3_sm_100a_pdl0|0.003936|0.003968|0.991935x|pass|pass|

|k_sweep_m1_k5__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m1_k5_sm_100a_pdl0|0.004640|0.004640|1.000000x|pass|pass|

|k_sweep_m1_k6__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m1_k6_sm_100a_pdl0|0.004928|0.004960|0.993548x|pass|pass|

|k_sweep_m1_k7__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m1_k7_sm_100a_pdl0|0.005055|0.004960|1.019153x|pass|pass|

|k_sweep_m4096_k2__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k2_sm_100a_pdl0|0.058592|0.058624|0.999454x|pass|pass|

|k_sweep_m4096_k3__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k3_sm_100a_pdl0|0.067200|0.067200|1.000000x|pass|pass|

|k_sweep_m4096_k5__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m4096_k5_sm_100a_pdl0|0.085023|0.084992|1.000365x|pass|pass|

|k_sweep_m4096_k6__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k6_sm_100a_pdl0|0.095712|0.095775|0.999342x|pass|pass|

|k_sweep_m4096_k7__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k7_sm_100a_pdl0|0.106400|0.106400|1.000000x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_100a__pdl0|G1|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_100a_pdl0|0.004865|0.004864|1.000206x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_100a__pdl0|G0|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_100a_pdl0|0.022304|0.022304|1.000000x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_100a__pdl0|G0|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_100a_pdl0|0.026944|0.026976|0.998814x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_100a__pdl0|G1|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_100a_pdl0|0.009408|0.009632|0.976744x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_100a__pdl0|G0|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_100a_pdl0|0.015904|0.015936|0.997992x|pass|pass|

|primary_m1_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1_k0_sm_100a_pdl1|0.002657|0.002687|0.988835x|pass|pass|

|primary_m1_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1_k1_sm_100a_pdl1|0.003489|0.003520|0.991193x|pass|pass|

|primary_m1_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1_k4_sm_100a_pdl1|0.004447|0.004447|1.000000x|pass|pass|

|primary_m1_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1_k8_sm_100a_pdl1|0.005504|0.005504|1.000000x|pass|pass|

|primary_m2_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2_k0_sm_100a_pdl1|0.002784|0.002784|1.000000x|pass|pass|

|primary_m2_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2_k1_sm_100a_pdl1|0.003360|0.003360|1.000000x|pass|pass|

|primary_m2_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2_k4_sm_100a_pdl1|0.004480|0.004448|1.007194x|pass|pass|

|primary_m2_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2_k8_sm_100a_pdl1|0.005376|0.005439|0.988417x|pass|pass|

|primary_m4_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4_k0_sm_100a_pdl1|0.002688|0.002689|0.999628x|pass|pass|

|primary_m4_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4_k1_sm_100a_pdl1|0.003360|0.003391|0.990858x|pass|pass|

|primary_m4_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4_k4_sm_100a_pdl1|0.004511|0.004480|1.006920x|pass|pass|

|primary_m4_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4_k8_sm_100a_pdl1|0.005633|0.005664|0.994527x|pass|pass|

|primary_m8_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8_k0_sm_100a_pdl1|0.002848|0.002848|1.000000x|pass|pass|

|primary_m8_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8_k1_sm_100a_pdl1|0.003584|0.003584|1.000000x|pass|pass|

|primary_m8_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8_k4_sm_100a_pdl1|0.004576|0.004576|1.000000x|pass|pass|

|primary_m8_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8_k8_sm_100a_pdl1|0.005664|0.005633|1.005503x|pass|pass|

|primary_m16_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16_k0_sm_100a_pdl1|0.002880|0.002880|1.000000x|pass|pass|

|primary_m16_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16_k1_sm_100a_pdl1|0.003616|0.003616|1.000000x|pass|pass|

|primary_m16_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16_k4_sm_100a_pdl1|0.004768|0.004737|1.006544x|pass|pass|

|primary_m16_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16_k8_sm_100a_pdl1|0.005920|0.005952|0.994624x|pass|pass|

|primary_m32_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m32_k0_sm_100a_pdl1|0.003040|0.003040|1.000000x|pass|pass|

|primary_m32_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m32_k1_sm_100a_pdl1|0.003808|0.003839|0.991925x|pass|pass|

|primary_m32_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m32_k4_sm_100a_pdl1|0.005120|0.005120|1.000000x|pass|pass|

|primary_m32_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m32_k8_sm_100a_pdl1|0.006432|0.006464|0.995050x|pass|pass|

|primary_m64_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m64_k0_sm_100a_pdl1|0.003232|0.003232|1.000000x|pass|pass|

|primary_m64_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m64_k1_sm_100a_pdl1|0.004160|0.004160|1.000000x|pass|pass|

|primary_m64_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m64_k4_sm_100a_pdl1|0.005664|0.005664|1.000000x|pass|pass|

|primary_m64_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m64_k8_sm_100a_pdl1|0.007360|0.007456|0.987124x|pass|pass|

|primary_m128_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m128_k0_sm_100a_pdl1|0.003712|0.003712|1.000000x|pass|pass|

|primary_m128_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m128_k1_sm_100a_pdl1|0.004768|0.004800|0.993333x|pass|pass|

|primary_m128_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m128_k4_sm_100a_pdl1|0.006624|0.006624|1.000000x|pass|pass|

|primary_m128_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m128_k8_sm_100a_pdl1|0.008609|0.008640|0.996412x|pass|pass|

|primary_m256_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m256_k0_sm_100a_pdl1|0.004767|0.004768|0.999790x|pass|pass|

|primary_m256_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m256_k1_sm_100a_pdl1|0.006240|0.006240|1.000000x|pass|pass|

|primary_m256_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m256_k4_sm_100a_pdl1|0.010015|0.009984|1.003105x|pass|pass|

|primary_m256_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m256_k8_sm_100a_pdl1|0.012607|0.012608|0.999921x|pass|pass|

|primary_m512_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m512_k0_sm_100a_pdl1|0.007616|0.007616|1.000000x|pass|pass|

|primary_m512_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m512_k1_sm_100a_pdl1|0.010079|0.010079|1.000000x|pass|pass|

|primary_m512_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m512_k4_sm_100a_pdl1|0.015040|0.015040|1.000000x|pass|pass|

|primary_m512_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m512_k8_sm_100a_pdl1|0.021279|0.021248|1.001459x|pass|pass|

|primary_m1024_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1024_k0_sm_100a_pdl1|0.011488|0.011488|1.000000x|pass|pass|

|primary_m1024_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1024_k1_sm_100a_pdl1|0.015264|0.015296|0.997908x|pass|pass|

|primary_m1024_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1024_k4_sm_100a_pdl1|0.023424|0.023424|1.000000x|pass|pass|

|primary_m1024_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1024_k8_sm_100a_pdl1|0.033824|0.033824|1.000000x|pass|pass|

|primary_m2048_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2048_k0_sm_100a_pdl1|0.021280|0.021312|0.998475x|pass|pass|

|primary_m2048_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2048_k1_sm_100a_pdl1|0.026880|0.026912|0.998811x|pass|pass|

|primary_m2048_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2048_k4_sm_100a_pdl1|0.040384|0.040416|0.999208x|pass|pass|

|primary_m2048_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2048_k8_sm_100a_pdl1|0.061215|0.061216|0.999984x|pass|pass|

|primary_m4096_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4096_k0_sm_100a_pdl1|0.039136|0.039168|0.999183x|pass|pass|

|primary_m4096_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4096_k1_sm_100a_pdl1|0.048640|0.048703|0.998706x|pass|pass|

|primary_m4096_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4096_k4_sm_100a_pdl1|0.075456|0.075487|0.999583x|pass|pass|

|primary_m4096_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4096_k8_sm_100a_pdl1|0.115103|0.114976|1.001105x|pass|pass|

|primary_m8192_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8192_k0_sm_100a_pdl1|0.074143|0.074112|1.000418x|pass|pass|

|primary_m8192_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8192_k1_sm_100a_pdl1|0.092768|0.092736|1.000345x|pass|pass|

|primary_m8192_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8192_k4_sm_100a_pdl1|0.142464|0.142528|0.999551x|pass|pass|

|primary_m8192_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8192_k8_sm_100a_pdl1|0.214623|0.214591|1.000149x|pass|pass|

|primary_m16384_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16384_k0_sm_100a_pdl1|0.144288|0.144288|1.000000x|pass|pass|

|primary_m16384_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16384_k1_sm_100a_pdl1|0.177376|0.177407|0.999825x|pass|pass|

|primary_m16384_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16384_k4_sm_100a_pdl1|0.274752|0.274815|0.999771x|pass|pass|

|primary_m16384_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16384_k8_sm_100a_pdl1|0.413536|0.413664|0.999691x|pass|pass|

|k_sweep_m1_k2__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m1_k2_sm_100a_pdl1|0.003552|0.003552|1.000000x|pass|pass|

|k_sweep_m1_k3__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m1_k3_sm_100a_pdl1|0.003936|0.003936|1.000000x|pass|pass|

|k_sweep_m1_k5__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m1_k5_sm_100a_pdl1|0.004672|0.004672|1.000000x|pass|pass|

|k_sweep_m1_k6__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m1_k6_sm_100a_pdl1|0.004896|0.004928|0.993506x|pass|pass|

|k_sweep_m1_k7__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m1_k7_sm_100a_pdl1|0.005025|0.004960|1.013105x|pass|pass|

|k_sweep_m4096_k2__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k2_sm_100a_pdl1|0.060096|0.060127|0.999484x|pass|pass|

|k_sweep_m4096_k3__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k3_sm_100a_pdl1|0.067136|0.067136|1.000000x|pass|pass|

|k_sweep_m4096_k5__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m4096_k5_sm_100a_pdl1|0.084832|0.084831|1.000012x|pass|pass|

|k_sweep_m4096_k6__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k6_sm_100a_pdl1|0.095264|0.095328|0.999329x|pass|pass|

|k_sweep_m4096_k7__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k7_sm_100a_pdl1|0.106304|0.106336|0.999699x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_100a__pdl1|G1|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_100a_pdl1|0.004896|0.004896|1.000000x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_100a__pdl1|G0|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_100a_pdl1|0.023232|0.023232|1.000000x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_100a__pdl1|G0|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_100a_pdl1|0.026559|0.026528|1.001169x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_100a__pdl1|G1|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_100a_pdl1|0.009440|0.009664|0.976821x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_100a__pdl1|G0|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_100a_pdl1|0.015776|0.015808|0.997976x|pass|pass|

|primary_m1_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m1_k0_sm_103a_pdl0|0.002592|0.002592|1.000000x|pass|pass|

|primary_m1_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m1_k1_sm_103a_pdl0|0.003264|0.003296|0.990291x|pass|pass|

|primary_m1_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m1_k4_sm_103a_pdl0|0.004256|0.004320|0.985185x|pass|pass|

|primary_m1_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m1_k8_sm_103a_pdl0|0.005088|0.005089|0.999803x|pass|pass|

|primary_m2_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m2_k0_sm_103a_pdl0|0.002656|0.002688|0.988095x|pass|pass|

|primary_m2_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m2_k1_sm_103a_pdl0|0.003232|0.003264|0.990196x|pass|pass|

|primary_m2_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m2_k4_sm_103a_pdl0|0.004256|0.004288|0.992537x|pass|pass|

|primary_m2_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m2_k8_sm_103a_pdl0|0.005248|0.005248|1.000000x|pass|pass|

|primary_m4_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m4_k0_sm_103a_pdl0|0.002720|0.002688|1.011905x|pass|pass|

|primary_m4_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m4_k1_sm_103a_pdl0|0.003232|0.003263|0.990500x|pass|pass|

|primary_m4_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m4_k4_sm_103a_pdl0|0.004385|0.004384|1.000228x|pass|pass|

|primary_m4_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m4_k8_sm_103a_pdl0|0.005344|0.005344|1.000000x|pass|pass|

|primary_m8_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m8_k0_sm_103a_pdl0|0.002720|0.002752|0.988372x|pass|pass|

|primary_m8_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m8_k1_sm_103a_pdl0|0.003296|0.003328|0.990385x|pass|pass|

|primary_m8_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m8_k4_sm_103a_pdl0|0.004512|0.004512|1.000000x|pass|pass|

|primary_m8_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m8_k8_sm_103a_pdl0|0.005408|0.005377|1.005765x|pass|pass|

|primary_m16_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m16_k0_sm_103a_pdl0|0.002912|0.002912|1.000000x|pass|pass|

|primary_m16_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m16_k1_sm_103a_pdl0|0.003520|0.003488|1.009174x|pass|pass|

|primary_m16_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m16_k4_sm_103a_pdl0|0.004703|0.004704|0.999787x|pass|pass|

|primary_m16_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m16_k8_sm_103a_pdl0|0.005664|0.005633|1.005503x|pass|pass|

|primary_m32_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m32_k0_sm_103a_pdl0|0.003007|0.002976|1.010417x|pass|pass|

|primary_m32_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m32_k1_sm_103a_pdl0|0.003648|0.003648|1.000000x|pass|pass|

|primary_m32_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m32_k4_sm_103a_pdl0|0.004992|0.004992|1.000000x|pass|pass|

|primary_m32_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m32_k8_sm_103a_pdl0|0.006273|0.006272|1.000159x|pass|pass|

|primary_m64_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m64_k0_sm_103a_pdl0|0.003200|0.003200|1.000000x|pass|pass|

|primary_m64_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m64_k1_sm_103a_pdl0|0.004032|0.004000|1.008000x|pass|pass|

|primary_m64_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m64_k4_sm_103a_pdl0|0.005600|0.005600|1.000000x|pass|pass|

|primary_m64_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m64_k8_sm_103a_pdl0|0.007233|0.007168|1.009068x|pass|pass|

|primary_m128_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m128_k0_sm_103a_pdl0|0.003712|0.003712|1.000000x|pass|pass|

|primary_m128_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m128_k1_sm_103a_pdl0|0.004672|0.004672|1.000000x|pass|pass|

|primary_m128_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m128_k4_sm_103a_pdl0|0.006560|0.006560|1.000000x|pass|pass|

|primary_m128_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m128_k8_sm_103a_pdl0|0.008384|0.008352|1.003831x|pass|pass|

|primary_m256_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m256_k0_sm_103a_pdl0|0.004736|0.004736|1.000000x|pass|pass|

|primary_m256_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m256_k1_sm_103a_pdl0|0.006272|0.006240|1.005128x|pass|pass|

|primary_m256_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m256_k4_sm_103a_pdl0|0.009760|0.009504|1.026936x|pass|pass|

|primary_m256_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m256_k8_sm_103a_pdl0|0.012736|0.012672|1.005051x|pass|pass|

|primary_m512_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m512_k0_sm_103a_pdl0|0.007073|0.007104|0.995636x|pass|pass|

|primary_m512_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m512_k1_sm_103a_pdl0|0.009856|0.009824|1.003257x|pass|pass|

|primary_m512_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m512_k4_sm_103a_pdl0|0.015008|0.014944|1.004283x|pass|pass|

|primary_m512_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m512_k8_sm_103a_pdl0|0.021472|0.021409|1.002943x|pass|pass|

|primary_m1024_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m1024_k0_sm_103a_pdl0|0.011425|0.011456|0.997294x|pass|pass|

|primary_m1024_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m1024_k1_sm_103a_pdl0|0.015936|0.015936|1.000000x|pass|pass|

|primary_m1024_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m1024_k4_sm_103a_pdl0|0.023873|0.024065|0.992022x|pass|pass|

|primary_m1024_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m1024_k8_sm_103a_pdl0|0.034496|0.034592|0.997239x|pass|pass|

|primary_m2048_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m2048_k0_sm_103a_pdl0|0.021760|0.021792|0.998532x|pass|pass|

|primary_m2048_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m2048_k1_sm_103a_pdl0|0.027168|0.027168|1.000000x|pass|pass|

|primary_m2048_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m2048_k4_sm_103a_pdl0|0.041600|0.041728|0.996933x|pass|pass|

|primary_m2048_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m2048_k8_sm_103a_pdl0|0.062433|0.062529|0.998465x|pass|pass|

|primary_m4096_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m4096_k0_sm_103a_pdl0|0.040033|0.040161|0.996813x|pass|pass|

|primary_m4096_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m4096_k1_sm_103a_pdl0|0.049344|0.049313|1.000629x|pass|pass|

|primary_m4096_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m4096_k4_sm_103a_pdl0|0.075680|0.075905|0.997036x|pass|pass|

|primary_m4096_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m4096_k8_sm_103a_pdl0|0.117313|0.117601|0.997551x|pass|pass|

|primary_m8192_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m8192_k0_sm_103a_pdl0|0.076769|0.076897|0.998335x|pass|pass|

|primary_m8192_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m8192_k1_sm_103a_pdl0|0.094114|0.094209|0.998992x|pass|pass|

|primary_m8192_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m8192_k4_sm_103a_pdl0|0.145345|0.145954|0.995827x|pass|pass|

|primary_m8192_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m8192_k8_sm_103a_pdl0|0.217666|0.217923|0.998823x|pass|pass|

|primary_m16384_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m16384_k0_sm_103a_pdl0|0.147682|0.147906|0.998486x|pass|pass|

|primary_m16384_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m16384_k1_sm_103a_pdl0|0.181091|0.181379|0.998412x|pass|pass|

|primary_m16384_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m16384_k4_sm_103a_pdl0|0.278884|0.279652|0.997254x|pass|pass|

|primary_m16384_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m16384_k8_sm_103a_pdl0|0.418534|0.418853|0.999238x|pass|pass|

|k_sweep_m1_k2__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m1_k2_sm_103a_pdl0|0.003456|0.003424|1.009346x|pass|pass|

|k_sweep_m1_k3__sm_103a__pdl0|G3|kimi_k3_attn_res_k_sweep_m1_k3_sm_103a_pdl0|0.003712|0.003712|1.000000x|pass|pass|

|k_sweep_m1_k5__sm_103a__pdl0|G4|kimi_k3_attn_res_k_sweep_m1_k5_sm_103a_pdl0|0.004416|0.004448|0.992806x|pass|pass|

|k_sweep_m1_k6__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m1_k6_sm_103a_pdl0|0.004480|0.004512|0.992908x|pass|pass|

|k_sweep_m1_k7__sm_103a__pdl0|G3|kimi_k3_attn_res_k_sweep_m1_k7_sm_103a_pdl0|0.004800|0.004768|1.006711x|pass|pass|

|k_sweep_m4096_k2__sm_103a__pdl0|G4|kimi_k3_attn_res_k_sweep_m4096_k2_sm_103a_pdl0|0.059072|0.059073|0.999983x|pass|pass|

|k_sweep_m4096_k3__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m4096_k3_sm_103a_pdl0|0.067393|0.067425|0.999525x|pass|pass|

|k_sweep_m4096_k5__sm_103a__pdl0|G3|kimi_k3_attn_res_k_sweep_m4096_k5_sm_103a_pdl0|0.086401|0.088065|0.981105x|pass|pass|

|k_sweep_m4096_k6__sm_103a__pdl0|G4|kimi_k3_attn_res_k_sweep_m4096_k6_sm_103a_pdl0|0.097985|0.098210|0.997709x|pass|pass|

|k_sweep_m4096_k7__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m4096_k7_sm_103a_pdl0|0.108193|0.108034|1.001472x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_103a__pdl0|G3|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_103a_pdl0|0.004608|0.004608|1.000000x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_103a__pdl0|G4|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_103a_pdl0|0.023009|0.022977|1.001393x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_103a__pdl0|G2|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_103a_pdl0|0.026144|0.026144|1.000000x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_103a__pdl0|G3|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_103a_pdl0|0.009216|0.009216|1.000000x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_103a__pdl0|G4|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_103a_pdl0|0.015489|0.015520|0.998003x|pass|pass|

|primary_m1_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m1_k0_sm_103a_pdl1|0.002592|0.002623|0.988181x|pass|pass|

|primary_m1_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m1_k1_sm_103a_pdl1|0.003232|0.003264|0.990196x|pass|pass|

|primary_m1_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m1_k4_sm_103a_pdl1|0.004288|0.004288|1.000000x|pass|pass|

|primary_m1_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m1_k8_sm_103a_pdl1|0.005152|0.005120|1.006250x|pass|pass|

|primary_m2_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m2_k0_sm_103a_pdl1|0.002656|0.002688|0.988095x|pass|pass|

|primary_m2_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m2_k1_sm_103a_pdl1|0.003264|0.003232|1.009901x|pass|pass|

|primary_m2_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m2_k4_sm_103a_pdl1|0.004256|0.004288|0.992537x|pass|pass|

|primary_m2_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m2_k8_sm_103a_pdl1|0.005216|0.005217|0.999808x|pass|pass|

|primary_m4_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m4_k0_sm_103a_pdl1|0.002688|0.002719|0.988599x|pass|pass|

|primary_m4_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m4_k1_sm_103a_pdl1|0.003232|0.003264|0.990196x|pass|pass|

|primary_m4_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m4_k4_sm_103a_pdl1|0.004384|0.004352|1.007353x|pass|pass|

|primary_m4_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m4_k8_sm_103a_pdl1|0.005312|0.005280|1.006061x|pass|pass|

|primary_m8_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m8_k0_sm_103a_pdl1|0.002752|0.002720|1.011765x|pass|pass|

|primary_m8_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m8_k1_sm_103a_pdl1|0.003296|0.003296|1.000000x|pass|pass|

|primary_m8_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m8_k4_sm_103a_pdl1|0.004512|0.004512|1.000000x|pass|pass|

|primary_m8_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m8_k8_sm_103a_pdl1|0.005472|0.005408|1.011834x|pass|pass|

|primary_m16_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m16_k0_sm_103a_pdl1|0.002944|0.002944|1.000000x|pass|pass|

|primary_m16_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m16_k1_sm_103a_pdl1|0.003488|0.003488|1.000000x|pass|pass|

|primary_m16_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m16_k4_sm_103a_pdl1|0.004673|0.004736|0.986698x|pass|pass|

|primary_m16_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m16_k8_sm_103a_pdl1|0.005728|0.005728|1.000000x|pass|pass|

|primary_m32_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m32_k0_sm_103a_pdl1|0.002975|0.002976|0.999664x|pass|pass|

|primary_m32_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m32_k1_sm_103a_pdl1|0.003648|0.003680|0.991304x|pass|pass|

|primary_m32_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m32_k4_sm_103a_pdl1|0.005023|0.005024|0.999801x|pass|pass|

|primary_m32_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m32_k8_sm_103a_pdl1|0.006272|0.006241|1.004967x|pass|pass|

|primary_m64_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m64_k0_sm_103a_pdl1|0.003232|0.003232|1.000000x|pass|pass|

|primary_m64_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m64_k1_sm_103a_pdl1|0.004032|0.004032|1.000000x|pass|pass|

|primary_m64_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m64_k4_sm_103a_pdl1|0.005537|0.005537|1.000000x|pass|pass|

|primary_m64_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m64_k8_sm_103a_pdl1|0.007232|0.007168|1.008929x|pass|pass|

|primary_m128_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m128_k0_sm_103a_pdl1|0.003680|0.003680|1.000000x|pass|pass|

|primary_m128_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m128_k1_sm_103a_pdl1|0.004640|0.004672|0.993151x|pass|pass|

|primary_m128_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m128_k4_sm_103a_pdl1|0.006560|0.006560|1.000000x|pass|pass|

|primary_m128_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m128_k8_sm_103a_pdl1|0.008384|0.008288|1.011583x|pass|pass|

|primary_m256_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m256_k0_sm_103a_pdl1|0.004769|0.004768|1.000210x|pass|pass|

|primary_m256_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m256_k1_sm_103a_pdl1|0.006272|0.006209|1.010147x|pass|pass|

|primary_m256_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m256_k4_sm_103a_pdl1|0.009664|0.009408|1.027211x|pass|pass|

|primary_m256_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m256_k8_sm_103a_pdl1|0.012672|0.012641|1.002452x|pass|pass|

|primary_m512_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m512_k0_sm_103a_pdl1|0.007105|0.007136|0.995656x|pass|pass|

|primary_m512_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m512_k1_sm_103a_pdl1|0.009953|0.009952|1.000100x|pass|pass|

|primary_m512_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m512_k4_sm_103a_pdl1|0.015136|0.015041|1.006316x|pass|pass|

|primary_m512_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m512_k8_sm_103a_pdl1|0.021569|0.021537|1.001486x|pass|pass|

|primary_m1024_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m1024_k0_sm_103a_pdl1|0.011200|0.011200|1.000000x|pass|pass|

|primary_m1024_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m1024_k1_sm_103a_pdl1|0.015712|0.015712|1.000000x|pass|pass|

|primary_m1024_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m1024_k4_sm_103a_pdl1|0.023616|0.023840|0.990604x|pass|pass|

|primary_m1024_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m1024_k8_sm_103a_pdl1|0.034560|0.034688|0.996310x|pass|pass|

|primary_m2048_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m2048_k0_sm_103a_pdl1|0.021857|0.021921|0.997080x|pass|pass|

|primary_m2048_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m2048_k1_sm_103a_pdl1|0.027040|0.027040|1.000000x|pass|pass|

|primary_m2048_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m2048_k4_sm_103a_pdl1|0.041185|0.041408|0.994615x|pass|pass|

|primary_m2048_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m2048_k8_sm_103a_pdl1|0.062337|0.062561|0.996419x|pass|pass|

|primary_m4096_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m4096_k0_sm_103a_pdl1|0.039969|0.040128|0.996038x|pass|pass|

|primary_m4096_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m4096_k1_sm_103a_pdl1|0.049120|0.049121|0.999980x|pass|pass|

|primary_m4096_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m4096_k4_sm_103a_pdl1|0.075841|0.076065|0.997055x|pass|pass|

|primary_m4096_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m4096_k8_sm_103a_pdl1|0.116737|0.116993|0.997812x|pass|pass|

|primary_m8192_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m8192_k0_sm_103a_pdl1|0.076737|0.076897|0.997919x|pass|pass|

|primary_m8192_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m8192_k1_sm_103a_pdl1|0.094017|0.093985|1.000340x|pass|pass|

|primary_m8192_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m8192_k4_sm_103a_pdl1|0.145761|0.146274|0.996493x|pass|pass|

|primary_m8192_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m8192_k8_sm_103a_pdl1|0.218082|0.218178|0.999560x|pass|pass|

|primary_m16384_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m16384_k0_sm_103a_pdl1|0.148034|0.148226|0.998705x|pass|pass|

|primary_m16384_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m16384_k1_sm_103a_pdl1|0.181218|0.181442|0.998765x|pass|pass|

|primary_m16384_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m16384_k4_sm_103a_pdl1|0.279108|0.279940|0.997028x|pass|pass|

|primary_m16384_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m16384_k8_sm_103a_pdl1|0.418406|0.418726|0.999236x|pass|pass|

|k_sweep_m1_k2__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m1_k2_sm_103a_pdl1|0.003424|0.003424|1.000000x|pass|pass|

|k_sweep_m1_k3__sm_103a__pdl1|G3|kimi_k3_attn_res_k_sweep_m1_k3_sm_103a_pdl1|0.003680|0.003712|0.991379x|pass|pass|

|k_sweep_m1_k5__sm_103a__pdl1|G4|kimi_k3_attn_res_k_sweep_m1_k5_sm_103a_pdl1|0.004416|0.004416|1.000000x|pass|pass|

|k_sweep_m1_k6__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m1_k6_sm_103a_pdl1|0.004512|0.004512|1.000000x|pass|pass|

|k_sweep_m1_k7__sm_103a__pdl1|G3|kimi_k3_attn_res_k_sweep_m1_k7_sm_103a_pdl1|0.004832|0.004800|1.006667x|pass|pass|

|k_sweep_m4096_k2__sm_103a__pdl1|G4|kimi_k3_attn_res_k_sweep_m4096_k2_sm_103a_pdl1|0.059265|0.059201|1.001081x|pass|pass|

|k_sweep_m4096_k3__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m4096_k3_sm_103a_pdl1|0.066977|0.066977|1.000000x|pass|pass|

|k_sweep_m4096_k5__sm_103a__pdl1|G3|kimi_k3_attn_res_k_sweep_m4096_k5_sm_103a_pdl1|0.086306|0.087937|0.981453x|pass|pass|

|k_sweep_m4096_k6__sm_103a__pdl1|G4|kimi_k3_attn_res_k_sweep_m4096_k6_sm_103a_pdl1|0.098082|0.098337|0.997407x|pass|pass|

|k_sweep_m4096_k7__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m4096_k7_sm_103a_pdl1|0.108609|0.108417|1.001771x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_103a__pdl1|G3|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_103a_pdl1|0.004769|0.004800|0.993542x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_103a__pdl1|G4|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_103a_pdl1|0.023169|0.023169|1.000000x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_103a__pdl1|G2|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_103a_pdl1|0.025760|0.025856|0.996287x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_103a__pdl1|G3|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_103a_pdl1|0.009280|0.009249|1.003352x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_103a__pdl1|G4|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_103a_pdl1|0.015552|0.015520|1.002062x|pass|pass|

## Per-shape comparison: pinned vLLM SM100f native CUDA AttnRes op
(csrc/libtorch_stable/kimi_k3/attn_res_kernel.cu)

|Shape|Baseline ms|Paired export ms|Baseline / Export|
|---|---:|---:|---:|
|primary_m1_k0__sm_100a__pdl0|0.004127|0.002720|1.517279x|
|primary_m1_k1__sm_100a__pdl0|0.004448|0.003520|1.263636x|
|primary_m1_k4__sm_100a__pdl0|0.005216|0.004416|1.181159x|
|primary_m1_k8__sm_100a__pdl0|0.006272|0.005536|1.132948x|
|primary_m2_k0__sm_100a__pdl0|0.004127|0.002784|1.482399x|
|primary_m2_k1__sm_100a__pdl0|0.004384|0.003360|1.304762x|
|primary_m2_k4__sm_100a__pdl0|0.005280|0.004416|1.195652x|
|primary_m2_k8__sm_100a__pdl0|0.006336|0.005409|1.171381x|
|primary_m4_k0__sm_100a__pdl0|0.004064|0.002688|1.511905x|
|primary_m4_k1__sm_100a__pdl0|0.004416|0.003424|1.289720x|
|primary_m4_k4__sm_100a__pdl0|0.005344|0.004480|1.192857x|
|primary_m4_k8__sm_100a__pdl0|0.006336|0.005633|1.124800x|
|primary_m8_k0__sm_100a__pdl0|0.004160|0.002880|1.444444x|
|primary_m8_k1__sm_100a__pdl0|0.004513|0.003584|1.259208x|
|primary_m8_k4__sm_100a__pdl0|0.005440|0.004607|1.180812x|
|primary_m8_k8__sm_100a__pdl0|0.006432|0.005727|1.123101x|
|primary_m16_k0__sm_100a__pdl0|0.004224|0.002912|1.450549x|
|primary_m16_k1__sm_100a__pdl0|0.004640|0.003616|1.283186x|
|primary_m16_k4__sm_100a__pdl0|0.005600|0.004736|1.182432x|
|primary_m16_k8__sm_100a__pdl0|0.006720|0.005952|1.129032x|
|primary_m32_k0__sm_100a__pdl0|0.004256|0.002977|1.429627x|
|primary_m32_k1__sm_100a__pdl0|0.004768|0.003776|1.262712x|
|primary_m32_k4__sm_100a__pdl0|0.005888|0.004960|1.187097x|
|primary_m32_k8__sm_100a__pdl0|0.007135|0.006528|1.092984x|
|primary_m64_k0__sm_100a__pdl0|0.004575|0.003232|1.415532x|
|primary_m64_k1__sm_100a__pdl0|0.005120|0.004160|1.230769x|
|primary_m64_k4__sm_100a__pdl0|0.006560|0.005600|1.171429x|
|primary_m64_k8__sm_100a__pdl0|0.007871|0.007424|1.060210x|
|primary_m128_k0__sm_100a__pdl0|0.005024|0.003743|1.342239x|
|primary_m128_k1__sm_100a__pdl0|0.005728|0.004736|1.209459x|
|primary_m128_k4__sm_100a__pdl0|0.007456|0.006592|1.131068x|
|primary_m128_k8__sm_100a__pdl0|0.008704|0.008608|1.011152x|
|primary_m256_k0__sm_100a__pdl0|0.006720|0.004832|1.390728x|
|primary_m256_k1__sm_100a__pdl0|0.008000|0.006464|1.237624x|
|primary_m256_k4__sm_100a__pdl0|0.010016|0.009920|1.009677x|
|primary_m256_k8__sm_100a__pdl0|0.012896|0.012448|1.035990x|
|primary_m512_k0__sm_100a__pdl0|0.008800|0.007648|1.150628x|
|primary_m512_k1__sm_100a__pdl0|0.011072|0.010144|1.091483x|
|primary_m512_k4__sm_100a__pdl0|0.015392|0.015008|1.025586x|
|primary_m512_k8__sm_100a__pdl0|0.021919|0.021024|1.042570x|
|primary_m1024_k0__sm_100a__pdl0|0.013088|0.011457|1.142358x|
|primary_m1024_k1__sm_100a__pdl0|0.015809|0.015360|1.029232x|
|primary_m1024_k4__sm_100a__pdl0|0.023968|0.023329|1.027391x|
|primary_m1024_k8__sm_100a__pdl0|0.036255|0.033728|1.074923x|
|primary_m2048_k0__sm_100a__pdl0|0.022497|0.021407|1.050918x|
|primary_m2048_k1__sm_100a__pdl0|0.027200|0.026656|1.020408x|
|primary_m2048_k4__sm_100a__pdl0|0.043040|0.040640|1.059055x|
|primary_m2048_k8__sm_100a__pdl0|0.064575|0.061536|1.049386x|
|primary_m4096_k0__sm_100a__pdl0|0.040176|0.039167|1.025749x|
|primary_m4096_k1__sm_100a__pdl0|0.049727|0.048960|1.015666x|
|primary_m4096_k4__sm_100a__pdl0|0.079088|0.076352|1.035834x|
|primary_m4096_k8__sm_100a__pdl0|0.118655|0.115008|1.031711x|
|primary_m8192_k0__sm_100a__pdl0|0.075200|0.074144|1.014243x|
|primary_m8192_k1__sm_100a__pdl0|0.093535|0.092512|1.011058x|
|primary_m8192_k4__sm_100a__pdl0|0.148736|0.143584|1.035881x|
|primary_m8192_k8__sm_100a__pdl0|0.225471|0.213887|1.054159x|
|primary_m16384_k0__sm_100a__pdl0|0.145600|0.144384|1.008422x|
|primary_m16384_k1__sm_100a__pdl0|0.181440|0.178719|1.015225x|
|primary_m16384_k4__sm_100a__pdl0|0.286303|0.274079|1.044600x|
|primary_m16384_k8__sm_100a__pdl0|0.435839|0.413631|1.053690x|
|k_sweep_m1_k2__sm_100a__pdl0|0.004640|0.003584|1.294643x|
|k_sweep_m1_k3__sm_100a__pdl0|0.005120|0.003968|1.290323x|
|k_sweep_m1_k5__sm_100a__pdl0|0.005472|0.004640|1.179310x|
|k_sweep_m1_k6__sm_100a__pdl0|0.005856|0.004960|1.180645x|
|k_sweep_m1_k7__sm_100a__pdl0|0.006112|0.004960|1.232258x|
|k_sweep_m4096_k2__sm_100a__pdl0|0.059328|0.058624|1.012009x|
|k_sweep_m4096_k3__sm_100a__pdl0|0.072960|0.067200|1.085714x|
|k_sweep_m4096_k5__sm_100a__pdl0|0.087744|0.084992|1.032380x|
|k_sweep_m4096_k6__sm_100a__pdl0|0.102016|0.095775|1.065163x|
|k_sweep_m4096_k7__sm_100a__pdl0|0.109760|0.106400|1.031579x|
|primary_m1_k0__sm_100a__pdl1|0.004064|0.002687|1.512467x|
|primary_m1_k1__sm_100a__pdl1|0.004417|0.003520|1.254830x|
|primary_m1_k4__sm_100a__pdl1|0.005185|0.004447|1.165955x|
|primary_m1_k8__sm_100a__pdl1|0.006240|0.005504|1.133721x|
|primary_m2_k0__sm_100a__pdl1|0.004128|0.002784|1.482759x|
|primary_m2_k1__sm_100a__pdl1|0.004384|0.003360|1.304762x|
|primary_m2_k4__sm_100a__pdl1|0.005184|0.004448|1.165468x|
|primary_m2_k8__sm_100a__pdl1|0.006335|0.005439|1.164736x|
|primary_m4_k0__sm_100a__pdl1|0.004097|0.002689|1.523615x|
|primary_m4_k1__sm_100a__pdl1|0.004416|0.003391|1.302271x|
|primary_m4_k4__sm_100a__pdl1|0.005376|0.004480|1.200000x|
|primary_m4_k8__sm_100a__pdl1|0.006304|0.005664|1.112994x|
|primary_m8_k0__sm_100a__pdl1|0.004128|0.002848|1.449438x|
|primary_m8_k1__sm_100a__pdl1|0.004512|0.003584|1.258929x|
|primary_m8_k4__sm_100a__pdl1|0.005376|0.004576|1.174825x|
|primary_m8_k8__sm_100a__pdl1|0.006432|0.005633|1.141843x|
|primary_m16_k0__sm_100a__pdl1|0.004256|0.002880|1.477778x|
|primary_m16_k1__sm_100a__pdl1|0.004609|0.003616|1.274613x|
|primary_m16_k4__sm_100a__pdl1|0.005600|0.004737|1.182183x|
|primary_m16_k8__sm_100a__pdl1|0.006720|0.005952|1.129032x|
|primary_m32_k0__sm_100a__pdl1|0.004320|0.003040|1.421053x|
|primary_m32_k1__sm_100a__pdl1|0.004768|0.003839|1.241990x|
|primary_m32_k4__sm_100a__pdl1|0.006016|0.005120|1.175000x|
|primary_m32_k8__sm_100a__pdl1|0.007072|0.006464|1.094059x|
|primary_m64_k0__sm_100a__pdl1|0.004544|0.003232|1.405941x|
|primary_m64_k1__sm_100a__pdl1|0.005184|0.004160|1.246154x|
|primary_m64_k4__sm_100a__pdl1|0.006592|0.005664|1.163842x|
|primary_m64_k8__sm_100a__pdl1|0.007872|0.007456|1.055794x|
|primary_m128_k0__sm_100a__pdl1|0.004993|0.003712|1.345097x|
|primary_m128_k1__sm_100a__pdl1|0.005792|0.004800|1.206667x|
|primary_m128_k4__sm_100a__pdl1|0.007520|0.006624|1.135266x|
|primary_m128_k8__sm_100a__pdl1|0.008672|0.008640|1.003704x|
|primary_m256_k0__sm_100a__pdl1|0.006656|0.004768|1.395973x|
|primary_m256_k1__sm_100a__pdl1|0.008000|0.006240|1.282051x|
|primary_m256_k4__sm_100a__pdl1|0.010080|0.009984|1.009615x|
|primary_m256_k8__sm_100a__pdl1|0.012992|0.012608|1.030457x|
|primary_m512_k0__sm_100a__pdl1|0.008832|0.007616|1.159664x|
|primary_m512_k1__sm_100a__pdl1|0.010975|0.010079|1.088898x|
|primary_m512_k4__sm_100a__pdl1|0.015360|0.015040|1.021277x|
|primary_m512_k8__sm_100a__pdl1|0.022016|0.021248|1.036145x|
|primary_m1024_k0__sm_100a__pdl1|0.013280|0.011488|1.155989x|
|primary_m1024_k1__sm_100a__pdl1|0.015744|0.015296|1.029289x|
|primary_m1024_k4__sm_100a__pdl1|0.024128|0.023424|1.030055x|
|primary_m1024_k8__sm_100a__pdl1|0.036255|0.033824|1.071872x|
|primary_m2048_k0__sm_100a__pdl1|0.022304|0.021312|1.046522x|
|primary_m2048_k1__sm_100a__pdl1|0.027584|0.026912|1.024970x|
|primary_m2048_k4__sm_100a__pdl1|0.043199|0.040416|1.068859x|
|primary_m2048_k8__sm_100a__pdl1|0.064639|0.061216|1.055917x|
|primary_m4096_k0__sm_100a__pdl1|0.040224|0.039168|1.026961x|
|primary_m4096_k1__sm_100a__pdl1|0.049440|0.048703|1.015133x|
|primary_m4096_k4__sm_100a__pdl1|0.078847|0.075487|1.044504x|
|primary_m4096_k8__sm_100a__pdl1|0.118880|0.114976|1.033955x|
|primary_m8192_k0__sm_100a__pdl1|0.075295|0.074112|1.015962x|
|primary_m8192_k1__sm_100a__pdl1|0.093439|0.092736|1.007581x|
|primary_m8192_k4__sm_100a__pdl1|0.148383|0.142528|1.041080x|
|primary_m8192_k8__sm_100a__pdl1|0.225311|0.214591|1.049955x|
|primary_m16384_k0__sm_100a__pdl1|0.145504|0.144288|1.008428x|
|primary_m16384_k1__sm_100a__pdl1|0.179584|0.177407|1.012271x|
|primary_m16384_k4__sm_100a__pdl1|0.286335|0.274815|1.041919x|
|primary_m16384_k8__sm_100a__pdl1|0.435296|0.413664|1.052294x|
|k_sweep_m1_k2__sm_100a__pdl1|0.004608|0.003552|1.297297x|
|k_sweep_m1_k3__sm_100a__pdl1|0.005088|0.003936|1.292683x|
|k_sweep_m1_k5__sm_100a__pdl1|0.005440|0.004672|1.164384x|
|k_sweep_m1_k6__sm_100a__pdl1|0.005824|0.004928|1.181818x|
|k_sweep_m1_k7__sm_100a__pdl1|0.006112|0.004960|1.232258x|
|k_sweep_m4096_k2__sm_100a__pdl1|0.060640|0.060127|1.008532x|
|k_sweep_m4096_k3__sm_100a__pdl1|0.072832|0.067136|1.084843x|
|k_sweep_m4096_k5__sm_100a__pdl1|0.087711|0.084831|1.033950x|
|k_sweep_m4096_k6__sm_100a__pdl1|0.101920|0.095328|1.069151x|
|k_sweep_m4096_k7__sm_100a__pdl1|0.109887|0.106336|1.033394x|
|primary_m1_k0__sm_103a__pdl0|0.003808|0.002592|1.469136x|
|primary_m1_k1__sm_103a__pdl0|0.004192|0.003296|1.271845x|
|primary_m1_k4__sm_103a__pdl0|0.004960|0.004320|1.148148x|
|primary_m1_k8__sm_103a__pdl0|0.005984|0.005089|1.175870x|
|primary_m2_k0__sm_103a__pdl0|0.003872|0.002688|1.440476x|
|primary_m2_k1__sm_103a__pdl0|0.004192|0.003264|1.284314x|
|primary_m2_k4__sm_103a__pdl0|0.004960|0.004288|1.156716x|
|primary_m2_k8__sm_103a__pdl0|0.006048|0.005248|1.152439x|
|primary_m4_k0__sm_103a__pdl0|0.003872|0.002688|1.440476x|
|primary_m4_k1__sm_103a__pdl0|0.004160|0.003263|1.274900x|
|primary_m4_k4__sm_103a__pdl0|0.005023|0.004384|1.145757x|
|primary_m4_k8__sm_103a__pdl0|0.006112|0.005344|1.143713x|
|primary_m8_k0__sm_103a__pdl0|0.003904|0.002752|1.418605x|
|primary_m8_k1__sm_103a__pdl0|0.004256|0.003328|1.278846x|
|primary_m8_k4__sm_103a__pdl0|0.005120|0.004512|1.134752x|
|primary_m8_k8__sm_103a__pdl0|0.006144|0.005377|1.142645x|
|primary_m16_k0__sm_103a__pdl0|0.004032|0.002912|1.384615x|
|primary_m16_k1__sm_103a__pdl0|0.004320|0.003488|1.238532x|
|primary_m16_k4__sm_103a__pdl0|0.005248|0.004704|1.115646x|
|primary_m16_k8__sm_103a__pdl0|0.006336|0.005633|1.124800x|
|primary_m32_k0__sm_103a__pdl0|0.004064|0.002976|1.365591x|
|primary_m32_k1__sm_103a__pdl0|0.004480|0.003648|1.228070x|
|primary_m32_k4__sm_103a__pdl0|0.005696|0.004992|1.141026x|
|primary_m32_k8__sm_103a__pdl0|0.006817|0.006272|1.086894x|
|primary_m64_k0__sm_103a__pdl0|0.004320|0.003200|1.350000x|
|primary_m64_k1__sm_103a__pdl0|0.004929|0.004000|1.232250x|
|primary_m64_k4__sm_103a__pdl0|0.006336|0.005600|1.131429x|
|primary_m64_k8__sm_103a__pdl0|0.007457|0.007168|1.040318x|
|primary_m128_k0__sm_103a__pdl0|0.004768|0.003712|1.284483x|
|primary_m128_k1__sm_103a__pdl0|0.005537|0.004672|1.185146x|
|primary_m128_k4__sm_103a__pdl0|0.007264|0.006560|1.107317x|
|primary_m128_k8__sm_103a__pdl0|0.008448|0.008352|1.011494x|
|primary_m256_k0__sm_103a__pdl0|0.006463|0.004736|1.364654x|
|primary_m256_k1__sm_103a__pdl0|0.007712|0.006240|1.235897x|
|primary_m256_k4__sm_103a__pdl0|0.009792|0.009504|1.030303x|
|primary_m256_k8__sm_103a__pdl0|0.012800|0.012672|1.010101x|
|primary_m512_k0__sm_103a__pdl0|0.008736|0.007104|1.229730x|
|primary_m512_k1__sm_103a__pdl0|0.010400|0.009824|1.058632x|
|primary_m512_k4__sm_103a__pdl0|0.015264|0.014944|1.021413x|
|primary_m512_k8__sm_103a__pdl0|0.021825|0.021409|1.019431x|
|primary_m1024_k0__sm_103a__pdl0|0.013152|0.011456|1.148045x|
|primary_m1024_k1__sm_103a__pdl0|0.015968|0.015936|1.002008x|
|primary_m1024_k4__sm_103a__pdl0|0.024544|0.024065|1.019904x|
|primary_m1024_k8__sm_103a__pdl0|0.036544|0.034592|1.056429x|
|primary_m2048_k0__sm_103a__pdl0|0.022464|0.021792|1.030837x|
|primary_m2048_k1__sm_103a__pdl0|0.027232|0.027168|1.002356x|
|primary_m2048_k4__sm_103a__pdl0|0.044129|0.041728|1.057539x|
|primary_m2048_k8__sm_103a__pdl0|0.065025|0.062529|1.039917x|
|primary_m4096_k0__sm_103a__pdl0|0.040672|0.040161|1.012724x|
|primary_m4096_k1__sm_103a__pdl0|0.049281|0.049313|0.999351x|
|primary_m4096_k4__sm_103a__pdl0|0.080289|0.075905|1.057756x|
|primary_m4096_k8__sm_103a__pdl0|0.119265|0.117601|1.014150x|
|primary_m8192_k0__sm_103a__pdl0|0.077568|0.076897|1.008726x|
|primary_m8192_k1__sm_103a__pdl0|0.094177|0.094209|0.999666x|
|primary_m8192_k4__sm_103a__pdl0|0.150818|0.145954|1.033326x|
|primary_m8192_k8__sm_103a__pdl0|0.225123|0.217923|1.033042x|
|primary_m16384_k0__sm_103a__pdl0|0.148290|0.147906|1.002596x|
|primary_m16384_k1__sm_103a__pdl0|0.182978|0.181379|1.008816x|
|primary_m16384_k4__sm_103a__pdl0|0.290692|0.279652|1.039478x|
|primary_m16384_k8__sm_103a__pdl0|0.436422|0.418853|1.041946x|
|k_sweep_m1_k2__sm_103a__pdl0|0.004352|0.003424|1.271028x|
|k_sweep_m1_k3__sm_103a__pdl0|0.004705|0.003712|1.267511x|
|k_sweep_m1_k5__sm_103a__pdl0|0.005152|0.004448|1.158273x|
|k_sweep_m1_k6__sm_103a__pdl0|0.005600|0.004512|1.241135x|
|k_sweep_m1_k7__sm_103a__pdl0|0.005792|0.004768|1.214765x|
|k_sweep_m4096_k2__sm_103a__pdl0|0.059201|0.059073|1.002167x|
|k_sweep_m4096_k3__sm_103a__pdl0|0.073633|0.067425|1.092073x|
|k_sweep_m4096_k5__sm_103a__pdl0|0.088257|0.088065|1.002180x|
|k_sweep_m4096_k6__sm_103a__pdl0|0.102401|0.098210|1.042674x|
|k_sweep_m4096_k7__sm_103a__pdl0|0.110433|0.108034|1.022206x|
|primary_m1_k0__sm_103a__pdl1|0.003808|0.002623|1.451773x|
|primary_m1_k1__sm_103a__pdl1|0.004192|0.003264|1.284314x|
|primary_m1_k4__sm_103a__pdl1|0.004992|0.004288|1.164179x|
|primary_m1_k8__sm_103a__pdl1|0.005984|0.005120|1.168750x|
|primary_m2_k0__sm_103a__pdl1|0.003872|0.002688|1.440476x|
|primary_m2_k1__sm_103a__pdl1|0.004192|0.003232|1.297030x|
|primary_m2_k4__sm_103a__pdl1|0.004928|0.004288|1.149254x|
|primary_m2_k8__sm_103a__pdl1|0.006048|0.005217|1.159287x|
|primary_m4_k0__sm_103a__pdl1|0.003872|0.002719|1.424053x|
|primary_m4_k1__sm_103a__pdl1|0.004160|0.003264|1.274510x|
|primary_m4_k4__sm_103a__pdl1|0.004992|0.004352|1.147059x|
|primary_m4_k8__sm_103a__pdl1|0.006112|0.005280|1.157576x|
|primary_m8_k0__sm_103a__pdl1|0.003872|0.002720|1.423529x|
|primary_m8_k1__sm_103a__pdl1|0.004192|0.003296|1.271845x|
|primary_m8_k4__sm_103a__pdl1|0.005120|0.004512|1.134752x|
|primary_m8_k8__sm_103a__pdl1|0.006176|0.005408|1.142012x|
|primary_m16_k0__sm_103a__pdl1|0.004032|0.002944|1.369565x|
|primary_m16_k1__sm_103a__pdl1|0.004288|0.003488|1.229358x|
|primary_m16_k4__sm_103a__pdl1|0.005280|0.004736|1.114865x|
|primary_m16_k8__sm_103a__pdl1|0.006400|0.005728|1.117318x|
|primary_m32_k0__sm_103a__pdl1|0.004096|0.002976|1.376344x|
|primary_m32_k1__sm_103a__pdl1|0.004480|0.003680|1.217391x|
|primary_m32_k4__sm_103a__pdl1|0.005697|0.005024|1.133957x|
|primary_m32_k8__sm_103a__pdl1|0.006880|0.006241|1.102387x|
|primary_m64_k0__sm_103a__pdl1|0.004320|0.003232|1.336634x|
|primary_m64_k1__sm_103a__pdl1|0.004928|0.004032|1.222222x|
|primary_m64_k4__sm_103a__pdl1|0.006304|0.005537|1.138523x|
|primary_m64_k8__sm_103a__pdl1|0.007552|0.007168|1.053571x|
|primary_m128_k0__sm_103a__pdl1|0.004800|0.003680|1.304348x|
|primary_m128_k1__sm_103a__pdl1|0.005536|0.004672|1.184932x|
|primary_m128_k4__sm_103a__pdl1|0.007296|0.006560|1.112195x|
|primary_m128_k8__sm_103a__pdl1|0.008449|0.008288|1.019426x|
|primary_m256_k0__sm_103a__pdl1|0.006528|0.004768|1.369128x|
|primary_m256_k1__sm_103a__pdl1|0.007776|0.006209|1.252376x|
|primary_m256_k4__sm_103a__pdl1|0.009729|0.009408|1.034120x|
|primary_m256_k8__sm_103a__pdl1|0.012736|0.012641|1.007515x|
|primary_m512_k0__sm_103a__pdl1|0.008832|0.007136|1.237668x|
|primary_m512_k1__sm_103a__pdl1|0.010625|0.009952|1.067625x|
|primary_m512_k4__sm_103a__pdl1|0.015424|0.015041|1.025464x|
|primary_m512_k8__sm_103a__pdl1|0.021824|0.021537|1.013326x|
|primary_m1024_k0__sm_103a__pdl1|0.013184|0.011200|1.177143x|
|primary_m1024_k1__sm_103a__pdl1|0.016001|0.015712|1.018394x|
|primary_m1024_k4__sm_103a__pdl1|0.024416|0.023840|1.024161x|
|primary_m1024_k8__sm_103a__pdl1|0.036320|0.034688|1.047048x|
|primary_m2048_k0__sm_103a__pdl1|0.022592|0.021921|1.030610x|
|primary_m2048_k1__sm_103a__pdl1|0.027424|0.027040|1.014201x|
|primary_m2048_k4__sm_103a__pdl1|0.044033|0.041408|1.063394x|
|primary_m2048_k8__sm_103a__pdl1|0.065185|0.062561|1.041943x|
|primary_m4096_k0__sm_103a__pdl1|0.040672|0.040128|1.013557x|
|primary_m4096_k1__sm_103a__pdl1|0.049409|0.049121|1.005863x|
|primary_m4096_k4__sm_103a__pdl1|0.080161|0.076065|1.053849x|
|primary_m4096_k8__sm_103a__pdl1|0.119201|0.116993|1.018873x|
|primary_m8192_k0__sm_103a__pdl1|0.077665|0.076897|1.009987x|
|primary_m8192_k1__sm_103a__pdl1|0.094177|0.093985|1.002043x|
|primary_m8192_k4__sm_103a__pdl1|0.151106|0.146274|1.033034x|
|primary_m8192_k8__sm_103a__pdl1|0.225634|0.218178|1.034174x|
|primary_m16384_k0__sm_103a__pdl1|0.148546|0.148226|1.002159x|
|primary_m16384_k1__sm_103a__pdl1|0.183234|0.181442|1.009876x|
|primary_m16384_k4__sm_103a__pdl1|0.290852|0.279940|1.038980x|
|primary_m16384_k8__sm_103a__pdl1|0.436806|0.418726|1.043179x|
|k_sweep_m1_k2__sm_103a__pdl1|0.004320|0.003424|1.261682x|
|k_sweep_m1_k3__sm_103a__pdl1|0.004736|0.003712|1.275862x|
|k_sweep_m1_k5__sm_103a__pdl1|0.005120|0.004416|1.159420x|
|k_sweep_m1_k6__sm_103a__pdl1|0.005568|0.004512|1.234043x|
|k_sweep_m1_k7__sm_103a__pdl1|0.005760|0.004800|1.200000x|
|k_sweep_m4096_k2__sm_103a__pdl1|0.059345|0.059201|1.002424x|
|k_sweep_m4096_k3__sm_103a__pdl1|0.073665|0.066977|1.099855x|
|k_sweep_m4096_k5__sm_103a__pdl1|0.088192|0.087937|1.002900x|
|k_sweep_m4096_k6__sm_103a__pdl1|0.102785|0.098337|1.045232x|
|k_sweep_m4096_k7__sm_103a__pdl1|0.110657|0.108417|1.020661x|

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|300|300|0.012676|0.012686|0.999208x|
|correctness|20|20|0.013343|0.013380|0.997192x|
|full_k_sweep|72|72|0.017204|0.017232|0.998363x|
|pdl_off|150|150|0.012676|0.012685|0.999263x|
|pdl_on|150|150|0.012676|0.012687|0.999154x|
|perf|280|280|0.012630|0.012638|0.999353x|
|primary_geomean|240|240|0.011840|0.011848|0.999372x|

### Geomeans: pinned vLLM SM100f native CUDA AttnRes op
(csrc/libtorch_stable/kimi_k3/attn_res_kernel.cu)

|Shape tag|Timed rows|Denominator|Baseline ms|Paired export ms|Baseline
/ Export|
|---|---:|---:|---:|---:|---:|
|all|280|280|0.014458|0.012638|1.144007x|
|full_k_sweep|72|72|0.019535|0.017232|1.133630x|
|pdl_off|140|140|0.014455|0.012640|1.143542x|
|pdl_on|140|140|0.014461|0.012636|1.144473x|
|perf|280|280|0.014458|0.012638|1.144007x|
|primary_geomean|240|240|0.013580|0.011848|1.146239x|

Complete denominator: **true** (300/300).

All gates passed: **true** (300/300).
## What changed in this revision

Baseline PR: #5994 (small-M kernel-structure round). This PR regenerates
the Kimi-K3 AttnRes programs after a routing round over all
token counts: the one-token-per-CTA kernel introduced by #5994
(register-resident sources, no TMA / mbarrier / TMEM) now also serves
the mid-size token counts where it measured faster than the persistent
and native programs on the same GPU, and the two-CTA cluster
variant covers the smallest of those counts for K >= 5. The host policy
in `cake_backend.py` selects the program per architecture, K
and M band: direct kernel up to M 256 / 512 for K 0-3 (512 for K0 on
SM103 and K1 on both), up to M 128 for K 4-7 and M 64 for K8;
two-CTA split at M <= 32 for K 6 / 7 (SM103 also K5) and M <= 64 for K8.
The programs above those bands and all kernel math are
unchanged.

Same-GPU paired measurement against the #5994 programs (two interleaved
blocks per row; ratio new / previous, both PDL modes):

| arch | cells | ratio range |
|---|---|---|
| SM100 | M 32 / 64 / 128, every K | 0.81-0.99 (K0-K7 0.81-0.93, K8
0.94-0.99) |
| SM100 | M 256 (K0-K3), M 512 (K1) | 0.83-0.98 |
| SM103 | M 32 / 64 / 128, every K | 0.82-0.99 (K0-K7 0.82-0.93, K8
0.92-0.99) |
| SM103 | M 256 (K0-K3), M 512 (K0, K1) | 0.82-0.99 |

Every re-routed cell is bit-identical to the program it replaces (the
K5-K7 cells chunk their online softmax like the persistent
program; `out` and the in-place state compared element-wise). Rows whose
program is unchanged are re-frozen with the generator:
300 / 300 rows complete and passed (sm_100a 150 rows on 3x B200, sm_103a
150 rows on 3x B300, closed out with the sm_103a results as the sealed
prior; parity `source / export` geomean 0.9992). Correctness: FP32
reference within atol 0.08 / rtol 0.03 on every row, in-place state
bit-exact,
compute-sanitizer synccheck and memcheck clean on the direct and cluster
programs at the new token counts.

Large token counts (M >= 512) were measured against `torch.add` /
`torch.clone` over the same byte count on the same GPU: every
exported row runs at or under the torch-add time (max ratio 0.986 on
SM100, 0.995 on SM103), 6.0-6.9 TB/s at M >= 4096.


## Baselines and their source PRs

- **Cake production AttnRes launcher** (parity arm, `source / export`
ratios): the same generated programs launched through the Cake
production dispatcher at the producer revision recorded in the summary.
- **vLLM native CUDA AttnRes op** (external baseline, `baseline /
export` ratios): `csrc/libtorch_stable/kimi_k3/attn_res_kernel.cu` from
https://github.com/vllm-project/vllm at revision
`ee3c00bbf47e0ef7e975705cc980b06ee5576bb0`, built from source on the
measuring node:
- vllm-project/vllm#50090 (`61ac3680`, 2026-07-28) — add AttnRes kernels
- vllm-project/vllm#50567 (`41ba11b8`, 2026-08-04) — enforce packed rows
and op availability in AttnRes dispatch
- vllm-project/vllm#50185 (`7b4ed496`, 2026-08-06) — attn_res kernel
latency improvements
- vllm-project/vllm#54261 (`d6d66585`, 2026-08-31) — make native CUDA
AttnRes the SM100 default
- **Correctness oracle**: FP32 PyTorch reference of the AttnRes op (BF16
outputs checked at atol 0.08 / rtol 0.03; in-place state bit-exact),
applied to source, export and vLLM arms before and after each timing
block.

## Acceptance

Every perf row must satisfy `vLLM / export >= 0.97` (owner decision
2026-10-01). Final measurement at Cake producer `dfa1b856faf` against
this scaffold (`49ca49a216f`, now `7f0c200b55e` after the rebase;
sm_100a on 3x B200, sm_103a on 3x B300): 300 / 300 rows pass; the lowest
perf-row `vLLM / export` is 0.999 (`primary_m4096_k1`, SM103, PDL off;
1.001 in the previous delivery).

| row | vLLM / export | previous delivery |
|---|---:|---:|
| primary_m4096_k1, SM103, PDL off | 0.999 | 1.001 |

Geomean of `vLLM / export` over the perf rows: 1.151 (SM100) / 1.137
(SM103) (previous delivery 1.139 / 1.109). Programs outside the
re-routed bands are byte-identical to #5994's: the only new generated
program is the K4 direct kernel for M 17-128, four persistent K1
programs that served only re-routed rows are removed, and no other
kernel or binding file changes. Their row-to-row movement against the
previous delivery is the node spread of the two measurements (the SM100
node ran the 3-6 us one-token rows 1-7 % slower for every K, including K
whose programs did not change; SM103 0.91-1.03).

Generated kernel files: 48 programs, 98 files (51 programs before: +1 K4
direct, -4 persistent K1); PDL stays a launch argument;
architecture-identical programs stay shared; the slop audit lists only
NUM_BLOCKS clones.

## CI

```
/bot run tests/experimental/test_cake_kimi_k3_attn_res.py
@flashinfer-bot run tests/experimental/test_cake_kimi_k3_attn_res.py
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance Improvements**
* Expanded small-sequence routing thresholds for selected hardware and
configurations, with updated chunk sizes and cluster choices.
  * Adjusted execution settings for selected workloads.

* **Reliability**
* When a selected schedule is unavailable, routing can use a registered
alternative from the same schedule family. Exact measured schedules
remain unchanged.

* **Documentation**
* Updated routing guidance with configuration-specific limits and
fallback behavior.

* **Tests**
* Expanded coverage for routing choices, chunk-size boundaries, and
registered-schedule fallbacks.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f62ffa9](https://github.com/flashinfer-ai/flashinfer/commit/f62ffa92a12b259bdd2cf9de0672438b17ad66e1)

- **作者**: eigen
- **时间**: 2026-10-04T17:49:26Z
- **提交信息**: feat(cake_minimax_h3): MiniMax-H3 stage operators take the diffusion engine's native operands (strided AdaLN tables, int64 indices, RoPE cache + positions, strided q/k/v views) on SM100/SM103 (#6039)

## Summary

Cake MiniMax-H3 stage operators take the diffusion engine's native
operands, so the sglang `multimodal_gen` route no longer copies per
block or falls back when the AdaLN projection does not have exactly 9
rows:

- `cake_minimax_h3_bf16_pre_attention`: AdaLN shift/scale tables `[rows,
5376]` with any `rows >= 1` and a 16-byte-aligned row stride (strided
column chunks of the `[rows, 6*5376]` projection are accepted in place),
int64 `adaln_index` (out-of-range rows produce zero rows), RoPE as
`(rope_cos_sin [S, 96], rope_positions int64 [M])` with an identity
default, separate `eps` / `qk_eps`.
- `cake_minimax_h3_fc1_swiglu` (bf16 / mxfp8 / nvfp4): same AdaLN table
contract in the norm prologue, `eps` free.
- `cake_minimax_h3_out_proj` (bf16 / mxfp8 / nvfp4): gate table
`[gate_rows, 5376]` with a row stride in `[5376, 2**32)`, int64
`gate_index`.
- Experimental varlen BF16 attention (`cake_backend`): q/k/v may be any
`[T, H, 128]` BF16 view with unit last stride and 16-byte-aligned
row/head strides (token-major; the fused-QKV view and the pre-attention
pack views go in without copies; head-major views are rejected), output
contiguous.

Regenerated `csrc/cake_minimax_h3_*_sm10{0,3}a.cu` from the Cake
sources; host Python validation mirrors the kernel bounds; tests cover
int64 indices, strided tables, `(cache, positions)` RoPE, split eps and
the strided q/k/v views; benchmarks updated. The varlen attention
package (`flashinfer/experimental/minimax_h3_varlen_attention`) is the
output of the generated-program export (240-row protocol, 120 per
architecture; sm_100a 120/120 rows pass on B200; sm_103a 117/120 on B300
— three 15–20 µs smoke rows pass correctness and the source/export floor
but miss the exporter's 2 % ordering-disagreement gate, which is below
their launch jitter); the delivered csrc is byte-identical between the
two architecture stages.

## Performance

Paired same-GPU A/B against the previous operators (CUPTI, cold L2) on
B200 and B300: every contract shape of every operator is within 1 % of
the previous kernel (most rows faster); on the engine's native operands
the new operators beat `previous kernel + the route's per-block copies`
on every representative DiT shape where the copy cost is resolvable
above measurement noise. Full tables are in the internal tracker.

## Test plan

- [ ] `pytest tests/diffusion_ops/test_minimax_h3_bf16_pre_attention.py
tests/diffusion_ops/test_minimax_h3_fc1_swiglu.py
tests/diffusion_ops/test_minimax_h3_out_proj.py
tests/experimental/test_cake_minimax_h3_varlen_attention.py` on B200 and
B300
- [ ] compute-sanitizer synccheck + memcheck on the attention kernel and
one GEMM-stage kernel per module (0 errors)
- [ ] scoped `@flashinfer-bot run
tests/diffusion_ops/test_minimax_h3_bf16_pre_attention.py
tests/diffusion_ops/test_minimax_h3_fc1_swiglu.py
tests/diffusion_ops/test_minimax_h3_out_proj.py
tests/experimental/test_cake_minimax_h3_varlen_attention.py`

🤖 Generated with [Claude Code](https://claude.com/claude-code)



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* MiniMax-H3 attention now accepts supported non-contiguous BF16 query,
key, and value layouts without requiring copies; outputs remain
contiguous.
* AdaLN and gate tables can have variable row counts and supported
strided layouts. Int64 indices are supported, with out-of-range indices
producing zero modulation or gating.
* Pre-attention supports RoPE position mapping and separate input and
Q/K normalization epsilon values.
* Benchmarks can exercise additional operand layouts and report
associated copy times.
* **Bug Fixes**
* Improved compatibility across supported GPU architectures and added
coverage for varied layouts, indices, and RoPE positions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [2b24171](https://github.com/flashinfer-ai/flashinfer/commit/2b24171c08a2cce501c4758ef7aa144be8a19682)

- **作者**: eigen
- **时间**: 2026-10-04T17:48:23Z
- **提交信息**: feat(cake_gemm): masked grouped FP8 batch DeepGEMM MoE GEMM backend for SM100 / SM103 (backend="cake") (#6044)

## Summary

Adds `backend="cake"` to
`flashinfer.gemm.batch_deepgemm_fp8_nt_groupwise`, the masked grouped
FP8 GEMM used by MoE layers (`out[g, :masked_m[g], :] = a[g] @ b[g]^T`,
FP8 E4M3 operands, per-row 128-wide K-block A scales, 128x128 B block
scales, FP32 accumulation, BF16 output). The backend runs generated Cake
programs on SM100a (B200) and SM103a (GB300) for the problem band they
own; the default `backend="deepgemm"` path is unchanged.

### Why

The DeepGEMM masked kernel is a single generic schedule. The Cake
programs are a dispatcher of specialised schedules (single-CTA tiles for
the small `(n, k)` geometries, swap-AB M224 pipelines with packed scales
for the expected-M 230 / 1228 profiles, a BLOCK_N menu for the
decode-shaped rows, and a zero-copy route for the native MN-major packed
UE8M0 serving scales) selected from the five problem scalars `(B, M, N,
K, expected_m)`. Numerics are DeepGEMM's: FP32 accumulation with the
block scales applied in the same K order, so results match the reference
within the existing masked-test tolerance (`3e-2`) and are
bitwise-identical to the generating programs.

### API

```python
out = batch_deepgemm_fp8_nt_groupwise(
    a, b, a_scale, b_scale, masked_m, expected_m,
    scale_granularity_mnk=(1, 128, 128), out=None, out_dtype=None,
    backend="cake",   # new; default "deepgemm"
)
```

* `backend` is explicit-only (no `"auto"` arbitration);
`is_backend_supported("cake", cc)` is `True` for compute capability 100
and 103 only.
* With `backend="cake"`, `a_scale`/`b_scale` may be either the FP32
groupwise scales of the DeepGEMM contract or the native MN-major packed
UE8M0 `torch.int32` tensors (`a_scale: (B, M, K // 512)`, `b_scale: (B,
N, K // 512)`), consumed without conversion.
* Lower-level entry points in
`flashinfer/gemm/cake_batch_deepgemm_fp8.py`:
`prepare_batch_deepgemm_fp8_nt_groupwise(...)` returns a prepared launch
(route, grids, workspace bound once) whose `launch()` allocates nothing
and may be captured into a CUDA graph from the first call;
`run_batch_deepgemm_fp8_nt_groupwise(...)` is the public-API path with a
per-call workspace (no process-wide cached arena);
`is_batch_deepgemm_fp8_nt_groupwise_cake_available(device)`.

### Admission band

The admission predicate (`backend_requirement` checker) equals the band
the generated programs were measured on; every other problem raises
`ValueError` with a named reason instead of falling back silently:

* SM100a device with 148 SMs or SM103a device with 152 SMs (the
dispatcher bakes the resident CTA counts; other SM counts of these
architectures are rejected with a named error);
* `scale_granularity_mnk == (1, 128, 128)`, positive 128-aligned `M`,
`N`, `K`, `0 <= expected_m <= M`;
* `(N, K)` in `{(128, 512), (512, 128), (4096, 7168), (7168, 2048),
(6144, 7168), (7168, 3072), (4096, 4096), (4096, 2048)}`;
* FP8 E4M3 `a`/`b`, `int32` `masked_m`, bfloat16 output (`out` must be
bfloat16 when given); packed UE8M0 scales require both scales to be
`int32`.

### Generated code

* `csrc/cake_batch_deepgemm_fp8/`: one architecture-neutral
`{kernel,binding}.cu` pair per program plus the shared device/host
headers, emitted by the Cake export protocol (public `nvcc` flags, FP32
accumulation, tensor maps passed by value).
* `flashinfer/jit/gemm/cake_batch_deepgemm_fp8.py`: program registry,
JIT loaders, and the dispatcher's ordered first-match route chain
rendered per `(architecture, SM count)` as plain Python over `(B, M, N,
K, expected_m)`.
* `flashinfer/gemm/cake_batch_deepgemm_fp8.py`: admission, route
selection, argument binding, prepared/public launch paths.

### Tests

*
`tests/gemm/test_groupwise_scaled_gemm_fp8.py::test_fp8_groupwise_batch_deepgemm_masked`
parametrised over `backend in {"deepgemm", "cake"}` (skips where the
backend is unsupported or no generated program exists for the device).
* `tests/gemm/test_cake_batch_deepgemm_fp8_nt_groupwise.py`: reference
parity on every supported `(N, K)` incl. empty and full groups; public
API; CUDA-graph capture of the first launch (prepared and public form);
allocation-free launch; packed UE8M0 scale path; out-of-band problems
raise (`(N, K)` outside the band, unaligned shapes, mixed scale dtypes,
unsupported compute capabilities, unknown backend); route chain covers
the inventory with registered programs.
* `benchmarks/bench_deepgemm_blackwell.py --batch-backend
{deepgemm,cake,both}` benchmark arm.
* `.pre-commit-config.yaml`: the generated
`csrc/cake_batch_deepgemm_fp8/` sources are excluded from clang-format
like the other generated source-export directories (their bytes are
attested by the export protocol).

On SM103a (GB300) and SM100a (B200) the generated-test file (33 tests)
and `test_fp8_groupwise_batch_deepgemm_masked` for both backends (192
tests) pass; `is_backend_supported("cake", cc)` is `False` for compute
capability 90 and 120 and `True` for 100 and 103. The export protocol's
source/export parity run passed on every denominator shape (123 on
SM103a, 119 on SM100a: bitwise-identical outputs, no device allocation
in the export launch, source/export latency ratio within the gate on
every row).

## Performance

Three-arm measurement on the same GPU in one process with interleaved
sessions (three sessions per row, CUPTI kernel timing with a cold L2,
medians). Arms: this PR's `backend="cake"` path; the public API at
`backend="deepgemm"` (per-call scale transform included, which is what
callers pay today); and the bundled DeepGEMM masked kernel alone with
its scale transform hoisted out of the timed region (the floor a
cached-scale serving path can reach). Row sets: the 56 shapes of
`benchmarks/bench_deepgemm_blackwell.py` (B in {1,4,8,64,128}, M in
{128..16384}, the four `(N, K)` geometries), 54 DeepSeek-V3
expert-parallel serving shapes at B=64 (gate-up 4096x7168 and down
7168x2048, expected-M 1..8, p10/p50/p90 masks, native packed UE8M0
scales) and the same grid at B=32.

| row set | GPU | public API (`backend="deepgemm"`) / Cake, geomean |
rows Cake faster | bundled DeepGEMM kernel only / Cake, geomean | rows
Cake faster |
|---|---|---:|---:|---:|---:|
| S1: FlashInfer bench-matrix rows (56) | GB300 (SM103a) | 2.620x |
56/56 | 0.957x | 19/56 |
| S1 | B200 (SM100a) | 2.592x | 56/56 | 1.003x | 23/56 |
| S2: DeepSeek-V3 EP serving rows, B=64 (54) | GB300 | 1.805x | 54/54 |
1.174x | 54/54 |
| S2 | B200 | 1.869x | 54/54 | 1.203x | 54/54 |
| S3: serving rows at B=32 (54) | GB300 | 1.997x | 54/54 | 1.208x |
52/54 |
| S3 | B200 | 2.059x | 54/54 | 1.231x | 52/54 |

Every row is faster than the public API on both GPUs. Against the
kernel-only floor, the serving rows are faster on every row except the
two empty-mask rows at B=32 (0.88-0.91x: the DeepGEMM kernel exits at
once, the Cake route still runs its prologue), and the small single-tile
bench-matrix rows (B=1, one M block) stay 0.6-0.9x of the kernel-only
floor because of the fixed prologue; all of them remain 2-4x faster than
the public API.

The export protocol's parity run (bitwise-identical outputs between the
generating programs and the delivered FlashInfer modules, no device
allocation in the launch, latency within the gate on every row) passed
on 123 shapes on SM103a and 119 on SM100a.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added the Cake backend for batch groupwise FP8 GEMM on supported
NVIDIA architectures, with prepared and one-shot APIs. The existing
DeepGEMM backend remains the default.
* Added benchmark options to run the DeepGEMM backend, Cake backend, or
both.
* **Tests**
* Added coverage for Cake results, supported configurations, CUDA graph
capture, repeated launches, and backend route selection.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [911cb09](https://github.com/flashinfer-ai/flashinfer/commit/911cb09d0981c38d15b775b7820e4a76c72fcfa0)

- **作者**: eigen
- **时间**: 2026-10-04T17:47:29Z
- **提交信息**: perf(cake_sparse_mla): rounds 7-17 DSv4 sparse-MLA Cake programs for SM100/SM103 on the #5920 layout (cumulative) (#6045)

## Summary

Rounds 7-17 of the DSv4 sparse-MLA Cake backend (`backend="cake"`, SM100
+ SM103) as one cumulative change on the #5920 layout (per-variant
bindings taking their checks from `tvm_ffi_utils.h`, shared sources
under `common/`, `run_sequence`, the host's direct variant launches).
Main carries round 6 (#5700) for this family; the eight per-round PRs
stacked on it (#5728, #5742, #5845, #5854, #5879, #5946, #5973, #5999)
and the held round 15-17 fork branches were closed in favour of this PR.
Programs: whole-family regeneration of the `cake_dsv4` sources from Cake
!1037's tree (the round-17 kernel tree `c7284461b47` merged into Cake
main, rendered by main's codegen) for sm_103a and sm_100a through the
exporter's #5920-layout path, replacing the round-6 sources. Host: the
four round 11-14 host changes re-expressed on main's host (descriptor
pool and `run_sequence` unchanged), plus the round tests ported onto
main's collapsed tests.

Numerics rule (every round): no precision-level change anywhere (same
tolerances, same or higher-precision intermediates). Rounds that change
output bits are called out below; every other program is bit-identical
to its predecessor (NaN-poisoned bit compare on the measured cells).

### What changed per round

- Round 7 ([Cake
!1037](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1037),
was #5728): FP8/H64 single-CTA SWA (class K1): single-pass softmax with
the TMEM-alias correctness fix (Q x400 over-tolerance elements
398..64359 -> 0) and softmax warps helping the first K-tile gather,
-0.7..-0.85 us per row; FP8/H64 cluster / wide one-partition: V4 gather
owner, whole 128-key tile per cluster CTA with an f32 end merge over
DSMEM (bits change by merge grouping), -0.13..-0.70 us; H8/H16 decode:
loader warps skip the padded gather rows, up to -1.6 us.
- Round 8 ([Cake
!1043](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1043),
was #5742): FP8/H64 wide one-partition in the whole-tile form with the
no-LSE epilogue, -0.8..-0.9 us per row (bits change by merge grouping);
K1 row max through `tcgen05.ld.red.max` on SM103a / full-tile fast max
on SM100a, -0.45..-0.83 us; H8/H16 index-row L2 prefetch, -0.10..-0.26
us; BF16 one-tile SWA chain K stage-0 gather before the index barrier,
-0.03..-0.10 us.
- Round 9 ([Cake
!1061](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1061),
was #5845): six bit-identical levers: coalesced final-O epilogue of the
fp8 H64 M64 persistent body (-7..-18 % on the six M64 rows), K4
first-tile gather split across the three warp roles (-2.5..-2.7 %), bf16
H64 guard by-value TMA descriptor ABI on sm_103a, K1 8-warp O epilogue
drain, H/I SwapsAb page pair 0 from page-loader registers, class-O fp8
H64 5-slot KV ring (-12 % / -7..-9 %).
- Round 10 ([Cake
!1066](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1066),
was #5854): bit-identical: class-O fp8 H64 split O-accumulator handshake
+ six-slot K ring with early Q release (-8..-10 %), bf16 H64 guard
mask-flag pre-decode + transposed O store (-3.1..-4.1 %), H/I SwapsAb
index-row L2 prefetch on sm_103a; the h8/h16 bindings gain the
`num_query_tokens` scalar the host already passes by name.
- Round 11 ([Cake
!1085](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1085),
was #5879): seven bit-identical levers (fp8 H64 M64 gated box-TMA K
gather + per-stage O split credit; fp8 K4 last-tile key split; fp8 H128
persistent epilogue load-ahead-4 on sm_100a + deferred staging wait;
bf16 H128 row-first elected multi-warp gather issue; bf16 H64 guard
class-conditional gather4 issue) plus three contract-identical
correctness fixes (split-FP8 P stage 1024 B-aligned at SMEM 175104 in
the K4 / M64 / fp8 H128 persistent programs; guarded 16 B vector loads
in the top-k index producers). **Host:** `out=None` is allocated in
`run_cake_dsv4` after routing and placed at `base % 4 KiB == 0x800` on
the six routes where the phase law was measured
(`allocate_cake_dsv4_output`, `cake_dsv4_out_phase`, `out_shape`);
caller-provided `out` and the other routes are unchanged. New
`tests/mla/test_cake_dsv4_out_placement.py`.
- Round 12 ([Cake
!1126](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1126),
was #5946): bf16 H128 row-first / prefill O epilogue `tcgen05.wait::ld`
per 32-column TMEM load (-1.4..-6.0 %); bf16 H32 top-k mixed-pool split
assignment (re-associates f32 partials by split geometry, strictly more
precise: cells > 1 ulp vs fp32 118.8k -> ~630) and active_topk mask
before the s_full wait (-3.5..-5.2 %); fp8 K4 wide quarter-tile tail +
helper-correction readback pre-issue (-2.0..-4.1 %); **Host:** the fp8
H64 M64 body is two exported programs selected by the item width in
`_route` (`_fp8_h64_m64_program`:
`fp8_h64_prefill_source_persistent_m64` for `sparse_topk == 128`,
`..._m64_multi_tile` otherwise; same ABI, same bits).
- Round 13 ([Cake
!1152](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1152),
was #5973): bit-identical: **Host + program:** bf16 H128 row-first rows
with 17-37 tokens run the new `bf16_h128_topk128x_row_first_vsplit`
program (two 2-CTA clusters per token gathering only their N256 V half;
grid 4 x tokens; `_BF16_ROW_FIRST_V_HALF_SPLIT_MAX_TOKENS = 37`),
hardening-000025 -8.4 % GB300 / -7.8 % B200; fp8 K4 whole-tile `st.async
... complete_tx` peer O push + four-stage chunked merge (-0.70..-0.74
us); fp8 H64 M64 multi-tile next-item Q TMA after the CLC response
(-0.4..-1.5 %); fp8 H128 persistent partial-o accumulation before the
final `o_full` wait (-0.3..-1.1 %).
- Round 14 ([Cake
!1168](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1168),
was #5999): bit-identical: bf16 H128 row-first (owner + vsplit) index
warp issues its nine index loads before the nine `st.shared` passes
(-5.0..-6.6 %); bf16 H64 guard program stores O through a TMA tensor map
from per-warp staging (-0.9..-3.5 %) -- **Host:** the explicit `"O":
"O"` entry in `_TMA_SOURCE_ALIASES` so the guard binding's
`("tma_buffer", "O")` resolves; fp8 H128 persistent two-box pipelined
epilogue drain on sm_103a.
- Round 15 ([Cake
!1177](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1177),
held on the layout decision): bit-identical: the two-box pipelined
epilogue drain becomes the default for the sm_100a fp8 H128 lane-gather
variant (>= 128 work items); no host change.
- Round 16 ([Cake
!1182](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1182),
held): bit-identical: fp8 H64 M64 multi-tile softmax -1 ballot hoisted
above the `s_full` join (-0.22..-0.56 us); bf16 H64 guard O store split
per V stage so the stage-0 O drain overlaps PV1 (-0.19..-0.35 us); no
host change.
- Round 17 ([Cake
!1186](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1186),
held): bit-identical: bf16 H128 row-first programs (owner + vsplit)
hoist the swa / compressed V table select out of the four elected gather
groups (hardening-000025 -0.593 us GB300 / -0.800 us B200,
hardening-000031 -0.160 / -0.751 us); no host change. Round 18 ([Cake
!1193](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1193))
shipped no program change (ledger only).

### Layout (#5920) notes

- Per-arch registry schema unchanged: arch-prefixed `sources`,
`arg_plan` as `_PLAN_<LABEL> [+ _SLAB] + _GRID`, `tma_workspace_bytes`
only where non-zero, reducers shared through `common/` where both
architectures compile the same kernel (`split_reduce`,
`bf16_h64_compressed_reduce`); the split-5 reducers stay per-arch under
the one key `bf16_h128_split5_reduce` (sm_103a grid `(tokens, heads / 4,
1)`, sm_100a `(tokens, heads, 1)`, as main's launch test pins).
- Two new variant keys per architecture:
`bf16_h128_topk128x_row_first_vsplit`,
`fp8_h64_prefill_source_persistent_m64_multi_tile` (27 variants per
arch).
- No family bindings; two-stage routes go through `run_sequence`; the
host's descriptor pool is untouched.

### Variant / file diff vs main `a12173ca0`

- Per-arch registrations: 27 variants each (main had 25): new keys
`bf16_h128_topk128x_row_first_vsplit` (round 13, host-routed for
17-37-token rows) and `fp8_h64_prefill_source_persistent_m64_multi_tile`
(round 12). Loader `flashinfer/jit/cake_dsv4.py`: data-only edits
(registrations, plan/grid constants, source lists); loader functions and
`__all__` untouched.
- Files: `common/` 30 (4 before), `sm_100a/` 24 (46 before), `sm_103a/`
24 (46 before); `sm_120a/` and every other family untouched. Diff vs
main: 107 files, +17906 / -62404.
- Fold disclosure: the exporter serves a variant from `common/` when its
kernel + binding sources are byte-identical on both architectures modulo
hash tokens. With the rounds 7-18 kernel tree rendered by current Cake
main codegen, 15 of the 27 variants fold (bf16_h128_swa128,
bf16_h128_topk128x_row_first, …_vsplit, bf16_h128_topk128x_split4_sm100,
bf16_h16_h32_swa128_v44, bf16_h32_topk128x_early_v47,
bf16_h64_compressed_q8_v38, bf16_h64_compressed_reduce,
bf16_h64_guard_q_tma_batch_r25, bf16_h64_prefill,
fp8_h64_prefill_source_persistent_m64, …_m64_multi_tile,
fp8_h64_source_exact, fp8_lowhead_h64, split_reduce); 12 stay per-arch.
Each architecture still compiles its own module from the shared source.
- Host: the six host/test commits below the export commits port the
rounds 13-17 host changes (vsplit route, descriptor-pool and
`run_sequence` plumbing, output-placement test) onto the #5920 host;
`cake_dsv4_host_shim.h` is unreferenced by the regenerated bindings and
left in place.

## Validation

Both architectures measured on the exported programs of this branch
(GB300 = sm_103a commit `08d1c3c8`, whose sm_103a sources are
byte-identical modulo hash tokens to this head; B200 = this head
`4146373e`). Baseline = FlashInfer trtllm-gen default path of the same
clone. Paired CUPTI sweeps (cold L2, active-union median), same-process;
same-GPU ABBA = legs A1 B1 B2 A2 on one GPU, A = this branch, B = the
round-17 fork head `dbf86c4d6` (quantum q = 0.032 us).

| | GB300 (sm_103a) | B200 (sm_100a) |
|---|---|---|
| production export: 134 shapes timed + correct vs the Cake source
programs (receipts) | 133/134 pass, source/export geomean 1.0022,
trtllm-gen/export 1.4948 (94 canonical); hardening-000004 timing-only
0.9578x (correctness pass; retained first-run receipt — an independent
full run on another node measured it 0.9820x pass; the same-GPU ABBA
below shows the row 0.16 us *faster* than round 17 in both orders) — JHB
802461 nvl72d426-T11, 4 GPUs | 134/134 pass, source/export 1.0037 (min
h004 0.9845), trtllm-gen/export 1.4404 — NSC 2138957, 4 GPUs |
| **94 canonical rows faster than the default path** | 94/94 correct,
every row > 1.0: geomean 1.4617, min 1.1191 (decode-000051) | 94/94
correct, every row > 1.0: geomean 1.4447, min 1.1774 (decode-000034) |
| 40 hardening rows faster than the default path | 40/40 correct, every
row > 1.0: geomean 1.4857, min 1.1068 (hardening-000004) | 40/40
correct, every row > 1.0: geomean 1.4396, min 1.1357 (hardening-000023)
|
| all 134 rows | geomean 1.4688, min 1.1068, 0 rows <= 1.0 | geomean
1.4432, min 1.1357, 0 rows <= 1.0 |
| no row > 2 % slower than the round-17 programs (same-GPU ABBA vs
`dbf86c4d6`) | pin rows (8): 0 slower, h004 -0.160 us / 064 -0.100 / 065
-0.070 faster both orders, rest within 1 q; hardening 00-39 (40): 0 rows
beyond 1.25 q (h034 +0.040 us = +0.13 %, h037 +0.040 us = +0.07 %; h020
-0.580 us); canonical 94: 94 rows in 3 parts (`68a1e0f7` `1e1726bf`
`59741678`): 134-row totals = 18 rows slower in both orders, 27 faster
in both orders, geomean A/B 0.9956; **1 row above +2 %: decode-000056
+0.350 us (6.53 -> 6.88 us, +5.4 %, program fp8_h16_source_exact)**,
next largest +1.7 % (decode-000074/077); largest gains decode-000078
-7.1 %, hardening-000020 -6.9 %, decode-000006/018 -6.7 %, 081 -6.6 %,
prefill-style-000086 -2.7 %. Attribution of decode-000056 (Cake round
19, measured on another GB300 node): **not a codegen or ABI effect**.
The non-ABI text differences compile to byte-identical SASS on sm_103a
(128 regs / 0 spills in every form); A-vs-B replications flip sign
between fresh processes of the same install; repeat sampling (5
alternating fresh A/B processes x 3 GPUs) gives this head 6.807 us vs
round 17 6.803 us (0.1 q). The kernel (`fp8_h16_source_exact`) has two
placement-dependent timing modes ~0.3 us apart that both exports reach;
the round-18 cell caught the two installs in different modes. Programs
unchanged | pin rows (8): `ea69b60d`: 1 slower both orders =
decode-000002 +0.070 us (10.46 us, +0.67 %, 2.2 q); 6 rows
timing-identical in all four legs; h031 within its band; hardening 00-39
(40): `0365c256` / `f0fee955` (B200 legs take ~45 min per 20 rows; both
steps hit the 3 h step budget during leg A2): 25/40 rows with all four
legs, code part <= +0.030 us (<= 1 q) on every one; the 15 rows without
A2 have |A1 - B1|, |A1 - B2| <= 0.09 us (h017 -0.09 us = faster); no row
> 2 % in any leg; canonical 94: 6 x 16-row parts (`d69139af` `1b42ff9f`
`d2cf5268` `49f23a7d` `fedccecc` `c3874f40`, all four legs): 134-row
totals = 8 rows slower in both orders (max decode-000002 +0.070 us =
+0.67 %, the other seven +0.04..+0.06 us <= 2 q), 0 rows faster in both
orders, 112 rows timing-identical or within 1 q, geomean A/B 1.0004;
**no row above +2 %**; decode-000056 (the GB300 +5.4 % row) is 6.690 us
in all four legs on B200: sm_100a already used the `grid_constant` TMA
ABI in round 17, consistent with the GB300 cell being a sampling
artefact (see the GB300 column) |
| `tests/mla/test_cake_dsv4*.py` (GPU, fresh clone of this head) | 320
passed, 4 skipped, 0 failed (`5e70a6c9`, 1 GPU of 802461) | 319 passed,
4 skipped, 1 failed in the full run (`b13c39b1`:
`test_cuda_graph_replay_matches_eager[h32-fp8-q1]` at "eager call
allocated" with memory_allocated *lower* than the baseline, i.e. a GC of
earlier tests' tensors during the call); the test re-run in isolation
passes 12/12 params (`cb812a81`) |
| Cake-side gates of the kernel tree (Cake !1037, head `f3108393953`) |
134 rows x all axes 528/528 correct; synccheck 8/8 + memcheck 7/8 rows 0
errors; CPU rule tests 705/705 | same: 528/528; synccheck 8/8 + memcheck
7/8 rows 0 errors; 705/705 |

Cross-node note: the sweep medians of this run are not comparable to the
round-17 PR numbers (different nodes / clock regime: on GB300 both Cake
and trtllm-gen moved +5.0 % / +3.0 % geomean vs the round-17 sweep); the
same-GPU ABBA row above is the valid round-over-round comparison.

## Baselines and their source PRs

- trtllm-gen default path: FlashInfer main as of `a12173ca0` (this
branch's base; the DSv4 trtllm-gen MLA path is unchanged since
`c4cb63534`, the #5879 head: the only commit touching the MLA dispatch
files since then is #5983, which adds an SM120 source to
`flashinfer/jit/mla.py`; #5854, #5845, #5742, #5728, #5700 before it).
- Cake round 17: fork branch `cake-772-dsv4-round17` (`dbf86c4d6`, held
on the #5920 layout decision); round 16: `cake-772-dsv4-round16`
(`45c0b819c`, held); round 15: `cake-772-dsv4-round15` (`1a91f12a9`,
held); round 14: #5999 (`e2f7310ee`); round 13: #5973; round 12: #5946;
round 11: #5879; round 10: #5854; round 9: #5845; round 8: #5742; round
7: #5728; round 6 and before: #5700 and the tracker's earlier PRs.
- Round 18 (Cake !1193) changed no program: the exported programs here
are the round-17 kernel tree `c7284461b47` as merged into Cake main
(!1037 head `f3108393953`), rendered on the #5920 layout by the exporter
(main's codegen since the round-17 base changes every generated
program's text — dead-helper pruning, grid_constant tensor maps,
`__shfl_sync`, launch-bounds macro — without touching the kernel
schedules); the pre-export source-vs-export agreement for the sm_103a
build-gap row (hardening-000031) is in the round-18 Cake doc.

- Tracker: flashinfer#4254 (DSv4 sparse-MLA Cake backend; this PR
supersedes the round 7-14 PRs listed above and the held round 15-17 fork
branches `cake-772-dsv4-round15` `1a91f12a9`, `cake-772-dsv4-round16`
`45c0b819c`, `cake-772-dsv4-round17` `dbf86c4d6`).

Cake MRs: !1037 .. !1193 (Linear CAKE-772); exporter #5920-layout
support: [Cake
!1200](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1200)
(stacked on !1037).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* CAKE DSV4 can now allocate its output when none is provided, with
route-specific output placement.
* Added and refined kernel routing for selected BF16 and FP8 workloads,
including support for wider sparse inputs and smaller query batches.
* **Bug Fixes**
* Improved tensor and launch validation across CUDA devices, including
checks for tensor placement and descriptor dimensions.
* Updated output handling for selected kernels to support
tensor-map-based writes and revised buffering.
* **Tests**
* Expanded coverage for route selection, output allocation, and output
placement.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4547
- **最后更新**: 2026-10-04T21:24:46Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Kyle Hu, YZJF

## AI分析总结

# FastVideo仓库提交分析总结

## 1. 主要更新类型
- **CI基础设施优化**：改进持续集成效率
- **文档更新**：新增OpenAI服务配置教程

## 2. 关键变更点及其与项目方向的关系

- **CI优化（#1914）**：通过重新排序CI流水线各阶段，减少不必要的等待和资源消耗，属于开发者体验（DX）层面的改进。这与FastVideo作为高性能视频生成框架的定位一致——项目自身也需要高效的开发和测试流程来支撑快速迭代。

- **文档更新（#1906）**：在Wan模型的Cookbook页面中补充了OpenAI服务（Serving）相关的配置教程。Wan是FastVideo支持的视频生成模型之一，此项更新直接响应了社区用户对"如何将Wan模型部署为OpenAI兼容API"的需求，是README中Cookbook部分的重要补充。

## 3. 对项目的影响和潜在意义

- **降低部署门槛**：OpenAI兼容的Serving配置文档意味着用户可以更方便地将FastVideo的视频生成能力接入现有的OpenAI生态工具链（如LangChain、各类Agent框架），扩大了项目的应用场景。

- **提升开发效率**：CI优化虽然不直接面向终端用户，但能减少贡献者的等待时间，间接提升社区参与度，符合README中"Weekly Dev Meeting"所体现的社区驱动开发理念。

## 4. 值得关注的技术点

- **CI流水线编排**：关注#1914中具体的lane重排策略——是基于依赖关系优化、并行度提升，还是资源预热机制？这反映了项目对大规模GPU资源调度的理解深度。
- **Wan模型Serving实现**：#1906中OpenAI API的适配方式值得研究——是使用FastAPI等标准框架，还是有专门的推理加速层？这关系到实际部署时的延迟和吞吐量表现。
- **Co-author署名**：提交中出现了Claude的Co-author署名，说明项目已在开发流程中引入AI辅助编程实践，这是一个值得跟踪的工程实践趋势。

## 5. 对项目发展方向的影响

结合README，FastVideo定位为面向视频生成（尤其是扩散模型）的高性能推理/训练框架，拥有Documentation、Cookbook和Quick Start等完善的开发者资源体系。

这两项提交体现了项目当前阶段的两个关键特征：

- **成熟度提升**：项目已进入"打磨基础架构+完善使用文档"的阶段，而非纯粹的功能开发阶段。CI优化和文档补全都是项目走向成熟的标志。

- **生态融合意图**：通过提供OpenAI Serving教程，项目明确向"可嵌入现有AI工具生态"的方向发展，这有助于将FastVideo从一个独立的研究/推理工具转变为可被广泛集成的基础设施组件。

总体而言，这些提交虽然规模不大，但体现了项目在工程质量和用户可及性方面的持续投入，与其作为开源AI基础设施的长期愿景相契合。

## 详细提交记录

### [6ded84e](https://github.com/hao-ai-lab/FastVideo/commit/6ded84ee0f60cb8081d6fc228671e52c7c71c749)

- **作者**: Kyle Hu
- **时间**: 2026-10-04T19:35:12Z
- **提交信息**: [ci]: improve CI efficiency by reordering lanes (#1914)

### [a4d6416](https://github.com/hao-ai-lab/FastVideo/commit/a4d6416c526b2af8493bb617a76ec1c412d3d747)

- **作者**: YZJF
- **时间**: 2026-10-04T19:20:06Z
- **提交信息**: [docs] Add OpenAI serving recipes for Wan cookbook pages (#1906)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34652
- **最后更新**: 2026-10-04T19:13:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
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


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13205
- **最后更新**: 2026-10-04T18:56:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36783
- **最后更新**: 2026-10-05T00:49:33Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 19
- **主要提交者**: Tokha233, Cheng Wan, Shangming Cai

## AI分析总结

# SGLang 昨日提交分析（33 条）

## 1. 主要更新类型
- **重构（约 7 条）**：以"stage boundaries"为核心，构建层栈、Qwen4 实验解码器、Hunyuan V4 解码器、HiCache 预取等统一到新的组织方式。
- **功能新增（约 10 条）**：diffusion 模型支持（CUDA graphs、LoRA 加载、视频编码预设）、Apple Silicon (MPS) 平台、XPu 融合 QK-norm+RoPE、CP+专家并行的分散交错输入等。
- **Bug 修复与稳定性（约 12 条）**：统一内存（unified memory）的 compaction、页面复用、session slot 分配；GigaChat 3.5 stage 边界；HiCache 物理传输；MoE all-reduce 归属等。
- **依赖升级与 CI**：CUDA PyTorch 升级至 2.14、ROCm kernel wheel 源修复、GB300 临时禁用、AMD/mi355x CI 修复。
- **文档更新**：AMD 相关 mori io 和 umbp playground 修正。

## 2. 关键变更点与项目方向的关系
- **多硬件生态扩展是明确主线**：AMD（ROCm topk v2、GLM-5.2 decode 路径、RoPE dtype）、Intel XPU、Apple Silicon、NVIDIA GB300/GB200 相关修复密集出现，表明 SGLang 正在从"优先 CUDA"转向"全平台可用的推理引擎"，与 README 中多后端推理的目标高度一致。
- **Diffusion/多模态投入显著**：约 9 条提交涉及 diffusion 视频/图像模型（qwen-image、JoyAI-Echo、ComfyUI 集成），说明项目正系统性地将扩散模型推理纳入一等公民支持，而非零散实验。
- **架构层的"stage boundaries"重构**：多个模型解码器统一用 stage 边界构建，意图是抽象模型结构的共性表示，为未来支持更多架构（GigaChat、Qwen4、Hunyuan V4）降低边际成本。
- **统一内存/HiCache 优化**：大量 unified-memory 相关修复表明项目在探索低成本长上下文与 KV cache 管理策略（lazy checkpoint、页面复用、物理 slot 映射）。

## 3. 对项目的影响和潜在意义
- **可维护性提升**：解码器和缓存逻辑的重构使后续模型支持更快、缺陷率更低。
- **平台覆盖面扩大**：MPS 支持和 XPU 融合算子让消费级/异构硬件用户可用性提升，有利于社区规模扩大。
- **生产就绪度增强**：PD（prefill-decode 分离）状态验证、weight_cache 多 rank 协调、unified memory compaction 修复都是面向大规模部署稳定性的改动。
- **依赖升级（PyTorch 2.14）** 可能带来新的算子与编译优化，但也存在兼容性风险，需观察后续修复。

## 4. 值得关注的技术点
- **ROCm topk v2 的"一长行跨 block 切分"**：CDNA 集群路径优化，对 AMD 上 MoE 路由性能影响直接。
- **GLM-5.2 decode 路径**：decode 形状的 MoE/MLA tile、投机采样 softmax 拆分、bf16 GEMM 路由，体现了 decode 阶段的深度优化思路。
- **explicit reciprocal scaling（recurrent Q/K 归一化）**：潜在数值稳定性改进，值得关注是否影响长上下文精度。
- **diffusion 的 CUDA graphs 与 kernel 校验移入 launcher**：推理延迟与吞吐的系统性优化，扩散模型服务成本将下降。

## 5. 对项目发展的综合影响
结合 README"LLM 与多模态模型的快速推理"定位，这批提交显示项目正沿着三条轨迹推进：**（1）架构抽象化**（stage boundaries 统一多模型构建），**（2）硬件民主化**（AMD/XPU/MPS 全面铺开），**（3）多模态实用化**（diffusion 从实验走向可服务化）。短期内最直接的收益是 AMD/Intel 用户的可用性与性能、diffusion 模型的推理效率，以及统一内存场景下的缓存可靠性；长期看，架构重构为支持更复杂的模型与更大规模部署奠定了基础。

## 详细提交记录

### [b792228](https://github.com/sgl-project/sglang/commit/b792228b35b21565067520857319dfc05e4d134e)

- **作者**: Eric.Chin.AMD
- **时间**: 2026-10-04T23:54:37Z
- **提交信息**: [ROCm] topk v2: split one long row across blocks, the CDNA cluster-path equivalent (#39931)

Co-authored-by: Bingxu Chen <bingxche@amd.com>

### [1f299e9](https://github.com/sgl-project/sglang/commit/1f299e9f2f34fa5df9c13f79afe70e815b248ded)

- **作者**: Cheng Wan
- **时间**: 2026-10-04T23:40:24Z
- **提交信息**: [Refactor] Build layer stacks in order with append_stages (#42481)

### [a99567a](https://github.com/sgl-project/sglang/commit/a99567ab7404902c3d1af03c0f05775262e0bbf4)

- **作者**: Cheng Wan
- **时间**: 2026-10-04T23:39:34Z
- **提交信息**: [Fix] GigaChat 3.5: build the stage boundaries once (#42480)

### [5c8fb9e](https://github.com/sgl-project/sglang/commit/5c8fb9e9385dec105fdd8469b27b76402f6e8897)

- **作者**: Cheng Wan
- **时间**: 2026-10-04T23:39:06Z
- **提交信息**: [Fix] Offer the fused MoE finalize all-reduce only to a block that owes the sum (#42479)

### [f07c1a3](https://github.com/sgl-project/sglang/commit/f07c1a398efdf1772beb59916634c1338574ee91)

- **作者**: Cheng Wan
- **时间**: 2026-10-04T23:38:36Z
- **提交信息**: [Refactor] Build the Qwen4 experimental decoders from stage boundaries (#42478)

### [92d6035](https://github.com/sgl-project/sglang/commit/92d60351e2eb0dc2a947ff4a18c79bc54b6c77ce)

- **作者**: Cheng Wan
- **时间**: 2026-10-04T23:38:03Z
- **提交信息**: [Refactor] Build the Hunyuan V4 decoder from stage boundaries (#42477)

### [f5ccc4d](https://github.com/sgl-project/sglang/commit/f5ccc4d7d960c238e63c26edb71b92e177cc0ed6)

- **作者**: Lianmin Zheng
- **时间**: 2026-10-04T22:30:03Z
- **提交信息**: [Kernel] Use explicit reciprocal scaling for recurrent Q/K normalization (#42486)

Co-authored-by: jiayisuse <jiayisuse@users.noreply.github.com>

### [d475b5a](https://github.com/sgl-project/sglang/commit/d475b5a25c3b723bbd46fafdf33eeef288a82db9)

- **作者**: Tarang Khanna
- **时间**: 2026-10-04T22:20:13Z
- **提交信息**: [weight_cache] Coordinate daemon readiness across ranks (#38828)

### [caf9632](https://github.com/sgl-project/sglang/commit/caf96324fc228a2cef5ec52b26862657962fb595)

- **作者**: Aditya Sharma
- **时间**: 2026-10-04T22:03:40Z
- **提交信息**: [Apple Silicon] Add an Apple Silicon (MPS) platform to the standard Torch model runner (#36780)

### [bab04cd](https://github.com/sgl-project/sglang/commit/bab04cd7913ff50d1bf1a677a2d10e5015dc4c3b)

- **作者**: SuperSong
- **时间**: 2026-10-04T19:51:22Z
- **提交信息**: fix(unified-memory): propagate unified-memory lazy checkpoint policy and handle unallocated session slots (#42072)

Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [fea3c08](https://github.com/sgl-project/sglang/commit/fea3c088a1412ba794b1f7998521360ad280c714)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-04T19:24:04Z
- **提交信息**: [CI] Temporarily disable GB300 (#42463)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [aa0ce20](https://github.com/sgl-project/sglang/commit/aa0ce20201f7fa3edefb8e5f6736151a42f1a3e9)

- **作者**: Zhang, Jiejing
- **时间**: 2026-10-04T18:19:37Z
- **提交信息**: [ROCm] GLM-5.2 decode path: decode-shaped MoE/MLA tiles, split speculative softmax, and bf16 GEMM routing (#41725)

Co-authored-by: kyle-256 <Kyle.Zhao@amd.com>

### [7a719e9](https://github.com/sgl-project/sglang/commit/7a719e9a65e7f52b012ab37211b5f174e5d3d38d)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-04T16:36:26Z
- **提交信息**: [AMD] Fix RoPE cache dtype and diffusion CI failures (#42494)

### [0343bc1](https://github.com/sgl-project/sglang/commit/0343bc14831e9000d0e32f9b0063f6de74d649c6)

- **作者**: billishyahao
- **时间**: 2026-10-04T16:28:11Z
- **提交信息**: [AMD][Docs] fix mori io and umbp playground (#42512)

### [137c084](https://github.com/sgl-project/sglang/commit/137c084000809a5d36068d71b77fb1196995d641)

- **作者**: Shuwen Wang
- **时间**: 2026-10-04T16:13:07Z
- **提交信息**: [HiCache] refactor: retire in-flight storage prefetches through one helper (#41453)

### [affa261](https://github.com/sgl-project/sglang/commit/affa261e3d289fe4f907c9b2e8d773fef0d36dba)

- **作者**: WenhaoZhang
- **时间**: 2026-10-04T14:22:08Z
- **提交信息**: [diffusion] feat: enable cuda graphs for observation encoding and denoising steps for action models (#42171)

### [279d3f3](https://github.com/sgl-project/sglang/commit/279d3f3888a8fe7387e703066acf94711693f71a)

- **作者**: WenhaoZhang
- **时间**: 2026-10-04T14:21:13Z
- **提交信息**: [diffusion] feat: load ComfyUI/ai-toolkit fused `gate_up` LoRAs and diffusers metadata alpha for qwen-image-2.1 (#42174)

### [44fac68](https://github.com/sgl-project/sglang/commit/44fac689f5aa2c303b44ffd5d73f1f610f52d721)

- **作者**: WenhaoZhang
- **时间**: 2026-10-04T14:20:20Z
- **提交信息**: [diffusion] optimization: decode json pixel lists to numpy at the entrypoint (#41895)

### [ab9d8f0](https://github.com/sgl-project/sglang/commit/ab9d8f029c12cda8167f51d46664d643c8771a6e)

- **作者**: Michael
- **时间**: 2026-10-04T13:23:54Z
- **提交信息**: [AMD][DI][CI] mi355x spur: skip RDMA ports that are not PORT_ACTIVE; dump driver log on failure (#41405)

### [35f3c96](https://github.com/sgl-project/sglang/commit/35f3c96ff4794a4de15daf12caad371084a037ee)

- **作者**: Shuwen Wang
- **时间**: 2026-10-04T10:45:31Z
- **提交信息**: [CI] Fix bootstrap sender registration test on main (#42487)

### [148da8e](https://github.com/sgl-project/sglang/commit/148da8e77d5c9e9e02be34b51fc388be2eeff280)

- **作者**: Shangming Cai
- **时间**: 2026-10-04T10:32:30Z
- **提交信息**: [PD] Validate decode state layout once at registration (#42051)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [bc5a055](https://github.com/sgl-project/sglang/commit/bc5a055dd772f45b4db7e649679ac8fc5f775f8c)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-04T10:23:29Z
- **提交信息**: [diffusion] move kernel validation into launchers and simplify dispatch (#42391)

### [29bcb74](https://github.com/sgl-project/sglang/commit/29bcb74a893ab0160e211b58f3553122c7e5f7c1)

- **作者**: Michael
- **时间**: 2026-10-04T09:54:28Z
- **提交信息**: [AMD][CI] Fix ROCm kernel wheel sources: drop eagle_utils, add DSV4 kernels (#42461)

### [6cec8f9](https://github.com/sgl-project/sglang/commit/6cec8f98cef8849e0ed810a78f1244b71f222811)

- **作者**: SuperSong
- **时间**: 2026-10-04T09:48:08Z
- **提交信息**: [Bugfix] Fix unified-memory compaction gates and pending page reuse (#39982)

Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [1d02a36](https://github.com/sgl-project/sglang/commit/1d02a36bb7ecd8ea112fc132aeaee4e0d23dc274)

- **作者**: SuperSong
- **时间**: 2026-10-04T09:45:45Z
- **提交信息**: fix(inkling): translate unified-memory checkpoint destinations to physical slots (#38229)

Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [1e49077](https://github.com/sgl-project/sglang/commit/1e490772e512317fab95608cbc9fb127776ae28e)

- **作者**: WenhaoZhang
- **时间**: 2026-10-04T09:19:09Z
- **提交信息**: [diffusion] fix: pin the JoyAI-Echo overlay's source revision (#42471)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ba68306](https://github.com/sgl-project/sglang/commit/ba68306256d64c53d302dc5d2f3be9e388af0738)

- **作者**: Mick
- **时间**: 2026-10-04T08:22:36Z
- **提交信息**: [diffusion] feat: let requests choose the video libx264 preset (#41797)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fbce0d9](https://github.com/sgl-project/sglang/commit/fbce0d9478c964b827517d6a0d917131e26d27ea)

- **作者**: Tokha233
- **时间**: 2026-10-04T08:08:56Z
- **提交信息**: [diffusion] fix: load serialized h3 INT8 in ComfyUI integrated mode (#42121)

Signed-off-by: Tokha233 <61346912+Tokha233@users.noreply.github.com>
Co-authored-by: WenhaoZhang <42087078+niehen6174@users.noreply.github.com>

### [0bdd0cc](https://github.com/sgl-project/sglang/commit/0bdd0cc8dc48573dcc5278e1ad0129a502affc47)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-04T07:48:02Z
- **提交信息**: [Deps] Upgrade the CUDA PyTorch stack to 2.14 (#38641)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [9631f6f](https://github.com/sgl-project/sglang/commit/9631f6f2d085f1fa6695331a31d0433f4f9173d2)

- **作者**: Kotthagattu Meher Sai
- **时间**: 2026-10-04T07:45:18Z
- **提交信息**: [XPU] Enable fused QK-norm + RoPE for Qwen3-MoE (#40190)

### [7eb6286](https://github.com/sgl-project/sglang/commit/7eb628612c43fcb74522057a0b88380e6f26b86a)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-04T07:44:51Z
- **提交信息**: [Fix] Publish the parallel config the CLIP attention test reads (#42460)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [55c5415](https://github.com/sgl-project/sglang/commit/55c5415c1720f121343588fb6492e0635399167d)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-04T07:43:31Z
- **提交信息**: [CP] Support scattered interleave CP inputs with expert parallelism (#42041)

### [937c0a6](https://github.com/sgl-project/sglang/commit/937c0a6cfe97f50adc62beff9a9e156124a6367a)

- **作者**: Yonghao Zhuang
- **时间**: 2026-10-04T07:38:56Z
- **提交信息**: Fix unified HiCache physical transfers (#39479)

Co-authored-by: yhzhuang <yhzhuang@fb.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>
Co-authored-by: Yonghao Zhuang <yhzhuang@users.noreply.github.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>
Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1288
- **最后更新**: 2026-10-03T18:50:23Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93176
- **最后更新**: 2026-10-05T00:11:06Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 11
- **主要提交者**: Taneem Ibrahim, Shenglei Fu, Harry Mellor

## AI分析总结

# vLLM 昨日提交分析总结

## 1. 主要更新类型

本次 11 个提交以 **Bug 修复** 为主（约 6 个），辅以 **内核/性能优化**、**CI/测试基础设施改进** 和 **小型前端功能增强**，整体属于日常维护与稳定性强化，无重大的新功能模块引入。

## 2. 关键变更点及与项目方向的关系

- **确定性（Batch Invariance）成为焦点**：#59377 为 LoRA 增加确定性 split-K shrink 内核、#59106 修复 batch-invariant mean 的输出 dtype、#53692 扩展批不变性测试覆盖的模型（GLM-4-9B、Phi-4）。这直接服务于 vLLM 的核心目标——提供**可复现、可靠的 LLM 推理服务**，保证相同输入在不同 batch 划分下产生一致输出。
- **多硬件平台适配**：#59550 修复 ROCm 滑动窗口注意力边界、#59159 让 DeepSeek V4 FP8 稀疏解码在 Intel XPU 上可图捕获。这与 vLLM "easy, fast, cheap LLM serving for everyone" 的愿景一致，持续降低新硬件平台的准入门槛。
- **前端与开发者体验**：#59889 在 404 错误中列出可用模型、#40986 让流式请求在首 token 前返回错误，两者都提升了 API 的易用性和错误诊断能力。
- **CI 与依赖维护**：#59521 简化权重同步指标的采集要求、#59913 自动为 pooling PR 打标签、#59932 升级 peft 以兼容 transformers 5.18 最低要求，以及 #58457 对齐 KV block 尺寸与注意力后端的交叉校验。这些属于支撑大规模开源协作的基础设施投入。

## 3. 对项目的影响和潜在意义

- **可靠性提升**：确定性内核与 batch-invariance 测试扩展显著降低生产环境中因 batch 变化导致输出漂移的风险，对企业级部署尤为重要。
- **兼容性保障**：依赖版本升级和 block 尺寸校验避免了未来兼容性断裂，减少升级成本。
- **生态友好**：404 错误列出模型名等小改进降低了新手使用门槛，符合项目 "for everyone" 的定位。

## 4. 值得关注的技术点

- **确定性与性能的权衡**：split-K=8 的固定配置表明团队在用确定性换取可预测的批不变性，这是推理引擎中较前沿的实践。
- **FP8 稀疏解码 + 图捕获**（XPU）：将动态稀疏解码纳入静态图捕获是硬件后端适配的难点，值得其他平台参考。
- **多智能体协作痕迹明显**：多个提交的 Co-authored-by 标注了 Claude/CodeBuddy 等 AI 工具，反映出项目已形成人机协作的贡献模式。

## 5. 对项目发展的影响

结合 README 所述目标，这些提交在**不改变宏观方向的前提下夯实了质量基线**：确定性保证了服务的可复现性，多硬件修复兑现了跨平台兼容承诺，CI 强化则支撑了社区持续贡献的能力。vLLM 正从"快速可用"向"生产级可靠"稳步演进，而这批提交正是这一转型期的典型缩影——在扩展能力边界的同时，持续加固已交付功能的确定性与跨平台一致性。

## 详细提交记录

### [1388100](https://github.com/vllm-project/vllm/commit/138810056093301f4881050fcf2b1786939da387)

- **作者**: Shenglei Fu
- **时间**: 2026-10-04T22:46:16Z
- **提交信息**: [Kernel][LoRA] Add deterministic split-K=8 LoRA shrink for batch invariance (#59377)

Signed-off-by: Shenglei Fu <117230642+ShengleiFu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [7867d6c](https://github.com/vllm-project/vllm/commit/7867d6c52d4542c1b5da641f8ca79124be497ee3)

- **作者**: Tyrone
- **时间**: 2026-10-04T20:45:51Z
- **提交信息**: [Frontend] Name the served models in the model-not-found 404 (#59889)

Signed-off-by: TyroneNel <71038642+TyroneNel@users.noreply.github.com>
Signed-off-by: TyroneNel <Tyrone.Nel@gmail.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [155488d](https://github.com/vllm-project/vllm/commit/155488d853a0bc42df227dbfc74005b3fd488e94)

- **作者**: Prudhvi Vuda
- **时间**: 2026-10-04T17:07:46Z
- **提交信息**: [Bugfix][Determinism] Preserve output dtype in batch-invariant mean (#59106)

Signed-off-by: Prudhvivuda <prudhvi12042001@gmail.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b0eb87f](https://github.com/vllm-project/vllm/commit/b0eb87fe4943316781913d99a8ef8413e425decb)

- **作者**: Stefan Wang
- **时间**: 2026-10-04T16:42:49Z
- **提交信息**: [Bugfix][Frontend] Return streaming errors before the first token (#40986)

Signed-off-by: 1fanwang <1fannnw@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [89439db](https://github.com/vllm-project/vllm/commit/89439db7276cf165377c088496e20098c8137727)

- **作者**: Lio Einaudi
- **时间**: 2026-10-04T15:55:18Z
- **提交信息**: [CI][Docs] Fix decode/prefill consistency test prefix construction; add GLM-4-9B and Phi-4 to batch-invariant tested models (#53692)

Signed-off-by: Yifan Da <1363818765@qq.com>
Signed-off-by: LioEinaudi <zhao3024667639@gmail.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Yifan Da <1363818765@qq.com>
Co-authored-by: CodeBuddy <noreply@codebuddy.dev>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [bd42276](https://github.com/vllm-project/vllm/commit/bd42276e1e25f540f019381c65994120158aa2a1)

- **作者**: Divy
- **时间**: 2026-10-04T15:13:20Z
- **提交信息**: [Misc][Platform] Check aligned KV block sizes against every attention backend (#58457)

Signed-off-by: Divy <divy@coralbricks.ai>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [bdd31c3](https://github.com/vllm-project/vllm/commit/bdd31c31defd0e47a2779eb46ac1a6d88198a41b)

- **作者**: Aarushi Jain
- **时间**: 2026-10-04T14:14:27Z
- **提交信息**: [CI] Stop requiring both API servers to record weight sync metrics (#59521)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [f98d1fc](https://github.com/vllm-project/vllm/commit/f98d1fc49361cb50457f6109c3c01a5c77e415b4)

- **作者**: 00CC
- **时间**: 2026-10-04T13:48:46Z
- **提交信息**: [ROCm][Bugfix] Fix ROCM_ATTN sliding-window boundary (#59550)

Signed-off-by: tangzzycc <3081129260@qq.com>

### [d64f6cd](https://github.com/vllm-project/vllm/commit/d64f6cd08a4eb390664ed5230e6b6ae48b73bfae)

- **作者**: Taneem Ibrahim
- **时间**: 2026-10-04T13:26:10Z
- **提交信息**: [CI] Auto-label pooling PRs and issues (#59913)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [d61081d](https://github.com/vllm-project/vllm/commit/d61081dc3d3f1740a5d8bf82608b62974393c2de)

- **作者**: Harry Mellor
- **时间**: 2026-10-04T10:53:07Z
- **提交信息**: [CI] Bump peft to satisfy transformers 5.18 minimum (#59932)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [155d23c](https://github.com/vllm-project/vllm/commit/155d23cb008f793d4609d2bd5885cd9882ba38ee)

- **作者**: Yongqi Wang
- **时间**: 2026-10-04T10:31:15Z
- **提交信息**: [Bugfix][XPU] Make DeepSeek V4 FP8 sparse decode graph-capturable (#59159)

Signed-off-by: Yongqi Wang <yongqi.wang@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-05
**监控日期**: 2026-10-04
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7046
- **最后更新**: 2026-10-05T00:13:05Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 10
- **主要提交者**: Sun, quan-yi-ai, nodeeeeee

## AI分析总结

# vllm-omni 昨日提交分析

## 1. 主要更新类型

- **Bug修复（4项）**：双工音频测试线框、T2I维度校验、TRT-LLM注意力自定义算子契约、层间offload关闭问题
- **性能优化（3项）**：MammothModa2 QK norm与RoPE融合、连续批处理支持、TeaCache缓存加速
- **功能新增（2项）**：MiniMax H3多步重采样器、AR分页注意力GPU CI路由
- **架构优化（1项）**：T2I通过LLM-typed DiT阶段服务化及基准测试框架

## 2. 关键变更点与项目方向的关系

本次提交**高度集中于MammothModa2模型（5/11项）**，涵盖T2I（文生图）的维度校验、服务化路径优化、批处理与缓存加速，直接响应README中"快速且低成本的全模态模型服务"的目标。双工音频链路修复（#8489/#7644）保障了语音双向交互的可靠性，TRT-LLM算子契约（#7214）和AR注意力CI路由（#8346）则体现了对**多后端（NVIDIA/AMD）支持**的持续投入。

## 3. 对项目的影响和潜在意义

- **MammothModa2进入生产可用阶段**：从维度校验到连续批处理再到TeaCache，形成完整的服务化闭环，图像模态的性能与稳定性显著提升。
- **全模态能力增强**：音频双工链路的修复与边界控制保证了语音对话场景的鲁棒性；MiniMax H3采样器扩展了生成多样性。
- **多硬件生态扩展**：TRT-LLM算子和AMD CI支持降低了跨平台部署门槛，与omni模型"面向所有人"的普惠定位一致。
- **工程化成熟度提升**：基准测试框架与profiler接入，使性能回归可量化跟踪。

## 4. 值得关注的技术点

- **QK norm与RoPE融合（#7969）**：通过算子级融合减少kernel启动开销，是推理性能调优的典型手法。
- **TeaCache + 连续批处理的叠加**：两者组合可大幅降低长序列图像生成的计算冗余，成本优化效果值得Benchmark验证。
- **LLM-typed DiT阶段设计（#7199）**：将扩散模型阶段伪装为LLM服务路径，可能带来更统一的调度与缓存复用策略。
- **双工输出边界控制（#7644）**：拒绝已取消的音频请求，防止资源浪费，对流式交互场景关键。
- **层间offload关闭修复（#8453）**：内存管理细节影响显存受限环境下的稳定性。

## 5. 对项目发展的整体影响

结合README的全模态服务定位，本批次提交体现了三重发展策略：**一是向图像模态深耕**，通过批处理、缓存和融合优化使MammothModa2达到高效服务标准；**二是强化多模态交互可靠性**，保障语音链路的生产级稳定；**三是拓展硬件与算子生态**，通过TRT-LLM、AMD CI等投入降低部署门槛。这些提交共同推动vllm-omni从"全模态模型服务的可用"向"高效、稳定、低成本"迈进，为其"面向所有人的服务"愿景奠定技术基础。

## 详细提交记录

### [c1e84ce](https://github.com/vllm-project/vllm-omni/commit/c1e84ce9465379242d1d35fb3a25c15d9ba93358)

- **作者**: Yueqian Lin
- **时间**: 2026-10-04T23:55:19Z
- **提交信息**: [Bugfix] Wire output buffers into duplex model test harnesses (#8489)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [f781f7b](https://github.com/vllm-project/vllm-omni/commit/f781f7bb0878e83bd620377212d62e56a5a955bd)

- **作者**: bcsdhjew
- **时间**: 2026-10-04T21:06:04Z
- **提交信息**: [Core][Frontend] Bound duplex output delivery and reject cancelled audio (#7644)

Signed-off-by: Nolen Liang <nliang@nvidia.com>
Signed-off-by: bcsdhjew <nliang@nvidia.com>

### [3f20252](https://github.com/vllm-project/vllm-omni/commit/3f202521518ae43739b05facbedd4572c7c77e56)

- **作者**: Sun
- **时间**: 2026-10-04T18:44:45Z
- **提交信息**: [Model] Fuse MammothModa2 QK norm and RoPE (#7969)

Signed-off-by: levius <2114377220@qq.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [855254d](https://github.com/vllm-project/vllm-omni/commit/855254d4afe7801ad2b8b453f928a30905d5a7c8)

- **作者**: TonybotNi
- **时间**: 2026-10-04T18:43:35Z
- **提交信息**: [Bugfix] Validate MammothModa2 text-to-image dimensions (#7482)

Signed-off-by: mudrobot <mudrobot@foxmail.com>

### [65f5a1d](https://github.com/vllm-project/vllm-omni/commit/65f5a1d5b32e3d51b5dd2e758bcfb7e9dbfc2c24)

- **作者**: quan-yi-ai
- **时间**: 2026-10-04T18:42:58Z
- **提交信息**: [Bugfix][Examples][MammothModa2] Serve T2I via LLM-typed DiT stage (#7199) + benchmark harness and profiler wiring (#7293)

Signed-off-by: quan-yi-ai <82917002+quan-yi-ai@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [b9cf743](https://github.com/vllm-project/vllm-omni/commit/b9cf74352a782513913fb301cf389eeb3c913050)

- **作者**: hurukawa
- **时间**: 2026-10-04T18:22:37Z
- **提交信息**:  [Perf] Support continuous batching for MammothModa2  (#7954)

Signed-off-by: nagisa-kun <1434936049@qq.com>
Signed-off-by: nagisa <1434936049@qq.com>

### [c9c478d](https://github.com/vllm-project/vllm-omni/commit/c9c478dd07d9b8ff45d68eeeda7a78d96004bdce)

- **作者**: hurukawa
- **时间**: 2026-10-04T17:25:56Z
- **提交信息**:  [Perf] Support TeaCache for MammothModa2 (#5357)

Signed-off-by: nagisa-kun <1434936049@qq.com>
Signed-off-by: nagisa <1434936049@qq.com>

### [c9bee16](https://github.com/vllm-project/vllm-omni/commit/c9bee166fb0f0b250eb227df5d1455c03a0509a1)

- **作者**: andyluo7
- **时间**: 2026-10-04T10:13:21Z
- **提交信息**: ci: route AR paged attention tests to GPU lanes (#8346)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [4934741](https://github.com/vllm-project/vllm-omni/commit/4934741df9c8a4b1d1ffefa4e15527c5f0ea7dda)

- **作者**: Rahul Steiger
- **时间**: 2026-10-04T09:33:51Z
- **提交信息**: [Bugfix] Add TRTLLM attention custom op and execution contract (#7214)

Signed-off-by: Rahul Steiger <rsteiger@aws-cmh-slurm-1-vscode-04.cm.cluster>
Signed-off-by: Rahul Steiger <rsteiger@nvidia.com>
Co-authored-by: Rahul Steiger <rsteiger@aws-cmh-slurm-1-vscode-04.cm.cluster>

### [b65f97b](https://github.com/vllm-project/vllm-omni/commit/b65f97bc48fe09f5aba51adb4c772e9b217f3e90)

- **作者**: nodeeeeee
- **时间**: 2026-10-04T07:26:19Z
- **提交信息**: [Feature] Add MiniMax H3 res_multistep sampler (#8378)

Signed-off-by: nodeeeeee <zhangkai.nodeee@gmail.com>

### [148cb94](https://github.com/vllm-project/vllm-omni/commit/148cb943ceba3cd2cb7cd362644669427049949a)

- **作者**: YAN YIXIN
- **时间**: 2026-10-04T07:25:51Z
- **提交信息**: [Bugfix][CI/Build] Fix layerwise offload shutdown and enable it for the LTX-2 distilled T2V accuracy test (#8453)

Signed-off-by: nikiwang-125 <yixinyan79@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---
