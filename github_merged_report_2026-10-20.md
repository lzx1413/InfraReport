# GitHub Stars 合并报告 - 2026-10-20

**合并日期**: 2026-10-21
**监控日期**: 2026-10-20
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


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2252
- **最后更新**: 2026-10-20T13:38:01Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Zeren Chen, Sun, YLlllllllllll

## AI分析总结

## VeOmni 昨日提交分析

### 1. 主要更新类型

本次提交以 **功能新增** 为主（4项），辅以 **Bug修复**（3项）和 **CI/工程改进**（1项），覆盖并行训练、算子优化、模型架构和工具链多个层面，是典型的高质量开发日。

### 2. 关键变更点及其与项目方向的关系

- **DeepSeek V4 专家并行数值对齐**：修复了大规模 MoE 训练中专家并行（expert parallelism）的数值精度问题，直接服务于项目"模型中心的分布式训练配方"核心定位。
- **Flex/Magi 算子按 GPU 代际自动选择**：让算子后端能根据 GPU 架构（如 Hopper/Blackwell）自动调度最优实现，体现了 VeOmni 对多硬件生态的适配策略。
- **Qwen3.5 共享前缀训练**：新增 shared-prefix training 能力，这是面向多模态/长上下文场景的重要训练优化，扩展了 VeOmni 支持的模型谱系。
- **qwen4_exp qsa attention 的上下文并行支持**：为新版 Qwen4 实验性 QSA 注意力注入 context parallelism，推进大模型并行训练的可扩展性。
- **NPU 无限 masked QSA TopK 修复**：解决昇腾 NPU 平台上 Attention 计算的数值 bug，延续了项目跨国产芯片支持的方向。
- **CUDA profiler 内存历史崩溃修复**：提升 CI 稳定性与性能调试可靠性。
- **CodeRabbit 增量审查限制显式化**：工程治理层面的小改进，优化代码审查效率。

### 3. 对项目的影响和潜在意义

- **鲁棒性显著提升**：同时修复了 GPU、NPU 上的数值稳定性和 CI 崩溃问题，降低了用户在不同硬件上复现训练配方的门槛。
- **模型覆盖版图扩张**：新增 Qwen3.5、qwen4_exp 等前沿模型支持，并补上 DeepSeek V4 关键修复，使 "Recipe Zoo" 的配方库更贴近产业最新实践。
- **并行策略深化**：专家并行、上下文并行两条线同时推进，强化了 VeOmni 在大规模分布式训练上的技术壁垒。

### 4. 值得关注的技术点

- **GPU 代际感知的算子选择机制**：说明项目已建立自动化的硬件能力探测抽象，这类基础设施可复用于更多算子。
- **共享前缀训练（shared-prefix training）**：在推理侧已广泛使用的前缀共享思路进入训练侧，有望显著降低多轮/多模态场景的训练成本。
- **由 AI 辅助（Cursor）协作产出的并行特性提交**：体现了项目在开发流程中已引入 AI 编码代理，值得关注其对交付效率的影响。
- **专家并行的数值对齐**：在 MoE 训练中，微小数值差异可能被梯度放大，此类修复对科研复现至关重要。

### 5. 对项目发展的整体影响

结合 README，VeOmni 的目标是成为"任意模态模型训练的模型中心分布式配方库"。本次提交群同时巩固了三条主线：**硬件多样性**（GPU/NPU 修复、算子自动选择）、**并行规模性**（专家并行、上下文并行）、**模型谱系广度**（DeepSeek V4、Qwen3.5/4）。这些变更使 VeOmni 的配方库更稳定、更前沿，降低了从论文到可运行训练脚本的转化阻力，有助于吸引更多研究者和工程师将 VeOmni 作为多模态大模型训练的默认基础设施，从而推动项目生态的正向增长。

## 详细提交记录

### [4c78b23](https://github.com/ByteDance-Seed/VeOmni/commit/4c78b23e1218837f851189299ff67f84ae37a4a3)

- **作者**: 0z5a
- **时间**: 2026-10-20T13:37:53Z
- **提交信息**: [parallel, ops] fix: align DeepSeek V4 expert parallel numerics (#1199)

Signed-off-by: 0z5a <dezhen.lu@student.uni-tuebingen.de>

### [611002d](https://github.com/ByteDance-Seed/VeOmni/commit/611002d69195e9fc81f03e96a20e5d61587ac326)

- **作者**: Zeren Chen
- **时间**: 2026-10-20T10:53:17Z
- **提交信息**: [ops] feat: select Flex/Magi by GPU generation (#1321)

### [dc91c05](https://github.com/ByteDance-Seed/VeOmni/commit/dc91c058ddb6d205dea4e047989f628a64209ba9)

- **作者**: Sun
- **时间**: 2026-10-20T10:51:26Z
- **提交信息**: [perf, ci] fix: avoid CUDA profiler memory history crash (#1233)

### [3089331](https://github.com/ByteDance-Seed/VeOmni/commit/308933155f8474ab0bed837bdd012f1e0e202d18)

- **作者**: YLlllllllllll
- **时间**: 2026-10-20T09:36:06Z
- **提交信息**: [model] fix: avoid infinite masked QSA TopK scores on NPU (#1275)

### [29ba189](https://github.com/ByteDance-Seed/VeOmni/commit/29ba1898389bd5de41ae943fc152ef98ce22668e)

- **作者**: Bin Jia
- **时间**: 2026-10-20T09:18:53Z
- **提交信息**: [agent] chore: make CodeRabbit incremental review limits explicit (#1325)

### [af5b287](https://github.com/ByteDance-Seed/VeOmni/commit/af5b287f19f808cd4d3f167068af99cb894abb36)

- **作者**: Maoqi Liu
- **时间**: 2026-10-20T08:03:37Z
- **提交信息**: [model, ops] feat: shared-prefix training for Qwen3.5 (#1266)

### [04e73c3](https://github.com/ByteDance-Seed/VeOmni/commit/04e73c3148c94c2853e76cca14cedda34d638257)

- **作者**: Coach257
- **时间**: 2026-10-20T08:01:53Z
- **提交信息**: [model, ops] feat: support context parallelism for qwen4_exp qsa attention (#1318)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2930
- **最后更新**: 2026-10-20T18:38:50Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Musisoul, STwangyingrui

## AI分析总结

**一、主要更新类型**  
本次提交以**性能优化**与**功能新增**为主：  
- 提交1 (`ec3d9c9`) 是针对特定硬件（L40S）的**推理性能优化**。  
- 提交2 (`74dee64`) 是新增功能，具体为“H3 draft and resample”。  

**二、关键变更点与项目方向的关系**  
- **L40S优化**：通过增加专属配置、复用静态图像条件、减少注意力填充和视频后处理开销，直接响应了LightX2V作为“轻量视频生成推理框架”的核心目标——提升推理效率与资源利用率。这体现了项目对**主流专业级GPU（如L40S）适配性**的重视。  
- **H3功能**：新增的“draft and resample”模块，暗示了项目在**生成管线或模型架构上**的扩展可能，旨在提供更丰富的生成控制或采样策略，符合框架向更复杂、可控视频生成发展的方向。  

**三、对项目的影响和潜在意义**  
- **L40S优化**将直接提升用户在该硬件上的推理速度与吞吐量，降低延迟和显存占用，增强了项目在数据中心级场景的实用性与竞争力。  
- **H3功能**的引入为框架带来了新的生成能力，可能为用户提供更高质量或更多样化的视频输出选项，拓宽了应用范围。  

**四、值得关注的技术点**  
- **硬件感知优化**：针对特定GPU架构进行细致调优（如条件复用、填充缩减），是推理框架性能提升的典型实践。  
- **条件复用机制**：将静态图像条件在多个片段间复用，是减少重复计算、提升效率的有效思路。  
- **“draft and resample”设计**：可能涉及两阶段生成或细化采样流程，值得深入研究其实现细节和效果。  

**五、对项目发展的影响**  
结合README中“轻量视频生成推理框架”的定位，这些提交表明LightX2V正在从两个维度巩固其优势：  
1.  **纵向深化性能**：通过硬件特定优化，持续兑现“Light”（轻量、高效）的承诺，吸引更多追求部署效率的用户。  
2.  **横向拓展能力**：通过新增生成模块，增强框架的功能完整性，向更专业的视频生成工具演进。  
这有助于项目在快速发展的视频生成AI领域中，同时保持**技术领先性**与**实用价值**，推动其成为高效、灵活的视频生成解决方案。

## 详细提交记录

### [ec3d9c9](https://github.com/ModelTC/LightX2V/commit/ec3d9c935358c046bf74ceb9302771dc762e9331)

- **作者**: STwangyingrui
- **时间**: 2026-10-20T16:26:27Z
- **提交信息**: Optimize InfiniteTalk inference on L40S (#1641)

Add a tuned L40S configuration, reuse static image conditioning across
segments, and reduce audio-attention padding and local video
finalization overhead.

### [74dee64](https://github.com/ModelTC/LightX2V/commit/74dee641eed4e52cf7fe7f0c7149f5e1784ff617)

- **作者**: Musisoul
- **时间**: 2026-10-20T14:54:06Z
- **提交信息**: Feat: H3 draft and resample (#1638)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2307
- **最后更新**: 2026-10-20T16:08:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6728
- **最后更新**: 2026-10-21T02:51:20Z

## 提交统计

- **昨日提交总数**: 51
- **提交者数量**: 14
- **主要提交者**: Omer Ullman Argov, ameynaik-hub, eigen

## AI分析总结

# FlashInfer 昨日提交合并分析（51 个提交）

## 一、主要更新类型
本次变更以**性能优化**与**Bug 修复**为主，辅以大规模代码清理、新功能融合与 CI 改进。性能提交覆盖 Cake 系列内核（QK RMSNorm+RoPE、FMHA、Sage-FP8 稀疏注意力、SVDQuant GEMM、Mamba2 SSD、MegaMoE、DeepSeek-V3.2 indexer 等）以及 RMSNorm 反向、causal conv1d 反向等训练算子；修复集中于 Blackwell/Rubin 代际（SM100a/SM103a/SM107、TMEM、GDN）新硬件指令族的并发安全与 PTX 合规问题；新增通信-计算融合算子 `cake_gemm_allreduce`、GDN 前缀缓存物化内核、DSA NoPE 变体与 Ulysses 序列并行 NVLink 通信核族。

## 二、关键变更
**1. 跨 CTA 异步竞态修复**：2-CTA 集群 GEMM 中成员 CTA 的 load warp 提前退出，而 leader 多播的 `tcgen05.commit` 仍在飞行，对已退出 CTA 的共享内存做异步操作属 PTX 未定义行为。采用 CUTLASS 式 **producer tail**（tile 循环结束后按相位等待最后 ring-depth 个 stage 释放，未填充阶段直接通过）修复，零开销且 JIT 缓存随源码摘要自动失效。

**2. TMEM 寻址合规修复**：tcgen05 要求每 warp 只访问自身 lane 且地址一致，原代码依赖 ptxas 将操作数提入 uniform 寄存器的副作用。修复为每 warp 追加 lane 基址，消除对编译器未承诺行为的依赖。另有 `wait::ld` 缺失、阶段释放前缺 warp 同步、MoE 共享缓冲竞争等内存序问题修复，并附回归测试。

**3. 性能优化**：SVDQuant GEMM 相对 CUTLASS 快 1.04–1.29×，Sage-FP8 提速 1.30–1.40×，静态单波程序 1.06–1.24×；DeepSeek-V3.2 indexer 几何均值约 1.11×；causal conv1d 反向在 C≥2048 时提升约 19%；SM107 QkvNormRopeExchangeOverlap 24 个 shape 中 23 个提速；Rubin MegaMoE 融合 NVFP4 量化与路由准备；MoE 路由修复使长序列提速 3–4 倍。

**4. 功能融合与清理**：matmul 与 allreduce 合并为单 kernel 服务 TP decode；MoE workspace 将峰值内存从 3.5 GiB 降至 896 MiB，降低 vLLM 集成门槛；CAKE 内核家族 deslop 与 Kimi-K3 死代码删除合计净减约 7.5 万行，kernel 源码逐字节不变，API 与 JIT 规格保持兼容。

## 三、技术关注点
- PTX 引用严谨（§2.2.2 已退出 CTA 内存未定义、§9.7.18.6 commit 无顺序保证），指明集群异步多播与传统 CTA 内 barrier 的语义差异。
- producer tail 高度模板化，可推广至其他 ring-buffer 内核家族。
- "条件化快速路径"：静态单波程序按严格形状阈值启用、保证逐位相同输出；按形状分派最优程序并存选优。
- `cp.async.bulk` + `mbarrier` 环形缓冲持久化协作；L2 evict-first 流提示与寄存器门控策略切换。
- 严格基准方法学：CUPTI 计时、冷 L2、ABBA 轮次、配对中位数与几何均值，并理性回退收益不佳路径。
- CI 增加 skip-all 检测与覆盖率审计，应对内核数量爆炸。

## 四、项目影响
FlashInfer 正沿三条主线推进：以 Cake 自动生成后端冲击性能极限（自动生成内核已系统性超越自调优基线）、以密集正确性修复保障 Blackwell/Rubin 生产落地、以基础设施支撑多团队协作生态。项目已从单一推理内核库演进为**覆盖训练与推理全栈、跨多代 GPU 的自适应高性能内核基础设施**，在性能前沿与代码库健康度之间保持平衡，技术领先性与工程成熟度同步提升。

## 详细提交记录

### [49aa24f](https://github.com/flashinfer-ai/flashinfer/commit/49aa24fbc4b30a2ba0be61062342f891e8af2972)

- **作者**: eigen
- **时间**: 2026-10-20T23:53:00Z
- **提交信息**: perf(cake_fused_qk_rope_append): converge the BF16 fused QK RMSNorm + NeoX RoPE + paged KV append kernel and ship it as a vendorable package (#6887)

The Cake fused QK RMSNorm + NeoX RoPE + paged KV append kernel has two
variants, BF16 and FP8. This PR delivers the BF16 variant,
`cake_fused_qk_rmsnorm_rope_append_paged_kv_cache`, as a vendorable
package. Against the Cake version of this kernel currently on `main`
(built by FlashInfer's own JIT with the same CUDA 13.4 toolkit), the
geomean speedup over 28 shapes is 1.06 on H100, 1.07 on H200 and 1.14 on
B200, B300 and GB300; all rows are faster except H3 on H100 (0.9975).

In the `shape` column, heads = query/KV heads (head_dim 128), B =
requests, Q = new tokens per request (Q=1 is decode), ctx = tokens
already in the paged KV cache, p = page size, and norm = qk_norm_policy
(0: no RMSNorm, 1: RoPE then RMSNorm, 2: RMSNorm then RoPE).

**NVIDIA H100 80GB HBM3, `sm_90a`, CUDA 13.4, driver 535.216.03** (CUPTI
kernel time, cold L2, 10 %-trimmed mean of ≥ 900 samples per side)

| shape | main (µs) | this PR (µs) | speedup (main / this PR) |
|---|---:|---:|---:|
| D1 · 8/1 heads, B=1 Q=1 ctx=2048 p=64, norm 2 | 2.486 | 2.322 | 1.0709
|
| D2 · 8/1 heads, B=8 Q=1 ctx=2048 p=64, norm 2 | 2.459 | 2.292 | 1.0729
|
| D3 · 8/1 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 3.601 | 3.480 |
1.0348 |
| D4 · 8/1 heads, B=256 Q=1 ctx=2048 p=64, norm 2 | 5.064 | 4.712 |
1.0748 |
| E1 · 8/1 heads, B=32 Q=1 ctx=2048 p=16, norm 2 | 2.499 | 2.325 |
1.0748 |
| E2 · 8/1 heads, B=32 Q=1 ctx=2048 p=128, norm 2 | 2.778 | 2.680 |
1.0366 |
| E3 · 8/1 heads, B=32 Q=1 ctx=0 p=64, norm 2 | 2.594 | 2.373 | 1.0933 |
| E4 · 8/1 heads, B=8 Q=16 ctx=2047 p=64, norm 2 | 2.959 | 2.757 |
1.0730 |
| E5 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, caller-owned out_k/out_v, norm
2 | 2.579 | 2.421 | 1.0653 |
| E6 · 8/1 heads, B=16 Q=1–64 ctx=0–4095 (ragged) p=64, norm 2 | 4.225 |
4.029 | 1.0488 |
| H1 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 4.903 | 4.544 |
1.0789 |
| H2 · 64/8 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 5.117 | 4.849 |
1.0552 |
| H3 · 64/8 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 14.589 | 14.626 |
0.9975 |
| H4 · 64/8 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 4.434 | 4.303 |
1.0305 |
| M1 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 2.618 | 2.443 |
1.0718 |
| M1a · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 2.514 | 2.401 |
1.0472 |
| M1b · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 2.679 | 2.430 |
1.1024 |
| M2 · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 2.974 | 2.756 |
1.0789 |
| M2a · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 0 | 2.893 | 2.720 |
1.0639 |
| M2b · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 1 | 3.042 | 2.768 |
1.0991 |
| P1 · 8/1 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 3.011 | 2.828 |
1.0647 |
| P2 · 8/1 heads, B=4 Q=64 ctx=2048 p=64, norm 2 | 3.106 | 2.937 |
1.0574 |
| P3 · 8/1 heads, B=32 Q=8 ctx=2048 p=64, norm 2 | 3.174 | 2.999 |
1.0582 |
| X1 · 8/1 heads, B=32 Q=1 ctx=32768 p=64, norm 2 | 2.587 | 2.430 |
1.0649 |
| X2 · 8/1 heads, B=512 Q=1 ctx=2048 p=64, norm 2 | 8.396 | 8.186 |
1.0257 |
| X3 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 4.888 | 4.521 |
1.0812 |
| X4 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 4.956 | 4.641 |
1.0680 |
| X5 · 8/1 heads, B=32 Q=1 ctx=2048 p=32, norm 2 | 2.531 | 2.384 |
1.0615 |
| **geomean (28 rows)** | — | — | **1.0623** |

**NVIDIA H200, `sm_90a`, CUDA 13.4, driver 615.71.09** (CUPTI kernel
time, cold L2, 10 %-trimmed mean of ≥ 900 samples per side)

| shape | main (µs) | this PR (µs) | speedup (main / this PR) |
|---|---:|---:|---:|
| D1 · 8/1 heads, B=1 Q=1 ctx=2048 p=64, norm 2 | 2.268 | 2.075 | 1.0934
|
| D2 · 8/1 heads, B=8 Q=1 ctx=2048 p=64, norm 2 | 2.394 | 2.185 | 1.0958
|
| D3 · 8/1 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 3.377 | 3.255 |
1.0376 |
| D4 · 8/1 heads, B=256 Q=1 ctx=2048 p=64, norm 2 | 4.673 | 4.180 |
1.1177 |
| E1 · 8/1 heads, B=32 Q=1 ctx=2048 p=16, norm 2 | 2.340 | 2.192 |
1.0674 |
| E2 · 8/1 heads, B=32 Q=1 ctx=2048 p=128, norm 2 | 2.791 | 2.599 |
1.0738 |
| E3 · 8/1 heads, B=32 Q=1 ctx=0 p=64, norm 2 | 2.494 | 2.262 | 1.1023 |
| E4 · 8/1 heads, B=8 Q=16 ctx=2047 p=64, norm 2 | 2.879 | 2.674 |
1.0763 |
| E5 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, caller-owned out_k/out_v, norm
2 | 2.482 | 2.303 | 1.0775 |
| E6 · 8/1 heads, B=16 Q=1–64 ctx=0–4095 (ragged) p=64, norm 2 | 3.899 |
3.689 | 1.0569 |
| H1 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 4.384 | 4.039 |
1.0853 |
| H2 · 64/8 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 4.691 | 4.401 |
1.0660 |
| H3 · 64/8 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 11.579 | 11.524 |
1.0048 |
| H4 · 64/8 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 3.991 | 3.942 |
1.0124 |
| M1 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 2.498 | 2.319 |
1.0773 |
| M1a · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 2.411 | 2.272 |
1.0611 |
| M1b · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 2.573 | 2.320 |
1.1093 |
| M2 · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 2.880 | 2.658 |
1.0834 |
| M2a · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 0 | 2.774 | 2.592 |
1.0706 |
| M2b · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 1 | 2.974 | 2.679 |
1.1100 |
| P1 · 8/1 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 2.912 | 2.693 |
1.0811 |
| P2 · 8/1 heads, B=4 Q=64 ctx=2048 p=64, norm 2 | 3.032 | 2.832 |
1.0707 |
| P3 · 8/1 heads, B=32 Q=8 ctx=2048 p=64, norm 2 | 3.120 | 2.894 |
1.0779 |
| X1 · 8/1 heads, B=32 Q=1 ctx=32768 p=64, norm 2 | 2.466 | 2.305 |
1.0697 |
| X2 · 8/1 heads, B=512 Q=1 ctx=2048 p=64, norm 2 | 7.174 | 6.699 |
1.0708 |
| X3 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 4.350 | 4.000 |
1.0877 |
| X4 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 4.468 | 4.161 |
1.0738 |
| X5 · 8/1 heads, B=32 Q=1 ctx=2048 p=32, norm 2 | 2.413 | 2.269 |
1.0633 |
| **geomean (28 rows)** | — | — | **1.0738** |

**NVIDIA B200, `sm_100a`, CUDA 13.4, driver 615.71.09** (CUPTI kernel
time, cold L2, 10 %-trimmed mean of ≥ 900 samples per side)

| shape | main (µs) | this PR (µs) | speedup (main / this PR) |
|---|---:|---:|---:|
| D1 · 8/1 heads, B=1 Q=1 ctx=2048 p=64, norm 2 | 3.504 | 2.893 | 1.2109
|
| D2 · 8/1 heads, B=8 Q=1 ctx=2048 p=64, norm 2 | 3.571 | 3.100 | 1.1519
|
| D3 · 8/1 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 3.718 | 3.668 |
1.0136 |
| D4 · 8/1 heads, B=256 Q=1 ctx=2048 p=64, norm 2 | 4.588 | 4.290 |
1.0696 |
| E1 · 8/1 heads, B=32 Q=1 ctx=2048 p=16, norm 2 | 3.572 | 3.074 |
1.1620 |
| E2 · 8/1 heads, B=32 Q=1 ctx=2048 p=128, norm 2 | 3.817 | 3.200 |
1.1927 |
| E3 · 8/1 heads, B=32 Q=1 ctx=0 p=64, norm 2 | 3.701 | 3.083 | 1.2003 |
| E4 · 8/1 heads, B=8 Q=16 ctx=2047 p=64, norm 2 | 3.755 | 3.220 |
1.1661 |
| E5 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, caller-owned out_k/out_v, norm
2 | 3.693 | 3.140 | 1.1760 |
| E6 · 8/1 heads, B=16 Q=1–64 ctx=0–4095 (ragged) p=64, norm 2 | 4.558 |
4.137 | 1.1018 |
| H1 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 4.110 | 3.817 |
1.0766 |
| H2 · 64/8 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 4.764 | 4.181 |
1.1394 |
| H3 · 64/8 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 8.432 | 8.050 |
1.0474 |
| H4 · 64/8 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 4.793 | 4.078 |
1.1754 |
| M1 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 3.710 | 3.168 |
1.1710 |
| M1a · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 3.155 | 3.074 |
1.0261 |
| M1b · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 3.759 | 3.163 |
1.1882 |
| M2 · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 3.808 | 3.208 |
1.1869 |
| M2a · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 0 | 3.344 | 3.165 |
1.0567 |
| M2b · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 1 | 3.781 | 3.263 |
1.1586 |
| P1 · 8/1 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 3.946 | 3.485 |
1.1323 |
| P2 · 8/1 heads, B=4 Q=64 ctx=2048 p=64, norm 2 | 3.937 | 3.428 |
1.1483 |
| P3 · 8/1 heads, B=32 Q=8 ctx=2048 p=64, norm 2 | 3.946 | 3.397 |
1.1614 |
| X1 · 8/1 heads, B=32 Q=1 ctx=32768 p=64, norm 2 | 3.789 | 3.164 |
1.1975 |
| X2 · 8/1 heads, B=512 Q=1 ctx=2048 p=64, norm 2 | 6.621 | 5.220 |
1.2683 |
| X3 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 4.004 | 3.686 |
1.0863 |
| X4 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 4.067 | 3.895 |
1.0441 |
| X5 · 8/1 heads, B=32 Q=1 ctx=2048 p=32, norm 2 | 3.641 | 3.157 |
1.1531 |
| **geomean (28 rows)** | — | — | **1.1362** |

**NVIDIA B300 SXM6 AC, `sm_103a`, CUDA 13.4, driver 580.126.09** (CUPTI
kernel time, cold L2, 10 %-trimmed mean of ≥ 900 samples per side)

| shape | main (µs) | this PR (µs) | speedup (main / this PR) |
|---|---:|---:|---:|
| D1 · 8/1 heads, B=1 Q=1 ctx=2048 p=64, norm 2 | 3.622 | 2.993 | 1.2103
|
| D2 · 8/1 heads, B=8 Q=1 ctx=2048 p=64, norm 2 | 3.460 | 2.921 | 1.1846
|
| D3 · 8/1 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 3.445 | 3.363 |
1.0244 |
| D4 · 8/1 heads, B=256 Q=1 ctx=2048 p=64, norm 2 | 4.299 | 3.969 |
1.0831 |
| E1 · 8/1 heads, B=32 Q=1 ctx=2048 p=16, norm 2 | 3.338 | 2.891 |
1.1544 |
| E2 · 8/1 heads, B=32 Q=1 ctx=2048 p=128, norm 2 | 3.639 | 2.989 |
1.2178 |
| E3 · 8/1 heads, B=32 Q=1 ctx=0 p=64, norm 2 | 3.436 | 2.862 | 1.2003 |
| E4 · 8/1 heads, B=8 Q=16 ctx=2047 p=64, norm 2 | 3.478 | 2.991 |
1.1628 |
| E5 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, caller-owned out_k/out_v, norm
2 | 3.447 | 2.938 | 1.1733 |
| E6 · 8/1 heads, B=16 Q=1–64 ctx=0–4095 (ragged) p=64, norm 2 | 4.260 |
3.817 | 1.1160 |
| H1 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 3.827 | 3.533 |
1.0832 |
| H2 · 64/8 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 4.490 | 3.937 |
1.1407 |
| H3 · 64/8 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 7.969 | 7.610 |
1.0472 |
| H4 · 64/8 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 4.516 | 3.881 |
1.1634 |
| M1 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 3.449 | 2.958 |
1.1659 |
| M1a · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 2.993 | 2.869 |
1.0433 |
| M1b · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 3.468 | 2.936 |
1.1811 |
| M2 · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 3.510 | 2.928 |
1.1988 |
| M2a · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 0 | 3.024 | 2.875 |
1.0517 |
| M2b · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 1 | 3.486 | 2.978 |
1.1706 |
| P1 · 8/1 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 3.676 | 3.221 |
1.1412 |
| P2 · 8/1 heads, B=4 Q=64 ctx=2048 p=64, norm 2 | 3.621 | 3.102 |
1.1674 |
| P3 · 8/1 heads, B=32 Q=8 ctx=2048 p=64, norm 2 | 3.651 | 3.110 |
1.1741 |
| X1 · 8/1 heads, B=32 Q=1 ctx=32768 p=64, norm 2 | 3.488 | 2.977 |
1.1719 |
| X2 · 8/1 heads, B=512 Q=1 ctx=2048 p=64, norm 2 | 6.250 | 4.873 |
1.2827 |
| X3 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 3.751 | 3.391 |
1.1060 |
| X4 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 3.804 | 3.599 |
1.0569 |
| X5 · 8/1 heads, B=32 Q=1 ctx=2048 p=32, norm 2 | 3.376 | 2.912 |
1.1595 |
| **geomean (28 rows)** | — | — | **1.1424** |

**NVIDIA GB300, `sm_103a`, CUDA 13.4, driver 580.159.03** (CUPTI kernel
time, cold L2, 10 %-trimmed mean of ≥ 900 samples per side)

| shape | main (µs) | this PR (µs) | speedup (main / this PR) |
|---|---:|---:|---:|
| D1 · 8/1 heads, B=1 Q=1 ctx=2048 p=64, norm 2 | 3.487 | 2.900 | 1.2026
|
| D2 · 8/1 heads, B=8 Q=1 ctx=2048 p=64, norm 2 | 3.403 | 2.888 | 1.1783
|
| D3 · 8/1 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 3.377 | 3.314 |
1.0190 |
| D4 · 8/1 heads, B=256 Q=1 ctx=2048 p=64, norm 2 | 4.077 | 3.692 |
1.1043 |
| E1 · 8/1 heads, B=32 Q=1 ctx=2048 p=16, norm 2 | 3.257 | 2.833 |
1.1497 |
| E2 · 8/1 heads, B=32 Q=1 ctx=2048 p=128, norm 2 | 3.562 | 2.924 |
1.2183 |
| E3 · 8/1 heads, B=32 Q=1 ctx=0 p=64, norm 2 | 3.365 | 2.847 | 1.1823 |
| E4 · 8/1 heads, B=8 Q=16 ctx=2047 p=64, norm 2 | 3.421 | 2.895 |
1.1817 |
| E5 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, caller-owned out_k/out_v, norm
2 | 3.385 | 2.884 | 1.1739 |
| E6 · 8/1 heads, B=16 Q=1–64 ctx=0–4095 (ragged) p=64, norm 2 | 4.171 |
3.765 | 1.1076 |
| H1 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 3.754 | 3.450 |
1.0881 |
| H2 · 64/8 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 4.409 | 3.792 |
1.1628 |
| H3 · 64/8 heads, B=128 Q=1 ctx=2048 p=64, norm 2 | 7.723 | 7.351 |
1.0506 |
| H4 · 64/8 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 4.417 | 3.783 |
1.1678 |
| M1 · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 2 | 3.347 | 2.864 |
1.1688 |
| M1a · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 2.943 | 2.841 |
1.0360 |
| M1b · 8/1 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 3.454 | 2.896 |
1.1927 |
| M2 · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 2 | 3.462 | 2.884 |
1.2004 |
| M2a · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 0 | 2.986 | 2.827 |
1.0563 |
| M2b · 8/1 heads, B=8 Q=16 ctx=2048 p=64, norm 1 | 3.450 | 2.910 |
1.1856 |
| P1 · 8/1 heads, B=1 Q=128 ctx=2048 p=64, norm 2 | 3.622 | 3.182 |
1.1383 |
| P2 · 8/1 heads, B=4 Q=64 ctx=2048 p=64, norm 2 | 3.561 | 3.065 |
1.1620 |
| P3 · 8/1 heads, B=32 Q=8 ctx=2048 p=64, norm 2 | 3.603 | 3.033 |
1.1881 |
| X1 · 8/1 heads, B=32 Q=1 ctx=32768 p=64, norm 2 | 3.423 | 2.910 |
1.1762 |
| X2 · 8/1 heads, B=512 Q=1 ctx=2048 p=64, norm 2 | 6.053 | 4.794 |
1.2627 |
| X3 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 0 | 3.637 | 3.320 |
1.0954 |
| X4 · 64/8 heads, B=32 Q=1 ctx=2048 p=64, norm 1 | 3.696 | 3.544 |
1.0431 |
| X5 · 8/1 heads, B=32 Q=1 ctx=2048 p=32, norm 2 | 3.288 | 2.853 |
1.1523 |
| **geomean (28 rows)** | — | — | **1.1428** |

The other Cake variant, FP8
(`cake_fused_qk_rmsnorm_rope_quantize_fp8_append_paged_kv_cache`),
quantizes Q to FP8 E4M3 with a dynamic per-token/per-head or static
scale, quantizes K/V with scalar scales into an FP8 E4M3 cache and
validates `q_indptr` on device; it is delivered in a separate PR, and
both variants ship on `sm_90a`, `sm_100a` and `sm_103a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a self-contained backend for fused QK normalization, rotary
embeddings, BF16 output, and paged KV-cache appends.
* Added architecture-aware kernel selection, launch planning,
validation, and caller-provided output buffers.
* Added support for multiple GPU architectures and packaged backend
sources.

* **Benchmarking**
* Expanded benchmarks for ragged workloads, configurable execution
settings, multiple baselines, and richer results.

* **Tests**
* Added coverage for backend loading, launch planning, deterministic
execution, buffer reuse, API behavior, and supported hardware.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [75b30ff](https://github.com/flashinfer-ai/flashinfer/commit/75b30ffdbf8c4413b26ff12ba7cb4c6c7d5f4d46)

- **作者**: eigen
- **时间**: 2026-10-20T23:35:58Z
- **提交信息**: deslop(cake_megamoe): drop the SM120 device-part byte copy and the uncalled EP16 host helper (#6898)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR deletes dead generated code from two Cake MegaMoE families
covered by #6664:
- **SM120 MXFP4 MegaMoE backend.** `part002.cuh` is a 1,090-line byte
copy of `part001.cuh`. The PR deletes it, points its only include site
at `part001.cuh` and re-seals the manifest by hand.
- **Experimental EP16 MXFP8 MegaMoE.** The generated binding defines a
device-count helper that nothing calls. The PR deletes it, along with a
pre-commit exclude branch that matches no file.

Both changes are mechanical. This PR does not touch the SM90 family or
the top-k reducer.

Behaviour changes:
- **SM120 device-module names.** The device-module identity hashes the
device sources, so every SM120 `copier` / `nocopier` device module gets
a new name once. This includes the two AOT `nocopier` modules. The
binding module keeps its name. On the first run after the change, the
device modules recompile once and produce the same cubins.
- **Manifest re-sealed by hand.** The part002 record is removed and the
part005 digest is recomputed. The exporter's provenance digests are kept
as written. The loader sees a consistent manifest.
- **EP16 traceback line numbers.** When a host check fails in the EP16
binding, the traceback reports a line number 1 or 21 lower than before.
Message texts, exception kinds, the file name, exports and device code
do not change.

No reachable input changes a launch, an argument, an export, a module
ABI or a test result.

## Changes

Base: upstream main `8dc1163fb` (2026-10-20). Head:
`031ce29d9e4dace93190db7d9ae44a0e815e9ecf` (2 commits). 5 files, +7 /
-1,119.

For every reachable input, both changes are mechanical and preserve
behaviour. The two edited generated sources are `part005.cuh` and the
EP16 binding. In each one, this disclosure line replaces the "do not
edit" claim:

`// Generated by Cake for FlashInfer. Exporter output, hand-edited here
pending exporter support.`

The untouched generated files keep their claim.

### Commit 1 (ce00bd960) - cake_sm120_megamoe: drop part002, a byte copy
of part001, and re-seal (3 files, +4 / -1,095)

Package `flashinfer/moe_ep/kernel_src/sm120/cake_mxfp4_megamoe`: the
`sm120_mxfp4_mxfp8_bf16_cake` MoE-EP backend, which runs on SM120 (CC
12.0) only.

**The copy.** This commit deletes
`src/cake_sm120_megamoe_kernel_part002.cuh`. The file has 1,090 lines
and is byte-identical to `part001.cuh` (same sha256): 0 code lines,
1,072 preprocessor directives, 258 `#error` lines.

**Why one file can serve both include sites:**
- At the base, part001 was included only at `part003.cuh:20`, under `#if
MOE_INSTANCE == 0`. That include sits in the shared-expert = 0 arm of
the `#if MOE_SHARED_EXPERT` chain that opens at `part005.cuh:132`.
- part002 was included only at `part005.cuh:136`, under the `#elif
MOE_SHARED_EXPERT == 1` arm.
- `MOE_SHARED_EXPERT` is one compile definition per translation unit, so
no unit ever included both files.
- At head, `part005.cuh:136` includes part001, and each unit includes
part001 at most once. No `#pragma once` is needed: the tree has none and
uses no `__FILE__`, `__LINE__` or `#line`.

**`part005.cuh`.** Besides the include at line 136, lines 17-18 are
reworded. They now hold the disclosure line and the kept sentence about
the loader's digest check. The file is 3,636 lines before and after.
After include expansion, the device text is 44,148 lines on both sides.
For every define set it is identical except for these two comment lines.

**Manifest.** `src/cake_sm120_megamoe_manifest.json` is re-sealed by
hand:
- The part002 record is removed, leaving 12 device sources. The part005
digest is replaced by the recomputed value. No other field changes.
- The manifest round-trips byte for byte through the loader's
serialisation, and `read_manifest()` verifies all 18 seals.
- The exporter's provenance digests (`single_file_sha256`,
`unrenamed_sha256`, `geometry_module_sha256`, `generator_commit`) are
kept as written. They describe the exporter's input, which this change
does not alter.

**Disclosed: module names.** The device-module identity hashes
`device.sources`, so every `cake_sm120_megamoe_{copier,nocopier}_<20
hex>` module name changes once. The AOT `nocopier` modules change as
follows:

| AOT device module | Base | Head |
|---|---|---|
| EP4 `nocopier` | `…_8791b1811417654d196f` | `…_99d979a0197363dccdba` |
| EP8 `nocopier` | `…_6901f476443a7cb78fb5` | `…_e2758fb86e9a46d36ad3` |

The binding module `cake_sm120_megamoe_binding_7d5fc70247b391e28fd7`
keeps its name. On the first run after the change, the device modules
recompile once and produce the same cubins (see Validation).
`gen_cake_sm120_megamoe_aot_modules()` delivers the two AOT device
modules under the new names. Nothing in the repository pins the old
names.

### Commit 2 (031ce29d9) - cake_mxfp8_megamoe_ep16: drop the uncalled
device-count helper (2 files, +3 / -24)

Package `flashinfer/experimental/cake_mxfp8_megamoe_ep16`: the
experimental EP16 MXFP8 MegaMoE, CUDA backend binding.

- **Binding.** The generated binding is
`csrc/cake_mxfp8_megamoe_ep16/cake_mxfp8_megamoe_ep16_seq_b6463fb4cca601f89fce_binding.cu`.
It loses three things:
- the 19-line `inline int64_t CakeDeviceMultiprocessorCount(int)`
helper, a device query cached with a mutex and an atomic, which has 0
callers anywhere in the repository;
  - the helper's blank line;
  - `#include <atomic>`, which nothing else in the unit uses.

The "do not edit" claim on line 16 becomes the disclosure line. The
exports (`__tvm_ffi_run`, `__tvm_ffi_setup_tma`), the three kernel
references and the device code do not change.
- **pre-commit config.** In `.pre-commit-config.yaml` (lines 52-53), the
`check-added-large-files` exclude loses the branch
`kernels/fused_(?:cta0|all_ctas)\.py`. That branch has matched no file
since the round-1 CuTe source fold. The comment is reworded to describe
the branch that remains.
- **Disclosed: traceback line numbers.** The preprocessed binding text
shifts. Every `TVM_FFI_CHECK` site below the removed lines moves up: by
1 line for the two device-scope checks, and by 21 lines for the 149
checks after the helper. As a result, tracebacks from the binding's host
checks report smaller line numbers. Message texts, exception kinds, the
file name, exports and device code do not change. An existing JIT cache
recompiles the binding unit once, under the same module name.

## Validation

All rows ran on GB300 (CUDA 13). Every SM120 and SM100 row is
compile-only, because a cubin or preprocessed-text comparison needs no
SM120 GPU. A B200 cross-check of the SM100 host row is optional and not
part of this PR.

- SM120 (compute capability 12.0) device gate, 8 preprocessed-text rows
+ 8 cubin/SASS rows: all 16 rows pass. The 8 preprocessed-text rows are
identical after dropping line markers (the two rows through
`part005.cuh:136` carry part002 line markers at the base and part001
markers at head; the control row carries part001 on both sides; the raw
texts are byte-identical after substituting the one file name). The 8
cubin rows, compiled in one environment on both sides, have equal cubin
sha256, identical SASS after masking addresses and encodings, and
identical resource usage. One caveat the gate had to control for: the
compiler's output for this source depends on the build environment
(input path, working directory and temporary directory, which it hashes
into internal symbol names); for the `m128_copier` instance that also
moves code layout (a few padding instructions and branch displacements).
Compiled in different environments the base and head cubins differ in
exactly that way; compiled in one environment they are byte-equal
- **Rows.** Each row pairs one of the shim's own define sets with a
kernel instance that set builds (`m128_nocopier`, `m64_nocopier`,
`m128_copier`, `m64_copier`). The define sets are the two AOT points
(EP4, EP8), the qualified shared-expert EP4 point of the host tests, and
a shared-expert = 0 control.
- **Coverage.** Two rows reach `part005.cuh:136` (part002 at the base,
part001 at head). One row is the negative control through
`part003.cuh:20`. Five rows reach neither file, because the AOT builds
are untouched.
- **Preprocessed-text rows.** The `nvcc` preprocessor output must be
identical after dropping line markers. Equivalently, it must be
byte-identical after replacing the file name part002 with part001 in the
base output.
- **Cubin rows.** Each row compiles with the shim's exact flag set and
compile definitions. It passes when the cubin sha256 is equal, the
`cuobjdump` SASS listing is identical after masking addresses and
encodings, and resource usage is identical.
- EP16 binding host gate, 2 rows (SM100 / CC 10.0 and SM103 / CC 10.3,
compile-only): both rows pass: the binding object's device SASS and
resource usage are identical; the exported global symbol sets are
identical; the preprocessed text is identical after the declared
normalisation, with exactly the 151 shifted check-site pairs on each row
(the base's 153 sites minus the 2 inside the removed helper); the only
text that changes above the first declaration is the expansion of the
dropped `<atomic>` include.
- Both sides compile the binding with the loader's flags. A row passes
when all of these hold:
- The device SASS of the binding object (the TMA descriptor upload
kernels) and its resource usage are identical.
- The exported symbol sets are identical. The removed helper was never
exported.
- The preprocessed text is identical after the declared normalisation.
That normalisation covers exactly these items: line markers, blank
lines, adjacent string literals, the helper block deleted from the base
text, and the 151 shifted `__FILE__` / `__LINE__` pairs at check sites.
- SM120 module build and names: all pass. `read_manifest()` at head
lists 12 device sources and no part002; the 8 device-module names equal
the expected renamed set and the AOT list is the unchanged binding
module plus the two renamed `nocopier` modules. The three AOT-shaped
SM120 device modules build compile-only under their new names (6
cubins). For every one of the 6 cubins, the base text compiled in the
module build's own environment (same wrapper file, working directory and
temporary directory, the base tree's headers) is byte-equal to the head
cubin; for the 5 cubins with a gate row, the loader's compile command
run on the gate's staged text in the gate's environment reproduces the
gate's head cubin byte for byte, and the module build's cubin has
identical SASS (addresses and encodings masked) and resource usage to
the gate's. Both EP16 modules, `cake_mxfp8_megamoe_ep16_sm_100a` and
`_sm_103a`, build through the loader and load: the two exports are
present, the three device kernels are in the embedded SASS, and no
device-count helper symbol remains
  - At head, `read_manifest()` lists 12 device sources and no part002.
- The 8 device-module names at head match the expected renamed set. The
AOT list is the unchanged binding module plus the two renamed `nocopier`
modules.
- The three AOT-shaped SM120 device modules build compile-only under
their new names. 5 of their 6 cubins are compared with the gate's head
cubins. The sixth, `m64_copier` of the EP4 copier module, has no gate
row and is only built.
- EP16 module build and load (SM100 + SM103): included in all pass.
`read_manifest()` at head lists 12 device sources and no part002; the 8
device-module names equal the expected renamed set and the AOT list is
the unchanged binding module plus the two renamed `nocopier` modules.
The three AOT-shaped SM120 device modules build compile-only under their
new names (6 cubins). For every one of the 6 cubins, the base text
compiled in the module build's own environment (same wrapper file,
working directory and temporary directory, the base tree's headers) is
byte-equal to the head cubin; for the 5 cubins with a gate row, the
loader's compile command run on the gate's staged text in the gate's
environment reproduces the gate's head cubin byte for byte, and the
module build's cubin has identical SASS (addresses and encodings masked)
and resource usage to the gate's. Both EP16 modules,
`cake_mxfp8_megamoe_ep16_sm_100a` and `_sm_103a`, build through the
loader and load: the two exports are present, the three device kernels
are in the embedded SASS, and no device-count helper symbol remains
- The `cake_mxfp8_megamoe_ep16_sm_100a` and `_sm_103a` modules both
build through the loader and load (`dlopen`). Each must have the two
exports, three kernel symbols and no device-count helper symbol.
- Tests (CPU, both the base and this branch, fresh JIT workspaces): all
pass with equal results on both trees (host-only tests, run on a GB300
node): `tests/moe_ep/test_sm120_w4a8_cake_host.py` 36 passed / 0 skipped
on both; `tests/experimental/test_cake_mxfp8_megamoe_ep16.py` with CUDA
hidden 95 passed / 2 skipped (the 16-rank torchrun test) on both
  - Expected on both trees:
- `tests/moe_ep/test_sm120_w4a8_cake_host.py`: 36 passed / 0 skipped.
- `tests/experimental/test_cake_mxfp8_megamoe_ep16.py` with CUDA hidden:
95 passed / 2 skipped. The two skips are the 16-rank torchrun test.
  - Base and branch results must be equal.
- CPU checks: all pass: pre-commit `--all-files` on both full checkouts
gives identical results (16 hooks: 15 passed, 1 skipped, 0 failed) and 0
failures on the 4 changed files; stale-reference searches at the
expected counts (`part002` 0 hits repo-wide, the device-count helper 0
under `flashinfer/experimental`, the removed exclude branch 0; the 35
remaining helper definitions in other bindings are untouched by design);
the disclosure line exactly once in each of the two touched generated
files and no "do not edit" in touched files; the re-sealed manifest
round-trips, lists 12 device sources without `part002`, every seal
verifies and only `device.sources` changed; test collection 36 / 97 on
both trees; commit messages: no banned words, trailer on both commits,
72 columns
- pre-commit on both full checkouts must give identical results. By the
repository's rule, the generated SM120 part stays excluded from
formatting. The manifest passes the standard hooks.
  - Stale-reference searches, each expecting 0 hits:
    - `part002`;
    - the device-count helper, under `flashinfer/experimental`;
    - the removed exclude branch.
- The disclosure line appears exactly once in each touched generated
file, and no touched file contains "do not edit".
  - The manifest seals verify.
  - Test collection gives 36 / 97 ids on both trees.
  - Commit message checks pass.

**Not run.** Two GPU suites are not part of this PR's validation. Each
has a proof of record:
- `bash tests/moe_ep/run_tests.sh mega_sm120_cake` (torchrun on 4 × RTX
PRO 6000 with the NCCL 2.30.7 device API). No four-GPU SM120 machine was
available for this PR. The proof of record for commit 1 is the gate's
bit-identical cubins for every reachable path, plus the module build and
the 36 host tests.
- The 16-rank EP16 GPU test was not run for this PR. The proof of record
for commit 2 is the two host rows (SASS, resource usage, preprocessed
text, exports), plus the module build and load.

## Not in this PR

- **The SM90 `FLASHINFER_SM90_CAKE_BF16_DEV_LAUNCHER` path.** This is
reachable behaviour gated by an environment variable. The issue's
precondition, a generator-side parity check between the exported and
in-process paths, is open. Question for the maintainers: does the Cake
generator CI run such a check for the SM90 GEMMs?
- **The EP16 CuTe DSL arm (about 17K lines).** This is a maintainer /
product decision and the open question of the round-1 issue. In its own
PR, the DSL arm measured 5.0-7.2 % faster on 16 × GB300.
- **SM90 `fc1_gated` → `fc1_gated_clamp(+inf)`.** This changes NaN
numerics and SASS. The `#if` alternative needs a re-seal of the SM90
manifest, which the exporter seals.
- **The unused SM90 `clamp_limit` parameter and the
one-binding-per-three-stages layout.** These are generated ABI and
sealed closure, so they are exporter work.
- **The SM120 `#error` ladder rewrite (about 7,900 lines), the phase
timestamps and the per-switch includes.** The timestamps involve device
lines, two ABI arguments and two buffers. All of this needs regeneration
that changes device text, SASS and ABI. The timestamps also need the
owner's confirmation.
- **One shared parametric top-k reducer**
(`csrc/cake_megamoe_topk_reduce` and the EP16 copy). This is a rewrite
that changes SASS, not an exact fold.
- **Host-template fixes.** These cover the device guard, the
function-local static shared-memory attribute, SM90 TMA descriptor
caching, and SM120 per-call argument packing and routing gather. They
are generator changes with behavioural effect.
- **The `max_tokens_per_rank in (256, 4096)` gate.** Widening it is a
maintainer decision. Before widening, it needs the bitwise B200 / B300
comparison at 512 / 1024 / 2048 that the issue describes.
- **The `prereduced_hilo` wire and the opt-in SM90 `FUSED_TAIL=0` /
`FUSED_DISPATCH=0` routes.** These are opt-in behaviour and need
maintainer approval.
- **Docs and benchmark options** (the repository's developer notes, the
MoE-EP runbook, `--combine-wire`). They describe things this PR keeps.
- **Generator requests** (requests, not PR changes):
  - stop emitting the device-count helper when nothing calls it;
  - emit the instance-0 part once instead of a byte copy;
- let the binding file-name digest and the manifest provenance follow
the next export.

Experimental test scope for CI:

```experimental-tests
tests/experimental/test_cake_mxfp8_megamoe_ep16.py
```

Part of #6664

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Bug Fixes**
- Corrected generated GPU kernel source selection for a supported
shared-expert configuration.
- Updated integrity metadata so runtime validation matches the corrected
kernel source.

- **Chores**
- Large-file checks now include previously excluded generated kernel
files.
- Refined generated-kernel metadata and removed unused internal support
code.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [849e8be](https://github.com/flashinfer-ai/flashinfer/commit/849e8be49ff27503ece16c27b54fcec2276ffdf8)

- **作者**: eigen
- **时间**: 2026-10-20T22:58:02Z
- **提交信息**: perf(cake_fmha): whole-tile static one-wave program for the BF16 head_dim-128 balanced DCP decode family (SM100a, SM103a) (#6122)

`cake_fmha` balanced DCP speculative-decode attention handles a paged KV
cache, context parallelism and several speculative q_len rows per
request. Cake ships it as three families, all with BF16 Q and each with
32-row and 64-row packed instances: BF16 KV cache at head_dim 128
(`dcp_spec_bf16_balanced`), E4M3 KV cache at head_dim 128
(`dcp_spec_bf16_fp8_balanced`) and E4M3 KV cache at head_dim 256
(`dcp_spec_bf16_fp8_d256_balanced`). This PR changes the BF16
head_dim-128 and E4M3 head_dim-256 families by adding programs to the
host `program` selector beside program 1, the device-planner program,
which is each family's default, the previous Cake version on FlashInfer
main and the baseline here. For BF16 head_dim 128 it adds programs 2-5.
Program 2, the whole-tile static one-wave program, runs when a single
request's block table keeps every (request, KV head) tile whole under
one static wave (at most 112 pages of 16 tokens for 8 KV heads on 148 or
152 SMs), so every CTA issues its tile from its block index without the
device planner. Programs 3-5 are its swapped-first-GEMM form for the
32-row instance and its early-issue forms, all selected on sm_100a,
while sm_103a runs program 2 for both instances. For E4M3 head_dim 256
it adds program 2, a plan-free static one-wave program, selected when
one static wave's speculative rows share a balanced row tile and a
per-architecture class table of (blocks per CTA, minimum q_len) admits
the row. Every other launch keeps program 1, and on every measured row
each program's output is bitwise identical to program 1's. On GB300 the
single-request rows speed up 1.138x for BF16 head_dim 128 (one request,
4096-token context, q_len 4: 11.07 µs to 9.73 µs) and 1.240x for E4M3
head_dim 256 (one request, 32768-token context, q_len 4, CUDA-graph
replay: 17.02 µs to 13.73 µs). The rows that still select program 1 run
the same program on both sides and measure 0.997x to 1.006x.

**BF16 KV cache, head_dim 128 (`dcp_spec_bf16_balanced`):** NVIDIA GB300
(sm_103a, 152 SMs), CUDA 13.3, paired kernel GPU time with L2 flushed
before each launch. Selected program 1 = device planner (unchanged), 2 =
whole-tile static one-wave. Speedup = program 1 time / this PR time.

| Shape | GB300 selected program | GB300 program 1 (µs) | GB300 this PR
(µs) | GB300 speedup |
|---|---|---|---|---|
| `perf_b1_s4096_q4_w4_r0` | 2 | 11.07 | 9.73 | 1.138x |
| `perf_b8_s4096_q4_w4_r0` | 1 | 14.53 | 14.53 | 1.000x |
| `perf_b64_s4096_q4_w4_r0` | 1 | 59.90 | 59.87 | 1.001x |
| `perf_b1_s16384_q8_w4_r0` | 1 | 16.00 | 15.97 | 1.002x |
| `perf_b8_s16384_q8_w4_r0` | 1 | 36.58 | 36.61 | 0.999x |
| `perf_b64_s16384_q8_w4_r0` | 1 | 176.22 | 176.13 | 1.001x |
| `perf_b8_s16383_q8_w4_r3_tail` | 1 | 36.48 | 36.48 | 1.000x |
| `dcp_bf16_agentx_b16_q4_cp4_r0` | 1 | 341.86 | 342.02 | 1.000x |
| `dcp_bf16_agentx_b16_q8_cp4_r3` | 1 | 347.26 | 347.33 | 1.000x |
| `dcp_bf16_random_128_65k_b64_q4_cp4_r0` | 1 | 312.42 | 312.19 | 1.001x
|
| `dcp_bf16_random_128_32k_b128_q4_cp4_r0` | 1 | 316.42 | 316.38 |
1.000x |

**E4M3 KV cache, head_dim 256 (`dcp_spec_bf16_fp8_d256_balanced`):**
NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.3, paired kernel GPU time with
L2 flushed before each launch. `_graph` rows report CUDA-graph replay
time and the `agentx` rows report plain launches. Selected program 1 =
device planner (unchanged), 2 = static one-wave. Speedup = program 1
time / this PR time.

| Shape | GB300 selected program | GB300 program 1 (µs) | GB300 this PR
(µs) | GB300 speedup |
|---|---|---|---|---|
| `prod_d256_b1_ctx32768_q4_cp4_graph` | 2 | 17.02 | 13.73 | 1.240x |
| `prod_d256_b8_ctx32768_q4_cp4_graph` | 1 | 20.86 | 20.77 | 1.005x |
| `prod_d256_b16_ctx32768_q4_cp4_graph` | 1 | 27.46 | 27.30 | 1.006x |
| `prod_d256_b32_ctx32768_q4_cp4_graph` | 1 | 40.26 | 40.35 | 0.998x |
| `prod_d256_b64_ctx32768_q4_cp4_graph` | 1 | 62.94 | 63.14 | 0.997x |
| `prod_d256_b128_ctx32768_q4_cp4_graph` | 1 | 99.74 | 99.87 | 0.999x |
| `prod_d256_b192_ctx32768_q4_cp4_graph` | 1 | 164.80 | 164.67 | 1.001x
|
| `prod_d256_b256_ctx32768_q4_cp4_graph` | 1 | 180.45 | 180.32 | 1.001x
|
| `prod_d256_b128_ctx32768_q1_cp4_graph` | 1 | 101.50 | 101.38 | 1.001x
|
| `prod_d256_b128_ctx32768_q2_cp4_graph` | 1 | 101.38 | 101.31 | 1.001x
|
| `prod_d256_b128_ctx32768_q3_cp4_graph` | 1 | 99.74 | 99.74 | 1.000x |
| `prod_d256_b128_ctx32768_q5_cp4_graph` | 1 | 130.88 | 130.91 | 1.000x
|
| `prod_d256_b128_ctx32768_q6_cp4_graph` | 1 | 131.30 | 131.68 | 0.997x
|
| `prod_d256_b128_ctx32768_q7_cp4_graph` | 1 | 131.49 | 131.39 | 1.001x
|
| `prod_d256_b128_ctx32768_q8_cp4_graph` | 1 | 132.45 | 132.42 | 1.000x
|
| `dcp_d256_agentx_b16_q4_cp4_r0` | 1 | 67.17 | 67.20 | 1.000x |
| `dcp_d256_agentx_b64_q4_cp4_r0` | 1 | 193.15 | 193.18 | 1.000x |

The kernel's other Cake variant, the E4M3 head_dim-128 balanced family
(`dcp_spec_bf16_fp8_balanced`, programs 0, 1 and 2), is unchanged by
this PR. All three families ship 32-row and 64-row packed instances and
ship on sm_100a and sm_103a only.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d1fec68](https://github.com/flashinfer-ai/flashinfer/commit/d1fec688fab5f64fe5473033bba1cf7373adebda)

- **作者**: Alex Ameen
- **时间**: 2026-10-20T22:18:47Z
- **提交信息**: ci: skip-all detection, cross-lane coverage, and GDN/KDA trace reference coverage (IKL-569) (#6256)

<!-- .github/pull_request_template.md -->

## 📌 Description

Detect CI runs that pass with zero meaningful test execution, addressing
IKL-569.

Two distinct failure modes are covered:

1. **All-skipped test files (requirements 1–3):** A changed test file
where every collected node was skipped on every CI lane. Example: PR
#5314 had 214 new SM100 test nodes, all skipped on H100.

2. **Missing numerical references (requirement 4):** GDN and KDA trace
definitions that lack a `reference` function or `check` comparator. A
skip-count check cannot detect a test that does not exist — these
definitions describe a kernel interface but the trace system has no
oracle to verify correctness against.

### Requirement mapping (IKL-569)

| Requirement | What | Implementation |
|---|---|---|
| **1** | Show passed/failed/skipped/executed counts per scope and lane
| `check_skip_all.py` summary table |
| **2** | Compare changed/added test files with results from all lanes |
`check_skip_all.py` cross-references PR diff against `run-summary.json`
from each lane |
| **3** | Fail or warn when all tests in a changed file are skipped on
every lane | `check_skip_all.py` emits GitHub annotations + step summary
warning (hard failure via `--fail`) |
| **4** | Check GDN/KDA trace reference coverage separately |
`check_trace_coverage.py` audits `tests/trace/fi_trace_out/` for missing
`reference`/`check` fields |

### Completion checks

| Check | What | How verified |
|---|---|---|
| **1** | Changed test file with only skipped results produces
warning/failure | `test_check_skip_all.py` synthetic XML tests |
| **2** | Report identifies affected files and skip causes | Skip
reasons extracted from JUnit XML `<skipped message="...">` |
| **3** | Trace signature check ≠ proof of numerical correctness |
`check_trace_coverage.py` requires `reference` + `check`, not just valid
JSON from `fi_trace()` |
| **4** | Record and fill missing GDN/KDA numerical checks | Trace
definitions updated with FP64 reference functions and standard check
comparators |

### Changes

**Skip-all detection (requirements 1–3)**

- **`scripts/pr_checks/check_skip_all.py`** — Cross-references the PR
diff against `run-summary.json` artifacts from each CI lane. Reports
changed test files where every node was skipped. Extracts skip reasons
from JUnit XML. Emits GitHub Actions annotations and step summary.
- **`pr-test.yml`** — Uploads `run-summary.json` alongside JUnit
artifacts; runs `check_skip_all.py` in the test-results-summary job.

**Trace reference coverage (requirement 4)**

- **`scripts/pr_checks/check_trace_coverage.py`** — Scans
`tests/trace/fi_trace_out/` for GDN and KDA definitions. Reports which
have `reference`, `check`, both, or neither. Exits non-zero when a
verified definition lacks coverage.
- **Trace definition updates** — Added `reference` and/or `check` to
definitions that were missing them (`recurrent_kda_q8_v16_d128`,
`gdn_decode_qk4_v8_d128`, `gdn_prefill_qk4_v8_d128`,
`packed_fused_kda_decode_q8_v16_d128`).

## 🔍 Related Issues

IKL-569

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

<!-- Not applicable — this PR does not touch experimental APIs or
backends. -->

## Reviewer Notes

- `check_skip_all.py` is **warning-only** by default. The `--fail` flag
exists for future enforcement once the team is comfortable with the
signal.
- `check_trace_coverage.py` exits non-zero only for definitions marked
`status:verified` that lack coverage. Experimental definitions produce
warnings only.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Quality Checks**
* Pull requests now receive a report when changed tests are skipped
across all test lanes, with findings highlighted in a pull request
comment.
* Trace-reference coverage gaps are reported during pull request checks.
Verified gaps receive error annotations; other gaps appear as warnings.
  * Test summaries flag skip-all findings and trace-coverage gaps.
* **Test Results**
* GPU test runs now provide downloadable JUnit results, including
separate results for GPU shards, retained for 14 days.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Alex Ameen <aameen@nvidia.com>
Co-authored-by: coderabbitai[bot] <136622811+coderabbitai[bot]@users.noreply.github.com>
Co-authored-by: Jonathan Dierksen <1507580+dierksen@users.noreply.github.com>

### [4e4c41d](https://github.com/flashinfer-ai/flashinfer/commit/4e4c41da67f6c463940e4c75d11207ce93d6c516)

- **作者**: eigen
- **时间**: 2026-10-20T22:11:49Z
- **提交信息**: perf(cake_sage): faster SM100/SM103 Sage-FP8 block-sparse attention and quantizers (#6872)

The Cake Sage-FP8 block-sparse attention backend
(`flashinfer/cake_sage_block_sparse_attention_backend`) has three kinds
of program. The first is the attention forward kernel: head_dim 128,
E4M3 Q/K/V with per-token Q scales, per-16-token K scales and
per-channel V scales, 64-row query blocks attending to selected 64-token
KV blocks (MHA or GQA), and BF16 output with optional LSE. The other two
are the fused QK quantizer with V amax (`quantize_qk_vamax`) and the V
quantizer (`quantize_v`). The attention kernel ships as one SM100/SM103
kernel and 20 SM120 specializations (RTX PRO 6000 class). This PR
updates the SM100/SM103 attention kernel (sm_100a on B200, sm_103a on
GB300) and ships it with both quantizers. It also moves the 20 SM120
specializations into the package without changing them, so they compile
to the same code as before. The baseline is the previous Cake version on
FlashInfer main (`bsa_attn_sm100_blk64_fwd(..., backend="cake")`).
Against that baseline, attention is 1.30–1.40× faster and the quantizers
are 1.23× faster.

Every shape uses S_q = S_k = 4096, head_dim 128, MHA and no LSE. `sel`
is how many of the 64 KV blocks (64 tokens each) each 64-row query block
selects. Q1 times the two quantizers together on B8 H32 S4096. It
reports the sum of its launches: the zero fill of the V-amax scratch and
the two quantizer kernels. Times are CUPTI kernel-time sums in ms (cold
L2, both sides in one process). For the attention rows, the previous
version's time includes its two launches (a descriptor upload and the
kernel), and this PR uses a single launch. Speedup = previous ÷ this PR.

**GB300 (sm_103a), CUDA 13.4**

| Shape | B | H | sel | Previous Cake (ms) | This PR (ms) | Speedup |
|---|---:|---:|---:|---:|---:|---:|
| A1 | 8 | 32 | 6 | 0.3892 | 0.2897 | 1.34× |
| A2 | 8 | 32 | 32 | 1.0926 | 0.8381 | 1.30× |
| A3 | 8 | 32 | 58 | 1.8138 | 1.3691 | 1.32× |
| A4 | 1 | 8 | 6 | 0.0219 | 0.0156 | 1.40× |
| A5 | 1 | 8 | 32 | 0.0482 | 0.0364 | 1.32× |
| A6 | 1 | 8 | 58 | 0.0747 | 0.0563 | 1.33× |
| Q1 (quantizers) | 8 | 32 | – | 0.2610 | 0.2127 | 1.23× |

Apart from the 20 SM120 attention specializations, Cake ships no other
variants of this kernel, its quantizers implement only the fused Sage
recipe (Q per token, K per 16 tokens, V per channel), and the family
ships on sm_100a, sm_103a and sm_120a.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [15c83f1](https://github.com/flashinfer-ai/flashinfer/commit/15c83f1c36f5468c6fdc49e8f7f8ede247705cbb)

- **作者**: Lain
- **时间**: 2026-10-20T22:03:21Z
- **提交信息**: feat(moe): Trtllm gen workspace size (#6825)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds a caller-owned workspace to the trtllm-gen fused-MoE APIs, the
trtllm-gen counterpart of `cutlass_fused_moe_workspace_size` /
`workspace_buffer=` (used by vllm-project/vllm#60570).

`trtllm_fused_moe_workspace_size` is implemented by adding a
`query_workspace_size` mode to each trtllm-gen moe call. It will not
execute the runner, but record the tensors allocated before the runner
call.

Test result:

Tested on B300, bf16 routed, 16384 tokens, H=7168, I=2048, 256 experts,
top-8, on B300, autotuning peak allocation drops to 896.8 MiB from
3,579.9 MiB (−2,683.1 MiB).

## 🔍 Related Issues

#4916

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


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added reusable workspace-buffer support for supported fused
Mixture-of-Experts operations and quantization modes.
  - Added an API to query required workspace size before execution.
- Workspace buffers can be reused across calls, with automatic fallback
when capacity is insufficient.
- Added validation for buffer size, device, layout, data type,
alignment, and unsupported distributed scenarios.

- **Documentation**
  - Documented the fused MoE workspace-size API.

- **Tests**
- Added coverage for sizing, reuse, fallback behavior, performance, and
invalid configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Siyuan Fu <siyuanf@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d8ddf1a](https://github.com/flashinfer-ai/flashinfer/commit/d8ddf1a36779ce83a166fb18802fdae7b3d2b4cb)

- **作者**: eigen
- **时间**: 2026-10-20T21:23:45Z
- **提交信息**: refactor(cake_grouped_mxfp8_quantize): regenerate the kernels and route the host through the in-tree program loader (#6868)

`grouped_mxfp8_quantize` quantizes a 2-D activation to MXFP8 with
per-group E8M0 scales. Cake has two variants of it: bfloat16 input and
float16 input. This PR delivers both, on sm_100a and sm_103a. The
baseline is the previous Cake version of the same kernel: the loader
shipped at FlashInfer main 23f3e8f6. Each variant was timed on one
shape. For BF16 the speedup is 0.983 on B200 (sm_100a) and 0.992 on
GB300 (sm_103a). For F16 it is 0.992 on B200 and 1.000 on GB300. Values
below 1.0 are slowdowns. The BF16 shape comes from the owner's shape
list. That list has no timed F16 shape, so the F16 row uses the kernel
test's benchmark shape.

### BF16 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| B=2 M=256 K=4096 (T=512) | 3.744 | 3.808 | 0.983 |

### F16 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new. The owner's shape list has no timed shape for this variant; the
row is the kernel test's benchmark shape.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| B=2 M=256 K=4096 (T=512) | 3.968 | 4.000 | 0.992 |

### BF16 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| B=2 M=256 K=4096 (T=512) | 3.744 | 3.776 | 0.992 |

### F16 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new. The owner's shape list has no timed shape for this variant; the
row is the kernel test's benchmark shape.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| B=2 M=256 K=4096 (T=512) | 3.648 | 3.648 | 1.000 |

Cake has no variants of this kernel other than these two; Cake ships it
on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added ahead-of-time grouped MXFP8 quantization support for BF16 and
FP16 on SM100a and SM103a GPUs.
- Added automatic selection and caching of device-specific quantization
programs.
- Added input validation for tensor types, devices, shapes, padding,
masks, and memory layout.
- Added launch-grid calculation for varied batch sizes and supported
block configurations.

- **Performance**
- Streamlined grouped MXFP8 quantization launches using preallocated
outputs and internal padding, reducing setup overhead.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [aacd0f1](https://github.com/flashinfer-ai/flashinfer/commit/aacd0f134f2a35eaea9ea534aa5b5b31534db449)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T20:44:20Z
- **提交信息**: fix(cake_minimax_h3): order the SM120 dense attention epilogue before the next Q TMA refill and close the ping-pong barrier (#6847)

**Proxy fence.** In the MiniMax-H3 dense attention kernel
(`csrc/cake_minimax_h3_dense_attention_sm120a.cu`), the epilogue stages
O in the Q shared-memory buffer through the generic proxy. The Q scaling
writes that buffer too, and the epilogue reads it back for the output
stores. The next work item's elected thread then refills the same buffer
with a TMA load, which writes through the async proxy. The kernel did
issue `fence.proxy.async.shared::cta`, but only at the start of the next
work item, after the end-of-item `__syncthreads()`. A thread's proxy
fence orders only that thread's own earlier accesses, so the other
warps' generic accesses were never ordered before the TMA refill. Every
thread now issues the fence after its last access of the buffer and
before the end-of-item barrier, and the fence at the start of the item
is removed.

**Ping-pong close.** The dense, FP8 varlen and NVFP4 varlen attention
kernels alternate two warp groups on named barriers 1 and 2. Group 1
pre-arrives on barrier 1 once before the persistent loop, so its
arrivals run one round ahead of group 0's syncs. Its last arrival
therefore forms a round that no group-0 `barrier.sync` joins, and the
CTA exits with that named-barrier round still open. Group 0 now runs one
more `barrier.sync 1, 256` after the persistent loop, which completes
the round.

**Code change (sm_120a SASS).**
- Dense: the fence moves to before the barrier, plus one `BAR.SYNC` and
one compare at kernel exit. Instruction count is unchanged.
- FP8 varlen: one `BAR.SYNC` and one compare at kernel exit.
- NVFP4 varlen: one `BAR.SYNC` and one compare at each of its two kernel
exits.

**Validation.** All three translation units compile for sm_120a. The
corresponding changes were validated on GB300 (sm_103a builds of the
same kernels):
- Correctness and compute-sanitizer racecheck/synccheck are clean.
- Timing is within ±0.35% of the unchanged kernels.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during attention processing to ensure
shared-memory operations complete reliably.
* Fixed barrier sequencing before cleanup and kernel exit, improving
stability across supported attention workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ec3bcf0](https://github.com/flashinfer-ai/flashinfer/commit/ec3bcf0301dac6455897d4a450115fdd8fea1bd3)

- **作者**: eigen
- **时间**: 2026-10-20T20:39:51Z
- **提交信息**: perf(cake_nvfp4_svdquant): converge the Cake NVFP4 SVDQuant GEMM backend and ship it as a vendorable package (#6878)

`flashinfer.mm_nvfp4_svdquant(..., backend="cake")` computes the NVFP4
SVDQuant GEMM `out = BF16(alpha * (deq(A) @ deq(B)^T + D @ L1^T) +
bias)`. In this kernel, A and B are NVFP4 (E2M1) with E4M3 block scales.
The low-rank D / L1, the bias and the output are BF16, and accumulation
is FP32. Its Cake backend has one data-type / layout variant, with two
fused forms (with and without the fused bias), across LoRA ranks 32 / 64
/ 96 / 128. This PR delivers that whole variant for sm_100a and sm_103a
as the vendorable package `flashinfer/cake_nvfp4_svdquant_gemm_backend`.
The package has 15 programs and replaces the 7 Cake programs shipped
before. All latencies are CUPTI kernel-active medians, with L2 cleared
before every launch. "Previous Cake" is `backend="cake"` on main at this
PR's base. "CUTLASS" is that backend's fastest autotuned tactic. Both
were measured in the same session as this PR.

**NVIDIA B200 (sm_100a), CUDA 13.4**

| M | N | K | rank | bias | previous Cake (µs) | CUTLASS (µs) | this PR
(µs) | speedup vs previous Cake | speedup vs CUTLASS |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 129 | 3072 | 3072 | 32 | 1 | 10.66 | 8.19 | 6.46 | 1.65 | 1.267 |
| 129 | 3072 | 3072 | 32 | 0 | 6.46 | 8.19 | 6.34 | 1.02 | 1.293 |
| 129 | 3072 | 3072 | 64 | 1 | 9.60 | 8.35 | 6.56 | 1.46 | 1.273 |
| 129 | 3072 | 3072 | 96 | 1 | 8.22 | 8.00 | 6.66 | 1.24 | 1.202 |
| 129 | 3072 | 3072 | 128 | 1 | 11.10 | 8.58 | 6.69 | 1.66 | 1.282 |
| 129 | 3072 | 3072 | 128 | 0 | 9.73 | 8.35 | 6.59 | 1.48 | 1.267 |
| 129 | 3072 | 12288 | 32 | 0 | 15.39 | 16.61 | 13.57 | 1.13 | 1.224 |
| 129 | 3072 | 12288 | 32 | 1 | 22.91 | 16.61 | 13.66 | 1.68 | 1.215 |
| 129 | 3072 | 12288 | 128 | 0 | 25.25 | 15.68 | 13.86 | 1.82 | 1.132 |
| 129 | 3072 | 12288 | 128 | 1 | 26.37 | 16.29 | 13.95 | 1.89 | 1.167 |
| 6912 | 3072 | 3072 | 32 | 1 | 84.29 | 31.78 | 30.46 | 2.77 | 1.043 |
| 6912 | 3072 | 3072 | 64 | 1 | 81.68 | 31.90 | 30.58 | 2.67 | 1.043 |
| 6912 | 3072 | 3072 | 96 | 1 | 68.48 | 33.47 | 32.29 | 2.12 | 1.037 |
| 6912 | 3072 | 3072 | 128 | 1 | 91.55 | 33.50 | 32.74 | 2.80 | 1.023 |
| 6912 | 3072 | 12288 | 32 | 1 | 196.82 | 90.78 | 84.21 | 2.34 | 1.078 |
| 6912 | 3072 | 12288 | 128 | 1 | 231.50 | 93.17 | 86.40 | 2.68 | 1.078
|
| 4096 | 3072 | 3072 | 32 | 1 | 55.94 | 21.92 | 20.58 | 2.72 | 1.065 |
| 4096 | 3072 | 12288 | 32 | 1 | 131.14 | 58.61 | 56.10 | 2.34 | 1.045 |
| 4096 | 12288 | 3072 | 32 | 1 | 195.73 | 63.10 | 60.05 | 3.26 | 1.051 |
| 6889 | 3072 | 3072 | 32 | 1 | 84.26 | 31.81 | 30.67 | 2.75 | 1.037 |
| 6889 | 3072 | 12288 | 32 | 1 | 197.10 | 90.88 | 84.18 | 2.34 | 1.080 |
| 6889 | 12288 | 3072 | 32 | 1 | 319.39 | 103.23 | 97.38 | 3.28 | 1.060
|
| 9216 | 3072 | 3072 | 32 | 1 | 111.34 | 37.60 | 35.87 | 3.10 | 1.048 |
| 9216 | 3072 | 12288 | 32 | 1 | 259.39 | 117.26 | 111.41 | 2.33 | 1.053
|
| 9216 | 12288 | 3072 | 32 | 1 | 420.32 | 138.11 | 132.24 | 3.18 | 1.044
|
| 16384 | 3072 | 3072 | 32 | 1 | 192.11 | 63.07 | 59.10 | 3.25 | 1.067 |
| 16384 | 3072 | 12288 | 32 | 1 | 452.61 | 221.09 | 206.29 | 2.19 |
1.072 |
| 16384 | 12288 | 3072 | 32 | 1 | 731.39 | 253.40 | 242.88 | 3.01 |
1.043 |

**NVIDIA GB300 (sm_103a), CUDA 13.4**

| M | N | K | rank | bias | previous Cake (µs) | CUTLASS (µs) | this PR
(µs) | speedup vs previous Cake | speedup vs CUTLASS |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 129 | 3072 | 3072 | 32 | 1 | 10.46 | 7.20 | 5.98 | 1.75 | 1.203 |
| 129 | 3072 | 3072 | 32 | 0 | 6.05 | 6.88 | 5.92 | 1.02 | 1.162 |
| 129 | 3072 | 3072 | 64 | 1 | 9.42 | 6.80 | 6.05 | 1.56 | 1.124 |
| 129 | 3072 | 3072 | 96 | 1 | 7.81 | 7.10 | 6.14 | 1.27 | 1.156 |
| 129 | 3072 | 3072 | 128 | 1 | 10.74 | 7.30 | 6.27 | 1.71 | 1.163 |
| 129 | 3072 | 3072 | 128 | 0 | 9.47 | 7.07 | 6.21 | 1.53 | 1.139 |
| 129 | 3072 | 12288 | 32 | 0 | 14.50 | 14.37 | 12.54 | 1.16 | 1.145 |
| 129 | 3072 | 12288 | 32 | 1 | 23.46 | 14.66 | 12.61 | 1.86 | 1.162 |
| 129 | 3072 | 12288 | 128 | 0 | 24.16 | 15.01 | 12.77 | 1.89 | 1.175 |
| 129 | 3072 | 12288 | 128 | 1 | 25.25 | 14.59 | 12.86 | 1.96 | 1.134 |
| 6912 | 3072 | 3072 | 32 | 1 | 79.62 | 28.32 | 27.57 | 2.89 | 1.027 |
| 6912 | 3072 | 3072 | 64 | 1 | 76.38 | 29.66 | 27.55 | 2.77 | 1.077 |
| 6912 | 3072 | 3072 | 96 | 1 | 63.71 | 29.66 | 29.02 | 2.20 | 1.022 |
| 6912 | 3072 | 3072 | 128 | 1 | 86.37 | 30.27 | 29.44 | 2.93 | 1.028 |
| 6912 | 3072 | 12288 | 32 | 1 | 185.30 | 76.99 | 75.57 | 2.45 | 1.019 |
| 6912 | 3072 | 12288 | 128 | 1 | 215.23 | 78.82 | 77.46 | 2.78 | 1.018
|
| 4096 | 3072 | 3072 | 32 | 1 | 52.19 | 19.46 | 18.56 | 2.81 | 1.048 |
| 4096 | 3072 | 12288 | 32 | 1 | 122.77 | 51.81 | 50.08 | 2.45 | 1.035 |
| 4096 | 12288 | 3072 | 32 | 1 | 179.26 | 54.66 | 53.01 | 3.38 | 1.031 |
| 6889 | 3072 | 3072 | 32 | 1 | 79.39 | 28.13 | 27.28 | 2.91 | 1.031 |
| 6889 | 3072 | 12288 | 32 | 1 | 185.04 | 77.10 | 75.49 | 2.45 | 1.021 |
| 6889 | 12288 | 3072 | 32 | 1 | 293.30 | 85.17 | 83.17 | 3.53 | 1.024 |
| 9216 | 3072 | 3072 | 32 | 1 | 104.13 | 33.92 | 32.06 | 3.25 | 1.058 |
| 9216 | 3072 | 12288 | 32 | 1 | 244.45 | 95.87 | 94.22 | 2.59 | 1.017 |
| 9216 | 12288 | 3072 | 32 | 1 | 384.96 | 111.38 | 108.29 | 3.55 | 1.029
|
| 16384 | 3072 | 3072 | 32 | 1 | 178.08 | 56.96 | 52.43 | 3.40 | 1.086 |
| 16384 | 3072 | 12288 | 32 | 1 | 422.53 | 173.76 | 163.50 | 2.58 |
1.063 |
| 16384 | 12288 | 3072 | 32 | 1 | 673.32 | 195.98 | 187.87 | 3.58 |
1.043 |

This kernel has no other Cake variants: this is its only data-type /
layout variant, both fused forms (with and without bias) and all four
ranks are in this PR, and the PR covers sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added Cake NVFP4 SVDQuant GEMM support for SM100 and SM103 GPUs.
* Added shape- and device-aware routing with optional bias, alpha
scaling, and BF16 output support.
  * Added prebuilt and JIT loading for Cake kernels.
* Added validation for supported dimensions, ranks, layouts, and launch
configurations.

* **Benchmarking**
* Added an optional Cake benchmark backend with latency, TFLOPS/s, and
speedup reporting.
* Unsupported configurations are reported without interrupting benchmark
runs.
* Cake benchmarking is limited to supported SM100/SM103 configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: averyh <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4af2072](https://github.com/flashinfer-ai/flashinfer/commit/4af20723d27e650b67dbb20b0569c316b2185ded)

- **作者**: eigen
- **时间**: 2026-10-20T20:33:25Z
- **提交信息**: fix(cake_ssd_combined): cap the look-back vcount at the device's SM count (#6884)

The Cake backend of FlashInfer's Mamba2 SSD combined chunk-scan prefill,
`SSDCombined(backend="cake")`, ships three state data types (bf16, f16,
f32) x two sequence layouts (batched, varlen) x these program forms:
exact-scan, look-back chunk-parallel and three-phase chunk-parallel.
This PR changes only the host side (the Python loader) of the look-back
chunk-parallel program (`chunkpar_*`). That program splits its tile
order into V virtual CTA ranges, and every CTA of its one-CTA-per-SM
grid claims ranges until none is left. The loader used to pass V = the
capability's table value (148 on `sm_100a`, 152 on `sm_103a`, 212 on
`sm_107a`) whatever the device, so on a board with fewer SMs than that
value some CTAs ran a second round of ranges. It now passes V =
min(table value, device SM count): the NVIDIA Rubin R200 board variant
with 208 SMs binds V = 208 (one range per CTA), while boards with at
least the table value's SMs (R200 with 212 or 216 SMs, B200 with 148,
GB300 with 152) bind the same V as before and are byte-for-byte
unchanged. Every result depends on the inputs and V only, never on the
launch grid, so on a 208-SM board the outputs change with V and stay
within the family's precision gate against the exact scan (the maximum
absolute output difference vs the forced exact scan is identical before
and after on every row below); `agg_work` is still sized for the table
value and the kernel indexes at most V ranges, and a CUDA-graph-captured
call replays its V because the SM count is fixed per device index. The
baseline is the previous Cake version of this loader on the same GPU, in
the same process, with the same compiled kernels; only V differs.
Against it, the whole call is 1.345x to 1.641x faster back to back and
1.512x to 1.639x faster cold, with generated device sources, kernels and
routing unchanged.

Whole-call GPU time (preprocess + main launch) of one CUDA-graph replay
of the prepared call, measured with CUDA events on an NVIDIA Rubin R200
board variant with 208 SMs (compute capability 10.7, `sm_107a`). Setup:
driver 615.71.09, Cake kernels compiled with CUDA 13.4 (nvcc 13.4.92),
PyTorch 2.14.1+cu130, chunk-parallel forced with
`FLASHINFER_CAKE_SSD_CHUNK_PARALLEL=always`. Back to back is the mean
over 200 consecutive replays (warm L2) and cold is the median of 50
replays, each preceded by a 1 GiB L2 flush. All rows use the batched
layout, 8 SSM groups, headdim 64 and state dim 128, with z, D, dt_bias,
softplus and initial states, and a main grid of 208 CTAs in both arms.

| shape (batch x seqlen) | heads | state dtype | tiles | V before ->
after | before µs (back to back / cold) | after µs (back to back / cold)
| speedup (back to back / cold) |
|---|---|---|---|---|---|---|---|
| 1 x 8192 | 8 | bf16 | 512 | 212 -> 208 | 61.39 / 71.09 | 40.85 / 44.93
| 1.503x / 1.582x |
| 1 x 32768 | 8 | bf16 | 2048 | 212 -> 208 | 164.55 / 167.02 | 104.94 /
107.25 | 1.568x / 1.557x |
| 1 x 65536 | 8 | bf16 | 4096 | 212 -> 208 | 301.68 / 303.55 | 183.87 /
185.15 | 1.641x / 1.639x |
| 1 x 32768 | 8 | f16 | 2048 | 212 -> 208 | 163.73 / 166.74 | 104.59 /
105.98 | 1.565x / 1.573x |
| 1 x 32768 | 8 | f32 | 2048 | 212 -> 208 | 163.85 / 166.03 | 106.64 /
108.18 | 1.536x / 1.535x |
| 2 x 256 | 128 | bf16 | 512 | 212 -> 208 | 47.73 / 59.20 | 35.50 /
39.15 | 1.345x / 1.512x |

This PR does not affect the exact-scan forms or the three-phase
chunk-parallel program, leaves the look-back program unchanged on boards
with at least the table value's SMs, and the family continues to ship on
`sm_100a`, `sm_103a` and `sm_107a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved chunk-parallel execution on supported GPU architectures by
capping virtual CTA counts to the device’s available SM count.
- Preserved architecture-specific and segment-based limits while
ensuring at least one CTA is selected.
- Updated workspace sizing and reuse to align with the capped CTA count.

- **Tests**
  - Added coverage for devices with 208, 212, and 216 SMs.
- Updated forwarding and workspace expectations to verify correct CTA
selection.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [bc45bb9](https://github.com/flashinfer-ai/flashinfer/commit/bc45bb9878d6153fc83baa38c2ca1a5e9b3db446)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T20:29:21Z
- **提交信息**: fix(cake_mla): read layout-B scores from the warp's TMEM lane quarter (#6590)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes wrong output from two Cake MLA decode backends once a split holds
more than 64 keys:

- `backend="cake"` of `trtllm_batch_decode_with_kv_cache_mla`, route
`mla_bf16_native_split8_pdl`
(producer `cake_trtllm_mla_blackwell_db015a53334184a3005e`, SM100 and
SM103). This route serves BF16,
128 heads, batch 1, `kv_lens == (1024,)`, with either page 32, q_len 4,
no sink, or page 64, q_len 1,
with sink. 1024 keys over 8 splits is one 128-key tile per split, so
every split goes past 64 keys.
- `flashinfer.experimental.cake_mla_varq_dcp_decode`: eight of its nine
programs (bf16 and fp8 decode;
  the split-merge program is not affected).

**Cause.** The score MMA is M128 N128 `cta_group::2` and keeps two score
slots, at TMEM columns 0 and 64.
In this layout keys 64..127 of row `r` sit in TMEM lane `64 + r` at the
same columns as keys 0..63, and
each warp loads from its own lane quarter. The affected programs load
the scores at

```cpp
int s_base = taddr + s_off + (n_half * 64) + (tmem_row_base << 16);
```

The `n_half * 64` column offset sends softmax warps 2 and 3 to the other
score slot: they read the
previous or next tile's scores, or stale data, instead of their own keys
64..127. The fix addresses the
warp's lane quarter at the slot's own columns:

```cpp
int s_base = taddr + s_off + (((warp % 4) * 32) << 16);
```

The other Blackwell MLA decode programs in
`csrc/cake_trtllm_mla_blackwell/` (vquarter, vhalf, CLC)
already address the scores this way, without a column offset. Masking
(`tail_valid`, which uses `n_half`
correctly), the row-statistics exchange and the P/O path do not change.

**Why the tests missed it.** The tests drew inputs at 0.05 (0.1 for
varq). At that scale the softmax is
nearly uniform, so scores taken from the wrong keys still land inside
`atol=1e-2`. With inputs at 0.5,
on main the native split-8 rows show max abs error 3.0e-2 against max
|ref| 0.087, with about 12% of
elements over tolerance. With the fix the error is 3.1e-4.

**Changes.**

- One line changes in each of the 9 affected device sources. Every other
byte stays the same, and so do
file names, kernel symbols and loader registry keys. The sources were
not regenerated: these programs
were rendered by an earlier Cake exporter that does not reproduce these
exact files, so the fix is
  applied in place. The edited line is the same in all nine.
- `tests/attention/test_trtllm_gen_mla.py`:
`test_trtllm_mla_blackwell_bf16_dispatch` draws inputs at
0.5 and adds the page-64 sink row (`(1, 1, 64, True)`), which also takes
the native split-8 route. The
  float32 reference takes `page_size` and per-head sinks.
- `tests/experimental/test_cake_mla_varq_dcp_decode.py`: inputs at 0.5
(`_INPUT_SCALE`).

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually (`pre-commit run --files` on every
changed file: all passed, clang-format included).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

All on GB300 (SM103a), CUDA 13.3.

| Test | main + new tests | this PR |
|---|---|---|
| `test_trtllm_gen_mla.py::test_trtllm_mla_blackwell_bf16_dispatch` | 2
failed, 5 passed (`[1-4-32-False]`: 12.2% mismatched, max abs 3.2e-2;
`[1-1-64-True]`: 11.7%, 2.9e-2) | 7 passed |
| `test_trtllm_gen_mla.py -k "blackwell or cake"` | — | 32 passed |
| `tests/experimental/test_cake_mla_varq_dcp_decode.py` | 12 failed, 10
passed, 3 skipped | 22 passed, 3 skipped |

The 12 varq failures on main are `test_variable_q_dcp_rank_merge[bf16]`,
`test_public_api_h96_w2`,
`test_packed_head_counts[12|24|48]`, `test_page_sizes[bf16_p32]`,
`test_strided_kv_cache_view_binds_without_copy`,
`test_world1_var_q_matches_disabled_dcp`,
`test_split_items_merge_kernel[bf16|fp8]`,
`test_prepared_runner_replays_without_allocation` and
`test_matches_cute_dsl_mla_decode`.

`compute-sanitizer` on both native split-8 rows, filtered to the Cake
MLA kernels: memcheck 0 errors,
racecheck 0 hazards.

**Performance** (GB300, `b1 h128 kv1024`, public API, cold L2, medians
in µs; back-to-back and cooled with
a delay kernel between calls; old and new interleaved in one process):

| Row | main back-to-back | this PR back-to-back | main cooled | this PR
cooled |
|---|---|---|---|---|
| q4 page 32 | 11.81 / 11.87 | 11.84 / 11.84 | 11.84 / 11.84 | 11.81 /
11.87 |
| q1 page 64, sink | 12.22 / 12.26 | 12.22 / 12.19 | 12.35 / 12.22 |
12.26 / 12.32 |

Each cell gives two medians, one per interleaved round (old then new,
then new then old), over
`warmup_ms=100, bench_ms=1000`. The two kernels are the split-8 producer
and the reducer. The two sides
run at the same speed: every difference is within one 32 ns tick of the
timer.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: # (the existing experimental `cake_mla_varq_dcp_decode`
package; this PR only fixes it)
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware (GB300).
- [x] Nothing is registered in `flashinfer/aot.py` (this PR does not
change registration or routing).
  - [x] **Test scope declared below.**

```experimental-tests
tests/experimental/test_cake_mla_varq_dcp_decode.py
```

## Reviewer Notes

The kernel change is the same single line in nine files: `git diff -U0
-- '*.cu'` shows it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected score selection across Blackwell attention and DCP decode
paths to align each warp with its assigned row group.
* Improved reference-test coverage for varying page sizes and optional
sinks, and made input variations more likely to expose incorrect score
selection.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fda1694](https://github.com/flashinfer-ai/flashinfer/commit/fda16949043745adcf03ab4b598c977c5b91c3b6)

- **作者**: eigen
- **时间**: 2026-10-20T20:14:20Z
- **提交信息**: perf(cake_fmha): plan-free static one-wave program for the E4M3 head_dim-128 balanced DCP decode family (SM100a, SM103a) (#6119)

The `cake_fmha` balanced DCP speculative-decode attention kernel serves
paged KV caches with context parallelism and speculative q_len rows per
request. Cake ships it in three families, each with BF16 Q: BF16 KV
cache at head_dim 128, E4M3 KV cache at head_dim 128, and E4M3 KV cache
at head_dim 256. Each family ships 32-row and 64-row packed instances.
This PR changes the E4M3 head_dim-128 family
(`dcp_spec_bf16_fp8_balanced`). It adds program 2, a plan-free static
one-wave program, to the host `program` selector. Program 0 is the
device planner without the idle-CTA eight-slice fold, used at or above
the grid. Program 1 is the device planner with the fold and stays the
default. Program 2 applies when two conditions hold. First, the
block-table width bounds every (request, KV head) tile to at least 3
chunks of 256 tokens. Second, the chunk and reduce tickets fit the grid.
In that case, each CTA derives its ticket from its block index and skips
the device planner. Output is bitwise identical to program 1. The
baseline is the previous Cake version of this kernel on FlashInfer main,
which is program 1. Of the eight production-contract shapes, only
`prod_b1_s8192_q4_cp4_graph` falls in the static regime. That shape is
batch 1, 8 KV heads, 8192 context, q_len 4, CP 4, under a CUDA graph. On
that shape, latency drops from 12.58 to 11.87 µs on GB300 (1.059x) and
from 12.58 to 10.85 µs on B200 (1.159x).

Kernel GPU time (CUPTI, L2 flushed before every launch) on NVIDIA GB300
(sm_103a) and NVIDIA B200 (sm_100a), CUDA 13.3.1, measured 2026-10-06;
row 1 is a paired A/B of program 1 vs program 2 under CUDA-graph replay
(median of 3 seeds x 3 runs x 5 rounds). Rows 2-8 run the same program
before and after this PR, so both columns show one program 1 reading
(median of 5 rounds); speedup = main / this PR.

| Shape | GB300 main (µs) | GB300 this PR (µs) | GB300 speedup | B200
main (µs) | B200 this PR (µs) | B200 speedup |
|---|---:|---:|---:|---:|---:|---:|
| `prod_b1_s8192_q4_cp4_graph` | 12.58 | 11.87 | 1.059x | 12.58 | 10.85
| 1.159x |
| `prod_b8_s8192_q4_cp4_graph` | 17.3 | 17.3 | 1.000x | 19.2 | 19.2 |
1.000x |
| `prod_b8_s4096_q4_cp4` | 12.6 | 12.6 | 1.000x | 13.7 | 13.7 | 1.000x |
| `prod_b8_s4096_q8_cp4` | 12.4 | 12.4 | 1.000x | 13.8 | 13.8 | 1.000x |
| `prod_b8_s16384_q4_cp4` | 24.7 | 24.7 | 1.000x | 26.1 | 26.1 | 1.000x
|
| `prod_b8_s16384_q8_cp4` | 25.5 | 25.5 | 1.000x | 27.0 | 27.0 | 1.000x
|
| `cp1_peer_b1_s8192_q4` | 15.3 | 15.3 | 1.000x | 16.0 | 16.0 | 1.000x |
| `cp1_peer_b8_s8192_q4` | 38.2 | 38.2 | 1.000x | 39.3 | 39.3 | 1.000x |

The kernel's other Cake variants are the BF16 head_dim-128
(`dcp_spec_bf16_balanced`) and E4M3 head_dim-256
(`dcp_spec_bf16_fp8_d256_balanced`) balanced DCP families, each with 32-
and 64-row packed instances; this family ships on sm_100a and sm_103a
only.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [fc8cfd0](https://github.com/flashinfer-ai/flashinfer/commit/fc8cfd004324f5f3dbd54ed4aa50192aa7592888)

- **作者**: Shreya Gaur
- **时间**: 2026-10-20T20:06:29Z
- **提交信息**: [BugFix #5139] Accept the TC-decode ultra FC2 tile in the SM12x W4A16 `force_tile_config` re-pin (#6292)

# Fixes #5139 : accept the TC-decode ultra FC2 tile in the SM12x W4A16
`force_tile_config` re-pin

Branch: `b12x_w4a16_kernel_fix` (on upstream main, 0.7.2) · Target:
`main`

## 📌 Description

### Why this is needed

vLLM is adding W4A16 (NVFP4 weights, BF16 activations) support to its
`flashinfer_b12x` MoE backend
([vllm-project/vllm#56535](https://github.com/vllm-project/vllm/pull/56535))
so that weight-only NVFP4 checkpoints such as
`nvidia/Qwen3.6-35B-A3B-NVFP4` run through
`B12xMoEWrapper(quant_mode="w4a16")` instead of being silently quantized
to W4A4. That path goes through `moe_w4a16_kernel.py`. On every
FlashInfer release since the TC-decode re-pin landed (0.6.18 through
0.7.2, including this tree) the W4A16 kernel crashes on the first
decode-sized launch, so vLLM currently has to refuse W4A16 on those
versions. This PR removes the crash.

### The issue

With `nvidia/Qwen3.6-35B-A3B-NVFP4` (hidden 2048, expert intermediate
512, top-k 8) on a GB10 (SM121):

```
vllm serve nvidia/Qwen3.6-35B-A3B-NVFP4 --max-model-len 4096 --moe-backend flashinfer_b12x
...
ValueError: force_tile_config fc2 tile (tile_k=32, tile_n=512) does not fit
problem N/K=2048/512 at moe_block_size=8
```

The error surfaces during CUDA graph capture only because that is the
first launch with 4 or fewer tokens. With `--enforce-eager` it fires on
the first real decode step. FlashInfer 0.6.16.post3 is unaffected
because it predates both the TC-decode path and the re-pin.

### Root cause

All in
`flashinfer/fused_moe/cute_dsl/blackwell_sm12x/moe_w4a16_kernel.py`:

1. **Small batches enable TC-decode.** For `m <= _TC_DECODE_MAX_M` (4)
with BF16 gated activations, packed weights and no expert map,
`run_w4a16_moe` compiles with `tc_decode_fused_sum=True`.
2. **The selector widens FC2 to `tile_k=32`.** In TC-decode mode
`compile_w4a16_fused_moe` applies the "wide" (`tile_n` 128 → 256) and
then the "ultra" (`tile_n` 256 → 512) FC2 overrides to fit FC2 in the
same single persistent wave as FC1. A 512-wide tile at 256 threads
forces `tile_k = 512*32/64 = 32`. The ultra branch knows this is below
the generic `tile_k >= 64` floor and deliberately validates footprint
and K-divisibility directly instead of calling `_candidate_tile_fits`.
3. **Every launch crosses a torch custom op.** `run_w4a16_moe` launches
through `torch.ops.flashinfer.w4a16_fused_moe_launch`, passing the
selected tile sizes as integers.
4. **The op recompiles with the same tiles forced.**
`_w4a16_fused_moe_launch_flat` calls `compile_w4a16_fused_moe` again
with `force_tile_config=(fc1_tile_k, fc1_tile_n, fc2_tile_k,
fc2_tile_n)` so it resolves the identical cache entry.
5. **The forced-tile re-validation rejects the selector's own tile.**
The `force_tile_config` block re-validates each tile with
`_candidate_tile_fits`, which starts with `tile_n < 64 or tile_k < 64 or
cta_threads < 128 → False`. The ultra FC2 tile has `tile_k=32`, so it
fails and the `ValueError` is raised.

The `tile_k >= 64` check prunes the automatic search space; it is not a
kernel correctness bound. The constraints that matter all hold for the
ultra tile: 512 divides N=2048, 32 divides K=512, 32 is a multiple of
the 16-element NVFP4 scale group, and the shared-memory footprint was
already checked by the ultra branch. The override is numerically
neutral: only the FC2 output-tile width changes.

### The fix

`_candidate_tile_fits` gains `enforce_search_floor: bool = True`.
Automatic selection is untouched. The `force_tile_config` re-validation
passes `enforce_search_floor=False`, so forced tiles are checked against
divisibility, scale alignment and shared memory only. Every tile in
`_SMALL_BATCH_TILE_CONFIGS`, `_LARGE_BATCH_TILE_CONFIGS` and the wide
override already satisfies the floor, so the only geometry whose outcome
changes is the ultra FC2 tile the selector itself produces.

No kernel code or tile geometry changes, so there is no performance
delta to report; the fix only lets an already-selected configuration
launch.

## 🔍 Related Issues

- vLLM W4A16 support for the b12x backend, which hits this crash and
currently guards against FlashInfer 0.6.18–0.7.x:
https://github.com/vllm-project/vllm/pull/56535
- FlashInfer issue: _<link once filed>_

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (So far only `ruff check` and `ruff
format --check` were run on the two changed files; both pass. Run the
full hook set before opening.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Added to `tests/moe/test_b12x_fused_moe.py`, next to the existing W4A16
host-level tile tests:

| Test | Needs GPU | What it guards |
|---|---|---|
| `test_w4a16_forced_tile_validation_accepts_tc_decode_ultra_fc2_tile` |
no | The (32, 512, 256-thread) FC2 tile is rejected under the search
floor and accepted without it. |
| `test_w4a16_forced_tile_validation_keeps_correctness_constraints` | no
| With the floor off, misaligned `tile_k`, non-dividing `tile_n` and
oversize smem are still rejected. |
| `test_w4a16_tc_decode_ultra_fc2_tile_survives_custom_op_repin` | SM12x
| Compiles the Qwen3.6 decode shape for m = 1, 2, 4 with
`tc_decode_fused_sum=True`, asserts the selector reaches the ultra tile,
then recompiles with the same tiles forced and asserts identical
geometry. |

```bash
python -m pytest tests/moe/test_b12x_fused_moe.py \
  -k "forced_tile_validation or ultra_fc2_tile_survives or static_tiler_uses_64" -v
```

Results on DGX Spark (GB10, SM121, CUDA 13):

| Tree | `..._survives_custom_op_repin` |
|---|---|
| main without this fix | **FAILED** – `ValueError: force_tile_config
fc2 tile (tile_k=32, tile_n=512) does not fit problem N/K=2048/512 at
moe_block_size=8` |
| this PR | PASSED (4 passed, 17 s) |

### End-to-end validation through vLLM

GSM8K, `nvidia/Qwen3.6-35B-A3B-NVFP4`, one GB10, 1319 questions, 5-shot,
greedy, via vLLM `--moe-backend flashinfer_b12x` with
`quant_mode="w4a16"` (vLLM#56535):

| FlashInfer | Outcome | GSM8K |
|---|---|---|
| 0.7.0.post1 stock | crashes at first decode launch (above error) | – |
| 0.6.18.post1 stock | crashes with the same error | – |
| **0.7.0.post1 + this fix** | serves normally | **0.9158** |
| 0.6.16.post3 (predates the re-pin) | serves normally | 0.9136 |

Reference points on the same model and GPU: vLLM Marlin W4A16 0.911
(mean of 3 runs), b12x W4A4 0.890 (mean of 4 runs). The fixed W4A16 path
matches the known-good 0.6.16.post3 kernel and the Marlin weight-only
path, and recovers ~2.4 points over running the checkpoint as W4A4.

Reproduce (requires vLLM#56535 and
`VLLM_FLASHINFER_B12X_W4A16_IGNORE_BROKEN=1` to bypass vLLM's version
guard on a patched build):

```bash
pytest -s tests/evals/gsm8k/test_gsm8k_correctness.py --config-list-file=configs/models-sm12x.txt
```

## 🔬 Experimental Track

Not experimental; this changes the shipped
`flashinfer/fused_moe/cute_dsl/blackwell_sm12x` kernel.

## Reviewer Notes

- **Parity with the experimental kernel.**
`flashinfer/experimental/b12x/moe/_shared/kernels/w4a16/kernel.py`
already fixed this same bug with an `allow_qualified_fc2_tile` flag that
keeps the `tile_n >= 64` and `cta_threads >= 128` floors and admits only
the exact (32, 512, 256-thread) FC2 geometry for forced pins. The
shipped kernel never received that change. This PR uses a simpler
`enforce_search_floor` switch because it is the variant validated end to
end above; for every tile the selector can produce the two are
behaviorally identical. If reviewers prefer the experimental naming and
tighter admission for the shipped kernel, that is a small follow-up on
this PR (a ready diff exists), and the compile round-trip test covers
both.
- `force_tile_config` is also used for explicit NF3 pins. Those pins
pass through the same relaxed check; divisibility, scale alignment and
shared memory are still enforced.
- AI assistance (Claude Code) was used for the root-cause investigation,
the tests and this description. All changes were reviewed and run by the
submitter.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved automatic tile selection for certain small-batch W4A16
workloads on supported GPUs, enabling additional valid configurations
while preserving checks for alignment, resource limits, and shared
memory.
* **Tests**
* Added coverage for tile selection and forced configurations across
supported workload sizes, including checks that invalid configurations
remain rejected.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6445497](https://github.com/flashinfer-ai/flashinfer/commit/6445497657b7bc06fcc768d6d499e38627221818)

- **作者**: Qidong Su
- **时间**: 2026-10-20T20:05:08Z
- **提交信息**: fix(moe): adapt localized execution to the updated PyTorch stream API (#6488)

<!-- .github/pull_request_template.md -->

## 📌 Description

After [#5276 — feat(moe): add Rubin locality-domain
execution](https://github.com/flashinfer-ai/flashinfer/pull/5276) was
merged, [PyTorch updated its stream-execution API in
pytorch/pytorch#199128](https://github.com/pytorch/pytorch/pull/199128)
to require explicit callback input sequences. This PR updates FlashInfer
to that upstream API change and restores compatibility with the newer
PyTorch nightly builds.

The updated API is `execute_on_streams(streams, fn, *inputs)`: callback
arguments come from the supplied input sequences, rather than an
implicitly supplied stream index. FlashInfer's existing two-argument
calls reflected the earlier interface and are incompatible with this
newer contract. Both FC1 and FC2 now explicitly pass the locality-domain
shard indices:

```python
torch.cuda.execute_on_streams(
    localized_streams, callback, range(len(localized_streams))
)
```

Use this single upstream interface directly and remove the local
fork/join implementation, executor resolver, and legacy callback-arity
handling. Keep the existing failure-path stream joins so queued work
remains ordered before the exception propagates.

Localized execution now explicitly requires a PyTorch build providing
`torch.cuda.execute_on_streams`. Non-localized execution does not
require that API. This is an API-compatibility fix, not a new kernel or
a standalone performance optimization.

## 🔍 Related Issues

- Previous implementation: [#5276 — feat(moe): add Rubin locality-domain
execution](https://github.com/flashinfer-ai/flashinfer/pull/5276).
- Upstream API:
[pytorch/pytorch#199128](https://github.com/pytorch/pytorch/pull/199128);
the landed implementation in [commit
5ba7f2bf](https://github.com/pytorch/pytorch/commit/5ba7f2bf58f6177091cdf890429ffd5f5dc2139a)
defines `execute_on_streams(streams, fn, *inputs)` and rejects calls
without input sequences.

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

* **Compatibility**
* Localized MoE execution requires a PyTorch build with the
stream-execution API and reports an error when unavailable. Standard MoE
execution remains available without it.
* **Bug Fixes**
* Improved handling of partial-width outputs in grouped GEMM
finalization, preventing invalid reductions and ensuring output data is
ready before reuse.
* Localized execution now joins participating streams before propagating
GEMM failures.
* **Testing**
* Expanded coverage for localized execution failures, partial-width
outputs, and CUDA graph capture and replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Qidong Su <qidongs@nvidia.com>
Co-authored-by: Haobin Guo <haobing@nvidia.com>

### [afbe429](https://github.com/flashinfer-ai/flashinfer/commit/afbe429cc26216343f00c17fc9aa23fa5d8449ed)

- **作者**: Omer Ullman Argov
- **时间**: 2026-10-20T18:55:24Z
- **提交信息**: fix(gdn): SM90 prefill wrote final states past a compact scratch for … (#6849)

## 📌 Description

With `state_indices`, `output_final_state=False` and no `output_state`
(a read-only state pool), the SM90 GDN prefill dispatch allocated a
compact `[num_seqs, H, V, K]` scratch state. The SM90 kernel always
stores each sequence's final state to `output_state[state_indices[i]]`,
so any slot id at or past `num_seqs` wrote past the end of the scratch.
In `test_prefill_state_indices_without_final_state` (slots `[3, 0]`, two
sequences, H = 16) that is 1 MB past a 2 MB buffer.

The write only faults when the memory after the buffer happens to be
unmapped, which is why the test failed with an illegal memory access
only in the full parallel suite and passed in isolation.

- The SM90 scratch now spans the pool (`initial_state.shape`), as the
SM120 dispatch already does.
- With `state_indices` but neither an initial state nor an output state
there is no pool to index, so the slot ids are dropped instead of
indexing the compact scratch on SM90 and SM120.

This code was implemented with AI assistance.

## 🔍 Related Issues

Found while reviewing #6181.

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

`test_prefill_state_indices_read_only_pool_scratch_spans_pool` (SM90)
checks the scratch the dispatcher hands the kernel, for a pool and for
no pool, so it fails deterministically without the fix.

H100:
- `tests/gdn/test_prefill_state_indices.py`: 108 passed, 68 skipped.
- `compute-sanitizer --tool memcheck` with
`PYTORCH_NO_CUDA_MEMORY_CACHING=1` on
`test_prefill_state_indices_without_final_state[flashinfer-non-cp]`:
2176 invalid global writes before, 0 after.

## Reviewer Notes

The caching allocator hides the overrun from compute-sanitizer: without
`PYTORCH_NO_CUDA_MEMORY_CACHING=1` the writes land inside a segment the
allocator owns and memcheck reports nothing.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved prefill behavior when state indices are provided without an
initial or output state pool.
- Corrected scratch state allocation for indexed state pools on
supported hardware, ensuring storage covers all referenced pool entries.
- Preserved state-index mappings for pooled inputs while avoiding
unnecessary mappings when no initial pool is supplied.

- **Tests**
- Added regression coverage for indexed, read-only state pools and
scratch storage sizing.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e2456a4](https://github.com/flashinfer-ai/flashinfer/commit/e2456a4eeafe3ab14159b8debebf0582e34d3ed4)

- **作者**: eigen
- **时间**: 2026-10-20T18:42:47Z
- **提交信息**: deslop(cake_kimi_k3_situ): dead selectors, one device-helper header, the FC1 pair folded, nine host bindings shared (#6879)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Issue #6662 was written against an older main, when this family had 37
programs. Two merged commits, #6622 and #6628, added six programs and
three selectors before the base, so every count in this PR is re-derived
at the base. The family is the Cake-generated Kimi-K3 NVFP4 SiTU expert
MoE path behind `cutlass_fused_moe(backend="cake")` on SM100 / SM103.
This PR does five things:
- It removes two unreachable selectors and the registry metadata that
nothing reads.
- It moves the kernels' device helpers into one header with a guard per
helper.
- It adds the orphan tutorial to the docs toctree.
- It folds the one dispatch key that bound a different program on each
architecture into one kernel source with an architecture arm.
- It builds 9 programs from 8 kept host bindings through two compile
definitions.

`csrc/fused_moe/cake_kimi_k3_situ/` goes from 88 entries / 75,311 lines
to 78 entries / 58,293 lines. Kernel symbols, host-shim namespaces, FFI
exports, launch arguments and check conditions do not change for any of
the 42 programs.

Behaviour changes:
- **Removed Python names.** The dispatch module no longer defines
`_M1_FUSED_ARCHES`, `_LARGE_Q8I_ARCHES`, `_LARGE`, `_SFB_IMAGE_BYTES`,
`_SFB_IMAGE_BLOCKS`, `_sfb_shuffled_bytes` or the `m1` / `large_c7`
selector arms. All of these are private. The registry no longer exports
`CARRIED_PROGRAMS`, and its records no longer carry `binding_style`,
`role`, `tma_workspace_bytes` or `carried`. Nothing in the repository
read them, but an external reader of those keys would break. No
reachable input changes its route, its launch arguments or its error
path.
- **Host error reporting.** Nine programs are now built from a shared
binding. When a host check fails in one of them, the backtrace reports
the kept binding's file and line. The message text, the exception kind
and the check condition are unchanged. In the 8 kept programs, every
check site moves down by 16 lines. On SM103, the two error messages of
the `fc1:n8_s2a` route (launch and attribute set) now name the kept
program's kernel symbol.
- **JIT cache.** All 42 kernel sources change (they include the header),
as do 8 bindings and the compile flags of 9 records. The spec names stay
the same, so a warm JIT cache rebuilds every module once: the build
system's dependency scan sees the changed sources and the new header.
The former SM103 `fc1:n8_s2a` spec name is retired, and that build now
carries the kept program's name.
- **Registry readers.** For the 9 re-pointed programs,
`MODULES[name]["sources"][1]` names the kept binding and `compile_flags`
carries the two definitions. The `arches` field of 177a36 lists both
architectures. Every library still exports its own kernel symbol and its
own host-shim namespace.
- **Docs.** The tutorial joins the Tutorials toctree, which removes the
orphan warning, and two of its sentences are corrected.
- **Tests and performance.** The test file loses one vacuous id (31 ->
30). The GPU ids and their skip conditions are unchanged. No GPU
benchmark is run. Device code may change only under SASS identity, and
host text only under the host gate's normalised identity, so this PR
makes no performance claim.

## Changes

Family: the Cake-generated Kimi-K3 NVFP4 SiTU expert MoE path behind
`cutlass_fused_moe(backend="cake")`,
`cutlass_fused_moe_workspace_size(backend="cake")` and
`cake_fused_moe_prepare_workspace` on SM100 / SM103. It serves one
pinned contract (H=3584, I=384, E=896, top_k=16, TP8, EP1) and is JIT
only. Base: upstream main `8dc1163fbfbec7098a2418276fd04bc1fa1aeaa5`.
Head: `107e06b916c9aacde35fc1e66e61f1ef7013f10c` (6 commits). `git diff
--shortstat --no-renames`: 67 files, +3,067 / -20,436 (1 added, 11
deleted, 55 modified).

- **At the base**, `csrc/fused_moe/cake_kimi_k3_situ/` holds 88 entries
/ 75,311 lines:
- 43 single-kernel sources
`cake_kimi_k3_nvfp4_situ_routed_moe_<hash>_kernel.cu` (56,216 lines);
  - the 43 matching `_binding.cu` files (18,961 lines);
  - the submit source (130 lines);
- `.clang-format` (4 lines). It sets `DisableFormat: true`, so by design
the repository's clang-format hook does nothing on this directory.

The 43 programs (`MODULES` records) make 73 (program, architecture)
builds, plus 2 submit builds. 39 builds target SM100 and 34 target
SM103, and 30 programs build for both. Every program has one kernel
symbol `kernel_cake_kimi_k3_nvfp4_situ_routed_moe_<hash>` and one
host-shim namespace `cake_host_shim_<16 hex>`. The Python side has four
files:
- the registry `flashinfer/jit/cake_kimi_k3_situ.py` (1,801 lines),
which holds `MODULES`, `KERNELS` per architecture, `CARRIED_PROGRAMS`
and `gen_cake_situ_module(name, arch)`;
- the dispatch module `flashinfer/fused_moe/cake_kimi_k3_situ.py` (1,039
lines);
- the test `tests/moe/test_cake_kimi_k3_situ.py` (1,179 lines; 31 ids =
9 CPU + 22 GPU);
  - the tutorial `docs/tutorials/cake_kimi_k3_situ.rst` (80 lines).
- **After the chain**, the directory holds 78 entries / 58,293 lines
(-17,018): 42 kernel sources, 33 bindings, the new device header, the
submit source and `.clang-format`. The 42 programs still make 73 builds
plus 2 submit builds, because one program now serves both architectures.
Head sizes: registry 1,527 lines, dispatch 971, test 1,167 (30 ids = 8
CPU + 22 GPU). `docs/index.rst` goes from 74 to 75 lines and the
tutorial from 80 to 82.
- **Unchanged for all 42 programs:** kernel symbols, host-shim
namespaces, FFI exports (`prepare_entry`, `submit_entry`, `run`), launch
arguments and check conditions. JIT spec names
(`cake_situ_<arch>_<program>_<closure[:16]>`) are unchanged for every
surviving build. The one exception is the former SM103 `fc1:n8_s2a`
program's spec name, which is retired; its build now carries the kept
program's name.
- **Byte-identical to the base:** 25 of the 33 remaining bindings, the
submit source, `.clang-format`, `flashinfer/fused_moe/core.py`,
`flashinfer/fused_moe/__init__.py` and `flashinfer/jit/core.py`.
- **Disclosure.** The following statement appears exactly once in each
of the 51 touched generated files: the 42 kernel sources, the header and
the 8 kept bindings. It is line 16 of
`csrc/fused_moe/cake_kimi_k3_situ/cake_kimi_k3_nvfp4_situ_device.cuh`,
of each touched kernel source and of each kept binding:
`// Generated by Cake for FlashInfer. Exporter output, hand-edited here
pending exporter support.`

None of the 5 hand-written files contains it: the dispatch module, the
registry, the test, `docs/index.rst` and the tutorial. The registry's
header comment used to say "do not edit by hand" and now reads "Written
by the Cake exporter and hand-edited here pending exporter support." No
touched file claims "do not edit".

### Commit 1 (1ac2d5797) - cake_kimi_k3_situ: drop the unreachable m1
and large_c7 selectors (2 files, +27 / -136)

The dispatch module goes from 1,039 to 971 lines, and the test from
1,179 to 1,138.

**Why the arms are dead.** The selector function returns `'m1'` and
`'large_c7'` only for architectures outside `_M1_FUSED_ARCHES` /
`_LARGE_Q8I_ARCHES`. Both tuples are `('sm_100a', 'sm_103a')`, and the
device-facts check accepts only CC 10.0 / 10.3, so neither arm can be
reached. Their four dispatch keys (`quant_route:m1`, `fc1:n8_small`,
`fc1:n128_sfbs`, `sfb_shuffle:n128`) appear in no architecture's
`KERNELS`; the programs behind them were removed in #6340 / #6341.

**Removed with the arms.** This is 20 dead spans in the dispatch module,
and 5 comment blocks are reworded:
- the two tuples, `_LARGE`, `_SFB_IMAGE_BYTES` / `_SFB_IMAGE_BLOCKS` and
`_sfb_shuffled_bytes`;
- the `sfb_shuffled` workspace field and the `*_LARGE_C7_TOKENS` size
term;
- the `sfb_shuffle` stage and the `large_c7` scale-factor branch;
- the quant-route `x` / `qx` / `packed` / `scales` / `M` slots and the
m1 grid arm.

`_FC1_K_STEP` / `_FC1_K_TILES` are still used, so they stay.

**Tests.** Four kinds of test code collapse to the unconditional fused
form:
- the `ROUTED` table rows for the two selectors;
- the `STAGES_BY_SELECTOR` rows for the two selectors;
- the `_expected_selector` guards;
- the non-fused m1 asserts.

The test constants `FUSED_M1_ARCHES` / `LARGE_Q8I_ARCHES` are removed.
`test_cake_situ_workspace_layout_has_no_pre_shuffled_scale_factors` no
longer tests anything, so it is deleted (31 -> 30 ids).

**Proof.**
- The route table of every architecture over all 16,384 token counts
must be the same before and after. The proof of record is the exhaustive
`test_cake_situ_route_table` on both architectures (see Validation), and
a static route mirror agrees.
- No `.cu` file changes, so this commit has no SASS rows.

### Commit 2 (9b966649d) - cake_kimi_k3_situ: drop unread registry
metadata and the carried list (2 files, +48 / -313)

The registry goes from 1,801 to 1,540 lines. Commits 5 and 6 bring it to
1,527 at head.

**What is unread:**
- `binding_style`, `role` and `tma_workspace_bytes` have a single value
across all 43 records, and nothing reads them.
- The 30 `carried` dicts (140 lines) and `CARRIED_PROGRAMS` (32 lines
plus 6 comment lines) are read by only one test assertion.

**What changes:**
- All of the above is removed.
- The carried dicts recorded which per-architecture copies the first
deslop round merged into which program. That provenance moves into a
45-line comment next to `MODULES`.
- `test_cake_situ_program_records_are_consistent` still checks the
surviving keys (`arches`, `sources`, `specializations`, `compile_flags`,
`closure_sha256`) but no longer asserts on the carried data. Two test
lines and the docstring change to match.
- The registry header's "do not edit by hand" sentence is replaced by
the disclosure wording quoted above.

**Proof:**
- A whole-repository grep finds 0 readers of the removed keys and name
at head.
- The registry view through the real loader is compared on both trees.
32 records are identical once the dropped keys are set aside. The other
10 differ only through commits 5 and 6.
- The CPU suite runs on both trees.

### Commit 3 (4f851a1d1) - cake_kimi_k3_situ: share the kernel device
helpers through one header (44 files, +2,780 / -14,238)

- **New header**
`csrc/fused_moe/cake_kimi_k3_situ/cake_kimi_k3_nvfp4_situ_device.cuh`
(1,268 lines). It holds 103 helpers: the tcgen05 / mbarrier / TMA /
cp.async helpers, the type converters and both `make_warp_uniform`
overloads. The two overloads are different helpers: `int(int)` is
defined in 22 sources and `uint32_t(uint32_t)` in 21.
  - Each body is copied verbatim and appears only once.
- Each body sits behind a guard keyed on the helper's name and signature
(`#ifdef CAKE_SITU_NEED_*`). As a result, a source receives exactly the
helpers it defined before and nothing else.
  - Two helpers that have `.ftz` variants stay in their sources.
- **Kernel sources.** Each of the 43 kernel sources drops its helper
definitions (12,152 helper lines plus their blank lines). In their place
it gains three things: a `#define CAKE_SITU_NEED_*` block for its own
helper set (1,296 defines across the 42 sources at head), one `#include`
of the header, and the disclosure line.
- These parts are byte-identical to the base: the licence, the preamble,
the per-schedule `#define` block, the ABI / typedef block and the kernel
text.
- Every source keeps its `<math_constants.h>` include, and the header
has none.
- **Why one guard per helper.** #6871 showed that a header can change a
kernel's SASS by adding helpers the kernel did not define before. So
nothing is hoisted into a source that did not already contain it.

**Proof:**
- Expanding the include reproduces each base kernel source token for
token, for all 43 / 43 sources.
- In 8 sources (12 builds), the helper definitions come back in a
different order. A text proof cannot accept a reordering; only SASS
identity can. Those 12 builds are among the gate rows.
- For device code, see the 73 SASS rows under Validation.

This commit changes no Python, tests or docs.

### Commit 4 (e732d5018) - cake_kimi_k3_situ: add the SiTU tutorial to
the docs toctree (2 files, +6 / -3)

- **Toctree.** `docs/index.rst` adds `tutorials/cake_kimi_k3_situ` to
the Tutorials toctree (74 -> 75 lines). It was the only orphan tutorial,
so the docs build warned that it "isn't included in any toctree".
- **Tutorial text.** Two sentences of the tutorial were wrong and are
corrected against the dispatch module: the work-counter sentence and the
sentence after it (lines 72-73; the page goes from 80 to 82 lines). 22
statements on the page were checked statically against the dispatch
module, the registry and the test, and all of them hold at head.
- **Precedent.** The merged deslop PRs that found an orphan tutorial
added it to the toctree rather than deleting it, and this PR does the
same.

### Commit 5 (1d1a68757) - cake_kimi_k3_situ: fold the fc1:n8_s2a pair
into one kernel source (4 files, +7 / -1,983)

**The pair.** `fc1:n8_s2a` is the 1-token FC1 behind selector `m1_s2a`.
It was the only key bound to a different program on each architecture:
177a36 on SM100 and 8adb08 on SM103. Their kernel sources have 2,059 and
2,058 lines, and each has a 671-line binding. After commit 3, the two
kernel sources differ in exactly one hunk, which derives the
shared-memory base address:
- 177a36 uses an inline `cvta.to.shared` plus `make_warp_uniform`;
- 8adb08 uses `__cvta_generic_to_shared`.

**What this commit changes:**
- The kept source is 177a36's. It wraps that hunk in an architecture
arm: `#if __CUDA_ARCH__ == 1000` (its own text) / `#else` (8adb08's
text, byte-identical) / `#endif`. 19 kernel sources of the family
already use the same idiom.
- 8adb08's kernel source, binding and `MODULES` record are deleted.
177a36's `arches` now lists both architectures, and
`KERNELS["sm_103a"]["fc1:n8_s2a"]` points to it. The deleted program's
digest remains in one annotated provenance line of the registry.
- The two bindings were already identical after normalisation, with the
same 30-entry argument plan.

**No latency A/B.** The issue proposed a latency A/B to choose one copy.
It is not needed, because nothing is chosen: each architecture compiles
the same arm it compiled before.

**Proof:**
- The SM103 fold row of the SASS gate compares the deleted 8adb08 source
at the base with the merged source at head, under the kernel-symbol
mapping.
- The SM100 identity row of 177a36.
- The host fold row compares 8adb08's binding with 177a36's. Its
normalised diff may contain only the kernel-symbol and namespace tokens.
- The 1-token cases of the suite run on both GPUs.

Disclosed: on SM103, the two error-message literals of this route (the
launch message and the attribute-set message) now name 177a36's kernel
symbol. See Behaviour changes.

### Commit 6 (107e06b91) - cake_kimi_k3_situ: share identical host
bindings via compile definitions (19 files, +293 / -3,857)

**Grouping.** Once the kernel-symbol and host-shim-namespace tokens are
normalised, the 43 base bindings fall into 9 groups of text-identical
files with 19 members in total. One of these groups is the 177a36 /
8adb08 pair, which commit 5 already folds. This commit handles the other
8 groups. The kept binding of each group is its lexicographically first
member.

**Deleted bindings.** This commit deletes 9 bindings (3,755 lines).
Their programs are now built from the group's kept binding:

| Kept binding | Programs now built from it |
|---|---|
| 920a88 | 94ed29, af08a3 |
| 523709 | 98eeb5 |
| 194f5c | bf0370 |
| 9b180b | bf607b |
| 13ccea | d87925 |
| 5f1134 | eb3418 |
| eca3a1 | f732ff |
| b2c812 | ffc17e |

**Changes to the kept bindings.** Each of the 8 kept bindings gains the
following after the licence block:
- the disclosure line, which replaces the exporter's title line that
named the file's own program;
- a 7-line sharing comment;
- `#ifndef CAKE_SITU_KERNEL` / `#ifndef CAKE_SITU_SHIM` defaults that
name its own kernel symbol and namespace (16 guards and 16 defaults
across the 8 files);
- a two-macro stringize pair that spells the selected kernel symbol in
every launch error message that names it.

The kernel declaration, the attribute call, the launch argument, the
namespace and the error-message literals now use the macros.

**Registry.**
- The `sources` of the 9 re-pointed records name the kept binding.
- Their `compile_flags` carry exactly two compile definitions:
`CAKE_SITU_KERNEL=kernel_<own program>` and
`CAKE_SITU_SHIM=cake_host_shim_<own 16 hex>`.
- The other 33 records keep `compile_flags == []`.
- The definitions also reach the program's kernel source through the
shared flag list. They have no effect there, because no kernel source
contains a `CAKE_SITU_KERNEL` or `CAKE_SITU_SHIM` token. The 13 SASS
rows whose head side carries the definitions check this.

**Test.** In `test_cake_situ_program_records_are_consistent`, the
per-program binding assertion becomes two rules: a 9-entry re-pointing
rule (member -> kept binding), and the own-binding rule for every other
program.

**Proof:**
- Text: expanding the kept binding with a member's two definitions
reproduces the member's former text token for token. This holds for 17 /
17 renders, one per member of the 8 groups. 6 negative controls detect a
wrong definition, a missing definition, another kernel and another
namespace.
- Host: the 27 host-gate rows under Validation.

Disclosed: when a host check fails in a re-pointed program, the
backtrace names the kept binding's file and line. In the kept programs,
every check site moves down by 16 lines. See Behaviour changes.

## Validation

- **Device SASS gate.** The gate has one row per (program, architecture)
build of the head registry: 73 rows in total, 39 on SM100 (all identity)
and 34 on SM103 (33 identity + 1 fold).
- Identity rows compare the same kernel source at the base (with inline
helpers) and at head (with the header include and its guard block). For
the 9 re-pointed programs, the head side also carries the two compile
definitions (8 rows on SM100, 5 on SM103), where they have no effect.
- The fold row (SM103 `fc1:n8_s2a`) compares the deleted 8adb08 source
at the base with the merged 177a36 source at head, under the
kernel-symbol mapping.
- Flags are composed the way the loader composes them. That means
without the fast-math flag, which the loader strips for program modules.
  - The gate compiles and disassembles; it launches nothing.
- Each build must contain exactly one kernel function, and it must carry
the program's own symbol.
- SASS is compared per function and must be identical after masking
instruction addresses and encodings.
- The rows of record for both architectures are compiled on GB300, whose
compiler is deterministic for these kernels. A B200 compile is only a
cross-check.
- SM100 (compute capability 10.0): 39 rows (39 identity): 39 rows
identical after masking instruction addresses and encodings (39
identity; 8 of them with the two compile definitions on the head side);
every build contains exactly one kernel function, the program's own
symbol; 0 rows accepted through a fallback rule and 0 needed a base
recompile. Compiled on the GB300 route, which compiles both
architectures' rows as the proof of record (its compiler is
deterministic for these kernels); the B200 compile is a cross-check that
waits for that cluster's maintenance window.
- SM103 (compute capability 10.3): 34 rows (33 identity + 1 fold): 34
rows identical after masking instruction addresses and encodings (33
identity + the fold row, whose head side is the merged source under the
former SM103 program's symbol mapping; 5 identity rows carry the two
compile definitions); exactly one kernel function per build; 0 fallback
acceptances, 0 base recompiles. Compiled on the GB300 route (the same
run, proof of record).
- **Host gate.** The gate has one row per binding build whose text or
flags change: 27 rows in total. SM100 has 15 (8 shared + 7 kept). SM103
has 12 (5 shared + 6 kept + 1 fold).
- Shared rows compare the deleted member binding at the base with the
kept binding at head, built with the member's two definitions.
- Kept rows compare the kept binding at the base and at head, built with
its defaults.
  - The fold row compares 8adb08's binding with 177a36's.

Both sides of each row are compiled (no binding contains device code)
and preprocessed. A row passes when all of these hold:
- The preprocessed texts are identical after three declared
normalisation classes:
    - line markers and blank lines;
- the join of adjacent string literals around the stringized kernel
symbol;
- the file and line arguments that the check macros pass to the
backtrace.

The third class is the only one that hides a real change: the backtrace
location described under Behaviour changes. With that class turned off,
exactly two lines per check site may differ. The bindings have 4 to 93
check sites each, counted from the base member.
- The exported symbol sets are identical: the shim namespace's `Run` /
`PrepareEntry` / `SubmitEntry` and the three FFI entries.
- For the fold row, the normalised diff consists of exactly the
kernel-symbol and namespace tokens of the mapping.

Result: 27 rows OK on the GB300 route (both architectures: SM100 15 = 8
shared + 7 kept; SM103 12 = 5 shared + 6 kept + 1 fold): every binding
compiled on both sides with 0 device functions; the preprocessed texts
are identical after the three declared normalisation classes (line
markers / blank lines, the adjacent-literal join of the stringized
symbol, and the backtrace file / line arguments) on all 27 rows (24 rows
needed the classes, the 3 others were identical as emitted); with the
backtrace class off exactly two lines per check site differ (27 / 27
matched the expected site counts); exported symbol sets identical on all
27 rows; the fold row's normalised diff is exactly the kernel-symbol and
namespace tokens of the mapping.
- **Load-all.** Every program of the architecture is built through the
real loader (`gen_cake_situ_module(name, arch)`) in one process with a
fresh JIT workspace, together with the submit module. That is 39
libraries on SM100 (8 of them from a kept binding) and 34 on SM103 (5
from a kept binding). Each library must pass four checks:
- Its disassembly contains exactly its own kernel symbol. For 177a36
this is the merged source's symbol, on both architectures.
- Its exports are exactly its own shim namespace's three entries and the
three FFI entries, with no foreign namespace.
- Libraries, symbols and namespaces are distinct across the
architecture's programs.
  - The stage entries resolve.

Result: GB300 (CC 10.3, 152 SMs): all 34 SM103 program libraries plus
the submit module built through the real loader and loaded into one
process from a fresh JIT workspace; 34 distinct kernel symbols, 34
distinct shim namespaces, the three FFI entries and resolvable stage
entries per program; the 5 programs built from a shared binding carry
their own symbol and namespace. SM100 (39 libraries): not run yet, the
B200 cluster is in a maintenance window until 2026-10-22; it will be
posted as a comment on this PR.
- **GPU tests.** The suite runs on the candidate and on the unchanged
base, on one GPU, with a fresh JIT workspace per tree and one invocation
of `tests/moe/test_cake_kimi_k3_situ.py`. At head the file has 9
functions / 30 ids (8 CPU + 22 GPU); at the base it has 31 ids.
- On CC 10.3, the per-CTA privatized-routing and fused quant-reset tests
skip themselves (4 ids), because those programs ship for SM100 only.
- Any other skip, any failure, or any candidate / base difference beyond
the one removed id fails the run.
- Expected: the candidate gives 30 passed / 0 skipped on SM100 and 26
passed / 4 skipped on SM103. The base gives 31 / 0 on SM100 and 27 / 4
on SM103.
- B200 (148 SMs): not run before this PR opened: the B200 cluster is in
a maintenance window until 2026-10-22, so the SM100 suite (expected
candidate 30 passed / 0 skipped, base 31 / 0) and the SM100 load-all are
queued to run right after it and will be posted as a comment on this PR.
The SM100 device code is covered by the 39 SASS identity rows and the
SM100 host bindings by the 15 host-gate rows above, both compiled on the
GB300 route.
- GB300 (152 SMs): candidate 26 passed / 4 skipped (the four documented
SM103 skips) in 11 min 12 s; base 27 passed / 4 skipped in 10 min 37 s;
0 failed; the only difference is the removed vacuous layout test; 35 JIT
modules built per tree from fresh workspaces.
- **CPU checks** on the head tree (one route), each with its expected
outcome:
  - Lint, format and byte-compile of the 3 changed Python files.
  - The repository's pre-commit hooks:
    - ruff;
    - mypy on the two `flashinfer/` files;
    - the text hooks on all 56 changed files;
- clang-format on the 51 changed `csrc` files, which does nothing under
the family's own `.clang-format`.
  - Stale-reference greps:
    - 0 hits repo-wide for the 11 deleted file names;
- 0 for the deleted program's name and namespace, and its digest only in
the provenance line;
    - 0 for `CARRIED_PROGRAMS` and the dropped keys;
    - 0 for the removed dispatch and test names;
- the disclosure line exactly once in each of the 51 generated files and
in none of the 5 hand-written ones;
    - 0 "do not edit" claims.
- Byte-identity with the base for the 25 untouched bindings, the submit
source, `.clang-format` and the three untouched Python modules.
  - The text proofs re-run:
    - the header renders 43 / 43 sources token for token;
    - the arms of the fold source reproduce both former sources;
    - 17 / 17 binding renders, with the 6 negative controls;
    - the gate row tables regenerate identically.
  - The registry view through the real loader:
- 42 records: 32 identical to the base once the dropped keys are set
aside, 177a36 widened to both architectures, 9 re-pointed with exactly
the two definitions, and 8adb08 gone;
    - `KERNELS` equal to the base except for the one SM103 key;
    - all 73 program specs and 2 submit specs composable.
- Collect-only gives 31 ids on the base and 30 on the candidate (the one
removed id).
  - CPU-only pytest with CUDA hidden:
    - the CPU subset passes 8 on the candidate and 9 on the base;
- the whole file gives 8 passed + 22 skipped on the candidate and 9
passed + 22 skipped on the base, with every skip coming from the device
fixture.
- The docs build is not available on this route (no sphinx stack), so
the toctree entry and the page are checked statically.
- Commit messages: no banned words, a trailer on each commit, and no
line over 72 columns.

Result: passed on the head tree: ruff check / format and byte-compile
clean on the 3 Python files; the repository's pre-commit hooks all
passed (ruff, mypy on the two flashinfer/ files, the six text hooks on
the 56 changed files, clang-format on the 51 csrc files as a no-op by
the family's own configuration); every stale-reference count met its
expectation (the 11 deleted file names 0 hits repo-wide, the deleted
program's name and namespace 0, the removed keys and names 0, the
disclosure line exactly once at line 16 in each of the 51 generated
files and absent from the 5 hand-written ones, no "do not edit" claim);
the 25 untouched bindings, the submit source, .clang-format and the
three untouched Python modules are byte-identical to the base; the text
proofs re-ran identically (43 / 43 header renders token for token with 8
reorder-only sources, the fold pair and its render, 17 / 17 binding
renders with 0 differing lines and 6 negative controls, the gate tables
regenerated identically); the registry view through the real loader
found 42 records (32 identical to the base after the dropped keys, one
widened to both architectures, 9 re-pointed with exactly the two
definitions, the deleted record gone; the per-architecture kernel tables
equal except the one SM103 key); collect-only base 31 / candidate 30
with the one removed id as the only difference; CPU-only pytest with
CUDA hidden 8 passed (candidate) / 9 passed (base) on the CPU subset and
8 + 22 skipped / 9 + 22 skipped on the whole file; the docs build was
not available on the route (no sphinx stack), so the toctree entry and
the page are verified statically only; commit messages clean (0 banned
words, a trailer on each of the 6, no line over 72 columns).

## Not in this PR

- **Issue step 4's latency A/B** to choose one copy of the `fc1:n8_s2a`
pair: not needed, because commit 5 keeps each architecture's own text
behind an arm. The cross-architecture question stays open and is not
measured: whether either copy could replace the other with zero change.
- **Issue step 5, the binding shim rewrite.** This covers:
  - a table-driven TMA encoder for the 93 `EncodeTma_*` functions;
  - one `PreparedLaunch` template;
- a static-once shared-memory setter in place of the 17 per-call mutex
caches;
  - descriptor caching, cutting encodes per forward from 8 to at most 4;
  - dropping `run` / `Run()` / `prepared["launches"]`.

These are behaviour and interface changes that need host-time
measurements; they are not text folds. The one text fold the shim allows
is re-pointing bindings that are identical after normalisation, and that
is commit 6. Hoisting the bindings' byte-identical host-helper prefix
into a host header is a text fold left for a later round. A related
leftover was found during this work: a device-count helper
(`CakeDeviceMultiprocessorCount`) is defined in 12 of the 33 remaining
bindings and called by nothing in the repository. Deleting it is a
host-only follow-up.
- **Issue step 6, regenerating the constant clones.** This covers 13ccea
/ eb3418, 1dc27d / b2c812 (/ 93e235), the generic FC1 / FC2 triples and
the finalize sets.
- No pair differs only in `#define` values. For example, 13ccea and
eb3418 differ in 119 lines: 21 define-only, 91 inlined literals and 7
structural.
- A fold therefore needs regenerated or templated bodies and must meet
the issue's 2-4 % latency bar. That is exporter work plus measurement.
- The three `_f2e` pairs are a cache-hint variant (13ccea / d87925,
eb3418 / 5f1134, b2c812 / ffc17e). Folding them would merge two logical
kernel keys, which is a design decision.
- **Issue step 7, the exact-shape routing policy** (widen the special
routes or drop low-value exact-count programs). This is a product
decision plus a latency sweep. 27 of the 42 programs are reachable only
at the 13 exact token counts.
- **Parametric re-pointing of the near-miss binding groups** (2-7
numeric lines apart): deferred, because it needs numeric definitions
that edit literals.
- **The C-ABI / typedef block shared by the kernel sources:** deferred.
The header carries device helpers only.
- **Exporter regeneration** (emitting the header, the guards, the arm
and the definitions). The header, the arm and the kept bindings are hand
edits of exporter output, disclosed by the one statement.
- **Re-sealing `closure_sha256`:** not done. It is an opaque exporter
value, and the spec names stay.
- **Benchmarks:** this PR has no benchmark, no host-time measurement and
no descriptor caching.

Part of #6662

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Expanded Cake SiTU FC2 routing support for pooled routes with 8–1024
tokens.
  * Added documentation for Cake Kimi-K3 SiTU workflows.
* Enabled more flexible kernel and host integration across supported
builds.

* **Changes**
  * Single-token inputs now use the `m1_s2a` route.
* Large inputs now use `large_q8i` variants instead of the previous
`large_c7` route.
  * Routing work counters are initialized on every launch.

* **Refactor**
* Consolidated CUDA device utilities for more consistent kernel
maintenance.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [99406bb](https://github.com/flashinfer-ai/flashinfer/commit/99406bb9cae63a7154dc3498460f4778f1b8a33b)

- **作者**: ameynaik-hub
- **时间**: 2026-10-20T18:13:45Z
- **提交信息**: feat(gdn): prefix-cache state materialization kernel (#5073)

## 📌 Description
 
Adds `gdn_prefix_materialize`: reconstruct a request's GDN SSM state at
a chosen token from its u-cache checkpoint + ring, and write it to a
separate state-pool slot. Sources and rings are read-only; `count == 0`
is an exact copy; rows with negative slot/count are skipped.
 
**Use case: prefix caching.** A cached prefix is only reusable if its
state sits at a fixed boundary (e.g. every 128 tokens), but the u-cache
decode kernels checkpoint wherever their flush lands.
 
Example: a request's last flush checkpointed the state after token 120,
and decoding has since accepted tokens 121..129 into the ring. Token 128
is a boundary, so the scheduler calls this kernel once with `count = 128
- 120 = 8`: it replays ring entries 121..128 (not the 9th, token 129)
onto the token-120 checkpoint and writes the exact token-128 state to
the prefix cache's slot. Decode continues undisturbed.
 
The call must happen before the next flush moves the checkpoint past
128; per-request `src`/`dst`/`count` means one launch serves a whole
batch in which different requests cross different boundaries (and most
cross none: rows are `-1`).
 
```python
gdn_prefix_materialize(state, src_slots, dst_slots,
                       k_cache, u_cache, g_cache, cache_base, count,
                       active_request_indices, num_active)
```
 
### IO
 
`R` = ring depth (32 or 16, auto-detected from the tensors).
 
| Name | Shape | Dtype | Dir | Meaning |
| --- | --- | --- | --- | --- |
| `state` | `[pool, HV, V, K]` | STATE | in/out | src read, dst written
|
| `src_slots`, `dst_slots` | `[B]` | int32 | in | pool slots per request
|
| `k_cache` | `[pool, H, R, K]` | RING | in | ring: L2-normalized keys |
| `u_cache` | `[pool, HV, R, V]` | RING | in | ring: corrections |
| `g_cache` | `[pool, HV, R]` | f32 | in | ring: cumulative log-decay |
| `cache_base` | `[B]` | int32 | in | ring window origin |
| `count` | `[B]` | int32 | in | entries to replay (<= 16) |
| `active_request_indices` | `[B]` | int32 | in | live rows first, then
`-1` |
| `num_active` | `[1]` | int32 | in | device scalar: live rows |
 
### Precision
 
STATE/RING = bf16 (default) or fp16 via `GDN_UCACHE_STATE_DTYPE` /
`GDN_UCACHE_IO_DTYPE`, matching the decode kernels; f32 accumulate, one
rounding on store. SM90+, `K == V == 128`.
 
### Perf
 
B200, H=16 / HV=64, CUPTI:
 
- Idle launch ~2.5 us; 4-active ~11 us — both independent of batch size
in 8..512.
- B=256, all folding: 189 us — at the memory floor (the equal-bytes
`count == 0` case measures 174 us vs 172 us for a plain contiguous copy
of the same 1.07 GB).
### Bench
 
```bash
python benchmarks/bench_gdn_prefix_materialize.py
```
 
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
```bash
pytest tests/gdn/test_gdn_prefix_materialize.py  # 110 tests
```
 
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
 
AI-assisted (Claude Code).
 
<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added GDN prefix-cache materialization to reconstruct SSM state from a
selected prefix without modifying source data.
- Supports multiple ring sizes, partial or zero-length replay,
active-request filtering, and paged cache pools.
- Added validation for incompatible cache layouts, dimensions, data
types, and memory alignment.

- **Tests**
- Added comprehensive coverage for replay behavior, ring windows,
skipped requests, paged pools, and randomized workloads.

- **Benchmarks**
- Added performance benchmarks covering request counts, replay depths,
execution modes, bandwidth, and padding overhead.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9f7a290](https://github.com/flashinfer-ai/flashinfer/commit/9f7a290987b69277a9031b1c6091810d83cfed3b)

- **作者**: eigen
- **时间**: 2026-10-20T18:09:36Z
- **提交信息**: deslop(cake_kda_tf32): dead host code, one device-helper header, 24 kernel clones folded onto 9 bodies (#6876)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Issue #6661 was written against an older main. Three merged commits
changed this family before the base. The largest was #6758, the BF16
half of the same family. It deleted all 85 checked-in host bindings, and
the 34 TF32 ones (9,497 lines) have been rendered from one template
since. It also trimmed the shared runtime (6,478 -> 5,832 lines) and the
host shim (3,264 -> 3,169), moved TMA-descriptor encoding into the
prepare branch and folded 8 BF16 clusters. This PR is the TF32 half and
uses the same three mechanics. It removes dead host code from the shared
runtime, moves the device helpers of the 34 TF32 kernel sources into one
shared header, and folds 24 kernel clones onto 9 bodies selected by
compile definitions. `csrc/kda/tf32/` goes from 35 entries / 97,009
lines to 21 entries / 41,231 lines. Module names, kernel symbols,
bindings and launch arguments do not change.

Behaviour changes:
- **Removed Python names.** The shared runtime no longer defines
`prepare_fwd`, `KDAInputABI`, `_rebind_tensor_signature`, the 15 probe
launch classes and 19 constants. None was exported from `flashinfer` or
imported anywhere in the repository. The `ValueError` guards that only
the deleted forced-probe classes could reach are removed with them. No
reachable input changes module selection, launch arguments or error
path, and the set of inputs that raise is unchanged (checked by the
planner dry run, see Validation).
- **JIT cache.** The source text of all 34 TF32 modules changes: all of
them get the header, and 24 of them also get a shared body and compile
definitions. The JIT spec names stay the same, so a persisted JIT cache
recompiles every TF32 module once, and a warm cache from the base is
stale.
- **Registry readers.** For the 24 folded modules,
`MODULES[name]["sources"]` names the shared body and `compile_flags`
carries the kernel-symbol and knob definitions. The other 10 keep their
own file and the base flag list. Every library still exports its own
kernel symbol and its own host-shim namespace.
- **Future modules.** The fold table also records which knobs each body
honours. A module added later with a new knob value or a different
co-varying kwarg needs its own body or a new arm, never an existing body
as is. The table comment states this whole-row rule.
- **Unchanged.** Everything host-side (the shim, the binding template,
the rendered bindings, `kda_prefill.py`), the BF16 family and every test
file except the m128 fold test are byte-identical to the base. No GPU
benchmark is run. Device code changes only under SASS identity and host
Python only by dead-code removal, so this PR makes no performance claim.

## Changes

Family: the 34 Cake-generated TF32 prefill modules behind
`flashinfer.prepare_tf32_kda_prefill` on SM100 / SM103, JIT only. That
is 57 (module, architecture) builds: 23 modules on both architectures, 9
on SM103 only and 2 on SM100 only. Base: upstream main
`28bf16712268f74a07beeef87dd2f57072e544e6`. Head:
`6b5466f4e645738d7c0d0731976751590017376f` (3 commits). `git diff
--shortstat --no-renames`: 40 files, +2,378 / -58,039 (3 added, 15
deleted, 22 modified).

- **At the base**, `csrc/kda/tf32/` holds 34 kernel sources (93,840
lines) and the host shim `cake_kda_prefill_host_shim.cuh` (3,169 lines,
untouched here). The shared Python is the registry
`flashinfer/jit/cake_kda_tf32.py` (2,279 lines: 85 module rows for both
families, `_M128_FOLDS` for BF16, `spec(name, arch)`) and the runtime
`flashinfer/cake_kda_tf32_runtime.py` (5,832 lines). Every module has
one kernel symbol `kernel_cake_kda_tf32_<digest>` and one host-shim
namespace `cake_host_shim_<digest>`.
- **After the chain**, `csrc/kda/tf32/` holds 19 kernel sources (37,023
lines), the new header (1,039 lines) and the shim (3,169 lines). The 19
sources are 9 fold bodies and 10 sources changed only by the header.
- **Unchanged for all 34 modules:** module names, JIT spec names, kernel
symbols, host-shim namespaces, rendered bindings, launch arguments and
FFI exports (`run`, `run_prepared`, `run_prepare_tma`). Of the 85
registry records, 24 change in `sources` / `compile_flags` only and 61
are identical. The factory keys (80 on SM100, 88 on SM103) are identical
to the base.
- **Byte-identical to the base:** the shim, the binding template
`flashinfer/jit/cake_kda_prefill_binding.py` and its sidecar,
`flashinfer/kda_prefill.py`, the whole `csrc/kda/bf16/` tree and its
fold sidecar, the four GPU test files and the four untouched CPU test
files.
- **Disclosure:** the 21 touched generated files are the 19 kernel
sources, the header and the registry's `_TF32_FOLDS` comment. Each
contains this statement exactly once (line 16 of
`csrc/kda/tf32/cake_kda_device.cuh` and of each kernel source):
`// Generated by Cake for FlashInfer. Exporter output, hand-edited here
pending exporter support.`
None of the 4 hand-written files (the runtime, the two tests and the
sidecar) contains it. No touched file carries a "do not edit" claim.

### Commit 1 (3ed3c6c38) - kda prefill: drop unreachable probe classes
and dead host code

1 file, +36 / -323. The subject uses the `kda prefill:` prefix because
the file is the shared runtime. `flashinfer/cake_kda_tf32_runtime.py`
goes from 5,832 to 5,545 lines by removing 29 dead items:
- **15 probe launch classes that nothing instantiates:** the BF16 / FP32
grouped probes, the LPT and piece M128 probes, the direct-N32, small-BH
and BT16 probes, the active-beta and short-N16 four-stage probes, and
the BT16 S7-chain and beta-TMA probes.
- **The class flags only those classes set, and the code those flags
selected:** the persistent task-schedule block, the forced BT16 chain
and beta-TMA overrides, the short-N16 four-stage contract check with its
parameters on three route predicates, and the never-set BF16
initial-state flag.
- **12 raw-pointer table rows** for factory families that no request
site names.
- **A dispatch ternary** whose two arms name the same class, plus its
two locals.
- **Unused code:** the uncalled `prepare_fwd` and
`_rebind_tensor_signature`, the unused `KDAInputABI` enum, and 19
constants that nothing reads.
- **Two stray expression-statement strings** become comments in place: a
21-line comment block and a one-line comment. The net change is -287
lines.

**Why behaviour-preserving.** Nothing outside the removed set references
a removed definition. Four of the 15 probe classes are referenced only
as bases of removed subclasses, and the contract check only by its
removed call. A separate PTX fallback package has its own function named
`prepare_fwd`; that function is untouched. At head, none of the removed
names survives anywhere in the repository, and nothing looks a class up
by string. Every collapsed conditional keeps the arm its default value
chose. The factory requests keep `n16_short_four_stage=False` and
`affine_main_indexed_initial_bf16=False` as literal key members. As a
result, no request key, module selection, launch argument or error path
changes for any reachable input.

**Proof.** Device code, bindings, shim and registry are untouched, so
this commit has no SASS rows. It is covered by the planner dry run and
by the CPU and GPU suites on both trees (see Validation).

### Commit 2 (c77add432) - cake_kda_tf32: share the TF32 device helpers
through one header

35 files, +1,107 / -29,682.
- **New header** `csrc/kda/tf32/cake_kda_device.cuh` (1,039 lines). It
holds the family's 97 helper items (96 `__device__ __forceinline__`
functions and one `union MmaSmemDesc`), each body verbatim and once.
They are in dependency order (8 edges, acyclic). The header also takes
the `<math_constants.h>` include that every kernel carried.
- **Kernel sources.** Each of the 34 sources defined 29 to 90 of the 97
items; the union appears in 26 of them. Every helper name has exactly
one body across the 34 files, byte-identical, not just equal after
whitespace normalisation.
- Each source drops its helper region and its `<math_constants.h>`
include. The regions total 29,682 lines, 25,589 of them function and
union lines.
- Each source gains `#include "cake_kda_device.cuh"` where that include
sat (after the preamble and the per-schedule `#define` block, before the
kernel), plus the disclosure line.
- Licence, preamble, `#define` block and kernel text are byte-identical
to the base.
  - `csrc/kda/tf32/` goes from 97,009 to 68,434 lines.
- **Overloads.** `make_warp_uniform` has 221 call sites: 194 pass `int`
and 27 pass `unsigned int`. The header ships only the `uint32_t`
overload. The three sources whose preamble defines the `int` overload
keep it there. No source's overload set changes, and 0 of the 221 call
sites bind to a different overload. A header with both overloads would
have changed the binding at 191 call sites.
- **No hidden coupling.** The helpers use no per-source macro: none of
the 156 `#define` names appears in the header text. No source mentions a
helper it did not define.

**Proof.** Expanding the include reproduces each base kernel token for
token, 34 / 34, and a byte-level line pass agrees. The only allowed
differences are:
- the header frame;
- the disclosure line;
- helpers that the source did not define (unused inline device functions
emit no code);
- in 8 sources, the order of the helpers.

For device code, see the 57 SASS rows below (17 identity, 40 fold). This
commit changes no Python, tests, packaging or docs.

### Commit 3 (6b5466f4e) - cake_kda_tf32: fold 24 TF32 kernel clones
onto 9 knob-keyed bodies

28 files, +1,265 / -28,064. 24 of the 34 kernel sources form 9 clusters.
Within a cluster, the members differ only in lines selected by one to
three factory kwargs (knobs): the booleans `compact_output`,
`split_prediction`, `write_checkpoints`, `active_beta_f32` and
`affine_map_only`, and the integers `value_rows` (64 / 128) and
`affine_factor_cache` (0 / 1).
- **Clusters (9 bodies / 24 members):**
- the 5-kernel BT16 chain, including the issue's P07 trio and
`d4bf3dee`;
  - the P05 prepare pair (the issue's P05 active-beta pair);
- 7 N32 clusters with 17 members: the 4-kernel affine-main cluster (the
issue's two P06 active-beta pairs crossed with `write_checkpoints`), the
3-kernel unbounded cluster, the 2-kernel affine-tail cluster and four
2-kernel `write_checkpoints` / `value_rows` pairs.
- **Bodies.** Each cluster keeps its representative's file as the body.
- The differing lines sit behind `#if` blocks on `CAKE_KDA_<KNOB>`
compile definitions: 147 `#if` arms over 147 regions. Boolean knobs are
tested bare or negated; integer knobs are compared.
- The kernel is named through `CAKE_KDA_KERNEL_SYMBOL`, so every member
keeps its own kernel symbol and no symbol mapping is involved.
- 22 `#ifndef` + `#error` guards sit after the licence block: 9
kernel-symbol guards and 13 knob guards (one per knob of each body).
- The 15 member files that are not bodies are deleted. Their 45,577
lines (with the header applied) become 18,374 body lines, net -27,203.
`csrc/kda/tf32/` goes from 68,434 to 41,231 lines.
- **Registry** (2,279 -> 2,425 lines):
- New tables `_TF32_FOLDS` (body -> (knobs, {module -> {knob ->
value}})) and `_TF32_FOLD_OF` (+141 lines). They sit next to the BF16
`_M128_FOLDS`, which keeps its 8 entries.
  - A one-line change to the module-rows comment (+1 net).
- A four-line arm in `_module_record` (+4). For a folded module,
`sources` is the body. `compile_flags` is the fast-math flag the
registry already carried, plus the compile definitions
`CAKE_KDA_KERNEL_SYMBOL=kernel_<own stem>` and `CAKE_KDA_<KNOB>=<value>`
for each knob, in table order.
- For each body, the table comment names the kwargs that co-vary with a
knob without selecting any text of their own. It also states the rule
that a module joins a body only when its whole row of kwargs matches a
member's.
- **Unfolded kernels.** The other 10 kernels are untouched beyond commit
2: two singletons with their own argument plans and eight N32
singletons.
- **New test** `tests/kda/test_cake_kda_tf32_fold.py` (184 lines, 3 CPU
tests):
- the table routes 24 modules onto 9 existing bodies, and no module is
in both fold tables;
  - the definitions match the factory rows and the body guards;
  - each expansion's sha256 equals the sidecar.
- **New sidecar** `tests/kda/cake_kda_tf32_fold_sha256.json` (74 lines,
24 pins). Each pin is the sha256 of a former kernel source as it stood
right before the fold, with the header applied.
- **m128 test.** Line 139 of `tests/kda/test_cake_kda_m128_fold.py` is
generalised: its own-kernel rule now also skips `_TF32_FOLD_OF` members.
The file stays at 192 lines.

**Why behaviour-preserving.** Each member compiles from its body, with
its own definitions, to its former source text and keeps its own kernel
symbol. Its registry record changes only in `sources` / `compile_flags`.

**Proof.** Expanding a body with a module's compile definitions
reproduces that module's former kernel source byte for byte, for all 24
modules. The negative controls all behave as required (0 failures):
- each of the 41 knob flips (one per knob assignment of the 24 members)
changes the expanded text;
- each of the 65 omitted definitions (41 knob, 24 kernel-symbol) reaches
an `#error` guard.

For device code, see the 40 SASS fold rows below. Each is built under
the member's own kernel symbol.

## Validation

- **Device SASS gate:** one row per shipped TF32 (module, architecture)
build, 57 rows.
- Fold rows (the 24 folded modules, 40 builds). Base side: the module's
own kernel source at the base (inline helpers) with the base flags. Head
side: the kept body with the module's exact head compile flags (the base
flag plus its kernel-symbol and knob compile definitions).
- Identity rows (the 10 unfolded modules, 17 builds): the same file at
the base (inline helpers) and at head (one include).
- Flags are composed the same way the loader composes them. The gate
compiles and disassembles; it launches nothing.
- Each build must contain exactly one kernel function, named by the
module's own symbol, so no row uses symbol mapping. The SASS is compared
per function and must be identical after masking instruction addresses
and encodings.
- SM100 (compute capability 10.0): 25 rows (18 fold + 7 identity): 25 /
25 identical after masking instruction addresses and encodings, 0 rows
accepted through a fallback, every build with exactly one kernel
function named by the module's own symbol. These rows were compiled on
the GB300 route (the same toolkit, compute capability 10.0 as the
target), whose compiler reproduces these kernels deterministically; the
B200 route's compiler is not deterministic for some Cake kernels (a
recompile of the unchanged base can differ by uniform-register
renaming), so a compile there is only a cross-check
- SM103 (compute capability 10.3): 32 rows (22 fold + 10 identity): 32 /
32 identical after masking instruction addresses and encodings, 0 rows
accepted through a fallback, every build with exactly one kernel
function named by the module's own symbol; compiled on the GB300 route
- **No host gate.** The shim, the binding template and the binding
sidecar are byte-identical to the base.
`tests/kda/test_cake_kda_prefill_binding.py` re-pins the 85 rendered
bindings on both trees. The render sha256 equals the sidecar for all 34
TF32 modules (CPU checks below).
- **Load-all.** Every TF32 module of the architecture is built through
the real registry (`spec(name, arch)`) in one process with a fresh JIT
workspace: 25 libraries on B200 (18 from the 9 bodies) and 32 on GB300
(22 from the bodies). Pass criteria:
- each library's disassembly contains exactly its own kernel symbol,
plus the upload kernel for every module with a TMA descriptor workspace
(all but one);
- its exports are exactly its own shim namespace's `Run` and the FFI
entry;
- `run` resolves, and so do `run_prepared` / `run_prepare_tma` for
descriptor modules.
- Result: B200 (148 SMs): 25 libraries built and loaded into one process
(25 distinct kernel symbols and host-shim namespaces, an FFI entry per
module, the upload kernel in 24 of them; the 18 folded modules built
from 7 of the 9 bodies with their own symbols); GB300 (152 SMs): 32
libraries built and loaded into one process (32 distinct kernel symbols
and host-shim namespaces, an FFI entry per module, the upload kernel in
31 of them; the 22 folded modules built from the 9 bodies with their own
symbols)
- **GPU tests** on the candidate and on the unchanged base: one GPU, a
fresh JIT workspace per tree, one invocation per suite. The four files
are byte-identical to the base and skip nothing on CC 10.0 / 10.3. Any
skip, or any difference in counts between candidate and base, is a
failure.
- `tests/kda/test_tf32_prefill.py`: 4 functions, 26 cases
(`test_prefill_prepared` 18, `test_prefill_rejects_bf16_external_state`
4, `test_active_beta_affine_without_checkpoints_replays` 2,
`test_bf16_active_beta_strided_checkpoints_replay` 2), 12 of them
`[tf32]` ids.
- The three BF16 neighbours of the shared runtime, 106 cases:
`tests/kda/test_kda_prefill_plan_cache.py` (68),
`tests/kda/test_bf16_one_wave_route.py` (7) and
`tests/kda/test_kda_prefill_trained_gate_distribution.py` (31).
- Expected per GPU, on both candidate and base: 26 passed / 0 skipped
and 106 passed / 0 skipped.
- B200 (148 SMs): candidate 26 passed / 0 skipped and 106 passed / 0
skipped. Base control (the PR's parent in a fresh JIT workspace): 26
passed / 0 skipped on the TF32 suite; the base neighbour run was
interrupted by a storage fault of the compute node after 72 of its 106
cases had passed (1 failure and 67 errors, all the same I/O error; no
assertion failed), and the cluster entered a two-day maintenance window
before the run could be repeated. The base control is complete on GB300
(below); the B200 repeat is scheduled after the maintenance window and
its result will be posted on this PR
- GB300 (152 SMs): candidate 26 passed / 0 skipped and 106 passed / 0
skipped; base (the PR's parent in a fresh JIT workspace of its own) 26
passed / 0 skipped and 106 passed / 0 skipped — identical counts per
suite
- **Planner dry run** (CPU, the real planner with device queries
stubbed), base vs head over 38,016 TF32 points: both gates, indexed and
plain state, 0 / 64-token checkpoints, logit and active beta, SM100 and
SM103. Expected: no point changes outcome, newly succeeds, newly raises
or selects a different module. The companion reachability grid documents
that the active-beta chain module `d4bf3dee` is selected; that is why it
is a fold member rather than a deletion. Result: 38,016 planner points
(every exported TF32 schedule request over the test stubs) evaluated on
the base and on the head in separate processes: rows=38016 changed=0
newly_ok=0 newly_raise=0 module_changed=0 only_in_base=0 only_in_cand=0
(the 9,272 unexported points raise identically on both sides)
- **CPU checks** on the head tree (one route), each with its expected
outcome:
  - Lint, format and byte-compile of the 4 changed Python files.
- The repository's pre-commit hooks: ruff, mypy on the registry and
runtime, and the text hooks on the 25 changed files. The repository
configuration excludes `csrc/kda/tf32/` from clang-format.
- Stale references: 0 repo-wide hits for the 15 deleted file names; the
deleted digests appear only in their 15 registry rows; 0 hits for the
removed Python names.
- Byte-identity of the shim, the template, the binding sidecar,
`kda_prefill.py`, the BF16 tree and the 8 untouched test files.
  - Text proofs re-run:
    - the header, regenerated from the pristine base, is byte-identical;
- token and line identity holds for 34 / 34 sources, and 0 of 221 call
sites bind to a different overload;
- all 24 fold expansions are byte-exact, with 0 negative-control
failures;
    - the regenerated sidecar equals the shipped one.
  - Registry view through the real loader:
- 85 records: 9 representatives differ in `compile_flags` only, 15
members differ in `sources` + `compile_flags`, and 61 are identical;
    - `spec(name, arch)` composes for all 57 builds;
- the render sha256 equals the binding sidecar for the 34 TF32 modules.
  - The planner dry run above.
- pytest collection: base 181 ids, candidate 184. The shared ids are
identical, and the candidate adds the 3 new fold-test ids.
  - CPU-only pytest with CUDA hidden:
- on the candidate, the six CPU files pass 52 tests:
`test_cake_kda_prefill_binding.py` 5,
`test_kda_prefill_route_exports.py` 29,
`test_kda_prefill_route_predicates.py` 10,
`test_cake_kda_prefill_binding_strides.py` 2,
`test_cake_kda_m128_fold.py` 3 and the new `test_cake_kda_tf32_fold.py`
3;
    - on the base, the five CPU files pass 49;
    - on both trees, the four GPU files skip 132.
- Result: all passed at 6b5466f4e on a GB300-route CPU step (CUDA hidden
where noted): ruff check / ruff format / py_compile on the 4 changed
Python files; the repository's pre-commit hooks on the changed files
(ruff-format and mypy on the 4 Python files; end-of-file-fixer,
trailing-whitespace, mixed-line-ending, remove-tabs and remove-crlf on
25 files; ruff-check and clang-format had no file in their scope by the
repository's own configuration) with a clean tree afterwards;
stale-reference greps: 0 hits repo-wide for the 15 deleted kernel file
names, exactly their 15 registry rows for the deleted digests, 0 kernel
file names spelled out in Python, and the expected counts for every kept
marker (9 kernel-symbol definitions and 23 guards in the 9 fold bodies,
147 conditional arms, 19 sources including the shared header, 24
fold-sidecar entries, the 85 binding-sidecar pins unchanged); the shared
host shim, the binding template, the binding sidecar, the planner
module, the bf16 kernel tree and every untouched test file
byte-identical to the base; each unit's own text tools re-run on the
delivered tree (fold check: 24 / 24 members expand byte-exact to their
former header-applied text, 0 negative-control failures; registry check:
85 modules, 24 folded records changed in sources / compile flags only,
factory keys unchanged; render and header checks ok; the shipped gate
entry files equal their regeneration); the registry imported with the
real environment equals the base registry except for the 24 folded
records' sources and compile flags (61 records identical, factory tables
identical, all 57 TF32 (module, arch) specs composable, rendered
bindings equal to the sidecar); collected ids base 181 / candidate 184
(the 3 new fold-test cases, no other change); CPU-only pytest with CUDA
hidden: candidate 52 passed on the six CPU files, base 49 passed on the
five, 132 GPU cases skipped on both; commit messages: 0 banned words,
trailer on all 3 commits, 0 lines over 72 columns, 0 added lines with
banned words.

## Not in this PR

- **Already landed by #6758, not claimed here:**
- issue step 2: the 34 TF32 bindings (9,497 lines) are rendered from one
template;
- step 5's TMA-descriptor encoding under the prepare branch, and the
adoption of the shared device guard and tensor checks (shim 3,264 ->
3,169);
- `gpu_spec_by_sku`, one of the 16 probe classes, the piece arm, and the
four raise-only TF32 branches (now one `NotImplementedError` ladder
naming the route);
  - the runtime's copies of the planner predicates.
- **The 8 raising TF32 routes, the N16 holdout and the `sm_count in
(148, 152)` piece policy.** The issue counted 7 raising routes; the BT16
compact-output chain without checkpoints raises too. Whether to keep,
remap or export these is a product decision. The dry run documents that
no route changes.
- **Deleting `d4bf3dee`.** The public API can reach it: active beta,
bounded, 64-token checkpoints, B*H <= 8 where the affine split declines.
It is a member of the chain fold instead, so the issue's GPU test for
that selection is not added either.
- **The remaining per-call host checks** (same-device, current-device
and range checks) and replacing them with shared equivalents. That would
change error behaviour, and the checks are not proven redundant with
prepare. The dynamic-shared-memory opt-in already sits in the prepare
branch for every module with descriptors.
- **Issue step 7:** the 55-encoder table rewrite and independent token /
batch strides (the B>1 padded g / beta staging copy). This is an
exporter / ABI change shared with BF16. The TF32 bodies keep the
contiguous raw-pointer contract.
- **Exporter regeneration** (emitting the header, the fold table and the
knob macros). The bodies, the header and the registry table are hand
edits of exporter output, disclosed by the one statement.
- **Benchmarks and per-launch host-cost measurements:** none in this PR.
- **Sharing the header with the 27 BF16 kernel sources** (issue step 4's
"shared with bf16"). The BF16 fold expansion pins would first have to
learn the header substitution. The preambles stay in the kernel sources,
and three of them must keep the `int make_warp_uniform(int)` overload
(see commit 2).
- **The larger fold set** (-61,081 lines at the base text). Not taken:
two of its bodies would be very `#if`-dense, mixing binding
shared-memory / block-size classes.
- **The 10 singleton TF32 kernels:** they have no clone partner, so
nothing changes beyond the header.
- **Issue step 8.** A test that the raising shapes still raise waits for
the route decision. The three environment flags are already documented
in the repository's contributor notes at the base.
- **BF16-only leftovers in the shared runtime** (the affine knobs and
the BF16 apply route): left to the BF16 owner.

Part of #6661

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added broader TF32 KDA kernel configuration options, including
value-row layouts, beta handling, affine mapping, output formats, and
optional checkpoint generation.
- Added support for reusing shared kernel implementations across
multiple TF32 configurations.

- **Refactor**
- Simplified runtime dispatch and launch selection for supported BF16
and FP32 execution paths.
  - Consolidated CUDA device utilities used by TF32 KDA operations.

- **Tests**
- Added coverage for kernel configuration folding, metadata consistency,
conditional compilation, and source integrity.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [272ed2a](https://github.com/flashinfer-ai/flashinfer/commit/272ed2a6cf2fe66356b31b91635c26220b819fc8)

- **作者**: eigen
- **时间**: 2026-10-20T18:04:52Z
- **提交信息**: deslop(cake_fp8_gemm): table-driven batch routing, shared headers, mxfp8 and grouped source folds, dead host text (#6862)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR covers the four Cake-generated FP8 families from #6660. All four
are JIT-built, and `flashinfer/aot.py` also builds the grouped and
SiLU-quant SM100 modules:
- the batch GEMM in `csrc/cake_batch_deepgemm_fp8/`, behind
`batch_deepgemm_fp8_nt_groupwise(backend="cake")` (38 programs, 67
modules across sm_100a and sm_103a)
- the grouped GEMM in `csrc/cake_grouped_fp8_gemm/`, behind
`prepare_group_gemm_fp8_nt_groupwise_contiguous` (15 programs)
- the grouped GEMM with fused SiLU quantisation in
`csrc/cake_grouped_fp8_fused_silu_quant/`, behind
`prepare_group_gemm_fp8_nt_groupwise_contiguous_silu_quant` (5 programs)
- the opt-in grouped MXFP8 quantize in
`csrc/cake_grouped_mxfp8_quantize/`, behind
`mxfp8_grouped_quantize(backend="cake")` (2 programs)

The PR has five commits. They drop dead host text, build the fp16 mxfp8
program from the bf16 source, replace the batch loader's two rendered
route chains with a 56-row data table, move the repeated device preamble
and host helpers into shared headers, and build the three grouped
`deepk_c2` programs from one source.

Against upstream main `9c68e44fd2a7664d53d49168ed616aa8c06ef1f7`
(2026-10-20), head a56fc72e83af791dc8326ac734ec5a29d96c538e changes 98
files (+1,434 / -15,211). In `csrc/`, 7 generated files are deleted, 1
header is added and 84 files are modified. The batch loader goes from
6,381 to 1,548 lines.

No kernel body changes. Every program keeps its module name, JIT spec
name, kernel symbol (`kernel_cake_<family>_<digest>`) and host-shim
namespace (`cake_host_shim_<16 hex>`). Every library still exports its
own kernel symbol, `<own shim>::Run` and `__tvm_ffi_run`.

The 89 touched generated files are the 85 sources and headers plus the
four loaders. Each carries this disclosure once (the loaders in their
docstrings): "Generated by Cake for FlashInfer. Exporter output,
hand-edited here pending exporter support." The two hand-written host
modules carry none because they are not exporter output.

Behaviour changes (all deliberate):
- **Grouped host text (commit 1).**
- The duplicated `(m, n, k) == (4096, 2048, 4096)` arm of the grouped
host's `route_for_shape` is gone. An earlier arm already returns for
that triple.
- The grouped and SiLU-quant loaders now read their flat `ROUTES` tables
directly. Before, they went through a per-architecture lookup that
always fell back to the same table.
- Every architecture a caller can produce gets the same answer as
before. No caller produces an architecture string equal to a route-name
key. If one did, it would now raise `NotImplementedError` where the base
raised `AttributeError`.
- **mxfp8 fold (commit 2).**
  - The fp16-input kernel and binding sources are deleted.
- The fp16 module builds from the bf16 sources with the compile
definitions `IS_BF16=0`, `CAKE_PROGRAM_KERNEL=<its own kernel symbol>`
and `CAKE_PROGRAM_SHIM=<its own shim namespace>`. The kept sources'
`#ifndef` defaults are the bf16 program's values.
- The fp16 library still exports `kernel_…e5d70aeb…` and its own
`cake_host_shim_…::Run`.
- The two fp16 spec names are reused with changed sources and flags, so
an existing JIT workspace rebuilds them.
- The launch error message is assembled from adjacent string literals,
which become one literal after preprocessing.
- **Batch route table (commit 3).**
- The two rendered route chains become one 56-row table, `_ROUTES`, read
by a first-match interpreter `select(arch, sm, B, M, N, K, expected_m)`.
It returns the same route-plan objects as before.
- `DISPATCH_TABLES[arch][sm]` is now `functools.partial(select, arch,
sm)` with the same keys. `route_chain`, `select_route`, `__all__` and
the tests are unchanged.
- Every per-architecture difference between the chains is kept. Text
proven never selected is dropped (see commit 3).
- **Shared headers (commit 4).**
- The batch kernels, the batch bindings and the SiLU-quant family now
include shared headers instead of their inlined copies.
- When the compiler emits an out-of-line symbol for
`CakeSetMaxDynamicSmem`, that symbol moves to the
`cake_host_shim_common` namespace.
- When a check fails inside a shared helper, the backtrace names the
header's file and line.
- **Grouped `deepk_c2` fold (commit 5).**
- The `cd2dca…` and `80f755…` kernel and binding sources are deleted.
Both programs build from the kept `917859…` sources with these compile
definitions:
    - `CAKE_KG4=0`: K-group 1 instead of 4, at 11 sites.
- `CAKE_SCALAR_STORE=1`: `80f755…` only; the scalar-store epilogue, at 3
sites.
    - `CAKE_SMEM_TOTAL=199296`.
    - Their own kernel-symbol and shim-namespace definitions.
  - Each library still exports its own symbol and namespace.
- The two programs' spec names are reused with changed sources and
flags.
- The grouped `csrc/` goes from 33 to 29 entries. Routes and module
names are unchanged.
- **Tests, benchmarks and docs:** unchanged and byte-identical to the
base.

## Changes

### Commit 1 (a1bde7289) - cake_fp8_gemm: drop dead host text in the
grouped routing (3 files, +10 / -15)

This commit makes three host edits for issue step 1:
- It removes the duplicated exact-shape arm from the grouped host's
`route_for_shape`.
- It removes the per-architecture `ROUTES` lookups in the grouped and
SiLU-quant loaders. Both loaders' tables are flat `route -> program`
tables that the two architectures share.
- It corrects the SiLU-quant loader's docstring, which claimed
exporter-written content.

The issue's `serving_config` branch stays because it is a public
function that a direct caller can reach with any (SM count,
architecture) pair. The unused `#define IS_BF16` lines are removed with
the fold in commit 2.

Proof: a CPU check runs on both the base and head trees and compares:
- `route_for_shape` over a grid of every literal in the function, their
neighbours and every pinned test shape
- `route_program` and `stage_program` over every route for both
architectures

34,121 rows are identical. The other 570 are envelope rows, and their
only difference is the error type for impossible architecture strings.
The three dedicated test files on both GPUs are under Validation.

### Commit 2 (1ac086372) - cake_grouped_mxfp8_quantize: one source for
the BF16 and FP16 programs (5 files, +230 / -643)

With the program hashes masked, the bf16- and fp16-input quantize
programs differed in 33 hunks: the `#define IS_BF16` line and 16
widening blocks (the input-type conversion). Their bindings differed
only in the shim namespace, at 3 sites.

- The fp16 kernel and binding are deleted.
- The bf16 kernel carries the 16 blocks as `#if IS_BF16 / #else /
#endif` arms, and `#ifndef IS_BF16` defaults it to 1.
- Both kept sources take `CAKE_PROGRAM_KERNEL` and `CAKE_PROGRAM_SHIM`.
Their `#ifndef` defaults equal the bf16 program's values.
- The loader's fp16 record points at the bf16 sources with the three
definitions listed in the Summary.

The fp16 program keeps its own kernel symbol through a compile
definition, so no symbol mapping is involved. This covers issue step 2.
Both formatting opt-outs of the directory stay as they are.

Proof: a preprocessor-model render of the kept sources under the fp16
definitions reproduces the deleted fp16 kernel and binding token for
token (4 / 4 comparisons). 4 / 4 negative controls detect a changed
value. The following rows and tests are under Validation:
- SASS identity rows for the bf16 program on both GPUs.
- SASS fold rows on both GPUs, comparing the deleted fp16 source with
the kept source under the fp16 definitions.
- Host-gate rows for both bindings.
- The 9 cake quantize cases, including the bit-exact fp16 case.

### Commit 3 (baada7093) - cake_batch_deepgemm_fp8: drive route
selection from a data table (2 files, +522 / -5,355)

The batch loader held two rendered route chains, one per (architecture,
SM count): sm_100a / 148 and sm_103a / 152. Together they took 5,351
lines and held 84 routes, 24 of them exact-point routes. An interpreter
over a 56-row table now reproduces them.

- Each `_ROUTES` row holds:
  - the architecture scope
  - the route and parent names
- the predicate form: CTA intervals with band exclusions, exact points,
N/K sets or expected_m sets
  - the programs, with their grid formulas and argument templates
  - the workspaces
- `select` walks the rows in order and returns the same route-plan
objects (route, parent, stages with program, grid and arguments,
workspaces).
- Text proven never selected is dropped: the two raise stubs, the two
`seed_n7168_k2048` blocks, the `M <= 256` clause and the shadowed
swap-AB disjuncts. The `seed_n7168_k2048` blocks would only become live
after the swap-AB removal, which is not done here.
- Two docstrings now describe the table-driven selection: the loader's
`route_chain` and the host module header.

This covers issue step 3. The issue's "share the 29 banded routes
between arches" is done as rows with an architecture scope.

Proof:
- A standard-library-only check confirms that the table literal
reproduces the extracted literals of every kept row of the old chains,
value for value (82 kept rows). The dropped text is listed with its
interval proofs: 2 stubs, 2 rows and 6 shadowed disjuncts.
- The issue asked for an exhaustive CPU sweep that compares the old
chains with the new table for both (architecture, SM count) tables. It
covers `SUPPORTED_NK` x B in {1, 2, 4, 6, 8, 32, 64, 128, 256} x M in
{128, 256, 512, 1024, 4096, 8192, 16384} x every expected_m in [0, M],
8,245,456 rows in all. For each row it compares the route, programs,
grids, arguments and workspaces. The dropped text is hit 0 times, and
every other route is hit.
- The batch test file and the 96 masked cases on both GPUs are under
Validation.

### Commit 4 (66848adf2) - cake_fp8_gemm: share the device preamble and
host helper headers (82 files, +525 / -7,214)

Before this commit:
- Each batch kernel source repeated a 26-line preamble and about 96
lines of device helpers. The repository already ships 22 of those
helpers as content-addressed headers under `csrc/cake_device_helpers/`.
- 36 batch bindings inlined `CakeSetMaxDynamicSmem`.
- The SiLU-quant host header was byte-identical to the grouped one.
- The SiLU-quant device header shared 117 of its 139 lines with the
grouped one.

What changes:
- New
`csrc/cake_batch_deepgemm_fp8/cake_batch_deepgemm_fp8_device_common.cuh`
(95 lines). It holds the shared preamble, `make_warp_uniform`,
`<math_constants.h>`, 20 includes of the content-addressed helper
headers and the 2 helper bodies that no such header holds.
- The 38 batch kernels include the new header and their own
`mbarrier_wait` flavour header. Each keeps its own `#define` block after
the includes.
- The 36 batch bindings include the grouped `host_common.cuh` and call
`cake_host_shim_common::CakeSetMaxDynamicSmem`.
- The SiLU-quant `host_common.cuh` is deleted, and its 5 bindings
include the grouped one.
- The SiLU-quant `device_common.cuh` includes the grouped device header
and keeps only its 6 own helpers.

This covers issue step 4, with two parts left out:
- No new `csrc/cake_common/` directory is created.
- The TMA encoders are not folded. The `EncodeTma_*` bodies differ per
program, and a template encoder needs an object-level host gate, so this
is left for a follow-up.

Proof: a render check expands each kernel's includes and compares the
result with the base source token for token (38 / 38). It also compares
the SiLU-quant device header with the base header, and the host bindings
with the base bindings. The following are under Validation:
- SASS identity rows for all 67 batch modules and 10 SiLU-quant modules.
- Host-gate rows for 64 batch modules and 10 SiLU-quant modules.
- The three dedicated test files on both GPUs.

### Commit 5 (a56fc72e8) - cake_grouped_fp8_gemm: fold the deepk_c2
triple into one source (7 files, +147 / -1,984)

The three grouped `deepk_c2` programs `917859…`, `cd2dca…` and `80f755…`
differ in 11 hunks (the K-group constant, 4 vs 1) and 3 more hunks (the
scalar-store epilogue). Their bindings differ only in one shared-memory
literal and the hashes.

- The kept `917859…` sources take the definitions listed in the Summary.
Their `#ifndef` defaults equal the kept program's values.
- The `cd2dca…` and `80f755…` kernel and binding pairs are deleted.
- The loader's two records point at the kept sources with their
definitions.
- Routes and module names are unchanged. The routes are
`deepk_c2_k_multiple_512` and the two exact-K routes.

Each folded program keeps its own kernel symbol through a compile
definition, so no symbol mapping is involved.

Proof: a render check reproduces both deleted kernels and both deleted
bindings token for token under their definitions (6 / 6 renders). 12 /
12 negative controls detect a changed value. The following are under
Validation:
- SASS identity rows for `917859…` on both GPUs.
- SASS fold rows on both GPUs, comparing each deleted program's source
with the kept source under that program's definitions.
- 6 host-gate rows.
- The grouped test file (62 cases).
`test_unaligned_output_is_written_in_place` exercises `80f755…`, and the
K=640 / 1152 shapes exercise `cd2dca…`.

## Validation

- **Device SASS gate.** There is one row per changed (program,
architecture) build.
- The candidate is compared against the base under one toolchain per
GPU, after masking instruction addresses and encodings.
- Each build unit's disassembly must contain exactly one kernel
function, and that function must be the program's own symbol.
- Flags are composed the way the loaders compose them. Fast math is on
for the 30 non-serving batch programs and off for the 8 serving batch
programs and the SiLU-quant programs. The mxfp8 loader's default fast
math is on.
- Fold rows compare a deleted source at the base with the kept source at
the head, built under the deleted program's compile definitions. That
program's own kernel symbol comes from a compile definition, so no
symbol mapping is involved.
- The route table and the dead host text add no device rows because they
are Python only.

  Results:
- sm_100a (CUDA 13.3), 46 rows: 43 identity rows (36 batch, 5
SiLU-quant, 1 mxfp8, 1 grouped), 1 mxfp8 fold row (the deleted fp16
source against the kept bf16 source under the fp16 definitions) and 2
grouped fold rows: 46 / 46 identical (36 batch + 5 SiLU-quant + 1 mxfp8
+ 1 grouped identity rows, 1 mxfp8 fold row, 2 grouped fold rows; 0
differ, 0 through an accepted-difference rule); the sm_100a rows were
compiled on the GB300 route, whose compiler reproduces its own output
exactly; on the B200 route the compiler does not reproduce its own
output for these kernels (recompiling the unchanged base source changed
the uniform-register numbering on 17 of 87 rows in one run and on 6 of
46 in a serial run), and every base-vs-head difference seen there (24 of
87 rows, then 12 of 46) is confined to register numbering with an
identical instruction skeleton; the B200 compile is therefore reported
as a cross-check only
- sm_103a on GB300 (CUDA 13.3), 41 rows: 38 identity rows (31 + 5 + 1 +
1), 1 mxfp8 fold row and 2 grouped fold rows: 41 / 41 identical on GB300
at a56fc72e8 (31 batch + 5 SiLU-quant + 1 mxfp8 + 1 grouped identity
rows, 1 mxfp8 fold row, 2 grouped fold rows; 0 differ, 0 through an
accepted-difference rule)
- **Host gate.** There is one row per changed binding build. Each row
compares the program's binding at the base, built with its base flags,
with the binding it builds at the head, built with its head flags. For
fold rows, the head side is the kept binding under the deleted program's
definitions. Both sides compile to objects with no device code. A row
passes when all three of these hold:
- The preprocessed texts are identical after normalisation, with one
exception. Only these are normalised:
    - line markers, pragma lines and blank lines
    - adjacent string-literal pieces
    - the backtrace file/line arguments of the repository's own sources

Nothing else inside a string literal is normalised. The absolute
checkout-root prefix of `__FILE__` paths is masked because the two sides
are compiled from two checkouts. The one documented exception applies to
the 64 batch rows: the `CakeSetMaxDynamicSmem` definition moves from the
program's own namespace into `cake_host_shim_common` with identical body
tokens, and the call site gains that qualifier.
- The two objects define the same set of global symbols (`<shim>::Run`,
`__tvm_ffi_run`). The moved helper's symbol is compared under its
canonical name.
  - No foreign host-shim namespace appears.

  Results:
- sm_100a, 44 rows (34 batch, 5 SiLU-quant, 1 mxfp8 identity, 1 mxfp8
fold, 1 grouped identity, 2 grouped fold): 44 / 44 OK (every row: both
bindings compile with no device code, preprocessed text identical after
the documented normalisation classes, exported global symbol sets
identical with the shared max-dynamic-shared-memory helper's namespace
move recorded on the 34 batch rows). These rows were compiled on the
GB300 route (same toolkit, compute capability 10.0 as the target) after
the B200 attempt was cut short by a storage quota on that route; a B200
re-run serves as a cross-check
- sm_103a on GB300, 40 rows (30 + 5 + 1 + 1 + 1 + 2): 40 / 40 OK on
GB300 (30 batch + 5 SiLU-quant + 2 mxfp8 + 3 grouped rows; every row:
both bindings compile with no device code, preprocessed text identical
after the documented normalisation classes, exported global symbol sets
identical with the shared max-dynamic-shared-memory helper's namespace
move recorded on the 30 batch rows); run at b2188db3a, whose csrc/ tree
is byte-identical to a56fc72e8 (the later commit changed two Python
annotation lines only)
- **Load-all.** For each family, every module of the architecture is
built through the family's real loader in one process, with a fresh JIT
workspace. Each build must meet four conditions:
  - `run` is resolvable.
- Each program gets its own distinct library. The folded programs build
distinct libraries from the shared sources.
  - The program's own kernel symbol is in its disassembly.
  - The program's own `<shim>::Run` is in its exports.

Module counts: batch 36 (B200) / 31 (GB300), grouped 15, SiLU-quant 5
and mxfp8 2 per GPU: GB300 at a56fc72e8: batch 31, grouped 15,
SiLU-quant 5, mxfp8 2 libraries built in fresh workspaces and loaded
into one process per family, distinct kernel symbols and shim namespaces
on every module, the route table registered for (sm_103a, 152); B200:
batch 36, grouped 15, SiLU-quant 5, mxfp8 2 libraries built in fresh
workspaces and loaded into one process per family at a56fc72e8, distinct
kernel symbols and shim namespaces on every module, the route table
registered for (sm_100a, 148)
- **GPU tests.** Each tree (candidate and base `9c68e44fd`) runs with a
fresh JIT workspace. All files are under `tests/gemm/` and
`tests/utils/`, inside the default collection roots, and are
byte-identical to the base. The expected results are the same on both
trees:
- The three dedicated files
(`test_cake_batch_deepgemm_fp8_nt_groupwise.py`,
`test_cake_group_gemm_fp8_nt_groupwise_contiguous.py`,
`test_cake_group_gemm_fp8_nt_groupwise_contiguous_silu_quant.py`)
collect 33 + 62 + 54 = 149 cases. All are expected to pass except two
groups that skip identically on both trees when their optional
dependency is absent: the 12 grouped CuTe-DSL comparison cases and the
14 + 3 SiLU-quant chain cases.
- The 96 cake cases of
`tests/gemm/test_groupwise_scaled_gemm_fp8.py::test_fp8_groupwise_batch_deepgemm_masked`,
selected with `-k "test_fp8_groupwise_batch_deepgemm_masked and cake"`.
Expected: 96 passed.
- The 9 cake cases of `tests/utils/test_fp8_quantize.py`. Expected: 9
passed, or 8 passed and 1 skipped when free VRAM is low.

  Results:
- B200: at a56fc72e8: the three family suites 146 passed, 3 skipped (the
grouped CuTe-DSL cases that need 128-aligned expert boundaries), 0
failed of 149 collected; the masked batch selection 96 passed; the
quantize selection 9 passed; the base revision 9c68e44fd on the same
GPU: 146 passed / 3 skipped, 96 passed, 9 passed (identical counts and
skip reasons)
- GB300: at a56fc72e8: the three family suites 146 passed, 3 skipped
(the grouped CuTe-DSL cases that need 128-aligned expert boundaries), 0
failed of 149 collected; the masked batch selection 96 passed; the
quantize selection 9 passed; the base revision 9c68e44fd on the same
GPU: 146 passed / 3 skipped, 96 passed, 9 passed (identical counts and
skip reasons)
- **CPU checks** on the head tree (one route):
- The dead-host CPU check: 34,121 rows identical and 570 envelope rows.
- The 8,245,456-row route sweep (`ROUTE_SWEEP rows=8245456 mismatches=0
exceptions=0`). Every dropped row's hit count is 0.
  - ruff, ruff format and py_compile on the 6 changed Python files.
- The repository's pre-commit hooks: ruff, mypy, and the text hooks on
the 91 changed files. clang-format is a no-op by design: the repository
configuration excludes the batch and mxfp8 directories, and the grouped
and SiLU-quant directories disable formatting.
- Stale-reference greps: the 7 deleted file names have 0 hits repo-wide,
and the deleted digests appear only in the two loaders' folded records.
  - Collected ids, base vs candidate: 149 / 96 / 9 on both.
- CPU-only pytest with CUDA hidden: 149 skipped, and the quantize file
has 3 passed / 6 skipped.
  - The imported registry views.
  - The four benchmarks' `--help`.
- The per-commit text checks: the render checks of commits 2, 4 and 5
and the table-literal check of commit 3.

Result: all passed at a56fc72e8 on a GB300-route CPU step (CUDA hidden
where noted): ruff check / ruff format / py_compile on the 6 changed
Python files and an isolated isort base-vs-head comparison; the
repository's pre-commit hooks on the changed files (ruff-check,
ruff-format, mypy on the 6 Python files; end-of-file-fixer,
trailing-whitespace, mixed-line-ending, remove-tabs, remove-crlf on 91
files; clang-format on the 85 changed csrc files, a no-op by the
repository's own exclusions) with a clean tree afterwards; route sweep
8,245,456 rows, 0 mismatches, 0 exceptions (55 old routes hit; the two
never-selected conditions are the expected ones); dead-host grid 34,121
rows, 0 mismatches (590 envelope rows); table_check 82 compared, 0
mismatches, 208 pins, 0 pin failures; gen_table output == the shipped
table region (0 differing lines); mxfp8 / grouped / helper render checks
ok; the import-level registry view equals the four loaders' literals
(batch 38 programs / 67 modules, DISPATCH_TABLES {sm_100a: [148],
sm_103a: [152]}); collected test ids identical base vs head (149 / 96 /
9); the four benchmark scripts' --help ok; commit messages: 0 banned
words, trailer on all 5 commits, 0 added lines with banned words.
- **No GPU benchmark** is run by this PR, so it makes no performance
claim. No kernel body changes, which the SASS gate checks. The host
bindings are reproduced token for token, which the host gate checks. The
exhaustive sweep shows that the route table selects the same plans as
the old chains.

## Not in this PR

- **Step 1, `serving_config` branch:** kept. It is a public function
that a direct caller can reach with any (SM count, architecture) pair.
- **Step 4 remainder.** Two parts are not done:
  - No new `csrc/cake_common/` directory is created.
- The bindings' TMA-encoder bodies, the largest remaining host
duplication, are not folded. The `EncodeTma_*` bodies differ per
program, so folding them needs a template encoder and an object-level
host gate.
- **Step 5** (remove the 5 `masked_bn` programs, their 8 exact routes
and the "12 redundant exact routes"): this is a routing change. At every
one of the 20 exact points the band selects a different program, so each
removal needs the issue's B200 / GB300 benchmarks. See also the
correction below: no exact block is redundant.
- **Step 6** (remove `eb727f…` and the `seed_large_nk_cta1` blocks): the
`expected_m == 24` points would fall to another program, so this is a
benchmark decision. The step also asks to confirm that the `M <= 256`
clause is never selected. The sweep confirms this, and commit 3 drops
the clause.
- **Step 7** (remove swap-AB): this would lift band exclusions, which is
a routing change. It would also make `seed_n7168_k2048` live and needs
the 12-shape benchmark and test rewrites.
- **Step 8** (regenerate the serving kernels with a runtime
`num_groups`): needs regeneration and benchmarks.
- **Step 9** (fold the BLOCK_N 9- and 4-cluster): the constants are
compiled into loop bounds, swizzles and shared-memory offsets. An exact
`#if`-arm fold would need about 200 arms, so this needs regeneration.
- **Step 10** (grouped routing rework, bucketed selection, the upstream
extra compile option of program `815c90…`): a product and benchmark
decision. The option stays as data.
- **Step 11** (resolve once per call; dedupe the Python helpers):
resolving once would change error timing, and callers who want one
resolution can already pass `skip_check=True`. The helper dedupe would
save about 40 net lines across 7 modules, which is not worth the churn.
- **Step 12** (keep or drop the mxfp8 cake backend): a product decision.
The fold in commit 2 is the mechanical alternative.
- **Step 13** (GPU route logging before removals): a prerequisite of the
removals above, and none of them lands here.

**Corrections to the issue text:**
- The batch chains hold 24 exact-point routes, not 26.
- None of the "12 redundant exact blocks" is redundant: at every exact
point the band would select a different program. Exactly one exact row
equals its fallback, and it is inside the swap-AB family, so it matters
only for step 7.
- The `host_common.cuh` text is identical in 5 directories under
`csrc/`, not 4.
- The Python helper duplication is 98 text-identical lines over 10
names, not about 226 over 12.
- The 8 serving batch programs are the only batch programs built without
fast math; the other 30 use it. The issue's wording implies the
opposite.

Part of #6660

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for shared BF16/FP16 grouped MXFP8 quantization
implementations.
* Added configurable grouped FP8 GEMM variants, including K-group and
scalar-output modes.

* **Bug Fixes**
* Corrected route selection by removing an unreachable shape exception.
* Standardized route-table lookup and first-match dispatch behavior
across architectures.

* **Refactor**
* Consolidated CUDA launch, memory configuration, and device helper
behavior across generated kernels without changing existing kernel
interfaces.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e1b052d](https://github.com/flashinfer-ai/flashinfer/commit/e1b052de722e193324559ba2639b26992c7b9f50)

- **作者**: eigen
- **时间**: 2026-10-20T18:04:44Z
- **提交信息**: deslop(cake_stepfun_moe): derived launchers, compact registry, routing-twin fold, 47 shared bindings, preamble hoist (#6871)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Issue #6658 was written against an earlier form of this package. Since
then, #6801 re-exported the StepFun SwiGLU fused-MoE kernels (H=4096,
I=1536, 64 experts, top-k 8; bf16 / fp8 / mxfp8 / nvfp4) in the
cake-build form. It merged on 2026-10-20 and is the base of this PR
(upstream main `af71dd7c8a841122838daacc949a4da735c92e82`). The
cake-build form has one `build.json` manifest (222 entries = 111
programs x {sm_100a, sm_103a}), the shared loader `cake_build.py`, a
registry `cake_jit.py`, a launcher module `cake_launch.py` and the
hand-written backend `cake_backend.py`. Under `csrc/cake_stepfun_moe/`
it has one kernel source and one host binding per program, plus two
shared headers. Several of the issue's findings no longer exist in this
form (see "Not in this PR"), so this PR applies the round-2 mechanics to
the new form.

The package `flashinfer/experimental/cake_stepfun_moe/` serves
`flashinfer.experimental.cake_stepfun_moe.{stepfun_moe, routing, fc1,
requant, fc2, finalize, prepare_stepfun_moe, ...}` on SM100 and SM103.
It is JIT only, with no AOT entry, and has 111 programs: routing 52, FC1
26, FC2 27, requant 2 and finalize 4.

Head aafa020be37ae0cab81fa539da25a9f8aa530a5e has five commits:
1. Derive the launchers from the registry.
2. Compact the registry and seal the manifest by content.
3. Fold one cooperative routing kernel into its twin.
4. Share 47 duplicate host bindings.
5. Hoist the duplicated `make_warp_uniform(int)` fallback into the
device header.

Together they change 149 files (+6,106 / -27,347). The per-commit counts
add up to more than this total because `build.json`, `cake_jit.py`, the
README and the backend test are each touched by more than one commit.

What stays the same:
- Every program keeps its name and its host-shim namespace
(`cake_host_shim_<16 hex>`, 111 distinct).
- Every program except the folded one keeps its kernel symbol
(`kernel_cake_stepfun_moe_<digest>`, 110 distinct).
- Every library still exports its own kernel symbol, `<own shim>::Run`
and the C entry `__tvm_ffi_run`.
- `cake_build.py`, `cake_backend.py`,
`tests/experimental/test_cake_stepfun_moe_api.py` and
`benchmarks/bench_swiglu_stepfun.py` are untouched.

The statement "Generated by Cake for FlashInfer. Exporter output,
hand-edited here pending exporter support." appears exactly once in each
of the 95 touched generated files: the registry, the launcher module,
both headers, the 9 kept bindings, the folded binding and the 81 edited
kernel sources. The loader and the 54 unchanged bindings keep the
exporter's own marker.

Behaviour changes (all deliberate):
- **Launchers (commit 1).** `cake_launch.STAGE_ARGS` is removed. Its
only reader was the launcher test. `LAUNCH[program]` is now built at
import from `PROGRAMS[program]["arg_plan"]`. It has the same keys and
the same positional call sequence (`run(*non-grid values, *grid)`).
- **Registry (commit 2).** `PROGRAMS` is expanded at import from compact
digest-keyed rows, 20 shared argument plans and per-stage tables.
- The unread record fields `native_config`, `num_tokens_static` and
`threads` are removed, along with the `pre_program` helper.
- `ROUTES` is no longer a module attribute. The catalogue now lives in
`tests/test_helpers/cake_stepfun_moe_routes.json`, which the test and
the manifest checker read.
- **Library names (commit 2).** Every entry's `closure_sha256` in
`build.json` becomes a content digest: SHA-256 over the entry name, the
architecture, its compile definitions, and each source's path and bytes.
- Every JIT spec name (`<name>_<digest[:20]>`) changes, and every
library rebuilds cold once.
  - An edited source can never reuse a cached library.
- This commit does not change kernel symbols, namespaces, sources or
flags.
- **Cooperative-routing fold (commit 3).** The float32-scores
cooperative routing program `cake_stepfun_moe_9a305f39c4182bc865be`
keeps its name, its binding and its float32 dtype check. Its library now
builds the bf16-scores twin's kernel source and launches
`kernel_cake_stepfun_moe_85e03fcd251dde9ebf18`.
`PROGRAMS[...]["kernel"]` reports the twin's symbol, and the launch
error message names it.
- **Shared bindings (commit 4).** 47 generated bindings are deleted. 94
manifest entries now each build one of 9 kept bindings, using per-entry
compile definitions.
- The definitions are `CAKE_PROGRAM_KERNEL` and `CAKE_PROGRAM_SHIM`,
plus `CAKE_BINDING_THREADS` and `CAKE_BINDING_SMEM` for the routing
groups. Each kept binding's `#ifndef` defaults are its own values.
- The definitions are visible in `build.json` `nvcc_flags` and on the
JIT command line of both translation units. They are inert in the kernel
source, which names none of these macros.
- When a host check fails in one of these programs, the backtrace
reports the shared binding's file and line. The message texts are
byte-identical.
  - The host header gains `CAKE_STRINGIZE` / `CAKE_UNSIGNED`.
- **Preamble hoist (commit 5).** The duplicated `make_warp_uniform(int)`
fallback moves into `device_common.cuh`.
- 81 kernel sources define `CAKE_NEED_INT_WARP_UNIFORM` before the
include and lose their copies.
- The 34 routing sources keep their `__as_u32` overload set (see "Not in
this PR").
  - 164 entries are re-sealed, so their library names change.
- **Tests, docs, tooling.**
- `tests/experimental/test_cake_stepfun_moe.py` goes from 1,357 to 1,486
lines and gains 3 CPU tests, so its ids go from 292 to 295. The new
tests check that the compact rows expand to the same records, that the
manifest digests recompute from the delivered sources, and that the
folded program launches its twin's kernel. No GPU id changes, and the
API suite is untouched.
- The README rows for `build.json`, `cake_jit.py`, `cake_launch.py` and
`csrc/` are rewritten ("64 bindings serve the 111 programs"). The README
stays at 167 lines. One facade sentence and one design-doc sentence also
change.
- `scripts/check_cake_build_manifests.py` (741 -> 753 lines) gains the
`refs_stepfun` reader for the routes catalogue.

## Changes

### Commit 1 (4c1c54573) - cake_stepfun_moe: derive the positional
launchers from arg_plan (3 files, +28 / -5,347)

`cake_launch.py` held 5,368 lines: 111 rendered positional launchers,
the `STAGE_ARGS` table and the `LAUNCH` dict. All of it is a pure
function of `PROGRAMS[*]["arg_plan"]`. The last three slots of every
plan are the grid triple, so one generic launcher builds the same
positional call for every program. The module becomes 49 lines that
derive `LAUNCH` at import.

Proof:
- A text-level comparison of the generic call sequence against each
exported launcher covers all 111 programs. The argument order is
identical, and the grid fills the last three slots for every program.
- The launcher test keeps its replay assertion, together with the
grid-tail invariant.
- Both suites on both GPUs are under Validation.

### Commit 2 (66a9f36ff) - cake_stepfun_moe: compact the registry, seal
the manifest by content (6 files, +4,662 / -8,301)

At the base, `PROGRAMS` held 111 verbose records in 6,420 lines:
- `kernel`, `library`, `ffi_entry`, `arches` and `sources` can be
derived.
- `native_config`, `num_tokens_static` and `threads` are read by
nothing.

`ROUTES` (135 records, 1,613 lines) is read only by the test, the README
and the manifest checker. No production code reads it.

What this commit changes:
- `PROGRAMS` becomes digest-keyed rows that are expanded at import. The
rows use 20 shared argument plans, keyed by the full `[kind, name]`
sequences, and per-stage tables.
- `ROUTES` moves to `tests/test_helpers/cake_stepfun_moe_routes.json`
(3,110 lines). The manifest checker gains a `refs_stepfun` reader for
it.
- `closure_sha256` is re-sealed as the content digest described in the
Summary.

`cake_jit.py` goes from 8,333 to 1,477 lines at this commit and is 1,481
lines at the head. This is the new-form analogue of the issue's
inventory-schema step (step 9).

Proof:
- The compact form is re-expanded and compared with the base literal
record for record: 111 records, 0 differences, the tables are equal, and
222 / 222 manifest references are equal.
- 2 new CPU tests.
- The comparison of the imported registry view on the CPU route and the
per-architecture load-all are under Validation.

### Commit 3 (db8cee468) - cake_stepfun_moe: fold the float32-scores
cooperative routing kernel (5 files, +53 / -5,068)

There are two cooperative routing kernel sources: `85e03fcd…` takes bf16
scores and `9a305f39…` takes float32 scores. Each is 5,052 lines. They
differ in one line, the declared type of the `scores` parameter, and the
kernel never reads that parameter. This is issue step 2.

What this commit changes:
- The float32 program's kernel source is deleted. Its two manifest
entries now build the twin's source.
- A one-row kernel override in the registry records the twin's symbol.
- The program's binding declares and launches the twin's kernel. This
rewrites 4 sites.

Proof:
- The hash-masked source diff is 1 line.
- The fold is proved SASS-identical with the kernel symbol mapped. Each
architecture has one fold row that compares the deleted source at the
base with the twin's source at the head, after masking instruction
addresses and encodings.
- Each architecture also has one expected-difference row in the host
gate. Its only allowed differences are the four rewrites.
- 1 new CPU test.
- The routing cases of both suites run on both GPUs.
- The gate and test results are under Validation.

### Commit 4 (8dd07a517) - cake_stepfun_moe: share 47 duplicate host
bindings via compile defines (61 files, +1,142 / -7,857)

The 111 bindings (28,293 lines at the base) fall into groups whose
members differ only in a few values:
- the kernel symbol
- the host-shim namespace
- for the routing groups, the block size and the dynamic shared memory

There are 3 strict pairs (two finalize pairs, one requant pair) and 6
routing groups (50 bindings).

What this commit changes:
- The second member of each pair and the 44 redundant routing bindings
are deleted: 47 files, 7,352 lines.
- The 9 kept bindings are parameterised with `CAKE_PROGRAM_KERNEL` /
`CAKE_PROGRAM_SHIM`, plus `CAKE_BINDING_THREADS` / `CAKE_BINDING_SMEM`
for the routing groups. Their `#ifndef` defaults equal their own values.
- 94 manifest entries carry the definitions.
- `host_common.cuh` gains `CAKE_STRINGIZE` / `CAKE_UNSIGNED`. It is 52
lines at the base and 66 at the head.

After this commit and commit 3, `csrc/` goes from 252 to 204 entries: 48
generated files are deleted (1 kernel source, 47 bindings), none are
added and 11 are modified (the 9 kept bindings, the folded binding and
`host_common.cuh`). At the head 93 are modified, because commit 5 edits
81 kernel sources and `device_common.cuh`. 110 kernel sources and 64
bindings serve the 111 programs.

Proof:
- Each kept binding is rendered with the definitions of every member of
its group. Each render reproduces the deleted binding token for token:
56 renders with 0 differing lines.
- 6 / 6 negative controls detect a changed value.
- The host gate, load-all and both suites are under Validation.

### Commit 5 (aafa020be) - cake_stepfun_moe: hoist the int warp-uniform
fallback into the header (83 files, +505 / -1,058)

At the base, 82 kernel sources carried the same `make_warp_uniform(int)`
fallback, copied into each file (81 at the head, because commit 3
deleted one of them).

What this commit changes:
- The fallback moves into `device_common.cuh`, which goes from 79 lines
at the base to 93 at the head.
- It sits under `#ifdef CAKE_NEED_INT_WARP_UNIFORM`. The 81 sources that
need it define that macro before the include.
- The 34 routing sources keep their 4-overload `__as_u32` set. Its hoist
is not in this PR (see "Not in this PR").
- The 29 FC1 / FC2 sources without the fallback are untouched and stay
byte-identical to the base.

Proof:
- A preprocess gate runs one row per edited source and architecture, 81
rows per architecture. The head's preprocessed text must equal the base
text, compared as a token stream.
- The SASS identity rows cover all 110 kernel sources.
- Both suites run on both GPUs.
- The results are under Validation.

## Validation

- **Device SASS gate.** There is one row per (program, architecture).
The candidate is compared against the base under one toolchain (CUDA
13.3), after masking instruction addresses and encodings. The gate
compiles and disassembles; it launches nothing. The rows of record for
both architectures are compiled on GB300, because the compiler on the
B200 (x86_64) host is not deterministic for some of these kernels: a
recompile of the unchanged base can differ by uniform-register renaming.
A B200 build of the sm_100a rows is a cross-check only. Each build
unit's disassembly must contain exactly one kernel function. That
function must be the program's own symbol, or the twin's symbol for the
folded program. Flags are composed the way the loader composes them,
with the manifest entry's compile definitions on the head side.
  - sm_100a, 111 rows, compiled on GB300 as described above:
- 110 identity rows compare the program's own kernel source at base and
head. 81 of these sources are edited by the preamble hoist, and 29 are
byte-identical.
- 1 fold row compares the deleted float32 routing source with the bf16
twin, with the kernel symbol mapped.
- Result: 111 / 111 identical (110 identity rows + 1 fold row; 0 rows
accepted through a fallback). The sm_100a rows of record were compiled
on the GB300 route, whose compiler reproduces these kernels
deterministically; the B200 route's compiler is not deterministic for
some of them (a recompile of the unchanged base differs by
uniform-register renaming), so a B200 run is only a cross-check
- sm_103a, the same 111 rows, compiled on GB300: 111 / 111 identical on
the GB300 route (110 identity rows + 1 fold row; 0 rows accepted through
a fallback; compiled on sm_103a, the row set `__(sm_103a)$`)
- **Host gate.** There is one row for each (program, architecture) whose
binding changed. Each row compares two builds, and both compile to
objects with no device code:
  - the program's exported binding at the base
- the binding the program builds at the head, with its compile
definitions

  A row passes when all three of these hold:
- The preprocessed texts are identical after normalising only these
items:
    - line markers
    - pragma lines
    - blank lines
    - adjacent string-literal pieces
    - the backtrace file/line arguments of the repository's own sources

The absolute checkout-root prefix of `__FILE__` paths is masked because
the two sides are compiled from two checkouts. Nothing else inside a
string literal is normalised.
- The two objects define the same set of global symbols (`<shim>::Run`,
`__tvm_ffi_run`).
  - No foreign host-shim namespace appears.

The folded program's row is an expected-difference row. Its only
differences must be these four rewrites:
  - the twin's symbol at the declaration
  - the twin's symbol at the launch site
  - the twin's symbol inside the launch message
  - the `scores` pointer type and cast

  Results:
- sm_100a on B200, 57 rows: 47 shared-binding rows, 9 kept-binding rows
(the same file, built with its defaults) and 1 fold row: 57 / 57 OK,
compiled on the GB300 route (47 shared + 9 kept + 1 fold; all 57 compile
with no device code, preprocessed texts identical after the listed
normalisation on every row, exported global symbol sets identical on all
57)
- sm_103a on GB300, the same 57 rows: 57 / 57 OK on the GB300 route (47
shared + 9 kept + 1 fold; all 57 compile with no device code,
preprocessed texts identical after the listed normalisation on every
row, exported global symbol sets identical on all 57)
- **Preprocess gate for the preamble hoist.** There is one row per
edited kernel source and architecture. The head's preprocessed token
stream must equal the base's token for token.
- 81 rows on B200: 81 / 81 identical, preprocessed on the GB300 route
(removal counts as expected on all 81: base 1 / candidate 1 for the 34
routing sources, 0 / 0 for the other 47)
- 81 rows on GB300: 81 / 81 identical on the GB300 route (removal counts
as expected on all 81: base 1 / candidate 1 for the 34 routing sources,
0 / 0 for the other 47)
- **Load-all.** Every program of the architecture is built through the
real loader in one process, with a fresh JIT workspace. Each build must
meet four conditions:
  - `run` is resolvable.
  - Each program gets its own distinct library.
- The program's own kernel symbol is in its disassembly. For the folded
program, this is the twin's symbol.
  - The program's own `<shim>::Run` is in its exports.

That is 111 libraries per GPU, with 110 distinct kernel symbols and 111
distinct host-shim namespaces: B200 (sm_100a, 148 SMs): 111 libraries
built and loaded into one process (110 distinct kernel symbols, the
folded f32-scores routing program sharing its bf16 twin's; 111 distinct
host-shim namespaces; 47 programs built from a shared binding; the run
entry resolvable on every module); GB300 (sm_103a, 152 SMs): the same
111 libraries / 110 kernel symbols / 111 namespaces / 47 shared-binding
programs
- **GPU tests.** Each tree gets a fresh JIT workspace. Both files are
invoked explicitly because they are outside the default collection
roots.
  - B200 (SM100, compute capability 10.0), expected results:
- candidate: `test_cake_stepfun_moe.py` 295 passed, 0 skipped;
`test_cake_stepfun_moe_api.py` 380 passed, 0 skipped
    - base af71dd7c8: 292 / 0 and 380 / 0
- Result: candidate 295 passed / 0 skipped on the backend suite and 380
/ 0 on the API suite. Base control (the PR's parent in a fresh JIT
workspace of its own): 292 / 0 on the backend suite; the base API-suite
run was interrupted by a storage fault of the compute node (22
stale-file-handle errors after 369 of its 380 cases had passed; no
assertion failed), and the cluster entered a two-day maintenance window
before the run could be repeated. The base control is complete on GB300
(below); the B200 repeat is scheduled after the maintenance window and
its result will be posted on this PR
- GB300 (SM103, compute capability 10.3), the same expected results
(candidate 295 / 0 + 380 / 0; base 292 / 0 + 380 / 0): candidate 295
passed / 0 skipped on the backend suite and 380 / 0 on the API suite;
base (the PR's parent) 292 / 0 and 380 / 0 in a fresh JIT workspace of
its own (the three extra candidate cases are the new CPU tests)
- **CPU checks** on the head tree (one route):
  - ruff, ruff format and py_compile on the 4 changed Python files.
  - The repository's pre-commit hooks:
    - ruff
    - mypy on the two package modules
    - the text hooks on the changed non-`csrc` text files

The repository configuration excludes `csrc/` from every hook, and the
package's `.clang-format` disables formatting.
- Stale-reference greps for the 48 deleted file names, the deleted
kernel symbol and the removed Python names: 0 hits repo-wide.
  - The manifest checker on the package: 0 findings.
- Collected ids: base 292 and candidate 295, plus 380 / 380 for the API
suite.
  - CPU-only pytest with CUDA hidden:
- candidate: 10 passed / 285 skipped, and 380 skipped in the API suite
    - base: 7 / 285, and 380 skipped
- The imported registry view compared with the text expansion (111
programs, 222 library names).
  - The benchmark's `--help`.
  - The per-commit text checks:
    - launcher equivalence
    - registry check
    - twin and render checks
    - binding render check
    - preamble render check
  - Commit-message checks.

Result: all passed at aafa020be on a GB300-route CPU step (CUDA hidden
where noted): ruff check / ruff format / py_compile on the 4 changed
Python files and an isolated isort base-vs-head comparison (0 / 0
findings on each file); the repository's pre-commit hooks on the changed
non-`csrc` files (ruff-format, mypy, end-of-file-fixer,
trailing-whitespace, mixed-line-ending, remove-tabs, remove-crlf and
check-added-large-files all passed; ruff-check had no file in its scope)
with a clean tree afterwards, plus a stdlib replica of the text hooks
over the 93 edited `csrc` files (0 CR / CRLF, tabs, trailing whitespace
or missing final newlines); stale-reference greps: 0 hits repo-wide for
the 48 deleted file names, the deleted kernel symbol and the removed
Python names, and the expected counts for every kept marker (81 guard
defines, 136 `__as_u32` definitions in the 34 routing kernel sources and
0 in the shared header, 9 kept bindings, 94 + 88 re-pointed manifest
entries); the manifest checker: checked 1 package(s), 0 finding(s);
collected ids base 292 / candidate 295 (the 3 added CPU tests, no GPU id
changes) and 380 / 380 for the API suite; CPU-only pytest with CUDA
hidden: candidate 10 passed / 285 skipped, base 7 / 285, and 380 skipped
on both sides of the API suite; the imported registry view equals the
text expansion (111 programs, 222 library names, 110 distinct kernel
symbols, 135 routes); the benchmark's `--help` ok; per-commit text
checks: launcher equivalence (111 programs, generic == exported for
all), registry check (111 records, 0 differences, 222 manifest refs),
re-seal (0 stale entries of 222), twin and render checks ok, binding
render check (56 programs rendered, 47 re-pointed, 9 kept, 0 differing
lines, 6 / 6 negative controls), host fold compare (0 residual
differences), preamble scan and render check (110 kernel sources, 110
identical after the normalisation, the 34 routing sources keep their
`__as_u32` set in place); the shipped gate entry files equal their
regeneration on the delivered tree (222 SASS rows, 114 host rows, 108
header rows, 162 preprocess rows); commit messages: 0 banned words,
trailer on all 5 commits, 0 lines over 72 columns, 0 added lines with
banned words.
- **No GPU benchmark** is run by this PR, and the PR makes no latency
claim. No kernel body changes: SASS identity covers every kernel, and
the folded source differs only in the type of an unread parameter. The
host launch code is reproduced token for token.

## Not in this PR

- **Step 1** (delete the mxfp8 FC2 tile-32 kernel): not done. In the new
form, the kernel (`94969f03…`) is still in use:
- It is reachable through the package's public `fc2()` / `prepare_fc2`
entries.
  - Two GPU test cells exercise it.
  - A route measures it.

  Retiring it is a product decision.
- **Steps 3-8**: moot after the re-export. None of these exist in the
cake-build form:
  - the dead host ops
  - the `CAKE_STEPFUN_FC1_*` environment hooks
  - the unused `host_common.cuh` and `TARGET_MINOR` guards
  - the FC1-only build filtering
- the per-call tile-ladder / SM-count work, which is now cached once per
runner
  - the test-only ops
- **Step 9 remainder** (inventory schema): commit 2 is the new-form
analogue. The per-architecture duplication of `sources` / `sha256` in
`build.json` stays, because it is the shared cake-build schema that
several Cake packages use.
- **Steps 10-11** (exporter): not done. These items need exporter
templates:
- The 36 exact-token-count routing kernels (T=5..16 x {bf16 scores, f32
scores, top-k ids}). They form three 12-member clusters with 19,558
redundant lines.
- The 17 constant-clone clusters, with 54,480 redundant lines at < 12 %
normalised difference.
- FC1 / FC2 binding templating, about 19,000 lines with 76 TMA-encoder
bodies.
- **Step 12** (tests: f32 logits and more token counts; the `top_k != 8`
/ `topk_ids` limits): this is coverage work, not a deslop step. 41
routing programs are launched by no test, both at the base and at the
head.
- **Step 13** (delete three inventory tests): not done. The manifest
checker is not wired into CI, so the test remains the only automatic
guard.
- **`FLASHINFER_CAKE_STEPFUN_FULL_PATH` /
`CakeStepFunConfig(full_path=...)`**: stays. It is a documented negative
path that the API suite pins, and removing it would change behaviour for
users who set it.
- **28 unread `HOST_PLAN_CONSTANTS` leaves**: stay. The backend's
constants accessor reads them, and trimming them is a behaviour
decision.
- **The `__as_u32` overload set of the 34 routing kernel sources**:
stays in those sources. Hoisting it into `device_common.cuh` changed the
SM100 device code of one FC1 kernel that never calls the overloads (its
sm_100a disassembly differed from the base after masking instruction
addresses and encodings, while its sm_103a row was identical), so that
step is left for later.
- **Content digest and the shared headers.** Today, editing a header
does not rename a library. Whether the digest should also cover the two
shared headers belongs to the shared-loader discussion.

```experimental-tests
tests/experimental/test_cake_stepfun_moe.py
tests/experimental/test_cake_stepfun_moe_api.py
```

Part of #6658

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added support for reusing shared launcher bindings across StepFun MoE
programs, with configurable kernel names and launch settings.
- Added comprehensive route coverage for FC, routing, finalize,
full-model, and quantization variants across supported data formats and
GPU architectures.

- **Documentation**
- Updated API and package documentation for manifest digests, shared
argument plans, launcher behavior, registry structure, and shared
bindings.

- **Refactor**
  - Consolidated warp-uniform support through shared device utilities.
- Removed obsolete generated launchers and their exported entry points.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6021353](https://github.com/flashinfer-ai/flashinfer/commit/60213537ce15b522fa75e4526187f505ec36ff70)

- **作者**: eigen
- **时间**: 2026-10-20T17:56:03Z
- **提交信息**: perf(cake_w8a8_megamoe_ep16): evict-first L2 hint on the FC2 weight loads (#6857)

The experimental W8A8 MegaMoE EP16 backend `sm103_mxfp8_mxfp8_bf16_cake`
has one data-type variant: MXFP8 activations × MXFP8 weights with BF16
output. It runs a single fixed configuration of 16 ranks, 32 experts per
rank, hidden 3072, intermediate 5120 and top-8 routing. It is built from
six generated device kernels: `publish_push`, `local_pack`, `fc1`,
`fc2`, `combine` and `quantize_weights`. This PR regenerates only `fc2`
and its manifest entry. `fc2` is the SwapAB FC2 GEMM fused with the
routed scatter of its outputs. Every expert-weight (A) and weight-scale
(SFA) TMA load in it now carries an L2 evict-first cache hint. The other
five kernels and the host package are unchanged. Compared with the
kernels on main (PR #6796), forward latency of the full MoE layer is
about 0.8% lower (geomean ratio 0.992) across the six shapes below.
Per-shape ratios range from 0.986 to 0.995.

**16 × NVIDIA GB300 (sm_103a) in one NVL72 block, CUDA 13.3.** Forward
span of the full MoE layer, as the rank-max CUPTI median under
CUDA-graph replay. Both arms ran on the same nodes in mirrored pairs.
Ratio = this PR / main; lower is better.

| Tokens per rank (T) | Routing | main (PR #6796), µs | this PR, µs |
Ratio |
|---:|---|---:|---:|---:|
| 256 | balanced | 265.2 | 263.9 | 0.995 |
| 256 | hot-set | 263.4 | 261.9 | 0.994 |
| 512 | balanced | 267.8 | 265.4 | 0.991 |
| 512 | hot-set | 266.5 | 264.9 | 0.994 |
| 1024 | balanced | 272.8 | 268.9 | 0.986 |
| 1024 | hot-set | 273.0 | 270.1 | 0.990 |

This MXFP8 × MXFP8 → BF16 family ships only for sm_103a (GB300). Cake's
other MegaMoE EP16 variant, the BF16-activation × MXFP8-weight family
`cake_mxfp8_megamoe_ep16`, ships on sm_100a and sm_103a.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5ea5018](https://github.com/flashinfer-ai/flashinfer/commit/5ea501832bf7e37a7acde903a32329d580c0e9b4)

- **作者**: eigen
- **时间**: 2026-10-20T17:49:54Z
- **提交信息**: refactor(cake_minimax_h3_qkv_quantize_pack): regenerate the kernels and route the host through the in-tree program loader (#6869)

`minimax_h3_qkv_quantize_pack` is the MiniMax H3 fused QKV quantize +
pack kernel. Cake has eight variants of it: MXFP8 output and NVFP4
output, each with pack factor P = 1, 2, 4 and 8. This PR delivers all
eight on sm_100a and sm_103a. The baseline is the previous Cake version
of the same kernel: the loader shipped at FlashInfer main 23f3e8f6. Each
variant was timed on the six shapes in the owner's shape list. On GB300
(sm_103a), the geomean speedup is 1.000 for all eight variants. On B200
(sm_100a), it is 1.000 for six variants, 0.999 (a slowdown) for MXFP8_P8
and 1.001 for NVFP4_P8.

### MXFP8_P1 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=33472, unit | 321.455 | 321.327 | 1.000 |
| M=38592, unit | 369.726 | 369.839 | 1.000 |
| M=48768, unit | 465.039 | 464.991 | 1.000 |
| M=58944, unit | 560.734 | 560.863 | 1.000 |
| M=74240, unit | 703.759 | 704.062 | 1.000 |
| M=109952, unit | 1038.077 | 1037.886 | 1.000 |

Geomean speedup over 6 shapes: 1.000.

### MXFP8_P2 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=16736, unit | 165.280 | 165.376 | 0.999 |
| M=19296, unit | 189.856 | 189.983 | 0.999 |
| M=24384, unit | 238.240 | 238.016 | 1.001 |
| M=29472, unit | 286.511 | 286.447 | 1.000 |
| M=37120, unit | 359.087 | 358.959 | 1.000 |
| M=54976, unit | 528.911 | 529.230 | 0.999 |

Geomean speedup over 6 shapes: 1.000.

### MXFP8_P4 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=8368, unit | 85.744 | 85.743 | 1.000 |
| M=9648, unit | 97.968 | 97.968 | 1.000 |
| M=12192, unit | 122.415 | 122.400 | 1.000 |
| M=14736, unit | 147.056 | 147.056 | 1.000 |
| M=18560, unit | 183.456 | 183.536 | 1.000 |
| M=27488, unit | 268.655 | 268.927 | 0.999 |

Geomean speedup over 6 shapes: 1.000.

### MXFP8_P8 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=4184, unit | 45.871 | 45.936 | 0.999 |
| M=4824, unit | 52.384 | 52.368 | 1.000 |
| M=6096, unit | 64.288 | 64.336 | 0.999 |
| M=7368, unit | 76.432 | 76.512 | 0.999 |
| M=9280, unit | 94.736 | 94.799 | 0.999 |
| M=13744, unit | 137.792 | 137.760 | 1.000 |

Geomean speedup over 6 shapes: 0.999.

### NVFP4_P1 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=33472, unit | 266.944 | 267.135 | 0.999 |
| M=38592, unit | 305.872 | 305.887 | 1.000 |
| M=48768, unit | 383.423 | 383.312 | 1.000 |
| M=58944, unit | 461.423 | 461.279 | 1.000 |
| M=74240, unit | 577.534 | 577.279 | 1.000 |
| M=109952, unit | 851.727 | 850.686 | 1.001 |

Geomean speedup over 6 shapes: 1.000.

### NVFP4_P2 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=16736, unit | 140.000 | 139.968 | 1.000 |
| M=19296, unit | 159.200 | 159.184 | 1.000 |
| M=24384, unit | 198.528 | 198.464 | 1.000 |
| M=29472, unit | 238.000 | 237.984 | 1.000 |
| M=37120, unit | 296.303 | 296.255 | 1.000 |
| M=54976, unit | 433.183 | 433.167 | 1.000 |

Geomean speedup over 6 shapes: 1.000.

### NVFP4_P4 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=8368, unit | 75.232 | 75.232 | 1.000 |
| M=9648, unit | 85.136 | 85.184 | 0.999 |
| M=12192, unit | 105.056 | 104.928 | 1.001 |
| M=14736, unit | 124.384 | 124.319 | 1.001 |
| M=18560, unit | 154.720 | 154.719 | 1.000 |
| M=27488, unit | 223.807 | 223.840 | 1.000 |

Geomean speedup over 6 shapes: 1.000.

### NVFP4_P8 on sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=4184, unit | 41.744 | 41.695 | 1.001 |
| M=4824, unit | 47.136 | 47.200 | 0.999 |
| M=6096, unit | 57.344 | 57.184 | 1.003 |
| M=7368, unit | 67.249 | 67.360 | 0.998 |
| M=9280, unit | 82.464 | 82.272 | 1.002 |
| M=13744, unit | 117.407 | 117.376 | 1.000 |

Geomean speedup over 6 shapes: 1.001.

### MXFP8_P1 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=33472, unit | 307.760 | 307.648 | 1.000 |
| M=38592, unit | 354.272 | 354.432 | 1.000 |
| M=48768, unit | 445.120 | 445.184 | 1.000 |
| M=58944, unit | 536.385 | 536.369 | 1.000 |
| M=74240, unit | 673.314 | 673.361 | 1.000 |
| M=109952, unit | 995.712 | 995.553 | 1.000 |

Geomean speedup over 6 shapes: 1.000.

### MXFP8_P2 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=16736, unit | 158.832 | 158.847 | 1.000 |
| M=19296, unit | 182.896 | 182.896 | 1.000 |
| M=24384, unit | 229.167 | 229.216 | 1.000 |
| M=29472, unit | 274.016 | 273.984 | 1.000 |
| M=37120, unit | 343.648 | 343.680 | 1.000 |
| M=54976, unit | 505.808 | 505.648 | 1.000 |

Geomean speedup over 6 shapes: 1.000.

### MXFP8_P4 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=8368, unit | 82.896 | 82.783 | 1.001 |
| M=9648, unit | 94.384 | 94.560 | 0.998 |
| M=12192, unit | 117.744 | 117.632 | 1.001 |
| M=14736, unit | 140.816 | 140.640 | 1.001 |
| M=18560, unit | 175.663 | 175.568 | 1.001 |
| M=27488, unit | 256.849 | 256.993 | 0.999 |

Geomean speedup over 6 shapes: 1.000.

### MXFP8_P8 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=4184, unit | 44.016 | 43.984 | 1.001 |
| M=4824, unit | 50.208 | 50.144 | 1.001 |
| M=6096, unit | 61.696 | 61.792 | 0.998 |
| M=7368, unit | 73.568 | 73.552 | 1.000 |
| M=9280, unit | 91.072 | 90.992 | 1.001 |
| M=13744, unit | 131.984 | 131.856 | 1.001 |

Geomean speedup over 6 shapes: 1.000.

### NVFP4_P1 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=33472, unit | 261.280 | 261.280 | 1.000 |
| M=38592, unit | 298.768 | 299.104 | 0.999 |
| M=48768, unit | 374.433 | 374.481 | 1.000 |
| M=58944, unit | 449.952 | 450.016 | 1.000 |
| M=74240, unit | 563.680 | 563.760 | 1.000 |
| M=109952, unit | 829.904 | 830.113 | 1.000 |

Geomean speedup over 6 shapes: 1.000.

### NVFP4_P2 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=16736, unit | 136.880 | 136.784 | 1.001 |
| M=19296, unit | 156.928 | 156.864 | 1.000 |
| M=24384, unit | 194.512 | 194.640 | 0.999 |
| M=29472, unit | 232.256 | 232.256 | 1.000 |
| M=37120, unit | 289.728 | 289.824 | 1.000 |
| M=54976, unit | 423.345 | 423.344 | 1.000 |

Geomean speedup over 6 shapes: 1.000.

### NVFP4_P4 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=8368, unit | 73.824 | 73.792 | 1.000 |
| M=9648, unit | 83.168 | 83.136 | 1.000 |
| M=12192, unit | 102.672 | 102.721 | 1.000 |
| M=14736, unit | 122.416 | 122.512 | 0.999 |
| M=18560, unit | 151.184 | 150.912 | 1.002 |
| M=27488, unit | 218.433 | 218.496 | 1.000 |

Geomean speedup over 6 shapes: 1.000.

### NVFP4_P8 on sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=4184, unit | 40.288 | 40.384 | 0.998 |
| M=4824, unit | 45.552 | 45.440 | 1.002 |
| M=6096, unit | 55.632 | 55.568 | 1.001 |
| M=7368, unit | 65.616 | 65.584 | 1.000 |
| M=9280, unit | 80.368 | 80.321 | 1.001 |
| M=13744, unit | 115.104 | 115.072 | 1.000 |

Geomean speedup over 6 shapes: 1.000.

Cake has no variants of this kernel other than these eight; Cake ships
it on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added ahead-of-time and runtime support for MiniMax H3 QKV
quantization and packing in NVFP4 and MXFP8 formats.
- Added support for NVIDIA `sm_100a` and `sm_103a` targets across
multiple partition configurations.
- Improved CUDA execution with validated tensor inputs, device
placement, launch dimensions, and clearer runtime errors.
- Added automatic kernel selection and launch-grid calculation based on
device and runtime dimensions.

- **Bug Fixes**
- Improved quantization scale handling, output packing, padding, and
boundary-token processing for more reliable results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [918d3e2](https://github.com/flashinfer-ai/flashinfer/commit/918d3e26c8377a14ae5df3062e964ecfd57b7970)

- **作者**: yufeiwu-nv
- **时间**: 2026-10-20T17:45:05Z
- **提交信息**: fix(benchmarks): skip unsupported CUTLASS MLA head counts (#6451)

<!-- .github/pull_request_template.md -->

## 📌 Description

A multi-backend `BatchMLAPagedAttentionWrapper` benchmark with a non-128
query-head count currently reaches CUTLASS planning and raises `Expected
128 heads`, aborting the case before the remaining backends finish.
Filter CUTLASS out alongside its existing page-size and dtype checks,
logging the requested head count. Supported 128-head inputs retain their
current behavior.

## 🔍 Related Issues

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

Changed-file hooks passed with `pre-commit run --files
benchmarks/routines/attention.py`; the full-tree hook suite was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validation: a temporary CPU-only harness executed the actual CUTLASS
filter block across 60 combinations of head count, page size, query
dtype, and KV dtype. It verified unsupported combinations are removed,
supported 128-head combinations remain, other backends are preserved,
and head-count skip messages are emitted. `git diff --check` passed. No
new test files were added. GPU benchmarks were not run.

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

This change aligns benchmark eligibility with the existing CUTLASS MLA
input validation; it does not alter the kernel or the library
validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* CUTLASS is now skipped for attention benchmarks with query/output head
counts other than 128, with an informational message.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [013f02e](https://github.com/flashinfer-ai/flashinfer/commit/013f02e75ddf8430ad010b965b2d5047c370f576)

- **作者**: lunarz-dev
- **时间**: 2026-10-20T17:44:32Z
- **提交信息**: fix(benchmark): use HND layout for cuDNN paged prefill (#6846)

<!-- .github/pull_request_template.md -->

## 📌 Description

The paged-prefill benchmark passes K/V tensors shaped `[pages, heads,
page_size, dim]` (HND) to the cuDNN wrapper, but declares their layout
as NHD. The wrapper consequently swaps the head and page dimensions
before calling cuDNN. With 8 KV heads and page size 16, this produces
page-table dimension errors or a GQA head-count error (for example, 40
query heads are incorrectly compared against 16 KV heads).

Declare HND when constructing the cuDNN paged-prefill wrapper to match
the tensors actually supplied. This restores execution of the affected
benchmark cases.

The paged-prefill benchmark already supplied HND-shaped K/V tensors when
this wrapper call declared `NHD`. The earlier cuDNN wrapper forwarded
those tensors without converting according to `kv_layout`, so the
incorrect declaration did not trigger this dimension swap. PR #5350
added the NHD-to-HND conversion needed to honor the wrapper's layout
contract, exposing the stale benchmark declaration: heads and page size
were then swapped. This change updates the benchmark declaration to
match its actual input tensors while preserving the wrapper's correct
layout handling.

## 🔍 Related Issues

No linked issue.

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

Changed-file checks passed: `pre-commit run --files
benchmarks/routines/attention.py` and `git diff --check`. The full
repository hook sweep was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated the existing benchmark on B200 with CUDA 13.0, cuDNN
9.27.0.42, and cuDNN Frontend 1.31.0:

```bash
python3 flashinfer_benchmark.py \
  --routine BatchPrefillWithPagedKVCacheWrapper --backends fa2 cudnn \
  --page_size 16 --batch_size 1 --s_qo 8192 --s_kv 8192 \
  --num_qo_heads 40 --num_kv_heads 8 --head_dim_qk 128 --head_dim_vo 128 \
  --q_dtype bfloat16 --kv_dtype bfloat16 --causal --refcheck -vv
```

Both backends completed and produced CSV rows. Strict reference checking
against FA2 passed with `allow_output_mismatch=False`; cuDNN median
latency was 0.600 ms. This validates the representative BF16 case; FP8
and GB300 were not tested.

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

Only the benchmark wrapper layout and its comment change; no kernel code
changes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected the cuDNN paged-prefill operation to use the appropriate
key-value cache layout, improving compatibility with cached attention
data.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0d062af](https://github.com/flashinfer-ai/flashinfer/commit/0d062af33b6b42786bc5442acb802dd265242355)

- **作者**: eigen
- **时间**: 2026-10-20T17:44:20Z
- **提交信息**: perf(cake_rmsnorm): faster H1536 / H4096 grad (SM100 / SM103 / SM107) (#6842)

`cake_rmsnorm_train` is Cake's RMSNorm training kernel: one data type
(BF16 activations and weight, FP32 `rstd` and deterministic FP32
`dweight`) in four variants, plain and residual-fused, each forward and
backward. This PR changes the plain backward (`dx`, `dweight`) at H=1536
and H=4096 for row counts above T=1024 and T=256 respectively on sm_100a
/ sm_103a, and above T=2048 and T=1024 on sm_107a. The new cooperative
persistent programs stage the `dy` / `x` rows through a `cp.async.bulk`
+ `mbarrier` shared-memory ring and keep the previous backward's dot
product and deterministic fixed-order FP32 `dweight` reduction under the
same numerical contract; the forward and the other hidden sizes are
unchanged. Against the previous Cake version (PR #6792), the new
backward is 1.08-1.13x faster on B200, 1.08-1.13x on GB300 and
1.03-1.22x on R200, and forward + backward is 1.05-1.08x, 1.05-1.08x and
1.02-1.13x faster.

Both versions run in the same process on the same GPU. Latencies are
CUPTI kernel-active times (T x H input, cold L2 before every launch),
each the median of 3 counterbalanced paired groups. `bwd` is the
backward, `step` is forward + backward, and Speedup = previous / new
latency (above 1.000x the new version is faster). Rows at or below those
thresholds run the unchanged program on both sides, so their ratios are
measurement noise around 1.000x. Both versions are compiled with CUDA
13.4; the host runs PyTorch 2.14.1+cu130.

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 1536 | 256 | bwd | 5.66 | 5.70 | 0.994x |
| 1536 | 256 | step | 8.10 | 8.03 | 1.008x |
| 1536 | 1024 | bwd | 7.62 | 7.49 | 1.017x |
| 1536 | 1024 | step | 10.62 | 10.59 | 1.003x |
| 1536 | 4096 | bwd | 13.60 | 12.32 | 1.104x |
| 1536 | 4096 | step | 20.00 | 18.59 | 1.076x |
| 1536 | 14928 | bwd | 31.81 | 28.48 | 1.117x |
| 1536 | 14928 | step | 48.06 | 44.77 | 1.074x |
| 1536 | 15288 | bwd | 32.58 | 29.02 | 1.122x |
| 1536 | 15288 | step | 48.67 | 45.34 | 1.073x |
| 1536 | 15566 | bwd | 32.73 | 29.41 | 1.113x |
| 1536 | 15566 | step | 49.50 | 46.14 | 1.073x |
| 1536 | 15590 | bwd | 32.93 | 29.41 | 1.120x |
| 1536 | 15590 | step | 49.22 | 46.02 | 1.070x |
| 1536 | 16114 | bwd | 33.57 | 30.27 | 1.109x |
| 1536 | 16114 | step | 50.46 | 47.10 | 1.071x |
| 1536 | 16132 | bwd | 33.57 | 30.30 | 1.108x |
| 1536 | 16132 | step | 50.27 | 46.94 | 1.071x |
| 1536 | 16164 | bwd | 33.66 | 30.08 | 1.119x |
| 1536 | 16164 | step | 50.46 | 46.94 | 1.075x |
| 1536 | 16263 | bwd | 33.92 | 30.24 | 1.122x |
| 1536 | 16263 | step | 50.78 | 47.33 | 1.073x |
| 1536 | 32768 | bwd | 60.61 | 54.62 | 1.110x |
| 1536 | 32768 | step | 92.22 | 86.62 | 1.065x |
| 1536 | 65536 | bwd | 113.53 | 100.96 | 1.125x |
| 1536 | 65536 | step | 173.95 | 161.98 | 1.074x |
| 4096 | 256 | bwd | 7.07 | 7.04 | 1.005x |
| 4096 | 256 | step | 9.50 | 9.70 | 0.980x |
| 4096 | 1024 | bwd | 11.46 | 10.30 | 1.112x |
| 4096 | 1024 | step | 15.55 | 14.43 | 1.078x |
| 4096 | 4096 | bwd | 24.90 | 22.88 | 1.088x |
| 4096 | 4096 | step | 37.57 | 35.33 | 1.063x |
| 4096 | 14928 | bwd | 70.34 | 63.71 | 1.104x |
| 4096 | 14928 | step | 106.94 | 101.18 | 1.057x |
| 4096 | 15288 | bwd | 72.22 | 65.31 | 1.106x |
| 4096 | 15288 | step | 109.34 | 103.78 | 1.054x |
| 4096 | 15566 | bwd | 72.74 | 67.07 | 1.084x |
| 4096 | 15566 | step | 110.56 | 105.47 | 1.048x |
| 4096 | 15590 | bwd | 73.09 | 67.33 | 1.086x |
| 4096 | 15590 | step | 111.55 | 106.37 | 1.049x |
| 4096 | 16114 | bwd | 75.39 | 68.48 | 1.101x |
| 4096 | 16114 | step | 114.56 | 108.96 | 1.051x |
| 4096 | 16132 | bwd | 75.20 | 68.29 | 1.101x |
| 4096 | 16132 | step | 114.66 | 108.86 | 1.053x |
| 4096 | 16164 | bwd | 74.98 | 68.90 | 1.088x |
| 4096 | 16164 | step | 114.50 | 109.50 | 1.046x |
| 4096 | 16263 | bwd | 75.65 | 68.83 | 1.099x |
| 4096 | 16263 | step | 115.68 | 109.66 | 1.055x |
| 4096 | 32768 | bwd | 140.93 | 129.18 | 1.091x |
| 4096 | 32768 | step | 219.30 | 208.03 | 1.054x |
| 4096 | 65536 | bwd | 274.53 | 248.48 | 1.105x |
| 4096 | 65536 | step | 429.20 | 403.33 | 1.064x |

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 1536 | 256 | bwd | 5.44 | 5.47 | 0.994x |
| 1536 | 256 | step | 7.71 | 7.68 | 1.004x |
| 1536 | 1024 | bwd | 7.10 | 7.23 | 0.982x |
| 1536 | 1024 | step | 10.21 | 10.11 | 1.009x |
| 1536 | 4096 | bwd | 12.83 | 11.68 | 1.099x |
| 1536 | 4096 | step | 19.17 | 17.98 | 1.066x |
| 1536 | 14928 | bwd | 31.01 | 27.55 | 1.125x |
| 1536 | 14928 | step | 46.11 | 42.88 | 1.075x |
| 1536 | 15288 | bwd | 31.14 | 27.94 | 1.115x |
| 1536 | 15288 | step | 46.69 | 43.52 | 1.073x |
| 1536 | 15566 | bwd | 31.84 | 28.42 | 1.120x |
| 1536 | 15566 | step | 47.65 | 44.29 | 1.076x |
| 1536 | 15590 | bwd | 32.00 | 28.51 | 1.122x |
| 1536 | 15590 | step | 47.65 | 44.42 | 1.073x |
| 1536 | 16114 | bwd | 32.00 | 28.90 | 1.107x |
| 1536 | 16114 | step | 48.16 | 45.15 | 1.067x |
| 1536 | 16132 | bwd | 32.22 | 29.02 | 1.110x |
| 1536 | 16132 | step | 48.22 | 45.31 | 1.064x |
| 1536 | 16164 | bwd | 32.03 | 28.80 | 1.112x |
| 1536 | 16164 | step | 48.19 | 45.38 | 1.062x |
| 1536 | 16263 | bwd | 32.22 | 28.93 | 1.114x |
| 1536 | 16263 | step | 48.64 | 45.57 | 1.067x |
| 1536 | 32768 | bwd | 57.42 | 51.97 | 1.105x |
| 1536 | 32768 | step | 87.94 | 82.78 | 1.062x |
| 1536 | 65536 | bwd | 107.26 | 96.54 | 1.111x |
| 1536 | 65536 | step | 165.95 | 155.62 | 1.066x |
| 4096 | 256 | bwd | 6.82 | 6.82 | 1.000x |
| 4096 | 256 | step | 9.41 | 9.34 | 1.007x |
| 4096 | 1024 | bwd | 11.14 | 10.08 | 1.105x |
| 4096 | 1024 | step | 15.20 | 14.14 | 1.075x |
| 4096 | 4096 | bwd | 24.00 | 21.73 | 1.105x |
| 4096 | 4096 | step | 36.16 | 33.66 | 1.074x |
| 4096 | 14928 | bwd | 67.42 | 62.50 | 1.079x |
| 4096 | 14928 | step | 103.49 | 98.66 | 1.049x |
| 4096 | 15288 | bwd | 68.80 | 63.36 | 1.086x |
| 4096 | 15288 | step | 104.90 | 100.13 | 1.048x |
| 4096 | 15566 | bwd | 70.14 | 64.58 | 1.086x |
| 4096 | 15566 | step | 106.94 | 101.73 | 1.051x |
| 4096 | 15590 | bwd | 70.21 | 64.67 | 1.086x |
| 4096 | 15590 | step | 107.42 | 101.92 | 1.054x |
| 4096 | 16114 | bwd | 72.19 | 66.18 | 1.091x |
| 4096 | 16114 | step | 110.43 | 104.86 | 1.053x |
| 4096 | 16132 | bwd | 71.97 | 66.05 | 1.090x |
| 4096 | 16132 | step | 109.89 | 104.42 | 1.052x |
| 4096 | 16164 | bwd | 71.78 | 66.21 | 1.084x |
| 4096 | 16164 | step | 110.40 | 104.80 | 1.053x |
| 4096 | 16263 | bwd | 72.99 | 66.56 | 1.097x |
| 4096 | 16263 | step | 111.46 | 105.50 | 1.056x |
| 4096 | 32768 | bwd | 135.39 | 125.60 | 1.078x |
| 4096 | 32768 | step | 211.78 | 201.76 | 1.050x |
| 4096 | 65536 | bwd | 260.13 | 241.06 | 1.079x |
| 4096 | 65536 | step | 410.53 | 391.82 | 1.048x |

### NVIDIA R200 (sm_107a, 212 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 1536 | 256 | bwd | 5.34 | 5.18 | 1.031x |
| 1536 | 256 | step | 7.65 | 7.58 | 1.008x |
| 1536 | 1024 | bwd | 6.11 | 6.14 | 0.995x |
| 1536 | 1024 | step | 9.06 | 8.67 | 1.044x |
| 1536 | 4096 | bwd | 9.38 | 8.86 | 1.058x |
| 1536 | 4096 | step | 13.47 | 13.15 | 1.024x |
| 1536 | 14928 | bwd | 20.35 | 19.17 | 1.062x |
| 1536 | 14928 | step | 29.38 | 27.68 | 1.061x |
| 1536 | 15288 | bwd | 21.02 | 20.10 | 1.046x |
| 1536 | 15288 | step | 29.99 | 28.67 | 1.046x |
| 1536 | 15566 | bwd | 21.15 | 19.58 | 1.080x |
| 1536 | 15566 | step | 30.27 | 28.64 | 1.057x |
| 1536 | 15590 | bwd | 20.96 | 19.94 | 1.051x |
| 1536 | 15590 | step | 30.24 | 28.90 | 1.047x |
| 1536 | 16114 | bwd | 21.44 | 20.58 | 1.042x |
| 1536 | 16114 | step | 30.82 | 29.79 | 1.034x |
| 1536 | 16132 | bwd | 21.50 | 20.67 | 1.040x |
| 1536 | 16132 | step | 30.94 | 29.76 | 1.040x |
| 1536 | 16164 | bwd | 21.50 | 20.61 | 1.043x |
| 1536 | 16164 | step | 30.98 | 29.50 | 1.050x |
| 1536 | 16263 | bwd | 21.76 | 20.99 | 1.037x |
| 1536 | 16263 | step | 31.14 | 29.95 | 1.039x |
| 1536 | 32768 | bwd | 36.16 | 34.85 | 1.038x |
| 1536 | 32768 | step | 54.69 | 53.50 | 1.022x |
| 1536 | 65536 | bwd | 66.46 | 64.13 | 1.036x |
| 1536 | 65536 | step | 100.64 | 98.53 | 1.021x |
| 4096 | 256 | bwd | 6.11 | 6.27 | 0.974x |
| 4096 | 256 | step | 9.15 | 8.99 | 1.018x |
| 4096 | 1024 | bwd | 8.32 | 8.38 | 0.992x |
| 4096 | 1024 | step | 12.13 | 12.06 | 1.005x |
| 4096 | 4096 | bwd | 16.51 | 16.03 | 1.030x |
| 4096 | 4096 | step | 25.38 | 24.86 | 1.021x |
| 4096 | 14928 | bwd | 44.35 | 38.11 | 1.164x |
| 4096 | 14928 | step | 66.27 | 60.64 | 1.093x |
| 4096 | 15288 | bwd | 45.38 | 39.23 | 1.157x |
| 4096 | 15288 | step | 67.87 | 62.08 | 1.093x |
| 4096 | 15566 | bwd | 47.97 | 40.13 | 1.195x |
| 4096 | 15566 | step | 70.40 | 63.39 | 1.111x |
| 4096 | 15590 | bwd | 47.36 | 40.26 | 1.176x |
| 4096 | 15590 | step | 70.18 | 63.39 | 1.107x |
| 4096 | 16114 | bwd | 47.46 | 41.09 | 1.155x |
| 4096 | 16114 | step | 70.88 | 64.77 | 1.094x |
| 4096 | 16132 | bwd | 47.52 | 41.22 | 1.153x |
| 4096 | 16132 | step | 71.01 | 64.99 | 1.093x |
| 4096 | 16164 | bwd | 47.46 | 40.90 | 1.160x |
| 4096 | 16164 | step | 70.91 | 64.90 | 1.093x |
| 4096 | 16263 | bwd | 47.68 | 40.80 | 1.169x |
| 4096 | 16263 | step | 71.23 | 64.86 | 1.098x |
| 4096 | 32768 | bwd | 87.84 | 75.54 | 1.163x |
| 4096 | 32768 | step | 131.55 | 120.29 | 1.094x |
| 4096 | 65536 | bwd | 172.90 | 142.18 | 1.216x |
| 4096 | 65536 | step | 258.34 | 228.51 | 1.131x |

Cake also ships the residual-fused forward and backward (which reject
H=1536 and H=4096) and hidden sizes 512, 2048 and 6144; the family
covers sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved CUDA RMSNorm training execution through updated,
architecture-optimized kernels and launch configurations.
* Added support for newer GPU architectures, including SM100A, SM103A,
and SM107A.

* **Compatibility**
* Updated backend routing to select optimized implementations based on
GPU architecture and workload size.
  * Maintained existing CUDA requirements and compilation settings.

* **Maintenance**
* Refreshed generated CUDA bindings and build metadata for the updated
training implementations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [566812d](https://github.com/flashinfer-ai/flashinfer/commit/566812deed79eff36b6c1298be9e9ea2d4f101e9)

- **作者**: eigen
- **时间**: 2026-10-20T17:42:51Z
- **提交信息**: perf(cake_fmha): uniform-gated per-item L2 stream hints for the balanced q1 decode kernels (SM100a, SM103a) (#6111)

PR #6111 is the uniform-gated L2 stream-hint change for the `cake_fmha`
on-device load-balanced ("balanced") paged-KV decode kernels. The family
has 7 variant bands with 14 compiled members: BF16 and FP16 KV at
head_dim 128 (each with a q_len-1 member and two packed multi-token
(MTP) members, n32 and n64), E4M3 KV cache at head_dim 128 in three
query/output dtypes (E4M3, BF16 or FP16 query and output), BF16 KV at
head_dim 64 (8 or 16 query heads per KV head) and BF16 KV at head_dim
256 (page size 16, 32, 64). This PR adds uniform-gated per-work-item L2
stream hints to two of those sources: the q_len-1 head_dim-128 kernel
(compiled for BF16 and for FP16) and the head_dim-64 BF16 kernel
(compiled for 8 and for 16 query heads per KV head). When every item has
the same length and every tile is split the same way, whole long items
prefetch their V pages into L2 (head_dim 64 only), and split tiles load
K/V under an evict_first L2 policy chosen per block through a runtime
cache-policy register; heavy uniform plans (head_dim 128, 64 or more
256-token pairs per CTA) and mixed-length plans run the previous path.
Against the previous Cake version of these kernels (the balanced decode
kernels currently on FlashInfer main), the geomean speedup is 1.0320 on
GB300 and 1.0291 on B200 for head_dim 64, and 1.0048 / 1.0047 for
head_dim 128.

The tables below give latency in us and speedup on GB300 (sm_103a) and
B200 (sm_100a) with CUDA 13.3.1. "current" is the previous Cake version
of the same kernels: the balanced decode kernels currently on FlashInfer
main. Latencies are CUPTI GPU time of the kernel under CUDA-graph
replay, with the L2 cache flushed before every launch. For each row, the
latency is the mean over 3 seeds of the per-seed median of 5 rounds. The
speedup is the geometric mean over the 3 seeds of the per-seed paired
ratio current / this PR (> 1 = this PR faster). Rows named `hd64_*` are
the standings shapes; rows named `perf_decode_balanced_*` are the
benchmark-suite shapes. All rows were measured in BF16 (FP16 compiles
from the same source). `--` = not measured.

## hd64 (38 rows)
| row | GB300 current us | GB300 this PR us | GB300 speedup | B200
current us | B200 this PR us | B200 speedup |
|---|---|---|---|---|---|---|
| hd64_agentx_b16_hkv1 | 105.98 | 106.21 | 0.9979 | 114.56 | 114.21 |
1.0031 |
| hd64_uniform_b128_hkv8_s32768 | 1209.95 | 1183.83 | 1.0221 | 1230.85 |
1212.35 | 1.0153 |
| hd64_uniform_b128_hkv8_s4096 | 175.94 | 168.16 | 1.0462 | 180.32 |
173.09 | 1.0418 |
| hd64_uniform_b16_hkv8_s65536 | 321.86 | 315.17 | 1.0212 | 327.33 |
321.62 | 1.0178 |
| hd64_uniform_b1_hkv8_s4096 | 14.18 | 14.27 | 0.9933 | 13.09 | 12.93 |
1.0124 |
| hd64_uniform_b4_hkv8_s65536 | 100.26 | 90.88 | 1.1032 | 101.57 | 92.96
| 1.0926 |
| hd64_uniform_b64_hkv8_s32768 | 625.41 | 613.35 | 1.0197 | 636.19 |
627.52 | 1.0138 |
| perf_decode_balanced_bf16_hd64_agentx_b128_hkv1 | 409.42 | 409.82 |
0.9990 | 422.69 | 423.39 | 0.9983 |
| perf_decode_balanced_bf16_hd64_agentx_b128_hkv4 | 1497.47 | 1498.21 |
0.9995 | 1533.89 | 1535.38 | 0.9990 |
| perf_decode_balanced_bf16_hd64_agentx_b128_hkv8 | 2943.75 | 2945.54 |
0.9994 | 3012.43 | 3014.96 | 0.9992 |
| perf_decode_balanced_bf16_hd64_agentx_b16_hkv1 | 76.42 | 76.38 |
1.0004 | 79.42 | 79.49 | 0.9992 |
| perf_decode_balanced_bf16_hd64_agentx_b16_hkv4 | 224.32 | 224.77 |
0.9980 | 219.94 | 219.90 | 1.0001 |
| perf_decode_balanced_bf16_hd64_agentx_b16_hkv8 | 405.06 | 405.15 |
0.9998 | 419.10 | 420.16 | 0.9975 |
| perf_decode_balanced_bf16_hd64_agentx_b64_hkv1 | 224.93 | 225.34 |
0.9981 | 225.28 | 225.47 | 0.9992 |
| perf_decode_balanced_bf16_hd64_agentx_b64_hkv4 | 775.97 | 776.58 |
0.9992 | 792.10 | 792.96 | 0.9989 |
| perf_decode_balanced_bf16_hd64_agentx_b64_hkv8 | 1490.11 | 1491.12 |
0.9993 | 1528.19 | 1529.34 | 0.9992 |
| perf_decode_balanced_bf16_hd64_b128_s1024 | 59.46 | 51.17 | 1.1620 |
59.49 | 51.17 | 1.1626 |
| perf_decode_balanced_bf16_hd64_b128_s16384 | 619.49 | 608.45 | 1.0181
| 625.17 | 617.44 | 1.0125 |
| perf_decode_balanced_bf16_hd64_b128_s4096 | 176.06 | 167.87 | 1.0488 |
179.65 | 171.90 | 1.0450 |
| perf_decode_balanced_bf16_hd64_b128_s8192 | 324.77 | 319.30 | 1.0171 |
327.87 | 324.06 | 1.0118 |
| perf_decode_balanced_bf16_hd64_b256_s1024 | 99.55 | 92.48 | 1.0765 |
100.35 | 93.95 | 1.0681 |
| perf_decode_balanced_bf16_hd64_b256_s16384 | 1224.22 | 1200.32 |
1.0199 | 1232.61 | 1215.33 | 1.0142 |
| perf_decode_balanced_bf16_hd64_b256_s4096 | 334.02 | 325.12 | 1.0274 |
338.08 | 328.93 | 1.0278 |
| perf_decode_balanced_bf16_hd64_b256_s8192 | 632.10 | 620.54 | 1.0186 |
638.40 | 630.67 | 1.0123 |
| perf_decode_balanced_bf16_hd64_b4_s1024 | 12.10 | 12.10 | 1.0000 |
10.82 | 10.78 | 1.0031 |
| perf_decode_balanced_bf16_hd64_b4_s16384 | 36.19 | 30.62 | 1.1818 |
35.97 | 30.78 | 1.1684 |
| perf_decode_balanced_bf16_hd64_b4_s4096 | 16.22 | 15.94 | 1.0181 |
15.49 | 15.10 | 1.0254 |
| perf_decode_balanced_bf16_hd64_b4_s8192 | 22.95 | 20.74 | 1.1065 |
22.53 | 20.22 | 1.1139 |
| perf_decode_balanced_bf16_hd64_uniform_b128_hkv1_s65536 | 326.21 |
321.31 | 1.0152 | 330.94 | 326.56 | 1.0134 |
| perf_decode_balanced_bf16_hd64_uniform_b128_hkv4_s65536 | 1218.83 |
1193.99 | 1.0208 | 1242.37 | 1226.62 | 1.0128 |
| perf_decode_balanced_bf16_hd64_uniform_b128_hkv8_s4096 | 175.17 |
167.68 | 1.0447 | 179.87 | 172.64 | 1.0419 |
| perf_decode_balanced_bf16_hd64_uniform_b128_hkv8_s65536 | 2385.25 |
2332.71 | 1.0225 | 2424.66 | 2387.90 | 1.0154 |
| perf_decode_balanced_bf16_hd64_uniform_b16_hkv1_s65536 | 63.30 | 54.69
| 1.1574 | 64.48 | 56.93 | 1.1326 |
| perf_decode_balanced_bf16_hd64_uniform_b16_hkv4_s65536 | 174.14 |
172.00 | 1.0125 | 177.82 | 175.81 | 1.0115 |
| perf_decode_balanced_bf16_hd64_uniform_b16_hkv8_s65536 | 323.68 |
316.67 | 1.0221 | 327.74 | 320.75 | 1.0218 |
| perf_decode_balanced_bf16_hd64_uniform_b64_hkv1_s65536 | 175.78 |
173.25 | 1.0146 | 178.56 | 178.37 | 1.0011 |
| perf_decode_balanced_bf16_hd64_uniform_b64_hkv4_s65536 | 630.75 |
611.30 | 1.0318 | 640.35 | 625.41 | 1.0239 |
| perf_decode_balanced_bf16_hd64_uniform_b64_hkv8_s65536 | 1214.95 |
1190.83 | 1.0202 | 1234.43 | 1216.67 | 1.0146 |
| geomean | | | 1.0320 (1 rows < 0.995 of 38) | | | 1.0291 (0 rows <
0.995 of 38) |

## hd128 (18 rows)
| row | GB300 current us | GB300 this PR us | GB300 speedup | B200
current us | B200 this PR us | B200 speedup |
|---|---|---|---|---|---|---|
| perf_decode_balanced_agentx_b128_hkv1 | 758.41 | 758.50 | 0.9999 |
789.06 | 789.83 | 0.9990 |
| perf_decode_balanced_agentx_b128_hkv4 | 2882.56 | 2884.22 | 0.9994 |
2952.02 | 2953.57 | 0.9995 |
| perf_decode_balanced_agentx_b128_hkv8 | 5691.37 | 5694.63 | 0.9994 |
-- | -- | -- |
| perf_decode_balanced_agentx_b16_hkv1 | 124.06 | 123.90 | 1.0013 |
125.27 | 125.35 | 0.9993 |
| perf_decode_balanced_agentx_b16_hkv4 | 398.33 | 398.45 | 0.9997 |
397.53 | 397.90 | 0.9991 |
| perf_decode_balanced_agentx_b16_hkv8 | 745.26 | 745.57 | 0.9996 |
780.98 | 781.78 | 0.9990 |
| perf_decode_balanced_agentx_b64_hkv1 | 402.66 | 402.84 | 0.9995 |
405.91 | 406.29 | 0.9991 |
| perf_decode_balanced_agentx_b64_hkv4 | 1467.20 | 1468.12 | 0.9994 |
1498.76 | 1499.42 | 0.9996 |
| perf_decode_balanced_agentx_b64_hkv8 | 2860.44 | 2862.24 | 0.9994 |
2936.79 | 2937.80 | 0.9997 |
| perf_decode_balanced_uniform_b128_hkv1_s65536 | 612.41 | 612.71 |
0.9995 | 622.18 | 622.42 | 0.9996 |
| perf_decode_balanced_uniform_b128_hkv4_s65536 | 2336.53 | 2338.02 |
0.9994 | 2393.05 | 2393.11 | 1.0000 |
| perf_decode_balanced_uniform_b128_hkv8_s65536 | 4605.27 | 4608.32 |
0.9993 | 4713.79 | 4715.28 | 0.9997 |
| perf_decode_balanced_uniform_b16_hkv1_s65536 | 101.80 | 92.69 | 1.0983
| 103.46 | 94.52 | 1.0945 |
| perf_decode_balanced_uniform_b16_hkv4_s65536 | 318.42 | 318.49 |
0.9998 | 322.93 | 323.21 | 0.9991 |
| perf_decode_balanced_uniform_b16_hkv8_s65536 | 606.33 | 606.67 |
0.9994 | 615.34 | 615.97 | 0.9990 |
| perf_decode_balanced_uniform_b64_hkv1_s65536 | 320.64 | 320.90 |
0.9992 | 324.81 | 325.05 | 0.9992 |
| perf_decode_balanced_uniform_b64_hkv4_s65536 | 1199.97 | 1201.32 |
0.9989 | 1218.66 | 1219.73 | 0.9991 |
| perf_decode_balanced_uniform_b64_hkv8_s65536 | 2319.63 | 2321.07 |
0.9994 | 2374.74 | 2375.41 | 0.9997 |
| geomean | | | 1.0048 (0 rows < 0.995 of 18) | | | 1.0047 (0 rows <
0.995 of 17) |

Cake also ships these variants of the family: the packed-MTP BF16 / FP16
members, the three E4M3-KV members and the head_dim-256 BF16 members.
The family ships only on sm_100a (B200 / GB200) and sm_103a (B300 /
GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Performance**
- Optimized attention decoding for improved memory-transfer efficiency.
- Adjusted workload handling to better support both uniform and
non-uniform workloads.
- Improved caching and prefetch behavior for large workloads, helping
maintain consistent performance across different decoding patterns.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5f8f8aa](https://github.com/flashinfer-ai/flashinfer/commit/5f8f8aad742043b38fe7c044f80cc96fa293a844)

- **作者**: eigen
- **时间**: 2026-10-20T17:42:47Z
- **提交信息**: perf(cake_causal_conv1d): a shape-selected big-channel backward program (C >= 512 on sm_100a/sm_103a, C >= 1024 on sm_107a) (#6874)

The `cake_causal_conv1d_train` kernel, a packed width-4 depthwise causal
conv fused with SiLU, has one data-type variant (BF16 in/out with FP32
math) and a forward and a backward program per architecture. This PR
adds a second backward program for that variant. The host selects it by
channel count C (C >= 512 on sm_100a and sm_103a, C >= 1024 on sm_107a);
below those thresholds the previous backward programs are still used,
and the forward is unchanged. Against the previous Cake version of this
backward (the programs shipped in #6844), the geomean speedup (previous
/ this PR) across all 14 shapes is 1.0569 on GB300, 1.0765 on B200 and
1.0511 on R200. On the shapes the host routes to the new program, the
per-shape speedup ranges from 1.0403 to 1.0991 on GB300 (12 shapes,
geomean 1.0667), from 1.0702 to 1.1226 on B200 (12 shapes, geomean
1.0898) and from 1.0694 to 1.2581 on R200 (4 shapes, geomean 1.1908).

**Backward latency, NVIDIA GB300 (sm_103a), CUDA 13.4**

| S | C | previous (us) | this PR (us) | ratio (previous / this PR) |
|---:|---:|---:|---:|---:|
| 239718 | 512 | 155.0 | 145.3 | 1.0671 |
| 245028 | 512 | 156.4 | 150.4 | 1.0403 |
| 249866 | 512 | 159.0 | 150.6 | 1.0557 |
| 250340 | 512 | 160.5 | 149.4 | 1.0741 |
| 258574 | 512 | 163.1 | 154.3 | 1.0570 |
| 259042 | 512 | 164.6 | 157.5 | 1.0448 |
| 259584 | 512 | 164.3 | 155.7 | 1.0550 |
| 261393 | 512 | 167.3 | 155.8 | 1.0735 |
| 250340 | 128 | 59.0 | 59.0 | 1.0000 |
| 250340 | 256 | 94.8 | 94.8 | 1.0000 |
| 250340 | 1024 | 294.0 | 272.4 | 1.0790 |
| 250340 | 2048 | 584.0 | 545.4 | 1.0709 |
| 250340 | 4096 | 1142.3 | 1052.4 | 1.0854 |
| 250340 | 8192 | 2264.3 | 2060.1 | 1.0991 |

Rows with C below 512 keep the previous program (same compiled kernel),
so their latency is unchanged.

**Backward latency, NVIDIA B200 (sm_100a), CUDA 13.4**

| S | C | previous (us) | this PR (us) | ratio (previous / this PR) |
|---:|---:|---:|---:|---:|
| 239718 | 512 | 171.0 | 157.4 | 1.0868 |
| 245028 | 512 | 172.6 | 159.2 | 1.0839 |
| 249866 | 512 | 177.8 | 165.8 | 1.0728 |
| 250340 | 512 | 177.5 | 162.9 | 1.0895 |
| 258574 | 512 | 181.6 | 166.6 | 1.0900 |
| 259042 | 512 | 181.7 | 168.4 | 1.0790 |
| 259584 | 512 | 183.3 | 171.2 | 1.0702 |
| 261393 | 512 | 185.2 | 167.9 | 1.1033 |
| 250340 | 128 | 63.3 | 63.3 | 1.0000 |
| 250340 | 256 | 102.1 | 102.1 | 1.0000 |
| 250340 | 1024 | 330.6 | 294.5 | 1.1226 |
| 250340 | 2048 | 658.2 | 611.0 | 1.0772 |
| 250340 | 4096 | 1289.5 | 1179.7 | 1.0931 |
| 250340 | 8192 | 2570.5 | 2315.7 | 1.1100 |

Rows with C below 512 keep the previous program (same compiled kernel),
so their latency is unchanged.

**Backward latency, NVIDIA R200 (sm_107a), CUDA 13.4**

| S | C | previous (us) | this PR (us) | ratio (previous / this PR) |
|---:|---:|---:|---:|---:|
| 239718 | 512 | 97.9 | 97.9 | 1.0000 |
| 245028 | 512 | 99.4 | 99.4 | 1.0000 |
| 249866 | 512 | 101.8 | 101.8 | 1.0000 |
| 250340 | 512 | 101.3 | 101.3 | 1.0000 |
| 258574 | 512 | 104.0 | 104.0 | 1.0000 |
| 259042 | 512 | 104.6 | 104.6 | 1.0000 |
| 259584 | 512 | 105.3 | 105.3 | 1.0000 |
| 261393 | 512 | 105.3 | 105.3 | 1.0000 |
| 250340 | 128 | 40.4 | 40.4 | 1.0000 |
| 250340 | 256 | 58.5 | 58.5 | 1.0000 |
| 250340 | 1024 | 190.3 | 178.0 | 1.0694 |
| 250340 | 2048 | 428.3 | 356.4 | 1.2017 |
| 250340 | 4096 | 836.0 | 672.3 | 1.2435 |
| 250340 | 8192 | 1652.2 | 1313.3 | 1.2581 |

Rows with C below 1024 keep the previous program (same compiled kernel),
so their latency is unchanged.

In Cake, the `cake_causal_conv1d_train` family ships the forward and the
backward on sm_100a, sm_103a and sm_107a, and has no other data-type or
layout variants.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added architecture-aware backward kernel selection for causal Conv1D
training, including optimized paths for larger channel counts.
* Added support for new GPU architecture builds and CUDA kernel
artifacts.
* Improved workspace management across available backward execution
paths.

* **Bug Fixes**
* Improved backward execution reliability by validating selected kernels
and workspace capacity.
* Preserved consistent results across fallback and optimized execution
paths.

* **Documentation**
* Clarified deterministic kernel selection, workspace sizing, and CUDA
Graph capture requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [fe380e2](https://github.com/flashinfer-ai/flashinfer/commit/fe380e20df7affc034938b12b80584b61824f489)

- **作者**: eigen
- **时间**: 2026-10-20T17:42:38Z
- **提交信息**: refactor(cake_fused_qk_rope_fp8_append): regenerate the kernel and route the host through the in-tree program loader (#6867)

`fused_qk_rope_fp8_append` fuses Q/K RMSNorm, RoPE, FP8 (e4m3)
quantization and the paged K/V cache append into one kernel. Cake has
one variant of it, with FP8 e4m3 output. This PR delivers that variant
on sm_90a, sm_100a and sm_103a. The baseline is the previous Cake
version of the same kernel: the loader shipped at FlashInfer main
23f3e8f6. Across the 30 shapes in the owner's shape list, the geomean
speedup is 0.961 on H100 (sm_90a), 0.998 on B200 (sm_100a) and 0.994 on
GB300 (sm_103a). All three geomeans are below 1.0, so the new export is
slower than the previous version on each architecture. sm_90a has the
largest slowdown.

### sm_90a (H100)

NVIDIA H100 80GB HBM3 (sm_90a), CUDA 13.0, driver 535.216.03. previous =
shipped Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export;
median GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup =
previous / new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 0
(T=32) | 2.927 | 3.040 | 0.963 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 1
(T=32) | 2.944 | 3.167 | 0.930 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 2
(T=32) | 2.944 | 3.136 | 0.939 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 0
(T=32) | 2.944 | 3.040 | 0.968 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 1
(T=32) | 2.960 | 3.168 | 0.934 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 2
(T=32) | 2.944 | 3.136 | 0.939 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 0
(T=32) | 4.064 | 4.128 | 0.984 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 1
(T=32) | 4.080 | 4.096 | 0.996 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 2
(T=32) | 4.065 | 4.080 | 0.996 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 0
(T=32) | 4.095 | 4.096 | 1.000 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 1
(T=32) | 4.096 | 4.096 | 1.000 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 2
(T=32) | 4.048 | 4.032 | 1.004 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 0
(T=128) | 3.007 | 3.168 | 0.949 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 1
(T=128) | 3.151 | 3.360 | 0.938 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 2
(T=128) | 3.136 | 3.360 | 0.933 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 0
(T=128) | 3.007 | 3.232 | 0.931 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 1
(T=128) | 3.104 | 3.360 | 0.924 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 2
(T=128) | 3.136 | 3.360 | 0.933 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 0
(T=128) | 4.864 | 4.928 | 0.987 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 1
(T=128) | 5.056 | 5.120 | 0.987 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 2
(T=128) | 5.087 | 5.120 | 0.994 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 0
(T=128) | 4.704 | 4.896 | 0.961 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 1
(T=128) | 5.024 | 5.120 | 0.981 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 2
(T=128) | 4.992 | 5.136 | 0.972 |
| prefill, 8q/1kv heads, q_len 127×4, ctx 2048, page 64, quant 1, norm 2
(T=508) | 3.936 | 4.192 | 0.939 |
| prefill, 8q/1kv heads, q_len 128×4, ctx 2048, page 64, quant 1, norm 2
(T=512) | 3.921 | 4.192 | 0.935 |
| prefill, 8q/1kv heads, q_len 129×4, ctx 2048, page 64, quant 1, norm 2
(T=516) | 3.904 | 4.192 | 0.931 |
| prefill, 64q/8kv heads, q_len 127×4, ctx 2048, page 64, quant 1, norm
2 (T=508) | 11.520 | 11.935 | 0.965 |
| prefill, 64q/8kv heads, q_len 128×4, ctx 2048, page 64, quant 1, norm
2 (T=512) | 11.600 | 12.000 | 0.967 |
| prefill, 64q/8kv heads, q_len 129×4, ctx 2048, page 64, quant 1, norm
2 (T=516) | 11.904 | 12.272 | 0.970 |

Geomean speedup over 30 shapes: 0.961.

### sm_100a (B200)

NVIDIA B200 (sm_100a), CUDA 13.4, driver 580.82.07. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 0
(T=32) | 3.231 | 3.232 | 1.000 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 1
(T=32) | 3.328 | 3.360 | 0.990 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 2
(T=32) | 3.328 | 3.360 | 0.990 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 0
(T=32) | 3.200 | 3.232 | 0.990 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 1
(T=32) | 3.360 | 3.360 | 1.000 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 2
(T=32) | 3.360 | 3.360 | 1.000 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 0
(T=32) | 3.616 | 3.569 | 1.013 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 1
(T=32) | 3.744 | 3.712 | 1.009 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 2
(T=32) | 3.712 | 3.776 | 0.983 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 0
(T=32) | 3.584 | 3.616 | 0.991 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 1
(T=32) | 3.712 | 3.776 | 0.983 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 2
(T=32) | 3.712 | 3.776 | 0.983 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 0
(T=128) | 3.296 | 3.264 | 1.010 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 1
(T=128) | 3.423 | 3.456 | 0.991 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 2
(T=128) | 3.423 | 3.424 | 1.000 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 0
(T=128) | 3.296 | 3.264 | 1.010 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 1
(T=128) | 3.456 | 3.456 | 1.000 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 2
(T=128) | 3.424 | 3.440 | 0.995 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 0
(T=128) | 4.000 | 3.968 | 1.008 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 1
(T=128) | 4.209 | 4.224 | 0.996 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 2
(T=128) | 4.224 | 4.192 | 1.008 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 0
(T=128) | 3.935 | 3.936 | 1.000 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 1
(T=128) | 4.144 | 4.160 | 0.996 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 2
(T=128) | 4.160 | 4.160 | 1.000 |
| prefill, 8q/1kv heads, q_len 127×4, ctx 2048, page 64, quant 1, norm 2
(T=508) | 3.713 | 3.712 | 1.000 |
| prefill, 8q/1kv heads, q_len 128×4, ctx 2048, page 64, quant 1, norm 2
(T=512) | 3.776 | 3.743 | 1.009 |
| prefill, 8q/1kv heads, q_len 129×4, ctx 2048, page 64, quant 1, norm 2
(T=516) | 3.744 | 3.680 | 1.017 |
| prefill, 64q/8kv heads, q_len 127×4, ctx 2048, page 64, quant 1, norm
2 (T=508) | 10.448 | 10.592 | 0.986 |
| prefill, 64q/8kv heads, q_len 128×4, ctx 2048, page 64, quant 1, norm
2 (T=512) | 10.688 | 10.576 | 1.011 |
| prefill, 64q/8kv heads, q_len 129×4, ctx 2048, page 64, quant 1, norm
2 (T=516) | 10.624 | 10.816 | 0.982 |

Geomean speedup over 30 shapes: 0.998.

### sm_103a (GB300)

NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.167.08. previous = shipped
Cake loader at FlashInfer 23f3e8f63b66; new = this PR's export; median
GPU time (CUPTI, cold L2), 3 groups × 128 iterations; speedup = previous
/ new.

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 0
(T=32) | 2.944 | 2.976 | 0.989 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 1
(T=32) | 3.040 | 3.136 | 0.969 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 2
(T=32) | 3.072 | 3.136 | 0.980 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 0
(T=32) | 2.944 | 2.976 | 0.989 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 1
(T=32) | 3.120 | 3.072 | 1.016 |
| decode, 8q/1kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 2
(T=32) | 3.120 | 3.072 | 1.016 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 0
(T=32) | 3.408 | 3.456 | 0.986 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 1
(T=32) | 3.520 | 3.520 | 1.000 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 1, norm 2
(T=32) | 3.520 | 3.552 | 0.991 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 0
(T=32) | 3.408 | 3.424 | 0.995 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 1
(T=32) | 3.520 | 3.568 | 0.987 |
| decode, 64q/8kv heads, q_len 1×32, ctx 2048, page 64, quant 2, norm 2
(T=32) | 3.504 | 3.552 | 0.986 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 0
(T=128) | 3.104 | 3.104 | 1.000 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 1
(T=128) | 3.232 | 3.232 | 1.000 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 2
(T=128) | 3.200 | 3.232 | 0.990 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 0
(T=128) | 3.136 | 3.168 | 0.990 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 1
(T=128) | 3.264 | 3.264 | 1.000 |
| prefill, 8q/1kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 2
(T=128) | 3.264 | 3.264 | 1.000 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 0
(T=128) | 3.808 | 3.872 | 0.983 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 1
(T=128) | 4.192 | 4.080 | 1.027 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 1, norm 2
(T=128) | 4.032 | 4.128 | 0.977 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 0
(T=128) | 3.856 | 3.840 | 1.004 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 1
(T=128) | 4.160 | 4.096 | 1.016 |
| prefill, 64q/8kv heads, q_len 16×8, ctx 2048, page 64, quant 2, norm 2
(T=128) | 4.032 | 4.080 | 0.988 |
| prefill, 8q/1kv heads, q_len 127×4, ctx 2048, page 64, quant 1, norm 2
(T=508) | 3.488 | 3.520 | 0.991 |
| prefill, 8q/1kv heads, q_len 128×4, ctx 2048, page 64, quant 1, norm 2
(T=512) | 3.520 | 3.552 | 0.991 |
| prefill, 8q/1kv heads, q_len 129×4, ctx 2048, page 64, quant 1, norm 2
(T=516) | 3.552 | 3.648 | 0.974 |
| prefill, 64q/8kv heads, q_len 127×4, ctx 2048, page 64, quant 1, norm
2 (T=508) | 9.216 | 9.184 | 1.003 |
| prefill, 64q/8kv heads, q_len 128×4, ctx 2048, page 64, quant 1, norm
2 (T=512) | 9.536 | 9.632 | 0.990 |
| prefill, 64q/8kv heads, q_len 129×4, ctx 2048, page 64, quant 1, norm
2 (T=516) | 9.824 | 9.760 | 1.007 |

Geomean speedup over 30 shapes: 0.994.

Cake ships no other data-type or layout variant of this kernel; Cake
ships it on sm_90a, sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added generated CUDA support for fused QK RoPE FP8 processing and
paged key/value-cache updates.
- Added support for NVIDIA architectures SM90, SM100, and SM103 through
ahead-of-time and just-in-time compilation.

- **Bug Fixes**
- Improved validation for tensor placement, data types, memory layout,
launch dimensions, and request metadata.
- Invalid requests now report failure status and avoid processing
invalid data.

- **Performance**
- Added optimized fused processing for normalization, rotary embeddings,
FP8 quantization, and cache updates.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6a4e51e](https://github.com/flashinfer-ai/flashinfer/commit/6a4e51eb81a108c0d44e32d74c7713da6577d92c)

- **作者**: eigen
- **时间**: 2026-10-20T17:42:33Z
- **提交信息**: feat(cake_dsa): native NoPE sparse MLA kernels (GLM-5.3-Flash) for the 64-head DSA backend on SM100 / SM103 / SM107 with grad (#6489) (#6836)

The experimental `cake_dsa_train` backend
(`flashinfer.dsa_sparse_attention.dsa_sparse_attention[_varlen]`) has
native 64-query-head DSA sparse-attention training kernels: forward,
backward, backward aux and index preparation. They use bf16
inputs/outputs and fp32 statistics and accumulation, and support dense
and packed/varlen rows. The kernels have two variants, by positional
encoding. The RoPE variant has 512 latent + 64 rope query/key dimensions
(the GLM-5.2 geometry). This PR delivers the NoPE variant, which has 512
latent dimensions only and no rope block (the GLM-5.3-Flash geometry).
It includes the variant's own generated programs for sm_100a, sm_103a
and sm_107a, the autograd entry, the packed/varlen entry with
device-side index conversion, and the planner/validation code. The
tables below give the NoPE speedup over the shipped Cake RoPE kernels
with zero rope inputs. That baseline computes the NoPE result exactly.

NVIDIA GB300 (sm_103a), CUDA 13.4 toolkit (nvcc 13.4), CUDA 13.0 runtime
(PyTorch 2.14.1+cu130), driver 580.159.03. Baseline (RoPE-path columns):
the shipped Cake RoPE kernels with zero rope inputs. Times are the
steady-state median of the GPU span per call, cold L2. Speedup =
RoPE-path time / NoPE time; step = one training step (forward +
backward).

| shape (Tq / Skv / K) | forward NoPE ms | forward RoPE-path ms |
speedup | backward NoPE ms | backward RoPE-path ms | speedup | step NoPE
ms | step RoPE-path ms | speedup |
|---|---|---|---|---|---|---|---|---|---|
| doc_4096 (4096 / 4096 / 2176) | 0.716 | 1.246 | 1.74x | 3.125 | 3.876
| 1.24x | 3.707 | 5.150 | 1.39x |
| doc_16384 (16384 / 16384 / 2176) | 3.381 | 4.367 | 1.29x | 14.564 |
18.192 | 1.25x | 17.776 | 22.447 | 1.26x |
| doc_16384_k128 (16384 / 16384 / 128) | 0.655 | 1.201 | 1.83x | 1.925 |
3.497 | 1.82x | 2.443 | 4.774 | 1.95x |
| tail_4096x131072 (4096 / 131072 / 2176) | 0.989 | 1.623 | 1.64x |
4.222 | 6.130 | 1.45x | 5.095 | 7.819 | 1.53x |
| chunk_4096x269564 (4096 / 269564 / 2176) | 0.651 | 1.208 | 1.86x |
2.851 | 3.510 | 1.23x | 3.426 | 4.829 | 1.41x |
| glm53_a (16263 / 269564 / 2176) | 2.836 | 3.801 | 1.34x | 12.790 |
16.335 | 1.28x | 15.674 | 20.181 | 1.29x |
| glm53_b (14928 / 247211 / 2176) | 2.536 | 3.376 | 1.33x | 11.155 |
14.232 | 1.28x | 13.585 | 17.670 | 1.30x |
| glm53_a_iid (16263 / 269564 / 2176) | 2.903 | 3.890 | 1.34x | 13.323 |
17.196 | 1.29x | 16.131 | 21.084 | 1.31x |
| glm53_a_p256 (16263 / 269564 / 1152) | 1.846 | 2.552 | 1.38x | 8.128 |
10.612 | 1.31x | 9.900 | 13.258 | 1.34x |
| band_4096_iid (4096 / 4096 / 2176) | 0.738 | 1.290 | 1.75x | 3.203 |
3.969 | 1.24x | 3.807 | 5.271 | 1.38x |
| chunk_3975x269564 (3975 / 269564 / 2176) | 0.762 | 1.345 | 1.77x |
3.419 | 4.261 | 1.25x | 4.106 | 5.672 | 1.38x |
| chunk_1927x269564 (1927 / 269564 / 2176) | 0.477 | 1.080 | 2.26x |
2.072 | 2.430 | 1.17x | 2.475 | 3.602 | 1.45x |
| short_1024_k128 (1024 / 1024 / 128) | 0.049 | 0.558 | 11.43x | 0.273 |
0.339 | 1.24x | 0.323 | 0.878 | 2.72x |
| short_4096_k512 (4096 / 4096 / 512) | 0.311 | 0.836 | 2.69x | 1.233 |
1.655 | 1.34x | 1.407 | 2.530 | 1.80x |
| tail_1024x16384_k512 (1024 / 16384 / 512) | 0.086 | 0.603 | 7.02x |
0.446 | 0.493 | 1.11x | 0.517 | 1.128 | 2.18x |
| doc_16384_k256 (16384 / 16384 / 256) | 0.824 | 1.413 | 1.72x | 2.792 |
4.512 | 1.62x | 3.474 | 5.953 | 1.71x |
| doc_16384_k512 (16384 / 16384 / 512) | 1.176 | 1.820 | 1.55x | 4.527 |
6.515 | 1.44x | 5.561 | 8.418 | 1.51x |
| doc_16384_k1024 (16384 / 16384 / 1024) | 1.920 | 2.618 | 1.36x | 7.895
| 10.458 | 1.32x | 9.665 | 13.150 | 1.36x |
| tail_2048x65536 (2048 / 65536 / 2176) | 0.510 | 1.101 | 2.16x | 2.216
| 2.869 | 1.29x | 2.600 | 4.040 | 1.55x |
| doc_65536 (65536 / 65536 / 2176) | 14.626 | 17.771 | 1.22x | 61.846 |
76.776 | 1.24x | 75.845 | 93.903 | 1.24x |

NVIDIA GB200 (sm_100a), CUDA 13.4 toolkit (nvcc 13.4), CUDA 13.0 runtime
(PyTorch 2.14.1+cu130), driver 580.126.20. Baseline (RoPE-path columns):
the shipped Cake RoPE kernels with zero rope inputs. Times are the
steady-state median of the GPU span per call, cold L2. Speedup =
RoPE-path time / NoPE time; step = one training step (forward +
backward).

| shape (Tq / Skv / K) | forward NoPE ms | forward RoPE-path ms |
speedup | backward NoPE ms | backward RoPE-path ms | speedup | step NoPE
ms | step RoPE-path ms | speedup |
|---|---|---|---|---|---|---|---|---|---|
| doc_4096 (4096 / 4096 / 2176) | 0.731 | 1.273 | 1.74x | 3.147 | 3.897
| 1.24x | 3.742 | 5.170 | 1.38x |
| doc_16384 (16384 / 16384 / 2176) | 3.466 | 4.534 | 1.31x | 14.705 |
18.327 | 1.25x | 17.929 | 22.668 | 1.26x |
| doc_16384_k128 (16384 / 16384 / 128) | 0.678 | 1.246 | 1.84x | 1.930 |
3.488 | 1.81x | 2.473 | 4.771 | 1.93x |
| tail_4096x131072 (4096 / 131072 / 2176) | 1.035 | 1.654 | 1.60x |
4.266 | 6.203 | 1.45x | 5.187 | 8.006 | 1.54x |
| chunk_4096x269564 (4096 / 269564 / 2176) | 0.665 | 1.259 | 1.89x |
2.877 | 3.559 | 1.24x | 3.462 | 4.870 | 1.41x |
| glm53_a (16263 / 269564 / 2176) | 2.908 | 3.935 | 1.35x | 13.011 |
16.689 | 1.28x | 16.075 | 20.719 | 1.29x |
| glm53_b (14928 / 247211 / 2176) | 2.608 | 3.515 | 1.35x | 11.364 |
14.651 | 1.29x | 13.906 | 18.166 | 1.31x |
| glm53_a_iid (16263 / 269564 / 2176) | 2.998 | 4.010 | 1.34x | 13.572 |
17.664 | 1.30x | 16.479 | 21.717 | 1.32x |
| glm53_a_p256 (16263 / 269564 / 1152) | 1.891 | 2.601 | 1.38x | 8.203 |
10.723 | 1.31x | 10.008 | 13.325 | 1.33x |
| band_4096_iid (4096 / 4096 / 2176) | 0.756 | 1.344 | 1.78x | 3.226 |
4.001 | 1.24x | 3.840 | 5.357 | 1.40x |
| chunk_3975x269564 (3975 / 269564 / 2176) | 0.781 | 1.395 | 1.79x |
3.461 | 4.388 | 1.27x | 4.165 | 5.782 | 1.39x |
| chunk_1927x269564 (1927 / 269564 / 2176) | 0.508 | 1.105 | 2.18x |
2.082 | 2.436 | 1.17x | 2.518 | 3.610 | 1.43x |
| short_1024_k128 (1024 / 1024 / 128) | 0.051 | 0.555 | 10.83x | 0.272 |
0.344 | 1.26x | 0.335 | 0.939 | 2.80x |
| short_4096_k512 (4096 / 4096 / 512) | 0.326 | 0.860 | 2.64x | 1.235 |
1.656 | 1.34x | 1.426 | 2.540 | 1.78x |
| tail_1024x16384_k512 (1024 / 16384 / 512) | 0.096 | 0.636 | 6.63x |
0.459 | 0.516 | 1.12x | 0.519 | 1.144 | 2.20x |
| doc_16384_k256 (16384 / 16384 / 256) | 0.846 | 1.464 | 1.73x | 2.809 |
4.510 | 1.61x | 3.516 | 6.019 | 1.71x |
| doc_16384_k512 (16384 / 16384 / 512) | 1.201 | 1.859 | 1.55x | 4.555 |
6.547 | 1.44x | 5.612 | 8.453 | 1.51x |
| doc_16384_k1024 (16384 / 16384 / 1024) | 1.950 | 2.691 | 1.38x | 7.951
| 10.530 | 1.32x | 9.757 | 13.201 | 1.35x |
| tail_2048x65536 (2048 / 65536 / 2176) | 0.538 | 1.157 | 2.15x | 2.265
| 2.867 | 1.27x | 2.634 | 4.078 | 1.55x |
| doc_65536 (65536 / 65536 / 2176) | 15.244 | 18.935 | 1.24x | 63.788 |
77.833 | 1.22x | 79.850 | 95.734 | 1.20x |

NVIDIA R200 (sm_107a), CUDA 13.4 toolkit (nvcc 13.4), CUDA 13.0 runtime
(PyTorch 2.14.1+cu130), driver 620.62. Baseline (RoPE-path columns): the
shipped Cake RoPE kernels with zero rope inputs. Times are the
steady-state median of the GPU span per call, cold L2. Speedup =
RoPE-path time / NoPE time; step = one training step (forward +
backward).

| shape (Tq / Skv / K) | forward NoPE ms | forward RoPE-path ms |
speedup | backward NoPE ms | backward RoPE-path ms | speedup | step NoPE
ms | step RoPE-path ms | speedup |
|---|---|---|---|---|---|---|---|---|---|
| doc_4096 (4096 / 4096 / 2176) | 0.442 | 0.618 | 1.40x | 1.905 | 2.641
| 1.39x | 2.303 | 3.262 | 1.42x |
| doc_16384 (16384 / 16384 / 2176) | 2.066 | 2.609 | 1.26x | 9.368 |
12.271 | 1.31x | 11.057 | 14.878 | 1.35x |
| doc_16384_k128 (16384 / 16384 / 128) | 0.387 | 0.602 | 1.56x | 1.153 |
2.898 | 2.51x | 1.508 | 3.515 | 2.33x |
| tail_4096x131072 (4096 / 131072 / 2176) | 0.591 | 0.818 | 1.39x |
2.498 | 4.113 | 1.65x | 3.058 | 4.940 | 1.62x |
| chunk_4096x269564 (4096 / 269564 / 2176) | 0.390 | 0.591 | 1.51x |
1.655 | 2.572 | 1.55x | 2.040 | 3.175 | 1.56x |
| glm53_a (16263 / 269564 / 2176) | 1.706 | 2.369 | 1.39x | 7.455 |
11.546 | 1.55x | 9.109 | 13.923 | 1.53x |
| glm53_b (14928 / 247211 / 2176) | 1.529 | 2.109 | 1.38x | 6.633 |
10.317 | 1.56x | 8.151 | 12.436 | 1.53x |
| glm53_a_iid (16263 / 269564 / 2176) | 1.748 | 2.432 | 1.39x | 7.697 |
11.826 | 1.54x | 9.292 | 14.261 | 1.53x |
| glm53_a_p256 (16263 / 269564 / 1152) | 1.117 | 1.544 | 1.38x | 4.803 |
7.825 | 1.63x | 5.911 | 9.374 | 1.59x |
| band_4096_iid (4096 / 4096 / 2176) | 0.451 | 0.632 | 1.40x | 1.881 |
2.696 | 1.43x | 2.286 | 3.331 | 1.46x |
| chunk_3975x269564 (3975 / 269564 / 2176) | 0.459 | 0.662 | 1.44x |
2.006 | 3.038 | 1.51x | 2.460 | 3.706 | 1.51x |
| chunk_1927x269564 (1927 / 269564 / 2176) | 0.295 | 0.488 | 1.66x |
1.256 | 1.769 | 1.41x | 1.545 | 2.270 | 1.47x |
| short_1024_k128 (1024 / 1024 / 128) | 0.034 | 0.203 | 6.03x | 0.127 |
0.211 | 1.66x | 0.153 | 0.420 | 2.75x |
| short_4096_k512 (4096 / 4096 / 512) | 0.179 | 0.363 | 2.03x | 0.704 |
1.223 | 1.74x | 0.839 | 1.592 | 1.90x |
| tail_1024x16384_k512 (1024 / 16384 / 512) | 0.056 | 0.234 | 4.17x |
0.233 | 0.345 | 1.48x | 0.260 | 0.588 | 2.26x |
| doc_16384_k256 (16384 / 16384 / 256) | 0.474 | 0.702 | 1.48x | 1.671 |
3.577 | 2.14x | 2.101 | 4.287 | 2.04x |
| doc_16384_k512 (16384 / 16384 / 512) | 0.693 | 0.914 | 1.32x | 2.746 |
4.861 | 1.77x | 3.365 | 5.781 | 1.72x |
| doc_16384_k1024 (16384 / 16384 / 1024) | 1.159 | 1.494 | 1.29x | 4.811
| 7.369 | 1.53x | 5.900 | 8.866 | 1.50x |
| tail_2048x65536 (2048 / 65536 / 2176) | 0.300 | 0.492 | 1.64x | 1.263
| 1.779 | 1.41x | 1.527 | 2.282 | 1.49x |
| doc_65536 (65536 / 65536 / 2176) | 8.779 | 10.956 | 1.25x | 37.106 |
51.489 | 1.39x | 45.704 | 62.112 | 1.36x |

Cake also ships the RoPE variant of these kernels (forward, backward,
backward aux and index preparation for the 512 + 64 geometry) in the
same backend; the family ships on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added zero-RoPE (NoPE) sparse-attention training APIs for fixed-length
and packed variable-length inputs.
* Added support for causal masking, top-k selection, optional
log-sum-exp outputs, key passes, destination mapping, and gradient
accumulation.
* Added validation for tensor layouts, sequence metadata, indices, and
runtime configuration.
* **Documentation**
* Added guidance covering NoPE APIs, supported layouts, validation,
backward behavior, and build availability.
* **Tests**
* Added comprehensive forward, backward, varlen, masking, validation,
and numerical-accuracy coverage.
* **Benchmarks**
  * Added NoPE performance, memory, workspace, and accuracy reporting.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [60b1652](https://github.com/flashinfer-ai/flashinfer/commit/60b1652f903bc6169b7ac1a4c9968e42e58cd9b2)

- **作者**: eigen
- **时间**: 2026-10-20T17:42:29Z
- **提交信息**: perf(cake_ulysses): interleaved-stripe NVLink all-to-all kernels for sm_100a/sm_103a (#6864)

The Cake Ulysses sequence-parallel all-to-all kernel family
(`scatter_heads` / `gather_heads` over single-node NVLink) has 24
variants per architecture: 3 data types (bf16, fp16, fp32) x 2
directions (scatter, gather) x 4 world sizes (2, 4, 6, 8 ranks). This PR
delivers the whole family on sm_100a and sm_103a. It is compared against
the previous Cake all-to-all kernels in FlashInfer main
(`backend="nvlink"`). On the BF16 performance shapes it is 1.33x–2.49x
faster on B200 and 1.29x–2.50x faster on B300.

**B200 (sm_100a): 8x NVIDIA B200, NVLink, CUDA 13.4 (nvcc 13.4.92).**
Median GPU time of one BF16 scatter or gather call, including the
staging-to-output copy, with cold L2, measured on the slowest rank.
Speedup = baseline / this PR.

| World | Shape | Direction | Baseline (µs) | This PR (µs) | Speedup |
|---|---|---|---|---|---|
| 2 ranks | B=1, S_local=16380, H=40, D=128 | scatter | 362.6 | 145.9 |
2.49x |
| 2 ranks | B=1, S_local=16380, H=40, D=128 | gather | 360.7 | 144.7 |
2.49x |
| 4 ranks | B=1, S_local=8190, H=40, D=128 | scatter | 191.0 | 114.0 |
1.68x |
| 4 ranks | B=1, S_local=8190, H=40, D=128 | gather | 188.9 | 114.2 |
1.65x |
| 6 ranks | B=1, S_local=5460, H=48, D=128 | scatter | 155.8 | 108.7 |
1.43x |
| 6 ranks | B=1, S_local=5460, H=48, D=128 | gather | 151.7 | 108.8 |
1.39x |
| 8 ranks | B=1, S_local=4095, H=40, D=128 | scatter | 106.5 | 76.2 |
1.40x |
| 8 ranks | B=1, S_local=4095, H=40, D=128 | gather | 102.3 | 77.2 |
1.33x |

**B300 (sm_103a): 8x NVIDIA B300 SXM6 AC, NVLink, CUDA 13.4 (nvcc
13.4.92).** Median GPU time of one BF16 scatter or gather call,
including the staging-to-output copy, with cold L2, measured on the
slowest rank. Speedup = baseline / this PR.

| World | Shape | Direction | Baseline (µs) | This PR (µs) | Speedup |
|---|---|---|---|---|---|
| 2 ranks | B=1, S_local=16380, H=40, D=128 | scatter | 361.0 | 145.7 |
2.48x |
| 2 ranks | B=1, S_local=16380, H=40, D=128 | gather | 359.1 | 143.8 |
2.50x |
| 4 ranks | B=1, S_local=8190, H=40, D=128 | scatter | 190.2 | 116.1 |
1.64x |
| 4 ranks | B=1, S_local=8190, H=40, D=128 | gather | 188.2 | 115.8 |
1.63x |
| 6 ranks | B=1, S_local=5460, H=48, D=128 | scatter | 155.3 | 108.5 |
1.43x |
| 6 ranks | B=1, S_local=5460, H=48, D=128 | gather | 151.3 | 109.6 |
1.38x |
| 8 ranks | B=1, S_local=4095, H=40, D=128 | scatter | 106.0 | 77.9 |
1.36x |
| 8 ranks | B=1, S_local=4095, H=40, D=128 | gather | 101.8 | 78.7 |
1.29x |

This package also includes the kernel's other Cake variants (fp16 and
fp32, both directions, W=2/4/6/8) for sm_100a and sm_103a; other
architectures keep FlashInfer's portable NVLink kernel.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added an optional Cake NVLink backend for Ulysses all-to-all
communication.
* Automatically selects Cake when supported, with portable NVLink
fallback otherwise.
* Supports float16, bfloat16, and float32 across supported Blackwell
devices and world sizes.
  * Added backend status reporting through the communicator.
  * Added package loading, validation, and prebuilt/JIT library support.

* **Performance**
* Expanded communication benchmarks to compare portable NVLink, Cake
NVLink, and NCCL, including timing and speedup results.

* **Tests**
* Added coverage for routing, backend selection, supported
configurations, signal handling, and manifest consistency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [80a4418](https://github.com/flashinfer-ai/flashinfer/commit/80a44189a0972922a98317612647df4f3012be74)

- **作者**: Dundy Pasupuleti
- **时间**: 2026-10-20T17:06:04Z
- **提交信息**: fix(gdn): fence TMEM loads before cg1 shared_acc releases (#5335)

## Summary

Fixes #5334.

In the Blackwell GDN chunked kernel (`compute_group_1_chunk`), two
`cg1_shared_acc` consumer releases signaled the producer that the TMEM
stage was free while `tcgen05.ld` (`LDTM`) into that stage was still in
flight. With `tmem_cg1_shared_acc_stages = 1`, the producer's next
`tcgen05.mma` can overwrite cells mid-read.

This PR adds `cute.arch.fence_view_async_tmem_load()` immediately
before:

1. `ks_handle.release()` (after the KS t2r + scale)
2. `nv_handle.release()` (after the NV t2r + cast loop)

These match the existing cg0 idiom at `kk0_handle` / `kk1_handle` (and
QK epilogue) releases, so the following `SYNCS.ARRIVE` inherits the LDTM
scoreboard wait mask.

### Changed vs preserved

| Site | Action |
|------|--------|
| `ks_handle.release` | **changed**: add load fence |
| `nv_handle.release` | **changed**: add load fence |
| `qs_handle.release` | **preserved**: intervening reg consumer +
`fence_view_async_tmem_store` already drains LDTM |
| `o_qs_handle.release` | **preserved**: same class of lookalike; leave
alone |
| cg0 `kk*` / `qk*` fences | **preserved**: already correct |

### Related

Possibly related to the nondeterministic NaN signature in #4704 (garbage
into `v - k·s` / NV inputs is consistent with that class of failure),
but this PR does **not** claim to fix #4704 or the production hang.
Linkage remains speculative; the hang is non-completion, while this race
predicts corruption.

## Diff

Two lines only in
`flashinfer/gdn_kernels/blackwell/gated_delta_net_chunked.py`.

## Verification

No Blackwell GPU or CUDA `nvdisasm` toolchain on the machine used for
this PR, so SASS control-bit re-check was not re-run here.

Verified instead:

- Against `main` @ `d7bfcab6091da2e1d98c1b26b46d8e613389c2e1` (same HEAD
cited in #5334).
- Source parity with cg0: fences sit immediately before release after
all t2r into the stage for that handoff (cg0 lines 3081/3109).
- Diff is exactly the two `fence_view_async_tmem_load()` insertions;
`qs` / `o_qs` untouched.
- Issue #5334 already documents baseline FAIL / +fence PASS / revert
FAIL via `nvdisasm -c -g -hex` on both reconstruction and the production
binary (unordered ARRIVE wait masks at the two sites).

Suggested follow-up for a Blackwell/CUDA host: re-run the issue's
compile+nvdisasm control-bit check and confirm those two ARRIVEs go from
`wait=000000` to a non-zero LDTM wait mask.

## Test plan

- [ ] Reviewers with SM100/SM103: compile GDN chunked specialization and
`nvdisasm -c -g -hex`; assert no `SYNCS.ARRIVE` releasing
`cg1_shared_acc` leaves an `LDTM` scoreboard live
- [ ] Optional B200/B300 sanity (not a proof): existing GDN chunked
correctness paths still pass

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during internal memory reads to ensure
subsequent operations observe updated data consistently.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Dundy Pasupuleti <dundysm@gmail.com>

### [69f082f](https://github.com/flashinfer-ai/flashinfer/commit/69f082fe759f23e3e37d457da9075c11c4e15eee)

- **作者**: Anerudhan Gopal
- **时间**: 2026-10-20T16:13:06Z
- **提交信息**: fix(moe_ep): skip non-local routes in split expert compute (#6840)

<!-- .github/pull_request_template.md -->

## 📌 Description

The split RANK_MAJOR/HT bridge maps non-local routes to the first local
expert with zero weight. Those routes still enter expert compute. Pass
the global expert count into the bridge and map masked routes to a valid
remote expert, so the existing runner filter excludes them before the
GEMMs.

Keep the original routing weights, top-k, tensor shapes, and fallback
when no remote expert exists. This covers the NVLink, NCCL LL
rank-major, and NCCL HT paths.

### Performance

Fresh stock/fixed comparisons on **8× NVIDIA GB200 (two nodes × four
GPUs), BF16, EP8/TP1**. Both use base `9c68e44`; the fixed revision is
`ba85c25`. Full-forward CUDA graph timing includes staging, dispatch,
compute, and combine. Each result is the median of 30 slowest-rank
sample averages, with 10 replays per sample. Setup and autotuning are
untimed.

| Model | Hidden | Intermediate | Experts | Top-k |
|---|---:|---:|---:|---:|
| Qwen3 | 4096 | 1536 | 128 | 8 |
| Qwen3.5 | 4096 | 1024 | 512 | 10 |
| DS-V4.1 | 5120 | 2304 | 384 | 6 |

| Model | Path | Tokens/GPU | Stock p50 µs | Fixed p50 µs | Speedup |
|---|---|---:|---:|---:|---:|
| Qwen3 | NVLink | 8 | 175.66 | 165.16 | 1.06× |
| Qwen3 | NVLink | 4096 | 7878.02 | 1793.31 | 4.39× |
| Qwen3 | NCCL LL | 8 | 181.99 | 174.57 | 1.04× |
| Qwen3 | NCCL LL | 4096 | 8011.27 | 1864.59 | 4.30× |
| Qwen3 | NCCL HT | 8 | 258.39 | 248.86 | 1.04× |
| Qwen3 | NCCL HT | 4096 | 7995.45 | 2110.27 | 3.79× |
| Qwen3.5 | NVLink | 8 | 265.37 | 254.56 | 1.04× |
| Qwen3.5 | NVLink | 4096 | 7124.89 | 1804.53 | 3.95× |
| Qwen3.5 | NCCL HT | 8 | 362.36 | 351.62 | 1.03× |
| Qwen3.5 | NCCL HT | 4096 | 7510.95 | 2268.59 | 3.31× |
| DS-V4.1 | NVLink | 8 | 441.91 | 400.70 | 1.10× |
| DS-V4.1 | NVLink | 4096 | 10446.81 | 2463.67 | 4.24× |
| DS-V4.1 | NCCL LL | 8 | 455.48 | 418.12 | 1.09× |
| DS-V4.1 | NCCL LL | 4096 | 10729.30 | 2572.68 | 4.17× |
| DS-V4.1 | NCCL HT | 8 | 529.80 | 489.99 | 1.08× |
| DS-V4.1 | NCCL HT | 4096 | 10796.32 | 2814.42 | 3.84× |

Prefill speedups are **3.31–4.39×**. All 32 benchmark runs passed
independent reference checks before timing and after graph warmup.
Qwen3.5/NCCL LL is omitted because top-k 10 exceeds the transport's
limit of 8.

[Full p50/p95 results, benchmark output, environment, and reproduction
commands](https://github.com/Anerudhan/moe_ep_perf/blob/31d4423a75839011475cc76107e0092639bc6f9b/results/split-route-fix/results.md).
This is one paired sweep with synthetic inputs, not an exhaustive tuning
claim.

## 🔍 Related Issues

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
- [x] All selected tests pass; the full GPU suite was not run.

On GB200, 32 tests passed (29 deselected). Coverage includes first/last
expert shards, invalid routes, single-rank fallback, an independent BF16
reference, and CUDA graph replay through mixed, all-masked, and changed
routing.

```bash
pytest tests/moe_ep/test_compute_bridge.py \
  tests/moe_ep/test_split_fused_moe_kernel_vs_reference.py \
  -k "not nvfp4 and not w4a8 and not fp8 and not mxint4 and not mxfp8" -v
pre-commit run --all-files
```

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

The patch reuses the existing local-expert filter; it changes no CUDA
kernels. Performance measurements cover BF16, EP8/TP1, on two nodes with
four GB200 GPUs each.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved mixture-of-experts routing to correctly exclude non-local or
invalid expert routes from computation.
* Preserved valid local routes and ensured masked routes produce zero
contribution, including fully invalid tokens.
* Improved consistency across standard execution and CUDA Graph replay
paths.

* **Tests**
* Added coverage for varied expert offsets, token counts, global expert
configurations, and BF16 CUDA Graph execution.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [91b201a](https://github.com/flashinfer-ai/flashinfer/commit/91b201a670ea5d86df8e0e4d601a510f606eac01)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-20T16:11:03Z
- **提交信息**: fix(moe): wait for Rubin finalize reductions before shared-buffer reuse (#6307)

<!-- .github/pull_request_template.md -->

## 📌 Description

Wait for outstanding bulk-reduction reads before reusing the shared
epilogue buffer. The existing thread barrier does not wait for those
asynchronous reads, so the next persistent tile can overwrite data still
being consumed.

## 🔍 Related Issues

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




<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability in grouped matrix operations by ensuring each
tile’s reduction work finishes before processing continues with the next
tile. This helps prevent overlapping work from affecting intermediate
results and supports more consistent operation across consecutive tiles.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [41b39c4](https://github.com/flashinfer-ai/flashinfer/commit/41b39c4af9ea7e3cad075effb97b571a57d51b78)

- **作者**: eigen
- **时间**: 2026-10-20T15:44:18Z
- **提交信息**: perf(cake_all_gather_matmul): SM103a peer-outer tile order, TP4 gate/up (#6841)

`cake_all_gather_matmul` all-gathers each rank's row-sharded activation
and multiplies it by a contiguous `[N, K]` weight. Cake ships it in bf16
and fp16, K-major and N-major weights, world sizes 2, 4 and 8, two
main-tile widths and two transport routes (copy engine, SM push). This
PR delivers one SM103a (B300) variant: for world-size-4 bf16 K-major
calls with 128 padded rows and N = 14336, the main GEMM program walks
its (peer, B-panel) output tiles in peer-outer order (`_po`) instead of
the previous order. Same tiles, same instructions, bitwise-identical
outputs; one program is added for that one shape and no other program
changes. The table compares it with the previous Cake version of this
kernel, the programs of #6761, whose branch this one is built on.

| Shape per rank, M × N (world size 4, K = 8192) | Previous version
(µs), node 1 / node 2 | This PR (µs), node 1 / node 2 | Speedup, node 1
/ node 2 |
|---|---:|---:|---:|
| 125 × 14336 (padded to 128 rows), bf16, K-major weights (Llama-3.1-70B
TP4 fused gate/up) | 187.4 / 191.0 | 171.8 / 174.9 | 1.098 / 1.112 |

NVIDIA B300 (SM103a), CUDA 13.3, two B300 nodes, four ranks with one
rank per GPU; latency = median over calls of the slowest rank's time.
Speedup > 1 means this PR is faster; it is the median of per-group
ratios paired through a common reference build, so it is not the
quotient of the latencies beside it. Both nodes clear their noise bands
(node 1: ln 0.0935 vs bands 0.0168 / 0.0294; node 2: ln 0.1061 vs bands
0.0238 / 0.0294; 9 groups per pass, two passes, 17 of 18 group ratios
above 1 on each node), so the speedup is credited on both.

Cake also ships `_n128` (128-wide) twins, copy-engine CTA-pair `_cg2`
twins, `_cg2s2` spill-split pair twins and `_ks4` per-K-slice readiness
twins of six main programs (`sm_103a` only), and the `peer_push_wide`
and `peer_push_wide_ks4` (`sm_103a` only) push programs for this kernel,
on `sm_100a` and `sm_103a`; the `_po` form ships for this one shape on
`sm_103a` only, and `sm_100a` is unchanged here.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added an optimized all-gather matrix multiplication route for
supported BF16, four-rank, K-major workloads on SM103a GPUs.
- Added tile-order execution for the supported 128-row, 14,336-column
configuration.
- Added validation and fallback handling for unsupported shapes and
configurations.

- **Tests**
- Expanded coverage for tile-order routing, launch validation, grid
selection, dispatch, and fallback behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8dc1163](https://github.com/flashinfer-ai/flashinfer/commit/8dc1163fbfbec7098a2418276fd04bc1fa1aeaa5)

- **作者**: eigen
- **时间**: 2026-10-20T10:43:52Z
- **提交信息**: perf(cake_deepgemm_dense_mqa): v11 re-export on the folded catalog, withdrawn paged points (#6579)

FlashInfer's `deepgemm_dense_mqa` family contains the DeepSeek-V3.2
lightning-indexer logits kernels, dense `fp8_mqa_logits` and paged
`fp8_paged_mqa_logits`, with FP32 accumulation and FP32 logits. Its Cake
catalog has 73 generated programs, 38 dense routes and 34 paged routes.
This PR re-exports the whole family at its round-4 text set
(`dense_mqa.v10` → `dense_mqa.v11`), regenerating the dense and paged
FP8 kernels and adding folded admission tables and an optional
per-forward schedule-meta input for paged routes. It also withdraws some
paged calls to FlashInfer's stock kernel. The baseline is the previous
Cake export on FlashInfer `main` (a04985696294). Across paired rows the
geometric-mean speedup is 1.11 on B200 (293 rows, 0.97 to 27.68) and
1.10 on GB300 (286 rows, 0.95 to 26.56), and 21 B200 rows and 19 GB300
rows are below 1.00. The largest gains are dense 64-head shapes with a
long prefix: for example, Q=64 K=4164 prefix=4100 drops from 11.5 to 6.9
µs on B200 and from 10.7 to 6.4 µs on GB300.

**Latency per shape, this PR vs `main`.** NVIDIA B200 (`sm_100a`) and
NVIDIA GB300 (`sm_103a`), CUDA 13.3. Latency is the GPU time of one call
from its first kernel start to its last kernel end (CUPTI, cold L2),
taken as the median of 9 interleaved sessions. Speedup = main / this PR.
Measured at revision a6c35cb7dbc5 of this PR (the previous head); the
current head changes only Python formatting and test lint in the
delivered Python files, not kernel texts or the catalog. The table has
54 dense FP8 shapes and 256 paged FP8 shapes. B=SMs means batch = SM
count (148 on B200, 152 on GB300). "not served by this PR" (17 rows on
B200, 24 on GB300) marks the withdrawn calls, which have no PR time.
Their main time is still shown except for paged B=512 n=1 ctx=128k
mixed, which main does not serve either.

| Shape | B200 main (µs) | B200 this PR (µs) | B200 speedup | GB300 main
(µs) | GB300 this PR (µs) | GB300 speedup |
|---|---:|---:|---:|---:|---:|---:|
| paged B=1 n=1 ctx=1k uniform page64 64h | 4.9 | 4.0 | 1.24 | 4.5 | 3.5
| 1.30 |
| paged B=1 n=1 ctx=1k mixed page64 64h | 4.9 | 4.0 | 1.24 | 4.5 | 3.5 |
1.30 |
| paged B=1 n=1 ctx=4k uniform page64 64h | 5.2 | 4.1 | 1.28 | 4.5 | 3.8
| 1.20 |
| paged B=1 n=1 ctx=4k mixed page64 64h | 5.2 | 4.0 | 1.28 | 4.6 | 3.6 |
1.29 |
| paged B=1 n=1 ctx=8k uniform page64 64h | 5.3 | 4.3 | 1.24 | 4.7 | 4.0
| 1.17 |
| paged B=1 n=1 ctx=8k mixed page64 64h | 5.2 | 4.3 | 1.22 | 4.9 | 4.0 |
1.22 |
| paged B=1 n=1 ctx=32k uniform page64 64h | 6.0 | 5.2 | 1.17 | 5.8 |
4.9 | 1.18 |
| paged B=1 n=1 ctx=32k mixed page64 64h | 6.0 | 5.0 | 1.19 | 5.7 | 4.8
| 1.19 |
| paged B=1 n=1 ctx=128k uniform page64 64h | 8.9 | 8.9 | 1.00 | 8.6 |
8.4 | 1.02 |
| paged B=1 n=1 ctx=128k mixed page64 64h | 10.0 | 10.0 | 1.00 | 9.4 |
9.2 | 1.01 |
| paged B=1 n=2 ctx=1k uniform page64 64h | 5.2 | 4.2 | 1.22 | 4.7 | 3.7
| 1.26 |
| paged B=1 n=2 ctx=1k mixed page64 64h | 5.1 | 4.2 | 1.21 | 4.8 | 3.8 |
1.26 |
| paged B=1 n=2 ctx=4k uniform page64 64h | 5.5 | 4.4 | 1.26 | 4.8 | 4.0
| 1.19 |
| paged B=1 n=2 ctx=4k mixed page64 64h | 5.4 | 4.5 | 1.20 | 5.0 | 4.1 |
1.22 |
| paged B=1 n=2 ctx=8k uniform page64 64h | 5.5 | 4.5 | 1.23 | 4.9 | 4.3
| 1.16 |
| paged B=1 n=2 ctx=8k mixed page64 64h | 5.5 | 4.5 | 1.23 | 4.9 | 4.2 |
1.17 |
| paged B=1 n=2 ctx=32k uniform page64 64h | 6.3 | 5.4 | 1.15 | 6.0 |
5.1 | 1.17 |
| paged B=1 n=2 ctx=32k mixed page64 64h | 6.8 | 6.2 | 1.09 | 6.2 | 5.3
| 1.17 |
| paged B=1 n=2 ctx=128k uniform page64 64h | 9.5 | 9.4 | 1.00 | 9.1 |
8.9 | 1.02 |
| paged B=1 n=2 ctx=128k mixed page64 64h | 9.3 | 9.4 | 0.98 | 8.9 | not
served by this PR | — |
| paged B=1 n=4 ctx=1k uniform page64 64h | 5.9 | 4.9 | 1.20 | 5.3 | 4.3
| 1.24 |
| paged B=1 n=4 ctx=1k mixed page64 64h | 5.9 | 4.9 | 1.20 | 5.5 | 4.5 |
1.23 |
| paged B=1 n=4 ctx=4k uniform page64 64h | 6.2 | 5.1 | 1.22 | 5.4 | 4.6
| 1.18 |
| paged B=1 n=4 ctx=4k mixed page64 64h | 6.1 | 5.1 | 1.20 | 5.7 | 4.7 |
1.20 |
| paged B=1 n=4 ctx=8k uniform page64 64h | 6.2 | 5.2 | 1.20 | 5.6 | 4.9
| 1.15 |
| paged B=1 n=4 ctx=8k mixed page64 64h | 6.2 | 5.2 | 1.19 | 5.8 | 4.9 |
1.18 |
| paged B=1 n=4 ctx=32k uniform page64 64h | 7.1 | 6.2 | 1.15 | 6.7 |
5.8 | 1.15 |
| paged B=1 n=4 ctx=32k mixed page64 64h | 7.1 | 6.2 | 1.14 | 6.8 | 5.9
| 1.16 |
| paged B=1 n=4 ctx=128k uniform page64 64h | 11.9 | 11.9 | 1.00 | 11.0
| 10.8 | 1.02 |
| paged B=1 n=4 ctx=128k mixed page64 64h | 11.9 | 11.9 | 1.01 | 11.0 |
10.8 | 1.02 |
| paged B=4 n=1 ctx=1k uniform page64 64h | 5.2 | 4.1 | 1.27 | 4.5 | 3.8
| 1.21 |
| paged B=4 n=1 ctx=1k mixed page64 64h | 5.1 | 4.1 | 1.24 | 4.5 | 3.9 |
1.17 |
| paged B=4 n=1 ctx=4k uniform page64 64h | 5.5 | 4.5 | 1.21 | 5.2 | 4.2
| 1.23 |
| paged B=4 n=1 ctx=4k mixed page64 64h | 5.6 | 4.6 | 1.22 | 5.2 | 4.3 |
1.23 |
| paged B=4 n=1 ctx=8k uniform page64 64h | 6.0 | 5.2 | 1.17 | 5.8 | 4.9
| 1.18 |
| paged B=4 n=1 ctx=8k mixed page64 64h | 6.0 | 5.6 | 1.07 | 5.8 | 5.3 |
1.09 |
| paged B=4 n=1 ctx=32k uniform page64 64h | 8.9 | 8.9 | 1.00 | 8.6 |
8.5 | 1.02 |
| paged B=4 n=1 ctx=32k mixed page64 64h | 8.9 | 8.9 | 1.00 | 8.5 | 8.4
| 1.02 |
| paged B=4 n=1 ctx=128k uniform page64 64h | 18.5 | 18.3 | 1.01 | 18.0
| 17.7 | 1.02 |
| paged B=4 n=1 ctx=128k mixed page64 64h | 19.4 | 19.4 | 1.00 | 18.6 |
18.6 | 1.00 |
| paged B=4 n=2 ctx=1k uniform page64 64h | 5.4 | 4.4 | 1.22 | 4.8 | 4.0
| 1.20 |
| paged B=4 n=2 ctx=1k mixed page64 64h | 5.4 | 4.4 | 1.22 | 5.0 | 4.1 |
1.22 |
| paged B=4 n=2 ctx=4k uniform page64 64h | 5.7 | 4.8 | 1.20 | 5.3 | 4.4
| 1.21 |
| paged B=4 n=2 ctx=4k mixed page64 64h | 5.6 | 4.7 | 1.20 | 5.2 | 4.4 |
1.19 |
| paged B=4 n=2 ctx=8k uniform page64 64h | 6.3 | 5.4 | 1.17 | 6.0 | 5.1
| 1.17 |
| paged B=4 n=2 ctx=8k mixed page64 64h | 6.4 | 6.0 | 1.07 | 6.1 | 5.6 |
1.09 |
| paged B=4 n=2 ctx=32k uniform page64 64h | 9.4 | 9.5 | 1.00 | 9.0 |
8.9 | 1.01 |
| paged B=4 n=2 ctx=32k mixed page64 64h | 9.0 | not served by this PR |
— | 8.5 | not served by this PR | — |
| paged B=4 n=2 ctx=128k uniform page64 64h | 19.4 | 19.6 | 0.99 | 18.4
| 18.5 | 0.99 |
| paged B=4 n=2 ctx=128k mixed page64 64h | 19.5 | 20.1 | 0.97 | 18.6 |
18.7 | 1.00 |
| paged B=4 n=4 ctx=1k uniform page64 64h | 6.3 | 5.1 | 1.24 | 5.4 | 4.6
| 1.18 |
| paged B=4 n=4 ctx=1k mixed page64 64h | 6.1 | 5.1 | 1.20 | 5.6 | 4.7 |
1.20 |
| paged B=4 n=4 ctx=4k uniform page64 64h | 6.6 | 5.5 | 1.20 | 6.0 | 5.1
| 1.19 |
| paged B=4 n=4 ctx=4k mixed page64 64h | 6.6 | 5.4 | 1.21 | 6.1 | 5.1 |
1.20 |
| paged B=4 n=4 ctx=8k uniform page64 64h | 7.1 | 6.2 | 1.15 | 6.7 | 5.8
| 1.15 |
| paged B=4 n=4 ctx=8k mixed page64 64h | 7.0 | 6.0 | 1.16 | 6.6 | 5.8 |
1.15 |
| paged B=4 n=4 ctx=32k uniform page64 64h | 12.0 | 12.0 | 1.00 | 11.1 |
11.0 | 1.01 |
| paged B=4 n=4 ctx=32k mixed page64 64h | 11.2 | 11.0 | 1.01 | 10.1 |
10.0 | 1.01 |
| paged B=4 n=4 ctx=128k uniform page64 64h | 26.8 | 26.6 | 1.01 | 24.7
| 24.4 | 1.01 |
| paged B=4 n=4 ctx=128k mixed page64 64h | 25.6 | 26.1 | 0.98 | 23.5 |
23.4 | 1.00 |
| paged B=16 n=1 ctx=1k uniform page64 64h | 5.5 | 4.5 | 1.23 | 5.1 |
4.4 | 1.17 |
| paged B=16 n=1 ctx=1k mixed page64 64h | 5.6 | 4.6 | 1.22 | 5.2 | 4.4
| 1.17 |
| paged B=16 n=1 ctx=4k uniform page64 64h | 7.2 | 6.7 | 1.07 | 6.9 |
6.6 | 1.05 |
| paged B=16 n=1 ctx=4k mixed page64 64h | 7.3 | 7.1 | 1.03 | 6.9 | 6.9
| 1.00 |
| paged B=16 n=1 ctx=8k uniform page64 64h | 9.0 | 9.0 | 1.01 | 8.7 |
not served by this PR | — |
| paged B=16 n=1 ctx=8k mixed page64 64h | 9.0 | 9.0 | 1.00 | 8.6 | not
served by this PR | — |
| paged B=16 n=1 ctx=32k uniform page64 64h | 18.4 | 18.3 | 1.01 | 17.7
| 17.7 | 1.00 |
| paged B=16 n=1 ctx=32k mixed page64 64h | 18.6 | 18.5 | 1.01 | 18.1 |
18.0 | 1.01 |
| paged B=16 n=1 ctx=128k uniform page64 64h | 51.5 | 51.0 | 1.01 | 49.9
| 49.8 | 1.00 |
| paged B=16 n=1 ctx=128k mixed page64 64h | 52.8 | 52.6 | 1.00 | 51.5 |
51.5 | 1.00 |
| paged B=16 n=2 ctx=1k uniform page64 64h | 5.8 | 4.8 | 1.20 | 5.3 |
4.6 | 1.15 |
| paged B=16 n=2 ctx=1k mixed page64 64h | 5.8 | 4.8 | 1.19 | 5.4 | 4.7
| 1.16 |
| paged B=16 n=2 ctx=4k uniform page64 64h | 7.6 | 7.1 | 1.06 | 7.3 |
6.9 | 1.05 |
| paged B=16 n=2 ctx=4k mixed page64 64h | 7.6 | 7.3 | 1.03 | 7.3 | 7.1
| 1.03 |
| paged B=16 n=2 ctx=8k uniform page64 64h | 9.6 | 9.6 | 1.00 | 9.1 |
not served by this PR | — |
| paged B=16 n=2 ctx=8k mixed page64 64h | 9.6 | 9.7 | 1.00 | 9.1 | not
served by this PR | — |
| paged B=16 n=2 ctx=32k uniform page64 64h | 19.5 | 19.4 | 1.00 | 18.6
| 18.4 | 1.01 |
| paged B=16 n=2 ctx=32k mixed page64 64h | 20.5 | 20.5 | 1.00 | 19.9 |
19.6 | 1.01 |
| paged B=16 n=2 ctx=128k uniform page64 64h | 54.1 | 54.0 | 1.00 | 52.0
| 52.2 | 1.00 |
| paged B=16 n=2 ctx=128k mixed page64 64h | 55.2 | 55.1 | 1.00 | 53.4 |
54.0 | 0.99 |
| paged B=16 n=4 ctx=1k uniform page64 64h | 6.5 | 5.5 | 1.18 | 6.1 |
5.2 | 1.16 |
| paged B=16 n=4 ctx=1k mixed page64 64h | 6.6 | 5.5 | 1.19 | 6.1 | 5.3
| 1.16 |
| paged B=16 n=4 ctx=4k uniform page64 64h | 8.9 | 8.7 | 1.03 | 8.5 |
8.3 | 1.02 |
| paged B=16 n=4 ctx=4k mixed page64 64h | 9.2 | 8.8 | 1.05 | 8.6 | 8.5
| 1.01 |
| paged B=16 n=4 ctx=8k uniform page64 64h | 12.2 | 12.0 | 1.01 | 11.2 |
11.2 | 1.00 |
| paged B=16 n=4 ctx=8k mixed page64 64h | 12.5 | 12.6 | 0.99 | 11.4 |
11.7 | 0.98 |
| paged B=16 n=4 ctx=32k uniform page64 64h | 26.6 | 26.5 | 1.00 | 24.6
| 24.5 | 1.00 |
| paged B=16 n=4 ctx=32k mixed page64 64h | 27.5 | 27.1 | 1.01 | 25.0 |
25.0 | 1.00 |
| paged B=16 n=4 ctx=128k uniform page64 64h | 76.8 | 77.6 | 0.99 | 72.6
| 72.9 | 1.00 |
| paged B=16 n=4 ctx=128k mixed page64 64h | 78.8 | 78.7 | 1.00 | 73.6 |
73.8 | 1.00 |
| paged B=64 n=1 ctx=1k uniform page64 64h | 7.2 | 6.8 | 1.06 | 6.9 |
6.6 | 1.06 |
| paged B=64 n=1 ctx=1k mixed page64 64h | 7.3 | 7.1 | 1.03 | 7.0 | 6.9
| 1.01 |
| paged B=64 n=1 ctx=4k uniform page64 64h | 13.0 | 12.9 | 1.01 | 12.1 |
12.1 | 1.00 |
| paged B=64 n=1 ctx=4k mixed page64 64h | 14.4 | 12.9 | 1.12 | 12.3 |
12.3 | 1.00 |
| paged B=64 n=1 ctx=8k uniform page64 64h | 20.4 | 19.2 | 1.06 | 19.5 |
18.6 | 1.05 |
| paged B=64 n=1 ctx=8k mixed page64 64h | 20.0 | 19.4 | 1.03 | 19.5 |
18.4 | 1.06 |
| paged B=64 n=1 ctx=32k uniform page64 64h | 51.7 | 51.9 | 1.00 | 50.2
| 50.1 | 1.00 |
| paged B=64 n=1 ctx=32k mixed page64 64h | 50.1 | 50.2 | 1.00 | 49.0 |
48.9 | 1.00 |
| paged B=64 n=1 ctx=128k uniform page64 64h | 177.7 | 176.8 | 1.01 |
174.3 | 174.4 | 1.00 |
| paged B=64 n=1 ctx=128k mixed page64 64h | 181.0 | 181.2 | 1.00 |
179.1 | 178.8 | 1.00 |
| paged B=64 n=2 ctx=1k uniform page64 64h | 7.6 | 7.1 | 1.06 | 7.3 |
7.0 | 1.04 |
| paged B=64 n=2 ctx=1k mixed page64 64h | 7.9 | not served by this PR |
— | 7.5 | not served by this PR | — |
| paged B=64 n=2 ctx=4k uniform page64 64h | 13.8 | 13.7 | 1.00 | 13.2 |
not served by this PR | — |
| paged B=64 n=2 ctx=4k mixed page64 64h | 15.2 | 13.7 | 1.11 | 14.2 |
12.7 | 1.12 |
| paged B=64 n=2 ctx=8k uniform page64 64h | 20.8 | 20.2 | 1.03 | 20.2 |
19.4 | 1.04 |
| paged B=64 n=2 ctx=8k mixed page64 64h | 21.0 | 20.1 | 1.05 | 20.2 |
19.3 | 1.05 |
| paged B=64 n=2 ctx=32k uniform page64 64h | 54.1 | 54.4 | 1.00 | 52.3
| 52.1 | 1.00 |
| paged B=64 n=2 ctx=32k mixed page64 64h | 53.9 | 53.8 | 1.00 | 52.2 |
52.3 | 1.00 |
| paged B=64 n=2 ctx=128k uniform page64 64h | 183.4 | 184.0 | 1.00 |
179.8 | 179.8 | 1.00 |
| paged B=64 n=2 ctx=128k mixed page64 64h | 184.6 | 184.2 | 1.00 |
180.4 | 180.1 | 1.00 |
| paged B=64 n=4 ctx=1k uniform page64 64h | 9.0 | 8.9 | 1.01 | 8.5 |
8.4 | 1.02 |
| paged B=64 n=4 ctx=1k mixed page64 64h | 9.5 | 9.3 | 1.02 | 8.9 | 8.8
| 1.01 |
| paged B=64 n=4 ctx=4k uniform page64 64h | 17.6 | 17.6 | 1.00 | 16.0 |
16.1 | 1.00 |
| paged B=64 n=4 ctx=4k mixed page64 64h | 17.9 | 17.9 | 1.00 | 16.3 |
16.1 | 1.01 |
| paged B=64 n=4 ctx=8k uniform page64 64h | 26.3 | 26.7 | 0.99 | 23.8 |
24.3 | 0.98 |
| paged B=64 n=4 ctx=8k mixed page64 64h | 25.9 | 26.0 | 1.00 | 23.3 |
23.6 | 0.99 |
| paged B=64 n=4 ctx=32k uniform page64 64h | 76.2 | 76.3 | 1.00 | 70.2
| 70.1 | 1.00 |
| paged B=64 n=4 ctx=32k mixed page64 64h | 75.3 | 75.1 | 1.00 | 69.9 |
70.0 | 1.00 |
| paged B=64 n=4 ctx=128k uniform page64 64h | 277.1 | 278.4 | 1.00 |
243.2 | 243.5 | 1.00 |
| paged B=64 n=4 ctx=128k mixed page64 64h | 273.2 | 274.3 | 1.00 |
240.4 | 241.1 | 1.00 |
| paged B=128 n=1 ctx=1k uniform page64 64h | 9.9 | 9.1 | 1.09 | 9.5 |
not served by this PR | — |
| paged B=128 n=1 ctx=1k mixed page64 64h | 10.3 | 9.3 | 1.11 | 9.9 |
8.7 | 1.14 |
| paged B=128 n=1 ctx=4k uniform page64 64h | 20.1 | 19.4 | 1.04 | 19.5
| 18.6 | 1.05 |
| paged B=128 n=1 ctx=4k mixed page64 64h | 20.9 | 19.6 | 1.07 | 20.2 |
18.8 | 1.07 |
| paged B=128 n=1 ctx=8k uniform page64 64h | 33.3 | 32.4 | 1.03 | 32.8
| 31.5 | 1.04 |
| paged B=128 n=1 ctx=8k mixed page64 64h | 33.9 | 32.9 | 1.03 | 32.9 |
31.8 | 1.03 |
| paged B=128 n=1 ctx=32k uniform page64 64h | 93.4 | 93.7 | 1.00 | 92.1
| 92.0 | 1.00 |
| paged B=128 n=1 ctx=32k mixed page64 64h | 93.8 | 94.6 | 0.99 | 92.3 |
91.9 | 1.00 |
| paged B=128 n=1 ctx=128k uniform page64 64h | 343.0 | 343.8 | 1.00 |
338.6 | 338.2 | 1.00 |
| paged B=128 n=1 ctx=128k mixed page64 64h | 340.8 | 341.5 | 1.00 |
336.4 | 336.1 | 1.00 |
| paged B=128 n=2 ctx=1k uniform page64 64h | 10.9 | 9.8 | 1.11 | 10.3 |
not served by this PR | — |
| paged B=128 n=2 ctx=1k mixed page64 64h | 11.4 | not served by this PR
| — | 10.8 | not served by this PR | — |
| paged B=128 n=2 ctx=4k uniform page64 64h | 20.9 | not served by this
PR | — | 20.2 | 19.6 | 1.03 |
| paged B=128 n=2 ctx=4k mixed page64 64h | 22.7 | 21.1 | 1.08 | 21.6 |
19.9 | 1.09 |
| paged B=128 n=2 ctx=8k uniform page64 64h | 35.3 | 33.5 | 1.05 | 33.8
| 32.4 | 1.05 |
| paged B=128 n=2 ctx=8k mixed page64 64h | 34.8 | 33.5 | 1.04 | 33.5 |
32.2 | 1.04 |
| paged B=128 n=2 ctx=32k uniform page64 64h | 98.0 | 97.7 | 1.00 | 95.2
| 95.6 | 1.00 |
| paged B=128 n=2 ctx=32k mixed page64 64h | 96.8 | 97.8 | 0.99 | 94.5 |
95.1 | 0.99 |
| paged B=128 n=2 ctx=128k uniform page64 64h | 361.4 | 360.8 | 1.00 |
350.3 | 351.8 | 1.00 |
| paged B=128 n=2 ctx=128k mixed page64 64h | 372.8 | 370.8 | 1.01 |
360.0 | 360.1 | 1.00 |
| paged B=128 n=4 ctx=1k uniform page64 64h | 12.6 | 12.4 | 1.02 | 11.6
| 11.7 | 0.99 |
| paged B=128 n=4 ctx=1k mixed page64 64h | 13.2 | 13.1 | 1.01 | 12.2 |
11.9 | 1.02 |
| paged B=128 n=4 ctx=4k uniform page64 64h | 26.7 | 26.6 | 1.00 | 23.8
| 24.0 | 0.99 |
| paged B=128 n=4 ctx=4k mixed page64 64h | 27.3 | 27.4 | 1.00 | 24.4 |
24.5 | 1.00 |
| paged B=128 n=4 ctx=8k uniform page64 64h | 43.0 | 43.0 | 1.00 | 40.1
| 40.1 | 1.00 |
| paged B=128 n=4 ctx=8k mixed page64 64h | 44.3 | 44.2 | 1.00 | 40.7 |
40.4 | 1.01 |
| paged B=128 n=4 ctx=32k uniform page64 64h | 137.6 | 137.1 | 1.00 |
125.7 | 126.0 | 1.00 |
| paged B=128 n=4 ctx=32k mixed page64 64h | 139.1 | 139.1 | 1.00 |
128.4 | 128.8 | 1.00 |
| paged B=128 n=4 ctx=128k uniform page64 64h | 582.4 | 592.3 | 0.98 |
491.6 | 491.2 | 1.00 |
| paged B=128 n=4 ctx=128k mixed page64 64h | 598.3 | 600.0 | 1.00 |
500.3 | 499.6 | 1.00 |
| paged B=SMs n=1 ctx=1k uniform page64 64h | 10.6 | 9.7 | 1.09 | 10.1 |
not served by this PR | — |
| paged B=SMs n=1 ctx=1k mixed page64 64h | 11.0 | 10.1 | 1.09 | 10.5 |
9.7 | 1.09 |
| paged B=SMs n=1 ctx=4k uniform page64 64h | 22.6 | 21.5 | 1.05 | 22.5
| 21.1 | 1.07 |
| paged B=SMs n=1 ctx=4k mixed page64 64h | 22.7 | 21.5 | 1.06 | 22.5 |
21.1 | 1.07 |
| paged B=SMs n=1 ctx=8k uniform page64 64h | 38.3 | 36.9 | 1.04 | 37.9
| 36.5 | 1.04 |
| paged B=SMs n=1 ctx=8k mixed page64 64h | 37.8 | 36.7 | 1.03 | 37.9 |
36.4 | 1.04 |
| paged B=SMs n=1 ctx=32k uniform page64 64h | 106.6 | 106.9 | 1.00 |
107.6 | 107.7 | 1.00 |
| paged B=SMs n=1 ctx=32k mixed page64 64h | 109.3 | 109.1 | 1.00 |
110.2 | 109.9 | 1.00 |
| paged B=SMs n=1 ctx=128k uniform page64 64h | 395.1 | 395.4 | 1.00 |
401.5 | 401.0 | 1.00 |
| paged B=SMs n=1 ctx=128k mixed page64 64h | 395.1 | 396.5 | 1.00 |
400.8 | 399.8 | 1.00 |
| paged B=SMs n=2 ctx=1k uniform page64 64h | 10.8 | not served by this
PR | — | 10.0 | not served by this PR | — |
| paged B=SMs n=2 ctx=1k mixed page64 64h | 10.9 | not served by this PR
| — | 10.3 | not served by this PR | — |
| paged B=SMs n=2 ctx=4k uniform page64 64h | 22.9 | not served by this
PR | — | 22.7 | 22.2 | 1.02 |
| paged B=SMs n=2 ctx=4k mixed page64 64h | 22.6 | not served by this PR
| — | 22.2 | 22.2 | 1.00 |
| paged B=SMs n=2 ctx=8k uniform page64 64h | 40.1 | 38.0 | 1.05 | 38.8
| 37.6 | 1.03 |
| paged B=SMs n=2 ctx=8k mixed page64 64h | 39.9 | 38.2 | 1.04 | 39.5 |
38.0 | 1.04 |
| paged B=SMs n=2 ctx=32k uniform page64 64h | 111.8 | 111.1 | 1.01 |
111.2 | 111.0 | 1.00 |
| paged B=SMs n=2 ctx=32k mixed page64 64h | 112.8 | 112.9 | 1.00 |
113.2 | 112.7 | 1.00 |
| paged B=SMs n=2 ctx=128k uniform page64 64h | 418.3 | 415.9 | 1.01 |
415.3 | 414.5 | 1.00 |
| paged B=SMs n=2 ctx=128k mixed page64 64h | 416.6 | 417.7 | 1.00 |
413.8 | 414.0 | 1.00 |
| paged B=SMs n=4 ctx=1k uniform page64 64h | 13.5 | 13.5 | 1.00 | 12.5
| not served by this PR | — |
| paged B=SMs n=4 ctx=1k mixed page64 64h | 14.2 | 14.2 | 1.00 | 13.2 |
13.3 | 0.99 |
| paged B=SMs n=4 ctx=4k uniform page64 64h | 31.0 | 30.8 | 1.01 | 29.6
| 29.5 | 1.00 |
| paged B=SMs n=4 ctx=4k mixed page64 64h | 29.6 | 29.6 | 1.00 | 27.6 |
27.9 | 0.99 |
| paged B=SMs n=4 ctx=8k uniform page64 64h | 51.7 | 51.9 | 1.00 | 49.2
| 49.4 | 0.99 |
| paged B=SMs n=4 ctx=8k mixed page64 64h | 48.8 | 48.7 | 1.00 | 45.7 |
45.4 | 1.01 |
| paged B=SMs n=4 ctx=32k uniform page64 64h | 160.4 | 160.7 | 1.00 |
149.9 | 150.2 | 1.00 |
| paged B=SMs n=4 ctx=32k mixed page64 64h | 156.4 | 156.3 | 1.00 |
146.7 | 146.7 | 1.00 |
| paged B=SMs n=4 ctx=128k uniform page64 64h | 714.4 | 713.2 | 1.00 |
598.6 | 597.4 | 1.00 |
| paged B=SMs n=4 ctx=128k mixed page64 64h | 691.7 | 677.4 | 1.02 |
588.8 | 588.0 | 1.00 |
| paged B=256 n=1 ctx=1k uniform page64 64h | 19.6 | 17.9 | 1.09 | 19.3
| not served by this PR | — |
| paged B=256 n=1 ctx=1k mixed page64 64h | 20.3 | 18.4 | 1.10 | 19.6 |
17.5 | 1.11 |
| paged B=256 n=1 ctx=4k uniform page64 64h | 41.4 | 39.2 | 1.06 | 40.1
| 37.9 | 1.06 |
| paged B=256 n=1 ctx=4k mixed page64 64h | 41.6 | 39.5 | 1.05 | 40.5 |
38.3 | 1.06 |
| paged B=256 n=1 ctx=8k uniform page64 64h | 66.8 | 65.0 | 1.03 | 64.1
| 62.8 | 1.02 |
| paged B=256 n=1 ctx=8k mixed page64 64h | 66.4 | 64.0 | 1.04 | 64.1 |
62.5 | 1.03 |
| paged B=256 n=1 ctx=32k uniform page64 64h | 185.2 | 185.0 | 1.00 |
180.9 | 180.3 | 1.00 |
| paged B=256 n=1 ctx=32k mixed page64 64h | 185.8 | 185.7 | 1.00 |
182.0 | 181.4 | 1.00 |
| paged B=256 n=1 ctx=128k uniform page64 64h | 686.3 | 687.3 | 1.00 |
667.9 | 667.5 | 1.00 |
| paged B=256 n=1 ctx=128k mixed page64 64h | 683.5 | 684.3 | 1.00 |
666.5 | 666.1 | 1.00 |
| paged B=256 n=2 ctx=1k uniform page64 64h | 20.6 | not served by this
PR | — | 19.7 | not served by this PR | — |
| paged B=256 n=2 ctx=1k mixed page64 64h | 21.9 | not served by this PR
| — | 20.7 | not served by this PR | — |
| paged B=256 n=2 ctx=4k uniform page64 64h | 43.0 | not served by this
PR | — | 41.7 | 41.9 | 1.00 |
| paged B=256 n=2 ctx=4k mixed page64 64h | 43.4 | not served by this PR
| — | 41.7 | 41.5 | 1.00 |
| paged B=256 n=2 ctx=8k uniform page64 64h | 69.0 | 67.9 | 1.02 | 65.9
| 64.7 | 1.02 |
| paged B=256 n=2 ctx=8k mixed page64 64h | 71.4 | 67.8 | 1.05 | 67.7 |
65.2 | 1.04 |
| paged B=256 n=2 ctx=32k uniform page64 64h | 193.0 | 193.1 | 1.00 |
186.9 | 187.5 | 1.00 |
| paged B=256 n=2 ctx=32k mixed page64 64h | 195.2 | 195.6 | 1.00 |
189.6 | 189.9 | 1.00 |
| paged B=256 n=2 ctx=128k uniform page64 64h | 732.7 | 732.0 | 1.00 |
692.4 | 692.7 | 1.00 |
| paged B=256 n=2 ctx=128k mixed page64 64h | 734.4 | 737.2 | 1.00 |
695.0 | 695.1 | 1.00 |
| paged B=256 n=4 ctx=1k uniform page64 64h | 24.5 | 24.5 | 1.00 | 22.9
| not served by this PR | — |
| paged B=256 n=4 ctx=1k mixed page64 64h | 25.9 | 26.2 | 0.99 | 24.4 |
23.8 | 1.02 |
| paged B=256 n=4 ctx=4k uniform page64 64h | 53.4 | 53.0 | 1.01 | 50.0
| 49.9 | 1.00 |
| paged B=256 n=4 ctx=4k mixed page64 64h | 53.6 | 53.8 | 1.00 | 48.7 |
48.4 | 1.01 |
| paged B=256 n=4 ctx=8k uniform page64 64h | 87.5 | 88.3 | 0.99 | 81.9
| 82.0 | 1.00 |
| paged B=256 n=4 ctx=8k mixed page64 64h | 83.4 | 83.7 | 1.00 | 78.1 |
77.4 | 1.01 |
| paged B=256 n=4 ctx=32k uniform page64 64h | 285.9 | 286.0 | 1.00 |
249.0 | 250.7 | 0.99 |
| paged B=256 n=4 ctx=32k mixed page64 64h | 284.6 | 285.3 | 1.00 |
248.3 | 247.5 | 1.00 |
| paged B=256 n=4 ctx=128k uniform page64 64h | 1254.7 | 1255.9 | 1.00 |
1014.4 | 1013.7 | 1.00 |
| paged B=256 n=4 ctx=128k mixed page64 64h | 1247.6 | 1248.8 | 1.00 |
1009.2 | 1013.3 | 1.00 |
| paged B=512 n=1 ctx=1k uniform page64 64h | 39.1 | 35.6 | 1.10 | 37.1
| not served by this PR | — |
| paged B=512 n=1 ctx=1k mixed page64 64h | 41.2 | 36.8 | 1.12 | 38.5 |
35.7 | 1.08 |
| paged B=512 n=1 ctx=4k uniform page64 64h | 79.7 | 75.9 | 1.05 | 75.5
| 73.3 | 1.03 |
| paged B=512 n=1 ctx=4k mixed page64 64h | 80.8 | 75.8 | 1.07 | 77.2 |
72.7 | 1.06 |
| paged B=512 n=1 ctx=8k uniform page64 64h | 122.9 | 118.4 | 1.04 |
120.0 | 114.9 | 1.04 |
| paged B=512 n=1 ctx=8k mixed page64 64h | 122.7 | 120.1 | 1.02 | 119.8
| 116.7 | 1.03 |
| paged B=512 n=1 ctx=32k uniform page64 64h | 366.3 | 365.6 | 1.00 |
357.0 | 356.8 | 1.00 |
| paged B=512 n=1 ctx=32k mixed page64 64h | 368.5 | 368.1 | 1.00 |
359.1 | 358.3 | 1.00 |
| paged B=512 n=1 ctx=128k uniform page64 64h | 1375.6 | 1380.7 | 1.00 |
1333.0 | 1333.4 | 1.00 |
| paged B=512 n=1 ctx=128k mixed page64 64h | not served on FlashInfer
main | not served by this PR | — | not served on FlashInfer main | not
served by this PR | — |
| paged B=512 n=2 ctx=1k uniform page64 64h | 40.2 | not served by this
PR | — | 36.9 | not served by this PR | — |
| paged B=512 n=2 ctx=1k mixed page64 64h | 42.1 | not served by this PR
| — | 38.6 | not served by this PR | — |
| paged B=512 n=2 ctx=4k uniform page64 64h | 81.0 | not served by this
PR | — | 78.3 | 78.1 | 1.00 |
| paged B=512 n=2 ctx=4k mixed page64 64h | 81.7 | 82.7 | 0.99 | 78.3 |
78.2 | 1.00 |
| paged B=512 n=2 ctx=8k uniform page64 64h | 128.6 | 124.2 | 1.04 |
126.2 | 123.9 | 1.02 |
| paged B=512 n=2 ctx=8k mixed page64 64h | 127.7 | 123.7 | 1.03 | 126.0
| 122.3 | 1.03 |
| paged B=512 n=2 ctx=32k uniform page64 64h | 388.1 | 386.2 | 1.00 |
372.7 | 371.2 | 1.00 |
| paged B=512 n=2 ctx=32k mixed page64 64h | 382.2 | 380.8 | 1.00 |
368.0 | 366.7 | 1.00 |
| paged B=512 n=2 ctx=128k uniform page64 64h | 1517.4 | 1495.2 | 1.01 |
1382.7 | 1383.1 | 1.00 |
| paged B=512 n=2 ctx=128k mixed page64 64h | 1514.1 | 1518.0 | 1.00 |
1381.5 | 1380.8 | 1.00 |
| paged B=512 n=4 ctx=1k uniform page64 64h | 47.2 | 47.4 | 1.00 | 44.3
| not served by this PR | — |
| paged B=512 n=4 ctx=1k mixed page64 64h | 50.7 | 50.8 | 1.00 | 47.8 |
46.9 | 1.02 |
| paged B=512 n=4 ctx=4k uniform page64 64h | 105.2 | 105.6 | 1.00 |
99.5 | 99.3 | 1.00 |
| paged B=512 n=4 ctx=4k mixed page64 64h | 102.4 | 101.8 | 1.01 | 95.0
| 94.8 | 1.00 |
| paged B=512 n=4 ctx=8k uniform page64 64h | 172.0 | 173.0 | 0.99 |
162.6 | 163.2 | 1.00 |
| paged B=512 n=4 ctx=8k mixed page64 64h | 163.4 | 162.7 | 1.00 | 152.2
| 150.7 | 1.01 |
| paged B=512 n=4 ctx=32k uniform page64 64h | 593.0 | 592.1 | 1.00 |
514.5 | 517.3 | 0.99 |
| paged B=512 n=4 ctx=32k mixed page64 64h | 577.3 | 577.8 | 1.00 |
502.9 | 501.9 | 1.00 |
| paged B=512 n=4 ctx=128k uniform page64 64h | 2620.8 | 2645.6 | 0.99 |
2115.3 | 2119.1 | 1.00 |
| paged B=512 n=4 ctx=128k mixed page64 64h | 2681.7 | 2661.8 | 1.01 |
2130.5 | 2129.3 | 1.00 |
| paged B=16 n=1 ctx=4k uniform page64 32h | 8.7 | 6.5 | 1.33 | 8.2 |
6.4 | 1.29 |
| paged B=16 n=1 ctx=4k uniform page32 64h | 7.2 | 6.6 | 1.09 | 6.8 |
6.5 | 1.06 |
| paged B=16 n=1 ctx=32k uniform page64 32h | 18.2 | 18.2 | 1.00 | 17.6
| 17.5 | 1.00 |
| paged B=16 n=1 ctx=32k uniform page32 64h | 18.4 | 18.3 | 1.00 | 17.7
| 17.8 | 0.99 |
| paged B=16 n=2 ctx=4k uniform page64 32h | 7.2 | 6.7 | 1.07 | 6.9 |
6.6 | 1.05 |
| paged B=16 n=2 ctx=4k uniform page32 64h | 7.6 | 7.1 | 1.06 | 7.2 |
6.9 | 1.04 |
| paged B=16 n=2 ctx=32k uniform page64 32h | 18.7 | 18.6 | 1.01 | 18.0
| 17.8 | 1.01 |
| paged B=16 n=2 ctx=32k uniform page32 64h | 19.5 | 19.4 | 1.01 | 18.4
| 18.4 | 1.00 |
| paged B=SMs n=1 ctx=4k uniform page64 32h | 22.3 | 21.2 | 1.05 | 22.1
| 20.8 | 1.06 |
| paged B=SMs n=1 ctx=4k uniform page32 64h | 22.6 | 21.4 | 1.06 | 22.2
| 21.0 | 1.06 |
| paged B=SMs n=1 ctx=32k uniform page64 32h | 106.6 | 106.7 | 1.00 |
107.5 | 107.2 | 1.00 |
| paged B=SMs n=1 ctx=32k uniform page32 64h | 107.7 | 107.3 | 1.00 |
108.3 | 108.2 | 1.00 |
| paged B=SMs n=2 ctx=4k uniform page64 32h | 22.8 | not served by this
PR | — | 22.4 | 21.3 | 1.05 |
| paged B=SMs n=2 ctx=4k uniform page32 64h | 23.6 | 22.1 | 1.06 | 22.9
| 21.6 | 1.06 |
| paged B=SMs n=2 ctx=32k uniform page64 32h | 109.7 | 109.6 | 1.00 |
110.4 | 109.6 | 1.01 |
| paged B=SMs n=2 ctx=32k uniform page32 64h | 112.0 | 112.0 | 1.00 |
112.5 | 111.6 | 1.01 |
| dense Q=1 K=1 prefix=0 64h | 4.0 | 4.0 | 1.00 | 4.0 | 3.7 | 1.07 |
| dense Q=1 K=4101 prefix=4100 64h | 10.9 | 4.2 | 2.63 | 10.3 | 3.9 |
2.63 |
| dense Q=1 K=32780 prefix=32779 64h | 59.0 | 4.9 | 11.97 | 55.4 | 4.9 |
11.32 |
| dense Q=1 K=131078 prefix=131077 64h | 224.1 | 8.1 | 27.68 | 209.9 |
7.9 | 26.56 |
| dense Q=37 K=37 prefix=0 64h | 3.9 | 3.9 | 1.01 | 3.8 | 3.8 | 1.00 |
| dense Q=37 K=4137 prefix=4100 64h | 11.4 | 6.0 | 1.90 | 10.8 | 5.7 |
1.89 |
| dense Q=37 K=32816 prefix=32779 64h | 60.9 | 14.5 | 4.19 | 57.2 | 13.1
| 4.38 |
| dense Q=37 K=131114 prefix=131077 64h | 227.5 | 40.9 | 5.56 | 215.0 |
34.5 | 6.23 |
| dense Q=128 K=128 prefix=0 64h | 4.1 | 4.0 | 1.01 | 3.9 | 3.9 | 1.00 |
| dense Q=128 K=4228 prefix=4100 64h | 12.2 | 9.8 | 1.24 | 10.9 | 9.0 |
1.21 |
| dense Q=128 K=32907 prefix=32779 64h | 67.1 | 36.7 | 1.83 | 55.7 |
30.4 | 1.83 |
| dense Q=128 K=131205 prefix=131077 64h | 238.8 | 121.4 | 1.97 | 207.7
| 102.8 | 2.02 |
| dense Q=1024 K=1024 prefix=0 64h | 11.3 | 11.3 | 1.00 | 10.8 | 10.7 |
1.01 |
| dense Q=1024 K=5124 prefix=4100 64h | 44.2 | 44.3 | 1.00 | 37.4 | 37.2
| 1.01 |
| dense Q=1024 K=33803 prefix=32779 64h | 255.0 | 255.4 | 1.00 | 220.5 |
220.2 | 1.00 |
| dense Q=1024 K=132101 prefix=131077 64h | 1083.3 | 1093.6 | 0.99 |
881.5 | 880.2 | 1.00 |
| dense Q=4096 K=4096 prefix=0 64h | 71.5 | 71.3 | 1.00 | 61.1 | 61.1 |
1.00 |
| dense Q=4096 K=8196 prefix=4100 64h | 179.5 | 179.8 | 1.00 | 153.3 |
153.5 | 1.00 |
| dense Q=4096 K=36875 prefix=32779 64h | 1098.7 | 1094.0 | 1.00 | 861.5
| 862.0 | 1.00 |
| dense Q=4096 K=135173 prefix=131077 64h | 4381.9 | 4379.5 | 1.00 |
3484.9 | 3484.3 | 1.00 |
| dense Q=8192 K=8192 prefix=0 64h | 249.4 | 250.1 | 1.00 | 208.2 |
208.3 | 1.00 |
| dense Q=8192 K=12292 prefix=4100 64h | 502.8 | 501.6 | 1.00 | 398.7 |
397.6 | 1.00 |
| dense Q=8192 K=40971 prefix=32779 64h | 2419.1 | 2419.2 | 1.00 |
1860.0 | 1860.9 | 1.00 |
| dense Q=8192 K=139269 prefix=131077 64h | 9065.2 | 9063.2 | 1.00 |
7051.8 | 7052.9 | 1.00 |
| dense Q=16231 K=16231 prefix=0 64h | 1046.0 | 1035.9 | 1.01 | 824.1 |
823.8 | 1.00 |
| dense Q=16231 K=20331 prefix=4100 64h | 1570.5 | 1589.9 | 0.99 |
1248.4 | 1248.4 | 1.00 |
| dense Q=16231 K=49010 prefix=32779 64h | 5399.2 | 5401.1 | 1.00 |
4231.6 | 4233.0 | 1.00 |
| dense Q=16231 K=147308 prefix=131077 64h | 18462.1 | 18461.4 | 1.00 |
14526.5 | 14530.1 | 1.00 |
| dense Q=4096 K=36875 prefix=32779 row chunks of 2048 64h | 1085.7 |
1072.0 | 1.01 | 853.8 | 853.5 | 1.00 |
| dense Q=4096 K=135173 prefix=131077 row chunks of 2048 64h | 4386.0 |
4389.6 | 1.00 | 3427.4 | 3441.7 | 1.00 |
| dense Q=8192 K=40971 prefix=32779 row chunks of 2048 64h | 2385.7 |
2373.1 | 1.01 | 1876.2 | 1873.9 | 1.00 |
| dense Q=8192 K=139269 prefix=131077 row chunks of 2048 64h | 8907.0 |
8949.5 | 1.00 | 7045.2 | 7045.7 | 1.00 |
| dense Q=16231 K=49010 prefix=32779 row chunks of 2048 64h | 5371.2 |
5369.1 | 1.00 | 4256.7 | 4258.3 | 1.00 |
| dense Q=16231 K=147308 prefix=131077 row chunks of 2048 64h | 18335.4
| 18330.6 | 1.00 | 14577.9 | 14578.1 | 1.00 |
| dense Q=128 K=6278 two sequences, prefix=4100 / 2050 64h | 11.6 | 8.5
| 1.36 | 10.8 | 7.9 | 1.37 |
| dense Q=4096 K=53264 two sequences, prefix=32779 / 16389 64h | 728.8 |
724.8 | 1.01 | 561.2 | 561.8 | 1.00 |
| dense Q=37 K=4137 prefix=4100 32h | 6.0 | 6.0 | 1.00 | 5.6 | 5.7 |
0.98 |
| dense Q=1024 K=33803 prefix=32779 32h | 127.6 | 127.6 | 1.00 | 108.3 |
108.4 | 1.00 |
| dense Q=2 K=2 prefix=0 64h | 3.9 | 4.0 | 0.97 | 3.7 | 4.0 | 0.95 |
| dense Q=2 K=4102 prefix=4100 64h | 11.0 | 5.0 | 2.20 | 10.2 | 4.9 |
2.11 |
| dense Q=8 K=8 prefix=0 64h | 3.9 | 3.9 | 1.00 | 3.9 | 3.7 | 1.03 |
| dense Q=8 K=4108 prefix=4100 64h | 11.1 | 4.8 | 2.30 | 10.3 | 4.7 |
2.20 |
| dense Q=3 K=3 prefix=0 64h | 4.0 | 3.9 | 1.02 | 3.9 | 3.7 | 1.03 |
| dense Q=3 K=4103 prefix=4100 64h | 10.9 | 4.9 | 2.24 | 10.4 | 4.7 |
2.23 |
| dense Q=7 K=7 prefix=0 64h | 3.8 | 3.9 | 0.99 | 3.8 | 3.9 | 0.98 |
| dense Q=7 K=4107 prefix=4100 64h | 11.0 | 4.9 | 2.26 | 10.5 | 4.7 |
2.22 |
| dense Q=129 K=129 prefix=0 64h | 4.2 | 4.1 | 1.03 | 3.9 | 3.9 | 1.02 |
| dense Q=129 K=4229 prefix=4100 64h | 12.2 | 9.7 | 1.26 | 11.1 | 9.0 |
1.23 |
| dense Q=1023 K=1023 prefix=0 64h | 11.2 | 11.3 | 0.99 | 10.7 | 10.8 |
0.99 |
| dense Q=1023 K=5123 prefix=4100 64h | 44.1 | 44.1 | 1.00 | 38.2 | 38.1
| 1.00 |
| dense Q=16 K=16 prefix=0 64h | 3.9 | 3.9 | 0.99 | 3.7 | 3.8 | 0.99 |
| dense Q=16 K=4116 prefix=4100 64h | 11.2 | 4.9 | 2.27 | 10.5 | 4.7 |
2.22 |
| dense Q=64 K=64 prefix=0 64h | 4.0 | 4.0 | 1.00 | 3.8 | 3.8 | 1.00 |
| dense Q=64 K=4164 prefix=4100 64h | 11.5 | 6.9 | 1.65 | 10.7 | 6.4 |
1.68 |

The family's other Cake variants are dense FP8 32-head logits (two-stage
and fused single-launch routes) and dense FP4 32-head logits (packed
E2M1 with UE8M0 block scales, carried unchanged), and the family ships
on `sm_100a` (B200) and `sm_103a` (GB300).

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3bf6d32](https://github.com/flashinfer-ai/flashinfer/commit/3bf6d3202239a107989451257c6f594cb5d2f008)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T09:46:51Z
- **提交信息**: fix(cake_kimi_k3_attn_res): drain tcgen05.ld with tcgen05.wait::ld before the TMEM dealloc (persistent programs) (#6740)

## 📌 Description

The persistent Kimi-K3 AttnRes programs in
`flashinfer/experimental/cake_kimi_k3_attn_res` are the 288-thread
schedules whose consumer warps park FP32 partials in TMEM. Their
consumer warps read TMEM with `tcgen05.ld` and use the result registers
directly. After the token loop, all 288 threads meet at `barrier.sync 9,
288`, and consumer warp 0 then runs `tcgen05.dealloc`. No
`tcgen05.wait::ld` exists anywhere in these programs.

A true register dependency on a `tcgen05.ld` result orders only the
register value. The PTX ISA (tcgen05 memory consistency model, "Register
dependencies, same thread") states that such a dependency "does not
imply any other form of ordering ... To enforce such memory orderings
and avoiding anti-dependency hazards around `tcgen05.ld`,
`tcgen05.wait::ld` must be used." `tcgen05.wait::ld` is the completion
mechanism of `tcgen05.ld`. Without it, the TMEM columns can be
deallocated while a load from them has not completed.

This PR adds one `tcgen05.wait::ld.sync.aligned` per consumer thread
right before that cleanup barrier, in all 39 persistent programs:

* The wait runs once per CTA, outside every loop.
* In the three programs whose TMEM path is compiled only for SM100
(`__CUDA_ARCH__ == 1000`), the wait sits under the same guard as the
loads and the dealloc.
* No other line changes.

## 🧪 Tests

- `pytest tests/experimental/test_cake_kimi_k3_attn_res.py` on a B300
(SM103): 443 passed, 2 skipped.
- All 39 changed modules build for their registered targets (`sm_100a`,
`sm_103a`).
- The same change in the Cake source kernel compiles to one extra
instruction per CTA: a scoreboard-wait `NOP` before the cleanup
`BAR.SYNC`.
- Timing of the Cake source kernel on B300 at M = 1024: all 83 TMEM
variants run at the same speed, both back to back and cooled. The
fix/base ratio is 0.9984 to 1.0024, mean 1.0000.

## 🔍 Related

Non-persistent programs of this module with the same pattern
(`709f669fe8647d61aaf0`, `99f148a06e530e457f4a`) will follow separately.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- Improved attention-kernel synchronization by ensuring outstanding
tensor-memory reads complete before memory is released.
- Added architecture-specific synchronization for supported Hopper/SM100
execution paths.
- Helps prevent potential synchronization issues during consumer
completion and cleanup.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <yingyihuang2000@outlook.com>

### [e563bf9](https://github.com/flashinfer-ai/flashinfer/commit/e563bf9867ba6cf5ef0f7becff219343c6ac519e)

- **作者**: Meghan Cowan
- **时间**: 2026-10-20T09:29:38Z
- **提交信息**: feat(cake_gemm_allreduce): fused tensor-parallel GEMM + MNNVL Lamport all-reduce for Blackwell (SM100 / SM103) (#6493)

## Summary

Adds `flashinfer.comm.cake_gemm_allreduce(x, w, out, workspace,
launch_with_pdl=False)`: one kernel launch per rank that computes a
row-parallel linear's local partial `x_r @ w_r^T` (bf16 in, fp32
accumulate) and all-reduces it across the NVLink group through
FlashInfer's existing MNNVL Lamport all-reduce workspace
(`create_allreduce_fusion_workspace(backend="mnnvl")`), replacing the
`matmul` + `allreduce_fusion` pair in the decode regime (M <= 128) of
TP8 / TP4 / TP2 attention output and MoE down projections.

- `csrc/cake_gemm_allreduce/cake_gemm_allreduce_kernels.cu`: twelve
generated bf16 tcgen05 kernels (world sizes 2 / 4 / 8 x token tiles 16
one-shot, 32 / 64 / 128 two-shot), one architecture-neutral source
compiled for `sm_100a` and `sm_103a`; `manifest.json` carries the launch
contract.
- `csrc/cake_gemm_allreduce/cake_gemm_allreduce_binding.cu`: tvm-ffi
launcher (driver-encoded K-major SWIZZLE_128B tensor maps, dynamic
shared memory set once per route, PDL attribute on request).
- `flashinfer/jit/cake_gemm_allreduce.py`: JIT loader (one module for
every supported build target), route table, workspace arithmetic.
- `flashinfer/comm/cake_gemm_allreduce.py`: the public API, exported
from `flashinfer.comm`.
- `tests/comm/test_cake_gemm_allreduce.py`: route / workspace unit tests
and a multi-rank test (2 / 4 / 8 GPUs with MNNVL fabric memory) against
the fp32 all-reduce of the bf16 local partials, with bitwise cross-rank
identity and PDL relaunch.

## Regime

Built for the decode band, `M <= 128` tokens per rank: the mainloop
streams the weight shard once per 128-token tile, which is where one
fused launch beats `mm_bf16` + `allreduce_fusion`. Above 128 tokens the
weight is re-streamed per tile and the two-call path is about 1.3x
faster, so callers should route larger token counts there; any positive
`M` is accepted.

## Semantics

Every rank receives bitwise the same `out`: the local partial is rounded
to bf16 once (as the unfused chain does before its collective), the
cross-rank sum is taken in fixed rank order in fp32, one final rounding.
Checked at `atol = rtol = 1e-2` against the NCCL fp32 all-reduce of the
bf16 partials. `M` is any positive row count (the kernel's TMA loads
zero-fill past M, the output tail is masked); `K % 128 == 0`, `N % 64 ==
0`; the workspace needs `cake_gemm_allreduce_workspace_bytes(M, N,
world_size)` bytes per Lamport buffer and stays usable by
`allreduce_fusion`.

## Measurements

Blackwell NVL72 (GB300), two trays, TP8 (`world_size = 8`), `N = 7168`,
bf16, us per launch, CUDA graphs of 16 back-to-back launches timed with
CUPTI (slowest rank), L2 flushed between replays. The baseline is
FlashInfer's public two-launch path: `flashinfer.gemm.mm_bf16` (cuBLASLt
backend, within 0.1 us of `auto` / cuDNN at these shapes) followed by
`allreduce_fusion` on the same MNNVL workspace (automatic one-/two-shot
selection, PDL). "FI CuTe-DSL fused class" is
`flashinfer.cute_dsl.gemm_allreduce_two_shot` called directly (M padded
to 128 as it requires, flags reset per launch). "In PDL chain" is each
arm's increment behind a producer GEMM that triggers its dependents
early, i.e. its cost inside a decode layer.

| K_r | M | Cake fused (1 launch) | FI mm_bf16 + allreduce_fusion (2
launches) | speedup | FI CuTe-DSL fused class | speedup | Cake fused, in
PDL chain | FI 2-launch, in PDL chain | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1536 | 1 | 7.3 | 8.6 | 1.17x | 44.4 | 6.05x | 6.7 | 8.2 | 1.24x |
| 1536 | 8 | 7.9 | 8.8 | 1.11x | 44.6 | 5.62x | 6.4 | 8.0 | 1.25x |
| 1536 | 16 | 8.6 | 9.0 | 1.05x | 43.8 | 5.10x | 7.4 | 9.0 | 1.22x |
| 1536 | 32 | 9.3 | 10.3 | 1.10x | 44.0 | 4.71x | 8.2 | 10.4 | 1.26x |
| 1536 | 64 | 10.4 | 11.8 | 1.13x | 43.7 | 4.20x | 9.7 | 11.6 | 1.19x |
| 1536 | 128 | 13.1 | 12.6 | 0.96x | 43.7 | 3.33x | 12.6 | 13.1 | 1.04x
|
| 1536 | 256 | 24.9 | 18.7 | 0.75x | 48.1 | 1.93x | 24.2 | 19.3 | 0.80x
|
| 1536 | 512 | 41.0 | 31.8 | 0.77x | 70.4 | 1.72x | 41.6 | 34.8 | 0.84x
|
| 1536 | 1024 | 76.3 | 59.0 | 0.77x | 106.8 | 1.40x | 81.4 | 63.5 |
0.78x |
| 768 | 1 | 6.2 | 7.2 | 1.16x | 42.7 | 6.89x | 5.3 | 6.7 | 1.27x |
| 768 | 8 | 7.1 | 7.5 | 1.06x | 42.8 | 6.03x | 5.7 | 6.7 | 1.18x |
| 768 | 16 | 8.0 | 8.1 | 1.01x | 42.0 | 5.27x | 7.0 | 8.1 | 1.16x |
| 768 | 32 | 8.4 | 9.0 | 1.08x | 42.3 | 5.06x | 7.5 | 9.3 | 1.25x |
| 768 | 64 | 9.5 | 10.3 | 1.09x | 42.0 | 4.44x | 8.7 | 10.2 | 1.18x |
| 768 | 128 | 11.7 | 11.4 | 0.98x | 42.1 | 3.60x | 10.9 | 11.5 | 1.06x |
| 768 | 256 | 22.1 | 17.0 | 0.77x | 45.6 | 2.06x | 21.7 | 17.2 | 0.79x |
| 768 | 512 | 35.8 | 28.8 | 0.80x | 67.0 | 1.87x | 35.0 | 30.2 | 0.86x |
| 768 | 1024 | 68.1 | 52.4 | 0.77x | 101.1 | 1.48x | 68.5 | 54.5 | 0.80x
|

In the decode band (M <= 64) the single fused launch is 1.05-1.17x
faster than FlashInfer's two-launch path standalone and 1.16-1.27x
faster behind a PDL producer GEMM, level at M = 128, and 4-7x faster
than FlashInfer's CuTe-DSL fused class. Above 128 tokens the kernel's
small-M mainloop re-streams the weight shard per 128-token tile and the
two-launch path is about 1.3x faster (the fused launch still beats the
CuTe-DSL class by 1.4-2x there); callers should route M > 128 to
`mm_bf16` + `allreduce_fusion`.

The same ratios were measured on GB200 NVL72 (TP8) and on one tray
(TP4). The delivered module built by FlashInfer's JIT is bitwise
identical to the reference implementation at every M on eight GPUs for
both `K_r`.

## Test plan

- [x] `pytest tests/comm/test_cake_gemm_allreduce.py` (unit tests;
multi-rank at world sizes 2 and 4 on an SM103 tray with MNNVL fabric
memory; world size 8 skipped there)
- [x] `pre-commit run --files` on every added / changed file
- [x] world size 8 across two trays (two Blackwell NVL72 trays): the
delivered module built by FlashInfer's JIT is bitwise identical to the
reference implementation at every M for both K_r, within tolerance of
the fp32 all-reduce reference


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added fused bfloat16 GEMM and all-reduce for tensor-parallel workloads
on supported Blackwell GPUs.
* Supports world sizes of 2, 4, or 8 and token counts up to 128, with
automatic route selection and workspace sizing.
  * Added an optional launch mode for stream serialization.
* **Tests**
* Added coverage for route selection, workspace sizing, input
validation, and multi-GPU result correctness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a6b7d64](https://github.com/flashinfer-ai/flashinfer/commit/a6b7d640f60f05056c29a1a55955c0395f4fe98e)

- **作者**: eigen
- **时间**: 2026-10-20T09:28:43Z
- **提交信息**: perf(cake_causal_conv1d): 2-D TMA stage loads in the sm_100a/sm_103a with grad (#6844)

`cake_causal_conv1d_train` has one data-type variant: BF16 in/out with
FP32 math, a packed width-4 depthwise causal conv fused with SiLU, with
a forward and a backward program. This PR replaces the sm_100a and
sm_103a backward program with its 2-D TMA stage-load version (one 2-D
TMA box per tensor and pipeline stage on the per-row copy path). The
baseline is the previous Cake version of this kernel in FlashInfer, the
backward program from PR #6816.

**Backward latency, NVIDIA GB300 (sm_103a), CUDA 13.4**

| S | C | previous (us) | this PR (us) | ratio (previous / this PR) |
|---:|---:|---:|---:|---:|
| 239718 | 512 | 155.2 | 155.0 | 1.0018 |
| 245028 | 512 | 156.0 | 156.1 | 0.9998 |
| 249866 | 512 | 159.2 | 159.3 | 0.9990 |
| 250340 | 512 | 160.8 | 160.7 | 1.0006 |
| 258574 | 512 | 162.9 | 162.9 | 0.9999 |
| 259042 | 512 | 164.6 | 164.6 | 0.9997 |
| 259584 | 512 | 164.3 | 164.4 | 0.9996 |
| 261393 | 512 | 167.4 | 167.0 | 1.0021 |
| 250340 | 128 | 59.5 | 59.5 | 1.0000 |
| 250340 | 256 | 94.7 | 94.8 | 0.9981 |
| 250340 | 1024 | 293.8 | 293.8 | 0.9998 |
| 250340 | 2048 | 694.4 | 583.0 | 1.1911 |
| 250340 | 4096 | 1363.2 | 1140.0 | 1.1958 |
| 250340 | 8192 | 2709.7 | 2261.4 | 1.1982 |

**Backward latency, NVIDIA B200 (sm_100a), CUDA 13.4**

| S | C | previous (us) | this PR (us) | ratio (previous / this PR) |
|---:|---:|---:|---:|---:|
| 239718 | 512 | 170.5 | 170.6 | 0.9992 |
| 245028 | 512 | 172.2 | 172.4 | 0.9983 |
| 249866 | 512 | 179.0 | 178.7 | 1.0014 |
| 250340 | 512 | 177.4 | 177.2 | 1.0014 |
| 258574 | 512 | 181.6 | 181.2 | 1.0026 |
| 259042 | 512 | 181.6 | 181.7 | 0.9995 |
| 259584 | 512 | 183.7 | 183.2 | 1.0031 |
| 261393 | 512 | 185.6 | 185.5 | 1.0006 |
| 250340 | 128 | 64.3 | 63.4 | 1.0149 |
| 250340 | 256 | 104.5 | 103.1 | 1.0137 |
| 250340 | 1024 | 329.8 | 329.9 | 0.9998 |
| 250340 | 2048 | 782.5 | 657.1 | 1.1907 |
| 250340 | 4096 | 1538.3 | 1286.8 | 1.1954 |
| 250340 | 8192 | 3069.7 | 2562.1 | 1.1981 |

The kernel's other Cake programs, the forward and the sm_107a backward,
are unchanged in this PR; the family ships on sm_100a, sm_103a and
sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Performance**
- Improved training-kernel execution for supported GPU architectures,
including more efficient memory transfers in applicable segmented
workloads.
- Added stronger validation for tensor layouts, dimensions, alignment,
and device placement to improve runtime reliability.

- **Compatibility**
- Updated backward execution for select GPU architectures while
preserving existing behavior on other supported architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [23f3e8f](https://github.com/flashinfer-ai/flashinfer/commit/23f3e8f63b66e9f42f24ac4e3e71dc7c38afbd00)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T08:05:58Z
- **提交信息**: fix(cake_kimi_k3_attn_res): drain tcgen05.ld with tcgen05.wait::ld before the TMEM dealloc (native programs) (#6744)

## 📌 Description

The two native Kimi-K3 AttnRes programs in
`flashinfer/experimental/cake_kimi_k3_attn_res` have the same missing
drain that #6740 fixes in the persistent programs:

* `cake_kimi_k3_attn_res_99f148a06e530e457f4a` (route key `native_k8`);
* `cake_kimi_k3_attn_res_709f669fe8647d61aaf0` (route key
`native_m128`).

Both are built for SM100 and SM103.

Their consumer warps read TMEM with `tcgen05.ld` and use the result
registers directly. After the token loop, all 288 threads meet at
`barrier.sync 0, 288`, and warp 0 then runs `tcgen05.dealloc`. No
`tcgen05.wait::ld` exists anywhere in these programs.

A true register dependency on a `tcgen05.ld` result orders only the
register value. The PTX ISA (tcgen05 memory consistency model, "Register
dependencies, same thread") says such a dependency "does not imply any
other form of ordering ... To enforce such memory orderings and avoiding
anti-dependency hazards around `tcgen05.ld`, `tcgen05.wait::ld` must be
used." Without the wait, the TMEM columns can be deallocated while a
load from them is still in flight.

**Changes:**

* Each consumer thread runs one `tcgen05.wait::ld.sync.aligned` right
before the cleanup barrier, in both programs. The wait runs once per
CTA, outside every loop. No other line of the sources changes.
* `tests/experimental/test_cake_kimi_k3_attn_res.py` gains
`test_native_programs_drain_tmem_loads_before_the_dealloc`. For every
program a native route takes, it checks that a `tcgen05.wait::ld` sits
between the program's last `tcgen05.ld` and the barrier before its
`tcgen05.dealloc`. The test fails on `main` for both programs and passes
with this change. Once #6740 lands, the same check can cover the
persistent programs too.

## 🧪 Tests

- `pytest tests/experimental/test_cake_kimi_k3_attn_res.py` on a B300
(SM103): 445 passed, 2 skipped.
- Both modules build for their registered targets (`sm_100a` and
`sm_103a`).
- **SASS (`cuobjdump`), both programs, both targets.** The instruction
count is unchanged. One scoreboard-wait `NOP` is inserted before the
cleanup `BAR.SYNC 0x0, 0x120`, and one tail padding `NOP` goes. The only
other differences are branch targets shifted by 0x10.
- **Correctness.** The old and new programs both match the FP32
reference on their routed cells: M = 256 with K = 8 for native_k8, and M
= 256 with K = 4 for native_m128.
- **Timing on B300 (152 SMs).** Timed with CUPTI and cold L2, back to
back and cooled, in old/new/control interleaved order, with 100 ms
warmup and a 1 s window. The control is a second build of the old
sources. All sides are bound to the same input tensors.

| program | GPU | old hot / cooled (µs) | new hot / cooled (µs) |
new/old | control/old |
  |---|---|---|---|---|---|
| `99f148a06e530e457f4a` (native_k8, M 256 K 8) | B300 #1 | 12.22 /
12.22 | 12.19 / 12.22 | 0.9974 / 1.0000 | 0.9974 / 0.9974 |
| `709f669fe8647d61aaf0` (native_m128, M 256 K 4) | B300 #1 | 9.25 /
9.25 | 9.25 / 9.26 | 1.0000 / 1.0017 | 1.0000 / 1.0000 |
| `99f148a06e530e457f4a` (native_k8, M 256 K 8) | B300 #2 | 12.16 /
12.16 | 12.13 / 12.16 | 0.9974 / 1.0000 | 0.9974 / 1.0000 |
| `709f669fe8647d61aaf0` (native_m128, M 256 K 4) | B300 #2 | 9.18 /
9.22 | 9.20 / 9.22 | 1.0017 / 1.0000 | 1.0035 / 1.0000 |

Every difference is within one 32 ns timer tick, the same spread as the
old-vs-control comparison.

## 🔍 Related

- #6740 (the same fix for the 39 persistent programs).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability in the experimental attention operation by
ensuring pending work is complete before resources are cleaned up. This
helps prevent issues that could occur when cleanup began while hardware
operations were still in progress.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [25e246a](https://github.com/flashinfer-ai/flashinfer/commit/25e246aaa60d33154340f810d1951e9c8e8cd799)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T08:05:45Z
- **提交信息**: fix(cake_selective_state_update): sync each consumer warp before its elected stage release (#6806)

Cake's `selective_state_update` backend ships thirteen programs: BF16
and FP32 state, single-token, MTP and checkpoint-cache forms, and
headdim 128 and 64. This PR changes seven of them: the five BF16
single-token programs, the headdim-64 paired-row program and the
horizontal MTP program. In each, every consumer warp now synchronizes
before its elected lane releases a shared-memory state stage, and
latency is unchanged against the previous Cake version.

Latency in µs, back to back / cooled (mean of the per-allocation medians
over 8 input allocations, two alternating runs per side), on NVIDIA
GB300 (sm_103a) with CUDA 13.3:

| program | batch | heads | groups | head dim | state dim | tokens |
before | after | speedup |
|---|---|---|---|---|---|---|---|---|---|
| BF16 single-token, direct | 32 | 16 | 16 | 128 | 128 | 1 | 10.68 /
10.69 | 10.70 / 10.69 | 0.999x / 0.999x |
| BF16 single-token, ratio 8 | 64 | 64 | 8 | 128 | 128 | 1 | 50.74 /
50.71 | 50.71 / 50.68 | 1.001x / 1.001x |
| BF16 single-token, ratio 8 saturated | 128 | 64 | 8 | 128 | 128 | 1 |
86.53 / 86.61 | 86.54 / 86.54 | 1.000x / 1.001x |
| BF16 single-token, ratio 16 | 32 | 128 | 8 | 128 | 128 | 1 | 50.70 /
50.71 | 50.67 / 50.64 | 1.001x / 1.001x |
| BF16 single-token, persistent | 257 | 128 | 8 | 128 | 128 | 1 | 337.11
/ 336.90 | 337.05 / 336.97 | 1.000x / 1.000x |
| headdim-64 paired rows | 64 | 128 | 8 | 64 | 128 | 1 | 43.63 / 43.65 |
43.65 / 43.66 | 1.000x / 1.000x |
| headdim-64 paired rows | 320 | 128 | 8 | 64 | 128 | 1 | 198.84 /
198.88 | 198.84 / 198.94 | 1.000x / 1.000x |
| horizontal MTP | 32 | 64 | 8 | 64 | 128 | 6 | 40.03 / 40.03 | 40.03 /
40.02 | 1.000x / 1.000x |

The other Cake programs of this operator are unchanged: FP32-state
single-token, MTP short, checkpoint cache, dynamic checkpoint, and the
headdim-64 row-owner programs. The family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during state updates to help ensure updated
values are ready before processing continues.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b815220](https://github.com/flashinfer-ai/flashinfer/commit/b815220c91936cd7e11a0b91fddb3307a4317a26)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T08:05:32Z
- **提交信息**: fix(cake_deepgemm_mixed_gemm): wait for the peer CTA's last stage releases before the load warp exits (#6819)

**Race.** These are 2-CTA (`cta_group::2`, cluster of 2) tcgen05 GEMMs.
The leader CTA's MMA warp releases each stage of the TMA load ring with
`tcgen05.commit.cta_group::2.mbarrier::arrive::one.shared::cluster.multicast::cluster`
(mask `0b11`) on the stage-release mbarrier of both CTAs. The peer CTA's
load warp waits that barrier only before a refill, so after its last
refill it can leave the tile loop and the CTA can exit while the
arrive-ons for the last ring-depth stages are still in flight toward its
shared memory; an async arrive on the shared memory of a CTA that has
exited is undefined (PTX ISA §2.2.2). PTX gives no ordering between two
`tcgen05.commit` operations (§9.7.18.6), so the later accumulator-ready
commit that the epilogue waits for does not cover the earlier stage
releases, and the teardown cluster barrier does not either.

**Change.** After its tile loop the load warp (the same lanes that wait
in the main loop) now waits the stage-release barrier for the last
ring-depth stages, advancing its stage index and phase exactly as the
main loop does (a producer tail, as in CUTLASS's `producer_tail`).
Stages that were never filled pass immediately, so short problems are
unaffected.

**Affected programs.** All nine shipped programs of the mixed FP8 x FP4
GEMM (`csrc/experimental/deepgemm_mixed_gemm/*_kernel.cu`: the normal
and swap-AB runtime-shape schedules and the split-K route, ring depths 5
to 12) release the ring with the multicast commit and had no tail.

**Tests.** `tests/experimental/test_mixed_fp8_fp4_gemm_generated.py`: 34
passed on GB300 (sm_103a); the sm_100a builds compile.

**Timing** (NVIDIA GB300, sm_103a, CUDA 13.3; kernel time per call,
median over 3 ABBA rounds in one process, cold L2; "cooled" adds an idle
delay before every call so the GPU is not power-throttled):

| M | N | K | program | before (us) | after (us) | change | before,
cooled (us) | after, cooled (us) | change, cooled |
|---|---|---|---|---|---|---|---|---|---|
| 16 | 4608 | 5120 | swap-AB, BM16 BN128, 12 stages | 8.43 | 8.42 |
-0.18% | 8.43 | 8.42 | -0.18% |
| 512 | 5120 | 2304 | normal, BM128 BN160, 7 stages | 8.16 | 8.04 |
-1.41% | 8.16 | 8.04 | -1.41% |
| 4096 | 7168 | 4096 | normal, BM128 BN256, 5 stages | 62.50 | 62.56 |
+0.10% | 62.53 | 62.71 | +0.29% |

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved completion handling for experimental mixed-precision matrix
multiplication workloads.
* Ensured pending operations finish cleanly before processing concludes,
reducing the risk of incomplete work or synchronization issues.
* Applied the fix across multiple supported kernel configurations and
pipeline variants.
* **Performance & Reliability**
* Improved consistency and robustness of experimental GPU computations,
particularly for workloads using staged execution.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ad76353](https://github.com/flashinfer-ai/flashinfer/commit/ad76353e734450d563c57c598beb753fcd7e3ea3)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T08:05:26Z
- **提交信息**: fix(cake_kimi_k3_latent_moe): wait for the peer CTA's last stage releases before the tail GEMM load warp exits (#6821)

**Race.** These are 2-CTA (`cta_group::2`, cluster of 2) tcgen05 GEMMs.
The leader CTA's MMA warp releases each stage of the TMA load ring with
`tcgen05.commit.cta_group::2.mbarrier::arrive::one.shared::cluster.multicast::cluster`
(mask `0b11`) on the stage-release mbarrier of both CTAs. The peer CTA's
load warp waits that barrier only before a refill, so after its last
refill it can leave the tile loop and the CTA can exit while the
arrive-ons for the last ring-depth stages are still in flight toward its
shared memory; an async arrive on the shared memory of a CTA that has
exited is undefined (PTX ISA §2.2.2). PTX gives no ordering between two
`tcgen05.commit` operations (§9.7.18.6), so the later accumulator-ready
commit that the epilogue waits for does not cover the earlier stage
releases, and the teardown cluster barrier does not either.

**Change.** After its tile loop the load warp (the same lanes that wait
in the main loop) now waits the stage-release barrier for the last
ring-depth stages, advancing its stage index and phase exactly as the
main loop does (a producer tail, as in CUTLASS's `producer_tail`).
Stages that were never filled pass immediately, so short problems are
unaffected.

**Affected programs.** The seven persistent 2-CTA prefill tail GEMM
programs (`tail_gemm:*` keys;
`flashinfer/experimental/kimi_k3_latent_moe/csrc/cake_kimi_k3_latent_moe/`
`5672f574…`, `704a177c…`, `715f9200…`, `85546046…`, `8a3e1501…`,
`a3737025…`, `f2749aaa…`; ring depths 6, 7 and 9). The tail is fully
unrolled, so its waits issue back to back. Not affected: the front GEMM,
decode and RMSNorm programs (no multicast stage release across a CTA
pair).

**Tests.** `tests/experimental/test_cake_kimi_k3_latent_moe.py`: 53
passed on GB300 (sm_103a); the sm_100a builds compile.

**Timing** (NVIDIA GB300, sm_103a, CUDA 13.3; one call of the prepared
tail runner, median over ABBA rounds in one process, cold L2; "cooled"
adds an idle delay before every call so the GPU is not power-throttled;
the cooled TP8 row is a ~30 us kernel whose per-round medians spread
over 27-37 us, so its change is within noise):

| shape | before (us) | after (us) | change | before, cooled (us) |
after, cooled (us) | change, cooled |
|---|---|---|---|---|---|---|
| prefill tail (RMSNorm + 2-CTA GEMM), TP8, T = 1024 (8 rounds) | 34.56
| 34.21 | -1.01% | 31.53 | 31.92 | +1.22% |
| prefill tail (RMSNorm + 2-CTA GEMM), TP1, T = 4096 (3 rounds) | 313.32
| 308.81 | -1.44% | 305.11 | 305.68 | +0.19% |

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved synchronization across Kimi K3 latent MoE execution paths by
ensuring outstanding pipeline operations are completed before processing
finishes.
- Added consistent handling for pipeline stage progression and
wraparound, reducing the risk of incomplete or out-of-order work.
- Applied the synchronization updates across supported execution
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [100282b](https://github.com/flashinfer-ai/flashinfer/commit/100282bc9176a3697ff6d9c7840a327a421aba78)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T08:05:12Z
- **提交信息**: fix(cake_minimax_h3): wait for the peer CTA's last stage releases before the FC1 / MLP / out-proj GEMM load warps exit (#6822)

**Race.** These are 2-CTA (`cta_group::2`, cluster of 2) tcgen05 GEMMs.
The leader CTA's MMA warp releases each stage of the TMA load ring with
`tcgen05.commit.cta_group::2.mbarrier::arrive::one.shared::cluster.multicast::cluster`
(mask `0b11`) on the stage-release mbarrier of both CTAs. The peer CTA's
load warp waits that barrier only before a refill, so after its last
refill it can leave the tile loop and the CTA can exit while the
arrive-ons for the last ring-depth stages are still in flight toward its
shared memory; an async arrive on the shared memory of a CTA that has
exited is undefined (PTX ISA §2.2.2). PTX gives no ordering between two
`tcgen05.commit` operations (§9.7.18.6), so the later accumulator-ready
commit that the epilogue waits for does not cover the earlier stage
releases, and the teardown cluster barrier does not either.

**Change.** After its tile loop the load warp (the same lanes that wait
in the main loop) now waits the stage-release barrier for the last
ring-depth stages, advancing its stage index and phase exactly as the
main loop does (a producer tail, as in CUTLASS's `producer_tail`).
Stages that were never filled pass immediately, so short problems are
unaffected.

**Affected programs.** Every 2-CTA GEMM kernel of the MiniMax-H3 FC1 +
SwiGLU, full-MLP and out-proj operators (twelve kernels, sm_100a and
sm_103a): `kernel_minimax_h3_fc1_swiglu_{bf16,e4m3,e2m1}` in
`csrc/cake_minimax_h3_fc1_swiglu_sm10x.cu`,
`kernel_minimax_h3_mlp_{fc1,fc2}_{bf16,e4m3,e2m1}` in
`csrc/cake_minimax_h3_mlp_sm10x.cu` and
`kernel_minimax_h3_out_proj_{bf16,e4m3,e2m1}` in
`csrc/cake_minimax_h3_out_proj_sm10x.cu` (ring depths 3 to 7). Not
affected: the norm / AdaLN / activation-quantization kernels of the same
files (no 2-CTA tcgen05 ring).

**Tests.** `tests/diffusion_ops/test_minimax_h3_mlp.py`,
`test_minimax_h3_fc1_swiglu.py` and `test_minimax_h3_out_proj.py`: 110
passed on GB300 (sm_103a); the sm_100a builds compile.

**Timing** (NVIDIA GB300, sm_103a, CUDA 13.3; one call of the operator
at M = 4824, median over 4 (MLP BF16 / MXFP8) or 3 ABBA rounds in one
process, cold L2; "cooled" adds an idle delay before every call so the
GPU is not power-throttled):

| operator | before (us) | after (us) | change | before, cooled (us) |
after, cooled (us) | change, cooled |
|---|---|---|---|---|---|---|
| MLP block, BF16 | 1286.92 | 1286.32 | -0.05% | 1151.20 | 1154.59 |
+0.29% |
| MLP block, MXFP8 | 708.48 | 698.07 | -1.47% | 672.20 | 671.96 | -0.04%
|
| MLP block, NVFP4 | 334.89 | 334.63 | -0.08% | 334.88 | 335.20 | +0.10%
|
| FC1 + SwiGLU, BF16 | 804.75 | 777.79 | -3.35% | 736.05 | 736.19 |
+0.02% |
| FC1 + SwiGLU, MXFP8 | 407.56 | 393.68 | -3.41% | 389.96 | 389.68 |
-0.07% |
| FC1 + SwiGLU, NVFP4 | 209.50 | 209.71 | +0.10% | 209.50 | 209.77 |
+0.13% |
| out-proj, BF16, P = 8 | 216.80 | 216.51 | -0.13% | 216.41 | 216.06 |
-0.16% |
| out-proj, MXFP8, P = 8 | 141.63 | 141.66 | +0.02% | 141.43 | 141.56 |
+0.09% |
| out-proj, NVFP4, P = 8 | 82.30 | 82.32 | +0.02% | 82.34 | 82.37 |
+0.04% |

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved completion reliability for BF16, MXFP8, and NVFP4 workloads.
- Ensured pending GPU operations finish cleanly when scheduled work
completes or is cancelled.
- Reduced the risk of synchronization issues during final processing
across supported model operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [09f848a](https://github.com/flashinfer-ai/flashinfer/commit/09f848a364cf66e84b30a5ae90a963c4b308d0ea)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T08:04:59Z
- **提交信息**: fix(cake_mla): address each warp's own TMEM lane quarter in the FP8 page-32 Blackwell MLA decode (#6828)

**Issue.** The FP8 page-32 decode program of the Cake Blackwell MLA
backend
(`csrc/cake_trtllm_mla_blackwell/cake_trtllm_mla_blackwell_79e49e216298d59fce33_kernel.cu`,
route `mla_fp8_p32_qk_l2`, sm_100a and sm_103a) runs its softmax and
correction roles on all four warps of a warpgroup. A `tcgen05.ld` /
`tcgen05.st` from warp *w* of a warpgroup may access only TMEM lanes
32·(w mod 4) … 32·(w mod 4)+31, and the lane comes from bits 31:16 of
the address (PTX ISA, tcgen05 memory-access restrictions). The softmax
warps' `.16x256b` score loads and statistics stores, and the correction
warps' statistics and output loads and stores, addressed TMEM from the
allocation base (lane 0) in every warp, so warps 1–3 issued
out-of-quarter accesses. GB300 serves such an access from the warp's own
quarter, so results were correct on current hardware, but the code
relied on behaviour that PTX leaves undefined.

**Change.** Every one of these accesses now adds the warp's lane base:
`(tid & 96) << 16` in the two softmax roles, and the row offset the
correction role already computes (`tmem_row_c`). No other program of the
family uses `.16x256b` accesses.

**Tests.** The Cake cases of `tests/attention/test_trtllm_gen_mla.py`
(`-k "trtllm_mla_blackwell or cake"`): 34 passed on GB300 (sm_103a). On
the page-32 route (batch 1, q_len 2, KV 1024; four seeds) and on the FP8
tail route, the output is bitwise identical to the previous build and
within 0.0023 of an FP32 torch reference. The sm_100a builds compile.

**Timing** (NVIDIA GB300, sm_103a, CUDA 13.3; one decode call, median
over ABBA rounds in one process, cold L2; "cooled" adds an idle delay
before every call so the GPU is not power-throttled):

| shape | before (us) | after (us) | change | before, cooled (us) |
after, cooled (us) | change, cooled |
|---|---|---|---|---|---|---|
| FP8 KV, page 32, batch 1, q_len 2, KV 1024 (6 rounds) | 9.60 | 9.60 |
+0.00% | 9.60 | 9.62 | +0.16% |

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved softmax and correction-stage processing on Blackwell hardware
by ensuring score, statistics, and output data use the correct per-warp
memory locations.
* Preserved existing pipeline and reduction behavior while improving
kernel reliability and result consistency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [63555f9](https://github.com/flashinfer-ai/flashinfer/commit/63555f9530f3e62b2a1185b040893a0adcf95288)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-20T07:44:44Z
- **提交信息**: perf(moe_ep): fuse Rubin MegaMoE forward preparation (#6398)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fuse NVFP4 input quantization and route staging for Rubin MegaMoE, and
use a fused checker for expert-ID bounds, duplicate routes and finite
scores. Standard MegaMoE and GenPhase share these preparation paths.

The routing checker reuses compiled code across token counts and keeps
separate assertion buffers for each captured shape. Unsupported layouts
and dtypes retain the Torch path.

## 🔍 Related Issues

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

The staging-helper changes are in a separate commit so they can be
dropped when the kernel refresh includes them.

### [25f5bbe](https://github.com/flashinfer-ai/flashinfer/commit/25f5bbe98c439127ad65d795a3c439b74440314c)

- **作者**: eigen
- **时间**: 2026-10-20T07:20:13Z
- **提交信息**: perf(cake_comm): QkvNormRopeExchangeOverlap SM107 four-rank plans use the bulk-row-store build (#6831)

`QkvNormRopeExchangeOverlap` combines the QKV projection, per-head QK
RMSNorm and RoPE with the Ulysses QKV all-to-all exchange in one kernel
(BF16 activations and weights, fp32 accumulation). Its producer kernel,
which writes the exchanged rows, has four builds: the shipped build,
`ow256` (operand load width 256), `bulk_ow256` (bulk row store plus
operand load width 256) and `bulk` (bulk row store alone, at the shipped
operand load width 128). Each build exists as bn128 / bn256 and single /
two-CTA pair programs, plus two fold programs per pair build. The
default build depends on architecture and world size:

- `ow256` on SM100 (B200) four-rank and on SM103 (B300) four- and
eight-rank
- `bulk_ow256` on SM100 eight-rank
- the shipped build on SM90 (H100) at every world size and on SM107
(Rubin) two- and four-rank

This PR makes the bulk-row-store build (`bulk`) the default for SM107
four-rank plans and adds three SM107 producer programs (a bn256 pair
program and two folds). SM107 two-rank plans keep the shipped build,
SM90 / SM100 / SM103 programs and defaults are unchanged, and
`FLASHINFER_QKV_EXCHANGE_PRODUCER_VARIANT` still selects any build
explicitly. The bulk-row-store build is faster on 23 of the 24 four-rank
shapes below (2.1 % to 7.9 % lower latency, median 3.7 %) and 0.35 %
slower on one (H 6144, S 32768).

Four-rank kernel latency on 4 × NVIDIA R200 (Rubin, `sm_107a`), CUDA
13.5; values are medians. Rows per rank M = S / 4; speedup = previous /
new.

| H | S | previous default build (ms) | bulk-row-store build (ms) |
speedup |
|---:|---:|---:|---:|---|
| 3072 | 4096 | 0.057841 | 0.054689 | 1.058 |
| 3072 | 8192 | 0.088161 | 0.084609 | 1.042 |
| 3072 | 16384 | 0.141138 | 0.138114 | 1.022 |
| 3072 | 32768 | 0.252067 | 0.240196 | 1.049 |
| 3072 | 65536 | 0.482582 | 0.465990 | 1.036 |
| 3072 | 131072 | 0.949611 | 0.916748 | 1.036 |
| 4096 | 4096 | 0.072913 | 0.069697 | 1.046 |
| 4096 | 8192 | 0.113041 | 0.106881 | 1.058 |
| 4096 | 16384 | 0.194291 | 0.184051 | 1.056 |
| 4096 | 32768 | 0.348356 | 0.334085 | 1.043 |
| 4096 | 65536 | 0.672712 | 0.633528 | 1.062 |
| 4096 | 131072 | 1.297535 | 1.231873 | 1.053 |
| 6144 | 4096 | 0.098273 | 0.090545 | 1.085 |
| 6144 | 8192 | 0.158706 | 0.153858 | 1.032 |
| 6144 | 16384 | 0.281940 | 0.275492 | 1.023 |
| 6144 | 32768 | 0.547207 | 0.549111 | 0.997 |
| 6144 | 65536 | 1.107006 | 1.074479 | 1.030 |
| 6144 | 131072 | 2.411968 | 2.297536 | 1.050 |
| 8192 | 4096 | 0.140578 | 0.135394 | 1.038 |
| 8192 | 8192 | 0.252132 | 0.246500 | 1.023 |
| 8192 | 16384 | 0.474438 | 0.457703 | 1.037 |
| 8192 | 32768 | 0.951101 | 0.924990 | 1.028 |
| 8192 | 65536 | 1.971820 | 1.929020 | 1.022 |
| 8192 | 131072 | 4.140500 | 4.015470 | 1.031 |

The family ships BF16 producer programs for `sm_90a` (H100 / H200),
`sm_100a` (B200), `sm_103a` (B300) and `sm_107a` (R200) with two-, four-
and eight-rank plans (eight-rank not on SM107), and the `ow256`,
`bulk_ow256` and `bulk` builds stay selectable on every architecture
that compiles them.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for optimized QKV normalization, rotary embedding, and
exchange execution on additional GPU configurations.
* Added the `bulk` producer variant for supported SM107 workloads,
including automatic selection for four-rank groups.
* Added optimized clustered processing and peer-exchange execution
paths.

* **Documentation**
* Updated producer variant guidance, build recommendations, scaling
settings, and alignment requirements.

* **Tests**
* Expanded coverage for the new producer variant, default selection,
folded variants, and alignment validation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [28bf167](https://github.com/flashinfer-ai/flashinfer/commit/28bf16712268f74a07beeef87dd2f57072e544e6)

- **作者**: eigen
- **时间**: 2026-10-20T07:08:46Z
- **提交信息**: deslop(cake_kimi_k3_vision_tower): one launcher for the 76 host bindings, fold SM100 attention copies, compact registry (#6830)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

The Cake-generated Kimi-K3 vision tower package lives in
`flashinfer/experimental/kimi_k3_vision_tower/`. It serves
`flashinfer.kimi_k3_vision.{kimi_k3_vision_tower,
prepare_kimi_k3_vision_tower}` with `backend="cake"` on SM100 and SM103,
and it is JIT only with no AOT entry. The exported package has three
kinds of duplication: five attention forms are exported twice (once per
architecture), each program has its own host binding, and the registry
is a 1,664-line literal. This PR has three commits. The first folds the
SM100 attention copies into their SM103 twins. The second compacts the
registry to one row per program. The third replaces the 76 host bindings
with one shared launcher.

Against upstream main `f325b32956ae70bcbf5d5e6da468bc67d7ac797a`
(2026-10-19), head ba0fe4609d8ab242302611e7955eed0deaa34334 changes 97
files (+2,247 / -47,414) and touches only the package and its test file.
Apart from the five merged attention sources, every kernel source and
both family headers (`host_common.cuh`, `device_common.cuh`) are
byte-identical to the base. Every kept program keeps its kernel symbol
(`kernel_cake_kimi_k3_vision_tower_<digest>`) and its host-shim
namespace (`cake_host_shim_<16 hex>`). Every library still exports its
own kernel symbol, `<own shim>::Run` and `__tvm_ffi_run`. The merged
attention sources, the compact registry, the launcher and its header are
exporter output that was folded by hand here until the exporter supports
it. A statement saying so appears once in `cake_jit.py`, the launcher,
the header, each merged source and both READMEs. `cake_backend.py` and
the benchmark are untouched.

Behaviour changes (all deliberate):
- **SM100 attention programs removed.** The 5 SM100-only attention
programs (`b217c889…`, `b7eb9c98…`, `d3641cd2…`, `f404bc44…`,
`2b1f73eb…`) no longer exist as registry names. On sm_100a, the kernel
keys `ring3`, `ring3:split`, `ring3:wide`, `tiles2` and `tiles2:wide`
now resolve to the SM103 twins (`baca276f…`, `6a51ed93…`, `23237a8f…`,
`05528121…`, `153c43aa…`). The SM100 library for each of these forms is
a new JIT module that uses the twin's kernel symbol and host-shim
namespace. The two `#error` guards that refused sm_100 in the SM103
copies are removed.
- **Registry records.** `MODULES` is built at import from one
`_PROGRAMS` row per program. `KERNELS` is a shared assignment table plus
the per-architecture entries. Records no longer carry `closure_sha256`,
so external code that reads that field will break.
- **JIT library names.** The salt is now a content digest computed when
the spec is created: SHA-256 over the source bytes in order, the
architecture and the program's compile flags. An edited source can never
reuse a cached library, and every program builds into a fresh library
once. Spec names change again in commit 3 because the digest also covers
the launcher and the flags.
- **`compile_flags`.** Callers that read `MODULES[...]["compile_flags"]`
will now see the per-program launch definitions (`CAKE_*`). No kernel
source reads them.
- **Backtraces.** When an argument check fails, the backtrace reports
the launcher's file and line instead of the program's own binding file.
The message texts are byte-identical.
- **Tests.** 4 new CPU tests bring the ids from 40 to 44. No GPU ids
change. The test file grows from 1,424 to 1,525 lines and nothing is
removed.
- **Docs.** The package README (145 -> 164 lines) gains a launcher
paragraph, the hand-fold statement and the corrected count of seven
coverage rows. `csrc/README.md` (12 -> 20 lines) describes the flat
layout. `csrc/` goes from 166 entries to 82 (76 kernel sources, the
launcher, the TMA-encode header, the two family headers, `README.md`,
`.clang-format`), and `cake_jit.py` from 1,664 to 674 lines.

## Changes

### Commit 1 (3f8dbe4a3) - kimi_k3_vision_tower: fold 5 SM100 attention
programs into SM103 twins (18 files, +834 / -9,587)

Both architectures serve the same five attention forms (`ring3`,
`ring3:split`, `ring3:wide`, `tiles2`, `tiles2:wide`), and each form was
exported twice, as an SM100 program and an SM103 program. The two
sources in each pair differ in 21-22 hunks: the score drain, the exp2
lane pattern, the tiles2 rescale threshold, and the temporaries that the
generator renumbers after them. The two bindings in each pair were
identical apart from the program hash and the host-shim id.

- The SM100 copies and their bindings (9,461 lines) are deleted.
- Each SM103 source now carries the SM100 text in `#if __CUDA_ARCH__ ==
1000` arms, the same pattern the GEMM kernels already use. The two
`#error` guards that refused sm_100 are removed.
- The twins' records now list both architectures, and the SM100 kernel
keys point at the twins.

This is the mechanical interim for issue step 3. The issue makes that
step depend on exporter support for arch-conditional attention emission.
Here the merge is done by hand and disclosed in each merged source.

Proof: line-identical renders. When each merged source is rendered for
`__CUDA_ARCH__` 1000, it reproduces the deleted SM100 source with the
kernel symbol mapped. When rendered for 1030, it reproduces the previous
SM103 source minus the guards. That is 5 pairs and 10 comparisons, with
0 differing lines. The SASS gate adds two kinds of rows, and their
results are under Validation along with the test file on both GPUs:
- Fold rows on sm_100a compare the deleted source at the base with the
merged source at the head. The kernel symbol is mapped because the SM100
build of a merged source now carries the twin's symbol.
- Changed-text rows on sm_103a compare the previous source with the
merged source.

### Commit 2 (e6ab9f5f0) - kimi_k3_vision_tower: compact the program
registry to rows (3 files, +324 / -1,319)

After the fold, the `MODULES` literal held 76 records in 1,138 lines.
Each record repeated four fields that can be derived: `role`
(`"kernel"`), `ffi_entry` (`"run"`) and the two source paths, which
follow from the program name. Each record also held a per-architecture
`closure_sha256`, which was read only as the salt of the JIT library
name. `KERNELS` listed twice the 72 assignments that both architectures
share.

- The literal becomes one `_PROGRAMS` row per program: `(arches,
compile_flags, arg_plan)`, keyed by the program digest. A `_module`
builder expands the rows into `MODULES` at import, and `_sources`
derives the translation units.
- `KERNELS` becomes the shared table plus the 4 entries that only SM103
has. It is expanded per architecture in sorted key order.
- The library-name salt becomes the content digest described in the
Summary.
- The package README's coverage-row count becomes seven. This is the
count fix from issue step 7.

`ARG_PLANS`, every helper, every compile flag, the kernel symbols and
the namespaces are unchanged by this commit. `cake_jit.py` goes from
1,603 to 552 lines at this commit. This covers issue step 2. The content
digest also answers the step's `closure_sha256` caveat: a stale library
cannot be loaded for edited sources.

Proof: when the compact form is re-expanded, it matches the literal
record for record (76 records, 72 + 76 keys, 0 differences, same key
order). The real sources produce 148 distinct library names. 2 new CPU
tests check two things: every row expands to the same record the literal
held, and the digest is a pure function of its inputs. The comparison of
the imported registry on the CPU route and the per-architecture load-all
are under Validation.

### Commit 3 (ba0fe4609) - kimi_k3_vision_tower: one shared launcher
replaces the 76 host bindings (82 files, +1,157 / -36,576)

The 76 exported host bindings totalled 36,528 lines. They came in three
structural shapes and held 420 copies of the TMA-descriptor encoder.
They fell into 17 duplicate groups that held 26,406 redundant lines. The
only differences between them were:
- the kernel symbol and the host-shim namespace
- the argument plan
- dynamic shared memory, block and cluster extents
- the B TMA box extent and the rank of the A / A2 descriptors

What this commit changes:
- The bindings become one launcher translation unit,
`csrc/cake_kimi_k3_vision_tower_launcher.cu` (667 lines), plus a
parameterised TMA-encode header,
`csrc/cake_kimi_k3_vision_tower_tma_encode.cuh` (256 lines).
- Per-program compile definitions select the text:
`CAKE_PROGRAM_KERNEL`, `CAKE_PROGRAM_SHIM`, `CAKE_PLAN_<PLAN>`,
`CAKE_DYNAMIC_SMEM`, `CAKE_BLOCK_X` and `CAKE_CLUSTER_X`, plus
`CAKE_B_BOX_N` and `CAKE_A_TMA_RANK` for the GEMM plans. The three small
programs (attention_merge, merge, rmsnorm_apply) each have their own
plan arm in the launcher.
- The registry gains one `_LAUNCH` row per program and
`launch_definitions(name)`, which builds the definitions from that row.
The definitions are appended to the program's `compile_flags`. They also
reach the kernel source's command line, but no kernel source names any
`CAKE_` macro other than `CAKE_INF`, so device code cannot see them.
- Spec names change once more because the digest covers the launcher and
the flags.
- The package README gains the launcher paragraph, and `csrc/README.md`
describes the flat layout: kernel sources, one launcher and one header.

Device code is untouched. 71 kernel sources stay byte-identical to the
base, and this commit does not change the 5 merged ones. The device
guard and the explicit `cudaSetDevice` stay as exported. The issue asks
for the guard's behaviour in the tvm-ffi header to be confirmed before
the call is dropped, and that confirmation is not done here.

This covers issue step 1 except for two parts:
- The `cudaSetDevice` drop, which waits on the confirmation above.
- The cross-family hoist of `host_common.cuh`. That header is
byte-identical in 14 Cake families, so moving it to a shared header at
the `csrc/` level is a cross-family change.

Proof: a text-level preprocessor model renders the launcher with each
program's definitions. The renders are line-identical to the exported
bindings for 76 / 76 programs, with 0 differing lines, and 8 / 8
negative controls detect a changed value. 2 new CPU tests check two
things: each program's definitions select its own kernel symbol and a
distinct host-shim namespace, and every macro the registry defines is
read by the launcher or the header. The host gate, the SASS identity
rows, load-all and the test file on both GPUs are under Validation.

## Validation

- **Device SASS gate.** There is one row per (program, architecture).
The candidate is compared against the base under one toolchain per GPU,
after masking instruction addresses and encodings. Each build unit's
disassembly must contain exactly one kernel function, and that function
must be the program's own symbol.
  - sm_100a on B200 (CUDA 13.3), 72 rows:
- 67 identity rows: the program's own kernel source, byte-identical at
base and head, built with the base flags against the head flags with the
launch definitions added.
- 5 fold rows: the deleted SM100 source at the base against the merged
twin source at the head, with the kernel symbol mapped.
- Result: 72 / 72 rows identical (67 identity + 5 fold with the kernel
symbol mapped); every build unit's disassembly holds exactly one kernel
function, the program's own symbol
  - sm_103a on GB300 (CUDA 13.3), 76 rows:
    - 71 identity rows.
- 5 changed-text rows: the previous SM103 source against the merged
source.
- Result: 76 / 76 rows identical (71 identity + 5 changed-text); every
build unit's disassembly holds exactly one kernel function, the
program's own symbol
- **Host gate.** There is one row per (program, architecture). Each row
compares the program's exported binding at the base, built with its base
compile flags, against the shared launcher at the head, built with the
program's head compile flags. Both sides compile to objects with no
device code. A row passes when all three of these hold:
- The preprocessed texts are identical after normalising only line
markers, pragma lines, blank lines, adjacent string-literal pieces and
the backtrace file/line arguments, with the absolute checkout-root
prefix of `__FILE__` paths masked because the two sides are compiled
from two checkouts. Nothing else inside a string literal is normalised.
- The two objects define the same set of global symbols (`<shim>::Run`,
`__tvm_ffi_run`).
  - No foreign host-shim namespace appears.

  Results:
- sm_100a on B200, 72 rows: 72 / 72 rows pass: both sides compile with
no device code, preprocessed texts identical after the normalisation
(every row needs the line-marker, blank-line, adjacent-literal and
backtrace classes; no row needs the pragma class), identical global
symbol sets on all 72
- sm_103a on GB300, 76 rows: 76 / 76 rows pass: both sides compile with
no device code, preprocessed texts identical after the normalisation
(every row needs the line-marker, blank-line, adjacent-literal and
backtrace classes; no row needs the pragma class), identical global
symbol sets on all 76
- **Load-all.** Every program of the architecture is built through the
real loader in one process, with a fresh JIT workspace. Each build must
meet four conditions:
  - `run` is resolvable.
  - Each program gets its own distinct library.
  - The program's own kernel symbol is in its disassembly.
  - The program's own `<shim>::Run` is in its exports.

That is 72 libraries on B200 and 76 on GB300: B200: 72 libraries built
and loaded in one process, 72 distinct kernel symbols, 72 distinct
host-shim namespaces, `run` resolvable on every module (148
multiprocessors); GB300: 76 libraries built and loaded in one process,
76 distinct kernel symbols, 76 distinct host-shim namespaces, `run`
resolvable on every module (the node reports 152 multiprocessors;
`DEFAULT_SM_COUNT` stays 148)
- **GPU tests.** These run
`tests/experimental/test_cake_kimi_k3_vision_tower.py` with a fresh JIT
workspace per tree. The file is invoked explicitly because it is outside
the default collection roots. The GPU tests run only on a CUDA device of
compute capability 10.0 or 10.3 whose architecture has a complete
registry.
- B200: candidate (expected 44 passed, 0 skipped) and base f325b3295
(expected 40 passed, 0 skipped): candidate 44 passed, 0 skipped; base 40
passed, 0 skipped (fresh JIT workspace per tree)
- GB300: the same (expected 44 / 0 and 40 / 0): candidate 44 passed, 0
skipped; base 40 passed, 0 skipped (fresh JIT workspace per tree)
- **CPU checks** on the head tree (one route):
  - ruff, ruff format and py_compile on the 2 changed Python files.
- The repository's pre-commit hooks: ruff, mypy on the registry, and the
text hooks on the launcher, the header and the READMEs. clang-format is
a no-op by design because the package's `csrc/.clang-format` disables
formatting.
- Stale-reference greps for the 86 deleted file names and the 5 deleted
program digests: 0 hits repo-wide.
  - Collected ids: base 40, candidate 44.
- CPU-only pytest with CUDA hidden: candidate 34 passed / 10 skipped,
base 30 / 10.
- The imported registry view compared with the text expansion for all 76
programs (148 distinct spec names).
  - The benchmark's `--help`.
- The text render checks: attention render, registry expansion and
launcher render.

Result: all pass on the head: ruff + format + py_compile clean; the
repository's pre-commit ruff-format and mypy hooks on the 2 Python files
and its text hooks on the launcher, header and READMEs pass (its
ruff-check hook targets other paths and skips these files; clang-format
is a no-op by design); stale-reference greps 0 hits; collected ids base
40 / candidate 44 (+4 CPU tests, nothing removed); CPU-only pytest
candidate 34 passed / 10 skipped, base 30 passed / 10 skipped; the
imported registry equals the text expansion for all 76 programs (148
distinct spec names); the benchmark's `--help` runs; attention render
check 5 pairs / 10 comparisons / 0 differing lines; registry check 76
records, 0 differences; launcher render check 76 / 76 programs, 0
differing lines, 8 / 8 negative controls; the gate tables regenerate
identically (148 + 148 rows)
- **No GPU benchmark** is run by this PR. The device code is unchanged
(SASS identity), and the host launch code is reproduced token for token,
so this PR makes no claim about launch overhead.

## Not in this PR

- **Step 1 remainder.** Two parts stay as exported:
- Hoisting `host_common.cuh` to a header at the `csrc/` level shared by
the 14 Cake families. This is a cross-family change.
- Dropping the explicit `cudaSetDevice` next to the device guard. The
issue asks for the tvm-ffi header to be confirmed first.
- **Step 3 proper.** The exporter would need to regenerate the attention
programs with arch-conditional emission. The merge here is a disclosed
hand fold of exporter output. The paired attention-stage timing that the
step asks for is not run; the per-architecture SASS gate stands in for
it.
- **Step 4** (drop the two N=1196 PDL-early programs `588033a8…` /
`ceb72031…`): not done. A real 720p row reaches these programs, so
dropping them is a performance decision that needs the paired timing the
step describes.
- **Step 5** (regenerate without the dead parameters `pf_l2`,
`COS`/`SIN`, `probe`): not done because it needs the exporter.
- **Step 6** (encode the TMA descriptors once per prepared runner;
compute the GEMM census once at import): not done. This is a host-path
change that needs its own tests.
- **Step 7 remainder.** Two parts are not done:
- Reading the SM103 SM count from hardware. The GB300 used for
validation reports 152 multiprocessors, and `DEFAULT_SM_COUNT` stays
148, which is within the rule's verified range.
- The optional import-time check of SM-count coverage. The 132-SM hole
stays.
- **Step 8** (the `_h` twin experiment): not run.
- **Package data.** `pyproject.toml` has no package-data entry for the
package's `csrc/`. This predates the PR: at the base, a wheel ships none
of it either.

```experimental-tests
tests/experimental/test_cake_kimi_k3_vision_tower.py
```

Part of #6659

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for Kimi K3 vision-tower kernels on SM100 and SM103
architectures.
* Improved JIT library identification so changes to source,
architecture, or compilation settings produce distinct builds.
* Added shared launch handling for GEMM, attention, merge, and RMSNorm
operations.
* **Documentation**
  * Updated architecture, launcher, export, and coverage documentation.
* **Tests**
* Added coverage for registry consistency, launcher selection, digest
behavior, and program reachability.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c8be875](https://github.com/flashinfer-ai/flashinfer/commit/c8be875c7c403c4eac664f034b098157d9dc0642)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T07:07:15Z
- **提交信息**: fix(cake_dsa_train): each warp's tcgen05.ld addresses its own TMEM lane quarter (#6778)

<!-- .github/pull_request_template.md -->

## 📌 Description

The Cake DSA sparse-attention training backward
(`flashinfer/experimental/cake_dsa_train`, the four backward programs
`cake_dsa_h64_train_{726ceb6d,76061910,d6a7bc0b,e29d165e}…_kernel.cu`)
loads its `.16x256b` TMEM fragments (S, dP, dQ, dQr, dKV, dKR) with
`tcgen05.ld` at lane 0 or 16 from every warp of a warpgroup:

```cpp
asm volatile("tcgen05.ld.sync.aligned.16x256b.x8.b32 ..." : ... : "r"(tmem_tmem + 192));
```

PTX ISA, tcgen05 "Access restrictions": "A lane of the Tensor Memory can
be accessed by a single warp in the warpgroup". Warp 0 of a warpgroup
may access lanes 0-31, warp 1 lanes 32-63, warp 2 lanes 64-95 and warp 3
lanes 96-127. Warps 1-3 therefore address another warp's lanes. On
SM100/SM103 the kernels compute the right result today, because the
hardware serves the warp's own quarter. All 20 loads of each program now
add the warp's lane base, so each warp names the lanes it reads:

```cpp
const int tmem_lane_base = (tid & 96) << 16;   // (warp % 4) * 32 in the lane field
asm volatile("tcgen05.ld.sync.aligned.16x256b.x8.b32 ..." : ... : "r"(tmem_tmem + tmem_lane_base + 192));
```

The MMA operands are unchanged. `build.json` carries the new source
digests, and a new closure digest for each of the 12 (program, arch)
entries, so no JIT cache entry of the old sources is reused.

`tests/experimental/test_cake_dsa_train.py` and
`test_cake_dsa_train_api.py` pass on GB300 (SM103): 108 passed.

The table times the backward (`cake_backend.backward`, eager) of the
benchmark rows on GB300 (sm_103a), CUDA 13.3. It compares main and this
PR as the mean of two processes per side (main, PR, PR, main), each with
1 s windows, back to back and with a cool-down delay before every call.
Times are in ms.

| row | back to back main → PR | cooled main → PR |
|---|---|---|
| doc_4096 | 3.625 → 3.610 (-0.4%) | 3.529 → 3.529 (+0.0%) |
| doc_4095 | 3.652 → 3.630 (-0.6%) | 3.530 → 3.530 (+0.0%) |
| doc_16231 | 16.615 → 16.588 (-0.2%) | 16.496 → 16.495 (-0.0%) |
| doc_32768 | 34.346 → 34.385 (+0.1%) | 34.190 → 34.187 (-0.0%) |
| tail_2123x67923 | 2.901 → 2.839 (-2.1%) | 2.773 → 2.774 (+0.0%) |
| packed_glm_a | 18.359 → 18.397 (+0.2%) | 18.216 → 18.209 (-0.0%) |

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Improvements**
* Updated memory reads in experimental DSA training kernels to use
lane-specific offsets across supported GPU architectures. This changes
how threads access existing data regions while preserving their
established offsets and other kernel behavior. The update applies to
several kernel variants and their associated generated-library build
metadata.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [653cce0](https://github.com/flashinfer-ai/flashinfer/commit/653cce0a6e903a042d374cd509002bd82ae6d3a3)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T07:06:32Z
- **提交信息**: fix(cake_minimax_h3): wait for the peer CTA's last stage releases before the pre-attention QKV GEMM load warp exits (#6820)

**Race.** These are 2-CTA (`cta_group::2`, cluster of 2) tcgen05 GEMMs.
The leader CTA's MMA warp releases each stage of the TMA load ring with
`tcgen05.commit.cta_group::2.mbarrier::arrive::one.shared::cluster.multicast::cluster`
(mask `0b11`) on the stage-release mbarrier of both CTAs. The peer CTA's
load warp waits that barrier only before a refill, so after its last
refill it can leave the tile loop and the CTA can exit while the
arrive-ons for the last ring-depth stages are still in flight toward its
shared memory; an async arrive on the shared memory of a CTA that has
exited is undefined (PTX ISA §2.2.2). PTX gives no ordering between two
`tcgen05.commit` operations (§9.7.18.6), so the later accumulator-ready
commit that the epilogue waits for does not cover the earlier stage
releases, and the teardown cluster barrier does not either.

**Change.** After its tile loop the load warp (the same lanes that wait
in the main loop) now waits the stage-release barrier for the last
ring-depth stages, advancing its stage index and phase exactly as the
main loop does (a producer tail, as in CUTLASS's `producer_tail`).
Stages that were never filled pass immediately, so short problems are
unaffected.

**Affected programs.** The 2-CTA QKV GEMMs of the MiniMax-H3
pre-attention: the BF16 GEMM kernel in
`csrc/cake_minimax_h3_bf16_pre_attention_sm103a.cu` (7-stage ring,
sm_100a and sm_103a) and the two NVFP4 fused QKV GEMM programs in
`csrc/cake_minimax_h3_nvfp4_pre_attention/` (5-stage rings; `10cb85…`
serves sm_103a, `bdfc61…` sm_100a). Not affected: the RMSNorm + AdaLN
stages, the MXFP8 pre-attention stages and the QKV quantize-and-pack
kernels (no 2-CTA tcgen05 ring).

**Tests.** `tests/diffusion_ops/test_minimax_h3_bf16_pre_attention.py`
(including the 44-shape suite under
`FLASHINFER_RUN_FULL_MINIMAX_H3_TESTS=1`) and
`tests/test_minimax_h3_nvfp4.py`: 116 passed on GB300 (sm_103a); the
sm_100a programs compile.

**Timing** (NVIDIA GB300, sm_103a, CUDA 13.3; one launch of the
operator, median over 3 ABBA rounds in one process, cold L2; "cooled"
adds an idle delay before every call so the GPU is not power-throttled):

| shape | before (us) | after (us) | change | before, cooled (us) |
after, cooled (us) | change, cooled |
|---|---|---|---|---|---|---|
| BF16 pre-attention stage, M = 4824, P = 8 | 583.42 | 583.99 | +0.10% |
581.79 | 581.47 | -0.06% |
| NVFP4 pre-attention stage, M = 4824, P = 8 | 238.57 | 236.96 | -0.68%
| 200.38 | 199.84 | -0.27% |

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved processing reliability for canceled or completed work items
by ensuring pending computation stages are fully synchronized.
* Updated pipeline tracking across multiple execution stages to prevent
incomplete work from affecting subsequent operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2b3cd4f](https://github.com/flashinfer-ai/flashinfer/commit/2b3cd4f2f990954ea9a196c352dadae25fd3ff8c)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T07:05:24Z
- **提交信息**: fix(cake_dense_projection_gemm): every CTA-pair program drains the multicast stage releases before it exits (#6763)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes an exit race in the Cake dense projection GEMM
(`flashinfer.experimental.dense_projection_gemm`).

**Cause.** The CTA-pair programs whose exit is the cluster barrier
(every program without bit 8 of `pro`) stop waiting on the stage-release
barrier `mma_done` in each CTA's load warp after the last refill. The
leader's MMA warp releases every stage of both CTAs with a multicast
`tcgen05.commit`. The last `min(stages, K steps)` of those arrivals can
still be in flight to the follower's shared memory when the follower CTA
exits. The PTX ISA requires a CTA to ensure that its peer has not exited
before an operation on the peer's shared memory completes. Neither
existing synchronisation orders these arrivals:

- the exit `barrier.cluster` completes no asynchronous operation;
- the epilogue's wait on the later accumulator commit does not order an
earlier commit's arrival (commits are not pipelined with one another).

**Fix.** The load warp of each CTA now ends with a producer tail: one
`mma_done` wait per stage after its last tile, the same tail in the same
spelling as the CTA-local-exit programs (bit 8 of `pro`) already have.
The stage barrier's initial phase lets the never-refilled stages pass at
once, so the waits consume exactly the commits still in flight.

- 49 kernel sources change, covering every CTA-pair program without bit
8.
- The single-CTA (`c1`) programs and the CTA-local-exit programs do not
change.
- `build.json` carries the new source digests, and the 75 affected
entries get new closure digests, so no JIT cache entry of the old
sources is reused.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually (no Python file changes;
`scripts/check_cake_build_manifests.py`: 7 packages, 0 findings).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

- Every changed entry compiles: 39 `sm_100a` entries with nvcc 13.3 and
36 `sm_107a` entries with NVRTC 13.4.
- `tests/experimental/test_cake_dense_projection_gemm.py` on GB300
(SM103a, CUDA 13.3) gives 166 passed. FlashInfer registers no SM103
program for this package, so these runs build the shipped `sm_100a`
sources for `sm_103a` through the package's own JIT and planner, as in
#6625.
- CPU only, 141 passed and 25 skipped.

**Performance.** GB300 under the same `sm_103a` build, cold L2,
`warmup_ms=100, bench_ms=1000`; cooled runs put a delay of one launch
between calls. Each cell gives two medians in µs from two interleaved
rounds (main then this PR, then this PR then main). The `pd2_pro15` row
runs a program this PR does not change.

| Row (GLM-5.2) | Program | main back-to-back | this PR back-to-back |
main cooled | this PR cooled |
|---|---|---|---|---|---|
| q_a fwd T 16172 | `kk_n256_cg_pro7` | 213.76 / 213.50 | 213.70 /
214.24 | 203.17 / 203.39 | 203.20 / 203.42 |
| q_a dgrad T 16172 | `kn_n256_pro7` | 216.48 / 216.06 | 215.97 / 215.62
| 202.17 / 202.17 | 202.37 / 202.08 |
| q_a wgrad T 16172 | `nn_n256_sks_sb2_pro7` | 221.18 / 222.40 | 221.92
/ 221.22 | 209.15 / 209.31 | 209.66 / 209.41 |
| o_proj fwd T 16231 | `kk_n256_m256_ov_ht_pro7` | 1875.96 / 1859.36 |
1863.53 / 1857.50 | 1592.19 / 1593.69 | 1593.88 / 1594.64 |
| shared_down dgrad T 16231 | `kn_n256` | 221.18 / 220.51 | 220.42 /
215.52 | 208.35 / 208.46 | 208.48 / 208.58 |
| kv_a dgrad T 16231 | `kn_n256_tma1_pd2_pro15` (unchanged) | 64.13 /
64.13 | 64.13 / 64.13 | 64.61 / 64.38 | 64.42 / 64.38 |

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #5677 (the existing experimental dense projection GEMM
package; this PR only changes its kernel sources and manifest digests)
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware (GB300, through the `sm_103a` build described above;
the package registers SM100 / SM107 programs).
- [x] Nothing is registered in `flashinfer/aot.py` (this PR does not
change registration or routing).
  - [x] **Test scope declared below.**

```experimental-tests
tests/experimental/test_cake_dense_projection_gemm.py
```


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Dense projection GEMM operations now wait for outstanding computation
to complete before the loader exits, improving synchronization across
supported kernel variants.
* **Chores**
* Refreshed build metadata without changing supported architectures,
CUDA requirements, build flags, or source lists.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e4e7510](https://github.com/flashinfer-ai/flashinfer/commit/e4e7510f51fe9f058390ad84c66178805c8b2f45)

- **作者**: Zihao Ye
- **时间**: 2026-10-20T07:05:20Z
- **提交信息**: fix(cake_alpha_moe): one TMEM address per warp for the NVFP4 epilogue tcgen05.ld (#6767)

<!-- .github/pull_request_template.md -->

## 📌 Description

The NVFP4 AlphaMoE kernels (`csrc/alphamoe_nvfp4_sm100.cu`,
`alphamoe_nvfp4_c386_up.cu`, `alphamoe_nvfp4_c388_up.cu`) load their
epilogue accumulators with `tcgen05.ld` at

```cpp
int down_addr = taddr + (unsigned int)(physical_feature << 16) + ...;   // physical_feature = consumer_warp * 32 + lane
```

a different TMEM lane in every thread. PTX requires one address per warp
for `tcgen05.ld` ("All the threads in the warp must specify the same
value of taddr [...] Otherwise, the behavior is undefined"). ptxas moves
the operand into a uniform register, which takes one lane's value, so
the kernels compute the right result today, but only by accident of that
lowering. The 66 sites now pass the warp's lane base, the value lane 0
already passed:

```cpp
int down_addr = taddr + (unsigned int)((consumer_warp * 32) << 16) + ...;
```

`tests/moe/test_alphamoe_nvfp4_sm100.py`,
`test_alphamoe_nvfp4_selfroute.py` and
`test_alphamoe_nvfp4_source_route.py` pass on GB300 (SM103): 30 passed.

`alphamoe_nvfp4_routed_moe` at E=256, N=1024, K=6144, top_k=8, GB300
(sm_103a), CUDA 13.3, main vs this PR, median of two runs per side
(main, PR, PR, main), 1 s windows, back to back and with a cool-down
delay before every call. The M=4 and M=16 unprepared routes vary by up
to ±30% between runs of the same build.

| M | prepared weights | route | back to back µs main → fix | cooled µs
main → fix |
|---|---|---|---|---|
| 1 | no | 1 | 19.95 → 20.03 (+0.4%) | 19.95 → 20.03 (+0.4%) |
| 1 | yes | 1 | 20.02 → 20.08 (+0.3%) | 20.00 → 20.08 (+0.4%) |
| 4 | no | 8 | 199.95 → 190.75 (-4.6%) | 98.75 → 135.87 (+37.6%) |
| 4 | yes | 8 | 194.48 → 199.39 (+2.5%) | 121.18 → 107.18 (-11.6%) |
| 8 | no | 2 | 87.06 → 87.41 (+0.4%) | 86.66 → 87.47 (+0.9%) |
| 8 | yes | 9 | 79.94 → 80.11 (+0.2%) | 80.00 → 80.08 (+0.1%) |
| 16 | no | 7 | 193.57 → 193.55 (-0.0%) | 157.56 → 160.67 (+2.0%) |
| 16 | yes | 9 | 110.51 → 110.34 (-0.2%) | 110.54 → 110.37 (-0.2%) |
| 32 | no | 7 | 264.37 → 267.92 (+1.3%) | 207.20 → 208.30 (+0.5%) |
| 32 | yes | 7 | 266.78 → 264.58 (-0.8%) | 206.77 → 208.22 (+0.7%) |
| 64 | no | 7 | 305.87 → 310.00 (+1.3%) | 251.06 → 251.76 (+0.3%) |
| 64 | yes | 7 | 306.94 → 307.15 (+0.1%) | 251.17 → 252.06 (+0.4%) |
| 128 | no | 3 | 266.13 → 267.28 (+0.4%) | 262.08 → 262.83 (+0.3%) |
| 128 | yes | 19 | 219.63 → 219.94 (+0.1%) | 219.65 → 219.87 (+0.1%) |
| 256 | no | 6 | 312.74 → 315.44 (+0.9%) | 280.06 → 280.00 (-0.0%) |
| 256 | yes | 6 | 318.54 → 315.39 (-1.0%) | 279.92 → 279.90 (-0.0%) |
| 512 | no | 4 | 328.79 → 330.11 (+0.4%) | 294.02 → 294.29 (+0.1%) |
| 512 | yes | 18 | 235.98 → 235.87 (-0.0%) | 236.05 → 235.82 (-0.1%) |
| 1000 | no | 6 | 400.70 → 401.64 (+0.2%) | 366.69 → 366.54 (-0.0%) |
| 1000 | yes | 16 | 258.94 → 258.75 (-0.1%) | 255.57 → 257.63 (+0.8%) |
| 4096 | no | 6 | 899.02 → 896.16 (-0.3%) | 863.42 → 862.53 (-0.1%) |
| 4096 | yes | 16 | 384.65 → 385.01 (+0.1%) | 384.32 → 384.54 (+0.1%) |

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected tensor-memory address selection in NVFP4 MoE up-projection
processing. Gate/up data loads now select the appropriate consumer-warp
region across standard and paired-consumer execution paths, while
retaining existing feature and stage offsets. This improves consistency
in how data is selected during these computations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4647
- **最后更新**: 2026-10-21T03:14:27Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Ishan, William Lin, Aryan Kumar

## AI分析总结

## FastVideo 昨日提交分析

### 1. 主要更新类型
本次提交以**功能新增**为主导，同时包含文档优化。5 条提交中 4 条标记为 `[feat]`，1 条标记为 `[docs]`，无 Bug 修复或性能优化类提交。

### 2. 关键变更点及其与项目方向的关系

- **H3 PDD/DMPDD 训练支持与 Ref2VA 预处理**（#1984）：引入了新的训练方法和预处理流程，直接扩展了 FastVideo 作为视频生成加速框架的核心训练能力。
- **Cookbook 生态体系大幅完善**：多条提交围绕 Cookbook 展开——包括服务化部署入口（#1999）、硬件目录、模型清单容量元数据（#1983）、单 GPU 显存计算器（#1978）以及文档交互体验优化（#1992）。这表明项目正加速构建面向用户的"即插即用"部署体验。

### 3. 对项目的影响和潜在意义

- **降低用户使用门槛**：显存计算器和容量元数据帮助用户在部署前预估硬件需求，减少试错成本。硬件目录的引入让不同 GPU 环境的选择更加透明。
- **从"框架"走向"平台"**：Cookbook 服务化和落地页的构建，标志着 FastVideo 正从一个单纯的加速训练/推理框架，向提供完整工具链和参考实践的平台化方向演进。
- **训练能力扩展**：H3 PDD/DMPDD 代表了对新的扩散模型变体的训练支持，增强了框架在学术研究和生产场景中的适用广度。

### 4. 值得关注的技术点

- **Ref2VA 预处理**：结合参考图生成视频的场景越来越热门，此预处理管线的加入意味着框架正在拥抱多模态条件生成。
- **Packed 预处理策略**：以打包方式组织数据可能涉及内存/IO 优化，值得关注其在大规模训练中的性能表现。
- **单 GPU 显存计算器**：这是一个面向开发者体验的实用工具，其计算精度和覆盖的模型/分辨率范围值得后续关注。

### 5. 对项目发展的影响

结合 README 可知，FastVideo 致力于视频生成的加速与部署，并配有 Documentation、Cookbook、Quick Start 等完善的用户资源体系。昨日提交的方向与项目定位高度一致：

- 一方面**深化训练侧能力**（H3 新方法、Ref2VA 预处理），保持技术前沿性；
- 另一方面**强化用户侧体验**（硬件目录、显存计算、服务化部署），提升项目在实际落地场景中的易用性。

两线并进的策略使 FastVideo 在"研究加速"和"工程部署"两端均有实质推进，体现了项目从核心引擎建设向生态完善过渡的成熟趋势。

## 详细提交记录

### [cdda1b7](https://github.com/hao-ai-lab/FastVideo/commit/cdda1b7535fe32699335e39db82c1d4db21ceb88)

- **作者**: William Lin
- **时间**: 2026-10-20T18:15:57Z
- **提交信息**: [feat] Add H3 PDD/DMPDD training and packed Ref2VA preprocessing (#1984)

### [089a5a5](https://github.com/hao-ai-lab/FastVideo/commit/089a5a55a000db41b53fb64bd5f65206de727aba)

- **作者**: Aryan Kumar
- **时间**: 2026-10-20T16:10:29Z
- **提交信息**: [feat] Cookbook serving, hardware catalog, and landing page (#1999)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [137d911](https://github.com/hao-ai-lab/FastVideo/commit/137d9110caaef5f9febc730b70749aff69393b4b)

- **作者**: Aryan Kumar
- **时间**: 2026-10-20T16:00:56Z
- **提交信息**: [docs] Make cookbook copy actions explicit and hardware opt-in (#1992)

### [d4f1445](https://github.com/hao-ai-lab/FastVideo/commit/d4f144581d6882d5bceb288ca13d767c054ca041)

- **作者**: Yixing Wang
- **时间**: 2026-10-20T08:24:19Z
- **提交信息**: [feat] Add capacity metadata to existing cookbook model manifests (#1983)

Co-authored-by: leo <yixingwang@YIXINGs-MacBook-Pro.local>
Co-authored-by: aryan5v <email.aryan1005@gmail.com>
Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [5f96664](https://github.com/hao-ai-lab/FastVideo/commit/5f96664abf9bedb9b0326d86e0513da6bfc5f983)

- **作者**: Ishan
- **时间**: 2026-10-20T08:12:06Z
- **提交信息**: [feat] Added a single-GPU VRAM calculator for cookbook deployments (#1978)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34771
- **最后更新**: 2026-10-21T00:14:28Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: Sayak Paul, Alexander Ivanov, Akshan Krithick

## AI分析总结

# huggingface/diffusers 昨日提交分析

## 1. 主要更新类型
- **功能新增**（占主导）：两个新 pipeline（RFD4-Proteina、Bria fibo-2）、一个新自编码器（KVAE-Audio）
- **重构**：解码逻辑从分散的模型中抽离到核心 denoise 组
- **Bug/CI 修复**：PyArrow 兼容性修复
- **文档与测试**：多提交均配套了文档和测试更新

## 2. 关键变更点及与项目方向的关系

- **领域扩展**：RFD4-Proteina 引入蛋白质结构生成 pipeline，将 diffusers 从视觉生成拓展到生物分子设计领域，标志着项目从"图像/视频"向更广泛科学生成模型的外延。
- **多模态与指令编辑**：Bria fibo-2 通过 Perceiver 重采样器和门控交叉注意力融合 Qwen3-VL 隐藏状态，一个 pipeline 同时覆盖文生图、五图指令编辑和带/不带引导两种 checkpoint，体现了"一个类覆盖多个任务与变体"的设计趋势。
- **音频生成储备**：KVAE-Audio 自动编码器为后续音频类 pipeline 铺路，契合 diffusers 支持多模态 latent 扩散的路线。
- **架构统一化**：将 unpack 步骤从 flux/krea2/ltx 各自的解码器移入核心 denoise 组，并定义"规范 latent 形态"，是减少家族间重复、推进管道代码模块化统一的关键一步。

## 3. 对项目的影响和潜在意义

- **覆盖面**：一天内新增两个完整 pipeline 和一个音频自编码器，说明社区生态活跃，核心抽象（Transformer + VAE + Scheduler + Pipeline 组合）已被反复验证可复用。
- **技术债清理**：unpack 的集中化使未来的模型家族更易接入，也避免了 latents 形态（packed/normalized/patchified）在各处隐式约定。
- **工程规范**：多个提交强调"按公开接口测试""与上游测试同步""转换脚本校验固定超参"，提升了合入门槛和回归可靠性。
- **兼容性维护**：PyArrow 修复保障 CPU CI 绿灯，避免依赖生态变化阻断贡献流程。

## 4. 值得关注的技术点

- **RFD4-Proteina** 的固定超参策略：checkpoint 转换脚本校验 trunk 复用、triangle multiplication、手性对齐等设定，而非暴露为可选项——保证复现与发布的严格一致。
- **fibo-2** 的条件融合双通道设计：gist tokens 共享主流 vs. 五块 gated cross-attention 各绑一组 Qwen3-VL 层；text_render 图像按训练方式绘制并交由 VLM 预览，是"训练-推理像素级对齐"的范例。
- **规范 latents 形态** 的引入与模块化测试，配合明确的弃用窗口（0.42 引入、0.47 移除），体现了 HuggingFace 对 API 生命周期的成熟管理。
- **torch.compile 兼容**：fibo-2 用 expected-failure 标记而非跳过动态设备上下文的失败，保持测试信号可见。

## 5. 对项目发展的整体影响

结合 README（HuggingFace 团队维护的开源扩散模型库），这些提交延续了 diffusers "以通用抽象容纳任意模态与任务"的核心方向：向生物、音频等新领域拓展边界；用统一的 denoise/latent 规范收敛各家族实现；并以严格的转换校验、公开接口测试和明确的弃用策略，为下一次架构演进积累工程信用。这使项目既能快速吸纳外部模型，又能保持内部一致性，巩固其作为生成模型基础设施的地位。

## 详细提交记录

### [5378870](https://github.com/huggingface/diffusers/commit/537887041938fc6fe61ad583c3ae77477c9ebac9)

- **作者**: Kieran Didi
- **时间**: 2026-10-20T21:12:21Z
- **提交信息**: Add RFD4-Proteina (#15088)

* Add RFD4-Proteina

Adds the RFD4-Proteina pipeline with its transformer, autoencoder and per-modality schedulers, a LoRA loader mixin, a checkpoint conversion script, tests and documentation.

* Address review: pass tensors instead of dicts, name the pipeline example inputs

prepare_latents returns a tuple and the sampling loop works on named tensors. The pipeline output has bb_ca, local_latents and clean_* fields instead of dicts, and the callback tensors are named. The pipeline properties move below __init__, the transformer return annotation names its tuple, LoRA moves from the loaders page to the pipeline docs, and the pipeline tests spell out their helpers.

* Remove the constructor options that are constant for the released checkpoint

The transformer always recycles the trunk, updates the pair representation with triangle multiplication (without bias) and aligns the chirality feature, as the released checkpoint does. The converter now checks that a checkpoint has exactly these settings instead of carrying them as options.

* Spell out the scheduler test arguments and the docs examples, default the autoencoder to its released features

The scheduler test helper takes its options by name, and the usage and batching examples pass the five required inputs by name. The autoencoder's default encoder features now match the released checkpoint, and the decoder moves its allowed-residue table to the token types' device.

* Follow the repository's test and docs checks

Restore the LoRA mixin on the loaders page, which utils/check_support_list.py requires for every LoRA loader mixin, and keep the mention in the pipeline docs. Compose the attention and torch.compile testers on the models, drop the model-level LoRA tests that the first pull request should not carry, and make the pipeline's backbone-noising step public as a lifecycle method.

* Keep the pipeline test helpers at the top of the test class

* Drop the training-only detach calls and make the noise helpers static methods

* Remove num_inference_steps and skip the unused encode for inverse folding

The number of steps is fixed by the released recipe and is the length of recycle_depths. Inverse folding starts both modalities at time zero, so its latents are noise and the encoded input was only consuming random draws.

---------

Co-authored-by: YiYi Xu <yixu310@gmail.com>

### [de988b7](https://github.com/huggingface/diffusers/commit/de988b7ee77c393a63865d265d19e267ef9c7bf5)

- **作者**: muhammadali-afridi
- **时间**: 2026-10-20T15:37:11Z
- **提交信息**: Add Bria fibo-2 (#14991)

* Add Bria fibo-2: BriaFibo2Pipeline and BriaFibo2Transformer2DModel

fibo-2 is Bria's 8.1B flow-matching DiT, built on the Z-Image block and
conditioned on Qwen3-VL hidden states two ways: a Perceiver resampler turns
them into gist tokens that share the stream with the image tokens, and five
blocks add gated cross-attention to their own bundle of Qwen3-VL layers. It
uses the Flux 2 VAE.

One pipeline class covers both of the model's jobs and both checkpoints:
text-to-image generation, instruction editing of up to five images with an
optional mask, the turbo checkpoint (4 steps, no guidance) and the guided one.

- BriaFibo2Transformer2DModel, with images to edit passed as context latents
- BriaFibo2Pipeline, including:
  - captions cleaned and serialized the way training did, for generation and
    edits, in every caption form fibo-2 was trained with: a full caption, a
    short description, or a short description with its text_render list
  - images of the caption's text, which Qwen3-VL sees beside the prompt:
    drawn the way training drew them, by default (`render_text_images`), or
    passed as `text_images`
  - masked edits, the region greyed out through a binary mask as in training
- a conversion script from the original checkpoint layout
- model and pipeline tests, and docs

Verified against Bria's reference implementation on an A100 and an H100.

* Apply RoPE with explicit casting instead of an autocast block

The rotation already runs in float32 and casts back to the input's dtype, and
none of its ops are autocast ops, so the autocast block changed nothing.

* Mark the full-graph compile tests as expected failures instead of skipping them

Both fail with torch._dynamo.exc.Unsupported, on the torch.device context in
which RopeEmbedder, copied from Z-Image, builds its frequency table. Strict, so
they show up once Dynamo can trace it.

* Test the pipeline through its public call only

Removes the tests of private prompt and text-image helpers. The caption
cleaning test now checks that a caption renders like its trained form, and
the text images test draws its strips with the public draw_text_image.

* Annotate the transformer's tuple return as tuple[torch.Tensor]

* Make _get_qwen_prompt_embeds a staticmethod that takes the text encoder and processor

The chat template, the sequence length and the Qwen3-VL layers become
arguments, defaulting to module constants; encode_prompt passes the
pipeline's own. The edit and text prompt helpers become classmethods.
Embeddings are unchanged.

* Point to the release checkpoints, briaai/Fibo-2.0-dev and briaai/Fibo-2.0-turbo

The docs and the example load Fibo-2.0-dev and show the turbo checkpoint's
4-step edits without guidance. Text-image fonts download from Fibo-2.0-dev,
and the conversion script's usage converts a local original checkpoint.

* Parse prompts in one method, take fonts as an argument, and size and mask images in BriaFibo2ImageProcessor

- `_parse_prompt` replaces `_clean_caption`, `_normalize_caption`, `_split_edit_prompt`, `_get_generation_prompt` and
  `_get_caption`. `_text_render_entries`, `_get_text_prompt` and `_draw_text_images` are inlined.
- The pipeline no longer fetches fonts: `__call__` takes `fonts`, and the docs show how to get the ones training
  used from briaai/Fibo-2.0-dev. A text that needs them warns without them.
- `BriaFibo2ImageProcessor` holds the trained sizes, the cover-and-crop and the masking. The masking stays before the
  crop, at the image's own size, where training greyed the images.

The prompts and images Qwen3-VL sees, the VAE's inputs and the outputs are byte-identical to before.

* Prepare the images to edit and the mask in BriaFibo2ImageProcessor.preprocess, as Flux3's image processor does

* Point to the turbo checkpoint's new name, briaai/Fibo-2.0-edit-turbo

* Show a working example for each use in the docs, and call the model Fibo 2.0, as its model cards do

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>
Co-authored-by: Linoy Tsaban <57615435+linoytsaban@users.noreply.github.com>

### [a5eb4c1](https://github.com/huggingface/diffusers/commit/a5eb4c1364370cb30875441965bcad89306624c0)

- **作者**: Sayak Paul
- **时间**: 2026-10-20T13:54:14Z
- **提交信息**: Fix PyArrow compatibility in CPU CI (#15082)

### [aea7b70](https://github.com/huggingface/diffusers/commit/aea7b70be0f594bcdc15a6f2677ee2ca85e49e8e)

- **作者**: Alexander Ivanov
- **时间**: 2026-10-20T09:14:11Z
- **提交信息**: [feat] add KVAE-Audio autoencoder (#14384)

* [feat] add KVAE-Audio autoencoder

* [fix] non-contiguous tensor into in_proj in AutoencoderKLKVAEAudio

* [chore] sync KVAE-Audio with upstream test and annotation changes

* [refactor] dedicated attention class and processor for AutoencoderKLKVAEAudio

* [refactor] remove the runtime sample_rate argument from AutoencoderKLKVAEAudio

* [refactor] always apply attention in AutoencoderKLKVAEAudio, drop use_attn

* [refactor] drop the derived latent_dim default from AutoencoderKLKVAEAudio

* [docs] fix encoder_rates docstring in AutoencoderKLKVAEAudio

* [refactor] rename Snake1d to KVAEAudioSnake1d in AutoencoderKLKVAEAudio

* [tests] skip layerwise casting training for AutoencoderKLKVAEAudio

### [6184688](https://github.com/huggingface/diffusers/commit/6184688f71087bf635414e90fd4b907de36534d4)

- **作者**: Akshan Krithick
- **时间**: 2026-10-20T08:16:18Z
- **提交信息**: move unpack out of the flux, krea2 and ltx decoders into the core denoise groups (#14737)

* add a modular test that pins the canonical latents form each family leaves in the state

* move unpack out of the flux, krea2 and ltx decoders into the core denoise groups

* pop the unpack step from a copy of the blocks in the deprecation tests

* let families that decode inside the denoise loop opt out of the latents-form test

* document the canonical latents form in the modular reference

* [docs] canonical latents form: name normalize, patchify and pack separately

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* require geometry on the unpack steps and test the deprecated decode path directly

* skip the canonical latents test explicitly for ltx 2.5 too

* remove the packed latents path in 0.47.0, five releases after 0.42

* update the latents_output_name comment for the explicit skips

* move the packed test latents to the test device

---------

Co-authored-by: YiYi Xu <yixu310@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
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


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13279
- **最后更新**: 2026-10-21T02:39:55Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 2
- **主要提交者**: Hong Zhang, Zhongjie Duan

## AI分析总结

## 昨日提交分析：modelscope/DiffSynth-Studio

### 1. 主要更新类型

- **Bug修复**（占比最大）：涉及CPU offload编译、MOSS VAE解码等运行时问题
- **版本发布**：连续两次版本迭代（2.1.10 → 2.1.11），频率较高
- **配置优化**：MOSS-Image默认scheduler配置更新
- **小规模重构**：修复逻辑从解码阶段迁移到模型decode阶段，涉及entropack相关依赖调整

### 2. 关键变更点与项目整体方向的关系

- **CPU offload编译修复**：针对CPU卸载场景下的Dynamo/PyTorch编译问题进行修复，表明项目正在强化**大模型在资源受限环境下的可用性**，与DiffSynth致力于让扩散模型更易部署的方向一致。
- **MOSS VAE修复与调度器配置**：MOSS系列是项目重点支持的图像/多模态模型之一，此次修复（类型转换）和配置优化直接提升MOSS模型的**推理稳定性与生成质量**。
- **entropack预量化依赖更新**：引用了"prequants"（预量化模型），说明项目正积极探索**量化加速**路径，降低模型推理的显存与计算开销。

### 3. 对项目的影响和潜在意义

- **稳定性提升**：多个Bug修复使MOSS和CPU offload场景下的用户少踩坑，减少issue数量。
- **发布节奏加快**：一天内两次版本发布说明项目处于**活跃迭代期**，可能有外部需求或合作方在推动。
- **扩展硬件适配**：CPU offload与量化修复的组合，暗示项目正从"高性能GPU实验"向**更广泛硬件兼容**过渡，有利于用户面扩大。

### 4. 值得关注的技术点

- **PyTorch Dynamo编译兼容性**：CPU offload + torch.compile的组合是当前PyTorch生态中的热门但易碎区域，该修复可能对其他使用类似组合的项目有参考价值。
- **MOSS VAE类型转换**：VAE解码时的dtype不匹配是多模态模型常见的隐性Bug，修复方式从后处理迁移到模型层，属于更合理的**根因修复**策略。
- **entropack预量化集成**：将量化模型作为链接引用，体现了"预量化权重分发"的模式，值得关注其后续是否成为项目的标准量化方案。

### 5. 对项目发展的影响

结合README中DiffSynth-Studio作为**ModelScope旗下扩散模型综合Studio**的定位，这批提交体现了三个发展方向：

1. **工程成熟度提升**：Bug修复和版本迭代表明项目正从功能开发阶段进入**质量打磨期**，为更多用户和场景提供可靠体验。
2. **MOSS生态持续投入**：MOSS模型的VQA、调度器配置等多处优化，说明MOSS是项目中受重视的核心模型族，可能与ModelScope平台上的MOSS生态形成联动。
3. **部署友好性增强**：CPU offload、量化修复等变更共同指向一个目标——**降低使用门槛**，让更多开发者和研究者能以较低硬件成本体验扩散模型，这符合模型社区开放易用的整体趋势。

## 详细提交记录

### [b34c837](https://github.com/modelscope/DiffSynth-Studio/commit/b34c83793f783b8bf0c7e82142e06dda01f98d27)

- **作者**: Hong Zhang
- **时间**: 2026-10-20T15:31:54Z
- **提交信息**: fix compile for cpu offload (#1772)

* fix compile for cpu offload

* fix cycle ref of entropack dynamo

### [6b3c254](https://github.com/modelscope/DiffSynth-Studio/commit/6b3c254299ec4031cb60ff5ecce18272a2646ea6)

- **作者**: Zhongjie Duan
- **时间**: 2026-10-20T08:54:06Z
- **提交信息**: update to version 2.1.11 (#1771)

### [38bcdab](https://github.com/modelscope/DiffSynth-Studio/commit/38bcdabf0866f0a647f3c6d2a02abda229ae2049)

- **作者**: Hong Zhang
- **时间**: 2026-10-20T08:43:40Z
- **提交信息**: Fix moss vae error (#1769)

* fix moss: add type cast before vae decoding

* update link for entropack prequants

* move fix to model decode

### [f796948](https://github.com/modelscope/DiffSynth-Studio/commit/f7969488aafcdcb64d1444f71eedd242416fa0dc)

- **作者**: Zhongjie Duan
- **时间**: 2026-10-20T08:37:38Z
- **提交信息**: update default MOSS-Image scheduler config (#1770)

### [6803d5c](https://github.com/modelscope/DiffSynth-Studio/commit/6803d5c84bb321e475ff6e43ff8a70c63c0990bc)

- **作者**: Zhongjie Duan
- **时间**: 2026-10-20T07:09:43Z
- **提交信息**: update to version 2.1.10 (#1768)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37527
- **最后更新**: 2026-10-21T03:12:18Z

## 提交统计

- **昨日提交总数**: 59
- **提交者数量**: 38
- **主要提交者**: Jimmy Shong, Aarne Talman, kk

## AI分析总结

# SGLang 昨日提交分析（59 条）

## 1. 主要更新类型分布
- **性能优化（Perf）约 17 条**：占据最大比重，是当日主线。
- **Bug 修复（Fix）约 20 条**：覆盖 MoE、NPU、radix-cache、DSpark 等核心模块。
- **重构（Refactor）约 5 条**，**文档（Doc）4 条**，**CI 7 条**，**测试（Test）3 条**，**功能新增（Feat）5 条**，其余为杂项维护。

## 2. 关键变更点与项目方向的关系
- **多硬件后端持续扩展**：大量提交标注 [AMD]/[NVIDIA]/[NPU]/[Apple]/[Intel]，包括 AMD gfx950 的 mHC Triton tile、MXFP8 FlyDSL GEMM、ROCm 原生 ReLU2；NVIDIA 上 B300 测试迁移与 SM100 TF32 路径；华为 NPU 上 GLM-5.2 的动态 INT8 MLAProlog 与 KV cache 扩容；新增 T-HEAD SAIL 平台初步支持；Apple MLX 改用原生 Extension Builder。这直接对应 SGLang "为多种平台提供高效 LLM 推理" 的核心定位。
- **MoE（混合专家）是架构级焦点**：路由输入从 layer/active forward 派生、层契约从量化方法派生、EP 下 expert id 映射修复、EPLB 重平衡后 Qwen3 MoE 输出损坏修复、FlashInfer CUTLASS MoE autotune 扩展到 prefill。MoE 推理正确性与性能是当前工程主线之一。
- **投机解码（speculative decoding）新组件 DSpark 兴起**：围绕 DSpark 的 CUDA 快速路径、模拟接受默认策略、权重加载测试等提交密集出现，显示项目在探索新的投机解码实现。
- **KV 与缓存系统深化**：radix-cache 拆分簿记统一化、逻辑长度与可回收长度分离、KVShard PD 传输端到端测试、unified memory 子池分配策略，均指向更大规模、更细粒度的内存复用。
- **prefill 阶段 CUDA graph 优化**（shared-read completion 默认开启）与 detokenizer 批量输出开关，针对 prefill 与输出路径的吞吐短板。

## 3. 对项目的影响和潜在意义
- 提交量大且类型均衡，表明项目处于**高速迭代期**，团队同时推进性能、稳定性和平台覆盖三条线。
- DSpark、KVShard、T-HEAD SAIL 等新代号/新平台的引入，意味着 SGLang 正在**提前布局下一代投机解码与国产芯片生态**。
- 修复类提交涉及输出损坏、位置构造器保持、OTel 上下文丢失等，说明在功能扩张的同时**重视生产环境可靠性**。

## 4. 值得关注的技术点
- **"bitwise unchanged" 式的性能优化**（如 #45124）：在保证数值完全一致的前提下加速，是高门槛的优化实践。
- **持久化 kernel 单次 launch 拷贝 decode 状态**（#45213）：利用 HBM 带宽优化 mamba 解码，属少见的状态管理级优化。
- **mHC 统计量路径按行数分流**（32 行阈值切 TF32）：体现对小 batch 数值精度与速度的精细权衡。
- **zsh IPC 安全加固**（#45250）与 CUTLASS runner 测试需要显式 server config，反映测试与部署边界的工程成熟度提升。

## 5. 结合 README 对项目发展的影响
SGLang 以"LLM 与多模态模型的快速推理"为目标，昨日提交从三个维度推进这一目标：**一是横向扩大硬件覆盖**（AMD/NVIDIA/NPU/Apple/Intel/T-HEAD），让"fast inference"可落地到更多硬件；**纵向深挖核心路径**（MoE、prefill CUDA graph、投机解码、KV 缓存），直接提升单次推理的吞吐与延迟；**并通过 CI/测试/文档同步**保证质量，使快速迭代不牺牲稳定性。总体上，这批提交强化了 SGLang 作为跨平台、高性能推理引擎的竞争力，同时为 DSpark、KVShard 等新特性进入稳定期奠定基础，预计下一阶段将看到这些特性在正式发布中的整合与文档化。

## 详细提交记录

### [b326e83](https://github.com/sgl-project/sglang/commit/b326e8349dbfa9ce23621d4309a51bdec801da94)

- **作者**: metamergebot
- **时间**: 2026-10-20T23:52:15Z
- **提交信息**: [Perf] mamba: Copy tracked decode states at HBM bandwidth in one persistent launch (#45213)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: YavorGIvanov <YavorGIvanov@users.noreply.github.com>

### [5b1dbc2](https://github.com/sgl-project/sglang/commit/5b1dbc2c80e59610e1d3189fbb7c6f1583e35ebb)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-20T23:49:13Z
- **提交信息**: [Fix] [NVIDIA] modelopt-nvfp4: Keep MoE global scales in gate/up order (#45289)

### [9686edc](https://github.com/sgl-project/sglang/commit/9686edcf80ba497f34c71676dc10fe13898bda1c)

- **作者**: kk
- **时间**: 2026-10-20T23:39:34Z
- **提交信息**: [Perf] [AMD] dsv41: faster mHC boundary Triton tile for 96+ rows, bitwise unchanged (#45124)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [027208a](https://github.com/sgl-project/sglang/commit/027208ae02fc6bb0c973714b490e38188dfd7df9)

- **作者**: Cheng Wan
- **时间**: 2026-10-20T23:26:40Z
- **提交信息**: [Doc] layer-boundary/moe: Correct guides and comments that drifted from the code (#44896)

### [299a75a](https://github.com/sgl-project/sglang/commit/299a75ac5d962087f8f09e19b23ff43548fc64c8)

- **作者**: Cheng Wan
- **时间**: 2026-10-20T23:26:15Z
- **提交信息**: [Refactor] moe: Derive routing inputs from the layer and active forward (#44994)

Co-authored-by: Aditya Suresh <152752311+adi-suresh01@users.noreply.github.com>

### [533020b](https://github.com/sgl-project/sglang/commit/533020b500ba781bfafd1f5cbadabaf03d8986f7)

- **作者**: kk
- **时间**: 2026-10-20T23:19:32Z
- **提交信息**: [Perf] [AMD] dsv41: run gfx950 MXFP8 dense GEMMs on aiter's preshuffled FlyDSL kernel (#45123)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [4f8f06f](https://github.com/sgl-project/sglang/commit/4f8f06faf3ac5e7056c827d9a2018d5f68167af5)

- **作者**: Cheng Wan
- **时间**: 2026-10-20T23:18:45Z
- **提交信息**: [Refactor] moe: Derive layer contracts from the selected quant method (#44993)

Co-authored-by: Aditya Suresh <152752311+adi-suresh01@users.noreply.github.com>

### [7b1d5cd](https://github.com/sgl-project/sglang/commit/7b1d5cd02df0b0020e74b063a745bc0aa417f953)

- **作者**: zydo
- **时间**: 2026-10-20T23:15:10Z
- **提交信息**: [Doc] agent-skills: Fix stale paths and deleted guard tests in skills and rules (#43666)

Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [bf14575](https://github.com/sgl-project/sglang/commit/bf145750a65245802dd21f3b850a604635181532)

- **作者**: weireweire
- **时间**: 2026-10-20T23:12:55Z
- **提交信息**: [Perf] prefill-cuda-graph: Make prefill shared-read completion explicit and default-on (#37958)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [d5e83ea](https://github.com/sgl-project/sglang/commit/d5e83ea4f6a07c43d16774b1e329196cebde3280)

- **作者**: Aarne Talman
- **时间**: 2026-10-20T23:11:01Z
- **提交信息**: [Perf] [AMD] deterministic: Faster extend attention launch on gfx950 (#45098)

### [c1e43b9](https://github.com/sgl-project/sglang/commit/c1e43b95f4e2286f476638d14ef10706a81950c7)

- **作者**: averyjones4
- **时间**: 2026-10-20T23:08:53Z
- **提交信息**: [Doc] cookbook: Add DeepReinforce Ornith-1.5 (#45455)

Co-authored-by: averyjones4 <averyjones4@users.noreply.github.com>

### [f1eec12](https://github.com/sgl-project/sglang/commit/f1eec1232d24559322f0cd7a7c7d8e02a1e5f6e5)

- **作者**: Cheng Wan
- **时间**: 2026-10-20T23:08:28Z
- **提交信息**: [Fix] config: Preserve ServerArgs positional constructor slots (#44991)

Co-authored-by: Aditya Suresh <152752311+adi-suresh01@users.noreply.github.com>

### [e2e1a97](https://github.com/sgl-project/sglang/commit/e2e1a97fc3e057f00ba464d49b46e723403811e6)

- **作者**: Aditya Suresh
- **时间**: 2026-10-20T23:07:48Z
- **提交信息**: [Fix] moe: Map expert ids for layers whose runner needs local ids under EP (#44480)

Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [b008ec3](https://github.com/sgl-project/sglang/commit/b008ec3de6a66d9fbf76f2c381aa9c303ac72a66)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-20T22:56:49Z
- **提交信息**: [CI] muse_spark: Move unified memory test to B300 (#45454)

### [1dd0f36](https://github.com/sgl-project/sglang/commit/1dd0f361b83a0f4c5fe917c37fc60525972c26e2)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-20T22:03:47Z
- **提交信息**: [Fix] moe: Run the shared-slot routing test without a published server config (#45448)

### [583cfc4](https://github.com/sgl-project/sglang/commit/583cfc4d55dda55b4b4de713b1ba7c728f095e34)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-20T21:57:01Z
- **提交信息**: [CI] muse_spark: Use complete local checkpoints in model tests (#45428)

### [f0b6590](https://github.com/sgl-project/sglang/commit/f0b65907227480afc376a66db62931b7e9c46c38)

- **作者**: Yuwei An
- **时间**: 2026-10-20T21:10:59Z
- **提交信息**: [Fix] DSpark: Disable simulated acceptance shortcuts by default (#45433)

### [7d9bc10](https://github.com/sgl-project/sglang/commit/7d9bc10493275a371989bd03a13147588005f136)

- **作者**: YAMY
- **时间**: 2026-10-20T20:36:33Z
- **提交信息**: [Perf] [NVIDIA] DSpark: Enable the simulated-acceptance fast paths on CUDA (#45421)

### [cc7ae37](https://github.com/sgl-project/sglang/commit/cc7ae372ac2fba9605460308c8f347c80702c828)

- **作者**: metamergebot
- **时间**: 2026-10-20T20:24:49Z
- **提交信息**: [Refactor] radix-cache: Route pending-backup split bookkeeping through one component action (#45242)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [0b536ca](https://github.com/sgl-project/sglang/commit/0b536ca112652008d5fa8766df7258b0700109f3)

- **作者**: metamergebot
- **时间**: 2026-10-20T20:24:20Z
- **提交信息**: [Fix] radix-cache: Separate logical and reclaimable value lengths in tree components (#45238)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [468e26f](https://github.com/sgl-project/sglang/commit/468e26f253b2f1d42bf3545742b7c363d0c6592e)

- **作者**: metamergebot
- **时间**: 2026-10-20T20:24:14Z
- **提交信息**: [Perf] detokenizer: Add SGLANG_BATCH_TOKENIZER_OUTPUTS to opt out of grouped return sends (#45280)

Co-authored-by: joshuadeng <joshuadeng@users.noreply.github.com>

### [bab4a80](https://github.com/sgl-project/sglang/commit/bab4a808d81fd47a039889a3f71514679d799136)

- **作者**: metamergebot
- **时间**: 2026-10-20T20:24:09Z
- **提交信息**: [Perf] unified-memory: Allocate free pages from each sub-pool's own end first (#45222)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [0d7638b](https://github.com/sgl-project/sglang/commit/0d7638b03509967e749c201146bfb04bbdfe380c)

- **作者**: metamergebot
- **时间**: 2026-10-20T20:24:04Z
- **提交信息**: [Fix] scheduler: Exclude accepted storage-tier hits from the waiting prefill load (#45158)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [dc62c3e](https://github.com/sgl-project/sglang/commit/dc62c3effd20f922fce9d54f976cf1d152517aa7)

- **作者**: metamergebot
- **时间**: 2026-10-20T20:23:59Z
- **提交信息**: [Feat] radix-tree: Report each path node's child count in collect_path_info (#45241)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [194876b](https://github.com/sgl-project/sglang/commit/194876bea07214539306526f1bd937a96e02bff9)

- **作者**: metamergebot
- **时间**: 2026-10-20T20:23:53Z
- **提交信息**: [Fix] srt: Admit only allowlisted peers on TCP-bound ZMQ IPC sockets (#45250)

Co-authored-by: daniel-salib <daniel-salib@users.noreply.github.com>

### [afe3e1d](https://github.com/sgl-project/sglang/commit/afe3e1df3107b0487258cd4a3d8e625248a8f881)

- **作者**: Yuwei An
- **时间**: 2026-10-20T20:13:39Z
- **提交信息**: [Fix] DSpark: Restore weight-loading CPU tests (#45427)

### [d69966f](https://github.com/sgl-project/sglang/commit/d69966f9c0815b7c81efece0f38c43f454cc5f92)

- **作者**: Jimmy Shong
- **时间**: 2026-10-20T20:00:46Z
- **提交信息**: [Chore] docker: Add Beam CUDA image (1/8) (#45253)

### [cfec1b9](https://github.com/sgl-project/sglang/commit/cfec1b91bb33f3267d1811680b51fd581e0df458)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-20T19:54:53Z
- **提交信息**: [Fix] muse_spark: support unified KV memory with TRT-LLM (#45356)

### [29274b4](https://github.com/sgl-project/sglang/commit/29274b41c6fc45748877d4fc72e2f79f692dad7e)

- **作者**: Aarne Talman
- **时间**: 2026-10-20T19:05:14Z
- **提交信息**: [Fix] [AMD] activation: Run ReLU2 natively on ROCm (#44198)

Signed-off-by: Aarne Talman <aarne.talman@amd.com>

### [82ac83a](https://github.com/sgl-project/sglang/commit/82ac83a8d0ab50ea7c9fe8e5b5934c2fa5a224bf)

- **作者**: Thomas Wang
- **时间**: 2026-10-20T18:49:05Z
- **提交信息**: [Perf] [AMD] dsv41: Skip unneeded layer 20 computation under decoder-bounded-replay (#45339)

### [f824657](https://github.com/sgl-project/sglang/commit/f82465718bea9d84121529848108eec59adc8e34)

- **作者**: Michael
- **时间**: 2026-10-20T18:37:32Z
- **提交信息**: [Test] [AMD] diffusion: Skip MOSS-Image mismatched-operand test on ROCm (#44596)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [c2e5742](https://github.com/sgl-project/sglang/commit/c2e574246485a055c0e51d60d1eae027e5d629c0)

- **作者**: Khoa Pham
- **时间**: 2026-10-20T17:12:06Z
- **提交信息**: [Perf] deepseek-v4: DSpark draft stages take the TF32 mHC statistics path from 32 rows on SM100 (#45260)

### [89860fb](https://github.com/sgl-project/sglang/commit/89860fbd2e3cf460c0968435670b7fdef6ab5529)

- **作者**: sogalin_codegen
- **时间**: 2026-10-20T17:08:39Z
- **提交信息**: [Fix] [AMD] gpt-oss: support EP for gfx1250 W4A8 MXFP4 MoE (#45365)

### [7591118](https://github.com/sgl-project/sglang/commit/759111879457fb5acd171284dc9a8a1e6bf8c77d)

- **作者**: Michael
- **时间**: 2026-10-20T16:12:06Z
- **提交信息**: [Fix] [AMD] grok: accept allow_patterns_overrides in presharded _prepare_weights patch (#45217)

### [eb4b167](https://github.com/sgl-project/sglang/commit/eb4b167d2749840eae18167fe9e0a608308e45aa)

- **作者**: Shunkangz
- **时间**: 2026-10-20T14:48:43Z
- **提交信息**: [Feat] KVShard: PD transfer and e2e test (#38473)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Zhangheng <hzh0425@apache.org>

### [7656071](https://github.com/sgl-project/sglang/commit/76560713092795ac051d0411574c3a8d73145c2f)

- **作者**: Vinsmoke86
- **时间**: 2026-10-20T14:19:07Z
- **提交信息**: [Feat] platform: Add initial T-HEAD SAIL platform support [2/N] (#43826)

Co-authored-by: Zhangheng <hzh0425@apache.org>
Co-authored-by: yzshi <163985193+Yunzshi310@users.noreply.github.com>

### [e262b44](https://github.com/sgl-project/sglang/commit/e262b44eef1f2bf83e34345276e2bb91a086587e)

- **作者**: pllimax
- **时间**: 2026-10-20T13:35:49Z
- **提交信息**: [CI] [NPU] tests: Replace DeepSeek-V2-Lite-W8A8 cases with Moonlight (#43063)

### [952c63b](https://github.com/sgl-project/sglang/commit/952c63b1bb851863583b466889d412f75c82854b)

- **作者**: Shangming Cai
- **时间**: 2026-10-20T13:33:42Z
- **提交信息**: [CI] sgl-router: Gate on live run-ci label so /tag-and-rerun-ci can start the tiers (#45383)

### [10d5293](https://github.com/sgl-project/sglang/commit/10d5293546faf6469ebe7b924ecf5d9519e14c6f)

- **作者**: Jensen
- **时间**: 2026-10-20T13:33:08Z
- **提交信息**: [Perf] [NPU] glm5.2: Support dynamic INT8 MLAProlog for attention (#43469)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [3bf4cbc](https://github.com/sgl-project/sglang/commit/3bf4cbc6cf18b539d88c08c17cb97d82ec82c951)

- **作者**: Jensen
- **时间**: 2026-10-20T13:30:01Z
- **提交信息**: [Perf] [NPU] mem_cache: Increase GLM-5.2-W4A8C8 KV cache capacity with compact DSA indexer allocation (#44436)

### [aa91108](https://github.com/sgl-project/sglang/commit/aa91108f64717b73ccb1993792d31984887ae103)

- **作者**: gjsheu
- **时间**: 2026-10-20T13:26:30Z
- **提交信息**: [Fix] [NPU] glm5.2: support pcp v2 with interleave & zigzag (#40165)

### [ee2f95a](https://github.com/sgl-project/sglang/commit/ee2f95a52262684a4981e7b72b5405a91baa1312)

- **作者**: gjsheu
- **时间**: 2026-10-20T13:25:37Z
- **提交信息**: [Fix] [NPU] glm5.2-mtp: L2 cache adaptation (#41642)

### [df13d5d](https://github.com/sgl-project/sglang/commit/df13d5dce31abfeff0e701a62e8c39a136758e6c)

- **作者**: lixiufei-leo
- **时间**: 2026-10-20T12:56:14Z
- **提交信息**: [Feat] sgl-router: Route prefill buckets by uncached tokens (#45103)

Co-authored-by: Xiufei Li <294029388+lixiufei-leo@users.noreply.github.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [eae134d](https://github.com/sgl-project/sglang/commit/eae134d61fa9ce2e532d7543062cb9c6a7e200d7)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-20T11:48:59Z
- **提交信息**: [Test] kernels: Import silu_and_mul_contig_post_quant from its new home (#45368)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [07eb671](https://github.com/sgl-project/sglang/commit/07eb671b6af092a4f9344365508ebdc56de74aef)

- **作者**: Kurkur
- **时间**: 2026-10-20T11:19:34Z
- **提交信息**: [Perf] [NPU] attn: add not needs_cpu_seq_lens for dsa modules (#38461)

### [ca473ef](https://github.com/sgl-project/sglang/commit/ca473ef3e437461241de0f3f966406b3a5bd403b)

- **作者**: Shijin Zhang
- **时间**: 2026-10-20T11:11:40Z
- **提交信息**: [Feat] glm-5.3: Render GLM-5.3 and GLM-5.3-Flash chat prompts with a Python chat template (#45154)

Signed-off-by: Shijin Zhang <75300765+Dovis01@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [800e60e](https://github.com/sgl-project/sglang/commit/800e60e3457108a9f7cfe8c27d37bdd28ca611bf)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-10-20T11:05:17Z
- **提交信息**: [Fix] moe: Publish a server config in the CUTLASS runner dispatch-format and placement tests (#45376)

### [306ccf6](https://github.com/sgl-project/sglang/commit/306ccf6f57bcd6efc9edc626e39a9673e22cb9d6)

- **作者**: Yuxuan Zhou
- **时间**: 2026-10-20T10:05:42Z
- **提交信息**: [Perf] spec: Let the FlashAttention backend capture the draft-extend CUDA graph (#40762)

### [9db58ab](https://github.com/sgl-project/sglang/commit/9db58ab547516435b544ae050dd6c2f91b52bcf3)

- **作者**: Sihan Chen
- **时间**: 2026-10-20T10:00:39Z
- **提交信息**: [Fix] eplb: Fix Qwen3 MoE output corruption after EPLB rebalance (#39580)

Signed-off-by: Spycsh <sihan.chen@intel.com>

### [a70b1b7](https://github.com/sgl-project/sglang/commit/a70b1b73d343ff1c18e989e8c18bae69c1ba4570)

- **作者**: aplus
- **时间**: 2026-10-20T09:57:16Z
- **提交信息**: [Fix] tracing: Fix OTel tracing context lost in multi-tokenizer router processes (#38211)

Co-authored-by: Ma <T9FOPWP@cn.vwgroup.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [16eb87c](https://github.com/sgl-project/sglang/commit/16eb87c06fca4b14f91ddc1503e2353f70094ff2)

- **作者**: Muqi Li
- **时间**: 2026-10-20T09:11:06Z
- **提交信息**: [Fix] openai: distinguish s3 served-model-name from LoRA adapter syntax (#44450)

Signed-off-by: Muqi Li <muqi1029@gmail.com>
Signed-off-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [2229345](https://github.com/sgl-project/sglang/commit/2229345dff2753423de5d8f6cb2513824a11c18d)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-20T08:50:58Z
- **提交信息**: [Doc] kda_kernels: Point the SM121 QSA kernel provenance at its SGLang PR (#45359)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f8fd41c](https://github.com/sgl-project/sglang/commit/f8fd41c36e493ec762e60f447c50c88fb8af3ec1)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-10-20T08:41:16Z
- **提交信息**: [Perf] moe: Extend FlashInfer CUTLASS MoE autotune coverage to prefill chunks (#43363)

### [06314dc](https://github.com/sgl-project/sglang/commit/06314dc2e8d34ffd54fb1109e8526bc22b835c35)

- **作者**: Ma Mingfei
- **时间**: 2026-10-20T08:40:13Z
- **提交信息**: [CI] [Intel] tests: Remove CPU monitor and crash-dump tests from Xeon CI (#45281)

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [0788f1f](https://github.com/sgl-project/sglang/commit/0788f1fdd01a059dbaa31a80b120c8f584fdc623)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-20T08:35:11Z
- **提交信息**: [Refactor] kernels: Register agent-generated kernels under their KDA / Cake backend (#45277)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fdd89d1](https://github.com/sgl-project/sglang/commit/fdd89d182a82fc78cc2c1b6dd0251d5bb7893172)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-20T08:20:46Z
- **提交信息**: [Fix] moe: add uses_expert_location to MegaMoE test fixtures (#45350)

Signed-off-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [78185f4](https://github.com/sgl-project/sglang/commit/78185f4b3f565cbe0fec20d71bb5deb372428e80)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-20T07:38:45Z
- **提交信息**: [Fix] [NVIDIA] modelopt-nvfp4: Read w13 global scales in the TRT-LLM [up, gate] order (#44858)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [1739d96](https://github.com/sgl-project/sglang/commit/1739d962a45d1c8ecd10cda5a7e387b5cc18c066)

- **作者**: XXXXRT666
- **时间**: 2026-10-20T07:35:29Z
- **提交信息**: [Refactor] [Apple] MLX: Use Native Extension Builder for Metal Kernels (#44367)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [15e8e68](https://github.com/sgl-project/sglang/commit/15e8e687dbd7d3c252595bdb3140e89af21c9eb6)

- **作者**: Shuwen Wang
- **时间**: 2026-10-20T07:02:43Z
- **提交信息**: [Chore] environ: Remove retired unified radix tree environment variable (#45090)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1290
- **最后更新**: 2026-10-21T02:58:48Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 1. 主要更新类型

- **功能新增为主**：为 Qwen-Image 2.1 模型提供完整支持，覆盖缓存（Prefix KV Cache）、张量并行（TP）、上下文并行（CP）、文本编码器并行（TE-P）、VAE 并行（VAE-P）五大能力。
- 附带**示例新增、文档更新、Bug 修复**（修正示例参数与配置问题），以及针对该模型的 CPU 回归测试体系。

## 2. 关键变更点与项目方向的关系

- 新增 `QwenImage21PatchFunctor`：由于 cache-dit 会将模型的 `transformer_blocks` 替换为统一缓存包装器，而 Qwen-Image 2.1 的原始前向依赖 `block.attn.processor` 等包装器未暴露的接口，因此复制并改写了 transformer 前向，在每个 block 内解析各自的层缓存，同时兼顾 CP 分片。
- 新增 `QwenImage21` 的 `BlockAdapter`（`ForwardPattern.Pattern_3`），并基于"注册表按类名前缀首个匹配"的规则注册在 `QwenImage` 之前，`has_separate_cfg` 跟随管线默认值以正确统计 CFG 步数。
- 新增 TP planner（仅切分权重，保持 `attn.heads` 完整以保证 `head_dim` 推导正确）、CP planner（仅支持 Ulysses：文本/条件前缀全量复制，仅对目标 token 分片以维持 block-causal 有效性，拒绝 Ring 等方案）、`AutoencoderKLQwenImage21` VAE-P planner（复用 tiled 编解码）。
- 提供 `modular_blocks_factory` 兜底方案，兼容缺少 `modular_model_index.json` 的检查点。
- 以上均直接对应 README 中"Cache、Parallelism、Quantization、CPU Offload"的核心定位。

## 3. 对项目的影响与潜在意义

- 显著扩大模型覆盖面，把当前热门的 Qwen-Image 2.1（含 Turbo）纳入推理加速生态，有望提升用户下载量与社区采用度。
- 修复了一个**静默错误**：未打补丁时循环只执行一次且所有 32 层共享第 0 层的 K/V，不崩溃但输出退化为彩色噪声——这类"看似正常实则错误"的问题最危险，本次以补丁函数从根上规避。
- 完善的 CPU 回归测试（逐层缓存、前向等价性、state_dict 键、CP 拒绝策略、单 rank 下 CP 与原生 processor 一致性）为后续类似模型接入建立了可复用的验证范式。

## 4. 值得关注的技术点

- **前缀 KV Cache 与层索引缓存的冲突**：模型按 transformer block 索引维护文本/条件前缀 KV，而缓存包装器替换了模块容器，需要自定义前向逐层解析缓存。
- **TP 下 `head_dim` 的推导约束**：注意力处理器通过 `inner_dim // heads` 计算 `head_dim`，因此 TP 只能切权重而不能切 heads。
- **CP 分片与 block-causal 有效性的平衡**：前缀全量复制、仅目标 token 分片，是保持注意力因果分段正确的关键设计。
- 注册表"首个类名前缀匹配"的机制要求新模型注册顺序先于同前缀的旧模型，属于易踩的工程细节。

## 5. 对项目发展的意义

结合 README，cache-dit 的目标是成为面向 DiT 的 PyTorch 原生推理引擎，本次提交正是该路线的典型推进：将缓存、并行、量化/卸载能力横向扩展到新的主流 DiT 系架构，并配套基准网格（Turbo 8-step benchmark）、六组生成示例（base/turbo × t2i/edit 及模块化变体）和 `--ws/--rdt` 等工程化参数支持，大幅降低了用户的接入与验证门槛。作为一次合并的大功能 PR（#1128），它既强化了项目的模型矩阵与正确性保障，也为后续更多"前缀缓存 + 模块替换"类模型的适配沉淀了架构模板，整体推动项目向更成熟、更广泛可用的推理引擎演进。

## 详细提交记录

### [c5951a0](https://github.com/vipshop/cache-dit/commit/c5951a00c2f91bec13db71e0f073800e2e40247b)

- **作者**: DefTruth
- **时间**: 2026-10-20T09:24:11Z
- **提交信息**: Support Qwen-Image 2.1 (cache, TP, CP, TE-P, VAE-P) (#1128)

* Support Qwen-Image 2.1 (cache, TP, CP, TE-P, VAE-P)

The model keeps a prefix (text and condition-image) KV cache indexed by the
transformer block, while cache-dit swaps `transformer_blocks` for a single
cached wrapper. Without a patch the loop runs once with `index_block == 0` and
all 32 layers share layer 0's K/V: no crash, but the image collapses to color
noise. The new `QwenImage21PatchFunctor` copies the transformer forward (the
original also reads `block.attn.processor`, which the wrapper does not expose),
resolves the per-layer cache inside each block, and carries the optional CP
sharding in the same forward.

- `QwenImage21` BlockAdapter with `ForwardPattern.Pattern_3`, registered ahead
  of `QwenImage` because the registry matches the first class-name prefix;
  `has_separate_cfg` follows the pipeline default so a single forward per step
  is not accounted as half a CFG step
- TP planner that shards weights only: the attention processor derives
  `head_dim = inner_dim // heads`, so `attn.heads` must stay at its full value
- CP planner (Ulysses only): the text/condition prefix is replicated on every
  rank and only the target tokens are sharded, which keeps the block-causal
  segments valid; Ring, `ulysses_anything` and the flex processor are rejected
- `AutoencoderKLQwenImage21` VAE-P planner, reusing the tiled encode/decode
  with the decoder's `first_chunk` and output clamp
- six generate examples (base/turbo x t2i/edit plus modular variants) and a
  `modular_blocks_factory` escape hatch for checkpoints without
  `modular_model_index.json`
- docs and CPU regression tests (per-layer cache, forward equivalence, state_dict
  keys, CP planner rejections, CP == stock processor at one rank)

* docs(assets): add Qwen-Image 2.1 Turbo 8-step benchmark grid

* feat(examples): honour --ws/--rdt for Qwen-Image 2.1, add modular edit examples

* fix(examples): give the Qwen-Image 2.1 modular edit example a CFG guider

* docs: shorten the Qwen-Image 2.1 row and count its variants

* docs(assets): add Qwen-Image 2.1 image-edit panel

* Update README.md

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 94489
- **最后更新**: 2026-10-21T03:12:52Z

## 提交统计

- **昨日提交总数**: 62
- **提交者数量**: 39
- **主要提交者**: Jhao-Ting Chen, qli88, zexplorerhj

## AI分析总结

# vLLM 昨日提交分析（共 62 条提交）

## 一、主要更新类型分布

- **Rust 前端对齐**：约 15 条，占比最高，集中对齐 Python 版行为
- **CI/构建优化**：约 13 条，包括分片、缓存释放、ROCm 测试调整及稳定性修复
- **Bug 修复**：约 12 条，覆盖分布式、模型、量化、Pooling、前端接口等
- **ROCm 硬件支持**：约 8 条，AMD GPU 深度优化
- **文档更新**：约 6 条，集中于 NVIDIA AgentX 部署指南
- **MyPy 类型检查**：3 条；**性能优化**：约 4 条，涉及 Mamba、Multimodal、注意力后端

## 二、关键变更点

**1. Rust 前端大规模对齐 Python 行为（最突出主题）**
Bugen Zhao 主导超过 15 个提交，系统性地让 Rust 前端在请求字段验证（拒绝静默丢弃）、参数边界（logit_bias 钳制、JSON 嵌套深度限制）、错误处理（501 而非 404）、generation_config 继承、prompt 截断等方面与 Python 实现保持一致，标志着 **Rust 前端进入生产就绪的精细化打磨阶段**，目标是让用户平滑迁移而不改变行为。

**2. ROCm/AMD 平台深度优化**
包括 AITER v1.26.0 升级、fp8 MoE 模块预构建、GLA gate GEMM 融合、MXFP8 共享专家融合、RDNA 调优修复等，AMD 持续投入将 ROCm 推向与 CUDA 同等级别的支持水平。

**3. NVIDIA AgentX 部署文档体系**
多条 Kimi-K3、MiniMax-M3、DeepSeek-V4.1-Flash 的 GB200/GB300/B200/B300 配置文档，反映 **AgentX 智能体推理场景正成为 NVIDIA 重点推广方向**。

**4. CI 基础设施与稳定性**
包括自动分片、GPU 显存释放、LM Eval 模型间页缓存清理，以及因 Transformers 5.20 上游变更导致不稳定而临时跳过 SmolVLM 对比测试的防御性修复，及时屏蔽外部依赖噪声以保障迭代速度。

**5. Bug 修复与 API 契约完善**
除 MoE 路由的 Cooperative TopK 溢出精确性修复、分布式 Symmetric collective 输出保留等精度级修复外，还修复了前端 derender 后未按需返回 prompt token ID 的缺陷，保障计费、日志与 prompt caching 的数据正确性。

## 三、项目影响与潜在意义

- **Rust 前端成熟度大幅提升**：与 Python 的 API 兼容性收尾接近完成，双前端战略进入关键节点，Rust 前端未来可能成为默认入口，带来更低启动延迟与内存开销。
- **多硬件生态加速**：AMD 与 NVIDIA 提交交替出现，体现 vLLM 作为中立推理引擎的核心定位，降低用户对单一厂商的依赖。
- **模型适配广度扩展**：DiffusionGemma、PaddleOCR-VL、Pixtral、MiMo-V2、Ling FP8 等覆盖多模态全场景。
- **生产可信度夯实**：持续的小修复累积形成稳定的 API 契约，是被企业广泛集成的前提；AI 工具（Claude、Cyrus）联署常态化，反映 AI 辅助开发在该项目中的普及。

## 四、值得关注的技术点

1. **Cooperative TopK 候选溢出精确性修复**（#59645）：影响 MoE 路由正确性的潜在精度级 bug。
2. **Symmetric collective 输出保留**（#58154）：多 GPU 分布式通信正确性关键。
3. **trtllm-gen 用于 FlashInfer DCP prefill**（#62029）：注意力后端新集成路径，可能提升 prefill 性能。
4. **Mamba2 Triton SSD prefill 主机开销优化**（#61497）：缓解长上下文场景 CPU 瓶颈。
5. **MyPy 分批治理**：系统性提升类型安全，降低后期重构风险。
6. **外部依赖脆弱性**：SmolVLM 测试跳过属权宜之计，需关注是否有正式适配 Transformers 新版本的跟进提交，否则可能掩盖真实兼容性问题。

## 五、对项目发展方向的影响

vLLM 使命是 "Easy, fast, and cheap LLM serving for everyone"，昨日提交从三个维度强化该目标：**Easy**——Rust 前端 API 精确对齐降低迁移门槛，AgentX 文档覆盖主流硬件组合，API 返回值完整可预期；**Fast**——ROCm 性能融合、Mamba 开销优化、注意力后端集成持续推进推理上限，CI 分片与缓存优化提升迭代速度；**Cheap**——CI 效率优化降低维护成本，多硬件支持让用户选择性价比更高的硬件。总体而言，vLLM 正在"横向扩展硬件/模型覆盖"与"纵向深化工程质量"两个维度同步推进，Rust 前端的集中投入是当前最具战略意义的方向，而持续的维护性修复则是其保持生产可信度、吸引企业采用的底层保障。

## 详细提交记录

### [7e3d559](https://github.com/vllm-project/vllm/commit/7e3d55956577605838e9babcba84dce354b0b78c)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-20T23:04:59Z
- **提交信息**: [Frontend] DiffusionGemma joint reads on /v1/systemone and /v1/decisions, images on /v1/systemone (#62437)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [b1ab16c](https://github.com/vllm-project/vllm/commit/b1ab16c548f114a40c0451de0d6c18d4d832e1de)

- **作者**: Josh Schell
- **时间**: 2026-10-20T22:36:20Z
- **提交信息**: [ROCm] Bump AITER to v1.26.0 (#62486)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [1e330b1](https://github.com/vllm-project/vllm/commit/1e330b1019b8739ede6454acb600cb8a9a7b5fff)

- **作者**: Adarsh Shirawalmath
- **时间**: 2026-10-20T22:30:21Z
- **提交信息**: [MyPy][5/N] Fix mypy errors in hard tests/ dirs and enforce follow-imports=silent (#62142)

Signed-off-by: adarshxs <adarsh.shirawalmath@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3a1bd83](https://github.com/vllm-project/vllm/commit/3a1bd8347af3ec61d89add3330cf210ce7c12b6d)

- **作者**: nien-hui
- **时间**: 2026-10-20T22:28:13Z
- **提交信息**: [MyPy] Fix mypy errors in easy tests/v1/kv_connector files (kv-A) (#55542)

Signed-off-by: paul <paulqwer.cs13@nycu.edu.tw>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [612e928](https://github.com/vllm-project/vllm/commit/612e928016e2cfe28da95fc03ed894aceaf18299)

- **作者**: Roberto L. Castro
- **时间**: 2026-10-20T22:06:55Z
- **提交信息**: [Bugfix] Make cooperative TopK exact on candidate overflow (#59645)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [88262cf](https://github.com/vllm-project/vllm/commit/88262cf7d172739be88ef1e930aaa50d7ff4287f)

- **作者**: stefankoncarevic
- **时间**: 2026-10-20T21:57:06Z
- **提交信息**: [CI] Release the previous checkpoint's page cache between LM Eval models (#61415)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [0f30006](https://github.com/vllm-project/vllm/commit/0f300062671c3485035aff157757cc8efb50f9a6)

- **作者**: qli88
- **时间**: 2026-10-20T21:55:16Z
- **提交信息**: [ROCm][CI][Bug] Remove padding from AITER output for quantization/tes… (#62735)

Signed-off-by: Qiang Li <qiang.li2@amd.com>

### [af31693](https://github.com/vllm-project/vllm/commit/af316933123da1ef15ff879bdbeda28ef4f52ae3)

- **作者**: Zaoyi Zheng
- **时间**: 2026-10-20T21:48:09Z
- **提交信息**: [Distributed] Include NCCL's last error in pynccl error messages (#59898)

Signed-off-by: Roy Zheng <39311511+roy6n23@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [56e67b4](https://github.com/vllm-project/vllm/commit/56e67b46a3dd987824335683d9adb8523bc28d82)

- **作者**: hshrivastava-droid
- **时间**: 2026-10-20T21:38:32Z
- **提交信息**: [Doc] Sync Kimi-K3 GB200 AgentX profiles with InferenceX #4322 (#62761)

Signed-off-by: Ankur Singh <ankusingh@nvidia.com>
Signed-off-by: hshrivastava-droid <hshrivastava@nvidia.com>
Co-authored-by: Ankur Singh <ankusingh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [9d4192a](https://github.com/vllm-project/vllm/commit/9d4192aaa1071e64553412f874d2159d6a2f1522)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-20T21:16:56Z
- **提交信息**: [Bugfix][DeepSeek V4] Load redundant EPLB expert slots (#59611)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [c693645](https://github.com/vllm-project/vllm/commit/c6936455a97d9dd580551f24121177c223fe1ab3)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-20T21:12:31Z
- **提交信息**: [CI] Add Nightly to optional Buildkite step labels (#61186)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9da5f2d](https://github.com/vllm-project/vllm/commit/9da5f2d3103df460dfca53df4ab4884def5c935f)

- **作者**: eky-amd
- **时间**: 2026-10-20T20:04:09Z
- **提交信息**: [ROCm] Enable the rms_norm_gated custom op by default (Qwen3.8-27B) (#60250)

Signed-off-by: Ethan Ky <ethan.ky@amd.com>
Signed-off-by: eky-amd <ethan.ky@amd.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [09fd027](https://github.com/vllm-project/vllm/commit/09fd027217648768c417261ab9a90a3149649ad2)

- **作者**: Omar Muhammad
- **时间**: 2026-10-20T20:03:06Z
- **提交信息**: [ROCm][Perf][Kimi-K3] Fuse the GLA gate GEMM and the MLA FP8 prefill q/k/v prep (#59634)

Signed-off-by: Omar Muhammad <omar.muhammad@amd.com>
Signed-off-by: Nicholas Susanto <nicholas.susanto@amd.com>
Co-authored-by: Nicholas Susanto <nicholas.susanto@amd.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [70a609a](https://github.com/vllm-project/vllm/commit/70a609ac403df4d2e8301b57a3d178f8a5980af2)

- **作者**: Ankur Singh
- **时间**: 2026-10-20T19:48:27Z
- **提交信息**: [Doc] Document MiniMax-M3 GB200 Dynamo AgentX profile (#62543)

Signed-off-by: Ankur Singh <ankusingh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [6083fde](https://github.com/vllm-project/vllm/commit/6083fdeaa26c2e0c1ba4a4f85827babfa972f6fb)

- **作者**: Ankur Singh
- **时间**: 2026-10-20T19:45:34Z
- **提交信息**: [Doc] Document the DeepSeek-V4.1-Flash B200 AgentX profile in the guide and command builder (#62541)

Signed-off-by: Ankur Singh <ankusingh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [005cef0](https://github.com/vllm-project/vllm/commit/005cef040a283aac2b156eccb12a2ab5d10f3157)

- **作者**: djramic
- **时间**: 2026-10-20T19:20:20Z
- **提交信息**: [CI][ROCm] Remove MI300 Model Runner V2 steps (#62731)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [7b569ec](https://github.com/vllm-project/vllm/commit/7b569ec8953cf8099638a6d2ee1e915b75867c3a)

- **作者**: Gagandeep Kang
- **时间**: 2026-10-20T18:29:35Z
- **提交信息**: [Attention] Use trtllm-gen for the FlashInfer DCP prefill context pass (#62029)

Signed-off-by: Gagandeep Kang <gagandeep.kang@cohere.com>
Signed-off-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [8122776](https://github.com/vllm-project/vllm/commit/8122776fba2dcfae2973a0659db2da6ac688306b)

- **作者**: jeffnvidia
- **时间**: 2026-10-20T18:21:37Z
- **提交信息**: [Bugfix][Distributed] Preserve symmetric collective outputs (#58154)

### [88077b7](https://github.com/vllm-project/vllm/commit/88077b746cb21e1ad5b9f25d9cae613814e892c3)

- **作者**: jack
- **时间**: 2026-10-20T18:13:13Z
- **提交信息**: [Bugfix] Reject mixed structured output backends during validation (#49625)

Signed-off-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>
Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [f1dbfef](https://github.com/vllm-project/vllm/commit/f1dbfef79973d0f8d05be56e8614db0409e3d7d3)

- **作者**: Nick Hill
- **时间**: 2026-10-20T17:41:06Z
- **提交信息**: [Core] Don't apply spec decode async scheduling fallbacks with MRV2 (#62521)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [76c9e23](https://github.com/vllm-project/vllm/commit/76c9e23ce7dd4646616e3b282d6263cc47ac17a6)

- **作者**: LiRenHao
- **时间**: 2026-10-20T17:15:07Z
- **提交信息**: [Docs] Use release tags for documentation source links (#62709)

Signed-off-by: stdlibstring <159357369p@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0ca531b](https://github.com/vllm-project/vllm/commit/0ca531ba64c61af32accb3b52226e8d819c6a49b)

- **作者**: ssingh231219
- **时间**: 2026-10-20T17:14:15Z
- **提交信息**: [Perf][Model] Support torch.compile for the PaddleOCR-VL vision encoder (#61838)

Signed-off-by: ssingh231219 <simran.singh@artificialy.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [b272cff](https://github.com/vllm-project/vllm/commit/b272cff368b3a0c733859ab308f7123291cf1489)

- **作者**: Harry Mellor
- **时间**: 2026-10-20T16:31:45Z
- **提交信息**: [Bugfix] Read ColPali hidden size from vlm_config (#62714)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [165152f](https://github.com/vllm-project/vllm/commit/165152f6680fc8a179fff5980f6f9e9ef61c439b)

- **作者**: Ankur Singh
- **时间**: 2026-10-20T16:08:58Z
- **提交信息**: [Doc] Fix Kimi-K3 GB300 disaggregated selector and guide gaps (#62710)

Signed-off-by: Ankur Singh <ankusingh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6e780d1](https://github.com/vllm-project/vllm/commit/6e780d14cdf0ea22bf91e199e4a355373cab37f3)

- **作者**: Aarushi Jain
- **时间**: 2026-10-20T15:32:05Z
- **提交信息**: [CI][ROCm] Use AITER prebuilt fp8 MoE modules when inter dim is 256 aligned (#62032)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>

### [4964e44](https://github.com/vllm-project/vllm/commit/4964e44825499f1365e1bd5fd0644147c91dba2e)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T15:18:04Z
- **提交信息**: [Rust Frontend] Report error type and code like Python (#62663)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [82b7dad](https://github.com/vllm-project/vllm/commit/82b7dad5e315040219ec657398d6197010121d15)

- **作者**: CharlesWu
- **时间**: 2026-10-20T14:52:43Z
- **提交信息**: [Test][UMBP][2/10] Add shared connector contract coverage (#61790)

Signed-off-by: CharlesWu <Charles.Wu@amd.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [4a30738](https://github.com/vllm-project/vllm/commit/4a30738d212f389cb1387f53441be7d6d19fefc0)

- **作者**: amd-xavierwang
- **时间**: 2026-10-20T14:47:50Z
- **提交信息**: [ROCm][benchmark][perf] fix moe tuning script for RDNA (#41197)

Signed-off-by: xawang <xawang@amd.com>

### [11a8d57](https://github.com/vllm-project/vllm/commit/11a8d571d2ff385615a15caabf8f299c9fc48816)

- **作者**: stefankoncarevic
- **时间**: 2026-10-20T14:31:53Z
- **提交信息**: [CI][AMD] Deselect distributed tests in the MI300 Model Executor step (#62680)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [c0fe6c4](https://github.com/vllm-project/vllm/commit/c0fe6c49996b61df25da4a1d8812e7534becaf9e)

- **作者**: zexplorerhj
- **时间**: 2026-10-20T14:29:06Z
- **提交信息**: [Model] Support updated Ling FP8 quantization exclusions and MLA gates (#62681)

Signed-off-by: zexplorerhj <zhjoneson@163.com>
Co-authored-by: Codex <noreply@openai.com>

### [92e3790](https://github.com/vllm-project/vllm/commit/92e379001c20cc88cb993604376ba637fdca2ce9)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:21:36Z
- **提交信息**: [Rust Frontend] Cap request token histogram buckets at max_model_len (#62644)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fbc3555](https://github.com/vllm-project/vllm/commit/fbc35552875a1d5f0da25cd66c156fbc8c47e682)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:21:23Z
- **提交信息**: [Rust Frontend] Return 501 instead of 404 for Python-only routes (#62432)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3593d8e](https://github.com/vllm-project/vllm/commit/3593d8e5ba48176d9163f449a1b771ce353809e8)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:21:09Z
- **提交信息**: [Rust Frontend] Emit transfer params at the top level of render output (#62429)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3eb3145](https://github.com/vllm-project/vllm/commit/3eb3145bd0f56e15667a3783044aa5720061f277)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:20:55Z
- **提交信息**: [Rust Frontend] Accept null for nullable request booleans (#62662)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [654f781](https://github.com/vllm-project/vllm/commit/654f78177a901b1dec5e8676242efc7d5df7e6b3)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:20:42Z
- **提交信息**: [Rust Frontend] Cap structured-output JSON nesting at 64 levels (#62661)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [68098c7](https://github.com/vllm-project/vllm/commit/68098c7c4fb534f00b48e68311dde8854611ab8e)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:19:55Z
- **提交信息**: [Rust Frontend] Accept empty stream_options without streaming (#62643)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [97a82d3](https://github.com/vllm-project/vllm/commit/97a82d3c92e65429f6571df01253e573f90fbf06)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:19:38Z
- **提交信息**: [Rust Frontend] Truncate prompts against max_model_len like Python (#62642)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [03dd81a](https://github.com/vllm-project/vllm/commit/03dd81a58466aa5aace4e82a5c0dcca52069c86e)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:19:22Z
- **提交信息**: [Rust Frontend] Accept top_logprobs=0 without logprobs (#62428)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [52712d4](https://github.com/vllm-project/vllm/commit/52712d425909a27e62f6e67b62da9202431fa78e)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:19:02Z
- **提交信息**: [Rust Frontend] Validate cache_salt like Python (#62427)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1466f37](https://github.com/vllm-project/vllm/commit/1466f372a3b332140ca32eff5d19c910969c5f80)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:18:46Z
- **提交信息**: [Rust Frontend] Inherit presence and frequency penalties from generation_config (#62426)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [50e2296](https://github.com/vllm-project/vllm/commit/50e2296c2398a243b57b8bd683ccb61fa6014357)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:18:30Z
- **提交信息**: [Rust Frontend] Clamp logit_bias to [-100, 100] (#62425)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [255e3a3](https://github.com/vllm-project/vllm/commit/255e3a310c1b72a8498ffeb99367cd748d2a1688)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:18:11Z
- **提交信息**: [Rust Frontend] Reject silently dropped request fields on chat, completions, and generate (#62434)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [29a26e5](https://github.com/vllm-project/vllm/commit/29a26e5b0e908ab9d7147a17b28c53bf4a9753da)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:13:21Z
- **提交信息**: [Rust Frontend] Support --trust-request-chat-template (#62673)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5528685](https://github.com/vllm-project/vllm/commit/5528685552edde717d907ee14eae189139b40f35)

- **作者**: Bugen Zhao
- **时间**: 2026-10-20T14:13:05Z
- **提交信息**: [Rust Frontend] Make unhandled `vllm serve` frontend flags explicit (#62431)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f0c5014](https://github.com/vllm-project/vllm/commit/f0c50148a211519f62c4ef40a4f7d75dff6827f4)

- **作者**: Bruno Volpato
- **时间**: 2026-10-20T14:10:42Z
- **提交信息**: [Bugfix][Pooling] Ignore token stream intervals for pooling (#55226)

Signed-off-by: bvolpato <brunocvcunha@gmail.com>
Signed-off-by: Bruno Volpato <brunocvcunha@gmail.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [a6c898e](https://github.com/vllm-project/vllm/commit/a6c898e2a9db6c8ee49a9edc5751f809749f3a5b)

- **作者**: stefankoncarevic
- **时间**: 2026-10-20T13:38:16Z
- **提交信息**: [CI][AMD] Shard the MI300 V1 Spec Decode step (#62686)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [5285b9b](https://github.com/vllm-project/vllm/commit/5285b9b8646d6d0e8b869c9f5c6d277ccfce637b)

- **作者**: Jared Wen
- **时间**: 2026-10-20T12:26:14Z
- **提交信息**: [Bugfix][Model] Build Pixtral vision position ids on device (#62648)

Signed-off-by: Jared Wen <w13431838023@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7921865](https://github.com/vllm-project/vllm/commit/79218659a6d7da7c2786e65c0caa0ad505e427d5)

- **作者**: James Meadlock
- **时间**: 2026-10-20T12:18:51Z
- **提交信息**: [Bugfix][Model] MiMo-V2: skip fused fp8 qkv_proj tensors for layers the model does not have (#58184)

Signed-off-by: James Meadlock <jmeadlock@users.noreply.github.com>
Co-authored-by: James Meadlock <jmeadlock@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [e7e8deb](https://github.com/vllm-project/vllm/commit/e7e8deb86cd69de29de13c43a6db0f4a428e43f3)

- **作者**: Liu Jinhao
- **时间**: 2026-10-20T12:16:36Z
- **提交信息**: [Perf][Multimodal] Keep audio encoder padding masks broadcastable (#62469)

Signed-off-by: Liu Jinhao <136283190+Loken-Lau@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [cc8a41f](https://github.com/vllm-project/vllm/commit/cc8a41f328422e76697431e47993ee839489f572)

- **作者**: Satvik Shrivas
- **时间**: 2026-10-20T11:51:15Z
- **提交信息**: [MyPy][4/N] Fix mypy errors in medium-hard tests/ dirs (#55485)

Signed-off-by: Satvik Shrivas <44926681+theSatvik@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [8407bc0](https://github.com/vllm-project/vllm/commit/8407bc0bb6b0061dacb731ae3cc54b6035f112b3)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-20T11:27:16Z
- **提交信息**: [CI][LoRA] Release punica test GPU memory before later engine tests (#62672)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b8e9001](https://github.com/vllm-project/vllm/commit/b8e9001bf9568c801985889deff34d3b9fe6d0b0)

- **作者**: aoshen02
- **时间**: 2026-10-20T10:00:14Z
- **提交信息**: [Rust][Frontend] Return routed experts from the generate route (#61949)

Signed-off-by: Ao Shen <aoshen@inferact.ai>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [39568e2](https://github.com/vllm-project/vllm/commit/39568e2ec76aa9107718d1be8adf43cebd84e83c)

- **作者**: Juntian Liu
- **时间**: 2026-10-20T09:52:35Z
- **提交信息**: [Doc] Document DeepSeek-V4.1-Flash B300 aggregate AgentX config (#62670)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0d00d8b](https://github.com/vllm-project/vllm/commit/0d00d8b9cf2b1961b436b6f58f1cd4194d57623b)

- **作者**: wenjinhust
- **时间**: 2026-10-20T09:27:06Z
- **提交信息**: [CI][Bugfix] ColPali miss hidden_size (#62627)

Signed-off-by: wenjinhust <wenjin.sh@huawei.com>

### [e2d2680](https://github.com/vllm-project/vllm/commit/e2d2680417432b80986a36d456e3d79173ee1a45)

- **作者**: Thang Nguyen
- **时间**: 2026-10-20T09:15:38Z
- **提交信息**: [CI] Shard E2E Scheduling, Benchmarks CLI and six AMD mirrors automatically (#62039)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [87fa712](https://github.com/vllm-project/vllm/commit/87fa712793418ff33a471f6a068ab759d9da54b8)

- **作者**: Thang Nguyen
- **时间**: 2026-10-20T08:55:28Z
- **提交信息**: [CI] Shard (H200 MIG 35GB / MI355 DPX) Multimodal Models (Standard) 4 automatically (#62562)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b9c8bd5](https://github.com/vllm-project/vllm/commit/b9c8bd5140238510737ea43b264311561210e3b4)

- **作者**: Thang Nguyen
- **时间**: 2026-10-20T08:55:15Z
- **提交信息**: [CI] Shard MTEB, DFlash Nightly, MoE Refactor DP and Entrypoints LLM automatically (#61999)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e4a676c](https://github.com/vllm-project/vllm/commit/e4a676cdc22f99e808093a87ff8509a6089d392d)

- **作者**: Jhao-Ting Chen
- **时间**: 2026-10-20T08:28:35Z
- **提交信息**: [Perf][Mamba] Reduce host overhead in the Mamba2 Triton SSD prefill path (#61497)

Signed-off-by: Jhao-Ting Chen <jhaotingc@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f85e39e](https://github.com/vllm-project/vllm/commit/f85e39ea01baca414809883a57ca536b6c9fec1f)

- **作者**: Sergey Shlyapnikov
- **时间**: 2026-10-20T08:15:59Z
- **提交信息**: [ROCm][Quantization][MOE] Enable fused shared experts for MXFP8 checkpoints (#57916)

Signed-off-by: Sergei Shliapnikov <sergei.shliapnikov@amd.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [428cd0c](https://github.com/vllm-project/vllm/commit/428cd0cb4a42750f5339d08bb67d534cf8051429)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-20T07:55:57Z
- **提交信息**: [ROCm][Model] DeepSeek-V4.1 VL: stream language-model weights on ROCm (#62421)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f8e1e87](https://github.com/vllm-project/vllm/commit/f8e1e87129aa08bdb57579ad9406fe39cb81caef)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-20T07:54:57Z
- **提交信息**: [CI][Bugfix] Skip the SmolVLM HF comparison on Transformers 5.20 (#62620)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d3c9c73](https://github.com/vllm-project/vllm/commit/d3c9c73307ca858686370d5d406deef1cafe493f)

- **作者**: Martin Hickey
- **时间**: 2026-10-20T07:54:50Z
- **提交信息**: [Bugfix][Frontend] Return prompt token IDs from derender when requested (#62449)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-21
**监控日期**: 2026-10-20
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7281
- **最后更新**: 2026-10-21T02:52:38Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 17
- **主要提交者**: wangyu, Joshna-Medisetty, boatman

## AI分析总结

## 一、主要更新类型

昨日提交涵盖**多模态（omni）服务的核心功能增强、Bug 修复、性能优化与 CI/测试基建强化**四大方向。其中 CI/测试相关提交占比最高（约 7 条），其次是 Bug 修复（约 5 条）、核心/实验性功能（约 4 条）、性能优化（约 3 条）。文档类提交缺席，说明当前重心在工程稳定性与运行时能力上。

## 二、关键变更点及其与项目整体方向的关系

README 明确项目定位为"人人可用的**易用、快速、低成本 omni-modality 模型服务**"，本次提交高度对齐这一方向：

- **对齐 vLLM v0.32.0**：Intel CI pin、NPU 升级、性能基线等多条提交将硬件生态（Intel、Ascend/Habana）与上游 vLLM 版本对齐，直接服务"易用 + 低成本"目标，降低多硬件部署门槛。
- **双工（Duplex）语音会话持续打磨**：涉及 MiniCPM-o 4.5 duplex 轮次结束、Qwen3-Omni 会话音色转发、duplex 队列与会话更新默认值修复、OmniInteract/MiniCPM-o duplex 夜间测试修复等，表明全双工实时语音交互是当前最重要的产品能力。
- **核心运行时能力**：允许标量广播、MRV2 生成器槽位生命周期与跨 chunk 保留对齐，属于面向 CausVid 等长视频/流式场景的底层调度改进。
- **性能优化聚焦推理吞吐与延迟**：prefix cache 按音频码本网格加盐、同一 step 的 CausVid Noisy KV 调度、融合采样 kernel、批量 Code2Wav、客户端 TTFP/RTF 指标——直指"快速、低成本"承诺。
- **测试与基线体系化**：按模型可靠性用例、性能/精度夜间评测统一、WER 可复现开关，为多模型并发演进提供回归护栏。

## 三、对项目的影响和潜在意义

- **稳定性显著提升**：大量双工与多模型（MiniCPM-o、Qwen Omni、CausVid、MOSS-TTS）修复减少线上会话错乱与测试漂移，增强用户对实时语音服务的信心。
- **跨硬件可维护性增强**：版本对齐与统一基线意味着 Intel/NPU/Ascend 后端与主干同步演进，避免碎片化。
- **可观测性补强**：TTFP/RTF、WER、性能基线完善，使项目可以量化证明其"fast and cheap"的主张，为性能回归与发布决策提供依据。

## 四、值得关注的技术点

1. **prefix cache 按音频码本网格加盐**——用细粒度缓存键规避跨参考音频的错误复用，是语音生成场景缓存设计的巧思。
2. **融合采样 kernel（Ascend）**——针对 MiniCPM-o talker 的端到端采样加速，显示硬件专属 kernel 优化正在深入。
3. **Same-Step cell schedule for CausVid Noisy KV**——实验性调度方案，可能改善长视频生成的 KV 缓存一致性。
4. **双工队列与会话事件快照修复**——揭示实时流式会话中并发状态管理的复杂性，属于系统性难题。

## 五、对项目发展的影响

结合 README"omni-modality model serving"愿景，这批提交显示出项目正从"功能可用"迈向"多模型、多硬件、全双工场景下的可靠与高效"。双工语音链路的密集修复与评测体系统一，意味着项目在为实时多模态交互的生产化铺路；而与 vLLM v0.32.0 的多后端对齐则巩固了其作为 vLLM 生态 omni 扩展的兼容基础。整体上，这些提交共同强化了项目在**实时性、硬件覆盖面与质量门禁**三个维度的竞争力，为下一阶段的功能扩展奠定了坚实基线。

## 详细提交记录

### [856394f](https://github.com/vllm-project/vllm-omni/commit/856394fc51a341fe10e558d9a3266af30209e59a)

- **作者**: Joshna-Medisetty
- **时间**: 2026-10-20T22:08:53Z
- **提交信息**: [CI/Build] Align Intel CI pin with vLLM v0.32.0 (#9131)

Signed-off-by: Joshna-Medisetty <joshna.medisetty@intel.com>
Signed-off-by: Iryna Boiko <iboiko@habana.ai>
Co-authored-by: Iryna Boiko <iboiko@habana.ai>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [fe15c4c](https://github.com/vllm-project/vllm-omni/commit/fe15c4c2e8f38e11fb81f7cbaeb1d7b210edd1fd)

- **作者**: Alex Brooks
- **时间**: 2026-10-20T19:02:58Z
- **提交信息**: [Core] Allow Broadcasting Scalars (#9021)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [3e40008](https://github.com/vllm-project/vllm-omni/commit/3e40008bbeedfdad7d82e1fd25e76db5820025c0)

- **作者**: Tianyao Wu
- **时间**: 2026-10-20T16:35:57Z
- **提交信息**: [Bugfix] MiniCPM-o 4.5 duplex: let the turn-end Talker condition finish speaking (#8911)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [7f5e70f](https://github.com/vllm-project/vllm-omni/commit/7f5e70f2cfb5ad4ae72675d7a0b72f8db76609d9)

- **作者**: Clodagh Walsh
- **时间**: 2026-10-20T15:28:44Z
- **提交信息**: [Qwen Omni] Confine to text modality only for the thinking tests (#9117)

Signed-off-by: Clodagh Walsh <clodaghwalsh17@gmail.com>

### [18c3bd5](https://github.com/vllm-project/vllm-omni/commit/18c3bd5d2d4323bc7adca1ac3c465c4a53bbfb6e)

- **作者**: wangyu
- **时间**: 2026-10-20T12:21:22Z
- **提交信息**: [CI/Build] Add per-model reliability cases (#9109)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>

### [c0551d2](https://github.com/vllm-project/vllm-omni/commit/c0551d22674d0db81305c800b66ad83035fdc980)

- **作者**: Weiming Liao
- **时间**: 2026-10-20T11:56:10Z
- **提交信息**: [NPU] upgrade to v0.32.0 (#9143)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [818de94](https://github.com/vllm-project/vllm-omni/commit/818de948ea34724e1e26a2d8281c51cc0b066681)

- **作者**: NATURE
- **时间**: 2026-10-20T11:16:50Z
- **提交信息**: [Model] Batch MiniCPM-o 4.5 Code2Wav across reference audio (#9159)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [d39b5fa](https://github.com/vllm-project/vllm-omni/commit/d39b5fa9954a9305febc38723c207dfa4ec735ff)

- **作者**: ZacheryAU
- **时间**: 2026-10-20T11:14:22Z
- **提交信息**: [Frontend][Duplex][Benchmark] add client side per-response TTFP / RTF (#8869)

### [942a5da](https://github.com/vllm-project/vllm-omni/commit/942a5daa6c094615812ed89749ef07da96b8edab)

- **作者**: NATURE
- **时间**: 2026-10-20T10:36:10Z
- **提交信息**: [CI/Build] Unify Omni-DuplexEval C8 performance and accuracy nightly (#9145)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [6dbef89](https://github.com/vllm-project/vllm-omni/commit/6dbef89649667b828b81fa6171cb2be18180c2b2)

- **作者**: NumberWan
- **时间**: 2026-10-20T09:44:50Z
- **提交信息**: [Bugfix][Duplex] Fix pending-commit queue, item event snapshots, and session.update defaults (#7996)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: NATURE <wzliu@connect.hku.hk>

### [ef9eded](https://github.com/vllm-project/vllm-omni/commit/ef9ededfb33308911dc59fc4e4e6006cfe1f1e62)

- **作者**: Alicia
- **时间**: 2026-10-20T09:40:55Z
- **提交信息**: [CI/Build] Update performance baselines and fill missing metrics (#8957)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [706f1dd](https://github.com/vllm-project/vllm-omni/commit/706f1dd1282761c811d12039309f57af768232fa)

- **作者**: psv666
- **时间**: 2026-10-20T09:10:04Z
- **提交信息**: [Bugfix] Forward Qwen3-Omni duplex session voice to the Talker (#9079)

Signed-off-by: psv666 <150513104+psv666@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [01f807f](https://github.com/vllm-project/vllm-omni/commit/01f807f6844bd063cd70dafc952bedf0ff3b6328)

- **作者**: y-null
- **时间**: 2026-10-20T08:42:15Z
- **提交信息**: [Perf][Ascend] Fused sampling kernel for MiniCPM-o 4.5 talker + WER bench reproducibility switch (#9077)

Signed-off-by: y-null <213026468+y-null@users.noreply.github.com>
Signed-off-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: y-null <213026468+y-null@users.noreply.github.com>
Co-authored-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [c9cbf1c](https://github.com/vllm-project/vllm-omni/commit/c9cbf1c971c9ab7c2d5504ea27faacf8e31e35ec)

- **作者**: Canlin Guo
- **时间**: 2026-10-20T08:19:40Z
- **提交信息**: [Perf][MOSS-TTS] Salt the prefix cache by the audio-code grid only (#9045)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8ce320a](https://github.com/vllm-project/vllm-omni/commit/8ce320a5fdd3ba9f5f54be676e65df02af1ae921)

- **作者**: psv666
- **时间**: 2026-10-20T08:19:04Z
- **提交信息**: [Bugfix] Stop caching synthetic videos without requested audio (#9071)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4bc45a2](https://github.com/vllm-project/vllm-omni/commit/4bc45a21fb8184121a83d40f3805a46039033113)

- **作者**: Sheng GAO
- **时间**: 2026-10-20T08:06:35Z
- **提交信息**: [Experimental] Add Same-Step cell schedule for CausVid Noisy KV (#9078)

Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Signed-off-by: GUOGUO <xwdong1998@163.com>
Signed-off-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>
Signed-off-by: Sheng <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: GUOGUO <xwdong1998@163.com>
Co-authored-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [37ef70a](https://github.com/vllm-project/vllm-omni/commit/37ef70ad39d94d81e624e3c9a6702b64072d322f)

- **作者**: Qing7364
- **时间**: 2026-10-20T07:58:25Z
- **提交信息**: [CI/Build][MiniCPM-o] Run the OmniInteract nightly with the basic sliding window (#9033)

Signed-off-by: Qing <vera.xpq@gmail.com>

### [baa2f5a](https://github.com/vllm-project/vllm-omni/commit/baa2f5adcb9b51780a5369da4c117c8ab76671d9)

- **作者**: boatman
- **时间**: 2026-10-20T07:52:14Z
- **提交信息**: [Core] Align MRV2 generation runner slot lifecycle with cross-chunk retention (#9053)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>
Co-authored-by: Sy03 <1370724210@qq.com>

### [ad6fc16](https://github.com/vllm-project/vllm-omni/commit/ad6fc16f56a2b6dab374ad2ab07b087df3d4e57b)

- **作者**: amy-why-3459
- **时间**: 2026-10-20T07:31:43Z
- **提交信息**: [CI] Fix MiniCPM-o duplex tests broken after #8971 (#9151)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

---
