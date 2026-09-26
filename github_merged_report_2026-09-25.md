# GitHub Stars 合并报告 - 2026-09-25

**合并日期**: 2026-09-26
**监控日期**: 2026-09-25
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


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
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


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2859
- **最后更新**: 2026-09-25T17:02:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2258
- **最后更新**: 2026-09-25T19:04:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6504
- **最后更新**: 2026-09-26T00:07:59Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 1
- **主要提交者**: eigen

## AI分析总结

根据提供的提交记录和项目README，对仓库昨日（2024-09-25）的6次提交总结如下：

### 1. 主要更新类型
本次提交集中于 **性能优化** 和 **功能新增**，兼有少量 **修复与重构**。优化主要针对特定硬件（SM100/SM103）上的关键内核，以提升推理效率；新增功能则扩展了对新模型架构（如MiniMax-H3）和新量化格式（如NVFP4）的支持。

### 2. 关键变更点及其与项目方向的关系
- **扩展硬件与量化支持**：提交 #5134 和 #5543 大幅扩展了NVFP4 warp-decode及KDA预填充在SM100/SM103架构上的覆盖范围与性能，体现了项目对**最新GPU架构（如B200/GB300）** 和**低精度计算**的持续投入，这与项目“高性能GPU推理内核”的核心目标完全一致。
- **新增模型操作符**：提交 #5525 为SM100/SM103新增了MiniMax-H3模型的融合输出投影算子，直接响应了社区对特定模型高效推理的需求（如#4532候选方案）。
- **优化推理关键路径**：提交 #5548 移除了Kimi-K3融合路由器中的冗余同步，提交 #5547 优化了Blackwell MLA解码中FP8生产者的握手流程。这些精细的性能调优旨在**降低推理延迟、提升吞吐量**，是项目追求极限性能的体现。
- **新增高性能后端**：提交 #4557 为Blackwell架构（SM100/SM103）引入了全新的TRT-LLM MLA解码后端，结合了15级流水线与Split-KV归约。这标志着项目在**为企业级推理框架提供底层加速能力**上迈出了重要一步。

### 3. 对项目的影响和潜在意义
- **巩固硬件领先地位**：通过持续针对NVIDIA最新数据中心GPU（B200/GB300）进行优化和验证，强化了FlashInfer在**前沿硬件推理优化**领域的技术优势。
- **提升生态覆盖**：新增的MiniMax-H3算子和优化的Blackwell MLA后端，使项目能更好地支持主流大模型架构，有望被更广泛的AI应用框架（如TRT-LLM）所集成。
- **增强量化生态**：对NVFP4、MXFP8等量化格式的广泛支持与性能验证，推动了**低比特推理**的实用化，有助于降低大模型部署成本。

### 4. 值得关注的技术点
- **精细的性能测量与验证**：提交信息中详细描述了使用CUPTI、冷L2缓存、配对测量等方法进行的严格性能门控测试（如基线加速比、导出无回退比），展现了项目**对性能数据可靠性的极高要求**。
- **高级调度与融合**：KDA预填充中的**测量仿射分界点**（#5543）、MoE路由器中**移除冗余fence**（#5548）、以及MLA解码中**拆分FP8生产者握手**（#5547），都是针对特定硬件微架构和调度器的深度优化，体现了**内核开发的高度专业性**。
- **生成式代码与精确匹配**：多个提交（如#5547, #4557）涉及从内核描述语言生成CUDA源码，并确保其与参考实现的比特级一致，展示了项目独特的**内核开发工作流**。

### 5. 对项目发展的影响
这些提交共同推动了FlashInfer项目的两个核心发展方向：**性能极致化**与**功能泛化**。通过不断挖掘最新硬件潜力、优化关键算法路径，项目为大模型在高端GPU上的高效运行提供了坚实的基础库。同时，通过支持更多模型架构和量化格式，项目的适用性得到扩展，有助于其在AI推理基础设施中扮演更重要的角色。

## 详细提交记录

### [d542cff](https://github.com/flashinfer-ai/flashinfer/commit/d542cff84090e43df79865230a7d9ac26961af6b)

- **作者**: eigen
- **时间**: 2026-09-25T23:59:25Z
- **提交信息**: fix(cake_warp_decode): extend NVFP4 warp-decode coverage and synchronization (#5134)

## NVFP4 warp-decode: public-model performance table (SM100 / SM103,
num_tokens 1–32)

Two gates per row, measured with symmetric repeated paired measurement
(CUPTI activity timing, cold L2, symmetric external CUDA Graph
population, 6 creation orders × 6 instances per arm, same-instance
prime, 3 counterbalanced groups, seed 28301, 50 ms warmup + 100 ms
measurement per arm/group, direction/endpoint drift ≤ 2 %, FP4 atol 1 /
rtol 0.1, SM clock ≥ 1900 MHz):

- **Baseline speedup gate**: official FlashInfer baseline latency B over
the export latency E_o measured in the same paired population; passes
when B/E_o > 1.
- **Export no-regression gate**: source (the reference implementation
this export is generated from) latency S over the export latency E_s
measured in its own paired population; passes when S/E_s ≥ 0.97, i.e.
the export is at most 3 % slower than its source. The strict outcome
S/E_s ≥ 1 (export not slower at all) is reported next to it in every
table. E_o and E_s are separately measured export populations and are
never combined.

Status of the 448 rows at 2026-09-25: measured 448/448; baseline speedup
gate passed 447/448; export no-regression gate (S/E_s ≥ 0.97) passed
448/448; **both gates passed 447/448**; rows with S/E_s ≥ 1 (strict, no
regression at all) 260/448; baseline not beaten 1.

### What changed in this update

- Qwen3-30B (2048, 768, 128, 8) packed rows — SM103 num_tokens 9–32 and
SM100 num_tokens 10–32 — now derive their packed route tables inside the
persistent FC1 prologue, so the separate route-pack launch and its graph
dependency disappear (three launches per row; the host binding accepts
three launches for these rows). Baseline/export 1.009–1.033 (SM103) and
1.015–1.044 (SM100) on all 47 rows; source/export 0.995–1.011.

### Previous updates (kept)

- Qwen3-30B SM103 num_tokens=9 moves from the direct route to the
num_tokens=10 packed schedule (route-pack kernel, merged-A MMA-unroll-2
workfeed FC1, K512 stage-5 prefetch workfeed FC2). Baseline/export moved
from 0.985–0.993 (direct route, four attempts) to 1.000 and 1.000 over
two paired attempts: num_tokens=9 now measures at parity with the
baseline, not above it.
- Qwen3.5-35B SM103 num_tokens=16 uses the merged-A MMA-unroll-2
workfeed FC1 kernel (already used by Qwen3-30B num_tokens=10).
Baseline/export moved from 0.993–1.000 (three attempts) to 1.001.
- MiniMax-M3 SM103 num_tokens=1 now uses the same schedule as num_tokens
2–4 (persistent FC1, K256 FC2); three single-row kernel modules are
retired. Baseline/export moved from 0.965 to 1.060.
- MiniMax-M3 SM103 num_tokens=5 gets a K512 stage-5 FC2 kernel with
early accumulator release and MMA unroll 2. Baseline/export moved from
0.996 to 1.017.
- MiniMax-M3 SM100 num_tokens=5 gets the K512 stage-5 FC2 kernel with
early accumulator release and MMA unroll 2 (previously stage 4).
Baseline/export moved from 0.998 to 1.002.
- Qwen3.5-35B SM103 num_tokens 15 and 16 move to the K512 stage-5 FC2
kernel with early accumulator release and MMA unroll 2. Baseline/export
moved from 0.995/0.998 to 1.001/1.000 (num_tokens 16 measures at parity:
1.000, 1.000 and 0.993 over three paired attempts; it stays below the >
1 gate).
- Qwen3-30B SM100 num_tokens=9 now uses the num_tokens=8 kernel set
(merged-A persistent FC1, K512 stage-5 grouped early-accumulator direct
FC2). Baseline/export moved from 0.988 to 1.006.
- Qwen3-30B SM103 num_tokens 8 and 9 move to the same kernel set as
SM100 (merged-A persistent FC1, K512 stage-5 grouped early-accumulator
direct FC2); two single-purpose K256 FC2 kernels are retired.
Baseline/export: num_tokens 8 0.998 → 0.999 / 0.998 over two paired
attempts (parity), num_tokens 9 0.988 → 0.985 / 0.986 (both remain below
1).

### Validation

- Correctness on both architectures for every exported route (FP4
tolerance atol 1.0 / rtol 0.1 against the PyTorch reference), plus
source/export/build/runtime/manifest/route checks in the export
pipeline.
- compute-sanitizer synccheck and racecheck (run separately; memcheck
not run) over the representative tokens of every kernel-module signature
per model and architecture, including the modules added in this update:
60/60 invocations PASS, 0 errors, 0 hazards. Wall time per invocation
0-174 s.

| arch | model | tool | tokens | result |
|---|---|---|---|---|
| sm_100a | Kimi-K3 latent expert bank | racecheck | [1] | PASS (0
errors, 0 hazards) |
| sm_100a | Kimi-K3 latent expert bank | synccheck | [1] | PASS (0
errors) |
| sm_100a | MiniMax-M2 | racecheck | [1, 2, 16] | PASS (0 errors, 0
hazards) |
| sm_100a | MiniMax-M2 | synccheck | [1, 2, 16] | PASS (0 errors) |
| sm_100a | MiniMax-M3 | racecheck | [1, 2, 5, 6] | PASS (0 errors, 0
hazards) |
| sm_100a | MiniMax-M3 | synccheck | [1, 2, 5, 6] | PASS (0 errors) |
| sm_100a | Qwen3-235B-A22B | racecheck | [1, 2, 12] | PASS (0 errors, 0
hazards) |
| sm_100a | Qwen3-235B-A22B | synccheck | [1, 2, 12] | PASS (0 errors) |
| sm_100a | Qwen3-30B-A3B | racecheck | [1, 2, 3, 7, 8, 10, 13, 18, 32]
| PASS (0 errors, 0 hazards) |
| sm_100a | Qwen3-30B-A3B | synccheck | [1, 2, 3, 7, 8, 10, 13, 18, 32]
| PASS (0 errors) |
| sm_100a | Qwen3.5-35B-A3B | racecheck | [1, 2, 15] | PASS (0 errors, 0
hazards) |
| sm_100a | Qwen3.5-35B-A3B | synccheck | [1, 2, 15] | PASS (0 errors) |
| sm_100a | Qwen3.5-397B-A17B | racecheck | [1, 8] | PASS (0 errors, 0
hazards) |
| sm_100a | Qwen3.5-397B-A17B | synccheck | [1, 8] | PASS (0 errors) |
| sm_103a | MiniMax-M2 | synccheck | [1, 2, 16] | PASS (0 errors) |
| sm_103a | MiniMax-M3 | synccheck | [1, 2, 5] | PASS (0 errors) |
| sm_103a | Qwen3-235B-A22B | synccheck | [1, 2, 12] | PASS (0 errors) |
| sm_103a | Qwen3-30B-A3B | synccheck | [1, 2, 8, 9, 10, 11, 12, 17, 20,
21] | PASS (0 errors) |
| sm_103a | Qwen3.5-35B-A3B | synccheck | [1, 2, 28] | PASS (0 errors) |
| sm_103a | Qwen3.5-397B-A17B | synccheck | [1, 2, 8, 24] | PASS (0
errors) |
| sm_103a | MiniMax-M2 | racecheck | [1, 2, 16] | PASS (0 errors, 0
hazards) |
| sm_103a | MiniMax-M3 | racecheck | [1, 2, 5] | PASS (0 errors, 0
hazards) |
| sm_103a | Qwen3-235B-A22B | racecheck | [1, 2, 12] | PASS (0 errors, 0
hazards) |
| sm_103a | Qwen3-30B-A3B | racecheck | [1, 2, 8, 9, 10, 11, 12, 17, 20,
21] | PASS (0 errors, 0 hazards) |
| sm_103a | Qwen3.5-35B-A3B | racecheck | [1, 2, 28] | PASS (0 errors, 0
hazards) |
| sm_103a | Qwen3.5-397B-A17B | racecheck | [1, 2, 8, 24] | PASS (0
errors, 0 hazards) |
| sm_103a | Kimi-K3 latent expert bank | racecheck | [1] | PASS (0
errors, 0 hazards) |
| sm_103a | Kimi-K3 latent expert bank | synccheck | [1] | PASS (0
errors) |
| sm_103a | Qwen3.5-397B-A17B | racecheck | [9, 16, 32] | PASS (0
errors, 0 hazards) |
| sm_103a | Qwen3.5-397B-A17B | synccheck | [9, 16, 32] | PASS (0
errors) |
| sm_103a | Qwen3-235B-A22B | racecheck | [11, 16] | PASS (0 errors, 0
hazards) |
| sm_103a | Qwen3-235B-A22B | synccheck | [11, 16] | PASS (0 errors) |
| sm_103a | Kimi-K3 latent expert bank | racecheck | [1, 32] | PASS (0
errors, 0 hazards) |
| sm_103a | Kimi-K3 latent expert bank | synccheck | [1, 32] | PASS (0
errors) |
| sm_103a | Qwen3.5-35B-A3B | racecheck | [15, 20, 31] | PASS (0 errors,
0 hazards) |
| sm_103a | Qwen3.5-35B-A3B | synccheck | [15, 20, 31] | PASS (0 errors)
|
| sm_103a | Qwen3-30B-A3B | racecheck | [14, 15, 16] | PASS (0 errors, 0
hazards) |
| sm_103a | Qwen3-30B-A3B | synccheck | [14, 15, 16] | PASS (0 errors) |
| sm_103a | Qwen3.5-397B-A17B | racecheck | [1] | PASS (0 errors, 0
hazards) |
| sm_103a | Qwen3.5-397B-A17B | synccheck | [1] | PASS (0 errors) |
| sm_103a | Qwen3-30B-A3B | racecheck | [17, 18, 19] | PASS (0 errors, 0
hazards) |
| sm_103a | Qwen3-30B-A3B | synccheck | [17, 18, 19] | PASS (0 errors) |
| sm_103a | MiniMax-M3 | racecheck | [1, 2, 5] | PASS (0 errors, 0
hazards) |
| sm_103a | MiniMax-M3 | synccheck | [1, 2, 5] | PASS (0 errors) |
| sm_103a | Qwen3-30B-A3B | racecheck | [1, 2, 8, 9, 10, 11, 12, 17, 20,
21] | PASS (0 errors, 0 hazards) |
| sm_103a | Qwen3-30B-A3B | synccheck | [1, 2, 8, 9, 10, 11, 12, 17, 20,
21] | PASS (0 errors) |
| sm_103a | Qwen3.5-35B-A3B | racecheck | [1, 2, 15, 16, 28] | PASS (0
errors, 0 hazards) |
| sm_103a | Qwen3.5-35B-A3B | synccheck | [1, 2, 15, 16, 28] | PASS (0
errors) |
| sm_100a | MiniMax-M3 | racecheck | [1, 2, 5, 6] | PASS (0 errors, 0
hazards) |
| sm_100a | MiniMax-M3 | synccheck | [1, 2, 5, 6] | PASS (0 errors) |
| sm_100a | Qwen3-30B-A3B | racecheck | [1, 2, 3, 7, 8, 9, 10, 13, 18,
32] | PASS (0 errors, 0 hazards) |
| sm_100a | Qwen3-30B-A3B | synccheck | [1, 2, 3, 7, 8, 9, 10, 13, 18,
32] | PASS (0 errors) |
| sm_103a | Qwen3-30B-A3B | racecheck | [9] | PASS (0 errors, 0 hazards)
|
| sm_103a | Qwen3-30B-A3B | synccheck | [9] | PASS (0 errors) |
| sm_103a | Qwen3.5-35B-A3B | racecheck | [16] | PASS (0 errors, 0
hazards) |
| sm_103a | Qwen3.5-35B-A3B | synccheck | [16] | PASS (0 errors) |
| sm_103a | Qwen3-30B-A3B | synccheck | [9, 11, 12, 20, 21, 31, 32] |
PASS (0 errors) |
| sm_103a | Qwen3-30B-A3B | racecheck | [9, 11, 12, 20, 21, 31, 32] |
PASS (0 errors, 0 hazards) |
| sm_100a | Qwen3-30B-A3B | synccheck | [10, 13, 18, 19, 20, 31, 32] |
PASS (0 errors) |
| sm_100a | Qwen3-30B-A3B | racecheck | [10, 13, 18, 19, 20, 31, 32] |
PASS (0 errors, 0 hazards) |

### Per-model summary

| arch | model | both gates | baseline gate B/E_o > 1 | export gate
S/E_s ≥ 0.97 | strict S/E_s ≥ 1 | baseline misses (token: B/E_o) |
|---|---|---:|---:|---:|---:|---|
| sm_100a | Qwen3-30B-A3B | 32/32 | 32/32 | 32/32 | 26/32 | — |
| sm_100a | Qwen3-235B-A22B | 32/32 | 32/32 | 32/32 | 12/32 | — |
| sm_100a | Qwen3.5-35B-A3B | 32/32 | 32/32 | 32/32 | 18/32 | — |
| sm_100a | Qwen3.5-397B-A17B | 32/32 | 32/32 | 32/32 | 14/32 | — |
| sm_100a | MiniMax-M2 | 32/32 | 32/32 | 32/32 | 17/32 | — |
| sm_100a | MiniMax-M3 | 32/32 | 32/32 | 32/32 | 22/32 | — |
| sm_100a | Kimi-K3 latent expert bank | 32/32 | 32/32 | 32/32 | 22/32 |
— |
| sm_103a | Qwen3-30B-A3B | 31/32 | 31/32 | 32/32 | 25/32 | T8: 0.9976 |
| sm_103a | Qwen3-235B-A22B | 32/32 | 32/32 | 32/32 | 14/32 | — |
| sm_103a | Qwen3.5-35B-A3B | 32/32 | 32/32 | 32/32 | 18/32 | — |
| sm_103a | Qwen3.5-397B-A17B | 32/32 | 32/32 | 32/32 | 18/32 | — |
| sm_103a | MiniMax-M2 | 32/32 | 32/32 | 32/32 | 15/32 | — |
| sm_103a | MiniMax-M3 | 32/32 | 32/32 | 32/32 | 23/32 | — |
| sm_103a | Kimi-K3 latent expert bank | 32/32 | 32/32 | 32/32 | 16/32 |
— |

### Complete 448-row table (baseline / source / export latencies in µs,
independent paired denominators, both gates)

### sm_100a

