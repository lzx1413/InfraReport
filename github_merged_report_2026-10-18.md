# GitHub Stars 合并报告 - 2026-10-18

**合并日期**: 2026-10-19
**监控日期**: 2026-10-18
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


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2247
- **最后更新**: 2026-10-18T15:50:47Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zeren Chen

## AI分析总结

# ByteDance-Seed/VeOmni 昨日提交分析

## 1. 主要更新类型

**重构（Breaking Change）**。本次提交以 `BREAKING` 标签显式声明为破坏性变更，核心内容是对算子抽象层进行重构，将原有的 `OpSlot` 机制替换为新的 `VeomniOp` 设计，影响 `ops`（算子库）与 `model`（模型定义）两个核心模块。

## 2. 关键变更点及与项目方向的关系

VeOmni 的项目定位是"以模型为中心的分布式配方库（Model-Centric Distributed Recipe Zoo）"，目标是让任意模态（视觉、语音、多模态等）的模型训练都能以统一、可扩展的方式组织。本次重构与此高度相关：

- **统一算子抽象**：`OpSlot` → `VeomniOp` 的更名与重构，很可能是将零散的算子占位符升级为一个具名、可扩展的算子接口/基类，使算子注册、调用和组合更加规范化。
- **支撑多模态扩展**：多模态训练需要频繁组合不同模态的算子（如视觉编码、音频编码、融合层等），统一的 `VeomniOp` 抽象有助于降低新模态接入的边际成本，直接服务于项目"Any Modality"的核心愿景。
- **模块联动修改**：同时涉及 `ops` 和 `model` 两个模块，说明模型定义层的算子引用方式发生了变化，是一次贯穿性的接口升级。

## 3. 对项目的影响和潜在影响

- **短期破坏性**：外部用户或下游仓库若直接引用了 `OpSlot`，升级后需要同步修改代码，存在迁移成本。
- **长期收益**：更清晰的算子抽象为后续功能扩展（如新的并行策略、新模态算子、自动算子融合）奠定基础，技术债务进一步减少。
- **项目成熟度信号**：敢于在公开仓库做 BREAKING 重构，说明项目处于积极迭代期，API 尚未冻结，但架构在向稳定收敛。

## 4. 值得关注的技术点

- **`VeomniOp` 的设计模式**：推测其采用了注册式（registry）或组合式（composition）设计，值得跟踪后续 PR 中如何利用它构建具体的模态算子。
- **CI Agent 协作**：提交带有 `Co-authored-by: Cursor <cursoragent@cursor.com>`，表明字节团队正在将 AI 编码助手（Cursor）纳入真实生产流程，这是 AI 辅助开发在大型开源项目中落地的一个值得关注的案例。
- **破坏性变更的沟通方式**：使用 `BREAKING` 前缀而非语义化版本号，需关注项目是否会在后续发布迁移指南或 changelog。

## 5. 对项目发展的影响（基于项目背景）

VeOmni 论文（arXiv:2508.02317）强调的是规模化多模态训练的分布式配方复用。本次重构正是围绕"配方可复用"这一核心——只有算子接口足够统一和稳定，分布式训练配方（并行策略、调度逻辑）才能跨模态、跨模型地迁移复用。因此，这次 `VeomniOp` 重构是实现其研究愿景的关键基础设施步骤，预计将加速后续新模态配方和分布式策略的落地速度。总体而言，这是一次"短期有痛感、长期有价值"的架构演进，标志着项目从原型阶段向工程化、平台化方向推进。

## 详细提交记录

### [8305980](https://github.com/ByteDance-Seed/VeOmni/commit/830598083b5429264c04340b42b9f0090e0a5907)

