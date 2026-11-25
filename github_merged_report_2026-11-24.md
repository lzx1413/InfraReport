# GitHub Stars 合并报告 - 2026-11-24

**合并日期**: 2026-11-25
**监控日期**: 2026-11-24
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


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2304
- **最后更新**: 2026-11-25T04:14:35Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Cui-yshoho, Jiaqi Wang, Coach257

## AI分析总结

# VeOmni 仓库近期提交分析

## 1. 主要更新类型

本次提交以**功能新增**为主，辅以**性能优化**，集中体现了项目在多模态大模型训练能力上的持续扩展。具体包括：

- **功能新增**：新增 HyperParallel Ascend 分布式后端；新增 kimi_k3 多模态 MoE 模型训练支持（含 Ascend NPU 内核与 GPU 对齐能力）
- **性能优化**：移除异步卸载中的 host 同步开销，优化 Muon 3D 专家工作区的内存管理
- **代码重构**：涉及模型、算子、配置、数据、训练器和文档等多模块的协调调整

## 2. 关键变更点及其与项目方向的关系

VeOmni 的核心定位是"Model-Centric Distributed Recipe Zoo"，即以模型为中心的分布式训练配方库，目标是支持**任意模态**的高效训练。本次提交紧密围绕这一方向：

- **Ascend 后端支持（#1466、#1291）**：新增 HyperParallel Ascend 后端和 Ascend NPU 内核，标志着 VeOmni 对国产 AI 芯片生态的深度适配。这是对项目"多模态模型训练"目标的重要补充，使训练硬件覆盖面从 GPU 扩展到 NPU 平台。
- **kimi_k3 多模态 MoE 训练（#1291）**：该提交横跨 model、ops、config、data、trainer、docs 六大模块，说明项目在"配方库"架构上新增了一个完整的多模态 MoE 训练配方，进一步丰富了 Recipe Zoo 的内容。
- **性能与内存优化（#1452）**：移除异步卸载的 host 同步和约束 Muon 3D 专家工作区，直接提升了大规模 MoE 训练的效率和稳定性。

## 3. 对项目的影响和潜在意义

- **硬件生态扩展**：Ascend 后端的引入降低了用户在国产硬件上的使用门槛，有助于 VeOmni 在更广泛的部署环境中被采用。
- **训练配方丰富化**：kimi_k3 作为新的多模态 MoE 配方，为用户提供了可参考的完整训练范例，增强了项目的实用性和可复用性。
- **训练效率提升**：移除冗余的 host 同步和优化专家工作区管理，对大规模 MoE 训练场景（专家数量多、激活参数大）尤为重要，能有效减少通信等待和内存碎片。
- **GPU/NPU 对齐**：同一模型在 NPU 和 GPU 上保持训练行为一致（GPU parity），降低了跨平台迁移和对比实验的复杂度。

## 4. 值得关注的技术点

- **HyperParallel 架构**：作为新的分布式后端，其并行策略值得关注，可能涉及数据并行与模型并行的更高效组合。
- **Muon 3D 专家工作区管理**：Muon 优化器在 MoE 训练中的 3D 工作区约束是较为前沿的技术点，涉及专家并行（Expert Parallel）场景下的内存优化。
- **异步卸载（Async Offload）的同步开销消除**：在分布式训练中移除 host-device 同步是一个精细的性能调优手段，体现了项目对底层训练性能的深度优化。
- **多模态 MoE 的端到端配置链路**：从 config 到 data 到 trainer 的全链路变更，展示了 VeOmni 以配方为中心的模块化设计。

## 5. 对项目发展的整体影响

结合 README 中"Scaling Any Modality Model Training"的愿景，本次提交从三个维度推进了项目发展：**硬件广度**（Ascend NPU 支持）、**模型深度**（kimi_k3 多模态 MoE 配方）和**训练效率**（异步卸载优化与内存约束）。这些变更使 VeOmni 从一个以 GPU 为中心的多模态训练框架，逐步演进为**跨硬件平台、多模型架构、高效分布式训练**的综合性训练配方库，进一步巩固了其作为模型中心化分布式训练方案的定位，也为社区贡献者和用户提供了更完整、更实用的多模态 MoE 训练参考实现。

## 详细提交记录

### [cc1681b](https://github.com/ByteDance-Seed/VeOmni/commit/cc1681bfe9ac3097da1240f089520dab6209ccd8)

