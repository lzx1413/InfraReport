# GitHub Stars 合并报告 - 2026-10-22

**合并日期**: 2026-10-23
**监控日期**: 2026-10-22
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


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2260
- **最后更新**: 2026-10-22T11:40:52Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Coach257, Zeren Chen

## AI分析总结

# ByteDance-Seed/VeOmni 昨日提交分析（第1/1批）

## 一、主要更新类型

本次共 2 个提交，涵盖**重构**与**功能新增**两个方向：

- **重构**：注意力（attention）封装层中 packed varlen cu_seqlens 的切分逻辑
- **功能新增**：SeedOmni 数据管线中动态批量（dynamic batching）的支持

两个提交均标注了 Cursor 协作开发（AI 辅助编码），体现了项目在工程效率上的实践。

---

## 二、关键变更点及与项目方向的关系

### 1. 注意力层 cu_seqlens 拆分重构（#1327）

- VeOmni 的核心目标之一是高效支持多模态模型训练，而注意力机制的 packed variable-length 序列（varlen）处理是实现高效训练的关键环节。cu_seqlens（CUDA 序列长度张量）是 varlen attention 的核心输入，用于标识各子序列的边界。
- 此次重构将 cu_seqlens 的拆分逻辑整合到 attention wrapper 中，属于对底层分布式训练算子的**架构级优化**，目的是使不同并行策略（如 sequence parallelism）下对长序列的拆分更加统一和健壮。

### 2. 动态批量数据管线（#1342）

- 该提交横跨 `omni、data、trainer、docs、agent` 五个模块，说明它不是单一功能点，而是打通了**从数据加载 → 训练器 → 智能体（agent）** 的完整链路。
- 动态批量意味着 batch size 可以根据输入序列长度自适应调整，在多模态场景中尤为重要——不同模态（文本/图像/视频/音频）的 token 长度差异巨大，固定 batch 会导致显存浪费或溢出。

---

## 三、对项目的影响和潜在意义

- **训练效率提升**：动态 batching 直接减少显存碎片和空转，对大规模多模态训练的吞吐量有显著正面影响。
- **系统稳定性增强**：attention wrapper 中 cu_seqlens 的统一管理降低了因序列拆分边界错误导致的潜在训练崩溃风险。
- **模块化与可维护性**：将拆分逻辑从外部调用者收拢到 wrapper 内部，符合"Model-Centric Distributed Recipe Zoo"的设计哲学——让用户更少地关注底层并行细节，更多地关注模型本身。
- **多模块联动**：#1342 涉及 agent 模块的更新，暗示 VeOmni 正在向**端到端多模态智能体训练**方向演进，而不仅是纯模型训练框架。

---

## 四、值得关注的技术点

1. **Packed Varlen Attention**：这是 Transformer 高效训练领域的前沿技术，与 FlashAttention 的 varlen 接口密切相关。将 cu_seqlens 拆分封装进 wrapper，意味着框架可以透明处理混合并行下的序列切分。
2. **多模态动态批处理的复杂性**：不同模态 token 化后的长度分布差异极大，动态 batching 需要在 GPU 显存利用率和调度开销之间取得平衡。
3. **AI 辅助开发流程**：两个提交均标注 Cursor 协作，反映出大型项目开始系统性引入 AI 编码工具进行底层工程重构。

---

## 五、对项目发展方向的影响

结合 README 中的项目定位（"Scaling Any Modality Model Training"），这两个提交共同指向了 VeOmni 的核心演进路线：**在保证多模态训练可扩展性的同时，持续优化底层分布式训练的效率与鲁棒性**。

- 重构提交夯实了 attention 这一最核心算子在分布式场景下的正确性和一致性，为后续支持更复杂的并行策略（如 context parallel、expert parallel）奠定基础。
- 动态 batching 的引入则使框架在实际多模态训练中更具实用性，降低了用户调参成本，增强了"Recipe Zoo"（预设配方库）的覆盖能力。

整体来看，这是一组**从底层算子到上层管线的系统性优化**，体现了项目从"功能可用"向"生产级高效"过渡的趋势，对目标用户（需要训练大规模多模态模型的研究者和工程师）具有明确的实用价值。

## 详细提交记录

### [5bbd362](https://github.com/ByteDance-Seed/VeOmni/commit/5bbd3623288533dfa71ad89227b38f98ce96903b)

- **作者**: Zeren Chen
- **时间**: 2026-10-22T11:40:46Z
- **提交信息**: [ops, model] refactor: support packed varlen cu_seqlens splitting in attention wrapper (#1327)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [b029df4](https://github.com/ByteDance-Seed/VeOmni/commit/b029df4b8aa2a60e32e1853aedfb6c52a823bd37)

- **作者**: Coach257
- **时间**: 2026-10-22T11:38:59Z
- **提交信息**: [omni, data, trainer, docs, agent] feat: support dynamic batching in SeedOmni data pipeline (#1342)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2942
- **最后更新**: 2026-10-22T14:19:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2311
- **最后更新**: 2026-10-22T05:08:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6747
- **最后更新**: 2026-10-23T00:41:16Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 12
- **主要提交者**: Akaash Parthasarathy, Jonathan Dierksen, Adrian

## AI分析总结

# FlashInfer 昨日 25 提交综合分析

## 一、主要更新类型

昨日提交以**性能优化**为绝对主导（约 15 项），其余包括：**重构去冗余**（多轮 Cake 包 deslop 清理）、**Bug 修复**（采样 RNG 偏移、MegaMoE 延迟路由权重）、**功能新增**（Rubin GDN T=1 decode 内核、上下文并行 KDA 训练后端）、**CI/基础设施改进**（JIT 缓存持久化、EP 安装条件修复）、**测试优化**和文档/CODEOWNERS 维护。

## 二、关键变更点

FlashInfer 定位为高性能 GPU 推理内核库，本日提交围绕三条主线推进：

1. **新硬件架构适配**：大量工作面向 Blackwell SM100/103 与 Rubin SM107。包括 Rubin GDN decode（uGPU 双 die 本地化使 DRAM 峰值从 61% 提升至 85–88%）、Rubin NVFP4 MLA paged decode（PDL 流水线重叠，批 1 加速 1.8–4.7%）、Rubin MTP MLA 后端（较 monolithic 快 10–30%）、SM107 MXFP8 小 M decode kernel（修复 M≤16 时带宽利用率极低问题，加速 1.2×）、SM120 e4m3 query FA2 tensor-core 解码等。

2. **训练与新算子生态扩展**：项目正从纯推理延伸至训练侧。KDA packed chunked grad 提速 1.43–1.89×；新增上下文并行 KDA 训练后端（GB300 上较 FLA KCP 加速 1.3–2.5 倍）；Kimi-K3 AttnRes 原生 K=6 kernel 扩展到 SM100；PrimsTS 新增 VC-Attention-QK16 dense FMHA context kernel，"repair tiles" 策略在 B200/B300 上相对 BF16 加速 1.16–1.33×，为 TRT-LLM VisualGen 生产化铺路。

3. **工程治理与正确性**：多轮 deslop 提交删除 24+50+10 个冗余文件，将 8 个重复内核合并为 4 个，编译期宏折叠实现"零 SASS 差异"重构验证，同时保持接口不变。修复采样 RNG 偏移预留（`get_seed_and_offset()` 语义修正，投机采样预留量改为 `B*(N+2)`），解决连续调用间随机数重复问题；修复 MegaMoE 延迟 NVFP4 路由权重正确性。

## 三、项目影响

- **端到端性能显著提升**：attention、RMSNorm、GEMM、MoE 等核心算子全线优化，直接改善推理延迟与吞吐，量化 NVFP4 路径打磨增强 Rubin 上 KV cache 压缩推理竞争力，视觉/视频生成（Wan2.2、SVDQuant LoRA）获直接收益。
- **开发效率改善**：CI 中 H100 测试约 5.7/7.0 worker-hours 花在首次编译，content-keyed JIT 缓存跨 job 持久化（区分可缓存 .o/cubin 与不可缓存项）显著降低 PR 反馈时间；sampling 测试内存从 980 MiB 降至 16–54 MiB；修复 `moe_ep` 子串误匹配减少 CI 噪声。
- **生态巩固**：持续巩固其在 vLLM、TRT-LLM 等框架中的核心内核基础设施地位，无接口变化的性能提交保证平滑升级。

## 四、值得关注的技术点

1. **uGPU 双 die 本地化**：每个 die 只访问自身内存，消除 die-to-die 链路瓶颈，是 Rubin 编程的重要范式；配合入口处 16KB CP.async 整块预取消除 CTA 屏障依赖。
2. **PDL 程序化依赖启动**：量化器、解码、split-KV merge 三 launch 序言重叠，实战隐藏流水线开销。
3. **按架构自适应分发**：nvfp4 SVDQuant、Kimi-K3 AttnRes 均按 sm 架构选择不同 program，未命中形态逐字节不变。
4. **严格基准规范**：冷 L2、CUDA-graph 整图回放、CUPTI 计时的验证协议成为项目标准。
5. **FP32 仿射状态摘要**：上下文并行跨 rank 精确状态传递，支持 zigzag 等分区布局。

## 五、对项目发展的影响

FlashInfer 已从注意力加速库演进为覆盖 MoE、GDN、MLA、KDA 的通用高性能内核平台。本日工作表明：Rubin 平台适配进入精细优化阶段，为未来部署做准备；训练算子投入使其竞争力延伸到训练侧；前沿学术成果（VC-Attention）快速工程化至生产链路；CI 与代码治理支撑日益增长的多架构 kernel 矩阵。这些共同巩固了其在 LLM 推理与多模态生成生态中的前沿地位。

## 详细提交记录

### [7b7db10](https://github.com/flashinfer-ai/flashinfer/commit/7b7db10941ad5153417532e48ba703b1ba7348ef)

- **作者**: eigen
- **时间**: 2026-10-22T23:50:59Z
- **提交信息**: perf(cake_kda): faster packed KDA chunked grad on SM100 / SM103 / SM107 (#7023)

The packed KDA chunked training forward and backward has one Cake
variant: BF16 tensors with an FP32 gate, laid out as `[1, S, H, 128]`.
Its saving forward stores a saved set for the backward in `light`
(default) or `tape` mode; a no-save forward pairs with a
checkpoint-replay backward. This PR replaces the kernels of that variant
with a faster version behind the same public entry points. The baseline
is the previous Cake version of this kernel on main (#6787). The tables
below list the latency of both versions and the speedup for 14 shapes on
each of three GPUs. Across all shapes, GPUs and the forward, backward
and checkpoint columns, the speedup ranges from 1.435× to 1.892×.

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4**

| Shape (H, S) | fwd previous / this PR ms | fwd speedup | bwd previous
/ this PR ms | bwd speedup | ckpt fwd+bwd previous / this PR ms | ckpt
speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 2.049 / 1.292 | 1.586× | 5.044 / 2.984 | 1.691× |
9.119 / 5.558 | 1.641× |
| P2 (H=4, S=245028) | 2.013 / 1.309 | 1.538× | 5.007 / 3.068 | 1.632× |
8.993 / 5.681 | 1.583× |
| P3 (H=4, S=249866) | 2.079 / 1.324 | 1.571× | 5.189 / 3.119 | 1.664× |
9.325 / 5.758 | 1.620× |
| P4 (H=4, S=250340) | 2.069 / 1.332 | 1.553× | 5.143 / 3.135 | 1.641× |
9.251 / 5.794 | 1.597× |
| P5 (H=4, S=258574) | 2.102 / 1.367 | 1.538× | 5.207 / 3.222 | 1.616× |
9.351 / 5.948 | 1.572× |
| P6 (H=4, S=259042) | 2.081 / 1.363 | 1.527× | 5.165 / 3.227 | 1.601× |
9.296 / 5.949 | 1.563× |
| P7 (H=4, S=259584) | 2.143 / 1.357 | 1.579× | 5.357 / 3.218 | 1.665× |
9.602 / 5.927 | 1.620× |
| P8 (H=4, S=261393) | 2.026 / 1.378 | 1.470× | 5.100 / 3.255 | 1.567× |
9.110 / 6.002 | 1.518× |
| P9 (H=1, S=261393) | 0.797 / 0.450 | 1.773× | 1.758 / 0.929 | 1.892× |
3.291 / 2.031 | 1.620× |
| P10 (H=2, S=261393) | 1.188 / 0.753 | 1.578× | 2.858 / 1.728 | 1.654×
| 5.201 / 3.223 | 1.614× |
| P11 (H=8, S=261393) | 3.841 / 2.613 | 1.470× | 9.878 / 6.359 | 1.553×
| 17.488 / 11.589 | 1.509× |
| P12 (H=16, S=261393) | 7.911 / 5.093 | 1.553× | 21.090 / 13.490 |
1.563× | 36.917 / 23.634 | 1.562× |
| P13 (H=32, S=261393) | 13.824 / 7.820 | 1.768× | 38.690 / 24.594 |
1.573× | 66.340 / 40.165 | 1.652× |
| P14 (H=64, S=261393) | 26.511 / 16.015 | 1.655× | 76.066 / 47.409 |
1.604× | 129.050 / 79.415 | 1.625× |

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4**

| Shape (H, S) | fwd previous / this PR ms | fwd speedup | bwd previous
/ this PR ms | bwd speedup | ckpt fwd+bwd previous / this PR ms | ckpt
speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 2.186 / 1.404 | 1.557× | 5.530 / 3.250 | 1.702× |
9.893 / 6.056 | 1.634× |
| P2 (H=4, S=245028) | 2.143 / 1.409 | 1.521× | 5.477 / 3.303 | 1.658× |
9.770 / 6.124 | 1.595× |
| P3 (H=4, S=249866) | 2.226 / 1.427 | 1.560× | 5.697 / 3.382 | 1.685× |
10.132 / 6.230 | 1.626× |
| P4 (H=4, S=250340) | 2.210 / 1.436 | 1.538× | 5.615 / 3.372 | 1.665× |
10.032 / 6.246 | 1.606× |
| P5 (H=4, S=258574) | 2.212 / 1.475 | 1.500× | 5.708 / 3.496 | 1.633× |
10.125 / 6.451 | 1.569× |
| P6 (H=4, S=259042) | 2.211 / 1.468 | 1.506× | 5.654 / 3.478 | 1.625× |
10.073 / 6.415 | 1.570× |
| P7 (H=4, S=259584) | 2.278 / 1.464 | 1.557× | 5.853 / 3.482 | 1.681× |
10.411 / 6.414 | 1.623× |
| P8 (H=4, S=261393) | 2.155 / 1.486 | 1.450× | 5.569 / 3.507 | 1.588× |
9.891 / 6.479 | 1.527× |
| P9 (H=1, S=261393) | 0.799 / 0.483 | 1.655× | 1.875 / 0.992 | 1.891× |
3.492 / 2.235 | 1.563× |
| P10 (H=2, S=261393) | 1.232 / 0.814 | 1.512× | 3.087 / 1.862 | 1.658×
| 5.563 / 3.488 | 1.595× |
| P11 (H=8, S=261393) | 4.302 / 2.826 | 1.523× | 11.333 / 6.951 | 1.630×
| 19.939 / 12.932 | 1.542× |
| P12 (H=16, S=261393) | 8.465 / 5.486 | 1.543× | 23.266 / 14.983 |
1.553× | 40.204 / 26.112 | 1.540× |
| P13 (H=32, S=261393) | 14.941 / 8.985 | 1.663× | 42.796 / 28.770 |
1.488× | 72.666 / 47.313 | 1.536× |
| P14 (H=64, S=261393) | 28.884 / 18.166 | 1.590× | 84.267 / 55.394 |
1.521× | 141.783 / 92.151 | 1.539× |

**NVIDIA R200 (sm_107a, 216 SMs), CUDA 13.4**

| Shape (H, S) | fwd previous / this PR ms | fwd speedup | bwd previous
/ this PR ms | bwd speedup | ckpt fwd+bwd previous / this PR ms | ckpt
speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 1.372 / 0.854 | 1.607× | 3.371 / 2.087 | 1.615× |
6.125 / 3.794 | 1.615× |
| P2 (H=4, S=245028) | 1.323 / 0.854 | 1.549× | 3.307 / 2.116 | 1.563× |
5.955 / 3.827 | 1.556× |
| P3 (H=4, S=249866) | 1.369 / 0.860 | 1.593× | 3.409 / 2.163 | 1.576× |
6.152 / 3.881 | 1.585× |
| P4 (H=4, S=250340) | 1.362 / 0.871 | 1.564× | 3.393 / 2.163 | 1.569× |
6.113 / 3.902 | 1.567× |
| P5 (H=4, S=258574) | 1.371 / 0.888 | 1.544× | 3.437 / 2.233 | 1.539× |
6.182 / 4.003 | 1.544× |
| P6 (H=4, S=259042) | 1.373 / 0.893 | 1.539× | 3.440 / 2.231 | 1.542× |
6.189 / 4.014 | 1.542× |
| P7 (H=4, S=259584) | 1.441 / 0.882 | 1.634× | 3.605 / 2.223 | 1.622× |
6.485 / 3.986 | 1.627× |
| P8 (H=4, S=261393) | 1.341 / 0.897 | 1.495× | 3.415 / 2.238 | 1.526× |
6.096 / 4.030 | 1.513× |
| P9 (H=1, S=261393) | 0.515 / 0.320 | 1.607× | 1.191 / 0.662 | 1.799× |
2.225 / 1.300 | 1.711× |
| P10 (H=2, S=261393) | 0.803 / 0.504 | 1.593× | 1.938 / 1.200 | 1.615×
| 3.547 / 2.204 | 1.609× |
| P11 (H=8, S=261393) | 2.473 / 1.688 | 1.465× | 6.487 / 4.351 | 1.491×
| 11.434 / 7.720 | 1.481× |
| P12 (H=16, S=261393) | 5.377 / 3.558 | 1.511× | 14.628 / 10.004 |
1.462× | 25.424 / 17.093 | 1.487× |
| P13 (H=32, S=261393) | 9.140 / 5.086 | 1.797× | 25.720 / 17.927 |
1.435× | 44.035 / 28.089 | 1.568× |
| P14 (H=64, S=261393) | 17.405 / 11.388 | 1.528× | 50.576 / 35.006 |
1.445× | 85.381 / 57.779 | 1.478× |

Cake ships no other data type, layout or form of this kernel; the family
covers `sm_100a`, `sm_103a` and `sm_107a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added architecture-aware planning and dispatch for KDA training on
SM100, SM103, and SM107.
* Expanded segmented execution with proportional segment planning,
optional saved boundary states, and overlapping launches.
* Added version 3 light saved sets and a `light_states` backward path;
tape mode remains available.
* Added workspace and memory reporting that reflects execution paths and
saved-state requirements.

* **Documentation**
* Updated KDA training guidance for saved-set versions, segmented
execution, and backward recomputation behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [8ba1ba1](https://github.com/flashinfer-ai/flashinfer/commit/8ba1ba1d6b04baf436f150542dd628a54f53b16a)

- **作者**: eigen
- **时间**: 2026-10-22T23:45:14Z
- **提交信息**: feat(cake_gdn_cp): dedicated SM 10.7 T-precompute program for the context-parallel GDN prefill route (#7018)

The T-precompute kernel is the first stage of the Cake context-parallel
GDN prefill route. It reads K and beta and writes the per-block T matrix
that the later stages use. The kernel has four variants: fp16 and bf16
activations, each available with int64 prefix sums or in an
int32-prefix-sum ("cu32") form. This PR adds a dedicated SM 10.7
(sm_107a, Rubin) program for the fp16-activation variant with int64
prefix sums. Before this PR, SM 10.7 ran the architecture-neutral
program that SM 10.0 / SM 10.3 still use unchanged, and the
bf16-activation variant on SM 10.7 still uses it. Compared with that
previous Cake version on the same GPU, the new program has a
geometric-mean speedup of 1.048 (4.8% faster) over 48 shapes, ranging
from 1.031 to 1.066, and is faster on every shape.

**NVIDIA R200 (Rubin, sm_107a, compute capability 10.7), CUDA 13.5.
Median GPU time with a cold L2 cache, previous and new programs paired
and interleaved in the same session, seed 17; speedup = previous / this
PR.**

| Shape | Previous Cake (ms) | This PR (ms) | Speedup |
|---|--:|--:|--:|
| T=16384 Hk=2 Hsab=8 seq_lens=[16384] | 0.01782 | 0.01699 | 1.0489 |
| T=65536 Hk=16 Hsab=16 seq_lens=[65536] | 0.12413 | 0.12007 | 1.0338 |
| T=32768 Hk=16 Hsab=16 seq_lens=[32768] | 0.06485 | 0.06221 | 1.0424 |
| T=8192 Hk=16 Hsab=16 seq_lens=[8192] | 0.01888 | 0.01797 | 1.0507 |
| T=4096 Hk=16 Hsab=16 seq_lens=[4096] | 0.01152 | 0.01101 | 1.0465 |
| T=8192 Hk=16 Hsab=16 seq_lens=[6144, 2048] | 0.01910 | 0.01826 |
1.0464 |
| T=8192 Hk=16 Hsab=16 seq_lens=[4096, 4096] | 0.01885 | 0.01792 |
1.0518 |
| T=8192 Hk=16 Hsab=16 seq_lens=[2048, 6144] | 0.01987 | 0.01907 |
1.0420 |
| T=8192 Hk=16 Hsab=16 seq_lens=[1024, 7168] | 0.02102 | 0.02022 |
1.0396 |
| T=65536 Hk=2 Hsab=8 seq_lens=[65536] | 0.06237 | 0.05934 | 1.0510 |
| T=32768 Hk=2 Hsab=8 seq_lens=[32768] | 0.03306 | 0.03143 | 1.0519 |
| T=8192 Hk=2 Hsab=8 seq_lens=[8192] | 0.01094 | 0.01040 | 1.0523 |
| T=4096 Hk=2 Hsab=8 seq_lens=[4096] | 0.00726 | 0.00701 | 1.0365 |
| T=8192 Hk=2 Hsab=8 seq_lens=[6144, 2048] | 0.01098 | 0.01043 | 1.0521
|
| T=8192 Hk=2 Hsab=8 seq_lens=[4096, 4096] | 0.01098 | 0.01037 | 1.0585
|
| T=8192 Hk=2 Hsab=8 seq_lens=[2048, 6144] | 0.01043 | 0.01002 | 1.0415
|
| T=8192 Hk=2 Hsab=8 seq_lens=[1024, 7168] | 0.01149 | 0.01091 | 1.0528
|
| T=65536 Hk=4 Hsab=16 seq_lens=[65536] | 0.12048 | 0.11405 | 1.0564 |
| T=32768 Hk=4 Hsab=16 seq_lens=[32768] | 0.06253 | 0.05965 | 1.0483 |
| T=16384 Hk=4 Hsab=16 seq_lens=[16384] | 0.03318 | 0.03158 | 1.0506 |
| T=8192 Hk=4 Hsab=16 seq_lens=[8192] | 0.01789 | 0.01706 | 1.0488 |
| T=4096 Hk=4 Hsab=16 seq_lens=[4096] | 0.01106 | 0.01050 | 1.0534 |
| T=8192 Hk=4 Hsab=16 seq_lens=[6144, 2048] | 0.01822 | 0.01741 | 1.0468
|
| T=8192 Hk=4 Hsab=16 seq_lens=[4096, 4096] | 0.01783 | 0.01702 | 1.0470
|
| T=8192 Hk=4 Hsab=16 seq_lens=[2048, 6144] | 0.01901 | 0.01814 | 1.0476
|
| T=8192 Hk=4 Hsab=16 seq_lens=[1024, 7168] | 0.02003 | 0.01933 | 1.0364
|
| T=65536 Hk=8 Hsab=32 seq_lens=[65536] | 0.23719 | 0.22311 | 1.0631 |
| T=32768 Hk=8 Hsab=32 seq_lens=[32768] | 0.12085 | 0.11445 | 1.0559 |
| T=16384 Hk=8 Hsab=32 seq_lens=[16384] | 0.06275 | 0.05986 | 1.0484 |
| T=8192 Hk=8 Hsab=32 seq_lens=[8192] | 0.03331 | 0.03178 | 1.0483 |
| T=4096 Hk=8 Hsab=32 seq_lens=[4096] | 0.01792 | 0.01712 | 1.0467 |
| T=65536 Hk=16 Hsab=32 seq_lens=[65536] | 0.23927 | 0.22544 | 1.0613 |
| T=32768 Hk=16 Hsab=32 seq_lens=[32768] | 0.12208 | 0.11595 | 1.0529 |
| T=16384 Hk=16 Hsab=32 seq_lens=[16384] | 0.06359 | 0.06103 | 1.0420 |
| T=8192 Hk=16 Hsab=32 seq_lens=[8192] | 0.03399 | 0.03248 | 1.0463 |
| T=4096 Hk=16 Hsab=32 seq_lens=[4096] | 0.01824 | 0.01746 | 1.0449 |
| T=65536 Hk=16 Hsab=48 seq_lens=[65536] | 0.35426 | 0.33245 | 1.0656 |
| T=32768 Hk=16 Hsab=48 seq_lens=[32768] | 0.17944 | 0.16899 | 1.0618 |
| T=16384 Hk=16 Hsab=48 seq_lens=[16384] | 0.09207 | 0.08726 | 1.0550 |
| T=8192 Hk=16 Hsab=48 seq_lens=[8192] | 0.04810 | 0.04610 | 1.0434 |
| T=4096 Hk=16 Hsab=48 seq_lens=[4096] | 0.02645 | 0.02538 | 1.0423 |
| T=16384 Hk=16 Hsab=16 seq_lens=[16384] | 0.03475 | 0.03322 | 1.0462 |
| T=65536 Hk=32 Hsab=32 seq_lens=[65536] | 0.24250 | 0.23482 | 1.0327 |
| T=32768 Hk=32 Hsab=32 seq_lens=[32768] | 0.12477 | 0.12098 | 1.0313 |
| T=16384 Hk=32 Hsab=32 seq_lens=[16384] | 0.06535 | 0.06263 | 1.0434 |
| T=8192 Hk=32 Hsab=32 seq_lens=[8192] | 0.03498 | 0.03341 | 1.0469 |
| T=4096 Hk=32 Hsab=32 seq_lens=[4096] | 0.01891 | 0.01811 | 1.0442 |
| T=193 Hk=2 Hsab=4 seq_lens=[64, 64, 65] | 0.00397 | 0.00378 | 1.0508 |

Besides this kernel, the Cake CP GDN prefill family ships these kernels
on SM 10.0, SM 10.3 and SM 10.7: the main prefill kernels (fp16 and bf16
activations, equal-head and generic-tail forms), the MN precompute, QK
norm and normalized-final-state kernels (fp16 and bf16), the fp32 SIMT
state-fixup kernel, and the state gather/scatter kernels (bf16, fp16 and
fp32 state with int32 or int64 indices); the two tensor-core (UTCMMA)
state-fixup kernels and the int32-prefix-sum T-precompute forms ship on
SM 10.0 / SM 10.3 only, so the family covers sm_100a, sm_103a and
sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for a new `t_precompute` implementation on compatible
NVIDIA GPUs.
* **Bug Fixes**
* Improved validation of inputs and launch parameters, so invalid
tensors or configuration values are reported as errors before the
operation runs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [73f6ceb](https://github.com/flashinfer-ai/flashinfer/commit/73f6cebdab710e7b7eefc0b437542037995d0e1d)

- **作者**: Yang Xu
- **时间**: 2026-10-22T22:40:04Z
- **提交信息**: chore: make Anerudhan a code owner for all paths (#7055)

<!-- .github/pull_request_template.md -->

## 📌 Description

Directory-specific CODEOWNERS rules override the catch-all, so Anerudhan
currently cannot satisfy code-owner review requirements for several
areas, including autotuner. Add `@Anerudhan` to the 45 rules that omit
him so he is an owner in all 56 existing rules, and document him in the
full-codebase approver list.

## 🔍 Related Issues

The missing autotuner ownership coverage surfaced during review of
#6894.

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

Ownership-only validation: all 56 rules include `@Anerudhan` exactly
once; every path pattern and existing owner list is preserved.
`pre-commit run --files .github/CODEOWNERS` and `git diff --check`
passed. Runtime tests and full-repository pre-commit checks were not
run.

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

Follows the existing full-codebase approver convention in the manually
maintained CODEOWNERS file. The change takes effect for PR review
requirements after it lands on the base branch.

AI-assisted change and validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated code review ownership assignments across several project
areas. No ownership rules were added or removed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0602a5b](https://github.com/flashinfer-ai/flashinfer/commit/0602a5b9929d0bc2322d16c56088d74b6e0413aa)

- **作者**: Xiaoming Yin
- **时间**: 2026-10-22T22:08:08Z
- **提交信息**: fix(sampling): reserve RNG offsets for the current call (#5651)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix generator-managed RNG offset reservation in sampling, including
Philox draw reuse across consecutive speculative sampling calls.

`get_seed_and_offset()` currently advances the generator and returns the
advanced offset, so the current call starts beyond the range it just
reserved. `chain_speculative_sampling()` also reserves `B * (N + 1)`,
while rejection consumes `N + 2` draws per Philox stream: `N + 1` across
the two acceptance loops, plus one recovery draw.

For `B=1, N=3`, consecutive calls currently start at offsets 4 and 8. A
rejecting first call consumes offsets 4 through 8, reusing offset 8 in
the next call.

This PR:

- Returns the current offset before advancing the generator to the end
of the current call's reservation. This keeps reservations associated
with their own calls even when successive call shapes differ.
- Changes the speculative sampling reservation to `B * (N + 2)`,
retaining the existing batch multiplier and four-draw alignment. The
example above now starts at offsets 0 and 8, with the first call
consuming offsets 0 through 4.
- Adds two focused regression tests (three parametrized cases, 44 lines)
covering the helper contract and consecutive rejecting speculative calls
with different lengths.

## 🔍 Related Issues

Fixes #5637.

Thanks to @cudabinary for the detailed report and reproducer.

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

`pre-commit run --all-files` passed with pre-commit 4.6.2 and the
repository-pinned hook versions: 15 hooks passed, and the broken-symlink
check was skipped because there were no matching files. No tracked files
were modified. `git diff --check` also passed.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Validated on NVIDIA H800 PCIe with PyTorch 2.8.0+cu128 and CUDA 12.8,
using the sampling CUDA module freshly compiled from source:

- All three new regression cases fail against the original
implementation and pass with this fix.
- The helper test checks initial offsets 0 and 12, varying reservation
sizes, four-draw alignment, and seed preservation.
- The speculative test forces rejection for consecutive `N=3` and `N=1`
calls, checks generator cursor advancement, and compares all three
returned tensors exactly against explicit seed/offset calls. It also
verifies that explicit seed/offset calls do not advance the generator.
- The related sampling test selection passes: **174 passed, 1872
deselected** (three deprecation warnings). This includes the three new
cases and 171 existing cases.

```bash
python -m pytest -q tests/utils/test_sampling.py \
  -k 'reserves_current_range or chain_speculative_sampling or seed_offset or sampling_with_default_device_cuda or int64_indices_sampling' \
  --tb=short
```

The complete repository test suite and cross-architecture validation
were not run; the full-suite checkbox above is therefore left unchecked.

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

The helper is shared by generator-managed sampling APIs, so fixed-seed
output sequences may change beyond speculative sampling. This is an
intentional consequence of returning the start of the current
reservation. Explicit seed/offset calls are unchanged.

This PR does not change CUDA kernels or non-speculative callers'
reservation sizes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved random-number state handling for speculative sampling,
helping ensure sufficient state is reserved and generator offsets
advance consistently.
* Explicitly supplied seeds and offsets now reproduce sampling results
without further advancing the generator.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b905213](https://github.com/flashinfer-ai/flashinfer/commit/b90521314b21a5c9b23aebaa7c09398000d01374)

- **作者**: eigen
- **时间**: 2026-10-22T21:48:48Z
- **提交信息**: perf(cake_stepfun_moe): add tile-128 MXFP8 FC1 and FC2 kernels for the StepFun fused MoE (sm_100a, sm_103a) (#7037)

Cake's StepFun SwiGLU fused MoE (hidden 4096, intermediate 1536, 64
experts, top-k 8) comes in five data-type variants: bf16, fp8 (e4m3),
mxfp8, nvfp4 and per-token NVFP4 (`nvfp4_bf16tok`). It is built from 113
kernels per architecture. This PR delivers the MXFP8 family's new
tile-128 FC1 (+SwiGLU) and FC2 kernels. With them, the default plan now
selects tile 128 at 1024 tokens; before, it could only pick tile 64 or
256. The baseline is the previous Cake version of this kernel, the
package on FlashInfer main from #6934. Both versions were measured with
whole-graph CUDA-graph replay, same node and GPU, interleaved pairs.
MXFP8 at 1024 tokens is the only consistent gain: 1.047x / 1.046x on
GB300 and 1.044x / 1.071x on B200. Every other row is within
0.984x–1.048x (GB300 0.996x–1.010x, B200 0.984x–1.048x), and the two
B200 extremes (mxfp8 at 2048 tokens and bf16 at 1024 tokens, both at
limit 16) are noisy large-token cells. Latencies are whole-graph medians
in µs. Speedup = previous / this PR, the median over the interleaved
pairs, so >1.000x means this PR is faster. Shapes: 5 families × tokens
{8, 64, 512, 1024, 2048} × limit {7, 16} = 50 rows per GPU.

**NVIDIA GB300, sm_103a, CUDA 13.4 (nvcc 13.4, torch CUDA 13.0), driver
580.159.03** (6 interleaved pairs per row)

| precision | tokens | limit | previous Cake (µs) | this PR (µs) |
speedup (previous / this PR) |
|---|---:|---:|---:|---:|---:|
| bf16 | 8 | 7 | 227.3 | 227.8 | 0.998x |
| bf16 | 8 | 16 | 227.5 | 227.7 | 0.999x |
| bf16 | 64 | 7 | 364.9 | 365.1 | 0.999x |
| bf16 | 64 | 16 | 364.8 | 365.1 | 0.999x |
| bf16 | 512 | 7 | 387.4 | 386.8 | 1.002x |
| bf16 | 512 | 16 | 387.2 | 386.7 | 1.001x |
| bf16 | 1024 | 7 | 412.1 | 412.7 | 0.999x |
| bf16 | 1024 | 16 | 412.3 | 412.7 | 0.999x |
| bf16 | 2048 | 7 | 546.5 | 547.2 | 0.999x |
| bf16 | 2048 | 16 | 547.8 | 548.8 | 0.999x |
| fp8 | 8 | 7 | 130.1 | 130.0 | 1.001x |
| fp8 | 8 | 16 | 130.0 | 130.0 | 0.999x |
| fp8 | 64 | 7 | 201.5 | 201.7 | 0.999x |
| fp8 | 64 | 16 | 201.5 | 201.8 | 0.999x |
| fp8 | 512 | 7 | 217.4 | 218.0 | 0.997x |
| fp8 | 512 | 16 | 217.5 | 217.9 | 0.998x |
| fp8 | 1024 | 7 | 235.0 | 235.8 | 0.996x |
| fp8 | 1024 | 16 | 235.1 | 235.8 | 0.997x |
| fp8 | 2048 | 7 | 313.7 | 314.3 | 0.998x |
| fp8 | 2048 | 16 | 313.8 | 314.4 | 0.998x |
| mxfp8 | 8 | 7 | 133.7 | 134.0 | 0.998x |
| mxfp8 | 8 | 16 | 133.7 | 134.0 | 0.997x |
| mxfp8 | 64 | 7 | 223.6 | 223.7 | 1.000x |
| mxfp8 | 64 | 16 | 223.5 | 223.7 | 0.999x |
| mxfp8 | 512 | 7 | 227.7 | 227.7 | 1.000x |
| mxfp8 | 512 | 16 | 227.6 | 227.8 | 1.000x |
| mxfp8 | 1024 | 7 | 260.0 | 248.4 | 1.047x |
| mxfp8 | 1024 | 16 | 260.0 | 248.6 | 1.046x |
| mxfp8 | 2048 | 7 | 351.7 | 350.2 | 1.005x |
| mxfp8 | 2048 | 16 | 351.9 | 350.1 | 1.006x |
| nvfp4 | 8 | 7 | 79.2 | 78.4 | 1.010x |
| nvfp4 | 8 | 16 | 79.2 | 78.4 | 1.010x |
| nvfp4 | 64 | 7 | 128.4 | 128.5 | 0.999x |
| nvfp4 | 64 | 16 | 128.4 | 128.4 | 1.000x |
| nvfp4 | 512 | 7 | 139.3 | 139.9 | 0.996x |
| nvfp4 | 512 | 16 | 139.3 | 139.8 | 0.997x |
| nvfp4 | 1024 | 7 | 169.4 | 168.8 | 1.004x |
| nvfp4 | 1024 | 16 | 169.4 | 168.9 | 1.003x |
| nvfp4 | 2048 | 7 | 229.7 | 227.7 | 1.009x |
| nvfp4 | 2048 | 16 | 229.7 | 227.8 | 1.009x |
| nvfp4_bf16tok | 8 | 7 | 85.2 | 85.2 | 1.001x |
| nvfp4_bf16tok | 8 | 16 | 85.1 | 85.0 | 1.001x |
| nvfp4_bf16tok | 64 | 7 | 134.8 | 135.1 | 0.998x |
| nvfp4_bf16tok | 64 | 16 | 134.9 | 135.2 | 0.997x |
| nvfp4_bf16tok | 512 | 7 | 150.9 | 151.4 | 0.997x |
| nvfp4_bf16tok | 512 | 16 | 151.0 | 151.4 | 0.997x |
| nvfp4_bf16tok | 1024 | 7 | 190.9 | 191.0 | 0.999x |
| nvfp4_bf16tok | 1024 | 16 | 190.8 | 191.0 | 0.999x |
| nvfp4_bf16tok | 2048 | 7 | 270.8 | 269.2 | 1.006x |
| nvfp4_bf16tok | 2048 | 16 | 270.8 | 269.1 | 1.006x |

**NVIDIA B200, sm_100a, CUDA 13.4 (nvcc 13.4, torch CUDA 13.0), driver
580.82.07** (6 interleaved pairs per row)

| precision | tokens | limit | previous Cake (µs) | this PR (µs) |
speedup (previous / this PR) |
|---|---:|---:|---:|---:|---:|
| bf16 | 8 | 7 | 231.2 | 231.1 | 1.000x |
| bf16 | 8 | 16 | 231.1 | 231.1 | 1.001x |
| bf16 | 64 | 7 | 374.2 | 376.3 | 0.994x |
| bf16 | 64 | 16 | 374.1 | 376.4 | 0.993x |
| bf16 | 512 | 7 | 395.8 | 396.3 | 1.000x |
| bf16 | 512 | 16 | 397.3 | 396.4 | 1.001x |
| bf16 | 1024 | 7 | 443.2 | 439.4 | 1.011x |
| bf16 | 1024 | 16 | 469.1 | 440.7 | 1.048x |
| bf16 | 2048 | 7 | 645.0 | 649.7 | 0.985x |
| bf16 | 2048 | 16 | 655.5 | 659.4 | 0.996x |
| fp8 | 8 | 7 | 133.0 | 132.9 | 1.000x |
| fp8 | 8 | 16 | 133.0 | 132.9 | 1.000x |
| fp8 | 64 | 7 | 206.6 | 206.4 | 1.001x |
| fp8 | 64 | 16 | 206.6 | 206.4 | 1.001x |
| fp8 | 512 | 7 | 223.0 | 222.9 | 1.001x |
| fp8 | 512 | 16 | 223.1 | 223.1 | 1.000x |
| fp8 | 1024 | 7 | 249.8 | 249.7 | 0.999x |
| fp8 | 1024 | 16 | 248.2 | 247.4 | 1.005x |
| fp8 | 2048 | 7 | 356.2 | 354.0 | 1.004x |
| fp8 | 2048 | 16 | 356.6 | 357.8 | 0.995x |
| mxfp8 | 8 | 7 | 136.6 | 136.7 | 1.000x |
| mxfp8 | 8 | 16 | 136.8 | 136.5 | 1.001x |
| mxfp8 | 64 | 7 | 229.6 | 229.5 | 1.001x |
| mxfp8 | 64 | 16 | 229.3 | 229.6 | 0.999x |
| mxfp8 | 512 | 7 | 234.7 | 234.6 | 1.001x |
| mxfp8 | 512 | 16 | 234.7 | 234.5 | 1.001x |
| mxfp8 | 1024 | 7 | 281.8 | 268.6 | 1.044x |
| mxfp8 | 1024 | 16 | 282.6 | 263.3 | 1.071x |
| mxfp8 | 2048 | 7 | 405.7 | 406.0 | 0.996x |
| mxfp8 | 2048 | 16 | 403.1 | 416.0 | 0.984x |
| nvfp4 | 8 | 7 | 81.1 | 81.1 | 0.999x |
| nvfp4 | 8 | 16 | 81.2 | 81.3 | 0.999x |
| nvfp4 | 64 | 7 | 132.4 | 132.7 | 0.999x |
| nvfp4 | 64 | 16 | 132.6 | 132.6 | 1.000x |
| nvfp4 | 512 | 7 | 146.6 | 146.0 | 1.005x |
| nvfp4 | 512 | 16 | 146.5 | 146.1 | 1.003x |
| nvfp4 | 1024 | 7 | 187.2 | 186.6 | 1.003x |
| nvfp4 | 1024 | 16 | 187.2 | 186.6 | 1.004x |
| nvfp4 | 2048 | 7 | 248.3 | 246.5 | 1.009x |
| nvfp4 | 2048 | 16 | 250.8 | 248.2 | 1.010x |
| nvfp4_bf16tok | 8 | 7 | 88.3 | 88.0 | 1.004x |
| nvfp4_bf16tok | 8 | 16 | 88.3 | 87.9 | 1.005x |
| nvfp4_bf16tok | 64 | 7 | 138.6 | 138.3 | 1.003x |
| nvfp4_bf16tok | 64 | 16 | 138.4 | 138.0 | 1.002x |
| nvfp4_bf16tok | 512 | 7 | 158.1 | 158.0 | 1.001x |
| nvfp4_bf16tok | 512 | 16 | 158.1 | 158.0 | 1.001x |
| nvfp4_bf16tok | 1024 | 7 | 204.0 | 203.0 | 1.005x |
| nvfp4_bf16tok | 1024 | 16 | 203.9 | 203.0 | 1.004x |
| nvfp4_bf16tok | 2048 | 7 | 293.7 | 292.6 | 1.007x |
| nvfp4_bf16tok | 2048 | 16 | 293.7 | 292.9 | 1.004x |

The other Cake variants of this kernel (bf16, fp8 (e4m3), nvfp4 and
per-token NVFP4) ship unchanged in this PR, and all five families ship
for sm_100a (B200) and sm_103a (GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added MXFP8 tile-128 support for the Cake StepFun MoE FC1 and FC2
stages, including full-pipeline routing on supported GPU architectures.
- **Bug Fixes**
- Improved input validation for select MoE operations, rejecting
unsupported parameter values before launch.
- **Tests**
- Updated registry and route coverage to include the new tile-128
programs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6fc0f52](https://github.com/flashinfer-ai/flashinfer/commit/6fc0f52beae043fbca07a8fb3c63c24b71466623)

- **作者**: ameynaik-hub
- **时间**: 2026-10-22T21:41:32Z
- **提交信息**: Gdn rubin stp t1 (#6604)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds a GDN T=1 decode kernel with a bfloat16 state tuned for Rubin
(compute capability 10.7, `sm_107a`), routes
`gated_delta_rule_decode_pretranspose` to it on SM107, and adds **uGPU
localization**: with a state pool from the new `ugpu_state_pool`, each
of Rubin's two dies updates the half of every state that lives in its
own memory, on its own SMs. On a Rubin VR200 at B = 512, HV = 64 this
takes the decode from 187.0 µs (61% of DRAM peak) to 132.6 µs (85%),
1.41× faster, and to 87–88% of DRAM peak from B = 1024. Nothing changes
on other GPUs.

### Why Rubin needs its own kernel

1. **Too little data in flight.** The generic T=1 wide_vec kernel loads
four state rows per thread, waits, computes, and repeats. Rubin's DRAM
bandwidth is about 2.5× B200's, so this keeps too few bytes in flight
and the warps mostly wait on memory (61–63% of DRAM peak at large
batch).
2. **Then too many instructions.** Requesting the whole state tile at
once fixes the waiting, but the extra copy and bookkeeping instructions
make the kernel issue-bound: Rubin's instruction issue rate grew only
about 1.8× over B200. Cutting instructions (below) brings the whole-GPU
kernel to 71%.
3. **Then the die-to-die link.** With an ordinary allocation, memory
pages are interleaved across both dies, so about half of all state bytes
cross the die-to-die link. That caps even a plain copy kernel near 68%
of DRAM peak on the whole GPU, against 90% when each die reads and
writes only its own memory. uGPU localization removes that crossing and
brings the kernel to 88%.

### Kernel: `flashinfer/gdn_kernels/gdn_decode_bf16_state_rubin.py`
(new)

- **Whole-tile copy.** 64-row state tiles, two CTAs per head. At entry
each CTA issues `cp.async` for its whole 16 KB state tile into shared
memory and then waits group by group. The copy partition and the compute
mapping coincide, so the state needs no CTA barrier.
- **No warp-0 precompute.** q/k normalization and the gates are computed
in registers by each 16-lane group (no precompute + barrier); v is
loaded at entry; the four row dot products are reduced with a
transpose-reduce (5 shuffles instead of 16) and issued as FFMA2.
- **L2 prefetch.** After its stores each CTA prefetches into L2
(evict_last) the state tile and q/k/v/a/b lines of the tile about 1.2
residency generations ahead (`pf_dist = num_SMs * 25 // 3` tiles).
- **Instruction cuts** (keyword arguments, all on by default; together
about 38% fewer warp-instructions): row-pair FFMA2 without register
regrouping, vn computed in the reducing lane, a hoisted output pointer,
state write-back through the copy partition, bf16→f32 by bit placement,
compile-time q/k/v/a/b/o strides, cheaper prefetch bookkeeping.
- **Numerics unchanged.** Same math and FMA order as the generic
wide_vec kernel: outputs and the updated state are **bitwise equal** to
it wherever the generic dispatcher uses wide_vec (B·HV ≥ 512). The
wrapper `gated_delta_rule_t1_rubin` raises `ValueError` off compute
capability 10.7.

### uGPU localization

Rubin VR200 is two dies (locality domains) of 106 SMs each, each with
its own DRAM.

- **Pool:** `flashinfer.gdn_decode.ugpu_state_pool(pool_size, HV)`
returns a bf16 pool of shape `[pool_size, HV, 2, V // 2, K]`. Half `t`
of every state lives in die `t`'s memory; element `[s, h, t, r, k]` is
element `[s, h, t * V // 2 + r, k]` of the usual `[pool_size, HV, V, K]`
pool, so an existing pool converts with `ugpu_pool.copy_(pool.view(P,
HV, 2, V // 2, K))`. It is built by `empty_per_locality_domain`: one
virtual address range, two physical allocations (`cuMemCreate` with
`CU_MEM_LOCATION_TYPE_DEVICE_LOCALITY_DOMAIN`, one per die) mapped into
it, released when the tensor is freed.
- **SMs:** `split_device_green_ctx_by_locality_domain` creates one green
context per die (`cuDevSmResourceSplit` with
`CU_DEV_SM_RESOURCE_GROUP_LOCALITY_DOMAIN_ID | BACKFILL`; 100 native + 6
backfilled SMs per die, so all 212 SMs work). Created on first use and
cached per device.
- **Launch:** when `initial_state` is such a pool,
`gated_delta_rule_decode_pretranspose` forks from the current stream,
runs the Rubin kernel on die `t`'s green-context stream for the V/2
value rows of half `t` (state rows are independent in the T=1 update),
with the L2 prefetch distance scaled to that die's SM count, and joins
back. No other argument changes; any batch order and slot indices, split
read/write pools and -1 padding work. CUDA-graph capturable after one
eager call. Bitwise equal to one launch over an ordinary pool.

Usage (the decode call itself is unchanged):

```python
from flashinfer.gdn_decode import gated_delta_rule_decode_pretranspose, ugpu_state_pool

pool = ugpu_state_pool(num_slots, num_v_heads)  # bf16 [num_slots, HV, 2, 64, 128]

out, _ = gated_delta_rule_decode_pretranspose(
    q, k, v, None, A_log, a, dt_bias, b,
    initial_state=pool, initial_state_indices=slot_idx,
)
```

### API (`gated_delta_rule_decode_pretranspose`)

- `backend="auto"` (default): with a `ugpu_state_pool`, the
uGPU-localized Rubin kernel. With an ordinary pool on SM107, T = 1,
bfloat16 state, K = V = 128 and B·HV ≥ 512, the Rubin kernel on the
whole GPU. Every other GPU and shape keeps today's dispatch.
- `backend="rubin"` (new): forces the Rubin kernel at any batch size;
`ValueError` on other GPUs or outside T = 1 / bfloat16 state / K = V =
128.
- `backend="flashinfer"`: always the generic FlashInfer kernels (rejects
a uGPU pool).

### Benchmark

`flashinfer_benchmark.py --routine gated_delta_rule_decode` gets `rubin`
and `rubin_ugpu` backends (listed for 10.7 only; `rubin_ugpu` times a
`ugpu_state_pool` copy of the same pool). Its `flashinfer` backend now
passes `backend="flashinfer"`, so one run compares the generic kernel,
the Rubin kernel and the Rubin kernel with a uGPU pool.

### Files

| File | Change |
|---|---|
| `flashinfer/gdn_kernels/gdn_decode_bf16_state_rubin.py` | new: Rubin
T=1 kernel and its `gated_delta_rule_t1_rubin` wrapper |
| `flashinfer/gdn_decode.py` | `backend="rubin"`, SM107 `auto` routing,
`ugpu_state_pool`, per-die launch |
| `flashinfer/green_ctx.py` | `get_locality_domain_count`,
`split_device_green_ctx_by_locality_domain`, `empty_per_locality_domain`
|
| `benchmarks/routines/gdn.py`,
`benchmarks/routines/flashinfer_benchmark_utils.py`,
`benchmarks/README.md` | `rubin` / `rubin_ugpu` backends |
| `docs/api/gdn_decode.rst`, `docs/api/green_ctx.rst` | Rubin and uGPU
sections |
| `tests/gdn/test_decode_bf16_state_rubin.py` (new),
`tests/gdn/test_decode_delta_rule.py`, `tests/utils/test_green_ctx.py` |
tests below |

### Performance

NVIDIA Rubin VR200 (TS4B, 212 SMs, two dies), clocks locked at max (SM
2376 MHz, memory 4752 MHz), driver 620.47, CUDA 13 / torch 2.14 (cu130).
HQ = HK = 16, K = V = 128, bfloat16 q/k/v and state, single pool, CUPTI
median, CUDA graph, `--refcheck` passed for every row and backend.

```
python benchmarks/flashinfer_benchmark.py --routine gated_delta_rule_decode --batch_size $B \
  --num_q_heads 16 --num_k_heads 16 --num_v_heads $HV --head_size 128 --state_dtype bfloat16 \
  --backends flashinfer rubin rubin_ugpu --refcheck
```

"Before" is the generic kernel (what SM107 ran before this PR).
Percentages are the benchmark's bytes (state read + write and inputs)
per second over the 19.15 TB/s DRAM peak. Speedup is `rubin` / `rubin` +
uGPU pool against before.

**HV = 64** (µs, and % of the 19.15 TB/s DRAM peak)

| B | before: generic | after: `rubin` (whole GPU) | after: `rubin` +
uGPU pool | speedup vs before |
|---:|---:|---:|---:|---:|
| 1 | 3.0 · 7% | 3.1 · 7% | **3.3 · 7%** | 0.98× / **0.92×** |
| 4 | 5.1 · 17% | 4.1 · 22% | **4.4 · 20%** | 1.25× / **1.16×** |
| 8 | 6.7 · 26% | 5.3 · 33% | **5.3 · 33%** | 1.25× / **1.26×** |
| 16 | 10.5 · 34% | 7.9 · 45% | **7.9 · 45%** | 1.33× / **1.32×** |
| 32 | 18.0 · 39% | 13.2 · 53% | **12.3 · 57%** | 1.36× / **1.46×** |
| 64 | 29.1 · 49% | 23.8 · 59% | **20.9 · 68%** | 1.22× / **1.39×** |
| 128 | 51.1 · 55% | 43.6 · 65% | **37.0 · 76%** | 1.17× / **1.38×** |
| 256 | 96.7 · 59% | 83.4 · 68% | **68.7 · 82%** | 1.16× / **1.41×** |
| 512 | 187.0 · 61% | 163.0 · 69% | **132.6 · 85%** | 1.15× / **1.41×**
|
| 1,024 | 366.6 · 62% | 322.1 · 70% | **260.1 · 87%** | 1.14× /
**1.41×** |
| 2,048 | 726.7 · 62% | 640.2 · 71% | **516.5 · 88%** | 1.14× /
**1.41×** |
| 4,096 | 1,447.7 · 63% | 1,276.9 · 71% | **1,029.9 · 88%** | 1.13× /
**1.41×** |
| 8,192 | 2,887.0 · 63% | 2,549.8 · 71% | **2,059.8 · 88%** | 1.13× /
**1.40×** |

**HV = 32** (µs, and % of the 19.15 TB/s DRAM peak)

| B | before: generic | after: `rubin` (whole GPU) | after: `rubin` +
uGPU pool | speedup vs before |
|---:|---:|---:|---:|---:|
| 1 | 3.0 · 4% | 3.1 · 4% | **3.3 · 3%** | 0.96× / **0.90×** |
| 4 | 3.5 · 13% | 3.5 · 13% | **3.7 · 12%** | 1.02× / **0.95×** |
| 8 | 5.1 · 18% | 4.1 · 21% | **4.3 · 21%** | 1.22× / **1.18×** |
| 16 | 6.8 · 26% | 5.3 · 33% | **5.3 · 34%** | 1.28× / **1.28×** |
| 32 | 10.2 · 35% | 7.9 · 45% | **7.8 · 45%** | 1.29× / **1.30×** |
| 64 | 17.9 · 40% | 13.3 · 53% | **12.4 · 57%** | 1.34× / **1.44×** |
| 128 | 28.8 · 49% | 24.0 · 59% | **21.0 · 67%** | 1.20× / **1.37×** |
| 256 | 51.0 · 56% | 43.7 · 65% | **36.9 · 77%** | 1.17× / **1.38×** |
| 512 | 96.8 · 59% | 83.7 · 68% | **69.2 · 82%** | 1.16× / **1.40×** |
| 1,024 | 187.2 · 61% | 163.5 · 69% | **133.1 · 85%** | 1.15× /
**1.41×** |
| 2,048 | 368.2 · 62% | 323.1 · 70% | **261.5 · 87%** | 1.14× /
**1.41×** |
| 4,096 | 728.9 · 62% | 642.5 · 71% | **518.3 · 88%** | 1.13× /
**1.41×** |
| 8,192 | 1,451.4 · 63% | 1,281.0 · 71% | **1,032.1 · 88%** | 1.13× /
**1.41×** |

With an ordinary pool, `auto` uses the Rubin kernel from B·HV ≥ 512;
below that it keeps the generic kernel, whose small-batch MTP path has a
different reduction order. For B ≤ 4 the uGPU pool costs up to 0.3 µs
over one launch (fork/join of the two die streams), which makes B = 1
(and B = 4 at HV = 32) up to 10% slower than before; from B = 8 it is as
fast or faster.

No change on other GPUs: the routing is gated to compute capability
10.7.

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

The repository's hooks were run with `pre-commit run --files <changed
files>`; all pass.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

- `tests/gdn/test_decode_bf16_state_rubin.py` (new, `arch_rubin`,
skipped unless compute capability 10.7):
- bitwise vs the generic kernel: B 1–512, HV 32/64, l2norm on/off,
single / split / shuffled pools, untouched pool slots, -1 padding;
- cuts on vs off, tile_v / stage_smem variants, fused-QKV views, padded
(strided) pools at two pool sizes, B = 2048 / 4096;
- API routing (`auto` == `rubin` == `flashinfer` bitwise at B·HV ≥ 512),
int64 indices, fp16 inputs;
- uGPU pool vs one launch, bitwise (B 1–512; single / split / shuffled
pools; -1 padding), and under CUDA graph capture.
- `tests/gdn/test_decode_delta_rule.py`:
`test_gdn_decode_bf16_state_t1_kernel` (fp32 reference with bf16 state)
parametrized over the Rubin kernel (`arch_rubin`); a test that
`backend="rubin"` and the kernel raise `ValueError` on other GPUs.
- `tests/utils/test_green_ctx.py`: one green context per locality domain
(SM counts), `empty_per_locality_domain` shape / per-part contiguity /
read-write, a device given without an index (skipped on GPUs with one
locality domain).

Results (the three files above plus
`tests/gdn/test_decode_pretranspose_bf16_padded_pool.py` and
`tests/gdn/test_cute_dsl_kernel_cache.py`):

| GPU | Commit | Passed | Skipped | Failed |
|---|---|---:|---:|---:|
| Rubin VR200 (TS3) | `53e923e` (head) | 675 | 1 (the off-SM107 test) |
0 |
| B200 | `69ebf13` (head before the last `main` merge, which touches
none of these files) | 435 | 241 (Rubin-only) | 0 |

The Rubin-only tests skip on B200 through the `arch_rubin` marker. On
B200 the benchmark's `flashinfer` backend (now called with
`backend="flashinfer"`) also passes `--refcheck` at B = 1 and 512.

## Reviewer Notes

- **Who allocates the pool.** uGPU localization needs the state pool to
come from `ugpu_state_pool`: memory placement is fixed at allocation,
and an ordinary allocation interleaves pages across both dies.
Frameworks that own the GDN state pool (vLLM, SGLang) would allocate it
this way on Rubin; everything after that is automatic. Only the state
pool is placed per die; q/k/v/a/b and the output stay where the caller
allocated them (about 1% of the bytes).
- **CUDA graphs.** The green contexts are created on the first uGPU call
and cached per device, so do one eager call before capture (as for any
JIT-compiled FlashInfer kernel).
- **`auto` threshold.** On an ordinary pool, `auto` uses the Rubin
kernel only from B·HV ≥ 512, where the result is bit-identical to the
generic kernel. Below that the Rubin kernel is also faster (for example
1.25× at B = 4, HV = 64) but not bit-identical to the generic MTP path;
it can be enabled later if wanted.
- **int64 indices.** The Rubin wrapper converts int64 slot indices to
int32. Separately (pre-existing, not changed here): the generic T=1
wide_vec kernel fails to compile with int64 `initial_state_indices`
(`TYPE_UNSTABLE_JOIN` at `if cache_idx < 0`), although the API docstring
allows int64.
- AI-assisted (Claude Code).

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5dded2b](https://github.com/flashinfer-ai/flashinfer/commit/5dded2b3b33324fba9ac072bb686e8e6680551b1)

- **作者**: eigen
- **时间**: 2026-10-22T21:19:01Z
- **提交信息**: deslop(cake_mla_varq_dcp_decode): fold the kernel and binding clones, drop dead preprocessor arms (#7022)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR is the round-2 deslop of two Cake MLA decode families for SM100
/ SM103, tracked in #6673. The families are `cake_mla_varq_dcp_decode`,
an MLA decode with variable-length queries and decode context
parallelism (DCP), and `nvfp4_mla_decode`, the NVFP4 MLA decode. Commit
1 folds the eight DCP main-kernel sources into four. Commit 2 keeps one
DCP host binding per query dtype. Commit 3 drops the dead fallback arms
and RTC scaffolds from the surviving kernel sources of both families.
Commit 4 drops two registry constants that nothing reads. The re-pointed
DCP records build from the kept files under per-source compile
definitions, and every former kernel symbol stays defined for its
program. The PR deletes 10 files: 4 kernel sources and 6 bindings. These
do not change: kernel symbols, device code, module names, routes,
argument plans, launch parameters, message texts, the public entry
points and the two test files.

Behaviour changes:
- **Host tracebacks.** The 6 re-pointed DCP programs now compile the
kept binding of their query dtype. When a host-side check fails, the
file name and line that the check macros record now point to the shared
file (its path and line numbers) instead of the deleted one. The error
kind, the message text and every check predicate are unchanged. Inside
the launch-failure message, the kernel symbol is spelled through
`CAKE_PROGRAM_KERNEL` and expands to the former literal.
- **One rebuild on an existing JIT workspace.** Module names stay the
same. Each of the 22 modules rebuilds once because its kernel source
text, its binding text or the shared DCP device header changed. The
per-commit counts below come from the files each commit changes and the
registries at that commit:
- commit 1 rebuilds 8 programs (16 modules): the 4 re-pointed main
programs, and the 4 kept main kernels whose source text gained the
definitions;
- commit 2 rebuilds 8 programs (16 modules): the 6 re-pointed programs
and the 2 kept bindings;
- commit 3 rebuilds all 11 programs (22 modules): every kernel source
and the shared header;
  - commit 4 rebuilds none.

  A fresh workspace is not affected.
- **Registry constants.** Commit 4 removes the module constants `ARCHES`
and `STAGES` from both registries. Nothing in the repository read them.
- **No device code changes.** For every kernel symbol, the gates compile
both sides to identical SASS from the loaders' exact compile
definitions. The entry points give bit-identical outputs over the tests'
shapes (see Validation).

## Changes

Validated over upstream main `f2f5add99`, then rebased onto main
`0179e5b31` with all four patches unchanged (range-diff) and no upstream
change to the two families or their tests in between. Head:
`64659892e2b73529c83f41533a6242efce5a8bdb` (4 commits). 23 files, +253 /
-15,372 (0 added, 10 deleted, 13 modified).

- **Families.** The PR touches two exporter-generated Cake families
under `flashinfer/experimental/`. Both serve only SM100 (B200, compute
capability 10.0) and SM103 (GB300, compute capability 10.3). Each is
JIT-compiled lazily per program and architecture through its own
registry (`cake_jit.py`) and `gen_jit_spec`.
- `cake_mla_varq_dcp_decode`
(`flashinfer/experimental/cake_mla_varq_dcp_decode/`, generated CUDA
under `csrc/cake_mla_varq_dcp_decode/`) is the MLA decode with
variable-length queries and DCP.
- Its registry has 9 `PROGRAMS` records: 8 main-kernel programs plus the
split-KV merge program. Each record is a kernel source plus a host
binding, built per architecture (18 JIT modules).
- `ROUTES` maps the 8 registered (query dtype, page size, item groups,
partition mode) combinations to the main programs: `bf16_p32_g4_pm1`,
`bf16_p64_g16_pm0`, `bf16_p64_g4_pm0`, `bf16_p64_g4_pm1`,
`fp8_p128_g4_pm1`, `fp8_p64_g16_pm0`, `fp8_p64_g4_pm0` and
`fp8_p64_g4_pm1`. For example, `bf16_p64_g4_pm1` means a BF16 query,
page size 64, 4 item groups and partition mode 1.
- `nvfp4_mla_decode` (`flashinfer/experimental/nvfp4_mla_decode/`,
generated CUDA under `csrc/cake_nvfp4_mla_decode/`) is the NVFP4 MLA
decode. It has 2 programs, `main` and `reduce`. Each is a kernel source
plus a host binding, built per architecture (4 JIT modules). Its
registry tables are unchanged apart from the two dropped constants
(commit 4).
- **Unchanged.**
- Every module name (record key + architecture) and every `ROUTES`
entry.
  - `MERGE_PROGRAM`, `ARG_PLANS` and every argument plan.
  - The `run` entry name and the route selection functions.
  - Every launch parameter, message text and accepted input.
- Every former kernel symbol, which stays defined for its program. The
kernel source and the binding spell it through `CAKE_PROGRAM_KERNEL`.
  - These files are byte-identical to the base:
- the public entry points (`flashinfer/mla/_core.py`,
`flashinfer/mla/__init__.py`, both packages' `__init__.py` and
`cake_backend.py`);
    - `flashinfer/jit/core.py`;
    - the two test files and both benchmarks;
    - the docs, `pyproject.toml` and the pre-commit configuration.
- **Sharing form.**
- The loaders already accept per-source compile flags through
`gen_jit_spec(extra_cuda_cflags_by_source=...)`
(`flashinfer/jit/core.py`, unchanged).
- A DCP registry record that shares another record's file now carries
its own values as compile definitions in a new optional list. The list
is `source_flags` for a kernel source (commit 1) and `binding_flags` for
a host binding (commit 2). `gen_program` passes the list to that source
only. Every source without such a list keeps its exact former command
line.
- Every kept shared file spells the differing tokens through compile
definitions. Their guarded defaults equal the file's own former tokens.
So the record that keeps the file builds with no per-source list and
with the former token stream.
- Fold arms are keyed on the compile definitions and never on
`__CUDA_ARCH__`, so the host pass sees the same text as the device pass.
- **Generated files.** The PR edits 12 kept generated files:
  - the 4 kept DCP main kernel sources and the DCP merge kernel source;
  - the DCP device header `cake_mla_varq_dcp_decode_device_common.cuh`;
  - the 2 kept DCP bindings;
  - the 2 NVFP4 kernel sources;
  - the two registries, in Python comment form.

The 2 kept DCP bindings, the DCP device header and the two registries
replace their exporter "do not edit" banner with this one-line
statement; the 7 kernel sources (the 4 kept DCP main kernels, the DCP
merge kernel and the 2 NVFP4 kernels), which carried no banner, gain it
as one inserted comment line after the licence block:
`Generated by Cake for FlashInfer. Exporter output, hand-edited here
pending exporter support.`

The untouched DCP merge binding, the DCP host header and the two NVFP4
bindings keep their exporter banners.
- **Packaging.** Packaging is unchanged. The generated CUDA of both
families ships through the existing package-data entries.

### Commit 1 (f21ac6b17) - cake_mla_varq_dcp_decode: fold the eight main
kernels into four sources (9 files, +156 / -11,575)

- **Pairs.** The eight generated main-kernel sources form four clone
pairs. Within each pair, the sources differ only in literal tokens:
- The two item-group variants, `bf16_p64_g16_pm0` and `fp8_p64_g16_pm0`,
differ from the 4-group partition-mode-0 sources in one token each (16
vs 4 scheduler lane groups).
- The FP8 page-128 variant differs from the FP8 page-64 4-group
partition-mode-1 source in 15 page-size tokens.
- The BF16 page-32 variant differs from the BF16 page-64 4-group
partition-mode-1 source in 47 tokens. These fall into four page-derived
classes: page size, pages per KV block, tokens per KV block and
shared-memory step.
- **Kept sources.** Each pair now shares its page-64 four-group source.
- The differing tokens go through `CAKE_ITEM_GROUPS`, `CAKE_PAGE_SIZE`,
`CAKE_KB_PAGES`, `CAKE_KB_TOKENS` and `CAKE_KB_SMEM_STEP`. Their
defaults equal the kept program's values.
- The kernel symbol goes through `CAKE_PROGRAM_KERNEL`, whose default is
the kept symbol.
  - The four other sources (11,501 lines) are deleted.
- **Registry and loader.** The four re-pointed registry records keep
their keys, bindings and module names, and carry their definitions in
`source_flags`. Through the loader's per-source flag lists,
`gen_program` passes those definitions to the kernel source only. The
registry gains the disclosure statement in Python form.
- **Consequence:** Device code is unchanged for every program. No test
changes.

### Commit 2 (3a57a3e59) - cake_mla_varq_dcp_decode: share one host
binding per query dtype (9 files, +87 / -3,381)

- **Clones.** Within a query dtype, the four main-kernel host bindings
(eight over both dtypes) are the same text apart from:
  - the kernel symbol;
  - the host-shim namespace id;
- for the BF16 page-32 program only, the three lines of the K tensor-map
box (32 vs 64 rows).
- **Kept bindings.** One binding is kept per dtype: the BF16 and FP8
page-64 4-group partition-mode-1 launchers. The kept file:
- spells its kernel symbol and its namespace through guarded compile
definitions (`CAKE_PROGRAM_KERNEL`, `CAKE_HOST_SHIM_NS`), whose defaults
are its own former tokens;
- spells the symbol inside the launch-failure message through a two-line
stringising helper (`CAKE_STR`);
- selects the page-32 box lines through verbatim preprocessor arms keyed
on `CAKE_PAGE_SIZE`.

The kept bindings grow by 25 lines (BF16) and 13 lines (FP8). The six
duplicate bindings (3,357 lines) are deleted.
- **Registry.** The records of the six other programs name the kept
binding. They carry their former symbol and namespace as per-source
compile definitions in `binding_flags`, and the loader composes the
definitions per source. The BF16 page-32 record also carries its page
size. The FP8 page-128 record carries no page size, because the FP8
binding spells no page-size text.
- **Disclosed:** In a re-pointed program, a failing host-side check now
records the shared binding's file and line (see Behaviour changes).
- **Consequence:** Module names, routes, argument plans and the exported
`run` entry are unchanged.

### Commit 3 (2c6a70fbf) - nvfp4_mla_decode, cake_mla_varq_dcp_decode:
drop dead preprocessor arms (8 files, +4 / -406)

- **Fallback arms.** Both loaders build the generated kernels only for
compute capability 10.0 and 10.3. Six of the seven surviving kernel
sources contain 62 `#if __CUDA_ARCH__ >= 1000` blocks, and the scalar
fallback arms of those blocks were never compiled to device code. The
host pass parsed them inside device function bodies and generated
nothing from them. The blocks are distributed as follows:
  - 6 in each DCP partition-mode-1 main kernel;
  - 4 in each DCP partition-mode-0 main kernel;
  - 1 in the DCP merge kernel;
  - 41 in the NVFP4 main kernel;
  - none in the NVFP4 reduce kernel.

At arm level, that is 195 lines. The guards and their fallback arms are
removed, and the SM100 bodies are no longer guarded.
- **RTC scaffolds.** There are six `__CUDACC_RTC__` typedef scaffolds:
two in each NVFP4 kernel source and two in the DCP device header. Each
is reduced to its nvcc arm, the only arm a `gen_jit_spec` build ever
took.
- **Disclosure.** Each hand-edited file carries the disclosure line. In
the device header, it replaces the "do not edit" banner.
- **Consequence:** No kernel symbol, module name, flag or Python table
changes.
- **Base count.** At the base, the same block form appeared 82 times
across ten kernel sources. The other 20 blocks were in the four sources
that commit 1 deletes.

### Commit 4 (64659892e) - nvfp4_mla_decode, cake_mla_varq_dcp_decode:
drop unread constants (3 files, +6 / -10)

- **Constants.** The module constants `ARCHES` and `STAGES` are deleted
from both registries. Nothing in the repository reads them. The records,
the compile flag tables and the loader name the two architectures and
the stage roles themselves.
- **Comments.**
- The registry header sentence that cited `ARCHES` now names the two
architecture keys directly.
- The NVFP4 registry carries the same one-line disclosure statement as
the other hand-edited Cake registries.
- The comment in the DCP `.clang-format` no longer claims a SHA-256
registry identity. The registry lists its sources by path, and the
record keys embed the exporter digest. The `DisableFormat: true` and
`SortIncludes: Never` settings are unchanged.
- **Consequence:** No kernel, binding, header, flag list, source list or
module name changes.

## Validation

The compile-only rows run on one CPU node with one CUDA toolkit for both
architectures. They are the device gate, the preprocessed-text gate and
the host gate. Each row's result gives the toolkit version. Every row
compares the base tree with the branch head. The GPU rows run on a B200
(SM100, compute capability 10.0, 148 SMs) and a GB300 (SM103, compute
capability 10.3, 152 SMs), with fresh JIT workspaces for both trees.

- Device gate, 30 rows (the 8 registered routes per architecture (16):
for the 4 re-pointed routes the former source at the base with its
former compile line against the kept source at head under the record's
compile definitions, for the 4 kept routes the kept source at the base
against head with its defaults; the 7 surviving kernel sources per
architecture (14): the 4 kept DCP main kernels, the DCP merge kernel and
the 2 NVFP4 kernels at the base against head; 8 of the kept-route rows
are the same compile as their surviving-source row and are reported
under both names, 22 distinct compiles per side; cubin + SASS +
preprocessed device text): all 30 rows identical (22 distinct compiles
per side; the 8 coincident kept-route pairs compiled once and reported
under both names; per unit 16 fold rows / 14 strip rows; per
architecture 15 / 15): identical SASS for every former kernel symbol,
exactly the expected kernel function, identical resource usage and
host-stub symbol sets, the preprocessed device text identical after
dropping line markers and blank lines and collapsing intra-line
whitespace (24 of 30 rows carry an indentation-only residue from the
preprocessor's re-alignment of the first token after a directive, the
other 6 none; no token differs on any row); nvcc Build
cuda_13.4.r13.4/compiler.38855100_0 (CUDA 13.4; no row needs CUDA 13.4)
- **Compilation.** Both sides are compiled from one staged path in one
environment.
  - **Pass criteria.** A row passes when all of these hold:
- the SASS is identical for the former kernel symbol, with no symbol
mapping;
    - each side has exactly the expected kernel function;
    - resource usage is identical;
- the device-pass preprocessed texts are identical after dropping line
markers and blank lines and collapsing intra-line whitespace (nvcc's
preprocessor re-aligns the first token after a directive, so the fold
and strip arms leave an indentation-only residue, which is tallied); any
token difference fails.
- Preprocessed-text gate, 30 rows (the same 30 source / architecture
pairs, both passes: the device pass of the compile above at head, and a
host pass with the architecture macro undefined; for the 16 route rows
the host pass is taken on the kept source as of commit 2, before commit
3's strip, with the head's include directories, because the strip's own
host-pass change is proven by the 14 host-pass strip rows): all 30 rows
identical in both passes: the device pass at head identical after line
markers, blank lines and intra-line whitespace (taken from the
device-gate compile of the same source); the host pass (architecture
macro undefined) identical for the fold rows, taken on the kept source
as of commit 2 before commit 3's strip with the head's include
directories, and identical after the declared edit set for the strip
rows at head
- **Pass criteria.** On both passes, the texts must be identical after
dropping line markers and blank lines and collapsing intra-line
whitespace. The fold arms are keyed on the compile definitions, so the
host pass must agree as well.
- Host-pass gate of the stripped sources, 14 rows (the 7 surviving
kernel sources per architecture at head against the base; host pass,
architecture macro undefined): all 14 rows identical: the host-pass
preprocessed text (architecture macro undefined, taken from nvcc's host
preprocessing step) of every surviving kernel source at head against the
base, after dropping line markers and blank lines and collapsing
intra-line whitespace, differs by exactly the declared edit set (the
removed fallback arms and the runtime-compilation scaffolds), both the
arm-level and the minimal line views exactly the declared counts; the
host-side symbol sets of the compiled objects identical
- **Pass criteria.** The host-pass texts must be identical after
dropping line markers and blank lines and collapsing intra-line
whitespace, except for exactly the declared removal. That removal is the
whole fallback arms and their directives:
    - 12 / 12 / 18 / 18 lines for the four DCP main kernels;
    - 3 lines for the merge kernel;
    - 132 lines for the NVFP4 main kernel;
    - 0 lines for the NVFP4 reduce kernel.

After preprocessing, the scaffold reduction and the banner line are
comments or identical typedefs. The host stub of the kernel symbol must
be present on both sides.
- Host gate, 16 rows (the 8 main-kernel bindings per architecture: the 6
re-pointed programs' former bindings at the base against the kept
binding at head under the record's compile definitions, the 2 kept
bindings at the base against head with their defaults; preprocessed host
text + compiled host object): all 16 rows identical: each former host
binding at the base against the kept binding of its query dtype at head
under the record's compile definitions, exact after line markers / blank
lines, the one adjacent-literal join at the kernel-name message site and
the check macros' file / line arguments with exactly the expected count
per binding (12 re-pointed rows, 4 kept-default rows); the compiled host
objects export the same symbol set and reference the same undefined
kernel symbol on both sides; no device code on either side
- **Preprocessed text.** The texts must be identical after the declared
normalisation, which covers:
- dropping line markers and blank lines, and collapsing intra-line
whitespace;
- masking the file / line arguments that the check macros expand at
every check site. There are exactly 119 sites per BF16 binding and 107
per FP8 binding, and every site must be present on both sides.
- joining the adjacent string literals of the one launch-failure
message. The joined message must equal the former literal with the
former kernel symbol.
  - **Host objects.** The compiled host objects must:
    - export identical defined-symbol sets;
    - reference exactly one undefined kernel symbol, the former one;
    - define the `run` entry inside the record's host-shim namespace;
    - contain no device code.
- Module build and load through the real loaders (per architecture: the
9 DCP programs and the 2 NVFP4 programs -- 11 modules, 22 over both
architectures; both trees, fresh JIT workspaces): 11 modules per tree
built and loaded through the real loaders on both devices with every
spec name, source list, shared flag list and per-source definition list
as expected and the run entry callable; device kernel set of every
module exactly its former kernel symbol and identical to the base-tree
module on both devices; export sets identical on both devices; every
module name unchanged
- Each module must be built by its loader with the expected name,
sources, shared flag list and per-source definition lists, and it must
load. The base has no per-source definition lists. On the branch,
exactly the re-pointed records have them.
- Each module's device kernel set must be exactly the former kernel
symbol.
- Every module's exported symbol set must be identical to that of the
base-tree module, and every module name must be unchanged.
- Registry tables re-read on both trees (import with CUDA hidden; every
table, route selection and loader spec of both families): both
registries imported on both trees with CUDA hidden and every table and
loader spec dumped: the head equals the base after exactly the declared
changes (4 kernel-source re-points with their definitions, 6 binding
re-points with theirs, the two unread constants gone from both
registries) and nothing else
- **Pass criteria.** The tables must be identical apart from the
declared deltas:
    - the 4 re-pointed kernel sources, with their `source_flags`;
- the 6 re-pointed bindings, with their `binding_flags` and the
per-source flag lists they produce;
    - the two removed constants.
- Bitwise before / after (torch.equal) on B200 and GB300, 12 cells per
device plus 2 informational ones; inputs rebuilt per tree with the
tests' own helpers and seeds: all 12 required cells bit-identical
(torch.equal over out and lse of every rank) on both devices: B200
(compute capability 10.0, 148 SMs) and GB300 (compute capability 10.3,
152 SMs); 60 / 60 output tensors compared per device, 0 differing; the
two informational no-merge cells 2 / 2 and 2 / 2 equal; the modules each
cell loaded (recorded through the loaders) equal the expected ones in
every cell on both trees; every re-pointed route, the merge program and
both NVFP4 programs were launched by at least one required cell on both
trees (coverage gate); the first GB300 torch.equal phase (step
`3696535311731b3a3f18e128`) reported `dcp_fp8_p64_g4_pm1` differed in
`rank3.lse` (2 elements, max_abs_diff nan) and was re-run with identical
inputs (step `bc4ecc8c16f6eb114bdd3c54`), which reproduced none of it:
with identical SASS for every kernel symbol this is run-to-run
nondeterminism of the base kernel's LSE output, not an effect of the
change
- **Program reached.** For each cell, the program reached is derived
from the registry's route table at head. The loader's recorded module
loads during the run confirm it.
  - **DCP cells (9).**
- The rank-merge test's inputs for BF16 and FP8 (page 64, 4 item groups,
partition mode 1; world 4, all four ranks launched) reach
`bf16_p64_g4_pm1` / `fp8_p64_g4_pm1`, which are the two kept sources and
kept bindings.
- The split-items test's inputs for BF16 and FP8 (batch 64, partition
mode 0, merge kernel launched) reach `bf16_p64_g4_pm0` /
`fp8_p64_g4_pm0` plus the merge program.
- The page-size test's inputs reach `bf16_p32_g4_pm1` (world 8) and
`fp8_p128_g4_pm1` (world 4).
- Two added cells use 129 requests of 4,096 tokens, 128 heads and world
1. They reach `bf16_p64_g16_pm0` / `fp8_p64_g16_pm0` plus the merge
program. These are the two item-group-16 routes, which no test item
launches.
- The public-entry test's inputs, run through
`flashinfer.mla.cake_mla_varq_dcp_decode` (96 heads, world 2), reach
`bf16_p64_g4_pm1`.
  - **NVFP4 cells (3).**
- The NVFP4 public entry `prepare_nvfp4_batch_decode_with_kv_cache_mla`,
over the public-API test's inputs, reaches `main`. It also reaches the
reduce program if and only if the plan splits. Whether it splits is
reported both as expected and as measured.
- The backend entry, over the forced-two-splits inputs and over the
balanced 16k / 12k inputs, reaches `main` + `reduce`.
- **Coverage.** At least one required cell reaches each of the 6
re-pointed routes and each of the 7 surviving kernel sources. The
outputs and the log-sum-exp are compared bitwise.
- **Informational cells (2).** These are the two item-group-16
geometries with 1,024 tokens per request. They launch no merge kernel.
- **Split count.** A cell's split count depends on the SM count, so it
is read at run time.
- Tests on B200 and GB300 (both the base and this branch, fresh JIT
workspaces) and with CUDA hidden: on B200 and on GB300, on both trees:
the DCP file 22 passed / 3 skipped (GB300 22 passed / 3 skipped) of 25
items and the NVFP4 file 51 passed / 1 skipped (GB300 51 passed / 1
skipped) of 52; the skipped ids are the unregistered page-size routes,
the unsupported-device rejection on a supported device and (when the
CuTe DSL is absent) the CuTe-DSL comparison, identical on both trees;
with CUDA hidden on both trees and both nodes the host-only items pass
(7 passed / 18 skipped and 44 passed / 8 skipped); passed / skipped /
failed counts and ids identical between the trees, 0 failed anywhere;
the JIT modules each run built equal the expected routes of the executed
device tests on both trees
  - **The two files:**
- `tests/experimental/test_cake_nvfp4_mla_decode.py`: 52 items, of which
8 need a GPU;
- `tests/experimental/test_cake_mla_varq_dcp_decode.py`: 25 items, of
which 18 need a GPU.
- **Both trees.** The passed / skipped / failed counts and the skipped
ids must be identical on both trees.
  - **Expected skips on a supported GPU:**
- the two page-size items whose route is not registered (`bf16_p128`,
`fp8_p32`);
    - the unsupported-compute-capability test of each file;
    - the CuTe-DSL comparison, when that package is absent.
- **JIT modules.** The JIT modules that the runs build must equal the
routes of the executed device tests. Both the expected and the measured
sets are reported.
- **CUDA hidden.** Both files run on both trees. The expected passed /
skipped counts are 44 / 8 for the NVFP4 file and 7 / 18 for the DCP
file.
- CPU checks: all passed on a CPU node: pre-commit --all-files on both
full checkouts (16 hooks, 15 passed / 0 failed / 1 skipped, identical
per hook, empty patches) and on the 13 modified files (12 passed, 0
failed); ruff and the repository's format check on both registries; the
registries re-read and all 22 loader specs built with CUDA hidden; every
edited generated file carries exactly one disclosure statement and no
'do not edit'; no deleted file name referenced anywhere; the four edits
re-applied to a snapshot of the base reproduce every commit tree and the
branch byte for byte (23 paths), with every unit's text proofs equal to
their recorded results and the proofs re-run at the head; the gate
inventory regenerated from the tree equals the staged one; collection
identical on both trees; the host-only items pass with CUDA hidden on
both trees; commit message checks
- pre-commit runs on both full checkouts. It must give identical
per-hook results and an empty patch. The clang-format hook covers the
DCP generated CUDA. pre-commit also runs on the 13 modified files.
  - The registries are re-read. The expected results are:
- 9 DCP programs and 8 routes, with the 4 + 6 re-pointed records
carrying their definitions;
    - 2 NVFP4 programs;
    - the two constants gone.
- Every edited generated file must carry exactly one disclosure
statement and its guarded defaults, and must not contain "do not edit".
  - No deleted file name may be referenced anywhere.
- Re-applying the four edits to a snapshot of the base must reproduce
every commit's tree byte for byte. Each unit's text proofs must equal
their recorded results. These proofs are preprocess-level renders of
every fold and every binding against the former sources, with negative
controls.
  - Test collection must be identical on both trees.
  - Commit message checks.
- Type check: the repository's mypy hook passed on this branch and on
the base, with identical findings
- The repository's mypy hook runs over the package on this branch and on
the base. Both runs must give identical findings.

**Not run.** By design, this PR's validation does not run the following.
Each item gives its proof of record.
- **Benchmarks.** No benchmark of either family runs. This is a
mechanical PR with identical SASS per kernel symbol and bit-identical
outputs, so there is nothing new to measure.
- **H100 / SM90.** Neither family serves SM90: both loaders map only
compute capability 10.0 and 10.3. Nothing in this PR executes there.
- **The two item-group-16 routes** (`bf16_p64_g16_pm0`,
`fp8_p64_g16_pm0`). No test item covers them. Their proof of record is:
  - their gate rows (device / preprocessed-text / host);
  - the module build + export check on both GPUs;
  - the two added torch.equal cells above.

## Not in this PR

- **The `#if __CUDA_ARCH__ == 1000` shared-memory address fork.** After
this PR, 5 sites of 6 lines each remain: one in each of the 4 kept DCP
main kernels and one in the NVFP4 main kernel. The base had 9; the other
4 were in the sources that commit 1 deletes. The fork is not
SASS-neutral on SM103, so removing it is a performance / exporter
question.
- **The `dbg` kernel argument.** It is present in every DCP main kernel
signature and never read. Removing it touches the kernel ABI, the host
plumbing, the argument plan and a test pin, so it belongs in a separate
PR after an owner ruling.
- **Page-size coverage.** Validation accepts 10 of the 18 dtype /
page-size / item-group / partition-mode combinations without registering
them. Registering them through the fold's definitions would change
behaviour, and so would shrinking the accepted page sizes.
- **Host path.** This covers four items, which are behaviour / exporter
changes:
  - encoding the tensor maps once per prepared plan;
  - the per-call `cudaSetDevice` in the DCP bindings;
- the NVFP4 thread-local device block (#6672, together with the
`cudaSetDevice` item above);
  - the NVFP4 argument pre-export;
  - the range-check volume.
- **Python-surface relocation** (`flashinfer/mla/_core.py` wrappers vs
the lazy export table of `flashinfer/mla/__init__.py`). This is an owner
decision, and many open PRs edit `_core.py`. Neither file is touched
here.
- **Shared host helpers.** `CakeFastDivmod` is re-declared in the DCP
bindings, and `CakeSetMaxDynamicSmem` is inlined in the NVFP4 binding.
Each package also has its own `_header_dirs` and architecture flag
copies. Sharing them would mean shared-file / exporter edits.
- **The NVFP4 `V_HALVES` pair-row layout.** It is ABI, with three pinned
tests.
- **The `TRACKING_ISSUE` strings.** They are message text.
- **The informational `#define` tables of the generated kernels.** They
are layout metadata emitted by the exporter, which would re-emit them
over a hand edit. They are left in place.
- **Dtype templating and partition-mode merging.** The BF16 and FP8
kernels differ by about 430 lines (partition mode 0) and about 450 to
520 lines (partition mode 1), and the two schedulers differ by about
2,600 lines. Both would change device code.
- **CI enrollment of `tests/experimental`, benchmark changes and new GPU
tests for the two item-group-16 routes.** These are coverage additions.
- **Exporter requests.** These are requests, not PR changes, and the
issue comment addresses them to the exporter owners:
- emit one kernel source and one binding per (dtype, partition mode),
and carry the route knobs (page size, item groups, kernel symbol,
host-shim namespace) as per-record `source_flags` / `binding_flags`, the
shape already merged for the TRT-LLM-style MLA loader;
- emit the SM100 helper bodies unconditionally when every registered
architecture is SM100 or newer, and emit no RTC scaffold for nvcc-only
loaders;
- emit per-architecture shared-memory address code only for the
architectures in the record;
- make the `dbg` slot an export option that is off for production
exports;
  - put the two host helpers in one host header per family;
- drop the zero-use `#define` tables, and point `TRACKING_ISSUE` at the
live issue;
- encode tensor maps once per prepared plan, and pre-export arguments on
the host;
- share `_header_dirs` and the architecture flags from `flashinfer/jit`;
  - drop the disclosure line on regeneration.

```experimental-tests
tests/experimental/test_cake_nvfp4_mla_decode.py
tests/experimental/test_cake_mla_varq_dcp_decode.py
```

Part of #6673

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Compatibility**
* Updated experimental MLA decode paths to support configurable cache
page sizes and consistent execution across supported GPU architectures.
* **Improvements**
* Streamlined how generated decode variants are built and selected,
while preserving their existing default behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4bfe096](https://github.com/flashinfer-ai/flashinfer/commit/4bfe0963180dc8aa0776e5dc867562df978af7f6)

- **作者**: eigen
- **时间**: 2026-10-22T21:18:17Z
- **提交信息**: perf(cake_kimi_k3_attn_res): depth-2 K = 4 snapshot-write (SM100/SM103) and held nc3 K = 5 (SM103) programs (#7014)

This PR changes routes of the Cake Kimi-K3 AttnRes operator,
`flashinfer.experimental.cake_kimi_k3_attn_res`. It is exposed as
`flashinfer.kimi_k3_attn_res.prepare_kimi_k3_attn_res` and
`kimi_k3_attn_res`. The operator runs residual add, an optional snapshot
write, K+1 candidate scoring, softmax, mix and output RMSNorm in one
launch. It takes BF16 inputs with hidden size 7168 and K in [0, 8]. It
writes BF16 output with FP32 accumulation. It has dense and
snapshot-write forms, and PDL (programmatic dependent launch) is a
launch parameter.

The snapshot-write cell M 4096, K 4 (block 4 written) used to run the
depth-3 held-release write program. It now runs a new depth-2 write
program with the early consumed release and a bf16 prefix add. This
applies on SM100 at 148 SMs (B200) and on SM103 at 148 SMs (B300) and
152 SMs (GB300). The new program is built once for SM100 and once for
SM103. On SM103, five K = 5 dense cells now route to the held-release
nc3 depth-3 K = 5 program, which takes three sources per chunk. These
cells are M 6144 and M 8192 at 148 SMs, and M 3072, M 4096 and M 8192 at
152 SMs. That program already shipped for SM100's own K = 5 cells. This
PR adds its SM103 build, which is the third new program. The previous
programs of these cells still ship, because other cells still reach
them. No program leaves either architecture's set. Every other program
is unchanged, with identical SASS. Every other route on all three GPUs
is unchanged. The baseline is the previous Cake version of this
operator, merged in PR #6984. For the shapes below, that version runs
the same programs as the version before it (PR #6980), and those
programs are the "previous" arm measured here. Times are CUPTI kernel
times with cold L2, from paired interleaved ABBA sampling with ≥ 3
groups × ≥ 300 samples per arm, the same protocol as the tables in PR
#6980.

NVIDIA GB300 (sm_103a, 152 SMs), driver 580.159.03, CUDA 13.4.92, torch
2.14.1+cu130.

| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 3072, K 5 (dense) | 66.064 | 65.824 | 1.0030 | 66.016 | 65.856 |
1.0028 |
| M 4096, K 5 (dense) | 85.248 | 83.920 | 1.0160 | 85.216 | 83.968 |
1.0152 |
| M 8192, K 5 (dense) | 160.928 | 158.464 | 1.0156 | 160.928 | 158.464 |
1.0155 |
| M 4096, K 4 (snapshot write, block 4) | 83.760 | 82.560 | 1.0143 |
83.776 | 82.560 | 1.0154 |

NVIDIA B300 SXM6 (sm_103a, 148 SMs), driver 580.126.09, CUDA 13.4.92,
torch 2.14.1+cu130.

| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 6144, K 5 (dense) | 126.177 | 124.994 | 1.0095 | 126.242 | 125.058 |
1.0089 |
| M 8192, K 5 (dense) | 165.826 | 164.290 | 1.0092 | 165.730 | 164.226 |
1.0092 |
| M 4096, K 4 (snapshot write, block 4) | 87.553 | 85.506 | 1.0234 |
87.649 | 85.473 | 1.0255 |

NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4.92, torch
2.14.1+cu130.

| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 4096, K 4 (snapshot write, block 4) | 86.176 | 84.927 | 1.0149 |
86.112 | 84.832 | 1.0152 |

The tables list only the shapes whose program changed. The shape list
has 291 shapes per GPU. The other 287 shapes on GB300, 288 on B300 and
290 on B200 run the same programs as the previous version, so their
timings are the ones listed in PR #6980.

Cake ships no other data types or layouts for this operator, since the
dense and snapshot-write forms are the whole family, and 138 programs
(167 libraries: 80 sm_100a, 87 sm_103a) cover B200 (sm_100a, 148 SMs),
B300 (sm_103a, 148 SMs) and GB300 (sm_103a, 152 SMs).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added experimental attention-kernel support for newer GPU
architectures and additional attention configurations.
* Added more targeted execution paths for snapshot-write operations
across supported configurations.

* **Bug Fixes**
* Improved route selection so certain snapshot-write operations use
their registered execution path rather than a fallback.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [513c4ae](https://github.com/flashinfer-ai/flashinfer/commit/513c4ae68a5a779c44bd3dc2525157e3bc4ca3b6)

- **作者**: eigen
- **时间**: 2026-10-22T21:18:00Z
- **提交信息**: perf(cake_rubin_mla_nvfp4_decode): faster NVFP4 MLA paged decode for Rubin (sm_107a) (#7004)

`flashinfer/experimental/cake_rubin_mla_nvfp4_decode` is the Rubin
(SM107, `sm_107a`) variant of the Cake NVFP4 MLA paged decode. Cake is
NVIDIA's kernel generator. On compute capability 10.7,
`flashinfer.mla.cake_mla_nvfp4_paged_decode` routes to this package. It
decodes BF16 queries against the paged NVFP4 MLA KV cache (352 B per
token) and writes BF16 output. This PR makes the decode and the split-KV
merge launch under programmatic dependent launch when the plan splits
the KV. The query quantizer and the decode now signal their dependents
as soon as their work is done, so the three launches of one decode call
overlap their prologues. The public API, cache layout and numerics are
unchanged, and outputs match the previous version bit for bit, except at
the largest-batch split-KV rows where the previous version is itself not
run-to-run deterministic (its merge sums the split partials in a
nondeterministic order). The baseline is the previous version of this
package, which FlashInfer `main` ships (merged in #6931). It was
measured in the same process on the same board, interleaved with this
PR. Across the 16 configurations the geometric-mean speedup is 1.012 (Q4
rows 1.011, Q8 rows 1.013), and 12 of 16 configurations are faster. The
batch-1 rows gain 1.018–1.047, including the two largest gains. The four
rows at or below 1.000 (0.997–0.999) have little for the overlap to
hide: three are one-wave unsplit rows where no merge runs, and the
fourth's quantizer and merge are a small fraction of its decode. All
four are within the paired-measurement noise.

| Configuration | Previous (µs) | This PR (µs) | Speedup (previous /
this PR) |
|---|---:|---:|---:|
| H96-Q4-B1-KV64K | 25.0 | 24.6 | 1.018 |
| H96-Q4-B4-KV64K | 53.2 | 52.3 | 1.016 |
| H96-Q4-B16-KV64K | 185.4 | 185.5 | 0.999 |
| H96-Q4-B64-KV64K | 672.2 | 668.4 | 1.005 |
| H96-Q4-B1-KV128K | 37.2 | 36.5 | 1.019 |
| H96-Q4-B4-KV128K | 90.6 | 90.1 | 1.004 |
| H96-Q4-B16-KV128K | 348.5 | 341.6 | 1.020 |
| H96-Q4-B64-KV128K | 1304.9 | 1299.2 | 1.004 |
| H96-Q8-B1-KV64K | 31.8 | 30.7 | 1.035 |
| H96-Q8-B4-KV64K | 81.9 | 80.6 | 1.016 |
| H96-Q8-B16-KV64K | 284.5 | 285.0 | 0.998 |
| H96-Q8-B64-KV64K | 1155.8 | 1158.7 | 0.997 |
| H96-Q8-B1-KV128K | 49.8 | 47.5 | 1.047 |
| H96-Q8-B4-KV128K | 150.1 | 149.0 | 1.007 |
| H96-Q8-B16-KV128K | 558.7 | 559.2 | 0.999 |
| H96-Q8-B64-KV128K | 2200.8 | 2198.8 | 1.001 |

*NVIDIA R200 (pre-release board, reported as "NVIDIA Graphics Device",
compute capability 10.7 / `sm_107a`, 208 SMs, 120 MiB L2), driver
615.71.09, CUDA 13.4 (runtime 13.4.92), PyTorch 2.14.1+cu130. H = 96
heads, page size 64; configurations are named H96-Q{query
length}-B{batch}-KV{keys per sequence}. Each latency is one decode call
in µs (quantizer + decode + merge), taken as the mean over two sessions
of the median of 15 replays of a 20-launch CUDA graph. Both versions
were interleaved in ABBA groups in one process, and each version used
its own cold-L2 KV copies. Speedup = previous / this PR; above 1 means
this PR is faster.*

The existing `cake_mla_nvfp4_paged_decode` package ships this Cake
decode on `sm_100a` and `sm_103a`, and the Rubin package ships it on
`sm_107a`, including the decode-context-parallel form.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Decode and merge operations now use programmatic dependent launch when
the execution plan supports it, while other plans continue to launch
normally.
* Launch behavior is available in runner metadata and through the
programmatic interface.
* **Bug Fixes**
* Improved synchronization between dependent GPU operations and
data-processing stages.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4020ab7](https://github.com/flashinfer-ai/flashinfer/commit/4020ab7c06d23cc857cc23acb24f5102cc6012d8)

- **作者**: eigen
- **时间**: 2026-10-22T21:17:29Z
- **提交信息**: deslop(cake_lm_head_loss): share launch shims, fold clone kernel sources, drop dead host code (#7007)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR is the round-2 deslop of the Cake chunked LM-head + fused loss
package for SM100 / SM103 (`flashinfer/experimental/cake_lm_head_loss`),
tracked in #6671. Commit 1 keeps one launch shim per launch shape.
Commits 2-5 fold clone kernel sources onto kept sources under compile
definitions:
- the four logits GEMM forms into one unit per architecture;
- the five dW variants into two sources;
- the six dX GEMM units into two sources;
- the fp32 scale cast into the bf16 source.

Commit 6 folds the SM103 logits unit into the SM100 one, so one logits
unit serves both architectures. Commits 7 and 8 delete host code that no
input can reach: the pinned-geometry record selection and the cluster
occupancy probe. Every former kernel symbol stays defined for its
library. In total, 24 files are deleted: 15 kernel translation units and
9 launch shims. These do not change: library and spec names, launch
parameters, exports, accepted inputs, the public entry points
`chunked_lm_head_loss` / `chunked_lm_head_logprob` and the API test
file.

Behaviour changes:
- **Module-level API of the package only.** The public entry points keep
their signatures and behaviour. Inside the package:
- `cake_jit.select_module(arch)` takes the architecture only. Before, it
returned the architecture's sole record for every input, because both
records pin neither hidden size nor vocabulary.
`cake_backend.record_for(device)` loses its `hidden` / `vocab` keywords,
`Geometry` loses its two pinned fields, and `PRIMARY_RECORD` /
`record_geometry` are gone (commit 7).
- `cake_backend.cluster_resident` raises `ValueError` for a cluster
wider than two CTAs, instead of answering through an NVRTC-compiled
occupancy probe. No registered program launches such a cluster.
`grid_dims` loses its `resident` parameter (commit 8).
- **Host tracebacks.** The 12 libraries whose launch stub now includes a
sibling's launch shim record the shared shim's file name and line
numbers, not the deleted shim's, in the check macros' traceback when a
host-side argument check fails. The error kind, the message text and the
check predicate are unchanged.
- **One rebuild on an existing JIT workspace.** 34 of the 46 libraries
rebuild once: every library whose kernel source, launch stub, included
launch shim or compile definitions changed. The 12 libraries of the six
untouched row kernels (`gather_rows_bf16`, `row_finalize`,
`loss_reduce`, `row_grad`, `slab_sum`, `scale_cast_scatter_bf16`, per
architecture) do not rebuild. Library and spec names are unchanged, so a
fresh workspace sees no difference.
- **No device code changes.** For every kernel symbol, the gates compile
both sides to identical SASS from the loader's exact compile
definitions. The backend's entry points give bit-identical outputs over
the cells listed under Validation.

## Changes

Base: upstream main `9f988bf98` (2026-10-22). Head:
`018205138e9423d1e5e11dd9a1c1e12500d81c0b` (8 commits). 53 files, +1,174
/ -13,794 (0 added, 24 deleted, 29 modified).

- **Package.** `flashinfer/experimental/cake_lm_head_loss` is one
exporter-generated Cake package for SM100 (B200, compute capability
10.0) and SM103 (GB300, compute capability 10.3). It holds the chunked
LM-head GEMM, the fused loss / log-probability row kernels and their
backward GEMMs. The public entry points `chunked_lm_head_loss` /
`chunked_lm_head_logprob` live in `flashinfer/chunked_lm_head.py`, which
is untouched. The package's own loader `cake_build.py` JIT-compiles each
stage lazily per architecture from the package manifest `build.json`.
The loader is byte-identical to the base and shared across the Cake
packages.
- **Libraries.** There are 46 libraries, 23 per architecture, one per
registered stage:
    - `gather_rows_bf16`;
- the four logits GEMM forms `gemm_logits`, `gemm_logits_mcnt`,
`gemm_logits_nostats` and `gemm_logits_nostats_mcnt`;
    - `row_finalize`, `loss_reduce` and `row_grad`;
- the six dX GEMM forms `gemm_dx`, `gemm_dx_s`, `gemm_dx_tn256`,
`gemm_dx_s_tn256`, `gemm_dx_st3` and `gemm_dx_s_st3`;
    - `slab_sum`;
- the five dW forms `gemm_dw_acc`, `gemm_dw_acc_gn`,
`gemm_dw_cast_bf16`, `gemm_dw_cast_f32` and `gemm_dw_cast_f32_gn`;
    - `scale_cast_bf16`, `scale_cast_f32` and `scale_cast_scatter_bf16`.
- **Sources.** Every library compiles two sources: a kernel translation
unit (`..._kernel.cu`) and a launch stub (`..._launch.cu`). The launch
stub defines the kernel symbol and includes a shared launch shim
(`csrc/cake_lm_head_loss/shim/cake_lm_head_loss_shim_<digest>.cuh`). The
shim holds the tvm-ffi `run` entry with its argument checks, the
descriptor encoders, the dynamic shared memory and the launch geometry.
- **Counts.** At the base there were 27 kernel translation units, 27
launch stubs and 20 launch shims. 19 of the kernel units were
architecture-neutral and compiled for both architectures. The four
logits forms shipped one unit per architecture, which made 8 units. At
head there are 12 kernel translation units, 27 launch stubs and 11
launch shims.
- **Registry and backend.** The registry `cake_jit.py` has two records,
one per architecture, and its generated block is byte-identical to the
base. The backend `cake_backend.py` does host-side planning, binding and
dispatch. Both are hand-written Python. The manifest check script
`scripts/check_cake_build_manifests.py` (unchanged) verifies the
manifest against the sources and the registry.
- **Unchanged.**
- Every library name, spec name (the manifest's closure digests are
unchanged), registry record, stage row, launch parameter, export (`run`,
`build_cuda_version`) and accepted input.
  - Every former kernel symbol, which stays defined for its library.
- These are byte-identical to the base: the public entry points,
`cake_build.py`, `flashinfer/jit`, the API test file, the shared test
helpers, `scripts/`, `pyproject.toml` and the pre-commit configuration.
- **Sharing form.** All sharing uses one spelling:
- The unchanged loader already passes each `build.json` entry's
per-library `nvcc_flags` to nvcc for both sources of the entry.
- A library whose kernel source was a deleted sibling's clone now
compiles the kept source. Its `build.json` entry carries the compile
definitions: the former kernel symbol through `CAKE_PROGRAM_KERNEL`, and
one key per folded form.
- A launch stub whose launch shim was a deleted sibling's clone defines
the differing values as compile definitions before it includes the kept
shim. These values are the operand element types with their DLPack codes
and bit widths, the dynamic shared-memory literal, the C-descriptor form
and the preferred-cluster launch form.
- Every kept shared file spells the differing tokens through compile
definitions. Their guarded defaults equal the file's own former tokens,
so the library that keeps the file builds with no definition and with
the former token stream.
- Fold arms are keyed on compile definitions: the deleted member's text
comes first and the kept text otherwise. They are never keyed on
`__CUDA_ARCH__` alone, so the host pass sees the same text as the device
pass.
- **Generated files.** The PR edits 23 kept generated files: the 5 kept
launch shims, the 12 re-pointed launch stubs and the 6 kept kernel
translation units. Each one replaces its exporter "do not edit" banner
with this one-line statement:
`Generated by Cake for FlashInfer. Exporter output, hand-edited here
pending exporter support.`

The untouched generated files (15 launch stubs, 6 launch shims and 6
kernel translation units) keep their banners. One sentence of the
registry's hand-written preamble comment is amended. It now says that a
library's `build.json` entry lists the kernel translation unit that
defines the stage's symbol: either the unit's own file, or a sibling
form's file with this unit's kernel symbol named through a compile
definition. The registry's generated block is byte-identical and keeps
its own banner, so the registry carries no disclosure statement.

  Three sentences of `README.md` (hand-written) are amended:
- The launch shims are "one per launch shape, the stub's compile
definitions selecting the operand types, the C descriptor form, dynamic
shared memory and cluster form within it" (commit 1).
- The kernel translation units are "one per kernel family shared by the
records of both architectures, the sibling forms of a family selected by
compile definitions". The four logits GEMM forms share "one unit across
both architectures", and their sm_103a lowering sits "in a
definition-keyed arm of it" (commits 2 and 6).
- The grid-rule sentence no longer describes the deleted occupancy
probe: "every registered GEMM instance launches a grid over its whole
work-item domain (no grid rule reads a co-resident cluster count), and
the dX K-slice rule uses the device's co-resident two-CTA clusters
(`cluster_resident`: the SM pair count)" (commit 8).
- **Packaging.** `pyproject.toml` is byte-identical to the base. This PR
changes nothing about packaging.

### Commit 1 (3e6523e24) - cake_lm_head_loss: share one launch shim per
launch shape (28 files, +303 / -2,889)

- **Shims.** Nine of the twenty launch shims differed from a sibling
only in these values:
- an operand element type, with the matching DLPack type code and bits:
the workspace pointer (`int` vs `float`), or the C or output operand
(`__nv_bfloat16` vs `float`);
  - the dynamic shared-memory literal;
  - C being a TMA descriptor instead of a pointer;
  - the preferred-cluster launch form.
- **Kept.** One shim per launch shape is kept, so eleven files remain.
The kept shims name those values through compile definitions guarded by
`#ifndef` defaults that equal the kept shim's own tokens:
  - `CAKE_WS_CTYPE` / `CAKE_WS_DLCODE`;
  - `CAKE_C_CTYPE` / `CAKE_C_DLCODE` / `CAKE_C_DLBITS`;
  - `CAKE_OUT_CTYPE` / `CAKE_OUT_DLCODE` / `CAKE_OUT_DLBITS`;
- `CAKE_SHIM_SMEM`, with a two-line `CAKE_CAT` helper for the unsigned
literal;
- two arm keys, `CAKE_C_TMA` and `CAKE_PREFERRED_CLUSTER`, whose arms
carry the former text verbatim.

  The nine other shims (2,806 lines) are deleted.
- **Stubs.** The twelve launch stubs of the deleted shims define their
kernel's values before including the kept shim, using 22 definition
lines across the 12 stubs. Their header comment names the kept shim.
`build.json` carries the new digests of those stubs and nothing else.
The README's layout sentence now says there is one launch shim per
launch shape.
- **Disclosed:** When a host-side check fails in one of those 12
libraries, the traceback records the shared shim's file and lines (see
Behaviour changes).
- **Consequence:** Every library keeps its name, kernel symbol, launch
facts and exports. No kernel source changes.

### Commit 2 (d8e82bcfc) - cake_lm_head_loss: fold the logits GEMM forms
into one unit per arch (12 files, +178 / -4,349)

- **Forms.** Each architecture had four logits GEMM translation units:
`gemm_logits`, `gemm_logits_mcnt`, `gemm_logits_nostats` and
`gemm_logits_nostats_mcnt`. They differed only in:
  - the workspace pointer type and the row count read from it;
  - the row-statistics block;
  - the store bounds.
- **Kept unit.** One translation unit per architecture is kept: the
`gemm_logits` text. It carries the sibling forms as arms keyed on
`CAKE_LOGITS_MCNT`, `CAKE_LOGITS_NOSTATS` and
`CAKE_LOGITS_NOSTATS_MCNT`, whose guarded defaults are 0. The SM100 unit
has six elementary blocks and the SM103 unit has five.
- Each arm holds a sibling's former lines verbatim, with the kept text
in `#else`.
  - The lines that the nostats forms drop are guarded on their keys.
- The unit names its kernel symbol through `CAKE_PROGRAM_KERNEL`, whose
guarded default is the kept symbol.

  Six translation units are deleted.
- **Manifest.** The six sibling libraries compile the kept unit under
their key and symbol definitions.
- **Registry, test and README.** The registry test now uses one shared
helper to read the symbol that a library's kernel source defines: a
literal, a guarded default, or a symbol carried by the library's compile
definitions. The registry module's preamble sentence names the
shared-unit case. The README's layout sentence names the folded forms.

### Commit 3 (9af790d7a) - cake_lm_head_loss: fold the dW kernel
variants into two sources (6 files, +172 / -2,317)

- **Folds.** The five weight-gradient kernel translation units are
folded into two:
- the blocked-raster accumulate (`gemm_dw_acc_gn`) becomes a
`CAKE_DW_GN` arm of the plain accumulate (`gemm_dw_acc`);
- the two FP32 fused-cast forms (`gemm_dw_cast_f32`,
`gemm_dw_cast_f32_gn`) become `CAKE_DW_F32` / `CAKE_DW_F32_GN` arms of
the BF16 fused cast (`gemm_dw_cast_bf16`).
- **Form.** There is one key per directive. Where two members share a
region's text, the second arm repeats it verbatim. The kernel symbol is
named through `CAKE_PROGRAM_KERNEL`. Without definitions, each kept
source is its former text.
- **Manifest.** Three translation units are deleted. The six member
libraries name the kept source in `build.json` and carry their
definitions.

### Commit 4 (b2f70abe9) - cake_lm_head_loss: fold the six dX GEMM units
into two sources (7 files, +275 / -3,073)

- **Variants.** There are four dX GEMM variants: the K-sliced
`gemm_dx_s`, the 3-stage ring `gemm_dx_st3`, `gemm_dx_s_st3` (both), and
the narrow-tile K-sliced `gemm_dx_s_tn256`. They differed from their
kept counterparts (`gemm_dx` wide, `gemm_dx_tn256` narrow) only in:
- for the sliced form, the workspace operand's type and the slab store;
- for the 3-stage form, the stage count with its shared-memory offsets
and barrier set.
- **Kept sources.** The two kept sources carry those lines as arms keyed
on two independent knobs, `CAKE_DX_SLICED` and `CAKE_DX_ST3`. The wide
source has 27 arm blocks and the narrow source has 10. The sliced
3-stage library sets both knobs. The kept sources name their kernel
through `CAKE_PROGRAM_KERNEL`.
- **Manifest.** Four translation units are deleted. Their eight
`build.json` entries point at the kept source and carry the definitions.
- **Kept apart.** The wide and narrow dX bodies stay separate, because
their differences are dense.

### Commit 5 (592cde798) - cake_lm_head_loss: fold the fp32 scale-cast
kernel into the bf16 source (3 files, +44 / -120)

- **Pair.** The two scale-cast row kernels (`scale_cast_bf16`,
`scale_cast_f32`) differed in seven of their 109 lines: the output
parameter type on the kernel signature and the six-line output store.
- **Kept source.** The bf16 source is kept. It has two
`CAKE_SCALE_CAST_F32` arms, with the fp32 text first and the bf16 text
in `#else`, and names its symbol through `CAKE_PROGRAM_KERNEL`. One
translation unit is deleted.
- **Manifest.** The two `scale_cast_f32` libraries point at the kept
source and carry the two definitions.

### Commit 6 (3af1f9c86) - cake_lm_head_loss: fold the sm_103a logits
unit into the sm_100a one (4 files, +216 / -814)

- **Pair.** After commit 2, one logits translation unit remained per
architecture. The two texts differ only in:
- the epilogue: the SM103 lowering stages the C tile in shared memory
for a TMA store behind a six-stage operand pipeline, while the SM100
lowering stores from registers behind seven stages;
- the pipeline-depth constants and the mbarrier table that follows from
them.
- **Kept unit.** The SM100 unit is kept. It carries the SM103 lowering
as arms keyed on `CAKE_LOGITS_SM103`, whose guarded default is 0. There
are 31 elementary blocks, with the former SM103 lines first and the
SM100 lines in `#else`. Regions that only one architecture has are
guarded on the key. The per-form arms of commit 2 stay where they are.
As a result, each of the eight former logits programs is the shared unit
compiled under its library's definitions.
- **Manifest and README.** One translation unit is deleted. The four
SM103 logits libraries compile the shared unit with the architecture key
added to their definitions. The README's layout sentence says where the
SM103 lowering now lives.
- **Droppable.** This commit can be dropped independently. The device
gate's stop rule applies to this commit alone.

### Commit 7 (185d25df0) - cake_lm_head_loss: drop the pinned-geometry
record selection (4 files, +39 / -161)

- **Dead selection.** Neither registry record pins a hidden size or a
vocabulary, because the kernels take the call geometry as launch
scalars. So `select_module(arch, H, V)` always returned the
architecture's sole record, and the two `validate` checks against a
pinned geometry could not raise.
- **Changed.** `select_module(arch)` now returns that record directly.
It fails loudly if a second record (which cannot exist) were present.
These are removed, together with their call sites in the backend, the
benchmark and the tests:
  - `PRIMARY_RECORD` and `record_geometry`;
  - the `Geometry.hidden` / `.vocab` fields;
- the `hidden` / `vocab` parameters of `record_for` and
`generated_program_available`.
- **Tests.** The geometry-selection test becomes a
one-record-per-architecture test. The validate-rejection test drops its
`pinned_geometry` row (24 -> 23 rows), because the check that row
exercised can no longer raise.
- **Unchanged.** The record keys, `MODULES`, `STAGES` and the generated
registry block.

### Commit 8 (018205138) - cake_lm_head_loss: drop the cluster occupancy
probe and dead grid input (3 files, +18 / -142)

- **Probe.** The backend carried an NVRTC-compiled empty kernel. Its
`cuOccupancyMaxActiveClusters` answer sized persistent grids of clusters
wider than two CTAs, and the backend passed that answer into the grid
evaluator under the name "resident".
- **Unreachable.** Both registered records launch every GEMM in one- or
two-CTA clusters. For those, `cluster_resident` returns the SM pair
count arithmetically. No registry grid rule names "resident" or "sms".
So no build and no input could reach the probe, the wider-cluster
branch, the `resident` parameter of `grid_dims` or the bind loop's
per-stage computation.
- **Deleted.**
  - the probe (73 lines);
- the wider-cluster branch: `cluster_resident` now raises `ValueError`
for a cluster wider than two CTAs, and the error names the supported
widths. The two-CTA arithmetic stays, and so do its callers in the
workspace-size rule and the plan builder;
- the `resident` parameter of `grid_dims` and the bind loop's
computation.
- **Tests and README.** The probe's device test is removed. The
grid-rule tests lose their `resident` inputs, and one expected tuple is
recomputed. The cluster-width rule keeps its raise asserts. The README's
grid-rule sentence no longer describes the probe.

## Host-code deletions

Commits 7 and 8 carry out steps that the issue owner proposed: items 2
and 4 of the proposed steps in #6671.
- **Scope.** They are module-level API changes of the package
(`cake_jit.select_module`, `cake_backend.record_for`, `Geometry`,
`cluster_resident`, `grid_dims`), not public API changes.
`chunked_lm_head_loss` and `chunked_lm_head_logprob` keep their
signatures and behaviour. The removed code is dead for every input the
public entry points can produce.
- **Droppable.** Each is its own commit and can be dropped
independently.
- **Alternative for commit 8.** Instead of raising for a cluster wider
than two CTAs, `cluster_resident` could return the unconditional
SM-count arithmetic (`max(1, sms // cluster_ctas)`) for every width.
This PR chooses the fail-closed `ValueError`, because no registered
program launches such a cluster and the test file pins the raise.

## Validation

The compile-only rows (device gate, preprocessed-text gate, host gate
and inertness gate) run on one node with one CUDA toolkit for both
architectures. Each row's result gives the toolkit version. The GPU rows
run on a B200 (SM100, compute capability 10.0, 148 SMs) and a GB300
(SM103, compute capability 10.3, 152 SMs).

- Device gate, 42 rows (every folded kernel of commits 2-6 per
architecture: the logits forms (8 + 8 for the cross-architecture fold),
dW (10), dX (12), scale-cast (4); cubin + SASS + preprocessed device
text): all 42 rows identical (per unit: F1 4 / 4, F2 4 / 4, F3 4 / 4, F4
6 / 6, F5 4 / 4, F6 4 / 4, F7 8 / 8, X 8 / 8; sm_100a 21 / 21, sm_103a
21 / 21): identical SASS for every former kernel symbol with no symbol
mapping, identical resource usage, exactly the expected kernel function
per side, and the device-pass preprocessed texts identical after line
markers and blank lines on 4 rows and, on the other 38 rows (the GEMM
kernels, declared per row), additionally after the indentation of the
kernel-signature continuation lines, which the preprocessor emits at
their source column; no inner-whitespace or token difference on any row
(class tally {'none': 0, 'line_markers': 0, 'line_markers+blank_lines':
4, 'line_markers+blank_lines+indentation': 38,
'line_markers+blank_lines+whitespace': 0, 'unresolved': 0}); nvcc Build
cuda_13.4.r13.4/compiler.38855100_0 (CUDA 13.4; no row needs CUDA 13.4)
  - **Rows.** Each row compares two sides:
- the former program's source at the base, compiled with its former
compile line;
- the kept source at head, compiled with the library's exact compile
definitions.
- **Compilation.** Both sides are compiled from one staged path in one
environment.
  - **Pass criteria.** A row passes when all of these hold:
- the SASS is identical for the former kernel symbol, with no symbol
mapping;
    - resource usage is identical;
    - each side has exactly the expected kernel function;
- the preprocessed device texts are identical after dropping line
markers and blank lines and, on the GEMM rows only, the indentation of
the kernel-signature continuation lines. No other class is allowed on
any row.
- Preprocessed-text gate, 42 rows (the host pass of every device-gate
row's kernel source): all 42 kernel-source host-pass rows identical
after line markers and blank lines on 4 rows and, on the other 38 rows
(the GEMM kernels, declared per row), additionally after the indentation
of the kernel-signature continuation lines, which the preprocessor emits
at their source column; no inner-whitespace or token difference on any
row (one per device row; the former source at the base against the kept
source at head under the library's compile definitions, both sides in
one environment; class tally {'none': 0, 'line_markers': 0,
'line_markers+blank_lines': 4, 'line_markers+blank_lines+indentation':
38, 'line_markers+blank_lines+whitespace': 0, 'unresolved': 0})
- Each row compares the former source at the base with the kept source
at head under the library's compile definitions.
- The preprocessed host text of the folded translation units is
identical to the base's up to line markers, blank lines and the
indentation of the kernel-signature continuation lines (the preprocessor
keeps source columns), with SASS identical on all 42 rows.
- Host gate, 34 rows (the 17 libraries per architecture whose launch
stub or included launch shim changed: the stub's preprocessed host text
and compiled host object, base against head): all 34 launch-stub rows
identical: the preprocessed host text of every stub whose text or
included launcher changed, base against head, after line markers, blank
lines and the check macros' file / line arguments with the derived
check-site count equal on both sides (34 of 34; class tally
{'line_markers': 34, 'backtrace_args': 34, 'blank_lines': 20}); host
objects export exactly `run` and `build_cuda_version` on both sides (34
of 34 identical after the declared weak-inline class, 34 raw-identical,
0 weak-inline symbols tallied), reference the same undefined kernel
symbol and carry no device code
- **Text.** The preprocessed host texts must be identical after dropping
line markers, blank lines and the check macros' file / line arguments.
The shared shim's path and lines replace the deleted shim's. The derived
check-site count must be equal on both sides.
- **Host objects.** The host objects must export exactly `run` and
`build_cuda_version`, reference the same undefined kernel symbol and
carry no device code.
- Inertness gate, 26 rows over the 23 libraries that gained compile
definitions (11 on SM100 and 12 on SM103; three SM103 logits libraries
carry two rows each, one per folding commit): each library's launch stub
preprocessed under the base flag list and under the head flag list: all
26 rows identical: the stub of every library that gained compile
definitions, preprocessed under the base flag list and under the head
flag list, identical after line markers and blank lines (26 of 26
byte-identical raw), with identical exports and the same undefined
kernel symbol under both
- The stub and its shim read none of the fold keys and do not read
`CAKE_PROGRAM_KERNEL`. The host text must therefore be identical after
line markers and blank lines, and the exports must be unchanged.
- Library build and load through the real loader (per architecture: the
23 libraries of that architecture; both trees, fresh JIT workspaces): 23
libraries per tree built and loaded through the real loader on both
devices with every entry (`run`, `build_cuda_version`) callable and
every spec name unchanged; kernel sets identical to the base-tree
library's 23 / 23 on both devices; export sets identical on both devices
(on B200 no weak-inline symbol was needed (23 of 23 export sets
raw-identical); on GB300 no weak-inline symbol was needed (23 of 23
export sets raw-identical)); the registry's resolved tables identical on
both trees
- Each library must be built by its loader with the expected compile
definitions, and it must load.
- Each library's device kernel set must be exactly the former kernel
symbol.
- The exported symbol set and the spec name of every library must be
identical to the base-tree library's.
  - The registry's resolved tables must be identical on both trees.
- Bitwise before / after (torch.equal) on B200 and GB300: 33 cells per
device over the backend's loss and log-probability entry points and the
package-internal fp32 forward / backward pair (row counts 1 to 8193,
chunk sizes 1000 to 4096, the compaction / fused-cast / dX-finalize /
dW-stream / hidden-count switches and explicit GEMM tuning pins), inputs
rebuilt per tree with the test file's own helpers and seed: all 33 cells
bit-identical (torch.equal) on both devices: NVIDIA B200 (compute
capability 10.0, 148 SMs) and NVIDIA GB300 (compute capability 10.3, 152
SMs); 130 / 130 output tensors (loss, log-probabilities, dX, dW)
compared per device, 0 differing. The libraries each cell launched were
measured through the backend's binding step with its cache disabled and
are identical on both trees in 33 of 33 cells on both devices; every
fold-member library of the architecture was reached by at least one cell
(11 of 11 on B200, 12 of 12 on GB300); the derived expectation matched
the measurement in 6 / 6 cells (informational).
- **Outputs.** The loss, log-probabilities, dX and dW are compared bit
for bit.
- **Libraries reached.** The libraries that each cell launches are
recorded through the backend's binding step. They must be identical on
both trees. Every folded library of the architecture must be reached by
at least one cell.
- Tests on B200 and GB300 (both the base and this branch, fresh JIT
workspaces) and with CUDA hidden: on B200 and on GB300, on both trees:
the main file's device selection 22 passed / 0 skipped / 0 failed on
this branch and 22 / 0 / 0 at the base (the deleted probe test
deselected on both trees; identical outcome per node id otherwise) and
the API file's device test 1 / 0 / 0; with CUDA hidden, on both trees
and both nodes: the main file 148 passed / 24 skipped on this branch
(149 / 25 at the base) and the API file 9 passed / 1 skipped on both,
the ids identical between the trees up to the three node ids this PR
deletes (the probe test, the geometry-selection test and the
pinned-geometry row of the validate test) and the one it adds (0 failed
anywhere)
  - **The two files:**
- `tests/experimental/test_cake_lm_head_loss.py`: 82 tests at the base
and 81 at head, which collect 174 and 172 items. The probe test is
removed, the geometry-selection test becomes a
one-record-per-architecture test, and the pinned-geometry row of the
validate test is dropped. The device selection collects 23 items at the
base and 22 at head. The deleted probe test is deselected on both trees.
- `tests/experimental/test_cake_lm_head_loss_api.py`: 10 tests, one of
them on the device. This file is byte-identical to the base.
- **Both trees.** No test may fail anywhere. The passed / skipped ids
must be identical on both trees, except for the three node ids this PR
deletes and the one it adds. With CUDA hidden, the passed count and the
skipped count of the main file therefore each differ by one between the
trees.
- CPU checks: all passed on a CPU node: pre-commit --all-files on both
full checkouts (16 hooks, 15 passed / 0 failed / 1 skipped, identical
per hook, empty patches) and on the 29 modified files (11 passed, 5
skipped, 0 failed); the repository's build-manifest check (in-tree mode)
exit 0; ruff E9 / F clean; the registry and the loader re-read as
expected (23 libraries per architecture, every spec with the expected
name, flag list and sources); text hooks (one disclosure statement per
edited generated file, no 'do not edit', the guarded defaults, no
deleted file name referenced); the eight edits replayed onto a snapshot
of the base reproduce the branch byte for byte with every unit tool
equal to its recorded result (129 records); test collection on both
trees differs by exactly the three node ids this PR deletes (the probe
test, the geometry-selection test and the pinned-geometry row of the
validate test) and the one it adds; with CUDA hidden both files pass on
both trees (148 + 9 passed, 24 + 1 skipped, 0 failed); commit messages
equal to the recorded ones
- pre-commit runs on both full checkouts, where it must give identical
per-hook results and an empty patch. It also runs on the 29 modified
files.
- The repository's build-manifest check script
`scripts/check_cake_build_manifests.py` runs in its in-tree mode. The
manifest entries, source digests and registry rows must be consistent,
and the script must exit 0.
- The registry and the loader are re-read. The expected result is two
records and 23 stages, with 23 libraries per architecture that have the
expected names, compile definitions and sources.
- Every edited generated file must carry exactly one disclosure
statement and its guarded defaults, and must not contain "do not edit".
Every folded kernel source must carry exactly one `CAKE_PROGRAM_KERNEL`
default.
  - No deleted file name may be referenced anywhere.
- Re-applying the eight edits to a snapshot of the base must reproduce
the branch byte for byte. Each unit's text proofs must equal their
recorded results. These proofs are preprocess-level renders of every
shim and every fold against the former sources, with negative controls.
- Test collection on the two trees must differ by exactly the three node
ids this PR deletes and the one it adds. The deleted ids are the probe
test, the geometry-selection test and the pinned-geometry row of the
validate test.
  - Commit message checks.
- Type check: the hook passed with 0 errors on this branch and on the
base (0 errors), with identical findings
- The repository's mypy hook runs over the package on this branch and on
the base. Both runs must give identical findings.

**Not run.** By design, this PR's validation does not run the following.
Each item gives its proof of record.
- **Benchmarks.** This is a mechanical PR with identical SASS per kernel
symbol and bit-identical outputs, so there is nothing new to measure. No
benchmark runs.
- **H100 / SM90.** The package registers programs for SM100 and SM103
only. It has two registry records, and the loader's architecture table
names sm_100a and sm_103a. Nothing in this PR executes on SM90.
- **The CUDA 13.0 toolkit variant of the SM103 entries.** Their manifest
entries carry two extra compile options that apply only when the toolkit
is exactly 13.0. The gates ran on a single newer toolkit, where those
options do not apply on either side. This PR does not touch the options.

Experimental test scope for CI:

```experimental-tests
tests/experimental/test_cake_lm_head_loss.py
tests/experimental/test_cake_lm_head_loss_api.py
```

## Not in this PR

- **The fp32 dW drop** (the three `scale_cast_f32` / `gemm_dw_cast_f32`
/ `gemm_dw_cast_f32_gn` programs, about 2,200 lines with their registry
rows, tests and docs). These programs can be reached through the
package-internal explicit forward / backward pair, and the owner marked
the drop as a product decision. In this PR the three programs stay as
fold members (commits 3 and 5), and every symbol and library is kept.
- **The registry collapse** (one record for both architectures). The two
records differ in six places. The registry literal must stay readable by
the unchanged manifest check script, the registry test and the exporter.
- **`epi_store='tma'` acceptance.** The switch parses, but no program is
registered for it. Accepting it would change the outcome of two explicit
pins through the public switch, so the switch grammar is an owner
decision.
- **Live behaviour and performance items.** These are live behaviour or
performance decisions:
  - the reference engine's placement;
- the host-side valid-row synchronisation path and the hidden-count
readback;
  - the blocked-raster dW route and its group rule;
  - the SM103 wide-dX efficiency threshold.
- **dX 6 -> 1 and the 12-shim GEMM launcher family.** The wide and
narrow dX bodies differ densely, so two dX sources and two launcher
families stay.
- **Launch-stub sharing** (27 -> 20 or -> 1). The savings are mostly
licence text. In exchange, every translation unit would carry a
definition, and two test pins would change.
- **Per-source compile flags in the shared loader.** By exporter
contract, `cake_build.py` is byte-identical across the Cake packages,
and this PR never edits it.
- **Templating re-derivation of the GEMM bodies and exporter changes**
(a shared launcher header, a shared `CakeSetMaxDynamicSmem` header,
per-source flags). This is exporter work, addressed to the exporter
owners in the issue comment.
- **CI enrollment of the two test files in a standing shard, and a
standalone SASS-baseline step in CI.** The gate rows run on our own
compute, not in CI.
- **The exporter-contract items, and the module functions that the tests
call directly** (the hidden-size branch of the dX tile rule, the dW
block group rule). These are kept as they are.
- **The issue's "about 1,430 test lines mirror constants".** This is a
classification, not a mechanical unit. The only tests deleted are those
of commits 7 and 8: the probe test, the geometry-selection test
(replaced by the one-record-per-architecture test) and the
pinned-geometry row of the validate test.
- **Exporter requests**, which are requests rather than PR changes. They
are addressed to the exporter owners in the issue comment:
- emit one launch shim per launch shape, parameterised by the compile
definitions above, with the per-library values in the launch stub;
- emit the sibling forms of a kernel family and the per-architecture
lowering as one source with definition-keyed arms (never `__CUDA_ARCH__`
alone), with the symbol through `CAKE_PROGRAM_KERNEL` and the
definitions carried in the manifest entry;
- stop emitting the pinned `hidden` / `vocab` geometry fields, and emit
the architecture-only `select_module` form;
  - drop the disclosure line on regeneration.

Part of #6671

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded Cake LM-head loss GPU support with shared kernel
implementations across architectures, additional output formats, and
configurable launch modes, including four-CTA clusters on supported
paths.
* **Bug Fixes**
* Program availability is now selected by GPU architecture, with input
dimensions validated at runtime.
* Launch grids now cover the full work-item domain; workspace sizing
guidance reflects paths that require the hidden dimension.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [83c54bd](https://github.com/flashinfer-ai/flashinfer/commit/83c54bdbd168567c6ab8ae6ea7a8c9e4faa7eabf)

- **作者**: eigen
- **时间**: 2026-10-22T21:17:02Z
- **提交信息**: deslop(cake_device_helpers): resolve three families' helpers from the repository headers and drop three dead ones (#7017)

## Summary

This PR is round 2 of the Cake device-helper cleanup tracked in #6672.
It covers three exporter-generated experimental Cake families for SM100
/ SM103: the Kimi-K3 FP8 projection GEMM, the NVFP4 paged MLA decode and
the MiniMax-H3 varlen attention. Each of these families now takes every
device helper from the repository helper directory,
`csrc/cake_device_helpers/`. The 50 package copies that are
token-identical to a repository header are deleted: 24 from kimi and 26
from MLA decode. The three helpers that had no repository twin move into
`csrc/cake_device_helpers/` with their names and bytes unchanged. This
PR also deletes three headers of that directory that no translation unit
includes. No include line changes. Loaders, registries, module names,
compile definitions, launch parameters, bindings, kernel sources, tests,
benchmarks and docs do not change. The only text edit is one sentence of
the kimi package's `csrc/README.md`.

Behaviour changes:
- **No device code changes.** The gates compile the base tree and this
branch for every (program, architecture) module of the three families.
Both sides use one staged path, one environment, and the loader's exact
flag list and include order. The result is identical SASS, identical
resource usage and an identical preprocessed token stream. The only
difference the compiler sees is the path of the header it opened (see
Validation).
- **One rebuild on an existing JIT workspace** (as #6947 disclosed). The
163 kimi modules, the 14 MLA decode modules and the 21 MiniMax varlen
modules rebuild once. They rebuild because the header dependency records
that ninja kept for them name the deleted or moved package copies.
Module names are unchanged, so a fresh workspace sees no difference.
Nothing rebuilds for the three dead headers, because no build ever
opened them.
- **Package data.** The wheel loses 53 files: the three dead headers and
the 50 deleted copies. It ships the three moved helpers from
`csrc/cake_device_helpers/`. `pyproject.toml` is unchanged.
- **Diagnostic paths.** If a compiler diagnostic were raised inside a
helper, it would now print the path of the repository header, not the
package copy. No helper emits a diagnostic at the base.

## Changes

Base: upstream main `f2f5add99` (2026-10-22). Head:
`62e1b65c6f3bffbc2a94aa4eaa32d80eb3fdf8f1` (4 commits). With rename
detection, which is what GitHub shows: 57 files, +3 / -1,557 (53
deleted, 3 renamed byte for byte, 1 modified). Without rename detection:
60 files, +102 / -1,656 (56 deleted, 3 added, 1 modified).

- **Families.** Three exporter-generated experimental Cake families for
SM100 (B200, compute capability 10.0) and SM103 (GB300, compute
capability 10.3). Each family's own loader (the package's `cake_jit.py`)
JIT-compiles it lazily per selected program and architecture.
- `flashinfer/experimental/kimi_k3_fp8_projection/` is the Kimi-K3 FP8
projection GEMM. It has 107 records and 163 (program, architecture)
modules: 81 on SM100 and 82 on SM103. `KERNELS` maps 83 keys onto the
SM100 records and 84 onto the SM103 records.
- `flashinfer/experimental/cake_mla_nvfp4_paged_decode/` is the NVFP4
paged MLA decode. It has 7 programs x 2 architectures = 14 modules. The
four attention programs carry `min_cuda_version` 13.4, so the loader
refuses them with an older toolkit. The other three programs build on
any CUDA 13 toolkit.
- `flashinfer/experimental/minimax_h3_varlen_attention/` is the
MiniMax-H3 varlen attention. It has 21 (program, target) modules: 11 on
SM100 and 10 on SM103.
- **Resolution.**
- Each package's device preamble,
`csrc/cake_<family>/cake_<family>_device_common.cuh`, includes every
device helper as `#include "cake_device_helpers/<name>.cuh"`. There are
24 such includes for kimi, 27 for MLA decode and 32 for MiniMax varlen.
- The loaders build the include directories in a fixed order: the
package's `csrc/` first, then the kernel-source directories, then the
repository `csrc/` and `include/`. The MiniMax loader lists its kernel
directory twice, so the repository `csrc/` is its fourth entry and its
third distinct directory.
- At the base, the quoted include resolved to the package copy. After
this PR the package copies are gone, and the same include line resolves
to the repository header of the same name.
- **Token identity.** Every deleted copy is token-identical to its
repository twin. The pairs differ only in licence text, indentation,
line wrapping and comment text, and one MLA pair is byte-identical. The
compiler therefore reads the same token stream from another path. No
helper or kernel uses `__FILE__` or `__LINE__`.
- **Repository helper directory.** `csrc/cake_device_helpers/` has 82
files both before and after this PR. Commit 1 deletes 3 dead headers,
and commits 3 and 4 move 3 helpers in with their names and bytes
unchanged.
- **Unchanged.**
- Byte-identical to the base: every loader, registry, binding, kernel
source, device preamble and test file.
- Unchanged: module / spec names, closure digests, compile definitions,
launch parameters, benchmarks and docs.
- The only text edit replaces one sentence (2 lines removed, 3 added) of
the kimi package's hand-maintained `csrc/README.md`.
- **Generated files.** No generated file is edited. Every commit deletes
or moves whole files, so no file gains a disclosure statement. The kimi
`csrc/README.md` keeps its existing hand-fold disclosure sentences.
- **Packaging.** `pyproject.toml` is unchanged. The repository `csrc/**`
ships as package data (`flashinfer.data`), and the kimi and MLA decode
packages ship their own `csrc/**`. The MiniMax package's own `csrc/`
tree has no package-data entry. As a result, the wheel loses the three
dead headers and the 50 deleted copies, and it ships the three moved
helpers under `csrc/cake_device_helpers/`.

### Commit 1 (2789a2d9c) - cake_device_helpers: drop three headers
nothing includes (3 files, +0 / -102)

- **Deleted.** This commit deletes three device-helper headers of
`csrc/cake_device_helpers/` that no translation unit includes:
  - `cake_ex2_emulation_f32x2` (25 lines);
- `cake_mma_ts_step` (38 lines), the f8f6f4 variant. The tf32 variant,
`cake_mma_ts_step_92cbf134668203d3.cuh`, is included by a DeepGEMM
family and stays;
  - `cake_softmax_frag_exp2_cast` (39 lines).
- **History.** The last file to include them was the Blackwell MSA
device preamble. When that preamble was regenerated, the includes were
dropped and the functions were inlined into the kernel sources, but the
shared headers were left in place.
- **Readers.** No include line, loader, build manifest, test or document
names these headers. No loader lists the directory's contents. The
deletion therefore changes no compile line.
- **Proof rows.**
- A repository-wide search for the three file stems and name digests
finds nothing on this commit.
- The GDN decode and batch DeepGEMM FP8 families are the two whose
preambles include other helpers from this directory. One Cake GDN decode
program and one Cake batch DeepGEMM FP8 module are built through their
loaders on the base and on this branch.
- The two builds must give the same compile digest, the same embedded
cubin and the same SASS. Their preprocessed kernel texts must list the
same helpers and must not name any of the three.
- The results are in the build-digest row and the two companion gate
rows in Validation.

### Commit 2 (f5bc6fa1e) - cake_kimi_k3_fp8_projection: resolve helpers
from the repository headers (25 files, +3 / -708)

- **Deleted.** This commit deletes the 24 device-helper headers vendored
under the package's own `csrc/cake_device_helpers/` (706 lines). Each
one duplicates the repository header of the same name. Each pair is
token-identical; only licence text, indentation and line wrapping
differ.
- **Resolution.** No include line changes. The loader lists the package
`csrc/` first and the repository `csrc/` after the package directories,
so the same quoted include now resolves to the repository header.
- **README.** The package's `csrc/README.md` now says where the
preamble's helpers come from (2 lines removed, 3 added).
- Old sentence: "`cake_device_helpers/` holds the compiler helper
headers (`cake_<helper>_<16-hex>.cuh`) that the device preamble
includes."
- New sentence: "The device preamble's compiler helper headers
(`cake_<helper>_<16-hex>.cuh`) come from the repository's top-level
`csrc/cake_device_helpers/` directory, which the loader puts on the
include path after the package's own `csrc/`."

  Nothing else in the file changes.
- **Unchanged:** the registry, the 163 module names, closure digests,
compile definitions, launch parameters, bindings, tests and benchmarks.
- **Consequence:** an existing JIT workspace rebuilds the family's 163
modules once, because of its header dependency records. A fresh
workspace is not affected.

### Commit 3 (ef1bec6f2) - cake_mla_nvfp4_paged_decode: resolve helpers
from the repository headers (27 files with rename detection, +0 / -747;
28 files, +31 / -778 without)

- **Deleted.** This commit deletes the 26 device-helper headers vendored
under the package's own `csrc/cake_device_helpers/` (747 lines), which
duplicate the repository headers of the same name. Each pair is
token-identical; only indentation, line wrapping and comment text
differ, and one pair is byte-identical.
- **Moved.** The one helper without a repository copy,
`cake_tcgen05_commit_cg2_multicast` (31 lines), moves into
`csrc/cake_device_helpers/` with its name and bytes unchanged. The
repository directory now holds every helper this package includes, and
the package helper directory is removed.
- **Resolution.** No include line changes. The include-order argument is
the same as in commit 2.
- **Unchanged:** the registry, the 14 module names, flags, bindings,
tests and docs.
- **Consequence:** an existing JIT workspace rebuilds the 14 modules
once.

### Commit 4 (62e1b65c6) - cake_minimax_h3_varlen_attention: move two
device helpers to csrc/ (2 files with rename detection, +0 / -0; 4
files, +68 / -68 without)

- **Moved.** Two device-helper headers of the MiniMax-H3 varlen
attention package have no counterpart in the repository helper
directory: `cake_make_sf_cp_desc_lo_sbo256` (27 lines) and
`cake_mma_ts_step_cg2` (41 lines). They move from the package's own
`csrc/cake_device_helpers/` into `csrc/cake_device_helpers/` with their
names and bytes unchanged. The package helper directory is removed.
- **Resolution.**
- The package's other 30 helper includes already resolved to the
repository directory at the base.
- The loader's include directories list the package `csrc/` first and
the repository `csrc/` as the third distinct entry.
- The two quoted includes therefore resolve in the third distinct
include directory instead of the first, and the compiler reads the same
bytes from another path.
- **Unchanged:** the registry, the 21 module names, closure digests,
compile definitions, launch parameters, tests and docs.
- **Consequence:** an existing JIT workspace rebuilds the 21 modules
once.

Together with commits 2 and 3, `csrc/cake_device_helpers/` now holds
every helper that the three families of this PR include.

## Validation

The compile-only rows (device gate and preprocessed-text gate) run on
one CPU node with one CUDA toolkit for both architectures. Each row's
result gives the toolkit version. The four MLA decode attention programs
need CUDA 13.4 or newer, so the gate toolkit is at least 13.4. The GPU
rows run on a B200 (SM100, compute capability 10.0, 148 SMs) and a GB300
(SM103, compute capability 10.3, 152 SMs). The CPU checks run on a CPU
node.

- Device gate, 200 rows (every (program, architecture) module of the
three families: 163 kimi (81 SM100 + 82 SM103), 14 MLA decode (7 + 7),
21 MiniMax varlen (11 + 10), plus the two companion rows of commit 1
(one GDN decode program and one batch DeepGEMM FP8 module, SM100); cubin
+ SASS + resource usage): all 200 rows passed with CUDA 13.4 (nvcc build
cuda_13.4.r13.4/compiler.38855100_0): for every row the SASS of every
kernel symbol, the resource usage and the cubin digest are identical
between the base tree and this branch, and both sides contain exactly
the record's kernel functions (163 kimi, 14 MLA decode, 21 MiniMax
varlen and the 2 companion rows; 101 SM100 + 99 SM103 rows).
- **Rows.** Each row compiles the kernel translation unit of one module
from the base tree and from this branch. Each side uses the repository
`csrc/` of its own tree.
- **Compilation.** Both sides are compiled at one staged path in one
environment, with the loader's exact flag list and include-directory
order.
  - **Pass criteria.** A row passes when all of these hold:
- the SASS is identical for every kernel symbol of the row, with no
symbol mapping;
    - resource usage is identical;
    - the cubin digest is equal;
    - each side has exactly the record's kernel functions.
- Preprocessed-text gate, 200 rows (the device pass and the host pass of
every device-gate row): all 200 rows passed (401 passes: the device pass
and the host pass of every row, plus the kept-host pass of the GDN
companion row): every pass is token-identical after dropping line
markers and inter-token whitespace (0 differing tokens); after dropping
line markers alone the texts differ in 196 lines (kimi) and 191 lines
(MLA) of whitespace-only re-wrapping, in 4 lines (MiniMax: blank-line
padding the preprocessor emits around the two moved helpers' include
from the new directory; the helpers' bytes are unchanged) and in 0 lines
for the two companion rows; the set of helper headers each pass opened
is identical on both trees and equals the preamble's include list, and
on this branch every opened helper lives under
csrc/cake_device_helpers/.
  - **Pass criteria.** A row passes when all of these hold:
- the token stream of each pass is identical after dropping line markers
and inter-token whitespace (0 differing tokens);
- the set of helper headers that the preprocessor opened is identical on
both sides and equal to the preamble's include list;
- on this branch, every helper that was opened is under
`csrc/cake_device_helpers/`.
  - **Expected line-wise differences.**
- Kimi and MLA decode rows: whitespace only, because the repository
headers are re-wrapped twins of the deleted copies.
- MiniMax varlen rows: whitespace only as well (blank-line padding that
the preprocessor emits around the two moved helpers' include from the
new directory). The helpers keep their bytes, and the other 30 helpers
already resolved to the repository headers at the base.
    - The two commit-1 rows: identical as written.
- Build digest, 2 rows on B200 through the real loaders (the GDN decode
program and the batch DeepGEMM FP8 module of commit 1; both trees, fresh
JIT workspaces): both rows passed on a B200 (the GPU route's CUDA 13.3
toolkit): for the GDN decode program the compile digest, the cubin and
the SASS are identical on both trees with exactly the record's kernel
and identical compile options, and the program is callable; for the
batch DeepGEMM FP8 module the spec name, the kernel set, the exported
symbols, both embedded cubins (the kernel translation unit's and the
binding translation unit's; raw bytes and normalised SASS alike), the
21-header dependency closure and the compile command ninja recorded are
identical on both trees (each tree's own include directories aside) and
equal to the gate row's flag list, and the module's entry point is
callable.
- **GDN decode program.** The compile digest, cubin and SASS must be
identical.
- **Batch DeepGEMM FP8 module.** The spec name, kernel set, exported
symbols and embedded cubin must be identical.
- **Both rows.** The compile command that ninja recorded must be
identical on both trees and equal to the gate row's flag list.
- Module build and load through the real loaders (kimi: every KERNELS
key of the node's architecture, 83 on SM100 / 84 on SM103; MLA decode:
the 7 programs of the architecture; MiniMax varlen: 11 on SM100 / 10 on
SM103; both trees, fresh JIT workspaces): on both GPUs every program the
route's CUDA 13.3 toolkit accepts was built through the real loaders on
both trees in fresh JIT workspaces and compared module by module, 97
modules per GPU (B200: kimi 83, MLA decode 3, MiniMax varlen 11; GB300:
kimi 84, MLA decode 3, MiniMax varlen 10), with 0 build or load failures
and every module's entry points callable: the JIT spec names of all 101
programs per GPU are unchanged; for every compared module the kernel
symbol set, the exported symbol set, the helper closure of the build
dependency records and the compile flags ninja recorded (each tree's own
include directories aside) are identical on both trees and equal to the
gate row's flag list; on this branch every helper opened lives under
csrc/cake_device_helpers/; the four MLA attention programs that need
CUDA 13.4 are refused by the loader on both trees alike under the 13.3
toolkit (their device code is proved by the gate rows compiled with CUDA
13.4)
- Each module must be built by its loader with its spec name unchanged,
and it must load with its entry points callable.
- Its kernel symbol set and exported symbol set must be identical to
those of the base-tree module.
- On this branch, the header dependency records must name only the
repository headers.
- If the toolkit on the GPU nodes is older than CUDA 13.4, the loader
refuses the four MLA decode attention programs on both trees alike. In
that case the result names the refused programs. Their device code is
covered by the device-gate rows, which are compiled with the newer
toolkit.
- Tests on B200 and GB300 (both the base and this branch, fresh JIT
workspaces) and with CUDA hidden: on both GPUs the three files pass with
identical counts on the base tree and this branch, 0 failures: kimi 83
passed (B200 and GB300), MLA decode 7 passed / 27 skipped (both GPU
routes run a CUDA 13.3 toolkit, so the 27 items gated on CUDA 13.4 skip
identically on both trees; those four programs' device code is proved by
the device-gate rows compiled with CUDA 13.4), MiniMax varlen 653
passed; with CUDA hidden on the GPU nodes and on a CPU node 26 passed /
57 skipped, 7 passed / 27 skipped and 579 passed / 74 skipped on both
trees with identical skipped ids; test collection identical on both
trees (83 / 34 / 653 ids, 0 differing).
  - **The three files:**
- `tests/experimental/test_cake_kimi_k3_fp8_projection.py` (83 items: 57
need a GPU, 26 run on the host);
- `tests/experimental/test_cake_mla_nvfp4_paged_decode.py` (34 items: 27
are gated on a supported GPU and toolkit, 7 run on the host);
- `tests/experimental/test_cake_minimax_h3_varlen_attention.py` (653
items: 74 need a GPU, 579 run on the host).
- **Both trees.** On each device, the passed / skipped / failed counts
and the skipped ids must be identical on both trees.
- **CUDA hidden.** On both trees, the expected passed / skipped counts
are 26 / 57, 7 / 27 and 579 / 74 for the three files, in the order
listed.
- If the toolkit on the GPU nodes is older than CUDA 13.4, the 27 gated
MLA decode items skip identically on both trees. In that case the result
says so and points to the device-gate rows for those programs.
- CPU checks: all CPU checks passed on both trees (CHECK_RC=0 on the
aarch64 CPU route): ruff and py_compile on the units' tools and the
staged gate tools; the generic pre-commit text hooks on every touched
file; the repository's pre-commit hooks on both full checkouts (empty
patches on the candidate and on the base); the package-manifest checker
(`scripts/check_cake_build_manifests.py --in-tree`: 22 packages, 0
findings, identical output on both trees); the unit replay (each unit
alone at the base: apply exit 0, a second apply exit 2 writing nothing,
every tool report equal to the recorded one; the four units chained in
commit order rebuild a tree byte-identical to this branch's head, 60 of
60 paths); the collected test ids of the three files identical with CUDA
hidden (83 / 34 / 653); the CPU-visible subset of those files passing
with identical counts on both trees (kimi 26 passed / 57 skipped, MLA
decode 7 / 27, MiniMax 579 / 74, 0 failed, identical skipped ids); and
the commit messages (0 banned words, 0 lines over 72 columns, the
trailer last on all four)
- pre-commit runs on both full checkouts, where it must give identical
per-hook results and an empty patch. It also runs on the touched files.
- The Cake build-manifest checker runs on both trees and must exit 0
with identical output.
- Stale-name search: no deleted or moved path may be referenced
anywhere, and the moved files must be present at their new paths. The
stems and digests of the three dead headers have 0 hits.
- Reference census: apart from the reworded kimi README, nothing names a
deleted path. The three test files are byte-identical to the base.
  - Test collection must be identical on both trees.
- Re-applying the four edits to a snapshot of the base must reproduce
the branch byte for byte. Each unit's text proofs must equal their
recorded results. These proofs are the token identity of every deleted
pair, the include-resolution derivation and the dead-header census.
  - Commit message checks.
- Type check: the repository's hook (`pre-commit run mypy --all-files`)
passes on the candidate and on the base with 0 errors each and identical
findings (no Python file changes in this PR)
- The repository's mypy hook runs on this branch and on the base. No
Python file changes, so both runs must give identical findings.

**Not run.** These items are left out of this PR's validation by design.
Each one gives its proof of record.
- **Benchmarks.** This is a mechanical PR with identical SASS per kernel
symbol on all 200 device-gate rows, so there is nothing new to measure.
No benchmark runs.
- **Other architectures.** The three families register only SM100 /
SM103 programs: the architecture tables of the kimi and MLA decode
loaders and the `arches` lists of the MiniMax records name `sm_100a` and
`sm_103a` only. Nothing in this PR runs on any other architecture. The
three dead headers were not included by anything on any architecture.
- **GPU items that the test files do not launch.** Every (program,
architecture) module of the three families has a device-gate row. Every
program of each node's architecture is built and loaded in the module
row. So no module's identity depends on a test item.

## Not in this PR

- **The import-time binding of the chunked LM-head backend
(`flashinfer/chunked_lm_head.py`) and the containment test for the
experimental packages.** These come in a follow-up PR after #6671
merges, because #6671 edits the same file. In that follow-up, the
containment test ships with a four-entry allowlist of the remaining
import-time statements as a burn-down list: `flashinfer/mega_moe_v3.py`,
two in `flashinfer/moe_ep/__init__.py` and one in
`flashinfer/moe_ep/backends/mega/kernel/sm103/__init__.py`.
- **The device-bind blocks of the generated host bindings.** Nothing is
edited here; this is exporter template work (see the issue comment). The
census of the issue's model needs a correction. Under the call-graph
rule, only 2 of the 105 "never-encoding" binding sites remain
never-encoding. The real risk is the bindings that take only the
current-device guard before encoding a tensor map.
- **The 26 self-contained Cake packages of the #6553 contract** (34
private checks headers, 57 helper copies in 3 packages, 26 identical
build scripts). Their helper copies stay. The owners must choose between
keeping "compiles without the repository `csrc/`" and falling back to
the repository include directories under JIT.
- **`flashinfer/mega_moe_v3.py`** (19 lines; a public import path used
by an example and a doc). This is a product decision: delete it or keep
deferred re-exports.
- **The two import-time registrations in `flashinfer/moe_ep/` named
above.** This is an owner decision; they change when the SM103 backend
registers.
- **Behaviour, API or exporter changes:** environment-only knobs, lazy
loading of the 10 eager Cake loaders, an SM-count / configure-once
helper in the shared host utilities, the exporter template changes, and
the `flashinfer/gdn_kernels/experimental` naming question.
- **Anything that changes device code or SASS,
`.pre-commit-config.yaml`, and the loaders' include order.** The
configuration's exclusion of `csrc/cake_device_helpers/` from the
formatter stays, and these PRs never edit that file. The include order
is unchanged.
- **The helper-name digest scheme (`cake_<helper>_<16-hex>`).** Nothing
here renames or re-hashes a helper. The recipe is a question for the
exporter.
- **Exporter requests.** These are requests, not PR changes, and the
issue comment addresses them to the exporter owners:
- for a family whose loader lists the repository `csrc/` on its include
path, emit no package copy of a helper whose name exists in
`csrc/cake_device_helpers/`, and write a new helper name into that
directory instead of the package;
  - document the digest recipe;
- regenerate the device-bind blocks of the older bindings with the
current template;
  - keep one in-repository template for the private checks header.

```experimental-tests
tests/experimental/test_cake_kimi_k3_fp8_projection.py
tests/experimental/test_cake_mla_nvfp4_paged_decode.py
tests/experimental/test_cake_minimax_h3_varlen_attention.py
```

Part of #6672

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified where compiler helper headers are located and the order in
which include paths are searched.
* **Changes**
* Removed generated CUDA device-helper headers from the experimental
kernel components. The affected helper files are no longer available in
those locations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4c73181](https://github.com/flashinfer-ai/flashinfer/commit/4c7318173bacd09d0f6ec59ff3ce551fb1e56147)

- **作者**: eigen
- **时间**: 2026-10-22T21:09:42Z
- **提交信息**: feat(cake_kda): context-parallel packed KDA grad with precise cross-rank state passing and per-document zigzag for GLM-5.3-Flash with grad (#7002)

Cake packed KDA, a chunked KDA training backend for documents packed
into one sequence, has two Cake variants: single-device and
context-parallel. This PR delivers the context-parallel variant:
cross-rank state passing through affine state summaries in FP32, three
partition layouts (contiguous, zigzag, and per-document zigzag +
ragged), saved-context and checkpoint-replay backward, and the halo
variant of the width-4 causal conv1d + SiLU training backend. On NVIDIA
GB300 (sm_103a), its speedup over the KDA context-parallel training of
flash-linear-attention (FLA KCP) ranges from 1.3058x to 2.4679x across
all 144 configurations and both sessions. Against Cake head-parallel
context parallelism built from the existing single-device kernel
(head-CP), the speedup ranges from 1.6184x to 2.3319x.

Latency in ms, NVIDIA GB300 (sm_103a), CUDA 13.0, driver 580.159.03, H =
64 heads, median over steady iterations of the slowest rank, two
sessions s1 / s2 on different nodes; CP2 / CP4 on one node, CP8 on two
nodes, CP16 on four nodes of one NVL72 domain; B1 = module forward, B3 =
forward + checkpoint replay + backward; for the per-document layout the
FLA KCP baseline is the faster of FLA's two layouts (the arm is named in
each cell: fla_C = contiguous, fla_Z = zigzag).

| pack | CP | layout | boundary | Cake ms (s1 / s2) | FLA KCP ms (s1 /
s2, arm) | speedup vs FLA KCP (s1 / s2) | Cake ms vs head-CP run (s1 /
s2) | Cake head-CP ms (s1 / s2) | speedup vs head-CP (s1 / s2) |
|---|---|---|---|---|---|---|---|---|---|
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B1 = forward | 17.927 /
17.929 | 33.597 / 33.576 (fla_C) | 1.8741 / 1.8727 | 17.916 / 17.926 |
36.925 / 36.926 | 2.0610 / 2.0599 |
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 75.601 / 75.563 | 136.119 / 135.937 (fla_C) | 1.8005
/ 1.7990 | 75.586 / 75.557 | 134.179 / 134.157 | 1.7752 / 1.7756 |
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B1 = forward | 18.147 /
18.148 | 42.477 / 42.638 (fla_Z) | 2.3407 / 2.3494 | 18.146 / 18.142 |
37.072 / 37.013 | 2.0430 / 2.0401 |
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 76.066 / 76.012 | 163.469 / 163.477 (fla_Z) | 2.1490
/ 2.1507 | 76.020 / 76.001 | 133.962 / 133.962 | 1.7622 / 1.7626 |
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 18.214 / 18.211 | 33.697 / 33.636 (fla_C) | 1.8500 / 1.8471 |
18.202 / 18.202 | 37.046 / 37.069 | 2.0352 / 2.0365 |
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 75.865 / 75.880 | 136.072 /
136.012 (fla_C) | 1.7936 / 1.7925 | 75.888 / 75.876 | 134.068 / 133.974
| 1.7667 / 1.7657 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B1 = forward | 9.281 /
9.278 | 22.140 / 22.202 (fla_C) | 2.3855 / 2.3930 | 9.283 / 9.273 |
21.414 / 21.253 | 2.3069 / 2.2919 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 38.590 / 38.499 | 89.905 / 89.638 (fla_C) | 2.3298 /
2.3283 | 38.589 / 38.508 | 75.783 / 75.354 | 1.9639 / 1.9568 |
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B1 = forward | 9.533 / 9.555
| 22.155 / 22.124 (fla_Z) | 2.3240 / 2.3155 | 9.518 / 9.533 | 21.449 /
21.315 | 2.2534 / 2.2359 |
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 39.193 / 39.187 | 88.666 / 88.205 (fla_Z) | 2.2623 /
2.2509 | 39.180 / 39.201 | 75.715 / 75.247 | 1.9325 / 1.9195 |
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 9.376 / 9.381 | 22.087 / 22.015 (fla_Z) | 2.3556 / 2.3468 |
9.381 / 9.380 | 21.396 / 21.248 | 2.2809 / 2.2652 |
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 38.230 / 38.194 | 88.515 /
88.098 (fla_Z) | 2.3153 / 2.3066 | 38.230 / 38.259 | 75.870 / 75.514 |
1.9846 / 1.9738 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B1 = forward | 5.110 /
5.114 | 11.681 / 11.671 (fla_C) | 2.2858 / 2.2824 | 5.111 / 5.110 |
11.266 / 11.273 | 2.2042 / 2.2063 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 20.482 / 20.497 | 46.333 / 46.387 (fla_C) | 2.2621 /
2.2631 | 20.503 / 20.509 | 37.638 / 37.646 | 1.8357 / 1.8356 |
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B1 = forward | 5.174 / 5.162
| 11.892 / 11.879 (fla_Z) | 2.2984 / 2.3014 | 5.170 / 5.158 | 11.340 /
11.362 | 2.1933 / 2.2026 |
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 20.375 / 20.380 | 46.190 / 46.261 (fla_Z) | 2.2670 /
2.2699 | 20.376 / 20.368 | 38.448 / 38.466 | 1.8869 / 1.8885 |
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 5.269 / 5.288 | 11.711 / 11.720 (fla_C) | 2.2229 / 2.2165 |
5.262 / 5.285 | 11.345 / 11.366 | 2.1560 / 2.1505 |
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 20.664 / 20.596 | 46.277 /
46.205 (fla_Z) | 2.2395 / 2.2434 | 20.602 / 20.606 | 38.504 / 38.456 |
1.8690 / 1.8663 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B1 = forward | 2.960 /
2.947 | 6.314 / 6.301 (fla_C) | 2.1329 / 2.1381 | 2.975 / 2.944 | 6.125
/ 6.126 | 2.0587 / 2.0809 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 11.074 / 11.053 | 24.310 / 24.312 (fla_C)
| 2.1952 / 2.1996 | 11.086 / 11.059 | 20.359 / 20.210 | 1.8365 / 1.8274
|
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B1 = forward | 3.058 / 3.046
| 7.097 / 7.089 (fla_Z) | 2.3208 / 2.3274 | 3.054 / 3.043 | 6.224 /
6.220 | 2.0376 / 2.0440 |
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 11.515 / 11.468 | 26.135 / 26.085 (fla_Z) | 2.2698 /
2.2745 | 11.520 / 11.574 | 20.570 / 20.569 | 1.7855 / 1.7772 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 3.197 / 3.188 | 6.370 / 6.395 (fla_C) | 1.9928 / 2.0060 |
3.193 / 3.180 | 6.235 / 6.214 | 1.9528 / 1.9543 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 11.506 / 11.512 | 24.413 /
24.453 (fla_C) | 2.1218 / 2.1241 | 11.496 / 11.485 | 20.547 / 20.569 |
1.7874 / 1.7909 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B1 = forward | 16.994 /
16.297 | 40.776 / 40.219 (fla_C) | 2.3994 / 2.4679 | 16.296 / 16.279 |
33.033 / 33.054 | 2.0270 / 2.0305 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 68.123 / 68.125 | 144.010 / 143.903 (fla_C) | 2.1140
/ 2.1123 | 68.090 / 68.094 | 116.391 / 116.430 | 1.7094 / 1.7098 |
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B1 = forward | 17.078 /
17.083 | 37.142 / 37.114 (fla_Z) | 2.1748 / 2.1726 | 17.076 / 17.083 |
33.139 / 33.161 | 1.9407 / 1.9411 |
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 70.823 / 70.845 | 146.212 / 146.334 (fla_Z) | 2.0645
/ 2.0656 | 70.856 / 70.856 | 119.718 / 119.765 | 1.6896 / 1.6903 |
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.828 / 16.828 | 37.067 / 37.088 (fla_Z) | 2.2027 / 2.2040 |
16.827 / 16.821 | 33.143 / 33.162 | 1.9697 / 1.9715 |
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 69.983 / 69.959 | 143.982 /
143.974 (fla_C) | 2.0574 / 2.0580 | 70.018 / 69.959 | 114.742 / 116.607
| 1.6387 / 1.6668 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B1 = forward | 8.602 /
8.585 | 20.589 / 20.465 (fla_C) | 2.3936 / 2.3838 | 8.606 / 8.578 |
19.602 / 19.414 | 2.2777 / 2.2631 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 35.058 / 35.006 | 82.533 / 82.144 (fla_C) | 2.3542 /
2.3465 | 35.054 / 35.049 | 65.715 / 68.034 | 1.8747 / 1.9411 |
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B1 = forward | 8.790 / 8.796
| 20.033 / 20.018 (fla_Z) | 2.2791 / 2.2758 | 8.784 / 8.796 | 19.577 /
19.416 | 2.2288 / 2.2074 |
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 35.947 / 35.893 | 80.661 / 80.327 (fla_Z) | 2.2439 /
2.2379 | 35.939 / 35.889 | 68.741 / 68.230 | 1.9127 / 1.9011 |
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.726 / 8.742 | 20.072 / 20.027 (fla_Z) | 2.3004 / 2.2908 |
8.734 / 8.737 | 19.591 / 19.417 | 2.2431 / 2.2223 |
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 35.203 / 35.243 | 80.685 /
80.336 (fla_Z) | 2.2920 / 2.2795 | 35.187 / 35.215 | 68.509 / 68.039 |
1.9470 / 1.9321 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B1 = forward | 4.822 /
4.795 | 10.721 / 10.725 (fla_C) | 2.2233 / 2.2367 | 4.816 / 4.797 |
10.342 / 10.380 | 2.1474 / 2.1637 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.864 / 18.851 | 42.221 / 42.297 (fla_C) | 2.2382 /
2.2438 | 18.876 / 18.832 | 35.192 / 35.198 | 1.8644 / 1.8691 |
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B1 = forward | 4.748 / 4.745
| 10.810 / 10.824 (fla_Z) | 2.2767 / 2.2810 | 4.745 / 4.739 | 10.315 /
10.327 | 2.1738 / 2.1791 |
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 18.621 / 18.634 | 42.163 / 42.179 (fla_Z) | 2.2643 /
2.2635 | 18.620 / 18.608 | 33.817 / 33.790 | 1.8162 / 1.8159 |
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.797 / 4.798 | 10.687 / 10.717 (fla_C) | 2.2281 / 2.2338 |
4.796 / 4.791 | 10.329 / 10.330 | 2.1539 / 2.1563 |
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 18.610 / 18.630 | 42.169 /
42.180 (fla_Z) | 2.2660 / 2.2640 | 18.590 / 18.681 | 34.039 / 35.282 |
1.8310 / 1.8886 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B1 = forward | 2.872 /
2.902 | 5.921 / 5.939 (fla_C) | 2.0614 / 2.0467 | 2.823 / 2.873 | 5.778
/ 5.805 | 2.0467 / 2.0206 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.660 / 11.094 | 22.407 / 22.423 (fla_C)
| 2.1020 / 2.0212 | 10.656 / 10.951 | 18.842 / 18.875 | 1.7682 / 1.7236
|
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B1 = forward | 3.044 / 3.061
| 6.710 / 6.762 (fla_Z) | 2.2043 / 2.2090 | 3.017 / 3.374 | 5.791 /
6.124 | 1.9192 / 1.8149 |
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 11.202 / 11.556 | 24.387 / 24.535 (fla_Z) | 2.1769 /
2.1232 | 11.205 / 11.176 | 18.886 / 18.822 | 1.6855 / 1.6842 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.913 / 2.911 | 5.923 / 5.926 (fla_C) | 2.0329 / 2.0361 |
2.978 / 2.899 | 6.067 / 5.782 | 2.0372 / 1.9946 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.530 / 10.513 | 22.435 /
22.425 (fla_C) | 2.1306 / 2.1330 | 10.522 / 10.489 | 18.851 / 18.838 |
1.7916 / 1.7960 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B1 = forward | 18.629 /
18.639 | 26.365 / 26.362 (fla_C) | 1.4152 / 1.4143 | 18.621 / 18.628 |
38.541 / 38.549 | 2.0698 / 2.0694 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 78.617 / 78.572 | 124.204 / 124.195 (fla_C) | 1.5799
/ 1.5807 | 78.552 / 78.592 | 139.753 / 139.740 | 1.7791 / 1.7780 |
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B1 = forward | 18.491 /
18.483 | 35.845 / 35.908 (fla_Z) | 1.9386 / 1.9428 | 18.483 / 18.486 |
38.700 / 38.715 | 2.0938 / 2.0943 |
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 78.015 / 78.001 | 151.711 / 151.823 (fla_Z) | 1.9446
/ 1.9464 | 78.027 / 78.014 | 139.745 / 139.545 | 1.7910 / 1.7887 |
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 19.355 / 19.348 | 26.435 / 26.414 (fla_C) | 1.3658 / 1.3652 |
19.349 / 19.341 | 38.721 / 38.683 | 2.0012 / 2.0001 |
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 80.359 / 80.338 | 124.299 /
124.276 (fla_C) | 1.5468 / 1.5469 | 80.322 / 80.304 | 139.365 / 139.598
| 1.7351 / 1.7384 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B1 = forward | 9.733 /
9.731 | 22.210 / 22.287 (fla_C) | 2.2818 / 2.2903 | 9.732 / 9.725 |
22.137 / 22.112 | 2.2746 / 2.2738 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 40.240 / 40.242 | 88.882 / 88.936 (fla_C) | 2.2088 /
2.2100 | 40.310 / 40.239 | 78.377 / 78.419 | 1.9444 / 1.9488 |
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B1 = forward | 10.007 /
10.012 | 23.425 / 23.442 (fla_Z) | 2.3408 / 2.3414 | 10.003 / 9.994 |
22.211 / 22.171 | 2.2204 / 2.2185 |
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 40.958 / 40.962 | 92.855 / 92.877 (fla_Z) | 2.2671 /
2.2674 | 40.929 / 40.943 | 78.362 / 78.160 | 1.9146 / 1.9090 |
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 9.904 / 9.905 | 22.362 / 22.462 (fla_C) | 2.2579 / 2.2677 |
11.086 / 9.898 | 23.731 / 22.193 | 2.1407 / 2.2422 |
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 40.085 / 40.076 | 89.014 /
88.864 (fla_C) | 2.2206 / 2.2174 | 40.054 / 40.062 | 78.356 / 78.242 |
1.9563 / 1.9530 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B1 = forward | 5.363 /
5.360 | 12.239 / 12.252 (fla_C) | 2.2824 / 2.2859 | 5.354 / 5.348 |
12.204 / 12.227 | 2.2795 / 2.2860 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 21.435 / 21.430 | 48.575 / 48.698 (fla_C) | 2.2662 /
2.2725 | 21.449 / 21.416 | 42.124 / 42.116 | 1.9639 / 1.9666 |
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B1 = forward | 5.342 / 5.349
| 12.380 / 12.382 (fla_Z) | 2.3176 / 2.3149 | 5.335 / 5.342 | 12.218 /
12.237 | 2.2903 / 2.2909 |
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 21.277 / 21.281 | 48.349 / 48.414 (fla_Z) | 2.2724 /
2.2750 | 21.271 / 21.288 | 42.097 / 42.098 | 1.9791 / 1.9775 |
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 5.532 / 5.528 | 12.183 / 12.230 (fla_C) | 2.2024 / 2.2125 |
5.522 / 5.520 | 12.211 / 12.219 | 2.2113 / 2.2135 |
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 21.667 / 21.624 | 48.386 /
48.370 (fla_Z) | 2.2332 / 2.2369 | 21.655 / 21.679 | 42.093 / 42.235 |
1.9438 / 1.9482 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B1 = forward | 3.132 /
3.119 | 6.689 / 6.697 (fla_C) | 2.1357 / 2.1474 | 3.129 / 3.113 | 6.626
/ 6.632 | 2.1177 / 2.1302 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 11.617 / 11.725 | 25.529 / 25.615 (fla_C)
| 2.1976 / 2.1847 | 11.653 / 11.860 | 21.800 / 21.931 | 1.8708 / 1.8492
|
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B1 = forward | 3.165 / 3.157
| 7.407 / 7.397 (fla_Z) | 2.3407 / 2.3431 | 3.166 / 3.153 | 6.644 /
6.621 | 2.0983 / 2.0999 |
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 11.832 / 11.793 | 27.326 / 27.381 (fla_Z) | 2.3095 /
2.3218 | 11.796 / 11.825 | 22.322 / 22.360 | 1.8924 / 1.8908 |
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 3.378 / 3.384 | 6.671 / 6.686 (fla_C) | 1.9750 / 1.9757 |
3.374 / 3.382 | 6.617 / 6.619 | 1.9614 / 1.9570 |
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 12.383 / 12.679 | 25.516 /
25.746 (fla_C) | 2.0606 / 2.0307 | 12.373 / 12.310 | 22.358 / 22.350 |
1.8070 / 1.8155 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B1 = forward | 17.024 /
17.020 | 24.694 / 24.686 (fla_C) | 1.4505 / 1.4504 | 17.004 / 16.999 |
36.243 / 36.269 | 2.1314 / 2.1336 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 71.927 / 71.917 | 136.727 / 136.461 (fla_C) | 1.9009
/ 1.8975 | 71.955 / 71.945 | 128.499 / 128.052 | 1.7858 / 1.7799 |
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B1 = forward | 17.148 /
17.143 | 33.756 / 33.709 (fla_Z) | 1.9685 / 1.9663 | 17.137 / 17.131 |
36.256 / 36.226 | 2.1156 / 2.1146 |
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 71.981 / 71.986 | 142.446 / 142.358 (fla_Z) | 1.9789
/ 1.9776 | 71.967 / 71.998 | 131.324 / 131.372 | 1.8248 / 1.8247 |
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 17.821 / 17.822 | 24.715 / 24.716 (fla_C) | 1.3868 / 1.3869 |
17.812 / 17.815 | 36.236 / 36.256 | 2.0343 / 2.0351 |
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 74.179 / 74.174 | 136.354 /
136.465 (fla_C) | 1.8382 / 1.8398 | 74.256 / 74.182 | 128.134 / 128.059
| 1.7256 / 1.7263 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B1 = forward | 9.120 /
9.115 | 21.698 / 21.678 (fla_C) | 2.3791 / 2.3784 | 9.111 / 9.115 |
21.246 / 21.246 | 2.3319 / 2.3308 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 37.317 / 37.327 | 87.162 / 87.158 (fla_C) | 2.3357 /
2.3350 | 37.395 / 37.298 | 74.560 / 73.748 | 1.9938 / 1.9773 |
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B1 = forward | 9.199 / 9.202
| 21.453 / 21.418 (fla_Z) | 2.3322 / 2.3276 | 9.201 / 9.201 | 21.282 /
21.170 | 2.3131 / 2.3009 |
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 37.906 / 37.861 | 85.592 / 85.251 (fla_Z) | 2.2580 /
2.2517 | 37.871 / 37.858 | 74.838 / 74.495 | 1.9761 / 1.9678 |
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 9.379 / 9.397 | 21.520 / 21.543 (fla_Z) | 2.2945 / 2.2925 |
9.386 / 9.385 | 21.262 / 21.237 | 2.2652 / 2.2627 |
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 38.225 / 38.242 | 85.231 /
85.218 (fla_Z) | 2.2297 / 2.2284 | 38.223 / 38.204 | 74.488 / 74.505 |
1.9488 / 1.9502 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B1 = forward | 4.960 /
4.973 | 11.283 / 11.288 (fla_C) | 2.2747 / 2.2701 | 4.965 / 4.964 |
11.031 / 11.028 | 2.2218 / 2.2217 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 19.817 / 19.819 | 44.702 / 44.698 (fla_C) | 2.2557 /
2.2553 | 19.801 / 19.844 | 36.984 / 36.562 | 1.8677 / 1.8424 |
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B1 = forward | 5.010 / 5.012
| 11.431 / 11.438 (fla_Z) | 2.2815 / 2.2822 | 5.017 / 5.000 | 11.120 /
11.111 | 2.2163 / 2.2221 |
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 19.741 / 19.707 | 44.528 / 44.612 (fla_Z) | 2.2555 /
2.2638 | 19.737 / 19.681 | 37.735 / 38.121 | 1.9119 / 1.9370 |
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 5.072 / 5.454 | 11.343 / 11.803 (fla_C) | 2.2365 / 2.1642 |
5.067 / 5.055 | 11.113 / 11.105 | 2.1932 / 2.1968 |
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 19.666 / 19.684 | 44.579 /
44.646 (fla_Z) | 2.2668 / 2.2681 | 19.666 / 19.671 | 37.729 / 37.943 |
1.9185 / 1.9289 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B1 = forward | 2.885 /
2.865 | 6.154 / 6.122 (fla_C) | 2.1333 / 2.1365 | 2.880 / 2.858 | 6.023
/ 6.006 | 2.0914 / 2.1013 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.715 / 10.693 | 23.522 / 23.566 (fla_C)
| 2.1954 / 2.2038 | 10.710 / 10.727 | 20.193 / 20.395 | 1.8855 / 1.9014
|
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B1 = forward | 3.056 / 3.023
| 6.956 / 6.951 (fla_Z) | 2.2762 / 2.2992 | 3.057 / 2.999 | 6.123 /
6.099 | 2.0031 / 2.0338 |
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 11.374 / 11.270 | 25.556 / 25.542 (fla_Z) | 2.2469 /
2.2665 | 11.487 / 11.319 | 20.297 / 20.296 | 1.7670 / 1.7932 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 3.106 / 3.088 | 6.207 / 6.199 (fla_C) | 1.9987 / 2.0076 |
3.094 / 3.087 | 6.106 / 6.099 | 1.9734 / 1.9758 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 11.174 / 11.169 | 23.595 /
23.656 (fla_C) | 2.1115 / 2.1180 | 11.172 / 11.158 | 20.262 / 20.295 |
1.8137 / 1.8188 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B1 = forward | 18.188 /
18.184 | 30.607 / 30.601 (fla_C) | 1.6828 / 1.6829 | 18.174 / 18.184 |
38.498 / 38.537 | 2.1183 / 2.1193 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 76.349 / 76.311 | 133.463 / 133.501 (fla_C) | 1.7481
/ 1.7494 | 76.339 / 76.328 | 139.535 / 139.478 | 1.8278 / 1.8274 |
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B1 = forward | 18.120 /
18.136 | 38.370 / 38.363 (fla_Z) | 2.1175 / 2.1153 | 18.109 / 18.121 |
38.652 / 38.614 | 2.1343 / 2.1309 |
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 76.122 / 76.105 | 156.849 / 156.947 (fla_Z) | 2.0605
/ 2.0623 | 76.144 / 76.111 | 138.818 / 138.281 | 1.8231 / 1.8168 |
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 18.652 / 18.653 | 30.652 / 30.672 (fla_C) | 1.6433 / 1.6444 |
18.641 / 18.643 | 38.613 / 38.609 | 2.0714 / 2.0709 |
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 77.727 / 77.722 | 133.591 /
133.597 (fla_C) | 1.7187 / 1.7189 | 77.709 / 77.702 | 138.596 / 138.535
| 1.7835 / 1.7829 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B1 = forward | 9.511 /
9.506 | 20.115 / 20.043 (fla_C) | 2.1150 / 2.1085 | 9.500 / 9.503 |
22.073 / 22.048 | 2.3236 / 2.3200 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 39.272 / 39.284 | 86.611 / 86.625 (fla_C) | 2.2054 /
2.2051 | 39.274 / 39.270 | 78.225 / 78.211 | 1.9918 / 1.9916 |
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B1 = forward | 9.805 / 9.798
| 20.292 / 20.260 (fla_Z) | 2.0695 / 2.0679 | 9.794 / 9.793 | 22.150 /
22.125 | 2.2615 / 2.2593 |
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 40.176 / 40.150 | 84.814 / 84.678 (fla_Z) | 2.1110 /
2.1090 | 40.143 / 40.187 | 78.144 / 78.088 | 1.9466 / 1.9431 |
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 9.726 / 9.729 | 20.103 / 20.129 (fla_C) | 2.0670 / 2.0690 |
9.712 / 9.712 | 22.129 / 22.127 | 2.2784 / 2.2783 |
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 39.331 / 39.286 | 84.841 /
84.735 (fla_Z) | 2.1571 / 2.1569 | 39.282 / 39.296 | 78.018 / 78.053 |
1.9861 / 1.9863 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B1 = forward | 5.238 /
5.250 | 11.928 / 11.982 (fla_C) | 2.2773 / 2.2824 | 5.232 / 5.252 |
11.852 / 11.859 | 2.2654 / 2.2578 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 20.938 / 20.966 | 47.355 / 47.469 (fla_C) | 2.2616 /
2.2641 | 20.916 / 20.956 | 40.713 / 40.740 | 1.9465 / 1.9441 |
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B1 = forward | 5.274 / 5.274
| 12.362 / 12.331 (fla_Z) | 2.3440 / 2.3382 | 5.265 / 5.258 | 11.859 /
11.856 | 2.2526 / 2.2547 |
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 20.825 / 20.816 | 47.413 / 47.410 (fla_Z) | 2.2768 /
2.2776 | 20.812 / 20.829 | 39.332 / 39.226 | 1.8899 / 1.8832 |
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 5.480 / 5.479 | 11.934 / 11.948 (fla_C) | 2.1776 / 2.1809 |
5.469 / 5.478 | 11.851 / 11.847 | 2.1668 / 2.1628 |
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 21.438 / 21.479 | 47.342 /
47.461 (fla_C) | 2.2083 / 2.2097 | 21.465 / 21.476 | 40.811 / 39.341 |
1.9013 / 1.8319 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B1 = forward | 3.207 /
3.102 | 6.905 / 6.582 (fla_C) | 2.1534 / 2.1219 | 3.084 / 3.060 | 6.491
/ 6.464 | 2.1051 / 2.1127 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 11.478 / 11.439 | 24.989 / 24.986 (fla_C)
| 2.1772 / 2.1843 | 11.402 / 11.492 | 21.767 / 21.770 | 1.9091 / 1.8944
|
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B1 = forward | 3.107 / 3.100
| 7.161 / 7.139 (fla_Z) | 2.3048 / 2.3034 | 3.096 / 3.097 | 6.474 /
6.462 | 2.0911 / 2.0865 |
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 11.703 / 11.711 | 27.011 / 27.012 (fla_Z) | 2.3080 /
2.3066 | 11.665 / 11.663 | 21.775 / 21.537 | 1.8666 / 1.8467 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 3.282 / 3.461 | 6.556 / 6.835 (fla_C) | 1.9977 / 1.9750 |
3.272 / 3.290 | 6.470 / 6.468 | 1.9778 / 1.9661 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 11.988 / 11.996 | 24.992 /
25.038 (fla_C) | 2.0848 / 2.0871 | 12.002 / 12.035 | 21.117 / 21.600 |
1.7595 / 1.7947 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B1 = forward | 18.189 /
18.181 | 24.771 / 24.770 (fla_C) | 1.3619 / 1.3624 | 18.169 / 18.187 |
36.344 / 36.362 | 2.0003 / 1.9994 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 75.838 / 75.801 | 139.808 / 139.840 (fla_C) | 1.8435
/ 1.8448 | 75.867 / 75.836 | 131.189 / 127.827 | 1.7292 / 1.6856 |
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B1 = forward | 18.447 /
18.442 | 33.134 / 33.086 (fla_Z) | 1.7961 / 1.7941 | 18.430 / 18.446 |
36.302 / 36.270 | 1.9697 / 1.9663 |
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 76.704 / 76.717 | 154.639 / 154.592 (fla_Z) | 2.0160
/ 2.0151 | 76.689 / 76.776 | 131.295 / 131.276 | 1.7121 / 1.7099 |
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 18.972 / 18.969 | 24.776 / 24.770 (fla_C) | 1.3059 / 1.3058 |
18.962 / 18.964 | 36.252 / 36.256 | 1.9118 / 1.9118 |
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 78.734 / 78.737 | 139.457 /
139.510 (fla_C) | 1.7712 / 1.7719 | 78.645 / 78.696 | 127.746 / 127.361
| 1.6243 / 1.6184 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B1 = forward | 9.355 /
9.349 | 22.721 / 22.724 (fla_C) | 2.4287 / 2.4306 | 9.341 / 9.340 |
21.167 / 21.177 | 2.2661 / 2.2674 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 38.610 / 38.639 | 90.944 / 90.953 (fla_C) | 2.3554 /
2.3539 | 38.599 / 38.628 | 73.671 / 73.604 | 1.9086 / 1.9055 |
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B1 = forward | 9.528 / 9.520
| 22.062 / 22.043 (fla_Z) | 2.3155 / 2.3155 | 9.513 / 9.519 | 21.164 /
21.184 | 2.2248 / 2.2255 |
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 39.035 / 39.082 | 88.499 / 88.471 (fla_Z) | 2.2672 /
2.2637 | 39.094 / 39.072 | 74.411 / 74.246 | 1.9034 / 1.9003 |
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 9.817 / 9.816 | 22.052 / 22.043 (fla_Z) | 2.2463 / 2.2456 |
9.826 / 9.817 | 21.188 / 21.172 | 2.1563 / 2.1567 |
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 39.952 / 39.954 | 88.426 /
88.442 (fla_Z) | 2.2133 / 2.2136 | 39.921 / 39.944 | 74.396 / 74.397 |
1.8636 / 1.8625 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B1 = forward | 5.190 /
5.171 | 11.773 / 11.773 (fla_C) | 2.2685 / 2.2766 | 5.181 / 5.169 |
11.315 / 11.315 | 2.1838 / 2.1890 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 20.539 / 20.539 | 46.491 / 46.554 (fla_C) | 2.2635 /
2.2667 | 20.570 / 20.528 | 38.159 / 37.785 | 1.8551 / 1.8407 |
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B1 = forward | 5.133 / 5.178
| 11.806 / 11.826 (fla_Z) | 2.2999 / 2.2840 | 5.129 / 5.157 | 11.313 /
11.307 | 2.2059 / 2.1926 |
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 20.346 / 20.370 | 46.127 / 46.248 (fla_Z) | 2.2672 /
2.2704 | 20.332 / 20.383 | 38.636 / 38.638 | 1.9003 / 1.8956 |
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 5.219 / 5.238 | 11.770 / 11.749 (fla_C) | 2.2551 / 2.2429 |
5.221 / 5.233 | 11.310 / 11.307 | 2.1664 / 2.1608 |
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 20.558 / 20.577 | 46.161 /
46.252 (fla_Z) | 2.2454 / 2.2478 | 20.525 / 20.553 | 38.629 / 38.648 |
1.8821 / 1.8804 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B1 = forward | 3.027 /
3.018 | 6.423 / 6.411 (fla_C) | 2.1222 / 2.1243 | 3.022 / 3.005 | 6.296
/ 6.284 | 2.0834 / 2.0912 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 11.245 / 11.255 | 24.481 / 24.452 (fla_C)
| 2.1770 / 2.1724 | 11.217 / 11.626 | 20.573 / 20.893 | 1.8341 / 1.7971
|
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B1 = forward | 3.133 / 3.125
| 7.095 / 7.242 (fla_Z) | 2.2650 / 2.3171 | 3.193 / 3.073 | 6.559 /
6.281 | 2.0539 / 2.0437 |
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 11.678 / 11.505 | 26.380 / 26.271 (fla_Z) | 2.2590 /
2.2836 | 11.775 / 11.458 | 21.065 / 20.813 | 1.7890 / 1.8166 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 3.070 / 3.080 | 6.407 / 6.412 (fla_C) | 2.0873 / 2.0820 |
3.056 / 3.079 | 6.287 / 6.280 | 2.0570 / 2.0393 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 11.336 / 11.370 | 24.459 /
24.474 (fla_C) | 2.1577 / 2.1525 | 11.363 / 11.375 | 21.081 / 20.893 |
1.8553 / 1.8367 |

The other, single-device Cake variant provides the packed KDA training
forward with saved-context and checkpoint-replay backward, plus the
non-context-parallel causal conv1d + SiLU training backend; sm_100a and
sm_103a are the acceptance architectures, and sm_107a is compiled from
the same sources.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added context-parallel training support for packed KDA and causal
convolution, including partition layouts, per-rank execution, and
automatic handling of fragment boundaries.
* Added forward, backward, and autograd APIs, with options to save
boundary data or recompute it during backward.
  * Added optional CUDA-graph replay for causal convolution.
  * Added kernel support for SM100, SM103, and SM107 architectures.
* **Documentation**
* Added guidance on context-parallel usage, layouts, memory sizing, and
execution options.
* **Tests**
* Added distributed and single-GPU correctness coverage and a
context-parallel performance benchmark.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5295d50](https://github.com/flashinfer-ai/flashinfer/commit/5295d50ac9ff9045aa25e4f8d63c8f274ec1c2ca)

- **作者**: S.J. Lee
- **时间**: 2026-10-22T21:08:59Z
- **提交信息**: perf(attention): e4m3-query FA2 tensor-core decode on SM120 (#6574)

<!-- .github/pull_request_template.md -->

## 📌 Description

FA2 tensor-core decode now takes an e4m3 query over an e4m3 KV cache.
Q·Kᵀ and P·V both run on m16n8k32 e4m3 MMA, so no K or V element is
converted to bf16. The softmax uses the VO-split layout, here from
head_dim_vo 256: each KV warp stages its probabilities in shared memory
as e4m3 words (P × 256) and multiplies the whole 64-token tile into its
own 64-dim output slice. A thread then keeps 32 output accumulators
instead of 128, and no cross-warp output merge is needed. The
denominator stays the fp32 cross-warp sum. The query scale reaches the
kernel the existing way, `run(q_scale=...)` folded into `sm_scale`.

The query dtype is part of the JIT module key, so bf16 and fp16 query
modules do not change; their SASS matches the merge base. The ragged
kernel is not instantiated for an e4m3 query.

`plan()` accepts an e4m3 query only where it was validated: SM120,
single-token decode, e4m3 KV cache, bf16 output, head_dim 256, no RoPE
or soft cap, and 1, 2, 4 or 8 query heads per KV head. Anything else
raises `NotImplementedError`, and `fast_decode_plan()` rejects
multi-token requests for this query.

## 🔍 Related Issues

The FA3 and trtllm-gen paths already take an fp8 query; FA2 did not.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files with `pre-commit run
--files <changed files>` and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see the pre-commit
documentation.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`test_tensor_core_decode_fp8_query` compares the e4m3-query decode
against the bf16-query decode on the same query values (q_scale 0.5,
exact in bf16), for 1, 2, 4 and 8 query heads per KV head. All four pass
on SM120; the test is skipped elsewhere.

Further checks on one SM120 GPU (16 query heads, 8 KV heads, head_dim
256, e4m3 KV with k/v scales):

- **Accuracy:** against an fp64 reference that uses the rounded query,
lengths 1 to 2000, windows 1023 and 4095, and split off, fixed and
default. O max abs error is 0.0138, in line with vLLM's Triton unified
attention on the same inputs. LSE max abs error is 7.9e-6. Re-planning a
captured CUDA graph with other lengths and replaying it gives the same
agreement.
- **SASS:** bf16-query e4m3-KV head-256 and fp16 head-128 batch-prefill
modules built for sm_120a match the merge base (20 objects).
- **Speed:** CUDA-graph GPU time per call for a 1024-token
sliding-window decode at 31 batch sizes from 20 to 128, with two length
profiles. The timed build is this commit plus the separate CUDA-graph
merge-path change; it is not this commit alone. Each row is the
geometric mean over the batch sizes.

| Comparison | Profile 1 | Profile 2 |
|---|---|---|
| e4m3 query / bf16 query (this decode) | 0.963 | 0.962 |
| e4m3 query / vLLM Triton unified attention, both given a pre-quantized
query | 0.961 | 0.960 |
| The same, both quantizing the query inside the call | 0.962 | 0.962 |

The e4m3 query was faster than the bf16 query at every batch size.

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
* Added support for FP8 E4M3 queries in FlashAttention 2 batch prefill
when the query and KV cache use the matching format.
* Added support for FP8 E4M3 queries in paged prefill on SM120 when the
query and KV cache use the matching format.
* Added support for FP8 E4M3 queries in tensor-core decode on SM120 with
BF16 outputs, single-token queries, and query-to-KV head ratios of 1, 2,
4, or 8.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: lesj0610 <lesj0610@gmail.com>

### [02b9c65](https://github.com/flashinfer-ai/flashinfer/commit/02b9c659254a15e214a02ddf6b34b6fa6c3541a1)

- **作者**: eigen
- **时间**: 2026-10-22T21:05:48Z
- **提交信息**: docs(cake_gdp): clarify the prefill backend launch and host-sync notes (#6998)

Docs-only follow-up to #6983: the `backend` docstring in
`flashinfer/gdp_prefill.py` and the `cake_chunk_gated_delta_product`
docstring in `flashinfer/cake_gdp_backend/__init__.py` now state that a
call issues one Cake kernel launch (the split programs add a workspace
clear and the item-table upload) and that a device-to-host
synchronization is issued only when `cu_seqlens_cpu` is not given,
replacing the "nothing is read on the host" claim a review comment
flagged as contradicting the `cu_seqlens_cpu` paragraph.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified Cake backend launch and setup behavior, including when
workspace clearing and item-table upload occur.
* Documented how providing CPU sequence offsets avoids copying offsets
from the device; otherwise, offsets are copied to the host once.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c139626](https://github.com/flashinfer-ai/flashinfer/commit/c13962606c066e93564b8f45d1ea740b7533039b)

- **作者**: Yinzuo Jiang
- **时间**: 2026-10-22T20:56:29Z
- **提交信息**: refactor(topk): remove unused device function RadixSelectOneRound (#3037)

<!-- .github/pull_request_template.md -->

## 📌 Description

Remove unused device function RadixSelectOneRound in topk.cuh

In addition to RadixSelectOneRound, the functions
RadixBuildLocalHistogram (lines 371-392) and RadixFindThresholdBucket
(lines 332-353) are unused as their logic has been inlined into
RadixSelectFromSharedMemory. Consider removing them as part of this
refactor to further clean up the codebase.

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Streamlined internal top-k selection logic by removing an obsolete
selection step.
  * Preserved all public interfaces and externally visible behavior.
* No user-facing functionality or configuration changes are included in
this update.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [fb644f5](https://github.com/flashinfer-ai/flashinfer/commit/fb644f5e0a4d34afeda2380f1af0e21e22940cc5)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-22T20:11:50Z
- **提交信息**: fix(moe_ep): fix MegaMoE deferred routing weights and workspace profiles (#6414)

<!-- .github/pull_request_template.md -->

## 📌 Description

Deferred NVFP4 output can omit routing weights or apply them twice when
an explicit knob dictionary changes `apply_topk_in_fc1`. Use the
resolved frontend configuration for the returned weights, and reject
knobs that disable a requested deferred output mode before allocation.

Workspace handles now adopt the default only when both capacity and
live-token profile match. The same check prevents explicit knobs from
replacing an allocated default while allowing another live-token profile
at the same capacity. Legacy cache entries count as full-capacity
workloads when mixed with newer live-token entries, so adding a smaller
profile keeps the existing full-capacity winner. The host tests mock
reducer device support, and the tuning guide now describes multiple
workload profiles in one cache file and the runtime requirements.

## 🔍 Related Issues

Follow-up to #6253.

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

Pre-commit passed for the nine changed files (`pre-commit run --files
...`).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Host validation passed with 250 tests and eight Blackwell GPU tests
skipped:

```bash
pytest -q tests/moe_ep/test_knob_cache.py \
  tests/moe_ep/test_mega_workspace_api.py \
  tests/moe_ep/test_mega_workspace_knobs.py \
  tests/moe_ep/test_mega_tuned_knobs.py \
  tests/moe_ep/test_workspace_pool.py \
  tests/moe_ep/test_tuning_dispatch.py
```

The public API documentation check and CUDA configuration validation
passed. The tuning guide’s shell examples pass `bash -n`.

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

GPU kernels were not run. The routing-weight regression test uses the
real NVFP4 configuration path with host allocations and synthetic
per-route outputs. Vendored kernel sources are unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Tuning-cache lookups now recognize older entries as full-capacity
profiles while preserving separate results for workloads with different
live-token counts.
* Workspaces now distinguish full-capacity profiles from profiles with a
configured live-token count, preventing one profile from replacing
another.
* Requests for deferred top-k reduction now return a clear error when
the selected configuration does not support it.
  * Unfinalized-output weights now follow the resolved configuration.

* **Documentation**
* Updated tuning and benchmark guidance, including cache behavior and
general environment setup.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [368aae5](https://github.com/flashinfer-ai/flashinfer/commit/368aae5e288f39154f2003288acd2d776aecd775)

- **作者**: Mingyang Wang
- **时间**: 2026-10-22T19:37:09Z
- **提交信息**: feat(mla): add Rubin MTP backend to the planned wrapper (#6177)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add `cute-dsl-rubin-mtp` to `BatchMLAPagedAttentionWrapper` for FP8
absorbed MLA on Rubin SM107. It participates in the `cute-dsl` alias and
wrapper autotuning, with split tactics and a bounded auto preference for
measured winning regions.

The adapter supports live KV lengths and CUDA graph replay, preserves
empty/masked-row semantics, and rejects unsupported compiler, scalar and
indexing configurations before launch. Shared monolithic changes expose
split tactics safely and allow legal workspaces whose byte size exceeds
signed32. Public method signatures and argument defaults are unchanged.

On Rubin SM107 (208 SMs, driver615.12), two independent benchmark
processes retained all six selected wins over `cute-dsl-monolithic`. FP8
packed inputs, 128 heads, 512+64 dimensions, native split1:

| Mode | B/Q/Page/K | Monolithic us | Auto (selects MTP) us |
| --- | --- | --- | --- |
| Graph | 64/4/64/129 | 25.149–25.166 | 17.252–17.259 |
| Graph | 128/2/128/1024 | 36.074–36.096 | 28.159–28.200 |
| Graph | 64/4/128/2048 | 47.963–48.001 | 41.143–41.158 |
| Eager | 64/4/64/8192 | 125.044–125.308 | 121.556–121.604 |
| Eager | 32/4/128/32768 | 277.684–277.744 | 249.732–249.924 |
| Eager | 64/2/128/32768 | 280.688–280.964 | 251.672–252.464 |

Ranges are the two process medians. Graph measurements represent
captured device work; eager event intervals include Python launch gaps.
These are comparisons against monolithic, not a same-machine
before/after bound for host-side fixes. The measured comparison includes
auto, explicit MTP and monolithic, with native split1 and no autotuner
search. Input and output dtype are FP8 E4M3; LSE is FP32.


<details>
<summary>Public-API timing reproduction</summary>

Requires Rubin SM107 and a CuTe DSL/compiler build exposing native SM107
support.
The measured stack used CUDA13.5.25 and CuTe
DSL4.8.0a0+20260922110000.6df00d3.
Use the six cases below with 256 MiB workspace, capacity rounded up
to128,
packed query/KV,128 heads,512+64 dimensions, causal attention and
default PDL.
LSE modes are respectively none/basee/base2/none/base2/basee.

Save this timing-only recipe as `bench_rubin_mtp.py`. For each case
index0–5,
run `python bench_rubin_mtp.py <index> 0` and
`python bench_rubin_mtp.py <index> 1` in separate processes. It uses
warm storage
without L2 flushing, five warmups, five samples of three event batches,
eight
eager calls per batch or64 captured calls per replay, and rotates
backend order.
The reported table was collected by the validation harness using this
setup;
this condensed recipe does not include that harness's numerical
reference checks.

```python
"""Timing recipe for the PR description; select CASE_INDEX and ORDER_OFFSET."""

import gc
import statistics
import sys

import torch
from flashinfer.mla import BatchMLAPagedAttentionWrapper, MLAPlanMetadata

cases = [
    ("graph", 64, 4, 64, 129, "none", 193813854),
    ("graph", 128, 2, 128, 1024, "basee", 193752803),
    ("graph", 64, 4, 128, 2048, "base2", 1196904595),
    ("eager", 64, 4, 64, 8192, "none", 688911001),
    ("eager", 32, 4, 128, 32768, "base2", 2050522178),
    ("eager", 64, 2, 128, 32768, "basee", 969208906),
]
index, order_offset = map(int, sys.argv[1:])
mode, batch, qlen, page, length, lse_mode, seed = cases[index]
assert torch.cuda.get_device_capability() == (10, 7)
generator = torch.Generator(device="cuda").manual_seed(seed)
dtype = torch.float8_e4m3fn


def random_fp8(shape):
    return (
        torch.randn(shape, device="cuda", dtype=torch.bfloat16, generator=generator)
        .mul_(0.5)
        .to(dtype)
    )


query = random_fp8((batch * qlen, 128, 576))
capacity = ((length + 127) // 128) * 128
pages = batch * (capacity // page)
kv = torch.empty((pages, page, 576), dtype=dtype, device="cuda")
chunk = max(1, (32 * 2**20) // (page * 576))
for start in range(0, pages, chunk):
    stop = min(start + chunk, pages)
    kv[start:stop].copy_(random_fp8((stop - start, page, 576)))
table = torch.randperm(pages, device="cuda", generator=generator).reshape(batch, -1)
metadata = MLAPlanMetadata.dense(
    torch.arange(batch + 1, device="cuda", dtype=torch.int32) * qlen,
    table.to(torch.int32),
    torch.full((batch,), length, device="cuda", dtype=torch.int32),
    max_q_len=qlen,
)
workspace = torch.empty(256 * 2**20, dtype=torch.uint8, device="cuda")
out = torch.empty((batch * qlen, 128, 512), dtype=dtype, device="cuda")
lse = torch.empty((batch * qlen, 128), dtype=torch.float32, device="cuda")
backends = ("auto", "cute-dsl-rubin-mtp", "cute-dsl-monolithic")
variants = []


def prepare(backend):
    wrapper = BatchMLAPagedAttentionWrapper(
        workspace, backend=backend, use_cuda_graph=mode == "graph"
    )
    wrapper.plan(
        metadata=metadata, num_heads=128, head_dim_ckv=512, head_dim_kpe=64,
        page_size=page, causal=True, sm_scale=576**-0.5,
        q_data_type=dtype, kv_data_type=dtype, output_dtype=dtype,
        query_layout="packed", kv_cache_layout="packed", lse_mode=lse_mode,
    )

    def run():
        return wrapper.run(
            query=query, kv_cache=kv, out=out,
            lse=lse if lse_mode != "none" else None,
            return_lse=lse_mode != "none", return_lse_base_on_e=lse_mode == "basee",
        )

    stream = torch.cuda.Stream()
    stream.wait_stream(torch.cuda.current_stream())
    with torch.cuda.stream(stream):
        for _ in range(5):
            run()
    torch.cuda.current_stream().wait_stream(stream)
    torch.cuda.synchronize()
    graph = None
    if mode == "graph":
        graph = torch.cuda.CUDAGraph()
        with torch.cuda.graph(graph):
            for _ in range(64):
                run()
    call = graph.replay if graph is not None else run
    for _ in range(5):
        call()
    torch.cuda.synchronize()
    return (wrapper, graph, call)


for backend in backends:
    variants.append(prepare(backend))
samples = [[] for _ in backends]
start_event, stop_event = (torch.cuda.Event(enable_timing=True) for _ in range(2))
for sample in range(5):
    shift = (sample + order_offset + index) % len(backends)
    order = list(range(len(backends)))
    order = order[shift:] + order[:shift]
    for position in order:
        batches = []
        for _ in range(3):
            torch.cuda.synchronize()
            start_event.record()
            for _ in range(1 if mode == "graph" else 8):
                variants[position][2]()
            stop_event.record()
            stop_event.synchronize()
            batches.append(
                start_event.elapsed_time(stop_event) * 1000
                / (64 if mode == "graph" else 8)
            )
        samples[position].append(statistics.median(batches))
for backend, values in zip(backends, samples):
    print(backend, statistics.median(values), "us")
del variants
gc.collect()

```

</details>

## 🔍 Related Issues

Builds on the MLA API unification in #6106, now merged. This change
integrates only the wrapper API.

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

Scoped validation: 510 selected checks passed on SM107 across wrapper
routing,
MTP tuning/numerics, optional import isolation, and monolithic
variable-Q/reducer
paths. Includes regression-first failures and fixes for missing optional
CuTe DSL
and real 2,151,677,952-byte scratch allocations (MTP FP8, monolithic
FP8/BF16/FP16),
plus eager/graph replay, live lengths, zero KV, scalar bounds and large
KV pools.
The full repository suite has not been run. Validation used CUDA13.5.25,
Torch2.15 Rubin and CuTe DSL4.8.0a0+20260922110000.6df00d3. The
source-identical integration was then rebased onto current main;
intervening MLA changes are confined to unrelated sparse DSv4 paths.
Runtime evidence is reused, not a fresh run on the rebased commit.

Scoped `pre-commit run --files ...` passed for all 19 changed/new files,
including
mypy and Ruff. The all-files and hook-installation checkboxes are
intentionally
unchecked because those commands were not performed as part of this
review.

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

- Functional MTP registration remains deferred.
- Auto is a plan-time heuristic; graph replay retains the chosen backend
as live lengths change.
- Workspace byte-length metadata uses 64 bits; device element-index
limits remain enforced.
- SM100/SM103 shared monolithic changes still need checks on those
architectures. No new sanitizer run or broad repository GPU matrix.
- Reference checks sample selected requests/heads for long-context
benchmarks; dedicated wrapper tests cover all rows/heads in their
smaller cases. The timing recipe below is included in the description;
no benchmark or provenance files are added to the repository.
- Positive split tactics and backend cache restoration are covered
separately. A focused positive-tactic cache round-trip test remains a
useful follow-up.
- Upstream vendored license notices are retained. The new adapter/helper
files use FlashInfer's license header.
- Suggested publishing CI scope:
`tests/attention/test_mla_auto_backend.py`,
`tests/attention/test_mla_wrapper.py`,
`tests/attention/test_mla_wrapper_autotune.py`, and
`tests/attention/test_cute_dsl_mla_decode.py`. No CI comment has been
posted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added Rubin MTP as a CuTe DSL backend for supported SM107 FP8
multi-query attention workloads, with automatic backend selection and
autotuning support.
* Added FP8 E4M3 output support to the monolithic and modular CuTe
backends.
* Added static split-budget options for planned monolithic CuTe
execution and an optional KV split budget for monolithic decoding;
automatic split selection remains available by default.
* **Bug Fixes**
* Improved workspace sizing and validation for attention workloads,
including checks for unsupported scales, layouts, and workspace
requirements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0d5dfba](https://github.com/flashinfer-ai/flashinfer/commit/0d5dfbaf542451465d84b5243948dd399d8be71a)

- **作者**: Harrison Zhang
- **时间**: 2026-10-22T18:19:42Z
- **提交信息**: feat(prims-ts): PrimsTS VC-attention-QK16 for dense FMHA context (#6296)

<!-- .github/pull_request_template.md -->

## 📌 Description

VC-Attention-QK16 kernels and optimizations for the PrimTS dense context
FMHA. This will be later productionized for TRT-LLM VisualGen.
The implementation follows the
[paper](https://arxiv.org/html/2609.15810) but uses QK-BF16 BMM1 and
PV-FP8 rather than QK-INT8/PV-FP8.

- **VC-Attention-QK16 kernel.** bf16 Q/K on the 16-bit MMA; V as E4M3
residuals around per-tile
means; P through the ExpCast E4M3 path. Plan/run follow the Sage
attention interface
(`vc_config`, `vc=`). K/V preparation is two CuTe DSL kernels behind
`VCAttentionPreprocessor`.
  Dense bf16 and fp8 paths unchanged.
- **Two V treatments, chosen at plan time.**
- *Tile means* (`VCAttentionConfig()`): the kernel restores each tile's
mean inside the online
softmax with batched UMMA steps on O. V-Smooth demeaning follows the
paper's step schedule.
- *Repair tiles* (`VCAttentionConfig(repair_tiles=N)`): No means. The
highest-residual tokens
are appended as key copies with their E4M3 value residuals, which drops
the mean ring and
UMMA steps and keeps the repair rows out of the softmax denominator.
Cherrypicked this method
from this [blog](https://www.machgen.ai/blog/open-vc-attn), which
discusses a variant of VC-attention.

B300, Wan2.2 P1 (B=2, H=40, S=75.6k): dense 132.4 ms, VC means 136.2 ms,
VC repair 131.3 ms.
LPIPS vs dense unchanged for both.

See the PrimTS VC-Attention-QK16 and PrimTS Open-VC-Attn-QK16 below
(purple and turqoise). Compare them with the original PrimTS
QK-BF16/PV-FP8.
We get:
- **1.2-1.3x/1.15-1.2x B200/300 speedup over trtllm-gen BF16 with better
LPIPS than normal PrimTS BF16** using means restoration.
- **1.29-1.33x/1.16x-1.21x speedup over trtllm-gen BF16 with very
similar LPIPS to VC-attention-QK16** using the cherrypicked tile repair
optimizations from Open-VC-attn.

<img width="2464" height="1184" alt="image"
src="https://github.com/user-attachments/assets/dcc22f47-f606-4a7c-8605-1ddd3d685c85"
/>

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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

New `tests/attention/test_attention_ts_vc.py` (17 cases including the
new repair tiles optimizations).
`tests/attention/test_attention_ts_context.py` (318) unchanged. All pass
on B300.

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
Follows PRs #4879, #5280, #5475, #5900.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added VC-Attention-QK16 for dense, fixed-length prefill, with optional
value preprocessing, E4M3 quantization, tile-mean restoration, and
repair tiles.
* Added configuration and runtime options for planned and one-shot
prefill, plus a reference implementation and usage guidance.
* **Limitations**
* Requires 128-dimensional heads, query-paired attention, equal query
and KV head counts, 16-bit queries and keys, and 8-bit values; supports
dense, contiguous prefill only.
* One-shot prefill does not support repair operands. Runs using the same
VC plan must not overlap.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Harrison Zhang <harrisonz@nvidia.com>

### [c53947e](https://github.com/flashinfer-ai/flashinfer/commit/c53947e2a8bf73d8de89f7fac7ebcd8f8479a1ae)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-22T18:15:33Z
- **提交信息**: ci: persist content-keyed JIT caches across GPU test jobs (#6811)

<!-- .github/pull_request_template.md -->

## 📌 Description

GPU test jobs in PR Test (H100, A10G, T4) run in `docker run --rm`
containers with no sccache and no persistent cache. sccache only covers
the AOT wheel jobs, which build nvcc kernels only. Every GPU test job
therefore recompiles every CuTe-DSL, cuTile, Triton, TIRx and nvcc
kernel it touches. In the H100 lane of run 39327533617, about 5.7 of 7.0
worker-hours of JUnit test time were first-call compile spikes.

This PR keeps the content-keyed caches between jobs on each runner, and
makes compile time per toolchain visible.

**Per-runner compile cache (`ci/bash.sh`, GPU jobs only)**
- Opt-in: PR Test's GPU "Run Test" step sets `CI_COMPILE_CACHE_DIR=${{
runner.workspace }}/flashinfer-compile-cache`; other `ci/bash.sh`
callers (e.g. the nightly package validation) leave it unset and run
cold. On the H100 hosts this is on the NVMe work volume, outside the
checkout that the Cleanup step wipes.
- `ci/bash.sh` mounts a per-CI-image subdirectory of it (the image name
includes the docker tag, so an image bump starts cold) as
`FLASHINFER_WORKSPACE_BASE` and `TRITON_CACHE_DIR`. Image directories
unused for a week are removed.
- The directory is per runner, and a runner runs one job at a time, so
two checkouts never share a directory at once.
- Kept between jobs: FlashInfer CuTe-DSL `.o` files, TIRx, KDA PTX
cubins, Triton, and downloaded cubins.
- Pruned before and after each job:
- nvcc modules: a fresh checkout makes every source newer than its
`.so`, so ninja rebuilds them anyway.
  - `*/autotune`: tests keep tuning from scratch.
  - `generated/` sources and `flashinfer_jit.log`.
- `CUTE_DSL_CACHE_DIR` (the DSL's own file cache) stays ephemeral,
because FlashInfer does not control its key.
- Before each job the cache is cleared if it exceeds
`CI_COMPILE_CACHE_MAX_MB` (default 40 GB) or its volume has less than
`CI_COMPILE_CACHE_MIN_FREE_MB` (default 20 GB) free. Non-numeric values
disable the cache with a warning.

**Strict CuTe-DSL cache key (`FLASHINFER_CUTE_DSL_STRICT_CACHE_KEY=1`,
set by CI; off by default)**
- Problem: many callers key their cache only on `(__file__,)`. For
example, `gdn_decode_mtp.py` imports `device_target` and `dtype_compat`
without hashing them. With a cache shared across commits, a PR that
edits such a helper could be tested against a stale kernel and pass
falsely.
- Strict mode adds the in-package import closure of each
`extra_key_file` to the hash. The closure is built by walking the source
with `ast`, including function-local imports.
- `from pkg import submodule` follows only the submodule.
- The top-level `flashinfer/__init__.py` is never followed. Following it
pulled in all ~900 files of the package; without it, closures are 8–30
files.
- `version.py` and `_build_meta.py` are never followed either: they
carry the build's git commit, which would change every key on every
checkout. The package version is already part of the cache path.
- If a key file cannot be parsed, the disk cache is bypassed, consistent
with the existing handling of unreadable files.

**Build timing (`FLASHINFER_JIT_BUILD_LOG`)**
- Records one JSONL line per build: `toolchain`, `name`, `seconds`.
- Covered: builds through `JitSpec.build_and_load()`, bulk
`build_jit_specs()` prebuilds, and CuTe-DSL `compile_and_persist`.
- Toolchain labels: `nvcc`, `cute_dsl`, `tirx`.
- The PR Test workflow sets the variable, prints
`scripts/summarize_jit_builds.py` output into the job summary, and
uploads the log with the JUnit artifacts.

Docs: `CLAUDE.md` covers the CI cache and has env-table entries for both
new variables.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run on all changed files.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
`tests/jit/test_jit_cache_key_and_build_log.py` (CPU-only) covers:
- closure resolution (helpers, function-local imports, package
`__init__`, the top-level `__init__` exclusion);
- the strict key changing when an imported helper changes and staying
fixed for unrelated files;
  - the parse-failure fallback;
  - build-log records and the summarizer.
- [x] All tests are passing (`unittest`, etc.).
- The new file plus `tests/jit/test_missing_jit_cache_reporting.py` pass
locally (macOS, CPU torch), both with and without
`FLASHINFER_CUTE_DSL_STRICT_CACHE_KEY=1`.
- Scoped PR Test runs on 89bcee8f6 (39695735120, 39721240110,
39790185855) passed on H100, A10G shard 1 and all six AOT builds.

## 🔬 Experimental Track

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

- **Before/after on H100** (Targeted Unittest (H100), same six-file
scope, 578 tests, same CI image, commit 89bcee8f6):

| Run | Runner | Cache at start | CuTe-DSL builds ≥ 1 s | nvcc builds |
Test time | Job time |
  |---|---|---|---:|---:|---:|---:|
| 39695735120 | runner-1 | cold (1 MB) | 205 (1571 s) | 29 (620 s) |
27m52s | 28m21s |
| 39721240110 | runner-2 | cold (1 MB) | 205 (1594 s) | 29 (570 s) |
28m06s | 28m51s |
| 39790185855 | runner-1 | warm (41 MB) | 0 | 29 (536 s) | 6m00s | 6m43s
|

Build seconds are summed over the 8 test workers, so they exceed wall
time. In the warm run no CuTe-DSL build took 1 s or longer (6 sub-second
builds remained, against 13 in each cold run), and the job took about
76% less time. Most of the cold time is the GDN decode file, whose 326
tests run in one worker and pay for its CuTe-DSL compiles serially. nvcc
still rebuilds every run (see the next note). The second run landed on
the other H100 runner, so it was cold too: each runner has its own
cache, and a job only hits when an earlier job ran on the same runner.
- **Cache size:** the warm cache was 41 MB after pruning, for this
scope. A full-suite size is still unmeasured. The follow-up #7016 shares
this cache across runners through S3, so new EC2 leases and added
runners start warm.
- **nvcc is covered by #6810, not here.** This PR prunes nvcc modules
instead of persisting them, because ninja's mtime check rebuilds them
after any fresh checkout. #6810 routes those rebuilds through the S3
sccache, so the two PRs complement each other. Its wrapper derives
`SCCACHE_BASEDIRS` from `FLASHINFER_WORKSPACE_BASE`, which this PR sets
to the stable `/compile-cache/flashinfer`.
- **Merge conflict with #6810:** both PRs edit the GPU "Run Test" step
of `pr-test.yml`. Since #6953 that step builds a `DOCKER_ARGS` list on
`main`, and this PR adds `-e FLASHINFER_JIT_BUILD_LOG
/workspace/junit/jit-builds.jsonl` to it. Whichever PR lands second
keeps both sets of arguments and both PRs' post-run steps.
- **Not instrumented:** Triton, cuTile and the cake nvcc/NVRTC side
paths do not go through `JitSpec`. Their compile time does not appear in
the summary.
- **Not persisted:**
  - cuTile has no FlashInfer disk cache.
- The TRT-LLM DeepGEMM cache (`~/.tensorrt_llm/cache`) is keyed on
shapes only, so it stays ephemeral.
  - The b12x cache (experimental) stays ephemeral.
- **Triton correctness** across commits relies on Triton's own key (JIT
function source plus called JIT functions and constexpr globals).
- **Strict-key tradeoff:** the closure includes `flashinfer/jit/*`
infrastructure. Editing `jit/core.py` or `jit/env.py` therefore
invalidates every CuTe-DSL kernel in CI. This errs toward correctness.
- **Trust:** the runner cache is writable by any job on that runner,
including fork PRs approved with `run-ci`, and later `main` runs on the
same runner load it. The existing shared pip cache in `ci/bash.sh` has
the same property. Splitting the cache by trust level (pushes to `main`
vs PRs) is a possible follow-up.
- **Prune verified in CI:** the prune uses GNU `find -printf`, so on
macOS it removes nothing. In CI the warm cache was 41 MB after a run
that built 29 nvcc modules, so the nvcc output was removed as intended.
- **Durations** come from JUnit `time` attribution; each spike is that
test's time above its file's median.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
  - Added persistent GPU compilation caching for repeated test runs.
- Added optional JIT build timing logs with summaries grouped by
toolchain.
- Added strict CuTe-DSL cache keys that track imported in-package code
changes.
  - Added Markdown and console reports for the slowest JIT builds.
- Added JIT build logs and improved visibility in GPU test artifacts
across non-AOT lanes.

- **Bug Fixes**
- Improved handling of incomplete JIT logs and syntax errors during
cache-key analysis.

- **Documentation**
- Documented GPU compile caching, cache behavior, JIT build summaries,
and configuration options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [78434b9](https://github.com/flashinfer-ai/flashinfer/commit/78434b94b3e596b4fbfe193ed9e5bb7639e05f36)

- **作者**: Adrian
- **时间**: 2026-10-22T17:11:31Z
- **提交信息**: test(sampling): size seed and offset checks by effective support (#6972)

<!-- .github/pull_request_template.md -->

## 📌 Description

Reduce the 1,000-row seed/offset sensitivity batches in the ordinary and
Cake sampling tests using an effective-support collision budget. Both
tests keep their existing output assertions.

On one SM100 GPU (reported as NVIDIA Graphics Device, compute capability
10.0; PyTorch 2.10.0+cu130), at vocabulary size 128,256:

| Test | Before | After | Incremental peak allocation |
|---|---:|---:|---:|
| Ordinary sampling | 1.662 ms | 0.729 ms | 980 MiB → 54 MiB |
| Cake sampling | 5.218 ms | 0.907 ms | 980 MiB → 16 MiB |

Times are synchronized per-function median wall times over five warm
repeats, including fixture construction. Small cases incur
budget-calculation overhead; these results do not imply a universal
speedup. Measurements were collected before the rebase; the changed test
functions and collision helper were verified unchanged afterward.

## 🔍 Related Issues

Follow-up to #6513, #6514, and #6515.

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

- Before rebase: 33 targeted GPU seed/offset cases passed on SM100; 12
ignored-seed/offset fault injections were detected. Cake reference
probabilities and reduced-batch pipeline dispatch were checked.
- After rebase: 19 local CPU budget checks and changed-file pre-commit
hooks passed. The CPU check file is a local validation artifact and is
excluded from this PR. GPU tests were not rerun after the rebase.
- Full repository suite and other GPU architectures were not run.

GPU test scope:

```bash
python -m pytest tests/utils/test_sampling.py tests/utils/test_cake_sampling_upstream.py \
  -k 'different_seed_offset or seed_offset_reproducibility' -q
```

Benchmark method (run on the original and modified revisions with
matching GPU/cache conditions):

```python
import statistics
import time
import torch
from tests.utils.test_sampling import (
    test_sampling_different_seed_offset_produces_different_results as ordinary,
)
from tests.utils.test_cake_sampling_upstream import (
    test_different_seed_offset_produces_different_results as cake,
)

for test in (ordinary, cake):
    test(128256)  # warm up
    torch.cuda.synchronize()
    times, peaks = [], []
    for _ in range(5):
        torch.cuda.reset_peak_memory_stats()
        initial = torch.cuda.memory_allocated()
        torch.cuda.synchronize()
        start = time.perf_counter()
        test(128256)
        torch.cuda.synchronize()
        times.append(time.perf_counter() - start)
        peaks.append(torch.cuda.max_memory_allocated() - initial)
    print(test.__module__, statistics.median(times), max(peaks))
```

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

The test covered in this PR is to verify the sampling seed and offset
working as expected.

Let's consider two random variables $X$ and $Y$, each drawn a token from
a probability vector $p$, then

$$
\Pr[X=Y] = \sum_i \Pr[X=i] \Pr[Y=i] = \sum_i p_i^2 = s
$$

Let this process repeat for $n$ times, each time we start on a new
probability vector $p_r$, then $X$ and $Y$ each produces a $n$-vector of
tokens, such that the $r$-th token is sampled from vector $p_r$. We do
not expect $X=Y$ so we want to make sure the probability $\Pr[X=Y]$ is
low enough. Reusing the equation above, we have

$$
\begin{aligned}
\Pr[X=Y] &= \prod_{r=1}^n \sum_i p_{r,i}^2 = \prod_{r=1}^n s_r \\
&= \exp\sum_r\log(s_r)
\end{aligned}
$$

Let $L_n = \sum_{r=1}^n \log(s_r) < 0$, then we would like to find the
minimal $n$ such that

$$
\begin{aligned}
\exp(L_n) &\le \epsilon \\
L_n &\le \log(\epsilon)
\end{aligned}
$$

The approach here is to collect $p_r$ and then accumulate $s_r$ starting
from $r=1$, and stop when we met $L_n\le \log(\epsilon)$, for $\epsilon$
at the magnitude of $10^{-12}$. Then we do sampling for only such $n$
probability vectors. It turns out $n$ can be much smaller than what used
in the original code.

### [f8664bf](https://github.com/flashinfer-ai/flashinfer/commit/f8664bf064674ee1aa2b9f52833b30b68423d45d)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-22T16:51:48Z
- **提交信息**: fix(ci): match tests/moe_ep by path component before installing the EP stack (#6497)

<!-- .github/pull_request_template.md -->

## 📌 Description

`scripts/task_run_unit_tests.sh` runs
`docker/install/build_flashinfer_ep_pytorch.sh` whenever `TEST_PATH`
contains the substring `moe_ep` on a CUDA 13 image. That also matches
file names outside `tests/moe_ep`: a scoped run of
`tests/experimental/test_cake_mxfp8_megamoe_ep16.py`
("mega**moe_ep**16") installed the whole NCCL-EP stack, including a
DeepGEMM source build, for tests that don't use it.

This PR matches `tests/moe_ep` as whole path components instead.
`tests/moe_ep`, files inside it, and absolute paths ending in
`.../tests/moe_ep` still trigger the install. Names like `megamoe_ep16`
and `tests/moe_ep_other/` no longer do.

A parent directory such as `TEST_PATH=tests` (or an empty `TEST_PATH`)
still doesn't trigger the install. That is unchanged.

## 🔍 Related Issues

Seen on the DGX Spark cu130 PR lane. Before #6379, a false positive
there failed dependency setup in under a minute (job 476981310), because
those containers run as a non-root user and the installer wrote to
`/etc`. #6379 fixed the non-root failure. This PR stops the unnecessary
install.

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

- New test `test_shell_installs_moe_ep_stack_only_for_moe_ep_paths`
checks six `TEST_PATH` values, three that should trigger the install and
three that shouldn't. Against the old substring check, the
`megamoe_ep16` and `moe_ep_other` cases fail. It reuses the stub setup
from #6379's `test_shell_passes_nccl_wheel_library_to_test_runner`, now
pulled into a shared helper `_stage_cuda13_entrypoint`.
- Verified locally: all 24 tests in
`tests/test_sharding/test_shell_entrypoint.py` pass. shellcheck passes
on the script, and the pre-commit hooks passed on the changed files. I
did not run the full suite.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Improved test coverage for CUDA 13+ setup, ensuring the MoE EP
installer runs only when the test path includes `tests/moe_ep` as a
complete component.
* Added coverage to verify the NCCL wheel library path is prepended
correctly when the existing library path is absent, empty, or already
set.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0179e5b](https://github.com/flashinfer-ai/flashinfer/commit/0179e5b312d6aa0c790e8e571b9037bb277f4dbd)

- **作者**: eigen
- **时间**: 2026-10-22T10:10:31Z
- **提交信息**: perf(cake_rmsnorm): faster H512 / H2048 / H6144 grad by bulk-copy backward windows (SM100 / SM103) (#6997)

`cake_rmsnorm_train` is Cake's RMSNorm training kernel: one data type
(BF16 activations and weight, FP32 `rstd` and deterministic FP32
`dweight`) in four variants, plain and residual-fused, each forward and
backward. This PR changes the plain backward (`dx`, `dweight`) at H=512,
H=2048 and H=6144 on sm_100a and sm_103a, and the plain forward at
H=6144 on sm_100a for row counts T in (768, 1024]; sm_107a is unchanged.
The baseline is the previous Cake version, the shipped build of PR
#6939. At these hidden sizes it still runs the row-wise forward programs
and the original backward of PR #5741, which is one cooperative
persistent program per hidden size and architecture (256 threads x 2
CTAs per SM, a two-stage pipeline and Kahan-compensated `dweight`
partials). As in #6939's H=1536 and H=4096 backward, the backward now
ships as row-count windows of the bulk-copy producer/consumer program
(`cp.async.bulk` + mbarrier ring, one CTA per SM, fixed-order tree fold
of the cross-chunk `dweight` reduction, self-resetting flip grid
barrier). Each window instance is tuned per hidden size, architecture
and row-count range (pipeline depth, slab, exit of non-reducing CTAs, L2
eviction hints). Above the last window (H=6144, T > 16384) the original
#5741 program still runs. The changed sm_100a H=6144 forward for T in
(768, 1024] is the shipped pipelined program re-tuned for that range
(five CTAs per SM instead of four). The numerical contract is unchanged
(BF16 I/O, FP32 products and sums, `dx` rounded once, `rstd` in FP32,
and `dweight` in FP32, deterministic and atomics-free). The tree fold
regroups the cross-chunk `dweight` sum, so `dweight` bits differ from
those of #5741's program within the same tolerance, while the re-tuned
H=6144 forward's `y` and `rstd` are bitwise equal to those of the
shipped forward.

Both versions run in the same process on the same GPU. Latencies are
CUPTI kernel-active times (T x H input, cold L2 before every launch),
each the median of 3 counterbalanced paired groups. In the Pass column,
`bwd` is the backward, `step` is forward + backward and `fwd` is the
forward. Speedup is previous / new latency; above 1.000x the new version
is faster. Rows whose program is unchanged on both sides are not listed.
Both versions are compiled with CUDA 13.4 (previous Cake: the shipped
FlashInfer build of #6939, nvcc 13.4; new Cake: NVRTC 13.4). The host
runs PyTorch 2.14.1+cu130, the same on both boards.

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 512 | 256 | bwd | 5.57 | 4.99 | 1.115x |
| 512 | 256 | step | 7.68 | 6.94 | 1.106x |
| 512 | 1024 | bwd | 6.37 | 5.06 | 1.259x |
| 512 | 1024 | step | 8.70 | 7.36 | 1.183x |
| 512 | 4096 | bwd | 8.06 | 7.55 | 1.068x |
| 512 | 4096 | step | 10.88 | 10.30 | 1.056x |
| 512 | 14928 | bwd | 13.98 | 12.67 | 1.104x |
| 512 | 14928 | step | 20.61 | 19.58 | 1.052x |
| 512 | 15288 | bwd | 14.11 | 13.31 | 1.060x |
| 512 | 15288 | step | 20.96 | 20.16 | 1.040x |
| 512 | 15566 | bwd | 14.30 | 12.90 | 1.109x |
| 512 | 15566 | step | 21.12 | 20.03 | 1.054x |
| 512 | 15590 | bwd | 14.30 | 12.87 | 1.112x |
| 512 | 15590 | step | 21.15 | 19.97 | 1.059x |
| 512 | 16114 | bwd | 14.40 | 13.02 | 1.106x |
| 512 | 16114 | step | 21.47 | 20.42 | 1.052x |
| 512 | 16132 | bwd | 14.40 | 13.02 | 1.106x |
| 512 | 16132 | step | 21.38 | 20.22 | 1.057x |
| 512 | 16164 | bwd | 14.40 | 12.99 | 1.108x |
| 512 | 16164 | step | 21.44 | 20.26 | 1.058x |
| 512 | 16263 | bwd | 14.40 | 13.02 | 1.106x |
| 512 | 16263 | step | 21.44 | 20.22 | 1.060x |
| 512 | 32768 | bwd | 22.98 | 20.90 | 1.100x |
| 512 | 32768 | step | 35.14 | 33.50 | 1.049x |
| 512 | 65536 | bwd | 38.82 | 36.13 | 1.074x |
| 512 | 65536 | step | 60.58 | 58.14 | 1.042x |
| 2048 | 256 | bwd | 6.34 | 5.82 | 1.088x |
| 2048 | 256 | step | 8.61 | 8.10 | 1.063x |
| 2048 | 1024 | bwd | 9.15 | 7.74 | 1.182x |
| 2048 | 1024 | step | 12.00 | 10.62 | 1.130x |
| 2048 | 4096 | bwd | 15.42 | 13.12 | 1.176x |
| 2048 | 4096 | step | 23.04 | 20.42 | 1.129x |
| 2048 | 14928 | bwd | 37.86 | 33.98 | 1.114x |
| 2048 | 14928 | step | 55.68 | 52.64 | 1.058x |
| 2048 | 15288 | bwd | 39.17 | 35.20 | 1.113x |
| 2048 | 15288 | step | 56.93 | 54.69 | 1.041x |
| 2048 | 15566 | bwd | 39.68 | 35.30 | 1.124x |
| 2048 | 15566 | step | 58.30 | 55.30 | 1.054x |
| 2048 | 15590 | bwd | 39.55 | 35.17 | 1.125x |
| 2048 | 15590 | step | 58.37 | 55.26 | 1.056x |
| 2048 | 16114 | bwd | 40.64 | 36.03 | 1.128x |
| 2048 | 16114 | step | 60.19 | 56.74 | 1.061x |
| 2048 | 16132 | bwd | 40.58 | 36.19 | 1.121x |
| 2048 | 16132 | step | 60.06 | 56.51 | 1.063x |
| 2048 | 16164 | bwd | 40.35 | 36.32 | 1.111x |
| 2048 | 16164 | step | 59.78 | 56.67 | 1.055x |
| 2048 | 16263 | bwd | 40.61 | 36.22 | 1.121x |
| 2048 | 16263 | step | 60.35 | 56.86 | 1.061x |
| 2048 | 32768 | bwd | 74.78 | 66.05 | 1.132x |
| 2048 | 32768 | step | 114.02 | 105.89 | 1.077x |
| 2048 | 65536 | bwd | 140.45 | 124.26 | 1.130x |
| 2048 | 65536 | step | 217.44 | 201.54 | 1.079x |
| 6144 | 256 | bwd | 8.38 | 7.71 | 1.087x |
| 6144 | 256 | step | 11.30 | 10.82 | 1.044x |
| 6144 | 1024 | bwd | 13.79 | 11.81 | 1.168x |
| 6144 | 1024 | step | 19.81 | 17.86 | 1.109x |
| 6144 | 4096 | bwd | 31.10 | 30.11 | 1.033x |
| 6144 | 4096 | step | 46.34 | 43.65 | 1.062x |
| 6144 | 14928 | bwd | 92.16 | 88.38 | 1.043x |
| 6144 | 14928 | step | 145.54 | 142.34 | 1.022x |
| 6144 | 15288 | bwd | 95.81 | 91.52 | 1.047x |
| 6144 | 15288 | step | 149.82 | 146.24 | 1.025x |
| 6144 | 15566 | bwd | 97.06 | 92.61 | 1.048x |
| 6144 | 15566 | step | 152.67 | 148.03 | 1.031x |
| 6144 | 15590 | bwd | 96.99 | 93.02 | 1.043x |
| 6144 | 15590 | step | 152.78 | 148.74 | 1.027x |
| 6144 | 16114 | bwd | 98.56 | 96.32 | 1.023x |
| 6144 | 16114 | step | 156.06 | 153.95 | 1.014x |
| 6144 | 16132 | bwd | 98.82 | 95.58 | 1.034x |
| 6144 | 16132 | step | 156.51 | 153.34 | 1.021x |
| 6144 | 16164 | bwd | 98.56 | 95.71 | 1.030x |
| 6144 | 16164 | step | 156.03 | 153.41 | 1.017x |
| 6144 | 16263 | bwd | 98.88 | 96.13 | 1.029x |
| 6144 | 16263 | step | 156.74 | 154.05 | 1.017x |

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 512 | 256 | bwd | 5.86 | 5.09 | 1.151x |
| 512 | 256 | step | 8.06 | 7.17 | 1.125x |
| 512 | 1024 | bwd | 6.66 | 5.47 | 1.216x |
| 512 | 1024 | step | 8.93 | 7.71 | 1.158x |
| 512 | 4096 | bwd | 8.48 | 8.06 | 1.052x |
| 512 | 4096 | step | 11.55 | 11.10 | 1.040x |
| 512 | 14928 | bwd | 14.49 | 13.34 | 1.086x |
| 512 | 14928 | step | 21.54 | 20.03 | 1.075x |
| 512 | 15288 | bwd | 14.62 | 13.57 | 1.078x |
| 512 | 15288 | step | 21.76 | 20.32 | 1.071x |
| 512 | 15566 | bwd | 14.62 | 13.63 | 1.073x |
| 512 | 15566 | step | 21.66 | 20.35 | 1.064x |
| 512 | 15590 | bwd | 14.66 | 13.60 | 1.078x |
| 512 | 15590 | step | 21.79 | 20.35 | 1.071x |
| 512 | 16114 | bwd | 14.88 | 13.70 | 1.086x |
| 512 | 16114 | step | 22.11 | 20.67 | 1.070x |
| 512 | 16132 | bwd | 14.88 | 13.76 | 1.081x |
| 512 | 16132 | step | 22.27 | 20.96 | 1.063x |
| 512 | 16164 | bwd | 14.91 | 13.73 | 1.086x |
| 512 | 16164 | step | 22.11 | 20.70 | 1.068x |
| 512 | 16263 | bwd | 14.91 | 13.73 | 1.086x |
| 512 | 16263 | step | 22.30 | 21.02 | 1.061x |
| 512 | 32768 | bwd | 23.68 | 22.40 | 1.057x |
| 512 | 32768 | step | 36.38 | 34.59 | 1.052x |
| 512 | 65536 | bwd | 40.58 | 38.18 | 1.063x |
| 512 | 65536 | step | 63.55 | 61.31 | 1.037x |
| 2048 | 256 | bwd | 6.72 | 5.98 | 1.123x |
| 2048 | 256 | step | 9.09 | 8.38 | 1.084x |
| 2048 | 1024 | bwd | 9.41 | 7.87 | 1.195x |
| 2048 | 1024 | step | 12.74 | 11.10 | 1.147x |
| 2048 | 4096 | bwd | 15.84 | 13.44 | 1.179x |
| 2048 | 4096 | step | 24.06 | 21.34 | 1.127x |
| 2048 | 14928 | bwd | 39.49 | 34.88 | 1.132x |
| 2048 | 14928 | step | 58.37 | 54.43 | 1.072x |
| 2048 | 15288 | bwd | 40.06 | 35.65 | 1.124x |
| 2048 | 15288 | step | 59.23 | 55.52 | 1.067x |
| 2048 | 15566 | bwd | 40.74 | 36.32 | 1.122x |
| 2048 | 15566 | step | 60.67 | 56.58 | 1.072x |
| 2048 | 15590 | bwd | 40.86 | 36.38 | 1.123x |
| 2048 | 15590 | step | 60.29 | 56.64 | 1.064x |
| 2048 | 16114 | bwd | 42.08 | 37.25 | 1.130x |
| 2048 | 16114 | step | 62.14 | 58.02 | 1.071x |
| 2048 | 16132 | bwd | 41.86 | 37.15 | 1.127x |
| 2048 | 16132 | step | 61.79 | 57.82 | 1.069x |
| 2048 | 16164 | bwd | 42.24 | 37.05 | 1.140x |
| 2048 | 16164 | step | 62.40 | 58.02 | 1.076x |
| 2048 | 16263 | bwd | 42.30 | 37.12 | 1.140x |
| 2048 | 16263 | step | 62.81 | 58.30 | 1.077x |
| 2048 | 32768 | bwd | 77.57 | 68.35 | 1.135x |
| 2048 | 32768 | step | 118.24 | 109.41 | 1.081x |
| 2048 | 65536 | bwd | 144.96 | 127.01 | 1.141x |
| 2048 | 65536 | step | 223.90 | 206.05 | 1.087x |
| 6144 | 256 | bwd | 8.58 | 7.90 | 1.085x |
| 6144 | 256 | step | 11.49 | 10.98 | 1.047x |
| 6144 | 1024 | fwd | 6.34 | 6.24 | 1.015x |
| 6144 | 1024 | bwd | 13.95 | 12.45 | 1.121x |
| 6144 | 1024 | step | 20.29 | 18.50 | 1.097x |
| 6144 | 4096 | bwd | 31.42 | 30.43 | 1.033x |
| 6144 | 4096 | step | 47.26 | 44.96 | 1.051x |
| 6144 | 14928 | bwd | 93.89 | 90.98 | 1.032x |
| 6144 | 14928 | step | 148.64 | 146.56 | 1.014x |
| 6144 | 15288 | bwd | 96.19 | 93.50 | 1.029x |
| 6144 | 15288 | step | 152.67 | 150.66 | 1.013x |
| 6144 | 15566 | bwd | 97.86 | 94.14 | 1.039x |
| 6144 | 15566 | step | 154.91 | 152.00 | 1.019x |
| 6144 | 15590 | bwd | 98.46 | 95.01 | 1.036x |
| 6144 | 15590 | step | 155.39 | 153.09 | 1.015x |
| 6144 | 16114 | bwd | 101.28 | 96.73 | 1.047x |
| 6144 | 16114 | step | 159.84 | 156.25 | 1.023x |
| 6144 | 16132 | bwd | 100.86 | 96.67 | 1.043x |
| 6144 | 16132 | step | 159.77 | 156.35 | 1.022x |
| 6144 | 16164 | bwd | 101.25 | 98.05 | 1.033x |
| 6144 | 16164 | step | 160.57 | 157.73 | 1.018x |
| 6144 | 16263 | bwd | 101.50 | 98.96 | 1.026x |
| 6144 | 16263 | step | 160.96 | 158.75 | 1.014x |

Cake also ships the residual-fused forward and backward and the H=1536 /
H=4096 programs (unchanged here); the family covers sm_100a, sm_103a and
sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded RMSNorm training support with additional GPU kernel variants
and more granular dispatch across input sizes and row ranges.
* Added bfloat16 training kernels for computing input and weight
gradients.
* **Improvements**
* Strengthened validation of tensor inputs and launch parameters before
GPU execution.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6a2f266](https://github.com/flashinfer-ai/flashinfer/commit/6a2f2661d24db6400466db51f482cd3c95faffaa)

- **作者**: eigen
- **时间**: 2026-10-22T07:46:53Z
- **提交信息**: perf(cake_nvfp4_svdquant): re-tuned kernels with per-architecture dispatch (#6986)

`flashinfer.mm_nvfp4_svdquant(..., backend="cake")` computes the NVFP4
SVDQuant GEMM `out = BF16(alpha * (deq(A) @ deq(B)^T + D @ L1^T) +
bias)`. In this kernel, A and B are NVFP4 (E2M1) with E4M3 block scales.
The low-rank D / L1, the bias and the output are BF16, and accumulation
is FP32. Its Cake backend has one data-type / layout variant, with two
fused forms (with and without the fused bias), across LoRA ranks 32 / 64
/ 96 / 128. That variant ships for sm_100a and sm_103a as the vendorable
package `flashinfer/cake_nvfp4_svdquant_gemm_backend`. This PR is the
second tuning round of the same variant. It replaces the package's
kernels with re-tuned programs, 34 in place of the 15 shipped before. It
also adds per-architecture dispatch, so for a given shape the package
may run a different program on sm_100a than on sm_103a. The public API
and semantics are unchanged. All latencies are CUPTI kernel-active
medians, with L2 cleared before every launch. "Previous Cake" is
`backend="cake"` on main at this PR's base (the package merged in
#6878). It was measured in the same session as this PR, on the same GPU.

**NVIDIA GB200 (sm_100a), CUDA 13.4**

| M | N | K | rank | bias | previous Cake (µs) | this PR (µs) | speedup
vs previous Cake |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 129 | 3072 | 3072 | 32 | 1 | 6.34 | 5.95 | 1.065 |
| 129 | 3072 | 3072 | 32 | 0 | 6.24 | 5.89 | 1.060 |
| 129 | 3072 | 3072 | 64 | 1 | 6.40 | 6.05 | 1.058 |
| 129 | 3072 | 3072 | 96 | 1 | 6.50 | 6.14 | 1.057 |
| 129 | 3072 | 3072 | 128 | 1 | 6.59 | 6.21 | 1.062 |
| 129 | 3072 | 3072 | 128 | 0 | 6.50 | 6.14 | 1.057 |
| 129 | 3072 | 12288 | 32 | 0 | 13.18 | 12.90 | 1.022 |
| 129 | 3072 | 12288 | 32 | 1 | 13.28 | 12.93 | 1.027 |
| 129 | 3072 | 12288 | 128 | 0 | 13.41 | 13.06 | 1.027 |
| 129 | 3072 | 12288 | 128 | 1 | 13.50 | 13.09 | 1.032 |
| 6912 | 3072 | 3072 | 32 | 1 | 29.95 | 28.80 | 1.040 |
| 6912 | 3072 | 3072 | 64 | 1 | 30.14 | 29.12 | 1.035 |
| 6912 | 3072 | 3072 | 96 | 1 | 31.78 | 31.04 | 1.024 |
| 6912 | 3072 | 3072 | 128 | 1 | 32.38 | 31.25 | 1.036 |
| 6912 | 3072 | 12288 | 32 | 1 | 97.89 | 96.96 | 1.010 |
| 6912 | 3072 | 12288 | 128 | 1 | 100.37 | 99.28 | 1.011 |
| 4096 | 3072 | 3072 | 32 | 1 | 19.87 | 19.63 | 1.012 |
| 4096 | 3072 | 12288 | 32 | 1 | 62.48 | 62.18 | 1.005 |
| 4096 | 12288 | 3072 | 32 | 1 | 65.44 | 63.17 | 1.036 |
| 6889 | 3072 | 3072 | 32 | 1 | 29.73 | 28.38 | 1.047 |
| 6889 | 3072 | 12288 | 32 | 1 | 97.89 | 96.91 | 1.010 |
| 6889 | 12288 | 3072 | 32 | 1 | 107.73 | 105.33 | 1.023 |
| 9216 | 3072 | 3072 | 32 | 1 | 35.49 | 35.58 | 0.997 ‡ |
| 9216 | 3072 | 12288 | 32 | 1 | 122.54 | 121.73 | 1.007 |
| 9216 | 12288 | 3072 | 32 | 1 | 136.42 | 133.92 | 1.019 |
| 16384 | 3072 | 3072 | 32 | 1 | 65.54 | 64.59 | 1.015 |
| 16384 | 3072 | 12288 | 32 | 1 | 206.93 | 205.90 | 1.005 |
| 16384 | 12288 | 3072 | 32 | 1 | 231.28 | 230.16 | 1.005 ‡ |

‡ This shape ships the previous Cake kernel unchanged on this GPU; its
ratio is the same-kernel control reading of the session.

**NVIDIA GB300 (sm_103a), CUDA 13.4**

| M | N | K | rank | bias | previous Cake (µs) | this PR (µs) | speedup
vs previous Cake |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 129 | 3072 | 3072 | 32 | 1 | 6.02 | 5.70 | 1.056 |
| 129 | 3072 | 3072 | 32 | 0 | 5.92 | 5.63 | 1.051 |
| 129 | 3072 | 3072 | 64 | 1 | 6.08 | 5.76 | 1.056 |
| 129 | 3072 | 3072 | 96 | 1 | 6.18 | 5.79 | 1.066 |
| 129 | 3072 | 3072 | 128 | 1 | 6.34 | 5.92 | 1.070 |
| 129 | 3072 | 3072 | 128 | 0 | 6.27 | 5.86 | 1.071 |
| 129 | 3072 | 12288 | 32 | 0 | 12.74 | 11.84 | 1.076 |
| 129 | 3072 | 12288 | 32 | 1 | 12.80 | 11.90 | 1.075 |
| 129 | 3072 | 12288 | 128 | 0 | 12.96 | 12.03 | 1.077 |
| 129 | 3072 | 12288 | 128 | 1 | 13.06 | 12.06 | 1.082 |
| 6912 | 3072 | 3072 | 32 | 1 | 27.33 | 26.18 | 1.044 |
| 6912 | 3072 | 3072 | 64 | 1 | 27.41 | 26.37 | 1.039 |
| 6912 | 3072 | 3072 | 96 | 1 | 28.91 | 27.94 | 1.035 |
| 6912 | 3072 | 3072 | 128 | 1 | 29.22 | 28.26 | 1.034 |
| 6912 | 3072 | 12288 | 32 | 1 | 75.49 | 74.21 | 1.017 |
| 6912 | 3072 | 12288 | 128 | 1 | 77.22 | 76.16 | 1.014 |
| 4096 | 3072 | 3072 | 32 | 1 | 18.46 | 18.46 | 1.000 ‡ |
| 4096 | 3072 | 12288 | 32 | 1 | 50.14 | 49.57 | 1.012 |
| 4096 | 12288 | 3072 | 32 | 1 | 52.69 | 50.16 | 1.050 |
| 6889 | 3072 | 3072 | 32 | 1 | 27.17 | 25.74 | 1.055 |
| 6889 | 3072 | 12288 | 32 | 1 | 75.42 | 74.27 | 1.016 |
| 6889 | 12288 | 3072 | 32 | 1 | 82.59 | 79.00 | 1.045 |
| 9216 | 3072 | 3072 | 32 | 1 | 31.97 | 31.52 | 1.014 |
| 9216 | 3072 | 12288 | 32 | 1 | 93.79 | 92.62 | 1.013 |
| 9216 | 12288 | 3072 | 32 | 1 | 107.26 | 102.50 | 1.047 |
| 16384 | 3072 | 3072 | 32 | 1 | 51.94 | 49.42 | 1.051 |
| 16384 | 3072 | 12288 | 32 | 1 | 161.68 | 159.60 | 1.013 |
| 16384 | 12288 | 3072 | 32 | 1 | 185.17 | 181.27 | 1.021 |

‡ This shape ships the previous Cake kernel unchanged on this GPU; its
ratio is the same-kernel control reading of the session.

Cake ships no other data-type, layout or fused-form variant of this
kernel beyond the one above (with and without the fused bias), and the
family ships on sm_100a and sm_103a only.

---------

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Avery Huang <averyh@oci-jhb-slurm-1-login-03.cm.cluster>

### [d8dc9d1](https://github.com/flashinfer-ai/flashinfer/commit/d8dc9d130a725218a3d0abc044954c6d45ceb3a3)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-22T07:40:48Z
- **提交信息**: perf(gemm): register the small-M MXFP8 kernels on SM107 (#6709)

## Problem

On SM107 (Rubin) `mm_mxfp8(backend="cute-dsl")` ran only the SM107
persistent kernel (#6136). That kernel's smallest tile covers 64 output
columns and it cannot split K, so decode-shaped calls (M <= 16 against a
6144-row FP8 weight) launched 48 CTAs on 208 SMs: each block streamed
its slice of the weight alone, and the kernel ran at a small fraction of
HBM bandwidth with most issue cycles idle. The untuned tactic scorer
could not see this because its wave term only counts whole waves (48 and
96 CTAs both read as "one wave").

SM100/SM103 never hit this: `_cute_dsl_mxfp8_runners` registers the warp
split-K kernel and the SM100 kernel's low-M policy (narrow swap-AB tiles
with cluster split-K) next to the main kernel. Rubin got neither.

## Fix

`_cute_dsl_mxfp8_runners_sm107` registers all three runners for the
`cute-dsl` backend on SM107 (the set is independent of M, as the
autotuner requires). Untuned order, from GR100 measurements:

- warp split-K first at M <= 8 and K <= 2048;
- the SM100 low-M path first at M <= 32 otherwise. Its untuned fallback
now splits K on SM107 (`_sm107_low_m_split_k`): the most slices that
keep >= 8 K blocks of 128 per slice and keep `ceil(N/128) * slices`
within one wave of SMs;
- the SM107 kernel first above M = 32 (unchanged behaviour).

On SM107 the SM100 runner is built with `low_m_only=True`, so it offers
only the narrow swap-AB tiles and split-K variants for M <= 32 and
nothing above; autotune time does not grow with that kernel's wide
tiles. Nothing in this PR is reachable on SM100/SM103: the new branches
are behind the SM107 runner set and the `low_m_only` flag, which only
that set passes.

## Measured on GR100 (untuned, vs the SM107 kernel alone, same node,
interleaved runs)

| M | N | K | untuned pick after this PR | speedup |
|---|---|---|---|---|
| 1 | 6144 | 1536 | warp split-K | 1.2x |
| 4 | 6144 | 4096 | low-M (128, 8) swap-AB, split-K 4 | 1.2x |
| 8 | 2304 | 6144 | low-M (128, 8) swap-AB, split-K 4 | 1.5x (1.8x
kernel-only) |
| 16 | 6144 | 1536 | low-M (128, 16) swap-AB, no split | 1.1x |
| 16 | 6144 | 6144 | low-M (128, 16) swap-AB, split-K 4 | 1.1x (1.3x
kernel-only) |
| > 32 | any | any | SM107 kernel (unchanged) | 1.0x |

A simpler variant that copied SM100's own rule (warp first at M <= 8
**or** K <= 2048) regressed M=4, K=4096 on Rubin; the K-aware rule above
is what the measurements support. Every run passed the benchmark
reference check, and each candidate kernel was also timed directly to
pick the order.

## Design notes (kept here rather than in code comments)

- **`_sm107_low_m_split_k`.** The low-M kernel runs with A and B
swapped, so it launches `ceil(N/128) * slices` CTAs. The rule takes the
most slices that still fit one wave of SMs and keep at least 8 K blocks
(128 FP8 elements each) per slice. Measured on GR100: N=6144, K=4096
gives 4 slices and 1.4x over the SM107 kernel; N=12288, K=6144 gives 2
(4 slices would be two waves and ran 1.4x slower than 2); K=1536 gives
1, because splitting a 12-block K only adds the cluster reduction.
- **Why the untuned fallback splits K on SM107 but not on SM100/103.**
An unsplit low-M tile launches `ceil(N/128)` CTAs, which at N=6144
leaves about three quarters of Rubin's SMs idle. The SM100/103 fallback
is left at one slice so their behaviour does not change.
- **`low_m_only`.** On SM107 the SM100 runner only has to cover M <= 32,
so it offers the narrow swap-AB tiles and their split-K variants there
and nothing above. Wide tiles stay the SM107 kernel's job, and autotune
time does not grow with the SM100 kernel's wide-tile list.
- **The runner set must not depend on M.** One autotune call covers
every M bucket, so the warp split-K runner is registered whenever its
non-M input checks pass, and it gates M per tactic in
`get_valid_tactics`. Only the untuned *order* of the set depends on the
current M and K.
- **Order.** Warp split-K first at M <= 8 and K <= 2048 (it loses at
longer K, where its per-slice K is too short); the low-M path first at M
<= 32 otherwise; the SM107 kernel first above M=32, unchanged.

## Tests

- `test_mm_mxfp8_cute_dsl_sm107` gains three small-M shapes (M=1 K=1024,
M=4 K=4096, M=16 K=1536) next to its existing ones. Below M=32 it
asserts the SM107 kernel does not launch untuned (a small-M runner ran
instead) while the result still matches the bf16 reference; above M=32
it asserts the SM107 kernel is the untuned pick, as before. Autotuned
cases check that the SM107 kernel was profiled at every shape. The
untuned cases clear the autotuner cache first: autotuning profiles every
M bucket up to the current size, so an autotuned case at M=4096 earlier
in the process leaves a cached winner for the small M buckets at the
same N and K.
- `tests/gemm/test_mm_mxfp8.py -k "cute_dsl_low_m or cute_dsl_sm107 or
stale_split_k or narrow_tiles or pdl_producer or small_m"` on GR100 with
the library change: 43 passed, the single failure being the M=1 case
whose expectation this PR flips.

Related: #6551 tunes the SM107 kernel's untuned tactic for M > 512 and
is orthogonal (no change at M <= 512 by design). #6615 also touches the
SM100 runner's `get_valid_tactics`; whichever lands second needs a
trivial rebase.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated MXFP8 matrix multiplication execution choices for SM107
hardware across small and larger matrix shapes.
* Split-K and warp split-K options are selected based on matrix
dimensions and hardware support, with small-M workloads using an
appropriate runner.
* **Tests**
* Expanded coverage for small matrix shapes and checked runner selection
in tuned and untuned execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [82914ab](https://github.com/flashinfer-ai/flashinfer/commit/82914ab3d89d4e3255fdae2fc6f01ea6eebefd11)

- **作者**: eigen
- **时间**: 2026-10-22T07:16:13Z
- **提交信息**: perf(cake_kimi_k3_attn_res): native K = 6 program for the (M 192, K 6) cell on SM100 at 148 SMs (#6984)

This PR changes one route of the Cake Kimi-K3 AttnRes operator,
`flashinfer.experimental.cake_kimi_k3_attn_res`. It is exposed as
`flashinfer.kimi_k3_attn_res.prepare_kimi_k3_attn_res` and
`kimi_k3_attn_res`. The operator runs residual add, an optional snapshot
write, K+1 candidate scoring, softmax, mix and output RMSNorm in one
launch. It takes BF16 inputs with hidden size 7168 and K in [0, 8]. It
writes BF16 output with FP32 accumulation. It has dense and
snapshot-write forms, and PDL (programmatic dependent launch) is a
launch parameter.

Until now, the native K = 6 program was built only for SM103. This PR
also builds it for SM100. On SM100 at 148 SMs, the cell M 192, K 6 now
routes to it. That cell used to run the persistent K = 6 program, which
still ships for its other cells. Every other program is unchanged byte
for byte. SM103 routes at 148 and 152 SMs are also unchanged. On SM103
the same change measured below 1 %, so it was not adopted there. The
baseline is the previous Cake version of this operator, merged in PR
#6980. Times are CUPTI kernel times with cold L2, from paired
interleaved ABBA sampling with ≥ 3 groups × ≥ 300 samples per arm, the
same protocol as the tables in PR #6980.

NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4.92, torch
2.14.1+cu130.

| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 192, K 6 (dense) | 10.912 | 10.720 | 1.0188 | 10.912 | 10.720 |
1.0189 |

The table has one row because the other 290 shapes of the shape list run
the same programs as the previous version on all three GPUs (B200, B300,
GB300), byte for byte, so their timings are the ones listed in PR #6980.

Cake ships no other data types or layouts for this operator, since the
dense and snapshot-write forms are the whole family, and 135 programs
(164 libraries: 79 sm_100a, 85 sm_103a) cover B200 (sm_100a, 148 SMs),
B300 (sm_103a, 148 SMs) and GB300 (sm_103a, 152 SMs).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added native attention-residual processing for the K=6, M=192 workload
on compatible SM100a GPUs. This expands hardware-specific coverage for
applications using this configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4685
- **最后更新**: 2026-10-23T00:40:27Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: William Lin, Aryan Kumar

## AI分析总结

## FastVideo 昨日提交分析

### 1. 主要更新类型

两个提交均属于 **基础设施（Infra）与 CI/CD 优化**，而非直接的功能新增或性能优化。具体来说：

- 提交 #2007：CI 流水线配置调整，将单 GPU CI 任务迁移到 DGX Spark 运行器上执行，每周在 main 分支上运行完整测试套件。
- 提交 #1986：修复 DGX Spark (GB10) 平台的 Docker 镜像，解决 flashinfer 库导入失败、sm_121a 架构内核不兼容以及输出与原生环境不一致等问题。

### 2. 关键变更点及与项目方向的关系

**Docker 镜像修复（#1986）** 是基础性工作。DGX Spark 基于 NVIDIA GB10 芯片，采用 Blackwell 架构（sm_121a），是一个较新的硬件平台。此前该镜像存在 flashinfer 无法导入和内核编译不匹配的问题，意味着 FastVideo 的推理/训练功能在该硬件上无法正常运行。此修复使项目首次能够在 DGX Spark 上实现与原生环境一致的输出，为后续在该平台上的性能调优和部署铺平了道路。

**CI 迁移（#2007）** 则在此基础上进一步将单 GPU 的 CI 测试迁移到 DGX Spark 运行器，并将完整的全量测试套件安排为每周在 main 分支上运行。这一策略在保证代码质量监控的同时，也有效平衡了 CI 资源消耗和测试覆盖度。

### 3. 对项目的影响和潜在意义

- **扩大硬件生态覆盖**：DGX Spark 是 NVIDIA 面向桌面级 AI 开发的新型平台，支持该平台意味着 FastVideo 的目标用户群从服务器级 GPU 扩展到了个人开发者和小型团队，降低了使用门槛。
- **CI 基础设施的现代化**：将 CI 部署到更先进、更高效的硬件上，有助于未来加速测试反馈循环，并为项目的持续集成质量提供更好的保障。
- **社区贡献导向**：两个提交均有外部协作者参与（Co-authored-by 标注），体现了社区对平台适配工作的积极参与，这对开源项目的长期健康至关重要。

### 4. 值得关注的技术点

- **flashinfer 在 GB10 上的兼容性修复**：flashinfer 是 Flash Attention 系列推理优化的核心依赖，其在新架构上的正常导入和运行对视频生成模型的推理效率至关重要。
- **sm_121a 内核支持**：这涉及 GPU 计算能力（Compute Capability）层面的适配，确保自定义 CUDA 内核能够在 Blackwell 架构上正确编译和执行。
- **CI 分层策略**：单 GPU 快速测试在日常 CI 中运行，全量测试每周运行一次，这是一种在覆盖率和资源效率之间的务实折中。

### 5. 对项目整体发展的影响

从 README 可以看出，FastVideo 是一个面向快速视频生成的高性能框架，项目持续关注推理效率和部署可及性。昨日的两个提交共同指向一个清晰的战略方向：**将 FastVideo 的支持范围从传统数据中心 GPU 扩展到新一代边缘/桌面 AI 硬件（DGX Spark / GB10）**。

虽然这两个提交本身不涉及视频生成算法层面的创新，但它们是项目生态扩展的关键基础工作。硬件适配的完善将直接吸引使用新型 NVIDIA 平台的开发者群体，扩大用户基数，同时也能借助 DGX Spark 的便携性探索更多实时视频生成的应用场景。从开源项目运营的角度看，这类基础设施提交反映了项目维护者对工程质量和平台兼容性的重视，是项目走向成熟的标志之一。

## 详细提交记录

### [7c2b447](https://github.com/hao-ai-lab/FastVideo/commit/7c2b447264016af4ddf0f08db194b27c9a2613cc)

- **作者**: Aryan Kumar
- **时间**: 2026-10-22T20:44:55Z
- **提交信息**: [ci] Run single-GPU CI lanes on a DGX Spark runner; weekly full suite on main (#2007)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [e136c2b](https://github.com/hao-ai-lab/FastVideo/commit/e136c2b7f8141e12668067c35f4d5347842512e5)

- **作者**: William Lin
- **时间**: 2026-10-22T18:59:31Z
- **提交信息**: [infra]: fix the DGX Spark (GB10) Docker image: importable flashinfer, sm_121a kernels, native-matching output (#1986)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34778
- **最后更新**: 2026-10-22T19:48:19Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, Linoy Tsaban

## AI分析总结

# huggingface/diffusers 昨日提交分析（第1/1批）

---

## 1. 主要更新类型

- **功能新增**：引入 fibo-2 LoRA 训练与加载支持
- **CI/基础设施修复**：修复编译 CI 及注意力后端名称分发问题

---

## 2. 关键变更点及其与项目整体方向的关系

- **fibo-2 LoRA 训练脚本**（text-to-image + image editing）：diffusers 作为 HuggingFace 生态中扩散模型的核心库，持续为用户提供低资源微调方案。LoRA 是当前社区最受欢迎的轻量微调方法，新增对 fibo-2 架构的 LoRA 支持，使社区能够在不完整重训模型的前提下，针对文生图和图像编辑两个典型场景进行定制化微调。这与 diffusers 一贯"让扩散模型易于使用和微调"的定位高度一致。

- **编译 CI 修复与注意力后端分发修正**：注意力后端（AttentionBackend）的名称分发是 diffusers 内部抽象不同加速实现（如 SDPA、xFormers、Flash Attention 等）的关键机制。修复该分发逻辑并配套 CI 验证，说明团队在多后端支持上做了持续打磨，确保不同编译环境下的稳定性和一致性。

---

## 3. 对项目的影响和潜在意义

- **降低微调门槛**：fibo-2 LoRA 脚本为用户提供了开箱即用的训练范例，尤其覆盖了图像编辑这一日益增长的需求方向，有助于扩大用户群体并鼓励社区贡献更多微调方案。
- **提升 CI 可靠性**：编译 CI 的修复意味着提交前的自动化检测更加完善，减少了因后端名称分发错误导致的回归风险，对保证项目长期稳定性有直接帮助。
- **推动新模型架构落地**：fibo-2 相对较新，将其纳入 diffusers 的 LoRA 工作流，说明项目在快速跟进前沿模型架构，保持生态位竞争力。

---

## 4. 值得关注的技术点

- **LoRA 与图像编辑的结合**：传统 LoRA 微调多聚焦于文生图，图像编辑任务中的 LoRA 训练在数据构造、条件注入方式上有所不同，该脚本的实现细节值得深入研究。
- **注意力后端名称分发机制**：diffusers 通过统一的 AttentionBackend 抽象层适配多种计算后端，其分发逻辑的健壮性直接影响跨平台（CPU/GPU/TPU）兼容性。
- **CI 中的标记跳过（marker skip）**：在 CI 中使用标记跳过某些编译测试，说明部分测试环境或依赖尚不稳定，后续可能需要补齐覆盖。

---

## 5. 基于 README 项目背景的影响总结

README 明确该项目为 HuggingFace 官方的 Apache 2.0 开源扩散模型库，核心使命是**让扩散模型的训练、微调和推理尽可能简单高效**。昨日的两个提交分别从"功能层"和"基础设施层"呼应了这一使命：fibo-2 LoRA 脚本直接扩展了库的微调能力版图，让更多用户能以低成本方式定制新架构模型；而编译 CI 和后端分发的修复则从质量保障角度确保了这种扩展建立在稳固的基础之上。两者结合，反映出 diffusers 在快速迭代新功能的同时，也不忽视工程质量，这对于一个社区驱动的开源项目而言是健康发展的关键信号。

## 详细提交记录

### [48cdbae](https://github.com/huggingface/diffusers/commit/48cdbaef5ee3d718aaee392b44f2099ae511c4a5)

- **作者**: Linoy Tsaban
- **时间**: 2026-10-22T13:16:58Z
- **提交信息**: add fibo-2 LoRA training and loading (#15084)

add fibo-2 LoRA training scripts (text-to-image + image editing)

### [73faca3](https://github.com/huggingface/diffusers/commit/73faca368c0da77645ea58836aa8780d2d8c5353)

- **作者**: Sayak Paul
- **时间**: 2026-10-22T10:24:08Z
- **提交信息**: [ci] fix compilation CI. (#15092)

* fix compilation CI.

* fix attentionbackend name dispatch.

* skip with a marker.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
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


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13291
- **最后更新**: 2026-10-22T21:24:48Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

## 提交分析：DiffSynth-Studio 昨日提交（d188f01）

### 1. 主要更新类型
**依赖精简/工程重构**。该提交的核心是减少项目的依赖项（reduce dependencies），不属于功能新增或Bug修复，而是一次面向工程维护的优化型改动。

### 2. 关键变更点与项目整体方向的关系
- **变更点**：梳理并移除了冗余或可选的第三方依赖包，可能通过内置替代实现、延迟导入（lazy import）或将可选功能改为 extras 安装的方式来实现。
- **与项目方向的关系**：DiffSynth-Studio 是一个扩散模型（DiffSynth）工作室工具库，覆盖视频/图像生成与训练，这类项目通常依赖 PyTorch、Diffusers、Transformers 等庞大的生态，依赖极易膨胀。精简依赖与该项目"提供开箱即用的生成式AI工具"的定位一致——依赖越少，用户安装门槛越低，冲突风险越小，也更利于 CI 与 PyPI 发布（README 中展示了 PyPI 徽章，说明该项目以分发包形式面向社区）。

### 3. 对项目的影响和潜在意义
- **安装体验改善**：用户从 PyPI 安装 DiffSynth 时下载体积更小、依赖解析更快，减少了版本冲突（如不同库要求不同版本 transformers/numpy 的经典问题）。
- **可维护性提升**：更少的依赖意味着升级适配面更窄，维护者跟进上游 API 变更的成本降低。
- **潜在风险**：若被移除的依赖对应的底层能力（如某些视频编码、特定模型后端）被静默移除，可能导致部分边缘功能不可用；需要关注是否有 feature gating（以 extras 形式保留可选能力）而非直接删除。

### 4. 值得关注的技术点
- **可选依赖的处理策略**：是通过 `pip install DiffSynth[video]` 之类的 extras 分组，还是完全移除能力？这决定了功能覆盖面。
- **导入方式的调整**：常见做法是把重量级依赖（如 decord、xformers、flash-attn）改为按需导入，避免核心路径的硬依赖，值得查看具体 diff 中的 import 变化。
- **对测试/CI 的影响**：依赖减少通常伴随 CI 矩阵调整，可观察其 workflow 是否同步精简。

### 5. 结合项目背景对发展的影响
从 README 看，DiffSynth-Studio 是 ModelScope 生态中活跃的扩散模型工具集，已被 Trendshift 收录、持续发布 PyPI 版本，处于快速迭代期。在这一阶段做依赖精简，说明项目正从"功能快速堆叠"转向**工程质量与分发成熟度**的打磨，为更广泛的用户群（研究者、开发者）降低使用门槛。这类看似不起眼的维护提交，往往为后续的功能扩展打下更稳健的基础——依赖面收窄后，引入新模型支持时的兼容性成本会显著下降。总体而言，这是项目走向稳定、易用的积极信号，短期内对用户透明，长期利好生态推广。

## 详细提交记录

### [d188f01](https://github.com/modelscope/DiffSynth-Studio/commit/d188f01d09013688dea27cc28f2e8dc0953c2543)

- **作者**: Zhongjie Duan
- **时间**: 2026-10-22T09:30:46Z
- **提交信息**: reduce dependencies (#1783)

* reduce dependencies

* reduce dependencies

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37623
- **最后更新**: 2026-10-23T00:36:07Z

## 提交统计

- **昨日提交总数**: 55
- **提交者数量**: 37
- **主要提交者**: Jayden Yu, Mick, Jooman

## AI分析总结

# SGLang 昨日提交分析（55条）

## 1. 主要更新类型

- **性能优化**（~20条）：占比最高，集中在 dsv4/dsv41、diffusion、MoE、Muse Spark 等内核级优化
- **Bug修复**（~22条）：覆盖 HiCache、logits精度、NCCL图捕获、AMD/NPU/Intel 平台适配等
- **功能新增**（~6条）：LoRA引擎、投机采样种子化、KVShard分页支持、wan-animate模型等
- **重构与CI**（~7条）：radix-tree插桩重构、CI测试入口完善与shard时长控制

## 2. 关键变更点与项目方向的关系

- **DeepSeek V4.1 深度优化**：多条提交（#45903、#45901、#45900、#45880、#45783、#45726）围绕 dsv4 prefill 图展开——融合 MXFP8 producer、直写 MegaAttention 输出缓冲、减少残差张量存活、精简 indexer。这表明项目正对旗舰模型做端到端 prefill 流水线的极致调优，契合"Fast inference"的核心目标。
- **扩散模型生态扩张**：FLUX、FLUX3、Wan VAE 等多条 fusion 提交（SwiGLU+FP8、QKV norm+RoPE、DupUp3D shortcut add）+ wan-animate-2 支持，显示 SGLang 正将推理加速能力系统性扩展到多模态/视频生成领域。
- **分层缓存（HiCache）成熟化**：修复 stale host KV 竞态、Mooncake 分配器空指针快失败、备份准入管道化、radix-tree 可恢复 OVERLAP 阶段——层次化 KV 缓存正在从"可用"走向"生产可靠"。
- **硬件平台矩阵加宽**：AMD（gfx1250 fp8、MI300阈值重校准、RCCL确定性限制）、NPU（pcp-v2适配、precise-test）、Intel（FLUX copy offload）、NVIDIA SM107 兼容（因 CUTLASS 滞后临时降级构建），体现多后端战略的持续投入。

## 3. 对项目的影响和潜在意义

- dsv4 prefill 融合链 + MXFP8/bf16 精度选择将直接提升 DeepSeek 系列模型的吞吐与延迟表现，强化 SGLang 在国产大模型推理服务中的竞争力。
- LoRA 引擎（dense + MoE）规划化改造为多租户/适配器场景铺路；投机采样草稿种子化（#33395，长期 PR）带来确定性推理，对可复现评测和调试价值显著。
- KVShard 分页 DSA 缓存支持（#44280）与 engram host-table 顺序读取（#45879）预示稀疏注意力缓存正成为一等公民。
- CI 侧：30分钟 shard 目标、Muse Spark router 测试入口补齐、统一 radix cache 测试态——测试基建在追赶功能扩张速度。

## 4. 值得关注的技术点

- **KDA（kernel-design-agents）工作流**：多条提交署名为 `kernel-design-agents`，涉及 CuTe DSL GEMV、BLOCK_M 调优、GB300 自定义 all-reduce——AI 代理参与内核开发的实验已在生产分支落地。
- **AI 协作常态化**：多个修复提交由 Claude Opus 协作完成，包括 1M context 版本参与 HiCache 竞态修复。
- **精度守恒式优化**：qknorm "two-per-warp, bit-identical"、logits 共享缓冲保留 lm_head 精度——强调数值等价的优化纪律。
- **CUDA 图与通信的边界治理**：捕获图含集合通信时禁用图缓冲注册（#43216），是 CUDA Graph + NCCL 组合的隐蔽坑位。

## 5. 对项目整体发展的影响

结合 README 定位（LLM 与多模态模型的快速推理引擎），本批提交呈现三条主线：其一，通过内核级融合（FP8/MXFP8/位级等价重排）持续压榨单卡与多卡推理性能，巩固"fast"标签；其二，扩散/视频模型支持从零散修复转为系统性加速，多模态推理正成为第二增长曲线；其三，HiCache、KVShard、投机采样确定性等基础设施的成熟，使项目从"推理加速器"向"生产级推理平台"演进。多硬件后端与 AI 代理内核开发的并行实验，则为长期生态扩展和技术组织模式提供了储备。综合来看，项目正处于性能纵深与场景横向同步扩张的高活跃期。

## 详细提交记录

### [77f90ad](https://github.com/sgl-project/sglang/commit/77f90ade9736170e4fb9cc5f61ef991a31d7942e)

- **作者**: HEJIAN SANG
- **时间**: 2026-10-22T23:57:49Z
- **提交信息**: [Fix] weight_checker: Make the checksum device-agnostic (#45918)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bb9e9d5](https://github.com/sgl-project/sglang/commit/bb9e9d5632e33fb10c7e6e4a026df749fca7017a)

- **作者**: Jayden Yu
- **时间**: 2026-10-22T23:49:39Z
- **提交信息**: [Perf] mlp: Fuse dense SwiGLU with block-FP8 quantization on decode (#45219)

Co-authored-by: Jayden Yu <jaydenyu@fb.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [5849ff5](https://github.com/sgl-project/sglang/commit/5849ff5337b5e865518c72f5bd45ce79d21a2604)

- **作者**: Chunan Zeng
- **时间**: 2026-10-22T23:42:00Z
- **提交信息**: [Fix] [NVIDIA] jit: Build sm_100f on CC 10.7 until the bundled CUTLASS supports SM107 (#45911)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8d47d51](https://github.com/sgl-project/sglang/commit/8d47d515e4d1b18580ac5539d60f64544a84078e)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-22T23:27:40Z
- **提交信息**: [CI] deepgemm: Remove obsolete ref_mhc preflight check (#45910)

### [035ed73](https://github.com/sgl-project/sglang/commit/035ed73b9d3aa90af6d32dad2de9637292738901)

- **作者**: Michael
- **时间**: 2026-10-22T23:19:34Z
- **提交信息**: [Fix] [AMD] kernels: Import the HIP launch helpers from jit.utils.hipcc in smallm_fp8_blockscale_gfx950 (#45676)

### [c394a90](https://github.com/sgl-project/sglang/commit/c394a90c2b4d82483ed908d2afbca1901d9d59d2)

- **作者**: Alex Nails
- **时间**: 2026-10-22T22:37:19Z
- **提交信息**: [Perf] gemma4: Capture single-step frozen-KV drafts (#45771)

### [f9b7225](https://github.com/sgl-project/sglang/commit/f9b7225f2e169b3a41d0087508fb607bd014e4fe)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-22T22:29:09Z
- **提交信息**: [Perf] dsv4: Use the fused MXFP8 producers in eager prefill (#45903)

### [9c0f6d6](https://github.com/sgl-project/sglang/commit/9c0f6d6a610531bd16ad3513572e55226450b244)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-22T21:56:08Z
- **提交信息**: [Perf] dsv4: Write the MegaAttention output straight into the prefill graph buffer (#45901)

### [818d793](https://github.com/sgl-project/sglang/commit/818d7932d7f7a8305d3c60d0c461d54fa50e1e26)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-22T21:55:49Z
- **提交信息**: [Perf] dsv4: Drop local references that keep residual-stream tensors alive through the prefill step (#45900)

### [3b0003d](https://github.com/sgl-project/sglang/commit/3b0003dac15f32b27cf247c5da555edf459a2e3f)

- **作者**: Jooman
- **时间**: 2026-10-22T21:46:51Z
- **提交信息**: [Fix] HiCache: stale host KV from write-through copies racing the in-flight forward (#42701)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Zhiqiang Xie <xiezhq@stanford.edu>

### [a904e4d](https://github.com/sgl-project/sglang/commit/a904e4d31a8a165bc7baede4798184afc39617b4)

- **作者**: Alison Shao
- **时间**: 2026-10-22T21:34:28Z
- **提交信息**: [Fix] ci: Reduce runner utilization scan overhead and bound API retries (#45873)

### [840a631](https://github.com/sgl-project/sglang/commit/840a6313c95735c46e55176b41ab263cfdc842c0)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-22T21:29:08Z
- **提交信息**: [Perf] dsv4: Score the V4.1 index logits in bf16 on SM100 (#45880)

### [25ad569](https://github.com/sgl-project/sglang/commit/25ad569ff93a43ce5c66cd94edbf75e2eb29b779)

- **作者**: Ajit Mistry
- **时间**: 2026-10-22T21:04:32Z
- **提交信息**: [Feat] speculative: Seed rejection-sampling draft proposals for deterministic inference (#33395)

Co-authored-by: Ajit Mistry <ajmistry@nvidia.com>
Co-authored-by: Ajit Mistry <ajmistry@amistry.nvidia.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [e5db41b](https://github.com/sgl-project/sglang/commit/e5db41b329ef371755c7769bb95fbc881fb953a4)

- **作者**: Alex
- **时间**: 2026-10-22T20:58:47Z
- **提交信息**: [Fix] nemotron_vl: Pad visual spans using processor offsets (#44581)

Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>

### [786cdfc](https://github.com/sgl-project/sglang/commit/786cdfc040be49f2b0dfbe59ca40745abd48cff2)

- **作者**: Andy Ye
- **时间**: 2026-10-22T20:56:19Z
- **提交信息**: [Fix] nccl: Disable graph buffer registration whenever a captured graph can hold a collective (#43216)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>

### [1399967](https://github.com/sgl-project/sglang/commit/13999673ef26f7e1ccd55f7b6e47e7fbd7199119)

- **作者**: Yanbin Jiang
- **时间**: 2026-10-22T20:40:56Z
- **提交信息**: [Feat] lora: Add plan-driven dense and MoE LoRA engines (#45892)

### [154e29c](https://github.com/sgl-project/sglang/commit/154e29c1ec7582d6eed287c58050060548cd2f41)

- **作者**: Shunkangz
- **时间**: 2026-10-22T20:33:04Z
- **提交信息**: [Perf] CP: QSA Context Parallel Optimization (#43792)

### [ba83415](https://github.com/sgl-project/sglang/commit/ba83415eea83616c3539d19dd3a36db02a7db326)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-22T20:13:43Z
- **提交信息**: [Perf] engram: Read host-table rows in address order on GPUs without host page tables (#45879)

### [bf0e193](https://github.com/sgl-project/sglang/commit/bf0e193bfd0049f7590808471ef5f18eb31cdedf)

- **作者**: metamergebot
- **时间**: 2026-10-22T20:12:37Z
- **提交信息**: [Refactor] radix-tree: Move insert overlap handling into a resumable OVERLAP phase (#45702)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [aae2145](https://github.com/sgl-project/sglang/commit/aae2145eb24ec3087961387cc2f0c908717e1d47)

- **作者**: metamergebot
- **时间**: 2026-10-22T20:11:33Z
- **提交信息**: [Feat] radix-tree: Report the last visited node and a shorter FULL device match in match results (#45703)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [357323e](https://github.com/sgl-project/sglang/commit/357323e912a64c0ade0910deabd0f29558ae815c)

- **作者**: metamergebot
- **时间**: 2026-10-22T20:10:18Z
- **提交信息**: [Refactor] hicache: Route buffer-mode backup admission keys and FULL transfers through pipeline hooks (#45701)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [4f96807](https://github.com/sgl-project/sglang/commit/4f96807ea85ae2c38f0e95cbe783b8d37af931fe)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-22T20:04:23Z
- **提交信息**: [CI] radix-cache: Build unified radix cache test states through production paths (#45334)

### [d67d1ae](https://github.com/sgl-project/sglang/commit/d67d1ae02c2c9f62757289e6453df29bc98082c7)

- **作者**: YAMY
- **时间**: 2026-10-22T19:46:27Z
- **提交信息**: [Fix] logits: Preserve lm_head precision with shared buffers (#45855)

### [0d6b283](https://github.com/sgl-project/sglang/commit/0d6b283d7e6ac79edc10b2ca788f309e972f527b)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-22T19:26:43Z
- **提交信息**: [Refactor] dsv4: Keep only the two-level V4.1 indexer in the prefill graph (#45783)

### [8d89168](https://github.com/sgl-project/sglang/commit/8d8916815b9f2717a34dac16190157189e54fb57)

- **作者**: WenhaoZhang
- **时间**: 2026-10-22T18:39:34Z
- **提交信息**: [Fix] ci: Add pytest entry point for Muse Spark router tests (#45843)

### [913e91e](https://github.com/sgl-project/sglang/commit/913e91ed51fd15c757b975024d8a55e076eba74d)

- **作者**: Zhangheng
- **时间**: 2026-10-22T16:45:41Z
- **提交信息**: [Fix] CI: add missing entry point to Muse Spark router test (#45845)

### [c80285c](https://github.com/sgl-project/sglang/commit/c80285ca9adc23946447128926c22e8e7dfb2b80)

- **作者**: Aarne Talman
- **时间**: 2026-10-22T16:31:25Z
- **提交信息**: [Fix] [AMD] deterministic: Refuse RCCL all-reduce in deterministic mode above TP2 (#43809)

Signed-off-by: Aarne Talman <aarne.talman@amd.com>

### [cc811ff](https://github.com/sgl-project/sglang/commit/cc811ff0c3d5e06b3d6ca10c0a0388bc720ab2c2)

- **作者**: Shunkangz
- **时间**: 2026-10-22T16:16:35Z
- **提交信息**: [Feat] KVShard: Add attention and indexer support for page-sharded DSA caches (#44280)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8cd3c49](https://github.com/sgl-project/sglang/commit/8cd3c494a3aa3ae56dfd76f51bab6912234914dc)

- **作者**: Shuwen Wang
- **时间**: 2026-10-22T14:36:32Z
- **提交信息**: [Fix] mem_cache: Skip linker L3 lookup on PD decode (#45538)

### [afd0d7b](https://github.com/sgl-project/sglang/commit/afd0d7b47b40448341036cea37294fcf3cb2aabd)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-22T13:30:45Z
- **提交信息**: [Fix] diffusion/flux: use true_cfg_scale as the FLUX CFG weight (#44260)

### [0f7d3a0](https://github.com/sgl-project/sglang/commit/0f7d3a045197f2a60e7f785fd28337067a28fdf7)

- **作者**: Mick
- **时间**: 2026-10-22T13:19:42Z
- **提交信息**: [CI] diffusion: target thirty-minute CI shards (#45761)

### [dcf0572](https://github.com/sgl-project/sglang/commit/dcf05724f72ea2bda1f08e7fbf6e17c8af1797e0)

- **作者**: Sun
- **时间**: 2026-10-22T13:18:39Z
- **提交信息**: [Perf] diffusion: accumulate chunked LoRA merges with addmm (#37620)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [698fa94](https://github.com/sgl-project/sglang/commit/698fa949ecd3f5662a87edcb4aefcb44884a2776)

- **作者**: trebladev
- **时间**: 2026-10-22T13:17:56Z
- **提交信息**: [Perf] diffusion: fuse FLUX3 SwiGLU with rowwise FP8 quantization (#42758)

### [6358361](https://github.com/sgl-project/sglang/commit/635836129b80dbabd97f43229abb5262077d75d0)

- **作者**: Song Bian
- **时间**: 2026-10-22T12:57:30Z
- **提交信息**: [Perf] [KDA] muse_spark: use BLOCK_M 240 for BF16 MegaMoE prefill shards (#45637)

Co-authored-by: kernel-design-agents <kernel-design-agents@users.noreply.github.com>

### [a9902f4](https://github.com/sgl-project/sglang/commit/a9902f47e392ad544a8a521bc4075190c57bf74a)

- **作者**: gjsheu
- **时间**: 2026-10-22T12:54:11Z
- **提交信息**: [Fix] [NPU] qwen: adapt pcp-v2 (#41564)

### [8514197](https://github.com/sgl-project/sglang/commit/851419717a14c29a52c06f22a158502510c337dc)

- **作者**: Song Bian
- **时间**: 2026-10-22T12:49:29Z
- **提交信息**: [Perf] [KDA] muse_spark: Run the one-token router GEMV on CuTe DSL (#45508)

Co-authored-by: kernel-design-agents <kernel-design-agents@users.noreply.github.com>

### [91fc46a](https://github.com/sgl-project/sglang/commit/91fc46a0179513dc562bdcc05814329c498dc976)

- **作者**: Trevor Morris
- **时间**: 2026-10-22T12:46:32Z
- **提交信息**: [Fix] [NVIDIA] docker: Disable torch 2.15 nccl2 in CUDA 13.4 container to fix EPLB rebalance crash (#45456)

### [0ec3fee](https://github.com/sgl-project/sglang/commit/0ec3fee429b685f791176f86fa12a4beab3c360f)

- **作者**: Song Bian
- **时间**: 2026-10-22T12:46:28Z
- **提交信息**: [Perf] [KDA] cookbook: enable custom all-reduce for GB300 BF16 Muse Spark (#45429)

Co-authored-by: kernel-design-agents <kernel-design-agents@users.noreply.github.com>

### [e43f612](https://github.com/sgl-project/sglang/commit/e43f6128a0d0bf98c8c73c42ba69773987b069fe)

- **作者**: Song Bian
- **时间**: 2026-10-22T12:38:35Z
- **提交信息**: [Fix] [KDA] cookbook: add MoE runner backend to Muse Spark BF16 recipes (#45422)

Co-authored-by: kernel-design-agents <kernel-design-agents@users.noreply.github.com>

### [f4ccfd4](https://github.com/sgl-project/sglang/commit/f4ccfd418347fe55d5b518a8c4cb97a72a749052)

- **作者**: Jzz1943
- **时间**: 2026-10-22T12:37:54Z
- **提交信息**: [Perf] moe: Add H200 block-FP8 Triton configurations (#45591)

### [178febe](https://github.com/sgl-project/sglang/commit/178febef5d8d2b418eb1f71f4d1fcc0e6e8f984e)

- **作者**: Monishver
- **时间**: 2026-10-22T12:34:16Z
- **提交信息**: [Perf] qknorm: run head_dim-128 rows two per warp with 16B lanes, bit-identical (#45214)

Signed-off-by: Monishver Chandrasekaran <monishverchandrasekaran@gmail.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [81841d6](https://github.com/sgl-project/sglang/commit/81841d6bdcf52182dc9eb8f583cbac44c9d7551f)

- **作者**: qiye
- **时间**: 2026-10-22T12:12:25Z
- **提交信息**: [Fix] hicache: Fail fast on a null pointer from the Mooncake host allocator (#40565)

Co-authored-by: huangtingwei <141888744+huangtingwei9988@users.noreply.github.com>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>

### [8a6770d](https://github.com/sgl-project/sglang/commit/8a6770d5660153f808da9d2b2697b7baa7688485)

- **作者**: Jzz1943
- **时间**: 2026-10-22T12:07:27Z
- **提交信息**: [Fix] NIXL: Preserve explicit UCX network device selection (#45722)

### [96f013b](https://github.com/sgl-project/sglang/commit/96f013b45202cabd8d4a0d6e79596f109538181e)

- **作者**: weireweire
- **时间**: 2026-10-22T11:18:55Z
- **提交信息**: [Doc] Cookbook: update GB300 DSV4.1 disagg AgentX launches from InferenceX #4303 (#45495)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [d0a7565](https://github.com/sgl-project/sglang/commit/d0a75654368a470d8484e3ea45b06e500fee57af)

- **作者**: Alex Nails
- **时间**: 2026-10-22T08:31:54Z
- **提交信息**: [Fix] diffusion: Drop stale mismatch_msg from FLUX 3 video VAE gate call (#45778)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3f6c313](https://github.com/sgl-project/sglang/commit/3f6c3133898ede30e69db0bc95f58ef831f727fd)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-22T08:25:13Z
- **提交信息**: [Fix] diffusion: Restore the kernel registry import after #41894 (#45775)

### [5c2cb60](https://github.com/sgl-project/sglang/commit/5c2cb60790d16874738871a060d7b2f472830e71)

- **作者**: ashwini rathi
- **时间**: 2026-10-22T08:24:41Z
- **提交信息**: [Fix] [Intel] diffusion: Restore copy offload for FLUX.2-dev nightly (#45725)

### [0a87f16](https://github.com/sgl-project/sglang/commit/0a87f163dc6052462cb797ebd0cb14ea4c0e1679)

- **作者**: Michael
- **时间**: 2026-10-22T08:14:14Z
- **提交信息**: [Test] [AMD] deepseek-v4.1: Fix the HIP breakable-graph unit tests for the default prefill context limit and the DSpark draft ring (#45507)

### [1c967f5](https://github.com/sgl-project/sglang/commit/1c967f5043e29bd08ae1ad80d1bba2757a17168f)

- **作者**: kangwangamd
- **时间**: 2026-10-22T08:08:54Z
- **提交信息**: [Fix] [AMD] test: Recalibrate MiniMax-M2.7 GSM8K threshold 0.93->0.91 for MI300 runners (#34241)

### [b513769](https://github.com/sgl-project/sglang/commit/b5137693a5318bd8f55f3ed8caa8c1cef8007118)

- **作者**: jacky.cheng
- **时间**: 2026-10-22T08:05:36Z
- **提交信息**: [Fix] [AMD] diffusion: Enable `--quantization fp8` on gfx1250 (torch.compile lowering + per-channel weight scales) (#45304)

### [24e4596](https://github.com/sgl-project/sglang/commit/24e45961c616ba36a5dd4a6083cf4069d36120a4)

- **作者**: WenhaoZhang
- **时间**: 2026-10-22T07:44:54Z
- **提交信息**: [Perf] diffusion: fuse QKV norm + RoPE, cached RoPE tables for FLUX 3 video VAE (#41894)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [c64886f](https://github.com/sgl-project/sglang/commit/c64886f9e383695c954e5f651a146e70c803a05a)

- **作者**: James Xu
- **时间**: 2026-10-22T07:38:51Z
- **提交信息**: [Perf] diffusion: fuse Wan VAE DupUp3D shortcut add (#32860)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [f727076](https://github.com/sgl-project/sglang/commit/f727076ed012e946bd78a563fbb5e68da3de8a00)

- **作者**: Ankit Dhall
- **时间**: 2026-10-22T07:37:08Z
- **提交信息**: [Feat] diffusion: support wan-animate-2 distilled model (#44085)

Co-authored-by: Ankit Dhall <8938083+ankitdhall@users.noreply.github.com>

### [9d5386f](https://github.com/sgl-project/sglang/commit/9d5386fd13f7a91e9e84dc0c0ab61c5b1fbaba98)

- **作者**: Shuwen Wang
- **时间**: 2026-10-22T07:13:33Z
- **提交信息**: [Perf] dsv41: Fuse request-window layout construction (#45726)

### [33a0734](https://github.com/sgl-project/sglang/commit/33a0734ca16b3f102f548ce66ae20265f75cf4af)

- **作者**: shun8686
- **时间**: 2026-10-22T07:11:47Z
- **提交信息**: [CI] [NPU] precise-test: collect multimodal_gen coverage per test case (#45553)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1293
- **最后更新**: 2026-10-22T13:38:30Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

# cache-dit 昨日提交分析总结

## 一、主要更新类型
以功能新增为主，附带关键Bug修复：新增MiniMax-H3模型对fl2va（首/尾帧条件生成）和ref2va两种工作流的支持，并修复了视觉语言条件器在流式offload下的设备不匹配崩溃；另有一组skills配置更新（工具链元数据调整，非核心代码）。

## 二、关键变更点与项目方向的关系
- **工作流层扩展**：在不重新实现缓存与并行逻辑的前提下，通过复用t2va（文本生视频）的DBCache缓存路径和TP/CP并行路径，让fl2va直接"搭便车"获得加速能力，这与cache-dit"以缓存和并行加速DiT推理"的核心定位高度一致。
- **接口抽象加固**：新增`resolve_transformer/assign_transformer`工具函数，因为不同工作流加载的是`transformer`或`transformer_ref`而非固定字段，`pipe.transformer`不再是安全假设——这是为多工作流、多适配器架构做的必要抽象。
- **条件器兼容**：修复Qwen3-VL视觉塔在offload下崩溃的问题（插值常量从`self.pos_embed.weight.device`取值导致设备错配），改为条件工作流下视觉塔常驻内存。这体现了项目对"CPU offload + 外部条件输入"组合场景的持续打磨。

## 三、对项目的影响和潜在意义
- **功能版图扩展**：首/尾帧条件生成是视频生成领域的高频需求（如视频续写、镜头衔接），补齐该能力直接拓宽了cache-dit的可用场景，使其从单纯的"加速引擎"向"条件工作流加速方案"演进。
- **性能收益可量化**：以256x448/124帧/50步为例，TP2+CP2+cache组合将推理从86.60s（纯缓存）压缩至32.50s，质量损失可控（PSNR 36.08→34.87），再次验证了"缓存+并行"叠加的乘法效应。
- **工程健壮性提升**：修复条件工作流的崩溃，避免用户在实际使用中踩坑，对开源项目的可用性和口碑有正面作用。

## 四、值得关注的技术点
1. **缓存阈值的workflow定制**：fl2va将缓存阈值设为0.022——原因是pinned的条件行会稀释残差DBCache的比较基数，且被跳过的步骤会表现为运动相位滞后。这说明缓存策略并非"一刀切"，项目已进入"按工作流调参"的精细化阶段。
2. **避免二次重采样**：`skip_image_resize`配合MiniMax-H3的自适应画布逻辑（首帧拉伸、尾帧cover裁剪），跳过客户端侧resize，防止源图被重采样两次导致质量损失，细节考虑到位。
3. **双返回格式兼容**：`parse_audio_video_output`同时接受模块化pipeline的字典返回和属性式返回，降低了对外部pipeline实现的耦合。

## 五、对项目发展的影响（结合README背景）
cache-dit的README明确了其作为"PyTorch原生DiT推理引擎"的定位，覆盖Cache、并行、量化、CPU offload四大加速支柱。本次提交虽然只扩展了工作流类型，但具有结构性意义：它验证了核心加速机制（缓存/并行）可以**以低成本横向复用**到新的条件生成范式，同时通过transformer解析抽象为未来更多工作流（ref2va已同步支持）铺平了道路。首尾帧条件支持的加入，使项目在面向实际创作场景（视频编辑、续写、多模态生成）时更具竞争力，而对Qwen3-VL兼容性的修复则显示出项目正认真对待"第三方视觉语言模型作为条件器"的生态整合——这与其"引擎+适配器"的架构方向一致，有望吸引更多模型适配贡献者。

## 详细提交记录

### [16015db](https://github.com/vipshop/cache-dit/commit/16015dbffb073da23fc8335470b9536c18a7df92)

- **作者**: DefTruth
- **时间**: 2026-10-22T13:33:14Z
- **提交信息**: skills: update skills (#1132)

### [1c27ef0](https://github.com/vipshop/cache-dit/commit/1c27ef006809a14b37fdef880670485c64eb0671)

- **作者**: DefTruth
- **时间**: 2026-10-22T13:09:49Z
- **提交信息**: skills: update skills (#1131)

### [39e71d8](https://github.com/vipshop/cache-dit/commit/39e71d87fb9c9526d25669dd45c41b374479c867)

- **作者**: DefTruth
- **时间**: 2026-10-22T10:32:38Z
- **提交信息**: feat: support the MiniMax-H3 fl2va and ref2va workflows (#1130)

* feat: support the MiniMax-H3 fl2va workflow

First/last-frame conditioning reuses the t2va caching and parallelism paths; what it needs is a way
to hand two frames to the pipeline, and a cache threshold that survives the pinned conditioning rows.

  ExampleType.FL2VA and one `_AUDIO_VIDEO_TASKS` set shared by `call_pipe` (which asks a modular
  pipeline for `videos/audio/sampling_rate`) and the output parse (`parse_audio_video_output`,
  which accepts both the dict a modular pipeline returns and the attribute form).
  `--last-image-path` / `ExampleInputData.last_image`, plus `skip_image_resize`: MiniMax-H3 derives
  its canvas from the source aspect ratio and stretches the first frame / cover-crops the last one,
  so a client-side resize would resample twice.
  `minimax_h3_fl2va` example (448x768, 124 frames, 50 steps) with a first/last frame pair, and a
  per-workflow cache preset: the pinned conditioning rows dilute the residual DBCache compares
  against, and the accepted skips show up as motion-phase lag, so fl2va starts at 0.022.
  `resolve_transformer` / `assign_transformer` in `cache_dit.utils`, and both the auto adapter and
  the H3 adapter route through them: a workflow loads either `transformer` or `transformer_ref`,
  never both, so `pipe.transformer` is not a safe assumption any more.

Fixes a crash the conditioning workflows hit: a vision-language conditioner cannot be streamed
whole. Qwen3-VL's vision tower places its interpolation constants from `self.pos_embed.weight.device`
inside a plain method, so a streamed tower builds them on the offload device and the first
`hidden_states + pos_embeds` fails. The tower stays resident instead (both offload paths, and only
when the workflow actually feeds images), and its size is logged.

256x448/124f/50 steps against the uncached run: cache 0.022 -> 86.60 s, 36.08 dB / 0.946;
TP2 52.82 s; TP2+CP2 33.71 s; TP2+CP2+cache 32.50 s / 34.87 dB / 0.904. Audio is muxed at 32 kHz.
Tests: 132 passed.

* feat: support the MiniMax-H3 ref2va workflow

`ref2va` loads `transformer_ref/` instead of `transformer/` — the two partitions are substitutes, so
a ref2va pipeline has no `transformer` attribute at all — and conditions on reference media that is
packed in front of the target sequence as read-only rows.

  ExampleType.REF2VA joins the audio-video set, so `call_pipe` asks for the same state keys and the
  output parse goes through `parse_audio_video_output`.
  `ExampleInputData.set_references` carries the media as an instance attribute rather than a field:
  `data()` runs `dataclasses.asdict`, which would deep copy every video frame and flatten a reference
  dataclass into a dict the pipeline cannot read. `--reference-image/video/audio-path` build the
  same objects through `from_file`, in image -> video -> audio order, are cached per flag so the
  media is decoded once instead of once per `data()` call, and fail early when only a soundtrack is
  given (the setup step would reject it much later).
  References are dropped with a warning for the workflows that do not take them: the flag is global.
  `minimax_h3_ref2va` example (448x768, 124 frames, 50 steps) with a first frame plus a bundled
  1.5 s reference clip, and a stricter cache preset (0.02) than fl2va.
  The offline quantizer and the Ray worker resolve the transformer by name instead of assuming
  `pipe.transformer`, and the worker re-resolves after the optimization step so compiling cannot
  discard a module that parallelism or quantization replaced.

256x448/124f/50 steps, against the uncached run (517.53 s / 55.38 GiB): cache 0.02 -> 353.70 s,
33.56 dB / 0.879; TP2+cache 213.98 s / 49.40 GiB; TP2+CP2 187.31 s / 33.27 dB / 0.866;
TP2+CP2+cache 137.62 s. The reference clip dominates the cost: 49 frames at 720x480 took 1608 s for
the same run. Audio is muxed at 32 kHz. Tests: 81 passed, and the 4 failures in
`tests/quantization` + `tests/api/test_load_configs.py` reproduce on the untouched tree.

* docs: list the MiniMax-H3 fl2va and ref2va workflows in the support table

* Update README.md

* Split MiniMax-H3 entry into FL2VA and Ref2VA

* Update MiniMax-H3 entries in README

* Update MiniMax-H3 model entry in README

* fix: let --compile compose with the streamed AdaLN tables

The host-residency mode rejected `--compile` outright while its modulation tables are streamed, on
the grounds that Dynamo cannot trace the per-step device move. It does not have to: the move already
happens inside the layerwise hooks, which are `torch.compiler.disable`d, so each streamed block
turns into a graph break and the block compiles around it.

Only the two knobs that genuinely cannot work that way are still rejected: `--compile-full-graph`
refuses a break by construction, and a CUDA graph would replay the device pointers the host mirror
rebinds on every block. `--compile` now logs the graph break and proceeds.

256x448/124f/50 steps, `--warmup 2`, against the same configuration without `--compile`:

  bf16 single card   88.76 s -> 78.42 s (1.13x)
  CP2 (2 cards)      68.04 s -> 62.12 s (1.10x, 33.45 dB / 0.895 vs the uncached baseline)

Smaller than the 1.18-1.59x a resident transformer gets, as expected: the attention and FFN bodies
compile, the copy does not.

Tests: 85 passed, including three new cases that pin the policy (compile allowed, full-graph and cuda
graph rejected).

* fix: address the review on the fl2va / ref2va support

  `--compile` now resolves the transformer by name. `ref2va` loads `transformer_ref` and has no
  `transformer`, so the previous `hasattr(pipe, "transformer")` check warned and left the denoiser
  uncompiled.
  Reference media is gated before it is built, not filtered after: `prepare_input_data` sets
  `allow_references` from the task type, so a workflow that takes no references neither decodes the
  flags nor imports the reference loaders (a non-REF2VA run with `--reference-audio-path` used to
  fail the audio-pairing check instead of ignoring the flag).
  The bundled demo frames and references are resolved lazily, only when the matching
  `--image-path` / `--last-image-path` / `--reference-*-path` is absent, so overriding every input no
  longer downloads (or decodes) artwork that is then discarded.
  `Example.run` builds and validates the inputs before `get_pipe()`, so an invalid combination fails
  in a second instead of after the 100+ GiB load.

The NHD fallback report is now a `logger.warning_once` line: it repeats per block and per step, and
the message carries the shape, so the shared helper dedupes it per shape instead of a bespoke set.

Tests: 108 passed across the workflow, ffpa-backend and layerwise suites, including four new cases
for the fixes above and two that pin the warn-once behaviour (one warning for a repeated fallback,
and a real TypeError still surfaced).

* fix: resolve the loaded transformer in quantize, summary and cache teardown

The `ref2va` workflow loads its denoiser as `transformer_ref` and has no `transformer`, but three
paths still assumed the latter and failed quietly or loudly:

  `maybe_quantize_transformer` skipped the module, so `--quantize` left the bf16 partition in place
  while `--adaln-host-residency` took `args.quantize` as proof it could keep the transformer
  resident — the run then held ~62 GiB and could OOM. It now resolves and writes back by name.
  `summary()` (reached through `strify()` on every save) read `pipe.transformer` unconditionally, so
  a ref-only run raised `AttributeError` after the inference and never saved its output.
  `CachedAdapter.release_hooks` only visited `transformer` / `transformer_2`, so `disable_cache`
  left `transformer_ref.forward` patched and its `_is_cached` flag set.

All three go through `resolve_transformer` / `assign_transformer`, so a partition rename is handled
once instead of per call site.

Tests: 268 passed in tests/api, with three new cases that build a `transformer_ref`-only pipeline and
assert it is quantized, summarized and released. The only failure, `test_load_configs[api/config.yaml]`,
reproduces on the untouched tree.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 95153
- **最后更新**: 2026-10-23T00:45:00Z

## 提交统计

- **昨日提交总数**: 60
- **提交者数量**: 55
- **主要提交者**: RomeJay, Victor Wang, Ronald

## AI分析总结

# vLLM 昨日提交分析（60 条记录）

## 1. 主要更新类型分布

- **Bug修复**：约 25 条，占比最大，覆盖模型加载、前端 API、多模态、注意力后端、MoE 等核心模块。
- **性能优化**：约 12 条，包括 ROCm 构建加速、投机解码优化、FlashMLA 稀疏 prefill、多模态融合算子等。
- **硬件平台适配**：ROCm（AMD）、SM100/SM107（NVIDIA Blackwell）、Rubin、CPU、TPU 均有涉及，约 15 条。
- **功能新增/模型支持**：新增 Recursive Flint、Alpamayo 2 Super、Muse Spark（ROCm）等模型，以及 XPress 投机解码方法。
- **重构与 CI**：FlashInfer 通信迁移、多模态前缀范围统一、CI 分片与 Rubin 单测启用等。

## 2. 关键变更点与项目方向的关系

vLLM 的目标是"为所有人提供简单、快速、廉价的 LLM 服务"，本次提交在三个维度直接支撑这一目标：

- **速度与成本**：ROCm 分页注意力 kernel 拆分带来 4–7 倍构建加速；DS V4.1 FlashMLA 稀疏 prefill、GLM-5.3 BF16 GEMM、Gemma4 多模态算子融合均降低推理延迟；MRV2（多请求投机解码）跳过无效 drafting 步骤，减少无用计算。
- **易用性与兼容性**：Responses API 支持 prompt-cache / safety_identifier 字段，修复 Kimi K3 标记泄漏、beam search 分数归一化、Anthropic 错误类型映射等，提升 API 兼容性与开发者体验。
- **生态广度**：大量 ROCm/CPU/TPU 适配（Engram 表、FP16 Triton 注意力路由、Quark MXFP8 量化）让 vLLM 可运行在更多硬件上，降低服务门槛。

## 3. 对项目的影响和潜在意义

- **内存与稳定性**：修复 P/D 分离下容错模式的 KV 块泄漏、LoRA 在 AsyncLLM 中每步从磁盘重载的问题，对生产环境长时运行意义重大。
- **多模态健壮性**：统一 mm 前缀范围计算、多模态限制纳入编译缓存哈希、PP 阶段跳过编码器塔，减少多模态部署中的缓存错误与冗余计算。
- **可观测性**：Mooncake KV Connector 通过 Prometheus 暴露传输统计，为 disaggregation 场景运维提供数据支撑。
- **安全**：刷新 Python 及运行时 CA 证书，维护供应链安全基线。

## 4. 值得关注的技术点

- **XPress 投机解码**（#54448）：一种新的投机解码方法进入核心，与已有的 MRV2 形成互补。
- **MRV2 智能跳过 drafting**：在无请求可消费草稿时跳过起草步骤，是投机解码实用化的重要优化。
- **Engram 表管理**：CPU 加载 + 按精确大小分配 + 跨 DP 副本聚合哈希，体现对大模型记忆/检索外挂组件的系统性支持。
- **CI 现代化**：AMD 镜像从固定分片迁移到自动分片、Rubin 平台单测启用，为新硬件世代做准备。
- **AI 辅助开发常态化**：大量提交出现 Claude/Codex/vllm-agent 等 Co-author，反映 AI 协作开发已深度融入 vLLM 的贡献流程。

## 5. 对项目发展的整体影响

这批提交表明 vLLM 正处于**多硬件平台均衡扩张 + 推理性能持续压榨 + API 生态对齐**三条主线并行推进的阶段。AMD ROCm 与 NVIDIA 新架构（SM100/107、Rubin）的密集适配，配合构建与内核级加速，直接服务"cheap serving"的定位；投机解码（MRV2、XPress）与 MoE 优化持续兑现"fast"的承诺；而前端 API 兼容性修复与错误处理规范化则降低集成摩擦，呼应"easy"与"for everyone"的愿景。大量生产级 bug 修复（KV 泄漏、LoRA 重载、缓存哈希）说明项目正在从功能扩张转向**大规模部署可靠性打磨**，这是走向企业级 LLM 服务基础设施的关键一步。

## 详细提交记录

### [01ab876](https://github.com/vllm-project/vllm/commit/01ab87600e046fe76b259cdae63f7bf444cbea3a)

- **作者**: CAICAII
- **时间**: 2026-10-22T23:52:47Z
- **提交信息**: [KV Connector][Mooncake] Expose transfer stats via Prometheus (#56939)

Signed-off-by: CAICAIIs <3360776475@qq.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [cc1a6d3](https://github.com/vllm-project/vllm/commit/cc1a6d31353205bf38b6dbecf4ad134ce3b2b678)

- **作者**: fxmarty-amd
- **时间**: 2026-10-22T23:31:19Z
- **提交信息**: [ROCm][Build] Reland #62475: paged attention kernel split with `--offload-compress` => x4-x7 wheel build speedup on ROCm (#63105)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Signed-off-by: Felix Marty <felmarty@amd.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [d0eb5d2](https://github.com/vllm-project/vllm/commit/d0eb5d2f217c8b6423fa778aecf712e130957938)

- **作者**: Thirumaran
- **时间**: 2026-10-22T23:27:19Z
- **提交信息**: [Frontend] Expose --sleep-mode-backend on the CLI (#63138)

Signed-off-by: mramaran <mrmaran@protonmail.com>

### [6d1909a](https://github.com/vllm-project/vllm/commit/6d1909a1f23e62d38ad25c029dd43a71106a3990)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-22T23:15:26Z
- **提交信息**: [Bugfix][ROCm][DSv4.1] Gather Engram hashes across DP replicas in the AMD model (#63007)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f01a76f](https://github.com/vllm-project/vllm/commit/f01a76f9503c4cc8c9e13304af7d02fc216012a4)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-22T23:15:22Z
- **提交信息**: [ROCm][DSv4.1] Allocate offloaded Engram tables at their exact size (#63009)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c0c0278](https://github.com/vllm-project/vllm/commit/c0c02786a3d6feed3c676daa63b275d87a90d330)

- **作者**: Aarushi Jain
- **时间**: 2026-10-22T22:53:26Z
- **提交信息**: [Bugfix][Model] Build the skipped DeepSeek-VL2 vision tower without meta .item() (#63192)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>

### [52f4483](https://github.com/vllm-project/vllm/commit/52f44839f2b7a05664f2ac74b5ba766c0045d6d3)

- **作者**: Kfir Toledo
- **时间**: 2026-10-22T22:40:33Z
- **提交信息**: [Startup][UX] Start multiproc workers concurrently when using spawn (#60028)

Signed-off-by: Kfir Toledo <kfir.toledo@ibm.com>
Signed-off-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [6ee316e](https://github.com/vllm-project/vllm/commit/6ee316eaeac39d315837e87f981a7b0f18f7b010)

- **作者**: Jay Yen
- **时间**: 2026-10-22T21:57:35Z
- **提交信息**: upgrade tpu-inference to v0.32.0 and torch to 2.14.0 (#63080)

Signed-off-by: Jay Yen <jay.yen@cienet.com>

### [899a168](https://github.com/vllm-project/vllm/commit/899a1689e2a014ca42567bd9ae6cf96c13fe5e94)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-22T21:56:35Z
- **提交信息**: [Model] Add Recursive Flint (#62938)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [856b984](https://github.com/vllm-project/vllm/commit/856b98415be95893a1b5b26adeb238783bcf91fe)

- **作者**: qizixi
- **时间**: 2026-10-22T21:48:03Z
- **提交信息**: [Spec Decode][MRV2] Skip drafting in steps where no request can use the drafts (#62784)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f0abb2f](https://github.com/vllm-project/vllm/commit/f0abb2f828ef7e52c9de18dcf0e90ad1fdb52c87)

- **作者**: zyulai
- **时间**: 2026-10-22T21:07:39Z
- **提交信息**: [Bugfix][Anthropic] Map vLLM error types to Anthropic error.type vocabulary (#62294)

Signed-off-by: norma blue <867562646@qq.com>
Co-authored-by: OmX <omx@oh-my-codex.dev>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [ce9467b](https://github.com/vllm-project/vllm/commit/ce9467b757c024a55fea4d0919ac2e682f28a894)

- **作者**: Victor Wang
- **时间**: 2026-10-22T21:04:54Z
- **提交信息**: [Core] Add XPress speculative decoding method (#54448)

Signed-off-by: Zheng Wang <zhengw10@illinois.edu>
Signed-off-by: Ubuntu <ubuntu@ip-172-31-27-124.us-west-2.compute.internal>
Signed-off-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [47c091b](https://github.com/vllm-project/vllm/commit/47c091b1006b2c5a13b7475fe919199646623fd7)

- **作者**: alberto
- **时间**: 2026-10-22T20:42:36Z
- **提交信息**: [Bugfix][Frontend] Accept and echo prompt-cache and safety_identifier fields in the Responses API (#62856)

Signed-off-by: Alberto Perdomo <aperdomo@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [2de0531](https://github.com/vllm-project/vllm/commit/2de0531d81525b3fd652ca2f89810b2ff038395e)

- **作者**: cjackal
- **时间**: 2026-10-22T19:45:26Z
- **提交信息**: [Bugfix][Frontend][Kimi K3] Fix Kimi K3 XTML marker leakage in responses API (#62507)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: Fazliddin Vakhobov <mike@aiand.com>

### [b4411f5](https://github.com/vllm-project/vllm/commit/b4411f58a9b42a0adb46a2f1c3473850b07b094c)

- **作者**: Jinzhen Lin
- **时间**: 2026-10-22T19:41:48Z
- **提交信息**: [Quantization] Bump humming-kernels to 0.1.18 and remove DeviceInfo workaround (#62816)

Signed-off-by: jinzhen.ljz <jinzhen.ljz@antgroup.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c722f3a](https://github.com/vllm-project/vllm/commit/c722f3a5368a9eed2b90c1a14b8eaf17acba3e93)

- **作者**: liranschour
- **时间**: 2026-10-22T18:37:41Z
- **提交信息**: [Docs][KV Offload] Document canonical_layout in the KV offloading usage guide (#61822)

Signed-off-by: Liran Schour <lirans@il.ibm.com>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2a03879](https://github.com/vllm-project/vllm/commit/2a038794e0fc1400d404489f8b902e03b7725a63)

- **作者**: Taeyang Yun
- **时间**: 2026-10-22T18:36:00Z
- **提交信息**: [Bugfix][Attention] Fix FA4 FP8 descale strides for singleton KV heads (#58304)

Signed-off-by: taeyangyun <264719684+taeyangyun@users.noreply.github.com>
Co-authored-by: taeyangyun <264719684+taeyangyun@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [1d3e400](https://github.com/vllm-project/vllm/commit/1d3e4006c42428335b8dc116ed137a7bfecf922b)

- **作者**: qli88
- **时间**: 2026-10-22T18:32:35Z
- **提交信息**: [ROCm][CI] Fix int8 GEMM kernel selection logic for ROCm platform (#62099)

Signed-off-by: Qiang Li <qiang.li2@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4a40c61](https://github.com/vllm-project/vllm/commit/4a40c6113072752d93123503444ac703f86f8976)

- **作者**: Jee Jee Li
- **时间**: 2026-10-22T18:20:33Z
- **提交信息**: [Bugfix] Add SM100 support for Step-5-Preview (#63147)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

### [e7bb7e2](https://github.com/vllm-project/vllm/commit/e7bb7e2f20752ad38f8d44a6e7258cf002e29bea)

- **作者**: tiankaijin
- **时间**: 2026-10-22T18:14:25Z
- **提交信息**: [bug-fix] Fix KV block leak with fault tolerance enabled in P/D disaggregation (#56430)

Signed-off-by: tiankaijin <tiankaijin1@h-partners.com>
Signed-off-by: tiankaijin <1669619752@qq.com>
Co-authored-by: tiankaijin <tiankaijin1@h-partners.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Pioneer-Weirdo <80094616+Pioneer-Weirdo@users.noreply.github.com>

### [1cc332e](https://github.com/vllm-project/vllm/commit/1cc332ee800a4fca98f83b9f8d6b379ea34c74d6)

- **作者**: Metehan Aydemir
- **时间**: 2026-10-22T18:14:12Z
- **提交信息**: [Frontend] Use VLLMValidationError for client input errors in renderers base (#62738)

Signed-off-by: MetehanAydemir <mmetehanaydemir@gmail.com>

### [60a7d56](https://github.com/vllm-project/vllm/commit/60a7d568f46851992a364074cbfd96e10ccd68a6)

- **作者**: Andrew Sansom
- **时间**: 2026-10-22T18:04:18Z
- **提交信息**: [Feature] [Frontend] [Reasoning] Support Prompt Embeds inputs for reasoning traces (#62765)

Signed-off-by: Andrew Sansom <andrew@protopia.ai>
Co-authored-by: Codex <codex@openai.com>

### [3895534](https://github.com/vllm-project/vllm/commit/38955340b7520c97dbc66b394bf75d13fc035a0a)

- **作者**: Sahithi Chigurupati
- **时间**: 2026-10-22T18:01:09Z
- **提交信息**: [Perf][GLM-5.3] Enable GLM low-latency BF16 GEMM on SM107 (#62843)

Signed-off-by: Sahithi Chigurupati <58884509+csahithi@users.noreply.github.com>
Signed-off-by: LopezCastroRoberto <robertol.c510@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: LopezCastroRoberto <robertol.c510@gmail.com>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [b6031d7](https://github.com/vllm-project/vllm/commit/b6031d71beb219b9c2cbf580745c7307bf15ec91)

- **作者**: fxmarty-amd
- **时间**: 2026-10-22T17:48:48Z
- **提交信息**: [Quantization][Quark] Support MXFP8 (W8A8) routed experts (#63125)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [b689feb](https://github.com/vllm-project/vllm/commit/b689feb9f22129cb9ba65ea72e3e67e4a9c95355)

- **作者**: Blaze-DSP
- **时间**: 2026-10-22T16:42:08Z
- **提交信息**: [Benchmark] benchmark_moe: read Gemma 4's MoE shape from its text config (#62526)

Signed-off-by: Blaze-DSP <devsp0703@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c723f6d](https://github.com/vllm-project/vllm/commit/c723f6d3ee5c832f7d4a64aaa8dfda5cecbf9eef)

- **作者**: dharak-cohere
- **时间**: 2026-10-22T16:06:20Z
- **提交信息**: [Bugfix][RL] Fix cross-stream reuse of packed NCCL receive buffers (#62555)

Signed-off-by: Dharak Kharod <dharak.kharod@cohere.com>
Co-authored-by: Mohit Kulkarni <mohit.kulkarni@cohere.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [71e9320](https://github.com/vllm-project/vllm/commit/71e9320633219b3e94a2b0db70647bbfe4e330b9)

- **作者**: S.J. Lee
- **时间**: 2026-10-22T15:46:13Z
- **提交信息**: [Attention] Decode FlashInfer spec queries with fa2 on pre-SM90 GPUs (#60532)

Signed-off-by: lesj0610 <lesj0610@gmail.com>
Co-authored-by: Pavani Majety <pmajety@nvidia.com>

### [58c903a](https://github.com/vllm-project/vllm/commit/58c903ac944a06ba15bf1b2a61e5e9ee06b8c751)

- **作者**: Ao Tang
- **时间**: 2026-10-22T15:32:49Z
- **提交信息**: [Refactor] Migrate FlashInfer NVLink one-sided to MoEEpCommunication (#61655)

Signed-off-by: Ao Tang <aot@nvidia.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [f235b89](https://github.com/vllm-project/vllm/commit/f235b89bdf62b5fc6356fc8d5e9d59572e48b145)

- **作者**: 0z5a
- **时间**: 2026-10-22T15:26:42Z
- **提交信息**: [Model] NemotronHMTP: share the target's embedding and LM head (#62194)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: 0z5a <0z5a@users.noreply.github.com>
Signed-off-by: 0z5a <dezhen.lu@student.uni-tuebingen.de>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>

### [6678595](https://github.com/vllm-project/vllm/commit/667859505be18dab1a4695ad68d204a70c4ebc33)

- **作者**: John Calderon
- **时间**: 2026-10-22T15:25:45Z
- **提交信息**: [CI][Test][1/N] Enable unit tests to run on Rubin (#60298)

Signed-off-by: John Calderon <jcalderon@nvidia.com>

### [90aa823](https://github.com/vllm-project/vllm/commit/90aa823cbae28a560b5aecc88e110fcca70aa628)

- **作者**: stefankoncarevic
- **时间**: 2026-10-22T15:17:59Z
- **提交信息**: [ROCm][CI] Download quick-reduce e2e model when cached snapshot has no weights (#63127)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [fdc5fde](https://github.com/vllm-project/vllm/commit/fdc5fde9d786832ab638bc0c2eb2328b637ecd0a)

- **作者**: Luciano Martins
- **时间**: 2026-10-22T14:52:24Z
- **提交信息**: [Perf][Gemma4][Multimodal] Fuse Gemma4Unified 2D posemb and batch image/video embedder (#60643)

Signed-off-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2719411](https://github.com/vllm-project/vllm/commit/271941177dba39fbb1c6f8dc2d386d5b69e63a95)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-10-22T14:40:37Z
- **提交信息**: [Perf] Bypass DispatchPooler grouping for homogeneous tasks (#62940)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3b364ba](https://github.com/vllm-project/vllm/commit/3b364baef5cd731b5e1f14ff16387feb69d01f10)

- **作者**: mushroomcarbon
- **时间**: 2026-10-22T14:28:16Z
- **提交信息**: [MoE] Use the sorted fused-MoE path for host-resident expert weights (#62054)

Signed-off-by: Andrew Goh <andrew.goh@zillion.network>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [3e44c0d](https://github.com/vllm-project/vllm/commit/3e44c0db26f3530d674d255dafabaedcf0e3d742)

- **作者**: RomeJay
- **时间**: 2026-10-22T14:21:12Z
- **提交信息**: [Bugfix][Benchmark] Support boolean sweep plot filters (#60774)

Signed-off-by: JRJRJPRO <j1870831863@outlook.com>

### [e6e4163](https://github.com/vllm-project/vllm/commit/e6e41634242b7ccd18d57cf0df87f753a2c9d1ab)

- **作者**: Ganesh R
- **时间**: 2026-10-22T14:13:12Z
- **提交信息**: [CPU] Warm up MRV2 Triton kernels at startup (#62888)

Signed-off-by: R <Ganesh.R@amd.com>
Signed-off-by: Ganesh R <Ganesh.R@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0ad6ec8](https://github.com/vllm-project/vllm/commit/0ad6ec839e0853333c60f7ccc98bf5ad8114d199)

- **作者**: Chinmay-Kulkarni-AMD
- **时间**: 2026-10-22T13:51:24Z
- **提交信息**: [CPU][GDN] Route FP16 attention through Triton/FLA (#60405)

Signed-off-by: Chinmay Kulkarni <Chinmay.Kulkarni@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [f424213](https://github.com/vllm-project/vllm/commit/f42421354d471d346e37c5da7af242cce13625ca)

- **作者**: Krzysztof Tomala
- **时间**: 2026-10-22T13:47:50Z
- **提交信息**: [Model] Add Alpamayo 2 Super (reasoning model) (#62957)

Signed-off-by: Krzysztof Tomala <ktomala@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [168a86a](https://github.com/vllm-project/vllm/commit/168a86ab8f418b0e12c21c3d582ddf5c6d2927ef)

- **作者**: SeongJun Lee
- **时间**: 2026-10-22T13:27:48Z
- **提交信息**: [Multimodal] Skip encoder towers on later PP stages under V2 (#60238)

Signed-off-by: lesj0610 <lesj0610@gmail.com>
Signed-off-by: Isotr0py <2037008807@qq.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <2037008807@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [87b804f](https://github.com/vllm-project/vllm/commit/87b804f09d698bdcc5dc53062d2058d7faad08ca)

- **作者**: Bugen Zhao
- **时间**: 2026-10-22T12:04:34Z
- **提交信息**: [Rust Frontend] Match reasoning delimiters by token identity (#62892)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ef5bcaa](https://github.com/vllm-project/vllm/commit/ef5bcaa387632c9943f1e1cd0716354d75b99285)

- **作者**: Aaron Hao
- **时间**: 2026-10-22T10:35:21Z
- **提交信息**: [bug] Fix lora reloading from disk every step when using AsyncLLM (#41482)

Signed-off-by: hao-aaron <ahao@anyscale.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [ded32c3](https://github.com/vllm-project/vllm/commit/ded32c3ba7dd7e7acdf6f76f055e95847007a506)

- **作者**: Lazurite
- **时间**: 2026-10-22T10:25:17Z
- **提交信息**: [Bugfix][Model] Fix maximum image token profiling for Unlimited-OCR (#61946)

Signed-off-by: Rapisurazurite <43494437+Rapisurazurite@users.noreply.github.com>

### [f9b0a11](https://github.com/vllm-project/vllm/commit/f9b0a11fe23fad458f5c720065154da102b03f10)

- **作者**: Patryk Mikulski
- **时间**: 2026-10-22T10:12:24Z
- **提交信息**: [Bugfix][CPU] Reject unsupported --kv-cache-dtype at CPU attention backend selection (#62665)

Signed-off-by: Patryk Mikulski <7378686+patrk@users.noreply.github.com>
Co-authored-by: Patryk Mikulski <7378686+patrk@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b3b0bc3](https://github.com/vllm-project/vllm/commit/b3b0bc30590748b859af89832ccc50482dc9b08e)

- **作者**: Isotr0py
- **时间**: 2026-10-22T10:09:37Z
- **提交信息**: [Refactor][Multimodal] Refactor and unify mm prefix range computation (#56937)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [47e2b61](https://github.com/vllm-project/vllm/commit/47e2b610bea16bc6206557a5861264156fccbb9f)

- **作者**: Matteo ATKINSON
- **时间**: 2026-10-22T10:00:08Z
- **提交信息**: [Bugfix][Core] Validate prompt token ids when skip_tokenizer_init is set (#62911)

Signed-off-by: Matteo ATKINSON <matteoatkinson@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c124987](https://github.com/vllm-project/vllm/commit/c1249873af59b43cefc913b919a516e50f4d11f2)

- **作者**: stefankoncarevic
- **时间**: 2026-10-22T09:49:22Z
- **提交信息**: [CI] Expect 400 from /v1/embeddings for bge-m3 token_embed (#63067)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [8121025](https://github.com/vllm-project/vllm/commit/8121025f71f1eda6b7dd78fb6399bff9c2fef673)

- **作者**: Hangrui Cao
- **时间**: 2026-10-22T09:47:45Z
- **提交信息**: [Bugfix] Include multimodal limits in the model compile-cache hash (#54642)

Signed-off-by: DiegoCao <DiegoCao@users.noreply.github.com>
Signed-off-by: Hangrui Cao <50705298+HangruiCao2000@users.noreply.github.com>
Co-authored-by: DiegoCao <DiegoCao@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fa72b61](https://github.com/vllm-project/vllm/commit/fa72b61b55989222302b3fa479044c5c9fc9415d)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-10-22T09:47:39Z
- **提交信息**: [Security] Refresh Python and runtime CA certificates (#62868)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [26cc019](https://github.com/vllm-project/vllm/commit/26cc019013157988c8254ca9c89c42041fa5b713)

- **作者**: dskwe
- **时间**: 2026-10-22T09:46:41Z
- **提交信息**: [Bugfix][Frontend] Keep completion derender stream logprob offsets aligned with tokens (#62163)

Signed-off-by: Yuan Li <dskwelmcy@163.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [390836a](https://github.com/vllm-project/vllm/commit/390836a3936629475696a2416378cf2f2aee8827)

- **作者**: Jared Wen
- **时间**: 2026-10-22T09:00:21Z
- **提交信息**: [Bugfix][Model] Load Granite Speech checkpoints saved by Transformers v5 (#63050)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6ab6bff](https://github.com/vllm-project/vllm/commit/6ab6bff1b6c7170a2d48360a00111abfe1d768fe)

- **作者**: Jee Jee Li
- **时间**: 2026-10-22T09:00:09Z
- **提交信息**: [Model][ROCm] Add Muse Spark Open support on ROCm (#62622)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Jiahan Chang (Cyrus) <173873397+jiahanc@users.noreply.github.com>
Co-authored-by: Hongxia Yang <62075498+hongxiayang@users.noreply.github.com>
Co-authored-by: Isotr0py <mozf@inferact.ai>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: qizixi <22851944+zixi-qi@users.noreply.github.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Tianyu Guo <guoty@inferact.ai>
Co-authored-by: Shangdi Yu <yushangdi123@gmail.com>
Co-authored-by: JohnQinAMD <yanyuan.qin@amd.com>
Co-authored-by: Duncan Moss <6038874+djmmoss@users.noreply.github.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [0f09c4b](https://github.com/vllm-project/vllm/commit/0f09c4b7ca77826bf6c9825231b09d30af09d103)

- **作者**: bzsuni
- **时间**: 2026-10-22T08:53:56Z
- **提交信息**: [Bugfix] Apply default multimodal LoRA per batch conversation (#62906)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>

### [5957bbf](https://github.com/vllm-project/vllm/commit/5957bbf125b1f6bed0dcbedba7737b27cd068f8d)

- **作者**: Linze Shi
- **时间**: 2026-10-22T08:44:22Z
- **提交信息**: [Bugfix][Pooling] Bound late chunk sizes in the Python API (#63051)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f46ea25](https://github.com/vllm-project/vllm/commit/f46ea25e5889e56ee29792b6a90e95f0bc3e6558)

- **作者**: Sun
- **时间**: 2026-10-22T08:36:59Z
- **提交信息**: [Perf][Frontend] Share orjson responses across render and pooling (#58660)

Signed-off-by: levius <2114377220@qq.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: wang.yuqi <yuqi.wang@daocloud.io>

### [12c01a2](https://github.com/vllm-project/vllm/commit/12c01a22eb2f5c7b43354e0b958538382e1d6e79)

- **作者**: Ronald
- **时间**: 2026-10-22T08:26:33Z
- **提交信息**: [MoE] Revert platform hook for routed-expert capture rows (#62624) (#63013)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>

### [aa31fa0](https://github.com/vllm-project/vllm/commit/aa31fa038f2cbfbc681ec9f7b7e39c9c728502ee)

- **作者**: Thang Nguyen
- **时间**: 2026-10-22T08:09:27Z
- **提交信息**: [CI] Move V1 Attention, core kernels and quantization AMD mirrors from fixed to automatic shards (#61862)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9c66703](https://github.com/vllm-project/vllm/commit/9c66703eef1726bdd582370cbeed52ebdb7c2c80)

- **作者**: Wei Zhao
- **时间**: 2026-10-22T07:54:40Z
- **提交信息**: [Bugfix] Support online quantization of Kimi K3 NVIDIA projections (#62980)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b579949](https://github.com/vllm-project/vllm/commit/b579949edf936304ac9e2b52a1613e2871bbcd54)

- **作者**: Chauncey
- **时间**: 2026-10-22T07:50:13Z
- **提交信息**: [Perf] Enable small-head FlashMLA sparse prefill for DS V4.1 on SM90 (#61615)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [7d53359](https://github.com/vllm-project/vllm/commit/7d5335936c40306063a29fc4e2ccbe71b280e40c)

- **作者**: Kein
- **时间**: 2026-10-22T07:26:05Z
- **提交信息**: [Bugfix][Frontend] Normalize beam search scores by generated length (#62928)

Signed-off-by: Kein <160526924+4arkeinlvy@users.noreply.github.com>

### [124501d](https://github.com/vllm-project/vllm/commit/124501da07150e79d10090fd353478a6b2186682)

- **作者**: Chauncey
- **时间**: 2026-10-22T07:23:51Z
- **提交信息**: [Bugfix] Load Engram tables on CPU in the InstantTensor loader (#62692)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-23
**监控日期**: 2026-10-22
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7304
- **最后更新**: 2026-10-23T00:33:54Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 13
- **主要提交者**: Zheng Wengang, Shiang Zhang, NumberWan

## AI分析总结

# vllm-omni 昨日提交分析（17 条）

## 1. 主要更新类型
- **性能优化**占比最高（约 6 条）：前缀缓存优化、CUDA/Triton 算子融合（QK RMSNorm+RoPE 融合）、KV 缓存优化。
- **Bug 修复**约 5 条：涉及 Wan2.2 Cache-DiT、Breeze-TTS、Blackwell dtype 守卫、Qwen-Image CI 精度、Qwen3-Omni。
- **硬件适配**（Intel XPU/ROCm/NVIDIA Blackwell）和**CI/构建**各约 3-4 条。
- **功能新增**较少但关键：OpenPI 多阶段策略服务、Cosmos3 TP/SP/CFG/HSDP 分布式并行、CPU TensorRT 参考实现。

## 2. 关键变更点与项目方向的关系
项目目标是"人人可用的易、快、廉价全模态模型服务"，本次提交精准对应这三个维度：
- **"快"（性能）**：对 omni prefix cache 进行两步系列优化（#9162、#9193），解决并发命中下的缓存塌缩与单步开销；对 HunyuanVideo、Z-Image 等视频/图像模型做 Triton 单 launch 算子融合，减少内核启动开销；MiniMax-H3 KV 缓存优化。
- **"廉价"（硬件覆盖）**：Intel GPU 启用 sleep mode（#5485，重要的能耗/成本特性）、Intel NPU/XPU 相关精度与硬件修复、ROCm MI300 夜间测试扩展与 AITER MHA 缓存复用——多厂商异构硬件支持是降低成本的直接手段。
- **"易"（可靠性与覆盖）**：多项 CI 精度基线固定（TORCH_SDPA、eager、NPU），保证跨硬件结果可比；为 MiniCPM-o 提供 CPU 参考实现便于验证。

## 3. 对项目的影响和潜在意义
- 前缀缓存的两步优化（1/N、2/N）是系列工作的开篇，预计将显著改善多模态推理在高并发场景下的吞吐，对服务成本影响直接。
- Intel sleep mode 和 ROCm 测试扩展表明项目正加速走向**多后端生产就绪**（NVIDIA/AMD/Intel 三线并进），符合"for everyone"的跨平台愿景。
- OpenPI 策略服务和 Cosmos3 分布式并行的加入，拓展了服务化与训练/推理并行的能力边界，为更复杂工作流铺路。

## 4. 值得关注的技术点
- **Triton 融合内核**：将 QK RMSNorm + RoPE（+ cat）合并为单次 Triton launch，并强调与 CUDA 数值一致，是视频模型低延迟的典型手法。
- **前缀缓存并发治理**：针对 omni 前缀缓存在并发命中下"塌缩"的根因修复 + 单步开销削减，属于系统级工程优化。
- **AI 辅助协作显著**：多条提交 Co-authored-by 为 Cursor 与 Claude Opus 5.5，反映 AI 编程工具已深度嵌入该项目的开发流程。
- **多阶段策略 over OpenPI** 与 **Noisy KV 语义澄清**代表服务化抽象和实验性研究方向的推进。

## 5. 结合 README 的项目发展影响
README 定位为"易、快、廉价的全模态服务"。本批提交中，性能优化与算子融合直接支撑"快"，Intel sleep mode 与 ROCm 缓存/测试建设支撑"廉价"的多硬件选择，而 CI 精度固化与 CPU 参考实现支撑"易"（易于验证和部署）。整体看，项目已从功能补齐阶段进入**性能打磨与多后端生产化**的关键期，前缀缓存系列优化有望成为下个里程碑的核心，多厂商硬件支持的成熟将实质性扩大其适用用户群。

## 详细提交记录

### [de7134f](https://github.com/vllm-project/vllm-omni/commit/de7134f97a52cc023d5f19337674fb0fdf53192f)

- **作者**: Chendi.Xue
- **时间**: 2026-10-22T22:21:37Z
- **提交信息**: [Bugfix][Wan2.2] Cache-DiT: support low-noise-only (single transformer_2) runs and discover cache targets (#8800)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [703f8e8](https://github.com/vllm-project/vllm-omni/commit/703f8e830e26b132adea8ea7911232f7c8a9659b)

- **作者**: Joshna-Medisetty
- **时间**: 2026-10-22T22:10:51Z
- **提交信息**: [Bugfix][Hardware][Intel] Breeze-TTS: replay depth and text graphs eagerly off CUDA (#8652)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Chendi Xue <chendi.xue@intel.com>

### [7cbab69](https://github.com/vllm-project/vllm-omni/commit/7cbab69609859021ff571f04969ee1725a480497)

- **作者**: haic0
- **时间**: 2026-10-22T21:11:42Z
- **提交信息**: [CI/Build][ROCm] Add Wan2.2 I2V accuracy to MI300 nightly (#9126)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [98c2041](https://github.com/vllm-project/vllm-omni/commit/98c20414423d0c19af7fa220e5a0244bae7734dc)

- **作者**: Yan Ma
- **时间**: 2026-10-22T19:34:58Z
- **提交信息**: [XPU][Feat] enable sleep mode support on intel GPU (#5485)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7cafa13](https://github.com/vllm-project/vllm-omni/commit/7cafa13cc65a8badc23877c4908238b323904cec)

- **作者**: haic0
- **时间**: 2026-10-22T18:30:30Z
- **提交信息**: [CI/Build][ROCm] Hit the AITER MHA cache from ABI-compatible main (#9224)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [101acb1](https://github.com/vllm-project/vllm-omni/commit/101acb1b7897694c1d6f6043b09e966f61ba2057)

- **作者**: haic0
- **时间**: 2026-10-22T16:56:23Z
- **提交信息**: [CI/Build][ROCm] Shard READY model-executor GPU coverage across two MI300s (#9227)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [224bd81](https://github.com/vllm-project/vllm-omni/commit/224bd81e5f9c86163b968050bf514d6aba4bb860)

- **作者**: wkutak
- **时间**: 2026-10-22T16:14:07Z
- **提交信息**: Enable Cosmos3 MAPS TP, SP, CFG and HSDP (#8633)

Signed-off-by: Wojciech Kutak <wkutak@nvidia.com>
Signed-off-by: wkutak <wkutak@nvidia.com>
Signed-off-by: Zhipeng Wang <zhipeng.wang@inferact.ai>
Co-authored-by: Zhipeng Wang <zhipeng.wang@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [798fef9](https://github.com/vllm-project/vllm-omni/commit/798fef99a33fba3ad3c2439d6ec10fe838c0076b)

- **作者**: Zheng Wengang
- **时间**: 2026-10-22T11:46:12Z
- **提交信息**: [1/N][Perf][Core] Stop the omni prefix cache from collapsing under concurrent hits (#9162)

Signed-off-by: ZhengWG <zwg0606@gmail.com>

### [b4ec9dd](https://github.com/vllm-project/vllm-omni/commit/b4ec9ddfd9f32e230ac4d43f57c2584af7289743)

- **作者**: hyw
- **时间**: 2026-10-22T11:27:35Z
- **提交信息**: [Kernel][HunyuanVideo-1.5] Fuse video/text QK RMSNorm + RoPE + cat into one Triton launch (#7596)

Signed-off-by: HuangYuwei <yuweih205@gmail.com>

### [89ae238](https://github.com/vllm-project/vllm-omni/commit/89ae23895ea01c0a9c09f497fd21970dc59216b4)

- **作者**: Krzysztof Tomala
- **时间**: 2026-10-22T11:13:58Z
- **提交信息**: [Frontend] Serve multi-stage policies over OpenPI (#9120)

Signed-off-by: Krzysztof Tomala <ktomala@nvidia.com>

### [10f23e4](https://github.com/vllm-project/vllm-omni/commit/10f23e4fc649bd90624b81964cd55a6d4e65139f)

- **作者**: Shiang Zhang
- **时间**: 2026-10-22T11:09:49Z
- **提交信息**: [Model] Optimize MiniMax-H3 reference KV caching (#8072)

Signed-off-by: zhang-s-a <1120187718@qq.com>

### [9534efe](https://github.com/vllm-project/vllm-omni/commit/9534efe802ef79ce52af31847fb144f63d259e90)

- **作者**: psv666
- **时间**: 2026-10-22T10:29:43Z
- **提交信息**: [Bugfix] Guard Qwen3-Omni Code2Wav dtype on Blackwell with cuDNN 9.20 (#9144)

Signed-off-by: psv666 <2693925048@qq.com>

### [d6db19b](https://github.com/vllm-project/vllm-omni/commit/d6db19b41f8c081506468859cd8f3910f77f1e5c)

- **作者**: NumberWan
- **时间**: 2026-10-22T09:50:07Z
- **提交信息**: [BugFix][CI][Qwen-Image] Pin accuracy to TORCH_SDPA, eager, and NPU (#8798)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [717f8a3](https://github.com/vllm-project/vllm-omni/commit/717f8a3499fb7dc6b3128b58a8baeacded1a7bbb)

- **作者**: amy-why-3459
- **时间**: 2026-10-22T07:34:21Z
- **提交信息**: [Model] Add CPU-reference TensorRT speaker extraction for MiniCPM-o (#9188)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [d12349a](https://github.com/vllm-project/vllm-omni/commit/d12349a46990be1e81f7d406ae53db08a7823b9e)

- **作者**: hyw
- **时间**: 2026-10-22T07:29:43Z
- **提交信息**: [Kernel][Z-Image] Fuse QK RMSNorm + RoPE with CUDA-matching numerics (#7597)

Signed-off-by: HuangYuwei <yuweih205@gmail.com>

### [9499078](https://github.com/vllm-project/vllm-omni/commit/949907817ee9c15a7fc2733b30b24f82dd9bbaf9)

- **作者**: Zheng Wengang
- **时间**: 2026-10-22T07:28:00Z
- **提交信息**: [2/N][Perf][Core] Cut the per-step cost of the omni prefix cache (#9193)

Signed-off-by: ZhengWG <zwg0606@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [34aca93](https://github.com/vllm-project/vllm-omni/commit/34aca93dc42481706247b103092284730581ef87)

- **作者**: Sheng GAO
- **时间**: 2026-10-22T07:11:33Z
- **提交信息**: [Experimental] Clarify Noisy KV step_replicas, D, and clean semantics (#9169)

Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

---
