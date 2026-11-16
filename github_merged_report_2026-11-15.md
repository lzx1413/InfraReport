# GitHub Stars 合并报告 - 2026-11-15

**合并日期**: 2026-11-16
**监控日期**: 2026-11-15
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


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2293
- **最后更新**: 2026-11-13T17:01:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3007
- **最后更新**: 2026-11-16T00:49:15Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2335
- **最后更新**: 2026-11-13T06:03:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6931
- **最后更新**: 2026-11-16T01:38:30Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: eigen

## AI分析总结

# FlashInfer 昨日提交分析（第1/1批，共2条）

## 1. 主要更新类型
- **纯性能优化**（perf），无新功能、无 Bug 修复、无文档改动。
- 两条提交都围绕同一内核：**SM100/SM103 上的 FP8 Sage 块稀疏注意力（Cake 后端）**，属于针对特定硬件代际（Blackwell/GB300 系列）的深层数值内核调优。

## 2. 关键变更点及与项目方向的关系
- **#9438（基础 PR）**：
  - 提供更快的注意力内核：sm_100a 在 `sel >= 10` 时使用 split-QK 构建，sm_103a 在 `sel >= 192` 时使用 per-tile 构建；
  - 为量化器和注意力加入 PDL（Programmatic Dependent Launch）构建；
  - 新增 eager 模式下小形状用的 one-launch 量化器；
  - **`backend="auto"` 成为默认值**，使 SM100/SM103 的 FP8 Sage 调用默认走 Cake 路径；
  - 新增融合 API `bsa_attn_sm100_sage_quantize_fwd_cake`，将量化与注意力合为一次调用。
- **#9500（后续优化 PR）**：
  - 为小形状（`seqlen_k ≤ 4096`，V 簇可占满一波 SM）新增 **one-launch TMA 量化器**（`impl="tma"`）；
  - `impl="auto"` 自动在 CUDA Graph 捕获与 eager 模式间选择该路径；
  - 输出与原量化器**逐位一致（bit-identical）**，保证可安全替换。
- 与项目方向的关系：README 核心定位是"高性能 GPU 推理内核"，这两条提交正是该定位的直接体现——把前沿量化格式（FP8 Sage）与最新 NVIDIA 架构（SM100/SM103）结合，持续压低注意力算子的端到端延迟。

## 3. 对项目的影响和潜在意义
- **性能收益明确**：#9438 在 B200 上小 sel 形状获得约 **5%–10%** 的端到端加速（如 B8/H32/S4096、sel=6 时 1.097×）；#9500 针对更小形状进一步优化量化步骤。
- **API 融合化**：量化+注意力的单一调用减少了 kernel launch 开销与中间张量往返，对 CUDA Graph 场景尤其友好——这正是 LLM 推理服务最关心的路径。
- **默认路径变更**：`backend="auto"` 默认切换意味着 Cake 路径从实验性走向生产默认，用户无需改代码即可获得加速，但也把质量责任转移到了该路径的正确性与覆盖面上（两条 PR 均强调 bit-identical 或严格基准测试来降低风险）。
- 体现了 FlashInfer 对**新硬件快速跟进**的工程能力：提交自带详尽的 CUPTI 计时基准、轮换 arm 顺序、冷 L2、置信区间，方法论严谨，有助于建立社区信任。

## 4. 值得关注的技术点
- **TMA（Tensor Memory Accelerator）用于量化**：利用 Blackwell 硬件的 TMA 异步搬运能力实现单 launch 量化，替代多 launch 方案。
- **分形状的内核特化策略**：split-QK vs per-tile 按 `sel` 阈值切换，是典型的"形状驱动特化"，说明该内核的性能高度依赖稀疏度模式。
- **PDL 与 CUDA Graph 的协同**：PDL 允许相邻 kernel 重叠，与图捕获结合可进一步压缩调度开销。
- **bit-identical 承诺**：在数值内核重构中保证逐位一致，是高质量性能 PR 的标志，便于回归验证。
- 基准方法（冷 L2、轮换顺序、成对比值区间）值得其他推理库借鉴。

## 5. 对项目发展的整体影响
结合 README，FlashInfer 的目标是成为推理场景下 GPU 内核的性能标杆。这两条提交表明项目当前的增长引擎之一是：**跟随 NVIDIA 新架构（SM100/SM103 / B200），把前沿量化方案（FP8 Sage）的块稀疏注意力打磨到极致**。将 `backend="auto"` 设为默认并提供融合 API，标志着该技术路径从"可选实验"进入"主推能力"，会强化 FlashInfer 在 Blackwell 时代推理栈中的核心地位；同时持续、可复现的性能基准文化也有助于吸引生态伙伴（如 vLLM、SGLang 等）集成其内核。总体而言，这两条提交是项目"深挖单点内核性能、快速适配新硬件"发展战略的典型且高质量的一步。

## 详细提交记录

### [67d996c](https://github.com/flashinfer-ai/flashinfer/commit/67d996c0a454cf975e91fd97dcce457b4a54b202)

