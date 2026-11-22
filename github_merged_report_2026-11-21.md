# GitHub Stars 合并报告 - 2026-11-21

**合并日期**: 2026-11-22
**监控日期**: 2026-11-21
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


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2299
- **最后更新**: 2026-11-20T15:30:44Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Coach257

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **功能增强**（feat）：属于核心训练算子的功能优化，非单纯新增功能。

### 2. 关键变更点及与项目方向的关系
- 该提交在**专家并行（Expert Parallel, EP）路径**上，让**MLP激活值通过路由专家（routed experts）传递**，涉及 `ops`（算子）、`model`（模型）、`dist`（分布式）三个模块的协同修改。
- 这直接服务于 VeOmni 的核心目标——**"Model-Centric Distributed Recipe Zoo"**：为任意模态模型训练提供以模型为中心的分布式配方。MoE（混合专家）模型是当前大模型的主流架构，而 EP 是 MoE 训练中的关键并行策略。修复/完善 EP 路径上 MLP 激活的传递逻辑，属于对分布式训练正确性的补强。
- 标注 `(#1480)` 表明这是来自社区贡献的合并 PR，体现项目社区协作活跃。

### 3. 对项目的影响和潜在意义
- **正确性提升**：若此前 EP 路径下 MLP 激活未正确穿过路由专家，可能导致 MoE 模型训练中梯度或前向结果不一致，该修复有助于保证多专家并行训练的数值正确性。
- **稳定性增强**：对于使用 EP 并行训练 MoE 模型的用户，这是降低训练风险的重要补丁。
- **影响范围**：改动触及 ops/model/dist 三层，说明变更虽小但跨越了算子实现、模型结构和通信/并行逻辑，属于底层基础设施级别的修改。

### 4. 值得关注的技术点
- **EP 路径上的激活流转机制**：MoE 中 token 经 router 分发到不同专家，EP 要求专家分布在不同设备上，MLP 激活必须正确跨设备/跨专家传递，否则会出现信息丢失。
- **多模块联动**：算子层、模型层、分布式层需要同步修改，说明 VeOmni 的分布式抽象需要三层一致地感知同一语义变更，体现了其"配方（Recipe）"设计中分层但耦合的架构特点。
- **PR 编号 #1480 较大**，暗示项目合并历史丰富、迭代速度快。

### 5. 对项目发展的影响（结合 README 背景）
VeOmni 定位为**任意模态模型训练的分布式配方库**（附论文 arXiv:2508.02317），MoE 是其支撑"scaling"目标的关键架构之一。此提交虽是单一功能修复，但属于**夯实 MoE + EP 这一核心训练路径的正确性基础**——没有正确的分布式算子语义，再丰富的"配方"也无法产出可靠结果。它强化了项目在"分布式训练可靠性"上的工程可信度，与项目持续推进社区贡献、完善多模态 MoE 训练能力的整体方向一致。

## 详细提交记录

### [12acd6e](https://github.com/ByteDance-Seed/VeOmni/commit/12acd6e326f375e1c9d5b81e3cdc1f75f7ea41f9)