- **作者**: Cui-yshoho
- **时间**: 2026-11-24T13:11:09Z
- **提交信息**: [dist] feat: add optional HyperParallel Ascend backend (#1466)

### [7aae5e5](https://github.com/ByteDance-Seed/VeOmni/commit/7aae5e562f6391e81dad409f0350fb9d5fbe369f)

- **作者**: Jiaqi Wang
- **时间**: 2026-11-24T05:38:06Z
- **提交信息**: [model, ops, config, data, trainer, docs] feat: add kimi_k3 multimodal MoE training with Ascend NPU kernels and GPU parity (#1291)

Co-authored-by: wangyier7 <wangyier7@users.noreply.github.com>

### [9db0eea](https://github.com/ByteDance-Seed/VeOmni/commit/9db0eea64cfb3aff181b85463023eec570866c91)

- **作者**: Coach257
- **时间**: 2026-11-24T02:35:31Z
- **提交信息**: [dist, optim, perf] feat: remove async-offload host syncs and bound Muon 3D expert workspace (#1452)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3021
- **最后更新**: 2026-11-24T12:45:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2345
- **最后更新**: 2026-11-24T14:56:34Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Saif Modan

## AI分析总结

## 提交分析总结

**提交记录：** [98fffa9] Honor export FPS in the VideoX-Fun GIF fallback (#534)

---

### 1. 主要更新类型
- **Bug修复**：修复了视频导出为GIF时帧率（FPS）参数未被正确尊重的问题，属于对视频生成管线中导出环节的小幅修复。

---

### 2. 关键变更点及其与项目整体方向的关系
- 该修复关注的是视频导出为GIF时的"fallback"（回退）路径，确保在GIF导出场景下用户指定的FPS参数能够被正确应用。
- VideoX-Fun作为一个视频生成框架（涵盖CogVideoX-Fun和Wan-Fun等子项目），其核心目标是提供高质量、可控的视频生成与导出能力。帧率控制是视频生成质量的重要参数，此修复直接关系到项目"输出可控视频"的整体目标，属于对核心功能链路的完善。

---

### 3. 对项目的影响和潜在意义
- **用户体验提升**：用户在使用GIF导出功能时，帧率将按预期生效，避免生成的GIF动画速度异常或不符合预期，提升了导出结果的一致性。
- **管线健壮性增强**：该修复填补了视频导出流程中的一个边界情况，使视频生成到最终格式转换的管线更加完整可靠。
- **社区贡献**：该提交带有社区协作者的签名（Saif Modan），表明项目社区活跃度良好，外部开发者在积极反馈和修复问题。

---

### 4. 值得关注的技术点
- **GIF fallback机制**：提交中提到的"GIF fallback"暗示项目在某些条件下会回退到GIF格式导出，这可能是在特定环境（如无ffmpeg等）下的兼容策略，值得关注该机制的设计。
- **帧率传递链路**：FPS参数从用户配置到最终GIF编码器的传递过程中存在断点，这类"参数丢失"问题在视频生成项目中较为常见，反映了对导出链路参数透传的重视。

---

### 5. 基于README项目背景的影响
- VideoX-Fun项目（含CogVideoX-Fun和Wan-Fun）以提供视频生成的Fun变体为核心，强调易用性和可控性。虽然此提交为小规模Bug修复，但它完善了视频生成→导出的完整用户体验闭环，与项目"开箱即用、参数可控"的定位一致。对于一个面向开源社区的视频生成框架而言，这类看似微小但直接影响用户体验的修复，有助于提升项目在社区中的口碑和使用可靠性，为后续更多功能迭代奠定稳定基础。

## 详细提交记录

### [98fffa9](https://github.com/aigc-apps/VideoX-Fun/commit/98fffa929bb373edcbfa3620e9aa05cd65a53103)

- **作者**: Saif Modan
- **时间**: 2026-11-24T03:20:36Z
- **提交信息**: Honor export FPS in the VideoX-Fun GIF fallback (#534)

Co-authored-by: Saif Modan <saifmodan2006@users.noreply.github.com>

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 7003
- **最后更新**: 2026-11-25T04:25:06Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 9
- **主要提交者**: Alex Ameen, eigen, xiufanl

## AI分析总结

# FlashInfer 昨日提交分析总结

## 一、主要更新类型

昨日提交以**性能优化**和 **Bug 修复**为主，辅以防御性校验、测试与文档增强。性能优化覆盖 SM90 Cake prefill、Trellis GEMM split-K、MoE 共享专家 staging、MLA NVFP4 decode mega output、Blackwell Cake prefill 状态池化、Sage FP8 稀疏注意力开销削减、NVFP4 QToken 稀疏注意力调度及 D512 GQA decode 等；修复集中在 CUDA graph 捕获、EP 调优回退、MXFP8 缓存污染、Hopper FP8 tile 校验、SM100 字节视图 scales 及 MegaMoE 后续问题；另将最低 Python 版本升至 3.11。

## 二、关键变更与项目方向

- **新硬件全栈覆盖**：性能提交横跨 H100（sm90a）、RTX PRO 6000（sm120）、Blackwell B200/GB300（sm100a/103a）与 Rubin（sm107a），项目正同时维护三代平台的峰值性能。
- **线性注意力 Cake**：SM90 侧通过长序列 warm-up 切分实现单次 kernel 启动与 CUDA Graph 捕获，对比旧 Cake 提速 3.52×、对比 FLA 0.6.0 达 7.94×；Blackwell 侧引入状态池、BF16/FP16 状态与 Philox 随机舍入，较 cuDNN 基线取得约 1.7× 几何平均加速。
- **低精度与 MoE 融合**：MoE 共享专家 BF16 输入单次 Triton launch staging 到 MXFP8，Rubin EP4 前向从 227.7µs 降至 188.1µs；NVFP4 decode 打通 run_mega 融合路径（Q RoPE + 注意力 + 逆 RoPE + 量化），加速 1.11×–1.37×。
- **稀疏注意力极致调优**：NVFP4 prefill 做 gather4 合并 scale 拷贝（32→8）、实测 per-layout 延迟模型（误差 ≤1.004×）与按 KV tile 计数的均衡 CLC 调度（SM 利用率从 71% 提升）；D512 GQA decode 改用密集 NVFP4 乘法指令并优化 TMEM 环形槽复用，超越 trtllm-gen FP8 基线。
- **数值可复现性**：Trellis GEMM split-K 以 `allow_split_k` 显式 opt-in，刻意不用 `batch_invariant` 认证命名，保持默认位稳定。
- **正确性修复**：修复 CUDA graph 捕获期内存池污染调优缓存、EP 离线调优回退、调优预算未纳入缓存键、MegaMoE FP8 tile K=128 校验、uint8 字节视图 scales 等问题；Blackwell GenPhase scale-pusher 计数在**内核构造期**即拒绝零/负值，实现 fail-fast。
- **MegaMoE 生态收敛**：#9740 合入后的一系列 follow-up（校验、缓存隔离、benchmark grid、文档）体现从"功能可用"到"生产稳健"的过渡。

## 三、影响与潜在意义

性能数字均附严格基准（B200/GB300/VR200/Rubin），巩固了 FlashInfer 相对 cuDNN、FLA、trtllm-gen 的竞争力。CUDA Graph 友好化、状态池与 graph-safe 行为使 vLLM/TensorRT-LLM 等引擎可直接嵌入，减少胶水代码。正确性修复降低了线上静默出错风险，对生产稳定性意义重大。位稳定性 opt-in 与大量"修复前必失败"的数值回归测试，反映项目向可认证、可复现推理演进。

## 四、值得关注的技术点

- **融合 staging 单 launch** 模式在 MoE 与 MLA 中反复出现，是统一的性能范式。
- **PDL（程序化依赖启动）** 使量化器与注意力内核重叠执行，Sage 主机时间减半。
- **缓存键签名钩子**（`get_tactic_cache_key`）统一管理调优缓存身份，避免跨预算复用错误赢家。
- **均衡调度与 L2 局部性权衡**：按 L2 占用选择最长优先或仅移动最短两波。
- **测试缓存污染**是并行测试下调优器类系统的隐性 flaky 根源；硬件靶向的分层 CI 与 PR 模板约束显示治理趋于成熟，项目已常规化接受 AI 辅助开发。

## 五、整体意义

FlashInfer 正沿三条主线推进：压榨各代硬件内核性能上限、完善 NVFP4/MXFP8 等低精度全链路、通过严格位级与回归测试建立数值可信度。"新硬件先行、旧路径加固"的双轨节奏，推动其从"更快的内核集合"演进为"可直接嵌入生产推理栈的完整内核基础设施"，进一步巩固开源推理内核事实标准的地位。

## 详细提交记录

### [f29e705](https://github.com/flashinfer-ai/flashinfer/commit/f29e705efed818214dd810a5b7db1295a5bfa3b6)

- **作者**: eigen
- **时间**: 2026-11-24T22:32:18Z
- **提交信息**: perf(cake_gdp): warm-up split and one launch per call for the SM90 prefill (#9989)

## Summary

The SM90 (sm_90a) Cake prefill of `chunk_gated_delta_product` behind
`backend="cake"` takes bf16 q/k/v and returns bf16 output, with K = 128,
V = 64, an FP32 state and `num_householder` 1 to 4. This PR adds a
warm-up split of long sequences. Before, a sequence ran on one CTA per
head. Now a long sequence is cut into rows that CTAs run in parallel,
and each row after a cut first warms up from a zero state. The split
comes as three new programs, the split twins of the existing V6 programs
(plain, initial state and `state_indices` pool). The PR also makes the
route one kernel launch per call, and its split tables can be captured
in a CUDA graph. There are two baselines. The first is the previous Cake
release, the Cake SM90 path currently in FlashInfer. The second is FLA
0.6.0 (`fla.ops.gated_delta_product.chunk_gated_delta_product`), the
strongest applicable non-Cake baseline on SM90, because FlashInfer's
cuDNN backend for this op is SM100-only. Over the 88 workloads in the
first table, the geometric-mean speedup over the previous Cake release
is **3.52×** (min 1.43×, same timing mode). Over FLA 0.6.0 it is
**7.94×** (min 5.98×, eager/eager).

Cake also ships the gated delta product prefill on sm_100a and sm_103a,
and the gated delta product decode on sm_90a, sm_100a, sm_103a and
sm_107a; this PR's changes are on sm_90a.

## Performance

NVIDIA H100 80GB HBM3 (sm_90a); PyTorch 2.14.1 with the CUDA 13.0
runtime, CUDA 13.4 toolkit, FLA 0.6.0. Latencies are medians in µs. Each
speedup is the paired median of the baseline/new Cake latency ratio;
above 1 means the new Cake is faster. The new Cake is timed as a CUDA
graph. On some rows the previous Cake path cannot be captured, because
it copies a pageable host tensor during capture. Those rows time the
previous Cake eager and compare it with the new Cake eager; the mode
column marks them. FLA does not capture, so it is timed eager and
compared with the new Cake eager. Every row uses `num_householder = 3`
and stores the output and the final state. Every sequence with history
reads an initial state. In A rows, `nx1+L` means n one-token sequences
that read an initial state, followed by one sequence of L tokens that
starts from a zero state. B rows are one sequence that reads an initial
state. C rows are two sequences (`a+b`): the first reads an initial
state, and the second starts from a zero state. In the second table,
`nxL` means n sequences of L tokens, and every sequence reads an initial
state.

| Workload | H | Sequence lengths | New Cake graph (µs) | New Cake eager
(µs) | Previous Cake (µs) | Previous Cake mode | Speedup vs previous
Cake (same mode) | FLA 0.6.0 eager (µs) | Speedup vs FLA (eager/eager) |
|---|---:|---|---:|---:|---:|---|---:|---:|---:|
| A_H10_L8192_d0 | 10 | 8192 | 114.2 | 114.9 | 364.7 | eager | 3.164 |
1027.0 | 8.932 |
| A_H10_L8192_d1 | 10 | 1x1+8192 | 114.5 | 114.6 | 862.7 | eager | 7.538
| 1065.8 | 9.313 |
| A_H10_L8192_d4 | 10 | 4x1+8192 | 115.0 | 115.2 | 868.2 | eager | 7.523
| 1064.8 | 9.224 |
| A_H10_L8192_d8 | 10 | 8x1+8192 | 116.1 | 115.9 | 881.7 | eager | 7.603
| 1074.4 | 9.277 |
| A_H10_L8192_d15 | 10 | 15x1+8192 | 116.1 | 116.2 | 897.0 | eager |
7.720 | 1090.7 | 9.390 |
| A_H10_L16384_d0 | 10 | 16384 | 166.8 | 166.8 | 594.6 | eager | 3.566 |
1770.8 | 10.630 |
| A_H10_L16384_d1 | 10 | 1x1+16384 | 166.0 | 167.0 | 1301.2 | eager |
7.800 | 1797.6 | 10.770 |
| A_H10_L16384_d4 | 10 | 4x1+16384 | 166.4 | 167.4 | 1307.4 | eager |
7.813 | 1799.6 | 10.754 |
| A_H10_L16384_d8 | 10 | 8x1+16384 | 168.2 | 168.9 | 1327.9 | eager |
7.861 | 1812.7 | 10.725 |
| A_H10_L16384_d15 | 10 | 15x1+16384 | 168.2 | 168.9 | 1334.0 | eager |
7.899 | 1826.3 | 10.815 |
| A_H10_L32768_d0 | 10 | 32768 | 286.4 | 286.8 | 1053.0 | eager | 3.664
| 3284.3 | 11.480 |
| A_H10_L32768_d1 | 10 | 1x1+32768 | 287.9 | 288.8 | 2066.3 | eager |
7.148 | 3314.1 | 11.474 |
| A_H10_L32768_d4 | 10 | 4x1+32768 | 288.7 | 289.4 | 2075.6 | eager |
7.168 | 3319.9 | 11.473 |
| A_H10_L32768_d8 | 10 | 8x1+32768 | 288.4 | 289.1 | 2092.0 | eager |
7.238 | 3342.2 | 11.564 |
| A_H10_L32768_d15 | 10 | 15x1+32768 | 290.3 | 290.5 | 2101.3 | eager |
7.230 | 3351.8 | 11.532 |
| A_H10_L65536_d0 | 10 | 65536 | 533.2 | 532.4 | 1972.7 | eager | 3.707
| 6289.4 | 11.819 |
| A_H10_L65536_d1 | 10 | 1x1+65535 | 533.7 | 533.4 | 3503.7 | eager |
6.564 | 6303.6 | 11.824 |
| A_H10_L65536_d4 | 10 | 4x1+65532 | 538.5 | 539.6 | 3519.9 | eager |
6.510 | 6308.5 | 11.686 |
| A_H10_L65536_d8 | 10 | 8x1+65528 | 540.0 | 542.1 | 3537.3 | eager |
6.523 | 6328.4 | 11.672 |
| A_H10_L65536_d15 | 10 | 15x1+65521 | 541.4 | 540.8 | 3544.5 | eager |
6.552 | 6339.3 | 11.716 |
| A_H20_L8192_d0 | 20 | 8192 | 168.7 | 168.7 | 664.9 | eager | 3.947 |
1348.0 | 7.992 |
| A_H20_L8192_d1 | 20 | 1x1+8192 | 167.9 | 168.1 | 1277.8 | eager |
7.607 | 1373.0 | 8.182 |
| A_H20_L8192_d4 | 20 | 4x1+8192 | 169.7 | 169.4 | 1284.1 | eager |
7.582 | 1382.5 | 8.162 |
| A_H20_L8192_d8 | 20 | 8x1+8192 | 170.3 | 170.1 | 1298.8 | eager |
7.635 | 1386.8 | 8.153 |
| A_H20_L8192_d15 | 20 | 15x1+8192 | 172.3 | 173.1 | 1302.4 | eager |
7.533 | 1398.1 | 8.086 |
| A_H20_L16384_d0 | 20 | 16384 | 306.6 | 306.8 | 1133.7 | eager | 3.697
| 2445.7 | 7.987 |
| A_H20_L16384_d1 | 20 | 1x1+16384 | 306.8 | 306.8 | 2092.7 | eager |
6.824 | 2476.2 | 8.074 |
| A_H20_L16384_d4 | 20 | 4x1+16384 | 307.3 | 307.1 | 2100.7 | eager |
6.841 | 2480.5 | 8.078 |
| A_H20_L16384_d8 | 20 | 8x1+16384 | 308.0 | 308.8 | 2118.6 | eager |
6.867 | 2486.8 | 8.052 |
| A_H20_L16384_d15 | 20 | 15x1+16384 | 309.7 | 309.9 | 2132.5 | eager |
6.881 | 2500.1 | 8.070 |
| A_H20_L32768_d0 | 20 | 32768 | 536.9 | 537.6 | 2060.0 | eager | 3.813
| 4637.5 | 8.632 |
| A_H20_L32768_d1 | 20 | 1x1+32768 | 538.2 | 538.2 | 3604.6 | eager |
6.691 | 4667.6 | 8.674 |
| A_H20_L32768_d4 | 20 | 4x1+32768 | 541.6 | 543.3 | 3616.0 | eager |
6.658 | 4676.6 | 8.605 |
| A_H20_L32768_d8 | 20 | 8x1+32768 | 546.0 | 551.7 | 3630.9 | eager |
6.586 | 4679.0 | 8.486 |
| A_H20_L32768_d15 | 20 | 15x1+32768 | 551.9 | 554.8 | 3633.1 | eager |
6.550 | 4691.0 | 8.454 |
| A_H20_L65536_d0 | 20 | 65536 | 1038.0 | 1038.4 | 3895.7 | eager |
3.756 | 8959.1 | 8.627 |
| A_H20_L65536_d1 | 20 | 1x1+65535 | 1040.1 | 1039.8 | 6504.7 | eager |
6.253 | 8972.9 | 8.630 |
| A_H20_L65536_d4 | 20 | 4x1+65532 | 1047.3 | 1053.2 | 6530.5 | eager |
6.197 | 8980.2 | 8.519 |
| A_H20_L65536_d8 | 20 | 8x1+65528 | 1049.6 | 1046.5 | 6538.1 | eager |
6.243 | 8983.7 | 8.591 |
| A_H20_L65536_d15 | 20 | 15x1+65521 | 1058.5 | 1060.4 | 6541.5 | eager
| 6.167 | 8992.2 | 8.476 |
| A_H40_L8192_d0 | 40 | 8192 | 304.6 | 304.9 | 795.3 | graph | 2.614 |
1990.2 | 6.530 |
| A_H40_L8192_d1 | 40 | 1x1+8192 | 307.2 | 307.1 | 802.0 | graph | 2.619
| 2020.9 | 6.578 |
| A_H40_L8192_d4 | 40 | 4x1+8192 | 307.1 | 307.6 | 799.5 | graph | 2.606
| 2032.9 | 6.615 |
| A_H40_L8192_d8 | 40 | 8x1+8192 | 308.4 | 309.5 | 804.9 | graph | 2.607
| 2047.5 | 6.617 |
| A_H40_L8192_d15 | 40 | 15x1+8192 | 318.5 | 319.2 | 814.2 | graph |
2.547 | 2066.7 | 6.463 |
| A_H40_L16384_d0 | 40 | 16384 | 543.8 | 544.6 | 1580.1 | graph | 2.907
| 3786.4 | 6.949 |
| A_H40_L16384_d1 | 40 | 1x1+16384 | 547.1 | 546.0 | 1595.6 | graph |
2.905 | 3818.4 | 6.989 |
| A_H40_L16384_d4 | 40 | 4x1+16384 | 550.9 | 552.9 | 1584.9 | graph |
2.883 | 3824.0 | 6.869 |
| A_H40_L16384_d8 | 40 | 8x1+16384 | 552.2 | 550.6 | 1589.4 | graph |
2.880 | 3839.8 | 6.975 |
| A_H40_L16384_d15 | 40 | 15x1+16384 | 562.8 | 563.5 | 1603.2 | graph |
2.848 | 3864.8 | 6.863 |
| A_H40_L32768_d0 | 40 | 32768 | 1034.2 | 1033.8 | 3151.5 | graph |
3.050 | 7364.4 | 7.121 |
| A_H40_L32768_d1 | 40 | 1x1+32768 | 1035.8 | 1038.3 | 3184.8 | graph |
3.066 | 7375.6 | 7.113 |
| A_H40_L32768_d4 | 40 | 4x1+32768 | 1045.6 | 1041.8 | 3163.9 | graph |
3.023 | 7382.7 | 7.090 |
| A_H40_L32768_d8 | 40 | 8x1+32768 | 1052.2 | 1054.6 | 3164.6 | graph |
3.009 | 7400.3 | 7.027 |
| A_H40_L32768_d15 | 40 | 15x1+32768 | 1065.1 | 1065.6 | 3181.2 | graph
| 2.990 | 7424.9 | 6.975 |
| A_H40_L65536_d0 | 40 | 65536 | 2042.3 | 2043.0 | 6352.8 | graph |
3.118 | 14577.6 | 7.134 |
| A_H40_L65536_d1 | 40 | 1x1+65535 | 2042.8 | 2044.7 | 6446.0 | graph |
3.170 | 14574.8 | 7.127 |
| A_H40_L65536_d4 | 40 | 4x1+65532 | 2047.6 | 2048.1 | 6369.1 | graph |
3.110 | 14574.8 | 7.120 |
| A_H40_L65536_d8 | 40 | 8x1+65528 | 2055.8 | 2058.3 | 6336.3 | graph |
3.095 | 14600.5 | 7.091 |
| A_H40_L65536_d15 | 40 | 15x1+65521 | 2066.0 | 2066.8 | 6403.3 | graph
| 3.106 | 14615.9 | 7.072 |
| A_H80_L8192_d0 | 80 | 8192 | 543.6 | 542.7 | 804.3 | graph | 1.480 |
3417.7 | 6.298 |
| A_H80_L8192_d1 | 80 | 1x1+8192 | 547.2 | 553.0 | 797.2 | graph | 1.455
| 3455.4 | 6.223 |
| A_H80_L8192_d4 | 80 | 4x1+8192 | 550.6 | 549.9 | 806.6 | graph | 1.467
| 3466.6 | 6.307 |
| A_H80_L8192_d8 | 80 | 8x1+8192 | 563.8 | 562.7 | 817.6 | graph | 1.449
| 3488.6 | 6.201 |
| A_H80_L8192_d15 | 80 | 15x1+8192 | 590.5 | 591.0 | 843.9 | graph |
1.430 | 3525.3 | 5.979 |
| A_H80_L16384_d0 | 80 | 16384 | 1032.7 | 1032.3 | 1608.4 | graph |
1.554 | 6807.4 | 6.599 |
| A_H80_L16384_d1 | 80 | 1x1+16384 | 1038.7 | 1036.5 | 1591.7 | graph |
1.531 | 6837.9 | 6.598 |
| A_H80_L16384_d4 | 80 | 4x1+16384 | 1048.8 | 1050.5 | 1602.9 | graph |
1.529 | 6840.1 | 6.523 |
| A_H80_L16384_d8 | 80 | 8x1+16384 | 1060.6 | 1061.7 | 1610.6 | graph |
1.517 | 6852.6 | 6.451 |
| A_H80_L16384_d15 | 80 | 15x1+16384 | 1083.1 | 1083.8 | 1636.2 | graph
| 1.512 | 6895.2 | 6.375 |
| A_H80_L32768_d0 | 80 | 32768 | 2038.5 | 2038.1 | 3307.9 | graph |
1.618 | 13534.2 | 6.646 |
| A_H80_L32768_d1 | 80 | 1x1+32768 | 2044.1 | 2042.1 | 3244.4 | graph |
1.586 | 13582.1 | 6.648 |
| A_H80_L32768_d4 | 80 | 4x1+32768 | 2050.1 | 2051.8 | 3271.9 | graph |
1.603 | 13595.5 | 6.633 |
| A_H80_L32768_d8 | 80 | 8x1+32768 | 2070.6 | 2066.2 | 3256.7 | graph |
1.574 | 13614.0 | 6.597 |
| A_H80_L32768_d15 | 80 | 15x1+32768 | 2090.2 | 2094.9 | 3370.8 | graph
| 1.613 | 13661.8 | 6.525 |
| A_H80_L65536_d0 | 80 | 65536 | 4065.6 | 4055.1 | 6606.9 | graph |
1.624 | 26922.5 | 6.614 |
| A_H80_L65536_d1 | 80 | 1x1+65535 | 4050.9 | 4054.7 | 6502.2 | graph |
1.582 | 27001.6 | 6.645 |
| A_H80_L65536_d4 | 80 | 4x1+65532 | 4072.4 | 4074.8 | 6521.4 | graph |
1.579 | 27032.6 | 6.604 |
| A_H80_L65536_d8 | 80 | 8x1+65528 | 4077.6 | 4065.4 | 6534.7 | graph |
1.597 | 27061.5 | 6.639 |
| A_H80_L65536_d15 | 80 | 15x1+65521 | 4125.3 | 4087.6 | 6581.9 | graph
| 1.586 | 27067.7 | 6.615 |
| B_H10 | 10 | 65536 | 533.0 | 533.6 | 1965.4 | eager | 3.686 | 6289.1 |
11.775 |
| B_H20 | 20 | 65536 | 1038.5 | 1038.4 | 3894.4 | eager | 3.756 | 8967.8
| 8.634 |
| B_H40 | 40 | 65536 | 2041.4 | 2041.9 | 6349.6 | graph | 3.108 |
14563.5 | 7.131 |
| B_H80 | 80 | 65536 | 4078.9 | 4057.6 | 6583.1 | graph | 1.591 |
26976.1 | 6.652 |
| C_H10 | 10 | 36864+28672 | 553.9 | 553.7 | 2092.5 | eager | 3.770 |
4830.2 | 8.720 |
| C_H20 | 20 | 36864+28672 | 1052.3 | 1052.4 | 4136.5 | eager | 3.936 |
7479.8 | 7.104 |
| C_H40 | 40 | 36864+28672 | 2070.7 | 2071.0 | 3633.8 | graph | 1.754 |
14244.6 | 6.881 |
| C_H80 | 80 | 36864+28672 | 4117.7 | 4145.4 | 6540.0 | graph | 1.578 |
27955.2 | 6.687 |

Most of the 21 short and single-sequence batches below do not take the
split, so there the new and previous Cake run the same kernel and ratios
near 1 are expected.

| Workload | H | Sequence lengths | New Cake graph (µs) | New Cake eager
(µs) | Previous Cake (µs) | Previous Cake mode | Speedup vs previous
Cake (same mode) | FLA 0.6.0 eager (µs) | Speedup vs FLA (eager/eager) |
|---|---:|---|---:|---:|---:|---|---:|---:|---:|
| S_H10_1x1024 | 10 | 1024 | 105.4 | 105.7 | 105.4 | graph | 1.000 |
721.7 | 6.804 |
| S_H10_1x8192 | 10 | 8192 | 113.8 | 114.7 | 364.4 | eager | 3.172 |
1025.6 | 8.938 |
| S_H10_1x32768 | 10 | 32768 | 284.3 | 284.5 | 1047.6 | eager | 3.687 |
3278.8 | 11.529 |
| S_H10_4x4096 | 10 | 4x4096 | 402.9 | 403.0 | 402.8 | graph | 1.000 |
1168.2 | 2.900 |
| S_H10_16x1024 | 10 | 16x1024 | 217.1 | 217.3 | 217.1 | graph | 1.000 |
1147.8 | 5.283 |
| S_H10_64x256 | 10 | 64x256 | 150.6 | 150.7 | 150.7 | graph | 1.001 |
1120.0 | 7.447 |
| S_H10_64x1024 | 10 | 64x1024 | 523.8 | 523.9 | 523.5 | graph | 1.000 |
3537.4 | 6.752 |
| S_H20_64x1024 | 20 | 64x1024 | 1038.0 | 1036.4 | 1034.7 | graph |
**0.999** | 6844.3 | 6.601 |
| S_H24_1x1024 | 24 | 1024 | 106.1 | 106.2 | 106.0 | graph | **0.999** |
733.7 | 6.913 |
| S_H24_1x8192 | 24 | 8192 | 181.5 | 182.2 | 752.4 | eager | 4.134 |
1480.3 | 8.130 |
| S_H24_1x32768 | 24 | 32768 | 646.4 | 646.7 | 2420.8 | eager | 3.745 |
5193.1 | 8.036 |
| S_H24_4x4096 | 24 | 4x4096 | 407.5 | 407.4 | 407.3 | graph | **0.999**
| 2386.2 | 5.857 |
| S_H24_16x1024 | 24 | 16x1024 | 317.5 | 318.0 | 317.8 | graph | 1.001 |
2259.0 | 7.103 |
| S_H24_64x256 | 24 | 64x256 | 340.3 | 340.5 | 340.3 | graph | 1.000 |
2275.9 | 6.680 |
| S_H40_16x1024 | 40 | 16x1024 | 522.6 | 523.7 | 522.7 | graph | 1.000 |
3584.3 | 6.837 |
| S_H80_1x1024 | 80 | 1024 | 111.9 | 112.0 | 112.1 | graph | 1.002 |
726.6 | 6.492 |
| S_H80_1x8192 | 80 | 8192 | 543.9 | 544.2 | 804.5 | graph | 1.480 |
3416.7 | 6.282 |
| S_H80_1x32768 | 80 | 32768 | 2035.4 | 2036.4 | 3263.2 | graph | 1.604
| 13569.2 | 6.670 |
| S_H80_4x4096 | 80 | 4x4096 | 1205.5 | 1204.9 | 1214.4 | graph | 1.006
| 6938.6 | 5.758 |
| S_H80_16x1024 | 80 | 16x1024 | 1038.5 | 1035.3 | 1036.7 | graph |
**0.999** | 6887.3 | 6.652 |
| S_H80_64x256 | 80 | 64x256 | 1104.6 | 1087.6 | 1089.6 | graph | 1.000
| 6928.3 | 6.365 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* SM90 prefill processes mixed batches in a single launch, scheduling
shorter sequences alongside eligible long sequences.
* Eligible batches can use a split execution path when the scheduler
estimates it will be more efficient.
* **Bug Fixes**
* Applicable SM90 split programs now check for changed sequence offsets
during graph replay and report invalid replay inputs.
* **Documentation**
* Updated guidance on prefill scheduling and graph replay behavior
across supported GPU architectures.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [51e5803](https://github.com/flashinfer-ai/flashinfer/commit/51e580305928e2cceee6798125232b01f39d7382)

- **作者**: nv-yunzheq
- **时间**: 2026-11-24T22:11:55Z
- **提交信息**: perf(b12x): Add opt-in split-K for dense Trellis GEMMs (#9731)

<!-- .github/pull_request_template.md -->

## 📌 Description

At decode and spec-verify batch sizes, the dense EXL3 `trellis_t256`
GEMM in `b12x.gemm.trellis_linear` launches one CTA per output tile, and
each CTA walks the full K range. A 6144→1024 projection therefore runs
on 4 CTAs of a 188-SM RTX PRO 6000
([flashinfer-ai/flashinfer#9381](https://github.com/flashinfer-ai/flashinfer/issues/9381)).

**No new kernel is needed.** The W4A16 kernel already contains a stripe
split-K schedule with a lock-ordered cross-CTA finalize, which the
routed-MoE paths use. The dense Trellis host path turned it off in two
places:
- `compile_w4a16_gemm` forced `schedule_whole_tiles=True` for
`trellis_t256`;
- `run_trellis256_dense` capped the grid at the tile count.

This PR adds an opt-in small-M split-K schedule for dense Trellis plans.
It answers the issue's two design questions.

**1. Bit stability: opt-in, off by default.**
- `TrellisQuery` and `query_from_weight` gain `allow_split_k: bool =
False`. Default plans keep the whole-tile schedule and today's bits.
- Split-K needs `allow_split_k=True`. `validate_config` rejects a split
config otherwise, including through `override`.

The flag is deliberately not named `batch_invariant`. In FlashInfer that
name selects the certified mode of `flashinfer.batch_invariant`:
properties R1–R4, fingerprints, proved reduction orders and bitwise
acceptance tests, defaulting to `False`. Dense Trellis does not meet
that standard, with or without this PR.

What dense Trellis does guarantee was measured on RTX PRO 6000; see
*Bit-level behaviour* below.
- **Default whole-tile plans.** A row's bits do not depend on the
planned M (1–2048, three shapes, including an M whose default tile
config differs), on its position, or on its neighbours. A new GPU test
pins this.
- **Whole-tile bits depend on `tile_k`** (pre-existing, unchanged here).
- The kernel folds each K-tile through 2 intra-CTA warp groups at
`tile_k=64` and 4 at `tile_k=128`.
- Every `tile_k=64` config agrees with the default bit for bit; every
`tile_k=128` config differs.
- The existing tuning space admits `tile_k=128`, so an autotuned or
overridden plan can differ from the default (4.4e-06–7.6e-05 relative).
This is why the configuration-agreement property (R3) does not hold.
- **Split-K plans.**
  - They differ from whole-tile by at most 1.1e-04 relative.
- A row's bits depend on the slice count. They are identical across M
while the count stays the same, and change when the default count
changes with M.

**2. Plan-based path: a plan config, chosen at preparation.** A dense
Trellis `Plan` is already exact-M (`run` requires `x.shape[0] ==
query.max_rows`), so each decode M already has its own plan and no
launch-time switch is needed.
- `TrellisConfig` gains `split_k_slices: int | None = None`, a tuning
knob.
- With `allow_split_k=True`, `default_config` splits K when whole tiles
leave at least half the SMs idle.
- Autotune searches `{None, 2, 4, 8, 16}`.

The default slice count was fitted to RTX PRO 6000 sweeps:
- **At most 8 slices.** The finalize is serial per slice, and more than
8 never won.
- **An even split** of the tile's K-tiles, so no slice straggles.
- **At least 512 of K per slice for every two live 16-row blocks.**
- **Within one SM wave.**

Across 24 swept cases (3 shapes × M = 1–128 × 2–16 slices) the default
is within 9% of the fastest slice count (geomean 1.008).

Plumbing:
- `compile_w4a16_gemm(schedule_whole_tiles=None)`: `None` keeps the
layout default. The flag is recorded in `W4A16GemmCompileResult` and was
already part of the kernel cache key.
- `run_trellis256_dense(split_k_slices=None)`: sizes the grid as
`mn_tiles × split_k_slices`, capped at the persistent `grid_cap` so
every slice is co-resident. It checks that the slice count matches the
compiled schedule.
- The trellis_linear tuning contract bumps `query_schema_version` (4→5)
and `config_schema_version` (1→2), so cached Trellis tuning entries are
re-resolved.
- **No kernel code changes.** The split path reuses the existing
finalize:
- the slice order is fixed, so results are bit-stable run to run and
under CUDA-graph replay;
  - the last slice resets the lock word;
- scratch (`c_tmp`, lock words) is already sized for one partial tile
per output tile.

### Scope

- Dense `gemm.trellis_linear` plans (native and P24/P33 pair layouts) on
SM120/SM121.
- Opt-in only (`allow_split_k=True`). Default behaviour and bits are
unchanged.
- `block_rows == 8` is excluded from split-K: the M8 decode schedule
computes one whole tile per CTA by design.
- MoE Trellis paths are untouched.

### Kernel-level performance

Setup:
- **Hardware:** NVIDIA RTX PRO 6000 Blackwell Server Edition (SM120, 188
SMs).
- **Inputs:** K6 MCG Trellis weights (random payload) and FP16
activations.
- **Command:** `python
benchmarks/experimental/b12x/benchmark_trellis_dense_split_k.py
--sweep`.
- **Timing:** median CUPTI GPU time of the GEMM kernel with a cold L2
every iteration. Both Hadamard rotations are no-ops in the benchmark, so
only the Trellis GEMM launches.
- **Arms:** "whole tile" is the default plan. "split" is the
`allow_split_k=True` default plan.
- **Error:** relative error is the norm-relative difference of the GEMM
output from the whole-tile result.

| K × N | M | whole tile (µs) | split (µs) | slices | speedup | rel. err
vs whole tile |
|---|---|---|---|---|---|---|
| 6144 × 1024 | 1 | 116.3 | 33.0 | 8 | 3.52× | 3.1e-05 |
| 6144 × 1024 | 2 | 116.4 | 32.2 | 8 | 3.62× | 2.6e-05 |
| 6144 × 1024 | 4 | 111.5 | 32.4 | 8 | 3.44× | 4.0e-05 |
| 6144 × 1024 | 8 | 111.6 | 33.1 | 8 | 3.37× | 3.8e-05 |
| 6144 × 1024 | 16 | 111.6 | 33.2 | 8 | 3.37× | 4.3e-05 |
| 6144 × 1024 | 32 | 114.8 | 44.3 | 8 | 2.59× | 4.7e-05 |
| 6144 × 1024 | 64 | 120.2 | 56.6 | 6 | 2.12× | 3.9e-05 |
| 6144 × 1024 | 128 | 120.3 | 56.8 | 6 | 2.12× | 4.2e-05 |
| 6144 × 1024 | 512 | 120.6 | 54.8 | 4 | 2.20× | 4.4e-05 |
| 6144 × 1024 | 2048 | 125.5 | 125.5 | whole tile kept | 1.00× | 0 |
| 4096 × 6144 | 1 | 73.8 | 28.5 | 4 | 2.59× | 2.0e-05 |
| 4096 × 6144 | 2 | 73.6 | 28.4 | 4 | 2.59× | 2.9e-05 |
| 4096 × 6144 | 4 | 73.8 | 28.6 | 4 | 2.58× | 3.1e-05 |
| 4096 × 6144 | 8 | 73.8 | 29.0 | 4 | 2.54× | 3.8e-05 |
| 4096 × 6144 | 16 | 73.8 | 29.0 | 4 | 2.55× | 3.7e-05 |
| 4096 × 6144 | 32 | 75.2 | 33.9 | 4 | 2.22× | 3.6e-05 |
| 4096 × 6144 | 64 | 78.2 | 44.1 | 4 | 1.77× | 3.6e-05 |
| 4096 × 6144 | 128 | 78.3 | 49.9 | 2 | 1.57× | 2.9e-05 |
| 4096 × 6144 | 512 | 131.2 | 131.2 | whole tile kept | 1.00× | 0 |
| 4096 × 6144 | 2048 | 404.5 | 404.5 | whole tile kept | 1.00× | 0 |
| 2048 × 4096 | 1 | 38.3 | 19.2 | 4 | 2.00× | 2.2e-05 |
| 2048 × 4096 | 2 | 38.3 | 19.2 | 4 | 1.99× | 1.8e-05 |
| 2048 × 4096 | 4 | 38.3 | 19.4 | 4 | 1.98× | 2.1e-05 |
| 2048 × 4096 | 8 | 38.3 | 19.6 | 4 | 1.95× | 1.8e-05 |
| 2048 × 4096 | 16 | 38.3 | 19.7 | 4 | 1.95× | 2.1e-05 |
| 2048 × 4096 | 32 | 39.6 | 24.5 | 4 | 1.62× | 2.2e-05 |
| 2048 × 4096 | 64 | 42.0 | 30.1 | 2 | 1.39× | 2.0e-05 |
| 2048 × 4096 | 128 | 42.0 | 30.1 | 2 | 1.40× | 2.0e-05 |
| 2048 × 4096 | 512 | 42.8 | 42.8 | whole tile kept | 1.00× | 0 |
| 2048 × 4096 | 2048 | 132.4 | 132.6 | whole tile kept | 1.00× | 0 |

- The issue's standalone harness reported 117.5 → 41.2 / 80.5 → 35.5 /
46.7 → 26.3 µs at M=4 for the three projections.
- Every split row was bit-identical across repeated runs.

### Bit-level behaviour

Setup: RTX PRO 6000 (SM120), K6 MCG weights, BF16 activations. Every
comparison is bitwise (`torch.equal`).

**A. Rows across M.** Each default (whole-tile) plan for M rows against
the first M rows of the M=2048 plan.

| K × N | planned M | default configs (block_rows, tile_k, tile_n) |
rows bit-equal to the M=2048 plan |
|---|---|---|---|
| 6144 × 1024 | 1, 4, 16, 32, 64, 65, 128, 512, 2048 | (64, 64, 256) |
all |
| 4096 × 6144 | 1, 4, 16, 32, 64, 65, 128, 512, 2048 | (48, 64, 128);
(64, 64, 256) | all |
| 2048 × 4096 | 1, 4, 16, 32, 64, 65, 128, 512, 2048 | (64, 64, 256) |
all |

**B. Position and neighbours.** One row at positions 0, 17, 63 of an
M=64 plan, among different random neighbours, against the same row run
alone: bit-equal at every position.

**C. Configuration agreement.** Every config the tuning contract admits
for a whole-tile 6144×1024 plan, against the default config.

| M | tile_k | intra-CTA K fold | configs (block_rows, tile_n) |
bit-equal to the default | rel. diff |
|---|---|---|---|---|---|
| 4 | 64 | 2 K-groups, m8 fold | (8, 128), (8, 256), (16, 128), (16,
256), (32, 128), (32, 256), (48, 128), (48, 256), (64, 128), (64, 256) |
all | 0 |
| 4 | 128 | 4 K-groups, m8 fold | (8, 64), (8, 128), (16, 64), (16,
128), (32, 64), (32, 128), (48, 64), (64, 64) | none | 4.4e-06 |
| 64 | 64 | 2 K-groups, m8 fold | (8, 128), (8, 256), (16, 128), (16,
256), (32, 128), (32, 256), (48, 128), (48, 256), (64, 128), (64, 256) |
all | 0 |
| 64 | 128 | 4 K-groups, m8 fold | (8, 64), (8, 128), (16, 64), (16,
128), (32, 64), (32, 128), (48, 64), (64, 64) | none | 7.6e-05 |

**D. Split-K** (`allow_split_k=True` default plans, 6144×1024).

| M | slices | bit-equal to whole tile | rel. diff vs whole tile | row 0
bit-equal to the M=1 split plan |
|---|---|---|---|---|
| 1 | 8 | no | 7.9e-06 | yes |
| 4 | 8 | no | 6.3e-05 | yes |
| 16 | 8 | no | 6.7e-05 | yes |
| 32 | 8 | no | 8.3e-05 | yes |
| 64 | 6 | no | 1.1e-04 | no |
| 512 | 4 | no | 1.1e-04 | no |


## 🔍 Related Issues

#9381 

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/...`

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Trellis dense GEMM supports optional split-K execution for eligible
workloads. Split-K remains disabled by default and can be enabled during
planning and tuning.
* Scheduling can use whole tiles or split-K, with validation for
supported configurations.
* **Tests**
* Expanded coverage for split-K planning, output accuracy,
repeatability, graph replay, and concurrent execution.
* **Benchmarks**
* Added a benchmark comparing whole-tile and split-K performance, output
error, and repeatability on supported CUDA hardware.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [af45204](https://github.com/flashinfer-ai/flashinfer/commit/af45204a5aab7301150fea8c32cac05538f5a7a2)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-24T20:52:17Z
- **提交信息**: perf(moe_ep): fuse SM107 shared-expert input staging (#9916)

<!-- .github/pull_request_template.md -->

## 📌 Description

Stage BF16 shared-expert inputs directly into the MXFP8 E4M3 workspace.
One Triton launch writes the activations, both scale layouts, and the
padded rows. `FLASHINFER_MEGA_FUSED_STAGE=0` selects the existing Torch
path.

A warm CUDA-graph forward on Rubin EP4 went from 227.7 to 188.1 µs at 32
tokens per rank and capacity 456. The case used H5120/I2304, 416 routed
experts, top-6, and one E4M3 shared expert. Both runs used MXFP4 routed
weights, MXFP8 activations, and the same inference tile (256×64×256,
4×1) with BF16 combine.

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

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe_ep/test_sm107_shared_staging.py
tests/moe_ep/test_sm107_shared_expert.py`

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

Assisted by Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved BF16 shared-input staging for MXFP8 on supported NVIDIA
hardware.
* Unsupported inputs and configurations continue to use the existing
fallback behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Akaash Parthasarathy <akaashp@nvidia.com>

### [a27e579](https://github.com/flashinfer-ai/flashinfer/commit/a27e5791162bddfe4b59b2787a40b5a18be5352f)

- **作者**: Guangyun Han
- **时间**: 2026-11-24T20:17:54Z
- **提交信息**: feat(mla): enable mega output for NVFP4 decode (#9439)

<!-- .github/pull_request_template.md -->

## 📌 Description

Enable fused Q RoPE, inverse output RoPE, and FP8 quantization for
native NVFP4 split-KV decode through `run_mega`. Both existing CTA
schedules support Direct, Merge2, and General final-output plans. Direct
plans write FP8 in the attention CTA. Split plans write partial contexts
and LSEs, and the existing merge kernel writes the FP8 result.
Stage-1-only plans require a separate final output step.

Tests compare mega output, scales, and LSE with the separate kernels.
They cover aligned and offset queries, empty and partial selections,
more than 32 splits, single and dual caches, and CUDA Graph replay with
poisoned destinations.

## Performance

RTX PRO 6000 Blackwell Server Edition, 188 SMs. DSpark block size 6 and
batch size 20 produce Q=140 verification queries, with H=64 and D=512.
Inputs use 20 independent 32K-token histories, seven shifted SWA windows
per request, and causal top-512 selections for sparse layers.

Times are median microseconds from three alternating trials using warmed
CUDA Graph replay and warm L2. Both arms include Q RoPE, attention,
inverse output RoPE, and FP8 quantization. Cache packing and index
construction occur before timing.

### Public dispatch

The table includes existing FP8 and NVFP4 prefill paths for context.
This PR enables the native NVFP4 decode paths measured below.

| Cache | Selected KV | Selected implementation | Mega µs | Separate
pipeline µs | Speedup |
|---|---:|---|---:|---:|---:|
| FP8 inline | 640 | Unsplit FP8 decode | 81.98 | 93.04 | 1.14× |
| FP8 inline | 128 | Unsplit FP8 decode | 29.86 | 40.08 | 1.34× |
| FP8 footer | 640 | Unsplit FP8 decode | 92.63 | 102.57 | 1.11× |
| FP8 footer | 128 | Unsplit FP8 decode | 29.45 | 38.67 | 1.31× |
| NVFP4 | 640 | NVFP4 prefill | 80.45 | 89.05 | 1.11× |
| NVFP4 | 128 | NVFP4 prefill | 24.31 | 33.34 | 1.37× |

### NVFP4 decode plans

Q=140, H=64, 128 SWA entries plus 512 selected entries. Each chunk
contains 64 entries. All rows use the existing grouped decode schedule.
Each comparison uses identical partitions in its fused and
separate-transform arms.

| Chunks per split | Merge | Mega µs | Separate pipeline µs | Speedup |
|---|---|---:|---:|---:|
| 1+1+1+1+1+1+1+1+1+1 | general | 182.13 | 208.34 | 1.14× |
| 2+2+2+2+2 | general | 113.52 | 126.22 | 1.11× |
| 3+3+3+1 | general | 106.97 | 118.44 | 1.11× |
| 4+4+2 | general | 98.67 | 108.50 | 1.10× |
| 5+5 | merge2 | 104.10 | 114.34 | 1.10× |
| 6+4 | merge2 | 102.16 | 112.29 | 1.10× |
| 7+3 | merge2 | 102.05 | 111.27 | 1.09× |
| 8+2 | merge2 | 81.73 | 91.61 | 1.12× |
| 9+1 | merge2 | 90.07 | 100.21 | 1.11× |
| 10 | direct | 95.50 | 103.79 | 1.09× |

All measured plans passed CUDA Graph replay with poisoned destinations
and comparisons against separate transforms. NVFP4 output values,
scales, and LSE matched exactly for the same partition. Independent
numerical checks sampled query rows across request boundaries.

## 🔍 Related Issues

This PR builds on #9356, which enables native NVFP4 prefill mega.

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] 149 targeted tests passed on RTX PRO 6000, including 32 NVFP4
decode mega cases, the existing NVFP4 suite, and prefill mega
regressions. Changed-file pre-commit hooks passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/attention/test_sparse_mla_sm120_nvfp4_decode_mega.py
tests/attention/test_sparse_mla_sm120_dsv4_nvfp4.py
tests/attention/test_sparse_mla_sm120_nvfp4_prefill_mega.py`

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

Review against #9356. The decode scheduling and attention pipeline stay
in the existing implementation. Code and validation were assisted by
Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* NVFP4 sparse MLA decode now supports mega output, including grouped
and ungrouped decode paths and result merging.
* **Tests**
* Expanded coverage across request counts, chunk settings, query
offsets, and boundary sequence lengths.
* Added checks for CUDA graph replay, output validity, reference
accuracy, and consistency with baseline results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [98c130a](https://github.com/flashinfer-ai/flashinfer/commit/98c130a946c9f71da72d20b11d072e541c66693f)

- **作者**: Cindy Zhang
- **时间**: 2026-11-24T19:46:36Z
- **提交信息**: build: raise minimum Python version to 3.11 (#9990)

Use Python 3.11 for builds and package metadata now that Python 3.10 has
reached end of life. Keep the mypy target aligned with the minimum
supported interpreter.

This allows cu134 JIT-cache provider builds to resolve torch after the
Python 3.10 wheel disappeared from the nightly index.

Validation: changed-file pre-commit hooks, TOML parsing and version
consistency checks, and git diff --check passed. Full cu134 provider
build remains to be validated in CI.

AI assistance: prepared with Codex.

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Raise the minimum supported Python version from 3.10 to 3.11, keeping
`.python-version`, package metadata, and the mypy target aligned.

The cu134 nightly provider builds fail because the PyTorch nightly index
no longer lists Python 3.10 wheels. Previous builds succeeded by
downloading an older September 23 wheel that is now unavailable. Using
Python 3.11 allows these builds to resolve a compatible torch package.

This change drops Python 3.10 support.


## 🔍 Related Issues

<!-- Link any related issues here -->
Fix #9976
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

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/...`
The complete cu134 provider build still needs validation in CI.

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Python 3.11 is now the minimum supported version. Python 3.10 is no
longer supported, so use Python 3.11 or newer. The documented supported
versions are Python 3.11 through 3.14.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d9d966a](https://github.com/flashinfer-ai/flashinfer/commit/d9d966a383b69d0d86d26edb99517daacd58363f)

- **作者**: Cindy Zhang
- **时间**: 2026-11-24T18:52:04Z
- **提交信息**: test: verify cold MoE autotuning profiles fused finalize (#9978)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Add a focused NVFP4 MoE test that verifies cold GEMM2 autotuning
actually profiles a fused FINALIZE specialization.

The test uses a fresh AutoTuner and checks CUDA kernel activity during a
successful profiling invocation.
It reuses the existing numerical test body through a shared helper,
preserving the original parameterization, input preparation, reference
calculation, and tolerances.

  Only tests are changed.


## 🔍 Related Issues

<!-- Link any related issues here -->
Follow-up test coverage for #9507
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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

  Suggested CI test targets: `tests/moe/test_trtllm_cutlass_fused_moe.py

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
The new test runs on SM100/SM103 and skips if CUDA profiling records no
activity. Temporary changes to the tuner and deterministic settings are
restored afterward.

This test verifies actual FINALIZE profiling coverage. It does not
directly validate the workspace-size bound or establish that reverting
#9507 would fail the test. Profiling timings are not used for
performance claims.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Added coverage for cold NVFP4 autotuning on supported GPUs, including
verification that profiling selects a finite GEMM2 tactic with a fused
finalize step.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [33b7d20](https://github.com/flashinfer-ai/flashinfer/commit/33b7d201c8ae4789716b5ef474b7f0f170309aae)

- **作者**: Cindy Zhang
- **时间**: 2026-11-24T18:51:15Z
- **提交信息**: test: strengthen PDL bias and top-k ordering regressions (#9964)

Make the delayed BF16 bias observable with a deterministic value and a
stale-bias control. Preserve the original top-k short-row regressions
and add delayed seq_lens cases crossing into selection for page-table
and ragged kernels, checked against an independent reference.

Validation: changed-file pre-commit hooks and static checks passed. GPU
tests remain pending because this host has no usable NVIDIA driver or
PyTorch environment.

AI-assisted: Codex.

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Strengthen the existing PDL ordering regressions for BF16 warp split-K
GEMM and cluster top-k.

- **BF16 bias:** Set the first two bias elements to a deterministic,
exactly representable value and verify that zeroing them
changes the corresponding output columns. This ensures BF16 rounding
cannot hide a stale bias read.
- **Cluster top-k:** Add page-table and ragged cases where a producer
updates `seq_lens[0]` from 1 to 4096, crossing
`top_k=2048`. Validate the selected indices against an independent
`torch.topk` reference, ignoring output order.

The original three short-row top-k cases, including the ragged offsets
dependency, are preserved. The GEMM regression retains its original
shape, direct warp split-K invocation, and bitwise comparison. No GPU
operations are added between `late_store` and the consumer.

  Only tests are changed.

## 🔍 Related Issues

<!-- Link any related issues here -->
Follow-up test hardening for #7288 and #7591.
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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: tests/gemm/test_mm_bf16.py
tests/utils/test_topk.py
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
The stale values and delayed producer intentionally expose ordering
violations; they do not model production timing or sequence-length
growth.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded matrix multiplication coverage to verify that changes to bias
values affect the corresponding output columns and that restored values
produce the expected results.
* Expanded top-k coverage for longer sequences, checking results against
expected rankings and verifying that delayed sequence-length updates are
handled correctly.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1debfbf](https://github.com/flashinfer-ai/flashinfer/commit/1debfbf85044157a344c140a676437c7b127a41f)

- **作者**: Cindy Zhang
- **时间**: 2026-11-24T18:50:54Z
- **提交信息**: test(prims_ts): cover E4M3 V rescaling after row-max rise (#9958)

Add BF16 and E4M3 Q/K regressions with a later KV tile raising the row
maximum by about four log2 units. Preserve the full 16K query and KV
shape while sharing an independent FP32 reference across identical query
rows.

Validated on SM100: both cases fail with the pre-fix kernel and pass on
PR #8549 head and the current checkout. A lazy-correction plus
P-scale-448 mutation passes the original regression and fails these new
cases. Changed-file pre-commit checks pass.

AI-assisted implementation and validation with Codex.

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Add a regression test for E4M3 V attention when a later KV tile raises
the running row maximum.

The regression added in #8549 places its highest-scoring key in the
first KV tile. This new case places high-scoring keys at positions 0 and
8192, making the later tile raise the row maximum by approximately four
log2 units—below the previous lazy- correction threshold of eight.
The test covers BF16 and E4M3 Q/K with E4M3 V. It preserves the full 16K
query and KV lengths and compares every output row against an
independent FP32 attention reference. Since all queries are identical
and the mask is dense, the reference is computed once and broadcast
across query rows.


## 🔍 Related Issues

<!-- Link any related issues here -->
Follow-up regression coverage for flashinfer-ai/flashinfer#8549

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

 Suggested CI test targets: tests/attention/test_attention_ts_context.py
Validated both new cases on SM100 with CUDA 13.0, PyTorch 2.14.1+cu130,
and CuTe DSL 4.8.0:

| Q/K dtype | Pre-fix kernel: relative L2 | PR #8549 head: relative L2 |
|:-----|:------:|------:|
|BF16    |   29.24% — failed    |     2.13% — passed |
| E4M3  |  16.78% — failed    |  0.97% — passed |

The pre-fix comparison uses the original fmha_kernel.py from #8549’s
parent commit (05de7b248), mounted over the PR-head snapshot. Both cases
pass on the exact PR head (ee8fe7a179) and the current checkout, using
the existing tolerances.
An additional sensitivity check retained lazy correction while forcing P
scale to 448: the original regression passed, while both new cases
failed. This demonstrates additional detection beyond the existing
first-tile case.

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
One parameterized test function adds two GPU cases. Requires a supported
SM100-class Blackwell GPU.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Added coverage for BF16 and E4M3 attention with E4M3 values on
SM100/SM103, including a long-sequence case that checks results against
an FP32 reference.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7774af2](https://github.com/flashinfer-ai/flashinfer/commit/7774af26fa347aefd43e2a45cb8d9ab93a7a12e4)

- **作者**: eigen
- **时间**: 2026-11-24T17:25:58Z
- **提交信息**: feat(cake_gdp): state pools, BF16/FP16 state and stochastic rounding for the SM100a/SM103a prefill (#9991)

## Summary

Until this PR, the Blackwell (sm_100a / sm_103a) prefill of
`chunk_gated_delta_product` behind `backend="cake"` (bf16 q/k/v/output,
K = 128, V = 64, `num_householder = 3`) took only a dense FP32 state.
This PR adds four things to that prefill. First, it adds state pools:
`state_indices` reads each sequence's initial state from a slot of
`initial_state`, and the new keyword-only `output_state_indices` writes
its final state to a slot of `output_state` (by default, the read slot).
Second, it adds a bf16 or fp16 state; the FP32 state stays. Third, a
16-bit state is rounded once, at the final store, with
round-to-nearest-even by default. Fourth, stochastic rounding is
available instead, controlled by `rand_seed` and `philox_rounds`. The
variant measured below is the bf16 state pool with
round-to-nearest-even. It is compared with two baselines. The first is
the previous Cake release on the same pools. This is the call pattern an
inference engine uses today: gather the pool slots to FP32, run the
shipped dense FP32 Cake prefill, then cast to bf16 and scatter back. The
second is FlashInfer's existing `backend="cudnn"` (cuDNN 9.24.0) with
bf16 pools and `state_indices`, the strongest non-Cake baseline. Over
the 88 workloads below, the geometric-mean speedup over the previous
Cake release is **1.107×** on B200 (min 0.987×) and **1.112×** on GB300
(min 1.011×). Over cuDNN it is **1.738×** on B200 (min 1.050×) and
**1.717×** on GB300 (min 1.048×).

Cake also ships the dense FP32 prefill on sm_90a, sm_100a and sm_103a,
and the gated delta product decode with FP32 and fp16 state pools; the
family ships on sm_90a, sm_100a, sm_103a and sm_107a, with prefill on
sm_90a, sm_100a and sm_103a and this PR's features on sm_100a and
sm_103a.

## Performance

NVIDIA B200 (sm_100a) and NVIDIA GB300 (sm_103a); PyTorch 2.14.1 with
the CUDA 13.0 runtime, CUDA 13.4 toolkit, cuDNN 9.24.0. Timing is
CUDA-graph replay with a warm L2. Latencies are medians in µs. Speedup
is the paired median of the baseline/new Cake latency ratio; above 1
means Cake is faster. Gates follow FlashInfer's test input generator,
and every call stores the final state to a pool slot. In A rows, `nx1+L`
means n one-token sequences that read their initial state from a pool
slot, followed by one sequence of L tokens that begins from a zero
state. B rows are one sequence that reads its initial state from a pool
slot. C rows are two sequences (`a+b`); the first reads its initial
state from a pool slot, and the second begins from a zero state.

### B200 (sm_100a)

| Workload | H | Sequence lengths | New Cake (µs) | Previous Cake (µs) |
Speedup vs previous Cake | cuDNN (µs) | Speedup vs cuDNN |
|---|---:|---|---:|---:|---:|---:|---:|
| A_H10_L8192_d0 | 10 | 8192 | 70.9 | 99.6 | 1.404 | 163.1 | 2.300 |
| A_H10_L8192_d1 | 10 | 1x1+8192 | 72.6 | 91.4 | 1.256 | 167.1 | 2.292 |
| A_H10_L8192_d4 | 10 | 4x1+8192 | 72.5 | 93.1 | 1.284 | 144.3 | 1.991 |
| A_H10_L8192_d8 | 10 | 8x1+8192 | 70.9 | 93.5 | 1.318 | 144.6 | 2.039 |
| A_H10_L8192_d15 | 10 | 15x1+8192 | 75.0 | 102.4 | 1.373 | 142.6 |
1.901 |
| A_H10_L16384_d0 | 10 | 16384 | 118.0 | 142.6 | 1.208 | 249.1 | 2.110 |
| A_H10_L16384_d1 | 10 | 1x1+16384 | 118.1 | 138.5 | 1.172 | 257.3 |
2.172 |
| A_H10_L16384_d4 | 10 | 4x1+16384 | 120.0 | 140.6 | 1.175 | 212.2 |
1.768 |
| A_H10_L16384_d8 | 10 | 8x1+16384 | 118.8 | 142.6 | 1.198 | 221.2 |
1.859 |
| A_H10_L16384_d15 | 10 | 15x1+16384 | 119.9 | 148.8 | 1.246 | 187.6 |
1.564 |
| A_H10_L32768_d0 | 10 | 32768 | 208.0 | 232.8 | 1.128 | 413.0 | 2.002 |
| A_H10_L32768_d1 | 10 | 1x1+32768 | 206.8 | 228.6 | 1.106 | 435.5 |
2.103 |
| A_H10_L32768_d4 | 10 | 4x1+32768 | 206.1 | 228.7 | 1.110 | 273.7 |
1.327 |
| A_H10_L32768_d8 | 10 | 8x1+32768 | 206.1 | 230.7 | 1.119 | 376.1 |
1.821 |
| A_H10_L32768_d15 | 10 | 15x1+32768 | 208.1 | 239.9 | 1.156 | 292.0 |
1.403 |
| A_H10_L65536_d0 | 10 | 65536 | 391.9 | 418.1 | 1.069 | 764.7 | 1.969 |
| A_H10_L65536_d1 | 10 | 1x1+65535 | 396.5 | 419.0 | 1.058 | 819.4 |
2.067 |
| A_H10_L65536_d4 | 10 | 4x1+65532 | 378.8 | 400.8 | 1.058 | 666.9 |
1.758 |
| A_H10_L65536_d8 | 10 | 8x1+65528 | 382.1 | 406.7 | 1.062 | 691.5 |
1.812 |
| A_H10_L65536_d15 | 10 | 15x1+65521 | 380.0 | 410.8 | 1.079 | 501.0 |
1.319 |
| B_H10 | 10 | 65536 | 389.4 | 417.0 | 1.068 | 763.1 | 1.965 |
| C_H10 | 10 | 36864+28672 | 398.6 | 418.1 | 1.058 | 767.2 | 1.941 |
| A_H20_L8192_d0 | 20 | 8192 | 118.8 | 144.6 | 1.212 | 249.1 | 2.087 |
| A_H20_L8192_d1 | 20 | 1x1+8192 | 119.7 | 140.5 | 1.179 | 288.0 | 2.417
|
| A_H20_L8192_d4 | 20 | 4x1+8192 | 118.8 | 144.7 | 1.222 | 213.1 | 1.791
|
| A_H20_L8192_d8 | 20 | 8x1+8192 | 120.0 | 150.7 | 1.256 | 202.7 | 1.698
|
| A_H20_L8192_d15 | 20 | 15x1+8192 | 124.2 | 167.2 | 1.347 | 208.2 |
1.677 |
| A_H20_L16384_d0 | 20 | 16384 | 204.1 | 230.5 | 1.127 | 411.6 | 2.016 |
| A_H20_L16384_d1 | 20 | 1x1+16384 | 204.1 | 226.5 | 1.107 | 507.2 |
2.486 |
| A_H20_L16384_d4 | 20 | 4x1+16384 | 204.0 | 230.7 | 1.135 | 1199.4 |
5.879 |
| A_H20_L16384_d8 | 20 | 8x1+16384 | 204.1 | 236.8 | 1.159 | 351.5 |
1.723 |
| A_H20_L16384_d15 | 20 | 15x1+16384 | 204.0 | 247.0 | 1.209 | 359.7 |
1.765 |
| A_H20_L32768_d0 | 20 | 32768 | 392.9 | 420.1 | 1.069 | 771.3 | 1.975 |
| A_H20_L32768_d1 | 20 | 1x1+32768 | 376.0 | 396.6 | 1.057 | 941.3 |
2.510 |
| A_H20_L32768_d4 | 20 | 4x1+32768 | 374.8 | 401.6 | 1.071 | 568.5 |
1.515 |
| A_H20_L32768_d8 | 20 | 8x1+32768 | 376.1 | 408.8 | 1.085 | 653.4 |
1.738 |
| A_H20_L32768_d15 | 20 | 15x1+32768 | 376.0 | 417.1 | 1.112 | 666.9 |
1.777 |
| A_H20_L65536_d0 | 20 | 65536 | 781.4 | 811.0 | 1.037 | 1540.2 | 1.973
|
| A_H20_L65536_d1 | 20 | 1x1+65535 | 744.7 | 779.5 | 1.038 | 1963.2 |
2.616 |
| A_H20_L65536_d4 | 20 | 4x1+65532 | 738.9 | 775.4 | 1.039 | 1082.4 |
1.463 |
| A_H20_L65536_d8 | 20 | 8x1+65528 | 719.0 | 765.6 | 1.066 | 1232.1 |
1.673 |
| A_H20_L65536_d15 | 20 | 15x1+65521 | 729.3 | 774.4 | 1.061 | 1330.9 |
1.828 |
| B_H20 | 20 | 65536 | 771.3 | 801.0 | 1.040 | 1548.4 | 2.007 |
| C_H20 | 20 | 36864+28672 | 780.4 | 803.5 | 1.032 | 1795.7 | 2.318 |
| A_H40_L8192_d0 | 40 | 8192 | 226.7 | 253.2 | 1.116 | 443.6 | 1.954 |
| A_H40_L8192_d1 | 40 | 1x1+8192 | 226.7 | 251.0 | 1.103 | 251.1 | 1.102
|
| A_H40_L8192_d4 | 40 | 4x1+8192 | 226.6 | 261.3 | 1.150 | 630.0 | 2.778
|
| A_H40_L8192_d8 | 40 | 8x1+8192 | 226.4 | 271.6 | 1.202 | 355.6 | 1.576
|
| A_H40_L8192_d15 | 40 | 15x1+8192 | 232.7 | 298.3 | 1.282 | 378.1 |
1.625 |
| A_H40_L16384_d0 | 40 | 16384 | 369.9 | 400.6 | 1.075 | 846.2 | 2.285 |
| A_H40_L16384_d1 | 40 | 1x1+16384 | 379.1 | 402.5 | 1.064 | 455.9 |
1.200 |
| A_H40_L16384_d4 | 40 | 4x1+16384 | 372.8 | 405.6 | 1.091 | 560.4 |
1.501 |
| A_H40_L16384_d8 | 40 | 8x1+16384 | 374.0 | 419.1 | 1.121 | 667.5 |
1.788 |
| A_H40_L16384_d15 | 40 | 15x1+16384 | 390.3 | 458.0 | 1.172 | 688.4 |
1.767 |
| A_H40_L32768_d0 | 40 | 32768 | 760.0 | 786.0 | 1.035 | 1700.0 | 2.251
|
| A_H40_L32768_d1 | 40 | 1x1+32768 | 755.8 | 787.7 | 1.038 | 847.0 |
1.113 |
| A_H40_L32768_d4 | 40 | 4x1+32768 | 716.0 | 761.1 | 1.052 | 1037.5 |
1.435 |
| A_H40_L32768_d8 | 40 | 8x1+32768 | 724.2 | 783.6 | 1.069 | 1321.1 |
1.804 |
| A_H40_L32768_d15 | 40 | 15x1+32768 | 743.0 | 816.3 | 1.090 | 1354.4 |
1.806 |
| A_H40_L65536_d0 | 40 | 65536 | 1533.1 | 1548.9 | 1.007 | 3452.0 |
2.251 |
| A_H40_L65536_d1 | 40 | 1x1+65535 | 1536.1 | 1561.2 | 1.019 | 1652.9 |
1.077 |
| A_H40_L65536_d4 | 40 | 4x1+65532 | 1450.3 | 1546.4 | 1.049 | 2140.3 |
1.440 |
| A_H40_L65536_d8 | 40 | 8x1+65528 | 1409.3 | 1540.8 | 1.052 | 2724.5 |
1.874 |
| A_H40_L65536_d15 | 40 | 15x1+65521 | 1415.4 | 1544.4 | 1.079 | 2695.9
| 1.875 |
| B_H40 | 40 | 65536 | 1536.6 | 1559.6 | 1.018 | 3493.4 | 2.266 |
| C_H40 | 40 | 36864+28672 | 1542.3 | 1541.3 | 1.007 | 1660.1 | 1.077 |
| A_H80_L8192_d0 | 80 | 8192 | 374.1 | 401.6 | 1.073 | 456.4 | 1.222 |
| A_H80_L8192_d1 | 80 | 1x1+8192 | 372.8 | 404.7 | 1.084 | 497.2 | 1.322
|
| A_H80_L8192_d4 | 80 | 4x1+8192 | 378.1 | 423.3 | 1.122 | 659.2 | 1.749
|
| A_H80_L8192_d8 | 80 | 8x1+8192 | 394.5 | 467.2 | 1.185 | 676.0 | 1.711
|
| A_H80_L8192_d15 | 80 | 15x1+8192 | 424.1 | 533.8 | 1.260 | 699.8 |
1.649 |
| A_H80_L16384_d0 | 80 | 16384 | 751.7 | 783.5 | 1.039 | 863.4 | 1.145 |
| A_H80_L16384_d1 | 80 | 1x1+16384 | 740.4 | 775.4 | 1.043 | 894.2 |
1.202 |
| A_H80_L16384_d4 | 80 | 4x1+16384 | 715.9 | 779.5 | 1.069 | 1301.8 |
1.796 |
| A_H80_L16384_d8 | 80 | 8x1+16384 | 746.5 | 825.3 | 1.101 | 1325.3 |
1.768 |
| A_H80_L16384_d15 | 80 | 15x1+16384 | 753.0 | 870.5 | 1.155 | 1323.2 |
1.746 |
| A_H80_L32768_d0 | 80 | 32768 | 1516.2 | 1550.4 | 1.021 | 1646.8 |
1.089 |
| A_H80_L32768_d1 | 80 | 1x1+32768 | 1498.7 | 1558.7 | 1.029 | 1767.5 |
1.174 |
| A_H80_L32768_d4 | 80 | 4x1+32768 | 1406.2 | 1513.6 | 1.061 | 2647.6 |
1.850 |
| A_H80_L32768_d8 | 80 | 8x1+32768 | 1431.8 | 1589.4 | 1.101 | 2730.2 |
1.877 |
| A_H80_L32768_d15 | 80 | 15x1+32768 | 1451.1 | 1589.4 | 1.099 | 2670.8
| 1.833 |
| A_H80_L65536_d0 | 80 | 65536 | 3049.7 | 3068.4 | 1.005 | 3239.1 |
1.065 |
| A_H80_L65536_d1 | 80 | 1x1+65535 | 3053.6 | 3049.1 | 1.003 | 3355.9 |
1.101 |
| A_H80_L65536_d4 | 80 | 4x1+65532 | 2977.0 | 3017.2 | 1.013 | 5316.2 |
1.821 |
| A_H80_L65536_d8 | 80 | 8x1+65528 | 3032.2 | 2910.3 | **0.987** |
5425.3 | 1.779 |
| A_H80_L65536_d15 | 80 | 15x1+65521 | 3087.5 | 3108.0 | 1.012 | 5372.6
| 1.758 |
| B_H80 | 80 | 65536 | 3067.0 | 3051.1 | **0.999** | 3223.1 | 1.050 |
| C_H80 | 80 | 36864+28672 | 3068.9 | 3081.9 | 1.002 | 3278.1 | 1.067 |

### GB300 (sm_103a)

| Workload | H | Sequence lengths | New Cake (µs) | Previous Cake (µs) |
Speedup vs previous Cake | cuDNN (µs) | Speedup vs cuDNN |
|---|---:|---|---:|---:|---:|---:|---:|
| A_H10_L8192_d0 | 10 | 8192 | 67.5 | 92.1 | 1.364 | 151.5 | 2.245 |
| A_H10_L8192_d1 | 10 | 1x1+8192 | 67.5 | 90.0 | 1.333 | 156.3 | 2.320 |
| A_H10_L8192_d4 | 10 | 4x1+8192 | 67.5 | 90.0 | 1.334 | 167.8 | 2.480 |
| A_H10_L8192_d8 | 10 | 8x1+8192 | 67.6 | 91.3 | 1.346 | 137.2 | 2.032 |
| A_H10_L8192_d15 | 10 | 15x1+8192 | 67.5 | 97.5 | 1.449 | 135.1 | 2.001
|
| A_H10_L16384_d0 | 10 | 16384 | 104.4 | 129.0 | 1.236 | 231.3 | 2.216 |
| A_H10_L16384_d1 | 10 | 1x1+16384 | 104.4 | 126.9 | 1.216 | 241.6 |
2.314 |
| A_H10_L16384_d4 | 10 | 4x1+16384 | 104.4 | 126.9 | 1.216 | 264.9 |
2.539 |
| A_H10_L16384_d8 | 10 | 8x1+16384 | 104.4 | 127.6 | 1.227 | 190.4 |
1.824 |
| A_H10_L16384_d15 | 10 | 15x1+16384 | 110.5 | 139.2 | 1.260 | 176.1 |
1.593 |
| A_H10_L32768_d0 | 10 | 32768 | 186.3 | 213.0 | 1.143 | 378.9 | 2.035 |
| A_H10_L32768_d1 | 10 | 1x1+32768 | 186.3 | 207.5 | 1.112 | 411.6 |
2.208 |
| A_H10_L32768_d4 | 10 | 4x1+32768 | 186.3 | 208.8 | 1.121 | 454.6 |
2.440 |
| A_H10_L32768_d8 | 10 | 8x1+32768 | 186.3 | 210.9 | 1.132 | 311.3 |
1.670 |
| A_H10_L32768_d15 | 10 | 15x1+32768 | 186.3 | 217.0 | 1.165 | 272.3 |
1.462 |
| A_H10_L65536_d0 | 10 | 65536 | 341.9 | 366.5 | 1.072 | 676.7 | 1.979 |
| A_H10_L65536_d1 | 10 | 1x1+65535 | 342.0 | 362.5 | 1.063 | 740.1 |
2.164 |
| A_H10_L65536_d4 | 10 | 4x1+65532 | 342.0 | 362.5 | 1.062 | 835.5 |
2.444 |
| A_H10_L65536_d8 | 10 | 8x1+65528 | 341.9 | 364.5 | 1.066 | 542.6 |
1.587 |
| A_H10_L65536_d15 | 10 | 15x1+65521 | 342.0 | 370.7 | 1.084 | 636.6 |
1.859 |
| B_H10 | 10 | 65536 | 341.9 | 366.5 | 1.072 | 676.5 | 1.979 |
| C_H10 | 10 | 36864+28672 | 354.2 | 374.7 | 1.058 | 713.6 | 2.018 |
| A_H20_L8192_d0 | 20 | 8192 | 114.6 | 139.2 | 1.215 | 235.5 | 2.054 |
| A_H20_L8192_d1 | 20 | 1x1+8192 | 112.5 | 135.1 | 1.200 | 272.3 | 2.419
|
| A_H20_L8192_d4 | 20 | 4x1+8192 | 112.7 | 139.2 | 1.231 | 249.8 | 2.213
|
| A_H20_L8192_d8 | 20 | 8x1+8192 | 113.1 | 145.3 | 1.283 | 168.0 | 1.491
|
| A_H20_L8192_d15 | 20 | 15x1+8192 | 112.6 | 153.5 | 1.363 | 192.4 |
1.709 |
| A_H20_L16384_d0 | 20 | 16384 | 198.6 | 223.2 | 1.124 | 389.1 | 1.959 |
| A_H20_L16384_d1 | 20 | 1x1+16384 | 198.6 | 219.1 | 1.103 | 479.2 |
2.413 |
| A_H20_L16384_d4 | 20 | 4x1+16384 | 198.6 | 223.2 | 1.124 | 435.9 |
2.194 |
| A_H20_L16384_d8 | 20 | 8x1+16384 | 198.6 | 229.3 | 1.155 | 284.6 |
1.433 |
| A_H20_L16384_d15 | 20 | 15x1+16384 | 204.7 | 245.6 | 1.200 | 331.7 |
1.622 |
| A_H20_L32768_d0 | 20 | 32768 | 362.4 | 387.0 | 1.068 | 703.4 | 1.941 |
| A_H20_L32768_d1 | 20 | 1x1+32768 | 362.5 | 383.6 | 1.058 | 885.7 |
2.444 |
| A_H20_L32768_d4 | 20 | 4x1+32768 | 362.4 | 388.0 | 1.072 | 814.0 |
2.245 |
| A_H20_L32768_d8 | 20 | 8x1+32768 | 362.4 | 393.1 | 1.085 | 511.9 |
1.413 |
| A_H20_L32768_d15 | 20 | 15x1+32768 | 362.4 | 401.3 | 1.107 | 606.1 |
1.673 |
| A_H20_L65536_d0 | 20 | 65536 | 671.7 | 695.2 | 1.034 | 1321.9 | 1.966
|
| A_H20_L65536_d1 | 20 | 1x1+65535 | 672.7 | 691.2 | 1.028 | 1696.7 |
2.524 |
| A_H20_L65536_d4 | 20 | 4x1+65532 | 673.6 | 694.2 | 1.032 | 1559.5 |
2.315 |
| A_H20_L65536_d8 | 20 | 8x1+65528 | 671.7 | 698.3 | 1.040 | 964.5 |
1.436 |
| A_H20_L65536_d15 | 20 | 15x1+65521 | 673.7 | 710.6 | 1.055 | 1154.0 |
1.714 |
| B_H20 | 20 | 65536 | 671.6 | 694.9 | 1.034 | 1321.2 | 1.966 |
| C_H20 | 20 | 36864+28672 | 690.1 | 708.6 | 1.028 | 1607.6 | 2.330 |
| A_H40_L8192_d0 | 40 | 8192 | 217.0 | 241.6 | 1.113 | 419.8 | 1.934 |
| A_H40_L8192_d1 | 40 | 1x1+8192 | 215.0 | 239.5 | 1.113 | 235.5 | 1.093
|
| A_H40_L8192_d4 | 40 | 4x1+8192 | 217.0 | 247.7 | 1.143 | 247.7 | 1.142
|
| A_H40_L8192_d8 | 40 | 8x1+8192 | 217.0 | 258.0 | 1.190 | 326.3 | 1.509
|
| A_H40_L8192_d15 | 40 | 15x1+8192 | 216.7 | 278.4 | 1.284 | 348.1 |
1.608 |
| A_H40_L16384_d0 | 40 | 16384 | 335.8 | 366.5 | 1.089 | 773.0 | 2.299 |
| A_H40_L16384_d1 | 40 | 1x1+16384 | 335.8 | 363.2 | 1.082 | 401.3 |
1.196 |
| A_H40_L16384_d4 | 40 | 4x1+16384 | 341.9 | 378.8 | 1.105 | 436.1 |
1.275 |
| A_H40_L16384_d8 | 40 | 8x1+16384 | 350.1 | 395.1 | 1.128 | 606.2 |
1.734 |
| A_H40_L16384_d15 | 40 | 15x1+16384 | 363.1 | 429.0 | 1.181 | 624.6 |
1.719 |
| A_H40_L32768_d0 | 40 | 32768 | 645.1 | 674.8 | 1.045 | 1471.4 | 2.279
|
| A_H40_L32768_d1 | 40 | 1x1+32768 | 645.8 | 672.7 | 1.041 | 713.7 |
1.105 |
| A_H40_L32768_d4 | 40 | 4x1+32768 | 647.1 | 683.8 | 1.055 | 824.3 |
1.273 |
| A_H40_L32768_d8 | 40 | 8x1+32768 | 657.3 | 703.5 | 1.071 | 1147.6 |
1.746 |
| A_H40_L32768_d15 | 40 | 15x1+32768 | 672.7 | 739.2 | 1.099 | 1169.3 |
1.737 |
| A_H40_L65536_d0 | 40 | 65536 | 1263.5 | 1290.1 | 1.021 | 2875.4 |
2.276 |
| A_H40_L65536_d1 | 40 | 1x1+65535 | 1263.6 | 1289.2 | 1.020 | 1352.7 |
1.070 |
| A_H40_L65536_d4 | 40 | 4x1+65532 | 1276.8 | 1306.5 | 1.023 | 1592.3 |
1.248 |
| A_H40_L65536_d8 | 40 | 8x1+65528 | 1282.0 | 1330.1 | 1.037 | 2243.5 |
1.750 |
| A_H40_L65536_d15 | 40 | 15x1+65521 | 1293.3 | 1358.8 | 1.051 | 2259.6
| 1.747 |
| B_H40 | 40 | 65536 | 1262.6 | 1289.5 | 1.021 | 2876.0 | 2.276 |
| C_H40 | 40 | 36864+28672 | 1274.0 | 1298.4 | 1.020 | 1381.3 | 1.084 |
| A_H80_L8192_d0 | 80 | 8192 | 337.9 | 366.5 | 1.085 | 411.6 | 1.217 |
| A_H80_L8192_d1 | 80 | 1x1+8192 | 341.9 | 372.6 | 1.090 | 443.3 | 1.298
|
| A_H80_L8192_d4 | 80 | 4x1+8192 | 352.2 | 398.3 | 1.131 | 591.8 | 1.681
|
| A_H80_L8192_d8 | 80 | 8x1+8192 | 368.7 | 437.9 | 1.183 | 614.4 | 1.662
|
| A_H80_L8192_d15 | 80 | 15x1+8192 | 403.4 | 501.7 | 1.245 | 640.9 |
1.589 |
| A_H80_L16384_d0 | 80 | 16384 | 647.1 | 675.7 | 1.044 | 739.3 | 1.142 |
| A_H80_L16384_d1 | 80 | 1x1+16384 | 647.2 | 679.9 | 1.049 | 775.8 |
1.197 |
| A_H80_L16384_d4 | 80 | 4x1+16384 | 658.2 | 706.5 | 1.073 | 1148.9 |
1.745 |
| A_H80_L16384_d8 | 80 | 8x1+16384 | 676.8 | 745.4 | 1.101 | 1163.9 |
1.720 |
| A_H80_L16384_d15 | 80 | 15x1+16384 | 705.5 | 804.8 | 1.142 | 1192.9 |
1.690 |
| A_H80_L32768_d0 | 80 | 32768 | 1256.4 | 1283.1 | 1.021 | 1363.9 |
1.086 |
| A_H80_L32768_d1 | 80 | 1x1+32768 | 1256.4 | 1289.1 | 1.026 | 1450.9 |
1.155 |
| A_H80_L32768_d4 | 80 | 4x1+32768 | 1268.7 | 1316.8 | 1.038 | 2229.2 |
1.757 |
| A_H80_L32768_d8 | 80 | 8x1+32768 | 1285.8 | 1354.0 | 1.053 | 2257.9 |
1.756 |
| A_H80_L32768_d15 | 80 | 15x1+32768 | 1312.7 | 1417.2 | 1.079 | 2284.4
| 1.740 |
| A_H80_L65536_d0 | 80 | 65536 | 2485.2 | 2511.8 | 1.011 | 2605.7 |
1.048 |
| A_H80_L65536_d1 | 80 | 1x1+65535 | 2482.1 | 2514.3 | 1.013 | 2708.4 |
1.091 |
| A_H80_L65536_d4 | 80 | 4x1+65532 | 2497.4 | 2546.6 | 1.020 | 4405.2 |
1.764 |
| A_H80_L65536_d8 | 80 | 8x1+65528 | 2513.9 | 2587.6 | 1.030 | 4430.8 |
1.762 |
| A_H80_L65536_d15 | 80 | 15x1+65521 | 2532.3 | 2636.7 | 1.041 | 4473.8
| 1.767 |
| B_H80 | 80 | 65536 | 2485.2 | 2511.8 | 1.011 | 2605.0 | 1.048 |
| C_H80 | 80 | 36864+28672 | 2492.3 | 2534.3 | 1.017 | 2702.3 | 1.084 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Blackwell Cake GDP prefill now supports dense and indexed state pools
in FP32, BF16, and FP16, with separate input and output state slots.
  * Added optional seeded stochastic rounding for 16-bit state writes.
* Added `output_state_indices`, `rand_seed`, and `philox_rounds` options
to the prefill API.
* **Bug Fixes**
* Invalid or out-of-range 64-bit state indices are safely treated as
invalid rather than wrapping.
* Empty-sequence state copies now support state pools and separate
read/write slots.
* **Compatibility**
* SM90 remains limited to FP32 state and does not support the new
write-slot or rounding options.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [a3a5d2e](https://github.com/flashinfer-ai/flashinfer/commit/a3a5d2e8507181eb791677b7a7be94c90630217a)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-24T17:01:55Z
- **提交信息**: fix(moe_ep): restore offline profiles for SM100 Standard (#9817)

<!-- .github/pull_request_template.md -->

## 📌 Description

Default the offline SM100 NVFP4 tuner to the serving Standard kernel.
Use `--implementation legacy` to tune the older NVFP4 backend.

Fixed workspaces can use a saved live-token profile at their existing
capacity. EP ranks compare the selected configs before consulting the
workspace pool or allocating symmetric storage.

## 🔍 Related Issues

Follow-up to #9740.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files and fixed any reported
issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted checks passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: `tests/cpu/moe_ep/test_tuning_dispatch.py`,
`tests/moe_ep/test_sm100_tuning_protocol.py`.

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

`--implementation next` remains accepted for one release.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* SM100 NVFP4 tuning now uses the native tuner by default; the legacy
tuner remains available through an explicit option.
* Standard inference profiles can be selected using live-token counts
and matching configuration settings.

* **Bug Fixes**
* Multi-rank workspace preparation now checks that ranks agree on
configuration and reports preparation or validation failures before
acquiring a workspace.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [11b60e7](https://github.com/flashinfer-ai/flashinfer/commit/11b60e7a2431850a58feca68bf73519973d309aa)

- **作者**: eigen
- **时间**: 2026-11-24T16:46:34Z
- **提交信息**: perf(cake_sage): cut host time per call and recover GB300 GPU-bound latency of the FP8 block-sparse attention (#9716)

This PR speeds up Sage FP8 block-sparse attention. The kernel runs on
FP8 E4M3 Q/K/V. It uses per-token Q scales, per-16-token K scales,
per-channel V scales and block-sparse KV selection. It comes in three
forms:
- pre-quantized FP8 attention;
- the combined API, which runs a fused BF16 quantizer and then the
attention;
- an INT8-QK/FP8-PV variant for sm_120a.

This PR changes the pre-quantized and combined forms on sm_100a and
sm_103a. It changes the attention launch and route choice. The attention
entries now take float8_e4m3fn Q/K/V directly. The wrapper no longer
makes uint8 views on every call. It allocates the output like Q and
launches the entry directly. Both changes lower the host (CPU) cost of
each call. On sm_103a, the fused BF16 quantizer in the combined API now
lets the attention launch start right after the quantizer starts, not
after its last store. This uses programmatic dependent launch (PDL).
Because of this, the sm_103a tail-split attention route now launches
with PDL on every row, with no exception for small rows.

Main is FlashInfer main 42bbaf163d, which this branch has merged and
which is still the previous Cake version. Outputs are bit-identical to
main. Compared with main, the pre-quantized attention call takes
1.859-1.947x less host time on B200 and 1.968-2.067x less on GB300
across the 15-row shape list. For example, GB300 B8/H32/Hkv32/S4096 sel
6 goes from 41.09 to 20.05 µs. The combined API call takes 1.380-1.497x
less host time on B200 and 1.366-1.425x less on GB300. This matters for
small calls whose latency is set by the CPU. On GB300, the combined call
was also measured queued behind other GPU work (GPU-bound). This PR is
faster on GPU-bound rows that use the sm_103a tail-split route. These
rows come from a wider shape grid than the tables. Each row below shows
main µs → PR µs, then the speedup:
- B1/H3/Hkv3/S4096 sel 24: 33.22 → 28.88, 1.150
- B1/H5/Hkv5/Sq=Sk=2048 sel 24: 29.13 → 25.08, 1.161
- B1/H5/Hkv5/S4096 sel 24: 37.49 → 33.38, 1.123
- B1/H10/Hkv10/Sq=Sk=2048 sel 24: 35.08 → 31.22, 1.124

Speedup is main / PR, so a value above 1 means this PR is faster. Each
run takes the median over 16 paired rounds. Each latency is the median
of 4 runs: 2 GPUs, each with a fixed and a rotated shape order. The
table columns mean:
- graph: the combined API under CUDA graph (CUPTI GPU time, cold L2).
- GPU-bound: the eager combined call queued behind a spin kernel (CUDA
events).
- eager: the eager combined call (CUPTI).
- Host time: the wall clock of the Python call.

Shapes are B/H/Hkv/S with Sq = Sk. sel is the number of selected KV
blocks per row. † marks a row whose attention launch in the combined
call differs from main. On sm_103a every combined call also starts the
attention launch early behind the quantizer; that alone is not marked by
†. A row counts as slower only if both of these hold:
- its median paired ratio exceeds 1 by more than run-to-run noise;
- this PR is slower in at least 14 of 16 rounds.

By that rule, no row in the GPU tables is slower than main on either
GPU. The lowest cells are 0.993 (B200 GPU-bound, B8/H32/Hkv32/S4096 sel
58) and 0.995 (GB300 GPU-bound, B2/H24/Hkv24/S16384 sel 32). Neither
meets the rule. The highest cells are 1.059 (GB300 eager,
B1/H8/Hkv8/S4096 sel 6), 1.047 (GB300 GPU-bound, B1/H8/Hkv8/S4096 sel 6)
and 1.030 (B200 graph, B1/H8/Hkv8/S4096 sel 32 †).

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.3 (PyTorch
2.13.0a0+9186a08b2c.nv26.07, nvcc 13.3), driver 580.82.07: combined API,
shape list**

| shape | sel | graph main | graph PR | graph speedup | GPU-bound main |
GPU-bound PR | GPU-bound speedup | eager main | eager PR | eager speedup
|
|---|---|---|---|---|---|---|---|---|---|---|
| B8/H32/Hkv32/S4096 | 6 | 460.85 | 460.95 | 1.000 | 487.29 | 487.89 |
0.999 | 469.43 | 468.76 | 1.001 |
| B8/H32/Hkv32/S4096 | 32 | 1084.86 | 1085.75 | 0.999 | 1229.65 |
1231.54 | 0.998 | 1113.87 | 1105.07 | 1.008 |
| B8/H32/Hkv32/S4096 | 58 | 1788.43 | 1797.55 | 0.995 | 1910.43 |
1923.07 | 0.993 | 1799.21 | 1807.45 | 0.995 |
| B1/H8/Hkv8/S4096 | 6 | 22.57 | 22.57 | 1.000 | 31.70 | 31.68 | 1.001 |
26.58 | 26.59 | 1.000 |
| B1/H8/Hkv8/S4096 † | 32 | 46.35 | 45.01 | 1.030 | 56.30 | 55.93 |
1.007 | 51.34 | 50.70 | 1.013 |
| B1/H8/Hkv8/S4096 | 58 | 67.46 | 66.52 | 1.014 | 78.79 | 78.78 | 1.000
| 73.12 | 72.82 | 1.004 |
| B1/H40/Hkv40/S32768 | 51 | 2116.00 | 2107.79 | 1.004 | 2216.83 |
2214.35 | 1.001 | 2100.06 | 2091.12 | 1.004 |
| B1/H40/Hkv40/S32768 | 128 | 4782.34 | 4764.82 | 1.004 | 4740.56 |
4742.98 | 0.999 | 4747.08 | 4753.71 | 0.999 |
| B1/H40/Hkv40/S32768 | 256 | 9096.12 | 9081.60 | 1.002 | 9012.46 |
9011.07 | 1.000 | 9055.06 | 9039.89 | 1.002 |
| B2/H24/Hkv24/S16384 | 32 | 812.60 | 815.41 | 0.997 | 931.05 | 935.86 |
0.995 | 828.52 | 828.78 | 1.000 |
| B1/H2/Hkv2/S4096 | 6 | 12.16 | 12.14 | 1.002 | 23.50 | 23.50 | 1.000 |
18.29 | 18.23 | 1.003 |
| B1/H2/Hkv2/S4096 | 58 | 24.81 | 24.86 | 0.998 | 35.80 | 35.84 | 0.999
| 31.02 | 30.99 | 1.001 |
| B1/H4/Hkv4/S4096 | 6 | 15.34 | 15.33 | 1.000 | 25.59 | 25.58 | 1.000 |
21.03 | 21.00 | 1.001 |
| B1/H4/Hkv4/S4096 | 58 | 40.22 | 40.22 | 1.000 | 51.44 | 51.23 | 1.004
| 46.70 | 46.53 | 1.004 |
| B1/H32/Hkv8/S4096 | 6 | 52.07 | 52.06 | 1.000 | 57.34 | 57.32 | 1.000
| 52.27 | 52.20 | 1.001 |

main = FlashInfer main 42bbaf163d, the previous Cake version. Latency in
µs: per run the median over 16 paired rounds, then the median of 4 runs
(2 GPUs, each with a fixed and a rotated shape order). graph = combined
API under CUDA graph (CUPTI GPU time, cold L2); GPU-bound = eager
combined call queued behind a spin kernel (CUDA events); eager = eager
combined call (CUPTI GPU time). Speedup = main / PR. † = the attention
launch of the combined call differs from main on that row.

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.3 (PyTorch
2.13.0a0+9186a08b2c.nv26.07, nvcc 13.3), driver 580.167.08: combined
API, shape list**

| shape | sel | graph main | graph PR | graph speedup | GPU-bound main |
GPU-bound PR | GPU-bound speedup | eager main | eager PR | eager speedup
|
|---|---|---|---|---|---|---|---|---|---|---|
| B8/H32/Hkv32/S4096 | 6 | 428.91 | 428.92 | 1.000 | 433.40 | 433.68 |
0.999 | 445.88 | 444.55 | 1.003 |
| B8/H32/Hkv32/S4096 | 32 | 894.23 | 894.12 | 1.000 | 901.47 | 900.47 |
1.001 | 911.79 | 910.65 | 1.001 |
| B8/H32/Hkv32/S4096 | 58 | 1354.98 | 1354.66 | 1.000 | 1390.12 |
1393.91 | 0.997 | 1371.95 | 1371.02 | 1.001 |
| B1/H8/Hkv8/S4096 | 6 | 20.85 | 20.86 | 0.999 | 29.20 | 27.88 | 1.047 |
30.86 | 29.15 | 1.059 |
| B1/H8/Hkv8/S4096 | 32 | 37.08 | 37.10 | 1.000 | 46.92 | 45.53 | 1.031
| 47.53 | 46.32 | 1.026 |
| B1/H8/Hkv8/S4096 | 58 | 52.34 | 52.33 | 1.000 | 62.32 | 60.02 | 1.038
| 62.73 | 61.56 | 1.019 |
| B1/H40/Hkv40/S32768 | 51 | 1563.54 | 1566.58 | 0.998 | 1582.64 |
1579.38 | 1.002 | 1580.33 | 1579.36 | 1.001 |
| B1/H40/Hkv40/S32768 | 128 | 3458.91 | 3470.74 | 0.997 | 3448.88 |
3449.80 | 1.000 | 3461.25 | 3476.66 | 0.996 |
| B1/H40/Hkv40/S32768 | 256 | 6516.83 | 6520.42 | 0.999 | 6477.22 |
6482.62 | 0.999 | 6487.70 | 6514.54 | 0.996 |
| B2/H24/Hkv24/S16384 | 32 | 669.85 | 670.02 | 1.000 | 678.33 | 681.50 |
0.995 | 687.28 | 686.00 | 1.002 |
| B1/H2/Hkv2/S4096 | 6 | 11.48 | 11.49 | 0.999 | 21.06 | 21.05 | 1.000 |
24.28 | 23.08 | 1.052 |
| B1/H2/Hkv2/S4096 | 58 | 20.61 | 20.60 | 1.000 | 30.74 | 30.34 | 1.013
| 33.75 | 32.44 | 1.041 |
| B1/H4/Hkv4/S4096 † | 6 | 14.41 | 14.41 | 1.000 | 23.74 | 23.10 | 1.028
| 26.58 | 25.48 | 1.043 |
| B1/H4/Hkv4/S4096 | 58 | 32.44 | 32.38 | 1.002 | 41.76 | 41.54 | 1.005
| 44.91 | 43.37 | 1.035 |
| B1/H32/Hkv8/S4096 | 6 | 47.40 | 47.42 | 1.000 | 51.73 | 51.73 | 1.000
| 50.71 | 49.41 | 1.026 |

main = FlashInfer main 42bbaf163d, the previous Cake version. Latency in
µs: per run the median over 16 paired rounds, then the median of 4 runs
(2 GPUs, each with a fixed and a rotated shape order). graph = combined
API under CUDA graph (CUPTI GPU time, cold L2); GPU-bound = eager
combined call queued behind a spin kernel (CUDA events); eager = eager
combined call (CUPTI GPU time). Speedup = main / PR. † = the attention
launch of the combined call differs from main on that row. On sm_103a
the fused quantizer of every combined call also lets the attention
launch start early, which main does not; that is not marked by †.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.3 (PyTorch
2.13.0a0+9186a08b2c.nv26.07, nvcc 13.3), driver 580.82.07: host (CPU)
time per call in µs, median of 4 runs of 16 rounds, shape list**

| shape | sel | attention main | attention PR | attention speedup |
combined main | combined PR | combined speedup |
|---|---|---|---|---|---|---|---|
| B8/H32/Hkv32/S4096 | 6 | 26.88 | 14.38 | 1.870 | 57.74 | 41.64 | 1.387
|
| B8/H32/Hkv32/S4096 | 32 | 27.01 | 14.39 | 1.877 | 57.74 | 41.63 |
1.387 |
| B8/H32/Hkv32/S4096 | 58 | 27.05 | 14.40 | 1.879 | 57.84 | 41.71 |
1.387 |
| B1/H8/Hkv8/S4096 | 6 | 25.44 | 13.10 | 1.942 | 51.37 | 34.34 | 1.496 |
| B1/H8/Hkv8/S4096 | 32 | 25.45 | 13.22 | 1.926 | 51.51 | 34.54 | 1.491
|
| B1/H8/Hkv8/S4096 | 58 | 25.64 | 13.21 | 1.940 | 51.53 | 34.59 | 1.490
|
| B1/H40/Hkv40/S32768 | 51 | 27.20 | 14.51 | 1.875 | 58.00 | 41.87 |
1.385 |
| B1/H40/Hkv40/S32768 | 128 | 27.19 | 14.51 | 1.874 | 57.76 | 41.85 |
1.380 |
| B1/H40/Hkv40/S32768 | 256 | 27.27 | 14.54 | 1.875 | 58.03 | 41.87 |
1.386 |
| B2/H24/Hkv24/S16384 | 32 | 26.81 | 14.42 | 1.859 | 57.61 | 41.57 |
1.386 |
| B1/H2/Hkv2/S4096 | 6 | 25.50 | 13.12 | 1.944 | 51.54 | 34.42 | 1.497 |
| B1/H2/Hkv2/S4096 | 58 | 25.45 | 13.12 | 1.940 | 51.59 | 34.52 | 1.494
|
| B1/H4/Hkv4/S4096 | 6 | 25.44 | 13.09 | 1.944 | 51.33 | 34.36 | 1.494 |
| B1/H4/Hkv4/S4096 | 58 | 25.26 | 13.11 | 1.926 | 51.29 | 34.26 | 1.497
|
| B1/H32/Hkv8/S4096 | 6 | 25.33 | 13.01 | 1.947 | 53.67 | 36.03 | 1.490
|

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.3 (PyTorch
2.13.0a0+9186a08b2c.nv26.07, nvcc 13.3), driver 580.167.08: host (CPU)
time per call in µs, median of 4 runs of 16 rounds, shape list**

| shape | sel | attention main | attention PR | attention speedup |
combined main | combined PR | combined speedup |
|---|---|---|---|---|---|---|---|
| B8/H32/Hkv32/S4096 | 6 | 41.09 | 20.05 | 2.049 | 83.58 | 60.68 | 1.378
|
| B8/H32/Hkv32/S4096 | 32 | 40.76 | 20.02 | 2.036 | 82.74 | 60.58 |
1.366 |
| B8/H32/Hkv32/S4096 | 58 | 41.33 | 20.19 | 2.047 | 83.09 | 60.47 |
1.374 |
| B1/H8/Hkv8/S4096 | 6 | 41.64 | 20.32 | 2.049 | 73.40 | 51.50 | 1.425 |
| B1/H8/Hkv8/S4096 | 32 | 42.01 | 20.64 | 2.035 | 73.70 | 52.02 | 1.417
|
| B1/H8/Hkv8/S4096 | 58 | 42.12 | 20.64 | 2.041 | 73.67 | 51.81 | 1.422
|
| B1/H40/Hkv40/S32768 | 51 | 41.30 | 20.40 | 2.025 | 83.63 | 61.11 |
1.368 |
| B1/H40/Hkv40/S32768 | 128 | 42.24 | 21.16 | 1.996 | 85.30 | 61.89 |
1.378 |
| B1/H40/Hkv40/S32768 | 256 | 41.39 | 21.04 | 1.968 | 84.94 | 61.69 |
1.377 |
| B2/H24/Hkv24/S16384 | 32 | 40.86 | 20.18 | 2.024 | 82.83 | 60.48 |
1.370 |
| B1/H2/Hkv2/S4096 | 6 | 41.61 | 20.13 | 2.067 | 73.88 | 51.89 | 1.424 |
| B1/H2/Hkv2/S4096 | 58 | 41.67 | 20.66 | 2.017 | 73.64 | 51.84 | 1.420
|
| B1/H4/Hkv4/S4096 | 6 | 41.34 | 20.17 | 2.049 | 72.92 | 51.83 | 1.407 |
| B1/H4/Hkv4/S4096 | 58 | 41.34 | 20.28 | 2.038 | 72.83 | 51.82 | 1.406
|
| B1/H32/Hkv8/S4096 | 6 | 41.04 | 20.22 | 2.029 | 74.43 | 52.97 | 1.405
|

The other Cake variants keep their coverage: the pre-quantized and
combined forms ship on sm_100a and sm_103a, and the INT8-QK/FP8-PV
variant ships on sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved attention routing across supported GPU workloads, including
combined quantization-and-attention calls and selected split-grid
configurations.
* Improved current-stream handling and CUDA Graph capture across
attention, dispatch, and quantization calls.
* Strengthened input validation and output allocation, with clearer
errors for invalid tensor types and layouts.
* **Compatibility**
* Attention query, key, and value inputs must use float8 E4M3FN;
unsigned and signed 8-bit integer substitutes are rejected.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [928cf4e](https://github.com/flashinfer-ai/flashinfer/commit/928cf4ebde597b7303fd952b614d3d3339178aad)

- **作者**: eigen
- **时间**: 2026-11-24T16:19:47Z
- **提交信息**: fix(cake_gdp): do not serve a prefill item table first filled in a CUDA graph to eager calls (#9974)

## What was wrong

On SM100 / SM103 the Cake GDP prefill (`chunk_gated_delta_product(...,
backend="cake")`) keeps its device item table in a cache keyed by the
batch's offsets. If the first call of a batch was a CUDA graph capture,
the table was allocated in the graph's memory pool and filled by a copy
node inside that graph. That table was still placed in the cache that
later calls read. An eager call of the same batch made after the capture
but before the first replay then read an unfilled buffer and returned
wrong values: a relative error of 1.0 and some non-finite outputs. After
one replay, the results were correct.

The usual path (an eager warm-up call of the batch, then the capture)
was not affected.

## Fix

`_item_table` keeps a table first created during capture alive for its
graph only, together with its pinned host source. It does not serve that
table to other calls. A later eager call or capture of the same batch
uploads its own complete copy. A complete eager table reused by a
capture is still kept and served as before.

The SM90 tests in `tests/gdp/test_cake_gdp_prefill.py` also fail on H100
since the Blackwell prefill records were added to the shared registry.
Two tests iterated over those records too. They now check only the SM90
records and the SM90 logical names (test-only change, separate commit).

## Tests

New regression test
`test_an_eager_call_after_a_cold_capture_of_its_batch` in
`tests/gdp/test_cake_gdp_prefill_bw.py`. The first call of a split batch
is a capture (the program is loaded by a different batch first). An
eager call before any replay must match cuDNN. The replay and a later
eager call must equal that result bitwise.

| GPU | regression test before the fix | after the fix | GDP prefill
tests after the fix |
| --- | --- | --- | --- |
| GB300 (sm_103a) | 2 failed (non-finite eager output) | 2 passed | 76
passed, 140 skipped |
| B200 (sm_100a) | 2 failed (non-finite eager output) | 2 passed | 76
passed, 140 skipped |
| H100 (sm_90a) | skipped (Blackwell only) | skipped | 175 passed, 41
skipped (before: 2 failed, 173 passed) |

GDP prefill tests: `tests/gdp/test_cake_gdp_prefill_bw.py`,
`test_cake_gdp_prefill_api.py`, `test_cake_gdp_prefill_route.py`,
`test_cake_gdp_prefill.py`. Skips are tests for the other architecture.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved result consistency when Cake prefill is first used during
CUDA graph capture, including across subsequent eager calls and graph
replays for split batches.
* **Tests**
* Expanded prefill validation across supported architectures and added
coverage for CUDA graph capture with multiple batch configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [ba93351](https://github.com/flashinfer-ai/flashinfer/commit/ba933516c6730a2aca0e62ba918195dce2e3cfac)

- **作者**: Alex Ameen
- **时间**: 2026-11-24T16:01:14Z
- **提交信息**: ci(deep_gemm): keep DeepGEMM JIT error messages instead of exiting the process (#9468)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR keeps native DeepGEMM JIT error messages so they reach the test
report and the CI job trace. It does not change kernel behavior and does
not fix any particular test failure.

**Why:** DeepGEMM's `CHECK_CUDA` and `CHECK_NVRTC` macros called
`exit(1)` when a CUDA driver or NVRTC call failed. That ends the Python
process before pytest writes its JUnit XML. The error message goes only
to the per-batch log, and the sharding runner can report only that the
XML is missing. H100/cu129 nightlies from 10/22 to 10/25 showed this,
`cause=pytest did not produce JUnit XML`, for batches in three files
that use the SM90 DeepGEMM JIT:

- `tests/gemm/test_fp8_blockscale_gemm.py`
- `tests/moe/test_unified_moe_cutlass.py`
- `tests/moe/test_unified_moe_fuzz.py`

We don't know what actually failed in those runs, and this PR doesn't
try to find out. It makes sure that when something like this happens,
the actual error is kept and reported.

**Changes:**

- **`deep_gemm/jit_utils.cuh`:** `CHECK_CUDA` and `CHECK_NVRTC` throw
`std::runtime_error` instead of calling `exit(1)`. The message gives the
error text, the failing call, and the file and line. TVM-FFI turns it
into a Python `RuntimeError` on the test that hit it, so pytest finishes
and records the error in the JUnit XML.
- **`deep_gemm/compiler.cuh`:** checks nvcc's exit status and that the
kernel file exists. nvcc's error output is captured and included in the
error message. Before this, a failed compile only showed up later, when
loading the missing kernel file failed.
- **`deep_gemm/runtime.cuh`:** loading a missing or empty kernel file
raises an error that names the path. `~Runtime` no longer throws.
- **`scripts/infra/test_sharding/workers.py`:**
- When a pytest batch exits without writing JUnit XML, the message gives
the exit code and the full ID of the last test that started. That is
kept after the test finishes, so a pytest that exits during teardown,
after its last test reported, still names it. The timeout message still
names the test that was running.
- The runner prints the last 40 lines of the batch log into the job
trace, so the error is visible even when the batch log artifact isn't
kept. It also prints the log tail when pytest exits with an
infrastructure error code, and when reading pytest's output fails (it
prints what is already in the log without waiting for more).
- The batch log is appended to across executions of the same batch. The
tail starts no earlier than where this execution's output begins, so it
cannot show output from an earlier run. It reads at most 16 KB.
- Batches with no XML are still reported as infrastructure failures,
never as passing.
- Batch pytest runs with `--capture=tee-sys` and `PYTHONUNBUFFERED=1`
(unless already set). pytest's default capture holds a test's output
until the test reports, so a test that ends the process lost the error
it printed, and the log tail showed only pytest's header. With
`tee-sys`, Python output goes to the batch log as it is printed and is
still attached to failure reports. `PYTHONUNBUFFERED` keeps `os._exit()`
and a native `exit()` from dropping buffered stdout. Trade-off: output
that native code writes straight to the file descriptors now appears
inline in the batch log instead of the report's "Captured ..." sections.
Neither was in the JUnit XML, since `junit_logging` is not set.
- **`tests/infra/test_sharding/test_workers.py`:** regression tests with
a fake pytest:
- It prints an error and exits with code 1 without writing XML. The
batch is reported as an infrastructure failure with the exit code and
last test, no XML is promoted, and the log tail containing the error
appears on the console.
- It exits after its only test finished; the message still names that
test.
- Its log already holds output from an earlier execution; the tail shows
only this execution's output, and the earlier output stays in the file.
- Its output fails to parse; the reader-failure message is kept and the
log tail is printed.
- A unit test checks that finishing a test clears the running test but
keeps the last-started one.

Two tests run real pytest, since the fake pytest above prints directly
and cannot show capture behavior:

- A test prints to stdout, stderr and file descriptor 2, then calls
`os._exit(1)`. All three lines appear in the console log tail. This
fails without the capture change, and also with `tee-sys` alone, without
`PYTHONUNBUFFERED`.
- A failing test's output still appears under "Captured stdout call" in
its report.

## 🔍 Related Issues

Motivating report: GitLab `dl/flashinfer/flashinfer-ci` scheduled
unit-test nightlies from 10/22 to 10/25. Example jobs: 502615440,
502615451, 508255535, 508255548.
Audit marker:
`flashinfer-gitlab-nightly-20261022-20261025-pytest-missing-junit-v1`

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. All hooks passed with no changes; the
broken-symlink check had no files to check.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Targeted H100 run (cu129, before the rebase, when the tests were still
under `tests/test_sharding`) for `tests/gemm/test_fp8_blockscale_gemm.py
tests/moe/test_unified_moe_cutlass.py tests/moe/test_unified_moe_fuzz.py
tests/test_sharding`: 1,074 tests, 811 passed, 0 failed, 263 skipped.
Every batch wrote JUnit XML. The DeepGEMM path compiles and passes on
H100 with the new error handling. This run did not hit a DeepGEMM error,
so the new error path was exercised by the regression test, not by a
real GPU failure.

Rebased onto `main` (25bc267eb), which moved the sharding runner and its
tests to `scripts/infra/` and `tests/infra/` (#8993). Locally,
`tests/infra/test_sharding/test_workers.py` passes on this branch (18
passed; the four tests added for the review fixes fail against the
previous `workers.py`, and the real-pytest exit test fails without the
capture change) and pre-commit passes on the changed files.
`tests/infra/test_sharding/test_test_path_scope.py::test_sm107_runner_selects_supported_lanes`
currently fails on `main`; that is unrelated to this PR and left to the
test's owners, so a CI scope that includes all of
`tests/infra/test_sharding` will show those failures until it is fixed.
The H100 results above are from before this rebase.

Demo in CI (draft #9724, do not merge): this branch plus a CPU test that
prints a fake CUDA error and calls `os._exit(1)`.

- [Before the capture
change](https://github.com/flashinfer-ai/flashinfer/actions/runs/44552016993/job/135658408079):
the batch was reported with the exit code and test name, but the log
tail ended at pytest's header, without the error.
-
[After](https://github.com/flashinfer-ai/flashinfer/actions/runs/44778877817/job/136436289928):
the tail shows both the stdout and stderr lines the test printed before
exiting. The other 11,417 `tests/cpu` tests passed, and the 3 demo tests
stayed pending rather than passing. The targeted H100 lane ran
`tests/infra/test_sharding/test_workers.py`: 18 of 18 passed.

Locally (no GPU), the changed DeepGEMM headers compile on the host side
with clang `-Wall`. A small program that triggers both macros gets an
exception with the expected message instead of `exit(1)`.

Suggested CI test targets: `tests/gemm/test_fp8_blockscale_gemm.py
tests/moe/test_unified_moe_cutlass.py tests/moe/test_unified_moe_fuzz.py
tests/infra/test_sharding/test_workers.py`

---------

Co-authored-by: Alex Ameen <aameen@nvidia.com>

### [998f841](https://github.com/flashinfer-ai/flashinfer/commit/998f841964c2904993f19bb667228933d42d607e)

- **作者**: Lee Nau
- **时间**: 2026-11-24T13:08:54Z
- **提交信息**: feat(gemm): retune MXFP8 CuTe-DSL entries when the tactic budget changes (#9892)

<!-- .github/pull_request_template.md -->

## 📌 Description

`FLASHINFER_MM_MXFP8_CUTE_DSL_MAX_TACTICS` (#6615) trims the tactic list
of `CuteDSLMxfp8GemmRunner`. It keeps every eligible split-K tactic plus
the top-ranked persistent tactics. The budget is not part of the
runner's cache identity. So a winner tuned under a budget was reused
after the budget changed, including after returning to the full search
(`0`), and the tactics the budget had dropped were never compared.

This PR adopts the tactic-pool signature hook from #9289 for this
runner:

- `CuteDSLMxfp8GemmRunner.get_tactic_cache_key()` returns
`("max_tactics", budget)`.
- The default `0` is reported too. When a call has a single runner that
returns `None`, the autotuner skips the coverage check, so returning to
`0` would silently reuse the budgeted winner.
- That case is real here: SM100/SM103 `mm_mxfp8(backend="cute-dsl")`
uses this runner alone when the warp split-K runner is unavailable or
doesn't support the shape.
- The hook and `_rank_tactics` parse the variable through one helper,
`_mm_mxfp8_cute_dsl_max_tactics()`, so they can't disagree. A negative
value still raises.
- This covers every instance of the class: SM100 and SM103, and the
SM107 `low_m_only` runner (M ≤ 32), which also applies the budget.

**Behaviour for existing caches.** Entries tuned before this change have
no coverage record for this signature. Serving from them, including
inside CUDA Graph capture, is unchanged, because the signature is only
checked while tuning. The first `autotune(True)` call after upgrading
retunes them once. This is the same treatment #9289 gives any cache
entry written before that hook existed.

`docs/design_docs/cute_dsl_kernel_cache.md` is updated to describe this.
That page also said "SM107/SM12x paths are outside this change" about
the budget, which was stale: the SM107 `low_m_only` runner applies it.
As suggested in review, it now says only the warp split-K runner and
SM12x paths are outside.

## 🔍 Related Issues

Closes #9789, the production adopter of the #9289 hook, requested in
that PR's approving review. The SM120 FP4 stream-K switch
(`FLASHINFER_FP4_GEMM_DISABLE_STREAM_K`) is the other runner that reads
its pool from the environment at enumeration time. It is not changed
here.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks pass on the three changed files (`pre-commit run --files
...`); the full repository was not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: the change is one runner's cache signature; targeted MXFP8 and
autotuner tests cover it.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/gemm/test_mxfp8_precompile.py
tests/cpu/autotuner tests/autotuner tests/gemm/test_mm_mxfp8.py`

"All tests are passing" stays unchecked until upstream CI has run.

**New tests** (`tests/cpu/gemm/test_mxfp8_precompile.py`, which skips
without `nvidia-cutlass-dsl`):
-
`test_runner_tactic_pool_signature_follows_budget[0-False|3-False|7-True]`:
on the SM100, SM103 and SM107 `low_m_only` runners, the signature is
`("max_tactics", 0)` when the variable is unset or `0` and
`("max_tactics", 32)` for `32`, and `-1` raises.
- `test_budget_change_retunes_through_autotuner`: the real runner and
`AutoTuner.choose_one()` with controlled timings, as a single runner, at
an M above the split-K limit.
  - Under budget 2, only the two budgeted tactics are profiled.
- Back at `0`, the full pool is profiled, and the fastest tactic (one
the budget dropped) wins.
  - A third call with an unchanged budget profiles nothing.

**Validation on SM107** (Hecate, `NVIDIA VR NVL72`). The setup:
- Nightly `0.7.5.dev20261120` wheels (`0cf9d70d8`) in a container with
torch `2.15.0.dev20260818+cu134` and `nvidia-cutlass-dsl` 4.8.0.
- Overlaid with `flashinfer/autotuner/autotuner.py` and
`flashinfer/tactics_blocklist.py` from `main` (`3424a3a11`). Since the
nightly, those files changed only through #8768, #9289 and #9790.
- The "PR" step also overlays this branch's `gemm_base.py`, which
differs from the nightly's by exactly this change. Each step runs in a
fresh container, with overlay checksums recorded. The validated commit
is `eaa3cb6e6`. Since then the branch has only gained a reworded commit
message, a merge of `main`, and the one-sentence design-doc fix above,
so the tested code is unchanged.

CPU tests (`test_mxfp8_precompile.py`,
`test_autotuner_tactic_coverage.py`):

| | passed | failed |
|---|---|---|
| `main` | 45 | 4: the four new cases (negative control) |
| this PR | 49 | 0 |

An earlier revision returned `None` at budget `0`. On that revision,
`test_budget_change_retunes_through_autotuner` failed in exactly the
single-runner way described above, which is why `0` is now reported.

End-to-end qualification on SM107: `mm_mxfp8(backend="cute-dsl")` at M =
16 and M = 32 with real kernels, the real profiler and the real cache.
- **Phases.** Probe the full pool, tune with budget 3, tune again at 0,
a warm tune, eager serving, then CUDA Graph capture and replay.
- **Across processes.** Seed a v1 JSON cache with budget 3, then
`load_configs` and tune at 0 in a new process.

| shape (M×N×K) | low-M pool | dropped by budget 3 | dropped tactics
profiled after returning to 0: `main` / PR | after reload at 0, low-M
tactics profiled: `main` / PR |
|---|---|---|---|---|
| 16×5120×8192 | 16 | 10 | 0 / 10 | 0 / 16 |
| 32×1792×5120 | 15 | 6 | 0 / 6 | 0 / 15 |

On both branches:
- Warm tuning, eager serving and CUDA Graph capture profiled nothing.
- Serving never called `get_tactic_cache_key()`. In this PR, the warm
tune called it once, before the cache hit.
- Graph replay output equalled eager output exactly.
- Every output's cosine similarity against a BF16 matmul of the
unquantized operands was ≥ 0.9992.

This is a cache-correctness change. No kernel, ranking or performance
change is claimed. The budget itself remains opt-in.

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

- **Why not `None` at the default.** `None` was tried first, to keep
existing entries' identity. But `_ProfilingCandidates.from_runners()`
returns no coverage at all for a lone runner with a `None` signature, so
the budgeted → `0` transition was missed on the single-runner
SM100/SM103 path. On SM107 it was caught only because `mm_mxfp8` passes
several runners there. Reporting `0` costs one retune of pre-existing
entries when tuning is next enabled.
- **Cost.** The hook reads one environment variable. It is called only
on the tuning path: once per `choose_one()` before enumeration, and
never while serving.

AI-assisted: drafted and validated with Claude Code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* MXFP8 tuning results are refreshed when the tactic budget changes or
cached entries predate budget reporting. Negative budget values produce
a validation error; zero leaves tactics untrimmed, and unchanged budgets
reuse the selected winner without profiling again.
* **Documentation**
* Startup guidance now explains that positive budgets apply analytical
ranking to persistent tactics while retaining eligible split-K tactics.
The budget must allow room for those tactics and at least one persistent
candidate. The documented scope includes the SM107 low-M runner for M ≤
32.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bdb7fc8](https://github.com/flashinfer-ai/flashinfer/commit/bdb7fc83825b70e2cfda46a9a63974f9077f7705)

- **作者**: eigen
- **时间**: 2026-11-24T09:53:58Z
- **提交信息**: perf(cake_batch_deepgemm_fp8): masked pair program for homed weights from expected_m 128 on sm_107a (#9885)

The batch DeepGEMM FP8 Cake family has three serving programs for
packed-UE8M0 weights on 212-SM sm_107a. The first is the whole-GPU M32
serving program. The second is its locality-domain twin, used for
weights homed by `localize_weights`. The third is the masked pair
program for large expected_m. This PR routes homed weights to the pair
program from expected_m 128 instead of 160. The baseline is the previous
Cake route for homed weights, which is the twin.

NVIDIA VR200 (sm_107a, 212 SMs, dies 106/106), driver 620.70.06, memory
at 4752 MHz, CUDA 13.5. B=64 homed weights of (N, K) = (4096, 7168).
CUPTI device time, CUDA graph replay, cold L2; medians over 6 rounds;
speedup = previous time / new time (per-round range). Uneven rows draw
each group's count as int(em x U(0.7, 1.3)).

| mask | expected_m | M | previous Cake (twin) us | this PR (pair) us |
speedup |
|---|---:|---:|---:|---:|---|
| even | 128 | 128 | 274.2 | 247.1 | 1.110 (1.108-1.111) |
| even | 144 | 256 | 334.2 | 256.0 | 1.306 (1.304-1.307) |
| even | 159 | 256 | 335.2 | 256.5 | 1.307 (1.305-1.308) |
| uneven | 128 | 256 | 299.3 | 250.4 | 1.195 (1.194-1.196) |
| uneven | 144 | 256 | 331.5 | 253.2 | 1.309 (1.307-1.311) |
| uneven | 159 | 256 | 371.6 | 255.6 | 1.454 (1.450-1.458) |

The family also ships whole-GPU serving programs on sm_100a, sm_103a and
sm_107a. The twins and the pair program are sm_107a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Updated the batch DeepGEMM FP8 routing threshold for 212-SM
configurations, changing when requests use homed weights versus the
serving route.
* **Documentation**
* Expanded Cake locality performance comparisons across memory layouts,
clock rates, and workloads.
* Clarified routing behavior for different expected batch sizes and
memory-clock conditions.
* **Tests**
* Added coverage validating locality-domain reporting and
remote-to-local memory latency on supported hardware.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [4d5a6ce](https://github.com/flashinfer-ai/flashinfer/commit/4d5a6ce322587d247fb192f97a0d23eeba9e3412)

- **作者**: xiufanl
- **时间**: 2026-11-24T05:25:17Z
- **提交信息**: Sync upstream SM120 scalar MMA compatibility fix (#9651)

<!-- .github/pull_request_template.md -->

## 📌 Description

Sync the vendored SM120 scalar-scale MMA helper with the upstream split
kernel's compatibility fix. The helper now emits the native block-scaled
instruction directly, avoiding a removed CuTeDSL operation. This updates
the scalar helper and records the partial sync in the vendor notes. Both
scalar helpers encode byte selector zero directly in the PTX because
each E8M0 scale occupies the low byte of its register. They retain
independent thread selectors and tied FP32 accumulators. The
packed-scale path still selects a byte from the scale word. Both split
paths and the SwapAB helper mark the warp-collective MMA as
side-effecting, following the BF16 CuTeDSL MMA and the volatile SM120
C++ MMA wrappers. A lane can contribute operands even when it does not
consume its own accumulator.

The SM120 MXFP8 SwapAB counterpart now uses the same native scalar MMA
approach with byte-zero scale selection. Its vendor notes track the
local change pending a future upstream sync.

AI assistance was used to prepare the sync and compilation checks.

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/moe_ep/test_moe_ep_sm120_w4a8_cutedsl_mega.py
tests/moe_ep/test_moe_ep_sm120_mxfp8_cutedsl_mega_multirank.py`

Ten SM120a compile cases with ordinary result use produced the same
native instructions before and after the side-effect annotation. In
three cases where only even lanes consumed the result, both revisions
issued an unpredicated MMA before divergence. When the result was unused
by every lane, the new annotation retained the MMA in PTX; the final
assembler could still remove that dead instruction. GPU execution at
this PR revision is pending.

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved compatibility for SM120 block-scaled matrix operations with
CuTeDSL versions that no longer provide the previous MMA operation.
* Added validation for supported accumulator and scale types in affected
MXFP8 and MXFP4/MXFP8 operations.
* Improved handling of scalar scales in these operations to ensure
warp-collective matrix operations are correctly recognized.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: xiufanl <186788561+xiufanl@users.noreply.github.com>
Co-authored-by: Haobin Guo <haobing@nvidia.com>

### [2561ebe](https://github.com/flashinfer-ai/flashinfer/commit/2561ebe1398229b67fe42ed00307fba7db4624f0)

- **作者**: Perkz Zheng
- **时间**: 2026-11-24T05:06:21Z
- **提交信息**: perf(prims-ts): QToken NVFP4 prefill: gather4 scale copies, per-layout group policy and balanced CLC scheduling (#9876)

<!-- .github/pull_request_template.md -->

## 📌 Description

Changes for NVFP4 QToken-KvBlock-Sparse-Attention prefill with grouped
routes (GB300, D256, block 4, top-k 512), one commit each:

1. **Gather4 NVFP4 scale copies and causal route unions.** With separate
compact scale tensors, the Keeps raw ring gathers four page fragments'
scale rows per TMA gather4 (8 instead of 32 scale copies per KV128
tile). The G latency model caps each route's expected union at the
context its last query sees, so causal prefill from a short prefix no
longer overestimates large groups (16/1 Q/KV heads, 4096 queries, empty
prefix: G4 177 us -> G8 138 us).
2. **Per-layout G latency model.** The union-growth exponent is now the
measured 0.48 (was 0.35, which overcharged TileQ128 at G2/G4 and picked
groups up to 1.26x slower for 32 and 64 Q heads per KV head). Work items
cost per TileQ and SM waves are fractional.
`suggest_q_token_kv_block_sparse_group_size(nvfp4_interleaved_kv=...)`
selects constants fitted per NVFP4 layout (interleaved rows make TileQ64
~7% slower than separate scales). Over 1848 swept cases the chosen group
is within 1.002x (separate scales) and 1.004x (interleaved rows) of the
best, vs 1.008x / 1.017x before.
3. **Balanced CLC scheduling.** Persistent launches handed out routes in
index order; route cost follows its K/V union, which varies 1.3-1.9x
within one call, so long routes often started last (SMs busy 71% of the
kernel in an all-CTA trace). The metadata kernel's last CTA now
counting-sorts routes by KV128 tiles in shared memory and the CLC work
queue takes them in that order. When the requests' K/V fits in half of
L2 every route is ordered longest first; otherwise only the shortest two
SM waves move to the end and the rest keep index order (L2 reuse). New
plan option
`QTokenKvBlockSparsePagedTSWrapper.plan(balanced_scheduler=None)`:
`None` enables it for persistent launches whose routes exceed one SM
wave, `True` for every persistent launch, `False` keeps index order.
Cost: ~0.9 us in the metadata kernel; attention starts at the same time
under PDL.
4. **Interleaved-rows group constants refit under the balanced
scheduler.** Fewer, larger TileQ128 work items lose less to the last
wave with balanced scheduling, so with interleaved rows G8 now beats G4
for 16 Q heads per KV head over long contexts (16/1, 4096 queries over
32K: 348 -> 311 us; 16/1 x 4 requests x 1024 queries: 1.15x). Refit on
the same sweeps with every multi-wave case re-measured on this branch;
separate-scale constants unchanged.
5. **Balanced scheduler auto rule skips short routes.** Routes that can
read at most two KV128 tiles (`max_seq_len_kv <= 256`) leave nothing to
balance while the order costs ~1-2 us; the default now leaves them in
index order.
6. **Review fixes.** These cover the CodeRabbit and reviewer comments.
- The work queue never reads the route order at the undefined index of a
failed CLC cancel: invalid tiles read entry 0, with no branch.
   - The L2 estimate counts separate NVFP4 scale tensors.
- Bitmap metadata launches stay within the per-CTA shared-memory limit.
   - The completion counter must be a nonempty 1-D tensor.
   - Only persistent launches reserve the route-order workspace region.
   - Gather4 scale launches skip the two unused 4-D scale-map encodes.
   - The longest bucket (127+ KV128 tiles) is documented.
- The scheduler test uses full indexer prefixes and poisons the order
before repeated runs.

This commit measured 1.000x geomean vs commit 5 on the full table below
for both layouts.
7. **Route-order workspace only for shared patterns.** Per-head sparse
patterns (even with one KV head) never take the route order, so they no
longer reserve its workspace region; shared-pattern layouts are
unchanged.
8. **Balanced scheduler auto rule by SM waves.** Commit 5's cut-off
(routes of more than two KV128 tiles) also dropped two-tile routes over
several SM waves, where the order pays: 16/1 Q/KV heads with 16 or 64
requests x 256 queries from an empty prefix now run 1.08-1.10x faster
than main (64 requests with separate scales was 0.987x). Short routes
over fewer waves lose to the order's cost instead. The default now
enables it when routes span more than one wave and can read more than
one KV128 tile; routes of up to four tiles (`max_seq_len_kv <= 512`)
also need three or more waves.

GB300, real indexer top-k, auto G, A/B/A/B on one GPU per shape, both
NVFP4 layouts (main/branch time, geomean (max)):

| Q/KV heads (top-k corpus) | cases | separate scales | interleaved rows
|

|---------------------------|------:|-----------------|------------------|
| 4/1 (book)                | 39 | 1.026x (1.16x) | 1.003x (1.08x) |
| 16/1 (book)               | 39 | 1.042x (1.40x) | 1.021x (1.48x) |
| 16/1 (code)               | 39 | 1.046x (1.44x) | 1.025x (1.50x) |
| 16/2 (book)               | 39 | 1.039x (1.24x) | 1.013x (1.20x) |
| 32/1 (book)               | 27 | 1.082x (1.45x) | 1.073x (1.52x) |
| 32/2 (book)               | 27 | 1.063x (1.17x) | 1.034x (1.18x) |
| 64/2 (book)               | 27 | 1.064x (1.44x) | 1.059x (1.49x) |
| 64/4 (book)               | 27 | 1.075x (1.45x) | 1.051x (1.50x) |
| 128/8 (book)              | 27 | 1.060x (1.17x) | 1.022x (1.08x) |
| 16/1, 4-64 requests (book)| 69 | 1.053x (1.22x) | 1.031x (1.19x) |
| all | 360 | **1.052x** (1.45x) | **1.030x** (1.52x) |

One request unless noted; 0/32K/64K-token prefixes, 1-4096 queries
(batches: 0/32K prefix, 1-1024 queries per request); split-KV auto; base
is main at a7ed35743, with all eight commits rebased onto it.

Cases flagged in this table (the branch's best run more than 1% slower
than main's worst) were re-timed in three rotated rounds of 30 replays.
All are within noise (0.995-1.007x) except the accepted 128/8 cases and
two small separate-scale launches listed under Reviewer Notes.

## 🔍 Related Issues

Follow-up to #9375.

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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/attention/test_attention_ts_q_token_kv_block_sparse_metadata.py
tests/attention/test_attention_ts_decode.py
tests/attention/test_attention_ts_decode_mixed_precision.py`

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

- Pre-commit itself was not run (it does not run on our build host). Ran
instead: `ruff check` / `ruff format --check` on the changed Python
files, `clang-format` (repo `.clang-format`) on the changed C++/CUDA
files, and `git diff --check`.
- Tests: `test_attention_ts_q_token_kv_block_sparse_metadata.py`,
`test_attention_ts_decode.py` and
`test_attention_ts_decode_mixed_precision.py` pass on GB300 (SM103),
CuTe DSL 4.8.1, CUDA 13.4, on this branch rebased onto main a7ed35743.
- `balanced_scheduler` adds an int32 [routes] region after `seq_lens` in
the workspace of packed grouped persistent plans with shared sparse
patterns, and the plan owns a one-int32 completion counter (zeroed at
plan time, rearmed by the metadata kernel), so a workspace shared
between plans cannot disturb it.
- Known small losses vs main, accepted: with interleaved rows the refit
(commit 4) takes G8 for 128/8 Q/KV heads at 512 queries over 32K/64K
(0.988x / 0.979x). The group model sees them as identical to 16/1 cases
that gain up to 1.25x (same work items and union size), so no constants
separate them. Launches whose order costs more than it saves (one-tile
routes, or short routes over fewer than three SM waves) keep index order
with commit 8. With separate scales, two small launches are slower after
rebasing onto #9771: 64/2 Q/KV heads at 256 queries from an empty prefix
(22.0 -> 22.5 us, 0.978x; about 60% of it is the gather4 scale copies,
which are 1.02-1.10x faster from 512 tokens up) and a single query over
a one-token context (12.6 -> 12.8 us, 0.979x).
- Rebased onto main after #9771. Its stage-sliced D512 scale maps and
this PR's gather4 scale maps never apply to the same launch (scale
reshape factor 4 vs 1), so the launcher encodes one of the three map
kinds.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optional balanced scheduling for packed, grouped sparse
attention. Eligible plans can prioritize longer routes while retaining a
configurable tail of shorter routes; scheduling can also be explicitly
enabled or disabled.
* Updated sparse-group size recommendations to account for route context
and interleaved NVFP4 cache layouts.
* Added an optimized scale-loading path for eligible NVFP4
configurations.
* **Tests**
* Added coverage for route scheduling across repeated runs, sparse-group
recommendations, and NVFP4 layout options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [56e0bef](https://github.com/flashinfer-ai/flashinfer/commit/56e0befb07b47cb26048c368a2dad025f5dd1a8f)

- **作者**: eigen
- **时间**: 2026-11-24T04:35:07Z
- **提交信息**: feat(cake_gdp): add SM100a and SM103a prefill backend for chunk_gated_delta_product (#9917)

## Summary

Cake ships two prefill variants of `chunk_gated_delta_product`: an SM90
variant (`num_householder` 1 to 4, dense or `state_indices` slot-indexed
state) and, with this PR, a Blackwell (sm_100a / sm_103a) variant behind
`backend="cake"`. The Blackwell variant takes bf16 q/k/v with K = 128
and V = 64 and `num_householder = 3`, keeps a dense FP32 state of shape
`[N, H, 64, 128]` (V-major; a bf16 initial state is converted to FP32),
and returns bf16 output. Cake had no Blackwell prefill before this PR,
so the baseline is FlashInfer's existing `backend="cudnn"` (cuDNN
9.24.0) for the same call. Over the 88 workloads below, the
geometric-mean speedup over cuDNN is **1.73×** on B200 (min 1.04×) and
**1.70×** on GB300 (min 1.02×).

Cake also ships the gated delta product decode (`num_householder` 1 to
4); the family ships on sm_90a, sm_100a, sm_103a and sm_107a, with
prefill on sm_90a, sm_100a and sm_103a.

## Performance

NVIDIA B200 (sm_100a) and NVIDIA GB300 (sm_103a); PyTorch 2.14.1 with
the CUDA 13.0 runtime, CUDA 13.4 toolkit, cuDNN 9.24.0. Timing is
CUDA-graph replay with a warm L2. Latencies are medians in µs. Speedup
is the paired median of the cuDNN/Cake latency ratio. Gates follow
FlashInfer's test input generator, and every call stores the final
state. In A rows, `nx1+L` means n one-token sequences that start from an
initial state, followed by one sequence of L tokens that starts from a
zero state. B rows are one sequence that starts from an initial state. C
rows are two sequences (`a+b`); only the first starts from an initial
state.

| Workload | H | Sequence lengths | B200 cuDNN (µs) | B200 Cake (µs) |
B200 speedup | GB300 cuDNN (µs) | GB300 Cake (µs) | GB300 speedup |
|---|---:|---|---:|---:|---:|---:|---:|---:|
| A_H10_L8192_d0 | 10 | 8192 | 163.26 | 70.88 | 2.33 | 151.42 | 67.46 |
2.24 |
| A_H10_L8192_d1 | 10 | 1x1+8192 | 165.31 | 71.1 | 2.32 | 155.55 | 67.49
| 2.31 |
| A_H10_L8192_d4 | 10 | 4x1+8192 | 144.86 | 71.17 | 2.01 | 165.79 |
67.46 | 2.46 |
| A_H10_L8192_d8 | 10 | 8x1+8192 | 144.7 | 71.1 | 2.03 | 137.09 | 67.49
| 2.03 |
| A_H10_L8192_d15 | 10 | 15x1+8192 | 144.83 | 75.2 | 1.93 | 133.12 |
67.46 | 1.97 |
| A_H10_L16384_d0 | 10 | 16384 | 249.28 | 118.11 | 2.11 | 229.28 |
104.35 | 2.20 |
| A_H10_L16384_d1 | 10 | 1x1+16384 | 257.31 | 119.38 | 2.16 | 239.52 |
104.32 | 2.30 |
| A_H10_L16384_d4 | 10 | 4x1+16384 | 216.51 | 118.34 | 1.80 | 264.06 |
104.35 | 2.53 |
| A_H10_L16384_d8 | 10 | 8x1+16384 | 226.72 | 120.22 | 1.89 | 186.3 |
104.35 | 1.79 |
| A_H10_L16384_d15 | 10 | 15x1+16384 | 187.84 | 118.24 | 1.58 | 176.0 |
108.45 | 1.62 |
| A_H10_L32768_d0 | 10 | 32768 | 411.1 | 208.32 | 1.97 | 379.65 | 186.27
| 2.04 |
| A_H10_L32768_d1 | 10 | 1x1+32768 | 434.62 | 207.26 | 2.10 | 409.5 |
186.24 | 2.20 |
| A_H10_L32768_d4 | 10 | 4x1+32768 | 271.84 | 208.32 | 1.30 | 452.54 |
186.27 | 2.43 |
| A_H10_L32768_d8 | 10 | 8x1+32768 | 382.3 | 208.19 | 1.84 | 305.06 |
186.27 | 1.64 |
| A_H10_L32768_d15 | 10 | 15x1+32768 | 288.19 | 210.4 | 1.37 | 268.19 |
186.27 | 1.44 |
| A_H10_L65536_d0 | 10 | 65536 | 748.82 | 378.34 | 1.98 | 675.74 |
339.94 | 1.98 |
| A_H10_L65536_d1 | 10 | 1x1+65535 | 784.7 | 380.35 | 2.07 | 739.23 |
339.87 | 2.18 |
| A_H10_L65536_d4 | 10 | 4x1+65532 | 666.08 | 382.96 | 1.75 | 835.46 |
341.86 | 2.44 |
| A_H10_L65536_d8 | 10 | 8x1+65528 | 698.82 | 384.3 | 1.83 | 536.48 |
340.9 | 1.57 |
| A_H10_L65536_d15 | 10 | 15x1+65521 | 500.16 | 381.31 | 1.31 | 626.56 |
341.86 | 1.83 |
| B_H10 | 10 | 65536 | 807.3 | 414.99 | 1.96 | 675.74 | 341.89 | 1.98 |
| C_H10 | 10 | 36864+28672 | 793.97 | 411.01 | 1.93 | 713.6 | 352.16 |
2.03 |
| A_H20_L8192_d0 | 20 | 8192 | 249.28 | 118.21 | 2.11 | 233.38 | 114.56
| 2.04 |
| A_H20_L8192_d1 | 20 | 1x1+8192 | 288.19 | 118.43 | 2.41 | 270.24 |
112.54 | 2.40 |
| A_H20_L8192_d4 | 20 | 4x1+8192 | 212.38 | 120.26 | 1.77 | 249.76 |
112.54 | 2.22 |
| A_H20_L8192_d8 | 20 | 8x1+8192 | 204.19 | 120.16 | 1.70 | 165.79 |
113.86 | 1.46 |
| A_H20_L8192_d15 | 20 | 15x1+8192 | 208.32 | 126.4 | 1.65 | 189.06 |
112.54 | 1.68 |
| A_H20_L16384_d0 | 20 | 16384 | 411.04 | 203.2 | 2.03 | 388.99 | 197.22
| 1.97 |
| A_H20_L16384_d1 | 20 | 1x1+16384 | 507.33 | 204.22 | 2.48 | 477.82 |
196.54 | 2.43 |
| A_H20_L16384_d4 | 20 | 4x1+16384 | 1224.1 | 204.26 | 5.99 | 434.82 |
197.78 | 2.20 |
| A_H20_L16384_d8 | 20 | 8x1+16384 | 355.74 | 206.22 | 1.73 | 281.22 |
196.51 | 1.43 |
| A_H20_L16384_d15 | 20 | 15x1+16384 | 357.86 | 204.29 | 1.74 | 327.58 |
202.66 | 1.62 |
| A_H20_L32768_d0 | 20 | 32768 | 741.17 | 374.21 | 1.98 | 699.36 |
360.35 | 1.94 |
| A_H20_L32768_d1 | 20 | 1x1+32768 | 938.43 | 376.1 | 2.51 | 881.57 |
360.35 | 2.45 |
| A_H20_L32768_d4 | 20 | 4x1+32768 | 563.68 | 375.54 | 1.51 | 808.9 |
360.35 | 2.24 |
| A_H20_L32768_d8 | 20 | 8x1+32768 | 660.93 | 374.3 | 1.77 | 502.4 |
360.35 | 1.39 |
| A_H20_L32768_d15 | 20 | 15x1+32768 | 661.95 | 376.26 | 1.76 | 595.87 |
360.34 | 1.65 |
| A_H20_L65536_d0 | 20 | 65536 | 1434.35 | 716.16 | 2.02 | 1318.78 |
669.54 | 1.97 |
| A_H20_L65536_d1 | 20 | 1x1+65535 | 1870.22 | 709.04 | 2.62 | 1693.54 |
669.6 | 2.53 |
| A_H20_L65536_d4 | 20 | 4x1+65532 | 1045.95 | 724.94 | 1.44 | 1554.05 |
669.6 | 2.32 |
| A_H20_L65536_d8 | 20 | 8x1+65528 | 1198.94 | 727.47 | 1.64 | 952.22 |
668.58 | 1.42 |
| A_H20_L65536_d15 | 20 | 15x1+65521 | 1315.25 | 733.63 | 1.80 | 1141.66
| 669.34 | 1.71 |
| B_H20 | 20 | 65536 | 1605.98 | 803.6 | 2.01 | 1319.81 | 669.6 | 1.97 |
| C_H20 | 20 | 36864+28672 | 1808.78 | 787.31 | 2.31 | 1604.48 | 689.07
| 2.33 |
| A_H40_L8192_d0 | 40 | 8192 | 440.75 | 224.74 | 1.96 | 415.65 | 214.94
| 1.93 |
| A_H40_L8192_d1 | 40 | 1x1+8192 | 245.18 | 224.7 | 1.09 | 228.62 |
214.94 | 1.06 |
| A_H40_L8192_d4 | 40 | 4x1+8192 | 634.3 | 226.66 | 2.80 | 241.57 |
214.91 | 1.12 |
| A_H40_L8192_d8 | 40 | 8x1+8192 | 351.65 | 226.59 | 1.55 | 321.44 |
214.94 | 1.50 |
| A_H40_L8192_d15 | 40 | 15x1+8192 | 366.02 | 232.8 | 1.58 | 335.94 |
214.94 | 1.57 |
| A_H40_L16384_d0 | 40 | 16384 | 818.54 | 359.87 | 2.28 | 768.93 |
341.86 | 2.25 |
| A_H40_L16384_d1 | 40 | 1x1+16384 | 423.36 | 358.85 | 1.18 | 393.06 |
342.91 | 1.15 |
| A_H40_L16384_d4 | 40 | 4x1+16384 | 546.21 | 365.98 | 1.49 | 429.98 |
344.0 | 1.25 |
| A_H40_L16384_d8 | 40 | 8x1+16384 | 660.96 | 376.38 | 1.76 | 594.85 |
350.16 | 1.70 |
| A_H40_L16384_d15 | 40 | 15x1+16384 | 677.18 | 390.59 | 1.74 | 610.24 |
366.53 | 1.66 |
| A_H40_L32768_d0 | 40 | 32768 | 1597.65 | 704.93 | 2.26 | 1467.3 |
653.22 | 2.24 |
| A_H40_L32768_d1 | 40 | 1x1+32768 | 763.33 | 708.0 | 1.09 | 699.3 |
652.19 | 1.07 |
| A_H40_L32768_d4 | 40 | 4x1+32768 | 1009.66 | 714.46 | 1.41 | 819.01 |
655.23 | 1.25 |
| A_H40_L32768_d8 | 40 | 8x1+32768 | 1303.47 | 729.49 | 1.79 | 1136.54 |
659.07 | 1.73 |
| A_H40_L32768_d15 | 40 | 15x1+32768 | 1318.74 | 739.71 | 1.77 | 1153.95
| 671.65 | 1.72 |
| A_H40_L65536_d0 | 40 | 65536 | 3162.03 | 1451.42 | 2.27 | 2870.18 |
1264.51 | 2.27 |
| A_H40_L65536_d1 | 40 | 1x1+65535 | 1568.43 | 1474.74 | 1.06 | 1320.83
| 1266.58 | 1.04 |
| A_H40_L65536_d4 | 40 | 4x1+65532 | 2009.47 | 1442.14 | 1.39 | 1584.03
| 1275.78 | 1.24 |
| A_H40_L65536_d8 | 40 | 8x1+65528 | 2577.81 | 1425.81 | 1.79 | 2229.15
| 1279.63 | 1.74 |
| A_H40_L65536_d15 | 40 | 15x1+65521 | 2547.55 | 1421.17 | 1.79 | 2243.5
| 1298.34 | 1.73 |
| B_H40 | 40 | 65536 | 3462.35 | 1526.51 | 2.28 | 2870.14 | 1265.54 |
2.27 |
| C_H40 | 40 | 36864+28672 | 1634.62 | 1526.51 | 1.07 | 1355.65 |
1278.72 | 1.06 |
| A_H80_L8192_d0 | 80 | 8192 | 434.48 | 359.81 | 1.21 | 402.3 | 337.82 |
1.19 |
| A_H80_L8192_d1 | 80 | 1x1+8192 | 470.5 | 362.93 | 1.30 | 434.05 |
339.94 | 1.27 |
| A_H80_L8192_d4 | 80 | 4x1+8192 | 646.59 | 373.18 | 1.73 | 589.73 |
350.11 | 1.68 |
| A_H80_L8192_d8 | 80 | 8x1+8192 | 657.7 | 389.6 | 1.69 | 599.97 |
369.28 | 1.62 |
| A_H80_L8192_d15 | 80 | 15x1+8192 | 681.41 | 421.33 | 1.62 | 621.47 |
401.25 | 1.55 |
| A_H80_L16384_d0 | 80 | 16384 | 781.76 | 693.71 | 1.13 | 720.98 |
649.07 | 1.11 |
| A_H80_L16384_d1 | 80 | 1x1+16384 | 822.64 | 693.55 | 1.19 | 757.63 |
649.09 | 1.17 |
| A_H80_L16384_d4 | 80 | 4x1+16384 | 1249.78 | 706.02 | 1.77 | 1134.53 |
659.33 | 1.72 |
| A_H80_L16384_d8 | 80 | 8x1+16384 | 1286.54 | 727.18 | 1.76 | 1148.8 |
675.82 | 1.70 |
| A_H80_L16384_d15 | 80 | 15x1+16384 | 1297.87 | 755.1 | 1.72 | 1171.33
| 705.36 | 1.66 |
| A_H80_L32768_d0 | 80 | 32768 | 1483.17 | 1393.06 | 1.07 | 1330.05 |
1258.43 | 1.06 |
| A_H80_L32768_d1 | 80 | 1x1+32768 | 1587.82 | 1393.06 | 1.14 | 1417.14
| 1262.5 | 1.12 |
| A_H80_L32768_d4 | 80 | 4x1+32768 | 2518.7 | 1396.64 | 1.79 | 2214.82 |
1270.75 | 1.74 |
| A_H80_L32768_d8 | 80 | 8x1+32768 | 2505.25 | 1407.39 | 1.78 | 2229.15
| 1288.03 | 1.73 |
| A_H80_L32768_d15 | 80 | 15x1+32768 | 2526.64 | 1434.08 | 1.76 |
2251.68 | 1318.85 | 1.71 |
| A_H80_L65536_d0 | 80 | 65536 | 3003.3 | 2896.32 | 1.04 | 2546.56 |
2486.88 | 1.02 |
| A_H80_L65536_d1 | 80 | 1x1+65535 | 3231.04 | 2981.09 | 1.10 | 2646.94
| 2489.25 | 1.06 |
| A_H80_L65536_d4 | 80 | 4x1+65532 | 5167.17 | 2734.51 | 1.86 | 4360.1 |
2505.02 | 1.74 |
| A_H80_L65536_d8 | 80 | 8x1+65528 | 5014.42 | 2741.46 | 1.84 | 4394.91
| 2516.9 | 1.75 |
| A_H80_L65536_d15 | 80 | 15x1+65521 | 5166.77 | 2802.58 | 1.83 |
4419.49 | 2544.54 | 1.74 |
| B_H80 | 80 | 65536 | 3163.46 | 3023.23 | 1.05 | 2546.56 | 2488.96 |
1.02 |
| C_H80 | 80 | 36864+28672 | 3263.78 | 3076.78 | 1.06 | 2642.85 | 2508.7
| 1.05 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added Cake GDP prefill support for SM100 and SM103 GPUs, including
batches with mixed sequence lengths and up to three Householder updates.
* Added graph-capture support for Blackwell prefill when sequence
offsets, sequence count, and total length match the captured values.
* **Limitations**
* Blackwell Cake prefill does not support state pools. Replaying a
captured graph with different sequence offsets produces NaNs in
designated output elements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [fabcf68](https://github.com/flashinfer-ai/flashinfer/commit/fabcf6898012d3ed4faf33a64f48c586c58efdb5)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-24T03:27:49Z
- **提交信息**: fix(moe_ep): validate Hopper blockwise FP8 tile K (#9816)

<!-- .github/pull_request_template.md -->

## 📌 Description

Hopper blockwise FP8×FP8 assumes K=128 when indexing FC2 scales. Require
that tile size in the config and tuner for native and swap-AB layouts.
Per-tensor and hybrid FP4 configurations still support K=256.

## 🔍 Related Issues

Follow-up to #9740.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files and fixed any reported
issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted checks passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: `tests/moe_ep/test_sm90_pull_fp8_tuner.py`.

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

### [0d47056](https://github.com/flashinfer-ai/flashinfer/commit/0d47056141422938f310069bb7ad002e2b0e93ff)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-24T03:27:08Z
- **提交信息**: docs(moe_ep): update layout and tuning references (#9818)

<!-- .github/pull_request_template.md -->

## 📌 Description

Update the runbook and source references for the MegaMoE layout. Label
the historical NVFP4 results with the kernel they measured and describe
the SM120 import conflict using the packages that actually collide.

## 🔍 Related Issues

Follow-up to #9740.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files and fixed any reported
issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted checks passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets:
`tests/cpu/infra/test_aot_cache_seed_workflow.py`.

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

### [6c4401d](https://github.com/flashinfer-ai/flashinfer/commit/6c4401dc7b6ba6288d9c81a418d8429ea2c56851)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-24T03:22:36Z
- **提交信息**: fix(moe_ep): accept byte-view NVFP4 scales on SM100 (#9815)

<!-- .github/pull_request_template.md -->

## 📌 Description

Reuse pretransformed SM100 NVFP4 weights whose E4M3 scales are stored in
`uint8` tensors. View the bytes as E4M3 at layer construction so the
existing validator and kernels receive the expected dtype.

## 🔍 Related Issues

Follow-up to #9740.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files and fixed any reported
issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted checks passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets:
`tests/cpu/moe_ep/test_megamoe_refresh_contracts.py`.

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

### [d3a7647](https://github.com/flashinfer-ai/flashinfer/commit/d3a764730a8b0587a4ea73b696b70bc283f0c268)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-24T03:22:21Z
- **提交信息**: fix(benchmarks): correct the legacy MegaMoE reducer grid size (#9814)

<!-- .github/pull_request_template.md -->

## 📌 Description

Report eight CTAs per token for the legacy CuTe DSL reducer baseline.

## 🔍 Related Issues

Follow-up to #9740.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files and fixed any reported
issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted checks passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

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

### [d87ad52](https://github.com/flashinfer-ai/flashinfer/commit/d87ad52ee3f6f45cac2b8d96477de79500056896)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-24T03:22:08Z
- **提交信息**: test(moe_ep): isolate MegaMoE tuning caches (#9813)

<!-- .github/pull_request_template.md -->

## 📌 Description

The workspace-sharing test can resolve different knobs for two identical
layers when a parallel reference test updates the saved tuning cache.
Disable saved lookup for the sharing tests and give each BF16/MXFP8
reference test a temporary cache.

## 🔍 Related Issues

Follow-up to #9740.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files and fixed any reported
issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted checks passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: `tests/moe_ep/test_workspace_pool.py`,
`tests/moe_ep/test_bf16_mxfp8_cutedsl_kernel_vs_reference.py`.

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

### [a7ed357](https://github.com/flashinfer-ai/flashinfer/commit/a7ed3574386db659bd017381ebafdd9513723125)

- **作者**: Perkz Zheng
- **时间**: 2026-11-24T01:31:35Z
- **提交信息**: perf(prims-ts): faster D512 GQA decode for NVFP4 and FP8 KV (#9771)

<!-- .github/pull_request_template.md -->

## 📌 Description

Speeds up PrimTS decode at head_dim 512 with eight Q heads per KV head
(Hq/Hkv 32/4, page 64, FP8 Q), the shape in #9602. Before this change it
was slower than trtllm-gen FP8, most visibly when requests share prefix
pages.

**q_len 1** (dense Swaps Q8, NVFP4 K/V):
- Stage each K or V tile once as a packed NVFP4 payload (all head-dim
slices, scale rows once) instead of one padded raw stage per D128 slice.
- Use one transformed TMEM ring slot per K or V tile (four head-dim
stages) and one converter warp group.
- Issue a slot's MMAs from one elected block.

**q_len 8** (grouped Keeps Q64/KV128):
- Auto-select Keeps for D512 NVFP4 K/V at eight Q heads per KV head;
before, only Swaps was considered. The same kernel also runs FP8-E4M3
K/V, which is now a supported D512 profile for that head ratio. Other
head ratios keep their current D512 behavior.
- Kernel changes:
- Scale TMAs are sliced per stage, which frees 20 KiB of SMEM for deeper
FP8 K/V rings.
  - Two loader warps.
  - Lane-panel O for head-dim stages 2/3.
- Allow the standalone split reducer
(`gmem_reduction_with_separate_kernel`) for grouped Keeps D512. Auto now
picks it before the in-kernel reducer.

**Both q_lens: dense FP4 multiply.** The NVFP4 row converters (packed
TMEM K, SMEM K/V rows) now use the dense `mul.rn.e4m3x4.e2m1x4.e4m3x4`
form, which the MLA decode converter already uses. It takes four
consecutive E2M1 values from each 16-bit half and returns their E4M3
bytes in order, two instructions per eight values. Before, the
converters used the padded `e2m1p4x4` form, which needs a shift, two
multiplies and two byte permutes. K and V therefore stay in logical
order, and neither Q nor O is permuted. The even-then-odd order is still
available via `use_permuted_packed_k_order` /
`use_permuted_packed_v_order`. Targets without the packed multiply (e.g.
SM107) keep the previous sequence.

**Divergence fixes in the split reducer** (`tmem_corr.py`). Two lane-0
spin loops left ptxas unable to prove warp convergence for the whole
kernel: one on the split ticket (after a lane-0 atomic), one on the
cluster transaction barrier. ptxas then wrapped every `tcgen05` MMA of
the MMA warp in `BRA.DIV`/`ELECT`/`VOTEU.ANY`/`R2UR.BROADCAST`. The
fixes:
- The ticket is taken by a whole warp: a lane-0 atomic, a shuffle, and a
uniform warp-wide spin.
- Every correction thread waits on the cluster mbarrier itself.

### Performance

The #9602 repro, unmodified: Hq/Hkv 32/4, D512, page 64, FP8 Q, BF16
output, KV 32768, 30720-token shared prefix. PrimTS uses NVFP4 K/V and
trtllm-gen uses FP8 K/V. Times are kernel µs, median of 3 runs. The
trtllm-gen column is the median over all 6 runs. The "this PR" and
trtllm-gen columns were re-measured after the dense-multiply commit,
interleaved with the previous head on the same node: q_len 1 shared got
2.2-3.0% faster and the other rows 0-0.6%. The "main" column is from the
original run on another node, so main / PR carries about 2% of node
variance (e.g. B300 q_len 1 unshared B32).

**B300**

| q_len | prefix pages | batch | main | this PR | trtllm-gen FP8 | main
/ PR | trtllm-gen / PR |
|---|---|---|---|---|---|---|---|
| 1 | shared | 8 | 104.9 | **61.7** | 73.8 | 1.70x | 1.20x |
| 1 | shared | 16 | 200.9 | **114.0** | 126.3 | 1.76x | 1.11x |
| 1 | shared | 32 | 364.5 | **216.1** | 236.5 | 1.69x | 1.09x |
| 1 | unshared | 8 | 121.6 | **111.1** | 173.7 | 1.09x | 1.56x |
| 1 | unshared | 16 | 218.5 | **198.0** | 320.6 | 1.10x | 1.62x |
| 1 | unshared | 32 | 401.7 | **369.7** | 615.0 | 1.09x | 1.66x |
| 8 | shared | 8 | 152.2 | **120.8** | 122.8 | 1.26x | 1.02x |
| 8 | shared | 16 | 278.2 | **225.2** | 226.5 | 1.24x | 1.01x |
| 8 | shared | 32 | 525.7 | **430.1** | 446.4 | 1.22x | 1.04x |
| 8 | unshared | 8 | 157.2 | **135.9** | 183.0 | 1.16x | 1.35x |
| 8 | unshared | 16 | 284.0 | **247.7** | 331.3 | 1.15x | 1.34x |
| 8 | unshared | 32 | 536.6 | **464.5** | 650.9 | 1.16x | 1.40x |

**B200**

| q_len | prefix pages | batch | main | this PR | trtllm-gen FP8 | main
/ PR | trtllm-gen / PR |
|---|---|---|---|---|---|---|---|
| 1 | shared | 8 | 109.7 | **63.6** | 74.8 | 1.72x | 1.18x |
| 1 | shared | 16 | 209.0 | **118.8** | 128.3 | 1.76x | 1.08x |
| 1 | shared | 32 | 379.2 | **224.5** | 240.8 | 1.69x | 1.07x |
| 1 | unshared | 8 | 121.6 | **111.4** | 172.1 | 1.09x | 1.54x |
| 1 | unshared | 16 | 220.6 | **194.0** | 315.9 | 1.14x | 1.63x |
| 1 | unshared | 32 | 400.7 | **359.6** | 601.8 | 1.11x | 1.67x |
| 8 | shared | 8 | 161.0 | **126.8** | 126.7 | 1.27x | 1.00x |
| 8 | shared | 16 | 291.9 | **234.3** | 237.9 | 1.25x | 1.02x |
| 8 | shared | 32 | 543.9 | **444.4** | 476.1 | 1.22x | 1.07x |
| 8 | unshared | 8 | 164.1 | **139.5** | 182.2 | 1.18x | 1.31x |
| 8 | unshared | 16 | 294.9 | **260.2** | 334.4 | 1.13x | 1.28x |
| 8 | unshared | 32 | 556.6 | **501.7** | 674.5 | 1.11x | 1.34x |

### Shared prefixes at q_len 8: convert-once split (example, not part of
this PR)

With a shared prefix at q_len 8, a single NVFP4 call converts the same
prefix pages to FP8 once per request. trtllm-gen reads FP8 directly, so
the single call stays near parity with it (table above).

The example
[`nvfp4_shared_prefix_convert_once.py`](https://github.com/PerkzZheng/prims-ts-examples/blob/examples/nvfp4-shared-prefix-convert-once/nvfp4_shared_prefix_convert_once.py)
in PerkzZheng/prims-ts-examples ([PR
#4](https://github.com/PerkzZheng/prims-ts-examples/pull/4)) uses only
public APIs plus its own small CUDA kernel. Each step it:
1. converts the shared pages once to `E4M3(e2m1 * block_scale)`, the
same FP8 values the NVFP4 kernel computes with;
2. runs an FP8 K/V prefix pass, which relies on the FP8 D512 profile
added here;
3. runs an NVFP4 suffix pass on a side stream;
4. combines the two with `flashinfer.merge_state_in_place`.

The example checks the conversion bit-exactly and checks both paths
against an FP32 reference.

B300 results, 30720 shared plus 2048 private tokens per request, q_len
8. Times are per CUDA-graph replay with a cold L2 (CUDA events, so a few
µs above the kernel times above):

| batch | single NVFP4 call | convert-once split | speedup |
|---|---|---|---|
| 32 | 436.2 µs | 323.6 µs | 1.35x |
| 16 | 229.4 µs | 210.9 µs | 1.09x |
| 8 | 124.9 µs | 149.5 µs | 0.84x |

The conversion is a fixed cost of about 35 µs per step. Use the split
for roughly 16 or more requests sharing a long prefix, and the single
call otherwise. The split is a caller-side choice; this PR does not
change dispatch for it.

## 🔍 Related Issues

Addresses #9602 (PrimTS NVFP4 D512 GQA decode slower than trtllm-gen FP8
with shared prefix pages).

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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_decode.py`

New tests in `tests/attention/test_attention_ts_decode.py`:
- `test_attention_ts_decode_d512_q8_auto_selects_grouped_keeps`:
B8/16/32 with NVFP4 and FP8 K/V select grouped Keeps Q64, no cluster
reduction, and the separate reducer when split.
- `test_attention_ts_decode_d512_keeps_policy_scope`: Hq64 and q_len 1
stay off Keeps; FP8 K/V D512 outside eight Q heads per KV head is
rejected.
- `test_attention_ts_decode_d512_fp8_kv_grouped_keeps`: FP8 K/V D512
grouped Keeps accuracy, causal and dense, BF16 and FP16, including
base-2 LSE.
- D512 Keeps rows in `test_attention_ts_decode_large_tile_size_q` with
the separate reducer.
- Review follow-up (host-only config tests):
`test_attention_ts_decode_nvfp4_d512_keeps_ring_depths_fit` (converted
and raw ring depths fit SMEM),
`test_attention_ts_decode_whole_tile_nvfp4_stage_requires_full_slices`
(D192 rejected), and override cases added to the D512 Q8
transformed-slot and policy-scope tests.
- Dense FP4 multiply follow-up:
`test_attention_ts_decode_nvfp4_d512_even_odd_order_opt_in` runs the
opt-in even-then-odd K order (q_len 1, Swaps Q8, with LSE) and K/V order
(Keeps Q64, q_len 8) on the GPU against the reference. The
transformed-slot and ring-depth tests now check that both orders are off
by default and that the opt-in resolves. The large-tile test's LSE
reference handles one-token decode Q.

Results on B300 and B200 (CUDA 13, local runs):
- Full `tests/attention/test_attention_ts_decode.py`: 1194 passed, 96
skipped. The 32 failures in that run were addressed:
- 28 `q_token_sparse` tests failed to build. My local tree had no link
to the CCCL now bundled with FlashInfer, so the build used the CTK's
older CCCL, which lacks `cuda::fast_mod_div`. This is unrelated to this
PR.
- 4 were in the new D512 tests: the FP8 reference partition and an
error-message match. Both were fixed in the test.
- Rerun of the failed groups after the fixes (`-k "q_token_sparse or
d512 or large_tile_size_q"`): 159 passed, 96 skipped, 0 failed on each
GPU.
- After the review fixes (9f58f96): the full file gave 1227 passed and
96 skipped on each GPU. The one failure was a new host test, fixed in
the same commit. After that fix, the D512, whole-tile and large-tile
subset gave 132 passed and 96 skipped on B300.
- Dense FP4 multiply (479a5d531): the full file gave 1229 passed, 96
skipped and 1 failed on each GPU. The failure was the new opt-in test's
q_len 1 case, where the large-tile helper's LSE reference expected 3-D Q
per request; the kernel itself ran. After the helper fix, the `-k
"large_tile_size_q or even_odd_order or d512"` subset gave 133 passed,
96 skipped, 0 failed on each GPU.

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

- Pre-commit could not run on my machine. I ran `ruff check` and `ruff
format --check` on the changed files instead, and both pass.
- The D512 Keeps auto policy and the FP8 K/V D512 profile are limited to
eight Q heads per KV head, the only ratio measured. Other D512 shapes
keep the current selection.
- `tmem_corr.py`: both reducer waits are now warp-uniform, and the
change applies to every kernel that uses the split reducer. The win
comes from ptxas no longer wrapping each MMA in a divergence guard;
check with `cuobjdump -sass` (no `BRA.DIV` next to `UTC*MMA`). On the
non-D512 kernels I measured, timing moved by 0 to 0.8%.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added D512 paged attention support for FP8 and NVFP4 key/value formats
with supported output types.
* Expanded grouped-Keeps support for eligible D512 query-to-key/value
head ratios, including split-reduction modes.
* Added NVFP4 execution options for supported D512 profiles, including
packed staging and even-then-odd packed K/V ordering.
* **Documentation**
* Updated D512 guidance with supported configurations, execution modes,
restrictions, and fallback behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [23d136d](https://github.com/flashinfer-ai/flashinfer/commit/23d136dd16234b9c0f81f52991a3ca5ef007de1d)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-24T00:21:39Z
- **提交信息**: fix(moe_ep): reject invalid Blackwell GenPhase scale-pusher counts (#9819)

<!-- .github/pull_request_template.md -->

## 📌 Description

Require at least one GenPhase CTA to push scale factors. Reject zero and
negative counts during kernel construction, before a workspace can
launch without a scale-factor publisher.

## 🔍 Related Issues

Follow-up to #9740.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files and fixed any reported
issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted checks passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: `tests/moe_ep/test_sm100_genphase_dtypes.py`,
`tests/moe_ep/test_provider_package.py`.

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

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4857
- **最后更新**: 2026-11-25T03:27:06Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Kirill Kozlov

## AI分析总结

### 1. 主要更新类型
**功能新增**。该提交为 FastVideo 项目添加了 **FastKandinsky 6.0 模型的 NVFP4 量化推理支持**，属于核心功能扩展，而非修复或重构。

### 2. 关键变更点及与项目整体方向的关系
- **集成新模型**：引入 Kandinsky 6.0 这一视频生成模型的加速版本，丰富了项目支持的模型生态。
- **引入 NVFP4 量化**：采用 NVIDIA 的 4-bit 浮点量化格式（NVFP4）进行推理，体现了项目对高效、低显存占用推理的追求。
- **与项目方向的契合**：FastVideo 本身专注于视频生成模型的高效部署与加速，该提交直接增强了其模型库的多样性与推理性能，符合其提供高效视频生成解决方案的定位。

### 3. 对项目的影响和潜在意义
- **功能覆盖提升**：为用户提供了 Kandinsky 6.0 这一新选择，特别是对需要低显存环境或追求快速推理的用户具有吸引力。
- **硬件兼容性**：NVFP4 格式通常针对较新的 NVIDIA GPU（如 Blackwell 架构）进行优化，这有助于项目在新硬件上发挥最佳性能。
- **潜在用户群扩大**：新模型和量化能力的加入，可能吸引更广泛的视频生成模型使用者和研究者。

### 4. 值得关注的技术点
- **NVFP4 量化实现**：需要关注其在 Kandinsky 6.0 架构上的具体应用方式（是全模型量化还是关键模块量化）及其带来的精度与速度平衡。
- **模型架构适配**：Kandinsky 6.0 作为视频生成模型，其与 FastVideo 框架的集成方式（如计算图优化、内存管理）是实现高效推理的关键。
- **性能基准**：值得期待该模型在不同硬件上的实际推理速度和显存占用对比数据。

### 5. 基于README背景对项目发展的影响
根据 README，FastVideo 是一个提供高效视频生成模型和工具的平台，并链接了 Uniserve 和 Dreamverse Harness 等项目，显示其致力于构建完整的视频生成生态系统。本次添加 **FastKandinsky 6.0 NVFP4 推理**，不仅直接扩展了项目的功能边界，更通过引入前沿的量化技术（NVFP4）强化了其“高效推理”的核心卖点。这一进展将吸引更多寻求高性能视频生成方案的开发者，巩固 FastVideo 在高效模型部署领域的技术领先地位，并为后续集成更多支持现代量化格式的模型奠定基础。

## 详细提交记录

### [a04639f](https://github.com/hao-ai-lab/FastVideo/commit/a04639fa976d9f27ea0ff0c3febb9e7643ecbc37)

- **作者**: Kirill Kozlov
- **时间**: 2026-11-24T15:24:36Z
- **提交信息**: [feat] Add FastKandinsky 6.0 NVFP4 inference (#2123)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34971
- **最后更新**: 2026-11-25T03:49:44Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 5
- **主要提交者**: Sayak Paul, NamdidNC, Xu-Peisen

## AI分析总结

## huggingface/diffusers 昨日提交分析总结

### 1. 主要更新类型
- **性能优化**（1项）：RoPE 旋转位置编码的显存优化
- **Bug 修复**（3项）：LoRA 转换错误、非PIL输入处理、CI测试修复
- **文档更新**（2项）：拼写和语法错误修复
- **CI/测试改进**（1项）：GPU测试覆盖范围扩大

### 2. 关键变更点及与项目方向的关系

**性能优化（RoPE）**：通过移除 apply_rotary_emb 及多个模型本地 RoPE 辅助函数中的显式 float32 强制转换，避免了不必要的中间副本分配。利用类型提升机制（type promotion），在 float32 cos/sin 下计算已自动在 float32 中进行，输出位级一致。此优化横跨 LTX、LTX-2、QwenImage、LongCat-AudioDiT、JoyImage、Allegro 等多个模型，与 diffusers 作为多模型统一推理库的方向一致，降低了显存占用。

**LoRA 转换修复**：Flux Control 和 HunyuanVideo 转换器在处理 final_layer 的 scale/shift 重映射时，错误地同时交换了 lora_A 的两个半部分，打乱了秩维度。修复后仅交换 lora_B，与 kohya Flux 转换器保持一致。这直接影响 LoRA 权重转换的正确性，对下游微调用户至关重要。

**非PIL输入裁剪修复**：对非PIL图像输入拒绝裁剪坐标，属于防御性编程，提升了 API 健壮性。

### 3. 对项目的影响和潜在意义
- **性能收益**：RoPE 优化在多模型上生效，减少推理和训练时的显存峰值，对长序列模型（如 LongCat）收益更明显
- **正确性保障**：LoRA 修复确保转换后的微调权重能产生正确的 delta，避免用户静默得到错误结果
- **工程规范**：CI 测试覆盖扩大到 LoRA 触发器和更多组件，减少回归风险
- **社区质量**：文档微调虽小但体现了对细节的重视

### 4. 值得关注的技术点
- **类型提升的正确利用**：RoPE 优化依赖于 PyTorch 的类型提升规则，需要理解 cos/sin 的 dtype 与输入 dtype 的交互，提交中还通过注释统一说明了这一点
- **`# Copied from` 机制**：QwenImage 2.1、NucleusMoE、SANA-WM refiner 等通过该机制同步代码，体现了 diffusers 维护大量重复代码片段的策略
- **CI 触发器设计**：GPU 测试的 LoRA 触发逻辑涉及条件路径，需要精准标记才能覆盖
- **位级一致性测试**：RoPE 优化声称 bit-identical，这类优化在浮点环境下需严格验证

### 5. 基于 README 背景的项目发展影响
从 README 可见，diffusers 是 Apache 2.0 许可的开源扩散模型库，由 HuggingFace 团队维护。这批提交反映了项目处于**成熟维护期**：以性能微优化、正确性修复、CI 完善和文档打磨为主，而非大规模功能新增。这与一个被广泛使用的生产级库的典型节奏一致——优先保障已有多模型（Flux、LTX、QwenImage、HunyuanVideo 等）的正确性和效率，同时通过 CI 扩展防止回归。LoRA 转换和 RoPE 优化这两类提交对下游用户（微调、推理服务提供方）的直接影响最大，体现了项目对实际使用场景的关注。

## 详细提交记录

### [2dfe493](https://github.com/huggingface/diffusers/commit/2dfe4932476aca0837b7b09a36549232416282ed)

- **作者**: Xu-Peisen
- **时间**: 2026-11-24T18:58:41Z
- **提交信息**: Reject crop coordinates for non-PIL image inputs (#15390)

### [5b58188](https://github.com/huggingface/diffusers/commit/5b58188bb8cf838e0b4b5a11208f7de59e67ed64)

- **作者**: NamdidNC
- **时间**: 2026-11-24T16:16:53Z
- **提交信息**: docs: fix "withy" -> "with" in LTX2 modality_scale docstring (#15374)

The modality_scale parameter docstring in the three LTX2 pipelines reads
"...the denoising model withy cross-modality ... cross attention disabled".
"withy" (a willow twig) is a real word, so the typos CI check does not flag it;
the intended word is "with". Docstring-only, no logic change.

Co-authored-by: NamdidNC <271918887+NamdidNC@users.noreply.github.com>

### [83b7b41](https://github.com/huggingface/diffusers/commit/83b7b410d941ebfa65ff6b064512f998760d9bdd)

- **作者**: NamdidNC
- **时间**: 2026-11-24T16:12:38Z
- **提交信息**: docs: fix "an" -> "a" before a consonant in two docs pages (#15375)

Two indefinite-article typos a spell-checker cannot catch because "an" is a
valid word:
- docs/source/en/api/pipelines/anyflow.md: "under an dark sky" -> "under a dark sky"
- docs/source/en/conceptual/contribution.md: "an recurring issue" -> "a recurring issue"

Docs-only, no logic change.

Co-authored-by: NamdidNC <271918887+NamdidNC@users.noreply.github.com>

### [f112184](https://github.com/huggingface/diffusers/commit/f112184d8b888456b66e2f68e2b79c698cb5de39)

- **作者**: Sayak Paul
- **时间**: 2026-11-24T04:23:00Z
- **提交信息**: ci: modular test to device fix (#15381)

* fix test_to_device test for none case cases

* fix mp inference test

* propagate to others.

### [aa974d5](https://github.com/huggingface/diffusers/commit/aa974d5c837e748b8b75ed6192088db3910c489e)

- **作者**: klin
- **时间**: 2026-11-24T03:54:12Z
- **提交信息**: Avoid float32 copies of q / k in the RoPE helpers (#15215)

* Avoid float32 copies of the input in apply_rotary_emb

`x.float() * cos + x_rotated.float() * sin` materializes float32 copies of
x and x_rotated. With float32 cos / sin, type promotion already computes
the products in float32, so drop the explicit casts. Bit-identical output.

Signed-off-by: Lin, KuanTing <Kuanting.Lin@amd.com>

* Drop the float32 copies in the model-local RoPE helpers too

Same change as in apply_rotary_emb, applied to the helpers that repeat the
`x.float() * cos + x_rotated.float() * sin` expression: LTX, LTX-2, QwenImage,
LongCat-AudioDiT, JoyImage, JoyImage-Edit-Plus and Allegro (plus the
`# Copied from` copies in QwenImage 2.1, NucleusMoE and the SANA-WM refiner,
synced with `make fix-copies`). Bit-identical output.

Signed-off-by: Lin, KuanTing <Kuanting.Lin@amd.com>

* Test apply_rotary_emb against the float32 reference

Checks that apply_rotary_emb matches the explicit float32 formula bit for bit
for fp32 / fp16 / bf16 inputs, both use_real_unbind_dim values and both
sequence_dim values.

Signed-off-by: Lin, KuanTing <Kuanting.Lin@amd.com>

* Use one comment for the RoPE type-promotion casts and drop the unit test

Address review: the same comment at every call site, and remove the
apply_rotary_emb test from test_layers_utils.py.

Signed-off-by: Lin, KuanTing <Kuanting.Lin@amd.com>

---------

Signed-off-by: Lin, KuanTing <Kuanting.Lin@amd.com>

### [98dfc1a](https://github.com/huggingface/diffusers/commit/98dfc1aa4146e0d8bcbdb2d00ff68e698ce3304c)

- **作者**: Aditya Gupta
- **时间**: 2026-11-24T03:35:04Z
- **提交信息**: [LoRA] Only swap lora_B in final_layer scale/shift remaps (Flux Control, HunyuanVideo) (#15307)

* [LoRA] Only swap lora_B in final_layer scale/shift remaps (Flux Control, HunyuanVideo)

The original final layer orders its modulation (shift, scale) and diffusers' norm_out
(scale, shift). The Flux Control and HunyuanVideo converters swapped the halves of
lora_A as well as lora_B, which scrambles lora_A's rank dimension and gives a wrong
delta. Swap only lora_B, as the kohya Flux converter already does.

* Use minimal tensors in the Flux Control final layer LoRA test

* Take the Flux Control LoRA block counts from the state dict and shrink its test

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [bdc22bd](https://github.com/huggingface/diffusers/commit/bdc22bd7b8e8430adf6c13342154fec325c6ede7)

- **作者**: Sayak Paul
- **时间**: 2026-11-24T03:34:43Z
- **提交信息**: [ci]: broaden PR GPU test coverage. (#15365)

* fix lora triggers in our ci.

* add lora markers where missing.

* fix lora triggers.

* add left out components.

* address review feedback.

* Apply batched suggestions from code review

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

* address remaining feedback.

---------

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
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


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13441
- **最后更新**: 2026-11-25T03:26:53Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

# DiffSynth-Studio 昨日提交分析

## 1. 主要更新类型
**功能新增**。该提交为项目添加了对 **SenseNova v1.6** 模型的支持，属于扩展模型/后端兼容性的功能迭代。

## 2. 关键变更点及与项目整体方向的关系

- **SenseNova v1.6 集成**：DiffSynth-Studio 作为扩散模型（Diffusion）综合实验平台，其核心目标是统一管理和支持多种扩散生成模型。此次提交将 SenseNova v1.6（商汤科技的多模态大模型系列）纳入支持范围，符合项目"一站式扩散模型工作室"的定位。
- **模型生态扩展**：项目持续扩充支持的模型列表，使开发者可以在统一框架下切换和使用不同来源的生成模型，降低接入成本。

## 3. 对项目的影响和潜在意义

- **提升兼容性与可用性**：用户无需为 SenseNova v1.6 单独适配，可直接在 DiffSynth-Studio 框架内使用该版本模型。
- **增强商业/生产场景适用性**：SenseNova 系列常用于商业多模态场景，支持该模型可拓展项目在产业端的影响力。
- **保持技术前沿性**：及时跟进上游模型版本更新（v1.6），确保框架不落后于模型发布节奏。

## 4. 值得关注的技术点

- **模型版本适配机制**：需关注项目如何抽象不同模型版本的接口（如配置文件、pipeline 注册等），版本升级通常涉及权重加载、超参调整和推理逻辑变化。
- **PR #1855 的实现范围**：作为单次提交，改动量应集中在模型加载/配置层，具体涉及的文件（如 `models/`、`pipelines/`）和测试情况值得进一步查阅。
- **依赖管理**：SenseNova v1.6 可能引入新的依赖或对现有推理后端有版本要求。

## 5. 对项目发展的整体影响

结合 README 背景，DiffSynth-Studio 是一个活跃迭代的扩散模型综合平台（已有 1800+ PR），此次提交延续了项目"持续扩展模型覆盖"的主线策略。这类常规但必要的模型支持更新有助于：

- **扩大用户群**：覆盖 SenseNova 生态的开发者；
- **巩固平台定位**：强化"多模型统一管理"的差异化优势；
- **降低维护风险**：尽早跟进新版本可避免用户自行适配时出现的兼容问题。

总体而言，这是一个典型的**平台化扩展型提交**，虽单次改动不大，但对维持项目与模型生态的同步性至关重要。

## 详细提交记录

### [3093e55](https://github.com/modelscope/DiffSynth-Studio/commit/3093e5599430e5605054cd052631344ae4298891)

- **作者**: Hong Zhang
- **时间**: 2026-11-24T06:16:17Z
- **提交信息**: support sensenova v1.6 (#1855)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 39033
- **最后更新**: 2026-11-25T04:00:34Z

## 提交统计

- **昨日提交总数**: 73
- **提交者数量**: 48
- **主要提交者**: Jacob0226, Yichi Zhang, weireweire

## AI分析总结

# sgl-project/sglang 昨日提交总结（共 73 条）

## 1. 主要更新类型

昨日提交以**性能优化**为主（约 25 条），覆盖 AMD gfx1250、NVIDIA Hopper/SM107、NPU、MoE/MLA 内核、linker 传输与采样热路径；**Bug 修复**次之（约 18 条），涉及 function_call 流式解析、JIT 缓存、PP 预填充传输、内存缓存与 KV 事件等核心推理路径；**CI/安全流程重构**约 19 条，是另一条主线；其余为功能新增（安全鉴权、muse_spark 专家 TP、FlashInfer KDA、Mooncake EGM Store）、文档与 Cookbook 更新及少量重构。

## 2. 关键变更点及与项目方向的关系

- **CI 与供应链安全收紧**：`run-ci` 改为仅允许命令式批准（以 `CI_PERMISSIONS.json` 为审批源）、`pr-test` 迁移至 `pull_request_target` 并绑定一次性 commit、MLU 与 sgl-router 门控改为逐提交审批、CI 日志掩码 HF token、监控栈绑定回环并强制 Grafana 密码。这些变更服务于活跃开源项目的自动化可信执行，回应了带凭证工作流的注入风险，也契合近期 AI 协作者批量署名提交带来的审查压力。
- **生产安全与运维加固**：扩散服务引入 API key 分权（分别控制权重、LoRA、内存与 profiling 路由）及环境变量校验，使模型服务具备上生产的安全前提。
- **函数调用流式可靠性**：DeepSeek V3、Qwen 2.5、MiniMax-M2 等多模型跨 chunk 流式 tool call 解析修复，强化 LLM Agent 场景正确性。
- **多硬件平台深度优化**：AMD gfx1250（RoPE、MLA、FP8 GEMM、AITER 升级、MoE 回退）、NVIDIA H20/H200/Hopper Triton 与 SM107 KDA、NPU 内核镜像升至 post14、XPU 与 MLU CI——体现多元算力生态的持续投入。
- **分布式传输与并行演进**：Mooncake linker 系列优化（批量 range read、分组加载元数据 numpy 化、DSpark draft KV 合并）、EGM Store、zigzag CP 元数据、AsyncPP 系列首篇（1/9）、PP 预填充传输经 PP0 统一释放，指向更大规模 PD 分离与流水线并行异步化。

## 3. 值得关注的技术点

- JIT 内核 nightly 基线加 PR 级回归报告（#52132），为性能回归提供量化守护；符号链接导致 JIT 永久 miss 的修复对容器化部署尤为重要。
- FlashInfer autotune 缓存与单 rank 策略持久化，减少重复编译冷启动开销。
- 采样与 allocator 批量向量化（dispatch map、balanced_packing、PageInterleave、sampler 参数复用）属低开销高收益的热路径调优。
- linker 分组 range read 流水线与 EGM-backed Store 池，预示 KV 传输架构向分层缓存演进。

## 4. 对项目整体发展的影响

这些提交共同推动 SGLang 在"快速推理"核心目标下，向**生产安全、多硬件覆盖、分布式传输效率、Agent 工具调用鲁棒性**四个方向纵深发展。CI 的"一次一批准、命令唯一入口"模式显著降低恶意 PR 风险，为更大规模社区贡献铺路；缓存与微优化修复改善长周期集群的稳定性；muse_spark 支持 `--ep-size 1` NVFP4 检查点补齐了量化模型的专家并行部署能力。性能提交多由社区与 AMD/NVIDIA 侧协同完成，生态协作已成常态。整体而言，项目正从功能扩张期进入**工程治理与性能精修并重**的成熟阶段，为规模化部署与性能基准保持奠定了坚实基础。

## 详细提交记录

### [2e4f4ca](https://github.com/sgl-project/sglang/commit/2e4f4ca1939d25f9c65377daabd5c19e237e97d0)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-24T23:56:30Z
- **提交信息**: [Feat] diffusion: Require API keys on the server, with the admin key for weight, LoRA, memory, and profiling routes (#52929)

### [2c07dbe](https://github.com/sgl-project/sglang/commit/2c07dbe76be9f2923088efbbc8af4eb2867f083a)

- **作者**: Sage
- **时间**: 2026-11-24T23:50:12Z
- **提交信息**: [Chore] sgl-router: move tokenizer prompt logic out of policies (#47978)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [67b442f](https://github.com/sgl-project/sglang/commit/67b442f4f9212309018a989f62bca3861cf1e82e)

- **作者**: ChihTsungLu
- **时间**: 2026-11-24T23:48:01Z
- **提交信息**: [Fix] io_struct: Reject list RIDs for single requests (#50709)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [fc371f7](https://github.com/sgl-project/sglang/commit/fc371f770ef8d51dbec04aaf3659453ccbb2a500)

- **作者**: Yibo Liu
- **时间**: 2026-11-24T23:46:37Z
- **提交信息**: [Test] function_call: Test streamed tool calls across chunk boundaries for every parser (#50609)

Signed-off-by: Yibo Liu <yibol9768@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [0cce4b8](https://github.com/sgl-project/sglang/commit/0cce4b86200dd342f946533d09a510d3a5332253)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-24T23:29:35Z
- **提交信息**: [CI] slash-commands: Comment only when a command fails; react on success (#52934)

### [2ad1c93](https://github.com/sgl-project/sglang/commit/2ad1c939a5c3cfd3dd8c4d6680209e0f289d625c)

- **作者**: Duy Hua
- **时间**: 2026-11-24T23:28:59Z
- **提交信息**: [Fix] environ: Reject invalid environment variable values (#50546)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [bdbfd87](https://github.com/sgl-project/sglang/commit/bdbfd879da4f454807c0de2d1e4b629631ab695a)

- **作者**: Yufeng He
- **时间**: 2026-11-24T23:27:06Z
- **提交信息**: [Fix] function_call: Match the first buffered call in DeepSeek V3/V3.1 streaming (#43544)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [9bb13b7](https://github.com/sgl-project/sglang/commit/9bb13b745bd25fab5ab336d240c125b76c3ae34c)

- **作者**: dingdangmao
- **时间**: 2026-11-24T23:19:35Z
- **提交信息**: [Fix] function_call: Release held-back Qwen 2.5 text at end of stream (#41039)

Signed-off-by: 叮当猫 <2756823972@qq.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [752473e](https://github.com/sgl-project/sglang/commit/752473e61b00a29d3811b2d85f0e6308665033bd)

- **作者**: shiyichuan
- **时间**: 2026-11-24T23:19:14Z
- **提交信息**: [Fix] function_call: Make MiniMax-M2 streaming match detect_and_parse (#36691)

Signed-off-by: CarrotSwordsman <mershi@tencent.com>
Signed-off-by: mershi <mershi@tencent.com>
Co-authored-by: CarrotSwordsman <mershi@tencent.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [751009f](https://github.com/sgl-project/sglang/commit/751009f22e1078200e4deffab6c7c32d757288bc)

- **作者**: Kaixing Wu
- **时间**: 2026-11-24T23:16:55Z
- **提交信息**: [Fix] mem_cache: Clip a unified-memory request's decode by the shared arena alone (#52904)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [a676d07](https://github.com/sgl-project/sglang/commit/a676d077a38cb7675f0c7292c7d284195f8a9e13)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-24T23:02:52Z
- **提交信息**: [Doc] monitoring: Bind the example stack to loopback, require a Grafana admin password, and warn before exposing the server (#52925)

### [2d03ffc](https://github.com/sgl-project/sglang/commit/2d03ffcdf29584165f98781d0aececa6526f3835)

- **作者**: garry569
- **时间**: 2026-11-24T22:47:28Z
- **提交信息**: [Perf] cp: Upload zigzag CP metadata with one pinned non-blocking copy (#47576)

Co-authored-by: garry569 <324435785+garry569@users.noreply.github.com>

### [7d068df](https://github.com/sgl-project/sglang/commit/7d068dfedd64cefac71fe6daca1eb5380f710266)

- **作者**: akhilg-nv
- **时间**: 2026-11-24T22:40:27Z
- **提交信息**: [Feat] mooncake: Add opt-in EGM-backed Mooncake Store pool over NVLink (#51416)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [84a0fe5](https://github.com/sgl-project/sglang/commit/84a0fe53c462fa8bbe822313e698a846374de4bc)

- **作者**: Hubert Lu
- **时间**: 2026-11-24T22:13:48Z
- **提交信息**: [Perf] [AMD] carv2: SPX-specific gfx1250 table for TP2/TP4 (#51631)

### [970b365](https://github.com/sgl-project/sglang/commit/970b3650939e35d019cef4bf482de3fb39e22410)

- **作者**: garry569
- **时间**: 2026-11-24T21:48:49Z
- **提交信息**: [Perf] kv-shard: Batch PageInterleave allocator pops and frees per batch (#47578)

Co-authored-by: garry569 <324435785+garry569@users.noreply.github.com>

### [2070487](https://github.com/sgl-project/sglang/commit/2070487eccdda795a6a4a00ecb0b9b560612cfee)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-24T21:09:58Z
- **提交信息**: [CI] slash-commands: Add an atomic /approve-ci and remove /tag-run-ci-label (#52831)

### [9686923](https://github.com/sgl-project/sglang/commit/96869231501ad19df4c7ef4e6755c1f2d84d2541)

- **作者**: Trevor Morris
- **时间**: 2026-11-24T19:47:09Z
- **提交信息**: [Perf] eplb: Compute the dispatch map's first match with scatters instead of a loop over replica slots (#51346)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [4237283](https://github.com/sgl-project/sglang/commit/4237283907fbe5abc688f45c5975a1f08e1e57de)

- **作者**: Trevor Morris
- **时间**: 2026-11-24T19:46:34Z
- **提交信息**: [Perf] eplb: Vectorize the greedy loop of balanced_packing over layers (#51345)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [d90d18d](https://github.com/sgl-project/sglang/commit/d90d18da5123ba980c7932fce6e3288d5d8fc2b0)

- **作者**: Mick
- **时间**: 2026-11-24T18:57:01Z
- **提交信息**: [CI] diffusion: Stabilize stage polling and make gated Praxis HTTP tests opt-in (#52810)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [ba76f34](https://github.com/sgl-project/sglang/commit/ba76f34b85a4b77d765ab96a82e3cc6eb804cb96)

- **作者**: leonid-talalaev-nebius
- **时间**: 2026-11-24T16:39:39Z
- **提交信息**: [Fix] kv-events: Retry replay batches under backpressure (#48114)

Signed-off-by: PeaBrane <yanrpei@gmail.com>
Co-authored-by: PeaBrane <yanrpei@gmail.com>
Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [34271ca](https://github.com/sgl-project/sglang/commit/34271ca06b5641ae0b794eae4e8f4c8edf88d007)

- **作者**: YAMY
- **时间**: 2026-11-24T16:34:52Z
- **提交信息**: [Perf] [NVIDIA] gdn: Make ReplaySSM verify pipeline stages configurable (#46633)

### [f4284f2](https://github.com/sgl-project/sglang/commit/f4284f29ba56fffe2d09c9e6c5ac5e218e6cc053)

- **作者**: Denji-kk
- **时间**: 2026-11-24T13:42:47Z
- **提交信息**: [Perf] linker: Build every Mooncake layer group's range reads before the forward fence (#49468)

Co-authored-by: alphabetc1 <2508695655@qq.com>

### [88c1065](https://github.com/sgl-project/sglang/commit/88c10654aedd7d3cc8ae7f16699020aff53efee0)

- **作者**: shun8686
- **时间**: 2026-11-24T13:31:06Z
- **提交信息**: [CI] [NPU] test: Fail fast on dead launchers and share multi-node startup mixins (#52857)

### [595b598](https://github.com/sgl-project/sglang/commit/595b59864c275ea1e2ca4033c48d6c12ffbfb018)

- **作者**: Jacob0226
- **时间**: 2026-11-24T13:03:27Z
- **提交信息**: [Fix] [AMD] GLM-5.3-Flash: Keep the MoE correction bias fp32 (#44415)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>
Co-authored-by: CHANG <jacchang@crsuse2-slog-006.us-east2-a.compute.internal>
Co-authored-by: Bingxu Chen <bingxche@amd.com>

### [87c11e4](https://github.com/sgl-project/sglang/commit/87c11e4ffc5b8db4fa8be1b3e929c09c96ff943d)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-11-24T13:03:17Z
- **提交信息**: [Perf] [AMD] muse-spark: Faster FP8 joint router/pooler GEMM for decode and verify (#50685)

Co-authored-by: jiaqiang-dot-liu <295720280+jiaqiang-dot-liu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [93e6375](https://github.com/sgl-project/sglang/commit/93e637504041b592a47a94d5e0ce0017b117cb4f)

- **作者**: Denji-kk
- **时间**: 2026-11-24T12:59:47Z
- **提交信息**: [Perf] linker: Complete landed Mooncake layer groups between submits (#49464)

Co-authored-by: alphabetc1 <2508695655@qq.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [72c9f47](https://github.com/sgl-project/sglang/commit/72c9f47614978e7e5d031636bef734d46f10c249)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-24T12:40:07Z
- **提交信息**: [Test] gdn: Stub is_batch_invariant_mode_enabled in the chunk_fwd_o dispatch test (#52848)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d34afcc](https://github.com/sgl-project/sglang/commit/d34afcc18071d909cee219a7cdda76a42e6f87a9)

- **作者**: Shuwen Wang
- **时间**: 2026-11-24T12:38:44Z
- **提交信息**: [Fix] test: Stub is_batch_invariant_mode_enabled in the GDN chunk output dispatch test (#52843)

### [c7be2a0](https://github.com/sgl-project/sglang/commit/c7be2a015e2a0ffa959ab4a349c4178e4435f090)

- **作者**: Peng Xingchen
- **时间**: 2026-11-24T11:16:35Z
- **提交信息**: [Fix] [NPU] mem_cache: Fix out-of-bounds KPool index writes in GLM-5.3-Flash (#51787)

### [a8101b6](https://github.com/sgl-project/sglang/commit/a8101b6a9ff44cdf141d00b2cd644fef13776c15)

- **作者**: Alan Kao
- **时间**: 2026-11-24T11:14:36Z
- **提交信息**: [Perf] [AMD] rotary_embedding: tile fused RoPE and KV write for large T on gfx1250 (#49566)

Co-authored-by: sogalin_codegen <39478626+sogalin@users.noreply.github.com

### [6e5e65c](https://github.com/sgl-project/sglang/commit/6e5e65cf509d85fbb6a81c3be85fcaac4a0ed0f4)

- **作者**: Aarne Talman
- **时间**: 2026-11-24T11:02:15Z
- **提交信息**: [Fix] deterministic: Keep the GDN output tile fixed for varlen prefill (#44194)

Signed-off-by: Aarne Talman <aarne.talman@amd.com>

### [fbb46d0](https://github.com/sgl-project/sglang/commit/fbb46d0fab56dee88e37ee31adda5572c81ed38c)

- **作者**: weireweire
- **时间**: 2026-11-24T09:58:30Z
- **提交信息**: [Perf] sampling: Reuse the sampler params of an unchanged batch (#52570)

### [4a441c0](https://github.com/sgl-project/sglang/commit/4a441c02435c5e7757fc8e0b04f1ff9f156918e1)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-24T09:53:19Z
- **提交信息**: [CI] run-ci: Skip the commit approval on /tag-and-rerun-ci when the PR author may approve (#52804)

### [00d7427](https://github.com/sgl-project/sglang/commit/00d74273acdd4a5fe762462731972f05b01ee85a)

- **作者**: HeYao
- **时间**: 2026-11-24T09:49:52Z
- **提交信息**: [CI] [NPU] Dsv4-Flash: Turn off speculative inference and enable mixChunk (#46013)

Co-authored-by: HeYao <heyao@example.com>

### [200b9a9](https://github.com/sgl-project/sglang/commit/200b9a9afe4ca30c8ed37ff3f1920b9289315f24)

- **作者**: Alphin Jain
- **时间**: 2026-11-24T09:30:27Z
- **提交信息**: [Fix] qwen2.5-vl: use per-frame cu_seqlens for video full attention (#47918)

### [88dc750](https://github.com/sgl-project/sglang/commit/88dc7501f58f026a18357b8ad4ef1f280e1fc2b4)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-24T08:56:32Z
- **提交信息**: [CI] pr-states: Drop the duplicate dispatch from pr-test and pr-test-extra; workflow_run already refreshes on reruns (#52788)

### [059e552](https://github.com/sgl-project/sglang/commit/059e552a208990cfe91cd5bffed3232d09ffda04)

- **作者**: Denji-kk
- **时间**: 2026-11-24T08:54:20Z
- **提交信息**: [Perf] linker: Load DSpark draft KV with the last transfer layers (#49466)

Co-authored-by: alphabetc1 <2508695655@qq.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [31f24e3](https://github.com/sgl-project/sglang/commit/31f24e3748da6d5bfe6fcf8c34e06f3d7d6a0bf7)

- **作者**: Mick
- **时间**: 2026-11-24T08:43:13Z
- **提交信息**: [Perf] [NVIDIA] diffusion/kernels: Look up the rounded SiLU in its table on Hopper too (#52491)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e6366d6](https://github.com/sgl-project/sglang/commit/e6366d62087df4308b598f7ed8ab57d76cc3e164)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-24T08:41:36Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main 1f8cf90a (#52550)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [049bf85](https://github.com/sgl-project/sglang/commit/049bf85d931c9633d26094ae5ff9a7dbac6723b4)

- **作者**: MatsueYu
- **时间**: 2026-11-24T08:35:36Z
- **提交信息**: [Refactor] [NPU] laser_attn: use the public sgl_kernel_npu operator entry (#52418)

### [b923ea1](https://github.com/sgl-project/sglang/commit/b923ea19b6644f55b5fcb9110c2648efa63bf861)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-24T08:25:09Z
- **提交信息**: [CI] coredump-tracker: Fail the step when the artifact listing fails, instead of posting (#52782)

### [8c0a524](https://github.com/sgl-project/sglang/commit/8c0a524b4c9853fb78fece4f9ba26966597c0233)

- **作者**: Denji-kk
- **时间**: 2026-11-24T07:55:39Z
- **提交信息**: [Perf] linker: Fill the restorable-prefix mask with one vectorized store (#49465)

Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [42c1baa](https://github.com/sgl-project/sglang/commit/42c1baa1c2557e17ca2499d2b8fbc8601bbbe220)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-24T07:48:59Z
- **提交信息**: [Doc] cookbook: Document FP32 state for Qwen3.5-122B FP8 on two H200s (#52609)

### [1936433](https://github.com/sgl-project/sglang/commit/19364330801ed22ff691a22fead35eaae779541f)

- **作者**: YAMY
- **时间**: 2026-11-24T07:16:00Z
- **提交信息**: [Fix] pp: Copy the output message's device logprob rows to the host before pickling (AsyncPP 1/9) (#52196)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7f8f135](https://github.com/sgl-project/sglang/commit/7f8f1351b820bea53b5e8305f0bcde803c067cb3)

- **作者**: Cao-Xing-Yu
- **时间**: 2026-11-24T07:05:46Z
- **提交信息**: [Perf] [NVIDIA] fused_moe: Add H20-3e Triton 3.8.0 config for E=257,N=256, tuned with real routing (#50928)

Co-authored-by: caoxingyu-cmi <caoxingyu@cmi.chinamobile.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c9c4047](https://github.com/sgl-project/sglang/commit/c9c404734f524b55329fc6146f676b596565e799)

- **作者**: DarkSharpness
- **时间**: 2026-11-24T07:00:32Z
- **提交信息**: [CI] jit: Nightly JIT kernel benchmark baseline and per-PR regression report (#52132)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5a491fb](https://github.com/sgl-project/sglang/commit/5a491fb037f1763c7c0f47bd05f58024b52bd465)

- **作者**: mugglew
- **时间**: 2026-11-24T06:59:58Z
- **提交信息**: [Fix] humming: Fix MoE finalize grid overflow (#51702)

Co-authored-by: 逸磊 <yilei.wm@antgroup.com>

### [0e9cff9](https://github.com/sgl-project/sglang/commit/0e9cff98f5b73267f7a84a034cba2668c3011ccc)

- **作者**: ashwini rathi
- **时间**: 2026-11-24T06:46:19Z
- **提交信息**: [CI] [Intel] ci/xpu: Run PR Test (XPU) every 6 hours with auto-bisect (#51251)

### [f4858fc](https://github.com/sgl-project/sglang/commit/f4858fcff9f62a957761b9e8aa18a6942c3564ec)

- **作者**: Chunan Zeng
- **时间**: 2026-11-24T06:27:29Z
- **提交信息**: [Doc] cookbook: Use one hardware id, rtxpro6000, for the RTX PRO 6000 (#51951)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yichi Zhang <109014949+Ccyest@users.noreply.github.com>

### [4b40f8c](https://github.com/sgl-project/sglang/commit/4b40f8cdf1590876c324515091ab6369cb9adc93)

- **作者**: AIbin
- **时间**: 2026-11-24T06:22:15Z
- **提交信息**: [Doc] cookbook: Point the ERNIE 5.5 Flash recipes at the Preview ckpt (#52754)

### [45dedea](https://github.com/sgl-project/sglang/commit/45dedead64817091d92cbb0af44b4239f69f8f7c)

- **作者**: jiaryang
- **时间**: 2026-11-24T06:14:58Z
- **提交信息**: [Perf] [AMD] mla: Read the fused_qkv_a slices in place in the gfx1250 q_a / kv_a RMSNorm, one launch (#49347)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>

### [6bd7db1](https://github.com/sgl-project/sglang/commit/6bd7db148b96fe98d6560785290716674c995ee1)

- **作者**: jiaryang
- **时间**: 2026-11-24T06:02:21Z
- **提交信息**: [Perf] [AMD] mla: Use the gfx950 aiter RoPE, RMSNorm and MLA KV-row paths on gfx1250 (#48154)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [369f9ae](https://github.com/sgl-project/sglang/commit/369f9ae91967024b4cd3670b2f0f8fc20ef3e812)

- **作者**: em-dreyer
- **时间**: 2026-11-24T05:59:22Z
- **提交信息**: [CI] pr-test: Allow the gated fork-PR checkout under pull_request_target (#52753)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6e31884](https://github.com/sgl-project/sglang/commit/6e31884dfcc297ac9d38c6493a239ebf4e372152)

- **作者**: Yu Song
- **时间**: 2026-11-24T05:53:07Z
- **提交信息**: [Fix] benchmark: Use current SGLang and vLLM fused MoE APIs (#52111)

### [c20d360](https://github.com/sgl-project/sglang/commit/c20d360d1b00f8e55aa59f209625dd1d370f5fdf)

- **作者**: garry569
- **时间**: 2026-11-24T05:49:52Z
- **提交信息**: [Feat] cp: Replay zigzag prefill CP breakable graph on PP stages (#51721)

Co-authored-by: garry569 <324435785+garry569@users.noreply.github.com>

### [2450a54](https://github.com/sgl-project/sglang/commit/2450a5439f184e14b8a436f212beae87aa32ddeb)

- **作者**: kangwangamd
- **时间**: 2026-11-24T05:49:16Z
- **提交信息**: [Chore] [AMD] aiter: Bump gfx1250 AITER pin to 58b435276 (#52535)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [fd7a534](https://github.com/sgl-project/sglang/commit/fd7a53408bcca69cfc173131947fe93878a470f0)

- **作者**: Kangyan-Zhou
- **时间**: 2026-11-24T05:21:33Z
- **提交信息**: [Fix] processor: render an explicit Kimi K3 tool_choice="none" without tools (#52635)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [06bfee9](https://github.com/sgl-project/sglang/commit/06bfee965f3135e183d716323b37fe6956dfc43e)

- **作者**: Shangming Cai
- **时间**: 2026-11-24T05:20:50Z
- **提交信息**: [Fix] sgl-router: Honor --cache-pending-prefix-consult-below under reorg routing (#48940)

### [30e076f](https://github.com/sgl-project/sglang/commit/30e076faf23c579af47ffe04fdfd7e363d792bc7)

- **作者**: em-dreyer
- **时间**: 2026-11-24T04:38:41Z
- **提交信息**: [CI] ci: Mask Hugging Face tokens in CUDA job logs and keep them out of lmms-eval (#52411)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2e4eebb](https://github.com/sgl-project/sglang/commit/2e4eebbc580228a41622b35b9e73b92d574b2714)

- **作者**: Yichi Zhang
- **时间**: 2026-11-24T04:25:14Z
- **提交信息**: [Doc] README: Put the adoption logo wall on a white background (#52488)

### [9f1a6dc](https://github.com/sgl-project/sglang/commit/9f1a6dca98bcafb6be68d74e2965f4129bc857c7)

- **作者**: Hubert Lu
- **时间**: 2026-11-24T04:16:21Z
- **提交信息**: [Fix] [AMD] moe: Fall back to the Triton MoE runner on gfx1250 for FP8 and BF16 experts (#52644)

### [c7bd81c](https://github.com/sgl-project/sglang/commit/c7bd81c9a57b5c43438adc78734fbda78cdf6a88)

- **作者**: AIbin
- **时间**: 2026-11-24T04:04:59Z
- **提交信息**: [Doc] cookbook: Update ERNIE 5.5 Flash for the Preview release (#52626)

### [5d14e90](https://github.com/sgl-project/sglang/commit/5d14e90ceea3c946168f91784c23cf4a508adda2)

- **作者**: 黄孝君
- **时间**: 2026-11-24T02:55:41Z
- **提交信息**: [CI] [NPU] docker: Bump SGLANG_KERNEL_NPU_TAG to post14 (#52710)

### [dacaf1d](https://github.com/sgl-project/sglang/commit/dacaf1d7135e7bcef6616a29f5c8f49759048ab3)

- **作者**: William Hu
- **时间**: 2026-11-24T02:32:43Z
- **提交信息**: [Feat] [NVIDIA] kda: Run the FlashInfer KDA prefill on SM107 (#52643)

### [1173264](https://github.com/sgl-project/sglang/commit/1173264b586a92e534f855a91e59f07644283248)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-24T02:03:55Z
- **提交信息**: [CI] pr-gate: Gate MLU and sgl-router on per-commit approval; move sgl-router to pull_request_target (#52706)

### [c559772](https://github.com/sgl-project/sglang/commit/c559772658c5ecfda30ce0958c27b44daf281aa1)

- **作者**: Denji-kk
- **时间**: 2026-11-24T01:58:28Z
- **提交信息**: [Perf] linker: Build Mooncake grouped load range metadata with numpy (#49462)

Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: alphabetc1 <2508695655@qq.com>

### [e0f9d9f](https://github.com/sgl-project/sglang/commit/e0f9d9fcbf8c04f48621da341baa1116163b3216)

- **作者**: David Tivris
- **时间**: 2026-11-24T01:35:21Z
- **提交信息**: [Fix] jit: Fix permanent cache misses behind a symlinked cache dir (#46177)

### [39f6abe](https://github.com/sgl-project/sglang/commit/39f6abefad95abfafa58939c5341cf72ca0d7a46)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-24T01:16:41Z
- **提交信息**: [CI] run-ci: Approve commits by command only, with CI_PERMISSIONS.json as the approver source; prune the file (#52690)

### [d9d6c12](https://github.com/sgl-project/sglang/commit/d9d6c12f28872b0cf3a8546fd478106a3ee94cb2)

- **作者**: em-dreyer
- **时间**: 2026-11-24T00:28:03Z
- **提交信息**: [CI] pr-test: Run on pull_request_target with a one-shot, commit-bound run-ci (#52652)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [4593b48](https://github.com/sgl-project/sglang/commit/4593b484412baff3f1d27878802ecbe6071fcac1)

- **作者**: YAMY
- **时间**: 2026-11-24T00:09:33Z
- **提交信息**: [Perf] QSA: build the extend row map from the host lengths instead of reading its size back (#50622)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1b85fbd](https://github.com/sgl-project/sglang/commit/1b85fbdb4ea3b49d68b71a890479e9117250d5af)

- **作者**: shyeh25
- **时间**: 2026-11-24T00:08:49Z
- **提交信息**: [Feat] muse_spark: Support expert TP (`--ep-size 1`) for NVFP4 checkpoints (#50065)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [e9167b2](https://github.com/sgl-project/sglang/commit/e9167b2869e148de5ed8c1e25e3b98a3760d4161)

- **作者**: Lee Nau
- **时间**: 2026-11-24T00:05:37Z
- **提交信息**: [Feat] flashinfer-autotune: Persist single-rank tactics in FlashInfer's managed v2 store (#51512)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c64f225](https://github.com/sgl-project/sglang/commit/c64f2256d58358ff65c53f0e38dc3e6bcfac8484)

- **作者**: garry569
- **时间**: 2026-11-24T00:00:36Z
- **提交信息**: [Fix] pd: Release PP prefill transfers via PP0 decision once every stage concludes (#47618)

Co-authored-by: Chao Shi <chao.shi@alibaba-inc.com>
Co-authored-by: garry569 <324435785+garry569@users.noreply.github.com>
Co-authored-by: Yangmin Li <yangminl@nvidia.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-25T02:44:13Z

## 提交统计

- **昨日提交总数**: 35
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

# vipshop/cache-dit 昨日提交分析（第 1/1 批，共 35 条）

## 1. 主要更新类型
- **性能优化**：W6A6 GEMM 内核及其 scale 访存优化、packed A4 expansion 向量化
- **功能新增**：可选 Sol-Attn 注意力后端（默认启用 prefix sink）、实验性 W3 表选择器与 packed few-shot、block-scaled MXFP6 SVDQ 内核
- **文档更新**：占比最高，包括 README 描述打磨、svdq W6A6 内核文档、nunchaku 归属范围澄清

## 2. 关键变更点及与项目方向的关系
- **MXFP6 SVDQ W6A6 GEMM（#1391）** 是本批最核心的功能提交：两操作数以 E2M3 打包、每 32 个 K 元素一个 UE8M0 micro-scale，直接喂给 `mma.sync...block_scale` 指令，mainloop 全程不做逐块提升/重缩放；配套 fused producer（打包激活 + 32 宽 scale 行 + BF16 LoRA-down 一次写入、split-K 归约）、TMA 16U6 staging、SU6 LDSM 展开、双缓冲 scale 预取、fused BF16 LoRA-up/bias epilogue。这直接对应 README 中"Quantization"这一核心卖点，把 SVDQ 量化谱系从 W8A8 扩展到更省显存的 W6A6。
- **Sol-Attn 后端（#1398）** 对应 README 的"Cache/注意力加速"方向，提供可选注意力后端并默认开启 prefix sink，属于注意力机制侧的能力扩展。
- **W3 表选择器、packed few-shot、A4 向量化（#1394/#1393）** 是量化精度/速度维度的持续迭代（SVDQ 实验分支）。
- 大量 README 微调（#1399/#1397 及十余条零散提交）集中打磨 Cache-DiT 描述、量化选项措辞与格式，反映项目正在强化对外呈现。

## 3. 对项目的影响和潜在意义
- W6A6 相比 W8A8 **体积缩小 25%**，FLUX.1-dev 1024×1024 实测质量提升 **2.4–3.6 dB**（24.77 dB / 0.942 vs 22.35 dB / 0.926），推理开销仅小幅增加（13.21s vs 10.19s eager，9.48s vs 8.23s compiled），为 DiT 推理在消费级/工作站 GPU 上的显存受限场景提供了新的质量-体积权衡点。
- NCU 驱动的第二轮优化（scale 访存合并、producer 融合）解决了 mainloop 饥饿问题（tensor pipe 70% vs W8A8 的 84%），说明该内核已进入"可交付性能"阶段而非原型。
- Sol-Attn 与 W3/packed-A4 实验功能表明项目在**注意力后端和量化精度**两条线上同时布局，验证多方案后择优固化。

## 4. 值得关注的技术点
- **UE8M0 micro-scale 直通 block-scale MMA**：scale 行经 `make_zip_tensor` 进入 SFA/SFB fragment，避免逐块重缩放，FP32 二级 scale 降级为 epilogue-only。
- **Tile-blocked scale 布局**（[row/128][K-tile][...]）替代 row-major，解决 128 行 CTA tile 触碰 128 条 cache line 只换取 512 有用字节的 L1TEX 瓶颈（63.6%）。
- **代码归属治理**：svdq.h 收窄 nunchaku 声明范围，仅 native/ 子树保留衍生物并列明差异（共享 INT4/NVFP4 族、fused MLP、量化平滑输出 epilogue、packed W1/W2/W3 解码器、row-major LoRA 布局），是开源合规的规范做法。
- 全量测试覆盖（code-book 位序、UE8M0 最小性、residual 重建、producer vs torch 参考、rank 0/32/64/128 GEMM 一致性、fullgraph compile）保证内核可回归。

## 5. 对项目发展的整体影响
结合 README 定位（PyTorch 原生 DiT 推理引擎，主打 Cache、Parallelism、Quantization、CPU Offload），本批提交使**量化维度显著加深**：W6A6 从内核、Python API（`svdq_fp6_r*`、SVDQW6A6Linear）、DQ/PTQ/checkpoint 流程到 CLI 预设与文档形成闭环，强化了 cache-dit 作为"量化能力最完整的 DiT 推理引擎"的差异化定位；Sol-Attn 扩充了注意力/缓存侧选项；而占比较高的文档打磨则显示项目正为更广泛的用户采用做准备。综合看，项目正从"功能铺开"阶段进入"内核性能调优 + 生态呈现"并重的成熟期，下一步大概率是将实验性 W3/packed-A4 方案与 Sol-Attn 在更多模型上验证后转正。

## 详细提交记录

### [05cd864](https://github.com/vipshop/cache-dit/commit/05cd8644b10cdab307684a3e52558fbe16f22ca4)

- **作者**: DefTruth
- **时间**: 2026-11-24T12:10:30Z
- **提交信息**: chore(docs): update README (#1399)

* update docs

* Update README.md

* Update README.md

* Update README.md

* Fix capitalization in Cache-DiT description

Corrected capitalization in the description of Cache-DiT.

* Fix attention acceleration terms in README

Updated the description of Cache-DiT to correct 'attention acceleration' terms.

* Fix formatting in README.md for Cache-DiT description

* Revise Cache-DiT description in README

Updated the description of Cache-DiT to include new terms and corrections.

* Update README.md

* Update README.md

* Enhance README with emoji for attention acceleration

Updated README to include an emoji in the attention acceleration section.

### [2e44e63](https://github.com/vipshop/cache-dit/commit/2e44e63a4990fabab979a1a26a9667a59207b765)

- **作者**: DefTruth
- **时间**: 2026-11-24T11:30:22Z
- **提交信息**: feat: add optional Sol-Attn attention backend (#1398)

* feat: add Sol-Attn attention backend

* feat: enable Sol-Attn prefix sink by default

* docs: remove duplicate Sol-Attn matrix

### [b75e1cd](https://github.com/vipshop/cache-dit/commit/b75e1cd8986175e8ef910d89a971765e15c0ee44)

- **作者**: DefTruth
- **时间**: 2026-11-24T07:24:19Z
- **提交信息**: chore: udpate docs (#1397)

* Update README.md

* Fix formatting in README.md for Cache-DiT description

### [71a4706](https://github.com/vipshop/cache-dit/commit/71a47063e46e9f5c955147bc3e32b172a49b6942)

- **作者**: DefTruth
- **时间**: 2026-11-24T06:29:29Z
- **提交信息**: docs(svdq): document the W6A6 kernels and scope the nunchaku attribution (#1396)

svdq.h no longer claims to be adapted from nunchaku at the file level:
only the native/ subtree still derives from nunchaku/src/kernels/zgemm,
and the header now says so in the native section together with what has
diverged since (shared INT4/NVFP4 family, fused MLP, quantized and smooth
output epilogues, packed W1/W2/W3 decoders, row-major LoRA layout).

Adds the fp6 entries to the source map (gemm_w6a6 with its sf_partition
helpers and tile-blocked scale layout, the fused quantize_w6a6 producer
and its rank-specialized instantiations) and a W6A6 line to the selection
summary.

Co-authored-by: DefTruth <yanjun.qiu@vipshop.com>

### [127e760](https://github.com/vipshop/cache-dit/commit/127e760d5dfcb63b315fec39ea0390a8552b5846)

- **作者**: DefTruth
- **时间**: 2026-11-24T05:34:09Z
- **提交信息**: feat(kernel): block-scaled MXFP6 SVDQ W6A6 GEMM and producer (#1391)

* feat(kernel): add block-scaled MXFP6 SVDQ W6A6

Both operands are packed E2M3 with one UE8M0 micro-scale per 32 K
elements, consumed directly by
`mma.sync.aligned.kind::mxf8f6f4.block_scale.scale_vec::1X.m16n8k32`
(e2m3.e2m3). The scale rows are loaded into the atom's SFA/SFB fragments
and reach the MMA through make_zip_tensor, so the mainloop never promotes
or rescales per block, and the FP32 second-level scales stay optional and
epilogue-only.

- csrc/kernels/svdq/cute/fp6/gemm: TMA 16U6 staging of packed 6-bit codes,
  SU6 LDSM expansion into 8-bit containers, double-buffered scale prefetch,
  fused BF16 LoRA-up and bias epilogue.
- csrc/kernels/svdq/cute/fp6/quantize: fused producer that writes the
  packed activation, its 32-wide block-scale row and the BF16 LoRA-down
  term in one pass, with split-K D reduction.
- Python: `svdq_fp6_r{32|64|128}[_dq]` (alias `svdq_w6a6_*`), SVDQW6A6Linear,
  DQ/PTQ/checkpoint plumbing through the shared SVDQ flow, generate CLI
  presets and quantization docs.
- tests/kernels/test_svdquant_w6a6.py: code-book and packing bit order,
  UE8M0 minimality, residual reconstruction, producer vs torch reference,
  GEMM parity for rank 0/32/64/128, module wiring and fullgraph compile.

Measured on RTX PRO 5000 (torch 2.15.0+cu132), FLUX.1-dev 1024x1024 28 steps:
W6A6 is 25% smaller than W8A8 and 2.4-3.6 dB closer to bf16 (24.77 dB /
0.942 vs 22.35 dB / 0.926), at 13.21 s vs 10.19 s eager and 9.48 s vs
8.23 s compiled.

* perf(kernel): coalesce W6A6 scale traffic and fuse the producer

NCU on the first W6A6 kernel showed the mainloop starving (tensor pipe
70% vs 84% for W8A8) with L1TEX at 63.6%: the UE8M0 scale rows were read
one byte per thread per 32-wide group from a row-major [rows, K/32]
layout, so a 128-row CTA tile touched 128 cache lines for 512 useful
bytes, and the B-side scales were re-read by every M warp.

- Store scales tile-blocked ([row/128][K-tile][row%128][group], 512 B per
  tile) so a CTA tile's scales are contiguous, and read a row's four
  scales with one vectorized LDG.32 instead of four LDG.8. The producer
  writes the same layout; `block_sf`/`deblock_sf` cover the Python side.
- Prefetch the next K tile's scales into a second fragment set; the
  buffer choice stays a compile-time branch so nothing lands in local
  memory.
- Fold the block-amax pass into the quantization kernel: a 32-wide scale
  group is owned by four consecutive lanes, so two XOR shuffles produce
  the exponent without a second activation read or kernel launch.
- Merge sf_partition.cuh into gemm_w6a6.cuh.

Measured on RTX PRO 5000 (torch 2.15.0+cu132), CUDA events, warmup 10 /
iters 50:

  GEMM 4096x3072x12288: 1211 -> 718 us (W8A8 711 us, was 1.69x)
  GEMM 4096x12288x3072: 866 -> 809 us (W8A8 766 us, was 1.13x)
  producer r32: 55 -> 48 us (W8A8 31 us)

FLUX.1-dev 1024x1024 28 steps, same host and seed as the base PR:

  W6A6 eager 13.21 -> 10.51 s (W8A8 10.07 s), PSNR 26.78 dB / SSIM 0.948
  W6A6 compile 9.48 -> 8.54 s (W8A8 8.08 s), PSNR 26.62 dB / SSIM 0.951

Rejected after measurement: cooperative smem staging of the scale tiles
with a per-tile NamedBarrier (1.24-1.31x slower than W8A8, because the
barrier plus cp.async.wait_group serializes the consumer warps).

* perf(kernel): vectorize W6A6 scale loads and producer stores

Two measured follow-ups to the scale-traffic fix:

- Fetch scales with LDG.128. The scale tiles now use CUTLASS's SfAtom
  interleave (16*(row%32) + 4*((row/32)%4)) inside each 512 B tile: a
  thread's two A rows sit 8 bytes apart in one aligned 16 B block and its
  eight B columns form two contiguous 16 B regions. The mainloop therefore
  issues three vector loads plus register moves instead of ten LDG.32, and
  the offsets are computed once per thread from the SF coordinate
  partition. `block_sf`/`deblock_sf` use the same permutation.
- Produce 16 elements per thread in the activation quantizer, so the
  packed output is written as three aligned 32-bit stores instead of three
  16-bit stores per eight elements. A 32-wide scale group is then two
  lanes, which also shortens the amax reduction to one XOR shuffle.

Producer drops 48.0 -> 35.4 us (W8A8 31.0 us). FLUX.1-dev 1024x1024 28
steps on the same RTX PRO 5000:

  W6A6 eager 10.51 -> 10.42 s (W8A8 10.07 s)
  W6A6 compile 8.54 -> 8.47 s (W8A8 8.08 s)

The remaining GEMM gap is not scale loads: after this change the kernel
still issues 1.56x the instructions of W8A8, and SASS shows the excess in
MOV/LOP3/SHF around the SU6 LDSM fragments (register rearrangement
between the unpacked 6-bit fragment layout and the MMA operand layout),
not in the scale path.

---------

Co-authored-by: DefTruth <yanjun.qiu@vipshop.com>

### [24af145](https://github.com/vipshop/cache-dit/commit/24af145679e759d9fb6e6a45c9a5430bc4a2c299)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:46:12Z
- **提交信息**: Merge pull request #1395 from vipshop/dev

chore: update docs

### [2edfbd8](https://github.com/vipshop/cache-dit/commit/2edfbd82b6c6694b9fc4aa3ffe620d5766198503)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:43:02Z
- **提交信息**: Update README.md

### [342355c](https://github.com/vipshop/cache-dit/commit/342355caf5904a6a24ba656b420abce96b3e36d4)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:41:51Z
- **提交信息**: Enhance Cache-DiT description with 'etc' for clarity

Updated the description of Cache-DiT to include 'etc' for parallelism.

### [5f65cca](https://github.com/vipshop/cache-dit/commit/5f65cca4b03169edc0a8e1b53da42aa0aca2e192)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:41:27Z
- **提交信息**: Update README.md

### [0cb3e95](https://github.com/vipshop/cache-dit/commit/0cb3e959f360a70fc66fbd4086c0551a80b68cd5)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:40:48Z
- **提交信息**: Refine description of Cache-DiT features

Removed redundant 'etc' from quantization and parallelism descriptions.

### [3f696c1](https://github.com/vipshop/cache-dit/commit/3f696c1d5c5a9936d0510e8c13ca300767760fea)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:40:02Z
- **提交信息**: Enhance README description for Cache-DiT

Updated the README to include 'etc' in the parallelism section.

### [e630172](https://github.com/vipshop/cache-dit/commit/e630172eac33b2a84d2d830ae29648e52c904972)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:39:29Z
- **提交信息**: Update README.md

### [036c859](https://github.com/vipshop/cache-dit/commit/036c859e5896576dbab20d0ca8f4a282bad274c4)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:38:22Z
- **提交信息**: Fix formatting in README.md for Cache-DiT description

### [ec6d3e8](https://github.com/vipshop/cache-dit/commit/ec6d3e8df805f93fc67f8f3049ae38da532dea25)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:38:05Z
- **提交信息**: Update README.md

### [28cd155](https://github.com/vipshop/cache-dit/commit/28cd155b119e249d4d261ce751afd5142a47ca8f)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:37:30Z
- **提交信息**: Update README.md

### [e083d66](https://github.com/vipshop/cache-dit/commit/e083d66222df1c9c5e94013fca129a8aae3d2712)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:36:16Z
- **提交信息**: Update README.md

### [a890baf](https://github.com/vipshop/cache-dit/commit/a890baf3394adb3bff7e9e57484803c4822e60a7)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:35:14Z
- **提交信息**: Fix formatting in Cache-DiT description

Corrected formatting in the description of Cache-DiT.

### [e9258c5](https://github.com/vipshop/cache-dit/commit/e9258c526ad5dba68eddf51dcefdb87df2396fd3)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:33:33Z
- **提交信息**: Update README.md

### [1c138ee](https://github.com/vipshop/cache-dit/commit/1c138ee97c3cbfba16d60023db400e9448e785e3)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:33:14Z
- **提交信息**: Fix formatting issues in README.md

### [0f2410b](https://github.com/vipshop/cache-dit/commit/0f2410b78c341fe4444d2e5f2a46ac61d92aa949)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:32:36Z
- **提交信息**: Update README.md

### [1cda33a](https://github.com/vipshop/cache-dit/commit/1cda33a2f009e9a4869acea9a86fd7ac7dc28589)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:31:21Z
- **提交信息**: Update README.md

### [e5f0d3b](https://github.com/vipshop/cache-dit/commit/e5f0d3b3186d5a555705d13c62d54866c1e5e8fb)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:30:54Z
- **提交信息**: Update README.md

### [0fe6fe7](https://github.com/vipshop/cache-dit/commit/0fe6fe79bcb09d0f5ac2074baad4e7948eb7c43d)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:30:10Z
- **提交信息**: Update README.md

### [85880e3](https://github.com/vipshop/cache-dit/commit/85880e33f3fedf1acb234e3fd5728d01c9a57b2a)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:29:40Z
- **提交信息**: Fix quantization options formatting in README

Corrected the formatting of quantization options in the README.

### [f452ee7](https://github.com/vipshop/cache-dit/commit/f452ee75fa569d706f98a7aa952cf4a555d5751e)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:29:15Z
- **提交信息**: Update README.md

### [ca6fa6d](https://github.com/vipshop/cache-dit/commit/ca6fa6dc57334855a41ce99f66b4bf110e34e0c2)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:28:24Z
- **提交信息**: Reorder quantization terms in README

Updated the quantization section to reorder terms for clarity.

### [5d2ad5b](https://github.com/vipshop/cache-dit/commit/5d2ad5b5752cf8f1bfb944eb403dcdd40d636d26)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:27:52Z
- **提交信息**: Update README.md

### [f360408](https://github.com/vipshop/cache-dit/commit/f360408d2f3a73c2301c93c8d849b52f1374c2aa)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:20:11Z
- **提交信息**: Merge pull request #1394 from vipshop/feat/packed-a4-experiments

feat(svdq): experimental W3 table selector and packed few-shot

### [90b79f2](https://github.com/vipshop/cache-dit/commit/90b79f2c6a3858b48fd6f7646d4014a3f9a2bdd8)

- **作者**: DefTruth
- **时间**: 2026-11-24T04:13:42Z
- **提交信息**: Merge pull request #1393 from vipshop/perf/wna4-e2e

perf(svdq): vectorize packed A4 expansion

### [39a1710](https://github.com/vipshop/cache-dit/commit/39a17105cfe7055e01b3e1ff20b740505da583e4)

- **作者**: DefTruth
- **时间**: 2026-11-24T03:48:02Z
- **提交信息**: docs(svdq): explain packed A4 stage defaults

### [b361535](https://github.com/vipshop/cache-dit/commit/b361535c91f23a50a374df08887d88c6a5e9e77f)

- **作者**: DefTruth
- **时间**: 2026-11-24T03:44:48Z
- **提交信息**: docs(svdq): escape pipes in quant type table

### [b314acc](https://github.com/vipshop/cache-dit/commit/b314acc358ae85b40eda041fcaaf48892ac217c3)

- **作者**: DefTruth
- **时间**: 2026-11-24T03:42:09Z
- **提交信息**: docs(svdq): show W3 stage2 versus stage3 comparison

### [61006ba](https://github.com/vipshop/cache-dit/commit/61006bac1f446e9f560b3963490df5b009ce3e50)

- **作者**: DefTruth
- **时间**: 2026-11-24T03:40:58Z
- **提交信息**: docs(svdq): add W3 stage3 visual comparison

### [8881521](https://github.com/vipshop/cache-dit/commit/8881521cd72cdd1aa8d5aa4245f892c7ea143fc6)

- **作者**: DefTruth
- **时间**: 2026-11-24T03:32:33Z
- **提交信息**: feat(svdq): add experimental W3 table selector and packed few-shot

### [e755134](https://github.com/vipshop/cache-dit/commit/e7551346ac31c41d54bc4f403fdadb1bfe39b14a)

- **作者**: DefTruth
- **时间**: 2026-11-24T02:53:07Z
- **提交信息**: perf(svdq): vectorize packed A4 expansion

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97517
- **最后更新**: 2026-11-25T04:31:35Z

## 提交统计

- **昨日提交总数**: 96
- **提交者数量**: 69
- **主要提交者**: Bandham Manikanta, Jee Jee Li, KathanSheth

## AI分析总结

# vLLM 昨日 96 个提交分析总结

## 1. 主要更新类型
以**Bug 修复**（约 35%）和**性能优化**（约 25%）为主，其次是**新模型/后端支持**（约 20%）、CI 与基础设施改进、重构清理、文档更新及安全加固。

## 2. 关键变更点及与项目方向的关系
- **Transformers 后端迁移**是主线之一：批量迁移 SarvamMLA/MoE、InternLM3、EXAONE 3、GPT-J、OmniASR、Youtu-LLM 等模型，并新增对 ERNIE 5.5、Nemotron VL 的支持，同时修复 MLA 自动检测（按 latent 形状识别）、MoE 门控 dtype、检查点张量拆分转换等问题，持续扩大官方模型覆盖面。
- **Rust 前端持续打磨**：支持 DeepSeek V4 后缀、Mistral v11 工具调用解析、UTF-8 SSE 类型、词表边界校验、多模态 fail-fast、提升文件描述符限制等，为默认启用铺路。
- **解析器性能**（工具调用/结构化输出）多次线性时间优化、单次遍历与分层解析（GLM-4.7、增量 lexer），降低流式解析开销，契合"快"的核心卖点。
- **内核级性能深耕**：FlashInfer CuTe-DSL 非量化 MoE（SM90）、原生小头 FlashMLA、SM100 skinny GEMM 计划、MoE 排序融合、Triton KV 向量化、RDNA 小 tile 预填充、MiniCPM-V varlen attention 等，针对不同 GPU 架构精细调优。
- **多硬件生态扩展**：Intel XPU 实现无状态分布式初始化与序列+流水线并行组合，ROCm 调优 QSA 稀疏 GQA 与 MI355X 配方，CPU 端修复 DeepSeek-V4 调度器。
- **权重传输与 RL 链路加固**：修复 ShardedRDT 传输死锁，新增 Connex 权重传输后端，在 finish_weight_update 中校验权重基线，表明 RL/在线训练正成为一等公民。
- **Bug 修复覆盖核心路径**：KV 卸载、DSA 索引器、配置缓存、ThreadPoolExecutor 死锁、P2P no-op 任务、驻留页回收、n>1 prefill 兄弟缓存命中统计等。
- **启动与缓存优化**：Inductor/Dynamo 延迟导入、compile cache key 剔除宿主字段，改善冷启动与缓存命中率。
- **依赖与技术债**：移除 LM Format Enforcer 后端、升级 Transformers 至 5.24.1、清理死代码、启用 mypy 类型检查。
- **CI 提速**：Arm 测试分片（20.5→15.5 分钟）、自动分片默认开启、auto-rebase 忽略状态、可复用 vllm-runners 工作流。
- **安全**：限制媒体预处理量、包含 Sentence Transformers 模块文件。

## 3. 对项目的影响与潜在意义
模型兼容面扩大降低迁移成本；解析与内核优化直接改善高并发流式延迟与单位推理成本；死锁/内存/指标类修复提升生产可靠性；CI 提速保障高并发贡献下的稳定演进；新增 API server committer 体现社区治理扩展。

## 4. 值得关注的技术点
按 latent 形状自动识别 MLA 与检查点张量拆分，使 Transformers 后端覆盖非常规模型结构；HiSparse 复用已结束请求的 GPU 拷贝与多节点共享 host pool，体现稀疏注意力的显存复用策略；压缩感知/稀疏场景（DSA 索引器、HiSparse、PCP）进入修复深水区，说明新特性正快速收敛；大量提交由 Claude、Codex、Copilot 等 AI 代理联合署名，反映 AI 深度参与内核与 CI 开发。

## 5. 结合项目背景的影响
README 强调"人人可用的快速、廉价 LLM 服务"。本批提交通过更多模型与后端可用性、解析与内核性能提升、安全与稳定性修复、Rust 前端与类型检查推动架构现代化，在**易用性、速度、成本**三个维度同步推进；RL 权重传输与校验则把 vLLM 从纯推理引擎推向"推理+在线学习"一体化平台，为其保持高性能开源推理引擎领先地位奠定基础。

## 详细提交记录

### [fb15924](https://github.com/vllm-project/vllm/commit/fb159244e6fdd0b2ecd9d62855cae9a2d282ae87)

- **作者**: Harry Mellor
- **时间**: 2026-11-24T23:50:46Z
- **提交信息**: [Transformers backend] Migrate SarvamMLA and SarvamMoE (#68728)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [97245ef](https://github.com/vllm-project/vllm/commit/97245ef4e5764a99ab2933bffe71f907fcedaadb)

- **作者**: seungrokj
- **时间**: 2026-11-24T23:14:09Z
- **提交信息**: [ROCm][Docs] DeepSeek-V4.1-Flash: MI355X AgentX TP and DP presets from InferenceX #5195 (#69752)

Signed-off-by: seungrokj <seungrok.jung@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [32e14df](https://github.com/vllm-project/vllm/commit/32e14dfc397ffc9c3d6b9a51cc976e3e880fccea)

- **作者**: seungrokj
- **时间**: 2026-11-24T23:13:02Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: MI355X kimi-k31-020490a image (amd_kernels bridge) and FlyDSL draft attention, align with InferenceX#5196 (#69749)

Signed-off-by: seungrokj <seungrok.jung@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [38e4d7a](https://github.com/vllm-project/vllm/commit/38e4d7ac17878b8006a21af1e56cfcf6d4ecc316)

- **作者**: Maroon Ayoub
- **时间**: 2026-11-24T23:00:21Z
- **提交信息**: [Perf][Parser] Skip streaming argument deltas in a single-pass parse (#69636)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [8d232b0](https://github.com/vllm-project/vllm/commit/8d232b04a616acc1e24c4b05da4d50a11d9220eb)

- **作者**: Maroon Ayoub
- **时间**: 2026-11-24T23:00:05Z
- **提交信息**: [Perf][Parser] Drain the incremental lexer in linear time (#69500)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [9bb2b59](https://github.com/vllm-project/vllm/commit/9bb2b593b92bc309c71b8eb78878b82dd27c1079)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-24T22:32:46Z
- **提交信息**: [Deprecation] Remove LM Format Enforcer structured outputs backend (#69564)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [048e791](https://github.com/vllm-project/vllm/commit/048e79116bea75ac5f17ef4f3fd667081382a417)

- **作者**: Johnny-Liou
- **时间**: 2026-11-24T22:18:57Z
- **提交信息**: [Kernel] ReplaySSM: cache SSM inputs for faster Gated DeltaNet standard decode (#62004)

Signed-off-by: Johnny-Liou <a897111@gmail.com>
Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>

### [55dd36c](https://github.com/vllm-project/vllm/commit/55dd36c27843964c25948d1d860c5e85d0a75e20)

- **作者**: Harry Mellor
- **时间**: 2026-11-24T22:14:40Z
- **提交信息**: [CI] Fix mypy errors in tests/v1/core and tests/v1/engine (#69751)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f214e0d](https://github.com/vllm-project/vllm/commit/f214e0d4cdbf2305c0a0d131e5ff100f56a41347)

- **作者**: Jongsu Liam Kim
- **时间**: 2026-11-24T22:01:56Z
- **提交信息**: [Bugfix][Distributed]  Gate MNNVL allreduce workspace creation on fabric support (#53377)

Signed-off-by: Jongsu Liam Kim <jongsukim8@gmail.com>
Signed-off-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3ef6b78](https://github.com/vllm-project/vllm/commit/3ef6b78dc3e01bd3e47a4b5ab61aef861b3c56e0)

- **作者**: Bandham Manikanta
- **时间**: 2026-11-24T21:26:17Z
- **提交信息**: [MoE] Use sorted fused-MoE path on integrated GPUs for multi-token batches (#63943) (#64163)

Signed-off-by: Manikanta Bandham <bandham.manikanta@gmail.com>
Signed-off-by: Manikanta Bandham <bandhammanikanta@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [b321d66](https://github.com/vllm-project/vllm/commit/b321d66fc8170f351bd3cff0685b0e381b71eb60)

- **作者**: El-euchidali
- **时间**: 2026-11-24T21:11:50Z
- **提交信息**: [Model] Support OmniASR via the Transformers backend (#69683)

Signed-off-by: Mohamed Ali El Euchi <316735094+El-euchidali@users.noreply.github.com>

### [8782331](https://github.com/vllm-project/vllm/commit/8782331b3bc95eed6612aa55a99f2a03285c4799)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-24T21:08:42Z
- **提交信息**: [HiSparse] Reuse finished requests' GPU copies before cached prefixes (#68820)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vMaroon <vMaroon@users.noreply.github.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Antigravity <noreply@google.com>

### [84981aa](https://github.com/vllm-project/vllm/commit/84981aa792dac06677d516f68551e12e56f5bc77)

- **作者**: Harry Mellor
- **时间**: 2026-11-24T20:40:27Z
- **提交信息**: [Transformers backend] Migrate InternLM3, IQuestCoder, EXAONE 3 and GPT-J (#66416)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [52c0d60](https://github.com/vllm-project/vllm/commit/52c0d6007cef8b0b5216891116272da03db2e6e7)

- **作者**: Ashraf Bhuiyan
- **时间**: 2026-11-24T20:35:44Z
- **提交信息**: [CI] Enable mypy for tests/v1/core and tests/v1/engine (#65740)

Signed-off-by: Ashraf Bhuiyan <mbhuiyan@redhat.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [212446e](https://github.com/vllm-project/vllm/commit/212446ea87baf1261d5016c353d56c85b1d5e468)

- **作者**: Maroon Ayoub
- **时间**: 2026-11-24T20:28:41Z
- **提交信息**: [Perf][Parser] Find GLM-4.7 tool-call arguments in linear time (#69637)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [e66bede](https://github.com/vllm-project/vllm/commit/e66bede56be433f55c936db3ea80864492c296fe)

- **作者**: Devanshi Jain
- **时间**: 2026-11-24T19:39:28Z
- **提交信息**: [Bugfix] Don't report sibling cache hits in n>1 prefill stats (#66720)

Signed-off-by: Devanshi Jain <devanshijain@meta.com>
Co-authored-by: Mark McLoughlin <markbmc@gmail.com>

### [b90597b](https://github.com/vllm-project/vllm/commit/b90597b7581c099888c699897b581306ecffa1bf)

- **作者**: Harry Mellor
- **时间**: 2026-11-24T18:56:15Z
- **提交信息**: [Transformers backend] Apply checkpoint conversions that split a tensor (#69695)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9c9e9d3](https://github.com/vllm-project/vllm/commit/9c9e9d3fbb63a369ed9c82981da80f5116b9eaec)

- **作者**: ziruil
- **时间**: 2026-11-24T18:56:08Z
- **提交信息**: [Bugfix][Core] Avoid initializing CUDA while resolving AllReduce+RMSNorm fusion config (#56239)

Signed-off-by: ziruil <ziruil@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [ba4b266](https://github.com/vllm-project/vllm/commit/ba4b266dfadbf231eb89b0b689e86b6854567bb8)

- **作者**: Harry Mellor
- **时间**: 2026-11-24T18:31:36Z
- **提交信息**: [CI] Bump Transformers version to 5.24.1 (#69129)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e261775](https://github.com/vllm-project/vllm/commit/e261775655ce0b88420dae3d28869b76d2109dfa)

- **作者**: Bugen Zhao
- **时间**: 2026-11-24T18:28:53Z
- **提交信息**: [Rust Frontend] Fail at launch for multimodal models the Rust frontend cannot serve (#68912)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b87e6a6](https://github.com/vllm-project/vllm/commit/b87e6a65e8ce41623604067b5a413a1f80a129c7)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-24T18:21:38Z
- **提交信息**: [HiSparse] Share the host pool per node under multi-node TP (#68747)

### [57a417a](https://github.com/vllm-project/vllm/commit/57a417ad01995dcf130c346a7606230ce01d7049)

- **作者**: Mingi Jeong
- **时间**: 2026-11-24T18:21:23Z
- **提交信息**: [Bugfix] Fix collect_env.py crash on non-Linux platforms (#48354)

Signed-off-by: jeongmingi <incheonkirin@gmail.com>

### [e207b0f](https://github.com/vllm-project/vllm/commit/e207b0fcceb990a2801cf0ccfae4858672447b1f)

- **作者**: Thang Nguyen
- **时间**: 2026-11-24T18:06:43Z
- **提交信息**: [CI] Run (H200) EC Filesystem Tiering on a 35GB MIG slice (#69693)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4f01a46](https://github.com/vllm-project/vllm/commit/4f01a462682e56d765f26d4e4b288252e396cffb)

- **作者**: Jiangyun Zhu
- **时间**: 2026-11-24T18:04:33Z
- **提交信息**: [Core] Remove dead pcp_world_size plumbing from KV cache managers (#69706)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Antigravity <noreply@google.com>

### [3a5ae75](https://github.com/vllm-project/vllm/commit/3a5ae75953d5c465a57c04586d7f5d11c96fefcf)

- **作者**: James E T Smith
- **时间**: 2026-11-24T18:03:27Z
- **提交信息**: [Model][ROCm] Hy4 and Hy4-Flash enablement and recipe on ROCm (#68839)

Signed-off-by: jamesETsmith <james.smith9113@gmail.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <AndreasKaratzas@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <AndreasKaratzas@users.noreply.github.com>

### [d99aa11](https://github.com/vllm-project/vllm/commit/d99aa11e6be7fcfbcde07ed3fc894a3ec923f65f)

- **作者**: Sherif Waly
- **时间**: 2026-11-24T17:57:26Z
- **提交信息**: [Core][KV Cache] Fail fast when explicit prefix_match_unit falls back to whole-block hits (#68934)

Signed-off-by: Sherif Waly <sherif.waly@mistral.ai>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Antigravity <noreply@google.com>

### [850fd21](https://github.com/vllm-project/vllm/commit/850fd21d75236227d280e28842f0b3c4dd0f6741)

- **作者**: Vyomakesh
- **时间**: 2026-11-24T17:41:39Z
- **提交信息**: [Model] Decouple Afmoe, Jamba and IQuestLoopCoder from llama.py (#69703)

Signed-off-by: vyomakesh0728 <dvyomkesh.vishwakarma@gmail.com>
Co-authored-by: Antigravity <noreply@google.com>

### [f66a40c](https://github.com/vllm-project/vllm/commit/f66a40cb3918d4ae6b69e5875e32ca05c3910639)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-24T17:08:40Z
- **提交信息**: [Cleanup] Bump ROCm gfx1250 to torch 2.12 and remove workarounds for torch <= 2.12 (#69572)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Wittachai <100832588+wittachai-as@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [65ada0c](https://github.com/vllm-project/vllm/commit/65ada0c40e18d1100deee9c3deb351326a309e82)

- **作者**: Harry Mellor
- **时间**: 2026-11-24T16:31:45Z
- **提交信息**: [Transformers backend] Detect MLA from the latent shape and support Youtu-LLM (#69689)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0772d29](https://github.com/vllm-project/vllm/commit/0772d298483a0578a747fd91a8278d511628373b)

- **作者**: Jee Jee Li
- **时间**: 2026-11-24T16:17:46Z
- **提交信息**: [CI/Build] Remove synthetic LoRA model tests (#69697)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [7427cda](https://github.com/vllm-project/vllm/commit/7427cda482c6e9f54c3cc8d9db93e953a657f678)

- **作者**: Dundy Pasupuleti
- **时间**: 2026-11-24T16:16:45Z
- **提交信息**: [Bugfix][Model Loader] Warn when ignoring an unindexed model.safetensors (#67062)

Signed-off-by: Dundy Pasupuleti <dundysm@gmail.com>

### [650054d](https://github.com/vllm-project/vllm/commit/650054dc65a64a624eb41a068a8e3ce739533e93)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-24T16:13:07Z
- **提交信息**: [Security] Contain Sentence Transformers module files (#61430)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>

### [1edf0da](https://github.com/vllm-project/vllm/commit/1edf0da10307e6f7d07a61cd6eb5943e10de9c14)

- **作者**: Avishek Goswami
- **时间**: 2026-11-24T16:09:51Z
- **提交信息**: [Feature][Quantization] Rewrite compressed-tensors regex targets on load (#66342)

### [f89471b](https://github.com/vllm-project/vllm/commit/f89471b21e5f18efc4b79a8b25d14979a1b7cebe)

- **作者**: Misha Goin
- **时间**: 2026-11-24T16:07:47Z
- **提交信息**: [Kernel] Fix the bad fallback config in the ll_fp32w router GEMM (#68755)

### [c77fabb](https://github.com/vllm-project/vllm/commit/c77fabb0fd769b024dcd271f0591e16626061a62)

- **作者**: Harry Mellor
- **时间**: 2026-11-24T16:07:06Z
- **提交信息**: [Transformers backend] Keep MoE gates in the dtype Transformers builds them in (#69673)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [eb42ba6](https://github.com/vllm-project/vllm/commit/eb42ba633eec9453f161e33494ae49d0284b12f2)

- **作者**: Jeremiah Hu
- **时间**: 2026-11-24T15:00:11Z
- **提交信息**: [Perf][Attention] Vectorize per-token-head KV tile loads in Triton attention (#69170)

Signed-off-by: Jeremiah-HL <1963569247@qq.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bdd3d78](https://github.com/vllm-project/vllm/commit/bdd3d787ae663e31299facff453323f74a92e751)

- **作者**: KathanSheth
- **时间**: 2026-11-24T14:45:20Z
- **提交信息**: [Bugfix] Fix /classify for per-position seq-cls heads on the Transformers backend (#69196)

Signed-off-by: Kathan Sheth <sheth.kathan92@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [31814a6](https://github.com/vllm-project/vllm/commit/31814a6f6f2d24b2bebebd7c94181c02ae51cef7)

- **作者**: Yunzhu Lu
- **时间**: 2026-11-24T14:17:25Z
- **提交信息**: [Perf][MM] Use varlen attention in MiniCPM-V vision encoder (#69136)

Signed-off-by: YunzhuLu <lucia.yunzhu@gmail.com>

### [03a905b](https://github.com/vllm-project/vllm/commit/03a905b941a204732d4f24e76d68a8f8cf4983cb)

- **作者**: Louie Tsai
- **时间**: 2026-11-24T14:07:39Z
- **提交信息**: [Recipes][XPU] Add validated 8192-token context defaults for some Qwen, Nemotron-3-Nano,  and GPT-OSS models on Arc Pro B60/B70 (#68901)

Signed-off-by: louie-tsai <louie.tsai@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [880c632](https://github.com/vllm-project/vllm/commit/880c63222bbf9522e115c34418f1e8039e6ee40c)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-24T13:46:40Z
- **提交信息**: [Security] Bound media preprocessing per prompt (#69098)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [bd1ebab](https://github.com/vllm-project/vllm/commit/bd1ebabfd95fb5a3638dbe17981b98c6bbb84244)

- **作者**: He Yingxu
- **时间**: 2026-11-24T13:45:18Z
- **提交信息**: [Bugfix][Multimodal] Include the cause in HF processor error messages (#69613)

Signed-off-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [93bb688](https://github.com/vllm-project/vllm/commit/93bb688f48fb5d75fee748947ec0e3256bee74f6)

- **作者**: Artem Perevedentsev
- **时间**: 2026-11-24T13:40:49Z
- **提交信息**: [Frontend][Perf] Default --renderer-num-workers to 4 for the async renderer (#69041)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d9586ca](https://github.com/vllm-project/vllm/commit/d9586ca916b49ad1e04d08b6ad3bbe00129269d6)

- **作者**: lijipeng
- **时间**: 2026-11-24T13:21:34Z
- **提交信息**: [Perf][ROCm][Attention] Use smaller tiles in the prefix_prefill kernel on RDNA (ROCM_ATTN prefill) (#69321)

Signed-off-by: Jipeng Li <jipengli@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b09bc99](https://github.com/vllm-project/vllm/commit/b09bc99f40951f8984a6c64cecfed47036bc6016)

- **作者**: suntp
- **时间**: 2026-11-24T12:44:44Z
- **提交信息**: [Rust Frontend] Support DeepSeek V4 completion suffixes (#68969)

Signed-off-by: suntianpei <20786998+suntp@users.noreply.github.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: suntianpei <20786998+suntp@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fbf9dad](https://github.com/vllm-project/vllm/commit/fbf9dadde6e8e454e48aa40e62757da28c45c3e9)

- **作者**: Bugen Zhao
- **时间**: 2026-11-24T12:43:51Z
- **提交信息**: [Rust Frontend] Parse Mistral v11+ tool calls (#69601)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [09b6084](https://github.com/vllm-project/vllm/commit/09b60846cd5c65bef519bd9b7a7ef4cc72c8e354)

- **作者**: Ren Yuzhou
- **时间**: 2026-11-24T12:36:45Z
- **提交信息**: [Bugfix][MoRIIO] Handle WRITE cancellation before submission (#60852)

Signed-off-by: Ren Yuzhou <54501155+yuzhouo7@users.noreply.github.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [669d308](https://github.com/vllm-project/vllm/commit/669d308d6088125180238d4df3be1197cda1501d)

- **作者**: Matt
- **时间**: 2026-11-24T12:29:22Z
- **提交信息**: [Frontend] Accept `reasoning_content` and `join` in response templates (#66156)

Signed-off-by: Matt <rocketknight1@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9df94b9](https://github.com/vllm-project/vllm/commit/9df94b99774f1a0e17716f26dbb4eac50cc66f7a)

- **作者**: Bugen Zhao
- **时间**: 2026-11-24T11:48:58Z
- **提交信息**: [Rust Frontend] Remove the phi4_mini_json tool parser (#69598)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6700554](https://github.com/vllm-project/vllm/commit/67005540852a3a185418582d67aad3d066b4284d)

- **作者**: Bugen Zhao
- **时间**: 2026-11-24T11:47:03Z
- **提交信息**: [Rust Frontend] Name the UTF-8 charset in SSE content types (#69600)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [21f021f](https://github.com/vllm-project/vllm/commit/21f021f804efeebf10d0c5213066466c814990f3)

- **作者**: Bugen Zhao
- **时间**: 2026-11-24T11:46:09Z
- **提交信息**: [Rust Frontend] Keep each scheduler metric group in one place (#68974)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d6aefef](https://github.com/vllm-project/vllm/commit/d6aefefa014322c3b54caa7890e0dca2483a5769)

- **作者**: Bugen Zhao
- **时间**: 2026-11-24T11:45:13Z
- **提交信息**: [Rust Frontend] Bound token-ID prompts by the model vocab unless they carry multimodal inputs (#69602)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9d91dd2](https://github.com/vllm-project/vllm/commit/9d91dd2a95d158f50402ff3b83305a167ae533d0)

- **作者**: Bugen Zhao
- **时间**: 2026-11-24T11:44:18Z
- **提交信息**: [Rust Frontend] Parse every checkpoint JSON file like Python's json (#69566)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8b014b2](https://github.com/vllm-project/vllm/commit/8b014b2cbe30e795be5e281a41135a4e08276b06)

- **作者**: Ahmed Nassar
- **时间**: 2026-11-24T11:39:41Z
- **提交信息**: [Model] Add Granite Docling (#66581)

Signed-off-by: Ahmed Nassar <nassarofficial@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c4f6d8c](https://github.com/vllm-project/vllm/commit/c4f6d8c77caf632d15bed1e040ccfc2dba9c4e72)

- **作者**: Shanshan Shen
- **时间**: 2026-11-24T11:18:31Z
- **提交信息**: [ROCm][UMBP] Support UMBP standalone mode for DeepSeek-V4-Pro (#63002)

Signed-off-by: shen-shanshan <467638484@qq.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6dac81b](https://github.com/vllm-project/vllm/commit/6dac81bcde1cdfd52f607e54e42ca52d57855c92)

- **作者**: Chinmay-Kulkarni-AMD
- **时间**: 2026-11-24T10:38:31Z
- **提交信息**: [ZenCPU][CI] Push the zen CPU image so the zen5 tests can reuse it (#68136)

Signed-off-by: Chinmay Kulkarni <Chinmay.Kulkarni@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2e2083c](https://github.com/vllm-project/vllm/commit/2e2083c2a5539008eee6c168f159d8f5c7cc4907)

- **作者**: Chauncey
- **时间**: 2026-11-24T10:08:59Z
- **提交信息**: [Bugfix] Fix InstantTensor loading for HY4 Flash Engram weights (#68659)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [2f7d4d7](https://github.com/vllm-project/vllm/commit/2f7d4d70bbeffff8dc437fb940be4ac8749a1c3e)

- **作者**: Talor Abramovich
- **时间**: 2026-11-24T10:06:52Z
- **提交信息**: [Docs] Update SPEED-Bench preparation script documentation (#65382)

Signed-off-by: talora <talora@nvidia.com>

### [f465550](https://github.com/vllm-project/vllm/commit/f4655507a93f1b9bc698d7c60a5feacd55393249)

- **作者**: Canlin Guo
- **时间**: 2026-11-24T09:58:18Z
- **提交信息**: [Bugfix][Rust Frontend] glm5_next: render developer messages like the HF renderer (#68922)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [596887a](https://github.com/vllm-project/vllm/commit/596887a06bfbdf66b56b21f755652c2a7262390c)

- **作者**: Yibo Liu
- **时间**: 2026-11-24T09:56:46Z
- **提交信息**: [Bugfix][Frontend] Raise the RLIMIT_NOFILE soft limit at vllm-rs startup (#68223)

Signed-off-by: Yibo Liu <yibol9768@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [efd53aa](https://github.com/vllm-project/vllm/commit/efd53aa4791dd8be49e28a6d071b15787a135240)

- **作者**: Martin Hickey
- **时间**: 2026-11-24T09:52:04Z
- **提交信息**: [Governance] Add hickeyma as committer for API server (#69405)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [7cd994e](https://github.com/vllm-project/vllm/commit/7cd994e2d973f5a535415cb1978b0f161f6c04c9)

- **作者**: Tomasz Zielinski
- **时间**: 2026-11-24T09:47:37Z
- **提交信息**: [XPU] Implement stateless_init_device_torch_dist_pg for XPU (#57196)

Signed-off-by: tzielinski-habana <tomasz.zielinski@intel.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ef61f6f](https://github.com/vllm-project/vllm/commit/ef61f6fe381b8c590e7b5a10244d2093a6ffd76d)

- **作者**: aoshen02
- **时间**: 2026-11-24T09:30:04Z
- **提交信息**: [Bugfix][Weight Transfer] Avoid ThreadPoolExecutor(wait=True) deadlock on exception in ShardedRDTTrainerWeightTransferEngine (#69589)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>

### [dd1c08d](https://github.com/vllm-project/vllm/commit/dd1c08d0293bda2f0f26daca18ac073315be2093)

- **作者**: Shuojie
- **时间**: 2026-11-24T09:28:12Z
- **提交信息**: [CI] Shard the Arm CPU tests automatically (slowest Arm job 20.5 → ~15.5 min) (#67470)

Signed-off-by: Shuojie Wang <latioswang@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [12eb1d4](https://github.com/vllm-project/vllm/commit/12eb1d4eec9288b21f5d6d0ac31ffe84f47d91da)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-11-24T09:27:56Z
- **提交信息**: [Bugfix][DSA] Stage ShardQ indexer indices in fresh host memory each step (#66052)

Signed-off-by: AMD-yanfeiwang <yanfei.wang@amd.com>
Signed-off-by: Yanfei Wang <yanfei.wang@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [cec6cf6](https://github.com/vllm-project/vllm/commit/cec6cf689bb44f4772338a7f260620e04e328734)

- **作者**: Canlin Guo
- **时间**: 2026-11-24T09:21:09Z
- **提交信息**: [Bugfix][Rust Frontend] Apply the configurable request size limit to gRPC messages (#68923)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [99b0b0b](https://github.com/vllm-project/vllm/commit/99b0b0b0f34adf48122e54396448950d72efb0fe)

- **作者**: Sherif Waly
- **时间**: 2026-11-24T08:47:48Z
- **提交信息**: [Frontend][ToolParser] Stream Kimi K3 tool arguments incrementally (#67021)

Signed-off-by: Sherif Waly <sherif.waly@mistral.ai>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [04b920e](https://github.com/vllm-project/vllm/commit/04b920eca4173e64fb7564dd814fbd4096fde961)

- **作者**: Chauncey
- **时间**: 2026-11-24T08:41:37Z
- **提交信息**: [Perf] Enable native small-head FlashMLA kernels for HYV4/V4-Flash on SM90 (#68321)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a0c1f16](https://github.com/vllm-project/vllm/commit/a0c1f162f4ded00f0f40928698b4b5816f4d3bd7)

- **作者**: Chaojun Zhang
- **时间**: 2026-11-24T08:37:08Z
- **提交信息**: [XPU][Qwen3.5] Support sequence parallelism with pipeline parallelism (#69314)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3d3332c](https://github.com/vllm-project/vllm/commit/3d3332c577b41f223f78d0e3f47b4ef88fd3cf75)

- **作者**: liuzhenwei
- **时间**: 2026-11-24T08:36:54Z
- **提交信息**: [XPU][CI] Skip cpu_test cases in Intel V1 kv_connector unit tests (#69524)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [cc9ac98](https://github.com/vllm-project/vllm/commit/cc9ac98ccefd188a0bd49db29992fd0d90404dc6)

- **作者**: aoshen02
- **时间**: 2026-11-24T08:35:13Z
- **提交信息**: [Frontend][RL] Verify weights against a baseline in finish_weight_update (#59371)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>

### [ab1c064](https://github.com/vllm-project/vllm/commit/ab1c06419cf62eb8cfed2e61548dbb92b92f7ca4)

- **作者**: Yanying Lin
- **时间**: 2026-11-24T08:19:06Z
- **提交信息**: [RL] Add Connex weight transfer backend (#63805)

Signed-off-by: yanyinglin <linyanying19@mails.ucas.ac.cn>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [3f86db3](https://github.com/vllm-project/vllm/commit/3f86db3b2df84dc2e4d10b81da43afad132d66c6)

- **作者**: waizuichougou
- **时间**: 2026-11-24T08:13:34Z
- **提交信息**: [Bugfix][KV Offload][P2P] Eliminate no-op store jobs and inflated write metrics (#69132)

Signed-off-by: waizuichougou <2082431897@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [565932f](https://github.com/vllm-project/vllm/commit/565932f97425111bf6514a52702e4200dc1098fc)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-24T07:43:09Z
- **提交信息**: [Doc] Fix docs build RecursionError from lazily imported torch._inductor (#69580)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f126828](https://github.com/vllm-project/vllm/commit/f1268288fd4feba8dd3425b07e82de35dd77c3d1)

- **作者**: Haobin Guo
- **时间**: 2026-11-24T07:26:28Z
- **提交信息**: [Kernel][MoE] Add FlashInfer CuTe-DSL unquantized MoE backend for Hopper (SM90) (#66749)

Signed-off-by: Haobin Guo <haobing@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8eb876b](https://github.com/vllm-project/vllm/commit/8eb876b9f91459b062a94a024c2b810b1b952ee4)

- **作者**: Ziqi Yin
- **时间**: 2026-11-24T07:12:27Z
- **提交信息**: [Bugfix][DSA][PCP] Fix indexer prefill logits lifetime and fused chunk planning (#69332)

Signed-off-by: Ziqi Yin <ziqi003@e.ntu.edu.sg>
Signed-off-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [14e9c30](https://github.com/vllm-project/vllm/commit/14e9c30d86249eb1c0d3aa57d9779dd68207aede)

- **作者**: Thien Tran
- **时间**: 2026-11-24T06:42:44Z
- **提交信息**: [Perf][GDN] Write only the used FlashInfer prefill checkpoint states (#69401)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f2f9edc](https://github.com/vllm-project/vllm/commit/f2f9edcac30d128bc090a3c032e4ba125716a641)

- **作者**: Johnson
- **时间**: 2026-11-24T06:01:41Z
- **提交信息**: [Perf][Qwen4Exp] Add SM100 TP=2 and TP=8 skinny GEMM plans (#69529)

Signed-off-by: Johnsonms <lizhaofu@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a5ae2ec](https://github.com/vllm-project/vllm/commit/a5ae2ec110420c9eab841d93a9ae182a03467b92)

- **作者**: Nils Matteson
- **时间**: 2026-11-24T06:01:23Z
- **提交信息**: [Bugfix][Config] Keep host-only renderer, timeout, and recovery fields out of compile cache key (#69475)

Signed-off-by: Nils Matteson <nils@inferact.ai>

### [f2c5fc2](https://github.com/vllm-project/vllm/commit/f2c5fc200926283075c7cd0f71967978d16eaaec)

- **作者**: yhcheong (vllmellm)
- **时间**: 2026-11-24T05:51:15Z
- **提交信息**: [Bugfix] Guard Conch W4A16 preconditions and pad non-tile-multiple outputs (#62268)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [ea625af](https://github.com/vllm-project/vllm/commit/ea625affc8d2bd62d2a80d47e5164a1074971ad0)

- **作者**: Lalithnarayan C
- **时间**: 2026-11-24T05:26:52Z
- **提交信息**: [Bugfix][CPU] DeepSeek-V4: return all layer types from the CPU tile scheduler (#65365)

Signed-off-by: Lalithnarayan C <Lalithnarayan.C@amd.com>

### [7262aa8](https://github.com/vllm-project/vllm/commit/7262aa85a5d7ce7e1496ae9948d0e5fa88b038a2)

- **作者**: Thang Nguyen
- **时间**: 2026-11-24T05:16:38Z
- **提交信息**: [CI] Let auto-rebase ignore per-step ci/step statuses (#69503)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f7db8ac](https://github.com/vllm-project/vllm/commit/f7db8ac0ebcded8dd1750687a86fc107a821beba)

- **作者**: Tony Lin
- **时间**: 2026-11-24T04:53:57Z
- **提交信息**: [CI][XPU] Enable batch invariance for OLMoE LoRA tests (#69509)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [de12dce](https://github.com/vllm-project/vllm/commit/de12dcefc13ae33526f94dae5a2bb71c10b13544)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-24T04:34:14Z
- **提交信息**: [Startup] Keep Inductor and Dynamo imports off the non-compiled path (#69520)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [341b2b3](https://github.com/vllm-project/vllm/commit/341b2b31f3219701e6f309426b481e5e13a6ad7e)

- **作者**: GuorongYe
- **时间**: 2026-11-24T03:56:54Z
- **提交信息**: [EPD] Support metadata-only images and videos for HY4 and HY4 Flash (#69426)

Signed-off-by: grYe99 <guorongye99@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [e30583d](https://github.com/vllm-project/vllm/commit/e30583d51bf577759e47e422c2cfbf43febd52ab)

- **作者**: milesial
- **时间**: 2026-11-24T03:51:01Z
- **提交信息**: [Rust Frontend] Serve Nemotron VL and Omni multimodal inputs (#68808)

Signed-off-by: Alexandre Milesi <milesial@users.noreply.github.com>
Signed-off-by: milesial <milesial@users.noreply.github.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2aae0e2](https://github.com/vllm-project/vllm/commit/2aae0e21f8ea109066080bd724fbdd27ce33a9df)

- **作者**: RuibinCheung
- **时间**: 2026-11-24T03:38:08Z
- **提交信息**: [CI][ROCm] Spawn the GPU memory wait worker (#69374)

Signed-off-by: RuibinCheung <ruibzhan@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [504c9fc](https://github.com/vllm-project/vllm/commit/504c9fc5aac5a206a3643297595025a833fd8504)

- **作者**: Yiliu Dong
- **时间**: 2026-11-24T03:21:33Z
- **提交信息**: [HY4 Flash][MoE] Allow passthrough all2all backend with DP (#68661)

Signed-off-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e0aa7ee](https://github.com/vllm-project/vllm/commit/e0aa7eeb0c686c371a0cb02f77e9178ff231bce6)

- **作者**: Thien Tran
- **时间**: 2026-11-24T03:19:45Z
- **提交信息**: [Perf][Qwen4Exp] Small NVIDIA-path wins: HC expand via cat, GDN ba overlap, fused HC mix from M=48 (#69122)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [77569b7](https://github.com/vllm-project/vllm/commit/77569b7a69a1281a61d90bbe1cd0f36bbefb3598)

- **作者**: Przemyslaw
- **时间**: 2026-11-24T03:16:23Z
- **提交信息**: [Bugfix][Model] Port Mistral Large 4 NVIDIA indexer cache to get_kv_cache_config (#68103)

Signed-off-by: Przemyslaw <kainoj@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9cd5cde](https://github.com/vllm-project/vllm/commit/9cd5cde84bc372462a9034e49462634a168304fb)

- **作者**: Thang Nguyen
- **时间**: 2026-11-24T02:19:48Z
- **提交信息**: [CI] Turn automatic sharding on by default (#64796)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [28fb136](https://github.com/vllm-project/vllm/commit/28fb1365a90e9929e4596a72906e309dd7ac701f)

- **作者**: CSWYF3634076
- **时间**: 2026-11-24T02:03:33Z
- **提交信息**: [Recipe] Update ERNIE recipe Support ERNIE 5.5 Flash Preview (#69425)

Signed-off-by: jackyYang6 <jacky6.yang@gmail.com>
Signed-off-by: wangyafeng <wangyafeng@baidu.com>
Co-authored-by: jackyYang6 <jacky6.yang@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ce2668a](https://github.com/vllm-project/vllm/commit/ce2668a3df8ba6746d5470075d46eb770c1b11ac)

- **作者**: Mikko Tukiainen
- **时间**: 2026-11-24T01:55:00Z
- **提交信息**: [ROCm][Perf][Qwen4Exp] Tune QSA sparse GQA and indexer on gfx942 and gfx950 (#65474)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f08216e](https://github.com/vllm-project/vllm/commit/f08216eb63e48973aba6cb4d67f1cf8d45c2491a)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-24T01:47:17Z
- **提交信息**: [CI] Switch vllm-runners callers to @main reusable workflows (step 2/2) (#69513)

Signed-off-by: khluu <khluu000@gmail.com>

### [7200a4e](https://github.com/vllm-project/vllm/commit/7200a4e0f5ce3457af19166d8a2de2f8a44fa9cc)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-24T01:33:21Z
- **提交信息**: [CI] Add reusable workflows for vllm-runners (step 1/2) (#69510)

Signed-off-by: khluu <khluu000@gmail.com>

### [66e8914](https://github.com/vllm-project/vllm/commit/66e8914fc93c1b49f27fda3da33b6f1126d37a37)

- **作者**: zhenwenqi2024
- **时间**: 2026-11-24T00:36:16Z
- **提交信息**: [Bugfix][HiSparse] Reclaim resident pages before allocating the next prefill chunk (#67185)

Signed-off-by: zhenwenqi2024 <zhenwenqi_2022@qq.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e04f069](https://github.com/vllm-project/vllm/commit/e04f069197ee4b3b5a6c67932735edb10d4e4ba2)

- **作者**: Wentao Ye
- **时间**: 2026-11-24T00:32:34Z
- **提交信息**: [Refactor] Remove dead code quantizations (#69483)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-25
**监控日期**: 2026-11-24
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7948
- **最后更新**: 2026-11-25T04:40:36Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 26
- **主要提交者**: wangyu, ziruil, Oliver7th

## AI分析总结

## vllm-omni 昨日提交分析（32条）

### 1. 主要更新类型
- **Bug修复**（约12条）：占比最高，集中在Duplex双工对话、扩散模型、Qwen系列模型
- **性能优化**（约7条）：MiniMax-H3扩散管线、算子融合、批量解码
- **功能新增/模型支持**（约8条）：新TTS模型、新Omni模型、请求级采样参数
- **CI/构建与硬件适配**（约7条）：ROCm、Ascend NPU、AMD测试

### 2. 关键变更点与项目方向的关系
- **多模态模型矩阵扩张**：新增 Chatterbox TTS、Ming-3.0-TTS、Realtime-Venus Omni（原生双工工具调用）、Nemotron VoiceChat 批量解码，直接落实"easy, cheap omni-modality serving"的定位。
- **双工（Duplex）对话稳定性**：修复启动warmup卡死、超时轮次泄漏等，强化实时语音交互的核心体验。
- **扩散（Diffusion）语音/视频管线**：大量 MiniMax-H3 优化（MP4预编码、VAE空间tile批量解码、fc1+SwiGLU融合、Q/K norm+RoPE kernel），并增加输入校验（非法flow shift拒绝）。
- **硬件生态广度**：ROCm（Qwen3-Omni冷启动、Voxtral延迟拆分）、Ascend NPU（VoxCPM2补丁开关、Cosmos3 RMSNorm融合）、AMD每周扩散一致性测试——延续多后端战略。
- **推理正确性**：Qwen2.5-Omni Talker投影保留在编译图内、Higgs v2路由提升、GLM-TTS采样顺序对齐上游，保证数值正确性优先于性能。

### 3. 影响与潜在意义
- 短期降低生产环境故障率（duplex、扩散、ngram缓存类修复），提升服务可靠性。
- 性能批次使扩散与语音生成吞吐提升，降低README宣称的"serving成本"。
- 新模型与新采样参数（重复惩罚、Subtalker温度）增强对下游场景的覆盖能力。

### 4. 值得关注的技术点
- **Model Runner V2 迁移**正在推进（Haru-4B帧状态、Qwen3-Omni ngram span保留均涉及MRv2），是底层架构演进信号。
- 部分提交由 Claude Code/Opus 协作完成，AI辅助开发已融入该仓库工作流。
- `#8313` 单提交携带25+签名者，显示Ascend补丁由多方共同维护，集成复杂度高。
- `[Core]` 在ASR后新增响应判定阶段（#8316），暗示流水线中引入质量把关环节。

### 5. 对项目发展的总体影响
这批提交体现了vllm-omni在README所承诺方向上的均衡推进：一方面通过持续的新模型接入（TTS、Omni、扩散）扩大"omni-modality"覆盖面，另一方面以密集的Bug修复和多硬件CI加固生产可用性；同时以MiniMax-H3系列算子级优化和Model Runner V2演进夯实性能底座。整体表明项目正从功能铺开期转向**稳定性与性能打磨期**，为更广泛的实时多模态服务商业化做准备。

## 详细提交记录

### [cfd0687](https://github.com/vllm-project/vllm-omni/commit/cfd0687a7192e5cebbc0dccda58117429b7d2112)

- **作者**: haic0
- **时间**: 2026-11-24T23:59:52Z
- **提交信息**: [CI/Build][ROCm] Split Voxtral latency from advisory NIGHTLY sweeps (#11104)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>

### [c0712a1](https://github.com/vllm-project/vllm-omni/commit/c0712a146bab93e58a461340181bf1dfc37db7b0)

- **作者**: lm10-arg
- **时间**: 2026-11-24T22:55:11Z
- **提交信息**: [CI/Build][Hardware][AMD] Add final weekly diffusion parity qualifiers (#11044)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [341b339](https://github.com/vllm-project/vllm-omni/commit/341b3391dbee2b802daa5f6186ca5b5857f00940)

- **作者**: Nyamkhuu Demberelsuren
- **时间**: 2026-11-24T22:40:34Z
- **提交信息**: [Model] Support Ming-3.0-TTS dense 0.5B checkpoint (#10977)

Signed-off-by: Nyamkhuu Demberelsuren <14359292+d-nyamkhuu@users.noreply.github.com>
Co-authored-by: Nyamkhuu Demberelsuren <14359292+d-nyamkhuu@users.noreply.github.com>

### [671b312](https://github.com/vllm-project/vllm-omni/commit/671b312d7417e4f06ed7a335f24edef2d728dc6a)

- **作者**: Shaun Walsh
- **时间**: 2026-11-24T22:15:38Z
- **提交信息**: [Bugfix][Duplex] End startup warmup when the model answers response.listen (#11099)

Signed-off-by: Shaun Walsh <shaunwalsh24@gmail.com>

### [8978966](https://github.com/vllm-project/vllm-omni/commit/8978966c60c8542514f631340e23db144d9103e7)

- **作者**: Liuchenbing-2026
- **时间**: 2026-11-24T21:33:41Z
- **提交信息**: [Bugfix] Reject unsupported streaming in diffusion speech (#8883)

Signed-off-by: liuchenbing <chenliumail@163.com>
Co-authored-by: liuchenbing <chenliumail@163.com>

### [7eb188f](https://github.com/vllm-project/vllm-omni/commit/7eb188ffa405fa7d33e46ee80cb5fa5e74c4e7bb)

- **作者**: Haiyi Dong
- **时间**: 2026-11-24T21:01:10Z
- **提交信息**: [Bugfix] Duplex: release timed-out deferred turns on cancel and drop (#11055)

Signed-off-by: Haiyi Dong <a1530931035@gmail.com>

### [8bc6f94](https://github.com/vllm-project/vllm-omni/commit/8bc6f942dcd2f95331997c2d8e796be796dbea37)

- **作者**: hac17
- **时间**: 2026-11-24T20:32:22Z
- **提交信息**: [CI/Build][ROCm] Allow Qwen3-Omni cold startup in accuracy and non-async perf (#11095)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [f809891](https://github.com/vllm-project/vllm-omni/commit/f809891bae7d6443ca475d7b29cb20848f10e99b)

- **作者**: SYLAR
- **时间**: 2026-11-24T20:21:20Z
- **提交信息**: [Perf][Diffusion] MiniMax-H3: pre-encode the MP4 on the worker for video API requests by default (#10861)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6719d50](https://github.com/vllm-project/vllm-omni/commit/6719d509be50eeb988a34b028ae87b0e5b4e04b7)

- **作者**: ziruil
- **时间**: 2026-11-24T20:07:16Z
- **提交信息**: [Bugfix][Qwen2.5-Omni] Keep the Talker input projection inside the compiled backbone (#11070)

Signed-off-by: ziruil <ziruil@nvidia.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [aae161a](https://github.com/vllm-project/vllm-omni/commit/aae161a3e194b9136328b8b9baeda329a2cbd509)

- **作者**: Xinpei Wang
- **时间**: 2026-11-24T19:13:22Z
- **提交信息**: [Model] Batch Nemotron VoiceChat Code2Wav decoding (#8920)

Signed-off-by: Xinpei Wang <wangxinpei@tju.edu.cn>

### [be17481](https://github.com/vllm-project/vllm-omni/commit/be17481fe141537d30dfe4318e6921a7ff7347f7)

- **作者**: SFA_Sukhoi
- **时间**: 2026-11-24T18:33:32Z
- **提交信息**: [Bugfix] Fix Haru-4B frame state on Model Runner V2 (#11069)

Signed-off-by: beiningwu <sukhoi258@163.com>
Co-authored-by: beiningwu <sukhoi258@163.com>

### [14a0123](https://github.com/vllm-project/vllm-omni/commit/14a01235186941ad7a26ce258a4ca27c45cb6ebf)

- **作者**: EddieTzy
- **时间**: 2026-11-24T17:58:55Z
- **提交信息**: [Model] Hoist uniform audio routing in Higgs v2 (#11068)

Signed-off-by: 陶子粤 <1137898187@qq.com>

### [c59fc0a](https://github.com/vllm-project/vllm-omni/commit/c59fc0ab1a35e86c623ee55e15dd6649ac4e01f0)

- **作者**: SYLAR
- **时间**: 2026-11-24T17:27:05Z
- **提交信息**: [Perf][Diffusion] MiniMax-H3: fuse fc1+SwiGLU and block-boundary gate+norm1, exact embedding copy (#10858)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bb3eed9](https://github.com/vllm-project/vllm-omni/commit/bb3eed927d9e0bf6157a5ccbe4293c2e108e4d8e)

- **作者**: lm10-arg
- **时间**: 2026-11-24T16:01:14Z
- **提交信息**: [Bugfix] Fix JoyAI resume and Chatterbox decoder batching (#11090)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [0ccd928](https://github.com/vllm-project/vllm-omni/commit/0ccd928150797a197bb6941d44f8324a106ac623)

- **作者**: wangqiankun13
- **时间**: 2026-11-24T13:29:58Z
- **提交信息**: [Bugfix][HunyuanImage3] Run DiT MoE router in FP32 (#10260)

Signed-off-by: wangqiankun13 <wangqiankun13@huawei.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [123c96e](https://github.com/vllm-project/vllm-omni/commit/123c96e4a81a597e08526d46c54dc2325fc01488)

- **作者**: amy-why-3459
- **时间**: 2026-11-24T13:14:36Z
- **提交信息**: [Model] Add Realtime-Venus Omni with native duplex tool calling (#10976)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4387f6f](https://github.com/vllm-project/vllm-omni/commit/4387f6f877f5d1d8f04df693f455927760aaa18c)

- **作者**: psv666
- **时间**: 2026-11-24T13:14:33Z
- **提交信息**: [CI/Build] Accept reasoning in Qwen3-Omni video smoke test (#11021)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [e71053a](https://github.com/vllm-project/vllm-omni/commit/e71053ae772ac729700984130abc68a74d551cac)

- **作者**: Lingwei1943
- **时间**: 2026-11-24T09:55:22Z
- **提交信息**: [Hardware][Ascend] Add disable switch and configurable graph limit for the VoxCPM2 NPU patch (#8313)

Signed-off-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Signed-off-by: Maciej Bala <mbala@nvidia.com>
Signed-off-by: Yuliya Zhautouskaya <yzhautouskay@nvidia.com>
Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>
Signed-off-by: y_null <y_null@qq.com>
Signed-off-by: Hang Zhengyang <hang.zhengyang1010@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Signed-off-by: dongbo910220 <1275604947@qq.com>
Signed-off-by: Yunzenn <209125778+Yunzenn@users.noreply.github.com>
Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Signed-off-by: Nick Cao <ncao@redhat.com>
Signed-off-by: Linze-Shi <linzeshi0@gmail.com>
Signed-off-by: Lewis Won <lewis.won@gmail.com>
Signed-off-by: yiminghub2024 <202503791+yiminghub2024@users.noreply.github.com>
Signed-off-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>
Signed-off-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Signed-off-by: jeffaa729 <hoiwanglo@gmail.com>
Signed-off-by: brandneway <gyuan4892@gmail.com>
Signed-off-by: dengyunyang <584797741@qq.com>
Signed-off-by: williamLyh <williamliuyinhong@gmail.com>
Signed-off-by: wutongyuonce <147830929+wutongyuonce@users.noreply.github.com>
Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: stone.li <mmlmonkey@163.com>
Signed-off-by: SunskyXH <sunskyxh@gmail.com>
Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: opencode <opencode@ai>
Co-authored-by: Sheng GAO <sheng.gao.dev@gmail.com>
Co-authored-by: MaciejBalaNV <mbala@nvidia.com>
Co-authored-by: Yuliya Zhautouskaya <yzhautouskay@nvidia.com>
Co-authored-by: boatman <1930807094@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: y-null <y_null@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Co-authored-by: Hang Zhengyang <42070978+DuFanYin@users.noreply.github.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: lm10-arg <linluo@icloud.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: dongbo910220 <32610838+dongbo910220@users.noreply.github.com>
Co-authored-by: Yunzenn <209125778+Yunzenn@users.noreply.github.com>
Co-authored-by: NATURE <wzliu@connect.hku.hk>
Co-authored-by: Ding Zuhao <e1583181@u.nus.edu>
Co-authored-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Linze Shi <linzeshi0@gmail.com>
Co-authored-by: searlion <39227195+searlion@users.noreply.github.com>
Co-authored-by: yiminghub2024 <482890@qq.com>
Co-authored-by: yiminghub2024 <202503791+yiminghub2024@users.noreply.github.com>
Co-authored-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>
Co-authored-by: He Yingxu <yingxu.he1998@gmail.com>
Co-authored-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: jeffaa729 <111237525+jeffaa729@users.noreply.github.com>
Co-authored-by: dengyunyang <584797741@qq.com>
Co-authored-by: ooooooye <53851298+brandneway@users.noreply.github.com>
Co-authored-by: Yinhong Liu <williamliuyinhong@gmail.com>
Co-authored-by: 梧桐雨 <147830929+wutongyuonce@users.noreply.github.com>
Co-authored-by: GUOGUO <xwdong1998@163.com>
Co-authored-by: hac17 <haczhang117@outlook.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: sdli1995 <mmlmonkey@163.com>
Co-authored-by: SunskyXH <sunskyxh@gmail.com>
Co-authored-by: ShuaiYeh <42410853+ShuaiYeh@users.noreply.github.com>
Co-authored-by: Samit <285365963@qq.com>

### [7b8ce44](https://github.com/vllm-project/vllm-omni/commit/7b8ce4451e78ff528ddee37598489e8c8ca2a7a7)

- **作者**: Krzysztof Tomala
- **时间**: 2026-11-24T09:45:44Z
- **提交信息**: [Bugfix] Alpamayo 2 Super: record the trajectory trigger on Model Run… (#11033)

Signed-off-by: Krzysztof Tomala <ktomala@nvidia.com>

### [3f7af97](https://github.com/vllm-project/vllm-omni/commit/3f7af97b961747676b14384f321086191deb1db1)

- **作者**: zzx
- **时间**: 2026-11-24T08:37:51Z
- **提交信息**: [Core] Add a response judge stage after ASR (#8316)

Signed-off-by: zxy <1335108150@qq.com>
Signed-off-by: zxy <u7905843@anu.edu.au>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [341d06f](https://github.com/vllm-project/vllm-omni/commit/341d06fa794d32c92e06a321f19102110af19af1)

- **作者**: SYLAR
- **时间**: 2026-11-24T07:24:09Z
- **提交信息**: [Perf][Diffusion] MiniMax-H3: decode VAE spatial tiles as one batch (#10860)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5ce0e3e](https://github.com/vllm-project/vllm-omni/commit/5ce0e3e51f975b501efb9db3d78b13a1cac83ccb)

- **作者**: SYLAR
- **时间**: 2026-11-24T07:23:34Z
- **提交信息**: [Perf][Diffusion] Indexed modulation and Q/K norm+RoPE kernel improvements (#10857)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4dafb46](https://github.com/vllm-project/vllm-omni/commit/4dafb464442956996be9633ed036cd24ebfef1d0)

- **作者**: Lingwei1943
- **时间**: 2026-11-24T04:06:23Z
- **提交信息**: [Feature][Frontend] initial burst buffering for streaming speech (#10194)

Signed-off-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: Remember3e <94928086+Remember3e@users.noreply.github.com>
Co-authored-by: Samit <285365963@qq.com>

### [da238f0](https://github.com/vllm-project/vllm-omni/commit/da238f0fbc3ecf52a1d50f5b500a90a30771c96b)

- **作者**: Zhongyu Yang
- **时间**: 2026-11-24T04:01:18Z
- **提交信息**: [Model][MiniCPM-o] Add the reference listen_prob_scale and listen_top_k knobs to the 4.5 duplex sampler (#10955)

Signed-off-by: yangzhongyu <yangzhongyu@modelbest.cn>
Co-authored-by: yangzhongyu <yangzhongyu@modelbest.cn>

### [cbdfef4](https://github.com/vllm-project/vllm-omni/commit/cbdfef434b20a601f3261dc1019e311761a4b508)

- **作者**: xiangrong zhong
- **时间**: 2026-11-24T03:29:42Z
- **提交信息**: [Bugfix] Reject invalid flow shifts for diffusion models (#9609)

Signed-off-by: zhongc1211 <huixindaddy@yahoo.com>
Co-authored-by: Zhengyuan Su (苏政渊) <su.zhengyuan@u.nus.edu>

### [02895a0](https://github.com/vllm-project/vllm-omni/commit/02895a0b2cbc43da3a52a3c4709b59a263aa37e9)

- **作者**: GXIN
- **时间**: 2026-11-24T03:02:55Z
- **提交信息**: [Feature] Support request-level repetition penalty and Subtalker temperature in Qwen3-TTS (#10717)

Signed-off-by: XIN GAO <1037396230@qq.com>

### [56217be](https://github.com/vllm-project/vllm-omni/commit/56217be932490d0aba6bf29caacea5c0e9785e21)

- **作者**: lm10-arg
- **时间**: 2026-11-24T02:33:28Z
- **提交信息**: [Bugfix][GLM-TTS] Match upstream nucleus sampling order (#11046)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [bc266e5](https://github.com/vllm-project/vllm-omni/commit/bc266e5d5a2667bacf59c4912cb5404c9002f53c)

- **作者**: seongyun.kim
- **时间**: 2026-11-24T02:19:58Z
- **提交信息**: [Bugfix] Preserve Qwen3-Omni ngram_gpu verified spans for Talker on MRv2 (#11029)

Signed-off-by: seongyun.kim <197560810+seongyun1104@users.noreply.github.com>

### [37249e2](https://github.com/vllm-project/vllm-omni/commit/37249e28ff4a62ad8f7973c503f38d4e22089056)

- **作者**: Oliver7th
- **时间**: 2026-11-24T01:54:22Z
- **提交信息**: [Hardware][Ascend] Fuse Cosmos3 RMSNorm and intra-block residual addition for Cosmos3 (#10056)

Signed-off-by: Oliver7th <1105319308@qq.com>

### [e5f80c9](https://github.com/vllm-project/vllm-omni/commit/e5f80c9480f6f1765825052a88cdc9717ffe8f78)

- **作者**: wangyu
- **时间**: 2026-11-24T01:44:08Z
- **提交信息**: [CI/Build] Share the CustomVoice default CUDA-graph OmniServer with 001/002 (#11008)

Signed-off-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Co-authored-by: wangyu <yenuo26@users.noreply.github.com>

### [48ad43c](https://github.com/vllm-project/vllm-omni/commit/48ad43c7d804602abd45e7fe5f865c49a6b5b972)

- **作者**: Mesut Oezdil
- **时间**: 2026-11-24T01:20:05Z
- **提交信息**: [Frontend] Import build_app and setup_server from vllm.entrypoints.launchers (#9598)

Signed-off-by: mesutoezdil <mesudozdil@gmail.com>
Co-authored-by: Alex Brooks <albrooks@redhat.com>

### [fe8e3ec](https://github.com/vllm-project/vllm-omni/commit/fe8e3ec89e20221d9464b5c7eac50c765066c570)

- **作者**: Will Rice
- **时间**: 2026-11-24T00:07:30Z
- **提交信息**: [Model] Add Chatterbox TTS (Turbo and Original) (#8700)

Signed-off-by: Will Rice <wrice20@gmail.com>

---
