# GitHub Stars 合并报告 - 2026-07-24

**合并日期**: 2026-07-25
**监控日期**: 2026-07-24
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


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2107
- **最后更新**: 2026-07-24T11:19:23Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Zeren Chen, Sang

## AI分析总结

好的，以下是对昨日两个提交的简明分析总结，结合VeOmni项目的背景（旨在为任意模态模型提供以模型为中心的分布式训练配方）。

---

### 1. 主要更新类型
- **Bug修复**：修复DiT（扩散Transformer）训练中梯度累积损失的归一化问题。
- **功能新增**：新增FlexAttention并与Ulysses序列并行方案集成。

### 2. 关键变更点及其与项目整体方向的关系
- **DiT梯度累积损失修复**：  
  修正了在梯度累积场景下DiT损失计算不正确的逻辑，确保每个微批次的损失按累积步数归一化。  
  *关系*：DiT是生成式多模态模型（如图片、视频生成）的核心架构，修复训练稳定性直接支持项目中“缩放任意模态模型训练”的目标。

- **FlexAttention + Ulysses序列并行**：  
  引入更灵活的注意力机制（FlexAttention），并利用Ulysses方案在序列维度上拆分计算，支持更长序列的高效分布式训练。  
  *关系*：多模态模型（如长视频、高分辨率图像）需要处理超长序列，该功能扩展了VeOmni的分布式配方库，符合“以模型为中心、可扩展”的设计哲学。

### 3. 对项目的影响和潜在意义
- **训练可靠性提升**：DiT的修复避免了梯度累积场景下梯度估计偏差，防止模型发散或收敛不充分，提升用户实际使用体验。
- **长序列能力增强**：FlexAttention + Ulysses使VeOmni能够在多GPU下高效训练超长上下文模型（如多模态视频理解、长文档生成），扩大了支持的模态和任务范围。
- **社区吸引力**：新增实用功能（FlexAttention）吸引需要自定义注意力机制的开发者，同时修复关键bug增加项目可信度。

### 4. 值得关注的技术点
- **梯度累积损失归一化**：通常梯度累积时，损失应除以累积步数（或等效处理），否则梯度量级错误。该修复可能只针对DiT的特定实现，但反映了对数值精度的重视。
- **FlexAttention的灵活性**：可能支持稀疏注意力、窗口注意力、线性注意力等变体，允许用户按需替换注意力内核。
- **Ulysses序列并行**：与ZeRO、张量并行正交，在序列维度分片计算注意力，能显著降低每块GPU的内存和计算负载，适合长序列。

### 5. 对项目发展的推动作用
- **覆盖更多模态**：DiT修复巩固了VeOmni对扩散模型的支持（常见于图像/视频生成）；序列并行扩展了处理长序列模态（如视频、音频）的能力。
- **完善配方Zoo**：新增的FlexAttention+Ulysses成为一个新的分布式训练“配方”，可被用户直接引用或组合，促进“Recipe Zoo”的丰富性和模块化。
- **迈向工业化**：修复关键bug和增加实用并行策略，表明项目正在从论文实验向稳定生产环境过渡，符合“Scaling Any Modality”的最终愿景。

## 详细提交记录

### [506f6d6](https://github.com/ByteDance-Seed/VeOmni/commit/506f6d6b6c1d715b1b22f6bb144797de222cc2d1)