- **作者**: Coach257
- **时间**: 2026-11-21T05:04:39Z
- **提交信息**: [ops, model, dist] feat: pass the MLP activation through the routed experts, on one EP path (#1480)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3017
- **最后更新**: 2026-11-22T01:39:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2338
- **最后更新**: 2026-11-22T01:43:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6984
- **最后更新**: 2026-11-22T01:49:13Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 2
- **主要提交者**: eigen, Zihao Ye

## AI分析总结

# FlashInfer 昨日提交分析（共5条）

## 1. 主要更新类型
- **性能优化**：4条，全部围绕 Cake 后端（MLA decode 与 Gated DeltaProduct 内核）
- **兼容性修复**：1条，Windows/MSVC 宿主下的编译问题
- 无文档更新或大功能新增

## 2. 关键变更点及与项目方向的关系
- **MLA decode 持续榨取性能**：多条提交针对 DeepSeek MLA 的 BF16/FP8 分页 KV decode，优化 split-KV 路径（staged epilogue、bulk-copy split reducer、批量 split-reducer 加载、FP8 page-64 单 split 融合写输出）。这直接服务于 FlashInfer 的核心使命——为大模型推理提供最快的 GPU 内核。
- **backend="auto" 自动调优扩展**：多条提交让 auto 在更多形状/批次/序列长度上自动选择 Cake，而非手动指定。这是提升易用性、让普通用户无需调参即可获得最优性能的关键方向。
- **Gated DeltaProduct 内核微调**：按架构（SM100/103/107）和 CTA 密度选择最优 Philox 轮数与 draw-share 变体，保持位级一致的前提下提速，体现了对稀有架构的精细化调优。
- **Windows 兼容修复**：Cake 生成的内核源码在 MSVC 宿主下可编译，扩展了平台覆盖面。

## 3. 对项目的影响和潜在意义
- 性能收益量化：B200 上 auto 整体 geomean 提升约 1.08–1.09x，FP8 单 split 最高 1.86x，说明 Cake 后端正在多个 decode 形状上全面超越 cute-dsl 和 trtllm-gen，成为 Blackwell 上的首选。
- auto 自动化范围扩大意味着 FlashInfer 正从"专家手动选后端"向"开箱即得最优"演进，降低用户门槛。
- Windows 支持使库可在更广泛的开发与部署环境中构建（包括原生 arm64 宿主），有利于生态扩展。

## 4. 值得关注的技术点
- **split-KV 的分层优化**：将长 KV、少 query 行的场景拆分为独立内核（mainloop + reducer），并用批量加载、bulk-copy 等手段减少同步开销。
- **位级一致性约束下的调优**：GDP 提交强调"输出位不变，只改速度"，这是对随机舍入（stochastic rounding）类内核进行性能迭代时的重要工程纪律——避免影响模型数值结果的可复现性。
- **代码量控制**：MLA 提交特意保证 device program 数量不变（替换而非新增），说明内核家族的编译时间与二进制体积是被认真管理的约束。
- **生成代码的跨工具链适配**：通过 `_MSC_VER` 条件编译隔离 GNU/MSVC 差异（`__int128`、128-bit load 拆分），保留原始路径不受影响。

## 5. 基于项目背景的影响评估
FlashInfer 作为"高性能推理 GPU 内核库"，这批复现了其典型迭代模式：围绕主流推理工作负载（DeepSeek MLA、GDP 变体解码）在最新硬件（B200/GB300）上做持续、可量化、位级安全的微架构级优化，同时通过 backend="auto" 把这些优化自动暴露给用户。这强化了项目在 Blackwell 时代保持内核性能领先地位的能力，也显示出 Cake 后端正逐步成为多形状 decode 的主导路径。Windows 修复则补齐了平台矩阵。整体而言，这些提交巩固了项目"开箱最快"的核心价值主张，并为后续 auto 调优的进一步自动化奠定了基础。

## 详细提交记录

### [253986e](https://github.com/flashinfer-ai/flashinfer/commit/253986e2dcf5499c180e834bf16e53d3b5596be8)

- **作者**: eigen
- **时间**: 2026-11-21T21:54:52Z
- **提交信息**: perf(mla): Cake BF16 split-KV decode with a staged epilogue and a bulk-copy split reducer, and backend="auto" split-KV offers (1.04x at batch 1, KV 16384 on B200) (#9834)

The Cake backend of `trtllm_batch_decode_with_kv_cache_mla` runs
DeepSeek MLA decode on Blackwell (qk_nope 128, kv_lora_rank 512, qk_rope
64, 128 heads). It covers BF16 and FP8 KV caches with paged layouts. The
family has 22 device programs. This PR replaces two of them with new
builds, so the count stays at 22. The two programs are the mainloop and
the prefetch_all reducer of the BF16 split-KV route. That route handles
long KV with at most 18 query rows. Versus the previous Cake version
(FlashInfer main 9bd0a68c9), the owner shape (BF16, page 32, batch 1,
q_len 1, KV 16384) is 1.041x faster on B200 (17.68 -> 16.98 us) and
1.014x faster on GB300 (16.18 -> 15.95 us). In kernel time it is now
1.033x faster than the fastest non-Cake backend on B200 (cute-dsl, 17.54
us) and 1.049x faster on GB300 (cute-dsl, 16.74 us), and
`backend="auto"` now runs Cake on this shape (Table 2).

`backend="auto"` now offers Cake for BF16 split-KV units. These are 26
offer rows on B200 and GB300, for page 32/64 and q_len 1/2, without
sinks. A unit is offered only where Cake measured faster than the faster
of tuned cute-dsl and trtllm-gen on that GPU. On these units, the
geomean of main auto / PR auto is 1.077x on B200 (36 cases) and 1.090x
on GB300 (32 cases).

The kernel's other Cake programs serve the remaining BF16 page-32/64
decode shapes, FP8 page 64, and a generic tail for other shapes (other
head counts, FP8 page 32, FP8 with sinks), and the family ships on
sm_100a (B200) and sm_103a (GB300).

**Table 1: explicit `backend="cake"`.** GPUs: NVIDIA B200 (sm_100a, 148
SMs) and NVIDIA GB300 (sm_103a, 152 SMs). Software: CUDA 13.5 JIT (nvcc
13.5) and torch 2.14.1+cu130. Baselines were measured on the same GPU in
the same rounds. "Previous Cake" is FlashInfer main 9bd0a68c9. "Fastest
non-Cake" is the faster of trtllm-gen and cute-dsl. Timing is the CUPTI
kernel span over CUDA-graph replay, with L2 flushed before every
iteration. Each value is the median of the per-round medians over 6
tuned rounds. Speedup is the ratio of medians; >1 means this PR is
faster.

| GPU | KV dtype | page size | batch | q_len | KV length | lengths |
previous Cake (us) | fastest non-Cake (us) | this PR (us) | speedup vs
previous Cake | speedup vs fastest non-Cake |
|---|---|---|---|---|---|---|---|---|---|---|---|
| B200 | BF16 | 32 | 1 | 1 | 16384 | uniform | 17.68 | 17.54 (cute-dsl)
| 16.98 | 1.041x | 1.033x |
| B200 | BF16 | 32 | 2 | 1 | 8192 | uniform | 18.53 | 17.22 (cute-dsl) |
15.81 | 1.172x | 1.089x |
| B200 | BF16 | 32 | 2 | 1 | 16384 | uniform | 22.11 | 20.10 (cute-dsl)
| 19.79 | 1.117x | 1.015x |
| B200 | BF16 | 32 | 4 | 1 | 16384 | uniform | 27.63 | 27.02 (cute-dsl)
| 26.42 | 1.046x | 1.023x |
| B200 | BF16 | 32 | 2 | 2 | 8192 | uniform | 19.10 | 18.54 (cute-dsl) |
17.28 | 1.106x | 1.073x |
| B200 | BF16 | 32 | 128 | 1 | 1024 | varied | 34.02 | 42.08
(trtllm-gen) | 34.14 | 0.997x | 1.232x |
| B200 | BF16 | 32 | 128 | 1 | 4096 | uniform | 132.53 | 139.38
(cute-dsl) | 130.74 | 1.014x | 1.066x |
| B200 | BF16 | 64 | 8 | 1 | 1024 | varied | 13.95 | 13.87 (cute-dsl) |
14.00 | 0.997x | 0.991x |
| B200 | FP8 | 64 | 8 | 1 | 1024 | varied | 11.58 | 11.97 (cute-dsl) |
11.58 | 1.000x | 1.033x |
| B200 | FP8 | 64 | 32 | 1 | 4096 | varied | 24.82 | 28.35 (cute-dsl) |
24.82 | 1.000x | 1.142x |
| B200 | FP8 | 64 | 128 | 1 | 1024 | uniform | 30.18 | 30.14
(trtllm-gen) | 30.21 | 0.999x | 0.998x |
| GB300 | BF16 | 32 | 1 | 1 | 16384 | uniform | 16.18 | 16.74 (cute-dsl)
| 15.95 | 1.014x | 1.049x |
| GB300 | BF16 | 32 | 2 | 1 | 8192 | uniform | 17.26 | 16.19 (cute-dsl)
| 15.20 | 1.136x | 1.065x |
| GB300 | BF16 | 32 | 2 | 1 | 16384 | uniform | 20.83 | 19.20 (cute-dsl)
| 18.72 | 1.113x | 1.026x |
| GB300 | BF16 | 32 | 4 | 1 | 16384 | uniform | 25.26 | 27.55 (cute-dsl)
| 24.46 | 1.033x | 1.126x |
| GB300 | BF16 | 32 | 2 | 2 | 8192 | uniform | 17.41 | 17.55 (cute-dsl)
| 16.29 | 1.069x | 1.078x |
| GB300 | BF16 | 32 | 128 | 1 | 1024 | varied | 33.54 | 39.78
(trtllm-gen) | 33.42 | 1.003x | 1.190x |
| GB300 | BF16 | 32 | 128 | 1 | 4096 | uniform | 118.98 | 124.90
(cute-dsl) | 119.06 | 0.999x | 1.049x |
| GB300 | BF16 | 64 | 8 | 1 | 1024 | varied | 12.02 | 13.66 (cute-dsl) |
12.00 | 1.001x | 1.139x |
| GB300 | FP8 | 64 | 8 | 1 | 1024 | varied | 10.64 | 11.89 (cute-dsl) |
10.74 | 0.991x | 1.107x |
| GB300 | FP8 | 64 | 32 | 1 | 4096 | varied | 23.28 | 25.17 (cute-dsl) |
23.38 | 0.996x | 1.077x |
| GB300 | FP8 | 64 | 128 | 1 | 1024 | uniform | 28.49 | 27.82
(trtllm-gen) | 28.49 | 1.000x | 0.977x |

Across all measured shapes, explicit Cake vs previous Cake has these
geomeans:

- **B200:** 1.051x over 92 shapes (min 0.992x, max 1.220x). On the 62
split-KV route shapes it is 1.076x (min 0.999x, max 1.220x).
- **GB300:** 1.028x over 87 shapes (min 0.983x, max 1.148x). On the 57
split-KV route shapes it is 1.044x (min 0.984x, max 1.148x).

With L2 not flushed (GB300, 3 rounds), the owner shape goes from 14.75
to 13.44 us (1.098x). cute-dsl takes 13.98 us in the same setup.

**Table 2: `backend="auto"` on the newly offered BF16 split-KV units.**
Cases sit at the edges of each offered bucket. The setup and timing are
the same as Table 1. "Main auto" is `backend="auto"` on FlashInfer main
9bd0a68c9. The runner that auto picked is shown in parentheses. Speedup
= main auto / this PR auto; >1 means this PR is faster.

| GPU | KV dtype | page size | batch | q_len | KV length | lengths |
main auto (us) | this PR auto (us) | speedup | PR runner |
|---|---|---|---|---|---|---|---|---|---|---|
| B200 | BF16 | 32 | 1 | 1 | 4096 | uniform | 12.96 (cute-dsl) | 11.65
(cake) | 1.113x | cake |
| B200 | BF16 | 32 | 1 | 1 | 4096 | varied | 12.92 (cute-dsl) | 11.44
(cake) | 1.129x | cake |
| B200 | BF16 | 32 | 2 | 1 | 8192 | uniform | 17.33 (cute-dsl) | 15.71
(cake) | 1.103x | cake |
| B200 | BF16 | 32 | 3 | 1 | 8192 | varied | 17.74 (cute-dsl) | 16.14
(cake) | 1.099x | cake |
| B200 | BF16 | 32 | 4 | 1 | 8192 | uniform | 20.05 (cute-dsl) | 19.10
(cake) | 1.049x | cake |
| B200 | BF16 | 32 | 7 | 1 | 8192 | varied | 26.06 (cute-dsl) | 24.64
(cake) | 1.058x | cake |
| B200 | BF16 | 32 | 1 | 1 | 16384 | uniform | 17.47 (cute-dsl) | 16.82
(cake) | 1.039x | cake |
| B200 | BF16 | 32 | 1 | 1 | 16384 | varied | 17.63 (cute-dsl) | 16.61
(cake) | 1.062x | cake |
| B200 | BF16 | 32 | 2 | 1 | 16384 | uniform | 20.18 (cute-dsl) | 19.84
(cake) | 1.017x | cake |
| B200 | BF16 | 32 | 3 | 1 | 16384 | varied | 22.64 (cute-dsl) | 21.41
(cake) | 1.058x | cake |
| B200 | BF16 | 32 | 2 | 2 | 4096 | uniform | 15.68 (cute-dsl) | 14.10
(cake) | 1.112x | cake |
| B200 | BF16 | 32 | 3 | 2 | 4096 | varied | 17.49 (cute-dsl) | 15.28
(cake) | 1.145x | cake |
| B200 | BF16 | 32 | 1 | 2 | 8192 | uniform | 15.73 (cute-dsl) | 14.90
(cake) | 1.056x | cake |
| B200 | BF16 | 32 | 1 | 2 | 8192 | varied | 14.70 (cute-dsl) | 14.13
(cake) | 1.041x | cake |
| B200 | BF16 | 32 | 2 | 2 | 8192 | uniform | 18.45 (cute-dsl) | 17.38
(cake) | 1.062x | cake |
| B200 | BF16 | 32 | 3 | 2 | 8192 | varied | 22.30 (cute-dsl) | 20.22
(cake) | 1.103x | cake |
| B200 | BF16 | 32 | 2 | 2 | 16384 | uniform | 24.91 (cute-dsl) | 23.87
(cake) | 1.044x | cake |
| B200 | BF16 | 32 | 3 | 2 | 16384 | varied | 28.83 (cute-dsl) | 26.86
(cake) | 1.073x | cake |
| B200 | BF16 | 64 | 1 | 1 | 4096 | uniform | 12.91 (cute-dsl) | 11.50
(cake) | 1.122x | cake |
| B200 | BF16 | 64 | 1 | 1 | 4096 | varied | 12.94 (cute-dsl) | 11.55
(cake) | 1.120x | cake |
| B200 | BF16 | 64 | 1 | 1 | 8192 | uniform | 14.57 (cute-dsl) | 13.55
(cake) | 1.075x | cake |
| B200 | BF16 | 64 | 1 | 1 | 8192 | varied | 14.34 (cute-dsl) | 13.58
(cake) | 1.055x | cake |
| B200 | BF16 | 64 | 2 | 1 | 8192 | uniform | 17.04 (cute-dsl) | 15.66
(cake) | 1.088x | cake |
| B200 | BF16 | 64 | 3 | 1 | 8192 | varied | 17.25 (cute-dsl) | 16.02
(cake) | 1.077x | cake |
| B200 | BF16 | 64 | 1 | 1 | 16384 | uniform | 17.42 (cute-dsl) | 16.80
(cake) | 1.037x | cake |
| B200 | BF16 | 64 | 1 | 1 | 16384 | varied | 16.27 (cute-dsl) | 14.82
(cake) | 1.098x | cake |
| B200 | BF16 | 64 | 2 | 2 | 4096 | uniform | 15.44 (cute-dsl) | 14.11
(cake) | 1.094x | cake |
| B200 | BF16 | 64 | 3 | 2 | 4096 | varied | 17.31 (cute-dsl) | 15.30
(cake) | 1.132x | cake |
| B200 | BF16 | 64 | 1 | 2 | 8192 | uniform | 15.74 (cute-dsl) | 14.83
(cake) | 1.061x | cake |
| B200 | BF16 | 64 | 1 | 2 | 8192 | varied | 15.57 (cute-dsl) | 14.34
(cake) | 1.086x | cake |
| B200 | BF16 | 64 | 2 | 2 | 8192 | uniform | 18.40 (cute-dsl) | 17.39
(cake) | 1.058x | cake |
| B200 | BF16 | 64 | 3 | 2 | 8192 | varied | 20.45 (cute-dsl) | 18.40
(cake) | 1.111x | cake |
| B200 | BF16 | 64 | 1 | 2 | 16384 | uniform | 18.72 (cute-dsl) | 18.19
(cake) | 1.029x | cake |
| B200 | BF16 | 64 | 1 | 2 | 16384 | varied | 16.82 (cute-dsl) | 15.94
(cake) | 1.055x | cake |
| B200 | BF16 | 64 | 2 | 2 | 16384 | uniform | 25.04 (cute-dsl) | 23.95
(cake) | 1.045x | cake |
| B200 | BF16 | 64 | 3 | 2 | 16384 | varied | 29.22 (cute-dsl) | 27.10
(cake) | 1.078x | cake |
| GB300 | BF16 | 32 | 1 | 1 | 4096 | uniform | 12.06 (cute-dsl) | 11.25
(cake) | 1.073x | cake |
| GB300 | BF16 | 32 | 1 | 1 | 4096 | varied | 12.18 (cute-dsl) | 11.09
(cake) | 1.098x | cake |
| GB300 | BF16 | 32 | 2 | 1 | 8192 | uniform | 16.27 (cute-dsl) | 15.31
(cake) | 1.063x | cake |
| GB300 | BF16 | 32 | 3 | 1 | 8192 | varied | 17.38 (cute-dsl) | 15.44
(cake) | 1.125x | cake |
| GB300 | BF16 | 32 | 4 | 1 | 8192 | uniform | 19.09 (cute-dsl) | 18.35
(cake) | 1.040x | cake |
| GB300 | BF16 | 32 | 7 | 1 | 8192 | varied | 24.18 (cute-dsl) | 21.95
(cake) | 1.101x | cake |
| GB300 | BF16 | 32 | 1 | 1 | 16384 | uniform | 16.86 (cute-dsl) | 15.98
(cake) | 1.055x | cake |
| GB300 | BF16 | 32 | 1 | 1 | 16384 | varied | 16.64 (cute-dsl) | 15.76
(cake) | 1.056x | cake |
| GB300 | BF16 | 32 | 4 | 1 | 16384 | uniform | 27.36 (cute-dsl) | 24.80
(cake) | 1.103x | cake |
| GB300 | BF16 | 32 | 7 | 1 | 16384 | varied | 34.53
(cute-dsl/trtllm-gen) | 32.62 (cake) | 1.058x | cake |
| GB300 | BF16 | 32 | 2 | 2 | 4096 | uniform | 14.86 (cute-dsl) | 13.70
(cake) | 1.085x | cake |
| GB300 | BF16 | 32 | 3 | 2 | 4096 | varied | 16.43 (cute-dsl) | 14.34
(cake) | 1.146x | cake |
| GB300 | BF16 | 32 | 2 | 2 | 8192 | uniform | 17.57 (cute-dsl) | 16.43
(cake) | 1.069x | cake |
| GB300 | BF16 | 32 | 3 | 2 | 8192 | varied | 21.09 (cute-dsl) | 18.56
(cake) | 1.136x | cake |
| GB300 | BF16 | 32 | 2 | 2 | 16384 | uniform | 24.46
(cute-dsl/trtllm-gen) | 21.36 (cake) | 1.145x | cake |
| GB300 | BF16 | 32 | 3 | 2 | 16384 | varied | 27.33
(cute-dsl/trtllm-gen) | 24.80 (cake) | 1.102x | cake |
| GB300 | BF16 | 64 | 1 | 1 | 4096 | uniform | 12.21 (cute-dsl) | 11.12
(cake) | 1.098x | cake |
| GB300 | BF16 | 64 | 1 | 1 | 4096 | varied | 12.27 (cute-dsl) | 11.17
(cake) | 1.099x | cake |
| GB300 | BF16 | 64 | 4 | 1 | 8192 | uniform | 19.26 (cute-dsl) | 18.40
(cake/cute-dsl) | 1.047x | cake/cute-dsl |
| GB300 | BF16 | 64 | 7 | 1 | 8192 | varied | 23.07 (cute-dsl) | 20.96
(cake) | 1.101x | cake |
| GB300 | BF16 | 64 | 1 | 1 | 16384 | uniform | 16.53 (cute-dsl) | 16.03
(cake) | 1.031x | cake |
| GB300 | BF16 | 64 | 1 | 1 | 16384 | varied | 15.55 (cute-dsl) | 13.92
(cake) | 1.117x | cake |
| GB300 | BF16 | 64 | 4 | 1 | 16384 | uniform | 27.20 (cute-dsl) | 24.26
(cake) | 1.121x | cake |
| GB300 | BF16 | 64 | 7 | 1 | 16384 | varied | 32.69
(cute-dsl/trtllm-gen) | 31.62 (cake/cute-dsl) | 1.034x | cake/cute-dsl |
| GB300 | BF16 | 64 | 2 | 2 | 4096 | uniform | 14.66 (cute-dsl) | 13.58
(cake) | 1.079x | cake |
| GB300 | BF16 | 64 | 3 | 2 | 4096 | varied | 16.86 (cute-dsl) | 14.35
(cake) | 1.175x | cake |
| GB300 | BF16 | 64 | 2 | 2 | 8192 | uniform | 17.54 (cute-dsl) | 16.38
(cake) | 1.070x | cake |
| GB300 | BF16 | 64 | 3 | 2 | 8192 | varied | 19.25 (cute-dsl) | 17.15
(cake) | 1.122x | cake |
| GB300 | BF16 | 64 | 1 | 2 | 16384 | uniform | 17.34 (cute-dsl) | 16.96
(cake) | 1.023x | cake |
| GB300 | BF16 | 64 | 1 | 2 | 16384 | varied | 15.55 (cute-dsl) | 15.09
(cake) | 1.031x | cake |
| GB300 | BF16 | 64 | 2 | 2 | 16384 | uniform | 24.45
(cute-dsl/trtllm-gen) | 21.13 (cake) | 1.157x | cake |
| GB300 | BF16 | 64 | 3 | 2 | 16384 | varied | 29.55
(cute-dsl/trtllm-gen) | 26.05 (cake) | 1.135x | cake |

- **B200:** 36 unit-auto cases. Main auto / PR auto geomean 1.077x (min
1.017x, max 1.145x), 0 below 0.98x.
- **GB300:** 32 unit-auto cases. Main auto / PR auto geomean 1.090x (min
1.023x, max 1.175x), 0 below 0.98x.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved split-KV attention execution with updated output staging and
prefetching.
* **New Features**
* Automatic backend selection now considers split-KV options for
additional Blackwell configurations and workload sizes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [9bd0a68](https://github.com/flashinfer-ai/flashinfer/commit/9bd0a68c94687ad920d2de04284370397a073798)

- **作者**: eigen
- **时间**: 2026-11-21T10:21:43Z
- **提交信息**: perf(mla): batched split-reducer loads for the Cake BF16 split-KV decode (1.08x at batch 1, KV 16384) (#9825)

The Cake BF16 split-KV route links a second split-reducer build that loads every split's partial output in one batch after the dependency wait, chosen per launch for few query rows (<= 6 on B200, <= 7 on GB300) and >= 9 splits; output bits are unchanged. backend="auto" also offers Cake for one more B200 unit and for listed requests with sinks, the Cake auto candidate serves up to 1024 BF16 query rows, FP8 page-64 LSE requests run on the FP8 page-64 program, and explicit Blackwell decode warns once on the generic tail.

### [e19a6f3](https://github.com/flashinfer-ai/flashinfer/commit/e19a6f30517489156586164c8d89876e6f71d48a)

- **作者**: eigen
- **时间**: 2026-11-21T08:56:18Z
- **提交信息**: perf(cake_gdp): per-arch snapshot_noise cells, a draw_share sibling (#9823)

The Cake Gated DeltaProduct (GDP) kernel family has four decode routes, `decode_nh1` to `decode_nh4`, for n = 1 to 4 Householder updates per token, all with head sizes K = 128, V = 64 and fused q/k L2 normalization. The state pool is FP32, or FP16 stored with round to nearest even (RNE) or stochastic rounding (SR: `rand_seed`, `philox_rounds` 5 to 16, default 10). FP16 calls that store per-token snapshots can use snapshot-noise programs with shared-memory Philox noise.

This PR changes only which program serves some SR FP16 calls of `decode_nh3` (n = 3). Each new or re-routed sibling stores the same bits as the plain program it replaces; only the speed changes.

- Runtime-token-count program (T = 9 to 15): its snapshot-noise sibling now serves SR snapshot calls by architecture and CTAs per SM (B x HV / SM count):
  - SM100 and SM103: from 10 Philox rounds, but from 11 within (3, 4] CTAs per SM. Main served all from 10 rounds, so 10-round calls within (3, 4] now launch the plain program.
  - SM107: from 10 rounds up to 3 CTAs per SM and within (4, 124], from 11 above 124, from 16 within (3, 4]. Main served them only from 16 rounds, so calls at 10 to 15 rounds outside (3, 4] (above 124: 11 to 15) now launch the sibling.
- Split-V program, T = 1, B x HV <= 160: a new draw-share sibling computes each Philox draw of its store once and gives half of it to the partner lane by a shuffle. It serves SR calls from 5 rounds on `sm_100a`, `sm_103a` and `sm_107a`; RNE calls keep the plain program.

The baseline is the previous Cake version: the same call on FlashInfer main. Speedup is main time / this PR's time (above 1: this PR is faster). Over the shapes whose program changes, geomean (min..max):

- B200, 171 shapes (138 faster, 9 slower than main beyond noise): 1.049x (0.974x..1.145x). Runtime program at 10 rounds within (3, 4] CTAs per SM (91 shapes): 1.044x (0.974x..1.145x); `all` 1.106x (1.083x..1.145x), `holes` 1.072x (1.038x..1.125x), `last` 1.008x (0.974x..1.072x). Split-V (80): 1.054x (1.013x..1.134x); 1.029x at 5 rounds to 1.083x at 16.
- GB300, 164 shapes (147 faster, 1 slower): 1.075x (0.990x..1.164x). Runtime program, same cell (84 shapes): 1.061x (0.990x..1.164x); `all` 1.116x (1.087x..1.164x), `holes` 1.085x (1.050x..1.137x), `last` 1.023x (0.990x..1.086x). Split-V (80): 1.090x (1.046x..1.143x); 1.066x at 5 rounds to 1.116x at 16.
- VR200, 959 shapes (945 faster, 0 slower): 1.159x (0.997x..1.572x). Runtime program (879 shapes): 1.170x (0.997x..1.572x); up to 3 CTAs per SM 1.379x (1.219x..1.572x), (4, 124] 1.132x (0.997x..1.511x), above 124 1.104x (1.008x..1.275x); by rounds, 1.109x at 10 to 1.244x at 15. Split-V (80): 1.049x (1.007x..1.134x); 1.026x at 5 rounds to 1.076x at 16.

All slower shapes are 10-round `last` calls on SM100 / SM103 with T >= 12 and 3.03 to 3.24 CTAs per SM: 9 on B200 (0.974x to 0.989x) and 1 on GB300 (B 58, HV 8, T 15: 0.990x). The selection cells bound B x HV only by whole multiples of the SM count and do not see T or the snapshot pattern, and within (3, 4] CTAs per SM the plain program is faster on the `all` and `holes` calls. Shapes that launch the same program on both sides were timed as controls and are not listed: geomean 0.999x to 1.001x per set on every GPU, lowest 0.995x / 0.995x / 0.994x (B200 / GB300 / VR200), none slower beyond noise.

All other calls are unchanged, including FP32 and RNE calls, the other decode routes and the SM90 chunked varlen prefill programs; the family ships on `sm_90a`, `sm_100a`, `sm_103a` and `sm_107a`.

The tables below list all of these shapes, on NVIDIA B200 (`sm_100a`, 148 SMs) and NVIDIA GB300 (`sm_103a`, 152 SMs) with CUDA 13.4 and NVIDIA VR200 (`sm_107a`, 212 SMs) with CUDA 13.5. All shapes: FP16 state pool, K = 128, V = 64, n = 3. Times are CUPTI kernel times (cold L2, eager calls), the median of two runs (forward and reversed order) x 3 groups x 32 iterations, both sides on the same GPU per shape. Noise is the A/A spread per shape; a shape is faster or slower when its speedup differs from 1 by more than its noise.

- Cells: `main us / this PR us (speedup)`.
- `snapshots`: `all` = every token's state is stored; `holes` = every token's state with every third slot skipped (index -1); `last` = only the last token's state; `none` = no snapshot (final state only).
- `B x HV / SM`: CTAs per SM.
- `†`: slower than main beyond noise (bold ratio).
- `‡N`: shape timed twice; the table shows the slower measurement, and the line under the table gives the other.
- Columns: one per T (all at 10 rounds) in the B200 and GB300 runtime tables; one per Philox round count in the VR200 runtime and split-V tables.

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4

171 shapes: 138 faster than main beyond noise, 9 slower beyond noise (†), geomean 1.049x, min 0.974x, max 1.145x. Noise (A/A spread per shape): 1.0 % to 4.8 %.

Runtime-token-count program, T = 9 to 15, 10 Philox rounds. Cells: main us / this PR us (speedup).

| B | HV | B x HV / SM | snapshots | T = 9 | T = 10 | T = 11 | T = 12 | T = 13 | T = 14 | T = 15 |
|---|---|---|---|---|---|---|---|---|---|---|
| 56 | 8 | 3.03 | all | 56.82 / 51.90 (1.095) | 61.71 / 57.01 (1.083) | 67.84 / 62.02 (1.094) | 73.12 / 67.44 (1.084) | 78.70 / 72.26 (1.089) | 84.18 / 77.30 (1.089) | 89.66 / 82.79 (1.083) |
| 56 | 8 | 3.03 | holes | 54.86 / 51.26 (1.070) | 59.46 / 56.34 (1.055) | 64.53 / 61.65 (1.047) | 69.60 / 66.35 (1.049) | 74.80 / 71.90 (1.040) | 79.65 / 76.72 (1.038) | 85.13 / 81.86 (1.040) |
| 56 | 8 | 3.03 | last | 51.31 / 50.59 (1.014) ‡1 | 55.50 / 55.78 (0.995) ‡2 | 60.56 / 60.61 (0.999) ‡3 | 64.90 / 65.72 (**0.988**) † ‡4 | 69.48 / 70.78 (**0.982**) † ‡5 | 74.44 / 75.94 (**0.980**) † ‡6 | 78.75 / 80.86 (**0.974**) † ‡7 |
| 57 | 8 | 3.08 | last | 51.87 / 50.64 (1.024) | 55.81 / 55.70 (1.002) | 61.32 / 60.74 (1.010) | 65.64 / 65.81 (0.998) | 70.29 / 70.84 (0.992) | 74.88 / 76.06 (**0.984**) † | 79.50 / 80.86 (**0.983**) † |
| 58 | 8 | 3.14 | last | 52.16 / 50.66 (1.030) | 56.43 / 55.76 (1.012) | 61.23 / 60.88 (1.006) | 65.52 / 66.00 (0.993) | 70.50 / 70.89 (0.995) | 75.54 / 76.10 (0.993) | 79.89 / 81.01 (**0.986**) † |
| 59 | 8 | 3.19 | last | 52.54 / 50.77 (1.035) | 56.46 / 55.89 (1.010) | 61.68 / 60.77 (1.015) | 66.05 / 65.96 (1.001) | 70.83 / 70.94 (0.999) | 75.53 / 76.07 (0.993) | 80.13 / 81.10 (**0.988**) † |
| 60 | 8 | 3.24 | last | 52.49 / 50.82 (1.033) | 56.70 / 55.94 (1.014) | 61.78 / 60.86 (1.015) | 66.28 / 66.10 (1.003) | 71.19 / 70.98 (1.003) | 75.52 / 76.35 (**0.989**) † | 80.46 / 81.18 (0.991) |
| 65 | 8 | 3.51 | all | 58.45 / 52.98 (1.103) | 63.89 / 58.03 (1.101) | 69.71 / 63.14 (1.104) | 75.18 / 68.40 (1.099) | 80.90 / 73.69 (1.098) | 85.94 / 78.76 (1.091) | 91.75 / 83.97 (1.093) |
| 65 | 8 | 3.51 | holes | 56.54 / 52.11 (1.085) | 61.02 / 57.05 (1.070) | 66.84 / 62.38 (1.071) | 71.50 / 67.31 (1.062) | 77.17 / 72.43 (1.065) | 82.13 / 77.70 (1.057) | 87.84 / 82.75 (1.062) |
| 65 | 8 | 3.51 | last | 53.31 / 51.13 (1.043) | 57.62 / 56.16 (1.026) | 62.70 / 61.22 (1.024) | 67.01 / 66.58 (1.006) | 71.95 / 71.31 (1.009) | 76.48 / 76.58 (0.999) | 81.31 / 81.44 (0.998) |
| 74 | 8 | 4.00 | all | 61.02 / 53.30 (1.145) | 66.61 / 58.50 (1.139) | 72.59 / 63.54 (1.143) | 77.71 / 69.04 (1.126) | 83.71 / 74.26 (1.127) | 88.80 / 79.26 (1.120) | 94.92 / 84.59 (1.122) |
| 74 | 8 | 4.00 | holes | 59.10 / 52.54 (1.125) | 63.77 / 57.70 (1.105) | 69.43 / 62.86 (1.105) | 74.51 / 67.83 (1.099) | 80.36 / 73.16 (1.098) | 84.22 / 78.21 (1.077) | 91.26 / 83.42 (1.094) |
| 74 | 8 | 4.00 | last | 55.25 / 51.55 (1.072) | 59.30 / 56.58 (1.048) | 64.58 / 61.68 (1.047) | 68.62 / 66.96 (1.025) | 74.20 / 71.81 (1.033) | 78.18 / 77.09 (1.014) | 83.05 / 81.95 (1.013) |

Split-V program, T = 1, by Philox rounds. Cells: main us / this PR us (speedup).

| B | HV | snapshots | 5 rounds | 7 rounds | 10 rounds | 13 rounds | 16 rounds |
|---|---|---|---|---|---|---|---|
| 1 | 1 | all | 3.63 / 3.57 (1.018) | 3.66 / 3.58 (1.022) | 3.74 / 3.64 (1.029) | 3.81 / 3.70 (1.029) | 3.87 / 3.73 (1.039) |
| 1 | 1 | none | 3.34 / 3.25 (1.029) | 3.38 / 3.26 (1.034) | 3.44 / 3.31 (1.038) | 3.50 / 3.36 (1.043) | 3.57 / 3.41 (1.047) |
| 1 | 10 | all | 3.73 / 3.68 (1.013) | 3.78 / 3.71 (1.017) | 3.86 / 3.74 (1.032) | 3.92 / 3.80 (1.032) | 3.98 / 3.82 (1.042) |
| 1 | 10 | none | 3.42 / 3.36 (1.019) | 3.46 / 3.41 (1.014) | 3.52 / 3.44 (1.023) | 3.58 / 3.47 (1.032) | 3.66 / 3.54 (1.036) |
| 1 | 20 | all | 3.81 / 3.74 (1.017) | 3.86 / 3.78 (1.021) | 3.94 / 3.84 (1.027) | 4.06 / 3.89 (1.045) | 4.16 / 3.94 (1.057) |
| 1 | 20 | none | 3.50 / 3.44 (1.019) | 3.54 / 3.47 (1.018) | 3.62 / 3.54 (1.023) | 3.73 / 3.60 (1.035) | 3.82 / 3.63 (1.053) |
| 1 | 24 | all | 3.87 / 3.78 (1.025) | 3.92 / 3.82 (1.025) | 4.03 / 3.87 (1.041) | 4.11 / 3.94 (1.045) | 4.23 / 4.01 (1.056) |
| 1 | 24 | none | 3.60 / 3.52 (1.023) | 3.68 / 3.57 (1.031) | 3.74 / 3.63 (1.031) | 3.84 / 3.68 (1.044) | 3.94 / 3.76 (1.047) |
| 1 | 80 | all | 4.32 / 4.21 (1.027) | 4.48 / 4.30 (1.041) | 4.71 / 4.42 (1.067) | 4.96 / 4.56 (1.088) | 5.17 / 4.70 (1.099) |
| 1 | 80 | none | 4.19 / 4.06 (1.034) | 4.34 / 4.14 (1.046) | 4.53 / 4.26 (1.064) | 4.74 / 4.38 (1.080) | 4.94 / 4.53 (1.092) |
| 2 | 80 | all | 5.34 / 5.15 (1.037) | 5.60 / 5.31 (1.054) | 5.98 / 5.52 (1.084) | 6.37 / 5.74 (1.109) | 6.75 / 5.99 (1.127) |
| 2 | 80 | none | 5.22 / 5.02 (1.038) | 5.47 / 5.18 (1.056) | 5.86 / 5.38 (1.089) | 6.22 / 5.62 (1.107) | 6.59 / 5.84 (1.129) |
| 8 | 20 | all | 5.33 / 5.14 (1.037) | 5.58 / 5.30 (1.054) | 5.97 / 5.52 (1.081) | 6.35 / 5.74 (1.106) | 6.77 / 5.97 (1.134) |
| 8 | 20 | none | 5.23 / 5.02 (1.041) | 5.47 / 5.18 (1.056) | 5.86 / 5.41 (1.083) | 6.24 / 5.62 (1.110) | 6.59 / 5.86 (1.126) |
| 16 | 10 | all | 5.34 / 5.15 (1.037) | 5.60 / 5.31 (1.054) | 5.97 / 5.54 (1.078) | 6.37 / 5.75 (1.107) | 6.75 / 6.00 (1.125) |
| 16 | 10 | none | 5.21 / 4.99 (1.045) | 5.46 / 5.15 (1.059) | 5.82 / 5.36 (1.087) | 6.20 / 5.60 (1.107) | 6.58 / 5.82 (1.129) |

Timed twice (the table shows the slower measurement): ‡1 the other: 51.26 / 50.51 (1.015); ‡2 the other: 55.54 / 55.52 (1.000); ‡3 the other: 60.72 / 60.64 (1.001); ‡4 the other: 65.22 / 65.57 (0.995); ‡5 the other: 69.79 / 70.80 (0.986); ‡6 the other: 74.42 / 75.90 (0.981); ‡7 the other: 79.06 / 80.86 (0.978).

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4

164 shapes: 147 faster than main beyond noise, 1 slower beyond noise (†), geomean 1.075x, min 0.990x, max 1.164x. Noise (A/A spread per shape): 1.0 % to 9.0 %.

Runtime-token-count program, T = 9 to 15, 10 Philox rounds. Cells: main us / this PR us (speedup).

| B | HV | B x HV / SM | snapshots | T = 9 | T = 10 | T = 11 | T = 12 | T = 13 | T = 14 | T = 15 |
|---|---|---|---|---|---|---|---|---|---|---|
| 58 | 8 | 3.05 | all | 54.32 / 48.94 (1.110) | 58.53 / 53.66 (1.091) | 63.82 / 58.60 (1.089) | 69.13 / 63.37 (1.091) | 74.46 / 68.40 (1.089) | 79.65 / 73.13 (1.089) | 84.82 / 78.06 (1.087) |
| 58 | 8 | 3.05 | holes | 52.48 / 48.66 (1.078) | 56.45 / 52.77 (1.070) | 61.86 / 58.06 (1.065) | 66.14 / 62.43 (1.060) | 71.04 / 67.27 (1.056) | 75.97 / 72.32 (1.050) | 81.63 / 77.31 (1.056) |
| 58 | 8 | 3.05 | last | 49.52 / 47.71 (1.038) ‡1 | 52.84 / 52.05 (1.015) ‡2 | 58.11 / 57.25 (1.015) ‡3 | 61.94 / 61.58 (1.006) ‡4 | 66.86 / 66.69 (1.003) ‡5 | 70.67 / 71.20 (0.993) ‡6 | 75.55 / 76.32 (**0.990**) † ‡7 |
| 59 | 8 | 3.11 | last | 49.84 / 47.83 (1.042) | 53.17 / 52.16 (1.019) | 57.94 / 56.97 (1.017) | 62.83 / 61.98 (1.014) | 66.53 / 66.47 (1.001) | 71.91 / 71.50 (1.006) | 75.89 / 76.00 (0.999) |
| 60 | 8 | 3.16 | last | 49.98 / 47.73 (1.047) | 53.50 / 52.14 (1.026) | 58.26 / 57.09 (1.020) | 62.95 / 61.97 (1.016) | 66.94 / 66.59 (1.005) | 71.95 / 71.46 (1.007) | 75.76 / 76.27 (0.993) |
| 61 | 8 | 3.21 | last | 49.74 / 47.55 (1.046) | 53.98 / 52.46 (1.029) | 58.35 / 57.25 (1.019) | 62.92 / 62.15 (1.012) | 67.54 / 66.83 (1.010) | 72.26 / 71.70 (1.008) | 76.28 / 76.18 (1.001) |
| 67 | 8 | 3.53 | all | 55.95 / 49.76 (1.124) | 60.38 / 54.34 (1.111) | 66.58 / 59.37 (1.121) | 71.29 / 64.21 (1.110) | 76.19 / 68.86 (1.106) | 81.22 / 73.63 (1.103) | 87.16 / 78.96 (1.104) |
| 67 | 8 | 3.53 | holes | 53.94 / 49.04 (1.100) | 57.71 / 53.28 (1.083) | 63.84 / 58.54 (1.091) | 68.06 / 63.22 (1.077) | 72.80 / 67.86 (1.073) | 77.63 / 72.61 (1.069) | 83.39 / 78.04 (1.069) |
| 67 | 8 | 3.53 | last | 50.26 / 47.74 (1.053) | 54.35 / 52.38 (1.038) | 59.66 / 57.43 (1.039) | 63.91 / 62.17 (1.028) | 67.87 / 66.66 (1.018) | 73.01 / 71.79 (1.017) | 77.55 / 76.78 (1.010) |
| 76 | 8 | 4.00 | all | 58.01 / 49.84 (1.164) | 62.64 / 54.58 (1.148) | 68.69 / 59.58 (1.153) | 72.99 / 64.48 (1.132) | 79.79 / 69.52 (1.148) | 83.26 / 73.84 (1.127) | 89.89 / 79.18 (1.135) |
| 76 | 8 | 4.00 | holes | 56.08 / 49.33 (1.137) | 60.00 / 53.60 (1.119) | 66.19 / 58.90 (1.124) | 70.69 / 63.42 (1.115) | 75.66 / 68.17 (1.110) | 79.65 / 72.94 (1.092) | 86.52 / 78.19 (1.107) |
| 76 | 8 | 4.00 | last | 52.26 / 48.13 (1.086) | 55.96 / 52.48 (1.066) | 60.94 / 57.41 (1.062) | 65.23 / 62.35 (1.046) | 69.82 / 66.88 (1.044) | 73.71 / 71.66 (1.029) | 78.82 / 76.45 (1.031) |

Split-V program, T = 1, by Philox rounds. Cells: main us / this PR us (speedup).

| B | HV | snapshots | 5 rounds | 7 rounds | 10 rounds | 13 rounds | 16 rounds |
|---|---|---|---|---|---|---|---|
| 1 | 1 | all | 3.46 / 3.15 (1.096) | 3.47 / 3.18 (1.090) | 3.54 / 3.22 (1.099) | 3.62 / 3.28 (1.102) | 3.68 / 3.30 (1.116) |
| 1 | 1 | none | 3.17 / 2.99 (1.059) | 3.20 / 3.02 (1.061) | 3.24 / 3.09 (1.049) | 3.31 / 3.10 (1.067) | 3.36 / 3.15 (1.066) |
| 1 | 10 | all | 3.63 / 3.37 (1.078) | 3.66 / 3.39 (1.080) | 3.73 / 3.42 (1.089) | 3.80 / 3.47 (1.094) | 3.86 / 3.52 (1.095) |
| 1 | 10 | none | 3.30 / 3.04 (1.085) | 3.34 / 3.07 (1.087) | 3.41 / 3.10 (1.099) | 3.46 / 3.14 (1.105) | 3.50 / 3.20 (1.095) |
| 1 | 20 | all | 3.71 / 3.46 (1.072) | 3.76 / 3.49 (1.078) | 3.86 / 3.54 (1.091) | 3.92 / 3.58 (1.094) | 4.03 / 3.65 (1.105) |
| 1 | 20 | none | 3.41 / 3.23 (1.055) | 3.47 / 3.26 (1.064) | 3.52 / 3.30 (1.068) | 3.60 / 3.34 (1.077) | 3.66 / 3.41 (1.075) |
| 1 | 24 | all | 3.71 / 3.49 (1.064) | 3.79 / 3.52 (1.077) | 3.89 / 3.58 (1.085) | 3.97 / 3.65 (1.088) | 4.08 / 3.68 (1.109) |
| 1 | 24 | none | 3.44 / 3.18 (1.080) | 3.47 / 3.23 (1.074) | 3.58 / 3.26 (1.096) | 3.65 / 3.33 (1.096) | 3.76 / 3.39 (1.109) |
| 1 | 80 | all | 4.14 / 3.87 (1.070) | 4.29 / 3.95 (1.085) | 4.51 / 4.08 (1.106) | 4.70 / 4.19 (1.122) | 4.94 / 4.35 (1.136) |
| 1 | 80 | none | 4.05 / 3.71 (1.091) | 4.16 / 3.81 (1.092) | 4.35 / 3.90 (1.115) | 4.54 / 4.02 (1.131) | 4.72 / 4.14 (1.139) |
| 2 | 80 | all | 5.06 / 4.83 (1.046) | 5.30 / 4.99 (1.061) | 5.65 / 5.22 (1.083) | 6.00 / 5.42 (1.106) | 6.35 / 5.63 (1.128) |
| 2 | 80 | none | 4.98 / 4.74 (1.051) | 5.20 / 4.86 (1.069) | 5.52 / 5.06 (1.092) | 5.87 / 5.28 (1.112) | 6.21 / 5.47 (1.135) |
| 8 | 20 | all | 5.12 / 4.86 (1.053) | 5.34 / 5.02 (1.064) | 5.71 / 5.22 (1.095) | 6.05 / 5.42 (1.115) | 6.42 / 5.65 (1.136) |
| 8 | 20 | none | 5.01 / 4.74 (1.057) | 5.23 / 4.86 (1.076) | 5.58 / 5.06 (1.103) | 5.90 / 5.27 (1.120) | 6.26 / 5.47 (1.143) |
| 16 | 10 | all | 5.09 / 4.85 (1.050) | 5.31 / 5.01 (1.061) | 5.65 / 5.20 (1.086) | 6.00 / 5.42 (1.106) | 6.38 / 5.62 (1.135) |
| 16 | 10 | none | 4.96 / 4.69 (1.058) | 5.18 / 4.83 (1.073) | 5.50 / 5.04 (1.092) | 5.84 / 5.23 (1.116) | 6.19 / 5.45 (1.137) |

Timed twice (the table shows the slower measurement): ‡1 the other: 49.54 / 47.68 (1.039); ‡2 the other: 52.93 / 52.06 (1.017); ‡3 the other: 58.10 / 57.21 (1.016); ‡4 the other: 62.46 / 61.82 (1.010); ‡5 the other: 67.35 / 66.74 (1.009); ‡6 the other: 70.96 / 71.24 (0.996); ‡7 the other: 75.95 / 76.51 (0.993).

### NVIDIA VR200 (sm_107a, 212 SMs), CUDA 13.5

959 shapes: 945 faster than main beyond noise, 0 slower beyond noise (†), geomean 1.159x, min 0.997x, max 1.572x. Noise (A/A spread per shape): 1.0 % to 3.0 %.

Runtime-token-count program, T = 9 to 15, by Philox rounds. Cells: main us / this PR us (speedup).

| B | HV | B x HV / SM | T | snapshots | 10 rounds | 11 rounds | 12 rounds | 13 rounds | 14 rounds | 15 rounds |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 80 | 0.38 | 9 | all | 31.82 / 25.58 (1.244) | 32.62 / 25.66 (1.271) | 33.41 / 25.76 (1.297) | 34.22 / 25.82 (1.325) | 35.01 / 25.94 (1.350) | 35.83 / 26.02 (1.377) |
| 1 | 80 | 0.38 | 10 | all | 34.26 / 27.07 (1.265) | 35.12 / 27.15 (1.294) | 36.03 / 27.26 (1.322) | 36.91 / 27.33 (1.351) | 37.79 / 27.41 (1.379) | 38.67 / 27.50 (1.407) |
| 1 | 80 | 0.38 | 11 | all | 37.68 / 29.62 (1.272) | 38.63 / 29.70 (1.301) | 39.60 / 29.81 (1.329) | 40.58 / 29.89 (1.358) | 41.57 / 29.98 (1.387) | 42.53 / 30.05 (1.415) |
| 1 | 80 | 0.38 | 12 | all | 40.18 / 31.30 (1.284) | 41.26 / 31.38 (1.315) | 42.30 / 31.49 (1.343) | 43.38 / 31.55 (1.375) | 44.45 / 31.67 (1.403) | 45.51 / 31.74 (1.433) |
| 1 | 80 | 0.38 | 13 | all | 43.74 / 33.88 (1.291) | 44.88 / 33.98 (1.321) | 46.06 / 34.06 (1.352) | 47.20 / 34.11 (1.384) | 48.34 / 34.20 (1.414) | 49.55 / 34.32 (1.444) |
| 1 | 80 | 0.38 | 14 | all | 46.19 / 35.49 (1.302) | 47.41 / 35.55 (1.333) | 48.67 / 35.63 (1.366) | 49.92 / 35.73 (1.397) | 51.14 / 35.81 (1.428) | 52.40 / 35.91 (1.459) |
| 1 | 80 | 0.38 | 15 | all | 49.89 / 38.34 (1.301) | 51.20 / 38.42 (1.333) | 52.54 / 38.51 (1.364) | 53.87 / 38.56 (1.397) | 55.21 / 38.69 (1.427) | 56.53 / 38.77 (1.458) |
| 4 | 80 | 1.51 | 9 | all | 33.44 / 27.42 (1.219) | 34.26 / 27.48 (1.246) | 35.04 / 27.60 (1.270) | 35.84 / 27.66 (1.296) | 36.64 / 27.74 (1.321) | 37.44 / 27.84 (1.345) |
| 4 | 80 | 1.51 | 10 | all | 36.16 / 29.31 (1.234) | 37.01 / 29.39 (1.259) | 37.89 / 29.49 (1.285) | 38.78 / 29.55 (1.312) | 39.65 / 29.65 (1.337) | 40.58 / 29.73 (1.365) |
| 4 | 80 | 1.51 | 11 | all | 39.62 / 32.05 (1.236) | 40.62 / 32.14 (1.264) | 41.58 / 32.21 (1.291) | 42.55 / 32.30 (1.317) | 43.60 / 32.39 (1.346) | 44.53 / 32.47 (1.372) |
| 4 | 80 | 1.51 | 12 | all | 42.24 / 33.78 (1.251) | 43.28 / 33.86 (1.278) | 44.37 / 33.94 (1.307) | 45.42 / 34.03 (1.335) | 46.51 / 34.13 (1.363) | 47.57 / 34.21 (1.391) |
| 4 | 80 | 1.51 | 13 | all | 45.66 / 36.37 (1.256) | 46.82 / 36.46 (1.284) | 47.98 / 36.54 (1.313) | 49.14 / 36.60 (1.343) | 50.29 / 36.72 (1.369) | 51.44 / 36.78 (1.398) |
| 4 | 80 | 1.51 | 14 | all | 48.38 / 38.21 (1.266) | 49.63 / 38.26 (1.297) | 50.90 / 38.38 (1.326) | 52.13 / 38.47 (1.355) | 53.34 / 38.54 (1.384) | 54.61 / 38.62 (1.414) |
| 4 | 80 | 1.51 | 15 | all | 51.83 / 40.82 (1.270) | 53.17 / 40.91 (1.300) | 54.48 / 41.01 (1.329) | 55.83 / 41.07 (1.359) | 57.17 / 41.16 (1.389) | 58.48 / 41.25 (1.418) |
| 79 | 8 | 2.98 | 9 | all | 42.72 / 33.02 (1.294) | 44.21 / 33.18 (1.332) | 45.65 / 33.33 (1.370) | 47.14 / 33.49 (1.408) | 48.56 / 33.62 (1.445) | 50.03 / 33.75 (1.482) |
| 79 | 8 | 2.98 | 10 | all | 46.70 / 35.81 (1.304) | 48.31 / 35.94 (1.344) | 49.94 / 36.13 (1.382) | 51.54 / 36.26 (1.421) | 53.12 / 36.41 (1.459) | 54.77 / 36.50 (1.500) |
| 79 | 8 | 2.98 | 11 | all | 51.21 / 38.93 (1.315) | 52.96 / 39.10 (1.355) | 54.72 / 39.22 (1.395) | 56.53 / 39.36 (1.436) | 58.24 / 39.50 (1.474) | 60.01 / 39.65 (1.514) |
| 79 | 8 | 2.98 | 12 | all | 55.04 / 41.60 (1.323) | 57.01 / 41.74 (1.366) | 58.92 / 41.90 (1.406) | 60.94 / 42.06 (1.449) | 62.85 / 42.18 (1.490) | 64.86 / 42.30 (1.533) |
| 79 | 8 | 2.98 | 13 | all | 59.51 / 44.62 (1.333) | 61.62 / 44.78 (1.376) | 63.76 / 44.90 (1.420) | 65.86 / 45.06 (1.462) | 67.95 / 45.17 (1.504) | 70.06 / 45.28 (1.547) |
| 79 | 8 | 2.98 | 14 | all | 63.57 / 47.41 (1.341) | 65.82 / 47.57 (1.384) | 68.03 / 47.67 (1.427) | 70.31 / 47.86 (1.469) | 72.55 / 47.97 (1.512) | 74.85 / 48.10 (1.556) |
| 79 | 8 | 2.98 | 15 | all | 67.78 / 50.24 (1.349) | 70.22 / 50.34 (1.395) | 72.67 / 50.50 (1.439) | 75.17 / 50.59 (1.486) | 77.57 / 50.77 (1.528) | 80.02 / 50.90 (1.572) |
| 53 | 12 | 3.00 | 9 | all | 43.04 / 33.30 (1.293) | 44.53 / 33.43 (1.332) | 46.00 / 33.57 (1.370) | 47.50 / 33.70 (1.410) | 48.91 / 33.87 (1.444) | 50.36 / 33.95 (1.484) |
| 53 | 12 | 3.00 | 10 | all | 46.74 / 35.86 (1.303) | 48.32 / 36.02 (1.342) | 49.89 / 36.16 (1.380) | 51.52 / 36.27 (1.420) | 53.15 / 36.43 (1.459) | 54.83 / 36.55 (1.500) |
| 53 | 12 | 3.00 | 11 | all | 51.51 / 39.18 (1.314) | 53.28 / 39.33 (1.355) | 55.06 / 39.42 (1.397) | 56.86 / 39.58 (1.437) | 58.59 / 39.71 (1.475) | 60.35 / 39.84 (1.515) |
| 53 | 12 | 3.00 | 12 | all | 55.09 / 41.62 (1.324) | 57.09 / 41.74 (1.368) | 59.03 / 41.92 (1.408) | 61.04 / 42.05 (1.452) | 62.93 / 42.18 (1.492) | 64.90 / 42.32 (1.534) |
| 53 | 12 | 3.00 | 13 | all | 59.74 / 44.74 (1.335) | 61.84 / 44.91 (1.377) | 63.98 / 45.04 (1.421) | 66.08 / 45.17 (1.463) | 68.15 / 45.31 (1.504) | 70.28 / 45.41 (1.548) |
| 53 | 12 | 3.00 | 14 | all | 63.68 / 47.39 (1.344) | 65.92 / 47.52 (1.387) | 68.14 / 47.66 (1.430) | 70.43 / 47.83 (1.473) | 72.66 / 47.94 (1.516) | 74.96 / 48.10 (1.559) |
| 53 | 12 | 3.00 | 15 | all | 68.11 / 50.53 (1.348) | 70.56 / 50.67 (1.393) | 73.03 / 50.80 (1.438) | 75.50 / 50.91 (1.483) | 77.92 / 51.09 (1.525) | 80.32 / 51.20 (1.569) |
| 107 | 8 | 4.04 | 9 | all | 68.74 / 53.38 (1.288) | 70.58 / 53.56 (1.318) | 72.50 / 53.79 (1.348) | 74.35 / 53.97 (1.378) | 76.37 / 54.15 (1.410) | 78.29 / 54.30 (1.442) |
| 107 | 8 | 4.04 | 10 | all | 75.36 / 57.65 (1.307) | 77.31 / 57.83 (1.337) | 79.64 / 57.98 (1.374) | 81.76 / 58.19 (1.405) | 83.23 / 58.34 (1.427) | 85.25 / 58.54 (1.456) |
| 107 | 8 | 4.04 | 11 | all | 81.98 / 62.93 (1.303) | 84.26 / 63.05 (1.336) | 86.71 / 63.27 (1.371) | 89.07 / 63.44 (1.404) | 90.94 / 63.63 (1.429) | 93.36 / 63.83 (1.463) |
| 107 | 8 | 4.04 | 12 | all | 88.91 / 66.87 (1.329) | 91.40 / 66.99 (1.364) | 94.22 / 67.16 (1.403) | 96.72 / 67.38 (1.435) | 99.02 / 67.53 (1.466) | 100.99 / 67.70 (1.492) |
| 107 | 8 | 4.04 | 13 | all | 95.42 / 72.10 (1.324) | 98.03 / 72.24 (1.357) | 101.00 / 72.43 (1.394) | 103.76 / 72.65 (1.428) | 106.34 / 72.82 (1.460) | 108.94 / 73.01 (1.492) |
| 107 | 8 | 4.04 | 14 | all | 102.78 / 76.32 (1.347) | 105.73 / 76.51 (1.382) | 108.94 / 76.66 (1.421) | 111.99 / 76.83 (1.458) | 114.51 / 77.01 (1.487) | 116.68 / 77.22 (1.511) |
| 107 | 8 | 4.04 | 15 | all | 108.96 / 81.50 (1.337) | 112.03 / 81.71 (1.371) | 115.02 / 81.88 (1.405) | 118.11 / 82.06 (1.439) | 121.22 / 82.27 (1.473) | 124.53 / 82.42 (1.511) |
| 212 | 8 | 8.00 | 9 | all | 85.33 / 83.07 (1.027) | 88.34 / 83.33 (1.060) | 91.36 / 83.58 (1.093) | 94.24 / 83.79 (1.125) | 96.54 / 84.03 (1.149) | 99.49 / 84.29 (1.180) |
| 212 | 8 | 8.00 | 9 | holes | 84.21 / 80.21 (1.050) | 87.16 / 80.42 (1.084) | 89.99 / 80.64 (1.116) | 92.86 / 80.86 (1.148) | 95.54 / 81.13 (1.178) | 98.27 / 81.42 (1.207) |
| 212 | 8 | 8.00 | 9 | last | 80.22 / 74.56 (1.076) | 82.89 / 74.78 (1.108) | 85.59 / 75.01 (1.141) | 88.48 / 75.35 (1.174) | 91.23 / 75.66 (1.206) | 94.02 / 75.94 (1.238) |
| 212 | 8 | 8.00 | 10 | all | 93.17 / 89.50 (1.041) | 96.37 / 89.75 (1.074) | 99.76 / 89.98 (1.109) | 102.99 / 90.21 (1.142) | 105.52 / 90.42 (1.167) | 108.72 / 90.72 (1.198) |
| 212 | 8 | 8.00 | 11 | all | 102.14 / 97.70 (1.046) | 105.76 / 97.92 (1.080) | 109.37 / 98.11 (1.115) | 112.84 / 98.37 (1.147) | 115.57 / 98.62 (1.172) | 119.11 / 98.85 (1.205) |
| 212 | 8 | 8.00 | 12 | all | 110.08 / 104.50 (1.053) | 113.94 / 104.66 (1.089) | 117.86 / 104.91 (1.123) | 121.70 / 105.15 (1.157) | 124.67 / 105.38 (1.183) | 128.72 / 105.60 (1.219) |
| 212 | 8 | 8.00 | 12 | holes | 108.85 / 100.48 (1.083) | 112.51 / 100.71 (1.117) | 116.24 / 100.86 (1.152) | 119.86 / 101.12 (1.185) | 123.33 / 101.38 (1.216) | 127.06 / 101.60 (1.251) |
| 212 | 8 | 8.00 | 12 | last | 103.64 / 93.47 (1.109) | 107.25 / 93.65 (1.145) | 110.67 / 93.94 (1.178) | 114.70 / 94.21 (1.218) | 118.37 / 94.45 (1.253) | 121.95 / 94.68 (1.288) |
| 212 | 8 | 8.00 | 13 | all | 118.89 / 112.07 (1.061) | 123.08 / 112.32 (1.096) | 127.25 / 112.51 (1.131) | 131.43 / 112.75 (1.166) | 134.58 / 113.03 (1.191) | 138.96 / 113.20 (1.228) |
| 212 | 8 | 8.00 | 14 | all | 126.69 / 118.80 (1.066) | 131.19 / 119.10 (1.101) | 135.68 / 119.27 (1.138) | 140.23 / 119.52 (1.173) | 143.59 / 119.76 (1.199) | 148.21 / 119.97 (1.235) |
| 212 | 8 | 8.00 | 15 | all | 135.46 / 126.56 (1.070) | 140.31 / 126.78 (1.107) | 144.95 / 126.95 (1.142) | 149.73 / 127.19 (1.177) | 153.47 / 127.48 (1.204) | 158.54 / 127.69 (1.242) |
| 424 | 8 | 16.00 | 9 | all | 163.63 / 164.10 (0.997) | 168.59 / 164.47 (1.025) | 173.74 / 164.91 (1.054) | 178.75 / 165.31 (1.081) | 183.43 / 165.77 (1.107) | 188.30 / 166.22 (1.133) |
| 424 | 8 | 16.00 | 10 | all | 179.11 / 176.82 (1.013) | 184.62 / 177.22 (1.042) | 190.39 / 177.61 (1.072) | 195.89 / 178.11 (1.100) | 201.02 / 178.58 (1.126) | 206.56 / 179.02 (1.154) |
| 424 | 8 | 16.00 | 11 | all | 196.07 / 194.05 (1.010) | 202.27 / 194.34 (1.041) | 208.45 / 194.74 (1.070) | 214.64 / 195.14 (1.100) | 220.21 / 195.50 (1.126) | 226.24 / 195.92 (1.155) |
| 424 | 8 | 16.00 | 12 | all | 211.16 / 206.37 (1.023) | 217.71 / 206.74 (1.053) | 224.56 / 207.11 (1.084) | 231.25 / 207.51 (1.114) | 237.35 / 207.97 (1.141) | 244.04 / 208.45 (1.171) |
| 424 | 8 | 16.00 | 13 | all | 228.07 / 223.49 (1.020) | 235.35 / 223.75 (1.052) | 242.62 / 224.08 (1.083) | 249.81 / 224.48 (1.113) | 256.44 / 224.91 (1.140) | 263.83 / 225.29 (1.171) |
| 424 | 8 | 16.00 | 14 | all | 243.50 / 235.83 (1.032) | 251.23 / 236.16 (1.064) | 259.00 / 236.43 (1.095) | 266.75 / 236.84 (1.126) | 273.68 / 237.28 (1.153) | 281.54 / 237.71 (1.184) |
| 424 | 8 | 16.00 | 15 | all | 259.97 / 251.59 (1.033) | 268.32 / 251.86 (1.065) | 276.68 / 252.22 (1.097) | 284.91 / 252.50 (1.128) | 292.40 / 252.91 (1.156) | 300.90 / 253.30 (1.188) |
| 1140 | 8 | 43.02 | 9 | all | 421.17 / 412.25 (1.022) | 432.12 / 412.76 (1.047) | 443.17 / 413.37 (1.072) | 454.19 / 414.17 (1.097) | 465.87 / 415.05 (1.122) | 478.37 / 416.00 (1.150) |
| 1140 | 8 | 43.02 | 12 | all | 544.16 / 516.11 (1.054) | 558.39 / 516.50 (1.081) | 573.62 / 517.29 (1.109) | 589.62 / 518.25 (1.138) | 605.67 / 519.41 (1.166) | 622.47 / 520.52 (1.196) |
| 1140 | 8 | 43.02 | 15 | all | 672.18 / 631.26 (1.065) | 690.34 / 632.55 (1.091) | 709.19 / 633.82 (1.119) | 728.71 / 635.03 (1.147) | 748.53 / 636.25 (1.177) | 769.30 / 637.51 (1.207) |
| 1166 | 8 | 44.00 | 9 | all | 425.30 / 416.02 (1.022) | 436.50 / 417.05 (1.047) | 448.26 / 418.32 (1.072) | 459.71 / 419.54 (1.096) | 471.49 / 420.85 (1.120) | 484.01 / 422.23 (1.146) |
| 1166 | 8 | 44.00 | 12 | all | 548.86 / 523.93 (1.048) | 563.38 / 524.93 (1.073) | 579.01 / 526.08 (1.101) | 595.41 / 527.26 (1.129) | 612.04 / 528.50 (1.158) | 628.98 / 529.80 (1.187) |
| 1166 | 8 | 44.00 | 15 | all | 677.70 / 643.98 (1.052) | 696.36 / 645.58 (1.079) | 716.12 / 646.98 (1.107) | 736.34 / 648.31 (1.136) | 756.41 / 649.54 (1.165) | 778.07 / 650.94 (1.195) |
| 1458 | 8 | 55.02 | 9 | all | 530.18 / 520.80 (1.018) | 543.63 / 521.45 (1.042) | 557.37 / 522.42 (1.067) | 571.49 / 523.66 (1.091) | 586.46 / 525.06 (1.117) | 602.52 / 526.50 (1.144) |
| 1458 | 8 | 55.02 | 12 | all | 685.48 / 653.98 (1.048) | 703.06 / 654.79 (1.074) | 722.75 / 655.89 (1.102) | 743.46 / 657.32 (1.131) | 764.16 / 658.79 (1.160) | 785.60 / 660.27 (1.190) |
| 1458 | 8 | 55.02 | 15 | all | 847.13 / 802.72 (1.055) | 869.42 / 804.42 (1.081) | 893.48 / 806.24 (1.108) | 918.12 / 807.83 (1.137) | 943.69 / 809.27 (1.166) | 970.40 / 811.05 (1.196) |
| 1484 | 8 | 56.00 | 9 | all | 536.22 / 526.71 (1.018) | 549.90 / 528.17 (1.041) | 564.31 / 529.83 (1.065) | 578.72 / 531.51 (1.089) | 593.73 / 533.25 (1.113) | 609.52 / 534.96 (1.139) |
| 1484 | 8 | 56.00 | 12 | all | 690.54 / 661.56 (1.044) | 708.98 / 663.37 (1.069) | 729.18 / 665.31 (1.096) | 749.76 / 667.10 (1.124) | 771.28 / 668.72 (1.153) | 792.85 / 670.54 (1.182) |
| 1484 | 8 | 56.00 | 15 | all | 854.31 / 817.23 (1.045) | 877.47 / 819.11 (1.071) | 902.30 / 820.85 (1.099) | 928.23 / 822.65 (1.128) | 954.34 / 824.23 (1.158) | 981.79 / 825.95 (1.189) |
| 2544 | 8 | 96.00 | 9 | all | 900.41 / 895.93 (1.005) | 922.90 / 898.43 (1.027) | 946.66 / 901.13 (1.050) | 971.29 / 903.93 (1.075) | 997.52 / 906.67 (1.100) | 1024.42 / 909.36 (1.127) |
| 2544 | 8 | 96.00 | 9 | holes | 875.56 / 861.63 (1.016) | 898.61 / 864.24 (1.040) | 922.69 / 866.95 (1.064) | 947.88 / 869.61 (1.090) | 974.31 / 872.41 (1.117) | 1001.40 / 875.02 (1.144) |
| 2544 | 8 | 96.00 | 9 | last | 824.26 / 790.14 (1.043) | 848.23 / 792.87 (1.070) | 874.79 / 795.88 (1.099) | 901.85 / 798.79 (1.129) | 929.96 / 801.68 (1.160) | 959.04 / 804.73 (1.192) |
| 2544 | 8 | 96.00 | 12 | all | 1161.73 / 1126.74 (1.031) | 1193.29 / 1129.88 (1.056) | 1227.26 / 1133.07 (1.083) | 1262.45 / 1135.92 (1.111) | 1298.96 / 1138.65 (1.141) | 1336.21 / 1141.43 (1.171) |
| 2544 | 8 | 96.00 | 12 | holes | 1129.73 / 1087.02 (1.039) | 1161.49 / 1089.88 (1.066) | 1195.96 / 1092.72 (1.095) | 1231.49 / 1095.59 (1.124) | 1270.69 / 1098.44 (1.157) | 1311.76 / 1101.15 (1.191) |
| 2544 | 8 | 96.00 | 12 | last | 1061.43 / 994.52 (1.067) | 1095.06 / 997.58 (1.098) | 1132.29 / 1000.64 (1.132) | 1172.72 / 1003.68 (1.168) | 1214.93 / 1006.77 (1.207) | 1258.50 / 1009.72 (1.246) |
| 2544 | 8 | 96.00 | 15 | all | 1440.59 / 1389.05 (1.037) | 1479.18 / 1392.09 (1.063) | 1521.18 / 1395.07 (1.090) | 1564.53 / 1397.87 (1.119) | 1609.46 / 1400.55 (1.149) | 1656.46 / 1403.25 (1.180) |
| 2544 | 8 | 96.00 | 15 | holes | 1398.68 / 1336.57 (1.046) | 1438.66 / 1339.42 (1.074) | 1481.85 / 1342.19 (1.104) | 1528.47 / 1345.01 (1.136) | 1577.15 / 1347.78 (1.170) | 1628.33 / 1350.50 (1.206) |
| 2544 | 8 | 96.00 | 15 | last | 1314.70 / 1217.65 (1.080) | 1357.20 / 1220.62 (1.112) | 1405.66 / 1223.63 (1.149) | 1458.34 / 1226.64 (1.189) | 1510.56 / 1229.62 (1.228) | 1563.78 / 1232.61 (1.269) |
| 2955 | 8 | 111.51 | 9 | all | 1040.76 / 1038.00 (1.003) | 1066.28 / 1041.20 (1.024) | 1093.37 / 1044.52 (1.047) | 1122.15 / 1047.77 (1.071) | 1152.88 / 1050.89 (1.097) | 1185.48 / 1053.93 (1.125) |
| 2955 | 8 | 111.51 | 9 | holes | 1011.36 / 998.63 (1.013) | 1037.68 / 1001.73 (1.036) | 1064.65 / 1004.88 (1.060) | 1093.49 / 1007.95 (1.085) | 1125.01 / 1011.10 (1.113) | 1156.59 / 1014.11 (1.141) |
| 2955 | 8 | 111.51 | 9 | last | 951.88 / 915.56 (1.040) | 978.46 / 918.86 (1.065) | 1008.23 / 922.23 (1.093) | 1040.68 / 925.66 (1.124) | 1074.23 / 929.13 (1.156) | 1109.28 / 932.54 (1.190) |
| 2955 | 8 | 111.51 | 12 | all | 1342.23 / 1307.10 (1.027) | 1378.02 / 1310.86 (1.051) | 1418.00 / 1314.51 (1.079) | 1460.34 / 1317.74 (1.108) | 1503.47 / 1320.81 (1.138) | 1546.13 / 1324.01 (1.168) |
| 2955 | 8 | 111.51 | 12 | holes | 1304.74 / 1260.11 (1.035) | 1341.33 / 1263.44 (1.062) | 1381.25 / 1266.73 (1.090) | 1423.46 / 1269.94 (1.121) | 1469.77 / 1273.10 (1.155) | 1518.59 / 1276.17 (1.190) |
| 2955 | 8 | 111.51 | 12 | last | 1224.69 / 1153.45 (1.062) | 1265.38 / 1156.92 (1.094) | 1310.05 / 1160.42 (1.129) | 1358.74 / 1164.01 (1.167) | 1408.89 / 1167.58 (1.207) | 1460.18 / 1171.09 (1.247) |
| 2955 | 8 | 111.51 | 15 | all | 1665.75 / 1611.86 (1.033) | 1709.41 / 1615.33 (1.058) | 1757.93 / 1618.76 (1.086) | 1808.65 / 1621.93 (1.115) | 1860.06 / 1625.08 (1.145) | 1914.36 / 1627.88 (1.176) |
| 2955 | 8 | 111.51 | 15 | holes | 1615.13 / 1548.56 (1.043) | 1660.58 / 1551.83 (1.070) | 1710.43 / 1554.91 (1.100) | 1764.93 / 1558.17 (1.133) | 1822.41 / 1561.24 (1.167) | 1882.77 / 1564.32 (1.204) |
| 2955 | 8 | 111.51 | 15 | last | 1518.75 / 1412.31 (1.075) | 1570.31 / 1415.77 (1.109) | 1628.43 / 1419.19 (1.147) | 1690.44 / 1422.72 (1.188) | 1752.57 / 1426.29 (1.229) | 1812.13 / 1429.70 (1.268) |
| 2968 | 8 | 112.00 | 9 | all | 1045.64 / 1041.88 (1.004) | 1071.57 / 1045.20 (1.025) | 1099.04 / 1048.65 (1.048) | 1128.12 / 1051.92 (1.072) | 1158.57 / 1055.11 (1.098) | 1190.19 / 1058.19 (1.125) |
| 2968 | 8 | 112.00 | 9 | holes | 1016.52 / 1002.35 (1.014) | 1043.28 / 1005.47 (1.038) | 1071.00 / 1008.60 (1.062) | 1100.49 / 1011.75 (1.088) | 1131.52 / 1014.92 (1.115) | 1163.21 / 1018.03 (1.143) |
| 2968 | 8 | 112.00 | 9 | last | 956.63 / 919.13 (1.041) | 984.43 / 922.49 (1.067) | 1015.47 / 925.87 (1.097) | 1048.18 / 929.29 (1.128) | 1081.24 / 932.74 (1.159) | 1114.90 / 936.32 (1.191) |
| 2968 | 8 | 112.00 | 12 | all | 1349.01 / 1312.39 (1.028) | 1385.38 / 1316.02 (1.053) | 1425.38 / 1319.72 (1.080) | 1466.63 / 1323.21 (1.108) | 1509.11 / 1326.26 (1.138) | 1552.31 / 1329.37 (1.168) |
| 2968 | 8 | 112.00 | 12 | holes | 1311.58 / 1265.05 (1.037) | 1348.82 / 1268.41 (1.063) | 1389.33 / 1271.73 (1.093) | 1431.14 / 1275.01 (1.123) | 1476.42 / 1278.28 (1.155) | 1524.31 / 1281.31 (1.190) |
| 2968 | 8 | 112.00 | 12 | last | 1233.35 / 1159.09 (1.064) | 1273.88 / 1162.57 (1.096) | 1317.07 / 1166.25 (1.129) | 1363.63 / 1169.73 (1.166) | 1413.62 / 1173.26 (1.205) | 1464.87 / 1176.86 (1.245) |
| 2968 | 8 | 112.00 | 15 | all | 1674.22 / 1618.38 (1.034) | 1718.69 / 1621.79 (1.060) | 1767.50 / 1625.21 (1.088) | 1818.01 / 1628.57 (1.116) | 1869.99 / 1631.61 (1.146) | 1925.10 / 1634.72 (1.178) |
| 2968 | 8 | 112.00 | 15 | holes | 1624.60 / 1556.45 (1.044) | 1671.07 / 1559.73 (1.071) | 1721.62 / 1563.06 (1.101) | 1776.02 / 1566.23 (1.134) | 1832.86 / 1569.46 (1.168) | 1892.82 / 1572.63 (1.204) |
| 2968 | 8 | 112.00 | 15 | last | 1528.57 / 1417.85 (1.078) | 1578.29 / 1421.38 (1.110) | 1634.77 / 1424.78 (1.147) | 1696.44 / 1428.31 (1.188) | 1757.88 / 1431.83 (1.228) | 1820.28 / 1435.21 (1.268) |
| 3180 | 8 | 120.00 | 9 | all | 1118.00 / 1116.43 (1.001) | 1145.93 / 1119.82 (1.023) | 1175.23 / 1123.42 (1.046) | 1206.25 / 1126.76 (1.071) | 1239.32 / 1130.20 (1.097) | 1273.10 / 1133.38 (1.123) |
| 3180 | 8 | 120.00 | 9 | holes | 1086.50 / 1073.21 (1.012) | 1114.77 / 1076.45 (1.036) | 1144.62 / 1079.79 (1.060) | 1176.53 / 1083.21 (1.086) | 1209.26 / 1086.55 (1.113) | 1243.78 / 1089.90 (1.141) |
| 3180 | 8 | 120.00 | 9 | last | 1022.91 / 984.32 (1.039) | 1052.62 / 987.96 (1.065) | 1085.80 / 991.48 (1.095) | 1121.09 / 995.21 (1.127) | 1156.93 / 998.91 (1.158) | 1193.06 / 1002.62 (1.190) |
| 3180 | 8 | 120.00 | 12 | all | 1443.59 / 1405.39 (1.027) | 1482.80 / 1409.43 (1.052) | 1525.80 / 1413.35 (1.080) | 1569.94 / 1416.90 (1.108) | 1615.42 / 1420.18 (1.137) | 1661.38 / 1423.38 (1.167) |
| 3180 | 8 | 120.00 | 12 | holes | 1402.22 / 1354.27 (1.035) | 1442.42 / 1357.89 (1.062) | 1485.23 / 1361.41 (1.091) | 1529.99 / 1364.80 (1.121) | 1579.14 / 1368.26 (1.154) | 1630.84 / 1371.51 (1.189) |
| 3180 | 8 | 120.00 | 12 | last | 1318.47 / 1241.04 (1.062) | 1362.24 / 1244.82 (1.094) | 1408.83 / 1248.70 (1.128) | 1458.71 / 1252.53 (1.165) | 1512.34 / 1256.24 (1.204) | 1567.23 / 1260.10 (1.244) |
| 3180 | 8 | 120.00 | 15 | all | 1789.60 / 1729.82 (1.035) | 1837.09 / 1733.68 (1.060) | 1889.44 / 1737.24 (1.088) | 1943.76 / 1740.95 (1.117) | 1998.92 / 1744.20 (1.146) | 2058.30 / 1747.37 (1.178) |
| 3180 | 8 | 120.00 | 15 | holes | 1738.35 / 1667.08 (1.043) | 1788.00 / 1670.60 (1.070) | 1842.10 / 1674.12 (1.100) | 1900.53 / 1677.60 (1.133) | 1961.11 / 1681.01 (1.167) | 2025.58 / 1684.42 (1.202) |
| 3180 | 8 | 120.00 | 15 | last | 1635.61 / 1517.87 (1.078) | 1689.10 / 1521.50 (1.110) | 1749.64 / 1525.36 (1.147) | 1815.96 / 1529.07 (1.188) | 1881.72 / 1532.87 (1.228) | 1948.99 / 1536.57 (1.268) |
| 3273 | 8 | 123.51 | 9 | all | 1149.60 / 1148.64 (1.001) | 1177.88 / 1152.11 (1.022) | 1208.00 / 1155.83 (1.045) | 1239.81 / 1159.29 (1.069) | 1274.24 / 1162.65 (1.096) | 1310.02 / 1166.01 (1.123) |
| 3273 | 8 | 123.51 | 9 | holes | 1116.85 / 1103.16 (1.012) | 1145.76 / 1106.70 (1.035) | 1175.69 / 1110.14 (1.059) | 1207.46 / 1113.67 (1.084) | 1242.26 / 1117.15 (1.112) | 1277.38 / 1120.65 (1.140) |
| 3273 | 8 | 123.51 | 9 | last | 1051.52 / 1012.57 (1.038) | 1080.90 / 1016.24 (1.064) | 1113.95 / 1019.84 (1.092) | 1149.85 / 1023.63 (1.123) | 1187.01 / 1027.40 (1.155) | 1225.80 / 1031.22 (1.189) |
| 3273 | 8 | 123.51 | 12 | all | 1484.23 / 1447.15 (1.026) | 1523.89 / 1451.21 (1.050) | 1568.55 / 1455.22 (1.078) | 1615.47 / 1458.82 (1.107) | 1662.58 / 1462.16 (1.137) | 1710.06 / 1465.48 (1.167) |
| 3273 | 8 | 123.51 | 12 | holes | 1440.34 / 1393.31 (1.034) | 1481.31 / 1397.05 (1.060) | 1525.55 / 1400.74 (1.089) | 1571.98 / 1404.44 (1.119) | 1623.90 / 1407.96 (1.153) | 1677.72 / 1411.41 (1.189) |
| 3273 | 8 | 123.51 | 12 | last | 1353.14 / 1275.45 (1.061) | 1398.11 / 1279.35 (1.093) | 1447.79 / 1283.30 (1.128) | 1501.48 / 1287.26 (1.166) | 1556.99 / 1291.18 (1.206) | 1613.59 / 1295.11 (1.246) |
| 3273 | 8 | 123.51 | 15 | all | 1839.86 / 1783.03 (1.032) | 1888.02 / 1786.81 (1.057) | 1941.70 / 1790.57 (1.084) | 1998.24 / 1794.19 (1.114) | 2054.70 / 1797.39 (1.143) | 2115.40 / 1800.72 (1.175) |
| 3273 | 8 | 123.51 | 15 | holes | 1784.88 / 1715.29 (1.041) | 1835.37 / 1718.88 (1.068) | 1890.65 / 1722.53 (1.098) | 1950.69 / 1725.86 (1.130) | 2015.15 / 1729.33 (1.165) | 2081.34 / 1732.81 (1.201) |
| 3273 | 8 | 123.51 | 15 | last | 1677.86 / 1562.10 (1.074) | 1735.29 / 1565.86 (1.108) | 1799.49 / 1569.75 (1.146) | 1868.17 / 1573.62 (1.187) | 1937.49 / 1577.46 (1.228) | 2003.18 / 1581.39 (1.267) |
| 3286 | 8 | 124.00 | 9 | all | 1154.94 / 1153.84 (1.001) | 1183.39 / 1157.43 (1.022) | 1213.97 / 1160.89 (1.046) | 1246.02 / 1164.46 (1.070) | 1279.89 / 1167.74 (1.096) | 1315.06 / 1171.15 (1.123) |
| 3286 | 8 | 124.00 | 9 | holes | 1121.61 / 1108.17 (1.012) | 1150.70 / 1111.68 (1.035) | 1181.55 / 1115.18 (1.060) | 1214.43 / 1118.70 (1.086) | 1248.43 / 1122.14 (1.113) | 1284.16 / 1125.61 (1.141) |
| 3286 | 8 | 124.00 | 9 | last | 1055.58 / 1015.87 (1.039) | 1086.50 / 1019.56 (1.066) | 1120.58 / 1023.32 (1.095) | 1156.96 / 1027.21 (1.126) | 1194.33 / 1030.98 (1.158) | 1231.91 / 1034.89 (1.190) |
| 3286 | 8 | 124.00 | 12 | all | 1490.81 / 1452.85 (1.026) | 1530.75 / 1456.71 (1.051) | 1575.19 / 1460.65 (1.078) | 1620.87 / 1464.39 (1.107) | 1667.70 / 1467.71 (1.136) | 1715.62 / 1471.20 (1.166) |
| 3286 | 8 | 124.00 | 12 | holes | 1447.55 / 1398.83 (1.035) | 1488.73 / 1402.55 (1.061) | 1533.31 / 1406.24 (1.090) | 1580.02 / 1409.74 (1.121) | 1630.60 / 1413.18 (1.154) | 1684.09 / 1416.62 (1.189) |
| 3286 | 8 | 124.00 | 12 | last | 1361.13 / 1280.96 (1.063) | 1406.84 / 1284.93 (1.095) | 1454.58 / 1288.82 (1.129) | 1506.37 / 1292.78 (1.165) | 1561.63 / 1296.63 (1.204) | 1618.36 / 1300.54 (1.244) |
| 3286 | 8 | 124.00 | 15 | all | 1849.44 / 1789.99 (1.033) | 1898.45 / 1793.92 (1.058) | 1952.53 / 1797.70 (1.086) | 2008.47 / 1801.56 (1.115) | 2065.73 / 1804.92 (1.145) | 2126.59 / 1808.01 (1.176) |
| 3286 | 8 | 124.00 | 15 | holes | 1793.50 / 1721.40 (1.042) | 1845.03 / 1724.95 (1.070) | 1900.98 / 1728.67 (1.100) | 1961.12 / 1732.23 (1.132) | 2024.73 / 1735.72 (1.167) | 2091.04 / 1739.08 (1.202) |
| 3286 | 8 | 124.00 | 15 | last | 1688.88 / 1568.10 (1.077) | 1744.41 / 1571.88 (1.110) | 1806.58 / 1575.79 (1.147) | 1875.05 / 1579.70 (1.187) | 1942.97 / 1583.52 (1.227) | 2012.40 / 1587.40 (1.268) |
| 3287 | 8 | 124.04 | 9 | all | - | 1184.00 / 1157.63 (1.023) | 1214.43 / 1161.12 (1.046) | 1246.35 / 1164.62 (1.070) | 1280.45 / 1167.93 (1.096) | 1315.38 / 1171.37 (1.123) |
| 3287 | 8 | 124.04 | 9 | holes | - | 1151.02 / 1111.99 (1.035) | 1182.00 / 1115.53 (1.060) | 1214.85 / 1119.01 (1.086) | 1249.38 / 1122.43 (1.113) | 1284.76 / 1125.90 (1.141) |
| 3287 | 8 | 124.04 | 9 | last | - | 1086.91 / 1020.46 (1.065) | 1121.45 / 1024.12 (1.095) | 1158.74 / 1028.03 (1.127) | 1197.31 / 1031.84 (1.160) | 1238.12 / 1035.63 (1.196) |
| 3287 | 8 | 124.04 | 12 | all | - | 1531.47 / 1456.60 (1.051) | 1575.84 / 1460.50 (1.079) | 1621.58 / 1464.34 (1.107) | 1667.78 / 1467.77 (1.136) | 1716.05 / 1471.01 (1.167) |
| 3287 | 8 | 124.04 | 15 | all | - | 1899.69 / 1794.71 (1.058) | 1953.56 / 1798.47 (1.086) | 2008.91 / 1802.01 (1.115) | 2066.54 / 1805.47 (1.145) | 2127.47 / 1808.73 (1.176) |
| 3287 | 8 | 124.04 | 15 | holes | - | 1847.09 / 1725.69 (1.070) | 1903.13 / 1729.40 (1.101) | 1963.44 / 1732.91 (1.133) | 2026.48 / 1736.39 (1.167) | 2092.94 / 1739.92 (1.203) |
| 3287 | 8 | 124.04 | 15 | last | - | 1752.85 / 1572.07 (1.115) | 1819.86 / 1575.92 (1.155) | 1887.32 / 1579.81 (1.195) | 1953.73 / 1583.63 (1.234) | 2023.46 / 1587.58 (1.275) |
| 3392 | 8 | 128.00 | 9 | all | - | 1220.83 / 1193.70 (1.023) | 1252.06 / 1197.51 (1.046) | 1285.36 / 1201.18 (1.070) | 1320.47 / 1204.59 (1.096) | 1356.56 / 1208.13 (1.123) |
| 3392 | 8 | 128.00 | 9 | holes | - | 1187.42 / 1147.01 (1.035) | 1219.00 / 1150.70 (1.059) | 1252.89 / 1154.25 (1.085) | 1288.86 / 1157.83 (1.113) | 1324.70 / 1161.36 (1.141) |
| 3392 | 8 | 128.00 | 9 | last | - | 1120.39 / 1052.42 (1.065) | 1155.57 / 1056.37 (1.094) | 1193.17 / 1060.29 (1.125) | 1232.05 / 1064.30 (1.158) | 1270.77 / 1068.30 (1.190) |
| 3392 | 8 | 128.00 | 12 | all | - | 1579.36 / 1502.85 (1.051) | 1624.90 / 1506.92 (1.078) | 1672.71 / 1510.71 (1.107) | 1720.31 / 1514.33 (1.136) | 1770.18 / 1517.64 (1.166) |
| 3392 | 8 | 128.00 | 15 | all | - | 1958.01 / 1851.64 (1.057) | 2014.17 / 1855.48 (1.085) | 2071.88 / 1859.29 (1.114) | 2130.93 / 1862.81 (1.144) | 2193.83 / 1865.99 (1.176) |
| 3392 | 8 | 128.00 | 15 | holes | - | 1903.96 / 1780.66 (1.069) | 1961.30 / 1784.29 (1.099) | 2023.37 / 1787.95 (1.132) | 2089.05 / 1791.54 (1.166) | 2157.37 / 1795.19 (1.202) |
| 3392 | 8 | 128.00 | 15 | last | - | 1798.65 / 1621.65 (1.109) | 1863.28 / 1625.73 (1.146) | 1933.83 / 1629.75 (1.187) | 2003.98 / 1633.72 (1.227) | 2075.76 / 1637.76 (1.267) |
| 5194 | 8 | 196.00 | 9 | all | - | 1851.29 / 1821.64 (1.016) | 1899.27 / 1827.35 (1.039) | 1950.58 / 1832.77 (1.064) | 2004.90 / 1838.01 (1.091) | 2060.51 / 1842.98 (1.118) |
| 5194 | 8 | 196.00 | 12 | all | - | 2397.48 / 2296.28 (1.044) | 2468.67 / 2302.31 (1.072) | 2542.35 / 2307.88 (1.102) | 2614.59 / 2312.86 (1.131) | 2689.89 / 2317.58 (1.161) |
| 5194 | 8 | 196.00 | 15 | all | - | 2974.02 / 2827.37 (1.052) | 3059.36 / 2833.36 (1.080) | 3147.33 / 2839.16 (1.109) | 3237.21 / 2844.09 (1.138) | 3333.69 / 2848.99 (1.170) |
| 6784 | 8 | 256.00 | 9 | all | - | 2408.28 / 2376.08 (1.014) | 2470.76 / 2383.56 (1.037) | 2537.55 / 2390.65 (1.061) | 2609.45 / 2397.30 (1.089) | 2681.35 / 2403.75 (1.115) |
| 6784 | 8 | 256.00 | 12 | all | - | 3118.81 / 2995.04 (1.041) | 3212.37 / 3002.88 (1.070) | 3308.24 / 3010.43 (1.099) | 3401.35 / 3016.69 (1.127) | 3499.73 / 3022.63 (1.158) |
| 6784 | 8 | 256.00 | 15 | all | - | 3869.35 / 3688.21 (1.049) | 3980.36 / 3695.82 (1.077) | 4095.18 / 3703.20 (1.106) | 4213.06 / 3709.88 (1.136) | 4338.56 / 3716.00 (1.167) |
| 10282 | 8 | 388.00 | 9 | all | - | 3633.00 / 3596.34 (1.010) | 3727.49 / 3607.36 (1.033) | 3828.57 / 3618.04 (1.058) | 3939.15 / 3627.69 (1.086) | 4047.70 / 3637.47 (1.113) |
| 10282 | 8 | 388.00 | 9 | holes | - | 3529.03 / 3449.60 (1.023) | 3624.47 / 3460.51 (1.047) | 3729.01 / 3471.51 (1.074) | 3837.49 / 3482.22 (1.102) | 3949.17 / 3492.76 (1.131) |
| 10282 | 8 | 388.00 | 9 | last | - | 3330.11 / 3161.85 (1.053) | 3436.57 / 3173.70 (1.083) | 3552.06 / 3185.43 (1.115) | 3673.52 / 3197.18 (1.149) | 3797.95 / 3209.21 (1.183) |
| 10282 | 8 | 388.00 | 12 | all | - | 4705.84 / 4534.40 (1.038) | 4846.80 / 4545.59 (1.066) | 4992.19 / 4556.39 (1.096) | 5137.18 / 4565.57 (1.125) | 5281.65 / 4574.37 (1.155) |
| 10282 | 8 | 388.00 | 15 | all | - | 5839.97 / 5583.43 (1.046) | 6008.25 / 5595.05 (1.074) | 6181.77 / 5606.11 (1.103) | 6360.50 / 5615.90 (1.133) | 6551.89 / 5625.55 (1.165) |
| 10282 | 8 | 388.00 | 15 | holes | - | 5674.99 / 5363.65 (1.058) | 5847.52 / 5374.78 (1.088) | 6037.02 / 5385.78 (1.121) | 6239.93 / 5396.34 (1.156) | 6447.59 / 5406.84 (1.192) |
| 10282 | 8 | 388.00 | 15 | last | - | 5371.32 / 4879.38 (1.101) | 5575.89 / 4891.43 (1.140) | 5786.44 / 4903.35 (1.180) | 6000.56 / 4915.32 (1.221) | 6212.47 / 4927.27 (1.261) |
| 10600 | 8 | 400.00 | 9 | all | - | 3744.36 / 3707.56 (1.010) | 3842.61 / 3718.89 (1.033) | 3947.03 / 3729.97 (1.058) | 4058.78 / 3740.12 (1.085) | 4172.08 / 3749.94 (1.113) |
| 10600 | 8 | 400.00 | 12 | all | - | 4850.47 / 4673.64 (1.038) | 4996.79 / 4685.65 (1.066) | 5146.72 / 4696.82 (1.096) | 5293.76 / 4706.07 (1.125) | 5445.07 / 4714.98 (1.155) |
| 10600 | 8 | 400.00 | 15 | all | - | 6020.02 / 5756.93 (1.046) | 6193.89 / 5768.92 (1.074) | 6374.00 / 5780.36 (1.103) | 6558.03 / 5790.44 (1.133) | 6754.05 / 5799.90 (1.165) |
| 14734 | 8 | 556.00 | 9 | all | - | 5191.09 / 5147.57 (1.008) | 5326.57 / 5163.65 (1.032) | 5473.21 / 5178.62 (1.057) | 5628.92 / 5192.43 (1.084) | 5787.47 / 5206.27 (1.112) |
| 14734 | 8 | 556.00 | 12 | all | - | 6725.84 / 6492.14 (1.036) | 6927.82 / 6509.47 (1.064) | 7136.69 / 6524.85 (1.094) | 7341.06 / 6537.84 (1.123) | 7551.67 / 6549.81 (1.153) |
| 14734 | 8 | 556.00 | 15 | all | - | 8349.56 / 7996.40 (1.044) | 8591.09 / 8013.51 (1.072) | 8841.78 / 8028.61 (1.101) | 9095.43 / 8042.53 (1.131) | 9369.33 / 8055.88 (1.163) |

Split-V program, T = 1, by Philox rounds. Cells: main us / this PR us (speedup).

| B | HV | snapshots | 5 rounds | 7 rounds | 10 rounds | 13 rounds | 16 rounds |
|---|---|---|---|---|---|---|---|
| 1 | 1 | all | 3.26 / 3.23 (1.010) | 3.30 / 3.23 (1.022) | 3.36 / 3.26 (1.029) | 3.41 / 3.31 (1.029) | 3.47 / 3.35 (1.038) |
| 1 | 1 | none | 2.99 / 2.93 (1.022) | 2.99 / 2.94 (1.016) | 3.07 / 3.00 (1.024) | 3.09 / 3.01 (1.027) | 3.15 / 3.06 (1.031) |
| 1 | 10 | all | 3.41 / 3.34 (1.019) | 3.44 / 3.35 (1.026) | 3.47 / 3.39 (1.024) | 3.54 / 3.44 (1.028) | 3.60 / 3.47 (1.037) |
| 1 | 10 | none | 3.07 / 3.01 (1.021) | 3.09 / 3.04 (1.016) | 3.14 / 3.07 (1.021) | 3.20 / 3.10 (1.031) | 3.25 / 3.14 (1.036) |
| 1 | 20 | all | 3.50 / 3.44 (1.019) | 3.53 / 3.47 (1.016) | 3.60 / 3.50 (1.027) | 3.65 / 3.55 (1.027) | 3.70 / 3.57 (1.036) |
| 1 | 20 | none | 3.20 / 3.14 (1.020) | 3.21 / 3.15 (1.018) | 3.26 / 3.18 (1.025) | 3.33 / 3.22 (1.035) | 3.38 / 3.26 (1.037) |
| 1 | 24 | all | 3.41 / 3.38 (1.007) | 3.44 / 3.39 (1.014) | 3.49 / 3.44 (1.014) | 3.57 / 3.47 (1.028) | 3.62 / 3.52 (1.027) |
| 1 | 24 | none | 3.22 / 3.18 (1.010) | 3.26 / 3.20 (1.020) | 3.31 / 3.23 (1.022) | 3.36 / 3.28 (1.024) | 3.42 / 3.31 (1.034) |
| 1 | 80 | all | 3.78 / 3.71 (1.017) | 3.86 / 3.79 (1.017) | 3.94 / 3.86 (1.021) | 4.08 / 3.90 (1.045) | 4.26 / 3.97 (1.073) |
| 1 | 80 | none | 3.37 / 3.30 (1.022) | 3.46 / 3.33 (1.038) | 3.57 / 3.39 (1.052) | 3.73 / 3.46 (1.079) | 3.90 / 3.55 (1.099) |
| 2 | 80 | all | 4.18 / 3.98 (1.050) | 4.34 / 4.06 (1.067) | 4.58 / 4.21 (1.089) | 4.85 / 4.35 (1.114) | 5.12 / 4.52 (1.133) |
| 2 | 80 | none | 4.13 / 3.95 (1.044) | 4.30 / 4.05 (1.061) | 4.56 / 4.21 (1.084) | 4.85 / 4.37 (1.110) | 5.14 / 4.53 (1.134) |
| 8 | 20 | all | 4.27 / 4.13 (1.035) | 4.42 / 4.19 (1.053) | 4.69 / 4.32 (1.085) | 4.93 / 4.46 (1.104) | 5.20 / 4.62 (1.125) |
| 8 | 20 | none | 4.18 / 4.00 (1.044) | 4.34 / 4.11 (1.054) | 4.59 / 4.24 (1.083) | 4.88 / 4.40 (1.109) | 5.15 / 4.56 (1.130) |
| 16 | 10 | all | 4.29 / 4.10 (1.047) | 4.42 / 4.18 (1.058) | 4.68 / 4.32 (1.083) | 4.94 / 4.46 (1.107) | 5.23 / 4.64 (1.128) |
| 16 | 10 | none | 4.05 / 3.90 (1.037) | 4.22 / 4.02 (1.052) | 4.50 / 4.16 (1.081) | 4.78 / 4.32 (1.107) | 5.07 / 4.49 (1.130) |

### [42bbaf1](https://github.com/flashinfer-ai/flashinfer/commit/42bbaf163d964ae360b7a19eab50d7a7edc1eb58)

- **作者**: eigen
- **时间**: 2026-11-21T03:16:25Z
- **提交信息**: perf(mla): one-split Cake MLA FP8 page-64 decode and new backend="auto" ranges (#9807)

Cake MLA decode (`trtllm_batch_decode_with_kv_cache_mla` with
`backend="cake"`) has three paged-KV variants for the DeepSeek MLA dims
(qk_nope 128, kv_lora_rank 512, qk_rope 64): BF16 at page size 32, BF16
at page size 64, and FP8 at page size 64. They handle q_len 1-2, with
tails for other shapes. This PR changes the FP8 page-64 variant. When
the work fills the GPU, the decode now runs as a single split: the
producer kernel writes the output and LSE itself and no reducer is
launched. "Fills the GPU" means 4 x query rows > SM count (from 38 rows
on B200 and 39 on GB300) or max_seq_len <= 256. Other sizes keep their
previous split count. The baseline is the previous Cake on FlashInfer
main `d91cc6c70`, which includes #9779. At FP8 page 64, batch 128, q_len
1, KV 1024, latency drops from 55.87 to 30.06 us on B200 (1.858x) and
from 52.58 to 28.32 us on GB300 (1.856x). On the FP8 page-64 shapes
whose split count changes, the speedup is 1.323x-1.858x on B200 and
1.321x-1.864x on GB300. On the shapes whose split is unchanged, it is
0.994x-1.003x on B200 (11 shapes) and 0.990x-1.003x on GB300 (8 shapes).

`backend="auto"` now offers Cake for the FP8 page-64 ranges where the
one-split decode is fastest. These are max_seq_len buckets 128/256 at
batch 16-63 for q_len 1 and batch 8-31 for q_len 2, plus bucket 1024 at
batch 32-63 for q_len 1 on B200. On these units, `backend="auto"` is
1.029x-1.302x faster on B200 (10 units) and 1.080x-1.318x faster on
GB300 (8 units), and per-call eager wall time drops on every unit. On
B200, `backend="auto"` also offers Cake for BF16 page 32, q_len 1,
max_seq_len bucket 4096, batch 128-255. At batch 128, KV 4096, this goes
from cute-dsl at 138.05 us to Cake at 132.30 us (1.058x). Elsewhere,
`backend="auto"` stays within run-to-run noise of main across the full
A/B (93 cases on B200, 94 on GB300).

The other Cake variants are BF16 paged KV at page sizes 32 and 64 and
the BF16 split-KV route for long, small batches; apart from the new BF16
page-32 `backend="auto"` range, their routes stay the same, and the
family ships on sm_100a (B200) and sm_103a (GB300).

All tables use NVIDIA B200 (sm_100a, 148 SMs) and NVIDIA GB300 (sm_103a,
152 SMs), CUDA 13.5 (nvcc 13.5 JIT) and torch 2.14.1+cu130. GPU time is
the CUPTI kernel span over CUDA-graph replay, with L2 flushed before
every iteration. Each value is the median of 6 tuned rounds, each round
in a separate process. The `backend="cake"` speedup is previous Cake /
this PR. The `backend="auto"` speedup is 1 / (median over rounds of this
PR / main).

**Table 1: owner shape list.**

| GPU | KV dtype | page size | batch | q_len | KV length | lengths |
previous Cake (us) | this PR (us) | speedup [backend="cake"] | main auto
runner | main auto (us) | PR auto runner | PR auto (us) | auto speedup |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B200 | BF16 | 32 | 1 | 1 | 16384 | uniform | 18.78 | 18.78 | 1.000x |
cute-dsl | 17.50 | cute-dsl | 17.41 | 1.005x |
| B200 | BF16 | 32 | 128 | 1 | 1024 | varied | 34.24 | 34.05 | 1.006x |
cake | 34.27 | cake/trtllm-gen | 34.45 | 0.995x |
| B200 | BF16 | 32 | 128 | 1 | 4096 | uniform | 134.00 | 130.62 | 1.026x
| cute-dsl | 138.05 | cake | 132.30 | 1.058x |
| B200 | BF16 | 64 | 8 | 1 | 1024 | varied | 13.82 | 13.82 | 1.000x |
cute-dsl | 13.79 | cute-dsl | 13.71 | 1.000x |
| B200 | FP8 | 64 | 8 | 1 | 1024 | varied | 11.57 | 11.57 | 1.000x |
cute-dsl | 11.98 | cute-dsl | 12.16 | 0.987x |
| B200 | FP8 | 64 | 32 | 1 | 4096 | varied | 24.66 | 24.66 | 1.000x |
cute-dsl | 27.76 | cute-dsl | 28.00 | 0.994x |
| B200 | FP8 | 64 | 128 | 1 | 1024 | uniform | 55.87 | 30.06 | 1.858x |
trtllm-gen | 29.89 | trtllm-gen | 29.94 | 0.998x |
| GB300 | BF16 | 32 | 1 | 1 | 16384 | uniform | 17.46 | 17.44 | 1.001x |
cute-dsl | 16.51 | cute-dsl | 16.52 | 0.998x |
| GB300 | BF16 | 32 | 128 | 1 | 1024 | varied | 33.12 | 33.07 | 1.001x |
cake | 33.09 | cake | 33.06 | 1.001x |
| GB300 | BF16 | 32 | 128 | 1 | 4096 | uniform | 119.12 | 119.02 |
1.001x | cake | 118.96 | cake | 119.01 | 1.000x |
| GB300 | BF16 | 64 | 8 | 1 | 1024 | varied | 12.06 | 12.05 | 1.001x |
cake | 12.00 | cake | 12.00 | 1.000x |
| GB300 | FP8 | 64 | 8 | 1 | 1024 | varied | 10.62 | 10.74 | 0.990x |
cute-dsl | 12.00 | cute-dsl | 11.90 | 1.000x |
| GB300 | FP8 | 64 | 32 | 1 | 4096 | varied | 23.12 | 23.22 | 0.996x |
cute-dsl | 24.94 | cute-dsl | 24.93 | 0.999x |
| GB300 | FP8 | 64 | 128 | 1 | 1024 | uniform | 52.58 | 28.32 | 1.856x |
trtllm-gen | 27.34 | trtllm-gen | 27.38 | 0.999x |

A runner shown as `a/b` means auto picked different runners across
rounds.

**Table 2: `backend="cake"`, other FP8 page-64 shapes whose split count
changes.** The FP8 batch 128, q_len 1, KV 1024 shape is in Table 1. The
trtllm-gen and cute-dsl columns give the other backends' times for the
same shape.

| GPU | batch | q_len | KV length | lengths | previous Cake (us) | this
PR (us) | speedup | trtllm-gen (us) | cute-dsl (us) |
|---|---|---|---|---|---|---|---|---|---|
| B200 | 64 | 2 | 1024 | uniform | 51.87 | 27.97 | 1.855x | 28.74 |
29.50 |
| B200 | 100 | 1 | 1024 | varied | 41.28 | 26.74 | 1.544x | 28.58 |
27.68 |
| B200 | 32 | 2 | 4096 | varied | 42.56 | 32.16 | 1.323x | 39.02 | 33.30
|
| GB300 | 64 | 2 | 1024 | uniform | 48.11 | 25.81 | 1.864x | 25.82 |
26.03 |
| GB300 | 100 | 1 | 1024 | varied | 38.70 | 25.15 | 1.539x | 26.14 |
25.14 |
| GB300 | 32 | 2 | 4096 | varied | 37.42 | 28.34 | 1.321x | 33.25 |
27.97 |

**Table 3: `backend="auto"`, newly offered FP8 page-64 units.** Eager is
the per-call wall time without CUDA graphs (median of rounds).

| GPU | batch | q_len | KV length | lengths | main runner | main (us) |
PR runner | this PR (us) | speedup | main eager (us) | PR eager (us) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| B200 | 16 | 1 | 128 | uniform | cute-dsl/trtllm-gen | 8.38 | cake |
8.03 | 1.044x | 80.87 | 41.97 |
| B200 | 63 | 1 | 128 | varied | cute-dsl/trtllm-gen | 11.33 | cake |
8.74 | 1.302x | 58.76 | 41.36 |
| B200 | 16 | 1 | 256 | uniform | trtllm-gen | 9.22 | cake | 8.96 |
1.029x | 63.77 | 41.16 |
| B200 | 63 | 1 | 256 | varied | trtllm-gen | 12.73 | cake | 10.21 |
1.247x | 58.31 | 41.01 |
| B200 | 32 | 1 | 1024 | uniform | cute-dsl/trtllm-gen | 18.94 | cake |
15.71 | 1.206x | 61.08 | 43.39 |
| B200 | 63 | 1 | 1024 | varied | cute-dsl/trtllm-gen | 18.16 | cake |
15.65 | 1.160x | 58.74 | 41.69 |
| B200 | 8 | 2 | 128 | uniform | trtllm-gen | 9.18 | cake | 8.10 |
1.134x | 59.00 | 41.13 |
| B200 | 31 | 2 | 128 | varied | cute-dsl/trtllm-gen | 9.76 | cake |
8.54 | 1.143x | 82.11 | 41.43 |
| B200 | 16 | 2 | 256 | uniform | trtllm-gen | 10.86 | cake | 9.18 |
1.183x | 59.23 | 40.98 |
| B200 | 31 | 2 | 256 | varied | trtllm-gen | 11.98 | cake | 9.86 |
1.215x | 58.68 | 41.87 |
| GB300 | 16 | 1 | 128 | uniform | cute-dsl/trtllm-gen | 8.80 | cake |
7.49 | 1.175x | 105.46 | 66.56 |
| GB300 | 63 | 1 | 128 | varied | trtllm-gen | 10.61 | cake | 8.13 |
1.305x | 102.20 | 64.60 |
| GB300 | 16 | 1 | 256 | uniform | trtllm-gen | 8.86 | cake | 8.19 |
1.082x | 102.44 | 64.76 |
| GB300 | 63 | 1 | 256 | varied | trtllm-gen | 11.81 | cake | 9.31 |
1.267x | 101.13 | 67.03 |
| GB300 | 8 | 2 | 128 | uniform | cute-dsl/trtllm-gen | 8.82 | cake |
7.50 | 1.171x | 102.96 | 65.00 |
| GB300 | 31 | 2 | 128 | varied | cute-dsl/trtllm-gen | 10.48 | cake |
7.95 | 1.318x | 101.65 | 64.92 |
| GB300 | 8 | 2 | 256 | uniform | trtllm-gen | 8.90 | cake | 8.22 |
1.080x | 102.82 | 68.00 |
| GB300 | 31 | 2 | 256 | varied | trtllm-gen | 11.49 | cake | 8.93 |
1.287x | 106.20 | 65.80 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* FP8 page-64 attention can now run with a single split, including in
graph-replay scenarios.
* Expanded automatic configuration coverage for selected BF16 and FP8
workloads.
* **Bug Fixes**
* Single-split attention skips the reduction step while retaining
normalized outputs.
* **Tests**
* Added coverage for single-split planning and execution across
additional workloads and device configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [91a12f6](https://github.com/flashinfer-ai/flashinfer/commit/91a12f6981d4b1b712355ad30af835e85e6747dd)

- **作者**: Zihao Ye
- **时间**: 2026-11-21T01:09:40Z
- **提交信息**: fix(windows): make Cake-generated kernels and the DCP all-to-all module build under MSVC hosts (#9711)

## Summary

Cake-generated CUDA kernels do not compile with nvcc under a Visual
Studio host (native Windows arm64). The generator assumes the GNU
toolchain and the LP64 data model. This PR fixes the checked-in sources,
refreshes the digests that pin them, and fixes the Windows-only defects
that sit behind the first compile error.

## Changes

### 1. Generated sources (mechanical rewrite)

| Pattern | Problem under MSVC | Fix | Sites |
| --- | --- | --- | --- |
| `#if defined(__CUDACC_RTC__)` / `typedef unsigned long uint64_t`
prologue | `unsigned long` is 32-bit and `<stdint.h>` already declares
`uint64_t`: `invalid redeclaration of type name "uint64_t"`, then
`static_assert(sizeof(uint64_t) == 8)` fails | condition becomes
`defined(__CUDACC_RTC__) \|\| defined(_MSC_VER)` | 3,285 in 3,264 files
|
| `__int128_t r; asm("ld.shared.b128 %0, [%1];" : "=q"(r) ...)` |
`__int128_t` is undefined in the MSVC host | under `#if
defined(_MSC_VER)` only: `uint64_t r[2]; asm("{ .reg .b128 b;
ld.shared.b128 b, [%2]; mov.b128 {%0, %1}, b; }" : "=l"(r[0]),
"=l"(r[1]) ...)`, one 128-bit load split into two 64-bit halves inside
the asm; the `#else` branch is the original text | 877 in 90 files |
| `reinterpret_cast<unsigned __int128*>` in `kimi_k3_tp12_tail` | same |
`cake_u128_t*`, declared at the head of the kernel's header tail under a
`CAKE_U128_T_DECLARED` guard: `unsigned __int128`, or a named 16-byte,
16-aligned struct under `_MSC_VER` (same stride) | 19 in 6 files |

Every rewrite is gated on `_MSC_VER`, so a Linux or NVRTC compile sees
the original source. `cake_qsa_nvfp4` is included (its declarations sit
outside the `#if __CUDA_ARCH__ == 1070` blocks and the loads are in both
branches). The unused `__int128_t` overload of `st_shared` in
`megamoe/detail/ptx.cuh` stays, under `#if !defined(_MSC_VER)`.

The same gated spelling belongs in the Cake generator (MR on the
internal flour repo), so a re-export reproduces this text.

### 2. Source digests (`chore(cake)` commit)

The rewrite changes file bytes, so the recorded sha256 values must
follow: 24 `build.json` manifests (4,009 sources, all verified against
the files), three `*_manifest.json` files and the digests pinned by
`tests/mamba/test_cake_ssd_combined.py`. Without this, `cake_build.py`
raises `does not match its build.json digest` (16 cases of
`test_gated_residual_rmsnorm.py` failed on it).

### 3. `__builtin_{add,sub,mul}_overflow` on an MSVC host

The generated host bindings (846 files, about 1,200 call sites) use the
GNU checked-arithmetic builtins. New
`include/flashinfer/windows_builtin_compat.h` defines them for an MSVC
host only, and `gen_jit_spec` pre-includes it on Windows (`nvcc
-include`). Same semantics (store the wrapped result, return true on
overflow); operands and result must be one integer type or the build
fails. Linux and clang hosts are untouched and no generated file
changes. Checked on MSVC arm64 against exact 64-bit arithmetic (2M
random operand pairs per operation for int32/uint32) and edge values for
int64/uint64/int32/uint32.

### 4. Windows-only defects exposed once the prologue compiles

- `tvm_ffi.cpp.load_inline(embed_cubin=...)` raises
`NotImplementedError: CUBIN embedding is not yet supported on Windows`.
New `jit/inline_cubin.load_inline_with_cubin` calls `cpp.load_inline`
unchanged on POSIX and, on Windows, builds the host shim through
`gen_jit_spec(embedded_cubin_factory=...)`, which embeds the cubins as
COFF objects. Used by `mamba/cake_ssd_combined`, `jit/cake_gdn`,
`jit/cake_fmha_request_ordered` and `kda_kernels/ptx/static_runtime`.
- JIT object names for modules named after a 64-hex digest repeat the
module name, so an object and its `.d` file reached 309 characters
(MAX_PATH is 260). On Windows, an object path over 230 characters is
renamed to `<stem[:32]>_<12 hex of a digest of the source path>`; other
names are unchanged.
- `kimi_k3_tp12_tail` and `kimi_k3_latent_moe` `_clear_cuda_last_error`:
`os.RTLD_NOLOAD` and `libcudart.so.N` do not exist on Windows
(`AttributeError`, and a silent no-op in `latent_moe`). Load
`cudart64_<major>.dll` by name there, which returns the copy the process
already holds; POSIX is unchanged. The test that plants a CUDA error and
checks the clear now passes.
- `cake_ulysses_backend/cake_backend.py`: `ctypes.CDLL(None)` raises
`TypeError` on Windows, which broke `tests/comm/conftest.py` at import.
Load `ucrtbase` there.
- `cudaAsyncOps.cuh`, `ll128Proto.cuh`: reopened `tensorrt_llm::kernels`
with a plain `namespace`, while `moeCommKernelsCommon.h` uses
`TRTLLM_NAMESPACE_BEGIN` (`tensorrt_llm::_v1::kernels`). GCC treats
these as one namespace; the MSVC-mode nvcc front end does not, so
`WARP_SIZE` and `UINT64_PER_128B_BLOCK` were undefined. Use the same
macros. Most other files in `csrc/nv_internal` still open the plain
form, so under `_MSC_VER` `config.h` leaves the inline ABI namespace out
and the macros open the same plain `tensorrt_llm` namespace (this fixes
the `kernels` ambiguity in `nvlink_one_sided_alltoall`).
- `jit/comm.py`: the `dcp_alltoall` helix sources omit `logger.cpp` and
`stringUtils.cpp`, so the Windows DLL link fails on `Logger::getLogger`
and `fmtstr_` (an ELF shared object defers them to load time). Add both,
as the other `nv_internal` modules do.

## Testing

Native Windows 11 arm64, GB300 (sm_103), CUDA 13.5, MSVC 14.52, torch
2.16.0.dev+cu135, main 855eece4e plus this PR.

| File | Result |
| --- | --- |
| `tests/comm/test_dcp_alltoall.py` | 29 passed |
| `tests/experimental/test_cake_mla_nvfp4_paged_decode.py` | 77 passed |
| `tests/mla/test_cake_kimi_k3_mla.py` | 136 passed, 2 skipped |
| `tests/model_optimizations/test_router_gemms.py` | 312 passed |
| `tests/attention/test_dcp_spec_balanced.py` | 237 passed |
| `tests/norm/test_gated_residual_rmsnorm.py` | 45 passed |
| `tests/gemm/test_cake_mm_fp4.py` | 166 passed, 18 skipped |
| `tests/experimental/test_cake_kimi_k3_tp12_tail.py` | 10 passed, 3
skipped |
| `tests/mamba/test_cake_ssd_combined.py` | full run: 691 passed, 2
skipped, 3 failed; the 3 pass when rerun after the test fix |
| `tests/kda/test_kda_prefill_plan_cache.py` | 80 passed |
| `tests/experimental/test_cake_qsa_nvfp4.py` and `_api.py` | 49 passed,
3 skipped; 19 passed |
| `tests/gdn/test_paged_state.py` | 102 passed, 18 skipped |

No failure remains in the files above. Two of them need a note:
`test_cake_ssd_combined.py` was run in full (691 passed, 3 failed) and
the 3 failures, tests that patched `cpp.load_inline`, were then run
again after the patch point moved and pass; the 25
`_ChainMapFoldUnavailable` failures of `test_kda_prefill_plan_cache.py`
disappeared together with the path-length failures, which suggests (I
did not check) they followed from the failed build.

`megamoe/detail/ptx.cuh` could not be exercised here (SM90 kernels; this
machine is sm103/sm120).

The Windows runs above were made before the rewrites were gated on
`_MSC_VER`. The MSVC branches hold the same text as then, but they have
not been rebuilt on Windows since.

Linux (GB300, CUDA 13.4): every rewritten kernel (95 translation units,
at sm_103a, sm_107a, sm_110a or sm_120a) compiles to the same PTX
(ignoring `.loc`/`.file`) and the same SASS as on main. `tests/cpu`
fails in exactly the cases it fails on main.
`tests/norm/test_cake_muse_spark_norm.py`,
`test_cake_mla_nvfp4_paged_decode.py` and
`test_cake_kimi_k3_tp12_tail.py`, built from an empty JIT cache, give
102 passed and 3 skipped. The compatibility header, the `config.h`
change and the object-name shortening apply only to MSVC or Windows. The
`cudaAsyncOps.cuh`/`ll128Proto.cuh` namespace change has no effect under
GCC, where a plain reopen already extends the inline `_v1::kernels`.

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4835
- **最后更新**: 2026-11-22T01:50:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34961
- **最后更新**: 2026-11-22T02:00:30Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

## 提交分析：`ed32672` — ci: add a workflow to pr post-release changes

### 1. 主要更新类型
CI/基础设施改进（非面向用户的功能变更），属于自动化流程新增，可归类为工程效能提升而非功能、修复或性能优化。

### 2. 关键变更点及与项目方向的关系
- 新增一个 GitHub Actions 工作流，用于在发布（release）后自动向相关 PR 推送/处理"发布后变更"（post-release changes），例如版本号回滚、`CHANGELOG`/版本占位符恢复、依赖版本约束更新等常见的 release 后置收尾工作。
- 提交信息包含两个阶段（"add a workflow" 与 "fixes"），说明工作流在落地后经过了调试修正，属于典型的 CI 迭代过程。
- 与项目整体方向的关系：`diffusers` 是 HuggingFace 的核心扩散模型库，发布频率高、贡献者（社区 PR）众多，发布流程的任何手动环节都是瓶颈。该变更把发布后最容易遗漏、最容易出错的手工步骤固化为自动化流程，与项目"高质量开源协作 + 快速迭代"的目标一致。

### 3. 对项目的影响和潜在意义
- **降低发布风险**：减少发布后忘记恢复版本号、忘记合并版本相关 PR 导致的下游破坏，保障主线始终处于可发布状态。
- **减轻维护者负担**：发布者无需手动跟踪"发布后 PR"，减少人为遗漏。
- **对终端用户基本无感知**：不改变 API 或生成行为，但通过更稳定的发布节奏间接受益。
- **潜在风险**：自动化工作流若触发条件（如 `push`/`release` 事件）配置不当，可能产生噪音 PR 或与人工流程冲突，需要后续观察。

### 4. 值得关注的技术点
- 工作流的触发时机与权限设计：通常需要区分 `contents: write`、`pull-requests: write` 等权限，并决定是自动开 PR 还是自动提交。
- 幂等性与并发安全：发布连续触发时工作流是否会重复创建 PR。
- 后续 "fixes" 提示 CI 实际运行中暴露的问题，可作为审查此类工作流模板时的参考案例。

### 5. 基于 README 背景对项目发展的影响
README 表明 `diffusers` 是 Apache 2.0 许可的 HuggingFace 官方扩散模型库，强调社区贡献与规范协作。本次提交虽不涉及模型能力，却属于支撑项目长期发展的"隐形基础设施"：它使发布周期更可预测、贡献者体验更顺畅，从而把维护者精力释放到模型支持与文档建设上。随着库规模和发布频率持续增长，这类发布工程化改造将成为项目成熟度的标志，并为后续可能的自动化版本管理、变更日志生成奠定基础。

## 详细提交记录

### [ed32672](https://github.com/huggingface/diffusers/commit/ed32672706fec20ddac3a090c5a8290b3fd313cb)

- **作者**: Sayak Paul
- **时间**: 2026-11-21T03:33:44Z
- **提交信息**: ci: add a workflow to pr post-release changes. (#15257)

* add a workflow to pr post-release changes.

* fixes

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
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


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13425
- **最后更新**: 2026-11-22T01:55:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38909
- **最后更新**: 2026-11-22T01:59:10Z

## 提交统计

- **昨日提交总数**: 74
- **提交者数量**: 42
- **主要提交者**: DarkSharpness, Shuwen Wang, forrestl

## AI分析总结

# SGLang 昨日提交总结（共 74 条）

## 一、主要更新

性能优化占比最高，集中在 MoE/GEMM 内核、扩散模型推理与缓存策略；Bug 修复二十余条，覆盖调度器、内存缓存、约束解码、权重更新等核心链路；功能新增涉及投机解码、采样惩罚、Marlin 量化内核与新模型支持；另有 diffusion e2e 用例、Cookbook 文档、采样模块整合等测试与重构工作。

## 二、关键变更

- **扩散模型服务成为主线**：约 20 条围绕 Wan、MiniMax-H3、Krea-2、FLUX、Cosmos3 的注意力融合（FlashInfer Ulysses）、VAE 卷积优化、GPU 端量化缩放、组件驻留规划，并补齐 worker 死亡、Ulysses 超时、LoRA 校验等错误恢复与安全加固。
- **多后端内核与量化**：Marlin 运行 MXFP8 MoE 专家、trtllm-gen MXFP4 工作区预分配、H20 小 M 尺寸 FP8 GEMM 选核、AMD 融合 QK norm、NPU DSA 前缀 KV 扩展、paged-experts 下一层专家预取、diffusion 顺序均方归约融合。
- **调度与内存正确性**：分块预填充预算计数、重复释放/恢复请求处理、静态 KV 切换行重置、hicache O_DIRECT 对齐，以及约束解码语法 LRU 限制 RSS 增长。
- **投机解码与采样**：verify 阶段逐行惩罚、接受 token 全量送入 penalizers、基于词表分块的块验证接受机制、NGRAM 提示词尾部插入。
- **分布式与路由**：PP 下控制请求与本地广播修复、等待队列中止请求采样掩码返回、sgl-router 运行时 worker 管理 API 及延迟发现恢复。
- **内存与模型扩展**：HiSparse 分配器释放路径统一与 PP>1 分离式 PD 传输修复、L2→L3 写延迟指标、Hunyuan-4-Flash 视觉语言支持、MiniMax-H3 远程条件输入并发获取、NVFP4 用微型 FP32 路由 GEMM。

## 三、项目影响

扩散链路的健壮性与安全加固，说明多模态模块已从"能跑"进入"可生产"阶段；约束解码 LRU 与调度预算改进，直接缓解网关式部署的内存泄漏并改善吞吐与首延迟平衡；PP、分离式传输与路由动态管理的修复，显著降低大规模多卡集群的踩坑概率，路由组件也从静态配置走向动态运维。

## 四、值得关注的技术点

DSA 元数据内核批大小改为运行时参数，消除每 batch 的 Triton 重编译；词表分块投机验证提供了少见的细粒度接受判定并行化思路；NVFP4 下用高精度小路由网络保证专家选择质量，体现混合精度权衡；OOD 平台可中断图后端增强第三方硬件接入；多条提交由 Claude 等 AI 助手共同署名，半数左右带有 AI 协作痕迹，反映 AI 辅助开发已深度融入工作流。

## 五、整体影响

上述变更共同推进三条主线：把扩散与多模态生成推向生产级、在 NVIDIA/AMD/NPU 上持续压榨低精度内核性能、夯实调度缓存与权重更新的基础设施正确性。SGLang 正从以 LLM 为主的推理引擎，加速演进为覆盖生成式全模态的统一高性能服务平台，并借助测试、指标与文档建设保障快速迭代下的质量门槛。

## 详细提交记录

### [e96e967](https://github.com/sgl-project/sglang/commit/e96e96757018ce842d570781ec8312f8c470493b)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-21T22:28:20Z
- **提交信息**: [Feat] speculative: Apply exact per-row sampling penalties in verify (#52054)

Co-authored-by: sgrigory <sgrigory@users.noreply.github.com>

### [17c9d6f](https://github.com/sgl-project/sglang/commit/17c9d6f983e382bf710059216621c992a955cf6c)

- **作者**: Sara Tähtinen
- **时间**: 2026-11-21T22:25:52Z
- **提交信息**: [Feat] [AMD] dsv4: Dispatch Mega-mHC prefill to aiter on gfx950 (#44265)

### [6cf2500](https://github.com/sgl-project/sglang/commit/6cf25001599cdc4f20f350ffd4272c08a238328d)

- **作者**: DarkSharpness
- **时间**: 2026-11-21T22:11:49Z
- **提交信息**: [Test] mem_cache: Give the stage-capacity test's stub scheduler _embedding_preserve_last_token_id (#52113)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a945a72](https://github.com/sgl-project/sglang/commit/a945a7216fd25cbff85b116f70066be8f57b8190)

- **作者**: Khoa Pham
- **时间**: 2026-11-21T21:01:50Z
- **提交信息**: [Fix] moe: Pre-allocate the trtllm-gen MXFP4 MoE workspace at weight load (#51995)

### [f2d0e6d](https://github.com/sgl-project/sglang/commit/f2d0e6d50e4008a3356b97e19146e63ea2c7f995)

- **作者**: Trevor Morris
- **时间**: 2026-11-21T21:00:12Z
- **提交信息**: [Perf] [NVIDIA] deep_select: Opt-in multi-wave cluster top-k for long-tailed rows (#51348)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d5c2f00](https://github.com/sgl-project/sglang/commit/d5c2f00a38272eccd22987b90fddbdd531dcf2b2)

- **作者**: Mick
- **时间**: 2026-11-21T19:55:56Z
- **提交信息**: [CI] diffusion: replace FLUX.1/2 nightlies and add FLUX.3 TP2 e2e (#44651)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [2a2a15a](https://github.com/sgl-project/sglang/commit/2a2a15acef265829facabcf575282ce38146c659)

- **作者**: DarkSharpness
- **时间**: 2026-11-21T19:49:26Z
- **提交信息**: [Fix] JIT: Import the rotation helper from marker.timing in the Gemma4 AR fusion benchmark (#52126)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f7de4ec](https://github.com/sgl-project/sglang/commit/f7de4ec2026e32e7c1c6c038031684f93609d324)

- **作者**: DarkSharpness
- **时间**: 2026-11-21T19:48:06Z
- **提交信息**: [Fix] JIT: Keep strides when the benchmark marker clones inputs (#52117)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [abb8fe2](https://github.com/sgl-project/sglang/commit/abb8fe22e44d842b17734964eb1520d9d9c5cedf)

- **作者**: Mick
- **时间**: 2026-11-21T19:44:29Z
- **提交信息**: [Refactor] diffusion/cosmos3: Decode on the main CFG rank only, like the generic stage (#51563)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [f984776](https://github.com/sgl-project/sglang/commit/f984776424d9be76819f8b0e1b1ecd4eb5e9048c)

- **作者**: Tamir Baydasov
- **时间**: 2026-11-21T19:28:38Z
- **提交信息**: [Perf] [NPU] dcp: DSA extend gathers the prefix KV when that moves fewer bytes (#44320)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>

### [9de985c](https://github.com/sgl-project/sglang/commit/9de985ce1e7ec20285198d5ddc7ae2eda761fbce)

- **作者**: Mick
- **时间**: 2026-11-21T19:15:09Z
- **提交信息**: [Fix] diffusion/media: Limit the environment inherited by local codecs (#51954)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [bf9e7e8](https://github.com/sgl-project/sglang/commit/bf9e7e8947697dc48e101693f661a79cb2f21433)

- **作者**: Mick
- **时间**: 2026-11-21T19:13:26Z
- **提交信息**: [Fix] diffusion/attention: Use private sample IDs for STA calibration artifacts (#51972)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [e10cd70](https://github.com/sgl-project/sglang/commit/e10cd70f6a89e0793b70d7b07486ceae8592ce66)

- **作者**: Mick
- **时间**: 2026-11-21T19:09:03Z
- **提交信息**: [Perf] diffusion: Reuse the MP4 encoder's staging buffer for smaller frames (#52050)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4b7870f](https://github.com/sgl-project/sglang/commit/4b7870f45a4511b31f414bc710e615571f984f14)

- **作者**: Mick
- **时间**: 2026-11-21T19:06:48Z
- **提交信息**: [Fix] diffusion: Fail the request whose Ulysses peer wait expired, and bound the head-group pipeline's waits (#52030)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [b8da62f](https://github.com/sgl-project/sglang/commit/b8da62f74de287e96f2fcf9f2a15b405be063737)

- **作者**: Ritesh Das
- **时间**: 2026-11-21T19:05:04Z
- **提交信息**: [Fix] diffusion: Do not report ready when a worker dies during warmup (#51260)

### [7b23196](https://github.com/sgl-project/sglang/commit/7b2319621a13a89778de190256a635dd35d5f16a)

- **作者**: Alex Nails
- **时间**: 2026-11-21T19:03:40Z
- **提交信息**: [CI] ci-permissions: Add micyan01 and gausah01 with 30 min cooldown (#51928)

### [8e7bd02](https://github.com/sgl-project/sglang/commit/8e7bd026be11f6bbb061da01aa6cef81776c7a28)

- **作者**: Rumit Desai
- **时间**: 2026-11-21T19:02:59Z
- **提交信息**: [Feat] platforms: Let OOT platforms provide breakable graph backends (3/3) (#50150)

### [61cc15e](https://github.com/sgl-project/sglang/commit/61cc15e42c56b5424cc20974cd81264454c748de)

- **作者**: Ruilin Gao
- **时间**: 2026-11-21T19:02:02Z
- **提交信息**: [Fix] diffusion: Reject a LoRA adapter that matches no LoRA layer (#51783)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [42b4957](https://github.com/sgl-project/sglang/commit/42b495749df451b478bd0271eb2bd2ab87c23edd)

- **作者**: Mick
- **时间**: 2026-11-21T18:51:05Z
- **提交信息**: [Perf] diffusion: Memoize MiniMax-H3 block AdaLN projections per timestep set (#51965)

Co-authored-by: niehen6174 <42087078+niehen6174@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [ff3d144](https://github.com/sgl-project/sglang/commit/ff3d144f52853d85cbe0ec93a1e3b280c8890a89)

- **作者**: ChangLiu0709
- **时间**: 2026-11-21T18:48:45Z
- **提交信息**: [Perf] diffusion: Quantize and LANCZOS-resize MiniMax-H3 image output on the GPU (#51825)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [4ce4137](https://github.com/sgl-project/sglang/commit/4ce41378f96da24f12e76eae35dfea5bbf35844a)

- **作者**: DarkSharpness
- **时间**: 2026-11-21T16:54:46Z
- **提交信息**: [Test] weight_update: Stub the control-request barrier in the tensor-rank test (#52085)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9b4b6b6](https://github.com/sgl-project/sglang/commit/9b4b6b6d163c31d234e770eac9f484bd469822a3)

- **作者**: metamergebot
- **时间**: 2026-11-21T15:54:28Z
- **提交信息**: [Feat] marlin: Run MXFP8 (E4M3 weights, E8M0 group-32 scales) MoE experts on the Marlin kernel (#51936)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: chriswxho <chriswxho@users.noreply.github.com>

### [6d0d305](https://github.com/sgl-project/sglang/commit/6d0d305f198088227d258a470e54aaf5e5b95263)

- **作者**: desmond-intel
- **时间**: 2026-11-21T15:14:20Z
- **提交信息**: [Fix] embedding: Keep the trailing [SEP] on auto-truncation and accumulate MEAN pooling in fp32 (#39754)

### [f9e7f97](https://github.com/sgl-project/sglang/commit/f9e7f97dad3529eb4cbe1b84066df2e2c375132a)

- **作者**: Jan Schalkamp
- **时间**: 2026-11-21T14:55:10Z
- **提交信息**: [Perf] paged-experts: pre-copy the next layer's predicted experts beside compute (#51279)

### [aca0221](https://github.com/sgl-project/sglang/commit/aca0221867fb69853be6466da8b7283181359ba2)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-21T14:25:28Z
- **提交信息**: [Perf] diffusion: Fuse ordered mean-square reductions in Nomas VAE (#50602)

### [0d606c1](https://github.com/sgl-project/sglang/commit/0d606c1bb1b02971aef381ac7754299fc81fab9e)

- **作者**: DarkSharpness
- **时间**: 2026-11-21T14:22:05Z
- **提交信息**: [CI] [AMD] qknorm: Register test_qknorm to the base-a-jit-kernel-unit stage (#52084)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [af80e8c](https://github.com/sgl-project/sglang/commit/af80e8ce0dcf59197814fe216a7bf3976dbc1e07)

- **作者**: yusen huang
- **时间**: 2026-11-21T13:50:14Z
- **提交信息**: [Perf] [H20] fp8-gemm: Take the swapAB kernel for small-M block FP8 GEMM on H20 (#51220)

### [77c393a](https://github.com/sgl-project/sglang/commit/77c393a7beae720dfc3a6b4cf44f7aedbfedabc0)

- **作者**: Zheng Gong
- **时间**: 2026-11-21T13:50:04Z
- **提交信息**: [Perf] [AMD] qknorm: Use the fused in-place QK norm kernel on ROCm (#39071)

Signed-off-by: ZhengGong-amd <zgong@amd.com>
Co-authored-by: BBuf <35585791+BBuf@users.noreply.github.com>

### [2f54c4a](https://github.com/sgl-project/sglang/commit/2f54c4ae3a239dfe20c37c35a5aa97ffb4faeb10)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-21T13:49:54Z
- **提交信息**: [Fix] diffusion: Align Krea-2 request sizes to the 16-pixel patch grid (#50639)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [2095320](https://github.com/sgl-project/sglang/commit/20953202cd8dc71e60c603f14c4b609503fa009f)

- **作者**: forrestl
- **时间**: 2026-11-21T13:49:44Z
- **提交信息**: [Feat] diffusion: Integrate FlashInfer Ulysses for Wan and MiniMax H3 (#50243)

Co-authored-by: triple-mu <gpu@163.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [b563de5](https://github.com/sgl-project/sglang/commit/b563de5bc03b94c6761b203a2d4571b5377436a9)

- **作者**: swh
- **时间**: 2026-11-21T13:49:34Z
- **提交信息**: [Fix] dsa: Make metadata kernel batch size a runtime arg to avoid per-bs Triton recompiles (#50929)

### [b83d28a](https://github.com/sgl-project/sglang/commit/b83d28a905e74c789fff73f736a7a6980f8ea668)

- **作者**: GinDoliee
- **时间**: 2026-11-21T13:49:23Z
- **提交信息**: [Fix] constrained: bound the compiled-grammar cache by host memory (LRU) to stop RSS growth with per-request schemas (#45087)

Signed-off-by: GinDoliee <116713295+GinDoliee@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: ybyang <10629930+whybeyoung@users.noreply.github.com>

### [105aa26](https://github.com/sgl-project/sglang/commit/105aa2688d9ab865c29a02e8709f1845e36bf731)

- **作者**: Brilliant Hanabi
- **时间**: 2026-11-21T13:49:14Z
- **提交信息**: [Fix] weight_update: Rebuild each CUDA-IPC tensor once for the target and draft runners (#51237)

### [4d3d7c8](https://github.com/sgl-project/sglang/commit/4d3d7c8b9d380e3eb1434b1738c96bb71b01a862)

- **作者**: janssen-llm
- **时间**: 2026-11-21T13:49:04Z
- **提交信息**: [Feat] speculative: Insert bounded prompt tail on extend in NGRAMWorker (#48592)

Co-authored-by: janssen-llm <224949727+janssen-llm@users.noreply.github.com>

### [24b4950](https://github.com/sgl-project/sglang/commit/24b4950314f85adc4efa15f484134a9f277b8495)

- **作者**: Cui Hangbin
- **时间**: 2026-11-21T13:48:54Z
- **提交信息**: [Fix] scheduler: Count the unprefilled part of a chunked request in total_tokens load (#50088)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0ad20be](https://github.com/sgl-project/sglang/commit/0ad20bef23e4f0a1885920101f1c5d26acbbfe1a)

- **作者**: ankitgala007
- **时间**: 2026-11-21T13:48:44Z
- **提交信息**: [Fix] gemm: Use int64 row offsets in block-scaled FP8/INT8 matmuls (#51148)

Co-authored-by: Ankit Gala <204639277+ankitgala007@users.noreply.github.com>

### [4e130f8](https://github.com/sgl-project/sglang/commit/4e130f8c4be110fd2ea0fc40ca9bd685d5a6d39c)

- **作者**: xiaoke12345678
- **时间**: 2026-11-21T13:48:34Z
- **提交信息**: [Fix] kernels/layernorm: Mask the padded hc stream in fused_hc_head (#51210)

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [2d63591](https://github.com/sgl-project/sglang/commit/2d63591ac8905392d919876a38b5cfc4aa4fe96c)

- **作者**: DarkSharpness
- **时间**: 2026-11-21T13:48:23Z
- **提交信息**: [Fix] cli: Detect the rtxpro6000 Cookbook hardware id as an RTX PRO 6000 (#51943)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b959096](https://github.com/sgl-project/sglang/commit/b959096ecfac779048a1926eeda2f6cd173becf3)

- **作者**: metamergebot
- **时间**: 2026-11-21T12:45:07Z
- **提交信息**: [Feat] scheduler: Load-scaled class boundary and token budget for shortest-prefill-first (#51957)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: bbus <bbus@users.noreply.github.com>

### [93edbeb](https://github.com/sgl-project/sglang/commit/93edbeb3a15ff60214be380e856f2e94e7edba7c)

- **作者**: Shuwen Wang
- **时间**: 2026-11-21T09:10:44Z
- **提交信息**: [Fix] mem_cache: Carry pending request-row resets across static KV storage swaps (#51256)

### [c93e784](https://github.com/sgl-project/sglang/commit/c93e78483ba825ee5613fef6a1dc4fcd3cae1f31)

- **作者**: Nguyễn Văn Cao Nguyên
- **时间**: 2026-11-21T08:55:07Z
- **提交信息**: [Fix] hicache: Move NIXL pages that are not whole O_DIRECT blocks (#46540)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a3f5175](https://github.com/sgl-project/sglang/commit/a3f5175144bb27a16511b52c2e111be80801cf52)

- **作者**: zijiexia
- **时间**: 2026-11-21T08:24:36Z
- **提交信息**: [Doc] cookbook: Add the Inkling-2 model introductions and hardware tables (#52042)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d643847](https://github.com/sgl-project/sglang/commit/d643847f00977410474b72b4aa950a211199b859)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-21T08:16:22Z
- **提交信息**: [Feat] sampling: Count penalty history right after sampling in a per-request pool (#52035)

### [9251a20](https://github.com/sgl-project/sglang/commit/9251a2038fb79b233df8325e142d51123e64c00a)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-21T08:05:25Z
- **提交信息**: [Test] disaggregation: Run the Kimi-Linear PD+DCP prefill at hybrid checkpoint level 3 (#51979)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dabc58b](https://github.com/sgl-project/sglang/commit/dabc58b46b4cb5cdf57dc1e13b2f9c43ada77a4a)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-21T08:01:33Z
- **提交信息**: [Test] layers: Expect Kimi QKV on the KDA sharding group in the repeated/batched parallel-group test (#51974)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [42f4b39](https://github.com/sgl-project/sglang/commit/42f4b397356a049f0bf5190bb2ad9e0ec3d390cc)

- **作者**: Mick
- **时间**: 2026-11-21T07:47:48Z
- **提交信息**: [Feat] diffusion: Plan component residency from calibrated warmup records (2/4) (#37917)

Co-authored-by: mickqian <mickqian@radixark.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [8a8f630](https://github.com/sgl-project/sglang/commit/8a8f6303333e952edd1ba4647f02bf357f9be633)

- **作者**: Yuhao Yang
- **时间**: 2026-11-21T07:45:33Z
- **提交信息**: [Perf] qwen-vl: Stop checking the CUDA cache after every image preprocess (#51867)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c7e8a6e](https://github.com/sgl-project/sglang/commit/c7e8a6ea182f3e932d34f557303ffd283d2f7e34)

- **作者**: YAMY
- **时间**: 2026-11-21T06:54:18Z
- **提交信息**: [Fix] scheduler: Hold a capped chunk's unfinished rest in the prefill budget (#50955)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [5fa316b](https://github.com/sgl-project/sglang/commit/5fa316b98f097eb2c15a3fa901b87f0802b48068)

- **作者**: Mick
- **时间**: 2026-11-21T06:36:58Z
- **提交信息**: [Fix] diffusion: Fall back from K/V-gather for a cross-attention key mask (#51620)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [5100b80](https://github.com/sgl-project/sglang/commit/5100b805caf319beb8293e438e53fe6334bb678c)

- **作者**: Mick
- **时间**: 2026-11-21T06:35:12Z
- **提交信息**: [Perf] [AMD] diffusion: Run the BigVGAN vocoder's convolutions in MIOpen's summation orders from Triton (#51934)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [c8f1139](https://github.com/sgl-project/sglang/commit/c8f113963c3ed3fd0f31bdd309888f4be6614aa9)

- **作者**: Mick
- **时间**: 2026-11-21T06:34:15Z
- **提交信息**: [Fix] diffusion/media: Keep request URLs out of download errors (#51962)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [f55a496](https://github.com/sgl-project/sglang/commit/f55a4968ac80024614ac71eee633d698beb3d4ec)

- **作者**: Mick
- **时间**: 2026-11-21T06:32:46Z
- **提交信息**: [Fix] diffusion: Keep request content out of automatic media filenames (#51971)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [b25261a](https://github.com/sgl-project/sglang/commit/b25261af686334a9269e5d5cee10e6c87c71df5f)

- **作者**: Ruilin Gao
- **时间**: 2026-11-21T06:30:11Z
- **提交信息**: [Fix] diffusion: Compute fp16 LoRA deltas in the activations' dtype (#51494)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [c569c43](https://github.com/sgl-project/sglang/commit/c569c43446c2b4cb7b97c2d20bdbfa48b346ceba)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-21T05:53:47Z
- **提交信息**: [Fix] scheduler: Handle repeated and retried memory release and resume requests (#51398)

Signed-off-by: wzrd <floatlibai@gmail.com>
Co-authored-by: wzrd <floatlibai@gmail.com>

### [efab9d6](https://github.com/sgl-project/sglang/commit/efab9d61c5d08eb5b49e16d13436afdebdb162f5)

- **作者**: metamergebot
- **时间**: 2026-11-21T05:30:36Z
- **提交信息**: [Feat] [NVIDIA] jit: Let a module build for its arch family (sm_100f) instead of the arch-specific target (#51929)

Co-authored-by: mxz297 <mxz297@users.noreply.github.com>

### [26f993e](https://github.com/sgl-project/sglang/commit/26f993e1b2cfe4ed893028d90cc4b41da7d93234)

- **作者**: metamergebot
- **时间**: 2026-11-21T05:29:50Z
- **提交信息**: [Fix] rust-server: Serve /internal/peer only to the launch's own listeners (#51946)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [8396d60](https://github.com/sgl-project/sglang/commit/8396d60a14ef03b23d2cdaa5c64adb18eba7c703)

- **作者**: Tri Dao
- **时间**: 2026-11-21T04:13:39Z
- **提交信息**: [Perf] kimi-k3: Order shared-expert side-stream frees on the current stream (#51900)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [1222adc](https://github.com/sgl-project/sglang/commit/1222adc2100468706289a0dc56fda3639c48240f)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-21T03:53:12Z
- **提交信息**: [Refactor] sampling: Merge penaltylib into one penalties module (#52002)

### [8171e9a](https://github.com/sgl-project/sglang/commit/8171e9a4f5418ddad2dda911b66605b9982cce7b)

- **作者**: Mick
- **时间**: 2026-11-21T03:04:39Z
- **提交信息**: [Doc] diffusion/storage: Prefer workload credentials for S3 uploads (#51987)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [3214ab0](https://github.com/sgl-project/sglang/commit/3214ab01723a8ae27fae71242f53e4b2fb02cc6f)

- **作者**: Shuwen Wang
- **时间**: 2026-11-21T02:53:49Z
- **提交信息**: [Fix] hicache: Clear storage existence beliefs when a new backend is attached (#51254)

### [afe1225](https://github.com/sgl-project/sglang/commit/afe1225125fd4d53f5472f600e89cf4dd51153c2)

- **作者**: Shuwen Wang
- **时间**: 2026-11-21T02:53:09Z
- **提交信息**: [Refactor] hisparse: Route every allocator free through one path that releases the HiSparse mapping (#51252)

### [ceb1d75](https://github.com/sgl-project/sglang/commit/ceb1d752d96184f0d548d22753968f687e513704)

- **作者**: Nan Jiang
- **时间**: 2026-11-21T02:43:15Z
- **提交信息**: [Fix] tokenizer: Return sampling masks on requests aborted from the waiting queue (#50859)

Co-authored-by: HEJIAN SANG <sanghj0923@gmail.com>

### [229747b](https://github.com/sgl-project/sglang/commit/229747b96ff3de390e02db73fec8b4daf3630308)

- **作者**: hhy-seven
- **时间**: 2026-11-21T02:33:55Z
- **提交信息**: [Feat] kv-cache: Metrics for write latency distribution from L2 to L3 (#49537)

Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [40327da](https://github.com/sgl-project/sglang/commit/40327da185016a3ffabe13a205eeac4cbe5f302e)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-21T02:20:02Z
- **提交信息**: [Fix] scheduler: Fix control requests under PP and local control broadcast (#51641)

### [fadfdc4](https://github.com/sgl-project/sglang/commit/fadfdc42b68ffc746abef349cb58dd54878f7795)

- **作者**: Jeongho Shin
- **时间**: 2026-11-21T01:40:06Z
- **提交信息**: [Fix] disaggregation: fix HiSparse spec PD transfer on PP>1 prefill (#47840)

Co-authored-by: mlleo <mlleo@users.noreply.github.com>
Co-authored-by: Zhiqiang Xie <zqx@meta.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [40afa8e](https://github.com/sgl-project/sglang/commit/40afa8e6c6f159bf43d967dfc3066b7b7ceba900)

- **作者**: Yuwei An
- **时间**: 2026-11-21T01:21:52Z
- **提交信息**: [Fix] kernel_plugins: Let the K3.1 verify megakernel serve its own request buckets (#51983)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5b03592](https://github.com/sgl-project/sglang/commit/5b03592a5e3e98122ad2fe2ef652d0da826d4183)

- **作者**: Yuwei An
- **时间**: 2026-11-21T01:17:06Z
- **提交信息**: [Perf] reject_sampling: Vocabulary-tiled block-verification accept (#51961)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [83df28f](https://github.com/sgl-project/sglang/commit/83df28fc0b5c2f4cecad5ac26f765f127e910139)

- **作者**: Shangming Cai
- **时间**: 2026-11-21T01:12:06Z
- **提交信息**: [Test] ci: Fix two base-a-test-cpu stubs broken by #51668 and #51788 (#51978)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d169830](https://github.com/sgl-project/sglang/commit/d16983012668192e17bb09f608a417de5e1bf823)

- **作者**: Mick
- **时间**: 2026-11-21T01:07:30Z
- **提交信息**: [Perf] diffusion: Fetch a MiniMax-H3 request's remote condition inputs concurrently (#51939)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: WenhaoZhang <42087078+niehen6174@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [46a931c](https://github.com/sgl-project/sglang/commit/46a931ccf99fd4a88ee7ad754c1e073f9a5e22db)

- **作者**: Shangming Cai
- **时间**: 2026-11-21T00:50:39Z
- **提交信息**: [Fix] sgl-router: defer discovery restore while an API worker owns the URL (#51973)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c95fb12](https://github.com/sgl-project/sglang/commit/c95fb12bb8c2dbe318ddba9bbcc80db561798dfa)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-21T00:31:20Z
- **提交信息**: [Fix] speculative: Feed every accepted token to the penalizers (#51788)

### [6f3f73a](https://github.com/sgl-project/sglang/commit/6f3f73aef5eacea34bff20e3ac04ab5c8490f826)

- **作者**: Qiaolin Yu
- **时间**: 2026-11-21T00:24:46Z
- **提交信息**: [Feat] models: Hunyuan-4-Flash vision-language support (#51937)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [a8ac865](https://github.com/sgl-project/sglang/commit/a8ac86595c72cdd2f340a986020bdad69a06b65e)

- **作者**: Jimmy Shong
- **时间**: 2026-11-21T00:03:54Z
- **提交信息**: [Perf] beam: Use the tiny FP32 router GEMM for NVFP4 checkpoints (#51688)

### [aaa1441](https://github.com/sgl-project/sglang/commit/aaa14413569991f4ff3dd604a878a3783416ba0f)

- **作者**: Vincent Gao
- **时间**: 2026-11-21T00:02:33Z
- **提交信息**: [Feat] sgl-router: Add runtime worker management API (#50242)

Signed-off-by: Vincent Gao <vincentbo@linux.alibaba.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-22T02:02:24Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97319
- **最后更新**: 2026-11-22T02:02:36Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 22
- **主要提交者**: Yan Ma, roborluo, my-git9

## AI分析总结

## vLLM 昨日提交分析（28 条）

### 1. 主要更新类型
- **Bug 修复**：约占 40%，涵盖多模态、安全性、注意力融合等领域。
- **性能优化**：TMA 路径保留、MTP decode 融合内核、CUDA Graph 编码器等。
- **功能新增**：Inkling 2 Mini、masked_token_ids、编码器注意力钩子等。
- **安全加固**：输入边界、路径剥离、指针算术等 6 条相关提交。
- **CI/构建与文档**：Rubin 平台 nightly 构建、安全审查 skill 等。

### 2. 关键变更点与项目方向的关系
- **模型覆盖面扩展**（Inkling 2 Mini、HY4 Flash、ZAYA1 导出、Hy4-flash 清理）延续 vLLM "易用、快速、低成本服务所有人" 的目标，持续纳入新模型。
- **安全集中修复**（#52794、#53473、#53131 等补齐 PR #51447/#54721 遗留问题）表明项目正系统性强化生产级输入校验与资源边界，符合其作为企业级 LLM 服务引擎的定位。
- **多模态健壮性**（400 错误返回、PIL RGB 转换、rope_2d 尺寸修正、Qwen3-VL 标记 token 保留）提升视觉/音频推理的正确性。

### 3. 对项目的影响和潜在意义
- 安全系列提交显著降低恶意输入导致的越界与资源耗尽风险，利好 Red Hat 等企业采用。
- 性能提交（SM12x TMA、16 位递归状态融合解码、FlashInfer 批不变性、音频塔 CUDA Graph）直接降低推理延迟与成本。
- CI 适配 PyTorch cu135 与 Rubin/SM107 硬件，为下一代 GPU 铺路。

### 4. 值得关注的技术点
- **Inkling 2 的 SM12x TMA k_group_partials 路径**：显示新架构对硬件专属优化的依赖。
- **int32 → int64 指针算术扩展**：CUDA 内核潜在整数溢出的经典安全加固手法。
- **manual FlashInfer norm fusion 批不变性**：保证数值结果与批大小无关，对正确性至关重要。
- **DiffusionGemma 混合因果/双向注意力**：扩展 vLLM 到扩散模型推理场景。
- **AI 协作提交普遍**（Claude、Codex、vllm-agent 多次出现）：反映 AI 辅助开发已深度融入 vLLM 工作流。

### 5. 对项目发展的整体影响
这批提交体现了 vLLM 在"性能—正确性—安全"三条主线上的同步推进：性能上紧跟 Rubin/SM12x 等新硬件并持续压榨内核效率；正确性上集中修复多模态与注意力融合的边界问题；安全上完成了欠账已久的输入加固。模型与功能的快速新增则巩固其作为多模型 LLM 服务平台的广度。总体而言，这些变更推动 vLLM 从"能跑"向"企业可信赖的高性能推理引擎"演进，与其 README 中"Easy, fast, and cheap LLM serving for everyone"的愿景高度一致，为大规模生产部署和新硬件世代做好了准备。

## 详细提交记录

### [c32251b](https://github.com/vllm-project/vllm/commit/c32251b5d192f0f72f9ca8c5595d1d43f1dd37b8)

- **作者**: hcl
- **时间**: 2026-11-21T19:19:59Z
- **提交信息**: [Perf][Model] Inkling 2: keep the TMA k_group_partials path on SM12x (#69021)

Signed-off-by: Chenglun Hu <chenglunhu@gmail.com>

### [25d7765](https://github.com/vllm-project/vllm/commit/25d7765e632beca1edd0ce3e6a6dc8186e9d9bb3)

- **作者**: Shang Wang
- **时间**: 2026-11-21T19:03:02Z
- **提交信息**: [CI/Build][NVIDIA] Use PyTorch's cu135 nightly for Rubin and document the ptxas 13.5.37 SM107 workaround (#68036)

Signed-off-by: Shang Wang <samshang.wang@mail.utoronto.ca>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [1bdc437](https://github.com/vllm-project/vllm/commit/1bdc437402d6eee29d3ca543c91574f8acc72c8d)

- **作者**: Jee Jee Li
- **时间**: 2026-11-21T16:21:29Z
- **提交信息**: [Model] Hy4-flash Cleanup (#69013)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [7e792e6](https://github.com/vllm-project/vllm/commit/7e792e6e105e3e83c0fc2ebecb0fccc0a49b0290)

- **作者**: Andy Chen
- **时间**: 2026-11-21T16:20:57Z
- **提交信息**: [Bugfix] Whisper prompt conditioning: use the real `<|startofprev|>` token (#53207)

Signed-off-by: Andy Chen <87085682+andynoodles@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ab18334](https://github.com/vllm-project/vllm/commit/ab18334a4f60da74db7de89fe95594e5ed0cda36)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-21T16:19:33Z
- **提交信息**: [Model] Add Inkling 2 Mini (#69028)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Kate Cheng <yunhsuanc@nvidia.com>
Co-authored-by: Eric Tang <46737979+erictang000@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cc00267](https://github.com/vllm-project/vllm/commit/cc00267752e51c76ef904da02bd0232eb682991e)

- **作者**: Tony Lin
- **时间**: 2026-11-21T15:47:05Z
- **提交信息**: [Bugfix] Normalize native GTE positional embedding configuration (#69145)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [81a4fe5](https://github.com/vllm-project/vllm/commit/81a4fe55a22d4f11754a535051b56c6faca738dc)

- **作者**: Tony Lin
- **时间**: 2026-11-21T15:29:21Z
- **提交信息**: [CI] Use platform device in M-RoPE prompt embeds test (#69134)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [93c590e](https://github.com/vllm-project/vllm/commit/93c590ef3a84a4a064bfe5ca5146b3d848054072)

- **作者**: aoshen02
- **时间**: 2026-11-21T15:27:29Z
- **提交信息**: [Model] Add masked_token_ids to never sample given tokens (#68976)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c2fb5c5](https://github.com/vllm-project/vllm/commit/c2fb5c5aba0a904fdbecb8e01b7c41db5bfaeadf)

- **作者**: my-git9
- **时间**: 2026-11-21T13:35:06Z
- **提交信息**: [Bugfix][Multimodal] Return 400 for unreadable embedding payloads (#69073)

Signed-off-by: xin.li <xin.li@daocloud.io>

### [0bf9c07](https://github.com/vllm-project/vllm/commit/0bf9c07376a4091627e6cb50dd85464361db452c)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-21T12:18:40Z
- **提交信息**: [Bugfix][Security] Complete input-bound hardening left incomplete by PR #51447 (#54721)

Signed-off-by: jperezde <jperezde@redhat.com>

### [80456e5](https://github.com/vllm-project/vllm/commit/80456e51f8ec16e88eeb918881f7a758cbd1c2fe)

- **作者**: Yan Ma
- **时间**: 2026-11-21T11:08:08Z
- **提交信息**: [XPU] skip not applied tests in lora/test_layer.py and test_config.py on XPU (#68971)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9920e7c](https://github.com/vllm-project/vllm/commit/9920e7c7c8aabd90384f03ef75143cfac8068737)

- **作者**: Jared Wen
- **时间**: 2026-11-21T10:52:43Z
- **提交信息**: [Perf][Model] Export ZAYA1 CCA prefill checkpoints (#68921)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dd8c157](https://github.com/vllm-project/vllm/commit/dd8c157895f01875bc5f44c51003bbe330647330)

- **作者**: Ashwani Agarwal
- **时间**: 2026-11-21T10:39:15Z
- **提交信息**: [Bugfix][EC Connector] Keep marker token embeddings for pruned Qwen3-VL video on encoder-only instances (#68314)

Signed-off-by: Ashwani Agarwal <ashwani.agarwal93@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a5a902d](https://github.com/vllm-project/vllm/commit/a5a902d02328e48493775ed75e352059e9d3b3b0)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-21T10:01:56Z
- **提交信息**: [Doc] Add vLLM security review skill (#69101)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Codex <codex@openai.com>

### [78f20a5](https://github.com/vllm-project/vllm/commit/78f20a5a3454bcdcc0717cf63d26acf4075c1161)

- **作者**: Thien Tran
- **时间**: 2026-11-21T08:55:33Z
- **提交信息**: [Kernel][GDN] Faster fused CUDA MTP decode for 16-bit recurrent state (#69065)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3a11764](https://github.com/vllm-project/vllm/commit/3a1176475f25255923cbf881b277a9f676c762ca)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-21T08:48:39Z
- **提交信息**: fix(security): use segment-boundary-aware root_path stripping in auth middleware (#52794)

Signed-off-by: jperezde <jperezde@redhat.com>

### [468d10a](https://github.com/vllm-project/vllm/commit/468d10ae51ed432ff0612a7e3a57ec308439846c)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-21T08:07:27Z
- **提交信息**: fix(security): enforce prompt-count bound on pooling and scoring routes (#53473)

Signed-off-by: jperezde <jperezde@redhat.com>

### [6e0991c](https://github.com/vllm-project/vllm/commit/6e0991c296f77de07d7d9007580544d91ae4d4ce)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-21T08:06:22Z
- **提交信息**: [Security] Share media byte budgets across batched requests (#68249)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>

### [bafe5cc](https://github.com/vllm-project/vllm/commit/bafe5cc3e803601b490ea6090c52b9b1e4e53497)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-21T07:52:24Z
- **提交信息**: [Security] Widen int32 pointer arithmetic to int64 in CUDA kernels (#53131)

Signed-off-by: jperezde <jperezde@redhat.com>
Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bf151b7](https://github.com/vllm-project/vllm/commit/bf151b7eb1403d3671200e0cd19ad9821fe4320f)

- **作者**: Yarikama
- **时间**: 2026-11-21T06:49:11Z
- **提交信息**: [Bugfix][Multimodal] Convert PIL video frames to RGB like PIL images (#69089)

Signed-off-by: yarikama <amaki30226@gmail.com>

### [a25064c](https://github.com/vllm-project/vllm/commit/a25064c85d0c9efef2ea0be00170bfd7720772c4)

- **作者**: sean
- **时间**: 2026-11-21T06:33:13Z
- **提交信息**: [Bugfix][Multimodal] Size rope_2d DP vision outputs from the spatial grid (#68739)

Signed-off-by: Sean Bangalore <bsudarshan@outlook.com>
Signed-off-by: sean <bsudarshan@outlook.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [f8b29fa](https://github.com/vllm-project/vllm/commit/f8b29fab414884206460fe63b983ca34fc6e3e9b)

- **作者**: Deepanker Kumeria
- **时间**: 2026-11-21T05:33:40Z
- **提交信息**: [Perf][Multimodal] Encoder CUDA graphs for the Qwen3-Omni / Qwen3-ASR audio tower (#68831)

Signed-off-by: Deepanker Kumeria <deepanker.kumeria@decagon.ai>
Co-authored-by: Devin (Cognition AI) <devin-ai-integration[bot]@users.noreply.github.com>

### [ad90533](https://github.com/vllm-project/vllm/commit/ad9053380fe83234bcdc1f262abb7143c9cf0cfb)

- **作者**: Wangyuane
- **时间**: 2026-11-21T04:42:10Z
- **提交信息**: [Bugfix] Honor batch invariance in manual FlashInfer norm fusion (#68600)

Signed-off-by: Wangyuaneee123 <zhimadoushabao@163.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bd53af0](https://github.com/vllm-project/vllm/commit/bd53af0bbec2296e36f9413b69b63664839267e3)

- **作者**: Jhao-Ting Chen
- **时间**: 2026-11-21T04:00:37Z
- **提交信息**: [Attention][FlashInfer] DiffusionGemma: mixed causal/bidirectional attention on TRTLLM-Gen, default for text-only SM100/SM103 (#62516)

Signed-off-by: Jhao-Ting Chen <jhaotingc@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2f170a0](https://github.com/vllm-project/vllm/commit/2f170a0fed20fd84dfcf6da2a3a8188a32f67e4e)

- **作者**: roborluo
- **时间**: 2026-11-21T00:55:45Z
- **提交信息**: [Bugfix][DSv4.1] Read the DSpark draft's native mega MoE flag from its layers (#69023)

Signed-off-by: bofengl <bofengl@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [bf4a317](https://github.com/vllm-project/vllm/commit/bf4a317ee65dba1198e420be5253334f23f2fbdc)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-21T00:23:11Z
- **提交信息**: [HiSparse] Support HY4 Flash (#69026)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [820fce0](https://github.com/vllm-project/vllm/commit/820fce0d6755e3ebd72abf01be099df4001835ca)

- **作者**: Alex Steiner
- **时间**: 2026-11-21T00:11:52Z
- **提交信息**: [Feature] Encoder-only attention hooks for model-owned layouts (#67798)

Signed-off-by: pst2154 <6865592+pst2154@users.noreply.github.com>
Co-authored-by: pst2154 <6865592+pst2154@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c6b1b80](https://github.com/vllm-project/vllm/commit/c6b1b800ec856e2cf504a10df8f8626bb6e24152)

- **作者**: Taneem Ibrahim
- **时间**: 2026-11-21T00:05:55Z
- **提交信息**: [Benchmark] Add decisions backends to vllm bench serve (#68760)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-22
**监控日期**: 2026-11-21
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7891
- **最后更新**: 2026-11-22T02:02:37Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 21
- **主要提交者**: He Yingxu, lm10-arg, Lingwei1943

## AI分析总结

## vllm-omni 昨日提交分析（34 条）

### 1. 主要更新类型
- **Bug 修复**：约 14 条，占比最高，涉及 token 预算、采样恢复、边界处理等核心推理逻辑。
- **CI/Build**：约 12 条，集中在 ROCm/AMD 平台的 NIGHTLY 测试覆盖与稳定性。
- **功能新增/模型接入**：PersonaPlex、Ming TTS、Phonon 31M 流式 TTS 等接入 Model Runner V2。
- **性能优化**：约 3 条，包括 NPUGraph 加速、FA2 varlen 注意力、线程调度优化。
- **文档与测试**：Ascend 硬件认证文档、实时音频格式解析测试覆盖。

### 2. 关键变更点与项目方向的关系
- **Model Runner V2 迁移持续推进**：PersonaPlex、Ming TTS、GLM-TTS、Higgs Audio V2 等陆续迁入 MRv2 或修复其采样问题，表明项目正将各模态统一到新一代执行框架，契合"简单、快速、低成本的全模态服务"目标。
- **语音生成正确性**：Step-Audio2、CoVo-Audio 的 token 预算尊重，JoyAI 轮次边界、Qwen3-TTS 语音参考校验，均保障多轮语音交互的可控性与合规性。
- **多硬件生态扩张**：ROCm、Ascend、Intel XPU（HunyuanImage-3）、NPUGraph 的提交，体现项目对全平台部署的重视。
- **测试矩阵完善**：LingBot、MiniMax-H3、Voxtral、Qwen3-Omni、MiniCPM-o 等场景矩阵化对齐，提升回归可靠性。

### 3. 对项目的影响与潜在意义
- MRv2 迁移与采样修复降低了新框架的碎片化风险，提升跨模型一致性。
- 丰富的 NIGHTLY 覆盖（尤其 AMD 平台）将硬件兼容问题提前暴露，减少生产环境故障。
- 流式 TTS 与实时客户端修复（CJK 文本支持、音频格式校验）直接改善端到端语音交互体验。

### 4. 值得关注的技术点
- **调度缓存**：VoxCPM2 统一解码图状态在调度器中缓存，减少重复编译开销。
- **NPUGraph 加速 AudioVAE 解码**，与 OmniVoice 的 FA2 varlen 优化同属推理热路径提效。
- **引擎关闭时失败在途请求**（Frontend），完善了服务生命周期语义，避免悬挂请求。
- **OOM 证据保留**（#10578）：CI 中保留内存溢出现场，便于诊断 flaky 测试根因。

### 5. 对项目发展的整体影响
这些提交共同强化了 vllm-omni 作为"全模态模型服务平台"的三大支柱：统一执行框架（MRv2）的成熟、多模态（语音/文本/图像/视频）交互的健壮性、以及跨 GPU/ROCm/Ascend/XPU 硬件的广泛验证。持续的测试矩阵化与性能修复表明项目已从功能扩张期进入工程质量深耕期，为生产级部署奠定基础，最终朝着 README 承诺的"面向大众的易用、快速、低成本全模态服务"稳步迈进。

## 详细提交记录

### [448a238](https://github.com/vllm-project/vllm-omni/commit/448a2381ca4a2423dc74171bf2a11a19c5b21154)

- **作者**: boatman
- **时间**: 2026-11-21T23:45:23Z
- **提交信息**: [Feat] Add PersonaPlex stage0 Model Runner V2 support (#10042)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>

### [5f9718b](https://github.com/vllm-project/vllm-omni/commit/5f9718bf89859a952488577fe11b4d76e678da0a)

- **作者**: lm10-arg
- **时间**: 2026-11-21T23:02:43Z
- **提交信息**: [CI/Build][ROCm] Probe Wan2.1 VACE weekly coverage (#10492)

Signed-off-by: lm10-arg <lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <lm10-arg@users.noreply.github.com>

### [df1bd5c](https://github.com/vllm-project/vllm-omni/commit/df1bd5c15dad08261b8b103879d32407e230a811)

- **作者**: lm10-arg
- **时间**: 2026-11-21T22:40:13Z
- **提交信息**: [Bugfix][ROCm] Restore GLM-TTS MRv2 RAS sampling (#10915)

Signed-off-by: lm10-arg <linluo@icloud.com>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>

### [9e50e66](https://github.com/vllm-project/vllm-omni/commit/9e50e66287481a9fcfcaeb1996e4a7b0062565fa)

- **作者**: dongbo910220
- **时间**: 2026-11-21T22:20:04Z
- **提交信息**: [Bugfix] Honor Step-Audio2 speech request token budgets (#10812)

Signed-off-by: dongbo910220 <1275604947@qq.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [3736c1c](https://github.com/vllm-project/vllm-omni/commit/3736c1c1805c05d1a61e0dcefb3f986995fdc887)

- **作者**: lm10-arg
- **时间**: 2026-11-21T21:55:01Z
- **提交信息**: [Bugfix][ROCm] Restore Higgs Audio V2 MRv2 sampling (#10914)

Signed-off-by: lm10-arg <linluo@icloud.com>

### [3789f7a](https://github.com/vllm-project/vllm-omni/commit/3789f7a2305dc3e152cbe9073c2267af9dfc85ce)

- **作者**: wuli666
- **时间**: 2026-11-21T21:10:51Z
- **提交信息**: [Model] Run Ming TTS on Model Runner V2 (#9970)

Signed-off-by: wuli666 <421774554@qq.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [cf8414f](https://github.com/vllm-project/vllm-omni/commit/cf8414f7c3cee84847646dedb9079d76f3a9138e)

- **作者**: haic0
- **时间**: 2026-11-21T21:08:52Z
- **提交信息**: [CI/Build] Add AMD NIGHTLY MiniMax-H3 Ref2VA partition coverage (#10765)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [cf6121c](https://github.com/vllm-project/vllm-omni/commit/cf6121c83b9a69bbd2875d2bfeb535aac0497939)

- **作者**: lm10-arg
- **时间**: 2026-11-21T20:48:08Z
- **提交信息**: [Model][CI/Build] Stabilize Voxtral, Qwen3-Omni, and H100 TTS NIGHTLY performance (#10759)

Signed-off-by: abdelmoumene boumadane <fa_boumadane@esi.dz>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: abdelmoumene boumadane <fa_boumadane@esi.dz>
Co-authored-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [cc035d6](https://github.com/vllm-project/vllm-omni/commit/cc035d6d5460b4e75a7fc974e1592ca3189efd5c)

- **作者**: haic0
- **时间**: 2026-11-21T20:34:47Z
- **提交信息**: [CI/Build] Add AMD NIGHTLY LingBot dense/MoE/offload coverage (#10764)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [9c82e5b](https://github.com/vllm-project/vllm-omni/commit/9c82e5bdf310af494e18242f55b0f4653d975b5a)

- **作者**: boatman
- **时间**: 2026-11-21T20:09:08Z
- **提交信息**: [Model] Add Phonon 31M EN streaming TTS integration  (#9995)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>

### [5d9e8b5](https://github.com/vllm-project/vllm-omni/commit/5d9e8b583604fc96345bb41197fdda8564a48009)

- **作者**: lm10-arg
- **时间**: 2026-11-21T19:04:45Z
- **提交信息**: [Bugfix][CI/Build] Preserve OOM evidence and restore reliability coverage (#10578)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>

### [f742a78](https://github.com/vllm-project/vllm-omni/commit/f742a7837653bd5d8ae55ab92a5c938ee06952b5)

- **作者**: Hikari
- **时间**: 2026-11-21T18:50:38Z
- **提交信息**: [Perf][OmniVoice] Use vLLM FA2 varlen when the diffusion attention backend lacks packed varlen (#10909)

Signed-off-by: altale <extsuioku@gmail.com>

### [33a4d78](https://github.com/vllm-project/vllm-omni/commit/33a4d787dd99cdfd6ca3638eaaddd6a3d58de993)

- **作者**: lm10-arg
- **时间**: 2026-11-21T18:26:09Z
- **提交信息**: [CI/Build][ROCm] Stabilize BAGEL cold AITER startup (#10497)

Signed-off-by: lm10-arg <lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <lm10-arg@users.noreply.github.com>

### [6f46df2](https://github.com/vllm-project/vllm-omni/commit/6f46df2cf18da6090c9a4f26860d1ced7f6a94c2)

- **作者**: lm10-arg
- **时间**: 2026-11-21T17:30:32Z
- **提交信息**: [Bugfix][Model] Handle text-only MiMo-Audio chunks (#10882)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [286d4a6](https://github.com/vllm-project/vllm-omni/commit/286d4a6a519fa34e2c6b914b03b76ed474c5f57e)

- **作者**: psv666
- **时间**: 2026-11-21T14:32:51Z
- **提交信息**: [CI/Build] Align Qwen3-Omni benchmarks with the scenario matrix (#10152)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [dbd2566](https://github.com/vllm-project/vllm-omni/commit/dbd2566e0ba155db0907ae65ef0eb9d0fc0d908c)

- **作者**: He Yingxu
- **时间**: 2026-11-21T10:54:45Z
- **提交信息**: [Bugfix][Cosmos3] Keep the reference image aspect ratio for image-to-video (#10787)

### [12469be](https://github.com/vllm-project/vllm-omni/commit/12469beb9a73bca21b111c86bafafa47210b3f3b)

- **作者**: searlion
- **时间**: 2026-11-21T10:18:57Z
- **提交信息**: [Bugfix][Qwen3-TTS] Reject Base requests without a voice reference (#10545)

Signed-off-by: Lewis Won <lewis.won@gmail.com>

### [6ce3e37](https://github.com/vllm-project/vllm-omni/commit/6ce3e37a52771195868bb91cfe4a6a9354c98c16)

- **作者**: amy-why-3459
- **时间**: 2026-11-21T09:55:28Z
- **提交信息**: [Bugfix] Preserve JoyAI turn boundaries after cancelled speech (#10890)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4172881](https://github.com/vllm-project/vllm-omni/commit/4172881a41963e9372ebe6028bfdbfbb45ad56f4)

- **作者**: dongbo910220
- **时间**: 2026-11-21T09:36:34Z
- **提交信息**: [Bugfix] Honor CoVo-Audio speech request token budgets (#10876)

Signed-off-by: dongbo910220 <1275604947@qq.com>

### [0f363a5](https://github.com/vllm-project/vllm-omni/commit/0f363a5ccfd348f28f0472dab978d061606439ec)

- **作者**: psv666
- **时间**: 2026-11-21T09:05:03Z
- **提交信息**: [Bugfix][Frontend] Fail in-flight requests during engine shutdown (#10808)

Signed-off-by: psv666 <2693925048@qq.com>
Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4bd645a](https://github.com/vllm-project/vllm-omni/commit/4bd645a7adee531b548a0b5dcd862f889e7e7414)

- **作者**: amy-why-3459
- **时间**: 2026-11-21T08:51:00Z
- **提交信息**: [Bugfix] Fix Qwen-Image-2.1 mixed-length RoPE on Ascend (#10889)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [ca47f05](https://github.com/vllm-project/vllm-omni/commit/ca47f05f5ca6bf6d7ceca3ab59808447a1d45570)

- **作者**: ZacheryAU
- **时间**: 2026-11-21T08:34:58Z
- **提交信息**: [CI/Build] Update MiniCPM-o 4.5 CI with the scenario matrix (#10697)

Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [79c209f](https://github.com/vllm-project/vllm-omni/commit/79c209f097fc7f5e66bf6bf684dd59a727004230)

- **作者**: Binbin Zhang
- **时间**: 2026-11-21T06:34:55Z
- **提交信息**: [Test] Cover realtime audio-format parsing and validation (#10012)

Signed-off-by: Binbin Zhang <binbin36520@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [c5b673d](https://github.com/vllm-project/vllm-omni/commit/c5b673d3efdeaca6f2363d1f393eacd8f861a022)

- **作者**: James-Bond123
- **时间**: 2026-11-21T06:03:16Z
- **提交信息**: [Fix] streaming_speech_client: support CJK text in --simulate-stt (#7860)

Signed-off-by: 艺毅 胡 <18235123525@163.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [d76c326](https://github.com/vllm-project/vllm-omni/commit/d76c3264df3b60437555257fd1a92263a3258aec)

- **作者**: Ryn Wang
- **时间**: 2026-11-21T05:31:26Z
- **提交信息**: [Core] Cache the resolved VoxCPM2 unified-decode-graph state in the scheduler (#10048)

Signed-off-by: Ryn Wang <Ryn.Wang@outlook.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [673daea](https://github.com/vllm-project/vllm-omni/commit/673daeada725f325fb488f9582c035411d60ef71)

- **作者**: Lingwei1943
- **时间**: 2026-11-21T04:59:02Z
- **提交信息**: [perf][VoxCPM2]: add AudioVAE NPUGraph for VAE decode acceleration (#8312)

Signed-off-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Signed-off-by: SamitHuang <285365963@qq.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: opencode <opencode@ai>
Co-authored-by: SamitHuang <285365963@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: SunXiaoYu1999 <38288359+SunXiaoYu1999@users.noreply.github.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [1d27e89](https://github.com/vllm-project/vllm-omni/commit/1d27e89879eaf5e2c9a071baac27d364718a4ee1)

- **作者**: Aiminer
- **时间**: 2026-11-21T04:50:30Z
- **提交信息**: [Doc] Qwen3-TTS: add Ascend 910B3 64GB qualification (#10285)

Signed-off-by: pop-aiminer <134584385+pop-aiminer@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [48a9fcd](https://github.com/vllm-project/vllm-omni/commit/48a9fcdb084aadc5bf29bbf0eefda28ffaa912c9)

- **作者**: Alessio Netti
- **时间**: 2026-11-21T04:18:57Z
- **提交信息**: [Perf] Avoid thread offload if Janus command queue has capacity (#9491)

Signed-off-by: Alessio Netti <26897207+AlessioNetti@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [e24f1fb](https://github.com/vllm-project/vllm-omni/commit/e24f1fb753c5279e517d022a6f98d066743519a4)

- **作者**: Indigo Tan
- **时间**: 2026-11-21T03:55:40Z
- **提交信息**: [CI/Build] Remove runtime version pins from LingBot accuracy capture (#10817)

Signed-off-by: Indigo Tan <344920135+IndigoTan@users.noreply.github.com>
Co-authored-by: Indigo Tan <344920135+IndigoTan@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [e2249b0](https://github.com/vllm-project/vllm-omni/commit/e2249b08a9c6b6dfa6e63013d01f402d0d808d18)

- **作者**: Carmen Lok
- **时间**: 2026-11-21T03:42:36Z
- **提交信息**: [Core][Model] JoyAI-VL-Interaction: skip the Code2Wav prewarm for text-only duplex turns (#10033)

Signed-off-by: carmenlok <lok@whitebad.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [d8e5258](https://github.com/vllm-project/vllm-omni/commit/d8e52586780a1d80c2ea8f880d6ca901f7cd450a)

- **作者**: hac17
- **时间**: 2026-11-21T03:01:36Z
- **提交信息**: [CI/Build][ROCm] Promote NIGHTLY MiniCPM-o 4.5 duplex function to blocking (#10769)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [882e4c7](https://github.com/vllm-project/vllm-omni/commit/882e4c750628658f24d0b60c028520f35e056176)

- **作者**: hac17
- **时间**: 2026-11-21T02:59:37Z
- **提交信息**: [CI/Build][ROCm] Enforce Stable Audio CPU offload memory savings in NIGHTLY (#10770)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [07adf5d](https://github.com/vllm-project/vllm-omni/commit/07adf5d85815448af12f2baa75bb6c33966cb4fd)

- **作者**: amy-why-3459
- **时间**: 2026-11-21T02:48:01Z
- **提交信息**: [Bugfix] Restore LingBot Video image generation capability (#10886)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [dc8214f](https://github.com/vllm-project/vllm-omni/commit/dc8214f410b32bcdef699b39572681425a312b92)

- **作者**: Chendi.Xue
- **时间**: 2026-11-21T02:09:13Z
- **提交信息**: [Bugfix][Hardware][Intel][HunyuanImage-3] Run HunyuanImage-3.0 AR+DiT on XPU (#10278)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

---