- **作者**: eigen
- **时间**: 2026-11-15T13:21:07Z
- **提交信息**: perf(cake_sage_block_sparse_attention): TMA-ring Sage-FP8 quantizer for small rows on SM100/SM103 (#9500)

The Cake backend for FP8 Sage block-sparse attention has one data-type
and layout variant: FP8 E4M3 Q/K/V with per-token Q/K scales and
per-channel V scales, BF16 input and output, and the BSHD layout. It
ships in two forms: a quantize step followed by attention, and the
combined API `bsa_attn_sm100_sage_quantize_fwd_cake`. This PR speeds up
the quantize step of both forms for small shapes. It adds a one-launch
TMA quantizer (`impl="tma"`) for shapes whose V clusters fit one wave of
the device (`seqlen_k` up to 4096). `impl="auto"` takes it inside a
CUDA-graph capture, and in eager mode for the small shapes that the
existing one-launch cluster quantizer does not serve. Its output is
bit-identical to the current quantizer.

The baseline is the previous Cake version of this kernel on FlashInfer
main. The tables show end-to-end latency (quantize + attention) in µs,
as the median over 16 rounds of 50 iterations with cold L2 and CUPTI
timing; the arm order rotates across rounds. Speedup is the main latency
divided by this PR's latency, with the [min..max] of the per-round
paired ratios. A speedup above 1 means this PR is faster. `sel` is the
number of KV blocks selected per query block. The first ten rows are the
shape list of the previous PR; the last five are small shapes that this
PR targets.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA graph, CUDA 13.3 runtime (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape (D=128) | sel | main (µs) | this PR, default path (µs) | speedup
| main, combined API (µs) | this PR, combined API (µs) | speedup |
|---|---|---|---|---|---|---|---|
| B8/H32/S4096 | 6 | 485.3 | 485.9 | 0.999 [0.997..1.002] | 485.4 |
485.9 | 0.999 [0.997..1.003] |
| B8/H32/S4096 | 32 | 1221.8 | 1214.6 | 1.006 [0.981..1.038] | 1214.7 |
1203.7 | 1.009 [0.988..1.033] |
| B8/H32/S4096 | 58 | 1986.7 | 1982.8 | 1.002 [0.961..1.039] | 2021.6 |
1991.6 | 1.015 [0.962..1.047] |
| B1/H8/S4096 | 6 | 26.4 | 23.8 | 1.109 [1.068..1.137] | 26.1 | 23.9 |
1.090 [1.060..1.107] |
| B1/H8/S4096 | 32 | 54.6 | 51.5 | 1.060 [1.055..1.075] | 54.6 | 51.6 |
1.058 [1.053..1.072] |
| B1/H8/S4096 | 58 | 82.0 | 78.1 | 1.050 [1.046..1.052] | 81.8 | 78.1 |
1.048 [1.044..1.053] |
| B1/H40/S32768 | 51 | 2341.7 | 2345.0 | 0.999 [0.969..1.050] | 2377.7 |
2353.3 | 1.010 [0.945..1.072] |
| B1/H40/S32768 | 128 | 5254.0 | 5282.7 | 0.995 [0.976..1.004] | 5233.9
| 5237.8 | 0.999 [0.980..1.026] |
| B1/H40/S32768 | 256 | 9968.0 | 9953.5 | 1.001 [0.989..1.006] | 9953.1
| 9956.1 | 1.000 [0.992..1.006] |
| B2/H24/S16384 | 32 | 915.4 | 914.8 | 1.001 [0.994..1.020] | 915.0 |
915.0 | 1.000 [0.980..1.010] |
| B1/H2/S4096 | 6 | 15.0 | 12.5 | 1.205 [1.128..1.300] | 14.3 | 12.4 |
1.152 [1.116..1.271] |
| B1/H2/S4096 | 58 | 29.6 | 26.6 | 1.111 [1.057..1.137] | 29.2 | 26.7 |
1.094 [1.054..1.131] |
| B1/H4/S4096 | 6 | 19.2 | 15.9 | 1.209 [1.180..1.241] | 19.4 | 15.7 |
1.234 [1.185..1.241] |
| B1/H4/S4096 | 58 | 47.8 | 43.8 | 1.092 [1.079..1.096] | 47.8 | 43.8 |
1.092 [1.060..1.099] |
| B1/H32/Hkv8/S4096 | 6 | 56.4 | 55.9 | 1.010 [0.988..1.020] | 56.4 |
56.0 | 1.007 [0.988..1.019] |

**NVIDIA B200 (sm_100a, 148 SMs), eager, CUDA 13.3 runtime (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape (D=128) | sel | main (µs) | this PR, default path (µs) | speedup
| main, combined API (µs) | this PR, combined API (µs) | speedup |
|---|---|---|---|---|---|---|---|
| B8/H32/S4096 | 6 | 493.9 | 494.1 | 1.000 [0.996..1.004] | 495.5 |
495.6 | 1.000 [0.997..1.005] |
| B8/H32/S4096 | 32 | 1215.0 | 1216.4 | 0.999 [0.976..1.026] | 1243.2 |
1243.2 | 1.000 [0.975..1.025] |
| B8/H32/S4096 | 58 | 1996.2 | 1991.7 | 1.002 [0.985..1.040] | 2025.0 |
2025.5 | 1.000 [0.963..1.031] |
| B1/H8/S4096 | 6 | 58.0 | 58.0 | 0.999 [0.980..1.026] | 27.9 | 27.9 |
0.999 [0.981..1.003] |
| B1/H8/S4096 | 32 | 86.5 | 86.7 | 0.998 [0.986..1.015] | 56.5 | 56.4 |
1.001 [0.998..1.002] |
| B1/H8/S4096 | 58 | 114.5 | 114.4 | 1.001 [0.992..1.012] | 84.0 | 83.9
| 1.002 [0.999..1.003] |
| B1/H40/S32768 | 51 | 2331.1 | 2320.8 | 1.004 [0.963..1.031] | 2367.4 |
2366.8 | 1.000 [0.942..1.046] |
| B1/H40/S32768 | 128 | 5139.1 | 5156.8 | 0.997 [0.980..1.010] | 5245.4
| 5245.1 | 1.000 [0.985..1.011] |
| B1/H40/S32768 | 256 | 9954.6 | 9911.2 | 1.004 [0.992..1.012] | 9959.7
| 9960.9 | 1.000 [0.994..1.005] |
| B2/H24/S16384 | 32 | 925.2 | 925.7 | 0.999 [0.998..1.006] | 942.6 |
941.4 | 1.001 [0.955..1.012] |
| B1/H2/S4096 | 6 | 50.2 | 50.3 | 0.998 [0.980..1.019] | 18.7 | 18.5 |
1.011 [0.978..1.077] |
| B1/H2/S4096 | 58 | 64.7 | 64.7 | 1.000 [0.983..1.020] | 33.0 | 33.0 |
1.001 [0.992..1.004] |
| B1/H4/S4096 | 6 | 52.8 | 53.1 | 0.995 [0.980..1.020] | 21.7 | 21.7 |
1.000 [0.993..1.006] |
| B1/H4/S4096 | 58 | 81.9 | 82.2 | 0.996 [0.982..1.021] | 50.6 | 50.5 |
1.001 [0.998..1.006] |
| B1/H32/Hkv8/S4096 | 6 | 96.1 | 84.6 | 1.136 [1.124..1.166] | 63.2 |
56.2 | 1.123 [1.102..1.134] |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA graph, CUDA 13.3 runtime (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape (D=128) | sel | main (µs) | this PR, default path (µs) | speedup
| main, combined API (µs) | this PR, combined API (µs) | speedup |
|---|---|---|---|---|---|---|---|
| B8/H32/S4096 | 6 | 450.5 | 450.3 | 1.000 [0.999..1.002] | 450.4 |
450.3 | 1.000 [0.999..1.002] |
| B8/H32/S4096 | 32 | 975.0 | 975.2 | 1.000 [0.999..1.001] | 974.9 |
974.8 | 1.000 [0.999..1.001] |
| B8/H32/S4096 | 58 | 1510.8 | 1510.7 | 1.000 [0.999..1.000] | 1510.5 |
1510.6 | 1.000 [0.999..1.001] |
| B1/H8/S4096 | 6 | 24.6 | 22.3 | 1.102 [1.056..1.133] | 25.1 | 22.2 |
1.128 [1.057..1.137] |
| B1/H8/S4096 | 32 | 45.1 | 41.8 | 1.078 [1.057..1.085] | 45.0 | 41.8 |
1.078 [1.062..1.086] |
| B1/H8/S4096 | 58 | 64.5 | 61.6 | 1.048 [1.041..1.056] | 64.7 | 61.6 |
1.050 [1.040..1.058] |
| B1/H40/S32768 | 51 | 1765.3 | 1765.0 | 1.000 [1.000..1.001] | 1764.9 |
1765.2 | 1.000 [0.999..1.000] |
| B1/H40/S32768 | 128 | 3660.1 | 3662.3 | 0.999 [0.996..1.004] | 3698.5
| 3697.2 | 1.000 [0.996..1.010] |
| B1/H40/S32768 | 256 | 6989.7 | 7002.9 | 0.998 [0.995..1.010] | 6976.3
| 6974.3 | 1.000 [0.996..1.012] |
| B2/H24/S16384 | 32 | 736.2 | 736.4 | 1.000 [0.999..1.001] | 736.4 |
736.4 | 1.000 [0.999..1.001] |
| B1/H2/S4096 | 6 | 13.7 | 11.5 | 1.188 [1.139..1.280] | 13.3 | 11.5 |
1.153 [1.129..1.285] |
| B1/H2/S4096 | 58 | 24.0 | 21.6 | 1.111 [1.073..1.148] | 23.7 | 21.6 |
1.097 [1.069..1.144] |
| B1/H4/S4096 | 6 | 18.0 | 14.8 | 1.220 [1.186..1.252] | 17.7 | 14.8 |
1.196 [1.184..1.234] |
| B1/H4/S4096 | 58 | 38.0 | 34.8 | 1.091 [1.080..1.103] | 37.9 | 34.8 |
1.089 [1.079..1.105] |
| B1/H32/Hkv8/S4096 | 6 | 51.2 | 50.3 | 1.019 [1.010..1.032] | 51.3 |
50.1 | 1.022 [1.007..1.028] |

**NVIDIA GB300 (sm_103a, 152 SMs), eager, CUDA 13.3 runtime (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape (D=128) | sel | main (µs) | this PR, default path (µs) | speedup
| main, combined API (µs) | this PR, combined API (µs) | speedup |
|---|---|---|---|---|---|---|---|
| B8/H32/S4096 | 6 | 465.6 | 465.7 | 1.000 [0.996..1.002] | 466.4 |
466.4 | 1.000 [0.998..1.001] |
| B8/H32/S4096 | 32 | 991.2 | 991.8 | 0.999 [0.999..1.001] | 992.0 |
991.6 | 1.000 [0.998..1.001] |
| B8/H32/S4096 | 58 | 1527.1 | 1526.9 | 1.000 [0.999..1.002] | 1527.6 |
1527.0 | 1.000 [0.999..1.002] |
| B1/H8/S4096 | 6 | 93.8 | 88.5 | 1.060 [0.944..1.199] | 32.4 | 31.3 |
1.034 [0.909..1.157] |
| B1/H8/S4096 | 32 | 105.2 | 104.4 | 1.008 [0.982..1.028] | 51.0 | 50.8
| 1.004 [0.986..1.023] |
| B1/H8/S4096 | 58 | 124.9 | 124.4 | 1.003 [0.984..1.022] | 70.9 | 70.8
| 1.002 [0.990..1.018] |
| B1/H40/S32768 | 51 | 1781.5 | 1781.2 | 1.000 [1.000..1.001] | 1781.3 |
1781.5 | 1.000 [0.999..1.000] |
| B1/H40/S32768 | 128 | 3672.4 | 3672.7 | 1.000 [0.999..1.003] | 3687.0
| 3687.9 | 1.000 [0.985..1.010] |
| B1/H40/S32768 | 256 | 6894.3 | 6894.0 | 1.000 [0.992..1.004] | 6980.2
| 6987.5 | 0.999 [0.992..1.005] |
| B2/H24/S16384 | 32 | 752.3 | 753.3 | 0.999 [0.997..1.001] | 753.1 |
753.1 | 1.000 [0.999..1.001] |
| B1/H2/S4096 | 6 | 77.7 | 77.5 | 1.003 [0.974..1.069] | 24.1 | 24.1 |
1.000 [0.967..1.041] |
| B1/H2/S4096 | 58 | 87.4 | 88.1 | 0.992 [0.969..1.032] | 34.1 | 34.2 |
0.997 [0.954..1.025] |
| B1/H4/S4096 | 6 | 81.0 | 80.4 | 1.006 [0.970..1.037] | 26.6 | 26.7 |
0.997 [0.963..1.041] |
| B1/H4/S4096 | 58 | 100.8 | 101.1 | 0.997 [0.968..1.024] | 47.1 | 47.0
| 1.002 [0.984..1.023] |
| B1/H32/Hkv8/S4096 | 6 | 134.4 | 107.1 | 1.255 [1.183..1.321] | 74.2 |
53.2 | 1.395 [1.337..1.438] |

Cake ships only this FP8 Sage variant of the kernel (BSHD, in the
quantize-then-attention and combined forms), for sm_100a and sm_103a.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a TMA quantization option for supported SM100/SM103 shapes, with
automatic selection and fallback to existing launch strategies.
* Added two TMA variants and expanded build support for SM100 and SM103.

* **Bug Fixes**
* Improved handling of unsupported shapes, occupancy checks during CUDA
Graph capture, and oversized work partitions.

* **Tests**
* Added coverage for TMA output consistency, routing, capture behavior,
and input validation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [0132cbc](https://github.com/flashinfer-ai/flashinfer/commit/0132cbc015787b0fcb04f2357ee31d405dc2b9c5)

- **作者**: eigen
- **时间**: 2026-11-15T07:47:34Z
- **提交信息**: perf(cake_sage_block_sparse_attention): faster FP8 Sage block-sparse attention on SM100/SM103, combined quantize+attention API, auto backend default (#9438)

The Cake backend for FP8 Sage block-sparse attention has one data-type
and layout variant. Q/K/V are FP8 E4M3 with per-token Q/K scales and
per-channel V scales, input and output are BF16, and the layout is BSHD.
Until now it ran in one form: a quantize step followed by attention.
This PR makes that variant faster and adds a second, fused form:

- A faster attention kernel. sm_100a uses a split-QK build for sel >=
10, and sm_103a uses a per-tile build for sel >= 192.
- PDL builds of the quantizers and of attention.
- A one-launch quantizer that eager mode uses for small shapes.
- `backend="auto"` is now the default, so SM100/SM103 FP8 Sage calls go
to the Cake path.
- A new combined API, `bsa_attn_sm100_sage_quantize_fwd_cake`, that runs
quantization and attention in one call.

The baseline is the previous Cake version of this kernel on FlashInfer
main. The tables show end-to-end latency (quantize + attention) in µs,
as the median over 8 rounds of 50 iterations with cold L2 and CUPTI
timing; arm order rotates across rounds. Speedup is FlashInfer main
latency divided by this PR's latency, paired per round: the median, with
[min..max] over the 8 rounds. A speedup above 1 means this PR is faster.
`sel` is the number of KV blocks selected per query block.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA graph, CUDA 13.3 runtime (torch
2.13 nv26.07)**

| shape (B/H/S, D=128) | sel | main (µs) | this PR, default path (µs) |
speedup | this PR, combined API (µs) | speedup |
|---|---|---|---|---|---|---|
| B8/H32/S4096 | 6 | 544.4 | 496.6 | 1.097 [1.093..1.100] | 496.0 |
1.097 [1.095..1.100] |
| B8/H32/S4096 | 32 | 1279.4 | 1216.6 | 1.051 [1.050..1.071] | 1218.4 |
1.052 [1.017..1.070] |
| B8/H32/S4096 | 58 | 2059.8 | 2002.2 | 1.023 [1.014..1.071] | 2024.5 |
1.017 [1.001..1.044] |
| B1/H8/S4096 | 6 | 29.6 | 27.8 | 1.064 [1.020..1.081] | 28.0 | 1.046
[1.036..1.095] |
| B1/H8/S4096 | 32 | 57.7 | 56.0 | 1.028 [1.015..1.039] | 55.9 | 1.028
[1.019..1.042] |
| B1/H8/S4096 | 58 | 86.1 | 83.0 | 1.033 [1.030..1.038] | 83.2 | 1.031
[1.025..1.041] |
| B1/H40/S32768 | 51 | 2390.6 | 2365.9 | 1.005 [0.966..1.056] | 2354.6 |
1.010 [1.008..1.047] |
| B1/H40/S32768 | 128 | 5396.5 | 5236.7 | 1.036 [1.022..1.043] | 5259.7
| 1.027 [1.004..1.039] |
| B1/H40/S32768 | 256 | 10232.8 | 9913.4 | 1.032 [1.029..1.047] | 9914.1
| 1.033 [1.021..1.046] |
| B2/H24/S16384 | 32 | 961.8 | 931.4 | 1.037 [1.028..1.039] | 927.8 |
1.037 [1.008..1.048] |

**NVIDIA B200 (sm_100a, 148 SMs), eager, CUDA 13.3 runtime (torch 2.13
nv26.07)**

| shape (B/H/S, D=128) | sel | main (µs) | this PR, default path (µs) |
speedup | this PR, combined API (µs) | speedup |
|---|---|---|---|---|---|---|
| B8/H32/S4096 | 6 | 562.4 | 504.6 | 1.115 [1.112..1.117] | 505.7 |
1.114 [1.110..1.115] |
| B8/H32/S4096 | 32 | 1298.4 | 1225.8 | 1.059 [1.039..1.062] | 1241.8 |
1.048 [1.038..1.059] |
| B8/H32/S4096 | 58 | 2094.5 | 1994.5 | 1.046 [1.013..1.058] | 1996.6 |
1.051 [1.008..1.067] |
| B1/H8/S4096 | 6 | 73.6 | 58.1 | 1.265 [1.240..1.296] | 28.8 | 2.559
[2.509..2.602] |
| B1/H8/S4096 | 32 | 101.9 | 86.7 | 1.173 [1.161..1.206] | 57.4 | 1.774
[1.763..1.815] |
| B1/H8/S4096 | 58 | 131.1 | 114.6 | 1.143 [1.123..1.163] | 85.0 | 1.543
[1.514..1.555] |
| B1/H40/S32768 | 51 | 2408.4 | 2313.1 | 1.034 [1.014..1.056] | 2356.5 |
1.024 [1.010..1.039] |
| B1/H40/S32768 | 128 | 5416.2 | 5245.0 | 1.033 [1.016..1.058] | 5252.6
| 1.031 [1.014..1.041] |
| B1/H40/S32768 | 256 | 10279.2 | 9921.0 | 1.036 [1.030..1.043] | 9922.7
| 1.036 [1.030..1.043] |
| B2/H24/S16384 | 32 | 982.4 | 935.2 | 1.050 [1.032..1.056] | 937.2 |
1.047 [1.040..1.054] |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA graph, CUDA 13.3 runtime (torch
2.13 nv26.07)**

| shape (B/H/S, D=128) | sel | main (µs) | this PR, default path (µs) |
speedup | this PR, combined API (µs) | speedup |
|---|---|---|---|---|---|---|
| B8/H32/S4096 | 6 | 490.8 | 457.0 | 1.074 [1.072..1.076] | 457.0 |
1.074 [1.071..1.077] |
| B8/H32/S4096 | 32 | 1029.9 | 980.9 | 1.050 [1.048..1.051] | 980.7 |
1.050 [1.048..1.052] |
| B8/H32/S4096 | 58 | 1558.2 | 1514.6 | 1.029 [1.021..1.030] | 1514.8 |
1.029 [1.028..1.030] |
| B1/H8/S4096 | 6 | 26.5 | 26.2 | 1.017 [1.000..1.048] | 26.0 | 1.026
[1.000..1.034] |
| B1/H8/S4096 | 32 | 47.0 | 46.2 | 1.022 [1.010..1.037] | 46.1 | 1.021
[1.010..1.036] |
| B1/H8/S4096 | 58 | 66.8 | 66.2 | 1.013 [1.008..1.019] | 65.9 | 1.015
[1.005..1.026] |
| B1/H40/S32768 | 51 | 1782.1 | 1769.8 | 1.007 [1.006..1.009] | 1770.0 |
1.007 [1.005..1.009] |
| B1/H40/S32768 | 128 | 3660.6 | 3697.3 | 0.992 [0.987..1.002] | 3668.2
| 0.999 [0.997..1.004] |
| B1/H40/S32768 | 256 | 7009.2 | 6979.7 | 1.001 [0.997..1.006] | 7031.8
| 0.997 [0.989..1.005] |
| B2/H24/S16384 | 32 | 761.4 | 744.0 | 1.023 [1.022..1.025] | 744.0 |
1.023 [1.022..1.025] |

**NVIDIA GB300 (sm_103a, 152 SMs), eager, CUDA 13.3 runtime (torch 2.13
nv26.07)**

| shape (B/H/S, D=128) | sel | main (µs) | this PR, default path (µs) |
speedup | this PR, combined API (µs) | speedup |
|---|---|---|---|---|---|---|
| B8/H32/S4096 | 6 | 528.3 | 472.3 | 1.119 [1.115..1.126] | 471.8 |
1.119 [1.116..1.130] |
| B8/H32/S4096 | 32 | 1063.5 | 996.2 | 1.068 [1.066..1.069] | 996.3 |
1.068 [1.066..1.068] |
| B8/H32/S4096 | 58 | 1592.5 | 1528.9 | 1.042 [1.041..1.042] | 1529.3 |
1.041 [1.041..1.042] |
| B1/H8/S4096 | 6 | 116.8 | 83.3 | 1.403 [1.328..1.424] | 30.6 | 3.784
[3.679..3.936] |
| B1/H8/S4096 | 32 | 136.8 | 102.7 | 1.339 [1.309..1.352] | 50.6 | 2.703
[2.660..2.758] |
| B1/H8/S4096 | 58 | 157.0 | 122.6 | 1.275 [1.261..1.307] | 70.6 | 2.220
[2.186..2.287] |
| B1/H40/S32768 | 51 | 1819.0 | 1787.4 | 1.018 [1.015..1.020] | 1787.5 |
1.018 [1.015..1.022] |
| B1/H40/S32768 | 128 | 3695.2 | 3700.7 | 0.999 [0.993..1.007] | 3669.0
| 1.007 [1.005..1.008] |
| B1/H40/S32768 | 256 | 7085.4 | 6979.9 | 1.015 [1.002..1.021] | 7055.2
| 1.006 [0.989..1.007] |
| B2/H24/S16384 | 32 | 796.3 | 758.7 | 1.049 [1.048..1.052] | 759.1 |
1.049 [1.047..1.051] |

Cake ships only this FP8 Sage variant of the kernel (BSHD, in the
quantize-then-attention and combined forms), for sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added automatic backend selection for block-sparse attention,
alongside explicit Cake and CuTe choices.
* Added a combined BF16 quantization-and-attention operation and
configurable one- or two-launch quantization.
* Added PDL controls, enabled by default on supported GPUs, and expanded
support for SM100 and SM103.
  * Added fallback dispatch and fake-tensor support.
* **Bug Fixes**
* Improved attention scale handling and validation of tensor alignment,
layouts, and launch parameters.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4820
- **最后更新**: 2026-11-15T13:48:10Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 2
- **主要提交者**: Aryan Kumar, wuyaole

## AI分析总结

## hao-ai-lab/FastVideo 昨日提交分析（第 1/1 批，共 5 条）

### 1. 主要更新类型
- **功能新增（3 条）**：种子扫描时复用文本条件、单服务器多模型目录与按需切换、DGX Spark 上的统一内存修复与可选优化开关
- **性能优化（1 条）**：Open-H3-Regenerate-2K 在 DGX Spark 上的多项加速选项
- **Bug 修复（1 条）**：Ray 执行器原生服务健康状态上报
- **CI/工程（1 条）**：Spark CI 流水线同步 fastvideo-kernel

### 2. 关键变更点与项目方向的关系
- **多模型服务化**：一次 FastVideo 服务器承载 FastH3 + 2K 两个模型、单 GPU 按需切换，直指 README 中强调的推理 Quick Start 与部署便利性，推动项目从"单模型推理脚本"走向"统一推理服务"。
- **种子扫描复用文本条件**：针对 MiniMax-H3 文本条件在多次种子实验中重复计算的浪费进行消除，属于训练/评估工作流的效率优化，契合 FastVideo 高效视频生成的核心目标。
- **DGX Spark 硬件适配**：统一内存（unified-memory）修复、Sol-Attn、MXFP8、fast-decoder 等按需开关，显示项目正积极扩展到 NVIDIA 新一代 DGX Spark 平台，属于硬件生态扩展。
- **CI 与服务健康**：kernel 同步与 Ray 健康上报是支撑上述功能稳定落地的基础设施补强。

### 3. 对项目的影响和潜在意义
- **降低使用门槛**：多模型目录与按需切换意味着用户无需为每个模型单独起服务，显著改善 Cookbook/Quick Start 体验。
- **提升吞吐与硬件利用率**：文本条件复用和 MXFP8/Sol-Attn 等优化可降低显存与计算开销，对研究者快速迭代实验价值明显。
- **生产就绪度提升**：健康状态上报与 CI 修复增强了服务的可观测性和持续交付能力，是从研究原型向可用服务演进的关键一步。
- **平台覆盖扩大**：DGX Spark 支持为社区提供了新的硬件选择，有助于吸引更广泛的用户群体。

### 4. 值得关注的技术点
- **Sol-Attn**：疑似新型注意力机制实现，需关注其在视频长序列上的内存/速度权衡。
- **MXFP8 按需开关**：低精度训练/推理的可配置化，是精度-性能折中的灵活方案。
- **统一内存修复**：DGX Grace-Hopper 架构下 CPU/GPU 内存共享的踩坑经验，对类似平台移植有参考价值。
- **单 GPU 多模型切换**：涉及模型加载策略、显存预算管理，是资源受限场景下的实用设计。
- **Ray 原生服务健康**：与 Ray 生态的深度集成点，影响分布式部署可靠性。

### 5. 基于 README 背景的项目发展影响
README 展示 FastVideo 是一个面向文档、Cookbook、快速入门和社区协作（周会、Slack）的成熟开源项目。本批提交表明项目正沿三条主线推进：**（a）服务化与易用性**（多模型目录、健康上报）直接强化 Quick Start 与 Cookbook 的落地体验；**（b）性能与硬件前沿**（DGX Spark、MXFP8、Sol-Attn）保持项目在高效视频生成领域的技术领先性；**（c）工程质量**（CI kernel 同步、bugfix）保障社区协作的稳定性。这些提交共同推动 FastVideo 从"研究工具集"向"生产级高效视频推理平台"演进，与项目"Fast"（高效）的品牌定位高度一致，也为后续吸引更多模型接入和硬件平台奠定了基础。

## 详细提交记录

### [c938a8a](https://github.com/hao-ai-lab/FastVideo/commit/c938a8aa2b856a594f791a61875ba0bdac5ef318)

- **作者**: wuyaole
- **时间**: 2026-11-15T18:21:00Z
- **提交信息**: [feat] Reuse MiniMax-H3 text conditioning across seed sweeps (#2022)

Signed-off-by: wuyaole <112309453+LeslieWylie@users.noreply.github.com>
Co-authored-by: wuyaole <112309453+LeslieWylie@users.noreply.github.com>

### [1a41551](https://github.com/hao-ai-lab/FastVideo/commit/1a41551d529c1298d0600a2e394f9537219748ea)

- **作者**: Aryan Kumar
- **时间**: 2026-11-15T04:22:28Z
- **提交信息**: [feat] Serve a model catalog from one FastVideo server with on-demand switching (FastH3 + 2K on one GPU) (#2099)

Co-authored-by: mk2k <mk2k@local>
Co-authored-by: mk2k <mk2k@spark>
Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [e4d9d8b](https://github.com/hao-ai-lab/FastVideo/commit/e4d9d8bc12d7466777e41b0f75212754c490a5fb)

- **作者**: Aryan Kumar
- **时间**: 2026-11-15T03:08:29Z
- **提交信息**: [perf] Open-H3-Regenerate-2K on DGX Spark: unified-memory fixes, Sol-Attn, MXFP8 and fast-decoder opt-ins (#2093)


Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [cbf011f](https://github.com/hao-ai-lab/FastVideo/commit/cbf011f3fb6179eff687ae26a21a43b23dc77d3e)

- **作者**: Aryan Kumar
- **时间**: 2026-11-15T01:38:52Z
- **提交信息**: [ci] Sync fastvideo-kernel to the checkout on Spark CI lanes (#2111)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [697adde](https://github.com/hao-ai-lab/FastVideo/commit/697adde1446b8a3de1e66811afa6379c7b9fbd33)

- **作者**: Aryan Kumar
- **时间**: 2026-11-15T01:37:40Z
- **提交信息**: [bugfix] Report native serving health for Ray executors (#2090)

Co-authored-by: fv-superagent <352344047+fv-superagent@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34917
- **最后更新**: 2026-11-15T12:39:14Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-11-12T08:10:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13368
- **最后更新**: 2026-11-15T04:06:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38916
- **最后更新**: 2026-11-16T02:09:24Z

## 提交统计

- **昨日提交总数**: 59
- **提交者数量**: 30
- **主要提交者**: Han-Yin Chang, jlqibm, Yuxuan Zhou

## AI分析总结

# SGLang 昨日提交分析（59条）

## 1. 主要更新类型分布

- **性能优化**：约20条，占比最高，涵盖扩散模型内核、内存缓存、GDN注意力、流水线调度等。
- **Bug修复**：约25条，覆盖AMD/NPU/NVIDIA多硬件后端、扩散模型、分布式通信、安全鉴权等。
- **CI/基础设施**：约12条，集中在rerun-test框架、NPU/AMD nightly构建、Rust编译配置。
- **功能新增**：约8条，包括Mamba状态驱逐策略、JIT事件追踪、GR/PLE序列并行等。
- **重构**：3条（多模态处理器解耦、鉴权路由表统一、克隆测试解析器）。

## 2. 关键变更点与项目方向的关系

**扩散模型（Diffusion）大規模修复与优化**：约15条提交针对qwen-image、Wan视频、HunyuanVideo、LTX-2、MiniMax-H3等扩散模型，修正张量尺寸对齐、PDL请求条件、RMSNorm通道维度等正确性问题，同时在QK-norm+RoPE融合、SDPA写入、注意力残差融合上做warp级内核优化。这表明SGLang正加速将扩散模型作为一等公民纳入推理框架。

**多硬件平台适配深化**：AMD（gfx1250 ring all-reduce、aiter Triton缓存修复、ROCm镜像构建sgl-router）、NPU（nightly跑检出代码、镜像内嵌路由器）、NVIDIA（SM12x FP8确定性、AR-fusion对称缓冲）均有系统性投入，体现跨硬件可移植的平台化战略。

**内存缓存与统一内存优化链**：#50307-50311五连提交形成完整系列——GDN预填充就地执行、无主机读的统一内存释放、字宽级状态清拷、批量槽位/页分配、准入主机工作削减，直指统一内存（如Apple Silicon/HBM共享架构）场景下的延迟瓶颈。

**Mamba/线性注意力状态管理**：新增state_cost驱逐策略（#50122）、GDN MIS状态重置避免主机同步、int64偏移修复，表明对线性注意力模型的生产级支持在推进。

## 3. 对项目的影响和潜在意义

- **稳定性提升**：鉴权路由表统一（Python/Rust双读）修复了内部端点安全漏洞；权重manifest预校验防止分布式广播失败。
- **运维成熟度**：rerun-test框架连续5次演进（fork令牌隔离、`--hw`参数、AMD/NPU单节点覆盖），CI从"能跑"走向"安全可控地重跑"。
- **流水线并行修正**：PD轮询与grammar同步按流水线深度限界（#50481），修复PP场景下潜在的无界阻塞。

## 4. 值得关注的技术点

- **JIT内核事件追踪（IKET与%clock后端）**：为GPU内核提供调试级时间线，是深度性能诊断的基础设施。
- **扩散内核warp级优化模式**：多条提交采用"每warp处理一个token的heads"等策略，反映内核调优已进入细粒度阶段。
- **AI辅助开发痕迹明显**：Claude Opus/Fable、Copilot等多次出现在Co-authored-by中，大型项目的AI协同开发已成常态。
- **causal Conv1D出树dispatch**：为树外自定义算子提供注册通道，扩展性架构决策。

## 5. 对项目发展的整体影响

结合README的定位（Fast inference for LLMs and multimodal models），这批提交显示SGLang三条主线并进：**多模态扩散模型推理**正从"能跑"走向"正确且高效"；**多硬件后端**（AMD/NPU/ROCm）的工程化程度显著提升，路由组件已内嵌进各厂商镜像；**统一内存与线性注意力**等新硬件范式的适配走在同类框架前列。短期内项目将获得更好的跨平台部署体验和扩散模型吞吐，中长期则为更广泛的异构硬件生态和多模态统一推理奠定基础。

## 详细提交记录

### [e896a5b](https://github.com/sgl-project/sglang/commit/e896a5be0267fca719fc98063d7feb4d4ddc1b7d)

- **作者**: Matti Varjokallio
- **时间**: 2026-11-15T23:26:03Z
- **提交信息**: [Fix] [AMD] dsa: Fix Triton cache flooding in aiter backend (#33506)

Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>

### [73c0e14](https://github.com/sgl-project/sglang/commit/73c0e14438cdaf5fd77c3b46aea28c9f81c6652e)

- **作者**: Yuxuan Zhang
- **时间**: 2026-11-15T23:24:56Z
- **提交信息**: [Fix] dp-attention: Deliver an abort behind its request on every DP rank (#50147)

### [0c283d8](https://github.com/sgl-project/sglang/commit/0c283d85be925b95148ce0a811811023260574bc)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T23:21:21Z
- **提交信息**: [Chore] pre-commit: Skip sglang-server in the clippy hook on macOS (#50655)

### [2726766](https://github.com/sgl-project/sglang/commit/27267664e9b5be98f82b9a60065095559b05fc86)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T21:57:11Z
- **提交信息**: [CI] amd: Build sgl-router in the ROCm image and launch it in the MI355X PD nightly (#50604)

### [0d08c7c](https://github.com/sgl-project/sglang/commit/0d08c7cc709dd0154a96c7e96ce82538d99294e1)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T21:50:05Z
- **提交信息**: [Fix] tokenizer_manager: Validate token_indices_to_pool at request entry (#49759)

### [302e0d1](https://github.com/sgl-project/sglang/commit/302e0d12e129a3e48f7a7ed02cd5d026220c4539)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T21:49:34Z
- **提交信息**: [CI] rerun-test: Keep the job token away from fork code, mark NPU runs running, and take --hw in /rerun-group (#50603)

### [d3f31fc](https://github.com/sgl-project/sglang/commit/d3f31fcd11f6ddbdf0d44ead2e2c57b7ecfe5a14)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T21:48:54Z
- **提交信息**: [CI] rust: Build the CI Rust extensions with a thin-LTO `ci` profile (#50606)

### [fd4b4fd](https://github.com/sgl-project/sglang/commit/fd4b4fdd7385f172fd5c1b98d904cd8ceff77e0e)

- **作者**: Wenkai Du
- **时间**: 2026-11-15T18:27:45Z
- **提交信息**: [Feat] [AMD] custom-all-reduce: Add a ring all-reduce and an unrolled 2shot_push on gfx1250 (#49955)

### [8f44124](https://github.com/sgl-project/sglang/commit/8f44124e6010351daffbd5c1d1754b3fa05d2c6c)

- **作者**: DarkSharpness
- **时间**: 2026-11-15T16:41:20Z
- **提交信息**: [Feat] JIT: In-kernel event tracing for debugging (IKET and %clock backends) (#50374)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e4c3f00](https://github.com/sgl-project/sglang/commit/e4c3f001d6bc8cb43e778b6b27d562af550db8c9)

- **作者**: shiyang.814
- **时间**: 2026-11-15T13:45:41Z
- **提交信息**: [Feat] qwen4-exp: Support GR and PLE sequence parallelism (#43048)

Co-authored-by: reviewer <reviewer@example.com>

### [463e86e](https://github.com/sgl-project/sglang/commit/463e86e077107b030cd8eac45fb1512f317022ce)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-15T13:42:08Z
- **提交信息**: [Fix] diffusion/qwen-image-2.1: Size edit outputs and references as Diffusers does (#50358)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [388b190](https://github.com/sgl-project/sglang/commit/388b190aec60ee7d8f5b8d2b23f5f01d30e9c4a2)

- **作者**: Shuwen Wang
- **时间**: 2026-11-15T13:40:33Z
- **提交信息**: [Fix] hicache: Report L3 prefetch tokens already cached during the read (#49328)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [a51b0e2](https://github.com/sgl-project/sglang/commit/a51b0e2b848fd5161813bbdec5ecdde5ac3cc6f2)

- **作者**: Cheng Wan
- **时间**: 2026-11-15T12:12:21Z
- **提交信息**: [Perf] mem_cache: Cut unified-memory admission host work (#50311)

### [9ae8cf0](https://github.com/sgl-project/sglang/commit/9ae8cf060880be6a3ab97cebfc5edb3e191bac9c)

- **作者**: Cheng Wan
- **时间**: 2026-11-15T12:11:53Z
- **提交信息**: [Perf] mem_cache: Batch unified-memory slot and page hand-outs (#50310)

### [fd510c5](https://github.com/sgl-project/sglang/commit/fd510c505f95d6b7b1b13740a50d3e1c49816053)

- **作者**: Cheng Wan
- **时间**: 2026-11-15T12:11:25Z
- **提交信息**: [Perf] mem_cache: Relieve unified memory without host reads (#50309)

### [a7da11b](https://github.com/sgl-project/sglang/commit/a7da11be3d09abc8f87310b9b489085394bd2387)

- **作者**: Cheng Wan
- **时间**: 2026-11-15T12:10:57Z
- **提交信息**: [Perf] mem_cache: Clear and copy unified-memory state entries word-wide (#50308)

### [ff68baa](https://github.com/sgl-project/sglang/commit/ff68baae6dce5650405b4532fc373411008e90e2)

- **作者**: Cheng Wan
- **时间**: 2026-11-15T12:10:27Z
- **提交信息**: [Perf] gdn: Run GDN prefill in place on a unified-memory state pool (#50307)

### [03d4f49](https://github.com/sgl-project/sglang/commit/03d4f49f22220cb56ad00a30a324b35e267560ce)

- **作者**: Cheng Wan
- **时间**: 2026-11-15T12:09:46Z
- **提交信息**: [Perf] gdn: Remove host stalls from GDN prefill (#50306)

### [22e1cb6](https://github.com/sgl-project/sglang/commit/22e1cb6d98476a936dad7e7e336b0d59f5055cbe)

- **作者**: Kangrui Du
- **时间**: 2026-11-15T11:15:09Z
- **提交信息**: [Refactor] multimodal: [MM refactor 6/9] Serve token-space processors behind --enable-token-space-processor (#46412)

Signed-off-by: rockdu <kangrdu@gmail.com>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>

### [d9ec74e](https://github.com/sgl-project/sglang/commit/d9ec74eb72b856419c6eb44733e00193d28ed840)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T10:29:36Z
- **提交信息**: [CI] [NPU] tests: Read test files from the checkout, not runner caches or the CI workspace path (#50592)

### [8d3185e](https://github.com/sgl-project/sglang/commit/8d3185e36765b3d13882c1704bafdfa6ab4aa2d6)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T10:21:58Z
- **提交信息**: [CI] rerun-test: Read registrations with one parser and share the rerun loop (#50593)

### [d33d81f](https://github.com/sgl-project/sglang/commit/d33d81fa9a5dff562e943d988dc6fcf29dbc6e48)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T10:04:12Z
- **提交信息**: [CI] npu: Launch sgl-router in the NPU multi-node tests and ship it in the NPU image (#50584)

### [c07efd2](https://github.com/sgl-project/sglang/commit/c07efd2153de5154826ba82b4baae6beea2018e0)

- **作者**: Vincent Liu
- **时间**: 2026-11-15T09:55:31Z
- **提交信息**: [Feat] kernels: Add out-of-tree dispatch for causal Conv1D (#38751)

Signed-off-by: Vincent Liu <vvinniev34@gmail.com>

### [76e1d59](https://github.com/sgl-project/sglang/commit/76e1d595c677c780da48f91957cda854f094e5b9)

- **作者**: huyhoang5-onexus
- **时间**: 2026-11-15T09:53:59Z
- **提交信息**: [Fix] sgl-router: Handle inline system messages on /v1/messages the way the engine does (#50435)

### [9a0e6ea](https://github.com/sgl-project/sglang/commit/9a0e6eafef0ffa014b6e94e8710528dd37c57eec)

- **作者**: Shangming Cai
- **时间**: 2026-11-15T09:53:30Z
- **提交信息**: [Perf] pp: Bound the PD poll and grammar PP-sync sends by the pipeline depth, not one round (#50481)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ecee6b4](https://github.com/sgl-project/sglang/commit/ecee6b49ef699812625028da04a6666debb30682)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-15T09:37:40Z
- **提交信息**: [Fix] diffusion: Request PDL in the HunyuanVideo QK RMSNorm site only on SM90+ (#50530)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [0021e79](https://github.com/sgl-project/sglang/commit/0021e795037e264fb0fcf29077126f3aff60400d)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-15T09:37:22Z
- **提交信息**: [Fix] diffusion: Align Wan text-to-video request sizes to the 16-pixel patch grid (#50357)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [fed5515](https://github.com/sgl-project/sglang/commit/fed551584198a9e43ad5da4fe3eab7ad020a41c1)

- **作者**: 黄云龙
- **时间**: 2026-11-15T09:37:06Z
- **提交信息**: [Fix] diffusion: Honor the channel_dim override in LTX-2 PerChannelRMSNorm (#50184)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [818743e](https://github.com/sgl-project/sglang/commit/818743e907bf87b91e51e99d1aed503e37ec8139)

- **作者**: 黄云龙
- **时间**: 2026-11-15T09:36:50Z
- **提交信息**: [Fix] diffusion: Answer 400 for invalid mesh sampling parameters (#50182)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [a187006](https://github.com/sgl-project/sglang/commit/a187006c248259154c9707fa341ec260a9ca6d79)

- **作者**: Yibo Liu
- **时间**: 2026-11-15T09:36:26Z
- **提交信息**: [Fix] [NVIDIA] modelopt: Keep SM12x FP8 batch-invariant in deterministic mode (#44861)

Signed-off-by: Yibo Liu <240359763+yibol9768-alt@users.noreply.github.com>
Signed-off-by: Yibo Liu <yibol9768@gmail.com>
Co-authored-by: Yibo Liu <240359763+yibol9768-alt@users.noreply.github.com>

### [8834769](https://github.com/sgl-project/sglang/commit/883476951c2b252f5f6c2e56c16a9b339e1b150a)

- **作者**: Chen Cheng
- **时间**: 2026-11-15T09:36:10Z
- **提交信息**: [Feat] mem_cache: Add an opt-in state-only, cost-based eviction order for Mamba states (--radix-eviction-policy state_cost) (#50122)

### [6cbee66](https://github.com/sgl-project/sglang/commit/6cbee669c1720b4ac2d6d6516596a80e0f430624)

- **作者**: Lucas Gadani
- **时间**: 2026-11-15T09:35:55Z
- **提交信息**: [Feat] kv-cache: Let platform plugins register KV cache dtypes (#49717)

### [2b9eab7](https://github.com/sgl-project/sglang/commit/2b9eab71258173c4bd3fbdf48a4275b3689296b9)

- **作者**: Marina Ma
- **时间**: 2026-11-15T09:35:34Z
- **提交信息**: [Fix] Kimi-K3: Reject flashinfer_mxfp4 SiTU experts on SM90/SM120 (#46392)

### [5b1e189](https://github.com/sgl-project/sglang/commit/5b1e18953844ed838eef4e352419e1df584f8f70)

- **作者**: Ankith Averineni
- **时间**: 2026-11-15T09:13:59Z
- **提交信息**: [CI] [AMD] disaggregation: Disable UCX ROCm dmabuf registration for the NIXL e2e test (#50550)

### [354738d](https://github.com/sgl-project/sglang/commit/354738ddfa44db58f8c2a19a052df6a959fc57b5)

- **作者**: Mick
- **时间**: 2026-11-15T09:11:59Z
- **提交信息**: [Perf] [NVIDIA] diffusion: Read both TP ranks' partial sums in the epilogue kernel (Z-Image, Qwen-Image-2.1) (#50389)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [cbd4439](https://github.com/sgl-project/sglang/commit/cbd4439f3daef86363ccc9172b39d5c202a9e559)

- **作者**: 黄云龙
- **时间**: 2026-11-15T08:10:06Z
- **提交信息**: [Doc] diffusion: Update the CausalWanSelfAttention Args block after #44753 (#50183)

### [6565c03](https://github.com/sgl-project/sglang/commit/6565c03ff9823003c458762ccc70aee448bdbd5b)

- **作者**: Yuxuan Zhou
- **时间**: 2026-11-15T07:56:02Z
- **提交信息**: [Fix] spec: Support a reduced draft vocabulary in rejection sampling (#40893)

Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>
Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>

### [40723a5](https://github.com/sgl-project/sglang/commit/40723a52ded9229e221a437254f34bc8a3327251)

- **作者**: Yufan Zhuang
- **时间**: 2026-11-15T07:06:04Z
- **提交信息**: [Fix] attention: Triton decode reads wrong KV head for GQA groups > 16 not divisible by 16 (GLM-4-32B breaks) (#47802)

### [26961ab](https://github.com/sgl-project/sglang/commit/26961ab26df9a4e80bad04559bfdbb2a226e434b)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-15T07:05:38Z
- **提交信息**: [Fix] diffusion: Build an offloaded text encoder's RoPE table on the GPU so offload gives the resident output (#50441)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>
Signed-off-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [6f5e302](https://github.com/sgl-project/sglang/commit/6f5e302243c835565a3253ac42cdf495cddc0f3e)

- **作者**: jlqibm
- **时间**: 2026-11-15T07:04:14Z
- **提交信息**: [Fix] granitemoe: Declare packed_modules_mapping so per-projection quant targets match qkv_proj (#45898)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4167502](https://github.com/sgl-project/sglang/commit/4167502ea57fbd8c41858001a46ffda62fa8a6bc)

- **作者**: qiaonan02
- **时间**: 2026-11-15T06:53:20Z
- **提交信息**: [Feat] glm5.3flash: Allow PD prefill CP with native MTP or without speculative decoding (#49089)

### [cb6a391](https://github.com/sgl-project/sglang/commit/cb6a391c961fa71e7b560f9819b1fb3a478b8dde)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T06:42:45Z
- **提交信息**: [CI] rerun-test: Run AMD test files with --hw amd, through a shared AMD setup action (#50580)

### [17e4738](https://github.com/sgl-project/sglang/commit/17e4738c4c94310d506328415831724f08ed9614)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T06:28:14Z
- **提交信息**: [Fix] auth: Key-check wrong methods by route and allowlist `/internal/peer` messages (#50586)

### [2e55a17](https://github.com/sgl-project/sglang/commit/2e55a173a79b89965b5c4cb30b5ec05d6825efc1)

- **作者**: zyxing
- **时间**: 2026-11-15T06:15:53Z
- **提交信息**: [Fix] observability: Snapshot STANDALONE metrics before settlement (#47060)

Co-authored-by: xingzheyuan.xzy <xingzheyuan.xzy@alibaba-inc.com>

### [cfe0fc5](https://github.com/sgl-project/sglang/commit/cfe0fc54ba15181c48dbaa9d4861f3bd99c11a16)

- **作者**: zyxing
- **时间**: 2026-11-15T06:15:24Z
- **提交信息**: [Feat] grpc: Advertise api.v1 owning-runtime instance identity (#50044)

### [b23260c](https://github.com/sgl-project/sglang/commit/b23260c63e4e9d49b7fec933fabdb3eb1a4e93b8)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T06:02:22Z
- **提交信息**: [CI] rerun-test: Run NPU single-node test files, with --hw to pick the backend (#50562)

### [f7f0c93](https://github.com/sgl-project/sglang/commit/f7f0c930c1e2b2cc0f8bf98dd9ce07d140bab384)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T06:01:31Z
- **提交信息**: [Refactor] auth: Declare every HTTP route's auth level in one table that the Python and Rust servers both read (#50559)

### [a56dbcf](https://github.com/sgl-project/sglang/commit/a56dbcf181cfb7f395c340a093ec5a0bca22cae5)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T05:20:37Z
- **提交信息**: [CI] npu: Run the checked-out sglang in the NPU nightly and honor job_filter (#50560)

### [d78af39](https://github.com/sgl-project/sglang/commit/d78af397248291e1de9c705adc5c6ec528163d33)

- **作者**: Mick
- **时间**: 2026-11-15T05:16:10Z
- **提交信息**: [Perf] diffusion: Write varlen SDPA segments in place when the backend can (#50387)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [40c2faa](https://github.com/sgl-project/sglang/commit/40c2faa94d4ca7772da4de72beffd8e7802ece5b)

- **作者**: Mick
- **时间**: 2026-11-15T04:48:46Z
- **提交信息**: [Perf] diffusion/minimax-h3: Fuse the attention gated residual with the norm2 modulation (#50391)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3c8b4d2](https://github.com/sgl-project/sglang/commit/3c8b4d2171e1bcdc2a18421c8561099473dc0a57)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-15T04:25:04Z
- **提交信息**: [Test] test_utils: Add ADMIN_LAUNCH_ARGS_FOR_TEST and admin_post for tests that call admin endpoints (#50558)

### [2af0a25](https://github.com/sgl-project/sglang/commit/2af0a254579ffa8218daf6442e92b3c61df5d466)

- **作者**: Shuwen Wang
- **时间**: 2026-11-15T03:40:27Z
- **提交信息**: [Perf] hicache: Reuse the host eviction heap across one write_back eviction walk (#47126)

Co-authored-by: Rui Ding <132779754+RuiDingY@users.noreply.github.com>

### [07f4c84](https://github.com/sgl-project/sglang/commit/07f4c845c2624f578bce67ab78025ade1a4ae033)

- **作者**: Shubham Garg
- **时间**: 2026-11-15T03:40:07Z
- **提交信息**: [Fix] weights: Reject mismatched manifests before distributed broadcasts (#50234)

### [077acd4](https://github.com/sgl-project/sglang/commit/077acd49a1ca1952832834482055ef8a5b6298c6)

- **作者**: Shri Rajamanikandan Vasudevan
- **时间**: 2026-11-15T03:39:48Z
- **提交信息**: [Perf] attention: Avoid host synchronization in GDN MIS state resets (#50197)

Co-authored-by: Copilot App <223556219+Copilot@users.noreply.github.com>

### [6a2f9b9](https://github.com/sgl-project/sglang/commit/6a2f9b974a9382da5c4e70c0057d638da2919ec9)

- **作者**: Haishuo.Kong
- **时间**: 2026-11-15T03:39:29Z
- **提交信息**: [Fix] attention: Widen GDN chunk-state offsets to int64 before multiplying (#49803)

### [80a4615](https://github.com/sgl-project/sglang/commit/80a461512ebe2b6bc0d11d4bae013a484082112d)

- **作者**: s
- **时间**: 2026-11-15T03:39:10Z
- **提交信息**: [Fix] deepseek-v4.1: Keep active DP decode ranks out of idle tail replay (#49170)

### [5dc801c](https://github.com/sgl-project/sglang/commit/5dc801cee30e675ae477c368af09caa02a898404)

- **作者**: Benjamin Truong
- **时间**: 2026-11-15T03:38:50Z
- **提交信息**: [Perf] [NVIDIA] gemma4: write o_proj/down_proj partials straight into the AR-fusion symmetric buffer (#50002)

### [f4c1623](https://github.com/sgl-project/sglang/commit/f4c16239a557734690ff6652e392f36ac3788798)

- **作者**: Mick
- **时间**: 2026-11-15T01:23:41Z
- **提交信息**: [Perf] diffusion: Run head_dim-64 rounded NeoX QK-norm+RoPE four rows per warp (#50392)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dc69bfd](https://github.com/sgl-project/sglang/commit/dc69bfd905809cca163e545609fdccc7a4bd3f9a)

- **作者**: Mick
- **时间**: 2026-11-15T01:23:06Z
- **提交信息**: [Perf] diffusion: Walk one token's heads per warp in the two-rows QK-norm+RoPE kernel (#50388)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-15T22:07:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 96983
- **最后更新**: 2026-11-16T01:48:52Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 23
- **主要提交者**: devshah-cohere, Advay Monga, Wei Zhao

## AI分析总结

## 一、主要更新类型

本次 26 条提交可归为四类：

- **性能优化（约 8 条）**：占比最高，集中在 DeepSeek-V4.1 系列模型在 AMD MI355X 上的推理加速，以及 MoE/FP8 路径的算子融合。
- **Bug 修复（约 7 条）**：涉及 Mamba 缓存、KV Offload、CUDA 图预热上限、音频解码限制等边界问题。
- **新功能/硬件支持（约 7 条）**：Intel XPU 的 MoE LoRA 与 MXFP8 内核、NVIDIA SM107（NVFP4 专家）、Rust 前端批量生成、多模态编码器缓存可配置化。
- **CI 与测试加固（约 6 条）**：修正测试平台补丁方式、FP8 权重范围、Ray 并行集群资源配置等。

## 二、关键变更点与项目方向的关系

vLLM 的目标是"为所有人提供简单、快速、低成本的 LLM 服务"，本批提交与之高度契合：

1. **DeepSeek-V4.1 成为性能主战场**：约 6 条提交围绕 DSv4.1-Flash，涵盖 Engram 主机查找排序、eager prefill 上下文并行、mHC 融合单发射 HIP 内核、MXFP8 GEMM 与激活量化调优。这表明项目正在把最新国产大模型作为旗舰优化对象。
2. **多硬件生态并进**：AMD（ROCm/SDMA 流水线并行）、Intel（XPU LoRA、MXFP8 扁平化）、NVIDIA（SM107/FlashInfer NVLink all2all）三线并行，直接支撑"cheap serving"的多平台承诺。
3. **MoE + 量化是统一技术主线**：DeepGEMM/Triton block-FP8 MoE 与 FlashInfer NVLink all2all 的打通、compressed-tensors CUTLASS FP8 缓存重启，说明 block-FP8/FP4 低比特 MoE 推理已进入生产可用阶段。

## 三、对项目的影响与潜在意义

- **性能层面**：DSv4.1 在 MI355X 上的多项调优叠加，可显著降低该模型的推理延迟与显存带宽压力，增强 AMD 平台对旗舰模型的竞争力。
- **稳定性层面**：warmup/CUDA 图大小按 `max_num_seqs * max_model_len` 封顶、Mamba 中块恢复不缓存越界块等修复，消除了长时间运行和异常恢复场景下的潜在崩溃，提升生产可靠性。
- **生态层面**：Rust 前端支持 n>1 与 llm-multimodal 版本升级，标志着非 Python 接口逐步走向功能完整。

## 四、值得关注的技术点

- **SDMA copy engine 用于 PP 层间交接**（`--pp-sdma-handoff`）：用专用拷贝引擎与计算重叠，是流水线并行通信优化的新思路。
- **AITER 单发射 HIP Mega-MHC 融合**：将 mHC 接缝算子合并为单次启动，体现算子融合向"整段计算图"演进的趋势。
- **K-cache gather 内核改用 int64 行偏移**：针对超长 KV 缓存的溢出防护，细节但关键。
- **Muse Spark 懒加载模型类**：避免导入包即初始化 CUDA，改善库式集成体验。
- **多个 AI 协作署名（Claude、vllm-agent）**：反映项目已深度采用 AI 辅助开发流程。

## 五、对项目发展的整体影响

这批提交显示 vLLM 正处于"多硬件深度优化 + 新模型快速适配"的双轮驱动阶段：一方面以 DeepSeek-V4.1 等模型为牵引，在 AMD/Intel/NVIDIA 三条硬件线上持续压榨性能，兑现"fast and cheap"的承诺；另一方面通过 CI 加固、Bug 修复和 Rust 前端推进，夯实"easy"的工程基础。整体上，项目正从通用推理引擎向"对特定旗舰模型和多硬件平台都达到生产级优化"的成熟基础设施演进，其生态位将更加巩固。

## 详细提交记录

### [207d6e6](https://github.com/vllm-project/vllm/commit/207d6e6f9a6650056df1bd00ef5b4b5d782045b1)

- **作者**: Fangzhou Ai
- **时间**: 2026-11-15T23:44:04Z
- **提交信息**: [ROCm][Perf][DSv4.1] Sort Engram host lookups by table offset on MI355X (#67805)

Signed-off-by: Fangzhou Ai <fangzhou.ai@amd.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [218459c](https://github.com/vllm-project/vllm/commit/218459c6cdaf7c3441155af08aef5d12454fc417)

- **作者**: Chaojun Zhang
- **时间**: 2026-11-15T23:28:51Z
- **提交信息**: [XPU][LoRA] Support unquantized MoE LoRA (#62807)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [75f3967](https://github.com/vllm-project/vllm/commit/75f3967ac127cb5cf36b2fee7b7377dca5725d51)

- **作者**: Wei Zhao
- **时间**: 2026-11-15T22:59:35Z
- **提交信息**: [Bugfix][Mamba] Don't cache a block that a mid-block prefill resume ran past (#67717)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1093310](https://github.com/vllm-project/vllm/commit/109331007a330093fa726b1c179729fd8088703e)

- **作者**: Mingyuan Ma
- **时间**: 2026-11-15T22:46:05Z
- **提交信息**: [MoE][NVIDIA] Support SM107 in flashinfer_moe_ep_cutedsl for NVFP4 experts for FI 0.7.3 (#65974)

Signed-off-by: Mingyuan Ma <mingyuanm@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e22287d](https://github.com/vllm-project/vllm/commit/e22287df5035af6919663c37171b57f827151b87)

- **作者**: Yibo Liu
- **时间**: 2026-11-15T22:00:59Z
- **提交信息**: [Bugfix] Cap warmup and CUDA graph sizes to max_num_seqs * max_model_len (#67469)

Signed-off-by: Yibo Liu <yibol9768@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [71c3541](https://github.com/vllm-project/vllm/commit/71c3541492cfb12b79ff0c4a31047f4d4b7ffcb8)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-15T21:49:13Z
- **提交信息**: [ROCm][DeepSeek-V4.1] Enable eager prefill context parallel for DeepSeek-V4.1-Flash (#66842)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Divakar Verma <137818590+divakar-amd@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [919d45f](https://github.com/vllm-project/vllm/commit/919d45fc3a54c07034bf637fe649dfa86eed48c2)

- **作者**: siyu
- **时间**: 2026-11-15T17:20:47Z
- **提交信息**: [Fast Start] Support compressed-tensors CUTLASS block FP8 cache restarts (#63976)

Signed-off-by: liusy58 <liusy58@smail.nju.edu.cn>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: liusy58 <liusy58@smail.nju.edu.cn>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [1da9b29](https://github.com/vllm-project/vllm/commit/1da9b29c651174b5839de06979572c50a072b13d)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-15T17:06:18Z
- **提交信息**: [CI][Test] Patch the platform class, not the instance, in the humming quantization tests (#67752)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dadf740](https://github.com/vllm-project/vllm/commit/dadf740edf4e5339afcfc6ae39df6a6a9dbf1548)

- **作者**: Tuukka Sarvi
- **时间**: 2026-11-15T15:27:43Z
- **提交信息**: [Bugfix][DSv4.1] Use int64 row offsets in the K-cache gather kernels (#65926)

Signed-off-by: Tuukka Sarvi <tuukka.sarvi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [9fbe012](https://github.com/vllm-project/vllm/commit/9fbe012bd78bc46471013541e04bb9f0cfc84b80)

- **作者**: David Zhu
- **时间**: 2026-11-15T12:56:28Z
- **提交信息**: [ROCm][DSv4.1][Perf] Run the fused mHC seams as AITER's single-launch HIP Mega-MHC (#65992)

Signed-off-by: David Zhu <david.zhu@amd.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [8657860](https://github.com/vllm-project/vllm/commit/8657860cd37d2ba777851b5fe4e026828ded402f)

- **作者**: aoshen02
- **时间**: 2026-11-15T11:58:19Z
- **提交信息**: [Perf] Allow DeepGEMM/Triton block-FP8 MoE with FlashInfer NVLink all2all (#67592)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [261042b](https://github.com/vllm-project/vllm/commit/261042baa696a1412816508e6189587606bc64a7)

- **作者**: Hangrui Cao
- **时间**: 2026-11-15T11:22:46Z
- **提交信息**: [Core][MM] Make the multimodal encoder cache size configurable  (#65534)

Signed-off-by: HangruiCao2000 <caohangrui2000@gmail.com>

### [1489434](https://github.com/vllm-project/vllm/commit/1489434bd56a33c068b946eca3a24804e28859b8)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-15T10:28:39Z
- **提交信息**: [CI][Test] Keep dummy FP8 weights within +-1 in the HiSparse e2e tests (#67753)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ca8952a](https://github.com/vllm-project/vllm/commit/ca8952a9bf3ee6dcbc4a2eec432f37a451524e1f)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-15T10:06:49Z
- **提交信息**: [KV Offload][Bugfix] Hold P2P e2e test ports until the tiers bind them (#67607)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5039f73](https://github.com/vllm-project/vllm/commit/5039f736e612ae637099eba3fa645031d416ef53)

- **作者**: Tianyu Guo
- **时间**: 2026-11-15T08:36:33Z
- **提交信息**: [CI] Require batch invariance for derender parity tests (#67742)

Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>

### [6a587fe](https://github.com/vllm-project/vllm/commit/6a587fedcd834d94f7f41b37a7dc715f0fde3202)

- **作者**: Nick Hill
- **时间**: 2026-11-15T08:14:49Z
- **提交信息**: [Bugfix][Muse Spark] Load the model classes lazily so importing the package doesn't initialize CUDA (#67691)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4244a09](https://github.com/vllm-project/vllm/commit/4244a09e4d403d688c43dad19b895ec95ee2fa18)

- **作者**: Taoyu Zhu
- **时间**: 2026-11-15T07:55:59Z
- **提交信息**: [ROCm][PP] Stage hand-off on SDMA copy engines (--pp-sdma-handoff) (#65658)

Signed-off-by: Taoyu Zhu <zhutaoyu97@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [730194d](https://github.com/vllm-project/vllm/commit/730194d2362716c47648d06e172c91bcdace3b32)

- **作者**: Itay Alroy
- **时间**: 2026-11-15T07:03:49Z
- **提交信息**: [CI] Fix NIXL EP import test (#67574)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b575d74](https://github.com/vllm-project/vllm/commit/b575d74ff95d490fdd71eca82931f9806a6b2877)

- **作者**: Advay Monga
- **时间**: 2026-11-15T06:49:53Z
- **提交信息**: [Bugfix][KV Offload] Report only written blocks from fs tier store jobs (#63524)

Signed-off-by: Advay Monga <advaymonga@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [85217ff](https://github.com/vllm-project/vllm/commit/85217ffebbab2905386bac2e38566e09912da25a)

- **作者**: devshah-cohere
- **时间**: 2026-11-15T06:29:23Z
- **提交信息**: [Rust Frontend] Support n > 1 on /inference/v1/generate (#66878)

Signed-off-by: Dev Shah <dev.shah@cohere.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9bc16ae](https://github.com/vllm-project/vllm/commit/9bc16ae6a34b1e0fe260e8d12b98568478bf38c3)

- **作者**: Liangliang Ma
- **时间**: 2026-11-15T04:52:52Z
- **提交信息**: [XPU] Flatten N-D input in XPU MXFP8 linear kernel (#66494)

Signed-off-by: Ma, Liangliang <liangliang.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [a58360c](https://github.com/vllm-project/vllm/commit/a58360ca30e84c70a89a676a38b3779a9fe9f110)

- **作者**: Harry Mellor
- **时间**: 2026-11-15T04:20:29Z
- **提交信息**: [CI] Load gte-Qwen2 without remote code in test_non_causal_models (#67716)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4388bec](https://github.com/vllm-project/vllm/commit/4388bec9295a82de7e8ff6fa58c904346a8374aa)

- **作者**: Ylean
- **时间**: 2026-11-15T04:01:23Z
- **提交信息**: [Bugfix][Audio] Treat zero decode limits as disabled (#67611)

Signed-off-by: Ylean <61880605+Woolgathererer@users.noreply.github.com>

### [6c7e480](https://github.com/vllm-project/vllm/commit/6c7e48049332df0c22412fc782a90518d7ff1a2e)

- **作者**: Isotr0py
- **时间**: 2026-11-15T03:40:04Z
- **提交信息**: [Rust Frontend] Bump llm-multimodal version (#67670)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [27a441c](https://github.com/vllm-project/vllm/commit/27a441ca4cc86623cac90b1977c8f0ca786fcfeb)

- **作者**: Wei Zhao
- **时间**: 2026-11-15T01:52:32Z
- **提交信息**: [CI] Start multi_process_parallel's Ray cluster with one CPU per rank (#67391)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [9d8c980](https://github.com/vllm-project/vllm/commit/9d8c9806617e623f10d7aec523a56214f21513ea)

- **作者**: LI MOU
- **时间**: 2026-11-15T01:46:26Z
- **提交信息**: [Perf][ROCm][DSv4.1] DeepSeek-V4.1-Flash: dense MXFP8 GEMMs and wo_a on AITER's tuned FlyDSL kernels, and a faster MXFP8 activation quant (MI355X) (#67377)

Signed-off-by: LI MOU <limou102@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-16
**监控日期**: 2026-11-15
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7773
- **最后更新**: 2026-11-16T00:46:01Z

## 提交统计

- **昨日提交总数**: 18
- **提交者数量**: 11
- **主要提交者**: kunkun, Ziang Tang, lm10-arg

## AI分析总结

# vllm-omni 昨日提交分析（第 1/1 批，共 18 条）

## 1. 主要更新类型
- **Bug 修复**（4 条）：CUDA graph 捕获时多模态输出解包、MOSS-TTS-Realtime 采样、前端流式队列拒绝后流保活、相关回归修复。
- **功能新增/模型支持**（约 8 条）：Praxis-1 系列四连发（YAM 双臂、recipe、DROID/YAM 部署）、Hy-Nomas 多项特性、Mooncake KV 缓存、Rubin 平台 MXFP8 服务、Ascend Ngram 支持。
- **性能优化**（3 条）：LingBot-World 流式性能、PixelUMM 解码器集成、Hy-Nomas 设备端量化。
- **CI/构建与重构**（3 条）：ROCm 周期性覆盖升级为阻塞门禁、Omni merge 分片、H100 超时调整。
- **Diffusion 核心改进**（2 条）：会话与副本亲和放置、Same-Step 会话逐步历史保留。

## 2. 关键变更点与项目方向的关系
README 强调"**Easy, fast, and cheap omni-modality model serving**"，本批提交紧密围绕这一目标：
- **多模态服务能力扩展**：新增 Praxis-1、MiniMax-H3-Image、MiniCPM-o 4.5、Qwen3-Omni、LingBot-World 等模型支持，直接扩充 omni 模型覆盖范围。
- **性能与成本**：Hy-Nomas 的零同步缓存、区域编译、设备端量化，以及 Mooncake KV/HS 缓存，均服务于"fast & cheap"。
- **可靠性**：多条 Bug 修复集中在 CUDA graph 采样与流式服务路径，保障 serving 稳定性。

## 3. 对项目的影响和潜在意义
- **硬件生态多元化**：同一批次覆盖 NVIDIA（Rubin）、AMD（ROCm）、Ascend 三平台，表明项目正加速多硬件落地。
- **CI 门禁收紧**：ROCm parity 覆盖转为阻塞、H100 超时规范、merge 分片，提升主干质量与合并效率。
- **会话/状态管理成熟化**：Diffusion 会话副本亲和与 Same-Step 历史保留，说明多模态长会话 serving 架构在系统化演进。
- **AI 辅助协作痕迹明显**：多个提交与 Claude 系列模型共同署名，反映开发流程的新形态。

## 4. 值得关注的技术点
- **CUDA graph 与多模态输出的解包**（#10414）：这是图捕获路径的典型坑，修复后可提升多模态推理吞吐。
- **Mooncake KV/HS 缓存接入 Qwen3-Omni 轮次服务**（#10107）：KV 缓存与 omni 轮次服务结合，是降低长上下文成本的关键。
- **Diffusion 会话放置与历史保留**（#9821/#9817）：会话亲和性调度对扩散模型的连续生成体验至关重要。
- **Hy-Nomas 系列**（#10246/#10113/#9567）：零同步缓存 + 区域编译 + PixelUMM 解码器，是一条完整的性能优化链路。
- **Praxis-1 四阶段发布**（10204/10198/10202）：分批交付 + checkpoint 门控测试的工程实践值得借鉴。

## 5. 对项目发展的整体影响
基于 README 的"人人可用的 omni 模型服务"愿景，这批提交显示出项目从**功能扩张转向"广度 + 深度 + 稳定性"并重**：一方面持续接入新模型与新硬件，扩大 omni 服务覆盖面；另一方面通过缓存、编译、量化等手段压缩成本与延迟，并以更严格的 CI 保证多平台质量。短期看，用户可获得更丰富的模型选择与更稳定的流式体验；长期看，多硬件与多会话架构的成熟将巩固 vllm-omni 在 omni-modality serving 领域的定位，使其真正兑现"easy, fast, cheap"的承诺。

## 详细提交记录

### [5555ce3](https://github.com/vllm-project/vllm-omni/commit/5555ce3ff7d8e5b457592328626f6c195cdf152a)

- **作者**: lm10-arg
- **时间**: 2026-11-15T23:08:00Z
- **提交信息**: [Bugfix] Unwrap multimodal outputs during CUDA graph capture (#10414)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [3831516](https://github.com/vllm-project/vllm-omni/commit/383151661f9bc030e3655f9f149bdaa7c1ea66d8)

- **作者**: lm10-arg
- **时间**: 2026-11-15T20:58:39Z
- **提交信息**: [CI/Build][ROCm] Add Drama 3 weekly burn-in coverage (#10413)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [ed8d8f0](https://github.com/vllm-project/vllm-omni/commit/ed8d8f00728036cd3ea317e95bb567182ddb9830)

- **作者**: lm10-arg
- **时间**: 2026-11-15T19:09:49Z
- **提交信息**: [Bugfix] Fix MOSS-TTS-Realtime request-local sampling (#10411)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [8ff8b02](https://github.com/vllm-project/vllm-omni/commit/8ff8b02c152a6217c169719d56a4d581782fd1af)

- **作者**: kunkun
- **时间**: 2026-11-15T16:07:34Z
- **提交信息**: [Core][Diffusion] Place sessions on the replica that holds them (#9821)

Signed-off-by: kunkunblueberry <kunkunblueberry@gmail.com>

### [0f55c39](https://github.com/vllm-project/vllm-omni/commit/0f55c39eb07ccc349d57ae436f99f7a612a2dd16)

- **作者**: Ziang Tang
- **时间**: 2026-11-15T12:13:00Z
- **提交信息**: [Core] Add Mooncake KV/HS caching for Qwen3-Omni turn serving (#10107)

Signed-off-by: Ziang Tang <ztang2370@gmail.com>
Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: psv666 <2693925048@qq.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [22721f0](https://github.com/vllm-project/vllm-omni/commit/22721f0acdfe129ba2a8937057dd321efecf8aa1)

- **作者**: Yiwen Cai
- **时间**: 2026-11-15T09:52:35Z
- **提交信息**: [Model] Hy-Nomas: add step-level zero-sync caching and regional compilation (#10246)

Signed-off-by: yiwen-cai <drinklessmilktea@gmail.com>

### [6360dcc](https://github.com/vllm-project/vllm-omni/commit/6360dcce6295025c498911bf8d123de9aec234e6)

- **作者**: kunkun
- **时间**: 2026-11-15T09:30:29Z
- **提交信息**: [Core][Diffusion] Retain per-step history for Same-Step sessions (#9817)

Signed-off-by: kunkunblueberry <kunkunblueberry@gmail.com>

### [b45b95e](https://github.com/vllm-project/vllm-omni/commit/b45b95e3a16fd34f3ad94be3ad0743ff6b8c1057)

- **作者**: Lucas Kabela
- **时间**: 2026-11-15T09:09:26Z
- **提交信息**: [4/4][Model] Ship the Praxis-1 DROID and YAM deployments with checkpoint-gated tests (#10202)

Signed-off-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [3d8a045](https://github.com/vllm-project/vllm-omni/commit/3d8a045a29ee32c4a981fc8851593af38d93d6ad)

- **作者**: kunkun
- **时间**: 2026-11-15T09:03:46Z
- **提交信息**: [Model] Hy-Nomas: quantize chunk frames on device and stage delivery (#10113)

Signed-off-by: kunkunblueberry <kunkunblueberry@gmail.com>

### [b576ed0](https://github.com/vllm-project/vllm-omni/commit/b576ed001032a78d565960d4b99740251a9daa8b)

- **作者**: SYLAR
- **时间**: 2026-11-15T06:19:57Z
- **提交信息**: [Hardware][NVIDIA] Enable MiniMax-H3-Image MXFP8 serving on Rubin (#10390)

Signed-off-by: lishunyang12 <lishunyang12@163.com>

### [d29ce30](https://github.com/vllm-project/vllm-omni/commit/d29ce307aef5a041df0627b6dc83719b8c164436)

- **作者**: Lucas Kabela
- **时间**: 2026-11-15T05:58:18Z
- **提交信息**: [3/4][Doc] Add the Praxis-1 recipe and worker tests (#10198)

Signed-off-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [484602f](https://github.com/vllm-project/vllm-omni/commit/484602f8ec3d2b04b410b359c971418d80b05e4c)

- **作者**: hurukawa
- **时间**: 2026-11-15T05:50:56Z
- **提交信息**: [Model] Improve LingBot-World streaming performance (#10383)

Signed-off-by: nagisa-kun <1434936049@qq.com>

### [20c94bf](https://github.com/vllm-project/vllm-omni/commit/20c94bf2118c00d52c2c16ca378416a2af4fc341)

- **作者**: Yuanbing Zhu
- **时间**: 2026-11-15T05:00:18Z
- **提交信息**: [Bugfix][Frontend] Keep the stream alive when a queued interaction is rejected (#8560)

Signed-off-by: zyuanbing <zhuyuanbing1021@icloud.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f375368](https://github.com/vllm-project/vllm-omni/commit/f3753687819a1c3b4b91e60b076a08e130e931fb)

- **作者**: BruceLoveDecimal
- **时间**: 2026-11-15T04:27:44Z
- **提交信息**: [Perf][Hy-NoMas]integrate native PixelUMM decoder (#9567)

Signed-off-by: BruceLoveDecimal <liuqihao970610@gmail.com>
Signed-off-by: BruceLoveDecimal <39156883+BruceLoveDecimal@users.noreply.github.com>

### [8a70379](https://github.com/vllm-project/vllm-omni/commit/8a70379959b2d0b09918759596620d0668bd0a74)

- **作者**: y-null
- **时间**: 2026-11-15T04:10:21Z
- **提交信息**: [Hardware][Ascend] Enable MiniCPM-o 4.5 Thinker Ngram on MRv2 (#10313)

Signed-off-by: y-null <213026468+y-null@users.noreply.github.com>
Co-authored-by: y-null <213026468+y-null@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [3f428a8](https://github.com/vllm-project/vllm-omni/commit/3f428a89a06f5235dc7f8e497b2e40c5e1fd9618)

- **作者**: lm10-arg
- **时间**: 2026-11-15T03:50:54Z
- **提交信息**: [CI/Build][ROCm] Promote weekly parity coverage to blocking (#10392)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [10efc8f](https://github.com/vllm-project/vllm-omni/commit/10efc8f35c7466d193fc62213f8d63b73523ba44)

- **作者**: Lucas Kabela
- **时间**: 2026-11-15T03:18:54Z
- **提交信息**: [2/4][Model] Add YAM two-arm support to Praxis-1 (#10204)

Signed-off-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e937f1c](https://github.com/vllm-project/vllm-omni/commit/e937f1c9e3032d34ce08b3e8b54c6028b8e85274)

- **作者**: wangyu
- **时间**: 2026-11-15T00:56:29Z
- **提交信息**: [CI/Build] Enable Omni merge sharding and set H100 job timeouts to 25 minutes (#10372)

---