- **作者**: Zeren Chen
- **时间**: 2026-10-18T15:50:38Z
- **提交信息**: [BREAKING][ops, model] refactor: replace OpSlot with VeomniOp (#1142)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2921
- **最后更新**: 2026-10-18T10:48:16Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Shiqiao Gu (谷石桥)

## AI分析总结

# LightX2V 仓库昨日提交分析

## 1. 主要更新类型
**功能新增**：本次提交主要属于功能新增范畴，为 LightX2V 框架添加了对 edenlive 平台的支持，同时包含对实时流式推理的优化。这是一个典型的特性增强型提交，旨在扩展框架的应用场景和提升性能表现。

## 2. 关键变更点与项目方向的关系
本次提交的核心变更点包括：
- 新增 edenlive 平台的支持适配
- 实现了优化的实时流式推理机制
- 通过 Co-authored-by 标记表明这是一个协作完成的功能

这些变更与 LightX2V 作为"轻量级视频生成推理框架"的整体定位高度契合。项目的核心目标是提供高效、轻量的视频生成推理解决方案，而实时流式推理的优化正是提升推理效率和用户体验的关键技术路径。edenlive 支持则体现了框架向多平台扩展的战略方向。

## 3. 对项目的影响和潜在意义
**直接影响**：
- 扩展了 LightX2V 的应用生态，使其能够更好地服务于 edenlive 平台用户
- 提升了实时视频生成的流式推理性能，改善用户体验
- 为后续更多平台集成提供了参考模式

**潜在意义**：
- 增强了框架的竞争力，使其在视频生成推理领域具有更广泛的应用场景
- 实时流式推理的优化为低延迟应用奠定了基础
- 展现了项目活跃的开发状态和持续的功能迭代能力

## 4. 值得关注的技术点
**实时流式推理优化**：这是本次提交的技术亮点，涉及到视频生成过程中的流式数据处理、内存管理和延迟控制等关键技术。这种优化通常需要在生成质量、推理速度和资源消耗之间找到平衡点。

**平台适配策略**：edenlive 支持体现了框架的可扩展性设计，通过模块化的适配方式支持不同平台，这种架构设计有助于降低后续集成新平台的成本。

**协作开发模式**：Co-authored-by 标记显示这是一个多人协作的特性开发，体现了项目社区的协作氛围和代码质量控制机制。

## 5. 对项目发展的影响分析
基于 LightX2V 的项目背景，本次提交对项目发展具有以下重要意义：

**生态建设方面**：通过添加 edenlive 支持，LightX2V 正在构建一个更加完善的视频生成推理生态系统。这种多平台支持策略有助于吸引更多开发者和企业用户，扩大项目的影响力和用户基础。

**技术演进方面**：实时流式推理的优化标志着项目从基础功能实现向高性能应用演进。这符合"轻量视频生成推理"的项目定位，通过持续的性能优化来提升框架的实用价值。

**发展方向方面**：本次提交体现了项目向实时应用和商业平台集成发展的趋势，预示着 LightX2V 未来可能会在实时视频生成、直播推理等场景中发挥更大作用。

总体而言，这次提交是 LightX2V 项目功能完善和技术提升的重要一步，既增强了框架的实用性，也为其在视频生成推理领域的发展奠定了更坚实的基础。

## 详细提交记录

### [d48a617](https://github.com/ModelTC/LightX2V/commit/d48a6173bc15a88b06cdcfb211183b43d8038846)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-10-18T10:40:44Z
- **提交信息**: feat(edenlive): add edenlive support with optimized real-time streaming inference (#1625)

Co-authored-by: Yang Yong (雍洋) <yongyang1030@163.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2304
- **最后更新**: 2026-10-17T17:04:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6690
- **最后更新**: 2026-10-18T23:58:47Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 6
- **主要提交者**: eigen, Julian, Zihao Ye

## AI分析总结

# FlashInfer 近期提交综合分析

## 一、主要更新类型

本次 16 条提交以**性能优化**为主（约 8 条），集中在 Cake 生成的 GPU kernel 上：BF16×FP4 GEMM、FP8 LoRA GEMM、DeepSeek 融合路由、扩散模型 FC1+SwiGLU、DSv4 attention 调度等。**功能新增** 3 条，涵盖 Rubin（sm_107a）内核、SM120 原生读取 DeepSeek-V4.1 inline-scale KV 记录、Mamba2 SSD prefill 的 Rubin 程序。**Bug 修复** 2 条，涉及采样 kernel 的 per-request top_k dtype 错配与 cake_mla 的空 KV split。**重构清理** 3 条，包括 SM120/SM100/SM103 跨架构 kernel 合并与 cake_vsa 大规模去重。其余为代码所有者更新、trtllm-gen BMM cubin 制品升级等杂项。

## 二、关键变更点及项目方向

- **低精度 GEMM 突破**：BF16×FP4 GEMM 重新生成 97 个程序，几何平均加速约 2.16–2.18 倍（B200/GB300），峰值近 3.9 倍，直接提升 Blackwell 平台低精度算力；E2M1 权重 + E4M3 块尺度 + FP32 累加的混合精度设计，同时维护 cuDNN-ABI 与 CuTe-ABI 两套布局后端。
- **Rubin 平台持续铺开**：DeepSeek 融合路由、BGMV MoE、concat-MLA-K、Mamba2 SSD prefill 均新增 Rubin 程序，并用 `redux.sync.max.u32` 单调编码 key 替代 `shfl_xor` max 树做路由优化。
- **DeepSeek 生态深度适配**：DSv4.1 inline-scale KV 布局与 FlashMLA ABI、vLLM 对齐；DSv4 FP8 prefill 调度在低 head 场景改走单-CTA M64 体，提速最高逾 5 倍，采用运行时 head 参数加 predication 复用同一 kernel body。
- **CAKE 内核工程化收敛**：FP16 与 BF16 块稀疏 kernel 源码由 3,038 行合并至 1,574 行，SM90 的 14 个启动器压缩为一个（减少约 6,166 行），并移除 experimental 下的 CuTe DSL 冗余版本，累计清除约 7,000 行重复死代码。
- **正确性修复**：采样 kernel 消除 int64 索引下的越界读风险；cake_mla 修复 FP8 page-64 MLA 解码中，短序列产生的空 split 仍执行完整 tile 流水线导致 load warp 越界访问页表、MMA warp 在屏障首相位前发出 drain PV，最终将陈旧 FP8 NaN 乘入输出的问题——该类 `0 × NaN = NaN` 错误无法被零权重掩盖，修复方式为空 split 跳过 K/V 加载与 PV 计算。

## 三、项目影响与潜在意义

Blackwell 与 Rubin 上的关键算子性能显著提升，直接降低 LLM 推理成本；FP8 LoRA GEMM 约 1.5–2.5% 的主循环提速虽小，但在大规模 LoRA 服务中累积收益可观。inline-scale KV 原生支持消除了与 vLLM/FlashMLA 生态的格式不兼容，降低集成摩擦。重构在保持公共 API、路由与默认值不变、SASS 设备代码逐字节一致的前提下大幅降低维护面；CPU planner 测试纳入 CI，为后续演化提供安全网，`backend="cake_cute"` 以别名保留，下游用户零迁移成本。

## 四、值得关注的技术点

SASS 级等价性验证作为 GPU kernel 重构最严格的证明方式；tcgen05 线程同步栅栏、guard fold、PDL 等 Blackwell 特性应用；warp specialization 下屏障相位与生产者-消费者流水线的微妙交互（`p_full` parity wait 在屏障未推进时立即通过）；`plan_num_split` 按最长行计算 split 数导致短行必然产生空 split 的边界设计权衡；CUPTI 计时、冷 L2、配对交错实验与双种子复现构成的严谨基准方法论。

## 五、对项目发展的整体影响

FlashInfer 正沿三条主线推进：向 Blackwell/Rubin 下一代硬件快速铺开 kernel 覆盖、紧跟 DeepSeek 等前沿模型的算子需求、依托 Cake 代码生成与系统化测试实现可重复的性能迭代。CAKE 稀疏注意力与 MLA 解码内核已从功能验证期转入工程化收敛期，正确性修复进一步强化了生产可信度。项目在高速迭代中兼顾代码瘦身与质量治理，持续巩固其作为高性能 LLM 推理内核基础设施的地位。

## 详细提交记录

### [e61e9b1](https://github.com/flashinfer-ai/flashinfer/commit/e61e9b1f375e8d95879b47a8bdf902fe39103238)

- **作者**: eigen
- **时间**: 2026-10-18T23:58:34Z
- **提交信息**: perf(cake_gdn): refresh Blackwell GDN prefill bodies for 84 records (guard fold, tcgen05 thread-sync fences) (#6752)

### [d1df416](https://github.com/flashinfer-ai/flashinfer/commit/d1df416be8c9e87e7ec6c8c64fda3c1cebf90286)

- **作者**: eigen
- **时间**: 2026-10-18T23:48:47Z
- **提交信息**: deslop(cake_deepgemm_mqa): fold SM120 and dense paged clones, share the host helper, drop unread catalog data (#6733)

### [c7eede4](https://github.com/flashinfer-ai/flashinfer/commit/c7eede45a49e600e414fc56b787a3f70af6e8777)

- **作者**: eigen
- **时间**: 2026-10-18T23:32:21Z
- **提交信息**: feat(cake_bf16_fp4_gemm): faster SM100/SM103 BF16 x FP4 GEMM kernels for the blackwell-native and blackwell-tiled backends (#6614)

FlashInfer's `mm_bf16_fp4` multiplies BF16 activations by FP4 (E2M1)
weights that carry E4M3 block scales, with FP32 accumulation. Cake ships
it as two backend variants that differ in operand layout.
`blackwell-native` uses cuDNN-ABI layouts and produces BF16 or FP16
output. `blackwell-tiled` uses CuTe-ABI prepared-tile layouts and
produces BF16 output. This PR regenerates both variants as 97 programs
across 20 kernel kinds, replacing the previous Cake generation of the
same kernels on `main` (#5990). Speedup is the previous time divided by
this PR's time. Across the 22 shape and GPU combinations it ranges from
1.36x to 3.90x, with a geometric mean of 2.18x on GB300 and 2.16x on
B200.

**NVIDIA GB300 (sm_103a), CUDA 13.3:** median CUPTI kernel time in us,
cold L2, PDL on; alpha calibrated and BF16 output unless noted.

| Shape M/N/K | Variant | Previous Cake (us) | This PR (us) | Speedup |
|---|---|---:|---:|---:|
| 1/4096/4096 | blackwell-native | 15.968 | 8.192 | 1.949x |
| 1/4096/4096 | blackwell-tiled | 30.464 | 7.808 | 3.902x |
| 768/2112/2048 | blackwell-native | 38.880 | 10.624 | 3.660x |
| 768/2112/2048 | blackwell-tiled | 31.200 | 11.264 | 2.770x |
| 7/4160/192 | blackwell-tiled | 4.640 | 3.040 | 1.526x |
| 13/11008/128 | blackwell-tiled | 5.056 | 3.104 | 1.629x |
| 17/3072/3072 | blackwell-tiled | 12.224 | 7.744 | 1.579x |
| 16/1024/1024 | blackwell-tiled, alpha=None | 5.472 | 4.000 | 1.368x |
| 16/1024/1024 | blackwell-native, FP16 output | 8.640 | 2.880 | 3.000x
|
| 16/1024/1024 | blackwell-native, caller-provided `out` | 8.672 | 2.848
| 3.045x |
| 16/1024/1024 | blackwell-tiled, caller-provided `out` | 5.664 | 4.160
| 1.362x |

**NVIDIA B200 (sm_100a), CUDA 13.3:** median CUPTI kernel time in us,
cold L2, PDL on; alpha calibrated and BF16 output unless noted.

| Shape M/N/K | Variant | Previous Cake (us) | This PR (us) | Speedup |
|---|---|---:|---:|---:|
| 1/4096/4096 | blackwell-native | 16.896 | 8.672 | 1.948x |
| 1/4096/4096 | blackwell-tiled | 29.696 | 8.128 | 3.654x |
| 768/2112/2048 | blackwell-native | 41.824 | 11.488 | 3.641x |
| 768/2112/2048 | blackwell-tiled | 34.016 | 12.400 | 2.743x |
| 7/4160/192 | blackwell-tiled | 4.576 | 3.072 | 1.490x |
| 13/11008/128 | blackwell-tiled | 5.056 | 3.200 | 1.580x |
| 17/3072/3072 | blackwell-tiled | 12.352 | 8.095 | 1.526x |
| 16/1024/1024 | blackwell-tiled, alpha=None | 5.536 | 4.000 | 1.384x |
| 16/1024/1024 | blackwell-native, FP16 output | 9.088 | 2.927 | 3.105x
|
| 16/1024/1024 | blackwell-native, caller-provided `out` | 9.088 | 2.944
| 3.087x |
| 16/1024/1024 | blackwell-tiled, caller-provided `out` | 5.792 | 4.160
| 1.392x |

Cake has no other variants of this kernel: FP16 output is only on
`blackwell-native`, there are no fused forms, and every program ships
for sm_100a (B200) and sm_103a (GB300).

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0780617](https://github.com/flashinfer-ai/flashinfer/commit/078061790be27c1502c4aeec0931cf13732efaeb)

- **作者**: eigen
- **时间**: 2026-10-18T23:27:23Z
- **提交信息**: perf(cake_quant_lora_gemm): hoisted stage wait in the SM90 FP8 LoRA GEMM (#6753)

### [859d933](https://github.com/flashinfer-ai/flashinfer/commit/859d93353209026fbdaeec7176bf67e82e12123a)

- **作者**: eigen
- **时间**: 2026-10-18T23:26:29Z
- **提交信息**: perf(cake): sm_107a (Rubin) kernels for DeepSeek fused routing, BGMV MoE and concat-MLA-K (#6747)

This PR adds Cake-generated sm_107a programs for three kernel families
(DeepSeek fused routing, BGMV MoE and concat-MLA-K) and routes them on
compute capability 10.7.

GPU: NVIDIA Graphics Device (R200, sm_107a; 212 SMs; compute capability
10.7); driver 620.62; CUDA 13.5 (PyTorch 2.13.0a0). Timing: CUPTI GPU
time, cold L2, paired interleaved arms, 100 ms per arm per group x 3
groups; values are medians in microseconds; speedup = baseline median /
Cake median (> 1 = Cake faster). Two seeds (17 / 29) per row.

## DeepSeek fused routing (`fused_topk_deepseek`)

FlashInfer's `fused_topk_deepseek` dispatches on (n_group, E) to four
kernel forms: `grouped<ScoreT,BiasT,4,8>` (E=256, 8 groups, topk_group
4, topk 8), `grouped<ScoreT,BiasT,1,1>`, `single<…,128>` (n_group == 1,
E ≤ 128) and `single<…,384>` (E ≤ 384). Each form covers the nine
score/bias dtype pairs of float32, float16 and bfloat16. For compute
capability 10.7 only, this PR adds seven multi-token grouped kernels,
`grouped_k8g4_mt2` to `grouped_k8g4_mt8`, which handle 2 to 8 tokens per
CTA as chosen by the launch header. It also adds single-group kernels
whose two `shfl_xor` max trees use `redux.sync.max.u32` on a
monotone-encoded key. The new programs reproduce the shipped outputs bit
for bit on the covered shapes and data types. The baseline is
FlashInfer's default `fused_topk_deepseek` (NoAuxTc) kernel.

| shape | Cake µs (seed 17 / 29) | FlashInfer default µs (seed 17 / 29)
| speedup (seed 17 / 29) |
|---|---|---|---|
| `correctness_pytest_main_t1_e384_k1_g1_kg1_float32_float32`<br>T=1
E=384 n_group=1 topk_group=1 topk=1 score_dtype=float32
bias_dtype=float32 routed_scaling_factor=1 launch_with_pdl replay_rows=0
| 1.696 / 1.344 | 2.848 / 3.008 | 1.679 / 2.238 |
| `correctness_pytest_main_t16_e256_k2_g8_kg2_float16_float16`<br>T=16
E=256 n_group=8 topk_group=2 topk=2 score_dtype=float16
bias_dtype=float16 routed_scaling_factor=1 launch_with_pdl replay_rows=0
| 2.368 / 2.336 | 3.584 / 3.648 | 1.514 / 1.562 |
| `correctness_pytest_replay_t1_e256_k4_g8_kg4_bfloat16`<br>T=1 E=256
n_group=8 topk_group=4 topk=4 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=1 | 2.176 / 2.144 |
3.200 / 3.104 | 1.471 / 1.448 |
| `correctness_pytest_replay_t7_e256_k1_g1_kg1_bfloat16`<br>T=7 E=256
n_group=1 topk_group=1 topk=1 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=7 | 1.920 / 2.016 |
3.360 / 3.264 | 1.750 / 1.619 |
| `correctness_pytest_replay_t8_e256_k1_g1_kg1_bfloat16`<br>T=8 E=256
n_group=1 topk_group=1 topk=1 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=8 | 2.016 / 2.016 |
3.360 / 3.360 | 1.667 / 1.667 |
| `correctness_pytest_replay_t32_e256_k1_g1_kg1_bfloat16`<br>T=32 E=256
n_group=1 topk_group=1 topk=1 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=32 | 2.016 / 1.984 |
3.680 / 3.712 | 1.825 / 1.871 |
| `correctness_pytest_replay_t64_e256_k1_g1_kg1_bfloat16`<br>T=64 E=256
n_group=1 topk_group=1 topk=1 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=64 | 2.016 / 2.016 |
3.712 / 3.680 | 1.841 / 1.825 |
| `correctness_embedded_benchmark_t1`<br>T=1 E=256 n_group=8
topk_group=4 topk=8 score_dtype=float32 bias_dtype=float32
routed_scaling_factor=2.5 launch_with_pdl replay_rows=0 | 2.048 / 2.272
| 3.296 / 2.944 | 1.609 / 1.296 |
| `correctness_embedded_benchmark_t4096`<br>T=4096 E=256 n_group=8
topk_group=4 topk=8 score_dtype=float32 bias_dtype=float32
routed_scaling_factor=2.5 launch_with_pdl replay_rows=0 | 4.096 / 4.224
| 11.521 / 11.488 | 2.813 / 2.720 |
| `correctness_successful_sample_t1024`<br>T=1024 E=256 n_group=8
topk_group=4 topk=8 score_dtype=float32 bias_dtype=float32
routed_scaling_factor=2.5 launch_with_pdl replay_rows=0 | 3.104 / 3.072
| 5.696 / 5.664 | 1.835 / 1.844 |
| `api_boundary_min_t1_e2_k1_g1_kg1_float16_bfloat16_pdl_false`<br>T=1
E=2 n_group=1 topk_group=1 topk=1 score_dtype=float16
bias_dtype=bfloat16 routed_scaling_factor=1 replay_rows=0 | 1.952 /
1.568 | 2.817 / 3.040 | 1.443 / 1.939 |
|
`api_boundary_single_group_max128_t64_bfloat16_float16_pdl_false`<br>T=64
E=128 n_group=1 topk_group=1 topk=1 score_dtype=bfloat16
bias_dtype=float16 routed_scaling_factor=1 replay_rows=0 | 2.016 / 2.016
| 3.584 / 3.552 | 1.778 / 1.762 |
| `api_boundary_multigroup_min_t2_e4_k2_g2_kg1_float32_float16`<br>T=2
E=4 n_group=2 topk_group=1 topk=2 score_dtype=float32 bias_dtype=float16
routed_scaling_factor=2.5 launch_with_pdl replay_rows=0 | 1.952 / 1.760
| 2.976 / 3.008 | 1.525 / 1.709 |
| `api_boundary_odd_t32_e96_k5_g3_kg2_float16_bfloat16`<br>T=32 E=96
n_group=3 topk_group=2 topk=5 score_dtype=float16 bias_dtype=bfloat16
routed_scaling_factor=1.3 launch_with_pdl replay_rows=0 | 2.464 / 2.464
| 3.616 / 3.648 | 1.468 / 1.481 |
|
`api_boundary_oversized_replay_t7_r64_e256_k8_g8_kg4_bfloat16_float32_pdl_false`<br>T=7
E=256 n_group=8 topk_group=4 topk=8 score_dtype=bfloat16
bias_dtype=float32 routed_scaling_factor=2.5 replay_rows=64 | 2.656 /
2.656 | 3.648 / 3.680 | 1.373 / 1.386 |
| `test_t7_e256_g8_kg4_k8_float32`<br>T=7 E=256 n_group=8 topk_group=4
topk=8 score_dtype=float32 bias_dtype=float32 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 2.528 / 2.496 | 3.840 / 3.841 | 1.519 /
1.539 |
| `test_t7_e256_g8_kg4_k8_float16`<br>T=7 E=256 n_group=8 topk_group=4
topk=8 score_dtype=float16 bias_dtype=float16 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 2.464 / 2.496 | 3.456 / 3.456 | 1.403 /
1.385 |
| `test_t7_e256_g8_kg4_k8_bfloat16`<br>T=7 E=256 n_group=8 topk_group=4
topk=8 score_dtype=bfloat16 bias_dtype=bfloat16 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 2.624 / 2.560 | 3.520 / 3.616 | 1.341 /
1.412 |
| `test_t7_e128_g4_kg2_k4_float32`<br>T=7 E=128 n_group=4 topk_group=2
topk=4 score_dtype=float32 bias_dtype=float32 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 2.464 / 2.464 | 3.936 / 3.936 | 1.597 /
1.597 |
| `test_t7_e128_g4_kg2_k4_float16`<br>T=7 E=128 n_group=4 topk_group=2
topk=4 score_dtype=float16 bias_dtype=float16 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 2.144 / 2.144 | 3.393 / 3.360 | 1.583 /
1.567 |
| `test_t7_e128_g4_kg2_k4_bfloat16`<br>T=7 E=128 n_group=4 topk_group=2
topk=4 score_dtype=bfloat16 bias_dtype=bfloat16 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 2.400 / 2.432 | 3.552 / 3.424 | 1.480 /
1.408 |
| `test_t7_e128_g1_kg1_k1_float32`<br>T=7 E=128 n_group=1 topk_group=1
topk=1 score_dtype=float32 bias_dtype=float32 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 2.016 / 1.984 | 3.488 / 3.328 | 1.730 /
1.677 |
| `test_t7_e128_g1_kg1_k1_float16`<br>T=7 E=128 n_group=1 topk_group=1
topk=1 score_dtype=float16 bias_dtype=float16 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 1.696 / 1.696 | 3.073 / 3.040 | 1.812 /
1.792 |
| `test_t7_e128_g1_kg1_k1_bfloat16`<br>T=7 E=128 n_group=1 topk_group=1
topk=1 score_dtype=bfloat16 bias_dtype=bfloat16 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 1.825 / 1.984 | 3.200 / 3.104 | 1.753 /
1.565 |
| `test_t7_e384_g1_kg1_k1_float32`<br>T=7 E=384 n_group=1 topk_group=1
topk=1 score_dtype=float32 bias_dtype=float32 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 2.016 / 2.016 | 3.616 / 3.616 | 1.794 /
1.794 |
| `test_t7_e384_g1_kg1_k1_float16`<br>T=7 E=384 n_group=1 topk_group=1
topk=1 score_dtype=float16 bias_dtype=float16 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 1.856 / 1.856 | 3.264 / 3.264 | 1.759 /
1.759 |
| `test_t7_e384_g1_kg1_k1_bfloat16`<br>T=7 E=384 n_group=1 topk_group=1
topk=1 score_dtype=bfloat16 bias_dtype=bfloat16 routed_scaling_factor=1
launch_with_pdl replay_rows=0 | 1.984 / 1.984 | 3.360 / 3.360 | 1.694 /
1.694 |
| `test_op_t1_e256_g8_kg4_k8_bfloat16`<br>T=1 E=256 n_group=8
topk_group=4 topk=8 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 1.984 / 2.112 |
3.040 / 2.912 | 1.532 / 1.379 |
| `test_op_t8_e256_g8_kg4_k8_bfloat16`<br>T=8 E=256 n_group=8
topk_group=4 topk=8 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 2.624 / 2.656 |
3.648 / 3.648 | 1.390 / 1.373 |
| `test_op_t16_e256_g8_kg4_k8_bfloat16`<br>T=16 E=256 n_group=8
topk_group=4 topk=8 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 2.400 / 2.464 |
3.776 / 3.840 | 1.573 / 1.558 |
| `test_op_t64_e256_g8_kg4_k8_bfloat16`<br>T=64 E=256 n_group=8
topk_group=4 topk=8 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 2.656 / 2.656 |
4.096 / 4.032 | 1.542 / 1.518 |
| `test_op_t1_e256_g8_kg4_k8_float32`<br>T=1 E=256 n_group=8
topk_group=4 topk=8 score_dtype=float32 bias_dtype=float32
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 2.336 / 2.464 |
3.488 / 3.200 | 1.493 / 1.299 |
| `test_op_t8_e256_g8_kg4_k8_float32`<br>T=8 E=256 n_group=8
topk_group=4 topk=8 score_dtype=float32 bias_dtype=float32
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 2.688 / 2.688 |
4.064 / 4.032 | 1.512 / 1.500 |
| `test_op_t16_e256_g8_kg4_k8_float32`<br>T=16 E=256 n_group=8
topk_group=4 topk=8 score_dtype=float32 bias_dtype=float32
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 2.656 / 2.656 |
3.840 / 3.808 | 1.446 / 1.434 |
| `test_op_t64_e256_g8_kg4_k8_float32`<br>T=64 E=256 n_group=8
topk_group=4 topk=8 score_dtype=float32 bias_dtype=float32
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 2.752 / 2.688 |
4.224 / 4.192 | 1.535 / 1.560 |
| `test_op_t64_e256_g8_kg2_k4_float16`<br>T=64 E=256 n_group=8
topk_group=2 topk=4 score_dtype=float16 bias_dtype=float16
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 2.464 / 2.464 |
4.000 / 4.000 | 1.623 / 1.623 |
| `test_op_t64_e256_g8_kg1_k2_bfloat16`<br>T=64 E=256 n_group=8
topk_group=1 topk=2 score_dtype=bfloat16 bias_dtype=bfloat16
routed_scaling_factor=1 launch_with_pdl replay_rows=0 | 2.400 / 2.368 |
3.937 / 3.936 | 1.640 / 1.662 |

Cake ships these routing kernels for sm_107a only, and on every other
architecture `fused_topk_deepseek` keeps its current kernels.

## BGMV MoE

The BGMV MoE kernel has a shrink body and an expand body. Cake ships it
as fixed bf16 variants for hidden sizes 2688 and 3072, plus a generic
bf16 rank-32 variant. This PR adds sm_107a to the kernel's JIT loader
table. The baseline is FlashInfer's portable BGMV MoE kernel, and the
last two columns also compare against the `bgmv_moe` API path.

| shape | Cake µs (seed 17 / 29) | FlashInfer portable µs (seed 17 / 29)
| speedup vs portable (seed 17 / 29) | FlashInfer `bgmv_moe` API µs
(seed 17 / 29) | speedup vs API (seed 17 / 29) |
|---|---|---|---|---|---|
| `perf_large_t1`<br>hidden_size=3072 num_tokens=1 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 5.984 / 5.953 | 20.384 / 20.480 | 3.406 / 3.440 |
142.818 / 144.066 | 23.867 / 24.201 |
| `perf_large_t4`<br>hidden_size=3072 num_tokens=4 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 6.464 / 6.464 | 20.833 / 20.800 | 3.223 / 3.218 |
142.018 / 141.761 | 21.971 / 21.931 |
| `perf_large_t8`<br>hidden_size=3072 num_tokens=8 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 6.336 / 6.336 | 21.120 / 20.960 | 3.333 / 3.308 |
143.489 / 142.657 | 22.647 / 22.515 |
| `perf_large_t32`<br>hidden_size=3072 num_tokens=32 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 10.336 / 10.336 | 23.968 / 23.585 | 2.319 / 2.282 |
144.481 / 143.778 | 13.978 / 13.910 |
| `perf_large_t256`<br>hidden_size=3072 num_tokens=256 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 25.472 / 25.472 | 44.640 / 44.385 | 1.753 / 1.743 |
149.825 / 149.729 | 5.882 / 5.878 |
| `perf_large_t512`<br>hidden_size=3072 num_tokens=512 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 42.560 / 42.560 | 67.200 / 67.009 | 1.579 / 1.574 |
163.585 / 163.425 | 3.844 / 3.840 |
| `perf_large_t1024`<br>hidden_size=3072 num_tokens=1024 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 74.081 / 74.081 | 110.497 / 110.337 | 1.492 / 1.489
| 190.946 / 190.722 | 2.578 / 2.575 |
| `perf_nemotron_t1`<br>hidden_size=2688 num_tokens=1 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 5.824 / 5.824 | 20.545 / 20.352 | 3.528 / 3.495 |
144.705 / 144.033 | 24.846 / 24.731 |
| `perf_nemotron_t4`<br>hidden_size=2688 num_tokens=4 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 6.400 / 6.400 | 20.800 / 20.832 | 3.250 / 3.255 |
143.809 / 144.481 | 22.470 / 22.575 |
| `perf_nemotron_t8`<br>hidden_size=2688 num_tokens=8 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 6.304 / 6.304 | 21.184 / 20.896 | 3.360 / 3.315 |
144.834 / 143.777 | 22.975 / 22.807 |
| `perf_nemotron_t32`<br>hidden_size=2688 num_tokens=32 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 10.176 / 10.176 | 26.369 / 26.208 | 2.591 / 2.575 |
143.330 / 142.753 | 14.085 / 14.028 |
| `perf_nemotron_t256`<br>hidden_size=2688 num_tokens=256 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 24.448 / 24.448 | 51.840 / 51.649 | 2.120 / 2.113 |
150.145 / 150.049 | 6.141 / 6.137 |
| `perf_nemotron_t512`<br>hidden_size=2688 num_tokens=512 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 38.624 / 38.624 | 76.416 / 76.257 | 1.978 / 1.974 |
159.905 / 159.297 | 4.140 / 4.124 |
| `perf_nemotron_t1024`<br>hidden_size=2688 num_tokens=1024 rank=32
num_experts=128 num_loras=8 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=none | 70.144 / 70.144 | 127.056 / 126.945 | 1.811 / 1.810
| 207.713 / 207.842 | 2.961 / 2.963 |
| `correctness_e2e_minimal_bf16`<br>hidden_size=768 num_tokens=1 rank=8
num_experts=1 num_loras=1 top_k=1 num_slices=1 dtype=bfloat16
inactive_mode=single_active | 5.152 / 5.152 | 20.129 / 20.064 | 3.907 /
3.894 | 142.657 / 142.626 | 27.690 / 27.684 |
| `correctness_shrink_bf16_small`<br>hidden_size=768 num_tokens=4
rank=16 num_experts=8 num_loras=4 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=mixed | 4.608 / 4.608 | 20.513 / 20.320 | 4.452 / 4.410 |
144.449 / 143.105 | 31.347 / 31.056 |
| `correctness_expand_fp16_experts64_t4`<br>hidden_size=768 num_tokens=4
rank=32 num_experts=64 num_loras=4 top_k=2 num_slices=1 dtype=float16
inactive_mode=mixed | 4.512 / 4.512 | 20.512 / 20.416 | 4.546 / 4.525 |
143.169 / 143.682 | 31.731 / 31.844 |
| `correctness_e2e_bf16_tokens32`<br>hidden_size=768 num_tokens=32
rank=16 num_experts=8 num_loras=4 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=mixed | 4.768 / 4.768 | 20.480 / 20.416 | 4.295 / 4.282 |
142.082 / 142.786 | 29.799 / 29.947 |
| `correctness_e2e_all_inactive`<br>hidden_size=768 num_tokens=16
rank=16 num_experts=8 num_loras=4 top_k=2 num_slices=1 dtype=bfloat16
inactive_mode=all | 3.712 / 3.712 | 19.456 / 19.552 | 5.241 / 5.267 |
145.634 / 145.889 | 39.233 / 39.302 |

Not measured: `correctness_e2e_multi_slice`. This shape uses two LoRA
slices, and the Cake kernel requires exactly one LoRA slice.

Cake already ships this kernel for sm_90a, sm_100a and sm_103a, and this
PR adds sm_107a.

## concat-MLA-K (`concat_mla_k`)

`concat_mla_k` supports four data types (bfloat16, float16,
float8_e4m3fn, float8_e5m2) and three input layouts (contiguous,
nope_strided, both_strided). Its shape is fixed at num_heads 128,
nope_dim 128 and rope_dim 64 (output_dim 192). This PR adds an sm_107a
slot-split module, in which several CTAs share one token window (split
choices 1, 2, 3 and 6; at most 424 CTAs) and the address math is hoisted
above the loads. The baseline is FlashInfer's default `concat_mla_k`
kernel.

| shape | Cake µs (seed 17 / 29) | FlashInfer default µs (seed 17 / 29)
| speedup (seed 17 / 29) |
|---|---|---|---|
| `perf_bf16_t2048_both_strided`<br>tokens=2048 dtype=bfloat16
layout=both_strided num_heads=128 nope_dim=128 rope_dim=64 | 15.168 /
15.424 | 21.313 / 21.376 | 1.405 / 1.386 |
| `bench_bf16_t4096_both_strided`<br>tokens=4096 dtype=bfloat16
layout=both_strided num_heads=128 nope_dim=128 rope_dim=64 | 27.488 /
27.488 | 37.984 / 38.016 | 1.382 / 1.383 |
| `bench_bf16_t8192_both_strided`<br>tokens=8192 dtype=bfloat16
layout=both_strided num_heads=128 nope_dim=128 rope_dim=64 | 51.520 /
51.265 | 72.129 / 72.097 | 1.400 / 1.406 |
| `perf_bf16_t16384_both_strided`<br>tokens=16384 dtype=bfloat16
layout=both_strided num_heads=128 nope_dim=128 rope_dim=64 | 99.297 /
99.329 | 137.282 / 137.314 | 1.383 / 1.382 |
| `perf_bf16_t32768_both_strided`<br>tokens=32768 dtype=bfloat16
layout=both_strided num_heads=128 nope_dim=128 rope_dim=64 | 195.234 /
195.171 | 266.083 / 266.051 | 1.363 / 1.363 |
| `correctness_core_t1_bfloat16`<br>tokens=1 dtype=bfloat16
layout=contiguous num_heads=128 nope_dim=128 rope_dim=64 | 1.888 / 1.824
| 5.248 / 5.216 | 2.780 / 2.860 |
| `correctness_strided_t2048_bfloat16`<br>tokens=2048 dtype=bfloat16
layout=nope_strided num_heads=128 nope_dim=128 rope_dim=64 | 15.232 /
15.424 | 21.280 / 21.344 | 1.397 / 1.384 |
| `correctness_strided_t2048_float8_e4m3fn`<br>tokens=2048
dtype=float8_e4m3fn layout=nope_strided num_heads=128 nope_dim=128
rope_dim=64 | 9.473 / 9.472 | 18.784 / 18.816 | 1.983 / 1.986 |
| `correctness_trace_t2048_bf16`<br>tokens=2048 dtype=bfloat16
layout=contiguous num_heads=128 nope_dim=128 rope_dim=64 | 15.296 /
15.488 | 22.528 / 22.560 | 1.473 / 1.457 |
| `correctness_output_strided_t1_bfloat16`<br>tokens=1 dtype=bfloat16
layout=contiguous padded_output num_heads=128 nope_dim=128 rope_dim=64 |
1.920 / 1.792 | 5.152 / 5.216 | 2.683 / 2.911 |
| `correctness_output_strided_t1_float16`<br>tokens=1 dtype=float16
layout=contiguous padded_output num_heads=128 nope_dim=128 rope_dim=64 |
1.856 / 1.856 | 5.280 / 5.120 | 2.845 / 2.759 |
| `correctness_output_strided_t1_float8_e4m3fn`<br>tokens=1
dtype=float8_e4m3fn layout=contiguous padded_output num_heads=128
nope_dim=128 rope_dim=64 | 1.824 / 1.696 | 5.056 / 5.024 | 2.772 / 2.962
|
| `correctness_output_strided_t1_float8_e5m2`<br>tokens=1
dtype=float8_e5m2 layout=contiguous padded_output num_heads=128
nope_dim=128 rope_dim=64 | 1.696 / 1.792 | 5.120 / 4.896 | 3.019 / 2.732
|
| `correctness_runtime_t2_padded_output_bfloat16`<br>tokens=2
dtype=bfloat16 layout=contiguous padded_output num_heads=128
nope_dim=128 rope_dim=64 | 2.080 / 2.081 | 5.377 / 5.312 | 2.585 / 2.553
|
| `correctness_runtime_t3_tail_float16`<br>tokens=3 dtype=float16
layout=contiguous num_heads=128 nope_dim=128 rope_dim=64 | 2.080 / 2.112
| 5.568 / 5.504 | 2.677 / 2.606 |
| `correctness_runtime_t4_tile_float8_e4m3fn`<br>tokens=4
dtype=float8_e4m3fn layout=contiguous num_heads=128 nope_dim=128
rope_dim=64 | 2.048 / 2.081 | 5.408 / 5.409 | 2.641 / 2.599 |
| `correctness_runtime_t5_combined_strides_float8_e5m2`<br>tokens=5
dtype=float8_e5m2 layout=both_strided padded_output num_heads=128
nope_dim=128 rope_dim=64 | 2.144 / 2.113 | 5.504 / 5.344 | 2.567 / 2.529
|
| `correctness_runtime_t31_tail_bfloat16`<br>tokens=31 dtype=bfloat16
layout=contiguous num_heads=128 nope_dim=128 rope_dim=64 | 2.336 / 2.272
| 6.272 / 6.304 | 2.685 / 2.775 |
| `correctness_runtime_t33_tail_float16`<br>tokens=33 dtype=float16
layout=contiguous num_heads=128 nope_dim=128 rope_dim=64 | 2.368 / 2.464
| 6.304 / 6.304 | 2.662 / 2.558 |
| `correctness_runtime_t1023_tail_float8_e4m3fn`<br>tokens=1023
dtype=float8_e4m3fn layout=contiguous num_heads=128 nope_dim=128
rope_dim=64 | 5.921 / 5.888 | 12.000 / 11.904 | 2.027 / 2.022 |
| `correctness_runtime_t1025_tail_float8_e5m2`<br>tokens=1025
dtype=float8_e5m2 layout=contiguous num_heads=128 nope_dim=128
rope_dim=64 | 5.920 / 5.952 | 11.936 / 12.096 | 2.016 / 2.032 |

Cake's sm_103a module for this kernel is unchanged, so the Cake family
now ships on sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added support for BF16 MoE operations with hidden sizes 2688 and 3072
on SM107a GPUs.
- Added SM107a support for DeepSeek fused routing, including multi-token
processing for selected workloads.
- Added split-CTA execution for MLA key concatenation on SM107a, with
automatic launch selection based on workload size.
- **Bug Fixes**
- Improved handling of invalid LoRA routes by ensuring affected output
columns are zeroed.
- **Tests**
- Added coverage for SM107a dispatch, split-CTA selection, and routing
correctness across varied workloads.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [feae9de](https://github.com/flashinfer-ai/flashinfer/commit/feae9de3580a6113df01637d7e7a17cc921afd4a)

- **作者**: eigen
- **时间**: 2026-10-18T22:46:46Z
- **提交信息**: perf(cake_diffusion): MiniMax-H3 FC1+SwiGLU 256x448 MXFP8 tile, PDL and packed epilogue rounding; prologue scale arithmetic (SM100/SM103) (#6720)

### [84f8428](https://github.com/flashinfer-ai/flashinfer/commit/84f8428303b2ec1d09af47f8cdf030eaa18ff49d)

- **作者**: eigen
- **时间**: 2026-10-18T22:45:06Z
- **提交信息**: deslop(cake_dsv4): share arch-identical SM100/SM103 kernels, fold NVFP4 launchers, drop dead host paths (#6731)

### [f41bfa1](https://github.com/flashinfer-ai/flashinfer/commit/f41bfa18fcee82fa199c2120b64956e671900334)

- **作者**: eigen
- **时间**: 2026-10-18T21:45:46Z
- **提交信息**: feat(cake_ssd_combined): Rubin sm_107a programs for the Mamba2 SSD combined prefill (#6746)

### [fedfed1](https://github.com/flashinfer-ai/flashinfer/commit/fedfed1371bf379da660d4f16a572907d5758c86)

- **作者**: eigen
- **时间**: 2026-10-18T18:48:15Z
- **提交信息**: perf(cake_quant_lora_gemm): faster SM90 FP8 LoRA GEMM mainloop (#6728)

`cake_quant_lora_gemm` fuses a quantized GEMM (FP8 E4M3 or NVFP4) with a
runtime BF16 low-rank LoRA term and BF16 output. The family ships 11
program variants: 6 FP8 and 5 NVFP4. This PR updates the two SM90 FP8
variants, `fp8_sm90` (form `acc2`) and `fp8_sm90_hint` (form
`acc2_hint`), with a faster mainloop schedule. The peer CTA of the 2-CTA
cluster now issues its own A box and LoRA D slab, while the W tile and
its LoRA B slab stay multicast. One elected lane per consumer warpgroup
releases a ring stage. Ring slot and parity come from running counters.
Output is bit-identical. The baseline is the previous Cake version of
the same two programs, already shipped in FlashInfer. Against it, the
new programs take 0.975 to 0.985 of the previous kernel time (table
below).

NVIDIA H100 80GB HBM3 (SXM, 700 W), sm_90a, CUDA 13.0. CUPTI kernel
time, cold L2, medians of paired rounds. Back to back: GPU throttled at
about 1330 MHz. Cooled: pause between rounds. Range in parentheses is
over all runs of the shape.

| Program | Shape (M x N x K, rank) | Thermal state | Previous (ms) |
New (ms) | New / previous |
|---|---|---|---:|---:|---:|
| `fp8_sm90_hint` | 131072 x 8192 x 32768, 64 | Back to back | 58.04 |
56.70 | 0.978 (0.978 to 0.985) |
| `fp8_sm90_hint` | 131072 x 8192 x 32768, 64 | Cooled | 51.37 | 50.27 |
0.979 (0.978 to 0.981) |
| `fp8_sm90` | 32768 x 32768 x 8192, 64 | Back to back | 14.57 | 14.25 |
0.980 (0.977 to 0.980) |
| `fp8_sm90` | 32768 x 32768 x 8192, 64 | Cooled | 12.86 | 12.54 | 0.977
(0.975 to 0.977) |

Cake also ships this family as FP8 on sm_100a and sm_103a (four
Blackwell programs) and as NVFP4 on sm_100a and sm_103a (five programs),
and the sm_90a coverage is the two FP8 programs in this PR.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d4b7d84](https://github.com/flashinfer-ai/flashinfer/commit/d4b7d8450b91f33805c0db5557f773a29b6a17bd)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-10-18T17:19:04Z
- **提交信息**: chore(artifacts): bump trtllm-gen BMM cubins for StepFun SwiGLU (#6726)

## 📌 Description

Bump `ArtifactPath.TRTLLM_GEN_BMM` / `CheckSumHash.TRTLLM_GEN_BMM` to
the trtllm-gen batched-GEMM (MoE) package that contains the StepFun
SwiGLU (`swigluStep`) FC1 kernels.

## 🔍 Related Issues

Fixes #6344. Follow-up to #6226.

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

Validated on B200 (SM100) against FlashInfer main, using the internal
build of the same package (cubin_publishing MR pipeline 74722898, same
8,350 kernel configurations as the main build) through
`FLASHINFER_CUBINS_REPOSITORY`:

- StepFun cases (`-k step` in `test_unified_moe.py`,
`test_unified_moe_fp8.py`, `test_trtllm_gen_fused_moe.py`, plus
`test_cake_stepfun_fused_moe.py`): **349 passed, 2 skipped, 0 failed**.
With the currently pinned package the same selection has 20 failures,
all the #6344 error.
- Regression over every single-GPU test that loads this package (26
files in `tests/moe`, `tests/autotuner`, `tests/jit`, `tests/trace`;
10,332 cases): **3,230 passed, 7,102 skipped, 0 failed**. All skips are
the static compatibility / speed skips in `tests/moe/utils.py`; none
come from a missing kernel.

Not covered locally: Rubin (SM107) execution, multi-GPU `moe_ep` tests,
and the `--full` matrices. Please rely on CI for those.

## Reviewer Notes

Pure artifact bump: two lines in `flashinfer/artifacts.py`.

The package must be published to the public Artifactory (manual
`publish-manual-tg-bmm-cubin` job in cubin_publishing pipeline 74757888)
before CI can download it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated the batched matrix multiplication artifact reference and its
integrity verification value. This keeps the artifact and its
verification information aligned; no user-facing behavior changes are
described in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5b0f0ca](https://github.com/flashinfer-ai/flashinfer/commit/5b0f0ca978ef28d05d71ee78637c3e445f32ddca)

- **作者**: Yang Xu
- **时间**: 2026-10-18T10:47:33Z
- **提交信息**: chore: update Attention, GEMM, and MoE code owners (#6732)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add @yanqinz2 as a code owner for the existing GEMM, Grouped GEMM, MoE,
and MoE EP rules, and @Anerudhan to all five Attention rules. This
covers the existing implementation and test paths while preserving every
previous owner and all unrelated rules.

## 🔍 Related Issues

No linked issue.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] `pre-commit` is available in the development environment.
- [x] The applicable hooks were run explicitly for this change.
- [x] `pre-commit run --files .github/CODEOWNERS` passed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Ownership metadata only; no runtime tests required.
- [x] `git diff --check` and changed-file hooks passed. Verified that
all 17 modified rules preserve existing owners. The final matching rules
include @yanqinz2 for the 2,147 tracked GEMM/MoE files and @Anerudhan
for the 368 tracked Attention files covered by those rules.

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

Confirmed that @yanqinz2 (maintain role) and @Anerudhan (admin role)
have the upstream repository access required for effective CODEOWNERS.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Chores**
* Updated ownership assignments for several project areas, adding
reviewers while retaining existing owners. This may affect how
contributions in those areas are routed for review. No end-user features
or application behavior changed.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c430dd0](https://github.com/flashinfer-ai/flashinfer/commit/c430dd088ab71aafe95ccfa25f1d99016220f608)

- **作者**: Julian
- **时间**: 2026-10-18T09:48:40Z
- **提交信息**: fix(sampling): cast per-request top_k to the dtype the kernel reads it with (#5348)

## 📌 Description

The two top-k sampling wrappers cast per-request thresholds to int32,
but the kernels read them using the output/index dtype. With int64
indices, this misreads thresholds and can read past the tensor.

Cast `top_k` to the output dtype in both wrappers. The regression covers
absent/int32/int64 indices and int32/int64 thresholds.
`top_k_renorm_probs` is unchanged.

## 🔍 Related Issues

Fixes #5347. This is a dtype bug, separate from the row-remapping fix in
#5340. The expanded tests in #5341 depend on this fix.

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

October 6 validation at `278d1d54` (RTX 4090 D, CUDA 12.8, torch 2.9.1):

- Dtype and #5340 row-remapping regressions: 24 passed.
- `pytest tests/utils/test_sampling.py -k 111`: 532 passed, 134 skipped.
- File-level pre-commit and `git diff --check`: passed.

## Reviewer Notes

The conflict resolution retains both regression tests. Code is unchanged
by the October 13 description cleanup.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Fixed per-request top-k and top-k/top-p sampling with 64-bit indices
so sampling limits are interpreted correctly.
* Prevented incorrect token selection and potential out-of-bounds reads
when index and sampling-limit types differ.

* **Tests**
* Added coverage across 32-bit and 64-bit indices and sampling limits,
verifying output types, valid results, input preservation, and expected
sampling ranges.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: JulianZJN <148066842+JulianZJN@users.noreply.github.com>

### [d32548e](https://github.com/flashinfer-ai/flashinfer/commit/d32548e085a4a0874f7483bd9ac4ab9091570d1f)

- **作者**: Gabriel Wu
- **时间**: 2026-10-18T07:48:37Z
- **提交信息**: feat(mla): read DeepSeek-V4.1 inline-scale KV records natively on SM120 (#6616)

## 📌 Description

FlashMLA's DeepSeek-V4.1 ABI (as of its 2026.09.30 release) stores each
token as one self-contained record: each token's data is followed by its
own scales. vLLM adopted it in vllm-project/vllm#61371. The SM120
sparse-MLA DSv4.1 path reads only footer-scale pages, in which a page
holds all its tokens' data and then all their scales.

The two layouts have the same record size (528 B), so a cache in the
other layout passes every shape check and decodes into silently wrong
output. This PR adds the inline-scale records as new, explicit formats.
The existing names keep their footer meaning.

| | main (SWA) cache | FP4 compressed cache |
|---|---|---|
| Footer (`fp8_dsv41`, `ue8m0_g32`) | per page: P × 512 B E4M3, then P ×
16 B UE8M0 | per page: P × 256 B E2M1, then P × 32 B E4M3 |
| Inline (new) | per token: 512 B E4M3 + 16 B UE8M0 (group 32) = 528 B |
per token: 256 B E2M1 + 32 B E4M3 (group 16) = 288 B |

As in FlashMLA, sparse indices address inline records as rows of the
whole cache, and a page stride must be a whole number of rows.

### API

- **SM120 wrapper / functional API:**
`kv_scale_format="ue8m0_g32_inline"` selects the inline records;
`"ue8m0_g32"` keeps the footer meaning.
- **`trtllm_batch_decode_with_kv_cache_mla`:** adds
`kv_cache_format="fp8_dsv41_inline"` and `"fp8_dsv41_inline_fp4_ca"`
(`backend="sparse"`). `backend="cake"` rejects them with a `ValueError`.
- **Writers:** the DSv4.1 FP8/FP4 pack and append writers take
`inline_scale=True`. They then write records at the cache's row pitch,
and append slots address rows.

The names follow the existing conventions: inline-scale vs footer-scale
vocabulary, and the record layout is part of the format identity rather
than a separate argument.

### Implementation

- **New model type:** a `DSV4_1_INLINE` model on the DSV4_1 routes. Its
record is the smem row, which DSV4_1 already pads to 528 B.
- **One copy per candidate:** the gathers issue one bulk copy per
candidate and drop the synchronous footer-scale load. The QK,
value-dequant and W-fold stages read the scales at +512 in smem.
- **Mixed-cache schedules:** they copy each 288 B FP4 record whole and
convert it straight into the inline KV row.
- **Full-BF16 kernels:** these load per thread, and address inline
records through an inline layout that has the footer layouts' offset
interface.
- **Row strides:** rows of both caches are addressed flat with validated
runtime row strides (16 B multiples of at least the record size), as for
GLM53_NOPE. The attention metadata gains the extra cache's row stride,
appended at the end so positional initializers keep working.
- **Prep refactor:** `qk_k_scale_selector` and `kv_scale_fp32` are now
keyed on `SCALE_FORMAT` instead of `SCALE_IN_KV_SMEM`, so an inline
model may store UE8M0 bytes. Every existing model keeps its reads.
- **Calibration:** gains a `dsv4_1_inline` family, keyed on the cache's
own page size. No device profiles are committed.
- **Bit-exact:** the math order is unchanged, so inline outputs and LSE
equal the footer form's bit for bit.

### Performance

Measured on an RTX PRO 6000 Blackwell Server Edition with CUPTI kernel
time, cold L2, median µs, on the same rows and indices. Each layout uses
its own calibrated profiles. "512" is a single cache with top-k 512;
"128 + fp4" is main top-k 128 plus 512 FP4 compressed candidates. Footer
pages hold 64 tokens.

Default precision:

| cache | heads | tokens | footer | inline | inline / footer |
|---|---|---|---|---|---|
| 512 | 8 | 1 | 13.3 | 11.7 | 0.88 |
| 512 | 64 | 1 | 14.1 | 12.7 | 0.90 |
| 512 | 64 | 16 | 34.3 | 30.4 | 0.89 |
| 512 | 64 | 64 | 85.4 | 78.3 | 0.92 |
| 512 (prefill) | 64 | 1024 | 1058.9 | 961.5 | 0.91 |
| 128 + fp4 | 8 | 1 | 14.8 | 12.4 | 0.84 |
| 128 + fp4 | 64 | 16 | 40.4 | 34.3 | 0.85 |
| 128 + fp4 | 16 | 64 | 49.0 | 39.4 | 0.80 |
| 128 + fp4 | 64 | 64 | 111.6 | 101.8 | 0.91 |
| 128 + fp4 (prefill) | 64 | 1024 | 1381.5 | 1160.2 | 0.84 |

Full-BF16 compute precision:

| cache | heads | tokens | footer | inline | inline / footer |
|---|---|---|---|---|---|
| 512 | 64 | 64 | 117.1 | 112.6 | 0.96 |
| 512 (prefill) | 64 | 1024 | 1259.2 | 1212.6 | 0.96 |
| 128 + fp4 | 32 | 64 | 88.5 | 83.1 | 0.94 |
| 128 + fp4 (prefill) | 64 | 1024 | 1644.2 | 1520.6 | 0.92 |

- **Default precision:** inline is 4–20% faster than footer pages across
all measured shapes.
- **Full BF16:** inline is up to 8% faster. Small FP4 decode is the
exception, within about 1% (one shape 1.2% slower). The BF16 kernels are
compute-bound with per-thread loads.
- **Row-stride cost:** making the extra cache's row stride a runtime
value costs nothing measurable (after/before 0.997–1.001; BF16 1.000).
- **Reproducing:** `benchmarks/bench_sparse_mla_sm120.py` has a DSv4.1
footer-vs-inline section.

## 🔍 Related Issues

- vllm-project/vllm#61371: vLLM's interleaved V4.1 KV records (FlashMLA
2026.09.30).
- vllm-project/vllm#59846: SM120 DSv4.1 decode through FlashInfer's V4.1
sparse MLA; it switches to these formats. End to end,
DeepSeek-V4.1-Flash chat GSM8K on SM120 TP4 scores 0.946
(`fp8_dsv41_inline`) and 0.948 (`fp8_dsv41_inline_fp4_ca`), against
0.945 / 0.947 with the footer formats before vLLM's layout change.
- #5197 introduced the SM120 DSv4.1 support this extends.

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

**New file:** `tests/attention/test_sparse_mla_sm120_dsv41_inline.py`,
117 tests, covering:
- cache-geometry checks;
- byte-level writer tests (packed blocks, padded row pitches, pitched
one-row pages);
- a cross-check of the FP8 append writer against vLLM's V4.1 MXFP8 cache
writer in packed blocks;
- inline-vs-footer decode and prefill equality (exact output and LSE)
across compute precisions including full BF16, with no / FP8 / FP4 extra
cache, packed-block strides, and padded main and extra row pitches;
- native model selection, CUDA graph capture, and Cake rejection.

**Existing suites:** `test_sparse_mla_sm120.py` (587), cache contracts
(53), binding guards (9), policy (52), execution (59), LSE (54),
calibration (98) and Cake DSv4.1 mixed (117 passed, 1 skipped) all pass
on SM120.

**Known pre-existing failure:** in the precision suite,
`test_nvfp4_precision_envelope_and_warmup` fails identically on the base
commit without this change.

## Reviewer Notes

- **Footer deprecation:** FlashInfer's sparse-MLA cache formats
otherwise mirror FlashMLA's ABI, and FlashMLA's V4.1 ABI is now
inline-scale. I kept `fp8_dsv41` / `ue8m0_g32` as the footer form,
because they shipped in 0.7.1/0.7.2 and the layouts can't be told apart
at run time. Should the footer form be deprecated in favor of the inline
one?
- **Effect beyond DSv4.1:** the binding's one-row-page rule applies to
every inline-scale format, including GLM53_NOPE. A GLM53_NOPE cache
built from one-row pages with a padded pitch is now read at that pitch,
and its prefill accepts it where it used to reject it. The existing GLM
tests pass. I can split this into its own commit if preferred.
- **Writer FFI change:** the four DSv4.1 writer FFI entry points gain an
`inline_scale` argument. Existing direct callers in the tests pass
`False`.
- **Not covered here:** the experimental SM100 Frost DSv4.1 decode
(`flashinfer/deepseek_v41.py`) also stores footer-scale pages. Cake's
SM120 mixed-cache family stays footer-only by design.

This PR was written with AI assistance (Claude); I reviewed every line.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added inline-scale FP8 and FP4 cache formats for DeepSeek-V4.1 sparse
MLA, with support for packing, appending, decode, and prefill.
- Added support for inline-scale caches with optional extra FP4 caches,
padded row pitches, and explicit FP8/BF16 precision.
- Expanded calibration and benchmarking coverage for inline and footer
scale placement.
- **Bug Fixes**
- Improved cache layout and stride validation for main and extra caches
across supported execution paths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [02afd49](https://github.com/flashinfer-ai/flashinfer/commit/02afd49e788a0e37627068b1bef6c1351555daab)

- **作者**: Zihao Ye
- **时间**: 2026-10-18T07:46:08Z
- **提交信息**: perf(cake_dsv4): route 16/32/64-head FP8 prefill rows to the single-CTA M64 body (#6724)

## Summary

The Cake DSv4 FP8 dispatcher sent every prefill request of at most 64
heads (`max_q_len >= 257`) to the low-head prefill producer
(`fp8_lowhead_prefill`). The single-CTA M64 persistent body already
served 64-head rows below that length; its head count is a runtime
argument with the heads past it predicated, so it serves 16 and 32 heads
as well. On GB300 it beats the low-head producer on every 16/32/64-head
prefill row of the DSv4 contract with the same oracle, so prefill rows
of 16, 32 and 64 heads now take the M64 program the item width selects
(`fp8_h64_prefill_source_persistent_m64` at width 128, `_multi_tile`
otherwise). 8-head prefill rows keep the low-head producer (not measured
on the M64 body). No kernel changes.

## Measurements

GB300 (sm_103a), both routes on the same inputs in the same lock hold,
cooled medians (CUPTI, cold L2, 100 ms warmup + 1 s timed, one serial
cool-down launch at the maximum clock), FP32 torch reference, tolerance
0.1 for both routes; two ragged sequences per row (the contract's
split), 131072-token pools, E4M3 latents, width = main + extra
selection. Rows are the DSv4 contract's prefill rows (`max_q_len >=
257`).

| row | tokens | width | low-head prefill (us) | M64 body (us) |
low-head / M64 |
|---|---|---|---|---|---|
| h16-k128-t512-single | 512 | 128 | 35.4 | 11.8 (box) | 2.99 |
| h16-k128-t512-dual | 512 | 256 | 48.7 | 22.3 (multi_tile) | 2.19 |
| h16-k128-t2048-single | 2048 | 128 | 134.2 | 29.6 (box) | 4.54 |
| h16-k128-t2048-dual | 2048 | 256 | 183.0 | 63.4 (multi_tile) | 2.89 |
| h16-k128-t8192-single | 8192 | 128 | 526.6 | 100.5 (box) | 5.24 |
| h16-k128-t8192-dual | 8192 | 256 | 710.4 | 210.8 (multi_tile) | 3.37 |
| h16-k512-t512-single | 512 | 512 | 78.4 | 36.8 (multi_tile) | 2.13 |
| h16-k512-t512-dual | 512 | 1024 | 137.6 | 66.8 (multi_tile) | 2.06 |
| h16-k512-t2048-single | 2048 | 512 | 295.7 | 105.7 (multi_tile) | 2.80
|
| h16-k512-t2048-dual | 2048 | 1024 | 528.2 | 204.7 (multi_tile) | 2.58
|
| h16-k512-t8192-single | 8192 | 512 | 1155.1 | 379.9 (multi_tile) |
3.04 |
| h16-k512-t8192-dual | 8192 | 1024 | 2076.1 | 766.3 (multi_tile) | 2.71
|
| h32-k128-t512-single | 512 | 128 | 35.9 | 12.7 (box) | 2.83 |
| h32-k128-t512-dual | 512 | 256 | 49.5 | 22.9 (multi_tile) | 2.16 |
| h32-k128-t2048-single | 2048 | 128 | 137.9 | 32.2 (box) | 4.28 |
| h32-k128-t2048-dual | 2048 | 256 | 185.7 | 64.2 (multi_tile) | 2.89 |
| h32-k128-t8192-single | 8192 | 128 | 538.1 | 109.0 (box) | 4.94 |
| h32-k128-t8192-dual | 8192 | 256 | 723.8 | 217.8 (multi_tile) | 3.32 |
| h32-k512-t512-single | 512 | 512 | 79.3 | 37.2 (multi_tile) | 2.13 |
| h32-k512-t512-dual | 512 | 1024 | 138.4 | 67.2 (multi_tile) | 2.06 |
| h32-k512-t2048-single | 2048 | 512 | 297.8 | 106.7 (multi_tile) | 2.79
|
| h32-k512-t2048-dual | 2048 | 1024 | 531.4 | 205.7 (multi_tile) | 2.58
|
| h32-k512-t8192-single | 8192 | 512 | 1166.9 | 383.7 (multi_tile) |
3.04 |
| h32-k512-t8192-dual | 8192 | 1024 | 2089.3 | 769.3 (multi_tile) | 2.72
|
| h64-k128-t512-single | 512 | 128 | 39.5 | 16.0 (box) | 2.47 |
| h64-k128-t512-dual | 512 | 256 | 53.2 | 24.5 (multi_tile) | 2.17 |
| h64-k128-t2048-single | 2048 | 128 | 151.2 | 41.1 (box) | 3.68 |
| h64-k128-t2048-dual | 2048 | 256 | 200.4 | 68.8 (multi_tile) | 2.91 |
| h64-k128-t8192-single | 8192 | 128 | 593.8 | 138.1 (box) | 4.30 |
| h64-k128-t8192-dual | 8192 | 256 | 784.4 | 246.1 (multi_tile) | 3.19 |
| h64-k512-t512-single | 512 | 512 | 83.6 | 38.3 (multi_tile) | 2.18 |
| h64-k512-t512-dual | 512 | 1024 | 143.7 | 68.0 (multi_tile) | 2.11 |
| h64-k512-t2048-single | 2048 | 512 | 315.0 | 109.3 (multi_tile) | 2.88
|
| h64-k512-t2048-dual | 2048 | 1024 | 550.8 | 208.3 (multi_tile) | 2.64
|
| h64-k512-t8192-single | 8192 | 512 | 1235.7 | 395.7 (multi_tile) |
3.12 |
| h64-k512-t8192-dual | 8192 | 1024 | 2168.9 | 779.1 (multi_tile) | 2.78
|

36 rows: low-head / M64 median 2.81, min 2.06, max 5.24.

## Tests

- `tests/mla/test_cake_dsv4.py`: the FP8 prefill predicate test now
expects the M64 program for 16/32/64 heads (both cache layouts) and the
low-head producer for 8 heads; 246 passed.
- `tests/mla/test_cake_dsv4_hardening.py -k fp8` on GB300 (sm_103a): 113
passed, 2 skipped; the 16/32/64-head FP8 prefill cases run the M64 body
through the public host path against the reference. The 32-head FP8
prefill example of the descriptor-slab tests names its new route (both
routes pass their descriptors by value on sm_103a, so those two tests
skip as before). The three `test_trtllm_gen_*` FP8 cases failed to
JIT-build the trtllm-gen module in this environment, unrelated to this
change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated FP8 prefill routing for query lengths of 257 or more.
Workloads with 16, 32, or 64 heads now use a persistent multi-tile
route, while 8-head workloads continue using the existing low-head
route.
* This routing behavior applies across the tested batch sizes and cache
page layouts.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ff2cc8c](https://github.com/flashinfer-ai/flashinfer/commit/ff2cc8c793226ae42f3d8df8a41558b8e799c91e)

- **作者**: eigen
- **时间**: 2026-10-18T07:37:32Z
- **提交信息**: deslop(cake_vsa): fold duplicated sources and remove the SM90 CuTe DSL build (#6719)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

The Cake variable block-sparse attention (VSA) family had duplicated
kernel and launcher sources, unused host code, and a second rendering of
the SM90 kernels in CuTe DSL. This PR merges the duplicated sources,
removes the unused code and the CuTe DSL rendering, and adds the CPU
planner tests to CI. Generated device code does not change: the
SM100/SM103 change was checked for identical SASS, and no SM90 device
translation unit is modified. Launch behaviour, routes, the public API,
defaults and error types also stay the same. `backend="cake_cute"` is
still accepted as an alias of `"cake"`.

Scope:
- SM100/SM103 kernels: `csrc/cake_vsa`, `flashinfer/jit/cake_vsa.py`,
`flashinfer/cake_vsa.py`.
- SM90 (Hopper) kernels: `csrc/cake_vsa_sm90`,
`flashinfer/jit/cake_vsa_sm90.py`, and the planner
`flashinfer/cake_vsa_sm90.py`. Both are reached through
`VariableBlockSparseAttentionWrapper(backend="cake")` in
`flashinfer/sparse.py`.
- Until this PR, the CuTe DSL rendering of the SM90 kernels lived in
`flashinfer/experimental/cake_vsa_sm90_cute/` (`backend="cake_cute"`).

Base: `main` at `04054522f`. Head: `b3d98f2da`.

| Commit | Change | Size effect |
|---|---|---|
| `ddae7c31c` | FP16 block-128 kernel merged into the BF16 source |
kernel sources 2 files / 3,038 lines -> 1 file / 1,574 lines |
| `17c445e86` | Unused SM90 host code removed, stale config fixed, CPU
tests added to CI | `flashinfer/jit/cake_vsa_sm90.py` 194 -> 173 lines |
| `77e31f6e6` | SM90 manifest replaced by a stage table, 14 launchers
merged into one | `csrc/cake_vsa_sm90` 31 files / 52,833 lines -> 17
files / 46,940 lines; diff 18 files, +430 / -6,166 |
| `b3d98f2da` | CuTe DSL rendering removed | diff 25 files, +59 /
-120,510 |

## Changes

### 1. `ddae7c31c` cake_vsa: fold the FP16 block-128 kernel into the
BF16 source through `CAKE_VSA_FP16`

- `csrc/cake_vsa/cake_vsa_blk128_fp16_compact.cu` (1,519 lines) was a
copy of `cake_vsa_blk128_compact.cu` with 38 lines changed:
  - the kernel symbol
  - four shared-memory typedefs
  - three conversion-intrinsic blocks
  - four tcgen05 instruction-descriptor immediates

The BF16 source now holds those lines behind `#if CAKE_VSA_FP16` guards,
and the FP16 profile points at that source. Kernel sources go from 2
files / 3,038 lines to 1 file / 1,574 lines. Resolving the guard either
way reproduces the matching former file byte for byte.
- The merge required a loader fix. `prepare_cake_vsa_cubin` passed no
`-D` defines to the device compile; only the launcher got the profile
defines. It now passes each profile's route defines for every profile.
The other eight profiles use none of these macros, so their device text
does not change. The gate compared those profiles as well.
- Launcher, routes, public API, defaults and error types are unchanged.
- Tests: the file-name assertion in the planning test now expects the
shared source. Two CPU tests pin the (source, defines) pairs and the
cubin command.

### 2. `17c445e86` cake_vsa: remove dead SM90 host code, fix stale
config, enroll CPU planner tests in CI

- Removed helpers that nothing calls:
- `cake_vsa_sm90_launch` and `build_all_cake_vsa_sm90_modules`, plus
their `__all__` rows, from `flashinfer/jit/cake_vsa_sm90.py` (194 -> 173
lines)
  - `compile_all` from the CuTe package

  A grep of the whole repository finds no callers.
- Moved `REFERENCE_CLUSTER_CAPACITY_H100_SXM` from
`flashinfer/cake_vsa_sm90.py` into
`tests/experimental/test_cake_vsa_sm90.py`, the only file that reads it.
- Removed the stale `vsa_sm90_blk64` candidate from
`benchmarks/bench_cake_vsa_sm90.py`.
- `.pre-commit-config.yaml`: added `csrc/cake_vsa_sm90/.*` to the
clang-format exclusion. These are generated sources pinned by hash, like
the other exported packages.
- `flashinfer/sparse.py`: fixed the docstring sentence about the CuTe
build's dependency.
- CI: `scripts/task_jit_run_tests_part5.sh` now runs:
  - `tests/attention/test_cake_vsa_planning.py` (CPU, 32 tests)
- the CPU subset of `tests/experimental/test_cake_vsa_sm90.py`, selected
with `-k` on the planner tests (36 tests; no GPU-guarded test is
selected)

  Before this PR, no CI part script ran any of the VSA test files.
- No CUDA source, header or manifest changes.

### 3. `77e31f6e6` cake_vsa: replace the SM90 manifest with a stage
table and fold the 14 launchers into one source

- The SM90 loader read only 382 of the 2,201 lines in
`cake_vsa_sm90_manifest.json`. A 14-row `_STAGES` table in
`flashinfer/jit/cake_vsa_sm90.py` replaces it. Each row holds the
stage's:
  - module identity
  - launcher shim-namespace hash
  - thread-block size
  - dynamic shared memory
  - cluster size
  - ABI kind
  - device-source sha256

One more sha256 pins the shared launcher. The issue proposed dropping
the re-hash, but this PR keeps the pins: 15 hashes replace a 30-entry
inventory and give the same protection.
- The 14 `*_binding.cu` launchers (4,176 lines) differed only in those
per-stage values and on two structural axes: ABI kind (small-selection
plan, split-KV plan or persistent) and cluster launch. They are merged
into one `cake_vsa_sm90_binding.cu` (484 lines).
- Six `-DCAKE_VSA_SM90_*` defines, derived by the loader from the table,
select each stage's configuration.
  - Each of these defines has an `#error` guard.
- The cluster-grid check passes the cluster size through one extra macro
level, so the check macro's stringified message still shows the literal
value.
- Device translation units are not modified.
- `csrc/cake_vsa_sm90` goes from 31 files / 52,833 lines to 17 files /
46,940 lines (commit diff: 18 files, +430 / -6,166).
- Two new CPU tests, both added to the part5 subset:
- `test_stage_table_builds_every_stage_from_the_shared_launcher`:
per-stage sources and defines, re-hashed pins, and `ValueError` for an
unknown stage
  - `test_stage_table_geometry_matches_the_stage_names`

### 4. `b3d98f2da` cake_vsa: keep the CUDA SM90 build, remove the CuTe
DSL rendering

- Deleted `flashinfer/experimental/cake_vsa_sm90_cute/` (19 files) and
`tests/experimental/test_cake_vsa_sm90_cute.py`, 120,426 lines together.
- Removed the `engine` / `_run_cute` paths from the planner
(`flashinfer/cake_vsa_sm90.py` 1,452 -> 1,401 lines).
- Removed the CuTe parametrizations from
`test_queue_kernel_matches_the_static_kernel_bit_exact` and
`test_odd_single_block_tile_never_stores_from_the_idle_warpgroup`. Both
tests now run against CUDA only.
- Removed the CuTe benchmark candidate and the package's ruff exclusion
in `pyproject.toml`.
- `VariableBlockSparseAttentionWrapper(backend="cake_cute")` is still
accepted as an alias of `"cake"`. The docstring says so, and one test
pins the alias.
- CUDA kernels, routes, public API, defaults and error types are
unchanged.
- Commit diff: 25 files, +59 / -120,510.
- Reasons, from the H100 measurements under Validation:
  - The CuTe rendering is not faster (GPU-time ratio geomean 0.981).
  - Its output is bit-identical to the CUDA build.
  - It costs about 130-140 us more host time per `run()`.
- It only worked from a source checkout, because the wheel never shipped
its manifest (`pyproject.toml` has no package-data entry for it).

### 5. `c14a696932` cake_vsa: skip the driver cluster-capacity test
below Hopper

-
`tests/experimental/test_cake_vsa_sm90.py::test_cluster_capacity_resolves_from_the_driver`
(pre-existing) queries `cuOccupancyMaxActiveClusters`, which only exists
for thread block clusters (Hopper and newer), but was guarded by
`torch.cuda.is_available()` alone. Running the file on an A10G failed
with `CUDA_ERROR_INVALID_CLUSTER_SIZE`; it now skips below compute
capability 9.0, like the other SM90 tests in the file. Test-only change.

## Validation

### Equivalence gates

- Commit 1: SASS compared per (profile, architecture) on sm_100a and
sm_103a. All 10 entries (the 2 merged sources plus the 8 unaffected
profiles) are identical, and the preprocessed text is identical.
- Commit 3: all 14 launchers identical on GB300. Each stage's original
launcher was preprocessed and compared with the shared launcher
preprocessed using that stage's defines. The comparison used a
whitespace-free token stream with:
  - stringified macro arguments joined
  - `u` suffixes dropped
  - the check macro's `__FILE__`/`__LINE__` tokens normalized

### Tests per commit

- After commit 1: `tests/attention/test_cake_vsa.py` +
`tests/attention/test_cake_vsa_planning.py` passed 48 on GB300 and 48 on
B200.
- After commit 2, on GB300: CPU subset 36 passed, planning 32 passed,
`test_cake_vsa.py` 16 passed. The removed names no longer appear
anywhere in `flashinfer/`, `tests/`, `benchmarks/` or `scripts/`.
- After commit 3, on GB300: CPU subset 38 passed, planning 32 passed,
`test_cake_vsa.py` 16 passed.

### H100 (sm_90a)

- Baseline on `main` `04054522f` with `nvidia-cutlass-dsl==4.7.0`:
`tests/attention/test_cake_vsa_planning.py`,
`tests/experimental/test_cake_vsa_sm90.py` and
`tests/experimental/test_cake_vsa_sm90_cute.py` gave 171 passed, 0
failed (256 s).
- Note for maintainers: with cutlass-dsl 4.8.1, the 38 CuTe tests fail
at import with `make_kwargs_wrapper() got an unexpected keyword argument
'map_dataclass_to_tuple'`. `requirements.txt` pins `>=4.6.2a0`, which
allows 4.8.1.
- Final head: `tests/attention/test_cake_vsa_planning.py` + the full
`tests/experimental/test_cake_vsa_sm90.py` at the final head: 136
passed, 0 failed (169 s); at the commit-3 head (CuTe tests still
present) 137 passed, 0 failed (203 s)

### CuTe vs CUDA measurement (H100, using the issue's protocol)

GPU time came from `benchmarks/bench_cake_vsa_sm90.py --candidate
cake_cute --baseline cake --pairs 3 --repeat-iters 50`: CUPTI kernel
time, cold L2, 20 shapes, median of 6 AB/BA rounds. Host time came from
1,000 timed calls after 100 warm-ups, on 4 shapes from 1x64x64 to
7x16384x16384.

| Metric | `cake` (CUDA) | `cake_cute` (CuTe DSL) |
|---|---|---|
| GPU latency, geometric mean over 20 shapes | 32.8 us | 33.4 us |
| Host time per `run()`, median (range over 4 shapes) | 23.9-25.7 us |
154.3-165.6 us |

- GPU-time ratio cake/cake_cute: geomean 0.981, min 0.954
(`h1-m64-n64-k1`), max 1.015 (`h1-m1024-n1024-k16`).
- By shape, the CuTe build is 1-5% slower on 13, within 1% on 5, and
about 1.5% faster on 2.
- Host overhead: the CuTe build costs about 130-140 us more per call.
The issue's earlier record said about 11 us.
- Output: the benchmark's own output check reports max abs error 0.0 on
all 20 shapes. The bit-exact parity test
`test_every_stage_matches_reference_and_cuda_build` gave 26 passed (13
stages the planner can reach x 2 scales), and the CuTe output matches
the CUDA output bit for bit.

### SM100 at the final head

- GB300: `tests/attention/test_cake_vsa.py` +
`test_cake_vsa_planning.py` 48 passed, 0 failed; CPU subset of
`test_cake_vsa_sm90.py` 38 passed; planning 32 passed (final tree)
- B200: `tests/attention/test_cake_vsa.py` + `test_cake_vsa_planning.py`
48 passed, 0 failed (85 s); CPU subset of `test_cake_vsa_sm90.py` 38
passed; planning 32 passed (final head)

## Not in this PR

- Dropping the debug ABI (the `tl`/`dbg` parameters of the persistent
and static kernels): needs regenerated kernels, so it is not a
mechanical change.
- SM100: regenerating the ABI-1/3 kernels without the temperature-LSE
parameters: needs a generator change.
- SM100 ultrasparse row (`cake_vsa_ultrasparse_bsr.cu`): whether to
delete it or fall back depends on the owner's benchmark decision.
- Regenerating the 12 small SM90 kernels as one template over (KMAX,
split, cluster): follow-up for the kernel producer.

Closes #6640

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added FP16 support for compact 128-block sparse attention on Blackwell
GPUs.

* **Bug Fixes**
* Fixed cubin compilation when FP16 and BF16 profiles share a source by
applying the selected profile’s build options.

* **Changes**
* SM90 planning now uses the CUDA JIT path. The separate CuTe
implementation and its experimental interfaces are no longer available.
  * Updated benchmark workspace allocation and reference descriptions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ee381fa](https://github.com/flashinfer-ai/flashinfer/commit/ee381fa6dd649605398b16e4000b667b279c4057)

- **作者**: Zihao Ye
- **时间**: 2026-10-18T07:33:59Z
- **提交信息**: fix(cake_mla): skip empty KV splits in the FP8 page-64 MLA decode producer (#6718)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes non-finite output from `backend="cake"` of
`trtllm_batch_decode_with_kv_cache_mla` on the FP8 page-64 route
(`mla_fp8_page64_pdl`: FP8 E4M3, 128 heads, page 64, dense, no sink,
SM100 and SM103). It happens whenever a work
item has a KV split with no tile.

**When a split is empty.** `plan_num_split` sizes the split count from
the longest row (and returns at least 2). The
producer cuts each row's `tiles = ceil(len / 128)` into runs of
`ceil(tiles / num_split)`, so a split starts past the
row's last tile whenever:

- a short row shares the batch with a long one, e.g. kv lens (600, 2)
give 3 splits and the 2-key row has 1 tile; or
- the split count does not divide the tiles, e.g. 8 rows of 4096 keys: 9
splits of 4 tiles over 32 tiles leave split 8
of every row empty. A single row of at most 128 keys always gets 2
splits, one of them empty.

**Cause.** An empty split still ran the tile pipeline:

- Its load warp primed K for tile 0 and drained V for tile `my_n_tiles -
1`, through a page-table index at or below
  the row's start.
- Its MMA warp issued the drain PV at position `my_n_tiles - 1`. With
`my_n_tiles <= 0` that is a position before
the barrier's first phase: the parity wait on `p_full` passed at once,
and the PV multiplied whatever was in
  shared memory as P into O.
- The epilogue stored stats `(-inf, 0)`, so the reducer weights the
split by 0. But `0 * NaN` is NaN: when the
stale bytes held an FP8 NaN (`0x7F`), the whole row came back
non-finite.

**Fix.** An empty split (`my_n_tiles <= 0`) now loads no K or V, and
issues no PV:

- The load warp skips its K prime, steady loop and V drain.
- The MMA warp keeps its drain's control flow. Its two drain waits take
the parity of the barrier's preceding
phase, which a barrier that never advanced reports complete. The drain
MMAs are issued by no thread, through a
predicate ANDed into the elected leader, so the commits after them
signal at once.
- The epilogue stores the producer's scrubbed tensor memory: O = 0,
stats `(-inf, 0)`. The reducer weights that by 0.

The change is in the two producer sources of the route (SM100 and SM103,
one hunk each in the load and MMA warps).
The planner and the reducer do not change.

The MMA-warp part is predicated rather than branched for speed, not
correctness. A branch around the drain, never
taken by a non-empty split, made b4 x kv4096 about 8% slower: it changes
how the whole program is compiled. The
details are under Performance.

**Test.** `test_trtllm_mla_blackwell_fp8_page64_empty_splits[(600, 2),
(2, 600)]`:

- The setup fills every SM's shared memory with `0x7F` before each of
eight calls (a small `load_inline` kernel, as
  `tests/comm/test_trtllm_allreduce_reduction.py` builds one).
- It checks that the output is finite and matches the float32 reference
at the FP8 tolerance.
- The 2-key row's two keys are identical, so its expected output does
not depend on how many of them the route attends.

## 🔍 Related Issues

Follows #6629, which changed the key count this route passes (same
route; this PR touches only the device sources
and adds a test, no overlap with its two lines in
`cake_trtllm_mla_blackwell.py`).

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

| Test | main + new test | this PR |
|---|---|---|
| `test_trtllm_mla_blackwell_fp8_page64_empty_splits` | 2 failed (3 of 3
runs) | 2 passed (3 of 3 runs) |
| `test_trtllm_gen_mla.py -k "blackwell or cake"` | 31 passed, 4 failed
| 35 passed |

On main, the 4 failures are the new test and
`test_trtllm_mla_blackwell_fp8_page64_attends_the_last_key[1, 2]`. The
latter fails because the shared-memory fill leaves its kv-600 row (5
tiles over 4 splits) with an empty split.

Without the fill, main already returns non-finite rows on ordinary
shapes through the public API. In one process on
GB300, inputs `randn x 0.05`:

| Shape (q_len 1 unless noted) | splits | main | this PR |
|---|---|---|---|
| kv (600, 2) | 3 | row 1 non-finite | finite |
| 8 x kv 4096 | 9 | non-finite rows | finite |
| 4 x q_len 2, kv 4096 | 9 | non-finite rows | finite |

On the shapes with no empty split, the outputs are bitwise identical to
main.

`compute-sanitizer`, filtered to the Cake MLA kernels, on kv (600, 2),
(2, 600) and 8 x 4096:
- memcheck: 0 errors.
- racecheck: 0 hazards.
- synccheck: 0 errors on the two short-row shapes. On 8 x 4096 it
reports "Missing wait" at a steady-loop barrier,
  with the same count (64) on main and this PR.

**Performance** (GB300, public API, cold L2, medians in µs; old and new
interleaved in one process; the two kernels
are the page-64 producer and the split reducer):

| Shape | GPU A main → PR | GPU B main → PR |
|---|---|---|
| b1 q16 kv4096 (4 splits) | 16.50 → 16.45 | 16.40 → 16.35 |
| b4 q1 kv4096 (16 splits) | 16.00 → 15.98 | 15.92 → 15.94 |
| b32 q1 kv2048 (2 splits) | 21.50 → 21.31 | 21.50 → 21.28 |
| b64 q1 kv4096 (2 splits) | 56.02 → 55.78 | 55.90 → 55.74 |
| b16 q1 kv1024 (4 splits) | 13.70 → 13.70 | 13.63 → 13.65 |
| b1 q1 kv8192 (32 splits) | 16.24 → 16.19 | 16.02 → 16.03 |
| b8 q1 kv4096 (9 splits) | 18.37 → 18.37 | 18.30 → 18.30 |
| b4 q2 kv4096 (9 splits) | 17.12 → 17.18 | 17.12 → 17.18 |
| b2 q1 kv(600, 2) (3 splits) | 10.72 → 10.67 | 10.75 → 10.82 |

These are back-to-back medians of two interleaved rounds of
`warmup_ms=100, bench_ms=1000`; the cooled medians (a
delay kernel between calls) agree.

b4 q1 kv4096 and b2 q1 kv8192 have bimodal times: each input allocation
lands in a fast or a slow mode (about
16.0 and 17.3 µs for b4). So they are compared as the mean over 16
allocations, in separate processes, with the
number of allocations in the slow mode:

| Shape | main | this PR |
|---|---|---|
| b4 q1 kv4096, GPU A (5 processes) | 16.39 / 16.31 / 16.22 / 16.54 /
16.47 (21 of 80 slow) | 16.46 / 16.40 / 16.13 / 16.63 / 16.51 (22 of 80
slow) |
| b4 q1 kv4096, GPU B (4 processes) | 16.54 / 16.34 / 16.44 / 16.36 (19
of 64 slow) | 16.88 / 16.49 / 16.53 / 16.62 (31 of 64 slow) |
| b2 q1 kv8192, GPU A (2 processes) | 18.85 / 18.81 | 18.96 / 18.87 |
| b2 q1 kv8192, GPU B (1 process) | 18.82 | 19.07 |
| b1 q16 kv4096, GPU A / B | 16.52, 16.53 / 16.39 | 16.51, 16.51 / 16.39
|

The b4 row is within 0.5% on GPU A; on GPU B this PR lands in the slow
mode somewhat more often.

**Why a branch was slower.** A first version of this fix branched around
the MMA warp's drain for an empty split.
At b4 q1 kv4096 that version landed in the slow mode in nearly every
allocation (17.24–17.58 µs).

- A semantically null control branch, always taken and wrapped around
the drain, did the same.
- A plain 32-byte shift of the MMA warp's code (two `nanosleep 0`) did
not, so loop alignment is not the cause.
- Per-kernel CUPTI spans show the producer's own time unchanged (10.43
vs 10.50 µs). The split reducer, launched
behind the producer, finished 5.6 µs after it on main and 7.1 µs after
it with the branch.
- In SASS the branch changes the whole program's layout and schedule,
not just the drain:
- the role dispatch for warps 8–11 at the role entry becomes a
constant-bank jump table
(`LDC R2, c[0x2][R0+0xc]` / `BRX R2`) instead of `UISETP` / `BRA.U` on
the uniform warp index;
- the drain's trailing `UTCBAR` commits are split across a new
`BSSY.RECONVERGENT` region;
- about 90 instructions in the softmax and correction roles are
rescheduled.
- Removing only the jump table (deriving the MMA warp's role test from a
second `shfl`) did not recover the fast
  mode. I did not narrow it to a single instruction.

The predicated form keeps main's control flow (the same `BRX` and `BSSY`
count, MMA-warp entry at the same address).
In the MMA warp the only change is `@P UTCQMMA` with a uniform
`VOTEU.ANY` predicate; about 30 instructions differ
elsewhere.

## Reviewer Notes

The behavior change is in the two
`cake_trtllm_mla_blackwell_*_kernel.cu` producers:
- the load warp's `if (my_n_tiles_3 > 0)`; most of the diff is its
re-indentation (`git diff -w` shows the changed
  lines);
- the MMA drain's `drain_has_tile` (the two wait parities and the MMA
issue predicate).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Empty KV splits now complete without accessing K/V data or performing
unnecessary final attention work. They produce zero outputs and `(-inf,
0)` statistics, while nonempty splits retain their existing behavior.

* **Tests**
* Added regression coverage for empty KV splits, checking that repeated
decodes produce finite outputs matching a PyTorch reference.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4615
- **最后更新**: 2026-10-18T23:08:06Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: lpc0220

## AI分析总结

## FastVideo 仓库昨日提交分析（1条）

### 1. 主要更新类型
- **Bug修复 / 测试稳定性维护**：这是一条修复主分支上失败测试的维护型提交，涉及测试隔离性和两个具体测试用例的修复。

### 2. 关键变更点及与项目方向的关系
- **修复主分支上失败的测试**：说明项目 CI 在持续运行且维护者对测试健康度有要求，保持主干绿色是高效协作和可靠发布的前提。
- **FastH3 Trim Spark audio 测试修复**：从命名推测涉及 FastH3 相关模块中 Spark 音频数据裁剪（trim）逻辑的测试，指向项目在视频/音频多模态处理与 Spark 分布式后端集成方面的能力。
- **测试隔离性（test isolation）修复**：消除测试之间的状态依赖，使测试可以独立、可靠地运行，属于工程规范层面的改进。

### 3. 对项目的影响和潜在意义
- 直接提升了主分支测试通过率，避免因测试失败掩盖真实回归问题，增强 CI 可信度。
- 测试隔离改进有助于并行测试和加速 CI，降低后续大规模提交（如新模型、新后端支持）的集成成本。
- 对用户而言，主干稳定意味着基于 FastVideo 做视频生成推理或训练时，更少遇到"官方代码不可用"的问题。

### 4. 值得关注的技术点
- **Spark 音频后端测试**：提示 FastVideo 在数据加载/预处理层可能存在分布式（Spark）与音频流的组合处理路径，值得关注其数据管道设计是否支持大规模集群场景。
- **测试隔离实践**：通常涉及消除全局状态、固定随机种子、独立临时目录等手法，是大型 ML 工程走向成熟的标志。
- **协作模式**：提交带有多个 Co-authored 署名（包括自动化/辅助工具），反映项目可能在使用 AI 辅助开发流程进行维护。

### 5. 结合项目背景的影响评估
FastVideo 定位为高性能视频生成（扩散模型）训练与推理框架，提供文档、Cookbook 和快速上手指南，说明其重视易用性和生态建设。这类测试修复提交虽不直接带来新功能，但对一个以"Fast"为名、强调工程可靠性的框架至关重要：稳定的测试基线是后续持续交付新模型支持、推理优化和分布式训练特性的地基。它保障了开发者和用户对项目主线质量的信心，间接支撑项目向更广泛用户群扩展的目标。

## 详细提交记录

### [3658b12](https://github.com/hao-ai-lab/FastVideo/commit/3658b120da9f4ca75e1b0c798ccdaffa1c5d52b3)

- **作者**: lpc0220
- **时间**: 2026-10-18T23:07:59Z
- **提交信息**: [bugfix] Fix tests that fail on main: FastH3 Trim Spark audio, test isolation (#1957)

Co-authored-by: root <root@ptyche0124.ptyche.clusters.nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: root <root@ptyche0040.ptyche.clusters.nvidia.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34753
- **最后更新**: 2026-10-19T00:04:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
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


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13261
- **最后更新**: 2026-10-18T19:45:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37284
- **最后更新**: 2026-10-19T00:09:25Z

## 提交统计

- **昨日提交总数**: 48
- **提交者数量**: 23
- **主要提交者**: Akshat Anand, jacky.cheng, Linda

## AI分析总结

# SGLang 昨日提交分析（48 条记录）

## 1. 主要更新类型分布
- **性能优化（Perf）约 15 条**：占比最高，集中在统一内存（unified-memory）、扩散模型、AMD monokernels、投机解码等领域。
- **Bug 修复（Fix）约 16 条**：涉及 deepseek-v4.1、hicache、VLM、sgl-router、AMD 平台等。
- **重构（Refactor）约 5 条**：主要围绕 memory-pool / hicache / attention 元数据的职责分离。
- **功能新增（Feat）约 4 条**：unified-memory 的非对称 KV 行、muse spark runtime 等。
- **CI 约 4 条**：radix-cache KL 测试、AMD Mooncake 传输测试等。

## 2. 关键变更点与项目方向的关系
- **统一内存（unified-memory）成为核心主线**：支持非对称 KV 行、融合 draft 与滑窗/循环状态层、减少 SWA 释放开销、无主机同步地释放 SWA 段。这直接服务于 SGLang 的核心目标——低延迟 LLM 推理，通过更高效的显存/内存管理降低传输和分配成本。
- **DeepSeek-V4.1 专项优化**：多条提交围绕 PD 分离架构下的 SWA（滑动窗口注意力）有界重放、编码器元数据内存限定、prefill 分块尺寸修正，显示该项目正在积极支持新一代大模型架构。
- **投机解码（speculative decoding）持续打磨**：融合 draft 写窗口收集与 KV 翻译、FA4 verify 元数据捕获、移除冗余的 DP MLP 同步开关，体现对吞吐提升的持续追求。
- **多模态与扩散模型加速**：Qwen-Image、FLUX.3 的 GEMM/MLP/调制融合，以及 Kimi 图像缓存标识加固，扩展了项目对多模态推理的覆盖。

## 3. 对项目的影响与潜在意义
- unified-memory 系列重构+优化为后续异构内存架构（CPU/GPU 混合 KV 池）打下基础，hicache 从 buffer/pool info 构建主机池的重构进一步统一了内存池抽象，降低长期维护成本。
- PD 分离（prefill-decode disaggregation）的稳定性修复（如 decode 图复用、sgl-router 连接重发与熔断器开关）提升了生产级部署的可靠性。
- AMD/ROCm 生态投入显著（monokernels、Mooncake 版本升级、SLURM CI、diffusion 修复），强化跨硬件支持这一差异化竞争力。

## 4. 值得关注的技术点
- **无主机同步的 SWA 段释放**：避免同步阻塞，是推理热路径上的关键优化。
- **投机解码中 draft 写窗口与 KV 翻译的融合**：减少 kernel 启动次数与中间缓冲。
- **按 TP rank 独立键控 MLA Mamba 状态**（file 与 SeaweedFS 后端）：修复了多卡并行下缓存串扰的隐患。
- **sgl-router 参数重命名**（`--max-in-flight` → `--max-inflight-requests`）：属于破坏性 CLI 变更，升级时需注意。
- 出现多个 AI 协作署名（Claude、Devin AI），反映项目已将 AI 辅助开发纳入工作流。

## 5. 对项目发展的整体影响
结合 README 所述的"LLM 与多模态模型快速推理"目标，这批提交呈现出清晰的三条发展路径：**（一）以 unified-memory 为轴心的内存架构现代化**，为更大模型和更长上下文铺路；**（二）以 DeepSeek-V4.1、投机解码、PD 分离为代表的前沿推理技术落地**，保持性能领先地位；**（三）跨硬件（AMD/NVIDIA/Intel）与多模态（扩散模型、VLM）的横向扩展**，扩大适用生态。大量修复类提交也说明项目正从功能扩张期过渡到生产稳定性加固期，对企业和大规模部署用户是积极信号。总体上，这些变更使 SGLang 在推理性能、硬件覆盖面和部署可靠性三个维度上同步增强，巩固其作为高性能 LLM 服务引擎的定位。

## 详细提交记录

### [6708426](https://github.com/sgl-project/sglang/commit/67084267289333faf784e895a88cf39d559922bd)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-18T23:41:21Z
- **提交信息**: [Fix] spec: Remove `--speculative-skip-dp-mlp-sync` (#45043)

### [3f13f5d](https://github.com/sgl-project/sglang/commit/3f13f5d9660a4cd9ed1547c331397e92e4fcd439)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-18T22:54:20Z
- **提交信息**: [Fix] scheduler: Drop prefill embedding overrides in `prepare_for_decode` (#45041)

### [1461152](https://github.com/sgl-project/sglang/commit/1461152cb0857ea2d8d95d3e87c491e4438c54ab)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-18T22:43:08Z
- **提交信息**: [Fix] deepseek-v4.1: Leave room for encoder replay rows when sizing a prefill chunk (#45040)

### [fe89a7c](https://github.com/sgl-project/sglang/commit/fe89a7c8901216237e1acf67ec08e648ca41d16d)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-18T22:06:20Z
- **提交信息**: [Fix] deepseek-v4.1: Start the PD decode draft SWA window at the prefill draft valid-from (#45037)

### [da414ad](https://github.com/sgl-project/sglang/commit/da414adda71957676dcbb434a60326bd3a14600a)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-18T19:24:05Z
- **提交信息**: [Fix] engram: Clamp multimodal pad ids in host-built history rows (#45038)

### [0f4aedf](https://github.com/sgl-project/sglang/commit/0f4aedfecc3e1e420292541af4e9da8909b9b4f7)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-18T18:53:35Z
- **提交信息**: [Perf] deepseek-v4.1: Default decoder SWA bounded replay on for both PD roles on CUDA (#45035)

### [4ec19ca](https://github.com/sgl-project/sglang/commit/4ec19ca27f08f7ce44bbe1da70ce964731940eb2)

- **作者**: Ke Bao
- **时间**: 2026-10-18T15:21:16Z
- **提交信息**: [Refactor] memory-pool: Build KV host pools from buffer info (#40917)

### [bb1d4cd](https://github.com/sgl-project/sglang/commit/bb1d4cddd953597b4e27a8489367ddcbb99e3762)

- **作者**: Ke Bao
- **时间**: 2026-10-18T15:02:46Z
- **提交信息**: [Refactor] hicache: Route Mamba host transfers from pool info (#44968)

### [d4e3c16](https://github.com/sgl-project/sglang/commit/d4e3c163c95afe5f549116c9c73a6f0e6a4830a7)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-18T14:23:34Z
- **提交信息**: [CI] radix-cache: Register the Inkling cache linker KL test to extra-b (#45004)

### [e9b22a0](https://github.com/sgl-project/sglang/commit/e9b22a0818292eedc0630b2b72cdfcb4ae81bf85)

- **作者**: Kevin Mi
- **时间**: 2026-10-18T14:04:57Z
- **提交信息**: [Perf] [AMD] monokernels: Let a plugin skip per-step attention metadata (#44601)

Co-authored-by: Kevin Mi <kevin.mi@radixark.ai>
Co-authored-by: kkHuang-amd <43161300+kkHuang-amd@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [57db508](https://github.com/sgl-project/sglang/commit/57db5089c207ae4ce189cc092a89a2027c8aea29)

- **作者**: Cheng Wan
- **时间**: 2026-10-18T12:42:16Z
- **提交信息**: [Perf] attention: Capture translated FA4 verify metadata for DSPARK (#44973)

### [2e9b2ca](https://github.com/sgl-project/sglang/commit/2e9b2cacda6af490fc26eb918b7bc236fbc59fc3)

- **作者**: Cheng Wan
- **时间**: 2026-10-18T12:41:34Z
- **提交信息**: [Perf] speculative: Fuse draft write-window gathering and KV translation (#44972)

### [2a83471](https://github.com/sgl-project/sglang/commit/2a8347167623aa21ddab89f1b9844c6e3df26040)

- **作者**: Cheng Wan
- **时间**: 2026-10-18T12:40:57Z
- **提交信息**: [Perf] mamba: Fuse strided state updates and replay index translation (#44971)

### [d318a54](https://github.com/sgl-project/sglang/commit/d318a546daaa6435a9b20128a7d91adb0dea87cb)

- **作者**: Cheng Wan
- **时间**: 2026-10-18T12:40:25Z
- **提交信息**: [Perf] unified-memory: Reduce allocation and SWA retirement overhead (#44970)

### [a5b2114](https://github.com/sgl-project/sglang/commit/a5b21145e15cb4a0cb14a82c3bc3737cb41f9905)

- **作者**: Cheng Wan
- **时间**: 2026-10-18T12:39:44Z
- **提交信息**: [Refactor] attention: Separate decode metadata from pool ownership (#44969)

### [3edb156](https://github.com/sgl-project/sglang/commit/3edb156decff8c2d1a4b5ddb9317260c3cebf0b6)

- **作者**: caihuali95
- **时间**: 2026-10-18T12:39:09Z
- **提交信息**: [Feat] unified-memory: Fuse drafts with sliding-window and recurrent-state layers (#43326)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [19cb24f](https://github.com/sgl-project/sglang/commit/19cb24f1e1c39edbdba7de4d46719150e6e55dec)

- **作者**: caihuali95
- **时间**: 2026-10-18T12:37:50Z
- **提交信息**: [Feat] unified-memory: Support asymmetric KV rows (#43325)

### [1d17066](https://github.com/sgl-project/sglang/commit/1d17066bad10281af50852d554444dd828c349bc)

- **作者**: caihuali95
- **时间**: 2026-10-18T12:37:24Z
- **提交信息**: [Perf] gdn: Select FlashInfer prefill for page-major pools (#43171)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>

### [ba50ea3](https://github.com/sgl-project/sglang/commit/ba50ea3d77eb1762b41e00185a2cb127f88d7cc2)

- **作者**: caihuali95
- **时间**: 2026-10-18T12:36:56Z
- **提交信息**: [Perf] unified-memory: Free SWA segments without a host sync (#43170)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>

### [47eeddc](https://github.com/sgl-project/sglang/commit/47eeddcd180e2b5228ea35dae7a0ff327c5d07ab)

- **作者**: caihuali95
- **时间**: 2026-10-18T12:36:02Z
- **提交信息**: [Fix] swa: Retain a whole window behind insertion pages (#43168)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>

### [fe1851c](https://github.com/sgl-project/sglang/commit/fe1851c3c257ad000f793f3b7afc0c0ccff382e1)

- **作者**: lixiufei-leo
- **时间**: 2026-10-18T12:35:50Z
- **提交信息**: [Fix] sgl-router: Receive kv-indexer-bridge event batches outside tokio's coop budget (#44305)

Co-authored-by: Xiufei Li <294029388+lixiufei-leo@users.noreply.github.com>

### [e17fed6](https://github.com/sgl-project/sglang/commit/e17fed6ea7adf1f93e4fcfab4d66022854f94f4c)

- **作者**: WenhaoZhang
- **时间**: 2026-10-18T12:33:31Z
- **提交信息**: [Perf] diffusion: fused gate/up + SwiGLU MLP on comfy_kitchen INT8 for Qwen-Image 2.1 (#44196)

### [680a2ff](https://github.com/sgl-project/sglang/commit/680a2ff27e09f08b9e48a84ff15cd91403aa3274)

- **作者**: Linda
- **时间**: 2026-10-18T12:32:19Z
- **提交信息**: [Perf] [NVIDIA] diffusion/FLUX.3: Run dynamic LoRA through PrimsTS GEMMs (#44761)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [1fd46dd](https://github.com/sgl-project/sglang/commit/1fd46ddd5688a678eaec7cca5d45761d1938a5ff)

- **作者**: WenhaoZhang
- **时间**: 2026-10-18T12:31:36Z
- **提交信息**: [Perf] diffusion: fused indexed modulation for FP32 AdaLN tables (#44180)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [8dee3f6](https://github.com/sgl-project/sglang/commit/8dee3f6bdb29846ac2d5d1f2f5e8365c38cf938f)

- **作者**: Shuwen Wang
- **时间**: 2026-10-18T11:26:40Z
- **提交信息**: [Fix] [H200] ci: Split GLM-5.3-Flash serving recipes into separate tests (#44892)

### [f8e3270](https://github.com/sgl-project/sglang/commit/f8e32706fc2fcd564d49e344a7f1ea2493a47102)

- **作者**: Shuwen Wang
- **时间**: 2026-10-18T11:26:22Z
- **提交信息**: [CI] radix-cache: Re-enable Inkling unified cache linker KL test (#44938)

### [a3abea3](https://github.com/sgl-project/sglang/commit/a3abea35609eeeff7e165486dd614963af211161)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-18T10:23:18Z
- **提交信息**: [Fix] sgl-router: Resend on a closed pooled connection; add --disable-circuit-breaker (#44075)

### [3b932cd](https://github.com/sgl-project/sglang/commit/3b932cde262945fb489e187f658fde7bbecd31a2)

- **作者**: Mick
- **时间**: 2026-10-18T09:39:37Z
- **提交信息**: [Fix] VLM: harden Kimi image cache identity across preprocessing and radix hashing (#43043)

Co-authored-by: Rahul Chalamala <22563365+rchalamala@users.noreply.github.com>
Co-authored-by: Devin AI <158243242+devin-ai-integration[bot]@users.noreply.github.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [5a930cf](https://github.com/sgl-project/sglang/commit/5a930cfd88b78c89ffb6dd7292cd4098c36d8e5e)

- **作者**: Akshat Anand
- **时间**: 2026-10-18T09:31:33Z
- **提交信息**: [Fix] glm4v: Clamp request video budgets to the deployment limit (#43871)

Co-authored-by: cipheraxat <cipheraxat@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6c3db0f](https://github.com/sgl-project/sglang/commit/6c3db0f5208ac18291ecae42698e4ee5dd712442)

- **作者**: Ilia Yastrebov
- **时间**: 2026-10-18T08:59:18Z
- **提交信息**: [Perf] NIXL: prepared dlists for hybrid-model state transfer (#44740)

Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [80fef63](https://github.com/sgl-project/sglang/commit/80fef637865ff8d84dce10b6c3362d69bd117e3a)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-18T08:47:56Z
- **提交信息**: [Fix] Inkling: frame constrained output in native message tokens (#44716)

### [889658a](https://github.com/sgl-project/sglang/commit/889658a5be0331a23794eb43ab7fa6421029d651)

- **作者**: Huang Long
- **时间**: 2026-10-18T08:16:46Z
- **提交信息**: [Fix] disaggregation: Reuse startup decode graphs across PD role switches (#43760)

### [d33dd05](https://github.com/sgl-project/sglang/commit/d33dd0566a1a8b77bdad83b64cbc45510307052b)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-18T08:00:24Z
- **提交信息**: [Feat] srt: Add muse spark runtime, multimodal support and tests (3/5) (#44666)

Co-authored-by: 1am9trash <1am9trash@gmail.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>
Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Ethan Che <eche@meta.com>
Co-authored-by: HAI <hixiao@gmail.com>
Co-authored-by: Jiajun Li <guapisolo@gmail.com>
Co-authored-by: Jiajun Li <jiajun.li@radixark.ai>
Co-authored-by: Jimmy Shiu <jimmysh341@gmail.com>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>
Co-authored-by: Liangsheng Yin <lsyincs@gmail.com>
Co-authored-by: Wookje Han <52435620+wookjeHan@users.noreply.github.com>
Co-authored-by: Wookje Han <wookjeh@nvl72d079-T17.cm.cluster>
Co-authored-by: Wookje Han <wookjeh@nvl72d094-T17.cm.cluster>
Co-authored-by: Wookje Han <wookjeh@nvl72d157-T16.cm.cluster>
Co-authored-by: Wookje Han <wookjeh@nvl72d170-T04.cm.cluster>
Co-authored-by: Wookje Han <wookjeh@nvl72d214-T17.cm.cluster>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Yuhao Yang <yhyang201@users.noreply.github.com>
Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>
Co-authored-by: ethche <ethche@gmail.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>
Co-authored-by: jianan-gu <jianan.gu@intel.com>

### [80914b7](https://github.com/sgl-project/sglang/commit/80914b7c9bb412720c0896862aede98faf5bc264)

- **作者**: Shangming Cai
- **时间**: 2026-10-18T07:33:58Z
- **提交信息**: [Refactor] sgl-router: Rename --max-in-flight to --max-inflight-requests (#44950)

### [3a6e1fc](https://github.com/sgl-project/sglang/commit/3a6e1fcf77588293e1bbb4347d94dab3ff122192)

- **作者**: Yuwei An
- **时间**: 2026-10-18T07:33:35Z
- **提交信息**: [Perf] DSv4.1: Bound encoder BCG metadata memory (#44963)

### [de61ab5](https://github.com/sgl-project/sglang/commit/de61ab53d47f406aadcd8771bf829bd66d2d1c84)

- **作者**: Richard Wang
- **时间**: 2026-10-18T07:31:10Z
- **提交信息**: [Perf] diffusion: Defer full GC collections while importing the runtime (#44606)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [f1cf2e1](https://github.com/sgl-project/sglang/commit/f1cf2e1005c9cb9fc33f3574c0d081a3001374ef)

- **作者**: Zhaoyi Li
- **时间**: 2026-10-18T07:29:22Z
- **提交信息**: [Fix] [AMD] mori: Look up elided DSA state entries by the paired dst index (#44412)

### [396e97e](https://github.com/sgl-project/sglang/commit/396e97e5dd0766cfb6a593cb71c6c0860838dbf4)

- **作者**: Zhaoyi Li
- **时间**: 2026-10-18T07:28:34Z
- **提交信息**: [CI] [AMD] ci/slurm: Add a Mooncake KV-transfer test to the MI355X disaggregation nightly (#44409)

### [8a4239f](https://github.com/sgl-project/sglang/commit/8a4239fbdcd7dedb5a4cf96ba17a0cec558bae2b)

- **作者**: Zhaoyi Li
- **时间**: 2026-10-18T07:22:55Z
- **提交信息**: [Fix] [AMD] mooncake: Bump Mooncake to v0.3.14-rc1 for cross-node KV transfer (#44404)

### [ba3fc94](https://github.com/sgl-project/sglang/commit/ba3fc9441dd1721b4fbf6ec6930e362fbdf61721)

- **作者**: Shuwen Wang
- **时间**: 2026-10-18T07:16:31Z
- **提交信息**: [Fix] mamba: Release consumed lazy Mamba prefix locks before donation retry (#43559)

### [f96a732](https://github.com/sgl-project/sglang/commit/f96a7326e601f0a7f57aacab15f366cddf537c78)

- **作者**: jacky.cheng
- **时间**: 2026-10-18T07:13:25Z
- **提交信息**: [Fix] [AMD] diffusion: Prevent ComponentResidencyError after compile warmup (#43952)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [a11fa06](https://github.com/sgl-project/sglang/commit/a11fa06be78dd3d033020f0f97f8f2be7befba53)

- **作者**: Shuwen Wang
- **时间**: 2026-10-18T07:10:50Z
- **提交信息**: [Fix] hicache: Key MLA Mamba state per TP rank in the file backend (#41907)

### [ffc4573](https://github.com/sgl-project/sglang/commit/ffc4573c981b35a45b89084c8dbea7d5ef393750)

- **作者**: Shuwen Wang
- **时间**: 2026-10-18T07:09:58Z
- **提交信息**: [Fix] hicache: Key MLA Mamba state per TP rank in the SeaweedFS backend (#43816)

### [e6c2cd4](https://github.com/sgl-project/sglang/commit/e6c2cd47a93e5bdb7aabe0c21c6799208afccd4a)

- **作者**: Shuwen Wang
- **时间**: 2026-10-18T07:09:26Z
- **提交信息**: [Fix] hicache: Keep unified memory off the direct page_first_direct copies (#43333)

### [df966f2](https://github.com/sgl-project/sglang/commit/df966f234504523ab3ff4bd88521c99796405bc6)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-18T07:07:55Z
- **提交信息**: [Feat] deepseek-v4.1: Run encoder SWA bounded replay on PD prefill workers (#44952)

### [520df8a](https://github.com/sgl-project/sglang/commit/520df8a4917fd1c4828ac988b12144c38a35c2a0)

- **作者**: Ziang Li
- **时间**: 2026-10-18T07:04:10Z
- **提交信息**: [Perf] weight-sync: Allocate packed receive buffers from metadata (#39264)

### [00f6cdc](https://github.com/sgl-project/sglang/commit/00f6cdcd1b6fdd215c623a7f6e167ee197d2b138)

- **作者**: Michael
- **时间**: 2026-10-18T07:01:40Z
- **提交信息**: [Fix] [AMD] kda: Reject match_cutedsl_decode on ROCm and skip its parity tests (#44089)

### [3626978](https://github.com/sgl-project/sglang/commit/3626978a13694eb4c6e3a6080e4f1c4d3e5f4d52)

- **作者**: Michael
- **时间**: 2026-10-18T07:01:11Z
- **提交信息**: [Fix] [AMD] kda: Match the fused verify Q/K norm to its reference kernel (#43991)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1291
- **最后更新**: 2026-10-16T11:34:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 94076
- **最后更新**: 2026-10-19T00:08:02Z

## 提交统计

- **昨日提交总数**: 18
- **提交者数量**: 14
- **主要提交者**: Harry Huang, trienebutdiene, aoshen02

## AI分析总结

# vLLM 昨日提交分析（18个提交）

## 1. 主要更新类型
- **Bug修复为主**：约8个提交为各类Bug修复，涉及MoE、ROCm、投机解码、结构化输出、前端、视频处理、构建系统等
- **文档更新**：3个提交，集中在RL（强化学习训练）和API接口文档
- **性能优化**：ROCm/AMD GPU上的MoE推理优化
- **构建/CI**：4个提交，涉及Docker镜像、发布构建、CI超时配置
- **代码清理**：Qwen模型实现的重构清理

## 2. 关键变更点与项目方向的关系

**MoE与分布式推理强化**：修复DeepEP高吞吐缓冲区在DBO流上的生命周期问题，ROCm上将未融合的共享专家与AITER MegaMoE重叠执行。这直接服务于vLLM"快速、低成本LLM服务"的核心目标——MoE模型（如DeepSeek、Qwen系列）是当前主流大模型架构，其推理效率至关重要。

**跨平台与硬件适配**：B300/GB300（SM103）的DeepEP构建支持、GDN MTP解码在SM80-90上的CUDA兼容性修复、ROCm的inductor批量不变性兼容性检查。体现项目持续扩展NVIDIA新一代GPU和AMD硬件生态。

**结构化输出正确性**：Rust前端gRPC结构化输出改用xgrammar；投机解码下结构化输出的语法掩码改为由GPU logit数量驱动。这两项解决了高级特性组合场景下的正确性问题。

**RL训练生态建设**：新增MoE路由重放（R3）中routed experts返回的文档、无vLLM的训练器权重传输HTTP协议文档。表明vLLM正深化作为RL训练推理后端的角色。

## 3. 对项目的影响
- 修复了一批影响生产稳定性的边界问题（WebM视频帧数、beam search的EOS停止、CrossEncoder的chat模板）
- 通过AI辅助开发（多个提交出现Claude、Codex、vllm-agent作为共同作者）加速了修复速度，值得注意这一开发模式的普及
- 文档完善降低了RL训练集成和API使用的门槛

## 4. 值得关注的技术点
- **AI协同开发常态化**：18个提交中超过10个有AI模型作为Co-authored-by，显示vLLM社区已深度采用AI辅助编码流程
- **投机解码×结构化输出**：语法掩码从CPU/GPU不一致的路径改为GPU logit计数驱动，这类交叉特性的正确性修复往往影响面广
- **Rust前端成熟化**：gRPC接口采用xgrammar后端，说明Rust推理前端正在生产化
- **Qwen3.8-Flash-Next等新模型**的HC/PLE实现清理，为支持最前沿模型做代码卫生准备

## 5. 对项目发展的影响
结合README定位（"Easy, fast, and cheap LLM serving for everyone"），这些提交从三个维度支撑项目发展：**可靠性**（大量Bug修复确保用户可信赖）、**硬件广度**（NVIDIA新卡+AMD+构建兼容性）、**生态广度**（RL训练协议文档化、多模态修复）。项目在保持核心推理性能优化的同时，正向"一站式LLM服务+训练基础设施"的方向拓展，且AI辅助开发流程可能进一步提升其迭代速度——这对需要快速跟进模型生态的推理框架而言是重要竞争优势。

## 详细提交记录

### [36e0ae2](https://github.com/vllm-project/vllm/commit/36e0ae2df2882de8027bb484da9179c10646ccee)

- **作者**: Anirudh Ravichandran
- **时间**: 2026-10-18T22:47:48Z
- **提交信息**: [Bugfix][MoE] Keep DeepEP high-throughput buffers alive across DBO streams (#60735)

Signed-off-by: Anirudh Ravichandran <ani@primeintellect.ai>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [e0adacc](https://github.com/vllm-project/vllm/commit/e0adacc9a67a5f2b2d8ba508f7f522bc1ff83c6d)

- **作者**: Alec
- **时间**: 2026-10-18T20:29:43Z
- **提交信息**: [Bugfix][Rust Frontend] Use xgrammar for gRPC structured outputs (#61892)

Signed-off-by: Alec Flowers <aflowers@nvidia.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [82a24bb](https://github.com/vllm-project/vllm/commit/82a24bb82dd9344cce7a43195bb51a2390adf00a)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-18T18:45:08Z
- **提交信息**: [Bugfix][ROCm] Only set inductor batch_invariant when torch has it (#62274)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6540d5c](https://github.com/vllm-project/vllm/commit/6540d5c8f8c73bb2dd6194e56ed002fc32a31837)

- **作者**: Lucas Wilkinson
- **时间**: 2026-10-18T18:29:21Z
- **提交信息**: [Bugfix][Spec Decode][Structured Output] Drive grammar masks from GPU logit counts (#52477)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ff01a6b](https://github.com/vllm-project/vllm/commit/ff01a6b14f329ccd4162fce309913542e2abcd5b)

- **作者**: alp
- **时间**: 2026-10-18T16:49:42Z
- **提交信息**: [Bugfix][Frontend] Stop beam search on generation config EOS tokens (#62072)

Signed-off-by: mottopanikeiku <176798723+mottopanikeiku@users.noreply.github.com>
Co-authored-by: mottopanikeiku <176798723+mottopanikeiku@users.noreply.github.com>

### [fe8f214](https://github.com/vllm-project/vllm/commit/fe8f2140eeb6103e2ac01fbe2ce40dcc9dba19de)

- **作者**: aoshen02
- **时间**: 2026-10-18T15:26:36Z
- **提交信息**: [Doc] Document /inference/v1/generate request/response fields and DP rank header (#62305)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e80b6c6](https://github.com/vllm-project/vllm/commit/e80b6c642f21fd5b24439825592f5b9ced36add8)

- **作者**: Taoyu Zhu
- **时间**: 2026-10-18T14:39:38Z
- **提交信息**: [ROCm][DSv4] Overlap the unfused shared expert with AITER MegaMoE (#61819)

Signed-off-by: Taoyu Zhu <zhutaoyu97@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [371745e](https://github.com/vllm-project/vllm/commit/371745ebd6c12f314402c6c319de2e7ef82c2981)

- **作者**: aoshen02
- **时间**: 2026-10-18T13:11:45Z
- **提交信息**: [Doc][RL] Document routed experts return for MoE routing replay (R3) (#62302)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [072c088](https://github.com/vllm-project/vllm/commit/072c0886d53d933a7e1d3da7e8a3a91670cf181d)

- **作者**: André Lustosa
- **时间**: 2026-10-18T12:13:17Z
- **提交信息**: [Build] Keep plain CUDA arch when its suffixed variant is also requested (#56549)

Signed-off-by: Andre Lustosa <alustosa@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [6b24947](https://github.com/vllm-project/vllm/commit/6b24947628b6e0f3363540f3fbdc5c14f7d99b94)

- **作者**: Muhammad Ibrahim
- **时间**: 2026-10-18T12:12:34Z
- **提交信息**: [CI/Build] Build DeepEP for SM103 (B300/GB300) in the Docker image (#61829)

Signed-off-by: Muhammad Ibrahim <muhammad.ibrahim@multiversecomputing.com>
Co-authored-by: Muhammad Ibrahim <muhammad.ibrahim@multiversecomputing.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [4946639](https://github.com/vllm-project/vllm/commit/494663940b9b44f667c4f61c8c2407ba8e725ceb)

- **作者**: Harry Huang
- **时间**: 2026-10-18T11:38:21Z
- **提交信息**: [Qwen4Exp] Clean up HC and PLE implementations for Qwen3.8-Flash-Next (#61454)

Signed-off-by: huanghaoyan.hhy <huanghaoyan.hhy@alibaba-inc.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [3c13653](https://github.com/vllm-project/vllm/commit/3c13653738dad0acd877c23373816fefffbdd373)

- **作者**: Rémi Delhaye
- **时间**: 2026-10-18T11:30:12Z
- **提交信息**: [Frontend] Score with the chat template declared by Sentence Transformers CrossEncoders (#60877)

Signed-off-by: rdlhio <contact@rdlh.io>

### [953fa44](https://github.com/vllm-project/vllm/commit/953fa442fafedbf51c3310d577474f80e457964a)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-18T11:00:16Z
- **提交信息**: [CI] Per-test timeout for Language Models (Extended Pooling) (#62279)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3f1b04e](https://github.com/vllm-project/vllm/commit/3f1b04e045beb841329519bacafa9b2ded86a762)

- **作者**: Isotr0py
- **时间**: 2026-10-18T10:37:39Z
- **提交信息**: [Bugfix] Fix Opencv video backend frames count missing for WebM video inputs (#61759)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [2365177](https://github.com/vllm-project/vllm/commit/2365177ddda7714502e4df7a1669cc79c0a4dfd0)

- **作者**: aoshen02
- **时间**: 2026-10-18T09:26:56Z
- **提交信息**: [Doc][RL] Document the weight-transfer HTTP protocol for trainers without vLLM (#62267)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1b2a666](https://github.com/vllm-project/vllm/commit/1b2a666391f2a24228a1436b64d547c34cc6b6ce)

- **作者**: Louie Tsai
- **时间**: 2026-10-18T08:46:56Z
- **提交信息**: [Doc][Recipe] Fix for redhat fp8 xeon support issue (#62245)

### [83c9a54](https://github.com/vllm-project/vllm/commit/83c9a547bf9a3b4f2653fb5766886bdc5dba35be)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-18T07:48:00Z
- **提交信息**: [CI][Release] Fix release wheel builds: stop excluding tracked recipes/ from Docker context (#62221)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b510857](https://github.com/vllm-project/vllm/commit/b510857d37640209a4a3e01a13260ac26f2a93f3)

- **作者**: trienebutdiene
- **时间**: 2026-10-18T07:14:06Z
- **提交信息**: [Bugfix][Build] Build fused GDN MTP decode for SM80-SM90 with CUDA < 13 (#60896)

Signed-off-by: kimseunghyun <incongnito12@gmail.com>
Signed-off-by: kimseunghyun <hellonypcteam@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>
Co-authored-by: kimseunghyun <hellonypcteam@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-19
**监控日期**: 2026-10-18
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7237
- **最后更新**: 2026-10-19T00:05:33Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 11
- **主要提交者**: Yueqian Lin, Wenbo Ji　嵇文博, andyluo7

## AI分析总结

## vllm-omni 昨日提交分析

### 1. 主要更新类型

| 类型 | 数量 | 说明 |
|------|------|------|
| **Bug修复** | 4 | 覆盖采样逻辑、超时处理、Diffusion CFG、Cosmos3清理 |
| **性能优化** | 2 | SDPA路径优化、去冗余同步 |
| **功能新增** | 3 | RL权重迁移、CUDA FA3 FP8内核、ComfyUI工作流 |
| **基础设施/CI** | 1 | CPU/设备测试路由优化 |
| **重构清理** | 1 | Cosmos3模型准备清理 |

---

### 2. 关键变更点及与项目方向的关系

项目目标是为**全模态（omni-modality）模型**提供"简单、快速、廉价"的推理服务。昨日提交恰好围绕这一核心展开：

- **性能与加速方向**：CUDA FA3 FP8 扩散注意力内核（`[Kernel]`）和 SDPA 执行路径报告（`[Core]`）直接服务于降低推理成本与提升速度。TeaCache CFG 分支分离则是扩散模型缓存机制的正确性修复，保障加速不以牺牲质量为代价。

- **多模态能力扩展**：YuE2 音乐生成与翻唱工作流集成到 ComfyUI（`[Frontend]`）体现了对音频/音乐模态的覆盖。Cosmos3 清理（`[Bugfix]`）为新模型接入做准备，说明模型生态在持续扩展。

- **训练与RL支持**：RL训练的权重迁移支持（`[RL]`）将vllm-omni从纯推理服务扩展到强化学习训练场景，是重要的能力边界拓展。

- **全双工/语音交互核心**：全双工工具结果的超时与取消恢复（`[Core]`）直接支撑语音/音频交互的实时性需求，是omni-modality中关键的全双工能力加固。

- **工程质量**：CPU/设备测试路由到匹配硬件车道，提升CI效率和可靠性。

---

### 3. 对项目的影响和潜在意义

- **短期影响**：多个bug修复（语义码0采样、超时初始化）提升了系统的稳定性和正确性，尤其语义码采样bug可能直接影响音频/语言生成质量。
- **中期影响**：FA3 FP8内核和SDPA优化带来推理吞吐与成本优势，契合项目"cheap and fast"的定位。
- **长期影响**：RL权重迁移支持为项目打开了训练侧的大门，ComfyUI工作流降低了用户接入门槛，Cosmos3清理预示更多omni模型即将支持。

---

### 4. 值得关注的技术点

- **CUDA FA3 FP8 扩散注意力**：结合Flash Attention 3与FP8量化用于扩散模型，这是当前扩散推理优化的前沿方向。
- **TeaCache CFG分支分离**：在共享CFG辅助函数中保持TeaCache分支独立，涉及缓存策略与classifier-free guidance的交互，是扩散模型加速中的微妙正确性问题。
- **全双工超时与取消恢复**：全双工模式下工具调用的异步超时与恢复机制设计复杂，对实时语音交互系统至关重要。
- **SDPA fullgraph推理支持**：通过报告CUDA SDPA执行路径并支持fullgraph推理，利用PyTorch编译提升性能。

---

### 5. 对项目发展的整体影响

基于README中"Easy, fast, and cheap omni-modality model serving"的定位，这批提交从四个维度推动了项目：**速度**（内核优化、SDPA fullgraph）、**广度**（音乐生成、新模型准备）、**深度**（RL训练支持、全双工核心能力）、**工程质量**（CI路由、多处bug修复）。整体来看，项目正在从纯推理服务向覆盖多模态生成、训练支持和易用工具链的全栈omni平台演进，社区贡献者活跃（多个Co-authored-by标记），生态建设态势良好。

## 详细提交记录

### [15470d2](https://github.com/vllm-project/vllm-omni/commit/15470d2c77221491cd525eac8e4293550b5211e8)

- **作者**: andyluo7
- **时间**: 2026-10-18T22:59:44Z
- **提交信息**: [CI/Build] Route CPU and device tests to matching hardware lanes (#8381)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [a965251](https://github.com/vllm-project/vllm-omni/commit/a965251bf1a3db3ab6871307ec39c938c0634479)

- **作者**: Yueqian Lin
- **时间**: 2026-10-18T18:07:55Z
- **提交信息**: [Bugfix] Drama 3: never sample semantic code 0 as the main token (#9044)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [1c0bde5](https://github.com/vllm-project/vllm-omni/commit/1c0bde507dfbffd25b32f6092dbe4526c945b7dd)

- **作者**: bcsdhjew
- **时间**: 2026-10-18T14:54:52Z
- **提交信息**: [Core] Add duplex tool result timeout and cancellation recovery (#8758)

Signed-off-by: NolenLiang <nliang@nvidia.com>
Signed-off-by: bcsdhjew <fangl001@zuaa.zju.edu.cn>
Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: NATURE <wzliu@connect.hku.hk>

### [172e565](https://github.com/vllm-project/vllm-omni/commit/172e56570eeeaa8f93b0c9d1359467b707d070e6)

- **作者**: Kuatova Kamila
- **时间**: 2026-10-18T13:46:06Z
- **提交信息**: [Bugfix] Enforce stage_init_timeout on stage readiness and stop launching after shutdown (#8606)

Signed-off-by: Kamila Kuatova <kuatova_kamila@list.ru>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5c79c4f](https://github.com/vllm-project/vllm-omni/commit/5c79c4f4dd4be35c3620a97514a46bd853979a2a)

- **作者**: Weiming Liao
- **时间**: 2026-10-18T13:08:05Z
- **提交信息**: [Frontend] Add YuE2 music generation and cover workflows to ComfyUI (#8881)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

### [e9a9ba8](https://github.com/vllm-project/vllm-omni/commit/e9a9ba825535738ec51f2b4f3b91d5b9171c5c6e)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-18T12:25:38Z
- **提交信息**: [Bugfix][Diffusion] Keep TeaCache CFG branches separate in the shared CFG helper (#8475)

Signed-off-by: Wenbo Ji <36562829+fusheng-ji@users.noreply.github.com>

### [2cefedd](https://github.com/vllm-project/vllm-omni/commit/2cefeddc8f54ec19a1a46668583b20c2139c2c62)

- **作者**: Sun
- **时间**: 2026-10-18T11:23:25Z
- **提交信息**: [Core] Report CUDA SDPA execution paths and support inference fullgraph (#7895)

Signed-off-by: levius <2114377220@qq.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e529e58](https://github.com/vllm-project/vllm-omni/commit/e529e586fb990047df50924b0d7d6518af00dfaf)

- **作者**: MaciejBalaNV
- **时间**: 2026-10-18T11:14:26Z
- **提交信息**: [bugfix] Cosmos3 cleanup for preparation of new models (#8898)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [a464081](https://github.com/vllm-project/vllm-omni/commit/a464081e1ba12dfe63e0406866d296acd2d46ba8)

- **作者**: Linze Shi
- **时间**: 2026-10-18T10:53:21Z
- **提交信息**: [Model] Avoid redundant SenseNova-U1 denoising synchronizations (#8254)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [d790c53](https://github.com/vllm-project/vllm-omni/commit/d790c53eeb9d35875054f1adf0d96ab0979d2403)

- **作者**: Yukim1
- **时间**: 2026-10-18T10:46:20Z
- **提交信息**: [Kernel] Add CUDA FA3 FP8 diffusion attention (#8965)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [72a665b](https://github.com/vllm-project/vllm-omni/commit/72a665bbe8b4fb035baf56516d643b7fd1f6b039)

- **作者**: dengyunyang
- **时间**: 2026-10-18T08:17:37Z
- **提交信息**: [RL] Add Weight Transfer Support for RL Training (#7686)

Signed-off-by: dengyunyang <584797741@qq.com>
Signed-off-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>
Co-authored-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

---