- **作者**: Sang
- **时间**: 2026-07-24T09:04:20Z
- **提交信息**: [trainer] fix: normalize DiT gradient accumulation loss (#963)

Co-authored-by: zsqiao <zsqiao@iflytek.com>

### [df65f4f](https://github.com/ByteDance-Seed/VeOmni/commit/df65f4fd7dafbd03702e35cf94d839530b280f96)

- **作者**: Zeren Chen
- **时间**: 2026-07-24T07:40:23Z
- **提交信息**: [ops, dist] feat: add FlexAttention with Ulysses sequence parallelism (#945)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2526
- **最后更新**: 2026-07-24T15:08:01Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: Watebear, Shiqiao Gu (谷石桥)

## AI分析总结

### 总结昨日更新要点

#### 1. 主要更新类型
- **功能新增**：支持 Wan2.2 和 Flux 张量并行（TP）推理（#1282）
- **性能优化与 Bug 修复**：修复 MLU 平台 SDPA 的 NaN 问题，替换 Gemma3 文本编码器的注意力运算（#1290）
- **模型更新**：更新 LTX2.3 版本（#1289）
- **功能增强**：LTX2 使用真实梅尔频谱图，并支持音频梅尔谱的 CPU 卸载（#1288）

#### 2. 关键变更点与项目方向关系
- **Wan2.2 + Flux TP**：扩展了支持的视频生成模型列表，Flux 张量并行可提升多卡推理效率，强化了框架的“轻量推理”和多模型兼容性。
- **Gemma3 注意力替换**：针对特定硬件（MLU）优化，通过平台自适应注意力算子避免 NaN，提升文本编码器在国产硬件上的稳定性，符合“跨平台推理”目标。
- **LTX 模型迭代**：持续跟进 LTX 系列（2.3），确保框架与最新模型版本同步。
- **音频功能完善**：真实梅尔谱与 CPU 卸载，为后续视频生成中音频模态支持（如配音、音画同步）打下基础，拓宽了应用的边界。

#### 3. 对项目的影响与潜在意义
- **兼容性与鲁棒性**：修复 MLU 平台 NaN 问题、新增平台算子替换机制，使得框架在更多硬件（非 NVIDIA）上可可靠运行，降低部署门槛。
- **生态扩展**：支持 Wan2.2 和 Flux TP 加速，吸引使用这些模型的用户，提升项目影响力。
- **多模态增强**：音频相关提交表明项目正从纯视频生成向音视频多模态方向演进，适应更丰富的应用场景（如视频配音、音画同步生成）。

#### 4. 值得关注的技术点
- **张量并行（TP）**：Flux TP 的实现可能涉及模型并行切分策略，对于大模型推理优化有参考价值。
- **平台自适应注意力**：替换 Gemma3 的注意力操作，设计可插拔的算子接口，使得框架能根据硬件自动选择最优实现（如 MLU SDPA 替代方案）。
- **梅尔频谱 CPU 卸载**：音频处理中常用的梅尔谱计算常占用 GPU 显存，CPU 卸载可节省显存用于视频生成主任务，体现“轻量”优化思路。

#### 5. 对项目发展的影响（结合 README 背景）
- 项目定位为“轻量视频生成推理框架”，此次更新使框架能运行更前沿的 Wan2.2 模型，并借助 Flux TP 实现高效多卡推理，增强了竞争力。
- MLU 平台的支持与算子替换策略，表明项目致力于打破 NVIDIA 生态依赖，向国产硬件和多样化计算平台拓展。
- 音频模块的引入暗示后续可能集成音视频联合生成（如 Sora 类模型），使框架从纯视觉走向多模态，符合视频生成领域“声音+画面”的技术趋势。

## 详细提交记录

### [d658c11](https://github.com/ModelTC/LightX2V/commit/d658c11edb77124387f275c1c080fcf9612ba8e1)

- **作者**: Watebear
- **时间**: 2026-07-24T10:51:00Z
- **提交信息**: feat: support wan2.2, flux tp (#1282)

### [babf5b3](https://github.com/ModelTC/LightX2V/commit/babf5b317871b9aad38c37097f61ef56a1316da6)

- **作者**: Watebear
- **时间**: 2026-07-24T10:48:40Z
- **提交信息**: LTX：gemma3 replace attn ops  (#1290)

1. mlu sdpa Nan
2. support replace by platform attn ops in gemma3 text encoder

---------

Co-authored-by: wushuo1 <540295877@example.com>

### [e6fc23e](https://github.com/ModelTC/LightX2V/commit/e6fc23e1448d984d13fe045f267b586f4dc4ca94)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-07-24T08:44:46Z
- **提交信息**: update ltx2.3 (#1289)

### [c0327b7](https://github.com/ModelTC/LightX2V/commit/c0327b74642a5e40bb852d96a91a4dd73a99116b)

- **作者**: Watebear
- **时间**: 2026-07-24T08:03:18Z
- **提交信息**: LTX2: use_real_mel_spectrogram (#1288)

audio_mel_cpu_offload

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2179
- **最后更新**: 2026-07-23T10:16:57Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6020
- **最后更新**: 2026-07-24T21:18:53Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Brian K. Ryu, Lee Yongjun, Prasun Gera

## AI分析总结

### 昨日更新总结（基于提交记录及项目背景）

#### 1. 主要更新类型
- **功能新增**：模块化预填充（prefill）支持滑动窗口（sliding-window）与带掩码（band-mask）；LayerNorm + FP8量化融合内核；机密计算（Confidential Computing）下的多播无关IPC通信工作区。
- **性能优化**：模块化prefill中去除无效计算（dead work）、优化掩码代码生成及调度策略；LayerNorm量化融合最高7倍速度提升。
- **重构**：CuTe-DSL prefll的MaskType从枚举改为可组合的带状掩码（band），统一了causal、window_left/right等语义。
- **文档更新**：新增`layernorm_quant` API文档条目。
- **维护**：添加代码所有者（codeowner）至通信模块。

#### 2. 关键变更点与项目方向的关系
- **注意力模块**：扩展支持多种窗口掩码（causal+window_left、对称窗口等），运行时参数化窗口大小，仅编译4种mask内核。  
  → 符合项目“高性能推理核”定位，覆盖长文本推理中常见的局部注意力（如滑动窗口）需求。
- **LayerNorm + FP8量化**：融合归一化与FP8量化，减少显存带宽（7B→3B per element）。  
  → 补齐RMSNorm系列功能，简化FP8部署流程，与推理量化趋势一致。
- **通信模块（TRT-LLM AR融合）**：在机密计算环境下自动切换到IPC工作区（绕过`cuMulticast`限制），并抛出mnnvl后端的异常。  
  → 扩大FlashInfer在企业安全场景的可用性，与多GPU推理扩展相关。

#### 3. 对项目的影响与潜在意义
- **注意力**：在与trtllm-gen的对比中，windowed场景下速度优势显著（如causal+window=

## 详细提交记录

### [ec2e0be](https://github.com/flashinfer-ai/flashinfer/commit/ec2e0be3b24859dccd36dfd8e48424c1023725bd)

- **作者**: Prasun Gera
- **时间**: 2026-07-24T21:13:42Z
- **提交信息**: CuTe-DSL modular prefill: sliding-window support + band-mask performance (#3952)

# CuTe-DSL modular prefill: sliding-window support + band-mask
performance

## Summary

The modular CuTe-DSL prefill (SM100) mapped `causal=True + window_left
>= 0`
to a plain causal mask — wrong results, and full O(s²/2) work. This PR
fixes
the mask semantics with composable per-row bands, removes the banded
regime's
dead work, makes window sizes runtime arguments (one compiled kernel per
mask
kind), and routes windowed plans to this path. It also adds native LSE
output and mixed K/V dtype support (bf16/fp16 Q/K + fp8 V) to the
modular
kernel, so windowed plans never leave it at run time.

## Changes

- **Composable band masks (correctness fix)**: the `MaskType` enum
becomes a
band `[lo(q), hi(q))` — causal composes with `window_left`;
`window_left`
  alone is a left-bounded non-causal window (FA2 semantics); new
  `window_right` plan() parameter for symmetric windows. Loader / MMA /
softmax / correction all derive trip counts from the same band helpers.
- **Dead work removal**: per-half band iteration (head/tail peel) — each
128-row half of the CTA runs exactly its own band's trips instead of the
union with ~1 dead step per stage; warp-ballot rescale skip in
correction
  (skips the O-tile TMEM roundtrip when the factor is exactly 1).
- **Mask codegen**: hoisted row-invariant bounds, trace-time-constant K
coordinates, `cutlass.select_` for masked writes; one shared path for
all
four mask kinds (avoids an MLIR lowering pathology that caused register
  spills on the release toolchain).
- **Runtime window values**: `MaskSpec` is two presence bits; window
sizes
are runtime `Int32` kernel args, causal is a right bound with value 0,
and
the `k < seqlen_k` tail check is always on. Mask compile matrix: 4
kernels.
- **Scheduling by mask kind**: banded masks default to non-persistent
launch,
unmasked stays persistent (`FLASHINFER_CUTE_PREFILL_PERSISTENT`
overrides).
- **`sm_scale` default fix**: cute-dsl wrapper plan() now defaults to
  `1/sqrt(head_dim_qk)` (was 1.0, silently unscaled).
- **Vendored FMHA windowed compile fix**: the #3857 path crashed on any
`window_left >= 0` (no window axis in the trace signature, compile
cache,
  or artifact names); it now JIT-compiles with window-presence bits.
- **Native LSE**: `run(return_lse=True)` is computed in the correction
warp
  from the final (row_sum, row_max) — log2-domain, matching the vendored
  kernel's convention. Zero cost when off (the non-LSE kernel's SASS is
  byte-identical) and ≲1% when on. Supported for score-mod and sink
  variants; logits-transform variants (no softmax) raise.
- **Mixed K/V dtypes**: bf16/fp16 Q/K with fp8 V. P converts to V's
dtype
for the PV MMA, V slots on the shared K/V smem ring re-arm their barrier
  with V's byte count, and the wrapper JIT-compiles per-V-dtype kernel
  variants at run time (V's dtype is a run-time property; plan()'s
  `kv_data_type` declares K and V together).
- **Routing**: `variant is None and head_dim_qk == 128 and window_left <
0`
routes to the #3857 vendored kernel; everything else — windows,
variants,
other head dims, any V dtype, `return_lse` — runs the modular path. The
  gate is decided entirely at plan(); there is no run-time fallback.

## Correctness

New causal+window, left-only, and symmetric-window tests in
`tests/attention/test_modular_fmha_prefill.py`, including windowed masks
over mixed-length ragged batches (each sequence gets its own band
geometry; short sequences exercise the item-skip path). Validated on
B200 against an
exact f32 reference over {8/8, 32/8, 64/8, 32/32} heads × 5 shapes × 4
masks
in both scheduler modes (152/152), with bitwise-identical outputs across
scheduler modes.

Also new: uniform-fp8 (e4m3) tests calibrated against the vendored
kernel's
fp8 error on identical inputs (both ~0.066 max vs f32); mixed
bf16-QK/fp8-V
tests against a dequantized-V f32 reference (~0.05 max — S stays
bf16-exact);
LSE tests (log2-domain, f32 logsumexp references) covering windowed,
ragged
varlen, ALiBi, and sink variants, with the output tensor bit-identical
between LSE and non-LSE runs.

## Performance vs trtllm-gen

B200 (SM100a), torch 2.11+cu130, `nvidia-cutlass-dsl` 4.6.0. CUPTI
kernel-only, median of 30 iters, cold L2; each cell benches both
backends
back-to-back in one process, median of 3 passes, single node and
session.
GQA 32/8 heads, head_dim 128, bf16. cute-dsl =
`BatchPrefillWithRaggedKVCacheWrapper(backend="cute-dsl")`, i.e. what
the
public wrapper runs per mask kind: vendored route for unmasked/causal,
modular kernel for windows. trtllm-gen = paged wrapper, HND, page 16,
preallocated output. Ratio = cute-dsl / trtllm (< 1: cute-dsl faster).
GPU clocks are not lockable on these nodes, so absolute times are only
comparable within a table (each table is built from back-to-back
same-process measurements; the ratios are clock-robust).

Modular vs vendored, why windows route to the modular kernel (B=1 S=16K,
median of 3 passes):

| config | modular (µs) | vendored (µs) | modular/vendored |
|--|--:|--:|:--:|
| unmasked | 3540.4 | 2893.8 | 1.22 |
| causal | 1808.3 | 1532.7 | 1.18 |
| causal + w=127 | 265.0 | 359.8 | 0.74 |
| causal + w=511 | 314.4 | 620.9 | 0.51 |
| causal + w=1023 | 412.0 | 748.1 | 0.55 |

Shape grid (increasing S; per shape: unmasked, causal, windows in
increasing
size). The kernel column shows which kernel the wrapper routes to:
windowed
rows run this PR's modular path; unmasked/causal rows run the #3857
vendored
kernel and are included for context only.

| B | S | mask | kernel | cute-dsl (µs) | trtllm (µs) | ratio |
|--:|--:|--|--|--:|--:|:--:|
| 64 | 512 | unmasked | vendored | 330.9 | 280.8 | 1.18 |
| 64 | 512 | causal | vendored | 511.7 | 269.4 | 1.90 |
| 64 | 512 | w=256 | modular | 570.9 | 300.6 | 1.90 |
| 16 | 1024 | unmasked | vendored | 249.9 | 236.4 | 1.06 |
| 16 | 1024 | causal | vendored | 318.9 | 185.7 | 1.72 |
| 16 | 1024 | w=256 | modular | 302.7 | 169.2 | 1.79 |
| 1 | 4096 | unmasked | vendored | 201.8 | 227.4 | 0.89 |
| 1 | 4096 | causal | vendored | 159.3 | 150.0 | 1.06 |
| 1 | 4096 | w=256 | modular | 76.4 | 52.5 | 1.46 |
| 1 | 4096 | w=1024 | modular | 115.6 | 87.9 | 1.32 |
| 1 | 4096 | w=2048 | modular | 151.1 | 121.0 | 1.25 |
| 4 | 4096 | unmasked | vendored | 824.4 | 825.0 | 0.99 |
| 4 | 4096 | causal | vendored | 557.9 | 483.7 | 1.15 |
| 4 | 4096 | w=256 | modular | 288.3 | 172.4 | 1.67 |
| 4 | 4096 | w=1024 | modular | 428.5 | 284.5 | 1.51 |
| 4 | 4096 | w=2048 | modular | 519.2 | 399.7 | 1.30 |
| 1 | 16384 | unmasked | vendored | 2845.0 | 3376.5 | 0.86 |
| 1 | 16384 | causal | vendored | 1568.4 | 1758.7 | 0.86 |
| 1 | 16384 | w=256 | modular | 292.8 | 178.1 | 1.62 |
| 1 | 16384 | w=1024 | modular | 415.0 | 304.8 | 1.36 |
| 1 | 16384 | w=2048 | modular | 576.9 | 480.3 | 1.20 |
| 1 | 16384 | w=4096 | modular | 881.7 | 808.0 | 1.09 |
| 1 | 16384 | w=8192 | modular | 1402.0 | 1314.6 | 1.06 |
| 1 | 32768 | unmasked | vendored | 12151.0 | 13847.2 | 0.88 |
| 1 | 32768 | causal | vendored | 6353.5 | 7176.0 | 0.89 |
| 1 | 32768 | w=256 | modular | 580.1 | 334.8 | 1.77 |
| 1 | 32768 | w=1024 | modular | 798.7 | 603.6 | 1.33 |
| 1 | 32768 | w=2048 | modular | 1145.3 | 983.6 | 1.16 |
| 1 | 32768 | w=4096 | modular | 1955.4 | 1740.8 | 1.11 |
| 1 | 32768 | w=8192 | modular | 3443.3 | 3392.4 | 1.01 |

Window-size sweep (B=1, S=16384):

| window | cute-dsl (µs) | trtllm (µs) | ratio |
|--:|--:|--:|:--:|
| 127 | 236.2 | 145.6 | 1.62 |
| 255 | 269.7 | 167.9 | 1.61 |
| 511 | 312.9 | 216.8 | 1.44 |
| 1023 | 411.3 | 304.6 | 1.35 |
| 2047 | 578.0 | 480.0 | 1.20 |
| 4095 | 883.8 | 804.9 | 1.10 |
| 8191 | 1387.7 | 1320.7 | 1.04 |

Mixed V dtype (bf16 Q/K + fp8 V, B=1 S=8192, same protocol): mixed
inputs
force the vendored path onto JIT compilation (its prebuilt artifact
matrix
has no mixed-dtype axis), where the modular kernel also wins causal:

| config | modular (µs) | vendored-JIT (µs) | modular/vendored |
|--|--:|--:|:--:|
| unmasked | 739.4 | 706.3 | 1.05 |
| causal | 481.8 | 548.1 | 0.88 |
| causal + w=127 | 117.7 | 183.9 | 0.64 |
| causal + w=1023 | 208.4 | 395.2 | 0.53 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added flexible attention band masking, including causal, symmetric,
left-only, and right-bounded sliding windows.
* Added optional log-sum-exp (LSE) output, including variable-length,
ALiBi, and attention-sink scenarios.
  * Added support for mixed Q/K/V data types in prefill attention.
  * Added automatic scale selection when no scale is provided.
* **Bug Fixes**
* Improved kernel selection and fallback behavior for windowed attention
and unsupported data-type combinations.
* **Tests**
* Expanded coverage for masking, FP8, mixed dtypes, LSE results, and
ragged inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [3e7106f](https://github.com/flashinfer-ai/flashinfer/commit/3e7106f5dcb6b37a6e2d94f67c886ae5f997a84b)

- **作者**: Brian K. Ryu
- **时间**: 2026-07-24T20:29:49Z
- **提交信息**: chore: Add Anerudhan to comm codeowner (#4135)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Add @Anerudhan to communication kernel code owners.

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
* Updated review ownership for communication-related code and tests to
include an additional required reviewer.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [80c8e70](https://github.com/flashinfer-ai/flashinfer/commit/80c8e70febbfa310724726a588905802f262d262)

- **作者**: Lee Yongjun
- **时间**: 2026-07-24T20:22:05Z
- **提交信息**: feat: fused FP8 quantization output for LayerNorm (#3962)

<!-- .github/pull_request_template.md -->

## 📌 Description

FlashInfer provides fused norm + FP8 quantization for the RMSNorm family
(`rmsnorm_quant`, `fused_add_rmsnorm_quant`), but not for LayerNorm.
Models that use LayerNorm (OPT, Falcon, BERT family, ViT/DiT variants,
Whisper/CLIP style encoders) currently have to run layernorm and
quantization as two kernels, which costs about 7 bytes of traffic per
element instead of 3.

The kernel side is already there: `generalLayerNorm` in
`include/flashinfer/norm.cuh` implements per-tensor and per-token
quantization paths, but the `LayerNorm` host launcher passes nullptr for
all quant arguments, with a note:

    // TODO(kaixih): add support for fp8 quantization if needed

This PR connects the existing per-tensor path rather than writing a new
kernel, so the diff stays small.

- Adds `flashinfer.layernorm_quant(out, input, gemma, beta, scale,
eps)`. Output dtype (float8_e4m3fn or float8_e5m2) is taken from the
preallocated `out` tensor, same as `rmsnorm_quant`.
- Adds fp8 `QuantTypeStaticVals` specializations (constants match
TRT-LLM `quantTypeUtils.cuh`) and the missing e5m2 `cuda_cast`
specializations. The FP8 dispatch macro instantiates both e4m3 and e5m2,
so the e5m2 casts are needed for compilation.
- Adds a `LayerNormQuant` host launcher, guarded by `ENABLE_FP8`. The
csrc launcher keeps a non-FP8 build working
(`test_norm_compilation_without_fp8` passes).
- Changes the per-tensor scale in `generalLayerNorm` to be applied as
division (`out = normed / scale`). The kernel originally multiplied, but
this path was unreachable from every existing call site (the pointer is
always nullptr), so no current behavior changes. Keeping the multiply
semantics would make `layernorm_quant` and `rmsnorm_quant` disagree on
what `scale` means, which seemed worse for fusion passes that target
both. Happy to adjust if there is a concern I am missing here.
- Trace template, docs entry, tests, and a `layernorm_quant` benchmark
routine.
## Performance

RTX 5090, bf16 input, e4m3 output, eps 1e-6. Fused kernel vs. unfused
baseline (`flashinfer.layernorm` followed by eager torch
div/clamp/cast), median over 100 iterations under CUDA graph:

| batch | hidden | unfused (us) | fused (us) | speedup |
|------:|-------:|-------------:|-----------:|--------:|
|   256 |   4096 |         13.2 |        6.9 |   1.91x |
|  1024 |   4096 |         36.9 |       21.4 |   1.73x |
|  4096 |   4096 |        178.9 |       71.8 |   2.49x |
|   256 |   8192 |         21.1 |        8.4 |   2.52x |
|  1024 |   8192 |         69.2 |       24.9 |   2.77x |
|  4096 |   8192 |        499.6 |       80.6 |   6.20x |
|  1024 |  16384 |        167.2 |       43.8 |   3.82x |
|  4096 |  16384 |       1066.5 |      148.7 |   7.17x |

The eager baseline materializes intermediate tensors for div/clamp/cast,
so large shapes gain more than the pure traffic ratio (7B vs 3B per
element, about 2.3x). At batch 4096 / hidden 16384 the fused kernel
reaches about 1.35 TB/s on this card.

Reproduce with:

python benchmarks/flashinfer_benchmark.py --routine layernorm_quant \
        --batch_size 1024 --hidden_size 4096 --refcheck

## 🔍 Related Issues

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

- `tests/utils/test_norm.py::test_layernorm_quant`: e4m3 and e5m2, batch
1 to 989, hidden 111 to 16384 (odd sizes cover the non-vectorized path),
scale 0.01/1.0/10.0, tolerance rtol=1/atol=1 following the existing FP8
norm tests. 168 cases pass.
- `test_layernorm_quant_invalid_inputs`: rejects fp16 input,
non-contiguous input, and non-scalar scale.
- `test_norm_compilation_without_fp8` passes unchanged (norm module
still builds without `ENABLE_FP8`).
- Full `tests/utils/test_norm.py` passes (2887 tests).
- `pytest tests/trace/` template consistency and end-to-end tests pass
for the new trace.
- CUDA graph capture/replay smoke test passes; scale is read on device
at kernel execution time, so updating the scale tensor between replays
works.

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added `flashinfer.layernorm_quant` (LayerNorm + FP8 quantization) with
CUDA support across supported compute capabilities.
* Exposed the API at both `flashinfer.norm` and the top-level
`flashinfer` namespace.
* Added benchmark and trace coverage for the quantized LayerNorm
operation.
* **Documentation**
  * Updated normalization API docs to include `layernorm_quant`.
* **Tests**
* Added correctness/invalid-input tests, plus trace example coverage and
expected outputs for `layernorm_quant`.
* **Bug Fixes**
* Improved trace output dtype resolution when traced tensors are not
available.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [cea7f46](https://github.com/flashinfer-ai/flashinfer/commit/cea7f46ffc190cabf82c95a39cd0d2aa6c888c17)

- **作者**: elvischenv
- **时间**: 2026-07-24T17:13:42Z
- **提交信息**: comm: multicast-free (IPC) workspace for TRT-LLM AR fusion under Confidential Computing (#3993)

## Motivation

Under NVIDIA Confidential Computing (CC), the symmetric-memory
allocator's `cuMulticast` setup fails (the bounce-buffer path can't
complete the fabric/multicast rendezvous), so the TRT-LLM
AllReduce-fusion workspace can't be created the usual way.

## What this changes

`create_allreduce_fusion_workspace` / `TRTLLMAllReduceFusionWorkspace`
now allocate a **multicast-free IPC workspace** instead of symmetric
device memory whenever CC is detected — auto-detected via
`is_confidential_compute()` (overridable with
`FLASHINFER_CONFIDENTIAL_COMPUTE`).

- The trtllm one-shot Lamport and two-shot sync fusion kernels are
**both multicast-free** (0 `multimem` in `trtllm_allreduce_fusion.cuh`),
and the IPC workspace is sized identically to the symmetric one, so both
strategies run on it — only the allocator differs.
- The shorter `(ipc_handles, workspace_tensor, metadata)` return tuple
is handled, and `mem_handles` is set to `[]` so the "handles attached?"
guard in `allreduce_fusion` and `destroy()` iterate a no-op.
- The `mnnvl` backend requires NVLink multicast (unavailable under CC),
so `create_allreduce_fusion_workspace` raises there rather than failing
deep inside workspace creation.

## Tests

`tests/comm/test_allreduce_unified_api.py`:
- **`test_allreduce_trtllm_multicast_free`** — forces CC via
`FLASHINFER_CONFIDENTIAL_COMPUTE=1`, exercising both kernels
(`use_oneshot` True/False), both AR patterns, and fp16/bf16.
- **`test_mnnvl_raises_under_cc`** — asserts the mnnvl+CC guard.

Verified 17/17 on 2×B200.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3879
- **最后更新**: 2026-07-24T06:37:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34145
- **最后更新**: 2026-07-24T21:21:07Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Sayak Paul, Atharva Joshi, YiYi Xu

## AI分析总结

以下是昨日（基于提交记录日期）`huggingface/diffusers` 仓库的更新要点总结：

### 1. 主要更新类型
- **功能新增**：Cosmos3 模型并行支持（上下文并行 + 张量并行）
- **测试增强**：组件管理器测试
- **重构**：清理未使用的中间输入（`modular` 相关）
- **CI/修复**：vq_diffusion 转换器 token 忽略及下载链接更正

### 2. 关键变更点与项目方向关系
- **Cosmos3 模型并行（#14054）**：为大型模型（如 Cosmos3 Super，~120GB）实现多 GPU 推理，支持上下文并行（Ulysses）和张量并行（Megatron）。这一方向与 HuggingFace Diffusers 社区对大规模视频/3D 模型高效推理的需求一致，扩展了框架对超大模型的支持能力。
- **组件管理器测试（#13961）**：增强对组件管理器的单元测试，提升框架的模块化可维护性，确保内部组件拆分正确。
- **清理未使用中间输入（#14278）**：优化 `modular` 模块代码，减少冗余，改善代码整洁度。
- **vq_diffusion 转换器修复（#14275）**：规避转换器对 token 的误处理，改用官方下载链接，提升转换可靠性。

### 3. 对项目的影响与潜在意义
- **Cosmos3 并行支持**：使得 HuggingFace Diffusers 能够运行超大规模权重模型，拓宽了视频生成/3D 等领域应用场景；同时保持单 GPU 行为不变，兼容性好。
- **测试覆盖提升**：组件管理器测试减少了模块化重构的回退风险，为未来更复杂的模型架构（如流水线并行、分层组件）奠定基础。
- **代码质量改进**：中间输入清理和 VQ-Diffusion 修复均属稳定性与可维护性优化，降低长期维护成本。

### 4. 值得关注的技术点
- **Cosmos3 并行方案规避了框架现有 `_cp_plan` 路径**：由于 Cosmos3 拥有分组查询注意力（GQA）和分流的理解/生成序列，无法直接复用官方上下文并行接口，而是通过注入 `_cp_shard_fn` / `_cp_gather_fn` 钩子以及独立处理器实现。这展示了在复杂模型上扩展并行支持的通用模式。
- **性能关键设计**：将 KV 头扩展为查询头数量，并使用 `enable_gqa=False` 迫使 SDPA 使用 Flash Attention 内核，避免因 `enable_gpu=True` 导致完整注意力矩阵内存溢出（OOM）。
- **权重加载优化**：张量并行下，权重先加载到 CPU 再逐层分片，避免单 GPU 显存不足。

### 5. 对项目发展的影响
- **强化大规模模型支持**：Cosmos3 的并行方案为后续类似超大规模扩散模型（如视频、多模态）提供了可复用的参考示例（`examples/cosmos3/cosmos_parallel.py`），推动 Diffusers 向“支持任意规模模型高效推理”的方向演进。
- **模块化与测试文化**：组件管理器测试和清理工作表明项目正在持续优化内部架构，为未来更灵活的组件组合（如 LoRA、ControlNet 与并行混合使用）打好基础。
- **生态兼容性**：vq_diffusion 的修复和示例文档更新保持了与官方模型转换链的兼容，巩固了用户对仓库稳定性的信任。

## 详细提交记录

### [ed58810](https://github.com/huggingface/diffusers/commit/ed58810cb940e4e38e3d730b4b9c75d4db39cd4f)

- **作者**: YiYi Xu
- **时间**: 2026-07-24T20:41:29Z
- **提交信息**: [modular] clean up unused intermediate_inputs (#14278)

upp

### [9f492ca](https://github.com/huggingface/diffusers/commit/9f492ca9676f6b775dd661978144b607e2d58e66)

- **作者**: Sayak Paul
- **时间**: 2026-07-24T17:32:50Z
- **提交信息**: [tests] component manager tests (#13961)

* component manager tests

* remove unneeded comments.

* remove component test mixin from flux modular test

* minor

### [6ad3573](https://github.com/huggingface/diffusers/commit/6ad357395d936c4d27347463f938cdbb400a6e59)

- **作者**: Atharva Joshi
- **时间**: 2026-07-24T08:56:44Z
- **提交信息**: Cosmos3 Model Parallelism (#14054)

* feat(cosmos3): multi-GPU inference — context + tensor parallelism

Cosmos 3 cannot use diffusers' declarative `_cp_plan` CP path: it is grouped-query
attention (the shared Ulysses kernel assumes K/V share the query head count), its
understanding (causal) and generation (full) streams are separate packed sequences
(gen attends to cat(und, gen)), and per-pathway lengths are ragged. The model carries
no parallelism logic -- it exposes only small, CP-agnostic seams; all sharding lives
outside it, in a reusable example module.

Model (transformer_cosmos3.py): adds two default-None `forward` seams -- `_cp_shard_fn`
(shards und/gen + rotary before the decoder layers) and `_cp_gather_fn` (gathers/unpads
after the final norm) -- and extracts `Cosmos3AttnProcessor._run_attention` as an
override point. The non-parallel path is unchanged.

Helpers (examples/cosmos3/cosmos_parallel.py): one importable module, two orthogonal
and composable axes:
  * Context parallelism (Ulysses) -- `enable_cosmos3_context_parallel`. Shards the
    sequence; brackets the two attention pathways with all-to-all (DTensor redistribute),
    repeats GQA KV heads, pads ragged lengths and masks padded generation keys.
  * Tensor parallelism (Megatron) -- `enable_cosmos3_tensor_parallel`. Column/row-shards
    the attention + MLP weights so a checkpoint that does not fit one GPU (Super, ~120 GB)
    loads across several; weights load to CPU then shard layer by layer.
Both expand KV heads to the query-head count and call SDPA with enable_gqa=False so it
dispatches to the flash kernel; enable_gqa=True forces the math path, which materializes
the full [S, S] score matrix and OOMs on long videos. A dense `Cosmos3FlashAttnProcessor`
(`enable_cosmos3_flash_attention`) provides the same for TP without CP.

CLI (examples/cosmos3/inference_cosmos3.py): imports these helpers, so any modality
(text-to-image/video, image-to-video, sound, action) runs single- or multi-GPU via
`--tp-degree` / `--cp-degree` (their product must equal --nproc_per_node). Single-GPU
behavior is unchanged.

Docs + example README updated. Verified: CP attention core is bit-exact vs non-CP in
fp32 (max|d|=0), and a full 36-layer forward matches CP-on vs CP-off to ~1e-6 in fp32
(bf16 differs only by floating-point rounding).

* refactor(cosmos3): make CP/TP attention processors standalone

Address review feedback on PR #14054: the parallel attention processors no
longer subclass Cosmos3AttnProcessor, so the model file needs no override seam.

- transformer_cosmos3.py: revert Cosmos3AttnProcessor to inline the attention
  in __call__ (remove the _run_attention seam); restores it to its base version.
- cosmos_parallel.py: Cosmos3CPAttnProcessor and Cosmos3FlashAttnProcessor each
  get their own full __call__, sharing a _project_qkv_with_rope prologue helper.

Verified behavior-preserving on 4x RTX PRO 6000: cp_unit_test (fp32) passes at
1e-4; cp_numeric_check is byte-identical to the pre-refactor code; the end-to-end
CLI passes in CP-only, TP-only, and TP+CP modes.

* fix(cosmos3): support modular multi-GPU inference

### [7156122](https://github.com/huggingface/diffusers/commit/7156122b1d175a5f3cf9292f4ab403d7806082f9)

- **作者**: Sayak Paul
- **时间**: 2026-07-24T08:23:16Z
- **提交信息**: [ci] ignore the token in vq_diffusion converter. (#14275)

* ignore the token in vq_diffusion converter.

* change to regular official download link

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
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


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12752
- **最后更新**: 2026-07-24T18:36:50Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Artiprocher, Zhongjie Duan

## AI分析总结

根据您提供的提交记录和项目背景，总结如下：

### 1. 主要更新类型
- **功能新增**：新增“时间步感知LoRA”（Timestep-aware LoRA）支持。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：通过PR #1538合并，实现了一个能够根据扩散模型采样时间步动态调整LoRA权重的机制。
- **与项目方向**：DiffSynth-Studio作为面向扩散模型的合成/编辑工具，LoRA是常用的轻量级微调方法。传统LoRA的时间步无关性可能导致不同生成阶段的控制能力不足；引入时间步感知后，可在去噪早期和后期施加不同的影响，从而更精细地控制生成内容或风格，符合项目提升生成可控性和质量的核心目标。

### 3. 对项目的影响和潜在意义
- **模型微调灵活性提升**：允许用户在扩散过程不同阶段施加不同的LoRA作用强度，可能改善时序生成（如视频、动画）的一致性。
- **用户体验优化**：为高级用户提供更细粒度的调控选项，有望在风格迁移、条件控制等场景产出更自然的结果。
- **生态拓展**：增强项目在LoRA变体研究中的竞争力，吸引更多研究人员和开发者使用该框架进行实验。

### 4. 值得关注的技术点
- **时间步编码与LoRA的融合方式**：需关注如何将时间步信息嵌入到LoRA的低秩矩阵中（如时间步embedding与LoRA权重的乘法或加法相互作用）。
- **性能开销**：相比标准LoRA，动态计算可能增加少量推理/训练耗时，需评估实际效率。
- **兼容性**：是否支持预训练的现有LoRA权重转换，或是否需要重新训练。

### 5. 对项目发展的影响
- **技术领先性**：DiffSynth-Studio明确表明支持前沿的LoRA变体（如Timestep-aware LoRA），有助于吸引关注扩散模型可解释性和可控性的社区用户。
- **项目定位强化**：README中提及PyPI安装，该功能有望成为新版发布的亮点，强化项目“即开即用、先进功能”的定位。
- **潜在下游应用**：对视频合成、动画生成等时间维度敏感的任务尤为关键，可能推动项目在影视、创意内容生成领域的实用化。

**总结**：本次更新是功能类增强，聚焦于扩散模型生成过程中的动态控制能力，与项目提升生成质量和用户可控性的方向高度一致，具有显著的学术和应用价值。

## 详细提交记录

### [a182384](https://github.com/modelscope/DiffSynth-Studio/commit/a182384c17dcca0f97bed0f942dce85d8c0deb6a)

- **作者**: Zhongjie Duan
- **时间**: 2026-07-24T09:20:49Z
- **提交信息**: Merge pull request #1538 from modelscope/multialign

Support Timestep-aware LoRA

### [250ee0c](https://github.com/modelscope/DiffSynth-Studio/commit/250ee0cff36e10e983af78c1c391e3c69edc3f9f)

- **作者**: Artiprocher
- **时间**: 2026-07-24T09:14:52Z
- **提交信息**: support Timestep-aware LoRA

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30711
- **最后更新**: 2026-07-24T22:10:01Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 21
- **主要提交者**: Zheng Wengang, Jun Liu, cctry

## AI分析总结

### 昨日更新要点总结（基于 sgl-project/sglang 仓库提交记录）

#### 1. 主要更新类型
- **功能新增**：FP4 Indexer（DeepSeek V4）、HPC-Ops FP8 MoE后端、Leveled invariant-check、DCP A2A通信后端、确定性EAGLE rejection采样
- **Bug修复**：DS/Kimi PP rank崩溃、Kimi-Linear异构TP传输、flashinfer-MLA回退污染、NPU内存泄漏、MoE输出in-place覆盖、safetensors索引缺失、dspark draft钳制、在线权重更新冲突
- **性能/稳定性优化**：写回策略修复、StagingBuffer鲁棒性、EPD接收器强化、multi-tokenizer指标修复
- **CI/测试**：跳过flaky测试、新增FP8 8-GPU nightly测试、XPU平台测试修复、CI权限管理
- **版本升级**：sgl-deep-gemm 0.1.5
- **其他**：chore（verbose twine）、rust server环境FSM错误ID生成

#### 2. 关键变更点与项目方向的关系
- **DeepSeek V4 支持强化**：多个提交聚焦 DeepSeek V4 的推理优化（FP4 Indexer、topk_transform_512、top-k renormalization epsilon），符合项目对最新模型的快速适配。
- **MoE 与 FP8 生态扩展**：HPC-Ops FP8 MoE后端、DSATopKBackend、sgl-deep-gemm更新，呼应项目在低精度和混合专家模型上的性能追求。
- **确定性推理与稳定性**：Kimi deterministic EAGLE采样、Leveled invariant-check、StagingBuffer故障处理，体现项目对可复现性和生产可靠性的重视。
- **异构与多后端兼容**：修复NPU Ascend内存、XPU测试、FlashInfer-MNNVL通信后端，巩固项目跨平台能力。
- **Disaggreg

## 详细提交记录

### [4ececf2](https://github.com/sgl-project/sglang/commit/4ececf2b1d380a0b16994e545c85b4f1d6ffe297)

- **作者**: Qiaolin Yu
- **时间**: 2026-07-24T21:54:07Z
- **提交信息**: [chore] Add verbose flag to twine upload command (#32349)

### [f7986c8](https://github.com/sgl-project/sglang/commit/f7986c8603f7f665eb48e280c3b1fb0228f71e45)

- **作者**: Zhihao Wang
- **时间**: 2026-07-24T21:45:44Z
- **提交信息**: [RL] DSV4: dispatch indexer topk_transform_512 through DSATopKBackend (#31087)

Signed-off-by: zhihaow6 <zhihaow6@illinois.edu>

### [8727d10](https://github.com/sgl-project/sglang/commit/8727d105db67fde93414f9163e503b4e700fee2d)

- **作者**: cctry
- **时间**: 2026-07-24T21:04:54Z
- **提交信息**: Add prefill and decode load counters to LoadSnapshot (#32245)

### [f15b432](https://github.com/sgl-project/sglang/commit/f15b43242b43adc5ec810be2e9978267bf64b990)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-24T21:03:38Z
- **提交信息**: Bump sgl-deep-gemm to 0.1.5 (#32345)

### [be7cc17](https://github.com/sgl-project/sglang/commit/be7cc173075c1c906f9a6589d04ba20eb03064d5)

- **作者**: Rain Jiang
- **时间**: 2026-07-24T20:55:10Z
- **提交信息**: sglang rust server environ fsm error id gen (#32240)

### [82fe0f0](https://github.com/sgl-project/sglang/commit/82fe0f041aec90b560fb39b8c1c2687b9dd0029e)

- **作者**: Qiaolin Yu
- **时间**: 2026-07-24T20:24:26Z
- **提交信息**: Fix stale flashinfer-MLA fallback poisoning spec verify capture (trtllm_mla + tc_piecewise) (#32288)

### [be7c13a](https://github.com/sgl-project/sglang/commit/be7c13af07cd93cf1967bdac61d8aa484af7e9e2)

- **作者**: Zheng Wengang
- **时间**: 2026-07-24T19:19:02Z
- **提交信息**: [BugFix] Fix DS/Kimi crash on non-first PP ranks when resolving input length (#31752)

### [71015f3](https://github.com/sgl-project/sglang/commit/71015f3fea7c3e40df73560ec849ccb3cb4f898a)

- **作者**: mosya415
- **时间**: 2026-07-24T19:10:38Z
- **提交信息**: fix(dsa): fail fast on fp8_e4m3 KV with tilelang DSA backend on CUDA (#31346)

Co-authored-by: mosya415 <263250241+mosya415@users.noreply.github.com>

### [1e69765](https://github.com/sgl-project/sglang/commit/1e69765bae5be01ce4a6dc3515d552c85dc832f6)

- **作者**: Jinyan Chen
- **时间**: 2026-07-24T18:37:23Z
- **提交信息**: Add FP4 Indexer for DeepSeek V4 on SM120 (#27059)

### [2428f56](https://github.com/sgl-project/sglang/commit/2428f5614561c9e3990782e99a76bfaaff56324c)

- **作者**: YAMY
- **时间**: 2026-07-24T17:31:17Z
- **提交信息**: [Bugfix] Fix Kimi-Linear state transfer across heterogeneous TP (#32262)

### [5da0b6e](https://github.com/sgl-project/sglang/commit/5da0b6ec39bd5014eead140f81967f837d3cc83b)

- **作者**: Zhiqiang Xie
- **时间**: 2026-07-24T16:58:18Z
- **提交信息**: Write-back policy fix for unified tree (#31845)

### [448662e](https://github.com/sgl-project/sglang/commit/448662e85e325f830cb2d1d423fa23099677cee4)

- **作者**: Lu Fang
- **时间**: 2026-07-24T15:27:24Z
- **提交信息**: [mm] Accept per-item embedding lists from DataEmbeddingFunc (#31826)

### [fa243fe](https://github.com/sgl-project/sglang/commit/fa243fee401c5c1fcaa8faa85d73dd8168f5cc4a)

- **作者**: Shangming Cai
- **时间**: 2026-07-24T13:59:20Z
- **提交信息**: [CI] Skip flaky test in CI for disaggregation group (#32324)

### [dfaf75b](https://github.com/sgl-project/sglang/commit/dfaf75b1a69e1dafaed89e78273f0cef1f452dba)

- **作者**: khalilzhk
- **时间**: 2026-07-24T13:13:21Z
- **提交信息**: [NPU] bugfix for extra device memory on Ascend (#30112)

### [3d91a56](https://github.com/sgl-project/sglang/commit/3d91a569ce480f5548ca836799e84b7ee7fe97c4)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-24T11:46:11Z
- **提交信息**: [MoE Backend] Add HPC-Ops FP8 MoE runner backend (#30541)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Halcyon <56064364+VAthree@users.noreply.github.com>

### [4d5917e](https://github.com/sgl-project/sglang/commit/4d5917e744578184237288c62c54a2035f69c72f)

- **作者**: Jun Liu
- **时间**: 2026-07-24T11:45:44Z
- **提交信息**: Add DeepSeek-reference 1e-20 epsilon to top-k renormalization to prevent 0/0 NaN (#31017)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [8389d79](https://github.com/sgl-project/sglang/commit/8389d79e43af729da74bea0dd9d5550f9684c6d3)

- **作者**: 王鹤男
- **时间**: 2026-07-24T11:45:28Z
- **提交信息**: ci: add LongCat-Flash-Lite-FP8 8-GPU nightly test + fix NextN rope_theta (#32125)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [841fa29](https://github.com/sgl-project/sglang/commit/841fa293b55a0e1bbbf30fc709d2d45333847259)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-24T11:30:13Z
- **提交信息**: [Fix] Reject online weight updates while the HPC-Ops router GEMM split cache is active (#31943)

Co-authored-by: Halcyon <56064364+VAthree@users.noreply.github.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [a31542e](https://github.com/sgl-project/sglang/commit/a31542ebd974b5a71d2085d88756760c1d925773)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-24T11:27:20Z
- **提交信息**: [Feature] Add leveled invariant-check primitive for nan/inf/oob validity checks (#32308)

### [de816e1](https://github.com/sgl-project/sglang/commit/de816e1eb53e12e1538df47d300ad0a74e63c54e)

- **作者**: YAMY
- **时间**: 2026-07-24T09:22:55Z
- **提交信息**: [Disagg][StagingBuffer][1/2] Robustness and failure handling (#31217)

### [34d02ba](https://github.com/sgl-project/sglang/commit/34d02bae470925a9464cdfb99112a589c39c6a2c)

- **作者**: Shangming Cai
- **时间**: 2026-07-24T09:20:15Z
- **提交信息**: Add CI permissions for Elastic EP contributor UNIDY2002 (#32306)

### [f4f1516](https://github.com/sgl-project/sglang/commit/f4f15162bc1250dd72191ac079103f6b334333ab)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-24T09:18:56Z
- **提交信息**: [Fix] Fail fast when a safetensors index references missing shard files (#32279)

### [b954e9c](https://github.com/sgl-project/sglang/commit/b954e9cf3dad048d8c198d622320c3a44f3ef2a9)

- **作者**: Yuzhen Zhou
- **时间**: 2026-07-24T09:11:21Z
- **提交信息**: [6/6][kimi-deterministic] Use deterministic seeded coins for EAGLE rejection sampling (#30822)

### [3849beb](https://github.com/sgl-project/sglang/commit/3849beb7e353226597afef452bcc42b9e5d2e65d)

- **作者**: Ethan (Yusheng) Su
- **时间**: 2026-07-24T08:42:36Z
- **提交信息**: [CI] Fix XPU platform test on machines without the XPU sgl-kernel op (#32298)

### [364b5f2](https://github.com/sgl-project/sglang/commit/364b5f23e65f5e7041d824fed402814efd84b0ba)

- **作者**: Zheng Wengang
- **时间**: 2026-07-24T08:37:52Z
- **提交信息**: [BugFix][EPD] Harden zmq_to_scheduler receiver failures; sync error info across TP (#31592)

Co-authored-by: siyu <liusy58@linux.alibaba.com>

### [58f4170](https://github.com/sgl-project/sglang/commit/58f417049d8a387c3d24e165696c0792c7c97716)

- **作者**: Jun Liu
- **时间**: 2026-07-24T08:27:21Z
- **提交信息**: [PD] Fix multi-tokenizer disaggregation metrics labels (#30412)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [b8bb1b4](https://github.com/sgl-project/sglang/commit/b8bb1b4e5a9443e6190b42bf87f7f1bc108a608d)

- **作者**: Sam Shleifer
- **时间**: 2026-07-24T07:58:55Z
- **提交信息**: [lora] Fix WAR race: never write MoE runner output into hidden_states in place (#31870)

### [d059b0f](https://github.com/sgl-project/sglang/commit/d059b0f56eaa44dd0edc34318316258b723e1fa4)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-24T07:53:56Z
- **提交信息**: [Fix] Clamp degenerate all-sentinel draft rows to token 0 in dspark `_online_combine_kernel` (#32277)

### [35e25f5](https://github.com/sgl-project/sglang/commit/35e25f53567c3290f3d96aebc21019b87ced710f)

- **作者**: Thanhhao
- **时间**: 2026-07-24T07:21:53Z
- **提交信息**: [Feature] DCP: A2A + FlashInfer-MNNVL comm backends and q-replicate (Helix) (#21637)

Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1238
- **最后更新**: 2026-07-24T12:46:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 87087
- **最后更新**: 2026-07-24T22:19:52Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 18
- **主要提交者**: Oxana Korzh, Harry Mellor, Andreas Karatzas

## AI分析总结

分析生成失败

## 详细提交记录

### [33c4f35](https://github.com/vllm-project/vllm/commit/33c4f3551ce9b4dc75864f16c40496d8d64f8e9d)

- **作者**: Aarushi Jain
- **时间**: 2026-07-24T22:19:46Z
- **提交信息**: [ROCm][CI] Wait for ROCm VRAM to settle between compiled and eager LL… (#49739)

Signed-off-by: aarushjain29 <Aarushi.Jain2@amd.com>

### [caa9cad](https://github.com/vllm-project/vllm/commit/caa9cad31ea2e577ac34f8695014f81f53c89e26)

- **作者**: Rohan Potdar
- **时间**: 2026-07-24T21:14:03Z
- **提交信息**: [ROCm][Docker] Drop MORI_GPU_ARCHS so MoRI autodetects the device arch (#49737)

Signed-off-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [7513d07](https://github.com/vllm-project/vllm/commit/7513d071bd749c938181fac9e67ac103d0c52dc1)

- **作者**: djramic
- **时间**: 2026-07-24T21:09:18Z
- **提交信息**: [ROCm][CI] Fix XPASS(strict) on mixed audio embeds test (#49733)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [89f6aa3](https://github.com/vllm-project/vllm/commit/89f6aa3a9e56a9228f55e8d722f23594223187cf)

- **作者**: Harry Mellor
- **时间**: 2026-07-24T20:56:57Z
- **提交信息**: [KV Offload][CI] Fall back to buffered I/O without O_DIRECT; fix flaky api-server test (#49734)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [84d26b9](https://github.com/vllm-project/vllm/commit/84d26b9ee3dde1991442539dcf5fc5b26aa08f7e)

- **作者**: Harry Mellor
- **时间**: 2026-07-24T20:54:24Z
- **提交信息**: [Model] Remove Plamo2 (#49729)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [9e6746b](https://github.com/vllm-project/vllm/commit/9e6746b3c7b4ec9bcc234db9a654df8eca5781ce)

- **作者**: Jiangyun Zhu
- **时间**: 2026-07-24T20:45:09Z
- **提交信息**: [CI] Stabilize memory-sensitive compile and structured output tests (#49749)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [972848f](https://github.com/vllm-project/vllm/commit/972848f2764e2f79deb7853320ccf0094be452aa)

- **作者**: Elvir Crnčević
- **时间**: 2026-07-24T20:38:59Z
- **提交信息**: [Bugfix] Support non-uniform page sizes in KVBlockZeroer (#49704)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [2279575](https://github.com/vllm-project/vllm/commit/2279575cd9caeb9174c7ec11a94a34af40903f4d)

- **作者**: Oxana Korzh
- **时间**: 2026-07-24T20:35:27Z
- **提交信息**: [AMD][Bugfix][EPLB] Fix elastic EP scaling accuracy on ROCm (#47206)

Signed-off-by: okorzh <okorzh@amd.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [5d8e90a](https://github.com/vllm-project/vllm/commit/5d8e90a96616c4fe339ff0b0c2a2d470f6eb24bf)

- **作者**: Tyler Michael Smith
- **时间**: 2026-07-24T20:00:02Z
- **提交信息**: [WideEP] Update NCCL to 2.30.7 to enable DeepEPv2 in the vllm/vllm-openai image (#45321)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Signed-off-by: Tyler Michael Smith <tyler@vllm.ai>
Signed-off-by: Tyler Michael Smith <tyler@tylermsmith.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Ilya Markov <ilmarkov@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Codex <noreply@openai.com>

### [e222c33](https://github.com/vllm-project/vllm/commit/e222c33f2f568b54b41d2ebfc44f6c85ea072737)

- **作者**: djramic
- **时间**: 2026-07-24T19:57:49Z
- **提交信息**: [Bugfix] Register axk1 config to fix A.X-K1 init (#49727)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [c064fa5](https://github.com/vllm-project/vllm/commit/c064fa52b6425b17dbc51fea2eaf4aac0f30863f)

- **作者**: Aarushi Jain
- **时间**: 2026-07-24T19:35:16Z
- **提交信息**: Fix GLM-4.1V video placeholder token ID handling. (#49484)

Signed-off-by: aarushjain29 <Aarushi.Jain2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [7e51939](https://github.com/vllm-project/vllm/commit/7e51939e25c34e6527a4971345c95dbefb029fc9)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-24T19:33:53Z
- **提交信息**: [CI] Avoid unnecessary Hugging Face metadata requests (#49508)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [9863102](https://github.com/vllm-project/vllm/commit/9863102ed94a91255cd6b0924027b3d3b985e913)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-24T19:32:40Z
- **提交信息**: [CI] Reuse loaded config for cached tokenizer (#49509)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [8c13ee5](https://github.com/vllm-project/vllm/commit/8c13ee5735f54fe7c653cf694be21bb462a99fed)

- **作者**: Tyler Michael Smith
- **时间**: 2026-07-24T18:59:49Z
- **提交信息**: Add `sm_107` for Rubin (#49387)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [4179806](https://github.com/vllm-project/vllm/commit/41798069f318b88334efdb7778190ce48c1084a4)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-24T18:41:08Z
- **提交信息**: [CI][AMD] Deprecate DinD for MI355 tests (#49257)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [866fea2](https://github.com/vllm-project/vllm/commit/866fea2b9900bf49d552c205d2eaac4716fb63ac)

- **作者**: Johnny-Liou
- **时间**: 2026-07-24T16:39:49Z
- **提交信息**: [Kernel] ReplaySSM: cache SSM inputs for faster Mamba2 standard decode (#48018)

Signed-off-by: Johnny-Liou <a897111@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: tomeras91 <57313761+tomeras91@users.noreply.github.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [d02df74](https://github.com/vllm-project/vllm/commit/d02df748bf9efd99022f1a062597dc3cb3808485)

- **作者**: Thomas Fahrner
- **时间**: 2026-07-24T15:23:08Z
- **提交信息**: [Bugfix] Accept RFC 2397 parameters in base64 data URLs (#48973)

Signed-off-by: Thomas Fahrner <thomas.fahrner@parasail.io>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [453f017](https://github.com/vllm-project/vllm/commit/453f01783d44abc3f325bcc6efadf4246ec18873)

- **作者**: Taneem Ibrahim
- **时间**: 2026-07-24T14:16:39Z
- **提交信息**: [UX] Improve data-parallel launch validation (#49124)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [7b40fb9](https://github.com/vllm-project/vllm/commit/7b40fb96450e1deef40ebc383ff549bea35b9b8f)

- **作者**: Taneem Ibrahim
- **时间**: 2026-07-24T14:16:22Z
- **提交信息**: [UX] Reject incompatible nested runtime overrides (#49247)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [8eac21a](https://github.com/vllm-project/vllm/commit/8eac21a602d4959eb8478c430d7fe1ca5b57311f)

- **作者**: BadrBasowid
- **时间**: 2026-07-24T14:16:17Z
- **提交信息**: [ROCM] Fix AITER Fused AllReduce RMSNorm for Transformers Backend (#49673)

Signed-off-by: BadrBasowid <badr.basowid@gmail.com>

### [a454a1d](https://github.com/vllm-project/vllm/commit/a454a1dd25a181334f6f126b2a2bec3d7c1d9aab)

- **作者**: mgazz
- **时间**: 2026-07-24T11:30:19Z
- **提交信息**: [Bugfix][Benchmarks] Restore --skip-tokenizer-init with custom dataset (#49180)

Signed-off-by: Michele Gazzetti <michele.gazzetti1@ibm.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [833483f](https://github.com/vllm-project/vllm/commit/833483f3578a2c4766977d0fe431bd32a01ce250)

- **作者**: hotTea
- **时间**: 2026-07-24T09:52:00Z
- **提交信息**: Encoder cache extension hooks (#48218)

Signed-off-by: hotTea <958436561@qq.com>
Signed-off-by: hanxi-java <634498162@qq.com>
Co-authored-by: hanxi-java <634498162@qq.com>
Co-authored-by: 韩熙 <63780107+hanxi-java@users.noreply.github.com>

### [163ecba](https://github.com/vllm-project/vllm/commit/163ecba37766e22036d8456a64d9122520647ab7)

- **作者**: li-jinpeng
- **时间**: 2026-07-24T08:53:48Z
- **提交信息**: [Bugfix] Skip linear bias in layerwise reload to avoid corruption (#49586)

Signed-off-by: li-jinpeng <3332126450@qq.com>
Signed-off-by: xymli <xymli@tencent.com>
Co-authored-by: xymli <xymli@tencent.com>

### [589a5b8](https://github.com/vllm-project/vllm/commit/589a5b884bcc9a7662aac4a184529aa68da77436)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-24T08:41:37Z
- **提交信息**: [PD][NixlPush][Bugfix] Fix blocking handshake call on writer thread (#49221)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5c5434e](https://github.com/vllm-project/vllm/commit/5c5434e2d89fe7008ec7a6046faa65a69ba568ca)

- **作者**: Kevin H. Luu
- **时间**: 2026-07-24T08:14:48Z
- **提交信息**: Remove Quantization test parallelism (#49693)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-25
**监控日期**: 2026-07-24
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5682
- **最后更新**: 2026-07-24T22:14:28Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 9
- **主要提交者**: rein yang, TaffyOfficial, wangyu

## AI分析总结

根据昨日提交记录，结合 vllm-omni “Easy, fast, and cheap omni-modality model serving” 的项目定位，总结如下：

---

### 1. 主要更新类型
- **Bug修复**：4 个（Docker镜像升级、K8s包发现路径、Cholesky正定崩溃、异步流计数）
- **性能优化**：3 个（扩散模型编译粒度、MOSS-TTS CUDA Graph重构、MiniCPM-o4.5优化）
- **新功能**：2 个（AllGather-KV序列并行注意力、FLUX.2-dev VAE补丁并行）
- **重构**：2 个（扩散缓存机制、CI统一跳过目标与管道预设）

---

### 2. 关键变更点与项目方向的关系
- **扩散模型编译粒度可配置**（`#4603`）→ 提升扩散模型推理灵活性，适配不同硬件与延迟要求，契合“fast & cheap”目标。
- **AllGather-KV序列并行注意力**（`#4968`）→ 长序列多模态输入（如视频、大图）的显存与计算优化，支撑更大规模模型服务。
- **FLUX.2-dev VAE补丁并行**（`#5292`）→ 扩展对最新扩散模型FLUX的支持，增强多模态模型生态。
- **MOSS-TTS CUDA Graph重构**（`#5197`）→ 降低语音生成推理开销，提升实时交互体验。
- **MiniCPM-o4.5优化**（`#5228`）→ 轻量级多模态模型调优，服务于低成本部署场景。
- **缓存与CI重构**（`#5226`、`#5254`）→ 提升代码可维护性与测试可靠性，间接加速迭代。

---

### 3. 对项目的影响与潜在意义
- **稳定性提升**：修复多项Bug（尤其是序列停止计数、数学库崩溃），保障生产环境可靠性。
- **推理性能边际改善**：扩散编译粒度、CUDA Graph、MiniCPM优化可显著降低延迟，尤其适合实时多模态服务。
- **功能扩展**：
  - 序列并行注意力使长上下文多模态任务（如视频理解、高分辨率图像）成为可能。
  - VAE补丁并行支持FLUX.2-dev，紧跟社区最新模型趋势。
- **基础设施增强**：Docker镜像与CI路径修复解决K8s部署问题，利于多云环境。

---

### 4. 值得关注的技术点
- **AllGather-KV序列并行**：属于Transformer解码优化，与多模态输入中的KV缓存管理直接相关。
- **扩散模型编译粒度**：允许用户按层或子图控制JIT编译，是推进扩散模型生产化的重要设计。
- **MOSS-TTS CUDA Graph**：将动态图转换为静态计算图，减少内核启动开销，对音频生成等低延迟场景关键。
- **FLUX.2-dev VAE补丁并行**：利用并行化加速VAE解码/编码，是扩散模型推理常见瓶颈。

---

### 5. 结合项目背景的整体影响
vllm-omni 定位于“简单、快速、廉价的全模态服务

## 详细提交记录

### [d624074](https://github.com/vllm-project/vllm-omni/commit/d6240742f365cd813991b540b8ea797347aac72e)

- **作者**: akshatvishu
- **时间**: 2026-07-24T18:18:32Z
- **提交信息**: [BugFix][CI] Upgrade ROCm and CUDA docker base images to v0.25.0 (#5115)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>

### [ff0a76e](https://github.com/vllm-project/vllm-omni/commit/ff0a76e31cbdb1f3bc5b0cb11f75ee63d5dbd3ca)

- **作者**: wangyu
- **时间**: 2026-07-24T16:34:30Z
- **提交信息**: [CI/Bugfix] Move CI editable APP_DIR to /opt/vllm-omni for k8s package discovery (#5364) (#5368)

Signed-off-by: wangyu <410167048@qq.com>

### [93786c9](https://github.com/vllm-project/vllm-omni/commit/93786c9cd3edcb0d812051adea1968346001b9b2)

- **作者**: TaffyOfficial
- **时间**: 2026-07-24T15:22:06Z
- **提交信息**: [perf] Add configurable diffusion compile granularity (#4603)

Signed-off-by: TaffyOfficial <2324465096@qq.com>
Co-authored-by: TaffyOfficial <2324465096@qq.com>

### [84bbd57](https://github.com/vllm-project/vllm-omni/commit/84bbd57e4d2f1210527587b8ba53e168902506cb)

- **作者**: Honghan Zhu
- **时间**: 2026-07-24T14:45:26Z
- **提交信息**: [Feature] Add AllGather-KV sequence-parallel attention str… (#4968)

Signed-off-by: zhuhh97 <zhuhonghan@huawei.com>
Signed-off-by: dph97 <nenbaying@163.com>
Signed-off-by: zhuhh97 <zhh@unknown>
Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [8927ec0](https://github.com/vllm-project/vllm-omni/commit/8927ec057c272ca15b11097dc404025b89005055)

- **作者**: Yang_wdrs
- **时间**: 2026-07-24T14:42:45Z
- **提交信息**: [Refactor][1/N]diffusion/cache: cache-dit (#5226)

Signed-off-by: yangjianjuan <66548561+yangjianjuan@users.noreply.github.com>

### [a5d9d57](https://github.com/vllm-project/vllm-omni/commit/a5d9d57adc8ff323dcbbe097fb470967ef4e8c60)

- **作者**: wangyu
- **时间**: 2026-07-24T14:28:43Z
- **提交信息**: [Refactor][CI] Unify skip-ci targeting and mirror_hardwares pipeline presets (#5254)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Signed-off-by: [Your Name] [Your Email]
Co-authored-by: Weiming Liao <fayespica@outlook.com>

### [536daea](https://github.com/vllm-project/vllm-omni/commit/536daea1074159d2ac91aa4dd53e8f1c1510c627)

- **作者**: akshatvishu
- **时间**: 2026-07-24T11:41:56Z
- **提交信息**: [BugFix] Fix Helios Cholesky positive-definite crashes and CPU LAPACK… (#4921)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [784c27f](https://github.com/vllm-project/vllm-omni/commit/784c27f4930127eb37266f0782b84da60772479d)

- **作者**: Viacheslav Klimkov
- **时间**: 2026-07-24T11:31:47Z
- **提交信息**: [Bugfix][Core] Fix async streaming segment-stop accounting (#5183)

Signed-off-by: Viacheslav Klimkov <vklimkov@nvidia.com>

### [c56d0da](https://github.com/vllm-project/vllm-omni/commit/c56d0da1bbd4382c838d807811b95a204d093710)

- **作者**: Canlin Guo
- **时间**: 2026-07-24T11:08:17Z
- **提交信息**: [Perf] Refactor MOSS-TTS-Local v1.5 talker and local structure for CUDA Graph (#5197)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>
Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>
Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>

Co-authored-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>

### [ad3a162](https://github.com/vllm-project/vllm-omni/commit/ad3a162eb8a843c734b48f8462ecb63abbf4df9b)

- **作者**: rein yang
- **时间**: 2026-07-24T09:20:39Z
- **提交信息**: [perf] Minicpm o4.5 optimization (#5228)

Signed-off-by: R2-Y <ruiruyang2@gmail.com>
Co-authored-by: Sy03 <1370724210@qq.com>

### [acf941d](https://github.com/vllm-project/vllm-omni/commit/acf941da4da8bdca36cf4e8e8ea16d1e2df38e95)

- **作者**: Diya Peng
- **时间**: 2026-07-24T07:00:57Z
- **提交信息**: [Diffusion] Add VAE patch parallel support for FLUX.2-dev (#5292)

Signed-off-by: dpeng123 <diyapeng123@gmail.com>

---