<details><summary>Qwen3-30B-A3B (2048/768/128/8) — 32/32 pass both
gates, 32/32 baseline gate, 32/32 export gate (26/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 16.768 | 16.000 | 1.0480 | P | 16.320 | 16.256 | 1.0039 | P | P |
1 | QUALIFIED |
| 2 | 22.016 | 20.192 | 1.0903 | P | 20.543 | 20.192 | 1.0174 | P | P |
1 | QUALIFIED |
| 3 | 25.824 | 24.192 | 1.0675 | P | 24.288 | 24.160 | 1.0053 | P | P |
1 | QUALIFIED |
| 4 | 29.344 | 27.648 | 1.0613 | P | 27.648 | 27.648 | 1.0000 | P | P |
1 | QUALIFIED |
| 5 | 31.232 | 31.103 | 1.0041 | P | 31.167 | 31.103 | 1.0021 | P | P |
1 | QUALIFIED |
| 6 | 34.368 | 33.600 | 1.0229 | P | 33.600 | 33.599 | 1.0000 | P | P |
1 | QUALIFIED |
| 7 | 37.664 | 37.216 | 1.0120 | P | 37.024 | 37.215 | 0.9949 | P | F |
1 | QUALIFIED |
| 8 | 39.744 | 39.584 | 1.0041 | P | 39.680 | 39.583 | 1.0025 | P | P |
1 | QUALIFIED |
| 9 | 42.176 | 41.920 | 1.0061 | P | 41.792 | 41.920 | 0.9969 | P | F |
3 | QUALIFIED |
| 10 | 43.456 | 42.592 | 1.0203 | P | 42.688 | 42.592 | 1.0022 | P | P |
1 | QUALIFIED |
| 11 | 44.896 | 44.192 | 1.0159 | P | 44.319 | 44.192 | 1.0029 | P | P |
1 | QUALIFIED |
| 12 | 46.207 | 45.472 | 1.0162 | P | 45.632 | 45.503 | 1.0028 | P | P |
1 | QUALIFIED |
| 13 | 48.352 | 46.815 | 1.0328 | P | 46.752 | 46.784 | 0.9993 | P | F |
1 | QUALIFIED |
| 14 | 48.991 | 47.647 | 1.0282 | P | 47.296 | 47.648 | 0.9926 | P | F |
1 | QUALIFIED |
| 15 | 50.816 | 49.024 | 1.0366 | P | 49.215 | 49.023 | 1.0039 | P | P |
1 | QUALIFIED |
| 16 | 51.840 | 49.888 | 1.0391 | P | 49.888 | 49.888 | 1.0000 | P | P |
1 | QUALIFIED |
| 17 | 53.216 | 51.327 | 1.0368 | P | 51.552 | 51.296 | 1.0050 | P | P |
1 | QUALIFIED |
| 18 | 54.464 | 53.664 | 1.0149 | P | 53.632 | 53.632 | 1.0000 | P | P |
1 | QUALIFIED |
| 19 | 55.072 | 54.176 | 1.0165 | P | 54.272 | 54.271 | 1.0000 | P | P |
1 | QUALIFIED |
| 20 | 55.744 | 53.952 | 1.0332 | P | 54.016 | 53.951 | 1.0012 | P | P |
1 | QUALIFIED |
| 21 | 56.736 | 54.688 | 1.0374 | P | 55.296 | 54.720 | 1.0105 | P | P |
1 | QUALIFIED |
| 22 | 57.984 | 56.160 | 1.0325 | P | 56.160 | 56.193 | 0.9994 | P | F |
1 | QUALIFIED |
| 23 | 57.920 | 55.664 | 1.0405 | P | 56.128 | 55.648 | 1.0086 | P | P |
1 | QUALIFIED |
| 24 | 58.368 | 56.512 | 1.0328 | P | 56.512 | 56.447 | 1.0012 | P | P |
1 | QUALIFIED |
| 25 | 60.672 | 58.720 | 1.0332 | P | 58.879 | 58.720 | 1.0027 | P | P |
1 | QUALIFIED |
| 26 | 62.656 | 60.544 | 1.0349 | P | 60.576 | 60.544 | 1.0005 | P | P |
1 | QUALIFIED |
| 27 | 63.040 | 60.384 | 1.0440 | P | 60.544 | 60.543 | 1.0000 | P | P |
1 | QUALIFIED |
| 28 | 63.200 | 61.664 | 1.0249 | P | 61.376 | 61.568 | 0.9969 | P | F |
1 | QUALIFIED |
| 29 | 64.576 | 62.143 | 1.0392 | P | 62.240 | 62.176 | 1.0010 | P | P |
1 | QUALIFIED |
| 30 | 65.025 | 62.720 | 1.0368 | P | 63.072 | 62.720 | 1.0056 | P | P |
1 | QUALIFIED |
| 31 | 65.856 | 63.615 | 1.0352 | P | 63.745 | 63.616 | 1.0020 | P | P |
1 | QUALIFIED |
| 32 | 65.568 | 64.000 | 1.0245 | P | 64.224 | 64.000 | 1.0035 | P | P |
1 | QUALIFIED |

</details>

<details><summary>Qwen3-235B-A22B (4096/1536/128/8) — 32/32 pass both
gates, 32/32 baseline gate, 32/32 export gate (12/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 35.808 | 34.240 | 1.0458 | P | 34.112 | 34.048 | 1.0019 | P | P |
1 | QUALIFIED |
| 2 | 53.248 | 44.607 | 1.1937 | P | 44.193 | 44.608 | 0.9907 | P | F |
1 | QUALIFIED |
| 3 | 67.967 | 58.496 | 1.1619 | P | 58.144 | 58.496 | 0.9940 | P | F |
1 | QUALIFIED |
| 4 | 79.552 | 68.993 | 1.1530 | P | 68.960 | 68.864 | 1.0014 | P | P |
1 | QUALIFIED |
| 5 | 91.008 | 78.623 | 1.1575 | P | 78.592 | 78.624 | 0.9996 | P | F |
1 | QUALIFIED |
| 6 | 103.904 | 89.024 | 1.1671 | P | 88.832 | 88.992 | 0.9982 | P | F |
1 | QUALIFIED |
| 7 | 118.240 | 101.441 | 1.1656 | P | 101.472 | 101.472 | 1.0000 | P |
P | 1 | QUALIFIED |
| 8 | 125.984 | 112.192 | 1.1229 | P | 113.279 | 112.224 | 1.0094 | P |
P | 1 | QUALIFIED |
| 9 | 133.952 | 122.848 | 1.0904 | P | 123.040 | 122.848 | 1.0016 | P |
P | 1 | QUALIFIED |
| 10 | 139.488 | 132.129 | 1.0557 | P | 132.160 | 132.112 | 1.0004 | P |
P | 1 | QUALIFIED |
| 11 | 145.568 | 143.424 | 1.0149 | P | 143.744 | 143.456 | 1.0020 | P |
P | 1 | QUALIFIED |
| 12 | 150.848 | 132.736 | 1.1365 | P | 132.672 | 132.736 | 0.9995 | P |
F | 1 | QUALIFIED |
| 13 | 159.392 | 140.000 | 1.1385 | P | 139.808 | 140.064 | 0.9982 | P |
F | 1 | QUALIFIED |
| 14 | 160.960 | 143.904 | 1.1185 | P | 143.808 | 143.936 | 0.9991 | P |
F | 1 | QUALIFIED |
| 15 | 168.512 | 151.328 | 1.1136 | P | 151.392 | 151.360 | 1.0002 | P |
P | 1 | QUALIFIED |
| 16 | 172.416 | 156.576 | 1.1012 | P | 156.640 | 156.608 | 1.0002 | P |
P | 1 | QUALIFIED |
| 17 | 178.720 | 160.352 | 1.1145 | P | 160.352 | 160.384 | 0.9998 | P |
F | 1 | QUALIFIED |
| 18 | 184.064 | 164.096 | 1.1217 | P | 163.872 | 164.128 | 0.9984 | P |
F | 1 | QUALIFIED |
| 19 | 185.696 | 165.728 | 1.1205 | P | 165.440 | 165.728 | 0.9983 | P |
F | 1 | QUALIFIED |
| 20 | 187.680 | 167.040 | 1.1236 | P | 167.104 | 167.008 | 1.0006 | P |
P | 1 | QUALIFIED |
| 21 | 191.552 | 169.536 | 1.1299 | P | 169.504 | 169.568 | 0.9996 | P |
F | 1 | QUALIFIED |
| 22 | 196.799 | 173.536 | 1.1341 | P | 173.216 | 173.536 | 0.9982 | P |
F | 1 | QUALIFIED |
| 23 | 196.736 | 173.920 | 1.1312 | P | 173.952 | 173.920 | 1.0002 | P |
P | 1 | QUALIFIED |
| 24 | 198.112 | 175.200 | 1.1308 | P | 175.232 | 175.264 | 0.9998 | P |
F | 1 | QUALIFIED |
| 25 | 205.696 | 180.032 | 1.1426 | P | 180.065 | 180.064 | 1.0000 | P |
P | 1 | QUALIFIED |
| 26 | 212.960 | 184.672 | 1.1532 | P | 184.512 | 184.641 | 0.9993 | P |
F | 1 | QUALIFIED |
| 27 | 215.072 | 186.240 | 1.1548 | P | 185.920 | 186.080 | 0.9991 | P |
F | 1 | QUALIFIED |
| 28 | 216.960 | 187.519 | 1.1570 | P | 187.232 | 187.360 | 0.9993 | P |
F | 1 | QUALIFIED |
| 29 | 220.096 | 189.856 | 1.1593 | P | 190.016 | 190.080 | 0.9997 | P |
F | 1 | QUALIFIED |
| 30 | 221.888 | 191.328 | 1.1597 | P | 191.296 | 191.456 | 0.9992 | P |
F | 1 | QUALIFIED |
| 31 | 225.984 | 194.016 | 1.1648 | P | 193.921 | 194.016 | 0.9995 | P |
F | 1 | QUALIFIED |
| 32 | 225.695 | 194.720 | 1.1591 | P | 194.208 | 194.688 | 0.9975 | P |
F | 1 | QUALIFIED |

</details>

<details><summary>Qwen3.5-35B-A3B (2048/512/256/8) — 32/32 pass both
gates, 32/32 baseline gate, 32/32 export gate (18/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 15.296 | 14.207 | 1.0767 | P | 14.335 | 14.144 | 1.0135 | P | P |
1 | QUALIFIED |
| 2 | 19.776 | 17.217 | 1.1486 | P | 17.120 | 17.247 | 0.9926 | P | F |
1 | QUALIFIED |
| 3 | 22.784 | 20.736 | 1.0988 | P | 20.832 | 20.704 | 1.0062 | P | P |
1 | QUALIFIED |
| 4 | 25.504 | 23.456 | 1.0873 | P | 23.584 | 23.424 | 1.0068 | P | P |
1 | QUALIFIED |
| 5 | 28.224 | 26.304 | 1.0730 | P | 26.496 | 26.335 | 1.0061 | P | P |
1 | QUALIFIED |
| 6 | 30.880 | 28.671 | 1.0770 | P | 28.736 | 28.640 | 1.0034 | P | P |
1 | QUALIFIED |
| 7 | 33.600 | 31.424 | 1.0692 | P | 31.424 | 31.456 | 0.9990 | P | F |
1 | QUALIFIED |
| 8 | 36.415 | 34.240 | 1.0635 | P | 34.112 | 34.240 | 0.9963 | P | F |
1 | QUALIFIED |
| 9 | 38.048 | 36.352 | 1.0467 | P | 36.576 | 36.385 | 1.0052 | P | P |
1 | QUALIFIED |
| 10 | 39.264 | 38.176 | 1.0285 | P | 38.080 | 38.176 | 0.9975 | P | F |
1 | QUALIFIED |
| 11 | 41.312 | 39.904 | 1.0353 | P | 40.032 | 39.903 | 1.0032 | P | P |
1 | QUALIFIED |
| 12 | 42.144 | 41.440 | 1.0170 | P | 42.112 | 41.440 | 1.0162 | P | P |
1 | QUALIFIED |
| 13 | 44.223 | 43.488 | 1.0169 | P | 43.296 | 43.519 | 0.9949 | P | F |
1 | QUALIFIED |
| 14 | 45.183 | 44.896 | 1.0064 | P | 44.800 | 44.895 | 0.9979 | P | F |
1 | QUALIFIED |
| 15 | 46.656 | 46.592 | 1.0014 | P | 46.688 | 46.592 | 1.0021 | P | P |
1 | QUALIFIED |
| 16 | 47.936 | 47.839 | 1.0020 | P | 47.744 | 47.840 | 0.9980 | P | F |
1 | QUALIFIED |
| 17 | 50.015 | 49.504 | 1.0103 | P | 49.216 | 49.407 | 0.9961 | P | F |
1 | QUALIFIED |
| 18 | 50.880 | 50.496 | 1.0076 | P | 50.175 | 50.496 | 0.9936 | P | F |
1 | QUALIFIED |
| 19 | 52.160 | 51.807 | 1.0068 | P | 51.616 | 51.808 | 0.9963 | P | F |
1 | QUALIFIED |
| 20 | 53.408 | 53.024 | 1.0072 | P | 52.768 | 53.024 | 0.9952 | P | F |
1 | QUALIFIED |
| 21 | 54.271 | 53.727 | 1.0101 | P | 53.920 | 53.728 | 1.0036 | P | P |
1 | QUALIFIED |
| 22 | 55.679 | 55.008 | 1.0122 | P | 55.008 | 55.008 | 1.0000 | P | P |
1 | QUALIFIED |
| 23 | 56.544 | 55.808 | 1.0132 | P | 55.775 | 55.679 | 1.0017 | P | P |
1 | QUALIFIED |
| 24 | 57.056 | 56.479 | 1.0102 | P | 56.479 | 56.576 | 0.9983 | P | F |
1 | QUALIFIED |
| 25 | 58.719 | 58.239 | 1.0082 | P | 58.303 | 58.239 | 1.0011 | P | P |
1 | QUALIFIED |
| 26 | 60.223 | 59.423 | 1.0135 | P | 59.520 | 59.424 | 1.0016 | P | P |
1 | QUALIFIED |
| 27 | 61.087 | 60.480 | 1.0100 | P | 60.128 | 60.352 | 0.9963 | P | F |
1 | QUALIFIED |
| 28 | 62.720 | 61.951 | 1.0124 | P | 61.920 | 61.823 | 1.0016 | P | P |
1 | QUALIFIED |
| 29 | 64.639 | 63.487 | 1.0181 | P | 63.679 | 63.520 | 1.0025 | P | P |
1 | QUALIFIED |
| 30 | 66.048 | 64.960 | 1.0167 | P | 65.024 | 64.960 | 1.0010 | P | P |
1 | QUALIFIED |
| 31 | 67.584 | 66.784 | 1.0120 | P | 66.656 | 66.815 | 0.9976 | P | F |
1 | QUALIFIED |
| 32 | 68.416 | 67.423 | 1.0147 | P | 67.488 | 67.424 | 1.0009 | P | P |
1 | QUALIFIED |

</details>

<details><summary>Qwen3.5-397B-A17B (4096/1024/512/10) — 32/32 pass both
gates, 32/32 baseline gate, 32/32 export gate (14/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 27.680 | 25.824 | 1.0719 | P | 26.080 | 25.760 | 1.0124 | P | P |
1 | QUALIFIED |
| 2 | 41.504 | 39.168 | 1.0596 | P | 39.295 | 39.199 | 1.0024 | P | P |
1 | QUALIFIED |
| 3 | 54.528 | 51.488 | 1.0590 | P | 52.192 | 51.520 | 1.0130 | P | P |
1 | QUALIFIED |
| 4 | 65.952 | 63.712 | 1.0352 | P | 63.648 | 63.712 | 0.9990 | P | F |
1 | QUALIFIED |
| 5 | 77.024 | 74.976 | 1.0273 | P | 74.752 | 74.944 | 0.9974 | P | F |
1 | QUALIFIED |
| 6 | 88.352 | 86.400 | 1.0226 | P | 85.664 | 86.400 | 0.9915 | P | F |
1 | QUALIFIED |
| 7 | 94.912 | 94.144 | 1.0082 | P | 93.823 | 94.144 | 0.9966 | P | F |
1 | QUALIFIED |
| 8 | 102.912 | 101.536 | 1.0136 | P | 101.311 | 101.536 | 0.9978 | P |
F | 1 | QUALIFIED |
| 9 | 112.128 | 110.688 | 1.0130 | P | 111.040 | 110.688 | 1.0032 | P |
P | 1 | QUALIFIED |
| 10 | 121.664 | 119.775 | 1.0158 | P | 120.256 | 119.775 | 1.0040 | P |
P | 1 | QUALIFIED |
| 11 | 127.488 | 125.632 | 1.0148 | P | 125.792 | 125.600 | 1.0015 | P |
P | 1 | QUALIFIED |
| 12 | 133.344 | 132.192 | 1.0087 | P | 132.255 | 132.192 | 1.0005 | P |
P | 1 | QUALIFIED |
| 13 | 141.152 | 139.776 | 1.0098 | P | 139.840 | 139.776 | 1.0005 | P |
P | 1 | QUALIFIED |
| 14 | 149.120 | 147.168 | 1.0133 | P | 147.360 | 147.327 | 1.0002 | P |
P | 1 | QUALIFIED |
| 15 | 157.951 | 156.224 | 1.0111 | P | 156.191 | 156.239 | 0.9997 | P |
F | 1 | QUALIFIED |
| 16 | 165.888 | 163.712 | 1.0133 | P | 163.712 | 163.711 | 1.0000 | P |
P | 1 | QUALIFIED |
| 17 | 171.999 | 166.623 | 1.0323 | P | 166.912 | 166.624 | 1.0017 | P |
P | 1 | QUALIFIED |
| 18 | 180.640 | 175.327 | 1.0303 | P | 175.360 | 175.392 | 0.9998 | P |
F | 1 | QUALIFIED |
| 19 | 188.319 | 183.136 | 1.0283 | P | 183.007 | 183.072 | 0.9996 | P |
F | 1 | QUALIFIED |
| 20 | 194.175 | 188.735 | 1.0288 | P | 189.152 | 188.703 | 1.0024 | P |
P | 1 | QUALIFIED |
| 21 | 199.760 | 195.327 | 1.0227 | P | 194.784 | 195.327 | 0.9972 | P |
F | 1 | QUALIFIED |
| 22 | 203.904 | 198.751 | 1.0259 | P | 198.655 | 198.815 | 0.9992 | P |
F | 1 | QUALIFIED |
| 23 | 208.928 | 203.648 | 1.0259 | P | 203.360 | 203.936 | 0.9972 | P |
F | 1 | QUALIFIED |
| 24 | 214.847 | 209.663 | 1.0247 | P | 209.312 | 209.600 | 0.9986 | P |
F | 1 | QUALIFIED |
| 25 | 220.479 | 214.624 | 1.0273 | P | 215.168 | 214.624 | 1.0025 | P |
P | 1 | QUALIFIED |
| 26 | 225.871 | 219.903 | 1.0271 | P | 219.712 | 219.872 | 0.9993 | P |
F | 1 | QUALIFIED |
| 27 | 230.528 | 224.608 | 1.0264 | P | 224.608 | 224.576 | 1.0001 | P |
P | 1 | QUALIFIED |
| 28 | 233.312 | 227.792 | 1.0242 | P | 227.584 | 228.032 | 0.9980 | P |
F | 1 | QUALIFIED |
| 29 | 240.992 | 235.743 | 1.0223 | P | 235.231 | 235.743 | 0.9978 | P |
F | 1 | QUALIFIED |
| 30 | 244.192 | 239.008 | 1.0217 | P | 238.848 | 238.944 | 0.9996 | P |
F | 1 | QUALIFIED |
| 31 | 249.952 | 244.704 | 1.0214 | P | 243.936 | 244.704 | 0.9969 | P |
F | 1 | QUALIFIED |
| 32 | 254.400 | 249.407 | 1.0200 | P | 248.927 | 249.120 | 0.9992 | P |
F | 1 | QUALIFIED |

</details>

<details><summary>MiniMax-M2 (3072/1536/256/8) — 32/32 pass both gates,
32/32 baseline gate, 32/32 export gate (17/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 31.360 | 29.632 | 1.0583 | P | 29.632 | 29.632 | 1.0000 | P | P |
1 | QUALIFIED |
| 2 | 44.768 | 35.520 | 1.2604 | P | 35.680 | 35.552 | 1.0036 | P | P |
1 | QUALIFIED |
| 3 | 58.112 | 47.520 | 1.2229 | P | 47.392 | 47.520 | 0.9973 | P | F |
1 | QUALIFIED |
| 4 | 70.496 | 58.560 | 1.2038 | P | 58.464 | 58.591 | 0.9978 | P | F |
1 | QUALIFIED |
| 5 | 80.000 | 67.231 | 1.1899 | P | 67.295 | 67.232 | 1.0009 | P | P |
1 | QUALIFIED |
| 6 | 93.215 | 77.184 | 1.2077 | P | 77.216 | 77.184 | 1.0004 | P | P |
1 | QUALIFIED |
| 7 | 106.176 | 87.264 | 1.2167 | P | 86.944 | 87.264 | 0.9963 | P | F |
1 | QUALIFIED |
| 8 | 117.024 | 96.256 | 1.2158 | P | 96.256 | 96.256 | 1.0000 | P | P |
1 | QUALIFIED |
| 9 | 126.943 | 104.767 | 1.2117 | P | 104.671 | 104.767 | 0.9991 | P |
F | 1 | QUALIFIED |
| 10 | 132.608 | 110.879 | 1.1960 | P | 110.848 | 110.879 | 0.9997 | P |
F | 1 | QUALIFIED |
| 11 | 141.055 | 117.695 | 1.1985 | P | 117.664 | 117.695 | 0.9997 | P |
F | 1 | QUALIFIED |
| 12 | 145.279 | 125.600 | 1.1567 | P | 125.632 | 125.631 | 1.0000 | P |
P | 1 | QUALIFIED |
| 13 | 153.984 | 133.472 | 1.1537 | P | 133.439 | 133.504 | 0.9995 | P |
F | 1 | QUALIFIED |
| 14 | 158.495 | 140.704 | 1.1264 | P | 140.863 | 140.703 | 1.0011 | P |
P | 1 | QUALIFIED |
| 15 | 164.223 | 149.407 | 1.0992 | P | 149.824 | 149.408 | 1.0028 | P |
P | 1 | QUALIFIED |
| 16 | 170.144 | 143.935 | 1.1821 | P | 143.936 | 143.935 | 1.0000 | P |
P | 1 | QUALIFIED |
| 17 | 177.440 | 166.495 | 1.0657 | P | 166.624 | 166.495 | 1.0008 | P |
P | 1 | QUALIFIED |
| 18 | 181.759 | 173.823 | 1.0457 | P | 173.407 | 173.823 | 0.9976 | P |
F | 1 | QUALIFIED |
| 19 | 187.103 | 181.791 | 1.0292 | P | 181.439 | 181.791 | 0.9981 | P |
F | 1 | QUALIFIED |
| 20 | 192.575 | 189.119 | 1.0183 | P | 189.119 | 189.279 | 0.9992 | P |
F | 1 | QUALIFIED |
| 21 | 196.607 | 170.719 | 1.1516 | P | 170.495 | 170.687 | 0.9989 | P |
F | 1 | QUALIFIED |
| 22 | 202.207 | 175.999 | 1.1489 | P | 175.872 | 175.904 | 0.9998 | P |
F | 1 | QUALIFIED |
| 23 | 206.399 | 180.703 | 1.1422 | P | 180.767 | 180.735 | 1.0002 | P |
P | 1 | QUALIFIED |
| 24 | 209.118 | 184.414 | 1.1340 | P | 184.703 | 184.447 | 1.0014 | P |
P | 1 | QUALIFIED |
| 25 | 216.287 | 190.879 | 1.1331 | P | 191.327 | 191.039 | 1.0015 | P |
P | 1 | QUALIFIED |
| 26 | 222.719 | 197.151 | 1.1297 | P | 196.991 | 197.119 | 0.9994 | P |
F | 1 | QUALIFIED |
| 27 | 226.815 | 200.991 | 1.1285 | P | 200.800 | 201.183 | 0.9981 | P |
F | 1 | QUALIFIED |
| 28 | 234.687 | 208.063 | 1.1280 | P | 208.160 | 208.063 | 1.0005 | P |
P | 1 | QUALIFIED |
| 29 | 241.823 | 214.879 | 1.1254 | P | 214.847 | 214.847 | 1.0000 | P |
P | 1 | QUALIFIED |
| 30 | 248.927 | 220.575 | 1.1285 | P | 220.607 | 220.607 | 1.0000 | P |
P | 1 | QUALIFIED |
| 31 | 256.974 | 228.095 | 1.1266 | P | 228.319 | 228.095 | 1.0010 | P |
P | 1 | QUALIFIED |
| 32 | 260.895 | 232.126 | 1.1239 | P | 232.063 | 232.095 | 0.9999 | P |
F | 1 | QUALIFIED |

</details>

<details><summary>MiniMax-M3 (6144/3072/128/4, SwiGLU α=1.702 β=1
clamp=7) — 32/32 pass both gates, 32/32 baseline gate, 32/32 export gate
(22/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 38.816 | 38.336 | 1.0125 | P | 38.271 | 38.336 | 0.9983 | P | F |
2 | QUALIFIED |
| 2 | 59.552 | 57.088 | 1.0432 | P | 57.472 | 57.120 | 1.0062 | P | P |
2 | QUALIFIED |
| 3 | 80.320 | 76.639 | 1.0480 | P | 76.415 | 76.671 | 0.9967 | P | F |
2 | QUALIFIED |
| 4 | 98.752 | 95.295 | 1.0363 | P | 95.616 | 95.296 | 1.0034 | P | P |
2 | QUALIFIED |
| 5 | 106.240 | 106.016 | 1.0021 | P | 106.016 | 106.144 | 0.9988 | P |
F | 2 | QUALIFIED |
| 6 | 124.992 | 124.128 | 1.0070 | P | 124.127 | 124.127 | 1.0000 | P |
P | 2 | QUALIFIED |
| 7 | 141.919 | 141.408 | 1.0036 | P | 141.184 | 141.376 | 0.9986 | P |
F | 2 | QUALIFIED |
| 8 | 154.912 | 154.144 | 1.0050 | P | 154.144 | 154.112 | 1.0002 | P |
P | 2 | QUALIFIED |
| 9 | 172.255 | 171.552 | 1.0041 | P | 171.871 | 171.552 | 1.0019 | P |
P | 1 | QUALIFIED |
| 10 | 177.376 | 175.488 | 1.0108 | P | 176.064 | 175.552 | 1.0029 | P |
P | 1 | QUALIFIED |
| 11 | 185.568 | 184.320 | 1.0068 | P | 184.351 | 184.288 | 1.0003 | P |
P | 1 | QUALIFIED |
| 12 | 194.207 | 192.352 | 1.0096 | P | 192.640 | 192.384 | 1.0013 | P |
P | 1 | QUALIFIED |
| 13 | 210.912 | 209.823 | 1.0052 | P | 209.503 | 209.792 | 0.9986 | P |
F | 1 | QUALIFIED |
| 14 | 211.072 | 209.343 | 1.0083 | P | 209.600 | 209.343 | 1.0012 | P |
P | 1 | QUALIFIED |
| 15 | 228.415 | 227.072 | 1.0059 | P | 227.135 | 227.104 | 1.0001 | P |
P | 1 | QUALIFIED |
| 16 | 236.703 | 235.135 | 1.0067 | P | 235.663 | 235.103 | 1.0024 | P |
P | 1 | QUALIFIED |
| 17 | 249.023 | 247.775 | 1.0050 | P | 248.032 | 247.871 | 1.0006 | P |
P | 1 | QUALIFIED |
| 18 | 262.367 | 260.895 | 1.0056 | P | 260.671 | 260.543 | 1.0005 | P |
P | 1 | QUALIFIED |
| 19 | 270.335 | 269.183 | 1.0043 | P | 269.247 | 269.055 | 1.0007 | P |
P | 1 | QUALIFIED |
| 20 | 271.071 | 269.311 | 1.0065 | P | 269.407 | 268.991 | 1.0015 | P |
P | 1 | QUALIFIED |
| 21 | 283.072 | 281.631 | 1.0051 | P | 282.079 | 281.791 | 1.0010 | P |
P | 1 | QUALIFIED |
| 22 | 291.583 | 290.335 | 1.0043 | P | 290.239 | 290.271 | 0.9999 | P |
F | 1 | QUALIFIED |
| 23 | 296.127 | 294.783 | 1.0046 | P | 295.006 | 295.135 | 0.9996 | P |
F | 1 | QUALIFIED |
| 24 | 304.383 | 303.231 | 1.0038 | P | 303.103 | 303.231 | 0.9996 | P |
F | 1 | QUALIFIED |
| 25 | 321.696 | 319.647 | 1.0064 | P | 319.999 | 319.743 | 1.0008 | P |
P | 1 | QUALIFIED |
| 26 | 330.687 | 329.087 | 1.0049 | P | 328.479 | 328.639 | 0.9995 | P |
F | 1 | QUALIFIED |
| 27 | 334.527 | 332.671 | 1.0056 | P | 332.703 | 332.671 | 1.0001 | P |
P | 1 | QUALIFIED |
| 28 | 342.880 | 341.535 | 1.0039 | P | 341.343 | 341.535 | 0.9994 | P |
F | 1 | QUALIFIED |
| 29 | 351.583 | 349.855 | 1.0049 | P | 349.951 | 349.887 | 1.0002 | P |
P | 1 | QUALIFIED |
| 30 | 364.159 | 362.335 | 1.0050 | P | 362.719 | 362.336 | 1.0011 | P |
P | 1 | QUALIFIED |
| 31 | 377.023 | 375.232 | 1.0048 | P | 375.423 | 375.231 | 1.0005 | P |
P | 1 | QUALIFIED |
| 32 | 376.991 | 375.360 | 1.0043 | P | 375.999 | 375.423 | 1.0015 | P |
P | 1 | QUALIFIED |

</details>

<details><summary>Kimi-K3 latent expert bank (3584/3072/896/16, SiTU
gate 4 / linear 25) — 32/32 pass both gates, 32/32 baseline gate, 32/32
export gate (22/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 124.768 | 75.584 | 1.6507 | P | 75.903 | 75.584 | 1.0042 | P | P |
1 | QUALIFIED |
| 2 | 220.480 | 118.913 | 1.8541 | P | 119.168 | 118.816 | 1.0030 | P |
P | 1 | QUALIFIED |
| 3 | 322.048 | 162.144 | 1.9862 | P | 162.207 | 162.143 | 1.0004 | P |
P | 1 | QUALIFIED |
| 4 | 416.992 | 206.144 | 2.0228 | P | 206.688 | 206.143 | 1.0026 | P |
P | 1 | QUALIFIED |
| 5 | 504.415 | 248.704 | 2.0282 | P | 248.704 | 248.448 | 1.0010 | P |
P | 1 | QUALIFIED |
| 6 | 600.864 | 292.224 | 2.0562 | P | 291.983 | 292.448 | 0.9984 | P |
F | 1 | QUALIFIED |
| 7 | 694.207 | 335.471 | 2.0693 | P | 335.647 | 335.520 | 1.0004 | P |
P | 1 | QUALIFIED |
| 8 | 784.031 | 378.463 | 2.0716 | P | 378.528 | 378.592 | 0.9998 | P |
F | 1 | QUALIFIED |
| 9 | 872.159 | 421.696 | 2.0682 | P | 421.535 | 421.328 | 1.0005 | P |
P | 1 | QUALIFIED |
| 10 | 960.463 | 464.431 | 2.0680 | P | 464.160 | 464.607 | 0.9990 | P |
F | 1 | QUALIFIED |
| 11 | 1056.223 | 508.431 | 2.0774 | P | 508.447 | 508.448 | 1.0000 | P
| F | 1 | QUALIFIED |
| 12 | 1149.119 | 551.968 | 2.0819 | P | 551.679 | 551.711 | 0.9999 | P
| F | 1 | QUALIFIED |
| 13 | 1217.983 | 593.567 | 2.0520 | P | 594.272 | 593.631 | 1.0011 | P
| P | 1 | QUALIFIED |
| 14 | 1312.320 | 636.896 | 2.0605 | P | 637.311 | 636.815 | 1.0008 | P
| P | 1 | QUALIFIED |
| 15 | 1400.511 | 678.656 | 2.0637 | P | 679.904 | 679.072 | 1.0012 | P
| P | 1 | QUALIFIED |
| 16 | 1481.807 | 722.911 | 2.0498 | P | 722.848 | 722.959 | 0.9998 | P
| F | 1 | QUALIFIED |
| 17 | 1543.292 | 765.278 | 2.0166 | P | 765.342 | 765.438 | 0.9999 | P
| F | 1 | QUALIFIED |
| 18 | 1600.077 | 808.030 | 1.9802 | P | 808.639 | 808.254 | 1.0005 | P
| P | 1 | QUALIFIED |
| 19 | 1661.757 | 850.782 | 1.9532 | P | 851.007 | 851.134 | 0.9999 | P
| F | 1 | QUALIFIED |
| 20 | 1719.005 | 893.726 | 1.9234 | P | 893.790 | 893.759 | 1.0000 | P
| P | 1 | QUALIFIED |
| 21 | 1781.597 | 936.430 | 1.9025 | P | 936.510 | 936.414 | 1.0001 | P
| P | 1 | QUALIFIED |
| 22 | 1856.860 | 979.070 | 1.8966 | P | 979.519 | 978.911 | 1.0006 | P
| P | 1 | QUALIFIED |
| 23 | 1932.203 | 1021.981 | 1.8906 | P | 1021.439 | 1021.999 | 0.9995 |
P | F | 1 | QUALIFIED |
| 24 | 1995.292 | 1064.542 | 1.8743 | P | 1064.094 | 1064.511 | 0.9996 |
P | F | 1 | QUALIFIED |
| 25 | 2025.828 | 1106.570 | 1.8307 | P | 1106.940 | 1106.845 | 1.0001 |
P | P | 1 | QUALIFIED |
| 26 | 2100.965 | 1149.194 | 1.8282 | P | 1149.486 | 1148.925 | 1.0005 |
P | P | 1 | QUALIFIED |
| 27 | 2158.438 | 1192.186 | 1.8105 | P | 1192.253 | 1192.157 | 1.0001 |
P | P | 1 | QUALIFIED |
| 28 | 2221.669 | 1234.361 | 1.7999 | P | 1235.421 | 1234.461 | 1.0008 |
P | P | 1 | QUALIFIED |
| 29 | 2272.469 | 1277.770 | 1.7785 | P | 1276.942 | 1276.862 | 1.0001 |
P | P | 1 | QUALIFIED |
| 30 | 2323.013 | 1319.738 | 1.7602 | P | 1319.806 | 1319.373 | 1.0003 |
P | P | 1 | QUALIFIED |
| 31 | 2367.372 | 1363.085 | 1.7368 | P | 1362.813 | 1362.269 | 1.0004 |
P | P | 1 | QUALIFIED |
| 32 | 2436.171 | 1405.822 | 1.7329 | P | 1405.977 | 1405.177 | 1.0006 |
P | P | 1 | QUALIFIED |

</details>

### sm_103a

<details><summary>Qwen3-30B-A3B (2048/768/128/8) — 31/32 pass both
gates, 31/32 baseline gate, 32/32 export gate (25/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 16.928 | 15.936 | 1.0622 | P | 16.032 | 15.936 | 1.0060 | P | P |
3 | QUALIFIED |
| 2 | 21.696 | 19.648 | 1.1042 | P | 20.032 | 19.648 | 1.0195 | P | P |
3 | QUALIFIED |
| 3 | 25.760 | 24.000 | 1.0733 | P | 24.096 | 24.000 | 1.0040 | P | P |
3 | QUALIFIED |
| 4 | 29.024 | 27.392 | 1.0596 | P | 27.392 | 27.328 | 1.0023 | P | P |
3 | QUALIFIED |
| 5 | 31.200 | 30.656 | 1.0177 | P | 30.720 | 30.657 | 1.0021 | P | P |
3 | QUALIFIED |
| 6 | 34.337 | 33.665 | 1.0200 | P | 33.504 | 33.665 | 0.9952 | P | F |
3 | QUALIFIED |
| 7 | 37.760 | 37.248 | 1.0137 | P | 36.896 | 37.280 | 0.9897 | P | F |
3 | QUALIFIED |
| 8 | 39.520 | 39.616 | 0.9976 | F | 39.712 | 39.616 | 1.0024 | P | P |
3 | BASELINE_FAIL |
| 9 | 41.600 | 41.217 | 1.0093 | P | 41.217 | 41.216 | 1.0000 | P | P |
1 | QUALIFIED |
| 10 | 42.912 | 42.529 | 1.0090 | P | 42.721 | 42.560 | 1.0038 | P | P |
1 | QUALIFIED |
| 11 | 44.353 | 43.713 | 1.0146 | P | 43.776 | 43.712 | 1.0015 | P | P |
1 | QUALIFIED |
| 12 | 45.664 | 45.249 | 1.0092 | P | 45.216 | 45.248 | 0.9993 | P | F |
1 | QUALIFIED |
| 13 | 47.744 | 47.136 | 1.0129 | P | 47.041 | 47.136 | 0.9980 | P | F |
1 | QUALIFIED |
| 14 | 48.352 | 47.777 | 1.0120 | P | 47.680 | 47.776 | 0.9980 | P | F |
1 | QUALIFIED |
| 15 | 50.304 | 49.344 | 1.0195 | P | 49.473 | 49.313 | 1.0032 | P | P |
1 | QUALIFIED |
| 16 | 51.297 | 50.272 | 1.0204 | P | 50.432 | 50.273 | 1.0032 | P | P |
1 | QUALIFIED |
| 17 | 53.472 | 51.776 | 1.0328 | P | 52.032 | 51.905 | 1.0024 | P | P |
1 | QUALIFIED |
| 18 | 54.912 | 53.440 | 1.0275 | P | 53.153 | 53.408 | 0.9952 | P | F |
1 | QUALIFIED |
| 19 | 55.297 | 53.665 | 1.0304 | P | 53.697 | 53.665 | 1.0006 | P | P |
1 | QUALIFIED |
| 20 | 55.904 | 54.721 | 1.0216 | P | 54.720 | 54.721 | 1.0000 | P | F |
1 | QUALIFIED |
| 21 | 57.089 | 56.001 | 1.0194 | P | 56.161 | 56.001 | 1.0029 | P | P |
1 | QUALIFIED |
| 22 | 58.049 | 57.217 | 1.0145 | P | 57.313 | 57.249 | 1.0011 | P | P |
1 | QUALIFIED |
| 23 | 58.048 | 56.992 | 1.0185 | P | 57.120 | 56.961 | 1.0028 | P | P |
1 | QUALIFIED |
| 24 | 58.561 | 57.473 | 1.0189 | P | 57.505 | 57.505 | 1.0000 | P | P |
1 | QUALIFIED |
| 25 | 60.256 | 59.329 | 1.0156 | P | 59.393 | 59.361 | 1.0005 | P | P |
1 | QUALIFIED |
| 26 | 62.336 | 61.216 | 1.0183 | P | 61.312 | 61.216 | 1.0016 | P | P |
1 | QUALIFIED |
| 27 | 62.689 | 61.537 | 1.0187 | P | 61.665 | 61.505 | 1.0026 | P | P |
1 | QUALIFIED |
| 28 | 63.041 | 61.953 | 1.0176 | P | 62.112 | 61.952 | 1.0026 | P | P |
1 | QUALIFIED |
| 29 | 64.193 | 62.945 | 1.0198 | P | 63.041 | 62.945 | 1.0015 | P | P |
1 | QUALIFIED |
| 30 | 64.513 | 63.424 | 1.0172 | P | 63.393 | 63.361 | 1.0005 | P | P |
1 | QUALIFIED |
| 31 | 65.600 | 64.385 | 1.0189 | P | 64.353 | 64.352 | 1.0000 | P | P |
1 | QUALIFIED |
| 32 | 65.633 | 64.288 | 1.0209 | P | 64.353 | 64.288 | 1.0010 | P | P |
1 | QUALIFIED |

</details>

<details><summary>Qwen3-235B-A22B (4096/1536/128/8) — 32/32 pass both
gates, 32/32 baseline gate, 32/32 export gate (14/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 35.296 | 33.632 | 1.0495 | P | 33.345 | 33.216 | 1.0039 | P | P |
1 | QUALIFIED |
| 2 | 52.801 | 44.385 | 1.1896 | P | 44.064 | 44.416 | 0.9921 | P | F |
1 | QUALIFIED |
| 3 | 67.328 | 58.177 | 1.1573 | P | 57.984 | 58.176 | 0.9967 | P | F |
1 | QUALIFIED |
| 4 | 79.825 | 69.056 | 1.1559 | P | 69.345 | 69.057 | 1.0042 | P | P |
1 | QUALIFIED |
| 5 | 90.401 | 79.201 | 1.1414 | P | 79.041 | 79.201 | 0.9980 | P | F |
1 | QUALIFIED |
| 6 | 103.137 | 89.665 | 1.1502 | P | 89.569 | 89.665 | 0.9989 | P | F |
1 | QUALIFIED |
| 7 | 117.217 | 102.241 | 1.1465 | P | 102.177 | 102.240 | 0.9994 | P |
F | 1 | QUALIFIED |
| 8 | 124.961 | 113.473 | 1.1012 | P | 114.657 | 113.505 | 1.0101 | P |
P | 1 | QUALIFIED |
| 9 | 132.546 | 124.386 | 1.0656 | P | 124.226 | 124.417 | 0.9985 | P |
F | 3 | QUALIFIED |
| 10 | 138.529 | 133.666 | 1.0364 | P | 133.762 | 133.538 | 1.0017 | P |
P | 2 | QUALIFIED |
| 11 | 144.258 | 120.193 | 1.2002 | P | 120.161 | 120.162 | 1.0000 | P |
F | 1 | QUALIFIED |
| 12 | 150.178 | 124.418 | 1.2070 | P | 124.514 | 124.418 | 1.0008 | P |
P | 2 | QUALIFIED |
| 13 | 157.666 | 130.466 | 1.2085 | P | 130.466 | 130.465 | 1.0000 | P |
P | 2 | QUALIFIED |
| 14 | 159.587 | 131.842 | 1.2104 | P | 132.033 | 131.810 | 1.0017 | P |
P | 2 | QUALIFIED |
| 15 | 166.626 | 137.954 | 1.2078 | P | 138.338 | 138.018 | 1.0023 | P |
P | 2 | QUALIFIED |
| 16 | 170.498 | 141.218 | 1.2073 | P | 141.537 | 141.218 | 1.0023 | P |
P | 1 | QUALIFIED |
| 17 | 176.675 | 145.794 | 1.2118 | P | 145.410 | 145.634 | 0.9985 | P |
F | 2 | QUALIFIED |
| 18 | 182.050 | 150.306 | 1.2112 | P | 149.986 | 150.306 | 0.9979 | P |
F | 2 | QUALIFIED |
| 19 | 184.130 | 151.842 | 1.2126 | P | 151.586 | 151.842 | 0.9983 | P |
F | 2 | QUALIFIED |
| 20 | 185.699 | 153.346 | 1.2110 | P | 153.122 | 153.186 | 0.9996 | P |
F | 2 | QUALIFIED |
| 21 | 189.667 | 156.322 | 1.2133 | P | 156.386 | 156.194 | 1.0012 | P |
P | 1 | QUALIFIED |
| 22 | 194.691 | 161.218 | 1.2076 | P | 160.674 | 160.962 | 0.9982 | P |
F | 2 | QUALIFIED |
| 23 | 195.107 | 161.058 | 1.2114 | P | 160.997 | 160.962 | 1.0002 | P |
P | 1 | QUALIFIED |
| 24 | 196.834 | 162.146 | 1.2139 | P | 162.434 | 162.339 | 1.0006 | P |
P | 1 | QUALIFIED |
| 25 | 203.939 | 168.546 | 1.2100 | P | 168.258 | 168.387 | 0.9992 | P |
F | 2 | QUALIFIED |
| 26 | 211.554 | 174.242 | 1.2141 | P | 173.922 | 174.178 | 0.9985 | P |
F | 1 | QUALIFIED |
| 27 | 213.026 | 175.714 | 1.2123 | P | 175.843 | 175.618 | 1.0013 | P |
P | 1 | QUALIFIED |
| 28 | 214.947 | 176.995 | 1.2144 | P | 177.250 | 177.090 | 1.0009 | P |
P | 1 | QUALIFIED |
| 29 | 218.723 | 179.970 | 1.2153 | P | 179.970 | 180.002 | 0.9998 | P |
F | 1 | QUALIFIED |
| 30 | 220.387 | 181.538 | 1.2140 | P | 181.219 | 181.490 | 0.9985 | P |
F | 1 | QUALIFIED |
| 31 | 224.099 | 184.515 | 1.2145 | P | 184.226 | 184.355 | 0.9993 | P |
F | 1 | QUALIFIED |
| 32 | 224.066 | 184.675 | 1.2133 | P | 184.291 | 184.707 | 0.9977 | P |
F | 1 | QUALIFIED |

</details>

<details><summary>Qwen3.5-35B-A3B (2048/512/256/8) — 32/32 pass both
gates, 32/32 baseline gate, 32/32 export gate (18/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 15.328 | 14.176 | 1.0813 | P | 14.112 | 14.176 | 0.9955 | P | F |
1 | QUALIFIED |
| 2 | 19.137 | 16.769 | 1.1412 | P | 16.704 | 16.800 | 0.9943 | P | F |
1 | QUALIFIED |
| 3 | 22.336 | 20.352 | 1.0975 | P | 20.544 | 20.352 | 1.0094 | P | P |
1 | QUALIFIED |
| 4 | 25.056 | 23.136 | 1.0830 | P | 23.392 | 23.136 | 1.0111 | P | P |
1 | QUALIFIED |
| 5 | 27.680 | 26.240 | 1.0549 | P | 26.049 | 26.240 | 0.9927 | P | F |
1 | QUALIFIED |
| 6 | 30.592 | 28.352 | 1.0790 | P | 28.385 | 28.352 | 1.0012 | P | P |
1 | QUALIFIED |
| 7 | 33.024 | 31.456 | 1.0498 | P | 31.360 | 31.457 | 0.9969 | P | F |
1 | QUALIFIED |
| 8 | 35.841 | 33.888 | 1.0576 | P | 33.889 | 33.857 | 1.0009 | P | P |
1 | QUALIFIED |
| 9 | 37.632 | 36.256 | 1.0380 | P | 36.704 | 36.288 | 1.0115 | P | P |
4 | QUALIFIED |
| 10 | 38.912 | 37.985 | 1.0244 | P | 37.857 | 37.985 | 0.9966 | P | F |
4 | QUALIFIED |
| 11 | 40.961 | 39.616 | 1.0340 | P | 39.809 | 39.617 | 1.0048 | P | P |
4 | QUALIFIED |
| 12 | 41.824 | 41.248 | 1.0140 | P | 41.985 | 41.248 | 1.0179 | P | P |
4 | QUALIFIED |
| 13 | 43.809 | 43.072 | 1.0171 | P | 43.104 | 43.073 | 1.0007 | P | P |
4 | QUALIFIED |
| 14 | 44.705 | 44.545 | 1.0036 | P | 44.544 | 44.544 | 1.0000 | P | P |
4 | QUALIFIED |
| 15 | 45.825 | 45.792 | 1.0007 | P | 46.049 | 45.888 | 1.0035 | P | P |
4 | QUALIFIED |
| 16 | 47.296 | 47.232 | 1.0014 | P | 47.392 | 47.456 | 0.9987 | P | F |
1 | QUALIFIED |
| 17 | 49.377 | 49.121 | 1.0052 | P | 49.153 | 49.345 | 0.9961 | P | F |
1 | QUALIFIED |
| 18 | 50.497 | 50.305 | 1.0038 | P | 49.856 | 50.176 | 0.9936 | P | F |
1 | QUALIFIED |
| 19 | 51.777 | 51.521 | 1.0050 | P | 51.297 | 51.489 | 0.9963 | P | F |
1 | QUALIFIED |
| 20 | 53.025 | 52.769 | 1.0049 | P | 52.417 | 52.640 | 0.9958 | P | F |
1 | QUALIFIED |
| 21 | 54.176 | 53.569 | 1.0113 | P | 53.761 | 53.600 | 1.0030 | P | P |
1 | QUALIFIED |
| 22 | 55.265 | 54.880 | 1.0070 | P | 54.945 | 54.881 | 1.0012 | P | P |
1 | QUALIFIED |
| 23 | 56.161 | 55.841 | 1.0057 | P | 55.905 | 55.873 | 1.0006 | P | P |
1 | QUALIFIED |
| 24 | 57.089 | 56.513 | 1.0102 | P | 56.449 | 56.544 | 0.9983 | P | F |
1 | QUALIFIED |
| 25 | 58.689 | 58.209 | 1.0082 | P | 58.305 | 58.209 | 1.0016 | P | P |
2 | QUALIFIED |
| 26 | 59.905 | 59.265 | 1.0108 | P | 59.585 | 59.265 | 1.0054 | P | P |
2 | QUALIFIED |
| 27 | 60.929 | 60.385 | 1.0090 | P | 60.289 | 60.417 | 0.9979 | P | F |
2 | QUALIFIED |
| 28 | 62.337 | 62.016 | 1.0052 | P | 61.952 | 61.985 | 0.9995 | P | F |
2 | QUALIFIED |
| 29 | 64.385 | 63.425 | 1.0151 | P | 63.617 | 63.424 | 1.0030 | P | P |
2 | QUALIFIED |
| 30 | 65.697 | 64.865 | 1.0128 | P | 64.960 | 64.960 | 1.0000 | P | P |
2 | QUALIFIED |
| 31 | 67.361 | 66.625 | 1.0110 | P | 66.433 | 66.561 | 0.9981 | P | F |
2 | QUALIFIED |
| 32 | 68.225 | 67.233 | 1.0148 | P | 67.297 | 67.201 | 1.0014 | P | P |
2 | QUALIFIED |

</details>

<details><summary>Qwen3.5-397B-A17B (4096/1024/512/10) — 32/32 pass both
gates, 32/32 baseline gate, 32/32 export gate (18/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 27.265 | 25.601 | 1.0650 | P | 25.985 | 25.600 | 1.0150 | P | P |
2 | QUALIFIED |
| 2 | 41.697 | 39.424 | 1.0577 | P | 39.456 | 39.424 | 1.0008 | P | P |
2 | QUALIFIED |
| 3 | 54.944 | 51.841 | 1.0599 | P | 52.161 | 51.872 | 1.0056 | P | P |
2 | QUALIFIED |
| 4 | 65.985 | 63.969 | 1.0315 | P | 63.712 | 63.808 | 0.9985 | P | F |
2 | QUALIFIED |
| 5 | 77.601 | 75.361 | 1.0297 | P | 75.233 | 75.361 | 0.9983 | P | F |
2 | QUALIFIED |
| 6 | 88.705 | 86.690 | 1.0232 | P | 86.208 | 86.689 | 0.9945 | P | F |
2 | QUALIFIED |
| 7 | 95.680 | 94.561 | 1.0118 | P | 94.337 | 94.593 | 0.9973 | P | F |
2 | QUALIFIED |
| 8 | 103.681 | 102.657 | 1.0100 | P | 102.561 | 102.657 | 0.9991 | P |
F | 2 | QUALIFIED |
| 9 | 112.898 | 111.681 | 1.0109 | P | 112.067 | 111.713 | 1.0032 | P |
P | 1 | QUALIFIED |
| 10 | 122.722 | 120.930 | 1.0148 | P | 121.154 | 120.961 | 1.0016 | P |
P | 1 | QUALIFIED |
| 11 | 128.674 | 127.009 | 1.0131 | P | 127.041 | 126.978 | 1.0005 | P |
P | 1 | QUALIFIED |
| 12 | 134.466 | 133.186 | 1.0096 | P | 133.218 | 133.217 | 1.0000 | P |
P | 1 | QUALIFIED |
| 13 | 142.626 | 141.153 | 1.0104 | P | 141.281 | 141.153 | 1.0009 | P |
P | 1 | QUALIFIED |
| 14 | 150.626 | 148.898 | 1.0116 | P | 148.994 | 148.930 | 1.0004 | P |
P | 1 | QUALIFIED |
| 15 | 159.586 | 157.762 | 1.0116 | P | 158.114 | 157.762 | 1.0022 | P |
P | 1 | QUALIFIED |
| 16 | 167.778 | 165.858 | 1.0116 | P | 165.570 | 165.826 | 0.9985 | P |
F | 2 | QUALIFIED |
| 17 | 174.947 | 168.577 | 1.0378 | P | 168.609 | 168.482 | 1.0008 | P |
P | 1 | QUALIFIED |
| 18 | 182.754 | 177.507 | 1.0296 | P | 177.634 | 177.506 | 1.0007 | P |
P | 1 | QUALIFIED |
| 19 | 190.466 | 185.218 | 1.0283 | P | 185.282 | 185.250 | 1.0002 | P |
P | 1 | QUALIFIED |
| 20 | 197.538 | 191.138 | 1.0335 | P | 191.330 | 191.075 | 1.0013 | P |
P | 1 | QUALIFIED |
| 21 | 202.242 | 197.698 | 1.0230 | P | 197.410 | 197.730 | 0.9984 | P |
F | 2 | QUALIFIED |
| 22 | 207.554 | 201.188 | 1.0316 | P | 201.602 | 201.154 | 1.0022 | P |
P | 1 | QUALIFIED |
| 23 | 212.579 | 206.594 | 1.0290 | P | 206.306 | 206.530 | 0.9989 | P |
F | 2 | QUALIFIED |
| 24 | 218.306 | 212.418 | 1.0277 | P | 211.938 | 212.419 | 0.9977 | P |
F | 2 | QUALIFIED |
| 25 | 222.819 | 217.602 | 1.0240 | P | 217.986 | 217.603 | 1.0018 | P |
P | 1 | QUALIFIED |
| 26 | 227.971 | 222.563 | 1.0243 | P | 222.787 | 222.882 | 0.9996 | P |
F | 2 | QUALIFIED |
| 27 | 233.955 | 227.426 | 1.0287 | P | 227.395 | 227.394 | 1.0000 | P |
P | 1 | QUALIFIED |
| 28 | 237.378 | 231.235 | 1.0266 | P | 230.531 | 230.882 | 0.9985 | P |
F | 2 | QUALIFIED |
| 29 | 243.427 | 238.402 | 1.0211 | P | 238.115 | 238.435 | 0.9987 | P |
F | 2 | QUALIFIED |
| 30 | 246.659 | 241.603 | 1.0209 | P | 241.763 | 241.603 | 1.0007 | P |
P | 1 | QUALIFIED |
| 31 | 254.019 | 248.131 | 1.0237 | P | 247.042 | 247.747 | 0.9972 | P |
F | 2 | QUALIFIED |
| 32 | 256.803 | 252.835 | 1.0157 | P | 252.580 | 252.643 | 0.9998 | P |
F | 1 | QUALIFIED |

</details>

<details><summary>MiniMax-M2 (3072/1536/256/8) — 32/32 pass both gates,
32/32 baseline gate, 32/32 export gate (15/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 30.753 | 28.992 | 1.0607 | P | 28.992 | 28.992 | 1.0000 | P | P |
1 | QUALIFIED |
| 2 | 43.904 | 35.616 | 1.2327 | P | 35.744 | 35.616 | 1.0036 | P | P |
1 | QUALIFIED |
| 3 | 56.832 | 47.393 | 1.1992 | P | 47.328 | 47.393 | 0.9986 | P | F |
1 | QUALIFIED |
| 4 | 69.184 | 58.752 | 1.1776 | P | 58.624 | 58.817 | 0.9967 | P | F |
1 | QUALIFIED |
| 5 | 79.169 | 67.457 | 1.1736 | P | 67.521 | 67.425 | 1.0014 | P | P |
1 | QUALIFIED |
| 6 | 92.097 | 77.713 | 1.1851 | P | 77.634 | 77.697 | 0.9992 | P | F |
1 | QUALIFIED |
| 7 | 104.609 | 87.617 | 1.1939 | P | 87.457 | 87.617 | 0.9982 | P | F |
1 | QUALIFIED |
| 8 | 115.201 | 97.025 | 1.1873 | P | 96.865 | 97.025 | 0.9984 | P | F |
1 | QUALIFIED |
| 9 | 125.217 | 105.953 | 1.1818 | P | 105.377 | 105.953 | 0.9946 | P |
F | 1 | QUALIFIED |
| 10 | 130.817 | 111.810 | 1.1700 | P | 111.809 | 111.809 | 1.0000 | P |
P | 1 | QUALIFIED |
| 11 | 139.169 | 118.721 | 1.1722 | P | 118.658 | 118.722 | 0.9995 | P |
F | 1 | QUALIFIED |
| 12 | 143.521 | 127.362 | 1.1269 | P | 126.818 | 127.393 | 0.9955 | P |
F | 1 | QUALIFIED |
| 13 | 152.066 | 134.977 | 1.1266 | P | 134.658 | 134.946 | 0.9979 | P |
F | 1 | QUALIFIED |
| 14 | 156.161 | 142.498 | 1.0959 | P | 142.401 | 142.497 | 0.9993 | P |
F | 1 | QUALIFIED |
| 15 | 161.762 | 151.169 | 1.0701 | P | 151.713 | 151.298 | 1.0027 | P |
P | 1 | QUALIFIED |
| 16 | 167.746 | 138.497 | 1.2112 | P | 138.305 | 138.497 | 0.9986 | P |
F | 1 | QUALIFIED |
| 17 | 174.914 | 168.673 | 1.0370 | P | 168.866 | 168.769 | 1.0006 | P |
P | 1 | QUALIFIED |
| 18 | 178.850 | 176.322 | 1.0143 | P | 175.713 | 176.098 | 0.9978 | P |
F | 1 | QUALIFIED |
| 19 | 184.418 | 152.001 | 1.2133 | P | 151.746 | 151.905 | 0.9990 | P |
F | 1 | QUALIFIED |
| 20 | 189.731 | 156.259 | 1.2142 | P | 156.355 | 156.290 | 1.0004 | P |
P | 1 | QUALIFIED |
| 21 | 193.762 | 159.617 | 1.2139 | P | 159.746 | 159.777 | 0.9998 | P |
F | 1 | QUALIFIED |
| 22 | 199.650 | 163.970 | 1.2176 | P | 163.938 | 164.034 | 0.9994 | P |
F | 1 | QUALIFIED |
| 23 | 203.650 | 167.234 | 1.2178 | P | 167.489 | 167.234 | 1.0015 | P |
P | 1 | QUALIFIED |
| 24 | 206.402 | 169.538 | 1.2174 | P | 169.889 | 169.538 | 1.0021 | P |
P | 1 | QUALIFIED |
| 25 | 213.506 | 175.330 | 1.2177 | P | 175.586 | 175.298 | 1.0016 | P |
P | 1 | QUALIFIED |
| 26 | 220.131 | 180.866 | 1.2171 | P | 180.641 | 180.770 | 0.9993 | P |
F | 1 | QUALIFIED |
| 27 | 224.067 | 184.162 | 1.2167 | P | 184.098 | 184.098 | 1.0000 | P |
P | 1 | QUALIFIED |
| 28 | 232.258 | 190.626 | 1.2184 | P | 190.690 | 190.626 | 1.0003 | P |
P | 1 | QUALIFIED |
| 29 | 238.882 | 196.002 | 1.2188 | P | 196.258 | 196.066 | 1.0010 | P |
P | 1 | QUALIFIED |
| 30 | 245.699 | 201.762 | 1.2178 | P | 201.506 | 201.763 | 0.9987 | P |
F | 1 | QUALIFIED |
| 31 | 254.115 | 208.322 | 1.2198 | P | 208.355 | 208.339 | 1.0001 | P |
P | 1 | QUALIFIED |
| 32 | 258.050 | 211.618 | 1.2194 | P | 211.714 | 211.554 | 1.0008 | P |
P | 1 | QUALIFIED |

</details>

<details><summary>MiniMax-M3 (6144/3072/128/4, SwiGLU α=1.702 β=1
clamp=7) — 32/32 pass both gates, 32/32 baseline gate, 32/32 export gate
(23/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 38.752 | 36.577 | 1.0595 | P | 36.960 | 36.577 | 1.0105 | P | P |
2 | QUALIFIED |
| 2 | 59.937 | 58.177 | 1.0303 | P | 58.369 | 58.177 | 1.0033 | P | P |
2 | QUALIFIED |
| 3 | 81.377 | 78.241 | 1.0401 | P | 78.049 | 78.273 | 0.9971 | P | F |
2 | QUALIFIED |
| 4 | 100.482 | 97.537 | 1.0302 | P | 97.761 | 97.537 | 1.0023 | P | P |
2 | QUALIFIED |
| 5 | 110.049 | 108.193 | 1.0172 | P | 108.033 | 108.193 | 0.9985 | P |
F | 2 | QUALIFIED |
| 6 | 127.713 | 126.242 | 1.0117 | P | 126.402 | 126.242 | 1.0013 | P |
P | 2 | QUALIFIED |
| 7 | 145.026 | 144.018 | 1.0070 | P | 143.778 | 144.034 | 0.9982 | P |
F | 2 | QUALIFIED |
| 8 | 158.242 | 157.027 | 1.0077 | P | 157.282 | 157.058 | 1.0014 | P |
P | 2 | QUALIFIED |
| 9 | 176.515 | 175.523 | 1.0057 | P | 175.618 | 175.523 | 1.0005 | P |
P | 1 | QUALIFIED |
| 10 | 181.442 | 179.618 | 1.0102 | P | 179.970 | 179.619 | 1.0020 | P |
P | 1 | QUALIFIED |
| 11 | 190.115 | 188.706 | 1.0075 | P | 189.091 | 188.674 | 1.0022 | P |
P | 1 | QUALIFIED |
| 12 | 198.946 | 197.059 | 1.0096 | P | 197.443 | 197.154 | 1.0015 | P |
P | 1 | QUALIFIED |
| 13 | 216.419 | 215.171 | 1.0058 | P | 214.787 | 215.010 | 0.9990 | P |
F | 1 | QUALIFIED |
| 14 | 216.611 | 214.723 | 1.0088 | P | 215.075 | 214.659 | 1.0019 | P |
P | 1 | QUALIFIED |
| 15 | 234.099 | 232.803 | 1.0056 | P | 232.803 | 232.835 | 0.9999 | P |
F | 1 | QUALIFIED |
| 16 | 242.851 | 241.155 | 1.0070 | P | 241.987 | 241.315 | 1.0028 | P |
P | 1 | QUALIFIED |
| 17 | 255.907 | 254.500 | 1.0055 | P | 254.947 | 254.723 | 1.0009 | P |
P | 1 | QUALIFIED |
| 18 | 269.028 | 267.684 | 1.0050 | P | 267.940 | 267.811 | 1.0005 | P |
P | 1 | QUALIFIED |
| 19 | 277.988 | 276.500 | 1.0054 | P | 276.739 | 276.516 | 1.0008 | P |
P | 1 | QUALIFIED |
| 20 | 278.020 | 276.676 | 1.0049 | P | 276.900 | 276.644 | 1.0009 | P |
P | 1 | QUALIFIED |
| 21 | 291.236 | 289.893 | 1.0046 | P | 289.828 | 289.892 | 0.9998 | P |
F | 1 | QUALIFIED |
| 22 | 299.908 | 298.628 | 1.0043 | P | 298.245 | 298.468 | 0.9993 | P |
F | 1 | QUALIFIED |
| 23 | 305.092 | 303.204 | 1.0062 | P | 302.980 | 302.949 | 1.0001 | P |
P | 1 | QUALIFIED |
| 24 | 313.221 | 311.844 | 1.0044 | P | 311.908 | 311.861 | 1.0002 | P |
P | 1 | QUALIFIED |
| 25 | 331.508 | 329.125 | 1.0072 | P | 329.125 | 328.900 | 1.0007 | P |
P | 1 | QUALIFIED |
| 26 | 339.749 | 338.052 | 1.0050 | P | 338.085 | 338.085 | 1.0000 | P |
P | 1 | QUALIFIED |
| 27 | 344.357 | 342.404 | 1.0057 | P | 342.341 | 342.501 | 0.9995 | P |
F | 1 | QUALIFIED |
| 28 | 352.997 | 352.229 | 1.0022 | P | 351.237 | 352.261 | 0.9971 | P |
F | 1 | QUALIFIED |
| 29 | 362.629 | 360.357 | 1.0063 | P | 360.261 | 360.005 | 1.0007 | P |
P | 1 | QUALIFIED |
| 30 | 375.077 | 373.173 | 1.0051 | P | 373.477 | 373.157 | 1.0009 | P |
P | 1 | QUALIFIED |
| 31 | 388.358 | 386.598 | 1.0046 | P | 386.758 | 386.629 | 1.0003 | P |
P | 1 | QUALIFIED |
| 32 | 388.422 | 386.630 | 1.0046 | P | 387.238 | 386.662 | 1.0015 | P |
P | 1 | QUALIFIED |

</details>

<details><summary>Kimi-K3 latent expert bank (3584/3072/896/16, SiTU
gate 4 / linear 25) — 32/32 pass both gates, 32/32 baseline gate, 32/32
export gate (16/32 strict)</summary>

| tokens | baseline B µs | export E_o µs | B/E_o | baseline gate |
source S µs | export E_s µs | S/E_s | export gate (≥ 0.97) | strict (≥
1) | paired attempts | status |
|---:|---:|---:|---:|---|---:|---:|---:|---|---|---:|---|
| 1 | 121.154 | 77.504 | 1.5632 | P | 77.537 | 77.473 | 1.0008 | P | P |
1 | QUALIFIED |
| 2 | 213.730 | 122.066 | 1.7509 | P | 121.889 | 122.049 | 0.9987 | P |
F | 1 | QUALIFIED |
| 3 | 311.779 | 167.585 | 1.8604 | P | 167.906 | 167.618 | 1.0017 | P |
P | 1 | QUALIFIED |
| 4 | 403.972 | 212.322 | 1.9026 | P | 212.002 | 212.434 | 0.9980 | P |
F | 1 | QUALIFIED |
| 5 | 487.973 | 256.642 | 1.9014 | P | 257.346 | 256.451 | 1.0035 | P |
P | 1 | QUALIFIED |
| 6 | 581.574 | 301.443 | 1.9293 | P | 301.379 | 301.395 | 0.9999 | P |
F | 1 | QUALIFIED |
| 7 | 671.271 | 345.859 | 1.9409 | P | 346.692 | 345.987 | 1.0020 | P |
P | 1 | QUALIFIED |
| 8 | 758.728 | 390.148 | 1.9447 | P | 389.795 | 389.828 | 0.9999 | P |
F | 1 | QUALIFIED |
| 9 | 843.561 | 434.660 | 1.9407 | P | 434.372 | 434.341 | 1.0001 | P |
P | 1 | QUALIFIED |
| 10 | 928.842 | 479.077 | 1.9388 | P | 478.309 | 479.045 | 0.9985 | P |
F | 1 | QUALIFIED |
| 11 | 1020.652 | 522.629 | 1.9529 | P | 523.731 | 523.201 | 1.0010 | P
| P | 1 | QUALIFIED |
| 12 | 1110.556 | 567.718 | 1.9562 | P | 567.735 | 567.367 | 1.0006 | P
| P | 1 | QUALIFIED |
| 13 | 1176.637 | 610.983 | 1.9258 | P | 610.726 | 611.014 | 0.9995 | P
| F | 1 | QUALIFIED |
| 14 | 1268.334 | 654.056 | 1.9392 | P | 654.808 | 654.872 | 0.9999 | P
| F | 1 | QUALIFIED |
| 15 | 1353.343 | 699.608 | 1.9344 | P | 700.184 | 699.880 | 1.0004 | P
| P | 1 | QUALIFIED |
| 16 | 1432.145 | 743.657 | 1.9258 | P | 744.298 | 743.785 | 1.0007 | P
| P | 1 | QUALIFIED |
| 17 | 1490.467 | 788.538 | 1.8902 | P | 788.652 | 788.396 | 1.0003 | P
| P | 1 | QUALIFIED |
| 18 | 1544.821 | 831.338 | 1.8582 | P | 832.091 | 832.235 | 0.9998 | P
| F | 1 | QUALIFIED |
| 19 | 1604.949 | 876.028 | 1.8321 | P | 876.155 | 876.492 | 0.9996 | P
| F | 1 | QUALIFIED |
| 20 | 1659.334 | 921.821 | 1.8001 | P | 920.316 | 920.797 | 0.9995 | P
| F | 1 | QUALIFIED |
| 21 | 1719.319 | 964.013 | 1.7835 | P | 964.652 | 963.661 | 1.0010 | P
| P | 1 | QUALIFIED |
| 22 | 1792.168 | 1008.045 | 1.7779 | P | 1010.158 | 1008.078 | 1.0021 |
P | P | 1 | QUALIFIED |
| 23 | 1864.908 | 1052.496 | 1.7719 | P | 1052.478 | 1052.430 | 1.0000 |
P | P | 1 | QUALIFIED |
| 24 | 1925.696 | 1096.255 | 1.7566 | P | 1096.047 | 1096.080 | 1.0000 |
P | F | 1 | QUALIFIED |
| 25 | 1955.851 | 1140.463 | 1.7150 | P | 1140.481 | 1139.873 | 1.0005 |
P | P | 1 | QUALIFIED |
| 26 | 2027.548 | 1183.712 | 1.7129 | P | 1183.135 | 1183.269 | 0.9999 |
P | F | 1 | QUALIFIED |
| 27 | 2082.653 | 1228.513 | 1.6953 | P | 1227.650 | 1228.451 | 0.9993 |
P | F | 1 | QUALIFIED |
| 28 | 2144.494 | 1271.522 | 1.6866 | P | 1273.342 | 1271.808 | 1.0012 |
P | P | 1 | QUALIFIED |
| 29 | 2193.280 | 1315.459 | 1.6673 | P | 1315.794 | 1317.138 | 0.9990 |
P | F | 1 | QUALIFIED |
| 30 | 2243.376 | 1359.380 | 1.6503 | P | 1360.403 | 1360.499 | 0.9999 |
P | F | 1 | QUALIFIED |
| 31 | 2286.193 | 1405.572 | 1.6265 | P | 1404.558 | 1405.694 | 0.9992 |
P | F | 1 | QUALIFIED |
| 32 | 2350.306 | 1448.965 | 1.6221 | P | 1448.436 | 1448.100 | 1.0002 |
P | P | 1 | QUALIFIED |

</details>


🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [797872e](https://github.com/flashinfer-ai/flashinfer/commit/797872eac1b44338ca78d89d30993391fc2fd807)

- **作者**: eigen
- **时间**: 2026-09-25T23:56:04Z
- **提交信息**: feat(cake_kda): dense-beta unbounded coverage, measured affine break-even, sm_103a constants (#5543)

## KDA prepared prefill: dense-beta unbounded coverage, measured affine
break-even, sm_103a constants

Follow-up to #5452 (merged as 71f724405): same program families plus the
four dense-beta rows below, a measured affine-split break-even and
sm_103a constants. Closes the two follow-ups left open there. A second
round added a cheaper plan-cache hit path and 256-token affine windows
(section 3).

### 1. Dense H12 beta on the unbounded softplus gate was unexported

A contiguous `[tokens, 12]` beta (token stride 12) selects the
pair-packed beta TensorMap. Only bounded-gate programs existed for it,
so an unbounded caller with a dense beta raised `NotImplementedError:
Unexported KDA schedule specialization` on SM100 and SM103. The registry
now carries the unbounded pair-packed variants (sequential body, FP32
checkpoint rows, and the affine slab parts) for both arches, resolved
from four new fixture rows (2048, 8192, 8128+64, 4096 without
checkpoints) and validated bitwise against the source (359/359 rows per
arch, see below).

New test:
`tests/kda/test_kda_prefill_plan_cache.py::test_dense_h12_beta_matches_the_strided_carrier_on_the_unbounded_gate`
compares the dense and strided layouts bitwise on the sequential body
and on the affine split.

### 2. Affine split break-even is now a measured cost model

The packed-call gate compared the longest member against a fixed
256-chunk threshold, so an 8128-token member (254 chunks) ran the
sequential body (B200: 1.03 ms vs 0.42 ms composite; unbounded
2×(8128+64) was 0.76–0.87x of Triton) while bounded H16 2×8192 took the
split and lost (0.62 vs 0.47 ms).

`cake_kda_tf32_runtime.py` now estimates both routes from a per-arch,
per-gate linear model fitted on forced-split / forced-sequential grids
(profiler GPU time, plan-cache hits) and splits iff the composite is
cheaper:

| arch | gate | composite (us) | sequential (us) |
|---|---|---|---|
| SM100 (B200) | unbounded softplus, FP32 rows | 75 + 14.2 × max chunks
per window | 20 + 4.0 × longest chunks |
| SM100 | bounded | 84 + 8.8 × | 16 + 1.75 × |
| SM103 (GB300) | unbounded softplus, FP32 rows | 95 + 11.7 × | 18 + 3.6
× |
| SM103 | bounded | 83 + 7.8 × | 14 + 1.66 × |

Windows: one CTA wave (`sm_count // heads` windows) shared by greedy
LPT, at least 8 chunks (256 tokens) each so every launch stays on an
exported slab specialization. `FLASHINFER_KDA_AFFINE_POLICY=legacy`
restores the previous thresholds.

### 3. Plan-cache hit path and window floor (round 2 of this PR)

The bench rows that lost on CUDA-event time only (GPU ratio above 1)
carried ~90 us of host work per plan-cache hit:
`KDAPrefillPlanCache.get` re-derived the structural signature and
re-pointed all 45 views / 14 TMA descriptors of the affine composite on
every call. Four changes in `kda_prefill.py` /
`cake_kda_tf32_runtime.py`, all host-side and bitwise-neutral:

- `get` records the address-level facts (`data_ptr`, shape, stride,
dtype) of the tensors an entry is bound to (at `put` and after each
rebind). A repeat call with identical facts and scalars returns the
prepared launch without any rebind (`fast_hits`); a call where only some
inputs moved (serving allocates the output and the int32 state indices
per call) re-points only those inputs' views and descriptors.
- Signature and facts come from one pass over the inputs
(`rebind_signature_and_facts`).
- The parts of the affine composite launch inside the composite's stream
context, and the int64 copy of the state indices follows the first chain
kernel instead of preceding it.
- `AFFINE_MIN_CHUNKS_PER_WINDOW` 16 → 8 (256-token windows). The 359-row
re-export on both arches added no program variant, i.e. the
256..511-token launch class was already exported; only the < 256-token
class is not. `FLASHINFER_KDA_AFFINE_WINDOW_WAVES` (default 1) exposes
the resident-window budget for A/B; two waves measured slower on every
bench_tb shape.

Composite hit cost (B200, cProfile, 200 hits): 89–92 us → 52–55 us; the
composite's event time drops 55–70 us per call. Serving-style repeats
(fresh output tensor per call) take the partial-rebind path; exact
repeats (static buffers, CUDA-graph replay) take the memo path. Tests:
`test_repeat_call_on_unchanged_tensors_skips_the_rebind_and_stays_bitwise`,
`test_hit_with_a_fresh_output_only_repoints_the_output_and_stays_bitwise`.

### 4. Window budget and one-kernel index preparation (round 3 of this
PR)

- **Window budget.** The composite planned `sm_count // heads` windows
per resident wave and shared them across every sequence of a packed
call, so the two 64-token members of 2×(8128+64) each took a window from
the two 254-chunk members (H16 on 148 SMs: 4+3 windows of 86 chunks
instead of 2×8192's 5+4 of 64). Sequences whose window target is one
cannot split and their CTAs finish a one- or two-chunk chain long before
a wave of long windows ends, so they now receive their window on top of
the wave budget (`_affine_window_budget(..., unsplittable=)`).
2×(8128+64) plans exactly 2×8192's windows on one wave; H12 gains its
twelfth window (6+6 of 44 chunks instead of 5+5 of 52). No program
changes.
- **Index preparation.** The composite launch issued `index_copy_`,
`index_select` and `add_` before its first chain kernel and an int64
copy after it, four launches on the host path the GPU waits on. The
fused-epilogue JIT module now also exports `index_prep`: one kernel
writes the window state indices, the in-place row starts and the int64
state indices (2.5 us of GPU time for the four kernels' ~11 us). The
torch sequence remains the fallback when the fused epilogue is
unavailable; `test_affine_fused_epilogue_matches_torch_epilogue_bitwise`
covers both paths.
- **Partial rebind.** `RebindPlan` keeps its specs grouped by caller
input, so rebinding the inputs that move on every serving call (output,
checkpoint rows, `cu_seqlens`) walks only their specs.

Whole-call cost of the serving adapter's layer call (B200, cProfile, 200
plan-cache hits): 263 → 226 us (`launch()` 137 → 105 us). Paired lanes
on one B200 (A B A B, GPU ms / event ms of the prepared path, ratio vs
Triton):

| row | previous head | + window budget | + index prep |
|---|---|---|---|
| unbounded H16 2×(8128+64) | 0.976 / 1.173 (1.00x / 0.93x) | 0.926 /
1.119 (1.05x / 0.98x) | 0.930 / 1.094 (1.05x / 1.00x) |
| unbounded H16 2×8192 | 0.903 / 1.099 (1.07x / 0.99x) | 0.905 / 1.098
(1.07x / 0.99x) | 0.920 / 1.089 (1.05x / 1.00x) |
| unbounded H12 2×(8128+64) | 0.760 / 0.950 (1.12x / 1.02x) | 0.670 /
0.865 (1.27x / 1.13x) | 0.685 / 0.840 (1.24x / 1.15x) |
| unbounded H12 2×8192 | 0.666 / 0.853 (1.28x / 1.14x) | 0.668 / 0.854
(1.27x / 1.14x) | 0.677 / 0.833 (1.26x / 1.16x) |

Forced-wave sweep (`FLASHINFER_KDA_AFFINE_WINDOW_WAVES`, previous head,
B200 GPU ms): H16 2×(8128+64) 1.125 / 0.974 / 1.002 / 1.005 for 1–4
waves; H16 2×8192 0.905 / 0.922 / 0.978 / 0.978. More than two waves
never wins; with the budget fix the model keeps one wave for both rows.

Measured but not changed here: the FP32 checkpoint-row stores of the
fused body sit on the recurrence chain (1.1 us per 64-token row: H16
8192 sequential 0.936 ms with rows, 0.793 ms without; the address load
itself costs 6 us). Moving them to the epilogue warps is a kernel change
for a later PR.

### 5. Host critical path before the first chain kernel (round 4 of this
PR)
On a serving-shaped call the plan cache never memo-hits (`out`, the FP32
checkpoint rows and `cu_seqlens` move every call), so each call paid,
before the composite's first chain kernel: the facts pass over the 14
rebind inputs (29 us), the rebind of every part's aliasing arguments (26
us), a `torch.cuda.device` context (~8 us) and
`tvm_ffi.use_torch_stream()` (a `torch.cuda.Stream` plus a device-string
parse, ~10 us). The GPU side of the unbounded H16 layer 2x(8128+64) row
was already 5 % faster than Triton while its event time sat at parity,
because the host lead to the first kernel was ~160 us against Triton's
~110 us.

- `rebind_signature_and_facts` reads each tensor once through the
cheapest accessors (`torch.Size` kept as the shape, `dtype.itemsize`,
`get_device()`); the recorded `(pointer, shape, stride, dtype)` facts
are handed to the rebind, which never re-reads tensor metadata.
- `rebind_prepared_launch(..., defer_parts=("_map", "_correction"))`
applies the main part's and the composite's own specs immediately and
records the map/correction specs; `flush_deferred_rebind` applies them
right after the main part is issued (while it runs), before any new
rebind of the same launch and before `prepare_descriptors`. A hit whose
launch is skipped cannot leave a part bound to stale addresses
(`test_deferred_part_rebinds_flush_before_another_hit_and_land_in_the_newest_output`).
- `_ffi_stream_context` enters the FFI stream context from
`torch._C._cuda_getCurrentRawStream` and a cached `tvm_ffi.device`
(falls back to `use_torch_stream`).
- The facade skips the `torch.cuda.device` context on hits when the
input device is already current.

No program or descriptor changed. Paired lanes on B200 (A B A B, a =
previous head, b = this change): H16 2x(8128+64) event 1.101 / 1.091 ->
1.077 / 1.074 ms (0.999x / 1.003x -> 1.022x / 1.020x) with GPU time
unchanged; H16 2x8192 event 0.995x / 1.005x -> 1.020x / 1.017x; H12
2x(8128+64) 1.146x -> 1.175x. On GB300 (same arms): H16 2x(8128+64)
event 1.082 / 1.074 -> 1.054 / 1.044 ms (1.023x / 1.017x -> 1.041x /
1.042x) with GPU time unchanged; H16 2x8192 event 1.024x / 1.032x ->
1.045x / 1.036x; H12 2x(8128+64) 1.109x / 1.095x -> 1.152x / 1.157x.

### Speedup vs Triton (bench_tb, same GPU, same inputs, FP32 state, rows
every 64)

Same harness as #5452 (serving-adapter layer call of the prepared export
vs the Triton `chunk_kda` path, fresh identically seeded inputs per arm,
FP32 state pool, checkpoint rows every 64 tokens; GPU time = profiler
CUDA activity per call, event = CUDA-event wall around the layer call).
Numbers are from the final branch head. Rows below 1 are marked; they
are the unbounded-gate two-sequence long packs, where the affine
composite runs three near-equal chain passes (two of the three rows per
arch are within 1–3 % on event time with GPU ratios of 1.05–1.14x; the
third takes the sequential body and also loses on GPU time); every
K3-shape bounded row and every wrapper row is above 1 on both arches.

**B200 (SM100, 148 SMs), serial lanes on one GPU — K3 shape, bounded
lb=-5, H12, layer** (Triton / prepared ms; speedup = Triton ÷ prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 8192 | 0.599 | 0.275 | 2.17x | 0.726 | 0.478 | 1.52x | 0.0052 | 0.0036
|
| 16384 | 1.137 | 0.458 | 2.48x | 1.265 | 0.727 | 1.74x | 0.0052 |
0.0041 |
| 2x8192 | 0.840 | 0.463 | 1.81x | 0.967 | 0.702 | 1.38x | 0.0052 |
0.0042 |
| 3000+13384 | 1.032 | 0.483 | 2.14x | 1.160 | 0.747 | 1.55x | 0.0052 |
0.0041 |
| 4x4096 | 0.694 | 0.243 | 2.86x | 0.821 | 0.481 | 1.71x | 0.0052 |
0.0039 |
| 2x(8128+64) | 0.837 | 0.458 | 1.83x | 0.963 | 0.699 | 1.38x | 0.0052 |
0.0042 |
| 8x(1024+64) | 0.371 | 0.122 | 3.03x | 0.513 | 0.312 | 1.65x | 0.0041 |
0.0017 |
| 32768 | 2.245 | 0.807 | 2.78x | 2.378 | 1.203 | 1.98x | 0.0052 |
0.0043 |

**B200 (SM100, 148 SMs), serial lanes on one GPU — K3 shape, bounded
lb=-5, H16, layer** (Triton / prepared ms; speedup = Triton ÷ prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 8192 | 0.639 | 0.338 | 1.89x | 0.765 | 0.568 | 1.35x | 0.0052 | 0.0038
|
| 16384 | 1.247 | 0.569 | 2.19x | 1.370 | 0.880 | 1.56x | 0.0052 |
0.0040 |
| 2x8192 | 0.948 | 0.464 | 2.05x | 1.067 | 0.745 | 1.43x | 0.0052 |
0.0039 |
| 3000+13384 | 1.145 | 0.585 | 1.96x | 1.264 | 0.893 | 1.42x | 0.0052 |
0.0038 |
| 4x4096 | 0.809 | 0.245 | 3.30x | 0.927 | 0.528 | 1.76x | 0.0052 |
0.0040 |
| 2x(8128+64) | 0.955 | 0.461 | 2.07x | 1.073 | 0.741 | 1.45x | 0.0052 |
0.0039 |
| 8x(1024+64) | 0.442 | 0.111 | 3.99x | 0.578 | 0.326 | 1.78x | 0.0052 |
0.0040 |
| 32768 | 2.427 | 1.033 | 2.35x | 2.568 | 1.512 | 1.70x | 0.0052 |
0.0041 |

**B200 (SM100, 148 SMs), serial lanes on one GPU — Kimi-Linear shape,
unbounded, H12, layer** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 8192 | 0.605 | 0.389 | 1.56x | 0.726 | 0.528 | 1.38x | 0.0040 | 0.0022
|
| 16384 | 1.147 | 0.676 | 1.70x | 1.265 | 0.825 | 1.53x | 0.0040 |
0.0019 |
| 2x8192 | 0.852 | 0.675 | 1.26x | 0.972 | 0.815 | 1.19x | 0.0040 |
0.0019 |
| 3000+13384 | 1.042 | 0.728 | 1.43x | 1.162 | 0.869 | 1.34x | 0.0040 |
0.0024 |
| 4x4096 | 0.704 | 0.551 | 1.28x | 0.820 | 0.679 | 1.21x | 0.0040 |
0.0020 |
| 2x(8128+64) | 0.846 | 0.681 | 1.24x | 0.965 | 0.821 | 1.18x | 0.0040 |
0.0020 |
| 8x(1024+64) | 0.377 | 0.165 | 2.28x | 0.512 | 0.284 | 1.81x | 0.0039 |
0.0020 |
| 32768 | 2.264 | 1.229 | 1.84x | 2.392 | 1.366 | 1.75x | 0.0040 |
0.0021 |

**B200 (SM100, 148 SMs), serial lanes on one GPU — Kimi-Linear shape,
unbounded, H16, layer** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 8192 | 0.648 | 0.490 | 1.32x | 0.767 | 0.630 | 1.22x | 0.0040 | 0.0020
|
| 16384 | 1.263 | 0.856 | 1.48x | 1.386 | 0.997 | 1.39x | 0.0040 |
0.0021 |
| 2x8192 | 0.964 | 0.916 | 1.05x | 1.086 | 1.054 | 1.03x | 0.0040 |
0.0021 |
| 3000+13384 | 1.161 | 0.874 | 1.33x | 1.287 | 1.014 | 1.27x | 0.0040 |
0.0025 |
| 4x4096 | 0.823 | 0.568 | 1.45x | 0.947 | 0.706 | 1.34x | 0.0040 |
0.0022 |
| 2x(8128+64) | 0.973 | 0.931 | 1.05x | 1.095 | 1.072 | 1.02x | 0.0040 |
0.0021 |
| 8x(1024+64) | 0.451 | 0.168 | 2.68x | 0.582 | 0.290 | 2.01x | 0.0040 |
0.0021 |
| 32768 | 2.458 | 1.566 | 1.57x | 2.596 | 1.714 | 1.51x | 0.0040 |
0.0021 |

**B200 (SM100, 148 SMs), serial lanes on one GPU — K3 shape, bounded
lb=-5, H12, wrapper** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| BS4 x T64 | 0.055 | 0.015 | 3.64x | 0.246 | 0.151 | 1.63x | 0.0053 |
0.0039 |
| BS16 x T64 | 0.080 | 0.035 | 2.30x | 0.275 | 0.174 | 1.58x | 0.0040 |
0.0017 |
| BS64 x T64 | 0.209 | 0.102 | 2.06x | 0.400 | 0.264 | 1.52x | 0.0040 |
0.0017 |
| BS16 x T128 | 0.115 | 0.045 | 2.58x | 0.362 | 0.182 | 1.99x | 0.0053 |
0.0040 |
| BS16 x T256 | 0.190 | 0.069 | 2.76x | 0.380 | 0.219 | 1.73x | 0.0052 |
0.0039 |
| BS16 x T(17..255) | 0.116 | 0.036 | 3.20x | 0.362 | 0.176 | 2.05x |
0.0052 | 0.0040 |

**B200 (SM100, 148 SMs), serial lanes on one GPU — K3 shape, bounded
lb=-5, H16, wrapper** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| BS4 x T64 | 0.054 | 0.015 | 3.56x | 0.246 | 0.150 | 1.64x | 0.0053 |
0.0040 |
| BS16 x T64 | 0.086 | 0.033 | 2.64x | 0.276 | 0.166 | 1.67x | 0.0053 |
0.0040 |
| BS64 x T64 | 0.245 | 0.114 | 2.15x | 0.423 | 0.289 | 1.46x | 0.0052 |
0.0040 |
| BS16 x T128 | 0.132 | 0.048 | 2.78x | 0.373 | 0.190 | 1.97x | 0.0052 |
0.0040 |
| BS16 x T256 | 0.221 | 0.071 | 3.12x | 0.399 | 0.239 | 1.67x | 0.0052 |
0.0040 |
| BS16 x T(17..255) | 0.132 | 0.050 | 2.66x | 0.377 | 0.194 | 1.94x |
0.0052 | 0.0040 |

**B200 (SM100, 148 SMs), serial lanes on one GPU — Kimi-Linear shape,
unbounded, H12, wrapper** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| BS4 x T64 | 0.055 | 0.025 | 2.23x | 0.248 | 0.152 | 1.63x | 0.0040 |
0.0021 |
| BS16 x T64 | 0.082 | 0.044 | 1.86x | 0.275 | 0.165 | 1.67x | 0.0039 |
0.0020 |
| BS64 x T64 | 0.212 | 0.128 | 1.66x | 0.403 | 0.255 | 1.58x | 0.0039 |
0.0020 |
| BS16 x T128 | 0.117 | 0.059 | 1.97x | 0.377 | 0.182 | 2.07x | 0.0040 |
0.0021 |
| BS16 x T256 | 0.193 | 0.097 | 1.99x | 0.383 | 0.216 | 1.77x | 0.0039 |
0.0020 |
| BS16 x T(17..255) | 0.118 | 0.051 | 2.31x | 0.365 | 0.172 | 2.13x |
0.0040 | 0.0023 |

**B200 (SM100, 148 SMs), serial lanes on one GPU — Kimi-Linear shape,
unbounded, H16, wrapper** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| BS4 x T64 | 0.055 | 0.025 | 2.23x | 0.244 | 0.153 | 1.60x | 0.0040 |
0.0021 |
| BS16 x T64 | 0.089 | 0.045 | 1.99x | 0.272 | 0.169 | 1.61x | 0.0040 |
0.0020 |
| BS64 x T64 | 0.254 | 0.154 | 1.65x | 0.416 | 0.276 | 1.51x | 0.0040 |
0.0021 |
| BS16 x T128 | 0.136 | 0.061 | 2.23x | 0.372 | 0.181 | 2.05x | 0.0039 |
0.0021 |
| BS16 x T256 | 0.231 | 0.100 | 2.30x | 0.396 | 0.227 | 1.74x | 0.0040 |
0.0021 |
| BS16 x T(17..255) | 0.138 | 0.066 | 2.08x | 0.365 | 0.183 | 1.99x |
0.0039 | 0.0023 |

B200 (SM100, 148 SMs), serial lanes on one GPU: 56 rows, 56 > 1 on both
metrics; below 1: []

B200: 56/56 rows above 1 on both metrics; lowest rows: unbounded H16
layer 2x(8128+64) (GPU 1.05x / event 1.02x) and 2x8192 (GPU 1.05x /
event 1.03x).

**GB300 (SM103, 160 SMs), serial lanes on one GPU — K3 shape, bounded
lb=-5, H12, layer** (Triton / prepared ms; speedup = Triton ÷ prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 8192 | 0.562 | 0.256 | 2.19x | 0.717 | 0.510 | 1.41x | 0.0052 | 0.0041
|
| 16384 | 1.054 | 0.426 | 2.48x | 1.246 | 0.766 | 1.63x | 0.0052 |
0.0037 |
| 2x8192 | 0.773 | 0.425 | 1.82x | 0.964 | 0.758 | 1.27x | 0.0052 |
0.0039 |
| 3000+13384 | 0.957 | 0.452 | 2.12x | 1.143 | 0.781 | 1.46x | 0.0052 |
0.0039 |
| 4x4096 | 0.637 | 0.226 | 2.82x | 0.824 | 0.517 | 1.59x | 0.0052 |
0.0039 |
| 2x(8128+64) | 0.771 | 0.427 | 1.81x | 0.948 | 0.764 | 1.24x | 0.0052 |
0.0039 |
| 8x(1024+64) | 0.338 | 0.110 | 3.06x | 0.523 | 0.357 | 1.47x | 0.0040 |
0.0016 |
| 32768 | 2.082 | 0.752 | 2.77x | 2.252 | 1.201 | 1.88x | 0.0052 |
0.0034 |

**GB300 (SM103, 160 SMs), serial lanes on one GPU — K3 shape, bounded
lb=-5, H16, layer** (Triton / prepared ms; speedup = Triton ÷ prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 8192 | 0.611 | 0.314 | 1.95x | 0.767 | 0.603 | 1.27x | 0.0052 | 0.0040
|
| 16384 | 1.188 | 0.530 | 2.24x | 1.367 | 0.900 | 1.52x | 0.0052 |
0.0040 |
| 2x8192 | 0.901 | 0.437 | 2.06x | 1.079 | 0.782 | 1.38x | 0.0052 |
0.0041 |
| 3000+13384 | 1.088 | 0.543 | 2.00x | 1.273 | 0.920 | 1.38x | 0.0052 |
0.0038 |
| 4x4096 | 0.764 | 0.226 | 3.38x | 0.945 | 0.576 | 1.64x | 0.0052 |
0.0040 |
| 2x(8128+64) | 0.906 | 0.435 | 2.08x | 1.085 | 0.780 | 1.39x | 0.0052 |
0.0040 |
| 8x(1024+64) | 0.417 | 0.092 | 4.51x | 0.619 | 0.381 | 1.62x | 0.0052 |
0.0040 |
| 32768 | 2.313 | 0.961 | 2.41x | 2.488 | 1.504 | 1.65x | 0.0052 |
0.0042 |

**GB300 (SM103, 160 SMs), serial lanes on one GPU — Kimi-Linear shape,
unbounded, H12, layer** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 8192 | 0.567 | 0.351 | 1.62x | 0.721 | 0.555 | 1.30x | 0.0040 | 0.0020
|
| 16384 | 1.069 | 0.614 | 1.74x | 1.246 | 0.830 | 1.50x | 0.0040 |
0.0020 |
| 2x8192 | 0.781 | 0.612 | 1.28x | 0.961 | 0.824 | 1.17x | 0.0040 |
0.0019 |
| 3000+13384 | 0.964 | 0.656 | 1.47x | 1.143 | 0.867 | 1.32x | 0.0040 |
0.0024 |
| 4x4096 | 0.646 | 0.487 | 1.32x | 0.819 | 0.669 | 1.23x | 0.0040 |
0.0021 |
| 2x(8128+64) | 0.782 | 0.624 | 1.25x | 0.956 | 0.829 | 1.15x | 0.0040 |
0.0020 |
| 8x(1024+64) | 0.344 | 0.149 | 2.31x | 0.521 | 0.332 | 1.57x | 0.0040 |
0.0020 |
| 32768 | 2.102 | 1.109 | 1.90x | 2.273 | 1.330 | 1.71x | 0.0040 |
0.0022 |

**GB300 (SM103, 160 SMs), serial lanes on one GPU — Kimi-Linear shape,
unbounded, H16, layer** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 8192 | 0.617 | 0.443 | 1.39x | 0.767 | 0.644 | 1.19x | 0.0040 | 0.0021
|
| 16384 | 1.202 | 0.774 | 1.55x | 1.372 | 0.989 | 1.39x | 0.0040 |
0.0020 |
| 2x8192 | 0.917 | 0.825 | 1.11x | 1.077 | 1.035 | 1.04x | 0.0040 |
0.0021 |
| 3000+13384 | 1.103 | 0.790 | 1.40x | 1.269 | 1.007 | 1.26x | 0.0039 |
0.0022 |
| 4x4096 | 0.777 | 0.503 | 1.54x | 0.936 | 0.692 | 1.35x | 0.0040 |
0.0021 |
| 2x(8128+64) | 0.922 | 0.837 | 1.10x | 1.082 | 1.051 | 1.03x | 0.0040 |
0.0021 |
| 8x(1024+64) | 0.425 | 0.151 | 2.81x | 0.604 | 0.334 | 1.81x | 0.0040 |
0.0021 |
| 32768 | 2.338 | 1.420 | 1.65x | 2.511 | 1.645 | 1.53x | 0.0040 |
0.0023 |

**GB300 (SM103, 160 SMs), serial lanes on one GPU — K3 shape, bounded
lb=-5, H12, wrapper** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| BS4 x T64 | 0.050 | 0.013 | 3.81x | 0.291 | 0.223 | 1.31x | 0.0053 |
0.0040 |
| BS16 x T64 | 0.075 | 0.031 | 2.38x | 0.342 | 0.230 | 1.49x | 0.0041 |
0.0017 |
| BS64 x T64 | 0.191 | 0.093 | 2.05x | 0.462 | 0.311 | 1.49x | 0.0041 |
0.0017 |
| BS16 x T128 | 0.106 | 0.040 | 2.64x | 0.437 | 0.258 | 1.70x | 0.0053 |
0.0040 |
| BS16 x T256 | 0.171 | 0.062 | 2.74x | 0.455 | 0.275 | 1.65x | 0.0052 |
0.0040 |
| BS16 x T(17..255) | 0.107 | 0.033 | 3.29x | 0.433 | 0.253 | 1.72x |
0.0052 | 0.0041 |

**GB300 (SM103, 160 SMs), serial lanes on one GPU — K3 shape, bounded
lb=-5, H16, wrapper** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| BS4 x T64 | 0.053 | 0.013 | 3.94x | 0.300 | 0.219 | 1.37x | 0.0053 |
0.0040 |
| BS16 x T64 | 0.075 | 0.029 | 2.56x | 0.354 | 0.295 | 1.20x | 0.0053 |
0.0040 |
| BS64 x T64 | 0.233 | 0.104 | 2.24x | 0.556 | 0.371 | 1.50x | 0.0052 |
0.0040 |
| BS16 x T128 | 0.126 | 0.042 | 2.97x | 0.491 | 0.279 | 1.76x | 0.0052 |
0.0040 |
| BS16 x T256 | 0.213 | 0.064 | 3.30x | 0.487 | 0.299 | 1.63x | 0.0052 |
0.0039 |
| BS16 x T(17..255) | 0.126 | 0.044 | 2.87x | 0.443 | 0.253 | 1.75x |
0.0052 | 0.0040 |

**GB300 (SM103, 160 SMs), serial lanes on one GPU — Kimi-Linear shape,
unbounded, H12, wrapper** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| BS4 x T64 | 0.051 | 0.022 | 2.36x | 0.302 | 0.221 | 1.37x | 0.0039 |
0.0020 |
| BS16 x T64 | 0.075 | 0.039 | 1.91x | 0.372 | 0.228 | 1.63x | 0.0040 |
0.0020 |
| BS64 x T64 | 0.193 | 0.114 | 1.68x | 0.484 | 0.310 | 1.56x | 0.0039 |
0.0020 |
| BS16 x T128 | 0.108 | 0.053 | 2.02x | 0.482 | 0.244 | 1.98x | 0.0040 |
0.0021 |
| BS16 x T256 | 0.177 | 0.087 | 2.04x | 0.481 | 0.277 | 1.74x | 0.0039 |
0.0020 |
| BS16 x T(17..255) | 0.110 | 0.046 | 2.39x | 0.472 | 0.232 | 2.04x |
0.0040 | 0.0023 |

**GB300 (SM103, 160 SMs), serial lanes on one GPU — Kimi-Linear shape,
unbounded, H16, wrapper** (Triton / prepared ms; speedup = Triton ÷
prepared)

| case | GPU Triton | GPU prepared | GPU x | event Triton | event
prepared | event x | out relL2 | state relL2 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| BS4 x T64 | 0.053 | 0.022 | 2.46x | 0.294 | 0.237 | 1.24x | 0.0040 |
0.0021 |
| BS16 x T64 | 0.076 | 0.040 | 1.90x | 0.353 | 0.230 | 1.53x | 0.0040 |
0.0020 |
| BS64 x T64 | 0.232 | 0.139 | 1.67x | 0.476 | 0.333 | 1.43x | 0.0039 |
0.0021 |
| BS16 x T128 | 0.125 | 0.054 | 2.31x | 0.450 | 0.243 | 1.85x | 0.0040 |
0.0020 |
| BS16 x T256 | 0.211 | 0.089 | 2.36x | 0.469 | 0.272 | 1.72x | 0.0040 |
0.0021 |
| BS16 x T(17..255) | 0.127 | 0.059 | 2.16x | 0.443 | 0.243 | 1.82x |
0.0040 | 0.0022 |

GB300 (SM103, 160 SMs), serial lanes on one GPU: 56 rows, 56 > 1 on both
metrics; below 1: []

GB300: 56/56 rows above 1 on both metrics; lowest rows: unbounded H16
layer 2x(8128+64) (GPU 1.10x / event 1.03x) and 2x8192 (GPU 1.11x /
event 1.04x).

### Window floor
Windows are planned with at least 8 chunks (256 tokens); every planned
launch maps onto an exported program (the 359-row export confirms no
variant is missing for this class). On the 4-head 8192-token
single-sequence benchmark in the source harness this restores the 32 ×
8-chunk plan: GB300 0.1708 ms vs 0.1724 ms on the merge-base (the first
round of this PR had 0.2229 ms with 16-chunk windows); B200 0.1847 ms vs
0.2399 ms in the first round.

### Validation

Source-vs-export validation of the regenerated programs (all 359
inventory rows per arch (350 of the first round plus nine
256-token-window rows), fixed inputs, bitwise compare of output / final
state / checkpoint rows against the source implementation, plus the
paired latency ratio):

| arch | rows measured | errors | bitwise | export/source latency
(median / max) | unbounded rows bitwise |
|---|---:|---:|---:|---|---|
| SM100 (B200) | 359 | 0 | 359 | 0.999 / 1.038 | 14/14 (incl. the 4
dense-beta rows) |
| SM103 (GB300) | 359 | 0 | 359 | 0.999 / 1.028 | 14/14 (incl. the 4
dense-beta rows) |

`tests/kda/test_kda_prefill_plan_cache.py`,
`test_bf16_one_wave_route.py`, `test_tf32_prefill.py` on the merged
trees: SM100 69 passed (the new dense-beta test 4/4; it failed 4/4
against the previous export), SM103 69 passed; on the previous head
1fd37d513 (both exports): SM100 70 passed, SM103 70 passed; on the final
measured revision 8c660e487: SM100 70 passed, SM103 70 passed (the head
f6199624b adds only the pre-commit clang-format of
`csrc/kda/cake_kda_affine_epilogue.cu`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a1f4948](https://github.com/flashinfer-ai/flashinfer/commit/a1f4948aa0494f9ccae35b141a46d159183d8141)

- **作者**: eigen
- **时间**: 2026-09-25T23:17:08Z
- **提交信息**: feat(cake_diffusion): add MiniMax-H3 direct-layout out-proj + gated residual for SM100 and SM103 (#5525)

## Summary

Fused MiniMax-H3 attention-output operator for SM100 (B200/GB200) and
SM103 (B300/GB300) — #4532 candidate 4 (tracker #4254): read the
inverse-Ulysses receive layout directly, output projection GEMM 7168 →
5376, indexed gate × projection + residual, BF16 `[M, 5376]` out. Three
operators in `flashinfer.diffusion_ops`:

| operator | activation / weight | scales | launches |
|---|---|---|---|
| `minimax_h3_out_proj` | BF16 / BF16 | – |
`kernel_minimax_h3_out_proj_bf16` |
| `minimax_h3_out_proj_mxfp8` | E4M3 / E4M3 | UE8M0 per 32 (128x4
swizzle) | `kernel_minimax_h3_quant_mxfp8` →
`kernel_minimax_h3_out_proj_e4m3` |
| `minimax_h3_out_proj_nvfp4` | E2M1 / E2M1 | UE4M3 per 16 + static
global scale (128x4 swizzle) | `kernel_minimax_h3_quant_nvfp4` →
`kernel_minimax_h3_out_proj_e2m1` |

Computation per call (batch 1, Ulysses degree `P ∈ {1, 2, 4, 8}`, `M`
packed rows on this rank, 56 heads × 128, hidden 5376, 9-row gate
table):

`attn_out [P, M, 56/P, 128]` (destination `p` holds heads `[p·56/P,
(p+1)·56/P)`) → `o = BF16(A @ o_weightᵀ)` → `p =
BF16(gate[gate_index[m]] · o)` (index outside `[0, 9)` → gate 0) → `out
= BF16(residual + p)`.

* No standalone unpack / transpose: the GEMM's activation tensor map
spans the `[P·M, 7168/P]` view of the receive layout and the load warp
fetches K block `kb` of row `m` at `((kb // (112/P)) · M + m, kb %
(112/P))`; the quantization kernels read the same layout one warp per
row. `P` and `M` are runtime parameters, one cubin per architecture.
* GEMMs: persistent `cta_group::2` tcgen05 kernels (256×256 tile per CTA
pair, cluster-launch-control in-order scheduler, double-buffered TMEM
accumulators for BF16; `kind::mxf8f6f4` / `kind::mxf4nvf4` block-scaled
MMA with scale factors staged through TMEM for the quantized variants),
fused gate/residual epilogue with 128-bit gate / residual loads and
256-bit stores.
* Quantization kernels are bit-exact with `mxfp8_quantize` /
`nvfp4_quantize` (7 independent 16-byte loads per lane in flight); the
block-scaled GEMMs are launched with programmatic dependent launch
(`griddepcontrol.wait` before the first activation / scale load) so
their prologue overlaps the quantization pass.
* `prepare_minimax_h3_o_weight_mxfp8` /
`prepare_minimax_h3_o_weight_nvfp4` quantize the weight offline
(FlashInfer quantizers) and build the 256-row scale tiles the paired MMA
expects; `minimax_h3_unpack_attn_out` and
`minimax_h3_out_proj_reference` give the unfused reference;
workspace-size helpers for caller-owned quantized-activation buffers.

## Performance

Complete operator (all launches), CUPTI kernel time, cold L2, medians,
against the fastest complete chain measured in the same run
(`torch_chain` = unpack + cuBLAS + torch epilogue;
`segmented_flashinfer_{bf16,mxfp8,nvfp4}` = unpack + FlashInfer quantize
+ `mm_bf16` / `mm_mxfp8` / `mm_fp4` + torch epilogue; the unpack is
timed in every chain because the receive layout is what the operator
receives). 47 shapes per variant: 24 production centers `T ∈ {33472,
38592, 48768, 58944, 74240, 109952} × P ∈ {1, 2, 4, 8}` (`M = T/P`), 16
aligned / ±1-row tails, 7 small-M correctness-only rows.

| GPU | variant | rows correct | timed shapes faster | speedup vs
fastest chain (min / geomean / max) | TFLOP/s (min–max) | vs bare
library GEMM only (pre-unpacked, pre-quantized activation) |
|---|---|---:|---:|---|---|---|
| B200 | BF16 | 47/47 | 40/40 | 1.185 / 1.515 / 1.815 | 1414–1639 |
0.88–1.02 (`cublas_gemm_only`) |
| B200 | MXFP8 | 47/47 | 40/40 | 1.475 / 1.967 / 2.275 | 2330–2645 |
0.90–1.09 (`flashinfer_mm_mxfp8_only`) |
| B200 | NVFP4 | 47/47 | 40/40 | 1.937 / 2.856 / 4.091 | 3566–4662 |
0.76–1.02 (`flashinfer_mm_fp4_only`) |
| B300 | BF16 | 47/47 | 40/40 | 1.073 / 1.495 / 1.831 | 1384–1699 |
0.88–1.02 (`cublas_gemm_only`) |
| B300 | MXFP8 | 47/47 | 40/40 | 1.421 / 1.972 / 2.277 | 2314–2757 |
0.90–1.07 (`flashinfer_mm_mxfp8_only`) |
| B300 | NVFP4 | 47/47 | 40/40 | 1.965 / 2.802 / 3.604 | 3564–4999 |
0.81–1.02 (`flashinfer_mm_fp4_only`) |

The bare-GEMM column is a diagnostic floor, not a complete operator: the
fused kernels include the layout handling, the quantization pass and the
gated-residual epilogue. The lowest NVFP4 ratios are P = 8 / M ≈ 4k,
where the quantization pass is ~20 % of the operator. The longest BF16
rows (P = 1, M ≥ 58944) run at sustained-power clocks on both GPUs
(cuBLAS drops the same way).

Single-shape numbers (P = 8, M = 4824, complete operator): B200 BF16
1563 / MXFP8 2344 / NVFP4 3691 TFLOP/s; B300 1600 / 2324 / 3730.

## Validation

* Output vs the unfused reference on the same operands: zero violations
of `|Δ| ≤ 1e-2 + 1e-2·mag + 2·bf16_ulp(mag)`, `mag = max(|out|, |p|)`
(one accumulation-order ulp of `o` moves `gate·o` by at most two BF16
steps), rows with an invalid gate index equal `residual` bit-exactly,
FP32-oracle fairness (the fused kernel's mean error ≤ 1.02x the unfused
chain's).
* Quantized activations bit-exact with `mxfp8_quantize` /
`nvfp4_quantize` (NVFP4: exact rounding ties excluded).
* `compute-sanitizer` synccheck + memcheck clean for all five kernels on
B200 and B300.
* `tests/diffusion_ops/test_minimax_h3_out_proj.py` (52 cases: P ∈ {1,
2, 4, 8} × M ∈ {1, 129, 257, 4824} × 3 variants, invalid-index probe,
argument validation, CPU layout self-tests); JIT smoke of the exported
operators PASS on B200 and B300.

## Limits

* **Architectures**: CC 10.0 and 10.3 only (tcgen05 MMA + TMEM + cluster
launch control); one source per arch
(`csrc/cake_minimax_h3_out_proj_sm100a.cu`, `_sm103a.cu`); other devices
raise at module build.
* **Topology**: GEMMs launch 2-CTA clusters, 320 threads (TMA warp, MMA
warp, 8 epilogue warps), persistent grid of one cluster per SM pair;
dynamic shared memory 230,528 B (BF16, 7 stages), 206,976 B (MXFP8, 3 ×
256-deep stages), 195,712 B (NVFP4, 5 stages). Quantization kernels: 128
threads, 4 rows per CTA, no shared memory.
* **Shapes**: hidden 5376, 56 × 128 heads, 9 gate rows are compile-time
constants; `P ∈ {1, 2, 4, 8}`, any `M ≥ 1` (row tails through TMA OOB
fill + predicated stores); `gate_index` int32; all tensors contiguous on
one device; `residual` / `out` 32-byte aligned.
* **Workspaces** (caller-owned or allocated by the wrapper): MXFP8 `[M,
7168]` E4M3 + `mxfp8_activation_scale_workspace_bytes(M)`; NVFP4 `[M,
3584]` uint8 + `nvfp4_activation_scale_workspace_bytes(M)`. The NVFP4
activation global scale is a calibrated input (`448 · 6 / absmax`
convention); `alpha = 1 / (g_a · g_w)`.
* Sol Engine / SGLang integration is left to the requester.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added MiniMax-H3 attention output projection for sequence-parallel
layouts, with BF16, MXFP8, and NVFP4 variants.
* Added utilities to prepare weights for MXFP8 and NVFP4, plus a
reference implementation for result comparisons.
  * Invalid gate indices now produce the residual as output.
* Optimized variants are available on supported Blackwell GPUs (SM100a
and SM103a).
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c894711](https://github.com/flashinfer-ai/flashinfer/commit/c89471142b6782353db12365e15c4ceb4a6f66b7)

- **作者**: eigen
- **时间**: 2026-09-25T21:58:24Z
- **提交信息**: perf(cake_backend): drop the redundant device fence before the grid join in the Kimi-K3 fused router (SM100/SM103) (#5548)

## Kimi-K3 fused MoE router: drop the redundant device fence before the
cooperative grid join (SM100 / SM103)

Follow-up to #5531 (same source family, one kernel-side change). Same K3
semantics (sigmoid gate, top-16 on `sigmoid(logit) + bias`, renormalized
unbiased weights, lower expert id on ties) and the same expert-aligned
route plan for `block_m` 8/16; the public entries
`flashinfer.fused_moe.kimi_k3_fused_router` /
`prepare_kimi_k3_fused_router` and the dispatch table are unchanged.

### What changed
The M arm (M256) and the Q4S arm (M512, M1024, M2048) publish each row's
sixteen expert ids and then join the grid with
`cooperative_groups::this_grid().sync()`. That join already performs
`bar.sync`, a gpu-scope release arrive and an acquire wait, so the
per-thread `__threadfence()` that preceded it only lengthened the join
phase. The regenerated M and Q4S programs differ from #5531 by exactly
that one removed `__threadfence();` line (8 programs per arch); the L,
LC and G programs are byte-identical modulo their embedded identity
hash, which is derived from the generating source build and therefore
changes on every re-export (all 28 programs per arch are re-emitted
under new names, `cake_jit.py` MODULES updated in place). The
regenerated bindings also drop a `CheckCurrentCudaDevice(logits)` call
that followed the scoped device guard (`ScopedCudaDevice
device_guard(dev.device_id)`) and therefore could not fail; the guard,
the tensor checks and `CheckSameCudaDevice` for every other tensor are
unchanged.

Per-phase attribution on B200 (paired cold-L2 CUPTI, us): Q4S M1024 join
phase 1.79 → 1.38, full 17.09 → 16.86; Q4S M2048 join 1.98 → 1.44, full
24.16 → 23.58; M arm M256 join 1.66 → 1.25, full 9.54 → 9.06. Selection
and every downstream phase are unchanged within noise.

### Exactness
Source-side gates on both arches: exact43 43/43, affected slice +
registered e2e, compute-sanitizer synccheck and racecheck (separate
runs) all green. Export receipts (source ↔ export bitwise parity on all
28 shapes per arch, generated grid == source grid): B200 (sm_100a) 28/28
rows correct, source/export time ratio 0.967–1.029; GB300 (sm_103a)
28/28 rows correct, ratio 0.960–1.009.
`tests/experimental/test_cake_kimi_k3_fused_router.py`: B200 44 passed,
GB300 44 passed.

### Benchmark
`benchmarks/bench_cake_kimi_k3_fused_router.py --cupti --rounds 5`
(interleaved A/B rounds, CUPTI kernel time with a cold L2) against
SGLang `route_radix` + `moe_align_block_size` (pinned SGLang revision
83bd2c47, kernel-only):

| row | arm (B200 / GB300) | B200 fused us | B200 SGLang us | B200
speedup | GB300 fused us | GB300 SGLang us | GB300 speedup |
|---|---|---:|---:|---:|---:|---:|---:|
| m1_bm8 | L / L | 5.76 | 9.63 | **1.672** | 5.86 | 13.25 | **2.262** |
| m2_bm8 | LC / LC | 5.34 | 9.86 | **1.844** | 5.44 | 13.02 | **2.395**
|
| m4_bm8 | LC / LC | 5.82 | 9.79 | **1.681** | 5.66 | 13.18 | **2.328**
|
| m8_bm8 | LC / LC | 5.86 | 9.98 | **1.705** | 5.79 | 12.64 | **2.182**
|
| m16_bm8 | L / L | 6.11 | 9.79 | **1.602** | 6.11 | 13.28 | **2.173** |
| m32_bm8 | L / L | 6.27 | 9.89 | **1.577** | 6.14 | 13.22 | **2.151** |
| m64_bm8 | L / L | 6.98 | 10.01 | **1.436** | 6.82 | 13.50 | **1.981**
|
| m128_bm8 | L / L | 8.06 | 10.56 | **1.310** | 7.65 | 13.63 | **1.782**
|
| m256_bm8 | M / M | 8.51 | 10.91 | **1.282** | 8.13 | 14.40 | **1.772**
|
| m512_bm8 | Q4S / Q4S | 10.53 | 13.15 | **1.249** | 10.21 | 16.03 |
**1.571** |
| m1024_bm8 | Q4S / Q4S | 14.34 | 18.34 | **1.279** | 13.73 | 19.04 |
**1.387** |
| m2048_bm8 | Q4S / Q4S | 21.02 | 28.48 | **1.355** | 20.00 | 27.20 |
**1.360** |
| m4096_bm8 | G / G | 37.57 | 47.90 | **1.275** | 33.22 | 45.98 |
**1.384** |
| m8192_bm8 | G / G | 62.02 | 88.00 | **1.419** | 53.92 | 83.49 |
**1.548** |
| m1_bm16 | L / L | 6.43 | 9.82 | **1.527** | 5.95 | 13.12 | **2.204** |
| m2_bm16 | LC / LC | 5.89 | 9.63 | **1.636** | 5.73 | 13.18 | **2.302**
|
| m4_bm16 | LC / LC | 5.54 | 9.82 | **1.775** | 5.57 | 13.44 | **2.414**
|
| m8_bm16 | LC / LC | 5.66 | 10.02 | **1.769** | 5.82 | 13.44 |
**2.308** |
| m16_bm16 | L / L | 6.18 | 10.05 | **1.627** | 5.95 | 13.41 | **2.253**
|
| m32_bm16 | L / L | 6.40 | 9.86 | **1.540** | 6.14 | 13.73 | **2.234**
|
| m64_bm16 | L / L | 7.10 | 9.98 | **1.405** | 6.85 | 13.44 | **1.963**
|
| m128_bm16 | L / L | 8.22 | 10.43 | **1.268** | 7.84 | 13.98 |
**1.784** |
| m256_bm16 | M / M | 8.32 | 11.14 | **1.338** | 8.32 | 14.53 |
**1.746** |
| m512_bm16 | Q4S / Q4S | 10.46 | 12.74 | **1.217** | 10.08 | 16.13 |
**1.600** |
| m1024_bm16 | Q4S / Q4S | 13.98 | 17.92 | **1.281** | 13.66 | 19.23 |
**1.408** |
| m2048_bm16 | Q4S / Q4S | 20.90 | 27.01 | **1.292** | 19.97 | 26.27 |
**1.316** |
| m4096_bm16 | G / G | 37.57 | 45.50 | **1.211** | 34.24 | 44.06 |
**1.287** |
| m8192_bm16 | G / G | 63.81 | 82.43 | **1.292** | 53.76 | 79.20 |
**1.473** |

Geomean speedup vs SGLang: **NVIDIA B200 1.447** (min 1.211, 28/28 rows
> 1.0), **NVIDIA GB300 1.837** (min 1.287, 28/28 rows > 1.0). Relative
to the #5531 programs on the same nodes (paired cold-L2 CUPTI, source
kernels): M256 +3 %, M512 +5–7 %, M1024 +5 %, M2048 +3–4 % on both
arches; other rows unchanged (same-session interleaved control on the 20
unchanged L/LC/G rows: geomean 0.998 on B200 and 1.001 on GB300, per-row
spread ±3–7 % in both directions on the 5–8 µs rows).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Kimi K3 fused-router calls can now run when the active CUDA device
differs from the logits tensor’s device. Calls continue to use the
tensor’s device, with other tensors still required to match.
* Updated fused-router kernels across supported configurations to
improve compatibility and reliability.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [40e642c](https://github.com/flashinfer-ai/flashinfer/commit/40e642c4f1d6dfb61100be58ad98964bf64cbb23)

- **作者**: eigen
- **时间**: 2026-09-25T21:01:30Z
- **提交信息**: perf(cake_mla): split the FP8 page-64 producer o_done handshake per V stage (SM100 + SM103) (#5547)

## Summary

Follow-up to #4557 (Blackwell TRT-LLM MLA decode backend, opt-in
`backend="cake"`): regenerates the
`csrc/cake_trtllm_mla_blackwell/generated/` package for both targets
(`sm_100a_148` B200, `sm_103a_152` GB300) from Cake `main` with one
producer-side scheduling change in the FP8 page-64 domain
(`mla_fp8_page64_pdl`, public row `benchmark-main-008172`):

- the end-of-kernel `o_done` mbarrier now carries one stage per local V
slice: the MMA warp commits stage 0 right after the vs=0 drain MMA and
stage 1 after the vs=1 drain MMA, so the correction warps
unload/scale/store the vs=0 O slice while the vs=1 PV MMA is still
running; the softmax warps wait for stage 1; the correction warps
publish their final row sum before waiting.
- Producer-only: the two-kernel split-major ABI, partial-O layout,
reducer, dispatcher and tolerances are unchanged.
`flashinfer/mla/cake_trtllm_mla_blackwell.py` is untouched.

All 54 generated sources change because the package is regenerated from
Cake `main` (see the codegen-divergence note in the Cake design doc
`design_doc/active/CAKE_647_TRTLLM_MLA_SOURCE_LANDING.md`); the device
idents (content hashes) therefore change as well. Every source is
byte-identical to the single-target projections that were gated on the
physical GPUs (27/27 per target).

## Qualification (same-session live TRT-LLM Gen reference, cold-L2
paired CUPTI)

Both targets: FULL32 32/32 (PyTorch reference), PR unit tests 18/18 (`-k
"trtllm_mla_blackwell or catalog or get_domain_module or source_dir"`),
20-row paired gate 60/60 live floors, isolated single-row screens
(008172, 007706, 008308), 5-row CLC screen 30/30, FORMAL 12/12, generic
CLC component 24/24 + compute-sanitizer synccheck/racecheck PASS.

| target | 20-row GM (this PR) | 20-row GM (#4557 package) | row 008172
(FP8 page-64) this PR | row 008172 #4557 |
|---|---|---|---|---|
| B200 `sm_100a_148` | 1.1923× (60/60) | 1.1933× | **1.0634×** (18.673
µs vs 19.872 µs live) | 1.042× |
| GB300 `sm_103a_152` | 1.2282× (60/60) | 1.2204× | **1.1105×** (17.056
µs vs 18.944 µs live) | 1.0085× |

Step-0 baseline (Cake `main` regenerated, no lever) measured in the same
session: B200 GM 1.1910× / 008172 1.0527×; GB300 GM 1.2263× / 008172
1.1019×.

Full gate tables, host/path/size/SHA-256 evidence manifest and the
harness notes are in the internal design doc
`design_doc/active/CAKE_647_FP8_PAGE64_ODONE_SPLIT.md`. Tracker: #4254.

## Test plan

- `pytest tests/attention/test_trtllm_gen_mla.py -k
"trtllm_mla_blackwell or catalog or get_domain_module or source_dir"` on
B200 and GB300 (18 passed each, against this package).
- FULL32 correctness on both targets (32/32).
- `test_trtllm_mla_blackwell_bf16_dispatch` now skips on GPUs whose
exact (arch, SM count) target is not in the shipped catalog. GB200
reports SM100a with 152 SMs, which the package does not ship (only
`sm_100a_148` and `sm_103a_152`); the GB200 CI legs turned the
dispatcher's refusal into 6 failures per CUDA version, exactly as on
#4557's own CI. No kernel or module change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* The Blackwell BF16 dispatch test now skips when the GPU target cannot
be resolved or isn’t available in the generated-source catalog.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [bf82326](https://github.com/flashinfer-ai/flashinfer/commit/bf82326b0c524048c7f810da9f0022f8316ac3ff)

- **作者**: eigen
- **时间**: 2026-09-25T07:10:44Z
- **提交信息**: feat(cake_mla): add generated Blackwell TRT-LLM MLA decode backend for SM100 and SM103 (#4557)

Add an explicit Blackwell TRT-LLM MLA backend with generated GB300
(sm_103a, 152 SMs) and B200 (sm_100a, 148 SMs) source packages.

The backend combines a 15-stage unified pipeline with Split-KV reduction
while preserving paged-KV semantics, BF16/FP8 scale handling and the
launch ABI. The integration supplies generated sources for the physical
target (sm_103a, 152 SMs), validates an explicit target catalog, passes
the required Split-KV workspace arguments, and keeps host metadata bound
to tensor identity so address reuse cannot return stale lengths. The
native split8 reducer keeps 32 statistics slots because host dispatch
never requests more than 16 splits. The persistent CLC decode route now
processes work items longest-first: the runtime appends a permutation of
the work ids after the page table and the CLC kernels map each raw work
id through it when the work set is deeper than one resident wave but at
most 1024 items; deeper sets and single-wave sets keep the previous
behaviour.

Validation on NVIDIA GB300, same process, against the live TRT-LLM Gen
kernels shipped by FlashInfer, cold-L2 paired CUPTI timing:

- Correctness: all 32 public API rows at unchanged tolerances (BF16
`atol=rtol=1e-2`, FP8 e4m3 `atol=rtol=0.1`), plus 24 metadata-lifetime
sequences and 24 warm-cache identity checks; 81 numerical checks in the
paired run, zero failures.
- Performance: all 60 floors across 20 rows, three paired blocks, 120
timing arms and 3,600 spans. Geometric mean of row-median speedups
1.220390×; weakest block 1.005947×.

| Row (query rows, route) | Candidate µs | Live Gen µs | Median speedup
|
|---|---:|---:|---:|
| q=1, CLC | 22.336 | 24.000 | 1.075931× |
| q=2 KV8192, CLC | 138.832 | 177.104 | 1.275671× |
| q=4, CLC | 36.528 | 47.552 | 1.298384× |
| q=8, CLC | 60.224 | 73.824 | 1.224847× |
| q=16, CLC | 17.760 | 19.632 | 1.105405× |
| B512 q=1 KV4096, CLC | 231.392 | 266.400 | 1.150259× |
| B512 q=2 KV4096, CLC | 377.136 | 432.096 | 1.145195× |
| B1024 q=4, CLC | 482.112 | 501.776 | 1.040787× |
| B512 q=16, CLC | 907.776 | 937.472 | 1.032950× |
| B1 KV1024 page64 sink, native split8 PDL | 11.904 | 12.416 | 1.044236×
|
| B1 KV1024 page64, native split8 PDL | 11.920 | 16.015 | 1.343164× |
| unsplit BF16 | 118.688 | 128.352 | 1.080841× |
| FP8 page64 PDL | 18.832 | 18.992 | 1.008489× |

A separate generic CLC component check passed 24/24 floors vs the
current build and 24/24 vs live on 007738/007779/007781/007782 (72 arms,
360 cold-L2 spans): 007738 1.048185× current / 1.087470× live, 007779
1.032560× / 1.085260×, 007781 1.322903× / 1.307959×, 007782 1.255043× /
1.229858×. A formal targeted-row check passed 12/12 floors on four
targeted rows (candidate aggregate 1.790903 ms vs 1.922619 / 1.912506 ms
for the two reference builds and 1.914265 ms live: 1.073547× / 1.067900×
/ 1.068883×, weakest block 1.059863×). Separate synchronization and race
sanitizer runs reached their 20-second limits and remain skipped. The
measured scope is GB300 only; other physical targets are not included in
this package.

CLC device SASS: four decode sites gain one predicated page-table load
each; registers (168), shared memory and local memory (none) are
unchanged. The four shape-specialised CLC variants with constant work
sets above 1024 items are instruction-identical to the previous build;
all other device images are byte-identical to the previously measured
build.


## SM100 (B200, 148 SMs) package — added 2026-09-24

This update adds a second generated source package for the physical
target `sm_100a_148` from the same producer lineage as the GB300
package, and makes the catalog and dispatch per-target
(`cake_source_catalog.json` schema 4: one host source and one
device-identity set per target; the sm_103a_152 host and device sources
are byte-identical to the previous head, only moved under
`host/sm_103a_152/cake_<domain>.cpp`). The SM100 package uses the
ld.red-free score reduction (`tcgen05.ld.red` is sm_103a-only), the
148-SM persistent CLC geometry, and an FP8 page-64 producer whose
partial-O epilogue is unloaded by all eight softmax/correction warps and
written back through a warp-private SMEM stage as full-sector coalesced
stores (the previous 16-byte per-lane stores to 1 KiB-strided head rows
were bound by the L1→L2 request path). The GB300 package and the host
runtime are unchanged.

Validation on NVIDIA B200 (same process, against the live TRT-LLM Gen
kernels shipped by FlashInfer, cold-L2 paired CUPTI timing):

- Correctness: all 32 public API rows at unchanged tolerances (BF16
`atol=rtol=1e-2`, FP8 e4m3 `atol=rtol=0.1`); 81 numerical checks in the
paired run, zero failures; PR unit tests 18 passed.
- Performance (publication run): all 60 floors across 20 rows, three
paired blocks, 120 timing arms; geometric mean of row-median speedups
1.193288×, weakest block 1.018258× (row 007783); FP8 page-64 batch 16 ×
4096 tokens (row 008172) 1.042276× (18.912 vs 19.696 µs).

| Row (public label, source route) | Candidate µs | Live Gen µs | Median
speedup |
|---|---:|---:|---:|
| 000020 (r143_fp8_p32_q2_kv1024_qk_l2_resident_v1) | 10.095 | 10.336 |
1.023822× |
| 007706 (v32_15stage_page_native_sink_pdl_runtime) | 12.512 | 17.088 |
1.365674× |
| 007707 (r6_bf16_q128_runtime_vquarter_underfill_) | 14.960 | 19.312 |
1.287780× |
| 007735 (r6_bf16_q128_runtime_vquarter_underfill_) | 14.816 | 20.544 |
1.385495× |
| 007736 (r6_bf16_q128_runtime_vquarter_underfill_) | 15.680 | 24.032 |
1.532621× |
| 007737 (r5_bf16_q128_runtime_vhalf_underfill_sin) | 17.455 | 19.968 |
1.143937× |
| 007738 (r171_bf16_clc_packed_affine_full_tile_ma) | 19.888 | 21.583 |
1.085461× |
| 007779 (r171_bf16_clc_packed_affine_full_tile_ma) | 23.280 | 25.440 |
1.090700× |
| 007781 (r171_bf16_clc_packed_affine_full_tile_ma) | 39.520 | 54.911 |
1.389466× |
| 007782 (r171_bf16_clc_packed_affine_full_tile_ma) | 66.351 | 83.391 |
1.256629× |
| 007783 (r165_bf16_b64_q16_kv1024_unsplit_v1) | 141.086 | 144.910 |
1.027570× |
| 007790 (r171_bf16_clc_packed_affine_full_tile_ma) | 148.925 | 196.862
| 1.322585× |
| 007826 (r171_bf16_clc_packed_affine_full_tile_ma) | 1094.801 |
1146.304 | 1.051175× |
| 007827 (r171_bf16_clc_packed_affine_full_tile_ma) | 244.685 | 286.077
| 1.169162× |
| 007828 (r171_bf16_clc_packed_affine_full_tile_ma) | 423.067 | 487.257
| 1.151120× |
| 007838 (r171_bf16_clc_packed_affine_full_tile_ma) | 834.549 | 885.876
| 1.090419× |
| 007850 (r171_bf16_clc_packed_affine_full_tile_ma) | 575.816 | 600.360
| 1.042625× |
| 008172 (r143_fp8_page64_native_pdl_sequence_unif) | 18.912 | 19.696 |
1.042276× |
| 008308 (v32_15stage_page_native_sink_pdl_runtime) | 12.832 | 13.168 |
1.026146× |
| 4c7ffd75e3ce4530 (r6_bf16_q128_runtime_vquarter_underfill_) | 14.928 |
24.192 | 1.621265× |

Generic CLC component check: 24/24 live floors on
007738/007779/007781/007782 (48 arms, 240 cold-L2 spans): 007738
1.068364×, 007779 1.089936×, 007781 1.376449×, 007782 1.256431×;
synccheck and racecheck passed. Formal targeted-row check: 12/12 floors
on 007826/007850/007790/007827 (geomean 1.131191×, weakest block
1.040618×).


## File naming — `cake_` prefix (2026-09-24)

All Cake-owned files added by this PR now carry the mandatory `cake_`
basename prefix used by every other Cake integration in FlashInfer; the
change is a pure rename (git `R` entries) plus path/import updates —
**device and host source bytes are unchanged**, so the qualified kernels
and the byte-identical `sm_103a_152` package are untouched.

| before | after |
|---|---|
| `csrc/mla/trtllm_mla_blackwell/generated/source_catalog.json` |
`csrc/cake_trtllm_mla_blackwell/generated/cake_source_catalog.json` |
| `csrc/mla/trtllm_mla_blackwell/generated/host/<target>/<domain>.cpp` |
`csrc/cake_trtllm_mla_blackwell/generated/host/<target>/cake_<domain>.cpp`
|
| `csrc/mla/trtllm_mla_blackwell/generated/device/<target>/<ident>.cu` |
`csrc/cake_trtllm_mla_blackwell/generated/device/<target>/cake_<ident>.cu`
|
| `flashinfer/jit/trtllm_mla_blackwell.py` | removed — the source-built
domain loader now lives in `flashinfer/mla/cake_trtllm_mla_blackwell.py`
(no separate JIT module) |
| `flashinfer/mla/trtllm_mla_blackwell.py` |
`flashinfer/mla/cake_trtllm_mla_blackwell.py` (semantic dispatcher +
domain loader) |

The catalog records the new relative paths with unchanged per-file
SHA-256 values; the loader validates `host/<target>/cake_<domain>.cpp`
and `device/<target>/cake_<ident>.cu` exactly. The Cake path is opt-in
only and, like every other Cake integration in FlashInfer, is selected
with `backend="cake"` (renamed from the earlier
`"trtllm-mla-blackwell"`); `backend="auto"` never selects it. The
dispatch itself (`trtllm_batch_decode_with_kv_cache_mla` →
`trtllm_mla_blackwell_decode`) is unchanged. Unit tests re-run on NVIDIA
B200 against the renamed package: 18 passed, 0 failed
(`tests/attention/test_trtllm_gen_mla.py -k "trtllm_mla_blackwell or
catalog or get_domain_module or source_dir"`, NVIDIA B200, same count as
the original package run).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a Blackwell backend for MLA batch decoding, with support for
BF16 and FP8 decoding and optional log-sum-exp output.
* The backend supports NVIDIA SM100a and SM103a GPUs with CUDA 12.9 or
later.
* **Bug Fixes**
* Improved decode output accuracy across supported batch and
query-length combinations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4501
- **最后更新**: 2026-09-25T23:07:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34600
- **最后更新**: 2026-09-25T15:56:08Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hidemitsu Ikeda

## AI分析总结

**1. 主要更新类型**
本次提交为**Bug修复**，并附带了相关的测试补充。

**2. 关键变更点及其与项目整体方向的关系**
- **关键变更**：修复了在使用TaylorSeer缓存优化时，当不同步骤间输入特征形状（如分辨率）发生变化导致程序崩溃的错误，并增加了针对此场景（涉及QwenImage模型与KV-cache预填充）的测试用例。
- **与项目方向的关系**：`diffusers`作为主流的扩散模型工具库，其核心目标之一是提供高效、稳定的推理与训练优化方案（如缓存技术）。此修复直接保障了高级优化功能（TaylorSeer）在处理动态或变化输入时的可靠性，符合项目对**稳定性**和**生产环境可用性**的追求。

**3. 对项目的影响和潜在意义**
- **直接影响**：显著提升了`TaylorSeer`缓存功能的健壮性，使其能安全应用于特征形状动态变化的场景（例如不同分辨率的图像生成），避免了运行时崩溃。
- **潜在意义**：增强了开发者在复杂管线中使用高级优化技术的信心，有助于推动这类高效缓存技术在更广泛任务中的采纳。

**4. 值得关注的技术点**
- **动态缓存管理**：修复核心在于处理“KV-cache预填充”阶段的形状变化问题，这涉及到在自回归或序列生成模型中，缓存机制如何适应非固定的特征维度，是一个具有挑战性的工程优化点。
- **特定模型支持**：提交明确提及了与`QwenImage`模型的测试，表明修复针对并支持特定架构，体现了库对多元化模型生态的适配工作。

**5. 基于README背景的项目发展影响**
`diffusers`项目致力于提供前沿、易用且稳定的扩散模型生态。本次提交虽然看似是一个具体的Bug修复，但其本质是**强化了库的底层基础设施的可靠性**。在复杂多变的AI应用场景中，这种稳定性是确保项目能作为可靠基石、持续被社区和企业采用的关键。它直接提升了用户在使用高级功能时的体验，减少了因工具链问题导致的调试负担，从而间接推动了基于该项目的创新与部署。

## 详细提交记录

### [bdc2bea](https://github.com/huggingface/diffusers/commit/bdc2bea37a36038c44452811610489ea30ede229)

- **作者**: Hidemitsu Ikeda
- **时间**: 2026-09-25T07:04:07Z
- **提交信息**: Fix TaylorSeer cache crash when the feature shape changes between steps (#14831)

* Fix TaylorSeer cache crash when the feature shape changes between steps

* Add QwenImage 2.1 x TaylorSeer tests covering the KV-cache prefill shape change

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
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


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13182
- **最后更新**: 2026-09-25T19:03:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36433
- **最后更新**: 2026-09-26T00:14:47Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 18
- **主要提交者**: Yuwei An, metamergebot, Kevin Mi

## AI分析总结

好的，我将以专业的代码分析助手身份，结合项目背景对昨日提交记录进行总结分析。

**1. 主要更新类型**
本次提交涵盖多种类型，其中**重构**与**Bug修复**占比突出，同时包含**功能新增**、**性能优化**和**测试优化**。
*   **重构**：以 `#41191`-`#41200` 系列提交为代表，集中对前馈网络（FFN）计算流程进行了一系列架构优化，旨在简化逻辑、提升可维护性。
*   **Bug修复**：修复了包括CI失败（`#41287`）、多模态输入处理错误（`#28131`）、内存管理竞态（`#40621`）以及特定硬件兼容性（如ROCm、NPU）在内的多个问题。
*   **功能新增**：主要集中在增强分布式计算和适配新硬件，例如为LoRA后端支持数据并行注意力（`#36389`）、为AMD GPU新增MXFP8矩阵乘法内核（`#41018`）以及集成MegaMoEv2（`#35619`）。
*   **性能优化与清理**：包括减少PyTorch弃用警告（`#41284`）、优化采样掩码处理（`#40986`）以及清理冗余测试代码（`#41286`， `#41215`）。

**2. 关键变更点及其与项目整体方向的关系**
这些提交紧密围绕 `sglang` 作为**高性能、易扩展大模型推理引擎**的核心目标。
*   **架构重构服务于可扩展性**：对FFN退出机制（`ffn_exit`）和层间数据流的持续重构，旨在为复杂并行策略（如张量并行、数据并行注意力）提供更清晰、灵活的代码基础，这是支持多样化模型架构的关键。
*   **硬件适配彰显生态扩展**：对AMD（`#35619`， `#39064`）、XPU（`#41224`）的支持，以及NPU修复的回退（`#41132`），表明项目致力于构建跨硬件平台的广泛兼容性。
*   **分布式与推理能力强化**：在LoRA、采样、KV缓存（HiCache）等方面的新功能和优化，直接增强了框架在复杂推理场景（如多用户并发、长序列、参数高效微调）下的性能和功能。

**3. 对项目的影响和潜在意义**
*   **提升长期可维护性**：大规模重构简化了核心计算路径，降低了未来添加新特性或修复问题的复杂度。
*   **增强生产稳定性**：对CI流程、竞态条件、错误处理的修复，提升了框架的健壮性和可靠性，这对生产环境部署至关重要。
*   **扩大应用边界**：新硬件支持和新功能（如统一的缓存策略`#38652`）使 `sglang` 能更好地服务于更广泛的用户和硬件环境。
*   **优化开发体验**：清理测试代码、统一评测入口（`#41216`）有助于降低贡献者的参与门槛，促进社区协作。

**4. 值得关注的技术点**
*   **FFN重构系列**：如何通过“声明式”地定义FFN退出点、解耦所有归约操作，来优雅地处理并行计算中的复杂依赖，这是一个优秀的架构设计案例。
*   **统一内存与HiCache优化**：在`#41248`和`#41092`中，对统一内存管理策略的调整（如尊重移动门控、智能调整缓存容量）展现了在异构内存系统中平衡性能与效率的工程深度。
*   **多模态处理健壮性**：修复`#28131`返回400状态码而非崩溃，体现了对输入鲁棒性和服务可用性的重视。
*   **分布式LoRA**：在数据并行注意力下支持LoRA（`#36389`），是适应现代大模型混合并行训练与推理需求的重要特性。

**5. 基于README的项目背景与发展影响**
`sglang` 定位为高效的大模型服务框架。本次提交通过**内部重构夯实基础**、**广泛修复保障稳定**、**积极适配拓展生态**，全面推动了项目向更**健壮、高效、通用**的方向发展。特别是FFN重构和分布式优化，直接提升了其处理前沿大模型（如DeepSeek、Qwen系列）核心瓶颈的能力，巩固了其在高性能推理领域的技术竞争力。

## 详细提交记录

### [1f6ce4b](https://github.com/sgl-project/sglang/commit/1f6ce4b0686232fce5feb0d0d841df7d9bcabc02)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-25T23:15:02Z
- **提交信息**: [Test] Remove unit tests that only mirror implementation or never run in CI (#41286)

### [2afd343](https://github.com/sgl-project/sglang/commit/2afd343934a6a25e5c53f34f2cc2591117e8cc25)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-25T23:14:13Z
- **提交信息**: [misc] Call all_gather_single / reduce_scatter_single to drop torch deprecation warnings (#41284)

### [efd9a40](https://github.com/sgl-project/sglang/commit/efd9a40bb8ab3ebe42da1d4cf3fdfe3da6e706a2)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-25T23:13:18Z
- **提交信息**: [PD] Share one head-slice helper across mooncake, mori, and nixl (#39660)

Co-authored-by: BBuf <1182563586@qq.com>

### [95047d3](https://github.com/sgl-project/sglang/commit/95047d3464764ccfa2ee3391e1c07e75df37c6aa)

- **作者**: Yuwei An
- **时间**: 2026-09-25T22:55:21Z
- **提交信息**: [Fix] Fix cpu CI fail introduced by pr #38652 (#41287)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [516ab77](https://github.com/sgl-project/sglang/commit/516ab7761950e600d73061473dc096f91b195c58)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-25T22:48:38Z
- **提交信息**: [Test] Route all sgl-eval benchmarks through run_sgl_eval and deprecate run_eval (#41280)

### [27e883a](https://github.com/sgl-project/sglang/commit/27e883a20d2d481fce2b3f8a6fab4367854da573)

- **作者**: Kevin Mi
- **时间**: 2026-09-25T22:45:40Z
- **提交信息**: dsv4.1-amd: gfx950 MXFP8 matmul kernels and fp8-grid producers (#41018)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c421d16](https://github.com/sgl-project/sglang/commit/c421d1656375099a53936a21171e2b5aa2d18dbd)

- **作者**: Erik Wijmans
- **时间**: 2026-09-25T22:03:47Z
- **提交信息**: [sglang][lora] Support DP attention in LoRA backends (#36389)

Co-authored-by: Ethan (Yusheng) Su <yushengsu@radixark.ai>

### [cf5df82](https://github.com/sgl-project/sglang/commit/cf5df82680a5a5ae066d8eb3d889f171f0bcfc97)

- **作者**: chunxiaozheng
- **时间**: 2026-09-25T21:08:45Z
- **提交信息**: [KVCache] Support lmcache unified radix cache (#38652)

Signed-off-by: chunxiaozheng <1179548172@qq.com>
Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [d3e3945](https://github.com/sgl-project/sglang/commit/d3e3945e41238749e19192d8bc3335216cd4ef55)

- **作者**: Ethan (Yusheng) Su
- **时间**: 2026-09-25T21:01:08Z
- **提交信息**: [LoRA] Size dense row/column-parallel LoRA buffers from the base linear's real shard (#39379)

### [f88572a](https://github.com/sgl-project/sglang/commit/f88572a57c72774ffc69f1667f45f87e60ad263c)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-25T20:59:17Z
- **提交信息**: [Test] Add in-process sgl-eval adapter and move validated GSM8K tests to it (#41216)

### [f337f01](https://github.com/sgl-project/sglang/commit/f337f01b80db4a1d48bfdab6e202577db8ee64a3)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-25T19:50:31Z
- **提交信息**: [Test] Remove dead eval modules and point GSM8K/MMLU docs to sgl-eval (#41215)

### [ac62ddf](https://github.com/sgl-project/sglang/commit/ac62ddf164a392dc6253381712719b24a83803e1)

- **作者**: metamergebot
- **时间**: 2026-09-25T19:47:38Z
- **提交信息**: [Rust frontend] Decode input_ids without untagged buffering (#41246)

Co-authored-by: Jialin Ouyang <Jialin.Ouyang@gmail.com>
Co-authored-by: Lucia Fang <116399278+luccafong@users.noreply.github.com>

### [24b6930](https://github.com/sgl-project/sglang/commit/24b693007619d95c6e9c1dd36c94e165c8d4d44c)

- **作者**: Nan Jiang
- **时间**: 2026-09-25T19:20:25Z
- **提交信息**: [Sampling] Stream sampling masks as per-request arrays (#40986)

### [6d35cee](https://github.com/sgl-project/sglang/commit/6d35cee7fc92d0ae0bdd3fa16e7767c2c361d5b1)

- **作者**: cctry
- **时间**: 2026-09-25T19:18:08Z
- **提交信息**: Fix multimodal feature offload races (#40621)

Co-authored-by: cctry <cctry@fb.com>
Co-authored-by: Yongji Wu <yongji@meta.com>
Co-authored-by: Zhiqiang Xie <xiezhq@stanford.edu>

### [671000a](https://github.com/sgl-project/sglang/commit/671000aee669c5af5bc8b40c70867c311050522e)

- **作者**: metamergebot
- **时间**: 2026-09-25T19:17:28Z
- **提交信息**: [unified-memory] Honor move gates in float relocation and size auto HiCache from host capacity (#41248)

Co-authored-by: Yonghao Zhuang <yhzhuang@meta.com>

### [31b931e](https://github.com/sgl-project/sglang/commit/31b931edc358c0ec01119a3a55952c1ea334a00e)

- **作者**: Ting SUN
- **时间**: 2026-09-25T17:51:33Z
- **提交信息**: fix(multimodal): return 400 for corrupt image inputs (#28131)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Co-authored-by: Justin Tong <justintong0323@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [0154f72](https://github.com/sgl-project/sglang/commit/0154f72b48d54e96df7dac69bd7677156c2dc1b6)

- **作者**: Olga Miroshnichenko
- **时间**: 2026-09-25T17:31:29Z
- **提交信息**: [ROCm][Bugfix] Keep quantization for mixed Quark Qwen3.5 MTP checkpoints (#39064)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>

### [67bb6a5](https://github.com/sgl-project/sglang/commit/67bb6a58d0dad4a39af80fa1b2bf86f0de0cb99b)

- **作者**: Even Zhou
- **时间**: 2026-09-25T15:56:22Z
- **提交信息**: Revert "[NPU] Fuse FIA KV-cache K/V writes into one npu_scatter_pa_kv_cache call" (#41132)

### [2f5c9ac](https://github.com/sgl-project/sglang/commit/2f5c9ac43d76eef11e8561c89c55a79db7db715a)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-25T10:01:06Z
- **提交信息**: [diffusion] Enable lossless Cosmos3 Super T2I QK fusion on Hopper TP2 (#40486)

### [a749d84](https://github.com/sgl-project/sglang/commit/a749d843032750435cac8322a4b92888efb4a89f)

- **作者**: Jianghai
- **时间**: 2026-09-25T09:27:38Z
- **提交信息**: [Diffusion] Fix AttributeError in grouped forward_batch by installing the residency manager (#34417)

Co-authored-by: mickqian <mickqian@users.noreply.github.com>

### [62122c8](https://github.com/sgl-project/sglang/commit/62122c838a81c933573a82860bce4fcc1fd86ddc)

- **作者**: ashwini rathi
- **时间**: 2026-09-25T08:54:05Z
- **提交信息**: [XPU] Disable test_ngram_corpus on XPU and extend XPU CI path filter (#41224)

### [3450d68](https://github.com/sgl-project/sglang/commit/3450d68d4ede9c5c8fbd7f56aba6b28e57630d9b)

- **作者**: Cheng Wan
- **时间**: 2026-09-25T08:50:35Z
- **提交信息**: [Refactor] Decide an FFN exit's completion once and declare the group it owes (#41200)

### [26a3214](https://github.com/sgl-project/sglang/commit/26a3214cdae3713feefae0ca67a85baa6a80b188)

- **作者**: Cheng Wan
- **时间**: 2026-09-25T08:49:33Z
- **提交信息**: [Refactor] Take a layer's last-layer fact from its scatter-mode plan (#41199)

### [8f5a636](https://github.com/sgl-project/sglang/commit/8f5a636f8d1c9e6657fe73d5b1084ded281f2656)

- **作者**: Cheng Wan
- **时间**: 2026-09-25T08:48:30Z
- **提交信息**: [Refactor] Build prepare_mlp and the layout moves from named steps (#41191)

### [b7f6d04](https://github.com/sgl-project/sglang/commit/b7f6d04a9af1a786990754e292551450d640b763)

- **作者**: Cheng Wan
- **时间**: 2026-09-25T08:47:43Z
- **提交信息**: [Refactor] Move Step-3.5, GLM5-Next, Dots3, MiniMax-M3 and Qwen3.5 onto ffn_exit (#41198)

### [963e9fb](https://github.com/sgl-project/sglang/commit/963e9fb42d9232863da5947ddd6d4c3deb41167c)

- **作者**: Cheng Wan
- **时间**: 2026-09-25T08:47:03Z
- **提交信息**: [Refactor] Leave the FFN reduction to the next layer under attention DP (#41197)

### [9d7f44b](https://github.com/sgl-project/sglang/commit/9d7f44bdbb1e413858d140d464c2473ccabd3ac4)

- **作者**: Cheng Wan
- **时间**: 2026-09-25T08:46:03Z
- **提交信息**: [Refactor] Carry a deferred FFN all-reduce as UnreducedOutput and complete it in the next layer without the fused kernel (#41196)

### [402df23](https://github.com/sgl-project/sglang/commit/402df23188dbdb16cd5a83392125498285c688b0)

- **作者**: Cheng Wan
- **时间**: 2026-09-25T08:45:00Z
- **提交信息**: [Fix] Stop counting a deferred FFN sum more than once: replicated TP1 shared expert, dense reduce_scatterv (#41195)

### [1409f46](https://github.com/sgl-project/sglang/commit/1409f469be467a5114ce08efe91446cdb23a61a2)

- **作者**: Cheng Wan
- **时间**: 2026-09-25T08:43:55Z
- **提交信息**: [Fix] Plan NextN / MTP draft layers as one-layer models and fix the Bailing V2 NextN draft (#41194)

### [51c92e8](https://github.com/sgl-project/sglang/commit/51c92e8df1378cdd9bd16022e46b49d913b6f040)

- **作者**: Cheng Wan
- **时间**: 2026-09-25T08:42:16Z
- **提交信息**: [Fix] Complete the all-reduce when the flashinfer fused norm declines a batch (#41193)

### [515f5be](https://github.com/sgl-project/sglang/commit/515f5be77e74761c269e007ac41a5895191a1b7d)

- **作者**: kk
- **时间**: 2026-09-25T07:47:08Z
- **提交信息**: [AMD] Integrate Aiter MegaMoEv2 for DeepSeek-V4 (#35619)

### [434c2e3](https://github.com/sgl-project/sglang/commit/434c2e3adcd77afe42d6604b693d97aef71938e6)

- **作者**: Shuwen Wang
- **时间**: 2026-09-25T07:06:24Z
- **提交信息**: [HiCache] fix: Drain pending backups before internal Mamba write-back (#41092)

### [cbe1377](https://github.com/sgl-project/sglang/commit/cbe137727ecc95d9e22e2cd8b14fe3f4f3ff6350)

- **作者**: Shuwen Wang
- **时间**: 2026-09-25T07:06:05Z
- **提交信息**: [HiCache] Give trailing sidecar storage transfers a contiguous prefix_keys chain (#40456)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
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


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92684
- **最后更新**: 2026-09-26T00:38:59Z

## 提交统计

- **昨日提交总数**: 41
- **提交者数量**: 29
- **主要提交者**: Raphaël Rialland, Harry Mellor, Taneem Ibrahim

## AI分析总结

### **提交分析总结 (vllm-project/vllm)**

**1. 主要更新类型**
本次提交批次包含多种类型更新，其中 **Bug修复** 和 **性能优化** 占主导，同时涵盖了 **新功能开发**、**平台支持扩展**、**持续集成（CI）改进** 和 **文档优化**。

**2. 关键变更点及其与项目方向的关系**
*   **核心稳定性与可靠性提升**：大量修复了针对特定模型（如Kimi K3、GLM-5.3）、核心组件（如内存分配器、KV缓存连接器）和前端API（如Responses API）的Bug。这直接支撑了项目“可靠、低成本服务”的目标。
*   **性能深度优化**：通过内核级优化（如向量化FP8量化、推理解析器延迟重计数）和算法改进（如字符串处理避免O(N^2)），提升推理吞吐量和降低延迟，服务于“快速、经济”的核心目标。
*   **硬件生态扩展（AMD ROCm）**：大量提交专注于ROCm平台，包括依赖更新、CI测试覆盖增强（针对MI355、gfx950等新硬件）及针对特定模型（如Kimi-K3, DeepSeek V4）的优化。这显著推动了项目“为所有人提供服务”的包容性目标。
*   **工程基础建设**：改进了CI测试报告、基准测试工具（添加model_id）和日志配置，提升了项目开发和维护效率。

**3. 对项目的影响和潜在意义**
*   **提升生产就绪度**：众多Bug修复和性能优化增强了vLLM在生产环境中的稳定性和效率，巩固了其作为主流LLM推理引擎的地位。
*   **扩大用户与硬件覆盖面**：对ROCm平台的大力投入和优化，使vLLM能更好地服务AMD GPU用户，实现了更广泛的硬件普惠。
*   **增强开发者体验与透明度**：改进的基准测试、日志记录和CI工具链，让性能评估、问题调试和贡献流程更加顺畅，有助于社区健康发展。

**4. 值得关注的技术点**
*   **推理框架优化**：如`LiLiCorr drafter`（投机解码）和针对非连续流的推理使用重计数延迟优化。
*   **内核与量化创新**：包括`DiffusionGemma`的一次性采样统计内核、动态FP8量化内核优化，以及针对特定模型（如GLM-5.3）的元数据操作和内核级性能提升。
*   **内存与分配器管理**：修复了分配器碎片化导致的KV缓存缩减问题，以及配置切换时的状态别名错误，对资源利用效率至关重要。

**5. 对项目发展的综合影响**
这些提交共同推动了vLLM向着**更稳健、更高效、更广泛兼容**的方向演进。项目不仅在“修补”现有功能以提升质量，更在积极“开疆拓土”——深度优化内核性能、积极拥抱AMD ROCm生态、加固投机解码等前沿技术。这体现了vLLM在巩固LLM服务核心竞争力的同时，正通过**技术创新和生态拓展**，持续践行其“Easy, fast, and cheap LLM serving for everyone”的愿景，为在多元化硬件上提供高性能推理服务奠定坚实基础。

## 详细提交记录

### [9bf44c4](https://github.com/vllm-project/vllm/commit/9bf44c40134c024956df9134036b1d5b3d4eef7b)

- **作者**: Elvir Crnčević
- **时间**: 2026-09-25T23:29:56Z
- **提交信息**: [Bugfix][Reasoning] Count Kimi K3 reasoning tokens (#58372)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>
Signed-off-by: Flora Feng <4florafeng@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [974cb65](https://github.com/vllm-project/vllm/commit/974cb65155303139cec4f5d8d8b68bbd8ef49a2a)

- **作者**: Rui Zhu
- **时间**: 2026-09-25T23:23:11Z
- **提交信息**: [Bugfix] V1: fix allowed_token_ids_mask aliasing in InputBatch.swap_states (#48419)

Signed-off-by: Rui Zhu <rui.zhu.rz399@yale.edu>
Co-authored-by: Claude <noreply@anthropic.com>

### [b040321](https://github.com/vllm-project/vllm/commit/b040321b333c1e9d1b9074d1a8c70e361544667e)

- **作者**: Ricardo-M-L
- **时间**: 2026-09-25T23:22:13Z
- **提交信息**: fix: perf: use startswith(x, i) instead of string slicing to avoid O(N^2) (#52580)

Signed-off-by: Ricardo-M-L <ricardoporsche001@icloud.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [6ec2f84](https://github.com/vllm-project/vllm/commit/6ec2f84e1a42cdca59779ffae20aa62c8beda993)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-25T23:10:14Z
- **提交信息**: [Pooling] Preserve BERT-family heads for raw logits (#57664)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [614b55f](https://github.com/vllm-project/vllm/commit/614b55f0b6dbcba0da27c261e9daa52633fe8dd0)

- **作者**: Linkun
- **时间**: 2026-09-25T22:55:21Z
- **提交信息**: [AuxOutput] Only require Model Runner V2 on GPU platform (#58205)

Signed-off-by: Linkun Chen <github@lkchen.net>

### [e55d076](https://github.com/vllm-project/vllm/commit/e55d076f89fd01a0538a3e496d8ff20bf7980100)

- **作者**: Oxana Korzh
- **时间**: 2026-09-25T22:34:19Z
- **提交信息**: [Bugfix] Don't drop the rest of the allocator config when toggling expandable segments (#57982)

Signed-off-by: Oxana Korzh <okorzh@amd.com>

### [4ccfe12](https://github.com/vllm-project/vllm/commit/4ccfe1239843998f9b3e109f159278dc0fcbf753)

- **作者**: Raphaël Rialland
- **时间**: 2026-09-25T22:01:48Z
- **提交信息**: [watermarking] golden tests for backwards compatibility (#56809)

Signed-off-by: Raphael Rialland <raphael.rialland@mistral.ai>
Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b6761e8](https://github.com/vllm-project/vllm/commit/b6761e8ded57ef85b708f34af8cab1649eae1069)

- **作者**: yzong-rh
- **时间**: 2026-09-25T21:08:55Z
- **提交信息**: [Bugfix] Default missing detail for Responses API input images (#57241)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Co-authored-by: Ben Browning <56071+bbrowning@users.noreply.github.com>

### [8b47e8b](https://github.com/vllm-project/vllm/commit/8b47e8b22caf0022b00df3b421cf2d41419a04a7)

- **作者**: Cheng Rui
- **时间**: 2026-09-25T21:08:23Z
- **提交信息**: [Perf][Frontend] Defer reasoning usage recounts for non-continuous chat streams (#56067)

Signed-off-by: Cheng Rui <286040359@qq.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [de2d478](https://github.com/vllm-project/vllm/commit/de2d478d9a1c5c9c99dd4f6e6ef304c4a5e42617)

- **作者**: Nick Hill
- **时间**: 2026-09-25T21:08:00Z
- **提交信息**: [Bugfix][Frontend] Document 404 response for `/generative_scoring` (#58788)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [7871963](https://github.com/vllm-project/vllm/commit/7871963fcc8cd3484addb2f7abddcd0f2478028d)

- **作者**: Denis Ermakov
- **时间**: 2026-09-25T21:00:39Z
- **提交信息**: [Bugfix][Frontend] Respect max_output_tokens in the Harmony tool-call loop (#58551)

Signed-off-by: errmakov <ide404@gmail.com>
Co-authored-by: Du Bin <8174807+dubin555@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [83db8c8](https://github.com/vllm-project/vllm/commit/83db8c83904dcccb95ed202a3453b0492ad9c2df)

- **作者**: Yousaf
- **时间**: 2026-09-25T20:43:08Z
- **提交信息**: [Feature][Frontend] Add granite_thinking_parser reasoning parser for Granite 4.2 (#55957)

Signed-off-by: Yousaf shah <yousaf.shah@gmail.com>
Co-authored-by: sfeng33 <4florafeng@gmail.com>

### [e440b75](https://github.com/vllm-project/vllm/commit/e440b75bb6d5d9f23a5403fab22fa8886c91b0a8)

- **作者**: Rohan Potdar
- **时间**: 2026-09-25T19:55:52Z
- **提交信息**: [ROCm] Bump torch 2.13, triton 3.8, torchaudio, torchvision (#50605)

Signed-off-by: Rohan Potdar <rohan.potdar@amd.com>
Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Signed-off-by: jpvillam <juan.villamizar@amd.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: jpvillam <juan.villamizar@amd.com>

### [31cc226](https://github.com/vllm-project/vllm/commit/31cc2264011a7f9dbbea4d6e13f696cb0eee5282)

- **作者**: stefankoncarevic
- **时间**: 2026-09-25T19:45:32Z
- **提交信息**: [ROCm][CI] Run the MLA attention+quant fusion test on ROCm (#58717)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [2d7dd0e](https://github.com/vllm-project/vllm/commit/2d7dd0e5c1f9800a3b8c8f38fd832ee335fa7fba)

- **作者**: stefankoncarevic
- **时间**: 2026-09-25T19:44:49Z
- **提交信息**: [Bugfix][CI] Report subprocess test skips as skips, not passes (#58701)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [2bc902e](https://github.com/vllm-project/vllm/commit/2bc902eb0f7d3e3e171002e456daee254497b46b)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-25T19:13:59Z
- **提交信息**: [CI] [MRV2] Restore MRV2 pp dp coverage (#57735)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [22bbe3f](https://github.com/vllm-project/vllm/commit/22bbe3f1023a68a7d1f2de566dd4242fdcfd36c3)

- **作者**: Sheral Kumar
- **时间**: 2026-09-25T18:27:53Z
- **提交信息**: [ROCm][CI] Expand single-GPU coverage on MI355 DPX (#57599)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <andreas.karatzas@protonmail.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Andreas Karatzas <andreas.karatzas@protonmail.com>

### [353e491](https://github.com/vllm-project/vllm/commit/353e491efd3a23057004a3ab68fcfbda4abbee13)

- **作者**: Matt Mastracci
- **时间**: 2026-09-25T18:14:55Z
- **提交信息**: [Perf] DiffusionGemma: one-pass sampler statistics kernel (#58226)

Signed-off-by: Matt Mastracci <matthew@mastracci.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e3dd5b5](https://github.com/vllm-project/vllm/commit/e3dd5b5a758a6ba1a56f0d79a652ffbb8560abab)

- **作者**: stefankoncarevic
- **时间**: 2026-09-25T18:05:54Z
- **提交信息**: [ROCm][CI] Test AMD DeepSeek V4 MoE routing against a PyTorch reference (#58740)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [1b922ff](https://github.com/vllm-project/vllm/commit/1b922ffcbe75cd411fab98a773f47b8f0294e43b)

- **作者**: stefankoncarevic
- **时间**: 2026-09-25T18:02:15Z
- **提交信息**: [ROCm][CI] Add quantized MoE serving test for gfx950 (#58748)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [b217575](https://github.com/vllm-project/vllm/commit/b21757555ac5f853a8eff02a687d2777437e055b)

- **作者**: stefankoncarevic
- **时间**: 2026-09-25T17:43:40Z
- **提交信息**: [ROCm][CI] Cover the AITER MQA logits dispatch on gfx950 (#58724)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [1417022](https://github.com/vllm-project/vllm/commit/1417022c3dbb633f9d0c2ac1db2171445bb91b08)

- **作者**: jiacao-amd
- **时间**: 2026-09-25T17:33:30Z
- **提交信息**: [ROCm][Kimi-K3] Optimize low-concurrency speculative KDA (#58045)

Signed-off-by: jiacao-amd <jiahui.cao@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [c89b5b4](https://github.com/vllm-project/vllm/commit/c89b5b4176066d689a5fe40b0bea8b425ac0c65b)

- **作者**: GokayAI
- **时间**: 2026-09-25T17:23:44Z
- **提交信息**: [Bugfix][KV Connector] Reap expired NIXL leases behind a heartbeated head (#58292)

Signed-off-by: GokayAI <60583610+gokay-ai@users.noreply.github.com>
Co-authored-by: GokayAI <gokay-ai@users.noreply.github.com>

### [c88f482](https://github.com/vllm-project/vllm/commit/c88f4824fff42794d026348b86f9b78869fa273e)

- **作者**: Wentao Ye
- **时间**: 2026-09-25T17:15:18Z
- **提交信息**: [GLM5.3 Perf] Optimize glm 5.3 metadata op, 1.6~4.8x kernel level performance improvement (#58450)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [2617fe9](https://github.com/vllm-project/vllm/commit/2617fe938355594c48d4512a2ef6b470962aac1a)

- **作者**: Matt Mastracci
- **时间**: 2026-09-25T16:51:34Z
- **提交信息**: [Bugfix][GLM-5.3-Flash] kpool corruption with speculative decoding (#58454)

Signed-off-by: Matt Mastracci <matthew@mastracci.com>
Signed-off-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [f83ea61](https://github.com/vllm-project/vllm/commit/f83ea61cfe77f0b200f2ded1fda9be5ff591af2c)

- **作者**: Yashasvi Chaurasia
- **时间**: 2026-09-25T16:43:37Z
- **提交信息**: [Benchmark] Record model_id in bench latency/throughput --output-json (#58112)

Signed-off-by: yashasvi <yashasvi@ibm.com>

### [2edbb32](https://github.com/vllm-project/vllm/commit/2edbb32e58aa719bd02ae568fe05ae3e87d2b38e)

- **作者**: Matt Mastracci
- **时间**: 2026-09-25T16:36:36Z
- **提交信息**: [Bugfix][GLM-5.3-Flash] SM90 sparse MLA: index_kpool mismatch leads to corruption via unread query token (#58704)

Signed-off-by: Matt Mastracci <matthew@mastracci.com>
Signed-off-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [f339e0e](https://github.com/vllm-project/vllm/commit/f339e0e7571c0bd49d6d5f1acb9f21a35b65e4ed)

- **作者**: Denis Ermakov
- **时间**: 2026-09-25T16:33:19Z
- **提交信息**: [Bugfix][Frontend] Keep logprobs of parser-suppressed streaming chunks (#58583)

Signed-off-by: errmakov <ide404@gmail.com>
Co-authored-by: Yanxiao Zhao <39199723+sdpkjc@users.noreply.github.com>
Co-authored-by: Prakhar Agarwal <270064960+agarwalprakhar2511@users.noreply.github.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [6491f48](https://github.com/vllm-project/vllm/commit/6491f481a7c0fb3aa77bbc6649584b545c65c871)

- **作者**: Robert Shaw
- **时间**: 2026-09-25T16:16:27Z
- **提交信息**: [Bugfix] Stop allocator fragmentation from shrinking the KV cache during memory profiling (#58430)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Signed-off-by: Robert Shaw <robertgshaw2-redhat@h100-01.nemg-001.lab.rdu2.dc.redhat.com>
Signed-off-by: Robert Shaw <robshaw@redhat.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Robert Shaw <robertgshaw2-redhat@h100-01.nemg-001.lab.rdu2.dc.redhat.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [a44d7b5](https://github.com/vllm-project/vllm/commit/a44d7b51511fff6fde2bafb9c4715433a7627d1c)

- **作者**: Mark McLoughlin
- **时间**: 2026-09-25T16:12:28Z
- **提交信息**: [Core][Logging] Fix JSON logging process decoration (#57957)

Signed-off-by: Mark McLoughlin <markmc@redhat.com>

### [38cc054](https://github.com/vllm-project/vllm/commit/38cc054fc2269941cd35ecdfd198aacbb2eabfb8)

- **作者**: Monishver
- **时间**: 2026-09-25T15:19:48Z
- **提交信息**: [Perf][Kernel] Vectorized flat abs-max for dynamic per-tensor FP8 quantization (#58194)

Signed-off-by: Monishver Chandrasekaran <monishverchandrasekaran@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [f550ad8](https://github.com/vllm-project/vllm/commit/f550ad8bf7a3983a16aafd25ad18d8b48f4d5218)

- **作者**: chuan932
- **时间**: 2026-09-25T15:11:42Z
- **提交信息**: [Kernel][Perf] Register-resident path for per-token-group 8-bit quant (#55330)

Signed-off-by: chao.huan <chao.huan@nio.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [bb35e25](https://github.com/vllm-project/vllm/commit/bb35e2587bb5ca3f149b718744949fd10210e124)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-25T15:04:41Z
- **提交信息**: [Pooling] Preserve reranker tokenization with document limits (#57666)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [50f7808](https://github.com/vllm-project/vllm/commit/50f78084da2af4c79f54aa19f09972e2ec5d1049)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-25T15:01:31Z
- **提交信息**: [Bugfix] Fix generative scoring body cancellation (#57729)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [234df71](https://github.com/vllm-project/vllm/commit/234df712ed6da81d8c8213a16cd913a747380214)

- **作者**: Nick Hill
- **时间**: 2026-09-25T14:59:27Z
- **提交信息**: [MRV2] Minor model_runner.py code cleanup (#58610)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [73a78e6](https://github.com/vllm-project/vllm/commit/73a78e6f1f38e280986b81e0f2a9aa5e1ee6fe47)

- **作者**: Andrii Skliar
- **时间**: 2026-09-25T14:08:28Z
- **提交信息**: [SpecDecode] Add LiLiCorr drafter (#57934)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Signed-off-by: Andrii Skliar <andreyws96@gmail.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Benjamin Chislett <chislett.ben@gmail.com>

### [25b0add](https://github.com/vllm-project/vllm/commit/25b0add7b8a1c944d5c4e364f2de6aa82497a2ad)

- **作者**: djramic
- **时间**: 2026-09-25T10:52:15Z
- **提交信息**: [ROCm][CI] Pass weight_shape in MXFP8 block32 linear tests (#58698)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [45d56c0](https://github.com/vllm-project/vllm/commit/45d56c0baf454f2816af514011ae27c2857ee312)

- **作者**: Mark McLoughlin
- **时间**: 2026-09-25T10:36:59Z
- **提交信息**: [Core] Model console logging as CLI configuration (#57205)

Add `--logging-config` CLI argument which can be supplied as
JSON or using dotted arguments. The `--log-level` argument
is provided for convenience, and `--log-config-file` is deprecated
in favor of `--logging-config.pylogging_config_file`.

Signed-off-by: Mark McLoughlin <markmc@redhat.com>
Co-authored-by: AI Assistant <noreply@openai.com>

### [fa6c407](https://github.com/vllm-project/vllm/commit/fa6c407d15697e1a1d4d017d799c9d4da36c87b2)

- **作者**: Thang Nguyen
- **时间**: 2026-09-25T10:25:11Z
- **提交信息**: [CI] Shard (H100) Helion Kernels five ways (#58645)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [afea5c2](https://github.com/vllm-project/vllm/commit/afea5c20c7c20d697132f6145cb68e06d447c23a)

- **作者**: Harry Mellor
- **时间**: 2026-09-25T10:01:11Z
- **提交信息**: [Docs] Add return annotation to `fused_mm_input_norm_triton` (#58687)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [378504a](https://github.com/vllm-project/vllm/commit/378504a5442b8a9240b359dae3e6f75f35c38f19)

- **作者**: Yongye Zhu
- **时间**: 2026-09-25T07:38:29Z
- **提交信息**: [MoE] Defer the TRTLLM-Gen top-k finalize on the modular path (#58635)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-26
**监控日期**: 2026-09-25
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7063
- **最后更新**: 2026-09-26T00:31:02Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 14
- **主要提交者**: Joshna-Medisetty, Gao Han, chickeyton

## AI分析总结

根据提供的提交记录，结合项目“易用、快速且经济的全模态模型服务”的目标，分析如下：

**1. 主要更新类型**
本次提交以 **Bug修复（占比超过70%）** 为主，同时包含 **新功能开发** 和 **CI/测试基础设施优化**。无明显文档更新或大规模重构。

**2. 关键变更点及其与项目整体方向的关系**
*   **稳定性与可靠性强化**：大量Bug修复集中于修复MiniCPM-o、MammothModa2、Nemotron VoiceChat等关键多模态模型的运行时崩溃、输入处理错误及资源管理问题，直接提升了核心服务的稳定性和生产就绪度。
*   **硬件生态扩展**：新增Intel Arc BMG的预配置支持，拓宽了项目的硬件部署选项，符合“为所有人提供服务”的普惠目标。
*   **性能与功能优化**：针对扩散模型的序列并行支持、融合后处理以及权重格式（如BF16/FP8）管理优化，旨在提升图像生成任务的效率和灵活性，丰富了“全模态”服务的内涵。

**3. 对项目的影响和潜在意义**
*   **正面影响**：显著增强了多款已支持模型的可靠性和运行效率，降低了用户的使用门槛和调试成本。新硬件支持扩大了潜在用户群。
*   **潜在意义**：持续的Bug修复表明项目正从快速迭代期向稳定期过渡。对Diffusion模型管线的多次优化，显示了社区在提升生成式AI服务性能上的持续投入。

**4. 值得关注的技术点**
*   **运行时资源管理**：涉及CUDA图填充下的内存切片（MRV2）、KV缓存分配（MammothModa2）及模型加载阶段的运行时构建（MiniCPM-o），反映了在复杂模型服务中进行精细资源调度的挑战。
*   **模型并行与优化**：图像序列并行（BOOGU）和融合后处理（mHC）技术，是提升大型生成模型吞吐量的关键手段。
*   **测试健壮性**：多个提交修复了测试环境（如默认设备、Codec回读）的隔离性问题，为持续集成提供了更可靠的保障。

**5. 对项目发展的影响**
这些提交共同推动项目朝着 **“更稳定”、“更广泛”和“更高效”** 的方向发展：
*   **更稳定**：通过系统性修复核心模型的Bug，夯实了作为可靠服务框架的基础，增强了用户信心。
*   **更广泛**：通过支持新的硬件（Intel Arc）和优化不同模型（如MiniCPM-o多轮对话、MammothModa2多模态），扩大了项目能覆盖的模型与设备范围。
*   **更高效**：针对扩散模型等计算密集型任务的优化，提升了服务在实际部署中的性能表现，直接服务于“快速且经济”的核心承诺。

总而言之，这批提交体现了项目社区在巩固核心功能、扩大硬件兼容性以及追求性能卓越方面的积极努力，是项目走向成熟和广泛应用的关键一步。

## 详细提交记录

### [bcb4ae2](https://github.com/vllm-project/vllm-omni/commit/bcb4ae288f77dbee431c0649b72ef43a4722bb2b)

- **作者**: Khairul Kabir
- **时间**: 2026-09-25T21:54:38Z
- **提交信息**: [CI][Diffusion] Add tiny model builder for Krea2Pipeline (#6421)

Signed-off-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>

### [62ebad2](https://github.com/vllm-project/vllm-omni/commit/62ebad2d7cd79da24653110d8043cc13fb744328)

- **作者**: Joshna-Medisetty
- **时间**: 2026-09-25T20:42:08Z
- **提交信息**: Add Intel Arc BMG recipes for validated P0 diffusion models. (#7537)

Signed-off-by: Joshna-Medisetty <joshna.medisetty@intel.com>

### [5e36b5a](https://github.com/vllm-project/vllm-omni/commit/5e36b5a86b47382cf6d8d213851400127d14fb7d)

- **作者**: Khairul Kabir
- **时间**: 2026-09-25T20:17:19Z
- **提交信息**: [Bugfix] Apply function module marker per-model instead of hardcoding diffusion (#5875)

Signed-off-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [a8576cc](https://github.com/vllm-project/vllm-omni/commit/a8576ccb725c4e21cd13c3eb5f9a546b21149d2b)

- **作者**: Gao Han
- **时间**: 2026-09-25T17:42:53Z
- **提交信息**: [Bugfix] Fix MiniCPM-o 4.5 seeded turns and window E2E inputs (#8160)

Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>

### [d31a2a3](https://github.com/vllm-project/vllm-omni/commit/d31a2a3ba8e33991665e3f1a652a0a7277f91e17)

- **作者**: Sy03
- **时间**: 2026-09-25T17:25:15Z
- **提交信息**: [Bugfix] Fix Nemotron VoiceChat duplex nightly handshake (#7884)

Signed-off-by: Sy03 <1370724210@qq.com>

### [5d0963b](https://github.com/vllm-project/vllm-omni/commit/5d0963b3dc325475730c1b1cc8321198da98bb39)

- **作者**: Sy03
- **时间**: 2026-09-25T16:07:22Z
- **提交信息**: [Bugfix] Fix MRV2 payload slicing with CUDA Graph padding (#8159)

Signed-off-by: Sy03 <1370724210@qq.com>

### [43e5071](https://github.com/vllm-project/vllm-omni/commit/43e507117f04a86f2df8d405cbe03c1b1642eac9)

- **作者**: wangyu
- **时间**: 2026-09-25T15:05:37Z
- **提交信息**: [Bugfix] Restore torch default device between tests (#8157)

Signed-off-by: wangyu <410167048@qq.com>

### [4be6bbe](https://github.com/vllm-project/vllm-omni/commit/4be6bbe0e4e91f49e67300a080989bf1d5915cac)

- **作者**: chickeyton
- **时间**: 2026-09-25T14:57:23Z
- **提交信息**: [Bugfix][MiniCPM-o] Build the Stage-0 duplex runtime at load time (#8146)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [fe9e22d](https://github.com/vllm-project/vllm-omni/commit/fe9e22df3dcec10cceee97f568d70f4476307668)

- **作者**: bcsdhjew
- **时间**: 2026-09-25T14:52:46Z
- **提交信息**: [Bugfix] Restore MiniCPM duplex Seed-TTS startup (#8152)

Signed-off-by: Nolen Liang <nliang@nvidia.com>
Signed-off-by: bcsdhjew <nliang@nvidia.com>

### [3bd5ac9](https://github.com/vllm-project/vllm-omni/commit/3bd5ac9685b7944bd72780047c839c47ae1696b4)

- **作者**: Yuanheng Zhao
- **时间**: 2026-09-25T14:47:29Z
- **提交信息**: [Bugfix] Align Ming-Image prompt templates and RNG, fix number of layer to decompose (#8118)

Signed-off-by: Yuanheng <jonathan.zhaoyh@gmail.com>

### [b41e670](https://github.com/vllm-project/vllm-omni/commit/b41e6707b1bb0f386a908b6190e6e699214bd919)

- **作者**: DanaerLee
- **时间**: 2026-09-25T13:28:59Z
- **提交信息**: [Bugfix][MammothModa2] Stop allocating AR KV cache for the replaced language model (#8095)

Signed-off-by: MrlixiangWE <mrdanaer@gmail.com>
Co-authored-by: zijianc2 <157244773+zijianc2@users.noreply.github.com>
Co-authored-by: hsliuustc0106 <222337142+hsliuustc0106@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [29dacbd](https://github.com/vllm-project/vllm-omni/commit/29dacbd3eff275a27237ba445433981337271ca0)

- **作者**: DanaerLee
- **时间**: 2026-09-25T13:25:49Z
- **提交信息**: [Bugfix][MammothModa2] Keep AR layer 0 in BF16 in the FP8 KV preset (#8083)

Signed-off-by: MrlixiangWE <mrdanaer@gmail.com>
Co-authored-by: zijianc2 <157244773+zijianc2@users.noreply.github.com>
Co-authored-by: hsliuustc0106 <222337142+hsliuustc0106@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [9f3f475](https://github.com/vllm-project/vllm-omni/commit/9f3f475685ba0a2c86cee64d12f7611f937d549b)

- **作者**: NATURE
- **时间**: 2026-09-25T08:45:05Z
- **提交信息**: [CI/Build] Fix MiniCPM-o codec readback test under default-device dispatch (#8147)

### [95781c3](https://github.com/vllm-project/vllm-omni/commit/95781c31e082c0182e0ab1f037ed03b1a740bd13)

- **作者**: Anjie Hou
- **时间**: 2026-09-25T08:33:32Z
- **提交信息**: [Bugfix][Diffusion] Skip AllGather DLO weight restore on worker shutdown (#8103)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [3bf9608](https://github.com/vllm-project/vllm-omni/commit/3bf96080f305fa91e775c01c52c07dabc7ef8a25)

- **作者**: R0CKSTAR
- **时间**: 2026-09-25T08:25:12Z
- **提交信息**: feat(magi2): add fused mHC post-processing (#7261)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [0c7042d](https://github.com/vllm-project/vllm-omni/commit/0c7042d0d5b78474167b57d9751bda7bc55a1b5b)

- **作者**: Xenoryn
- **时间**: 2026-09-25T08:18:23Z
- **提交信息**: [Feature][Diffusion] Add BOOGU Image sequence parallel support (#5718)

Signed-off-by: Xenoryn <timberh2000@outlook.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [e561379](https://github.com/vllm-project/vllm-omni/commit/e5613794cae9e827677d5a319737769b4aacd8a6)

- **作者**: NumberWan
- **时间**: 2026-09-25T07:53:24Z
- **提交信息**: [BugFix][Cosmos3] Decode uploaded video paths in v2v preprocess (#8106)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

---
