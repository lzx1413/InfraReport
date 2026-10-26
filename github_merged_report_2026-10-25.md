# GitHub Stars 合并报告 - 2026-10-25

**合并日期**: 2026-10-26
**监控日期**: 2026-10-25
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


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2264
- **最后更新**: 2026-10-24T00:29:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2956
- **最后更新**: 2026-10-25T16:41:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2312
- **最后更新**: 2026-10-25T13:39:14Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6779
- **最后更新**: 2026-10-26T00:04:24Z

## 提交统计

- **昨日提交总数**: 83
- **提交者数量**: 3
- **主要提交者**: Akaash Parthasarathy, Yang Xu, eigen

## AI分析总结

# FlashInfer 昨日 83 项提交合并总结

## 主要更新

昨日提交以**性能优化为绝对主体**（约八成），辅以功能新增、Bug 修复与大规模代码去冗。优化聚焦"Cake"生成式后端，覆盖 Blackwell（SM100/SM103）、Rubin（SM107）与 Hopper（SM90）多架构程序调训，并向下延伸至 Ampere SM80；功能新增包括 BF16×NVFP4 W4A16 split fused-MoE、GLM-5.3-Flash mHC 推理内核、SM120 QSA NVFP4 稀疏解码等；修复涉及 deepgemm 配置错误导致的数据损坏、32 位索引溢出、wheel 打包缺失等问题。

## 关键变更

- **MoE 路径**：Kimi-K3 fused router 提速 1.1–1.7x；MegaMoE EP16 改为推送式 dispatch，EP8 引入双缓冲与 epoch 保护；MoK 调度按 owner-rank 分桶、warp_decode 重调最高 1.29x；新增 NVFP4 稀疏 decode 与 W4A16 fused-MoE，MoE all-reduce 提速最高 2.6x。
- **GEMM 路径**：tcgen05 tinygemm 新程序最高提速 3.82x；NVFP4 per-token 量化 GEMM 在 B200 达 1.255x；grouped FP8、SwiGLU+MXFP8、all-gather matmul 持续提速。
- **注意力与 MLA**：NVFP4 sparse MLA decode 换用 35 个 tcgen05 程序提速约 15%；MiniMax-H3 SM120 FP8 变长注意力提速至 1.40x；Rubin MLA 双缓冲；持久化 softmax 去 CTA 屏障；Blackwell softmax 引入 shared-tile 程序使每 SM 驻留 CTA 翻倍。
- **通信优化**：DCP all-to-all 提速至 1.33x；SM120 PCIe 多机新增流水线 Copy-Engine 环形 all-reduce；Megamoe 以单条 NVLink fence 替代 16 次原子操作。
- **训练延伸**：Cake KDA 变体覆盖 chunked training 前后向，SM103 backward 提速 1.05–1.11x，标志项目向训练/微调生态拓展。
- **代码健康**：deslop 提交净删数十万行冗余内核与死代码（fp4 allreduce 8.4 万行、SM110 8.8 万行），统一跨架构分发，部分重构经 SASS/AST 形式化恒等证明。

## 项目影响

- **性能与可靠性并重**：多数提交附严格基准（ABBA 交错、冷 L2、CUPTI、多种子双 GPU），普遍声明位级一致输出，公开 API 零变更；deepgemm 修复以约 6% 性能代价消除数据损坏风险。
- **硬件前瞻**：对 B200/GB300/R200/Jetson Thor 密集铺开，配合 CUDA 13.4 门槛提示，为 Rubin 架构提前就绪。
- **精度生态成势**：NVFP4 在 attention、GEMM、MoE 上形成合力，量化覆盖 BF16→FP8→FP4/MXFP4 全链条；相对 vLLM 原生实现普遍 1.1–1.9x 提速，直接惠及 SGLang 等下游框架。
- **成熟度提升**：以微小性能代价换取内存序正确性，去冗降低 JIT 模块膨胀风险，项目从"跑得快"转向"稳定可靠"，精细基准与多架构覆盖正构成工程壁垒。

## 技术关注点

- **逐形状自动选程序**：按 SM 架构、对齐与形状窗口在 host 端纯规则路由内核变体，大量提交仅调调度不动 device 代码。
- **延迟隐藏手法**：PDL 分层路由、fence-free 内核衔接、TMA 节奏化、双缓冲与 persistent 调度。
- **同步竞态修复**：奇数级环三屏障 parity 提前通过导致 warp 交接死锁，是 CUDA 同步原语的典型反面教材。
- **融合内核权衡**：mHC 将混合、Sinkhorn、RMSNorm 融入单一持久化 launch；KDA 保存 `qg`/`w`/`u` 换取 backward 预处理开销降低；fused norm combine 有舍入顺序变化，下游需评估数值差异。

## 整体展望

FlashInfer 正处于"性能深耕 + 代码治理 + 新硬件扩展 + 训练延伸"多线并进阶段，在 GEMM、MoE、Attention 三大关键路径上同步推进多架构多精度优化，以形式化验证清理技术债，巩固其作为大模型推理与训练基础设施的高性能 GPU 内核基座地位。

## 详细提交记录

### [e177fd1](https://github.com/flashinfer-ai/flashinfer/commit/e177fd16c98fddfc3a551e8b6097a821b1f09e6c)

- **作者**: eigen
- **时间**: 2026-10-25T23:59:01Z
- **提交信息**: perf(cake_tinygemm2_tcgen05): unroll narrow tile and retune its windows (#7370)

This PR speeds up the narrow tile of `cake_tinygemm2_tcgen05`. That is
the Cake backend that #7302 added for `flashinfer.gemm.tinygemm_bf16`
(BF16 `out = input @ weight.T (+ bias)` for small batches), and it
contains generated tcgen05 programs. The backend supports BF16 only,
with and without bias and with and without PDL. It has three tiles:
narrow, packed and per-chain-accumulator. In this PR, the narrow tile
unrolls its MMA and loader loops in blocks of rounds, and it comes in
three builds. Each architecture sends its narrow windows to its fastest
build. On sm_100a, that is the build unrolled by two rounds. On sm_103a,
it is the build unrolled by four MMA rounds that issues full stages
without a per-step K test. On sm_107a, it is the build unrolled by four
MMA rounds. The narrow windows were re-measured on each architecture, so
more shapes now use the narrow tile. Each architecture now has 20
programs instead of 12. The packed and accumulator tiles keep their
code, and the four packed programs are renamed. Shapes outside the
windows keep their current kernel. The baseline is what `tinygemm_bf16`
runs on FlashInfer main today: the round-1 Cake programs and windows
from #7302.

The tables show CUPTI kernel times in µs (median, cold L2) with PDL off.
Each GPU covers 16 shapes, with and without bias. A † marks rows where
the route and program are the same on both sides, so both columns time
the same kernel.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.88 / 2.88 | 1.00x † | 3.04 / 3.06 | 0.99x † |
| 1 x 128 x 14336 | 7.58 / 6.85 | 1.11x | 7.42 / 6.88 | 1.08x |
| 2 x 16 x 256 | 2.85 / 2.85 | 1.00x † | 2.93 / 2.91 | 1.00x † |
| 4 x 2880 x 2880 | 6.82 / 6.78 | 1.00x † | 7.30 / 7.30 | 1.00x † |
| 7 x 128 x 4096 | 4.29 / 4.13 | 1.04x | 4.37 / 4.16 | 1.05x |
| 8 x 128 x 7168 | 5.31 / 5.29 | 1.00x † | 5.22 / 4.99 | 1.04x |
| 8 x 1024 x 1024 | 3.14 / 3.14 | 1.00x † | 3.23 / 3.23 | 1.00x † |
| 13 x 1024 x 2048 | 3.97 / 3.97 | 1.00x † | 4.03 / 4.03 | 1.00x † |
| 16 x 2880 x 2880 | 7.36 / 7.36 | 1.00x † | 7.39 / 7.39 | 1.00x † |
| 64 x 4096 x 3072 | 10.02 / 10.02 | 1.00x † | 9.98 / 9.98 | 1.00x † |
| 16 x 1024 x 1024 | 3.10 / 3.10 | 1.00x † | 3.20 / 3.20 | 1.00x † |
| 8 x 2048 x 2048 | 4.77 / 4.77 | 1.00x † | 4.86 / 4.86 | 1.00x † |
| 8 x 4096 x 4096 | 9.66 / 9.66 | 1.00x † | 10.14 / 10.14 | 1.00x † |
| 16 x 4096 x 3072 | 8.43 / 8.43 | 1.00x † | 8.45 / 8.45 | 1.00x † |
| 64 x 4096 x 4096 | 12.38 / 12.38 | 1.00x † | 12.35 / 12.35 | 1.00x † |
| 4 x 128 x 256 | 2.81 / 2.78 | 1.01x † | 2.94 / 2.96 | 0.99x † |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.59 / 2.59 | 1.00x † | 2.72 / 2.72 | 1.00x † |
| 1 x 128 x 14336 | 7.26 / 6.56 | 1.11x | 7.20 / 6.56 | 1.10x |
| 2 x 16 x 256 | 2.43 / 2.38 | 1.02x † | 2.61 / 2.59 | 1.01x † |
| 4 x 2880 x 2880 | 6.56 / 6.56 | 1.00x † | 7.17 / 7.17 | 1.00x † |
| 7 x 128 x 4096 | 4.10 / 3.90 | 1.05x | 3.97 / 3.97 | 1.00x † |
| 8 x 128 x 7168 | 5.12 / 4.74 | 1.08x | 5.06 / 4.74 | 1.07x |
| 8 x 1024 x 1024 | 2.94 / 2.94 | 1.00x † | 3.04 / 3.04 | 1.00x † |
| 13 x 1024 x 2048 | 3.87 / 3.87 | 1.00x † | 3.95 / 3.97 | 1.00x † |
| 16 x 2880 x 2880 | 7.07 / 7.07 | 1.00x † | 7.07 / 7.07 | 1.00x † |
| 64 x 4096 x 3072 | 9.57 / 9.57 | 1.00x † | 9.54 / 9.54 | 1.00x † |
| 16 x 1024 x 1024 | 3.01 / 3.01 | 1.00x † | 3.07 / 3.07 | 1.00x † |
| 8 x 2048 x 2048 | 4.67 / 4.67 | 1.00x † | 4.74 / 4.74 | 1.00x † |
| 8 x 4096 x 4096 | 9.12 / 9.12 | 1.00x † | 9.79 / 9.79 | 1.00x † |
| 16 x 4096 x 3072 | 8.16 / 8.16 | 1.00x † | 8.19 / 8.19 | 1.00x † |
| 64 x 4096 x 4096 | 11.17 / 11.17 | 1.00x † | 11.10 / 11.10 | 1.00x † |
| 4 x 128 x 256 | 2.69 / 2.69 | 1.00x † | 2.86 / 2.88 | 0.99x † |

**NVIDIA R200 (sm_107a, 212 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.56 / 2.56 | 1.00x † | 2.66 / 2.66 | 1.00x † |
| 1 x 128 x 14336 | 6.27 / 5.66 | 1.11x | 6.11 / 5.66 | 1.08x |
| 2 x 16 x 256 | 2.21 / 2.21 | 1.00x † | 2.37 / 2.37 | 1.00x † |
| 4 x 2880 x 2880 | 5.70 / 5.66 | 1.01x † | 5.34 / 5.36 | 1.00x † |
| 7 x 128 x 4096 | 3.74 / 3.62 | 1.03x | 3.68 / 3.68 | 1.00x † |
| 8 x 128 x 7168 | 4.38 / 4.22 | 1.04x | 4.48 / 4.22 | 1.06x |
| 8 x 1024 x 1024 | 2.75 / 2.75 | 1.00x † | 2.88 / 2.88 | 1.00x † |
| 13 x 1024 x 2048 | 3.20 / 3.20 | 1.00x † | 3.33 / 3.31 | 1.00x † |
| 16 x 2880 x 2880 | 5.02 / 5.02 | 1.00x † | 5.47 / 5.47 | 1.00x † |
| 64 x 4096 x 3072 | 7.74 / 7.74 | 1.00x † | 7.52 / 7.52 | 1.00x † |
| 16 x 1024 x 1024 | 2.72 / 2.72 | 1.00x † | 2.82 / 2.82 | 1.00x † |
| 8 x 2048 x 2048 | 3.58 / 3.57 | 1.00x † | 3.71 / 3.71 | 1.00x † |
| 8 x 4096 x 4096 | 5.89 / 5.89 | 1.00x † | 7.57 / 6.94 | 1.09x |
| 16 x 4096 x 3072 | 8.32 / 5.82 | 1.43x | 5.86 / 5.86 | 1.00x † |
| 64 x 4096 x 4096 | 8.80 / 8.80 | 1.00x † | 8.61 / 8.61 | 1.00x † |
| 4 x 128 x 256 | 2.40 / 2.40 | 1.00x † | 2.59 / 2.56 | 1.01x † |

Cake has no other data type, layout or fused form of this kernel,
`tinygemm2_sm100` is still the with-bias path outside the windows, and
the family covers sm_100a, sm_103a and sm_107a (B200, GB300 and R200
class GPUs).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added additional BF16 matrix multiplication options for supported GPU
architectures, including packed and full-stage tile variants.
* Expanded architecture-specific routing to select from a broader range
of tile configurations.

* **Performance**
* Updated matrix multiplication execution paths to process work in
larger rounds, with the potential to improve throughput.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [fd4ccea](https://github.com/flashinfer-ai/flashinfer/commit/fd4cceab18ab8198bddd95f3839b4728ad2d8a4e)

- **作者**: eigen
- **时间**: 2026-10-25T23:48:30Z
- **提交信息**: fix(cake_minimax_h3): SM120 FP8 varlen attention: proxy fence before each K / V stage release (#7369)

The MiniMax-H3 noncausal packed-varlen attention kernel works on THD
tensors ([tokens, 56 heads, 128 head dim]), with BF16 input and output
and int32 `cu_seqlens`. It has six Cake variants in FlashInfer. This PR
adds a new version of the sm_120a FP8 variant,
`minimax_h3_sm120_varlen_attention_fp8` (E4M3 QK and PV), with the same
API. Only the attention kernel changes: each lane now issues a proxy
fence (`fence.proxy.async.shared::cta`) before its warp releases a K / V
ring stage for the TMA refill. The output is bitwise unchanged. The
baseline is the previous Cake version of the same op (FlashInfer main at
84f3bb3, delivered by #7334). The speedup is 0.994x-0.998x on the 11
large RTX 5090 shapes and 1.010x on seg_empty, and 0.992x-0.997x on all
12 RTX PRO 6000 shapes. This is a small slowdown in exchange for a
memory-ordering fix. Timings are median end-to-end operator latency with
cold L2 on CUDA 13.4, from paired, interleaved runs on the same GPU with
the same inputs.

### NVIDIA GeForce RTX 5090 (sm_120a, 170 SMs)

| shape | cu_seqlens | previous (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| center_4s | `[0, 33472]` | 48,688 | 48,989 | 0.994x |
| center_5s | `[0, 38592]` | 64,920 | 65,301 | 0.994x |
| center_6s | `[0, 48768]` | 105,445 | 105,948 | 0.995x |
| center_8s | `[0, 58944]` | 156,877 | 157,544 | 0.996x |
| center_10s | `[0, 74240]` | 247,823 | 249,012 | 0.995x |
| center_15s | `[0, 109952]` | 541,209 | 543,366 | 0.996x |
| tail_5s_a | `[0, 38531]` | 67,262 | 67,570 | 0.995x |
| tail_5s_b | `[0, 38629]` | 67,686 | 67,982 | 0.996x |
| pad_15s | `[0, 109901, 109952]` | 541,614 | 543,908 | 0.996x |
| seg4 | `[0, 8368, 16736, 25104, 33472]` | 14,447 | 14,473 | 0.998x |
| seg3_ragged | `[0, 257, 4567, 4824]` | 1,161 | 1,165 | 0.997x |
| seg_empty | `[0, 0, 129, 129, 500]` | 44.4 | 44.0 | 1.010x |

### NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120a, 188 SMs)

| shape | cu_seqlens | previous (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| center_4s | `[0, 33472]` | 46,680 | 46,965 | 0.994x |
| center_5s | `[0, 38592]` | 62,371 | 62,782 | 0.993x |
| center_6s | `[0, 48768]` | 99,394 | 99,960 | 0.994x |
| center_8s | `[0, 58944]` | 144,343 | 145,439 | 0.992x |
| center_10s | `[0, 74240]` | 227,838 | 229,153 | 0.994x |
| center_15s | `[0, 109952]` | 496,254 | 499,342 | 0.994x |
| tail_5s_a | `[0, 38531]` | 62,728 | 63,063 | 0.995x |
| tail_5s_b | `[0, 38629]` | 62,766 | 63,148 | 0.994x |
| pad_15s | `[0, 109901, 109952]` | 496,173 | 499,091 | 0.994x |
| seg4 | `[0, 8368, 16736, 25104, 33472]` | 13,646 | 13,717 | 0.995x |
| seg3_ragged | `[0, 257, 4567, 4824]` | 1,140 | 1,145 | 0.996x |
| seg_empty | `[0, 0, 129, 129, 500]` | 57.5 | 57.7 | 0.997x |

The other five Cake variants are the sm_120a NVFP4-QK forms
`minimax_h3_sm120_varlen_attention_nvfp4` (default) and
`minimax_h3_sm120_varlen_attention_nvfp4_nodelta`, plus the sm_100a /
sm_103a forms `minimax_h3_varlen_attention` (BF16),
`minimax_h3_varlen_fp8_attention` (FP8, with the BF16-input form
`minimax_h3_varlen_fp8_attention_bf16`) and
`minimax_h3_varlen_nvfp4_attention` (NVFP4-QK), so the family covers
sm_100a, sm_103a and sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during variable-length attention processing,
helping ensure K and V matrix operations complete in the correct order.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d07ec95](https://github.com/flashinfer-ai/flashinfer/commit/d07ec956ad41575a9cf7afc6283a36f96075fc88)

- **作者**: eigen
- **时间**: 2026-10-25T23:43:10Z
- **提交信息**: perf(cake_grouped_fp8_gemm): store16 programs for short expert runs on SM100 / SM103 (#7367)

`cake_grouped_fp8_gemm` is Cake's grouped FP8 GEMM over a padded
contiguous layout. It ships in two block-scale formats: FP32
per-128-block scales and packed power-of-two UE8M0 block scales. Cake
also ships two related forms of the kernel: a fused SiLU-and-quantize
form and a masked batch form. This PR changes the UE8M0 variant in two
ways. First, it adds 7 programs with a 16-byte (store16) output
epilogue. They cover four routes: the non-swapped N-tile 128 and 256
routes (n128, n256) and the swap-AB routes swap and swap_carry. The host
uses them when the group alignment is a multiple of 128 and the
estimated rows per group, d_est = (M - G (alignment - 1)) / G with G the
number of groups, is at most 128. Other shapes keep the shipped
programs. Second, it adds a long-K swap-AB route on sm_100a. At 100 or
more routed rows per group, the host also takes the swap-AB route when K
>= 2048 and the non-swapped BLOCK_N 128 grid has at most 74 tiles. Of
the shapes below, this rule changes only one: M 1664, N 256, K 4096, 5
groups, align 128, on B200, which moves from n128 to swap. The speedup
below compares this PR against the previous Cake version of the kernel,
which is the set of Cake programs that FlashInfer main ships and routes
after #7342.

NVIDIA B200 (sm_100a) and NVIDIA GB300 (sm_103a), CUDA 13.4 toolkit.
Some GB300 GPUs run 2-CTA cluster kernels more slowly, so the table
shows both kinds as "GB300 fast" and "GB300 slow". Latency is in
microseconds and is the median of 3 draws (5 draws for five of the B200
rows). "shipped" is FlashInfer main's routing (the previous Cake
programs), and "new" is this PR's routing. The new/shipped ratio is the
median of the per-draw new/shipped ratios, so it does not have to equal
the quotient of the two median latencies. A ratio below 1 means the new
routing is faster. The few ratios above 1.000 (at most 1.019) are within
the run-to-run noise of their rows. The program column gives the program
that the new routing picks on B200 / GB300, named by its FlashInfer
route without the `bs_ue8m0_` prefix. swap, swap_run32 and swap_carry
are swap-AB routes, and n128, n128_run32 and n256 are the non-swapped
N-tile 128 / 256 programs. A `_s16` suffix marks this PR's store16
program of a route; the shipped program has the same name without
`_s16`. Each of the 38 rows with a store16 program uses it on every GPU.
On the other rows both sides run the same program, so the table shows
the shipped program's time on both sides with "1.000 (same program)".
The exception is the shape M 1664, N 256, K 4096, 5 groups, align 128 on
B200, where the long-K rule replaces the shipped n128 program with swap.
GB300 already ran swap for this shape. That B200 measurement was taken
in a separate run on another B200. The shape M 1152, N 384, K 128, 6
groups, align 96 was also measured in separate runs, on another GPU of
each kind; both sides run the same program there. M is the row count of
the padded contiguous layout, groups are experts and align is the
per-group row alignment. tokens x top-k counts routed assignments under
uniform or skewed routing; explicit rows give the number of valid rows
instead.

| M | N | K | groups | align | tokens x top-k, routing | program B200 /
GB300 | B200 shipped us | B200 new us | B200 new/shipped | GB300 fast
shipped us | GB300 fast new us | GB300 fast new/shipped | GB300 slow
shipped us | GB300 slow new us | GB300 slow new/shipped |

|---:|---:|---:|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 32640 | 1024 | 2048 | 256 | 128 | 1 x 8, uniform | n256_s16 / n256_s16
| 11.95 | 11.74 | 0.992 | 11.79 | 11.78 | 0.997 | 11.84 | 11.81 | 1.000
|
| 32640 | 1024 | 2048 | 256 | 128 | 8 x 8, uniform | n256_s16 / n256_s16
| 25.86 | 25.55 | 0.986 | 25.60 | 25.33 | 0.994 | 25.49 | 25.12 | 0.993
|
| 32768 | 1024 | 2048 | 256 | 128 | 32 x 8, uniform | swap_s16 /
swap_s16 | 59.09 | 58.58 | 0.996 | 57.12 | 56.50 | 0.992 | 56.91 | 56.53
| 0.995 |
| 34560 | 1024 | 2048 | 256 | 128 | 256 x 8, uniform | swap_s16 /
swap_s16 | 88.43 | 87.01 | 0.983 | 85.55 | 84.56 | 0.988 | 85.65 | 84.51
| 0.986 |
| 36608 | 1024 | 2048 | 256 | 128 | 512 x 8, uniform | swap_s16 /
swap_s16 | 88.72 | 87.84 | 0.991 | 85.54 | 85.14 | 0.994 | 85.60 | 85.09
| 0.995 |
| 48896 | 1024 | 2048 | 256 | 128 | 2048 x 8, uniform | swap_s16 /
swap_s16 | 98.14 | 98.11 | 1.002 | 93.95 | 93.63 | 0.998 | 93.89 | 93.87
| 0.998 |
| 65280 | 1024 | 2048 | 256 | 128 | 4096 x 8, uniform | swap_carry_s16 /
n256_s16 | 111.95 | 111.66 | 0.996 | 106.29 | 105.94 | 0.996 | 106.10 |
105.55 | 0.996 |
| 98048 | 1024 | 2048 | 256 | 128 | 8192 x 8, uniform | swap_carry /
n256 | 151.93 | 151.93 | 1.000 (same program) | 148.35 | 148.35 | 1.000
(same program) | 147.87 | 147.87 | 1.000 (same program) |
| 163584 | 1024 | 2048 | 256 | 128 | 16384 x 8, uniform | swap_carry /
swap_carry | 272.41 | 272.41 | 1.000 (same program) | 230.54 | 230.54 |
1.000 (same program) | 231.65 | 231.65 | 1.000 (same program) |
| 8064 | 1024 | 2048 | 256 | 32 | 8 x 8, uniform | swap_run32 /
swap_run32 | 23.14 | 23.14 | 1.000 (same program) | 22.66 | 22.66 |
1.000 (same program) | 22.62 | 22.62 | 1.000 (same program) |
| 33024 | 1024 | 2048 | 256 | 128 | 64 x 8, uniform | swap_s16 /
swap_s16 | 76.74 | 75.23 | 0.983 | 74.32 | 73.36 | 0.989 | 74.24 | 73.39
| 0.987 |
| 32640 | 2048 | 512 | 256 | 128 | 1 x 8, uniform | n256_s16 / n256_s16
| 11.49 | 11.39 | 0.999 | 11.97 | 11.90 | 0.996 | 11.86 | 11.81 | 0.997
|
| 32640 | 2048 | 512 | 256 | 128 | 8 x 8, uniform | n256_s16 / n256_s16
| 17.78 | 17.70 | 1.001 | 17.84 | 17.81 | 0.995 | 17.86 | 17.78 | 0.992
|
| 32768 | 2048 | 512 | 256 | 128 | 32 x 8, uniform | n256_s16 / n256_s16
| 35.42 | 34.48 | 0.966 | 34.21 | 33.31 | 0.975 | 34.22 | 33.25 | 0.974
|
| 34560 | 2048 | 512 | 256 | 128 | 256 x 8, uniform | swap_s16 /
swap_s16 | 47.33 | 45.25 | 0.959 | 45.82 | 44.22 | 0.962 | 45.82 | 44.27
| 0.963 |
| 36608 | 2048 | 512 | 256 | 128 | 512 x 8, uniform | swap_s16 /
swap_s16 | 47.66 | 46.11 | 0.969 | 46.03 | 45.04 | 0.978 | 46.22 | 45.14
| 0.979 |
| 48896 | 2048 | 512 | 256 | 128 | 2048 x 8, uniform | n256_s16 /
n256_s16 | 56.78 | 55.86 | 0.970 | 56.69 | 55.70 | 0.985 | 56.16 | 55.12
| 0.990 |
| 65280 | 2048 | 512 | 256 | 128 | 4096 x 8, uniform | n256_s16 /
n256_s16 | 70.74 | 69.82 | 0.986 | 67.87 | 67.12 | 0.985 | 67.86 | 67.26
| 0.989 |
| 98048 | 2048 | 512 | 256 | 128 | 8192 x 8, uniform | n256 / n256 |
110.34 | 110.34 | 1.000 (same program) | 101.34 | 101.34 | 1.000 (same
program) | 100.32 | 100.32 | 1.000 (same program) |
| 163584 | 2048 | 512 | 256 | 128 | 16384 x 8, uniform | n256 / n256 |
196.49 | 196.49 | 1.000 (same program) | 176.56 | 176.56 | 1.000 (same
program) | 174.26 | 174.26 | 1.000 (same program) |
| 8064 | 2048 | 512 | 256 | 32 | 8 x 8, uniform | swap_run32 /
swap_run32 | 15.57 | 15.57 | 1.000 (same program) | 14.98 | 14.98 |
1.000 (same program) | 14.94 | 14.94 | 1.000 (same program) |
| 33024 | 2048 | 512 | 256 | 128 | 64 x 8, uniform | swap_s16 / swap_s16
| 41.71 | 40.34 | 0.967 | 40.59 | 39.28 | 0.963 | 40.70 | 39.41 | 0.966
|
| 65152 | 512 | 4096 | 512 | 128 | 1 x 10, uniform | n256_s16 / n256_s16
| 17.49 | 17.38 | 0.996 | 17.09 | 16.98 | 0.990 | 16.91 | 16.75 | 0.992
|
| 65152 | 512 | 4096 | 512 | 128 | 8 x 10, uniform | n256_s16 / n256_s16
| 32.34 | 32.05 | 0.994 | 31.65 | 31.52 | 0.988 | 31.62 | 31.46 | 0.988
|
| 65408 | 512 | 4096 | 512 | 128 | 32 x 10, uniform | swap_s16 /
swap_s16 | 84.86 | 85.34 | 1.004 | 84.74 | 84.00 | 0.992 | 84.85 | 84.03
| 0.992 |
| 67584 | 512 | 4096 | 512 | 128 | 256 x 10, uniform | swap_s16 /
swap_s16 | 171.12 | 169.07 | 0.989 | 169.41 | 167.49 | 0.992 | 169.46 |
167.63 | 0.989 |
| 70144 | 512 | 4096 | 512 | 128 | 512 x 10, uniform | swap_s16 /
swap_s16 | 171.79 | 169.45 | 0.991 | 169.65 | 167.95 | 0.989 | 169.92 |
168.14 | 0.991 |
| 85504 | 512 | 4096 | 512 | 128 | 2048 x 10, uniform | swap_s16 /
swap_s16 | 185.95 | 184.64 | 0.993 | 180.90 | 180.38 | 0.995 | 181.01 |
180.32 | 0.995 |
| 105984 | 512 | 4096 | 512 | 128 | 4096 x 10, uniform | swap_s16 /
swap_s16 | 205.05 | 205.20 | 1.000 | 198.30 | 197.97 | 0.997 | 197.52 |
197.62 | 0.996 |
| 146944 | 512 | 4096 | 512 | 128 | 8192 x 10, uniform | n256 / swap |
262.37 | 262.37 | 1.000 (same program) | 242.48 | 242.48 | 1.000 (same
program) | 246.40 | 246.40 | 1.000 (same program) |
| 228864 | 512 | 4096 | 512 | 128 | 16384 x 10, uniform | n256 / swap |
391.88 | 391.88 | 1.000 (same program) | 352.32 | 352.32 | 1.000 (same
program) | 354.46 | 354.46 | 1.000 (same program) |
| 16000 | 512 | 4096 | 512 | 32 | 2 x 10, uniform | swap_run32 /
swap_run32 | 24.61 | 24.61 | 1.000 (same program) | 23.58 | 23.58 |
1.000 (same program) | 23.55 | 23.55 | 1.000 (same program) |
| 16000 | 512 | 4096 | 512 | 32 | 4 x 10, uniform | swap_run32 /
swap_run32 | 25.81 | 25.81 | 1.000 (same program) | 24.74 | 24.74 |
1.000 (same program) | 24.67 | 24.67 | 1.000 (same program) |
| 16000 | 512 | 4096 | 512 | 32 | 8 x 10, uniform | swap_run32 /
swap_run32 | 32.24 | 32.24 | 1.000 (same program) | 32.03 | 32.03 |
1.000 (same program) | 32.10 | 32.10 | 1.000 (same program) |
| 16128 | 512 | 4096 | 512 | 32 | 16 x 10, uniform | swap_run32 /
swap_run32 | 49.86 | 49.86 | 1.000 (same program) | 49.65 | 49.65 |
1.000 (same program) | 49.63 | 49.63 | 1.000 (same program) |
| 16256 | 512 | 4096 | 512 | 32 | 32 x 10, uniform | swap_run32 /
swap_run32 | 84.27 | 84.27 | 1.000 (same program) | 84.05 | 84.05 |
1.000 (same program) | 84.06 | 84.06 | 1.000 (same program) |
| 65664 | 512 | 4096 | 512 | 128 | 64 x 10, uniform | swap_s16 /
swap_s16 | 122.85 | 121.84 | 0.991 | 121.90 | 120.90 | 0.992 | 122.08 |
121.01 | 0.991 |
| 65152 | 4096 | 256 | 512 | 128 | 1 x 10, uniform | n256_s16 / n256_s16
| 32.90 | 32.80 | 1.000 | 32.16 | 32.05 | 1.004 | 32.03 | 31.95 | 1.001
|
| 65152 | 4096 | 256 | 512 | 128 | 8 x 10, uniform | n256_s16 / n256_s16
| 41.54 | 41.25 | 0.992 | 40.21 | 39.74 | 0.995 | 39.87 | 39.68 | 0.995
|
| 65408 | 4096 | 256 | 512 | 128 | 32 x 10, uniform | n256_s16 /
n256_s16 | 66.45 | 64.22 | 0.969 | 65.22 | 63.42 | 0.969 | 65.04 | 63.10
| 0.978 |
| 67584 | 4096 | 256 | 512 | 128 | 256 x 10, uniform | swap_carry_s16 /
swap_carry_s16 | 101.61 | 98.58 | 0.971 | 97.92 | 94.13 | 0.959 | 98.13
| 94.10 | 0.957 |
| 70144 | 4096 | 256 | 512 | 128 | 512 x 10, uniform | swap_carry_s16 /
swap_carry_s16 | 103.12 | 99.89 | 0.973 | 99.26 | 95.60 | 0.962 | 99.42
| 95.26 | 0.960 |
| 85504 | 4096 | 256 | 512 | 128 | 2048 x 10, uniform | n256_s16 /
n256_s16 | 128.43 | 123.09 | 0.958 | 124.50 | 119.39 | 0.959 | 124.02 |
119.10 | 0.960 |
| 105984 | 4096 | 256 | 512 | 128 | 4096 x 10, uniform | n256_s16 /
n256_s16 | 154.30 | 150.34 | 0.972 | 149.36 | 145.17 | 0.972 | 149.26 |
145.02 | 0.973 |
| 146944 | 4096 | 256 | 512 | 128 | 8192 x 10, uniform | n256 / n256 |
242.38 | 242.38 | 1.000 (same program) | 224.11 | 224.11 | 1.000 (same
program) | 223.07 | 223.07 | 1.000 (same program) |
| 228864 | 4096 | 256 | 512 | 128 | 16384 x 10, uniform | n256 / n256 |
389.55 | 389.55 | 1.000 (same program) | 355.18 | 355.18 | 1.000 (same
program) | 353.62 | 353.62 | 1.000 (same program) |
| 16000 | 4096 | 256 | 512 | 32 | 2 x 10, uniform | swap_run32 /
swap_run32 | 22.02 | 22.02 | 1.000 (same program) | 20.74 | 20.74 |
1.000 (same program) | 20.72 | 20.72 | 1.000 (same program) |
| 16000 | 4096 | 256 | 512 | 32 | 4 x 10, uniform | swap_run32 /
swap_run32 | 23.97 | 23.97 | 1.000 (same program) | 23.04 | 23.04 |
1.000 (same program) | 23.04 | 23.04 | 1.000 (same program) |
| 16000 | 4096 | 256 | 512 | 32 | 8 x 10, uniform | swap_run32 /
swap_run32 | 28.37 | 28.37 | 1.000 (same program) | 26.91 | 26.91 |
1.000 (same program) | 26.91 | 26.91 | 1.000 (same program) |
| 16128 | 4096 | 256 | 512 | 32 | 16 x 10, uniform | swap_run32 /
swap_run32 | 38.26 | 38.26 | 1.000 (same program) | 36.18 | 36.18 |
1.000 (same program) | 36.22 | 36.22 | 1.000 (same program) |
| 16256 | 4096 | 256 | 512 | 32 | 32 x 10, uniform | swap_run32 /
swap_run32 | 54.94 | 54.94 | 1.000 (same program) | 51.97 | 51.97 |
1.000 (same program) | 52.05 | 52.05 | 1.000 (same program) |
| 65664 | 4096 | 256 | 512 | 128 | 64 x 10, uniform | swap_carry_s16 /
swap_carry_s16 | 82.42 | 79.55 | 0.966 | 80.06 | 76.61 | 0.955 | 80.16 |
76.46 | 0.956 |
| 65280 | 1024 | 2048 | 256 | 128 | 4096 x 8, skewed | swap_carry_s16 /
n256_s16 | 112.64 | 112.37 | 0.997 | 110.03 | 109.52 | 0.996 | 109.98 |
109.33 | 0.996 |
| 65280 | 2048 | 512 | 256 | 128 | 4096 x 8, skewed | n256_s16 /
n256_s16 | 75.66 | 74.46 | 0.987 | 71.60 | 71.42 | 0.992 | 71.49 | 70.94
| 0.993 |
| 105984 | 512 | 4096 | 512 | 128 | 4096 x 10, skewed | swap_s16 /
swap_s16 | 205.09 | 204.83 | 0.999 | 198.03 | 197.78 | 0.997 | 198.67 |
198.38 | 0.998 |
| 105984 | 4096 | 256 | 512 | 128 | 4096 x 10, skewed | n256_s16 /
n256_s16 | 164.90 | 163.25 | 0.990 | 156.77 | 154.24 | 0.982 | 156.06 |
153.66 | 0.983 |
| 163584 | 1024 | 2048 | 256 | 128 | 16384 x 8, skewed | swap_carry /
swap_carry | 264.17 | 264.17 | 1.000 (same program) | 235.89 | 235.89 |
1.000 (same program) | 234.85 | 234.85 | 1.000 (same program) |
| 34560 | 2048 | 512 | 256 | 128 | 256 x 8, skewed | swap_s16 / swap_s16
| 45.31 | 43.62 | 0.962 | 43.78 | 42.50 | 0.969 | 43.74 | 42.46 | 0.967
|
| 1152 | 256 | 512 | 8 | 64 | explicit, 565 valid rows | swap_run32 /
swap_run32 | 6.45 | 6.45 | 1.000 (same program) | 6.45 | 6.45 | 1.000
(same program) | 6.42 | 6.42 | 1.000 (same program) |
| 640 | 1024 | 256 | 8 | 32 | explicit, 297 valid rows | swap_run32 /
swap_run32 | 6.32 | 6.32 | 1.000 (same program) | 6.03 | 6.03 | 1.000
(same program) | 6.05 | 6.05 | 1.000 (same program) |
| 1152 | 384 | 128 | 6 | 96 | explicit, 487 valid rows | n128_run32 /
n128_run32 | 6.913 | 6.913 | 1.000 (same program) | 6.112 | 6.112 |
1.000 (same program) | 5.824 | 5.824 | 1.000 (same program) |
| 1664 | 384 | 128 | 8 | 128 | explicit, 556 valid rows | n128_s16 /
n128_s16 | 4.93 | 4.90 | 0.993 | 5.09 | 5.20 | 1.010 | 4.99 | 5.12 |
1.019 |
| 1664 | 256 | 4096 | 5 | 128 | explicit, 1028 valid rows | swap / swap
(B200 shipped: n128) | 12.82 | 11.10 | 0.866 | 10.43 | 10.43 | 1.000
(same program) | 10.37 | 10.37 | 1.000 (same program) |

Besides these UE8M0 programs, Cake ships `cake_grouped_fp8_gemm` with
FP32 per-128-block scales, plus the fused SiLU-and-quantize form
`cake_grouped_fp8_fused_silu_quant` and the masked batch form
`cake_batch_deepgemm_fp8`; all of them ship on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added additional execution routes for grouped FP8 matrix
multiplication, including store16 options and support for more GPU
architectures.
* Route selection now accounts for alignment, group size, and long-K
workloads to choose an eligible execution path.
* **Behavior Changes**
* Output values in padding rows are unspecified; only routed rows are
checked for results. Output padding may be written in 16-row or 32-row
units.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5b79a1f](https://github.com/flashinfer-ai/flashinfer/commit/5b79a1f2223ee1e5e6c5598b5a37893704e0dcce)

- **作者**: eigen
- **时间**: 2026-10-25T23:22:23Z
- **提交信息**: deslop(cake_fp4_allreduce): drop 5 unreachable prefetch programs, fold 14 _pf twins, share 10 bindings, trim registry (#7366)

## 📌 Description

### Summary

This PR is a deslop of the Cake-exported `cake_fp4_allreduce` package.
The package is the NVFP4-transport all-reduce with fused residual +
RMSNorm behind `cake_fp4_allreduce`, `cake_fp4_allreduce_nvfp4`,
`cake_fp4_allreduce_rmsnorm` and `cake_fp4_allreduce_rmsnorm_nvfp4`. It
targets B200 (SM100), GB300 (SM103) and R200 (SM107). Each (program,
target) pair builds one JIT module from one kernel source and one
binding source.

At the base, the package has:
- 116 `.cu` files under `csrc/cake_fp4_allreduce/`: 58 `*_kernel.cu`
(241,718 lines) and 58 `*_binding.cu` (10,799 lines);
- the registry `flashinfer/jit/cake_fp4_allreduce_programs.py` (3,367
lines), with 58 `PROGRAMS` records of 34 keys and 11 `SELECT_ROWS`
bands;
- the loader `flashinfer/jit/cake_fp4_allreduce.py` (639 lines);
- 75 modules: 27 on sm_100a, 28 on sm_103a and 20 on sm_107a.

The four commits are mechanical:
- commit 1 removes 5 fused-norm prefetch programs that no shipped GPU
selects;
- commit 2 folds the 14 remaining `_pf` kernels into their base kernels
behind `-D` switches;
- commit 3 replaces 53 per-program bindings with 10 shared bindings, one
per form;
- commit 4 drops unread registry keys, dead loader code and 5 table
tests.

The commits hand-edit exporter-written kernels, bindings and the
registry. These edits are pending exporter regeneration.

Totals versus `main` `a4dc7d17f`, counted without rename detection: 103
files changed (8 added, 75 deleted, 20 modified), +2,038 / −83,919. The
package goes from 116 `.cu` files to 49 (39 kernels, 10 bindings).
Programs go from 58 to 53, modules from 75 to 68, and test ids from 114
to 109.

### Changes

Base: `main` `a4dc7d17f`. Head:
`37a83de1c6e37ee41812956222f418c34b36ad2e` (4 commits). Several commits
edit the registry, the loader and the host test, so the per-commit
counts do not sum to the totals.

### Commit 1 (4376c61c5) - drop the 5 never-selected fused-norm prefetch
programs (13 files, +77 / −21,615)

- **The programs.** `tp2_rmsnorm_bf16_bf16_p2d_u4_w11_csp_sop_pf`,
`tp2_rmsnorm_bf16_mxfp8_p2d_w11_qp_csp_sop_pf`,
`tp2_rmsnorm_bf16_nvfp4_p2d_w11_qp_csp_sop_pf`,
`tp2_rmsnorm_bf16_nvfp4_p2d_w11_qp_sfu_csp_sop_pf` and
`tp2_rmsnorm_nvfp4_bf16_pa_p2d_u2_csp_pf` (7 modules, 10 files). The
removed prefetch programs are selected only on launch grids of 212 or
more CTAs. The all-reduce launches one CTA per SM. SM100 (B200) parts
have 148 SMs and SM103 (B300 / GB300) parts have at most 160 (the GB300
used for validation reports 152), so no shipped part reaches them.
- **Change.** The registry drops the 5 records and 5 band entries: the
four bands of removed programs and the band of
`tp2_rmsnorm_nvfp4_bf16_pa_p2d_u2_csp_sop_pf`, whose whole program was
removed. That program now serves its whole cell (`rows_kind` and
`rows_threshold` become `None`). Host test pins go from 58 to 53
programs and from 11 to 6 bands. The GPU test's comment now names the
148- and 160-SM configurations, and its AST does not change.
- **Proof.** Program selection over every cell and row count is
identical at 148, 160 and 211 SMs, and it never picks a removed program.
At 212 SMs only the 7 declared cells differ, at rows 6144 to 6147. The
106 kept sources match by hash, and no kept module name changes.
- **Behaviour.** None on any part with fewer than 212 SMs, which is
every shipped SM100 and SM103 part.

### Commit 2 (c18f53418) - fold the 14 `_pf` kernels into their base
kernels (31 files, +195 / −51,242)

- **The copies.** Each of the 14 prefetch kernels differs from its base
program's kernel by its kernel symbol and one three-line
`prefetch.global.L2` hunk on the residual input. Together they cover 18
prefetch modules and 18 base modules.
- **Change.** Each base kernel gains a default `#define
CAKE_FP4_ALLREDUCE_KERNEL cake_fp4_allreduce_<base id>` under `#ifndef`.
It names its `__global__` through that macro and holds the hunk under
`#ifdef CAKE_FP4_ALLREDUCE_PREFETCH`. The 14 `_pf` kernels are deleted.
Their records now point at the base kernel and keep their ids, bindings
and `kernel_symbol`. The new `program_defines(program)` returns
`-DCAKE_FP4_ALLREDUCE_KERNEL=<kernel_symbol>`, plus
`-DCAKE_FP4_ALLREDUCE_PREFETCH=1` for a prefetch program. The loader
passes this list through `extra_cuda_cflags` for every program. The host
test pins the macro form where a prefetch twin ships.
- **Proof.** Under its two define sets, each folded source preprocesses
to the two kernels it replaces, byte for byte (14 of 14). For each
(program, target), the gate requires identical preprocessed text, SASS,
symbol tables and resource usage.
- **Declared.** The module-name digest now covers the define list, so
all 68 module names change.

### Commit 3 (e33724c53) - share one binding per form, selected by `-D`
flags (64 files, +1,784 / −9,600)

- **The copies.** The 53 bindings fall into ten forms, one per (family,
world size, input format, output format). Within a form, bindings differ
only by the kernel symbol and the program id in their header comment. In
the three BF16-input fused-norm forms, block size and dynamic shared
memory also differ.
- **Change.** Ten shared bindings replace them: 51 files are deleted, 8
are added and the two `tp2_oneshot` files are rewritten in place. The
symbol, block size and shared memory come from
`-DCAKE_FP4_ALLREDUCE_KERNEL`, `-DCAKE_FP4_ALLREDUCE_THREADS` and
`-DCAKE_FP4_ALLREDUCE_DYNAMIC_SMEM`. Each sits behind `#ifndef` /
`#error` because a shared binding has no program of its own. The
launch-failure message stringizes the symbol through a two-level
`CAKE_STRINGIZE` helper. `program_defines` gains the two binding flags,
and each record's second source names its form's binding. The host test
checks each record's form, the three guards and the four flags.
- **Proof.** Under a program's flags, the shared binding preprocesses to
that program's own binding, token for token on both passes. This holds
under the two declared masks described in Validation. Export sets match
under one declared mask. SASS matches on 9 spot modules.
- **Behaviour.** The message is now two adjacent string literals. The
compiler joins them, so the message reads the same. Error tracebacks
from the host checks now name the shared binding's file and line. All 68
module names change because the binding bytes enter the digest.

### Commit 4 (37a83de1c) - drop unread registry keys, dead loader code,
table tests (3 files, +41 / −1,521)

- **Change.** Each record has 34 keys. The loader, the dispatch and the
GPU test read 16 of them. The registry drops the other 18, which have no
run-time reader: the host test read most of them, `poll` was also read
in the loader, only by the dead `programs(poll=)` filter that this
commit removes, and three had no reader at all. It also drops the unread
`WINDOWS` keys `table_entries`, `cap_max` and `world_size`, and the
`SELECT_ROWS` key `whole`. The loader drops `output_formats()`, the
`CakeFp4AllReduceTarget` alias, the `programs(poll=)` keyword and the
`getattr` fallback for `SELECT_ROWS`. Five host tests that restated the
tables are deleted. Six tests, two fixtures and one constant are trimmed
to the kept keys.
- **Proof.** The registry literal equals the parent minus the declared
keys. The loader and host test ASTs change only in the declared
statements. No reader of a dropped key or dead name remains. No module
name changes (0 of 68).
- **Behaviour.** None at run time. `output_formats` and
`CakeFp4AllReduceTarget` leave the `__all__` of a private module. Test
ids go from 114 to 109.

### Validation

The compile rows run on a CPU node with CUDA 13.4 for both trees,
including sm_107a. Each row builds one module per side with the loader's
JIT compile line and that side's `-D` list. The text rows compare token
streams from the host pass and the target's device pass, with line
markers and blank lines removed. In the row values below, G-A to G-D are
the four compile runs (base to commit 1, commit 1 to commit 2, commit 2
to commit 3, and base to head), U1 to U4 are commits 1 to 4, N0 means
line markers and blank lines removed, TOK means token-stream comparison,
TU is one source file, and E-B-F and H-A name the two declared masks
described under Binding text and Export sets.

**Chain**

- **Apply replay.** Each commit's apply script is replayed on a fresh
base and must reproduce that commit's tree: 4 unit scripts replayed on a
fresh checkout of the base (U1 U2 U3 U4); the resulting tree is
identical to the pre-format tree of each commit; the format patches fold
on top for U1, U2, U3, U4
- **Formatting.** clang-format, ruff-format and the whitespace hooks ran
per commit. The repository config excludes this package's `*_kernel.cu`
files. Only commit 3 has a patch (8 files), and the patch leaves token
streams and ASTs unchanged: clang-format (shared bindings; the
`*_kernel.cu` files are hook-excluded) + ruff-format + the whitespace
hooks folded per unit on a CPU node (pre-commit hooks, repo config);
patches: U1 0 B over 0 of 3 files (whitespace hooks rewrote 0); U2 0 B
over 0 of 17 files (whitespace hooks rewrote 0); U3 12,196 B over 8 of
13 files (whitespace hooks rewrote 0); U4 0 B over 0 of 3 files
(whitespace hooks rewrote 0); a second pass is a no-op

**Compile rows**

- **Kernel text.** 36 rows per kernel run, each under the program's `-D`
list. Macro-selected forms are proven on preprocessed text, not by SASS
alone: G-B 36/36; G-D 36/36 (kernel TUs: both -E passes token-identical
after N0 under each program's -D list; the folded prefetch hunk and the
kernel-symbol macro default proven by preprocessed text, never by SASS
alone)
- **Binding text.** 68 rows per binding run, with two declared masks.
First, the two adjacent string literals of the launch-failure message
are joined. Second, the `__FILE__` / `__LINE__` pairs in the
`TVM_FFI_CHECK` tracebacks are masked: 1,144 pairs per run, each moved
by 15 to 17 lines. Header sites must match exactly. Run-time
consequence: error tracebacks from the host checks name the shared
binding's file and line: G-C 68/68; G-D 68/68 (binding TUs: N0 +
string-literal concatenation (translation phase 6) + TOK; the __FILE__ /
__LINE__ check-traceback sites masked per row after the join and
reported as counts (declared deviation E-B-F), header sites identical)
- **Include closure.** G-C: the include closure of one binding
(tp2_oneshot_bf16@sm_100a) reaches the same repository files on both
sides (3 files on each side), no Python include added; G-D: the include
closure of one binding (tp2_oneshot_bf16@sm_100a) reaches the same
repository files on both sides (3 files on each side), no Python include
added
- **Shared headers.** none (no shared device header in this family)
- **SASS.** Compared per function, with addresses and encodings masked
and no symbol mask: G-B 36/36; G-D 36/36 (per-function SASS identical,
cubin sha per module; CUDA 13.4)
- **Symbol tables.** Must be identical. A mask for the source-file
symbol is allowed only where a side has one, and it applied on no row:
G-B 36/36; G-D 36/36 (full symbol multiset identical; the TU-basename
FILE symbol masked only where present, counted)
- **Resource usage.** Registers, shared memory and stack, compared
strictly: G-B 0 differences; G-D 0 differences (registers, shared
memory, stack and spills per symbol)
- **Export sets.** The compiler gives each anonymous namespace a name
unique to its source file (`_GLOBAL__N_...`). The bindings' helpers in
that namespace are global symbols, so moving to a shared binding renames
them. The row masks only that identifier. The FFI entry points and the
undefined kernel symbol are compared unmasked. Run-time consequence:
none, because nothing looks the helpers up by name: G-C 68/68; G-D 68/68
(nm export sets identical once the per-TU anonymous-namespace identifier
that the compiler assigns is masked (declared deviation H-A; masked rows
per run: G-C 68, G-D 68); __tvm_ffi_run present; kernel symbol undefined
on both sides)
- **Spot rows.** Nine full modules, three per target: G-C 9/9; G-D 9/9
(SASS and symbol-table rows for both the kernel and the binding of each
shared-binding module)
- **Coincidence.** Every source that a run does not compile must match
by sha256: G-A 106; G-B 78; G-C 39; G-D 25 (sha256 identity, between the
two revisions, of every file of the package directory that the run does
not compile)
- **Deleted and added files.** G-A 10/10; G-B 14/14; G-C 51/51; G-D
75/75 (every deleted path absent at the later revision; the added shared
bindings compiled)

**Other rows**

- **Digests.** The module-name digest hashes the kernel bytes, the
binding bytes and, from commit 2 on, each `-D` define. At the head, all
68 names differ from the base, which is every module of the family. The
define list and the shared binding bytes both enter the digest. 7 names
are removed, and commit 4 renames none: module names distinct on both
trees (prefix cake_fp4_allreduce_, 20-hex digest over kernel || binding
|| each -D define); 68 module names change at HEAD (U1 0, U2 68, U3 68,
U4 0); the loader's module names equal that rule on both trees
- **New macro names.** 4/4 new macro names: 0 hits in the family at the
base, present at HEAD, outside-family hits identical
- **Reference search.** Covers the removed ids, deleted paths, dropped
keys and dead names: 12/12 reference rows (removed program ids, deleted
paths, dropped keys, dead names): 0 hits at HEAD in their scope, > 0 at
the base
- **AST.** 5/5 (dispatch, GPU test, host test, loader, registry literal)
- **Program selection.** The real `program_for` runs over 30 cells and
every row count at grids 148, 160, 211 and 212. Expected: identical
results at 148, 160 and 211, and at 212 only the 7 declared cells
differ: program_for over 30 cells x rows 1..cap_max (3,103,512 points
per grid) x grids 148, 160, 211, 212: 113/120 (cell, grid) pairs
identical; the 7 declared pairs differ only at grid 212 where a removed
program would have been selected; 0 errors
- **Test id sets.** 114 ids at the base and at commits 1 to 3, and 109
at the head: 114 -> 109 ids: 5 removed
(test_fused_norm_programs_cover_every_form_once_per_target,
test_one_shot_programs_serve_every_target_once,
test_registry_bands_are_the_measured_cells,
test_select_rows_bands_name_dispatched_programs_with_their_whole_program,
test_two_shot_programs_cover_every_variant_once_per_target), 0 added
- **Tests with CUDA hidden.** Both files run on both trees and are
compared per id: base 114 ids: 108 passed / 6 skipped; head 109 ids: 103
passed / 6 skipped (CUDA hidden; the 6 GPU ids skip identically on both
trees), 0 pre-existing failures, per-id identical on the common ids; 5
table tests removed by design (-5 / +0)
- **Tests on B200** (SM100, 148 SMs). The 6 GPU ids run on 4 GPUs, base
arm then head arm. Each arm uses a fresh JIT directory with no prebuilt
module provider. Each arm first builds every module of the target (27 at
the base, 24 at the head): base 6 ids: 6 passed / 0 skipped; head 6 ids:
6 passed / 0 skipped on 4x B200 (SM100) (148 SMs, driver 580.82.07), 0
failures on both arms, per-id identical incl. skip reasons; fresh JIT
workspace per arm, both arms on one node
- **Tests on GB300** (SM103, 152 SMs on the validation node). The same
run, building 28 modules at the base and 24 at the head: base 6 ids: 6
passed / 0 skipped; head 6 ids: 6 passed / 0 skipped on 4x GB300 (SM103)
(152 SMs, driver 580.159.03), 0 failures on both arms, per-id identical
incl. skip reasons; fresh JIT workspace per arm, both arms on one node
- **Tests on R200** (SM107). No SM107 node ran the test. The sm_107a
compile rows are the evidence of record: not run: the SM107 build is
covered by the compile rows; no SM107 node ran the test in the
validation window
- **JIT isolation.** B200 (SM100): base 27 + head 24 modules built by
the per-arm prewarm (build_jit_specs over the registry), module dirs ==
the chain's module names and no module outside that set, pytest's log
has no FlashInfer build marker; the loader's build step re-ran at load
and rewrote the module file (27 of 27 base-arm modules, 24 of 24
head-arm modules); GB300 (SM103): base 28 + head 24 modules built by the
per-arm prewarm (build_jit_specs over the registry), module dirs == the
chain's module names and no module outside that set, pytest's log has no
FlashInfer build marker; the loader's build step re-ran at load and
rewrote the module file (28 of 28 base-arm modules, 24 of 24 head-arm
modules)
- **CPU checks.** Chain shape, file scope, untouched shared files such
as `.pre-commit-config.yaml` and `pyproject.toml`, ruff, pre-commit,
mypy and file hygiene: 22/22
- **Rows limited by the environment (count and reason):** 1: the SM107
(R200) GPU test row (the SM107 build is covered by the compile rows; no
SM107 node ran the test in the validation window)

### Not in this PR

- **Six of the ten `LIMITS` keys.** They have no run-time reader.
Whether to read them or drop them is an owner-side decision.
- **The prefetch axis, the `rsb` route and the row bands.** These are
performance decisions and need re-measurement.
- **Per-target program forms.** Folding them is exporter work and needs
per-target re-measurement.
- **The host path.** A per-program launch plan built at workspace init.
No step is proposed.
- **Deriving `kernel_symbol` from the program id.** The key stays as the
source of `-DCAKE_FP4_ALLREDUCE_KERNEL`.
- **Exporter emission.** These hand edits are pending exporter
regeneration. The registry keeps its "do not edit" line. The rules are
filed on #7225 as a comment.
- **Untouched files.** `flashinfer/comm/cake_fp4_allreduce.py`,
`tests/comm/cake_fp4_allreduce_reference.py`,
`benchmarks/comm/bench_cake_fp4_allreduce.py`, `docs/api/comm.rst`,
`flashinfer/aot.py`, `flashinfer/comm/__init__.py` and the shared
repository files.

## 🔍 Related Issues

Part of #7225

The deferred items are listed under "Not in this PR". The exporter rules
are filed on #7225 as a comment.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks ran per commit with the repository config: clang-format,
ruff-format and the whitespace hooks. `pre-commit run --all-files` on
the head, on a CPU node: 16 hooks, 15 passed, 1 skipped, 0 failed, no
patch; the base gives the same result. The CPU checks row in Validation
gives the per-commit result.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

The CI test files are `tests/comm/test_cake_fp4_allreduce.py` and
`tests/comm/test_cake_fp4_allreduce_host.py`. Commit 1 changes one
comment in the GPU file. Every commit updates the host file, and commit
4 deletes 5 of its tests. The GPU shapes are the 6 ids of
`tests/comm/test_cake_fp4_allreduce.py`: all-reduce bf16 and nvfp4 at
TP2 and TP4, and RMSNorm bf16 and nvfp4 at TP2. They run on 4 GPUs of
B200 and of GB300, and TP4 uses 4 ranks. Validation records the R200 row
as not run.

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.

This PR is not experimental. The package lives under
`csrc/cake_fp4_allreduce/` with its loader
`flashinfer/jit/cake_fp4_allreduce.py`, and its tests live under
`tests/comm/`. So this PR declares no experimental test scope.

## Reviewer Notes

- **Reading the proof.**
- Kernels and bindings: compare preprocessed text per (program, target)
under each program's `-D` list.
- Modules: compare SASS and symbol tables, and the export sets under the
anonymous-namespace mask.
  - Python: read the registry, loader and test AST rows.
- GPU tests: per-id identity on B200 and GB300, with a fresh JIT
directory per arm and its module build count.
  - CPU tests: run with CUDA hidden.
- **Hand edits.** The exported kernels, bindings and registry are
hand-edited pending exporter regeneration.
- **Commit 3 message.** The message says the bindings are committed
before the formatter pass. The clang-format patch was folded in
afterwards, so the committed bindings are formatted.
- **Module cache.** All 68 module names change, so modules built under
base names are not reused. Program names stay the same.
- **Coverage.** On H100 (SM90) the GPU ids skip by construction (the
test skips when the loader reports no supported capability for the
device) and the host file runs without CUDA.
- **Base.** This PR is published from `main` `a4dc7d17f`. The branch was
checked versus `main` `9e016bdfc`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added compile-time selection of all-reduce kernels and launch
settings, with optional residual-data prefetching for supported kernels.

* **Refactor**
* Consolidated kernel launch configuration and program records around
shared build definitions.
* Removed numerous variant-specific launch entry points and related
registry options.

* **Tests**
* Updated host-side dispatch and registry checks for the revised program
selection and build configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [04430a3](https://github.com/flashinfer-ai/flashinfer/commit/04430a391bba65ae03a44d52a1e8aff7dd6f981e)

- **作者**: Yang Xu
- **时间**: 2026-10-25T23:16:02Z
- **提交信息**: [Attention] Reuse bounded cuDNN prefill plans and gate Blackwell paged auto (#6231)

## Latest capture-lifetime fix (`6cbd9ff66`)

Changing query partitions after an FA2 capture could leave its
CPU-generated output/merge schedule stale when a later `auto` plan chose
cuDNN. Refreshing the Q/KV indptr buffers alone was insufficient. The
exact preceding public head `e9193db317ba` reproduces all eight
FA2-first failures; cuDNN-first controls pass. Keeping the query
partition or explicitly replanning FA2 fixes the failure; skipping cuDNN
execution does not.

Graph-mode `auto` now keeps FA2 once FA2 has been planned, so each later
plan refreshes the schedule retained by that capture. Eager provider
switching is unchanged. A cuDNN-first capture remains valid through
fallback because its metadata is still refreshed; use a separate wrapper
to choose cuDNN for a new graph after planning FA2. This adds one
plan-time condition, no second planner/cache/state, and no `run()` work.
Both public wrapper `run()` bodies are AST-identical to the parent.

**Exact-source B200 validation:** 70 focused tests passed without skips,
including 32 combinations of initial provider, eager/graph mode,
CPU/device lengths, owned/external tables and NH/HN Stats. Changed query
partitions, page IDs and values are checked against references. Balanced
parent/fix/fix/parent measurement also passed 1,700 output/lifecycle and
1,000 strict-LSE checks across seven workload geometries. Common
development FE1.32 with matching native extension, cuDNN9.27, DSL4.8,
Torch2.14/cu130; no forced FE engine or FROST-enable override.

**Performance scope:** there is no broad GPU or host regression in this
sample, but not every measurement is unchanged. For B1 H32/8 D128
Q128/KV8192, external table and NH Stats, graph plan+1 replay
is64.92→65.57us, warmrun37.38→37.23us, and GPU replay32.837→32.805us.
Plan+32replays is145.22→150.28us (+3.88%/+3.35% in the two orders); that
small host increase remains unassigned. These are host enqueue and
hot-input CUDA-event measurements, not serving TTFT or a speedup claim.

The preceding head's internal CI completed (9,511 passed /1,123 skipped
across29 runtime jobs); it does not certify this new commit. Fresh-head
review/CI and broader mixed-length paged-auto performance qualification
remain before merge. The official FE1.32 wheel/native pairing is a
post-release follow-up, **not a release-date merge prerequisite**;
runtime version/capability gates remain in place.

<!-- .github/pull_request_template.md -->

## 📌 Description

Consolidate the pending cuDNN prefill integration into one review:
bounded ragged graph reuse, caller-workspace-aware planning, cheaper
paged metadata staging, and a release-gated Blackwell paged-auto path.
Serving steps can change lengths and pointers while retaining prepared
plans and valid older CUDA Graph captures.

This is the single review entry replacing #6168, #6209, #6213, #6216,
and #6223. Their complete commit histories are retained; they are no
longer separate merge prerequisites. The branch incorporates main at
`aec44bda63e69b657b7fee4935a3d5b2ffe08462`, preserving its LSE guards
and per-token/head-scale FA2 selection.

Review the two production files in three parts:

1. **Bounded ragged plans and lifetime capacity.** Extend the existing
MLA cache to SM100/SM107 D128 FP16/BF16 and short Q2–63 prefixes; Q=1
remains separate. A CUDA Graph wrapper's enforced initialization
capacity participates in immutable graph keys. Replanning fewer live
tokens never shrinks that capacity. Ordinary dynamic wrappers retain the
B/Q envelope.
2. **Workspace and plan-time staging.** Select a separately cached FE
plan within the caller's workspace budget; do not mutate a graph held by
an older capture. Reuse page-table capacity and stage page
mappings/lengths in `plan()`.
3. **Gated paged auto.** On SM100, admit causal BF16 HND D128/V128,
page16, B1–4, Hq8–64, GQA1/2/4/8/16, Q64–1024, KV2K–32K, KV >= 4Q, and
`total_query_tokens * Hq * max_KV >= 8 * 1024 * 1024`. This upper bound
remains a cheap initial rejection. When KV lengths are already on CPU,
additionally require `Hq * sum(Q_i * KV_i) >= 8 * 1024 * 1024`, pairing
each query with its own KV length. With GPU-only lengths and explicit
maxima, preserve the previous bound-based policy to avoid a
fallback-induced host readback. Stable FE1.32+, its matching native
paged capability, a compatible FROST runtime and cuDNN9.27+ are
required. Unsupported features and older runtimes retain their existing
auto route. Full prefill and large batches are outside this admission.
Preserve and refresh older cuDNN captures through FA2 fallback. In graph
mode, keep FA2 after its first plan to refresh captured scheduling
metadata; eager auto may switch in either direction.

Public signatures are unchanged. Eligible paged `auto` dispatch changes
as described above; public wrapper `run()` implementations remain
unchanged. Backend and FROST use the same FE graph contract, with no
forced engine, split count or new caller knob.

**Remaining qualification.** Complete broader paged-auto performance
qualification, including skewed mixed-length batches. The preceding head
completed public/internal GPU CI and incremental review. The
capture-lifetime fix above requires fresh-head review and CI.
Development FE1.32 with its matching native extension has been tested as
documented below. Publishing the official FE1.32 wheel is not itself a
merge prerequisite: the runtime version/capability gate remains in
place, and older runtimes keep their existing route. Verify the
published wheel/native package after release. This consolidation is not
a claim of universal eager or vLLM serving speedup.

### Review follow-up (931a28e2c)

- Preserve FP16/BF16 run-time calibration on the graph route: Q/K scales
multiply the attention score scale; V scales O without changing LSE. GPU
float32 scalars remain device bindings and are reread on replay. The
kernel was receiving incomplete plumbing, not computing a correctly
supplied scale incorrectly. FP8 scale handling is unchanged.
- Refresh wrapper-owned page tables retained by older CUDA Graphs even
when a later plan supplies an external table. Preserve the captured
pointer/row stride, copy the retained width and clear unused tail
entries. Cover narrower/wider tables and cuDNN/FA2 transitions.
- Use the native D128 capability for D128 packed-capacity tests and
restrict only the bounded-override case to its qualified architectures.
- Keep small work on FA2 using the work floor above. This addresses the
[reported small-shape
regression](https://github.com/flashinfer-ai/flashinfer/pull/6231#pullrequestreview-5556625244),
without a tuple-specific blacklist or timing/winner golden. It does
**not** establish universal wins for mixed-length batches; those remain
a qualification item.

The original numerical probe was rerun **before narrowing admission**:
auto still selected cuDNN, `v_scale=0.5` returned0.5, and an older
owned-table capture returned3 after replanning to the external table.
New tests also independently exercise nontrivial Q-only and K-only
scaling, fresh device scalar pointers, and changed scalar/input values
on replay.

Default warm execution remains unchanged: both wrapper `run()` bodies
and the prepared runtime-key/match/execute functions are AST-identical
to07d125a96. Scale-key normalization occurs only in the
graph-build/cache path; no new per-run metadata staging or D2H scale
extraction is introduced. No main-kernel change or new public API/knob.

### Host-visible work refinement (`884f48531`)

The reported skewed Q=[1,128], KV=[32768,2048], Hq=8 case now retains
FA2 by using paired per-request work when host lengths are available.
Keep the old cheap upper-bound rejection before optional-runtime
queries. Explicit-bound GPU-length planning retains its previous
no-readback policy: simply declining cuDNN would make FA2 stage those
lengths on CPU. No run, kernel, cache, public-signature or caller-knob
change.

Two new cases in the existing wrapper regression file guard that
no-readback contract with synchronization debugging and a pending GPU
event. They require an admitted CPU-metadata control dynamically,
without a heuristic-winner or timing golden. Published931a passes both;
an unpublished draft that declined GPU-only lengths fails both; the
repaired implementation passes both. This change does not claim to close
every remaining mixed-length selection gap or recover GPU-only
distribution information.

### Historical B200 evidence

These are earlier component measurements, not measurements of this
refreshed head.

**Ragged initialized-capacity slice (#6223):**

Same public ragged wrapper, ordinary shape override enabled, BF16
D128/V128, HN natural-log LSE, four independent layer buffers. B200 (148
SMs, 1000 W), cuDNN 9.27.0.42, FE at merged NVIDIA/cudnn-frontend#1452
(`16e6d19dc`), DSL 4.8, Torch 2.12 / CUDA 13.2. Baseline uses the exact
#6209 attention source; two arm orders. GPU times include setup and
combine. These are component measurements, not serving throughput.

| Shape | GPU replay before / after | Host plan before / after | Host
enqueue per layer before / after |
|---|---:|---:|---:|
| H32/8; Q=[300,40,40,40]; KV=[16384,8000,8000,8000] | 292.09 / 146.79
us | 39.52 / 40.51 us | 50.43 / 42.75 us |
| H64/8; Q=[128,10,10]; KV=[8192,8192,8192] | 205.85 / 78.59 us | 39.70
/ 40.59 us | 48.66 / 40.57 us |
| H64/4; Q=[61,50,16,16]; KV=[11571,13689,15793,10376] | 369.68 / 100.01
us | 37.93 / 40.50 us | 48.55 / 42.01 us |

Plan plus four submissions improves 279.25→241.03us, 271.90→231.69us,
and 269.41→238.10us respectively, despite the small plan-time increase.
All three switch from the backend to the existing packed split2 plan;
final workspace is 13.87/9.78/9.45MB. L2-flushed replay confirms the
improvement. Separate `backend="auto"` runs for both BF16 and FP16
select cuDNN/FROST on all three cases and pass O/LSE and changed-input
replay checks.

This evidence applies to FI wrappers initialized with
`use_cuda_graph=True` and an enforced query capacity. It does not
establish a gain for ordinary dynamic wrappers or stock vLLM serving;
those paths need separate capacity integration and end-to-end
validation.


**Paged-auto slice (#6231, candidate `63b0955fd`):**

B200,148SM/1000W; Torch2.12/CUDA13.2, CuTeDSL4.8, cuDNN9.27.0.42,
FEdevelopc57af965 plus #1469. Exact candidate `63b0955fd`; public FI
wrapper with ordinary `use_cuda_graph=False` planning, pinned CPU plan
metadata, no caller-supplied block table/maxima. FA2 is the same-source
explicit backend and FA4 is vLLM-flash-attention
`9cd61de38763d712bb6ce56e2a02cc2bf718c89f` (vLLM source
`cbee82324c4ac2e780514122604f8f5fdb7c1d21`). Two reversed measurement
orders,32 independent layer buffers, warm CUDA-event replay including
all helper/combine kernels, plus directly timed eager attention-chain
completion. Outputs and changed-input replay are checked against an FP64
reference.

| B/Hq/Hkv; Q; KV | FA2 GPU us/layer | cuDNN auto GPU us/layer | FA4 GPU
us/layer | FA2 plan + 32 completed layers ms | cuDNN auto ms |
|---|---:|---:|---:|---:|---:|
|1/16/4;128;8192|40.46|23.50|32.10|1.386|1.357|
|1/64/8;128;8192|131.81|48.47|78.96|4.328|1.820|
|1/16/4;513;16384|237.83|84.65|136.82|7.716|2.974|
|3/16/4;[257,1,1];8192|90.17|54.06|75.59|2.981|1.993|

L2-flushed GPU replay confirms the direction. This is an attention-only
proxy, not serving throughput. Host cost is still higher than FA2:
plan94–103us versus43–44us, enqueue about36us versus13us per layer. The
first row is consequently close in a completed32-layer eager chain,
despite its GPU gain; short host-bound chains can lose. CUDA Graph
replay and per-step planning must be evaluated separately. New bucket
first-use still needs prewarming, and stock vLLM can select directTRTLLM
before reaching this wrapper.


The fixed-graph capacity variant also has an eager tradeoff: historical
measurements added approximately 4–6 us per submission while reducing
GPU replay. Neither these results nor the paged proxy establish
stock-vLLM serving throughput. New bucket first-use must be prewarmed.

Reproducible public-wrapper host/graph benchmark:

```bash
python benchmarks/bench_cudnn_wrapper_host.py --kind paged --batch 1 --q 128 --kv 8192 --qo-heads 16 --kv-heads 4 --layout HND --backends fa2 auto --replan --output paged-auto.json
```


## 🔍 Related Issues

Consolidates #6168, #6209, #6213, #6216 and #6223. Related FE
selection/capacity work: NVIDIA/cudnn-frontend#1439,
NVIDIA/cudnn-frontend#1452 and NVIDIA/cudnn-frontend#1469.

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

Scoped `pre-commit run --files` passed for all nine changed files. The
all-files checkbox above is intentionally not claimed.

## 🧪 Tests

Earlier released-runtime compatibility at `03092ec2b`: [authorized H100
CI](https://github.com/flashinfer-ai/flashinfer/actions/runs/39836781114/job/120027356967)
completed **663 passed / 141 skipped**, with no failures or unfinalized
tests. The job checked out `03092ec2b` merged into its current main base
and reports FE1.31.0, cuDNN9.24, DSL4.7 and Torch2.13/CUDA12.9. This
validates the existing route on older released dependencies; H100 does
not exercise the new SM100 paged-auto admission.

Earlier integration `50a9b2e72691`: native SM100 qualification passed
**370 tests / 1 multi-GPU skip**, including the first-auto capture
regression and per-token/head-scale plan checks. Scoped hooks and source
hashes passed. This historical run is not relabeled as validation of the
later `146d53935827` integration.

Earlier integration `03092ec2b`: **366 passed / 1 multi-GPU skip**
across the five focused cuDNN attention files plus two existing
per-token/head-scale planning checks on native SM100, development FE
`cfcb846a295f` with a freshly built matching native extension,
cuDNN9.27, and DSL4.8. The final merged FE tree is identical to the
locally tested integration tree. Exact FI source hashes were verified
after the run; scoped hooks passed. The process exited zero. Shutdown
still emitted nanobind reference-leak diagnostics, as in earlier
qualification; their cause is not attributed by this run. No new
performance measurement is claimed.

Previous `884f48531` production: **224 passed / 1 multi-GPU skip**
across the prepared-contract and wrapper-regression suites on native
SM100, development FE1.32/native, cuDNN9.27, DSL4.8. Separate
explicit-bound changing-length probes pass O/LSE without waiting for GPU
work. Scoped hooks pass for the three changed files. That exact head is
now approved, and internal pipeline 74849387 completed all 31 executed
test jobs successfully. The later main integrations are tracked
separately above.

Repair qualification at `931a28e2c`: native SM100 **362 passed / 1
multi-GPU skip** across the same five files (combined broad and final
affected-file runs). Final scale-key/capture/prepared check: **84
passed**. Independent H100 scale/capture check: **36 passed / 6 FP8
architecture skips**. FE development1.32/native, cuDNN9.27, DSL4.8.
These correctness counts are not a stable-release or serving
qualification. Scoped pre-commit passed on all six repair files.

New half-scale and retained-table cases were first run against
unchanged07d125a96 production code and failed, then passed after repair.
Existing FP8 tests and tolerances are retained. No new test file was
added.


- [x] Tests have been added or updated as needed.
- [ ] Fresh-head GPU CI for `6cbd9ff66`; preceding-head results are
preserved as historical coverage.

Earlier consolidation candidate `07d125a96`: **312 passed / 13 skipped**
across the five focused files below on SM107, development FE1.32 with
matching native extension, cuDNN9.27, DSL4.8, CUDA13.5 and Torch2.15
development. This is correctness/capture qualification, not new
performance evidence. Twelve skips require SM100 paged-auto admission;
one requires a second visible GPU.

The first run passed 283 tests; 29 reference/fallback tests stopped
before execution because the isolated source install lacked its
generated `flashinfer/data` JIT source links. After restoring the
standard build-backend links, exactly those 29 passed. Source and
tolerances were unchanged. All nine PR file hashes match the committed
candidate. The native-log2 mock separately reproduced three
workspace-query AttributeErrors before its fixture correction; all 28
native-log2 tests pass afterward.

```bash
pytest tests/attention/test_cudnn_native_log2.py tests/attention/test_cudnn_prepared_contract.py tests/attention/test_cudnn_ragged_shape_override.py tests/attention/test_cudnn_wrapper_regressions.py tests/attention/test_cudnn_prepared_graph.py -q -o addopts=
```

The preceding head had no actionable review defect and completed
upstream GPU CI; fresh review/CI for the capture fix is pending. Broader
SM100 paged-auto performance qualification remains pending. Older B200
and released-FE GPU fallback validation remains documented on the
superseded PRs; it is not relabeled as fresh-head validation. An earlier
review also reported 74 passed / 12 skipped CPU tests with released
FE1.31; these are historical CPU checks, not current-head GPU
qualification.

Coverage includes O/LSE references, changed-input replay, retained
captures, pointer rebinding, NH/HN Stats, workspace-constrained
fallback, runtime capability gates, page-table growth and provider
transitions. No new test files, timing thresholds or heuristic-winner
goldens are introduced.

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

Please focus on initialization capacity versus live length; cache
separation by workspace/capacity; and ownership of metadata retained by
captured calls. The refresh preserves main's LSE safety checks and fixes
an existing mock that did not implement the graph workspace query. The
review follow-up additionally repairs runtime scales and retained
external-table transitions; details above.

Remaining merge qualification: SM100 paged-auto performance, including
mixed-length workloads, plan + completed eager chains and GPU replay.
Preceding-head CI completion and fresh-head requirements are documented
above. Keep development FE/native compatibility and older-release
fallback covered; verification of the official FE1.32 wheel/native
package is a post-release follow-up, not a requirement to wait for the
release date. Historical small/host-bound chains and lower-SM
configurations are not covered by a universal speedup claim. The
capacity benefit requires an initialized graph-mode capacity; ordinary
vLLM integration still needs its own serving validation.

The PR is currently Ready for review; it is not being merged while those
qualification gates remain open.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Paged prefill can automatically select cuDNN for supported Blackwell
workloads; other workloads retain existing backend selection.
* Added bounded cuDNN prefill support for eligible FP16 and BF16
workloads on SM100 and SM107 GPUs, with runtime Q/K/V scaling.
* CUDA Graph plans retain query capacity across shorter replans and
support workspace-constrained execution.
* The cuDNN wrapper benchmark supports paged workloads and configurable
query/KV head counts.
* **Bug Fixes**
* Improved graph replay reliability when page indices, sequence lengths,
layouts, or backends change.
* Page-table reuse clears unused entries and checks that tables meet
required capacity.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e18eb1d](https://github.com/flashinfer-ai/flashinfer/commit/e18eb1d2ee324f758120fb99be33fecf14563590)

- **作者**: eigen
- **时间**: 2026-10-25T23:11:53Z
- **提交信息**: fix(cake_kimi_k3_fused_router): reject arm M launches below 128 plan-owner CTAs (#7365)

In the experimental Kimi-K3 fused MoE router
(`flashinfer.fused_moe.kimi_k3_fused_router`), arm M handles 129 to 256
tokens on SM100 and SM103. It gives each of its 128 plan-owner CTAs a
fixed slice of seven experts, and no other CTA publishes those experts.
`launch_grid` in `cake_backend.py` capped arm M's grid at the persistent
capacity (3 CTAs per SM on CC 10.0, 4 on CC 10.3) but never checked that
the grid stayed at 128 or more. On a device or MIG slice with fewer than
43 SMs (CC 10.0) or 32 SMs (CC 10.3), the launch would leave part of the
route plan unwritten instead of failing.

`launch_grid` now raises `RuntimeError` for arm M when the grid is below
128 owner CTAs, which is what the Q4S / Q4SP arms already do. Arms L /
LP and GW stride their owners over the experts, so they work with any
grid size. Their comments now say this. The README now says that 129 to
2048 tokens raise `RuntimeError` on a device or MIG slice that can't
hold 128 co-resident CTAs. Full B200 / B300 / GB300 parts have a
persistent capacity of 444 or more CTAs, so outputs on them don't
change. No generated kernel or binding source changes. The new
`test_launch_grid_small_devices` tests the 42 vs 43 SM (CC 10.0) and 31
vs 32 SM (CC 10.3) boundaries and checks that L / LP / GW keep their
grids.

Tests:
- `tests/experimental/test_cake_kimi_k3_fused_router.py`: 87 passed on
B200 (sm_100a) and on GB300 (sm_103a), both with the package as of #7355
(now on main) and with the package before it.
- Forcing smaller grids on both GPUs: with 96 CTAs, arm M writes no
counts, offsets or plan blocks for experts 672 to 895; arms L / LP and
GW give bit-identical plans with grids of 1 to 127.

The automated review on #7355 found this
([comment](https://github.com/flashinfer-ai/flashinfer/pull/7355#discussion_r4372129936)),
though the code is older than that PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Preparation now reports an error when a device or MIG slice lacks the
capacity needed for certain token counts, rather than attempting a
launch that cannot be supported.
* Other routing options continue to support smaller devices, with launch
sizes limited to available capacity.
* **Documentation**
* Clarified device-capacity requirements for token counts from 129 to
2048. The existing limit for counts above 8192 remains unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [967a8ed](https://github.com/flashinfer-ai/flashinfer/commit/967a8ed85870c40ff7549e977ebfc51eb0ffb4c9)

- **作者**: eigen
- **时间**: 2026-10-25T23:06:31Z
- **提交信息**: perf(cake_sage): SM120 block-sparse Sage attention computes P's first half ahead of the rescale vote (#7364)

The block-sparse Sage attention forward for SM120 (RTX PRO 6000 / RTX
5090), `flashinfer.cute_dsl.sparse.bsa_attn_sm120_blk64_sage_fwd(...,
backend="cake")`, takes prequantized INT8 Q and K, with QK^T on INT8
`mma.sync`, and FP8 (e4m3) V for the PV product. It produces BF16 output
with head dim 128, uses 64-token Q and KV blocks, is non-causal, and
takes a list of selected KV blocks for each Q block. One CUDA source is
specialized into 20 programs by five metadata flags: whether per-row KV
block counts are given, the block-size mask mode, whether every KV tile
is a full 64-token tile, whether every row selects the same non-zero
number of blocks, and whether the selected block indices are contiguous.
The host picks the specialization on each call. This PR regenerates that
source again for all 20 specializations, with bitwise-identical outputs.
On sm_120a it is 1.0031x to 1.0100x faster on all 8 shapes than the
previous Cake version (the `backend="cake"` path on main, shown as the
baseline below).

| batch | heads | seq len | selected KV blocks / all | baseline (ms) |
this PR (ms) | speedup | 95% CI |
|---:|---:|---:|---:|---:|---:|---:|---|
| 8 | 32 | 1024 | 15 / 16 | 0.2141 | 0.2121 | 1.0100x | 1.0091x -
1.0108x |
| 8 | 32 | 2048 | 16 / 32 | 0.4290 | 0.4256 | 1.0075x | 1.0068x -
1.0082x |
| 8 | 32 | 4096 | 7 / 64 | 0.4783 | 0.4769 | 1.0031x | 1.0026x - 1.0036x
|
| 8 | 32 | 8192 | 116 / 128 | 10.9677 | 10.9274 | 1.0037x | 1.0036x -
1.0038x |
| 8 | 32 | 16384 | 128 / 256 | 24.2547 | 24.1733 | 1.0033x | 1.0033x -
1.0034x |
| 8 | 32 | 32768 | 52 / 512 | 20.0529 | 19.9868 | 1.0033x | 1.0033x -
1.0034x |
| 4 | 32 | 65536 | 512 / 1024 | 202.6229 | 201.9672 | 1.0034x | 1.0030x
- 1.0038x |
| 4 | 32 | 65536 | 103 / 1024 | 39.2189 | 39.0776 | 1.0036x | 1.0036x -
1.0036x |

*NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120a, 188 SMs); CUDA
13.0 runtime; programs compiled with nvcc 13.4. Q, K and V are [batch,
heads, seq len, 128]. "Selected KV blocks / all" is the number of KV
blocks each 64-row Q block attends to, out of all KV blocks. The two seq
len 65536 rows use batch 4 because batch 8 exceeds the API's
2^31-element limit. Latency is the median of single cold-L2 calls. Each
side ran in its own process, with calls interleaved between the two
processes. Speedup is the reciprocal of the mean of 8 per-group
new/previous time ratios, shown with its 95% CI.*

The same Cake package also ships the Sage-FP8 block-sparse attention
forward (FP8 Q/K/V on tcgen05) and its fused FP8 quantizer for sm_100a
and sm_103a (B200, B300/GB300), and with this PR the SM120
INT8-QK/FP8-PV form stays on sm_120a, so the family covers sm_100a,
sm_103a and sm_120a.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Refreshed build metadata and integrity records for existing GPU
library packages. The listed package configurations remain unchanged,
and no user-facing behavior changes are included in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [bf82f4d](https://github.com/flashinfer-ai/flashinfer/commit/bf82f4d7973bc6cc9eee1cded6b3c631f0910c8e)

- **作者**: eigen
- **时间**: 2026-10-25T22:55:58Z
- **提交信息**: perf(cake_minimax_h3): N-split tail for the BF16 and MXFP8 out-projection GEMMs on SM100/SM103 (#7363)

`flashinfer.diffusion_ops.minimax_h3_out_proj` (BF16),
`minimax_h3_out_proj_mxfp8` (MXFP8 W8A8) and `minimax_h3_out_proj_nvfp4`
(NVFP4 W4A4) are the three variants of the MiniMax-H3 attention output
projection with the fused indexed gate and residual on SM100 (`sm_100a`)
and SM103 (`sm_103a`). The quantized variants run an
activation-quantization pass, then a persistent block-scaled GEMM with
the fused epilogue. The BF16 variant has no quantization pass. The NVFP4
variant already uses a tail split. This PR adds the same tail split to
the BF16 variant and the MXFP8 variant (E4M3 data, UE8M0 block-32
scales) on SM100 and SM103. The NVFP4 variant is unchanged. A BF16 shape
uses the tail split if it has at least 16 rows and a partial last wave
that fits in half a wave, within 10 waves (SM103) or 9 waves (SM100). An
MXFP8 shape uses it if it has at least 129 rows and meets the same
half-wave condition, within 26 waves (SM103) or 17 waves (SM100). For
those shapes, the GEMM now runs the tail tiles as half-width units (256
x 128 output columns), so the partial last wave costs about half a tile.
Every other shape runs the unchanged kernel. The output is bitwise
identical to main. Compared with the current main `minimax_h3_out_proj`,
the BF16 tail-split shapes in the 40-shape list are 1.012x to 1.041x
faster on GB300 (7 shapes, geomean 1.034x) and 1.012x to 1.020x faster
on GB200 (6 shapes, geomean 1.016x). Compared with the current main
`minimax_h3_out_proj_mxfp8`, the MXFP8 tail-split shapes in the 40-shape
list are 1.018x to 1.057x faster on GB300 (17 shapes, geomean 1.032x)
and 1.012x to 1.043x faster on GB200 (15 shapes, geomean 1.028x).

BF16 (`minimax_h3_out_proj`) on NVIDIA GB300 (`sm_103a`), CUDA 13.4.
Time of the complete operator (GEMM with the fused gate and residual;
BF16 has no quantization pass), median of 10 interleaved rounds (5
rounds in each of two sessions) with a cold L2. P = sequence-parallel
degree, M = rows. Rows with tail split = yes run the new tail schedule.
The other rows run the unchanged kernel in both columns, so their ratio
is run-to-run variation.

| P | M | tail split | before (µs) | after (µs) | speedup |
|---:|---:|:---:|---:|---:|---:|
| 1 | 33472 | no | 1544.0 | 1567.5 | 0.985x |
| 1 | 38528 | no | 1779.5 | 1780.9 | 0.999x |
| 1 | 38591 | no | 1779.5 | 1789.2 | 0.995x |
| 1 | 38592 | no | 1778.7 | 1788.6 | 0.994x |
| 1 | 38593 | no | 1776.7 | 1790.9 | 0.992x |
| 1 | 38656 | no | 1779.2 | 1775.9 | 1.002x |
| 1 | 48768 | no | 2262.1 | 2271.1 | 0.996x |
| 1 | 58944 | no | 2733.2 | 2740.4 | 0.997x |
| 1 | 74240 | no | 3436.6 | 3483.8 | 0.986x |
| 1 | 109952 | no | 5088.3 | 5129.7 | 0.992x |
| 2 | 16736 | no | 766.7 | 778.6 | 0.985x |
| 2 | 19264 | no | 881.5 | 882.7 | 0.999x |
| 2 | 19295 | no | 886.9 | 884.0 | 1.003x |
| 2 | 19296 | no | 882.6 | 882.7 | 1.000x |
| 2 | 19297 | no | 882.7 | 884.3 | 0.998x |
| 2 | 19328 | no | 879.1 | 885.7 | 0.993x |
| 2 | 24384 | no | 1123.9 | 1127.8 | 0.997x |
| 2 | 29472 | no | 1366.7 | 1372.3 | 0.996x |
| 2 | 37120 | no | 1714.2 | 1709.9 | 1.003x |
| 2 | 54976 | no | 2530.8 | 2546.5 | 0.994x |
| 4 | 8368 | yes | 383.3 | 378.6 | 1.012x |
| 4 | 9632 | no | 433.9 | 435.6 | 0.996x |
| 4 | 9647 | no | 435.8 | 434.5 | 1.003x |
| 4 | 9648 | no | 436.3 | 437.0 | 0.998x |
| 4 | 9649 | no | 433.5 | 433.6 | 1.000x |
| 4 | 9664 | no | 434.6 | 432.3 | 1.005x |
| 4 | 12192 | no | 554.9 | 556.9 | 0.996x |
| 4 | 14736 | no | 682.0 | 681.9 | 1.000x |
| 4 | 18560 | no | 861.5 | 858.6 | 1.003x |
| 4 | 27488 | no | 1266.5 | 1274.0 | 0.994x |
| 8 | 4184 | no | 197.4 | 196.9 | 1.003x |
| 8 | 4816 | yes | 227.7 | 218.9 | 1.040x |
| 8 | 4823 | yes | 228.0 | 219.0 | 1.041x |
| 8 | 4824 | yes | 228.5 | 220.4 | 1.037x |
| 8 | 4825 | yes | 227.6 | 219.0 | 1.039x |
| 8 | 4832 | yes | 227.4 | 218.6 | 1.041x |
| 8 | 6096 | no | 275.4 | 275.0 | 1.002x |
| 8 | 7368 | yes | 342.4 | 332.4 | 1.030x |
| 8 | 9280 | no | 426.1 | 426.1 | 1.000x |
| 8 | 13744 | no | 625.5 | 624.5 | 1.002x |

BF16 (`minimax_h3_out_proj`) on NVIDIA GB200 (`sm_100a`), CUDA 13.4.
Time of the complete operator (GEMM with the fused gate and residual;
BF16 has no quantization pass), median of 10 interleaved rounds (5
rounds in each of two sessions) with a cold L2. P = sequence-parallel
degree, M = rows. Rows with tail split = yes run the new tail schedule.
The other rows run the unchanged kernel in both columns, so their ratio
is run-to-run variation.

| P | M | tail split | before (µs) | after (µs) | speedup |
|---:|---:|:---:|---:|---:|---:|
| 1 | 33472 | no | 1848.0 | 1872.2 | 0.987x |
| 1 | 38528 | no | 2134.5 | 2130.6 | 1.002x |
| 1 | 38591 | no | 2141.0 | 2169.5 | 0.987x |
| 1 | 38592 | no | 2137.4 | 2155.9 | 0.991x |
| 1 | 38593 | no | 2144.4 | 2167.5 | 0.989x |
| 1 | 38656 | no | 2128.0 | 2148.1 | 0.991x |
| 1 | 48768 | no | 2724.4 | 2742.9 | 0.993x |
| 1 | 58944 | no | 3251.2 | 3331.9 | 0.976x |
| 1 | 74240 | no | 4127.7 | 4234.9 | 0.975x |
| 1 | 109952 | no | 6065.8 | 6173.2 | 0.983x |
| 2 | 16736 | no | 930.0 | 934.5 | 0.995x |
| 2 | 19264 | no | 1064.3 | 1063.2 | 1.001x |
| 2 | 19295 | no | 1069.3 | 1070.3 | 0.999x |
| 2 | 19296 | no | 1064.5 | 1063.6 | 1.001x |
| 2 | 19297 | no | 1063.5 | 1065.1 | 0.999x |
| 2 | 19328 | no | 1063.8 | 1065.0 | 0.999x |
| 2 | 24384 | no | 1348.3 | 1349.2 | 0.999x |
| 2 | 29472 | no | 1651.9 | 1663.9 | 0.993x |
| 2 | 37120 | no | 2061.4 | 2102.7 | 0.980x |
| 2 | 54976 | no | 3057.8 | 3131.0 | 0.977x |
| 4 | 8368 | no | 464.7 | 465.6 | 0.998x |
| 4 | 9632 | no | 526.4 | 522.1 | 1.008x |
| 4 | 9647 | no | 522.5 | 524.6 | 0.996x |
| 4 | 9648 | no | 525.3 | 526.4 | 0.998x |
| 4 | 9649 | no | 521.5 | 523.5 | 0.996x |
| 4 | 9664 | no | 524.7 | 522.2 | 1.005x |
| 4 | 12192 | no | 668.0 | 673.5 | 0.992x |
| 4 | 14736 | no | 821.2 | 817.9 | 1.004x |
| 4 | 18560 | no | 1036.2 | 1037.0 | 0.999x |
| 4 | 27488 | no | 1537.9 | 1557.8 | 0.987x |
| 8 | 4184 | no | 243.8 | 243.4 | 1.002x |
| 8 | 4816 | yes | 278.1 | 274.1 | 1.015x |
| 8 | 4823 | yes | 278.0 | 273.1 | 1.018x |
| 8 | 4824 | yes | 280.0 | 274.4 | 1.020x |
| 8 | 4825 | yes | 276.7 | 273.3 | 1.012x |
| 8 | 4832 | yes | 277.9 | 272.9 | 1.018x |
| 8 | 6096 | no | 336.6 | 335.1 | 1.005x |
| 8 | 7368 | yes | 413.4 | 407.6 | 1.014x |
| 8 | 9280 | no | 515.5 | 518.0 | 0.995x |
| 8 | 13744 | no | 754.3 | 742.4 | 1.016x |

MXFP8 (`minimax_h3_out_proj_mxfp8`) on NVIDIA GB300 (`sm_103a`), CUDA
13.4. Time of the complete operator (activation quantization + GEMM),
median of 10 interleaved rounds (5 rounds in each of two sessions) with
a cold L2. P = sequence-parallel degree, M = rows. Rows with tail split
= yes run the new tail schedule. The other rows run the unchanged kernel
in both columns, so their ratio is run-to-run variation.

| P | M | tail split | before (µs) | after (µs) | speedup |
|---:|---:|:---:|---:|---:|---:|
| 1 | 33472 | no | 920.7 | 924.4 | 0.996x |
| 1 | 38528 | no | 1062.9 | 1063.1 | 1.000x |
| 1 | 38591 | no | 1063.5 | 1067.8 | 0.996x |
| 1 | 38592 | no | 1062.7 | 1068.6 | 0.994x |
| 1 | 38593 | no | 1065.5 | 1064.6 | 1.001x |
| 1 | 38656 | no | 1066.5 | 1067.8 | 0.999x |
| 1 | 48768 | no | 1352.6 | 1354.3 | 0.999x |
| 1 | 58944 | no | 1651.6 | 1640.0 | 1.007x |
| 1 | 74240 | no | 2068.2 | 2077.0 | 0.996x |
| 1 | 109952 | no | 3078.5 | 3084.5 | 0.998x |
| 2 | 16736 | yes | 467.0 | 458.7 | 1.018x |
| 2 | 19264 | no | 523.8 | 523.0 | 1.002x |
| 2 | 19295 | no | 521.8 | 522.7 | 0.998x |
| 2 | 19296 | no | 524.4 | 524.2 | 1.000x |
| 2 | 19297 | no | 523.4 | 523.7 | 1.000x |
| 2 | 19328 | no | 524.2 | 524.2 | 1.000x |
| 2 | 24384 | no | 667.1 | 666.3 | 1.001x |
| 2 | 29472 | no | 822.4 | 818.1 | 1.005x |
| 2 | 37120 | no | 1028.0 | 1029.2 | 0.999x |
| 2 | 54976 | no | 1536.3 | 1523.2 | 1.009x |
| 4 | 8368 | yes | 246.8 | 238.8 | 1.033x |
| 4 | 9632 | yes | 270.5 | 264.9 | 1.021x |
| 4 | 9647 | yes | 270.4 | 264.8 | 1.021x |
| 4 | 9648 | yes | 271.1 | 265.8 | 1.020x |
| 4 | 9649 | yes | 269.5 | 264.5 | 1.019x |
| 4 | 9664 | yes | 270.1 | 264.7 | 1.021x |
| 4 | 12192 | yes | 339.2 | 331.9 | 1.022x |
| 4 | 14736 | yes | 413.3 | 404.7 | 1.021x |
| 4 | 18560 | yes | 512.4 | 503.2 | 1.018x |
| 4 | 27488 | no | 750.3 | 750.4 | 1.000x |
| 8 | 4184 | no | 123.7 | 123.8 | 0.999x |
| 8 | 4816 | yes | 145.0 | 137.2 | 1.057x |
| 8 | 4823 | yes | 144.8 | 137.0 | 1.057x |
| 8 | 4824 | yes | 145.0 | 137.6 | 1.053x |
| 8 | 4825 | yes | 144.7 | 136.9 | 1.057x |
| 8 | 4832 | yes | 144.9 | 137.4 | 1.055x |
| 8 | 6096 | no | 171.2 | 171.0 | 1.001x |
| 8 | 7368 | yes | 217.0 | 209.6 | 1.035x |
| 8 | 9280 | yes | 267.5 | 260.9 | 1.025x |
| 8 | 13744 | no | 372.9 | 372.9 | 1.000x |

MXFP8 (`minimax_h3_out_proj_mxfp8`) on NVIDIA GB200 (`sm_100a`), CUDA
13.4. Time of the complete operator (activation quantization + GEMM),
median of 10 interleaved rounds (5 rounds in each of two sessions) with
a cold L2. P = sequence-parallel degree, M = rows. Rows with tail split
= yes run the new tail schedule. The other rows run the unchanged kernel
in both columns, so their ratio is run-to-run variation.

| P | M | tail split | before (µs) | after (µs) | speedup |
|---:|---:|:---:|---:|---:|---:|
| 1 | 33472 | no | 1109.3 | 1110.3 | 0.999x |
| 1 | 38528 | no | 1273.6 | 1286.1 | 0.990x |
| 1 | 38591 | no | 1274.7 | 1273.7 | 1.001x |
| 1 | 38592 | no | 1281.5 | 1278.6 | 1.002x |
| 1 | 38593 | no | 1284.1 | 1273.9 | 1.008x |
| 1 | 38656 | no | 1284.6 | 1284.8 | 1.000x |
| 1 | 48768 | no | 1630.0 | 1632.3 | 0.999x |
| 1 | 58944 | no | 1970.0 | 1979.7 | 0.995x |
| 1 | 74240 | no | 2505.0 | 2503.1 | 1.001x |
| 1 | 109952 | no | 3718.6 | 3761.8 | 0.989x |
| 2 | 16736 | no | 545.3 | 543.2 | 1.004x |
| 2 | 19264 | no | 621.8 | 621.6 | 1.000x |
| 2 | 19295 | no | 624.0 | 621.1 | 1.005x |
| 2 | 19296 | no | 623.5 | 623.8 | 0.999x |
| 2 | 19297 | no | 622.0 | 622.9 | 0.998x |
| 2 | 19328 | no | 621.0 | 622.5 | 0.998x |
| 2 | 24384 | no | 799.5 | 796.6 | 1.004x |
| 2 | 29472 | no | 974.8 | 977.8 | 0.997x |
| 2 | 37120 | no | 1226.7 | 1243.2 | 0.987x |
| 2 | 54976 | no | 1823.8 | 1855.5 | 0.983x |
| 4 | 8368 | yes | 292.3 | 282.6 | 1.034x |
| 4 | 9632 | yes | 324.1 | 316.8 | 1.023x |
| 4 | 9647 | yes | 322.1 | 315.4 | 1.021x |
| 4 | 9648 | yes | 324.9 | 319.0 | 1.019x |
| 4 | 9649 | yes | 319.6 | 314.5 | 1.016x |
| 4 | 9664 | yes | 322.0 | 318.3 | 1.012x |
| 4 | 12192 | yes | 399.1 | 390.5 | 1.022x |
| 4 | 14736 | yes | 482.3 | 473.8 | 1.018x |
| 4 | 18560 | no | 601.5 | 605.5 | 0.993x |
| 4 | 27488 | no | 900.6 | 899.5 | 1.001x |
| 8 | 4184 | no | 149.5 | 149.4 | 1.000x |
| 8 | 4816 | yes | 171.7 | 165.6 | 1.037x |
| 8 | 4823 | yes | 171.6 | 164.6 | 1.043x |
| 8 | 4824 | yes | 173.1 | 166.5 | 1.039x |
| 8 | 4825 | yes | 171.3 | 164.5 | 1.041x |
| 8 | 4832 | yes | 172.2 | 165.8 | 1.039x |
| 8 | 6096 | no | 207.2 | 207.0 | 1.001x |
| 8 | 7368 | yes | 260.0 | 249.8 | 1.040x |
| 8 | 9280 | yes | 315.2 | 310.9 | 1.014x |
| 8 | 13744 | no | 441.3 | 443.9 | 0.994x |

The other variants of this kernel are the NVFP4 SM100/SM103 variant
(`minimax_h3_out_proj_nvfp4`) and the SM120 (`sm_120a`) fused FP8 and
NVFP4 variants `minimax_h3_fp8_out_proj` and
`minimax_h3_nvfp4_out_proj`, which fuse activation quantization into the
GEMM; the family ships on `sm_100a`, `sm_103a` and `sm_120a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded coverage for BF16 and MXFP8 computation schedules, including
additional large and single-row workloads.
* Added checks that compare outputs across the default schedule and
alternative tile-splitting strategies, verifying bitwise-equivalent
results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [563a902](https://github.com/flashinfer-ai/flashinfer/commit/563a9021ad2cf3c7663751b192b4d0ae63795bb8)

- **作者**: eigen
- **时间**: 2026-10-25T22:24:22Z
- **提交信息**: perf(cake_bf16_bmm_swap_ab): tcgen05 swap-AB programs for decode-row bmm_bf16 on SM100/SM103 (#7351)

The Cake backend of `flashinfer.gemm.bmm_bf16` has one input type
(BF16), one layout and three output types (BF16, FP16, FP32). Until now
every shape ran on hand-written mma.sync kernels. This PR adds a tcgen05
swap-AB variant: weight rows fill the MMA's M, decode tokens fill N,
split-K across a cluster is optional, and the FP32 accumulator is
rounded once to the output type. The host routes 9 decode shapes per
architecture to it (K = 1024, M = 8-33, batch 1-4, all three output
types), which run 1.01x-1.20x faster on B200 and 1.03x-1.22x faster on
GB300 than the previous Cake kernel (the same `backend="cake"` call on
the mma.sync kernels).

NVIDIA B200 (sm_100a, CUDA 13.4, driver 580.82.07): GPU kernel time per
call (CUPTI, cold L2), mean of two sessions' medians over 7 interleaved
rounds, speedup = previous / this PR. "unchanged" rows run the same
kernel in both columns, so their 0.99x-1.01x ratios are measurement
spread; "bf16, 2 calls" times two back-to-back calls as one span.

| batch | M | N | K | output | kernel | previous (µs) | this PR (µs) |
speedup |
|---:|---:|---:|---:|---|---|---:|---:|---:|
| 5 | 17 | 24 | 256 | bf16 | unchanged | 2.35 | 2.35 | 1.00x |
| 4 | 128 | 256 | 256 | bf16, 2 calls | unchanged | 24.02 | 24.35 |
0.99x |
| 1 | 8 | 40 | 1024 | f32 | tcgen05 swap-AB | 3.38 | 2.94 | 1.15x |
| 2 | 33 | 1032 | 1024 | bf16 | tcgen05 swap-AB | 5.50 | 4.59 | 1.20x |
| 3 | 8 | 8 | 64 | bf16 | unchanged | 2.03 | 2.03 | 1.00x |
| 5 | 17 | 24 | 256 | f32 | unchanged | 2.35 | 2.37 | 0.99x |
| 7 | 130 | 72 | 64 | f16 | unchanged | 2.13 | 2.13 | 1.00x |
| 1 | 16 | 64 | 1024 | f16 | tcgen05 swap-AB | 3.42 | 2.88 | 1.19x |
| 2 | 8 | 1024 | 1024 | f16 | tcgen05 swap-AB | 4.29 | 3.95 | 1.09x |
| 2 | 8 | 1024 | 1024 | f32 | tcgen05 swap-AB | 4.19 | 3.90 | 1.07x |
| 4 | 16 | 1024 | 1024 | f16 | tcgen05 swap-AB | 5.06 | 4.88 | 1.04x |
| 4 | 16 | 1024 | 1024 | f32 | tcgen05 swap-AB | 5.06 | 4.90 | 1.03x |
| 16 | 128 | 64 | 256 | bf16 | unchanged | 2.88 | 2.88 | 1.00x |
| 16 | 128 | 64 | 256 | f16 | unchanged | 2.91 | 2.91 | 1.00x |
| 16 | 128 | 64 | 256 | f32 | unchanged | 2.90 | 2.90 | 1.00x |
| 16 | 128 | 64 | 64 | bf16 | unchanged | 2.18 | 2.19 | 0.99x |
| 16 | 128 | 64 | 64 | f16 | unchanged | 2.16 | 2.16 | 1.00x |
| 16 | 128 | 64 | 64 | f32 | unchanged | 2.19 | 2.18 | 1.01x |
| 16 | 128 | 80 | 256 | bf16 | unchanged | 3.01 | 3.01 | 1.00x |
| 16 | 128 | 80 | 256 | f16 | unchanged | 3.01 | 3.01 | 1.00x |
| 16 | 128 | 80 | 256 | f32 | unchanged | 3.06 | 3.06 | 1.00x |
| 16 | 128 | 80 | 64 | bf16 | unchanged | 2.19 | 2.19 | 1.00x |
| 16 | 128 | 80 | 64 | f16 | unchanged | 2.24 | 2.24 | 1.00x |
| 16 | 128 | 80 | 64 | f32 | unchanged | 2.24 | 2.24 | 1.00x |
| 16 | 48 | 64 | 256 | bf16 | unchanged | 2.54 | 2.54 | 1.00x |
| 16 | 48 | 64 | 256 | f16 | unchanged | 2.53 | 2.54 | 0.99x |
| 16 | 48 | 64 | 256 | f32 | unchanged | 2.53 | 2.51 | 1.01x |
| 16 | 48 | 64 | 64 | bf16 | unchanged | 2.08 | 2.07 | 1.00x |
| 16 | 48 | 64 | 64 | f16 | unchanged | 2.10 | 2.10 | 1.00x |
| 16 | 48 | 64 | 64 | f32 | unchanged | 2.05 | 2.05 | 1.00x |
| 16 | 48 | 80 | 256 | bf16 | unchanged | 2.53 | 2.53 | 1.00x |
| 16 | 48 | 80 | 256 | f16 | unchanged | 2.56 | 2.56 | 1.00x |
| 16 | 48 | 80 | 256 | f32 | unchanged | 2.58 | 2.58 | 1.00x |
| 16 | 48 | 80 | 64 | bf16 | unchanged | 2.10 | 2.10 | 1.00x |
| 16 | 48 | 80 | 64 | f16 | unchanged | 2.10 | 2.10 | 1.00x |
| 16 | 48 | 80 | 64 | f32 | unchanged | 2.13 | 2.14 | 0.99x |
| 1 | 128 | 64 | 256 | bf16 | unchanged | 2.27 | 2.27 | 1.00x |
| 1 | 128 | 64 | 256 | f16 | unchanged | 2.26 | 2.26 | 1.00x |
| 1 | 128 | 64 | 256 | f32 | unchanged | 2.26 | 2.27 | 0.99x |
| 1 | 128 | 64 | 64 | bf16 | unchanged | 1.94 | 1.94 | 1.00x |
| 1 | 128 | 64 | 64 | f16 | unchanged | 1.87 | 1.86 | 1.01x |
| 1 | 128 | 64 | 64 | f32 | unchanged | 1.92 | 1.92 | 1.00x |
| 1 | 128 | 80 | 256 | bf16 | unchanged | 2.18 | 2.16 | 1.01x |
| 1 | 128 | 80 | 256 | f16 | unchanged | 2.18 | 2.18 | 1.00x |
| 1 | 128 | 80 | 256 | f32 | unchanged | 2.19 | 2.18 | 1.01x |
| 1 | 128 | 80 | 64 | bf16 | unchanged | 1.82 | 1.82 | 1.00x |
| 1 | 128 | 80 | 64 | f16 | unchanged | 1.86 | 1.84 | 1.01x |
| 1 | 128 | 80 | 64 | f32 | unchanged | 1.86 | 1.86 | 1.00x |
| 1 | 48 | 64 | 256 | bf16 | unchanged | 2.16 | 2.16 | 1.00x |
| 1 | 48 | 64 | 256 | f16 | unchanged | 2.18 | 2.18 | 1.00x |
| 1 | 48 | 64 | 256 | f32 | unchanged | 2.14 | 2.14 | 1.00x |
| 1 | 48 | 64 | 64 | bf16 | unchanged | 1.79 | 1.79 | 1.00x |
| 1 | 48 | 64 | 64 | f16 | unchanged | 1.81 | 1.81 | 1.00x |
| 1 | 48 | 64 | 64 | f32 | unchanged | 1.81 | 1.81 | 1.00x |
| 1 | 48 | 80 | 256 | bf16 | unchanged | 2.10 | 2.10 | 1.00x |
| 1 | 48 | 80 | 256 | f16 | unchanged | 2.14 | 2.14 | 1.00x |
| 1 | 48 | 80 | 256 | f32 | unchanged | 2.13 | 2.13 | 1.00x |
| 1 | 48 | 80 | 64 | bf16 | unchanged | 1.78 | 1.78 | 1.00x |
| 1 | 48 | 80 | 64 | f16 | unchanged | 1.79 | 1.79 | 1.00x |
| 1 | 48 | 80 | 64 | f32 | unchanged | 1.81 | 1.81 | 1.00x |
| 2 | 8 | 1024 | 1024 | bf16 | tcgen05 swap-AB | 3.92 | 3.89 | 1.01x |
| 4 | 16 | 1024 | 1024 | bf16 | tcgen05 swap-AB | 5.10 | 4.90 | 1.04x |

NVIDIA GB300 (sm_103a, CUDA 13.4, driver 580.159.03), same method;
"unchanged" rows again stay within 0.99x-1.01x.

| batch | M | N | K | output | kernel | previous (µs) | this PR (µs) |
speedup |
|---:|---:|---:|---:|---|---|---:|---:|---:|
| 5 | 17 | 24 | 256 | bf16 | unchanged | 2.29 | 2.29 | 1.00x |
| 4 | 128 | 256 | 256 | bf16, 2 calls | unchanged | 36.64 | 36.80 |
1.00x |
| 1 | 8 | 40 | 1024 | f32 | tcgen05 swap-AB | 3.23 | 2.74 | 1.18x |
| 2 | 33 | 1032 | 1024 | bf16 | tcgen05 swap-AB | 5.15 | 4.22 | 1.22x |
| 3 | 8 | 8 | 64 | bf16 | unchanged | 1.95 | 1.97 | 0.99x |
| 5 | 17 | 24 | 256 | f32 | unchanged | 2.30 | 2.30 | 1.00x |
| 7 | 130 | 72 | 64 | f16 | unchanged | 2.08 | 2.06 | 1.01x |
| 1 | 16 | 64 | 1024 | f16 | tcgen05 swap-AB | 3.30 | 2.77 | 1.19x |
| 2 | 8 | 1024 | 1024 | f16 | tcgen05 swap-AB | 3.94 | 3.60 | 1.09x |
| 2 | 8 | 1024 | 1024 | f32 | tcgen05 swap-AB | 4.03 | 3.73 | 1.08x |
| 4 | 16 | 1024 | 1024 | f16 | tcgen05 swap-AB | 4.82 | 4.64 | 1.04x |
| 4 | 16 | 1024 | 1024 | f32 | tcgen05 swap-AB | 4.85 | 4.70 | 1.03x |
| 16 | 128 | 64 | 256 | bf16 | unchanged | 2.80 | 2.80 | 1.00x |
| 16 | 128 | 64 | 256 | f16 | unchanged | 2.80 | 2.80 | 1.00x |
| 16 | 128 | 64 | 256 | f32 | unchanged | 2.77 | 2.77 | 1.00x |
| 16 | 128 | 64 | 64 | bf16 | unchanged | 2.08 | 2.08 | 1.00x |
| 16 | 128 | 64 | 64 | f16 | unchanged | 2.08 | 2.08 | 1.00x |
| 16 | 128 | 64 | 64 | f32 | unchanged | 2.14 | 2.13 | 1.01x |
| 16 | 128 | 80 | 256 | bf16 | unchanged | 2.88 | 2.88 | 1.00x |
| 16 | 128 | 80 | 256 | f16 | unchanged | 2.93 | 2.93 | 1.00x |
| 16 | 128 | 80 | 256 | f32 | unchanged | 2.91 | 2.91 | 1.00x |
| 16 | 128 | 80 | 64 | bf16 | unchanged | 2.13 | 2.13 | 1.00x |
| 16 | 128 | 80 | 64 | f16 | unchanged | 2.18 | 2.16 | 1.01x |
| 16 | 128 | 80 | 64 | f32 | unchanged | 2.19 | 2.19 | 1.00x |
| 16 | 48 | 64 | 256 | bf16 | unchanged | 2.40 | 2.42 | 0.99x |
| 16 | 48 | 64 | 256 | f16 | unchanged | 2.43 | 2.45 | 0.99x |
| 16 | 48 | 64 | 256 | f32 | unchanged | 2.42 | 2.42 | 1.00x |
| 16 | 48 | 64 | 64 | bf16 | unchanged | 2.00 | 2.00 | 1.00x |
| 16 | 48 | 64 | 64 | f16 | unchanged | 2.03 | 2.03 | 1.00x |
| 16 | 48 | 64 | 64 | f32 | unchanged | 1.98 | 1.98 | 1.00x |
| 16 | 48 | 80 | 256 | bf16 | unchanged | 2.46 | 2.46 | 1.00x |
| 16 | 48 | 80 | 256 | f16 | unchanged | 2.45 | 2.45 | 1.00x |
| 16 | 48 | 80 | 256 | f32 | unchanged | 2.46 | 2.45 | 1.01x |
| 16 | 48 | 80 | 64 | bf16 | unchanged | 1.98 | 2.00 | 0.99x |
| 16 | 48 | 80 | 64 | f16 | unchanged | 2.03 | 2.03 | 1.00x |
| 16 | 48 | 80 | 64 | f32 | unchanged | 2.03 | 2.05 | 0.99x |
| 1 | 128 | 64 | 256 | bf16 | unchanged | 2.14 | 2.14 | 1.00x |
| 1 | 128 | 64 | 256 | f16 | unchanged | 2.16 | 2.18 | 0.99x |
| 1 | 128 | 64 | 256 | f32 | unchanged | 2.16 | 2.16 | 1.00x |
| 1 | 128 | 64 | 64 | bf16 | unchanged | 1.84 | 1.84 | 1.00x |
| 1 | 128 | 64 | 64 | f16 | unchanged | 1.79 | 1.79 | 1.00x |
| 1 | 128 | 64 | 64 | f32 | unchanged | 1.87 | 1.87 | 1.00x |
| 1 | 128 | 80 | 256 | bf16 | unchanged | 2.11 | 2.11 | 1.00x |
| 1 | 128 | 80 | 256 | f16 | unchanged | 2.18 | 2.16 | 1.01x |
| 1 | 128 | 80 | 256 | f32 | unchanged | 2.16 | 2.16 | 1.00x |
| 1 | 128 | 80 | 64 | bf16 | unchanged | 1.78 | 1.78 | 1.00x |
| 1 | 128 | 80 | 64 | f16 | unchanged | 1.79 | 1.79 | 1.00x |
| 1 | 128 | 80 | 64 | f32 | unchanged | 1.81 | 1.81 | 1.00x |
| 1 | 48 | 64 | 256 | bf16 | unchanged | 2.05 | 2.05 | 1.00x |
| 1 | 48 | 64 | 256 | f16 | unchanged | 2.08 | 2.10 | 0.99x |
| 1 | 48 | 64 | 256 | f32 | unchanged | 2.08 | 2.08 | 1.00x |
| 1 | 48 | 64 | 64 | bf16 | unchanged | 1.73 | 1.73 | 1.00x |
| 1 | 48 | 64 | 64 | f16 | unchanged | 1.76 | 1.74 | 1.01x |
| 1 | 48 | 64 | 64 | f32 | unchanged | 1.73 | 1.73 | 1.00x |
| 1 | 48 | 80 | 256 | bf16 | unchanged | 2.05 | 2.05 | 1.00x |
| 1 | 48 | 80 | 256 | f16 | unchanged | 2.08 | 2.08 | 1.00x |
| 1 | 48 | 80 | 256 | f32 | unchanged | 2.06 | 2.06 | 1.00x |
| 1 | 48 | 80 | 64 | bf16 | unchanged | 1.71 | 1.71 | 1.00x |
| 1 | 48 | 80 | 64 | f16 | unchanged | 1.74 | 1.74 | 1.00x |
| 1 | 48 | 80 | 64 | f32 | unchanged | 1.76 | 1.76 | 1.00x |
| 2 | 8 | 1024 | 1024 | bf16 | tcgen05 swap-AB | 3.81 | 3.71 | 1.03x |
| 4 | 16 | 1024 | 1024 | bf16 | tcgen05 swap-AB | 4.86 | 4.70 | 1.03x |

Cake ships no other variant of this kernel beyond those mma.sync
kernels, which keep serving every non-routed shape; the family ships on
sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added generated BF16 batched matrix multiplication routes for selected
shapes on supported SM100a and SM103a GPUs.
* Eligible calls using the CAKE backend can use these routes when tensor
layouts and alignment meet requirements. Other calls continue through
the existing dispatcher.
  * Added ahead-of-time compilation support for the new routes.
* Added an environment variable to keep CAKE calls on the existing
dispatcher instead of selecting the generated routes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b41ed3f](https://github.com/flashinfer-ai/flashinfer/commit/b41ed3f4cb8d0094d0ca9aa2a1c6c32987746c26)

- **作者**: Yang Xu
- **时间**: 2026-10-25T22:20:23Z
- **提交信息**: docs: correct managed autotune cache examples (#7164)

<!-- .github/pull_request_template.md -->

## 📌 Description

The managed-cache quickstart tuned with `execution_mode="cuda_graph"`
but omitted that policy when attaching in a fresh process. Because the
policy is part of the store identity, copying the example would select
the default-policy store and miss the graph-tuned entries.

Pass the same policy in both contexts and explain how the default
process attachment serves later bare calls. Also correct the module
overview's cache placement argument from `root` to the actual
`cache_root` keyword.

## 🔍 Related Issues

Related to #3920 and the SGLang policy-aware cache integration
discussion.

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

- [x] Tests have been added or updated as needed. Existing coverage
applies; no new test for this documentation correction.
- [x] All relevant tests pass:
`test_measure_policy_isolates_store_identity` and
`test_measure_policy_attach_carries_to_serving` — **2 passed** with an
A100 visible. An initial run hiding CUDA devices failed at the existing
stream-capture query; no source change was needed.

Validation: changed-file pre-commit hooks; `git diff --check`; the
Python module AST is identical after excluding its leading docstring.

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

Documentation only; no runtime or API changes. The existing
`test_measure_policy_attach_carries_to_serving` already covers both
matching-policy reuse and the omitted-policy miss.

Self-review: checked the example against the current store identity and
process attachment implementation. Changed-file pre-commit hooks and
`git diff --check` passed; hooks were not installed or run over
unrelated files.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Updated the tuning and replay example to use the same measurement
policy, including when replaying in a fresh process.
* Clarified that the measurement policy affects managed-cache identity,
and that bare serving after the context exits uses the attached store
under the default process scope.
  * Updated the documented cache-root keyword to `cache_root`.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f83439d](https://github.com/flashinfer-ai/flashinfer/commit/f83439d2a6e3cc9572d6900e86d80c7982a8988f)

- **作者**: eigen
- **时间**: 2026-10-25T22:04:04Z
- **提交信息**: feat(cake_nvfp4_attention): add Cake NVFP4 attention for SM100, SM103 and SM120 (#7362)

This Cake attention kernel comes in three variants. All three do dense
non-causal MHA with D = 128, take BF16 in and give BF16 out, use FP32
softmax and accept any strides (NHD or HND views). Each variant is one
call that runs a chain of statistics, quantization and attention
kernels, and it smooths and quantizes the inputs on the GPU on every
call. The variants are NVFP4 QK + NVFP4 PV on SM100 / SM103 (four
kernels), INT8 QK + NVFP4 PV on SM120 (three kernels) and INT8 QK + FP8
E4M3 PV on SM90 (four kernels). This PR delivers the first two as
`flashinfer/experimental/nvfp4_attention` (sm_100a, sm_103a, sm_120a),
replacing the previously shipped program of that package (SM103 only,
`S` divisible by 512, inputs quantized on the host) behind the same
call, through `flashinfer.prefill.prepare_nvfp4_attention(q, k, v, out,
backend="cake")` and `nvfp4_attention_workspace_bytes`. We measured the
complete BF16-in / BF16-out call (statistics + quantization + attention
under CUDA-graph replay) against the baseline's complete call. Against
FlashAttention-4 BF16, it is 1.01x–1.06x faster on B200 and 1.03x–1.08x
faster on GB300 for R2–R7, and 0.72x and 0.70x on R1. Against PyTorch
SDPA (cuDNN backend) BF16 on RTX PRO 6000 Blackwell Server Edition, it
is 1.41x–1.84x faster across R1–R7.

**NVIDIA B200 (sm_100a), CUDA 13.0 runtime, kernels JIT-compiled with
CUDA 13.4: Cake vs FlashAttention-4 BF16, D = 128**

| Shape | Batch | Seq len | Heads | Cake (ms) | FlashAttention-4 BF16
(ms) | Speedup (baseline / Cake) |
|---|---:|---:|---:|---:|---:|---:|
| R1 | 1 | 4800 | 40 | 0.4940 | 0.3534 | 0.72x |
| R2 | 1 | 32760 | 40 | 16.0399 | 16.4005 | 1.02x |
| R3 | 1 | 75600 | 40 | 84.5186 | 87.0277 | 1.03x |
| R4 | 1 | 32760 | 5 | 1.9515 | 2.0763 | 1.06x |
| R5 | 1 | 75600 | 5 | 10.4680 | 10.8258 | 1.03x |
| R6 | 2 | 32760 | 40 | 32.4710 | 32.8883 | 1.01x |
| R7 | 1 | 32760 | 12 | 4.8390 | 5.0445 | 1.04x |

**NVIDIA GB300 (sm_103a), CUDA 13.0 runtime, kernels JIT-compiled with
CUDA 13.4: Cake vs FlashAttention-4 BF16, D = 128**

| Shape | Batch | Seq len | Heads | Cake (ms) | FlashAttention-4 BF16
(ms) | Speedup (baseline / Cake) |
|---|---:|---:|---:|---:|---:|---:|
| R1 | 1 | 4800 | 40 | 0.3923 | 0.2743 | 0.70x |
| R2 | 1 | 32760 | 40 | 11.1800 | 11.8955 | 1.06x |
| R3 | 1 | 75600 | 40 | 58.4486 | 62.9903 | 1.08x |
| R4 | 1 | 32760 | 5 | 1.4460 | 1.4919 | 1.03x |
| R5 | 1 | 75600 | 5 | 7.3968 | 7.9395 | 1.07x |
| R6 | 2 | 32760 | 40 | 22.3310 | 23.9050 | 1.07x |
| R7 | 1 | 32760 | 12 | 3.3869 | 3.5245 | 1.04x |

**NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120a), CUDA 13.0
runtime, kernels JIT-compiled with CUDA 13.4: Cake vs PyTorch SDPA
(cuDNN backend) BF16, D = 128**

| Shape | Batch | Seq len | Heads | Cake (ms) | PyTorch SDPA (cuDNN)
BF16 (ms) | Speedup (baseline / Cake) |
|---|---:|---:|---:|---:|---:|---:|
| R1 | 1 | 4800 | 40 | 1.0082 | 1.4242 | 1.41x |
| R2 | 1 | 32760 | 40 | 33.2754 | 59.6590 | 1.79x |
| R3 | 1 | 75600 | 40 | 172.0325 | 315.4792 | 1.83x |
| R4 | 1 | 32760 | 5 | 4.1421 | 7.5130 | 1.81x |
| R5 | 1 | 75600 | 5 | 21.5641 | 39.7563 | 1.84x |
| R6 | 2 | 32760 | 40 | 66.7597 | 119.1982 | 1.79x |
| R7 | 1 | 32760 | 12 | 10.1126 | 18.1876 | 1.80x |

The other Cake variant of this attention is INT8 QK + FP8 E4M3 PV on
SM90 (`flashinfer/experimental/cake_fp8_attention`, delivered in a
companion PR), and the family ships on sm_90a, sm_100a, sm_103a and
sm_120a.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9e016bd](https://github.com/flashinfer-ai/flashinfer/commit/9e016bdfc39624c1659a10d60ed8c9af4c3cea61)

- **作者**: eigen
- **时间**: 2026-10-25T21:48:51Z
- **提交信息**: perf(cake_softmax): per-tile turnover ring for the Blackwell persistent softmax (#7359)

`flashinfer.sampling.softmax` on Blackwell (`cake_blackwell_softmax`)
has one data type (FP32) and one layout (row-major `[rows, vocab]`). It
can fuse a scalar or per-row temperature, and it can use PDL on sm_103a.
As before, 14 Cake programs serve it: a warp program, a rowwise program,
a bootstrap program, 7 row-caching cluster programs (1- to 16-CTA
clusters x 4 or 8 tiles), 2 shared-tile programs (8- and 16-CTA
clusters) and 2 persistent programs (8- and 16-CTA clusters, 8 tiles).
This PR changes the persistent programs, the row-caching cluster
programs, the shared-tile programs and the dispatcher. In the 2
persistent programs, each CTA writes row i one tile at a time. Right
after each tile's store, it reads the next row's copy of that tile into
the same registers. The stores drain while the next row is read, and the
CTA-wide barrier before the next row's copies is gone. On sm_100a, a
16-CTA cluster that walks more than 24 rows refills its buffer one row
at a time instead. Over a long walk on B200, the tile-at-a-time copies
fall behind a row burst. The 7 row-caching cluster programs, the 2
shared-tile programs and the persistent programs now take the warp max
with `redux.sync` instead of a shuffle tree. Above one wave of
persistent clusters, the dispatcher sends more full-chunk (8-tile) rows
to the persistent programs and keeps the shared-tile programs for the
widest batches. The baseline is the previous Cake version in FlashInfer
main (`847172573`, which includes #7308). Against it, the geometric-mean
speedup across the 41 shapes below is 1.047x on B200 and 1.042x on
GB300. Shapes that moved to or stay on the persistent programs gain the
most. The largest gains are 1.246x on B200 and 1.197x on GB300, both at
128 × 128000. Other examples on B200 / GB300 are 64 × 256000 (1.203x /
1.165x), 128 × 256000 (1.170x / 1.178x), 64 × 128000 (1.145x / 1.096x)
and 256 × 128000 (1.102x / 1.102x). The row-caching cluster shapes gain
up to 6 % from the warp max, for example 1 × 32000 at 1.053x / 1.049x.
Five results land between 0.996x and 0.999x, which is within the run's
measurement noise: 8 × 256000 on B200, 512 × 256000 and 1024 × 128000 on
GB300, and 1024 × 256000 on both.

Latency in microseconds (median, cold L2), previous Cake version (main
`847172573`) vs this PR, on B200 (sm_100a) and GB300 (sm_103a); CUDA
13.4 (nvcc 13.4.2), PyTorch 2.14.1+cu130.

| rows × vocab | B200 previous (µs) | B200 this PR (µs) | B200 speedup |
GB300 previous (µs) | GB300 this PR (µs) | GB300 speedup |
|---|---:|---:|---:|---:|---:|---:|
| 1 × 32000 | 2.53 | 2.40 | 1.053× | 2.40 | 2.27 | 1.049× |
| 1 × 64000 | 2.91 | 2.78 | 1.046× | 2.77 | 2.64 | 1.045× |
| 1 × 128000 | 3.41 | 3.28 | 1.040× | 3.18 | 3.06 | 1.042× |
| 1 × 256000 | 4.54 | 4.42 | 1.029× | 4.18 | 4.06 | 1.030× |
| 4 × 32000 | 2.75 | 2.62 | 1.049× | 2.56 | 2.45 | 1.052× |
| 4 × 64000 | 3.06 | 2.93 | 1.044× | 2.78 | 2.66 | 1.048× |
| 4 × 128000 | 3.63 | 3.47 | 1.039× | 3.31 | 3.20 | 1.037× |
| 4 × 256000 | 4.94 | 4.82 | 1.027× | 4.59 | 4.46 | 1.029× |
| 8 × 32000 | 2.85 | 2.72 | 1.049× | 2.77 | 2.62 | 1.052× |
| 8 × 64000 | 3.39 | 3.25 | 1.042× | 3.18 | 3.04 | 1.047× |
| 8 × 128000 | 4.50 | 4.29 | 1.045× | 4.19 | 4.06 | 1.031× |
| 8 × 256000 | 6.91 | 6.94 | 0.996× | 6.37 | 6.22 | 1.021× |
| 16 × 32000 | 3.17 | 3.01 | 1.053× | 2.99 | 2.85 | 1.050× |
| 16 × 64000 | 3.92 | 3.76 | 1.044× | 3.71 | 3.55 | 1.045× |
| 16 × 128000 | 5.76 | 5.70 | 1.011× | 5.34 | 5.20 | 1.029× |
| 16 × 256000 | 9.82 | 9.60 | 1.023× | 9.28 | 9.18 | 1.010× |
| 32 × 32000 | 4.94 | 4.66 | 1.064× | 3.54 | 3.36 | 1.050× |
| 32 × 64000 | 5.79 | 5.68 | 1.018× | 4.80 | 4.62 | 1.036× |
| 32 × 128000 | 7.79 | 7.66 | 1.016× | 7.34 | 7.28 | 1.009× |
| 32 × 256000 | 15.09 | 13.15 | 1.150× | 12.96 | 12.85 | 1.009× |
| 64 × 32000 | 4.85 | 4.69 | 1.034× | 4.69 | 4.54 | 1.032× |
| 64 × 64000 | 7.36 | 7.23 | 1.017× | 7.17 | 7.06 | 1.018× |
| 64 × 128000 | 13.47 | 11.76 | 1.145× | 12.69 | 11.58 | 1.096× |
| 64 × 256000 | 24.90 | 20.67 | 1.203× | 23.70 | 20.35 | 1.165× |
| 128 × 32000 | 7.18 | 7.04 | 1.020× | 6.93 | 6.82 | 1.016× |
| 128 × 64000 | 11.68 | 11.28 | 1.035× | 11.42 | 11.10 | 1.027× |
| 128 × 128000 | 22.54 | 18.08 | 1.246× | 21.33 | 17.82 | 1.197× |
| 128 × 256000 | 42.02 | 35.92 | 1.170× | 41.63 | 35.25 | 1.178× |
| 256 × 32000 | 11.10 | 10.90 | 1.019× | 11.10 | 10.83 | 1.024× |
| 256 × 64000 | 19.66 | 18.96 | 1.036× | 18.93 | 18.45 | 1.026× |
| 256 × 128000 | 39.66 | 36.00 | 1.102× | 36.88 | 33.47 | 1.102× |
| 256 × 256000 | 78.84 | 78.45 | 1.005× | 76.30 | 74.12 | 1.029× |
| 512 × 32000 | 18.74 | 18.16 | 1.032× | 18.11 | 17.74 | 1.021× |
| 512 × 64000 | 37.15 | 36.13 | 1.029× | 35.86 | 35.20 | 1.019× |
| 512 × 128000 | 76.77 | 76.70 | 1.001× | 74.22 | 72.84 | 1.019× |
| 512 × 256000 | 152.05 | 151.90 | 1.001× | 148.74 | 148.88 | 0.999× |
| 1024 × 32000 | 35.81 | 35.23 | 1.017× | 34.64 | 34.29 | 1.011× |
| 1024 × 64000 | 73.07 | 72.54 | 1.007× | 71.78 | 71.44 | 1.005× |
| 1024 × 128000 | 151.29 | 151.25 | 1.000× | 147.09 | 147.30 | 0.998× |
| 1024 × 256000 | 299.88 | 300.18 | 0.999× | 293.94 | 294.16 | 0.999× |
| 64 × 32000 (scalar temperature, PDL) | 4.86 | 4.70 | 1.034× | 4.67 |
4.51 | 1.035× |
| geometric mean | | | 1.047× | | | 1.042× |

The family's other Cake programs are the warp, rowwise and bootstrap
programs, which this PR leaves unchanged, and the whole family ships on
sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved Blackwell GPU softmax execution across a wider range of input
sizes, with kernel selection better adapted to workload shape and
hardware.
* Updated reduction operations across cached-cluster kernel variants
while retaining their existing softmax calculations and cluster exchange
behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [62c2ada](https://github.com/flashinfer-ai/flashinfer/commit/62c2ada6a5ef277acdd1d744016b335bb9f3f235)

- **作者**: eigen
- **时间**: 2026-10-25T21:47:14Z
- **提交信息**: fix(cake_kda): N16 aux hand-off barriers on a one-owner ring of ten slots (#7358)

## Summary

The FlashKDA N16 bodies behind `recurrent_kda(backend="cake")` and three
prepared-path BF16 bodies (`prepare_bf16_kda_prefill`) can deadlock the
CTA or return wrong output when one (sequence, head) has 6 or more
chunks of 16 tokens. On unmodified inputs the failure is intermittent.
This PR fixes the auxiliary hand-off protocol in every affected body. It
also fixes a launch-argument bug that stopped the static m128_n16 path
from building.

## Problem

In these bodies, two auxiliary MMA warps take turns handling chunks. The
three hand-off barriers between the preparation and auxiliary roles
(`aux_pairwise_inputs_ready`, `aux_pairwise_consumed`,
`aux_inverse_ready`) were indexed on the 5-stage chunk ring. Because
that ring has an odd number of stages, two consecutive uses of the same
stage belong to different warps. A parity wait can therefore pass one
lap early, which either deadlocks the CTA or produces wrong output.

These code paths reach the bug:

- **Generated N16 modules** (`flashkda_generated_bf16_fused_m128_*`):
reached by prefill for inputs with 6 or more chunks of 16 tokens per
(sequence, head).
- **Static `m128_n16` and `m128_n16_checkpoint` bodies**: used only
after a generated-selector miss.
- **Prepared path**:
- `cake_kda_bf16_51e813006f17147a02a5` and
`cake_kda_bf16_b7a36d7e13872a35abe8` reach N16 naturally in the tested
64-chunk shapes.
- `cake_kda_bf16_3bd0815de00cd1122604` goes to N16 only for up to 4
chunks; longer inputs go to N32. In production the defect is latent
there, but a test-only route pin reproduces it in the body.

The generated `ac3225bbea` body (one auxiliary warp) and
`m128_n16_short` (one chunk) are not affected and are unchanged.

Separately, `cake_flashkda_bf16_fused_m128_n16_binding.cu` passed a
trailing `nullptr` that `kernel_flashkda_bf16_fused_m128` does not take.
nvcc fails with "too many arguments in function call", so the static
m128_n16 module did not build on either architecture.

## Fix

- The three hand-off barriers move to their own ring of ten slots,
addressed by chunk index: slot `chunk % 10`, parity `chunk / 10 % 2`.
Each slot now has a single owner warp. The two roles no longer track
phase variables for these barriers.
- Shared-memory data stays on the 5-stage chunk ring. The new barriers
use previously unused bytes below the 1024-byte data start, so the
shared-memory size does not change. For the prepared-path bodies, ptxas
reports the same registers (64), stack and spills before and after.
- The same minimal edit is applied to all affected bodies: the 9
FlashKDA N16 files (2 static, 7 generated) and the 3 bodies in
`csrc/kda/bf16/`.
- The binding drops the extra `nullptr`, so the static m128_n16 path
builds and runs.

## Testing

All tests ran on B200 (sm_100a) and GB300 (sm_103a).

- **Normal path:** output, final state and checkpoint rows are bitwise
equal to main for all 9 N16 cases and all 9 prepared-path cases, with
identical results across 4 launches. The static m128_n16 path now builds
without a workaround and gives the same output as the tested body.
- **Injected delay** (test-only spin in one preparation warp): main
hangs at the first launch or returns wrong output in every affected
case. The fixed bodies complete all 10 launches and match the clean run
bitwise. A 4-chunk control does not hang on either version.
- **Back-to-back launches:** the fixed bodies had 0 hangs and 0
mismatches over 200,000 launches in each N16 case and 1,000,000 launches
in each of 4 prepared-path cases. Without any injection, main hung in 1
N16 case on B200, in 2 on GB300, and in 1 prepared-path case on GB300
(at launch 251648).
- **compute-sanitizer and tests:** memcheck and synccheck report 0
errors on the fixed bodies. For the N16 bodies, racecheck reports the
same records as main (they already exist on main, and none are new). For
the prepared-path bodies, racecheck reports 0 hazards on both versions.
The KDA tests (`tests/kda`) pass with 0 failures on both GPUs.

No existing FlashInfer test loads the `b7a36d7e` or `3bd0815` modules.
Their only coverage is the standalone repro above.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Improvements**
- Updated BF16 KDA processing to coordinate auxiliary work across longer
sequences of chunks. This provides a more consistent handoff between
processing stages while retaining the existing five-stage data flow.
- Applied the synchronization update across the supported fused and
checkpointed BF16 kernel variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7dbb267](https://github.com/flashinfer-ai/flashinfer/commit/7dbb267ae89d9c2f6586ded623ad9d10f5f8a303)

- **作者**: eigen
- **时间**: 2026-10-25T21:31:39Z
- **提交信息**: perf(cake_dense_projection_gemm): paced output-store programs for the SM103a 5120-column input-gradient rows (#7361)

The Cake `dense_projection_gemm` kernel takes BF16 inputs with FP32
accumulation and writes BF16 or FP32 output for the fwd, dgrad and wgrad
GEMMs in the nn / kn / kk operand layouts. It has 117 dense templates:
79 with BF16 output and 38 with FP32 output; 55 nn, 42 kn, 19 kk and one
nk; 28 of them write a transposed output. The templates differ in tile
shape (64-, 128- and 256-row tiles at 128–256 columns), epilogue,
raster, stream-K tail handling and fused forms such as the pipelined
chunked TMEM drain and the whole-tile tile resolve. The kernel also has
an FP32 router GEMM that uses split-BF16x3 tensor-core emulation in 3
layouts (kk / kn / nn_t) with a fused split program, for 124 registered
programs (121 distinct templates) in all. This PR delivers two new
sm_103a programs for the BF16-output input-gradient (dgrad) GEMM in the
K-major (kn) layout. Both use the 128x256 CTA-pair tile with the
TMA-store epilogue and the pipelined chunked TMEM drain, and both add
paced output stores: each epilogue warp delays the issue of its bulk
tensor stores by a per-warp number of short dependent-arithmetic steps,
which turns the per-item burst of eight stores into a ramp while the
stores and their bytes stay unchanged. One program combines the pacing
with the whole-tile tile resolve from the previous PR and is selected
for 5120→512; the other leaves out the tile resolve and is selected for
5120→1024. The baseline is the previous Cake version of the kernel,
meaning the programs the planner selected for the same shapes before
this PR (the same programs without the paced output stores). Against it,
the speedup is 1.027 / 1.029 on 5120→512 and 1.012 / 1.009 on 5120→1024
at T = 16231 / 16384. The table lists every shape of the owner's shape
list (294 rows). Only the four BF16-output dgrad rows of 5120→512 and
5120→1024 change program; every other row keeps its previous program,
and no other row's plan changes on any architecture.

**NVIDIA GB300 (sm_103a), driver 580.159.03, CUDA 13.4 (nvcc 13.4.92);
node nvl72d213-T18. Cold-L2 CUPTI kernel time, median of 5 alternating
groups × [20] iterations, both sides in the same session. Latency in µs;
speedup = previous version / this PR.**

| shape (K→N) | op | out | T | baseline | baseline µs | this PR µs |
speedup |
|---|---|---|---:|---|---:|---:|---:|
| indexer_q (2048→4096) | dgrad | bf16 | 16172 | previous version |
139.7 | 139.6 | 1.001 |
| indexer_q (2048→4096) | dgrad | bf16 | 16231 | previous version |
139.5 | 139.0 | 1.004 |
| indexer_q (2048→4096) | fwd | bf16 | 16172 | previous version | 135.1
| 135.2 | 1.000 |
| indexer_q (2048→4096) | fwd | bf16 | 16231 | previous version | 135.8
| 135.7 | 1.000 |
| indexer_q (2048→4096) | wgrad | bf16 | 16172 | previous version |
144.3 | 144.2 | 1.001 |
| indexer_q (2048→4096) | wgrad | bf16 | 16231 | previous version |
145.0 | 144.8 | 1.001 |
| indexer_q (2048→4096) | wgrad | f32 | 16172 | previous version | 142.5
| 142.5 | 1.000 |
| indexer_q (2048→4096) | wgrad | f32 | 16231 | previous version | 143.0
| 143.1 | 0.999 |
| shared_down (2048→6144) | dgrad | bf16 | 16172 | previous version |
211.2 | 211.4 | 0.999 |
| shared_down (2048→6144) | dgrad | bf16 | 16231 | previous version |
209.9 | 212.1 | 0.990 |
| shared_down (2048→6144) | dgrad | f32 | 16172 | previous version |
214.4 | 214.3 | 1.000 |
| shared_down (2048→6144) | dgrad | f32 | 16231 | previous version |
212.5 | 212.4 | 1.001 |
| shared_down (2048→6144) | fwd | bf16 | 16172 | previous version |
208.8 | 209.0 | 0.999 |
| shared_down (2048→6144) | fwd | bf16 | 16231 | previous version |
207.7 | 207.8 | 1.000 |
| shared_down (2048→6144) | wgrad | bf16 | 16172 | previous version |
213.7 | 215.5 | 0.992 |
| shared_down (2048→6144) | wgrad | bf16 | 16231 | previous version |
214.4 | 214.6 | 0.999 |
| shared_down (2048→6144) | wgrad | f32 | 16172 | previous version |
215.3 | 215.9 | 0.997 |
| shared_down (2048→6144) | wgrad | f32 | 16231 | previous version |
216.3 | 216.5 | 0.999 |
| q_b (2048→16384) | dgrad | bf16 | 16172 | previous version | 565.5 |
564.3 | 1.002 |
| q_b (2048→16384) | dgrad | bf16 | 16231 | previous version | 562.9 |
562.4 | 1.001 |
| q_b (2048→16384) | dgrad | f32 | 16172 | previous version | 564.7 |
564.6 | 1.000 |
| q_b (2048→16384) | dgrad | f32 | 16231 | previous version | 565.0 |
564.1 | 1.001 |
| q_b (2048→16384) | fwd | bf16 | 16172 | previous version | 537.2 |
537.6 | 0.999 |
| q_b (2048→16384) | fwd | bf16 | 16231 | previous version | 537.6 |
534.7 | 1.006 |
| q_b (2048→16384) | wgrad | bf16 | 16172 | previous version | 551.1 |
548.4 | 1.005 |
| q_b (2048→16384) | wgrad | bf16 | 16231 | previous version | 552.5 |
554.0 | 0.997 |
| q_b (2048→16384) | wgrad | f32 | 16172 | previous version | 557.5 |
552.2 | 1.010 |
| q_b (2048→16384) | wgrad | f32 | 16231 | previous version | 555.2 |
559.4 | 0.992 |
| 4096→32 | dgrad | bf16 | 16231 | previous version | 23.2 | 23.3 |
0.997 |
| 4096→32 | dgrad | bf16 | 16384 | previous version | 23.4 | 23.4 |
1.001 |
| 4096→32 | dgrad | f32 | 16231 | previous version | 42.9 | 43.1 | 0.996
|
| 4096→32 | dgrad | f32 | 16384 | previous version | 43.4 | 43.3 | 1.002
|
| 4096→32 | fwd | bf16 | 16231 | previous version | 26.2 | 26.2 | 1.001
|
| 4096→32 | fwd | bf16 | 16384 | previous version | 25.8 | 25.8 | 1.000
|
| 4096→32 | wgrad | bf16 | 16231 | previous version | 28.2 | 28.0 |
1.005 |
| 4096→32 | wgrad | bf16 | 16384 | previous version | 28.1 | 28.1 |
0.999 |
| 4096→32 | wgrad | f32 | 16231 | previous version | 28.1 | 28.1 | 1.001
|
| 4096→32 | wgrad | f32 | 16384 | previous version | 28.2 | 28.1 | 1.002
|
| 4096→48 | dgrad | bf16 | 16231 | previous version | 23.8 | 23.8 |
0.997 |
| 4096→48 | dgrad | bf16 | 16384 | previous version | 23.8 | 23.9 |
0.995 |
| 4096→48 | dgrad | f32 | 16231 | previous version | 43.4 | 43.5 | 0.997
|
| 4096→48 | dgrad | f32 | 16384 | previous version | 43.8 | 43.9 | 0.999
|
| 4096→48 | fwd | bf16 | 16231 | previous version | 26.2 | 26.2 | 1.001
|
| 4096→48 | fwd | bf16 | 16384 | previous version | 25.8 | 25.8 | 1.001
|
| 4096→48 | wgrad | bf16 | 16231 | previous version | 28.3 | 28.3 |
1.002 |
| 4096→48 | wgrad | bf16 | 16384 | previous version | 28.4 | 28.3 |
1.005 |
| 4096→48 | wgrad | f32 | 16231 | previous version | 28.3 | 28.4 | 0.997
|
| 4096→48 | wgrad | f32 | 16384 | previous version | 28.4 | 28.4 | 1.002
|
| 4096→64 | dgrad | bf16 | 16231 | previous version | 23.6 | 23.7 |
0.996 |
| 4096→64 | dgrad | bf16 | 16384 | previous version | 23.9 | 23.9 |
0.997 |
| 4096→64 | dgrad | f32 | 16231 | previous version | 43.8 | 43.6 | 1.004
|
| 4096→64 | dgrad | f32 | 16384 | previous version | 43.8 | 43.7 | 1.002
|
| 4096→64 | fwd | bf16 | 16231 | previous version | 26.4 | 26.4 | 0.999
|
| 4096→64 | fwd | bf16 | 16384 | previous version | 26.2 | 26.2 | 1.000
|
| 4096→64 | wgrad | bf16 | 16231 | previous version | 28.5 | 28.5 |
0.999 |
| 4096→64 | wgrad | bf16 | 16384 | previous version | 28.4 | 28.3 |
1.002 |
| 4096→64 | wgrad | f32 | 16231 | previous version | 28.6 | 28.6 | 0.997
|
| 4096→64 | wgrad | f32 | 16384 | previous version | 28.4 | 28.4 | 0.997
|
| 4096→128 | dgrad | bf16 | 16231 | previous version | 24.8 | 24.9 |
0.998 |
| 4096→128 | dgrad | bf16 | 16384 | previous version | 24.8 | 24.8 |
1.001 |
| 4096→128 | dgrad | f32 | 16231 | previous version | 45.3 | 45.2 |
1.002 |
| 4096→128 | dgrad | f32 | 16384 | previous version | 45.4 | 45.4 |
1.000 |
| 4096→128 | fwd | bf16 | 16231 | previous version | 27.2 | 27.2 | 0.998
|
| 4096→128 | fwd | bf16 | 16384 | previous version | 26.7 | 26.8 | 0.996
|
| 4096→128 | wgrad | bf16 | 16231 | previous version | 29.3 | 29.2 |
1.004 |
| 4096→128 | wgrad | bf16 | 16384 | previous version | 29.2 | 29.2 |
0.997 |
| 4096→128 | wgrad | f32 | 16231 | previous version | 29.3 | 29.2 |
1.001 |
| 4096→128 | wgrad | f32 | 16384 | previous version | 29.2 | 29.2 |
1.001 |
| 4096→512 | dgrad | bf16 | 16231 | previous version | 43.4 | 43.4 |
1.000 |
| 4096→512 | dgrad | bf16 | 16384 | previous version | 43.4 | 43.4 |
0.999 |
| 4096→512 | dgrad | f32 | 16231 | previous version | 60.4 | 60.4 |
0.999 |
| 4096→512 | dgrad | f32 | 16384 | previous version | 60.3 | 60.3 |
0.999 |
| 4096→512 | fwd | bf16 | 16231 | previous version | 48.2 | 48.2 | 1.000
|
| 4096→512 | fwd | bf16 | 16384 | previous version | 48.1 | 48.3 | 0.996
|
| 4096→512 | wgrad | bf16 | 16231 | previous version | 43.9 | 43.8 |
1.001 |
| 4096→512 | wgrad | bf16 | 16384 | previous version | 44.0 | 44.0 |
1.000 |
| 4096→512 | wgrad | f32 | 16231 | previous version | 43.5 | 43.6 |
0.999 |
| 4096→512 | wgrad | f32 | 16384 | previous version | 43.9 | 43.9 |
1.000 |
| 4096→1024 | dgrad | bf16 | 16231 | previous version | 74.1 | 73.8 |
1.004 |
| 4096→1024 | dgrad | bf16 | 16384 | previous version | 74.3 | 74.2 |
1.001 |
| 4096→1024 | fwd | bf16 | 16231 | previous version | 74.0 | 74.1 |
0.998 |
| 4096→1024 | fwd | bf16 | 16384 | previous version | 73.6 | 73.9 |
0.995 |
| 4096→1024 | wgrad | bf16 | 16231 | previous version | 71.7 | 71.2 |
1.007 |
| 4096→1024 | wgrad | bf16 | 16384 | previous version | 72.0 | 72.3 |
0.996 |
| 4096→1024 | wgrad | f32 | 16231 | previous version | 73.6 | 73.5 |
1.000 |
| 4096→1024 | wgrad | f32 | 16384 | previous version | 74.0 | 74.2 |
0.997 |
| 4096→4096 | dgrad | bf16 | 16231 | previous version | 264.8 | 265.3 |
0.998 |
| 4096→4096 | dgrad | bf16 | 16384 | previous version | 263.4 | 264.9 |
0.994 |
| 4096→4096 | fwd | bf16 | 16231 | previous version | 264.3 | 263.6 |
1.003 |
| 4096→4096 | fwd | bf16 | 16384 | previous version | 264.1 | 264.2 |
0.999 |
| 4096→4096 | wgrad | bf16 | 16231 | previous version | 272.7 | 272.5 |
1.001 |
| 4096→4096 | wgrad | bf16 | 16384 | previous version | 275.2 | 275.4 |
0.999 |
| 4096→4096 | wgrad | f32 | 16231 | previous version | 278.4 | 278.3 |
1.000 |
| 4096→4096 | wgrad | f32 | 16384 | previous version | 281.2 | 281.2 |
1.000 |
| 4096→12288 | dgrad | bf16 | 16231 | previous version | 814.9 | 814.4 |
1.001 |
| 4096→12288 | dgrad | bf16 | 16384 | previous version | 816.2 | 822.2 |
0.993 |
| 4096→12288 | fwd | bf16 | 16231 | previous version | 792.0 | 789.6 |
1.003 |
| 4096→12288 | fwd | bf16 | 16384 | previous version | 795.4 | 794.0 |
1.002 |
| 4096→12288 | wgrad | bf16 | 16231 | previous version | 811.9 | 802.6 |
1.012 |
| 4096→12288 | wgrad | bf16 | 16384 | previous version | 818.2 | 810.8 |
1.009 |
| 4096→12288 | wgrad | f32 | 16231 | previous version | 836.4 | 832.9 |
1.004 |
| 4096→12288 | wgrad | f32 | 16384 | previous version | 834.9 | 833.8 |
1.001 |
| 5120→32 | dgrad | bf16 | 16231 | previous version | 27.7 | 27.8 |
0.999 |
| 5120→32 | dgrad | bf16 | 16384 | previous version | 27.8 | 27.8 |
1.001 |
| 5120→32 | dgrad | f32 | 16231 | previous version | 51.7 | 51.6 | 1.003
|
| 5120→32 | dgrad | f32 | 16384 | previous version | 52.0 | 52.2 | 0.996
|
| 5120→32 | fwd | bf16 | 16231 | previous version | 30.8 | 30.8 | 1.000
|
| 5120→32 | fwd | bf16 | 16384 | previous version | 31.8 | 31.7 | 1.003
|
| 5120→32 | wgrad | bf16 | 16231 | previous version | 33.8 | 34.0 |
0.993 |
| 5120→32 | wgrad | bf16 | 16384 | previous version | 34.0 | 34.2 |
0.997 |
| 5120→32 | wgrad | f32 | 16231 | previous version | 33.7 | 33.9 | 0.996
|
| 5120→32 | wgrad | f32 | 16384 | previous version | 34.1 | 34.1 | 0.999
|
| 5120→48 | dgrad | bf16 | 16231 | previous version | 28.1 | 28.1 |
1.001 |
| 5120→48 | dgrad | bf16 | 16384 | previous version | 28.2 | 28.2 |
0.998 |
| 5120→48 | dgrad | f32 | 16231 | previous version | 52.2 | 52.3 | 0.998
|
| 5120→48 | dgrad | f32 | 16384 | previous version | 52.6 | 52.7 | 0.997
|
| 5120→48 | fwd | bf16 | 16231 | previous version | 30.8 | 30.9 | 0.997
|
| 5120→48 | fwd | bf16 | 16384 | previous version | 31.8 | 31.8 | 1.001
|
| 5120→48 | wgrad | bf16 | 16231 | previous version | 34.1 | 34.3 |
0.994 |
| 5120→48 | wgrad | bf16 | 16384 | previous version | 34.5 | 34.5 |
1.000 |
| 5120→48 | wgrad | f32 | 16231 | previous version | 34.1 | 34.1 | 1.001
|
| 5120→48 | wgrad | f32 | 16384 | previous version | 34.6 | 34.5 | 1.000
|
| 5120→64 | dgrad | bf16 | 16231 | previous version | 28.0 | 28.1 |
0.998 |
| 5120→64 | dgrad | bf16 | 16384 | previous version | 28.3 | 28.3 |
1.001 |
| 5120→64 | dgrad | f32 | 16231 | previous version | 52.4 | 52.5 | 0.998
|
| 5120→64 | dgrad | f32 | 16384 | previous version | 52.9 | 52.8 | 1.002
|
| 5120→64 | fwd | bf16 | 16231 | previous version | 31.4 | 31.3 | 1.003
|
| 5120→64 | fwd | bf16 | 16384 | previous version | 32.1 | 32.1 | 1.000
|
| 5120→64 | wgrad | bf16 | 16231 | previous version | 34.4 | 34.4 |
1.000 |
| 5120→64 | wgrad | bf16 | 16384 | previous version | 34.5 | 34.5 |
1.001 |
| 5120→64 | wgrad | f32 | 16231 | previous version | 34.4 | 34.5 | 0.998
|
| 5120→64 | wgrad | f32 | 16384 | previous version | 34.5 | 34.4 | 1.004
|
| 5120→128 | dgrad | bf16 | 16231 | previous version | 29.6 | 29.5 |
1.002 |
| 5120→128 | dgrad | bf16 | 16384 | previous version | 29.6 | 29.6 |
0.999 |
| 5120→128 | dgrad | f32 | 16231 | previous version | 54.7 | 54.6 |
1.003 |
| 5120→128 | dgrad | f32 | 16384 | previous version | 54.8 | 54.8 |
1.000 |
| 5120→128 | fwd | bf16 | 16231 | previous version | 32.5 | 32.5 | 1.001
|
| 5120→128 | fwd | bf16 | 16384 | previous version | 32.3 | 32.4 | 0.997
|
| 5120→128 | wgrad | bf16 | 16231 | previous version | 35.6 | 35.6 |
1.000 |
| 5120→128 | wgrad | bf16 | 16384 | previous version | 36.0 | 36.1 |
0.996 |
| 5120→128 | wgrad | f32 | 16231 | previous version | 35.5 | 35.4 |
1.004 |
| 5120→128 | wgrad | f32 | 16384 | previous version | 35.8 | 35.9 |
0.998 |
| 5120→512 | dgrad | bf16 | 16231 | previous version | 54.2 | 52.8 |
1.027 |
| 5120→512 | dgrad | bf16 | 16384 | previous version | 54.3 | 52.7 |
1.029 |
| 5120→512 | dgrad | f32 | 16231 | previous version | 73.8 | 73.9 |
0.999 |
| 5120→512 | dgrad | f32 | 16384 | previous version | 74.2 | 74.4 |
0.998 |
| 5120→512 | fwd | bf16 | 16231 | previous version | 57.8 | 57.8 | 1.000
|
| 5120→512 | fwd | bf16 | 16384 | previous version | 57.9 | 57.9 | 0.999
|
| 5120→512 | wgrad | bf16 | 16231 | previous version | 52.6 | 52.8 |
0.997 |
| 5120→512 | wgrad | bf16 | 16384 | previous version | 52.9 | 53.0 |
1.000 |
| 5120→512 | wgrad | f32 | 16231 | previous version | 54.7 | 54.9 |
0.997 |
| 5120→512 | wgrad | f32 | 16384 | previous version | 54.2 | 54.3 |
0.998 |
| 5120→1024 | dgrad | bf16 | 16231 | previous version | 92.1 | 91.1 |
1.012 |
| 5120→1024 | dgrad | bf16 | 16384 | previous version | 92.2 | 91.4 |
1.009 |
| 5120→1024 | fwd | bf16 | 16231 | previous version | 91.6 | 91.8 |
0.998 |
| 5120→1024 | fwd | bf16 | 16384 | previous version | 92.1 | 92.0 |
1.001 |
| 5120→1024 | wgrad | bf16 | 16231 | previous version | 96.1 | 96.3 |
0.999 |
| 5120→1024 | wgrad | bf16 | 16384 | previous version | 96.7 | 96.8 |
0.999 |
| 5120→1024 | wgrad | f32 | 16231 | previous version | 97.7 | 97.6 |
1.001 |
| 5120→1024 | wgrad | f32 | 16384 | previous version | 98.1 | 98.1 |
1.001 |
| 5120→5120 | dgrad | bf16 | 16231 | previous version | 417.1 | 417.7 |
0.999 |
| 5120→5120 | dgrad | bf16 | 16384 | previous version | 417.3 | 417.6 |
0.999 |
| 5120→5120 | fwd | bf16 | 16231 | previous version | 417.0 | 417.4 |
0.999 |
| 5120→5120 | fwd | bf16 | 16384 | previous version | 417.8 | 418.2 |
0.999 |
| 5120→5120 | wgrad | bf16 | 16231 | previous version | 421.8 | 421.6 |
1.000 |
| 5120→5120 | wgrad | bf16 | 16384 | previous version | 425.6 | 424.2 |
1.003 |
| 5120→5120 | wgrad | f32 | 16231 | previous version | 423.5 | 422.9 |
1.001 |
| 5120→5120 | wgrad | f32 | 16384 | previous version | 426.2 | 426.8 |
0.999 |
| 5120→17408 | dgrad | bf16 | 16231 | previous version | 1420.3 | 1421.1
| 0.999 |
| 5120→17408 | dgrad | bf16 | 16384 | previous version | 1426.9 | 1416.5
| 1.007 |
| 5120→17408 | fwd | bf16 | 16231 | previous version | 1410.9 | 1404.8 |
1.004 |
| 5120→17408 | fwd | bf16 | 16384 | previous version | 1400.2 | 1441.4 |
0.971 |
| 5120→17408 | wgrad | bf16 | 16231 | previous version | 1397.8 | 1393.0
| 1.003 |
| 5120→17408 | wgrad | bf16 | 16384 | previous version | 1425.0 | 1405.0
| 1.014 |
| 5120→17408 | wgrad | f32 | 16231 | previous version | 1406.8 | 1408.4
| 0.999 |
| 5120→17408 | wgrad | f32 | 16384 | previous version | 1416.5 | 1416.5
| 1.000 |
| indexer_hw (6144→32) | dgrad | bf16 | 16172 | previous version | 32.9
| 33.4 | 0.986 |
| indexer_hw (6144→32) | dgrad | bf16 | 16231 | previous version | 32.9
| 32.9 | 1.000 |
| indexer_hw (6144→32) | dgrad | f32 | 16172 | previous version | 58.4 |
58.6 | 0.997 |
| indexer_hw (6144→32) | dgrad | f32 | 16231 | previous version | 58.8 |
58.7 | 1.002 |
| indexer_hw (6144→32) | fwd | bf16 | 16172 | previous version | 36.3 |
36.4 | 0.997 |
| indexer_hw (6144→32) | fwd | bf16 | 16231 | previous version | 36.3 |
36.3 | 1.000 |
| indexer_hw (6144→32) | wgrad | bf16 | 16172 | previous version | 39.0
| 39.0 | 1.000 |
| indexer_hw (6144→32) | wgrad | bf16 | 16231 | previous version | 39.0
| 38.9 | 1.001 |
| indexer_hw (6144→32) | wgrad | f32 | 16172 | previous version | 39.1 |
39.0 | 1.000 |
| indexer_hw (6144→32) | wgrad | f32 | 16231 | previous version | 39.1 |
39.1 | 0.999 |
| indexer_k (6144→128) | dgrad | bf16 | 16172 | previous version | 34.5
| 34.6 | 0.999 |
| indexer_k (6144→128) | dgrad | bf16 | 16231 | previous version | 34.5
| 34.6 | 0.998 |
| indexer_k (6144→128) | dgrad | f32 | 16172 | previous version | 62.5 |
62.4 | 1.001 |
| indexer_k (6144→128) | dgrad | f32 | 16231 | previous version | 62.3 |
62.2 | 1.001 |
| indexer_k (6144→128) | fwd | bf16 | 16172 | previous version | 37.7 |
37.6 | 1.001 |
| indexer_k (6144→128) | fwd | bf16 | 16231 | previous version | 37.5 |
37.6 | 1.000 |
| indexer_k (6144→128) | wgrad | bf16 | 16172 | previous version | 40.5
| 40.6 | 0.998 |
| indexer_k (6144→128) | wgrad | bf16 | 16231 | previous version | 41.1
| 41.0 | 1.002 |
| indexer_k (6144→128) | wgrad | f32 | 16172 | previous version | 40.5 |
40.4 | 1.004 |
| indexer_k (6144→128) | wgrad | f32 | 16231 | previous version | 40.9 |
40.8 | 1.001 |
| kv_a (6144→576) | dgrad | bf16 | 16172 | previous version | 66.5 |
66.4 | 1.001 |
| kv_a (6144→576) | dgrad | bf16 | 16231 | previous version | 66.6 |
66.7 | 0.999 |
| kv_a (6144→576) | dgrad | f32 | 16172 | previous version | 91.1 | 91.2
| 0.999 |
| kv_a (6144→576) | dgrad | f32 | 16231 | previous version | 91.9 | 92.0
| 0.999 |
| kv_a (6144→576) | fwd | bf16 | 16172 | previous version | 71.8 | 71.6
| 1.003 |
| kv_a (6144→576) | fwd | bf16 | 16231 | previous version | 71.6 | 71.7
| 0.998 |
| kv_a (6144→576) | wgrad | bf16 | 16172 | previous version | 64.3 |
64.4 | 0.998 |
| kv_a (6144→576) | wgrad | bf16 | 16231 | previous version | 64.9 |
64.9 | 0.999 |
| kv_a (6144→576) | wgrad | f32 | 16172 | previous version | 65.1 | 65.1
| 1.001 |
| kv_a (6144→576) | wgrad | f32 | 16231 | previous version | 65.5 | 65.4
| 1.001 |
| q_a (6144→2048) | dgrad | bf16 | 16172 | previous version | 207.7 |
208.7 | 0.996 |
| q_a (6144→2048) | dgrad | bf16 | 16231 | previous version | 207.5 |
208.0 | 0.997 |
| q_a (6144→2048) | dgrad | f32 | 16172 | previous version | 218.0 |
218.2 | 0.999 |
| q_a (6144→2048) | dgrad | f32 | 16231 | previous version | 218.4 |
218.3 | 1.000 |
| q_a (6144→2048) | fwd | bf16 | 16172 | previous version | 206.6 |
206.0 | 1.003 |
| q_a (6144→2048) | fwd | bf16 | 16231 | previous version | 206.5 |
206.1 | 1.002 |
| q_a (6144→2048) | wgrad | bf16 | 16172 | previous version | 214.0 |
214.0 | 1.000 |
| q_a (6144→2048) | wgrad | bf16 | 16231 | previous version | 214.5 |
214.7 | 0.999 |
| q_a (6144→2048) | wgrad | f32 | 16172 | previous version | 215.3 |
215.0 | 1.001 |
| q_a (6144→2048) | wgrad | f32 | 16231 | previous version | 215.8 |
215.3 | 1.002 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16172 | previous version |
207.4 | 207.1 | 1.001 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16231 | previous version |
207.6 | 208.0 | 0.998 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16172 | previous version |
218.4 | 218.0 | 1.002 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16231 | previous version |
218.2 | 218.2 | 1.000 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16172 | previous version |
206.4 | 206.6 | 0.999 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16231 | previous version |
206.5 | 206.3 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16172 | previous version |
213.6 | 213.6 | 1.000 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16231 | previous version |
214.9 | 214.7 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16172 | previous version |
214.8 | 214.6 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16231 | previous version |
215.9 | 215.6 | 1.001 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16172 | previous version |
1187.8 | 1184.9 | 1.002 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16231 | previous version |
1188.1 | 1193.8 | 0.995 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16172 | previous version |
1192.8 | 1188.8 | 1.003 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16231 | previous version |
1206.2 | 1194.9 | 1.009 |
| 8192→128 | dgrad | bf16 | 16231 | previous version | 47.0 | 44.0 |
1.069 |
| 8192→128 | dgrad | bf16 | 16384 | previous version | 44.2 | 44.2 |
1.001 |
| 8192→128 | dgrad | f32 | 16231 | previous version | 85.9 | 86.1 |
0.998 |
| 8192→128 | dgrad | f32 | 16384 | previous version | 85.4 | 85.4 |
1.001 |
| 8192→128 | fwd | bf16 | 16231 | previous version | 47.2 | 47.2 | 1.000
|
| 8192→128 | fwd | bf16 | 16384 | previous version | 47.7 | 47.8 | 0.999
|
| 8192→128 | wgrad | bf16 | 16231 | previous version | 45.3 | 45.4 |
0.998 |
| 8192→128 | wgrad | bf16 | 16384 | previous version | 45.6 | 45.8 |
0.995 |
| 8192→128 | wgrad | f32 | 16231 | previous version | 45.4 | 45.1 |
1.005 |
| 8192→128 | wgrad | f32 | 16384 | previous version | 45.6 | 45.6 |
0.998 |
| 12288→4096 | dgrad | bf16 | 16231 | previous version | 795.0 | 793.5 |
1.002 |
| 12288→4096 | dgrad | bf16 | 16384 | previous version | 795.6 | 794.3 |
1.002 |
| 12288→4096 | fwd | bf16 | 16231 | previous version | 807.2 | 811.5 |
0.995 |
| 12288→4096 | fwd | bf16 | 16384 | previous version | 810.1 | 807.6 |
1.003 |
| 12288→4096 | wgrad | bf16 | 16231 | previous version | 797.3 | 800.0 |
0.997 |
| 12288→4096 | wgrad | bf16 | 16384 | previous version | 801.7 | 803.5 |
0.998 |
| 12288→4096 | wgrad | f32 | 16231 | previous version | 826.8 | 827.0 |
1.000 |
| 12288→4096 | wgrad | f32 | 16384 | previous version | 828.5 | 828.3 |
1.000 |
| dense_down (12288→6144) | wgrad | bf16 | 16172 | previous version |
1186.9 | 1182.2 | 1.004 |
| dense_down (12288→6144) | wgrad | bf16 | 16231 | previous version |
1180.4 | 1195.8 | 0.987 |
| dense_down (12288→6144) | wgrad | f32 | 16172 | previous version |
1187.9 | 1186.0 | 1.002 |
| dense_down (12288→6144) | wgrad | f32 | 16231 | previous version |
1197.2 | 1191.8 | 1.004 |
| o_proj (16384→6144) | dgrad | bf16 | 16172 | previous version | 1583.1
| 1584.9 | 0.999 |
| o_proj (16384→6144) | dgrad | bf16 | 16231 | previous version | 1694.0
| 1596.3 | 1.061 |
| o_proj (16384→6144) | dgrad | f32 | 16172 | previous version | 1630.2
| 1621.3 | 1.005 |
| o_proj (16384→6144) | dgrad | f32 | 16231 | previous version | 1620.9
| 1630.9 | 0.994 |
| o_proj (16384→6144) | fwd | bf16 | 16172 | previous version | 1618.2 |
1628.5 | 0.994 |
| o_proj (16384→6144) | fwd | bf16 | 16231 | previous version | 1647.1 |
1623.8 | 1.014 |
| o_proj (16384→6144) | wgrad | bf16 | 16172 | previous version | 1598.0
| 1599.7 | 0.999 |
| o_proj (16384→6144) | wgrad | bf16 | 16231 | previous version | 1608.1
| 1601.1 | 1.004 |
| o_proj (16384→6144) | wgrad | f32 | 16172 | previous version | 1611.1
| 1608.8 | 1.001 |
| o_proj (16384→6144) | wgrad | f32 | 16231 | previous version | 1618.2
| 1617.3 | 1.001 |
| 17408→5120 | dgrad | bf16 | 16231 | previous version | 1418.0 | 1405.1
| 1.009 |
| 17408→5120 | dgrad | bf16 | 16384 | previous version | 1413.8 | 1411.7
| 1.002 |
| 17408→5120 | fwd | bf16 | 16231 | previous version | 1409.9 | 1415.6 |
0.996 |
| 17408→5120 | fwd | bf16 | 16384 | previous version | 1468.6 | 1422.5 |
1.032 |
| 17408→5120 | wgrad | bf16 | 16231 | previous version | 1398.9 | 1456.5
| 0.961 |
| 17408→5120 | wgrad | bf16 | 16384 | previous version | 1483.4 | 1403.6
| 1.057 |
| 17408→5120 | wgrad | f32 | 16231 | previous version | 1411.4 | 1448.9
| 0.974 |
| 17408→5120 | wgrad | f32 | 16384 | previous version | 1426.9 | 1424.3
| 1.002 |
| qabs (None→None) | dgrad | bf16 | 16172 | previous version | 229.9 |
229.6 | 1.001 |
| qabs (None→None) | dgrad | bf16 | 16231 | previous version | 228.3 |
228.2 | 1.001 |
| qabs (None→None) | fwd | bf16 | 16172 | previous version | 242.5 |
242.7 | 0.999 |
| qabs (None→None) | fwd | bf16 | 16231 | previous version | 247.3 |
247.4 | 1.000 |
| qabs (None→None) | wgrad | bf16 | 16172 | previous version | 216.3 |
216.2 | 1.001 |
| qabs (None→None) | wgrad | bf16 | 16231 | previous version | 216.7 |
217.0 | 0.999 |
| vproj (None→None) | dgrad | bf16 | 16172 | previous version | 266.1 |
266.7 | 0.998 |
| vproj (None→None) | dgrad | bf16 | 16231 | previous version | 265.9 |
265.6 | 1.001 |
| vproj (None→None) | fwd | bf16 | 16172 | previous version | 250.7 |
250.8 | 0.999 |
| vproj (None→None) | fwd | bf16 | 16231 | previous version | 254.2 |
254.1 | 1.000 |
| vproj (None→None) | wgrad | bf16 | 16172 | previous version | 234.7 |
233.9 | 1.003 |
| vproj (None→None) | wgrad | bf16 | 16231 | previous version | 234.9 |
235.0 | 0.999 |
| 4096→256 | dgrad | f32 | 16231 | previous version | 170.4 | 170.2 |
1.001 |
| 4096→256 | fwd | f32 | 16231 | previous version | 163.6 | 163.3 |
1.001 |
| 4096→256 | wgrad | f32 | 16231 | previous version | 160.6 | 160.4 |
1.001 |
| 5120→256 | dgrad | f32 | 16231 | previous version | 222.8 | 222.6 |
1.001 |
| 5120→256 | fwd | f32 | 16231 | previous version | 192.6 | 192.8 |
0.999 |
| 5120→256 | wgrad | f32 | 16231 | previous version | 206.8 | 206.8 |
1.000 |
| 6144→256 | dgrad | f32 | 16172 | previous version | 257.2 | 257.0 |
1.001 |
| 6144→256 | dgrad | f32 | 16231 | previous version | 259.7 | 259.4 |
1.001 |
| 6144→256 | fwd | f32 | 16172 | previous version | 224.2 | 224.2 |
1.000 |
| 6144→256 | fwd | f32 | 16231 | previous version | 222.5 | 222.7 |
0.999 |
| 6144→256 | wgrad | f32 | 16172 | previous version | 211.7 | 211.2 |
1.003 |
| 6144→256 | wgrad | f32 | 16231 | previous version | 211.6 | 211.2 |
1.002 |

Every variant listed above ships in this package, which has programs for
sm_100a (GB200), sm_103a (GB300) and sm_107a: 251 build entries (80 / 84
/ 87) and 124 registry records, up from 249 (80 / 82 / 87) and 122 in
the previous version; the two added entries are the two new sm_103a
programs.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optional pacing setting for dense-projection GEMM output
stores, with automatic selection for certain BF16 input-gradient
workloads on supported hardware.
  * Documented when pacing applies and how to configure it.
* **Bug Fixes**
* Corrected generated kernel metadata and tensor-transfer tile
configurations for dense-projection GEMM variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0b352a6](https://github.com/flashinfer-ai/flashinfer/commit/0b352a6333c706d9910c622de978e934f8be7c33)

- **作者**: eigen
- **时间**: 2026-10-25T21:23:04Z
- **提交信息**: perf(cake_gated_act_mxfp8): narrow tiles for small problems and four rows per thread for large ones (#7346)

This PR updates the Cake programs behind FlashInfer's fused SwiGLU +
MXFP8 quantization. The kernel computes silu(gate) * up from a BF16
input [M, 2K] and quantizes the result to MXFP8. The output uses E4M3
values with one E8M0 scale (RCEIL rounding) per 32 values, and the
scales are stored in the swizzled 128 x 4 layout. There is one data type
(BF16 in, MXFP8 E4M3 + E8M0 out) and six forms. The forward form is
`flashinfer.silu_and_mul_mxfp8_quantize`, with output [M, K]. The
backward form is `flashinfer.silu_and_mul_mxfp8_quantize_backward`,
which produces gate and up gradients [M, 2K] from grad_output [M, K].
Each one has rowwise, colwise or both outputs. The package
`flashinfer.cake_gated_act_mxfp8_backend` runs one program per call,
chosen by M * K per architecture. This PR updates the programs of all
six forms on sm_100a, sm_103a and sm_107a:
- Below the first size threshold, a 32 x 32 CTA tile runs the forward on
sm_100a and sm_103a and the backward on all three architectures.
- On sm_103a, the colwise forward runs a 32 x 64 tile from 2^22 to 2^24
elements.
- A four-rows-per-thread program runs at the large sm_107a shapes and at
the largest sm_103a forward shapes with both outputs.

The public API is unchanged, and every output byte is identical. The
baseline is the previous Cake version of this kernel, which is the Cake
package FlashInfer main ships (#7305).

Speedup is previous Cake latency / this PR's latency. Latency is the
mean CUPTI kernel time in microseconds, with a cold L2 before every
launch, and both versions run in the same process on the same GPU in
alternating paired runs. On B200, only the six 128 x 128 rows run a new
program, at 1.144-1.260x. The other 24 rows run the same program on both
sides, and their ratios (0.978-1.014x) are run-to-run variation. On
GB300, nine rows run a new program at 1.005-1.121x: the six 128 x 128
rows, 4096 x 2048 fwd colwise, and 16384 x 7168 and 131072 x 8192 fwd
both. The other 21 rows run the same program on both sides, at
0.998-1.001x. On R200, twelve rows run a new program at 1.017-1.116x:
the three 128 x 128 backward rows, 4096 x 7168 fwd both, 16384 x 7168
fwd rowwise / colwise / both and bwd colwise, and 131072 x 8192 fwd
rowwise / colwise / both and bwd colwise. The other 18 rows run the same
program on both sides, at 0.999-1.001x.

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4.92

| M x K | Pass | Previous Cake (µs) | This PR (µs) | Speedup |
|---|---|---:|---:|---:|
| 128 x 128 | fwd rowwise | 2.53 | 2.06 | 1.230x |
| 128 x 128 | fwd colwise | 2.67 | 2.12 | 1.260x |
| 128 x 128 | fwd both | 2.78 | 2.25 | 1.234x |
| 128 x 128 | bwd rowwise | 2.56 | 2.24 | 1.144x |
| 128 x 128 | bwd colwise | 2.85 | 2.36 | 1.206x |
| 128 x 128 | bwd both | 2.92 | 2.53 | 1.152x |
| 4096 x 2048 | fwd rowwise | 9.60 | 9.60 | 1.001x |
| 4096 x 2048 | fwd colwise | 10.37 | 10.37 | 1.000x |
| 4096 x 2048 | fwd both | 11.53 | 11.53 | 1.000x |
| 4096 x 2048 | bwd rowwise | 13.83 | 13.83 | 1.000x |
| 4096 x 2048 | bwd colwise | 14.91 | 14.90 | 1.000x |
| 4096 x 2048 | bwd both | 18.04 | 18.04 | 1.000x |
| 4096 x 7168 | fwd rowwise | 25.30 | 25.29 | 1.000x |
| 4096 x 7168 | fwd colwise | 26.47 | 26.47 | 1.000x |
| 4096 x 7168 | fwd both | 31.31 | 31.31 | 1.000x |
| 4096 x 7168 | bwd rowwise | 39.34 | 39.34 | 1.000x |
| 4096 x 7168 | bwd colwise | 41.06 | 41.07 | 1.000x |
| 4096 x 7168 | bwd both | 50.41 | 50.40 | 1.000x |
| 16384 x 7168 | fwd rowwise | 89.91 | 89.92 | 1.000x |
| 16384 x 7168 | fwd colwise | 91.71 | 91.72 | 1.000x |
| 16384 x 7168 | fwd both | 108.54 | 108.53 | 1.000x |
| 16384 x 7168 | bwd rowwise | 141.22 | 141.29 | 1.000x |
| 16384 x 7168 | bwd colwise | 145.29 | 145.30 | 1.000x |
| 16384 x 7168 | bwd both | 187.17 | 187.21 | 1.000x |
| 131072 x 8192 | fwd rowwise | 765.89 | 764.82 | 1.001x |
| 131072 x 8192 | fwd colwise | 821.69 | 815.25 | 1.008x |
| 131072 x 8192 | fwd both | 1003.00 | 1025.67 | 0.978x |
| 131072 x 8192 | bwd rowwise | 1247.49 | 1241.54 | 1.005x |
| 131072 x 8192 | bwd colwise | 1391.55 | 1371.77 | 1.014x |
| 131072 x 8192 | bwd both | 1728.92 | 1746.36 | 0.990x |

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4.92

| M x K | Pass | Previous Cake (µs) | This PR (µs) | Speedup |
|---|---|---:|---:|---:|
| 128 x 128 | fwd rowwise | 2.13 | 1.94 | 1.096x |
| 128 x 128 | fwd colwise | 2.26 | 2.02 | 1.121x |
| 128 x 128 | fwd both | 2.35 | 2.12 | 1.111x |
| 128 x 128 | bwd rowwise | 2.16 | 2.14 | 1.010x |
| 128 x 128 | bwd colwise | 2.42 | 2.23 | 1.087x |
| 128 x 128 | bwd both | 2.48 | 2.41 | 1.031x |
| 4096 x 2048 | fwd rowwise | 9.02 | 9.03 | 1.000x |
| 4096 x 2048 | fwd colwise | 9.88 | 9.83 | 1.005x |
| 4096 x 2048 | fwd both | 10.97 | 10.97 | 1.000x |
| 4096 x 2048 | bwd rowwise | 13.27 | 13.26 | 1.001x |
| 4096 x 2048 | bwd colwise | 13.99 | 13.99 | 1.000x |
| 4096 x 2048 | bwd both | 16.81 | 16.81 | 1.000x |
| 4096 x 7168 | fwd rowwise | 24.42 | 24.44 | 0.999x |
| 4096 x 7168 | fwd colwise | 25.52 | 25.52 | 1.000x |
| 4096 x 7168 | fwd both | 30.30 | 30.30 | 1.000x |
| 4096 x 7168 | bwd rowwise | 37.75 | 37.81 | 0.998x |
| 4096 x 7168 | bwd colwise | 39.95 | 39.92 | 1.001x |
| 4096 x 7168 | bwd both | 47.77 | 47.77 | 1.000x |
| 16384 x 7168 | fwd rowwise | 87.35 | 87.28 | 1.001x |
| 16384 x 7168 | fwd colwise | 90.02 | 90.02 | 1.000x |
| 16384 x 7168 | fwd both | 106.60 | 105.34 | 1.012x |
| 16384 x 7168 | bwd rowwise | 135.79 | 135.81 | 1.000x |
| 16384 x 7168 | bwd colwise | 139.71 | 139.69 | 1.000x |
| 16384 x 7168 | bwd both | 175.33 | 175.25 | 1.000x |
| 131072 x 8192 | fwd rowwise | 742.29 | 741.71 | 1.001x |
| 131072 x 8192 | fwd colwise | 756.04 | 756.05 | 1.000x |
| 131072 x 8192 | fwd both | 923.27 | 904.89 | 1.020x |
| 131072 x 8192 | bwd rowwise | 1174.31 | 1174.17 | 1.000x |
| 131072 x 8192 | bwd colwise | 1222.94 | 1223.02 | 1.000x |
| 131072 x 8192 | bwd both | 1552.67 | 1552.57 | 1.000x |

### NVIDIA R200 (sm_107a, 208 SMs), CUDA 13.4.92

| M x K | Pass | Previous Cake (µs) | This PR (µs) | Speedup |
|---|---|---:|---:|---:|
| 128 x 128 | fwd rowwise | 2.11 | 2.11 | 1.000x |
| 128 x 128 | fwd colwise | 2.28 | 2.28 | 0.999x |
| 128 x 128 | fwd both | 2.34 | 2.34 | 1.001x |
| 128 x 128 | bwd rowwise | 2.24 | 2.05 | 1.090x |
| 128 x 128 | bwd colwise | 2.42 | 2.17 | 1.116x |
| 128 x 128 | bwd both | 2.56 | 2.30 | 1.112x |
| 4096 x 2048 | fwd rowwise | 7.22 | 7.22 | 1.000x |
| 4096 x 2048 | fwd colwise | 7.34 | 7.34 | 1.000x |
| 4096 x 2048 | fwd both | 8.76 | 8.76 | 1.001x |
| 4096 x 2048 | bwd rowwise | 10.50 | 10.49 | 1.000x |
| 4096 x 2048 | bwd colwise | 11.07 | 11.06 | 1.000x |
| 4096 x 2048 | bwd both | 13.34 | 13.33 | 1.000x |
| 4096 x 7168 | fwd rowwise | 18.48 | 18.48 | 1.000x |
| 4096 x 7168 | fwd colwise | 18.99 | 19.00 | 0.999x |
| 4096 x 7168 | fwd both | 22.84 | 21.96 | 1.040x |
| 4096 x 7168 | bwd rowwise | 28.84 | 28.82 | 1.001x |
| 4096 x 7168 | bwd colwise | 29.04 | 29.05 | 1.000x |
| 4096 x 7168 | bwd both | 36.09 | 36.11 | 1.000x |
| 16384 x 7168 | fwd rowwise | 63.67 | 59.12 | 1.077x |
| 16384 x 7168 | fwd colwise | 63.19 | 61.00 | 1.036x |
| 16384 x 7168 | fwd both | 78.43 | 75.13 | 1.044x |
| 16384 x 7168 | bwd rowwise | 97.26 | 97.26 | 1.000x |
| 16384 x 7168 | bwd colwise | 100.35 | 98.63 | 1.017x |
| 16384 x 7168 | bwd both | 131.91 | 131.93 | 1.000x |
| 131072 x 8192 | fwd rowwise | 528.30 | 481.99 | 1.096x |
| 131072 x 8192 | fwd colwise | 533.65 | 515.98 | 1.034x |
| 131072 x 8192 | fwd both | 682.08 | 658.88 | 1.035x |
| 131072 x 8192 | bwd rowwise | 831.87 | 831.91 | 1.000x |
| 131072 x 8192 | bwd colwise | 882.75 | 864.51 | 1.021x |
| 131072 x 8192 | bwd both | 1183.12 | 1183.07 | 1.000x |

Cake ships this kernel only in this BF16-to-MXFP8 form (the six forms
above), and the package ships on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added broader GPU kernel coverage for gated-activation MXFP8
operations, including forward and gradient calculations across
additional tile sizes and architectures.
* Expanded support for large input sizes and added more flexible kernel
selection based on input dimensions.

* **Bug Fixes**
* Improved fallback selection when an architecture has no specific rule,
and added checks for ambiguous kernel-selection rules.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e7f5b1e](https://github.com/flashinfer-ai/flashinfer/commit/e7f5b1e13d97a444de6e8a06504a8fa86f2dfe8a)

- **作者**: eigen
- **时间**: 2026-10-25T21:22:36Z
- **提交信息**: perf(cake_all_gather_matmul): SM103a last-pass N-split twin for 1025-row bf16 K-major calls at world size 8 (#7360)

`cake_all_gather_matmul` all-gathers each rank's row-sharded activation
and multiplies it by a `[K, N]` weight. The weight is either a
contiguous `[K, N]` tensor (N-major) or the transposed view of a
contiguous `[N, K]` parameter (K-major). Cake ships the kernel in bf16
and fp16, with K-major and N-major weights, for world sizes 2, 4 and 8,
with two main-tile widths and two transport routes (copy engine, SM
push). This PR adds one SM103a (B300) program and routes one call to it.
The new program is the last-pass N-split twin (`_cg1s2`) of the
world-size-8 bf16 K-major main program. The call is world size 8 with
K-major weights, 1025 rows per rank (1152 padded) and N = 1280, in bf16.
The twin changes only how it runs the main program's last landing group,
which holds the P tiles of the final peer pass. When 2P is at most the
CTA count, it runs that group as 2P half-width 128 x 128 tiles on CTAs
that would otherwise be idle. The stages, K order, MMA sequence,
accumulator, epilogue, barriers, grid, launch path and ABI stay the same
as the main program's. The copy-engine transport is unchanged, no other
call changes its program, and SM100a routes no call to the twin. The
baseline is the previous Cake version of this kernel, which FlashInfer
ships for SM103a today. Against it, the speedup is 1.0116 to 1.0209
across both nodes.

| Shape per rank, M x N (K = 8192, K-major weights, world size 8) |
Dtype | Node | Previous Cake version (µs) | This PR (µs) | Speedup |
|---|---|---|---:|---:|---:|
| 1025 x 1280 (Llama-3.1-70B TP8 QKV) | bf16 | node 1 | 341.6 | 336.6 |
1.0116 |
| 1025 x 1280 (Llama-3.1-70B TP8 QKV) | bf16 | node 2 | 340.7 | 337.7 |
1.0209 |

NVIDIA B300 (SM103a), CUDA 13.3, two 8xB300 nodes, one rank per GPU.
Latency is the median over calls of the slowest rank's time. Speedup > 1
means this PR is faster. Each speedup is the median of the per-group
ratios (previous / this PR) over interleaved measurement groups. It is
therefore not the quotient of the two latencies beside it. Every ratio
lies outside its node's noise band (in ln; node 1: 0.0099; node 2:
0.0097).

Cake also ships `_n128` (128-wide), CTA-pair `_cg2`, spill-split pair
`_cg2s2` (world sizes 4 and 8 on both architectures) and `_ks4`
per-K-slice readiness (`sm_103a` only) twins of its main programs, a
`_po` peer-outer tile-order form of the world-size-4 bf16 K-major main
program for one 128-row shape (`sm_103a` only), and the push programs
`peer_push` and `peer_push_wide` (both architectures) with the
`peer_push_wide_ks4` twin (`sm_103a` only); the family ships on
`sm_100a` (B200) and `sm_103a` (B300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a specialized execution option for 8-rank BF16 all-gather matrix
multiplication on supported hardware and workloads. For matching
configurations, the operation can use a one-CTA path with N-split
output, while other configurations continue to use their existing
execution paths.
* Improved support for selecting and validating this option, including
its required launch configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [941fda2](https://github.com/flashinfer-ai/flashinfer/commit/941fda25dbb0c06fa2dfadb28928e1594047a00a)

- **作者**: eigen
- **时间**: 2026-10-25T21:19:31Z
- **提交信息**: perf(cake_mm_fp4): faster per-token NVFP4 quantizer and GEMM programs on SM100 / SM103 (#7356)

`cake_mm_fp4` (`flashinfer.experimental.cake_nvfp4_per_token`,
experimental) quantizes activations to NVFP4 per token, then runs an
NVFP4 x NVFP4 GEMM. Callers opt in with `nvfp4_quantize(...,
per_token_activation=True, backend="cake")` and with `mm_fp4(...,
backend="cake")` plus a per-token fp32 `alpha [M]`. The family has two
kernels and one fused form:

- The activation quantizer has three variants: bf16 activations, bf16
with the GEMM output scale folded into the per-token scale, and fp16
activations (K = 7168).
- The GEMM uses block-16 scales and a per-token alpha epilogue. It has
two variants: bf16 output and fp16 output.
- The fused form is the quantize -> GEMM chain, launched back to back
with programmatic dependent launch.

This PR replaces programs in both bf16 quantizer variants and both GEMM
variants, and updates the quantizer and GEMM dispatch rules to match.
The fused chain uses both kernels, so it gets both changes. The fp16
quantizer does not change. Shapes this PR does not reroute keep `main`'s
programs. The baseline is the previous Cake version of these kernels, as
shipped in `main` (`backend="cake"`).

On the rows whose program this PR changes, speedup is 1.005x to 1.255x
on B200 (110 of 428 rows) and 1.000x to 1.243x on GB300 (199 of 428
rows). The rows that keep `main`'s programs measure 0.996x to 1.004x on
B200 (318 of 428) and 0.997x to 1.004x on GB300 (229 of 428). The best
row for the quantizer alone is 1.255x on B200 and 1.243x on GB300. For
the GEMM alone it is 1.040x and 1.144x, and for quantize + GEMM it is
1.062x and 1.140x.

**NVIDIA B200 (sm_100a), CUDA 13.4**: latency in µs; GEMM and quant =
kernel time with a cold L2, quant+GEMM = CUDA-graph replay of both;
median over interleaved groups, mean of two GPUs; speedup = median over
interleaved groups of the per-group previous Cake / this PR ratio, mean
of two GPUs. dtype = GEMM output dtype (quant rows: activation dtype,
`+fold` = output scale folded into the per-token scale); N is `-` on
quant rows.

|kind|K|N|M|dtype|previous Cake µs|this PR µs|speedup|
|---|--:|--:|--:|---|--:|--:|--:|
|GEMM|7168|2112|1|bf16|6.022|5.894|1.022|
|GEMM|7168|2112|1|fp16|6.051|5.906|1.023|
|GEMM|7168|2112|8|bf16|6.061|5.927|1.022|
|GEMM|7168|2112|8|fp16|6.056|5.934|1.022|
|GEMM|7168|2112|17|bf16|6.500|6.505|1.000|
|GEMM|7168|2112|17|fp16|6.504|6.347|1.025|
|GEMM|7168|2112|32|bf16|6.607|6.360|1.040|
|GEMM|7168|2112|32|fp16|6.599|6.348|1.040|
|GEMM|7168|2112|128|bf16|7.869|7.886|0.999|
|GEMM|7168|2112|128|fp16|7.873|7.878|1.001|
|GEMM|7168|2112|130|bf16|7.958|7.959|1.000|
|GEMM|7168|2112|130|fp16|7.957|7.954|1.000|
|GEMM|7168|2112|257|bf16|8.477|8.481|0.999|
|GEMM|7168|2112|257|fp16|8.501|8.499|1.000|
|GEMM|7168|2112|512|bf16|8.656|8.666|1.000|
|GEMM|7168|2112|512|fp16|8.654|8.645|1.001|
|GEMM|7168|2112|2048|bf16|14.67|14.65|1.001|
|GEMM|7168|2112|2048|fp16|14.67|14.67|1.000|
|GEMM|7168|2112|8192|bf16|44.67|44.62|1.001|
|GEMM|7168|2112|8192|fp16|44.68|44.63|1.001|
|GEMM|7168|1536|1|bf16|5.722|5.582|1.025|
|GEMM|7168|1536|1|fp16|5.744|5.593|1.026|
|GEMM|7168|1536|8|bf16|5.755|5.609|1.027|
|GEMM|7168|1536|8|fp16|5.755|5.617|1.025|
|GEMM|7168|1536|17|bf16|5.797|5.808|0.999|
|GEMM|7168|1536|17|fp16|5.804|5.799|1.001|
|GEMM|7168|1536|32|bf16|6.207|6.052|1.027|
|GEMM|7168|1536|32|fp16|6.210|6.203|1.000|
|GEMM|7168|1536|128|bf16|7.634|7.635|1.000|
|GEMM|7168|1536|128|fp16|7.635|7.623|1.000|
|GEMM|7168|1536|130|bf16|7.684|7.700|0.999|
|GEMM|7168|1536|130|fp16|7.699|7.689|1.000|
|GEMM|7168|1536|257|bf16|8.081|8.079|1.001|
|GEMM|7168|1536|257|fp16|8.082|8.078|1.000|
|GEMM|7168|1536|512|bf16|8.238|8.235|1.000|
|GEMM|7168|1536|512|fp16|8.231|8.228|1.000|
|GEMM|7168|1536|2048|bf16|11.98|11.95|1.001|
|GEMM|7168|1536|2048|fp16|12.00|11.99|1.001|
|GEMM|7168|1536|8192|bf16|35.31|35.25|1.001|
|GEMM|7168|1536|8192|fp16|35.29|35.21|1.002|
|GEMM|16384|7168|1|bf16|15.38|15.38|1.000|
|GEMM|16384|7168|1|fp16|15.40|15.37|1.002|
|GEMM|16384|7168|8|bf16|15.38|15.41|0.999|
|GEMM|16384|7168|8|fp16|15.38|15.39|0.999|
|GEMM|16384|7168|17|bf16|16.01|15.60|1.027|
|GEMM|16384|7168|17|fp16|16.02|15.60|1.028|
|GEMM|16384|7168|32|bf16|16.11|15.66|1.027|
|GEMM|16384|7168|32|fp16|16.09|15.66|1.027|
|GEMM|16384|7168|128|bf16|18.21|17.83|1.022|
|GEMM|16384|7168|128|fp16|18.21|17.79|1.025|
|GEMM|16384|7168|130|bf16|19.09|19.11|0.998|
|GEMM|16384|7168|130|fp16|19.09|19.05|1.001|
|GEMM|16384|7168|257|bf16|26.49|26.47|1.000|
|GEMM|16384|7168|257|fp16|26.46|26.46|1.000|
|GEMM|16384|7168|512|bf16|26.99|27.01|1.001|
|GEMM|16384|7168|512|fp16|27.04|26.99|1.001|
|GEMM|16384|7168|2048|bf16|81.57|81.47|1.001|
|GEMM|16384|7168|2048|fp16|81.49|81.39|1.001|
|GEMM|16384|7168|8192|bf16|335.8|335.7|1.000|
|GEMM|16384|7168|8192|fp16|335.4|335.2|1.000|
|GEMM|7168|18432|1|bf16|16.47|16.47|1.000|
|GEMM|7168|18432|1|fp16|16.46|16.49|0.998|
|GEMM|7168|18432|8|bf16|16.48|16.47|1.000|
|GEMM|7168|18432|8|fp16|16.50|16.49|1.001|
|GEMM|7168|18432|17|bf16|16.65|16.65|1.000|
|GEMM|7168|18432|17|fp16|16.66|16.67|0.999|
|GEMM|7168|18432|32|bf16|16.72|16.71|1.000|
|GEMM|7168|18432|32|fp16|16.72|16.72|1.001|
|GEMM|7168|18432|128|bf16|17.69|17.69|1.000|
|GEMM|7168|18432|128|fp16|17.70|17.66|1.002|
|GEMM|7168|18432|130|bf16|18.75|18.75|1.001|
|GEMM|7168|18432|130|fp16|18.76|18.77|0.999|
|GEMM|7168|18432|257|bf16|25.98|25.97|1.001|
|GEMM|7168|18432|257|fp16|25.97|25.97|1.000|
|GEMM|7168|18432|512|bf16|27.03|27.02|1.001|
|GEMM|7168|18432|512|fp16|27.07|27.04|1.001|
|GEMM|7168|18432|2048|bf16|87.06|86.86|1.001|
|GEMM|7168|18432|2048|fp16|86.78|86.66|1.002|
|GEMM|7168|18432|8192|bf16|378.5|378.5|1.000|
|GEMM|7168|18432|8192|fp16|379.8|379.9|1.000|
|GEMM|18432|7168|1|bf16|17.21|17.21|1.000|
|GEMM|18432|7168|1|fp16|17.21|17.20|1.000|
|GEMM|18432|7168|8|bf16|17.24|17.21|1.001|
|GEMM|18432|7168|8|fp16|17.24|17.22|1.001|
|GEMM|18432|7168|17|bf16|18.10|17.67|1.025|
|GEMM|18432|7168|17|fp16|18.09|17.66|1.025|
|GEMM|18432|7168|32|bf16|18.17|17.74|1.024|
|GEMM|18432|7168|32|fp16|18.17|17.74|1.024|
|GEMM|18432|7168|128|bf16|19.80|19.32|1.025|
|GEMM|18432|7168|128|fp16|19.78|19.35|1.023|
|GEMM|18432|7168|130|bf16|20.82|20.82|1.000|
|GEMM|18432|7168|130|fp16|20.82|20.84|0.999|
|GEMM|18432|7168|257|bf16|29.05|29.05|1.000|
|GEMM|18432|7168|257|fp16|29.03|29.01|1.000|
|GEMM|18432|7168|512|bf16|29.54|29.50|1.001|
|GEMM|18432|7168|512|fp16|29.52|29.54|1.000|
|GEMM|18432|7168|2048|bf16|91.01|90.95|1.001|
|GEMM|18432|7168|2048|fp16|90.84|90.74|1.001|
|GEMM|18432|7168|8192|bf16|383.6|383.5|1.000|
|GEMM|18432|7168|8192|fp16|381.3|380.9|1.000|
|GEMM|8192|8192|1|bf16|10.63|10.62|1.002|
|GEMM|8192|8192|1|fp16|10.60|10.61|1.000|
|GEMM|8192|8192|8|bf16|10.61|10.58|1.002|
|GEMM|8192|8192|8|fp16|10.60|10.60|1.002|
|GEMM|8192|8192|17|bf16|10.92|10.92|1.002|
|GEMM|8192|8192|17|fp16|10.93|10.90|1.000|
|GEMM|8192|8192|32|bf16|11.00|11.00|0.999|
|GEMM|8192|8192|32|fp16|10.99|10.97|1.001|
|GEMM|8192|8192|128|bf16|11.76|11.65|1.009|
|GEMM|8192|8192|128|fp16|11.75|11.65|1.009|
|GEMM|8192|8192|130|bf16|12.41|12.41|1.001|
|GEMM|8192|8192|130|fp16|12.37|12.39|1.000|
|GEMM|8192|8192|257|bf16|16.41|16.40|1.001|
|GEMM|8192|8192|257|fp16|16.43|16.43|1.000|
|GEMM|8192|8192|512|bf16|16.68|16.67|1.000|
|GEMM|8192|8192|512|fp16|16.67|16.67|1.001|
|GEMM|8192|8192|2048|bf16|49.05|48.96|1.002|
|GEMM|8192|8192|2048|fp16|49.05|48.99|1.001|
|GEMM|8192|8192|8192|bf16|181.7|181.5|1.001|
|GEMM|8192|8192|8192|fp16|179.2|178.8|1.001|
|GEMM|8192|28672|1|bf16|25.38|25.37|1.001|
|GEMM|8192|28672|1|fp16|25.41|25.45|0.999|
|GEMM|8192|28672|8|bf16|25.43|25.43|1.000|
|GEMM|8192|28672|8|fp16|25.43|25.44|0.999|
|GEMM|8192|28672|17|bf16|25.51|25.53|0.999|
|GEMM|8192|28672|17|fp16|25.51|25.50|1.000|
|GEMM|8192|28672|32|bf16|25.67|25.66|1.000|
|GEMM|8192|28672|32|fp16|25.69|25.69|1.000|
|GEMM|8192|28672|128|bf16|29.70|29.68|1.001|
|GEMM|8192|28672|128|fp16|29.62|29.66|0.999|
|GEMM|8192|28672|130|bf16|32.05|32.05|1.000|
|GEMM|8192|28672|130|fp16|31.87|31.89|1.000|
|GEMM|8192|28672|257|bf16|47.78|47.78|1.000|
|GEMM|8192|28672|257|fp16|47.81|47.82|1.000|
|GEMM|8192|28672|512|bf16|49.72|49.69|1.001|
|GEMM|8192|28672|512|fp16|49.75|49.75|1.000|
|GEMM|8192|28672|2048|bf16|162.8|162.7|1.001|
|GEMM|8192|28672|2048|fp16|164.0|163.7|1.001|
|GEMM|8192|28672|8192|bf16|696.3|697.0|1.000|
|GEMM|8192|28672|8192|fp16|699.2|701.2|1.000|
|GEMM|28672|8192|1|bf16|25.73|25.71|1.000|
|GEMM|28672|8192|1|fp16|25.72|25.72|1.000|
|GEMM|28672|8192|8|bf16|25.75|25.76|1.000|
|GEMM|28672|8192|8|fp16|25.80|25.80|1.001|
|GEMM|28672|8192|17|bf16|26.96|26.54|1.016|
|GEMM|28672|8192|17|fp16|26.97|26.57|1.015|
|GEMM|28672|8192|32|bf16|27.11|26.70|1.015|
|GEMM|28672|8192|32|fp16|27.05|26.65|1.015|
|GEMM|28672|8192|128|bf16|29.35|28.59|1.026|
|GEMM|28672|8192|128|fp16|29.36|28.61|1.026|
|GEMM|28672|8192|130|bf16|30.66|30.69|0.998|
|GEMM|28672|8192|130|fp16|30.69|30.65|1.000|
|GEMM|28672|8192|257|bf16|42.87|42.83|1.000|
|GEMM|28672|8192|257|fp16|42.86|42.83|1.001|
|GEMM|28672|8192|512|bf16|43.75|43.72|1.001|
|GEMM|28672|8192|512|fp16|43.72|43.67|1.001|
|GEMM|28672|8192|2048|bf16|166.1|165.8|1.001|
|GEMM|28672|8192|2048|fp16|166.5|166.2|1.001|
|GEMM|28672|8192|8192|bf16|710.4|715.6|0.999|
|GEMM|28672|8192|8192|fp16|718.5|713.6|1.000|
|quant+GEMM|7168|2112|1|bf16|7.602|7.338|1.035|
|quant+GEMM|7168|2112|1|fp16|7.606|7.366|1.032|
|quant+GEMM|7168|2112|8|bf16|7.630|7.524|1.014|
|quant+GEMM|7168|2112|8|fp16|7.631|7.517|1.014|
|quant+GEMM|7168|2112|17|bf16|8.188|8.178|1.001|
|quant+GEMM|7168|2112|17|fp16|8.170|8.020|1.019|
|quant+GEMM|7168|2112|32|bf16|8.411|8.120|1.037|
|quant+GEMM|7168|2112|32|fp16|8.424|8.137|1.036|
|quant+GEMM|7168|2112|128|bf16|10.02|10.01|1.001|
|quant+GEMM|7168|2112|128|fp16|10.01|10.02|0.999|
|quant+GEMM|7168|2112|130|bf16|10.22|10.19|1.004|
|quant+GEMM|7168|2112|130|fp16|10.22|10.19|1.001|
|quant+GEMM|7168|2112|257|bf16|10.96|10.97|1.001|
|quant+GEMM|7168|2112|257|fp16|10.99|10.95|1.001|
|quant+GEMM|7168|2112|512|bf16|11.77|11.76|1.000|
|quant+GEMM|7168|2112|512|fp16|11.77|11.80|0.998|
|quant+GEMM|7168|2112|2048|bf16|22.30|22.26|1.001|
|quant+GEMM|7168|2112|2048|fp16|22.31|22.27|1.001|
|quant+GEMM|7168|2112|8192|bf16|68.17|68.18|1.000|
|quant+GEMM|7168|2112|8192|fp16|68.25|68.32|0.999|
|quant+GEMM|7168|1536|1|bf16|7.258|7.011|1.035|
|quant+GEMM|7168|1536|1|fp16|7.245|6.986|1.036|
|quant+GEMM|7168|1536|8|bf16|7.302|7.199|1.015|
|quant+GEMM|7168|1536|8|fp16|7.297|7.173|1.018|
|quant+GEMM|7168|1536|17|bf16|7.474|7.472|1.001|
|quant+GEMM|7168|1536|17|fp16|7.471|7.471|0.999|
|quant+GEMM|7168|1536|32|bf16|7.932|7.762|1.021|
|quant+GEMM|7168|1536|32|fp16|7.931|7.913|1.003|
|quant+GEMM|7168|1536|128|bf16|9.807|9.808|0.999|
|quant+GEMM|7168|1536|128|fp16|9.806|9.803|1.000|
|quant+GEMM|7168|1536|130|bf16|9.936|9.918|1.002|
|quant+GEMM|7168|1536|130|fp16|9.916|9.917|1.000|
|quant+GEMM|7168|1536|257|bf16|10.69|10.69|1.001|
|quant+GEMM|7168|1536|257|fp16|10.67|10.67|1.000|
|quant+GEMM|7168|1536|512|bf16|11.41|11.40|1.001|
|quant+GEMM|7168|1536|512|fp16|11.40|11.41|0.999|
|quant+GEMM|7168|1536|2048|bf16|19.56|19.59|0.999|
|quant+GEMM|7168|1536|2048|fp16|19.59|19.59|1.000|
|quant+GEMM|7168|1536|8192|bf16|58.43|58.42|1.000|
|quant+GEMM|7168|1536|8192|fp16|58.37|58.44|1.000|
|quant+GEMM|16384|7168|1|bf16|17.64|17.07|1.035|
|quant+GEMM|16384|7168|1|fp16|17.64|17.07|1.033|
|quant+GEMM|16384|7168|8|bf16|17.72|17.16|1.033|
|quant+GEMM|16384|7168|8|fp16|17.72|17.14|1.033|
|quant+GEMM|16384|7168|17|bf16|18.24|17.54|1.039|
|quant+GEMM|16384|7168|17|fp16|18.27|17.52|1.041|
|quant+GEMM|16384|7168|32|bf16|18.34|17.69|1.037|
|quant+GEMM|16384|7168|32|fp16|18.38|17.71|1.038|
|quant+GEMM|16384|7168|128|bf16|20.63|20.30|1.017|
|quant+GEMM|16384|7168|128|fp16|20.63|20.29|1.016|
|quant+GEMM|16384|7168|130|bf16|21.67|21.70|0.999|
|quant+GEMM|16384|7168|130|fp16|21.69|21.66|1.001|
|quant+GEMM|16384|7168|257|bf16|30.46|30.46|1.000|
|quant+GEMM|16384|7168|257|fp16|30.52|30.51|0.999|
|quant+GEMM|16384|7168|512|bf16|32.78|32.80|1.001|
|quant+GEMM|16384|7168|512|fp16|32.76|32.76|1.000|
|quant+GEMM|16384|7168|2048|bf16|96.63|96.62|1.000|
|quant+GEMM|16384|7168|2048|fp16|96.67|96.57|1.001|
|quant+GEMM|16384|7168|8192|bf16|378.8|379.2|1.000|
|quant+GEMM|16384|7168|8192|fp16|378.6|377.2|1.000|
|quant+GEMM|7168|18432|1|bf16|18.14|18.06|1.005|
|quant+GEMM|7168|18432|1|fp16|18.14|18.06|1.005|
|quant+GEMM|7168|18432|8|bf16|18.24|18.20|1.002|
|quant+GEMM|7168|18432|8|fp16|18.20|18.22|0.999|
|quant+GEMM|7168|18432|17|bf16|18.40|18.36|1.001|
|quant+GEMM|7168|18432|17|fp16|18.38|18.36|1.001|
|quant+GEMM|7168|18432|32|bf16|18.49|18.51|0.999|
|quant+GEMM|7168|18432|32|fp16|18.49|18.50|1.001|
|quant+GEMM|7168|18432|128|bf16|19.60|19.58|1.002|
|quant+GEMM|7168|18432|128|fp16|19.58|19.59|0.999|
|quant+GEMM|7168|18432|130|bf16|20.77|20.76|1.000|
|quant+GEMM|7168|18432|130|fp16|20.75|20.76|1.001|
|quant+GEMM|7168|18432|257|bf16|28.54|28.50|1.003|
|quant+GEMM|7168|18432|257|fp16|28.53|28.51|1.000|
|quant+GEMM|7168|18432|512|bf16|30.06|30.06|0.999|
|quant+GEMM|7168|18432|512|fp16|30.03|30.02|1.001|
|quant+GEMM|7168|18432|2048|bf16|94.50|94.49|1.000|
|quant+GEMM|7168|18432|2048|fp16|94.57|94.54|1.000|
|quant+GEMM|7168|18432|8192|bf16|390.8|391.0|0.999|
|quant+GEMM|7168|18432|8192|fp16|393.4|393.1|1.001|
|quant+GEMM|18432|7168|1|bf16|20.16|19.03|1.059|
|quant+GEMM|18432|7168|1|fp16|20.13|19.03|1.058|
|quant+GEMM|18432|7168|8|bf16|20.24|19.07|1.060|
|quant+GEMM|18432|7168|8|fp16|20.19|19.01|1.062|
|quant+GEMM|18432|7168|17|bf16|20.42|19.64|1.040|
|quant+GEMM|18432|7168|17|fp16|20.41|19.63|1.040|
|quant+GEMM|18432|7168|32|bf16|20.51|19.79|1.037|
|quant+GEMM|18432|7168|32|fp16|20.54|19.79|1.038|
|quant+GEMM|18432|7168|128|bf16|22.27|21.88|1.018|
|quant+GEMM|18432|7168|128|fp16|22.28|21.83|1.021|
|quant+GEMM|18432|7168|130|bf16|23.44|23.42|1.000|
|quant+GEMM|18432|7168|130|fp16|23.49|23.49|1.000|
|quant+GEMM|18432|7168|257|bf16|33.40|33.43|1.000|
|quant+GEMM|18432|7168|257|fp16|33.39|33.40|1.000|
|quant+GEMM|18432|7168|512|bf16|35.93|35.87|1.002|
|quant+GEMM|18432|7168|512|fp16|35.78|35.78|1.000|
|quant+GEMM|18432|7168|2048|bf16|106.8|106.8|1.000|
|quant+GEMM|18432|7168|2048|fp16|106.8|106.8|1.001|
|quant+GEMM|18432|7168|8192|bf16|431.4|431.3|1.000|
|quant+GEMM|18432|7168|8192|fp16|432.1|432.1|1.000|
|quant+GEMM|8192|8192|1|bf16|12.32|12.12|1.016|
|quant+GEMM|8192|8192|1|fp16|12.31|12.10|1.016|
|quant+GEMM|8192|8192|8|bf16|12.28|12.28|1.001|
|quant+GEMM|8192|8192|8|fp16|12.30|12.29|1.000|
|quant+GEMM|8192|8192|17|bf16|12.61|12.60|1.001|
|quant+GEMM|8192|8192|17|fp16|12.60|12.63|0.999|
|quant+GEMM|8192|8192|32|bf16|12.70|12.71|1.000|
|quant+GEMM|8192|8192|32|fp16|12.69|12.72|0.997|
|quant+GEMM|8192|8192|128|bf16|13.66|13.59|1.005|
|quant+GEMM|8192|8192|128|fp16|13.68|13.57|1.009|
|quant+GEMM|8192|8192|130|bf16|14.47|14.47|1.000|
|quant+GEMM|8192|8192|130|fp16|14.48|14.46|1.001|
|quant+GEMM|8192|8192|257|bf16|19.12|19.12|1.001|
|quant+GEMM|8192|8192|257|fp16|19.11|19.13|1.000|
|quant+GEMM|8192|8192|512|bf16|20.12|20.10|1.001|
|quant+GEMM|8192|8192|512|fp16|20.10|20.13|0.999|
|quant+GEMM|8192|8192|2048|bf16|58.13|58.18|0.999|
|quant+GEMM|8192|8192|2048|fp16|58.19|58.13|1.001|
|quant+GEMM|8192|8192|8192|bf16|204.1|204.2|1.000|
|quant+GEMM|8192|8192|8192|fp16|204.4|204.4|1.000|
|quant+GEMM|8192|28672|1|bf16|27.43|27.15|1.010|
|quant+GEMM|8192|28672|1|fp16|27.44|27.10|1.011|
|quant+GEMM|8192|28672|8|bf16|27.43|27.44|1.001|
|quant+GEMM|8192|28672|8|fp16|27.43|27.43|1.003|
|quant+GEMM|8192|28672|17|bf16|27.49|27.49|1.000|
|quant+GEMM|8192|28672|17|fp16|27.49|27.48|1.001|
|quant+GEMM|8192|28672|32|bf16|27.72|27.69|1.001|
|quant+GEMM|8192|28672|32|fp16|27.71|27.69|1.000|
|quant+GEMM|8192|28672|128|bf16|31.49|31.48|1.001|
|quant+GEMM|8192|28672|128|fp16|31.48|31.44|1.002|
|quant+GEMM|8192|28672|130|bf16|33.93|33.92|1.001|
|quant+GEMM|8192|28672|130|fp16|33.92|33.92|1.000|
|quant+GEMM|8192|28672|257|bf16|50.21|50.22|1.000|
|quant+GEMM|8192|28672|257|fp16|50.18|50.20|1.000|
|quant+GEMM|8192|28672|512|bf16|53.05|53.03|1.000|
|quant+GEMM|8192|28672|512|fp16|53.04|53.07|1.000|
|quant+GEMM|8192|28672|2048|bf16|170.9|170.8|1.000|
|quant+GEMM|8192|28672|2048|fp16|172.1|172.0|1.001|
|quant+GEMM|8192|28672|8192|bf16|694.0|695.2|1.001|
|quant+GEMM|8192|28672|8192|fp16|696.2|697.0|1.000|
|quant+GEMM|28672|8192|1|bf16|29.03|27.67|1.048|
|quant+GEMM|28672|8192|1|fp16|29.05|27.69|1.049|
|quant+GEMM|28672|8192|8|bf16|29.18|27.76|1.051|
|quant+GEMM|28672|8192|8|fp16|29.23|27.77|1.053|
|quant+GEMM|28672|8192|17|bf16|29.67|28.66|1.035|
|quant+GEMM|28672|8192|17|fp16|29.69|28.68|1.035|
|quant+GEMM|28672|8192|32|bf16|29.79|28.81|1.033|
|quant+GEMM|28672|8192|32|fp16|29.77|28.81|1.033|
|quant+GEMM|28672|8192|128|bf16|32.19|31.50|1.022|
|quant+GEMM|28672|8192|128|fp16|32.16|31.44|1.023|
|quant+GEMM|28672|8192|130|bf16|33.66|33.64|1.001|
|quant+GEMM|28672|8192|130|fp16|33.62|33.65|0.999|
|quant+GEMM|28672|8192|257|bf16|48.14|48.09|1.001|
|quant+GEMM|28672|8192|257|fp16|48.16|48.17|1.000|
|quant+GEMM|28672|8192|512|bf16|52.39|52.40|0.999|
|quant+GEMM|28672|8192|512|fp16|52.37|52.41|1.000|
|quant+GEMM|28672|8192|2048|bf16|191.8|191.4|0.999|
|quant+GEMM|28672|8192|2048|fp16|191.7|191.7|1.000|
|quant+GEMM|28672|8192|8192|bf16|770.3|770.4|1.000|
|quant+GEMM|28672|8192|8192|fp16|769.9|770.1|1.000|
|quant|7168|-|1|bf16|2.470|2.267|1.088|
|quant|7168|-|1|bf16+fold|2.466|2.278|1.084|
|quant|7168|-|8|bf16|2.477|2.475|0.999|
|quant|7168|-|8|bf16+fold|2.493|2.486|1.000|
|quant|7168|-|17|bf16|2.511|2.517|0.998|
|quant|7168|-|17|bf16+fold|2.520|2.516|0.999|
|quant|7168|-|32|bf16|2.576|2.579|1.000|
|quant|7168|-|32|bf16+fold|2.573|2.581|1.000|
|quant|7168|-|128|bf16|2.884|2.884|1.001|
|quant|7168|-|128|bf16+fold|2.885|2.885|0.999|
|quant|7168|-|130|bf16|2.947|2.948|0.998|
|quant|7168|-|130|bf16+fold|2.945|2.943|1.002|
|quant|7168|-|257|bf16|3.563|3.562|1.000|
|quant|7168|-|257|bf16+fold|3.556|3.557|0.998|
|quant|7168|-|512|bf16|4.641|4.637|1.001|
|quant|7168|-|512|bf16+fold|4.638|4.632|1.001|
|quant|7168|-|2048|bf16|8.987|9.023|0.998|
|quant|7168|-|2048|bf16+fold|9.043|9.018|1.003|
|quant|7168|-|8192|bf16|24.24|24.24|1.000|
|quant|7168|-|8192|bf16+fold|24.24|24.23|0.998|
|quant|8192|-|1|bf16|2.578|2.281|1.129|
|quant|8192|-|1|bf16+fold|2.596|2.284|1.133|
|quant|8192|-|8|bf16|2.531|2.535|1.000|
|quant|8192|-|8|bf16+fold|2.532|2.538|0.998|
|quant|8192|-|17|bf16|2.562|2.559|1.004|
|quant|8192|-|17|bf16+fold|2.573|2.566|1.001|
|quant|8192|-|32|bf16|2.636|2.632|1.000|
|quant|8192|-|32|bf16+fold|2.628|2.639|0.997|
|quant|8192|-|128|bf16|3.002|3.000|0.998|
|quant|8192|-|128|bf16+fold|3.007|3.005|1.000|
|quant|8192|-|130|bf16|3.066|3.073|0.999|
|quant|8192|-|130|bf16+fold|3.073|3.071|0.999|
|quant|8192|-|257|bf16|3.774|3.772|1.001|
|quant|8192|-|257|bf16+fold|3.755|3.751|1.002|
|quant|8192|-|512|bf16|4.939|4.937|1.000|
|quant|8192|-|512|bf16+fold|4.901|4.906|0.999|
|quant|8192|-|2048|bf16|9.851|9.841|1.001|
|quant|8192|-|2048|bf16+fold|9.857|9.865|1.000|
|quant|8192|-|8192|bf16|27.26|27.23|1.001|
|quant|8192|-|8192|bf16+fold|27.25|27.26|1.000|
|quant|16384|-|1|bf16|2.869|2.457|1.169|
|quant|16384|-|1|bf16+fold|2.863|2.442|1.172|
|quant|16384|-|8|bf16|2.962|2.578|1.149|
|quant|16384|-|8|bf16+fold|2.943|2.567|1.147|
|quant|16384|-|17|bf16|3.063|2.645|1.161|
|quant|16384|-|17|bf16+fold|3.058|2.625|1.160|
|quant|16384|-|32|bf16|3.180|2.802|1.138|
|quant|16384|-|32|bf16+fold|3.150|2.782|1.134|
|quant|16384|-|128|bf16|3.881|3.877|1.000|
|quant|16384|-|128|bf16+fold|3.873|3.864|1.000|
|quant|16384|-|130|bf16|4.067|4.057|1.001|
|quant|16384|-|130|bf16+fold|4.037|4.049|0.996|
|quant|16384|-|257|bf16|5.219|5.230|0.999|
|quant|16384|-|257|bf16+fold|5.223|5.220|1.001|
|quant|16384|-|512|bf16|6.992|6.989|1.000|
|quant|16384|-|512|bf16+fold|6.926|6.920|1.000|
|quant|16384|-|2048|bf16|16.05|16.04|0.998|
|quant|16384|-|2048|bf16+fold|16.04|16.01|1.000|
|quant|16384|-|8192|bf16|52.88|52.88|1.000|
|quant|16384|-|8192|bf16+fold|52.89|52.89|1.000|
|quant|18432|-|1|bf16|3.003|2.561|1.173|
|quant|18432|-|1|bf16+fold|3.027|2.552|1.187|
|quant|18432|-|8|bf16|3.068|2.648|1.157|
|quant|18432|-|8|bf16+fold|3.082|2.652|1.163|
|quant|18432|-|17|bf16|3.184|2.712|1.169|
|quant|18432|-|17|bf16+fold|3.206|2.724|1.178|
|quant|18432|-|32|bf16|3.304|2.880|1.146|
|quant|18432|-|32|bf16+fold|3.327|2.887|1.155|
|quant|18432|-|128|bf16|4.099|4.095|1.000|
|quant|18432|-|128|bf16+fold|4.109|4.103|1.003|
|quant|18432|-|130|bf16|4.296|4.286|1.001|
|quant|18432|-|130|bf16+fold|4.285|4.285|1.000|
|quant|18432|-|257|bf16|5.498|5.498|1.001|
|quant|18432|-|257|bf16+fold|5.531|5.521|1.000|
|quant|18432|-|512|bf16|7.364|7.357|1.002|
|quant|18432|-|512|bf16+fold|7.374|7.373|1.001|
|quant|18432|-|2048|bf16|17.57|17.58|0.999|
|quant|18432|-|2048|bf16+fold|17.76|17.72|1.000|
|quant|18432|-|8192|bf16|59.59|59.62|1.000|
|quant|18432|-|8192|bf16+fold|59.67|59.67|0.999|
|quant|28672|-|1|bf16|3.341|2.664|1.254|
|quant|28672|-|1|bf16+fold|3.338|2.685|1.244|
|quant|28672|-|8|bf16|3.467|2.768|1.254|
|quant|28672|-|8|bf16+fold|3.464|2.767|1.247|
|quant|28672|-|17|bf16|3.601|2.874|1.255|
|quant|28672|-|17|bf16+fold|3.593|2.892|1.245|
|quant|28672|-|32|bf16|3.759|3.095|1.215|
|quant|28672|-|32|bf16+fold|3.749|3.102|1.208|
|quant|28672|-|128|bf16|4.934|4.918|1.001|
|quant|28672|-|128|bf16+fold|4.908|4.908|1.001|
|quant|28672|-|130|bf16|5.257|5.263|1.002|
|quant|28672|-|130|bf16+fold|5.250|5.268|0.999|
|quant|28672|-|257|bf16|6.879|6.877|1.000|
|quant|28672|-|257|bf16+fold|6.886|6.881|1.000|
|quant|28672|-|512|bf16|9.659|9.634|1.000|
|quant|28672|-|512|bf16+fold|9.873|9.885|1.000|
|quant|28672|-|2048|bf16|24.89|24.91|1.001|
|quant|28672|-|2048|bf16+fold|25.12|25.14|0.999|
|quant|28672|-|8192|bf16|91.68|91.66|1.000|
|quant|28672|-|8192|bf16+fold|92.01|92.03|1.000|
|quant|7168|-|8|fp16|2.471|2.462|1.002|
|quant|7168|-|17|fp16|2.503|2.517|1.001|
|quant|7168|-|32|fp16|2.559|2.559|1.002|
|quant|7168|-|128|fp16|2.875|2.878|0.999|
|quant|7168|-|130|fp16|2.941|2.934|1.001|
|quant|7168|-|257|fp16|3.534|3.530|1.001|
|quant|7168|-|512|fp16|4.577|4.581|0.999|
|quant|7168|-|2048|fp16|8.902|8.888|1.000|

**NVIDIA GB300 (sm_103a), CUDA 13.4**: latency in µs; GEMM and quant =
kernel time with a cold L2, quant+GEMM = CUDA-graph replay of both;
median over interleaved groups, mean of two GPUs; speedup = median over
interleaved groups of the per-group previous Cake / this PR ratio, mean
of two GPUs. dtype = GEMM output dtype (quant rows: activation dtype,
`+fold` = output scale folded into the per-token scale); N is `-` on
quant rows.

|kind|K|N|M|dtype|previous Cake µs|this PR µs|speedup|
|---|--:|--:|--:|---|--:|--:|--:|
|GEMM|7168|2112|1|bf16|5.856|5.713|1.025|
|GEMM|7168|2112|1|fp16|5.839|5.692|1.026|
|GEMM|7168|2112|8|bf16|5.846|5.699|1.024|
|GEMM|7168|2112|8|fp16|5.852|5.714|1.024|
|GEMM|7168|2112|17|bf16|6.171|5.957|1.036|
|GEMM|7168|2112|17|fp16|6.176|5.960|1.037|
|GEMM|7168|2112|32|bf16|6.273|5.960|1.053|
|GEMM|7168|2112|32|fp16|6.283|5.974|1.050|
|GEMM|7168|2112|128|bf16|7.400|7.410|1.000|
|GEMM|7168|2112|128|fp16|7.399|7.407|0.999|
|GEMM|7168|2112|130|bf16|7.453|7.454|0.999|
|GEMM|7168|2112|130|fp16|7.448|7.456|1.000|
|GEMM|7168|2112|257|bf16|7.950|7.944|1.001|
|GEMM|7168|2112|257|fp16|7.946|7.958|0.999|
|GEMM|7168|2112|512|bf16|8.111|8.129|0.998|
|GEMM|7168|2112|512|fp16|8.140|8.140|1.000|
|GEMM|7168|2112|2048|bf16|13.06|12.54|1.042|
|GEMM|7168|2112|2048|fp16|13.05|12.53|1.040|
|GEMM|7168|2112|8192|bf16|40.56|35.62|1.139|
|GEMM|7168|2112|8192|fp16|40.56|35.60|1.139|
|GEMM|7168|1536|1|bf16|5.437|5.292|1.027|
|GEMM|7168|1536|1|fp16|5.447|5.299|1.028|
|GEMM|7168|1536|8|bf16|5.458|5.317|1.028|
|GEMM|7168|1536|8|fp16|5.466|5.318|1.029|
|GEMM|7168|1536|17|bf16|5.518|5.432|1.016|
|GEMM|7168|1536|17|fp16|5.514|5.424|1.016|
|GEMM|7168|1536|32|bf16|5.794|5.632|1.028|
|GEMM|7168|1536|32|fp16|5.800|5.631|1.029|
|GEMM|7168|1536|128|bf16|7.205|7.214|1.000|
|GEMM|7168|1536|128|fp16|7.218|7.213|1.001|
|GEMM|7168|1536|130|bf16|7.221|7.224|1.000|
|GEMM|7168|1536|130|fp16|7.231|7.221|1.000|
|GEMM|7168|1536|257|bf16|7.559|7.555|1.001|
|GEMM|7168|1536|257|fp16|7.559|7.560|1.000|
|GEMM|7168|1536|512|bf16|7.678|7.691|0.999|
|GEMM|7168|1536|512|fp16|7.697|7.696|1.000|
|GEMM|7168|1536|2048|bf16|10.93|10.76|1.016|
|GEMM|7168|1536|2048|fp16|10.93|10.74|1.018|
|GEMM|7168|1536|8192|bf16|31.90|29.34|1.088|
|GEMM|7168|1536|8192|fp16|31.85|29.30|1.087|
|GEMM|16384|7168|1|bf16|14.78|14.75|1.000|
|GEMM|16384|7168|1|fp16|14.75|14.74|0.999|
|GEMM|16384|7168|8|bf16|14.77|14.75|0.999|
|GEMM|16384|7168|8|fp16|14.77|14.75|1.000|
|GEMM|16384|7168|17|bf16|15.40|15.03|1.025|
|GEMM|16384|7168|17|fp16|15.38|15.02|1.026|
|GEMM|16384|7168|32|bf16|15.46|15.07|1.026|
|GEMM|16384|7168|32|fp16|15.46|15.06|1.026|
|GEMM|16384|7168|128|bf16|17.19|16.80|1.023|
|GEMM|16384|7168|128|fp16|17.19|16.77|1.025|
|GEMM|16384|7168|130|bf16|17.94|17.95|1.000|
|GEMM|16384|7168|130|fp16|17.92|17.94|0.998|
|GEMM|16384|7168|257|bf16|20.89|20.88|1.001|
|GEMM|16384|7168|257|fp16|20.87|20.89|1.000|
|GEMM|16384|7168|512|bf16|21.31|21.32|1.001|
|GEMM|16384|7168|512|fp16|21.27|21.31|0.999|
|GEMM|16384|7168|2048|bf16|64.15|62.23|1.031|
|GEMM|16384|7168|2048|fp16|64.14|62.28|1.030|
|GEMM|16384|7168|8192|bf16|246.1|229.2|1.074|
|GEMM|16384|7168|8192|fp16|246.3|229.0|1.075|
|GEMM|7168|18432|1|bf16|15.81|15.84|0.999|
|GEMM|7168|18432|1|fp16|15.85|15.84|1.000|
|GEMM|7168|18432|8|bf16|15.85|15.82|1.002|
|GEMM|7168|18432|8|fp16|15.84|15.85|1.000|
|GEMM|7168|18432|17|bf16|15.98|15.95|1.002|
|GEMM|7168|18432|17|fp16|15.97|15.97|1.001|
|GEMM|7168|18432|32|bf16|15.99|16.02|0.999|
|GEMM|7168|18432|32|fp16|16.00|16.02|0.999|
|GEMM|7168|18432|128|bf16|16.83|16.83|0.999|
|GEMM|7168|18432|128|fp16|16.83|16.80|1.001|
|GEMM|7168|18432|130|bf16|17.71|17.69|1.001|
|GEMM|7168|18432|130|fp16|17.70|17.69|1.000|
|GEMM|7168|18432|257|bf16|23.79|23.78|1.000|
|GEMM|7168|18432|257|fp16|23.78|23.79|0.999|
|GEMM|7168|18432|512|bf16|24.88|24.86|1.000|
|GEMM|7168|18432|512|fp16|24.87|24.86|1.001|
|GEMM|7168|18432|2048|bf16|77.64|74.03|1.049|
|GEMM|7168|18432|2048|fp16|77.70|74.10|1.049|
|GEMM|7168|18432|8192|bf16|287.6|254.3|1.131|
|GEMM|7168|18432|8192|fp16|288.0|254.6|1.131|
|GEMM|18432|7168|1|bf16|16.47|16.50|0.998|
|GEMM|18432|7168|1|fp16|16.49|16.48|1.001|
|GEMM|18432|7168|8|bf16|16.49|16.50|1.000|
|GEMM|18432|7168|8|fp16|16.50|16.49|1.000|
|GEMM|18432|7168|17|bf16|17.07|16.69|1.022|
|GEMM|18432|7168|17|fp16|17.08|16.67|1.024|
|GEMM|18432|7168|32|bf16|17.14|16.74|1.023|
|GEMM|18432|7168|32|fp16|17.14|16.78|1.023|
|GEMM|18432|7168|128|bf16|18.77|18.34|1.024|
|GEMM|18432|7168|128|fp16|18.78|18.32|1.025|
|GEMM|18432|7168|130|bf16|19.72|19.71|1.001|
|GEMM|18432|7168|130|fp16|19.73|19.71|1.000|
|GEMM|18432|7168|257|bf16|22.99|22.99|1.000|
|GEMM|18432|7168|257|fp16|22.98|22.97|1.001|
|GEMM|18432|7168|512|bf16|23.41|23.41|1.000|
|GEMM|18432|7168|512|fp16|23.49|23.50|1.000|
|GEMM|18432|7168|2048|bf16|71.44|68.84|1.038|
|GEMM|18432|7168|2048|fp16|71.42|68.83|1.038|
|GEMM|18432|7168|8192|bf16|279.8|260.7|1.073|
|GEMM|18432|7168|8192|fp16|279.7|260.7|1.073|
|GEMM|8192|8192|1|bf16|10.24|10.25|1.000|
|GEMM|8192|8192|1|fp16|10.22|10.23|1.000|
|GEMM|8192|8192|8|bf16|10.25|10.23|1.002|
|GEMM|8192|8192|8|fp16|10.24|10.22|1.001|
|GEMM|8192|8192|17|bf16|10.58|10.59|1.000|
|GEMM|8192|8192|17|fp16|10.58|10.57|1.001|
|GEMM|8192|8192|32|bf16|10.62|10.62|1.000|
|GEMM|8192|8192|32|fp16|10.65|10.62|1.002|
|GEMM|8192|8192|128|bf16|11.26|11.12|1.011|
|GEMM|8192|8192|128|fp16|11.26|11.12|1.012|
|GEMM|8192|8192|130|bf16|11.76|11.76|1.000|
|GEMM|8192|8192|130|fp16|11.77|11.74|1.000|
|GEMM|8192|8192|257|bf16|15.12|15.13|1.001|
|GEMM|8192|8192|257|fp16|15.11|15.12|1.000|
|GEMM|8192|8192|512|bf16|15.30|15.31|1.000|
|GEMM|8192|8192|512|fp16|15.32|15.32|1.000|
|GEMM|8192|8192|2048|bf16|44.47|43.82|1.015|
|GEMM|8192|8192|2048|fp16|44.47|43.82|1.015|
|GEMM|8192|8192|8192|bf16|149.1|136.8|1.090|
|GEMM|8192|8192|8192|fp16|149.2|136.8|1.090|
|GEMM|8192|28672|1|bf16|24.64|24.33|1.013|
|GEMM|8192|28672|1|fp16|24.57|24.32|1.011|
|GEMM|8192|28672|8|bf16|24.63|24.33|1.012|
|GEMM|8192|28672|8|fp16|24.66|24.33|1.013|
|GEMM|8192|28672|17|bf16|24.86|24.83|1.001|
|GEMM|8192|28672|17|fp16|24.89|24.94|0.999|
|GEMM|8192|28672|32|bf16|25.01|24.99|1.000|
|GEMM|8192|28672|32|fp16|24.95|25.00|0.998|
|GEMM|8192|28672|128|bf16|27.14|27.13|1.000|
|GEMM|8192|28672|128|fp16|27.17|27.25|0.997|
|GEMM|8192|28672|130|bf16|27.29|27.35|0.998|
|GEMM|8192|28672|130|fp16|27.35|27.36|1.000|
|GEMM|8192|28672|257|bf16|37.07|37.04|1.001|
|GEMM|8192|28672|257|fp16|37.08|37.08|1.000|
|GEMM|8192|28672|512|bf16|39.02|39.07|0.999|
|GEMM|8192|28672|512|fp16|39.07|39.09|1.000|
|GEMM|8192|28672|2048|bf16|130.1|121.3|1.072|
|GEMM|8192|28672|2048|fp16|130.0|121.3|1.072|
|GEMM|8192|28672|8192|bf16|516.1|453.3|1.140|
|GEMM|8192|28672|8192|fp16|519.5|454.5|1.144|
|GEMM|28672|8192|1|bf16|25.19|25.19|1.000|
|GEMM|28672|8192|1|fp16|25.23|25.24|0.999|
|GEMM|28672|8192|8|bf16|25.22|25.24|1.000|
|GEMM|28672|8192|8|fp16|25.27|25.28|0.999|
|GEMM|28672|8192|17|bf16|26.04|25.64|1.014|
|GEMM|28672|8192|17|fp16|26.05|25.71|1.013|
|GEMM|28672|8192|32|bf16|26.11|25.72|1.015|
|GEMM|28672|8192|32|fp16|26.06|25.69|1.014|
|GEMM|28672|8192|128|bf16|28.32|27.56|1.027|
|GEMM|28672|8192|128|fp16|28.33|27.58|1.027|
|GEMM|28672|8192|130|bf16|29.44|29.42|1.000|
|GEMM|28672|8192|130|fp16|29.46|29.47|1.000|
|GEMM|28672|8192|257|bf16|39.45|39.44|1.000|
|GEMM|28672|8192|257|fp16|39.41|39.41|1.000|
|GEMM|28672|8192|512|bf16|40.21|40.19|1.000|
|GEMM|28672|8192|512|fp16|40.17|40.21|0.999|
|GEMM|28672|8192|2048|bf16|140.5|133.3|1.053|
|GEMM|28672|8192|2048|fp16|140.4|133.4|1.053|
|GEMM|28672|8192|8192|bf16|527.1|490.3|1.075|
|GEMM|28672|8192|8192|fp16|523.8|489.5|1.071|
|quant+GEMM|7168|2112|1|bf16|7.368|7.152|1.029|
|quant+GEMM|7168|2112|1|fp16|7.337|7.145|1.028|
|quant+GEMM|7168|2112|8|bf16|7.399|7.222|1.023|
|quant+GEMM|7168|2112|8|fp16|7.386|7.267|1.018|
|quant+GEMM|7168|2112|17|bf16|7.809|7.598|1.029|
|quant+GEMM|7168|2112|17|fp16|7.807|7.613|1.026|
|quant+GEMM|7168|2112|32|bf16|7.982|7.725|1.035|
|quant+GEMM|7168|2112|32|fp16|7.983|7.707|1.035|
|quant+GEMM|7168|2112|128|bf16|9.431|9.426|1.000|
|quant+GEMM|7168|2112|128|fp16|9.444|9.431|1.001|
|quant+GEMM|7168|2112|130|bf16|9.622|9.640|0.997|
|quant+GEMM|7168|2112|130|fp16|9.617|9.622|1.000|
|quant+GEMM|7168|2112|257|bf16|10.34|10.33|1.001|
|quant+GEMM|7168|2112|257|fp16|10.35|10.33|1.001|
|quant+GEMM|7168|2112|512|bf16|11.12|11.11|1.001|
|quant+GEMM|7168|2112|512|fp16|11.10|11.10|1.000|
|quant+GEMM|7168|2112|2048|bf16|20.32|19.66|1.035|
|quant+GEMM|7168|2112|2048|fp16|20.39|19.66|1.037|
|quant+GEMM|7168|2112|8192|bf16|61.78|58.26|1.061|
|quant+GEMM|7168|2112|8192|fp16|61.96|58.38|1.061|
|quant+GEMM|7168|1536|1|bf16|6.967|6.731|1.032|
|quant+GEMM|7168|1536|1|fp16|6.970|6.748|1.033|
|quant+GEMM|7168|1536|8|bf16|6.974|6.852|1.019|
|quant+GEMM|7168|1536|8|fp16|6.990|6.859|1.019|
|quant+GEMM|7168|1536|17|bf16|7.154|7.060|1.011|
|quant+GEMM|7168|1536|17|fp16|7.156|7.053|1.015|
|quant+GEMM|7168|1536|32|bf16|7.528|7.326|1.028|
|quant+GEMM|7168|1536|32|fp16|7.545|7.299|1.031|
|quant+GEMM|7168|1536|128|bf16|9.269|9.289|0.998|
|quant+GEMM|7168|1536|128|fp16|9.275|9.277|1.000|
|quant+GEMM|7168|1536|130|bf16|9.383|9.356|1.002|
|quant+GEMM|7168|1536|130|fp16|9.375|9.384|0.999|
|quant+GEMM|7168|1536|257|bf16|10.09|10.08|1.001|
|quant+GEMM|7168|1536|257|fp16|10.07|10.08|0.997|
|quant+GEMM|7168|1536|512|bf16|10.82|10.80|1.001|
|quant+GEMM|7168|1536|512|fp16|10.81|10.82|1.000|
|quant+GEMM|7168|1536|2048|bf16|18.14|17.83|1.018|
|quant+GEMM|7168|1536|2048|fp16|18.17|17.88|1.015|
|quant+GEMM|7168|1536|8192|bf16|53.25|49.66|1.072|
|quant+GEMM|7168|1536|8192|fp16|53.07|49.58|1.070|
|quant+GEMM|16384|7168|1|bf16|16.87|16.33|1.033|
|quant+GEMM|16384|7168|1|fp16|16.86|16.34|1.030|
|quant+GEMM|16384|7168|8|bf16|16.92|16.51|1.026|
|quant+GEMM|16384|7168|8|fp16|16.92|16.50|1.026|
|quant+GEMM|16384|7168|17|bf16|17.55|16.89|1.039|
|quant+GEMM|16384|7168|17|fp16|17.58|16.87|1.041|
|quant+GEMM|16384|7168|32|bf16|17.70|17.03|1.039|
|quant+GEMM|16384|7168|32|fp16|17.71|17.03|1.040|
|quant+GEMM|16384|7168|128|bf16|19.41|19.05|1.020|
|quant+GEMM|16384|7168|128|fp16|19.46|19.06|1.022|
|quant+GEMM|16384|7168|130|bf16|20.22|20.26|0.999|
|quant+GEMM|16384|7168|130|fp16|20.24|20.26|0.999|
|quant+GEMM|16384|7168|257|bf16|24.02|23.98|1.000|
|quant+GEMM|16384|7168|257|fp16|23.99|24.02|0.999|
|quant+GEMM|16384|7168|512|bf16|26.07|26.08|1.000|
|quant+GEMM|16384|7168|512|fp16|26.12|26.13|0.999|
|quant+GEMM|16384|7168|2048|bf16|78.29|75.76|1.034|
|quant+GEMM|16384|7168|2048|fp16|78.28|75.85|1.032|
|quant+GEMM|16384|7168|8192|bf16|296.1|279.2|1.060|
|quant+GEMM|16384|7168|8192|fp16|295.9|278.9|1.061|
|quant+GEMM|7168|18432|1|bf16|17.41|17.38|1.002|
|quant+GEMM|7168|18432|1|fp16|17.42|17.40|1.001|
|quant+GEMM|7168|18432|8|bf16|17.49|17.47|1.003|
|quant+GEMM|7168|18432|8|fp16|17.50|17.45|1.004|
|quant+GEMM|7168|18432|17|bf16|17.66|17.66|1.000|
|quant+GEMM|7168|18432|17|fp16|17.64|17.65|0.999|
|quant+GEMM|7168|18432|32|bf16|17.75|17.71|1.002|
|quant+GEMM|7168|18432|32|fp16|17.75|17.75|1.000|
|quant+GEMM|7168|18432|128|bf16|18.74|18.76|0.998|
|quant+GEMM|7168|18432|128|fp16|18.80|18.78|1.002|
|quant+GEMM|7168|18432|130|bf16|19.63|19.62|1.001|
|quant+GEMM|7168|18432|130|fp16|19.64|19.65|0.999|
|quant+GEMM|7168|18432|257|bf16|26.15|26.16|0.999|
|quant+GEMM|7168|18432|257|fp16|26.15|26.17|0.999|
|quant+GEMM|7168|18432|512|bf16|27.81|27.79|1.000|
|quant+GEMM|7168|18432|512|fp16|27.85|27.84|1.000|
|quant+GEMM|7168|18432|2048|bf16|84.88|80.93|1.049|
|quant+GEMM|7168|18432|2048|fp16|84.89|81.04|1.047|
|quant+GEMM|7168|18432|8192|bf16|306.7|272.4|1.126|
|quant+GEMM|7168|18432|8192|fp16|307.0|272.9|1.125|
|quant+GEMM|18432|7168|1|bf16|19.35|18.26|1.059|
|quant+GEMM|18432|7168|1|fp16|19.36|18.29|1.059|
|quant+GEMM|18432|7168|8|bf16|19.37|18.35|1.056|
|quant+GEMM|18432|7168|8|fp16|19.41|18.34|1.058|
|quant+GEMM|18432|7168|17|bf16|19.33|18.58|1.041|
|quant+GEMM|18432|7168|17|fp16|19.35|18.63|1.039|
|quant+GEMM|18432|7168|32|bf16|19.53|18.80|1.040|
|quant+GEMM|18432|7168|32|fp16|19.53|18.77|1.040|
|quant+GEMM|18432|7168|128|bf16|21.21|20.72|1.023|
|quant+GEMM|18432|7168|128|fp16|21.23|20.72|1.024|
|quant+GEMM|18432|7168|130|bf16|22.21|22.18|1.001|
|quant+GEMM|18432|7168|130|fp16|22.18|22.23|0.998|
|quant+GEMM|18432|7168|257|bf16|26.34|26.31|1.001|
|quant+GEMM|18432|7168|257|fp16|26.41|26.42|1.000|
|quant+GEMM|18432|7168|512|bf16|28.63|28.69|0.999|
|quant+GEMM|18432|7168|512|fp16|28.65|28.69|0.998|
|quant+GEMM|18432|7168|2048|bf16|87.01|83.75|1.038|
|quant+GEMM|18432|7168|2048|fp16|86.88|83.70|1.038|
|quant+GEMM|18432|7168|8192|bf16|334.7|315.8|1.060|
|quant+GEMM|18432|7168|8192|fp16|334.6|315.9|1.060|
|quant+GEMM|8192|8192|1|bf16|11.92|11.73|1.016|
|quant+GEMM|8192|8192|1|fp16|11.94|11.71|1.020|
|quant+GEMM|8192|8192|8|bf16|11.92|11.92|0.998|
|quant+GEMM|8192|8192|8|fp16|11.89|11.90|1.000|
|quant+GEMM|8192|8192|17|bf16|12.27|12.24|1.003|
|quant+GEMM|8192|8192|17|fp16|12.26|12.26|1.000|
|quant+GEMM|8192|8192|32|bf16|12.34|12.37|1.000|
|quant+GEMM|8192|8192|32|fp16|12.35|12.33|1.001|
|quant+GEMM|8192|8192|128|bf16|13.19|13.06|1.011|
|quant+GEMM|8192|8192|128|fp16|13.22|13.07|1.011|
|quant+GEMM|8192|8192|130|bf16|13.81|13.80|1.000|
|quant+GEMM|8192|8192|130|fp16|13.80|13.81|1.000|
|quant+GEMM|8192|8192|257|bf16|17.63|17.64|1.000|
|quant+GEMM|8192|8192|257|fp16|17.65|17.63|1.001|
|quant+GEMM|8192|8192|512|bf16|18.48|18.50|0.999|
|quant+GEMM|8192|8192|512|fp16|18.46|18.46|1.001|
|quant+GEMM|8192|8192|2048|bf16|52.45|51.72|1.013|
|quant+GEMM|8192|8192|2048|fp16|52.38|51.64|1.014|
|quant+GEMM|8192|8192|8192|bf16|174.3|162.0|1.076|
|quant+GEMM|8192|8192|8192|fp16|174.4|162.1|1.076|
|quant+GEMM|8192|28672|1|bf16|26.55|25.85|1.028|
|quant+GEMM|8192|28672|1|fp16|26.56|25.83|1.030|
|quant+GEMM|8192|28672|8|bf16|26.58|26.12|1.016|
|quant+GEMM|8192|28672|8|fp16|26.50|26.07|1.016|
|quant+GEMM|8192|28672|17|bf16|26.69|26.58|1.005|
|quant+GEMM|8192|28672|17|fp16|26.70|26.62|1.003|
|quant+GEMM|8192|28672|32|bf16|26.87|26.75|1.004|
|quant+GEMM|8192|28672|32|fp16|26.82|26.77|1.002|
|quant+GEMM|8192|28672|128|bf16|28.97|28.99|0.999|
|quant+GEMM|8192|28672|128|fp16|29.09|29.05|1.000|
|quant+GEMM|8192|28672|130|bf16|29.13|29.15|1.000|
|quant+GEMM|8192|28672|130|fp16|29.31|29.28|1.001|
|quant+GEMM|8192|28672|257|bf16|39.42|39.38|1.001|
|quant+GEMM|8192|28672|257|fp16|39.31|39.35|0.999|
|quant+GEMM|8192|28672|512|bf16|42.09|42.13|1.000|
|quant+GEMM|8192|28672|512|fp16|42.12|42.11|1.000|
|quant+GEMM|8192|28672|2048|bf16|137.8|128.8|1.070|
|quant+GEMM|8192|28672|2048|fp16|137.8|128.7|1.071|
|quant+GEMM|8192|28672|8192|bf16|540.6|474.0|1.140|
|quant+GEMM|8192|28672|8192|fp16|541.0|474.6|1.140|
|quant+GEMM|28672|8192|1|bf16|28.20|27.07|1.042|
|quant+GEMM|28672|8192|1|fp16|28.23|27.04|1.044|
|quant+GEMM|28672|8192|8|bf16|28.30|27.14|1.042|
|quant+GEMM|28672|8192|8|fp16|28.26|27.09|1.043|
|quant+GEMM|28672|8192|17|bf16|28.54|27.63|1.034|
|quant+GEMM|28672|8192|17|fp16|28.62|27.64|1.036|
|quant+GEMM|28672|8192|32|bf16|28.79|27.83|1.035|
|quant+GEMM|28672|8192|32|fp16|28.78|27.82|1.035|
|quant+GEMM|28672|8192|128|bf16|31.01|30.31|1.022|
|quant+GEMM|28672|8192|128|fp16|30.99|30.35|1.022|
|quant+GEMM|28672|8192|130|bf16|32.19|32.19|1.001|
|quant+GEMM|28672|8192|130|fp16|32.22|32.22|0.999|
|quant+GEMM|28672|8192|257|bf16|43.71|43.72|0.999|
|quant+GEMM|28672|8192|257|fp16|43.73|43.71|1.000|
|quant+GEMM|28672|8192|512|bf16|47.59|47.58|1.000|
|quant+GEMM|28672|8192|512|fp16|47.62|47.54|1.001|
|quant+GEMM|28672|8192|2048|bf16|162.8|156.1|1.043|
|quant+GEMM|28672|8192|2048|fp16|162.7|156.1|1.042|
|quant+GEMM|28672|8192|8192|bf16|611.9|575.6|1.063|
|quant+GEMM|28672|8192|8192|fp16|610.6|575.2|1.061|
|quant|7168|-|1|bf16|2.399|2.280|1.050|
|quant|7168|-|1|bf16+fold|2.400|2.278|1.055|
|quant|7168|-|8|bf16|2.415|2.417|1.001|
|quant|7168|-|8|bf16+fold|2.428|2.429|1.000|
|quant|7168|-|17|bf16|2.489|2.493|0.998|
|quant|7168|-|17|bf16+fold|2.508|2.504|1.002|
|quant|7168|-|32|bf16|2.557|2.559|0.998|
|quant|7168|-|32|bf16+fold|2.556|2.556|1.000|
|quant|7168|-|128|bf16|2.829|2.825|1.001|
|quant|7168|-|128|bf16+fold|2.835|2.835|1.000|
|quant|7168|-|130|bf16|2.884|2.889|0.999|
|quant|7168|-|130|bf16+fold|2.889|2.885|1.001|
|quant|7168|-|257|bf16|3.468|3.465|1.001|
|quant|7168|-|257|bf16+fold|3.476|3.479|1.000|
|quant|7168|-|512|bf16|4.495|4.502|0.999|
|quant|7168|-|512|bf16+fold|4.501|4.498|1.001|
|quant|7168|-|2048|bf16|8.787|8.762|1.003|
|quant|7168|-|2048|bf16+fold|8.829|8.849|1.000|
|quant|7168|-|8192|bf16|23.84|23.77|1.002|
|quant|7168|-|8192|bf16+fold|23.63|23.63|1.001|
|quant|8192|-|1|bf16|2.507|2.272|1.102|
|quant|8192|-|1|bf16+fold|2.518|2.281|1.105|
|quant|8192|-|8|bf16|2.479|2.486|1.000|
|quant|8192|-|8|bf16+fold|2.494|2.493|1.000|
|quant|8192|-|17|bf16|2.547|2.441|1.045|
|quant|8192|-|17|bf16+fold|2.565|2.457|1.043|
|quant|8192|-|32|bf16|2.636|2.510|1.046|
|quant|8192|-|32|bf16+fold|2.629|2.626|1.003|
|quant|8192|-|128|bf16|2.934|2.937|1.000|
|quant|8192|-|128|bf16+fold|2.946|2.946|1.000|
|quant|8192|-|130|bf16|2.994|3.002|1.000|
|quant|8192|-|130|bf16+fold|3.001|2.995|1.002|
|quant|8192|-|257|bf16|3.657|3.659|1.000|
|quant|8192|-|257|bf16+fold|3.649|3.652|1.000|
|quant|8192|-|512|bf16|4.795|4.802|0.998|
|quant|8192|-|512|bf16+fold|4.779|4.786|0.999|
|quant|8192|-|2048|bf16|9.691|9.673|1.002|
|quant|8192|-|2048|bf16+fold|9.602|9.649|0.997|
|quant|8192|-|8192|bf16|26.68|26.63|1.000|
|quant|8192|-|8192|bf16+fold|26.59|26.60|1.000|
|quant|16384|-|1|bf16|2.794|2.420|1.158|
|quant|16384|-|1|bf16+fold|2.809|2.410|1.164|
|quant|16384|-|8|bf16|2.865|2.529|1.135|
|quant|16384|-|8|bf16+fold|2.863|2.530|1.133|
|quant|16384|-|17|bf16|2.990|2.602|1.148|
|quant|16384|-|17|bf16+fold|2.973|2.596|1.147|
|quant|16384|-|32|bf16|3.104|2.719|1.145|
|quant|16384|-|32|bf16+fold|3.111|2.716|1.142|
|quant|16384|-|128|bf16|3.793|3.795|0.997|
|quant|16384|-|128|bf16+fold|3.796|3.798|1.001|
|quant|16384|-|130|bf16|3.947|3.949|1.000|
|quant|16384|-|130|bf16+fold|3.944|3.941|0.999|
|quant|16384|-|257|bf16|5.033|5.015|1.002|
|quant|16384|-|257|bf16+fold|5.025|5.020|1.001|
|quant|16384|-|512|bf16|6.799|6.786|1.001|
|quant|16384|-|512|bf16+fold|6.759|6.748|1.001|
|quant|16384|-|2048|bf16|15.73|15.76|1.001|
|quant|16384|-|2048|bf16+fold|15.70|15.67|1.001|
|quant|16384|-|8192|bf16|51.39|51.36|1.000|
|quant|16384|-|8192|bf16+fold|51.56|51.58|0.999|
|quant|18432|-|1|bf16|2.896|2.517|1.151|
|quant|18432|-|1|bf16+fold|2.943|2.513|1.172|
|quant|18432|-|8|bf16|2.936|2.617|1.121|
|quant|18432|-|8|bf16+fold|2.986|2.614|1.143|
|quant|18432|-|17|bf16|3.080|2.687|1.143|
|quant|18432|-|17|bf16+fold|3.120|2.696|1.157|
|quant|18432|-|32|bf16|3.205|2.835|1.131|
|quant|18432|-|32|bf16+fold|3.244|2.836|1.142|
|quant|18432|-|128|bf16|3.968|3.963|1.001|
|quant|18432|-|128|bf16+fold|3.995|3.996|1.000|
|quant|18432|-|130|bf16|4.136|4.134|1.002|
|quant|18432|-|130|bf16+fold|4.146|4.156|0.997|
|quant|18432|-|257|bf16|5.332|5.324|1.000|
|quant|18432|-|257|bf16+fold|5.374|5.379|1.001|
|quant|18432|-|512|bf16|7.161|7.168|1.000|
|quant|18432|-|512|bf16+fold|7.193|7.194|1.000|
|quant|18432|-|2048|bf16|17.15|17.18|0.998|
|quant|18432|-|2048|bf16+fold|17.28|17.29|0.998|
|quant|18432|-|8192|bf16|57.81|57.78|1.000|
|quant|18432|-|8192|bf16+fold|58.04|57.94|1.001|
|quant|28672|-|1|bf16|3.235|2.604|1.243|
|quant|28672|-|1|bf16+fold|3.244|2.617|1.242|
|quant|28672|-|8|bf16|3.349|2.726|1.229|
|quant|28672|-|8|bf16+fold|3.358|2.722|1.234|
|quant|28672|-|17|bf16|3.503|2.857|1.226|
|quant|28672|-|17|bf16+fold|3.499|2.850|1.233|
|quant|28672|-|32|bf16|3.678|3.063|1.201|
|quant|28672|-|32|bf16+fold|3.668|3.061|1.198|
|quant|28672|-|128|bf16|4.800|4.803|1.001|
|quant|28672|-|128|bf16+fold|4.814|4.818|0.999|
|quant|28672|-|130|bf16|5.067|5.067|1.001|
|quant|28672|-|130|bf16+fold|5.038|5.053|0.999|
|quant|28672|-|257|bf16|6.635|6.640|0.999|
|quant|28672|-|257|bf16+fold|6.620|6.622|1.000|
|quant|28672|-|512|bf16|9.308|9.324|0.998|
|quant|28672|-|512|bf16+fold|9.617|9.636|0.999|
|quant|28672|-|2048|bf16|24.28|24.30|1.000|
|quant|28672|-|2048|bf16+fold|24.52|24.54|0.999|
|quant|28672|-|8192|bf16|89.15|89.20|0.999|
|quant|28672|-|8192|bf16+fold|89.57|89.54|1.000|
|quant|7168|-|8|fp16|2.407|2.403|0.997|
|quant|7168|-|17|fp16|2.490|2.491|0.999|
|quant|7168|-|32|fp16|2.540|2.539|1.000|
|quant|7168|-|128|fp16|2.815|2.819|1.000|
|quant|7168|-|130|fp16|2.864|2.867|1.000|
|quant|7168|-|257|fp16|3.451|3.448|1.001|
|quant|7168|-|512|fp16|4.467|4.469|1.000|
|quant|7168|-|2048|fp16|8.586|8.630|0.997|

Cake ships no other data type, layout or fused form of this kernel
beyond the variants listed above, and the family ships on sm_100a (B200)
and sm_103a (GB300) only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded NVFP4 per-token quantization and matrix multiplication
support with additional GPU-optimized execution choices for different
input shapes, output types, and hardware.
* Improved handling of long quantization rows through multi-CTA
processing, with specialized paths for select cases.
* Added clearer validation for inputs and launch configurations, with
actionable error messages.
* **Documentation**
* Expanded guidance on kernel selection, row splitting, and tile
choices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [a70a503](https://github.com/flashinfer-ai/flashinfer/commit/a70a503844d94a07fea1f43ab21dab74476d95d4)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-25T21:16:26Z
- **提交信息**: Add standard Blackwell MegaMoE to the next CuTe DSL backend (#7001)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add opt-in NVFP4/NVFP4 and MXFP8/MXFP8 backends from a combined
Blackwell export. Standard inference and GenPhase share the FC12
epilogue and extension, with separate mainloops. Existing backend
defaults and legacy BF16 paths stay in place.

The standard adapter forwards parameterized SwiGLU, bounded or unbounded
SiTU, early or late routing weights, and static, persistent or deferred
finalization. NVFP4 also supports per-token FC1 activation scales and
its existing CAKE finalizer. Invalid routes are masked in BF16 and
quantized combine.

The export also fixes packed routing bounds, missing NVFP4 scale checks,
FC1 scale padding in AOT, and overlapping grid-stride scheduler work.

Select `sm100_nvfp4_nvfp4_bf16_cutedsl_next` or
`sm100_mxfp8_mxfp8_bf16_cutedsl_next`. Source and exporter revisions are
recorded in `VENDOR.md`.

## 🔍 Related Issues

Builds on #6565.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --files ...`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Tested reference correctness, live-token counts, invalid routes,
workspace reuse, AOT execution and CUDA graphs on B200, including EP1,
EP2 and EP4. Affected host tests, pre-commit, export reproduction and
wheel imports pass.

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

Standard inference accepts default or fixed knobs. Online autotuning and
IKET capture remain unavailable through these selectors. Shared input
staging uses the existing implementation.

The GenPhase cache revision is bumped manually for the shared reducer
change. Its default FC2 staging depth is preserved. Performance
measurements and `TUNING.md` updates are deferred.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added standard Blackwell MoE inference support for NVFP4 and MXFP8,
with configurable SwiGLU or SiTU activation and routing-weight
placement.
* Added additional finalization options, including persistent and custom
finalization, plus support for per-token activation scales.
* Expanded support for routing, token communication, and output
reduction across supported configurations.

* **Bug Fixes**
* Improved validation of configurations, inputs, and routing metadata to
catch unsupported settings earlier.
  * Improved handling of invalid routes and padded inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ee50fd0](https://github.com/flashinfer-ai/flashinfer/commit/ee50fd017a835682a83faf3f4ff37d17e1f3d2af)

- **作者**: eigen
- **时间**: 2026-10-25T21:10:37Z
- **提交信息**: perf(cake_kimi_k3_fused_router): faster Kimi-K3 fused router programs on every route for SM100/SM103 (#7355)

`flashinfer.fused_moe.kimi_k3_fused_router` (package
`flashinfer/experimental/kimi_k3_fused_router/`) is FlashInfer's
experimental Kimi-K3 fused MoE router. It takes FP32 gate logits and an
FP32 bias for the Kimi-K3 MoE layer (896 experts, top-16), selects the
top-16 experts per token and builds the expert-aligned route plan (the
`moe_align_block_size` layout) that grouped MoE GEMMs consume, all in
one launch. The router has one data type (FP32 logits and bias) and two
route block alignments (`block_m` 8 and 16). Each architecture has a
dispatch table over 28 measured cells (`num_tokens` 1, 2, 4, ..., 8192 x
`block_m` 8 / 16) that names one generated program per cell, and token
counts between cells are served by a neighbouring cell's program. This
PR regenerates the program for every cell on both sm_100a and sm_103a,
so all 28 cells in both tables change, with the same API and the same
outputs. The baseline, labeled "FlashInfer main" below, is the previous
Cake version of this kernel, which is the set of router programs
FlashInfer main ships today.

NVIDIA GB300 (sm_103a), CUDA 13.4, median kernel latency; speedup =
FlashInfer main / this PR.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
|---:|---:|---:|---:|---:|
| 1 | 8 | 4.11 | 3.71 | 1.11x |
| 1 | 16 | 4.48 | 3.71 | 1.21x |
| 2 | 8 | 5.49 | 3.41 | 1.61x |
| 2 | 16 | 5.71 | 3.42 | 1.67x |
| 4 | 8 | 5.42 | 3.34 | 1.62x |
| 4 | 16 | 5.28 | 3.39 | 1.56x |
| 8 | 8 | 5.57 | 3.42 | 1.63x |
| 8 | 16 | 5.46 | 3.52 | 1.55x |
| 16 | 8 | 5.89 | 3.39 | 1.74x |
| 16 | 16 | 5.73 | 3.36 | 1.70x |
| 32 | 8 | 5.86 | 5.06 | 1.16x |
| 32 | 16 | 5.82 | 5.14 | 1.13x |
| 64 | 8 | 5.98 | 5.23 | 1.14x |
| 64 | 16 | 6.11 | 5.22 | 1.17x |
| 128 | 8 | 6.11 | 5.57 | 1.10x |
| 128 | 16 | 6.30 | 5.50 | 1.15x |
| 256 | 8 | 7.17 | 6.40 | 1.12x |
| 256 | 16 | 7.42 | 6.32 | 1.17x |
| 512 | 8 | 9.25 | 7.49 | 1.24x |
| 512 | 16 | 9.34 | 7.58 | 1.23x |
| 1024 | 8 | 12.64 | 9.79 | 1.29x |
| 1024 | 16 | 12.61 | 9.79 | 1.29x |
| 2048 | 8 | 18.14 | 13.60 | 1.33x |
| 2048 | 16 | 18.16 | 13.47 | 1.35x |
| 4096 | 8 | 25.12 | 17.18 | 1.46x |
| 4096 | 16 | 25.47 | 17.30 | 1.47x |
| 8192 | 8 | 39.36 | 22.88 | 1.72x |
| 8192 | 16 | 40.66 | 22.61 | 1.80x |

NVIDIA B200 (sm_100a), CUDA 13.4; speedup = FlashInfer main / this PR.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
|---:|---:|---:|---:|---:|
| 1 | 8 | 4.35 | 3.90 | 1.11x |
| 1 | 16 | 4.67 | 3.87 | 1.21x |
| 2 | 8 | 5.79 | 3.55 | 1.63x |
| 2 | 16 | 6.02 | 3.58 | 1.68x |
| 4 | 8 | 5.68 | 3.46 | 1.64x |
| 4 | 16 | 5.50 | 3.50 | 1.57x |
| 8 | 8 | 5.79 | 3.55 | 1.63x |
| 8 | 16 | 5.71 | 3.62 | 1.58x |
| 16 | 8 | 6.13 | 3.54 | 1.73x |
| 16 | 16 | 6.00 | 3.50 | 1.71x |
| 32 | 8 | 6.11 | 5.42 | 1.13x |
| 32 | 16 | 6.02 | 5.39 | 1.12x |
| 64 | 8 | 6.21 | 5.47 | 1.13x |
| 64 | 16 | 6.26 | 5.54 | 1.13x |
| 128 | 8 | 6.40 | 5.81 | 1.10x |
| 128 | 16 | 6.56 | 5.82 | 1.13x |
| 256 | 8 | 7.58 | 6.94 | 1.09x |
| 256 | 16 | 7.62 | 6.82 | 1.12x |
| 512 | 8 | 9.79 | 9.12 | 1.07x |
| 512 | 16 | 9.76 | 9.22 | 1.06x |
| 1024 | 8 | 13.44 | 12.32 | 1.09x |
| 1024 | 16 | 13.25 | 12.06 | 1.10x |
| 2048 | 8 | 19.74 | 17.10 | 1.15x |
| 2048 | 16 | 20.22 | 17.17 | 1.18x |
| 4096 | 8 | 26.88 | 18.26 | 1.47x |
| 4096 | 16 | 26.77 | 17.89 | 1.50x |
| 8192 | 8 | 40.34 | 24.00 | 1.68x |
| 8192 | 16 | 40.64 | 23.94 | 1.70x |

Cake ships no other data type, layout or fused form of this router, and
the family ships on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added fused routing support for Kimi K3 models with 896 experts and
top-16 selection.
* Added kernel variants for supported SM100a and SM103a GPU
architectures, with routing outputs including selected expert IDs and
weights, grouped token assignments, and expert counts and offsets.
* Added input and launch validation to report invalid tensor layouts,
types, devices, and launch configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [1cfd731](https://github.com/flashinfer-ai/flashinfer/commit/1cfd731235caaf87fc3b2cc31f5d698ba71d6600)

- **作者**: eigen
- **时间**: 2026-10-25T21:10:02Z
- **提交信息**: feat(cake_qsa_nvfp4): the persistent walk serves compute capability 10.7 within a three-wave bound (#7353)

`cake_qsa_nvfp4` is Cake's QSA NVFP4 sparse paged decode attention
kernel. It has seven program variants:

- `decode` (mma.sync K-first; sm_80, sm_90a, sm_120a)
- `decode_whole_tile` (mma.sync whole-tile issue schedule; sm_80,
sm_120a)
- `decode_coop` (mma.sync fused co-resident split merge; sm_80, sm_90a,
sm_120a)
- `decode_tcgen05` (tcgen05 plain split decode; sm_100a, sm_103a,
sm_107a)
- `decode_tcgen05_coop` (tcgen05 fused; sm_100a, sm_103a, sm_107a)
- `decode_tcgen05_persistent` (persistent balanced tile walk; sm_103a,
sm_107a)
- `merge` (split-KV merge with LSE and gate; all six architectures)

This PR adds the persistent balanced tile walk for compute capability
10.7 (sm_107a). Compute capability 10.7 runs only the split form. The
route picks the persistent walk for split-form calls when the plain grid
needs more than one resident wave but no more than three. All other
calls keep the previous route bit for bit. The baseline is the previous
Cake version of the same route, which is the package on upstream main
before this PR. On compute capability 10.7, that route is the plain
tcgen05 split decode followed by merge. At 128 rows with eager launches,
the speedup is 1.17x for NHD and 1.21x for HND. With CUDA-graph replay,
the same rows show 1.19x and 1.20x. From 1 to 64 rows, the ratios range
from 0.97x to 1.03x.

Eager launches on NVIDIA R200 (212 SMs, sm_107a), CUDA 13.4, torch
2.14.1+cu130 (torch CUDA 13.0). Each value is the whole call (decode +
merge), as the median of 3 x 64 cold-L2 samples with a memset flush, at
24 x 2 heads and 2051 selected tokens per row. The SM clock was not
sampled.

| layout | rows | previous Cake version us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 8.99 | 9.01 | 1.00x |
| NHD | 2 | 9.44 | 9.28 | 1.02x |
| NHD | 4 | 10.21 | 10.22 | 1.00x |
| NHD | 8 | 11.09 | 11.07 | 1.00x |
| NHD | 16 | 13.18 | 13.22 | 1.00x |
| NHD | 32 | 16.30 | 16.34 | 1.00x |
| NHD | 64 | 28.67 | 28.67 | 1.00x |
| NHD | 128 | 54.99 | 47.15 | 1.17x |
| HND | 1 | 8.93 | 8.94 | 1.00x |
| HND | 2 | 9.38 | 9.31 | 1.01x |
| HND | 4 | 10.37 | 10.32 | 1.00x |
| HND | 8 | 11.20 | 11.22 | 1.00x |
| HND | 16 | 13.36 | 13.34 | 1.00x |
| HND | 32 | 16.61 | 16.58 | 1.00x |
| HND | 64 | 28.42 | 28.48 | 1.00x |
| HND | 128 | 55.71 | 46.05 | 1.21x |

CUDA-graph replay of each side's whole call (decode + merge) on NVIDIA
R200 (212 SMs, sm_107a), CUDA 13.4, torch 2.14.1+cu130 (torch CUDA
13.0). Each value is the median of 3 x 64 cold-L2 samples with a memset
flush, at 24 x 2 heads and 2051 selected tokens per row. The SM clock
was not sampled.

| layout | rows | previous Cake version us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 8.51 | 8.74 | 0.97x |
| NHD | 2 | 8.93 | 8.80 | 1.01x |
| NHD | 4 | 10.54 | 10.26 | 1.03x |
| NHD | 8 | 11.20 | 11.04 | 1.01x |
| NHD | 16 | 13.20 | 13.34 | 0.99x |
| NHD | 32 | 16.37 | 16.64 | 0.98x |
| NHD | 64 | 28.78 | 28.75 | 1.00x |
| NHD | 128 | 55.15 | 46.27 | 1.19x |
| HND | 1 | 8.86 | 8.88 | 1.00x |
| HND | 2 | 9.33 | 9.54 | 0.98x |
| HND | 4 | 10.27 | 10.21 | 1.01x |
| HND | 8 | 11.39 | 11.14 | 1.02x |
| HND | 16 | 13.57 | 13.66 | 0.99x |
| HND | 32 | 16.61 | 16.77 | 0.99x |
| HND | 64 | 28.64 | 28.59 | 1.00x |
| HND | 128 | 55.76 | 46.64 | 1.20x |

The other Cake variants of this kernel take BF16 queries and packed E2M1
NVFP4 KV with E4M3 block scales in NHD or HND layout, write BF16 output
with an optional output gate, ship in split (decode + merge) and fused
(cooperative decode alone) forms, and cover sm_80, sm_90a, sm_100a,
sm_103a, sm_107a and sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added persistent-walk support for 10.7 GPUs, including configurations
with two or three waves.
* Expanded supported split configurations for 128- and 256-row workloads
on R200 devices.
* **Bug Fixes**
  * Improved shared-memory descriptor addressing for 10.7 GPUs.
* **Documentation**
* Updated hardware support and configuration guidance for the new GPU
architecture.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ea95347](https://github.com/flashinfer-ai/flashinfer/commit/ea95347ab663fe63997942e157073372c4d7bb22)

- **作者**: eigen
- **时间**: 2026-10-25T20:57:05Z
- **提交信息**: perf(cake_warp_decode): five-deep-ring K256 FC2 and vector finalize for the H4096/E512 rows (#7357)

`cake_warp_decode` is Cake's NVFP4 routed fused-MoE decode for 1 to 32
tokens, called through
`flashinfer.fused_moe.trtllm_fp4_block_scale_routed_moe(...)` with
`CakeWarpDecodeConfig(backend="cake")`. It has one data type (NVFP4
W4A4, BF16 output), five activation variants and one fused form: FC1
with the activation, FC2 and the top-k finalize. This PR adds two
programs, a new FC2 program and a new top-10 finalize program, and
removes the two programs they replace. The FC2 program serves every
1-to-32-token row of `h4096_e512_i256_k10` and `h4096_e512_i512_k10` on
both sm_100a and sm_103a. The finalize program serves the same rows. It
also serves `e512_i1024_k10` (hidden 4096, intermediate 1024, 512
experts, top-10) at 8 to 32 tokens on sm_100a and at 9 to 32 tokens on
sm_103a. In total, 89 rows change on sm_100a (64 + 25) and 88 rows
change on sm_103a (64 + 24). All changed geometries use SwiGLU. All
other rows run the same kernels as FlashInfer main.

The new FC2 program is the same K256 FC2 on the 1-D linear grid, now
with a five-deep work ring. The scheduler claims up to five work items
ahead of the loads instead of three. The per-route-tile metadata
(expert, row limit, output scale) is copied into shared memory once
instead of being loaded for every work item. The new finalize program is
the packed top-10 finalize with four consecutive features per thread. It
issues all route loads before the first add, loads the route weights
before the wait on the preceding kernel, and uses a grid four times
smaller. The summation order is unchanged. On every measured row, the
outputs are bit-identical to the previous version's. Against the
previous Cake version on FlashInfer main, `h4096_e512_i256_k10` runs up
to 1.11x faster on sm_100a and up to 1.10x faster on sm_103a.
`h4096_e512_i512_k10` runs up to 1.05x faster on both. The
`e512_i1024_k10` rows gain about 1 %. On sm_103a, a few small-token
`h4096_e512_i512_k10` rows are within noise. The worst of them has a
ratio of 1.004 (new / previous latency) at 2 tokens with the read flush.

The "memset" and "read" column groups are two cold-L2 modes: before
every call, we flush L2 with a memset of a large buffer or a read of
one.

**sm_100a** (NVIDIA GB200, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake version
(FlashInfer main), new = this PR; ratio = new / previous. **Bold**
num_tokens = rows this PR routes to a new program.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.21|14.28|1.005|12.58|12.55|0.997|
|2|19.10|19.17|1.003|17.15|16.76|0.977|
|3|22.99|22.94|0.998|19.18|19.22|1.002|
|4|26.62|26.49|0.995|21.78|21.90|1.005|
|5|30.36|30.32|0.999|24.80|24.81|1.000|
|6|33.52|33.59|1.002|26.98|26.88|0.996|
|7|36.93|37.03|1.003|29.48|29.26|0.992|
|8|39.77|39.82|1.001|31.31|31.30|0.999|
|9|43.03|43.00|0.999|33.83|34.01|1.005|
|10|46.15|46.23|1.002|36.67|36.50|0.995|
|11|49.50|49.51|1.000|39.09|39.02|0.998|
|12|52.56|52.62|1.001|41.57|41.43|0.997|
|13|56.10|55.79|0.994|44.08|44.24|1.004|
|14|59.31|59.03|0.995|46.58|46.54|0.999|
|15|62.09|62.04|0.999|49.27|49.19|0.998|
|16|65.74|65.58|0.997|51.88|51.80|0.998|
|17|67.58|67.65|1.001|53.84|53.82|1.000|
|18|70.24|70.11|0.998|56.14|56.14|1.000|
|19|72.48|72.43|0.999|58.06|58.03|1.000|
|20|71.66|71.61|0.999|57.27|57.29|1.000|
|21|71.57|71.59|1.000|57.41|57.30|0.998|
|22|71.55|71.62|1.001|57.33|57.43|1.002|
|23|71.53|71.71|1.003|57.27|57.41|1.002|
|24|71.63|71.58|0.999|57.34|57.41|1.001|
|25|71.82|71.75|0.999|57.50|57.46|0.999|
|26|71.96|71.86|0.999|57.46|57.61|1.003|
|27|71.82|71.94|1.002|57.59|57.53|0.999|
|28|71.82|71.96|1.002|57.56|57.65|1.002|
|29|71.95|71.90|0.999|57.59|57.66|1.001|
|30|71.77|71.70|0.999|57.52|57.54|1.000|
|31|71.88|71.92|1.001|57.60|57.66|1.001|
|32|72.77|72.74|1.000|58.42|58.47|1.001|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|17.16|16.78|0.978|15.78|15.66|0.992|
|**2**|22.74|22.70|0.998|21.16|20.94|0.989|
|**3**|26.90|26.22|0.975|24.54|24.00|0.978|
|**4**|33.44|31.69|0.948|30.14|28.69|0.952|
|**5**|37.12|36.06|0.972|33.86|32.81|0.969|
|**6**|42.14|41.23|0.978|38.50|37.47|0.973|
|**7**|46.95|45.84|0.976|42.89|41.47|0.967|
|**8**|51.67|50.34|0.974|47.12|45.44|0.964|
|**9**|56.71|55.65|0.981|51.97|50.39|0.970|
|**10**|61.48|60.14|0.978|56.32|54.30|0.964|
|**11**|65.86|64.92|0.986|60.42|58.89|0.975|
|**12**|70.98|69.40|0.978|65.33|62.74|0.960|
|**13**|75.25|74.06|0.984|69.19|67.51|0.976|
|**14**|80.02|78.76|0.984|73.64|71.54|0.972|
|**15**|84.64|83.53|0.987|77.82|75.87|0.975|
|**16**|89.18|88.10|0.988|82.50|80.32|0.974|
|**17**|93.92|92.98|0.990|86.69|84.33|0.973|
|**18**|98.58|97.48|0.989|91.01|88.63|0.974|
|**19**|102.67|101.83|0.992|94.26|92.48|0.981|
|**20**|106.82|106.41|0.996|98.20|96.66|0.984|
|**21**|111.51|111.19|0.997|102.43|101.12|0.987|
|**22**|116.32|115.82|0.996|106.62|105.15|0.986|
|**23**|120.53|119.86|0.994|110.89|109.06|0.984|
|**24**|124.76|124.25|0.996|115.19|113.05|0.981|
|**25**|129.49|129.05|0.997|119.70|117.37|0.980|
|**26**|133.96|133.65|0.998|123.70|121.67|0.984|
|**27**|138.53|137.99|0.996|127.71|125.43|0.982|
|**28**|142.94|142.49|0.997|131.89|130.30|0.988|
|**29**|147.40|147.02|0.997|136.27|133.78|0.982|
|**30**|151.73|151.48|0.998|140.44|138.33|0.985|
|**31**|156.30|155.90|0.997|144.60|142.02|0.982|
|**32**|160.56|160.47|0.999|148.60|146.66|0.987|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|14.71|14.30|0.972|13.94|13.59|0.975|
|**2**|17.49|16.58|0.948|16.32|15.44|0.946|
|**3**|20.78|19.70|0.948|19.08|18.17|0.952|
|**4**|25.04|22.91|0.915|23.58|21.19|0.899|
|**5**|27.42|25.21|0.919|25.50|23.32|0.914|
|**6**|29.80|27.54|0.924|27.72|25.50|0.920|
|**7**|32.79|30.26|0.923|30.50|28.00|0.918|
|**8**|36.93|33.21|0.899|33.89|30.48|0.899|
|**9**|38.84|35.98|0.926|36.05|33.19|0.921|
|**10**|41.19|38.27|0.929|38.21|35.49|0.929|
|**11**|43.81|40.86|0.933|40.86|38.03|0.931|
|**12**|46.52|43.51|0.935|43.57|40.65|0.933|
|**13**|49.03|45.92|0.937|45.91|42.85|0.933|
|**14**|51.74|48.67|0.941|48.32|45.28|0.937|
|**15**|54.75|51.30|0.937|50.98|47.75|0.937|
|**16**|57.14|53.87|0.943|53.19|50.05|0.941|
|**17**|59.90|56.35|0.941|55.90|52.50|0.939|
|**18**|62.66|59.05|0.942|58.56|54.95|0.938|
|**19**|65.44|61.60|0.941|61.12|57.31|0.938|
|**20**|68.14|63.90|0.938|63.66|59.65|0.937|
|**21**|70.66|66.30|0.938|65.66|61.74|0.940|
|**22**|73.26|69.06|0.943|68.39|64.26|0.940|
|**23**|76.22|71.64|0.940|71.03|66.96|0.943|
|**24**|78.52|73.97|0.942|73.47|69.03|0.940|
|**25**|81.16|76.55|0.943|75.82|71.33|0.941|
|**26**|84.02|79.11|0.942|78.57|74.17|0.944|
|**27**|86.82|81.54|0.939|81.50|76.43|0.938|
|**28**|89.24|84.14|0.943|83.63|78.68|0.941|
|**29**|91.73|86.41|0.942|86.25|80.92|0.938|
|**30**|94.55|88.86|0.940|88.49|83.50|0.944|
|**31**|96.96|91.22|0.941|91.01|85.65|0.941|
|**32**|99.46|93.94|0.944|93.46|88.30|0.945|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.34|16.30|0.998|14.88|14.80|0.995|
|2|21.79|21.82|1.001|19.74|19.86|1.006|
|3|25.66|25.72|1.002|22.87|22.78|0.996|
|4|29.62|29.76|1.005|26.58|26.58|1.000|
|5|34.82|34.86|1.001|31.19|31.14|0.998|
|6|38.86|38.82|0.999|34.93|34.95|1.001|
|7|43.16|43.20|1.001|38.52|38.57|1.001|
|8|47.42|47.47|1.001|42.41|42.39|1.000|
|9|51.38|51.38|1.000|45.95|45.90|0.999|
|10|55.59|55.67|1.001|49.51|49.66|1.003|
|11|59.55|59.52|0.999|53.30|53.32|1.000|
|12|63.50|63.59|1.001|56.76|56.83|1.001|
|13|67.44|67.54|1.001|60.92|60.82|0.998|
|14|71.57|71.47|0.999|64.02|64.10|1.001|
|15|75.48|75.60|1.002|68.09|68.04|0.999|
|16|75.54|75.52|1.000|67.99|67.91|0.999|
|17|75.62|75.57|0.999|67.96|68.10|1.002|
|18|75.70|75.66|1.000|68.02|68.08|1.001|
|19|75.66|75.50|0.998|68.19|68.30|1.002|
|20|75.64|75.64|1.000|68.07|68.07|1.000|
|21|75.56|75.55|1.000|68.22|68.05|0.997|
|22|75.50|75.48|1.000|68.19|68.24|1.001|
|23|75.60|75.54|0.999|68.20|68.12|0.999|
|24|75.62|75.46|0.998|68.02|68.27|1.004|
|25|75.70|75.66|0.999|68.15|68.07|0.999|
|26|75.76|75.70|0.999|68.21|68.36|1.002|
|27|75.81|75.82|1.000|68.10|68.25|1.002|
|28|75.79|75.79|1.000|68.14|68.14|1.000|
|29|75.99|75.70|0.996|68.17|68.37|1.003|
|30|76.08|75.93|0.998|68.01|68.13|1.002|
|31|75.95|75.82|0.998|68.14|68.22|1.001|
|32|75.79|75.81|1.000|68.13|68.24|1.002|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.05|14.06|1.001|13.10|12.94|0.988|
|2|17.02|16.78|0.986|15.14|15.34|1.013|
|3|19.46|19.50|1.002|17.71|17.68|0.998|
|4|21.94|21.98|1.002|20.02|20.08|1.003|
|5|24.36|24.42|1.002|22.26|22.14|0.994|
|6|27.02|26.91|0.996|24.14|24.23|1.004|
|7|29.54|29.58|1.002|26.66|26.66|1.000|
|8|31.56|31.50|0.998|28.36|28.33|0.999|
|9|33.56|33.61|1.001|30.36|30.43|1.002|
|10|35.97|36.08|1.003|32.57|32.58|1.000|
|11|38.26|38.33|1.002|34.56|34.68|1.003|
|12|40.22|40.31|1.002|36.58|36.43|0.996|
|13|42.48|42.31|0.996|38.38|38.46|1.002|
|14|44.47|44.43|0.999|40.18|40.20|1.001|
|15|46.59|46.57|0.999|42.21|42.25|1.001|
|16|46.67|46.47|0.996|42.18|42.13|0.999|
|17|46.71|46.62|0.998|42.46|42.42|0.999|
|18|46.66|46.67|1.000|42.30|42.30|1.000|
|19|46.87|46.90|1.001|42.39|42.55|1.004|
|20|46.65|46.87|1.005|42.36|42.34|0.999|
|21|46.81|46.83|1.001|42.39|42.26|0.997|
|22|46.75|46.65|0.998|42.38|42.38|1.000|
|23|46.82|46.78|0.999|42.34|42.38|1.001|
|24|46.88|46.78|0.998|42.31|42.48|1.004|
|25|46.99|47.02|1.001|42.62|42.56|0.998|
|26|47.06|47.13|1.001|42.66|42.74|1.002|
|27|47.02|47.08|1.001|42.53|42.63|1.002|
|28|47.22|47.04|0.996|42.70|42.70|1.000|
|29|47.03|47.03|1.000|42.57|42.78|1.005|
|30|46.92|46.97|1.001|42.45|42.49|1.001|
|31|46.93|47.20|1.006|42.58|42.79|1.005|
|32|47.07|47.14|1.002|42.58|42.86|1.007|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.26|14.38|1.009|12.80|12.79|0.999|
|2|18.99|19.06|1.003|16.38|16.58|1.013|
|3|21.77|21.74|0.999|18.45|18.35|0.995|
|4|25.62|25.71|1.003|21.21|21.34|1.006|
|5|28.33|28.30|0.999|22.80|22.93|1.006|
|6|31.60|31.68|1.003|25.74|25.66|0.997|
|7|34.34|34.32|1.000|27.22|27.20|0.999|
|8|37.02|37.09|1.002|29.41|29.42|1.001|
|9|39.85|39.90|1.001|31.21|31.18|0.999|
|10|42.66|42.70|1.001|33.81|33.91|1.003|
|11|45.48|45.52|1.001|35.82|35.70|0.996|
|12|48.12|48.27|1.003|38.22|38.34|1.003|
|13|51.02|50.97|0.999|40.14|40.16|1.000|
|14|53.77|53.82|1.001|42.65|42.67|1.001|
|15|56.47|56.41|0.999|44.91|44.78|0.997|
|16|59.02|58.96|0.999|47.23|47.06|0.996|
|17|61.71|61.86|1.002|49.26|49.42|1.003|
|18|64.17|64.30|1.002|51.54|51.75|1.004|
|19|66.54|66.60|1.001|53.75|53.82|1.001|
|20|69.01|69.03|1.000|55.94|56.21|1.005|
|21|71.43|71.29|0.998|58.53|58.40|0.998|
|22|73.68|73.79|1.002|60.44|60.49|1.001|
|23|76.06|76.13|1.001|62.59|62.69|1.002|
|24|78.51|78.50|1.000|64.73|64.89|1.002|
|25|80.92|80.95|1.000|67.35|67.15|0.997|
|26|83.46|83.37|0.999|69.74|69.41|0.995|
|27|85.87|85.89|1.000|71.79|71.83|1.001|
|28|88.24|88.34|1.001|73.90|73.98|1.001|
|29|91.02|90.90|0.999|76.30|76.12|0.998|
|30|93.42|93.56|1.001|78.40|78.54|1.002|
|31|96.02|96.07|1.001|80.77|80.88|1.001|
|32|98.62|98.58|1.000|83.08|82.97|0.999|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.11|13.96|0.989|12.63|12.66|1.003|
|2|17.18|17.06|0.993|15.26|15.19|0.996|
|3|21.10|21.20|1.005|18.06|18.17|1.006|
|4|23.69|23.87|1.008|19.82|19.94|1.006|
|5|27.49|27.45|0.999|22.54|22.44|0.995|
|6|29.97|30.08|1.004|24.05|24.22|1.007|
|7|32.78|32.83|1.001|26.03|26.04|1.000|
|8|35.56|35.55|1.000|28.26|28.31|1.002|
|9|37.78|37.89|1.003|29.68|29.79|1.004|
|10|40.26|40.30|1.001|31.84|31.70|0.996|
|11|42.33|42.38|1.001|32.94|33.06|1.004|
|12|44.15|44.29|1.003|34.58|34.62|1.001|
|13|46.36|46.25|0.998|36.03|36.00|0.999|
|14|48.50|48.53|1.001|37.57|37.62|1.001|
|15|48.86|48.89|1.001|38.56|38.80|1.006|
|16|50.81|50.80|1.000|40.04|40.02|1.000|
|17|52.66|52.62|0.999|41.50|41.47|0.999|
|18|54.61|54.53|0.999|43.34|43.10|0.995|
|19|56.31|56.36|1.001|44.50|44.54|1.001|
|20|58.06|58.05|1.000|45.92|45.92|1.000|
|21|59.78|59.58|0.997|47.12|47.22|1.002|
|22|61.44|61.54|1.002|48.73|48.77|1.001|
|23|63.06|63.10|1.001|50.26|50.16|0.998|
|24|64.74|64.79|1.001|51.50|51.54|1.001|
|25|66.74|66.70|1.000|53.18|53.12|0.999|
|26|68.43|68.42|1.000|54.50|54.54|1.001|
|27|68.36|68.45|1.001|54.51|54.51|1.000|
|28|68.42|68.43|1.000|54.50|54.59|1.002|
|29|68.44|68.43|1.000|54.60|54.59|1.000|
|30|68.49|68.42|0.999|54.65|54.65|1.000|
|31|68.52|68.40|0.998|54.60|54.65|1.001|
|32|68.38|68.47|1.001|54.52|54.74|1.004|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|20.04|19.98|0.997|17.54|17.39|0.991|
|2|25.80|25.70|0.996|21.15|21.00|0.993|
|3|31.12|31.48|1.012|25.13|25.15|1.001|
|4|38.80|38.58|0.994|30.70|30.49|0.993|
|5|43.11|43.15|1.001|33.51|33.74|1.007|
|6|47.90|48.02|1.002|37.51|37.59|1.002|
|7|54.75|54.70|0.999|42.67|42.33|0.992|
|8|59.66|59.73|1.001|46.18|46.44|1.006|
|9|64.46|64.38|0.999|50.19|50.15|0.999|
|10|69.51|69.53|1.000|55.51|55.43|0.999|
|11|73.70|73.61|0.999|59.01|58.98|0.999|
|12|77.96|77.79|0.998|63.07|62.98|0.999|
|13|82.44|82.67|1.003|68.06|68.25|1.003|
|14|86.94|86.60|0.996|72.23|72.43|1.003|
|15|91.22|91.23|1.000|76.34|76.30|0.999|
|16|95.66|95.93|1.003|80.66|81.00|1.004|
|17|100.18|99.94|0.998|85.38|85.35|1.000|
|18|104.56|104.56|1.000|89.56|89.50|0.999|
|19|108.98|108.90|0.999|93.92|94.00|1.001|
|20|113.16|113.18|1.000|98.42|98.26|0.998|
|21|117.66|117.96|1.003|102.25|102.09|0.998|
|22|122.38|122.51|1.001|106.61|106.73|1.001|
|23|126.72|126.54|0.999|111.17|110.85|0.997|
|24|131.15|130.74|0.997|115.22|115.04|0.998|
|25|135.72|135.38|0.997|119.47|119.25|0.998|
|26|140.37|140.26|0.999|124.01|124.01|1.000|
|27|144.65|144.27|0.997|128.30|128.24|1.000|
|28|148.54|149.10|1.004|132.21|132.79|1.004|
|29|153.26|153.18|0.999|136.72|136.92|1.001|
|30|157.53|157.50|1.000|141.26|140.82|0.997|
|31|161.76|161.72|1.000|145.39|145.34|1.000|
|32|166.06|165.90|0.999|149.70|149.50|0.999|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|11.95|11.94|0.999|10.94|10.98|1.003|
|2|14.58|14.48|0.993|13.14|13.22|1.006|
|3|17.00|16.94|0.997|15.17|15.26|1.006|
|4|19.38|19.62|1.012|17.45|17.58|1.007|
|5|21.18|21.34|1.008|18.50|18.28|0.988|
|6|23.19|23.02|0.993|19.58|19.31|0.987|
|7|25.89|25.95|1.002|21.56|21.72|1.007|
|8|27.18|27.36|1.007|22.61|22.53|0.996|
|9|29.02|28.79|0.992|23.54|23.51|0.999|
|10|31.26|30.96|0.991|25.56|25.49|0.997|
|11|32.97|32.72|0.992|26.62|26.72|1.004|
|12|34.45|34.54|1.003|27.62|27.53|0.997|
|13|36.46|36.34|0.997|29.30|29.18|0.996|
|14|37.91|37.87|0.999|30.38|30.42|1.001|
|15|39.89|39.88|1.000|31.26|31.41|1.005|
|16|41.40|41.45|1.001|32.80|32.88|1.002|
|17|43.16|43.11|0.999|34.48|34.51|1.001|
|18|44.70|44.83|1.003|35.54|35.49|0.998|
|19|46.45|46.42|0.999|36.99|37.00|1.000|
|20|47.94|48.07|1.003|38.30|38.06|0.994|
|21|49.56|49.76|1.004|39.73|39.43|0.993|
|22|51.44|51.58|1.003|40.81|40.81|1.000|
|23|53.23|53.22|1.000|42.37|42.29|0.998|
|24|54.76|54.82|1.001|43.48|43.54|1.001|
|25|56.66|56.70|1.001|45.14|45.04|0.998|
|26|58.45|58.48|1.001|46.29|46.43|1.003|
|27|60.02|59.91|0.998|47.72|47.80|1.002|
|28|61.53|61.47|0.999|49.22|49.31|1.002|
|29|62.93|62.92|1.000|50.58|50.71|1.003|
|30|64.18|64.13|0.999|51.78|51.66|0.998|
|31|65.81|65.84|1.000|53.08|53.18|1.002|
|32|67.12|67.16|1.001|54.66|54.69|1.000|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|27.37|27.16|0.992|22.62|22.69|1.003|
|2|40.27|40.26|1.000|32.44|32.37|0.998|
|3|53.32|53.13|0.996|42.11|42.14|1.001|
|4|65.26|65.15|0.998|51.90|51.96|1.001|
|5|77.06|76.87|0.998|62.10|62.12|1.000|
|6|87.30|87.43|1.002|72.35|72.29|0.999|
|7|97.84|98.14|1.003|82.61|82.59|1.000|
|8|108.32|108.30|1.000|92.57|92.57|1.000|
|9|118.83|118.78|1.000|102.66|102.65|1.000|
|10|128.99|128.86|0.999|112.81|112.84|1.000|
|11|138.98|138.99|1.000|122.92|122.72|0.998|
|12|148.91|148.91|1.000|132.14|132.10|1.000|
|13|159.02|158.81|0.999|142.12|141.87|0.998|
|14|168.61|168.48|0.999|151.69|151.63|1.000|
|15|178.41|178.22|0.999|161.46|161.21|0.998|
|16|187.95|188.07|1.001|171.11|170.98|0.999|
|17|195.54|195.46|1.000|178.30|178.40|1.001|
|18|202.45|202.50|1.000|185.47|185.31|0.999|
|19|209.32|209.38|1.000|192.37|192.43|1.000|
|20|209.46|209.38|1.000|192.38|192.40|1.000|
|21|209.50|209.54|1.000|192.62|192.58|1.000|
|22|209.43|209.56|1.001|192.53|192.52|1.000|
|23|209.62|209.55|1.000|192.58|192.73|1.001|
|24|209.50|209.59|1.000|192.66|192.70|1.000|
|25|210.21|210.30|1.000|193.60|193.52|1.000|
|26|210.58|210.27|0.999|193.60|193.66|1.000|
|27|210.34|210.14|0.999|193.66|193.66|1.000|
|28|210.38|210.26|0.999|193.69|193.66|1.000|
|29|210.46|210.26|0.999|193.86|193.89|1.000|
|30|210.46|210.45|1.000|193.75|193.92|1.001|
|31|210.26|210.47|1.001|193.87|193.87|1.000|
|32|210.53|210.41|0.999|193.94|194.13|1.001|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.04|12.98|0.995|11.73|11.74|1.001|
|2|16.51|16.35|0.990|14.47|14.36|0.992|
|3|19.90|19.93|1.002|17.21|17.07|0.992|
|4|22.25|22.06|0.991|18.54|18.29|0.986|
|5|24.90|25.10|1.008|20.95|20.98|1.002|
|6|27.45|27.33|0.996|22.24|22.17|0.997|
|7|29.49|29.63|1.005|23.17|23.13|0.998|
|8|32.22|32.14|0.998|25.52|25.65|1.005|
|9|34.37|34.30|0.998|26.90|26.86|0.999|
|10|36.28|36.55|1.007|28.81|28.90|1.003|
|11|38.81|38.77|0.999|30.29|30.14|0.995|
|12|41.11|41.04|0.998|31.91|32.03|1.004|
|13|43.20|43.26|1.001|33.87|34.02|1.004|
|14|45.33|45.34|1.000|35.53|35.47|0.998|
|15|47.42|47.29|0.997|37.40|37.27|0.997|
|16|48.39|48.41|1.000|38.64|38.54|0.998|
|17|48.39|48.57|1.004|38.54|38.69|1.004|
|18|48.50|48.54|1.001|38.69|38.55|0.996|
|19|48.51|48.49|1.000|38.63|38.65|1.000|
|20|48.57|48.46|0.998|38.51|38.64|1.003|
|21|48.57|48.55|1.000|38.70|38.60|0.997|
|22|48.58|48.60|1.000|38.60|38.83|1.006|
|23|48.50|48.61|1.002|38.50|38.58|1.002|
|24|48.53|48.61|1.002|38.59|38.73|1.004|
|25|48.70|48.98|1.006|38.70|38.74|1.001|
|26|48.81|48.85|1.001|38.70|38.81|1.003|
|27|48.80|48.77|0.999|38.79|38.71|0.998|
|28|48.82|48.80|1.000|38.80|38.79|1.000|
|29|48.70|48.88|1.004|38.74|38.73|1.000|
|30|48.84|48.86|1.000|38.87|38.94|1.002|
|31|48.73|48.84|1.002|38.83|38.89|1.001|
|32|48.64|48.95|1.006|38.85|38.91|1.002|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|25.47|25.41|0.997|21.78|21.74|0.998|
|2|37.49|37.37|0.997|30.64|30.70|1.002|
|3|47.78|47.63|0.997|38.02|38.12|1.003|
|4|58.45|58.42|1.000|45.93|45.94|1.000|
|5|68.46|68.46|1.000|54.59|54.90|1.006|
|6|78.78|78.72|0.999|63.50|63.54|1.001|
|7|87.76|87.74|1.000|72.30|72.26|0.999|
|**8**|97.20|96.44|0.992|81.27|80.86|0.995|
|**9**|106.35|105.63|0.993|90.22|89.49|0.992|
|**10**|115.49|114.44|0.991|98.94|97.94|0.990|
|**11**|124.18|123.05|0.991|107.26|106.13|0.989|
|**12**|132.76|131.82|0.993|115.87|114.82|0.991|
|**13**|141.14|140.18|0.993|124.24|123.25|0.992|
|**14**|149.69|148.32|0.991|132.69|131.44|0.991|
|**15**|158.34|157.15|0.993|141.10|140.10|0.993|
|**16**|166.35|165.18|0.993|149.33|148.17|0.992|
|**17**|175.38|173.94|0.992|158.26|157.04|0.992|
|**18**|183.56|182.38|0.994|166.40|165.47|0.994|
|**19**|191.88|190.81|0.994|174.71|173.74|0.994|
|**20**|200.54|199.34|0.994|183.33|182.03|0.993|
|**21**|208.97|207.66|0.994|191.58|190.57|0.995|
|**22**|217.22|216.20|0.995|199.96|198.91|0.995|
|**23**|225.49|224.37|0.995|208.23|206.98|0.994|
|**24**|234.18|233.03|0.995|216.71|215.56|0.995|
|**25**|242.94|241.83|0.995|225.08|224.29|0.997|
|**26**|251.38|250.34|0.996|233.83|232.72|0.995|
|**27**|259.63|258.83|0.997|242.30|241.14|0.995|
|**28**|268.03|267.17|0.997|250.45|249.58|0.997|
|**29**|276.49|275.45|0.996|258.94|258.00|0.996|
|**30**|284.70|283.97|0.997|267.15|266.42|0.997|
|**31**|292.97|292.07|0.997|275.57|274.62|0.997|
|**32**|301.13|300.23|0.997|283.64|282.68|0.997|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|22.78|22.98|1.009|19.54|19.45|0.995|
|2|33.25|33.31|1.002|26.62|26.63|1.001|
|3|43.26|43.12|0.997|34.18|33.96|0.994|
|4|53.02|53.05|1.000|41.72|41.84|1.003|
|5|62.08|62.17|1.001|48.91|49.06|1.003|
|6|70.78|70.76|1.000|56.70|56.70|1.000|
|7|79.25|79.19|0.999|64.51|64.48|0.999|
|8|87.25|87.24|1.000|72.02|71.93|0.999|
|9|94.94|95.00|1.001|79.66|79.65|1.000|
|10|102.61|102.60|1.000|87.02|87.06|1.000|
|11|110.54|110.59|1.001|94.76|94.70|0.999|
|12|118.28|118.37|1.001|102.23|102.24|1.000|
|13|126.03|126.06|1.000|109.71|109.86|1.001|
|14|133.55|133.52|1.000|117.22|117.22|1.000|
|15|141.21|141.22|1.000|124.70|124.75|1.000|
|16|141.76|141.99|1.002|125.14|125.15|1.000|
|17|142.41|142.16|0.998|125.54|125.66|1.001|
|18|142.38|142.30|0.999|125.62|125.48|0.999|
|19|142.41|142.34|0.999|125.56|125.70|1.001|
|20|142.42|142.35|1.000|125.87|125.77|0.999|
|21|142.38|142.51|1.001|125.78|125.87|1.001|
|22|142.51|142.47|1.000|125.82|125.86|1.000|
|23|142.42|142.70|1.002|125.84|125.88|1.000|
|24|142.72|142.61|0.999|125.91|125.92|1.000|
|25|143.28|143.16|0.999|126.35|126.38|1.000|
|26|143.30|143.20|0.999|126.49|126.42|0.999|
|27|143.02|142.96|1.000|126.17|125.98|0.998|
|28|143.06|143.13|1.000|126.18|126.16|1.000|
|29|143.34|143.44|1.001|126.51|126.52|1.000|
|30|143.04|143.06|1.000|126.31|126.31|1.000|
|31|143.38|143.21|0.999|126.54|126.72|1.001|
|32|143.12|143.14|1.000|126.49|126.39|0.999|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|36.45|36.42|0.999|28.98|28.91|0.998|
|2|52.58|52.54|0.999|40.32|40.10|0.995|
|3|68.04|68.10|1.001|53.34|53.22|0.998|
|4|82.36|82.32|1.000|66.53|66.63|1.002|
|5|94.77|94.66|0.999|78.64|78.79|1.002|
|6|108.47|108.27|0.998|91.94|92.08|1.001|
|7|121.51|121.70|1.002|104.95|104.71|0.998|
|8|134.64|134.68|1.000|117.26|117.49|1.002|
|9|148.42|148.26|0.999|130.24|130.30|1.000|
|10|161.34|161.35|1.000|142.82|142.92|1.001|
|11|173.43|173.60|1.001|155.45|155.54|1.001|
|12|186.07|186.15|1.000|167.88|168.15|1.002|
|13|198.42|198.65|1.001|180.62|180.67|1.000|
|14|211.04|211.07|1.000|193.07|193.23|1.001|
|15|223.42|223.51|1.000|205.81|205.67|0.999|
|16|236.22|235.99|0.999|218.21|217.94|0.999|
|17|250.13|250.31|1.001|232.57|232.66|1.000|
|18|262.70|262.91|1.001|245.25|245.30|1.000|
|19|274.93|275.19|1.001|257.61|257.50|1.000|
|20|283.48|283.42|1.000|265.84|265.86|1.000|
|21|291.70|292.02|1.001|274.12|274.23|1.000|
|22|300.01|299.78|0.999|282.50|282.58|1.000|
|23|308.54|308.52|1.000|290.97|290.82|1.000|
|24|316.86|316.80|1.000|299.36|299.40|1.000|
|25|325.64|325.28|0.999|307.93|308.09|1.001|
|26|333.82|333.92|1.000|316.25|316.29|1.000|
|27|342.30|342.22|1.000|324.76|324.66|1.000|
|28|350.31|350.41|1.000|333.09|333.11|1.000|
|29|358.79|358.70|1.000|341.50|341.45|1.000|
|30|367.35|367.33|1.000|349.81|349.85|1.000|
|31|375.42|375.37|1.000|358.02|358.18|1.000|
|32|383.49|383.81|1.001|366.43|366.44|1.000|

`e256_i2048_k6_clamp10`: hidden 4096, intermediate 2048, 256 experts,
top-6, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.34|24.43|1.004|19.92|19.87|0.998|
|2|37.86|37.68|0.995|29.48|29.55|1.002|
|3|49.98|49.92|0.999|38.45|38.38|0.998|
|4|61.23|61.26|1.001|48.02|47.94|0.998|
|5|72.46|72.43|1.000|58.06|58.05|1.000|
|6|82.49|82.53|1.000|67.22|67.35|1.002|
|7|94.94|94.93|1.000|79.38|79.53|1.002|
|8|104.81|104.86|1.001|89.23|89.18|0.999|
|9|115.81|115.66|0.999|99.90|99.90|1.000|
|10|124.98|124.98|1.000|108.87|108.74|0.999|
|11|133.91|134.06|1.001|117.44|117.60|1.001|
|12|144.30|144.20|0.999|127.17|127.29|1.001|
|13|152.92|152.94|1.000|135.83|135.72|0.999|
|14|163.24|163.23|1.000|145.66|145.69|1.000|
|15|172.78|172.70|1.000|155.25|155.09|0.999|
|16|172.98|172.92|1.000|155.58|155.52|1.000|
|17|173.39|173.38|1.000|155.98|155.87|0.999|
|18|173.50|173.62|1.001|156.08|156.14|1.000|
|19|173.51|173.46|1.000|156.14|156.26|1.001|
|20|173.68|173.79|1.001|156.60|156.70|1.001|
|21|173.88|173.74|0.999|156.70|156.47|0.999|
|22|173.64|173.61|1.000|156.23|156.24|1.000|
|23|172.61|172.85|1.001|155.42|155.71|1.002|
|24|173.74|173.89|1.001|156.29|156.37|1.001|
|25|174.79|174.99|1.001|157.69|157.81|1.001|
|26|174.84|174.85|1.000|157.28|157.20|0.999|
|27|174.88|174.90|1.000|157.22|157.16|1.000|
|28|174.86|175.06|1.001|157.23|157.41|1.001|
|29|175.30|175.24|1.000|158.38|158.26|0.999|
|30|175.35|175.31|1.000|158.67|158.62|1.000|
|31|175.02|175.07|1.000|157.52|157.68|1.001|
|32|174.00|174.05|1.000|156.97|156.72|0.998|

**sm_103a** (NVIDIA GB300, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake version
(FlashInfer main), new = this PR; ratio = new / previous. **Bold**
num_tokens = rows this PR routes to a new program.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.00|13.95|0.997|12.48|12.53|1.004|
|2|18.82|18.69|0.993|16.61|16.52|0.995|
|3|22.38|22.38|1.000|19.10|19.08|0.999|
|4|25.94|26.22|1.010|21.81|21.81|1.000|
|5|30.02|30.21|1.006|24.66|24.81|1.006|
|6|33.36|33.44|1.002|26.88|26.93|1.002|
|7|36.62|36.65|1.001|29.10|29.36|1.009|
|8|35.21|35.34|1.004|31.62|31.60|0.999|
|9|38.80|38.84|1.001|34.80|34.70|0.997|
|10|41.53|41.58|1.001|37.22|37.26|1.001|
|11|44.01|44.09|1.002|39.61|39.58|0.999|
|12|46.54|46.47|0.999|41.84|41.90|1.002|
|13|49.04|49.06|1.000|44.38|44.47|1.002|
|14|51.62|51.56|0.999|46.64|46.71|1.002|
|15|54.64|54.42|0.996|49.22|49.24|1.000|
|16|56.92|57.02|1.002|51.56|51.53|0.999|
|17|59.13|59.24|1.002|53.39|53.58|1.003|
|18|60.98|60.89|0.998|55.02|55.09|1.001|
|19|62.81|62.90|1.001|56.82|56.75|0.999|
|20|63.54|63.45|0.998|56.96|57.00|1.001|
|21|63.82|63.70|0.998|57.44|57.48|1.001|
|22|63.90|63.84|0.999|57.34|57.39|1.001|
|23|63.63|63.44|0.997|57.10|57.13|1.000|
|24|63.43|63.54|1.002|57.04|57.16|1.002|
|25|63.56|63.65|1.001|57.34|57.39|1.001|
|26|63.96|63.88|0.999|57.63|57.53|0.998|
|27|63.91|64.00|1.001|57.60|57.69|1.002|
|28|63.91|63.94|1.000|57.69|57.54|0.997|
|29|64.03|64.10|1.001|57.57|57.78|1.004|
|30|64.09|63.86|0.996|57.62|57.58|0.999|
|31|64.02|64.03|1.000|57.49|57.74|1.004|
|32|64.07|64.03|0.999|57.74|57.79|1.001|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|16.93|16.56|0.978|15.52|15.35|0.989|
|**2**|22.28|22.33|1.002|20.78|20.87|1.004|
|**3**|26.43|25.78|0.975|24.38|23.77|0.975|
|**4**|32.85|31.18|0.949|29.64|28.34|0.956|
|**5**|36.58|35.53|0.971|33.39|32.50|0.973|
|**6**|41.91|40.93|0.977|38.22|37.38|0.978|
|**7**|46.39|45.33|0.977|42.50|41.22|0.970|
|**8**|51.39|50.02|0.973|47.04|45.68|0.971|
|**9**|56.15|55.32|0.985|51.68|50.18|0.971|
|**10**|61.15|59.81|0.978|56.38|54.25|0.962|
|**11**|65.65|64.75|0.986|60.51|58.89|0.973|
|**12**|70.48|69.17|0.981|64.78|62.74|0.969|
|**13**|74.79|74.01|0.990|68.89|67.52|0.980|
|**14**|79.41|78.66|0.991|73.18|71.62|0.979|
|**15**|83.96|83.54|0.995|77.31|76.40|0.988|
|**16**|88.76|88.19|0.994|81.90|80.58|0.984|
|**17**|93.48|92.95|0.994|86.09|84.86|0.986|
|**18**|98.19|97.45|0.992|90.51|88.98|0.983|
|**19**|102.71|101.80|0.991|94.87|93.11|0.981|
|**20**|107.18|106.63|0.995|99.23|97.38|0.981|
|**21**|112.00|111.26|0.993|103.58|101.78|0.983|
|**22**|116.52|115.84|0.994|107.67|105.74|0.982|
|**23**|121.02|120.10|0.992|112.16|109.83|0.979|
|**24**|125.33|124.56|0.994|116.32|114.02|0.980|
|**25**|130.34|129.39|0.993|121.01|118.32|0.978|
|**26**|134.86|133.87|0.993|125.10|122.66|0.980|
|**27**|139.44|138.45|0.993|129.31|126.53|0.978|
|**28**|143.80|142.98|0.994|133.61|131.08|0.981|
|**29**|148.46|147.50|0.993|137.98|134.91|0.978|
|**30**|152.93|152.02|0.994|142.18|139.37|0.980|
|**31**|157.38|156.34|0.993|146.74|143.50|0.978|
|**32**|161.95|160.84|0.993|150.63|147.54|0.979|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|14.40|14.12|0.981|13.70|13.36|0.975|
|**2**|16.99|16.24|0.956|15.87|15.10|0.951|
|**3**|20.39|19.50|0.956|18.99|17.98|0.947|
|**4**|24.30|22.65|0.932|22.87|20.72|0.906|
|**5**|26.69|24.77|0.928|24.96|22.85|0.915|
|**6**|29.19|27.00|0.925|27.18|25.06|0.922|
|**7**|31.99|29.79|0.931|29.56|27.50|0.930|
|**8**|35.46|32.75|0.924|32.82|30.17|0.919|
|**9**|38.28|35.36|0.924|35.49|32.70|0.921|
|**10**|40.49|37.84|0.935|37.78|34.94|0.925|
|**11**|43.34|40.47|0.934|40.36|37.60|0.932|
|**12**|46.26|43.01|0.930|43.18|40.00|0.926|
|**13**|48.74|45.61|0.936|45.53|42.44|0.932|
|**14**|51.27|48.17|0.939|48.00|44.87|0.935|
|**15**|54.16|50.77|0.937|50.46|47.18|0.935|
|**16**|56.78|53.25|0.938|52.75|49.50|0.938|
|**17**|59.34|55.96|0.943|55.43|52.10|0.940|
|**18**|62.29|58.43|0.938|58.06|54.31|0.935|
|**19**|64.94|61.08|0.941|60.52|56.90|0.940|
|**20**|67.69|63.41|0.937|63.24|59.18|0.936|
|**21**|70.20|66.20|0.943|65.72|61.75|0.940|
|**22**|72.74|68.48|0.941|68.13|63.94|0.939|
|**23**|75.69|71.12|0.940|70.84|66.50|0.939|
|**24**|78.10|73.38|0.939|73.18|68.39|0.935|
|**25**|80.87|76.03|0.940|75.66|71.08|0.940|
|**26**|83.51|78.52|0.940|78.44|73.55|0.938|
|**27**|86.36|80.99|0.938|80.98|75.91|0.937|
|**28**|88.78|83.20|0.937|83.48|77.90|0.933|
|**29**|91.50|85.90|0.939|85.83|80.50|0.938|
|**30**|94.27|88.53|0.939|88.41|82.94|0.938|
|**31**|96.70|91.05|0.942|90.95|85.71|0.942|
|**32**|99.14|93.42|0.942|93.36|87.63|0.939|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.14|16.24|1.006|14.66|14.66|1.000|
|2|21.49|21.62|1.006|19.57|19.52|0.998|
|3|25.30|25.22|0.997|22.77|22.88|1.005|
|4|29.25|29.30|1.002|26.54|26.45|0.996|
|5|34.22|34.30|1.003|30.82|30.89|1.002|
|6|38.22|38.30|1.002|34.40|34.38|1.000|
|7|42.68|42.52|0.996|38.35|38.12|0.994|
|8|46.57|46.66|1.002|41.91|41.98|1.002|
|9|50.80|50.71|0.998|45.70|45.74|1.001|
|10|55.17|55.16|1.000|49.74|49.63|0.998|
|11|59.18|59.16|1.000|53.55|53.42|0.998|
|12|62.97|63.18|1.003|56.83|57.06|1.004|
|13|67.29|67.22|0.999|60.90|60.86|0.999|
|14|71.22|71.27|1.001|64.34|64.36|1.000|
|15|75.30|75.51|1.003|68.24|68.44|1.003|
|16|75.38|75.38|1.000|68.14|68.34|1.003|
|17|75.62|75.42|0.997|68.39|68.32|0.999|
|18|75.47|75.49|1.000|68.50|68.34|0.998|
|19|75.61|75.58|1.000|68.41|68.38|1.000|
|20|75.56|75.46|0.999|68.40|68.34|0.999|
|21|75.43|75.56|1.002|68.45|68.45|1.000|
|22|75.50|75.60|1.001|68.53|68.33|0.997|
|23|75.61|75.48|0.998|68.49|68.50|1.000|
|24|75.54|75.52|1.000|68.34|68.41|1.001|
|25|75.66|75.59|0.999|68.53|68.45|0.999|
|26|75.75|75.69|0.999|68.64|68.46|0.997|
|27|75.77|75.62|0.998|68.48|68.52|1.001|
|28|75.70|75.60|0.999|68.54|68.50|1.000|
|29|75.71|75.70|1.000|68.34|68.57|1.003|
|30|75.64|75.75|1.001|68.54|68.34|0.997|
|31|75.64|75.71|1.001|68.41|68.59|1.003|
|32|75.70|75.77|1.001|68.50|68.45|0.999|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.58|13.69|1.008|12.72|12.86|1.011|
|2|16.47|16.44|0.998|15.15|15.09|0.996|
|3|19.03|19.18|1.008|17.18|17.20|1.001|
|4|21.46|21.44|0.999|19.58|19.57|0.999|
|5|23.70|23.58|0.995|21.74|21.61|0.994|
|6|26.06|25.97|0.997|23.74|23.64|0.996|
|7|28.78|28.71|0.997|26.06|26.10|1.001|
|8|30.61|30.63|1.001|27.76|27.82|1.002|
|9|33.05|33.02|0.999|29.92|29.78|0.995|
|10|35.38|35.32|0.998|32.01|31.90|0.997|
|11|37.64|37.50|0.996|34.20|34.10|0.997|
|12|39.62|39.54|0.998|36.02|35.96|0.998|
|13|41.70|41.76|1.002|38.01|37.93|0.998|
|14|43.91|43.88|0.999|39.94|40.10|1.004|
|15|46.10|46.17|1.001|41.95|41.94|1.000|
|16|46.14|46.22|1.002|41.85|41.98|1.003|
|17|46.09|46.08|1.000|42.12|42.14|1.001|
|18|46.13|46.17|1.001|42.03|42.06|1.001|
|19|46.18|46.25|1.001|42.20|42.14|0.999|
|20|46.17|46.23|1.001|42.10|42.01|0.998|
|21|46.10|46.07|0.999|42.08|42.01|0.998|
|22|46.22|46.18|0.999|42.10|41.90|0.995|
|23|46.21|46.01|0.996|42.22|42.02|0.995|
|24|46.16|46.17|1.000|41.99|42.10|1.003|
|25|46.51|46.44|0.998|42.42|42.16|0.994|
|26|46.50|46.49|1.000|42.35|42.32|0.999|
|27|46.57|46.46|0.998|42.44|42.22|0.995|
|28|46.38|46.36|1.000|42.13|42.16|1.001|
|29|46.57|46.59|1.001|42.39|42.26|0.997|
|30|46.50|46.50|1.000|42.37|42.27|0.998|
|31|46.50|46.43|0.998|42.22|42.29|1.002|
|32|46.54|46.43|0.998|42.15|42.12|0.999|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.96|13.98|1.002|12.70|12.77|1.006|
|2|18.56|18.46|0.995|16.30|16.34|1.002|
|3|21.42|21.50|1.004|18.24|18.21|0.998|
|4|25.53|25.69|1.006|21.50|21.52|1.001|
|5|27.96|28.17|1.007|22.74|22.78|1.002|
|6|31.58|31.65|1.002|25.67|25.51|0.994|
|7|34.06|34.02|0.999|27.11|27.07|0.999|
|8|37.00|37.17|1.005|29.18|29.14|0.998|
|9|39.73|39.55|0.996|31.15|31.22|1.002|
|10|42.45|42.56|1.003|33.68|33.73|1.001|
|11|45.23|45.19|0.999|35.94|35.74|0.994|
|12|47.80|47.94|1.003|38.16|38.16|1.000|
|13|50.64|50.57|0.999|40.34|40.30|0.999|
|14|53.46|53.46|1.000|42.47|42.50|1.001|
|15|56.36|56.27|0.998|44.97|44.83|0.997|
|16|58.84|58.84|1.000|47.18|47.12|0.999|
|17|61.24|61.30|1.001|49.46|49.58|1.002|
|18|63.74|63.88|1.002|51.59|51.74|1.003|
|19|66.26|66.31|1.001|53.90|53.79|0.998|
|20|68.77|68.88|1.002|56.19|56.18|1.000|
|21|71.36|71.30|0.999|58.46|58.44|1.000|
|22|73.49|73.72|1.003|60.75|60.74|1.000|
|23|76.02|76.06|1.001|62.86|62.95|1.001|
|24|78.73|78.70|1.000|65.22|65.27|1.001|
|25|80.90|81.06|1.002|67.62|67.30|0.995|
|26|83.34|83.32|1.000|70.06|69.90|0.998|
|27|85.61|85.80|1.002|72.03|72.31|1.004|
|28|88.17|88.20|1.000|74.35|74.35|1.000|
|29|90.84|90.62|0.998|76.71|76.62|0.999|
|30|93.18|93.29|1.001|78.95|79.11|1.002|
|31|95.86|95.76|0.999|81.38|81.29|0.999|
|32|98.26|98.14|0.999|83.57|83.39|0.998|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.12|13.15|1.002|11.79|11.82|1.003|
|2|16.67|16.58|0.995|14.73|14.81|1.005|
|3|20.53|20.63|1.005|17.64|17.56|0.995|
|4|23.27|23.38|1.004|19.91|19.68|0.988|
|5|26.50|26.45|0.998|21.34|21.30|0.999|
|6|29.43|29.33|0.996|23.23|23.26|1.001|
|7|32.28|32.23|0.999|25.38|25.34|0.998|
|8|34.77|34.72|0.999|27.14|27.27|1.005|
|9|37.50|37.31|0.995|29.09|28.90|0.993|
|10|40.05|40.10|1.001|30.96|30.98|1.001|
|11|41.26|41.40|1.003|33.26|33.25|1.000|
|12|43.38|43.38|1.000|35.19|35.34|1.004|
|13|45.29|45.30|1.000|36.78|36.79|1.000|
|14|47.10|47.23|1.003|38.33|38.38|1.001|
|15|49.33|49.28|0.999|40.42|40.41|1.000|
|16|50.85|50.96|1.002|41.43|41.53|1.002|
|17|52.94|52.83|0.998|42.85|42.67|0.996|
|18|54.63|54.63|1.000|44.23|44.26|1.001|
|19|56.45|56.38|0.999|45.33|45.42|1.002|
|20|58.26|58.19|0.999|46.58|46.62|1.001|
|21|60.06|60.10|1.001|48.02|48.13|1.002|
|22|61.98|62.00|1.000|49.70|49.73|1.001|
|23|63.57|63.62|1.001|50.93|50.84|0.998|
|24|65.39|65.18|0.997|52.36|52.35|1.000|
|25|67.25|67.31|1.001|54.10|54.08|1.000|
|26|69.07|68.99|0.999|55.55|55.53|1.000|
|27|69.08|69.05|1.000|55.58|55.45|0.998|
|28|69.06|69.04|1.000|55.50|55.56|1.001|
|29|68.98|69.02|1.001|55.49|55.53|1.001|
|30|69.00|69.03|1.000|55.56|55.62|1.001|
|31|69.04|69.12|1.001|55.66|55.52|0.997|
|32|68.99|69.02|1.000|55.62|55.62|1.000|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|20.06|20.05|0.999|17.74|17.62|0.993|
|2|25.90|25.88|0.999|21.13|21.14|1.000|
|3|31.40|31.27|0.996|25.44|25.54|1.004|
|4|38.81|38.78|0.999|30.94|31.01|1.002|
|5|43.50|43.90|1.009|34.26|34.58|1.009|
|6|48.48|48.42|0.999|38.50|38.04|0.988|
|7|55.18|55.30|1.002|43.66|43.64|0.999|
|8|59.93|59.81|0.998|47.00|47.11|1.002|
|9|64.54|64.50|0.999|51.06|51.08|1.000|
|10|69.76|69.92|1.002|56.22|56.41|1.003|
|11|74.39|74.29|0.999|60.37|60.61|1.004|
|12|78.62|78.56|0.999|64.79|64.63|0.998|
|13|83.58|83.52|0.999|69.49|69.42|0.999|
|14|88.18|88.26|1.001|73.91|73.96|1.001|
|15|92.39|92.31|0.999|78.02|78.12|1.001|
|16|97.38|97.08|0.997|82.90|82.88|1.000|
|17|101.64|101.50|0.999|87.18|87.27|1.001|
|18|105.55|106.04|1.005|91.49|91.57|1.001|
|19|111.27|111.54|1.002|96.34|96.40|1.001|
|20|115.18|115.28|1.001|100.42|100.31|0.999|
|21|119.84|120.08|1.002|104.74|104.96|1.002|
|22|124.67|124.97|1.002|109.18|109.36|1.002|
|23|129.17|129.32|1.001|113.53|113.50|1.000|
|24|133.78|133.78|1.000|117.82|118.15|1.003|
|25|138.05|138.36|1.002|122.43|122.78|1.003|
|26|143.09|142.62|0.997|127.07|126.66|0.997|
|27|147.32|147.11|0.999|131.29|131.05|0.998|
|28|151.50|151.52|1.000|135.78|135.61|0.999|
|29|156.26|155.93|0.998|140.36|140.06|0.998|
|30|160.59|160.30|0.998|144.56|144.35|0.999|
|31|165.02|164.60|0.997|149.14|148.83|0.998|
|32|168.82|169.46|1.004|153.19|153.38|1.001|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.09|12.06|0.998|10.92|11.02|1.010|
|2|14.47|14.51|1.003|13.17|13.18|1.001|
|3|16.86|16.77|0.994|14.98|14.90|0.995|
|4|19.53|19.54|1.000|17.17|17.55|1.022|
|5|21.29|21.30|1.000|18.03|18.03|1.000|
|6|23.20|23.22|1.001|19.20|19.33|1.007|
|7|25.46|25.42|0.998|21.44|21.52|1.004|
|8|27.46|27.54|1.003|22.50|22.63|1.006|
|9|29.23|29.28|1.002|23.78|23.86|1.004|
|10|31.14|31.28|1.004|25.74|25.66|0.997|
|11|33.01|33.02|1.000|26.82|26.93|1.004|
|12|34.74|34.82|1.002|27.81|27.94|1.005|
|13|36.69|36.67|1.000|29.78|29.77|1.000|
|14|38.18|38.36|1.005|30.62|30.87|1.008|
|15|39.96|39.96|1.000|32.12|32.30|1.005|
|16|41.66|41.74|1.002|33.33|33.39|1.002|
|17|43.57|43.33|0.994|35.07|34.95|0.997|
|18|45.01|45.06|1.001|36.22|36.18|0.999|
|19|46.94|46.80|0.997|37.62|37.68|1.002|
|20|48.73|48.62|0.998|39.26|39.23|0.999|
|21|50.41|50.24|0.997|40.58|40.48|0.998|
|22|52.28|52.20|0.998|41.98|41.89|0.998|
|23|54.13|54.01|0.998|43.25|43.10|0.997|
|24|55.71|55.68|0.999|44.68|44.79|1.003|
|25|57.38|57.26|0.998|46.14|46.18|1.001|
|26|58.81|58.80|1.000|47.58|47.66|1.002|
|27|60.28|60.28|1.000|48.69|48.67|1.000|
|28|61.97|61.89|0.999|50.37|50.26|0.998|
|29|63.80|63.82|1.000|51.70|51.66|0.999|
|30|65.26|65.25|1.000|53.17|53.11|0.999|
|31|66.90|66.88|1.000|54.42|54.45|1.000|
|32|68.66|68.54|0.998|55.83|56.02|1.003|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|26.82|26.74|0.997|22.46|22.42|0.998|
|2|40.75|40.77|1.000|32.61|32.62|1.000|
|3|54.37|54.18|0.997|42.82|42.82|1.000|
|4|66.03|66.13|1.001|52.96|52.99|1.001|
|5|77.51|77.50|1.000|63.64|63.37|0.996|
|6|88.44|88.52|1.001|74.23|74.05|0.998|
|7|99.38|99.23|0.999|84.57|84.22|0.996|
|8|110.23|110.26|1.000|94.83|95.06|1.002|
|9|120.71|120.77|1.000|105.20|105.29|1.001|
|10|131.14|131.23|1.001|115.64|115.67|1.000|
|11|141.11|141.14|1.000|125.22|125.26|1.000|
|12|151.22|151.34|1.001|135.24|135.26|1.000|
|13|161.42|161.33|0.999|145.39|145.39|1.000|
|14|171.54|171.44|0.999|155.44|155.59|1.001|
|15|181.52|181.57|1.000|165.39|165.39|1.000|
|16|191.34|191.31|1.000|175.38|175.35|1.000|
|17|199.24|199.17|1.000|183.27|183.06|0.999|
|18|206.46|206.28|0.999|190.42|190.37|1.000|
|19|213.34|213.52|1.001|197.47|197.46|1.000|
|20|213.47|213.48|1.000|197.50|197.44|1.000|
|21|213.55|213.43|0.999|197.58|197.65|1.000|
|22|213.44|213.75|1.001|197.58|197.63|1.000|
|23|213.54|213.52|1.000|197.77|197.92|1.001|
|24|213.74|213.80|1.000|197.79|197.89|1.000|
|25|214.34|214.30|1.000|198.76|198.60|0.999|
|26|214.31|214.26|1.000|198.65|198.66|1.000|
|27|214.43|214.38|1.000|198.82|198.47|0.998|
|28|214.59|214.15|0.998|198.93|198.59|0.998|
|29|214.68|214.59|1.000|198.88|198.85|1.000|
|30|214.58|214.55|1.000|198.90|198.94|1.000|
|31|214.63|214.65|1.000|199.05|198.93|0.999|
|32|214.51|214.53|1.000|199.17|199.02|0.999|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.81|12.79|0.999|11.58|11.52|0.995|
|2|16.07|16.03|0.998|14.53|14.42|0.992|
|3|19.26|19.31|1.002|16.86|16.91|1.003|
|4|21.28|21.34|1.003|18.20|18.39|1.011|
|5|24.65|24.82|1.007|21.04|21.15|1.005|
|6|26.68|26.65|0.999|22.02|22.10|1.004|
|7|29.02|28.94|0.997|23.58|23.49|0.996|
|8|32.20|31.97|0.993|25.39|25.39|1.000|
|9|33.91|34.00|1.003|26.66|26.84|1.007|
|10|36.16|36.38|1.006|28.64|28.52|0.996|
|11|38.36|38.22|0.996|30.10|30.04|0.998|
|12|40.65|40.90|1.006|32.01|32.10|1.003|
|13|42.86|42.60|0.994|33.70|33.69|1.000|
|14|44.94|44.98|1.001|35.49|35.50|1.000|
|15|47.10|47.15|1.001|37.27|37.30|1.001|
|16|48.06|48.26|1.004|38.49|38.60|1.003|
|17|48.46|48.42|0.999|38.77|38.84|1.002|
|18|48.40|48.54|1.003|38.70|38.74|1.001|
|19|48.38|48.40|1.000|38.74|38.76|1.001|
|20|48.28|48.41|1.003|38.83|38.94|1.003|
|21|48.49|48.39|0.998|38.80|38.70|0.998|
|22|48.52|48.43|0.998|38.86|38.86|1.000|
|23|48.38|48.43|1.001|38.79|38.97|1.005|
|24|48.47|48.46|1.000|38.74|38.83|1.002|
|25|48.50|48.43|0.999|38.94|38.83|0.997|
|26|48.46|48.51|1.001|38.95|39.01|1.001|
|27|48.77|48.63|0.997|38.95|38.90|0.999|
|28|48.50|48.64|1.003|39.05|38.99|0.999|
|29|48.61|48.62|1.000|39.12|38.87|0.994|
|30|48.58|48.58|1.000|38.96|38.93|0.999|
|31|48.56|48.68|1.002|38.98|38.96|1.000|
|32|48.45|48.50|1.001|39.11|38.79|0.992|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.75|24.91|1.006|21.54|21.52|0.999|
|2|36.79|36.84|1.001|30.18|30.36|1.006|
|3|47.75|47.70|0.999|38.45|38.51|1.002|
|4|58.85|58.87|1.000|47.14|47.26|1.003|
|5|68.85|68.91|1.001|56.10|56.20|1.002|
|6|79.17|79.02|0.998|65.39|65.49|1.001|
|7|88.15|87.90|0.997|74.54|74.49|0.999|
|8|97.67|97.46|0.998|82.91|82.70|0.997|
|**9**|106.17|105.69|0.995|91.01|90.32|0.992|
|**10**|115.38|114.49|0.992|99.78|98.68|0.989|
|**11**|124.16|123.30|0.993|108.30|107.36|0.991|
|**12**|132.75|131.70|0.992|116.88|115.74|0.990|
|**13**|141.46|140.30|0.992|125.66|124.57|0.991|
|**14**|150.02|148.60|0.991|134.03|132.66|0.990|
|**15**|158.52|157.32|0.992|142.65|141.34|0.991|
|**16**|166.70|165.57|0.993|150.86|149.73|0.992|
|**17**|175.59|174.43|0.993|159.85|158.65|0.992|
|**18**|184.22|182.95|0.993|168.34|167.22|0.993|
|**19**|192.46|191.44|0.995|176.62|175.57|0.994|
|**20**|200.99|199.97|0.995|185.30|184.25|0.994|
|**21**|209.54|208.25|0.994|193.58|192.67|0.995|
|**22**|218.14|217.00|0.995|202.10|201.13|0.995|
|**23**|226.74|225.38|0.994|210.78|209.46|0.994|
|**24**|235.18|234.09|0.995|219.34|218.10|0.994|
|**25**|244.09|243.06|0.996|228.10|226.98|0.995|
|**26**|252.58|251.76|0.997|236.69|235.59|0.995|
|**27**|261.28|260.04|0.995|245.18|244.03|0.995|
|**28**|269.62|268.78|0.997|253.77|252.69|0.996|
|**29**|278.36|277.19|0.996|262.18|261.14|0.996|
|**30**|286.86|285.89|0.997|270.62|269.67|0.996|
|**31**|295.03|294.06|0.997|279.03|277.96|0.996|
|**32**|303.24|302.12|0.996|287.15|286.16|0.997|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|22.65|22.61|0.998|19.58|19.65|1.004|
|2|33.46|33.39|0.998|26.87|26.85|0.999|
|3|43.38|43.34|0.999|34.59|34.60|1.000|
|4|53.36|53.32|0.999|42.20|42.29|1.002|
|5|62.62|62.63|1.000|49.90|49.93|1.000|
|6|71.42|71.51|1.001|57.97|57.97|1.000|
|7|79.97|80.13|1.002|65.85|66.08|1.004|
|8|88.20|88.04|0.998|73.73|73.58|0.998|
|9|96.16|96.23|1.001|81.44|81.47|1.000|
|10|104.26|104.17|0.999|89.18|89.18|1.000|
|11|112.17|112.10|0.999|97.01|97.01|1.000|
|12|120.14|120.02|0.999|104.71|104.75|1.000|
|13|127.89|127.78|0.999|112.36|112.50|1.001|
|14|135.58|135.61|1.000|120.18|120.26|1.001|
|15|143.42|143.29|0.999|127.94|127.94|1.000|
|16|144.49|144.55|1.000|128.67|128.67|1.000|
|17|144.94|144.87|1.000|128.98|129.00|1.000|
|18|144.86|144.96|1.001|129.00|129.09|1.001|
|19|145.03|145.02|1.000|129.20|129.09|0.999|
|20|144.91|144.90|1.000|129.16|129.18|1.000|
|21|145.14|145.14|1.000|129.05|129.15|1.001|
|22|145.01|145.02|1.000|129.26|129.11|0.999|
|23|145.03|145.21|1.001|129.14|129.20|1.000|
|24|145.26|145.15|0.999|129.15|129.20|1.000|
|25|145.64|145.66|1.000|129.82|129.69|0.999|
|26|145.51|145.51|1.000|129.86|129.81|1.000|
|27|145.70|145.65|1.000|129.94|129.88|1.000|
|28|145.56|145.70|1.001|129.94|129.98|1.000|
|29|145.76|145.61|0.999|129.95|129.89|1.000|
|30|145.75|145.67|0.999|129.90|129.93|1.000|
|31|145.82|145.81|1.000|130.15|129.99|0.999|
|32|145.87|145.83|1.000|130.14|129.96|0.999|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|36.77|36.63|0.996|29.55|29.42|0.996|
|2|53.27|53.21|0.999|41.06|40.95|0.997|
|3|68.91|68.85|0.999|54.75|54.60|0.997|
|4|83.04|83.33|1.003|67.86|68.62|1.011|
|5|96.04|96.21|1.002|80.59|80.62|1.000|
|6|109.86|110.04|1.002|94.13|94.02|0.999|
|7|123.28|123.30|1.000|107.24|107.06|0.998|
|8|136.53|136.67|1.001|120.43|120.35|0.999|
|9|150.83|150.79|1.000|133.90|134.14|1.002|
|10|163.80|163.72|1.000|146.84|147.00|1.001|
|11|177.02|176.72|0.998|159.92|159.94|1.000|
|12|189.59|189.46|0.999|172.90|172.79|0.999|
|13|202.62|202.71|1.000|185.78|185.96|1.001|
|14|215.82|215.67|0.999|198.79|198.84|1.000|
|15|228.58|228.60|1.000|211.67|211.69|1.000|
|16|241.50|241.55|1.000|224.70|224.76|1.000|
|17|256.14|255.98|0.999|239.45|239.66|1.001|
|18|269.11|268.86|0.999|252.35|252.22|0.999|
|19|281.41|281.42|1.000|265.34|265.17|0.999|
|20|290.08|290.40|1.001|273.95|273.73|0.999|
|21|298.84|298.88|1.000|282.46|282.54|1.000|
|22|307.43|307.58|1.000|291.20|291.17|1.000|
|23|316.03|316.02|1.000|299.95|299.97|1.000|
|24|324.65|324.74|1.000|308.60|308.61|1.000|
|25|333.47|333.41|1.000|317.42|317.46|1.000|
|26|342.15|342.03|1.000|326.11|326.06|1.000|
|27|350.67|350.68|1.000|334.62|334.54|1.000|
|28|359.16|359.26|1.000|343.08|343.14|1.000|
|29|367.85|367.80|1.000|351.83|351.76|1.000|
|30|376.57|376.30|0.999|360.36|360.43|1.000|
|31|385.19|385.10|1.000|369.19|368.98|0.999|
|32|393.43|393.51|1.000|377.83|377.75|1.000|

This PR doesn't change the kernel's Cake variants: SwiGLU, GPT-OSS-style
SwiGLU (alpha/beta/limit), SiLU and SiTU on sm_100a and sm_103a, plus
clamped SwiGLU (limit 10) on sm_100a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved handling of token counts from 1 to 32 across supported
targets.
* Added safeguards for workloads with a high number of routes, avoiding
configurations that exceed supported limits.
* **Performance**
* Updated available decoding implementations to better match supported
workload geometries.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [66a7808](https://github.com/flashinfer-ai/flashinfer/commit/66a780899a23cd4242cc8d4293fa62496ad2206a)

- **作者**: eigen
- **时间**: 2026-10-25T20:47:45Z
- **提交信息**: fix(cake_causal_conv1d_train): raise the sm_107a min_cuda floor to 13.4 (#7354)

This PR fixes the toolkit floor for the `sm_107a` entries in the
`cake_causal_conv1d_train` build manifest. `cake_build.jit_specs` and
`scripts/check_cake_build_manifests.py` use the per-entry `min_cuda`
value to skip any entry the local toolkit can't build ("skip min_cuda >
toolkit"). These entries had `"min_cuda": "13.0"`, so a CUDA 13.0–13.3
toolkit kept them. nvcc then failed on
`-gencode=arch=compute_107a,code=sm_107a` with a raw `nvcc fatal :
Unsupported gpu architecture 'compute_107a'` instead of the intended
"needs CUDA 13.4 or newer" message. #7199 fixed the same defect in two
other manifests.

The PR changes `"min_cuda": "13.0"` to `"min_cuda": "13.4"` for the 24
`sm_107a` entries in
`flashinfer/cake_causal_conv1d_train_backend/build.json`. With this
floor, a CUDA 13.0–13.3 toolkit skips these entries through the
`min_cuda` check, so the build no longer hits the raw nvcc error.
Nothing else changes. No kernel source or host code is touched.
`common.requires.cuda_toolkit.min` stays 12.8 because it is the lowest
entry floor of the package. The 22 sm_100a and 23 sm_103a entries keep
12.8 / 12.9. The kernels, routes and measured speedups of #6782, #6816,
#6844, #6874, #6930, #7072, #7089 and #7140 are unchanged. On a CUDA
13.4+ toolkit, nothing changes.

nvcc supports `compute_107a` / `sm_107a` starting with CUDA 13.4. The
CUDA 13.4 nvcc documentation lists them ("Rubin support"), and no
13.0–13.3.1 edition does. Confirmed for #7199 by compiling a trivial
kernel with `-gencode=arch=compute_107a,code=sm_107a -cubin` using the
pip toolchains (`nvidia-cuda-nvcc` and companions pinned per release);
as a control, `sm_103a` compiled on every release.

| nvcc | `sm_107a` |
|---|---|
| 13.0.88 | rejected: Unsupported gpu architecture 'compute_107a' |
| 13.1.115 | rejected |
| 13.2.86 | rejected |
| 13.3.73 | rejected |
| 13.4.59 | compiles |
| 13.4.92 | compiles |
The nvcc table is the one measured for #7199; it was not re-measured for
this PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Compatibility**
* Builds targeting `sm_107a` now require CUDA 13.4 or later.
Requirements for other architectures are unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [20ede14](https://github.com/flashinfer-ai/flashinfer/commit/20ede1453faaa800adf87bfc612c83e48ff113ca)

- **作者**: eigen
- **时间**: 2026-10-25T20:47:22Z
- **提交信息**: perf(cake_fused_norm_combine): one-token program, packed norm in the owner programs and an early-load pipelined band (#7352)

`cake_fused_norm_combine` has one Cake variant: BF16, hidden size 2560,
eight peers and two norm tracks. This PR delivers a new version of that
variant, and its outputs are bitwise equal to the previous version. The
host now picks one of six programs by token count instead of four. One
token gets its own build of the one-CTA-per-token program. The stream
program and the pipelined program are rebuilt. A new pipelined program
at three CTAs per SM covers 593 to 1772 tokens on 148 SMs. The
eight-CTA-per-token program (4 to 39 tokens) and the one-CTA-per-token
program for 2 to 3 tokens are unchanged. The baseline is the previous
Cake version of this kernel shipped in FlashInfer (current main, which
includes #7330). At 8 tokens both sides run the same program, so the
0.997× ratio on both GPUs is measurement noise, not a change. Every
other measured token count is faster. Speedups range from 1.012× to
1.088× on B200 and from 1.014× to 1.092× on B300.

| GPU | tokens | previous Cake (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|---:|
| B200 | 1 | 8.736 | 8.032 | 1.088× |
| B200 | 8 | 10.528 | 10.560 | 0.997× (same program) |
| B200 | 64 | 13.088 | 12.672 | 1.033× |
| B200 | 256 | 15.744 | 15.296 | 1.029× |
| B200 | 1024 | 28.335 | 27.297 | 1.038× |
| B200 | 2048 | 43.200 | 42.688 | 1.012× |
| B300 | 1 | 9.153 | 8.384 | 1.092× |
| B300 | 8 | 11.424 | 11.457 | 0.997× (same program) |
| B300 | 64 | 13.760 | 13.472 | 1.021× |
| B300 | 256 | 16.480 | 16.096 | 1.024× |
| B300 | 1024 | 29.025 | 28.032 | 1.035× |
| B300 | 2048 | 43.809 | 43.200 | 1.014× |

Measured on 8× NVIDIA B200 (sm_100a) and 8× NVIDIA B300 (sm_103a) with
CUDA 13.4, where each time is the per-call kernel time of the eight-rank
collective (the slowest rank of each call, median over calls) and
speedup = previous Cake / this PR.

Cake ships no other variant of this kernel, and the kernel ships on
sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized execution paths for single-token inputs and larger
token counts, selected according to input size and GPU capabilities.
* Expanded support for pipelined normalization and collective-combine
workloads.
* **Bug Fixes**
  * Collective results now incorporate all peer contributions.
* Normalization and residual calculations consistently use rounded
bfloat16 values.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e9261a5](https://github.com/flashinfer-ai/flashinfer/commit/e9261a5e280b6c24d437d4b798e56d056dae5b8f)

- **作者**: eigen
- **时间**: 2026-10-25T20:46:12Z
- **提交信息**: perf(cake_kimi_k3_attn_res): fence-free K2 register-carry, two-CTA-per-SM and retuned persistent programs (SM100/SM103) (#7338)

This PR changes routes of the Cake Kimi-K3 AttnRes operator,
`flashinfer.experimental.cake_kimi_k3_attn_res`. It is exposed as
`flashinfer.kimi_k3_attn_res.prepare_kimi_k3_attn_res` and
`kimi_k3_attn_res`. The operator runs residual add, an optional snapshot
write, K+1 candidate scoring, softmax, mix and output RMSNorm in one
launch. It takes BF16 inputs with hidden size 7168 and K in [0, 8]. This
PR changes routes in both the dense form and the snapshot-write form.

New persistent programs run two CTAs per SM, with a one-deep chunk ring,
on min(M, 2 × SMs) CTAs. They serve some K = 2 and K = 3 cells with M
from 384 to 1024 on SM100 and SM103. On SM103, new nc3 register-carry
programs without the consumed-release fence serve large-M and small-M K
= 2 cells. On SM100, fence-free twins serve some K = 2 and K = 3 cells.
Many dense and snapshot-write cells use retuned persistent programs. The
retuning changes chunk count, ring depth, release and prefix-add
options, and fast math. This PR also adds small-M cluster programs. The
program set grows from 138 programs (167 libraries: 80 sm_100a, 87
sm_103a) to 181 programs (211 libraries: 96 sm_100a, 115 sm_103a). This
PR adds 48 programs, adds an sm_100a build to one existing small-M
cluster program, and removes 5 programs that no route reaches any more.

The baseline is the previous Cake version of this operator, merged in PR
#7014. The route changes at one or both PDL modes for 46 shapes on
GB300, 43 on B300 and 38 on B200. All of these shapes are faster at both
PDL modes. Their ratios are 1.0071 to 1.1097 on GB300, 1.0069 to 1.1219
on B300 and 1.0067 to 1.1297 on B200. A further 15 shapes on GB300, 15
on B300 and 16 on B200 keep their route. The updated code generator
rebuilds their programs, and their SASS differs. These programs are the
K = 0 TMA program, the native K = 6, 7 and 8 programs and, on SM103, one
K = 4 pair program. Their ratios are 0.9956 to 1.0013 on GB300, 0.9971
to 1.0017 on B300 and 0.9961 to 1.0012 on B200. These ratios are within
±0.5 % and do not show a speedup. The tables list both groups of shapes.
Times are CUPTI kernel times with cold L2, from paired interleaved ABBA
sampling with 3 groups × 300 samples per arm; the ratio is the geometric
mean, over the three groups, of the per-group median ratio previous /
new.

NVIDIA GB300 (sm_103a, 152 SMs), driver 580.159.03, CUDA 13.4.92, torch
2.14.1+cu130.

| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 768, K 0 (dense) | 9.984 | 9.984 | 0.9989 | 9.952 | 9.984 | 0.9979 |
| M 1024, K 0 (dense) | 10.816 | 10.848 | 0.9965 | 10.784 | 10.848 |
0.9956 |
| M 1536, K 0 (dense) | 16.640 | 16.640 | 1.0006 | 16.608 | 16.608 |
1.0000 |
| M 2048, K 0 (dense) | 20.704 | 20.704 | 1.0000 | 20.672 | 20.704 |
0.9985 |
| M 3072, K 0 (dense) | 29.888 | 29.888 | 1.0002 | 29.888 | 29.856 |
1.0007 |
| M 4096, K 0 (dense) | 37.984 | 37.984 | 0.9997 | 37.952 | 37.984 |
0.9990 |
| M 6144, K 0 (dense) | 55.456 | 55.488 | 0.9997 | 55.505 | 55.456 |
1.0003 |
| M 8192, K 0 (dense) | 73.152 | 73.152 | 1.0000 | 73.121 | 73.152 |
1.0001 |
| M 12288, K 0 (dense) | 107.456 | 107.424 | 1.0003 | 107.456 | 107.488
| 0.9999 |
| M 16384, K 0 (dense) | 141.409 | 141.376 | 1.0003 | 141.376 | 141.376
| 1.0002 |
| M 384, K 2 (dense) | 9.984 | 9.152 | 1.0909 | 10.016 | 9.152 | 1.0920
|
| M 512, K 2 (dense) | 11.872 | 11.008 | 1.0795 | 11.904 | 11.008 |
1.0824 |
| M 8192, K 2 (dense) | 108.256 | 106.720 | 1.0143 | 108.240 | 106.785 |
1.0138 |
| M 12288, K 2 (dense) | 158.881 | 157.088 | 1.0114 | 158.912 | 157.153
| 1.0113 |
| M 192, K 3 (dense) | 8.416 | 7.584 | 1.1097 | 8.416 | 7.584 | 1.1083 |
| M 384, K 3 (dense) | 10.976 | 10.400 | 1.0544 | 10.976 | 10.400 |
1.0554 |
| M 512, K 3 (dense) | 13.280 | 12.864 | 1.0324 | 13.248 | 12.816 |
1.0341 |
| M 768, K 3 (dense) | 17.536 | 16.721 | 1.0468 | 17.520 | 16.736 |
1.0478 |
| M 1024, K 3 (dense) | 20.832 | 19.872 | 1.0472 | 20.832 | 19.904 |
1.0461 |
| M 192, K 4 (dense) | 8.880 | 8.864 | 1.0006 | 8.864 | 8.864 | 1.0012 |
| M 256, K 4 (snapshot write, block 4) | 9.632 | 9.408 | 1.0215 | 9.600
| 9.408 | 1.0204 |
| M 512, K 4 (dense) | 14.368 | 14.208 | 1.0120 | 14.368 | 14.208 |
1.0120 |
| M 768, K 4 (dense) | 19.488 | 19.264 | 1.0108 | 19.456 | 19.232 |
1.0097 |
| M 1024, K 4 (dense) | 23.072 | 22.784 | 1.0117 | 23.040 | 22.816 |
1.0108 |
| M 1536, K 4 (dense) | 32.800 | 32.320 | 1.0145 | 32.768 | 32.320 |
1.0132 |
| M 3072, K 4 (dense) | 58.529 | 57.824 | 1.0125 | 58.496 | 57.792 |
1.0118 |
| M 6144, K 4 (dense) | 108.433 | 107.200 | 1.0113 | 108.448 | 107.168 |
1.0119 |
| M 512, K 5 (dense) | 15.696 | 15.488 | 1.0131 | 15.712 | 15.520 |
1.0117 |
| M 1536, K 5 (dense) | 36.576 | 36.176 | 1.0119 | 36.688 | 36.192 |
1.0136 |
| M 2048, K 5 (dense) | 45.600 | 44.928 | 1.0153 | 45.664 | 44.928 |
1.0164 |
| M 6144, K 5 (dense) | 123.264 | 121.632 | 1.0132 | 123.360 | 121.632 |
1.0137 |
| M 12288, K 5 (dense) | 239.696 | 232.865 | 1.0293 | 239.905 | 232.881
| 1.0302 |
| M 16384, K 5 (dense) | 313.440 | 306.784 | 1.0216 | 313.297 | 306.753
| 1.0210 |
| M 256, K 6 (dense) | 10.944 | 10.688 | 1.0240 | 10.912 | 10.656 |
1.0240 |
| M 384, K 6 (dense) | 14.097 | 13.792 | 1.0213 | 14.112 | 13.824 |
1.0216 |
| M 512, K 6 (dense) | 17.056 | 16.832 | 1.0120 | 17.024 | 16.864 |
1.0108 |
| M 768, K 6 (dense) | 23.632 | 23.104 | 1.0226 | 23.648 | 23.104 |
1.0240 |
| M 1024, K 6 (dense) | 28.497 | 28.000 | 1.0173 | 28.480 | 27.968 |
1.0179 |
| M 1536, K 6 (dense) | 40.608 | 40.224 | 1.0098 | 40.672 | 40.256 |
1.0101 |
| M 2048, K 6 (dense) | 51.569 | 50.656 | 1.0178 | 51.632 | 50.688 |
1.0188 |
| M 3072, K 6 (dense) | 73.920 | 72.704 | 1.0167 | 73.953 | 72.672 |
1.0181 |
| M 4096, K 6 (dense) | 94.848 | 93.984 | 1.0095 | 94.897 | 93.920 |
1.0107 |
| M 192, K 7 (dense) | 10.784 | 10.784 | 0.9990 | 10.784 | 10.784 |
0.9990 |
| M 256, K 7 (snapshot write, block 7) | 11.616 | 11.392 | 1.0197 |
11.616 | 11.392 | 1.0197 |
| M 512, K 7 (dense) | 18.624 | 18.272 | 1.0199 | 18.624 | 18.272 |
1.0198 |
| M 768, K 7 (dense) | 25.408 | 25.088 | 1.0115 | 25.344 | 25.088 |
1.0113 |
| M 1024, K 7 (dense) | 31.328 | 30.784 | 1.0173 | 31.328 | 30.768 |
1.0178 |
| M 1024, K 7 (snapshot write, block 7) | 32.480 | 31.808 | 1.0215 |
32.480 | 31.744 | 1.0228 |
| M 1536, K 7 (dense) | 44.896 | 44.097 | 1.0174 | 44.928 | 44.096 |
1.0192 |
| M 2048, K 7 (dense) | 56.960 | 56.160 | 1.0140 | 56.960 | 56.224 |
1.0133 |
| M 3072, K 7 (dense) | 81.632 | 80.672 | 1.0118 | 81.600 | 80.656 |
1.0116 |
| M 4096, K 7 (dense) | 104.993 | 103.904 | 1.0110 | 105.057 | 103.872 |
1.0115 |
| M 6144, K 7 (dense) | 150.848 | 148.881 | 1.0132 | 150.880 | 148.912 |
1.0131 |
| M 12288, K 7 (dense) | 285.473 | 282.625 | 1.0101 | 285.457 | 282.705
| 1.0096 |
| M 192, K 8 (dense) | 11.328 | 11.328 | 1.0000 | 11.328 | 11.328 |
1.0009 |
| M 256, K 8 (dense) | 12.160 | 12.160 | 0.9991 | 12.128 | 12.160 |
0.9991 |
| M 384, K 8 (dense) | 16.576 | 16.544 | 1.0013 | 16.544 | 16.544 |
1.0006 |
| M 768, K 8 (dense) | 27.360 | 27.136 | 1.0087 | 27.360 | 27.168 |
1.0071 |
| M 1024, K 8 (dense) | 33.440 | 32.864 | 1.0175 | 33.440 | 32.832 |
1.0182 |
| M 2048, K 8 (dense) | 61.344 | 60.512 | 1.0133 | 61.312 | 60.528 |
1.0130 |
| M 3072, K 8 (dense) | 87.968 | 86.528 | 1.0166 | 87.968 | 86.560 |
1.0164 |

NVIDIA B300 SXM6 AC (sm_103a, 148 SMs), driver 580.126.09, CUDA 13.4.92,
torch 2.14.1+cu130.

| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 768, K 0 (dense) | 10.144 | 10.176 | 0.9990 | 10.144 | 10.145 |
1.0000 |
| M 1024, K 0 (dense) | 11.072 | 11.104 | 0.9971 | 11.072 | 11.104 |
0.9976 |
| M 1536, K 0 (dense) | 17.184 | 17.216 | 0.9988 | 17.215 | 17.184 |
1.0012 |
| M 2048, K 0 (dense) | 21.440 | 21.441 | 0.9995 | 21.441 | 21.440 |
0.9995 |
| M 3072, K 0 (dense) | 30.657 | 30.688 | 0.9986 | 30.657 | 30.657 |
1.0003 |
| M 4096, K 0 (dense) | 39.520 | 39.520 | 1.0000 | 39.552 | 39.520 |
1.0005 |
| M 6144, K 0 (dense) | 57.248 | 57.281 | 1.0000 | 57.249 | 57.248 |
1.0002 |
| M 8192, K 0 (dense) | 75.201 | 75.201 | 1.0001 | 75.232 | 75.264 |
0.9999 |
| M 12288, K 0 (dense) | 110.337 | 110.241 | 1.0007 | 110.337 | 110.305
| 1.0003 |
| M 16384, K 0 (dense) | 146.049 | 146.113 | 0.9997 | 146.049 | 146.082
| 0.9999 |
| M 768, K 1 (dense) | 13.024 | 12.769 | 1.0184 | 13.024 | 12.800 |
1.0175 |
| M 384, K 2 (dense) | 10.208 | 9.344 | 1.0925 | 10.208 | 9.344 | 1.0925
|
| M 512, K 2 (dense) | 12.097 | 10.976 | 1.1046 | 12.128 | 10.976 |
1.1050 |
| M 2048, K 2 (dense) | 31.857 | 31.393 | 1.0153 | 31.872 | 31.392 |
1.0160 |
| M 4096, K 2 (dense) | 59.392 | 58.433 | 1.0165 | 59.329 | 58.433 |
1.0154 |
| M 16384, K 2 (dense) | 215.010 | 212.642 | 1.0110 | 215.011 | 212.626
| 1.0112 |
| M 192, K 3 (dense) | 8.736 | 7.776 | 1.1219 | 8.736 | 7.776 | 1.1219 |
| M 384, K 3 (dense) | 11.360 | 10.848 | 1.0472 | 11.360 | 10.847 |
1.0483 |
| M 512, K 3 (dense) | 13.504 | 12.896 | 1.0479 | 13.504 | 12.896 |
1.0488 |
| M 768, K 3 (dense) | 18.240 | 17.120 | 1.0654 | 18.208 | 17.120 |
1.0642 |
| M 1024, K 3 (dense) | 21.696 | 20.929 | 1.0362 | 21.697 | 20.960 |
1.0362 |
| M 192, K 4 (dense) | 9.248 | 9.216 | 1.0012 | 9.247 | 9.248 | 1.0005 |
| M 256, K 4 (snapshot write, block 4) | 9.824 | 9.664 | 1.0166 | 9.824
| 9.664 | 1.0166 |
| M 1024, K 4 (dense) | 23.936 | 23.601 | 1.0151 | 23.968 | 23.552 |
1.0167 |
| M 1536, K 4 (dense) | 33.760 | 32.992 | 1.0233 | 33.745 | 32.992 |
1.0231 |
| M 3072, K 4 (dense) | 60.033 | 59.233 | 1.0131 | 60.033 | 59.296 |
1.0126 |
| M 6144, K 4 (dense) | 111.169 | 109.825 | 1.0123 | 111.233 | 109.793 |
1.0130 |
| M 384, K 5 (dense) | 13.248 | 13.024 | 1.0181 | 13.248 | 12.992 |
1.0205 |
| M 1536, K 5 (dense) | 37.185 | 36.577 | 1.0163 | 37.200 | 36.576 |
1.0171 |
| M 2048, K 5 (dense) | 46.849 | 45.984 | 1.0182 | 46.912 | 45.953 |
1.0203 |
| M 3072, K 5 (dense) | 67.521 | 66.688 | 1.0126 | 67.584 | 66.688 |
1.0134 |
| M 4096, K 5 (dense) | 87.489 | 85.825 | 1.0198 | 87.585 | 85.808 |
1.0207 |
| M 12288, K 5 (dense) | 241.363 | 239.171 | 1.0096 | 241.378 | 239.074
| 1.0097 |
| M 16384, K 5 (dense) | 316.900 | 314.627 | 1.0069 | 316.932 | 314.467
| 1.0077 |
| M 192, K 6 (dense) | 10.625 | 10.400 | 1.0225 | 10.625 | 10.400 |
1.0226 |
| M 256, K 6 (dense) | 11.104 | 10.816 | 1.0266 | 11.104 | 10.848 |
1.0256 |
| M 384, K 6 (dense) | 14.336 | 14.176 | 1.0120 | 14.336 | 14.176 |
1.0121 |
| M 512, K 6 (dense) | 17.280 | 16.928 | 1.0202 | 17.312 | 16.928 |
1.0221 |
| M 768, K 6 (dense) | 24.736 | 24.160 | 1.0234 | 24.704 | 24.177 |
1.0221 |
| M 1024, K 6 (dense) | 28.960 | 28.384 | 1.0197 | 28.960 | 28.401 |
1.0201 |
| M 1536, K 6 (dense) | 41.185 | 40.496 | 1.0169 | 41.121 | 40.512 |
1.0153 |
| M 2048, K 6 (dense) | 52.081 | 51.329 | 1.0147 | 52.065 | 51.312 |
1.0150 |
| M 192, K 7 (dense) | 10.976 | 10.976 | 1.0010 | 10.944 | 10.976 |
0.9980 |
| M 256, K 7 (snapshot write, block 7) | 11.904 | 11.552 | 1.0295 |
11.904 | 11.584 | 1.0267 |
| M 512, K 7 (dense) | 18.816 | 18.464 | 1.0185 | 18.784 | 18.432 |
1.0191 |
| M 768, K 7 (dense) | 26.512 | 26.272 | 1.0095 | 26.544 | 26.241 |
1.0112 |
| M 1024, K 7 (dense) | 31.968 | 31.456 | 1.0161 | 31.968 | 31.520 |
1.0147 |
| M 1024, K 7 (snapshot write, block 7) | 33.153 | 32.465 | 1.0205 |
33.120 | 32.496 | 1.0192 |
| M 1536, K 7 (dense) | 45.632 | 44.929 | 1.0152 | 45.728 | 45.024 |
1.0160 |
| M 2048, K 7 (dense) | 57.728 | 57.120 | 1.0103 | 57.760 | 57.184 |
1.0099 |
| M 3072, K 7 (dense) | 83.457 | 82.209 | 1.0150 | 83.424 | 82.209 |
1.0151 |
| M 4096, K 7 (dense) | 108.161 | 106.881 | 1.0122 | 108.289 | 106.849 |
1.0131 |
| M 6144, K 7 (dense) | 155.426 | 153.794 | 1.0105 | 155.425 | 153.793 |
1.0109 |
| M 192, K 8 (dense) | 11.584 | 11.584 | 1.0000 | 11.584 | 11.616 |
0.9973 |
| M 256, K 8 (dense) | 12.480 | 12.449 | 1.0017 | 12.480 | 12.480 |
0.9992 |
| M 384, K 8 (dense) | 16.992 | 17.024 | 0.9987 | 16.992 | 17.024 |
0.9978 |
| M 1024, K 8 (dense) | 34.209 | 33.760 | 1.0138 | 34.081 | 33.665 |
1.0133 |
| M 2048, K 8 (dense) | 62.321 | 61.376 | 1.0152 | 62.240 | 61.409 |
1.0137 |

NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4.92, torch
2.14.1+cu130.

| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 192, K 0 (dense) | 4.448 | 4.385 | 1.0144 | 4.448 | 4.385 | 1.0144 |
| M 384, K 0 (dense) | 6.528 | 6.528 | 1.0001 | 6.528 | 6.528 | 1.0000 |
| M 512, K 0 (dense) | 7.552 | 7.552 | 0.9993 | 7.553 | 7.584 | 0.9985 |
| M 768, K 0 (dense) | 10.240 | 10.240 | 1.0000 | 10.240 | 10.240 |
1.0005 |
| M 1024, K 0 (dense) | 11.232 | 11.232 | 1.0010 | 11.232 | 11.232 |
0.9991 |
| M 1536, K 0 (dense) | 17.008 | 17.008 | 1.0000 | 16.992 | 16.992 |
0.9991 |
| M 2048, K 0 (dense) | 21.280 | 21.248 | 1.0005 | 21.280 | 21.248 |
1.0010 |
| M 3072, K 0 (dense) | 30.239 | 30.208 | 0.9991 | 30.272 | 30.272 |
1.0000 |
| M 4096, K 0 (dense) | 39.104 | 39.072 | 1.0006 | 39.120 | 39.072 |
1.0009 |
| M 6144, K 0 (dense) | 56.768 | 56.736 | 1.0006 | 56.799 | 56.736 |
1.0012 |
| M 8192, K 0 (dense) | 74.255 | 74.303 | 0.9994 | 74.272 | 74.304 |
0.9997 |
| M 12288, K 0 (dense) | 109.056 | 109.056 | 0.9999 | 109.056 | 109.056
| 0.9999 |
| M 16384, K 0 (dense) | 143.808 | 143.776 | 1.0002 | 143.808 | 143.792
| 1.0001 |
| M 1024, K 1 (snapshot write, block 1) | 18.305 | 17.856 | 1.0251 |
18.288 | 17.856 | 1.0236 |
| M 192, K 2 (dense) | 7.968 | 7.072 | 1.1282 | 8.000 | 7.072 | 1.1297 |
| M 384, K 2 (dense) | 10.143 | 9.408 | 1.0758 | 10.128 | 9.440 | 1.0741
|
| M 512, K 2 (dense) | 12.064 | 11.104 | 1.0854 | 12.064 | 11.104 |
1.0855 |
| M 12288, K 2 (dense) | 163.167 | 159.936 | 1.0201 | 163.151 | 159.904
| 1.0202 |
| M 16384, K 2 (dense) | 215.487 | 210.447 | 1.0237 | 215.631 | 210.592
| 1.0239 |
| M 192, K 3 (dense) | 8.704 | 7.744 | 1.1225 | 8.704 | 7.744 | 1.1226 |
| M 384, K 3 (dense) | 11.521 | 10.944 | 1.0547 | 11.552 | 10.912 |
1.0567 |
| M 512, K 3 (dense) | 13.248 | 12.704 | 1.0419 | 13.248 | 12.705 |
1.0419 |
| M 768, K 3 (dense) | 17.888 | 17.233 | 1.0390 | 17.920 | 17.216 |
1.0403 |
| M 1024, K 3 (dense) | 21.632 | 21.056 | 1.0279 | 21.633 | 21.056 |
1.0273 |
| M 2048, K 3 (dense) | 36.736 | 36.512 | 1.0067 | 36.768 | 36.480 |
1.0077 |
| M 3072, K 3 (dense) | 52.575 | 51.968 | 1.0117 | 52.512 | 52.000 |
1.0102 |
| M 6144, K 3 (dense) | 100.064 | 97.248 | 1.0298 | 100.128 | 97.248 |
1.0293 |
| M 8192, K 3 (dense) | 129.311 | 125.759 | 1.0283 | 129.407 | 125.727 |
1.0294 |
| M 12288, K 3 (dense) | 190.256 | 184.287 | 1.0320 | 190.335 | 184.352
| 1.0328 |
| M 16384, K 3 (dense) | 254.143 | 242.495 | 1.0483 | 254.543 | 242.431
| 1.0504 |
| M 4096, K 4 (dense) | 76.944 | 75.103 | 1.0244 | 76.864 | 75.136 |
1.0229 |
| M 512, K 5 (dense) | 16.256 | 16.064 | 1.0113 | 16.255 | 16.064 |
1.0113 |
| M 3072, K 5 (dense) | 66.912 | 65.056 | 1.0274 | 66.912 | 65.055 |
1.0285 |
| M 6144, K 5 (dense) | 126.048 | 122.224 | 1.0315 | 126.048 | 122.175 |
1.0318 |
| M 8192, K 5 (dense) | 167.327 | 160.096 | 1.0449 | 167.360 | 160.095 |
1.0456 |
| M 192, K 6 (dense) | 10.720 | 10.720 | 0.9990 | 10.688 | 10.720 |
0.9961 |
| M 256, K 6 (dense) | 11.135 | 10.880 | 1.0225 | 11.104 | 10.896 |
1.0191 |
| M 2048, K 6 (dense) | 50.800 | 50.176 | 1.0122 | 50.816 | 50.144 |
1.0134 |
| M 192, K 7 (dense) | 11.136 | 11.136 | 1.0000 | 11.152 | 11.136 |
1.0004 |
| M 256, K 7 (snapshot write, block 7) | 12.064 | 11.616 | 1.0386 |
12.064 | 11.616 | 1.0395 |
| M 768, K 7 (dense) | 26.528 | 26.080 | 1.0174 | 26.560 | 26.048 |
1.0192 |
| M 1024, K 7 (dense) | 31.424 | 31.072 | 1.0113 | 31.424 | 31.072 |
1.0110 |
| M 1024, K 7 (snapshot write, block 7) | 33.728 | 33.216 | 1.0157 |
33.728 | 33.216 | 1.0151 |
| M 1536, K 7 (dense) | 45.103 | 44.512 | 1.0135 | 45.120 | 44.512 |
1.0138 |
| M 2048, K 7 (dense) | 56.864 | 56.352 | 1.0089 | 56.864 | 56.352 |
1.0096 |
| M 3072, K 7 (dense) | 81.472 | 80.544 | 1.0117 | 81.472 | 80.512 |
1.0123 |
| M 192, K 8 (dense) | 11.648 | 11.680 | 0.9982 | 11.680 | 11.711 |
0.9982 |
| M 256, K 8 (dense) | 12.544 | 12.576 | 0.9970 | 12.544 | 12.576 |
0.9983 |
| M 384, K 8 (dense) | 16.992 | 16.608 | 1.0244 | 16.992 | 16.592 |
1.0248 |
| M 512, K 8 (dense) | 21.151 | 20.736 | 1.0198 | 21.152 | 20.735 |
1.0201 |
| M 768, K 8 (dense) | 28.512 | 28.000 | 1.0179 | 28.512 | 28.032 |
1.0173 |
| M 1024, K 8 (dense) | 33.888 | 33.440 | 1.0137 | 33.920 | 33.471 |
1.0131 |
| M 1536, K 8 (dense) | 48.767 | 48.032 | 1.0151 | 48.736 | 48.064 |
1.0143 |
| M 2048, K 8 (dense) | 61.632 | 60.959 | 1.0108 | 61.631 | 61.024 |
1.0104 |

The shape list has 291 shapes per GPU. The tables do not list the other
230 shapes on GB300, 233 on B300 and 237 on B200. These shapes run the
same programs as the previous version, with identical SASS. Their
timings are the ones listed in PRs #6980 and #7014.

Cake ships no other data types or layouts for this operator, since the
dense and snapshot-write forms are the whole family, and 181 programs
(211 libraries: 96 sm_100a, 115 sm_103a) cover B200 (sm_100a, 148 SMs),
B300 (sm_103a, 148 SMs) and GB300 (sm_103a, 152 SMs).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added experimental CUDA implementations for Kimi K3 attention-residual
processing across several source configurations.
* Persistent attention routes now support two-CTA-per-SM execution, with
matching fallback selection and route labeling.

* **Bug Fixes**
* Improved validation of tensor strides and launch parameters, including
clearer errors for invalid values and arithmetic overflow.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [84f3bb3](https://github.com/flashinfer-ai/flashinfer/commit/84f3bb30b29e2a927bfdacdef2bbe7eca5830fc0)

- **作者**: eigen
- **时间**: 2026-10-25T20:21:13Z
- **提交信息**: perf(cake_grouped_fp8_gemm): swap-AB block-scaled programs for packed UE8M0 scales on SM100 / SM103 (#7342)

`cake_grouped_fp8_gemm` is Cake's grouped FP8 GEMM over a padded
contiguous layout. It has two block-scale formats. FP32 per-128-block
scales have 11 routes. Packed power-of-two UE8M0 block scales have 4
routes: N-tile 128 or 256, each with a 128-row or a 32-row group walk.
Cake also ships two related forms: a fused SiLU-and-quantize form and a
masked batch form. This PR adds the swap-AB route for UE8M0 block scales
as three programs: `swap`, `swap_run32` (for 32-row group alignment) and
`swap_carry`. Each program is built for sm_100a and sm_103a. The speedup
below compares this PR against the previous Cake version of the kernel,
which is the set of Cake programs shipped and routed by FlashInfer main.

NVIDIA B200 (sm_100a) and NVIDIA GB300 (sm_103a), CUDA 13.4 toolkit
(nvcc 13.4), PyTorch 2.14.1+cu130 (CUDA 13.0 runtime). Some GB300 GPUs
run 2-CTA cluster kernels slower, so both kinds are shown as "GB300
fast" and "GB300 slow". Latency is in microseconds, and a new/shipped
ratio below 1 means the new routing is faster. "shipped" is FlashInfer
main's routing (the previous Cake programs), and "new" is this PR's
routing. The program column gives the program the new routing picks on
B200 / GB300. `n256` is the shipped N-tile-256 program, so its ratio is
a tie. M is the row count of the padded contiguous layout and groups are
experts. align is the per-group row alignment. tokens x top-k counts
routed assignments under uniform (distinct uniform top-k) or skewed
(skewed multinomial) routing.

| M | N | K | groups | align | tokens x top-k, routing | program B200 /
GB300 | B200 shipped us | B200 new us | B200 new/shipped | GB300 fast
shipped us | GB300 fast new us | GB300 fast new/shipped | GB300 slow
shipped us | GB300 slow new us | GB300 slow new/shipped |

|---:|---:|---:|---:|---:|---:|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 32768 | 1024 | 2048 | 256 | 128 | 32 x 8, uniform | swap / swap |
62.88 | 58.82 | 0.935 | 61.04 | 57.14 | 0.937 | 60.98 | 56.88 | 0.934 |
| 34560 | 1024 | 2048 | 256 | 128 | 256 x 8, uniform | swap / swap |
93.86 | 88.35 | 0.941 | 91.58 | 86.13 | 0.940 | 91.50 | 85.68 | 0.936 |
| 36608 | 1024 | 2048 | 256 | 128 | 512 x 8, uniform | swap / swap |
94.06 | 88.66 | 0.941 | 91.42 | 86.19 | 0.943 | 91.26 | 85.66 | 0.939 |
| 48896 | 1024 | 2048 | 256 | 128 | 2048 x 8, uniform | swap / swap |
101.06 | 97.76 | 0.966 | 99.20 | 94.03 | 0.948 | 98.93 | 93.79 | 0.949 |
| 65280 | 1024 | 2048 | 256 | 128 | 4096 x 8, uniform | swap_carry /
n256 | 118.00 | 111.87 | 0.948 | 105.82 | 105.94 | 1.000 | 105.98 |
106.03 | 1.000 |
| 98048 | 1024 | 2048 | 256 | 128 | 8192 x 8, uniform | swap_carry /
n256 | 166.02 | 152.56 | 0.917 | 148.27 | 148.10 | 0.998 | 147.97 |
147.87 | 1.000 |
| 163584 | 1024 | 2048 | 256 | 128 | 16384 x 8, uniform | swap_carry /
swap_carry | 287.04 | 261.10 | 0.910 | 248.56 | 231.30 | 0.930 | 247.71
| 233.28 | 0.942 |
| 8064 | 1024 | 2048 | 256 | 32 | 8 x 8, uniform | swap_run32 /
swap_run32 | 28.58 | 23.14 | 0.810 | 27.95 | 22.53 | 0.806 | 27.65 |
22.59 | 0.817 |
| 33024 | 1024 | 2048 | 256 | 128 | 64 x 8, uniform | swap / swap |
81.42 | 76.38 | 0.938 | 79.55 | 74.40 | 0.935 | 79.49 | 74.42 | 0.936 |
| 34560 | 2048 | 512 | 256 | 128 | 256 x 8, uniform | swap / swap |
51.74 | 47.46 | 0.917 | 49.90 | 46.19 | 0.928 | 50.22 | 45.95 | 0.915 |
| 36608 | 2048 | 512 | 256 | 128 | 512 x 8, uniform | swap / swap |
51.73 | 47.65 | 0.921 | 50.18 | 46.40 | 0.923 | 49.98 | 46.03 | 0.921 |
| 8064 | 2048 | 512 | 256 | 32 | 8 x 8, uniform | swap_run32 /
swap_run32 | 18.30 | 15.62 | 0.853 | 18.45 | 15.04 | 0.815 | 17.50 |
14.94 | 0.855 |
| 33024 | 2048 | 512 | 256 | 128 | 64 x 8, uniform | swap / swap | 45.15
| 41.78 | 0.925 | 43.95 | 40.51 | 0.921 | 43.97 | 40.96 | 0.931 |
| 65408 | 512 | 4096 | 512 | 128 | 32 x 10, uniform | swap / swap |
91.86 | 84.66 | 0.922 | 92.58 | 84.51 | 0.912 | 94.21 | 84.64 | 0.899 |
| 67584 | 512 | 4096 | 512 | 128 | 256 x 10, uniform | swap / swap |
175.76 | 171.02 | 0.973 | 177.23 | 169.52 | 0.957 | 176.67 | 169.38 |
0.958 |
| 70144 | 512 | 4096 | 512 | 128 | 512 x 10, uniform | swap / swap |
176.54 | 171.25 | 0.970 | 177.50 | 169.74 | 0.957 | 176.72 | 169.87 |
0.961 |
| 85504 | 512 | 4096 | 512 | 128 | 2048 x 10, uniform | swap / swap |
190.67 | 184.62 | 0.968 | 192.82 | 181.22 | 0.940 | 190.42 | 181.12 |
0.951 |
| 105984 | 512 | 4096 | 512 | 128 | 4096 x 10, uniform | swap / swap |
224.34 | 203.36 | 0.906 | 220.38 | 197.74 | 0.897 | 218.22 | 197.81 |
0.907 |
| 146944 | 512 | 4096 | 512 | 128 | 8192 x 10, uniform | n256 / swap |
263.34 | 263.71 | 1.001 | 251.98 | 237.06 | 0.941 | 250.40 | 246.11 |
0.983 |
| 228864 | 512 | 4096 | 512 | 128 | 16384 x 10, uniform | n256 / swap |
382.67 | 382.53 | 1.000 | 350.38 | 334.86 | 0.956 | 345.79 | 354.72 |
1.026 |
| 16000 | 512 | 4096 | 512 | 32 | 2 x 10, uniform | swap_run32 /
swap_run32 | 42.30 | 24.58 | 0.581 | 39.90 | 23.52 | 0.590 | 40.56 |
23.49 | 0.579 |
| 16000 | 512 | 4096 | 512 | 32 | 4 x 10, uniform | swap_run32 /
swap_run32 | 43.06 | 25.81 | 0.600 | 41.49 | 24.74 | 0.596 | 41.63 |
24.74 | 0.594 |
| 16000 | 512 | 4096 | 512 | 32 | 8 x 10, uniform | swap_run32 /
swap_run32 | 46.46 | 32.53 | 0.699 | 43.71 | 31.95 | 0.731 | 43.63 |
32.00 | 0.735 |
| 16128 | 512 | 4096 | 512 | 32 | 16 x 10, uniform | swap_run32 /
swap_run32 | 55.33 | 49.78 | 0.900 | 55.06 | 49.39 | 0.897 | 55.06 |
49.41 | 0.897 |
| 16256 | 512 | 4096 | 512 | 32 | 32 x 10, uniform | swap_run32 /
swap_run32 | 94.35 | 84.50 | 0.896 | 92.91 | 84.02 | 0.904 | 93.09 |
83.94 | 0.903 |
| 65664 | 512 | 4096 | 512 | 128 | 64 x 10, uniform | swap / swap |
126.45 | 122.35 | 0.968 | 127.55 | 121.92 | 0.955 | 127.95 | 122.06 |
0.954 |
| 67584 | 4096 | 256 | 512 | 128 | 256 x 10, uniform | swap_carry /
swap_carry | 113.38 | 101.78 | 0.898 | 110.26 | 97.87 | 0.887 | 109.36 |
97.95 | 0.896 |
| 70144 | 4096 | 256 | 512 | 128 | 512 x 10, uniform | swap_carry /
swap_carry | 113.70 | 103.02 | 0.906 | 110.59 | 99.17 | 0.899 | 109.79 |
99.41 | 0.904 |
| 16000 | 4096 | 256 | 512 | 32 | 2 x 10, uniform | swap_run32 /
swap_run32 | 28.35 | 22.14 | 0.781 | 29.07 | 20.77 | 0.714 | 27.87 |
20.80 | 0.746 |
| 16000 | 4096 | 256 | 512 | 32 | 4 x 10, uniform | swap_run32 /
swap_run32 | 30.64 | 23.81 | 0.777 | 30.05 | 22.82 | 0.759 | 29.54 |
22.91 | 0.775 |
| 16000 | 4096 | 256 | 512 | 32 | 8 x 10, uniform | swap_run32 /
swap_run32 | 36.75 | 28.34 | 0.771 | 35.06 | 26.75 | 0.762 | 34.64 |
26.74 | 0.772 |
| 16128 | 4096 | 256 | 512 | 32 | 16 x 10, uniform | swap_run32 /
swap_run32 | 47.92 | 38.34 | 0.800 | 45.92 | 36.26 | 0.790 | 45.01 |
36.45 | 0.810 |
| 16256 | 4096 | 256 | 512 | 32 | 32 x 10, uniform | swap_run32 /
swap_run32 | 64.90 | 54.86 | 0.847 | 60.22 | 52.02 | 0.864 | 59.28 |
51.98 | 0.877 |
| 65664 | 4096 | 256 | 512 | 128 | 64 x 10, uniform | swap_carry /
swap_carry | 85.81 | 82.56 | 0.961 | 83.68 | 79.58 | 0.951 | 82.88 |
79.55 | 0.960 |
| 65280 | 1024 | 2048 | 256 | 128 | 4096 x 8, skewed | swap_carry / n256
| 123.26 | 113.98 | 0.924 | 109.73 | 109.86 | 1.001 | 109.95 | 110.02 |
1.000 |
| 105984 | 512 | 4096 | 512 | 128 | 4096 x 10, skewed | swap / swap |
214.78 | 203.09 | 0.945 | 211.97 | 197.54 | 0.932 | 211.01 | 198.10 |
0.939 |
| 163584 | 1024 | 2048 | 256 | 128 | 16384 x 8, skewed | swap_carry /
swap_carry | 278.46 | 259.71 | 0.933 | 250.21 | 234.30 | 0.935 | 250.05
| 233.73 | 0.935 |
| 34560 | 2048 | 512 | 256 | 128 | 256 x 8, skewed | swap / swap | 49.71
| 45.31 | 0.913 | 47.73 | 43.89 | 0.919 | 47.42 | 43.82 | 0.925 |

Besides this route, Cake ships `cake_grouped_fp8_gemm` with FP32
per-128-block scales (11 routes) and with its 4 earlier UE8M0 routes,
plus the fused SiLU-and-quantize form
`cake_grouped_fp8_fused_silu_quant` and the masked batch form
`cake_batch_deepgemm_fp8`; `cake_grouped_fp8_gemm` ships on sm_100a and
sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized grouped FP8 matrix multiplication routes for supported
GPU architectures and layouts.
* Route selection now accounts for alignment, group count, and input
shape, and can use swapped operands when eligible.
* Added support for additional tile configurations and launch plans for
these routes.
* **Bug Fixes**
* Improved handling of packed scale layouts and padding when selecting
and launching block-scaled operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a8ec053](https://github.com/flashinfer-ai/flashinfer/commit/a8ec053888bdb597e9a0a3ca9ae57dfe1fc8b900)

- **作者**: eigen
- **时间**: 2026-10-25T20:16:01Z
- **提交信息**: perf(cake_nvfp4_sparse_mla_decode): tcgen05 programs for sm_100a and sm_103a (#7335)

`flashinfer.mla.nvfp4_sparse_mla_decode(..., backend="cake")` has a
single data-type/layout form. It takes E4M3 queries `[T, 16, 576]` and
int32 top-k row ids (`-1` = empty slot) that select 352-byte NVFP4
(`nvfp4_ds_mla`) KV cache rows, and it writes BF16 output `[T, 16,
512]`. This PR replaces the backend's seven `mma.sync` programs (one per
cluster size) with 35 tcgen05 programs, each built for sm_100a and
sm_103a. They cover 7 cluster sizes (1, 2, 3, 4, 5, 6, 8 CTAs per token)
and 5 split bounds (at most 64, 128, 192 or 256 keys per CTA, or any).
The host plan considers only the cluster sizes that fit every token's
cluster into one wave, and picks the one with the least work per CTA.
The baseline is the previous Cake version of `backend="cake"` as shipped
on FlashInfer main. Speedup = previous latency / new latency, so > 1
means the new programs are faster. The new programs are faster on every
row on both GPUs. On B200 the geomean over 39 rows is 1.131x (range
1.020x to 1.305x). On GB300 the geomean over 40 rows is 1.152x (range
1.028x to 1.375x).

Latency is in microseconds per launch, with the same inputs for both
sides and 16 heads. P rows: T = 5..45 tokens per launch at topk 512 /
1024 / 2048. W rows: the wave-boundary token counts from each GPU's
planner, at topk 2048. A `-` means the row exists only in the other
GPU's planner table. S rows: suffix-padded indices (the tail of every
third token is empty), at topk 2048. Timing uses cold L2 (flushed before
every launch) and CUPTI kernel time, and each value is the median of 8
interleaved groups x 200 launches per side. GPUs: NVIDIA B200 (sm_100a,
148 SMs, driver 580.82.07) and NVIDIA GB300 (sm_103a, 152 SMs, driver
580.159.03), with CUDA 13.4 and PyTorch 2.14.1+cu130.

| row | T | topk | padding | B200 previous us | B200 new us | B200
speedup | GB300 previous us | GB300 new us | GB300 speedup |
|---|---|---|---|---|---|---|---|---|---|
| P | 5 | 2048 | none | 12.32 | 10.02 | 1.230 | 11.62 | 9.57 | 1.214 |
| P | 10 | 2048 | none | 12.64 | 10.46 | 1.208 | 11.87 | 9.86 | 1.205 |
| P | 15 | 2048 | none | 13.15 | 10.91 | 1.205 | 12.22 | 10.21 | 1.197 |
| P | 20 | 2048 | none | 15.81 | 14.05 | 1.125 | 14.69 | 12.99 | 1.131 |
| P | 25 | 2048 | none | 17.66 | 15.97 | 1.106 | 16.29 | 14.88 | 1.095 |
| P | 30 | 2048 | none | 20.29 | 16.26 | 1.248 | 18.72 | 15.14 | 1.237 |
| P | 35 | 2048 | none | 24.13 | 20.32 | 1.187 | 18.91 | 15.33 | 1.234 |
| P | 40 | 2048 | none | 24.45 | 20.61 | 1.186 | 23.55 | 18.85 | 1.250 |
| P | 45 | 2048 | none | 24.70 | 20.96 | 1.179 | 23.68 | 19.04 | 1.244 |
| P | 5 | 1024 | none | 8.93 | 7.68 | 1.163 | 8.51 | 7.26 | 1.172 |
| P | 10 | 1024 | none | 9.25 | 8.06 | 1.147 | 8.77 | 7.65 | 1.146 |
| P | 15 | 1024 | none | 9.60 | 8.45 | 1.136 | 9.09 | 8.03 | 1.131 |
| P | 20 | 1024 | none | 11.36 | 10.46 | 1.086 | 10.69 | 9.76 | 1.095 |
| P | 25 | 1024 | none | 12.26 | 11.46 | 1.070 | 11.52 | 10.75 | 1.071 |
| P | 30 | 1024 | none | 13.22 | 11.78 | 1.122 | 12.35 | 11.01 | 1.122 |
| P | 35 | 1024 | none | 15.14 | 14.53 | 1.042 | 12.48 | 11.23 | 1.111 |
| P | 40 | 1024 | none | 15.33 | 14.69 | 1.044 | 14.75 | 13.73 | 1.075 |
| P | 45 | 1024 | none | 15.52 | 14.98 | 1.036 | 14.91 | 13.89 | 1.074 |
| P | 5 | 512 | none | 7.17 | 6.78 | 1.057 | 6.94 | 6.56 | 1.059 |
| P | 10 | 512 | none | 7.49 | 7.10 | 1.054 | 7.14 | 6.72 | 1.062 |
| P | 15 | 512 | none | 7.78 | 7.49 | 1.038 | 7.39 | 7.07 | 1.045 |
| P | 20 | 512 | none | 8.70 | 8.32 | 1.046 | 8.22 | 8.00 | 1.028 |
| P | 25 | 512 | none | 9.44 | 8.67 | 1.089 | 9.02 | 8.13 | 1.110 |
| P | 30 | 512 | none | 9.66 | 8.90 | 1.086 | 9.18 | 8.45 | 1.087 |
| P | 35 | 512 | none | 10.98 | 10.53 | 1.042 | 9.34 | 8.61 | 1.086 |
| P | 40 | 512 | none | 11.14 | 10.78 | 1.033 | 10.78 | 10.11 | 1.066 |
| P | 45 | 512 | none | 11.30 | 11.07 | 1.020 | 10.91 | 10.30 | 1.059 |
| W | 16 | 2048 | none | 15.49 | 14.02 | 1.105 | 14.46 | 12.96 | 1.116 |
| W | 22 | 2048 | none | 16.00 | 14.37 | 1.114 | - | - | - |
| W | 23 | 2048 | none | 17.47 | 16.06 | 1.088 | 14.85 | 13.28 | 1.118 |
| W | 24 | 2048 | none | - | - | - | 16.29 | 14.91 | 1.092 |
| W | 26 | 2048 | none | 17.76 | 16.19 | 1.097 | - | - | - |
| W | 27 | 2048 | none | 20.06 | 16.35 | 1.227 | - | - | - |
| W | 28 | 2048 | none | - | - | - | 16.48 | 15.10 | 1.091 |
| W | 29 | 2048 | none | - | - | - | 18.72 | 15.10 | 1.239 |
| W | 33 | 2048 | none | 20.54 | 16.57 | 1.239 | - | - | - |
| W | 34 | 2048 | none | 24.06 | 20.29 | 1.186 | - | - | - |
| W | 36 | 2048 | none | - | - | - | 18.94 | 15.46 | 1.226 |
| W | 37 | 2048 | none | - | - | - | 23.46 | 18.78 | 1.249 |
| W | 46 | 2048 | none | 31.97 | 24.77 | 1.291 | 23.71 | 19.04 | 1.245 |
| W | 47 | 2048 | none | - | - | - | 31.26 | 22.88 | 1.366 |
| W | 64 | 2048 | none | 32.74 | 25.55 | 1.281 | 31.55 | 23.30 | 1.354 |
| W | 128 | 2048 | none | 63.94 | 48.99 | 1.305 | 61.60 | 44.80 | 1.375
|
| S | 20 | 2048 | suffix | 15.62 | 14.11 | 1.107 | 14.59 | 13.12 | 1.112
|
| S | 45 | 2048 | suffix | 24.54 | 20.80 | 1.180 | 23.65 | 18.98 | 1.246
|

Cake has no other data type, layout or fused form of this kernel, and
this kernel runs on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added generated kernel variants for NVFP4 sparse MLA decode, with
automatic program and split selection based on workload and cluster
size.
  * Added support for a separate KV tensor input used during decoding.
* **Performance**
* Benchmarks report Cake faster than the comparison backend across all
measured shapes on B200 and GB300, with geomean ratios of 0.759 and
0.756, respectively.
* **Documentation**
* Expanded guidance on kernel variants, split planning, launch behavior,
and benchmark results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [38b6198](https://github.com/flashinfer-ai/flashinfer/commit/38b6198055ca44baa10600e62b9c513b59ead0c8)

- **作者**: eigen
- **时间**: 2026-10-25T19:56:06Z
- **提交信息**: perf(cake_mxfp8_megamoe_ep16): pushed routes and rows, direct rank-barrier wait, async-proxy fences (#7350)

`flashinfer.experimental.cake_mxfp8_megamoe_ep16`
(`CakeMxfp8MegaMoeEp16`) runs expert-parallel MoE across 16 ranks. It
supports one data-type configuration: BF16 activations, MXFP8 expert
weights (E4M3 values with E8M0 scales per 32 elements) and BF16 output.
The shape is hidden 3072, intermediate 5120, 512 experts (32 per rank)
and top-8. Each forward runs two kernels: a fused kernel for dispatch,
FC1, SwiGLU, FC2 and return, followed by a top-k reduce kernel. The
module has two backends, CUDA and CuTe DSL. The CUDA backend's fused
kernel is compiled from one body in two token specializations, one for
16 and 64 tokens per rank and one for 32 tokens per rank. Both are
compiled for sm_100a and sm_103a. This PR changes the CUDA backend's
fused kernel, in both specializations on both architectures, and its
host-side buffers, and adds proxy fences to the CuTe DSL backend. The
top-k reduce kernel is unchanged. First, dispatch now pushes data
instead of pulling it. Before the cross-rank barrier, each rank writes
its tokens' routed expert ids, weights and hidden rows into per-source
slots on every rank that owns one of the token's experts, including
itself. The published buffers now hold one slot per source rank: [16, T,
3072] rows and [16, T, 8] routes per rank, where T is tokens per rank.
At 64 tokens per rank this is about 6 MiB of symmetric memory per rank.
After the barrier, dispatch reads ids and rows locally instead of
pulling them over NVLink. The second cross-rank barrier phase still
guards reuse of these slots by the next forward. Second, every CTA now
waits on its rank's barrier flag itself, instead of waiting for a second
GPU-scope hand-off from CTA 0. The per-thread system-scope release fence
after the publication barrier is removed. Ordering is still kept by the
CTA barrier, the elected thread's GPU-scope release and CTA 0's
system-scope fence before its barrier adds. Third, the TMA warp now
executes `fence.proxy.async.global` after it sees that dispatch finished
and after each FC1-completion wait. These fences come before the TMA
loads that read the activation rows and the FC1 workspace, which are
written with generic stores. The CuTe DSL backend gets the same fences,
plus a shared-memory proxy fence before TMA reuses the shared memory
that dispatch wrote. Outputs are bit-identical on all 16 ranks.
End-to-end forward is 1.014x to 1.019x faster than the previous Cake
CUDA backend on main, which already includes the previous round of this
kernel. Every configuration below is faster.

| Tokens per rank (global) | Routing | Previous Cake CUDA (us) | This PR
(us) | Speedup |
|---|---|---:|---:|---:|
| 16 (256) | balanced | 299.9 | 295.4 | 1.015x |
| 16 (256) | hotset50 | 301.1 | 296.0 | 1.017x |
| 32 (512) | balanced | 302.0 | 297.5 | 1.015x |
| 32 (512) | hotset50 | 301.6 | 296.2 | 1.018x |
| 64 (1024) | balanced | 302.6 | 298.5 | 1.014x |
| 64 (1024) | hotset50 | 305.0 | 299.3 | 1.019x |

*16x NVIDIA GB300 (sm_103a), 4 nodes x 4 GPUs in one NVL72 domain, CUDA
13.4; end-to-end eager forward (both kernels) with cold L2; per round,
the slowest rank's median over 100 iterations, averaged over two
sessions of each side; median of 48 interleaved rounds (4 independent
launches x 12 rounds); balanced = uniform top-8, hotset50 = 4 of the 8
slots drawn from the first 128 experts.*

This PR changes the module's other Cake variant, its CuTe DSL backend,
only by adding the proxy fences, and the whole family ships on sm_100a
and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability of distributed expert routing by ensuring route
data and activation rows are available where dispatch needs them.
* Added checks to catch undersized publication buffers with a clear
validation error.
* Updated synchronization around dispatch and data reads to help prevent
stale or incomplete data from being consumed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d4d4bd0](https://github.com/flashinfer-ai/flashinfer/commit/d4d4bd06d109795a48df613b578fcd36baf65789)

- **作者**: eigen
- **时间**: 2026-10-25T19:55:21Z
- **提交信息**: perf(cake_mega_moe): flag-in-data path for up to 32 rows, pushed route codes and post-wait unpermute reads for the BF16 rank-major EP8 layer (#7348)

This PR speeds up the BF16 rank-major expert-parallel (EP8) layer of the
`MoEEpLayer` mega backend for SM100
(`flashinfer/moe_ep/kernel_src/blackwell_bf16_rank_major/`), which Cake
generates. The layer uses BF16 activations, weights and output, with
hidden size 7168, intermediate size 2048, 256 experts (32 per rank),
top-8 routing, 8 ranks and 1 to 128 tokens per rank. It has one variant
(BF16, rank-major, sm_100a). This PR changes only the stages around the
GEMMs; FC1 and FC2 are unchanged. For up to 32 tokens per rank, dispatch
and combine no longer stage data through barriers. Each sender writes
8-byte words, each holding a 4-byte payload and a 4-byte epoch, directly
into the owner rank's receive bank, and the receiver polls those words.
Two banks alternate by epoch parity, and a system-scope release/acquire
pair orders their reuse. The epoch never takes the value of a freshly
zeroed bank, and every rank clears the other bank before the 32-bit
epoch wraps. A forward on this path launches six kernels. Once expert
weights are bound, input staging already sends the rows to the owner
ranks. Before the first weight bind, the inputs are kept and `run()`
sends them. If peers may be waiting on a staged forward, it is completed
internally before new inputs are staged or when `run()` rejects its
arguments. A forward interrupted by a failed launch is resumed or
completed. Inputs or launches recorded in a CUDA graph capture that is
no longer active are dropped. Every rank must call `bind_weights`,
`stage_inputs` and `run` symmetrically. Above 32 tokens per rank, the
input-arrive kernel pushes per-owner route codes and dispatch derives
the routing from them in one extra CTA. The separate route kernel is
therefore no longer launched, and a forward on this path launches eight
kernels. The unpermute kernel now reads the top-k weights and the
inverse permutation only after its grid-dependency wait, and it
prefetches the same lines into L2 before the wait. Outputs are
bit-identical to the previous version on all 8 ranks. The baseline is
the previous Cake version on current FlashInfer main, which already
includes the earlier updates of this layer. Against it, the full layer
forward is 1.01x–1.15x faster in eager mode and 1.01x–1.10x faster under
CUDA graph replay. Every row is faster in both modes, and the largest
gains are at 1 and 2 tokens per rank. In the "all-ranks" routing
pattern, each token's 8 experts sit on 8 different ranks, which is the
pattern the FlashInfer test uses. In "random", each token takes the top
8 of 256 experts from random scores.

| Routing | Tokens per rank | Eager: previous (us) | Eager: this PR (us)
| Eager speedup | CUDA graph: previous (us) | CUDA graph: this PR (us) |
CUDA graph speedup |
|---|---:|---:|---:|---:|---:|---:|---:|
| all-ranks | 1 | 164.6 | 143.4 | 1.15x | 155.5 | 141.2 | 1.10x |
| all-ranks | 2 | 254.8 | 233.5 | 1.09x | 245.7 | 233.3 | 1.05x |
| all-ranks | 4 | 406.5 | 393.1 | 1.03x | 403.5 | 393.7 | 1.02x |
| all-ranks | 8 | 440.1 | 425.9 | 1.03x | 432.1 | 423.9 | 1.02x |
| all-ranks | 16 | 445.4 | 435.8 | 1.02x | 438.3 | 434.1 | 1.01x |
| all-ranks | 32 | 455.7 | 448.6 | 1.02x | 449.6 | 446.4 | 1.01x |
| all-ranks | 64 | 472.1 | 468.3 | 1.01x | 466.8 | 462.7 | 1.01x |
| all-ranks | 128 | 510.9 | 504.8 | 1.01x | 503.8 | 498.9 | 1.01x |
| random | 1 | 194.1 | 174.2 | 1.11x | 187.5 | 171.0 | 1.10x |
| random | 2 | 275.5 | 258.1 | 1.07x | 268.2 | 255.9 | 1.05x |
| random | 4 | 345.1 | 327.6 | 1.05x | 337.8 | 323.6 | 1.04x |
| random | 8 | 404.5 | 387.1 | 1.04x | 397.2 | 386.8 | 1.03x |
| random | 16 | 445.3 | 431.6 | 1.03x | 438.1 | 429.7 | 1.02x |
| random | 32 | 453.6 | 442.4 | 1.03x | 447.5 | 442.2 | 1.01x |
| random | 64 | 467.4 | 463.8 | 1.01x | 460.6 | 456.6 | 1.01x |
| random | 128 | 492.5 | 487.8 | 1.01x | 485.4 | 481.2 | 1.01x |

Measured on 8x NVIDIA B200 (sm_100a, 148 SMs) in one node with the CUDA
13.4 toolkit, PyTorch 2.14.1+cu130 and driver 580.82.07. The full layer
forward (input staging + run) was timed with CUDA events and a cold L2
before each iteration, in eager mode and as CUDA graph replay. Each
number is the slowest rank's median over 20 iterations, then the median
over 12 interleaved rounds that rotate the arm order; speedup = previous
/ this PR.

Cake's other MegaMoE backends in FlashInfer are SM90 BF16 (sm_90a),
MXFP8 EP16 (sm_100a and sm_103a) and SM120 MXFP4 x MXFP8 (sm_120a); this
BF16 rank-major layer ships on sm_100a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a low-latency processing path for workloads with up to 32 active
rows per rank.
* Expanded supported token-count coverage to 128 rows, with larger
small-workload counts using the existing processing path.
* **Bug Fixes**
* Improved handling of staged inputs and in-progress operations during
CUDA graph capture, input restaging, validation errors, and launch
failures.
* **Tests**
* Added coverage for delayed sends, epoch wraparound, graph capture
scenarios, and token-count boundaries.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5e5835e](https://github.com/flashinfer-ai/flashinfer/commit/5e5835ed42f037838c1f0e11ba9dfa67825a134d)

- **作者**: eigen
- **时间**: 2026-10-25T19:14:12Z
- **提交信息**: deslop(cake_mamba_ssd_combined): fold the 21 mask-only sm_107a renders and drop the dead export guard (#7349)

## 📌 Description

### Summary

This PR is a deslop of the Cake-exported `cake_mamba_ssd_combined`
package. The package holds the Cake programs of the SSD combined
operation of `flashinfer.mamba`. The public facade
`flashinfer/mamba/ssd_combined.py` reaches them through
`SSDCombined(backend="cake")` and `ssd_combined_fwd`. This PR does not
edit the facade. The programs target B200 (SM100), GB300 (SM103) and
R200 (SM107). The package is JIT-only, and each program builds lazily
for sm_100a, sm_103a or sm_107a.

At the base, the package has these parts:
- 93 device sources under
`csrc/cake_mamba_ssd_combined/generated/device/`: 51 fold main modules
for the 56 programs, 40 sm_107a renders and 2 shared kernels;
- 5 host templates under `csrc/cake_mamba_ssd_combined/generated/host/`;
- `flashinfer/mamba/cake_ssd_combined.py`, the loader. It holds the 7
fold tables, the `_SM107_MODULES` table, the shared-memory literals and
`_load_generated_program`. `_SM107_MODULES` has 45 entries that name the
40 renders.

Module ids are 10 hex digits, and they appear only in the module name
and the file name. The kernel symbol is `kernel_<stem>` and does not
include the id. So a fold source and its render share the kernel symbol.
Only `_main_module` reads `_SM107_MODULES`, and only for sm_107a.

Three test files cover the package:
- `tests/mamba/test_cake_ssd_combined.py`, the main file, which also
holds the CPU structure tests;
- `tests/mamba/test_cake_ssd_combined_capture.py`;
- `tests/mamba/test_cake_ssd_combined_rubin_tail.py`.

Together they collect 623 ids at the base (529 / 88 / 6) and 620 at the
head. Every id change is in the main file: 3 ids leave and 1 is renamed.

The two commits are mechanical:
- commit 1 folds the 21 sm_107a renders that differ from their fold
source only by the descriptor address mask. It also drops 26 entries of
`_SM107_MODULES`;
- commit 2 drops the dead `_PENDING_EXPORT` / `_require_exported` guard
and the test lines that pin it.

Each commit has an identity proof. For the device sources, the proof
compares preprocessed text, SASS and symbol tables per (program,
architecture). For the Python files, it uses AST checks, reference
searches, digest and host-text recomputation, a planner enumeration and
the test id sets. Each commit section lists its declared deviations and
behaviour notes, and Reviewer Notes repeats them.

Commit 1 folds exporter-written sources by hand and edits the
exporter-written loader table by hand. These folds and edits are pending
exporter regeneration.

Totals versus `main` `a0a6460f6`: 44 files changed, +349 / −46,088.
`generated/device` goes from 93 files to 72. All 56 programs stay
registered, and the 7 fold tables do not change. `_SM107_MODULES` goes
from 45 entries to 19.

### Changes

Base: `main` `a0a6460f6`. Head:
`492a7618af9e42af149c0c2b54210b0094346946` (2 commits). Reviewer Notes
give the `main` sha at publish time.

Files per commit:
- commit 1: the 21 deleted renders, the 21 fold sources, the loader and
`tests/mamba/test_cake_ssd_combined.py`;
- commit 2: the loader and `tests/mamba/test_cake_ssd_combined.py`.

Both commits edit `flashinfer/mamba/cake_ssd_combined.py` and
`tests/mamba/test_cake_ssd_combined.py`. So the per-commit counts do not
sum to the branch totals.

### Commit 1 (8d554bf8f) - fold the 21 mask-only sm_107a renders into
the fold sources (44 files, +326 / −45,942)

- **The copies.** 21 of the 40 sm_107a renders differ from their fold
source only by the shared-memory descriptor address mask. Each pair has
the same line count and exactly 7 differing lines in 4 hunks. Each
differing line changes `& 0x3FFF` to `& 0x7FFF` inside `int
_mma_{a,b}_lo_<n> = make_warp_uniform(...)`. That makes 147 sites in
all. The tcgen05 shared-memory descriptor start-address field is 14 bits
on SM100 / SM103 and 15 bits on SM107. The 21 renders hold 45,726 lines.
Each family below comes in bf16, f16 and f32:
  - exactfused batched and batched_noring, 6 renders;
  - exactpre batched, batched_tail and varlen_tail, 9 renders;
  - chunkpar3 batched and varlen, 6 renders.

Outside `generated/device/`, each of the 21 render ids appears only in
its own `_SM107_MODULES` line. The other 19 renders were regenerated
with a Rubin geometry. They differ from their fold source in 56 to 135
hunks, so they are real per-architecture sources and they stay. The 5
`exactmeta_*` entries are aliases of exactfused varlen renders. The
exactmeta programs are gated to SM100 (`_LIGHT_STAGE_CAPABILITIES ==
((10, 0),)`), so these 5 entries are never requested on sm_107a.
- **Change.**
- After its `#define CAKE_INF CUDART_INF_F` line, each of the 21 fold
sources gains one comment line followed by this block:

    ```cpp
    #if __CUDA_ARCH__ >= 1070
    #define CAKE_SSD_SMEM_DESC_ADDR_MASK 0x7FFF
    #else
    #define CAKE_SSD_SMEM_DESC_ADDR_MASK 0x3FFF
    #endif
    ```
- The 7 mask sites in each source use `& CAKE_SSD_SMEM_DESC_ADDR_MASK`.
Each fold source grows by 6 lines. No other file in the repository uses
the macro name.
  - The 21 render files are deleted.
- `_SM107_MODULES` drops the 21 render entries and the 5 `exactmeta_*`
alias entries, so it goes from 45 entries to 19. The table comment and
the loader's header comment are rewritten to match.
- `test_source_program_table_names_shipped_sources` pins the set of 19
names. Its source-count check keeps `53 + len(rubin_sources)`: 51 fold
modules plus 2 shared kernels plus 19 renders give 72 files. A glob
equality pins that no orphan file remains.
- `test_source_sm107_lookup_shadows_the_fold_main_module` checks the
fold arm for the `exactmeta_*` programs and the folded programs.
- The unrelated pin `len(module._MAIN_ARGS_CHUNKPAR3) == 45` counts
chunkpar3 arguments and does not change. The test ids do not change
(623).
  - No host template, shared kernel or other device file changes.
- **Why behaviour is unchanged.**
- In the sm_107a device pass (`__CUDA_ARCH__` 1070), the macro is
0x7FFF. So each folded source preprocesses to the text of the deleted
render. In the sm_100a and sm_103a passes (1000 and 1030), the macro is
0x3FFF. So the source preprocesses to its own base text.
- The loader passes no `-D` flag on the device line, so only
`__CUDA_ARCH__` selects the mask.
- No routing function reads `_SM107_MODULES`, so program selection does
not change.
- On SM107, the 21 programs now build their fold module. Each one keeps
its kernel symbol, build flags, thread count, shared-memory literal,
cluster dims and host template.
- **Proof.**
- The 63 device rows (21 sources × 3 architectures) compare the
preprocessed device text with a reference. At sm_107a the reference is
the deleted render. At sm_100a and sm_103a it is the base fold.
- On the same 63 rows, SASS and symbol tables must be identical. That
takes 126 compiles.
- The 51 untouched device files and the 5 host templates must coincide
by hash.
- The loader AST must equal the base AST minus the 26 removed keys. In
the test file, only the two functions named above may change.
- A whole-repository search must find no render id and no render module
name at the head.
- Program names must be identical on every planner cell. `_main_module`
may differ only on the 26 sm_107a cells.
- On B200 and GB300, the GPU rows compare per-id test outcomes and the
calibration sweep. The sm_107a rows are compile rows.
- **Declared deviations.**
- The JIT module names of 68 (program, arch) cells change: 21 on sm_100a
and 21 on sm_103a because the fold source bytes change, and 26 on
sm_107a, which are the 21 folded programs and the 5 `exactmeta_*` alias
cells; only the names change, and a warm JIT directory rebuilds the 63
live cells once.
- The rendered host text of the 26 sm_107a cells differs only by the
module identity string.
- The host-pass preprocessed text of a folded source differs from the
deleted render on the 7 mask lines, because the host pass sees 0x3FFF;
the host pass never compiles these device lines.
- clang-format does not run on `generated/` by repository configuration,
so the hygiene row covers the added preprocessor lines.
- The 5 `exactmeta_*` sm_107a alias cells are unreachable by the
capability gate, so their module-name change is dead.
- **Declared.** These are hand folds of exporter-written sources and a
hand edit of the exporter-written loader table.

### Commit 2 (492a7618a) - drop the dead `_PENDING_EXPORT` /
`_require_exported` guard (2 files, +24 / −147)

- **The guard.** The loader carried a guard for table entries that the
Cake export had not filled. The guard had three parts: the constant
`_PENDING_EXPORT = "PENDINGEXPORT"`, the function `_require_exported`,
and the function's one call at the top of `_load_generated_program`. It
refused a program whose main module identity carried the token, or whose
main shared-memory literal was zero or less.
- **Why it is dead.** No table identity carries the token, and all ten
`*_SMEM_BYTES` literals are positive. So the guard condition is false
for every bound program on every architecture. The error text also names
an export script that does not exist in the repository.
- **Change.**
- The loader loses the constant and its comment, `_require_exported` and
its call. It also loses two comment phrases on the shared-memory
literals: "0 is the unfilled placeholder" and "0 = not exported yet".
- `test_source_unexported_program_refuses_to_build` is deleted, with its
ids `[module]` and `[smem]`.
- The sm_107a build test loses its placeholder arm and its
parametrization. It is renamed
`test_source_sm107_program_builds_its_table_module`. Its former
`[filled]` id becomes the new id.
- Three tests drop their token filters and `_require_exported` calls and
keep their filled-only form:
`test_source_program_table_names_shipped_sources`,
`test_active_source_package_declares_cuda_half_types_explicitly` and
`test_source_three_phase_host_template_binds_main_arguments_in_loader_order`.
No new assertion is added.
- No device source, host template or table entry changes. This commit
touches no file under `csrc/`.
  - Test ids go from 623 to 620.
- **Why behaviour is unchanged.** The guard could not fire for any
shipped program on any architecture. Removing it changes no build and no
launch of a shipped program.
- **Proof.**
- A whole-repository search covers `_PENDING_EXPORT`,
`_require_exported`, `PENDINGEXPORT` and the export script's name. At
the base it must find them only in the loader and the main test file. At
the head it must find none.
- At the head, the guard's error phrases must have no hit in the two PR
files.
- The loader AST must equal the commit 1 AST minus three declared nodes:
the assignment, the function and the call.
- In the test file, the per-function AST may differ only by the declared
rewrites in three tests, the one deleted function and the one rename.
- Collect-only must name exactly the 3 removed ids and the 1 renamed id.
- **Behaviour note.** The loader no longer refuses a placeholder
identity or a zero shared-memory literal by name. A placeholder identity
now fails at the device-source read, because the file is missing. A zero
`*_SMEM_BYTES` literal with a filled identity is not caught before the
build. The source and the host module build normally, and the zero
reaches the host template as `CAKE_SSD_MAIN_SMEM_BYTES`. It would
surface only at the kernel launch. So the export must deliver filled
identities and non-zero SMEM literals.
- **Declared deviation.** This commit removes 3 test ids and renames 1,
so the three files go from 623 ids to 620.

### Validation

The compile rows compare the two trees program by program. Each row
stages one fold source and its reference. It builds both with the
loader's compile line, `nvcc -cubin -arch=<arch> --std=c++17 -O3 -I
<nvcc>/../include --use_fast_math`. The loader passes no `-D` flag.
These rows run on a CPU node with CUDA 13.4 for both trees. So they
prove that the two trees are identical under that toolkit. The GPU test
rows build the programs with the CUDA 13.3 of the test image.

There are three gate runs:
- base → commit 1, the only device change: the device text, host pass,
SASS, symbol table and coincidence rows;
- commit 1 → commit 2: `csrc/` is identical, so nothing is compiled;
- base → head: the digest, host text, reference, AST, planner, CPU and
GPU rows.

The collect-only, CPU test and ruff rows also run at commit 1, so each
commit is checked on its own.

Every preprocessed-text row runs one device pass each for
`__CUDA_ARCH__` 1000, 1030 and 1070. The sources carry `#if
__CUDA_ARCH__ == 1000` blocks, so the sm_100a and sm_103a texts differ.
Each row drops line markers and blank lines and compares the normalised
text. No unit uses `__FILE__` or `__LINE__`.

**Chain**

- **Shape.** The two commits sit in order over the base, and their
subjects must match the planned subjects. Commit 1 may touch only the 21
deleted and 21 modified `.cu` files under `generated/device/`, the
loader and the main test file. Commit 2 may touch only the loader and
the main test file. No forbidden shared file may be touched, including
`.pre-commit-config.yaml`, `pyproject.toml`, `flashinfer/__init__.py`,
`flashinfer/jit/**`, `.github/**`, `csrc/cake_selective_state_update/**`
and `tests/mamba/test_cake_selective_state_update.py`. The CPU checks
row reports this.
- **Apply replay.** Each commit's data-driven apply script re-runs in
order on a fresh copy of the base. Each resulting tree must equal that
commit's tree: 2 commits replayed in order on a fresh copy of the base;
each resulting tree is identical to its commit

**Compile rows**

- **Device text.** Each of the 21 fold sources is preprocessed for
sm_107a, sm_100a and sm_103a, which gives 63 rows. At sm_107a the
reference is the deleted render. At sm_100a and sm_103a it is the base
fold. A residue on any row fails that row and names the program: 63/63
compile rows: the device -E text of the folded source equals the base
render on SM107 (21 rows) and the base fold on SM100 / SM103 (42 rows)
after the line-marker drop
- **Host pass.** The host-pass text of each folded source is recorded.
It must equal the base fold. Against the deleted render it may differ
only on the 7 declared mask lines: 21 host-pass rows differ from the
base render only on the declared mask lines (recorded); 42 host-pass
rows identical
- **SASS.** `nvcc -cubin` builds every row on both sides with the
loader's compile line. That gives 21 fold-versus-render rows at sm_107a
and 42 fold-versus-fold rows at sm_100a and sm_103a. `cuobjdump -sass`
output is compared per `Function :` block, after masking addresses and
encodings. No symbol mask is needed, because the kernel symbol is the
same on both sides: 63/63 (per Function block, 126 compiles; CUDA 13.4;
the loader's compile line verbatim)
- **Symbol tables.** The `cuobjdump -symbols` multisets must be
identical. A mask for the source file name (F) applies only to a row
whose symbol table carries a file symbol, and the row reports how often
it applied: 63/63 symbol tables identical (file-symbol mask F applied on
0 rows); .nv.info decoded identical on every row; resource usage
identical on 63/63 rows
- **Coincidence.** The 51 untouched device files and the 5 host
templates are compared by sha256 and not compiled: 56/56 untouched
device / host files byte-identical at both revisions; device files 93 →
72 (21 renders deleted)

**Other rows**

- **Digests.** The JIT module name is
`cake_mamba_ssd_<program>_<arch>_<key16>`. The key hashes the rendered
host source, the architecture and the compiler path. It also hashes the
module name, source bytes and flags of each kernel. The digest rule does
not change. The row recomputes the key for all 168 (program, arch) cells
on both trees with the run's compiler path, because the path string
enters the digest. Expected: 68 names change (21 on sm_100a, 21 on
sm_103a, 26 on sm_107a), 100 stay, and the distinct modules go from 93
to 72 with none new: 168 (program, arch) cells recomputed with the run's
compiler path: module names change on 68 ({"sm_100a": 21, "sm_103a": 21,
"sm_107a": 26}), unchanged on 100; distinct modules 93 → 72
- **Host text.** The loader renders each cell's host source from the
family template, and the template embeds `TVM_FFI_EMBED_CUBIN(<main
module>)`. Expected: identical on all 56 cells of sm_100a and all 56 of
sm_103a, and on 30 of the 56 cells of sm_107a. The other 26 sm_107a
cells may differ only by the module identity, which the row masks:
rendered host text identical on every cell except the module identity
string on 26 SM107 cells; 5/5 host templates byte-identical
- **Reference search.** A whole-repository search at the head looks for
the 21 render ids and the 21 render module names. It also looks for
`_PENDING_EXPORT`, `_require_exported`, `PENDINGEXPORT` and the export
script's name. Each must have hits at the base and none at the head. The
guard's error phrases are searched in the two PR files. The row also
records the plain phrase `is not exported yet`: 2 hits at the head, both
host-template existence asserts in the main test file, within the 4
allowed. An eighth row runs the table census on the head: no alias
entry, 19 `_SM107_MODULES` entries and 72 device files: 8/8 reference
rows: 0 hits at HEAD, defined at the base (incl. the structural table
census)
- **AST.** There are four rows:
- at commit 1, the loader AST must equal the base AST minus the 26
removed `_SM107_MODULES` keys (comments are not part of the AST);
- at the head, the loader AST must equal the commit 1 AST minus the
`_PENDING_EXPORT` assignment, the `_require_exported` function and its
call;
- in the test file, only the declared functions may change at each
commit, and commit 2 deletes one function and renames one.

Result: 4/4 AST rows: the loader equals its base minus the declared
nodes; the test file changes only in the declared functions
- **Planner.** The program-selection stream `(program_name,
_main_module(name, arch))` is enumerated on both trees. It covers the
enumerator grid and the 513 calibration cells, for three capabilities
(SM100, SM103, SM107) and four values of
`FLASHINFER_CAKE_SSD_CHUNK_PARALLEL` (`auto`, which is the default when
the variable is unset, `always`, `three_phase`, `never`). Program names
must be identical on every cell. `_main_module` may differ only on the
26 sm_107a cells and on no sm_100a or sm_103a cell: program selection
identical on 1,079,964 cells (enumerator grid + calibration cells × 3
capabilities × 4 modes); module names differ on exactly the 26 declared
SM107 programs
- **Test id sets.** Collect-only runs on the base, commit 1 and the head
with CUDA hidden. Expected: 623 → 623 → 620. The `[module]` and `[smem]`
ids of `test_source_unexported_program_refuses_to_build` leave. The
sm_107a build test loses its placeholder-arm id. Its `[filled]` id
becomes `test_source_sm107_program_builds_its_table_module`. No other id
may change. The CPU checks row reports the result.
- **Tests with CUDA hidden** on a CPU node. The three files run on the
base, commit 1 and the head. Apart from the declared id changes, per-id
outcomes must be identical, skip reasons included. GPU tests that call
`torch.cuda.get_device_capability()` without a guard fail on every tree,
and these failures are pre-existing. An import probe loads the loader
and the package on each tree. Result: base 623 / HEAD 620 ids with CUDA
hidden: base 410 / commit 1 410 / HEAD 407 passed, 12 skipped and 201
pre-existing failures on every tree, per-id identical apart from the
declared ids (the 3 removed ids and the 1 renamed id: 4 old ids absent,
1 new id), every surviving base-passed id (406) passes on the head;
loader + package import probes OK on both trees
- **Tests on B200** (SM100). The three files run on the base tree, then
on the head tree, in one step on one B200 node. Each arm uses a fresh
JIT directory, so every module it reaches is built from source. Apart
from the declared id changes, per-id outcomes must be identical, skip
reasons included. Thresholds are read from the base arm. On B200, the 3
ids of `test_cake_ssd_combined_exactone_flags_out_of_range_seq_idx` skip
by design, because that test routes on SM103 and SM107 only. The 2 ids
that need two GPUs skip when the step exposes one GPU. Result: base 623
/ HEAD 620 ids on B200 (SM100) (driver 580.82.07, cc 10.0): 615 passed /
5 skipped, per-id identical on both trees incl. skip reasons (the 3
removed ids and the 1 renamed id declared: 4 old ids absent, 1 new id);
fresh JIT workspace per arm (38 programs built per arm, every module
name in the arm's digest table)
- **Tests on GB300** (SM103). The same two-arm run on one GB300 node.
The exactone ids run there; only the 2 ids that need two GPUs skip.
Result: base 623 / HEAD 620 ids on GB300 (SM103) (driver 580.159.03, cc
10.3): 618 passed / 2 skipped, per-id identical on both trees incl. skip
reasons (the 3 removed ids and the 1 renamed id declared: 4 old ids
absent, 1 new id); fresh JIT workspace per arm (38 programs built per
arm, every module name in the arm's digest table)
- **Tests on R200** (SM107), best effort. The same two-arm run on one
R200 node. `tests/mamba/conftest.py` skips every mamba test when the
installed Triton cannot target the GPU, so this run can report every id
as skipped. The sm_107a compile rows above are the evidence of record
for this architecture. Result, or the reason the row did not run: not
run on R200 (SM107): no R200 GPU with a CUDA 13.4 PyTorch environment is
available for this validation; the SM107 identity proof is the
compile-only rows (preprocessed text, SASS, resource usage, symbol
tables and metadata of every folded source against the base SM107
render)
- **JIT isolation.** Before each GPU arm, the JIT directory is fresh and
holds no `cake_mamba_ssd_*` module directory. After the tests and the
sweep, the module directories are compared by program name, which is the
directory name without `_<arch>_<key16>`. The program-name sets must be
identical between arms, and every directory must appear in that arm's
digest table: B200 (SM100): 38 programs built per arm in a fresh JIT
dir, module names changed on 14 programs, every one of them among the 21
declared for the arch (the other declared programs are not reached by
the test shapes or the sweep); 24 unchanged; GB300 (SM103): 38 programs
built per arm in a fresh JIT dir, module names changed on 14 programs,
every one of them among the 21 declared for the arch (the other declared
programs are not reached by the test shapes or the sweep); 24 unchanged
- **Calibration sweep.** On each GPU, each tree records
`last_program_name` for the 513 calibration cells through both entries,
`SSDCombined(backend="cake").run` and `ssd_combined_fwd`. Program names
and the hashes of the output and the final state must be identical
between trees and between entries: B200 (SM100): 513 calibration cells ×
2 entries, 0 program / output / final-state differences base vs HEAD, 0
entry-to-entry differences; GB300 (SM103): 513 calibration cells × 2
entries, 0 program / output / final-state differences base vs HEAD, 0
entry-to-entry differences
- **CPU checks.** These run on one node, on both trees:
  - chain shape and commit-message form;
  - `git diff --check` and the per-commit file scope;
  - forbidden files untouched;
  - `py_compile`;
  - ruff check and `ruff format --check` on the two touched `.py` files;
  - collect-only parity;
  - the CPU test run and the import probe;
  - pre-commit on the changed files, and with `--all-files`;
- the repository's mypy hook on `flashinfer/mamba/cake_ssd_combined.py`,
with no new finding;
  - the reference rows, the AST rows and the planner enumeration;
  - the digest and host-text rows;
  - the apply replay;
- file hygiene per modified file against its base bytes: trailing
newline kept, blank-line runs no longer than in the base, no tabs or
CRLF;
  - the public-text scan;
  - the trailer and subject check;
  - a clean worktree.

  Result: 21/21
- **Rows limited by the environment (count and reason):** 1 row: the
R200 (SM107) test row (no R200 GPU with a CUDA 13.4 PyTorch environment
is available for this validation; the SM107 identity proof is the
compile-only rows: preprocessed text, SASS, resource usage, symbol
tables and metadata of every folded source against the base SM107
render)

### Not in this PR

- **Retiring the chunkpar3 varlen family.** Only the
`FLASHINFER_CAKE_SSD_CHUNK_PARALLEL` override reaches these programs.
Their 3 fold sources stay. Commit 1 removes only their 3 mask-only
sm_107a copies. Retiring the family is an owner and performance
decision.
- **The batched noring window of the exact family.** Dropping it needs a
bitwise re-run of the ring and noring outputs and a profiler gate.
- **One SSD source per shape with a state-type define.** This is
exporter-side work and an API decision.
- **The ring / noring fold or retirement.** This is exporter-side work
and depends on a performance gate.
- **One host template.** Rendering the 5 host templates from one
template, with shared argument checks and cached tensor-map descriptors,
is a structural change.
- **The selective-state-update clones.** A separate re-export of that
package supersedes them. This PR touches no selective-state-update path.
- **The calibration log and the table-structure tests.** Moving the
calibration log to docs and pruning table-structure tests are not
mechanical changes.
- **Performance-gated retirements, hot-path trims and owner decisions.**
These need performance evidence or an owner decision.
- **Exporter emission.** Commit 1 folds exporter-written sources by hand
and edits the exporter-written loader table by hand. These folds and
edits are pending exporter regeneration. The exporter rules are filed on
#7215 as a comment.

## 🔍 Related Issues

Tracking issue: #7215

Part of #7215

The deferred items are listed under "Not in this PR". The exporter rules
are filed on #7215 as a comment.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks run on the changed files and with `--all-files` on both
checkouts, clang-format does not run on `generated/` by repository
configuration, and the CPU checks row in Validation gives the results.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

This PR updates one test file, `tests/mamba/test_cake_ssd_combined.py`.
Commit 1 rewrites its table pins for the 19 `_SM107_MODULES` entries,
keeps the file-count pin `53 + len(rubin_sources)`, and changes no id.
Commit 2 deletes `test_source_unexported_program_refuses_to_build`. It
also removes the placeholder arm of the sm_107a build test and renames
that test `test_source_sm107_program_builds_its_table_module`.
`tests/mamba/test_cake_ssd_combined_capture.py` and
`tests/mamba/test_cake_ssd_combined_rubin_tail.py` are not edited. The
three files collect 623 ids at the base and 620 at the head. Validation
lists the run with CUDA hidden on a CPU node. It also lists the GPU runs
on B200 and GB300, and it records the R200 row as not run.

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.

This PR is not experimental. The package lives under
`csrc/cake_mamba_ssd_combined/` and `flashinfer/mamba/`, and its tests
live under `tests/mamba/`. So this PR declares no experimental test
scope.

## Reviewer Notes

- **Hand folds and hand edits.** Commit 1 folds 21 exporter-written
device sources by hand and edits the exporter-written loader table by
hand. A re-export re-hashes the 21 fold ids and the loader tables.
Re-adding the 21 copies would undo the fold. The exporter rules are
filed on #7215 as a comment.
- **Formatting.** clang-format does not run on `generated/` by
repository configuration. So the hygiene row checks the added
preprocessor lines against each file's base bytes. Ruff check and `ruff
format --check` cover the two Python files.
- **Declared deviations.**
- Commit 1: the JIT module names of 68 (program, arch) cells change (21
on sm_100a, 21 on sm_103a, 26 on sm_107a); only the names change, and a
warm JIT directory rebuilds the 63 live cells once.
- Commit 1: the rendered host text of the 26 sm_107a cells differs only
by the module identity string.
- Commit 1: the host-pass preprocessed text of a folded source differs
from the deleted render on the 7 mask lines; the host pass never
compiles these device lines.
- Commit 1: clang-format does not run on `generated/` by repository
configuration, so the hygiene row covers the added preprocessor lines.
- Commit 1: the 5 `exactmeta_*` sm_107a alias cells are unreachable by
the capability gate, so their module-name change is dead.
- Commit 2: 3 test ids leave and 1 is renamed, so the three files go
from 623 ids to 620.
- **Behaviour notes.**
- Commit 1: program selection and outputs do not change. On SM107, the
21 folded programs build their fold module with the same kernel symbol,
flags, threads, shared memory and cluster dims.
- Commit 2: the loader no longer refuses a placeholder identity or a
zero shared-memory literal by name. A placeholder identity fails at the
device-source read. A zero `*_SMEM_BYTES` literal with a filled identity
would surface only at the kernel launch. So the export must deliver
filled identities and non-zero SMEM literals.
- **Module cache.** 68 JIT module names change. A warm JIT directory
rebuilds the 63 live cells once, for both the main and the preprocess
cubin. `CakeSSDCombined.last_program_name` is the program name, and it
does not change. No public attribute exposes the module name. On
sm_107a, the embedded cubin module name and the host
`EmbedCubinModule_<module>` symbol now carry the fold id. The kernel
symbol does not change.
- **Toolkit.** The compile rows use CUDA 13.4 for both arms. They prove
that the two trees are identical under that toolkit. The GPU tests build
the programs with CUDA 13.3.
- **Coverage.**
- The Cake GPU tests skip unless the capability is SM100, SM103 or
SM107. On H100 (SM90), only the CPU tests run.
- The GPU test phase builds only the modules that the test shapes reach.
The JIT isolation row counts the programs each arm built, and the
calibration sweep covers the 513 calibration cells.
- The sm_107a compile rows are the evidence of record for SM107. The
R200 row is best effort and did not run.
- **Base.** This PR is published from `main` `a0a6460f6`. `main` at
publish time is `0cdbe67b8`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated program selection on SM107 for fused variable-length scans,
chunk-parallel operations, and variable-length ring operations.
* Other supported operations on SM107 now use their regular program
variants.
  * Program loading no longer requires a separate export-status check.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [53f6bc4](https://github.com/flashinfer-ai/flashinfer/commit/53f6bc4d3f47876542206e5c8e430dcee0102c2f)

- **作者**: eigen
- **时间**: 2026-10-25T18:59:50Z
- **提交信息**: perf(cake_warp_decode): linear-grid K256 FC2 for the H4096/E512 shard rows (#7339)

`cake_warp_decode` is Cake's NVFP4 routed fused-MoE decode for 1 to 32
tokens, called through
`flashinfer.fused_moe.trtllm_fp4_block_scale_routed_moe(...)` with
`CakeWarpDecodeConfig(backend="cake")`. It has one data type (NVFP4
W4A4, BF16 output), five activation variants and one fused form: FC1
with the activation, FC2 and the top-k finalize. This PR adds one FC2
program and routes rows from the two hidden-4096, 512-expert, top-10
geometries to it. On sm_100a these are `h4096_e512_i256_k10` at 9 to 32
tokens and `h4096_e512_i512_k10` at 19 to 32 tokens (38 rows). On
sm_103a they are the same geometries at 7 to 32 and 12 to 32 tokens (47
rows). All other rows run the same kernels as FlashInfer main.

The new program is the K256 FC2 (one fused K=256 MMA per 128-row output
tile of an 8-token route tile) on a 1-D linear grid with an unthrottled
work queue, and its outputs are bit-identical to the previous program's.
Against the previous Cake version on FlashInfer main, the changed rows
run up to 1.05x faster on both sm_100a and sm_103a. The
`h4096_e512_i512_k10` rows gain less, about 2 % at most, and some
changed rows gain under 1 %.

The "memset" and "read" column groups are two cold-L2 modes: before
every call, we flush L2 with a memset of a large buffer or a read of
one.

**sm_100a** (NVIDIA GB200, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake version
(FlashInfer main), new = this PR; ratio = new / previous. **Bold**
num_tokens = rows this PR routes to the new program.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.41|14.40|0.999|12.59|12.57|0.998|
|2|19.26|19.14|0.994|16.90|16.83|0.996|
|3|22.78|22.95|1.008|19.28|19.22|0.997|
|4|26.60|26.45|0.994|22.01|21.94|0.997|
|5|30.67|30.60|0.998|24.86|24.76|0.996|
|6|33.69|34.10|1.012|26.94|26.83|0.996|
|7|37.26|37.31|1.001|29.34|29.24|0.997|
|8|40.20|40.29|1.002|31.63|31.42|0.993|
|9|43.30|43.34|1.001|34.00|33.97|0.999|
|10|46.46|46.49|1.001|36.51|36.59|1.002|
|11|49.46|49.51|1.001|38.97|38.99|1.001|
|12|52.66|52.71|1.001|41.67|41.47|0.995|
|13|56.04|55.92|0.998|44.06|43.90|0.997|
|14|59.18|59.20|1.000|46.38|46.46|1.002|
|15|62.28|62.41|1.002|49.18|49.05|0.997|
|16|65.56|65.52|0.999|52.09|51.92|0.997|
|17|67.51|67.55|1.001|54.00|53.82|0.997|
|18|70.23|70.26|1.000|56.26|56.25|1.000|
|19|72.41|72.34|0.999|57.99|58.03|1.001|
|20|71.59|71.55|0.999|57.28|57.12|0.997|
|21|71.54|71.59|1.001|57.30|57.32|1.000|
|22|71.62|71.65|1.000|57.39|57.33|0.999|
|23|71.49|71.57|1.001|57.27|57.44|1.003|
|24|71.50|71.64|1.002|57.35|57.34|1.000|
|25|71.71|71.65|0.999|57.51|57.52|1.000|
|26|71.74|71.55|0.997|57.34|57.65|1.005|
|27|71.70|71.62|0.999|57.59|57.66|1.001|
|28|71.62|71.84|1.003|57.63|57.56|0.999|
|29|71.65|71.58|0.999|57.58|57.58|1.000|
|30|71.85|71.69|0.998|57.60|57.60|1.000|
|31|71.75|71.71|0.999|57.61|57.57|0.999|
|32|72.71|72.73|1.000|58.34|58.42|1.001|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.87|16.73|0.991|15.62|15.41|0.987|
|2|22.72|22.84|1.005|20.80|20.99|1.009|
|3|26.87|26.90|1.001|24.54|24.53|1.000|
|4|33.15|33.22|1.002|29.51|29.65|1.005|
|5|37.33|37.47|1.004|33.69|33.75|1.002|
|6|42.38|42.30|0.998|38.28|38.21|0.998|
|7|46.86|46.74|0.998|42.83|42.86|1.001|
|8|51.49|51.33|0.997|47.15|46.92|0.995|
|9|56.07|56.15|1.001|51.66|51.70|1.001|
|10|61.01|61.14|1.002|56.02|56.08|1.001|
|11|65.74|65.64|0.998|60.52|60.57|1.001|
|12|70.81|70.85|1.001|64.90|65.06|1.002|
|13|75.00|75.11|1.001|69.32|69.34|1.000|
|14|80.02|79.95|0.999|73.30|73.06|0.997|
|15|84.83|84.66|0.998|78.45|78.22|0.997|
|16|89.25|89.14|0.999|82.04|82.01|1.000|
|17|93.92|93.84|0.999|87.11|87.02|0.999|
|18|98.59|98.70|1.001|91.08|91.09|1.000|
|**19**|102.93|102.30|0.994|95.30|93.94|0.986|
|**20**|107.31|106.86|0.996|99.46|98.23|0.988|
|**21**|111.82|111.06|0.993|103.52|102.09|0.986|
|**22**|116.54|116.18|0.997|108.39|107.06|0.988|
|**23**|121.20|120.52|0.994|112.34|110.68|0.985|
|**24**|125.39|124.73|0.995|117.19|115.23|0.983|
|**25**|130.26|129.41|0.993|121.18|119.40|0.985|
|**26**|134.85|133.95|0.993|125.91|123.83|0.983|
|**27**|139.18|138.21|0.993|129.79|127.82|0.985|
|**28**|143.82|142.67|0.992|134.20|131.92|0.983|
|**29**|148.36|147.43|0.994|138.66|136.22|0.982|
|**30**|152.75|151.81|0.994|142.70|140.66|0.986|
|**31**|157.30|156.26|0.993|146.81|144.65|0.985|
|**32**|161.86|160.59|0.992|151.61|148.80|0.981|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.64|14.86|1.015|13.82|14.08|1.019|
|2|17.64|17.50|0.992|16.46|16.32|0.992|
|3|20.77|20.74|0.998|19.16|19.18|1.001|
|4|24.90|24.83|0.997|23.41|23.41|1.000|
|5|27.09|27.22|1.005|25.23|25.38|1.006|
|6|29.56|29.58|1.001|27.58|27.64|1.002|
|7|32.69|32.77|1.002|30.43|30.46|1.001|
|8|36.97|36.93|0.999|34.05|33.73|0.991|
|**9**|39.26|38.83|0.989|36.56|35.95|0.983|
|**10**|41.96|41.18|0.982|39.04|38.23|0.979|
|**11**|44.86|43.78|0.976|41.66|40.54|0.973|
|**12**|48.13|46.58|0.968|44.87|43.31|0.965|
|**13**|50.59|49.09|0.970|47.46|45.88|0.967|
|**14**|53.26|51.46|0.966|49.92|48.05|0.963|
|**15**|56.55|54.58|0.965|52.85|50.90|0.963|
|**16**|59.14|57.18|0.967|55.20|53.29|0.965|
|**17**|61.83|59.80|0.967|57.86|55.83|0.965|
|**18**|64.82|62.39|0.962|60.52|58.17|0.961|
|**19**|67.50|65.17|0.966|63.36|60.80|0.960|
|**20**|70.50|67.96|0.964|65.90|63.27|0.960|
|**21**|73.04|70.06|0.959|68.26|65.37|0.958|
|**22**|75.55|72.86|0.964|70.98|67.98|0.958|
|**23**|78.64|75.94|0.966|73.70|70.86|0.962|
|**24**|81.50|78.41|0.962|76.66|73.26|0.956|
|**25**|84.58|80.88|0.956|79.08|75.71|0.957|
|**26**|86.82|83.51|0.962|81.64|78.46|0.961|
|**27**|90.00|86.20|0.958|84.46|80.80|0.957|
|**28**|92.33|88.83|0.962|87.06|83.47|0.959|
|**29**|95.46|91.75|0.961|89.82|86.15|0.959|
|**30**|98.10|94.02|0.958|92.57|88.46|0.956|
|**31**|100.74|96.55|0.958|94.85|90.73|0.957|
|**32**|103.84|99.38|0.957|98.18|93.46|0.952|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.52|16.46|0.996|14.88|14.91|1.002|
|2|22.03|21.93|0.995|20.02|19.90|0.994|
|3|25.63|25.49|0.994|22.90|23.02|1.005|
|4|29.62|29.61|0.999|26.48|26.58|1.004|
|5|34.94|34.91|0.999|30.94|31.01|1.002|
|6|38.86|38.75|0.997|34.75|34.71|0.999|
|7|42.96|42.96|1.000|38.33|38.37|1.001|
|8|47.05|47.06|1.000|42.33|42.36|1.001|
|9|51.06|51.18|1.003|45.70|45.65|0.999|
|10|55.54|55.65|1.002|49.65|49.81|1.003|
|11|59.43|59.39|0.999|53.06|53.22|1.003|
|12|63.34|63.26|0.999|56.83|56.94|1.002|
|13|67.67|67.58|0.999|60.58|60.56|1.000|
|14|71.35|71.32|1.000|64.14|64.05|0.999|
|15|75.27|75.31|1.001|68.08|68.00|0.999|
|16|75.30|75.38|1.001|68.02|67.90|0.998|
|17|75.70|75.75|1.001|68.07|68.14|1.001|
|18|75.50|75.70|1.003|68.22|68.13|0.999|
|19|75.58|75.62|1.001|68.14|68.18|1.001|
|20|75.55|75.58|1.000|68.12|68.17|1.001|
|21|75.69|75.67|1.000|68.05|68.10|1.001|
|22|75.70|75.66|0.999|68.17|68.29|1.002|
|23|75.58|75.69|1.001|68.21|68.18|1.000|
|24|75.54|75.71|1.002|68.17|68.13|0.999|
|25|75.66|75.82|1.002|68.35|68.32|1.000|
|26|75.83|75.86|1.000|68.26|68.41|1.002|
|27|75.74|75.82|1.001|68.32|68.34|1.000|
|28|75.82|75.79|1.000|68.32|68.14|0.997|
|29|75.95|75.83|0.998|68.30|68.29|1.000|
|30|75.78|75.82|1.001|68.30|68.35|1.001|
|31|75.88|75.66|0.997|68.24|68.33|1.001|
|32|75.68|75.95|1.004|68.26|68.36|1.001|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.06|13.93|0.991|13.15|13.24|1.007|
|2|16.81|16.72|0.995|15.46|15.50|1.003|
|3|19.64|19.56|0.996|17.66|17.84|1.010|
|4|22.17|22.11|0.997|20.10|20.03|0.997|
|5|24.57|24.42|0.994|22.26|22.29|1.001|
|6|26.98|26.98|1.000|24.23|24.10|0.994|
|7|29.67|29.66|0.999|26.72|26.70|0.999|
|8|31.37|31.55|1.006|28.30|28.42|1.004|
|9|33.84|33.94|1.003|30.27|30.30|1.001|
|10|36.10|36.07|0.999|32.48|32.45|0.999|
|11|38.46|38.45|1.000|34.55|34.67|1.003|
|12|40.31|40.50|1.005|36.45|36.52|1.002|
|13|42.59|42.44|0.996|38.56|38.51|0.999|
|14|44.66|44.50|0.996|40.48|40.38|0.998|
|15|46.51|46.58|1.001|42.34|42.31|0.999|
|16|46.56|46.73|1.004|42.31|42.30|1.000|
|17|46.68|46.63|0.999|42.32|42.35|1.001|
|18|46.58|46.81|1.005|42.28|42.63|1.008|
|19|46.74|46.65|0.998|42.41|42.43|1.001|
|20|46.85|46.71|0.997|42.58|42.36|0.995|
|21|46.78|46.91|1.003|42.44|42.48|1.001|
|22|46.82|46.76|0.999|42.32|42.31|1.000|
|23|46.82|46.84|1.000|42.42|42.56|1.003|
|24|46.80|46.76|0.999|42.68|42.42|0.994|
|25|46.96|47.02|1.001|42.63|42.65|1.000|
|26|47.32|47.14|0.996|42.97|42.62|0.992|
|27|47.23|47.17|0.999|42.95|42.58|0.991|
|28|46.92|47.07|1.003|42.42|42.58|1.004|
|29|47.12|46.97|0.997|42.96|42.68|0.993|
|30|47.18|47.20|1.001|42.77|42.67|0.998|
|31|46.98|47.10|1.003|42.57|42.80|1.005|
|32|47.21|47.14|0.999|42.79|42.62|0.996|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.24|14.25|1.001|12.74|12.81|1.005|
|2|19.29|18.93|0.981|17.00|16.46|0.968|
|3|21.84|21.70|0.993|18.46|18.42|0.998|
|4|25.99|25.77|0.991|21.66|21.46|0.991|
|5|28.26|28.35|1.003|22.99|22.77|0.990|
|6|31.86|31.86|1.000|25.72|25.70|0.999|
|7|34.61|34.42|0.995|27.49|27.27|0.992|
|8|37.24|37.27|1.001|29.35|29.41|1.002|
|9|39.83|39.92|1.002|31.40|31.42|1.001|
|10|42.71|42.78|1.002|33.94|33.94|1.000|
|11|45.59|45.39|0.996|36.06|35.82|0.994|
|12|48.09|48.23|1.003|38.26|38.16|0.997|
|13|51.07|51.18|1.002|40.28|40.19|0.998|
|14|53.61|53.81|1.004|42.38|42.84|1.011|
|15|56.55|56.60|1.001|44.99|44.84|0.997|
|16|59.05|59.02|1.000|47.08|47.22|1.003|
|17|61.71|61.61|0.998|49.16|49.45|1.006|
|18|64.33|64.33|1.000|51.56|51.59|1.001|
|19|66.70|66.72|1.000|53.80|53.62|0.997|
|20|69.11|69.11|1.000|55.94|55.93|1.000|
|21|71.38|71.47|1.001|58.37|58.45|1.001|
|22|73.76|73.83|1.001|60.42|60.67|1.004|
|23|76.23|76.07|0.998|62.63|62.59|0.999|
|24|78.58|78.61|1.000|64.84|65.02|1.003|
|25|81.00|80.89|0.999|67.19|67.21|1.000|
|26|83.36|83.54|1.002|69.48|69.74|1.004|
|27|85.96|85.90|0.999|71.70|71.61|0.999|
|28|88.46|88.28|0.998|74.02|73.76|0.996|
|29|90.86|90.90|1.000|75.97|76.01|1.001|
|30|93.49|93.66|1.002|78.26|78.37|1.001|
|31|95.94|95.97|1.000|80.64|80.66|1.000|
|32|98.42|98.54|1.001|82.92|82.81|0.999|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.13|14.53|1.028|12.50|12.78|1.022|
|2|17.26|17.42|1.009|15.24|15.21|0.998|
|3|21.54|21.47|0.997|18.22|18.18|0.998|
|4|23.83|23.96|1.005|19.94|20.06|1.006|
|5|27.94|27.83|0.996|22.62|22.50|0.995|
|6|30.66|30.53|0.996|24.30|24.23|0.997|
|7|33.03|33.14|1.003|25.98|26.17|1.007|
|8|35.98|36.14|1.005|28.42|28.74|1.012|
|9|38.15|38.26|1.003|29.74|29.90|1.005|
|10|40.70|40.79|1.002|31.71|31.86|1.005|
|11|43.00|43.05|1.001|33.35|33.12|0.993|
|12|45.06|45.25|1.004|34.84|35.08|1.007|
|13|47.09|47.23|1.003|36.56|36.65|1.002|
|14|49.45|49.34|0.998|38.16|38.22|1.002|
|15|49.12|49.01|0.998|38.98|39.04|1.002|
|16|51.06|50.98|0.998|40.50|40.47|0.999|
|17|52.81|52.85|1.001|41.74|41.64|0.998|
|18|54.79|54.81|1.000|43.48|43.47|1.000|
|19|56.51|56.63|1.002|44.72|44.78|1.001|
|20|58.23|58.38|1.003|45.99|46.17|1.004|
|21|59.87|59.86|1.000|47.58|47.67|1.002|
|22|61.78|61.70|0.999|49.01|49.02|1.000|
|23|63.51|63.46|0.999|50.38|50.46|1.002|
|24|65.03|65.01|1.000|51.86|51.86|1.000|
|25|66.97|67.02|1.001|53.46|53.43|0.999|
|26|68.65|68.71|1.001|54.79|54.74|0.999|
|27|68.68|68.65|1.000|54.75|54.83|1.001|
|28|68.65|68.75|1.002|54.85|54.70|0.997|
|29|68.62|68.66|1.001|54.82|54.78|0.999|
|30|68.71|68.82|1.002|54.94|54.78|0.997|
|31|68.72|68.69|1.000|54.79|54.88|1.002|
|32|68.73|68.61|0.998|54.94|54.93|1.000|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|20.06|20.08|1.001|17.66|17.76|1.005|
|2|26.03|26.04|1.000|21.20|21.09|0.995|
|3|31.62|31.33|0.991|25.53|25.25|0.989|
|4|38.76|38.70|0.998|30.69|30.64|0.998|
|5|43.51|43.47|0.999|34.18|33.88|0.991|
|6|47.97|48.03|1.001|37.50|37.78|1.008|
|7|55.08|55.09|1.000|42.92|42.74|0.996|
|8|59.55|59.58|1.000|46.35|46.30|0.999|
|9|64.26|64.35|1.001|50.49|50.13|0.993|
|10|69.57|69.64|1.001|55.21|55.21|1.000|
|11|73.50|73.56|1.001|59.24|59.08|0.997|
|12|77.91|77.93|1.000|63.12|62.98|0.998|
|13|82.52|82.58|1.001|67.68|67.89|1.003|
|14|87.13|87.12|1.000|72.30|72.20|0.999|
|15|91.61|91.32|0.997|76.23|76.17|0.999|
|16|96.02|96.10|1.001|80.96|80.84|0.999|
|17|100.21|100.02|0.998|85.11|85.08|1.000|
|18|104.59|104.40|0.998|89.20|89.48|1.003|
|19|109.34|109.34|1.000|94.02|93.94|0.999|
|20|113.49|113.75|1.002|98.08|98.26|1.002|
|21|117.96|117.87|0.999|102.43|102.17|0.997|
|22|122.86|122.78|0.999|106.72|106.86|1.001|
|23|126.91|127.11|1.002|110.89|110.78|0.999|
|24|131.39|131.20|0.999|115.10|115.33|1.002|
|25|135.34|135.38|1.000|119.25|119.37|1.001|
|26|140.42|140.43|1.000|123.82|123.74|0.999|
|27|144.76|144.73|1.000|128.01|127.91|0.999|
|28|148.66|149.07|1.003|131.85|132.35|1.004|
|29|153.41|153.49|1.001|136.82|136.67|0.999|
|30|157.66|157.52|0.999|140.91|140.82|0.999|
|31|161.97|161.58|0.998|145.22|144.75|0.997|
|32|166.10|166.10|1.000|149.38|149.21|0.999|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.11|12.18|1.005|11.14|11.19|1.005|
|2|14.96|14.98|1.001|13.46|13.42|0.997|
|3|17.12|17.08|0.998|15.22|15.27|1.004|
|4|19.47|19.64|1.009|17.39|17.74|1.020|
|5|21.18|21.26|1.004|18.26|18.48|1.012|
|6|23.21|23.10|0.995|19.48|19.29|0.990|
|7|25.96|25.60|0.986|22.14|21.98|0.993|
|8|27.40|27.54|1.005|22.94|22.78|0.993|
|9|29.08|29.26|1.006|23.76|23.78|1.001|
|10|31.68|31.51|0.995|26.28|26.08|0.992|
|11|33.02|33.06|1.001|27.09|26.86|0.991|
|12|34.76|34.72|0.999|27.84|27.85|1.000|
|13|36.29|36.24|0.999|29.19|29.17|0.999|
|14|38.01|38.13|1.003|30.41|30.30|0.997|
|15|39.62|39.78|1.004|31.38|31.39|1.001|
|16|41.33|41.38|1.001|32.92|32.84|0.998|
|17|42.84|42.70|0.997|34.30|34.13|0.995|
|18|44.66|44.47|0.996|35.30|35.23|0.998|
|19|46.27|46.51|1.005|36.72|36.78|1.002|
|20|47.95|48.01|1.001|38.00|38.06|1.002|
|21|49.56|49.67|1.002|39.22|39.38|1.004|
|22|51.50|51.70|1.004|40.63|40.87|1.006|
|23|53.17|53.06|0.998|42.12|42.06|0.998|
|24|54.91|54.90|1.000|43.26|43.35|1.002|
|25|56.62|56.71|1.002|44.90|44.94|1.001|
|26|58.30|58.31|1.000|46.24|46.18|0.999|
|27|60.05|60.12|1.001|47.38|47.42|1.001|
|28|61.76|61.72|0.999|48.90|48.76|0.997|
|29|63.25|63.34|1.001|50.26|50.30|1.001|
|30|64.60|64.47|0.998|51.45|51.42|0.999|
|31|66.16|66.13|1.000|52.71|52.82|1.002|
|32|67.61|67.66|1.001|54.24|54.17|0.999|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|26.74|26.77|1.001|22.54|22.70|1.007|
|2|40.50|40.49|1.000|32.30|32.22|0.998|
|3|53.37|53.51|1.003|42.05|42.17|1.003|
|4|65.39|65.35|0.999|51.95|52.01|1.001|
|5|77.10|77.15|1.001|62.45|62.55|1.002|
|6|87.46|87.45|1.000|72.32|72.45|1.002|
|7|97.94|97.98|1.000|82.45|82.34|0.999|
|8|108.14|108.55|1.004|92.39|92.63|1.003|
|9|118.72|118.83|1.001|102.48|102.49|1.000|
|10|128.98|128.77|0.998|112.37|112.51|1.001|
|11|138.71|138.86|1.001|122.36|122.44|1.001|
|12|149.02|149.08|1.000|131.95|132.11|1.001|
|13|158.83|158.78|1.000|141.82|141.72|0.999|
|14|168.47|168.41|1.000|151.59|151.58|1.000|
|15|178.22|178.38|1.001|161.50|161.34|0.999|
|16|187.74|187.74|1.000|170.73|170.82|1.001|
|17|195.27|195.33|1.000|178.47|178.38|1.000|
|18|202.15|202.21|1.000|185.31|185.42|1.001|
|19|209.20|209.22|1.000|192.38|192.29|0.999|
|20|209.19|209.23|1.000|192.42|192.42|1.000|
|21|209.25|209.53|1.001|192.26|192.52|1.001|
|22|209.42|209.34|1.000|192.66|192.37|0.999|
|23|209.55|209.46|1.000|192.53|192.61|1.000|
|24|209.60|209.50|1.000|192.64|192.62|1.000|
|25|210.14|210.09|1.000|193.50|193.53|1.000|
|26|210.21|210.14|1.000|193.76|193.70|1.000|
|27|210.25|210.17|1.000|193.61|193.74|1.001|
|28|210.27|210.21|1.000|193.87|193.66|0.999|
|29|210.40|210.30|1.000|193.79|193.97|1.001|
|30|210.23|210.43|1.001|193.78|193.90|1.001|
|31|210.46|210.36|1.000|193.86|193.86|1.000|
|32|210.34|210.47|1.001|193.79|193.85|1.000|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.78|12.78|1.000|11.66|11.66|1.000|
|2|16.44|16.47|1.002|14.48|14.56|1.006|
|3|19.73|19.74|1.000|17.22|17.27|1.003|
|4|22.02|21.74|0.988|18.78|18.53|0.987|
|5|24.58|24.57|1.000|20.48|20.50|1.001|
|6|26.95|27.07|1.004|22.21|22.22|1.001|
|7|29.32|29.30|0.999|23.54|23.42|0.995|
|8|31.76|31.76|1.000|25.42|25.45|1.001|
|9|34.12|34.12|1.000|27.01|27.06|1.002|
|10|36.42|36.27|0.996|28.97|28.80|0.994|
|11|38.75|38.69|0.998|30.34|30.23|0.997|
|12|40.90|40.81|0.998|31.99|32.02|1.001|
|13|42.98|42.98|1.000|34.08|34.14|1.002|
|14|45.13|45.10|0.999|35.62|35.57|0.999|
|15|46.94|46.90|0.999|37.15|37.18|1.001|
|16|48.33|48.48|1.003|38.45|38.69|1.006|
|17|48.70|48.53|0.996|38.53|38.48|0.999|
|18|48.64|48.58|0.999|38.50|38.52|1.001|
|19|48.66|48.69|1.000|38.47|38.67|1.005|
|20|48.75|48.61|0.997|38.58|38.52|0.998|
|21|48.65|48.76|1.002|38.58|38.53|0.999|
|22|48.83|48.73|0.998|38.58|38.72|1.004|
|23|48.72|48.78|1.001|38.70|38.71|1.000|
|24|48.69|48.82|1.003|38.61|38.65|1.001|
|25|48.87|48.89|1.000|38.80|38.95|1.004|
|26|48.84|48.70|0.997|38.88|38.66|0.994|
|27|48.78|48.76|1.000|38.62|38.74|1.003|
|28|48.75|48.75|1.000|38.69|38.73|1.001|
|29|48.82|48.86|1.001|38.80|38.98|1.005|
|30|48.71|48.82|1.002|38.83|38.81|0.999|
|31|48.88|48.87|1.000|38.82|38.89|1.002|
|32|48.68|48.91|1.005|38.62|38.82|1.005|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|25.18|25.30|1.005|21.79|21.93|1.006|
|2|37.16|37.06|0.997|29.71|29.74|1.001|
|3|47.86|47.78|0.998|37.81|37.62|0.995|
|4|58.62|58.66|1.001|46.44|46.29|0.997|
|5|68.76|68.50|0.996|55.10|54.99|0.998|
|6|79.34|79.06|0.996|64.07|63.78|0.995|
|7|88.82|88.66|0.998|72.89|73.10|1.003|
|8|97.18|97.12|0.999|81.44|81.42|1.000|
|9|106.14|106.16|1.000|90.04|90.14|1.001|
|10|115.22|115.29|1.001|98.82|98.91|1.001|
|11|124.26|124.30|1.000|107.38|107.38|1.000|
|12|132.99|133.00|1.000|115.78|115.96|1.002|
|13|141.48|141.25|0.998|124.32|124.06|0.998|
|14|149.76|149.94|1.001|132.52|132.70|1.001|
|15|158.14|158.16|1.000|140.98|141.08|1.001|
|16|166.73|166.73|1.000|149.43|149.36|1.000|
|17|175.24|175.38|1.001|157.94|158.03|1.001|
|18|183.55|183.82|1.001|166.30|166.55|1.002|
|19|192.31|192.02|0.999|174.87|174.68|0.999|
|20|200.31|200.63|1.002|182.91|183.18|1.001|
|21|209.01|208.66|0.998|191.60|191.38|0.999|
|22|217.07|217.30|1.001|199.79|200.02|1.001|
|23|225.51|225.25|0.999|208.06|207.90|0.999|
|24|233.82|233.86|1.000|216.52|216.46|1.000|
|25|242.67|242.35|0.999|225.29|225.17|0.999|
|26|250.94|250.98|1.000|233.82|233.77|1.000|
|27|259.37|259.49|1.000|242.05|242.12|1.000|
|28|267.72|267.88|1.001|250.43|250.42|1.000|
|29|275.93|276.30|1.001|258.61|259.05|1.002|
|30|284.22|284.41|1.001|266.94|266.69|0.999|
|31|292.84|292.65|0.999|275.64|275.48|0.999|
|32|300.66|300.85|1.001|283.41|283.47|1.000|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|22.78|22.69|0.996|19.86|19.92|1.003|
|2|33.59|33.25|0.990|26.94|26.71|0.992|
|3|43.30|43.45|1.003|34.11|34.14|1.001|
|4|52.98|52.99|1.000|41.55|41.46|0.998|
|5|62.38|62.42|1.001|48.82|48.96|1.003|
|6|70.70|70.78|1.001|56.70|56.61|0.998|
|7|78.96|78.97|1.000|64.14|64.18|1.000|
|8|87.03|87.17|1.002|71.98|71.90|0.999|
|9|94.92|94.90|1.000|79.58|79.44|0.998|
|10|102.71|102.73|1.000|86.98|87.00|1.000|
|11|110.50|110.42|0.999|94.44|94.36|0.999|
|12|118.23|118.24|1.000|101.96|101.98|1.000|
|13|125.91|125.99|1.001|109.38|109.43|1.001|
|14|133.40|133.45|1.000|116.86|116.80|1.000|
|15|140.93|141.16|1.002|124.31|124.39|1.001|
|16|141.66|141.75|1.001|124.80|125.00|1.002|
|17|142.00|142.10|1.001|125.46|125.38|0.999|
|18|141.99|142.24|1.002|125.50|125.43|0.999|
|19|142.08|142.18|1.001|125.38|125.58|1.002|
|20|142.18|142.18|1.000|125.44|125.46|1.000|
|21|142.26|142.13|0.999|125.46|125.56|1.001|
|22|142.24|142.22|1.000|125.54|125.41|0.999|
|23|142.28|142.31|1.000|125.52|125.61|1.001|
|24|142.34|142.31|1.000|125.54|125.70|1.001|
|25|142.62|142.70|1.001|126.18|126.17|1.000|
|26|142.75|142.80|1.000|126.18|126.31|1.001|
|27|142.53|142.54|1.000|126.10|126.04|1.000|
|28|142.55|142.65|1.001|126.24|126.09|0.999|
|29|142.85|142.89|1.000|126.38|126.48|1.001|
|30|142.63|142.53|0.999|126.11|126.16|1.000|
|31|142.95|142.85|0.999|126.54|126.48|1.000|
|32|142.70|142.81|1.001|126.20|126.37|1.001|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|35.89|36.38|1.014|29.08|28.90|0.994|
|2|52.27|52.24|0.999|39.95|40.03|1.002|
|3|67.59|67.59|1.000|53.76|53.78|1.000|
|4|82.00|82.14|1.002|66.59|66.63|1.001|
|5|95.96|96.21|1.003|78.70|78.75|1.001|
|6|109.30|109.34|1.000|91.74|91.82|1.001|
|7|121.37|121.59|1.002|104.69|104.99|1.003|
|8|134.10|134.11|1.000|117.09|117.17|1.001|
|9|147.48|147.52|1.000|130.30|130.17|0.999|
|10|160.27|160.46|1.001|142.63|142.84|1.001|
|11|172.82|172.90|1.000|155.28|155.39|1.001|
|12|185.55|185.17|0.998|167.86|167.95|1.001|
|13|197.90|198.13|1.001|180.53|180.76|1.001|
|14|210.66|210.28|0.998|193.06|193.16|1.001|
|15|223.01|223.04|1.000|205.63|205.70|1.000|
|16|235.74|235.69|1.000|218.13|218.22|1.000|
|17|249.82|249.98|1.001|232.59|232.64|1.000|
|18|262.38|262.14|0.999|244.97|245.06|1.000|
|19|274.90|274.70|0.999|257.73|257.67|1.000|
|20|282.91|283.13|1.001|265.79|265.77|1.000|
|21|291.26|291.34|1.000|274.20|274.32|1.000|
|22|299.65|299.74|1.000|282.39|282.58|1.001|
|23|308.09|308.18|1.000|290.82|291.00|1.001|
|24|316.61|316.50|1.000|299.37|299.23|1.000|
|25|325.06|325.14|1.000|308.03|308.02|1.000|
|26|333.49|333.40|1.000|316.48|316.30|0.999|
|27|341.81|341.74|1.000|324.54|324.80|1.001|
|28|350.16|350.03|1.000|332.99|332.90|1.000|
|29|358.42|358.41|1.000|341.34|341.39|1.000|
|30|366.73|366.94|1.001|349.71|349.75|1.000|
|31|375.25|375.22|1.000|358.04|358.13|1.000|
|32|383.42|383.38|1.000|366.40|366.36|1.000|

`e256_i2048_k6_clamp10`: hidden 4096, intermediate 2048, 256 experts,
top-6, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.35|24.47|1.005|20.09|19.97|0.994|
|2|37.94|37.98|1.001|29.40|29.34|0.998|
|3|50.38|50.32|0.999|38.58|38.58|1.000|
|4|61.54|61.65|1.002|48.26|48.30|1.001|
|5|72.50|72.50|1.000|58.22|58.26|1.001|
|6|82.70|82.78|1.001|67.46|67.61|1.002|
|7|94.91|94.90|1.000|79.26|79.42|1.002|
|8|104.77|104.94|1.002|89.24|89.18|0.999|
|9|115.93|115.81|0.999|99.93|99.90|1.000|
|10|124.94|124.90|1.000|108.81|108.67|0.999|
|11|133.87|134.09|1.002|117.34|117.65|1.003|
|12|144.17|144.04|0.999|127.27|127.23|1.000|
|13|152.93|152.89|1.000|135.84|135.90|1.000|
|14|163.10|163.16|1.000|145.77|145.74|1.000|
|15|172.74|172.62|0.999|155.25|155.06|0.999|
|16|172.77|172.77|1.000|155.60|155.65|1.000|
|17|173.29|173.30|1.000|156.00|155.85|0.999|
|18|173.41|173.66|1.001|156.23|156.19|1.000|
|19|173.47|173.38|0.999|156.13|156.26|1.001|
|20|173.59|173.64|1.000|156.59|156.62|1.000|
|21|173.75|173.66|0.999|156.52|156.43|0.999|
|22|173.54|173.55|1.000|156.30|156.26|1.000|
|23|172.69|172.86|1.001|155.62|155.77|1.001|
|24|173.72|173.66|1.000|156.40|156.40|1.000|
|25|174.69|174.88|1.001|157.66|157.78|1.001|
|26|174.81|174.78|1.000|157.30|157.26|1.000|
|27|174.82|174.76|1.000|157.12|157.28|1.001|
|28|174.84|174.80|1.000|157.34|157.53|1.001|
|29|175.14|175.12|1.000|158.33|158.20|0.999|
|30|175.30|175.24|1.000|158.83|158.55|0.998|
|31|175.00|175.02|1.000|157.70|157.88|1.001|
|32|173.97|173.94|1.000|157.21|156.88|0.998|

**sm_103a** (NVIDIA GB300, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake version
(FlashInfer main), new = this PR; ratio = new / previous. **Bold**
num_tokens = rows this PR routes to the new program.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.20|14.09|0.992|12.46|12.35|0.991|
|2|18.98|18.94|0.997|16.50|16.30|0.988|
|3|22.73|22.66|0.997|19.06|19.13|1.003|
|4|26.50|26.39|0.996|21.90|21.86|0.998|
|5|30.51|30.50|1.000|25.08|24.95|0.995|
|6|33.90|34.09|1.006|27.15|27.19|1.001|
|7|37.22|37.18|0.999|29.63|29.65|1.001|
|8|36.05|36.07|1.001|31.98|32.00|1.001|
|9|39.74|39.75|1.000|35.11|35.27|1.005|
|10|42.39|42.34|0.999|37.63|37.54|0.998|
|11|45.13|45.22|1.002|40.03|40.06|1.001|
|12|47.75|47.65|0.998|42.32|42.31|1.000|
|13|50.50|50.53|1.001|44.83|44.94|1.002|
|14|53.08|53.12|1.001|47.15|47.25|1.002|
|15|55.73|55.78|1.001|49.82|49.70|0.998|
|16|58.39|58.37|1.000|52.11|52.21|1.002|
|17|60.40|60.38|1.000|54.06|54.10|1.001|
|18|62.27|62.38|1.002|55.73|55.77|1.001|
|19|64.16|64.03|0.998|57.43|57.46|1.000|
|20|65.10|64.98|0.998|57.94|57.89|0.999|
|21|65.20|65.22|1.000|58.19|58.27|1.001|
|22|65.28|65.30|1.000|58.19|58.09|0.998|
|23|65.04|64.93|0.998|57.95|57.79|0.997|
|24|65.02|64.88|0.998|57.82|57.78|0.999|
|25|65.28|65.27|1.000|58.09|58.10|1.000|
|26|65.52|65.55|1.000|58.27|58.35|1.001|
|27|65.56|65.58|1.000|58.47|58.44|0.999|
|28|65.51|65.56|1.001|58.30|58.32|1.000|
|29|65.77|65.56|0.997|58.35|58.42|1.001|
|30|65.54|65.59|1.001|58.38|58.31|0.999|
|31|65.70|65.47|0.997|58.50|58.35|0.998|
|32|65.66|65.62|0.999|58.43|58.38|0.999|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.83|16.57|0.984|15.54|15.19|0.977|
|2|22.66|22.85|1.008|20.85|20.73|0.994|
|3|26.85|26.82|0.999|24.58|24.43|0.994|
|4|32.96|33.11|1.005|29.76|30.00|1.008|
|5|37.17|37.12|0.999|33.94|33.78|0.995|
|6|42.10|42.10|1.000|38.48|38.50|1.000|
|7|46.98|47.10|1.002|43.05|43.06|1.000|
|8|51.50|51.33|0.997|47.46|47.31|0.997|
|9|56.84|56.82|1.000|52.38|52.24|0.997|
|10|61.30|61.47|1.003|56.61|56.62|1.000|
|11|66.59|66.53|0.999|61.42|61.48|1.001|
|**12**|71.24|70.90|0.995|66.10|65.45|0.990|
|**13**|76.12|75.66|0.994|70.42|69.66|0.989|
|**14**|80.92|80.35|0.993|74.93|73.98|0.987|
|**15**|85.68|85.14|0.994|79.66|78.46|0.985|
|**16**|90.55|89.82|0.992|84.22|82.73|0.982|
|**17**|95.35|94.70|0.993|88.64|87.53|0.987|
|**18**|99.99|99.19|0.992|92.90|91.68|0.987|
|**19**|104.67|104.00|0.994|97.44|96.17|0.987|
|**20**|109.13|108.43|0.994|101.85|100.60|0.988|
|**21**|113.75|112.89|0.992|106.12|104.62|0.986|
|**22**|118.50|117.84|0.994|110.60|109.32|0.988|
|**23**|123.11|122.43|0.994|114.91|113.31|0.986|
|**24**|127.75|126.65|0.991|119.66|117.73|0.984|
|**25**|132.90|131.67|0.991|124.35|122.38|0.984|
|**26**|137.38|136.22|0.992|128.68|126.74|0.985|
|**27**|141.94|140.81|0.992|132.99|131.10|0.986|
|**28**|146.65|145.45|0.992|137.56|135.36|0.984|
|**29**|151.35|150.08|0.992|142.26|139.82|0.983|
|**30**|156.06|154.65|0.991|146.66|144.40|0.985|
|**31**|160.71|159.14|0.990|151.16|148.82|0.984|
|**32**|165.24|163.61|0.990|155.45|152.69|0.982|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.20|14.45|1.017|13.62|13.90|1.021|
|2|17.30|17.14|0.991|16.03|15.89|0.991|
|3|20.47|20.42|0.997|18.90|18.82|0.996|
|4|24.32|24.37|1.002|22.97|22.69|0.988|
|5|26.62|26.63|1.001|24.84|24.93|1.004|
|6|29.02|29.08|1.002|27.11|27.22|1.004|
|**7**|32.30|32.17|0.996|30.15|29.74|0.986|
|**8**|36.32|36.00|0.991|33.49|33.06|0.987|
|**9**|38.87|38.42|0.988|36.14|35.62|0.985|
|**10**|41.58|40.74|0.980|38.76|37.92|0.978|
|**11**|44.39|43.23|0.974|41.39|40.26|0.973|
|**12**|47.60|46.17|0.970|44.83|43.29|0.966|
|**13**|50.34|48.70|0.968|47.32|45.77|0.967|
|**14**|53.11|51.39|0.968|49.66|47.94|0.966|
|**15**|56.14|54.24|0.966|52.50|50.49|0.962|
|**16**|58.62|56.77|0.968|55.14|53.26|0.966|
|**17**|61.46|59.55|0.969|57.81|55.86|0.966|
|**18**|64.55|62.22|0.964|60.59|58.31|0.962|
|**19**|67.44|65.16|0.966|63.22|60.76|0.961|
|**20**|70.14|67.50|0.962|65.78|63.16|0.960|
|**21**|72.74|69.98|0.962|68.45|65.49|0.957|
|**22**|75.76|73.00|0.964|71.06|68.37|0.962|
|**23**|78.59|75.99|0.967|73.82|71.06|0.963|
|**24**|81.44|78.38|0.962|76.56|73.42|0.959|
|**25**|84.27|80.87|0.960|79.23|75.75|0.956|
|**26**|87.00|83.82|0.963|81.99|78.88|0.962|
|**27**|90.03|86.32|0.959|85.00|81.26|0.956|
|**28**|92.46|88.96|0.962|87.17|83.47|0.958|
|**29**|95.30|91.90|0.964|89.93|86.34|0.960|
|**30**|97.97|94.02|0.960|92.77|88.86|0.958|
|**31**|100.93|96.83|0.959|95.57|91.24|0.955|
|**32**|103.84|99.61|0.959|98.34|94.00|0.956|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.10|16.10|1.000|14.69|14.66|0.998|
|2|21.82|21.91|1.004|19.60|19.64|1.002|
|3|25.42|25.53|1.004|23.10|22.90|0.991|
|4|29.54|29.57|1.001|26.88|26.93|1.002|
|5|34.47|34.46|1.000|31.19|31.22|1.001|
|6|38.46|38.45|1.000|34.86|34.84|1.000|
|7|42.98|42.99|1.000|38.82|38.78|0.999|
|8|47.25|47.19|0.999|42.50|42.57|1.002|
|9|51.46|51.62|1.003|46.54|46.58|1.001|
|10|55.70|55.74|1.001|50.09|50.15|1.001|
|11|59.85|59.94|1.002|54.32|54.29|0.999|
|12|63.98|63.99|1.000|57.84|57.61|0.996|
|13|68.20|68.20|1.000|61.95|61.88|0.999|
|14|72.31|72.31|1.000|65.38|65.18|0.997|
|15|76.38|76.41|1.000|69.27|69.27|1.000|
|16|76.47|76.44|1.000|69.19|69.26|1.001|
|17|76.47|76.46|1.000|69.26|69.33|1.001|
|18|76.45|76.48|1.000|69.10|69.47|1.005|
|19|76.50|76.53|1.000|69.22|69.24|1.000|
|20|76.51|76.54|1.000|69.33|69.27|0.999|
|21|76.50|76.47|1.000|69.44|69.32|0.998|
|22|76.58|76.48|0.999|69.39|69.35|0.999|
|23|76.46|76.61|1.002|69.23|69.30|1.001|
|24|76.60|76.48|0.998|69.26|69.26|1.000|
|25|76.59|76.68|1.001|69.33|69.53|1.003|
|26|76.66|76.68|1.000|69.38|69.48|1.002|
|27|76.75|76.67|0.999|69.58|69.38|0.997|
|28|76.67|76.60|0.999|69.46|69.39|0.999|
|29|76.69|76.65|0.999|69.48|69.48|1.000|
|30|76.65|76.70|1.001|69.56|69.36|0.997|
|31|76.66|76.74|1.001|69.42|69.37|0.999|
|32|76.65|76.75|1.001|69.48|69.46|1.000|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.86|13.71|0.990|12.92|12.96|1.003|
|2|16.46|16.58|1.007|15.06|15.13|1.004|
|3|19.14|19.03|0.994|17.38|17.54|1.009|
|4|21.66|21.70|1.002|19.82|19.80|0.999|
|5|23.91|24.05|1.006|21.94|21.84|0.995|
|6|26.38|26.49|1.004|23.98|23.78|0.992|
|7|29.16|29.18|1.001|26.42|26.41|0.999|
|8|30.98|31.13|1.005|28.17|28.26|1.003|
|9|33.43|33.60|1.005|30.34|30.29|0.998|
|10|35.66|35.71|1.002|32.38|32.37|1.000|
|11|38.36|38.23|0.997|34.58|34.74|1.005|
|12|40.17|40.30|1.003|36.48|36.54|1.002|
|13|42.39|42.22|0.996|38.49|38.58|1.002|
|14|44.33|44.27|0.999|40.52|40.54|1.001|
|15|46.49|46.56|1.002|42.58|42.55|0.999|
|16|46.66|46.75|1.002|42.55|42.55|1.000|
|17|46.74|46.69|0.999|42.50|42.59|1.002|
|18|46.60|46.89|1.006|42.51|42.74|1.005|
|19|46.84|46.69|0.997|42.58|42.62|1.001|
|20|46.95|46.73|0.995|42.74|42.53|0.995|
|21|46.82|46.86|1.001|42.70|42.74|1.001|
|22|46.82|46.83|1.000|42.47|42.49|1.000|
|23|46.83|46.73|0.998|42.57|42.67|1.002|
|24|46.93|46.85|0.998|42.76|42.55|0.995|
|25|47.06|46.95|0.998|42.86|42.78|0.998|
|26|47.23|47.00|0.995|43.01|42.74|0.994|
|27|47.19|47.05|0.997|42.93|42.79|0.997|
|28|46.96|46.98|1.000|42.65|42.78|1.003|
|29|47.22|47.06|0.997|42.93|42.86|0.998|
|30|47.21|47.06|0.997|42.88|42.77|0.997|
|31|46.99|47.06|1.002|42.72|42.93|1.005|
|32|47.18|47.13|0.999|42.89|42.70|0.996|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.17|14.15|0.999|12.70|12.67|0.997|
|2|18.83|18.74|0.995|16.46|16.37|0.994|
|3|21.66|21.82|1.007|18.42|18.42|1.000|
|4|25.54|25.38|0.994|21.30|21.12|0.992|
|5|28.11|28.14|1.001|22.86|22.90|1.001|
|6|31.48|31.60|1.004|25.74|25.92|1.007|
|7|34.34|34.23|0.997|27.55|27.45|0.996|
|8|37.26|37.04|0.994|29.67|29.66|0.999|
|9|39.97|39.96|1.000|31.77|31.82|1.002|
|10|42.82|42.87|1.001|34.25|34.36|1.003|
|11|45.54|45.62|1.002|36.33|36.27|0.998|
|12|48.20|48.41|1.004|38.78|38.70|0.998|
|13|50.94|51.15|1.004|40.82|40.74|0.998|
|14|53.75|53.83|1.001|43.02|43.31|1.007|
|15|56.69|56.71|1.000|45.62|45.46|0.997|
|16|59.34|59.38|1.001|48.00|47.93|0.999|
|17|61.66|61.70|1.001|49.99|50.24|1.005|
|18|64.42|64.46|1.001|52.29|52.30|1.000|
|19|67.10|67.29|1.003|54.66|54.59|0.999|
|20|69.79|69.93|1.002|57.15|57.22|1.001|
|21|72.23|72.28|1.001|59.28|59.38|1.002|
|22|74.55|74.72|1.002|61.56|61.73|1.003|
|23|77.16|76.98|0.998|63.85|63.80|0.999|
|24|79.71|79.79|1.001|66.28|66.29|1.000|
|25|82.06|82.08|1.000|68.56|68.50|0.999|
|26|84.30|84.29|1.000|70.82|71.02|1.003|
|27|86.80|86.83|1.000|73.16|73.10|0.999|
|28|89.38|89.16|0.997|75.47|75.41|0.999|
|29|91.78|91.97|1.002|77.68|77.66|1.000|
|30|94.54|94.57|1.000|80.19|80.17|1.000|
|31|97.13|96.98|0.998|82.65|82.38|0.997|
|32|99.33|99.47|1.001|84.54|84.59|1.001|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.23|13.35|1.009|11.98|12.06|1.006|
|2|16.61|16.66|1.003|14.59|14.47|0.992|
|3|20.81|20.92|1.005|17.82|17.77|0.997|
|4|23.31|23.28|0.999|19.51|19.62|1.006|
|5|26.91|26.91|1.000|21.74|21.84|1.004|
|6|29.74|29.70|0.999|23.54|23.57|1.001|
|7|32.46|32.38|0.998|25.44|25.56|1.005|
|8|35.02|35.14|1.003|27.43|27.65|1.008|
|9|37.37|37.54|1.005|28.91|29.04|1.004|
|10|40.06|40.20|1.003|31.02|31.02|1.000|
|11|41.45|41.20|0.994|33.26|33.18|0.997|
|12|43.29|43.37|1.002|34.87|35.06|1.006|
|13|45.23|45.20|0.999|36.77|36.52|0.993|
|14|47.27|47.10|0.996|38.20|38.51|1.008|
|15|49.52|49.42|0.998|40.60|40.43|0.996|
|16|50.91|50.88|0.999|41.47|41.42|0.999|
|17|52.96|53.04|1.002|42.86|42.80|0.999|
|18|54.75|54.67|0.999|44.13|44.11|1.000|
|19|56.34|56.48|1.002|45.09|45.26|1.004|
|20|58.20|58.06|0.998|46.46|46.31|0.997|
|21|59.96|59.86|0.998|47.82|47.94|1.003|
|22|61.82|61.74|0.999|49.45|49.37|0.998|
|23|63.44|63.41|0.999|50.75|50.91|1.003|
|24|65.26|65.22|1.000|52.38|52.31|0.999|
|25|67.26|67.07|0.997|54.10|53.98|0.998|
|26|68.86|68.76|0.998|55.37|55.34|1.000|
|27|68.82|68.78|0.999|55.42|55.41|1.000|
|28|68.88|68.91|1.000|55.46|55.54|1.001|
|29|68.71|68.82|1.002|55.37|55.54|1.003|
|30|68.84|68.78|0.999|55.48|55.42|0.999|
|31|68.91|68.77|0.998|55.53|55.38|0.997|
|32|68.87|68.74|0.998|55.42|55.40|1.000|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|19.88|19.97|1.004|17.57|17.75|1.010|
|2|25.94|26.13|1.007|21.20|21.28|1.004|
|3|31.29|31.30|1.000|25.13|25.14|1.001|
|4|39.09|39.03|0.999|31.16|31.30|1.004|
|5|43.44|43.58|1.003|34.39|34.39|1.000|
|6|48.62|48.24|0.992|38.42|38.08|0.991|
|7|55.36|55.34|1.000|43.60|43.47|0.997|
|8|59.65|59.90|1.004|47.13|47.18|1.001|
|9|64.50|64.50|1.000|51.08|51.21|1.003|
|10|69.95|69.92|1.000|56.45|56.51|1.001|
|11|74.18|74.26|1.001|60.29|60.54|1.004|
|12|78.53|78.53|1.000|64.36|64.47|1.002|
|13|83.52|83.46|0.999|69.63|69.38|0.996|
|14|88.02|88.07|1.001|73.88|73.91|1.000|
|15|92.58|92.46|0.999|77.95|77.78|0.998|
|16|96.75|96.80|1.000|82.72|82.70|1.000|
|17|101.40|101.23|0.998|87.30|87.26|1.000|
|18|106.09|105.84|0.998|91.50|91.56|1.001|
|19|110.69|110.35|0.997|96.05|95.77|0.997|
|20|114.86|115.32|1.004|100.18|100.45|1.003|
|21|120.03|119.55|0.996|104.86|104.64|0.998|
|22|124.21|124.30|1.001|108.98|109.07|1.001|
|23|128.59|128.89|1.002|113.18|113.62|1.004|
|24|133.28|132.95|0.998|117.75|117.75|1.000|
|25|137.86|137.89|1.000|122.27|122.39|1.001|
|26|142.81|142.30|0.996|127.00|126.68|0.997|
|27|146.96|146.75|0.999|131.30|131.10|0.998|
|28|151.45|151.31|0.999|135.58|135.44|0.999|
|29|155.66|155.57|0.999|139.89|139.82|0.999|
|30|160.16|159.79|0.998|144.35|143.78|0.996|
|31|164.53|164.70|1.001|148.83|148.98|1.001|
|32|168.90|168.71|0.999|153.06|153.00|1.000|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.10|12.16|1.005|10.94|10.90|0.996|
|2|14.52|14.39|0.991|13.05|12.94|0.991|
|3|16.90|16.78|0.993|15.03|14.91|0.992|
|4|19.35|19.38|1.002|16.99|17.27|1.016|
|5|21.10|21.12|1.001|18.06|18.21|1.008|
|6|23.06|23.03|0.999|19.56|19.54|0.999|
|7|25.54|25.52|0.999|21.78|21.77|0.999|
|8|27.41|27.48|1.003|22.84|22.77|0.997|
|9|29.11|29.02|0.997|23.72|23.78|1.003|
|10|31.47|31.40|0.998|26.08|26.10|1.001|
|11|32.92|32.98|1.002|27.06|26.99|0.997|
|12|34.78|34.65|0.996|28.01|28.00|1.000|
|13|36.62|36.78|1.004|29.70|29.49|0.993|
|14|38.45|38.42|0.999|30.84|30.97|1.004|
|15|39.95|40.16|1.005|32.05|32.09|1.001|
|16|41.58|41.75|1.004|33.40|33.38|1.000|
|17|43.24|43.21|0.999|34.79|34.78|1.000|
|18|44.86|44.94|1.002|36.02|35.78|0.993|
|19|46.63|46.73|1.002|37.26|37.16|0.997|
|20|48.33|48.38|1.001|38.56|38.44|0.997|
|21|50.23|50.10|0.997|39.92|39.95|1.001|
|22|52.04|52.05|1.000|41.09|41.18|1.002|
|23|53.57|53.78|1.004|42.82|42.80|1.000|
|24|55.45|55.37|0.999|44.17|44.13|0.999|
|25|56.99|57.16|1.003|45.50|45.55|1.001|
|26|58.65|58.84|1.003|46.90|46.98|1.002|
|27|60.15|60.32|1.003|48.36|48.31|0.999|
|28|61.96|62.00|1.001|49.76|49.50|0.995|
|29|63.66|63.65|1.000|51.15|51.26|1.002|
|30|65.17|65.30|1.002|52.30|52.30|1.000|
|31|66.98|66.83|0.998|53.87|53.95|1.001|
|32|68.67|68.66|1.000|55.15|55.29|1.002|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|26.78|26.94|1.006|22.70|22.65|0.998|
|2|40.59|40.74|1.004|32.66|32.69|1.001|
|3|53.75|53.92|1.003|42.72|42.64|0.998|
|4|65.87|65.85|1.000|52.82|53.00|1.003|
|5|77.78|77.66|0.998|63.47|63.61|1.002|
|6|88.66|88.90|1.003|74.09|74.06|1.000|
|7|99.45|99.50|1.000|84.95|84.65|0.996|
|8|110.22|110.24|1.000|95.15|95.10|0.999|
|9|120.67|120.64|1.000|105.15|105.18|1.000|
|10|131.24|131.05|0.999|115.54|115.52|1.000|
|11|141.38|141.43|1.000|125.27|125.22|1.000|
|12|151.27|151.46|1.001|135.42|135.34|0.999|
|13|161.52|161.54|1.000|145.56|145.51|1.000|
|14|171.42|171.62|1.001|155.54|155.46|0.999|
|15|181.46|181.63|1.001|165.60|165.69|1.001|
|16|191.60|191.38|0.999|175.51|175.74|1.001|
|17|199.16|199.36|1.001|183.28|183.19|1.000|
|18|206.35|206.24|0.999|190.44|190.50|1.000|
|19|213.46|213.58|1.001|197.53|197.58|1.000|
|20|213.51|213.57|1.000|197.66|197.58|1.000|
|21|213.55|213.66|1.000|197.86|197.59|0.999|
|22|213.64|213.67|1.000|197.94|197.74|0.999|
|23|213.59|213.86|1.001|197.88|197.85|1.000|
|24|213.81|213.82|1.000|197.85|197.66|0.999|
|25|214.50|214.41|1.000|198.66|198.57|1.000|
|26|214.57|214.49|1.000|198.58|198.69|1.001|
|27|214.54|214.53|1.000|198.67|198.93|1.001|
|28|214.62|214.48|0.999|198.53|198.87|1.002|
|29|214.53|214.57|1.000|198.82|198.81|1.000|
|30|214.79|214.50|0.999|198.94|199.00|1.000|
|31|214.89|214.72|0.999|198.94|198.75|0.999|
|32|214.65|214.66|1.000|199.04|198.88|0.999|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.42|12.50|1.006|11.62|11.58|0.997|
|2|16.10|16.12|1.001|14.28|14.15|0.991|
|3|19.62|19.65|1.001|17.30|17.22|0.996|
|4|21.70|21.64|0.997|18.54|18.61|1.004|
|5|25.23|25.02|0.991|20.86|20.98|1.006|
|6|27.02|27.10|1.003|22.31|22.22|0.996|
|7|29.34|29.44|1.004|23.79|23.66|0.994|
|8|32.06|32.06|1.000|25.74|25.70|0.999|
|9|34.15|34.29|1.004|27.18|27.32|1.005|
|10|36.70|36.55|0.996|29.26|29.13|0.996|
|11|38.82|38.73|0.998|30.75|30.81|1.002|
|12|40.94|40.98|1.001|32.47|32.70|1.007|
|13|43.24|43.22|1.000|34.38|34.49|1.003|
|14|45.47|45.29|0.996|36.01|35.98|0.999|
|15|47.62|47.40|0.995|37.93|37.98|1.001|
|16|48.58|48.63|1.001|38.68|38.78|1.002|
|17|48.74|48.69|0.999|38.86|38.83|0.999|
|18|48.67|48.78|1.002|38.92|38.96|1.001|
|19|48.74|48.82|1.002|38.79|38.88|1.002|
|20|48.82|48.82|1.000|38.81|38.72|0.998|
|21|48.70|48.74|1.001|38.95|38.80|0.996|
|22|48.83|48.82|1.000|39.06|38.84|0.994|
|23|48.85|48.87|1.000|38.99|38.89|0.997|
|24|48.86|48.82|0.999|38.94|38.98|1.001|
|25|48.94|48.80|0.997|38.96|39.07|1.003|
|26|49.06|48.88|0.996|39.04|38.93|0.997|
|27|48.94|48.98|1.001|39.10|38.95|0.996|
|28|48.90|48.97|1.001|38.93|38.94|1.000|
|29|49.01|49.00|1.000|39.07|39.04|0.999|
|30|49.01|49.02|1.000|39.11|39.03|0.998|
|31|48.94|49.01|1.001|39.03|39.00|0.999|
|32|49.12|49.02|0.998|38.91|39.11|1.005|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|25.19|25.45|1.010|21.69|21.76|1.003|
|2|38.06|37.70|0.991|30.59|30.62|1.001|
|3|48.20|48.29|1.002|38.91|38.79|0.997|
|4|59.52|59.45|0.999|47.54|47.37|0.996|
|5|69.42|69.46|1.001|56.45|56.42|0.999|
|6|79.65|79.66|1.000|65.63|65.64|1.000|
|7|88.81|88.74|0.999|74.77|74.70|0.999|
|8|98.86|98.84|1.000|83.68|83.64|1.000|
|9|107.55|107.52|1.000|92.16|92.24|1.001|
|10|116.68|116.67|1.000|101.18|101.13|0.999|
|11|125.61|125.71|1.001|109.77|109.86|1.001|
|12|134.59|134.45|0.999|118.51|118.47|1.000|
|13|143.38|143.42|1.000|127.30|127.20|0.999|
|14|151.77|151.78|1.000|136.02|136.03|1.000|
|15|160.79|160.50|0.998|144.24|144.65|1.003|
|16|169.22|169.21|1.000|153.03|153.10|1.000|
|17|178.18|178.12|1.000|162.12|162.16|1.000|
|18|186.42|186.61|1.001|170.68|170.64|1.000|
|19|195.41|195.42|1.000|179.36|179.28|1.000|
|20|204.06|204.28|1.001|187.78|187.74|1.000|
|21|212.89|212.66|0.999|196.40|196.37|1.000|
|22|221.34|221.42|1.000|205.00|204.95|1.000|
|23|230.03|230.02|1.000|213.88|213.54|0.998|
|24|238.67|238.34|0.999|222.43|222.52|1.000|
|25|247.38|247.35|1.000|231.26|231.15|1.000|
|26|256.34|256.38|1.000|239.95|239.92|1.000|
|27|265.00|264.83|0.999|248.53|248.72|1.001|
|28|273.82|273.75|1.000|257.26|257.26|1.000|
|29|281.81|282.06|1.001|266.12|265.77|0.999|
|30|290.81|290.78|1.000|274.34|274.64|1.001|
|31|299.19|299.34|1.001|282.98|283.08|1.000|
|32|307.44|307.70|1.001|291.36|291.14|0.999|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|22.66|22.65|1.000|19.37|19.32|0.998|
|2|33.36|33.35|1.000|26.91|26.98|1.002|
|3|43.33|43.29|0.999|34.59|34.62|1.001|
|4|53.45|53.48|1.001|42.26|42.26|1.000|
|5|62.69|62.67|1.000|49.90|49.95|1.001|
|6|71.46|71.54|1.001|57.78|57.90|1.002|
|7|80.03|80.03|1.000|65.70|65.59|0.998|
|8|88.29|88.21|0.999|73.48|73.57|1.001|
|9|96.22|96.25|1.000|81.54|81.41|0.998|
|10|104.30|104.22|0.999|89.06|89.16|1.001|
|11|112.32|112.27|1.000|96.76|96.87|1.001|
|12|120.39|120.26|0.999|104.58|104.85|1.003|
|13|127.97|128.06|1.001|112.19|112.22|1.000|
|14|135.80|135.82|1.000|119.89|120.00|1.001|
|15|143.53|143.66|1.001|127.67|127.82|1.001|
|16|144.23|144.14|0.999|128.18|128.14|1.000|
|17|144.61|144.62|1.000|128.47|128.58|1.001|
|18|144.52|144.54|1.000|128.61|128.58|1.000|
|19|144.59|144.55|1.000|128.80|128.70|0.999|
|20|144.50|144.66|1.001|128.65|128.60|1.000|
|21|144.63|144.74|1.001|128.62|128.66|1.000|
|22|144.78|144.62|0.999|128.84|128.83|1.000|
|23|144.74|144.86|1.001|128.81|128.82|1.000|
|24|144.67|144.72|1.000|128.78|128.90|1.001|
|25|145.37|145.18|0.999|129.35|129.30|1.000|
|26|145.33|145.29|1.000|129.31|129.30|1.000|
|27|145.35|145.43|1.001|129.41|129.38|1.000|
|28|145.30|145.30|1.000|129.44|129.62|1.001|
|29|145.38|145.39|1.000|129.50|129.56|1.000|
|30|145.43|145.38|1.000|129.50|129.63|1.001|
|31|145.29|145.43|1.001|129.70|129.55|0.999|
|32|145.41|145.37|1.000|129.58|129.59|1.000|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|37.01|37.10|1.003|29.50|29.46|0.999|
|2|52.89|52.90|1.000|41.07|41.05|0.999|
|3|68.38|68.44|1.001|54.26|54.58|1.006|
|4|82.86|82.85|1.000|67.91|67.89|1.000|
|5|96.18|96.28|1.001|80.43|80.44|1.000|
|6|110.18|110.00|0.998|93.78|93.78|1.000|
|7|123.16|123.27|1.001|106.94|106.98|1.000|
|8|136.56|136.42|0.999|120.34|120.03|0.997|
|9|150.55|150.58|1.000|134.14|134.10|1.000|
|10|163.83|163.71|0.999|147.04|146.86|0.999|
|11|176.84|176.99|1.001|159.72|159.84|1.001|
|12|189.83|189.98|1.001|172.80|172.85|1.000|
|13|202.62|202.69|1.000|185.77|185.66|0.999|
|14|215.58|215.59|1.000|198.64|198.70|1.000|
|15|228.31|228.37|1.000|211.70|211.64|1.000|
|16|241.28|241.22|1.000|224.53|224.54|1.000|
|17|255.68|255.62|1.000|239.29|239.50|1.001|
|18|268.40|268.48|1.000|252.16|252.03|0.999|
|19|281.23|281.34|1.000|265.06|265.20|1.001|
|20|290.18|290.07|1.000|273.74|273.62|1.000|
|21|298.81|298.78|1.000|282.49|282.61|1.000|
|22|307.36|307.40|1.000|291.06|291.17|1.000|
|23|315.88|316.06|1.001|299.81|299.71|1.000|
|24|324.61|324.55|1.000|308.42|308.46|1.000|
|25|333.62|333.50|1.000|317.33|317.19|1.000|
|26|342.38|342.47|1.000|325.76|325.98|1.001|
|27|350.81|351.10|1.001|334.35|334.53|1.001|
|28|359.87|359.65|0.999|342.97|343.10|1.000|
|29|368.16|367.99|1.000|351.66|351.68|1.000|
|30|377.06|376.83|0.999|360.34|360.16|0.999|
|31|385.62|385.58|1.000|368.89|368.89|1.000|
|32|394.29|393.99|0.999|377.59|377.55|1.000|

The kernel's Cake variants are SwiGLU, GPT-OSS-style SwiGLU
(alpha/beta/limit), SiLU and SiTU on sm_100a and sm_103a, plus clamped
SwiGLU (limit 10) on sm_100a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added warp-decode support for select configurations with 4096 hidden
units and 512 experts on SM100a and SM103a GPUs. These configurations
can use the supported K256 FC2 execution schedule on both GPU targets.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [01b18dc](https://github.com/flashinfer-ai/flashinfer/commit/01b18dc98dc1574ec4f3b9402e451cf097474ea1)

- **作者**: eigen
- **时间**: 2026-10-25T18:58:24Z
- **提交信息**: deslop(cake_hopper_msa): one binding per role, fold 38 clone kernels, add a device header, drop dead code (#7332)

## 📌 Description

### Summary

This PR is a deslop of the Cake-exported `cake_hopper_msa` package. The
package holds the SM90 programs behind the four MSA operations of
`flashinfer.msa_ops`: `msa_sparse_decode_attention`,
`msa_sparse_attention`, `msa_proxy_score` and `msa_topk_select`. It
targets H100 (SM90) only. It is JIT-only, and each program builds lazily
for sm_90a.

At the base, the package has these parts:
- 89 kernel and 89 binding translation units under
`csrc/cake_hopper_msa/`, named `cake_hopper_msa_<20-hex>_kernel.cu` and
`cake_hopper_msa_<20-hex>_binding.cu`, plus `cake_ffi_checks.h`;
- `flashinfer/jit/cake_hopper_msa.py`, the registry: 89 `MODULES`
records, 89 `ROUTES`, the content digest and the loader;
- `flashinfer/msa_ops/cake_hopper_sm90.py`, the host module: the
planners, the scratch buffers and the launchers.

The programs per family are decode_v5 22, topk_select 32, proxy_decode
24, proxy_prefill 5, prefill_v1 3 and prefill_v2 3.
`flashinfer/msa_ops/_sm90_dispatch.py` sends each operation to these
programs when a route exists. For top-k, proxy scores and prefill it
otherwise sends the call to the CuTe DSL kernels; sparse decode has no
fallback. This PR does not edit it.

Four test files cover the package:
- `tests/msa_ops/test_cake_hopper_msa_programs.py`, the CPU structure
test;
- `tests/msa_ops/test_msa_sm90.py`;
- `tests/msa_ops/test_msa_topk_per_token.py`;
- `tests/msa_ops/test_sparse_prefill.py`.

Together they collect 453 ids at the base and 372 at the head. Every id
change is in the structure test: 89 ids leave and 8 arrive.

The four commits are mechanical:
- commit 1 replaces the 89 bindings with one shared binding per role, 15
in all, selected by `-D` flags;
- commit 2 folds the 38 constant-clone kernels into 20 shared sources
with integer `-D` knobs;
- commit 3 moves the device preamble and helpers into one shared header;
- commit 4 drops dead host code, compacts the registry and trims the
structure test.

Each commit has an identity proof. For the translation units, the proof
compares preprocessed text, SASS, symbol tables and host exports per
program. For the Python files, it uses AST checks, reference searches
and the test id sets. Each commit section lists its declared deviation
or behaviour notes, and Reviewer Notes repeats them.

Commits 1, 2 and 3 fold exporter-written translation units by hand.
Commits 1, 2 and 4 edit the exporter-written registry by hand. These
folds and edits are pending exporter regeneration.

Totals versus `main` `e3b5b1e34`: 182 files changed, +2,313 / −79,655.
`csrc/cake_hopper_msa/` goes from 179 files to 68: 51 kernel units, 15
bindings, `cake_ffi_checks.h` and the new device header. All 89 programs
stay registered. The registry keeps 89 `MODULES` records and 89
`ROUTES`.

### Changes

Base: `main` `e3b5b1e34`. Head:
`2097953f5085930f4e8a99d60bca6bce6ab3dce9` (4 commits). Reviewer Notes
give the `main` sha at publish time.

Files per commit:
- commit 1: the 74 deleted bindings, the 15 kept bindings, the registry
and the structure test;
- commit 2: the 38 deleted kernels, the 20 shared kernel sources, the
registry and the structure test;
- commit 3: the new device header and the 51 remaining kernel units;
- commit 4: the host module, the registry and the structure test.

Several commits edit the same files:
- `flashinfer/jit/cake_hopper_msa.py` (commits 1, 2 and 4);
- `tests/msa_ops/test_cake_hopper_msa_programs.py` (commits 1, 2 and 4);
- the 20 shared kernel sources (commits 2 and 3).

So the per-commit counts do not sum to the branch totals.

### Commit 1 (1559d6c76) - share one tvm-ffi binding per role, selected
by -D flags (91 files, +630 / −15,035)

- **The copies.** Once the program hash, the shared-memory value at its
two sites and the `blockDim` literal are masked, the 89 binding texts
reduce to 15. That is one text per role:
  - decode_v5 3, prefill_v1 3, prefill_v2 1;
  - proxy_decode 4, proxy_prefill 3, topk_select 1.

In 89 of 89 programs, the shared-memory literal equals the kernel's
`SMEM_TOTAL` and the block size equals its `THREADS`. Only the loader
and the structure test name a binding path.
- **Change.**
- The other 74 `*_binding.cu` files are deleted. The 15 kept bindings
keep their hash names.
- Three macros carry the per-program values. `CAKE_PROGRAM_KERNEL` names
the kernel symbol, `CAKE_BIND_SMEM` gives the dynamic shared memory and
`CAKE_BIND_THREADS` gives the block size. Each macro has an `#ifndef` /
`#error` guard, so a missing flag is a compile error.
- `KERNEL_NAME` is the stringized `CAKE_PROGRAM_KERNEL`, and the
namespace `CAKE_PROGRAM_SHIM` is pasted from it. So each program keeps
its own namespace and `Run`.
- Each registry record gains `kernel` and `binding` fields and the three
flags. `_content_digest` and `gen_hopper_msa_module` read the two
fields. They no longer build paths from the program name.
- The structure test's three binding and digest tests read the record
fields. The test accepts `kernel_<name>` or `CAKE_PROGRAM_KERNEL` as the
kernel symbol.
- The new `test_shared_bindings_serve_one_route_family_each` checks that
programs sharing a binding are one family and one plan, with
pairwise-distinct flag sets. The structure test goes from 364 to 365
ids.
  - No kernel unit is edited.
- **Proof.**
- The base literals carry no suffix, as in `87808;` and `dim3(128, 1,
1)`. So the flags reproduce them token for token.
- `TVM_FFI_DLL_EXPORT_TYPED_FUNC` pastes only its first parameter. So
the exported C symbols stay `__tvm_ffi_run` and
`__tvm_ffi_build_cuda_version`.
- Each program's binding preprocesses to its own base binding in the
device and host passes. This holds after the backtrace mask described in
Validation. Its host object exports the same set.
- The 89 kernel units are compiled on both trees. Their preprocessed
text, SASS and symbol tables must be identical, which shows that no
kernel unit references the new flag names.
- Every content digest changes. The uri prefix `<program>_sm90a_` stays.
- No file outside the package, its loader and its structure test names a
binding path.
- **Declared deviation.** Every `TVM_FFI_CHECK` / `TVM_FFI_THROW` site
of the 89 binding translation units, 1,639 sites in all, reports the
shared binding's file name and a line number 16 higher in a failure
backtrace; message texts are unchanged and no test reads a backtrace.
- **Declared.** These are hand folds of exporter-written files.

### Commit 2 (d475fc8b6) - fold the 38 constant-clone kernels into 20
shared sources (60 files, +1,595 / −60,718)

- **The clones.** 38 of the 89 kernels differ from a sibling only in
constants. They form five fold sets:
- **decode_v5, 9 pairs.** At the TMA load sites, the `:evict_first:`
twin issues an inline `cp.async.bulk.tensor.3d` with an L2 cache hint.
The `:none:` twin calls the `tma_3d_gmem2smem` helper instead. Knob:
`CAKE_L2_EVICT_FIRST`.
- **topk_select, 5 kernels.** Each one differs from its sibling in four
literals that depend on the index bits l: `l`, `(1<<l)-1`, `~((1<<l)-1)`
and `0x7F7FFFFF & ~((1<<l)-1)`. Knobs: `CAKE_INDEX_BITS`,
`CAKE_INDEX_LOW_MASK`, `CAKE_INDEX_HIGH_MASK` and
`CAKE_INDEX_SCORE_MASK`.
- **proxy_decode, 20 kernels.** They fold onto 4 bodies. They differ in
the index arithmetic for the query heads HQ and the query length SQ.
Knobs: `CAKE_HQ`, `CAKE_SQ` and `CAKE_HQ_SQ`.
- **prefill, 3 kernels.** They fold onto 2 bodies. They differ in
per-group values: mask widths, shifts, the `cnt_b` divisor and
shared-memory offsets. Knob: `CAKE_GROUP`.
- **proxy_prefill, 1 kernel.** f16t4 (`38ae2d`) is f16t4F (`aa3467`)
without two 16-line fold-remap blocks. f16t4 is reachable, so it is
folded, not deleted. Knob: `CAKE_FOLD`.
- **Change.**
- The 38 `*_kernel.cu` files are deleted. Their programs keep their
names, records and routes.
- Each of the 20 kept sources gains a knob block after its preamble.
Every knob has an `#ifndef` / `#error` guard.
- Each knob is an integer literal that replaces the same literal of the
base clone. For example, a topk_select record carries
`-DCAKE_INDEX_BITS=7 -DCAKE_INDEX_LOW_MASK=127
-DCAKE_INDEX_HIGH_MASK=4294967168u -DCAKE_INDEX_SCORE_MASK=2139094912`.
- Some lines change shape with the constants: four proxy_decode lines,
including the `oidx` term, and the four prefill_v1 mask tests. They
become `#if` arms that keep the generator's text for each case.
  - `CAKE_GROUP` selects an in-unit table of per-group literals.
- The decode and proxy_prefill folds put `#if` arms around the exact
base hunks.
- The decode fold keeps the `:none:` twin's `tma_3d_gmem2smem`
definition under `#if !CAKE_L2_EVICT_FIRST`. So this commit is
text-identical on its own. Commit 3 moves the helper into the header.
- The kernel line of each shared source names `CAKE_PROGRAM_KERNEL`, so
each record keeps its own kernel symbol. The 31 unfolded kernel units
keep their literal symbol, and this commit does not edit them.
- 58 registry records point at the 20 shared sources and carry their
knob flags.
- The registry's module docstring gains one clause about the shared
kernel sources.
- The structure test extends the shared-sources check to kernels.
Programs that share a kernel source must be one family with
pairwise-distinct knob sets. A shared kernel must name its symbol
through the flag. The ids do not change.
- **Proof.**
- Each of the 58 fold records is compiled from its shared source with
its flags. Its preprocessed token stream must equal its base clone's, in
the device pass and in the host pass.
- SASS and symbol tables are compared per program. Each cubin must hold
exactly one kernel, `kernel_<program>`.
- No knob name occurs in any binding text, so the binding rows coincide.
- The AST check of the registry allows only the 58 declared record lines
to change.
  - 58 content digests change.
- **Declared deviation.** None. Every fold record must have the
preprocessed text of its base clone.
- **Declared.** These are hand folds of exporter-written files.

### Commit 3 (38f5126c3) - move the device preamble and helpers into a
shared header (52 files, +259 / −4,033)

- **The copies.** Lines 1-46 are byte-identical in all 89 kernels. They
are the 15-line license, a blank line, 29 ABI and include lines, and
another blank line. 13 device helper names have byte-identical bodies in
every unit that carries them:
- 11 helpers have a single body: `elect_sync`, `mbarrier_init`,
`mbarrier_wait`, `mbarrier_arrive_expect_tx`, `mbarrier_arrive`,
`approx_exp2`, `approx_rcp`, `max_noftz`, `tma_3d_gmem2smem`,
`tma_2d_gmem2smem` and `cp_async_bulk_gmem2smem`;
- `__as_u32` has 4 overloads, which already coexist in every top-k unit;
- `make_warp_uniform` has two signatures: `int(int)` in the top-k units
and `uint32_t(uint32_t)` in the others. The two must not coexist.
- **Change.**
  - The new `csrc/cake_hopper_msa/cake_hopper_msa_device.h` holds:
    - the license, an include guard and the 29-line preamble;
    - `#define CAKE_INF CUDART_INF_F` and `#include <math_constants.h>`;
    - the 11 single-body helpers and the 4 `__as_u32` overloads;
- the `make_warp_uniform` pair, selected by `#if
defined(CAKE_WARP_UNIFORM_INT)`.
- Each of the 51 remaining kernel units drops those lines and includes
the header after its license.
- The 27 remaining top-k units add the one line `#define
CAKE_WARP_UNIFORM_INT 1` on the line before the include, so the header
sees it. So every unit keeps the `make_warp_uniform` signature it had,
and no call site changes.
- Each unit keeps its license, its own `#define` block, its knob block
and everything from `extern "C" {` on.
  - No `.py` file changes.
- **Why the binaries do not change.**
- Every helper is `__device__ __forceinline__`. An inline definition
that is never used produces no PTX, no SASS and no symbol.
- Without `-rdc=true`, nvcc drops unreferenced device functions before
the device back end of the compiler sees them.
- No helper references a macro of the unit. So moving the helpers above
the unit's `#define` block changes no expansion.
- **Proof.**
- The header rows in Validation check that each unit's preprocessed text
only gains helper definitions attributed to the header. The expected
count is 11 on each of the 32 top-k programs and 6 to 10 on each of the
57 others.
- SASS and symbol tables must be identical per program. These rows are
the gate for this commit.
  - No binding includes the header, so the binding rows coincide.
  - All 89 content digests change.
  - The header record row gives the header's sha256 and line count.
- **Declared deviations.**
- The preprocessed text of each kernel unit gains the header's helper
definitions that the unit did not use before; the change only inserts
lines, and every inserted line comes from the header.
- The JIT content digest does not cover the header, just as it does not
cover `cake_ffi_checks.h` at the base; the ninja dependency files
rebuild a module when the header changes.
- **Risk.** A top-k unit without the selector, or with the selector
after the include, would compile, but its calls would bind to the other
`make_warp_uniform` overload. The apply script checks that exactly the
27 units whose base text defined `int make_warp_uniform(int)` carry the
selector before the include. The header rows are the detector for this
case: both overloads compile to the same instructions, so the SASS rows
cannot tell them apart. An earlier draft of this commit placed the
selector after the include; the header rows reported the missing `int`
body on all 32 top-k programs while the SASS rows passed.
- **Declared.** These are hand edits of exporter-written files.

### Commit 4 (2097953f5) - drop dead host code, compact the registry,
trim the tests (3 files, +131 / −171)

- **Dead host code.** `flashinfer/msa_ops/cake_hopper_sm90.py` loses:
- `HopperTopkPlan.one` / `.ilv`, and `_TK_ONE_GEOMETRIES`, which only
`.one` read;
  - `HopperDecodePlan.pre`;
- `minb`, which is always `None`, with `_NC16_MINB` and the `:minb`
route suffix;
- `_PERSIST_RULE`, `_HALF_RULE` and `_HALF_RULE_NC16`, which are the
literal `True`;
  - the `gate == 1` branch, because `gate` is the constant 2;
  - `is_hopper_msa_device`, which has no caller;
- the `done` scratch buffer. It was allocated per scratch key and bound
into the constants, but no argument plan names it.

  Four texts lose wording about the removed code:
- the `preload_programs` docstring drops its hard-coded per-family
counts;
  - the `HopperDecodePlan` docstring drops "prologue issue";
  - the gate comment and the `f16_short_form` docstring drop "gate 1".
- **Registry.** The 89 records of `flashinfer/jit/cake_hopper_msa.py`
use only 7 distinct `arg_plan` literals.
- The 7 plans move into one `_ARG_PLANS` table under the existing `#
fmt: off`. Each record references its plan.
- `HopperMSAVariant`, a `str` alias used only in annotations, is
removed.
  - `HOPPER_MSA_VARIANTS`, which only a test read, is removed.
  - Both names leave the module's `__all__`.
  - `ffi_entry` stays in every record.
- **Tests.** The structure test changes as follows:
- `test_every_program_serves_exactly_one_route` drops the
`HOPPER_MSA_VARIANTS` pin. It checks that every record's `arg_plan` is
one of the `_ARG_PLANS` objects;
- `test_plan_ends_in_the_grid_triple` runs once per plan, so its 89
per-program ids become 7 per-plan ids;
  - the shared-bindings test compares plans by identity;
  - `_HOST_DTYPES["decode_v5"]` loses `done`.

The structure test goes from 365 to 283 ids. Every name that
`tests/msa_ops/test_msa_sm90.py` pins is kept.
- **Why behaviour is unchanged.**
  - `None or 4` is `4`, and `True and e` is `e`.
- `plan.route` never carried `:minb`, because `minb` was always `None`.
- `done` never reached a kernel, because `_Program.bind` passes only the
names in the plan.
  - No test patches `gate`.
- `_sm90_dispatch.py` imports `preload_programs`, the five launchers and
the four `*_route_available` names. None of them moves.
- **Proof.**
- For each of the three files, the AST check prunes the declared
removals from the base AST. The result must equal the head AST, apart
from the declared edits.
- The registry has exactly 7 `_ARG_PLANS` entries and 89 references to
them.
  - Whole-repository searches find no reader of a removed name.
  - Collect-only names the 89 removed ids and the 7 added ids.
- The kernel and binding sources equal those of commit 3, so the compile
rows coincide.
- **Behaviour notes.**
- `is_hopper_msa_device` leaves the `__all__` of `cake_hopper_sm90`.
`flashinfer.msa_ops` does not re-export it.
- `HopperMSAVariant` and `HOPPER_MSA_VARIANTS` leave the `__all__` of
`flashinfer.jit.cake_hopper_msa`.
- Both modules are private. Code outside the tree that reads these names
would break.
  - One per-key scratch allocation disappears.
- **Declared.** The registry change is a hand edit of an
exporter-written file.

### Validation

The compile rows compare the two trees program by program. Each row
stages the program's record-declared kernel and binding and builds them
with the JIT flag line plus the record's flags. These rows run on a CPU
node with CUDA 13.4 for both arms. The family was exported with CUDA
13.3. So these rows prove that the two trees are identical under one
toolkit. They do not prove identity with binaries built by CUDA 13.3.

There are four gate runs:
- G-A, base → commit 1. All 89 kernel rows and all 89 binding rows are
compiled;
- G-B, commit 1 → commit 2. The 58 fold rows are compiled and compared
with each record's base clone. The 31 unfolded rows coincide by file
hash;
- G-C, commit 2 → commit 3. The 89 kernel rows use the header class
described in commit 3;
- G-D, base → head, end to end.

Every preprocessed-text row runs the device pass for sm_90a and the host
pass. It drops line markers and blank lines (N0) and compares the token
stream (TOK); the header rows also drop the lines attributed to the
header (HDR). So a line that clang-format re-wrapped compares equal. No
unit uses `__LINE__`.

**Chain**

- **Shape.** The four commits sit in order over the base, and their
subjects must match the planned subjects. No forbidden shared file is
touched. These include `.pre-commit-config.yaml`, `pyproject.toml`,
`flashinfer/__init__.py`, `flashinfer/msa_ops/cute_dsl/**`,
`scripts/**`, `.github/**` and `csrc/cake_hopper_msa/cake_ffi_checks.h`.
The CPU checks row reports this.
- **Macro names.** A whole-repository search for every new macro and
knob name runs on both trees. At the base, the package names none of
them. At the head, the hits in the package must be exactly the shared
sources, the bindings, the header and the registry. Any hit outside the
package belongs to another package, which has its own JIT modules and
module-scoped flags: 23/23 new macro / knob names: 0 hits in the unit at
the base, present at HEAD, outside-unit hits identical
- **Formatting.** pre-commit runs again on the head. clang-format and
ruff-format must change no file: clang-format + ruff-format folded per
unit on the cluster (pre-commit hooks, repo config); patches: commit 1:
24,608 B over 16 files; commit 2: 60,187 B over 21 files; commit 3:
55,299 B over 20 files; commit 4: 3,512 B over 1 file; a second pass is
a no-op
- **Apply replay.** Each commit's data-driven apply script re-runs in
order on a fresh copy of the base. Each resulting tree must equal that
commit's tree: 4 unit scripts replayed in order on a fresh copy of the
base (commits 1 to 4); tree identical to the commits; the formatting
patch of each commit is applied after its script: commit 1
format_u1.patch, commit 2 format_u2.patch, commit 3 format_u3.patch,
commit 4 format_u4.patch

**Compile rows**

- **Kernel units, preprocessed text.** At commit 1, all 89 kernel units
are compiled on both trees and must be identical. At commit 2, each of
the 58 fold records is compiled from its shared source with its flags
and must equal its base clone. A residue on any row fails that row and
names the program: G-A 89/89 (N0+TOK: 89 compiled, 0 coincidence); G-B
89/89 (N0+TOK: 58 compiled, 31 coincidence); G-C 89/89 (N0+TOK+HDR: 89
compiled, 0 coincidence); G-D 89/89 (N0+TOK+HDR: 89 compiled, 0
coincidence) (both -E passes token-identical after N0; HDR runs: the
candidate tokens attributed to the shared device header are dropped, the
remainders are token-identical and the surplus definitions match the
declared count per translation unit)
- **Binding units, preprocessed text.** At commit 1, each program is
built from its role binding with its flags. It must equal its own base
binding after the backtrace mask. The mask classifies each backtrace
file and line pair: the moved sites must total 1,639, the file literal
changes for 74 programs, and the line offset is +16 on every row. The 7
sites in `cake_ffi_checks.h` do not move. At commits 2 and 3, the
bindings coincide. No knob name occurs in any binding, and no binding
includes the device header: G-A 89/89 (89 compiled, 0 coincidence; F:
1639 moved TVM_FFI sites, expected 1639, 74 renamed / 15 same file,
offset +16); G-B 89/89 (0 compiled, 89 coincidence); G-C 89/89 (0
compiled, 89 coincidence); G-D 89/89 (89 compiled, 0 coincidence; F:
1639 moved TVM_FFI sites, expected 1639, 74 renamed / 15 same file,
offset +16) (N0 + TOK + F: every TVM_FFI check site of a deleted binding
names the kept binding's file at one fixed line offset, message texts
unchanged)
- **Header rows.** These run for commit 2 → commit 3 and for base →
head. Each kernel row drops the lines that line markers attribute to
`cake_hopper_msa_device.h`. It also drops the base's own preamble and
helper region. The remaining texts must be identical. The dropped base
lines must be a sub-multiset of the header lines. The surplus must be
exactly the helper definitions that the unit did not carry: G-C: 89/89
translation units, inserted definitions == declared ({"6": 11, "7": 13,
"8": 9, "10": 24, "11": 32}); G-D: 89/89 translation units, inserted
definitions == declared ({"6": 11, "7": 13, "8": 9, "10": 24, "11": 32})
- **SASS.** `nvcc -cubin -gencode arch=compute_90a,code=sm_90a` builds
every compiled row on each arm. `cuobjdump -sass` output is compared per
`Function :` block, after masking addresses and encodings: G-A 89/89 (89
compiled, 0 coincidence); G-B 89/89 (58 compiled, 31 coincidence); G-C
89/89 (89 compiled, 0 coincidence); G-D 89/89 (89 compiled, 0
coincidence) (CUDA 13.4)
- **Symbol tables.** The function lists from `cuobjdump -symbols` must
be identical. Each cubin must hold exactly one kernel,
`kernel_<program>`: G-A 89/89 (89 compiled, 0 coincidence); G-B 89/89
(58 compiled, 31 coincidence); G-C 89/89 (89 compiled, 0 coincidence);
G-D 89/89 (89 compiled, 0 coincidence) (STT_FUNC lists identical; kernel
entries == [kernel_<program>] on both sides)
- **Host objects.** `nvcc -c` builds each binding with its flags. The
export sets must be identical, and `kernel_<program>` must be undefined
on both sides: G-A 89/89 (89 compiled, 0 coincidence); G-B 89/89 (0
compiled, 89 coincidence); G-C 89/89 (0 compiled, 89 coincidence); G-D
89/89 (89 compiled, 0 coincidence) (export sets identical;
kernel_<program> undefined on both sides)

**Other rows**

- **Digests.** The content digest of every program is recomputed on
every tree of the chain. It must change for all 89 programs at commit 1,
for the 58 fold records at commit 2 and for all 89 programs at commit 3.
The 89 uris stay distinct and keep the `<program>_sm90a_` prefix. The
rewritten `test_jit_key_is_the_content_digest` recomputes the same rule:
89 uris distinct on both trees; base == pins; 89 program digests changed
at HEAD (U1 89, U2 58, U3 89, U4 0); the device header is digested by
nothing
- **Header record.** This row records the sha256 and line count of
`cake_hopper_msa_device.h` at the head. No record lists the header in
its sources, so no content digest covers it: 1 new device header
recorded (sha256 + line count), 51 kernel TU includers, in no sources
list, not digested (disclosed)
- **Reference search.** At the head, a whole-repository search looks for
every removed host name and for the paths of the 74 deleted bindings and
the 38 deleted kernels. It also looks for the loader's former path
f-strings. The search covers every file that names the package. The 89
program names stay in `MODULES` and `ROUTES`: 10/10 (decode_pre,
deleted_files, done_scratch, fstring_sources, gate_eq_1,
is_hopper_msa_device, minb, rules, topk_one_ilv, variants: 0 hits at
HEAD, > 0 at the base)
- **Planner enumeration.** On a CPU node, the planners map the shapes of
the 47 SM90 test ids to routes and programs, at 132 and 114 SMs. The
resulting table shows which ids build which programs, folded ones
included. It also counts the shapes whose route has no program and the
admitted routes without a program: 131 test shapes at 132 / 114 SMs:
route → program identical on both trees; 104 map to a program; 21 land
on a route without a program (top-k shapes the planner does not admit,
which fall back to the CuTe DSL kernels, and the decode recipe shape); 0
admitted route(s) without a program
- **Test id sets.** Collect-only runs on both trees and names the id
difference. Expected: 453 → 372. The 89
`test_plan_ends_in_the_grid_triple[<program>]` ids leave. The 7
`test_plan_ends_in_the_grid_triple[<plan>]` ids and
`test_shared_bindings_serve_one_route_family_each` arrive. No other id
may change: Observed on the CPU node: 453 → 372 ids, 89 removed and 8
added, equal to the declared sets.
- **Tests with CUDA hidden** on a CPU node. The four files run on both
trees. Apart from the declared id changes, per-id outcomes must be
identical, skip reasons included. Without CUDA, the 26 ids of
`test_sparse_prefill.py` fail at run time on both trees, because the
file's skip helper touches `cuda:0`. These 26 failures are pre-existing
and identical. Expected: 365 passed / 62 skipped → 284 / 62. Result:
base 453 ids: 365 passed / 62 skipped; head 372 ids: 284 passed / 62
skipped (CUDA hidden), 26 pre-existing failures identical on both trees
(the ids of test_sparse_prefill.py touch cuda:0 without CUDA), per-id
identical on the common ids; 89 ids re-parametrised by design (-89 / +8)
- **Tests on H100** (SM90). The four files run on the base tree, then on
the head tree, on one H100 node. The planners read the SM count, so both
arms use the same node, and the row records the GPU name and SM count.
Each arm runs in a fresh JIT workspace, so every module it reaches is
built from source. Apart from the declared id changes, per-id outcomes
must be identical, skip reasons included. The set of built
`<program>_sm90a_` module prefixes must be identical between arms. The
41 skips are the SM120/121-only ids, by design. Expected: 412 passed /
41 skipped → 331 / 41. Result: base 453 ids: 412 passed / 41 skipped by
design; head 372 ids: 331 passed / 41 skipped by design on an NVIDIA
H100 80GB HBM3 (132 SMs, driver 535.216.03), 0 failures on both arms,
per-id identical on the 364 common ids; 89 structure-test ids
re-parametrised (89 removed, 8 added); fresh JIT workspace per arm, both
arms on one node
- **Load all.** In each arm, `build_jit_specs` builds all 89 modules,
and `preload_programs()` loads them in one process. Each `.so` must
export `__tvm_ffi_run` and `__tvm_ffi_build_cuda_version`. `cuobjdump
-symbols` must list exactly `kernel_<program>`. This row covers the
programs that no test reaches: all 89 programs built and loaded on both
arms (preload_programs + load_hopper_msa_module); every .so exports the
tvm-ffi entry and carries kernel_<program>
- **JIT isolation.** Module directories must be absent before each arm.
The base digests must equal the recorded base pins. The head digests
must be distinct and differ from the base digests. If the test phase did
not build a module, the load phase must not report `ninja: no work to
do` for it: module dirs == the 89 <name>_sm90a_<digest20> uris of the
chain on both arms; 16 / 16 programs built by the test files alone,
identical program-name sets; no stale module
- **CPU checks.** These run on one node, on both trees:
  - chain shape and commit-message form;
  - `git diff --check` and file hygiene;
  - scope, and forbidden files untouched;
  - `py_compile`;
  - ruff check and `ruff format --check` on every touched `.py` file;
- the repository's mypy hook on `cake_hopper_sm90.py`,
`jit/cake_hopper_msa.py` and `_sm90_dispatch.py`, with no new finding;
- pre-commit on the changed files, and with `--all-files` on both
checkouts;
  - collect-only parity;
  - AST identity for the three Python files;
  - the reference search, the macro-name search and the digest rows;
  - the planner enumeration;
  - the apply replay;
  - the public-text scan;
  - a clean worktree.

  Result: 20/20
- **Rows limited by the environment (count and reason):** 0

### Not in this PR

- **Decode routes without a program.** A hand evaluation in #7222 finds
that the decode planner can emit routes that have no program. For such a
route, `route_program` raises `KeyError`, and the decode path has no
CuTe DSL fallback. A host fallback would turn that error into a computed
output for reachable shapes, so it is not mechanical. A follow-up needs
a CPU enumeration of `plan_sparse_decode` and an H100 reference
comparison. The planner enumeration row in Validation reports any test
shape on such a route.
- **The 4 tiny-context top-k programs.** These are c32:w1 and c256:w1 at
index bits 1 and 3. Unregistering them would send those shapes to the
CuTe DSL top-k. This is an owner decision. It needs an H100 A/B at tiles
{1, 2, 5, 6, 7, 8}.
- **`cake_ffi_checks.h`.** It is byte-identical to the copies in
`flashinfer/cake_gdp_backend/csrc/` and
`flashinfer/experimental/cake_rubin_mla_nvfp4_decode/csrc/`.
De-duplicating it is a cross-package decision. This PR does not touch
it.
- **The 132-SM fold remap and `_L2_BYTES`.** `aa3467` (f16t4F)
hard-codes 132 SMs in its fold remap. The host module sets `_L2_BYTES =
50 << 20`. Both are owner questions. The 132 literal stays inside the
`#if CAKE_FOLD` block.
- **Further binding folds, 15 → 9.** These are prefill_v1 3 → 1,
proxy_decode 4 → 2 and proxy_prefill 3 → 1. They are not among the
audited steps.
- **The decode T2 fold.** Folding the `7b41c417` binding into the other
decode_v5 template would change its preprocessed text.
- **The duplicated `--use_fast_math` flags.** 28 records repeat the
default `-use_fast_math` of `gen_jit_spec`. The flags are part of the
content digest, so they stay.
- **A loader closure digest.** Hashing the include closure in
`_content_digest` would cover `cake_ffi_checks.h` and the device header.
That changes the loader's behaviour, so it is a separate change.
- **Exporter emission.** If the exporter emitted the kernel folds, the
shared bindings and the device header, the tree would stay regenerable.
The exporter rules for each unit are filed on #7222 as a comment.

## 🔍 Related Issues

Tracking issue: #7222

Part of #7222

The deferred items are listed under "Not in this PR". The exporter rules
for each unit are filed on #7222 as a comment.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks run on the changed files, and with `--all-files` on both
checkouts (base and head). The repository's mypy hook must report no new
finding. The formatting row and the CPU checks row in Validation give
the results.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

This PR updates one test file,
`tests/msa_ops/test_cake_hopper_msa_programs.py`. It adds
`test_shared_bindings_serve_one_route_family_each`. It also replaces the
89 per-program grid-triple ids with 7 per-plan ids. The other three
files are not edited. The four files under `tests/msa_ops/` collect 453
ids at the base and 372 at the head. Validation lists the run on H100
and the run with CUDA hidden on a CPU node.

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.

This PR is not experimental. The package lives under
`csrc/cake_hopper_msa/`, `flashinfer/msa_ops/` and `flashinfer/jit/`,
and its tests live under `tests/msa_ops/`. So this PR declares no
experimental test scope.

## Reviewer Notes

- **Hand folds and hand edits.** Commits 1, 2 and 3 fold
exporter-written translation units by hand. Commits 1, 2 and 4 edit the
registry by hand. A re-export of the family rewrites every hashed unit
and the registry. It would re-inline the 20 shared kernel sources, the
15 shared bindings and the header. The exporter rules for each unit are
filed on #7222 as a comment.
- **Formatting.** The committed text of every edited or new `.cu`, `.h`
and `.py` file is formatted with the repository's pre-commit hooks,
clang-format and ruff-format. The hooks ran per commit, and their output
is folded into each commit, so pre-commit is a no-op on the head. The
formatting row in Validation checks this.
- **Declared deviations.**
- Commit 1: every `TVM_FFI_CHECK` / `TVM_FFI_THROW` site of the 89
binding translation units, 1,639 sites in all, reports the shared
binding's file name and a line number 16 higher in a failure backtrace;
message texts are unchanged and no test reads a backtrace.
- Commit 3: the preprocessed text of each kernel unit gains the header's
helper definitions that the unit did not use before; the change only
inserts lines, and every inserted line comes from the header.
- Commit 3: the JIT content digest does not cover the header, just as it
does not cover `cake_ffi_checks.h` at the base; the ninja dependency
files rebuild a module when the header changes.
- **Behaviour notes.**
- Commit 4: `is_hopper_msa_device` leaves the `__all__` of
`cake_hopper_sm90`, and `HopperMSAVariant` and `HOPPER_MSA_VARIANTS`
leave the `__all__` of `flashinfer.jit.cake_hopper_msa`. Both modules
are private.
  - Commit 4: one per-key scratch allocation disappears.
- **Module cache.** Every JIT key changes at commit 1. 58 keys change at
commit 2, and all 89 change at commit 3. The uri prefix
`<program>_sm90a_` stays. So a warm cache rebuilds each program once. No
test or doc pins a digest value or a module name.
- **Toolkit.** The compile rows use CUDA 13.4 for both arms. They prove
that the two trees are identical under that toolkit. The family was
exported with CUDA 13.3.
- **Coverage.**
- 47 of the 48 ids of `test_msa_sm90.py`, the `@sm90_only` ones,
exercise the Cake path through the public operations, with no
environment switch; the 48th is a CPU-only predicate test.
- The test phase builds only the modules that the test shapes reach. The
planner enumeration row lists them.
  - The load-all row builds and loads all 89 modules in each arm.
- The 41 skipped ids need SM120/121. On H100 they reach no Cake program.
- **Base.** This PR is published from `main` `e3b5b1e34`. `main` at
publish time is `131f85942`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Standardized Hopper MSA kernel builds around configurable launch
settings and shared device support.
* **Behavior Changes**
* Updated sparse-decode route selection, including special-route
fallback when a route is unavailable.
  * Restricted fold-free prefill planning to eligible configurations.
* Removed the public Hopper MSA device-detection helper and some
decode-planning options.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5c314c5](https://github.com/flashinfer-ai/flashinfer/commit/5c314c510256271da2e84dad887b5acc9b6a9b2b)

- **作者**: eigen
- **时间**: 2026-10-25T18:56:40Z
- **提交信息**: perf(cake_rubin_mla_nvfp4_decode): two epilogue staging tiles per correction warp for Rubin (sm_107a) (#7329)

`flashinfer/experimental/cake_rubin_mla_nvfp4_decode` is the Rubin
(SM107, `sm_107a`) variant of the Cake NVFP4 MLA paged decode. Cake is
NVIDIA's kernel generator. On compute capability 10.7,
`flashinfer.mla.cake_mla_nvfp4_paged_decode` routes to this package. It
decodes BF16 queries against the paged NVFP4 MLA KV cache (352 B per
token) and writes BF16 output. Previously, the mixed decode's PV
epilogue wrote its eight 64-dim output rounds through one 4 KB staging
tile per correction warp, and before each round it waited for the
previous round's bulk tensor store to finish reading that tile. Each
correction warp now alternates between two staging tiles, so a round
waits only for the store from two rounds back; the shared-memory
footprint grows from 323,584 to 332,800 bytes. The arithmetic is
unchanged. This PR also adds a second full-decode program with a
converter software pipeline in the pair body. In the previous program,
each of a tile's eight rounds waited for its loads, its scale and its
conversion in turn. In the new program, a converter warp first loads the
16-byte pieces and scale words for all eight rounds of a tile. It then
forms the scales and converts, so the rounds overlap. The host selects
this program from the plan scalars of one problem class: 64 requests × 8
query tokens × 96 heads over 64K keys (H96-Q8-B64-KV64K). The same
selection also applies to a 96K-key sweep point outside the table. Every
other configuration keeps its existing program and host plan. In the
table, 73 configurations keep their program and plan, and only
H96-Q8-B64-KV64K is dispatched to the new program. There is no API
change. The output is bitwise identical to the previous version on every
configuration, including the routed one. The baseline is the previous
version of this package, which FlashInfer `main` ships (merged in
#7206). Against it, the geometric-mean speedup is 1.0060 on board A,
ranging from 0.982 (H96-Q4-B2-KV64K) to 1.044 (H192-Q1-B2-KV64K). On
board B it is 1.0062, ranging from 0.980 (H96-Q4-B96-KV64K) to 1.047
(H448-Q1-B1-KV64K). The gain concentrates on small-batch rows (batch
1–2), where the output drains sooner. The routed configuration
H96-Q8-B64-KV64K reaches 1.013 on board A and 1.009 on board B. The
largest gains (A, B) are H192-Q1-B2-KV64K (1.044, 1.044),
H448-Q1-B1-KV64K (1.043, 1.047), H96-Q8-B1-KV64K (1.039, 1.037),
H192-Q1-B1-KV128K (1.030, 1.036) and H448-Q1-B2-KV64K (1.028, 1.033). On
both boards, 12 of the 74 configurations have a speedup of at least
1.010, and all of them are batch 1–8 rows of the H96-Q8, H192-Q1 and
H448-Q1 families. The lowest rows (A, B) are H96-Q4-B2-KV64K (0.982,
0.983), H96-Q4-B96-KV64K (1.003, 0.980), H192-Q1-B96-KV64K (1.001,
0.983), H96-Q8-B2-KV128K (1.013, 0.986) and H192-Q1-B48-KV128K (0.986,
1.000).

| Configuration | Previous (µs), board A | Previous (µs), board B | This
PR (µs), board A | This PR (µs), board B | Speedup A | Speedup B |
|---|---:|---:|---:|---:|---:|---:|
| H96-Q4-B1-KV64K | 24.24 | 25.05 | 24.07 | 24.96 | 1.007 | 1.003 |
| H96-Q4-B2-KV64K | 34.94 | 36.32 | 35.58 | 36.93 | 0.982 | 0.983 |
| H96-Q4-B4-KV64K | 53.01 | 54.33 | 53.12 | 54.56 | 0.998 | 0.996 |
| H96-Q4-B8-KV64K | 95.28 | 99.38 | 95.86 | 99.58 | 0.994 | 0.998 |
| H96-Q4-B16-KV64K | 184.01 | 192.77 | 183.72 | 191.80 | 1.002 | 1.005 |
| H96-Q4-B24-KV64K | 264.72 | 279.11 | 264.52 | 277.46 | 1.001 | 1.006 |
| H96-Q4-B32-KV64K | 359.95 | 374.19 | 359.54 | 377.75 | 1.001 | 0.991 |
| H96-Q4-B48-KV64K | 505.18 | 533.66 | 505.21 | 532.71 | 1.000 | 1.002 |
| H96-Q4-B64-KV64K | 668.57 | 718.40 | 667.74 | 711.20 | 1.001 | 1.010 |
| H96-Q4-B96-KV64K | 1013.80 | 1073.07 | 1010.81 | 1094.47 | 1.003 |
0.980 |
| H96-Q4-B128-KV64K | 1310.12 | 1437.91 | 1308.68 | 1413.68 | 1.001 |
1.017 |
| H96-Q4-B1-KV128K | 36.45 | 37.69 | 36.68 | 37.70 | 0.994 | 1.000 |
| H96-Q4-B2-KV128K | 53.31 | 54.62 | 53.63 | 54.93 | 0.994 | 0.994 |
| H96-Q4-B4-KV128K | 91.14 | 95.68 | 91.74 | 95.68 | 0.993 | 1.000 |
| H96-Q4-B8-KV128K | 175.22 | 186.10 | 175.50 | 184.38 | 0.998 | 1.009 |
| H96-Q4-B16-KV128K | 347.17 | 364.98 | 345.25 | 362.71 | 1.006 | 1.006
|
| H96-Q4-B24-KV128K | 503.90 | 544.45 | 503.03 | 535.14 | 1.002 | 1.017
|
| H96-Q4-B32-KV128K | 665.95 | 729.31 | 665.37 | 710.18 | 1.001 | 1.027
|
| H96-Q4-B48-KV128K | 990.09 | 1044.33 | 989.31 | 1054.06 | 1.001 |
0.991 |
| H96-Q4-B64-KV128K | 1288.88 | 1403.27 | 1293.63 | 1403.32 | 0.996 |
1.000 |
| H96-Q4-B96-KV128K | 1933.08 | 2115.07 | 1934.76 | 2121.90 | 0.999 |
0.997 |
| H96-Q4-B128-KV128K | 2560.94 | 2798.91 | 2555.55 | 2798.37 | 1.002 |
1.000 |
| H96-Q8-B1-KV64K | 30.68 | 31.88 | 29.53 | 30.76 | 1.039 | 1.037 |
| H96-Q8-B2-KV64K | 47.40 | 48.49 | 46.24 | 47.36 | 1.025 | 1.024 |
| H96-Q8-B4-KV64K | 81.14 | 83.60 | 80.36 | 83.02 | 1.010 | 1.007 |
| H96-Q8-B8-KV64K | 152.06 | 163.23 | 152.22 | 163.57 | 0.999 | 0.998 |
| H96-Q8-B16-KV64K | 285.12 | 309.27 | 285.78 | 309.67 | 0.998 | 0.999 |
| H96-Q8-B24-KV64K | 435.67 | 449.50 | 436.27 | 448.61 | 0.999 | 1.002 |
| H96-Q8-B32-KV64K | 560.40 | 587.67 | 558.83 | 587.19 | 1.003 | 1.001 |
| H96-Q8-B64-KV64K | 1109.24 | 1102.01 | 1094.48 | 1092.17 | 1.013 |
1.009 |
| H96-Q8-B1-KV128K | 47.63 | 48.57 | 46.76 | 47.44 | 1.019 | 1.024 |
| H96-Q8-B2-KV128K | 80.76 | 83.21 | 79.74 | 84.38 | 1.013 | 0.986 |
| H96-Q8-B4-KV128K | 150.21 | 161.08 | 149.40 | 160.55 | 1.005 | 1.003 |
| H96-Q8-B8-KV128K | 287.68 | 307.65 | 286.52 | 306.85 | 1.004 | 1.003 |
| H96-Q8-B16-KV128K | 555.69 | 603.85 | 554.19 | 602.29 | 1.003 | 1.003
|
| H96-Q8-B24-KV128K | 841.69 | 877.80 | 840.90 | 875.94 | 1.001 | 1.002
|
| H96-Q8-B32-KV128K | 1106.97 | 1155.12 | 1105.62 | 1154.47 | 1.001 |
1.001 |
| H96-Q8-B64-KV128K | 2196.53 | 2328.58 | 2189.62 | 2328.25 | 1.003 |
1.000 |
| H192-Q1-B1-KV64K | 20.19 | 21.19 | 19.91 | 20.79 | 1.014 | 1.019 |
| H192-Q1-B2-KV64K | 25.01 | 26.06 | 23.96 | 24.96 | 1.044 | 1.044 |
| H192-Q1-B4-KV64K | 37.03 | 38.18 | 36.68 | 37.52 | 1.009 | 1.018 |
| H192-Q1-B8-KV64K | 58.62 | 60.81 | 58.02 | 59.93 | 1.010 | 1.015 |
| H192-Q1-B16-KV64K | 106.11 | 112.36 | 105.02 | 111.99 | 1.010 | 1.003
|
| H192-Q1-B24-KV64K | 155.12 | 166.61 | 154.44 | 165.44 | 1.004 | 1.007
|
| H192-Q1-B32-KV64K | 202.48 | 214.14 | 200.99 | 213.21 | 1.007 | 1.004
|
| H192-Q1-B48-KV64K | 297.93 | 319.04 | 296.65 | 317.57 | 1.004 | 1.005
|
| H192-Q1-B64-KV64K | 379.24 | 424.16 | 372.85 | 425.48 | 1.017 | 0.997
|
| H192-Q1-B96-KV64K | 568.24 | 607.28 | 567.77 | 617.64 | 1.001 | 0.983
|
| H192-Q1-B128-KV64K | 749.43 | 850.99 | 748.33 | 851.08 | 1.001 | 1.000
|
| H192-Q1-B1-KV128K | 25.68 | 26.71 | 24.95 | 25.78 | 1.030 | 1.036 |
| H192-Q1-B2-KV128K | 36.76 | 37.81 | 36.33 | 37.24 | 1.012 | 1.015 |
| H192-Q1-B4-KV128K | 56.99 | 59.72 | 56.50 | 58.47 | 1.009 | 1.021 |
| H192-Q1-B8-KV128K | 105.64 | 111.78 | 104.23 | 111.20 | 1.013 | 1.005
|
| H192-Q1-B16-KV128K | 199.33 | 216.85 | 200.73 | 216.01 | 0.993 | 1.004
|
| H192-Q1-B24-KV128K | 301.22 | 321.90 | 299.80 | 321.07 | 1.005 | 1.003
|
| H192-Q1-B32-KV128K | 386.20 | 413.11 | 384.98 | 410.12 | 1.003 | 1.007
|
| H192-Q1-B48-KV128K | 576.44 | 620.28 | 584.64 | 619.99 | 0.986 | 1.000
|
| H192-Q1-B64-KV128K | 741.92 | 824.72 | 744.29 | 823.91 | 0.997 | 1.001
|
| H192-Q1-B96-KV128K | 1124.12 | 1202.20 | 1123.14 | 1197.71 | 1.001 |
1.004 |
| H192-Q1-B128-KV128K | 1464.59 | 1608.64 | 1463.66 | 1613.88 | 1.001 |
0.997 |
| H448-Q1-B1-KV64K | 25.22 | 26.22 | 24.19 | 25.04 | 1.043 | 1.047 |
| H448-Q1-B2-KV64K | 36.77 | 38.16 | 35.78 | 36.95 | 1.028 | 1.033 |
| H448-Q1-B4-KV64K | 58.44 | 59.98 | 57.83 | 59.26 | 1.011 | 1.012 |
| H448-Q1-B8-KV64K | 104.25 | 110.11 | 104.66 | 110.61 | 0.996 | 0.995 |
| H448-Q1-B16-KV64K | 200.51 | 209.00 | 199.36 | 207.88 | 1.006 | 1.005
|
| H448-Q1-B24-KV64K | 286.85 | 311.87 | 285.54 | 310.43 | 1.005 | 1.005
|
| H448-Q1-B32-KV64K | 377.03 | 412.17 | 371.00 | 413.69 | 1.016 | 0.996
|
| H448-Q1-B1-KV128K | 36.23 | 37.12 | 35.85 | 36.13 | 1.011 | 1.027 |
| H448-Q1-B2-KV128K | 56.86 | 59.39 | 56.52 | 57.92 | 1.006 | 1.025 |
| H448-Q1-B4-KV128K | 104.58 | 108.60 | 103.61 | 109.19 | 1.009 | 0.995
|
| H448-Q1-B8-KV128K | 197.32 | 210.55 | 196.23 | 209.51 | 1.006 | 1.005
|
| H448-Q1-B16-KV128K | 383.01 | 404.05 | 381.58 | 402.83 | 1.004 | 1.003
|
| H448-Q1-B24-KV128K | 565.01 | 607.40 | 559.00 | 606.11 | 1.011 | 1.002
|
| H448-Q1-B32-KV128K | 736.20 | 803.82 | 726.35 | 806.41 | 1.014 | 0.997
|

*NVIDIA R200 (pre-release board, reported as "NVIDIA Graphics Device",
compute capability 10.7 / `sm_107a`, 208 SMs, 120 MiB L2), driver
615.71.10, CUDA 13.4 (runtime 13.4.92), PyTorch 2.14.1+cu130. Board A
and board B are two boards of the same model, each measured in its own
session. Configurations are named H{heads}-Q{query
length}-B{batch}-KV{keys per sequence}; H is 96, 192 or 448 heads; page
size 64. Each latency is one decode call in µs (quantizer + decode +
merge). For each ABBA group it is the median of 15 replays of a
20-launch CUDA graph, and the reported value is the median over 3 ABBA
groups. Both versions were interleaved in ABBA groups in one process,
and each version used its own cold-L2 KV copies. Speedup = previous /
this PR; above 1 means this PR is faster. The H96-Q8-B64-KV64K row was
re-measured on the delivered bytes in two sessions, on boards 0082 (A)
and 0130 (B) of the same model, with the same protocol over 5 ABBA
groups and both versions under the same power cap; the other 73 rows
come from the earlier sessions on boards 0082 (A) and 0074 (B).*

The existing `cake_mla_nvfp4_paged_decode` package ships this Cake
decode on `sm_100a` and `sm_103a`, and the Rubin package ships it on
`sm_107a`, including the decode-context-parallel form.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated Cake Rubin MLA NVFP4 decoding to use more on-device working
memory and revised output handling. These changes apply to both standard
and full decoding paths, while preserving existing decoding options and
output modes.
* No new user-facing settings or changes to the available decoding
controls are included.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [1e47a69](https://github.com/flashinfer-ai/flashinfer/commit/1e47a692ef2a37e5c1decd7d43944d6e73623b34)

- **作者**: eigen
- **时间**: 2026-10-25T18:55:49Z
- **提交信息**: perf(cake_mok): owner-rank load bins in the count kernels, lower host launch overhead and an early backward scratch release (#7326)

The Cake MoK package ships 16 fused kernel variants and 32 small
scheduler and epilogue kernels: 48 per architecture, 144 libraries on 3
architectures. Fused variants cover BF16 and native MXFP8 routed
experts, plain and clamped SwiGLU, forward, context-only recompute and
backward (BF16 or FP32 weight-gradient accumulation). This PR changes
the nine scheduler count kernels to also bin the routed load per owning
rank and the expert-layout kernel to follow a per-schedule layout
interface (these ten units ship on sm_100a, sm_103a and sm_107a and are
the only units whose machine code changes), and changes the package's
host-side launch path to derive the expert layout once per schedule,
zero-fill one counter slab per launch and release the backward's dead
scratch before the output epilogue. It adds no variant and keeps the
arithmetic, MXFP8 recipe and public API of the previous Cake version of
this package on `main`. The table below gives both versions' step time
and this PR's speedup per shape on B200 (sm_100a) and GB300 (sm_103a).

Step time of one MoE training step (forward + backward of the routed and
shared experts, including dispatch/combine), ms; A = previous Cake
version (main @ 1ff9f677), B = this PR; each value is the two-round mean
(r1 / r2 = the two measurement rounds, each the median over three
sampling groups of the per-iteration slowest rank); Δ % = (B − A) / A;
speedup = A / B.

**B200 (sm_100a), EP8: 8 GPUs; CUDA 13.4 (nvcc `Build
cuda_13.4.r13.4/compiler.38855100_0`), driver 580.82.07, torch
2.14.1+cu130 cuda 13.0 py 3.12.15, container image
devel:cuda13.4-20261005; `glm52_ep8_bf16_full_skew2_defaults`
re-measured once on a fresh allocation after its first measurement
failed the drift check.**

| shape | A ms (r1 / r2) | B ms (r1 / r2) | Δ % (r1 / r2) | speedup A/B
|
|---|---|---|---|---|
| `glm52_ep8_bf16_full_defaults` | 30.310 (30.435 / 30.184) | 30.294
(30.247 / 30.340) | -0.05 (-0.62 / +0.52) | 1.001 |
| `glm52_ep8_bf16_ckpt_defaults` | 36.916 (36.939 / 36.893) | 36.838
(36.950 / 36.726) | -0.21 (+0.03 / -0.45) | 1.002 |
| `glm52_ep8_bf16_full_cap2_defaults` | 30.626 (30.638 / 30.613) |
30.268 (30.346 / 30.190) | -1.17 (-0.95 / -1.38) | 1.012 |
| `glm52_ep8_bf16_full_mb393216_defaults` | 30.336 (30.190 / 30.482) |
30.332 (30.465 / 30.200) | -0.01 (+0.91 / -0.92) | 1.000 |
| `glm52_ep8_bf16_ckpt_mb393216_defaults` | 36.829 (36.823 / 36.834) |
36.787 (36.721 / 36.853) | -0.11 (-0.28 / +0.05) | 1.001 |
| `glm52_ep8_bf16_full_imbal_defaults` | 87.242 (87.083 / 87.401) |
87.676 (87.380 / 87.972) | +0.50 (+0.34 / +0.65) | 0.995 |
| `glm52_ep8_bf16_ckpt_imbal_defaults` | 99.411 (99.942 / 98.881) |
99.398 (99.082 / 99.714) | -0.01 (-0.86 / +0.84) | 1.000 |
| `glm52_ep8_bf16_full_ragged_defaults` | 20.707 (20.660 / 20.754) |
20.668 (20.611 / 20.724) | -0.19 (-0.23 / -0.15) | 1.002 |
| `glm52_ep8_bf16_ckpt_ragged_defaults` | 25.093 (25.146 / 25.039) |
25.159 (25.258 / 25.061) | +0.26 (+0.44 / +0.09) | 0.997 |
| `glm52_ep8_bf16_full_raggedimbal_defaults` | 49.168 (49.082 / 49.255)
| 48.893 (49.085 / 48.700) | -0.56 (+0.01 / -1.13) | 1.006 |
| `glm52_ep8_bf16_ckpt_raggedimbal_defaults` | 59.538 (59.677 / 59.399)
| 59.667 (59.697 / 59.636) | +0.22 (+0.03 / +0.40) | 0.998 |
| `glm52_ep8_bf16_full_skew2_defaults` | 85.793 (85.682 / 85.904) |
85.777 (85.898 / 85.656) | -0.02 (+0.25 / -0.29) | 1.000 |
| `glm52_ep8_bf16_full_skew4_defaults` | 175.101 (174.725 / 175.477) |
174.377 (173.833 / 174.920) | -0.41 (-0.51 / -0.32) | 1.004 |
| `glm52_ep8_bf16_full_skew8_defaults` | 231.429 (233.584 / 229.274) |
230.294 (230.326 / 230.261) | -0.48 (-1.39 / +0.43) | 1.005 |
| `glm52_ep8_mxfp8_full_defaults` | 22.350 (22.433 / 22.266) | 22.166
(22.156 / 22.177) | -0.82 (-1.23 / -0.40) | 1.008 |
| `glm52_ep8_mxfp8_ckpt_defaults` | 27.247 (27.172 / 27.322) | 27.049
(27.075 / 27.023) | -0.73 (-0.36 / -1.09) | 1.007 |
| `glm52_ep8_mxfp8_full_cap2_defaults` | 22.500 (22.360 / 22.641) |
22.300 (22.346 / 22.254) | -0.89 (-0.06 / -1.71) | 1.009 |
| `glm52_ep8_mxfp8_full_mb393216_defaults` | 22.269 (22.283 / 22.255) |
22.108 (22.078 / 22.138) | -0.72 (-0.92 / -0.53) | 1.007 |
| `glm52_ep8_mxfp8_ckpt_mb393216_defaults` | 27.272 (27.354 / 27.191) |
27.062 (27.052 / 27.072) | -0.77 (-1.10 / -0.44) | 1.008 |
| `glm52_ep8_mxfp8_full_imbal_defaults` | 60.023 (59.733 / 60.314) |
60.000 (59.969 / 60.030) | -0.04 (+0.40 / -0.47) | 1.000 |
| `glm52_ep8_mxfp8_ckpt_imbal_defaults` | 68.995 (69.068 / 68.922) |
68.793 (68.909 / 68.677) | -0.29 (-0.23 / -0.36) | 1.003 |
| `glm52_ep8_mxfp8_full_ragged_defaults` | 15.975 (15.967 / 15.984) |
15.596 (15.600 / 15.591) | -2.38 (-2.30 / -2.46) | 1.024 |
| `glm52_ep8_mxfp8_ckpt_ragged_defaults` | 19.412 (19.453 / 19.371) |
19.114 (19.095 / 19.133) | -1.53 (-1.84 / -1.23) | 1.016 |
| `glm52_ep8_mxfp8_full_raggedimbal_defaults` | 33.871 (33.691 / 34.051)
| 33.764 (33.707 / 33.821) | -0.31 (+0.05 / -0.68) | 1.003 |
| `glm52_ep8_mxfp8_ckpt_raggedimbal_defaults` | 41.659 (41.665 / 41.654)
| 41.594 (41.751 / 41.437) | -0.16 (+0.21 / -0.52) | 1.002 |
| `glm52_ep8_mxfp8_full_skew2_defaults` | 60.168 (59.988 / 60.347) |
59.825 (59.791 / 59.860) | -0.57 (-0.33 / -0.81) | 1.006 |
| `glm52_ep8_mxfp8_full_skew4_defaults` | 116.782 (116.802 / 116.762) |
116.883 (116.863 / 116.904) | +0.09 (+0.05 / +0.12) | 0.999 |
| `glm52_ep8_mxfp8_full_skew8_defaults` | 155.664 (155.821 / 155.508) |
155.246 (155.174 / 155.318) | -0.27 (-0.41 / -0.12) | 1.003 |

**B200 (sm_100a), EP4: 4 GPUs; CUDA 13.4 (nvcc `Build
cuda_13.4.r13.4/compiler.38855100_0`), driver 580.82.07, torch
2.14.1+cu130 cuda 13.0 py 3.12.15, container image
devel:cuda13.4-20261005; `glm52_ep4_mxfp8_full_skew8_defaults`
re-measured once on a fresh allocation after its first measurement
failed the drift check.**

| shape | A ms (r1 / r2) | B ms (r1 / r2) | Δ % (r1 / r2) | speedup A/B
|
|---|---|---|---|---|
| `glm52_ep4_bf16_full_defaults` | 31.332 (31.352 / 31.312) | 31.262
(31.286 / 31.237) | -0.22 (-0.21 / -0.24) | 1.002 |
| `glm52_ep4_bf16_ckpt_defaults` | 38.160 (38.109 / 38.210) | 38.249
(38.302 / 38.196) | +0.23 (+0.51 / -0.04) | 0.998 |
| `glm52_ep4_bf16_full_cap2_defaults` | 31.560 (31.662 / 31.457) |
31.374 (31.280 / 31.468) | -0.59 (-1.21 / +0.04) | 1.006 |
| `glm52_ep4_bf16_full_mb393216_defaults` | 31.541 (31.560 / 31.521) |
31.313 (31.324 / 31.303) | -0.72 (-0.75 / -0.69) | 1.007 |
| `glm52_ep4_bf16_ckpt_mb393216_defaults` | 38.132 (37.997 / 38.267) |
38.167 (38.107 / 38.227) | +0.09 (+0.29 / -0.10) | 0.999 |
| `glm52_ep4_bf16_full_imbal_defaults` | 69.370 (69.080 / 69.660) |
69.151 (68.950 / 69.352) | -0.31 (-0.19 / -0.44) | 1.003 |
| `glm52_ep4_bf16_ckpt_imbal_defaults` | 80.437 (80.416 / 80.458) |
80.425 (80.451 / 80.399) | -0.01 (+0.04 / -0.07) | 1.000 |
| `glm52_ep4_bf16_full_ragged_defaults` | 21.884 (21.945 / 21.823) |
21.733 (21.796 / 21.670) | -0.69 (-0.68 / -0.70) | 1.007 |
| `glm52_ep4_bf16_ckpt_ragged_defaults` | 26.452 (26.400 / 26.503) |
26.450 (26.412 / 26.488) | -0.01 (+0.05 / -0.06) | 1.000 |
| `glm52_ep4_bf16_full_raggedimbal_defaults` | 40.153 (40.219 / 40.087)
| 40.185 (40.199 / 40.171) | +0.08 (-0.05 / +0.21) | 0.999 |
| `glm52_ep4_bf16_ckpt_raggedimbal_defaults` | 49.189 (49.458 / 48.920)
| 49.005 (48.872 / 49.138) | -0.37 (-1.18 / +0.44) | 1.004 |
| `glm52_ep4_bf16_full_skew2_defaults` | 69.154 (69.169 / 69.139) |
69.017 (68.971 / 69.062) | -0.20 (-0.29 / -0.11) | 1.002 |
| `glm52_ep4_bf16_full_skew4_defaults` | 104.621 (103.965 / 105.276) |
104.353 (104.398 / 104.309) | -0.25 (+0.42 / -0.92) | 1.003 |
| `glm52_ep4_bf16_full_skew8_defaults` | 120.499 (120.353 / 120.645) |
120.323 (120.407 / 120.239) | -0.15 (+0.05 / -0.34) | 1.001 |
| `glm52_ep4_mxfp8_full_defaults` | 23.186 (23.203 / 23.168) | 23.009
(23.027 / 22.992) | -0.76 (-0.76 / -0.76) | 1.008 |
| `glm52_ep4_mxfp8_ckpt_defaults` | 28.323 (28.380 / 28.265) | 28.219
(28.295 / 28.143) | -0.37 (-0.30 / -0.43) | 1.004 |
| `glm52_ep4_mxfp8_full_cap2_defaults` | 23.354 (23.331 / 23.377) |
23.195 (23.200 / 23.190) | -0.68 (-0.56 / -0.80) | 1.007 |
| `glm52_ep4_mxfp8_full_mb393216_defaults` | 23.192 (23.190 / 23.195) |
23.085 (23.105 / 23.064) | -0.46 (-0.37 / -0.56) | 1.005 |
| `glm52_ep4_mxfp8_ckpt_mb393216_defaults` | 28.332 (28.346 / 28.317) |
28.226 (28.159 / 28.294) | -0.37 (-0.66 / -0.08) | 1.004 |
| `glm52_ep4_mxfp8_full_imbal_defaults` | 48.985 (48.937 / 49.034) |
48.975 (49.033 / 48.917) | -0.02 (+0.20 / -0.24) | 1.000 |
| `glm52_ep4_mxfp8_ckpt_imbal_defaults` | 57.678 (57.543 / 57.813) |
57.662 (57.587 / 57.736) | -0.03 (+0.08 / -0.13) | 1.000 |
| `glm52_ep4_mxfp8_full_ragged_defaults` | 16.796 (16.843 / 16.750) |
16.674 (16.680 / 16.668) | -0.73 (-0.97 / -0.49) | 1.007 |
| `glm52_ep4_mxfp8_ckpt_ragged_defaults` | 20.394 (20.401 / 20.388) |
20.236 (20.262 / 20.211) | -0.78 (-0.68 / -0.87) | 1.008 |
| `glm52_ep4_mxfp8_full_raggedimbal_defaults` | 28.553 (28.560 / 28.546)
| 28.362 (28.377 / 28.347) | -0.67 (-0.64 / -0.70) | 1.007 |
| `glm52_ep4_mxfp8_ckpt_raggedimbal_defaults` | 35.012 (34.996 / 35.027)
| 34.937 (34.860 / 35.015) | -0.21 (-0.39 / -0.04) | 1.002 |
| `glm52_ep4_mxfp8_full_skew2_defaults` | 49.059 (49.101 / 49.017) |
48.850 (48.910 / 48.790) | -0.43 (-0.39 / -0.46) | 1.004 |
| `glm52_ep4_mxfp8_full_skew4_defaults` | 72.743 (72.795 / 72.692) |
72.649 (72.592 / 72.706) | -0.13 (-0.28 / +0.02) | 1.001 |
| `glm52_ep4_mxfp8_full_skew8_defaults` | 81.422 (81.556 / 81.288) |
81.206 (81.204 / 81.209) | -0.26 (-0.43 / -0.10) | 1.003 |

**GB300 (sm_103a), EP4: 4 GPUs; CUDA 13.4 (nvcc `Build
cuda_13.4.r13.4/compiler.38855100_0`), driver 580.159.03, torch
2.14.1+cu130 cuda 13.0 py 3.12.15, container image
devel:cuda13.4-20261005.**

| shape | A ms (r1 / r2) | B ms (r1 / r2) | Δ % (r1 / r2) | speedup A/B
|
|---|---|---|---|---|
| `glm52_ep4_bf16_full_defaults` | 24.355 (24.351 / 24.359) | 24.343
(24.366 / 24.321) | -0.05 (+0.06 / -0.15) | 1.000 |
| `glm52_ep4_bf16_ckpt_defaults` | 29.741 (29.735 / 29.747) | 29.738
(29.765 / 29.710) | -0.01 (+0.10 / -0.12) | 1.000 |
| `glm52_ep4_bf16_full_cap2_defaults` | 24.468 (24.481 / 24.456) |
24.378 (24.364 / 24.393) | -0.37 (-0.48 / -0.26) | 1.004 |
| `glm52_ep4_bf16_full_mb393216_defaults` | 24.358 (24.344 / 24.372) |
24.340 (24.357 / 24.322) | -0.08 (+0.05 / -0.21) | 1.001 |
| `glm52_ep4_bf16_ckpt_mb393216_defaults` | 29.727 (29.699 / 29.755) |
29.748 (29.751 / 29.744) | +0.07 (+0.18 / -0.04) | 0.999 |
| `glm52_ep4_bf16_full_imbal_defaults` | 54.918 (54.798 / 55.038) |
54.990 (55.013 / 54.968) | +0.13 (+0.39 / -0.13) | 0.999 |
| `glm52_ep4_bf16_ckpt_imbal_defaults` | 64.202 (64.257 / 64.146) |
63.958 (63.856 / 64.061) | -0.38 (-0.62 / -0.13) | 1.004 |
| `glm52_ep4_bf16_full_ragged_defaults` | 16.888 (16.868 / 16.908) |
16.819 (16.790 / 16.849) | -0.41 (-0.46 / -0.35) | 1.004 |
| `glm52_ep4_bf16_ckpt_ragged_defaults` | 20.453 (20.450 / 20.455) |
20.399 (20.409 / 20.389) | -0.26 (-0.20 / -0.32) | 1.003 |
| `glm52_ep4_bf16_full_raggedimbal_defaults` | 32.003 (32.015 / 31.991)
| 31.961 (32.005 / 31.918) | -0.13 (-0.03 / -0.23) | 1.001 |
| `glm52_ep4_bf16_ckpt_raggedimbal_defaults` | 39.408 (39.675 / 39.141)
| 39.238 (39.092 / 39.385) | -0.42 (-1.47 / +0.62) | 1.004 |
| `glm52_ep4_bf16_full_skew2_defaults` | 54.919 (54.907 / 54.932) |
54.933 (54.982 / 54.884) | +0.02 (+0.14 / -0.09) | 1.000 |
| `glm52_ep4_bf16_full_skew4_defaults` | 82.432 (82.354 / 82.510) |
82.448 (82.594 / 82.301) | +0.02 (+0.29 / -0.25) | 1.000 |
| `glm52_ep4_bf16_full_skew8_defaults` | 91.564 (91.647 / 91.480) |
91.530 (91.432 / 91.628) | -0.04 (-0.24 / +0.16) | 1.000 |
| `glm52_ep4_mxfp8_full_defaults` | 17.876 (17.850 / 17.902) | 17.775
(17.760 / 17.790) | -0.56 (-0.51 / -0.62) | 1.006 |
| `glm52_ep4_mxfp8_ckpt_defaults` | 21.922 (21.927 / 21.918) | 21.816
(21.811 / 21.821) | -0.49 (-0.53 / -0.44) | 1.005 |
| `glm52_ep4_mxfp8_full_cap2_defaults` | 17.999 (17.986 / 18.012) |
17.899 (17.921 / 17.876) | -0.56 (-0.36 / -0.75) | 1.006 |
| `glm52_ep4_mxfp8_full_mb393216_defaults` | 17.875 (17.880 / 17.870) |
17.767 (17.747 / 17.787) | -0.60 (-0.74 / -0.46) | 1.006 |
| `glm52_ep4_mxfp8_ckpt_mb393216_defaults` | 21.914 (21.939 / 21.888) |
21.775 (21.789 / 21.760) | -0.64 (-0.69 / -0.59) | 1.006 |
| `glm52_ep4_mxfp8_full_imbal_defaults` | 38.565 (38.593 / 38.537) |
38.669 (38.646 / 38.692) | +0.27 (+0.14 / +0.40) | 0.997 |
| `glm52_ep4_mxfp8_ckpt_imbal_defaults` | 45.389 (45.318 / 45.461) |
45.346 (45.340 / 45.353) | -0.09 (+0.05 / -0.24) | 1.001 |
| `glm52_ep4_mxfp8_full_ragged_defaults` | 13.091 (13.127 / 13.056) |
12.917 (12.900 / 12.934) | -1.33 (-1.73 / -0.93) | 1.013 |
| `glm52_ep4_mxfp8_ckpt_ragged_defaults` | 15.805 (15.801 / 15.810) |
15.652 (15.652 / 15.653) | -0.97 (-0.94 / -0.99) | 1.010 |
| `glm52_ep4_mxfp8_full_raggedimbal_defaults` | 23.022 (23.010 / 23.034)
| 22.841 (22.846 / 22.835) | -0.79 (-0.71 / -0.86) | 1.008 |
| `glm52_ep4_mxfp8_ckpt_raggedimbal_defaults` | 28.128 (28.127 / 28.130)
| 28.005 (28.024 / 27.986) | -0.44 (-0.37 / -0.51) | 1.004 |
| `glm52_ep4_mxfp8_full_skew2_defaults` | 38.905 (38.901 / 38.909) |
38.745 (38.846 / 38.644) | -0.41 (-0.14 / -0.68) | 1.004 |
| `glm52_ep4_mxfp8_full_skew4_defaults` | 57.609 (57.676 / 57.543) |
57.432 (57.286 / 57.578) | -0.31 (-0.68 / +0.06) | 1.003 |
| `glm52_ep4_mxfp8_full_skew8_defaults` | 63.859 (63.850 / 63.869) |
63.713 (63.751 / 63.674) | -0.23 (-0.16 / -0.30) | 1.002 |

**GB300 (sm_103a), EP8: 8 GPUs on 2 nodes; CUDA 13.4 (nvcc `Build
cuda_13.4.r13.4/compiler.38855100_0`), driver 580.159.03, torch
2.14.1+cu130 cuda 13.0 py 3.12.15, container image
devel:cuda13.4-20261005.**

| shape | A ms (r1 / r2) | B ms (r1 / r2) | Δ % (r1 / r2) | speedup A/B
|
|---|---|---|---|---|
| `glm52_ep8_bf16_ckpt_defaults` | 29.649 (29.616 / 29.683) | 29.498
(29.445 / 29.550) | -0.51 (-0.58 / -0.45) | 1.005 |
| `glm52_ep8_bf16_full_defaults` | 24.209 (24.181 / 24.238) | 24.172
(24.172 / 24.171) | -0.16 (-0.03 / -0.28) | 1.002 |
| `glm52_ep8_bf16_full_imbal_defaults` | 69.501 (69.889 / 69.114) |
69.533 (69.385 / 69.682) | +0.05 (-0.72 / +0.82) | 1.000 |
| `glm52_ep8_bf16_full_skew4_defaults` | 137.561 (137.506 / 137.616) |
137.538 (137.616 / 137.461) | -0.02 (+0.08 / -0.11) | 1.000 |
| `glm52_ep8_bf16_full_skew8_defaults` | 183.450 (183.423 / 183.477) |
183.200 (183.450 / 182.950) | -0.14 (+0.01 / -0.29) | 1.001 |
| `glm52_ep8_mxfp8_ckpt_defaults` | 21.654 (21.655 / 21.653) | 21.511
(21.523 / 21.498) | -0.66 (-0.61 / -0.71) | 1.007 |
| `glm52_ep8_mxfp8_full_defaults` | 17.698 (17.701 / 17.695) | 17.603
(17.613 / 17.594) | -0.54 (-0.50 / -0.57) | 1.005 |
| `glm52_ep8_mxfp8_full_imbal_defaults` | 48.380 (48.393 / 48.366) |
48.254 (48.295 / 48.213) | -0.26 (-0.20 / -0.32) | 1.003 |
| `glm52_ep8_mxfp8_full_skew4_defaults` | 94.317 (94.471 / 94.164) |
93.843 (93.974 / 93.711) | -0.50 (-0.53 / -0.48) | 1.005 |
| `glm52_ep8_mxfp8_full_skew8_defaults` | 125.088 (124.976 / 125.199) |
125.005 (124.799 / 125.211) | -0.07 (-0.14 / +0.01) | 1.001 |

Every data type, SwiGLU form, weight-gradient form and pass ships on
sm_100a, sm_103a and sm_107a; the table does not measure sm_107a.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [882d4a6](https://github.com/flashinfer-ai/flashinfer/commit/882d4a6d65e29c71c73ad58224acfe9c8f8d3116)

- **作者**: eigen
- **时间**: 2026-10-25T18:55:35Z
- **提交信息**: perf(cake_selective_state_update): faster programs for every variant on sm_100a and sm_103a (#7319)

`flashinfer.mamba.selective_state_update(..., backend="cake")` runs the
Mamba2 selective-state-update decode step for Nemotron-H and
Granite-4.0-H models, under both the SGLang and the canonical calling
conventions. The kernel's variants are defined by these dimensions: SSM
state dtype (BF16 or FP32), input convention (canonical FP32 dt / D /
dt_bias with an int64 state-slot index, or raw SGLang BF16 dt / D /
dt_bias with an int32 slot index and padded fused-projection rows), head
dim 64 or 128 (state dim 128), single-token decode or multi-token
(speculative) decode with an intermediate-state cache or a
destination-slot table, and an optional fused z gate and dt softplus.
This PR adds new generated programs and routing for every one of these
variants on sm_100a (B200) and sm_103a (GB300). Compared with the
previous Cake version (`backend="cake"` on main), all 122 shapes in the
shape list run faster on both GPUs. The speedup is 1.015x to 1.253x on
B200 and 1.018x to 1.248x on GB300.

*NVIDIA B200 (sm_100a, 148 SMs); CUDA 13.0 runtime (PyTorch
2.14.1+cu130); programs compiled with nvcc 13.4. Timer: CUPTI kernel
time with a cold L2; times are medians over 2 runs x 9 interleaved
rounds (us); speedup = previous Cake / this PR.*

| case | batch | tokens | heads | groups | head dim | state dim | state
| inputs | options | Cake (us) | this PR (us) | speedup |
|---|---:|---:|---:|---:|---:|---:|---|---|---|---:|---:|---:|
| sample_stp_bf16 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 44.560 | 39.440 | 1.130x |
| sample_stp_state_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32
dt/D, int64 index | - | 81.264 | 77.320 | 1.051x |
| sample_stp_z | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | z gate | 44.624 | 41.864 | 1.066x |
| sample_stp_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | softplus | 44.608 | 39.488 | 1.130x |
| sample_stp_z_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | z gate, softplus | 44.736 | 41.936 | 1.067x |
| sample_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 8.768 | 8.240 | 1.064x |
| sample_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 44.528 | 39.376 | 1.131x |
| sample_stp_b256 | 256 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 175.056 | 156.624 | 1.118x |
| sample_stp_b128 | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 86.112 | 78.880 | 1.092x |
| sample_mtp1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 41.336 | 40.304 | 1.026x |
| sample_mtp2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 46.856 | 44.864 | 1.044x |
| sweep_bfloat16_vertical_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | softplus, state cache, no state write,
algorithm=vertical | 4.064 | 3.744 | 1.085x |
| sweep_bfloat16_horizontal_b1024 | 1024 | 6 | 64 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus, state cache, no state write,
algorithm=horizontal | 1333.614 | 1223.927 | 1.090x |
| dynamic_dump_b1_t1_prev0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.976 |
2.816 | 1.057x |
| dynamic_dump_b1_t2_prev1 | 1 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.232 |
3.024 | 1.069x |
| dynamic_dump_b1_t4_prev2 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.520 |
3.200 | 1.100x |
| dynamic_dump_b1_t8_prev4 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 4.529 |
3.840 | 1.179x |
| dynamic_dump_b1_t8_prev8 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 4.592 |
3.840 | 1.196x |
| granite_ngram_t6_c4_legacy_adapted_graph_b1 | 1 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 4.064 | 3.744 | 1.085x |
| granite_ngram_t6_c4_legacy_adapted_graph_b2 | 2 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 4.992 | 4.736 | 1.054x |
| granite_ngram_t6_c4_legacy_adapted_graph_b3 | 3 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.304 | 5.952 | 1.059x |
| granite_ngram_t6_c4_legacy_adapted_graph_b4 | 4 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 7.048 | 6.680 | 1.055x |
| granite_ngram_t6_c4_sglang_raw_b1 | 1 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 4.064 |
3.968 | 1.024x |
| granite_ngram_t6_c4_sglang_raw_b2 | 2 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 5.088 |
4.992 | 1.019x |
| granite_ngram_t6_c4_sglang_raw_b3 | 3 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.400 |
6.176 | 1.036x |
| granite_ngram_t6_c4_sglang_raw_b4 | 4 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 7.264 |
6.992 | 1.039x |
| fitest_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 8.768 | 8.248 | 1.063x |
| fitest_stp_ratio8 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 44.640 | 39.392 | 1.133x |
| fitest_stp_ratio8_sat | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 86.104 | 78.880 | 1.092x |
| fitest_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 44.256 | 39.280 | 1.127x |
| fitest_stp_persistent | 257 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 358.048 | 313.880 | 1.141x |
| fitest_stp_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32 dt/D,
int64 index | - | 81.944 | 77.296 | 1.060x |
| fitest_mtp_short1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 41.216 | 40.256 | 1.024x |
| fitest_mtp_short2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 46.840 | 44.880 | 1.044x |
| fitest_mtp_cache | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D, int64
index | softplus, state cache, no state write, algorithm=vertical |
4.096 | 3.744 | 1.094x |
| fitest_mtp_horizontal | 32 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write,
algorithm=horizontal | 41.952 | 39.224 | 1.070x |
| fitest_dynamic0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 2.976 | 2.816 | 1.057x |
| fitest_dynamic0_b8 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | softplus, dst slots, algorithm=simple | 4.256 | 4.144 |
1.027x |
| fitest_dynamic1 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.520 | 3.200 | 1.100x |
| fitest_dynamic3 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 4.544 | 3.840 | 1.183x |
| fitest_dynamic7 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 4.584 | 3.840 | 1.194x |
| sweep_bfloat16_auto_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write | 4.096 | 3.744 |
1.094x |
| dynamic_dump_b8_t2_prev1 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 4.256 |
4.160 | 1.023x |
| nemotron_h_tp1_hd64_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.800 | 3.072 | 1.237x |
| nemotron_h_tp1_hd64_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.712 | 3.104 | 1.196x |
| nemotron_h_tp1_hd64_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.432 | 3.680 | 1.204x |
| nemotron_h_tp1_hd64_canonical_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 4.480 | 3.648 | 1.228x |
| nemotron_h_tp1_hd64_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 5.696 | 5.344 | 1.066x |
| nemotron_h_tp1_hd64_canonical_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 5.776 | 5.264 | 1.097x |
| nemotron_h_tp1_hd64_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 8.304 | 7.184 | 1.156x |
| nemotron_h_tp1_hd64_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 8.384 | 7.168 | 1.170x |
| nemotron_h_tp1_hd64_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 12.399 | 11.584 | 1.070x |
| nemotron_h_tp1_hd64_canonical_b16 | 16 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 12.256 | 11.568 | 1.059x |
| nemotron_h_tp1_hd64_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 21.480 | 20.512 | 1.047x |
| nemotron_h_tp1_hd64_canonical_b32 | 32 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 21.072 | 20.433 | 1.031x |
| nemotron_h_tp1_hd64_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 42.664 | 39.536 | 1.079x |
| nemotron_h_tp1_hd64_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 42.608 | 39.456 | 1.080x |
| nemotron_h_tp1_hd64_sglang_raw_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 82.992 | 79.208 | 1.048x |
| nemotron_h_tp1_hd64_canonical_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 82.336 | 79.168 | 1.040x |
| nemotron_h_tp1_hd64_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 163.792 | 157.064 | 1.043x |
| nemotron_h_tp1_hd64_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 163.104 | 157.096 | 1.038x |
| nemotron_h_tp1_hd64_sglang_raw_b6 | 6 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.944 | 6.465 | 1.074x |
| nemotron_h_tp1_hd64_sglang_raw_b12 | 12 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 10.160 | 9.528 | 1.066x |
| nemotron_h_tp1_hd64_sglang_raw_b20 | 20 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 16.192 | 14.288 | 1.133x |
| nemotron_h_tp1_hd64_sglang_raw_b24 | 24 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 16.832 | 15.232 | 1.105x |
| nemotron_h_tp1_hd64_sglang_raw_b48 | 48 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 32.112 | 29.864 | 1.075x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 3.776 | 3.616 | 1.044x |
| nemotron_h_tp1_hd64_fp32_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 3.912 | 3.520 | 1.111x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 11.104 | 10.816 | 1.027x |
| nemotron_h_tp1_hd64_fp32_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 11.008 | 10.840 | 1.015x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 77.976 | 75.799 | 1.029x |
| nemotron_h_tp1_hd64_fp32_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 77.832 | 76.000 | 1.024x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 |
128 | FP32 | BF16 dt/D, int32 index | softplus | 312.120 | 306.696 |
1.018x |
| nemotron_h_tp1_hd64_fp32_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128
| FP32 | FP32 dt/D, int64 index | softplus | 312.144 | 306.192 | 1.019x
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 5.072 | 4.712 | 1.076x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 7.680 | 6.800 | 1.129x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 18.672 | 18.368 | 1.017x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 38.312 | 37.408 | 1.024x |
| nemotron_h_tp2_hd64_sglang_raw_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.296 | 2.944 | 1.120x |
| nemotron_h_tp2_hd64_canonical_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.296 | 2.912 | 1.132x |
| nemotron_h_tp2_hd64_sglang_raw_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 21.248 | 20.464 | 1.038x |
| nemotron_h_tp2_hd64_canonical_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 21.080 | 20.368 | 1.035x |
| nemotron_h_tp2_hd64_sglang_raw_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 82.912 | 79.136 | 1.048x |
| nemotron_h_tp2_hd64_canonical_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 82.400 | 78.992 | 1.043x |
| nemotron_h_tp2_hd64_sglang_raw_b2 | 2 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.680 | 3.136 | 1.173x |
| nemotron_h_tp2_hd64_sglang_raw_b4 | 4 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 4.448 | 3.648 | 1.219x |
| nemotron_h_tp2_hd64_sglang_raw_b8 | 8 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 5.728 | 5.344 | 1.072x |
| nemotron_h_tp2_hd64_sglang_raw_b16 | 16 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 8.288 | 7.200 | 1.151x |
| nemotron_h_tp2_hd64_sglang_raw_b32 | 32 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 12.368 | 11.568 | 1.069x |
| nemotron_h_tp2_hd64_sglang_raw_b128 | 128 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 42.760 | 39.536 | 1.082x |
| nemotron_h_tp4_hd64_sglang_raw_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.064 | 2.656 | 1.154x |
| nemotron_h_tp4_hd64_canonical_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.136 | 2.825 | 1.110x |
| nemotron_h_tp4_hd64_sglang_raw_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 12.432 | 11.568 | 1.075x |
| nemotron_h_tp4_hd64_canonical_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 12.400 | 11.600 | 1.069x |
| nemotron_h_tp4_hd64_sglang_raw_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 42.600 | 39.520 | 1.078x |
| nemotron_h_tp4_hd64_canonical_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 42.592 | 39.504 | 1.078x |
| nemotron_h_tp4_hd64_sglang_raw_b4 | 4 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.647 | 3.120 | 1.169x |
| nemotron_h_tp4_hd64_sglang_raw_b8 | 8 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 4.448 | 3.616 | 1.230x |
| nemotron_h_tp4_hd64_sglang_raw_b16 | 16 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 5.728 | 5.312 | 1.078x |
| nemotron_h_tp4_hd64_sglang_raw_b32 | 32 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 8.256 | 7.200 | 1.147x |
| nemotron_h_tp4_hd64_sglang_raw_b128 | 128 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 21.392 | 20.432 | 1.047x |
| granite_h_small_hd64_sglang_raw_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.808 | 3.040 | 1.253x |
| granite_h_small_hd64_canonical_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 3.680 | 3.136 | 1.173x |
| granite_h_small_hd64_sglang_raw_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 8.032 | 7.120 | 1.128x |
| granite_h_small_hd64_canonical_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 8.008 | 7.136 | 1.122x |
| granite_h_small_hd64_sglang_raw_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 40.816 | 39.488 | 1.034x |
| granite_h_small_hd64_canonical_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 41.001 | 39.392 | 1.041x |
| granite_h_small_hd64_sglang_raw_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 160.688 | 156.912 | 1.024x |
| granite_h_small_hd64_canonical_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 160.744 | 156.952 | 1.024x |
| granite_h_tiny_hd64_sglang_raw_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.224 | 2.816 | 1.145x |
| granite_h_tiny_hd64_canonical_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.240 | 2.840 | 1.141x |
| granite_h_tiny_hd64_sglang_raw_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 16.808 | 15.208 | 1.105x |
| granite_h_tiny_hd64_canonical_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 16.952 | 15.216 | 1.114x |
| fitest_stp_hd64_rows_bf16 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 5.760 | 5.248 | 1.098x |
| fitest_stp_hd64_paired_rows | 64 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | - | 42.520 | 39.408 | 1.079x |
| fitest_stp_hd64_paired_rows_b320 | 320 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | - | 203.352 | 196.192 | 1.036x |
| fitest_stp_hd64_fp32 | 64 | 1 | 128 | 8 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | - | 77.704 | 75.776 | 1.025x |
| fitest_stp_hd64_odd_pairs | 8 | 1 | 24 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 4.000 | 3.488 | 1.147x |
| fitest_stp_hd64_raw_rows | 2 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 4.424 | 3.672 | 1.205x |
| fitest_stp_hd64_raw_paired | 64 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 42.689 | 39.536 | 1.080x |
| fitest_stp_hd64_raw_fp32 | 8 | 1 | 128 | 8 | 64 | 128 | FP32 | BF16
dt/D, int32 index | softplus | 11.168 | 10.848 | 1.029x |
| fitest_stp_hd64_raw_paired_four_cta | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 12.440 | 11.568 | 1.075x |

*NVIDIA GB300 (sm_103a, 152 SMs); CUDA 13.0 runtime (PyTorch
2.14.1+cu130); programs compiled with nvcc 13.4. Timer: CUPTI kernel
time with a cold L2; times are medians over 2 runs x 9 interleaved
rounds (us); speedup = previous Cake / this PR.*

| case | batch | tokens | heads | groups | head dim | state dim | state
| inputs | options | Cake (us) | this PR (us) | speedup |
|---|---:|---:|---:|---:|---:|---:|---|---|---|---:|---:|---:|
| sample_stp_bf16 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 47.048 | 37.760 | 1.246x |
| sample_stp_state_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32
dt/D, int64 index | - | 76.696 | 74.792 | 1.025x |
| sample_stp_z | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | z gate | 47.432 | 39.816 | 1.191x |
| sample_stp_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | softplus | 47.168 | 37.792 | 1.248x |
| sample_stp_z_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | z gate, softplus | 47.480 | 39.856 | 1.191x |
| sample_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 9.544 | 8.064 | 1.184x |
| sample_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 45.736 | 37.704 | 1.213x |
| sample_stp_b256 | 256 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 159.712 | 151.408 | 1.055x |
| sample_stp_b128 | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 83.176 | 75.904 | 1.096x |
| sample_mtp1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 39.672 | 38.288 | 1.036x |
| sample_mtp2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 44.384 | 42.240 | 1.051x |
| sweep_bfloat16_vertical_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | softplus, state cache, no state write,
algorithm=vertical | 3.872 | 3.552 | 1.090x |
| sweep_bfloat16_horizontal_b1024 | 1024 | 6 | 64 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus, state cache, no state write,
algorithm=horizontal | 1175.080 | 1100.512 | 1.068x |
| dynamic_dump_b1_t1_prev0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.880 |
2.664 | 1.081x |
| dynamic_dump_b1_t2_prev1 | 1 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.072 |
2.880 | 1.067x |
| dynamic_dump_b1_t4_prev2 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.424 |
3.072 | 1.115x |
| dynamic_dump_b1_t8_prev4 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 4.320 |
3.616 | 1.195x |
| dynamic_dump_b1_t8_prev8 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 4.416 |
3.648 | 1.211x |
| granite_ngram_t6_c4_legacy_adapted_graph_b1 | 1 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 3.872 | 3.576 | 1.083x |
| granite_ngram_t6_c4_legacy_adapted_graph_b2 | 2 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 4.768 | 4.480 | 1.064x |
| granite_ngram_t6_c4_legacy_adapted_graph_b3 | 3 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 5.792 | 5.504 | 1.052x |
| granite_ngram_t6_c4_legacy_adapted_graph_b4 | 4 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.720 | 6.368 | 1.055x |
| granite_ngram_t6_c4_sglang_raw_b1 | 1 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 3.904 |
3.792 | 1.030x |
| granite_ngram_t6_c4_sglang_raw_b2 | 2 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 4.896 |
4.800 | 1.020x |
| granite_ngram_t6_c4_sglang_raw_b3 | 3 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 5.824 |
5.600 | 1.040x |
| granite_ngram_t6_c4_sglang_raw_b4 | 4 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.864 |
6.624 | 1.036x |
| fitest_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 9.568 | 8.064 | 1.187x |
| fitest_stp_ratio8 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 47.096 | 37.768 | 1.247x |
| fitest_stp_ratio8_sat | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 83.144 | 75.872 | 1.096x |
| fitest_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 45.216 | 37.480 | 1.206x |
| fitest_stp_persistent | 257 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 331.192 | 303.976 | 1.090x |
| fitest_stp_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32 dt/D,
int64 index | - | 76.976 | 74.832 | 1.029x |
| fitest_mtp_short1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 39.624 | 38.448 | 1.031x |
| fitest_mtp_short2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 44.399 | 42.272 | 1.050x |
| fitest_mtp_cache | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D, int64
index | softplus, state cache, no state write, algorithm=vertical |
3.872 | 3.584 | 1.080x |
| fitest_mtp_horizontal | 32 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write,
algorithm=horizontal | 39.752 | 36.736 | 1.082x |
| fitest_dynamic0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 2.880 | 2.664 | 1.081x |
| fitest_dynamic0_b8 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | softplus, dst slots, algorithm=simple | 4.064 | 3.840 |
1.058x |
| fitest_dynamic1 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.424 | 3.072 | 1.115x |
| fitest_dynamic3 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 4.304 | 3.632 | 1.185x |
| fitest_dynamic7 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 4.368 | 3.648 | 1.197x |
| sweep_bfloat16_auto_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write | 3.872 | 3.584 |
1.080x |
| dynamic_dump_b8_t2_prev1 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 4.064 |
3.840 | 1.058x |
| nemotron_h_tp1_hd64_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.616 | 3.008 | 1.202x |
| nemotron_h_tp1_hd64_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.568 | 3.040 | 1.174x |
| nemotron_h_tp1_hd64_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.256 | 3.520 | 1.209x |
| nemotron_h_tp1_hd64_canonical_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 4.304 | 3.520 | 1.223x |
| nemotron_h_tp1_hd64_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 5.472 | 5.152 | 1.062x |
| nemotron_h_tp1_hd64_canonical_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 5.560 | 5.024 | 1.107x |
| nemotron_h_tp1_hd64_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.840 | 6.896 | 1.137x |
| nemotron_h_tp1_hd64_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 7.888 | 6.848 | 1.152x |
| nemotron_h_tp1_hd64_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 12.480 | 10.896 | 1.145x |
| nemotron_h_tp1_hd64_canonical_b16 | 16 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 12.512 | 10.896 | 1.148x |
| nemotron_h_tp1_hd64_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 20.640 | 19.464 | 1.060x |
| nemotron_h_tp1_hd64_canonical_b32 | 32 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 20.880 | 19.496 | 1.071x |
| nemotron_h_tp1_hd64_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 40.672 | 37.784 | 1.076x |
| nemotron_h_tp1_hd64_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 40.480 | 37.808 | 1.071x |
| nemotron_h_tp1_hd64_sglang_raw_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 79.312 | 75.840 | 1.046x |
| nemotron_h_tp1_hd64_canonical_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 78.864 | 76.160 | 1.036x |
| nemotron_h_tp1_hd64_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 156.784 | 151.696 | 1.034x |
| nemotron_h_tp1_hd64_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 156.704 | 151.960 | 1.031x |
| nemotron_h_tp1_hd64_sglang_raw_b6 | 6 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.592 | 6.272 | 1.051x |
| nemotron_h_tp1_hd64_sglang_raw_b12 | 12 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 9.632 | 9.040 | 1.065x |
| nemotron_h_tp1_hd64_sglang_raw_b20 | 20 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 14.840 | 14.576 | 1.018x |
| nemotron_h_tp1_hd64_sglang_raw_b24 | 24 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 15.312 | 14.528 | 1.054x |
| nemotron_h_tp1_hd64_sglang_raw_b48 | 48 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 30.256 | 28.480 | 1.062x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 3.648 | 3.552 | 1.027x |
| nemotron_h_tp1_hd64_fp32_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 3.776 | 3.296 | 1.146x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 11.120 | 10.336 | 1.076x |
| nemotron_h_tp1_hd64_fp32_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 10.880 | 10.296 | 1.057x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 76.696 | 73.472 | 1.044x |
| nemotron_h_tp1_hd64_fp32_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 76.208 | 73.640 | 1.035x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 |
128 | FP32 | BF16 dt/D, int32 index | softplus | 306.656 | 299.856 |
1.023x |
| nemotron_h_tp1_hd64_fp32_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128
| FP32 | FP32 dt/D, int64 index | softplus | 306.784 | 299.656 | 1.024x
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 4.992 | 4.464 | 1.118x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 7.328 | 6.576 | 1.114x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 17.856 | 17.344 | 1.030x |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 37.424 | 35.536 | 1.053x |
| nemotron_h_tp2_hd64_sglang_raw_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.168 | 2.784 | 1.138x |
| nemotron_h_tp2_hd64_canonical_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.200 | 2.720 | 1.176x |
| nemotron_h_tp2_hd64_sglang_raw_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 20.640 | 19.423 | 1.063x |
| nemotron_h_tp2_hd64_canonical_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 21.032 | 19.392 | 1.085x |
| nemotron_h_tp2_hd64_sglang_raw_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 79.280 | 75.872 | 1.045x |
| nemotron_h_tp2_hd64_canonical_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 79.256 | 75.872 | 1.045x |
| nemotron_h_tp2_hd64_sglang_raw_b2 | 2 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.584 | 3.040 | 1.179x |
| nemotron_h_tp2_hd64_sglang_raw_b4 | 4 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 4.320 | 3.488 | 1.239x |
| nemotron_h_tp2_hd64_sglang_raw_b8 | 8 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 5.472 | 5.136 | 1.065x |
| nemotron_h_tp2_hd64_sglang_raw_b16 | 16 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.784 | 6.896 | 1.129x |
| nemotron_h_tp2_hd64_sglang_raw_b32 | 32 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 12.576 | 10.848 | 1.159x |
| nemotron_h_tp2_hd64_sglang_raw_b128 | 128 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 40.592 | 37.744 | 1.075x |
| nemotron_h_tp4_hd64_sglang_raw_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.976 | 2.528 | 1.177x |
| nemotron_h_tp4_hd64_canonical_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.976 | 2.560 | 1.162x |
| nemotron_h_tp4_hd64_sglang_raw_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 12.576 | 10.880 | 1.156x |
| nemotron_h_tp4_hd64_canonical_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 12.544 | 10.912 | 1.150x |
| nemotron_h_tp4_hd64_sglang_raw_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 40.584 | 37.720 | 1.076x |
| nemotron_h_tp4_hd64_canonical_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 40.336 | 38.024 | 1.061x |
| nemotron_h_tp4_hd64_sglang_raw_b4 | 4 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.488 | 3.040 | 1.147x |
| nemotron_h_tp4_hd64_sglang_raw_b8 | 8 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 4.352 | 3.680 | 1.183x |
| nemotron_h_tp4_hd64_sglang_raw_b16 | 16 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 5.504 | 4.944 | 1.113x |
| nemotron_h_tp4_hd64_sglang_raw_b32 | 32 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.824 | 6.912 | 1.132x |
| nemotron_h_tp4_hd64_sglang_raw_b128 | 128 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 20.752 | 19.352 | 1.072x |
| granite_h_small_hd64_sglang_raw_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.648 | 2.976 | 1.226x |
| granite_h_small_hd64_canonical_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 3.552 | 3.120 | 1.138x |
| granite_h_small_hd64_sglang_raw_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.552 | 6.848 | 1.103x |
| granite_h_small_hd64_canonical_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 7.648 | 6.848 | 1.117x |
| granite_h_small_hd64_sglang_raw_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.328 | 37.744 | 1.042x |
| granite_h_small_hd64_canonical_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 39.279 | 37.760 | 1.040x |
| granite_h_small_hd64_sglang_raw_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 154.576 | 151.544 | 1.020x |
| granite_h_small_hd64_canonical_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 154.712 | 151.696 | 1.020x |
| granite_h_tiny_hd64_sglang_raw_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.104 | 2.608 | 1.190x |
| granite_h_tiny_hd64_canonical_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.104 | 2.688 | 1.155x |
| granite_h_tiny_hd64_sglang_raw_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 15.240 | 14.464 | 1.054x |
| granite_h_tiny_hd64_canonical_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 15.376 | 14.416 | 1.067x |
| fitest_stp_hd64_rows_bf16 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 5.536 | 4.992 | 1.109x |
| fitest_stp_hd64_paired_rows | 64 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | - | 40.432 | 37.760 | 1.071x |
| fitest_stp_hd64_paired_rows_b320 | 320 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | - | 194.992 | 189.824 | 1.027x |
| fitest_stp_hd64_fp32 | 64 | 1 | 128 | 8 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | - | 76.128 | 73.544 | 1.035x |
| fitest_stp_hd64_odd_pairs | 8 | 1 | 24 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 3.840 | 3.296 | 1.165x |
| fitest_stp_hd64_raw_rows | 2 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 4.256 | 3.520 | 1.209x |
| fitest_stp_hd64_raw_paired | 64 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 40.688 | 37.760 | 1.078x |
| fitest_stp_hd64_raw_fp32 | 8 | 1 | 128 | 8 | 64 | 128 | FP32 | BF16
dt/D, int32 index | softplus | 10.864 | 10.320 | 1.053x |
| fitest_stp_hd64_raw_paired_four_cta | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 12.512 | 10.880 | 1.150x |

Cake has no variants of this kernel beyond the dimensions above, and it
ships the kernel only on sm_100a and sm_103a, both of which this PR
covers.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded GPU support for selective state updates across additional
input layouts, data types, index formats, and sequence lengths.
* Added support for optional output gating, timestep transforms, and
cached intermediate state in supported configurations.
* **Reliability**
* Improved validation of tensor formats, device placement, and launch
dimensions, with clearer errors for invalid inputs.
* **Tests**
* Broadened correctness and compatibility coverage, including graph
capture, padded inputs, architecture-specific builds, and fallback
behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [83755d9](https://github.com/flashinfer-ai/flashinfer/commit/83755d9093ba358ad005a4489c05f4cfbb0ff8e9)

- **作者**: eigen
- **时间**: 2026-10-25T18:22:08Z
- **提交信息**: feat(cake_qsa_nvfp4): the SM120 whole-tile decode, selected by the per-CTA tile stream (#7345)

This PR adds the SM120 build of the whole-tile decode to the Cake
backend of `flashinfer.sparse.qsa_sparse_paged_attention`. The kernel
computes gated sparse paged GQA decode attention of BF16 queries over an
NVFP4 paged KV cache, with Hq 24 / Hkv 2 / D 256, 2051 selected tokens
per row in 64-token tiles, page 16, and NHD and HND KV layouts. The
kernel has seven programs: the mma.sync K-first decode, its whole-tile
build, the mma.sync cooperative decode that merges its splits in the
launch (the fused form), the tcgen05 decode, the tcgen05 cooperative
decode, the tcgen05 persistent walk and the split-KV merge. A call takes
either the split form (decode + merge) or the fused form (cooperative
decode alone). This PR delivers the whole-tile decode for SM120 (compute
capability 12.0). It issues every copy of a 64-token tile before that
tile's compute, keeps two stages in flight and applies an L2 evict-first
policy to the copies. On SM120, the host now selects it for split-form
calls whose CTAs each walk at least 11 tiles (704 selected tokens). That
covers rows 32 / 64 / 128 at 3 / 2 / 1 splits. Shorter streams keep the
fused cooperative decode within the co-resident capacity, as before. The
baseline is the previous Cake version of the kernel on this device: the
fused cooperative decode within the co-resident capacity and the K-first
decode + merge beyond it. The baseline is timed in the same process with
the new program withheld, and both arms time the whole call including
the merge. Against that baseline, the whole call is 1.05x-1.06x faster
at rows 32 / 64 / 128 with eager launches and 1.05x-1.07x faster under
CUDA-graph replay. Rows 1-16 are the unchanged shapes where the host
rule does not select the new program, and they measure 0.99x-1.01x in
both tables.

Eager launches on an NVIDIA RTX PRO 6000 Blackwell Server Edition
(sm_120a) with CUDA 13.4, reporting medians of 3 x 64 samples with a
cold-L2 memset flush between samples, 24 x 2 heads and 2051 selected
tokens per row.

| layout | rows | previous route us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 12.24 | 12.21 | 1.00x |
| NHD | 2 | 16.88 | 17.06 | 0.99x |
| NHD | 4 | 15.84 | 16.02 | 0.99x |
| NHD | 8 | 22.80 | 22.56 | 1.01x |
| NHD | 16 | 35.23 | 34.94 | 1.01x |
| NHD | 32 | 57.25 | 54.74 | 1.05x |
| NHD | 64 | 98.86 | 94.26 | 1.05x |
| NHD | 128 | 161.65 | 152.80 | 1.06x |
| HND | 1 | 12.48 | 12.51 | 1.00x |
| HND | 2 | 17.38 | 17.60 | 0.99x |
| HND | 4 | 15.84 | 15.74 | 1.01x |
| HND | 8 | 23.20 | 23.20 | 1.00x |
| HND | 16 | 35.95 | 35.90 | 1.00x |
| HND | 32 | 59.89 | 56.64 | 1.06x |
| HND | 64 | 102.21 | 97.42 | 1.05x |
| HND | 128 | 168.11 | 158.50 | 1.06x |

CUDA-graph replay of each arm's whole call on the same NVIDIA RTX PRO
6000 Blackwell Server Edition (sm_120a) with CUDA 13.4, reporting
medians of 3 x 64 samples with a cold-L2 memset flush between samples,
24 x 2 heads and 2051 selected tokens per row.

| layout | rows | previous route us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 12.99 | 13.07 | 0.99x |
| NHD | 2 | 18.54 | 18.61 | 1.00x |
| NHD | 4 | 17.73 | 17.55 | 1.01x |
| NHD | 8 | 24.19 | 24.19 | 1.00x |
| NHD | 16 | 36.19 | 36.26 | 1.00x |
| NHD | 32 | 57.90 | 55.06 | 1.05x |
| NHD | 64 | 100.35 | 93.86 | 1.07x |
| NHD | 128 | 159.76 | 152.14 | 1.05x |
| HND | 1 | 13.90 | 13.89 | 1.00x |
| HND | 2 | 18.93 | 19.02 | 0.99x |
| HND | 4 | 17.47 | 17.38 | 1.01x |
| HND | 8 | 24.53 | 24.62 | 1.00x |
| HND | 16 | 37.15 | 37.23 | 1.00x |
| HND | 32 | 61.07 | 57.79 | 1.06x |
| HND | 64 | 103.46 | 98.11 | 1.05x |
| HND | 128 | 168.67 | 160.40 | 1.05x |

The kernel's other Cake variants are the tcgen05 plain and cooperative
decodes (SM100 / SM103 / SM107), the SM103 persistent walk and the SM80
whole-tile build, and the family ships for sm_80, sm_90a, sm_100a,
sm_103a, sm_107a and sm_120a; the fused form runs on 9.0 and 12.0 within
the device's co-resident capacity (on 12.0 except on a long-stream call)
and on 10.0 / 10.3 on aarch64 hosts at rows <= 4 outside a stream
capture, while 10.7 keeps the split form.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added architecture-specific NVFP4 QSA decode support for newer NVIDIA
GPUs, including RTX PRO 6000-class hardware.
* Decode form and specialized kernel selection now adapt to GPU
architecture and workload size.
* **Improvements**
* Updated GPU-specific memory-copy behavior for NVFP4 decode workloads.
* **Documentation**
* Clarified architecture-specific selection thresholds and added RTX PRO
6000 examples and measurement results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0604b07](https://github.com/flashinfer-ai/flashinfer/commit/0604b07a46e1ac7620e652e2b152c833a5dffb22)

- **作者**: eigen
- **时间**: 2026-10-25T18:16:43Z
- **提交信息**: perf(cake_mxfp8_megamoe_ep16): route terms returned by relaxed system-scope stores, later FC1 prefetch, evict-first weights (#7323)

`flashinfer.experimental.cake_mxfp8_megamoe_ep16`
(`CakeMxfp8MegaMoeEp16`) runs expert-parallel MoE across 16 ranks. It
supports one data-type configuration: BF16 activations, MXFP8 expert
weights (E4M3 values with E8M0 scales per 32 elements) and BF16 output.
The shape is hidden 3072, intermediate 5120, 512 experts (32 per rank)
and top-8. Each forward runs two kernels: a fused kernel for dispatch,
FC1, SwiGLU, FC2 and return, followed by a top-k reduce kernel. The
module has two backends, CUDA and CuTe DSL. The CUDA backend's fused
kernel is compiled from one body in two token specializations, one for
16 and 64 tokens per rank and one for 32 tokens per rank, and both use
the same return path. Both are compiled for sm_100a and sm_103a. This PR
changes the CUDA backend's fused kernel, in both specializations on both
architectures, and its top-k reduce kernel with three changes. First,
the FC2 epilogue now stores each route term directly into the source
rank's route-term words with relaxed system-scope stores
(`st.relaxed.sys`). Before the publication barrier, each rank sets its
own route-term words to an all-ones sentinel. The top-k reduce kernel
waits until no word of a group holds the sentinel, reduces from those
values and re-arms the words. A BF16 pair word can never equal the
all-ones sentinel, so -0.0 and NaN terms stay exact. This removes the
end-of-kernel system-scope fence, the return grid counter and one NVLink
barrier phase. The second cross-rank barrier is split: its arrival moves
to the end of dispatch and its wait moves to the end of the kernel,
where it still guards buffer reuse by the next forward. Second, the L2
weight prefetch for the first FC1 work item
(`cp.async.bulk.prefetch.tensor`) is now issued after the publication
grid barrier instead of before it, so it no longer delays publication.
Third, FC1 and FC2 weight TMA loads carry an L2 evict-first cache hint.
Outputs are bit-identical on all 16 ranks. End-to-end forward is 1.046x
to 1.051x faster than the previous Cake CUDA backend on main, which
already includes the previous round of this kernel. Every configuration
below is faster.

| Tokens per rank (global) | Routing | Previous Cake CUDA (us) | This PR
(us) | Speedup |
|---|---|---:|---:|---:|
| 16 (256) | balanced | 313.3 | 299.0 | 1.048x |
| 16 (256) | hotset50 | 313.3 | 299.1 | 1.047x |
| 32 (512) | balanced | 316.4 | 301.0 | 1.051x |
| 32 (512) | hotset50 | 315.9 | 300.9 | 1.050x |
| 64 (1024) | balanced | 317.4 | 303.1 | 1.047x |
| 64 (1024) | hotset50 | 318.0 | 303.9 | 1.046x |

*16x NVIDIA GB300 (sm_103a), 4 nodes x 4 GPUs in one NVL72 domain, CUDA
13.4; end-to-end eager forward (both kernels) with cold L2; per round,
the slowest rank's median over 100 iterations, averaged over two
sessions of each side; median of 48 interleaved rounds (4 independent
launches x 12 rounds); balanced = uniform top-8, hotset50 = 4 of the 8
slots drawn from the first 128 experts.*

This PR does not change the module's other Cake variant, its CuTe DSL
backend, and the whole family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved coordination of routing data across ranks during fused expert
execution. The forward pass now waits for required route terms before
consuming them, reducing the risk of using incomplete routing
information.
  * Synchronization covers all required route terms in the forward pass.
* Routing must remain consistent with the session’s immutable-routing
contract; violations may cause the forward pass to stall.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0cdbe67](https://github.com/flashinfer-ai/flashinfer/commit/0cdbe67b8c465e0686dd8ac1fa095e9341566d68)

- **作者**: eigen
- **时间**: 2026-10-25T17:55:46Z
- **提交信息**: perf(cake_nvfp4_mla_decode): faster SM100 / SM103 decode with a paced dequant transform and a shorter start chain (#7343)

`cake_nvfp4_mla_decode`
(`flashinfer.mla.prepare_nvfp4_batch_decode_with_kv_cache_mla`,
experimental) is the DeepSeek-V4 main-attention decode with NVFP4
queries and KV cache (E2M1 values with UE4M3 block-16 scales), one
512-wide latent row per token that serves as both K and V, 64-token
pages, an optional per-head attention sink, BF16 output and FP32 LSE;
its single variant runs a persistent decode program and a split-KV
combine program. This PR replaces that variant's decode program with a
faster build of the same kernel and leaves the combine program
unchanged. Measured against the previous Cake version in `main`, the
speedup is 1.012x to 1.056x on GB300 and 1.012x to 1.032x on B200, where
speedup is `main` latency divided by this PR's latency, each the median
of one complete call (decode, plus the combine when a request is split).

**NVIDIA GB300 (sm_103a), CUDA 13.4**

| Shape | `main` (µs) | This PR (µs) | Speedup |
|---|---:|---:|---:|
| 2 requests (256, 300 keys), 64 heads, 6 query tokens, forced 2-way
split | 12.32 | 12.10 | 1.019x |
| 3 requests (1000, 8192, 5000 keys), 8 heads, 6 query tokens | 25.70 |
25.39 | 1.012x |
| 4 requests (64, 65, 4096, 777 keys), 64 heads, 1 query token, no sink
| 32.64 | 32.00 | 1.020x |
| batch 32, 8K keys each, 64 heads, 6 query tokens | 84.00 | 82.88 |
1.014x |
| batch 32, 16K keys each, 64 heads, 6 query tokens | 147.65 | 144.62 |
1.021x |
| batch 32, 32K keys each, 64 heads, 6 query tokens | 275.59 | 270.18 |
1.020x |
| batch 32, 64K keys each, 64 heads, 6 query tokens | 550.83 | 532.61 |
1.034x |
| batch 32, 128K keys each, 64 heads, 6 query tokens | 1125.70 | 1066.37
| 1.056x |

**NVIDIA B200 (sm_100a), CUDA 13.4**

| Shape | `main` (µs) | This PR (µs) | Speedup |
|---|---:|---:|---:|
| 2 requests (256, 300 keys), 64 heads, 6 query tokens, forced 2-way
split | 12.83 | 12.58 | 1.020x |
| 3 requests (1000, 8192, 5000 keys), 8 heads, 6 query tokens | 27.31 |
26.78 | 1.020x |
| 4 requests (64, 65, 4096, 777 keys), 64 heads, 1 query token, no sink
| 37.06 | 35.90 | 1.032x |
| batch 32, 8K keys each, 64 heads, 6 query tokens | 97.49 | 96.37 |
1.012x |
| batch 32, 16K keys each, 64 heads, 6 query tokens | 177.02 | 173.89 |
1.018x |
| batch 32, 32K keys each, 64 heads, 6 query tokens | 393.89 | 387.17 |
1.017x |
| batch 32, 64K keys each, 64 heads, 6 query tokens | 789.41 | 775.68 |
1.018x |
| batch 32, 128K keys each, 64 heads, 6 query tokens | 1589.30 | 1560.10
| 1.019x |

Cake has no other variants of this decode (no other data type, layout or
fused form), and the kernel covers sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated NVFP4 MLA decoding behavior across supported GPU
architectures, including changes to data fetching and compute handling.
* The existing decoding workflow remains available, with no changes to
user-facing settings or interfaces. These updates are limited to
supported GPU configurations and do not change the documented minimum
CUDA versions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [31d0a81](https://github.com/flashinfer-ai/flashinfer/commit/31d0a811aebed9047ee60d27760d7872600ad93f)

- **作者**: eigen
- **时间**: 2026-10-25T17:29:45Z
- **提交信息**: perf(cake_muse_spark_norm): PDL route for rmsnorm_sigmoid_gate with per-window launch forms (#7341)

`rmsnorm_sigmoid_gate` computes a per-head RMSNorm of 64 BF16 values
times `sigmoid(gate)`, in place, on `(rows, 64)` or `(rows, heads, 64)`
inputs. It supports BF16 only and has one fused form. Cake ships two
variants of this kernel. `bf16` is the plain launch form and shipped
before this PR. `bf16_pdl` is added by this PR and is the
programmatic-dependent-launch form on SM100 and SM103. With
`enable_pdl=True`, `backend="auto"` now serves the call from `bf16_pdl`.
That route picks a launch form for each token-count window: a PDL build,
a late-signal PDL build, a borrowed plain build launched without the
attribute, or a declared gap. In a gap, `backend="auto"` keeps the
existing CuTe DSL kernel with PDL. This PR also gives the
`gated_residual_rmsnorm` PDL routes per-window launch forms on SM100 and
SM103. The baseline is the previous Cake version of these kernels: the
plain route, which the previous release launched without the PDL
attribute for every call, including `enable_pdl=True`. The tables also
list the CuTe DSL kernel launched with PDL, which is what the gap rows
run in this PR. Rows served by a borrowed plain build run the same
kernel as the baseline, launched without the attribute.

**`rmsnorm_sigmoid_gate` on NVIDIA B200 (sm_100a, 148 SMs), driver
580.82.07, kernels JIT-compiled with nvcc 13.4 (CUDA 13.4), torch
2.14.1+cu130.** Values are microseconds per launch from graph replay:
one CUDA graph of 32 launches replayed 20x, per-launch average, median
of 5 counterbalanced groups. Each cell gives two sessions as s1 / s2.
Speedup is previous Cake / this PR, so ratios > 1 mean this PR is
faster. In this PR, rows marked (gap) run the CuTe DSL kernel with PDL.

| shape (heads, tokens) | previous Cake us s1 / s2 | this PR us s1 / s2
| CuTe DSL kernel + PDL us s1 / s2 | speedup s1 / s2 |
|---|---|---|---|---|
| h128 T=1 (gap) | 1.184 / 1.185 | 0.929 / 0.927 | 0.929 / 0.929 | 1.274
/ 1.278 |
| h128 T=2 | 1.187 / 1.186 | 0.995 / 0.994 | 1.187 / 1.186 | 1.193 /
1.193 |
| h128 T=3 | 1.188 / 1.185 | 0.993 / 0.990 | 1.121 / 1.120 | 1.196 /
1.197 |
| h128 T=8 | 1.312 / 1.312 | 1.089 / 1.087 | 1.120 / 1.121 | 1.205 /
1.207 |
| h128 T=64 (gap) | 1.698 / 1.695 | 1.338 / 1.336 | 1.331 / 1.330 |
1.269 / 1.269 |
| h128 T=256 | 2.593 / 2.593 | 2.273 / 2.275 | 2.466 / 2.466 | 1.141 /
1.140 |
| h128 T=1024 | 5.730 / 5.731 | 5.674 / 5.673 | 7.326 / 7.326 | 1.010 /
1.010 |
| h128 T=4096 | 29.126 / 29.110 | 28.914 / 28.925 | 30.519 / 30.517 |
1.007 / 1.006 |
| h128 T=16384 | 113.988 / 113.972 | 113.898 / 113.895 | 118.527 /
118.509 | 1.001 / 1.001 |
| h32 T=1 (gap) | 1.248 / 1.249 | 0.866 / 0.867 | 0.866 / 0.866 | 1.441
/ 1.441 |
| h32 T=2 | 1.250 / 1.249 | 0.993 / 0.992 | 1.122 / 1.121 | 1.259 /
1.259 |
| h32 T=8 | 1.312 / 1.312 | 0.994 / 0.995 | 1.187 / 1.185 | 1.320 /
1.319 |
| h32 T=9 | 1.276 / 1.279 | 0.995 / 0.994 | 1.121 / 1.119 | 1.282 /
1.287 |
| h32 T=17 | 1.315 / 1.312 | 1.054 / 1.049 | 1.120 / 1.118 | 1.248 /
1.251 |
| h32 T=64 | 1.314 / 1.313 | 1.058 / 1.057 | 1.122 / 1.121 | 1.242 /
1.242 |
| h32 T=256 (gap) | 1.697 / 1.697 | 1.372 / 1.372 | 1.315 / 1.315 |
1.237 / 1.237 |
| h32 T=257 (gap) | 1.697 / 1.696 | 1.367 / 1.367 | 1.316 / 1.315 |
1.241 / 1.241 |
| h32 T=1024 | 2.595 / 2.593 | 2.305 / 2.303 | 2.470 / 2.468 | 1.126 /
1.126 |
| h32 T=4096 | 5.735 / 5.734 | 5.669 / 5.668 | 7.328 / 7.325 | 1.012 /
1.012 |
| h32 T=16384 | 29.086 / 29.083 | 28.920 / 28.909 | 30.631 / 30.624 |
1.006 / 1.006 |
| h16 T=1 (gap) | 1.183 / 1.185 | 0.909 / 0.907 | 0.867 / 0.865 | 1.301
/ 1.307 |
| h16 T=8 | 1.187 / 1.184 | 0.946 / 0.945 | 1.187 / 1.186 | 1.255 /
1.253 |
| h16 T=16 | 1.185 / 1.185 | 0.930 / 0.929 | 1.188 / 1.186 | 1.274 /
1.276 |
| h16 T=17 | 1.187 / 1.186 | 0.931 / 0.931 | 1.377 / 1.376 | 1.275 /
1.274 |
| h16 T=64 | 1.247 / 1.247 | 0.980 / 0.980 | 1.380 / 1.379 | 1.272 /
1.272 |
| h16 T=256 | 1.439 / 1.441 | 1.149 / 1.144 | 1.441 / 1.442 | 1.252 /
1.260 |
| h16 T=1024 | 1.953 / 1.953 | 1.762 / 1.760 | 2.079 / 2.080 | 1.108 /
1.110 |
| h16 T=4096 | 3.526 / 3.527 | 3.538 / 3.535 | 4.498 / 4.497 | 0.997 /
0.998 |
| h16 T=16384 | 10.044 / 10.046 | 10.074 / 10.072 | 14.352 / 14.357 |
0.997 / 0.997 |

**`gated_residual_rmsnorm` on NVIDIA B200 (sm_100a, 148 SMs), driver
580.82.07, kernels JIT-compiled with nvcc 13.4 (CUDA 13.4), torch
2.14.1+cu130: the shape-list rows whose launch under `enable_pdl=True`
changes in this PR.** Values are microseconds per launch from graph
replay: one CUDA graph of 32 launches replayed 20x, per-launch average,
median of 5 counterbalanced groups. Each cell gives two sessions as s1 /
s2. Speedup is previous Cake / this PR, so ratios > 1 mean this PR is
faster. In this PR, rows marked (gap) run the CuTe DSL kernel with PDL.

| shape (mode, M) | previous Cake us s1 / s2 | this PR us s1 / s2 | CuTe
DSL kernel + PDL us s1 / s2 | speedup s1 / s2 |
|---|---|---|---|---|
| mode0 M=1 | 1.668 / 1.669 | 1.221 / 1.221 | 1.445 / 1.447 | 1.366 /
1.367 |
| mode0 M=2 | 1.761 / 1.760 | 1.256 / 1.258 | 1.505 / 1.503 | 1.402 /
1.399 |
| mode0 M=4 | 1.760 / 1.760 | 1.247 / 1.248 | 1.504 / 1.504 | 1.411 /
1.410 |
| mode0 M=8 | 1.735 / 1.738 | 1.312 / 1.311 | 1.505 / 1.503 | 1.322 /
1.326 |
| mode0 M=16 | 1.825 / 1.824 | 1.377 / 1.375 | 1.567 / 1.568 | 1.325 /
1.327 |
| mode0 M=32 | 2.017 / 2.016 | 1.504 / 1.504 | 1.696 / 1.696 | 1.341 /
1.340 |
| mode0 M=64 | 2.467 / 2.465 | 1.927 / 1.922 | 2.034 / 2.031 | 1.280 /
1.283 |
| mode0 M=128 | 2.916 / 2.943 | 2.337 / 2.338 | 2.339 / 2.344 | 1.248 /
1.259 |
| mode0 M=256 | 3.886 / 3.883 | 3.520 / 3.523 | 3.586 / 3.582 | 1.104 /
1.102 |
| mode0 M=1024 (gap) | 12.331 / 12.319 | 12.260 / 12.280 | 12.279 /
12.276 | 1.006 / 1.003 |
| mode0 M=2048 (gap) | 26.711 / 26.707 | 24.973 / 24.963 | 24.327 /
24.331 | 1.070 / 1.070 |
| mode0 M=4096 | 52.467 / 52.057 | 52.027 / 52.215 | 52.196 / 52.245 |
1.008 / 0.997 |
| mode0 M=8192 | 101.343 / 100.964 | 100.527 / 100.753 | 102.920 /
103.127 | 1.008 / 1.002 |
| mode0 M=16384 | 198.443 / 198.508 | 198.564 / 198.670 | 205.136 /
205.474 | 0.999 / 0.999 |
| mode1 M=1 | 2.209 / 2.208 | 1.504 / 1.503 | 1.570 / 1.571 | 1.469 /
1.469 |
| mode1 M=2 | 2.208 / 2.208 | 1.504 / 1.504 | 1.569 / 1.569 | 1.468 /
1.468 |
| mode1 M=4 | 2.210 / 2.211 | 1.567 / 1.567 | 1.633 / 1.631 | 1.410 /
1.411 |
| mode1 M=8 | 2.272 / 2.272 | 1.507 / 1.506 | 1.633 / 1.631 | 1.508 /
1.509 |
| mode1 M=16 | 2.401 / 2.401 | 1.697 / 1.695 | 1.760 / 1.760 | 1.415 /
1.417 |
| mode1 M=32 | 2.274 / 2.528 | 1.695 / 1.792 | 1.789 / 1.823 | 1.342 /
1.411 |
| mode1 M=64 | 2.664 / 2.892 | 2.185 / 2.221 | 2.288 / 2.336 | 1.219 /
1.302 |
| mode1 M=128 | 2.788 / 3.035 | 2.403 / 2.402 | 2.623 / 2.593 | 1.160 /
1.264 |
| mode1 M=256 | 3.896 / 4.085 | 3.778 / 3.770 | 4.267 / 4.261 | 1.031 /
1.084 |
| mode1 M=1024 | 12.927 / 13.148 | 12.463 / 12.453 | 14.025 / 14.024 |
1.037 / 1.056 |
| mode1 M=2048 | 26.725 / 27.135 | 26.514 / 26.559 | 27.938 / 28.080 |
1.008 / 1.022 |
| mode1 M=4096 | 52.847 / 53.220 | 52.668 / 52.604 | 58.203 / 58.107 |
1.003 / 1.012 |
| mode1 M=8192 | 102.591 / 102.651 | 102.370 / 102.436 | 113.588 /
113.663 | 1.002 / 1.002 |
| mode1 M=16384 | 203.520 / 202.950 | 203.935 / 204.061 | 226.903 /
226.827 | 0.998 / 0.995 |

**`rmsnorm_sigmoid_gate` on NVIDIA GB300 (sm_103a, 152 SMs), driver
580.159.03, kernels JIT-compiled with nvcc 13.4 (CUDA 13.4), torch
2.14.1+cu130.** Values are microseconds per launch from graph replay:
one CUDA graph of 32 launches replayed 20x, per-launch average, median
of 5 counterbalanced groups. Each cell gives two sessions as s1 / s2.
Speedup is previous Cake / this PR, so ratios > 1 mean this PR is
faster. In this PR, rows marked (gap) run the CuTe DSL kernel with PDL.

| shape (heads, tokens) | previous Cake us s1 / s2 | this PR us s1 / s2
| CuTe DSL kernel + PDL us s1 / s2 | speedup s1 / s2 |
|---|---|---|---|---|
| h128 T=1 (gap) | 1.174 / 1.171 | 0.880 / 0.876 | 0.912 / 0.917 | 1.334
/ 1.337 |
| h128 T=2 | 1.170 / 1.174 | 0.979 / 0.978 | 1.170 / 1.170 | 1.195 /
1.200 |
| h128 T=3 | 1.178 / 1.177 | 0.976 / 0.979 | 1.051 / 1.050 | 1.207 /
1.202 |
| h128 T=8 | 1.239 / 1.243 | 1.045 / 1.052 | 1.048 / 1.051 | 1.186 /
1.182 |
| h128 T=64 (gap) | 1.557 / 1.560 | 1.239 / 1.241 | 1.241 / 1.243 |
1.257 / 1.257 |
| h128 T=256 | 2.261 / 2.263 | 2.018 / 2.015 | 2.331 / 2.328 | 1.120 /
1.123 |
| h128 T=1024 | 4.863 / 4.862 | 4.852 / 4.851 | 7.002 / 7.009 | 1.002 /
1.002 |
| h128 T=4096 | 28.380 / 28.381 | 28.073 / 28.069 | 29.692 / 29.695 |
1.011 / 1.011 |
| h128 T=16384 | 113.268 / 113.256 | 113.088 / 113.074 | 114.893 /
114.886 | 1.002 / 1.002 |
| h32 T=1 (gap) | 1.236 / 1.235 | 0.867 / 0.862 | 0.915 / 0.914 | 1.426
/ 1.433 |
| h32 T=2 | 1.237 / 1.232 | 0.987 / 0.986 | 1.111 / 1.111 | 1.253 /
1.249 |
| h32 T=8 | 1.237 / 1.239 | 0.986 / 0.985 | 1.169 / 1.170 | 1.255 /
1.258 |
| h32 T=9 | 1.242 / 1.240 | 0.985 / 0.985 | 1.049 / 1.051 | 1.261 /
1.259 |
| h32 T=17 | 1.242 / 1.249 | 0.987 / 0.989 | 1.053 / 1.050 | 1.258 /
1.263 |
| h32 T=64 | 1.363 / 1.365 | 1.105 / 1.109 | 1.105 / 1.103 | 1.233 /
1.231 |
| h32 T=256 (gap) | 1.557 / 1.555 | 1.242 / 1.242 | 1.241 / 1.240 |
1.254 / 1.252 |
| h32 T=257 | 1.557 / 1.554 | 1.240 / 1.245 | 1.245 / 1.241 | 1.256 /
1.248 |
| h32 T=1024 | 2.264 / 2.263 | 2.026 / 2.031 | 2.327 / 2.328 | 1.117 /
1.114 |
| h32 T=4096 | 4.855 / 4.863 | 4.865 / 4.868 | 7.002 / 7.007 | 0.998 /
0.999 |
| h32 T=16384 | 28.371 / 28.372 | 28.055 / 28.050 | 29.681 / 29.682 |
1.011 / 1.011 |
| h16 T=1 (gap) | 1.171 / 1.172 | 0.917 / 0.916 | 0.858 / 0.859 | 1.277
/ 1.279 |
| h16 T=8 | 1.169 / 1.171 | 0.925 / 0.922 | 1.169 / 1.171 | 1.264 /
1.270 |
| h16 T=16 | 1.176 / 1.178 | 0.918 / 0.924 | 1.180 / 1.182 | 1.281 /
1.275 |
| h16 T=17 | 1.172 / 1.172 | 0.920 / 0.922 | 1.305 / 1.305 | 1.274 /
1.271 |
| h16 T=64 | 1.242 / 1.244 | 0.984 / 0.986 | 1.304 / 1.305 | 1.262 /
1.262 |
| h16 T=256 | 1.364 / 1.364 | 1.112 / 1.113 | 1.367 / 1.367 | 1.227 /
1.226 |
| h16 T=1024 | 1.755 / 1.756 | 1.749 / 1.751 | 1.941 / 1.941 | 1.003 /
1.003 |
| h16 T=4096 | 3.156 / 3.160 | 3.158 / 3.159 | 4.243 / 4.244 | 0.999 /
1.000 |
| h16 T=16384 | 9.366 / 9.365 | 9.540 / 9.530 | 13.607 / 13.604 | 0.982
/ 0.983 |

**`gated_residual_rmsnorm` on NVIDIA GB300 (sm_103a, 152 SMs), driver
580.159.03, kernels JIT-compiled with nvcc 13.4 (CUDA 13.4), torch
2.14.1+cu130: the shape-list rows whose launch under `enable_pdl=True`
changes in this PR.** Values are microseconds per launch from graph
replay: one CUDA graph of 32 launches replayed 20x, per-launch average,
median of 5 counterbalanced groups. Each cell gives two sessions as s1 /
s2. Speedup is previous Cake / this PR, so ratios > 1 mean this PR is
faster. In this PR, rows marked (gap) run the CuTe DSL kernel with PDL.

| shape (mode, M) | previous Cake us s1 / s2 | this PR us s1 / s2 | CuTe
DSL kernel + PDL us s1 / s2 | speedup s1 / s2 |
|---|---|---|---|---|
| mode0 M=1 | 1.541 / 1.541 | 1.092 / 1.093 | 1.349 / 1.350 | 1.411 /
1.410 |
| mode0 M=2 | 1.626 / 1.625 | 1.177 / 1.179 | 1.435 / 1.436 | 1.381 /
1.378 |
| mode0 M=4 | 1.641 / 1.645 | 1.235 / 1.237 | 1.437 / 1.437 | 1.329 /
1.330 |
| mode0 M=8 | 1.748 / 1.748 | 1.240 / 1.243 | 1.496 / 1.495 | 1.410 /
1.406 |
| mode0 M=16 | 1.752 / 1.753 | 1.300 / 1.299 | 1.557 / 1.561 | 1.348 /
1.349 |
| mode0 M=32 | 1.880 / 1.880 | 1.375 / 1.375 | 1.629 / 1.627 | 1.367 /
1.367 |
| mode0 M=64 | 2.390 / 2.394 | 1.875 / 1.868 | 1.941 / 1.940 | 1.275 /
1.282 |
| mode0 M=128 | 2.841 / 2.837 | 2.261 / 2.259 | 2.268 / 2.267 | 1.257 /
1.256 |
| mode0 M=256 | 3.988 / 3.968 | 3.291 / 3.290 | 3.483 / 3.480 | 1.212 /
1.206 |
| mode0 M=1024 | 12.644 / 12.654 | 12.019 / 12.018 | 12.297 / 12.290 |
1.052 / 1.053 |
| mode0 M=2048 (gap) | 24.503 / 24.513 | 22.497 / 22.495 | 22.459 /
22.463 | 1.089 / 1.090 |
| mode0 M=4096 (gap) | 51.438 / 51.441 | 50.432 / 50.434 | 50.290 /
50.287 | 1.020 / 1.020 |
| mode0 M=8192 | 98.402 / 98.415 | 97.848 / 97.846 | 98.706 / 98.671 |
1.006 / 1.006 |
| mode0 M=16384 | 193.403 / 193.401 | 193.262 / 193.273 | 195.495 /
195.584 | 1.001 / 1.001 |
| mode1 M=1 | 2.002 / 2.007 | 1.369 / 1.369 | 1.432 / 1.433 | 1.462 /
1.466 |
| mode1 M=2 | 2.070 / 2.072 | 1.490 / 1.491 | 1.559 / 1.559 | 1.389 /
1.390 |
| mode1 M=4 | 2.072 / 2.074 | 1.493 / 1.492 | 1.558 / 1.561 | 1.388 /
1.390 |
| mode1 M=8 | 2.131 / 2.131 | 1.509 / 1.513 | 1.560 / 1.560 | 1.412 /
1.408 |
| mode1 M=16 | 2.196 / 2.198 | 1.555 / 1.556 | 1.627 / 1.624 | 1.412 /
1.413 |
| mode1 M=32 | 2.005 / 2.007 | 1.560 / 1.560 | 1.686 / 1.687 | 1.285 /
1.287 |
| mode1 M=64 | 2.456 / 2.456 | 2.006 / 2.004 | 2.195 / 2.196 | 1.224 /
1.226 |
| mode1 M=128 | 2.704 / 2.708 | 2.265 / 2.262 | 2.456 / 2.453 | 1.194 /
1.197 |
| mode1 M=256 | 3.994 / 3.995 | 3.364 / 3.355 | 4.062 / 4.057 | 1.187 /
1.191 |
| mode1 M=1024 | 12.672 / 12.676 | 12.200 / 12.208 | 13.539 / 13.551 |
1.039 / 1.038 |
| mode1 M=2048 | 25.135 / 25.133 | 25.143 / 25.143 | 25.491 / 25.494 |
1.000 / 1.000 |
| mode1 M=4096 | 51.109 / 51.106 | 50.700 / 50.705 | 53.367 / 53.360 |
1.008 / 1.008 |
| mode1 M=8192 | 98.961 / 98.956 | 98.885 / 98.892 | 104.078 / 104.075 |
1.001 / 1.001 |
| mode1 M=16384 | 194.849 / 194.894 | 194.665 / 194.813 | 206.620 /
206.713 | 1.001 / 1.000 |

The other Cake variant of `rmsnorm_sigmoid_gate`, the plain `bf16`
route, ships on SM100 (sm_100a), SM103 (sm_103a) and SM107 (sm_107a) and
is unchanged; `bf16_pdl` ships on SM100 and SM103, while on SM107
`enable_pdl=True` keeps the CuTe DSL kernel with PDL; the
`gated_residual_rmsnorm` PDL routes get per-window launch forms on SM100
and SM103 and are unchanged on SM107.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* RMSNorm sigmoid-gate operations now support PDL-enabled launches, with
backend selection accounting for the requested launch mode and device
support.
* Cake routes can use compatible plain builds for some PDL-enabled
calls; availability depends on the selected route and input shape.

* **Bug Fixes**
* Improved route admission checks across supported input sizes,
including clearer handling of unsupported gaps and fallback to CuTe when
available.
  * Hardened validation for edge cases in generated CUDA bindings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [53feaae](https://github.com/flashinfer-ai/flashinfer/commit/53feaae34c0a9c7bd8801676a150c4321b496c16)

- **作者**: eigen
- **时间**: 2026-10-25T17:24:26Z
- **提交信息**: perf(cake_dcp_alltoall): faster DCP all-to-all CP2 / CP4 kernels on sm_100a and sm_103a (#7340)

FlashInfer's DCP (decode context parallelism) all-to-all,
`decode_cp_a2a_alltoall` (`cake_dcp_alltoall`), exchanges each rank's
partial attention output rows and their softmax statistics between the
CP ranks of one node over NVLink, through an LL128 FIFO. Cake generates
five variants of this kernel. FlashInfer ships two of them, CP2 and CP4
(BF16, head dim 128, two FP32 statistics), each for sm_100a and sm_103a.
This PR updates both shipped variants to a new kernel version. In it,
the receiver releases its last FIFO slot at the beginning of the next
launch and writes received entries from registers with plain stores. The
baseline is the previous Cake version of these kernels, which FlashInfer
main ships today. The new version is 1.15x–1.33x faster, and every shape
measured is faster.

Latency per call in us on NVIDIA GB300 (sm_103a) and GB200 (sm_100a)
with CUDA 13.4, using BF16 partial outputs, head dim 128 and two FP32
softmax statistics per row, one rank per GPU on one node (CP2 on 2 GPUs,
CP4 on 4 GPUs), under warm and cold L2. Each value is the slowest rank's
median, each call begins after an untimed cross-rank barrier, measured
in 30 interleaved rounds, and speedup = previous / this PR.

| GPU | CP size | tokens | previous, warm L2 (us) | this PR, warm L2
(us) | speedup | previous, cold L2 (us) | this PR, cold L2 (us) |
speedup |
|---|---|---|---|---|---|---|---|---|
| GB300 (sm_103a) | 2 | 1 | 5.872 | 4.784 | 1.23x | 5.840 | 4.864 |
1.20x |
| GB300 (sm_103a) | 2 | 16 | 6.288 | 5.344 | 1.18x | 6.192 | 5.248 |
1.18x |
| GB300 (sm_103a) | 2 | 64 | 6.560 | 5.536 | 1.18x | 6.624 | 5.568 |
1.19x |
| GB300 (sm_103a) | 2 | 128 | 7.248 | 6.192 | 1.17x | 7.232 | 6.240 |
1.16x |
| GB300 (sm_103a) | 4 | 1 | 5.440 | 4.480 | 1.21x | 5.424 | 4.480 |
1.21x |
| GB300 (sm_103a) | 4 | 16 | 5.664 | 4.736 | 1.20x | 5.664 | 4.736 |
1.20x |
| GB300 (sm_103a) | 4 | 64 | 6.816 | 5.728 | 1.19x | 6.784 | 5.728 |
1.18x |
| GB300 (sm_103a) | 4 | 128 | 7.536 | 6.496 | 1.16x | 7.569 | 6.496 |
1.17x |
| GB200 (sm_100a) | 2 | 1 | 5.456 | 4.288 | 1.27x | 5.584 | 4.192 |
1.33x |
| GB200 (sm_100a) | 2 | 16 | 6.384 | 5.184 | 1.23x | 6.240 | 5.280 |
1.18x |
| GB200 (sm_100a) | 2 | 64 | 6.704 | 5.696 | 1.18x | 6.640 | 5.632 |
1.18x |
| GB200 (sm_100a) | 2 | 128 | 7.376 | 6.368 | 1.16x | 7.312 | 6.336 |
1.15x |
| GB200 (sm_100a) | 4 | 1 | 5.472 | 4.608 | 1.19x | 5.472 | 4.608 |
1.19x |
| GB200 (sm_100a) | 4 | 16 | 5.888 | 4.960 | 1.19x | 6.672 | 5.728 |
1.16x |
| GB200 (sm_100a) | 4 | 64 | 6.720 | 5.680 | 1.18x | 6.784 | 5.744 |
1.18x |
| GB200 (sm_100a) | 4 | 128 | 7.824 | 6.768 | 1.16x | 7.872 | 6.816 |
1.15x |

Cake also generates CP8, a CP2 build with peer-CTA fan-out and an FP16
head-dim-256 CP4 build of this kernel, which FlashInfer does not ship;
the family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* Updated the kernel variants used for all-to-all operations. Their
configured communication sizes and shared-memory settings remain
unchanged, so the operation’s existing configuration is preserved.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5396dc3](https://github.com/flashinfer-ai/flashinfer/commit/5396dc3b7a955386c37a606c97c8269f8bab9a73)

- **作者**: eigen
- **时间**: 2026-10-25T17:19:05Z
- **提交信息**: perf(cake_grouped_mxfp8_quantize): select the bulk-copy and row-tiled programs by shape (#7322)

`cake_grouped_mxfp8_quantize` (FlashInfer's Cake grouped MXFP8
quantization) takes a BF16 or F16 `x[B, M, K]` and an int32 `mask[B]`
that gives the valid rows per group. It produces FP8 E4M3 values and
UE8M0 block scales in the 128x4 grouped-GEMM layout. The kernel now has
three forms, each for BF16 and F16 input:

- the existing row-2D kernel;
- a bulk-copy form that fetches the row tile while the group's mask word
is read;
- a row-tiled form in which each thread quantizes two rows of its group,
so a sparse mask launches fewer CTAs.

This PR adds the bulk-copy and row-tiled programs. It picks a program
from the problem shape alone, and the host never reads the mask:

- inputs of at most 4 MiB use bulk-copy;
- problems with at least 16,384 rows (B·M) use row-tiled;
- all other problems keep row-2D.

The baseline is the previous Cake version, which used row-2D for every
shape. Against it, 14 of the 19 shapes are faster: 1.07–1.11x on the
four small full-mask inputs and 1.41–1.94x on the large inputs with
sparse masks. The three large full-mask inputs are memory-bandwidth
bound and are 1.0–2.8% slower (speedup 0.973–0.990). The two shapes that
keep row-2D are unchanged.

Speedup = previous µs / this PR µs, the median of paired per-round
ratios; above 1 is faster.
† These shapes use the same row-2D program before and after, so their
two columns are an A/A pair of that program.

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4**

| shape [B, M, K] | dtype | mask | valid rows | program | previous (µs)
| this PR (µs) | speedup |
|---|---|---|---:|---|---:|---:|---:|
| [2, 256, 4096] | BF16 | full | 512 | bulk-copy | 3.721 | 3.482 |
1.0678 |
| [2, 256, 4096] | F16 | full | 512 | bulk-copy | 3.719 | 3.468 | 1.0721
|
| [2, 128, 4096] | BF16 | full | 256 | bulk-copy | 2.997 | 2.797 |
1.0727 |
| [3, 256, 2048] | BF16 | full | 768 | bulk-copy | 3.406 | 3.096 |
1.0995 |
| [8, 512, 2048] † | BF16 | full | 4096 | row-2D | 6.857 | 6.861 |
1.0003 |
| [64, 128, 4096] † | BF16 | full | 8192 | row-2D | 19.023 | 19.056 |
0.9984 |
| [32, 1024, 7168] | BF16 | 16 / group | 512 | row-tiled | 34.219 |
18.879 | 1.8125 |
| [32, 1024, 7168] | BF16 | 32 / group | 1024 | row-tiled | 34.252 |
19.040 | 1.7992 |
| [32, 1024, 7168] | BF16 | 128 / group | 4096 | row-tiled | 34.463 |
21.544 | 1.5998 |
| [32, 1024, 7168] | BF16 | 512 in group 0 | 512 | row-tiled | 34.724 |
17.955 | 1.9340 |
| [32, 1024, 7168] | BF16 | 1024 in group 0 | 1024 | row-tiled | 36.461
| 19.712 | 1.8497 |
| [32, 1024, 7168] | BF16 | 1024 in group 0, 99 in others | 4093 |
row-tiled | 36.683 | 22.532 | 1.6280 |
| [32, 1024, 7168] | BF16 | Zipf, 4096 total | 4096 | row-tiled | 38.155
| 24.999 | 1.5261 |
| [32, 1024, 7168] | BF16 | full | 32768 | row-tiled | 103.497 | 104.558
| 0.9899 |
| [32, 1024, 7168] | F16 | 128 / group | 4096 | row-tiled | 34.478 |
21.552 | 1.5997 |
| [32, 1024, 4096] | BF16 | 16 / group | 512 | row-tiled | 17.902 |
10.827 | 1.6535 |
| [32, 1024, 4096] | BF16 | 128 / group | 4096 | row-tiled | 18.383 |
13.039 | 1.4099 |
| [32, 1024, 4096] | BF16 | full | 32768 | row-tiled | 61.790 | 63.192 |
0.9778 |
| [32, 1024, 2048] | BF16 | full | 32768 | row-tiled | 33.816 | 34.440 |
0.9821 |

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4**

| shape [B, M, K] | dtype | mask | valid rows | program | previous (µs)
| this PR (µs) | speedup |
|---|---|---|---:|---|---:|---:|---:|
| [2, 256, 4096] | BF16 | full | 512 | bulk-copy | 3.909 | 3.604 |
1.0838 |
| [2, 256, 4096] | F16 | full | 512 | bulk-copy | 3.868 | 3.575 | 1.0816
|
| [2, 128, 4096] | BF16 | full | 256 | bulk-copy | 3.145 | 2.889 |
1.0882 |
| [3, 256, 2048] | BF16 | full | 768 | bulk-copy | 3.552 | 3.210 |
1.1065 |
| [8, 512, 2048] † | BF16 | full | 4096 | row-2D | 7.066 | 7.062 |
0.9999 |
| [64, 128, 4096] † | BF16 | full | 8192 | row-2D | 19.141 | 19.156 |
0.9993 |
| [32, 1024, 7168] | BF16 | 16 / group | 512 | row-tiled | 35.968 |
19.796 | 1.8166 |
| [32, 1024, 7168] | BF16 | 32 / group | 1024 | row-tiled | 35.991 |
19.948 | 1.8042 |
| [32, 1024, 7168] | BF16 | 128 / group | 4096 | row-tiled | 36.124 |
22.392 | 1.6130 |
| [32, 1024, 7168] | BF16 | 512 in group 0 | 512 | row-tiled | 36.392 |
18.802 | 1.9357 |
| [32, 1024, 7168] | BF16 | 1024 in group 0 | 1024 | row-tiled | 38.085
| 20.548 | 1.8535 |
| [32, 1024, 7168] | BF16 | 1024 in group 0, 99 in others | 4093 |
row-tiled | 38.313 | 23.362 | 1.6398 |
| [32, 1024, 7168] | BF16 | Zipf, 4096 total | 4096 | row-tiled | 39.844
| 25.898 | 1.5383 |
| [32, 1024, 7168] | BF16 | full | 32768 | row-tiled | 102.500 | 103.954
| 0.9860 |
| [32, 1024, 7168] | F16 | 128 / group | 4096 | row-tiled | 36.120 |
22.427 | 1.6105 |
| [32, 1024, 4096] | BF16 | 16 / group | 512 | row-tiled | 18.771 |
11.325 | 1.6574 |
| [32, 1024, 4096] | BF16 | 128 / group | 4096 | row-tiled | 19.237 |
13.624 | 1.4114 |
| [32, 1024, 4096] | BF16 | full | 32768 | row-tiled | 61.319 | 63.047 |
0.9726 |
| [32, 1024, 2048] | BF16 | full | 32768 | row-tiled | 33.969 | 34.534 |
0.9838 |

All six programs (row-2D, bulk-copy and row-tiled, each for BF16 and F16
input) ship for sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded grouped MXFP8 quantization support for float16 and bfloat16
inputs.
* Added automatic selection among row-based, bulk, and tiled processing
based on input type and shape.
  * Large workloads can use tiled processing across multiple rows.
  * Quantization supports caller-provided wider padded rows.
* **Bug Fixes**
* Improved handling of masked rows and padded chunks, including empty or
partial groups.
  * Added validation for incompatible inputs and launch dimensions.
* Improved consistency of quantized outputs across supported processing
modes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [53ecbde](https://github.com/flashinfer-ai/flashinfer/commit/53ecbde224f45741a2aa4a0b928a330a502ab15e)

- **作者**: eigen
- **时间**: 2026-10-25T16:58:12Z
- **提交信息**: perf(cake_minimax_h3): faster FP8 out-projection on SM120 (#7333)

`flashinfer.diffusion_ops.cake_minimax_h3_sm120_quant_out_proj` computes
the MiniMax-H3 out-projection on SM120 (`sm_120a`) in two variants: FP8
per-token (`minimax_h3_fp8_out_proj`) and NVFP4
(`minimax_h3_nvfp4_out_proj`). Each variant runs as one persistent
launch that does the activation quantization, the GEMM and the
gate/residual epilogue. This PR changes only the FP8 variant: its
persistent tile order now walks one M tile per swath, as the NVFP4
variant already does. The contraction and its accumulation order are
unchanged and the output is bitwise equal; compared with the current
main `minimax_h3_fp8_out_proj`, the six FP8 shapes run 1.006x to 1.011x
faster (geomean 1.009).

NVIDIA RTX PRO 6000 Blackwell Server Edition (`sm_120a`), CUDA 13.4.
Time of the complete operator (activation quantization + GEMM + gated
residual), median of 5 interleaved rounds with a cold L2. M = rows.
NVFP4 rows ("changed = no") run the same kernel in both columns, so
their ratio is run-to-run variation.

| quantization | M | changed | before (µs) | after (µs) | speedup |
|---|---:|---|---:|---:|---:|
| FP8 | 33472 | yes | 3619.0 | 3584.4 | 1.010x |
| FP8 | 38592 | yes | 4155.7 | 4114.0 | 1.010x |
| FP8 | 48768 | yes | 5285.4 | 5225.9 | 1.011x |
| FP8 | 58944 | yes | 6412.0 | 6361.2 | 1.008x |
| FP8 | 74240 | yes | 8087.9 | 8002.2 | 1.011x |
| FP8 | 109952 | yes | 12028.8 | 11955.9 | 1.006x |
| NVFP4 | 33472 | no | 1959.0 | 1957.3 | 1.001x |
| NVFP4 | 38592 | no | 2264.6 | 2270.8 | 0.997x |
| NVFP4 | 48768 | no | 2876.6 | 2877.6 | 1.000x |
| NVFP4 | 58944 | no | 3481.1 | 3485.5 | 0.999x |
| NVFP4 | 74240 | no | 4374.0 | 4372.8 | 1.000x |
| NVFP4 | 109952 | no | 6500.4 | 6511.9 | 0.998x |

The SM100/SM103 module `flashinfer.diffusion_ops.minimax_h3_out_proj`
ships BF16, MXFP8 and NVFP4 variants of the same projection on `sm_100a`
and `sm_103a`; with this module the family covers `sm_100a`, `sm_103a`
and `sm_120a`.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b8ed186](https://github.com/flashinfer-ai/flashinfer/commit/b8ed186df31b1ad175d6b0b4a47120542c48279d)

- **作者**: eigen
- **时间**: 2026-10-25T16:37:22Z
- **提交信息**: perf(cake_minimax_h3): SM120 FP8 varlen attention: early PV hand-off and next-unit prefetch (#7334)

The MiniMax-H3 noncausal packed-varlen attention kernel works on THD
tensors ([tokens, 56 heads, 128 head dim]), with BF16 input and output
and int32 `cu_seqlens`. It has six Cake variants in FlashInfer. This PR
adds a new version of the sm_120a FP8 variant,
`minimax_h3_sm120_varlen_attention_fp8` (E4M3 QK and PV), with the same
API. Only the attention kernel changes. The baseline is the previous
Cake version of the same op (FlashInfer main at ba12a83, delivered by
#7289). The new version is 1.014x-1.055x faster on RTX 5090 and
1.030x-1.041x faster on RTX PRO 6000. Timings are median end-to-end
operator latency with cold L2 on CUDA 13.4, from paired, interleaved
runs on the same GPU with the same inputs.

### NVIDIA GeForce RTX 5090 (sm_120a, 170 SMs)

| shape | cu_seqlens | previous (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| center_4s | `[0, 33472]` | 50,039 | 48,541 | 1.031x |
| center_5s | `[0, 38592]` | 66,930 | 65,403 | 1.023x |
| center_6s | `[0, 48768]` | 108,228 | 106,476 | 1.016x |
| center_8s | `[0, 58944]` | 162,049 | 159,635 | 1.015x |
| center_10s | `[0, 74240]` | 259,573 | 255,989 | 1.014x |
| center_15s | `[0, 109952]` | 573,310 | 564,483 | 1.016x |
| tail_5s_a | `[0, 38531]` | 70,275 | 69,180 | 1.016x |
| tail_5s_b | `[0, 38629]` | 70,185 | 69,200 | 1.014x |
| pad_15s | `[0, 109901, 109952]` | 574,649 | 565,173 | 1.017x |
| seg4 | `[0, 8368, 16736, 25104, 33472]` | 15,049 | 14,829 | 1.015x |
| seg3_ragged | `[0, 257, 4567, 4824]` | 1,201 | 1,169 | 1.027x |
| seg_empty | `[0, 0, 129, 129, 500]` | 46.8 | 44.3 | 1.055x |

### NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120a, 188 SMs)

| shape | cu_seqlens | previous (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| center_4s | `[0, 33472]` | 48,276 | 46,558 | 1.037x |
| center_5s | `[0, 38592]` | 64,283 | 62,268 | 1.032x |
| center_6s | `[0, 48768]` | 102,432 | 99,322 | 1.031x |
| center_8s | `[0, 58944]` | 149,134 | 144,542 | 1.032x |
| center_10s | `[0, 74240]` | 234,716 | 227,466 | 1.032x |
| center_15s | `[0, 109952]` | 511,128 | 495,453 | 1.032x |
| tail_5s_a | `[0, 38531]` | 64,671 | 62,670 | 1.032x |
| tail_5s_b | `[0, 38629]` | 64,980 | 62,942 | 1.032x |
| pad_15s | `[0, 109901, 109952]` | 510,331 | 494,800 | 1.031x |
| seg4 | `[0, 8368, 16736, 25104, 33472]` | 14,144 | 13,693 | 1.033x |
| seg3_ragged | `[0, 257, 4567, 4824]` | 1,180 | 1,145 | 1.030x |
| seg_empty | `[0, 0, 129, 129, 500]` | 60.0 | 57.7 | 1.041x |

The other five Cake variants are the sm_120a NVFP4-QK forms
`minimax_h3_sm120_varlen_attention_nvfp4` (default) and
`minimax_h3_sm120_varlen_attention_nvfp4_nodelta`, plus the sm_100a /
sm_103a forms `minimax_h3_varlen_attention` (BF16),
`minimax_h3_varlen_fp8_attention` (FP8, with the BF16-input form
`minimax_h3_varlen_fp8_attention_bf16`) and
`minimax_h3_varlen_nvfp4_attention` (NVFP4-QK), so the family covers
sm_100a, sm_103a and sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated variable-length attention processing to prepare upcoming work
while the current task is finishing. This can improve processing
efficiency for workloads with multiple task segments. The operation’s
inputs and launch configuration remain unchanged, and no changes to
user-facing controls or behavior are noted.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d08a1f7](https://github.com/flashinfer-ai/flashinfer/commit/d08a1f73219323c4d507c2273e95cc95c06fda29)

- **作者**: eigen
- **时间**: 2026-10-25T15:19:40Z
- **提交信息**: perf(cake_nvfp4_attention): faster SM103 kernel with a tile-boundary overlap and P in tensor memory (#7328)

The experimental NVFP4 attention package ships exactly one Cake variant:
BF16 `[B, H, S, 128]` inputs and BF16 output, quantized to NVFP4 (E2M1
values with E4M3 block scales), noncausal, `S` divisible by 512, with
one program built for sm_103a (SM103). This PR delivers a faster kernel
for that same variant. It runs 1.02x to 1.05x faster than the Cake
program that FlashInfer main ships today.

NVIDIA GB300, sm_103a, CUDA 13.4: median kernel time in ms with a cold
L2; Speedup = FlashInfer main ms / this PR ms, computed from unrounded
medians.

| (B, H, S) | FlashInfer main (ms) | This PR (ms) | Speedup |
|---|---:|---:|---:|
| (4, 8, 4096) | 0.1145 | 0.1094 | 1.05x |
| (1, 8, 32768) | 1.4432 | 1.4201 | 1.02x |
| (8, 32, 8192) | 2.8392 | 2.7562 | 1.03x |

Cake ships no other data type, layout or fused form of this kernel in
FlashInfer, and the kernel family ships on sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated NVFP4 attention processing. No changes to supported library
configurations or CUDA version are noted.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [85fcf53](https://github.com/flashinfer-ai/flashinfer/commit/85fcf535775bb7b131dc52ac524d873e8063842b)

- **作者**: Yang Xu
- **时间**: 2026-10-25T15:09:28Z
- **提交信息**: perf(cudnn): avoid Stream object construction in warm attention calls (#7331)

## 📌 Description

Warm cuDNN attention calls construct a Python `torch.cuda.Stream` solely
to obtain its pointer. Read the current raw stream for the input
tensor's explicit CUDA device when Torch provides that getter and CUDA
is initialized, then bind it to the existing per-thread, per-device
cuDNN handle. Both prepared prefill and decode use the same helper.

The raw query runs on every call. Explicit Stream callers and Torch's
ordinary lazy-initialization/device-resolution path remain supported,
including environments without the raw getter. The fallback keeps the
previous integer device lookup.

### Measurements

NVIDIA B200 (1000 W), driver 615.71.10, Python 3.12.3, PyTorch
2.14.0+cu130, cuDNN 9.27, released Frontend 1.31.0, CuTe DSL 4.8.0.
Compare baseline `506fac620` (after #7317) with `baef56cd0`; four fresh
processes in baseline/candidate/candidate/baseline order, pinned to one
CPU, one Torch thread. Both rows select the same backend plan
(`eng10_k24=1_k27=0_k38=0_k40=3_k41=2`) before and after.

Existing `benchmarks/bench_cudnn_wrapper_host.py`, BF16, B=1,
Hq/Hkv=32/8, D=128, page size 16, fixed output buffers, no LSE. Values
are microseconds, baseline → candidate, aggregating the two per-process
medians for each variant:

| Workload | Warm host enqueue | Plan only | Plan + run host | CUDA
graph GPU replay |
|---|---:|---:|---:|---:|
| Ragged causal prefill, Q=KV=1024 | 32.796 → 31.154 | 42.429 → 44.927 |
83.560 → 84.441 | 26.858 → 26.856 |
| HND decode, Q=1, KV=8192 | 35.717 → 32.706 | 96.417 → 94.399 | 144.979
→ 139.089 | 12.127 → 12.108 |

Warm enqueue improves by 1.642 µs (5.0%) and 3.011 µs (8.4%). These are
host component measurements, not serving throughput or a kernel speedup.
Replay is essentially unchanged. The ragged plan-only result is **5.9%
slower** and plan+run is **1.1% slower** in this sample: candidate plan
medians were 47.102 and 42.752 µs, versus baseline 42.240 and 42.618 µs.
That repeat variation is retained and its cause is unresolved; this PR
does not claim a plan-time improvement. The public wrapper planning code
is byte-identical to the baseline.

Reproduce both commands in each installed checkout, verifying
`flashinfer.__file__` resolves to that checkout, and use the same idle
GPU/CPU and software stack for all four processes:

```bash
export OMP_NUM_THREADS=1 CUDNN_FRONTEND_ENABLE_FROST_ENGINES=0
python benchmarks/bench_cudnn_wrapper_host.py --kind ragged --batch 1 --q 1024 --kv 1024 --layout NHD --replan --output ragged.json
python benchmarks/bench_cudnn_wrapper_host.py --kind decode --batch 1 --q 1 --kv 8192 --layout HND --replan --output decode.json
```

The benchmark checks independent reference rows, replans before replay,
poisons outputs, and validates the timed replays within one output ULP.
All samples are retained.

## 🔍 Related Issues

Follows #7317; this removes per-call stream-object work, independent of
the immutable cuDNN capability cache.

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
- [x] All tests are passing (`unittest`, etc.; scoped validation below).

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

Review the raw getter's explicit-device and lazy-init guards, per-thread
handle ownership, and binding the current stream on each call. No public
API signatures, backend selection rules or kernels change.

Validation on the exact final source and B200: **181 passed, 2 skipped**
across the existing ragged-shape-override, prepared-contract and
wrapper-regression files plus three real public-wrapper capture tests
with the raw getter forced unavailable. Both skips require two GPUs. The
new stream tests switch A/B streams, change Q, then replay the old
capture and verify O/LSE. Six additional ragged/paged/decode forms, with
and without Stats, pass 192 FP64/lifecycle observations over four
processes. No timing or heuristic-choice golden tests.

The raw Torch getter is private: it is optional and used only after CUDA
initialization with an explicit CUDA device index. Missing getter,
unresolved device and lazy-init paths retain ordinary
`torch.cuda.current_stream`; explicit Stream calls remain supported.
Multi-device/thread ownership has CPU contract coverage, while the
actual two-GPU checks are the skips above.

Scoped changed-file pre-commit checks pass; the all-files checkbox above
remains unchecked deliberately. No timing or heuristic-selection golden
tests were added.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved cuDNN attention handling across CUDA devices and streams,
helping ensure operations use the appropriate stream.
* Prepared attention operations now produce consistent results when
executed on different CUDA streams, including during replay.
* **Tests**
* Added coverage for stream selection, device-specific behavior, and
prepared attention results across multiple streams.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9bad274](https://github.com/flashinfer-ai/flashinfer/commit/9bad274a7d8669c229b32f578ba3d9376337e601)

- **作者**: eigen
- **时间**: 2026-10-25T15:09:10Z
- **提交信息**: fix(cake_nvfp4_mla_decode): ship build.json in the wheel and size test workspaces on the current device (#7327)

The package loader reads `build.json` on first use, but the package-data
entry listed only `csrc/**`, so an installed (non-editable) wheel raised
`RuntimeError` from `manifest()`. Add `build.json` to the entry, as the
other Cake packages do.

The tests sized the split workspace from device 0's SM count while
running on the current device; use the current device instead.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* NVFP4 MLA decode package distributions now include build metadata
alongside their supporting resources.

* **Tests**
* GPU decode checks now use the active CUDA device when determining its
multiprocessor count, improving validation when a non-default device is
selected.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [66a81f1](https://github.com/flashinfer-ai/flashinfer/commit/66a81f1bca98a6c313102b2d1fe4becee0b0923b)

- **作者**: eigen
- **时间**: 2026-10-25T14:58:44Z
- **提交信息**: perf(cake_fused_norm_combine): packed BF16x2 peer sums, packed norm conversions, early stream loads and a one-trip pipelined token body (#7330)

`cake_fused_norm_combine` has one Cake variant: BF16, hidden size 2560,
eight peers and two norm tracks. This PR delivers a new version of that
variant. The host picks one of four programs by token count, and this PR
changes all four with the same outputs. The baseline is the previous
Cake version of this kernel shipped in FlashInfer (current main, which
includes #7285). The new version is faster at every measured token count
on both GPUs. Speedups range from 1.048× to 1.101× on B200 and from
1.054× to 1.107× on B300.

| GPU | tokens | previous Cake (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|---:|
| B200 | 1 | 10.112 | 9.184 | 1.101× |
| B200 | 8 | 11.520 | 10.528 | 1.094× |
| B200 | 64 | 14.175 | 12.928 | 1.096× |
| B200 | 256 | 16.768 | 15.776 | 1.063× |
| B200 | 1024 | 29.792 | 28.416 | 1.048× |
| B200 | 2048 | 46.560 | 42.881 | 1.086× |
| B300 | 1 | 10.272 | 9.280 | 1.107× |
| B300 | 8 | 12.384 | 11.392 | 1.087× |
| B300 | 64 | 15.008 | 13.792 | 1.088× |
| B300 | 256 | 17.472 | 16.576 | 1.054× |
| B300 | 1024 | 30.688 | 28.991 | 1.059× |
| B300 | 2048 | 47.008 | 43.872 | 1.071× |

Measured on 8× NVIDIA B200 (sm_100a) and 8× NVIDIA B300 (sm_103a) with
CUDA 13.4, where each time is the per-call kernel time of the eight-rank
collective (the slowest rank of each call, median over calls) and
speedup = previous Cake / this PR.

Cake ships no other variant of this kernel, and the kernel ships on
sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Behavior Changes**
* Fused normalization and collective-combine calculations now use direct
BF16 operations. Residual, normalized, and combined outputs may differ
slightly from previous versions because of changes in rounding and
accumulation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a02c8c5](https://github.com/flashinfer-ai/flashinfer/commit/a02c8c5e6b57f74130c7729c3911d439dba7e672)

- **作者**: eigen
- **时间**: 2026-10-25T14:53:28Z
- **提交信息**: fix(cake_minimax_h3): reject SM120 varlen attention inputs whose offsets overflow 32-bit indexing (#7320)

The SM120 FP8 and NVFP4 packed-varlen attention programs index the
`[tokens padded to 128, heads, 128]` operands with signed 32-bit
offsets. The host checked shapes and dtypes but not that extent, so a
large enough input (about 299,600 tokens at 56 heads) would overflow the
offsets. The segment plan that both ops build now raises `ValueError`
before it builds any table, so cached plans add no per-call cost.

This addresses the review comment on #7289.

Tests on an RTX PRO 6000 Blackwell Server Edition (sm_120a, CUDA 13.4):
`tests/diffusion_ops/test_minimax_h3_sm120_quant_varlen_attention.py`
(with the new
`test_minimax_h3_sm120_varlen_plan_rejects_32_bit_offset_overflow`),
`test_minimax_h3_sm120_quant_varlen_attention_programs.py`,
`test_minimax_h3_sm120_nvfp4_varlen_attention.py`,
`test_minimax_h3_sm120_nvfp4_varlen_attention_nodelta.py` and
`test_minimax_h3_sm120_nvfp4_fp8pv_programs.py`: 126 passed, 8 skipped.
pre-commit passes on the changed files.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Plan creation now rejects inputs whose padded token count, head count,
and head dimension exceed the supported 32-bit offset limit.
* Plan creation also rejects inputs whose segment counts or query-tile
statistics exceed the statistics kernels’ 32-bit offset limit, including
cases with empty segments.
* These checks prevent plans from being created for inputs whose offsets
cannot be represented safely.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cf5c9a6](https://github.com/flashinfer-ai/flashinfer/commit/cf5c9a6a415b6273fe58c88e082520e2bf9cbf5f)

- **作者**: eigen
- **时间**: 2026-10-25T14:48:08Z
- **提交信息**: feat(cake_fused_moe): BF16 × NVFP4 W4A16 split fused-MoE kernels for sm_100a/sm_103a (#7315)

FlashInfer's Cake fused-MoE kernels come in four forms: two SiTU
routed-MoE forms (NVFP4 weights; MXFP4 weights with MXFP8 activations,
in CUDA C++ and CuTe DSL lowerings), the warp-decode MoE, and, with this
PR, the BF16 activation × NVFP4 weight "W4A16 Split" form. It runs FC1
with gated SwiGLU and FC2 as two kernels behind
`cutlass_fused_moe(backend="cake")` on the prequantized W4A16 weight
tensors, with 10 programs per architecture. No earlier Cake W4A16
version exists, so the baseline is FlashInfer's own CuTe DSL W4A16 split
fused-MoE at its tuned tactic. Against that baseline, 6 of the 12 shapes
are faster in both sessions, up to 1.054 / 1.046 at D1. The other 6 are
slower: D8, D32, D128, D512, D4096 and G128. The largest gap is at G128
(0.923).

NVIDIA B300 (SXM6, sm_103a), CUDA 13.4. Preset D = H 7168, I 2048, E
256, top-8 on 1 GPU; preset G = H 6144, I 2048, E 256, top-8, EP8 on 8
GPUs. Both arms CUDA-graph captured, CUPTI kernel time, cold L2, mean of
4 identical instances, two sessions s1/s2. Ratio = FlashInfer µs / Cake
µs (>1 = Cake faster).

| preset | T | FlashInfer µs s1 / s2 | Cake µs s1 / s2 | FI/Cake s1 / s2
|
|---|---|---|---|---|
| D (H7168, 1 GPU) | 1 | 53.73 / 53.85 | 50.98 / 51.50 | 1.054 / 1.046 |
| D | 8 | 223.15 / 223.49 | 224.84 / 223.86 | 0.993 / 0.998 |
| D | 32 | 623.55 / 624.06 | 636.09 / 645.40 | 0.980 / 0.967 |
| D | 128 | 974.94 / 975.76 | 1027.63 / 1034.14 | 0.949 / 0.944 |
| D | 512 | 1060.01 / 1065.24 | 1116.36 / 1127.91 | 0.950 / 0.944 |
| D | 4096 | 3026.56 / 3084.37 | 3146.70 / 3202.83 | 0.962 / 0.963 |
| G (H6144, EP8, 8 GPUs) | 8 | 58.63 / 58.62 | 55.98 / 55.97 | 1.047 /
1.047 |
| G | 32 | 92.95 / 93.73 | 92.28 / 92.94 | 1.007 / 1.009 |
| G | 64 | 118.21 / 118.15 | 117.02 / 117.05 | 1.010 / 1.009 |
| G | 128 | 123.31 / 123.33 | 133.62 / 133.65 | 0.923 / 0.923 |
| G | 512 | 134.50 / 134.53 | 133.23 / 133.27 | 1.010 / 1.010 |
| G | 4096 | 317.56 / 317.60 | 310.51 / 310.54 | 1.023 / 1.023 |

FlashInfer also ships the Cake SiTU routed MoE with NVFP4 weights and
with MXFP4 weights × MXFP8 activations (CUDA C++ and CuTe DSL
lowerings), and the Cake warp-decode MoE module; this family ships on
sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a Cake W4A16 option for fused mixture-of-experts workloads with
BF16 activations and NVFP4 expert weights.
* The route selects supported kernels based on workload size and
supports optional per-expert scaling, SwiGLU clamping, and
caller-provided workspace.
* Cake W4A16 options are now supported through the existing SiTU
interface; other options retain their existing behavior.
* Added support for supported Blackwell GPU targets, with graceful
handling of zero-token inputs and routes outside the local expert range.
* Added workspace sizing and preparation options, including lazy
preparation when workspace setup is not performed in advance.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [131f859](https://github.com/flashinfer-ai/flashinfer/commit/131f85942edb00c9258bc6e393ccbe57b88b55bc)

- **作者**: eigen
- **时间**: 2026-10-25T13:46:26Z
- **提交信息**: feat(cake_qsa_nvfp4): persistent-walk decode for SM103 two-wave grids and the tcgen05 one-tile fused merge (#7324)

`flashinfer.sparse.qsa_sparse_paged_attention(..., backend="cake")` runs
gated sparse paged GQA decode attention over an NVFP4 KV cache. It has
one data-type variant (BF16 queries, NVFP4 KV cache, BF16 output), two
KV layouts (NHD, HND), and split and fused forms. This PR adds a
persistent split-form decode for two-wave grids on sm_103a and a
one-tile merge in the tcgen05 fused form (sm_100a, sm_103a, sm_107a).
The baseline is the previous Cake version: the `backend="cake"` package
on upstream main, built for the device, each version using its own host
rules. On GB300, eager calls with one or two rows are 1.10x-1.17x
faster, and calls with 128 rows are 1.06x faster. At four rows the
result is mixed (0.97x-1.14x), and rows 8-64 are unchanged
(0.98x-1.02x). Under CUDA-graph replay, rows 1-64 stay within
0.98x-1.04x and 128 rows are 1.06x-1.07x faster. On B200 the result is a
tie, with every row within 0.97x-1.05x, because these shapes select none
of the new code there.

Speedup of this PR's route (`backend="cake"`) over the previous Cake
version of the same route (the package on upstream main, built for the
device; both arms use the package's own host rules) on NVIDIA GB300 (152
SMs, sm_103a), CUDA 13.4 (torch 2.14.1+cu130, torch CUDA 13.0); whole
call (decode + merge), medians of 3 x 64 cold-L2 samples (memset flush),
eager launches; 24 x 2 heads, 2051 selected tokens per row.

| layout | rows | previous Cake version us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 11.65 | 10.21 | 1.14x |
| NHD | 2 | 12.35 | 11.23 | 1.10x |
| NHD | 4 | 13.55 | 13.73 | 0.99x |
| NHD | 8 | 17.04 | 17.22 | 0.99x |
| NHD | 16 | 17.60 | 17.55 | 1.00x |
| NHD | 32 | 24.93 | 24.77 | 1.01x |
| NHD | 64 | 37.86 | 37.79 | 1.00x |
| NHD | 128 | 71.89 | 67.74 | 1.06x |
| HND | 1 | 11.71 | 10.53 | 1.11x |
| HND | 2 | 14.70 | 12.77 | 1.15x |
| HND | 4 | 15.92 | 13.95 | 1.14x |
| HND | 8 | 18.19 | 18.18 | 1.00x |
| HND | 16 | 18.03 | 17.94 | 1.01x |
| HND | 32 | 25.01 | 25.06 | 1.00x |
| HND | 64 | 37.52 | 37.42 | 1.00x |
| HND | 128 | 72.11 | 67.79 | 1.06x |

The same pair under CUDA-graph replay on NVIDIA GB300 (152 SMs,
sm_103a), CUDA 13.4 (torch 2.14.1+cu130, torch CUDA 13.0); whole call
(decode + merge), medians of 3 x 64 cold-L2 samples (memset flush),
CUDA-graph replay of each arm's whole call; 24 x 2 heads, 2051 selected
tokens per row.

| layout | rows | previous Cake version us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 10.08 | 9.84 | 1.02x |
| NHD | 2 | 10.54 | 10.40 | 1.01x |
| NHD | 4 | 11.62 | 11.47 | 1.01x |
| NHD | 8 | 13.90 | 14.10 | 0.99x |
| NHD | 16 | 17.73 | 17.62 | 1.01x |
| NHD | 32 | 25.31 | 25.28 | 1.00x |
| NHD | 64 | 38.00 | 38.06 | 1.00x |
| NHD | 128 | 72.10 | 67.76 | 1.06x |
| HND | 1 | 10.69 | 10.32 | 1.04x |
| HND | 2 | 10.77 | 11.01 | 0.98x |
| HND | 4 | 12.48 | 12.05 | 1.04x |
| HND | 8 | 14.32 | 14.00 | 1.02x |
| HND | 16 | 17.92 | 18.13 | 0.99x |
| HND | 32 | 25.44 | 25.26 | 1.01x |
| HND | 64 | 37.57 | 37.57 | 1.00x |
| HND | 128 | 72.37 | 67.74 | 1.07x |

Speedup of this PR's route (`backend="cake"`) over the previous Cake
version of the same route (the package on upstream main, built for the
device; both arms use the package's own host rules) on NVIDIA GB300 (152
SMs, sm_103a), CUDA 13.4 (torch 2.14.1+cu130, torch CUDA 13.0); whole
call (decode + merge), medians of 3 x 64 cold-L2 samples (read flush),
eager launches; 24 x 2 heads, 2051 selected tokens per row.

| layout | rows | previous Cake version us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 11.70 | 10.02 | 1.17x |
| NHD | 2 | 11.94 | 10.67 | 1.12x |
| NHD | 4 | 12.66 | 12.90 | 0.98x |
| NHD | 8 | 17.36 | 17.63 | 0.98x |
| NHD | 16 | 17.09 | 17.28 | 0.99x |
| NHD | 32 | 23.98 | 23.92 | 1.00x |
| NHD | 64 | 37.02 | 37.02 | 1.00x |
| NHD | 128 | 70.58 | 66.64 | 1.06x |
| HND | 1 | 11.81 | 10.16 | 1.16x |
| HND | 2 | 12.02 | 10.54 | 1.14x |
| HND | 4 | 12.74 | 13.12 | 0.97x |
| HND | 8 | 17.92 | 17.57 | 1.02x |
| HND | 16 | 17.95 | 17.66 | 1.02x |
| HND | 32 | 24.03 | 23.90 | 1.01x |
| HND | 64 | 36.48 | 36.62 | 1.00x |
| HND | 128 | 70.54 | 66.67 | 1.06x |

Speedup of this PR's route (`backend="cake"`) over the previous Cake
version of the same route (the package on upstream main, built for the
device; both arms use the package's own host rules) on NVIDIA B200 (148
SMs, sm_100a), CUDA 13.4 (torch 2.14.1+cu130, torch CUDA 13.0); whole
call (decode + merge), medians of 3 x 64 cold-L2 samples (memset flush),
eager launches; 24 x 2 heads, 2051 selected tokens per row.

| layout | rows | previous Cake version us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 10.34 | 10.27 | 1.01x |
| NHD | 2 | 10.98 | 11.07 | 0.99x |
| NHD | 4 | 12.24 | 12.27 | 1.00x |
| NHD | 8 | 14.29 | 14.30 | 1.00x |
| NHD | 16 | 18.21 | 18.19 | 1.00x |
| NHD | 32 | 26.34 | 26.34 | 1.00x |
| NHD | 64 | 40.06 | 40.06 | 1.00x |
| NHD | 128 | 76.34 | 76.29 | 1.00x |
| HND | 1 | 10.51 | 10.46 | 1.00x |
| HND | 2 | 11.15 | 11.25 | 0.99x |
| HND | 4 | 12.45 | 12.54 | 0.99x |
| HND | 8 | 14.40 | 14.48 | 0.99x |
| HND | 16 | 18.45 | 18.46 | 1.00x |
| HND | 32 | 26.38 | 26.42 | 1.00x |
| HND | 64 | 39.82 | 39.70 | 1.00x |
| HND | 128 | 76.29 | 76.18 | 1.00x |

The same pair under CUDA-graph replay on NVIDIA B200 (148 SMs, sm_100a),
CUDA 13.4 (torch 2.14.1+cu130, torch CUDA 13.0); whole call (decode +
merge), medians of 3 x 64 cold-L2 samples (memset flush), CUDA-graph
replay of each arm's whole call; 24 x 2 heads, 2051 selected tokens per
row.

| layout | rows | previous Cake version us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 10.18 | 9.98 | 1.02x |
| NHD | 2 | 10.67 | 11.04 | 0.97x |
| NHD | 4 | 12.21 | 12.59 | 0.97x |
| NHD | 8 | 14.62 | 14.21 | 1.03x |
| NHD | 16 | 18.29 | 18.61 | 0.98x |
| NHD | 32 | 26.35 | 26.26 | 1.00x |
| NHD | 64 | 40.13 | 40.16 | 1.00x |
| NHD | 128 | 76.11 | 76.22 | 1.00x |
| HND | 1 | 10.48 | 10.66 | 0.98x |
| HND | 2 | 11.81 | 11.23 | 1.05x |
| HND | 4 | 12.46 | 12.53 | 0.99x |
| HND | 8 | 14.43 | 14.86 | 0.97x |
| HND | 16 | 18.83 | 18.45 | 1.02x |
| HND | 32 | 26.34 | 26.78 | 0.98x |
| HND | 64 | 39.66 | 39.76 | 1.00x |
| HND | 128 | 76.32 | 76.43 | 1.00x |

Speedup of this PR's route (`backend="cake"`) over the previous Cake
version of the same route (the package on upstream main, built for the
device; both arms use the package's own host rules) on NVIDIA B200 (148
SMs, sm_100a), CUDA 13.4 (torch 2.14.1+cu130, torch CUDA 13.0); whole
call (decode + merge), medians of 3 x 64 cold-L2 samples (read flush),
eager launches; 24 x 2 heads, 2051 selected tokens per row.

| layout | rows | previous Cake version us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 10.08 | 10.03 | 1.00x |
| NHD | 2 | 10.42 | 10.46 | 1.00x |
| NHD | 4 | 11.58 | 11.54 | 1.00x |
| NHD | 8 | 13.30 | 13.36 | 1.00x |
| NHD | 16 | 17.38 | 17.36 | 1.00x |
| NHD | 32 | 25.70 | 25.68 | 1.00x |
| NHD | 64 | 39.60 | 39.54 | 1.00x |
| NHD | 128 | 75.87 | 75.84 | 1.00x |
| HND | 1 | 10.08 | 9.98 | 1.01x |
| HND | 2 | 10.46 | 10.56 | 0.99x |
| HND | 4 | 11.74 | 11.66 | 1.01x |
| HND | 8 | 13.41 | 13.38 | 1.00x |
| HND | 16 | 17.41 | 17.41 | 1.00x |
| HND | 32 | 25.79 | 25.70 | 1.00x |
| HND | 64 | 39.20 | 39.30 | 1.00x |
| HND | 128 | 75.71 | 75.66 | 1.00x |

Other Cake variants are the mma.sync decode (plain, fused; whole-tile on
sm_80) on sm_80/sm_90a/sm_120a, the tcgen05 decode (plain, fused) on
sm_100a/sm_103a/sm_107a, and the merge.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for NVFP4 QSA workloads on GB300-class hardware with
CUDA 12.9.
* Qualifying workloads can now use an optimized decode path that
balances work across GPU processing units; other workloads continue
using the existing path.
* **Bug Fixes**
* Improved decode-path selection and launch validation to avoid
unsupported configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [8471725](https://github.com/flashinfer-ai/flashinfer/commit/847172573ad1d5a929a8e7fb67aa7c072f8f7dcb)

- **作者**: eigen
- **时间**: 2026-10-25T13:20:35Z
- **提交信息**: feat(cake_deepgemm_mega_mhc): hidden-4096 mHC inference programs for SM100 and SM103 (#7321)

This PR adds Cake's kernel for the hidden-size-4096, four-route mHC
(manifold-constrained hyper-connection) inference step that
GLM-5.3-Flash uses in vLLM. One persistent launch runs post mixing, the
BF16x3 split-K mapping projection, 20 Sinkhorn iterations, collapse and
the input RMSNorm, and writes BF16 outputs. The kernel has five programs
per architecture: the plain bf16 program, the tailpipe and
tailpipe_wsmem fused forms that the host rule selects by token count,
and the fp8_group128 and nvfp4 quantized-output variants. This PR
delivers all five for sm_100a (B200) and sm_103a (GB300) through
`flashinfer.mega_mhc.prepare_mega_mhc`, and because no previous Cake
version exists on these architectures, the baseline is vLLM's existing
`MHCFusedPostPreOp.forward_cuda` default dispatch, measured as the
kernel-sum of its dispatched kernel sequence on the same GPU with the
same inputs.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4.** Latency in µs, CUPTI
kernel-sum, cold L2, median of 3 ABBA groups × 64 launches; speedup =
vLLM µs / Cake µs.

| tokens T | Cake µs | vLLM µs | speedup |
|---:|---:|---:|---:|
| 1 | 11.104 | 12.305 | 1.108 |
| 4 | 11.680 | 12.135 | 1.039 |
| 8 | 11.681 | 12.130 | 1.038 |
| 16 | 12.064 | 12.640 | 1.048 |
| 32 | 12.032 | 13.525 | 1.124 |
| 64 | 12.672 | 16.160 | 1.275 |
| 128 | 13.408 | 16.840 | 1.256 |
| 256 | 15.857 | 18.995 | 1.198 |
| 512 | 19.648 | 23.885 | 1.216 |
| 1024 | 27.424 | 39.095 | 1.426 |
| 2048 | 46.177 | 62.760 | 1.359 |
| 4096 | 86.913 | 118.465 | 1.363 |
| 8192 | 174.817 | 219.300 | 1.254 |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4.** Latency in µs, CUPTI
kernel-sum, cold L2, median of 3 ABBA groups × 64 launches; speedup =
vLLM µs / Cake µs.

| tokens T | Cake µs | vLLM µs | speedup |
|---:|---:|---:|---:|
| 1 | 10.432 | 11.480 | 1.100 |
| 4 | 10.592 | 11.030 | 1.041 |
| 8 | 10.720 | 11.350 | 1.059 |
| 16 | 10.872 | 11.895 | 1.094 |
| 32 | 11.168 | 12.700 | 1.137 |
| 64 | 11.488 | 14.730 | 1.282 |
| 128 | 12.824 | 15.120 | 1.179 |
| 256 | 14.968 | 17.295 | 1.155 |
| 512 | 17.975 | 21.855 | 1.216 |
| 1024 | 25.608 | 35.510 | 1.387 |
| 2048 | 42.728 | 58.240 | 1.363 |
| 4096 | 79.744 | 109.945 | 1.379 |
| 8192 | 161.871 | 208.755 | 1.290 |

Cake also ships the same five programs for sm_107a, which this PR leaves
unchanged, and the hidden-5120 programs for sm_100a and sm_103a are also
unchanged.

Closes #7318


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for SM100a and SM103a GPUs for hidden-4096 examples and
programs, alongside SM107a.
* Quantized hidden-4096 layouts now use an adjusted split count in
qualifying cases; deterministic mode and BF16 output retain their
existing split-count behavior.
* **Tests**
* Expanded coverage for architecture support and split-count behavior
across quantized and BF16 layouts.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a47e170](https://github.com/flashinfer-ai/flashinfer/commit/a47e1701a0e01693e7a24f63439a11bf7ffe6184)

- **作者**: eigen
- **时间**: 2026-10-25T12:44:44Z
- **提交信息**: docs(cake_kimi_k3_tp12_tail): the fused K23 tail serves up to eight tokens (#7316)

Docs only. `K23_MAX_TOKENS` is 8 (accumulator capacities 4 and 8), so
the up-projection is fused into the tail kernel for `M <= 8` and the
early-shared-scatter tail starts at nine tokens. Three docstring and
comment ranges in the `kimi_k3_tp12_tail` package still said four; this
follows up the review comment on `cake_jit.py` in #7310.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Updated the Kimi K3 TP12 tail-kernel guidance to describe the fused
tail-kernel and output-column CTA paths as applying when `M <= 8`.
* Clarified that the grouped ESS path serves `8 < M <= 960` after an ESS
K1. Documentation for the cuBLAS, token-based CTA, and
persistent-token-pipeline paths remains unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [506fac6](https://github.com/flashinfer-ai/flashinfer/commit/506fac6203ae3b3ce1852c13a41654ab22478b0d)

- **作者**: Yang Xu
- **时间**: 2026-10-25T12:36:34Z
- **提交信息**: perf(cudnn): cache prefill shape-override version support (#7317)

<!-- .github/pull_request_template.md -->

## 📌 Description

Repeated cuDNN prefill capability checks query the same installed
backend version and parse the same frontend version on every call. Cache
`_cudnn_version_supports_shape_override()` with `functools.cache`,
consistent with the neighboring version capability predicates.

`FLASHINFER_CUDNN_PREFILL_SHAPE_OVERRIDE` remains dynamic:
`_cudnn_supports_shape_override()` still reads it on each call. This
caches only a process-wide version predicate; it does not cache tensors,
pointers, plans, or runtime arguments.

CPU-only warm-call measurement on AMD EPYC 9554, Python 3.12.12,
released cuDNN Frontend 1.31.0 and backend 9.27.0:

| Call | Before | After |
| --- | ---: | ---: |
| Version predicate | 0.897 µs | 0.072 µs |
| Including the environment-switch check | 1.890 µs | 1.023 µs |

These are capability-query costs, not end-to-end `plan()`/`run()`, GPU
replay, or serving speedups. CUDA was not initialized. The measurement
compares the cached callable with its original `__wrapped__` body in one
process, pinned to one CPU, with four ABBA cycles and seven samples of
20,000 calls per metric per block.

## 🔍 Related Issues

No issue required. Independent of the pending prefill PR stack; based
directly on `main` at `4796d2eff`.

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

Changed-file validation passed: `pre-commit run --files
flashinfer/cudnn/prefill.py` (including mypy, Ruff, formatting, and
repository file checks) and `git diff --check`. The full-repository
hooks and GPU suite have not been run locally.

## 🧪 Tests

- [x] Tests have been added or updated as needed. No new test file for
this one-line cache annotation; focused CPU checks are described below.
- [ ] All tests are passing (`unittest`, etc.). Focused checks pass; GPU
CI is pending.

Seven focused checks passed against the imported modified module:
supported version floor, current released versions, old backend, old
frontend, missing cuDNN, malformed frontend version, and backend-version
query failure. Each checks repeated calls and disable/re-enable of the
environment switch after warming the cache. The version query executes
once when cuDNN is available; the environment switch remains effective
without clearing the cache. Actual FlashInfer/cuDNN import paths were
verified. The existing cuDNN wrapper, prepared-contract, and ragged
shape-override suites are the intended CI coverage.

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

The installed library versions are treated as immutable for the process,
as in the adjacent cached capability checks. This also caches an
unsupported/error result; code that deliberately replaces the loaded
library in-process would need to clear the private cache, as with those
neighboring predicates.

GPU/tensor configuration: not applicable to this CPU-only capability
check. No kernel, dispatch threshold, or public API changes. The
reported numbers do not establish a GPU or serving gain.

<details>
<summary>Reproduce the CPU measurement on the PR head with FE ≥ 1.29 and
backend ≥ 9.22</summary>

Run with `CUDA_VISIBLE_DEVICES=''` and a compatible FlashInfer/cuDNN
installation. CPU affinity uses Linux `sched_setaffinity`.

```python
import os
import statistics
import time
from flashinfer.cudnn import prefill as p

os.sched_setaffinity(0, {min(os.sched_getaffinity(0))})
os.environ.pop('FLASHINFER_CUDNN_PREFILL_SHAPE_OVERRIDE', None)
cached = p._cudnn_version_supports_shape_override
uncached = cached.__wrapped__  # The exact function body before this PR.
assert cached() and uncached()
results = []
try:
    for mode in ['uncached', 'cached', 'cached', 'uncached'] * 4:
        query = cached if mode == 'cached' else uncached
        p._cudnn_version_supports_shape_override = query
        row = {'mode': mode}
        for name, call in [('version', query), ('env_gate', p._cudnn_supports_shape_override)]:
            for _ in range(1000):
                call()
            samples = []
            for _ in range(7):
                start = time.perf_counter_ns()
                for _ in range(20000):
                    call()
                samples.append((time.perf_counter_ns() - start) / 20000 / 1000)
            row[name] = statistics.median(samples)
        results.append(row)
finally:
    p._cudnn_version_supports_shape_override = cached
for name in ['version', 'env_gate']:
    print(name, {mode: statistics.median(r[name] for r in results if r['mode'] == mode)
                 for mode in ['uncached', 'cached']}, 'us/call')
```

</details>


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Repeated checks for cuDNN shape-override support are now more
efficient. This internal optimization does not change the behavior or
availability of cuDNN features.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b412544](https://github.com/flashinfer-ai/flashinfer/commit/b4125442a53382fad96d08bbf3eda580c9d58a02)

- **作者**: eigen
- **时间**: 2026-10-25T12:14:50Z
- **提交信息**: perf(cake_minimax_h3): N-split tail for the NVFP4 out-projection GEMM on SM100/SM103 (#7314)

`flashinfer.diffusion_ops.minimax_h3_out_proj` (BF16),
`minimax_h3_out_proj_mxfp8` (MXFP8 W8A8) and `minimax_h3_out_proj_nvfp4`
(NVFP4 W4A4) are the three variants of the MiniMax-H3 attention output
projection with the fused indexed gate and residual on SM100 (`sm_100a`)
and SM103 (`sm_103a`). The quantized variants run an
activation-quantization pass, then a persistent block-scaled GEMM with
the fused epilogue. This PR changes only the NVFP4 variant (E2M1 data,
UE4M3 block-16 scales and a global scale) on SM100 and SM103. Some
shapes have at least 32 rows and a partial last wave that fits in half a
wave, within 48 waves (SM103) or 10 waves (SM100). For those shapes, the
GEMM now runs the tail tiles as half-width units (256 x 128 output
columns), so the partial last wave costs about half a tile. Every other
shape runs the unchanged kernel. The output is bitwise identical to
main. Compared with the current main `minimax_h3_out_proj_nvfp4`, the
tail-split shapes in the 40-shape list are 1.003x to 1.041x faster on
GB300 (20 shapes, geomean 1.021x) and 1.017x to 1.052x faster on GB200
(7 shapes, geomean 1.042x).

NVIDIA GB300 (`sm_103a`), CUDA 13.4. Time of the complete operator
(activation quantization + GEMM), median of 10 interleaved rounds (5
rounds in each of two sessions) with a cold L2. P = sequence-parallel
degree, M = rows. Rows with tail split = yes run the new tail schedule.
The other rows run the unchanged kernel in both columns, so their ratio
is run-to-run variation.

| P | M | tail split | before (µs) | after (µs) | speedup |
|---:|---:|:---:|---:|---:|---:|
| 1 | 33472 | yes | 469.5 | 467.9 | 1.003x |
| 1 | 38528 | no | 539.9 | 540.6 | 0.999x |
| 1 | 38591 | no | 540.6 | 541.1 | 0.999x |
| 1 | 38592 | no | 540.1 | 540.1 | 1.000x |
| 1 | 38593 | no | 539.6 | 540.6 | 0.998x |
| 1 | 38656 | no | 540.7 | 540.9 | 1.000x |
| 1 | 48768 | no | 685.2 | 687.4 | 0.997x |
| 1 | 58944 | no | 830.3 | 834.4 | 0.995x |
| 1 | 74240 | no | 1050.4 | 1048.7 | 1.002x |
| 1 | 109952 | no | 1583.4 | 1587.4 | 0.997x |
| 2 | 16736 | yes | 240.0 | 237.6 | 1.010x |
| 2 | 19264 | no | 272.7 | 272.7 | 1.000x |
| 2 | 19295 | no | 272.8 | 272.5 | 1.001x |
| 2 | 19296 | no | 273.3 | 273.2 | 1.001x |
| 2 | 19297 | no | 272.8 | 272.7 | 1.000x |
| 2 | 19328 | no | 272.5 | 272.5 | 1.000x |
| 2 | 24384 | no | 344.5 | 344.4 | 1.000x |
| 2 | 29472 | yes | 417.9 | 414.3 | 1.009x |
| 2 | 37120 | yes | 520.7 | 518.9 | 1.004x |
| 2 | 54976 | no | 775.2 | 777.4 | 0.997x |
| 4 | 8368 | yes | 129.7 | 126.0 | 1.029x |
| 4 | 9632 | yes | 143.8 | 141.8 | 1.014x |
| 4 | 9647 | yes | 143.7 | 141.8 | 1.013x |
| 4 | 9648 | yes | 144.0 | 141.7 | 1.016x |
| 4 | 9649 | yes | 143.7 | 141.8 | 1.013x |
| 4 | 9664 | yes | 144.0 | 142.0 | 1.014x |
| 4 | 12192 | yes | 178.4 | 175.0 | 1.020x |
| 4 | 14736 | yes | 214.1 | 210.4 | 1.018x |
| 4 | 18560 | yes | 265.2 | 261.4 | 1.014x |
| 4 | 27488 | no | 385.4 | 386.5 | 0.997x |
| 8 | 4184 | no | 72.6 | 72.6 | 1.000x |
| 8 | 4816 | yes | 82.2 | 79.0 | 1.041x |
| 8 | 4823 | yes | 82.2 | 79.0 | 1.041x |
| 8 | 4824 | yes | 82.8 | 79.5 | 1.041x |
| 8 | 4825 | yes | 82.3 | 79.2 | 1.040x |
| 8 | 4832 | yes | 82.3 | 79.1 | 1.040x |
| 8 | 6096 | no | 96.9 | 96.9 | 1.000x |
| 8 | 7368 | yes | 116.4 | 112.8 | 1.031x |
| 8 | 9280 | yes | 140.2 | 137.7 | 1.018x |
| 8 | 13744 | no | 196.9 | 196.8 | 1.001x |

NVIDIA GB200 (`sm_100a`), CUDA 13.4. Time of the complete operator
(activation quantization + GEMM), median of 10 interleaved rounds (5
rounds in each of two sessions) with a cold L2. P = sequence-parallel
degree, M = rows. Rows with tail split = yes run the new tail schedule.
The other rows run the unchanged kernel in both columns, so their ratio
is run-to-run variation.

| P | M | tail split | before (µs) | after (µs) | speedup |
|---:|---:|:---:|---:|---:|---:|
| 1 | 33472 | no | 602.6 | 600.6 | 1.003x |
| 1 | 38528 | no | 691.8 | 703.5 | 0.983x |
| 1 | 38591 | no | 697.4 | 701.5 | 0.994x |
| 1 | 38592 | no | 705.1 | 699.5 | 1.008x |
| 1 | 38593 | no | 696.0 | 683.7 | 1.018x |
| 1 | 38656 | no | 704.6 | 706.7 | 0.997x |
| 1 | 48768 | no | 880.2 | 897.8 | 0.980x |
| 1 | 58944 | no | 1082.6 | 1090.2 | 0.993x |
| 1 | 74240 | no | 1379.0 | 1373.3 | 1.004x |
| 1 | 109952 | no | 2070.7 | 2076.7 | 0.997x |
| 2 | 16736 | no | 297.5 | 300.0 | 0.992x |
| 2 | 19264 | no | 345.2 | 344.6 | 1.002x |
| 2 | 19295 | no | 344.2 | 345.1 | 0.997x |
| 2 | 19296 | no | 345.6 | 342.8 | 1.008x |
| 2 | 19297 | no | 344.5 | 343.3 | 1.003x |
| 2 | 19328 | no | 345.0 | 344.4 | 1.002x |
| 2 | 24384 | no | 433.8 | 433.0 | 1.002x |
| 2 | 29472 | no | 528.8 | 529.1 | 1.000x |
| 2 | 37120 | no | 666.8 | 662.5 | 1.007x |
| 2 | 54976 | no | 1012.8 | 1015.0 | 0.998x |
| 4 | 8368 | yes | 157.6 | 155.0 | 1.017x |
| 4 | 9632 | no | 176.8 | 176.9 | 0.999x |
| 4 | 9647 | no | 176.0 | 176.0 | 1.000x |
| 4 | 9648 | no | 177.4 | 177.7 | 0.998x |
| 4 | 9649 | no | 176.3 | 176.1 | 1.001x |
| 4 | 9664 | no | 176.3 | 176.9 | 0.996x |
| 4 | 12192 | no | 221.8 | 221.2 | 1.003x |
| 4 | 14736 | no | 265.5 | 265.5 | 1.000x |
| 4 | 18560 | no | 333.2 | 330.7 | 1.008x |
| 4 | 27488 | no | 489.5 | 489.5 | 1.000x |
| 8 | 4184 | no | 84.0 | 84.1 | 0.998x |
| 8 | 4816 | yes | 98.2 | 93.4 | 1.052x |
| 8 | 4823 | yes | 98.7 | 93.8 | 1.052x |
| 8 | 4824 | yes | 98.2 | 93.6 | 1.049x |
| 8 | 4825 | yes | 98.7 | 94.0 | 1.050x |
| 8 | 4832 | yes | 98.7 | 93.9 | 1.051x |
| 8 | 6096 | no | 116.1 | 116.1 | 1.000x |
| 8 | 7368 | yes | 140.7 | 137.5 | 1.023x |
| 8 | 9280 | no | 172.4 | 172.0 | 1.002x |
| 8 | 13744 | no | 245.5 | 245.6 | 1.000x |

On SM120 (`sm_120a`), a separate module,
`flashinfer.diffusion_ops.cake_minimax_h3_sm120_quant_out_proj`, ships
FP8 (per-token) and NVFP4 variants; this PR does not change the BF16 and
MXFP8 out-projection variants, and the family covers `sm_100a`,
`sm_103a` and `sm_120a`.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [09a7750](https://github.com/flashinfer-ai/flashinfer/commit/09a77503f004b8f36a38d23074fc5da6877de811)

- **作者**: eigen
- **时间**: 2026-10-25T12:14:11Z
- **提交信息**: feat(cake_qsa_nvfp4): mma.sync decode programs and the merge for SM120 (#7313)

This PR adds SM120 support to the Cake backend for QSA NVFP4 decode,
`flashinfer.experimental.cake_qsa_nvfp4`. Callers reach it through
`flashinfer.sparse.qsa_sparse_paged_attention(..., backend="cake")`, and
the default `backend="auto"` picks it on the supported compute
capabilities. The kernel runs gated sparse paged GQA decode attention of
BF16 queries over an NVFP4 paged KV cache. The shape is Hq 24 / Hkv 2 /
D 256, with 2051 selected tokens per row in 64-token tiles and page 16.
It supports two KV layouts (NHD and HND) and two call forms: split
(decode + merge) and fused (cooperative decode alone). Six programs
serve these forms:

- the mma.sync K-first decode
- its whole-tile build
- the mma.sync cooperative decode, which merges its splits in the launch
(the fused form)
- the tcgen05 decode
- the tcgen05 cooperative decode
- the split-KV merge

This PR delivers the SM120 (compute capability 12.0) libraries of the
plain and cooperative mma.sync decodes and of the merge. The SM120 part
has no tcgen05 instructions and no tensor memory, so the mma.sync
programs serve it. Compute capabilities 8.x, 9.0, 10.0, 10.3 and 10.7
were delivered before; 12.1 is not covered.

No Cake version of the kernel ran on SM120 before this PR. The baseline
is therefore FlashInfer's existing `qsa_nvfp4` implementation
(`backend="default"`), built for the device, with its host guard
admitting compute capability 12 for the measurement. Both arms time the
whole call (decode + merge). Cake is 1.27x to 1.89x faster with eager
launches and 1.21x to 1.90x faster under CUDA-graph replay.

Eager launches on an NVIDIA RTX PRO 6000 Blackwell Server Edition (188
SMs, sm_120a) with CUDA 13.4 (torch 2.14.1+cu130): medians of 3 x 64
samples with a cold-L2 memset flush between samples, over rows 1 / 2 / 4
/ 8 / 16 / 32 / 64 / 128 x layouts NHD / HND, 24 x 2 heads and 2051
selected tokens per row.

| layout | rows | FlashInfer reference us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 16.22 | 11.82 | 1.37x |
| NHD | 2 | 21.70 | 16.99 | 1.28x |
| NHD | 4 | 28.59 | 16.13 | 1.77x |
| NHD | 8 | 39.06 | 22.53 | 1.73x |
| NHD | 16 | 53.78 | 35.34 | 1.52x |
| NHD | 32 | 73.38 | 57.82 | 1.27x |
| NHD | 64 | 132.83 | 99.65 | 1.33x |
| NHD | 128 | 301.26 | 161.36 | 1.87x |
| HND | 1 | 17.14 | 12.61 | 1.36x |
| HND | 2 | 22.46 | 17.55 | 1.28x |
| HND | 4 | 28.26 | 16.18 | 1.75x |
| HND | 8 | 40.58 | 23.39 | 1.73x |
| HND | 16 | 55.54 | 35.87 | 1.55x |
| HND | 32 | 79.38 | 59.73 | 1.33x |
| HND | 64 | 152.75 | 101.81 | 1.50x |
| HND | 128 | 320.93 | 169.62 | 1.89x |

The same two arms on the same GPU (sm_120a, CUDA 13.4) with the same
shapes, sampling and cold-L2 memset flush, but with each arm's whole
call replayed from a CUDA graph instead of launched eagerly.

| layout | rows | FlashInfer reference us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 16.29 | 12.74 | 1.28x |
| NHD | 2 | 21.76 | 17.95 | 1.21x |
| NHD | 4 | 28.54 | 17.49 | 1.63x |
| NHD | 8 | 38.00 | 24.22 | 1.57x |
| NHD | 16 | 52.58 | 36.30 | 1.45x |
| NHD | 32 | 74.54 | 59.39 | 1.26x |
| NHD | 64 | 132.77 | 100.69 | 1.32x |
| NHD | 128 | 300.91 | 162.66 | 1.85x |
| HND | 1 | 17.15 | 13.98 | 1.23x |
| HND | 2 | 22.91 | 18.99 | 1.21x |
| HND | 4 | 28.62 | 17.36 | 1.65x |
| HND | 8 | 40.38 | 24.72 | 1.63x |
| HND | 16 | 55.36 | 37.04 | 1.49x |
| HND | 32 | 79.71 | 61.17 | 1.30x |
| HND | 64 | 152.22 | 103.84 | 1.47x |
| HND | 128 | 321.59 | 169.10 | 1.90x |

The kernel's other Cake variants are the tcgen05 plain and cooperative
decodes (SM100 / SM103 / SM107) and the SM80 whole-tile build; the
family ships for sm_80, sm_90a, sm_100a, sm_103a, sm_107a and sm_120a,
and the fused form runs on 9.0 and 12.0 within the device's co-resident
capacity, on 10.0 / 10.3 on aarch64 hosts at rows <= 4 outside a stream
capture, while 10.7 keeps the split form.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Cake QSA NVFP4 attention now supports NVIDIA compute capability 12.0,
including RTX PRO 6000. Automatic backend selection can choose Cake on
supported 12.0 GPUs, with split and fused execution options.
* Architecture matching is exact: capability 12.1 is not included and
continues to use the reference implementation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [68e3e09](https://github.com/flashinfer-ai/flashinfer/commit/68e3e09ad3a52cbbd6b39d159d2fad7d1653073d)

- **作者**: eigen
- **时间**: 2026-10-25T11:40:07Z
- **提交信息**: perf(cake_comm): pipelined, topology-weighted PCIe CE ring all-reduce on SM120 (#7301)

The PCIe IPC all-reduce workspace in `flashinfer.comm` (bf16/fp16, 2, 4
and 8 ranks on PCIe-only machines) has eight launch schedules, and the
library's tuner picks one per shape. This PR adds the eighth: a
pipelined, topology-weighted copy-engine ring
(`IpcVariant.COPY_ENGINE_RING_PIPED`) for SM120 (compute capability
12.0) groups of 4 or 8 ranks, which the tuner offers only when each
rank's chunk is at least 4 MiB. On the shapes where the tuner selects
it, the all-reduce is 1.004–1.111x faster; on the other shapes it runs
the same schedule as before. The baseline is the previous Cake version
(FlashInfer main before this PR), using the fastest configuration among
its existing schedules for each shape.

| TP | dtype | MiB per rank | Baseline config | Baseline (ms) | This PR
config | This PR (ms) | Speedup |
|---:|:---|---:|:---|---:|:---|---:|---:|
| 8 | bf16 | 12 | RING_MEMOP, 1 | 0.6038 | same | 0.6008 | same schedule
|
| 8 | bf16 | 24 | RING_MEMOP, 1 | 1.1169 | same | 1.1102 | same schedule
|
| 8 | bf16 | 48 | RING_MEMOP, 1 | 2.1832 | RING_PIPED, 2 | 2.0792 |
1.050x |
| 8 | bf16 | 96 | RING_MEMOP, 1 | 4.4753 | RING_PIPED, 3 | 4.0287 |
1.111x |
| 8 | fp16 | 12 | RING_MEMOP, 1 | 0.6056 | same | 0.6001 | same schedule
|
| 8 | fp16 | 24 | RING_MEMOP, 1 | 1.1213 | same | 1.1252 | same schedule
|
| 8 | fp16 | 48 | RING_MEMOP, 1 | 2.1986 | RING_PIPED, 2 | 2.0990 |
1.047x |
| 8 | fp16 | 96 | RING_MEMOP, 1 | 4.5031 | RING_PIPED, 3 | 4.0560 |
1.110x |
| 4 | bf16 | 12 | RING_MEMOP, 1 | 0.4084 | same | 0.4077 | same schedule
|
| 4 | bf16 | 24 | RING_MEMOP, 1 | 0.7807 | RING_PIPED, 2 | 0.7605 |
1.027x |
| 4 | bf16 | 48 | RING, 2 | 1.4864 | same | 1.4791 | same schedule |
| 4 | bf16 | 96 | RING, 2 | 2.9482 | RING_PIPED, 2 | 2.9358 | 1.004x |
| 4 | fp16 | 12 | RING_MEMOP, 1 | 0.4089 | same | 0.4086 | same schedule
|
| 4 | fp16 | 24 | RING_MEMOP, 1 | 0.7816 | RING_PIPED, 2 | 0.7640 |
1.023x |
| 4 | fp16 | 48 | RING, 2 | 1.4907 | RING_PIPED, 2 | 1.4768 | 1.009x |
| 4 | fp16 | 96 | RING, 2 | 2.9637 | RING_PIPED, 4 | 2.9274 | 1.012x |

*Latency per all-reduce call on 8x SM120 (compute capability 12.0) PCIe
Gen5 GPUs across two CPU sockets, CUDA 13.0; median over 8
single-workspace processes per side, baseline and this PR alternating;
config = `IpcVariant.COPY_ENGINE_<name>`, pieces per chunk; speedup =
baseline / this PR.*

The four SM-path schedules (unstaged, staged, staged ring, flat staged),
the copy-engine flat ring and the 4+4 island build for every
architecture FlashInfer targets, while the two copy-engine rings that
publish through stream memory operations (the single-piece ring and this
pipelined ring) run only on SM120.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a pipelined copy-engine ring option for supported 4- and 8-rank
configurations, with topology-aware slow-hop settings.
* Added optional `ce_slow_hops` configuration when creating an
all-reduce workspace.
* Autotuning can select the new option when hardware and payload size
meet its requirements.
* **Bug Fixes**
* Improved validation of ring configuration, payload size, and supported
operation settings.
* **Tests**
* Expanded coverage for ring geometry, topology masks, tuning, workspace
sizing, and graph replay.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [1c0d2be](https://github.com/flashinfer-ai/flashinfer/commit/1c0d2be434d6d57ca16a428d439c433b8b1e6f81)

- **作者**: eigen
- **时间**: 2026-10-25T11:34:59Z
- **提交信息**: perf(cake_kimi_k3_latent_moe): evict-first decode weights and a claimed-item resident TP1 tail GEMM (#7312)

This PR updates the Cake programs for the Kimi-K3 Stable LatentMoE front
and tail projections of one rank (BF16, `sm_100a` and `sm_103a`). The
front computes router logits and the latent down and shared-expert
gate/up projections; the tail runs RMSNorm and the latent up and
shared-expert down projections. Each projection has a TP1 and a TP8
variant. For T ≤ 128 tokens, each variant runs one weight-streaming
tcgen05 launch. For T > 128, it runs a persistent 2-CTA GEMM, and the
tail first runs a one-pass RMSNorm. Speedup is previous / this PR,
against the previous Cake version: the Cake programs currently on
FlashInfer main. For T ≤ 128, the front and TP1 tail programs now stream
weights with an evict-first L2 policy, so activations stay in L2. At
1-128 tokens, front rows show 1.079-1.201x and TP1 tail rows show
1.156-1.191x. From 1024 tokens up, the TP1 tail runs a new resident GEMM
with fused RMSNorm, where CTA pairs claim work items from a device
counter. A 256x512 tile form serves the largest rows. These rows
(1024-16384 tokens) show 1.028-1.121x. The other 31 rows run the same
programs as before: front 256-16384 tokens, TP1 tail 256 and 512 tokens,
and all TP8 tail rows. Their ratios (0.981-1.012x) are run-to-run
variation. All ranges cover the four GPUs in the table; tail rows reduce
one routed partial.

| Projection | TP | Tokens | B200 previous (µs) | B200 this PR (µs) |
B200 speedup | B300 previous (µs) | B300 this PR (µs) | B300 speedup |
GB200 previous (µs) | GB200 this PR (µs) | GB200 speedup | GB300
previous (µs) | GB300 this PR (µs) | GB300 speedup |
|:--|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|
| front | 1 | 1 | 50.37 | 43.34 | 1.162x | 49.92 | 42.59 | 1.172x |
48.38 | 41.41 | 1.168x | 48.85 | 41.74 | 1.170x |
| front | 1 | 2 | 50.46 | 43.44 | 1.162x | 50.02 | 42.69 | 1.172x |
48.51 | 41.34 | 1.173x | 48.99 | 41.89 | 1.170x |
| front | 1 | 4 | 50.58 | 43.65 | 1.159x | 50.02 | 42.74 | 1.170x |
48.54 | 41.41 | 1.172x | 48.94 | 41.86 | 1.169x |
| front | 1 | 8 | 50.46 | 43.52 | 1.160x | 50.02 | 42.70 | 1.171x |
48.51 | 41.41 | 1.172x | 48.93 | 41.83 | 1.170x |
| front | 1 | 16 | 50.93 | 43.84 | 1.162x | 50.26 | 43.02 | 1.168x |
48.93 | 41.92 | 1.167x | 49.25 | 42.13 | 1.169x |
| front | 1 | 32 | 50.93 | 43.33 | 1.175x | 51.15 | 43.30 | 1.181x |
49.60 | 42.05 | 1.180x | 50.32 | 42.61 | 1.181x |
| front | 1 | 64 | 53.66 | 44.91 | 1.195x | 54.02 | 44.98 | 1.201x |
52.38 | 43.78 | 1.197x | 53.07 | 44.18 | 1.201x |
| front | 1 | 128 | 58.67 | 50.08 | 1.172x | 58.78 | 50.06 | 1.174x |
59.01 | 50.69 | 1.164x | 58.10 | 49.02 | 1.185x |
| front | 1 | 256 | 52.24 | 52.22 | 1.000x | 52.35 | 52.34 | 1.000x |
56.19 | 56.26 | 0.999x | 50.40 | 50.40 | 1.000x |
| front | 1 | 512 | 89.07 | 89.09 | 1.000x | 80.48 | 80.44 | 1.000x |
98.82 | 98.88 | 0.999x | 75.28 | 75.25 | 1.000x |
| front | 1 | 1024 | 172.10 | 173.12 | 0.994x | 163.44 | 163.63 | 0.999x
| 173.57 | 174.14 | 0.997x | 134.66 | 134.72 | 1.000x |
| front | 1 | 2048 | 335.53 | 335.49 | 1.000x | 317.67 | 318.06 | 0.999x
| 315.75 | 316.58 | 0.997x | 255.22 | 255.43 | 0.999x |
| front | 1 | 4096 | 691.89 | 691.66 | 1.000x | 663.56 | 664.45 | 0.999x
| 632.54 | 633.12 | 0.999x | 524.90 | 525.38 | 0.999x |
| front | 1 | 8192 | 1381.36 | 1384.17 | 0.998x | 1364.23 | 1364.65 |
1.000x | 1276.74 | 1279.20 | 0.998x | 1089.78 | 1090.37 | 0.999x |
| front | 1 | 16384 | 2803.08 | 2857.64 | 0.981x | 2741.84 | 2745.92 |
0.999x | 2612.61 | 2610.98 | 1.001x | 2196.90 | 2209.11 | 0.994x |
| front | 8 | 1 | 21.44 | 18.94 | 1.132x | 21.38 | 18.80 | 1.137x |
20.61 | 18.30 | 1.126x | 20.96 | 18.46 | 1.135x |
| front | 8 | 2 | 21.54 | 19.04 | 1.131x | 21.47 | 18.88 | 1.137x |
20.70 | 18.37 | 1.127x | 21.06 | 18.56 | 1.134x |
| front | 8 | 4 | 21.55 | 19.07 | 1.130x | 21.50 | 18.91 | 1.137x |
20.70 | 18.37 | 1.127x | 21.06 | 18.56 | 1.134x |
| front | 8 | 8 | 21.57 | 19.07 | 1.131x | 21.50 | 18.91 | 1.137x |
20.70 | 18.37 | 1.127x | 21.06 | 18.58 | 1.134x |
| front | 8 | 16 | 21.98 | 19.52 | 1.126x | 21.92 | 19.33 | 1.134x |
21.09 | 18.78 | 1.123x | 21.46 | 18.96 | 1.132x |
| front | 8 | 32 | 23.17 | 20.45 | 1.133x | 23.10 | 20.22 | 1.142x |
22.24 | 19.68 | 1.130x | 22.59 | 19.81 | 1.140x |
| front | 8 | 64 | 25.70 | 22.50 | 1.142x | 25.70 | 22.37 | 1.149x |
24.74 | 21.73 | 1.138x | 25.12 | 21.94 | 1.145x |
| front | 8 | 128 | 30.91 | 28.35 | 1.090x | 31.34 | 28.35 | 1.106x |
30.21 | 28.00 | 1.079x | 30.37 | 27.38 | 1.109x |
| front | 8 | 256 | 30.41 | 30.42 | 1.000x | 29.39 | 29.39 | 1.000x |
29.47 | 29.47 | 1.000x | 28.11 | 28.13 | 0.999x |
| front | 8 | 512 | 45.22 | 45.22 | 1.000x | 42.75 | 42.78 | 0.999x |
44.48 | 44.48 | 1.000x | 40.29 | 40.29 | 1.000x |
| front | 8 | 1024 | 67.55 | 67.33 | 1.003x | 64.48 | 64.31 | 1.003x |
77.28 | 77.18 | 1.001x | 60.83 | 60.82 | 1.000x |
| front | 8 | 2048 | 120.83 | 121.09 | 0.998x | 115.68 | 115.63 | 1.000x
| 131.10 | 131.04 | 1.000x | 105.62 | 105.65 | 1.000x |
| front | 8 | 4096 | 238.91 | 238.25 | 1.003x | 232.03 | 231.99 | 1.000x
| 245.22 | 244.26 | 1.004x | 195.31 | 195.49 | 0.999x |
| front | 8 | 8192 | 488.97 | 488.94 | 1.000x | 491.22 | 489.75 | 1.003x
| 474.82 | 474.13 | 1.001x | 393.38 | 393.25 | 1.000x |
| front | 8 | 16384 | 987.57 | 983.73 | 1.004x | 999.45 | 998.99 |
1.000x | 955.43 | 952.23 | 1.003x | 796.51 | 795.99 | 1.001x |
| tail | 1 | 1 | 31.20 | 26.74 | 1.167x | 31.55 | 26.94 | 1.171x | 30.11
| 25.86 | 1.165x | 30.53 | 26.10 | 1.170x |
| tail | 1 | 2 | 31.20 | 26.72 | 1.168x | 31.54 | 26.91 | 1.172x | 30.08
| 25.90 | 1.161x | 30.55 | 26.08 | 1.171x |
| tail | 1 | 4 | 31.39 | 26.85 | 1.169x | 31.71 | 27.04 | 1.173x | 30.21
| 25.97 | 1.163x | 30.67 | 26.18 | 1.172x |
| tail | 1 | 8 | 31.55 | 26.94 | 1.171x | 31.75 | 27.04 | 1.174x | 30.35
| 26.03 | 1.166x | 30.77 | 26.24 | 1.173x |
| tail | 1 | 16 | 33.77 | 28.96 | 1.166x | 33.63 | 28.99 | 1.160x |
32.24 | 27.89 | 1.156x | 32.42 | 27.89 | 1.162x |
| tail | 1 | 32 | 34.13 | 29.22 | 1.168x | 34.26 | 29.31 | 1.169x |
32.67 | 28.16 | 1.160x | 33.07 | 28.26 | 1.170x |
| tail | 1 | 64 | 35.97 | 30.34 | 1.186x | 36.06 | 30.43 | 1.185x |
34.62 | 29.44 | 1.176x | 34.98 | 29.36 | 1.191x |
| tail | 1 | 128 | 39.01 | 33.06 | 1.180x | 39.10 | 33.12 | 1.181x |
37.63 | 32.26 | 1.167x | 37.92 | 31.97 | 1.186x |
| tail | 1 | 256 | 42.78 | 42.75 | 1.001x | 42.38 | 42.37 | 1.000x |
44.22 | 44.22 | 1.000x | 41.39 | 41.44 | 0.999x |
| tail | 1 | 512 | 56.37 | 56.38 | 1.000x | 54.06 | 54.08 | 1.000x |
59.31 | 59.28 | 1.001x | 50.45 | 50.42 | 1.001x |
| tail | 1 | 1024 | 109.90 | 101.86 | 1.079x | 104.75 | 97.41 | 1.075x |
120.87 | 107.81 | 1.121x | 90.03 | 84.66 | 1.064x |
| tail | 1 | 2048 | 204.81 | 196.34 | 1.043x | 199.23 | 193.22 | 1.031x
| 201.23 | 192.51 | 1.045x | 157.43 | 149.52 | 1.053x |
| tail | 1 | 4096 | 414.58 | 394.93 | 1.050x | 405.53 | 393.28 | 1.031x
| 385.44 | 364.26 | 1.058x | 320.11 | 298.18 | 1.074x |
| tail | 1 | 8192 | 841.07 | 806.36 | 1.043x | 849.32 | 806.79 | 1.053x
| 779.27 | 757.99 | 1.028x | 653.16 | 623.73 | 1.047x |
| tail | 1 | 16384 | 1699.36 | 1631.75 | 1.041x | 1721.59 | 1636.63 |
1.052x | 1620.56 | 1560.16 | 1.039x | 1375.24 | 1294.29 | 1.063x |
| tail | 8 | 1 | 7.87 | 7.84 | 1.004x | 7.82 | 7.82 | 1.000x | 7.68 |
7.67 | 1.002x | 7.54 | 7.54 | 1.000x |
| tail | 8 | 2 | 7.89 | 7.86 | 1.004x | 7.84 | 7.84 | 1.000x | 7.68 |
7.70 | 0.998x | 7.57 | 7.57 | 1.000x |
| tail | 8 | 4 | 7.93 | 7.90 | 1.004x | 7.87 | 7.87 | 1.000x | 7.74 |
7.73 | 1.002x | 7.60 | 7.60 | 1.000x |
| tail | 8 | 8 | 7.95 | 7.95 | 1.000x | 7.94 | 7.94 | 1.000x | 7.79 |
7.79 | 1.000x | 7.68 | 7.68 | 1.000x |
| tail | 8 | 16 | 9.15 | 9.15 | 1.000x | 9.50 | 9.50 | 1.000x | 9.04 |
9.06 | 0.998x | 8.85 | 8.83 | 1.002x |
| tail | 8 | 32 | 10.59 | 10.59 | 1.000x | 10.85 | 10.85 | 1.000x |
10.62 | 10.62 | 1.000x | 10.38 | 10.37 | 1.002x |
| tail | 8 | 64 | 11.63 | 11.65 | 0.999x | 11.78 | 11.78 | 1.000x |
11.52 | 11.52 | 1.000x | 11.36 | 11.38 | 0.999x |
| tail | 8 | 128 | 13.76 | 13.73 | 1.002x | 13.47 | 13.49 | 0.999x |
13.41 | 13.39 | 1.001x | 13.07 | 13.07 | 1.000x |
| tail | 8 | 256 | 14.64 | 14.72 | 0.995x | 14.10 | 14.18 | 0.994x |
14.29 | 14.26 | 1.002x | 13.74 | 13.76 | 0.999x |
| tail | 8 | 512 | 18.83 | 18.80 | 1.002x | 17.78 | 17.75 | 1.002x |
18.72 | 18.58 | 1.008x | 17.60 | 17.39 | 1.012x |
| tail | 8 | 1024 | 26.03 | 26.02 | 1.001x | 24.05 | 23.94 | 1.005x |
24.91 | 25.06 | 0.994x | 23.22 | 23.30 | 0.997x |
| tail | 8 | 2048 | 39.84 | 39.90 | 0.998x | 36.91 | 36.98 | 0.998x |
36.26 | 36.13 | 1.004x | 33.52 | 33.49 | 1.001x |
| tail | 8 | 4096 | 65.86 | 65.79 | 1.001x | 61.66 | 61.65 | 1.000x |
65.10 | 65.10 | 1.000x | 56.32 | 56.30 | 1.000x |
| tail | 8 | 8192 | 120.24 | 120.18 | 1.001x | 111.95 | 111.84 | 1.001x
| 123.42 | 123.46 | 1.000x | 103.44 | 103.49 | 1.000x |
| tail | 8 | 16384 | 244.00 | 243.91 | 1.000x | 231.83 | 231.31 | 1.002x
| 233.38 | 233.31 | 1.000x | 200.40 | 200.24 | 1.001x |

_Times are µs per call on one rank from `bench_gpu_time_with_cupti` with
cold L2 and CUDA graph replay (some ≥4096-token passes without graphs,
both sides alike). Both sides interleave in six groups over two passes
(one pass for GB200 front and 1-token TP1 tail); values are medians of
group medians. GPUs: B200 and GB200 NVL72 (`sm_100a`), B300 and GB300
NVL72 (`sm_103a`); CUDA 13.4._

Cake also ships a TP12 fused tail of this block for GB200/GB300 NVL72 in
`kimi_k3_tp12_tail`; both packages are BF16 only and target `sm_100a`
and `sm_103a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Improved Kimi K3 LatentMoE decode and prefill planning, including
adaptive tail-kernel selection based on token count and GPU size.
* Added a resident fused-normalization path for eligible prefill
workloads.
* Added clearer validation for invalid tensor layouts, types, devices,
and launch parameters.
* **Performance**
* Updated cache policies and work scheduling for decode and prefill to
better fit different execution plans.
* **Tests**
* Expanded coverage for tail routes, fused normalization, repeated
launches, and graph replay.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d3d7c24](https://github.com/flashinfer-ai/flashinfer/commit/d3d7c2488783d85e678bd693318bbee19e2fbb97)

- **作者**: Yang Xu
- **时间**: 2026-10-25T11:15:37Z
- **提交信息**: feat(moe): extend grouped Frost decode to FP8 and block-FP8 on Hopper and SM120 (#7212)

<!-- .github/pull_request_template.md -->

## 📌 Description

Builds on the merged #7204 and targets `main`. The parent squash merge
has been reconciled without changing any of the 17 qualified feature
files; their contents match the previously tested head. Auto-merge
remains disabled until this head is reviewed and required CI passes.

Add grouped per-tensor E4M3 and DeepSeek block-FP8 Tensor Core
candidates to the opt-in Frost low-latency backend on SM90 and SM120,
and extend the SM120 BF16/FP16 candidate set to additional gated
activations. The original checkpoint layout, live scales, common
activation lowering and ordered combine remain shared with the existing
implementation.

| Architecture / dtype | New grouped candidates at H2048/I512/top-k10,
finalized matching output |
|---|---|
| SM90 per-tensor FP8 → BF16 | Default SwiGLU/SiTU at T4/T8; ReLU2 at
T8; WGMMA group2/stages4/K128 |
| SM120 per-tensor FP8 → BF16 | Default SwiGLU/SiTU/ReLU2 at T4/T8;
native warp FP8 MMA group2 or group4/stages2/K128 |
| SM90/SM120 DeepSeek block-FP8 → BF16 | Default SwiGLU at T4/T8;
ReLU2/SiLU at T8; existing 128x128 weight scales and dynamic activation
quantization |
| SM120 BF16 and FP16 | GeGLUTanh, default SiTU and SwiGLUStep at T4/T8,
alongside existing candidates |

FP8 accumulates native partials spanning at most K64 and promotes them
through separate FP32 additions, independently of the TMA staging tile.
This preserves the existing BF16 preactivation boundary, static E4M3
intermediate quantization and BF16 expert partials without relaxing
numerical thresholds. BF16/FP16 keep their existing accumulation
schedules. All sixteen FMA choices and the untuned FMA default remain;
representative routing/cache conditions must be tuned. T1/T2, unmeasured
shapes/activations and raw output retain existing choices.

DeepSeek block-FP8 reuses the same architecture-specific projections
with explicit scale handling: each native partial covers at most K64,
receives the original weight-block and token/route activation scales,
and accumulates in FP32. Its FP32 preactivation and dynamic 128-element
intermediate quantizer remain distinct from per-tensor FP8's BF16
boundary and static scale. Both BF16 inputs and prequantized E4M3 inputs
bind live scales through the existing API. Full BF16-entry timing
includes input quantization, FC1, activation/requantization, FC2 and
ordered combine. The Hopper native comparator uses its own BF16
intermediate reference; the SM120 native comparator supports SwiGLU only
in this harness. Native Hopper search uses per-stage top-two candidates
plus the heuristic rather than an exhaustive Cartesian search.

The reproducer adds activation/route-seed controls and a stronger
standalone vLLM device comparator. It searches both naive and
expert-grouped route policies; the latter includes FI GPU sort and
padding costs in timing. Pinned upstream GEMM device functions remain
unchanged, and each implementation uses its own typed numerical
reference. A win against the naive policy or one native backend does not
imply a best-backend win. The benchmark scope is the complete
routed-expert GPU interval, not serving or model throughput.

## 🔍 Related Issues

Builds on #7204 and the grouped Frost pipeline from #7194. Continues
#6626.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] Scoped `pre-commit run --files <changed files>` passes, including
mypy and formatting.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

The cumulative immutable source was checked with CuTe DSL 4.8:

- SM90: **304 passed, 21 expected skips** on the cumulative shared
device implementation; the final admission/test/reproducer delta
additionally passes **85 tests, 7 expected skips**.
- SM120: **311 passed, 14 expected skips** on the cumulative shared
device implementation; the final admission/test/reproducer delta
additionally passes **92 tests**.
- SM80 regression before the SM90/SM120-only block-FP8 addition: **226
passed, 54 expected skips**; FP8 TC is not admitted there.

The grouped-FP8 tests cover live graph inputs, changed
scales/routes/scores, poisoned scratch, invalid NaN/Inf padding scores,
both admitted SM120 group sizes and negative admission. Seventeen SM90
and twenty-four SM120 graph contracts each pass memcheck, racecheck and
synccheck with zero errors/hazards. Native public benchmark controls
cover the new FP8 activations and BF16 regression. The block-FP8
addition separately passes fourteen changing-input/independent-stream
graph contracts and eight advertised-candidate graph contracts per
architecture under all three sanitizers. Sixteen final public block-FP8
controls cover both architectures, admitted activations, T1 FMA fallback
and T4 ReLU2 exclusion. The stronger standalone comparator additionally
passes changing-route graph tests, sanitizer checks and both
grouped/naive public CLI controls. Source/import paths were checked
before execution; no numerical tolerance was relaxed.

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

Please focus on the two Hopper WGMMA promotion loops, native SM120 FP8
operand/epilogue handling, and the restricted candidate admission. The
compilation cache stores immutable metadata only; tensor pointers, scale
values and streams are bound per call. Tuning-domain identities change
for the new candidate sets.

CI lanes with CuTe DSL older than 4.8 can skip these kernels; skipped
tests are not native execution evidence. The target-GPU qualification
above is separate. Unqualified large-shape block-FP8 and Ampere
tile/gather experiments are not part of this PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added grouped Tensor Core execution options for selected FP8 and
DeepSeek block-FP8 workloads on supported GPUs.
* Expanded grouped execution support for additional activations,
including GeGLU-Tanh, SiTU, and SwiGLU-Step in supported configurations.
* Added naive and grouped routing choices to the standalone vLLM
baseline.
* **Documentation**
* Added guidance on supported grouped execution configurations,
activation limits, and routing policies.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2866b59](https://github.com/flashinfer-ai/flashinfer/commit/2866b59272d7976d10409e34cf15ce9dd9400f70)

- **作者**: eigen
- **时间**: 2026-10-25T11:14:41Z
- **提交信息**: perf(cake_blackwell_bf16_fp4): faster tcgen05 M128 pair programs on SM100/SM103 (#7311)

FlashInfer's `mm_bf16_fp4` multiplies BF16 activations by FP4 (E2M1)
weights that carry E4M3 block scales, with FP32 accumulation. Cake ships
it as two backend variants that differ in operand layout.
`blackwell-native` uses cuDNN-ABI layouts and produces BF16 or FP16
output. `blackwell-tiled` uses CuTe-ABI prepared-tile layouts and
produces BF16 output. This PR regenerates 3 of the 97 Cake programs of
this kernel. They are the PDL programs of the large-M tcgen05 M128 pair
kernel: the `blackwell-native` arm with and without alpha, and the
`blackwell-tiled` arm with alpha. They replace the previous Cake
generation of the same programs on `main` (#7282). That previous version
is the baseline. Speedup is the previous time divided by this PR's time.
Both times come from the same GPU in one job. These programs serve the
768/2112/2048 shape. There, speedup is 1.015x for `blackwell-native` and
1.029x for `blackwell-tiled` on GB300, and 1.018x and 1.023x on B200.
The other 9 rows use programs this PR does not change. They measure
0.999x-1.001x on GB300 and 0.999x-1.003x on B200.

**NVIDIA GB300 (sm_103a), CUDA 13.4:** median CUPTI kernel time in us,
cold L2, PDL on; alpha passed and BF16 output unless the variant column
notes otherwise.

| Shape M/N/K | Variant | Previous Cake (us) | This PR (us) | Speedup |
|---|---|---:|---:|---:|
| 1/4096/4096 | blackwell-native | 7.588 | 7.592 | 0.999x |
| 1/4096/4096 | blackwell-tiled | 7.464 | 7.460 | 1.001x |
| 768/2112/2048 | blackwell-native | 10.096 | 9.948 | 1.015x |
| 768/2112/2048 | blackwell-tiled | 10.860 | 10.552 | 1.029x |
| 7/4160/192 | blackwell-tiled | 2.968 | 2.968 | 1.000x |
| 13/11008/128 | blackwell-tiled | 3.088 | 3.088 | 1.000x |
| 17/3072/3072 | blackwell-tiled | 7.552 | 7.552 | 1.000x |
| 16/1024/1024 | blackwell-tiled, alpha=None | 3.872 | 3.872 | 1.000x |
| 16/1024/1024 | blackwell-native, FP16 output | 2.968 | 2.968 | 1.000x
|
| 16/1024/1024 | blackwell-native, caller-provided `out` | 2.952 | 2.952
| 1.000x |
| 16/1024/1024 | blackwell-tiled, caller-provided `out` | 4.008 | 4.008
| 1.000x |

**NVIDIA B200 (sm_100a), CUDA 13.4:** median CUPTI kernel time in us,
cold L2, PDL on; alpha passed and BF16 output unless the variant column
notes otherwise.

| Shape M/N/K | Variant | Previous Cake (us) | This PR (us) | Speedup |
|---|---|---:|---:|---:|
| 1/4096/4096 | blackwell-native | 7.816 | 7.824 | 0.999x |
| 1/4096/4096 | blackwell-tiled | 7.728 | 7.724 | 1.000x |
| 768/2112/2048 | blackwell-native | 10.396 | 10.216 | 1.018x |
| 768/2112/2048 | blackwell-tiled | 11.280 | 11.024 | 1.023x |
| 7/4160/192 | blackwell-tiled | 2.936 | 2.936 | 1.000x |
| 13/11008/128 | blackwell-tiled | 3.148 | 3.144 | 1.001x |
| 17/3072/3072 | blackwell-tiled | 7.864 | 7.864 | 1.000x |
| 16/1024/1024 | blackwell-tiled, alpha=None | 3.850 | 3.848 | 1.001x |
| 16/1024/1024 | blackwell-native, FP16 output | 2.960 | 2.960 | 1.000x
|
| 16/1024/1024 | blackwell-native, caller-provided `out` | 2.944 | 2.936
| 1.003x |
| 16/1024/1024 | blackwell-tiled, caller-provided `out` | 4.016 | 4.016
| 1.000x |

Cake has no other variants of this kernel: FP16 output is only on
`blackwell-native`, there are no fused forms, and every program ships
for sm_100a (B200) and sm_103a (GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Other**
* Updated internal processing for BF16-to-FP4 workloads. The public
interface remains unchanged, and no user-facing behavior changes are
specified.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Yingyi Huang <averyh@nvidia.com>

### [06da6cc](https://github.com/flashinfer-ai/flashinfer/commit/06da6cc640a059b95286d275ee464e0d26c9c16f)

- **作者**: eigen
- **时间**: 2026-10-25T11:06:45Z
- **提交信息**: perf(cake_kimi_k3_tp12_tail): route 256-960 token tails through the early-shared-scatter forms (#7310)

The TP12 LatentMoE tail kernel (BF16, 12 ranks on one GB200 / GB300
NVL72 domain) has three fused forms. The host picks one by token count
M. For M <= 8 it runs a one-shot early-shared-scatter (ESS) K1 and the
fused up-projection tail. In the middle range it runs ESS K1 and the
one-CTA-per-token ESS tail (K3-ESS). Above that it runs a plain two-shot
K1 and the persistent tail. This PR changes only the host routing. The
ESS forms now cover 9-960 tokens, where they used to stop at 255, so
256-960 tokens no longer go to the persistent tail. Compared with the
previous Cake version (the routing on FlashInfer main), this is
1.06-1.08x faster at 256 and 512 tokens on both GB300 and GB200.

| Tokens (M) | GB300 previous (µs) | GB300 this PR (µs) | GB300 speedup
| GB200 previous (µs) | GB200 this PR (µs) | GB200 speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 18.20 | 18.77 | 0.970x | 19.39 | 19.25 | 1.007x |
| 8 | 23.57 | 22.98 | 1.025x | 24.05 | 23.87 | 1.007x |
| 32 | 25.90 | 25.89 | 1.001x | 26.42 | 26.40 | 1.001x |
| 64 | 27.88 | 27.62 | 1.009x | 28.01 | 28.20 | 0.993x |
| 128 | 31.34 | 30.78 | 1.018x | 31.86 | 31.34 | 1.016x |
| 256 | 41.74 | 39.39 | 1.060x | 43.17 | 39.96 | 1.080x |
| 512 | 60.59 | 56.10 | 1.080x | 61.53 | 57.22 | 1.075x |
| 1024 | 93.54 | 93.52 | 1.000x | 94.72 | 94.67 | 1.001x |
| 2048 | 163.11 | 163.18 | 1.000x | 164.95 | 165.04 | 0.999x |
| 4096 | 297.67 | 297.42 | 1.001x | 299.39 | 299.30 | 1.000x |

*Time of the tail in a CUDA graph, taken from the slowest of the 12
ranks, as the median of 8 groups x 2 passes. Measured on GB300 NVL72
(sm_103a) and GB200 NVL72 (sm_100a) with 12 ranks on 3 nodes x 4 GPUs
and CUDA 13.4; speedup = previous / this PR. Rows outside 256-960 tokens
run the same programs before and after, so their ratio is run-to-run
variation.*

This kernel has no other Cake variants: it ships only in BF16, this
package holds all three fused forms, and every program is built for
sm_100a and sm_103a (GB200 / GB300 NVL72).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Performance**
- Updated token-count routing for Kimi K3 TP12 tail processing: ESS and
grouped paths are selected through 960 tokens, while persistent bulk
processing is selected from 961 tokens onward.
- Updated the cuBLAS selection threshold to apply when the token count
exceeds 8.
- **Tests**
- Expanded route-selection coverage across token counts up to 4096,
including the updated routing boundaries.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4796d2e](https://github.com/flashinfer-ai/flashinfer/commit/4796d2effd9ea8511c32ffcd21609998c2896bc0)

- **作者**: eigen
- **时间**: 2026-10-25T10:54:47Z
- **提交信息**: perf(cake_minimax_h3): faster NVFP4 out-projection on SM120 (#7309)

`flashinfer.diffusion_ops.cake_minimax_h3_sm120_quant_out_proj` computes
the MiniMax-H3 attention output projection with the fused indexed gate
and residual on SM120 (`sm_120a`). It has two variants: FP8
(`minimax_h3_fp8_out_proj`, per-token) and NVFP4
(`minimax_h3_nvfp4_out_proj`). Each runs as one persistent launch that
does the activation quantization, the GEMM and the gate/residual
epilogue. This PR changes only the NVFP4 variant. The persistent tile
order now walks one M tile per swath. The kernel now computes the
dequantization factor from the two global scales on the device, using
the same FP64 formula as before, so the output is bitwise equal. The
call no longer reads the global scales on the host, which removes two
host synchronizations per call. Across the six NVFP4 shapes below, it is
1.012x to 1.039x faster than the current main
`minimax_h3_nvfp4_out_proj` (geomean 1.021). With back-to-back calls and
no host synchronization, the GPU idle gap between consecutive NVFP4
calls drops from 186.9-223.3 µs on main to 3.1-3.6 µs.

NVIDIA RTX PRO 6000 Blackwell Server Edition (`sm_120a`), CUDA 13.4.
Time of the complete operator (activation quantization + GEMM + gated
residual), median of 5 interleaved rounds with a cold L2. M = rows. FP8
rows ("changed = no") run the same kernel in both columns, so their
ratio is run-to-run variation.

| quantization | M | changed | before (µs) | after (µs) | speedup |
|---|---:|---|---:|---:|---:|
| FP8 | 33472 | no | 3655.4 | 3660.6 | 0.999x |
| FP8 | 38592 | no | 4204.8 | 4190.0 | 1.004x |
| FP8 | 48768 | no | 5306.8 | 5308.4 | 1.000x |
| FP8 | 58944 | no | 6449.1 | 6428.9 | 1.003x |
| FP8 | 74240 | no | 8121.0 | 8110.8 | 1.001x |
| FP8 | 109952 | no | 12085.6 | 12088.7 | 1.000x |
| NVFP4 | 33472 | yes | 2004.4 | 1929.1 | 1.039x |
| NVFP4 | 38592 | yes | 2307.6 | 2244.5 | 1.028x |
| NVFP4 | 48768 | yes | 2889.6 | 2855.3 | 1.012x |
| NVFP4 | 58944 | yes | 3560.0 | 3483.6 | 1.022x |
| NVFP4 | 74240 | yes | 4461.0 | 4399.9 | 1.014x |
| NVFP4 | 109952 | yes | 6631.7 | 6546.6 | 1.013x |

The SM100/SM103 module `flashinfer.diffusion_ops.minimax_h3_out_proj`
ships BF16, MXFP8 and NVFP4 variants of the same projection on `sm_100a`
and `sm_103a`; with this module the family covers `sm_100a`, `sm_103a`
and `sm_120a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* NVFP4 output projection now handles the weight global scale as an FP32
device tensor. Scalar scale inputs are converted to one-element tensors,
and the kernel computes alpha from the global scales in FP64 before
rounding it to FP32. This keeps scale handling within the device-side
computation and avoids extracting tensor values on the host.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a4dc7d1](https://github.com/flashinfer-ai/flashinfer/commit/a4dc7d17fb6ae7f6f0e9e809e2e9f88e48eacb00)

- **作者**: eigen
- **时间**: 2026-10-25T10:38:14Z
- **提交信息**: perf(cake_mxfp8_megamoe_ep16): one-fence NVLink barrier, per-warp dispatch, balanced static partition (#7299)

`flashinfer.experimental.cake_mxfp8_megamoe_ep16`
(`CakeMxfp8MegaMoeEp16`) runs expert-parallel MoE across 16 ranks. It
supports one data-type configuration: BF16 activations, MXFP8 expert
weights (E4M3 values with E8M0 scales per 32 elements) and BF16 output.
The shape is hidden 3072, intermediate 5120, 512 experts (32 per rank)
and top-8. Each forward runs two kernels: a fused kernel for dispatch,
FC1, SwiGLU, FC2 and return, followed by a top-k reduce kernel. The
module has two backends, CUDA and CuTe DSL. The CUDA backend's fused
kernel has two return-protocol forms: a CTA-0 coordinator for 16 and 64
tokens per rank, and an all-CTA protocol for 32 tokens per rank. Both
forms are compiled for sm_100a and sm_103a. This PR updates the CUDA
fused kernel in both forms on both architectures with three changes.
First, the two cross-rank NVLink barriers now issue one system-scope
acquire-release fence followed by relaxed system-scope adds to the 16
rank flags, replacing 16 sequential system-scope release atomics.
Second, every warp dispatches its own source tokens without CTA-wide
ordering. Third, FC1/FC2 row tiles are split statically so every two-CTA
cluster streams the same number of weight K tiles. Outputs are
bitwise-identical on all 16 ranks. End-to-end forward is 1.13x to 1.18x
faster than the previous Cake CUDA backend on main, which already
includes the previous round of this kernel. Every configuration below is
faster.

| Tokens per rank (global) | Routing | Previous Cake CUDA (us) | This PR
(us) | Speedup |
|---|---|---:|---:|---:|
| 16 (256) | balanced | 355.4 | 312.6 | 1.14x |
| 16 (256) | hotset50 | 355.3 | 313.8 | 1.13x |
| 32 (512) | balanced | 362.7 | 320.5 | 1.13x |
| 32 (512) | hotset50 | 368.4 | 318.5 | 1.16x |
| 64 (1024) | balanced | 376.1 | 322.0 | 1.17x |
| 64 (1024) | hotset50 | 377.5 | 320.5 | 1.18x |

*16x NVIDIA GB300 (sm_103a), 4 nodes x 4 GPUs in one NVL72 domain, CUDA
13.4, driver 580.159.03; end-to-end eager forward (both kernels) with
cold L2, slowest rank's median, median of 6 interleaved rounds (40
iterations each); balanced = uniform top-8, hotset50 = 4 of the 8 slots
drawn from the first 128 experts.*

This PR does not change the module's other Cake variant, its CuTe DSL
backend, and the whole family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated MXFP8 MoE processing to distribute routed tokens across
experts and coordinate work across ranks. The processing flow now uses
shared token dispatch and revised workload assignments for the two fully
connected stages, along with updated cross-rank synchronization. These
changes affect internal execution; no new user-facing controls or
capabilities are described.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ba12a83](https://github.com/flashinfer-ai/flashinfer/commit/ba12a832238575233f2cee795bd93479494fc69a)

- **作者**: eigen
- **时间**: 2026-10-25T10:37:22Z
- **提交信息**: perf(cake_minimax_h3): SM120 FP8 varlen attention: fused statistics, unit-scale block-scaled MMA, split K/V refill (#7289)

The MiniMax-H3 noncausal packed-varlen attention kernel works on THD
tensors ([tokens, 56 heads, 128 head dim]), with BF16 input and output
and int32 `cu_seqlens`. It has six Cake variants in FlashInfer. This PR
adds a new version of the sm_120a FP8 variant,
`minimax_h3_sm120_varlen_attention_fp8` (E4M3 QK and PV), with the same
API. The baseline is the previous Cake version of the same op
(FlashInfer main at 5e45550). The new version is 1.24x-1.40x faster on
RTX 5090 and 1.005x-1.104x faster on RTX PRO 6000. Timings are median
end-to-end operator latency with cold L2 on CUDA 13.4, using the same
inputs for both versions.

### NVIDIA GeForce RTX 5090 (sm_120a, 170 SMs)

| shape | cu_seqlens | previous (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| center_4s | `[0, 33472]` | 73,983 | 52,679 | 1.404x |
| center_5s | `[0, 38592]` | 99,568 | 72,475 | 1.374x |
| center_6s | `[0, 48768]` | 159,122 | 115,851 | 1.374x |
| center_8s | `[0, 58944]` | 232,110 | 169,787 | 1.367x |
| center_10s | `[0, 74240]` | 367,365 | 267,778 | 1.372x |
| center_15s | `[0, 109952]` | 798,811 | 578,255 | 1.381x |
| tail_5s_a | `[0, 38531]` | 100,499 | 73,358 | 1.370x |
| tail_5s_b | `[0, 38629]` | 100,598 | 73,499 | 1.369x |
| pad_15s | `[0, 109901, 109952]` | 802,931 | 589,271 | 1.363x |
| seg4 | `[0, 8368, 16736, 25104, 33472]` | 20,426 | 15,071 | 1.355x |
| seg3_ragged | `[0, 257, 4567, 4824]` | 1,616 | 1,174 | 1.376x |
| seg_empty | `[0, 0, 129, 129, 500]` | 56.1 | 45.1 | 1.244x |

### NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120a, 188 SMs)

| shape | cu_seqlens | previous (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| center_4s | `[0, 33472]` | 48,598 | 48,169 | 1.009x |
| center_5s | `[0, 38592]` | 63,796 | 63,136 | 1.010x |
| center_6s | `[0, 48768]` | 101,461 | 100,440 | 1.010x |
| center_8s | `[0, 58944]` | 148,189 | 146,819 | 1.009x |
| center_10s | `[0, 74240]` | 233,783 | 231,183 | 1.011x |
| center_15s | `[0, 109952]` | 508,771 | 503,153 | 1.011x |
| tail_5s_a | `[0, 38531]` | 64,133 | 63,475 | 1.010x |
| tail_5s_b | `[0, 38629]` | 64,133 | 63,508 | 1.010x |
| pad_15s | `[0, 109901, 109952]` | 511,583 | 505,027 | 1.013x |
| seg4 | `[0, 8368, 16736, 25104, 33472]` | 13,782 | 13,707 | 1.005x |
| seg3_ragged | `[0, 257, 4567, 4824]` | 1,194 | 1,166 | 1.024x |
| seg_empty | `[0, 0, 129, 129, 500]` | 68.1 | 61.7 | 1.104x |

The other five Cake variants are the sm_120a NVFP4-QK forms
`minimax_h3_sm120_varlen_attention_nvfp4` (default) and
`minimax_h3_sm120_varlen_attention_nvfp4_nodelta`, plus the sm_100a /
sm_103a forms `minimax_h3_varlen_attention` (BF16),
`minimax_h3_varlen_fp8_attention` (FP8, with the BF16-input form
`minimax_h3_varlen_fp8_attention_bf16`) and
`minimax_h3_varlen_nvfp4_attention` (NVFP4-QK), so the family covers
sm_100a, sm_103a and sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
  * Added quantized variable-length attention for NVIDIA SM120 GPUs.
* Added launch-grid calculation support for configuring attention
workloads.

* **Improvements**
* Reuses and grows workspaces across calls on the same device and
stream, helping avoid repeated allocation.
  * Skips kernel launches when there are no non-empty segments.

* **Compatibility**
* Non-empty attention calls require an SM120 GPU; other device
architectures raise an error.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [dc39352](https://github.com/flashinfer-ai/flashinfer/commit/dc39352926e8db106670d138c8cfb53f09e1e388)

- **作者**: eigen
- **时间**: 2026-10-25T10:34:41Z
- **提交信息**: perf(cake_fused_norm_combine): pipelined owner program at lag 3, final store 4 steps behind (#7285)

`cake_fused_norm_combine` has one Cake variant: BF16, hidden size 2560,
eight peers and two norm tracks. This PR delivers a new version of that
variant. The host picks one of four programs by token count, and only
the program for 480 or more tokens changes. The three programs for fewer
tokens are unchanged. At 1, 8, 64 and 256 tokens both sides run the same
code, so the differences in those rows are run-to-run variation. The
baseline is the previous Cake version of this kernel shipped in
FlashInfer (current main, which includes #7270). The new version is
faster at 1024 and 2048 tokens on both GPUs, with speedups from 1.006×
to 1.018×.

| GPU | tokens | previous Cake (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|---:|
| B200 | 1 | 10.304 | 10.336 | 0.997× |
| B200 | 8 | 11.552 | 11.647 | 0.992× |
| B200 | 64 | 14.048 | 14.048 | 1.000× |
| B200 | 256 | 16.832 | 16.895 | 0.996× |
| B200 | 1024 | 30.656 | 30.112 | 1.018× |
| B200 | 2048 | 46.976 | 46.720 | 1.006× |
| B300 | 1 | 9.760 | 9.920 | 0.984× |
| B300 | 8 | 12.256 | 12.256 | 1.000× |
| B300 | 64 | 14.977 | 14.944 | 1.002× |
| B300 | 256 | 17.440 | 17.440 | 1.000× |
| B300 | 1024 | 31.040 | 30.560 | 1.016× |
| B300 | 2048 | 47.360 | 47.040 | 1.007× |

Measured on 8× NVIDIA B200 (sm_100a) and 8× NVIDIA B300 (sm_103a) with
CUDA 13.4. Each time is the per-call kernel time of the eight-rank
collective: the slowest rank of each call, median over calls. Speedup =
previous Cake / this PR.

Cake ships no other variant of this kernel, and the kernel ships on
sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* Updated fused normalization and combination processing to handle
pending work at adjusted token positions, with an additional output path
for the final token. Existing input validation and launch configuration
remain unchanged. These changes affect internal processing; no
user-facing interface changes are included.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ba24b42](https://github.com/flashinfer-ai/flashinfer/commit/ba24b4214024a0cd1ce07ca95e0f28928374aca9)

- **作者**: eigen
- **时间**: 2026-10-25T10:33:51Z
- **提交信息**: perf(cake_warp_decode): retune SM100/SM103 schedule selection (#7292)

`cake_warp_decode` is Cake's NVFP4 routed fused-MoE decode for 1 to 32
tokens, called through
`flashinfer.fused_moe.trtllm_fp4_block_scale_routed_moe(...)` with
`CakeWarpDecodeConfig(backend="cake")`. It has one data type (NVFP4
W4A4, BF16 output), five activation variants and one fused form: FC1
with the activation, FC2 and the top-k finalize. This PR changes only
the host-side schedule selection. It moves 75 rows on sm_100a and 26 on
sm_103a to schedules the module already ships, and outputs are
unchanged. Against the previous Cake selection on FlashInfer main, the
rerouted rows run up to 1.29x faster on sm_100a and up to 1.24x faster
on sm_103a.

The "memset" and "read" column groups are two cold-L2 modes: before
every call, we flush L2 with a memset of a large buffer or a read of
one.

**sm_100a** (NVIDIA GB200, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake
selection, new = this PR; ratio = new / previous. **Bold** num_tokens =
rows this PR routes to a different schedule.

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|16.14|14.39|0.891|14.41|12.67|0.880|
|**2**|19.29|19.02|0.986|16.64|16.38|0.984|
|**3**|22.04|21.91|0.994|18.43|18.24|0.990|
|4|25.42|25.69|1.010|21.42|21.66|1.011|
|5|28.26|28.38|1.004|22.97|22.86|0.995|
|6|31.62|31.57|0.998|25.83|25.85|1.001|
|7|34.13|34.34|1.006|27.26|27.34|1.003|
|8|37.04|37.04|1.000|29.40|29.42|1.001|
|9|39.88|39.87|1.000|31.38|31.37|0.999|
|10|42.71|42.64|0.998|33.86|33.74|0.996|
|11|45.38|45.38|1.000|35.85|35.99|1.004|
|12|47.90|48.04|1.003|38.16|38.22|1.001|
|13|50.77|50.79|1.000|40.41|40.23|0.996|
|14|53.66|53.52|0.997|42.67|42.51|0.996|
|15|56.31|56.22|0.998|44.95|44.94|1.000|
|16|58.94|58.70|0.996|47.09|47.01|0.998|
|17|61.30|61.37|1.001|49.18|49.20|1.000|
|18|63.86|63.82|0.999|51.52|51.44|0.998|
|19|66.25|66.21|0.999|53.70|53.75|1.001|
|20|68.60|68.66|1.001|55.89|55.94|1.001|
|21|70.78|70.95|1.002|58.34|58.52|1.003|
|22|73.18|73.16|1.000|60.25|60.49|1.004|
|23|75.62|75.61|1.000|62.70|62.52|0.997|
|24|78.03|77.98|0.999|64.98|64.78|0.997|
|25|80.31|80.39|1.001|67.27|67.15|0.998|
|26|83.01|82.86|0.998|69.74|69.58|0.998|
|27|85.42|85.28|0.998|71.96|71.60|0.995|
|28|87.68|87.77|1.001|73.92|73.79|0.998|
|29|90.41|90.39|1.000|76.35|76.10|0.997|
|30|92.91|92.85|0.999|78.40|78.31|0.999|
|31|95.42|95.41|1.000|80.70|80.65|0.999|
|32|97.86|98.00|1.001|82.78|82.98|1.003|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|15.27|14.31|0.937|13.34|12.53|0.939|
|2|17.39|17.26|0.993|15.45|15.28|0.989|
|3|21.21|21.10|0.995|17.91|17.88|0.998|
|4|23.78|23.70|0.996|19.98|19.66|0.984|
|5|27.34|27.52|1.006|22.53|22.45|0.996|
|6|30.01|29.97|0.999|24.05|24.01|0.998|
|7|32.74|32.78|1.001|26.03|26.21|1.007|
|8|35.43|35.57|1.004|28.35|28.44|1.003|
|9|37.63|37.73|1.003|29.75|29.74|0.999|
|10|39.96|40.18|1.005|31.57|31.85|1.009|
|11|42.09|42.21|1.003|33.23|33.32|1.003|
|12|44.12|44.04|0.998|34.62|34.59|0.999|
|13|46.04|46.18|1.003|35.94|35.97|1.001|
|14|48.30|48.26|0.999|37.50|37.66|1.004|
|**15**|50.62|48.68|0.962|39.20|38.97|0.994|
|**16**|52.84|50.65|0.959|40.77|40.46|0.993|
|**17**|55.06|52.61|0.956|43.04|41.82|0.972|
|**18**|57.11|54.47|0.954|44.42|43.64|0.983|
|**19**|59.32|56.22|0.948|46.55|44.82|0.963|
|**20**|58.14|57.85|0.995|46.58|46.24|0.993|
|**21**|59.96|59.67|0.995|48.14|47.64|0.990|
|**22**|61.83|61.38|0.993|49.73|49.04|0.986|
|**23**|63.52|63.01|0.992|51.03|50.39|0.987|
|**24**|65.30|64.53|0.988|52.52|51.88|0.988|
|**25**|67.13|66.50|0.991|53.90|53.34|0.989|
|**26**|68.98|68.18|0.988|55.44|54.92|0.991|
|**27**|68.89|68.10|0.989|55.53|54.91|0.989|
|**28**|68.90|68.14|0.989|55.50|54.81|0.987|
|**29**|68.74|68.14|0.991|55.42|54.94|0.991|
|**30**|68.94|68.26|0.990|55.45|54.87|0.990|
|**31**|68.93|68.26|0.990|55.38|54.98|0.993|
|**32**|68.80|68.13|0.990|55.41|54.97|0.992|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|20.85|20.22|0.970|18.31|17.62|0.962|
|2|25.79|25.72|0.997|21.25|21.02|0.989|
|3|31.03|31.07|1.001|25.19|25.37|1.007|
|4|38.69|38.67|1.000|30.51|30.76|1.008|
|5|42.96|43.04|1.002|34.07|33.80|0.992|
|6|47.96|47.76|0.996|37.66|37.82|1.004|
|7|54.66|54.62|0.999|42.56|42.94|1.009|
|8|59.11|59.13|1.000|46.30|46.10|0.996|
|9|63.70|63.73|1.001|50.26|50.39|1.003|
|10|68.96|69.08|1.002|55.32|55.42|1.002|
|11|73.06|73.08|1.000|59.22|59.16|0.999|
|12|77.10|77.15|1.001|63.14|63.15|1.000|
|13|81.86|81.74|0.999|68.06|68.14|1.001|
|14|86.14|85.96|0.998|72.26|72.40|1.002|
|15|90.86|90.82|0.999|76.15|76.65|1.007|
|16|95.15|95.26|1.001|80.95|80.86|0.999|
|17|99.42|99.54|1.001|85.10|85.39|1.003|
|18|103.52|103.70|1.002|89.53|89.70|1.002|
|19|108.10|108.40|1.003|94.08|94.31|1.002|
|20|112.37|112.24|0.999|98.17|98.42|1.003|
|21|116.74|116.69|1.000|102.09|102.37|1.003|
|22|121.31|121.34|1.000|106.70|106.72|1.000|
|23|125.03|125.48|1.004|111.25|111.32|1.001|
|24|129.49|129.86|1.003|115.04|115.28|1.002|
|25|134.42|134.28|0.999|119.92|119.66|0.998|
|26|138.73|138.87|1.001|123.77|124.23|1.004|
|27|143.07|142.95|0.999|128.54|128.38|0.999|
|28|147.53|147.26|0.998|132.71|132.16|0.996|
|29|151.73|151.83|1.001|136.84|136.89|1.000|
|30|156.13|155.87|0.998|141.38|141.53|1.001|
|31|160.15|160.27|1.001|145.54|145.51|1.000|
|32|164.80|164.54|0.998|149.83|149.62|0.999|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|13.80|12.02|0.871|12.44|11.09|0.891|
|2|14.84|14.78|0.996|13.06|13.06|1.001|
|3|17.03|17.05|1.001|15.11|15.07|0.997|
|4|19.50|19.60|1.005|17.54|17.44|0.995|
|5|21.17|21.21|1.002|18.15|18.32|1.009|
|6|23.23|23.16|0.997|19.31|19.82|1.026|
|7|25.88|25.90|1.001|21.36|21.25|0.995|
|8|27.46|27.41|0.998|22.38|22.50|1.005|
|9|28.92|28.95|1.001|23.72|23.69|0.999|
|10|31.46|31.13|0.989|25.58|25.66|1.003|
|11|32.86|32.74|0.996|26.68|26.53|0.994|
|12|34.55|34.66|1.003|27.68|27.54|0.995|
|13|36.23|36.43|1.006|28.98|29.26|1.010|
|14|37.82|37.80|0.999|30.32|30.32|1.000|
|15|39.68|39.65|0.999|31.68|31.59|0.997|
|16|41.38|41.34|0.999|32.74|32.79|1.002|
|17|43.07|43.02|0.999|34.62|34.54|0.997|
|18|44.62|44.54|0.998|35.74|35.78|1.001|
|19|46.39|46.42|1.001|37.06|37.18|1.003|
|20|47.98|48.03|1.001|38.22|38.15|0.998|
|21|49.63|49.78|1.003|39.59|39.85|1.006|
|22|51.67|51.92|1.005|41.08|40.97|0.997|
|23|53.16|53.14|1.000|42.38|42.34|0.999|
|24|54.87|54.79|0.999|43.78|43.68|0.998|
|25|56.72|56.61|0.998|45.07|45.06|1.000|
|26|58.38|58.19|0.997|46.56|46.44|0.997|
|27|59.91|60.05|1.002|47.82|47.81|1.000|
|28|61.63|61.62|1.000|49.30|49.15|0.997|
|29|63.22|63.22|1.000|50.58|50.65|1.001|
|30|64.78|64.50|0.996|51.90|52.04|1.003|
|31|66.15|66.12|1.000|53.27|53.21|0.999|
|32|67.60|67.58|1.000|54.58|54.72|1.002|

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|15.02|14.06|0.936|13.35|12.58|0.942|
|2|19.42|19.38|0.998|17.14|16.91|0.986|
|3|23.10|23.02|0.997|19.40|19.31|0.995|
|4|27.10|27.05|0.998|21.88|21.90|1.001|
|5|30.30|30.54|1.008|24.90|25.09|1.008|
|6|33.63|33.98|1.010|27.03|27.14|1.004|
|7|36.98|36.83|0.996|29.28|29.42|1.005|
|8|40.14|40.10|0.999|31.43|31.39|0.999|
|9|43.06|43.13|1.002|33.99|34.05|1.002|
|**10**|47.20|46.39|0.983|37.58|36.54|0.972|
|**11**|50.37|49.54|0.983|39.81|39.20|0.985|
|**12**|53.52|52.62|0.983|42.34|41.69|0.985|
|**13**|56.21|55.80|0.993|44.74|44.17|0.987|
|**14**|59.58|59.06|0.991|47.25|46.62|0.987|
|**15**|62.67|62.12|0.991|49.46|49.31|0.997|
|16|65.64|65.66|1.000|51.98|51.90|0.999|
|17|67.71|67.70|1.000|53.82|53.94|1.002|
|18|70.26|70.39|1.002|56.22|56.17|0.999|
|19|72.60|72.55|0.999|58.02|58.09|1.001|
|20|71.83|71.74|0.999|57.38|57.38|1.000|
|21|71.85|71.91|1.001|57.34|57.40|1.001|
|22|71.82|71.83|1.000|57.41|57.42|1.000|
|23|71.89|71.78|0.998|57.42|57.30|0.998|
|24|71.88|71.94|1.001|57.43|57.42|1.000|
|25|71.93|71.98|1.001|57.54|57.52|1.000|
|26|72.00|72.03|1.000|57.58|57.56|1.000|
|27|71.84|72.11|1.004|57.50|57.65|1.003|
|28|72.05|71.85|0.997|57.50|57.54|1.001|
|29|71.99|71.58|0.994|57.60|57.69|1.002|
|30|71.86|71.98|1.002|57.57|57.56|1.000|
|31|72.06|71.95|0.998|57.70|57.66|0.999|
|32|72.80|72.85|1.001|58.55|58.50|0.999|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|31.82|26.81|0.842|26.86|22.58|0.841|
|2|40.38|40.32|0.999|32.22|32.38|1.005|
|3|53.23|53.24|1.000|42.19|42.25|1.001|
|4|64.66|64.89|1.004|52.08|52.08|1.000|
|5|76.29|76.30|1.000|62.26|62.31|1.001|
|6|87.58|87.46|0.999|72.47|72.36|0.998|
|7|97.79|97.78|1.000|82.51|82.55|1.000|
|8|108.42|108.45|1.000|92.61|92.68|1.001|
|9|118.73|118.69|1.000|102.73|102.70|1.000|
|10|128.94|129.00|1.000|112.78|112.74|1.000|
|11|139.08|139.14|1.000|122.78|123.02|1.002|
|**12**|149.79|148.86|0.994|132.92|132.02|0.993|
|**13**|159.88|158.68|0.993|143.06|142.06|0.993|
|**14**|170.02|168.39|0.990|153.14|151.62|0.990|
|**15**|180.24|178.30|0.989|163.34|161.40|0.988|
|**16**|190.31|187.71|0.986|173.26|171.04|0.987|
|**17**|196.09|195.34|0.996|179.10|178.31|0.996|
|**18**|202.67|202.30|0.998|185.67|185.36|0.998|
|**19**|210.17|209.34|0.996|193.21|192.43|0.996|
|**20**|210.26|209.32|0.996|193.40|192.30|0.994|
|**21**|210.16|209.60|0.997|193.43|192.64|0.996|
|**22**|210.51|209.52|0.995|193.49|192.54|0.995|
|**23**|209.72|209.54|0.999|193.10|192.55|0.997|
|**24**|209.97|209.62|0.998|192.94|192.72|0.999|
|**25**|210.39|210.15|0.999|193.82|193.63|0.999|
|**26**|210.46|210.22|0.999|193.90|193.70|0.999|
|**27**|210.76|210.34|0.998|194.25|193.64|0.997|
|**28**|210.78|210.26|0.998|194.66|193.65|0.995|
|**29**|211.41|210.25|0.995|195.05|193.77|0.993|
|**30**|212.04|210.22|0.991|195.19|193.86|0.993|
|**31**|212.40|210.57|0.991|195.75|193.91|0.991|
|**32**|212.52|210.40|0.990|195.94|193.90|0.990|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|13.92|13.01|0.934|12.25|11.66|0.952|
|2|16.26|16.21|0.997|14.45|14.38|0.996|
|3|19.77|19.90|1.006|17.26|17.30|1.002|
|4|21.94|22.18|1.011|18.21|18.48|1.015|
|5|25.00|24.92|0.997|20.93|20.68|0.988|
|6|27.46|27.40|0.998|22.18|22.19|1.000|
|7|29.75|29.45|0.990|23.23|23.46|1.010|
|8|32.34|32.34|1.000|25.59|25.65|1.002|
|9|34.71|34.50|0.994|26.88|27.06|1.007|
|10|36.66|36.48|0.995|28.77|28.91|1.005|
|11|38.90|38.93|1.001|30.43|30.37|0.998|
|12|41.13|41.00|0.997|32.06|32.02|0.999|
|13|43.30|43.26|0.999|33.90|34.11|1.006|
|14|45.48|45.42|0.999|35.76|35.58|0.995|
|**15**|48.13|47.50|0.987|38.44|37.44|0.974|
|16|48.17|48.17|1.000|38.65|38.55|0.998|
|17|48.44|48.39|0.999|38.71|38.57|0.996|
|18|48.46|48.46|1.000|38.56|38.64|1.002|
|19|48.34|48.39|1.001|38.51|38.64|1.003|
|20|48.33|48.40|1.001|38.54|38.51|0.999|
|21|48.50|48.54|1.001|38.55|38.61|1.001|
|22|48.55|48.58|1.000|38.63|38.54|0.998|
|23|48.52|48.54|1.000|38.64|38.50|0.996|
|24|48.31|48.39|1.002|38.61|38.54|0.998|
|25|48.56|48.45|0.998|38.64|38.58|0.998|
|26|48.64|48.56|0.998|38.75|38.66|0.998|
|27|48.58|48.77|1.004|38.72|38.72|1.000|
|28|48.70|48.66|0.999|38.72|38.78|1.001|
|29|48.53|48.61|1.002|38.69|38.69|1.000|
|30|48.48|48.63|1.003|38.89|38.66|0.994|
|31|48.50|48.72|1.005|38.73|38.81|1.002|
|32|48.66|48.68|1.000|38.88|38.80|0.998|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|25.41|25.54|1.005|21.53|21.46|0.997|
|2|37.87|37.63|0.994|29.66|29.59|0.998|
|3|47.66|47.77|1.002|37.63|37.78|1.004|
|4|58.51|58.58|1.001|46.15|46.20|1.001|
|5|69.15|68.85|0.996|55.02|54.86|0.997|
|6|78.38|78.64|1.003|64.29|64.09|0.997|
|7|88.03|87.88|0.998|72.91|73.24|1.005|
|8|97.15|97.10|0.999|81.12|81.31|1.002|
|9|106.21|106.15|0.999|90.18|90.06|0.999|
|10|115.41|115.10|0.997|98.61|98.60|1.000|
|11|124.32|124.25|0.999|107.39|107.20|0.998|
|12|132.66|132.67|1.000|115.87|115.84|1.000|
|13|141.06|141.41|1.002|124.28|124.33|1.000|
|14|149.42|149.66|1.002|132.62|132.70|1.001|
|15|157.98|157.95|1.000|140.98|141.14|1.001|
|16|166.55|166.50|1.000|149.26|149.29|1.000|
|17|175.27|175.54|1.002|158.00|158.10|1.001|
|18|183.46|183.71|1.001|166.47|166.45|1.000|
|19|191.95|191.74|0.999|174.77|174.77|1.000|
|20|200.46|200.34|0.999|183.22|183.21|1.000|
|21|208.82|208.56|0.999|191.78|191.73|1.000|
|22|217.20|216.98|0.999|199.78|199.81|1.000|
|23|225.39|225.50|1.000|208.30|208.26|1.000|
|24|233.76|233.55|0.999|216.54|216.74|1.001|
|25|242.43|242.27|0.999|225.28|225.20|1.000|
|26|251.14|251.34|1.001|233.93|233.91|1.000|
|27|259.38|259.36|1.000|242.12|242.01|1.000|
|28|267.76|267.77|1.000|250.54|250.50|1.000|
|29|276.01|275.86|0.999|258.96|258.91|1.000|
|30|284.43|284.32|1.000|266.94|267.12|1.001|
|31|292.76|292.48|0.999|275.35|275.45|1.000|
|32|300.81|300.60|0.999|283.40|283.40|1.000|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|27.70|22.80|0.823|24.59|19.62|0.798|
|2|33.36|33.50|1.004|26.58|26.60|1.001|
|3|43.17|43.27|1.002|34.07|34.15|1.002|
|4|52.89|52.74|0.997|41.71|41.44|0.993|
|5|62.00|62.09|1.001|48.74|48.85|1.002|
|6|70.62|70.72|1.001|56.49|56.56|1.001|
|7|79.07|79.12|1.001|64.18|64.08|0.999|
|8|87.17|87.02|0.998|71.73|71.58|0.998|
|9|94.75|94.88|1.001|79.19|79.24|1.001|
|10|102.58|102.56|1.000|86.78|86.90|1.001|
|11|110.44|110.45|1.000|94.42|94.31|0.999|
|12|118.16|118.08|0.999|101.88|101.82|0.999|
|13|125.78|125.81|1.000|109.17|109.23|1.001|
|14|133.46|133.38|0.999|116.65|116.76|1.001|
|15|140.87|141.06|1.001|124.28|124.06|0.998|
|**16**|145.54|141.78|0.974|128.58|125.05|0.973|
|**17**|156.01|142.15|0.911|139.26|125.26|0.899|
|**18**|163.38|142.18|0.870|146.66|125.45|0.855|
|**19**|170.90|142.22|0.832|154.15|125.23|0.812|
|**20**|178.23|142.27|0.798|161.68|125.43|0.776|
|**21**|154.86|142.42|0.920|138.21|125.58|0.909|
|**22**|156.77|142.46|0.909|140.03|125.55|0.897|
|**23**|158.64|142.38|0.898|141.89|125.51|0.885|
|**24**|160.29|142.51|0.889|143.64|125.66|0.875|
|**25**|162.54|142.82|0.879|145.86|126.17|0.865|
|**26**|164.43|142.87|0.869|147.73|126.22|0.854|
|**27**|165.31|142.65|0.863|148.77|125.97|0.847|
|**28**|167.24|142.58|0.853|150.72|126.00|0.836|
|**29**|169.87|142.98|0.842|153.12|126.13|0.824|
|**30**|171.02|142.80|0.835|154.42|126.02|0.816|
|**31**|173.42|143.01|0.825|156.94|126.38|0.805|
|**32**|174.59|142.70|0.817|158.01|126.16|0.798|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|39.27|36.35|0.926|31.74|28.82|0.908|
|2|52.66|52.54|0.998|39.98|40.15|1.004|
|3|68.12|67.91|0.997|53.06|53.04|1.000|
|**4**|83.52|82.63|0.989|67.90|66.55|0.980|
|5|95.06|95.10|1.000|78.62|78.62|1.000|
|6|108.25|108.26|1.000|91.77|91.86|1.001|
|7|121.26|121.34|1.001|104.58|104.52|0.999|
|8|134.30|134.18|0.999|117.59|117.74|1.001|
|9|147.88|147.88|1.000|130.22|130.25|1.000|
|10|160.54|160.61|1.000|142.93|142.73|0.999|
|11|173.06|173.10|1.000|155.41|155.59|1.001|
|12|185.90|185.87|1.000|168.09|168.08|1.000|
|13|198.33|198.21|0.999|180.68|180.61|1.000|
|14|210.30|210.51|1.001|193.13|193.19|1.000|
|15|222.84|222.81|1.000|205.89|205.82|1.000|
|16|235.44|235.24|0.999|218.19|218.21|1.000|
|17|249.37|249.31|1.000|232.77|232.60|0.999|
|18|261.94|262.14|1.001|245.21|245.06|0.999|
|19|274.29|274.27|1.000|257.50|257.72|1.001|
|20|282.74|282.63|1.000|265.91|265.84|1.000|
|21|291.30|290.96|0.999|274.34|274.42|1.000|
|22|299.54|299.30|0.999|282.60|282.70|1.000|
|23|307.61|307.82|1.001|291.14|291.14|1.000|
|24|316.42|316.38|1.000|299.44|299.38|1.000|
|25|324.93|325.03|1.000|308.15|308.13|1.000|
|26|333.06|333.06|1.000|316.19|316.42|1.001|
|27|341.51|341.42|1.000|324.69|324.83|1.000|
|28|349.78|349.88|1.000|333.09|333.32|1.001|
|29|358.02|357.95|1.000|341.42|341.31|1.000|
|30|366.59|366.66|1.000|349.93|349.72|0.999|
|31|374.95|374.96|1.000|358.41|358.18|0.999|
|32|383.27|383.44|1.000|366.54|366.77|1.001|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.98|17.10|1.007|15.63|15.50|0.992|
|2|23.08|23.08|1.000|21.05|21.02|0.999|
|3|26.96|27.04|1.003|24.46|24.50|1.002|
|4|33.37|33.35|1.000|29.98|30.00|1.001|
|5|37.36|37.32|0.999|33.82|33.78|0.999|
|6|42.35|42.32|0.999|38.47|38.44|0.999|
|7|47.01|47.07|1.001|42.87|42.72|0.996|
|8|51.74|51.64|0.998|47.15|46.97|0.996|
|9|56.50|56.44|0.999|51.41|51.43|1.000|
|10|61.67|61.74|1.001|55.99|55.95|0.999|
|11|66.13|66.11|1.000|60.38|60.19|0.997|
|12|70.90|70.95|1.001|65.22|65.02|0.997|
|13|75.45|75.54|1.001|69.02|68.86|0.998|
|14|79.79|79.98|1.002|73.72|73.63|0.999|
|15|84.62|84.81|1.002|77.78|77.43|0.996|
|16|89.27|89.22|0.999|82.46|82.58|1.002|
|17|94.05|93.82|0.998|86.62|86.70|1.001|
|18|98.65|98.78|1.001|91.00|91.31|1.003|
|19|103.18|103.33|1.001|95.61|95.73|1.001|
|20|107.43|107.80|1.003|99.87|99.86|1.000|
|21|112.34|112.42|1.001|104.10|104.44|1.003|
|22|116.67|116.56|0.999|108.40|108.57|1.002|
|23|121.15|121.36|1.002|113.02|112.90|0.999|
|24|125.78|125.83|1.000|116.95|116.90|1.000|
|25|130.46|130.62|1.001|121.50|121.75|1.002|
|26|134.89|135.11|1.002|125.50|126.06|1.004|
|27|139.38|139.34|1.000|129.94|130.20|1.002|
|28|143.88|144.02|1.001|134.32|134.32|1.000|
|29|148.42|148.37|1.000|138.45|138.44|1.000|
|30|152.97|153.04|1.000|143.18|143.09|0.999|
|31|157.27|157.28|1.000|147.14|146.83|0.998|
|32|161.98|161.84|0.999|151.38|151.44|1.000|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.75|14.53|0.985|13.76|13.98|1.016|
|2|17.33|17.33|1.000|16.14|16.10|0.998|
|3|20.54|20.70|1.008|19.10|19.06|0.998|
|4|24.73|25.04|1.013|22.79|22.90|1.005|
|5|27.47|27.41|0.998|25.46|25.40|0.997|
|6|29.65|29.72|1.002|27.58|27.68|1.003|
|7|32.69|32.78|1.003|30.24|30.18|0.998|
|8|36.57|36.66|1.002|33.62|33.78|1.005|
|9|39.26|39.49|1.006|36.58|36.70|1.004|
|10|41.98|41.97|1.000|39.00|38.99|1.000|
|11|45.26|45.16|0.998|41.81|41.88|1.002|
|12|48.02|48.04|1.000|44.60|44.66|1.001|
|13|50.83|51.02|1.004|47.72|47.26|0.990|
|14|53.23|53.22|1.000|49.86|49.86|1.000|
|15|56.03|56.22|1.003|52.78|52.84|1.001|
|16|59.01|58.97|0.999|55.15|55.13|1.000|
|17|61.81|62.02|1.003|57.83|57.90|1.001|
|18|64.62|64.60|1.000|60.86|60.90|1.001|
|19|67.66|67.70|1.001|63.26|63.47|1.003|
|20|70.50|70.41|0.999|65.91|65.95|1.001|
|21|72.65|72.76|1.002|68.34|68.50|1.002|
|22|75.42|75.82|1.005|71.46|71.48|1.000|
|23|78.40|78.67|1.003|74.32|74.05|0.996|
|24|81.26|81.10|0.998|76.72|76.45|0.996|
|25|83.82|83.80|1.000|79.46|79.32|0.998|
|26|87.03|86.71|0.996|81.99|82.11|1.001|
|27|89.62|89.86|1.003|84.29|84.54|1.003|
|28|92.74|92.17|0.994|86.69|86.90|1.002|
|29|95.36|95.15|0.998|89.98|89.96|1.000|
|30|98.10|97.54|0.994|92.57|92.99|1.005|
|31|100.55|100.63|1.001|95.13|95.14|1.000|
|32|104.06|103.53|0.995|97.66|97.37|0.997|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.37|16.31|0.997|14.82|14.79|0.998|
|2|21.93|21.75|0.992|19.90|19.84|0.997|
|3|25.56|25.55|1.000|22.86|22.86|1.000|
|4|29.42|29.51|1.003|26.43|26.42|1.000|
|5|34.71|34.80|1.003|31.05|30.90|0.995|
|6|38.66|38.73|1.002|34.67|34.70|1.001|
|7|42.78|42.82|1.001|38.30|38.33|1.001|
|8|47.29|47.26|0.999|42.18|42.28|1.002|
|9|51.07|51.11|1.001|45.84|45.91|1.002|
|10|55.34|55.46|1.002|49.61|49.62|1.000|
|11|59.44|59.42|1.000|53.26|53.35|1.002|
|12|63.52|63.44|0.999|56.70|56.82|1.002|
|13|67.63|67.60|1.000|60.73|60.66|0.999|
|14|71.44|71.40|0.999|64.00|64.04|1.001|
|15|75.63|75.57|0.999|68.08|68.09|1.000|
|16|75.49|75.32|0.998|67.82|67.99|1.002|
|17|75.57|75.59|1.000|68.00|68.07|1.001|
|18|75.59|75.54|0.999|68.07|68.08|1.000|
|19|75.54|75.52|1.000|68.06|68.20|1.002|
|20|75.54|75.53|1.000|68.10|68.10|1.000|
|21|75.70|75.61|0.999|68.11|68.13|1.000|
|22|75.46|75.54|1.001|68.02|67.97|0.999|
|23|75.62|75.59|1.000|68.10|68.06|0.999|
|24|75.63|75.63|1.000|68.03|68.15|1.002|
|25|76.04|75.80|0.997|68.14|68.26|1.002|
|26|75.80|75.86|1.001|68.10|68.14|1.001|
|27|75.90|75.93|1.000|68.10|68.11|1.000|
|28|75.81|75.82|1.000|68.18|68.22|1.001|
|29|75.84|75.98|1.002|68.34|68.22|0.998|
|30|76.04|75.93|0.999|68.16|68.29|1.002|
|31|76.07|75.98|0.999|68.23|68.22|1.000|
|32|75.84|75.76|0.999|68.10|68.18|1.001|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.94|14.07|1.010|13.02|13.12|1.008|
|2|16.75|16.81|1.003|15.61|15.42|0.988|
|3|19.64|19.84|1.010|17.66|17.70|1.002|
|4|21.95|22.20|1.011|20.03|20.06|1.002|
|5|24.45|24.41|0.998|22.29|22.32|1.001|
|6|26.98|26.85|0.995|24.20|24.30|1.004|
|7|29.51|29.55|1.001|26.56|26.53|0.999|
|8|31.50|31.56|1.002|28.34|28.39|1.002|
|9|33.76|33.78|1.001|30.31|30.35|1.001|
|10|36.08|36.06|1.000|32.36|32.48|1.004|
|11|37.93|37.90|0.999|34.66|34.58|0.998|
|12|40.09|40.29|1.005|36.45|36.52|1.002|
|13|42.40|42.45|1.001|38.35|38.34|1.000|
|14|44.48|44.36|0.997|40.51|40.46|0.999|
|15|46.49|46.50|1.000|42.21|42.30|1.002|
|16|46.49|46.34|0.997|42.36|42.26|0.998|
|17|46.60|46.41|0.996|42.42|42.43|1.000|
|18|46.62|46.62|1.000|42.36|42.55|1.005|
|19|46.56|46.53|0.999|42.50|42.60|1.002|
|20|46.50|46.54|1.001|42.31|42.40|1.002|
|21|46.58|46.72|1.003|42.48|42.41|0.998|
|22|46.66|46.67|1.000|42.34|42.42|1.002|
|23|46.70|46.66|0.999|42.58|42.47|0.998|
|24|46.56|46.64|1.002|42.51|42.49|0.999|
|25|46.90|46.88|1.000|42.63|42.53|0.998|
|26|46.86|46.86|1.000|42.87|42.42|0.989|
|27|46.87|46.94|1.001|42.63|42.51|0.997|
|28|46.88|46.78|0.998|42.83|42.79|0.999|
|29|46.94|46.83|0.998|42.89|42.69|0.995|
|30|47.01|47.02|1.000|42.73|42.79|1.001|
|31|47.04|46.83|0.996|42.55|42.85|1.007|
|32|46.89|46.94|1.001|42.50|42.58|1.002|

`e256_i2048_k6_clamp10`: hidden 4096, intermediate 2048, 256 experts,
top-6, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.41|24.43|1.001|19.95|19.91|0.998|
|2|37.66|37.77|1.003|29.53|29.53|1.000|
|3|49.95|49.94|1.000|38.50|38.48|0.999|
|4|61.34|61.24|0.998|48.10|48.10|1.000|
|5|72.46|72.42|1.000|58.06|58.03|1.000|
|6|82.57|82.48|0.999|67.30|67.33|1.000|
|7|95.06|94.97|0.999|79.51|79.45|0.999|
|8|104.83|104.75|0.999|89.35|89.15|0.998|
|9|115.78|115.80|1.000|99.95|100.00|1.000|
|10|125.02|124.98|1.000|108.84|108.80|1.000|
|11|134.10|133.98|0.999|117.61|117.53|0.999|
|12|144.14|144.14|1.000|127.30|127.38|1.001|
|13|152.86|152.86|1.000|135.90|135.80|0.999|
|14|163.12|163.25|1.001|145.81|145.74|1.000|
|15|172.62|172.71|1.001|155.19|155.08|0.999|
|16|172.94|172.86|1.000|155.71|155.61|0.999|
|17|173.36|173.44|1.000|156.03|156.02|1.000|
|18|173.46|173.48|1.000|156.01|156.10|1.001|
|19|173.46|173.59|1.001|156.22|156.14|0.999|
|20|173.83|173.67|0.999|156.78|156.66|0.999|
|21|173.60|173.66|1.000|156.54|156.61|1.000|
|22|173.76|173.58|0.999|156.28|156.34|1.000|
|23|172.66|172.58|1.000|155.75|155.58|0.999|
|24|173.72|173.73|1.000|156.47|156.30|0.999|
|25|174.80|174.88|1.000|157.82|157.70|0.999|
|26|174.72|174.57|0.999|157.16|157.14|1.000|
|27|174.77|174.72|1.000|157.23|157.12|0.999|
|28|175.05|175.10|1.000|157.46|157.40|1.000|
|29|175.07|175.06|1.000|158.33|158.34|1.000|
|30|175.38|175.26|0.999|158.70|158.55|0.999|
|31|174.98|174.94|1.000|157.83|157.74|0.999|
|32|174.06|173.71|0.998|156.92|156.71|0.999|

**sm_103a** (NVIDIA GB300, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake
selection, new = this PR; ratio = new / previous. **Bold** num_tokens =
rows this PR routes to a different schedule.

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|15.71|14.06|0.895|14.30|12.65|0.885|
|**2**|18.74|18.66|0.996|16.30|16.27|0.998|
|**3**|21.62|21.46|0.993|18.45|18.34|0.994|
|4|25.45|25.42|0.999|21.19|21.27|1.004|
|5|27.98|28.18|1.007|22.85|22.90|1.002|
|6|31.42|31.40|0.999|25.64|25.80|1.006|
|7|33.96|33.93|0.999|27.12|27.37|1.009|
|8|37.02|36.91|0.997|29.60|29.58|0.999|
|9|39.78|39.78|1.000|31.86|31.56|0.990|
|10|42.51|42.42|0.998|34.26|34.23|0.999|
|11|45.19|45.25|1.001|36.34|36.30|0.999|
|12|47.88|47.90|1.001|38.64|38.72|1.002|
|13|50.58|50.74|1.003|40.92|40.83|0.998|
|14|53.50|53.41|0.998|43.18|43.09|0.998|
|15|56.33|56.43|1.002|45.60|45.64|1.001|
|16|59.02|58.87|0.998|47.98|47.94|0.999|
|17|61.30|61.23|0.999|50.00|50.09|1.002|
|18|63.78|63.80|1.000|52.27|52.36|1.002|
|19|66.54|66.34|0.997|54.64|54.62|1.000|
|20|68.86|68.90|1.001|57.10|56.94|0.997|
|21|71.32|71.50|1.002|59.38|59.42|1.001|
|22|73.70|73.66|0.999|61.40|61.56|1.003|
|**23**|78.09|76.04|0.974|65.26|63.72|0.976|
|**24**|80.42|78.77|0.979|67.37|66.16|0.982|
|**25**|82.55|81.07|0.982|69.79|68.56|0.982|
|**26**|85.06|83.38|0.980|72.33|71.04|0.982|
|**27**|87.35|85.90|0.983|74.22|73.16|0.986|
|**28**|89.86|88.25|0.982|76.65|75.38|0.983|
|**29**|92.18|90.93|0.986|78.78|77.78|0.987|
|**30**|94.52|93.38|0.988|81.06|80.05|0.987|
|**31**|96.94|95.95|0.990|83.20|82.50|0.992|
|**32**|99.16|98.45|0.993|85.19|84.61|0.993|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.38|13.51|1.010|11.96|11.94|0.999|
|2|16.61|16.61|1.000|14.81|14.71|0.993|
|3|20.62|20.58|0.998|17.76|17.66|0.994|
|4|23.64|23.16|0.980|19.33|19.24|0.995|
|**5**|26.68|26.58|0.996|21.93|21.59|0.985|
|**6**|29.54|29.18|0.988|23.93|23.49|0.982|
|**7**|32.52|32.10|0.987|25.81|25.42|0.985|
|8|34.62|34.63|1.000|27.34|27.38|1.001|
|9|37.01|36.95|0.998|28.90|28.80|0.996|
|10|39.50|39.66|1.004|30.86|31.12|1.008|
|11|41.02|41.10|1.002|33.14|33.22|1.002|
|12|43.01|42.97|0.999|34.95|34.82|0.996|
|13|44.89|44.97|1.002|36.61|36.68|1.002|
|14|46.82|46.86|1.001|38.25|38.31|1.002|
|15|49.17|49.07|0.998|40.25|40.05|0.995|
|16|50.59|50.70|1.002|41.32|41.38|1.002|
|17|52.54|52.49|0.999|42.44|42.39|0.999|
|18|54.38|54.20|0.997|43.95|44.01|1.001|
|19|56.32|56.18|0.998|45.18|45.23|1.001|
|20|57.99|57.90|0.998|46.35|46.38|1.001|
|21|59.74|59.70|0.999|47.62|47.78|1.003|
|22|61.55|61.42|0.998|49.58|49.48|0.998|
|23|63.23|63.26|1.001|50.74|50.59|0.997|
|24|64.84|64.79|0.999|52.23|52.17|0.999|
|25|66.89|66.84|0.999|53.90|53.91|1.000|
|26|68.49|68.51|1.000|55.40|55.35|0.999|
|27|68.39|68.48|1.001|55.28|55.23|0.999|
|28|68.46|68.38|0.999|55.39|55.37|1.000|
|29|68.42|68.54|1.002|55.36|55.50|1.003|
|30|68.52|68.41|0.998|55.42|55.28|0.997|
|31|68.48|68.46|1.000|55.33|55.42|1.002|
|32|68.51|68.46|0.999|55.52|55.44|0.999|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|20.51|19.99|0.975|18.33|17.50|0.955|
|2|25.61|25.86|1.010|21.08|21.28|1.009|
|3|31.08|30.92|0.995|25.30|25.37|1.003|
|4|38.74|38.71|0.999|31.02|30.90|0.996|
|5|43.14|43.33|1.004|34.42|34.38|0.999|
|6|47.95|47.90|0.999|38.18|38.33|1.004|
|7|54.81|54.93|1.002|43.38|43.61|1.005|
|8|59.44|59.70|1.004|47.32|47.17|0.997|
|9|64.04|64.03|1.000|50.91|51.07|1.003|
|10|69.22|69.50|1.004|56.38|56.57|1.003|
|11|73.46|73.39|0.999|60.37|60.22|0.997|
|12|77.64|77.70|1.001|64.36|64.37|1.000|
|13|82.74|82.69|0.999|69.67|69.34|0.995|
|14|87.06|87.23|1.002|74.10|73.93|0.998|
|15|91.12|91.18|1.001|77.79|77.79|1.000|
|16|95.60|95.70|1.001|82.49|82.82|1.004|
|17|100.50|100.27|0.998|87.27|87.21|0.999|
|18|104.57|104.90|1.003|91.46|91.52|1.001|
|19|109.14|109.11|1.000|96.14|96.02|0.999|
|20|113.86|113.76|0.999|100.50|100.58|1.001|
|21|118.41|118.22|0.998|104.93|104.86|0.999|
|22|122.94|122.82|0.999|109.07|109.22|1.001|
|23|127.02|127.37|1.003|113.59|113.82|1.002|
|24|131.77|131.82|1.000|118.15|118.34|1.002|
|25|136.20|136.00|0.999|122.62|122.45|0.999|
|26|140.75|140.53|0.998|126.78|126.81|1.000|
|27|144.94|144.90|1.000|131.57|131.45|0.999|
|28|149.38|149.38|1.000|135.82|135.78|1.000|
|29|153.60|153.62|1.000|140.04|140.11|1.001|
|30|158.10|157.95|0.999|144.82|144.36|0.997|
|31|162.09|162.00|0.999|148.81|148.79|1.000|
|32|166.54|166.58|1.000|153.24|153.37|1.001|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|13.48|11.88|0.881|12.22|10.82|0.886|
|2|14.56|14.51|0.997|13.09|13.12|1.002|
|3|16.99|16.94|0.997|15.02|14.99|0.998|
|4|19.36|19.27|0.995|17.32|17.28|0.998|
|5|21.18|21.23|1.002|18.17|18.07|0.995|
|6|23.01|23.14|1.006|19.53|19.38|0.993|
|7|25.72|25.60|0.995|21.74|21.71|0.999|
|8|27.07|27.20|1.005|22.57|22.65|1.004|
|9|28.97|28.98|1.000|23.65|23.70|1.002|
|10|31.17|31.18|1.000|26.02|26.02|1.000|
|11|33.18|33.16|0.999|27.21|27.26|1.002|
|12|34.90|34.77|0.996|28.00|28.23|1.008|
|13|36.59|36.85|1.007|29.77|29.90|1.005|
|14|38.23|38.26|1.001|30.87|30.82|0.998|
|15|40.02|39.93|0.998|32.00|32.05|1.001|
|16|41.38|41.71|1.008|33.55|33.60|1.001|
|17|43.38|43.22|0.996|34.98|35.02|1.001|
|18|44.83|44.87|1.001|36.11|36.15|1.001|
|19|46.74|46.65|0.998|37.58|37.70|1.003|
|20|48.10|48.24|1.003|38.82|38.77|0.999|
|21|49.90|49.90|1.000|40.22|40.16|0.998|
|22|51.54|51.71|1.003|41.70|41.76|1.002|
|23|53.37|53.28|0.998|43.14|43.04|0.998|
|24|54.97|55.01|1.001|44.49|44.44|0.999|
|25|56.50|56.58|1.001|45.84|45.80|0.999|
|26|58.22|58.05|0.997|47.14|47.40|1.006|
|27|59.81|59.86|1.001|48.53|48.65|1.002|
|28|61.45|61.14|0.995|50.01|50.17|1.003|
|29|62.75|62.84|1.001|51.48|51.53|1.001|
|30|64.43|64.40|0.999|52.74|52.67|0.999|
|31|66.01|66.03|1.000|54.34|54.22|0.998|
|32|67.78|67.79|1.000|55.70|55.54|0.997|

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|14.91|13.94|0.935|13.44|12.42|0.924|
|2|18.70|18.75|1.003|16.56|16.70|1.009|
|3|22.61|22.63|1.001|19.26|19.22|0.998|
|4|26.35|26.29|0.998|21.79|21.78|1.000|
|5|30.22|30.22|1.000|24.99|25.06|1.003|
|6|33.31|33.55|1.007|27.16|27.15|1.000|
|7|36.58|36.70|1.003|29.62|29.54|0.997|
|8|35.89|36.03|1.004|32.00|31.98|0.999|
|9|39.59|39.60|1.000|35.15|35.14|1.000|
|10|42.21|42.26|1.001|37.66|37.63|0.999|
|11|44.83|44.92|1.002|40.07|40.06|1.000|
|12|47.44|47.53|1.002|42.29|42.50|1.005|
|13|50.24|50.06|0.996|44.78|44.90|1.003|
|14|52.67|52.71|1.001|47.26|47.43|1.004|
|15|55.45|55.64|1.003|49.67|49.71|1.001|
|16|58.02|58.19|1.003|52.10|52.01|0.998|
|17|60.19|60.14|0.999|53.86|54.08|1.004|
|18|61.93|62.05|1.002|55.72|55.74|1.000|
|19|63.70|63.80|1.002|57.47|57.38|0.998|
|20|64.63|64.70|1.001|57.94|57.89|0.999|
|21|64.85|64.99|1.002|58.21|57.96|0.996|
|22|64.98|65.00|1.000|58.19|58.09|0.998|
|23|64.82|64.60|0.997|57.57|58.11|1.009|
|24|64.53|64.72|1.003|58.22|58.03|0.997|
|25|64.67|64.81|1.002|58.23|58.21|1.000|
|26|65.06|65.20|1.002|58.55|58.38|0.997|
|27|65.12|65.03|0.999|58.34|58.45|1.002|
|28|65.22|65.10|0.998|58.35|58.50|1.003|
|29|65.21|65.18|1.000|58.44|58.32|0.998|
|30|65.16|65.12|0.999|58.46|58.36|0.998|
|31|65.24|65.16|0.999|58.47|58.31|0.997|
|32|65.18|65.14|0.999|58.38|58.39|1.000|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|13.64|12.72|0.933|12.57|11.66|0.927|
|2|15.91|15.91|1.000|14.25|14.29|1.003|
|3|19.43|19.26|0.991|16.88|17.07|1.011|
|4|21.41|21.33|0.996|18.54|18.68|1.008|
|5|24.75|24.87|1.005|21.03|20.94|0.996|
|6|26.95|26.86|0.996|22.00|22.20|1.009|
|7|29.16|29.28|1.004|23.86|23.78|0.997|
|8|31.85|31.77|0.997|25.71|25.90|1.007|
|9|33.87|33.86|1.000|27.37|27.49|1.004|
|10|36.45|36.22|0.994|29.34|29.38|1.001|
|11|38.18|38.26|1.002|30.70|30.75|1.002|
|12|40.36|40.42|1.002|32.64|32.62|0.999|
|13|42.46|42.49|1.001|34.35|34.35|1.000|
|14|44.68|44.86|1.004|36.06|36.19|1.004|
|**15**|48.63|46.54|0.957|38.92|37.93|0.975|
|16|48.30|48.42|1.002|39.06|38.88|0.995|
|17|48.53|48.58|1.001|39.30|39.22|0.998|
|18|48.55|48.45|0.998|39.25|39.32|1.002|
|19|48.59|48.46|0.997|39.22|39.25|1.001|
|20|48.50|48.54|1.001|39.24|39.09|0.996|
|21|48.44|48.51|1.001|39.23|39.12|0.997|
|22|48.70|48.46|0.995|39.10|39.14|1.001|
|23|48.64|48.51|0.997|39.14|39.23|1.002|
|24|48.64|48.65|1.000|39.28|39.41|1.003|
|25|48.81|48.69|0.998|39.31|39.23|0.998|
|26|48.73|48.76|1.001|39.33|39.43|1.003|
|27|48.82|48.66|0.997|39.38|39.29|0.998|
|28|48.83|48.74|0.998|39.37|39.36|1.000|
|29|48.84|48.82|1.000|39.35|39.58|1.006|
|30|48.87|48.81|0.999|39.34|39.34|1.000|
|31|48.86|48.81|0.999|39.38|39.26|0.997|
|32|48.75|48.83|1.002|39.38|39.39|1.000|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.36|14.38|1.002|13.50|13.46|0.998|
|2|17.00|17.09|1.005|15.76|15.87|1.007|
|3|20.44|20.40|0.998|18.87|18.90|1.001|
|4|24.30|24.47|1.007|22.62|22.68|1.003|
|5|26.82|26.82|1.000|24.73|24.74|1.001|
|6|29.28|29.41|1.004|27.19|27.26|1.002|
|7|32.28|32.45|1.005|30.01|30.17|1.005|
|8|36.48|36.50|1.000|33.40|33.22|0.994|
|9|38.85|38.91|1.002|36.18|36.26|1.002|
|10|41.61|41.59|1.000|38.83|38.85|1.000|
|11|44.57|44.50|0.998|41.58|41.63|1.001|
|12|47.70|47.55|0.997|44.32|44.29|0.999|
|13|50.54|50.69|1.003|47.18|47.14|0.999|
|14|53.12|53.05|0.999|49.62|49.44|0.996|
|15|55.98|55.97|1.000|52.46|52.46|1.000|
|16|58.54|58.65|1.002|55.04|54.90|0.998|
|17|61.37|61.49|1.002|57.83|57.74|0.998|
|18|64.12|64.29|1.003|60.40|60.19|0.997|
|19|67.18|67.03|0.998|63.07|63.05|1.000|
|20|69.87|69.78|0.999|65.98|65.58|0.994|
|21|72.28|72.54|1.004|68.44|68.40|0.999|
|22|75.25|75.51|1.004|71.30|70.94|0.995|
|23|78.42|78.29|0.998|73.77|73.66|0.999|
|24|80.79|81.19|1.005|76.58|76.54|0.999|
|25|84.14|83.91|0.997|79.42|79.34|0.999|
|26|86.74|86.82|1.001|82.32|81.81|0.994|
|27|89.57|89.75|1.002|84.51|84.52|1.000|
|28|92.44|92.48|1.000|87.76|87.78|1.000|
|29|95.41|95.15|0.997|90.57|90.53|1.000|
|30|97.88|98.06|1.002|92.87|92.82|0.999|
|31|100.39|100.47|1.001|95.36|95.20|0.998|
|32|103.28|103.46|1.002|98.28|98.10|0.998|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.86|13.92|1.004|13.02|12.92|0.992|
|2|16.39|16.36|0.998|15.06|14.94|0.992|
|3|19.12|19.15|1.002|17.62|17.46|0.991|
|4|21.58|21.65|1.003|19.89|19.82|0.996|
|5|23.84|23.93|1.004|21.97|21.91|0.997|
|6|26.38|26.27|0.996|24.00|24.00|1.000|
|7|29.18|29.05|0.996|26.53|26.46|0.998|
|8|31.10|31.10|1.000|28.25|28.31|1.002|
|9|33.36|33.23|0.996|30.42|30.24|0.994|
|10|35.50|35.57|1.002|32.46|32.35|0.997|
|11|38.16|38.07|0.998|34.70|34.65|0.999|
|12|40.04|40.06|1.000|36.46|36.50|1.001|
|13|42.15|42.23|1.002|38.50|38.50|1.000|
|14|44.16|44.23|1.002|40.47|40.32|0.996|
|15|46.34|46.39|1.001|42.46|42.28|0.996|
|16|46.46|46.47|1.000|42.34|42.28|0.998|
|17|46.54|46.50|0.999|42.54|42.62|1.002|
|18|46.65|46.62|0.999|42.59|42.49|0.998|
|19|46.62|46.58|0.999|42.42|42.63|1.005|
|20|46.60|46.57|0.999|42.45|42.31|0.997|
|21|46.74|46.50|0.995|42.70|42.60|0.998|
|22|46.71|46.59|0.997|42.50|42.58|1.002|
|23|46.71|46.73|1.000|42.66|42.54|0.997|
|24|46.63|46.62|1.000|42.54|42.52|0.999|
|25|46.74|46.80|1.001|42.62|42.72|1.002|
|26|46.91|46.96|1.001|42.84|42.81|0.999|
|27|46.89|46.82|0.999|42.80|42.62|0.996|
|28|46.83|46.83|1.000|42.54|42.60|1.001|
|29|47.09|46.83|0.995|42.81|42.79|1.000|
|30|46.97|46.91|0.999|42.78|42.76|1.000|
|31|46.82|47.07|1.005|42.75|42.74|1.000|
|32|46.89|46.92|1.001|42.60|42.67|1.002|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|31.78|26.54|0.835|27.12|22.59|0.833|
|2|40.60|40.48|0.997|32.62|32.67|1.001|
|3|53.28|53.43|1.003|42.69|42.69|1.000|
|4|65.25|65.29|1.001|52.87|53.16|1.005|
|5|76.72|76.71|1.000|63.30|63.26|0.999|
|6|87.23|87.35|1.001|73.73|73.89|1.002|
|7|97.78|98.10|1.003|84.26|84.44|1.002|
|8|108.71|108.74|1.000|94.92|94.78|0.999|
|9|119.11|119.12|1.000|105.18|105.22|1.000|
|10|129.39|129.36|1.000|115.57|115.79|1.002|
|11|139.50|139.42|0.999|125.27|125.26|1.000|
|12|149.31|149.46|1.001|135.22|135.41|1.001|
|13|159.26|159.17|0.999|145.31|145.26|1.000|
|14|169.30|169.18|0.999|155.49|155.40|0.999|
|15|179.11|178.94|0.999|165.51|165.29|0.999|
|16|188.81|188.86|1.000|175.38|175.60|1.001|
|17|196.59|196.75|1.001|183.31|183.30|1.000|
|18|203.80|203.57|0.999|190.47|190.38|1.000|
|19|210.70|210.78|1.000|197.70|197.58|0.999|
|20|210.74|210.88|1.001|197.66|197.68|1.000|
|21|210.95|210.97|1.000|197.81|197.74|1.000|
|22|210.77|211.00|1.001|197.76|197.68|1.000|
|23|211.00|210.94|1.000|197.90|197.83|1.000|
|24|210.95|210.98|1.000|197.92|198.06|1.001|
|25|211.77|211.58|0.999|198.67|198.59|1.000|
|26|211.88|211.72|0.999|198.74|198.62|0.999|
|27|211.81|211.96|1.001|198.63|198.69|1.000|
|28|211.87|211.86|1.000|198.76|198.70|1.000|
|29|211.86|212.02|1.001|198.79|198.79|1.000|
|30|211.90|211.90|1.000|198.96|199.04|1.000|
|31|211.90|211.88|1.000|198.93|198.81|0.999|
|32|211.89|212.11|1.001|198.99|198.98|1.000|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|25.10|25.05|0.998|21.59|21.77|1.008|
|2|37.68|37.70|1.000|30.66|30.73|1.002|
|3|48.07|48.10|1.001|39.12|39.02|0.998|
|4|58.62|58.89|1.005|47.72|47.82|1.002|
|5|68.71|68.79|1.001|56.85|56.78|0.999|
|6|78.70|78.56|0.998|65.76|65.85|1.001|
|7|88.50|88.54|1.000|74.98|75.02|1.001|
|8|97.82|97.82|1.000|83.58|83.41|0.998|
|9|106.07|106.06|1.000|91.95|92.01|1.001|
|10|115.10|115.24|1.001|100.94|100.94|1.000|
|11|124.22|123.99|0.998|109.80|109.88|1.001|
|12|132.88|132.74|0.999|118.65|118.62|1.000|
|13|141.52|141.54|1.000|127.55|127.58|1.000|
|14|149.88|149.78|0.999|135.90|135.87|1.000|
|15|158.58|158.59|1.000|144.52|144.78|1.002|
|16|166.90|166.82|0.999|153.30|153.10|0.999|
|17|175.87|175.80|1.000|162.39|162.26|0.999|
|18|184.37|184.38|1.000|171.01|170.98|1.000|
|19|192.69|192.69|1.000|179.40|179.51|1.001|
|20|201.22|201.20|1.000|188.22|188.13|0.999|
|21|209.74|209.56|0.999|196.58|196.62|1.000|
|22|218.13|218.16|1.000|205.23|205.34|1.001|
|23|226.43|226.49|1.000|213.80|213.88|1.000|
|24|235.18|234.83|0.999|222.62|222.35|0.999|
|25|243.59|243.66|1.000|231.30|231.42|1.000|
|26|252.58|252.50|1.000|240.22|240.30|1.000|
|27|260.81|260.90|1.000|248.67|248.70|1.000|
|28|269.46|269.46|1.000|257.41|257.43|1.000|
|29|277.80|278.00|1.001|266.02|266.13|1.000|
|30|286.46|286.51|1.000|274.50|274.45|1.000|
|31|295.15|294.86|0.999|283.30|282.90|0.999|
|32|303.32|303.28|1.000|291.45|291.42|1.000|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|**1**|27.34|22.55|0.825|24.02|19.42|0.809|
|2|33.18|33.20|1.000|26.99|27.09|1.004|
|3|42.90|42.90|1.000|34.54|34.54|1.000|
|4|52.60|52.39|0.996|42.24|42.18|0.998|
|5|61.52|61.65|1.002|49.90|49.95|1.001|
|6|70.46|70.45|1.000|57.59|57.65|1.001|
|7|78.81|78.82|1.000|65.66|65.66|1.000|
|8|86.90|86.94|1.000|73.54|73.58|1.000|
|9|94.90|94.72|0.998|81.34|81.45|1.001|
|10|102.54|102.51|1.000|89.10|89.10|1.000|
|11|110.50|110.40|0.999|97.02|96.86|0.998|
|12|118.06|118.22|1.001|104.50|104.62|1.001|
|13|125.93|126.00|1.001|112.35|112.26|0.999|
|14|133.70|133.65|1.000|120.04|120.00|1.000|
|15|141.17|141.22|1.000|127.74|127.76|1.000|
|16|142.23|142.22|1.000|128.19|128.22|1.000|
|**17**|156.36|142.81|0.913|143.29|128.63|0.898|
|**18**|164.08|142.76|0.870|150.98|128.71|0.853|
|19|142.70|142.72|1.000|128.70|128.71|1.000|
|20|142.84|142.94|1.001|128.79|128.86|1.001|
|21|142.75|142.85|1.001|128.80|128.85|1.000|
|22|142.90|142.86|1.000|128.91|128.94|1.000|
|23|142.85|142.82|1.000|128.87|128.91|1.000|
|24|142.88|142.82|1.000|128.98|128.91|0.999|
|25|143.22|143.33|1.001|129.45|129.38|1.000|
|26|143.35|143.38|1.000|129.38|129.34|1.000|
|27|143.42|143.42|1.000|129.47|129.49|1.000|
|28|143.54|143.54|1.000|129.58|129.54|1.000|
|29|143.54|143.54|1.000|129.63|129.56|0.999|
|30|143.56|143.66|1.001|129.59|129.64|1.000|
|31|143.54|143.57|1.000|129.54|129.70|1.001|
|32|143.61|143.60|1.000|129.59|129.60|1.000|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|36.82|36.55|0.993|29.53|29.52|1.000|
|2|52.70|52.65|0.999|41.24|40.97|0.993|
|3|67.32|67.30|1.000|54.18|54.30|1.002|
|**4**|82.77|82.21|0.993|69.62|68.08|0.978|
|5|95.06|95.00|0.999|80.78|80.66|0.999|
|6|108.40|108.42|1.000|94.10|94.06|1.000|
|7|121.45|121.43|1.000|106.94|107.01|1.001|
|8|134.10|134.10|1.000|120.74|120.15|0.995|
|9|148.13|148.14|1.000|133.83|134.02|1.001|
|10|160.68|160.67|1.000|147.08|146.97|0.999|
|11|173.61|173.47|0.999|159.82|160.09|1.002|
|12|186.43|186.22|0.999|172.71|172.85|1.001|
|13|198.95|198.90|1.000|185.65|185.82|1.001|
|14|211.74|211.69|1.000|198.74|198.69|1.000|
|15|224.46|224.31|0.999|211.51|211.75|1.001|
|16|237.10|237.17|1.000|224.42|224.38|1.000|
|17|251.96|251.75|0.999|239.54|239.70|1.001|
|18|264.48|264.62|1.001|252.56|252.42|0.999|
|19|277.18|277.38|1.001|265.30|265.38|1.000|
|20|285.81|285.71|1.000|273.90|273.94|1.000|
|21|294.32|294.26|1.000|282.76|282.59|0.999|
|22|302.65|302.80|1.001|291.35|291.25|1.000|
|23|311.10|310.79|0.999|299.86|299.89|1.000|
|24|319.91|319.71|0.999|308.49|308.51|1.000|
|25|328.60|328.72|1.000|317.41|317.34|1.000|
|26|337.00|336.84|1.000|326.00|326.06|1.000|
|27|345.46|345.35|1.000|334.58|334.66|1.000|
|28|353.97|353.78|0.999|343.14|343.00|1.000|
|29|362.48|362.59|1.000|351.91|351.77|1.000|
|30|371.22|370.98|0.999|360.32|360.43|1.000|
|31|379.54|379.74|1.001|369.08|369.03|1.000|
|32|388.22|388.14|1.000|377.82|377.76|1.000|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.70|16.74|1.002|15.06|15.26|1.013|
|2|22.42|22.44|1.001|20.42|20.66|1.012|
|3|26.73|26.72|1.000|24.63|24.58|0.998|
|4|32.82|32.86|1.001|29.78|29.74|0.999|
|5|36.83|36.93|1.003|33.74|33.74|1.000|
|6|41.82|41.87|1.001|38.65|38.50|0.996|
|7|46.78|46.72|0.999|43.22|43.08|0.997|
|8|51.44|51.35|0.998|47.56|47.47|0.998|
|9|56.40|56.38|1.000|52.03|52.21|1.003|
|10|61.43|61.42|1.000|56.86|56.86|1.000|
|11|66.29|66.18|0.998|61.27|61.30|1.000|
|12|71.15|71.04|0.998|66.36|66.34|1.000|
|13|75.70|75.50|0.997|70.46|70.44|1.000|
|14|80.24|80.37|1.002|74.75|74.78|1.000|
|15|85.42|85.21|0.997|79.83|79.60|0.997|
|16|89.82|89.66|0.998|83.98|83.81|0.998|
|17|94.43|94.46|1.000|88.32|88.32|1.000|
|18|99.26|99.22|1.000|92.79|92.82|1.000|
|19|103.63|103.73|1.001|97.22|97.37|1.001|
|20|108.59|108.30|0.997|101.86|101.78|0.999|
|21|112.77|112.74|1.000|105.90|106.10|1.002|
|22|117.57|117.48|0.999|110.94|110.85|0.999|
|23|122.13|122.19|1.001|115.11|115.09|1.000|
|24|126.57|126.50|0.999|119.65|119.52|0.999|
|25|131.58|131.37|0.998|124.22|123.95|0.998|
|26|136.08|136.08|1.000|128.77|128.83|1.000|
|27|140.67|140.53|0.999|133.02|133.19|1.001|
|28|145.11|145.01|0.999|137.54|137.56|1.000|
|29|149.75|149.82|1.000|141.98|142.06|1.001|
|30|154.13|154.25|1.001|146.62|146.37|0.998|
|31|158.81|158.81|1.000|150.73|150.66|1.000|
|32|163.29|163.43|1.001|155.03|155.30|1.002|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.10|16.02|0.995|14.57|14.58|1.001|
|2|21.64|21.61|0.999|19.64|19.65|1.000|
|3|25.44|25.44|1.000|22.98|23.10|1.006|
|4|29.55|29.48|0.998|26.83|26.89|1.002|
|5|34.43|34.46|1.001|31.35|31.30|0.998|
|6|38.18|38.20|1.000|34.82|34.78|0.999|
|7|42.49|42.55|1.002|38.87|38.97|1.002|
|8|46.84|46.84|1.000|42.58|42.40|0.996|
|9|51.10|51.15|1.001|46.58|46.61|1.001|
|10|55.18|55.20|1.000|50.45|50.46|1.000|
|11|59.00|59.05|1.001|54.02|54.03|1.000|
|12|63.06|63.14|1.001|57.85|57.93|1.001|
|13|67.38|67.22|0.998|61.62|61.66|1.001|
|14|71.33|71.34|1.000|65.50|65.49|1.000|
|15|75.26|75.30|1.000|69.21|69.26|1.001|
|16|75.26|75.34|1.001|69.12|69.12|1.000|
|17|75.54|75.51|1.000|69.34|69.38|1.000|
|18|75.63|75.43|0.997|69.46|69.35|0.998|
|19|75.58|75.46|0.998|69.42|69.20|0.997|
|20|75.50|75.50|1.000|69.27|69.40|1.002|
|21|75.66|75.59|0.999|69.37|69.38|1.000|
|22|75.72|75.64|0.999|69.50|69.46|0.999|
|23|75.70|75.65|0.999|69.44|69.33|0.998|
|24|75.67|75.56|0.999|69.34|69.39|1.001|
|25|75.76|75.82|1.001|69.46|69.50|1.001|
|26|75.78|75.72|0.999|69.38|69.52|1.002|
|27|75.78|75.62|0.998|69.53|69.47|0.999|
|28|75.80|75.92|1.002|69.40|69.66|1.004|
|29|75.91|75.86|0.999|69.55|69.32|0.997|
|30|75.76|75.77|1.000|69.33|69.46|1.002|
|31|75.86|75.82|0.999|69.50|69.44|0.999|
|32|75.88|75.83|0.999|69.54|69.47|0.999|

The kernel's Cake variants are SwiGLU, GPT-OSS-style SwiGLU
(alpha/beta/limit), SiLU and SiTU on sm_100a and sm_103a, plus clamped
SwiGLU (limit 10) for DeepSeek-V4-Flash on sm_100a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated GPU execution schedules across several model geometries and
token counts, including expanded support for device-workfeed processing.
* Adjusted routing and finalization choices at selected token-count
boundaries.
* **Tests**
* Expanded GPU parity coverage for several geometries and boundary token
counts.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f911858](https://github.com/flashinfer-ai/flashinfer/commit/f911858bfc321ac0f6c1787341d61f5ff0f38ffc)

- **作者**: eigen
- **时间**: 2026-10-25T10:25:18Z
- **提交信息**: perf(cake_mega_moe): staging kernel, arrive-only barriers and route-in-dispatch for the BF16 rank-major EP8 layer (#7300)

This PR speeds up the BF16 rank-major expert-parallel (EP8) layer of the
`MoEEpLayer` mega backend for SM100
(`flashinfer/moe_ep/kernel_src/blackwell_bf16_rank_major/`). Cake
generates this layer. It uses BF16 activations, weights and output, with
hidden size 7168, intermediate size 2048, 256 experts (32 per rank),
top-8 routing, 8 ranks and 1 to 128 tokens per rank. The layer has one
variant (BF16, rank-major, sm_100a). Like the previous update, this PR
changes only the stages around the GEMMs; FC1 and FC2 are unchanged. The
three input staging copies now run as one kernel. The input and partial
barriers become one-warp arrive kernels that release a per-peer mailbox.
Dispatch and combine wait only for the peers they read, so combine pulls
each owner's rows as soon as that owner arrives. For up to 16 tokens per
rank, dispatch computes the routing itself and the separate route kernel
is skipped. The layer now launches nine kernels. The baseline is the
previous Cake version on current FlashInfer main, which already includes
the earlier non-GEMM update. Against it, the full layer forward is
1.03x–1.06x faster in eager mode and 1.03x–1.08x faster under CUDA graph
replay. Every row is faster in both modes. The table covers two routing
patterns. In "all-ranks", each token's 8 experts sit on 8 different
ranks, which is the pattern the FlashInfer test uses. In "random", each
token takes the top 8 of 256 experts from random scores.

| Routing | Tokens per rank | Eager: previous (us) | Eager: this PR (us)
| Eager speedup | CUDA graph: previous (us) | CUDA graph: this PR (us) |
CUDA graph speedup |
|---|---:|---:|---:|---:|---:|---:|---:|
| all-ranks | 1 | 173.1 | 162.8 | 1.06x | 165.9 | 153.8 | 1.08x |
| all-ranks | 2 | 266.0 | 254.4 | 1.05x | 260.1 | 247.8 | 1.05x |
| all-ranks | 4 | 427.0 | 414.7 | 1.03x | 420.3 | 406.1 | 1.03x |
| all-ranks | 8 | 455.8 | 443.4 | 1.03x | 450.6 | 436.2 | 1.03x |
| all-ranks | 16 | 462.9 | 447.6 | 1.03x | 456.7 | 442.3 | 1.03x |
| all-ranks | 32 | 472.1 | 457.8 | 1.03x | 466.9 | 450.7 | 1.04x |
| all-ranks | 64 | 490.5 | 474.0 | 1.03x | 485.3 | 468.9 | 1.03x |
| all-ranks | 128 | 533.6 | 513.0 | 1.04x | 527.4 | 507.9 | 1.04x |
| random | 1 | 201.8 | 193.5 | 1.04x | 196.7 | 188.4 | 1.04x |
| random | 2 | 289.2 | 277.5 | 1.04x | 282.8 | 270.4 | 1.05x |
| random | 4 | 359.5 | 348.6 | 1.03x | 354.3 | 340.0 | 1.04x |
| random | 8 | 420.9 | 408.5 | 1.03x | 414.6 | 400.8 | 1.03x |
| random | 16 | 461.3 | 445.5 | 1.04x | 454.7 | 438.4 | 1.04x |
| random | 32 | 470.0 | 455.6 | 1.03x | 464.8 | 448.6 | 1.04x |
| random | 64 | 483.4 | 468.0 | 1.03x | 477.2 | 460.9 | 1.04x |
| random | 128 | 511.0 | 494.6 | 1.03x | 505.9 | 487.5 | 1.04x |

Measured on 8x NVIDIA B200 (sm_100a, 148 SMs) in one node with the CUDA
13.4 toolkit (nvcc 13.4.92), PyTorch 2.14.1+cu130 and driver 580.82.07,
timing the full layer forward (input staging + run) with CUDA events and
a cold L2 before each iteration, in eager mode and as CUDA graph replay.
Each number is the slowest rank's median over 20 iterations, then the
median over 12 interleaved rounds that alternate the arm order; speedup
= previous / this PR.

Cake's other MegaMoE backends in FlashInfer are SM90 BF16 (sm_90a),
MXFP8 EP16 (sm_100a and sm_103a) and SM120 MXFP4 x MXFP8 (sm_120a); this
BF16 rank-major layer ships on sm_100a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance Improvements**
* Improved Blackwell BF16 rank-major MoE processing by streamlining
input staging and routing, including support for small active token
batches.
* Updated synchronization and data exchange between ranks to reduce
unnecessary waits and data transfers.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7b220a6](https://github.com/flashinfer-ai/flashinfer/commit/7b220a67a48606c82105cb4cafa22189489583ee)

- **作者**: eigen
- **时间**: 2026-10-25T10:24:52Z
- **提交信息**: perf(cake_router_gemm): per-shape schedules for the router GEMM on SM100/SM103 (#7287)

`cake_router_gemm` is FlashInfer's Cake router GEMM for MoE routing
logits. It computes out[M, N] = A[M, K] · B[N, K]^T with BF16 inputs,
FP32 accumulation and FP32 or BF16 output. It ships 32 programs, one for
each pair of num_tokens M in 1..16 and hidden_dim K in {6144, 7168}, and
takes N (number of experts) at run time. This PR gives each program its
own schedule, which reuses each loaded A chunk across several experts
and splits K across a thread-block cluster where that is faster.

The baseline is the previous Cake version on FlashInfer main, which uses
one CTA per expert. Each table covers three (K, N, output)
configurations for every num_tokens from 1 to 16, with PDL off and on.
That makes 96 rows per GPU, and this PR is faster than main on every
row. Latencies are median kernel times on one GPU, with both versions
timed interleaved on the same inputs.

**NVIDIA GB200, sm_100a (152 SMs), CUDA runtime 13.0**

| K | N | Output | num_tokens | PDL | FlashInfer main (µs) | This PR
(µs) | Speedup |
|---:|---:|---|---:|---|---:|---:|---:|
| 7168 | 256 | FP32 | 1 | off | 3.200 | 3.136 | 1.020x |
| 7168 | 256 | FP32 | 1 | on | 3.200 | 3.136 | 1.020x |
| 7168 | 256 | FP32 | 2 | off | 3.328 | 3.200 | 1.040x |
| 7168 | 256 | FP32 | 2 | on | 3.328 | 3.168 | 1.050x |
| 7168 | 256 | FP32 | 3 | off | 3.872 | 3.264 | 1.186x |
| 7168 | 256 | FP32 | 3 | on | 3.808 | 3.264 | 1.167x |
| 7168 | 256 | FP32 | 4 | off | 4.000 | 3.328 | 1.202x |
| 7168 | 256 | FP32 | 4 | on | 4.016 | 3.328 | 1.207x |
| 7168 | 256 | FP32 | 5 | off | 4.192 | 3.424 | 1.224x |
| 7168 | 256 | FP32 | 5 | on | 4.160 | 3.456 | 1.204x |
| 7168 | 256 | FP32 | 6 | off | 4.320 | 3.584 | 1.205x |
| 7168 | 256 | FP32 | 6 | on | 4.320 | 3.616 | 1.195x |
| 7168 | 256 | FP32 | 7 | off | 4.800 | 3.968 | 1.210x |
| 7168 | 256 | FP32 | 7 | on | 4.769 | 3.968 | 1.202x |
| 7168 | 256 | FP32 | 8 | off | 4.992 | 4.032 | 1.238x |
| 7168 | 256 | FP32 | 8 | on | 4.992 | 4.032 | 1.238x |
| 7168 | 256 | FP32 | 9 | off | 5.120 | 4.304 | 1.190x |
| 7168 | 256 | FP32 | 9 | on | 5.120 | 4.320 | 1.185x |
| 7168 | 256 | FP32 | 10 | off | 5.664 | 4.576 | 1.238x |
| 7168 | 256 | FP32 | 10 | on | 5.696 | 4.544 | 1.254x |
| 7168 | 256 | FP32 | 11 | off | 5.760 | 4.576 | 1.259x |
| 7168 | 256 | FP32 | 11 | on | 5.760 | 4.576 | 1.259x |
| 7168 | 256 | FP32 | 12 | off | 5.952 | 4.672 | 1.274x |
| 7168 | 256 | FP32 | 12 | on | 5.952 | 4.640 | 1.283x |
| 7168 | 256 | FP32 | 13 | off | 6.368 | 4.896 | 1.301x |
| 7168 | 256 | FP32 | 13 | on | 6.400 | 4.896 | 1.307x |
| 7168 | 256 | FP32 | 14 | off | 6.544 | 4.960 | 1.319x |
| 7168 | 256 | FP32 | 14 | on | 6.592 | 4.976 | 1.325x |
| 7168 | 256 | FP32 | 15 | off | 6.816 | 5.120 | 1.331x |
| 7168 | 256 | FP32 | 15 | on | 6.848 | 5.120 | 1.337x |
| 7168 | 256 | FP32 | 16 | off | 7.136 | 5.216 | 1.368x |
| 7168 | 256 | FP32 | 16 | on | 7.136 | 5.216 | 1.368x |
| 7168 | 128 | BF16 | 1 | off | 2.720 | 2.656 | 1.024x |
| 7168 | 128 | BF16 | 1 | on | 2.752 | 2.656 | 1.036x |
| 7168 | 128 | BF16 | 2 | off | 2.816 | 2.720 | 1.035x |
| 7168 | 128 | BF16 | 2 | on | 2.816 | 2.720 | 1.035x |
| 7168 | 128 | BF16 | 3 | off | 3.392 | 2.816 | 1.204x |
| 7168 | 128 | BF16 | 3 | on | 3.360 | 2.816 | 1.193x |
| 7168 | 128 | BF16 | 4 | off | 3.520 | 2.848 | 1.236x |
| 7168 | 128 | BF16 | 4 | on | 3.488 | 2.848 | 1.225x |
| 7168 | 128 | BF16 | 5 | off | 3.648 | 2.944 | 1.239x |
| 7168 | 128 | BF16 | 5 | on | 3.680 | 2.944 | 1.250x |
| 7168 | 128 | BF16 | 6 | off | 3.808 | 3.008 | 1.266x |
| 7168 | 128 | BF16 | 6 | on | 3.840 | 3.008 | 1.277x |
| 7168 | 128 | BF16 | 7 | off | 4.352 | 3.072 | 1.417x |
| 7168 | 128 | BF16 | 7 | on | 4.320 | 3.072 | 1.406x |
| 7168 | 128 | BF16 | 8 | off | 4.448 | 3.168 | 1.404x |
| 7168 | 128 | BF16 | 8 | on | 4.480 | 3.136 | 1.429x |
| 7168 | 128 | BF16 | 9 | off | 4.608 | 3.360 | 1.371x |
| 7168 | 128 | BF16 | 9 | on | 4.576 | 3.360 | 1.362x |
| 7168 | 128 | BF16 | 10 | off | 5.120 | 3.488 | 1.468x |
| 7168 | 128 | BF16 | 10 | on | 5.152 | 3.488 | 1.477x |
| 7168 | 128 | BF16 | 11 | off | 5.184 | 3.584 | 1.446x |
| 7168 | 128 | BF16 | 11 | on | 5.152 | 3.584 | 1.438x |
| 7168 | 128 | BF16 | 12 | off | 5.376 | 3.712 | 1.448x |
| 7168 | 128 | BF16 | 12 | on | 5.408 | 3.728 | 1.451x |
| 7168 | 128 | BF16 | 13 | off | 5.888 | 3.808 | 1.546x |
| 7168 | 128 | BF16 | 13 | on | 5.824 | 3.840 | 1.517x |
| 7168 | 128 | BF16 | 14 | off | 6.016 | 3.840 | 1.567x |
| 7168 | 128 | BF16 | 14 | on | 6.080 | 3.840 | 1.583x |
| 7168 | 128 | BF16 | 15 | off | 6.368 | 3.872 | 1.645x |
| 7168 | 128 | BF16 | 15 | on | 6.320 | 3.872 | 1.632x |
| 7168 | 128 | BF16 | 16 | off | 6.656 | 3.968 | 1.677x |
| 7168 | 128 | BF16 | 16 | on | 6.720 | 3.968 | 1.694x |
| 6144 | 256 | FP32 | 1 | off | 3.040 | 3.008 | 1.011x |
| 6144 | 256 | FP32 | 1 | on | 3.040 | 2.992 | 1.016x |
| 6144 | 256 | FP32 | 2 | off | 3.136 | 2.976 | 1.054x |
| 6144 | 256 | FP32 | 2 | on | 3.120 | 2.976 | 1.048x |
| 6144 | 256 | FP32 | 3 | off | 3.360 | 3.072 | 1.094x |
| 6144 | 256 | FP32 | 3 | on | 3.360 | 3.072 | 1.094x |
| 6144 | 256 | FP32 | 4 | off | 3.744 | 3.120 | 1.200x |
| 6144 | 256 | FP32 | 4 | on | 3.744 | 3.136 | 1.194x |
| 6144 | 256 | FP32 | 5 | off | 3.936 | 3.232 | 1.218x |
| 6144 | 256 | FP32 | 5 | on | 3.904 | 3.232 | 1.208x |
| 6144 | 256 | FP32 | 6 | off | 4.096 | 3.392 | 1.208x |
| 6144 | 256 | FP32 | 6 | on | 4.096 | 3.392 | 1.208x |
| 6144 | 256 | FP32 | 7 | off | 4.320 | 3.456 | 1.250x |
| 6144 | 256 | FP32 | 7 | on | 4.320 | 3.424 | 1.262x |
| 6144 | 256 | FP32 | 8 | off | 4.640 | 3.712 | 1.250x |
| 6144 | 256 | FP32 | 8 | on | 4.608 | 3.744 | 1.231x |
| 6144 | 256 | FP32 | 9 | off | 4.800 | 3.968 | 1.210x |
| 6144 | 256 | FP32 | 9 | on | 4.800 | 3.936 | 1.220x |
| 6144 | 256 | FP32 | 10 | off | 5.024 | 4.128 | 1.217x |
| 6144 | 256 | FP32 | 10 | on | 5.056 | 4.128 | 1.225x |
| 6144 | 256 | FP32 | 11 | off | 5.200 | 4.160 | 1.250x |
| 6144 | 256 | FP32 | 11 | on | 5.216 | 4.160 | 1.254x |
| 6144 | 256 | FP32 | 12 | off | 5.440 | 4.256 | 1.278x |
| 6144 | 256 | FP32 | 12 | on | 5.504 | 4.224 | 1.303x |
| 6144 | 256 | FP32 | 13 | off | 5.632 | 4.320 | 1.304x |
| 6144 | 256 | FP32 | 13 | on | 5.600 | 4.320 | 1.296x |
| 6144 | 256 | FP32 | 14 | off | 5.920 | 4.384 | 1.350x |
| 6144 | 256 | FP32 | 14 | on | 5.888 | 4.416 | 1.333x |
| 6144 | 256 | FP32 | 15 | off | 6.240 | 4.480 | 1.393x |
| 6144 | 256 | FP32 | 15 | on | 6.256 | 4.480 | 1.396x |
| 6144 | 256 | FP32 | 16 | off | 6.528 | 4.416 | 1.478x |
| 6144 | 256 | FP32 | 16 | on | 6.528 | 4.448 | 1.468x |

**NVIDIA GB300, sm_103a (152 SMs), CUDA runtime 13.0**

| K | N | Output | num_tokens | PDL | FlashInfer main (µs) | This PR
(µs) | Speedup |
|---:|---:|---|---:|---|---:|---:|---:|
| 7168 | 256 | FP32 | 1 | off | 3.200 | 3.104 | 1.031x |
| 7168 | 256 | FP32 | 1 | on | 3.264 | 3.168 | 1.030x |
| 7168 | 256 | FP32 | 2 | off | 3.360 | 3.200 | 1.050x |
| 7168 | 256 | FP32 | 2 | on | 3.360 | 3.200 | 1.050x |
| 7168 | 256 | FP32 | 3 | off | 3.840 | 3.296 | 1.165x |
| 7168 | 256 | FP32 | 3 | on | 3.808 | 3.296 | 1.155x |
| 7168 | 256 | FP32 | 4 | off | 3.952 | 3.328 | 1.187x |
| 7168 | 256 | FP32 | 4 | on | 3.984 | 3.328 | 1.197x |
| 7168 | 256 | FP32 | 5 | off | 4.128 | 3.408 | 1.211x |
| 7168 | 256 | FP32 | 5 | on | 4.128 | 3.424 | 1.206x |
| 7168 | 256 | FP32 | 6 | off | 4.256 | 3.520 | 1.209x |
| 7168 | 256 | FP32 | 6 | on | 4.224 | 3.488 | 1.211x |
| 7168 | 256 | FP32 | 7 | off | 4.704 | 3.872 | 1.215x |
| 7168 | 256 | FP32 | 7 | on | 4.736 | 3.872 | 1.223x |
| 7168 | 256 | FP32 | 8 | off | 4.864 | 3.936 | 1.236x |
| 7168 | 256 | FP32 | 8 | on | 4.896 | 3.936 | 1.244x |
| 7168 | 256 | FP32 | 9 | off | 5.024 | 4.192 | 1.198x |
| 7168 | 256 | FP32 | 9 | on | 5.024 | 4.192 | 1.198x |
| 7168 | 256 | FP32 | 10 | off | 5.568 | 4.416 | 1.261x |
| 7168 | 256 | FP32 | 10 | on | 5.568 | 4.416 | 1.261x |
| 7168 | 256 | FP32 | 11 | off | 5.664 | 4.448 | 1.273x |
| 7168 | 256 | FP32 | 11 | on | 5.664 | 4.416 | 1.283x |
| 7168 | 256 | FP32 | 12 | off | 5.792 | 4.512 | 1.284x |
| 7168 | 256 | FP32 | 12 | on | 5.792 | 4.544 | 1.275x |
| 7168 | 256 | FP32 | 13 | off | 6.272 | 4.704 | 1.333x |
| 7168 | 256 | FP32 | 13 | on | 6.272 | 4.704 | 1.333x |
| 7168 | 256 | FP32 | 14 | off | 6.400 | 4.768 | 1.342x |
| 7168 | 256 | FP32 | 14 | on | 6.416 | 4.768 | 1.346x |
| 7168 | 256 | FP32 | 15 | off | 6.752 | 4.864 | 1.388x |
| 7168 | 256 | FP32 | 15 | on | 6.736 | 4.864 | 1.385x |
| 7168 | 256 | FP32 | 16 | off | 7.040 | 4.992 | 1.410x |
| 7168 | 256 | FP32 | 16 | on | 7.008 | 4.992 | 1.404x |
| 7168 | 128 | BF16 | 1 | off | 2.720 | 2.656 | 1.024x |
| 7168 | 128 | BF16 | 1 | on | 2.720 | 2.624 | 1.037x |
| 7168 | 128 | BF16 | 2 | off | 2.784 | 2.688 | 1.036x |
| 7168 | 128 | BF16 | 2 | on | 2.816 | 2.720 | 1.035x |
| 7168 | 128 | BF16 | 3 | off | 3.328 | 2.784 | 1.195x |
| 7168 | 128 | BF16 | 3 | on | 3.328 | 2.784 | 1.195x |
| 7168 | 128 | BF16 | 4 | off | 3.488 | 2.816 | 1.239x |
| 7168 | 128 | BF16 | 4 | on | 3.456 | 2.816 | 1.227x |
| 7168 | 128 | BF16 | 5 | off | 3.616 | 2.880 | 1.256x |
| 7168 | 128 | BF16 | 5 | on | 3.648 | 2.880 | 1.267x |
| 7168 | 128 | BF16 | 6 | off | 3.808 | 2.944 | 1.294x |
| 7168 | 128 | BF16 | 6 | on | 3.776 | 2.976 | 1.269x |
| 7168 | 128 | BF16 | 7 | off | 4.320 | 3.040 | 1.421x |
| 7168 | 128 | BF16 | 7 | on | 4.320 | 3.008 | 1.436x |
| 7168 | 128 | BF16 | 8 | off | 4.448 | 3.088 | 1.440x |
| 7168 | 128 | BF16 | 8 | on | 4.448 | 3.136 | 1.418x |
| 7168 | 128 | BF16 | 9 | off | 4.576 | 3.328 | 1.375x |
| 7168 | 128 | BF16 | 9 | on | 4.576 | 3.296 | 1.388x |
| 7168 | 128 | BF16 | 10 | off | 5.088 | 3.392 | 1.500x |
| 7168 | 128 | BF16 | 10 | on | 5.056 | 3.392 | 1.491x |
| 7168 | 128 | BF16 | 11 | off | 5.120 | 3.504 | 1.461x |
| 7168 | 128 | BF16 | 11 | on | 5.120 | 3.488 | 1.468x |
| 7168 | 128 | BF16 | 12 | off | 5.344 | 3.584 | 1.491x |
| 7168 | 128 | BF16 | 12 | on | 5.408 | 3.616 | 1.496x |
| 7168 | 128 | BF16 | 13 | off | 5.776 | 3.680 | 1.570x |
| 7168 | 128 | BF16 | 13 | on | 5.760 | 3.680 | 1.565x |
| 7168 | 128 | BF16 | 14 | off | 6.016 | 3.712 | 1.621x |
| 7168 | 128 | BF16 | 14 | on | 6.048 | 3.712 | 1.629x |
| 7168 | 128 | BF16 | 15 | off | 6.336 | 3.776 | 1.678x |
| 7168 | 128 | BF16 | 15 | on | 6.336 | 3.776 | 1.678x |
| 7168 | 128 | BF16 | 16 | off | 6.592 | 3.840 | 1.717x |
| 7168 | 128 | BF16 | 16 | on | 6.656 | 3.840 | 1.733x |
| 6144 | 256 | FP32 | 1 | off | 3.040 | 2.976 | 1.022x |
| 6144 | 256 | FP32 | 1 | on | 3.040 | 2.976 | 1.022x |
| 6144 | 256 | FP32 | 2 | off | 3.136 | 3.008 | 1.043x |
| 6144 | 256 | FP32 | 2 | on | 3.136 | 3.008 | 1.043x |
| 6144 | 256 | FP32 | 3 | off | 3.328 | 3.072 | 1.083x |
| 6144 | 256 | FP32 | 3 | on | 3.328 | 3.072 | 1.083x |
| 6144 | 256 | FP32 | 4 | off | 3.744 | 3.120 | 1.200x |
| 6144 | 256 | FP32 | 4 | on | 3.744 | 3.136 | 1.194x |
| 6144 | 256 | FP32 | 5 | off | 3.904 | 3.232 | 1.208x |
| 6144 | 256 | FP32 | 5 | on | 3.904 | 3.200 | 1.220x |
| 6144 | 256 | FP32 | 6 | off | 4.064 | 3.328 | 1.221x |
| 6144 | 256 | FP32 | 6 | on | 4.096 | 3.328 | 1.231x |
| 6144 | 256 | FP32 | 7 | off | 4.288 | 3.376 | 1.270x |
| 6144 | 256 | FP32 | 7 | on | 4.256 | 3.392 | 1.255x |
| 6144 | 256 | FP32 | 8 | off | 4.608 | 3.648 | 1.263x |
| 6144 | 256 | FP32 | 8 | on | 4.608 | 3.648 | 1.263x |
| 6144 | 256 | FP32 | 9 | off | 4.768 | 3.872 | 1.231x |
| 6144 | 256 | FP32 | 9 | on | 4.704 | 3.840 | 1.225x |
| 6144 | 256 | FP32 | 10 | off | 4.928 | 4.000 | 1.232x |
| 6144 | 256 | FP32 | 10 | on | 4.960 | 4.032 | 1.230x |
| 6144 | 256 | FP32 | 11 | off | 5.152 | 4.064 | 1.268x |
| 6144 | 256 | FP32 | 11 | on | 5.088 | 4.032 | 1.262x |
| 6144 | 256 | FP32 | 12 | off | 5.408 | 4.128 | 1.310x |
| 6144 | 256 | FP32 | 12 | on | 5.440 | 4.176 | 1.303x |
| 6144 | 256 | FP32 | 13 | off | 5.472 | 4.224 | 1.296x |
| 6144 | 256 | FP32 | 13 | on | 5.504 | 4.192 | 1.313x |
| 6144 | 256 | FP32 | 14 | off | 5.760 | 4.288 | 1.343x |
| 6144 | 256 | FP32 | 14 | on | 5.792 | 4.288 | 1.351x |
| 6144 | 256 | FP32 | 15 | off | 6.144 | 4.352 | 1.412x |
| 6144 | 256 | FP32 | 15 | on | 6.160 | 4.352 | 1.415x |
| 6144 | 256 | FP32 | 16 | off | 6.400 | 4.320 | 1.482x |
| 6144 | 256 | FP32 | 16 | on | 6.400 | 4.320 | 1.482x |

Cake has no other data-type, layout or fused variant of this router GEMM
(the same programs serve both output types), and it covers sm_100a and
sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded optimized router matrix-multiplication coverage for workloads
with 7–16 tokens at hidden size 7168.
* The system now selects between specialized execution paths based on
workload size and available GPU capacity.
  * Existing FP32 and BF16 output options remain supported.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [bfe3de5](https://github.com/flashinfer-ai/flashinfer/commit/bfe3de571c093e4f516a813c9bead22c2486d898)

- **作者**: eigen
- **时间**: 2026-10-25T10:21:17Z
- **提交信息**: perf(cake_gated_act_mxfp8): faster fused SwiGLU + MXFP8 quantization forward and backward (SM100 / SM103 / SM107) (#7305)

FlashInfer's fused SwiGLU + MXFP8 quantization kernel computes
silu(gate) * up from a BF16 input [M, 2K]. It quantizes the result to
MXFP8: E4M3 values with one E8M0 scale (RCEIL rounding) per 32 values,
and scales in the swizzled 128 x 4 layout. The kernel has one data type
(BF16 in, MXFP8 E4M3 + E8M0 out) and six forms. These are forward
(`flashinfer.silu_and_mul_mxfp8_quantize`, output [M, K]) and backward
(`flashinfer.silu_and_mul_mxfp8_quantize_backward`, gate and up
gradients [M, 2K] from grad_output [M, K]), each with rowwise, colwise
or both outputs. This PR delivers all six forms on sm_100a, sm_103a and
sm_107a through the Cake package
`flashinfer.cake_gated_act_mxfp8_backend`, which runs one program per
call, chosen by M * K. The public API is unchanged, and every output
byte is identical to the previous kernels' output. The baseline is the
previous Cake version, the gated_act_mxfp8 kernels FlashInfer ships on
main (added in #4638, SM107 enabled in #5392). Against that baseline,
the PR is 1.075-1.501x faster on B200 (forward 1.196-1.501x, backward
1.075-1.474x), 1.044-1.411x faster on GB300 (forward 1.169-1.411x,
backward 1.044-1.383x) and 1.094-1.697x faster on R200 (forward
1.331-1.697x, backward 1.094-1.427x). Every row of every table is
faster.

Latency is the mean CUPTI kernel time in microseconds, with a cold L2
before every launch. Both versions run in the same process on the same
GPU, in alternating paired runs, and speedup = FlashInfer latency / Cake
latency.

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4.92

| M x K | Pass | FlashInfer (µs) | Cake (µs) | Speedup |
|---|---|---:|---:|---:|
| 128 x 128 | fwd rowwise | 2.90 | 2.21 | 1.312x |
| 128 x 128 | fwd colwise | 3.53 | 2.35 | 1.501x |
| 128 x 128 | fwd both | 3.16 | 2.46 | 1.283x |
| 128 x 128 | bwd rowwise | 3.18 | 2.25 | 1.412x |
| 128 x 128 | bwd colwise | 3.71 | 2.52 | 1.474x |
| 128 x 128 | bwd both | 3.37 | 2.62 | 1.283x |
| 4096 x 2048 | fwd rowwise | 11.50 | 9.58 | 1.201x |
| 4096 x 2048 | fwd colwise | 13.22 | 10.35 | 1.278x |
| 4096 x 2048 | fwd both | 14.00 | 11.58 | 1.209x |
| 4096 x 2048 | bwd rowwise | 15.37 | 14.02 | 1.096x |
| 4096 x 2048 | bwd colwise | 17.75 | 14.87 | 1.194x |
| 4096 x 2048 | bwd both | 19.24 | 17.89 | 1.075x |
| 4096 x 7168 | fwd rowwise | 30.15 | 25.17 | 1.198x |
| 4096 x 7168 | fwd colwise | 34.21 | 26.39 | 1.296x |
| 4096 x 7168 | fwd both | 38.92 | 31.12 | 1.250x |
| 4096 x 7168 | bwd rowwise | 42.45 | 39.33 | 1.079x |
| 4096 x 7168 | bwd colwise | 48.94 | 41.14 | 1.190x |
| 4096 x 7168 | bwd both | 56.97 | 50.58 | 1.126x |
| 16384 x 7168 | fwd rowwise | 107.91 | 90.22 | 1.196x |
| 16384 x 7168 | fwd colwise | 119.10 | 91.90 | 1.296x |
| 16384 x 7168 | fwd both | 141.33 | 108.95 | 1.297x |
| 16384 x 7168 | bwd rowwise | 153.82 | 141.40 | 1.088x |
| 16384 x 7168 | bwd colwise | 174.27 | 145.00 | 1.202x |
| 16384 x 7168 | bwd both | 214.97 | 186.93 | 1.150x |
| 131072 x 8192 | fwd rowwise | 1007.29 | 772.63 | 1.304x |
| 131072 x 8192 | fwd colwise | 1117.21 | 829.95 | 1.346x |
| 131072 x 8192 | fwd both | 1383.01 | 1041.45 | 1.328x |
| 131072 x 8192 | bwd rowwise | 1556.70 | 1259.40 | 1.236x |
| 131072 x 8192 | bwd colwise | 1727.04 | 1374.90 | 1.256x |
| 131072 x 8192 | bwd both | 2176.56 | 1742.34 | 1.249x |

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4.92

| M x K | Pass | FlashInfer (µs) | Cake (µs) | Speedup |
|---|---|---:|---:|---:|
| 128 x 128 | fwd rowwise | 3.12 | 2.45 | 1.271x |
| 128 x 128 | fwd colwise | 3.66 | 2.59 | 1.411x |
| 128 x 128 | fwd both | 3.38 | 2.67 | 1.267x |
| 128 x 128 | bwd rowwise | 3.33 | 2.48 | 1.343x |
| 128 x 128 | bwd colwise | 3.81 | 2.75 | 1.383x |
| 128 x 128 | bwd both | 3.58 | 2.81 | 1.274x |
| 4096 x 2048 | fwd rowwise | 11.03 | 9.17 | 1.203x |
| 4096 x 2048 | fwd colwise | 12.74 | 9.94 | 1.281x |
| 4096 x 2048 | fwd both | 13.20 | 10.99 | 1.202x |
| 4096 x 2048 | bwd rowwise | 14.53 | 13.39 | 1.085x |
| 4096 x 2048 | bwd colwise | 16.81 | 14.24 | 1.181x |
| 4096 x 2048 | bwd both | 17.87 | 17.12 | 1.044x |
| 4096 x 7168 | fwd rowwise | 28.59 | 24.45 | 1.169x |
| 4096 x 7168 | fwd colwise | 33.01 | 25.22 | 1.309x |
| 4096 x 7168 | fwd both | 35.86 | 30.07 | 1.193x |
| 4096 x 7168 | bwd rowwise | 39.81 | 37.80 | 1.053x |
| 4096 x 7168 | bwd colwise | 45.91 | 39.87 | 1.151x |
| 4096 x 7168 | bwd both | 52.57 | 47.64 | 1.104x |
| 16384 x 7168 | fwd rowwise | 102.48 | 87.20 | 1.175x |
| 16384 x 7168 | fwd colwise | 112.74 | 89.99 | 1.253x |
| 16384 x 7168 | fwd both | 132.00 | 107.36 | 1.229x |
| 16384 x 7168 | bwd rowwise | 145.33 | 135.92 | 1.069x |
| 16384 x 7168 | bwd colwise | 161.97 | 140.02 | 1.157x |
| 16384 x 7168 | bwd both | 199.32 | 175.60 | 1.135x |
| 131072 x 8192 | fwd rowwise | 892.55 | 741.25 | 1.204x |
| 131072 x 8192 | fwd colwise | 978.03 | 756.15 | 1.293x |
| 131072 x 8192 | fwd both | 1151.23 | 923.12 | 1.247x |
| 131072 x 8192 | bwd rowwise | 1295.83 | 1173.58 | 1.104x |
| 131072 x 8192 | bwd colwise | 1426.45 | 1223.10 | 1.166x |
| 131072 x 8192 | bwd both | 1791.29 | 1550.96 | 1.155x |

### NVIDIA R200 (sm_107a, 216 SMs), CUDA 13.4.92

| M x K | Pass | FlashInfer (µs) | Cake (µs) | Speedup |
|---|---|---:|---:|---:|
| 128 x 128 | fwd rowwise | 2.87 | 2.12 | 1.351x |
| 128 x 128 | fwd colwise | 3.36 | 2.29 | 1.470x |
| 128 x 128 | fwd both | 3.13 | 2.35 | 1.331x |
| 128 x 128 | bwd rowwise | 3.10 | 2.26 | 1.369x |
| 128 x 128 | bwd colwise | 3.49 | 2.44 | 1.427x |
| 128 x 128 | bwd both | 3.30 | 2.58 | 1.278x |
| 4096 x 2048 | fwd rowwise | 9.98 | 7.04 | 1.417x |
| 4096 x 2048 | fwd colwise | 11.13 | 7.10 | 1.567x |
| 4096 x 2048 | fwd both | 11.31 | 8.43 | 1.343x |
| 4096 x 2048 | bwd rowwise | 11.36 | 10.07 | 1.128x |
| 4096 x 2048 | bwd colwise | 12.89 | 10.62 | 1.213x |
| 4096 x 2048 | bwd both | 13.77 | 12.59 | 1.094x |
| 4096 x 7168 | fwd rowwise | 25.82 | 17.58 | 1.469x |
| 4096 x 7168 | fwd colwise | 29.20 | 17.95 | 1.627x |
| 4096 x 7168 | fwd both | 29.39 | 21.82 | 1.347x |
| 4096 x 7168 | bwd rowwise | 30.34 | 26.99 | 1.124x |
| 4096 x 7168 | bwd colwise | 34.27 | 27.66 | 1.239x |
| 4096 x 7168 | bwd both | 38.45 | 33.98 | 1.132x |
| 16384 x 7168 | fwd rowwise | 92.36 | 60.46 | 1.528x |
| 16384 x 7168 | fwd colwise | 99.37 | 60.56 | 1.641x |
| 16384 x 7168 | fwd both | 103.98 | 73.93 | 1.407x |
| 16384 x 7168 | bwd rowwise | 109.31 | 92.89 | 1.177x |
| 16384 x 7168 | bwd colwise | 120.11 | 95.36 | 1.260x |
| 16384 x 7168 | bwd both | 143.59 | 123.53 | 1.162x |
| 131072 x 8192 | fwd rowwise | 825.25 | 508.96 | 1.621x |
| 131072 x 8192 | fwd colwise | 864.60 | 509.53 | 1.697x |
| 131072 x 8192 | fwd both | 919.51 | 638.00 | 1.441x |
| 131072 x 8192 | bwd rowwise | 973.58 | 796.37 | 1.223x |
| 131072 x 8192 | bwd colwise | 1052.92 | 830.90 | 1.267x |
| 131072 x 8192 | bwd both | 1286.11 | 1094.90 | 1.175x |

Cake has no other variants of this kernel; it ships on sm_100a (B200),
sm_103a (GB300) and sm_107a (R200) only, with no family fallback to
other architectures.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a Cake backend for fused SwiGLU MXFP8 forward and backward
operations, with row-wise and column-wise output options on supported
GPUs.
* Added automatic selection between available kernel implementations
based on GPU architecture and input shape.
* **Bug Fixes**
* Improved handling of extreme values during activation computation and
quantization.
* **Refactor**
  * Routed existing gated MXFP8 operations through the new backend.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a62a860](https://github.com/flashinfer-ai/flashinfer/commit/a62a8601f6f0742c62cc77bcb1f1cebec0b059df)

- **作者**: eigen
- **时间**: 2026-10-25T10:16:33Z
- **提交信息**: deslop(cake_rmsnorm_train): fold duplicate and per-arch kernel pairs, drop unread registry keys, collapse dead guards (#7307)

## 📌 Description

### Summary

This PR is a deslop of `flashinfer/cake_rmsnorm_train_backend/`. The
Cake exporter generates this package. It targets SM100 (B200), SM103
(GB300) and SM107 (R200).

The package has these parts:
- kernel and binding translation units under `csrc/`, named
`cake_rmsnorm_train_<20-hex>_kernel.cu` and
`cake_rmsnorm_train_<20-hex>_binding.cu`;
- `build.json`, the manifest: per-library sources, SHA-256 digests,
arches and the closure identifier. At the base it has 132 libraries: 46
/ 44 / 42 on SM100 / SM103 / SM107;
- `cake_jit.py`, the registry: 126 `MODULES` records, `ROUTES` per
architecture, `HIDDEN_SIZES` and the loader.

The facade `flashinfer/cake_rmsnorm_train.py` is hand-written glue. Its
public entry points are `cake_rmsnorm_train_forward`,
`cake_rmsnorm_train_backward` and `cake_rmsnorm`.

Four test files cover the package:
- `tests/norm/test_cake_rmsnorm_train.py`;
- `tests/norm/test_cake_rmsnorm_train_api.py`;
- `tests/norm/test_cake_rmsnorm_train_pairs.py`;
- `tests/norm/test_cake_rmsnorm_train_stall.py`.

Together they collect 411 test ids at the base and at the head. No id is
added or removed.

The seven commits are mechanical:
- commit 1 folds a duplicate H=512 dw-reduce pair into a stage record of
the kept library;
- commit 2 drops an sm_107a build of `780b9833` that no route selects;
- commit 3 drops six registry record keys that nothing reads;
- commit 4 derives `arg_plan` and `logical` from three record classes;
- commit 5 replaces the facade's docstring copies with delegations to
the backend;
- commit 6 merges five per-arch kernel pairs into one translation unit
each;
- commit 7 collapses a dead sm_100a guard in 28 kernels.

Each commit has an identity proof. For the compiled units, the proof
compares preprocessed text, SASS, symbol tables and host exports. For
the Python files, it uses AST checks, reference searches and the
host-plan stream. Each commit section lists its declared behaviour
notes, and Reviewer Notes repeats them.

Commits 1, 2, 3, 4, 6 and 7 change exporter-written files. Commits 1 and
6 are hand folds. Commits 2, 3, 4 and 7 are hand edits. These folds and
edits are pending exporter regeneration. Commit 5 edits the hand-written
facade, so a regeneration keeps it.

Totals versus `main` `03f82fdda`: 48 files changed, +375 / −9,421.
Twelve translation units are deleted (six kernel units and six binding
units), and 36 files are edited. `build.json` goes from 132 to 130
libraries. Per architecture, that is 46 / 44 / 42 → 45 / 44 / 41 on
SM100 / SM103 / SM107. The registry keeps its 126 records. Six are
renamed in place: one in commit 1 and five in commit 6.

### Changes

Base: `main` `03f82fdda`. Head:
`7b66139f48cc04e589178337158d1f7507a3ab2f` (7 commits). Reviewer Notes
give the `main` sha at publish time.

Files per commit:
- commit 1: the two `4ad7e802` units, `build.json` and `cake_jit.py`;
- commit 2: `build.json` and `cake_jit.py`;
- commits 3 and 4: `cake_jit.py`;
- commit 5: `flashinfer/cake_rmsnorm_train.py`;
- commit 6: the ten units of the dropped members, the five merged kernel
units, `build.json` and `cake_jit.py`;
- commit 7: the 28 kernel units and `build.json`.

Several commits edit the same files:
- `build.json` (commits 1, 2, 6 and 7);
- `cake_jit.py` (commits 1, 2, 3, 4 and 6).

So the per-commit counts do not sum to the branch totals.

### Commit 1 (90e8588df) - fold the duplicate dw-reduce pair into a
stage record (4 files, +5 / −390)

- **The duplicate.** The exporter emitted two H=512 dw-reduce programs.
They are byte-identical except for their 20-hex name:
  - `4ad7e802`: rows in (4096, 32768], sm_100a;
  - `7097069b`: rows in (0, 1024], sm_100a and sm_103a.
- **Fold.**
- The `4ad7e802` kernel and binding translation units are deleted, along
with its `build.json` entry (132 → 131 libraries).
- Its registry record becomes, in place, a second stage record of the
kept library: `cake_rmsnorm_train_7097069b8eea6ba44d5a__4096_32768`.
- The record keeps the old `arches` and `select_rule`. Its `kernel`,
`kernel_symbol` and `library` point at the kept stem.
- The sm_100a `bwd_h512` route names the stage record in the same slot.
  - No other record, route or entry changes.
- **Proof.**
- The two kernel sources (273 lines) and the two bindings (89 lines) are
identical after masking the name. So preprocessed-text identity per
device pass and identical SASS for the pair on SM100 prove the fold.
- The manifest keeps references equal to the entry names (131 == 131).
Every listed source is present, and every digest equals its file.
- The registry equals the base modulo the declared rename. The static
selection is identical over every (architecture, route, rows) cell, up
to the library name.
- The per-id GPU test identity on SM100 exercises the stage record at
rows 4097 and 32768.
  - No file outside the package names the dropped hash.
- **Behaviour note.** On sm_100a, the dw-reduce launch for H=512 rows in
(4096, 32768] now names `kernel_cake_rmsnorm_train_7097069b8eea6ba44d5a`
in its error texts. No test pins those texts.
- **Declared.** This is a hand fold of exporter-written files.

### Commit 2 (5d609bb0c) - drop the unrouted sm_107a build of 780b9833
(2 files, +0 / −25)

- **The build.** The exporter kept an SM107 build of the H=2048 forward
pair `780b9833`. This is the entry
`cake_rmsnorm_train_780b9833fd0a236ef0e4_sm_107a`, with `min_cuda` 13.4.
No sm_107a route has selected it since the last re-export. The sm_107a
route table (12 routes, 49 names) names neither the main record nor its
`__cut` stage record.
- **Change.**
- The `build.json` entry is deleted. This takes the manifest from 131 to
130 libraries, and from 42 to 41 on sm_107a.
- Both registry records lose the `"sm_107a"` element of `arches`:
`['sm_100a', 'sm_103a', 'sm_107a']` → `['sm_100a', 'sm_103a']`.
- **Kept.** Both records stay routed on sm_100a, and the main record
stays routed on sm_103a. So the kernel and binding translation units
stay, and no digest changes. The CUDA floor stays 12.8. No other record,
route or entry changes.
- **Proof.**
- The sm_107a route literal names no `780b9833` record. The entry name
occurs nowhere else in the tree.
- The manifest keeps references equal to the entry names (130 == 130).
Every listed source is present, and every digest equals its file. The
manifest round-trips through its own JSON form.
- The registry equals its input after pruning exactly the two declared
`"sm_107a"` constants (AST identity). The route table and hidden sizes
are unchanged.
- The host-plan stream over every (architecture, route, rows) cell is
identical, because no sm_107a route reaches either record.
- The per-id GPU test identity on SM100 and SM103 is unaffected. The
dropped build was never selected on SM107.
- **Behaviour.** None: no device selects a different library.
- **Declared.** This is a hand edit of exporter-written files.

### Commit 3 (52eb3deeb) - drop the six unread registry record keys (1
file, +5 / −761)

- **The keys.** All 126 registry records in `cake_jit.py` carried six
keys that nothing reads:
- `launch.block`, `launch.cluster`, `launch.dynamic_smem_bytes` and
`launch.persistent_ctas_per_sm`;
  - `kernel_symbol` and `ffi_entry`.

The bindings hard-code the block size and the dynamic shared memory. The
cluster is (1, 1, 1) in every record. Nothing reads the persistent CTA
count.
- **Change.** The six `"key": value` lines are deleted from every record
(756 lines). Five loader lines are rewritten:
- the two sites that read `kernel_symbol` hold four error-message
f-strings, in the chunking and workspace-layout paths. Those f-strings
now spell the symbol as `kernel_{record['kernel']}`;
- the one site that read `ffi_entry` now calls the fixed entry
`module.run`.

`kernel_symbol == "kernel_" + kernel` and `ffi_entry == "run"` hold for
126 of 126 records. So the messages and the call are text-identical.
- **Kept.** Tests pin `launch.cooperative`, `launch.use_pdl`,
`grid_rule`, `kernel` and `role`, so these keys stay. Routes, hidden
sizes, `build.json` and the kernel sources do not change.
- **Proof.**
- A whole-repository search for readers of the six keys covers the
package, the facade, the test suite and the benchmark. It finds no
reader other than the five rewritten loader lines. Other packages have
registries of the same shape, but they do not read this one.
- The input AST, with exactly the 756 key / value pairs pruned, equals
the output AST modulo the five declared one-line edits.
- Every record equals its input minus the six keys, in JSON form. The
route table and hidden sizes are unchanged.
- The host-plan stream over every (architecture, route, rows) cell is
identical, because no selection, grid or workspace rule reads a dropped
key.
- The per-id GPU test identity on SM100 and SM103 is unaffected. The
R200 (SM107) row in Validation covers SM107.
- **Behaviour.** None in the tree. An out-of-tree reader of the removed
keys would break.
- **Declared.** This is a hand edit of an exporter-written file.

### Commit 4 (dc7be1691) - derive arg_plan and logical from three record
classes (1 file, +141 / −2,894)

- **The literals.** All 126 records spelled out their kernel-parameter
plan in two literals:
- `arg_plan`: the ordered (kind, name) list of the kernel's parameters;
- `logical`: the map from kernel parameter names to the logical argument
names of the public API.

Across the registry, the two literals take only three values, one per
kernel shape:
  - the forward kernel: 49 records; 11 parameters, 8 names;
  - the main backward kernel: 40 records; 15 parameters, 12 names;
  - the dw-reduce kernel: 37 records; 6 parameters, 3 names.

A record's shape follows from keys it already carries. Role
`"bwd_reduce"` is the dw-reduce kernel. A `workspace_rule` marks the
main backward kernel. Every other record is a forward kernel.
- **Change.**
- The three (`arg_plan`, `logical`) values move into one `_CLASSES`
table above `MODULES`.
  - The two literals are deleted from every record (2,848 lines).
- After `ROUTES`, `_plan_class` and one update loop give each record its
class at import.
- `MODULES` stays one top-level literal of per-record dicts that carry
`library` and `arches`. So the manifest checker's literal walk finds
every library reference as before.
- Routes, hidden sizes, the loader functions, `build.json` and the
kernel sources do not change.
- **Proof.**
- The class rule is a pure function of `role` and `workspace_rule` for
126 of 126 records. Exactly three distinct (`arg_plan`, `logical`)
values exist.
- Every record, updated with its class, equals its input literal in JSON
form with sorted keys. The order of the remaining keys is unchanged. So
are the route table and the hidden sizes.
- The input AST, with exactly the 252 `arg_plan` / `logical` pairs
pruned, equals the output AST apart from three declared statements.
These are the `_CLASSES` literal, `_plan_class` and the update loop.
- The host-plan stream over every (architecture, route, rows) cell is
identical, because every (kind, key, logical name) lookup reads the same
values.
- The per-id GPU test identity on SM100 and SM103 is unaffected. The
R200 (SM107) row in Validation covers SM107.
- **Behaviour note.** The records of one class now share the table's
`arg_plan` list and `logical` dict. No reader mutates them in the
package, the facade, the test suites or the benchmark. The loader and
the pairs test (`tests/norm/test_cake_rmsnorm_train_pairs.py`) only
index and iterate them.
- **Declared.** This is a hand edit of an exporter-written file.

### Commit 5 (05bccc071) - delegate the facade docstrings to the backend
(1 file, +9 / −91)

- **The copies.** The facade `flashinfer/cake_rmsnorm_train.py` has
three public entry points: `cake_rmsnorm_train_forward`,
`cake_rmsnorm_train_backward` and `cake_rmsnorm`. They are thin defs
whose bodies call the backend package. Each one carried a full copy of
the backend function's docstring (91 lines in total).
- **Change.**
- Each copy becomes the one-line delegation ``See
:func:`flashinfer.cake_rmsnorm_train_backend.<fn>`.``, which the
docstring checker accepts for a thin wrapper.
- After the three decorated defs, `<fn>.__doc__ = _backend.<fn>.__doc__`
copies the backend docstrings onto the public objects at import. So the
rendered API pages keep their Parameters / Returns sections.
- The backend package, the signatures, the bodies and `__all__` do not
change.
- **Proof.**
- The output AST equals the input AST with exactly the three docstring
constants replaced and the three declared module-level assignments
inserted. The check runs in both directions.
- Each new docstring is in the checker's delegation form. So the
docstring and API-docs checkers report no new finding.
- The decorator returns either the original function or a
`functools.wraps` wrapper, and it adds no banner. So the `__doc__`
reassignment is clean.
- No test reads a docstring. The per-id GPU test identity on SM100 and
SM103 is unaffected. The R200 (SM107) row in Validation covers SM107.
- **Behaviour note.** The forward and `cake_rmsnorm` pages render the
same text as before. The backward page gains one clause from the backend
text: the workspace is "sized for at least this many rows". The facade
is hand-written glue, so this edit survives a regeneration of the
exported package.

### Commit 6 (043a58d1c) - merge five per-arch kernel pairs into one TU
each (17 files, +194 / −5,099)

- **The pairs.** Five backward programs were exported once per
architecture, each as separate kernel and binding translation units.
Their bindings are byte-identical except for the 20-hex name. Their
kernels differ only in architecture-selected lines:
- `0dcdc563` / `fe599c89` (sm_100a + sm_103a) vs `44cae844` / `75f75802`
(sm_107a): the `griddepcontrol.launch_dependents` line sits at a
different point;
- `35a0b0ca` (sm_100a) vs `a6c25d5d` (sm_103a): the chunk counter is
masked with `& 7` vs `& 15` at two sites;
- `7dc29629` / `00b9969b` (sm_100a + sm_103a) vs `a160d436` / `4e509f24`
(sm_107a): the L2 cache-hint operand differs at four sites.
- **Merge.** Each pair folds into the kept kernel unit with
architecture-selected arms:
- the ten replaced lines take the form that the exporter already emits
inside one program: `#if __CUDA_ARCH__ == <code>` / the arch line /
`#else` / the other line / `#endif`;
- the two moved lines take two else-less guards, written with the
exporter's `__CUDA_ARCH__` comparison: `#if __CUDA_ARCH__ == 1070` at
the sm_107a site, and `#if __CUDA_ARCH__ != 1070` at the sm_100a /
sm_103a site.

  The ten translation units of the dropped members are deleted.
- **Manifest and registry.**
- The five `build.json` entries of the dropped members are renamed in
place to the kept stem. Their sources, kernel digest and binding digest
are now the kept files'.
- The nine kept entries take the merged kernel digest. The list stays
sorted, at 130 entries.
- The five registry records are renamed in place to `<kept>__107` /
`<kept>__103`. Their `kernel` and `library` point at the kept stem.
  - The five routes that named them now name the renamed records.
- No selection rule, grid rule, launch field or workspace rule changes.
- **Proof.**
- A preprocessor emulation of the arch guards reduces each merged unit,
per device pass, to the text of the member built for that architecture.
This holds for sm_100a, sm_103a and sm_107a, with 14 of 14 rows
identical. In the host pass, the emulation reduces each merged unit to
the kept member's text.
- The acceptance gate compiles each merged unit per architecture. It
requires preprocessed text identical to the member that the unit
replaces, and identical SASS per library and architecture.
- The manifest keeps references equal to the entry names (130 == 130).
Every listed source is present, and every digest equals its file.
  - The registry equals the base modulo the five declared renames.
- The per-id GPU test identity on SM103 covers the `35a0b0ca` merge. The
four sm_107a merges are compile-only, with a best-effort GPU run where a
device is available.
- **Declared.**
- The two else-less guards are new forms in this package. In the host
pass `__CUDA_ARCH__` is undefined, so the kept text is selected.
- The five renamed entries keep the closure identifier of the entry they
replace. So their module cache names change, and a warm cache rebuilds
them once. The nine kept entries keep their module names and rebuild
once.
- #7273 names six per-arch copies. This commit merges five of the six.
The sixth pair (`3d20ab4a` / `60f47c5d`) also differs in its binding:
block size 256 vs 512. Merging it needs a per-arch host constant from
the exporter.
  - These are hand folds of exporter-written files.

### Commit 7 (7b66139f4) - collapse dead sm_100a guards in 28 kernels
(29 files, +30 / −170)

- **The guard.** Twenty-eight kernel translation units carry a six-line
shared-memory address block. It is guarded by `#if __CUDA_ARCH__ ==
1000`:
- the sm_100a arm holds an inline-asm `cvta.to.shared` conversion plus
`make_warp_uniform`;
  - the `#else` arm holds `__cvta_generic_to_shared`.

None of these units is built for sm_100a: 24 are sm_107a-only, 2 are
sm_103a-only, and 2 are sm_103a + sm_107a. So every device pass (1030 /
1070) already selects the `#else` line. The host pass does too: the
macro is undefined there and evaluates to 0.
- **Change.**
- Each block collapses to that line. This removes 5 lines per unit, 140
in total.
- The block was the only `__CUDA_ARCH__` conditional in each of the 28
units. `make_warp_uniform` stays in use elsewhere in all of them.
- The 5 remaining sm_100a-only kernels keep their blocks. Dropping their
`#else` arm would change the host-pass text.
- **Manifest.** `build.json` takes the new kernel digest for the 30
entries that list one of the 28 kernels. Binding digests, closure
identifiers, entry names, order and count (130) are unchanged.
- **Proof.**
- A preprocessor emulation of the arch guards reduces the original unit
and the collapsed unit to identical text. This holds in every pass that
the unit is built for and in the host pass (58 of 58 pairs).
- The acceptance gate compiles each of the 30 (library, architecture)
pairs on both sides. It requires preprocessed text identical in every
pass, and identical SASS per library and architecture.
- The manifest keeps references equal to the entry names (130 == 130).
Every listed source is present, and every digest equals its file.
- **Behaviour.** None. The 30 re-digested entries keep their module
names. A warm module cache rebuilds them once.
- **Declared.** These are hand edits of exporter-written files. The
exporter should not emit an arm that a unit's architecture set cannot
take.

### Validation

The compile rows compare the base with the head. They run on a CPU node
with CUDA 13.4 (nvcc 13.4.92), for every (library, architecture) pair of
the manifest. There are three kinds of row:
- 125 identity pairs. Libraries whose sources are unchanged are compared
by file hash. The rest are compiled;
- 6 fold pairs: commit 1's duplicate pair and the five merged pairs of
commit 6. Each merged unit is compiled per architecture and compared
with the member it replaces;
- 30 guard entries over the 28 kernels of commit 7. Every pass must have
identical preprocessed text.

For each architecture, the flag line of record is derived from
`build.json`, using the manifest's own nvcc flags. The gate environment
could not capture the compile plan through the build helper. The last
row below reports this.

**Chain**

- **Pre-checks.** The seven commits must sit in order over the base, and
their subjects must equal the plan. No forbidden shared file may be
touched: `.pre-commit-config.yaml`, `pyproject.toml`,
`tests/test_helpers/cake_package.py`,
`scripts/check_cake_build_manifests.py`, `.github/**`,
`flashinfer/__init__.py` and the backend's shared build helper. The
scope is limited to the package, the facade and the four test files:
INCLUDE_CLOSURE (365 files, Python.h no), F_SHAPE OK (5 source sites, 5
-E sites; informational), GATE_COUNTS OK (11 counts against the chain of
record)

**Compile rows**

- **Kernel units, preprocessed text.** Both `nvcc -E` passes run on
every kernel unit: the device pass per architecture, and the host pass.
The comparison drops line markers and blank lines: 125/125 identity +
6/6 fold (both -E passes identical after the marker drop; the fold rows
compare the kept TU with the removed TU under the hash mask)
- **Binding units, preprocessed text.** The same comparison runs on
every binding unit, in both passes: 125/125 identity + 6/6 fold (binding
host text identical; backtrace sites unchanged)
- **Fold rows.** Each merged or folded unit is checked per architecture.
In the device passes, it must preprocess to the text of the member it
replaces. In the host pass, it must preprocess to the kept member's
text. The rows are the commit-1 pair, plus the 14 device rows and 5 host
rows of commit 6. SASS must be identical per library and architecture:
6/6 fold rows (E-Kf / E-Bf / S-fold / RES-fold / SYM-fold / INFO-fold /
H-fold; U1 duplicate pair + 5 U6 arch merges) compared with the removed
base entries
- **Guard rows.** The 30 (library, architecture) entries of the 28
collapsed kernels must have identical preprocessed text in every pass,
and identical SASS: 28/28 kernels (30 entries) identical in every device
pass and the host pass after the dead-guard collapse
- **SASS.** `nvcc -cubin` builds every compiled kernel on each arm.
`cuobjdump -sass` output is compared per function, after masking
addresses and encodings: 125/125 identity + 6/6 fold (per Function
block; CUDA 13.4; flag line derived from build.json: the generated
compile line was not captured)
- **Symbol tables.** The function lists from `cuobjdump -symbols` must
be identical: 125/125 identity + 6/6 fold: full symbol tables identical
after the declared module-id mask (6/6 entries masked; raw delta -6+6
INFO); resource usage identical per Function on every S row (131);
.nv.info per kernel decoded identical on every compiled row (45;
raw-identical 45)
- **Host objects.** `nvcc -c` builds each binding. The export sets must
be identical: 125/125 identity + 6/6 fold (exports {build_cuda_version,
run} + symbol tables identical); kernel-TU host objects of the fold rows
6/6 identical (INFO)

**Manifest rows** (both trees)

- **Digests.** Every SHA-256 of both trees is recomputed. The digest
diff must be exactly the declared set. Commit 1 removes one entry, and
commit 2 removes one entry. Commit 6 renames 5 entries to the kept stem
with the kept files' digests, and gives 9 kept entries the merged kernel
digest. Commit 7 gives 30 entries the new kernel digest: 0 mismatches on
both trees; entries kept 125 / removed 7 / added 5; 33 kept-source
digests changed (U6 14, U6b 30); entry set == the base minus the removed
plus the declared entries
- **Manifest checker.** `scripts/check_cake_build_manifests.py
--in-tree` runs on both trees. A replica of its rule also runs:
references must equal entry names, and every listed source must be
present: the in-tree manifest checker exit 0 on both trees; replica 0
findings on both trees, registry refs 132 / 130 == entries 132 / 130; 6
documented names resolve on both trees

**Other rows**

- **Reference search.** At the head, the search covers every repository
file that names the package. It looks for the dropped library hashes,
the six removed record keys and the renamed record names: 8/8 reference
rows: 0 hits at HEAD, defined at the base
- **Apply replay.** Each commit's apply script, which works by text and
AST matching, re-runs in order on a fresh copy of the base. Each
resulting tree must equal that commit's tree byte for byte: 7 unit
scripts replayed on the base (U1 U2 U3 U4 U5 U6 U6b); tree identical to
the commits
- **Tests with CUDA hidden** on a CPU node. The four files run on the
base, then on the head. Per-id outcomes must be identical: 411 ids: 35
passed / 376 skipped (CUDA hidden), per-id identical on both trees,
every base-passed id passes on the candidate; host-module import probe
OK on both trees
- **Tests on B200** (SM100). The four files run on the base tree, then
on the head tree. Each arm runs in a fresh JIT workspace, so every
module of the architecture is rebuilt: 46 at the base and 45 at the
head. Per-id outcomes must be identical, skip reasons included. The
files collect 411 ids. On B200, 355 ids pass and 56 skip by design,
because they cover other architectures' builds. Result: 411 ids on B200
(SM100) (driver 580.82.07, cc 10.0): 355 passed / 56 skipped, per-id
identical on both trees; fresh JIT workspace per arm (46 / 45 modules
built per arm, every entry of the arch)
- **Tests on GB300** (SM103). The protocol is the same, with 44 modules
rebuilt on each tree. This row covers the `35a0b0ca` merge of commit 6:
411 ids on GB300 (SM103) (driver 580.159.03, cc 10.3): 355 passed / 56
skipped, per-id identical on both trees; fresh JIT workspace per arm (44
/ 44 modules built per arm, every entry of the arch)
- **Tests on R200** (SM107). The protocol is the same where a device is
available, with 42 modules at the base and 41 at the head. Without an
R200 device run, the four sm_107a merges of commit 6 are compile-only,
as its commit message says: not run on R200 (SM107): no R200 GPU with a
CUDA 13.4 PyTorch environment could be allocated in the validation
window; the sm_107a identity proof is the compile-only rows of the gate
step (preprocessed text, SASS, resource usage, symbol tables, metadata
and host objects over every sm_107a entry)
- **CPU checks.** These run on one node, on both trees:
  - chain shape;
  - `git diff --check`;
  - scope;
  - forbidden files untouched;
  - `py_compile`;
  - ruff;
  - collect-only parity (411 ids);
  - the CUDA-hidden tests;
- pre-commit on the changed files, and with `--all-files` on both
checkouts;
  - the repository's mypy hook, with no new finding;
  - the reference search;
  - the manifest checks;
  - the digest rows;
  - AST identity rows for commits 3, 4 and 5;
- the host-plan stream over every (architecture, route, rows) cell,
identical for commits 2, 3 and 4;
  - the docstring and API-docs checkers for commit 5;
- file hygiene with a per-file baseline from the base. The 14 touched
kernels keep their pre-existing exporter blank-line runs;
  - the apply replay;
  - the public-text scan;
  - the commit-message form;
  - a clean worktree.

  Result: 24/24
- **Rows limited by the environment (count and reason):** 2 row(s): the
JIT build's generated compile line was not captured (the compile-only
rows used the manifest-derived flag line; see the SASS row); the R200
test row (no R200 GPU with a CUDA 13.4 PyTorch environment could be
allocated in the validation window; see its row)

### Not in this PR

- **Host-side overhead items.** These are:
  - redundant library loads through the record-keyed cache;
  - per-call capability queries;
  - the zero-filled workspace of the autograd backward path;
  - duplicated workspace helpers;
  - the device index of `partial_capacity`.

  Each item needs a timing row or an owner decision.
- **Folding the 81 bindings into three launcher headers.** The exporter
is the preferred place for this fold.
- **The sixth per-arch pair (`3d20ab4a` / `60f47c5d`).** Its bindings
differ in block size. Merging it needs a per-arch host constant from the
exporter.
- **The 14 constant-clone kernel clusters.** Folding them needs template
parameters in the exporter.
- **The `#include <cuda_fp8.h>` line in 81 kernels without fp8 use.**
The line comes from the exporter preamble.
- **`check_dense_leading_dims` in the shared checks header.** It has no
callers. The header is shared by 31 packages.
- **The manifest checker's `gencode` / entry-key rules and the
`build.json` hoist.** These touch shared files.
- **The eager import in `flashinfer/__init__.py`.** This is a shared
root file.
- **The five sm_100a-only `#else` arms.** Dropping them would change the
host-pass text.
- **The facade's `__all__` extras `ARCHES`,
`SUPPORTED_COMPUTE_CAPABILITIES` and `route_key`.** They are public
surface, so removing them is an owner decision.
- **The `HIDDEN_SIZES` literal.** It can be derived from the route
tables. This is an exporter item, and the H=5120 variant is coming.
- **Registry trims behind owned-test pins.** This PR does not propose
them.
- **Exporter rules.** The exporter rules for each unit are filed on
#7273 as a comment.

## 🔍 Related Issues

Part of #7273

The deferred items are listed under "Not in this PR". The exporter rules
for each unit are filed on #7273 as a comment.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks run on the changed files, and with `--all-files` on both
checkouts (base and head). The repository's mypy hook must report no new
finding. The CPU checks row in Validation gives the results.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

This PR adds or changes no test. The four files under `tests/norm/`
collect 411 ids at the base and at the head. Validation lists the runs
on B200 and GB300, the R200 row, and the run with CUDA hidden on a CPU
node.

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.

This PR is not experimental. The package lives under `flashinfer/`, and
its tests live under `tests/norm/`. So this PR declares no experimental
test scope.

## Reviewer Notes

- **Hand folds and hand edits.** Commits 1 and 6 fold exporter-written
files by hand. Commits 2, 3, 4 and 7 edit them by hand. The exporter
rules for each unit are filed on #7273 as a comment. Commit 5 edits the
hand-written facade, so a regeneration keeps it.
- **Declared behaviour notes.**
- Commit 1: on sm_100a, the H=512 dw-reduce launch for rows in (4096,
32768] names `kernel_cake_rmsnorm_train_7097069b8eea6ba44d5a` in its
error texts. No test pins them.
  - Commit 3: an out-of-tree reader of the six removed keys would break.
- Commit 4: the records of one class share one `arg_plan` list and one
`logical` dict. No in-tree reader mutates them.
- Commit 5: the backward page gains one clause from the backend text.
The forward and `cake_rmsnorm` pages render the same text.
- Commit 6: the two else-less guards are new forms in this package. The
ten replaced lines use the exporter's `#if … / #else / #endif` form.
- **Module cache.** The five renamed entries of commit 6 keep the
closure identifier of the entry they replace. So their module cache
names change, and a warm cache rebuilds them once. The nine kept entries
of commit 6 and the 30 re-digested entries of commit 7 keep their module
names and rebuild once.
- **Flag line.** The compile rows use the flag line derived from
`build.json`. The gate environment could not capture the compile plan
through the build helper. The GPU test rows build every module through
the JIT path, in a fresh workspace per arm.
- **Coverage.**
- The SM100 tests exercise commit 1's stage record at rows 4097 and
32768.
  - The GB300 tests cover the `35a0b0ca` merge.
- The four sm_107a merges rely on the compile rows unless the R200 row
reports a device run.
- **Base.** This PR is published from `main` `03f82fdda`. `main` at
publish time is `a0a6460f6`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated CUDA execution paths for RMSNorm training on selected GPU
architectures. The changes adjust data-transfer hints, scheduling, and
processing intervals; performance may vary by hardware.
* **Compatibility**
* Standardized shared-memory address handling across CUDA architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [57bf6a3](https://github.com/flashinfer-ai/flashinfer/commit/57bf6a3f5a471afcf156f42d8e6e0b214df8c3a3)

- **作者**: eigen
- **时间**: 2026-10-25T10:16:09Z
- **提交信息**: deslop(sm110): fold the ratio-clone tree units into body headers; drop dead registry leaves and NEED selectors (#7293)

## 📌 Description

### Summary

This PR is round 3 of the deslop program for the two SM110 (Jetson AGX
Thor) decode packages under `flashinfer/experimental/`. `sm110_xqa`
holds the XQA tree and decode routes in 43 kernel translation units and
43 bindings. `sm110_gqa_decode` holds the GQA decode routes in 7 kernel
units and 7 bindings. The Cake exporter generates both packages. Each
package has a `build.json` manifest with the SHA-256 of every source,
and a `cake_jit.py` registry.

Every kernel and binding unit is a generated file. Commits 1 and 3 are
hand folds of generated text, awaiting regeneration from the exporter. A
re-export may re-inline the units and leave the headers unreferenced.

The four commits are mechanical. Each one covers one step of #7221:
- commit 1 folds the 10 ratio-clone sets of `sm110_xqa` into 20 body
headers ("Fold the 10 ratio-clone sets");
- commit 2 drops the dead registry leaves and the gqa forwarding layer
("Drop the dead registry leaves and the gqa forwarding layer");
- commit 3 turns the device-helper headers into supersets and drops the
NEED selector lines ("Superset device-helper headers");
- commit 4 trims the structure-only tests and the duplicate ledger rows
("Trim the structure-only tests and the ledger").

Each commit has its own proof form:
- commit 1: preprocessed-text identity and SASS identity, with one
declared deviation (the backtrace file and line of 600 moved check
sites);
- commit 2: a reference search, and syntax-tree identity after the
declared prunes and rewrites;
- commit 3: SASS and symbol-table identity, with a declared insertion in
the preprocessed text;
- commit 4: syntax-tree identity after the declared prunes, ledger JSON
identity, and exactly one removed test id.

Totals against `main` `03f82fdda`: 120 files changed, +34,596 /
-122,868. Part of #7221.

### Changes

Base: `main` `03f82fdda`. Head:
`578887f4d07128a8054a3f0b2c49165bc8f6b35a` (4 commits). Reviewer Notes
give the `main` sha at publish time.

The per-commit counts overlap on `build.json` and the test files. So
they do not sum to the branch totals.

### Commit 1 (d32f23da3) - fold the 10 ratio-clone sets into body
headers (94 files, +34,632 / -122,078)

- **Ratio-clone sets.** 36 tree libraries of `sm110_xqa` form 10
ratio-clone sets. Within a set, the kernel and binding units differ only
in the GQA ratio literal and the library hash. The sets split by
precision, cache layout and schedule (`tmem_even` / `tmem_odd` /
`pair`).
- **New headers.** Each set folds into one kernel body header,
`csrc/cake_sm110_xqa_tree_<set>_kernel.cuh`, and one binding body
header, `csrc/cake_sm110_xqa_tree_<set>_binding.h`. That makes 20
headers. Each body header is the g2 member's text with these
substitutions:
  - the 8-9 kernel ratio literals become `CAKE_HGS`;
  - the binding box dimensions become `CAKE_HGS_U` / `CAKE_QBOX_U`;
- the hash-bearing tokens become `CAKE_KERNEL_SYMBOL`,
`CAKE_KERNEL_NAME` and `CAKE_BINDING_NAMESPACE`.
- **Stubs.** The 72 units become stubs. Each stub defines those macros
with its member's values and includes the body header. Each stub keeps
its hash-named path, the license block and its `build.json` entry.
- **Kept.** The 4 tuned ratio-8 units and the 3 decode units differ
structurally. They stay as they are. `sm110_gqa_decode` is untouched.
- **Manifest and README.** `build.json` carries the recomputed SHA-256
of the 72 rewritten sources. Every other manifest value is unchanged.
The body headers are not manifest sources, like the existing shared
headers under `csrc/`. The build's header dependency tracking picks up a
header edit. The README lists the 20 headers.
- **Why behaviour is preserved.** Every ratio site is one
integer-literal token in code. None sits inside a string, comment or
include. The hash-bearing sites are identifiers, with two kinds of
exception per binding:
- one string literal (`KERNEL_NAME`), whose macro expands to the same
literal;
  - two comment mentions, which the preprocessor drops.
- **Proof.** Substituting each member's values back into its body header
must reproduce the member's unit byte for byte. The preprocessed kernel
units must be identical after dropping line markers and blank lines. The
SASS of every kernel must be identical.
- **Declared deviation: backtrace file and line.** The binding units
must be identical in the same sense, apart from 600 `TVM_FFI_CHECK` /
`TVM_FFI_THROW` sites. That is 16 per tmem binding and 20 per pair
binding. These sites now live in the body header. A failure backtrace
reports the body header's file, with the line number shifted by a
constant +6. The message texts are unchanged. No test reads a backtrace.

### Commit 2 (a40829d2f) - drop the `launch` and `kernel_symbol` leaves
and the gqa forwarders (9 files, +30 / -387)

- **Registry leaves.** Each record carried two derived leaves that no
loader path reads: `launch` (`cluster`, `cooperative`, `use_pdl`) and
`kernel_symbol`. `cake_jit.entry` finds the binding's run entry through
the library name and `ffi_entry`. The binding launches the kernel
itself. So neither leaf crosses from Python. Both leaves go from all 50
records (43 xqa, 7 gqa).
- **gqa prepared state.** The prepared state held the one host reader of
`kernel_symbol`: the symbol element of each `stages` tuple. That element
goes, so each `stages` entry is a 2-tuple of entry and arguments. The
`launch_names` list built from the symbols goes too. So does the
`kv_capacity` binding, which no record's argument plan consumes.
- **gqa forwarders.** The `sm110_gqa_decode` package `__init__` loses
its three pass-through forwarders (`decode`, `prepare_for_launch`,
`launch_prepared`) and its `__all__`. `flashinfer/decode.py` imports
`sm110_gqa_decode`, `prepare_for_launch` and `launch_prepared` from
`.backend` directly. The arguments are the same as before.
- **Docstring (issue #7221 step 2).** The `num_splits` docstring of
`flashinfer.prepare_sm110_gqa_decode` now follows the route table. It
names the four-slot-ring 64-token-tile build. It sends two requests over
at most 512 keys to the one-split 64-token-tile build, as `select_route`
and the README table do.
- **Tests and README.** 17 test lines restated the removed leaves (12 +
3 + 2 across three test files). They are deleted. The gqa README
sentence on the prepared state drops `launch_names`.
- **Proof.** A reference search runs over every repository file that
names either package. It must find no reader of `launch`,
`kernel_symbol`, `kv_capacity` or `launch_names` outside the removed
definitions and the deleted test lines. Same-named keys of other
packages belong to those packages. For every edited Python file, the
base syntax tree after the declared prunes or rewrites must equal the
result's syntax tree.
- Prunes: the two registry keys of every record, the forwarder
definitions and `__all__`, the pin statements.
- Rewrites: the `stages` tuple, the launch loop header, the three import
lines, the one docstring paragraph.
- **Behaviour notes.**
- `prepared["launch_names"]` disappears, and each `stages` entry is a
2-tuple. The prepared state is documented as opaque.
- `flashinfer.experimental.sm110_gqa_decode.decode`,
`.prepare_for_launch`, `.launch_prepared` and that package's `__all__`
disappear. An out-of-tree caller of those module attributes would break.
- The public wrappers `flashinfer.sm110_gqa_decode`,
`flashinfer.prepare_sm110_gqa_decode` and
`flashinfer.launch_sm110_gqa_decode_prepared` are unchanged, and so are
their signatures.
- No entry cache is added. Neither `backend._entry` is cached, as
before.

### Commit 3 (3b328e63f) - superset device-helper headers; drop the NEED
selector lines (29 files, +15 / -301)

- **Before.** Every kernel unit of both packages selected the guarded
helpers it uses from the shared device helper header. A block of
`CAKE_SM110_*_NEED_*` defines before the include made the selection. The
header wrapped 20 (xqa) and 15 (gqa) of its helpers in matching `#if
defined` guards.
- **Superset headers.** The 70 guard directive lines go from the two
helper headers. Each header is now the whole helper library, in its
existing order and text.
- **Selector lines.** 216 selector lines are deleted:
  - 82 from the 10 kernel body headers;
  - 57 from the 7 unfolded xqa kernel units;
  - 77 from the 6 gqa kernel units that carried them.

The gqa `short` unit had none and is unchanged. Every kernel unit now
includes the whole helper library. The include order
(`math_constants.h`, then the helpers header) is unchanged.
- **Why behaviour is preserved.** Every helper is a forceinline device
function. A definition that a unit never uses is not instantiated. It
emits no code and no symbol. Independently, the libraries build without
relocatable device code. So the compiler compiles each unit as a whole
program and internalises unreferenced device functions before code
generation. The unguarded helpers of both headers were already compiled
into every unit this way. No unit defines a name that a helper uses.
Every selector named an existing guard.
- **Proof.** SASS and symbol tables must be identical for all 50 kernels
(43 xqa, 7 gqa). Each compiled unit must have exactly one kernel entry.
- **Declared insertion.** The preprocessed text is not identical, by
design. After dropping line markers and blank lines, the previous text
of each kernel unit must be an ordered subsequence of the new text. The
inserted lines must be exactly the definitions of the helpers that the
unit did not select. That is 92 to 166 lines per xqa unit and 8 to 108
per gqa unit.
- **Manifests and READMEs.** `build.json` carries the recomputed SHA-256
of the 13 edited kernel sources (7 xqa, 6 gqa). With the 72 of commit 1,
that makes 85 values since the base. Every other manifest value is
unchanged. The helper headers and body headers are not manifest sources.
The README file tables describe the new role of the helper headers.
- **Hand edit.** The units and the helper headers are exporter-generated
files. This commit is a hand edit awaiting regeneration from the
exporter.

### Commit 4 (578887f4d) - trim structure-only test blocks and duplicate
ledger rows (4 files, +1 / -184)

- **Why.** Three test files carried blocks that restated the structure
of the registry tables. These blocks did not exercise the code that
reads the tables. The xqa benchmark ledger carried four rows that time
the same launch as four earlier rows.
- **Test removals.**
- `tests/experimental/test_cake_sm110_xqa.py` loses the test
`test_record_table_is_the_routed_closure` (one test id). It also loses
the module constant `TREE_RECORDS`, whose only readers were inside that
test. The test re-derived four things from the registry literal itself:
the 40-record tree closure, the record naming scheme, the grid rule
fields and the decode record set.
- `tests/experimental/test_cake_sm110_gqa_decode.py` loses the seven
literal `select_rule` dict asserts inside
`test_constants_and_accepted_splits`, with their helper and comment. The
three constant asserts stay.
- `tests/experimental/test_sm110_gqa_decode.py` loses the exact
`set(cake_jit.MODULES)` literal inside
`test_registry_names_delivered_sources`.
- **Remaining coverage.**
- `test_select_record_and_launch_grid` looks up every tree record by
name through `select_record` and checks it against `MODULES`.
- The manifest digest test,
`test_registry_records_reference_the_build_manifest` in both suites,
walks every record and its `build.json` entry.
- The `ROUTE_TABLE` tests and
`test_every_row_carries_the_split_count_its_record_launches` exercise
the gqa `select_rule` tables by behaviour.
- `tests/experimental/test_cake_sm110_gqa_decode.py` asserts the exact
registry set through `RECORDS`.
- Two assertions are not restated elsewhere: the exact tree record count
(40) and the `page_list` presence check. The page128 kernels run on
device.
- **Ledger rows.** `benchmarks/sm110_xqa_shapes.json` drops four rows:
`tree_fp16_contiguous_tmem`, `tree_fp16_paged_tmem`,
`tree_fp8_contiguous_pair` and `tree_fp8_paged_pair`. Each one pinned
the kernel that the automatic choice already makes for its shape. That
is tmem for fp16, and pair for fp8 with an even Q-tile count. So each
row mapped to the same record and shape as one of rows 1-4, and the
benchmark timed the same launch twice. `shape_count` goes from 13 to 9.
- **Kept rows.** The two fp8 tmem rows stay. They pin the tmem schedule
on fp8 shapes that the automatic choice sends to pair, which is a
distinct record. The set of records that the ledger measures is
unchanged. It has nine records:
  - the four tree records of rows 1-4;
  - the two fp8 tmem records;
- the three decode records, one per partition count 4, 2 and 1 of the
capacities 1024, 512 and 256.
- **`--kernel` override.** It applies to every tree row, as before.
`--kernel tmem` runs the six tree rows under the tmem schedule.
`--kernel pair` runs the four fp8 tree rows under pair and reports the
two fp16 rows as unsupported.
- **Ledger reader.** `benchmarks/bench_sm110_xqa.py` iterates the rows
and checks `shape_count` against their number. The ledger SHA-256 that
it records in reports changes by construction.
- **Proof.** For each test file, the previous syntax tree after the
declared prunes must equal the result's. The prunes are the function and
the constant; the helper and the seven asserts; and the one set assert.
Two blank lines must separate neighbouring top-level definitions. For
the ledger, the previous JSON with the four rows removed and
`shape_count` recounted must equal the result. Every kept row must be
byte-identical in serialised form. Exactly one test id goes: 624 ids
collect instead of 625. No other id changes.

### Validation

Three gate runs on a CPU node compare compiler output:
- run A compares the base with commit 1 (strict text identity);
- run B compares commit 2 with commit 3 (the declared insertion class);
- run C compares the base with the head.

Commits 2 and 4 edit no compiled source. Both arms of each run were
staged at the same absolute path. So line markers and `__FILE__` strings
agree between arms.

The compiler rows use CUDA 13.4 (nvcc 13.4.92). They use the manifest's
own flag line for `sm_110a`, which is identical for all 50 libraries:
`-gencode=arch=compute_110a,code=sm_110a -std=c++17 -O3 -DNDEBUG
--compiler-options=-fPIC --expt-relaxed-constexpr -Xfatbin=-compress-all
--compress-mode=size -static-global-template-stub=false
--use_fast_math`.

- Kernel preprocessed text, 50 kernel units. Both passes of `nvcc -E`
ran: the device pass with `__CUDA_ARCH__` = 1100, and the host pass. The
comparison drops `# <n> "<file>"` line markers and whitespace-only
lines. Run A requires identical text. In runs B and C, the older arm's
text must be an ordered subsequence of the newer arm's text. Every
inserted line must come from the helper header. The per-unit
inserted-line counts must match the declared ranges: G-A 50/50 (N0
strict: 36 compiled, 14 coincidence); G-B 50/50 (INS: 50 compiled, 0
coincidence); G-C 50/50 (INS: 50 compiled, 0 coincidence) (both -E
passes identical after N0; INS runs: the base text is an ordered
subsequence, inserted lines attributed to the device-helper headers) and
G-B: rows 50 ok 50 fail 0 coincidence 0 compiled 50 inserted_total 5073;
G-C: rows 50 ok 50 fail 0 coincidence 0 compiled 50 inserted_total 5073
- Binding preprocessed text, 50 binding units, both passes, with the
same comparison. It adds the declared accounting of the 600 check sites
that commit 1 moves. The `TVMFFIBacktrace("<file>", <line>` pairs of the
two arms are paired index by index. Each moved site must name the body
header's file, at one constant +6 line offset. The 14 unfolded bindings
are compared by file hash, without a compile: G-A 50/50 (36 compiled, 14
coincidence; F': 600 moved backtrace sites, expected 600); G-B 50/50 (0
compiled, 50 coincidence); G-C 50/50 (36 compiled, 14 coincidence; F':
600 moved backtrace sites, expected 600) (N0 + F': the moved TVM_FFI
backtrace sites name the body header, one fixed line offset, message
texts unchanged)
- SASS, 50 kernels. `nvcc -cubin` builds each kernel unit per arm.
`cuobjdump -sass` output is compared per function, after masking
instruction addresses and encodings. The `cuobjdump -symbols` function
lists must be identical, with exactly one kernel per unit: G-A 50/50 (36
compiled, 14 coincidence); G-B 50/50 (50 compiled, 0 coincidence); G-C
50/50 (50 compiled, 0 coincidence) (CUDA 13.4) and G-A 50/50 (36
compiled, 14 coincidence); G-B 50/50 (50 compiled, 0 coincidence); G-C
50/50 (50 compiled, 0 coincidence) (STT_FUNC lists identical; kernel
entries == [kernel_<library>])
- Host objects, 50 objects. `nvcc -c` builds each binding unit per arm.
The export sets must be identical. `kernel_<library>` must be undefined.
The host object must hold no device function: G-A 50/50 (36 compiled, 14
coincidence); G-B 50/50 (0 compiled, 50 coincidence); G-C 50/50 (36
compiled, 14 coincidence) (exports + symbol tables identical)
- Manifest digests. Every source SHA-256 in both `build.json` files is
recomputed from the tree, at the base and at the head. The manifest diff
may touch only the SHA-256 values of the 85 edited sources: 72 after
commit 1 and 13 after commit 3: 0 mismatches on both packages of both
trees; 85 source digests changed (79 xqa + 6 gqa), no header digested
- Manifest checker. The upstream `scripts/check_cake_build_manifests.py
--in-tree --package sm110_xqa` runs on both trees. A replica of its rule
runs over both packages, because `sm110_gqa_decode` is not registered
upstream: M1 exit 0 both trees; M2 findings identical to the base (1),
INFO +20 new headers; clang-format no-op on 107 csrc files
- Headers. The 20 new body headers and the 2 modified helper headers are
recorded by path, line count and SHA-256. By design, no manifest digest
covers a header, because the manifest digests the sources handed to
nvcc: 20 new body headers + 2 modified device-helper headers recorded
(sha256 + line count); 20 README rows; no header in any sources list
- Reference search at the head, over the files that name either package.
It covers `launch_names`, `kv_capacity`, `kernel_symbol`, the
launch-reader forms, the forwarders, the four ledger row names,
`TREE_RECORDS` and the removed test id. It has 8 rows: 8/8
(TREE_RECORDS, forwarders, kernel_symbol, kv_capacity, launch_names,
launch_reader, ledger_rows, removed_test: 0 hits at HEAD, > 0 at the
base)
- Apply replay. Each commit's text-matching apply script re-runs in
order on a fresh copy of the base. Each resulting tree must equal that
commit's tree byte for byte: 4 unit scripts replayed on the base with
--map (U1 U2 U3 U4); tree identical to the commits
- Tests on a Jetson AGX Thor (SM110, CC 11.0) with the CUDA 13.4
toolkit, the five test files. The base tree ran first, then the branch
tree. Each arm ran in a fresh JIT workspace, with the 50 module
directories asserted absent. Every id must have the same outcome on both
arms, including skip reasons. The base collects 625 ids and the head
624. The one removed id is `test_record_table_is_the_routed_closure`:
base 625 ids: 590 passed / 35 skipped; head 624 ids: 589 passed / 35
skipped by design on Jetson AGX Thor (SM110) (driver 595.78), per-id
identical on the 624 common ids; 1 structure-only id removed; fresh JIT
workspace per arm
- Tests with CUDA hidden on a CPU node, the same five files, both trees.
Per-id outcomes must be identical. The expected split is 160 passed /
465 skipped at the base and 159 / 465 at the head: base 625 ids: 160
passed / 465 skipped; head 624 ids: 159 passed / 465 skipped (CUDA
hidden), per-id identical on the 624 common ids; 1 id removed by design
- GitHub CI on H100 runs the same five files. On a non-SM110 GPU, the
SM110-only ids skip by their fixture. So 190 passed / 435 skipped are
expected at the base, and 189 / 435 at the head.
- CPU checks on one node, both trees, 19 checks:
  - chain shape and totals;
  - `git diff --check`;
  - scope of the touched paths;
  - the shared files that this PR must not touch are untouched;
  - `py_compile`;
  - ruff on every touched Python file;
  - collect-only parity (625 -> 624 ids, with the removed id named);
  - the CUDA-hidden tests;
- pre-commit on the changed files, and with `--all-files` on both
checkouts (clang-format must be a no-op on the touched csrc files);
  - the repository's mypy hook, with no new finding;
  - the reference search;
  - the upstream and replica manifest checks;
  - the header record;
  - the digest rows;
  - the apply replay;
  - the public-text scan;
  - the commit-message form;
  - a clean worktree.

  Result: 19/19
- Not run (environment): 0

### Not in this PR

- **Unread workspace.** A later step of #7221 stops allocating workspace
that no kernel reads. The change is host-only. It needs an owner
decision on the public `workspace=` contract.
- **The gqa `short` route.** A later step decides this route. The
decision needs Thor timings.
- **The 8 fp8 `tmem_even` records.** A later step decides these records.
The decision needs a Thor sweep.
- **Entry cache.** Neither backend `_entry` is cached at the base. This
PR adds no cache.
- **Owner-side shared-file changes**, for a separate small PR:
  - `pyproject.toml` package data for the gqa `build.json`;
  - registering `sm110_gqa_decode` with the manifest checker;
  - a stale `.clang-format-ignore` line;
  - the pre-commit config line for both csrc trees.
- **Exporter-side changes:**
  - emit the ratio as a parameter;
  - emit the shared fragments once;
  - record header digests;
  - hoist TMA descriptor encodes;
  - accept strided views.
- **Parity, layout and precision twin folds.** These twins are not
text-identical, so a text fold does not cover them.
- **The 13 remaining TMA encoder forms.** This PR leaves them as they
are.
- **Merging the overlapping GPU suites.** The suites overlap. This PR
keeps them separate.

## 🔍 Related Issues

Tracking issue: #7221

Part of #7221

#7221 is the tracking issue for this round. This PR covers its four
mechanical steps for `sm110_xqa` and `sm110_gqa_decode`:
- "Fold the 10 ratio-clone sets";
- "Drop the dead registry leaves and the gqa forwarding layer";
- "Superset device-helper headers";
- "Trim the structure-only tests and the ledger".

The later steps and the exporter-side items are listed under "Not in
this PR".

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks ran on the changed files and with `--all-files` on both
checkouts (base and branch). The repository's mypy hook ran on both
trees. The CPU checks row in Validation gives the results.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Commit 2 deletes 17 test lines that pinned the removed leaves. Commit 4
deletes one test (`test_record_table_is_the_routed_closure`) and two
literal-restatement blocks. No test is added. The collected ids go from
625 to 624. The removed id is the only change.

The five test files are:
- `tests/experimental/sm110_xqa/test_sm110_xqa.py`;
- `tests/experimental/test_cake_sm110_xqa.py`;
- `tests/experimental/test_sm110_gqa_decode.py`;
- `tests/experimental/test_sm110_gqa_decode_prepared.py`;
- `tests/experimental/test_cake_sm110_gqa_decode.py`.

They ran on a Jetson AGX Thor, and with CUDA hidden on a CPU node (see
Validation).

CI targets: the five files in the experimental-tests block below.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #7221
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`.
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

```experimental-tests
tests/experimental/sm110_xqa/test_sm110_xqa.py
tests/experimental/test_cake_sm110_xqa.py
tests/experimental/test_sm110_gqa_decode.py
tests/experimental/test_sm110_gqa_decode_prepared.py
tests/experimental/test_cake_sm110_gqa_decode.py
```

Both packages are experimental and live under
`flashinfer/experimental/`. Their tests live under
`tests/experimental/`. These five files are the CI run targets.

Outside the two packages, this PR edits three kinds of file:
- test files under `tests/experimental/`;
- the benchmark ledger `benchmarks/sm110_xqa_shapes.json`;
- `flashinfer/decode.py`.

In `flashinfer/decode.py`, it changes only the three import lines and
one docstring paragraph. The public wrappers and their signatures are
unchanged. The runnable examples are the two benchmarks,
`benchmarks/bench_sm110_xqa.py` and
`benchmarks/bench_sm110_gqa_decode.py`. This PR changes the xqa ledger
but neither benchmark script. Neither package is registered in
`flashinfer/aot.py`, and neither is reachable from `backend="auto"`.
Their entry points are the `@flashinfer_experimental_api` functions in
`flashinfer/decode.py` and `flashinfer/sm110_xqa.py`.

## Reviewer Notes

- **Hand folds.** Commits 1 and 3 edit exporter-generated files by hand.
A re-export may re-inline the units and leave the headers unreferenced.
The exporter-side items under "Not in this PR" are the durable solution.
- **Declared deviation (commit 1).** For the 600 moved check sites, a
failure backtrace names the body header's file, with the line shifted by
+6. The message texts are unchanged.
- **Declared insertion (commit 3).** The preprocessed text of each
kernel unit gains the definitions of the helpers that it did not select.
The SASS and symbol rows compare every kernel.
- **Behaviour notes (commit 2).** `prepared["launch_names"]` and the gqa
package forwarders disappear. An out-of-tree caller of them would break.
The public wrappers and their signatures are unchanged.
- **Header digests.** No digest covers the 20 body headers or the 2
helper headers. The manifest digests the sources handed to nvcc, and
those sources `#include` the headers.
- **Coverage.** The CUDA-hidden run and the H100 CI exercise the host
paths. The kernel paths run only on SM110. They ran on a Jetson AGX
Thor, as Validation describes.
- **Base.** This PR is based on `main` `03f82fdda`. `main` at publish
time is `a0a6460f6`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified SM110 GQA decode routing guidance for one or two requests
versus larger batches, including the applicable cache-length ranges and
split options.
* Updated SM110 XQA documentation to describe shared kernel and binding
coverage.

* **Refactor**
* Consolidated SM110 XQA bindings and decode launch handling while
retaining the documented decode routing options.

* **Benchmarks**
  * Reduced the SM110 XQA benchmark shape set from 13 cases to 9.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [923ff13](https://github.com/flashinfer-ai/flashinfer/commit/923ff1321520f1495a0f64493f34a045e9f6d116)

- **作者**: eigen
- **时间**: 2026-10-25T10:15:39Z
- **提交信息**: perf(cake_nvfp4_mla_decode): faster SM100 / SM103 decode with a native E2M1 x E4M3 dequant multiply and a shorter softmax chain (#7306)

`cake_nvfp4_mla_decode`
(`flashinfer.mla.prepare_nvfp4_batch_decode_with_kv_cache_mla`,
experimental) has one variant. That variant is MLA decode with NVFP4
queries and KV cache: E2M1 values with UE4M3 block-16 scales, one
512-wide latent row per token used as both K and V, 64-token pages, an
optional per-head attention sink, BF16 output and FP32 LSE. A persistent
decode kernel and a split-KV combine kernel serve it.

This PR replaces that variant's programs with faster builds of the same
kernel. The baseline is the previous Cake version of this kernel, as
currently shipped in `main`. Speedup is 1.046x to 1.124x on GB300 and
1.029x to 1.074x on B200.

Each value is the median latency of one complete call (decode, plus the
combine when a request is split), measured with a cold L2. Speedup is
the `main` latency divided by this PR's latency.

**NVIDIA GB300 (sm_103a), CUDA 13.4**

| Shape | `main` (µs) | This PR (µs) | Speedup |
|---|---:|---:|---:|
| 2 requests (256, 300 keys), 64 heads, 6 query tokens, forced 2-way
split | 12.86 | 12.30 | 1.046x |
| 3 requests (1000, 8192, 5000 keys), 8 heads, 6 query tokens | 27.30 |
25.82 | 1.057x |
| 4 requests (64, 65, 4096, 777 keys), 64 heads, 1 query token, no sink
| 36.26 | 32.59 | 1.112x |
| batch 32, 8K keys each, 64 heads, 6 query tokens | 92.35 | 83.57 |
1.105x |
| batch 32, 16K keys each, 64 heads, 6 query tokens | 163.17 | 147.44 |
1.107x |
| batch 32, 32K keys each, 64 heads, 6 query tokens | 303.87 | 272.07 |
1.117x |
| batch 32, 64K keys each, 64 heads, 6 query tokens | 598.32 | 532.19 |
1.124x |
| batch 32, 128K keys each, 64 heads, 6 query tokens | 1189.57 | 1058.39
| 1.124x |

**NVIDIA B200 (sm_100a), CUDA 13.4**

| Shape | `main` (µs) | This PR (µs) | Speedup |
|---|---:|---:|---:|
| 2 requests (256, 300 keys), 64 heads, 6 query tokens, forced 2-way
split | 13.41 | 13.02 | 1.029x |
| 3 requests (1000, 8192, 5000 keys), 8 heads, 6 query tokens | 28.94 |
27.20 | 1.064x |
| 4 requests (64, 65, 4096, 777 keys), 64 heads, 1 query token, no sink
| 39.65 | 37.04 | 1.070x |
| batch 32, 8K keys each, 64 heads, 6 query tokens | 105.30 | 98.02 |
1.074x |
| batch 32, 16K keys each, 64 heads, 6 query tokens | 187.26 | 176.40 |
1.062x |
| batch 32, 32K keys each, 64 heads, 6 query tokens | 407.07 | 382.91 |
1.063x |
| batch 32, 64K keys each, 64 heads, 6 query tokens | 811.83 | 768.35 |
1.057x |
| batch 32, 128K keys each, 64 heads, 6 query tokens | 1625.40 | 1543.81
| 1.053x |

Cake ships no other data type, layout or fused form of this decode, and
the kernel ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded experimental NVFP4 MLA decode support with CUDA kernels for
supported GPU architectures. The package can use compatible prebuilt
libraries or compile them on demand.
* Added validation for tensor inputs and launch configurations, with
clearer errors for unsupported or incompatible inputs.
* **Tests**
* Expanded coverage of the experimental decode API, including output
comparisons against a reference implementation and checks for
unsupported configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ce1758b](https://github.com/flashinfer-ai/flashinfer/commit/ce1758b8b38feff3b994ccd3d2fd34be4210b2e2)

- **作者**: eigen
- **时间**: 2026-10-25T10:13:21Z
- **提交信息**: perf(cake_softmax): shared-tile Blackwell cached-cluster softmax for wide multi-wave rows (#7308)

`flashinfer.sampling.softmax` on Blackwell (`cake_blackwell_softmax`)
has one data type (FP32) and one layout (row-major `[rows, vocab]`). It
can fuse a scalar or per-row temperature, and it can use PDL on sm_103a.
After this PR, 14 Cake programs serve it: a warp program, a rowwise
program, a bootstrap program, 7 row-caching cluster programs (1- to
16-CTA clusters x 4 or 8 tiles), 2 persistent programs (8- and 16-CTA
clusters, 8 tiles) and 2 new shared-tile programs (8- and 16-CTA
clusters, 4 register tiles plus up to 4 shared-memory tiles per CTA).
This PR delivers the 2 shared-tile programs. Each CTA keeps half of its
8-tile chunk in shared memory, so four CTAs per SM stay resident instead
of two. Compared with the previous Cake version in FlashInfer main
(`a0a6460f6`, which includes #7277), the geometric-mean speedup across
the 41 shapes below is 1.008x on B200 and 1.009x on GB300. The
shared-tile route serves 9 of the 41 shapes on B200 and 8 on GB300: 16 ×
256000, 32 × 256000, 64 × 128000, 256 × 256000, 512 × 128000, 512 ×
256000, 1024 × 128000 and 1024 × 256000 on both GPUs, plus 128 × 256000
on B200. The largest gains are 1.081x on B200 (16 × 256000) and 1.173x
on GB300 (32 × 256000). The other shapes keep their previous kernels and
measure between 0.996x and 1.004x, which is measurement noise.

Latency in microseconds (median, cold L2), previous Cake version (main
`a0a6460f6`) vs this PR, on B200 (sm_100a) and GB300 (sm_103a); CUDA
13.4 (nvcc 13.4.2), PyTorch 2.14.1+cu130.

| rows × vocab | B200 previous (µs) | B200 this PR (µs) | B200 speedup |
GB300 previous (µs) | GB300 this PR (µs) | GB300 speedup |
|---|---:|---:|---:|---:|---:|---:|
| 1 × 32000 | 2.53 | 2.53 | 1.000× | 2.40 | 2.40 | 1.000× |
| 1 × 64000 | 2.91 | 2.91 | 1.000× | 2.78 | 2.78 | 1.000× |
| 1 × 128000 | 3.46 | 3.46 | 1.000× | 3.20 | 3.20 | 1.000× |
| 1 × 256000 | 4.58 | 4.58 | 1.000× | 4.16 | 4.16 | 1.004× |
| 4 × 32000 | 2.82 | 2.82 | 1.000× | 2.59 | 2.59 | 1.003× |
| 4 × 64000 | 3.07 | 3.07 | 1.000× | 2.78 | 2.78 | 1.000× |
| 4 × 128000 | 3.62 | 3.62 | 1.000× | 3.33 | 3.33 | 1.000× |
| 4 × 256000 | 4.96 | 4.96 | 1.000× | 4.58 | 4.58 | 1.000× |
| 8 × 32000 | 2.91 | 2.91 | 1.000× | 2.78 | 2.78 | 1.000× |
| 8 × 64000 | 3.39 | 3.42 | 1.000× | 3.20 | 3.20 | 1.000× |
| 8 × 128000 | 4.51 | 4.51 | 1.000× | 4.22 | 4.22 | 1.000× |
| 8 × 256000 | 6.98 | 6.98 | 1.000× | 6.50 | 6.50 | 1.000× |
| 16 × 32000 | 3.23 | 3.23 | 1.000× | 2.98 | 2.98 | 1.000× |
| 16 × 64000 | 4.00 | 4.03 | 0.996× | 3.74 | 3.74 | 1.000× |
| 16 × 128000 | 5.79 | 5.79 | 1.000× | 5.44 | 5.44 | 1.000× |
| 16 × 256000 | 10.69 | 9.89 | 1.081× | 10.05 | 9.50 | 1.057× |
| 32 × 32000 | 5.02 | 5.02 | 1.000× | 3.55 | 3.55 | 1.000× |
| 32 × 64000 | 5.89 | 5.89 | 1.000× | 4.83 | 4.83 | 1.000× |
| 32 × 128000 | 8.16 | 8.16 | 0.999× | 7.39 | 7.39 | 1.000× |
| 32 × 256000 | 15.81 | 14.78 | 1.069× | 15.20 | 12.96 | 1.173× |
| 64 × 32000 | 4.90 | 4.87 | 1.000× | 4.67 | 4.67 | 1.000× |
| 64 × 64000 | 7.26 | 7.26 | 1.000× | 7.20 | 7.20 | 1.000× |
| 64 × 128000 | 14.53 | 13.57 | 1.071× | 13.38 | 12.70 | 1.053× |
| 64 × 256000 | 24.77 | 24.77 | 1.000× | 24.16 | 24.16 | 0.999× |
| 128 × 32000 | 7.20 | 7.20 | 1.000× | 7.01 | 7.01 | 1.000× |
| 128 × 64000 | 11.71 | 11.71 | 1.000× | 11.49 | 11.49 | 1.000× |
| 128 × 128000 | 22.56 | 22.56 | 1.001× | 21.38 | 21.38 | 1.000× |
| 128 × 256000 | 42.69 | 42.08 | 1.014× | 41.79 | 41.79 | 0.999× |
| 256 × 32000 | 11.17 | 11.17 | 1.000× | 11.01 | 11.01 | 1.000× |
| 256 × 64000 | 19.68 | 19.68 | 1.000× | 19.01 | 19.04 | 0.999× |
| 256 × 128000 | 40.64 | 40.61 | 0.999× | 36.58 | 36.61 | 1.000× |
| 256 × 256000 | 79.78 | 79.01 | 1.010× | 77.60 | 76.06 | 1.021× |
| 512 × 32000 | 18.72 | 18.72 | 1.000× | 18.34 | 18.34 | 1.000× |
| 512 × 64000 | 37.41 | 37.44 | 0.999× | 36.13 | 36.13 | 1.000× |
| 512 × 128000 | 79.44 | 77.28 | 1.028× | 76.56 | 74.30 | 1.029× |
| 512 × 256000 | 153.38 | 153.23 | 1.001× | 150.66 | 148.83 | 1.012× |
| 1024 × 32000 | 35.68 | 35.68 | 1.000× | 34.53 | 34.53 | 1.000× |
| 1024 × 64000 | 73.89 | 73.89 | 1.000× | 71.81 | 71.82 | 1.000× |
| 1024 × 128000 | 161.15 | 152.26 | 1.058× | 153.57 | 147.01 | 1.045× |
| 1024 × 256000 | 306.78 | 302.34 | 1.015× | 297.22 | 293.94 | 1.011× |
| 64 × 32000 (scalar temperature, PDL) | 4.86 | 4.86 | 1.000× | 4.70 |
4.70 | 1.000× |
| geometric mean | | | 1.008× | | | 1.009× |

The family's other Cake programs are the warp, rowwise, bootstrap,
row-caching cluster and persistent programs, and the whole family ships
on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Blackwell GPU softmax now supports additional cached execution paths,
expanding the range of workloads that can use optimized processing.
* Execution can select between shared-memory and persistent processing
based on workload characteristics.
* **Tests**
* Expanded coverage for softmax route selection and result correctness
across additional workload scenarios.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7888b26](https://github.com/flashinfer-ai/flashinfer/commit/7888b26bf6b5bc5d9c33cd104bb4d6cd18121c5f)

- **作者**: eigen
- **时间**: 2026-10-25T10:13:01Z
- **提交信息**: perf(cake_trtllm_moe_allreduce_union): latency-ordered one-shot and two-shot schedules for SM100/SM103 (#7298)

The Cake MoE all-reduce fusion union,
`flashinfer.comm.trtllm_moe_allreduce_fusion(..., backend="cake")`, does
four things in one fused call: the MoE finalize reduction (the scaled
sum of the active experts' outputs plus the shared token input), the
all-reduce across ranks, and the residual add and RMSNorm. It writes the
all-reduce output, the new residual and the normalized output. The union
has 12 variants: 2 data types (bf16, fp16) x 3 world sizes (2, 4, 8) x
PDL launch on/off. This PR gives every variant new schedules: a
latency-ordered one-shot exchange and a two-shot (reduce-scatter +
all-gather) exchange, chosen by token count and active-expert count.
Outputs are bitwise identical to before. Compared with the previous Cake
version (the union currently on FlashInfer main), every one of the 30
measured shapes is faster on both GPUs: 1.05x-2.64x on B200 and
1.03x-2.67x on B300.

Median latency per call in µs, hidden size 7168, previous Cake union vs
this PR. NVIDIA B200 (sm_100a, driver 580.82.07) and NVIDIA B300 SXM6 AC
(sm_103a, driver 580.126.09), CUDA 13.4.

| World size | dtype | Tokens | Active experts | PDL | B200 previous
(µs) | B200 this PR (µs) | B200 speedup | B300 previous (µs) | B300 this
PR (µs) | B300 speedup |
|---:|---|---:|---:|---|---:|---:|---:|---:|---:|---:|
| 2 | bf16 | 1 | 8 | off | 9.47 | 8.42 | 1.12x | 10.18 | 8.96 | 1.13x |
| 2 | bf16 | 64 | 8 | on | 13.41 | 12.70 | 1.05x | 14.34 | 13.66 | 1.05x
|
| 2 | bf16 | 128 | 16 | off | 18.08 | 17.09 | 1.05x | 18.94 | 18.08 |
1.05x |
| 2 | bf16 | 256 | 8 | off | 21.15 | 20.22 | 1.05x | 22.18 | 21.47 |
1.03x |
| 2 | bf16 | 256 | 12 | on | 24.58 | 22.53 | 1.09x | 28.06 | 23.71 |
1.18x |
| 2 | bf16 | 2048 | 12 | on | 134.93 | 120.10 | 1.12x | 126.50 | 120.74
| 1.04x |
| 2 | fp16 | 64 | 12 | off | 15.29 | 13.02 | 1.18x | 16.58 | 14.05 |
1.19x |
| 2 | fp16 | 128 | 16 | on | 18.30 | 17.25 | 1.05x | 19.30 | 18.21 |
1.06x |
| 2 | fp16 | 2048 | 8 | off | 114.24 | 98.78 | 1.16x | 108.99 | 98.91 |
1.10x |
| 2 | fp16 | 2048 | 16 | on | 156.10 | 139.04 | 1.12x | 142.69 | 138.24
| 1.03x |
| 4 | bf16 | 1 | 8 | off | 9.41 | 8.38 | 1.13x | 10.59 | 9.79 | 1.08x |
| 4 | bf16 | 64 | 8 | on | 15.52 | 14.43 | 1.08x | 16.80 | 15.68 | 1.08x
|
| 4 | bf16 | 128 | 16 | off | 24.58 | 19.01 | 1.30x | 24.03 | 20.16 |
1.19x |
| 4 | bf16 | 256 | 8 | off | 33.86 | 24.03 | 1.41x | 33.79 | 25.50 |
1.33x |
| 4 | bf16 | 256 | 12 | on | 35.04 | 26.85 | 1.31x | 35.87 | 28.03 |
1.28x |
| 4 | bf16 | 2048 | 12 | on | 197.02 | 139.81 | 1.41x | 194.91 | 140.10
| 1.39x |
| 4 | fp16 | 64 | 12 | off | 17.95 | 14.85 | 1.20x | 18.91 | 15.94 |
1.19x |
| 4 | fp16 | 128 | 16 | on | 23.97 | 19.23 | 1.24x | 24.93 | 20.35 |
1.23x |
| 4 | fp16 | 2048 | 8 | off | 181.44 | 124.93 | 1.45x | 180.51 | 126.02
| 1.43x |
| 4 | fp16 | 2048 | 16 | on | 208.74 | 158.27 | 1.32x | 208.06 | 159.11
| 1.31x |
| 8 | bf16 | 1 | 8 | off | 11.10 | 10.05 | 1.11x | 10.88 | 10.53 | 1.04x
|
| 8 | bf16 | 64 | 8 | on | 24.00 | 16.61 | 1.45x | 23.68 | 17.15 | 1.38x
|
| 8 | bf16 | 128 | 16 | off | 37.41 | 21.22 | 1.76x | 36.99 | 22.08 |
1.68x |
| 8 | bf16 | 256 | 8 | off | 60.35 | 26.08 | 2.31x | 59.55 | 26.75 |
2.22x |
| 8 | bf16 | 256 | 12 | on | 62.24 | 28.74 | 2.17x | 63.01 | 29.63 |
2.12x |
| 8 | bf16 | 2048 | 12 | on | 367.26 | 150.21 | 2.44x | 365.54 | 148.48
| 2.46x |
| 8 | fp16 | 64 | 12 | off | 24.16 | 16.77 | 1.45x | 24.42 | 17.41 |
1.40x |
| 8 | fp16 | 128 | 16 | on | 37.25 | 21.41 | 1.74x | 37.06 | 22.11 |
1.68x |
| 8 | fp16 | 2048 | 8 | off | 357.76 | 135.26 | 2.64x | 357.92 | 134.14
| 2.67x |
| 8 | fp16 | 2048 | 16 | on | 371.62 | 168.32 | 2.21x | 370.47 | 167.14
| 2.21x |

The other Cake kernel for this operation is the MoE finalize all-reduce
fusion, `flashinfer.comm.trtllm_moe_finalize_allreduce_fusion(...,
backend="cake")`, which has its own Cake kernels; the union supports
bf16 and fp16 at hidden size 7168 with no quantized outputs and ships on
sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* Updated automatic MoE all-reduce specialization selection for
supported GPU architectures, world sizes, data types, and token/expert
ranges. Configurations that match the new selection rules use the
corresponding latency-focused or two-shot path; other configurations
continue to use the existing fallback.
* Removed several previous specialized all-reduce paths. Their
availability may change for configurations that previously selected
them.
* **Tests**
* Expanded specialization-selection coverage across supported
configurations and range boundaries.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [cc8552a](https://github.com/flashinfer-ai/flashinfer/commit/cc8552a3a0158391f514571597b3b495090ce43c)

- **作者**: eigen
- **时间**: 2026-10-25T10:07:28Z
- **提交信息**: feat(cake_qsa_nvfp4): tcgen05 decode programs for SM107 (#7284)

This PR adds the compute capability 10.7 variant of `cake_qsa_nvfp4`.
The kernel is the sparse paged GQA decode over an NVFP4 KV cache, with
bf16 queries, NVFP4 paged keys/values, and both `NHD` and `HND` layouts.
It is reached through `flashinfer.sparse.qsa_sparse_paged_attention(...,
backend="cake")`. The kernel has two device programs. The mma.sync
program covers compute capability 8.x / 9.0. The tcgen05 program covers
compute capability 10.0 / 10.3 and, with this PR, 10.7. Each program has
a split form (decode + merge kernels). On 10.0 / 10.3 there is also a
fused (cooperative) form, used on aarch64 hosts at 4 or fewer query rows
outside a stream capture; 10.7 keeps the split form on every host (its
fused form measured no faster at any row). This PR compiles the tcgen05
decode (plain and cooperative) and the merge for `sm_107a`. Their device
text is the same as the 10.0 / 10.3 units except for the shared-memory
descriptor field. There is no earlier Cake version of this kernel for
10.7, so the baseline is FlashInfer's own `qsa_sparse_paged_attention`
reference backend built for the device.

Speedup of this PR's route (`backend="cake"`) over the FlashInfer
reference (`qsa_nvfp4`, host guard bypassed, built for the device) on
NVIDIA R200 (compute capability 10.7, 212 SMs, sm_107a), driver 620.62,
CUDA 13.4 (torch 2.14.1+cu130); whole call (decode + merge), medians of
3 x 64 cold-L2 samples (memset flush), eager launches; 24 x 2 heads,
2051 selected tokens per row.

| layout | rows | FlashInfer reference us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 13.15 | 9.15 | 1.44x |
| NHD | 2 | 13.87 | 9.54 | 1.45x |
| NHD | 4 | 13.81 | 10.37 | 1.33x |
| NHD | 8 | 16.98 | 11.18 | 1.52x |
| NHD | 16 | 24.11 | 13.42 | 1.80x |
| NHD | 32 | 39.12 | 16.59 | 2.36x |
| NHD | 64 | 68.56 | 29.07 | 2.36x |
| NHD | 128 | 151.44 | 55.52 | 2.73x |
| HND | 1 | 13.39 | 9.15 | 1.46x |
| HND | 2 | 13.62 | 9.63 | 1.41x |
| HND | 4 | 13.89 | 10.46 | 1.33x |
| HND | 8 | 17.12 | 11.26 | 1.52x |
| HND | 16 | 24.27 | 13.65 | 1.78x |
| HND | 32 | 39.78 | 16.93 | 2.35x |
| HND | 64 | 68.93 | 28.88 | 2.39x |
| HND | 128 | 152.98 | 56.19 | 2.72x |

Speedup of this PR's route (`backend="cake"`) over the FlashInfer
reference (`qsa_nvfp4`, host guard bypassed, built for the device) on
NVIDIA R200 (compute capability 10.7, 212 SMs, sm_107a), driver 620.62,
CUDA 13.4 (torch 2.14.1+cu130); whole call (decode + merge), medians of
3 x 64 cold-L2 samples (read flush), eager launches; 24 x 2 heads, 2051
selected tokens per row.

| layout | rows | FlashInfer reference us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 13.28 | 9.06 | 1.47x |
| NHD | 2 | 13.70 | 9.41 | 1.46x |
| NHD | 4 | 13.66 | 10.08 | 1.36x |
| NHD | 8 | 16.96 | 10.94 | 1.55x |
| NHD | 16 | 24.03 | 13.12 | 1.83x |
| NHD | 32 | 38.62 | 16.27 | 2.37x |
| NHD | 64 | 67.47 | 28.83 | 2.34x |
| NHD | 128 | 151.57 | 54.99 | 2.76x |
| HND | 1 | 13.44 | 9.07 | 1.48x |
| HND | 2 | 13.54 | 9.42 | 1.44x |
| HND | 4 | 13.82 | 10.18 | 1.36x |
| HND | 8 | 16.99 | 11.12 | 1.53x |
| HND | 16 | 24.13 | 13.28 | 1.82x |
| HND | 32 | 39.22 | 16.45 | 2.38x |
| HND | 64 | 67.86 | 28.54 | 2.38x |
| HND | 128 | 153.17 | 55.63 | 2.75x |

The same pair under CUDA-graph replay on NVIDIA R200 (compute capability
10.7, 212 SMs, sm_107a), driver 620.62, CUDA 13.4 (torch 2.14.1+cu130);
whole call (decode + merge), medians of 3 x 64 cold-L2 samples (memset
flush), CUDA-graph replay of each arm's whole call; 24 x 2 heads, 2051
selected tokens per row.

| layout | rows | FlashInfer reference us | this PR us | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 12.77 | 8.75 | 1.46x |
| NHD | 2 | 13.60 | 9.10 | 1.49x |
| NHD | 4 | 13.87 | 10.30 | 1.35x |
| NHD | 8 | 17.15 | 11.07 | 1.55x |
| NHD | 16 | 24.16 | 13.60 | 1.78x |
| NHD | 32 | 39.09 | 16.91 | 2.31x |
| NHD | 64 | 68.48 | 29.11 | 2.35x |
| NHD | 128 | 151.40 | 55.65 | 2.72x |
| HND | 1 | 13.46 | 9.63 | 1.40x |
| HND | 2 | 13.47 | 9.86 | 1.37x |
| HND | 4 | 13.82 | 10.70 | 1.29x |
| HND | 8 | 17.46 | 11.28 | 1.55x |
| HND | 16 | 24.66 | 13.79 | 1.79x |
| HND | 32 | 39.89 | 17.25 | 2.31x |
| HND | 64 | 69.07 | 28.98 | 2.38x |
| HND | 128 | 152.56 | 56.42 | 2.70x |

With this PR, the `cake_qsa_nvfp4` family ships the mma.sync decode for
`sm_80` / `sm_90a` and the tcgen05 decode for `sm_100a` / `sm_103a` /
`sm_107a`, with the split merge on all five.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added Cake QSA NVFP4 support for R200 GPUs (compute capability 10.7),
including automatic backend selection.
* R200 uses split-form decoding and merging, with launch behavior tuned
for its hardware capacity.
* **Documentation**
* Updated support and backend guidance to cover R200 and clarify that
compute capability 12.x uses the default implementation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [fd0e4fd](https://github.com/flashinfer-ai/flashinfer/commit/fd0e4fdd96b046b1433a44e9eec8f0c3d8fe9e70)

- **作者**: eigen
- **时间**: 2026-10-25T09:39:51Z
- **提交信息**: perf(cake_minimax_h3): 256 x 448 MXFP8 FC1 with staggered accumulator halves in the MLP block on SM100 / SM103 (#7304)

The Cake MiniMax-H3 MLP block (`minimax_h3_mlp*`) fuses RMSNorm + AdaLN
(+ activation quantization) -> FC1 + SwiGLU -> FC2 + gate + residual. On
SM100/SM103 it has three variants: BF16 (`minimax_h3_mlp`), MXFP8
(`minimax_h3_mlp_mxfp8`) and NVFP4 (`minimax_h3_mlp_nvfp4`). This PR
adds a new FC1 program to the MXFP8 variant. `minimax_h3_mlp_mxfp8` now
also accepts FC1 weight scale tiles from
`prepare_minimax_h3_fc1_swiglu_weight_mxfp8` and runs them on a 256 x
448 FC1 tile. The existing scale layout keeps the existing kernel. The
baseline is the previous Cake version of this block:
`minimax_h3_mlp_mxfp8` on FlashInfer main. Across 40 shapes (M = token
rows; hidden 5376, intermediate 14336), the new path is 1.023x-1.060x
faster on B200 and 1.033x-1.068x faster on B300, with outputs bitwise
identical to the existing kernel. Speedup = FlashInfer main ms / this PR
ms.

**NVIDIA B200 (sm_100a), CUDA 13.4.** Whole MLP block, CUDA graph, cold
L2, median of 6 CUPTI-timed rounds.

| M | FlashInfer main (ms) | this PR (ms) | speedup |
|---:|---:|---:|---:|
| 4184 | 0.8132 | 0.7803 | 1.042x |
| 4816 | 0.9300 | 0.8773 | 1.060x |
| 4823 | 0.9324 | 0.8847 | 1.054x |
| 4824 | 0.9192 | 0.8773 | 1.048x |
| 4825 | 0.9201 | 0.8772 | 1.049x |
| 4832 | 0.9215 | 0.8810 | 1.046x |
| 6096 | 1.1524 | 1.0953 | 1.052x |
| 7368 | 1.3939 | 1.3317 | 1.047x |
| 8368 | 1.6275 | 1.5448 | 1.054x |
| 9280 | 1.7974 | 1.7054 | 1.054x |
| 9632 | 1.8239 | 1.7348 | 1.051x |
| 9647 | 1.8244 | 1.7404 | 1.048x |
| 9648 | 1.8266 | 1.7436 | 1.048x |
| 9649 | 1.8270 | 1.7361 | 1.052x |
| 9664 | 1.8287 | 1.7350 | 1.054x |
| 12192 | 2.3269 | 2.2268 | 1.045x |
| 13744 | 2.6020 | 2.4655 | 1.055x |
| 14736 | 2.7960 | 2.6846 | 1.041x |
| 16736 | 3.2558 | 3.1238 | 1.042x |
| 18560 | 3.5617 | 3.3675 | 1.058x |
| 19264 | 3.6670 | 3.5146 | 1.043x |
| 19295 | 3.6641 | 3.5066 | 1.045x |
| 19296 | 3.6338 | 3.4617 | 1.050x |
| 19297 | 3.6547 | 3.5154 | 1.040x |
| 19328 | 3.6561 | 3.5163 | 1.040x |
| 24384 | 4.7098 | 4.5619 | 1.032x |
| 27488 | 5.2228 | 5.0239 | 1.040x |
| 29472 | 5.5555 | 5.3022 | 1.048x |
| 33472 | 6.3595 | 6.0741 | 1.047x |
| 37120 | 7.2590 | 6.9556 | 1.044x |
| 38528 | 7.3077 | 7.0634 | 1.035x |
| 38591 | 7.2745 | 7.1085 | 1.023x |
| 38592 | 7.2328 | 6.8560 | 1.055x |
| 38593 | 7.5461 | 7.2039 | 1.048x |
| 38656 | 7.5535 | 7.2607 | 1.040x |
| 48768 | 9.3097 | 9.0164 | 1.033x |
| 54976 | 10.3099 | 9.9040 | 1.041x |
| 58944 | 11.0942 | 10.6453 | 1.042x |
| 74240 | 14.1096 | 13.7136 | 1.029x |
| 109952 | 20.6112 | 19.7886 | 1.042x |

**NVIDIA B300 (sm_103a), CUDA 13.4.** Whole MLP block, CUDA graph, cold
L2, median of 6 CUPTI-timed rounds.

| M | FlashInfer main (ms) | this PR (ms) | speedup |
|---:|---:|---:|---:|
| 4184 | 0.7979 | 0.7520 | 1.061x |
| 4816 | 0.9062 | 0.8524 | 1.063x |
| 4823 | 0.9047 | 0.8527 | 1.061x |
| 4824 | 0.9181 | 0.8599 | 1.068x |
| 4825 | 0.9205 | 0.8646 | 1.065x |
| 4832 | 0.9198 | 0.8649 | 1.063x |
| 6096 | 1.1227 | 1.0623 | 1.057x |
| 7368 | 1.3899 | 1.3211 | 1.052x |
| 8368 | 1.5871 | 1.5001 | 1.058x |
| 9280 | 1.7613 | 1.6621 | 1.060x |
| 9632 | 1.8145 | 1.7277 | 1.050x |
| 9647 | 1.8145 | 1.7267 | 1.051x |
| 9648 | 1.7805 | 1.6883 | 1.055x |
| 9649 | 1.8124 | 1.7099 | 1.060x |
| 9664 | 1.8132 | 1.7125 | 1.059x |
| 12192 | 2.2876 | 2.1694 | 1.054x |
| 13744 | 2.5957 | 2.4834 | 1.045x |
| 14736 | 2.7482 | 2.6239 | 1.047x |
| 16736 | 3.1856 | 3.0429 | 1.047x |
| 18560 | 3.4746 | 3.3029 | 1.052x |
| 19264 | 3.6172 | 3.4340 | 1.053x |
| 19295 | 3.6205 | 3.4363 | 1.054x |
| 19296 | 3.6335 | 3.4308 | 1.059x |
| 19297 | 3.6262 | 3.4437 | 1.053x |
| 19328 | 3.6227 | 3.4420 | 1.052x |
| 24384 | 4.6232 | 4.4102 | 1.048x |
| 27488 | 5.1404 | 4.9056 | 1.048x |
| 29472 | 5.5007 | 5.2554 | 1.047x |
| 33472 | 6.1970 | 5.9385 | 1.044x |
| 37120 | 7.1282 | 6.7252 | 1.060x |
| 38528 | 7.2220 | 6.8739 | 1.051x |
| 38591 | 7.2228 | 6.8827 | 1.049x |
| 38592 | 7.1977 | 6.8791 | 1.046x |
| 38593 | 7.3943 | 6.9679 | 1.061x |
| 38656 | 7.3863 | 6.9621 | 1.061x |
| 48768 | 9.1521 | 8.7261 | 1.049x |
| 54976 | 10.2084 | 9.8533 | 1.036x |
| 58944 | 11.1218 | 10.6389 | 1.045x |
| 74240 | 13.9364 | 13.3549 | 1.044x |
| 109952 | 20.5279 | 19.8661 | 1.033x |

The other Cake variants of this block are its BF16 and NVFP4 forms on
sm_100a and sm_103a, which this PR does not change, plus FP8 and NVFP4
quantized MLP blocks for sm_120 (`minimax_h3_mlp_fp8_sm120`,
`minimax_h3_mlp_nvfp4_sm120`), so the family ships on sm_100a, sm_103a
and sm_120.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* MXFP8 MLPs now support two FC1 scale-tile layouts, with matching
outputs across both options.
* **Bug Fixes**
* Unsupported MXFP8 scale-tile sizes are rejected with an error that
lists the supported sizes and preparation methods.
* BF16 MLP launches now handle partial work waves with adjusted
scheduling.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c4b6ec9](https://github.com/flashinfer-ai/flashinfer/commit/c4b6ec9e36b241f1298eef13a2ddedec7b1390d5)

- **作者**: eigen
- **时间**: 2026-10-25T09:31:54Z
- **提交信息**: perf(cake_sage): faster SM120 block-sparse Sage attention (#7303)

The block-sparse Sage attention forward for SM120 (RTX PRO 6000 / RTX
5090), `flashinfer.cute_dsl.sparse.bsa_attn_sm120_blk64_sage_fwd(...,
backend="cake")`, takes prequantized INT8 Q and K, with QK^T on INT8
`mma.sync`, and FP8 (e4m3) V for the PV product. It produces BF16 output
with head dim 128, uses 64-token Q and KV blocks, is non-causal, and
takes a list of selected KV blocks for each Q block. One CUDA source is
specialized into 20 programs by five metadata flags: whether per-row KV
block counts are given, the block-size mask mode, whether every KV tile
is a full 64-token tile, whether every row selects the same non-zero
number of blocks, and whether the selected block indices are contiguous.
The host picks the specialization on each call. This PR regenerates that
source for all 20 specializations, with bitwise-identical outputs, and
on sm_120a it is 1.0047x to 1.0169x faster on all 8 shapes than the
previous Cake version (the `backend="cake"` path on main, shown as the
baseline below).

| batch | heads | seq len | selected KV blocks / all | baseline (ms) |
this PR (ms) | speedup | 95% CI |
|---:|---:|---:|---:|---:|---:|---:|---|
| 8 | 32 | 1024 | 15 / 16 | 0.2228 | 0.2194 | 1.0152x | 1.0136x -
1.0168x |
| 8 | 32 | 2048 | 16 / 32 | 0.4454 | 0.4381 | 1.0169x | 1.0164x -
1.0175x |
| 8 | 32 | 4096 | 7 / 64 | 0.4805 | 0.4782 | 1.0047x | 1.0038x - 1.0056x
|
| 8 | 32 | 8192 | 116 / 128 | 11.2617 | 11.1451 | 1.0104x | 1.0103x -
1.0104x |
| 8 | 32 | 16384 | 128 / 256 | 25.1041 | 24.8752 | 1.0093x | 1.0090x -
1.0095x |
| 8 | 32 | 32768 | 52 / 512 | 20.7371 | 20.5251 | 1.0103x | 1.0102x -
1.0104x |
| 4 | 32 | 65536 | 512 / 1024 | 217.4434 | 215.5313 | 1.0101x | 1.0091x
- 1.0111x |
| 4 | 32 | 65536 | 103 / 1024 | 40.4100 | 40.0211 | 1.0097x | 1.0096x -
1.0098x |

*NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120a, 188 SMs); CUDA
13.0 runtime; programs compiled with nvcc 13.4. Q, K and V are [batch,
heads, seq len, 128]. "Selected KV blocks / all" is the number of KV
blocks each 64-row Q block attends to, out of all KV blocks. The two seq
len 65536 rows use batch 4 because batch 8 exceeds the API's
2^31-element limit. Latency is the median of single cold-L2 calls. Each
side ran in its own process, with calls interleaved between the two
processes. Speedup is the reciprocal of the mean of 8 per-group
new/previous time ratios, shown with its 95% CI.*

The same Cake package also ships the Sage-FP8 block-sparse attention
forward (FP8 Q/K/V on tcgen05) and its fused FP8 quantizer for sm_100a
and sm_103a (B200, B300/GB300), and with this PR the SM120
INT8-QK/FP8-PV form stays on sm_120a, so the family covers sm_100a,
sm_103a and sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Refreshed build metadata for selected GPU artifacts. Build
configurations, supported architectures, and artifact availability
remain unchanged.
  * No user-visible functionality changes are included in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0e406f3](https://github.com/flashinfer-ai/flashinfer/commit/0e406f333bda4cb7312519895253b5a1f158e09e)

- **作者**: Yang Xu
- **时间**: 2026-10-25T09:30:21Z
- **提交信息**: feat(moe): extend grouped Frost decode to SM80 and typed activations (#7204)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extend the opt-in Frost low-latency backend with an Ampere SM80
projection using CUTLASS cp.async and warp MMA, and broaden the existing
Hopper/SM120 grouped paths to qualified FP16 and activation
combinations. The runtime discovers matching expert routes from live
inputs and shares original weights, typed intermediates, activation
lowering and ordered FP32 combine with the existing implementation.

| Architecture | Grouped candidate coverage |
|---|---|
| SM80 | BF16/FP16 default SwiGLU and ReLU2, H2048/I512/top-k10, T4/T8;
additionally BF16 default SwiGLU, H7168/I2048/top-k8, T4/T8 |
| SM90 | BF16/FP16 default SwiGLU and GeGLU at T4/T8; ReLU2/SiLU at T8;
H2048/I512/top-k10 |
| SM120 | BF16/FP16 default SwiGLU, GeGLU, ReLU2 and SiLU at T4/T8;
H2048/I512/top-k10 |

Grouped candidates require matching input/weight/output dtypes and
finalized output. SM80 also gains the existing BF16/FP16 FMA path;
quantized formats remain unsupported there. All 16 FMA choices and the
untuned FMA default remain. The backend remains opt-in; callers set
`FrostLowLatencyConfig(max_num_tokens=8)` and tune representative
routes/cache conditions. Tuning-domain identities change to avoid
reusing records from the older candidate sets.

The Ampere pipeline is adapted from the NVIDIA CUTLASS CuTe DSL example,
retaining its license notice. It stages original up/gate slices with
128-bit cp.async, uses a free-slot pipeline and drains asynchronous
readers before reusing shared storage for the epilogue. Weight alignment
is checked before compilation. Live pointers and streams are rebound per
call; route values never enter compile keys.

The benchmark adds native FP16 CUTLASS and a pinned, hash-checked
standalone vLLM device-function comparator for SM80. It preserves
separate rounding references and labels the latter as a standalone
kernel harness. The measured scope is the full
FC1/activation/FC2/combine GPU interval, with precomputed routing; it is
not model or serving throughput. The docs include runnable commands and
comparison boundaries.

## 🔍 Related Issues

Builds on merged #7194. Continues the Frost low-latency coverage work
from #6626.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] Scoped `pre-commit run --files <changed files>` passes for all 12
changed files.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted native GPU qualification completed; details below.

The combined source was checked on all three target architectures using
CuTe DSL 4.8:

- SM80:210 passed, 1 expected skip.
- SM90:197 passed, 14 expected skips.
- SM120:197 passed, 14 expected skips.

The SM90/SM120 skips are 13 SM80-only cases and one existing SM10x-only
case. The SM80 skip is the SM10x-only case. Before integration, the new
Ampere typed/large-shape cohorts and Hopper/SM120 activation cohorts
each passed memcheck, racecheck and synccheck with zero errors/hazards.
The integrated branch reruns the full grouped-TC/BF16/FP16 suites and
paired controls using its public reproducer. Source/import paths were
verified for each immutable snapshot; no tolerance was relaxed.

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

Please focus on Ampere stage ownership/alignment and the
architecture/dtype/activation admission boundaries. Tests cover live
CUDA Graph inputs, changing routes/scores, poisoned buffers, invalid
NaN/Inf routing scores, independent streams, mixed output and negative
admission cases.

The repo CI may use CuTe DSL older than4.8 and skip these kernels; green
skipped tests are not counted as GPU execution evidence. Native DSL 4.8
qualification is reported separately. Route reuse/cache state influence
the winning family, so this is a bounded tuning extension, not
unconditional token-count dispatch.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Frost low-latency MoE now supports selected grouped Tensor Core
workloads on SM80, including BF16 and FP16 with qualified activations
and shapes.
* Added Ampere-optimized grouped projection tactics and expanded
supported workload coverage across SM80, SM90, and SM120.
* The benchmark now compares configurable workloads and data types
across supported baselines.

* **Bug Fixes**
* Improved handling of invalid routes and unsupported workload
configurations in eligible paths.

* **Documentation**
* Expanded guidance on supported architectures, workload coverage, and
benchmarking requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8d9c839](https://github.com/flashinfer-ai/flashinfer/commit/8d9c839db0cb6ca119cbd3e1bf878ce91fc274df)

- **作者**: eigen
- **时间**: 2026-10-25T09:20:26Z
- **提交信息**: feat(cake_tinygemm2_tcgen05): add tcgen05 tinygemm_bf16 programs for sm_100a/103a/107a (#7302)

This PR adds the Cake backend `cake_tinygemm2_tcgen05`, which contains
generated tcgen05 programs for `flashinfer.gemm.tinygemm_bf16` (BF16
`out = input @ weight.T (+ bias)` for small batches). It covers every
variant: BF16 with and without bias, with and without PDL, using narrow,
packed and per-chain-accumulator tiles. That makes 12 programs per
architecture for sm_100a, sm_103a and sm_107a. A shape uses these
programs only inside per-architecture windows where they measured
faster. Other shapes keep their current kernel. The baseline is what the
op runs today: Cake `tinygemm2_sm100` with a bias and FlashInfer
`tinygemm2` without one. The tables below show the speedups.

Times are CUPTI kernel times in µs (median, cold L2) with PDL off.
Speedups marked † fall outside the routing windows and keep their
current kernel, so both columns time the same kernel.

**NVIDIA B200** (sm_100a, 148 SMs), CUDA 13.4, PyTorch 2.14.1+cu130

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.88 / 2.93 | 0.98x † | 3.07 / 3.07 | 1.00x † |
| 1 x 128 x 14336 | 7.58 / 7.58 | 1.00x † | 8.06 / 7.39 | 1.09x |
| 2 x 16 x 256 | 2.86 / 2.85 | 1.01x † | 2.93 / 2.94 | 0.99x † |
| 4 x 2880 x 2880 | 6.78 / 6.78 | 1.00x † | 8.29 / 7.26 | 1.14x |
| 7 x 128 x 4096 | 4.58 / 4.29 | 1.07x | 4.38 / 4.40 | 1.00x † |
| 8 x 128 x 7168 | 5.25 / 5.25 | 1.00x † | 5.46 / 5.18 | 1.05x |
| 8 x 1024 x 1024 | 3.14 / 3.14 | 1.00x † | 3.23 / 3.23 | 1.00x † |
| 13 x 1024 x 2048 | 3.97 / 3.97 | 1.00x † | 4.03 / 4.03 | 1.00x † |
| 16 x 2880 x 2880 | 7.87 / 7.39 | 1.06x | 10.72 / 7.39 | 1.45x |
| 64 x 4096 x 3072 | 21.65 / 10.05 | 2.15x | 38.18 / 9.98 | 3.82x |
| 16 x 1024 x 1024 | 3.10 / 3.10 | 1.00x † | 3.20 / 3.20 | 1.00x † |
| 8 x 2048 x 2048 | 4.77 / 4.77 | 1.00x † | 4.86 / 4.87 | 1.00x † |
| 8 x 4096 x 4096 | 9.63 / 9.63 | 1.00x † | 11.52 / 10.16 | 1.13x |
| 16 x 4096 x 3072 | 9.57 / 8.42 | 1.14x | 14.05 / 8.42 | 1.67x |
| 64 x 4096 x 4096 | 27.68 / 12.42 | 2.23x | 44.86 / 12.37 | 3.63x |
| 4 x 128 x 256 | 2.72 / 2.72 | 1.00x † | 2.91 / 2.91 | 1.00x † |

**NVIDIA GB300** (sm_103a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.75 / 2.75 | 1.00x † | 2.88 / 2.88 | 1.00x † |
| 1 x 128 x 14336 | 7.30 / 7.33 | 1.00x † | 7.81 / 7.23 | 1.08x |
| 2 x 16 x 256 | 2.50 / 2.50 | 1.00x † | 2.67 / 2.67 | 1.00x † |
| 4 x 2880 x 2880 | 6.56 / 6.56 | 1.00x † | 7.84 / 7.17 | 1.09x |
| 7 x 128 x 4096 | 4.32 / 4.06 | 1.06x | 4.06 / 4.08 | 1.00x † |
| 8 x 128 x 7168 | 5.20 / 5.22 | 1.00x † | 5.36 / 5.06 | 1.06x |
| 8 x 1024 x 1024 | 2.98 / 2.98 | 1.00x † | 3.07 / 3.07 | 1.00x † |
| 13 x 1024 x 2048 | 3.87 / 3.87 | 1.00x † | 3.97 / 3.97 | 1.00x † |
| 16 x 2880 x 2880 | 7.55 / 7.07 | 1.07x | 10.27 / 7.07 | 1.45x |
| 64 x 4096 x 3072 | 20.19 / 9.57 | 2.11x | 35.36 / 9.47 | 3.73x |
| 16 x 1024 x 1024 | 2.98 / 2.98 | 1.00x † | 3.07 / 3.07 | 1.00x † |
| 8 x 2048 x 2048 | 4.67 / 4.67 | 1.00x † | 4.74 / 4.74 | 1.00x † |
| 8 x 4096 x 4096 | 9.22 / 9.22 | 1.00x † | 10.85 / 9.57 | 1.13x |
| 16 x 4096 x 3072 | 8.99 / 8.16 | 1.10x | 13.41 / 8.16 | 1.64x |
| 64 x 4096 x 4096 | 25.46 / 11.17 | 2.28x | 41.02 / 11.14 | 3.68x |
| 4 x 128 x 256 | 2.72 / 2.72 | 1.00x † | 2.94 / 2.94 | 1.00x † |

**NVIDIA R200** (sm_107a, 212 SMs), CUDA 13.4, PyTorch 2.14.1+cu130

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.56 / 2.56 | 1.00x † | 2.66 / 2.66 | 1.00x † |
| 1 x 128 x 14336 | 6.18 / 6.18 | 1.00x † | 6.75 / 6.08 | 1.11x |
| 2 x 16 x 256 | 2.24 / 2.22 | 1.01x † | 2.42 / 2.40 | 1.01x † |
| 4 x 2880 x 2880 | 4.93 / 4.93 | 1.00x † | 5.12 / 5.10 | 1.00x † |
| 7 x 128 x 4096 | 3.97 / 3.74 | 1.06x | 3.68 / 3.65 | 1.01x † |
| 8 x 128 x 7168 | 4.38 / 4.38 | 1.00x † | 4.61 / 4.45 | 1.04x |
| 8 x 1024 x 1024 | 2.75 / 2.75 | 1.00x † | 2.85 / 2.85 | 1.00x † |
| 13 x 1024 x 2048 | 3.14 / 3.14 | 1.00x † | 3.30 / 3.30 | 1.00x † |
| 16 x 2880 x 2880 | 5.02 / 4.99 | 1.01x † | 6.53 / 5.47 | 1.19x |
| 64 x 4096 x 3072 | 18.37 / 7.71 | 2.38x | 22.94 / 7.49 | 3.06x |
| 16 x 1024 x 1024 | 2.67 / 2.69 | 0.99x † | 2.78 / 2.75 | 1.01x † |
| 8 x 2048 x 2048 | 3.55 / 3.55 | 1.00x † | 3.68 / 3.68 | 1.00x † |
| 8 x 4096 x 4096 | 5.89 / 5.89 | 1.00x † | 7.47 / 7.46 | 1.00x † |
| 16 x 4096 x 3072 | 8.38 / 8.35 | 1.00x † | 8.86 / 5.79 | 1.53x |
| 64 x 4096 x 4096 | 22.37 / 8.74 | 2.56x | 26.15 / 8.48 | 3.08x |
| 4 x 128 x 256 | 2.46 / 2.43 | 1.01x † | 2.62 / 2.59 | 1.01x † |

Cake has no other data type, layout or fused form of this kernel, and
`tinygemm2_sm100` remains the with-bias path outside the windows. This
family covers sm_100a, sm_103a and sm_107a (B200, GB300 and R200 class
GPUs).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a specialized BF16 matrix-multiplication backend for supported
NVIDIA GPUs, with automatic selection for eligible inputs and fallback
to existing implementations.
* Added support for multiple tile configurations, bias and no-bias
operation, and PDL variants.
* Added input validation for device, data type, layout, dimensions, and
launch parameters.
* **Tests**
* Added coverage for numerical results, backend selection, supported
shapes, bias and PDL settings, and fallback conditions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [9f6ba5a](https://github.com/flashinfer-ai/flashinfer/commit/9f6ba5a820e892c9465ca5c516e6094086c6ff83)

- **作者**: eigen
- **时间**: 2026-10-25T09:01:41Z
- **提交信息**: perf(cake_gdp): preload the dense row in the one-row-per-thread T = 1 decode program on SM100 / SM103 (#7297)

The Cake Gated DeltaProduct decode kernel
(`flashinfer.cake_gdp.cake_gated_delta_product_mtp`) has one variant:
BF16 q / k / v / output with an FP32 recurrent state in a slot-indexed
state pool, float32 `A_log` and `dt_bias`, optional per-token state
scatter, 1 <= T <= 16 tokens per sequence, K = 128, V = 64 and 1 <= n <=
4 Householder sub-steps. This PR delivers that same variant with a
change inside the one-row-per-thread T = 1 decode program on sm_100a /
sm_103a: that program now issues the dense v / beta row loads at the k
load site (the same producer preload the one-wave-of-5 T = 1 program
gained in PR #7201), and its kernel text changes on both architectures.
Its band (B x HV above 5 x and up to 64 x the SM count), the host plan
and the registry are unchanged; the sm_90a build of this program
compiles to identical SASS, and every other program is byte-identical to
the previous package. The baseline is the previous Cake version of this
kernel, the Cake GDP decode package of FlashInfer PR #7201, whose head
is the direct predecessor of this package. Both packages ran in the same
process with paired A/B/B/A kernel-sum timing over 3 groups x 32 samples
per call with cold L2 (a same-binary A/B reference on the same node
spans 0.98-1.04 on GB300 and 0.99-1.03 on B200), and speedup = previous
/ this PR is 0.99-1.07 on GB300 and 0.99-1.06 on B200 across the 48
shapes (HV in {80, 20, 10, 24} x B in {1, 16, 64, 256} x T in {1, 4, 8},
n = 3). The changed program runs on seven T = 1 rows, at 1.00-1.07 on
GB300 and 1.01-1.06 on B200: HV 80 x B 16, HV 80 x B 64, HV 20 x B 64,
HV 20 x B 256, HV 10 x B 256, HV 24 x B 64 and HV 24 x B 256; every
other row runs a byte-identical kernel in both packages.

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4.92 -- 48 rows, speedup
0.99-1.07**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.1 | 4.1 | 1.00 |
| 80 | 1 | 4 | 6.1 | 6.1 | 1.00 |
| 80 | 1 | 8 | 8.2 | 8.1 | 1.01 |
| 80 | 16 | 1 | 16.8 | 16.4 | 1.03 |
| 80 | 16 | 4 | 25.0 | 24.9 | 1.00 |
| 80 | 16 | 8 | 40.2 | 40.1 | 1.00 |
| 80 | 64 | 1 | 53.2 | 52.7 | 1.01 |
| 80 | 64 | 4 | 76.2 | 76.1 | 1.00 |
| 80 | 64 | 8 | 131.4 | 131.4 | 1.00 |
| 80 | 256 | 1 | 198.3 | 198.6 | 1.00 |
| 80 | 256 | 4 | 282.1 | 282.1 | 1.00 |
| 80 | 256 | 8 | 499.8 | 499.9 | 1.00 |
| 20 | 1 | 1 | 3.3 | 3.3 | 1.00 |
| 20 | 1 | 4 | 5.5 | 5.6 | 0.99 |
| 20 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 20 | 16 | 1 | 7.3 | 7.2 | 1.01 |
| 20 | 16 | 4 | 11.0 | 11.1 | 0.99 |
| 20 | 16 | 8 | 16.7 | 16.7 | 1.00 |
| 20 | 64 | 1 | 17.3 | 16.2 | 1.07 |
| 20 | 64 | 4 | 24.8 | 24.7 | 1.00 |
| 20 | 64 | 8 | 40.1 | 40.1 | 1.00 |
| 20 | 256 | 1 | 53.0 | 52.7 | 1.00 |
| 20 | 256 | 4 | 76.2 | 76.3 | 1.00 |
| 20 | 256 | 8 | 131.4 | 131.4 | 1.00 |
| 10 | 1 | 1 | 3.2 | 3.2 | 1.00 |
| 10 | 1 | 4 | 5.5 | 5.5 | 1.00 |
| 10 | 1 | 8 | 7.5 | 7.5 | 1.00 |
| 10 | 16 | 1 | 5.2 | 5.1 | 1.02 |
| 10 | 16 | 4 | 8.3 | 8.2 | 1.01 |
| 10 | 16 | 8 | 12.1 | 12.1 | 1.00 |
| 10 | 64 | 1 | 10.7 | 10.6 | 1.00 |
| 10 | 64 | 4 | 16.2 | 16.1 | 1.00 |
| 10 | 64 | 8 | 25.1 | 25.3 | 0.99 |
| 10 | 256 | 1 | 29.2 | 28.8 | 1.01 |
| 10 | 256 | 4 | 41.6 | 41.7 | 1.00 |
| 10 | 256 | 8 | 69.6 | 69.7 | 1.00 |
| 24 | 1 | 1 | 3.3 | 3.3 | 1.00 |
| 24 | 1 | 4 | 5.6 | 5.6 | 1.00 |
| 24 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 24 | 16 | 1 | 7.6 | 7.6 | 1.00 |
| 24 | 16 | 4 | 11.6 | 11.5 | 1.00 |
| 24 | 16 | 8 | 17.6 | 17.4 | 1.03 |
| 24 | 64 | 1 | 19.7 | 18.4 | 1.07 |
| 24 | 64 | 4 | 28.4 | 28.5 | 0.99 |
| 24 | 64 | 8 | 47.0 | 47.1 | 1.00 |
| 24 | 256 | 1 | 63.0 | 62.5 | 1.01 |
| 24 | 256 | 4 | 90.0 | 90.2 | 1.00 |
| 24 | 256 | 8 | 156.4 | 156.4 | 1.00 |

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4.92 -- 48 rows, speedup
0.99-1.06**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.2 | 4.3 | 1.00 |
| 80 | 1 | 4 | 6.4 | 6.4 | 1.00 |
| 80 | 1 | 8 | 8.6 | 8.6 | 1.00 |
| 80 | 16 | 1 | 17.6 | 17.0 | 1.03 |
| 80 | 16 | 4 | 26.4 | 26.6 | 1.00 |
| 80 | 16 | 8 | 43.5 | 43.5 | 1.00 |
| 80 | 64 | 1 | 54.9 | 54.3 | 1.01 |
| 80 | 64 | 4 | 83.2 | 83.1 | 1.00 |
| 80 | 64 | 8 | 144.5 | 144.6 | 1.00 |
| 80 | 256 | 1 | 205.1 | 205.4 | 1.00 |
| 80 | 256 | 4 | 305.6 | 305.5 | 1.00 |
| 80 | 256 | 8 | 543.4 | 543.3 | 1.00 |
| 20 | 1 | 1 | 3.4 | 3.4 | 1.00 |
| 20 | 1 | 4 | 5.8 | 5.8 | 0.99 |
| 20 | 1 | 8 | 8.0 | 8.1 | 0.99 |
| 20 | 16 | 1 | 7.6 | 7.6 | 1.00 |
| 20 | 16 | 4 | 11.6 | 11.6 | 1.00 |
| 20 | 16 | 8 | 17.9 | 17.9 | 1.00 |
| 20 | 64 | 1 | 17.9 | 17.1 | 1.05 |
| 20 | 64 | 4 | 26.6 | 26.7 | 0.99 |
| 20 | 64 | 8 | 43.5 | 43.5 | 1.00 |
| 20 | 256 | 1 | 54.9 | 54.1 | 1.02 |
| 20 | 256 | 4 | 83.2 | 83.4 | 1.00 |
| 20 | 256 | 8 | 144.4 | 144.5 | 1.00 |
| 10 | 1 | 1 | 3.3 | 3.3 | 1.00 |
| 10 | 1 | 4 | 5.7 | 5.7 | 1.00 |
| 10 | 1 | 8 | 8.0 | 8.0 | 1.00 |
| 10 | 16 | 1 | 5.4 | 5.2 | 1.02 |
| 10 | 16 | 4 | 8.5 | 8.5 | 1.01 |
| 10 | 16 | 8 | 12.7 | 12.7 | 1.00 |
| 10 | 64 | 1 | 10.9 | 10.8 | 1.01 |
| 10 | 64 | 4 | 17.2 | 17.1 | 1.01 |
| 10 | 64 | 8 | 27.4 | 27.3 | 1.00 |
| 10 | 256 | 1 | 30.6 | 29.8 | 1.03 |
| 10 | 256 | 4 | 45.7 | 45.7 | 1.00 |
| 10 | 256 | 8 | 78.2 | 78.2 | 1.00 |
| 24 | 1 | 1 | 3.4 | 3.5 | 0.99 |
| 24 | 1 | 4 | 5.8 | 5.8 | 1.00 |
| 24 | 1 | 8 | 8.1 | 8.1 | 1.00 |
| 24 | 16 | 1 | 8.0 | 7.9 | 1.00 |
| 24 | 16 | 4 | 12.1 | 12.2 | 0.99 |
| 24 | 16 | 8 | 18.5 | 18.5 | 1.00 |
| 24 | 64 | 1 | 20.4 | 19.2 | 1.06 |
| 24 | 64 | 4 | 30.4 | 30.6 | 1.00 |
| 24 | 64 | 8 | 51.1 | 51.1 | 1.00 |
| 24 | 256 | 1 | 64.8 | 64.3 | 1.01 |
| 24 | 256 | 4 | 98.2 | 98.4 | 1.00 |
| 24 | 256 | 8 | 171.3 | 171.2 | 1.00 |

This variant is the kernel family's only data-type form; Cake ships it
on sm_90a (H100 / H200), sm_100a (B200 / GB200) and sm_103a (B300 /
GB300), and the T = 1 kernel change in this PR takes effect on sm_100a /
sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Updated execution paths for non-SM90 GPUs, including input loading,
normalization, and state updates. SM90 behavior remains unchanged.
* Refreshed backend build metadata for SM90, SM100, and SM103 GPU
architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4d018bc](https://github.com/flashinfer-ai/flashinfer/commit/4d018bcd125c6e71d0535296008eaeb62b28834a)

- **作者**: eigen
- **时间**: 2026-10-25T09:01:29Z
- **提交信息**: fix(cake_batch_deepgemm_fp8): use an even n_l2_group on the K=7168 expected_m<=1 serving route (#7296)

For `K == 7168` and `expected_m <= 1`, `serving_config()` picked
`n_l2_group=1` on the packed UE8M0 serving route
(`seed_serving_m32_packed`, used by
`batch_deepgemm_fp8_nt_groupwise(..., backend="cake")`). With that
setting, any group with more than 32 rows produces wrong output rows.
This PR switches that case to already-shipped programs with
`n_l2_group=8`, which fixes the output on B200 and GB300 and costs up to
about 6 % on the frozen expected_m=1 serving rows.

## Root cause

The two CTAs of a cluster take consecutive tile indices and must share
one 32-row M block. Each CTA loads half of A at `off_m + cta_rank *
load_block_m`. With `n_l2_group=1`, `m_block = block_idx % m_blocks_g`.
In any group with more than one M block (more than 32 rows), the pair
mixes two M blocks and those rows are wrong. `expected_m` is only a host
hint, so such a group can reach this route at `expected_m=1`, for
example with many experts and a small batch.

Reproduction on unmodified `main` with the public API, packed UE8M0
scales, M=256, `expected_m=1`, N=4096, K=7168. All other groups have 0–4
rows. Each cell shows bad elements / valid elements (max abs error):

| Mask | GB300, 32 groups | GB300, 64 groups | B200, 32 groups | B200,
64 groups |
|---|---|---|---|---|
| one 40-row group | 97,355 / 413,696 (575) | 97,297 / 671,744 (574) |
97,347 / 413,696 (646) | 97,294 / 671,744 (596) |
| one 33-row group | 68,950 / 385,024 (575) | 68,888 / 643,072 (512) |
68,947 / 385,024 (646) | 68,921 / 643,072 (596) |
| groups of 256/100/65 rows | 894,598 / 1,982,464 (605) | 894,486 /
2,265,088 (667) | 894,252 / 1,982,464 (588) | 894,484 / 2,265,088 (668)
|

These controls are correct:
- The same masks at `expected_m=2`, which uses the `n_l2_group=8`
programs.
- Every N=7168, K=2048 case.
- On the old config, any mask where every group has ≤ 4 rows.

## Fix

In `flashinfer/gemm/cake_batch_deepgemm_fp8.py`, `serving_config()` now
returns `(5, 2, "evict_normal", 0, 8)` instead of `(6, 1,
"evict_normal", 0, 1)` for `k == 7168 and expected_m <= 1`. The
docstring gains 5 lines explaining why `n_l2_group` must be even.

| Groups | Old program | New program |
|---|---|---|
| 32 | `1602ca00` | `1405732a` |
| 64 | `364ce5d1` | `ce9db474` |

The new programs already ship and are the same ones the expected_m 2–3
configuration uses, but here they run with cta_reserve 0. With the fix,
every reproduction case above is correct. On the frozen serving rows and
the small-mask cases (every group ≤ 4 rows), the output is bitwise
identical to the old programs.

## Tests

The new test
`test_packed_serving_expected_m_one_with_multi_block_groups` in
`tests/gemm/test_cake_batch_deepgemm_fp8_nt_groupwise.py`:
- Is parametrized over both packed (N, K) shapes and both packed group
counts.
- Uses M=256 and `expected_m=1`. Groups 9 and 20 hold 40 and 33 rows;
every other group `g` holds `g % 5` rows.
- Asserts that the route is `seed_serving_m32_packed`, then compares the
public API against the FP32 reference on valid rows. N=7168, K=2048 is
the control.

Results for the whole test file:

| | B200 (sm_100a, 148 SMs) | GB300 (sm_103a, 152 SMs) |
|---|---|---|
| unmodified `main` + new test | 2 failed, 35 passed | 2 failed, 35
passed |
| this PR | 37 passed | 37 passed |

The two failures on `main` are the N=4096, K=7168 cases (32 and 64
groups). `ruff check` and `ruff format --check` (0.12.8) pass on both
changed files.

## Performance

This is a correctness fix, and it costs up to about 6 % on these rows. A
dedicated `n_l2_group=2` program for this route could recover the cost
in a follow-up.

Frozen expected_m=1 serving rows, in µs (median of 3 runs, CUPTI, cold
L2). In each row the old and new programs read the same input and
`masked_m` tensors and write the same output buffer. Noise is the
largest deviation from 1.0 over the three runs of an A/A pair and of a
second instance of the old program, in both orders. Outputs are bitwise
equal to the old programs. Ratio is the median of the three per-run
paired ratios, so it can differ slightly from the ratio of the two µs
columns.

| Row | GB300 old | GB300 new | Ratio (noise) | B200 old | B200 new |
Ratio (noise) |
|---|---|---|---|---|---|---|
| p10 b64 | 17.80 | 18.33 | 1.026 (0.006) | 18.18 | 18.90 | 1.038
(0.004) |
| p50 b64 | 30.12 | 31.36 | 1.059 (0.006) | 30.62 | 32.27 | 1.054
(0.005) |
| p90 b64 | 58.79 | 59.04 | 1.004 (0.002) | 59.52 | 59.90 | 1.006
(0.002) |
| p10 b32 | 4.97 | 4.97 | 1.000 (0.001) | 5.29 | 5.31 | 1.004 (0.005) |
| p50 b32 | 18.48 | 18.69 | 1.014 (0.004) | 18.74 | 19.06 | 1.012
(0.004) |
| p90 b32 | 38.00 | 38.20 | 1.005 (0.002) | 38.51 | 38.84 | 1.009
(0.003) |

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a6af6da](https://github.com/flashinfer-ai/flashinfer/commit/a6af6da1781d76fffc31fb73f2c77a21daf8a85e)

- **作者**: eigen
- **时间**: 2026-10-25T08:59:25Z
- **提交信息**: perf(cake_dsa_indexer): 32768-slot candidate buffers for short units on sm_103a and a re-tuned register split in the sm_103a wide scan programs (#7295)

This PR speeds up the Cake DSA indexer top-k scan behind
`flashinfer.dsa_indexer.dsa_indexer_topk`. The kernel has only one
data-type variant, with BF16 queries and keys and FP32 head weights and
scores. All changes are on sm_103a. The host plan now gives short units
a 32768-slot candidate buffer (candidate multiplier 16 with a 32768
ceiling, where it used the 16384 floor before), so they compact less
often. Long units and `sample_tiles_max=0` calls are unchanged. The
sampled-first-threshold scan program is now selected only where the
architecture ships it. Two wide scan programs are re-rendered. The
sampled wide program moves to a 232/40 register split between its math
and load warpgroups. It also drops the register-usage-level compile
hint, which on this hardware had rematerialized a staged-weight base
before every weight load. The no-sample-fit wide program keeps its
224/56 split and the hint. It now probes the next tile's completion
right after releasing the current accumulator stage. It also issues one
elected, aggregated arrive on the accumulator-empty barrier per warp and
tile instead of one per thread. On GB300 the no-sample-fit wide program
serves Z1k256, S7 and S8, and the sampled wide program serves V2. The
trade is a larger persistent workspace for calls whose short units now
get 32768 slots. On a 152-SM GB300 it grows from 114 MiB to 228 MiB on
the sampled path at `top_k` 2048 and 4096. Workspace is unchanged for
calls that keep 16384 slots and for `sample_tiles_max=0` calls. The
baseline is the previous Cake version of this kernel, the package merged
in #7187. Against it, the speedup on GB300 is 1.04x on P1sink, 1.02x on
Z3cp and S4sink, and 1.01x on Z3, Z1k256, S7, S8 and S4_peaked. All
other rows are 1.00x. No row is slower beyond the A/A band of the paired
measurement, and output is bit-identical on every shape.

Speedup on GB300:

GB300 (NVIDIA GB300, sm_103a, CUDA 13.4); ms = median of the two
arm-order processes of the CUPTI kernel time; speedup = previous / this
PR.

| row | shape | T (queries) | Tkv (keys) | segments | top-k | previous
Cake kernel ms | this PR ms | speedup |
|---|---|---|---|---|---|---|---|---|
| Z1 | #7042 repro: 262k document, CP16 zigzag rank 0 | 16384 | 270336 |
2 | 2048 | 11.819 | 11.821 | 1.00x |
| Z1k4096 | Z1 with top-k 4096 | 16384 | 270336 | 2 | 4096 | 15.210 |
15.209 | 1.00x |
| Z1k256 | Z1 with top-k 256 | 16384 | 270336 | 2 | 256 | 11.286 |
11.217 | 1.01x |
| Z2 | 8 x 32k documents, full causal | 262144 | 262144 | 8 | 2048 |
30.599 | 30.590 | 1.00x |
| Z2cp | 8 x 32k documents, CP16 zigzag rank 0 | 16384 | 270336 | 16 |
2048 | 1.884 | 1.884 | 1.00x |
| Z3 | packed 4k-64k documents, full causal | 169984 | 169984 | 8 | 2048
| 22.695 | 22.520 | 1.01x |
| Z3cp | packed 4k-64k documents, CP16 zigzag rank 0 | 10624 | 175296 |
16 | 2048 | 1.516 | 1.482 | 1.02x |
| P1sink | recorded P1 geometry with sink statistics | 16231 | 268757 |
8 | 2048 | 3.530 | 3.391 | 1.04x |
| S4sink | one 64k causal document, sink statistics | 65536 | 65536 | 1
| 2048 | 14.355 | 14.020 | 1.02x |
| S6sink | one 262k causal document, sink statistics | 262144 | 262144 |
1 | 2048 | 192.693 | 192.573 | 1.00x |
| P1 | recorded packed call | 16231 | 268757 | 8 | 2048 | 3.353 | 3.358
| 1.00x |
| P1_peaked | P1 with dominating keys | 16231 | 268757 | 8 | 2048 |
3.361 | 3.361 | 1.00x |
| P2 | second recorded token count, boundaries derived | 16172 | 267520
| 8 | 2048 | 3.354 | 3.361 | 1.00x |
| P3 | P1 with top-k 4096 | 16231 | 268757 | 8 | 4096 | 3.643 | 3.645 |
1.00x |
| S1 | single causal document N = 8192 | 8192 | 8192 | 1 | 2048 | 0.409
| 0.409 | 1.00x |
| S2 | single causal document N = 16384 | 16384 | 16384 | 1 | 2048 |
1.188 | 1.188 | 1.00x |
| S3 | single causal document N = 32768 | 32768 | 32768 | 1 | 2048 |
3.717 | 3.718 | 1.00x |
| S4 | single causal document N = 65536 | 65536 | 65536 | 1 | 2048 |
13.279 | 13.293 | 1.00x |
| S5 | single causal document N = 131072 | 131072 | 131072 | 1 | 2048 |
48.580 | 48.465 | 1.00x |
| S6 | single causal document N = 262144 | 262144 | 262144 | 1 | 2048 |
184.968 | 184.848 | 1.00x |
| S7 | single causal document N = 524288 | 524288 | 524288 | 1 | 2048 |
759.289 | 749.153 | 1.01x |
| S4_peaked | S4 with dominating keys | 65536 | 65536 | 1 | 2048 |
13.250 | 13.175 | 1.01x |
| C1 | CP tail 4096 x 65536 | 4096 | 65536 | 1 | 2048 | 1.545 | 1.544 |
1.00x |
| C2 | CP tail 4096 x 131072 | 4096 | 131072 | 1 | 2048 | 2.909 | 2.912
| 1.00x |
| C3 | packed 8 x (2048 x 32768) | 16384 | 262144 | 8 | 2048 | 3.162 |
3.158 | 1.00x |
| V1 | N = 65536, ratio 2 | 65536 | 32768 | 1 | 2048 | 7.414 | 7.388 |
1.00x |
| V2 | N = 65536, top-k 256 | 65536 | 65536 | 1 | 256 | 12.196 | 12.151
| 1.00x |
| V3 | N = 65536, top-k 4096 | 65536 | 65536 | 1 | 4096 | 14.379 |
14.337 | 1.00x |
| S8 | single causal document N = 1048576 | 1048576 | 1048576 | 1 | 2048
| 3245.010 | 3215.902 | 1.01x |

GB200 is not re-measured in this PR, because the sm_100a programs render
byte-identical machine code and the GB200 dispatch plan is unchanged (0
differing plans on the dense grid).

Cake ships no other variant of this kernel; the family ships on sm_100a
(GB200), sm_103a (GB300) and sm_107a (R200), and only the sm_103a host
plan and the two sm_103a wide programs change in this PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated candidate sizing for sampled queries, including
architecture-specific capacity limits, to better control resource use
while preserving configured minimums.
  * Tuned GPU kernel execution across supported architectures.

* **Bug Fixes**
* Sampled-fit dispatch now applies only to eligible scan types and
fitting workloads, improving selection of the appropriate execution
path.
* Added validation for candidate-capacity settings and sampled-fit
eligibility.

* **Documentation**
* Expanded workspace capacity examples for additional query and hardware
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [c05b4bf](https://github.com/flashinfer-ai/flashinfer/commit/c05b4bf87ccdcf6d3e16c42daacabbcce4849a7e)

- **作者**: eigen
- **时间**: 2026-10-25T08:53:42Z
- **提交信息**: feat(cake_minimax_h3_dense_attention): generated programs for sm_90a, sm_100a, sm_103a, sm_120a and sm_121a (#7291)

The MiniMax-H3 dense self-attention kernel
(`flashinfer.diffusion_ops.minimax_h3_dense_attention`) has one variant:
BF16 Q, K, V and output, 56 heads of head dim 128 ([S, 7168] rows),
non-causal, with FP32 softmax statistics and accumulation. This PR
replaces the previous hand-written Cake source with a generated program
(128-row Q tile, ping-pong schedule). It builds one program per target
for sm_90a, sm_100a, sm_103a, sm_120a and sm_121a, and the host picks
the program from the device's compute capability. On sm_120a, the only
target measured, it is 1.030x to 1.046x faster than the previous Cake
version on every shape.

| S | previous Cake (ms) | this PR (ms) | speedup |
|---|---|---|---|
| 4097 | 1.3018 | 1.2638 | 1.0299x |
| 15493 | 18.0689 | 17.3125 | 1.0405x |
| 17147 | 22.0893 | 21.1716 | 1.0448x |
| 30224 | 69.9804 | 67.4257 | 1.0405x |
| 37804 | 110.1258 | 107.3626 | 1.0389x |
| 41870 | 141.5971 | 137.1580 | 1.0391x |
| 42554 | 148.0890 | 143.0410 | 1.0343x |
| 44208 | 161.8934 | 156.1000 | 1.0340x |
| 52535 | 228.1386 | 218.9494 | 1.0354x |
| 57287 | 277.9732 | 266.2975 | 1.0411x |
| 104060 | 954.8838 | 914.4829 | 1.0422x |
| 108126 | 1033.5490 | 989.9808 | 1.0413x |
| 118793 | 1250.0063 | 1197.5293 | 1.0456x |

*NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120a, 188 SMs); CUDA
13.0 runtime; programs compiled with nvcc 13.4. S is the sequence
length. Q, K, V and O are [S, 56, 128] BF16. Speedup is the median over
8 interleaved groups of the previous/new time ratio; times are pooled
medians.*

FlashInfer already ships other Cake variants of this attention, which
are packed variable-length (varlen) forms: BF16, FP8, and NVFP4 QK with
FP8 or FP4 PV on sm_100a and sm_103a, and NVFP4 QK forms on sm_120a;
with this PR, the dense BF16 program covers sm_90a, sm_100a, sm_103a,
sm_120a and sm_121a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* MiniMax-H3 dense attention now supports additional GPU architectures,
including compute capability 12.1.
* Added APIs to plan attention launches and determine required workspace
size.
  * Added ahead-of-time build support for the attention operation.
* **Bug Fixes**
* Improved validation of tensor alignment, device compatibility, and
launch parameters, with clearer errors for invalid inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [51509a6](https://github.com/flashinfer-ai/flashinfer/commit/51509a65ec77531fd71e860c46d0df5e67fa3e41)

- **作者**: eigen
- **时间**: 2026-10-25T08:50:54Z
- **提交信息**: perf(cake_dense_projection_gemm): whole-tile tile resolve programs for the SM103a 128x256 input-gradient rows (#7283)

The Cake `dense_projection_gemm` kernel takes BF16 inputs with FP32
accumulation and writes BF16 or FP32 output for the fwd, dgrad and wgrad
GEMMs in the nn / kn / kk operand layouts: 115 dense templates (77 with
BF16 output, 38 with FP32 output; 55 nn, 40 kn, 19 kk and one nk; 28 of
them write a transposed output). It also has an FP32 router GEMM through
split-BF16x3 tensor-core emulation in 3 layouts with a fused split
program, for 122 registered programs (119 distinct templates) in all.
This PR delivers two new sm_103a programs for the K-major (kn) BF16
input-gradient rows that use the 128x256 CTA-pair tile with the TMA
epilogue: the whole-tile tile-resolve program with and without the
load-warp prelude form, which the planner selects on sm_103a for
4096→512 (with the prelude form), 5120→512 and kv_a (6144→576). It also
refreshes the kernel's other generated programs: their kernels are
unchanged under refreshed program identities, the host-side launch
checks now evaluate the shape requirements over int64, and the sm_107a
minimum CUDA version is 13.4. The baseline is the previous Cake version
of the kernel, meaning the programs the planner selected for the same
shapes before this PR. The table lists every shape of the owner's shape
list (294 rows); only the BF16-output dgrad rows of 4096→512, 5120→512
and kv_a (6144→576) change program, and every other row runs the same
kernel on both sides.

**NVIDIA GB300 (sm_103a), driver 580.159.03, CUDA 13.4 (nvcc 13.4.92);
node nvl72d411-T17. Cold-L2 CUPTI kernel time, median of 5 alternating
groups × [20] iterations, both sides in the same session. Latency in µs;
speedup = previous version / this PR.**

| shape (K→N) | op | out | T | baseline | baseline µs | this PR µs |
speedup |
|---|---|---|---:|---|---:|---:|---:|
| indexer_q (2048→4096) | dgrad | bf16 | 16172 | previous version |
142.7 | 142.6 | 1.000 |
| indexer_q (2048→4096) | dgrad | bf16 | 16231 | previous version |
142.7 | 142.6 | 1.001 |
| indexer_q (2048→4096) | fwd | bf16 | 16172 | previous version | 140.0
| 140.2 | 0.999 |
| indexer_q (2048→4096) | fwd | bf16 | 16231 | previous version | 140.6
| 140.5 | 1.001 |
| indexer_q (2048→4096) | wgrad | bf16 | 16172 | previous version |
148.2 | 148.0 | 1.001 |
| indexer_q (2048→4096) | wgrad | bf16 | 16231 | previous version |
148.9 | 148.7 | 1.002 |
| indexer_q (2048→4096) | wgrad | f32 | 16172 | previous version | 147.3
| 146.4 | 1.006 |
| indexer_q (2048→4096) | wgrad | f32 | 16231 | previous version | 147.3
| 147.2 | 1.001 |
| shared_down (2048→6144) | dgrad | bf16 | 16172 | previous version |
217.1 | 217.4 | 0.999 |
| shared_down (2048→6144) | dgrad | bf16 | 16231 | previous version |
218.1 | 217.5 | 1.002 |
| shared_down (2048→6144) | dgrad | f32 | 16172 | previous version |
220.0 | 220.8 | 0.996 |
| shared_down (2048→6144) | dgrad | f32 | 16231 | previous version |
219.1 | 219.8 | 0.997 |
| shared_down (2048→6144) | fwd | bf16 | 16172 | previous version |
213.2 | 212.9 | 1.001 |
| shared_down (2048→6144) | fwd | bf16 | 16231 | previous version |
213.0 | 214.0 | 0.996 |
| shared_down (2048→6144) | wgrad | bf16 | 16172 | previous version |
220.6 | 221.2 | 0.997 |
| shared_down (2048→6144) | wgrad | bf16 | 16231 | previous version |
221.2 | 220.3 | 1.004 |
| shared_down (2048→6144) | wgrad | f32 | 16172 | previous version |
221.3 | 222.1 | 0.996 |
| shared_down (2048→6144) | wgrad | f32 | 16231 | previous version |
221.8 | 221.8 | 1.000 |
| q_b (2048→16384) | dgrad | bf16 | 16172 | previous version | 583.3 |
584.9 | 0.997 |
| q_b (2048→16384) | dgrad | bf16 | 16231 | previous version | 583.9 |
582.5 | 1.002 |
| q_b (2048→16384) | dgrad | f32 | 16172 | previous version | 585.1 |
585.2 | 1.000 |
| q_b (2048→16384) | dgrad | f32 | 16231 | previous version | 585.7 |
585.0 | 1.001 |
| q_b (2048→16384) | fwd | bf16 | 16172 | previous version | 557.1 |
556.2 | 1.002 |
| q_b (2048→16384) | fwd | bf16 | 16231 | previous version | 557.6 |
555.8 | 1.003 |
| q_b (2048→16384) | wgrad | bf16 | 16172 | previous version | 572.8 |
573.4 | 0.999 |
| q_b (2048→16384) | wgrad | bf16 | 16231 | previous version | 575.3 |
575.4 | 1.000 |
| q_b (2048→16384) | wgrad | f32 | 16172 | previous version | 580.0 |
576.8 | 1.006 |
| q_b (2048→16384) | wgrad | f32 | 16231 | previous version | 578.5 |
578.9 | 0.999 |
| 4096→32 | dgrad | bf16 | 16231 | previous version | 23.3 | 23.3 |
0.999 |
| 4096→32 | dgrad | bf16 | 16384 | previous version | 23.4 | 23.6 |
0.991 |
| 4096→32 | dgrad | f32 | 16231 | previous version | 43.2 | 43.0 | 1.004
|
| 4096→32 | dgrad | f32 | 16384 | previous version | 43.3 | 43.4 | 0.998
|
| 4096→32 | fwd | bf16 | 16231 | previous version | 26.3 | 26.3 | 1.000
|
| 4096→32 | fwd | bf16 | 16384 | previous version | 25.9 | 25.8 | 1.004
|
| 4096→32 | wgrad | bf16 | 16231 | previous version | 28.2 | 28.3 |
0.997 |
| 4096→32 | wgrad | bf16 | 16384 | previous version | 28.2 | 28.2 |
1.001 |
| 4096→32 | wgrad | f32 | 16231 | previous version | 28.1 | 28.3 | 0.993
|
| 4096→32 | wgrad | f32 | 16384 | previous version | 28.3 | 28.4 | 0.998
|
| 4096→48 | dgrad | bf16 | 16231 | previous version | 23.7 | 23.8 |
0.997 |
| 4096→48 | dgrad | bf16 | 16384 | previous version | 23.8 | 23.8 |
1.000 |
| 4096→48 | dgrad | f32 | 16231 | previous version | 43.5 | 43.6 | 0.998
|
| 4096→48 | dgrad | f32 | 16384 | previous version | 43.8 | 43.9 | 0.998
|
| 4096→48 | fwd | bf16 | 16231 | previous version | 26.2 | 26.3 | 0.999
|
| 4096→48 | fwd | bf16 | 16384 | previous version | 25.9 | 26.0 | 0.998
|
| 4096→48 | wgrad | bf16 | 16231 | previous version | 28.4 | 28.5 |
0.997 |
| 4096→48 | wgrad | bf16 | 16384 | previous version | 28.6 | 28.5 |
1.003 |
| 4096→48 | wgrad | f32 | 16231 | previous version | 28.3 | 28.4 | 0.996
|
| 4096→48 | wgrad | f32 | 16384 | previous version | 29.0 | 28.9 | 1.003
|
| 4096→64 | dgrad | bf16 | 16231 | previous version | 23.5 | 23.4 |
1.003 |
| 4096→64 | dgrad | bf16 | 16384 | previous version | 23.6 | 23.6 |
0.999 |
| 4096→64 | dgrad | f32 | 16231 | previous version | 43.6 | 43.6 | 0.999
|
| 4096→64 | dgrad | f32 | 16384 | previous version | 43.7 | 43.6 | 1.001
|
| 4096→64 | fwd | bf16 | 16231 | previous version | 26.5 | 26.6 | 0.996
|
| 4096→64 | fwd | bf16 | 16384 | previous version | 26.2 | 26.2 | 1.000
|
| 4096→64 | wgrad | bf16 | 16231 | previous version | 28.7 | 28.7 |
1.000 |
| 4096→64 | wgrad | bf16 | 16384 | previous version | 28.5 | 28.5 |
0.999 |
| 4096→64 | wgrad | f32 | 16231 | previous version | 28.7 | 28.6 | 1.006
|
| 4096→64 | wgrad | f32 | 16384 | previous version | 28.5 | 28.5 | 0.998
|
| 4096→128 | dgrad | bf16 | 16231 | previous version | 24.5 | 24.5 |
0.999 |
| 4096→128 | dgrad | bf16 | 16384 | previous version | 24.5 | 24.6 |
0.996 |
| 4096→128 | dgrad | f32 | 16231 | previous version | 45.0 | 45.2 |
0.995 |
| 4096→128 | dgrad | f32 | 16384 | previous version | 45.4 | 45.3 |
1.001 |
| 4096→128 | fwd | bf16 | 16231 | previous version | 27.2 | 27.3 | 0.997
|
| 4096→128 | fwd | bf16 | 16384 | previous version | 26.6 | 26.8 | 0.995
|
| 4096→128 | wgrad | bf16 | 16231 | previous version | 29.4 | 29.4 |
1.001 |
| 4096→128 | wgrad | bf16 | 16384 | previous version | 29.3 | 29.3 |
1.002 |
| 4096→128 | wgrad | f32 | 16231 | previous version | 29.2 | 29.3 |
0.998 |
| 4096→128 | wgrad | f32 | 16384 | previous version | 29.4 | 29.4 |
1.002 |
| 4096→512 | dgrad | bf16 | 16231 | previous version | 43.5 | 43.2 |
1.009 |
| 4096→512 | dgrad | bf16 | 16384 | previous version | 43.6 | 43.2 |
1.009 |
| 4096→512 | dgrad | f32 | 16231 | previous version | 60.7 | 60.8 |
0.998 |
| 4096→512 | dgrad | f32 | 16384 | previous version | 60.7 | 60.4 |
1.004 |
| 4096→512 | fwd | bf16 | 16231 | previous version | 48.6 | 48.4 | 1.004
|
| 4096→512 | fwd | bf16 | 16384 | previous version | 48.4 | 48.3 | 1.002
|
| 4096→512 | wgrad | bf16 | 16231 | previous version | 43.7 | 43.7 |
1.001 |
| 4096→512 | wgrad | bf16 | 16384 | previous version | 43.9 | 44.0 |
0.997 |
| 4096→512 | wgrad | f32 | 16231 | previous version | 43.6 | 43.6 |
1.000 |
| 4096→512 | wgrad | f32 | 16384 | previous version | 43.9 | 44.0 |
0.998 |
| 4096→1024 | dgrad | bf16 | 16231 | previous version | 75.7 | 75.2 |
1.007 |
| 4096→1024 | dgrad | bf16 | 16384 | previous version | 76.1 | 76.0 |
1.001 |
| 4096→1024 | fwd | bf16 | 16231 | previous version | 76.1 | 75.8 |
1.004 |
| 4096→1024 | fwd | bf16 | 16384 | previous version | 75.7 | 75.4 |
1.004 |
| 4096→1024 | wgrad | bf16 | 16231 | previous version | 74.2 | 74.4 |
0.996 |
| 4096→1024 | wgrad | bf16 | 16384 | previous version | 75.0 | 75.0 |
1.000 |
| 4096→1024 | wgrad | f32 | 16231 | previous version | 76.4 | 76.2 |
1.002 |
| 4096→1024 | wgrad | f32 | 16384 | previous version | 77.0 | 76.6 |
1.005 |
| 4096→4096 | dgrad | bf16 | 16231 | previous version | 275.1 | 273.9 |
1.004 |
| 4096→4096 | dgrad | bf16 | 16384 | previous version | 275.0 | 275.4 |
0.999 |
| 4096→4096 | fwd | bf16 | 16231 | previous version | 273.1 | 274.0 |
0.996 |
| 4096→4096 | fwd | bf16 | 16384 | previous version | 273.5 | 273.6 |
0.999 |
| 4096→4096 | wgrad | bf16 | 16231 | previous version | 283.5 | 283.0 |
1.002 |
| 4096→4096 | wgrad | bf16 | 16384 | previous version | 285.7 | 285.7 |
1.000 |
| 4096→4096 | wgrad | f32 | 16231 | previous version | 288.2 | 287.7 |
1.002 |
| 4096→4096 | wgrad | f32 | 16384 | previous version | 290.5 | 290.8 |
0.999 |
| 4096→12288 | dgrad | bf16 | 16231 | previous version | 844.5 | 844.5 |
1.000 |
| 4096→12288 | dgrad | bf16 | 16384 | previous version | 850.3 | 851.5 |
0.999 |
| 4096→12288 | fwd | bf16 | 16231 | previous version | 820.0 | 818.3 |
1.002 |
| 4096→12288 | fwd | bf16 | 16384 | previous version | 820.5 | 824.5 |
0.995 |
| 4096→12288 | wgrad | bf16 | 16231 | previous version | 842.6 | 849.8 |
0.992 |
| 4096→12288 | wgrad | bf16 | 16384 | previous version | 856.3 | 860.8 |
0.995 |
| 4096→12288 | wgrad | f32 | 16231 | previous version | 861.9 | 848.5 |
1.016 |
| 4096→12288 | wgrad | f32 | 16384 | previous version | 849.3 | 848.0 |
1.002 |
| 5120→32 | dgrad | bf16 | 16231 | previous version | 28.7 | 27.7 |
1.039 |
| 5120→32 | dgrad | bf16 | 16384 | previous version | 27.7 | 27.7 |
1.001 |
| 5120→32 | dgrad | f32 | 16231 | previous version | 51.6 | 51.8 | 0.996
|
| 5120→32 | dgrad | f32 | 16384 | previous version | 52.1 | 52.0 | 1.001
|
| 5120→32 | fwd | bf16 | 16231 | previous version | 30.9 | 30.7 | 1.005
|
| 5120→32 | fwd | bf16 | 16384 | previous version | 31.8 | 31.8 | 0.999
|
| 5120→32 | wgrad | bf16 | 16231 | previous version | 34.0 | 33.9 |
1.004 |
| 5120→32 | wgrad | bf16 | 16384 | previous version | 34.2 | 34.2 |
0.998 |
| 5120→32 | wgrad | f32 | 16231 | previous version | 34.0 | 33.9 | 1.002
|
| 5120→32 | wgrad | f32 | 16384 | previous version | 34.3 | 34.2 | 1.004
|
| 5120→48 | dgrad | bf16 | 16231 | previous version | 28.0 | 28.0 |
1.002 |
| 5120→48 | dgrad | bf16 | 16384 | previous version | 28.0 | 28.1 |
0.999 |
| 5120→48 | dgrad | f32 | 16231 | previous version | 52.3 | 52.1 | 1.005
|
| 5120→48 | dgrad | f32 | 16384 | previous version | 52.3 | 52.5 | 0.997
|
| 5120→48 | fwd | bf16 | 16231 | previous version | 30.9 | 30.9 | 1.001
|
| 5120→48 | fwd | bf16 | 16384 | previous version | 31.9 | 31.9 | 1.002
|
| 5120→48 | wgrad | bf16 | 16231 | previous version | 34.3 | 34.3 |
1.000 |
| 5120→48 | wgrad | bf16 | 16384 | previous version | 34.6 | 34.5 |
1.004 |
| 5120→48 | wgrad | f32 | 16231 | previous version | 34.4 | 34.4 | 1.000
|
| 5120→48 | wgrad | f32 | 16384 | previous version | 34.5 | 34.5 | 1.000
|
| 5120→64 | dgrad | bf16 | 16231 | previous version | 28.1 | 28.0 |
1.003 |
| 5120→64 | dgrad | bf16 | 16384 | previous version | 28.2 | 28.3 |
0.995 |
| 5120→64 | dgrad | f32 | 16231 | previous version | 52.5 | 52.4 | 1.002
|
| 5120→64 | dgrad | f32 | 16384 | previous version | 52.7 | 52.7 | 1.001
|
| 5120→64 | fwd | bf16 | 16231 | previous version | 31.4 | 31.4 | 0.999
|
| 5120→64 | fwd | bf16 | 16384 | previous version | 32.2 | 32.2 | 1.000
|
| 5120→64 | wgrad | bf16 | 16231 | previous version | 34.5 | 34.5 |
1.000 |
| 5120→64 | wgrad | bf16 | 16384 | previous version | 34.5 | 34.5 |
1.000 |
| 5120→64 | wgrad | f32 | 16231 | previous version | 34.3 | 34.6 | 0.992
|
| 5120→64 | wgrad | f32 | 16384 | previous version | 34.5 | 34.6 | 0.996
|
| 5120→128 | dgrad | bf16 | 16231 | previous version | 29.3 | 29.2 |
1.002 |
| 5120→128 | dgrad | bf16 | 16384 | previous version | 29.3 | 29.3 |
1.001 |
| 5120→128 | dgrad | f32 | 16231 | previous version | 54.6 | 54.6 |
1.000 |
| 5120→128 | dgrad | f32 | 16384 | previous version | 54.8 | 54.7 |
1.001 |
| 5120→128 | fwd | bf16 | 16231 | previous version | 32.6 | 32.7 | 0.998
|
| 5120→128 | fwd | bf16 | 16384 | previous version | 32.4 | 32.4 | 1.002
|
| 5120→128 | wgrad | bf16 | 16231 | previous version | 35.7 | 35.6 |
1.000 |
| 5120→128 | wgrad | bf16 | 16384 | previous version | 36.3 | 36.1 |
1.003 |
| 5120→128 | wgrad | f32 | 16231 | previous version | 35.6 | 35.6 |
0.998 |
| 5120→128 | wgrad | f32 | 16384 | previous version | 36.2 | 36.0 |
1.004 |
| 5120→512 | dgrad | bf16 | 16231 | previous version | 55.3 | 54.4 |
1.015 |
| 5120→512 | dgrad | bf16 | 16384 | previous version | 55.4 | 54.7 |
1.013 |
| 5120→512 | dgrad | f32 | 16231 | previous version | 74.0 | 74.4 |
0.994 |
| 5120→512 | dgrad | f32 | 16384 | previous version | 74.4 | 74.9 |
0.994 |
| 5120→512 | fwd | bf16 | 16231 | previous version | 58.5 | 58.3 | 1.004
|
| 5120→512 | fwd | bf16 | 16384 | previous version | 58.5 | 58.5 | 1.001
|
| 5120→512 | wgrad | bf16 | 16231 | previous version | 53.4 | 53.8 |
0.993 |
| 5120→512 | wgrad | bf16 | 16384 | previous version | 53.8 | 54.2 |
0.994 |
| 5120→512 | wgrad | f32 | 16231 | previous version | 55.6 | 55.5 |
1.001 |
| 5120→512 | wgrad | f32 | 16384 | previous version | 55.4 | 55.2 |
1.004 |
| 5120→1024 | dgrad | bf16 | 16231 | previous version | 94.2 | 94.2 |
1.000 |
| 5120→1024 | dgrad | bf16 | 16384 | previous version | 94.1 | 94.0 |
1.001 |
| 5120→1024 | fwd | bf16 | 16231 | previous version | 94.1 | 94.2 |
1.000 |
| 5120→1024 | fwd | bf16 | 16384 | previous version | 93.8 | 94.4 |
0.994 |
| 5120→1024 | wgrad | bf16 | 16231 | previous version | 98.4 | 98.7 |
0.996 |
| 5120→1024 | wgrad | bf16 | 16384 | previous version | 99.3 | 99.1 |
1.003 |
| 5120→1024 | wgrad | f32 | 16231 | previous version | 99.5 | 99.5 |
1.000 |
| 5120→1024 | wgrad | f32 | 16384 | previous version | 100.9 | 100.4 |
1.005 |
| 5120→5120 | dgrad | bf16 | 16231 | previous version | 434.0 | 435.7 |
0.996 |
| 5120→5120 | dgrad | bf16 | 16384 | previous version | 432.3 | 432.4 |
1.000 |
| 5120→5120 | fwd | bf16 | 16231 | previous version | 431.7 | 432.0 |
0.999 |
| 5120→5120 | fwd | bf16 | 16384 | previous version | 432.4 | 432.8 |
0.999 |
| 5120→5120 | wgrad | bf16 | 16231 | previous version | 435.7 | 437.7 |
0.996 |
| 5120→5120 | wgrad | bf16 | 16384 | previous version | 440.5 | 440.2 |
1.001 |
| 5120→5120 | wgrad | f32 | 16231 | previous version | 438.6 | 439.1 |
0.999 |
| 5120→5120 | wgrad | f32 | 16384 | previous version | 442.5 | 442.3 |
1.000 |
| 5120→17408 | dgrad | bf16 | 16231 | previous version | 1476.3 | 1476.2
| 1.000 |
| 5120→17408 | dgrad | bf16 | 16384 | previous version | 1471.9 | 1480.7
| 0.994 |
| 5120→17408 | fwd | bf16 | 16231 | previous version | 1457.6 | 1456.7 |
1.001 |
| 5120→17408 | fwd | bf16 | 16384 | previous version | 1458.7 | 1465.9 |
0.995 |
| 5120→17408 | wgrad | bf16 | 16231 | previous version | 1463.4 | 1458.7
| 1.003 |
| 5120→17408 | wgrad | bf16 | 16384 | previous version | 1472.6 | 1478.6
| 0.996 |
| 5120→17408 | wgrad | f32 | 16231 | previous version | 1474.7 | 1467.2
| 1.005 |
| 5120→17408 | wgrad | f32 | 16384 | previous version | 1500.0 | 1501.6
| 0.999 |
| indexer_hw (6144→32) | dgrad | bf16 | 16172 | previous version | 32.8
| 32.6 | 1.005 |
| indexer_hw (6144→32) | dgrad | bf16 | 16231 | previous version | 32.5
| 32.5 | 1.001 |
| indexer_hw (6144→32) | dgrad | f32 | 16172 | previous version | 58.5 |
58.4 | 1.001 |
| indexer_hw (6144→32) | dgrad | f32 | 16231 | previous version | 58.7 |
58.7 | 1.000 |
| indexer_hw (6144→32) | fwd | bf16 | 16172 | previous version | 36.6 |
36.4 | 1.003 |
| indexer_hw (6144→32) | fwd | bf16 | 16231 | previous version | 36.4 |
36.4 | 1.001 |
| indexer_hw (6144→32) | wgrad | bf16 | 16172 | previous version | 39.3
| 39.2 | 1.003 |
| indexer_hw (6144→32) | wgrad | bf16 | 16231 | previous version | 39.0
| 39.1 | 0.997 |
| indexer_hw (6144→32) | wgrad | f32 | 16172 | previous version | 39.1 |
39.1 | 1.001 |
| indexer_hw (6144→32) | wgrad | f32 | 16231 | previous version | 39.2 |
39.2 | 0.999 |
| indexer_k (6144→128) | dgrad | bf16 | 16172 | previous version | 34.4
| 34.4 | 1.000 |
| indexer_k (6144→128) | dgrad | bf16 | 16231 | previous version | 34.4
| 34.4 | 0.999 |
| indexer_k (6144→128) | dgrad | f32 | 16172 | previous version | 62.4 |
62.4 | 1.000 |
| indexer_k (6144→128) | dgrad | f32 | 16231 | previous version | 62.3 |
62.3 | 1.001 |
| indexer_k (6144→128) | fwd | bf16 | 16172 | previous version | 37.6 |
37.7 | 0.996 |
| indexer_k (6144→128) | fwd | bf16 | 16231 | previous version | 37.6 |
37.5 | 1.003 |
| indexer_k (6144→128) | wgrad | bf16 | 16172 | previous version | 40.6
| 40.5 | 1.002 |
| indexer_k (6144→128) | wgrad | bf16 | 16231 | previous version | 41.1
| 40.9 | 1.004 |
| indexer_k (6144→128) | wgrad | f32 | 16172 | previous version | 40.6 |
40.5 | 1.002 |
| indexer_k (6144→128) | wgrad | f32 | 16231 | previous version | 40.8 |
41.0 | 0.994 |
| kv_a (6144→576) | dgrad | bf16 | 16172 | previous version | 67.7 |
67.4 | 1.005 |
| kv_a (6144→576) | dgrad | bf16 | 16231 | previous version | 68.0 |
68.0 | 1.000 |
| kv_a (6144→576) | dgrad | f32 | 16172 | previous version | 93.0 | 92.6
| 1.004 |
| kv_a (6144→576) | dgrad | f32 | 16231 | previous version | 93.2 | 93.3
| 1.000 |
| kv_a (6144→576) | fwd | bf16 | 16172 | previous version | 73.2 | 73.0
| 1.002 |
| kv_a (6144→576) | fwd | bf16 | 16231 | previous version | 73.0 | 72.8
| 1.003 |
| kv_a (6144→576) | wgrad | bf16 | 16172 | previous version | 65.9 |
65.9 | 1.001 |
| kv_a (6144→576) | wgrad | bf16 | 16231 | previous version | 66.4 |
66.6 | 0.996 |
| kv_a (6144→576) | wgrad | f32 | 16172 | previous version | 66.8 | 66.8
| 0.999 |
| kv_a (6144→576) | wgrad | f32 | 16231 | previous version | 67.2 | 67.0
| 1.002 |
| q_a (6144→2048) | dgrad | bf16 | 16172 | previous version | 214.1 |
213.7 | 1.002 |
| q_a (6144→2048) | dgrad | bf16 | 16231 | previous version | 213.9 |
212.6 | 1.006 |
| q_a (6144→2048) | dgrad | f32 | 16172 | previous version | 223.8 |
223.7 | 1.000 |
| q_a (6144→2048) | dgrad | f32 | 16231 | previous version | 224.0 |
224.0 | 1.000 |
| q_a (6144→2048) | fwd | bf16 | 16172 | previous version | 211.8 |
212.3 | 0.997 |
| q_a (6144→2048) | fwd | bf16 | 16231 | previous version | 212.5 |
212.1 | 1.002 |
| q_a (6144→2048) | wgrad | bf16 | 16172 | previous version | 219.3 |
219.2 | 1.001 |
| q_a (6144→2048) | wgrad | bf16 | 16231 | previous version | 220.0 |
220.3 | 0.999 |
| q_a (6144→2048) | wgrad | f32 | 16172 | previous version | 220.7 |
221.0 | 0.998 |
| q_a (6144→2048) | wgrad | f32 | 16231 | previous version | 221.6 |
221.2 | 1.002 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16172 | previous version |
212.5 | 212.3 | 1.001 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16231 | previous version |
212.8 | 212.6 | 1.001 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16172 | previous version |
224.0 | 223.7 | 1.002 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16231 | previous version |
224.4 | 223.6 | 1.004 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16172 | previous version |
212.7 | 212.3 | 1.002 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16231 | previous version |
212.9 | 212.4 | 1.002 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16172 | previous version |
219.4 | 219.7 | 0.999 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16231 | previous version |
220.8 | 220.5 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16172 | previous version |
220.9 | 221.1 | 0.999 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16231 | previous version |
221.9 | 221.4 | 1.002 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16172 | previous version |
1234.6 | 1233.0 | 1.001 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16231 | previous version |
1248.7 | 1238.5 | 1.008 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16172 | previous version |
1239.8 | 1259.3 | 0.984 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16231 | previous version |
1243.9 | 1250.6 | 0.995 |
| 8192→128 | dgrad | bf16 | 16231 | previous version | 46.1 | 44.2 |
1.043 |
| 8192→128 | dgrad | bf16 | 16384 | previous version | 44.0 | 44.1 |
0.998 |
| 8192→128 | dgrad | f32 | 16231 | previous version | 86.0 | 86.0 |
1.000 |
| 8192→128 | dgrad | f32 | 16384 | previous version | 85.4 | 85.5 |
0.999 |
| 8192→128 | fwd | bf16 | 16231 | previous version | 47.1 | 47.2 | 0.998
|
| 8192→128 | fwd | bf16 | 16384 | previous version | 47.8 | 47.8 | 1.000
|
| 8192→128 | wgrad | bf16 | 16231 | previous version | 45.4 | 45.5 |
0.999 |
| 8192→128 | wgrad | bf16 | 16384 | previous version | 45.8 | 45.7 |
1.001 |
| 8192→128 | wgrad | f32 | 16231 | previous version | 45.2 | 45.2 |
1.001 |
| 8192→128 | wgrad | f32 | 16384 | previous version | 45.5 | 45.6 |
0.998 |
| 12288→4096 | dgrad | bf16 | 16231 | previous version | 827.0 | 827.5 |
0.999 |
| 12288→4096 | dgrad | bf16 | 16384 | previous version | 828.5 | 823.9 |
1.006 |
| 12288→4096 | fwd | bf16 | 16231 | previous version | 852.1 | 842.7 |
1.011 |
| 12288→4096 | fwd | bf16 | 16384 | previous version | 850.5 | 837.1 |
1.016 |
| 12288→4096 | wgrad | bf16 | 16231 | previous version | 833.2 | 833.4 |
1.000 |
| 12288→4096 | wgrad | bf16 | 16384 | previous version | 841.1 | 843.6 |
0.997 |
| 12288→4096 | wgrad | f32 | 16231 | previous version | 856.4 | 838.8 |
1.021 |
| 12288→4096 | wgrad | f32 | 16384 | previous version | 856.7 | 839.7 |
1.020 |
| dense_down (12288→6144) | wgrad | bf16 | 16172 | previous version |
1223.1 | 1240.1 | 0.986 |
| dense_down (12288→6144) | wgrad | bf16 | 16231 | previous version |
1231.2 | 1228.4 | 1.002 |
| dense_down (12288→6144) | wgrad | f32 | 16172 | previous version |
1241.3 | 1228.7 | 1.010 |
| dense_down (12288→6144) | wgrad | f32 | 16231 | previous version |
1235.6 | 1241.8 | 0.995 |
| o_proj (16384→6144) | dgrad | bf16 | 16172 | previous version | 1653.8
| 1654.9 | 0.999 |
| o_proj (16384→6144) | dgrad | bf16 | 16231 | previous version | 1649.0
| 1661.9 | 0.992 |
| o_proj (16384→6144) | dgrad | f32 | 16172 | previous version | 1681.8
| 1691.2 | 0.994 |
| o_proj (16384→6144) | dgrad | f32 | 16231 | previous version | 1694.7
| 1692.2 | 1.002 |
| o_proj (16384→6144) | fwd | bf16 | 16172 | previous version | 1673.6 |
1685.5 | 0.993 |
| o_proj (16384→6144) | fwd | bf16 | 16231 | previous version | 1674.5 |
1688.7 | 0.992 |
| o_proj (16384→6144) | wgrad | bf16 | 16172 | previous version | 1653.6
| 1648.5 | 1.003 |
| o_proj (16384→6144) | wgrad | bf16 | 16231 | previous version | 1659.5
| 1658.0 | 1.001 |
| o_proj (16384→6144) | wgrad | f32 | 16172 | previous version | 1662.4
| 1666.1 | 0.998 |
| o_proj (16384→6144) | wgrad | f32 | 16231 | previous version | 1673.9
| 1664.4 | 1.006 |
| 17408→5120 | dgrad | bf16 | 16231 | previous version | 1457.1 | 1466.5
| 0.994 |
| 17408→5120 | dgrad | bf16 | 16384 | previous version | 1458.1 | 1468.8
| 0.993 |
| 17408→5120 | fwd | bf16 | 16231 | previous version | 1468.6 | 1472.2 |
0.998 |
| 17408→5120 | fwd | bf16 | 16384 | previous version | 1468.2 | 1460.9 |
1.005 |
| 17408→5120 | wgrad | bf16 | 16231 | previous version | 1460.9 | 1449.6
| 1.008 |
| 17408→5120 | wgrad | bf16 | 16384 | previous version | 1480.5 | 1478.9
| 1.001 |
| 17408→5120 | wgrad | f32 | 16231 | previous version | 1461.4 | 1461.9
| 1.000 |
| 17408→5120 | wgrad | f32 | 16384 | previous version | 1473.0 | 1477.4
| 0.997 |
| qabs | dgrad | bf16 | 16172 | previous version | 229.6 | 229.9 | 0.999
|
| qabs | dgrad | bf16 | 16231 | previous version | 228.3 | 228.3 | 1.000
|
| qabs | fwd | bf16 | 16172 | previous version | 242.7 | 242.7 | 1.000 |
| qabs | fwd | bf16 | 16231 | previous version | 247.5 | 247.4 | 1.000 |
| qabs | wgrad | bf16 | 16172 | previous version | 216.2 | 216.2 | 1.000
|
| qabs | wgrad | bf16 | 16231 | previous version | 217.0 | 217.0 | 1.000
|
| vproj | dgrad | bf16 | 16172 | previous version | 266.5 | 266.3 |
1.001 |
| vproj | dgrad | bf16 | 16231 | previous version | 265.5 | 265.9 |
0.999 |
| vproj | fwd | bf16 | 16172 | previous version | 250.4 | 250.5 | 1.000
|
| vproj | fwd | bf16 | 16231 | previous version | 254.0 | 254.1 | 1.000
|
| vproj | wgrad | bf16 | 16172 | previous version | 234.2 | 233.6 |
1.003 |
| vproj | wgrad | bf16 | 16231 | previous version | 235.0 | 235.4 |
0.998 |
| router 4096→256 | dgrad | f32 | 16231 | previous version | 174.3 |
174.5 | 0.999 |
| router 4096→256 | fwd | f32 | 16231 | previous version | 165.4 | 165.9
| 0.997 |
| router 4096→256 | wgrad | f32 | 16231 | previous version | 163.8 |
163.9 | 1.000 |
| router 5120→256 | dgrad | f32 | 16231 | previous version | 226.4 |
226.6 | 0.999 |
| router 5120→256 | fwd | f32 | 16231 | previous version | 196.6 | 196.6
| 1.000 |
| router 5120→256 | wgrad | f32 | 16231 | previous version | 210.4 |
209.6 | 1.004 |
| router 6144→256 | dgrad | f32 | 16172 | previous version | 262.2 |
261.9 | 1.001 |
| router 6144→256 | dgrad | f32 | 16231 | previous version | 264.9 |
264.0 | 1.003 |
| router 6144→256 | fwd | f32 | 16172 | previous version | 228.8 | 228.8
| 1.000 |
| router 6144→256 | fwd | f32 | 16231 | previous version | 227.4 | 227.0
| 1.002 |
| router 6144→256 | wgrad | f32 | 16172 | previous version | 217.4 |
216.9 | 1.002 |
| router 6144→256 | wgrad | f32 | 16231 | previous version | 217.0 |
216.1 | 1.004 |

Every variant listed above ships in this package, which has programs for
sm_100a (GB200), sm_103a (GB300) and sm_107a: 249 build entries (80 / 82
/ 87) and 122 registry records, up from 247 (80 / 80 / 87) and 120 in
the previous version; the two added entries are the two new sm_103a
programs.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added whole-tile tile resolution for selected dense-projection GEMM
plans on supported hardware. Incompatible plan shapes and stream-K
configurations continue to use other planning options.
  - Added a clustered GEMM kernel for dense-projection workloads.

- **Bug Fixes**
- Improved validation of large dimensions and layout calculations:
arithmetic overflow and invalid modulo operations now produce clear
errors rather than potentially bypassing checks.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [762b237](https://github.com/flashinfer-ai/flashinfer/commit/762b237e151e2e7d408a33e8778c8b772c8f4eb8)

- **作者**: eigen
- **时间**: 2026-10-25T08:50:03Z
- **提交信息**: perf(cake_kda): with grad; fused gate epilogue on SM103, segmented 16-head rows on SM103 / SM107, two-level segment carry on SM100 / SM107, saved fold tensors on all three (#7274)

Cake has one variant of the packed KDA chunked training forward and
backward: BF16 tensors `q`, `k`, `v`, `out`, `dout`, `beta` and the
gradients, an FP32 gate, int32 `cu_seqlens`, layout `[1, S, H, 128]` and
head dimension 128. Its saving forward stores a saved set for the
backward in `light` (default) or `tape` mode, and a no-save forward
pairs with a checkpoint-replay backward. This PR changes the dispatch of
that variant on all three GPUs; the baseline is the previous Cake
version on main ("previous" in the tables). On SM103 (`sm_103a`, GB300),
every backward fuses the gate epilogue into the intra-chunk gradient
kernel (one launch fewer per backward) and the light forward saves the
fold's `qg`, so the backward prep recomputes less; the 16-head row (P12)
also runs a segmented forward-state plan instead of the serial walk. On
SM100 (`sm_100a`, B200), the rows with at most 2 heads use a two-level
segment carry (P9 in forward and backward, P10 in backward), every row
saves `qg` and the 16-head row saves `w`/`u`; the gate epilogue stays a
separate launch on this GPU. On SM107 (`sm_107a`, R200), the 16-head row
runs the segmented forward-state plan, P9 and P10 use the two-level
segment carry, and every row saves `qg`. Outputs and gradients are
bitwise identical to the previous version on every row on all three
GPUs; times are CUPTI GPU time with a cold L2, 3 groups × 64 iterations,
taking the more conservative of two independent processes.

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4** -- Previous is the Cake
version on main and this PR is the new dispatch, which changes every
row's backward on this GPU (fused gate epilogue, saved `qg`) and also
moves P12 to the segmented forward-state plan. The backward speedup is
1.05–1.07× on every row except P12 (1.1146×), and ckpt fwd+bwd is
1.03–1.06× on every row except P9 (1.0053×); forward ratios stay within
0.2 % of 1.00× except P12 (0.9905×).

| Shape (H, S) | fwd previous / this PR ms | fwd speedup | bwd previous
/ this PR ms | bwd speedup | ckpt fwd+bwd previous / this PR ms | ckpt
fwd+bwd speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 1.2892 / 1.2884 | 1.0006× | 2.9830 / 2.8220 |
1.0570× | 5.5558 / 5.3895 | 1.0309× |
| P2 (H=4, S=245028) | 1.3028 / 1.3031 | 0.9998× | 3.0685 / 2.9009 |
1.0578× | 5.6730 / 5.5035 | 1.0308× |
| P3 (H=4, S=249866) | 1.3197 / 1.3196 | 1.0001× | 3.1195 / 2.9515 |
1.0569× | 5.7557 / 5.5838 | 1.0308× |
| P4 (H=4, S=250340) | 1.3282 / 1.3283 | 0.9999× | 3.1348 / 2.9624 |
1.0582× | 5.7854 / 5.6151 | 1.0303× |
| P5 (H=4, S=258574) | 1.3609 / 1.3631 | 0.9984× | 3.2214 / 3.0468 |
1.0573× | 5.9434 / 5.7708 | 1.0299× |
| P6 (H=4, S=259042) | 1.3559 / 1.3571 | 0.9991× | 3.2314 / 3.0502 |
1.0594× | 5.9361 / 5.7585 | 1.0308× |
| P7 (H=4, S=259584) | 1.3527 / 1.3520 | 1.0005× | 3.2174 / 3.0399 |
1.0584× | 5.9175 / 5.7394 | 1.0310× |
| P8 (H=4, S=261393) | 1.3714 / 1.3726 | 0.9991× | 3.2539 / 3.0758 |
1.0579× | 5.9957 / 5.8149 | 1.0311× |
| P9 (H=1, S=261393) | 0.4477 / 0.4478 | 0.9999× | 0.9291 / 0.8849 |
1.0499× | 2.0692 / 2.0583 | 1.0053× |
| P10 (H=2, S=261393) | 0.7488 / 0.7487 | 1.0000× | 1.7310 / 1.6399 |
1.0555× | 3.2269 / 3.1356 | 1.0291× |
| P11 (H=8, S=261393) | 2.6008 / 2.6038 | 0.9988× | 6.3567 / 5.9971 |
1.0600× | 11.5556 / 11.2138 | 1.0305× |
| P12 (H=16, S=261393) | 5.0682 / 5.1170 | 0.9905× | 13.4631 / 12.0785 |
1.1146× | 23.6166 / 22.3657 | 1.0559× |
| P13 (H=32, S=261393) | 7.6824 / 7.6935 | 0.9986× | 24.6064 / 23.0944 |
1.0655× | 39.9803 / 38.4361 | 1.0402× |
| P14 (H=64, S=261393) | 15.7942 / 15.8017 | 0.9995× | 47.5263 / 44.4113
| 1.0701× | 79.0943 / 76.1164 | 1.0391× |

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4** -- Previous is the Cake
version on main and this PR is the new dispatch: P9 and P10 move to the
two-level segment carry (P9 fwd 1.1104× and bwd 1.0827×, P10 bwd
1.0563×), P12 saves `w`/`u` (bwd 1.0942×), and the saved `qg` lightens
every row's backward prep (bwd 1.015–1.029× on the H=4 rows, 1.0268× on
P11, 1.0252× and 1.0255× on P13 and P14). Every forward ratio except
P9's stays within 0.6 % of 1.00×.

| Shape (H, S) | fwd previous / this PR ms | fwd speedup | bwd previous
/ this PR ms | bwd speedup | ckpt fwd+bwd previous / this PR ms | ckpt
fwd+bwd speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 1.3989 / 1.4009 | 0.9986× | 3.2465 / 3.1627 |
1.0265× | 6.0436 / 5.9578 | 1.0144× |
| P2 (H=4, S=245028) | 1.4051 / 1.4082 | 0.9978× | 3.3017 / 3.2139 |
1.0273× | 6.1089 / 6.0237 | 1.0141× |
| P3 (H=4, S=249866) | 1.4249 / 1.4249 | 1.0000× | 3.3742 / 3.2831 |
1.0278× | 6.2187 / 6.1242 | 1.0154× |
| P4 (H=4, S=250340) | 1.4331 / 1.4340 | 0.9993× | 3.3763 / 3.2955 |
1.0245× | 6.2387 / 6.1444 | 1.0153× |
| P5 (H=4, S=258574) | 1.4739 / 1.4748 | 0.9993× | 3.5004 / 3.4073 |
1.0273× | 6.4356 / 6.3368 | 1.0156× |
| P6 (H=4, S=259042) | 1.4675 / 1.4685 | 0.9993× | 3.4800 / 3.4299 |
1.0146× | 6.4165 / 6.3189 | 1.0154× |
| P7 (H=4, S=259584) | 1.4629 / 1.4577 | 1.0035× | 3.5011 / 3.4027 |
1.0289× | 6.3987 / 6.2892 | 1.0174× |
| P8 (H=4, S=261393) | 1.4796 / 1.4802 | 0.9996× | 3.5004 / 3.4370 |
1.0185× | 6.4553 / 6.3619 | 1.0147× |
| P9 (H=1, S=261393) | 0.4816 / 0.4337 | 1.1104× | 0.9934 / 0.9175 |
1.0827× | 2.1989 / 2.1077 | 1.0432× |
| P10 (H=2, S=261393) | 0.8131 / 0.8128 | 1.0003× | 1.8646 / 1.7653 |
1.0563× | 3.4905 / 3.3909 | 1.0294× |
| P11 (H=8, S=261393) | 2.8247 / 2.8291 | 0.9985× | 6.9843 / 6.8022 |
1.0268× | 12.7905 / 12.6104 | 1.0143× |
| P12 (H=16, S=261393) | 5.5066 / 5.5135 | 0.9988× | 14.8983 / 13.6161 |
1.0942× | 25.9614 / 24.5401 | 1.0579× |
| P13 (H=32, S=261393) | 8.9015 / 8.9070 | 0.9994× | 28.4724 / 27.7728 |
1.0252× | 46.7632 / 46.1506 | 1.0133× |
| P14 (H=64, S=261393) | 17.8684 / 17.9726 | 0.9942× | 54.8974 / 53.5313
| 1.0255× | 91.1194 / 89.6880 | 1.0160× |

**NVIDIA R200 (sm_107a, 216 SMs), CUDA 13.4** -- Previous is the Cake
version on main and this PR is the new dispatch: P12 changes most
(segmented forward-state plan: fwd 1.0765×, bwd 1.1357×, ckpt fwd+bwd
1.1101×), P9 and P10 move to the two-level segment carry (P9 fwd 1.1278×
and bwd 1.0839×, P10 bwd 1.0523×), and the saved `qg` puts every other
row's backward at 1.020–1.025×. Every forward ratio except P9's and
P12's stays within 0.3 % of 1.00×.

| Shape (H, S) | fwd previous / this PR ms | fwd speedup | bwd previous
/ this PR ms | bwd speedup | ckpt fwd+bwd previous / this PR ms | ckpt
fwd+bwd speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 0.8585 / 0.8582 | 1.0003× | 2.0910 / 2.0459 |
1.0221× | 3.8046 / 3.7597 | 1.0119× |
| P2 (H=4, S=245028) | 0.8536 / 0.8539 | 0.9997× | 2.1160 / 2.0705 |
1.0220× | 3.8207 / 3.7764 | 1.0117× |
| P3 (H=4, S=249866) | 0.8604 / 0.8599 | 1.0005× | 2.1606 / 2.1122 |
1.0229× | 3.8792 / 3.8346 | 1.0116× |
| P4 (H=4, S=250340) | 0.8703 / 0.8709 | 0.9993× | 2.1613 / 2.1160 |
1.0214× | 3.9022 / 3.8535 | 1.0127× |
| P5 (H=4, S=258574) | 0.8861 / 0.8870 | 0.9990× | 2.2305 / 2.1823 |
1.0221× | 3.9995 / 3.9533 | 1.0117× |
| P6 (H=4, S=259042) | 0.8920 / 0.8919 | 1.0001× | 2.2302 / 2.1819 |
1.0222× | 4.0130 / 3.9641 | 1.0123× |
| P7 (H=4, S=259584) | 0.8832 / 0.8807 | 1.0029× | 2.2194 / 2.1728 |
1.0215× | 3.9881 / 3.9272 | 1.0155× |
| P8 (H=4, S=261393) | 0.8938 / 0.8951 | 0.9985× | 2.2346 / 2.1905 |
1.0201× | 4.0215 / 3.9802 | 1.0104× |
| P9 (H=1, S=261393) | 0.3177 / 0.2817 | 1.1278× | 0.6619 / 0.6106 |
1.0839× | 1.3296 / 1.2613 | 1.0542× |
| P10 (H=2, S=261393) | 0.5025 / 0.5034 | 0.9982× | 1.1972 / 1.1376 |
1.0523× | 2.2006 / 2.1396 | 1.0285× |
| P11 (H=8, S=261393) | 1.6804 / 1.6811 | 0.9996× | 4.3492 / 4.2429 |
1.0251× | 7.7151 / 7.6048 | 1.0145× |
| P12 (H=16, S=261393) | 3.5325 / 3.2815 | 1.0765× | 9.8339 / 8.6590 |
1.1357× | 16.8828 / 15.2082 | 1.1101× |
| P13 (H=32, S=261393) | 5.0435 / 5.0496 | 0.9988× | 17.6094 / 17.1754 |
1.0253× | 27.7019 / 27.2660 | 1.0160× |
| P14 (H=64, S=261393) | 11.0074 / 11.0021 | 1.0005× | 34.3914 / 33.5803
| 1.0242× | 56.3674 / 55.5737 | 1.0143× |

Cake ships no other data type or layout of this kernel; the same package
also carries its context-parallel form, which this PR leaves unchanged,
and the family covers `sm_100a`, `sm_103a` and `sm_107a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added architecture-specific optimized recurrence paths, including
segmented processing for additional workloads and two-level segment
carry.
* Light-mode saved state now supports version 4, including gated
queries, WY data, and segment-boundary states for applicable workloads.
* **Bug Fixes**
* Improved validation of tensor strides and launch inputs, reporting
errors for arithmetic overflow and unsupported values.
* Updated backward execution to support saved-state variants and fused
computation paths.
* **Documentation**
* Updated KDA training guidance with saved-state formats, memory
estimates, backward behavior, and architecture-specific dispatch
details.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4729
- **最后更新**: 2026-10-25T21:24:00Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Loay Rashid

## AI分析总结

# FastVideo 昨日提交分析（1/1 批）

## 1. 主要更新类型
**功能新增**：为新模型 Qwen-Image-2.1 添加了初始推理支持（`[new-model] Add initial Qwen-Image-2.1 inference (#1918)`），属于模型生态扩展类工作。

## 2. 关键变更点及与项目整体方向的关系
- 引入 Qwen-Image-2.1 的推理管线，扩展了 FastVideo 所支持的模型矩阵，属于"新模型接入"这一持续性工作流的一部分。
- 提交标题带有 `[new-model]` 标签，说明项目团队已建立规范化的模型接入流程（类似标签在社区协作中常见），与 README 中体现的文档化、社区驱动开发模式（Weekly Dev Meeting、Discussions、Cookbook）相一致。
- "initial" 一词表明这是该模型支持的第一版实现，后续预计还会有性能调优、分布式推理适配等迭代。

## 3. 对项目的影响和潜在意义
- **增强兼容性与竞争力**：FastVideo 作为快速视频/图像生成推理框架，每接入一个主流新模型都直接扩大用户可选择的模型范围，尤其 Qwen 系列背后是阿里通义生态，接入可吸引使用 Qwen 生态的开发者。
- **短期影响有限**：由于是"初始"版本，功能可能尚未覆盖所有优化路径（如量化、并行策略），实际性能优势有待后续提交验证。
- **社区协作信号**：Co-authored-by 记录表明该功能由外部贡献者与核心团队协作完成，体现了 README 所倡导的开放社区开发模式。

## 4. 值得关注的技术点
- **推理管线适配**：新模型接入通常涉及权重加载、模型结构映射、调度策略（如 spatio-temporal attention 切分）等核心推理组件的适配，可关注其是否复用了现有 FastVideo 加速内核（如 FP8 量化、KV cache 优化）还是走了独立路径。
- **分阶段交付模式**：先提交"initial inference"再逐步优化，是快速跟进上游新模型的常见策略，有助于保持框架的时效性。
- **协作元数据**：保留 Co-authored-by 有助于追踪贡献来源，也反映了项目对开源贡献的规范化管理。

## 5. 基于 README 背景的项目发展影响
FastVideo 定位为高性能视频/图像生成推理框架，配有完善的文档体系（Documentation、Cookbook、Quick Start）和活跃的社区机制（每周开发会议、Slack、Discussions）。本次提交延续了该框架"快速跟进前沿模型、降低用户上手门槛"的核心发展方向：新模型的接入使 Quick Start 和 Cookbook 有更多内容可覆盖，同时为开发者会议提供了持续的迭代议题。整体而言，这是一次典型的生态扩张型提交，单次影响较小，但与项目积累模型支持广度的长期战略一致，后续若跟进性能优化与文档更新，将真正兑现其对项目竞争力的贡献。

## 详细提交记录

### [0d05b09](https://github.com/hao-ai-lab/FastVideo/commit/0d05b09c575f3d74d80cfbc0808681ccb96ab540)

- **作者**: Loay Rashid
- **时间**: 2026-10-25T17:28:49Z
- **提交信息**: [new-model] Add initial Qwen-Image-2.1 inference (#1918)

Co-authored-by: Aryan Kumar <156166681+aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34807
- **最后更新**: 2026-10-25T23:48:21Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
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


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13302
- **最后更新**: 2026-10-25T10:34:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38156
- **最后更新**: 2026-10-26T00:09:06Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 13
- **主要提交者**: Shangming Cai, WenhaoZhang, Ke Bao

## AI分析总结

# SGLang 昨日提交分析（27 条）

## 1. 主要更新类型分布
- **功能新增（Feat）**：约 11 条，占比最高
- **Bug 修复（Fix）**：约 9 条
- **性能优化（Perf）**：约 5 条
- **重构/杂项（Refactor/Chore/CI）**：约 3 条
- 几乎没有纯文档更新，开发重心完全在代码层。

## 2. 关键变更点及与项目方向的关系
SGLang 定位为"LLM 与多模态模型的快速推理引擎"，本次提交与该方向高度吻合，主要围绕四条主线：

- **新模型/新硬件的深度适配**：围绕 DeepSeek-V4/V4.1（MoE 传输、稀疏备份、Rust prompt 渲染）、MiniMax-M3.1 NVFP4 量化、kimi-k3、Cosmos3、Hy-Nomas、LTX-2 等新模型持续投入；硬件上同时覆盖 NVIDIA（SM107/GB200、MNNVL fabric）、AMD（mamba、CI 调整）、Apple MLX。
- **量化与显存效率**：新增 MSA-v1 稀疏注意力后端与 NVFP4 KV cache kernel、block-FP8 量化投影复制、paged-experts 扩展支持 AWQ/MXFP4/NVFP4/W8A8 等多种专家量化格式，直接服务于降低显存占用和提升吞吐的核心目标。
- **分布式与分离式架构（Disaggregation/HiCache）**：KV checksum 校验落地并接入 decode 侧 radix cache、host Mamba 池占用导出、DP attention 图 bucket 对齐，强化了 PD 分离和分层缓存的正确性与可观测性。
- **Diffusion 推理管线崛起**：约 6 条提交涉及 diffusion（共享内存回收、消息隔离、GPU 预处理泛化、多 GPU VAE、内核向量化），表明项目正在把多模态/扩散模型支持提升为主线，而非附属功能。

## 3. 对项目的影响与潜在意义
- 多种量化格式（尤其 NVFP4、MXFP4 系）在 KV cache、注意力、MoE 专家中的贯通，将显著降低新 GPU 架构上的显存压力，提升长上下文服务能力。
- KV checksum 与 disaggregation 的完善，提高大规模 PD 分离部署的可靠性，降低跨节点传输损坏风险。
- Diffusion 管线的健壮性修复与性能优化，意味着 SGLang 正式扩展为"LLM + 多模态"统一推理平台，与其 README 定位一致。

## 4. 值得关注的技术点
- **MSA-v1 稀疏后端 + NVFP4 KV 池**：面向超长上下文的稀疏注意力方案，配合 4-bit KV 是前沿组合。
- **SM107 上的 FP32 warp split-K GEMM 与 KDA 分块调优**：针对下一代 NVIDIA 架构的细粒度 kernel 级优化。
- **MNNVL fabric 检测改为 NVML fabric 状态**：比硬编码 GB200/GB300 更鲁棒的硬件识别方式。
- **AMD mamba 的 chunked prefill 与 DCP checkpoint 对齐**：保证分布式 checkpoint 可复用的细节工程。
- **AI 协作工具（Claude/Cursor/Opus）频繁出现在 Co-authored-by 中**：AI 辅助开发已深度嵌入该项目的日常工程流程，值得社区关注其对代码质量和审阅流程的影响。

## 5. 对项目整体发展的影响
结合 README 中"快速推理"的核心目标，这批提交显示出 SGLang 正在三个维度同步扩张：硬件前沿（NVIDIA 下一代 + AMD + MLX）、模型前沿（DeepSeek-V4、MiniMax、扩散模型）、系统前沿（PD 分离、分层缓存、多量化格式统一支持）。短期内用户可期待更高吞吐、更低显存占用与更可靠的分布式部署；长期看，项目正从"LLM 推理引擎"演进为覆盖生成式文本与多模态扩散的通用高性能推理基础设施，这与其多模态模型快速推理的定位完全契合。

## 详细提交记录

### [8252e3a](https://github.com/sgl-project/sglang/commit/8252e3af630c103e960e13a77e570e810f8e3eb8)

- **作者**: chien-an-chen
- **时间**: 2026-10-25T22:30:06Z
- **提交信息**: [Fix] [AMD] mamba: Keep a chunked prefill cut on the mamba chunk grid so DCP can donate checkpoints (#41701)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [1b112fd](https://github.com/sgl-project/sglang/commit/1b112fd62aa19acf8cb6183890ef3d38430395e5)

- **作者**: Khoa Pham
- **时间**: 2026-10-25T22:25:32Z
- **提交信息**: [Perf] [NVIDIA] kimi-k3: FP32 warp split-K GEMM for the MoE front projection on SM107 (#46464)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [39b54ae](https://github.com/sgl-project/sglang/commit/39b54ae0eeca90f7097b22fe016e9212523a5968)

- **作者**: Khoa Pham
- **时间**: 2026-10-25T20:40:28Z
- **提交信息**: [Fix] [NVIDIA] dist: Detect MNNVL fabric devices by NVML fabric state, not only by GB200/GB300 name (#46463)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [640e11e](https://github.com/sgl-project/sglang/commit/640e11ebc0dfc660ea766acf43b0586d1819f494)

- **作者**: Khoa Pham
- **时间**: 2026-10-25T20:38:44Z
- **提交信息**: [Perf] [NVIDIA] kda: Narrower V tiles for the KDA spec-verify recurrence on SM107 (#46465)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f264183](https://github.com/sgl-project/sglang/commit/f264183bfe1d6f7e8f9046d5234f22e0496ecac7)

- **作者**: Khoa Pham
- **时间**: 2026-10-25T20:06:33Z
- **提交信息**: [Feat] dcp: Replicate a block-FP8 q_b_proj under --dcp-replicate-q-proj (#46359)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ee98bb0](https://github.com/sgl-project/sglang/commit/ee98bb09b02877ce55bbacd304121dfb7a2692a9)

- **作者**: Shangming Cai
- **时间**: 2026-10-25T17:51:22Z
- **提交信息**: [Feat] disaggregation: Verify the KV checksum under a decode-side radix cache (#46423)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8db75fc](https://github.com/sgl-project/sglang/commit/8db75fc6d0df398a0d384d9d5431b66a7ceb9666)

- **作者**: Ke Bao
- **时间**: 2026-10-25T16:52:29Z
- **提交信息**: [Fix] mlx: Accept draft_parallel_layout in the stub's alloc_memory_pool (#46441)

### [94d2b61](https://github.com/sgl-project/sglang/commit/94d2b61e38ca4c096c3ffe2586356bbc5ad55cc0)

- **作者**: Ke Bao
- **时间**: 2026-10-25T16:47:24Z
- **提交信息**: [Fix] unified-memory: Name the draft KV dtype flag in the fused-region mismatch error (#46442)

### [1406ffd](https://github.com/sgl-project/sglang/commit/1406ffda099f53c819e548ffea242350a0e55281)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-25T16:44:42Z
- **提交信息**: [Feat] rust: Render DeepSeek-V4/V4.1 prompts with deepseek-recipe in sglang-processor and sgl-router (#46243)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [26a1e51](https://github.com/sgl-project/sglang/commit/26a1e5110d4a3b185bdb9050145050615b3f805f)

- **作者**: feixiangpeng
- **时间**: 2026-10-25T15:33:09Z
- **提交信息**: [Feat] hicache: Export host Mamba pool occupancy next to host KV (#43727)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: alphabetc1 <2508695655@qq.com>

### [2d3de82](https://github.com/sgl-project/sglang/commit/2d3de82633b0ef16e11a6e39ab45d2a78d86752c)

- **作者**: Jan Schalkamp
- **时间**: 2026-10-25T15:26:24Z
- **提交信息**: [Feat] paged-experts: AWQ, compressed-tensors, MXFP4, NVFP4, W8A8 and block-INT8 experts (#45787)

### [c00e7e1](https://github.com/sgl-project/sglang/commit/c00e7e12b64b587da336c4350b1d2484c7dffcd6)

- **作者**: Shuwen Wang
- **时间**: 2026-10-25T14:51:27Z
- **提交信息**: [Fix] hisparse: Copy DeepSeek-V4 eager backups token by token (#45104)

### [3dfb166](https://github.com/sgl-project/sglang/commit/3dfb166322ca82f812d2de19dea7430fe4654ddb)

- **作者**: Shuwen Wang
- **时间**: 2026-10-25T14:50:47Z
- **提交信息**: [Refactor] linker: Use dedicated configuration throughout linker setup (#46388)

### [c05fb1b](https://github.com/sgl-project/sglang/commit/c05fb1bd04d2f9953dcef9a798d0984fb62d5253)

- **作者**: Mick
- **时间**: 2026-10-25T14:42:24Z
- **提交信息**: [Fix] diffusion/serving: Reclaim abandoned shared-memory replies (#46154)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [97220dd](https://github.com/sgl-project/sglang/commit/97220dd674370d5f30ba89d8c5ee2a7f36c68d40)

- **作者**: Mick
- **时间**: 2026-10-25T14:41:31Z
- **提交信息**: [Perf] diffusion: Run Cosmos3's multi-GPU VAE decode on the lossless fast path (#46173)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick <mickqian@radixark.ai>

### [4991bd3](https://github.com/sgl-project/sglang/commit/4991bd33ae1c9d7468394eaf966d7db88f352b7b)

- **作者**: Ke Bao
- **时间**: 2026-10-25T14:34:03Z
- **提交信息**: [Feat] attention: Add the MSA-v1 sparse backend and NVFP4 KV pool (#46141)

Co-authored-by: zhongyu <zhongyu@minimaxi.com>
Co-authored-by: Denji-kk <51020465+Denji-kk@users.noreply.github.com>
Co-authored-by: Thanhhao <31717833+thanhhao98@users.noreply.github.com>
Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: Qiaolin Yu <liin1211@outlook.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>

### [a99c7d0](https://github.com/sgl-project/sglang/commit/a99c7d050faee00b104a0b861df2d394ded74eb6)

- **作者**: Ke Bao
- **时间**: 2026-10-25T12:41:57Z
- **提交信息**: [Feat] quantization: Add the MiniMax-M3.1 NVFP4 MoE method (#46140)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: zhongyu <zhongyu@minimaxi.com>
Co-authored-by: Denji-kk <51020465+Denji-kk@users.noreply.github.com>
Co-authored-by: Qiaolin Yu <liin1211@outlook.com>

### [ad950cd](https://github.com/sgl-project/sglang/commit/ad950cdcd9666a104321deeaf1cbf883b4e8c60b)

- **作者**: Shu Wang
- **时间**: 2026-10-25T11:20:48Z
- **提交信息**: [Fix] deepseek-v4: Complete the MoE output locally when the transport declares no sum group (#46365)

Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [b48809d](https://github.com/sgl-project/sglang/commit/b48809dfc2d24ae4ed7d33326ca1a87cb1aa160f)

- **作者**: Michael
- **时间**: 2026-10-25T11:04:50Z
- **提交信息**: [CI] [AMD] pr-test: Move large-model and perf tests from AMD PR CI to nightly (#46085)

### [bea6a21](https://github.com/sgl-project/sglang/commit/bea6a21c368bc00900f4f7661360d7736ae7841d)

- **作者**: WenhaoZhang
- **时间**: 2026-10-25T10:27:23Z
- **提交信息**: [Feat] diffusion/model: support Hy-Nomas (#46124)

Co-authored-by: Yihao Wang <42559837+AgainstEntropy@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ca4bedf](https://github.com/sgl-project/sglang/commit/ca4bedfffae1fb248bbb55aaf9177c37f95d7d19)

- **作者**: Sage
- **时间**: 2026-10-25T10:06:30Z
- **提交信息**: [Chore] processor: use typed api output (#46031)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [5d11819](https://github.com/sgl-project/sglang/commit/5d11819f3a7a4c046da0d885a9335ed0f86ae92b)

- **作者**: Shangming Cai
- **时间**: 2026-10-25T10:05:27Z
- **提交信息**: [Fix] disaggregation: Clean-up and optimize the KV checksum implementation (#39729)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [174bd29](https://github.com/sgl-project/sglang/commit/174bd2976d34492915721504768f90bb988cd8a7)

- **作者**: Ke Bao
- **时间**: 2026-10-25T09:41:02Z
- **提交信息**: [Feat] msa: Add MSA-v1 decode and NVFP4 KV cache kernels (#46139)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Denji-kk <51020465+Denji-kk@users.noreply.github.com>
Co-authored-by: zhongyu <zhongyu@minimaxi.com>
Co-authored-by: Thanhhao <31717833+thanhhao98@users.noreply.github.com>
Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: Qiaolin Yu <liin1211@outlook.com>

### [9b230c1](https://github.com/sgl-project/sglang/commit/9b230c1dae7eb2fffd2c978e784821d7ac22d8e9)

- **作者**: Ke Bao
- **时间**: 2026-10-25T08:50:37Z
- **提交信息**: [Fix] dp-attention: Align prefill graph buckets and decode padding across DP ranks (#46138)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Denji-kk <51020465+Denji-kk@users.noreply.github.com>

### [933853a](https://github.com/sgl-project/sglang/commit/933853a3f2632b10e0bf10d7ffd2f6f853f574fa)

- **作者**: Mick
- **时间**: 2026-10-25T08:10:33Z
- **提交信息**: [Perf] diffusion/preprocess: generalize exact GPU input processing optimization across pipelines (#45733)

Signed-off-by: pinjie <pinjiex@nvidia.com>
Co-authored-by: pinjie <pinjiex@nvidia.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [a887ac8](https://github.com/sgl-project/sglang/commit/a887ac8fc6eae2bac7b892d108c1f9b939142840)

- **作者**: Mick
- **时间**: 2026-10-25T07:57:03Z
- **提交信息**: [Perf] diffusion: Vectorize the LTX-2 Q/K RMSNorm + split-RoPE kernel (#46111)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick <mickqian@radixark.ai>

### [a996b5f](https://github.com/sgl-project/sglang/commit/a996b5f2244ede791ce76f78e347db66bd7f0521)

- **作者**: Mick
- **时间**: 2026-10-25T07:55:59Z
- **提交信息**: [Fix] diffusion/disaggregation: Isolate malformed request and result messages (#46120)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1293
- **最后更新**: 2026-10-25T13:16:23Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Léon Simmons

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交（`763391a`）属于**文档更新**性质的改动，具体为修复代码注释和一条日志消息中的拼写错误（typos）。虽然修改位置在代码文件内部，但从变更内容看不涉及任何逻辑修改，归类为文档/文案层面的清理。

### 2. 关键变更点及与项目整体方向的关系
- **变更核心**：修正代码注释中的拼写错误以及一处日志输出消息中的错别字。
- **与项目方向的关联**：Cache-Dit 是一个面向 DiT（Diffusion Transformer）模型的 PyTorch 原生推理引擎，涵盖缓存、并行、量化、CPU offload 等核心能力。这类项目日志消息的准确性直接关系到用户在调试和性能分析时对引擎行为的理解。修正日志中的 typo 有助于提升用户排查问题时的可读性，与项目"高性能、生产可用"的定位相契合。
- 此类改动也体现了社区对代码质量细节的关注（由外部贡献者通过 PR #1138 提交），说明项目已有活跃的社区审阅流程。

### 3. 对项目的影响和潜在影响
- **功能性影响**：无。不改变任何运行时行为、接口或性能特征，升级无兼容性风险。
- **可维护性影响**：正面。准确的注释能降低新贡献者的理解成本，正确的日志文案能减少运维/用户误读。
- **项目形象影响**：持续的 typo 清理表明维护者重视代码整洁度，对一个被下载量徽章所标注、面向开源用户的推理引擎库而言，有助于提升专业度和可信度。
- **潜在意义**：这类"小而美"的贡献通常是项目社区健康的信号，说明有外部开发者愿意投入精力完善细节，也反映出项目的 PR 审核流程运转正常。

### 4. 值得关注的技术点
- 本次提交本身技术含量较低，值得关注的是**协作模式**：外部贡献者通过标准 PR 流程（#1138）完成小规模文档修复，提交包含规范的 `Signed-off-by` 签名，符合 DCO（Developer Certificate of Origin）规范，说明项目有较规范的开源治理实践。
- 对于推理引擎类项目，日志消息是用户感知引擎状态（如缓存命中、量化模式、offload 策略）的重要窗口，日志文案的准确性间接影响用户体验，后续可关注是否有更多围绕日志体系的结构化改进。

### 5. 基于 README 背景对项目发展的影响评估
Cache-Dit 的核心价值在于为 DiT 模型提供缓存、并行、量化和 CPU offload 等推理加速能力，属于 AI 推理基础设施赛道，竞争激烈（需与 TorchCompile、xFormers、各类量化框架等对比）。本次提交属于**低优先级的打磨型改动**，在项目发展时间线上的作用有限，但有两点积极意义：

其一，它反映出项目当前处于**相对稳定的维护期**，没有紧急的功能或 bug 修复压力，维护者有余力处理文案细节；其二，持续积累的社区小贡献（文档、注释、typo）会在长期内降低项目的整体维护成本，为后续功能开发铺平道路。

总体而言，此类提交对项目技术演进影响甚微，但对开源社区建设和项目精细化运营具有渐进式的正面价值。建议关注后续是否会出现围绕推理性能（如新缓存策略、新并行方案）的实质性提交，那才是判断项目技术发展方向的关键信号。

## 详细提交记录

### [763391a](https://github.com/vipshop/cache-dit/commit/763391abe5447b1d1b4cb7534bd10c1f04069841)

- **作者**: Léon Simmons
- **时间**: 2026-10-25T13:16:18Z
- **提交信息**: docs: fix typos in code comments and a log message (#1138)

Signed-off-by: Léon Avic Simmons <Avicennasis@gmail.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 95490
- **最后更新**: 2026-10-26T00:27:31Z

## 提交统计

- **昨日提交总数**: 21
- **提交者数量**: 18
- **主要提交者**: Woosuk Kwon, Andreas Karatzas, Isotr0py

## AI分析总结

## vLLM 昨日提交（21 条）分析总结

### 1. 主要更新类型
- **Bug 修复**为主（约 12 条），集中在 KV Offload、调度、投机解码等核心模块
- **功能新增**约 6 条：基准测试增强（PP/PCP 支持）、Dory 模型支持、预热缓存播种等
- **CI/文档**更新约 3 条：禁用不稳定依赖的 CI 任务、修复测试、Kimi-K3 文档

### 2. 关键变更点
- **KV Offload 大规模修复（6 条）**：处理已发布块重复存储、会话重启游标重置、异步查询异常捕获、二级存储失败背压、流式会话块表重置、NIXL 遥测。这表明 KV 卸载子系统正处于密集稳定化阶段。
- **调度器修复**：优先级自我抢占后保持运行请求调度，影响服务连续性。
- **投机解码修复**：auto-fit 后同步投机器限制，保证参数一致性。
- **新模型支持**：Dory 模型（NVIDIA 贡献）、Gemma 系列修复，体现对多厂商模型生态的持续扩展。
- **Fast Start 预热**：新增 daemon 间预热缓存播种，提升冷启动速度。
- **基准测试**：为 `vllm bench forward` 增加流水线并行（PP）稳态和 PCP 支持，增强性能评估能力。

### 3. 对项目的影响
- KV Offload 的密集修复显著提升分层存储子系统的可靠性，为大规模长上下文推理奠定基础。
- 调度与投机解码的修复直接改善生产环境下的服务稳定性。
- CI 稳定性治理（禁用未固定依赖的作业）反映项目对可复现构建的重视。

### 4. 值得关注的技术点
- **AI 辅助开发趋势明显**：多个提交由 Claude、Codex、vllm-agent、Kimi Code 等 AI 工具协同完成，体现人机协作开发模式正在渗透核心基础设施项目。
- KV Offload 的错误处理从"静默失败"转向"背压/遥测"语义，是分布式存储设计的成熟化信号。
- 预热缓存 daemon 间播种是对"Easy, fast, and cheap"目标中"fast"的直接呼应。

### 5. 对项目发展方向的影响
结合 README 强调的"简单、快速、低成本的 LLM 服务"目标：本轮提交整体呈现**从功能扩张转向生产级稳定化**的趋势。KV Offload 的加固支持"低成本"（分层存储降本），预热机制支持"快速"（减少冷启动），基准测试增强支撑持续的性能可测量性。这些工作共同推动 vLLM 从研究级推理引擎向企业级可靠服务平台演进。

## 详细提交记录

### [a7407ab](https://github.com/vllm-project/vllm/commit/a7407ab44557802ca32a0ba2c2707362d7d21563)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-25T23:55:29Z
- **提交信息**: [Benchmark] Add steady-state PP support to bench forward (#63616)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

### [237d2ff](https://github.com/vllm-project/vllm/commit/237d2ffd08044b52625453af59f1e47b9802d4ff)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-25T21:25:55Z
- **提交信息**: [Benchmark] Add PCP support to vllm bench forward (#63613)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [2c880f1](https://github.com/vllm-project/vllm/commit/2c880f1e68200f79c4663dd0f1e7beab6f536cfa)

- **作者**: Pablo Llopis
- **时间**: 2026-10-25T19:42:48Z
- **提交信息**: [Bugfix] Preserve FP8 indexer WK pairs across load_weights calls (#59223)

Signed-off-by: Pablo Llopis <pablo.llopis@epfl.ch>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>

### [f8c12c2](https://github.com/vllm-project/vllm/commit/f8c12c212acaff081378470e2af34e6a5d90dfc6)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-25T19:40:35Z
- **提交信息**: [CI] Disable jobs with unpinned runtime installs (#63609)

Signed-off-by: khluu <khluu000@gmail.com>

### [9d48c8a](https://github.com/vllm-project/vllm/commit/9d48c8ab952d490dc8fb55f133dcc132c325ee6a)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-25T19:30:06Z
- **提交信息**: [CI] Disable jobs with unlocked transitive dependencies (#63608)

Signed-off-by: khluu <khluu000@gmail.com>

### [0765565](https://github.com/vllm-project/vllm/commit/0765565f103d5579382ad61994a041654684778b)

- **作者**: Taneem Ibrahim
- **时间**: 2026-10-25T17:01:10Z
- **提交信息**: [Pooling] Reduce Clef metadata overhead (#63495)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [ceb01b6](https://github.com/vllm-project/vllm/commit/ceb01b6ddf6e19510ba138f810d38dd70e665f52)

- **作者**: dingdangmao
- **时间**: 2026-10-25T16:31:07Z
- **提交信息**: [Bugfix][Core] Keep scheduling running requests after a priority self-preemption (#61976)

Signed-off-by: apex-mochen <2756823972@qq.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [636da24](https://github.com/vllm-project/vllm/commit/636da2476d184b44e670449498ec850fbfaab8d6)

- **作者**: Harshil
- **时间**: 2026-10-25T16:14:29Z
- **提交信息**: [Bugfix][Spec Decode] Keep speculator limits in sync after auto-fit (#60513)

Signed-off-by: QHarshil <harshil_c@hotmail.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [1757f67](https://github.com/vllm-project/vllm/commit/1757f6720c3c1cc130a834b41f264ac22a782289)

- **作者**: Shreyansh Jain
- **时间**: 2026-10-25T15:41:55Z
- **提交信息**: [Bugfix][KV Offload] Treat an already-published fs block as stored (#61390)

Signed-off-by: Shreyansh Jain <shreyanshjain646@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [fa2881e](https://github.com/vllm-project/vllm/commit/fa2881ed19bef2957096788ce84d3b12cbd48948)

- **作者**: John Calderon
- **时间**: 2026-10-25T15:31:31Z
- **提交信息**: [CI][Benchmarks] Fix attention smoke test backend names and failure exit status (#63177)

Signed-off-by: John Calderon <jcalderon@nvidia.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [b346636](https://github.com/vllm-project/vllm/commit/b3466364b69db84ddeca30435f56c822551f8b14)

- **作者**: Chongmin Li
- **时间**: 2026-10-25T15:12:42Z
- **提交信息**: [Bugfix] Release cached cuBLAS workspaces after daemon warmup (#63451)

Signed-off-by: lichongmin <chongminli.cn@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6f51433](https://github.com/vllm-project/vllm/commit/6f51433838b858a9cd0478b2ffee4d2c610a1712)

- **作者**: Advay Monga
- **时间**: 2026-10-25T13:40:14Z
- **提交信息**: [Bugfix][KV Offload] Reset the store cursor when a request restarts from token 0 (#63010)

Signed-off-by: Advay Monga <advaymonga@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [94a29d3](https://github.com/vllm-project/vllm/commit/94a29d316e8c1d6dcf6ff75645c2e61c7e3c83fd)

- **作者**: Isotr0py
- **时间**: 2026-10-25T13:03:40Z
- **提交信息**: [Fast Start] Add daemon-to-daemon warmup cache seeding for Preload (#63088)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Xun Sun <UNIDY2002@outlook.com>
Co-authored-by: liusy58 <mg21330037@smail.nju.edu.cn>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [503e4e1](https://github.com/vllm-project/vllm/commit/503e4e16ad8d4c4b7b1290c9f2792af0ca622c47)

- **作者**: Pepsi-Cola-qqq
- **时间**: 2026-10-25T12:28:46Z
- **提交信息**: [Bugfix][KV Offload] Catch async lookup iterator errors (#63126)

Signed-off-by: w_wanghaiqiao <w_wanghaiqiao@kingsoft.com>
Co-authored-by: w_wanghaiqiao <w_wanghaiqiao@kingsoft.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4a81a50](https://github.com/vllm-project/vllm/commit/4a81a5097631ad9851a7045ebb4f2f8c4873eec0)

- **作者**: Zupeng Wang
- **时间**: 2026-10-25T12:28:31Z
- **提交信息**: [Bugfix][KV Offload] Enable NIXL telemetry for the OBJ tier (#55576)

Signed-off-by: Wang Zupeng <zupenwang@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [75fc05a](https://github.com/vllm-project/vllm/commit/75fc05a53a366068f534a61ab3ee6b50485419f2)

- **作者**: Shantanu Acharya
- **时间**: 2026-10-25T11:13:22Z
- **提交信息**: [Model] Add Dory support (#60149)

Signed-off-by: Shantanu Acharya <shantanua@nvidia.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [24324ef](https://github.com/vllm-project/vllm/commit/24324ef0f667c633ee9bbb9412343d829f7e6d4e)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-25T09:22:35Z
- **提交信息**: [CI] Fix the Qwen2 embed memory leak and HfRunner no-cache logprobs (#63537)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b70de52](https://github.com/vllm-project/vllm/commit/b70de52965a87125fa103a50834ec6cc1b276cb0)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-25T09:20:53Z
- **提交信息**: [Bugfix][Model] Borrow Gemma4 _get_max_soft_tokens in EmbeddingGemma2 and DiffusionGemma (#63538)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [2b1f75c](https://github.com/vllm-project/vllm/commit/2b1f75c80f79496b313e28362f0856632dfbf5ea)

- **作者**: Marcel Yeonghyeon Ko
- **时间**: 2026-10-25T08:54:10Z
- **提交信息**: [Bugfix][KV Offload] Treat failed secondary-tier stores as back-pressure (#61780)

Signed-off-by: YeonghyeonKO <dk02315@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2f1041e](https://github.com/vllm-project/vllm/commit/2f1041e8dd05415d9984d0a83ad957d54a049eb4)

- **作者**: Roy Wang
- **时间**: 2026-10-25T08:30:41Z
- **提交信息**: [Doc] Kimi-K3: InferenceX AgentX lanes as tuned presets; DCP only in presets (#63552)

Signed-off-by: esmeetu <jasonailu87@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [921ed7f](https://github.com/vllm-project/vllm/commit/921ed7fa11c41b89ce36e81f50fb3b1c293dc8f7)

- **作者**: alberto
- **时间**: 2026-10-25T07:55:59Z
- **提交信息**: [Bugfix][KV Offload] Reset a resumed streaming session's block table in OffloadingConnector and SimpleCPUOffloadConnector (#60810)

Signed-off-by: Alberto Perdomo <aperdomo@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-26
**监控日期**: 2026-10-25
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7349
- **最后更新**: 2026-10-25T23:06:56Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 8
- **主要提交者**: amy-why-3459, lm10-arg, Liuchenbing-2026

## AI分析总结

## 一、主要更新类型

- **CI/构建与硬件覆盖**：3 条，占比最高，集中在 AMD/ROCm 夜间测试流水线。
- **Bug 修复**：2 条，均针对 diffusion speech（扩散式语音）输入校验。
- **文档更新**：2 条，涉及 MiniCPM-o 注意力后端对比与 Tongyi/Z-Image-Turbo。
- **性能优化**：1 条，CosyVoice3 采样器同步开销削减。
- **可观测性/指标**：1 条，暴露预热后内存快照。
- **基准测试**：1 条，CosyVoice3 并发基准支持多参考音色。

## 二、关键变更与项目方向的关系

- vLLM-Omni 的目标是"为所有人提供简单、快速、低成本的全模态模型服务"，本批次提交恰好落在支撑这一目标的三条主线上：**多硬件可服务性（ROCm）、多模态模型正确性与效率、服务易用性**。
- ROCm 相关提交把 MI300/MI325 的覆盖从单一场景扩展到 tiny-diffusion 多卡与 MiniCPM-o Omni-DuplexEval，并按源码变更过滤夜间构建以降低无效算力消耗，直接服务于"cheap"这一承诺。
- diffusion speech 的两条校验修复补齐了服务入口的参数与模型名防御，属于全模态服务稳定性基础工作。

## 三、影响与潜在意义

- 短期看，CI 侧改动减少夜间任务开销、扩大硬件回归面，有助于在 AMD 平台上更早发现全模态回归问题。
- 内存快照与并发基准增强，使开发者能定量观察服务内存行为与语音合成并发表现，符合项目"fast"的定位。
- 校验类修复降低了非法请求导致的异常路径风险，对线上服务健壮性有直接收益。

## 四、值得关注的技术点

- **按源码变更过滤夜间构建**：一种兼顾覆盖率与 CI 成本的折中策略，值得其他模态流水线复用。
- **MI325 多卡 diffusion 夜间覆盖**：扩散模型的多卡一致性测试此前较为薄弱，此次补齐是硬件适配深度的信号。
- **CosyVoice3 V1 RAS 采样器减少同步**：提示该模型推理路径中同步开销是当前瓶颈之一，后续可能还有优化空间。
- **文档明确记录"识别错误与提交后超时仍未解决"**（关联 #8637）：体现了透明的技术债管理，也提醒使用者注意相关限制。

## 五、对项目发展的整体影响

这批提交表明 vLLM-Omni 正处于**从功能铺开转向工程加固**的阶段：一方面通过 ROCm 夜间覆盖与过滤机制夯实跨硬件交付能力，使全模态服务真正具备"cheap 且 fast"的落地条件；另一方面通过语音入口校验、内存指标与采样器优化提升服务的正确性与可观测性。文档侧对后端对比与部署覆盖层的澄清，则降低了用户在 MiniCPM-o 等复杂模型上的上手门槛，呼应 README 中"Easy"的承诺。综合来看，这些改动虽单个体量不大，但共同推进了项目在多硬件、多模态、可运维三个维度上的成熟度，为后续更大规模的模型与硬件支持奠定了基础。

## 详细提交记录

### [14874d0](https://github.com/vllm-project/vllm-omni/commit/14874d08a12bc1e61c5194ae6ce32e20589ea74e)

- **作者**: lm10-arg
- **时间**: 2026-10-25T20:06:23Z
- **提交信息**: [CI/Build] Filter AMD PR nightlies by source changes (#9372)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [89b9d5a](https://github.com/vllm-project/vllm-omni/commit/89b9d5a8947d55f3461794abf032dbba015c301f)

- **作者**: lm10-arg
- **时间**: 2026-10-25T19:07:56Z
- **提交信息**: [CI][ROCm] Add MI325 tiny-diffusion multi-GPU nightly coverage (#9369)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [3ff951d](https://github.com/vllm-project/vllm-omni/commit/3ff951df1935a174d67ca670645c57ba11d29238)

- **作者**: Liuchenbing-2026
- **时间**: 2026-10-25T18:37:50Z
- **提交信息**: [Bugfix] Validate served model names in diffusion speech (#8882)

Signed-off-by: liuchenbing <chenliumail@163.com>
Co-authored-by: liuchenbing <chenliumail@163.com>

### [36027f8](https://github.com/vllm-project/vllm-omni/commit/36027f8f936dd456de7dfc220fd871dfe826106d)

- **作者**: Liuchenbing-2026
- **时间**: 2026-10-25T17:57:03Z
- **提交信息**: [Bugfix] Validate diffusion speech sampling parameters (#8685)

Signed-off-by: liuchenbing <chenliumail@163.com>
Co-authored-by: liuchenbing <chenliumail@163.com>

### [b6dd3e9](https://github.com/vllm-project/vllm-omni/commit/b6dd3e9c5ef8c2495394f036f32036a385f950c2)

- **作者**: Arifuzzaman Joy
- **时间**: 2026-10-25T17:21:10Z
- **提交信息**: [Benchmark] Accept multiple reference voices in CosyVoice3 concurrency benchmark (#8456)

Signed-off-by: Arifuzzamanjoy <s1710374103@ru.ac.bd>

### [68f0c78](https://github.com/vllm-project/vllm-omni/commit/68f0c78ee4648c906990ac7f262ff616c93f9be3)

- **作者**: akshatvishu
- **时间**: 2026-10-25T16:51:11Z
- **提交信息**: [Core][Metrics] Expose stage post-warmup memory snapshots (#5180)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>

### [f7d012b](https://github.com/vllm-project/vllm-omni/commit/f7d012bf3c2f63468a76b86acef5e5033872f7f5)

- **作者**: SuyanLi
- **时间**: 2026-10-25T13:25:32Z
- **提交信息**: [Model] Reduce CosyVoice3 V1 RAS sampler synchronization (#8730)

Signed-off-by: SuyanLi <suyanli220@gmail.com>

### [0a4998d](https://github.com/vllm-project/vllm-omni/commit/0a4998dca1bfae67ae25d72c33325771ebf31331)

- **作者**: haic0
- **时间**: 2026-10-25T12:45:23Z
- **提交信息**: [CI/Build][ROCm] Add MiniCPM-o Omni-DuplexEval to MI300 nightly (#9269)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [324cb5d](https://github.com/vllm-project/vllm-omni/commit/324cb5d9c546fb0381db0ba614959ee0ac5b6703)

- **作者**: amy-why-3459
- **时间**: 2026-10-25T09:25:03Z
- **提交信息**: [Docs] Clarify MiniCPM-o attention backend comparisons (#9344)

Document a CUDA-only stage-0 deployment overlay and a controlled backend comparison procedure for MiniCPM-o. Keep deployment defaults unchanged and retain a test dictionary type annotation.

Related to #8637; recognition errors and post-commit timeouts remain unresolved.

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [c586c28](https://github.com/vllm-project/vllm-omni/commit/c586c28ed6b4d108e0e0a43eddf58e13fba184eb)

- **作者**: MrDongsls
- **时间**: 2026-10-25T09:11:33Z
- **提交信息**: [Doc] Tongyi/Z-Image-Turbo (#3283)

Signed-off-by: Mr.Dong <1042542469@qq.com>
Co-authored-by: Mr.Dong <1042542469@qq.com>

---
